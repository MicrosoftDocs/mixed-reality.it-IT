---
title: Testa e occhio estasiati DirectX
description: Guida per sviluppatori per l'uso sguardo head e sotto controllo di rilevamento in native nelle App DirectX.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 05/09/2019
ms.topic: article
keywords: sguardo, head sguardo, head di rilevamento, sotto controllo di rilevamento, directx, input, vntana
ms.openlocfilehash: edf20a621178d76bfc97477f9f9b2eca200f1318
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414414"
---
# <a name="head-and-eye-gaze-input-in-directx"></a>Testa e occhio estasiati input DirectX

In realtà mista di Windows, occhio e head sguardo input viene usato per determinare cosa sta guardando l'utente. Ciò può essere utilizzato per guidare i modelli di input primari, ad esempio [head sguardo ed eseguire il commit](gaze-and-commit.md)e anche per fornire il contesto per i tipi di interazioni. Esistono due tipi di sguardo vettori disponibili tramite l'API: head sguardo e sguardo sotto controllo.  Entrambi sono specificati come una tre ray dimensionale con un'origine e la direzione. Le applicazioni possono quindi raycast le scene o reale e determinare cosa è destinato all'utente.

**Head estasiati** rappresenta la direzione che punta in head dell'utente. È possibile scegliere la posizione e la direzione in avanti dei dispositivi, con la posizione che rappresenta il centro di scegliere tra le due visualizzazioni.  Sguardo HEAD è disponibile in tutti i dispositivi di realtà mista.

**Sguardo occhio** rappresenta la direzione che desiderano verso gli occhi dell'utente. L'origine si trova tra gli occhi dell'utente.  È disponibile nei dispositivi di realtà mista che includono un occhio di sistema di registrazione.

Head sia occhio rays sguardo sono accessibili tramite il [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API. È sufficiente chiamare [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) per ricevere un nuovo oggetto SpatialPointerPose al timestamp specificato e [sistema di coordinate](coordinate-systems-in-directx.md). Questo SpatialPointerPose contiene un'origine sguardo head e la direzione. Contiene anche un occhio sguardo origine e la direzione se è disponibile sotto controllo di rilevamento.

## <a name="using-head-gaze"></a>Usando sguardo head

Per accedere la sguardo head, avviare chiamando [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) per ricevere un nuovo oggetto SpatialPointerPose. È necessario passare i parametri seguenti.
 - Oggetto [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) che rappresenta il sistema di coordinate desiderato per lo sguardo head. Ciò è rappresentato dal *sistema di coordinate* variabile nel codice seguente. Per altre informazioni, visitare il nostro [sistemi di coordinate](coordinate-systems-in-directx.md) Guida per gli sviluppatori.
 - Oggetto [Timestamp](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) che rappresenta l'ora esatta della posa head richiesta.  In genere si utilizzerà un timestamp che corrisponde al tempo quando verrà visualizzato il frame corrente. È possibile ottenere questo timestamp previste per la visualizzazione da un [HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) oggetto, che è accessibile tramite l'istanza corrente [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe).  Questo oggetto HolographicFramePrediction è rappresentato dal *stima* variabile nel codice seguente.

 Dopo aver creato un SpatialPointerPose valido, la posizione head e la direzione in avanti sono accessibili come proprietà.  Il codice seguente viene illustrato come accedervi.

 ```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    float3 headPosition = pointerPose.Head().Position();
    float3 headForwardDirection = pointerPose.Head().ForwardDirection();

    // Do something with the head gaze
}
```

## <a name="using-eye-gaze"></a>Usando sguardo sotto controllo

L'API di sguardo occhio è molto simile a sguardo head.  Usa lo stesso [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API, che offre un raggio di origine e la direzione che è possibile raycast contro la scena.  L'unica differenza è che è necessario abilitare in modo esplicito il rilevamento sotto controllo prima di poterla usare. A tale scopo, è necessario eseguire due passaggi:
1. Richiedere l'autorizzazione utente per usare occhio rilevamento nell'app.
2. Abilitare la funzionalità di "Input sguardo" nel manifesto del pacchetto.

### <a name="requesting-access-to-gaze-input"></a>Richiesta di accesso a input sguardo
Quando si avvia l'app, chiamare [EyesPose::RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) per richiedere l'accesso a rilevamento sotto controllo. Il sistema richiede all'utente se necessario e restituire [GazeInputAccessStatus::Allowed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus) dopo che è stato concesso l'accesso. Si tratta di una chiamata asincrona, pertanto è necessario un po' di gestione supplementare. Nell'esempio seguente attiva un std::thread scollegato per attendere il risultato, che viene archiviato in una variabile membro denominata *m_isEyeTrackingEnabled*.

```cpp
using namespace winrt::Windows::Perception::People;
using namespace winrt::Windows::UI::Input;

std::thread requestAccessThread([this]()
{
    auto status = EyesPose::RequestAccessAsync().get();

    if (status == GazeInputAccessStatus::Allowed)
        m_isEyeTrackingEnabled = true;
    else
        m_isEyeTrackingEnabled = false;
});

requestAccessThread.detach();

```
Avvio di un thread scollegato è solo un'opzione per la gestione delle chiamate async.  In alternativa, è possibile usare le nuove [co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) funzionalità supportate da C++/WinRT.
Ecco un altro esempio per l'autorizzazione utente:
-   EyesPose::IsSupported() consente all'applicazione attivare la finestra di dialogo di autorizzazione solo se è presente un tracker sotto controllo.
-   M_gazeInputAccessStatus GazeInputAccessStatus; Si tratta di evitare comparendo ripetutamente il prompt relativo alle autorizzazioni.

```cpp
GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.

// This will trigger to show the permission prompt to the user.
// Ask for access if there is a corresponding device and registry flag did not disable it.
if (Windows::Perception::People::EyesPose::IsSupported() &&
   (m_gazeInputAccessStatus == GazeInputAccessStatus::Unspecified))
{ 
    Concurrency::create_task(Windows::Perception::People::EyesPose::RequestAccessAsync()).then(
    [this](GazeInputAccessStatus status)
    {
        // GazeInputAccessStatus::{Allowed, DeniedBySystem, DeniedByUser, Unspecified}
            m_gazeInputAccessStatus = status;
        
        // Let's be sure to not ask again.
        if(status == GazeInputAccessStatus::Unspecified)
        {
                m_gazeInputAccessStatus = GazeInputAccessStatus::DeniedBySystem;    
        }
    });
}

```


### <a name="declaring-the-gaze-input-capability"></a>Dichiarare la *estasiati Input* funzionalità

Fare doppio clic sul file appxmanifest nel *Esplora soluzioni*.  Quindi passare al *funzionalità* sezione e selezionare il *estasiati Input* funzionalità. 

![Capacità di input sguardo](images/gaze-input-capability.png)

Ciò consente di aggiungere le righe seguenti per il *pacchetto* sezione nel file appxmanifest:
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a>Ottenere il raggio sguardo sotto controllo
Dopo aver ricevuto l'accesso a ET, si possono acquisire raggio sguardo occhio ogni fotogramma.  Come avviene con head sguardo, ottenere il [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) chiamando [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) con un timestamp desiderato e un sistema di coordinate. Il SpatialPointerPose contiene un' [EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) dell'oggetto tramite il [occhi](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) proprietà. Ciò è diverso da null solo se è abilitata l'occhio di rilevamento. Da qui è possibile controllare se l'utente del dispositivo ha un occhio rilevamento calibrazione chiamando [EyesPose::IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).  Successivamente, usare il [estasiati](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) proprietà da ottenere l'una [SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) fissata l'occhio del lettore estasiati posizione e la direzione. La proprietà sguardo può talvolta essere null, pertanto assicurarsi di eseguire questo controllo. Questo può verificarsi è se un utente calibrato chiude temporaneamente ai loro stessi occhi.

Il codice seguente viene illustrato come il raggio sguardo sotto controllo di accesso.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    if (pointerPose.Eyes() && pointerPose.Eyes().IsCalibrationValid())
    {
        if (pointerPose.Eyes().Gaze())
        {
            auto spatialRay = pointerPose.Eyes().Gaze().Value();
            float3 eyeGazeOrigin = spatialRay.Origin;
            float3 eyeGazeDirection = spatialRay.Direction;
            
            // Do something with the eye gaze
        }
    }
}

```

## <a name="correlating-gaze-with-other-inputs"></a>Sguardo con correlazione con altri input

In alcuni casi si potrebbe rilevare che è necessario un [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) che corrisponde a un evento in passato. Ad esempio, se l'utente esegue un'aria toccare, l'app potrebbe essere necessario sapere che cosa si sta cercando. A tale scopo, utilizzare semplicemente [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) il frame stimato ora saranno impreciso a causa della latenza tra l'elaborazione dell'input del sistema e l'ora di visualizzazione. Inoltre, se si usa sguardo sotto controllo per specificare come destinazione, gli occhi tendono a passare anche prima del completamento di un'operazione di commit. È minore di un problema per un semplice Air Tap, ma diventano più importanti quando si combinano tempo comandi vocali con spostamenti occhio veloce. Un modo per gestire questo scenario è eseguire una chiamata aggiuntiva al [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), usando un timestamp cronologico che corrisponde all'evento di input.  

Tuttavia, per l'input viene indirizzata attraverso il SpatialInteractionManager, vi è un metodo più semplice. Il [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) ha il proprio [TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) (funzione). Chiamare il metodo che fornirà un perfettamente correlati [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) senza lasciare al caso. Per altre informazioni sull'uso di SpatialInteractionSourceStates, esaminiamo il [mani e i controller di movimento in DirectX](hands-and-motion-controllers-in-directx.md) documentazione.

## <a name="see-also"></a>Vedere anche
* [Head sguardo ed eseguire il commit del modello di input](gaze-and-commit.md)
* [Visiva in HoloLens 2](eye-tracking.md)
* [Sistemi di coordinate in DirectX](coordinate-systems-in-directx.md)
* [Input vocale in DirectX](voice-input-in-directx.md)
* [Mani e controller del movimento in DirectX](hands-and-motion-controllers-in-directx.md)

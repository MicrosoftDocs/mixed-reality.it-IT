---
title: Sguardo in DirectX
description: Guida per gli sviluppatori per l'uso degli sguardi e degli occhi nelle app DirectX native.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 05/09/2019
ms.topic: article
keywords: occhio, sguardo, Head-sguardi, tracking, tracciamento degli occhi, DirectX, input, ologrammi
ms.openlocfilehash: 48188cc8c886b371847357701b42249f486bceac
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641123"
---
# <a name="head-gaze-and-eye-gaze-input-in-directx"></a>Input occhi e sguardi in DirectX

Per quanto riguarda la realtà mista di Windows, viene usato l'input occhi e occhio per determinare l'aspetto dell'utente. Questo può essere usato per gestire i modelli di input primari, ad esempio [Head-sguardi e commit](gaze-and-commit.md), nonché per fornire il contesto per i tipi di interazioni. Esistono due tipi di vettori di sguardi disponibili tramite l'API, ovvero Head-sguardi e sguardo.  Entrambe sono fornite come un raggio tridimensionale con un'origine e una direzione. Le applicazioni possono quindi Raycast nelle proprie scene, o nel mondo reale, e determinare le operazioni di destinazione dell'utente.

**Head-sguardi** rappresenta la direzione a cui è puntata la testa dell'utente. Si pensi a questo come la posizione e la direzione di avanzamento del dispositivo stesso, con la posizione che rappresenta il punto centrale tra le due visualizzazioni. Head-sguardi è disponibile in tutti i dispositivi a realtà mista.

**Eye-sguardi** rappresenta la direzione verso la quale gli occhi dell'utente stanno cercando. L'origine si trova tra gli occhi dell'utente.  È disponibile nei dispositivi a realtà mista che includono un sistema di rilevamento degli occhi.

I raggi Head e sguardi sono accessibili tramite l'API [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) . È sufficiente chiamare [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) per ricevere un nuovo oggetto SpatialPointerPose in corrispondenza del timestamp e del [sistema di coordinate](coordinate-systems-in-directx.md)specificati. Questo SpatialPointerPose contiene un'origine e una direzione per lo sguardo del capo. Contiene anche un'origine e una direzione degli sguardi se è disponibile la verifica degli occhi.

### <a name="device-support"></a>Supporto di dispositivi
<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><strong>Funzionalità</strong></td>
     <td><a href="hololens-hardware-details.md"><strong>HoloLens (prima generazione)</strong></a></td>
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
</tr>
<tr>
     <td>Puntamento con la testa</td>
     <td>✔️</td>
     <td>✔️</td>
     <td>✔️</td>
</tr>
<tr>
     <td>Sguardo attento</td>
     <td>❌</td>
     <td>✔️</td>
     <td>❌</td>
</tr>
</table>

## <a name="using-head-gaze"></a>Uso di Head-sguardi

Per accedere all'Head-sguardi, iniziare chiamando [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) per ricevere un nuovo oggetto SpatialPointerPose. È necessario passare i parametri seguenti.
 - Oggetto [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) che rappresenta il sistema di coordinate desiderato per lo sguardo Head. Questa operazione è rappresentata dalla variabile *coordinateSystem* nel codice riportato di seguito. Per ulteriori informazioni, visitare la guida per gli sviluppatori di [sistemi di coordinate](coordinate-systems-in-directx.md) .
 - [Timestamp](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) che rappresenta l'ora esatta della richiesta Head.  Viene in genere utilizzato un timestamp corrispondente all'ora in cui verrà visualizzato il frame corrente. È possibile ottenere questo timestamp di visualizzazione stimato da un oggetto [HolographicFramePrediction](https://docs.microsoft.com//uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) , accessibile tramite il [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe)corrente.  Questo oggetto HolographicFramePrediction è rappresentato dalla variabile di *stima* nel codice riportato di seguito.

 Quando si dispone di un SpatialPointerPose valido, la posizione della testa e la direzione di avanzamento sono accessibili come proprietà.  Nel codice seguente viene illustrato come accedervi.

 ```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    float3 headPosition = pointerPose.Head().Position();
    float3 headForwardDirection = pointerPose.Head().ForwardDirection();

    // Do something with the head-gaze
}
```

## <a name="using-eye-gaze"></a>Uso degli sguardi

Si noti che, per consentire agli utenti di usare l'input con sguardo oculare, ogni utente deve esaminare la [calibrazione degli utenti](calibration.md) per la prima volta che usa il dispositivo. L'API Eye-sguardi è molto simile a Head-sguardi.
Usa la stessa API [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) , che fornisce un'origine e una direzione del raggio che è possibile Raycast per la scena.  L'unica differenza è che è necessario abilitare in modo esplicito il rilevamento degli occhi prima di usarlo. A tale scopo, è necessario eseguire due passaggi:
1. Richiedere all'utente l'autorizzazione per usare il rilevamento degli occhi nell'app.
2. Abilitare la funzionalità di "input dello sguardo" nel manifesto del pacchetto.

### <a name="requesting-access-to-eye-gaze-input"></a>Richiesta di accesso a Eye-sguardi input
All'avvio dell'app, chiamare [EyesPose:: RequestAccessAsync](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) per richiedere l'accesso al rilevamento degli occhi. Se necessario, il sistema richiede all'utente e restituisce [GazeInputAccessStatus:: allowed](https://docs.microsoft.com//uwp/api/windows.ui.input.gazeinputaccessstatus) dopo che è stato concesso l'accesso. Si tratta di una chiamata asincrona, quindi richiede un po' di gestione aggiuntiva. Nell'esempio seguente viene avviata un'operazione std:: thread scollegata per attendere il risultato, che viene archiviato in una variabile membro denominata *m_isEyeTrackingEnabled*.

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
L'avvio di un thread scollegato è solo un'opzione per la gestione delle chiamate asincrone. In alternativa, è possibile usare la nuova funzionalità [co_await](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) supportata da C++/WinRT.
Di seguito è riportato un altro esempio per richiedere l'autorizzazione utente:
-   EyesPose:: supporto () consente all'applicazione di attivare la finestra di dialogo di autorizzazione solo se è presente uno strumento di rilevamento.
-   GazeInputAccessStatus m_gazeInputAccessStatus; In questo modo si evita di riscattare il prompt delle autorizzazioni più volte.

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

### <a name="declaring-the-gaze-input-capability"></a>Dichiarazione della funzionalità di *input di sguardi*

Fare doppio clic sul file appxmanifest in *Esplora soluzioni*.  Passare quindi alla sezione *funzionalità* e controllare la funzionalità di *input di sguardi* . 

![Funzionalità di input di sguardi](images/gaze-input-capability.png)

Vengono aggiunte le righe seguenti alla sezione del *pacchetto* nel file appxmanifest:
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a>Ottenere il raggio d'occhio
Dopo aver ricevuto l'accesso a ET, è possibile cogliere il raggio d'occhio per ogni fotogramma.
Come per gli occhi, ottenere il [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) chiamando [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) con un timestamp e un sistema di coordinate desiderati. SpatialPointerPose contiene un oggetto [EyesPose](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose) tramite la proprietà [Eyes](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) . Questo valore non è null solo se è abilitata la funzionalità Eye Tracking. Da qui è possibile verificare se l'utente nel dispositivo ha una calibrazione del rilevamento degli occhi chiamando [EyesPose:: IsCalibrationValid](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).  Usare quindi la proprietà [sguardi](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) per ottenere la posizione e la direzione di un [SpatialRay](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialray) . La proprietà sguardi può talvolta essere null, quindi assicurarsi di controllarla. Questo problema può verificarsi se un utente calibrato chiude temporaneamente gli occhi.

Il codice seguente illustra come accedere al raggio d'occhio.

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
            
            // Do something with the eye-gaze
        }
    }
}

```

## <a name="fallback-when-eye-tracking-is-not-available"></a>Fallback quando il rilevamento degli occhi non è disponibile
Come indicato nella documentazione di progettazione per il [monitoraggio degli occhi](eye-tracking.md#fallback-solutions-when-eye-tracking-is-not-available), sia le finestre di progettazione che gli sviluppatori devono tenere presente che potrebbero essere presenti istanze in cui i dati di rilevamento degli occhi potrebbero non essere disponibili per l'app.
Sono diversi i motivi per cui un utente non è calibrato, l'utente ha negato l'accesso dell'app ai dati di rilevamento degli occhi o semplicemente interferenze temporanee (ad esempio, le sbavature sulla visiera HoloLens o sui capelli occlusione gli occhi dell'utente). Sebbene alcune API siano già state citate in questo documento, di seguito viene fornito un riepilogo su come rilevare che il rilevamento degli occhi è disponibile come riferimento rapido: 

* Verificare che il sistema supporti la verifica degli occhi. Chiamare il *Metodo*seguente: [Windows. Perception. people. EyesPose. IsValid ()](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.issupported#Windows_Perception_People_EyesPose_IsSupported)

* Verificare che l'utente sia calibrato. Chiamare la *Proprietà*seguente: [Windows. Perception. people. EyesPose. IsCalibrationValid](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid) 

* Verificare che l'utente abbia specificato l'autorizzazione dell'app per usare i dati di rilevamento degli occhi: recuperare il _' GazeInputAccessStatus '_ corrente. Un esempio di come eseguire questa operazione è illustrato nella pagina relativa alla [richiesta di accesso a sguardi input](https://docs.microsoft.com/windows/mixed-reality/gaze-in-directX#requesting-access-to-gaze-input).   

Inoltre, è possibile verificare che i dati di rilevamento degli occhi non siano obsoleti aggiungendo un timeout tra gli aggiornamenti dei dati di rilevamento degli occhi ricevuti e altrimenti il fallback a Head-sguardi come descritto di seguito.  
Per ulteriori informazioni, vedere le [considerazioni sulla progettazione di fallback](eye-tracking.md#fallback-solutions-when-eye-tracking-is-not-available) .

<br>

## <a name="correlating-gaze-with-other-inputs"></a>Correlazione di sguardi con altri input
In alcuni casi potrebbe essere necessario un [SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) che corrisponda a un evento nel passato. Ad esempio, se l'utente esegue una scelta aerea, l'app potrebbe voler sapere cosa stavano cercando. A questo scopo, l'uso di [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) con il tempo previsto per i frame potrebbe non essere accurato a causa della latenza tra l'elaborazione dell'input di sistema e l'ora di visualizzazione. Inoltre, se si usa il controllo degli sguardi per la destinazione, gli occhi tendono a proseguire anche prima di terminare un'azione di commit. Si tratta di un problema minore per un semplice tocco, ma diventa più importante quando si combinano i comandi Long Voice con rapidi movimenti oculari. Un modo per gestire questo scenario è eseguire un'ulteriore chiamata a [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), usando un timestamp cronologico corrispondente all'evento di input.  

Tuttavia, per l'input che viene indirizzato attraverso SpatialInteractionManager, è disponibile un metodo più semplice. [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) dispone di una propria funzione [TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) . Chiamando che fornirà un [SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) perfettamente correlato senza le congetture. Per altre informazioni sull'uso di SpatialInteractionSourceStates, vedere la documentazione su [hands and Motion Controllers in DirectX](hands-and-motion-controllers-in-directx.md) .

<br>

## <a name="calibration"></a>Calibrazione
Per il corretto funzionamento dell'analisi degli occhi, è necessario che ogni utente debba esaminare la [calibrazione degli utenti](calibration.md). In questo modo, il dispositivo può modificare il sistema per un'esperienza di visualizzazione più comoda e di qualità superiore per l'utente e garantire il rilevamento accurato degli occhi allo stesso tempo. Gli sviluppatori non devono eseguire alcuna operazione al termine della gestione della calibrazione degli utenti. Il sistema garantisce che all'utente venga richiesto di calibrare il dispositivo nei casi seguenti: * l'utente sta usando il dispositivo per la prima volta * l'utente ha rifiutato in precedenza il processo di calibrazione * il processo di calibrazione non ha avuto esito positivo per l'ultimo tempo di utilizzo del dispositivo da parte dell'utente

Gli sviluppatori devono garantire un supporto adeguato per gli utenti per i quali i dati di rilevamento degli occhi potrebbero non essere disponibili. Per altre informazioni sulle soluzioni di fallback, vedere [Eye tracking on Hololens 2](eye-tracking.md).

<br>

## <a name="see-also"></a>Vedi anche
* [Calibrazione](calibration.md)
* [Sistemi di coordinate in DirectX](coordinate-systems-in-directx.md)
* [Eye-sguardi su HoloLens 2](eye-tracking.md)
* [Modello di input sguardo e commit](gaze-and-commit.md)
* [Mani e controller del movimento in DirectX](hands-and-motion-controllers-in-directx.md)
* [Input vocale in DirectX](voice-input-in-directx.md)

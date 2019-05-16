---
title: Le mani e i controller di movimento in DirectX
description: Guida per sviluppatori per l'uso di rilevamento disponibili e i controller di movimento in native nelle App DirectX.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/30/2019
ms.topic: article
keywords: le mani, i controller di movimento, directx, input, vntana
ms.openlocfilehash: 08666c8c26cd4851c0c003a96a9e96d7a90228ac
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629644"
---
# <a name="hands-and-motion-controllers-in-directx"></a>Le mani e i controller di movimento in DirectX

Nella realtà mista di Windows, sia a essere passate e [controller di movimento](motion-controllers.md) input viene gestito tramite l'input spaziale API, disponibili nel [Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial) dello spazio dei nomi. In questo modo è possibile gestire facilmente le azioni comuni, ad esempio **seleziona** preme allo stesso modo attraverso le mani sia i controller di movimento.

## <a name="getting-started"></a>Attività iniziali

Per accedere a spaziale di input in realtà mista di Windows, iniziare con l'interfaccia SpatialInteractionManager.  È possibile accedere all'interfaccia chiamando [SpatialInteractionManager::GetForCurrentView](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getforcurrentview), in genere a volte durante l'avvio dell'app.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

SpatialInteractionManager interactionManager = SpatialInteractionManager::GetForCurrentView();
```

Processo del SpatialInteractionManager consiste nel fornire l'accesso a [SpatialInteractionSources](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource), che rappresenta un'origine di input.  Sono disponibili tre tipi di SpatialInteractionSources nel sistema.
* **Mano** rappresenta mano rilevato dell'utente. Origini disponibili offrono diverse funzionalità in base al dispositivo, compreso tra i movimenti di base su HoloLens mano completamente articolati e di rilevamento in 2 HoloLens. 
* **Controller** rappresenta un controller di movimento associati. I controller di movimento possono offrire un'ampia gamma di funzionalità.  Ad esempio:  Selezionare i trigger, pulsanti di Menu, pulsanti. é quindi, touchpad multipli e levette.
* **Voce** rappresenta la voce dell'utente a proposito di sistema ha rilevato le parole chiave. Questa origine verrà, ad esempio, inserire una pressione Seleziona e rilasciare ogni volta che l'utente afferma "Select".

Per frame dei dati per un'origine è rappresentata dal [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) interfaccia. Esistono due modi diversi per accedere a questi dati, a seconda che si voglia usare un modello basato sugli eventi o basati su polling nell'applicazione.

### <a name="event-driven-input"></a>Input basato su eventi
Il SpatialInteractionManager fornisce una serie di eventi che può essere in ascolto l'app.  Alcuni esempi includono [SourcePressed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed), [SourceReleased](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased) e [SourceUpdated](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated).

Ad esempio, il codice seguente associa un gestore eventi chiamato MyApp::OnSourcePressed all'evento SourcePressed.  In questo modo l'app rilevare le pressioni in qualsiasi tipo di origine di interazione.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

auto interactionManager = SpatialInteractionManager::GetForCurrentView();
interactionManager.SourcePressed({ this, &MyApp::OnSourcePressed });

```

Questo evento premuto viene inviato all'App in modo asincrono, insieme al SpatialInteractionSourceState corrispondente al momento che si è verificata la pressione. L'app o il motore di gioco potrebbe essere necessario eseguire alcune operazioni di elaborazione sin da subito oppure è possibile accodare i dati dell'evento nelle routine di elaborazione dell'input. Di seguito è una funzione del gestore eventi per l'evento SourcePressed, che illustra come controllare se è stato premuto il pulsante di selezione.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

void MyApp::OnSourcePressed(SpatialInteractionManager const& sender, SpatialInteractionSourceEventArgs const& args)
{
    if (args.PressKind() == SpatialInteractionPressKind::Select)
    {
        // Select button was pressed, update app state
    }
}
```

Il codice precedente verifica solo per la stampa 'Select', che corrisponde all'azione principale nel dispositivo. Ad esempio eseguire un'AirTap su HoloLens o il pull del trigger in un controller di movimento.  'Select' pressioni rappresentano l'intenzione dell'utente per attivare l'ologrammi che di destinazione.  Verrà generato l'evento SourcePressed per un numero di diversi pulsanti e i movimenti ed è possibile esaminare le altre proprietà in SpatialInteractionSource per eseguire il test per i casi.

### <a name="polling-based-input"></a>Input basati su polling
È anche possibile usare SpatialInteractionManager per eseguire il polling ogni fotogramma per lo stato corrente dell'input.  A tale scopo, è sufficiente chiamare [GetDetectedSourcesAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp) ogni fotogramma.  Questa funzione restituisce una matrice contenente uno [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) per ogni attivo [SpatialInteractionSource](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource). Ciò significa, uno per ogni controller attivo del movimento, uno per ogni indicatore rilevate e uno per i dialoghi se un comando 'select' è stato recentemente pronunciato. È quindi possibile esaminare le proprietà in ogni SpatialInteractionSourceState all'input dell'unità all'interno dell'applicazione. 

Ecco un esempio di come verificare l'azione 'select' utilizzando il metodo di polling. Si noti che il *prediction* variabile rappresenta un [HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) oggetto, che può essere ottenuto dal [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe).

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

auto interactionManager = SpatialInteractionManager::GetForCurrentView();
auto sourceStates = m_spatialInteractionManager.GetDetectedSourcesAtTimestamp(prediction.Timestamp());

for (auto& sourceState : sourceStates)
{
    if (sourceState.IsSelectPressed())
    {
        // Select button is down, update app state
    }
}
```

Ogni SpatialInteractionSource ha un ID, che è possibile usare per identificare le origini nuova e correlare le origini esistenti da un fotogramma per fotogramma.  Mani vengono assegnate un ID di nuovo ogni volta che possono lasciare e immettere il campo di visualizzazione, ma gli ID controller restano statici per la durata della sessione.  È possibile usare, ad esempio gli eventi in SpatialInteractionManager [SourceDetected](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcedetected) e [SourceLost](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcelost), per rispondere al mani immettono o lasciare il dispositivo di visualizzazione o quando i controller di movimento sono attivati/disattivato o sono abbinate/non abbinato.

### <a name="predicted-vs-historical-poses"></a>Prevedere e può causare cronologici
Si noti che GetDetectedSourcesAtTimestamp ha un parametro di timestamp. In questo modo è possibile richiedere lo stato e presentare i dati sia stimato o cronologici e ciò consente correlare spaziali interazioni con altre origini di input. Ad esempio, durante il rendering di posizione dell'icona della mano nel frame corrente, è possibile passare il timestamp stimato fornito dal [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe). Ciò consente al sistema di forward-prevedere la posizione di mano ai fini corretto allineamento con l'output di frame sottoposto a rendering, riducendo al minimo la latenza percepita.

Tuttavia, questo tipo una posa stimata non produce un raggio di puntamento ideale per lo sviluppo con un'origine di interazione per. Ad esempio, quando viene premuto un pulsante di controller di movimento, può richiedere fino a 20 ms per l'evento di bubbling tramite Bluetooth al sistema operativo. Allo stesso modo, dopo che un utente ha eseguito un'azione manuale, determinato intervallo di tempo può trascorrere prima che il sistema rileva il movimento e l'app, quindi esegue il polling per tale. Una volta l'app esegue il polling di una modifica dello stato, può causare l'intestazione e il trasferimento di consente di destinazione che in passato è effettivamente successo l'interazione. Se la destinazione è passando il timestamp di HolographicFrame corrente a GetDetectedSourcesAtTimestamp, la posa verrà invece inoltrare eseguita la stima per il raggio di destinazione al momento che verrà visualizzato il frame, che può essere più di 20 ms in futuro. Source sia vantaggioso per il futuro posa *rendering* l'origine di interazione, ma si sommano il problema in fase di *destinate a* interazione, come la destinazione è l'utente si è verificato in passato.

Per fortuna, il [SourcePressed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed), [SourceReleased](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased) e [SourceUpdated](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated) eventi forniscono la cronologia [stato](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state) associato ogni evento di input.  Ciò include direttamente i cronologici head e mano pose disponibili tramite [TryGetPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose), insieme a un cronologici [Timestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.timestamp) che è possibile passare ad altre API per la correlazione con questo evento.

Ciò porta per le procedure consigliate seguenti durante il rendering e selezione di destinazioni con controller e le mani ogni frame:
* Per la **per il rendering manuale/controller** ogni fotogramma, l'app deve **polling** per il **stimato forward** comportare di ogni origine di interazione in fase di photon del frame corrente.  È possibile eseguire il polling per tutte le origini di interazione chiamando [GetDetectedSourcesAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp) ogni fotogramma, passando il timestamp stimato fornito da [HolographicFrame::CurrentPrediction](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.currentprediction).
* Per **destinate a mano/controller** durante una pressione o una versione, l'app deve gestire premuto o rilasciato **eventi**, raycasting base il **cronologici** posa head o manualmente per tale evento. Si ottiene questo ray targeting gestendo il [SourcePressed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed) o [SourceReleased](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased) evento, recupero il [stato](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state) proprietà dagli argomenti dell'evento e chiamando quindi il [ TryGetPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) (metodo).

## <a name="cross-device-input-properties"></a>Proprietà di input di più dispositivi
L'API SpatialInteractionSource supporta i controller e il trasferimento di sistemi con un'ampia gamma di funzionalità di rilevamento. Un numero di queste funzionalità è comune tra i tipi di dispositivo. Ad esempio, mano rilevamento movimento controller ed entrambi forniscono un'azione 'select' e alla posizione 3D. Laddove possibile, l'API esegue il mapping di queste funzionalità comuni per le stesse proprietà nel SpatialInteractionSource.  Ciò consente alle applicazioni di supportare più facilmente un'ampia gamma di tipi di input. Nella tabella seguente vengono descritte le proprietà supportate e le modalità di confronto tra i tipi di input.

| Proprietà | Descrizione | Movimenti di HoloLens | Controller di movimento | Articolati e mani|
|--- |--- |--- |--- |--- |
| [SpatialInteractionSource::**Handedness**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.handedness) | A sinistra o destra / controller. | Non supportato | Supportato | Supportato |
| [SpatialInteractionSourceState::**IsSelectPressed**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isselectpressed) | Stato corrente del pulsante principale. | Indice puntato | Trigger | Tipo "relaxed" aria toccare (zoom indietro verticale) |
| [SpatialInteractionSourceState::**IsGrasped**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isgrasped) | Stato corrente del pulsante con quadratini di ridimensionamento. | Non supportato | Pulsante di quadratini di ridimensionamento | Zoom indietro o chiuso manualmente |
| [SpatialInteractionSourceState::**IsMenuPressed**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.ismenupressed) | Stato corrente del pulsante di menu.    | Non supportato | Pulsante di menu | Non supportato |
| [SpatialInteractionSourceLocation::**Position**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.position) | Percorso XYZ della posizione del triangolo di ridimensionamento o manualmente nel controller. | Percorso Palm | Triangolo di ridimensionamento posa posizione | Percorso Palm |
| [SpatialInteractionSourceLocation::**Orientation**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.orientation) | Quaternione che rappresenta l'orientamento della mano o triangolo rappresentare nel controller. | Non supportato | Orientamento posa triangolo di ridimensionamento | Orientamento Palm |
| [SpatialPointerInteractionSourcePose::**Position**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.position#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_Position) | Origine del raggio puntamento. | Non supportato | Supportato | Supportato |
| [SpatialPointerInteractionSourcePose::**ForwardDirection**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.forwarddirection#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_ForwardDirection) | Direzione del raggio puntamento. | Non supportato | Supportato | Supportato |

Alcune di queste proprietà non sono disponibili in tutti i dispositivi e l'API fornisce un mezzo per effettuare questa verifica. Ad esempio, è possibile esaminare i [SpatialInteractionSource::IsGraspSupported](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.isgraspsupported) proprietà per determinare se un'azione. é quindi disponibile per l'origine.

### <a name="grip-pose-vs-pointing-pose"></a>Triangolo di ridimensionamento posa confronto posa puntamento

Realtà mista di Windows supporta controller di movimento in un'ampia gamma di fattori di forma.  Supporta inoltre la mano articolati e sistemi di rilevamento.  Tutti questi sistemi dispongono di diverse relazioni tra la posizione di disponibilità e la direzione di "inoltro" naturale che le app devono usare per gli oggetti che puntano o rendreing a disposizione dell'utente.  Per supportare tutto ciò, esistono due tipi di può causare 3D fornite per entrambi i controller di rilevamento e movimenti della mano.  Il primo è posa triangolo di ridimensionamento, che rappresenta la posizione dell'utente mano.  Il secondo fa posa, che rappresenta un raggio di puntamento provenienti da parte dell'utente o un controller. Pertanto, se si desidera eseguire il rendering **manuale dell'utente** oppure **mantenuto un oggetto a disposizione dell'utente**, ad esempio un doppio taglio o gun, utilizzare posa il triangolo di ridimensionamento. Se si desidera raycast dal controller o manualmente, ad esempio quando l'utente sta **che punta all'interfaccia utente** , usare il puntamento posa.

È possibile accedere la **posa triangolo** tramite [SpatialInteractionSourceState::Properties::TryGetLocation(...) ](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties.trygetlocation#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_).  Viene definito come segue:
* Il **afferrare posizione**: Il centroide palm quando tenendo naturalmente, il controller è regolato sinistro o destro da allineare al centro la posizione all'interno del triangolo di ridimensionamento.
* Il **afferrare asse a destra dell'orientamento**: Quando si apre completamente la mano per formare una posa flat con un dito di 5, il raggio è normale che palm (in avanti dal palmo a sinistra, con le versioni precedenti dal palmo a destra)
* Il **afferrare asse diretta dell'orientamento**: Quando si chiude la mano parzialmente (come se che contiene il controller), il raggio che punta "forward" tramite il tubo costituita dalle dita non thumb.
* Il **afferrare orientamento di asse**: L'asse verticale in cui è inclusa per le definizioni di destra e l'inoltro.

È possibile accedere la **puntatore posa** attraverso [SpatialInteractionSourceState::Properties::TryGetLocation (...):: SourcePointerPose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose) o [SpatialInteractionSourceState:: TryGetPointerPose (...):: TryGetInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_).

## <a name="controller-specific-input-properties"></a>Proprietà di input specifici dei controller
Per i controller, il SpatialInteractionSource ha una proprietà di Controller con funzionalità aggiuntive.
* **HasThumbstick:** Se true, il controller ha una levetta. Esaminare i [ControllerProperties](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties) proprietà SpatialInteractionSourceState per acquisire il thumbstick x e i valori y (ThumbstickX e ThumbstickY), nonché lo stato di premuto (IsThumbstickPressed).
* **HasTouchpad:** Se true, il controller ha il touchpad. Esaminare la proprietà ControllerProperties di SpatialInteractionSourceState per acquisire il touchpad x e y (TouchpadX e TouchpadY), i valori e per sapere se l'utente tocca il riquadro (IsTouchpadTouched) e se essi sono premendo il touchpad verso il basso ( IsTouchpadPressed).
* **SimpleHapticsController:** L'API SimpleHapticsController per il controller consente di esaminare le funzionalità haptics del controller e permette anche di controllare l'implementazione del feedback aptico.

Si noti che l'intervallo per touchpad e thumbstick è -1 e 1 per entrambi gli assi (dal basso verso l'alto e da sinistra a destra). L'intervallo per il trigger analogico, che è possibile accedere tramite la proprietà SpatialInteractionSourceState::SelectPressedValue, ha un intervallo di 0 e 1. Un valore di 1 è correlata con IsSelectPressed quali uguale a true. qualsiasi altro valore mette in correlazione con IsSelectPressed quali uguale a false.

## <a name="articulated-hand-tracking"></a>Mano articolati e rilevamento
L'API di realtà mista di Windows fornisce supporto completo per le mani articolati e rilevamento, ad esempio in 2 HoloLens. Mano articolati e di rilevamento è utilizzabile per implementare i modelli di input di punto di commit e manipolazione diretta nelle applicazioni. Può essere utilizzato anche per creare interazioni completamente personalizzate.

### <a name="hand-skeleton"></a>Scheletro di mano
Mano articolati e di rilevamento fornisce una struttura comune 25 che consente a molti tipi diversi di interazioni.  Lo scheletro fornisce giunti a 5 per l'indice/intermedio/anello/little dita giunti a 4 per il controllo thumb e 1 polso giunto.  La giunzione polso funge da base della gerarchia. L'immagine seguente illustra il layout della struttura.

![Scheletro di mano](images/hand-skeleton.png)

Nella maggior parte dei casi, ogni attività di collaborazione è denominato base ossa da essa rappresentato.  Poiché sono presenti due ossa in ogni attività di collaborazione, usiamo una convenzione di denominazione ogni attività di collaborazione basata su ossa figlio nel percorso specificato.  Ossa figlio viene definito come ossa distante polso.  Ad esempio, è il "indice Proximal" joint contiene la posizione iniziale dell'ossa proximal indice e l'orientamento di tale ossa.  Non contiene la posizione finale di ossa.  Se è necessario che, si otterrebbe lo dal successivo comune nella gerarchia, il "indice intermedio" comune.

Oltre i 25 giunti gerarchici, il sistema fornisce un joint palm.  Palmo non è in genere considerato parte della struttura di base.  Viene fornito solo come un modo pratico per ottenere una posizione e l'orientamento complessivo la mano.

Le informazioni seguenti viene fornite per ogni attività di collaborazione:

| Nome | Descrizione |
|--- |--- |
|Posizione | 3D posizione del punto di giunzione, disponibile in qualsiasi sistema di coordinate richiesta. |
|Orientation | Orientamento 3D di ossa, disponibile in qualsiasi richiesta del sistema di coordinate. |
|Raggio | Distanza all'area dell'interfaccia in corrispondenza della posizione comune. È utile per l'ottimizzazione di interazioni dirette o visualizzazioni che si basano sulla larghezza di un dito. |
|Precisione | Fornisce un suggerimento su quanta fiducia scelga di sistema sulle informazioni della giunzione. |

È possibile accedere ai dati scheletro manualmente tramite una funzione nel [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate).  La funzione viene chiamata [TryGetHandPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygethandpose#Windows_UI_Input_Spatial_SpatialInteractionSourceState_TryGetHandPose), e restituisce un oggetto denominato [HandPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handpose).  Se l'origine non supporta le mani articolati e, questa funzione restituirà null.  Dopo aver creato un HandPose, è possibile ottenere dati joint correnti chiamando [TryGetJoint](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handpose.trygetjoint#Windows_Perception_People_HandPose_TryGetJoint_Windows_Perception_Spatial_SpatialCoordinateSystem_Windows_Perception_People_HandJointKind_Windows_Perception_People_JointPose__), con il nome dell'attività di collaborazione si è interessati.  I dati vengono restituiti come una [JointPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.jointpose) struttura.  Il codice seguente ottiene la posizione del suggerimento dito indice. La variabile *currentState* rappresenta un'istanza di [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate).

```cpp
using namespace winrt::Windows::Perception::People;
using namespace winrt::Windows::Foundation::Numerics;

auto handPose = currentState.TryGetHandPose();
if (handPose)
{
    JointPose joint;
    if (handPose.TryGetJoint(desiredCoordinateSystem, HandJointKind::IndexTip, joint))
    {
        float3 indexTipPosition = joint.Position;

        // Do something with the index tip position
    }
}
```

### <a name="hand-mesh"></a>Rete mesh di mano

L'icona della mano articolati e API di rilevamento consente una mesh di mano completamente deformabile triangolare.  Questa trama può deform in tempo reale con lo scheletro di mano e risulta utile per la visualizzazione, nonché le tecniche avanzate fisica.  Per accedere a mesh manualmente, è necessario creare prima di tutto una [HandMeshObserver](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handmeshobserver) oggetto chiamando [TryCreateHandMeshObserverAsync](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync) sul [SpatialInteractionSource](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource).  Ciò è sufficiente essere eseguito una volta per ogni origine, in genere la prima volta che viene visualizzato.  Ciò significa che è possibile chiamare questa funzione per creare un oggetto HandMeshObserver ogni volta che una mano passa il campo di visualizzazione.  Si tratta di una funzione asincrona, pertanto sarà necessario gestire un po' di concorrenza qui.  Una volta disponibile, è possibile porre l'oggetto HandMeshObserver per il buffer di triangolo indice chiamando [GetTriangleIndices](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handmeshobserver.gettriangleindices#Windows_Perception_People_HandMeshObserver_GetTriangleIndices_System_UInt16___).  Gli indici di non modificare frame tramite cornice, pertanto è possibile ottenerle una sola volta e memorizzarli nella cache per la durata dell'origine.  Gli indici sono disponibili nell'ordine dei vertici in senso orario.

Il codice seguente attiva un std::thread scollegato per creare l'osservatore mesh ed estrae l'index buffer dopo l'osservatore mesh è disponibile.  Viene avviato da una variabile denominata *currentState*, che è un'istanza del [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) che rappresenta una mano rilevata.

```cpp
using namespace Windows::Perception::People;

std::thread createObserverThread([this, currentState]()
{
    HandMeshObserver newHandMeshObserver = currentState.Source().TryCreateHandMeshObserverAsync().get();
    if (newHandMeshObserver)
    {
        unsigned indexCount = newHandMeshObserver.TriangleIndexCount();
        vector<unsigned short> indices(indexCount);
        newHandMeshObserver.GetTriangleIndices(indices);

        // Save the indices and handMeshObserver for later use - and use a mutex to synchronize access if needed!
     }
});
createObserverThread.detach();
```
Avvio di un thread scollegato è solo un'opzione per la gestione delle chiamate async.  In alternativa, è possibile usare le nuove [co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) funzionalità supportate da C++/WinRT.

Dopo aver creato un oggetto HandMeshObserver, è consigliabile tenere premuto su di esso per tutta la durata relativa SpatialInteractionSource corrispondente è attivo.  Quindi ogni fotogramma, è possibile richiedere il buffer dei vertici più recente che rappresenta l'icona della mano chiamando [GetVertexStateForPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handmeshobserver.getvertexstateforpose) e passando un [HandPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handpose) istanza che rappresenta la posa che si desidera che i vertici per.  Ogni vertice nel buffer con una posizione e una normale.  Ecco un esempio di come ottenere il set corrente di vertici per una rete mesh di mano.  Come in precedenza, il *currentState* variabile rappresenta un'istanza di [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate).

```cpp
using namespace winrt::Windows::Perception::People;

auto handPose = currentState.TryGetHandPose();
if (handPose)
{
    std::vector<HandMeshVertex> vertices(handMeshObserver.VertexCount());
    auto vertexState = handMeshObserver.GetVertexStateForPose(handPose);
    vertexState.GetVertices(vertices);

    auto meshTransform = vertexState.CoordinateSystem().TryGetTransformTo(desiredCoordinateSystem);
    if (meshTransform != nullptr)
    {
        // Do something with the vertices and mesh transform, along with the indices that you saved earlier
    }
}
```

A differenza delle scheletro giunzioni, l'API di rete mesh di disponibilità non consentono di specificare un sistema di coordinate per i vertici.  Al contrario, il [HandMeshVertexState](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handmeshvertexstate) specifica il sistema di coordinate dei vertici forniti in.  È quindi possibile ottenere una trasformazione mesh chiamando [TryGetTransformTo](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem.trygettransformto#Windows_Perception_Spatial_SpatialCoordinateSystem_TryGetTransformTo_Windows_Perception_Spatial_SpatialCoordinateSystem_) e specifica il sistema di coordinate desiderato.  È necessario usare questa trasformazione mesh ogni volta che procede con i vertici.  Questo approccio riduce il sovraccarico della CPU, in particolare se si usa solo il mesh per scopi di rendering.

## <a name="gaze-and-commit-composite-gestures"></a>Estasiati ed eseguire il Commit i movimenti compositi
Per le applicazioni usando il modello di input sguardo e commit, in particolare su HoloLens (gen primo), l'API di Input spaziali fornisce facoltativo [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx) che può essere utilizzato per abilitare i movimenti compositi costruita basati su di 'select' evento.  Dal routine interazioni dal SpatialInteractionManager a SpatialGestureRecognizer di ologramma, le app possono rilevare gli eventi di tocco, tenere premuto, manipolazione e navigazione in modo uniforme tra le mani, voce e spaziali dispositivi di input, senza dovere gestire le pressioni e rilascia manualmente.

SpatialGestureRecognizer esegue solo la minima risoluzione dell'ambiguità tra il set di gesti richiesti. Ad esempio, se vengono richiesti solo tocco, l'utente può tenere premuto il dito, purché che desiderano e tocco continueranno a essere eseguiti. Se si richiede sia toccare e tenere premuto, dopo circa un secondo di tenendo premuto il dito, l'azione alzerà di livello a un'esenzione e una scelta non verrà più eseguita.

Per usare SpatialGestureRecognizer, gestire il SpatialInteractionManager [InteractionDetected](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected) evento e il SpatialPointerPose esposte sono quadratini di ridimensionamento. Usare ray head sguardo dell'utente da questo posa da intersecare con l'ologrammi e trame area nelle vicinanze dell'utente, per poter determinare ciò che l'utente non sia progettata per interagire con. Quindi, instradare il SpatialInteraction negli argomenti di evento per SpatialGestureRecognizer del ologrammi destinazione, con relativi [CaptureInteraction](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction) (metodo). Verrà avviata l'interpretazione di questa interazione in base al [SpatialGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings) impostata su tale riconoscimento al momento della creazione - o da [TrySetGestureSettings](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings).

Su HoloLens (prima di tutto di generazione), le interazioni e movimenti in genere devono derivare il targeting da sguardo head dell'utente, piuttosto che tentare per eseguire il rendering o interagire direttamente nella posizione dell'icona della mano. Dopo aver avviato un'interazione, relativi movimenti della mano consente di controllare il movimento, come con il movimento di manipolazione o la navigazione.

## <a name="see-also"></a>Vedere anche
* [Testa e occhio estasiati DirectX](gaze-in-directx.md)
* [Modello di input di manipolazione diretta](direct-manipulation.md)
* [Modello di input di punto di commit](point-and-commit.md)
* [Modello di input sguardo ed eseguire il commit](gaze-and-commit.md)
* [Controller del movimento](motion-controllers.md)

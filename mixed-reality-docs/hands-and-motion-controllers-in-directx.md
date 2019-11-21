---
title: Controller hands and Motion in DirectX
description: Guida per gli sviluppatori per l'uso del controllo della mano e dei controller di movimento nelle app DirectX native.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/30/2019
ms.topic: article
keywords: Hands, controller di movimento, DirectX, input, ologrammi
ms.openlocfilehash: 54eaacc3f0dccf728b5438c020a5efd7e0788251
ms.sourcegitcommit: 4081dc2356fec0ea3625f1d989689cfbbb3fcf5f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2019
ms.locfileid: "74203333"
---
# <a name="hands-and-motion-controllers-in-directx"></a>Controller hands and Motion in DirectX

Nella realtà mista di Windows, l'input del controller della mano e del [movimento](motion-controllers.md) viene gestito tramite le API di input spaziali, disponibile nello spazio dei nomi [Windows. UI. input. Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial) . In questo modo è possibile gestire con facilità azioni comuni, come **Select** , che vengono stampate nello stesso modo tra le mani e i controller di movimento.

## <a name="getting-started"></a>Attività iniziali

Per accedere all'input spaziale in realtà mista di Windows, iniziare con l'interfaccia SpatialInteractionManager.  È possibile accedere a questa interfaccia chiamando [SpatialInteractionManager:: GetForCurrentView](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getforcurrentview), in genere talvolta durante l'avvio dell'app.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

SpatialInteractionManager interactionManager = SpatialInteractionManager::GetForCurrentView();
```

Il processo di SpatialInteractionManager consente di fornire l'accesso a [SpatialInteractionSources](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource), che rappresentano un'origine di input.  Sono disponibili tre tipi di SpatialInteractionSources nel sistema.
* **Hand** rappresenta la mano rilevata da un utente. Le origini della mano offrono funzionalità diverse in base al dispositivo, a partire da movimenti di base su HoloLens fino al rilevamento manuale completo su HoloLens 2. 
* Il **controller** rappresenta un controller di movimento associato. I controller di movimento possono offrire un'ampia gamma di funzionalità.  Ad esempio: selezionare trigger, pulsanti di menu, pulsanti di comprensione, touchpad e ThumbSticks.
* **Voice** rappresenta le parole chiave rilevate dal sistema vocale dell'utente. Questa origine, ad esempio, inserisce una selezione stampa e rilascia ogni volta che l'utente dice "Select".

I dati per fotogramma per un'origine sono rappresentati dall'interfaccia [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) . Esistono due modi diversi per accedere a questi dati, a seconda che si desideri usare un modello basato sugli eventi o sul polling nell'applicazione.

### <a name="event-driven-input"></a>Input guidato dagli eventi
SpatialInteractionManager fornisce una serie di eventi che l'app è in grado di ascoltare.  Alcuni esempi includono [SourcePressed](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed), [SourceReleased](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased) e [SourceUpdated](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated).

Il codice seguente, ad esempio, associa un gestore eventi denominato MyApp:: OnSourcePressed all'evento SourcePressed.  Ciò consente all'app di rilevare le pressioni su qualsiasi tipo di origine interazione.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

auto interactionManager = SpatialInteractionManager::GetForCurrentView();
interactionManager.SourcePressed({ this, &MyApp::OnSourcePressed });

```

Questo evento premuto viene inviato all'app in modo asincrono, insieme al SpatialInteractionSourceState corrispondente nel momento in cui si è verificato il clic. È possibile che l'app o il motore di gioco voglia eseguire immediatamente un'elaborazione oppure accodare i dati dell'evento nella routine di elaborazione dell'input. Ecco una funzione del gestore eventi per l'evento SourcePressed, che Mostra come controllare se è stato premuto il pulsante Seleziona.

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

Il codice sopra riportato controlla solo la pressione ' Select ', che corrisponde all'azione principale del dispositivo. Gli esempi includono l'operazione di AirTap in HoloLens o il pull del trigger in un controller di movimento.  Le pressioni ' Select ' rappresentano l'intenzione dell'utente di attivare l'ologramma di destinazione.  L'evento SourcePressed viene attivato per una serie di pulsanti e movimenti diversi ed è possibile controllare altre proprietà nel SpatialInteractionSource per verificare i casi.

### <a name="polling-based-input"></a>Input basato sul polling
È anche possibile usare SpatialInteractionManager per eseguire il polling dello stato corrente dell'input di ogni frame.  A tale scopo, è sufficiente chiamare [GetDetectedSourcesAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp) ogni frame.  Questa funzione restituisce una matrice contenente un [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) per ogni [SpatialInteractionSource](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource)attivo. Ciò significa uno per ogni controller di movimento attivo, uno per ogni mano registrata e uno per il riconoscimento vocale se è stato recentemente pronunciato un comando ' Select '. È quindi possibile esaminare le proprietà in ogni SpatialInteractionSourceState per guidare l'input nell'applicazione. 

Di seguito è riportato un esempio di come verificare l'azione ' Select ' usando il metodo di polling. Si noti che la variabile di *stima* rappresenta un oggetto [HolographicFramePrediction](https://docs.microsoft.com//uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) , che può essere ottenuto da [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe).

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

Ogni SpatialInteractionSource dispone di un ID, che è possibile usare per identificare nuove origini e correlare le origini esistenti dal frame al frame.  A mano viene assegnato un nuovo ID ogni volta che lasciano e si immette il FOV, ma gli ID del controller rimangono statici per la durata della sessione.  È possibile usare gli eventi in SpatialInteractionManager, ad esempio [SourceDetected](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcedetected) e [SourceLost](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcelost), per reagire quando le mani entrano o lasciano la visualizzazione del dispositivo o quando i controller di movimento sono accesi o spenti oppure sono abbinati o non abbinati.

### <a name="predicted-vs-historical-poses"></a>Pose stimate rispetto alla cronologia
Si noti che GetDetectedSourcesAtTimestamp ha un parametro timestamp. Ciò consente di richiedere lo stato e di porre dati stimati o cronologici, consentendo di correlare le interazioni spaziali con altre origini di input. Ad esempio, quando si esegue il rendering della posizione della mano nel frame corrente, è possibile passare il timestamp stimato fornito da [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe). In questo modo, il sistema è in grado di eseguire la stima della posizione della mano per allinearsi strettamente all'output del frame di cui è stato eseguito il rendering, riducendo

Tuttavia, tale posizione stimata non produce un raggio di puntamento ideale per la destinazione con un'origine interazione. Ad esempio, quando viene premuto un pulsante del controller di movimento, può essere necessario fino a 20ms per l'evento per propagarsi attraverso la tecnologia Bluetooth al sistema operativo. Analogamente, dopo che un utente ha eseguito un movimento di mano, è possibile che si verifichi una certa quantità di tempo prima che il sistema rilevi il gesto e l'app esegua il polling. Nel momento in cui l'app esegue il polling di una modifica dello stato, le pose Head e Hand usate per la destinazione dell'interazione si sono effettivamente verificate in passato. Se la destinazione viene passata passando il timestamp corrente di HolographicFrame a GetDetectedSourcesAtTimestamp, la posizione verrà invece stimata in base al raggio di destinazione nel momento in cui il frame verrà visualizzato, che potrebbe essere maggiore di 20ms in futuro. Questa generazione futura è ideale per il *rendering* dell'origine interazione, ma costituisce un problema di tempo per la *destinazione* dell'interazione, in quanto la destinazione dell'utente si è verificata in precedenza.

Fortunatamente, gli eventi [SourcePressed](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed), [SourceReleased](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased) e [SourceUpdated](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated) forniscono lo [stato](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state) cronologico associato a ogni evento di input.  Questo include direttamente le rappresentazioni della sede e della mano cronologiche disponibili tramite [TryGetPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose), oltre a un [timestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.timestamp) cronologico che è possibile passare ad altre API per la correlazione con questo evento.

Ciò comporta le seguenti procedure consigliate per il rendering e la destinazione con le procedure e i controller di ogni frame:
* Per il **rendering della mano/controller** ogni frame, l'app deve eseguire il **polling** per la posizione **stimata in** base a ogni origine interazione al momento del fotone del frame corrente.  È possibile eseguire il polling per tutte le origini interazione chiamando [GetDetectedSourcesAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp) ogni frame, passando il timestamp stimato fornito da [HolographicFrame:: CurrentPrediction](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.currentprediction).
* Per la selezione di **mano/controller** su una pressione o un rilascio, l'app deve gestire **gli eventi**premuti o rilasciati, Raycasting in base all'intestazione o alla mano **storica** per quell'evento. Si ottiene questo raggio di destinazione gestendo l'evento [SourcePressed](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed) o [SourceReleased](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased) , ottenendo la proprietà [state](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state) dagli argomenti dell'evento e quindi chiamando il relativo metodo [TryGetPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) .

## <a name="cross-device-input-properties"></a>Proprietà input tra dispositivi
L'API SpatialInteractionSource supporta i controller e i sistemi di rilevamento manuale con una vasta gamma di funzionalità. Alcune di queste funzionalità sono comuni tra i tipi di dispositivi. Ad esempio, il rilevamento manuale e i controller di movimento forniscono un'azione ' Select ' e una posizione 3D. Laddove possibile, l'API esegue il mapping di queste funzionalità comuni alle stesse proprietà in SpatialInteractionSource.  Ciò consente alle applicazioni di supportare più facilmente un'ampia gamma di tipi di input. Nella tabella seguente vengono descritte le proprietà supportate e il modo in cui vengono confrontate tra i tipi di input.

| Proprietà | Descrizione | Movimenti di HoloLens (1a generazione) | Controller di movimento | Mano articolata|
|--- |--- |--- |--- |--- |
| [SpatialInteractionSource::**manualità**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource.handedness) | A destra o a sinistra/controller. | Non supportato | Supportato | Supportato |
| [SpatialInteractionSourceState::**IsSelectPressed**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isselectpressed) | Stato corrente del pulsante primario. | Rubinetto aereo | Trigger | Tocco aria rilassato (tocco verticale) |
| [SpatialInteractionSourceState:: è stato**afferrato**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isgrasped) | Stato corrente del pulsante di cattura. | Non supportato | Pulsante di cattura | Pinza o chiusa |
| [SpatialInteractionSourceState::**IsMenuPressed**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.ismenupressed) | Stato corrente del pulsante di menu.    | Non supportato | Pulsante di menu | Non supportato |
| [SpatialInteractionSourceLocation::**position**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.position) | Posizione XYZ della mano o della posizione del grip sul controller. | Percorso Palm | Posizione del grip | Percorso Palm |
| [SpatialInteractionSourceLocation::**Orientation**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.orientation) | Quaternione che rappresenta l'orientamento della mano o della posizione del grip sul controller. | Non supportato | Orientamento della posizione del grip | Orientamento Palm |
| [SpatialPointerInteractionSourcePose::**position**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.position#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_Position) | Origine del raggio di puntamento. | Non supportato | Supportato | Supportato |
| [SpatialPointerInteractionSourcePose::**ForwardDirection**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.forwarddirection#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_ForwardDirection) | Direzione del raggio di puntamento. | Non supportato | Supportato | Supportato |

Alcune delle proprietà precedenti non sono disponibili in tutti i dispositivi e l'API fornisce un mezzo per testarlo. Ad esempio, è possibile esaminare la proprietà [SpatialInteractionSource:: IsGraspSupported](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource.isgraspsupported) per determinare se l'origine fornisce un'azione di comprensione.

### <a name="grip-pose-vs-pointing-pose"></a>Posa del grip e puntamento

La realtà mista di Windows supporta i controller di movimento in diversi fattori di forma.  Supporta anche sistemi di rilevamento a mano articolati.  Tutti questi sistemi hanno relazioni diverse tra la posizione della mano e la direzione naturale "Avanti" che le app devono usare per puntare o eseguire il rendering degli oggetti nella mano dell'utente.  Per supportare questa operazione, sono disponibili due tipi di istanze 3D per i controller di rilevamento e movimento della mano.  Il primo è costituito da grip, che rappresenta la posizione della mano dell'utente.  Il secondo sta puntando a pose, che rappresenta un raggio di puntamento che origina dalla mano o dal controller dell'utente. Se quindi si desidera eseguire il rendering **della mano dell'utente** o di **un oggetto contenuto nella mano dell'utente**, ad esempio una spada o una pistola, utilizzare il grip. Se si desidera Raycast dal controller o dalla mano, ad esempio quando l'utente **punta all'interfaccia utente** , utilizzare la posizione di puntamento.

È possibile accedere al **grip** con [SpatialInteractionSourceState::P oprietà:: TryGetLocation (...)](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties.trygetlocation#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_).  Viene definito come segue:
* **Posizione del grip**: il centro della palma quando si tiene il controller in modo naturale, regolato a sinistra o a destra per centrare la posizione all'interno del grip.
* L' **asse destro dell'orientamento del grip**: quando si apre completamente la mano per formare una formula a 5 dita piatta, il raggio normale per la Palma (in avanti dal palmo sinistro e viceversa)
* **Asse di avanzamento dell'orientamento del grip**: quando si chiude parzialmente la mano (come se si utilizzasse il controller), il raggio che punta "in poi" attraverso il tubo formato dalle dita non Thumb.
* **Asse verticale dell'orientamento del grip**: l'asse verso l'alto implicato dalle definizioni di destra e di avanzamento.

È possibile accedere al **puntatore** con [SpatialInteractionSourceState::P oprietà:: TryGetLocation (...):: SourcePointerPose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose) o [SpatialInteractionSourceState:: TryGetPointerPose (...):: TryGetInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_).

## <a name="controller-specific-input-properties"></a>Proprietà di input specifiche del controller
Per i controller, SpatialInteractionSource dispone di una proprietà Controller con funzionalità aggiuntive.
* **HasThumbstick:** Se true, il controller dispone di un levetta. Esaminare la proprietà [ControllerProperties](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties) di SpatialInteractionSourceState per acquisire i valori levetta x e y (ThumbstickX e ThumbstickY), così come lo stato premuto (IsThumbstickPressed).
* **HasTouchpad:** Se true, il controller dispone di un touchpad. Esaminare la proprietà ControllerProperties di SpatialInteractionSourceState per acquisire i valori x e y del touchpad (TouchpadX e Touchpady) e per verificare se l'utente sta toccando il riquadro (IsTouchpadTouched) e se preme il touchpad verso il basso ( IsTouchpadPressed).
* **SimpleHapticsController:** L'API SimpleHapticsController per il controller consente di esaminare le funzionalità haptics del controller e di controllare il feedback tattile.

Si noti che l'intervallo per touchpad e levetta è-1 a 1 per entrambi gli assi (dal basso verso l'alto e da sinistra a destra). L'intervallo per il trigger analogico, a cui si accede tramite la proprietà SpatialInteractionSourceState:: SelectPressedValue, ha un intervallo compreso tra 0 e 1. Il valore 1 è correlato a IsSelectPressed in modo che sia uguale a true; qualsiasi altro valore correlato a IsSelectPressed è uguale a false.

## <a name="articulated-hand-tracking"></a>Rilevamento a mano articolata
L'API di realtà mista di Windows fornisce il supporto completo per il rilevamento manuale articolato, ad esempio in HoloLens 2. Il rilevamento a mano articolata può essere usato per implementare la manipolazione diretta e i modelli di input Point-and-commit nelle applicazioni. Può essere usato anche per creare interazioni completamente personalizzate.

### <a name="hand-skeleton"></a>Scheletro mano
Il rilevamento a mano articolata offre una struttura a 25 forme che consente molti tipi diversi di interazioni.  La struttura fornisce 5 giunzioni per le barrette index/Middle/Ring/Little, 4 giunzioni per il pollice e 1 polso.  Il giunto del polso funge da base della gerarchia. Nell'immagine seguente viene illustrato il layout dello scheletro.

![Scheletro mano](images/hand-skeleton.png)

Nella maggior parte dei casi, ogni joint viene denominato in base all'osso che rappresenta.  Poiché sono presenti due ossa in ogni giunzione, viene usata una convenzione di denominazione di ogni joint in base all'osso figlio in tale posizione.  L'osso figlio viene definito come l'osso più a fondo.  Ad esempio, il giunto "index Prossimal" contiene la posizione iniziale dell'osso prossimale dell'indice e l'orientamento di tale osso.  Non contiene la posizione finale dell'osso.  Se necessario, è possibile ottenerlo dalla giunzione successiva nella gerarchia, ovvero il collegamento "index Intermediate".

Oltre ai 25 giunti gerarchici, il sistema fornisce un insieme di Palm.  Il Palm non è in genere considerato parte della struttura scheletrica.  Viene fornito solo come un modo pratico per ottenere la posizione e l'orientamento complessivi della mano.

Per ogni giunzione vengono fornite le informazioni seguenti:

| Nome | Descrizione |
|--- |--- |
|Posizione | posizione 3D del giunto, disponibile in qualsiasi sistema di coordinate richiesto. |
|Orientation | orientamento 3D dell'osso, disponibile in qualsiasi sistema di coordinate richiesto. |
|Raggio | Distanza dalla superficie dell'interfaccia in corrispondenza della posizione di giunzione. Utile per l'ottimizzazione di interazioni dirette o visualizzazioni basate sulla larghezza del dito. |
|Precisione | Fornisce un suggerimento sul modo in cui il sistema ritiene attendibile le informazioni di questo comune. |

È possibile accedere ai dati dello scheletro della mano tramite una funzione in [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate).  La funzione viene chiamata [TryGetHandPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygethandpose#Windows_UI_Input_Spatial_SpatialInteractionSourceState_TryGetHandPose)e restituisce un oggetto denominato [HandPose](https://docs.microsoft.com//uwp/api/windows.perception.people.handpose).  Se l'origine non supporta le lancette articolate, questa funzione restituirà null.  Quando si dispone di un HandPose, è possibile ottenere i dati comuni correnti chiamando [TryGetJoint](https://docs.microsoft.com//uwp/api/windows.perception.people.handpose.trygetjoint#Windows_Perception_People_HandPose_TryGetJoint_Windows_Perception_Spatial_SpatialCoordinateSystem_Windows_Perception_People_HandJointKind_Windows_Perception_People_JointPose__), con il nome del giunto a cui si è interessati.  I dati vengono restituiti come struttura [JointPose](https://docs.microsoft.com//uwp/api/windows.perception.people.jointpose) .  Il codice seguente ottiene la posizione del suggerimento per il dito dell'indice. La variabile *CurrentState* rappresenta un'istanza di [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate).

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

### <a name="hand-mesh"></a>Mesh mano

L'API di rilevamento a mano articolata consente un reticolo a mano triangolo completamente deformabile.  Questa mesh può deformarsi in tempo reale insieme allo scheletro della mano ed è utile per la visualizzazione, nonché per tecniche di fisica avanzate.  Per accedere alla rete a mano, è necessario innanzitutto creare un oggetto [HandMeshObserver](https://docs.microsoft.com//uwp/api/windows.perception.people.handmeshobserver) chiamando [TryCreateHandMeshObserverAsync](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync) in [SpatialInteractionSource](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource).  Questa operazione deve essere eseguita solo una volta per origine, in genere la prima volta che viene visualizzata.  Questo significa che si chiamerà questa funzione per creare un oggetto HandMeshObserver ogni volta che una mano entra nell'oggetto FOV.  Si noti che si tratta di una funzione asincrona, quindi è necessario gestire un po' di concorrenza.  Una volta disponibile, è possibile chiedere all'oggetto HandMeshObserver per il buffer dell'indice del triangolo chiamando [GetTriangleIndices](https://docs.microsoft.com//uwp/api/windows.perception.people.handmeshobserver.gettriangleindices#Windows_Perception_People_HandMeshObserver_GetTriangleIndices_System_UInt16___).  Gli indici non cambiano frame rispetto al frame, quindi è possibile ottenerli una volta e memorizzarli nella cache per la durata dell'origine.  Gli indici vengono specificati in ordine di avvolgimento in senso orario.

Il codice seguente consente di avviare un std:: thread scollegato per creare l'osservatore mesh ed estrarre il buffer dell'indice dopo che l'osservatore mesh è disponibile.  Inizia da una variabile denominata *CurrentState*, che è un'istanza di [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) che rappresenta una mano rilevata.

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
L'avvio di un thread scollegato è solo un'opzione per la gestione delle chiamate asincrone.  In alternativa, è possibile usare la nuova funzionalità di [co_await](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) supportata C++da/WinRT.

Quando si dispone di un oggetto HandMeshObserver, è necessario mantenerlo per la durata di attivazione del SpatialInteractionSource corrispondente.  Ogni frame, quindi, può essere richiesto per l'ultimo buffer di vertex che rappresenta la mano chiamando [GetVertexStateForPose](https://docs.microsoft.com//uwp/api/windows.perception.people.handmeshobserver.getvertexstateforpose) e passando un'istanza di [HandPose](https://docs.microsoft.com//uwp/api/windows.perception.people.handpose) che rappresenta la posa per la quale si desiderano i vertici.  Ogni vertice nel buffer ha una posizione e una normale.  Di seguito è riportato un esempio di come ottenere il set corrente di vertici per una mesh a mano.  Esattamente come in precedenza, la variabile *CurrentState* rappresenta un'istanza di [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate).

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

Diversamente dalle giunzioni di scheletro, l'API della mesh mano non consente di specificare un sistema di coordinate per i vertici.  Il [HandMeshVertexState](https://docs.microsoft.com//uwp/api/windows.perception.people.handmeshvertexstate) specifica invece il sistema di coordinate in cui vengono forniti i vertici.  È quindi possibile ottenere una trasformazione mesh chiamando [TryGetTransformTo](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem.trygettransformto#Windows_Perception_Spatial_SpatialCoordinateSystem_TryGetTransformTo_Windows_Perception_Spatial_SpatialCoordinateSystem_) e specificando il sistema di coordinate desiderato.  È necessario usare questa trasformazione mesh ogni volta che si lavora con i vertici.  Questo approccio riduce il sovraccarico della CPU, soprattutto se si usa solo la rete a scopo di rendering.

## <a name="gaze-and-commit-composite-gestures"></a>Movimenti compositi di sguardi e commit
Per le applicazioni che usano il modello di input con sguardo e commit, in particolare in HoloLens (First Gen), l'API di input spaziale fornisce un [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx) facoltativo che può essere usato per abilitare i movimenti compositi compilati sopra l'evento ' Select '.  Tramite il routing delle interazioni dal SpatialInteractionManager al SpatialGestureRecognizer di un ologramma, le app possono rilevare gli eventi di tocco, attesa, manipolazione ed esplorazione in modo uniforme tra le mani, le voci e i dispositivi di input spaziali, senza dover gestire le pressioni. e rilascia manualmente.

SpatialGestureRecognizer esegue solo la disambiguazione minima tra il set di movimenti richiesto. Ad esempio, se si richiede solo il tocco, l'utente può mantenere il dito verso il basso fino a quando si desidera e si verificherà ancora un tocco. Se si richiedono sia toccare che tenere premuto, dopo circa un secondo di tenere premuto il dito, il movimento produrrà a una sospensione e il tocco non si verificherà più.

Per usare SpatialGestureRecognizer, gestire l'evento [InteractionDetected](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected) di SpatialInteractionManager e fare in modo che i SpatialPointerPose esposti siano presenti. Usare il raggio di sguardi dell'utente da questa posa per intersecare gli ologrammi e le mesh di superficie nell'ambiente dell'utente, in modo da determinare gli elementi che l'utente intende interagire. Quindi, indirizzare il SpatialInteraction negli argomenti dell'evento al SpatialGestureRecognizer dell'ologramma di destinazione usando il metodo [CaptureInteraction](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction) . Questa operazione inizia a interpretare l'interazione in base al set di [SpatialGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings) in quel riconoscimento al momento della creazione, o [TrySetGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings).

In HoloLens (First Gen), le interazioni e i movimenti dovrebbero in genere derivare il loro targeting da quello degli utenti, anziché tentare di eseguire il rendering o interagire direttamente nella posizione della mano. Una volta avviata un'interazione, è possibile usare i movimenti relativi della mano per controllare il movimento, come per il gesto di manipolazione o spostamento.

## <a name="see-also"></a>Vedi anche
* [Puntamento con la testa e sguardo fisso in DirectX](gaze-in-directx.md)
* [Modello di input di manipolazione diretta](direct-manipulation.md)
* [Modello di input Point-and-commit](point-and-commit.md)
* [Modello di input sguardo e commit](gaze-and-commit.md)
* [Controller del movimento](motion-controllers.md)

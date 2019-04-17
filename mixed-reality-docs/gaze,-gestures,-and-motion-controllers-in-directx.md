---
title: Sguardo, gesti e controller di movimento in DirectX
description: La combinazione di input provenienti da sguardo, gesti e controller di movimento, è possibile abilitare un utente di inserire un ologrammi nell'app.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: sguardo, gesti, i controller di movimento, directx, input, vntana
ms.openlocfilehash: 7cee3d3d7fbcd903eae0376e205034b9cc4ead3b
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605090"
---
# <a name="gaze-gestures-and-motion-controllers-in-directx"></a>Sguardo, gesti e controller di movimento in DirectX

Se si intende compilare direttamente all'inizio della piattaforma, è necessario gestire l'input proveniente dall'utente, ad esempio in cui l'utente esegue la ricerca tramite [sguardo head](gaze.md) e ciò che l'utente ha selezionato con [movimenti](gestures.md) o [controller di movimento](motion-controllers.md). La combinazione di questi formati di input, è possibile abilitare un utente di inserire un [ologrammi](hologram.md) nell'app. Il [modello di app holographic](creating-a-holographic-directx-project.md) presenta un esempio di facile utilizzo.

>[!NOTE]
>I frammenti di codice in questo articolo illustrano attualmente l'utilizzo di C++/CX invece di C + + 17 conformi C++/WinRT usato nel [ C++ modello di progetto holographic](creating-a-holographic-directx-project.md).  I concetti sono equivalenti per un C++progetto /WinRT, anche se è necessario convertire il codice.

## <a name="gaze-input"></a>Input sguardo fisso

Di accesso dell'utente [sguardo head](gaze.md), si utilizza il [SpatialPointerPose](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialpointerpose.aspx) tipo. Il modello di app holographic include per sguardo conoscenza di base del codice. Questo codice fornisce un vettore che puntano forward nell'intervallo tra gli occhi dell'utente, prendendo in considerazione la posizione del dispositivo e l'orientamento in un determinato [sistema di coordinate](coordinate-systems-in-directx.md).




```cpp
void SpinningCubeRenderer::PositionHologram(SpatialPointerPose^ pointerPose)
{
    if (pointerPose != nullptr)
    {
        // Get the gaze direction relative to the given coordinate system.
        const float3 headPosition    = pointerPose->Head->Position;
        const float3 headDirection   = pointerPose->Head->ForwardDirection;
    
        // The hologram is positioned two meters along the user's gaze direction.
        static const float distanceFromUser = 2.0f; // meters
        const float3 gazeAtTwoMeters        = headPosition + (distanceFromUser * headDirection);
    
        // This will be used as the translation component of the hologram's
        // model transform.
        SetPosition(gazeAtTwoMeters);
    }
}
```

Potrebbe essere necessario chiedere: ", Ma il sistema di coordinate da dove provengono?"

È possibile rispondere a questa domanda. Nel nostro AppMain **Update** funzione, viene elaborato un evento di input spaziale acquistando rispetto al sistema di coordinate per i nostri StationaryFrameOfReference. È importante ricordare che è stato creato il StationaryFrameOfReference quando si configura il [HolographicSpace](https://msdn.microsoft.com/library/windows/apps/windows.graphics.holographic.holographicspace.aspx), e il sistema di coordinate è stato acquisito all'inizio del [Update](rendering-in-directx.md).




```cpp
// Check for new input state since the last frame.
SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
if (pointerState != nullptr)
{
    // When a Pressed gesture is detected, the sample hologram will be repositioned
    // two meters in front of the user.
    m_spinningCubeRenderer->PositionHologram(
        pointerState->TryGetPointerPose(currentCoordinateSystem)
        );
}
```

Si noti che i dati sono associati a uno stato di puntatore di qualche tipo. È tutto da un evento di input spaziale. L'oggetto dati di evento include un sistema di coordinate, in modo che è sempre possibile correlare la direzione sguardo al momento dell'evento a qualsiasi sistema di coordinate spaziale, è necessario. In effetti, è necessario farlo per poter ottenere la posa puntatore.

> [!NOTE]
> Altre indicazioni specifiche su 2 HoloLens [presto](index.md#news-and-notes).

## <a name="gesture-and-motion-controller-input"></a>Controller di movimento e movimento di input

Nella realtà mista di Windows, sia a essere passate [movimenti](gestures.md) e [movimento controller](motion-controllers.md) vengono gestite tramite lo stesso input spaziali API, disponibili nel [Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial) spazio dei nomi. In questo modo è possibile gestire facilmente le azioni comuni, ad esempio **seleziona** preme allo stesso modo attraverso le mani sia i controller di movimento.

Esistono due livelli di API è possibile fare riferimento quando si gestiscono i movimenti o i controller di movimento in realtà mista:
* [Interazioni](gestures.md#the-two-core-gestures-of-hololens) ([SourcePressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed.aspx), [SourceReleased](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased.aspx) e [SourceUpdated](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated.aspx)), a cui si accede tramite un [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx)
* [I movimenti compositi](gestures.md#composite-gestures) ([Tapped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.tapped.aspx), tenere premuto, modifica, esplorazione), a cui si accede tramite un [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx)

### <a name="selectmenugrasptouchpadthumbstick-interactions-spatialinteractionmanager"></a>Interazioni di selezione/Menu /. é quindi/Touchpad/Thumbstick: SpatialInteractionManager

Per rilevare le pressioni a basso livello, versioni e sugli aggiornamenti tra le mani e dispositivi di input in realtà mista di Windows, iniziare da un [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx). Il SpatialInteractionManager dispone di un evento che informa l'app durante una mano o controller di movimento ha rilevato l'input.

Esistono tre tipi principali di SpatialInteractionSource, ognuno rappresentato da un valore SpatialInteractionSourceKind diverso:
* **Mano** rappresenta mano rilevato dell'utente. Origini disponibili sono disponibili solo su HoloLens.
* **Controller** rappresenta un controller di movimento associati. I controller di movimento possono offrire un'ampia gamma di funzionalità, ad esempio: Selezionare i trigger, pulsanti di Menu, pulsanti. é quindi, touchpad multipli e levette.
* **Voce** rappresenta la voce dell'utente a proposito di sistema ha rilevato le parole chiave. Verrà inserire una pressione Seleziona e rilasciare ogni volta che l'utente afferma "Select".

Per rilevare le pressioni tra qualsiasi di queste origini di interazione, è possibile gestire l'evento SourcePressed su SpatialInteractionManager in SpatialInputHandler.cpp:


```cpp
m_interactionManager = SpatialInteractionManager::GetForCurrentView();
    
// Bind a handler to the SourcePressed event.
m_sourcePressedEventToken =
    m_interactionManager->SourcePressed +=
        ref new TypedEventHandler<SpatialInteractionManager^, SpatialInteractionSourceEventArgs^>(
            bind(&SpatialInputHandler::OnSourcePressed, this, _1, _2)
            );
```

Questo evento premuto viene inviato all'App in modo asincrono. L'app o il motore di gioco potrebbe essere necessario eseguire alcune operazioni di elaborazione sin da subito oppure è possibile accodare i dati dell'evento nelle routine di elaborazione dell'input.

Il modello include una classe helper per iniziare a usare. Questo modello forgoes elaborazioni per motivi di semplicità di progettazione. La classe helper tiene traccia di se uno o più **Pressed** eventi si sono verificati dopo l'ultimo **Update** chiamare. Da SpatialInputHandler.cpp:




```cpp
void SpatialInputHandler::OnSourcePressed(SpatialInteractionManager^ sender, SpatialInteractionSourceEventArgs^ args)
{
    m_sourceState = args->State;
    
    //
    // TODO: In your app or game engine, rewrite this method to queue
    //       input events in your input class or event handler.
    //
}
```

Se, pertanto, restituisce il [SpatialInteractionSourceState](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) per l'evento di input più recente durante il successivo aggiornamento. Da SpatialInputHandler.cpp:




```cpp
// Checks if the user performed an input gesture since the last call to this method.
// Allows the main update loop to check for asynchronous changes to the user
// input state.
SpatialInteractionSourceState^ SpatialInputHandler::CheckForInput()
{
    SpatialInteractionSourceState^ sourceState = m_sourceState;
    m_sourceState = nullptr;
    return sourceState;
}
```

Si noti che il codice sopra riportato considererà tutti preme allo stesso modo, se l'utente esegue una replica primaria **selezionate** premere né una secondaria **dal Menu** o **afferrare** premere. Il **seleziona** press è una forma principale di interazione tra le mani, movimento controller e la voce attivate da una mano eseguendo un puntato, un controller di movimento con relativo grilletto primario premuto o l'utente è supportato Voice che informa che "Select". Selezionare pressioni rappresentano l'intenzione dell'utente per attivare l'ologrammi che di destinazione.

Ragionare su quale tipo di stampa è in corso, si modificherà il gestore dell'evento SpatialInteractionManager::SourceUpdated. Il nostro codice rileverà. é quindi preme (se disponibili) e usarli per riposizionare il cubo. Se. é quindi non sono disponibile, si userà invece pressioni Select.

Aggiungere le seguenti dichiarazioni di membro privato per SpatialInputHandler.h: 


```cpp
void OnSourceUpdated(
       Windows::UI::Input::Spatial::SpatialInteractionManager^ sender,
       Windows::UI::Input::Spatial::SpatialInteractionSourceEventArgs^ args);
   Windows::Foundation::EventRegistrationToken m_sourceUpdatedEventToken;
```

Aprire SpatialInputHandler.cpp. Aggiungere la registrazione di eventi seguente al costruttore: 


```cpp
m_sourceUpdatedEventToken =
       m_interactionManager->SourceUpdated +=
       ref new TypedEventHandler<SpatialInteractionManager^, SpatialInteractionSourceEventArgs^>(
           bind(&SpatialInputHandler::OnSourceUpdated, this, _1, _2)
           );
```

Questo è il codice del gestore eventi. Se l'origine di input sta riscontrando. é quindi, il puntatore posa verrà archiviata per il successivo ciclo di aggiornamento. In caso contrario, verrà verificata la pressione di un seleziona invece. Da SpatialInputHandler.cpp:




```cpp
void SpatialInputHandler::OnSourceUpdated(SpatialInteractionManager^ sender, SpatialInteractionSourceEventArgs^ args)
{
    if (args->State->Source->IsGraspSupported)
    {
        if (args->State->IsGrasped)
        {
            m_sourceState = args->State;
        }
    }
    else
    {
        if (args->State->IsSelectPressed)
        {
            m_sourceState = args->State;
        }
    }
}
```

Assicurarsi di annullare la registrazione il gestore eventi nel distruttore. Da SpatialInputHandler.cpp:


```cpp
m_interactionManager->SourceUpdated -= m_sourcePressedEventToken;
```

Ricompilare e ridistribuire. Il progetto di modello dovrebbe ora essere in grado di riconoscere le interazioni. é quindi riposizionare il cubo rotante.

L'API SpatialInteractionSource supporta i controller con un'ampia gamma di funzionalità. Nell'esempio illustrato in precedenza, viene verificato se sono supportata. é quindi prima di provare a usarlo. Il SpatialInteractionSource supporta le funzionalità facoltative seguenti oltre i comuni **seleziona** premere:
* **Pulsante di menu:** Verificare il supporto esaminando la proprietà IsMenuSupported. Se supportato, verificare i [SpatialInteractionSourceState::IsMenuPressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) proprietà per determinare se il pulsante di menu viene premuto.
* **Afferrare pulsante:** Verificare il supporto esaminando la proprietà IsGraspSupported. Se supportato, verificare i [SpatialInteractionSourceState::IsGrasped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) proprietà per sapere se sono attivato. é quindi.

Per i controller, il SpatialInteractionSource ha una proprietà di Controller con funzionalità aggiuntive.
* **HasThumbstick:** Se true, il controller ha una levetta. Esaminare i [ControllerProperties](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties) proprietà SpatialInteractionSourceState per acquisire il thumbstick x e i valori y (ThumbstickX e ThumbstickY), nonché lo stato di premuto (IsThumbstickPressed).
* **HasTouchpad:** Se true, il controller ha il touchpad. Esaminare la proprietà ControllerProperties di SpatialInteractionSourceState per acquisire il touchpad x e y (TouchpadX e TouchpadY), i valori e per sapere se l'utente tocca il riquadro (IsTouchpadTouched) e se essi sono premendo il touchpad verso il basso ( IsTouchpadPressed).
* **SimpleHapticsController:** L'API SimpleHapticsController per il controller consente di esaminare le funzionalità haptics del controller e permette anche di controllare l'implementazione del feedback aptico.

Si noti che l'intervallo per touchpad e thumbstick compreso tra -1 e 1 per entrambi gli assi (dal basso verso l'alto e da sinistra a destra). L'intervallo per il trigger analogico, che è possibile accedere tramite la proprietà SpatialInteractionSourceState::SelectPressedValue, ha un intervallo di 0 e 1. Un valore di 1 è correlata con IsSelectPressed quali uguale a true. qualsiasi altro valore mette in correlazione con IsSelectPressed quali uguale a false.

Si noti che per una mano e un controller, usando SpatialInteractionSourceState::Properties::TryGetLocation fornirà la posizione dell'utente manualmente, ciò è diverso dal posa puntatore che rappresenta ray puntamento del controller. Se si desidera disegnare qualcosa in corrispondenza della posizione di disponibilità, usare TryGetLocation. Se si desidera raycast tra la punta del controller, ottenere il raggio di puntamento da TryGetInteractionSourcePose sul SpatialPointerPose.

È possibile utilizzare anche gli altri eventi su SpatialInteractionManager, ad esempio SourceDetected e SourceLost, per rispondere al mani immettono o lasciano il dispositivo visualizzazione o quando si sposta o rifiutare la posizione di pronta (dito indice generato con rollforward palm) o quando il movimento i controller sono per attivare/disattivare o non sono abbinate/abbinati.

### <a name="grip-pose-vs-pointing-pose"></a>Triangolo di ridimensionamento posa confronto posa puntamento

Realtà mista di Windows supporta controller di movimento in un'ampia gamma di fattori di forma, con la progettazione del ogni controller che differiscono per la relazione tra la posizione dell'utente mano e naturale "inoltro" direzione tale app deve usare per fare riferimento durante il rendering di controller.

Per rappresentare meglio questi controller, esistono due tipi di può causare che è possibile esaminare per ogni origine di interazione:
* Il **triangolo posa**, che rappresenta la posizione di palmo di una mano rilevata da un HoloLens o palmo che contiene un controller di movimento.
    * In coinvolgenti auricolari, questo posa è particolarmente utile per eseguire il rendering **manuale dell'utente** oppure **mantenuto un oggetto a disposizione dell'utente**, ad esempio un doppio taglio o gun.
    * Il **afferrare posizione**: Il centroide palm quando tenendo naturalmente, il controller è regolato sinistro o destro da allineare al centro la posizione all'interno del triangolo di ridimensionamento.
    * Il **afferrare asse a destra dell'orientamento**: Quando si apre completamente la mano per formare una posa flat con un dito di 5, il raggio è normale che palm (in avanti dal palmo a sinistra, con le versioni precedenti dal palmo a destra)
    * Il **afferrare asse diretta dell'orientamento**: Quando si chiude la mano parzialmente (come se che contiene il controller), il raggio che punta "forward" tramite il tubo costituita dalle dita non thumb.
    * Il **afferrare orientamento di asse**: L'asse verticale in cui è inclusa per le definizioni di destra e l'inoltro.
    * È possibile accedere a posa il triangolo di ridimensionamento tramite [SpatialInteractionSourceState.Properties.TryGetLocation(...) ](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_).
* Il **posa puntatore**, che rappresenta la punta del controller in avanti che punta.
    * Questo posa è particolarmente utile per raycast quando **che punta all'interfaccia utente** quando si esegue il rendering di modello controller stesso.
    * È possibile accedere la posa puntatore tramite [SpatialInteractionSourceState.Properties.TryGetLocation(...). SourcePointerPose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose) o [SpatialInteractionSourceState.TryGetPointerPose(...). TryGetInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_).

### <a name="composite-gestures-spatialgesturerecognizer"></a>Movimenti compositi: SpatialGestureRecognizer

Oggetto [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx) interpreta le interazioni dell'utente da mani, i controller di movimento e il comando "Seleziona" casella vocale per gli eventi di movimento spaziali surface, destinazione a cui gli utenti usando le sguardo head.

I movimenti spaziali sono una forma di chiave di input per le app di realtà mista di Windows. Dal routine interazioni dal SpatialInteractionManager a SpatialGestureRecognizer di ologramma, le app possono rilevare gli eventi di tocco, tenere premuto, manipolazione e navigazione in modo uniforme tra le mani, voce e spaziali dispositivi di input, senza dovere gestire le pressioni e rilascia manualmente.

SpatialGestureRecognizer esegue solo la minima risoluzione dell'ambiguità tra il set di gesti richiesti. Ad esempio, se vengono richiesti solo tocco, l'utente può tenere premuto il dito, purché che desiderano e tocco continueranno a essere eseguiti. Se si richiede sia toccare e tenere premuto, dopo circa un secondo di tenendo premuto il dito, l'azione alzerà di livello a un'esenzione e una scelta non verrà più eseguita.

Per usare SpatialGestureRecognizer, gestire il SpatialInteractionManager [InteractionDetected](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected) evento e il SpatialPointerPose esposte sono quadratini di ridimensionamento. Usare ray head sguardo dell'utente da questo posa da intersecare con l'ologrammi e trame area nelle vicinanze dell'utente, per poter determinare ciò che l'utente non sia progettata per interagire con. Quindi, instradare il SpatialInteraction negli argomenti di evento per SpatialGestureRecognizer del ologrammi destinazione, con relativi [CaptureInteraction](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction) (metodo). Verrà avviata l'interpretazione di questa interazione in base al [SpatialGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings) impostata su tale riconoscimento al momento della creazione - o da [TrySetGestureSettings](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings).

Su HoloLens, interazioni e i movimenti devono derivano in genere la destinazione da sguardo head dell'utente, piuttosto che tentare per eseguire il rendering o interagire direttamente nella posizione dell'icona della mano. Dopo aver avviato un'interazione, relativi movimenti della mano consente di controllare il movimento, come con il movimento di manipolazione o la navigazione.

## <a name="see-also"></a>Vedere anche
* [Sguardo](gaze.md)
* [Movimenti](gestures.md)
* [Controller di movimento](motion-controllers.md)

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
# <a name="gaze-gestures-and-motion-controllers-in-directx"></a><span data-ttu-id="9b040-104">Sguardo, gesti e controller di movimento in DirectX</span><span class="sxs-lookup"><span data-stu-id="9b040-104">Gaze, gestures, and motion controllers in DirectX</span></span>

<span data-ttu-id="9b040-105">Se si intende compilare direttamente all'inizio della piattaforma, è necessario gestire l'input proveniente dall'utente, ad esempio in cui l'utente esegue la ricerca tramite [sguardo head](gaze.md) e ciò che l'utente ha selezionato con [movimenti](gestures.md) o [controller di movimento](motion-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="9b040-105">If you're going to build directly on top of the platform, you will have to handle input coming from the user - such as where the user is looking via [head gaze](gaze.md) and what the user has selected with [gestures](gestures.md) or [motion controllers](motion-controllers.md).</span></span> <span data-ttu-id="9b040-106">La combinazione di questi formati di input, è possibile abilitare un utente di inserire un [ologrammi](hologram.md) nell'app.</span><span class="sxs-lookup"><span data-stu-id="9b040-106">Combining these forms of input, you can enable a user to place a [hologram](hologram.md) in your app.</span></span> <span data-ttu-id="9b040-107">Il [modello di app holographic](creating-a-holographic-directx-project.md) presenta un esempio di facile utilizzo.</span><span class="sxs-lookup"><span data-stu-id="9b040-107">The [holographic app template](creating-a-holographic-directx-project.md) has an easy to use example.</span></span>

>[!NOTE]
><span data-ttu-id="9b040-108">I frammenti di codice in questo articolo illustrano attualmente l'utilizzo di C++/CX invece di C + + 17 conformi C++/WinRT usato nel [ C++ modello di progetto holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="9b040-108">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="9b040-109">I concetti sono equivalenti per un C++progetto /WinRT, anche se è necessario convertire il codice.</span><span class="sxs-lookup"><span data-stu-id="9b040-109">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="gaze-input"></a><span data-ttu-id="9b040-110">Input sguardo fisso</span><span class="sxs-lookup"><span data-stu-id="9b040-110">Gaze input</span></span>

<span data-ttu-id="9b040-111">Di accesso dell'utente [sguardo head](gaze.md), si utilizza il [SpatialPointerPose](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialpointerpose.aspx) tipo.</span><span class="sxs-lookup"><span data-stu-id="9b040-111">To access the user's [head gaze](gaze.md), you use the [SpatialPointerPose](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialpointerpose.aspx) type.</span></span> <span data-ttu-id="9b040-112">Il modello di app holographic include per sguardo conoscenza di base del codice.</span><span class="sxs-lookup"><span data-stu-id="9b040-112">The holographic app template includes basic code for understanding gaze.</span></span> <span data-ttu-id="9b040-113">Questo codice fornisce un vettore che puntano forward nell'intervallo tra gli occhi dell'utente, prendendo in considerazione la posizione del dispositivo e l'orientamento in un determinato [sistema di coordinate](coordinate-systems-in-directx.md).</span><span class="sxs-lookup"><span data-stu-id="9b040-113">This code provides a vector pointing forward from between the user's eyes, taking into account the device's position and orientation in a given [coordinate system](coordinate-systems-in-directx.md).</span></span>




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

<span data-ttu-id="9b040-114">Potrebbe essere necessario chiedere: ", Ma il sistema di coordinate da dove provengono?"</span><span class="sxs-lookup"><span data-stu-id="9b040-114">You may find yourself asking: "But where does the coordinate system come from?"</span></span>

<span data-ttu-id="9b040-115">È possibile rispondere a questa domanda.</span><span class="sxs-lookup"><span data-stu-id="9b040-115">Let's answer that question.</span></span> <span data-ttu-id="9b040-116">Nel nostro AppMain **Update** funzione, viene elaborato un evento di input spaziale acquistando rispetto al sistema di coordinate per i nostri StationaryFrameOfReference.</span><span class="sxs-lookup"><span data-stu-id="9b040-116">In our AppMain's **Update** function, we processed a spatial input event by acquiring it relative to the coordinate system for our StationaryFrameOfReference.</span></span> <span data-ttu-id="9b040-117">È importante ricordare che è stato creato il StationaryFrameOfReference quando si configura il [HolographicSpace](https://msdn.microsoft.com/library/windows/apps/windows.graphics.holographic.holographicspace.aspx), e il sistema di coordinate è stato acquisito all'inizio del [Update](rendering-in-directx.md).</span><span class="sxs-lookup"><span data-stu-id="9b040-117">Recall that the StationaryFrameOfReference was created when we set up the [HolographicSpace](https://msdn.microsoft.com/library/windows/apps/windows.graphics.holographic.holographicspace.aspx), and the coordinate system was acquired at the start of [Update](rendering-in-directx.md).</span></span>




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

<span data-ttu-id="9b040-118">Si noti che i dati sono associati a uno stato di puntatore di qualche tipo.</span><span class="sxs-lookup"><span data-stu-id="9b040-118">Note that the data is tied to a pointer state of some kind.</span></span> <span data-ttu-id="9b040-119">È tutto da un evento di input spaziale.</span><span class="sxs-lookup"><span data-stu-id="9b040-119">We get this from a spatial input event.</span></span> <span data-ttu-id="9b040-120">L'oggetto dati di evento include un sistema di coordinate, in modo che è sempre possibile correlare la direzione sguardo al momento dell'evento a qualsiasi sistema di coordinate spaziale, è necessario.</span><span class="sxs-lookup"><span data-stu-id="9b040-120">The event data object includes a coordinate system, so that you can always relate the gaze direction at the time of the event to whatever spatial coordinate system you need.</span></span> <span data-ttu-id="9b040-121">In effetti, è necessario farlo per poter ottenere la posa puntatore.</span><span class="sxs-lookup"><span data-stu-id="9b040-121">In fact, you must do so in order to get the pointer pose.</span></span>

> [!NOTE]
> <span data-ttu-id="9b040-122">Altre indicazioni specifiche su 2 HoloLens [presto](index.md#news-and-notes).</span><span class="sxs-lookup"><span data-stu-id="9b040-122">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

## <a name="gesture-and-motion-controller-input"></a><span data-ttu-id="9b040-123">Controller di movimento e movimento di input</span><span class="sxs-lookup"><span data-stu-id="9b040-123">Gesture and motion controller input</span></span>

<span data-ttu-id="9b040-124">Nella realtà mista di Windows, sia a essere passate [movimenti](gestures.md) e [movimento controller](motion-controllers.md) vengono gestite tramite lo stesso input spaziali API, disponibili nel [Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial) spazio dei nomi.</span><span class="sxs-lookup"><span data-stu-id="9b040-124">In Windows Mixed Reality, both hand [gestures](gestures.md) and [motion controllers](motion-controllers.md) are handled through the same spatial input APIs, found in the [Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial) namespace.</span></span> <span data-ttu-id="9b040-125">In questo modo è possibile gestire facilmente le azioni comuni, ad esempio **seleziona** preme allo stesso modo attraverso le mani sia i controller di movimento.</span><span class="sxs-lookup"><span data-stu-id="9b040-125">This enables you to easily handle common actions like **Select** presses the same way across both hands and motion controllers.</span></span>

<span data-ttu-id="9b040-126">Esistono due livelli di API è possibile fare riferimento quando si gestiscono i movimenti o i controller di movimento in realtà mista:</span><span class="sxs-lookup"><span data-stu-id="9b040-126">There are two levels of API you can target when handling gestures or motion controllers in mixed reality:</span></span>
* <span data-ttu-id="9b040-127">[Interazioni](gestures.md#the-two-core-gestures-of-hololens) ([SourcePressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed.aspx), [SourceReleased](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased.aspx) e [SourceUpdated](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated.aspx)), a cui si accede tramite un [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx)</span><span class="sxs-lookup"><span data-stu-id="9b040-127">[Interactions](gestures.md#the-two-core-gestures-of-hololens) ([SourcePressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed.aspx), [SourceReleased](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased.aspx) and [SourceUpdated](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated.aspx)), accessed using a [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx)</span></span>
* <span data-ttu-id="9b040-128">[I movimenti compositi](gestures.md#composite-gestures) ([Tapped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.tapped.aspx), tenere premuto, modifica, esplorazione), a cui si accede tramite un [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx)</span><span class="sxs-lookup"><span data-stu-id="9b040-128">[Composite gestures](gestures.md#composite-gestures) ([Tapped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.tapped.aspx), Hold, Manipulation, Navigation), accessed using a [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx)</span></span>

### <a name="selectmenugrasptouchpadthumbstick-interactions-spatialinteractionmanager"></a><span data-ttu-id="9b040-129">Interazioni di selezione/Menu /. é quindi/Touchpad/Thumbstick: SpatialInteractionManager</span><span class="sxs-lookup"><span data-stu-id="9b040-129">Select/Menu/Grasp/Touchpad/Thumbstick interactions: SpatialInteractionManager</span></span>

<span data-ttu-id="9b040-130">Per rilevare le pressioni a basso livello, versioni e sugli aggiornamenti tra le mani e dispositivi di input in realtà mista di Windows, iniziare da un [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx).</span><span class="sxs-lookup"><span data-stu-id="9b040-130">To detect low-level presses, releases and updates across hands and input devices in Windows Mixed Reality, you start from a [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx).</span></span> <span data-ttu-id="9b040-131">Il SpatialInteractionManager dispone di un evento che informa l'app durante una mano o controller di movimento ha rilevato l'input.</span><span class="sxs-lookup"><span data-stu-id="9b040-131">The SpatialInteractionManager has an event that informs the app when a hand or motion controller has detected input.</span></span>

<span data-ttu-id="9b040-132">Esistono tre tipi principali di SpatialInteractionSource, ognuno rappresentato da un valore SpatialInteractionSourceKind diverso:</span><span class="sxs-lookup"><span data-stu-id="9b040-132">There are three key kinds of SpatialInteractionSource, each represented by a different SpatialInteractionSourceKind value:</span></span>
* <span data-ttu-id="9b040-133">**Mano** rappresenta mano rilevato dell'utente.</span><span class="sxs-lookup"><span data-stu-id="9b040-133">**Hand** represents a user's detected hand.</span></span> <span data-ttu-id="9b040-134">Origini disponibili sono disponibili solo su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9b040-134">Hand sources are available only on HoloLens.</span></span>
* <span data-ttu-id="9b040-135">**Controller** rappresenta un controller di movimento associati.</span><span class="sxs-lookup"><span data-stu-id="9b040-135">**Controller** represents a paired motion controller.</span></span> <span data-ttu-id="9b040-136">I controller di movimento possono offrire un'ampia gamma di funzionalità, ad esempio: Selezionare i trigger, pulsanti di Menu, pulsanti. é quindi, touchpad multipli e levette.</span><span class="sxs-lookup"><span data-stu-id="9b040-136">Motion controllers can offer a variety of capabilities, for example: Select triggers, Menu buttons, Grasp buttons, touchpads and thumbsticks.</span></span>
* <span data-ttu-id="9b040-137">**Voce** rappresenta la voce dell'utente a proposito di sistema ha rilevato le parole chiave.</span><span class="sxs-lookup"><span data-stu-id="9b040-137">**Voice** represents the user's voice speaking system-detected keywords.</span></span> <span data-ttu-id="9b040-138">Verrà inserire una pressione Seleziona e rilasciare ogni volta che l'utente afferma "Select".</span><span class="sxs-lookup"><span data-stu-id="9b040-138">This will inject a Select press and release whenever the user says "Select".</span></span>

<span data-ttu-id="9b040-139">Per rilevare le pressioni tra qualsiasi di queste origini di interazione, è possibile gestire l'evento SourcePressed su SpatialInteractionManager in SpatialInputHandler.cpp:</span><span class="sxs-lookup"><span data-stu-id="9b040-139">To detect presses across any of these interaction sources, you can handle the SourcePressed event on SpatialInteractionManager in SpatialInputHandler.cpp:</span></span>


```cpp
m_interactionManager = SpatialInteractionManager::GetForCurrentView();
    
// Bind a handler to the SourcePressed event.
m_sourcePressedEventToken =
    m_interactionManager->SourcePressed +=
        ref new TypedEventHandler<SpatialInteractionManager^, SpatialInteractionSourceEventArgs^>(
            bind(&SpatialInputHandler::OnSourcePressed, this, _1, _2)
            );
```

<span data-ttu-id="9b040-140">Questo evento premuto viene inviato all'App in modo asincrono.</span><span class="sxs-lookup"><span data-stu-id="9b040-140">This pressed event is sent to your app asynchronously.</span></span> <span data-ttu-id="9b040-141">L'app o il motore di gioco potrebbe essere necessario eseguire alcune operazioni di elaborazione sin da subito oppure è possibile accodare i dati dell'evento nelle routine di elaborazione dell'input.</span><span class="sxs-lookup"><span data-stu-id="9b040-141">Your app or game engine may want to perform some processing right away or you may want to queue up the event data in your input processing routine.</span></span>

<span data-ttu-id="9b040-142">Il modello include una classe helper per iniziare a usare.</span><span class="sxs-lookup"><span data-stu-id="9b040-142">The template includes a helper class to get you started.</span></span> <span data-ttu-id="9b040-143">Questo modello forgoes elaborazioni per motivi di semplicità di progettazione.</span><span class="sxs-lookup"><span data-stu-id="9b040-143">This template forgoes any processing for simplicity of design.</span></span> <span data-ttu-id="9b040-144">La classe helper tiene traccia di se uno o più **Pressed** eventi si sono verificati dopo l'ultimo **Update** chiamare.</span><span class="sxs-lookup"><span data-stu-id="9b040-144">The helper class keeps track of whether one or more **Pressed** events occurred since the last **Update** call.</span></span> <span data-ttu-id="9b040-145">Da SpatialInputHandler.cpp:</span><span class="sxs-lookup"><span data-stu-id="9b040-145">From SpatialInputHandler.cpp:</span></span>




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

<span data-ttu-id="9b040-146">Se, pertanto, restituisce il [SpatialInteractionSourceState](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) per l'evento di input più recente durante il successivo aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="9b040-146">If so, it returns the [SpatialInteractionSourceState](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) for the most recent input event during the next Update.</span></span> <span data-ttu-id="9b040-147">Da SpatialInputHandler.cpp:</span><span class="sxs-lookup"><span data-stu-id="9b040-147">From SpatialInputHandler.cpp:</span></span>




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

<span data-ttu-id="9b040-148">Si noti che il codice sopra riportato considererà tutti preme allo stesso modo, se l'utente esegue una replica primaria **selezionate** premere né una secondaria **dal Menu** o **afferrare** premere.</span><span class="sxs-lookup"><span data-stu-id="9b040-148">Note that the code above will treat all presses the same way, whether the user is performing a primary **Select** press or a secondary **Menu** or **Grasp** press.</span></span> <span data-ttu-id="9b040-149">Il **seleziona** press è una forma principale di interazione tra le mani, movimento controller e la voce attivate da una mano eseguendo un puntato, un controller di movimento con relativo grilletto primario premuto o l'utente è supportato Voice che informa che "Select".</span><span class="sxs-lookup"><span data-stu-id="9b040-149">The **Select** press is a primary form of interaction supported across hands, motion controllers and voice, triggered either by a hand performing an air-tap, a motion controller with its primary trigger/button pressed, or the user's voice saying "Select".</span></span> <span data-ttu-id="9b040-150">Selezionare pressioni rappresentano l'intenzione dell'utente per attivare l'ologrammi che di destinazione.</span><span class="sxs-lookup"><span data-stu-id="9b040-150">Select presses represent the user's intention to activate the hologram they are targeting.</span></span>

<span data-ttu-id="9b040-151">Ragionare su quale tipo di stampa è in corso, si modificherà il gestore dell'evento SpatialInteractionManager::SourceUpdated.</span><span class="sxs-lookup"><span data-stu-id="9b040-151">To reason about which kind of press is occurring, we will modify the SpatialInteractionManager::SourceUpdated event handler.</span></span> <span data-ttu-id="9b040-152">Il nostro codice rileverà. é quindi preme (se disponibili) e usarli per riposizionare il cubo.</span><span class="sxs-lookup"><span data-stu-id="9b040-152">Our code will detect Grasp presses (where available) and use them to reposition the cube.</span></span> <span data-ttu-id="9b040-153">Se. é quindi non sono disponibile, si userà invece pressioni Select.</span><span class="sxs-lookup"><span data-stu-id="9b040-153">If Grasp is not available, we will use Select presses instead.</span></span>

<span data-ttu-id="9b040-154">Aggiungere le seguenti dichiarazioni di membro privato per SpatialInputHandler.h:</span><span class="sxs-lookup"><span data-stu-id="9b040-154">Add the following private member declarations to SpatialInputHandler.h:</span></span> 


```cpp
void OnSourceUpdated(
       Windows::UI::Input::Spatial::SpatialInteractionManager^ sender,
       Windows::UI::Input::Spatial::SpatialInteractionSourceEventArgs^ args);
   Windows::Foundation::EventRegistrationToken m_sourceUpdatedEventToken;
```

<span data-ttu-id="9b040-155">Aprire SpatialInputHandler.cpp.</span><span class="sxs-lookup"><span data-stu-id="9b040-155">Open SpatialInputHandler.cpp.</span></span> <span data-ttu-id="9b040-156">Aggiungere la registrazione di eventi seguente al costruttore:</span><span class="sxs-lookup"><span data-stu-id="9b040-156">Add the following event registration to the constructor:</span></span> 


```cpp
m_sourceUpdatedEventToken =
       m_interactionManager->SourceUpdated +=
       ref new TypedEventHandler<SpatialInteractionManager^, SpatialInteractionSourceEventArgs^>(
           bind(&SpatialInputHandler::OnSourceUpdated, this, _1, _2)
           );
```

<span data-ttu-id="9b040-157">Questo è il codice del gestore eventi.</span><span class="sxs-lookup"><span data-stu-id="9b040-157">This is the event handler code.</span></span> <span data-ttu-id="9b040-158">Se l'origine di input sta riscontrando. é quindi, il puntatore posa verrà archiviata per il successivo ciclo di aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="9b040-158">If the input source is experiencing a Grasp, the pointer pose will be stored for the next update loop.</span></span> <span data-ttu-id="9b040-159">In caso contrario, verrà verificata la pressione di un seleziona invece.</span><span class="sxs-lookup"><span data-stu-id="9b040-159">Otherwise, it will check for a Select press instead.</span></span> <span data-ttu-id="9b040-160">Da SpatialInputHandler.cpp:</span><span class="sxs-lookup"><span data-stu-id="9b040-160">From SpatialInputHandler.cpp:</span></span>




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

<span data-ttu-id="9b040-161">Assicurarsi di annullare la registrazione il gestore eventi nel distruttore.</span><span class="sxs-lookup"><span data-stu-id="9b040-161">Make sure to unregister the event handler in the destructor.</span></span> <span data-ttu-id="9b040-162">Da SpatialInputHandler.cpp:</span><span class="sxs-lookup"><span data-stu-id="9b040-162">From SpatialInputHandler.cpp:</span></span>


```cpp
m_interactionManager->SourceUpdated -= m_sourcePressedEventToken;
```

<span data-ttu-id="9b040-163">Ricompilare e ridistribuire.</span><span class="sxs-lookup"><span data-stu-id="9b040-163">Recompile, and then redeploy.</span></span> <span data-ttu-id="9b040-164">Il progetto di modello dovrebbe ora essere in grado di riconoscere le interazioni. é quindi riposizionare il cubo rotante.</span><span class="sxs-lookup"><span data-stu-id="9b040-164">Your template project should now be able to recognize Grasp interactions to reposition the spinning cube.</span></span>

<span data-ttu-id="9b040-165">L'API SpatialInteractionSource supporta i controller con un'ampia gamma di funzionalità.</span><span class="sxs-lookup"><span data-stu-id="9b040-165">The SpatialInteractionSource API supports controllers with a wide range of capabilities.</span></span> <span data-ttu-id="9b040-166">Nell'esempio illustrato in precedenza, viene verificato se sono supportata. é quindi prima di provare a usarlo.</span><span class="sxs-lookup"><span data-stu-id="9b040-166">In the example shown above, we check to see if Grasp is supported before trying to use it.</span></span> <span data-ttu-id="9b040-167">Il SpatialInteractionSource supporta le funzionalità facoltative seguenti oltre i comuni **seleziona** premere:</span><span class="sxs-lookup"><span data-stu-id="9b040-167">The SpatialInteractionSource supports the following optional features beyond the common **Select** press:</span></span>
* <span data-ttu-id="9b040-168">**Pulsante di menu:** Verificare il supporto esaminando la proprietà IsMenuSupported.</span><span class="sxs-lookup"><span data-stu-id="9b040-168">**Menu button:** Check support by inspecting the IsMenuSupported property.</span></span> <span data-ttu-id="9b040-169">Se supportato, verificare i [SpatialInteractionSourceState::IsMenuPressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) proprietà per determinare se il pulsante di menu viene premuto.</span><span class="sxs-lookup"><span data-stu-id="9b040-169">When supported, check the [SpatialInteractionSourceState::IsMenuPressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) property to find out if the menu button is pressed.</span></span>
* <span data-ttu-id="9b040-170">**Afferrare pulsante:** Verificare il supporto esaminando la proprietà IsGraspSupported.</span><span class="sxs-lookup"><span data-stu-id="9b040-170">**Grasp button:** Check support by inspecting the IsGraspSupported property.</span></span> <span data-ttu-id="9b040-171">Se supportato, verificare i [SpatialInteractionSourceState::IsGrasped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) proprietà per sapere se sono attivato. é quindi.</span><span class="sxs-lookup"><span data-stu-id="9b040-171">When supported, check the [SpatialInteractionSourceState::IsGrasped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) property to find out if grasp is activated.</span></span>

<span data-ttu-id="9b040-172">Per i controller, il SpatialInteractionSource ha una proprietà di Controller con funzionalità aggiuntive.</span><span class="sxs-lookup"><span data-stu-id="9b040-172">For controllers, the SpatialInteractionSource has a Controller property with additional capabilities.</span></span>
* <span data-ttu-id="9b040-173">**HasThumbstick:** Se true, il controller ha una levetta.</span><span class="sxs-lookup"><span data-stu-id="9b040-173">**HasThumbstick:** If true, the controller has a thumbstick.</span></span> <span data-ttu-id="9b040-174">Esaminare i [ControllerProperties](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties) proprietà SpatialInteractionSourceState per acquisire il thumbstick x e i valori y (ThumbstickX e ThumbstickY), nonché lo stato di premuto (IsThumbstickPressed).</span><span class="sxs-lookup"><span data-stu-id="9b040-174">Inspect the [ControllerProperties](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties) property of the SpatialInteractionSourceState to acquire the thumbstick x and y values (ThumbstickX and ThumbstickY), as well as its pressed state (IsThumbstickPressed).</span></span>
* <span data-ttu-id="9b040-175">**HasTouchpad:** Se true, il controller ha il touchpad.</span><span class="sxs-lookup"><span data-stu-id="9b040-175">**HasTouchpad:** If true, the controller has a touchpad.</span></span> <span data-ttu-id="9b040-176">Esaminare la proprietà ControllerProperties di SpatialInteractionSourceState per acquisire il touchpad x e y (TouchpadX e TouchpadY), i valori e per sapere se l'utente tocca il riquadro (IsTouchpadTouched) e se essi sono premendo il touchpad verso il basso ( IsTouchpadPressed).</span><span class="sxs-lookup"><span data-stu-id="9b040-176">Inspect the ControllerProperties property of the SpatialInteractionSourceState to acquire the touchpad x and y values (TouchpadX and TouchpadY), and to know if the user is touching the pad (IsTouchpadTouched) and if they are pressing the touchpad down (IsTouchpadPressed).</span></span>
* <span data-ttu-id="9b040-177">**SimpleHapticsController:** L'API SimpleHapticsController per il controller consente di esaminare le funzionalità haptics del controller e permette anche di controllare l'implementazione del feedback aptico.</span><span class="sxs-lookup"><span data-stu-id="9b040-177">**SimpleHapticsController:** The SimpleHapticsController API for the controller allows you to inspect the haptics capabilities of the controller, and it also allows you to control haptic feedback.</span></span>

<span data-ttu-id="9b040-178">Si noti che l'intervallo per touchpad e thumbstick compreso tra -1 e 1 per entrambi gli assi (dal basso verso l'alto e da sinistra a destra).</span><span class="sxs-lookup"><span data-stu-id="9b040-178">Note that the range for touchpad and thumbstick from -1 to 1 for both axes (from bottom to top, and from left to right).</span></span> <span data-ttu-id="9b040-179">L'intervallo per il trigger analogico, che è possibile accedere tramite la proprietà SpatialInteractionSourceState::SelectPressedValue, ha un intervallo di 0 e 1.</span><span class="sxs-lookup"><span data-stu-id="9b040-179">The range for the analog trigger, which is accessed using the SpatialInteractionSourceState::SelectPressedValue property, has a range of 0 to 1.</span></span> <span data-ttu-id="9b040-180">Un valore di 1 è correlata con IsSelectPressed quali uguale a true. qualsiasi altro valore mette in correlazione con IsSelectPressed quali uguale a false.</span><span class="sxs-lookup"><span data-stu-id="9b040-180">A value of 1 correlates with IsSelectPressed being equal to true; any other value correlates with IsSelectPressed being equal to false.</span></span>

<span data-ttu-id="9b040-181">Si noti che per una mano e un controller, usando SpatialInteractionSourceState::Properties::TryGetLocation fornirà la posizione dell'utente manualmente, ciò è diverso dal posa puntatore che rappresenta ray puntamento del controller.</span><span class="sxs-lookup"><span data-stu-id="9b040-181">Note that for both a hand and a controller, using SpatialInteractionSourceState::Properties::TryGetLocation will provide the user's hand position - this is distinct from the pointer pose representing the controller's pointing ray.</span></span> <span data-ttu-id="9b040-182">Se si desidera disegnare qualcosa in corrispondenza della posizione di disponibilità, usare TryGetLocation.</span><span class="sxs-lookup"><span data-stu-id="9b040-182">If you want to draw something at the hand location, use TryGetLocation.</span></span> <span data-ttu-id="9b040-183">Se si desidera raycast tra la punta del controller, ottenere il raggio di puntamento da TryGetInteractionSourcePose sul SpatialPointerPose.</span><span class="sxs-lookup"><span data-stu-id="9b040-183">If you want to raycast from the tip of the controller, get the pointing ray from TryGetInteractionSourcePose on the SpatialPointerPose.</span></span>

<span data-ttu-id="9b040-184">È possibile utilizzare anche gli altri eventi su SpatialInteractionManager, ad esempio SourceDetected e SourceLost, per rispondere al mani immettono o lasciano il dispositivo visualizzazione o quando si sposta o rifiutare la posizione di pronta (dito indice generato con rollforward palm) o quando il movimento i controller sono per attivare/disattivare o non sono abbinate/abbinati.</span><span class="sxs-lookup"><span data-stu-id="9b040-184">You can also use the other events on SpatialInteractionManager, such as SourceDetected and SourceLost, to react when hands enter or leave the device's view or when they move in or out of the ready position (index finger raised with palm forward), or when motion controllers are turned on/off or are paired/unpaired.</span></span>

### <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="9b040-185">Triangolo di ridimensionamento posa confronto posa puntamento</span><span class="sxs-lookup"><span data-stu-id="9b040-185">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="9b040-186">Realtà mista di Windows supporta controller di movimento in un'ampia gamma di fattori di forma, con la progettazione del ogni controller che differiscono per la relazione tra la posizione dell'utente mano e naturale "inoltro" direzione tale app deve usare per fare riferimento durante il rendering di controller.</span><span class="sxs-lookup"><span data-stu-id="9b040-186">Windows Mixed Reality supports motion controllers in a variety of form factors, with each controller's design differing in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="9b040-187">Per rappresentare meglio questi controller, esistono due tipi di può causare che è possibile esaminare per ogni origine di interazione:</span><span class="sxs-lookup"><span data-stu-id="9b040-187">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source:</span></span>
* <span data-ttu-id="9b040-188">Il **triangolo posa**, che rappresenta la posizione di palmo di una mano rilevata da un HoloLens o palmo che contiene un controller di movimento.</span><span class="sxs-lookup"><span data-stu-id="9b040-188">The **grip pose**, representing the location of either the palm of a hand detected by a HoloLens, or the palm holding a motion controller.</span></span>
    * <span data-ttu-id="9b040-189">In coinvolgenti auricolari, questo posa è particolarmente utile per eseguire il rendering **manuale dell'utente** oppure **mantenuto un oggetto a disposizione dell'utente**, ad esempio un doppio taglio o gun.</span><span class="sxs-lookup"><span data-stu-id="9b040-189">On immersive headsets, this pose is best used to render **the user's hand** or **an object held in the user's hand**, such as a sword or gun.</span></span>
    * <span data-ttu-id="9b040-190">Il **afferrare posizione**: Il centroide palm quando tenendo naturalmente, il controller è regolato sinistro o destro da allineare al centro la posizione all'interno del triangolo di ridimensionamento.</span><span class="sxs-lookup"><span data-stu-id="9b040-190">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span>
    * <span data-ttu-id="9b040-191">Il **afferrare asse a destra dell'orientamento**: Quando si apre completamente la mano per formare una posa flat con un dito di 5, il raggio è normale che palm (in avanti dal palmo a sinistra, con le versioni precedenti dal palmo a destra)</span><span class="sxs-lookup"><span data-stu-id="9b040-191">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
    * <span data-ttu-id="9b040-192">Il **afferrare asse diretta dell'orientamento**: Quando si chiude la mano parzialmente (come se che contiene il controller), il raggio che punta "forward" tramite il tubo costituita dalle dita non thumb.</span><span class="sxs-lookup"><span data-stu-id="9b040-192">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
    * <span data-ttu-id="9b040-193">Il **afferrare orientamento di asse**: L'asse verticale in cui è inclusa per le definizioni di destra e l'inoltro.</span><span class="sxs-lookup"><span data-stu-id="9b040-193">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>
    * <span data-ttu-id="9b040-194">È possibile accedere a posa il triangolo di ridimensionamento tramite [SpatialInteractionSourceState.Properties.TryGetLocation(...) ](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_).</span><span class="sxs-lookup"><span data-stu-id="9b040-194">You can access the grip pose through [SpatialInteractionSourceState.Properties.TryGetLocation(...)](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_).</span></span>
* <span data-ttu-id="9b040-195">Il **posa puntatore**, che rappresenta la punta del controller in avanti che punta.</span><span class="sxs-lookup"><span data-stu-id="9b040-195">The **pointer pose**, representing the tip of the controller pointing forward.</span></span>
    * <span data-ttu-id="9b040-196">Questo posa è particolarmente utile per raycast quando **che punta all'interfaccia utente** quando si esegue il rendering di modello controller stesso.</span><span class="sxs-lookup"><span data-stu-id="9b040-196">This pose is best used to raycast when **pointing at UI** when you are rendering the controller model itself.</span></span>
    * <span data-ttu-id="9b040-197">È possibile accedere la posa puntatore tramite [SpatialInteractionSourceState.Properties.TryGetLocation(...). SourcePointerPose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose) o [SpatialInteractionSourceState.TryGetPointerPose(...). TryGetInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_).</span><span class="sxs-lookup"><span data-stu-id="9b040-197">You can access the pointer pose through [SpatialInteractionSourceState.Properties.TryGetLocation(...).SourcePointerPose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose) or [SpatialInteractionSourceState.TryGetPointerPose(...).TryGetInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_).</span></span>

### <a name="composite-gestures-spatialgesturerecognizer"></a><span data-ttu-id="9b040-198">Movimenti compositi: SpatialGestureRecognizer</span><span class="sxs-lookup"><span data-stu-id="9b040-198">Composite gestures: SpatialGestureRecognizer</span></span>

<span data-ttu-id="9b040-199">Oggetto [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx) interpreta le interazioni dell'utente da mani, i controller di movimento e il comando "Seleziona" casella vocale per gli eventi di movimento spaziali surface, destinazione a cui gli utenti usando le sguardo head.</span><span class="sxs-lookup"><span data-stu-id="9b040-199">A [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx) interprets user interactions from hands, motion controllers, and the "Select" voice command to surface spatial gesture events, which users target using their head gaze.</span></span>

<span data-ttu-id="9b040-200">I movimenti spaziali sono una forma di chiave di input per le app di realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="9b040-200">Spatial gestures are a key form of input for Windows Mixed Reality apps.</span></span> <span data-ttu-id="9b040-201">Dal routine interazioni dal SpatialInteractionManager a SpatialGestureRecognizer di ologramma, le app possono rilevare gli eventi di tocco, tenere premuto, manipolazione e navigazione in modo uniforme tra le mani, voce e spaziali dispositivi di input, senza dovere gestire le pressioni e rilascia manualmente.</span><span class="sxs-lookup"><span data-stu-id="9b040-201">By routing interactions from the SpatialInteractionManager to a hologram's SpatialGestureRecognizer, apps can detect Tap, Hold, Manipulation, and Navigation events uniformly across hands, voice, and spatial input devices, without having to handle presses and releases manually.</span></span>

<span data-ttu-id="9b040-202">SpatialGestureRecognizer esegue solo la minima risoluzione dell'ambiguità tra il set di gesti richiesti.</span><span class="sxs-lookup"><span data-stu-id="9b040-202">SpatialGestureRecognizer performs only the minimal disambiguation between the set of gestures that you request.</span></span> <span data-ttu-id="9b040-203">Ad esempio, se vengono richiesti solo tocco, l'utente può tenere premuto il dito, purché che desiderano e tocco continueranno a essere eseguiti.</span><span class="sxs-lookup"><span data-stu-id="9b040-203">For example, if you request just Tap, the user may hold their finger down as long as they like and a Tap will still occur.</span></span> <span data-ttu-id="9b040-204">Se si richiede sia toccare e tenere premuto, dopo circa un secondo di tenendo premuto il dito, l'azione alzerà di livello a un'esenzione e una scelta non verrà più eseguita.</span><span class="sxs-lookup"><span data-stu-id="9b040-204">If you request both Tap and Hold, after about a second of holding down their finger, the gesture will promote to a Hold and a Tap will no longer occur.</span></span>

<span data-ttu-id="9b040-205">Per usare SpatialGestureRecognizer, gestire il SpatialInteractionManager [InteractionDetected](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected) evento e il SpatialPointerPose esposte sono quadratini di ridimensionamento.</span><span class="sxs-lookup"><span data-stu-id="9b040-205">To use SpatialGestureRecognizer, handle the SpatialInteractionManager's [InteractionDetected](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected) event and grab the SpatialPointerPose exposed there.</span></span> <span data-ttu-id="9b040-206">Usare ray head sguardo dell'utente da questo posa da intersecare con l'ologrammi e trame area nelle vicinanze dell'utente, per poter determinare ciò che l'utente non sia progettata per interagire con.</span><span class="sxs-lookup"><span data-stu-id="9b040-206">Use the user's head gaze ray from this pose to intersect with the holograms and surface meshes in the user's surroundings, in order to determine what the user is intending to interact with.</span></span> <span data-ttu-id="9b040-207">Quindi, instradare il SpatialInteraction negli argomenti di evento per SpatialGestureRecognizer del ologrammi destinazione, con relativi [CaptureInteraction](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction) (metodo).</span><span class="sxs-lookup"><span data-stu-id="9b040-207">Then, route the SpatialInteraction in the event arguments to the target hologram's SpatialGestureRecognizer, using its [CaptureInteraction](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction) method.</span></span> <span data-ttu-id="9b040-208">Verrà avviata l'interpretazione di questa interazione in base al [SpatialGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings) impostata su tale riconoscimento al momento della creazione - o da [TrySetGestureSettings](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings).</span><span class="sxs-lookup"><span data-stu-id="9b040-208">This starts interpreting that interaction according to the [SpatialGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings) set on that recognizer at creation time - or by [TrySetGestureSettings](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings).</span></span>

<span data-ttu-id="9b040-209">Su HoloLens, interazioni e i movimenti devono derivano in genere la destinazione da sguardo head dell'utente, piuttosto che tentare per eseguire il rendering o interagire direttamente nella posizione dell'icona della mano.</span><span class="sxs-lookup"><span data-stu-id="9b040-209">On HoloLens, interactions and gestures should generally derive their targeting from the user's head gaze, rather than trying to render or interact at the hand's location directly.</span></span> <span data-ttu-id="9b040-210">Dopo aver avviato un'interazione, relativi movimenti della mano consente di controllare il movimento, come con il movimento di manipolazione o la navigazione.</span><span class="sxs-lookup"><span data-stu-id="9b040-210">Once an interaction has started, relative motions of the hand may be used to control the gesture, as with the Manipulation or Navigation gesture.</span></span>

## <a name="see-also"></a><span data-ttu-id="9b040-211">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9b040-211">See also</span></span>
* [<span data-ttu-id="9b040-212">Sguardo</span><span class="sxs-lookup"><span data-stu-id="9b040-212">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="9b040-213">Movimenti</span><span class="sxs-lookup"><span data-stu-id="9b040-213">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="9b040-214">Controller di movimento</span><span class="sxs-lookup"><span data-stu-id="9b040-214">Motion controllers</span></span>](motion-controllers.md)

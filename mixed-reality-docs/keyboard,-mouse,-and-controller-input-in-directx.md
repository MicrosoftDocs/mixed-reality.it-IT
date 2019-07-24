---
title: Input da tastiera, mouse e controller in DirectX
description: Viene illustrato come creare un'app per la realtà mista di Windows che usa i controller di tastiera, mouse e gioco.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, tastiera, mouse, controller di gioco, Xbox Controller, HoloLens, desktop, procedura dettagliata, codice di esempio
ms.openlocfilehash: 1e61cb50a561492fdc6849b5b231e97fab1bb6cf
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63551003"
---
# <a name="keyboard-mouse-and-controller-input-in-directx"></a><span data-ttu-id="e7329-104">Input da tastiera, mouse e controller in DirectX</span><span class="sxs-lookup"><span data-stu-id="e7329-104">Keyboard, mouse, and controller input in DirectX</span></span>

<span data-ttu-id="e7329-105">Tastiere, topi e controller di gioco possono essere tutti formati utili per i dispositivi di realtà mista Windows.</span><span class="sxs-lookup"><span data-stu-id="e7329-105">Keyboards, mice, and game controllers can all be useful forms of input for Windows Mixed Reality devices.</span></span> <span data-ttu-id="e7329-106">Le tastiere e i topi Bluetooth sono entrambi supportati in HoloLens, per l'uso con il debug dell'app o come forma alternativa di input.</span><span class="sxs-lookup"><span data-stu-id="e7329-106">Bluetooth keyboards and mice are both supported on HoloLens, for use with debugging your app or as an alternate form of input.</span></span> <span data-ttu-id="e7329-107">La realtà mista di Windows supporta anche auricolari immersivi collegati a PC, in cui i topi, le tastiere e i controller di gioco hanno storicamente la norma.</span><span class="sxs-lookup"><span data-stu-id="e7329-107">Windows Mixed Reality also supports immersive headsets attached to PCs - where mice, keyboards, and game controllers have historically been the norm.</span></span>

<span data-ttu-id="e7329-108">Per usare l'input da tastiera in HoloLens, associare una tastiera Bluetooth al dispositivo o usare l'input virtuale tramite il portale del dispositivo Windows.</span><span class="sxs-lookup"><span data-stu-id="e7329-108">To use keyboard input on HoloLens, pair a Bluetooth keyboard to your device or use virtual input via the Windows Device Portal.</span></span> <span data-ttu-id="e7329-109">Per usare l'input da tastiera con una cuffia mista a realtà mista di Windows, assegnare lo stato attivo per l'input alla realtà mista inserendo sul dispositivo o usando la combinazione di tasti tasto Windows + Y.</span><span class="sxs-lookup"><span data-stu-id="e7329-109">To use keyboard input while wearing a Windows Mixed Reality immersive headset, assign input focus to mixed reality by putting on the device or using the Windows Key + Y keyboard combination.</span></span> <span data-ttu-id="e7329-110">Tenere presente che le app destinate a HoloLens devono fornire funzionalità senza questi dispositivi collegati.</span><span class="sxs-lookup"><span data-stu-id="e7329-110">Keep in mind that apps intended for HoloLens must provide functionality without these devices attached.</span></span>

>[!NOTE]
><span data-ttu-id="e7329-111">I frammenti di codice in questo articolo illustrano attualmente l' C++uso di/CX, invece di/WinRT conformi C++a C + 17 come usato nel modello di [ C++ progetto olografico](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="e7329-111">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="e7329-112">I concetti sono equivalenti per C++un progetto/WinRT, anche se sarà necessario tradurre il codice.</span><span class="sxs-lookup"><span data-stu-id="e7329-112">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="subscribe-for-corewindow-input-events"></a><span data-ttu-id="e7329-113">Sottoscrivere gli eventi di input di CoreWindow</span><span class="sxs-lookup"><span data-stu-id="e7329-113">Subscribe for CoreWindow input events</span></span>

### <a name="keyboard-input"></a><span data-ttu-id="e7329-114">Input da tastiera</span><span class="sxs-lookup"><span data-stu-id="e7329-114">Keyboard input</span></span>

<span data-ttu-id="e7329-115">Nel modello di app olografico di Windows è incluso un gestore eventi per l'input da tastiera come qualsiasi altra app UWP.</span><span class="sxs-lookup"><span data-stu-id="e7329-115">In the Windows Holographic app template, we include an event handler for keyboard input just like any other UWP app.</span></span> <span data-ttu-id="e7329-116">L'app usa i dati di input della tastiera nello stesso modo in realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="e7329-116">Your app consumes keyboard input data the same way in Windows Mixed Reality.</span></span>

<span data-ttu-id="e7329-117">Da AppView. cpp:</span><span class="sxs-lookup"><span data-stu-id="e7329-117">From AppView.cpp:</span></span>

```
// Register for keypress notifications.
   window->KeyDown +=
       ref new TypedEventHandler<CoreWindow^, KeyEventArgs^>(this, &AppView::OnKeyPressed);

    …

   // Input event handlers

   void AppView::OnKeyPressed(CoreWindow^ sender, KeyEventArgs^ args)
   {
       //
       // TODO: Respond to keyboard input here.
       //
   }
```

### <a name="virtual-keyboard-input"></a><span data-ttu-id="e7329-118">Input tastiera virtuale</span><span class="sxs-lookup"><span data-stu-id="e7329-118">Virtual keyboard input</span></span>
<span data-ttu-id="e7329-119">Per gli auricolari desktop immersivi è possibile supportare anche le tastiere virtuali di cui è stato eseguito il rendering da Windows attraverso la visualizzazione immersiva.</span><span class="sxs-lookup"><span data-stu-id="e7329-119">For immersive desktop headsets, you can also support virtual keyboards rendered by Windows over your immersive view.</span></span> <span data-ttu-id="e7329-120">Per supportare questa operazione, l'app può implementare **CoreTextEditContext**.</span><span class="sxs-lookup"><span data-stu-id="e7329-120">To support this, your app can implement **CoreTextEditContext**.</span></span> <span data-ttu-id="e7329-121">Questo consente a Windows di comprendere lo stato delle caselle di testo sottoposte a rendering dell'app, in modo che la tastiera virtuale possa contribuire correttamente al testo presente.</span><span class="sxs-lookup"><span data-stu-id="e7329-121">This lets Windows understand the state of your own app-rendered text boxes, so the virtual keyboard can correctly contribute to the text there.</span></span>

<span data-ttu-id="e7329-122">Per ulteriori informazioni sull'implementazione del supporto CoreTextEditContext, vedere l' [esempio CoreTextEditContext](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).</span><span class="sxs-lookup"><span data-stu-id="e7329-122">For more information on implementing CoreTextEditContext support, see the [CoreTextEditContext sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).</span></span>

### <a name="mouse-input"></a><span data-ttu-id="e7329-123">Input del mouse</span><span class="sxs-lookup"><span data-stu-id="e7329-123">Mouse Input</span></span>

<span data-ttu-id="e7329-124">È anche possibile usare l'input del mouse, tramite i gestori eventi di input di UWP CoreWindow.</span><span class="sxs-lookup"><span data-stu-id="e7329-124">You can also use mouse input, again via the UWP CoreWindow input event handlers.</span></span> <span data-ttu-id="e7329-125">Ecco come modificare il modello di app olografico di Windows per supportare i clic del mouse nello stesso modo dei movimenti premuti.</span><span class="sxs-lookup"><span data-stu-id="e7329-125">Here's how to modify the Windows Holographic app template to support mouse clicks in the same way as pressed gestures.</span></span> <span data-ttu-id="e7329-126">Dopo aver apportato questa modifica, un clic del mouse quando si indossa un dispositivo headset immersivo riposiziona il cubo.</span><span class="sxs-lookup"><span data-stu-id="e7329-126">After making this modification, a mouse click while wearing an immersive headset device will reposition the cube.</span></span>

<span data-ttu-id="e7329-127">Si noti che le app UWP possono anche ottenere dati XY non elaborati per il mouse usando l'API [MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) .</span><span class="sxs-lookup"><span data-stu-id="e7329-127">Note that UWP apps can also get raw XY data for the mouse by using the [MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) API.</span></span>

<span data-ttu-id="e7329-128">Per iniziare, dichiarare un nuovo gestore OnPointerPressed in AppView. h:</span><span class="sxs-lookup"><span data-stu-id="e7329-128">Start by declaring a new OnPointerPressed handler in AppView.h:</span></span>

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

<span data-ttu-id="e7329-129">In AppView. cpp aggiungere questo codice a Window:</span><span class="sxs-lookup"><span data-stu-id="e7329-129">In AppView.cpp, add this code to SetWindow:</span></span>

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

<span data-ttu-id="e7329-130">Inserire quindi questa definizione per OnPointerPressed nella parte inferiore del file:</span><span class="sxs-lookup"><span data-stu-id="e7329-130">Then put this definition for OnPointerPressed at the bottom of the file:</span></span>

```
void AppView::OnPointerPressed(CoreWindow^ sender, PointerEventArgs^ args)
   {
       // Allow the user to interact with the holographic world using the mouse.
       if (m_main != nullptr)
       {
           m_main->OnPointerPressed();
       }
   }
```

<span data-ttu-id="e7329-131">Il gestore eventi appena aggiunto è un pass-through alla classe principale del modello.</span><span class="sxs-lookup"><span data-stu-id="e7329-131">The event handler we just added is a pass-through to the template main class.</span></span> <span data-ttu-id="e7329-132">Verrà ora modificata la classe principale per supportare questo pass-through.</span><span class="sxs-lookup"><span data-stu-id="e7329-132">Let's modify the main class to support this pass-through.</span></span> <span data-ttu-id="e7329-133">Aggiungere la dichiarazione del metodo public al file di intestazione:</span><span class="sxs-lookup"><span data-stu-id="e7329-133">Add this public method declaration to the header file:</span></span>

```
// Handle mouse input.
       void OnPointerPressed();
```

<span data-ttu-id="e7329-134">Sarà necessaria anche questa variabile membro privata:</span><span class="sxs-lookup"><span data-stu-id="e7329-134">You'll need this private member variable, as well:</span></span>

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

<span data-ttu-id="e7329-135">Infine, la classe principale viene aggiornata con la nuova logica per supportare i clic del mouse.</span><span class="sxs-lookup"><span data-stu-id="e7329-135">Finally, we will update the main class with new logic to support mouse clicks.</span></span> <span data-ttu-id="e7329-136">Per iniziare, aggiungere questo gestore eventi.</span><span class="sxs-lookup"><span data-stu-id="e7329-136">Start by adding this event handler.</span></span> <span data-ttu-id="e7329-137">Assicurarsi di aggiornare il nome della classe:</span><span class="sxs-lookup"><span data-stu-id="e7329-137">Make sure to update the class name:</span></span>

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

<span data-ttu-id="e7329-138">A questo punto, nel metodo Update sostituire la logica esistente per ottenere un puntatore con questo:</span><span class="sxs-lookup"><span data-stu-id="e7329-138">Now, in the Update method, replace the existing logic for getting a pointer pose with this:</span></span>

```
SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   SpatialPointerPose^ pose = nullptr;
   if (pointerState != nullptr)
   {
       pose = pointerState->TryGetPointerPose(currentCoordinateSystem);
   }
   else if (m_pointerPressed)
   {
       pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
   }
   m_pointerPressed = false;
```

<span data-ttu-id="e7329-139">Ricompilare e ridistribuire.</span><span class="sxs-lookup"><span data-stu-id="e7329-139">Recompile and redeploy.</span></span> <span data-ttu-id="e7329-140">Si noterà che il clic del mouse riposiziona il cubo nell'auricolare immersivo o HoloLens con il mouse Bluetooth collegato.</span><span class="sxs-lookup"><span data-stu-id="e7329-140">You should notice that the mouse click will now reposition the cube in your immersive headset - or HoloLens with bluetooth mouse attached.</span></span>

### <a name="game-controller-support"></a><span data-ttu-id="e7329-141">Supporto del controller di gioco</span><span class="sxs-lookup"><span data-stu-id="e7329-141">Game controller support</span></span>

<span data-ttu-id="e7329-142">I controller dei giochi possono essere un metodo divertente e pratico per consentire all'utente di controllare un'esperienza di realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="e7329-142">Game controllers can be a fun and convenient way of allowing the user to control an immersive Windows Mixed Reality experience.</span></span>

<span data-ttu-id="e7329-143">Il primo passaggio per aggiungere il supporto per i controller di gioco al modello di app olografico di Windows consiste nell'aggiungere le seguenti dichiarazioni di membro privato alla classe di intestazione per il file principale:</span><span class="sxs-lookup"><span data-stu-id="e7329-143">The first step in adding support for game controllers to the Windows Holographic app template, is to add the following private member declarations to the header class for your main file:</span></span>

```
// Recognize gamepads that are plugged in after the app starts.
       void OnGamepadAdded(Platform::Object^, Windows::Gaming::Input::Gamepad^ args);
```

```
// Stop looking for gamepads that are unplugged.
       void OnGamepadRemoved(Platform::Object^, Windows::Gaming::Input::Gamepad^ args);
```

```
Windows::Foundation::EventRegistrationToken                     m_gamepadAddedEventToken;
       Windows::Foundation::EventRegistrationToken                     m_gamepadRemovedEventToken;
```

```
// Keeps track of a gamepad and the state of its A button.
       struct GamepadWithButtonState
       {
           Windows::Gaming::Input::Gamepad^ gamepad;
           bool buttonAWasPressedLastFrame = false;
       };
       std::vector<GamepadWithButtonState>                             m_gamepads;
```

<span data-ttu-id="e7329-144">Inizializzare gli eventi del gamepad e gli eventuali gamepad attualmente collegati nel costruttore della classe principale:</span><span class="sxs-lookup"><span data-stu-id="e7329-144">Initialize gamepad events, and any gamepads that are currently attached, in the constructor for your main class:</span></span>

```
// If connected, a game controller can also be used for input.
   m_gamepadAddedEventToken = Gamepad::GamepadAdded +=
       ref new EventHandler<Gamepad^>(
           bind(&$safeprojectname$Main::OnGamepadAdded, this, _1, _2)
           );
```

```
m_gamepadRemovedEventToken = Gamepad::GamepadRemoved +=
       ref new EventHandler<Gamepad^>(
           bind(&$safeprojectname$Main::OnGamepadRemoved, this, _1, _2)
           );
```

```
for (auto const& gamepad : Gamepad::Gamepads)
   {
       OnGamepadAdded(nullptr, gamepad);
   }
```

<span data-ttu-id="e7329-145">Aggiungere i gestori eventi alla classe principale.</span><span class="sxs-lookup"><span data-stu-id="e7329-145">Add these event handlers to your main class.</span></span> <span data-ttu-id="e7329-146">Assicurarsi di aggiornare il nome della classe:</span><span class="sxs-lookup"><span data-stu-id="e7329-146">Make sure to update the class name:</span></span>

```
void MyHolographicAppMain::OnGamepadAdded(Object^, Gamepad^ args)
   {
       for (auto const& gamepadWithButtonState : m_gamepads)
       {
           if (args == gamepadWithButtonState.gamepad)
           {
               // This gamepad is already in the list.
               return;
           }
       }
       m_gamepads.push_back({ args, false });
   }
```

```
void MyHolographicAppMain::OnGamepadRemoved(Object^, Gamepad^ args)
   {
       m_gamepads.erase(
           std::remove_if(m_gamepads.begin(), m_gamepads.end(), [&](GamepadWithButtonState& gamepadWithState)
               {
                   return gamepadWithState.gamepad == args;
               }),
           m_gamepads.end());
   }
```

<span data-ttu-id="e7329-147">Infine, aggiornare la logica di input per riconoscere le modifiche nello stato del controller.</span><span class="sxs-lookup"><span data-stu-id="e7329-147">Finally, update the input logic to recognize changes in controller state.</span></span> <span data-ttu-id="e7329-148">Qui viene usata la stessa variabile m_pointerPressed descritta nella sezione precedente per l'aggiunta di eventi del mouse.</span><span class="sxs-lookup"><span data-stu-id="e7329-148">Here, we use the same m_pointerPressed variable discussed in the section above for adding mouse events.</span></span> <span data-ttu-id="e7329-149">Aggiungere questo oggetto al metodo Update, immediatamente prima della posizione in cui viene verificato il SpatialPointerPose:</span><span class="sxs-lookup"><span data-stu-id="e7329-149">Add this to the Update method, just before where it checks for the SpatialPointerPose:</span></span>

```
// Check for new input state since the last frame.
   for (auto& gamepadWithButtonState : m_gamepads)
   {
       bool buttonDownThisUpdate = ((gamepadWithButtonState.gamepad->GetCurrentReading().Buttons & GamepadButtons::A) == GamepadButtons::A);
       if (buttonDownThisUpdate && !gamepadWithButtonState.buttonAWasPressedLastFrame)
       {
           m_pointerPressed = true;
       }
       gamepadWithButtonState.buttonAWasPressedLastFrame = buttonDownThisUpdate;
   }
```

```
// For context.
   SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   SpatialPointerPose^ pose = nullptr;
   if (pointerState != nullptr)
   {
       pose = pointerState->TryGetPointerPose(currentCoordinateSystem);
   }
   else if (m_pointerPressed)
   {
       pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
   }
   m_pointerPressed = false;
```

<span data-ttu-id="e7329-150">Non dimenticare di annullare la registrazione degli eventi durante la pulizia della classe principale:</span><span class="sxs-lookup"><span data-stu-id="e7329-150">Don't forget to unregister the events when cleaning up the main class:</span></span>

```
if (m_gamepadAddedEventToken.Value != 0)
   {
       Gamepad::GamepadAdded -= m_gamepadAddedEventToken;
   }
   if (m_gamepadRemovedEventToken.Value != 0)
   {
       Gamepad::GamepadRemoved -= m_gamepadRemovedEventToken;
   }
```

<span data-ttu-id="e7329-151">Ricompilare e ridistribuire.</span><span class="sxs-lookup"><span data-stu-id="e7329-151">Recompile, and redeploy.</span></span> <span data-ttu-id="e7329-152">È ora possibile associare, o associare, un controller di gioco e usarlo per riposizionare il cubo rotante.</span><span class="sxs-lookup"><span data-stu-id="e7329-152">You can now attach, or pair, a game controller and use it to reposition the spinning cube.</span></span>

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a><span data-ttu-id="e7329-153">Linee guida importanti per l'input della tastiera e del mouse</span><span class="sxs-lookup"><span data-stu-id="e7329-153">Important guidelines for keyboard and mouse input</span></span>

<span data-ttu-id="e7329-154">Esistono alcune differenze fondamentali nel modo in cui questo codice può essere usato in Microsoft HoloLens, ovvero un dispositivo che si basa principalmente sull'input dell'utente naturale, rispetto a quello disponibile in un PC con Windows Mixed Reality-Enabled.</span><span class="sxs-lookup"><span data-stu-id="e7329-154">There are some key differences in how this code can be used on Microsoft HoloLens – which is a device that relies primarily on natural user input – versus what is available on a Windows Mixed Reality-enabled PC.</span></span>
* <span data-ttu-id="e7329-155">Non è possibile fare affidamento sull'input della tastiera o del mouse per essere presente.</span><span class="sxs-lookup"><span data-stu-id="e7329-155">You can’t rely on keyboard or mouse input to be present.</span></span> <span data-ttu-id="e7329-156">Tutte le funzionalità dell'app devono funzionare con lo sguardo, il gesto e l'input vocale.</span><span class="sxs-lookup"><span data-stu-id="e7329-156">All of your app's functionality must work with gaze, gesture, and speech input.</span></span>
* <span data-ttu-id="e7329-157">Quando viene collegata una tastiera Bluetooth, può essere utile abilitare l'input da tastiera per qualsiasi testo che l'app potrebbe richiedere.</span><span class="sxs-lookup"><span data-stu-id="e7329-157">When a Bluetooth keyboard is attached, it can be helpful to enable keyboard input for any text that your app might ask for.</span></span> <span data-ttu-id="e7329-158">Questo può essere un ottimo supplemento per la dettatura, ad esempio.</span><span class="sxs-lookup"><span data-stu-id="e7329-158">This can be a great supplement for dictation, for example.</span></span>
* <span data-ttu-id="e7329-159">Per quanto riguarda la progettazione dell'app, non fare affidamento su (ad esempio) i controlli WASD e mouse per il gioco.</span><span class="sxs-lookup"><span data-stu-id="e7329-159">When it comes to designing your app, don’t rely on (for example) WASD and mouse look controls for your game.</span></span> <span data-ttu-id="e7329-160">HoloLens è progettato per l'utente in modo da aggirare la stanza.</span><span class="sxs-lookup"><span data-stu-id="e7329-160">HoloLens is designed for the user to walk around the room.</span></span> <span data-ttu-id="e7329-161">In questo caso, l'utente controlla direttamente la fotocamera.</span><span class="sxs-lookup"><span data-stu-id="e7329-161">In this case, the user controls the camera directly.</span></span> <span data-ttu-id="e7329-162">Un'interfaccia per guidare la fotocamera attorno alla stanza con i controlli Move/look non fornirà la stessa esperienza.</span><span class="sxs-lookup"><span data-stu-id="e7329-162">An interface for driving the camera around the room with move/look controls won't provide the same experience.</span></span>
* <span data-ttu-id="e7329-163">L'input da tastiera può essere un ottimo modo per controllare gli aspetti di debug dell'app o del motore di gioco, soprattutto perché l'utente non dovrà usare la tastiera.</span><span class="sxs-lookup"><span data-stu-id="e7329-163">Keyboard input can be an excellent way to control the debugging aspects of your app or game engine, especially since the user will not be required to use the keyboard.</span></span> <span data-ttu-id="e7329-164">Il cablaggio è identico a quello usato per le API degli eventi CoreWindow.</span><span class="sxs-lookup"><span data-stu-id="e7329-164">Wiring it up is the same as you're used to, with CoreWindow event APIs.</span></span> <span data-ttu-id="e7329-165">In questo scenario, è possibile scegliere di implementare un modo per configurare l'app per instradare gli eventi della tastiera a una modalità di "debug solo input" durante le sessioni di debug.</span><span class="sxs-lookup"><span data-stu-id="e7329-165">In this scenario, you might choose to implement a way to configure your app to route keyboard events to a "debug input only" mode during your debug sessions.</span></span>
* <span data-ttu-id="e7329-166">Anche i controller Bluetooth funzionano.</span><span class="sxs-lookup"><span data-stu-id="e7329-166">Bluetooth controllers work as well.</span></span>

## <a name="see-also"></a><span data-ttu-id="e7329-167">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e7329-167">See also</span></span>
* [<span data-ttu-id="e7329-168">Accessori hardware</span><span class="sxs-lookup"><span data-stu-id="e7329-168">Hardware accessories</span></span>](hardware-accessories.md)

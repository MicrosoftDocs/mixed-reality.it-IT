---
title: Input di tastiera, mouse e controller DirectX
description: Viene illustrato come creare un'app per realtà mista di Windows che usa periferiche di gioco, tastiera e mouse.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, tastiera, mouse, di gioco, controller xbox, HoloLens, desktop, procedura dettagliata, codice di esempio
ms.openlocfilehash: 1e61cb50a561492fdc6849b5b231e97fab1bb6cf
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605089"
---
# <a name="keyboard-mouse-and-controller-input-in-directx"></a><span data-ttu-id="5b3de-104">Input di tastiera, mouse e controller DirectX</span><span class="sxs-lookup"><span data-stu-id="5b3de-104">Keyboard, mouse, and controller input in DirectX</span></span>

<span data-ttu-id="5b3de-105">Tutte le tastiere, mouse e periferiche di gioco possono essere utile maschere di input per i dispositivi di realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="5b3de-105">Keyboards, mice, and game controllers can all be useful forms of input for Windows Mixed Reality devices.</span></span> <span data-ttu-id="5b3de-106">Bluetooth tastiere e mouse vengono supportati sia su HoloLens, per l'uso con debug della tua app o come un tipo alternativo di input.</span><span class="sxs-lookup"><span data-stu-id="5b3de-106">Bluetooth keyboards and mice are both supported on HoloLens, for use with debugging your app or as an alternate form of input.</span></span> <span data-ttu-id="5b3de-107">Realtà mista di Windows supporta anche auricolari immersive collegati al PC - dove mice, tastiera e periferiche di gioco sono tradizionalmente la norma.</span><span class="sxs-lookup"><span data-stu-id="5b3de-107">Windows Mixed Reality also supports immersive headsets attached to PCs - where mice, keyboards, and game controllers have historically been the norm.</span></span>

<span data-ttu-id="5b3de-108">Per usare gli input da tastiera in HoloLens, coppia di una tastiera Bluetooth nel dispositivo oppure usare input virtuale tramite il Windows Device Portal.</span><span class="sxs-lookup"><span data-stu-id="5b3de-108">To use keyboard input on HoloLens, pair a Bluetooth keyboard to your device or use virtual input via the Windows Device Portal.</span></span> <span data-ttu-id="5b3de-109">Per utilizzare input da tastiera durante indossare le cuffie immersive realtà mista di Windows, assegnare lo stato attivo per realtà mista da inserire nel dispositivo o usando il tasto Windows + Y combinazione di tasti.</span><span class="sxs-lookup"><span data-stu-id="5b3de-109">To use keyboard input while wearing a Windows Mixed Reality immersive headset, assign input focus to mixed reality by putting on the device or using the Windows Key + Y keyboard combination.</span></span> <span data-ttu-id="5b3de-110">Tenere presente che le applicazioni destinate a HoloLens devono fornire funzionalità senza questi dispositivi collegati.</span><span class="sxs-lookup"><span data-stu-id="5b3de-110">Keep in mind that apps intended for HoloLens must provide functionality without these devices attached.</span></span>

>[!NOTE]
><span data-ttu-id="5b3de-111">I frammenti di codice in questo articolo illustrano attualmente l'utilizzo di C++/CX invece di C + + 17 conformi C++/WinRT usato nel [ C++ modello di progetto holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="5b3de-111">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="5b3de-112">I concetti sono equivalenti per un C++progetto /WinRT, anche se è necessario convertire il codice.</span><span class="sxs-lookup"><span data-stu-id="5b3de-112">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="subscribe-for-corewindow-input-events"></a><span data-ttu-id="5b3de-113">La sottoscrizione per gli eventi di input CoreWindow</span><span class="sxs-lookup"><span data-stu-id="5b3de-113">Subscribe for CoreWindow input events</span></span>

### <a name="keyboard-input"></a><span data-ttu-id="5b3de-114">Input da tastiera</span><span class="sxs-lookup"><span data-stu-id="5b3de-114">Keyboard input</span></span>

<span data-ttu-id="5b3de-115">Il modello di app Windows Holographic, include un gestore eventi per l'input da tastiera come qualsiasi altra app UWP.</span><span class="sxs-lookup"><span data-stu-id="5b3de-115">In the Windows Holographic app template, we include an event handler for keyboard input just like any other UWP app.</span></span> <span data-ttu-id="5b3de-116">L'app utilizza i dati di input di tastiera simile a quello nella realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="5b3de-116">Your app consumes keyboard input data the same way in Windows Mixed Reality.</span></span>

<span data-ttu-id="5b3de-117">Da AppView.cpp:</span><span class="sxs-lookup"><span data-stu-id="5b3de-117">From AppView.cpp:</span></span>

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

### <a name="virtual-keyboard-input"></a><span data-ttu-id="5b3de-118">Input da tastiera virtuale</span><span class="sxs-lookup"><span data-stu-id="5b3de-118">Virtual keyboard input</span></span>
<span data-ttu-id="5b3de-119">Per immersive auricolari desktop, è anche possibile supportare tastiere virtuale sottoposto a rendering dal Windows tramite la vista coinvolgente e concreto.</span><span class="sxs-lookup"><span data-stu-id="5b3de-119">For immersive desktop headsets, you can also support virtual keyboards rendered by Windows over your immersive view.</span></span> <span data-ttu-id="5b3de-120">A tale scopo, è possibile implementare l'app **CoreTextEditContext**.</span><span class="sxs-lookup"><span data-stu-id="5b3de-120">To support this, your app can implement **CoreTextEditContext**.</span></span> <span data-ttu-id="5b3de-121">In questo modo Windows comprendere lo stato propria app con rendering di caselle di testo, in modo che la tastiera virtuale correttamente può contribuire a presenti il testo.</span><span class="sxs-lookup"><span data-stu-id="5b3de-121">This lets Windows understand the state of your own app-rendered text boxes, so the virtual keyboard can correctly contribute to the text there.</span></span>

<span data-ttu-id="5b3de-122">Per altre informazioni sull'implementazione CoreTextEditContext supporto, vedere la [CoreTextEditContext esempio](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).</span><span class="sxs-lookup"><span data-stu-id="5b3de-122">For more information on implementing CoreTextEditContext support, see the [CoreTextEditContext sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).</span></span>

### <a name="mouse-input"></a><span data-ttu-id="5b3de-123">Input del mouse</span><span class="sxs-lookup"><span data-stu-id="5b3de-123">Mouse Input</span></span>

<span data-ttu-id="5b3de-124">È anche possibile usare l'input del mouse, anche in questo caso tramite i gestori di eventi di input CoreWindow UWP.</span><span class="sxs-lookup"><span data-stu-id="5b3de-124">You can also use mouse input, again via the UWP CoreWindow input event handlers.</span></span> <span data-ttu-id="5b3de-125">Di seguito viene illustrato come modificare il modello di app Windows Holographic per supportare i clic del mouse nella stesso modo come premuti movimenti.</span><span class="sxs-lookup"><span data-stu-id="5b3de-125">Here's how to modify the Windows Holographic app template to support mouse clicks in the same way as pressed gestures.</span></span> <span data-ttu-id="5b3de-126">Dopo aver apportato questa modifica, un clic del mouse durante l'uso di un dispositivo visore VR immersivi verrà riposizionata nel cubo.</span><span class="sxs-lookup"><span data-stu-id="5b3de-126">After making this modification, a mouse click while wearing an immersive headset device will reposition the cube.</span></span>

<span data-ttu-id="5b3de-127">Si noti che le app UWP possono anche ottenere dati XY non elaborati per il mouse tramite il [MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) API.</span><span class="sxs-lookup"><span data-stu-id="5b3de-127">Note that UWP apps can also get raw XY data for the mouse by using the [MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) API.</span></span>

<span data-ttu-id="5b3de-128">Per iniziare, dichiarare un nuovo gestore OnPointerPressed in AppView.h:</span><span class="sxs-lookup"><span data-stu-id="5b3de-128">Start by declaring a new OnPointerPressed handler in AppView.h:</span></span>

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

<span data-ttu-id="5b3de-129">In AppView.cpp, aggiungere questo codice al SetWindow:</span><span class="sxs-lookup"><span data-stu-id="5b3de-129">In AppView.cpp, add this code to SetWindow:</span></span>

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

<span data-ttu-id="5b3de-130">Inserire quindi questa definizione per OnPointerPressed nella parte inferiore del file:</span><span class="sxs-lookup"><span data-stu-id="5b3de-130">Then put this definition for OnPointerPressed at the bottom of the file:</span></span>

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

<span data-ttu-id="5b3de-131">Il gestore eventi che appena aggiunto è un pass-through alla classe principale del modello.</span><span class="sxs-lookup"><span data-stu-id="5b3de-131">The event handler we just added is a pass-through to the template main class.</span></span> <span data-ttu-id="5b3de-132">È possibile modificare la classe principale per supportare questo pass-through.</span><span class="sxs-lookup"><span data-stu-id="5b3de-132">Let's modify the main class to support this pass-through.</span></span> <span data-ttu-id="5b3de-133">Aggiungere questa dichiarazione di metodo pubblico per il file di intestazione:</span><span class="sxs-lookup"><span data-stu-id="5b3de-133">Add this public method declaration to the header file:</span></span>

```
// Handle mouse input.
       void OnPointerPressed();
```

<span data-ttu-id="5b3de-134">Questa variabile membro privata, nonché sarà necessario:</span><span class="sxs-lookup"><span data-stu-id="5b3de-134">You'll need this private member variable, as well:</span></span>

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

<span data-ttu-id="5b3de-135">Infine, si aggiornerà la classe principale con nuove per la logica per supportare i clic del mouse.</span><span class="sxs-lookup"><span data-stu-id="5b3de-135">Finally, we will update the main class with new logic to support mouse clicks.</span></span> <span data-ttu-id="5b3de-136">Iniziare aggiungendo il gestore eventi.</span><span class="sxs-lookup"><span data-stu-id="5b3de-136">Start by adding this event handler.</span></span> <span data-ttu-id="5b3de-137">Assicurarsi di aggiornare il nome della classe:</span><span class="sxs-lookup"><span data-stu-id="5b3de-137">Make sure to update the class name:</span></span>

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

<span data-ttu-id="5b3de-138">A questo punto, nel metodo di aggiornamento, sostituire la logica esistente per ottenere una puntatore posa con questo:</span><span class="sxs-lookup"><span data-stu-id="5b3de-138">Now, in the Update method, replace the existing logic for getting a pointer pose with this:</span></span>

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

<span data-ttu-id="5b3de-139">Ricompilare e ridistribuire.</span><span class="sxs-lookup"><span data-stu-id="5b3de-139">Recompile and redeploy.</span></span> <span data-ttu-id="5b3de-140">Si noterà che al clic del mouse ora verrà riposizionata del cubo nel visore VR immersivi - o HoloLens con bluetooth mouse collegato.</span><span class="sxs-lookup"><span data-stu-id="5b3de-140">You should notice that the mouse click will now reposition the cube in your immersive headset - or HoloLens with bluetooth mouse attached.</span></span>

### <a name="game-controller-support"></a><span data-ttu-id="5b3de-141">Supporto di gioco</span><span class="sxs-lookup"><span data-stu-id="5b3de-141">Game controller support</span></span>

<span data-ttu-id="5b3de-142">Periferiche di gioco possono essere un modo pratico di consentire all'utente di controllare un'esperienza di realtà mista di Windows e divertenti.</span><span class="sxs-lookup"><span data-stu-id="5b3de-142">Game controllers can be a fun and convenient way of allowing the user to control an immersive Windows Mixed Reality experience.</span></span>

<span data-ttu-id="5b3de-143">Aggiunta del supporto per periferiche di gioco per il modello di app Windows Holographic, il primo passaggio consiste nell'aggiungere le seguenti dichiarazioni di membro private alla classe dell'intestazione per il file principale:</span><span class="sxs-lookup"><span data-stu-id="5b3de-143">The first step in adding support for game controllers to the Windows Holographic app template, is to add the following private member declarations to the header class for your main file:</span></span>

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

<span data-ttu-id="5b3de-144">Inizializzare gli eventi su gamepad e qualsiasi gamepad attualmente connessa, nel costruttore per la classe principale:</span><span class="sxs-lookup"><span data-stu-id="5b3de-144">Initialize gamepad events, and any gamepads that are currently attached, in the constructor for your main class:</span></span>

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

<span data-ttu-id="5b3de-145">Aggiungere questi gestori eventi alla classe principale.</span><span class="sxs-lookup"><span data-stu-id="5b3de-145">Add these event handlers to your main class.</span></span> <span data-ttu-id="5b3de-146">Assicurarsi di aggiornare il nome della classe:</span><span class="sxs-lookup"><span data-stu-id="5b3de-146">Make sure to update the class name:</span></span>

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

<span data-ttu-id="5b3de-147">Infine, aggiornare la logica di input in modo che riconosca le modifiche di stato del controller.</span><span class="sxs-lookup"><span data-stu-id="5b3de-147">Finally, update the input logic to recognize changes in controller state.</span></span> <span data-ttu-id="5b3de-148">In questo caso, usiamo la stessa variabile m_pointerPressed illustrata nella sezione precedente per l'aggiunta di eventi del mouse.</span><span class="sxs-lookup"><span data-stu-id="5b3de-148">Here, we use the same m_pointerPressed variable discussed in the section above for adding mouse events.</span></span> <span data-ttu-id="5b3de-149">Aggiungere quanto segue al metodo Update, prima in cui verifica la presenza di SpatialPointerPose:</span><span class="sxs-lookup"><span data-stu-id="5b3de-149">Add this to the Update method, just before where it checks for the SpatialPointerPose:</span></span>

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

<span data-ttu-id="5b3de-150">Non dimenticare di annullare la registrazione di eventi durante la pulizia della classe principale:</span><span class="sxs-lookup"><span data-stu-id="5b3de-150">Don't forget to unregister the events when cleaning up the main class:</span></span>

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

<span data-ttu-id="5b3de-151">Ricompilare e ridistribuire.</span><span class="sxs-lookup"><span data-stu-id="5b3de-151">Recompile, and redeploy.</span></span> <span data-ttu-id="5b3de-152">È ora possibile collegare, o associare, periferica di gioco e usarlo per riposizionare il cubo rotante.</span><span class="sxs-lookup"><span data-stu-id="5b3de-152">You can now attach, or pair, a game controller and use it to reposition the spinning cube.</span></span>

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a><span data-ttu-id="5b3de-153">Importanti linee guida per l'input del mouse e tastiera</span><span class="sxs-lookup"><span data-stu-id="5b3de-153">Important guidelines for keyboard and mouse input</span></span>

<span data-ttu-id="5b3de-154">Esistono alcune differenze fondamentali nel modo in cui questo codice può essere utilizzato in Microsoft HoloLens, ovvero un dispositivo che si basa principalmente su input utente naturali – rispetto a ciò che è disponibile in un computer abilitato alla realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="5b3de-154">There are some key differences in how this code can be used on Microsoft HoloLens – which is a device that relies primarily on natural user input – versus what is available on a Windows Mixed Reality-enabled PC.</span></span>
* <span data-ttu-id="5b3de-155">È possibile basarsi sulla tastiera o del mouse di input deve per essere presente.</span><span class="sxs-lookup"><span data-stu-id="5b3de-155">You can’t rely on keyboard or mouse input to be present.</span></span> <span data-ttu-id="5b3de-156">Tutte le funzionalità dell'applicazione necessario collaborare con sguardo, gesti e l'input vocale.</span><span class="sxs-lookup"><span data-stu-id="5b3de-156">All of your app's functionality must work with gaze, gesture, and speech input.</span></span>
* <span data-ttu-id="5b3de-157">Quando è associata una tastiera Bluetooth, può essere utile abilitare l'input da tastiera per qualsiasi testo che potrebbe richiedere l'app.</span><span class="sxs-lookup"><span data-stu-id="5b3de-157">When a Bluetooth keyboard is attached, it can be helpful to enable keyboard input for any text that your app might ask for.</span></span> <span data-ttu-id="5b3de-158">Può trattarsi di un'integrazione ottima per la dettatura, ad esempio.</span><span class="sxs-lookup"><span data-stu-id="5b3de-158">This can be a great supplement for dictation, for example.</span></span>
* <span data-ttu-id="5b3de-159">Se si desidera progettare la tua app, non fare affidamento sugli WASD (ad esempio) e mouse cerca i controlli per il tuo gioco.</span><span class="sxs-lookup"><span data-stu-id="5b3de-159">When it comes to designing your app, don’t rely on (for example) WASD and mouse look controls for your game.</span></span> <span data-ttu-id="5b3de-160">HoloLens è progettato per l'utente per spostarsi nella stanza.</span><span class="sxs-lookup"><span data-stu-id="5b3de-160">HoloLens is designed for the user to walk around the room.</span></span> <span data-ttu-id="5b3de-161">In questo caso, l'utente controlla direttamente la fotocamera.</span><span class="sxs-lookup"><span data-stu-id="5b3de-161">In this case, the user controls the camera directly.</span></span> <span data-ttu-id="5b3de-162">Un'interfaccia per l'attivazione della fotocamera nella stanza con controlli di spostamento/aspetto non fornisce la stessa esperienza.</span><span class="sxs-lookup"><span data-stu-id="5b3de-162">An interface for driving the camera around the room with move/look controls won't provide the same experience.</span></span>
* <span data-ttu-id="5b3de-163">Input da tastiera può essere un ottimo modo per controllare gli aspetti di debug dell'app o il motore di gioco, soprattutto perché l'utente non dovranno usare la tastiera.</span><span class="sxs-lookup"><span data-stu-id="5b3de-163">Keyboard input can be an excellent way to control the debugging aspects of your app or game engine, especially since the user will not be required to use the keyboard.</span></span> <span data-ttu-id="5b3de-164">Il completamento dell'aggiunta di è lo stesso come è possibile usare, con API degli eventi CoreWindow.</span><span class="sxs-lookup"><span data-stu-id="5b3de-164">Wiring it up is the same as you're used to, with CoreWindow event APIs.</span></span> <span data-ttu-id="5b3de-165">In questo scenario, è possibile scegliere di implementare un modo per configurare l'app per instradare gli eventi della tastiera in una modalità "debug solo input" durante le sessioni di debug.</span><span class="sxs-lookup"><span data-stu-id="5b3de-165">In this scenario, you might choose to implement a way to configure your app to route keyboard events to a "debug input only" mode during your debug sessions.</span></span>
* <span data-ttu-id="5b3de-166">Controller Bluetooth attivati.</span><span class="sxs-lookup"><span data-stu-id="5b3de-166">Bluetooth controllers work as well.</span></span>

## <a name="see-also"></a><span data-ttu-id="5b3de-167">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5b3de-167">See also</span></span>
* [<span data-ttu-id="5b3de-168">Accessori hardware</span><span class="sxs-lookup"><span data-stu-id="5b3de-168">Hardware accessories</span></span>](hardware-accessories.md)

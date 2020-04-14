---
title: Input da tastiera, mouse e controller in DirectX
description: Viene illustrato come creare un'app per la realtà mista di Windows che usa i controller di tastiera, mouse e gioco.
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, tastiera, mouse, controller di gioco, Xbox Controller, HoloLens, desktop, procedura dettagliata, codice di esempio
ms.openlocfilehash: 27f1bf72435ce6889ba3f7b83664367a4440b162
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278089"
---
# <a name="keyboard-mouse-and-controller-input-in-directx"></a>Input da tastiera, mouse e controller in DirectX

Tastiere, topi e controller di gioco possono essere tutti formati utili per i dispositivi di realtà mista Windows. Le tastiere e i topi Bluetooth sono entrambi supportati in HoloLens, per l'uso con il debug dell'app o come forma alternativa di input. La realtà mista di Windows supporta anche auricolari immersivi collegati a PC, in cui i topi, le tastiere e i controller di gioco hanno storicamente la norma.

Per usare l'input da tastiera in HoloLens, associare una tastiera Bluetooth al dispositivo o usare l'input virtuale tramite il portale del dispositivo Windows. Per usare l'input da tastiera con una cuffia mista a realtà mista di Windows, assegnare lo stato attivo per l'input alla realtà mista inserendo sul dispositivo o usando la combinazione di tasti tasto Windows + Y. Tenere presente che le app destinate a HoloLens devono fornire funzionalità senza questi dispositivi collegati.

>[!NOTE]
>I frammenti di codice in questo articolo illustrano attualmente l' C++uso di/CX, invece di/WinRT conformi C++a C + 17 come usato nel modello di [ C++ progetto olografico](creating-a-holographic-directx-project.md).  I concetti sono equivalenti per C++un progetto/WinRT, anche se sarà necessario tradurre il codice.

## <a name="subscribe-for-corewindow-input-events"></a>Sottoscrivere gli eventi di input di CoreWindow

### <a name="keyboard-input"></a>Input da tastiera

Nel modello di app olografico di Windows è incluso un gestore eventi per l'input da tastiera come qualsiasi altra app UWP. L'app usa i dati di input della tastiera nello stesso modo in realtà mista di Windows.

Da AppView. cpp:

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

### <a name="virtual-keyboard-input"></a>Input tastiera virtuale
Per gli auricolari desktop immersivi è possibile supportare anche le tastiere virtuali di cui è stato eseguito il rendering da Windows attraverso la visualizzazione immersiva. Per supportare questa operazione, l'app può implementare **CoreTextEditContext**. Questo consente a Windows di comprendere lo stato delle caselle di testo sottoposte a rendering dell'app, in modo che la tastiera virtuale possa contribuire correttamente al testo presente.

Per ulteriori informazioni sull'implementazione del supporto CoreTextEditContext, vedere l' [esempio CoreTextEditContext](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).

### <a name="mouse-input"></a>Input del mouse

È anche possibile usare l'input del mouse, tramite i gestori eventi di input di UWP CoreWindow. Ecco come modificare il modello di app olografico di Windows per supportare i clic del mouse nello stesso modo dei movimenti premuti. Dopo aver apportato questa modifica, un clic del mouse quando si indossa un dispositivo headset immersivo riposiziona il cubo.

Si noti che le app UWP possono anche ottenere dati XY non elaborati per il mouse usando l'API [MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) .

Per iniziare, dichiarare un nuovo gestore OnPointerPressed in AppView. h:

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

In AppView. cpp aggiungere questo codice a Window:

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

Inserire quindi questa definizione per OnPointerPressed nella parte inferiore del file:

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

Il gestore eventi appena aggiunto è un pass-through alla classe principale del modello. Verrà ora modificata la classe principale per supportare questo pass-through. Aggiungere la dichiarazione del metodo public al file di intestazione:

```
// Handle mouse input.
       void OnPointerPressed();
```

Sarà necessaria anche questa variabile membro privata:

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

Infine, la classe principale viene aggiornata con la nuova logica per supportare i clic del mouse. Per iniziare, aggiungere questo gestore eventi. Assicurarsi di aggiornare il nome della classe:

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

A questo punto, nel metodo Update sostituire la logica esistente per ottenere un puntatore con questo:

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

Ricompilare e ridistribuire. Si noterà che il clic del mouse riposiziona il cubo nell'auricolare immersivo o HoloLens con il mouse Bluetooth collegato.

### <a name="game-controller-support"></a>Supporto del controller di gioco

I controller dei giochi possono essere un metodo divertente e pratico per consentire all'utente di controllare un'esperienza di realtà mista di Windows.

Il primo passaggio per aggiungere il supporto per i controller di gioco al modello di app olografico di Windows consiste nell'aggiungere le seguenti dichiarazioni di membro privato alla classe di intestazione per il file principale:

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

Inizializzare gli eventi del gamepad e gli eventuali gamepad attualmente collegati nel costruttore della classe principale:

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

Aggiungere i gestori eventi alla classe principale. Assicurarsi di aggiornare il nome della classe:

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

Infine, aggiornare la logica di input per riconoscere le modifiche nello stato del controller. Qui viene usata la stessa variabile di m_pointerPressed descritta nella sezione precedente per l'aggiunta di eventi del mouse. Aggiungere questo oggetto al metodo Update, immediatamente prima della posizione in cui viene verificato il SpatialPointerPose:

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

Non dimenticare di annullare la registrazione degli eventi durante la pulizia della classe principale:

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

Ricompilare e ridistribuire. È ora possibile associare, o associare, un controller di gioco e usarlo per riposizionare il cubo rotante.

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a>Linee guida importanti per l'input della tastiera e del mouse

Esistono alcune differenze fondamentali nel modo in cui questo codice può essere usato in Microsoft HoloLens, ovvero un dispositivo che si basa principalmente sull'input dell'utente naturale, rispetto a quello disponibile in un PC con Windows Mixed Reality-Enabled.
* Non è possibile fare affidamento sull'input della tastiera o del mouse per essere presente. Tutte le funzionalità dell'app devono funzionare con lo sguardo, il gesto e l'input vocale.
* Quando viene collegata una tastiera Bluetooth, può essere utile abilitare l'input da tastiera per qualsiasi testo che l'app potrebbe richiedere. Questo può essere un ottimo supplemento per la dettatura, ad esempio.
* Per quanto riguarda la progettazione dell'app, non fare affidamento su (ad esempio) i controlli WASD e mouse per il gioco. HoloLens è progettato per l'utente in modo da aggirare la stanza. In questo caso, l'utente controlla direttamente la fotocamera. Un'interfaccia per guidare la fotocamera attorno alla stanza con i controlli Move/look non fornirà la stessa esperienza.
* L'input da tastiera può essere un ottimo modo per controllare gli aspetti di debug dell'app o del motore di gioco, soprattutto perché l'utente non dovrà usare la tastiera. Il cablaggio è identico a quello usato per le API degli eventi CoreWindow. In questo scenario, è possibile scegliere di implementare un modo per configurare l'app per instradare gli eventi della tastiera a una modalità di "debug solo input" durante le sessioni di debug.
* Anche i controller Bluetooth funzionano.

## <a name="see-also"></a>Vedere anche
* [Accessori hardware](hardware-accessories.md)

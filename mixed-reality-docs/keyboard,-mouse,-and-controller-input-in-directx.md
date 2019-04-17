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
# <a name="keyboard-mouse-and-controller-input-in-directx"></a>Input di tastiera, mouse e controller DirectX

Tutte le tastiere, mouse e periferiche di gioco possono essere utile maschere di input per i dispositivi di realtà mista di Windows. Bluetooth tastiere e mouse vengono supportati sia su HoloLens, per l'uso con debug della tua app o come un tipo alternativo di input. Realtà mista di Windows supporta anche auricolari immersive collegati al PC - dove mice, tastiera e periferiche di gioco sono tradizionalmente la norma.

Per usare gli input da tastiera in HoloLens, coppia di una tastiera Bluetooth nel dispositivo oppure usare input virtuale tramite il Windows Device Portal. Per utilizzare input da tastiera durante indossare le cuffie immersive realtà mista di Windows, assegnare lo stato attivo per realtà mista da inserire nel dispositivo o usando il tasto Windows + Y combinazione di tasti. Tenere presente che le applicazioni destinate a HoloLens devono fornire funzionalità senza questi dispositivi collegati.

>[!NOTE]
>I frammenti di codice in questo articolo illustrano attualmente l'utilizzo di C++/CX invece di C + + 17 conformi C++/WinRT usato nel [ C++ modello di progetto holographic](creating-a-holographic-directx-project.md).  I concetti sono equivalenti per un C++progetto /WinRT, anche se è necessario convertire il codice.

## <a name="subscribe-for-corewindow-input-events"></a>La sottoscrizione per gli eventi di input CoreWindow

### <a name="keyboard-input"></a>Input da tastiera

Il modello di app Windows Holographic, include un gestore eventi per l'input da tastiera come qualsiasi altra app UWP. L'app utilizza i dati di input di tastiera simile a quello nella realtà mista di Windows.

Da AppView.cpp:

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

### <a name="virtual-keyboard-input"></a>Input da tastiera virtuale
Per immersive auricolari desktop, è anche possibile supportare tastiere virtuale sottoposto a rendering dal Windows tramite la vista coinvolgente e concreto. A tale scopo, è possibile implementare l'app **CoreTextEditContext**. In questo modo Windows comprendere lo stato propria app con rendering di caselle di testo, in modo che la tastiera virtuale correttamente può contribuire a presenti il testo.

Per altre informazioni sull'implementazione CoreTextEditContext supporto, vedere la [CoreTextEditContext esempio](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).

### <a name="mouse-input"></a>Input del mouse

È anche possibile usare l'input del mouse, anche in questo caso tramite i gestori di eventi di input CoreWindow UWP. Di seguito viene illustrato come modificare il modello di app Windows Holographic per supportare i clic del mouse nella stesso modo come premuti movimenti. Dopo aver apportato questa modifica, un clic del mouse durante l'uso di un dispositivo visore VR immersivi verrà riposizionata nel cubo.

Si noti che le app UWP possono anche ottenere dati XY non elaborati per il mouse tramite il [MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) API.

Per iniziare, dichiarare un nuovo gestore OnPointerPressed in AppView.h:

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

In AppView.cpp, aggiungere questo codice al SetWindow:

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

Il gestore eventi che appena aggiunto è un pass-through alla classe principale del modello. È possibile modificare la classe principale per supportare questo pass-through. Aggiungere questa dichiarazione di metodo pubblico per il file di intestazione:

```
// Handle mouse input.
       void OnPointerPressed();
```

Questa variabile membro privata, nonché sarà necessario:

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

Infine, si aggiornerà la classe principale con nuove per la logica per supportare i clic del mouse. Iniziare aggiungendo il gestore eventi. Assicurarsi di aggiornare il nome della classe:

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

A questo punto, nel metodo di aggiornamento, sostituire la logica esistente per ottenere una puntatore posa con questo:

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

Ricompilare e ridistribuire. Si noterà che al clic del mouse ora verrà riposizionata del cubo nel visore VR immersivi - o HoloLens con bluetooth mouse collegato.

### <a name="game-controller-support"></a>Supporto di gioco

Periferiche di gioco possono essere un modo pratico di consentire all'utente di controllare un'esperienza di realtà mista di Windows e divertenti.

Aggiunta del supporto per periferiche di gioco per il modello di app Windows Holographic, il primo passaggio consiste nell'aggiungere le seguenti dichiarazioni di membro private alla classe dell'intestazione per il file principale:

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

Inizializzare gli eventi su gamepad e qualsiasi gamepad attualmente connessa, nel costruttore per la classe principale:

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

Aggiungere questi gestori eventi alla classe principale. Assicurarsi di aggiornare il nome della classe:

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

Infine, aggiornare la logica di input in modo che riconosca le modifiche di stato del controller. In questo caso, usiamo la stessa variabile m_pointerPressed illustrata nella sezione precedente per l'aggiunta di eventi del mouse. Aggiungere quanto segue al metodo Update, prima in cui verifica la presenza di SpatialPointerPose:

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

Non dimenticare di annullare la registrazione di eventi durante la pulizia della classe principale:

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

Ricompilare e ridistribuire. È ora possibile collegare, o associare, periferica di gioco e usarlo per riposizionare il cubo rotante.

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a>Importanti linee guida per l'input del mouse e tastiera

Esistono alcune differenze fondamentali nel modo in cui questo codice può essere utilizzato in Microsoft HoloLens, ovvero un dispositivo che si basa principalmente su input utente naturali – rispetto a ciò che è disponibile in un computer abilitato alla realtà mista di Windows.
* È possibile basarsi sulla tastiera o del mouse di input deve per essere presente. Tutte le funzionalità dell'applicazione necessario collaborare con sguardo, gesti e l'input vocale.
* Quando è associata una tastiera Bluetooth, può essere utile abilitare l'input da tastiera per qualsiasi testo che potrebbe richiedere l'app. Può trattarsi di un'integrazione ottima per la dettatura, ad esempio.
* Se si desidera progettare la tua app, non fare affidamento sugli WASD (ad esempio) e mouse cerca i controlli per il tuo gioco. HoloLens è progettato per l'utente per spostarsi nella stanza. In questo caso, l'utente controlla direttamente la fotocamera. Un'interfaccia per l'attivazione della fotocamera nella stanza con controlli di spostamento/aspetto non fornisce la stessa esperienza.
* Input da tastiera può essere un ottimo modo per controllare gli aspetti di debug dell'app o il motore di gioco, soprattutto perché l'utente non dovranno usare la tastiera. Il completamento dell'aggiunta di è lo stesso come è possibile usare, con API degli eventi CoreWindow. In questo scenario, è possibile scegliere di implementare un modo per configurare l'app per instradare gli eventi della tastiera in una modalità "debug solo input" durante le sessioni di debug.
* Controller Bluetooth attivati.

## <a name="see-also"></a>Vedere anche
* [Accessori hardware](hardware-accessories.md)

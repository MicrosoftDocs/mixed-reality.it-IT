---
title: Aggiungere .NET remoting holographic
description: Viene illustrato come utilizzare i servizi remoti Holographic per il rendering vntana un HoloLens in rete.
author: MikeRiches
ms.author: mriches
ms.date: 05/24/2019
ms.topic: article
keywords: Realtà mista di Windows, vntana, holographic .NET remoting, remoto per il rendering, rete per il rendering, HoloLens, vntana remoto
ms.openlocfilehash: 8d645f634ff0fc820893f5554fd602aa3a2f38e3
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829625"
---
# <a name="add-holographic-remoting"></a><span data-ttu-id="a3190-104">Aggiungere .NET remoting holographic</span><span class="sxs-lookup"><span data-stu-id="a3190-104">Add holographic remoting</span></span>

## <a name="hololens-2"></a><span data-ttu-id="a3190-105">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="a3190-105">HoloLens 2</span></span>

> [!NOTE]
> <span data-ttu-id="a3190-106">Altre indicazioni specifiche su 2 HoloLens [presto](index.md#news-and-notes).</span><span class="sxs-lookup"><span data-stu-id="a3190-106">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

<span data-ttu-id="a3190-107">Gli sviluppatori di HoloLens che utilizzano .NET Remoting Holographic sarà necessario aggiornare le proprie App per renderli compatibili con 2 HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a3190-107">HoloLens developers using Holographic Remoting will need to update their apps to make them compatible with HoloLens 2.</span></span>  <span data-ttu-id="a3190-108">Questo richiederà una nuova versione del pacchetto NuGet di .NET Remoting Holographic che non è ancora disponibile pubblicamente.</span><span class="sxs-lookup"><span data-stu-id="a3190-108">This will require a new version of the Holographic Remoting NuGet package that is not publicly available yet.</span></span>  <span data-ttu-id="a3190-109">Se un'applicazione usando il pacchetto NuGet di HoloLens tenta di connettersi al lettore di .NET Remoting Holographic in 2 HoloLens, la connessione avrà esito negativo.</span><span class="sxs-lookup"><span data-stu-id="a3190-109">If an application using the HoloLens NuGet package attempts to connect to the Holographic Remoting Player on HoloLens 2, the connection will fail.</span></span>  <span data-ttu-id="a3190-110">Guarda questa pagina per gli aggiornamenti quando il pacchetto NuGet 2 HoloLens è disponibile.</span><span class="sxs-lookup"><span data-stu-id="a3190-110">Watch this page for updates once the HoloLens 2 NuGet package is available.</span></span>

## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a><span data-ttu-id="a3190-111">Aggiungere .NET remoting holographic a un'app UWP o il desktop</span><span class="sxs-lookup"><span data-stu-id="a3190-111">Add holographic remoting to your desktop or UWP app</span></span>

<span data-ttu-id="a3190-112">Questa pagina descrive come aggiungere Holographic .NET Remoting a un desktop o un'app UWP.</span><span class="sxs-lookup"><span data-stu-id="a3190-112">This page describes how to add Holographic Remoting to a desktop or UWP app.</span></span>

<span data-ttu-id="a3190-113">.NET remoting holographic consente all'app come destinazione un HoloLens con holographic contenuto ospitato in un PC desktop o in un dispositivo UWP, ad esempio Xbox One, consentendo l'accesso a più risorse di sistema e rendendo possibile l'integrazione remota [coinvolgenti visualizzazioni](app-views.md) nel software di PC desktop esistente.</span><span class="sxs-lookup"><span data-stu-id="a3190-113">Holographic remoting allows your app to target a HoloLens with holographic content hosted on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources and making it possible to integrate remote [immersive views](app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="a3190-114">Un'applicazione host .NET remoting riceve un flusso di dati di input da un HoloLens, esegue il rendering di contenuto in una vista virtuale coinvolgente e trasmette i frame di contenuto a HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a3190-114">A remoting host app receives an input data stream from a HoloLens, renders content in a virtual immersive view, and streams content frames back to HoloLens.</span></span> <span data-ttu-id="a3190-115">Viene stabilita la connessione tramite Wi-Fi standard.</span><span class="sxs-lookup"><span data-stu-id="a3190-115">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="a3190-116">Per utilizzare .NET remoting, si verrà utilizzare un pacchetto NuGet per aggiungere remoting holographic a un'app UWP o il desktop e scrivere codice per gestire la connessione e per eseguire il rendering in una vista coinvolgente e concreto.</span><span class="sxs-lookup"><span data-stu-id="a3190-116">To use remoting, you will use a NuGet package to add holographic remoting to your desktop or UWP app, and write code to handle the connection and to render in an immersive view.</span></span> <span data-ttu-id="a3190-117">Librerie di supporto sono inclusi nell'esempio di codice che consentono di semplificare l'attività di gestire la connessione al dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a3190-117">Helper libraries are included in the code sample that simplify the task of handling the device connection.</span></span>

<span data-ttu-id="a3190-118">Una connessione remota tipica avrà minimo a 50 ms di latenza.</span><span class="sxs-lookup"><span data-stu-id="a3190-118">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="a3190-119">L'app di Windows Media player può segnalare la latenza in tempo reale.</span><span class="sxs-lookup"><span data-stu-id="a3190-119">The player app can report the latency in real-time.</span></span>

>[!NOTE]
><span data-ttu-id="a3190-120">I frammenti di codice in questo articolo illustrano attualmente l'utilizzo di C++/CX invece di C + + 17 conformi C++/WinRT usato nel [ C++ modello di progetto holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="a3190-120">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="a3190-121">I concetti sono equivalenti per un C++progetto /WinRT, anche se è necessario convertire il codice.</span><span class="sxs-lookup"><span data-stu-id="a3190-121">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

### <a name="get-the-remoting-nuget-packages"></a><span data-ttu-id="a3190-122">Ottenere i pacchetti NuGet di .NET remoting</span><span class="sxs-lookup"><span data-stu-id="a3190-122">Get the remoting NuGet packages</span></span>

<span data-ttu-id="a3190-123">Seguire questi passaggi per ottenere il pacchetto NuGet per la comunicazione remota holographic e aggiungere un riferimento dal progetto:</span><span class="sxs-lookup"><span data-stu-id="a3190-123">Follow these steps to get the NuGet package for holographic remoting, and add a reference from your project:</span></span>
1. <span data-ttu-id="a3190-124">Accedere al progetto in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a3190-124">Go to your project in Visual Studio.</span></span>
2. <span data-ttu-id="a3190-125">Fare doppio clic sul nodo del progetto e selezionare **Gestisci pacchetti NuGet...**</span><span class="sxs-lookup"><span data-stu-id="a3190-125">Right-click on the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="a3190-126">Nel pannello che viene visualizzata, fare clic su **esplorare** e quindi cercare "Holographic la comunicazione remota".</span><span class="sxs-lookup"><span data-stu-id="a3190-126">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="a3190-127">Selezionare **Microsoft.Holographic.Remoting** e fare clic su **installare**.</span><span class="sxs-lookup"><span data-stu-id="a3190-127">Select **Microsoft.Holographic.Remoting** and click **Install**.</span></span>
5. <span data-ttu-id="a3190-128">Se il **Preview** finestra di dialogo viene visualizzata, fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="a3190-128">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="a3190-129">Finestra di dialogo successiva visualizzata è il contratto di licenza.</span><span class="sxs-lookup"><span data-stu-id="a3190-129">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="a3190-130">Fare clic su **accetto** per accettare il contratto di licenza.</span><span class="sxs-lookup"><span data-stu-id="a3190-130">Click on **I Accept** to accept the license agreement.</span></span>

### <a name="create-the-holographicstreamerhelpers"></a><span data-ttu-id="a3190-131">Creare il HolographicStreamerHelpers</span><span class="sxs-lookup"><span data-stu-id="a3190-131">Create the HolographicStreamerHelpers</span></span>

<span data-ttu-id="a3190-132">In primo luogo, è necessaria un'istanza di HolographicStreamerHelpers.</span><span class="sxs-lookup"><span data-stu-id="a3190-132">First, we need an instance of HolographicStreamerHelpers.</span></span> <span data-ttu-id="a3190-133">Aggiungere questo elemento alla classe che gestiscono i servizi remoti.</span><span class="sxs-lookup"><span data-stu-id="a3190-133">Add this to the class that will be handling remoting.</span></span>

```
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

<span data-ttu-id="a3190-134">È inoltre necessario tenere traccia dello stato di connessione.</span><span class="sxs-lookup"><span data-stu-id="a3190-134">You'll also need to track connection state.</span></span> <span data-ttu-id="a3190-135">Se si desidera eseguire il rendering di anteprima, è necessario disporre di una trama da copiare.</span><span class="sxs-lookup"><span data-stu-id="a3190-135">If you want to render the preview, you need to have a texture to copy it to.</span></span> <span data-ttu-id="a3190-136">Anche necessario alcuni aspetti, ad esempio un blocco dello stato di connessione, un modo per archiviare l'indirizzo IP di HoloLens e così via.</span><span class="sxs-lookup"><span data-stu-id="a3190-136">You also need a few things like a connection state lock, some way of storing the IP address of HoloLens, and so on.</span></span>

```
private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;

       Microsoft::WRL::Wrappers::SRWLock                   m_connectionStateLock;

       RemotingHostSample::AppView^                        m_appView;
       Platform::String^                                   m_ipAddress;
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;

       Microsoft::WRL::Wrappers::CriticalSection           m_deviceLock;
       Microsoft::WRL::ComPtr<IDXGISwapChain1>             m_swapChain;
       Microsoft::WRL::ComPtr<ID3D11Texture2D>             m_spTexture;
```

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a><span data-ttu-id="a3190-137">Inizializzare HolographicStreamerHelpers e connettersi a HoloLens</span><span class="sxs-lookup"><span data-stu-id="a3190-137">Initialize HolographicStreamerHelpers and connect to HoloLens</span></span>

<span data-ttu-id="a3190-138">Per connettersi a un dispositivo HoloLens, creare un'istanza di HolographicStreamerHelpers e connettersi all'indirizzo IP di destinazione.</span><span class="sxs-lookup"><span data-stu-id="a3190-138">To connect to a HoloLens device, create an instance of HolographicStreamerHelpers and connect to the target IP address.</span></span> <span data-ttu-id="a3190-139">È necessario impostare le dimensioni del fotogramma video in modo che corrisponda la larghezza di visualizzazione di HoloLens e l'altezza, in quanto la libreria .NET Remoting Holographic prevede che il codificatore e decodificatore risoluzioni in modo che corrisponda esattamente.</span><span class="sxs-lookup"><span data-stu-id="a3190-139">You will need to set the video frame size to match the HoloLens display width and height, because the Holographic Remoting library expects the encoder and decoder resolutions to match exactly.</span></span>

```
m_streamerHelpers = ref new HolographicStreamerHelpers();
       m_streamerHelpers->CreateStreamer(m_d3dDevice);

       // We currently need to stream at 720p because that's the resolution of our remote display.
       // There is a check in the holographic streamer that makes sure the remote and local
       // resolutions match. The default streamer resolution is 1080p.
       m_streamerHelpers->SetVideoFrameSize(1280, 720);

       try
       {
           m_streamerHelpers->Connect(m_ipAddress->Data(), 8001);
       }
       catch (Platform::Exception^ ex)
       {
           DebugLog(L"Connect failed with hr = 0x%08X", ex->HResult);
       }
```

<span data-ttu-id="a3190-140">La connessione del dispositivo è asincrona.</span><span class="sxs-lookup"><span data-stu-id="a3190-140">The device connection is asynchronous.</span></span> <span data-ttu-id="a3190-141">Le esigenze delle app per fornire i gestori eventi per connettersi, disconnettersi e frame di inviare eventi.</span><span class="sxs-lookup"><span data-stu-id="a3190-141">Your app needs to provide event handlers for connect, disconnect, and frame send events.</span></span>

<span data-ttu-id="a3190-142">L'evento OnConnected può aggiornare l'interfaccia utente, avvio del rendering e così via.</span><span class="sxs-lookup"><span data-stu-id="a3190-142">The OnConnected event can update the UI, start rendering, and so on.</span></span> <span data-ttu-id="a3190-143">Nel nostro esempio di codice per il desktop, è aggiornare il titolo della finestra con un messaggio di "connessione".</span><span class="sxs-lookup"><span data-stu-id="a3190-143">In our desktop code sample, we update the window title with a "connected" message.</span></span>

```
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

<span data-ttu-id="a3190-144">Può gestire l'evento OnDisconnected riconnessione, aggiornamenti dell'interfaccia utente e così via.</span><span class="sxs-lookup"><span data-stu-id="a3190-144">The OnDisconnected event can handle reconnection, UI updates, and so on.</span></span> <span data-ttu-id="a3190-145">In questo esempio è ristabilire la connessione se si verifica un errore temporaneo.</span><span class="sxs-lookup"><span data-stu-id="a3190-145">In this example, we reconnect if there is a transient failure.</span></span>

```
Platform::WeakReference streamerHelpersWeakRef = Platform::WeakReference(m_streamerHelpers);
       m_streamerHelpers->OnDisconnected += ref new DisconnectedEvent(
           [this, streamerHelpersWeakRef](_In_ HolographicStreamerConnectionFailureReason failureReason)
           {
               DebugLog(L"Disconnected with reason %d", failureReason);
               UpdateWindowTitle();

               // Reconnect if this is a transient failure.
               if (failureReason == HolographicStreamerConnectionFailureReason::Unreachable ||
                   failureReason == HolographicStreamerConnectionFailureReason::ConnectionLost)
               {
                   DebugLog(L"Reconnecting...");

                   try
                   {
                       auto helpersResolved = streamerHelpersWeakRef.Resolve<HolographicStreamerHelpers>();
                       if (helpersResolved)
                       {
                           helpersResolved->Connect(m_ipAddress->Data(), 8001);
                       }
                       else
                       {
                           DebugLog(L"Failed to reconnect because a disconnect has already occurred.\n");
                       }
                   }
                   catch (Platform::Exception^ ex)
                   {
                       DebugLog(L"Connect failed with hr = 0x%08X", ex->HResult);
                   }
               }
               else
               {
                   DebugLog(L"Disconnected with unrecoverable error, not attempting to reconnect.");
               }
           });
```

<span data-ttu-id="a3190-146">Quando il componente di .NET remoting è pronto per l'invio di un frame, l'app viene fornita un'opportunità per creare una copia di esso nel SendFrameEvent.</span><span class="sxs-lookup"><span data-stu-id="a3190-146">When the remoting component is ready to send a frame, your app is provided an opportunity to make a copy of it in the SendFrameEvent.</span></span> <span data-ttu-id="a3190-147">In questo caso, deve essere copiato il frame di una catena di scambio in modo che è possibile visualizzarla in una finestra di anteprima.</span><span class="sxs-lookup"><span data-stu-id="a3190-147">Here, we copy the frame to a swap chain so that we can display it in a preview window.</span></span>

```
m_streamerHelpers->OnSendFrame += ref new SendFrameEvent(
           [this](_In_ const ComPtr<ID3D11Texture2D>& spTexture, _In_ FrameMetadata metadata)
           {
               if (m_showPreview)
               {
                   ComPtr<ID3D11Device1> spDevice = m_appView->GetDeviceResources()->GetD3DDevice();
                   ComPtr<ID3D11DeviceContext> spContext = m_appView->GetDeviceResources()->GetD3DDeviceContext();

                   ComPtr<ID3D11Texture2D> spBackBuffer;
                   ThrowIfFailed(m_swapChain->GetBuffer(0, IID_PPV_ARGS(&spBackBuffer)));

                   spContext->CopySubresourceRegion(
                       spBackBuffer.Get(), // dest
                       0,                  // dest subresource
                       0, 0, 0,            // dest x, y, z
                       spTexture.Get(),    // source
                       0,                  // source subresource
                       nullptr);           // source box, null means the entire resource

                   DXGI_PRESENT_PARAMETERS parameters = { 0 };
                   ThrowIfFailed(m_swapChain->Present1(1, 0, &parameters));
               }
           });
```

### <a name="render-holographic-content"></a><span data-ttu-id="a3190-148">Il rendering del contenuto holographic</span><span class="sxs-lookup"><span data-stu-id="a3190-148">Render holographic content</span></span>

<span data-ttu-id="a3190-149">Per eseguire il rendering del contenuto tramite la comunicazione remota, si imposta una IFrameworkView virtuale all'interno di un'app UWP o il desktop ed elaborare holographic frame da servizi remoti .NET.</span><span class="sxs-lookup"><span data-stu-id="a3190-149">To render content using remoting, you set up a virtual IFrameworkView within your desktop or UWP app and process holographic frames from remoting.</span></span> <span data-ttu-id="a3190-150">Tutte le API di Windows Holographic sono Usa che esattamente da questa visualizzazione, ma è configurato in modo leggermente diverso.</span><span class="sxs-lookup"><span data-stu-id="a3190-150">All of the Windows Holographic APIs are uses the same way by this view, but it is set up slightly differently.</span></span>

<span data-ttu-id="a3190-151">Anziché crearne di nuove autonomamente, i componenti dello spazio e riconoscimento vocale holographic provengono dalla classe HolographicRemotingHelpers:</span><span class="sxs-lookup"><span data-stu-id="a3190-151">Instead of creating them yourself, the holographic space and speech components come from your HolographicRemotingHelpers class:</span></span>

```
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

<span data-ttu-id="a3190-152">Invece di usare un ciclo di aggiornamento all'interno di un metodo di esecuzione, è fornire gli aggiornamenti dei segni di graduazione dal ciclo principale del desktop o dell'app UWP.</span><span class="sxs-lookup"><span data-stu-id="a3190-152">Instead of using an update loop inside of a Run method, you provide tick updates from the main loop of your desktop or UWP app.</span></span> <span data-ttu-id="a3190-153">In questo modo il desktop o app UWP per rimanere in controllo dell'elaborazione del messaggio.</span><span class="sxs-lookup"><span data-stu-id="a3190-153">This allows your desktop or UWP app to remain in control of message processing.</span></span>

```
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

<span data-ttu-id="a3190-154">Metodo Tick() della visualizzazione olografica app completa un'iterazione dell'aggiornamento, draw, ciclo presenta.</span><span class="sxs-lookup"><span data-stu-id="a3190-154">The holographic app view's Tick() method completes one iteration of the update, draw, present loop.</span></span>

```
void AppView::Tick()
   {
       if (m_main)
       {
           // When running on Windows Holographic, we can use the holographic rendering system.
           HolographicFrame^ holographicFrame = m_main->Update();

           if (holographicFrame && m_main->Render(holographicFrame))
           {
               // The holographic frame has an API that presents the swap chain for each
               // holographic camera.
               m_deviceResources->Present(holographicFrame);
           }
       }
   }
```

<span data-ttu-id="a3190-155">L'aggiornamento della visualizzazione olografica app, rendering e ciclo presenta è esattamente lo stesso di quando in esecuzione su HoloLens - ad eccezione del fatto che si ha accesso a una maggiore quantità di risorse di sistema nel PC desktop.</span><span class="sxs-lookup"><span data-stu-id="a3190-155">The holographic app view update, render, and present loop is exactly the same as it is when running on HoloLens - except that you have access to a much greater amount of system resources on your desktop PC.</span></span> <span data-ttu-id="a3190-156">È possibile eseguire il rendering di molte altre triangoli, avere ulteriori passaggi di disegni, eseguire ulteriori fisica e usano x64 processi per caricare il contenuto che richiede più di 2 GB di RAM.</span><span class="sxs-lookup"><span data-stu-id="a3190-156">You can render many more triangles, have more drawing passes, do more physics, and use x64 processes to load content that requires more than 2 GB of RAM.</span></span>

### <a name="disconnect-and-end-the-remote-session"></a><span data-ttu-id="a3190-157">Disconnettersi e terminare la sessione remota</span><span class="sxs-lookup"><span data-stu-id="a3190-157">Disconnect and end the remote session</span></span>

<span data-ttu-id="a3190-158">Per disconnettere - ad esempio, quando l'utente sceglie un pulsante di interfaccia utente di disconnettere - chiamare Disconnect () sul HolographicStreamerHelpers e infine rilasciare l'oggetto.</span><span class="sxs-lookup"><span data-stu-id="a3190-158">To disconnect - for example, when the user clicks a UI button to disconnect - call Disconnect() on the HolographicStreamerHelpers, and then release the object.</span></span>

```
void DesktopWindow::DisconnectFromRemoteDevice()
   {
       // Disconnecting from the remote device can change the connection state.
       auto exclusiveLock = m_connectionStateLock.LockExclusive();

       if (m_streamerHelpers != nullptr)
       {
           m_streamerHelpers->Disconnect();

           // Reset state
           m_streamerHelpers = nullptr;
       }
   }
```

## <a name="get-the-remoting-player"></a><span data-ttu-id="a3190-159">Ottenere il lettore di servizi remoti</span><span class="sxs-lookup"><span data-stu-id="a3190-159">Get the remoting player</span></span>

<span data-ttu-id="a3190-160">L'assegnatario di comunicazione remota di Windows Holographic è disponibile in app store di Windows come endpoint per la comunicazione remota di hosting di App a cui connettersi.</span><span class="sxs-lookup"><span data-stu-id="a3190-160">The Windows Holographic remoting player is offered in the Windows app store as an endpoint for remoting host apps to connect to.</span></span> <span data-ttu-id="a3190-161">Per ottenere l'assegnatario di comunicazione remota di Windows Holographic, visitare l'app di Windows store da di HoloLens, ricerca per la comunicazione remota e scaricare l'app.</span><span class="sxs-lookup"><span data-stu-id="a3190-161">To get the Windows Holographic remoting player, visit the Windows app store from your HoloLens, search for Remoting, and download the app.</span></span> <span data-ttu-id="a3190-162">Il giocatore remoto include una funzionalità per visualizzare le statistiche su schermo, che può essere utile durante il debug di .NET remoting hosting delle app.</span><span class="sxs-lookup"><span data-stu-id="a3190-162">The remoting player includes a feature to display statistics on-screen, which can be useful when debugging remoting host apps.</span></span>

## <a name="notes-and-resources"></a><span data-ttu-id="a3190-163">Note e le risorse</span><span class="sxs-lookup"><span data-stu-id="a3190-163">Notes and resources</span></span>

<span data-ttu-id="a3190-164">La visualizzazione olografica app sarà necessario un modo per fornire all'app con il dispositivo Direct3D, che deve essere utilizzato per inizializzare lo spazio holographic.</span><span class="sxs-lookup"><span data-stu-id="a3190-164">The holographic app view will need a way to provide your app with the Direct3D device, which must be used to initialize the holographic space.</span></span> <span data-ttu-id="a3190-165">L'app deve usare questo dispositivo Direct3D per copiare e visualizzare il frame di anteprima.</span><span class="sxs-lookup"><span data-stu-id="a3190-165">Your app should use this Direct3D device to copy and display the preview frame.</span></span>

```
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

<span data-ttu-id="a3190-166">**Esempio di codice:** Un esempio di codice .NET Remoting Holographic completo è disponibile, che include una visualizzazione olografica applicazione compatibile con .NET remoting e di host .NET remoting per desktop Win32, DirectX UWP e UWP con XAML.</span><span class="sxs-lookup"><span data-stu-id="a3190-166">**Code sample:** A complete Holographic Remoting code sample is available, which includes a holographic application view that is compatible with remoting and remoting host projects for desktop Win32, UWP DirectX, and UWP with XAML.</span></span> <span data-ttu-id="a3190-167">Per ottenerlo, fare clic qui:</span><span class="sxs-lookup"><span data-stu-id="a3190-167">To get it, go here:</span></span>
* [<span data-ttu-id="a3190-168">Esempio di codice Holographic Windows per la comunicazione remota</span><span class="sxs-lookup"><span data-stu-id="a3190-168">Windows Holographic Code Sample for Remoting</span></span>](https://github.com/Microsoft/HoloLensCompanionKit/)

<span data-ttu-id="a3190-169">**Nota di debug:** La libreria .NET Remoting Holographic può generare eccezioni first-chance.</span><span class="sxs-lookup"><span data-stu-id="a3190-169">**Debugging note:** The Holographic Remoting library can throw first-chance exceptions.</span></span> <span data-ttu-id="a3190-170">Queste eccezioni possono essere visibili nella sessione, a seconda delle impostazioni di eccezione di Visual Studio attivi al momento di debug.</span><span class="sxs-lookup"><span data-stu-id="a3190-170">These exceptions may be visible in debugging sessions, depending on the Visual Studio exception settings that are active at the time.</span></span> <span data-ttu-id="a3190-171">Queste eccezioni vengono intercettate internamente dalla libreria di .NET Remoting Holographic e possono essere ignorate.</span><span class="sxs-lookup"><span data-stu-id="a3190-171">These exceptions are caught internally by the Holographic Remoting library and can be ignored.</span></span>

---
title: Aggiungere la comunicazione remota olografica
description: Viene illustrato come usare la comunicazione remota olografica per eseguire il rendering degli ologrammi in una HoloLens in rete.
author: MikeRiches
ms.author: mriches
ms.date: 05/24/2019
ms.topic: article
keywords: Realtà mista di Windows, ologrammi, comunicazione remota olografica, rendering remoto, rendering di rete, HoloLens, ologrammi remoti
ms.openlocfilehash: 8d645f634ff0fc820893f5554fd602aa3a2f38e3
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829625"
---
# <a name="add-holographic-remoting"></a><span data-ttu-id="32944-104">Aggiungere la comunicazione remota olografica</span><span class="sxs-lookup"><span data-stu-id="32944-104">Add holographic remoting</span></span>

## <a name="hololens-2"></a><span data-ttu-id="32944-105">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="32944-105">HoloLens 2</span></span>

> [!NOTE]
> <span data-ttu-id="32944-106">Altre indicazioni specifiche per HoloLens 2 [saranno presto](index.md#news-and-notes)disponibili.</span><span class="sxs-lookup"><span data-stu-id="32944-106">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

<span data-ttu-id="32944-107">Gli sviluppatori HoloLens che usano la comunicazione remota olografica dovranno aggiornare le proprie app per renderle compatibili con HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="32944-107">HoloLens developers using Holographic Remoting will need to update their apps to make them compatible with HoloLens 2.</span></span>  <span data-ttu-id="32944-108">Questa operazione richiederà una nuova versione del pacchetto NuGet per la comunicazione remota olografica, che non è ancora disponibile pubblicamente.</span><span class="sxs-lookup"><span data-stu-id="32944-108">This will require a new version of the Holographic Remoting NuGet package that is not publicly available yet.</span></span>  <span data-ttu-id="32944-109">Se un'applicazione che usa il pacchetto NuGet HoloLens tenta di connettersi al lettore di comunicazione remota olografica in HoloLens 2, la connessione avrà esito negativo.</span><span class="sxs-lookup"><span data-stu-id="32944-109">If an application using the HoloLens NuGet package attempts to connect to the Holographic Remoting Player on HoloLens 2, the connection will fail.</span></span>  <span data-ttu-id="32944-110">Guardare questa pagina per gli aggiornamenti dopo che è disponibile il pacchetto NuGet HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="32944-110">Watch this page for updates once the HoloLens 2 NuGet package is available.</span></span>

## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a><span data-ttu-id="32944-111">Aggiungere la comunicazione remota olografica all'app desktop o UWP</span><span class="sxs-lookup"><span data-stu-id="32944-111">Add holographic remoting to your desktop or UWP app</span></span>

<span data-ttu-id="32944-112">Questa pagina descrive come aggiungere la comunicazione remota olografica a un'app desktop o UWP.</span><span class="sxs-lookup"><span data-stu-id="32944-112">This page describes how to add Holographic Remoting to a desktop or UWP app.</span></span>

<span data-ttu-id="32944-113">La comunicazione remota olografica consente all'app di avere come destinazione un HoloLens con contenuto olografico ospitato in un computer desktop o in un dispositivo UWP, ad esempio la Xbox One, consentendo l'accesso a più risorse di sistema e rendendo possibile l'integrazione di [visualizzazioni immersive](app-views.md) remote in software per PC desktop esistente.</span><span class="sxs-lookup"><span data-stu-id="32944-113">Holographic remoting allows your app to target a HoloLens with holographic content hosted on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources and making it possible to integrate remote [immersive views](app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="32944-114">Un'app host Remoting riceve un flusso di dati di input da un HoloLens, esegue il rendering del contenuto in una visualizzazione immersiva virtuale e trasmette i frame di contenuto a HoloLens.</span><span class="sxs-lookup"><span data-stu-id="32944-114">A remoting host app receives an input data stream from a HoloLens, renders content in a virtual immersive view, and streams content frames back to HoloLens.</span></span> <span data-ttu-id="32944-115">La connessione viene eseguita usando il Wi-Fi standard.</span><span class="sxs-lookup"><span data-stu-id="32944-115">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="32944-116">Per usare la comunicazione remota, si userà un pacchetto NuGet per aggiungere la comunicazione remota olografica all'app desktop o UWP e scrivere il codice per gestire la connessione e per eseguire il rendering in una visualizzazione immersiva.</span><span class="sxs-lookup"><span data-stu-id="32944-116">To use remoting, you will use a NuGet package to add holographic remoting to your desktop or UWP app, and write code to handle the connection and to render in an immersive view.</span></span> <span data-ttu-id="32944-117">Le librerie helper sono incluse nell'esempio di codice che semplificano l'attività di gestione della connessione del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="32944-117">Helper libraries are included in the code sample that simplify the task of handling the device connection.</span></span>

<span data-ttu-id="32944-118">Una tipica connessione remota avrà una bassa di 50 ms di latenza.</span><span class="sxs-lookup"><span data-stu-id="32944-118">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="32944-119">L'App Player può segnalare la latenza in tempo reale.</span><span class="sxs-lookup"><span data-stu-id="32944-119">The player app can report the latency in real-time.</span></span>

>[!NOTE]
><span data-ttu-id="32944-120">I frammenti di codice in questo articolo illustrano attualmente l' C++uso di/CX, invece di/WinRT conformi C++a C + 17 come usato nel modello di [ C++ progetto olografico](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="32944-120">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="32944-121">I concetti sono equivalenti per C++un progetto/WinRT, anche se sarà necessario tradurre il codice.</span><span class="sxs-lookup"><span data-stu-id="32944-121">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

### <a name="get-the-remoting-nuget-packages"></a><span data-ttu-id="32944-122">Ottenere i pacchetti NuGet per la comunicazione remota</span><span class="sxs-lookup"><span data-stu-id="32944-122">Get the remoting NuGet packages</span></span>

<span data-ttu-id="32944-123">Seguire questa procedura per ottenere il pacchetto NuGet per la comunicazione remota olografica e aggiungere un riferimento dal progetto:</span><span class="sxs-lookup"><span data-stu-id="32944-123">Follow these steps to get the NuGet package for holographic remoting, and add a reference from your project:</span></span>
1. <span data-ttu-id="32944-124">Passare al progetto in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="32944-124">Go to your project in Visual Studio.</span></span>
2. <span data-ttu-id="32944-125">Fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Gestisci pacchetti NuGet...**</span><span class="sxs-lookup"><span data-stu-id="32944-125">Right-click on the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="32944-126">Nel pannello visualizzato fare clic su **Sfoglia** e quindi cercare "comunicazione remota olografica".</span><span class="sxs-lookup"><span data-stu-id="32944-126">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="32944-127">Selezionare **Microsoft. olografic. Remoting** e fare clic su **Installa**.</span><span class="sxs-lookup"><span data-stu-id="32944-127">Select **Microsoft.Holographic.Remoting** and click **Install**.</span></span>
5. <span data-ttu-id="32944-128">Se viene visualizzata la finestra di dialogo **Anteprima** , fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="32944-128">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="32944-129">La finestra di dialogo successiva visualizzata è il contratto di licenza.</span><span class="sxs-lookup"><span data-stu-id="32944-129">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="32944-130">Fare clic su **Accetto** per accettare il contratto di licenza.</span><span class="sxs-lookup"><span data-stu-id="32944-130">Click on **I Accept** to accept the license agreement.</span></span>

### <a name="create-the-holographicstreamerhelpers"></a><span data-ttu-id="32944-131">Creare il HolographicStreamerHelpers</span><span class="sxs-lookup"><span data-stu-id="32944-131">Create the HolographicStreamerHelpers</span></span>

<span data-ttu-id="32944-132">In primo luogo, è necessaria un'istanza di HolographicStreamerHelpers.</span><span class="sxs-lookup"><span data-stu-id="32944-132">First, we need an instance of HolographicStreamerHelpers.</span></span> <span data-ttu-id="32944-133">Aggiungere questo oggetto alla classe che gestirà la comunicazione remota.</span><span class="sxs-lookup"><span data-stu-id="32944-133">Add this to the class that will be handling remoting.</span></span>

```
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

<span data-ttu-id="32944-134">Sarà inoltre necessario tenere traccia dello stato della connessione.</span><span class="sxs-lookup"><span data-stu-id="32944-134">You'll also need to track connection state.</span></span> <span data-ttu-id="32944-135">Se si desidera eseguire il rendering dell'anteprima, è necessario disporre di una trama in cui copiarla.</span><span class="sxs-lookup"><span data-stu-id="32944-135">If you want to render the preview, you need to have a texture to copy it to.</span></span> <span data-ttu-id="32944-136">Sono necessari anche alcuni elementi, ad esempio un blocco dello stato della connessione, un modo per archiviare l'indirizzo IP di HoloLens e così via.</span><span class="sxs-lookup"><span data-stu-id="32944-136">You also need a few things like a connection state lock, some way of storing the IP address of HoloLens, and so on.</span></span>

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

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a><span data-ttu-id="32944-137">Inizializzare HolographicStreamerHelpers e connettersi a HoloLens</span><span class="sxs-lookup"><span data-stu-id="32944-137">Initialize HolographicStreamerHelpers and connect to HoloLens</span></span>

<span data-ttu-id="32944-138">Per connettersi a un dispositivo HoloLens, creare un'istanza di HolographicStreamerHelpers e connettersi all'indirizzo IP di destinazione.</span><span class="sxs-lookup"><span data-stu-id="32944-138">To connect to a HoloLens device, create an instance of HolographicStreamerHelpers and connect to the target IP address.</span></span> <span data-ttu-id="32944-139">È necessario impostare la dimensione del fotogramma video in modo che corrisponda alla larghezza e all'altezza di visualizzazione HoloLens, perché la libreria remota olografica prevede che le risoluzioni del codificatore e del decodificatore corrispondano esattamente.</span><span class="sxs-lookup"><span data-stu-id="32944-139">You will need to set the video frame size to match the HoloLens display width and height, because the Holographic Remoting library expects the encoder and decoder resolutions to match exactly.</span></span>

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

<span data-ttu-id="32944-140">La connessione del dispositivo è asincrona.</span><span class="sxs-lookup"><span data-stu-id="32944-140">The device connection is asynchronous.</span></span> <span data-ttu-id="32944-141">L'app deve fornire gestori eventi per gli eventi di connessione, disconnessione e invio frame.</span><span class="sxs-lookup"><span data-stu-id="32944-141">Your app needs to provide event handlers for connect, disconnect, and frame send events.</span></span>

<span data-ttu-id="32944-142">L'evento OnConnected può aggiornare l'interfaccia utente, avviare il rendering e così via.</span><span class="sxs-lookup"><span data-stu-id="32944-142">The OnConnected event can update the UI, start rendering, and so on.</span></span> <span data-ttu-id="32944-143">Nell'esempio di codice desktop, viene aggiornato il titolo della finestra con un messaggio "Connected".</span><span class="sxs-lookup"><span data-stu-id="32944-143">In our desktop code sample, we update the window title with a "connected" message.</span></span>

```
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

<span data-ttu-id="32944-144">L'evento disconnected può gestire la riconnessione, gli aggiornamenti dell'interfaccia utente e così via.</span><span class="sxs-lookup"><span data-stu-id="32944-144">The OnDisconnected event can handle reconnection, UI updates, and so on.</span></span> <span data-ttu-id="32944-145">In questo esempio viene riconnessa se si verifica un errore temporaneo.</span><span class="sxs-lookup"><span data-stu-id="32944-145">In this example, we reconnect if there is a transient failure.</span></span>

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

<span data-ttu-id="32944-146">Quando il componente remoto è pronto per l'invio di un frame, l'app ha la possibilità di crearne una copia nella SendFrameEvent.</span><span class="sxs-lookup"><span data-stu-id="32944-146">When the remoting component is ready to send a frame, your app is provided an opportunity to make a copy of it in the SendFrameEvent.</span></span> <span data-ttu-id="32944-147">Qui viene copiato il frame in una catena di scambio in modo che sia possibile visualizzarlo in una finestra di anteprima.</span><span class="sxs-lookup"><span data-stu-id="32944-147">Here, we copy the frame to a swap chain so that we can display it in a preview window.</span></span>

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

### <a name="render-holographic-content"></a><span data-ttu-id="32944-148">Rendering del contenuto olografico</span><span class="sxs-lookup"><span data-stu-id="32944-148">Render holographic content</span></span>

<span data-ttu-id="32944-149">Per eseguire il rendering del contenuto usando la comunicazione remota, è necessario configurare un IFrameworkView virtuale all'interno dell'app desktop o UWP ed elaborare i frame olografici dalla comunicazione remota.</span><span class="sxs-lookup"><span data-stu-id="32944-149">To render content using remoting, you set up a virtual IFrameworkView within your desktop or UWP app and process holographic frames from remoting.</span></span> <span data-ttu-id="32944-150">Tutte le API olografiche di Windows vengono utilizzate allo stesso modo da questa visualizzazione, ma sono impostate in modo leggermente diverso.</span><span class="sxs-lookup"><span data-stu-id="32944-150">All of the Windows Holographic APIs are uses the same way by this view, but it is set up slightly differently.</span></span>

<span data-ttu-id="32944-151">Invece di crearli autonomamente, i componenti di spazio olografico e vocale provengono dalla classe HolographicRemotingHelpers:</span><span class="sxs-lookup"><span data-stu-id="32944-151">Instead of creating them yourself, the holographic space and speech components come from your HolographicRemotingHelpers class:</span></span>

```
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

<span data-ttu-id="32944-152">Anziché usare un ciclo di aggiornamento all'interno di un metodo Run, è necessario fornire gli aggiornamenti del ciclo principale dell'app desktop o UWP.</span><span class="sxs-lookup"><span data-stu-id="32944-152">Instead of using an update loop inside of a Run method, you provide tick updates from the main loop of your desktop or UWP app.</span></span> <span data-ttu-id="32944-153">Ciò consente all'app desktop o UWP di rimanere in controllo dell'elaborazione dei messaggi.</span><span class="sxs-lookup"><span data-stu-id="32944-153">This allows your desktop or UWP app to remain in control of message processing.</span></span>

```
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

<span data-ttu-id="32944-154">Il metodo di sequenza () del segno di visualizzazione dell'app olografica completa un'iterazione del ciclo di aggiornamento, di estrazione e di presentazione.</span><span class="sxs-lookup"><span data-stu-id="32944-154">The holographic app view's Tick() method completes one iteration of the update, draw, present loop.</span></span>

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

<span data-ttu-id="32944-155">Il ciclo di aggiornamento, rendering e presenza dell'app olografica è identico a quello che si verifica quando è in esecuzione in HoloLens, ad eccezione del fatto che è possibile accedere a una quantità molto maggiore di risorse di sistema nel PC desktop.</span><span class="sxs-lookup"><span data-stu-id="32944-155">The holographic app view update, render, and present loop is exactly the same as it is when running on HoloLens - except that you have access to a much greater amount of system resources on your desktop PC.</span></span> <span data-ttu-id="32944-156">È possibile eseguire il rendering di molti più triangoli, avere più passaggi di disegno, eseguire più fisica e usare processi x64 per caricare contenuti che richiedono più di 2 GB di RAM.</span><span class="sxs-lookup"><span data-stu-id="32944-156">You can render many more triangles, have more drawing passes, do more physics, and use x64 processes to load content that requires more than 2 GB of RAM.</span></span>

### <a name="disconnect-and-end-the-remote-session"></a><span data-ttu-id="32944-157">Disconnetti e termina la sessione remota</span><span class="sxs-lookup"><span data-stu-id="32944-157">Disconnect and end the remote session</span></span>

<span data-ttu-id="32944-158">Per disconnettersi, ad esempio, quando l'utente fa clic su un pulsante dell'interfaccia utente per disconnettere-chiamare Disconnect () in HolographicStreamerHelpers e quindi rilasciare l'oggetto.</span><span class="sxs-lookup"><span data-stu-id="32944-158">To disconnect - for example, when the user clicks a UI button to disconnect - call Disconnect() on the HolographicStreamerHelpers, and then release the object.</span></span>

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

## <a name="get-the-remoting-player"></a><span data-ttu-id="32944-159">Ottenere il lettore di comunicazione remota</span><span class="sxs-lookup"><span data-stu-id="32944-159">Get the remoting player</span></span>

<span data-ttu-id="32944-160">Il lettore di comunicazione remota olografica di Windows è disponibile nell'App Store di Windows come endpoint per le applicazioni host Remote a cui connettersi.</span><span class="sxs-lookup"><span data-stu-id="32944-160">The Windows Holographic remoting player is offered in the Windows app store as an endpoint for remoting host apps to connect to.</span></span> <span data-ttu-id="32944-161">Per ottenere il lettore di comunicazione remota olografica Windows, visitare l'App Store di Windows dalla HoloLens, cercare i servizi remoti e scaricare l'app.</span><span class="sxs-lookup"><span data-stu-id="32944-161">To get the Windows Holographic remoting player, visit the Windows app store from your HoloLens, search for Remoting, and download the app.</span></span> <span data-ttu-id="32944-162">Il lettore .NET Remoting include una funzionalità per la visualizzazione delle statistiche sullo schermo, che può essere utile quando si esegue il debug di applicazioni host Remote.</span><span class="sxs-lookup"><span data-stu-id="32944-162">The remoting player includes a feature to display statistics on-screen, which can be useful when debugging remoting host apps.</span></span>

## <a name="notes-and-resources"></a><span data-ttu-id="32944-163">Note e risorse</span><span class="sxs-lookup"><span data-stu-id="32944-163">Notes and resources</span></span>

<span data-ttu-id="32944-164">La visualizzazione dell'app olografica richiede un modo per fornire all'app il dispositivo Direct3D, che deve essere usato per inizializzare lo spazio olografico.</span><span class="sxs-lookup"><span data-stu-id="32944-164">The holographic app view will need a way to provide your app with the Direct3D device, which must be used to initialize the holographic space.</span></span> <span data-ttu-id="32944-165">L'app deve usare questo dispositivo Direct3D per copiare e visualizzare il frame di anteprima.</span><span class="sxs-lookup"><span data-stu-id="32944-165">Your app should use this Direct3D device to copy and display the preview frame.</span></span>

```
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

<span data-ttu-id="32944-166">**Esempio di codice:** È disponibile un esempio di codice .NET Remoting completo, che include una visualizzazione di applicazioni olografica compatibile con i progetti host .NET Remoting e Remoting per desktop Win32, UWP DirectX e UWP con XAML.</span><span class="sxs-lookup"><span data-stu-id="32944-166">**Code sample:** A complete Holographic Remoting code sample is available, which includes a holographic application view that is compatible with remoting and remoting host projects for desktop Win32, UWP DirectX, and UWP with XAML.</span></span> <span data-ttu-id="32944-167">Per ottenerlo, fare clic qui:</span><span class="sxs-lookup"><span data-stu-id="32944-167">To get it, go here:</span></span>
* [<span data-ttu-id="32944-168">Esempio di codice Windows olografico per servizi remoti</span><span class="sxs-lookup"><span data-stu-id="32944-168">Windows Holographic Code Sample for Remoting</span></span>](https://github.com/Microsoft/HoloLensCompanionKit/)

<span data-ttu-id="32944-169">**Nota di debug:** La libreria remota olografica può generare eccezioni first-chance.</span><span class="sxs-lookup"><span data-stu-id="32944-169">**Debugging note:** The Holographic Remoting library can throw first-chance exceptions.</span></span> <span data-ttu-id="32944-170">Queste eccezioni possono essere visibili nelle sessioni di debug, a seconda delle impostazioni delle eccezioni di Visual Studio attive al momento.</span><span class="sxs-lookup"><span data-stu-id="32944-170">These exceptions may be visible in debugging sessions, depending on the Visual Studio exception settings that are active at the time.</span></span> <span data-ttu-id="32944-171">Queste eccezioni vengono rilevate internamente dalla libreria di comunicazione remota olografica e possono essere ignorate.</span><span class="sxs-lookup"><span data-stu-id="32944-171">These exceptions are caught internally by the Holographic Remoting library and can be ignored.</span></span>

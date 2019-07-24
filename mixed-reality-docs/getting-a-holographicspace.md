---
title: Recupero di un HolographicSpace
description: Viene illustrata l'API HolographicSpace, un concetto di base per il rendering olografico e l'input spaziale.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, HolographicSpace, CoreWindow, input spaziale, rendering, catena di scambio, frame olografico, ciclo di aggiornamento, ciclo di gioco, frame di riferimento, locatability, codice di esempio, procedura dettagliata
ms.openlocfilehash: 828352203b20ec38275796b3f172e7ecc5df3f00
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63525442"
---
# <a name="getting-a-holographicspace"></a><span data-ttu-id="ae3ee-104">Recupero di un HolographicSpace</span><span class="sxs-lookup"><span data-stu-id="ae3ee-104">Getting a HolographicSpace</span></span>

<span data-ttu-id="ae3ee-105">La classe <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> è il portale nel mondo olografico.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-105">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> class is your portal into the holographic world.</span></span> <span data-ttu-id="ae3ee-106">Controlla il rendering immersivo, fornisce i dati della fotocamera e fornisce l'accesso alle API di ragionamento spaziale.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-106">It controls immersive rendering, provides camera data, and provides access to spatial reasoning APIs.</span></span> <span data-ttu-id="ae3ee-107">Ne viene creato uno per il <a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a> dell'app UWP o l'HWND dell'app Win32.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-107">You will create one for your UWP app's <a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a> or your Win32 app's HWND.</span></span>

## <a name="set-up-the-holographic-space"></a><span data-ttu-id="ae3ee-108">Configurare lo spazio olografico</span><span class="sxs-lookup"><span data-stu-id="ae3ee-108">Set up the holographic space</span></span>

<span data-ttu-id="ae3ee-109">La creazione dell'oggetto spazio olografico è il primo passaggio per creare un'app per la realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-109">Creating the holographic space object is the first step in making your Windows Mixed Reality app.</span></span> <span data-ttu-id="ae3ee-110">Le applicazioni Windows tradizionali eseguono il rendering di una catena di scambio Direct3D creata per la finestra principale della visualizzazione dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-110">Traditional Windows apps render to a Direct3D swap chain created for the core window of their application view.</span></span> <span data-ttu-id="ae3ee-111">Questa catena di scambio viene visualizzata in uno Slate nell'interfaccia utente olografica.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-111">This swap chain is displayed to a slate in the holographic UI.</span></span> <span data-ttu-id="ae3ee-112">Per rendere olografica la visualizzazione dell'applicazione anziché una lavagna 2D, creare uno spazio olografico per la finestra principale anziché una catena di scambio.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-112">To make your application view holographic rather than a 2D slate, create a holographic space for its core window instead of a swap chain.</span></span> <span data-ttu-id="ae3ee-113">La presentazione di frame olografici creati da questo spazio olografico consente di inserire l'app in modalità di rendering a schermo intero.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-113">Presenting holographic frames that are created by this holographic space puts your app into full-screen rendering mode.</span></span>

<span data-ttu-id="ae3ee-114">Per un' **app UWP** [a partire dal *modello di app DirectX 11 (Windows universale) olografico*](creating-a-holographic-directx-project.md), cercare questo codice nel  metodo sewindow in AppView. cpp:</span><span class="sxs-lookup"><span data-stu-id="ae3ee-114">For a **UWP app** [starting from the *Holographic DirectX 11 App (Universal Windows) template*](creating-a-holographic-directx-project.md), look for this code in the **SetWindow** method in AppView.cpp:</span></span>

```cpp
m_holographicSpace = HolographicSpace::CreateForCoreWindow(window);
```

<span data-ttu-id="ae3ee-115">Per un' **app Win32** [a partire dall'esempio Win32 *BasicHologram* ](creating-a-holographic-directx-project.md#creating-a-win32-project), vedere **app:: CreateWindowAndHolographicSpace** per un esempio di come creare un HWND e quindi convertirlo in un HWND immersivo creando un oggetto associato <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank"> HolographicSpace</a>:</span><span class="sxs-lookup"><span data-stu-id="ae3ee-115">For a **Win32 app** [starting from the *BasicHologram* Win32 sample](creating-a-holographic-directx-project.md#creating-a-win32-project), look at **App::CreateWindowAndHolographicSpace** for an example of how to create an HWND and then convert it into an immersive HWND by creating an associated <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>:</span></span>
```cpp
void App::CreateWindowAndHolographicSpace(HINSTANCE hInstance, int nCmdShow)
{
    // Store the instance handle in our class variable.
    m_hInst = hInstance;

    // Create the window for the HolographicSpace.
    hWnd = CreateWindowW(
        m_szWindowClass, 
        m_szTitle,
        WS_VISIBLE,
        CW_USEDEFAULT, 
        0, 
        CW_USEDEFAULT, 
        0, 
        nullptr, 
        nullptr, 
        hInstance, 
        nullptr);

    if (!hWnd)
    {
        winrt::check_hresult(E_FAIL);
    }

    {
        // Use WinRT factory to create the holographic space.
        using namespace winrt::Windows::Graphics::Holographic;
        winrt::com_ptr<IHolographicSpaceInterop> holographicSpaceInterop =
            winrt::get_activation_factory<HolographicSpace, IHolographicSpaceInterop>();
        winrt::com_ptr<ABI::Windows::Graphics::Holographic::IHolographicSpace> spHolographicSpace;
        winrt::check_hresult(holographicSpaceInterop->CreateForWindow(
            hWnd, __uuidof(ABI::Windows::Graphics::Holographic::IHolographicSpace),
            winrt::put_abi(spHolographicSpace)));

        if (!spHolographicSpace)
        {
            winrt::check_hresult(E_FAIL);
        }

        // Store the holographic space.
        m_holographicSpace = spHolographicSpace.as<HolographicSpace>();
    }

    // The DeviceResources class uses the preferred DXGI adapter ID from the holographic
    // space (when available) to create a Direct3D device. The HolographicSpace
    // uses this ID3D11Device to create and manage device-based resources such as
    // swap chains.
    m_deviceResources->SetHolographicSpace(m_holographicSpace);

    // The main class uses the holographic space for updates and rendering.
    m_main->SetHolographicSpace(hWnd, m_holographicSpace);

    // Show the window. This will activate the holographic view and switch focus
    // to the app in Windows Mixed Reality.
    ShowWindow(hWnd, nCmdShow);
    UpdateWindow(hWnd);
}
```

<span data-ttu-id="ae3ee-116">Ora che è stato ottenuto un HolographicSpace per UWP CoreWindow o l'HWND Win32, è possibile usare tale HolographicSpace per gestire le fotocamere olografiche, creare sistemi di coordinate ed eseguire il rendering olografico.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-116">Now that you've obtained a HolographicSpace for either your UWP CoreWindow or Win32 HWND, you'll use that HolographicSpace to handle holographic cameras, create coordinate systems and do holographic rendering.</span></span> <span data-ttu-id="ae3ee-117">Lo spazio olografico corrente viene usato in più posizioni nel modello DirectX:</span><span class="sxs-lookup"><span data-stu-id="ae3ee-117">The current holographic space is used in multiple places in the DirectX template:</span></span>
* <span data-ttu-id="ae3ee-118">La classe **DeviceResources** deve ottenere alcune informazioni dall'oggetto HolographicSpace per creare il dispositivo Direct3D.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-118">The **DeviceResources** class needs to get some information from the HolographicSpace object in order to create the Direct3D device.</span></span> <span data-ttu-id="ae3ee-119">ID adattatore DXGI associato alla visualizzazione olografica.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-119">This is the DXGI adapter ID associated with the holographic display.</span></span> <span data-ttu-id="ae3ee-120">La classe <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> usa il dispositivo Direct3D 11 dell'app per creare e gestire risorse basate su dispositivo, ad esempio i buffer indietro per ogni fotocamera olografica.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-120">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> class uses your app's Direct3D 11 device to create and manage device-based resources, such as the back buffers for each holographic camera.</span></span> <span data-ttu-id="ae3ee-121">Se si è interessati a vedere il funzionamento di questa funzione sotto la cappa, è possibile trovarla in DeviceResources. cpp.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-121">If you're interested in seeing what this function does under the hood, you'll find it in DeviceResources.cpp.</span></span>
* <span data-ttu-id="ae3ee-122">La funzione **DeviceResources:: InitializeUsingHolographicSpace** illustra come ottenere l'adapter cercando LUID e come scegliere una scheda predefinita se non è specificata alcuna scheda preferita.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-122">The function **DeviceResources::InitializeUsingHolographicSpace** demonstrates how to obtain the adapter by looking up the LUID – and how to choose a default adapter when no preferred adapter is specified.</span></span>
* <span data-ttu-id="ae3ee-123">La classe principale dell'app usa lo spazio olografico di **AppView:: sewindow** o **app:: CreateWindowAndHolographicSpace** per gli aggiornamenti e il rendering.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-123">The app's main class uses the holographic space from **AppView::SetWindow** or **App::CreateWindowAndHolographicSpace** for updates and rendering.</span></span>

>[!NOTE]
><span data-ttu-id="ae3ee-124">Mentre le sezioni seguenti menzionano i nomi di funzione del modello come **AppView:: sefinestra** che presuppone che sia stato avviato dal modello di app UWP olografico, i frammenti di codice visualizzati verranno applicati equamente nelle app UWP e Win32.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-124">While the sections below mention function names from the template like **AppView::SetWindow** that assume that you started from the holographic UWP app template, the code snippets you see will apply equally across UWP and Win32 apps.</span></span>

<span data-ttu-id="ae3ee-125">Successivamente, verrà analizzato il processo di installazione di cui **SetHolographicSpace** è responsabile nella classe AppMain.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-125">Next, we'll dive into the setup process that **SetHolographicSpace** is responsible for in the AppMain class.</span></span>

## <a name="subscribe-to-camera-events-create-and-remove-camera-resources"></a><span data-ttu-id="ae3ee-126">Sottoscrivere gli eventi della fotocamera, creare e rimuovere le risorse della fotocamera</span><span class="sxs-lookup"><span data-stu-id="ae3ee-126">Subscribe to camera events, create and remove camera resources</span></span>

<span data-ttu-id="ae3ee-127">Il contenuto olografico dell'app si trova nello spazio olografico e viene visualizzato tramite una o più fotocamere olografiche che rappresentano prospettive diverse sulla scena.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-127">Your app's holographic content lives in its holographic space, and is viewed through one or more holographic cameras which represent different perspectives on the scene.</span></span> <span data-ttu-id="ae3ee-128">Ora che si dispone dello spazio olografico, è possibile ricevere i dati per le fotocamere olografiche.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-128">Now that you have the holographic space, you can receive data for holographic cameras.</span></span>

<span data-ttu-id="ae3ee-129">L'app deve rispondere agli eventi **CameraAdded** creando le risorse specifiche della fotocamera, ad esempio la visualizzazione della destinazione di rendering del buffer nascosto.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-129">Your app needs to respond to **CameraAdded** events by creating any resources that are specific to that camera, like your back buffer render target view.</span></span> <span data-ttu-id="ae3ee-130">È possibile visualizzare questo codice nella funzione **DeviceResources:: SetHolographicSpace** , chiamato da **AppView:: sefinestra** prima che l'app crei qualsiasi frame olografico:</span><span class="sxs-lookup"><span data-stu-id="ae3ee-130">You can see this code in the **DeviceResources::SetHolographicSpace** function, called by **AppView::SetWindow** before the app creates any holographic frames:</span></span>

```cpp
m_cameraAddedToken = m_holographicSpace.CameraAdded(
    std::bind(&AppMain::OnCameraAdded, this, _1, _2));
```

<span data-ttu-id="ae3ee-131">L'app deve anche rispondere agli eventi **CameraRemoved** rilasciando le risorse create per la fotocamera.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-131">Your app also needs to respond to **CameraRemoved** events by releasing resources that were created for that camera.</span></span>

<span data-ttu-id="ae3ee-132">Da **DeviceResources:: SetHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="ae3ee-132">From **DeviceResources::SetHolographicSpace**:</span></span>

```cpp
m_cameraRemovedToken = m_holographicSpace.CameraRemoved(
    std::bind(&AppMain::OnCameraRemoved, this, _1, _2));
```

<span data-ttu-id="ae3ee-133">I gestori di eventi devono completare alcune operazioni per garantire che il rendering olografico scorra senza problemi e che l'app sia in grado di eseguire il rendering.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-133">The event handlers must complete some work in order to keep holographic rendering flowing smoothly, and so that your app is able to render at all.</span></span> <span data-ttu-id="ae3ee-134">Leggere il codice e i commenti per i dettagli: è possibile cercare **OnCameraAdded** e **OnCameraRemoved** nella classe principale per comprendere in che modo la mappa **m_cameraResources** viene gestita da **DeviceResources**.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-134">Read the code and comments for the details: you can look for **OnCameraAdded** and **OnCameraRemoved** in your main class to understand how the **m_cameraResources** map is handled by **DeviceResources**.</span></span>

<span data-ttu-id="ae3ee-135">A questo punto, ci siamo concentrati su AppMain e sulla configurazione che consente all'app di sapere sulle fotocamere olografiche.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-135">Right now, we're focused on AppMain and the setup that it does to enable your app to know about holographic cameras.</span></span> <span data-ttu-id="ae3ee-136">Tenendo presente questo aspetto, è importante prendere in considerazione i due requisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="ae3ee-136">With this in mind, it's important to take note of the following two requirements:</span></span>

1. <span data-ttu-id="ae3ee-137">Per il gestore dell'evento **CameraAdded** , l'app può funzionare in modo asincrono per completare la creazione di risorse e il caricamento di asset per la nuova fotocamera olografica.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-137">For the **CameraAdded** event handler, the app can work asynchronously to finish creating resources and loading assets for the new holographic camera.</span></span> <span data-ttu-id="ae3ee-138">Le app che accettano più di un frame per completare questa operazione devono richiedere un rinvio e completare il rinvio dopo il caricamento asincrono. un' [attività PPL](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl) può essere utilizzata per eseguire operazioni asincrone.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-138">Apps that take more than one frame to complete this work should request a deferral, and complete the deferral after loading asynchronously; a [PPL task](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl) can be used to do asynchronous work.</span></span> <span data-ttu-id="ae3ee-139">L'app deve assicurarsi che sia pronta per il rendering della fotocamera immediatamente quando esce dal gestore eventi o quando completa il rinvio.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-139">Your app must ensure that it's ready to render to that camera right away when it exits the event handler, or when it completes the deferral.</span></span> <span data-ttu-id="ae3ee-140">Se si esce dal gestore eventi o si completa il rinvio, viene indicato al sistema che l'app è ora pronta a ricevere i frame olografici con la fotocamera inclusa.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-140">Exiting the event handler or completing the deferral tells the system that your app is now ready to receive holographic frames with that camera included.</span></span>

2. <span data-ttu-id="ae3ee-141">Quando l'app riceve un evento **CameraRemoved** , deve rilasciare tutti i riferimenti al buffer nascosto e chiudere immediatamente la funzione.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-141">When the app receives a **CameraRemoved** event, it must release all references to the back buffer and exit the function right away.</span></span> <span data-ttu-id="ae3ee-142">Sono incluse le visualizzazioni della destinazione di rendering e qualsiasi altra risorsa che può includere un riferimento a [IDXGIResource](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource).</span><span class="sxs-lookup"><span data-stu-id="ae3ee-142">This includes render target views, and any other resource that might hold a reference to the [IDXGIResource](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource).</span></span> <span data-ttu-id="ae3ee-143">L'app deve inoltre assicurarsi che il buffer nascosto non sia collegato come destinazione di rendering, come illustrato in **CameraResources:: ReleaseResourcesForBackBuffer**.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-143">The app must also ensure that the back buffer is not attached as a render target, as shown in **CameraResources::ReleaseResourcesForBackBuffer**.</span></span> <span data-ttu-id="ae3ee-144">Per velocizzare le operazioni, l'app può rilasciare il buffer nascosto e avviare un'attività per completare in modo asincrono qualsiasi altra operazione necessaria per arrestare la fotocamera.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-144">To help speed things along, your app can release the back buffer and then launch a task to asynchronously complete any other work that is necessary to tear down that camera.</span></span> <span data-ttu-id="ae3ee-145">Il modello di app olografico include un'attività PPL che è possibile usare a questo scopo.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-145">The holographic app template includes a PPL task that you can use for this purpose.</span></span>

>[!NOTE]
><span data-ttu-id="ae3ee-146">Per determinare quando viene visualizzata una fotocamera aggiunta o rimossa nel frame, usare le proprietà **HolographicFrame** [AddedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) e [RemovedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) .</span><span class="sxs-lookup"><span data-stu-id="ae3ee-146">If you want to determine when an added or removed camera shows up on the frame, use the **HolographicFrame** [AddedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) and [RemovedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) properties.</span></span>

## <a name="create-a-frame-of-reference-for-your-holographic-content"></a><span data-ttu-id="ae3ee-147">Creare un frame di riferimento per il contenuto olografico</span><span class="sxs-lookup"><span data-stu-id="ae3ee-147">Create a frame of reference for your holographic content</span></span>

<span data-ttu-id="ae3ee-148">Il contenuto dell'app deve essere posizionato in un [sistema di coordinate spaziali](coordinate-systems-in-directx.md) per poter essere sottoposto a rendering nella HolographicSpace.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-148">Your app's content must be positioned in a [spatial coordinate system](coordinate-systems-in-directx.md) to be rendered in the HolographicSpace.</span></span> <span data-ttu-id="ae3ee-149">Il sistema fornisce due frame primari di riferimento che è possibile usare per definire un sistema di coordinate per gli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-149">The system provides two primary frames of reference which you can use to establish a coordinate system for your holograms.</span></span>

<span data-ttu-id="ae3ee-150">Sono disponibili due tipi di frame di riferimento in Windows olografico: frame di riferimento collegati al dispositivo e frame di riferimento che rimangono fissi quando il dispositivo viene spostato nell'ambiente dell'utente.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-150">There are two kinds of reference frames in Windows Holographic: reference frames attached to the device, and reference frames that remain stationary as the device moves through the user's environment.</span></span> <span data-ttu-id="ae3ee-151">Per impostazione predefinita, il modello di applicazione olografica usa un frame di riferimento fisso. Questo è uno dei modi più semplici per eseguire il rendering degli ologrammi con blocco mondiale.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-151">The holographic app template uses a stationary reference frame by default; this is one of the simplest ways to render world-locked holograms.</span></span>

<span data-ttu-id="ae3ee-152">I frame di riferimento stazionari sono progettati per stabilizzare le posizioni vicino alla posizione corrente del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-152">Stationary reference frames are designed to stabilize positions near the device's current location.</span></span> <span data-ttu-id="ae3ee-153">Ciò significa che le coordinate aggiuntive del dispositivo sono consentite alla deviazione leggermente rispetto all'ambiente dell'utente, perché il dispositivo apprende altre informazioni sullo spazio.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-153">This means that coordinates further from the device are allowed to drift slightly with respect to the user's environment as the device learns more about the space around it.</span></span> <span data-ttu-id="ae3ee-154">Esistono due modi per creare un frame di riferimento stazionario: acquisire il sistema di coordinate dalla [fase spaziale](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)oppure usare il valore predefinito <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-154">There are two ways to create a stationary frame of reference: acquire the coordinate system from the [spatial stage](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), or use the default <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span></span> <span data-ttu-id="ae3ee-155">Se si sta creando un'app di realtà mista di Windows per auricolari immersivi, il punto di partenza consigliato è la [fase spaziale](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), che fornisce anche informazioni sulle funzionalità dell'auricolare immersivo utilizzato dal lettore.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-155">If you are creating a Windows Mixed Reality app for immersive headsets, the recommended starting point is the [spatial stage](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), which also provides information about the capabilities of the immersive headset worn by the player.</span></span> <span data-ttu-id="ae3ee-156">Qui viene illustrato come usare il valore predefinito <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-156">Here, we show how to use the default <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span></span>

<span data-ttu-id="ae3ee-157">Il localizzatore spaziale rappresenta il dispositivo di realtà mista di Windows e tiene traccia del movimento del dispositivo e fornisce sistemi di coordinate che possono essere riconosciuti in relazione alla relativa posizione.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-157">The spatial locator represents the Windows Mixed Reality device, and tracks the motion of the device and provides coordinate systems that can be understood relative to its location.</span></span>

<span data-ttu-id="ae3ee-158">Da **AppMain:: OnHolographicDisplayIsAvailableChanged**:</span><span class="sxs-lookup"><span data-stu-id="ae3ee-158">From **AppMain::OnHolographicDisplayIsAvailableChanged**:</span></span>

```cpp
spatialLocator = SpatialLocator::GetDefault();
```

<span data-ttu-id="ae3ee-159">Creare il frame di riferimento fisso una volta all'avvio dell'app.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-159">Create the stationary reference frame once when the app is launched.</span></span> <span data-ttu-id="ae3ee-160">Questo è analogo alla definizione di un sistema di coordinate globale, con l'origine posizionata in corrispondenza della posizione del dispositivo all'avvio dell'app.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-160">This is analogous to defining a world coordinate system, with the origin placed at the device's position when the app is launched.</span></span> <span data-ttu-id="ae3ee-161">Questo frame di riferimento non si sposta con il dispositivo.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-161">This reference frame doesn't move with the device.</span></span>

<span data-ttu-id="ae3ee-162">Da **AppMain:: SetHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="ae3ee-162">From **AppMain::SetHolographicSpace**:</span></span>

```cpp
m_stationaryReferenceFrame =
    m_spatialLocator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```

<span data-ttu-id="ae3ee-163">Tutti i frame di riferimento sono allineati a gravità, ovvero l'asse y punta "verso l'alto" rispetto all'ambiente dell'utente.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-163">All reference frames are gravity aligned, meaning that the y axis points "up" with respect to the user's environment.</span></span> <span data-ttu-id="ae3ee-164">Poiché Windows utilizza i sistemi di coordinate "di destra", la direzione dell'asse – z coincide con la direzione "Avanti" del dispositivo quando viene creato il frame di riferimento.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-164">Since Windows uses "right-handed" coordinate systems, the direction of the –z axis coincides with the "forward" direction the device is facing when the reference frame is created.</span></span>

>[!NOTE]
><span data-ttu-id="ae3ee-165">Quando l'app richiede un posizionamento preciso dei singoli ologrammi, usare un <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a> per ancorare il singolo ologramma a una posizione nel mondo reale.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-165">When your app requires precise placement of individual holograms, use a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a> to anchor the individual hologram to a position in the real world.</span></span> <span data-ttu-id="ae3ee-166">Ad esempio, usare un ancoraggio spaziale quando l'utente indica un punto di interesse speciale.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-166">For example, use a spatial anchor when the user indicates a point to be of special interest.</span></span> <span data-ttu-id="ae3ee-167">Le posizioni di ancoraggio non sono derivate, ma possono essere modificate.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-167">Anchor positions do not drift, but they can be adjusted.</span></span> <span data-ttu-id="ae3ee-168">Per impostazione predefinita, quando si modifica un ancoraggio, la posizione viene semplificata al posto dei diversi frame successivi dopo la correzione.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-168">By default, when an anchor is adjusted, it eases its position into place over the next several frames after the correction has occurred.</span></span> <span data-ttu-id="ae3ee-169">A seconda dell'applicazione, in questo caso si potrebbe voler gestire la regolazione in modo diverso, ad esempio rinviando l'ologramma al di fuori della visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-169">Depending on your application, when this occurs you may want to handle the adjustment in a different manner (e.g. by deferring it until the hologram is out of view).</span></span> <span data-ttu-id="ae3ee-170">La proprietà <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a> e gli eventi <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a> abilitano queste personalizzazioni.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-170">The <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a> property and <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a> events enable these customizations.</span></span>

## <a name="respond-to-locatability-changed-events"></a><span data-ttu-id="ae3ee-171">Risposta agli eventi locatability modificati</span><span class="sxs-lookup"><span data-stu-id="ae3ee-171">Respond to locatability changed events</span></span>

<span data-ttu-id="ae3ee-172">Il rendering di ologrammi con blocco universale richiede che il dispositivo sia in grado di trovarsi nel mondo.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-172">Rendering world-locked holograms requires the device to be able to locate itself in the world.</span></span> <span data-ttu-id="ae3ee-173">Questo potrebbe non essere sempre possibile a causa di condizioni ambientali e, in tal caso, l'utente può prevedere un'indicazione visiva dell'interruzione del rilevamento.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-173">This may not always be possible due to environmental conditions, and if so, the user may expect a visual indication of the tracking interruption.</span></span> <span data-ttu-id="ae3ee-174">È necessario eseguire il rendering di questa indicazione visiva usando i frame di riferimento collegati al dispositivo, anziché stazionari al mondo.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-174">This visual indication must be rendered using reference frames attached to the device, instead of stationary to the world.</span></span>

<span data-ttu-id="ae3ee-175">L'app può richiedere di ricevere una notifica in caso di interruzione del rilevamento per qualsiasi motivo.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-175">You app can request to be notified if tracking is interrupted for any reason.</span></span> <span data-ttu-id="ae3ee-176">Eseguire la registrazione per l'evento LocatabilityChanged per rilevare quando la capacità del dispositivo di individuarsi nel mondo cambia.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-176">Register for the LocatabilityChanged event to detect when the device's ability to locate itself in the world changes.</span></span> <span data-ttu-id="ae3ee-177">Da **AppMain:: SetHolographicSpace:**</span><span class="sxs-lookup"><span data-stu-id="ae3ee-177">From **AppMain::SetHolographicSpace:**</span></span>

```cpp
m_locatabilityChangedToken = m_spatialLocator.LocatabilityChanged(
    std::bind(&HolographicApp6Main::OnLocatabilityChanged, this, _1, _2));
```

<span data-ttu-id="ae3ee-178">Usare quindi questo evento per determinare quando gli ologrammi non possono essere resi stazionari al mondo.</span><span class="sxs-lookup"><span data-stu-id="ae3ee-178">Then use this event to determine when holograms cannot be rendered stationary to the world.</span></span>

## <a name="see-also"></a><span data-ttu-id="ae3ee-179">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ae3ee-179">See also</span></span>
* [<span data-ttu-id="ae3ee-180">Rendering in DirectX</span><span class="sxs-lookup"><span data-stu-id="ae3ee-180">Rendering in DirectX</span></span>](rendering-in-directx.md)
* [<span data-ttu-id="ae3ee-181">Sistemi di coordinate in DirectX</span><span class="sxs-lookup"><span data-stu-id="ae3ee-181">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)

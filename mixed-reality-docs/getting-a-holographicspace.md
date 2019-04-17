---
title: Ottenere un HolographicSpace
description: Illustra l'API HolographicSpace, un concetto fondamentale per il rendering holographic e input spaziale.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, HolographicSpace, CoreWindow, spaziale di input, il rendering, scambiare catena, holographic frame, ciclo di aggiornamento, ciclo del gioco, frame di riferimento, locatability, codice di esempio, questa procedura dettagliata
ms.openlocfilehash: 828352203b20ec38275796b3f172e7ecc5df3f00
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605080"
---
# <a name="getting-a-holographicspace"></a><span data-ttu-id="10179-104">Ottenere un HolographicSpace</span><span class="sxs-lookup"><span data-stu-id="10179-104">Getting a HolographicSpace</span></span>

<span data-ttu-id="10179-105">Il <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> classe è il portale in tutto il mondo holographic.</span><span class="sxs-lookup"><span data-stu-id="10179-105">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> class is your portal into the holographic world.</span></span> <span data-ttu-id="10179-106">Controlla il rendering coinvolgente, fornisce i dati della fotocamera e fornisce l'accesso a spaziali motivazione delle API.</span><span class="sxs-lookup"><span data-stu-id="10179-106">It controls immersive rendering, provides camera data, and provides access to spatial reasoning APIs.</span></span> <span data-ttu-id="10179-107">Si creerà una per dell'app piattaforma UWP <a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a> o HWND dell'app Win32.</span><span class="sxs-lookup"><span data-stu-id="10179-107">You will create one for your UWP app's <a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a> or your Win32 app's HWND.</span></span>

## <a name="set-up-the-holographic-space"></a><span data-ttu-id="10179-108">Configurare lo spazio holographic</span><span class="sxs-lookup"><span data-stu-id="10179-108">Set up the holographic space</span></span>

<span data-ttu-id="10179-109">Creazione dell'oggetto spazio holographic è il primo passaggio per rendere l'app di realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="10179-109">Creating the holographic space object is the first step in making your Windows Mixed Reality app.</span></span> <span data-ttu-id="10179-110">Le app di Windows tradizionali eseguire il rendering in una catena di scambio Direct3D creata per la finestra principale della loro visualizzazione dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="10179-110">Traditional Windows apps render to a Direct3D swap chain created for the core window of their application view.</span></span> <span data-ttu-id="10179-111">Questa catena di scambio viene visualizzata uno slate nell'interfaccia utente holographic.</span><span class="sxs-lookup"><span data-stu-id="10179-111">This swap chain is displayed to a slate in the holographic UI.</span></span> <span data-ttu-id="10179-112">Per semplificare la visualizzazione dell'applicazione holographic anziché uno slate 2D, creare uno spazio holographic per la finestra principale invece di una catena di scambio.</span><span class="sxs-lookup"><span data-stu-id="10179-112">To make your application view holographic rather than a 2D slate, create a holographic space for its core window instead of a swap chain.</span></span> <span data-ttu-id="10179-113">Presentazione frame holographic creati da questo spazio holographic inserisce l'app in modalità di rendering a schermo intero.</span><span class="sxs-lookup"><span data-stu-id="10179-113">Presenting holographic frames that are created by this holographic space puts your app into full-screen rendering mode.</span></span>

<span data-ttu-id="10179-114">Per un **app UWP** [a partire dal *modello Holographic DirectX 11 App (Windows universale)*](creating-a-holographic-directx-project.md), cercare il codice nel **SetWindow** metodo in AppView.cpp:</span><span class="sxs-lookup"><span data-stu-id="10179-114">For a **UWP app** [starting from the *Holographic DirectX 11 App (Universal Windows) template*](creating-a-holographic-directx-project.md), look for this code in the **SetWindow** method in AppView.cpp:</span></span>

```cpp
m_holographicSpace = HolographicSpace::CreateForCoreWindow(window);
```

<span data-ttu-id="10179-115">Per un **app Win32** [a partire dal *BasicHologram* esempio Win32](creating-a-holographic-directx-project.md#creating-a-win32-project), esaminare **App::CreateWindowAndHolographicSpace** per un esempio di come creare un oggetto HWND e quindi convertirlo in un oggetto HWND coinvolgente tramite la creazione di un oggetto associato <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>:</span><span class="sxs-lookup"><span data-stu-id="10179-115">For a **Win32 app** [starting from the *BasicHologram* Win32 sample](creating-a-holographic-directx-project.md#creating-a-win32-project), look at **App::CreateWindowAndHolographicSpace** for an example of how to create an HWND and then convert it into an immersive HWND by creating an associated <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>:</span></span>
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

<span data-ttu-id="10179-116">Ora che hai ottenuto un HolographicSpace per il UWP CoreWindow o l'handle Win32 HWND, si userà tale HolographicSpace per gestire holographic fotocamere, creare sistemi di coordinate ed eseguire il rendering holographic.</span><span class="sxs-lookup"><span data-stu-id="10179-116">Now that you've obtained a HolographicSpace for either your UWP CoreWindow or Win32 HWND, you'll use that HolographicSpace to handle holographic cameras, create coordinate systems and do holographic rendering.</span></span> <span data-ttu-id="10179-117">Lo spazio holographic corrente viene usato in più posizioni nel modello di DirectX:</span><span class="sxs-lookup"><span data-stu-id="10179-117">The current holographic space is used in multiple places in the DirectX template:</span></span>
* <span data-ttu-id="10179-118">Il **DeviceResources** classe deve ottenere alcune informazioni dall'oggetto HolographicSpace per creare il dispositivo Direct3D.</span><span class="sxs-lookup"><span data-stu-id="10179-118">The **DeviceResources** class needs to get some information from the HolographicSpace object in order to create the Direct3D device.</span></span> <span data-ttu-id="10179-119">Questo è l'ID della scheda DXGI associato alla visualizzazione olografica.</span><span class="sxs-lookup"><span data-stu-id="10179-119">This is the DXGI adapter ID associated with the holographic display.</span></span> <span data-ttu-id="10179-120">Il <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> classe Usa dispositivi dell'app Direct3D 11 per creare e gestire le risorse basate su dispositivo, ad esempio il buffer per ogni videocamera holographic.</span><span class="sxs-lookup"><span data-stu-id="10179-120">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> class uses your app's Direct3D 11 device to create and manage device-based resources, such as the back buffers for each holographic camera.</span></span> <span data-ttu-id="10179-121">Se si è interessati a visualizzare ciò che svolge questa funzione dietro le quinte, si potrà risultare in Deviceresources.</span><span class="sxs-lookup"><span data-stu-id="10179-121">If you're interested in seeing what this function does under the hood, you'll find it in DeviceResources.cpp.</span></span>
* <span data-ttu-id="10179-122">La funzione **DeviceResources::InitializeUsingHolographicSpace** viene illustrato come ottenere l'adapter Cerca l'identificatore univoco locale – e spiega come scegliere un adattatore predefinito quando non viene specificato alcun adattatore preferito.</span><span class="sxs-lookup"><span data-stu-id="10179-122">The function **DeviceResources::InitializeUsingHolographicSpace** demonstrates how to obtain the adapter by looking up the LUID – and how to choose a default adapter when no preferred adapter is specified.</span></span>
* <span data-ttu-id="10179-123">Classe principale dell'app Usa dello spazio da holographic **AppView::SetWindow** oppure **App::CreateWindowAndHolographicSpace** per gli aggiornamenti e per il rendering.</span><span class="sxs-lookup"><span data-stu-id="10179-123">The app's main class uses the holographic space from **AppView::SetWindow** or **App::CreateWindowAndHolographicSpace** for updates and rendering.</span></span>

>[!NOTE]
><span data-ttu-id="10179-124">Anche se le sezioni seguenti ricordare i nomi delle funzioni del modello come **AppView::SetWindow** che basate sul presupposto che è stata avviata dal modello di app UWP holographic, i frammenti di codice viene visualizzato verranno applicata in modo uniforme tra le app UWP e Win32.</span><span class="sxs-lookup"><span data-stu-id="10179-124">While the sections below mention function names from the template like **AppView::SetWindow** that assume that you started from the holographic UWP app template, the code snippets you see will apply equally across UWP and Win32 apps.</span></span>

<span data-ttu-id="10179-125">Successivamente, verrà esaminato il programma di installazione che elaborano **SetHolographicSpace** è responsabile della classe AppMain.</span><span class="sxs-lookup"><span data-stu-id="10179-125">Next, we'll dive into the setup process that **SetHolographicSpace** is responsible for in the AppMain class.</span></span>

## <a name="subscribe-to-camera-events-create-and-remove-camera-resources"></a><span data-ttu-id="10179-126">Sottoscrivere gli eventi della fotocamera, creare e rimuovere le risorse della fotocamera</span><span class="sxs-lookup"><span data-stu-id="10179-126">Subscribe to camera events, create and remove camera resources</span></span>

<span data-ttu-id="10179-127">Contenuto holographic dell'app si trova nel relativo spazio holographic e possono essere visualizzato tramite uno o più fotocamere holographic che rappresentano diverse prospettive nella scena.</span><span class="sxs-lookup"><span data-stu-id="10179-127">Your app's holographic content lives in its holographic space, and is viewed through one or more holographic cameras which represent different perspectives on the scene.</span></span> <span data-ttu-id="10179-128">Dopo aver creato lo spazio holographic, è possibile ricevere i dati relativi a fotocamere holographic.</span><span class="sxs-lookup"><span data-stu-id="10179-128">Now that you have the holographic space, you can receive data for holographic cameras.</span></span>

<span data-ttu-id="10179-129">L'app deve rispondere **CameraAdded** eventi mediante la creazione di tutte le risorse che sono specifici di tale fotocamera, indica come visualizzazione destinazione rendering del buffer nascosto.</span><span class="sxs-lookup"><span data-stu-id="10179-129">Your app needs to respond to **CameraAdded** events by creating any resources that are specific to that camera, like your back buffer render target view.</span></span> <span data-ttu-id="10179-130">È possibile visualizzare il codice nel **DeviceResources::SetHolographicSpace** funzione, denominata **AppView::SetWindow** prima che l'app crea qualsiasi frame holographic:</span><span class="sxs-lookup"><span data-stu-id="10179-130">You can see this code in the **DeviceResources::SetHolographicSpace** function, called by **AppView::SetWindow** before the app creates any holographic frames:</span></span>

```cpp
m_cameraAddedToken = m_holographicSpace.CameraAdded(
    std::bind(&AppMain::OnCameraAdded, this, _1, _2));
```

<span data-ttu-id="10179-131">L'app deve inoltre rispondere **CameraRemoved** eventi rilasciando le risorse che sono state create per tale fotocamera.</span><span class="sxs-lookup"><span data-stu-id="10179-131">Your app also needs to respond to **CameraRemoved** events by releasing resources that were created for that camera.</span></span>

<span data-ttu-id="10179-132">Dal **DeviceResources::SetHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="10179-132">From **DeviceResources::SetHolographicSpace**:</span></span>

```cpp
m_cameraRemovedToken = m_holographicSpace.CameraRemoved(
    std::bind(&AppMain::OnCameraRemoved, this, _1, _2));
```

<span data-ttu-id="10179-133">I gestori di eventi devono completare alcune operazioni per mantenere il rendering holographic trasmessi senza problemi, e in modo che l'app è in grado di eseguire il rendering affatto.</span><span class="sxs-lookup"><span data-stu-id="10179-133">The event handlers must complete some work in order to keep holographic rendering flowing smoothly, and so that your app is able to render at all.</span></span> <span data-ttu-id="10179-134">Leggere il codice e i commenti per i dettagli: è possibile cercare **OnCameraAdded** e **OnCameraRemoved** nella classe principale per comprendere come il **m_cameraResources** mappa è gestito da **DeviceResources**.</span><span class="sxs-lookup"><span data-stu-id="10179-134">Read the code and comments for the details: you can look for **OnCameraAdded** and **OnCameraRemoved** in your main class to understand how the **m_cameraResources** map is handled by **DeviceResources**.</span></span>

<span data-ttu-id="10179-135">Al momento, si impegna per AppMain e le impostazioni di cui avviene per abilitare l'app di sapere sulle videocamere holographic.</span><span class="sxs-lookup"><span data-stu-id="10179-135">Right now, we're focused on AppMain and the setup that it does to enable your app to know about holographic cameras.</span></span> <span data-ttu-id="10179-136">A tal fine, è importante tenere conto dei seguenti due requisiti:</span><span class="sxs-lookup"><span data-stu-id="10179-136">With this in mind, it's important to take note of the following two requirements:</span></span>

1. <span data-ttu-id="10179-137">Per il **CameraAdded** gestore eventi, l'app può funzionare in modo asincrono per completare la creazione di risorse e il caricamento di asset per la nuova fotocamera holographic.</span><span class="sxs-lookup"><span data-stu-id="10179-137">For the **CameraAdded** event handler, the app can work asynchronously to finish creating resources and loading assets for the new holographic camera.</span></span> <span data-ttu-id="10179-138">Le app che accettano più di un frame per completare questa operazione dovrebbero richiedere un rinvio e completare il rinvio dopo il caricamento in modo asincrono; una [attività PPL](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl) può essere utilizzato per svolgere il lavoro asincrono.</span><span class="sxs-lookup"><span data-stu-id="10179-138">Apps that take more than one frame to complete this work should request a deferral, and complete the deferral after loading asynchronously; a [PPL task](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl) can be used to do asynchronous work.</span></span> <span data-ttu-id="10179-139">L'app deve garantire che è pronto per eseguire il rendering a tale tipo di camera immediatamente quando si conclude il gestore dell'evento o quando viene completato il rinvio.</span><span class="sxs-lookup"><span data-stu-id="10179-139">Your app must ensure that it's ready to render to that camera right away when it exits the event handler, or when it completes the deferral.</span></span> <span data-ttu-id="10179-140">Uscita dal gestore eventi o di completare il rinvio indica al sistema che l'app è ora pronto per ricevere i frame holographic con tale fotocamera inclusa.</span><span class="sxs-lookup"><span data-stu-id="10179-140">Exiting the event handler or completing the deferral tells the system that your app is now ready to receive holographic frames with that camera included.</span></span>

2. <span data-ttu-id="10179-141">Quando l'app riceve un **CameraRemoved** evento, è necessario rilasciare tutti i riferimenti per il buffer nascosto e di uscita immediatamente e la funzione.</span><span class="sxs-lookup"><span data-stu-id="10179-141">When the app receives a **CameraRemoved** event, it must release all references to the back buffer and exit the function right away.</span></span> <span data-ttu-id="10179-142">Ciò include le viste di destinazione di rendering e qualsiasi altra risorsa che potrebbe contenere un riferimento al [IDXGIResource](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource).</span><span class="sxs-lookup"><span data-stu-id="10179-142">This includes render target views, and any other resource that might hold a reference to the [IDXGIResource](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource).</span></span> <span data-ttu-id="10179-143">L'applicazione deve inoltre garantire che il buffer nascosto non è collegato come destinazione di rendering, come illustrato nella **CameraResources::ReleaseResourcesForBackBuffer**.</span><span class="sxs-lookup"><span data-stu-id="10179-143">The app must also ensure that the back buffer is not attached as a render target, as shown in **CameraResources::ReleaseResourcesForBackBuffer**.</span></span> <span data-ttu-id="10179-144">Per velocizzare le operazioni lungo, l'app può rilasciare il buffer nascosto, quindi avviare un'attività per completare in modo asincrono tutte le altre operazioni che sono necessaria chiudere tale fotocamera.</span><span class="sxs-lookup"><span data-stu-id="10179-144">To help speed things along, your app can release the back buffer and then launch a task to asynchronously complete any other work that is necessary to tear down that camera.</span></span> <span data-ttu-id="10179-145">Il modello di app holographic include un'attività PPL che è possibile usare per questo scopo.</span><span class="sxs-lookup"><span data-stu-id="10179-145">The holographic app template includes a PPL task that you can use for this purpose.</span></span>

>[!NOTE]
><span data-ttu-id="10179-146">Se si desidera determinare quando una fotocamera aggiunta o rimossa viene visualizzata nel frame, usare il **HolographicFrame** [AddedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) e [RemovedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) proprietà.</span><span class="sxs-lookup"><span data-stu-id="10179-146">If you want to determine when an added or removed camera shows up on the frame, use the **HolographicFrame** [AddedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) and [RemovedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) properties.</span></span>

## <a name="create-a-frame-of-reference-for-your-holographic-content"></a><span data-ttu-id="10179-147">Creare un frame di riferimento per il contenuto holographic</span><span class="sxs-lookup"><span data-stu-id="10179-147">Create a frame of reference for your holographic content</span></span>

<span data-ttu-id="10179-148">Contenuto dell'app deve essere posizionato una [sistema di coordinate spaziale](coordinate-systems-in-directx.md) da sottoporre a rendering nel HolographicSpace.</span><span class="sxs-lookup"><span data-stu-id="10179-148">Your app's content must be positioned in a [spatial coordinate system](coordinate-systems-in-directx.md) to be rendered in the HolographicSpace.</span></span> <span data-ttu-id="10179-149">Il sistema fornisce due primari frame di riferimento che è possibile usare per stabilire un sistema di coordinate per la vntana.</span><span class="sxs-lookup"><span data-stu-id="10179-149">The system provides two primary frames of reference which you can use to establish a coordinate system for your holograms.</span></span>

<span data-ttu-id="10179-150">Esistono due tipi di frame di riferimento in Windows Holographic: fare riferimento a frame collegati al dispositivo e frame di riferimento che rimangano fermo mentre si sposta il dispositivo tramite l'ambiente dell'utente.</span><span class="sxs-lookup"><span data-stu-id="10179-150">There are two kinds of reference frames in Windows Holographic: reference frames attached to the device, and reference frames that remain stationary as the device moves through the user's environment.</span></span> <span data-ttu-id="10179-151">Il modello di app holographic Usa un frame di riferimento fisso per impostazione predefinita. Questo è uno dei modi più semplici per eseguire il rendering vntana bloccato al mondo.</span><span class="sxs-lookup"><span data-stu-id="10179-151">The holographic app template uses a stationary reference frame by default; this is one of the simplest ways to render world-locked holograms.</span></span>

<span data-ttu-id="10179-152">I frame di riferimento fisso sono progettati per stabilizzare le posizioni nella posizione corrente del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="10179-152">Stationary reference frames are designed to stabilize positions near the device's current location.</span></span> <span data-ttu-id="10179-153">Ciò significa che le coordinate del dispositivo sono autorizzate a deviano leggermente rispetto all'ambiente dell'utente come il dispositivo viene a conoscenza delle informazioni sullo spazio intorno a esso.</span><span class="sxs-lookup"><span data-stu-id="10179-153">This means that coordinates further from the device are allowed to drift slightly with respect to the user's environment as the device learns more about the space around it.</span></span> <span data-ttu-id="10179-154">Esistono due modi per creare un fotogramma di riferimento fisso: acquisire il sistema di coordinate dal [fase spaziali](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), oppure usare il valore predefinito <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span><span class="sxs-lookup"><span data-stu-id="10179-154">There are two ways to create a stationary frame of reference: acquire the coordinate system from the [spatial stage](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), or use the default <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span></span> <span data-ttu-id="10179-155">Se si sta creando un'app per realtà mista di Windows per le cuffie coinvolgente e concreto, il punto di partenza consigliato è il [fase spaziali](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), che offre anche informazioni sulle funzionalità del visore VR immersivi indossate dal personale dal lettore.</span><span class="sxs-lookup"><span data-stu-id="10179-155">If you are creating a Windows Mixed Reality app for immersive headsets, the recommended starting point is the [spatial stage](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), which also provides information about the capabilities of the immersive headset worn by the player.</span></span> <span data-ttu-id="10179-156">In questo caso, viene illustrato come usare il valore predefinito <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span><span class="sxs-lookup"><span data-stu-id="10179-156">Here, we show how to use the default <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span></span>

<span data-ttu-id="10179-157">L'indicatore di posizione spaziale rappresenta il dispositivo di realtà mista di Windows e rileva il movimento del dispositivo e fornisce i sistemi di coordinate che possono essere interpretati rispetto alla relativa posizione.</span><span class="sxs-lookup"><span data-stu-id="10179-157">The spatial locator represents the Windows Mixed Reality device, and tracks the motion of the device and provides coordinate systems that can be understood relative to its location.</span></span>

<span data-ttu-id="10179-158">Dal **AppMain::OnHolographicDisplayIsAvailableChanged**:</span><span class="sxs-lookup"><span data-stu-id="10179-158">From **AppMain::OnHolographicDisplayIsAvailableChanged**:</span></span>

```cpp
spatialLocator = SpatialLocator::GetDefault();
```

<span data-ttu-id="10179-159">Creare il frame di riferimento fisso a una sola volta quando l'app viene avviata.</span><span class="sxs-lookup"><span data-stu-id="10179-159">Create the stationary reference frame once when the app is launched.</span></span> <span data-ttu-id="10179-160">Questo comportamento è analogo alla definizione di un sistema di coordinate world, con l'origine inserita nella posizione del dispositivo quando l'app viene avviata.</span><span class="sxs-lookup"><span data-stu-id="10179-160">This is analogous to defining a world coordinate system, with the origin placed at the device's position when the app is launched.</span></span> <span data-ttu-id="10179-161">Il frame di riferimento non viene spostati con il dispositivo.</span><span class="sxs-lookup"><span data-stu-id="10179-161">This reference frame doesn't move with the device.</span></span>

<span data-ttu-id="10179-162">Dal **AppMain::SetHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="10179-162">From **AppMain::SetHolographicSpace**:</span></span>

```cpp
m_stationaryReferenceFrame =
    m_spatialLocator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```

<span data-ttu-id="10179-163">Tutti i frame di riferimento sono gravità allineate, il che significa che l'asse y punti "up" per quanto riguarda l'ambiente dell'utente.</span><span class="sxs-lookup"><span data-stu-id="10179-163">All reference frames are gravity aligned, meaning that the y axis points "up" with respect to the user's environment.</span></span> <span data-ttu-id="10179-164">Poiché Windows Usa sistemi di coordinate "destra", la direzione dell'asse z coincide con la direzione "forward" è rivolta verso il dispositivo quando viene creato il frame di riferimento.</span><span class="sxs-lookup"><span data-stu-id="10179-164">Since Windows uses "right-handed" coordinate systems, the direction of the –z axis coincides with the "forward" direction the device is facing when the reference frame is created.</span></span>

>[!NOTE]
><span data-ttu-id="10179-165">Quando l'app richiede il posizionamento preciso degli vntana singoli, usare una <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a> ancorare l'ologrammi singole in una posizione nel mondo reale.</span><span class="sxs-lookup"><span data-stu-id="10179-165">When your app requires precise placement of individual holograms, use a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a> to anchor the individual hologram to a position in the real world.</span></span> <span data-ttu-id="10179-166">Usare un punto di ancoraggio spaziale, ad esempio, quando l'utente indica che un punto di particolare interesse.</span><span class="sxs-lookup"><span data-stu-id="10179-166">For example, use a spatial anchor when the user indicates a point to be of special interest.</span></span> <span data-ttu-id="10179-167">Le posizioni di ancoraggio non dello sfasamento, ma può essere modificate.</span><span class="sxs-lookup"><span data-stu-id="10179-167">Anchor positions do not drift, but they can be adjusted.</span></span> <span data-ttu-id="10179-168">Per impostazione predefinita, quando un ancoraggio viene regolato, semplifica la relativa posizione nella posizione corretta dei frame successivi diversi dopo che si è verificata la correzione.</span><span class="sxs-lookup"><span data-stu-id="10179-168">By default, when an anchor is adjusted, it eases its position into place over the next several frames after the correction has occurred.</span></span> <span data-ttu-id="10179-169">A seconda dell'applicazione, in questo caso è possibile gestire la regolazione in modo diverso (ad esempio rinviarla fino a quando l'ologrammi sono all'esterno della visualizzazione).</span><span class="sxs-lookup"><span data-stu-id="10179-169">Depending on your application, when this occurs you may want to handle the adjustment in a different manner (e.g. by deferring it until the hologram is out of view).</span></span> <span data-ttu-id="10179-170">Il <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a> proprietà e <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a> queste personalizzazioni gli eventi.</span><span class="sxs-lookup"><span data-stu-id="10179-170">The <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a> property and <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a> events enable these customizations.</span></span>

## <a name="respond-to-locatability-changed-events"></a><span data-ttu-id="10179-171">Rispondere agli eventi locatability modificato</span><span class="sxs-lookup"><span data-stu-id="10179-171">Respond to locatability changed events</span></span>

<span data-ttu-id="10179-172">Per il rendering bloccato world vntana richiede che il dispositivo sia in grado di individuare se stessa nel mondo.</span><span class="sxs-lookup"><span data-stu-id="10179-172">Rendering world-locked holograms requires the device to be able to locate itself in the world.</span></span> <span data-ttu-id="10179-173">Ciò potrebbe non essere sempre possibile a causa di condizioni ambientali e in questo caso, l'utente può aspettarsi un'indicazione visiva dell'interruzione di rilevamento.</span><span class="sxs-lookup"><span data-stu-id="10179-173">This may not always be possible due to environmental conditions, and if so, the user may expect a visual indication of the tracking interruption.</span></span> <span data-ttu-id="10179-174">Questa indicazione visiva rendering deve essere eseguito utilizzando i fotogrammi di riferimento collegati al dispositivo, anziché in sosta al mondo.</span><span class="sxs-lookup"><span data-stu-id="10179-174">This visual indication must be rendered using reference frames attached to the device, instead of stationary to the world.</span></span>

<span data-ttu-id="10179-175">App può richiedere per ricevere una notifica se il rilevamento viene interrotta per qualsiasi motivo.</span><span class="sxs-lookup"><span data-stu-id="10179-175">You app can request to be notified if tracking is interrupted for any reason.</span></span> <span data-ttu-id="10179-176">Registrare per l'evento LocatabilityChanged rilevare quando la capacità della periferica stesso individuare le modifiche del mondo.</span><span class="sxs-lookup"><span data-stu-id="10179-176">Register for the LocatabilityChanged event to detect when the device's ability to locate itself in the world changes.</span></span> <span data-ttu-id="10179-177">Da **AppMain::SetHolographicSpace:**</span><span class="sxs-lookup"><span data-stu-id="10179-177">From **AppMain::SetHolographicSpace:**</span></span>

```cpp
m_locatabilityChangedToken = m_spatialLocator.LocatabilityChanged(
    std::bind(&HolographicApp6Main::OnLocatabilityChanged, this, _1, _2));
```

<span data-ttu-id="10179-178">Utilizzare questo evento per determinare quando vntana non può essere eseguito il rendering fermo per tutto il mondo.</span><span class="sxs-lookup"><span data-stu-id="10179-178">Then use this event to determine when holograms cannot be rendered stationary to the world.</span></span>

## <a name="see-also"></a><span data-ttu-id="10179-179">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="10179-179">See also</span></span>
* [<span data-ttu-id="10179-180">Per il rendering in DirectX</span><span class="sxs-lookup"><span data-stu-id="10179-180">Rendering in DirectX</span></span>](rendering-in-directx.md)
* [<span data-ttu-id="10179-181">Sistemi di coordinate in DirectX</span><span class="sxs-lookup"><span data-stu-id="10179-181">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)

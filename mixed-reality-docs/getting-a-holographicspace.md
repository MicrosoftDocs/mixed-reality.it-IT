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
# <a name="getting-a-holographicspace"></a>Ottenere un HolographicSpace

Il <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> classe è il portale in tutto il mondo holographic. Controlla il rendering coinvolgente, fornisce i dati della fotocamera e fornisce l'accesso a spaziali motivazione delle API. Si creerà una per dell'app piattaforma UWP <a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a> o HWND dell'app Win32.

## <a name="set-up-the-holographic-space"></a>Configurare lo spazio holographic

Creazione dell'oggetto spazio holographic è il primo passaggio per rendere l'app di realtà mista di Windows. Le app di Windows tradizionali eseguire il rendering in una catena di scambio Direct3D creata per la finestra principale della loro visualizzazione dell'applicazione. Questa catena di scambio viene visualizzata uno slate nell'interfaccia utente holographic. Per semplificare la visualizzazione dell'applicazione holographic anziché uno slate 2D, creare uno spazio holographic per la finestra principale invece di una catena di scambio. Presentazione frame holographic creati da questo spazio holographic inserisce l'app in modalità di rendering a schermo intero.

Per un **app UWP** [a partire dal *modello Holographic DirectX 11 App (Windows universale)*](creating-a-holographic-directx-project.md), cercare il codice nel **SetWindow** metodo in AppView.cpp:

```cpp
m_holographicSpace = HolographicSpace::CreateForCoreWindow(window);
```

Per un **app Win32** [a partire dal *BasicHologram* esempio Win32](creating-a-holographic-directx-project.md#creating-a-win32-project), esaminare **App::CreateWindowAndHolographicSpace** per un esempio di come creare un oggetto HWND e quindi convertirlo in un oggetto HWND coinvolgente tramite la creazione di un oggetto associato <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>:
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

Ora che hai ottenuto un HolographicSpace per il UWP CoreWindow o l'handle Win32 HWND, si userà tale HolographicSpace per gestire holographic fotocamere, creare sistemi di coordinate ed eseguire il rendering holographic. Lo spazio holographic corrente viene usato in più posizioni nel modello di DirectX:
* Il **DeviceResources** classe deve ottenere alcune informazioni dall'oggetto HolographicSpace per creare il dispositivo Direct3D. Questo è l'ID della scheda DXGI associato alla visualizzazione olografica. Il <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> classe Usa dispositivi dell'app Direct3D 11 per creare e gestire le risorse basate su dispositivo, ad esempio il buffer per ogni videocamera holographic. Se si è interessati a visualizzare ciò che svolge questa funzione dietro le quinte, si potrà risultare in Deviceresources.
* La funzione **DeviceResources::InitializeUsingHolographicSpace** viene illustrato come ottenere l'adapter Cerca l'identificatore univoco locale – e spiega come scegliere un adattatore predefinito quando non viene specificato alcun adattatore preferito.
* Classe principale dell'app Usa dello spazio da holographic **AppView::SetWindow** oppure **App::CreateWindowAndHolographicSpace** per gli aggiornamenti e per il rendering.

>[!NOTE]
>Anche se le sezioni seguenti ricordare i nomi delle funzioni del modello come **AppView::SetWindow** che basate sul presupposto che è stata avviata dal modello di app UWP holographic, i frammenti di codice viene visualizzato verranno applicata in modo uniforme tra le app UWP e Win32.

Successivamente, verrà esaminato il programma di installazione che elaborano **SetHolographicSpace** è responsabile della classe AppMain.

## <a name="subscribe-to-camera-events-create-and-remove-camera-resources"></a>Sottoscrivere gli eventi della fotocamera, creare e rimuovere le risorse della fotocamera

Contenuto holographic dell'app si trova nel relativo spazio holographic e possono essere visualizzato tramite uno o più fotocamere holographic che rappresentano diverse prospettive nella scena. Dopo aver creato lo spazio holographic, è possibile ricevere i dati relativi a fotocamere holographic.

L'app deve rispondere **CameraAdded** eventi mediante la creazione di tutte le risorse che sono specifici di tale fotocamera, indica come visualizzazione destinazione rendering del buffer nascosto. È possibile visualizzare il codice nel **DeviceResources::SetHolographicSpace** funzione, denominata **AppView::SetWindow** prima che l'app crea qualsiasi frame holographic:

```cpp
m_cameraAddedToken = m_holographicSpace.CameraAdded(
    std::bind(&AppMain::OnCameraAdded, this, _1, _2));
```

L'app deve inoltre rispondere **CameraRemoved** eventi rilasciando le risorse che sono state create per tale fotocamera.

Dal **DeviceResources::SetHolographicSpace**:

```cpp
m_cameraRemovedToken = m_holographicSpace.CameraRemoved(
    std::bind(&AppMain::OnCameraRemoved, this, _1, _2));
```

I gestori di eventi devono completare alcune operazioni per mantenere il rendering holographic trasmessi senza problemi, e in modo che l'app è in grado di eseguire il rendering affatto. Leggere il codice e i commenti per i dettagli: è possibile cercare **OnCameraAdded** e **OnCameraRemoved** nella classe principale per comprendere come il **m_cameraResources** mappa è gestito da **DeviceResources**.

Al momento, si impegna per AppMain e le impostazioni di cui avviene per abilitare l'app di sapere sulle videocamere holographic. A tal fine, è importante tenere conto dei seguenti due requisiti:

1. Per il **CameraAdded** gestore eventi, l'app può funzionare in modo asincrono per completare la creazione di risorse e il caricamento di asset per la nuova fotocamera holographic. Le app che accettano più di un frame per completare questa operazione dovrebbero richiedere un rinvio e completare il rinvio dopo il caricamento in modo asincrono; una [attività PPL](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl) può essere utilizzato per svolgere il lavoro asincrono. L'app deve garantire che è pronto per eseguire il rendering a tale tipo di camera immediatamente quando si conclude il gestore dell'evento o quando viene completato il rinvio. Uscita dal gestore eventi o di completare il rinvio indica al sistema che l'app è ora pronto per ricevere i frame holographic con tale fotocamera inclusa.

2. Quando l'app riceve un **CameraRemoved** evento, è necessario rilasciare tutti i riferimenti per il buffer nascosto e di uscita immediatamente e la funzione. Ciò include le viste di destinazione di rendering e qualsiasi altra risorsa che potrebbe contenere un riferimento al [IDXGIResource](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource). L'applicazione deve inoltre garantire che il buffer nascosto non è collegato come destinazione di rendering, come illustrato nella **CameraResources::ReleaseResourcesForBackBuffer**. Per velocizzare le operazioni lungo, l'app può rilasciare il buffer nascosto, quindi avviare un'attività per completare in modo asincrono tutte le altre operazioni che sono necessaria chiudere tale fotocamera. Il modello di app holographic include un'attività PPL che è possibile usare per questo scopo.

>[!NOTE]
>Se si desidera determinare quando una fotocamera aggiunta o rimossa viene visualizzata nel frame, usare il **HolographicFrame** [AddedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) e [RemovedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) proprietà.

## <a name="create-a-frame-of-reference-for-your-holographic-content"></a>Creare un frame di riferimento per il contenuto holographic

Contenuto dell'app deve essere posizionato una [sistema di coordinate spaziale](coordinate-systems-in-directx.md) da sottoporre a rendering nel HolographicSpace. Il sistema fornisce due primari frame di riferimento che è possibile usare per stabilire un sistema di coordinate per la vntana.

Esistono due tipi di frame di riferimento in Windows Holographic: fare riferimento a frame collegati al dispositivo e frame di riferimento che rimangano fermo mentre si sposta il dispositivo tramite l'ambiente dell'utente. Il modello di app holographic Usa un frame di riferimento fisso per impostazione predefinita. Questo è uno dei modi più semplici per eseguire il rendering vntana bloccato al mondo.

I frame di riferimento fisso sono progettati per stabilizzare le posizioni nella posizione corrente del dispositivo. Ciò significa che le coordinate del dispositivo sono autorizzate a deviano leggermente rispetto all'ambiente dell'utente come il dispositivo viene a conoscenza delle informazioni sullo spazio intorno a esso. Esistono due modi per creare un fotogramma di riferimento fisso: acquisire il sistema di coordinate dal [fase spaziali](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), oppure usare il valore predefinito <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>. Se si sta creando un'app per realtà mista di Windows per le cuffie coinvolgente e concreto, il punto di partenza consigliato è il [fase spaziali](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), che offre anche informazioni sulle funzionalità del visore VR immersivi indossate dal personale dal lettore. In questo caso, viene illustrato come usare il valore predefinito <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.

L'indicatore di posizione spaziale rappresenta il dispositivo di realtà mista di Windows e rileva il movimento del dispositivo e fornisce i sistemi di coordinate che possono essere interpretati rispetto alla relativa posizione.

Dal **AppMain::OnHolographicDisplayIsAvailableChanged**:

```cpp
spatialLocator = SpatialLocator::GetDefault();
```

Creare il frame di riferimento fisso a una sola volta quando l'app viene avviata. Questo comportamento è analogo alla definizione di un sistema di coordinate world, con l'origine inserita nella posizione del dispositivo quando l'app viene avviata. Il frame di riferimento non viene spostati con il dispositivo.

Dal **AppMain::SetHolographicSpace**:

```cpp
m_stationaryReferenceFrame =
    m_spatialLocator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```

Tutti i frame di riferimento sono gravità allineate, il che significa che l'asse y punti "up" per quanto riguarda l'ambiente dell'utente. Poiché Windows Usa sistemi di coordinate "destra", la direzione dell'asse z coincide con la direzione "forward" è rivolta verso il dispositivo quando viene creato il frame di riferimento.

>[!NOTE]
>Quando l'app richiede il posizionamento preciso degli vntana singoli, usare una <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a> ancorare l'ologrammi singole in una posizione nel mondo reale. Usare un punto di ancoraggio spaziale, ad esempio, quando l'utente indica che un punto di particolare interesse. Le posizioni di ancoraggio non dello sfasamento, ma può essere modificate. Per impostazione predefinita, quando un ancoraggio viene regolato, semplifica la relativa posizione nella posizione corretta dei frame successivi diversi dopo che si è verificata la correzione. A seconda dell'applicazione, in questo caso è possibile gestire la regolazione in modo diverso (ad esempio rinviarla fino a quando l'ologrammi sono all'esterno della visualizzazione). Il <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a> proprietà e <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a> queste personalizzazioni gli eventi.

## <a name="respond-to-locatability-changed-events"></a>Rispondere agli eventi locatability modificato

Per il rendering bloccato world vntana richiede che il dispositivo sia in grado di individuare se stessa nel mondo. Ciò potrebbe non essere sempre possibile a causa di condizioni ambientali e in questo caso, l'utente può aspettarsi un'indicazione visiva dell'interruzione di rilevamento. Questa indicazione visiva rendering deve essere eseguito utilizzando i fotogrammi di riferimento collegati al dispositivo, anziché in sosta al mondo.

App può richiedere per ricevere una notifica se il rilevamento viene interrotta per qualsiasi motivo. Registrare per l'evento LocatabilityChanged rilevare quando la capacità della periferica stesso individuare le modifiche del mondo. Da **AppMain::SetHolographicSpace:**

```cpp
m_locatabilityChangedToken = m_spatialLocator.LocatabilityChanged(
    std::bind(&HolographicApp6Main::OnLocatabilityChanged, this, _1, _2));
```

Utilizzare questo evento per determinare quando vntana non può essere eseguito il rendering fermo per tutto il mondo.

## <a name="see-also"></a>Vedere anche
* [Per il rendering in DirectX](rendering-in-directx.md)
* [Sistemi di coordinate in DirectX](coordinate-systems-in-directx.md)

---
title: Recupero di un HolographicSpace
description: Viene illustrata l'API HolographicSpace, un concetto di base per il rendering olografico e l'input spaziale.
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, HolographicSpace, CoreWindow, input spaziale, rendering, catena di scambio, frame olografico, ciclo di aggiornamento, ciclo di gioco, frame di riferimento, locatability, codice di esempio, procedura dettagliata
ms.openlocfilehash: 76211c8a5394e2e296748253df4eac063841746c
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277829"
---
# <a name="getting-a-holographicspace"></a>Recupero di un HolographicSpace

La classe <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> è il portale nel mondo olografico. Controlla il rendering immersivo, fornisce i dati della fotocamera e fornisce l'accesso alle API di ragionamento spaziale. Ne viene creato uno per il <a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a> dell'app UWP o l'HWND dell'app Win32.

## <a name="set-up-the-holographic-space"></a>Configurare lo spazio olografico

La creazione dell'oggetto spazio olografico è il primo passaggio per creare un'app per la realtà mista di Windows. Le applicazioni Windows tradizionali eseguono il rendering di una catena di scambio Direct3D creata per la finestra principale della visualizzazione dell'applicazione. Questa catena di scambio viene visualizzata in uno Slate nell'interfaccia utente olografica. Per rendere olografica la visualizzazione dell'applicazione anziché una lavagna 2D, creare uno spazio olografico per la finestra principale anziché una catena di scambio. La presentazione di frame olografici creati da questo spazio olografico consente di inserire l'app in modalità di rendering a schermo intero.

Per un' **app UWP** [a partire dal *modello di app DirectX 11 (Windows universale) olografico*](creating-a-holographic-directx-project.md), cercare questo codice nel metodo **sewindow** in AppView. cpp:

```cpp
m_holographicSpace = HolographicSpace::CreateForCoreWindow(window);
```

Per un' **app Win32** [a partire dall'esempio Win32 *BasicHologram* ](creating-a-holographic-directx-project.md#creating-a-win32-project), vedere **app:: CreateWindowAndHolographicSpace** per un esempio di come creare un HWND e quindi convertirlo in un HWND immersivo creando un <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>associato:
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

Ora che è stato ottenuto un HolographicSpace per UWP CoreWindow o l'HWND Win32, è possibile usare tale HolographicSpace per gestire le fotocamere olografiche, creare sistemi di coordinate ed eseguire il rendering olografico. Lo spazio olografico corrente viene usato in più posizioni nel modello DirectX:
* La classe **DeviceResources** deve ottenere alcune informazioni dall'oggetto HolographicSpace per creare il dispositivo Direct3D. ID adattatore DXGI associato alla visualizzazione olografica. La classe <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> usa il dispositivo Direct3D 11 dell'app per creare e gestire risorse basate su dispositivo, ad esempio i buffer indietro per ogni fotocamera olografica. Se si è interessati a vedere il funzionamento di questa funzione sotto la cappa, è possibile trovarla in DeviceResources. cpp.
* La funzione **DeviceResources:: InitializeUsingHolographicSpace** illustra come ottenere l'adapter cercando LUID e come scegliere una scheda predefinita se non è specificata alcuna scheda preferita.
* La classe principale dell'app usa lo spazio olografico di **AppView:: sewindow** o **app:: CreateWindowAndHolographicSpace** per gli aggiornamenti e il rendering.

>[!NOTE]
>Mentre le sezioni seguenti menzionano i nomi di funzione del modello come **AppView:: sefinestra** che presuppone che sia stato avviato dal modello di app UWP olografico, i frammenti di codice visualizzati verranno applicati equamente nelle app UWP e Win32.

Successivamente, verrà analizzato il processo di installazione di cui **SetHolographicSpace** è responsabile nella classe AppMain.

## <a name="subscribe-to-camera-events-create-and-remove-camera-resources"></a>Sottoscrivere gli eventi della fotocamera, creare e rimuovere le risorse della fotocamera

Il contenuto olografico dell'app si trova nello spazio olografico e viene visualizzato tramite una o più fotocamere olografiche che rappresentano prospettive diverse sulla scena. Ora che si dispone dello spazio olografico, è possibile ricevere i dati per le fotocamere olografiche.

L'app deve rispondere agli eventi **CameraAdded** creando le risorse specifiche della fotocamera, ad esempio la visualizzazione della destinazione di rendering del buffer nascosto. È possibile visualizzare questo codice nella funzione **DeviceResources:: SetHolographicSpace** , chiamato da **AppView:: sefinestra** prima che l'app crei qualsiasi frame olografico:

```cpp
m_cameraAddedToken = m_holographicSpace.CameraAdded(
    std::bind(&AppMain::OnCameraAdded, this, _1, _2));
```

L'app deve anche rispondere agli eventi **CameraRemoved** rilasciando le risorse create per la fotocamera.

Da **DeviceResources:: SetHolographicSpace**:

```cpp
m_cameraRemovedToken = m_holographicSpace.CameraRemoved(
    std::bind(&AppMain::OnCameraRemoved, this, _1, _2));
```

I gestori di eventi devono completare alcune operazioni per garantire che il rendering olografico scorra senza problemi e che l'app sia in grado di eseguire il rendering. Leggere il codice e i commenti per i dettagli: è possibile cercare **OnCameraAdded** e **OnCameraRemoved** nella classe principale per comprendere in che modo la mappa **m_cameraResources** viene gestita da **DeviceResources**.

A questo punto, ci siamo concentrati su AppMain e sulla configurazione che consente all'app di sapere sulle fotocamere olografiche. Tenendo presente questo aspetto, è importante prendere in considerazione i due requisiti seguenti:

1. Per il gestore dell'evento **CameraAdded** , l'app può funzionare in modo asincrono per completare la creazione di risorse e il caricamento di asset per la nuova fotocamera olografica. Le app che accettano più di un frame per completare questa operazione devono richiedere un rinvio e completare il rinvio dopo il caricamento asincrono. un' [attività PPL](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl) può essere utilizzata per eseguire operazioni asincrone. L'app deve assicurarsi che sia pronta per il rendering della fotocamera immediatamente quando esce dal gestore eventi o quando completa il rinvio. Se si esce dal gestore eventi o si completa il rinvio, viene indicato al sistema che l'app è ora pronta a ricevere i frame olografici con la fotocamera inclusa.

2. Quando l'app riceve un evento **CameraRemoved** , deve rilasciare tutti i riferimenti al buffer nascosto e chiudere immediatamente la funzione. Sono incluse le visualizzazioni della destinazione di rendering e qualsiasi altra risorsa che può includere un riferimento a [IDXGIResource](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource). L'app deve inoltre assicurarsi che il buffer nascosto non sia collegato come destinazione di rendering, come illustrato in **CameraResources:: ReleaseResourcesForBackBuffer**. Per velocizzare le operazioni, l'app può rilasciare il buffer nascosto e avviare un'attività per completare in modo asincrono qualsiasi altra operazione necessaria per arrestare la fotocamera. Il modello di app olografico include un'attività PPL che è possibile usare a questo scopo.

>[!NOTE]
>Per determinare quando viene visualizzata una fotocamera aggiunta o rimossa nel frame, usare le proprietà **HolographicFrame** [AddedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) e [RemovedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) .

## <a name="create-a-frame-of-reference-for-your-holographic-content"></a>Creare un frame di riferimento per il contenuto olografico

Il contenuto dell'app deve essere posizionato in un [sistema di coordinate spaziali](coordinate-systems-in-directx.md) per poter essere sottoposto a rendering nella HolographicSpace. Il sistema fornisce due frame primari di riferimento che è possibile usare per definire un sistema di coordinate per gli ologrammi.

Sono disponibili due tipi di frame di riferimento in Windows olografico: frame di riferimento collegati al dispositivo e frame di riferimento che rimangono fissi quando il dispositivo viene spostato nell'ambiente dell'utente. Per impostazione predefinita, il modello di applicazione olografica usa un frame di riferimento fisso. Questo è uno dei modi più semplici per eseguire il rendering degli ologrammi con blocco mondiale.

I frame di riferimento stazionari sono progettati per stabilizzare le posizioni vicino alla posizione corrente del dispositivo. Ciò significa che le coordinate aggiuntive del dispositivo sono consentite alla deviazione leggermente rispetto all'ambiente dell'utente, perché il dispositivo apprende altre informazioni sullo spazio. Esistono due modi per creare un frame di riferimento stazionario: acquisire il sistema di coordinate dalla [fase spaziale](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)oppure usare il valore predefinito <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>. Se si sta creando un'app di realtà mista di Windows per auricolari immersivi, il punto di partenza consigliato è la [fase spaziale](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), che fornisce anche informazioni sulle funzionalità dell'auricolare immersivo utilizzato dal lettore. Qui viene illustrato come usare il valore predefinito <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.

Il localizzatore spaziale rappresenta il dispositivo di realtà mista di Windows e tiene traccia del movimento del dispositivo e fornisce sistemi di coordinate che possono essere riconosciuti in relazione alla relativa posizione.

Da **AppMain:: OnHolographicDisplayIsAvailableChanged**:

```cpp
spatialLocator = SpatialLocator::GetDefault();
```

Creare il frame di riferimento fisso una volta all'avvio dell'app. Questo è analogo alla definizione di un sistema di coordinate globale, con l'origine posizionata in corrispondenza della posizione del dispositivo all'avvio dell'app. Questo frame di riferimento non si sposta con il dispositivo.

Da **AppMain:: SetHolographicSpace**:

```cpp
m_stationaryReferenceFrame =
    m_spatialLocator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```

Tutti i frame di riferimento sono allineati a gravità, ovvero l'asse y punta "verso l'alto" rispetto all'ambiente dell'utente. Poiché Windows utilizza i sistemi di coordinate "di destra", la direzione dell'asse – z coincide con la direzione "Avanti" del dispositivo quando viene creato il frame di riferimento.

>[!NOTE]
>Quando l'app richiede un posizionamento preciso dei singoli ologrammi, usare un <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a> per ancorare il singolo ologramma a una posizione nel mondo reale. Ad esempio, usare un ancoraggio spaziale quando l'utente indica un punto di interesse speciale. Le posizioni di ancoraggio non sono derivate, ma possono essere modificate. Per impostazione predefinita, quando si modifica un ancoraggio, la posizione viene semplificata al posto dei diversi frame successivi dopo la correzione. A seconda dell'applicazione, in questo caso si potrebbe voler gestire la regolazione in modo diverso, ad esempio rinviando l'ologramma al di fuori della visualizzazione. La proprietà <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a> e gli eventi <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a> abilitano queste personalizzazioni.

## <a name="respond-to-locatability-changed-events"></a>Risposta agli eventi locatability modificati

Il rendering di ologrammi con blocco universale richiede che il dispositivo sia in grado di trovarsi nel mondo. Questo potrebbe non essere sempre possibile a causa di condizioni ambientali e, in tal caso, l'utente può prevedere un'indicazione visiva dell'interruzione del rilevamento. È necessario eseguire il rendering di questa indicazione visiva usando i frame di riferimento collegati al dispositivo, anziché stazionari al mondo.

L'app può richiedere di ricevere una notifica in caso di interruzione del rilevamento per qualsiasi motivo. Eseguire la registrazione per l'evento LocatabilityChanged per rilevare quando la capacità del dispositivo di individuarsi nel mondo cambia. Da **AppMain:: SetHolographicSpace:**

```cpp
m_locatabilityChangedToken = m_spatialLocator.LocatabilityChanged(
    std::bind(&HolographicApp6Main::OnLocatabilityChanged, this, _1, _2));
```

Usare quindi questo evento per determinare quando gli ologrammi non possono essere resi stazionari al mondo.

## <a name="see-also"></a>Vedere anche
* [Rendering in DirectX](rendering-in-directx.md)
* [Sistemi di coordinate in DirectX](coordinate-systems-in-directx.md)

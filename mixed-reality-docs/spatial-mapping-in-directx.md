---
title: Mapping spaziale in DirectX
description: Viene illustrato come implementare il mapping spaziale nell'app DirectX. Questo include una spiegazione dettagliata dell'applicazione di esempio di mapping spaziale inclusa con l'SDK piattaforma UWP (Universal Windows Platform).
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, mapping spaziale, ambiente, interazione, DirectX, WinRT, API, codice di esempio, UWP, SDK, procedura dettagliata
ms.openlocfilehash: b3ef74a7e11e0e73fce47e4c7193ace42ffe7c20
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277499"
---
# <a name="spatial-mapping-in-directx"></a>Mapping spaziale in DirectX

Questo argomento descrive come implementare il [mapping spaziale](spatial-mapping.md) nell'app DirectX. Questo include una spiegazione dettagliata dell'applicazione di esempio di mapping spaziale inclusa con l'SDK piattaforma UWP (Universal Windows Platform).

Questo argomento usa il codice dell'esempio di codice UWP di [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) .

>[!NOTE]
>I frammenti di codice in questo articolo illustrano attualmente l' C++uso di/CX, invece di/WinRT conformi C++a C + 17 come usato nel modello di [ C++ progetto olografico](creating-a-holographic-directx-project.md).  I concetti sono equivalenti per C++un progetto/WinRT, anche se sarà necessario tradurre il codice.

## <a name="device-support"></a>Supporto per i dispositivi

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Funzionalità</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (prima generazione)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
    </tr>
     <tr>
        <td>Mapping spaziale</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="directx-development-overview"></a>Panoramica sullo sviluppo di DirectX

Lo sviluppo di applicazioni native per il mapping spaziale USA le API nello spazio dei nomi [Windows. Perception. Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) . Queste API offrono il controllo completo della funzionalità di mapping spaziale, in modo direttamente analogo alle API di mapping spaziale esposte da [Unity](spatial-mapping-in-unity.md).

### <a name="perception-apis"></a>API di percezione

I tipi primari forniti per lo sviluppo di mapping spaziale sono i seguenti:
* [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) fornisce informazioni sulle superfici in aree di spazio specificate dall'applicazione in prossimità dell'utente, sotto forma di oggetti SpatialSurfaceInfo.
* [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) descrive una singola superficie spaziale esistente, incluso un ID univoco, il volume di delimitazione e l'ora dell'Ultima modifica. Fornirà un SpatialSurfaceMesh in modo asincrono su richiesta.
* [SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) contiene i parametri usati per personalizzare gli oggetti SpatialSurfaceMesh richiesti da SpatialSurfaceInfo.
* [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) rappresenta i dati mesh per una singola superficie spaziale. I dati per le posizioni del vertice, le normali dei vertici e gli indici dei triangoli sono contenuti negli oggetti SpatialSurfaceMeshBuffer del membro.
* [SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) esegue il wrapping di un singolo tipo di dati mesh.

Quando si sviluppa un'applicazione con queste API, il flusso del programma di base sarà simile al seguente (come illustrato nell'applicazione di esempio descritta di seguito):
- **Configurare il SpatialSurfaceObserver**
  - Chiamare [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx)per assicurarsi che l'utente disponga dell'autorizzazione per l'uso delle funzionalità di mapping spaziale del dispositivo da parte dell'applicazione.
  - Creare un'istanza di un oggetto SpatialSurfaceObserver.
  - Chiamare [SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) per specificare le aree di spazio in cui si desiderano informazioni sulle superfici spaziali. È possibile modificare queste aree in futuro chiamando semplicemente questa funzione. Ogni area viene specificata usando un [SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx).
  - Eseguire la registrazione per l'evento [ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) , che verrà attivato ogni volta che sono disponibili nuove informazioni sulle superfici spaziali nelle aree di spazio specificate.
- **Elabora eventi ObservedSurfacesChanged**
  - Nel gestore eventi chiamare [GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) per ricevere una mappa di oggetti SpatialSurfaceInfo. Utilizzando questa mappa, è possibile aggiornare i record delle superfici spaziali [presenti nell'ambiente dell'utente](spatial-mapping.md#mesh-caching).
  - Per ogni oggetto SpatialSurfaceInfo, è possibile eseguire una query su [TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) per determinare gli extent spaziali della superficie, espressa in un [sistema di coordinate spaziali](coordinate-systems.md) a scelta.
  - Se si decide di richiedere una mesh per una superficie spaziale, chiamare [TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx). È possibile specificare opzioni che specificano la densità desiderata dei triangoli e il formato dei dati della mesh restituiti.
- **Rete di ricezione ed elaborazione**
  - Ogni chiamata a TryComputeLatestMeshAsync restituirà aysnchronously un oggetto SpatialSurfaceMesh.
  - Da questo oggetto è possibile accedere agli oggetti SpatialSurfaceMeshBuffer contenuti per accedere agli indici triangolari, alle posizioni dei vertici e alle normali del vertice, se richiesti, della mesh. Questi dati saranno in un formato compatibile direttamente con le [API Direct3D 11](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) usate per il rendering dei mesh.
  - Da qui l'applicazione può facoltativamente eseguire l'analisi o l' [elaborazione](spatial-mapping.md#mesh-processing) dei dati di rete e usarla per il [rendering](spatial-mapping.md#rendering) e la Raycasting fisica [e il conflitto](spatial-mapping.md#raycasting-and-collision).
  - Un dettaglio importante da tenere presente è che è necessario applicare una scala alle posizioni dei vertici della mesh, ad esempio nel vertex shader usato per il rendering delle mesh, per convertirle dalle unità Integer ottimizzate in cui sono archiviate nel buffer, ai contatori. È possibile recuperare questa scala chiamando [VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx).

### <a name="troubleshooting"></a>Risoluzione dei problemi
* Non dimenticare di ridimensionare le posizioni dei vertici mesh nel vertex shader, usando la scala restituita da [SpatialSurfaceMesh. VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)

## <a name="spatial-mapping-code-sample-walkthrough"></a>Procedura dettagliata di esempio di codice di mapping spaziale

L'esempio di codice di [mapping spaziale olografico](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) include codice che è possibile usare per iniziare a caricare mesh di superficie nell'app, inclusa l'infrastruttura per la gestione e il rendering di mesh di superficie.

A questo punto, viene illustrato come aggiungere la funzionalità di mapping della superficie all'app DirectX. È possibile aggiungere questo codice al progetto di [modello di app Windows olografico](creating-a-holographic-directx-project.md) oppure è possibile seguire l'esempio di codice riportato in precedenza. Questo esempio di codice è basato sul modello di app olografico di Windows.

### <a name="set-up-your-app-to-use-the-spatialperception-capability"></a>Configurare l'app per l'uso della funzionalità spatialPerception

L'app deve essere in grado di usare la funzionalità di mapping spaziale. Questa operazione è necessaria perché la mesh spaziale è una rappresentazione dell'ambiente dell'utente, che può essere considerato dati privati. Dichiarare questa funzionalità nel file Package. appxmanifest per l'app. Ecco un esempio:

```xml
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

La funzionalità deriva dallo spazio dei nomi **uap2** . Per ottenere l'accesso a questo spazio dei nomi nel manifesto, includerlo come attributo *xlmns* nell'elemento &lt;Package >. Ecco un esempio:

```xml
<Package
    xmlns="https://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="https://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="https://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="https://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap uap2 mp"
    >
```

### <a name="check-for-spatial-mapping-feature-support"></a>Verificare il supporto della funzionalità di mapping spaziale

La realtà mista di Windows supporta un'ampia gamma di dispositivi, inclusi i dispositivi che non supportano il mapping spaziale. Se l'app può usare il mapping spaziale o deve usare il mapping spaziale per fornire funzionalità, deve verificare che il mapping spaziale sia supportato prima di provare a usarlo. Se, ad esempio, il mapping spaziale è richiesto dall'app per la realtà mista, viene visualizzato un messaggio in tal senso se un utente prova a eseguirlo su un dispositivo senza mapping spaziale. In alternativa, l'app potrebbe essere in grado di eseguire il rendering del proprio ambiente virtuale al posto dell'ambiente dell'utente, offrendo un'esperienza simile a quella che sarebbe accaduto se fosse disponibile il mapping spaziale. In ogni caso, questa API consente all'app di essere a conoscenza del momento in cui non otterrà dati di mapping spaziali e risponderà nel modo appropriato.

Per controllare il dispositivo corrente per il supporto del mapping spaziale, verificare prima di tutto che il contratto UWP sia al livello 4 o superiore, quindi chiamare SpatialSurfaceObserver:: di supporto (). Di seguito viene illustrato come eseguire questa operazione nel contesto dell'esempio di codice di [mapping spaziale olografico](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) . Il supporto viene verificato immediatamente prima di richiedere l'accesso.

L'API SpatialSurfaceObserver:: di supporto () è disponibile a partire dalla versione 15063 dell'SDK. Se necessario, ridestinare il progetto alla versione della piattaforma 15063 prima di usare questa API.

```cpp
if (m_surfaceObserver == nullptr)
   {
       using namespace Windows::Foundation::Metadata;
       if (ApiInformation::IsApiContractPresent(L"Windows.Foundation.UniversalApiContract", 4))
       {
           if (!SpatialSurfaceObserver::IsSupported())
           {
               // The current system does not have spatial mapping capability.
               // Turn off spatial mapping.
               m_spatialPerceptionAccessRequested = true;
               m_surfaceAccessAllowed = false;
           }
       }

       if (!m_spatialPerceptionAccessRequested)
       {
           /// etc ...
```

Si noti che quando il contratto UWP è inferiore al livello 4, l'app deve continuare come se il dispositivo fosse in grado di eseguire il mapping spaziale.

### <a name="request-access-to-spatial-mapping-data"></a>Richiedere l'accesso ai dati di mapping spaziale

L'app deve richiedere l'autorizzazione per accedere ai dati di mapping spaziale prima di provare a creare gli osservatori di superficie. Di seguito è riportato un esempio basato sull'esempio di codice Surface mapping, con ulteriori dettagli disponibili più avanti in questa pagina:

```cpp
auto initSurfaceObserverTask = create_task(SpatialSurfaceObserver::RequestAccessAsync());
initSurfaceObserverTask.then([this, coordinateSystem](Windows::Perception::Spatial::SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Create a surface observer.
    }
    else
    {
        // Handle spatial mapping unavailable.
    }
}
```

### <a name="create-a-surface-observer"></a>Creare un osservatore di superficie

Lo spazio dei nomi **Windows::P erception:: Spatial:: Surfaces** include la classe [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) , che osserva uno o più volumi specificati in un [SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx). Usare un'istanza di [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) per accedere ai dati di Surface Mesh in tempo reale.

Da **AppMain. h**:

```cpp
// Obtains surface mapping data from the device in real time.
Windows::Perception::Spatial::Surfaces::SpatialSurfaceObserver^     m_surfaceObserver;
Windows::Perception::Spatial::Surfaces::SpatialSurfaceMeshOptions^  m_surfaceMeshOptions;
```

Come indicato nella sezione precedente, è necessario richiedere l'accesso ai dati di mapping spaziale prima che l'app possa usarla. Questo accesso viene concesso automaticamente in HoloLens.

```cpp
// The surface mapping API reads information about the user's environment. The user must
// grant permission to the app to use this capability of the Windows Mixed Reality device.
auto initSurfaceObserverTask = create_task(SpatialSurfaceObserver::RequestAccessAsync());
initSurfaceObserverTask.then([this, coordinateSystem](Windows::Perception::Spatial::SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // If status is allowed, we can create the surface observer.
        m_surfaceObserver = ref new SpatialSurfaceObserver();
```

Successivamente, è necessario configurare l'osservatore della superficie per osservare un volume di delimitazione specifico. Qui viene osservato un riquadro 20x20x5 metri, centrato sull'origine del sistema di coordinate.

```cpp
// The surface observer can now be configured as needed.

        // In this example, we specify one area to be observed using an axis-aligned
        // bounding box 20 meters in width and 5 meters in height and centered at the
        // origin.
        SpatialBoundingBox aabb =
        {
            { 0.f,  0.f, 0.f },
            {20.f, 20.f, 5.f },
        };

        SpatialBoundingVolume^ bounds = SpatialBoundingVolume::FromBox(coordinateSystem, aabb);
        m_surfaceObserver->SetBoundingVolume(bounds);
```

Si noti che è invece possibile impostare più volumi di delimitazione.

*Si tratta di pseudocodice:*

```cpp
m_surfaceObserver->SetBoundingVolumes(/* iterable collection of bounding volumes*/);
```

È anche possibile usare altre forme di delimitazione, ad esempio una vista tronco, o un rettangolo di delimitazione che non è allineato all'asse.

*Si tratta di pseudocodice:*

```cpp
m_surfaceObserver->SetBoundingVolume(
            SpatialBoundingVolume::FromFrustum(/*SpatialCoordinateSystem*/, /*SpatialBoundingFrustum*/)
            );
```

Se l'app deve eseguire operazioni in modo diverso quando i dati di mapping di superficie non sono disponibili, è possibile scrivere codice per rispondere al caso in cui [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) non è **consentito** , ad esempio, non sarà consentito nei PC con dispositivi immersivi collegati perché i dispositivi non hanno hardware per il mapping spaziale. Per questi dispositivi, è invece necessario basarsi sulla fase spaziale per ottenere informazioni sull'ambiente e la configurazione del dispositivo dell'utente.

### <a name="initialize-and-update-the-surface-mesh-collection"></a>Inizializzare e aggiornare la raccolta Surface Mesh

Se l'osservatore della superficie è stato creato correttamente, è possibile procedere con l'inizializzazione della raccolta di mesh della superficie. Qui viene usata l'API del modello pull per ottenere immediatamente il set corrente di superfici osservate:

```cpp
auto mapContainingSurfaceCollection = m_surfaceObserver->GetObservedSurfaces();
        for (auto& pair : mapContainingSurfaceCollection)
        {
            // Store the ID and metadata for each surface.
            auto const& id = pair->Key;
            auto const& surfaceInfo = pair->Value;
            m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
        }
```

Per ottenere i dati di Surface Mesh è disponibile anche un modello push. È possibile progettare l'applicazione in modo che usi solo il modello pull, se si sceglie, nel qual caso verrà eseguito il polling dei dati ogni tanto spesso, ad esempio per ogni fotogramma o durante un periodo di tempo specifico, ad esempio durante l'installazione del gioco. In tal caso, il codice precedente è quello che ti serve.

Nell'esempio di codice si è scelto di illustrare l'uso di entrambi i modelli a scopo pedagogico. Qui viene sottoscritto un evento per ricevere dati di Surface Mesh aggiornati ogni volta che il sistema riconosce una modifica.

```cpp
m_surfaceObserver->ObservedSurfacesChanged += ref new TypedEventHandler<SpatialSurfaceObserver^, Platform::Object^>(
            bind(&HolographicDesktopAppMain::OnSurfacesChanged, this, _1, _2)
            );
```

Il codice di esempio è inoltre configurato per rispondere a questi eventi. Esaminiamo ora come eseguire questa operazione.

**Nota:** Questo potrebbe non essere il modo più efficiente per gestire i dati della mesh nell'app. Questo codice viene scritto per maggiore chiarezza e non è ottimizzato.

I dati della superficie mesh sono disponibili in una mappa di sola lettura che archivia gli oggetti [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) usando [Platform:: GUID](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) come valori chiave.

```cpp
IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection = sender->GetObservedSurfaces();
```

Per elaborare questi dati, si cerca prima i valori di chiave che non sono presenti nella raccolta. Informazioni dettagliate sulla modalità di archiviazione dei dati nell'app di esempio verranno illustrate più avanti in questo argomento.

```cpp
// Process surface adds and updates.
for (const auto& pair : surfaceCollection)
{
    auto id = pair->Key;
    auto surfaceInfo = pair->Value;

    if (m_meshCollection->HasSurface(id))
    {
        // Update existing surface.
        m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
    }
    else
    {
        // New surface.
        m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
    }
}
```

È anche necessario rimuovere le mesh di superficie presenti nella raccolta di mesh della superficie, ma che non sono più presenti nella raccolta di sistema. A tale scopo, è necessario eseguire un'operazione analoga al contrario di quanto appena illustrato per l'aggiunta e l'aggiornamento delle mesh; viene visualizzato un ciclo nella raccolta dell'app e viene verificato se il **GUID** è presente nella raccolta di sistema. Se non è presente nella raccolta di sistema, viene rimossa dalla nostra.

Dal gestore eventi in AppMain. cpp:

```cpp
m_meshCollection->PruneMeshCollection(surfaceCollection);
```

Implementazione della potatura mesh in RealtimeSurfaceMeshRenderer. cpp:

```cpp
void RealtimeSurfaceMeshRenderer::PruneMeshCollection(IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection)
{
    std::lock_guard<std::mutex> guard(m_meshCollectionLock);
    std::vector<Guid> idsToRemove;

    // Remove surfaces that moved out of the culling frustum or no longer exist.
    for (const auto& pair : m_meshCollection)
    {
        const auto& id = pair.first;
        if (!surfaceCollection->HasKey(id))
        {
            idsToRemove.push_back(id);
        }
    }

    for (const auto& id : idsToRemove)
    {
        m_meshCollection.erase(id);
    }
}
```

### <a name="acquire-and-use-surface-mesh-data-buffers"></a>Acquisire e usare i buffer di dati di Surface Mesh

Il recupero delle informazioni sulla mesh della superficie è semplice quanto il pull di una raccolta di dati e l'elaborazione degli aggiornamenti in tale raccolta. A questo punto, verranno fornite informazioni dettagliate su come è possibile usare i dati.

Nell'esempio di codice si è scelto di usare le mesh di superficie per il rendering. Si tratta di uno scenario comune per gli ologrammi occlusione dietro le superfici reali. È anche possibile eseguire il rendering delle mesh o eseguire il rendering delle versioni elaborate di tali mesh per mostrare all'utente quali aree della chat vengono analizzate prima di iniziare a fornire funzionalità per app o giochi.

L'esempio di codice avvia il processo quando riceve gli aggiornamenti di Surface Mesh dal gestore eventi descritto nella sezione precedente. La riga di codice importante in questa funzione è la chiamata a Update the Surface *mesh*: da questo momento abbiamo già elaborato le informazioni di mesh e stiamo per ottenere i dati relativi ai vertici e agli indici da usare nel modo appropriato.

Da RealtimeSurfaceMeshRenderer. cpp:

```cpp
void RealtimeSurfaceMeshRenderer::AddOrUpdateSurface(Guid id, SpatialSurfaceInfo^ newSurface)
{
    auto options = ref new SpatialSurfaceMeshOptions();
    options->IncludeVertexNormals = true;

    auto createMeshTask = create_task(newSurface->TryComputeLatestMeshAsync(1000, options));
    createMeshTask.then([this, id](SpatialSurfaceMesh^ mesh)
    {
        if (mesh != nullptr)
        {
            std::lock_guard<std::mutex> guard(m_meshCollectionLock);
            '''m_meshCollection[id].UpdateSurface(mesh);'''
        }
    }, task_continuation_context::use_current());
}
```

Il codice di esempio è progettato in modo che una classe di dati, **SurfaceMesh**, gestisca l'elaborazione e il rendering dei dati di rete. Questi mesh sono gli elementi di cui **RealtimeSurfaceMeshRenderer** mantiene effettivamente una mappa. Ognuno di essi contiene un riferimento al SpatialSurfaceMesh da cui proviene e viene usato ogni volta che è necessario accedere al vertice mesh o ai buffer di indice oppure ottenere una trasformazione per la mesh. Per il momento, la mesh viene contrassegnata in modo da richiedere un aggiornamento.

Da SurfaceMesh. cpp:

```cpp
void SurfaceMesh::UpdateSurface(SpatialSurfaceMesh^ surfaceMesh)
{
    m_surfaceMesh = surfaceMesh;
    m_updateNeeded = true;
}
```

Alla successiva richiesta di tracciatura da parte della mesh, il flag verrà prima controllato. Se è necessario un aggiornamento, i buffer di Vertex e index verranno aggiornati nella GPU.

```cpp
void SurfaceMesh::CreateDeviceDependentResources(ID3D11Device* device)
{
    m_indexCount = m_surfaceMesh->TriangleIndices->ElementCount;
    if (m_indexCount < 3)
    {
        // Not enough indices to draw a triangle.
        return;
    }
```

In primo luogo, vengono acquisiti i buffer di dati non elaborati:

```cpp
Windows::Storage::Streams::IBuffer^ positions = m_surfaceMesh->VertexPositions->Data;
    Windows::Storage::Streams::IBuffer^ normals   = m_surfaceMesh->VertexNormals->Data;
    Windows::Storage::Streams::IBuffer^ indices   = m_surfaceMesh->TriangleIndices->Data;
```

Quindi, creiamo buffer del dispositivo Direct3D con i dati mesh forniti da HoloLens:

```cpp
CreateDirectXBuffer(device, D3D11_BIND_VERTEX_BUFFER, positions, m_vertexPositions.GetAddressOf());
    CreateDirectXBuffer(device, D3D11_BIND_VERTEX_BUFFER, normals,   m_vertexNormals.GetAddressOf());
    CreateDirectXBuffer(device, D3D11_BIND_INDEX_BUFFER,  indices,   m_triangleIndices.GetAddressOf());

    // Create a constant buffer to control mesh position.
    CD3D11_BUFFER_DESC constantBufferDesc(sizeof(SurfaceTransforms), D3D11_BIND_CONSTANT_BUFFER);
    DX::ThrowIfFailed(
        device->CreateBuffer(
            &constantBufferDesc,
            nullptr,
            &m_modelTransformBuffer
            )
        );

    m_loadingComplete = true;
}
```

**Nota:** Per la funzione helper CreateDirectXBuffer usata nel frammento di codice precedente, vedere l'esempio di codice di mapping di Surface: SurfaceMesh. cpp, GetDataFromIBuffer. h. A questo punto, la creazione delle risorse del dispositivo è stata completata e il mesh viene considerato caricato e pronto per l'aggiornamento e il rendering.

### <a name="update-and-render-surface-meshes"></a>Aggiornare ed eseguire il rendering delle mesh di superficie

La classe SurfaceMesh dispone di una funzione di aggiornamento specializzata. Ogni [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) ha una propria trasformazione e l'esempio usa il sistema di coordinate corrente per il **SpatialStationaryReferenceFrame** per acquisire la trasformazione. Aggiorna quindi il buffer costante del modello nella GPU.

```cpp
void SurfaceMesh::UpdateTransform(
    ID3D11DeviceContext* context,
    SpatialCoordinateSystem^ baseCoordinateSystem
    )
{
    if (m_indexCount < 3)
    {
        // Not enough indices to draw a triangle.
        return;
    }

    XMMATRIX transform = XMMatrixIdentity();

    auto tryTransform = m_surfaceMesh->CoordinateSystem->TryGetTransformTo(baseCoordinateSystem);
    if (tryTransform != nullptr)
    {
        transform = XMLoadFloat4x4(&tryTransform->Value);
    }

    XMMATRIX scaleTransform = XMMatrixScalingFromVector(XMLoadFloat3(&m_surfaceMesh->VertexPositionScale));

    XMStoreFloat4x4(
        &m_constantBufferData.vertexWorldTransform,
        XMMatrixTranspose(
            scaleTransform * transform
            )
        );

    // Normals don't need to be translated.
    XMMATRIX normalTransform = transform;
    normalTransform.r[3] = XMVectorSet(0.f, 0.f, 0.f, XMVectorGetW(normalTransform.r[3]));
    XMStoreFloat4x4(
        &m_constantBufferData.normalWorldTransform,
        XMMatrixTranspose(
            normalTransform
        )
        );

    if (!m_loadingComplete)
    {
        return;
    }

    context->UpdateSubresource(
        m_modelTransformBuffer.Get(),
        0,
        NULL,
        &m_constantBufferData,
        0,
        0
        );
}
```

Quando è il momento di eseguire il rendering delle mesh della superficie, le operazioni di preparazione vengono eseguite prima del rendering della raccolta. Viene configurata la pipeline dello shader per la configurazione di rendering corrente e viene configurata la fase dell'assembler di input. Si noti che la classe helper della fotocamera olografica **CameraResources. cpp** ha già configurato il buffer costante di visualizzazione/proiezione da ora.

Da **RealtimeSurfaceMeshRenderer:: Render**:

```cpp
auto context = m_deviceResources->GetD3DDeviceContext();

context->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);
context->IASetInputLayout(m_inputLayout.Get());

// Attach our vertex shader.
context->VSSetShader(
    m_vertexShader.Get(),
    nullptr,
    0
    );

// The constant buffer is per-mesh, and will be set as such.

if (depthOnly)
{
    // Explicitly detach the later shader stages.
    context->GSSetShader(nullptr, nullptr, 0);
    context->PSSetShader(nullptr, nullptr, 0);
}
else
{
    if (!m_usingVprtShaders)
    {
        // Attach the passthrough geometry shader.
        context->GSSetShader(
            m_geometryShader.Get(),
            nullptr,
            0
            );
    }

    // Attach our pixel shader.
    context->PSSetShader(
        m_pixelShader.Get(),
        nullptr,
        0
        );
}
```

Al termine di questa operazione, viene eseguito il loop sulle mesh e si indica a ognuno di disegnarlo. **Nota:** Questo codice di esempio non è ottimizzato per l'uso di qualsiasi tipo di eliminazione di tronco, ma è necessario includere questa funzionalità nell'app.

```cpp
std::lock_guard<std::mutex> guard(m_meshCollectionLock);

auto device = m_deviceResources->GetD3DDevice();

// Draw the meshes.
for (auto& pair : m_meshCollection)
{
    auto& id = pair.first;
    auto& surfaceMesh = pair.second;

    surfaceMesh.Draw(device, context, m_usingVprtShaders, isStereo);
}
```

Le singole mesh sono responsabili della configurazione del buffer di Vertex e index buffer, stride e della trasformazione del modello. Come per il cubo rotante nel modello di app olografico di Windows, viene eseguito il rendering nei buffer stereoscopici usando le istanze.

Da **SurfaceMesh::D RAW**:

```cpp
// The vertices are provided in {vertex, normal} format

const auto& vertexStride = m_surfaceMesh->VertexPositions->Stride;
const auto& normalStride = m_surfaceMesh->VertexNormals->Stride;

UINT strides [] = { vertexStride, normalStride };
UINT offsets [] = { 0, 0 };
ID3D11Buffer* buffers [] = { m_vertexPositions.Get(), m_vertexNormals.Get() };

context->IASetVertexBuffers(
    0,
    ARRAYSIZE(buffers),
    buffers,
    strides,
    offsets
    );

const auto& indexFormat = static_cast<DXGI_FORMAT>(m_surfaceMesh->TriangleIndices->Format);

context->IASetIndexBuffer(
    m_triangleIndices.Get(),
    indexFormat,
    0
    );

context->VSSetConstantBuffers(
    0,
    1,
    m_modelTransformBuffer.GetAddressOf()
    );

if (!usingVprtShaders)
{
    context->GSSetConstantBuffers(
        0,
        1,
        m_modelTransformBuffer.GetAddressOf()
        );
}

context->PSSetConstantBuffers(
    0,
    1,
    m_modelTransformBuffer.GetAddressOf()
    );

context->DrawIndexedInstanced(
    m_indexCount,       // Index count per instance.
    isStereo ? 2 : 1,   // Instance count.
    0,                  // Start index location.
    0,                  // Base vertex location.
    0                   // Start instance location.
    );
```

### <a name="rendering-choices-with-surface-mapping"></a>Opzioni di rendering con mapping di superficie

Il codice di esempio Surface mapping fornisce il codice per il rendering di solo occlusione dei dati di Surface Mesh e per il rendering su schermo dei dati della superficie mesh. Il percorso scelto, o entrambi, dipende dall'applicazione. In questo documento verranno illustrate in dettaglio entrambe le configurazioni.

**Rendering dei buffer di occlusione per effetto olografico**

Per iniziare, deselezionare la visualizzazione della destinazione di rendering per la fotocamera virtuale corrente.

Da AppMain. cpp:

```cpp
context->ClearRenderTargetView(pCameraResources->GetBackBufferRenderTargetView(), DirectX::Colors::Transparent);
```

Si tratta di un passaggio di pre-rendering. Qui viene creato un buffer di occlusione chiedendo al renderer mesh di eseguire il rendering solo della profondità. In questa configurazione non viene collegata una visualizzazione della destinazione di rendering e il renderer di mesh imposta la fase pixel shader su **nullptr** in modo che la GPU non preferisca disegnare pixel. La geometria verrà rasterizzata nel buffer di profondità e la pipeline grafica verrà arrestata.

```cpp
// Pre-pass rendering: Create occlusion buffer from Surface Mapping data.
context->ClearDepthStencilView(pCameraResources->GetSurfaceDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target to null, and set the depth target occlusion buffer.
// We will use this same buffer as a shader resource when drawing holograms.
context->OMSetRenderTargets(0, nullptr, pCameraResources->GetSurfaceOcclusionDepthStencilView());

// The first pass is a depth-only pass that generates an occlusion buffer we can use to know which
// hologram pixels are hidden behind surfaces in the environment.
m_meshCollection->Render(pCameraResources->IsRenderingStereoscopic(), true);
```

È possibile creare ologrammi con un test di profondità aggiuntivo sul buffer di occlusione del mapping della superficie. In questo esempio di codice viene eseguito il rendering dei pixel sul cubo con un colore diverso se si trovano dietro una superficie.

Da AppMain. cpp:

```cpp
// Hologram rendering pass: Draw holographic content.
context->ClearDepthStencilView(pCameraResources->GetHologramDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target, and set the depth target drawing buffer.
ID3D11RenderTargetView *const targets[1] = { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, pCameraResources->GetHologramDepthStencilView());

// Render the scene objects.
// In this example, we draw a special effect that uses the occlusion buffer we generated in the
// Pre-Pass step to render holograms using X-Ray Vision when they are behind physical objects.
m_xrayCubeRenderer->Render(
    pCameraResources->IsRenderingStereoscopic(),
    pCameraResources->GetSurfaceOcclusionShaderResourceView(),
    pCameraResources->GetHologramOcclusionShaderResourceView(),
    pCameraResources->GetDepthTextureSamplerState()
    );
```

In base al codice di SpecialEffectPixelShader. HLSL:

```cpp
// Draw boundaries
min16int surfaceSum = GatherDepthLess(envDepthTex, uniSamp, input.pos.xy, pixelDepth, input.idx.x);

if (surfaceSum <= -maxSum)
{
    // The pixel and its neighbors are behind the surface.
    // Return the occluded 'X-ray' color.
    return min16float4(0.67f, 0.f, 0.f, 1.0f);
}
else if (surfaceSum < maxSum)
{
    // The pixel and its neighbors are a mix of in front of and behind the surface.
    // Return the silhouette edge color.
    return min16float4(1.f, 1.f, 1.f, 1.0f);
}
else
{
    // The pixel and its neighbors are all in front of the surface.
    // Return the color of the hologram.
    return min16float4(input.color, 1.0f);
}
```

**Nota:** Per la routine **GatherDepthLess** , vedere l'esempio di codice di mapping di Surface: SpecialEffectPixelShader. HLSL.

**Rendering dei dati di Surface Mesh sullo schermo**

È anche possibile creare solo le mesh della superficie nei buffer di visualizzazione stereo. Abbiamo scelto di creare i visi completi con l'illuminazione, ma è possibile creare wireframe, elaborare mesh prima del rendering, applicare una mappa di trama e così via.

Qui, l'esempio di codice indica al renderer mesh di creare la raccolta. Questa volta non viene specificato un passaggio di sola profondità, quindi si collegherà una pixel shader e si completerà la pipeline di rendering usando le destinazioni specificate per la fotocamera virtuale corrente.

```cpp
// Spatial Mapping mesh rendering pass: Draw Spatial Mapping mesh over the world.
context->ClearDepthStencilView(pCameraResources->GetSurfaceOcclusionDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target to the current holographic camera's back buffer, and set the depth buffer.
ID3D11RenderTargetView *const targets[1] = { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, pCameraResources->GetSurfaceDepthStencilView());

// This drawing pass renders the surface meshes to the stereoscopic display. The user will be
// able to see them while wearing the device.
m_meshCollection->Render(pCameraResources->IsRenderingStereoscopic(), false);
```

## <a name="see-also"></a>Vedere anche
* [Creazione di un progetto DirectX olografico](creating-a-holographic-directx-project.md)
* [API Windows. Perception. Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)

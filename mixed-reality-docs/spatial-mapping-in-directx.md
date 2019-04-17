---
title: Mapping spaziale DirectX
description: Viene illustrato come implementare mapping spaziale nell'app DirectX. Ciò include una spiegazione dettagliata dell'applicazione di esempio di mapping spaziale inclusa in Universal Windows Platform SDK.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows misti realtà, mapping spaziale, ambiente, l'interazione, directx, winrt, api, codice di esempio, UWP, SDK, questa procedura dettagliata
ms.openlocfilehash: db3f1464158c04127e456cadd5fb633336909344
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605139"
---
# <a name="spatial-mapping-in-directx"></a>Mapping spaziale DirectX

In questo argomento descrive come implementare [mapping spaziale](spatial-mapping.md) nell'app DirectX. Ciò include una spiegazione dettagliata dell'applicazione di esempio di mapping spaziale inclusa in Universal Windows Platform SDK.

Questo argomento viene usato dal codice il [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) esempio di codice di piattaforma UWP.

>[!NOTE]
>I frammenti di codice in questo articolo illustrano attualmente l'utilizzo di C++/CX invece di C + + 17 conformi C++/WinRT usato nel [ C++ modello di progetto holographic](creating-a-holographic-directx-project.md).  I concetti sono equivalenti per un C++progetto /WinRT, anche se è necessario convertire il codice.

## <a name="directx-development-overview"></a>Panoramica dello sviluppo DirectX

Sviluppo di applicazioni native per mapping spaziale Usa le API con il [Windows.Perception.Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) dello spazio dei nomi. Queste API forniscono il controllo completo di funzionalità di mapping spaziale, in modo analogo direttamente per le API esposte dal mapping spaziale [Unity](spatial-mapping-in-unity.md).

### <a name="perception-apis"></a>API di percezione

Come indicato di seguito sono riportati i tipi primari disponibili per lo sviluppo di mapping spaziale:
* [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) fornisce informazioni su superfici in aree specificata dall'applicazione di spazio quasi l'utente, sotto forma di oggetti SpatialSurfaceInfo.
* [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) descrive una singola superficie spaziale rilevarle incluso un ID univoco, volume e l'ora dell'ultima modifica di delimitazione. Fornirà un SpatialSurfaceMesh in modo asincrono su richiesta.
* [SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) contiene parametri utilizzati per personalizzare gli oggetti SpatialSurfaceMesh richiesti dal SpatialSurfaceInfo.
* [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) rappresenta i dati di rete per una singola superficie spaziale. I dati per le posizioni di vertice, normali vertici e gli indici del triangolo sono contenuti negli oggetti SpatialSurfaceMeshBuffer membro.
* [SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) esegue il wrapping di un singolo tipo di dati di trama.

Quando si sviluppa un'applicazione che Usa queste API, il flusso di programma di base avrà un aspetto simile al seguente (come illustrato nell'applicazione di esempio descritta di seguito):
- **Configurare il SpatialSurfaceObserver**
  - Chiamare [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx), per assicurarsi che l'utente ha dato l'autorizzazione per l'applicazione per usare le funzionalità di mapping spaziale del dispositivo.
  - Creare un'istanza di un oggetto SpatialSurfaceObserver.
  - Chiamare [SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) per specificare le aree di spazio in cui si desiderano informazioni su superfici spaziale. È possibile modificare queste aree in futuro semplicemente chiamando di nuovo questa funzione. Ogni area viene specificato usando un [SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx).
  - Registrarsi per il [ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) evento, che viene attivato ogni volta nuove informazioni sono disponibili sulle aree di spaziale nelle aree dello spazio è stato specificato.
- **Elaborare eventi ObservedSurfacesChanged**
  - Nel gestore eventi, chiamare [GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) per ricevere una mappa di oggetti SpatialSurfaceInfo. Utilizzando questa mappa, è possibile aggiornare i record di quali dispositivi Surface spaziale [presenti nell'ambiente dell'utente](spatial-mapping.md#mesh-caching).
  - Per ogni oggetto SpatialSurfaceInfo, è possibile eseguire una query [TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) per determinare gli extent spaziali della superficie, espressa in un [spaziale sistema di coordinate](coordinate-systems.md) di propria scelta.
  - Se si decide di richieste di rete per una superficie spaziale, chiamare [TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx). È possibile fornire le opzioni che specifica la densità di triangoli desiderata e il formato dei dati restituiti mesh.
- **Ricevere ed elaborare mesh**
  - Ogni chiamata a TryComputeLatestMeshAsync will aysnchronously restituire un oggetto SpatialSurfaceMesh.
  - Da questo oggetto, è possibile accedere gli oggetti SpatialSurfaceMeshBuffer contenuti per poter accedere il indici del triangolo, posizioni di vertice e (se richiesto) normali vertici della mesh. I dati andranno in un formato direttamente compatibile con il [Direct3D 11 API](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) usati per il rendering mesh.
  - A questo punto l'applicazione può anche eseguire analisi o [elaborazione](spatial-mapping.md#mesh-processing) dei dati di trama e usarlo per [rendering](spatial-mapping.md#rendering) fisica e [raycasting e collisione](spatial-mapping.md#raycasting-and-collision).
  - Un dettaglio importante da notare è che è necessario applicare un scalabilità per le posizioni dei vertici mesh (ad esempio in vertex shader usati per il rendering mesh), per convertire tali dalle unità di integer ottimizzato in cui sono archiviati nel buffer, a contatori. È possibile recuperare questa scala chiamando [VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx).

### <a name="troubleshooting"></a>Risoluzione dei problemi
* Non dimenticare di posizioni di vertice trama allo shader vertice, tramite la scala restituita da ridimensionare [SpatialSurfaceMesh.VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)

## <a name="spatial-mapping-code-sample-walkthrough"></a>Procedura di esempio di codice Mapping spaziale

Il [Mapping spaziale Holographic](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) codice di esempio include codice che è possibile usare per iniziare a usare il caricamento di superficie mesh in un'app, nonché l'infrastruttura per la gestione e la superficie di rendering mesh.

A questo punto, viene illustrato come aggiungere funzionalità di mapping superficie all'App DirectX. È possibile aggiungere questo codice per il [modello di app Windows Holographic](creating-a-holographic-directx-project.md) progetto oppure è possibile seguire la procedura esplorando il codice di esempio indicato in precedenza. Questo esempio di codice si basa sul modello di app Windows Holographic.

### <a name="set-up-your-app-to-use-the-spatialperception-capability"></a>Configurare l'app per usare la funzionalità spatialPerception

L'app deve essere in grado di usare la funzionalità di mapping spaziale. Ciò è necessario perché il reticolato spaziale è una rappresentazione dell'ambiente dell'utente, che può essere considerato dati privati. Dichiarare questa funzionalità nel file package. appxmanifest per l'app. Di seguito è riportato un esempio:

```xml
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

La funzionalità proviene il **uap2** dello spazio dei nomi. Per poter accedere a questo spazio dei nomi nel manifesto, includerlo come un *xlmns* attributo il &lt;pacchetto > elemento. Di seguito è riportato un esempio:

```xml
<Package
    xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap uap2 mp"
    >
```

### <a name="check-for-spatial-mapping-feature-support"></a>Verificare il supporto di funzionalità di mapping spaziale

Realtà mista di Windows supporta un'ampia gamma di dispositivi, inclusi quelli che non supportano il mapping spaziale. Se l'app può usare il mapping spaziale o necessario usare mapping spaziale, per fornire funzionalità, è necessario verificare per assicurarsi che il mapping spaziale è supportato prima di provare a usarlo. Ad esempio, se mapping spaziale è richiesto dall'app per realtà mista, visualizzerà un messaggio in tal senso se un utente tenta di eseguirlo in un dispositivo senza mapping spaziale. In alternativa, l'app potrebbe essere in grado di eseguire il rendering di un proprio ambiente virtuale al posto di ambiente dell'utente, offrendo un'esperienza simile a che cosa accadrebbe se mapping spaziale non erano disponibili. In ogni caso, questa API consente all'app da tenere presenti quando non recuperare i dati di mapping spaziale e rispondere nel modo appropriato.

Per controllare il dispositivo corrente per il supporto di mapping spaziale, prima di tutto assicurarsi che il contratto UWP è al livello 4 o versione successiva e quindi chiamare SpatialSurfaceObserver::IsSupported(). Ecco come eseguire questa operazione nel contesto del [Mapping spaziale Holographic](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) esempio di codice. Il supporto viene controllato appena prima che richiede l'accesso.

L'API SpatialSurfaceObserver::IsSupported() è disponibile a partire da SDK versione 15063. Se necessario, è possibile Ridestinare il progetto alla versione della piattaforma 15063 prima di usare questa API.

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

Si noti che, quando il contratto UWP è minore di livello 4, l'app deve continuare come se il dispositivo è in grado di soddisfare mapping spaziale.

### <a name="request-access-to-spatial-mapping-data"></a>Richiedere l'accesso ai dati di mapping spaziale

L'app deve richiedere l'autorizzazione per accedere ai dati di mapping spaziale prima di tentare di creare qualsiasi superficie osservatori. Di seguito è riportato un esempio in base al nostro esempio di codice il Mapping di area, con maggiori dettagli, forniti più avanti in questa pagina:

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

### <a name="create-a-surface-observer"></a>Creare un observer surface

Il **Windows::Perception::Spatial::Surfaces** spazio dei nomi include le [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) classe, che rileva uno o più volumi che specificano in un [ SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx). Usare un [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) istanza per accedere ai dati di trama della superficie in tempo reale.

Dal **AppMain.h**:

```cpp
// Obtains surface mapping data from the device in real time.
Windows::Perception::Spatial::Surfaces::SpatialSurfaceObserver^     m_surfaceObserver;
Windows::Perception::Spatial::Surfaces::SpatialSurfaceMeshOptions^  m_surfaceMeshOptions;
```

Come indicato nella sezione precedente, è necessario richiedere l'accesso ai dati di mapping spaziale prima che l'app può utilizzarlo. Questo accesso viene concesso automaticamente nella finestra di HoloLens.

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

Successivamente, è necessario configurare l'osservatore superficie per osservare un volume specifico di delimitazione. In questo caso, riscontrata una finestra che è 20 x 20 x 5 metri, centrato rispetto all'origine del sistema di coordinate.

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

Si noti che è possibile impostare più volumi di delimitazione.

*Si tratta di pseudocodice:*

```cpp
m_surfaceObserver->SetBoundingVolumes(/* iterable collection of bounding volumes*/);
```

È anche possibile usare altre forme di delimitazione - ad esempio un cono, vista o un rettangolo di selezione dell'asse non è allineato.

*Si tratta di pseudocodice:*

```cpp
m_surfaceObserver->SetBoundingVolume(
            SpatialBoundingVolume::FromFrustum(/*SpatialCoordinateSystem*/, /*SpatialBoundingFrustum*/)
            );
```

Se l'app deve eseguire alcuna operazione in modo diverso quando i dati di mapping surface non sono disponibili, è possibile scrivere codice per rispondere al caso in cui il [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) non è **consentito** , ad esempio non sarà possibile nei PC con immersive periferiche collegate perché non dispone di tali dispositivi hardware per il mapping spaziale. Per questi dispositivi, è invece necessario affidarsi a stage spaziali per informazioni sull'ambiente e configurazione del dispositivo dell'utente.

### <a name="initialize-and-update-the-surface-mesh-collection"></a>Inizializzare e aggiornare la raccolta di trama della superficie

Se è stato creato correttamente l'osservatore surface, è possibile procedere per inizializzare la raccolta di trama della superficie. In questo caso, utilizziamo l'API del modello pull per ottenere il set corrente di superfici osservate subito:

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

È inoltre disponibile un modello push disponibile per ottenere i dati di trama della superficie. Si è liberi di progettare l'applicazione usi solo il modello di pull se si sceglie, nel qual caso si sarà esegue il polling per i dati di tanto in tanto, ad esempio, una volta per frame - o durante un periodo di tempo specifico, ad esempio durante l'installazione del gioco. In questo caso, il codice sopra riportato è ciò che è necessario.

Nel nostro esempio di codice, abbiamo scelto illustrare l'utilizzo di entrambi i modelli per a scopo formativo. In questo caso, si sottoscrive un evento di ricevere i dati di trama della superficie aggiornate ogni volta che il sistema rileva una modifica.

```cpp
m_surfaceObserver->ObservedSurfacesChanged += ref new TypedEventHandler<SpatialSurfaceObserver^, Platform::Object^>(
            bind(&HolographicDesktopAppMain::OnSurfacesChanged, this, _1, _2)
            );
```

L'esempio di codice è inoltre configurato per rispondere a tali eventi. Di seguito viene illustrato come è eseguire questa operazione.

**NOTA:** Ciò potrebbe non essere il modo più efficiente per l'app per la gestione dei dati di trama. Questo codice viene scritto per maggiore chiarezza e non è ottimizzato.

Vengono forniti in una mappa di sola lettura che archivia dati trama della superficie [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) degli oggetti mediante [Platform::Guids](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) come valori delle chiavi.

```cpp
IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection = sender->GetObservedSurfaces();
```

Per elaborare i dati, verranno esaminate prima per valori di chiave che non si trovano nella nostra raccolta. Visualizzerà i dettagli sul modo in cui i dati vengono archiviati nella nostra app di esempio più avanti in questo argomento.

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

È anche necessario rimuovere superficie trame che sono nella nostra raccolta di trama della superficie, ma che non sono in più la raccolta di sistema. A tale scopo, è necessario eseguire un'operazione simile il contrario di ciò che abbiamo appena illustrato per aggiungere e aggiornare le reti mesh di; esegue il ciclo nella raccolta dell'app e verificare se il **Guid** abbiamo è incluso nella raccolta di sistema. Se non è nell'insieme di sistema, abbiamo rimuoverlo da noi.

Dal nostro gestore di eventi in AppMain.cpp:

```cpp
m_meshCollection->PruneMeshCollection(surfaceCollection);
```

L'implementazione dell'eliminazione di mesh in RealtimeSurfaceMeshRenderer.cpp:

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

### <a name="acquire-and-use-surface-mesh-data-buffers"></a>Acquisizione e l'uso di buffer di dati di trama della superficie

Recupero delle informazioni di trama della superficie era basta eseguire il pull di una raccolta di dati e l'elaborazione degli aggiornamenti alla raccolta. A questo punto, si passerà in modo dettagliato sul modo in cui è possibile usare i dati.

In questo esempio di codice, abbiamo scelto di usare le reti mesh di surface per il rendering. Si tratta di uno scenario comune per occluding vntana dietro aree del mondo reale. È anche possibile eseguire il rendering mesh o eseguire il rendering elaborate versioni di tali, in modo da visualizzare all'utente informazioni sulle aree di chat room viene eseguita l'analisi prima di iniziare la funzionalità di app o giochi.

Nell'esempio di codice avvia il processo quando riceve gli aggiornamenti di trama della superficie dal gestore dell'evento che è descritti nella sezione precedente. La riga di codice in questa funzione importante è la chiamata per aggiornare l'area *mesh*: a questo punto abbiamo già elaborato le informazioni di rete e si sta tentando di ottenere i dati di vertici e indici per l'uso come si preferisce.

Da RealtimeSurfaceMeshRenderer.cpp:

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

Il codice di esempio è progettato in modo che una classe di dati **SurfaceMesh**, trama di gestione dei dati di elaborazione e rendering. Queste reti sono ciò che il **RealtimeSurfaceMeshRenderer** effettivamente mantiene una mappa di. Ognuno di essi ha un riferimento al SpatialSurfaceMesh da cui proviene e viene usato ogni volta che è necessario accedere ai buffer di vertice o indice la mesh o ottenere una trasformazione per la rete mesh. Per ora, abbiamo flag mesh come da un aggiornamento.

Da SurfaceMesh.cpp:

```cpp
void SurfaceMesh::UpdateSurface(SpatialSurfaceMesh^ surfaceMesh)
{
    m_surfaceMesh = surfaceMesh;
    m_updateNeeded = true;
}
```

La volta successiva che la trama viene chiesto di disegnarsi da solo, il flag verrà verificata prima di tutto. Se è necessario un aggiornamento, i buffer vertici e indici verranno aggiornati nella GPU.

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

In primo luogo, acquisizione di buffer di dati non elaborati:

```cpp
Windows::Storage::Streams::IBuffer^ positions = m_surfaceMesh->VertexPositions->Data;
    Windows::Storage::Streams::IBuffer^ normals   = m_surfaceMesh->VertexNormals->Data;
    Windows::Storage::Streams::IBuffer^ indices   = m_surfaceMesh->TriangleIndices->Data;
```

Quindi, creiamo buffer dispositivo Direct3D con i dati di trama forniti da di HoloLens:

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

**NOTA:** Per la funzione di supporto CreateDirectXBuffer usata nel frammento di codice precedente, vedere l'esempio di codice nell'area di Mapping: SurfaceMesh.cpp, GetDataFromIBuffer.h. A questo punto è stata completata la creazione di risorse del dispositivo e la trama viene considerata per essere caricati e pronti per l'aggiornamento e il rendering.

### <a name="update-and-render-surface-meshes"></a>Aggiornare ed eseguire il rendering mesh surface

La classe SurfaceMesh ha una funzione di aggiornamento specializzate. Ciascuna [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) ha la propria trasformazione e l'esempio Usa il sistema di coordinate per nostro **SpatialStationaryReferenceFrame** per acquisire la trasformazione. Quindi aggiorna il buffer costante del modello nella GPU.

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

Al momento per eseguire il rendering mesh superficie, eseguiamo alcune operazioni di preparazione prima il rendering dell'insieme. Abbiamo configurato la pipeline di shader per la configurazione di rendering corrente, e impostiamo la fase di assemblaggio input. Si noti che la classe helper di fotocamera holographic **CameraResources.cpp** già ha configurato il buffer costante/proiezione vista a questo punto.

Dal **RealtimeSurfaceMeshRenderer::Render**:

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

Al termine, è il ciclo sul nostro mesh e indicare a ognuno di essi di disegnarsi da solo. **NOTA:** Questo codice di esempio non è ottimizzato per l'utilizzo una sorta di cono della faccia posteriore, ma è necessario includere questa funzionalità nell'app.

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

Le singole trame sono responsabili dell'impostazione del buffer di vertici e indici, stride e buffer costante di trasformazione del modello. Come per il cubo rotante nel modello di app Windows Holographic, si esegue il rendering nei buffer stereoscopico utilizzando la creazione di istanze.

Dal **SurfaceMesh::Draw**:

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

### <a name="rendering-choices-with-surface-mapping"></a>Opzioni di rendering con il Mapping di area

Nell'esempio di codice di Mapping nell'area offre il codice per il rendering solo relative all'occlusione di dati di trama della superficie e per il rendering sullo schermo di dati di trama della superficie. Il percorso scelto - o entrambi - dipende dall'applicazione. Si esamineranno entrambe le configurazioni in questo documento.

**Buffer per il rendering occlusione holographic effetto**

Iniziare cancellando la vista di destinazione di rendering per la fotocamera virtuale corrente.

Da AppMain.cpp:

```cpp
context->ClearRenderTargetView(pCameraResources->GetBackBufferRenderTargetView(), DirectX::Colors::Transparent);
```

Si tratta di un passaggio "pre-rendering". In questo caso, creiamo un buffer di occlusione chiedendo il renderer mesh per eseguire il rendering solo profondità. In questa configurazione, si non collega una vista di destinazione di rendering e il programma di rendering mesh imposta la fase pixel shader **nullptr** in modo che la GPU non preoccuparsi di disegnare i pixel. La geometria sarà rasterizzato al buffer di profondità e la pipeline grafica verrà interrotta non esiste.

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

È possibile trarre vntana con un test di profondità con il buffer di relative all'occlusione di Mapping nell'area. Nell'esempio di codice, si esegue il rendering pixel sul cubo un colore diverso se sono protetti da una superficie.

Da AppMain.cpp:

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

Basato su codice da SpecialEffectPixelShader.hlsl:

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

**Nota:** Per i **GatherDepthLess** routine, vedere l'esempio di codice nell'area di Mapping: SpecialEffectPixelShader.hlsl.

**Dati di trama della superficie di rendering sullo schermo**

È anche possibile trarre le reti mesh di surface ai buffer di visualizzazione stereo. È stato scelto di tracciare i volti completi con illuminazione, ma è possibile disegnare wireframe, elaborare mesh prima del rendering, applicare una mappa di trama e così via.

In questo caso, l'esempio di codice indica il renderer mesh per disegnare la raccolta. Questa volta non viene specificato pass solo profondità, in modo che verrà allegare un pixel shader e completare la pipeline di rendering utilizzando le destinazioni che è stata specificata la fotocamera virtuale corrente.

```cpp
// SR mesh rendering pass: Draw SR mesh over the world.
context->ClearDepthStencilView(pCameraResources->GetSurfaceOcclusionDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target to the current holographic camera's back buffer, and set the depth buffer.
ID3D11RenderTargetView *const targets[1] = { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, pCameraResources->GetSurfaceDepthStencilView());

// This drawing pass renders the surface meshes to the stereoscopic display. The user will be
// able to see them while wearing the device.
m_meshCollection->Render(pCameraResources->IsRenderingStereoscopic(), false);
```

## <a name="see-also"></a>Vedere anche
* [Creazione di un progetto di DirectX holographic](creating-a-holographic-directx-project.md)
* [Windows.Perception.Spatial API](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)

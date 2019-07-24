---
title: Sistemi di coordinate in DirectX
description: Spiega come usare i localizzatori spaziali di realtà mista di Windows, i frame di riferimento, gli ancoraggi spaziali e i sistemi di coordinate, come usare SpatialStage, come gestire la perdita di rilevamento, come salvare e caricare ancoraggi e come eseguire la stabilizzazione delle immagini.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Realtà mista, localizzatore spaziale, frame di riferimento spaziale, sistema di coordinate spaziali, fase spaziale, codice di esempio, stabilizzazione dell'immagine, ancoraggio spaziale, archivio di ancoraggio spaziale, perdita di tracce, procedura dettagliata
ms.openlocfilehash: 5a48e0a829ba8647718e28ec20760d8a764b13fe
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65628978"
---
# <a name="coordinate-systems-in-directx"></a>Sistemi di coordinate in DirectX

I [sistemi di coordinate](coordinate-systems.md) costituiscono la base per la comprensione spaziale offerta dalle API per la realtà mista di Windows.

Gli attuali dispositivi VR o Single-Room VR stabiliscono un sistema di coordinate primario per rappresentare lo spazio rilevato. I dispositivi di realtà mista di Windows, ad esempio HoloLens, sono progettati per essere usati in ambienti di grandi dimensioni non definiti, con l'individuazione e l'apprendimento del dispositivo in base all'ambiente in cui l'utente si aggira. Ciò consente al dispositivo di adattarsi a un miglioramento continuo delle informazioni sulle chat dell'utente, ma comporta sistemi di coordinate che cambieranno la relazione tra loro attraverso la durata dell'app. La realtà mista di Windows supporta un'ampia gamma di dispositivi, spaziando da cuffie immersive sedute attraverso frame di riferimento collegati al mondo.

>[!NOTE]
>I frammenti di codice in questo articolo illustrano attualmente l' C++uso di/CX, invece di/WinRT conformi C++a C + 17 come usato nel modello di [ C++ progetto olografico](creating-a-holographic-directx-project.md).  I concetti sono equivalenti per C++un progetto/WinRT, anche se sarà necessario tradurre il codice.

## <a name="spatial-coordinate-systems-in-windows"></a>Sistemi di coordinate spaziali in Windows

Il tipo di base usato per ragionare sui sistemi di coordinate reali in Windows è <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>. Un'istanza di questo tipo rappresenta un sistema di coordinate arbitrario e fornisce un metodo per ottenere una matrice di trasformazione che è possibile utilizzare per trasformare tra due sistemi di coordinate senza comprenderne i dettagli.

I metodi che restituiscono le informazioni spaziali, rappresentate come punti, raggi o volumi nell'ambiente dell'utente, accetteranno un parametro SpatialCoordinateSystem per consentire di decidere il sistema di coordinate in cui è più utile per le coordinate da restituire. Le unità per queste coordinate saranno sempre espresse in metri.

Un SpatialCoordinateSystem ha una relazione dinamica con altri sistemi di coordinate, inclusi quelli che rappresentano la posizione del dispositivo. In qualsiasi momento, il dispositivo potrebbe essere in grado di individuare alcuni sistemi di coordinate e non altri. Per la maggior parte dei sistemi di coordinate, l'app deve essere pronta per gestire i periodi di tempo durante i quali non possono essere individuati.

L'applicazione non deve creare direttamente SpatialCoordinateSystems, bensì deve essere usata tramite le API percettive. Nelle API percettive sono disponibili tre fonti principali di sistemi di coordinate, ciascuna delle quali è mappata a un concetto descritto nella pagina [sistemi di coordinate](coordinate-systems.md) :
* Per ottenere un frame di riferimento fisso, creare un <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference</a> o ottenerne uno dalla <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference</a>corrente.
* Per ottenere un ancoraggio spaziale, creare un <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>.
* Per ottenere un frame di riferimento collegato, creare un <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>.

Tutti i sistemi di coordinate restituiti da questi oggetti vengono gestiti a destra, con + y su, + x a destra e + z all'indietro. È possibile ricordare quale direzione punta l'asse z positivo puntando le dita della parte sinistra o destra nella direzione x positiva e inserendole nella direzione y positiva. La direzione in cui punta il pollice, verso di te o in direzione opposta, è la direzione a cui punta l’asse z positivo per tale sistema di coordinate. La figura seguente mostra questi due sistemi di coordinate.

![Sistemi di coordinate a sinistra e a destra](images/left-hand-right-hand.gif)<br>
*Sistemi di coordinate a sinistra e a destra*

Per eseguire il bootstrap in un SpatialCoordinateSystem in base alla posizione di un HoloLens, usare la classe <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a> per creare un frame di riferimento collegato o fisso, come descritto nelle sezioni riportate di seguito.

## <a name="place-holograms-in-the-world-using-a-spatial-stage"></a>Posizionare gli ologrammi in tutto il mondo usando una fase spaziale

Il sistema di coordinate per gli auricolari a realtà mista di Windows opaco si accede usando la proprietà <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference:: Current</a> statica. Questa API fornisce un sistema di coordinate, informazioni sul fatto che il lettore sia seduto o mobile, il limite di un'area sicura per spostarsi se il lettore è mobile e indica se l'auricolare è direzionale o meno. Per gli aggiornamenti della fase spaziale è inoltre disponibile un gestore eventi.

Prima di tutto, si ottiene la fase spaziale e si sottoscrive la sottoscrizione degli aggiornamenti: 

Codice per l'inizializzazione di una **fase spaziale**

```
SpatialStageManager::SpatialStageManager(
    const std::shared_ptr<DX::DeviceResources>& deviceResources, 
    const std::shared_ptr<SceneController>& sceneController)
    : m_deviceResources(deviceResources), m_sceneController(sceneController)
{
    // Get notified when the stage is updated.
    m_spatialStageChangedEventToken = SpatialStageFrameOfReference::CurrentChanged +=
        ref new EventHandler<Object^>(std::bind(&SpatialStageManager::OnCurrentChanged, this, _1));

    // Make sure to get the current spatial stage.
    OnCurrentChanged(nullptr);
}
```

Nel metodo OnCurrentChanged l'app deve esaminare la fase spaziale e aggiornare di conseguenza l'esperienza del lettore. In questo esempio viene fornita una visualizzazione del limite della fase, nonché la posizione iniziale specificata dall'utente e l'intervallo di visualizzazione e l'intervallo di proprietà dello spostamento della fase. Viene anche eseguito il fallback al nostro sistema di coordinate fisse, quando non è possibile fornire una fase.


Codice per l'aggiornamento di una **fase spaziale**

```
void SpatialStageManager::OnCurrentChanged(Object^ /*o*/)
{
    // The event notifies us that a new stage is available.
    // Get the current stage.
    m_currentStage = SpatialStageFrameOfReference::Current;

    // Clear previous content.
    m_sceneController->ClearSceneObjects();

    if (m_currentStage != nullptr)
    {
        // Obtain stage geometry.
        auto stageCoordinateSystem = m_currentStage->CoordinateSystem;
        auto boundsVertexArray = m_currentStage->TryGetMovementBounds(stageCoordinateSystem);

        // Visualize the area where the user can move around.
        std::vector<float3> boundsVertices;
        boundsVertices.resize(boundsVertexArray->Length);
        memcpy(boundsVertices.data(), boundsVertexArray->Data, boundsVertexArray->Length * sizeof(float3));
        std::vector<unsigned short> indices = TriangulatePoints(boundsVertices);
        m_stageBoundsShape =
            std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(boundsVertices),
                    indices,
                    XMFLOAT3(DirectX::Colors::SeaGreen),
                    stageCoordinateSystem);
        m_sceneController->AddSceneObject(m_stageBoundsShape);

        // In this sample, we draw a visual indicator for some spatial stage properties.
        // If the view is forward-only, the indicator is a half circle pointing forward - otherwise, it
        // is a full circle.
        // If the user can walk around, the indicator is blue. If the user is seated, it is red.

        // The indicator is rendered at the origin - which is where the user declared the center of the
        // stage to be during setup - above the plane of the stage bounds object.
        float3 visibleAreaCenter = float3(0.f, 0.001f, 0.f);

        // Its shape depends on the look direction range.
        std::vector<float3> visibleAreaIndicatorVertices;
        if (m_currentStage->LookDirectionRange == SpatialLookDirectionRange::ForwardOnly)
        {
            // Half circle for forward-only look direction range.
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.25f, 9, XM_PI);
        }
        else
        {
            // Full circle for omnidirectional look direction range.
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.25f, 16, XM_2PI);
        }

        // Its color depends on the movement range.
        XMFLOAT3 visibleAreaColor;
        if (m_currentStage->MovementRange == SpatialMovementRange::NoMovement)
        {
            visibleAreaColor = XMFLOAT3(DirectX::Colors::OrangeRed);
        }
        else
        {
            visibleAreaColor = XMFLOAT3(DirectX::Colors::Aqua);
        }

        std::vector<unsigned short> visibleAreaIndicatorIndices = TriangulatePoints(visibleAreaIndicatorVertices);

        // Visualize the look direction range.
        m_stageVisibleAreaIndicatorShape =
            std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(visibleAreaIndicatorVertices),
                    visibleAreaIndicatorIndices,
                    visibleAreaColor,
                    stageCoordinateSystem);
        m_sceneController->AddSceneObject(m_stageVisibleAreaIndicatorShape);
    }
    else
    {
        // No spatial stage was found.
        // Fall back to a stationary coordinate system.
        auto locator = SpatialLocator::GetDefault();
        if (locator)
        {
            m_stationaryFrameOfReference = locator->CreateStationaryFrameOfReferenceAtCurrentLocation();

            // Render an indicator, so that we know we fell back to a mode without a stage.
            std::vector<float3> visibleAreaIndicatorVertices;
            float3 visibleAreaCenter = float3(0.f, -2.0f, 0.f);
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.125f, 16, XM_2PI);
            std::vector<unsigned short> visibleAreaIndicatorIndices = TriangulatePoints(visibleAreaIndicatorVertices);
            m_stageVisibleAreaIndicatorShape =
                std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(visibleAreaIndicatorVertices),
                    visibleAreaIndicatorIndices,
                    XMFLOAT3(DirectX::Colors::LightSlateGray),
                    m_stationaryFrameOfReference->CoordinateSystem);
            m_sceneController->AddSceneObject(m_stageVisibleAreaIndicatorShape);
        }
    }
}
```

Il set di vertici che definiscono i limiti della fase vengono forniti in ordine orario. La shell di realtà mista di Windows disegna una recinzione al limite quando l'utente lo avvicina; è possibile che si desideri triangularize l'area a cui è possibile passare per i propri scopi. L'algoritmo seguente può essere usato per triangularize la fase.


Codice per la triangolazione della **fase spaziale**

```
std::vector<unsigned short> SpatialStageManager::TriangulatePoints(std::vector<float3> const& vertices)
{
    size_t const& vertexCount = vertices.size();

    // Segments of the shape are removed as they are triangularized.
    std::vector<bool> vertexRemoved;
    vertexRemoved.resize(vertexCount, false);
    unsigned int vertexRemovedCount = 0;

    // Indices are used to define triangles.
    std::vector<unsigned short> indices;

    // Decompose into convex segments.
    unsigned short currentVertex = 0;
    while (vertexRemovedCount < (vertexCount - 2))
    {
        // Get next triangle:
        // Start with the current vertex.
        unsigned short index1 = currentVertex;

        // Get the next available vertex.
        unsigned short index2 = index1 + 1;

        // This cycles to the next available index.
        auto CycleIndex = [=](unsigned short indexToCycle, unsigned short stopIndex)
        {
            // Make sure the index does not exceed bounds.
            if (indexToCycle >= unsigned short(vertexCount))
            {
                indexToCycle -= unsigned short(vertexCount);
            }

            while (vertexRemoved[indexToCycle])
            {
                // If the vertex is removed, go to the next available one.
                ++indexToCycle;

                // Make sure the index does not exceed bounds.
                if (indexToCycle >= unsigned short(vertexCount))
                {
                    indexToCycle -= unsigned short(vertexCount);
                }

                // Prevent cycling all the way around.
                // Should not be needed, as we limit with the vertex count.
                if (indexToCycle == stopIndex)
                {
                    break;
                }
            }

            return indexToCycle;
        };
        index2 = CycleIndex(index2, index1);

        // Get the next available vertex after that.
        unsigned short index3 = index2 + 1;
        index3 = CycleIndex(index3, index1);

        // Vertices that may define a triangle inside the 2D shape.
        auto& v1 = vertices[index1];
        auto& v2 = vertices[index2];
        auto& v3 = vertices[index3];

        // If the projection of the first segment (in clockwise order) onto the second segment is 
        // positive, we know that the clockwise angle is less than 180 degrees, which tells us 
        // that the triangle formed by the two segments is contained within the bounding shape.
        auto v2ToV1 = v1 - v2;
        auto v2ToV3 = v3 - v2;
        float3 normalToV2ToV3 = { -v2ToV3.z, 0.f, v2ToV3.x };
        float projectionOntoNormal = dot(v2ToV1, normalToV2ToV3);
        if (projectionOntoNormal >= 0)
        {
            // Triangle is contained within the 2D shape.

            // Remove peak vertex from the list.
            vertexRemoved[index2] = true;
            ++vertexRemovedCount;

            // Create the triangle.
            indices.push_back(index1);
            indices.push_back(index2);
            indices.push_back(index3);

            // Continue on to the next outer triangle.
            currentVertex = index3;
        }
        else
        {
            // Triangle is a cavity in the 2D shape.
            // The next triangle starts at the inside corner.
            currentVertex = index2;
        }
    }

    indices.shrink_to_fit();
    return indices;
}
```

## <a name="place-holograms-in-the-world-using-a-stationary-frame-of-reference"></a>Posizionare gli ologrammi nel mondo usando un frame di riferimento fisso

La classe [SpatialStationaryFrameOfReference](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialstationaryframeofreference.aspx) rappresenta un frame di riferimento che [rimane](coordinate-systems.md#stationary-frame-of-reference) stazionario rispetto a quello dell'utente quando l'utente si sposta. Questo frame di riferimento assegna priorità a mantenere le coordinate stabili vicino al dispositivo. Un uso chiave di un SpatialStationaryFrameOfReference è fungere da sistema di coordinate globale sottostante all'interno di un motore di rendering durante il rendering degli ologrammi.

Per ottenere un SpatialStationaryFrameOfReference, usare la classe [SpatialLocator](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.aspx) e chiamare [CreateStationaryFrameOfReferenceAtCurrentLocation](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.createstationaryframeofreferenceatcurrentlocation.aspx).

Dal codice del modello di applicazione olografica di Windows:

```
           // The simplest way to render world-locked holograms is to create a stationary reference frame
           // when the app is launched. This is roughly analogous to creating a "world" coordinate system
           // with the origin placed at the device's position as the app is launched.
           referenceFrame = locator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```
* I frame di riferimento stazionari sono progettati per fornire una posizione più adatta rispetto allo spazio complessivo. Le singole posizioni all'interno del frame di riferimento possono essere leggermente derivate. Si tratta di una situazione normale quando il dispositivo apprende altre informazioni sull'ambiente.
* Quando è richiesto un posizionamento preciso dei singoli ologrammi, è consigliabile usare un SpatialAnchor per ancorare il singolo ologramma a una posizione nel mondo reale, ad esempio un punto che l'utente indica di essere di particolare interesse. Le posizioni di ancoraggio non sono derivate, ma possono essere corrette; l'ancoraggio utilizzerà la posizione corretta a partire dal fotogramma successivo dopo che è stata eseguita la correzione.

## <a name="place-holograms-in-the-world-using-spatial-anchors"></a>Posizionare gli ologrammi in tutto il mondo usando ancoraggi spaziali

Gli [ancoraggi spaziali](coordinate-systems.md#spatial-anchors) sono un ottimo modo per collocare gli ologrammi in una posizione specifica nel mondo reale, con il sistema che garantisce che l'ancoraggio rimanga in vigore nel tempo. In questo argomento viene illustrato come creare e utilizzare un ancoraggio e come utilizzare i dati di ancoraggio.

È possibile creare un SpatialAnchor in qualsiasi posizione e orientamento all'interno della SpatialCoordinateSystem scelta. Il dispositivo deve essere in grado di individuare il sistema di coordinate al momento e il sistema non deve avere raggiunto il limite di ancoraggi spaziali.

Una volta definito, il sistema di coordinate di un SpatialAnchor si adatta continuamente per mantenere la posizione e l'orientamento precisi della posizione iniziale. È quindi possibile usare questo SpatialAnchor per eseguire il rendering degli ologrammi che appariranno corretti negli ambienti dell'utente nella posizione esatta.

Gli effetti delle rettifiche che mantengono l'ancoraggio sul posto vengono ingranditi come distanza dall'ancoraggio. Pertanto, è consigliabile evitare di eseguire il rendering del contenuto relativo a un ancoraggio maggiore di circa 3 metri dall'origine dell'ancoraggio.

La proprietà [CoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.coordinatesystem.aspx) ottiene un sistema di coordinate che consente di posizionare il contenuto relativo all'ancoraggio, con l'interpolazione applicata quando il dispositivo regola la posizione esatta dell'ancoraggio.

Utilizzare la proprietà [RawCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystem.aspx) e l'evento [RawCoordinateSystemAdjusted](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted.aspx) corrispondente per gestire manualmente queste modifiche.

### <a name="persist-and-share-spatial-anchors"></a>Mantieni e Condividi ancoraggi spaziali

È possibile salvare in locale una SpatialAnchor usando la classe [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx) e quindi riportarla in una sessione di app futura nello stesso dispositivo HoloLens.

Usando gli <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">ancoraggi spaziali di Azure</a>, è possibile creare un ancoraggio cloud durevole da un SpatialAnchor locale, che può essere individuato dall'app su più dispositivi HoloLens, iOS e Android.  Condividendo un ancoraggio spaziale comune tra più dispositivi, ogni utente può visualizzare il contenuto di cui è stato eseguito il rendering relativo a tale ancoraggio nella stessa posizione fisica.  Ciò rende possibili esperienze condivise in tempo reale.

Puoi usare <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Ancoraggi nello spazio di Azure</a> anche per la persistenza asincrona degli ologrammi su dispositivi HoloLens, iOS e Android.  Condividendo un ancoraggio durevole nello spazio del cloud, più dispositivi possono osservare nel tempo lo stesso ologramma salvato in modo permanente, anche se tali dispositivi non sono presenti insieme contemporaneamente.

Per iniziare a creare esperienze condivise nell'app HoloLens, provare la <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Guida introduttiva di Azure Spatial Anchors HoloLens</a>di 5 minuti.

Una volta che si è in esecuzione con gli ancoraggi spaziali di Azure, è possibile <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">creare e individuare ancoraggi in HoloLens</a>.  Le procedure dettagliate sono disponibili anche per <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android e iOS</a> , consentendo di condividere gli stessi ancoraggi in tutti i dispositivi.

### <a name="create-spatialanchors-for-holographic-content"></a>Crea SpatialAnchors per contenuto olografico

Per questo esempio di codice, il modello di applicazione Windows olografico è stato modificato per creare ancoraggi quando viene rilevato il movimento **premuto** . Il cubo viene quindi inserito in corrispondenza dell'ancoraggio durante il passaggio di rendering.

Poiché più ancoraggi sono supportati dalla classe helper, è possibile inserire tutti i cubi desiderati usando questo esempio di codice.

Si noti che gli ID per gli ancoraggi sono elementi che è possibile controllare nell'app. In questo esempio è stato creato uno schema di denominazione sequenziale in base al numero di ancoraggi attualmente archiviati nella raccolta di ancoraggi dell'app.

```
   // Check for new input state since the last frame.
   SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   if (pointerState != nullptr)
   {
       // Try to get the pointer pose relative to the SpatialStationaryReferenceFrame.
       SpatialPointerPose^ pointerPose = pointerState->TryGetPointerPose(currentCoordinateSystem);
       if (pointerPose != nullptr)
       {
           // When a Pressed gesture is detected, the anchor will be created two meters in front of the user.

           // Get the gaze direction relative to the given coordinate system.
           const float3 headPosition = pointerPose->Head->Position;
           const float3 headDirection = pointerPose->Head->ForwardDirection;

           // The anchor position in the StationaryReferenceFrame.
           static const float distanceFromUser = 2.0f; // meters
           const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * headDirection);

           // Create the anchor at position.
           SpatialAnchor^ anchor = SpatialAnchor::TryCreateRelativeTo(currentCoordinateSystem, gazeAtTwoMeters);

           if ((anchor != nullptr) && (m_spatialAnchorHelper != nullptr))
           {
               // In this example, we store the anchor in an IMap.
               auto anchorMap = m_spatialAnchorHelper->GetAnchorMap();

               // Create an identifier for the anchor.
               String^ id = ref new String(L"HolographicSpatialAnchorStoreSample_Anchor") + anchorMap->Size;

               anchorMap->Insert(id->ToString(), anchor);
           }
       }
   }
```

### <a name="asynchronously-load-and-cache-the-spatialanchorstore"></a>Caricare e memorizzare nella cache in modo asincrono SpatialAnchorStore

Viene ora illustrato come scrivere una classe SampleSpatialAnchorHelper che consente di gestire questa persistenza, tra cui:
* Archiviazione di una raccolta di ancoraggi in memoria, indicizzati da una chiave Platform:: String.
* Caricamento di ancoraggi dal SpatialAnchorStore del sistema, mantenuto separato dalla raccolta locale in memoria.
* Salvataggio della raccolta in memoria locale degli ancoraggi in SpatialAnchorStore quando l'app sceglie di eseguire questa operazione.

Di seguito viene illustrato come salvare gli oggetti [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) in [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).

Quando la classe viene avviata, viene richiesto il SpatialAnchorStore in modo asincrono. Ciò implica l'I/O di sistema, perché l'API carica l'archivio di ancoraggio e questa API viene resa asincrona in modo che l'I/O non sia bloccante.

```
   // Request the spatial anchor store, which is the WinRT object that will accept the imported anchor data.
   return create_task(SpatialAnchorManager::RequestStoreAsync())
       .then([](task<SpatialAnchorStore^> previousTask)
   {
       std::shared_ptr<SampleSpatialAnchorHelper> newHelper = nullptr;

       try
       {
           SpatialAnchorStore^ anchorStore = previousTask.get();

           // Once the SpatialAnchorStore has been loaded by the system, we can create our helper class.

           // Using "new" to access private constructor
           newHelper = std::shared_ptr<SampleSpatialAnchorHelper>(new SampleSpatialAnchorHelper(anchorStore));

           // Now we can load anchors from the store.
           newHelper->LoadFromAnchorStore();
       }
       catch (Exception^ exception)
       {
           PrintWstringToDebugConsole(
               std::wstring(L"Exception while loading the anchor store: ") +
               exception->Message->Data() +
               L"\n"
               );
       }

       // Return the initialized class instance.
       return newHelper;
   });
```

Verrà fornito un SpatialAnchorStore che è possibile usare per salvare gli ancoraggi. Si tratta di un IMapView che associa i valori di chiave che sono stringhe, con valori di dati SpatialAnchors. Nel codice di esempio, viene archiviato in una variabile membro della classe privata accessibile tramite una funzione pubblica della classe helper.

```
   SampleSpatialAnchorHelper::SampleSpatialAnchorHelper(SpatialAnchorStore^ anchorStore)
   {
       m_anchorStore = anchorStore;
       m_anchorMap = ref new Platform::Collections::Map<String^, SpatialAnchor^>();
   }
```

>[!NOTE]
>Non dimenticare di associare gli eventi di sospensione/ripresa per salvare e caricare l'archivio di ancoraggio.

```
   void HolographicSpatialAnchorStoreSampleMain::SaveAppState()
   {
       // For example, store information in the SpatialAnchorStore.
       if (m_spatialAnchorHelper != nullptr)
       {
           m_spatialAnchorHelper->TrySaveToAnchorStore();
       }
   }
```

```
   void HolographicSpatialAnchorStoreSampleMain::LoadAppState()
   {
       // For example, load information from the SpatialAnchorStore.
       LoadAnchorStore();
   }
```

### <a name="save-content-to-the-anchor-store"></a>Salva contenuto nell'archivio di ancoraggio

Quando il sistema sospende l'app, è necessario salvare gli ancoraggi spaziali nell'archivio di ancoraggio. È anche possibile scegliere di salvare gli ancoraggi nell'archivio di ancoraggio in altri momenti, perché si ritiene che siano necessari per l'implementazione dell'app.

Quando si è pronti per provare a salvare gli ancoraggi in memoria in SpatialAnchorStore, è possibile eseguire il ciclo della raccolta e provare a salvarli.

```
   // TrySaveToAnchorStore: Stores all anchors from memory into the app's anchor store.
   //
   // For each anchor in memory, this function tries to store it in the app's AnchorStore. The operation will fail if
   // the anchor store already has an anchor by that name.
   //
   bool SampleSpatialAnchorHelper::TrySaveToAnchorStore()
   {
       // This function returns true if all the anchors in the in-memory collection are saved to the anchor
       // store. If zero anchors are in the in-memory collection, we will still return true because the
       // condition has been met.
       bool success = true;

       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           for each (auto& pair in m_anchorMap)
           {
               auto const& id = pair->Key;
               auto const& anchor = pair->Value;

               // Try to save the anchors.
               if (!m_anchorStore->TrySave(id, anchor))
               {
                   // This may indicate the anchor ID is taken, or the anchor limit is reached for the app.
                   success=false;
               }
           }
       }

       return success;
   }
```

### <a name="load-content-from-the-anchor-store-when-the-app-resumes"></a>Carica il contenuto dall'archivio di ancoraggio quando l'app riprende

Quando l'app riprende o in qualsiasi altro momento necessario per il implementaiton dell'app, è possibile ripristinare gli ancoraggi salvati in precedenza nel AnchorStore trasferendo i file dal IMapView dell'archivio di ancoraggio nel database in memoria di SpatialAnchors.

Per ripristinare gli ancoraggi dal SpatialAnchorStore, ripristinare ognuno di essi interessato alla raccolta in memoria.

È necessario un database in memoria personalizzato di SpatialAnchors; un modo per associare le stringhe al SpatialAnchors creato. Nel codice di esempio si sceglie di usare Windows:: Foundation:: Collections:: IMap per archiviare gli ancoraggi, che semplifica l'uso della stessa chiave e del valore di dati per SpatialAnchorStore.

```
   // This is an in-memory anchor list that is separate from the anchor store.
   // These anchors may be used, reasoned about, and so on before committing the collection to the store.
   Windows::Foundation::Collections::IMap<Platform::String^, Windows::Perception::Spatial::SpatialAnchor^>^ m_anchorMap;
```

>[!NOTE]
>Un ancoraggio ripristinato potrebbe non essere locatable immediatamente. Ad esempio, potrebbe trattarsi di un ancoraggio in una stanza separata o in una compilazione diversa. Gli ancoraggi recuperati da AnchorStore devono essere testati per locatability prima di usarli.

<br>

>[!NOTE]
>In questo esempio di codice, vengono recuperati tutti gli ancoraggi da AnchorStore. Questo non è un requisito; l'app potrebbe anche selezionare e scegliere un certo subset di ancoraggi usando valori di chiave di stringa significativi per l'implementazione.

```
   // LoadFromAnchorStore: Loads all anchors from the app's anchor store into memory.
   //
   // The anchors are stored in memory using an IMap, which stores anchors using a string identifier. Any string can be used as
   // the identifier; it can have meaning to the app, such as "Game_Leve1_CouchAnchor," or it can be a GUID that is generated
   // by the app.
   //
   void SampleSpatialAnchorHelper::LoadFromAnchorStore()
   {
       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           // Get all saved anchors.
           auto anchorMapView = m_anchorStore->GetAllSavedAnchors();
           for each (auto const& pair in anchorMapView)
           {
               auto const& id = pair->Key;
               auto const& anchor = pair->Value;
               m_anchorMap->Insert(id, anchor);
           }
       }
   }
```

### <a name="clear-the-anchor-store-when-needed"></a>Cancellare l'archivio di ancoraggio, quando necessario

In alcuni casi è necessario cancellare lo stato dell'app e scrivere nuovi dati. Ecco come si esegue questa operazione con [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).

Con la classe helper è quasi inutile eseguire il wrapping della funzione Clear. Si sceglie di eseguire questa operazione nell'implementazione di esempio, perché la classe helper è responsabile del proprietario dell'istanza di SpatialAnchorStore.

```
   // ClearAnchorStore: Clears the AnchorStore for the app.
   //
   // This function clears the AnchorStore. It has no effect on the anchors stored in memory.
   //
   void SampleSpatialAnchorHelper::ClearAnchorStore()
   {
       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           // Clear all anchors from the store.
           m_anchorStore->Clear();
       }
   }
```

### <a name="example-relating-anchor-coordinate-systems-to-stationary-reference-frame-coordinate-systems"></a>Esempio: Correlazione dei sistemi di coordinate di ancoraggio ai sistemi di coordinate dei frame di riferimento stazionari

Supponiamo di avere un ancoraggio e di voler mettere in relazione un elemento del sistema di coordinate dell'ancoraggio alla SpatialStationaryReferenceFrame che si sta già usando per la maggior parte degli altri contenuti. È possibile usare [TryGetTransformTo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.trygettransformto.aspx) per ottenere una trasformazione dal sistema di coordinate dell'ancoraggio a quello del frame di riferimento fisso:

```
   // In this code snippet, someAnchor is a SpatialAnchor^ that has been initialized and is valid in the current environment.
   float4x4 anchorSpaceToCurrentCoordinateSystem;
   SpatialCoordinateSystem^ anchorSpace = someAnchor->CoordinateSystem;
   const auto tryTransform = anchorSpace->TryGetTransformTo(currentCoordinateSystem);
   if (tryTransform != nullptr)
   {
       anchorSpaceToCurrentCoordinateSystem = tryTransform->Value;
   }
```

Questo processo è utile in due modi:
1. Indica se i due frame di riferimento possono essere compresi tra loro e;
2. In tal caso, viene fornita una trasformazione per passare direttamente da un sistema di coordinate all'altro.

Con queste informazioni, è possibile comprendere la relazione spaziale tra gli oggetti tra i due frame di riferimento.

Per il rendering, è spesso possibile ottenere risultati migliori raggruppando gli oggetti in base al frame di riferimento originale o all'ancoraggio. Eseguire un passaggio di disegno separato per ogni gruppo. Le matrici di visualizzazione sono più accurate per gli oggetti con trasformazioni del modello create inizialmente con lo stesso sistema di coordinate.

## <a name="create-holograms-using-a-device-attached-frame-of-reference"></a>Creare ologrammi usando un frame di riferimento collegato al dispositivo

In alcuni casi si desidera eseguire il rendering di un ologramma che [rimane collegato](coordinate-systems.md#attached-frame-of-reference) alla posizione del dispositivo, ad esempio un pannello con informazioni di debug o un messaggio informativo quando il dispositivo è in grado di determinare solo l'orientamento e non la posizione in spazio. A tale scopo, viene usato un frame di riferimento allegato.

La classe SpatialLocatorAttachedFrameOfReference definisce i sistemi di coordinate relativi al dispositivo anziché al mondo reale. Questo frame dispone di un'intestazione fissa rispetto all'area circostante dell'utente che punta alla posizione in cui l'utente si trovava al momento della creazione del frame di riferimento. Da questo punto in poi, tutti gli orientamenti in questo frame di riferimento sono relativi a tale intestazione fissa, anche quando l'utente ruota il dispositivo.

Per HoloLens, l'origine del sistema di coordinate del frame si trova al centro della rotazione della testa dell'utente, in modo che la relativa posizione non sia interessata dalla rotazione della testa. L'app può specificare un offset rispetto a questo punto per posizionare gli ologrammi davanti all'utente.

Per ottenere un SpatialLocatorAttachedFrameOfReference, usare la classe SpatialLocator e chiamare CreateAttachedFrameOfReferenceAtCurrentHeading.

Si noti che questo vale per l'intero intervallo di dispositivi di realtà mista di Windows.

### <a name="use-a-reference-frame-attached-to-the-device"></a>Usare un frame di riferimento collegato al dispositivo

In queste sezioni vengono illustrate le modifiche apportate al modello di app olografico di Windows per abilitare un frame di riferimento collegato al dispositivo tramite questa API. Si noti che questo ologramma "collegato" funziona insieme a ologrammi fissi o ancorati e può essere usato anche quando il dispositivo non è temporaneamente in grado di trovare la propria posizione nel mondo.

In primo luogo, il modello è stato modificato per archiviare un SpatialLocatorAttachedFrameOfReference anziché un SpatialStationaryFrameOfReference:

Da **HolographicTagAlongSampleMain. h**:

```
   // A reference frame attached to the holographic camera.
   Windows::Perception::Spatial::SpatialLocatorAttachedFrameOfReference^   m_referenceFrame;
```

Da **HolographicTagAlongSampleMain. cpp**:

```
   // In this example, we create a reference frame attached to the device.
   m_referenceFrame = m_locator->CreateAttachedFrameOfReferenceAtCurrentHeading();
```

Durante l'aggiornamento, viene ora ottenuto il sistema di coordinate al timestamp ottenuto da con la stima del frame.

```
   // Next, we get a coordinate system from the attached frame of reference that is
   // associated with the current frame. Later, this coordinate system is used for
   // for creating the stereo view matrices when rendering the sample content.
   SpatialCoordinateSystem^ currentCoordinateSystem =
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp);
```

### <a name="get-a-spatial-pointer-pose-and-follow-the-users-gaze"></a>Ottenere un indicatore di misura spaziale e seguire lo sguardo dell'utente

Si vuole che l'ologramma di esempio segua lo [sguardo](gaze.md)dell'utente, in modo analogo a come la shell olografica può seguire lo sguardo dell'utente. A questo punto, è necessario ottenere il SpatialPointerPose dallo stesso timestamp.

```
SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
```

Questo SpatialPointerPose contiene le informazioni necessarie per posizionare l'ologramma in base all' [intestazione corrente dell'utente](gaze-in-directx.md).

Per motivi di comodità dell'utente, viene usata l'interpolazione lineare ("Lerp") per smussare la modifica nella posizione in modo tale che si verifichi in un determinato periodo di tempo. Si tratta di un'operazione più comoda per l'utente rispetto al blocco degli ologrammi. Lerping la posizione dell'ologramma tag-along consente anche di stabilizzare l'ologramma smorzando il movimento; Se questa operazione non è stata eseguita, l'utente vedrà la jitter dell'ologramma a causa di ciò che in genere è considerato un movimento impercettibile della testa dell'utente.

Da **StationaryQuadRenderer::P ositionhologram**:

```
   const float& dtime = static_cast<float>(timer.GetElapsedSeconds());

   if (pointerPose != nullptr)
   {
       // Get the gaze direction relative to the given coordinate system.
       const float3 headPosition  = pointerPose->Head->Position;
       const float3 headDirection = pointerPose->Head->ForwardDirection;

       // The tag-along hologram follows a point 2.0m in front of the user's gaze direction.
       static const float distanceFromUser = 2.0f; // meters
       const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * headDirection);

       // Lerp the position, to keep the hologram comfortably stable.
       auto lerpedPosition = lerp(m_position, gazeAtTwoMeters, dtime * c_lerpRate);

       // This will be used as the translation component of the hologram's
       // model transform.
       SetPosition(lerpedPosition);
   }
```

>[!NOTE]
>Nel caso di un pannello di debug, è possibile scegliere di riposizionare l'ologramma sul lato leggermente, in modo che non ostacoli la visualizzazione. Ecco un esempio di come è possibile eseguire questa operazione.

Per **StationaryQuadRenderer::P ositionhologram**:

```
       // If you're making a debug view, you might not want the tag-along to be directly in the
       // center of your field of view. Use this code to position the hologram to the right of
       // the user's gaze direction.
       /*
       const float3 offset = float3(0.13f, 0.0f, 0.f);
       static const float distanceFromUser = 2.2f; // meters
       const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * (headDirection + offset));
       */
```

### <a name="rotate-the-hologram-to-face-the-camera"></a>Ruotare l'ologramma per far fronte alla fotocamera

Non è sufficiente posizionare semplicemente l'ologramma, che in questo caso è un quad; è anche necessario ruotare l'oggetto per far fronte all'utente. Si noti che questa rotazione si verifica nello spazio globale, perché questo tipo di tabellone consente all'ologramma di rimanere parte dell'ambiente dell'utente. Il tabellone degli spazi di visualizzazione non è altrettanto comodo perché l'ologramma viene bloccato sull'orientamento della visualizzazione. in tal caso, è anche necessario interpolare tra le matrici di visualizzazione a sinistra e a destra per acquisire una trasformazione di Billboard dello spazio di visualizzazione che non interrompa il rendering stereo. In questo caso, gli assi X e Z vengono ruotati in modo da far fronte all'utente.

Da **StationaryQuadRenderer:: Update**:

```
   // Seconds elapsed since previous frame.
   const float& dTime = static_cast<float>(timer.GetElapsedSeconds());

   // Create a direction normal from the hologram's position to the origin of person space.
   // This is the z-axis rotation.
   XMVECTOR facingNormal = XMVector3Normalize(-XMLoadFloat3(&m_position));

   // Rotate the x-axis around the y-axis.
   // This is a 90-degree angle from the normal, in the xz-plane.
   // This is the x-axis rotation.
   XMVECTOR xAxisRotation = XMVector3Normalize(XMVectorSet(XMVectorGetZ(facingNormal), 0.f, -XMVectorGetX(facingNormal), 0.f));

   // Create a third normal to satisfy the conditions of a rotation matrix.
   // The cross product  of the other two normals is at a 90-degree angle to
   // both normals. (Normalize the cross product to avoid floating-point math
   // errors.)
   // Note how the cross product will never be a zero-matrix because the two normals
   // are always at a 90-degree angle from one another.
   XMVECTOR yAxisRotation = XMVector3Normalize(XMVector3Cross(facingNormal, xAxisRotation));

   // Construct the 4x4 rotation matrix.

   // Rotate the quad to face the user.
   XMMATRIX rotationMatrix = XMMATRIX(
       xAxisRotation,
       yAxisRotation,
       facingNormal,
       XMVectorSet(0.f, 0.f, 0.f, 1.f)
       );

   // Position the quad.
   const XMMATRIX modelTranslation = XMMatrixTranslationFromVector(XMLoadFloat3(&m_position));

   // The view and projection matrices are provided by the system; they are associated
   // with holographic cameras, and updated on a per-camera basis.
   // Here, we provide the model transform for the sample hologram. The model transform
   // matrix is transposed to prepare it for the shader.
   XMStoreFloat4x4(&m_modelConstantBufferData.model, XMMatrixTranspose(rotationMatrix * modelTranslation));
```

### <a name="render-the-attached-hologram"></a>Eseguire il rendering dell'ologramma collegato

Per questo esempio, si sceglie anche di eseguire il rendering dell'ologramma nel sistema di coordinate del SpatialLocatorAttachedReferenceFrame, che è il punto in cui è stato posizionato l'ologramma. (Se si è deciso di eseguire il rendering usando un altro sistema di coordinate, è necessario acquisire una trasformazione dal sistema di coordinate del frame di riferimento collegato al dispositivo a tale sistema di coordinate).

Da **HolographicTagAlongSampleMain:: Render**:

```
   // The view and projection matrices for each holographic camera will change
   // every frame. This function refreshes the data in the constant buffer for
   // the holographic camera indicated by cameraPose.
   pCameraResources->UpdateViewProjectionBuffer(
       m_deviceResources,
       cameraPose,
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp)
       );
```

La procedura è terminata. L'ologramma ora "inseguisce" una posizione che è di 2 metri davanti alla direzione dello sguardo dell'utente.

>[!NOTE]
>Questo esempio carica anche contenuto aggiuntivo. vedere StationaryQuadRenderer. cpp.

## <a name="handling-tracking-loss"></a>Gestione della perdita di rilevamento

Quando il dispositivo non è in grado di trovarsi nel mondo, l'app riscontra una "perdita di rilevamento". Le app per la realtà mista di Windows dovrebbero essere in grado di gestire tali rotture per il sistema di rilevamento posizionale. Queste rotture possono essere osservate e le risposte create usando l'evento LocatabilityChanged sul SpatialLocator predefinito.

Da **AppMain:: SetHolographicSpace:**

```
   // Be able to respond to changes in the positional tracking state.
   m_locatabilityChangedToken =
       m_locator->LocatabilityChanged +=
           ref new Windows::Foundation::TypedEventHandler<SpatialLocator^, Object^>(
               std::bind(&HolographicApp1Main::OnLocatabilityChanged, this, _1, _2)
               );
```

Quando l'app riceve un evento LocatabilityChanged, può modificare il comportamento in base alle esigenze. Ad esempio, nello stato PositionalTrackingInhibited, l'app può sospendere l'operazione normale ed eseguire il rendering di un ologramma con [tag lungo](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) che visualizza un messaggio di avviso.

Il modello di app olografico di Windows viene creato con un gestore LocatabilityChanged già creato automaticamente. Per impostazione predefinita, viene visualizzato un avviso nella console di debug quando il rilevamento posizionale non è disponibile. È possibile aggiungere codice a questo gestore per fornire una risposta in base alle esigenze dell'app.

Da **AppMain. cpp:**

```
   void HolographicApp1Main::OnLocatabilityChanged(SpatialLocator^ sender, Object^ args)
   {
       switch (sender->Locatability)
       {
       case SpatialLocatability::Unavailable:
           // Holograms cannot be rendered.
           {
               String^ message = L"Warning! Positional tracking is " +
                                           sender->Locatability.ToString() + L".\n";
               OutputDebugStringW(message->Data());
           }
           break;

       // In the following three cases, it is still possible to place holograms using a
       // SpatialLocatorAttachedFrameOfReference.
       case SpatialLocatability::PositionalTrackingActivating:
           // The system is preparing to use positional tracking.

       case SpatialLocatability::OrientationOnly:
           // Positional tracking has not been activated.

       case SpatialLocatability::PositionalTrackingInhibited:
           // Positional tracking is temporarily inhibited. User action may be required
           // in order to restore positional tracking.
           break;

       case SpatialLocatability::PositionalTrackingActive:
           // Positional tracking is active. World-locked content can be rendered.
           break;
       }
   }
```

## <a name="spatial-mapping"></a>Mapping spaziale

Le API di [mapping spaziale](spatial-mapping-in-directx.md) utilizzano i sistemi di coordinate per ottenere le trasformazioni del modello per le mesh di superficie.

## <a name="see-also"></a>Vedere anche
* [Sistemi di coordinate](coordinate-systems.md)
* [Ancoraggi nello spazio](spatial-anchors.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Ancoraggi nello spazio di Azure</a>
* [Puntamento con la testa e sguardo fisso in DirectX](gaze-in-directx.md)
* [Mani e controller del movimento in DirectX](hands-and-motion-controllers-in-directx.md)
* [Mapping spaziale in DirectX](spatial-mapping-in-directx.md)

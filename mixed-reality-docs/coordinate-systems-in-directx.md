---
title: Sistemi di coordinate in DirectX
description: Viene illustrato come usare i localizzatori spaziali di realtà mista di Windows, frame di riferimento, gli ancoraggi spaziali e i sistemi di coordinate, come usare il SpatialStage, come gestire la perdita di rilevamento, come salvare e caricare gli ancoraggi e procedura per creare l'immagine di stabilizzazione.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Mista realtà, indicatore di posizione spaziale, frame di riferimento spaziale, spaziale sistema di coordinate, fase spaziali, esempio codice, stabilizzazione immagine, ancoraggio spaziale, spaziali store di ancoraggio, rilevamento perdite, procedura dettagliata
ms.openlocfilehash: 5a48e0a829ba8647718e28ec20760d8a764b13fe
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65628978"
---
# <a name="coordinate-systems-in-directx"></a>Sistemi di coordinate in DirectX

[Sistemi di coordinate](coordinate-systems.md) costituiscono la base per informazioni sulle spaziali offerti dalle API di realtà mista di Windows.

Oggi seduto VR o dispositivi VR singolo spazio stabilire un sistema di coordinate primario per rappresentare il relativo spazio rilevata. Dispositivi per realtà mista di Windows come HoloLens sono progettati per essere usate in ambienti di grandi dimensioni non definiti, con il dispositivo rilevando e apprendere i concetti relativi adatto al contesto dell'utente camminare. In questo modo il dispositivo per adattarsi a migliorare continuamente una conoscenza dell'utente locali, i risultati in sistemi di coordinate che modificheranno le relazioni tra loro ciclo di vita dell'app. Realtà mista di Windows supporta un'ampia gamma di dispositivi, compreso fra seduti auricolari coinvolgenti e frame di riferimento collegati al mondo.

>[!NOTE]
>I frammenti di codice in questo articolo illustrano attualmente l'utilizzo di C++/CX invece di C + + 17 conformi C++/WinRT usato nel [ C++ modello di progetto holographic](creating-a-holographic-directx-project.md).  I concetti sono equivalenti per un C++progetto /WinRT, anche se è necessario convertire il codice.

## <a name="spatial-coordinate-systems-in-windows"></a>Sistemi di coordinate spaziali in Windows

Il tipo di base utilizzato per prendere in considerazione i sistemi di coordinate reali in Windows è il <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>. Un'istanza di questo tipo rappresenta un sistema di coordinate arbitrario e fornisce un metodo per ottenere una matrice di trasformazione che è possibile usare per eseguire una conversione tra due sistemi di coordinate senza conoscere i dettagli della ognuno.

I metodi che restituiscono informazioni spaziali, rappresentate come punti, rays o volumi nell'ambiente circostante dell'utente, accetterà un parametro SpatialCoordinateSystem per decidere il sistema di coordinate in cui è particolarmente utile per le coordinate da restituire. Le unità per tali coordinate sarà sempre in metri.

Un SpatialCoordinateSystem ha una relazione dinamica con altri sistemi di coordinate, incluse quelle che rappresentano la posizione del dispositivo. In qualsiasi momento, il dispositivo potrebbe essere in grado di individuare alcuni sistemi di coordinate e non altri. Per la maggior parte dei sistemi di coordinate, l'app deve essere pronta a gestire i periodi di tempo durante il quale non è possibile individuare.

L'applicazione non deve essere creato direttamente SpatialCoordinateSystems - piuttosto devono essere usati tramite le API di percezione. Sono disponibili tre fonti principali di sistemi di coordinate nelle API di percezione, ognuna delle quali mappa a un concetto descritto nel [sistemi di Coordinate](coordinate-systems.md) pagina:
* Per ottenere un frame di riferimento fisso, creare un <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference</a> oppure ottenerne uno da corrente <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference</a>.
* Per ottenere un punto di ancoraggio spaziale, creare un <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>.
* Per ottenere un frame di riferimento collegati, creare un <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>.

Tutti i sistemi di coordinate restituiti da questi oggetti sono da destra, con + y, + x a destra e + z con le versioni precedenti. È possibile ricordare direzione in cui i punti di positivi dell'asse z verso le dita di sinistra o a destra nella direzione x positivo e a usare CURL li nella direzione y positivo. La direzione in cui punta il pollice, verso di te o in direzione opposta, è la direzione a cui punta l’asse z positivo per tale sistema di coordinate. La figura seguente mostra questi due sistemi di coordinate.

![Sistemi di coordinate a sinistra e destra](images/left-hand-right-hand.gif)<br>
*Sistemi di coordinate a sinistra e destra*

Per eseguire il bootstrap in un SpatialCoordinateSystem basato sulla posizione di un HoloLens, usare il <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a> classe per creare entrambi un allegato o fermo fotogramma di riferimento, come descritto nelle sezioni seguenti.

## <a name="place-holograms-in-the-world-using-a-spatial-stage"></a>Ologrammi luogo nel mondo usando una fase spaziale

Il sistema di coordinate per opachi auricolari coinvolgenti di realtà mista di Windows è accessibile tramite il metodo statico <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference::Current</a> proprietà. Questa API fornisce un sistema di coordinate, informazioni su se il lettore viene inserito o per dispositivi mobili, il limite di una zona di sicurezza per l'analisi di tutto se il giocatore è mobile e un'indicazione o meno le cuffie direzionale. È inoltre disponibile un gestore eventi per gli aggiornamenti alla fase spaziale.

Prima di tutto è ottenere la fase spaziale e la sottoscrizione per gli aggiornamenti: 

Il codice per **inizializzazione fase spaziali**

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

Nel metodo OnCurrentChanged, l'app deve controllare la fase spaziale e aggiornare di conseguenza l'esperienza dei giocatori. In questo esempio, viene fornita una visualizzazione del limite di fase, nonché la posizione iniziale specificata dall'utente e intervallo della fase di visualizzazione e l'intervallo di proprietà di spostamento. È anche eseguire il fallback al nostro sistema di coordinate stazionario, quando una fase non può essere fornita.


Il codice per **update fase spaziali**

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

Il set di vertici che definiscono il limite di fase vengono forniti in senso antiorario. La shell di realtà mista di Windows consente di disegnare un limite in corrispondenza del limite quando l'utente si avvicina a esso. è consigliabile triangularize l'area è percorribile per le proprie esigenze. L'algoritmo seguente utilizzabile per triangularize della fase.


Il codice per **triangularization fase spaziali**

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

## <a name="place-holograms-in-the-world-using-a-stationary-frame-of-reference"></a>Ologrammi luogo nel mondo usando un frame di riferimento fisso

Il [SpatialStationaryFrameOfReference](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialstationaryframeofreference.aspx) classe rappresenta un frame di fare riferimento a tale [rimane stazionario](coordinate-systems.md#stationary-frame-of-reference) rispetto all'ambiente circostante dell'utente come utente non si sposta. Questo fa riferimento a assegna la priorità alle coordinate mantenere stabili in prossimità del dispositivo. Uno degli utilizzi principali di un SpatialStationaryFrameOfReference deve agire come sistema di coordinate world sottostante all'interno di un motore di rendering per il rendering vntana.

Per ottenere un SpatialStationaryFrameOfReference, usare il [SpatialLocator](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.aspx) classe e chiamare [CreateStationaryFrameOfReferenceAtCurrentLocation](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.createstationaryframeofreferenceatcurrentlocation.aspx).

Dal codice del modello di app Windows Holographic:

```
           // The simplest way to render world-locked holograms is to create a stationary reference frame
           // when the app is launched. This is roughly analogous to creating a "world" coordinate system
           // with the origin placed at the device's position as the app is launched.
           referenceFrame = locator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```
* I frame di riferimento fisso sono progettati per fornire una posizione ottimale rispetto al spazio complessivo. Le singole posizioni all'interno di quel frame di riferimento sono consentite per deviare leggermente. Questo è normale, poiché il dispositivo viene a conoscenza delle informazioni sull'ambiente.
* Quando viene richiesto il posizionamento preciso degli vntana singoli, una SpatialAnchor deve essere usato per ancorare l'ologrammi singole in una posizione nel mondo reale, ad esempio, un punto indica all'utente di particolare interesse. Le posizioni di ancoraggio non dello sfasamento, ma possono essere corretto; il punto di ancoraggio userà la posizione corretta partire il frame successivo dopo che si è verificata la correzione.

## <a name="place-holograms-in-the-world-using-spatial-anchors"></a>Ologrammi luogo nel mondo usando gli ancoraggi spaziali

[Gli ancoraggi spaziali](coordinate-systems.md#spatial-anchors) sono un ottimo modo per inserire vntana in un punto specifico nel mondo reale, con il sistema assicurando l'ancoraggio rimarrà nella stessa posizione nel corso del tempo. Questo argomento viene illustrato come creare e usare un ancoraggio e come usare i dati di ancoraggio.

È possibile creare un SpatialAnchor in qualsiasi posizione e l'orientamento all'interno di SpatialCoordinateSystem di propria scelta. Il dispositivo deve essere in grado di individuare il sistema di coordinate nel momento in cui e il sistema non deve avere raggiunto il limite di ancoraggi spaziali.

Una volta definito, il sistema di coordinate di un SpatialAnchor regola continuamente per mantenere la posizione esatta e l'orientamento del relativo percorso iniziale. È quindi possibile usare questo SpatialAnchor per eseguire il rendering vntana che verrà visualizzato predefinito nelle vicinanze dell'utente in tale posizione esatta.

Gli effetti delle modifiche che consentono di mantenere il punto di ancoraggio posto diventano ancora più evidenti come distanza tra gli aumenti di ancoraggio. Pertanto, è consigliabile evitare il rendering del contenuto relativo un ancoraggio che è superiore a circa 3 misuratori dall'origine di tale dell'ancoraggio.

Il [sistema di coordinate](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.coordinatesystem.aspx) proprietà ottiene un sistema di coordinate che consente di collocare il contenuto relativo all'ancoraggio, l'interpolazione applicata quando il dispositivo viene modificata la posizione esatta dell'ancoraggio.

Usare la [RawCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystem.aspx) proprietà e le corrispondenti [RawCoordinateSystemAdjusted](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted.aspx) eventi di gestire queste modifiche manualmente.

### <a name="persist-and-share-spatial-anchors"></a>Salvare in modo permanente e condividere gli ancoraggi spaziali

È possibile rendere persistente un SpatialAnchor in locale usando il [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx) classe e quindi dobbiamo riceverlo di nuovo in una sessione di app future sullo stesso dispositivo HoloLens.

Usando <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Anchor spaziali Azure</a>, è possibile creare un punto di ancoraggio cloud permanenti da un SpatialAnchor locale, che consente quindi di individuare l'app in più HoloLens, dispositivi iOS e Android.  Condividendo un ancoraggio spaziale comune tra più dispositivi, ogni utente può visualizzare il contenuto sottoposto a rendering relativo tale ancoraggio nella stessa posizione fisica.  Ciò consente esperienze condivise in tempo reale.

È anche possibile usare <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Anchor spaziali Azure</a> per la persistenza asincrona ologrammi nei dispositivi Android, iOS e HoloLens.  Condividendo un ancoraggio spaziali cloud durevole, più dispositivi possono osservare le stessi ologrammi persistenti nel corso del tempo, anche se questi dispositivi non sono presenti nello stesso momento.

Per iniziare a creare esperienze condivise nell'app HoloLens, provare i 5 minuti <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Guida introduttiva di Azure spaziali ancoraggi HoloLens</a>.

Quando si è in esecuzione con Azure Anchor spaziale, è possibile quindi <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">creare e individuare gli ancoraggi su HoloLens</a>.  Sono disponibili per procedure dettagliate <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android e iOS</a> , consentendo di condividere gli ancoraggi stesso in tutti i dispositivi.

### <a name="create-spatialanchors-for-holographic-content"></a>Creare SpatialAnchors per contenuto holographic

Per questo esempio di codice è stata modificata la Windows Holographic consente di vincolare il modello di app da creare quando la **Pressed** viene rilevato movimento. Il cubo viene quindi inserito nel punto di ancoraggio durante il passaggio di rendering.

Poiché più punti di ancoraggio sono supportate dalla classe helper, possiamo inserire tutti i cubi vogliamo usando questo esempio di codice!

Si noti che gli ID per gli ancoraggi sono un elemento che possono essere controllati tramite l'app. In questo esempio è stato creato uno schema di denominazione che è sequenza in base al numero dei Anchor attualmente archiviati nella raccolta dell'app di punti di ancoraggio.

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

### <a name="asynchronously-load-and-cache-the-spatialanchorstore"></a>Caricare in modo asincrono e memorizza nella cache, il SpatialAnchorStore

Ora verrà descritto come scrivere una classe SampleSpatialAnchorHelper che consente di gestire la persistenza, tra cui:
* L'archiviazione di una raccolta di punti di ancoraggio in memoria, indicizzati da una chiave di platform:: String.
* Carica gli ancoraggi da SpatialAnchorStore del sistema, che vengono mantenuti separati dalla raccolta in memoria locale.
* Salvataggio di raccolta in memoria locale dei punti di ancoraggio nel SpatialAnchorStore quando l'app sceglie di eseguire questa operazione.

Di seguito viene illustrato come salvare [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) gli oggetti di [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).

Quando la classe di avvio, richiediamo il SpatialAnchorStore in modo asincrono. Ciò comporta il / o di sistema come l'API viene caricato nell'archivio di ancoraggio e questa API viene resa asincrona in modo che il / o è non bloccante.

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

Verrà assegnato un SpatialAnchorStore che è possibile usare per salvare gli ancoraggi. Si tratta di un IMapView che associa i valori di chiave che sono stringhe, con valori di dati che sono SpatialAnchors. Nel codice di esempio, viene memorizzato in una variabile membro di classe privata che è accessibile tramite una funzione pubblica della nostra classe helper.

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

### <a name="save-content-to-the-anchor-store"></a>Salvare il contenuto nell'archivio di ancoraggio

Quando il sistema sospende l'app, è necessario salvare i punti di ancoraggio spaziali nell'archivio di ancoraggio. È anche possibile salvare gli ancoraggi nell'archivio di ancoraggio in altri momenti, si trova come necessari per l'implementazione dell'app.

Quando si è pronti per provare a salvare gli ancoraggi in memoria per il SpatialAnchorStore, è possibile scorrere la raccolta e provare a salvare ognuno di essi.

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

### <a name="load-content-from-the-anchor-store-when-the-app-resumes"></a>Caricare il contenuto dall'archivio di ancoraggio alla ripresa dell'app

Quando si riprende l'app o in qualsiasi altro momento necessario per implementaiton dell'app, è possibile ripristinare gli ancoraggi che sono stati salvati in precedenza per il AnchorStore trasferendo li dal IMapView l'ancoraggio dell'archivio per il proprio database in memoria di SpatialAnchors.

Per ripristinare gli ancoraggi dal SpatialAnchorStore, ripristinare ognuno dei quali si è interessati alla propria raccolta in memoria.

È necessario il proprio database in memoria di SpatialAnchors; un modo per associare le stringhe SpatialAnchors creato. Nel codice di esempio, si sceglie di utilizzare un Windows::Foundation::Collections::IMap per archiviare gli ancoraggi, che rendono più facile da usare lo stesso valore chiave e i dati per il SpatialAnchorStore.

```
   // This is an in-memory anchor list that is separate from the anchor store.
   // These anchors may be used, reasoned about, and so on before committing the collection to the store.
   Windows::Foundation::Collections::IMap<Platform::String^, Windows::Perception::Spatial::SpatialAnchor^>^ m_anchorMap;
```

>[!NOTE]
>Un ancoraggio che viene ripristinato potrebbe non essere immediatamente individuabile. Ad esempio, potrebbe essere un ancoraggio in una stanza separata o in una compilazione diversa completamente. Gli ancoraggi recuperati il AnchorStore dovrebbero essere verificati locatability prima di usarli.

<br>

>[!NOTE]
>In questo codice di esempio, vengono recuperati tutti i punti di ancoraggio dal AnchorStore. Questo non è un requisito; l'app può anche scegliere un determinato subset di punti di ancoraggio utilizzando i valori stringa chiave che sono significativi per l'implementazione.

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

In alcuni casi, è necessario cancellare lo stato dell'app e scrivere nuovi dati. Ecco come procedere con il [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).

Usa la classe helper, non è quasi necessario includere la funzione non crittografata. Abbiamo scegliere di eseguire questa operazione nel nostro esempio di implementazione, poiché la classe helper ha la responsabilità di possedere l'istanza SpatialAnchorStore.

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

### <a name="example-relating-anchor-coordinate-systems-to-stationary-reference-frame-coordinate-systems"></a>Esempio: Relativi sistemi di coordinate di ancoraggio a sistemi di coordinate di frame di riferimento fisso

Si supponga che è un ancoraggio che si desidera correlare qualcosa nel sistema di coordinate dell'ancoraggio a SpatialStationaryReferenceFrame che è già in uso per la maggior parte di altri contenuti. È possibile usare [TryGetTransformTo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.trygettransformto.aspx) per ottenere una trasformazione dal sistema di coordinate dell'ancoraggio a quello del fotogramma di riferimento fisso:

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
1. Indica se i due frame di riferimento può essere interpretata una rispetto a altra, e;
2. In questo caso, esso fornisce una trasformazione per passare direttamente da un sistema di coordinate a altro.

Con queste informazioni, è necessario comprendere la relazione tra gli oggetti tra i due frame di riferimento spaziale.

Per il rendering, è spesso possibile ottenere risultati migliori mediante il raggruppamento di oggetti in base ai relativi frame di riferimento originale o un punto di ancoraggio. Eseguire un passaggio di disegno distinto per ogni gruppo. Le matrici di visualizzazione sono più accurate per gli oggetti con le trasformazioni di modello che vengono creati inizialmente utilizzando lo stesso sistema di coordinate.

## <a name="create-holograms-using-a-device-attached-frame-of-reference"></a>Creare vntana usando un dispositivo collegato fotogramma di riferimento

Vi sono casi quando si desidera eseguire il rendering di ologramma che [rimane collegato](coordinate-systems.md#attached-frame-of-reference) alla posizione del dispositivo, ad esempio un pannello con il debug quando il dispositivo è in grado di determinare il relativo orientamento solo informazioni o un messaggio informativo e non la posizione nello spazio. A tale scopo, utilizziamo un frame di riferimento collegati.

La classe SpatialLocatorAttachedFrameOfReference definisce i sistemi di coordinate che rappresentano rispetto al dispositivo invece che a del mondo reale. Il frame è un'intestazione fissa rispetto all'ambiente circostante dell'utente che punta nella direzione l'utente si trovava quando è stato creato il frame di riferimento. Da questo momento, tutti gli orientamenti in questo frame di riferimento sono relative all'intestazione fissa, anche quando l'utente ruota il dispositivo.

Per HoloLens, l'origine del sistema di coordinate del frame, questa si trova al centro di rotazione dell'intestazione dell'utente, in modo che la posizione non è interessata dalla rotazione head. L'app può specificare un offset rispetto a questo punto per posizionare vntana davanti all'utente.

Per ottenere un SpatialLocatorAttachedFrameOfReference, usare la classe SpatialLocator e chiamare CreateAttachedFrameOfReferenceAtCurrentHeading.

Si noti che questo si applica ai dispositivi intero intervallo della realtà mista di Windows.

### <a name="use-a-reference-frame-attached-to-the-device"></a>Utilizzare un frame di riferimento collegato al dispositivo

Queste sezioni sono descritti nel modello di app Windows Holographic per abilitare un dispositivo collegato fotogramma di riferimento usano questa API è stato modificato. Si noti che questo ologrammi "collegato" procederanno vntana fermo o ancorati e possono essere utilizzato anche quando il dispositivo è temporaneamente non è possibile trovare la posizione corrispondente in tutto il mondo.

In primo luogo, è stato modificato il modello per archiviare un SpatialLocatorAttachedFrameOfReference anziché un SpatialStationaryFrameOfReference:

Dal **HolographicTagAlongSampleMain.h**:

```
   // A reference frame attached to the holographic camera.
   Windows::Perception::Spatial::SpatialLocatorAttachedFrameOfReference^   m_referenceFrame;
```

Dal **HolographicTagAlongSampleMain.cpp**:

```
   // In this example, we create a reference frame attached to the device.
   m_referenceFrame = m_locator->CreateAttachedFrameOfReferenceAtCurrentHeading();
```

Durante l'aggiornamento, è ora possibile ottenere il sistema di coordinate dal timestamp ottenuto con la stima di frame.

```
   // Next, we get a coordinate system from the attached frame of reference that is
   // associated with the current frame. Later, this coordinate system is used for
   // for creating the stereo view matrices when rendering the sample content.
   SpatialCoordinateSystem^ currentCoordinateSystem =
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp);
```

### <a name="get-a-spatial-pointer-pose-and-follow-the-users-gaze"></a>Ottenere una puntatore spaziali posa e seguire sguardo dell'utente

Vogliamo ologrammi nostro esempio di seguire l'utente [estasiati](gaze.md), analogamente al modo in cui la shell holographic può seguire sguardo dell'utente. A tale scopo, è necessario ottenere il SpatialPointerPose da stesso timestamp.

```
SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
```

Questo SpatialPointerPose contiene le informazioni necessarie per posizionare l'ologrammi in base al [intestazione corrente dell'utente](gaze-in-directx.md).

Per ragioni di comodità per l'utente, si userà l'interpolazione lineare ("lerp") per semplificare la modifica della posizione in modo che si verifica un periodo di tempo. Questo è più pratico per l'utente di blocco di ologramma per loro sguardo. Posizione del ologrammi tag-along consente anche di stabilizzare l'ologrammi dal blocco del movimento; Lerping Se si non è stato il blocco della, l'utente visualizzerà l'ologrammi instabilità a causa di ciò che sono normalmente considerati impercettibili spostamenti principale dell'utente di.

Dal **StationaryQuadRenderer::PositionHologram**:

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
>Nel caso di un pannello di debug, è possibile scegliere riposizionare un po' di ologramma disattivato sul lato in modo che non ostacolano la visualizzazione. Di seguito è riportato un esempio di come è possibile farlo.

Per la **StationaryQuadRenderer::PositionHologram**:

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

### <a name="rotate-the-hologram-to-face-the-camera"></a>Ruotare l'ologramma per affrontare la fotocamera

Non è sufficiente posizionare semplicemente l'ologrammi, ovvero in questo caso un quadrato; è anche necessario ruotare l'oggetto in modo che sia l'utente. Si noti che questo si verifica la rotazione nello spazio globale, poiché questo tipo di billboard consente ologrammi deve rimanere una parte dell'ambiente dell'utente. Spazio di visualizzazione del billboard non agio perché l'ologrammi viene bloccato l'orientamento di visualizzazione; In tal caso, sarebbe è interpolare tra le matrici di sinistra e destra vista al fine di acquisire una trasformazione di Pannello di spazio di visualizzazione che non interrompano le attività per il rendering stereo. In questo caso, si ruota sugli assi X e Z per affrontare l'utente.

Dal **StationaryQuadRenderer::Update**:

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

### <a name="render-the-attached-hologram"></a>Eseguire il rendering di ologramma collegato

In questo esempio abbiamo anche scegliere di eseguire il rendering di ologramma nel sistema di coordinate di SpatialLocatorAttachedReferenceFrame, ovvero dove è posizionato l'ologramma. (Se avessimo deciso di eseguire il rendering utilizzando un altro sistema di coordinate, è necessario acquisire una trasformazione dal sistema di coordinate del dispositivo collegato riferimento frame da tale sistema di coordinate.)

From **HolographicTagAlongSampleMain::Render**:

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

La procedura è terminata. L'ologrammi verranno ora "vengono cercati" una posizione 2 metri davanti direzione sguardo dell'utente.

>[!NOTE]
>Questo esempio viene caricato anche il contenuto aggiuntivo, vedere StationaryQuadRenderer.cpp.

## <a name="handling-tracking-loss"></a>Gestione di una perdita di rilevamento

Quando il dispositivo non è possibile individuare se stessa nel mondo, l'app si verifichi "perdita di rilevamento". Le app di realtà mista di Windows devono essere in grado di gestire queste interruzioni per il sistema di rilevamento posizionale. È possono osservare queste interruzioni e risposte creato utilizzando l'evento LocatabilityChanged SpatialLocator predefinito.

Da **AppMain::SetHolographicSpace:**

```
   // Be able to respond to changes in the positional tracking state.
   m_locatabilityChangedToken =
       m_locator->LocatabilityChanged +=
           ref new Windows::Foundation::TypedEventHandler<SpatialLocator^, Object^>(
               std::bind(&HolographicApp1Main::OnLocatabilityChanged, this, _1, _2)
               );
```

Quando l'app riceve un evento LocatabilityChanged, è possibile modificare il comportamento in base alle esigenze. Ad esempio, nello stato PositionalTrackingInhibited possibile sospendere il normale funzionamento ed eseguire il rendering all'app un [ologrammi tag-along](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) che visualizza un messaggio di avviso.

Il modello di app per Windows Holographic dotato di un gestore LocatabilityChanged già creato. Per impostazione predefinita, verrà visualizzato un avviso nella console di debug quando rilevamento posizionale non è disponibile. È possibile aggiungere codice a questo gestore a fornire una risposta in base alle esigenze dell'app.

Da **AppMain.cpp:**

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

Il [mapping spaziale](spatial-mapping-in-directx.md) alle API di utilizzo di sistemi di coordinate per ottenere trasformazioni del modello di surface trame.

## <a name="see-also"></a>Vedere anche
* [Sistemi di coordinate](coordinate-systems.md)
* [Ancoraggi nello spazio](spatial-anchors.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Ancoraggi nello spazio di Azure</a>
* [Testa e occhio estasiati DirectX](gaze-in-directx.md)
* [Le mani e i controller di movimento in DirectX](hands-and-motion-controllers-in-directx.md)
* [Mapping spaziale in DirectX](spatial-mapping-in-directx.md)

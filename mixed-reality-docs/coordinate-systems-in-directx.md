---
title: Sistemi di coordinate in DirectX
description: Viene illustrato come usare i localizzatori spaziali di realtà mista di Windows, frame di riferimento, gli ancoraggi spaziali e i sistemi di coordinate, come usare il SpatialStage, come gestire la perdita di rilevamento, come salvare e caricare gli ancoraggi e procedura per creare l'immagine di stabilizzazione.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Mista realtà, indicatore di posizione spaziale, frame di riferimento spaziale, spaziale sistema di coordinate, fase spaziali, esempio codice, stabilizzazione immagine, ancoraggio spaziale, spaziali store di ancoraggio, rilevamento perdite, procedura dettagliata
ms.openlocfilehash: c8cdb39cbf4634edb4ed0a595381fc70f1388ce4
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605150"
---
# <a name="coordinate-systems-in-directx"></a><span data-ttu-id="e0fb4-104">Sistemi di coordinate in DirectX</span><span class="sxs-lookup"><span data-stu-id="e0fb4-104">Coordinate systems in DirectX</span></span>

<span data-ttu-id="e0fb4-105">[Sistemi di coordinate](coordinate-systems.md) costituiscono la base per informazioni sulle spaziali offerti dalle API di realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-105">[Coordinate systems](coordinate-systems.md) form the basis for spatial understanding offered by Windows Mixed Reality APIs.</span></span>

<span data-ttu-id="e0fb4-106">Oggi seduto VR o dispositivi VR singolo spazio stabilire un sistema di coordinate primario per rappresentare il relativo spazio rilevata.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-106">Today's seated VR or single-room VR devices establish one primary coordinate system to represent their tracked space.</span></span> <span data-ttu-id="e0fb4-107">Dispositivi per realtà mista di Windows come HoloLens sono progettati per essere usate in ambienti di grandi dimensioni non definiti, con il dispositivo rilevando e apprendere i concetti relativi adatto al contesto dell'utente camminare.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-107">Windows Mixed Reality devices such as HoloLens are designed to be used throughout large undefined environments, with the device discovering and learning about its surroundings as the user walks around.</span></span> <span data-ttu-id="e0fb4-108">In questo modo il dispositivo per adattarsi a migliorare continuamente una conoscenza dell'utente locali, i risultati in sistemi di coordinate che modificheranno le relazioni tra loro ciclo di vita dell'app.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-108">This allows the device to adapt to continually-improving knowledge about the user's rooms, but results in coordinate systems that will change their relationship to one another through the lifetime of the app.</span></span> <span data-ttu-id="e0fb4-109">Realtà mista di Windows supporta un'ampia gamma di dispositivi, compreso fra seduti auricolari coinvolgenti e frame di riferimento collegati al mondo.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-109">Windows Mixed Reality supports a wide spectrum of devices, ranging from seated immersive headsets through world-attached reference frames.</span></span>

>[!NOTE]
><span data-ttu-id="e0fb4-110">I frammenti di codice in questo articolo illustrano attualmente l'utilizzo di C++/CX invece di C + + 17 conformi C++/WinRT usato nel [ C++ modello di progetto holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="e0fb4-110">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="e0fb4-111">I concetti sono equivalenti per un C++progetto /WinRT, anche se è necessario convertire il codice.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-111">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="spatial-coordinate-systems-in-windows"></a><span data-ttu-id="e0fb4-112">Sistemi di coordinate spaziali in Windows</span><span class="sxs-lookup"><span data-stu-id="e0fb4-112">Spatial coordinate systems in Windows</span></span>

<span data-ttu-id="e0fb4-113">Il tipo di base utilizzato per prendere in considerazione i sistemi di coordinate reali in Windows è il <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-113">The core type used to reason about real-world coordinate systems in Windows is the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>.</span></span> <span data-ttu-id="e0fb4-114">Un'istanza di questo tipo rappresenta un sistema di coordinate arbitrario e fornisce un metodo per ottenere una matrice di trasformazione che è possibile usare per eseguire una conversione tra due sistemi di coordinate senza conoscere i dettagli della ognuno.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-114">An instance of this type represents an arbitrary coordinate system and provides a method to get a transformation matrix that you can use to transform between two coordinate systems without understanding the details of each.</span></span>

<span data-ttu-id="e0fb4-115">I metodi che restituiscono informazioni spaziali, rappresentate come punti, rays o volumi nell'ambiente circostante dell'utente, accetterà un parametro SpatialCoordinateSystem per decidere il sistema di coordinate in cui è particolarmente utile per le coordinate da restituire.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-115">Methods that return spatial information, represented as points, rays, or volumes in the user's surroundings, will accept a SpatialCoordinateSystem parameter to let you decide the coordinate system in which it's most useful for those coordinates to be returned.</span></span> <span data-ttu-id="e0fb4-116">Le unità per tali coordinate sarà sempre in metri.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-116">The units for these coordinates will always be in meters.</span></span>

<span data-ttu-id="e0fb4-117">Un SpatialCoordinateSystem ha una relazione dinamica con altri sistemi di coordinate, incluse quelle che rappresentano la posizione del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-117">A SpatialCoordinateSystem has a dynamic relationship with other coordinate systems, including those that represent the device's position.</span></span> <span data-ttu-id="e0fb4-118">In qualsiasi momento, il dispositivo potrebbe essere in grado di individuare alcuni sistemi di coordinate e non altri.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-118">At any point in time, the device may be able to locate some coordinate systems and not others.</span></span> <span data-ttu-id="e0fb4-119">Per la maggior parte dei sistemi di coordinate, l'app deve essere pronta a gestire i periodi di tempo durante il quale non è possibile individuare.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-119">For most coordinate systems, your app must be ready to handle periods of time during which they cannot be located.</span></span>

<span data-ttu-id="e0fb4-120">L'applicazione non deve essere creato direttamente SpatialCoordinateSystems - piuttosto devono essere usati tramite le API di percezione.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-120">Your application should not create SpatialCoordinateSystems directly - rather they should be consumed via the Perception APIs.</span></span> <span data-ttu-id="e0fb4-121">Sono disponibili tre fonti principali di sistemi di coordinate nelle API di percezione, ognuna delle quali mappa a un concetto descritto nel [sistemi di Coordinate](coordinate-systems.md) pagina:</span><span class="sxs-lookup"><span data-stu-id="e0fb4-121">There are three primary sources of coordinate systems in the Perception APIs, each of which map to a concept described on the [Coordinate systems](coordinate-systems.md) page:</span></span>
* <span data-ttu-id="e0fb4-122">Per ottenere un frame di riferimento fisso, creare un <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference</a> oppure ottenerne uno da corrente <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference</a>.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-122">To get a stationary frame of reference, create a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference</a> or obtain one from the current <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference</a>.</span></span>
* <span data-ttu-id="e0fb4-123">Per ottenere un punto di ancoraggio spaziale, creare un <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-123">To get a spatial anchor, create a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>.</span></span>
* <span data-ttu-id="e0fb4-124">Per ottenere un frame di riferimento collegati, creare un <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-124">To get an attached frame of reference, create a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>.</span></span>

<span data-ttu-id="e0fb4-125">Tutti i sistemi di coordinate restituiti da questi oggetti sono da destra, con + y, + x a destra e + z con le versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-125">All of the coordinate systems returned by these objects are right-handed, with +y up, +x to the right and +z backwards.</span></span> <span data-ttu-id="e0fb4-126">È possibile ricordare direzione in cui i punti di positivi dell'asse z verso le dita di sinistra o a destra nella direzione x positivo e a usare CURL li nella direzione y positivo.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-126">You can remember which direction the positive z-axis points by pointing the fingers of either your left or right hand in the positive x direction and curling them into the positive y direction.</span></span> <span data-ttu-id="e0fb4-127">La direzione in cui punta il pollice, verso di te o in direzione opposta, è la direzione a cui punta l’asse z positivo per tale sistema di coordinate.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-127">The direction your thumb points, either toward or away from you, is the direction that the positive z-axis points for that coordinate system.</span></span> <span data-ttu-id="e0fb4-128">La figura seguente mostra questi due sistemi di coordinate.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-128">The following illustration shows these two coordinate systems.</span></span>

<span data-ttu-id="e0fb4-129">![Sistemi di coordinate a sinistra e destra](images/left-hand-right-hand.gif)</span><span class="sxs-lookup"><span data-stu-id="e0fb4-129">![Left-hand and right-hand coordinate systems](images/left-hand-right-hand.gif)</span></span><br>
<span data-ttu-id="e0fb4-130">*Sistemi di coordinate a sinistra e destra*</span><span class="sxs-lookup"><span data-stu-id="e0fb4-130">*Left-hand and right-hand coordinate systems*</span></span>

<span data-ttu-id="e0fb4-131">Per eseguire il bootstrap in un SpatialCoordinateSystem basato sulla posizione di un HoloLens, usare il <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a> classe per creare entrambi un allegato o fermo fotogramma di riferimento, come descritto nelle sezioni seguenti.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-131">To bootstrap into a SpatialCoordinateSystem based on the position of a HoloLens, use the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a> class to create either an attached or stationary frame of reference, as described in the sections below.</span></span>

## <a name="place-holograms-in-the-world-using-a-spatial-stage"></a><span data-ttu-id="e0fb4-132">Ologrammi luogo nel mondo usando una fase spaziale</span><span class="sxs-lookup"><span data-stu-id="e0fb4-132">Place holograms in the world using a spatial stage</span></span>

<span data-ttu-id="e0fb4-133">Il sistema di coordinate per opachi auricolari coinvolgenti di realtà mista di Windows è accessibile tramite il metodo statico <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference::Current</a> proprietà.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-133">The coordinate system for opaque Windows Mixed Reality immersive headsets is accessed using the static <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference::Current</a> property.</span></span> <span data-ttu-id="e0fb4-134">Questa API fornisce un sistema di coordinate, informazioni su se il lettore viene inserito o per dispositivi mobili, il limite di una zona di sicurezza per l'analisi di tutto se il giocatore è mobile e un'indicazione o meno le cuffie direzionale.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-134">This API provides a coordinate system, information about whether the player is seated or mobile, the boundary of a safe area for walking around if the player is mobile, and an indication of whether or not the headset is directional.</span></span> <span data-ttu-id="e0fb4-135">È inoltre disponibile un gestore eventi per gli aggiornamenti alla fase spaziale.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-135">There is also an event handler for updates to the spatial stage.</span></span>

<span data-ttu-id="e0fb4-136">Prima di tutto è ottenere la fase spaziale e la sottoscrizione per gli aggiornamenti:</span><span class="sxs-lookup"><span data-stu-id="e0fb4-136">First, we get the spatial stage and subscribe for updates to it:</span></span> 

<span data-ttu-id="e0fb4-137">Il codice per **inizializzazione fase spaziali**</span><span class="sxs-lookup"><span data-stu-id="e0fb4-137">Code for **Spatial stage initialization**</span></span>

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

<span data-ttu-id="e0fb4-138">Nel metodo OnCurrentChanged, l'app deve controllare la fase spaziale e aggiornare di conseguenza l'esperienza dei giocatori.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-138">In the OnCurrentChanged method, your app should inspect the spatial stage and update the player experience accordingly.</span></span> <span data-ttu-id="e0fb4-139">In questo esempio, viene fornita una visualizzazione del limite di fase, nonché la posizione iniziale specificata dall'utente e intervallo della fase di visualizzazione e l'intervallo di proprietà di spostamento.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-139">In this example, we provide a visualization of the stage boundary, as well as the start position specified by the user and the stage's range of view and range of movement properties.</span></span> <span data-ttu-id="e0fb4-140">È anche eseguire il fallback al nostro sistema di coordinate stazionario, quando una fase non può essere fornita.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-140">We also fall back to our own stationary coordinate system, when a stage cannot be provided.</span></span>


<span data-ttu-id="e0fb4-141">Il codice per **update fase spaziali**</span><span class="sxs-lookup"><span data-stu-id="e0fb4-141">Code for **Spatial stage update**</span></span>

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

<span data-ttu-id="e0fb4-142">Il set di vertici che definiscono il limite di fase vengono forniti in senso antiorario.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-142">The set of vertices that define the stage boundary are provided in clockwise order.</span></span> <span data-ttu-id="e0fb4-143">La shell di realtà mista di Windows consente di disegnare un limite in corrispondenza del limite quando l'utente si avvicina a esso. è consigliabile triangularize l'area è percorribile per le proprie esigenze.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-143">The Windows Mixed Reality shell draws a fence at the boundary when the user approaches it; you may wish to triangularize the walkable area for your own purposes.</span></span> <span data-ttu-id="e0fb4-144">L'algoritmo seguente utilizzabile per triangularize della fase.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-144">The following algorithm can be used to triangularize the stage.</span></span>


<span data-ttu-id="e0fb4-145">Il codice per **triangularization fase spaziali**</span><span class="sxs-lookup"><span data-stu-id="e0fb4-145">Code for **Spatial stage triangularization**</span></span>

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

## <a name="place-holograms-in-the-world-using-a-stationary-frame-of-reference"></a><span data-ttu-id="e0fb4-146">Ologrammi luogo nel mondo usando un frame di riferimento fisso</span><span class="sxs-lookup"><span data-stu-id="e0fb4-146">Place holograms in the world using a stationary frame of reference</span></span>

<span data-ttu-id="e0fb4-147">Il [SpatialStationaryFrameOfReference](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialstationaryframeofreference.aspx) classe rappresenta un frame di fare riferimento a tale [rimane stazionario](coordinate-systems.md#stationary-frame-of-reference) rispetto all'ambiente circostante dell'utente come utente non si sposta.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-147">The [SpatialStationaryFrameOfReference](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialstationaryframeofreference.aspx) class represents a frame of reference that [remains stationary](coordinate-systems.md#stationary-frame-of-reference) relative to the user's surroundings as the user moves around.</span></span> <span data-ttu-id="e0fb4-148">Questo fa riferimento a assegna la priorità alle coordinate mantenere stabili in prossimità del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-148">This frame of reference prioritizes keeping coordinates stable near the device.</span></span> <span data-ttu-id="e0fb4-149">Uno degli utilizzi principali di un SpatialStationaryFrameOfReference deve agire come sistema di coordinate world sottostante all'interno di un motore di rendering per il rendering vntana.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-149">One key use of a SpatialStationaryFrameOfReference is to act as the underlying world coordinate system within a rendering engine when rendering holograms.</span></span>

<span data-ttu-id="e0fb4-150">Per ottenere un SpatialStationaryFrameOfReference, usare il [SpatialLocator](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.aspx) classe e chiamare [CreateStationaryFrameOfReferenceAtCurrentLocation](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.createstationaryframeofreferenceatcurrentlocation.aspx).</span><span class="sxs-lookup"><span data-stu-id="e0fb4-150">To get a SpatialStationaryFrameOfReference, use the [SpatialLocator](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.aspx) class and call [CreateStationaryFrameOfReferenceAtCurrentLocation](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.createstationaryframeofreferenceatcurrentlocation.aspx).</span></span>

<span data-ttu-id="e0fb4-151">Dal codice del modello di app Windows Holographic:</span><span class="sxs-lookup"><span data-stu-id="e0fb4-151">From the Windows Holographic app template code:</span></span>

```
           // The simplest way to render world-locked holograms is to create a stationary reference frame
           // when the app is launched. This is roughly analogous to creating a "world" coordinate system
           // with the origin placed at the device's position as the app is launched.
           referenceFrame = locator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```
* <span data-ttu-id="e0fb4-152">I frame di riferimento fisso sono progettati per fornire una posizione ottimale rispetto al spazio complessivo.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-152">Stationary reference frames are designed to provide a best-fit position relative to the overall space.</span></span> <span data-ttu-id="e0fb4-153">Le singole posizioni all'interno di quel frame di riferimento sono consentite per deviare leggermente.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-153">Individual positions within that reference frame are allowed to drift slightly.</span></span> <span data-ttu-id="e0fb4-154">Questo è normale, poiché il dispositivo viene a conoscenza delle informazioni sull'ambiente.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-154">This is normal as the device learns more about the environment.</span></span>
* <span data-ttu-id="e0fb4-155">Quando viene richiesto il posizionamento preciso degli vntana singoli, una SpatialAnchor deve essere usato per ancorare l'ologrammi singole in una posizione nel mondo reale, ad esempio, un punto indica all'utente di particolare interesse.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-155">When precise placement of individual holograms is required, a SpatialAnchor should be used to anchor the individual hologram to a position in the real world - for example, a point the user indicates to be of special interest.</span></span> <span data-ttu-id="e0fb4-156">Le posizioni di ancoraggio non dello sfasamento, ma possono essere corretto; il punto di ancoraggio userà la posizione corretta partire il frame successivo dopo che si è verificata la correzione.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-156">Anchor positions do not drift, but can be corrected; the anchor will use the corrected position starting in the next frame after the correction has occurred.</span></span>

## <a name="place-holograms-in-the-world-using-spatial-anchors"></a><span data-ttu-id="e0fb4-157">Ologrammi luogo nel mondo usando gli ancoraggi spaziali</span><span class="sxs-lookup"><span data-stu-id="e0fb4-157">Place holograms in the world using spatial anchors</span></span>

<span data-ttu-id="e0fb4-158">[Gli ancoraggi spaziali](coordinate-systems.md#spatial-anchors) sono un ottimo modo per inserire vntana in un punto specifico nel mondo reale, con il sistema assicurando l'ancoraggio rimarrà nella stessa posizione nel corso del tempo.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-158">[Spatial anchors](coordinate-systems.md#spatial-anchors) are a great way to place holograms at a specific place in the real world, with the system ensuring the anchor stays in place over time.</span></span> <span data-ttu-id="e0fb4-159">Questo argomento viene illustrato come creare e usare un ancoraggio e come usare i dati di ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-159">This topic explains how to create and use an anchor, and how to work with anchor data.</span></span>

<span data-ttu-id="e0fb4-160">È possibile creare un SpatialAnchor in qualsiasi posizione e l'orientamento all'interno di SpatialCoordinateSystem di propria scelta.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-160">You can create a SpatialAnchor at any position and orientation within the SpatialCoordinateSystem of your choosing.</span></span> <span data-ttu-id="e0fb4-161">Il dispositivo deve essere in grado di individuare il sistema di coordinate nel momento in cui e il sistema non deve avere raggiunto il limite di ancoraggi spaziali.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-161">The device must be able to locate that coordinate system at the moment, and the system must not have reached its limit of spatial anchors.</span></span>

<span data-ttu-id="e0fb4-162">Una volta definito, il sistema di coordinate di un SpatialAnchor regola continuamente per mantenere la posizione esatta e l'orientamento del relativo percorso iniziale.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-162">Once defined, the coordinate system of a SpatialAnchor adjusts continually to retain the precise position and orientation of its initial location.</span></span> <span data-ttu-id="e0fb4-163">È quindi possibile usare questo SpatialAnchor per eseguire il rendering vntana che verrà visualizzato predefinito nelle vicinanze dell'utente in tale posizione esatta.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-163">You can then use this SpatialAnchor to render holograms that will appear fixed in the user's surroundings at that exact location.</span></span>

<span data-ttu-id="e0fb4-164">Gli effetti delle modifiche che consentono di mantenere il punto di ancoraggio posto diventano ancora più evidenti come distanza tra gli aumenti di ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-164">The effects of the adjustments that keep the anchor in place are magnified as distance from the anchor increases.</span></span> <span data-ttu-id="e0fb4-165">Pertanto, è consigliabile evitare il rendering del contenuto relativo un ancoraggio che è superiore a circa 3 misuratori dall'origine di tale dell'ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-165">Therefore, you should avoid rendering content relative to an anchor that is more than about 3 meters from that anchor's origin.</span></span>

<span data-ttu-id="e0fb4-166">Il [sistema di coordinate](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.coordinatesystem.aspx) proprietà ottiene un sistema di coordinate che consente di collocare il contenuto relativo all'ancoraggio, l'interpolazione applicata quando il dispositivo viene modificata la posizione esatta dell'ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-166">The [CoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.coordinatesystem.aspx) property gets a coordinate system that lets you place content relative to the anchor, with easing applied when the device adjusts the anchor's precise location.</span></span>

<span data-ttu-id="e0fb4-167">Usare la [RawCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystem.aspx) proprietà e le corrispondenti [RawCoordinateSystemAdjusted](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted.aspx) eventi di gestire queste modifiche manualmente.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-167">Use the [RawCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystem.aspx) property and the corresponding [RawCoordinateSystemAdjusted](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted.aspx) event to manage these adjustments yourself.</span></span>

### <a name="persist-and-share-spatial-anchors"></a><span data-ttu-id="e0fb4-168">Salvare in modo permanente e condividere gli ancoraggi spaziali</span><span class="sxs-lookup"><span data-stu-id="e0fb4-168">Persist and share spatial anchors</span></span>

<span data-ttu-id="e0fb4-169">È possibile rendere persistente un SpatialAnchor in locale usando il [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx) classe e quindi dobbiamo riceverlo di nuovo in una sessione di app future sullo stesso dispositivo HoloLens.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-169">You can persist a SpatialAnchor locally using the [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx) class and then get it back in a future app session on the same HoloLens device.</span></span>

<span data-ttu-id="e0fb4-170">Usando <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Anchor spaziali Azure</a>, è possibile creare un punto di ancoraggio cloud permanenti da un SpatialAnchor locale, che consente quindi di individuare l'app in più HoloLens, dispositivi iOS e Android.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-170">By using <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a>, you can create a durable cloud anchor from a local SpatialAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="e0fb4-171">Condividendo un ancoraggio spaziale comune tra più dispositivi, ogni utente può visualizzare il contenuto sottoposto a rendering relativo tale ancoraggio nella stessa posizione fisica.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-171">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="e0fb4-172">Ciò consente esperienze condivise in tempo reale.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-172">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="e0fb4-173">È anche possibile usare <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Anchor spaziali Azure</a> per la persistenza asincrona ologrammi nei dispositivi Android, iOS e HoloLens.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-173">You can also use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="e0fb4-174">Condividendo un ancoraggio spaziali cloud durevole, più dispositivi possono osservare le stessi ologrammi persistenti nel corso del tempo, anche se questi dispositivi non sono presenti nello stesso momento.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-174">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices are not present together at the same time.</span></span>

<span data-ttu-id="e0fb4-175">Per iniziare a creare esperienze condivise nell'app HoloLens, provare i 5 minuti <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Guida introduttiva di Azure spaziali ancoraggi HoloLens</a>.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-175">To get started building shared experiences in your HoloLens app, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure Spatial Anchors HoloLens quickstart</a>.</span></span>

<span data-ttu-id="e0fb4-176">Quando si è in esecuzione con Azure Anchor spaziale, è possibile quindi <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">creare e individuare gli ancoraggi su HoloLens</a>.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-176">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">create and locate anchors on HoloLens</a>.</span></span>  <span data-ttu-id="e0fb4-177">Sono disponibili per procedure dettagliate <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android e iOS</a> , consentendo di condividere gli ancoraggi stesso in tutti i dispositivi.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-177">Walkthroughs are available for <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android and iOS</a> as well, enabling you to share the same anchors on all devices.</span></span>

### <a name="create-spatialanchors-for-holographic-content"></a><span data-ttu-id="e0fb4-178">Creare SpatialAnchors per contenuto holographic</span><span class="sxs-lookup"><span data-stu-id="e0fb4-178">Create SpatialAnchors for holographic content</span></span>

<span data-ttu-id="e0fb4-179">Per questo esempio di codice è stata modificata la Windows Holographic consente di vincolare il modello di app da creare quando la **Pressed** viene rilevato movimento.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-179">For this code sample, we modified the Windows Holographic app template to create anchors when the **Pressed** gesture is detected.</span></span> <span data-ttu-id="e0fb4-180">Il cubo viene quindi inserito nel punto di ancoraggio durante il passaggio di rendering.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-180">The cube is then placed at the anchor during the render pass.</span></span>

<span data-ttu-id="e0fb4-181">Poiché più punti di ancoraggio sono supportate dalla classe helper, possiamo inserire tutti i cubi vogliamo usando questo esempio di codice!</span><span class="sxs-lookup"><span data-stu-id="e0fb4-181">Since multiple anchors are supported by the helper class, we can place as many cubes as we want using this code sample!</span></span>

<span data-ttu-id="e0fb4-182">Si noti che gli ID per gli ancoraggi sono un elemento che possono essere controllati tramite l'app.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-182">Note that the IDs for anchors are something you control in your app.</span></span> <span data-ttu-id="e0fb4-183">In questo esempio è stato creato uno schema di denominazione che è sequenza in base al numero dei Anchor attualmente archiviati nella raccolta dell'app di punti di ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-183">In this example, we have created a naming scheme that is sequential based on the number of anchors currently stored in the app's collection of anchors.</span></span>

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

### <a name="asynchronously-load-and-cache-the-spatialanchorstore"></a><span data-ttu-id="e0fb4-184">Caricare in modo asincrono e memorizza nella cache, il SpatialAnchorStore</span><span class="sxs-lookup"><span data-stu-id="e0fb4-184">Asynchronously load, and cache, the SpatialAnchorStore</span></span>

<span data-ttu-id="e0fb4-185">Ora verrà descritto come scrivere una classe SampleSpatialAnchorHelper che consente di gestire la persistenza, tra cui:</span><span class="sxs-lookup"><span data-stu-id="e0fb4-185">Let's see how to write a SampleSpatialAnchorHelper class that helps handle this persistence, including:</span></span>
* <span data-ttu-id="e0fb4-186">L'archiviazione di una raccolta di punti di ancoraggio in memoria, indicizzati da una chiave di platform:: String.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-186">Storing a collection of in-memory anchors, indexed by a Platform::String key.</span></span>
* <span data-ttu-id="e0fb4-187">Carica gli ancoraggi da SpatialAnchorStore del sistema, che vengono mantenuti separati dalla raccolta in memoria locale.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-187">Loading anchors from the system's SpatialAnchorStore, which is kept separate from the local in-memory collection.</span></span>
* <span data-ttu-id="e0fb4-188">Salvataggio di raccolta in memoria locale dei punti di ancoraggio nel SpatialAnchorStore quando l'app sceglie di eseguire questa operazione.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-188">Saving the local in-memory collection of anchors to the SpatialAnchorStore when the app chooses to do so.</span></span>

<span data-ttu-id="e0fb4-189">Di seguito viene illustrato come salvare [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) gli oggetti di [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).</span><span class="sxs-lookup"><span data-stu-id="e0fb4-189">Here's how to save [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) objects in the [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).</span></span>

<span data-ttu-id="e0fb4-190">Quando la classe di avvio, richiediamo il SpatialAnchorStore in modo asincrono.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-190">When the class starts up, we request the SpatialAnchorStore asynchronously.</span></span> <span data-ttu-id="e0fb4-191">Ciò comporta il / o di sistema come l'API viene caricato nell'archivio di ancoraggio e questa API viene resa asincrona in modo che il / o è non bloccante.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-191">This involves system I/O as the API loads the anchor store, and this API is made asynchronous so that the I/O is non-blocking.</span></span>

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

<span data-ttu-id="e0fb4-192">Verrà assegnato un SpatialAnchorStore che è possibile usare per salvare gli ancoraggi.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-192">You will be given a SpatialAnchorStore that you can use to save the anchors.</span></span> <span data-ttu-id="e0fb4-193">Si tratta di un IMapView che associa i valori di chiave che sono stringhe, con valori di dati che sono SpatialAnchors.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-193">This is an IMapView that associates key values that are Strings, with data values that are SpatialAnchors.</span></span> <span data-ttu-id="e0fb4-194">Nel codice di esempio, viene memorizzato in una variabile membro di classe privata che è accessibile tramite una funzione pubblica della nostra classe helper.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-194">In our sample code, we store this in a private class member variable that is accessible through a public function of our helper class.</span></span>

```
   SampleSpatialAnchorHelper::SampleSpatialAnchorHelper(SpatialAnchorStore^ anchorStore)
   {
       m_anchorStore = anchorStore;
       m_anchorMap = ref new Platform::Collections::Map<String^, SpatialAnchor^>();
   }
```

>[!NOTE]
><span data-ttu-id="e0fb4-195">Non dimenticare di associare gli eventi di sospensione/ripresa per salvare e caricare l'archivio di ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-195">Don't forget to hook up the suspend/resume events to save and load the anchor store.</span></span>

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

### <a name="save-content-to-the-anchor-store"></a><span data-ttu-id="e0fb4-196">Salvare il contenuto nell'archivio di ancoraggio</span><span class="sxs-lookup"><span data-stu-id="e0fb4-196">Save content to the anchor store</span></span>

<span data-ttu-id="e0fb4-197">Quando il sistema sospende l'app, è necessario salvare i punti di ancoraggio spaziali nell'archivio di ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-197">When the system suspends your app, you need to save your spatial anchors to the anchor store.</span></span> <span data-ttu-id="e0fb4-198">È anche possibile salvare gli ancoraggi nell'archivio di ancoraggio in altri momenti, si trova come necessari per l'implementazione dell'app.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-198">You may also choose to save anchors to the anchor store at other times, as you find to be necessary for your app's implementation.</span></span>

<span data-ttu-id="e0fb4-199">Quando si è pronti per provare a salvare gli ancoraggi in memoria per il SpatialAnchorStore, è possibile scorrere la raccolta e provare a salvare ognuno di essi.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-199">When you're ready to try saving the in-memory anchors to the SpatialAnchorStore, you can loop through your collection and try to save each one.</span></span>

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

### <a name="load-content-from-the-anchor-store-when-the-app-resumes"></a><span data-ttu-id="e0fb4-200">Caricare il contenuto dall'archivio di ancoraggio alla ripresa dell'app</span><span class="sxs-lookup"><span data-stu-id="e0fb4-200">Load content from the anchor store when the app resumes</span></span>

<span data-ttu-id="e0fb4-201">Quando si riprende l'app o in qualsiasi altro momento necessario per implementaiton dell'app, è possibile ripristinare gli ancoraggi che sono stati salvati in precedenza per il AnchorStore trasferendo li dal IMapView l'ancoraggio dell'archivio per il proprio database in memoria di SpatialAnchors.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-201">When your app resumes, or at any other time necessary for your app's implementaiton, you can restore anchors that were previously saved to the AnchorStore by transferring them from the anchor store's IMapView to your own in-memory database of SpatialAnchors.</span></span>

<span data-ttu-id="e0fb4-202">Per ripristinare gli ancoraggi dal SpatialAnchorStore, ripristinare ognuno dei quali si è interessati alla propria raccolta in memoria.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-202">To restore anchors from the SpatialAnchorStore, restore each one that you are interested in to your own in-memory collection.</span></span>

<span data-ttu-id="e0fb4-203">È necessario il proprio database in memoria di SpatialAnchors; un modo per associare le stringhe SpatialAnchors creato.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-203">You need your own in-memory database of SpatialAnchors; some way to associate Strings with the SpatialAnchors that you create.</span></span> <span data-ttu-id="e0fb4-204">Nel codice di esempio, si sceglie di utilizzare un Windows::Foundation::Collections::IMap per archiviare gli ancoraggi, che rendono più facile da usare lo stesso valore chiave e i dati per il SpatialAnchorStore.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-204">In our sample code, we choose to use a Windows::Foundation::Collections::IMap to store the anchors, which makes it easy to use the same key and data value for the SpatialAnchorStore.</span></span>

```
   // This is an in-memory anchor list that is separate from the anchor store.
   // These anchors may be used, reasoned about, and so on before committing the collection to the store.
   Windows::Foundation::Collections::IMap<Platform::String^, Windows::Perception::Spatial::SpatialAnchor^>^ m_anchorMap;
```

>[!NOTE]
><span data-ttu-id="e0fb4-205">Un ancoraggio che viene ripristinato potrebbe non essere immediatamente individuabile.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-205">An anchor that is restored might not be locatable right away.</span></span> <span data-ttu-id="e0fb4-206">Ad esempio, potrebbe essere un ancoraggio in una stanza separata o in una compilazione diversa completamente.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-206">For example, it might be an anchor in a separate room or in a different building altogether.</span></span> <span data-ttu-id="e0fb4-207">Gli ancoraggi recuperati il AnchorStore dovrebbero essere verificati locatability prima di usarli.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-207">Anchors retrieved from the AnchorStore should be tested for locatability before using them.</span></span>

<br>

>[!NOTE]
><span data-ttu-id="e0fb4-208">In questo codice di esempio, vengono recuperati tutti i punti di ancoraggio dal AnchorStore.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-208">In this example code, we retrieve all anchors from the AnchorStore.</span></span> <span data-ttu-id="e0fb4-209">Questo non è un requisito; l'app può anche scegliere un determinato subset di punti di ancoraggio utilizzando i valori stringa chiave che sono significativi per l'implementazione.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-209">This is not a requirement; your app could just as well pick and choose a certain subset of anchors by using String key values that are meaningful to your implementation.</span></span>

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

### <a name="clear-the-anchor-store-when-needed"></a><span data-ttu-id="e0fb4-210">Cancellare l'archivio di ancoraggio, quando necessario</span><span class="sxs-lookup"><span data-stu-id="e0fb4-210">Clear the anchor store, when needed</span></span>

<span data-ttu-id="e0fb4-211">In alcuni casi, è necessario cancellare lo stato dell'app e scrivere nuovi dati.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-211">Sometimes, you need to clear app state and write new data.</span></span> <span data-ttu-id="e0fb4-212">Ecco come procedere con il [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).</span><span class="sxs-lookup"><span data-stu-id="e0fb4-212">Here's how you do that with the [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).</span></span>

<span data-ttu-id="e0fb4-213">Usa la classe helper, non è quasi necessario includere la funzione non crittografata.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-213">Using our helper class, it's almost unnecessary to wrap the Clear function.</span></span> <span data-ttu-id="e0fb4-214">Abbiamo scegliere di eseguire questa operazione nel nostro esempio di implementazione, poiché la classe helper ha la responsabilità di possedere l'istanza SpatialAnchorStore.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-214">We choose to do so in our sample implementation, because our helper class is given the responsibility of owning the SpatialAnchorStore instance.</span></span>

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

### <a name="example-relating-anchor-coordinate-systems-to-stationary-reference-frame-coordinate-systems"></a><span data-ttu-id="e0fb4-215">Esempio: Relativi sistemi di coordinate di ancoraggio a sistemi di coordinate di frame di riferimento fisso</span><span class="sxs-lookup"><span data-stu-id="e0fb4-215">Example: Relating anchor coordinate systems to stationary reference frame coordinate systems</span></span>

<span data-ttu-id="e0fb4-216">Si supponga che è un ancoraggio che si desidera correlare qualcosa nel sistema di coordinate dell'ancoraggio a SpatialStationaryReferenceFrame che è già in uso per la maggior parte di altri contenuti.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-216">Let's say that you have an anchor, and you want to relate something in your anchor's coordinate system to the SpatialStationaryReferenceFrame that you’re already using for most of your other content.</span></span> <span data-ttu-id="e0fb4-217">È possibile usare [TryGetTransformTo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.trygettransformto.aspx) per ottenere una trasformazione dal sistema di coordinate dell'ancoraggio a quello del fotogramma di riferimento fisso:</span><span class="sxs-lookup"><span data-stu-id="e0fb4-217">You can use [TryGetTransformTo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.trygettransformto.aspx) to obtain a transform from the anchor’s coordinate system to that of the stationary reference frame:</span></span>

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

<span data-ttu-id="e0fb4-218">Questo processo è utile in due modi:</span><span class="sxs-lookup"><span data-stu-id="e0fb4-218">This process is useful to you in two ways:</span></span>
1. <span data-ttu-id="e0fb4-219">Indica se i due frame di riferimento può essere interpretata una rispetto a altra, e;</span><span class="sxs-lookup"><span data-stu-id="e0fb4-219">It tells you if the two reference frames can be understood relative to one another, and;</span></span>
2. <span data-ttu-id="e0fb4-220">In questo caso, esso fornisce una trasformazione per passare direttamente da un sistema di coordinate a altro.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-220">If so, it provides you a transform to go directly from one coordinate system to the other.</span></span>

<span data-ttu-id="e0fb4-221">Con queste informazioni, è necessario comprendere la relazione tra gli oggetti tra i due frame di riferimento spaziale.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-221">With this information, you have an understanding of the spatial relation between objects between the two reference frames.</span></span>

<span data-ttu-id="e0fb4-222">Per il rendering, è spesso possibile ottenere risultati migliori mediante il raggruppamento di oggetti in base ai relativi frame di riferimento originale o un punto di ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-222">For rendering, you can often obtain better results by grouping objects according to their original reference frame or anchor.</span></span> <span data-ttu-id="e0fb4-223">Eseguire un passaggio di disegno distinto per ogni gruppo.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-223">Perform a separate drawing pass for each group.</span></span> <span data-ttu-id="e0fb4-224">Le matrici di visualizzazione sono più accurate per gli oggetti con le trasformazioni di modello che vengono creati inizialmente utilizzando lo stesso sistema di coordinate.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-224">The view matrices are more accurate for objects with model transforms that are created initially using the same coordinate system.</span></span>

## <a name="create-holograms-using-a-device-attached-frame-of-reference"></a><span data-ttu-id="e0fb4-225">Creare vntana usando un dispositivo collegato fotogramma di riferimento</span><span class="sxs-lookup"><span data-stu-id="e0fb4-225">Create holograms using a device-attached frame of reference</span></span>

<span data-ttu-id="e0fb4-226">Vi sono casi quando si desidera eseguire il rendering di ologramma che [rimane collegato](coordinate-systems.md#attached-frame-of-reference) alla posizione del dispositivo, ad esempio un pannello con il debug quando il dispositivo è in grado di determinare il relativo orientamento solo informazioni o un messaggio informativo e non la posizione nello spazio.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-226">There are times when you want to render a hologram that [remains attached](coordinate-systems.md#attached-frame-of-reference) to the device's location, for example a panel with debugging information or an informational message when the device is only able to determine its orientation and not its position in space.</span></span> <span data-ttu-id="e0fb4-227">A tale scopo, utilizziamo un frame di riferimento collegati.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-227">To accomplish this, we use an attached frame of reference.</span></span>

<span data-ttu-id="e0fb4-228">La classe SpatialLocatorAttachedFrameOfReference definisce i sistemi di coordinate che rappresentano rispetto al dispositivo invece che a del mondo reale.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-228">The SpatialLocatorAttachedFrameOfReference class defines coordinate systems which are relative to the device rather than to the real-world.</span></span> <span data-ttu-id="e0fb4-229">Il frame è un'intestazione fissa rispetto all'ambiente circostante dell'utente che punta nella direzione l'utente si trovava quando è stato creato il frame di riferimento.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-229">This frame has a fixed heading relative to the user's surroundings that points in the direction the user was facing when the reference frame was created.</span></span> <span data-ttu-id="e0fb4-230">Da questo momento, tutti gli orientamenti in questo frame di riferimento sono relative all'intestazione fissa, anche quando l'utente ruota il dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-230">From then on, all orientations in this frame of reference are relative to that fixed heading, even as the user rotates the device.</span></span>

<span data-ttu-id="e0fb4-231">Per HoloLens, l'origine del sistema di coordinate del frame, questa si trova al centro di rotazione dell'intestazione dell'utente, in modo che la posizione non è interessata dalla rotazione head.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-231">For HoloLens, the origin of this frame's coordinate system is located at the center of rotation of the user's head, so that its position is not affected by head rotation.</span></span> <span data-ttu-id="e0fb4-232">L'app può specificare un offset rispetto a questo punto per posizionare vntana davanti all'utente.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-232">Your app can specify an offset relative to this point to position holograms in front of the user.</span></span>

<span data-ttu-id="e0fb4-233">Per ottenere un SpatialLocatorAttachedFrameOfReference, usare la classe SpatialLocator e chiamare CreateAttachedFrameOfReferenceAtCurrentHeading.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-233">To get a SpatialLocatorAttachedFrameOfReference, use the SpatialLocator class and call CreateAttachedFrameOfReferenceAtCurrentHeading.</span></span>

<span data-ttu-id="e0fb4-234">Si noti che questo si applica ai dispositivi intero intervallo della realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-234">Note that this applies to the entire range of Windows Mixed Reality devices.</span></span>

### <a name="use-a-reference-frame-attached-to-the-device"></a><span data-ttu-id="e0fb4-235">Utilizzare un frame di riferimento collegato al dispositivo</span><span class="sxs-lookup"><span data-stu-id="e0fb4-235">Use a reference frame attached to the device</span></span>

<span data-ttu-id="e0fb4-236">Queste sezioni sono descritti nel modello di app Windows Holographic per abilitare un dispositivo collegato fotogramma di riferimento usano questa API è stato modificato.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-236">These sections talk about what we changed in the Windows Holographic app template to enable a device-attached frame of reference using this API.</span></span> <span data-ttu-id="e0fb4-237">Si noti che questo ologrammi "collegato" procederanno vntana fermo o ancorati e possono essere utilizzato anche quando il dispositivo è temporaneamente non è possibile trovare la posizione corrispondente in tutto il mondo.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-237">Note that this "attached" hologram will work alongside stationary or anchored holograms, and may also be used when the device is temporarily unable to find its position in the world.</span></span>

<span data-ttu-id="e0fb4-238">In primo luogo, è stato modificato il modello per archiviare un SpatialLocatorAttachedFrameOfReference anziché un SpatialStationaryFrameOfReference:</span><span class="sxs-lookup"><span data-stu-id="e0fb4-238">First, we changed the template to store a SpatialLocatorAttachedFrameOfReference instead of a SpatialStationaryFrameOfReference:</span></span>

<span data-ttu-id="e0fb4-239">Dal **HolographicTagAlongSampleMain.h**:</span><span class="sxs-lookup"><span data-stu-id="e0fb4-239">From **HolographicTagAlongSampleMain.h**:</span></span>

```
   // A reference frame attached to the holographic camera.
   Windows::Perception::Spatial::SpatialLocatorAttachedFrameOfReference^   m_referenceFrame;
```

<span data-ttu-id="e0fb4-240">Dal **HolographicTagAlongSampleMain.cpp**:</span><span class="sxs-lookup"><span data-stu-id="e0fb4-240">From **HolographicTagAlongSampleMain.cpp**:</span></span>

```
   // In this example, we create a reference frame attached to the device.
   m_referenceFrame = m_locator->CreateAttachedFrameOfReferenceAtCurrentHeading();
```

<span data-ttu-id="e0fb4-241">Durante l'aggiornamento, è ora possibile ottenere il sistema di coordinate dal timestamp ottenuto con la stima di frame.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-241">During the update, we now obtain the coordinate system at the time stamp obtained from with the frame prediction.</span></span>

```
   // Next, we get a coordinate system from the attached frame of reference that is
   // associated with the current frame. Later, this coordinate system is used for
   // for creating the stereo view matrices when rendering the sample content.
   SpatialCoordinateSystem^ currentCoordinateSystem =
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp);
```

### <a name="get-a-spatial-pointer-pose-and-follow-the-users-gaze"></a><span data-ttu-id="e0fb4-242">Ottenere una puntatore spaziali posa e seguire sguardo dell'utente</span><span class="sxs-lookup"><span data-stu-id="e0fb4-242">Get a spatial pointer pose, and follow the user's Gaze</span></span>

<span data-ttu-id="e0fb4-243">Vogliamo ologrammi nostro esempio di seguire l'utente [estasiati](gaze.md), analogamente al modo in cui la shell holographic può seguire sguardo dell'utente.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-243">We want our example hologram to follow the user's [gaze](gaze.md), similar to how the holographic shell can follow the user's gaze.</span></span> <span data-ttu-id="e0fb4-244">A tale scopo, è necessario ottenere il SpatialPointerPose da stesso timestamp.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-244">For this, we need to get the SpatialPointerPose from the same time stamp.</span></span>

```
SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
```

<span data-ttu-id="e0fb4-245">Questo SpatialPointerPose contiene le informazioni necessarie per posizionare l'ologrammi in base al [intestazione corrente dell'utente](gaze,-gestures,-and-motion-controllers-in-directx.md).</span><span class="sxs-lookup"><span data-stu-id="e0fb4-245">This SpatialPointerPose has the information needed to position the hologram according to the [user's current heading](gaze,-gestures,-and-motion-controllers-in-directx.md).</span></span>

<span data-ttu-id="e0fb4-246">Per ragioni di comodità per l'utente, si userà l'interpolazione lineare ("lerp") per semplificare la modifica della posizione in modo che si verifica un periodo di tempo.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-246">For reasons of user comfort, we use linear interpolation ("lerp") to smooth the change in position such that it occurs over a period of time.</span></span> <span data-ttu-id="e0fb4-247">Questo è più pratico per l'utente di blocco di ologramma per loro sguardo.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-247">This is more comfortable for the user than locking the hologram to their gaze.</span></span> <span data-ttu-id="e0fb4-248">Posizione del ologrammi tag-along consente anche di stabilizzare l'ologrammi dal blocco del movimento; Lerping Se si non è stato il blocco della, l'utente visualizzerà l'ologrammi instabilità a causa di ciò che sono normalmente considerati impercettibili spostamenti principale dell'utente di.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-248">Lerping the tag-along hologram's position also allows us to stabilize the hologram by dampening the movement; if we did not do this dampening, the user would see the hologram jitter because of what are normally considered to be imperceptible movements of the user's head.</span></span>

<span data-ttu-id="e0fb4-249">Dal **StationaryQuadRenderer::PositionHologram**:</span><span class="sxs-lookup"><span data-stu-id="e0fb4-249">From **StationaryQuadRenderer::PositionHologram**:</span></span>

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
><span data-ttu-id="e0fb4-250">Nel caso di un pannello di debug, è possibile scegliere riposizionare un po' di ologramma disattivato sul lato in modo che non ostacolano la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-250">In the case of a debugging panel, you might choose to reposition the hologram off to the side a little so that it does not obstruct your view.</span></span> <span data-ttu-id="e0fb4-251">Di seguito è riportato un esempio di come è possibile farlo.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-251">Here's an example of how you might do that.</span></span>

<span data-ttu-id="e0fb4-252">Per la **StationaryQuadRenderer::PositionHologram**:</span><span class="sxs-lookup"><span data-stu-id="e0fb4-252">For **StationaryQuadRenderer::PositionHologram**:</span></span>

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

### <a name="rotate-the-hologram-to-face-the-camera"></a><span data-ttu-id="e0fb4-253">Ruotare l'ologramma per affrontare la fotocamera</span><span class="sxs-lookup"><span data-stu-id="e0fb4-253">Rotate the hologram to face the camera</span></span>

<span data-ttu-id="e0fb4-254">Non è sufficiente posizionare semplicemente l'ologrammi, ovvero in questo caso un quadrato; è anche necessario ruotare l'oggetto in modo che sia l'utente.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-254">It is not enough to simply position the hologram, which in this case is a quad; we must also rotate the object to face the user.</span></span> <span data-ttu-id="e0fb4-255">Si noti che questo si verifica la rotazione nello spazio globale, poiché questo tipo di billboard consente ologrammi deve rimanere una parte dell'ambiente dell'utente.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-255">Note that this rotation occurs in world space, because this type of billboarding allows the hologram to remain a part of the user's environment.</span></span> <span data-ttu-id="e0fb4-256">Spazio di visualizzazione del billboard non agio perché l'ologrammi viene bloccato l'orientamento di visualizzazione; In tal caso, sarebbe è interpolare tra le matrici di sinistra e destra vista al fine di acquisire una trasformazione di Pannello di spazio di visualizzazione che non interrompano le attività per il rendering stereo.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-256">View-space billboarding is not as comfortable because the hologram becomes locked to the display orientation; in that case, you would also have to interpolate between the left and right view matrices in order to acquire a view-space billboard transform that does not disrupt stereo rendering.</span></span> <span data-ttu-id="e0fb4-257">In questo caso, si ruota sugli assi X e Z per affrontare l'utente.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-257">Here, we rotate on the X and Z axes to face the user.</span></span>

<span data-ttu-id="e0fb4-258">Dal **StationaryQuadRenderer::Update**:</span><span class="sxs-lookup"><span data-stu-id="e0fb4-258">From **StationaryQuadRenderer::Update**:</span></span>

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

### <a name="render-the-attached-hologram"></a><span data-ttu-id="e0fb4-259">Eseguire il rendering di ologramma collegato</span><span class="sxs-lookup"><span data-stu-id="e0fb4-259">Render the attached hologram</span></span>

<span data-ttu-id="e0fb4-260">In questo esempio abbiamo anche scegliere di eseguire il rendering di ologramma nel sistema di coordinate di SpatialLocatorAttachedReferenceFrame, ovvero dove è posizionato l'ologramma.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-260">For this example, we also choose to render the hologram in the coordinate system of the SpatialLocatorAttachedReferenceFrame, which is where we positioned the hologram.</span></span> <span data-ttu-id="e0fb4-261">(Se avessimo deciso di eseguire il rendering utilizzando un altro sistema di coordinate, è necessario acquisire una trasformazione dal sistema di coordinate del dispositivo collegato riferimento frame da tale sistema di coordinate.)</span><span class="sxs-lookup"><span data-stu-id="e0fb4-261">(If we had decided to render using another coordinate system, we would need to acquire a transform from the device-attached reference frame's coordinate system to that coordinate system.)</span></span>

<span data-ttu-id="e0fb4-262">From **HolographicTagAlongSampleMain::Render**:</span><span class="sxs-lookup"><span data-stu-id="e0fb4-262">From **HolographicTagAlongSampleMain::Render**:</span></span>

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

<span data-ttu-id="e0fb4-263">La procedura è terminata.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-263">That's it!</span></span> <span data-ttu-id="e0fb4-264">L'ologrammi verranno ora "vengono cercati" una posizione 2 metri davanti direzione sguardo dell'utente.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-264">The hologram will now "chase" a position that is 2 meters in front of the user's gaze direction.</span></span>

>[!NOTE]
><span data-ttu-id="e0fb4-265">Questo esempio viene caricato anche il contenuto aggiuntivo, vedere StationaryQuadRenderer.cpp.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-265">This example also loads additional content - see StationaryQuadRenderer.cpp.</span></span>

## <a name="handling-tracking-loss"></a><span data-ttu-id="e0fb4-266">Gestione di una perdita di rilevamento</span><span class="sxs-lookup"><span data-stu-id="e0fb4-266">Handling tracking loss</span></span>

<span data-ttu-id="e0fb4-267">Quando il dispositivo non è possibile individuare se stessa nel mondo, l'app si verifichi "perdita di rilevamento".</span><span class="sxs-lookup"><span data-stu-id="e0fb4-267">When the device cannot locate itself in the world, the app experiences "tracking loss".</span></span> <span data-ttu-id="e0fb4-268">Le app di realtà mista di Windows devono essere in grado di gestire queste interruzioni per il sistema di rilevamento posizionale.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-268">Windows Mixed Reality apps should be able to handle such disruptions to the positional tracking system.</span></span> <span data-ttu-id="e0fb4-269">È possono osservare queste interruzioni e risposte creato utilizzando l'evento LocatabilityChanged SpatialLocator predefinito.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-269">These disruptions can be observed, and responses created, by using the LocatabilityChanged event on the default SpatialLocator.</span></span>

<span data-ttu-id="e0fb4-270">Da **AppMain::SetHolographicSpace:**</span><span class="sxs-lookup"><span data-stu-id="e0fb4-270">From **AppMain::SetHolographicSpace:**</span></span>

```
   // Be able to respond to changes in the positional tracking state.
   m_locatabilityChangedToken =
       m_locator->LocatabilityChanged +=
           ref new Windows::Foundation::TypedEventHandler<SpatialLocator^, Object^>(
               std::bind(&HolographicApp1Main::OnLocatabilityChanged, this, _1, _2)
               );
```

<span data-ttu-id="e0fb4-271">Quando l'app riceve un evento LocatabilityChanged, è possibile modificare il comportamento in base alle esigenze.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-271">When your app receives a LocatabilityChanged event, it can change behavior as needed.</span></span> <span data-ttu-id="e0fb4-272">Ad esempio, nello stato PositionalTrackingInhibited possibile sospendere il normale funzionamento ed eseguire il rendering all'app un [ologrammi tag-along](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) che visualizza un messaggio di avviso.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-272">For example, in the PositionalTrackingInhibited state, your app can pause normal operation and render a [tag-along hologram](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) that displays a warning message.</span></span>

<span data-ttu-id="e0fb4-273">Il modello di app per Windows Holographic dotato di un gestore LocatabilityChanged già creato.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-273">The Windows Holographic app template comes with a LocatabilityChanged handler already created for you.</span></span> <span data-ttu-id="e0fb4-274">Per impostazione predefinita, verrà visualizzato un avviso nella console di debug quando rilevamento posizionale non è disponibile.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-274">By default, it displays a warning in the debug console when positional tracking is unavailable.</span></span> <span data-ttu-id="e0fb4-275">È possibile aggiungere codice a questo gestore a fornire una risposta in base alle esigenze dell'app.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-275">You can add code to this handler to provide a response as needed from your app.</span></span>

<span data-ttu-id="e0fb4-276">Da **AppMain.cpp:**</span><span class="sxs-lookup"><span data-stu-id="e0fb4-276">From **AppMain.cpp:**</span></span>

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

## <a name="spatial-mapping"></a><span data-ttu-id="e0fb4-277">Mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="e0fb4-277">Spatial mapping</span></span>

<span data-ttu-id="e0fb4-278">Il [mapping spaziale](spatial-mapping-in-directx.md) alle API di utilizzo di sistemi di coordinate per ottenere trasformazioni del modello di surface trame.</span><span class="sxs-lookup"><span data-stu-id="e0fb4-278">The [spatial mapping](spatial-mapping-in-directx.md) APIs make use of coordinate systems to get model transforms for surface meshes.</span></span>

## <a name="see-also"></a><span data-ttu-id="e0fb4-279">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e0fb4-279">See also</span></span>
* [<span data-ttu-id="e0fb4-280">Sistemi di coordinate</span><span class="sxs-lookup"><span data-stu-id="e0fb4-280">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="e0fb4-281">Ancoraggi spaziali</span><span class="sxs-lookup"><span data-stu-id="e0fb4-281">Spatial anchors</span></span>](spatial-anchors.md)
* <span data-ttu-id="e0fb4-282"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Anchor spaziali</a></span><span class="sxs-lookup"><span data-stu-id="e0fb4-282"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* [<span data-ttu-id="e0fb4-283">Sguardo, gesti e controller di movimento in DirectX</span><span class="sxs-lookup"><span data-stu-id="e0fb4-283">Gaze, gestures, and motion controllers in DirectX</span></span>](gaze,-gestures,-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="e0fb4-284">Mapping spaziale DirectX</span><span class="sxs-lookup"><span data-stu-id="e0fb4-284">Spatial mapping in DirectX</span></span>](spatial-mapping-in-directx.md)

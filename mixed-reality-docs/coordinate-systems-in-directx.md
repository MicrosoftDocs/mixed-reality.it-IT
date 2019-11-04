---
title: Sistemi di coordinate in DirectX
description: Spiega come usare i localizzatori spaziali di realtà mista di Windows, i frame di riferimento, gli ancoraggi spaziali e i sistemi di coordinate, come usare SpatialStage, come gestire la perdita di rilevamento, come salvare e caricare ancoraggi e come eseguire la stabilizzazione delle immagini.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Realtà mista, localizzatore spaziale, frame di riferimento spaziale, sistema di coordinate spaziali, fase spaziale, codice di esempio, stabilizzazione dell'immagine, ancoraggio spaziale, archivio di ancoraggio spaziale, perdita di tracce, procedura dettagliata
ms.openlocfilehash: a0bce897c1982715af24f0bf7c398cdee10f017f
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436231"
---
# <a name="coordinate-systems-in-directx"></a><span data-ttu-id="5a57e-104">Sistemi di coordinate in DirectX</span><span class="sxs-lookup"><span data-stu-id="5a57e-104">Coordinate systems in DirectX</span></span>

<span data-ttu-id="5a57e-105">I [sistemi di coordinate](coordinate-systems.md) costituiscono la base per la comprensione spaziale offerta dalle API per la realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="5a57e-105">[Coordinate systems](coordinate-systems.md) form the basis for spatial understanding offered by Windows Mixed Reality APIs.</span></span>

<span data-ttu-id="5a57e-106">Gli attuali dispositivi VR o Single-Room VR stabiliscono un sistema di coordinate primario per rappresentare lo spazio rilevato.</span><span class="sxs-lookup"><span data-stu-id="5a57e-106">Today's seated VR or single-room VR devices establish one primary coordinate system to represent their tracked space.</span></span> <span data-ttu-id="5a57e-107">I dispositivi di realtà mista di Windows, ad esempio HoloLens, sono progettati per essere usati in ambienti di grandi dimensioni non definiti, con l'individuazione e l'apprendimento del dispositivo in base all'ambiente in cui l'utente si aggira.</span><span class="sxs-lookup"><span data-stu-id="5a57e-107">Windows Mixed Reality devices such as HoloLens are designed to be used throughout large undefined environments, with the device discovering and learning about its surroundings as the user walks around.</span></span> <span data-ttu-id="5a57e-108">Ciò consente al dispositivo di adattarsi a un miglioramento continuo delle informazioni sulle chat dell'utente, ma comporta sistemi di coordinate che cambieranno la relazione tra loro attraverso la durata dell'app.</span><span class="sxs-lookup"><span data-stu-id="5a57e-108">This allows the device to adapt to continually-improving knowledge about the user's rooms, but results in coordinate systems that will change their relationship to one another through the lifetime of the app.</span></span> <span data-ttu-id="5a57e-109">La realtà mista di Windows supporta un'ampia gamma di dispositivi, spaziando da cuffie immersive sedute attraverso frame di riferimento collegati al mondo.</span><span class="sxs-lookup"><span data-stu-id="5a57e-109">Windows Mixed Reality supports a wide spectrum of devices, ranging from seated immersive headsets through world-attached reference frames.</span></span>

>[!NOTE]
><span data-ttu-id="5a57e-110">I frammenti di codice in questo articolo illustrano attualmente l' C++uso di/CX, invece di/WinRT conformi C++a C + 17 come usato nel modello di [ C++ progetto olografico](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="5a57e-110">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="5a57e-111">I concetti sono equivalenti per C++un progetto/WinRT, anche se sarà necessario tradurre il codice.</span><span class="sxs-lookup"><span data-stu-id="5a57e-111">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="spatial-coordinate-systems-in-windows"></a><span data-ttu-id="5a57e-112">Sistemi di coordinate spaziali in Windows</span><span class="sxs-lookup"><span data-stu-id="5a57e-112">Spatial coordinate systems in Windows</span></span>

<span data-ttu-id="5a57e-113">Il tipo di base usato per ragionare sui sistemi di coordinate reali in Windows è <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>.</span><span class="sxs-lookup"><span data-stu-id="5a57e-113">The core type used to reason about real-world coordinate systems in Windows is the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>.</span></span> <span data-ttu-id="5a57e-114">Un'istanza di questo tipo rappresenta un sistema di coordinate arbitrario e fornisce un metodo per ottenere una matrice di trasformazione che è possibile utilizzare per trasformare tra due sistemi di coordinate senza comprenderne i dettagli.</span><span class="sxs-lookup"><span data-stu-id="5a57e-114">An instance of this type represents an arbitrary coordinate system and provides a method to get a transformation matrix that you can use to transform between two coordinate systems without understanding the details of each.</span></span>

<span data-ttu-id="5a57e-115">I metodi che restituiscono le informazioni spaziali, rappresentate come punti, raggi o volumi nell'ambiente dell'utente, accetteranno un parametro SpatialCoordinateSystem per consentire di decidere il sistema di coordinate in cui è più utile per le coordinate da restituire.</span><span class="sxs-lookup"><span data-stu-id="5a57e-115">Methods that return spatial information, represented as points, rays, or volumes in the user's surroundings, will accept a SpatialCoordinateSystem parameter to let you decide the coordinate system in which it's most useful for those coordinates to be returned.</span></span> <span data-ttu-id="5a57e-116">Le unità per queste coordinate saranno sempre espresse in metri.</span><span class="sxs-lookup"><span data-stu-id="5a57e-116">The units for these coordinates will always be in meters.</span></span>

<span data-ttu-id="5a57e-117">Un SpatialCoordinateSystem ha una relazione dinamica con altri sistemi di coordinate, inclusi quelli che rappresentano la posizione del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5a57e-117">A SpatialCoordinateSystem has a dynamic relationship with other coordinate systems, including those that represent the device's position.</span></span> <span data-ttu-id="5a57e-118">In qualsiasi momento, il dispositivo potrebbe essere in grado di individuare alcuni sistemi di coordinate e non altri.</span><span class="sxs-lookup"><span data-stu-id="5a57e-118">At any point in time, the device may be able to locate some coordinate systems and not others.</span></span> <span data-ttu-id="5a57e-119">Per la maggior parte dei sistemi di coordinate, l'app deve essere pronta per gestire i periodi di tempo durante i quali non possono essere individuati.</span><span class="sxs-lookup"><span data-stu-id="5a57e-119">For most coordinate systems, your app must be ready to handle periods of time during which they cannot be located.</span></span>

<span data-ttu-id="5a57e-120">L'applicazione non deve creare direttamente SpatialCoordinateSystems, bensì deve essere usata tramite le API percettive.</span><span class="sxs-lookup"><span data-stu-id="5a57e-120">Your application should not create SpatialCoordinateSystems directly - rather they should be consumed via the Perception APIs.</span></span> <span data-ttu-id="5a57e-121">Nelle API percettive sono disponibili tre fonti principali di sistemi di coordinate, ciascuna delle quali è mappata a un concetto descritto nella pagina [sistemi di coordinate](coordinate-systems.md) :</span><span class="sxs-lookup"><span data-stu-id="5a57e-121">There are three primary sources of coordinate systems in the Perception APIs, each of which map to a concept described on the [Coordinate systems](coordinate-systems.md) page:</span></span>
* <span data-ttu-id="5a57e-122">Per ottenere un frame di riferimento fisso, creare un <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference</a> o ottenerne uno dalla <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference</a>corrente.</span><span class="sxs-lookup"><span data-stu-id="5a57e-122">To get a stationary frame of reference, create a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference</a> or obtain one from the current <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference</a>.</span></span>
* <span data-ttu-id="5a57e-123">Per ottenere un ancoraggio spaziale, creare un <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>.</span><span class="sxs-lookup"><span data-stu-id="5a57e-123">To get a spatial anchor, create a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>.</span></span>
* <span data-ttu-id="5a57e-124">Per ottenere un frame di riferimento collegato, creare un <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>.</span><span class="sxs-lookup"><span data-stu-id="5a57e-124">To get an attached frame of reference, create a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>.</span></span>

<span data-ttu-id="5a57e-125">Tutti i sistemi di coordinate restituiti da questi oggetti vengono gestiti a destra, con + y su, + x a destra e + z all'indietro.</span><span class="sxs-lookup"><span data-stu-id="5a57e-125">All of the coordinate systems returned by these objects are right-handed, with +y up, +x to the right and +z backwards.</span></span> <span data-ttu-id="5a57e-126">È possibile ricordare quale direzione punta l'asse z positivo puntando le dita della parte sinistra o destra nella direzione x positiva e inserendole nella direzione y positiva.</span><span class="sxs-lookup"><span data-stu-id="5a57e-126">You can remember which direction the positive z-axis points by pointing the fingers of either your left or right hand in the positive x direction and curling them into the positive y direction.</span></span> <span data-ttu-id="5a57e-127">La direzione in cui punta il pollice, verso di te o in direzione opposta, è la direzione a cui punta l’asse z positivo per tale sistema di coordinate.</span><span class="sxs-lookup"><span data-stu-id="5a57e-127">The direction your thumb points, either toward or away from you, is the direction that the positive z-axis points for that coordinate system.</span></span> <span data-ttu-id="5a57e-128">La figura seguente mostra questi due sistemi di coordinate.</span><span class="sxs-lookup"><span data-stu-id="5a57e-128">The following illustration shows these two coordinate systems.</span></span>

<span data-ttu-id="5a57e-129">![sistemi di coordinate a sinistra e a destra](images/left-hand-right-hand.gif)</span><span class="sxs-lookup"><span data-stu-id="5a57e-129">![Left-hand and right-hand coordinate systems](images/left-hand-right-hand.gif)</span></span><br>
<span data-ttu-id="5a57e-130">*Sistemi di coordinate a sinistra e a destra*</span><span class="sxs-lookup"><span data-stu-id="5a57e-130">*Left-hand and right-hand coordinate systems*</span></span>

<span data-ttu-id="5a57e-131">Per eseguire il bootstrap in un SpatialCoordinateSystem in base alla posizione di un HoloLens, usare la classe <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a> per creare un frame di riferimento collegato o fisso, come descritto nelle sezioni riportate di seguito.</span><span class="sxs-lookup"><span data-stu-id="5a57e-131">To bootstrap into a SpatialCoordinateSystem based on the position of a HoloLens, use the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a> class to create either an attached or stationary frame of reference, as described in the sections below.</span></span>

## <a name="place-holograms-in-the-world-using-a-spatial-stage"></a><span data-ttu-id="5a57e-132">Posizionare gli ologrammi in tutto il mondo usando una fase spaziale</span><span class="sxs-lookup"><span data-stu-id="5a57e-132">Place holograms in the world using a spatial stage</span></span>

<span data-ttu-id="5a57e-133">Il sistema di coordinate per gli auricolari a realtà mista di Windows opaco si accede usando la proprietà <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference:: Current</a> statica.</span><span class="sxs-lookup"><span data-stu-id="5a57e-133">The coordinate system for opaque Windows Mixed Reality immersive headsets is accessed using the static <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference::Current</a> property.</span></span> <span data-ttu-id="5a57e-134">Questa API fornisce un sistema di coordinate, informazioni sul fatto che il lettore sia seduto o mobile, il limite di un'area sicura per spostarsi se il lettore è mobile e indica se l'auricolare è direzionale o meno.</span><span class="sxs-lookup"><span data-stu-id="5a57e-134">This API provides a coordinate system, information about whether the player is seated or mobile, the boundary of a safe area for walking around if the player is mobile, and an indication of whether or not the headset is directional.</span></span> <span data-ttu-id="5a57e-135">Per gli aggiornamenti della fase spaziale è inoltre disponibile un gestore eventi.</span><span class="sxs-lookup"><span data-stu-id="5a57e-135">There is also an event handler for updates to the spatial stage.</span></span>

<span data-ttu-id="5a57e-136">Prima di tutto, si ottiene la fase spaziale e si sottoscrive la sottoscrizione degli aggiornamenti:</span><span class="sxs-lookup"><span data-stu-id="5a57e-136">First, we get the spatial stage and subscribe for updates to it:</span></span> 

<span data-ttu-id="5a57e-137">Codice per l' **inizializzazione di una fase spaziale**</span><span class="sxs-lookup"><span data-stu-id="5a57e-137">Code for **Spatial stage initialization**</span></span>

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

<span data-ttu-id="5a57e-138">Nel metodo OnCurrentChanged l'app deve esaminare la fase spaziale e aggiornare di conseguenza l'esperienza del lettore.</span><span class="sxs-lookup"><span data-stu-id="5a57e-138">In the OnCurrentChanged method, your app should inspect the spatial stage and update the player experience accordingly.</span></span> <span data-ttu-id="5a57e-139">In questo esempio viene fornita una visualizzazione del limite della fase, nonché la posizione iniziale specificata dall'utente e l'intervallo di visualizzazione e l'intervallo di proprietà dello spostamento della fase.</span><span class="sxs-lookup"><span data-stu-id="5a57e-139">In this example, we provide a visualization of the stage boundary, as well as the start position specified by the user and the stage's range of view and range of movement properties.</span></span> <span data-ttu-id="5a57e-140">Viene anche eseguito il fallback al nostro sistema di coordinate fisse, quando non è possibile fornire una fase.</span><span class="sxs-lookup"><span data-stu-id="5a57e-140">We also fall back to our own stationary coordinate system, when a stage cannot be provided.</span></span>


<span data-ttu-id="5a57e-141">Codice per l'aggiornamento di una **fase spaziale**</span><span class="sxs-lookup"><span data-stu-id="5a57e-141">Code for **Spatial stage update**</span></span>

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

<span data-ttu-id="5a57e-142">Il set di vertici che definiscono i limiti della fase vengono forniti in ordine orario.</span><span class="sxs-lookup"><span data-stu-id="5a57e-142">The set of vertices that define the stage boundary are provided in clockwise order.</span></span> <span data-ttu-id="5a57e-143">La shell di realtà mista di Windows disegna una recinzione al limite quando l'utente lo avvicina; è possibile che si desideri triangularize l'area a cui è possibile passare per i propri scopi.</span><span class="sxs-lookup"><span data-stu-id="5a57e-143">The Windows Mixed Reality shell draws a fence at the boundary when the user approaches it; you may wish to triangularize the walkable area for your own purposes.</span></span> <span data-ttu-id="5a57e-144">L'algoritmo seguente può essere usato per triangularize la fase.</span><span class="sxs-lookup"><span data-stu-id="5a57e-144">The following algorithm can be used to triangularize the stage.</span></span>


<span data-ttu-id="5a57e-145">Codice per la **triangolazione della fase spaziale**</span><span class="sxs-lookup"><span data-stu-id="5a57e-145">Code for **Spatial stage triangularization**</span></span>

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

## <a name="place-holograms-in-the-world-using-a-stationary-frame-of-reference"></a><span data-ttu-id="5a57e-146">Posizionare gli ologrammi nel mondo usando un frame di riferimento fisso</span><span class="sxs-lookup"><span data-stu-id="5a57e-146">Place holograms in the world using a stationary frame of reference</span></span>

<span data-ttu-id="5a57e-147">La classe [SpatialStationaryFrameOfReference](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialstationaryframeofreference.aspx) rappresenta un frame di riferimento che [rimane stazionario](coordinate-systems.md#stationary-frame-of-reference) rispetto a quello dell'utente quando l'utente si sposta.</span><span class="sxs-lookup"><span data-stu-id="5a57e-147">The [SpatialStationaryFrameOfReference](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialstationaryframeofreference.aspx) class represents a frame of reference that [remains stationary](coordinate-systems.md#stationary-frame-of-reference) relative to the user's surroundings as the user moves around.</span></span> <span data-ttu-id="5a57e-148">Questo frame di riferimento assegna priorità a mantenere le coordinate stabili vicino al dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5a57e-148">This frame of reference prioritizes keeping coordinates stable near the device.</span></span> <span data-ttu-id="5a57e-149">Un uso chiave di un SpatialStationaryFrameOfReference è fungere da sistema di coordinate globale sottostante all'interno di un motore di rendering durante il rendering degli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="5a57e-149">One key use of a SpatialStationaryFrameOfReference is to act as the underlying world coordinate system within a rendering engine when rendering holograms.</span></span>

<span data-ttu-id="5a57e-150">Per ottenere un SpatialStationaryFrameOfReference, usare la classe [SpatialLocator](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.aspx) e chiamare [CreateStationaryFrameOfReferenceAtCurrentLocation](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.createstationaryframeofreferenceatcurrentlocation.aspx).</span><span class="sxs-lookup"><span data-stu-id="5a57e-150">To get a SpatialStationaryFrameOfReference, use the [SpatialLocator](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.aspx) class and call [CreateStationaryFrameOfReferenceAtCurrentLocation](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.createstationaryframeofreferenceatcurrentlocation.aspx).</span></span>

<span data-ttu-id="5a57e-151">Dal codice del modello di applicazione olografica di Windows:</span><span class="sxs-lookup"><span data-stu-id="5a57e-151">From the Windows Holographic app template code:</span></span>

```
           // The simplest way to render world-locked holograms is to create a stationary reference frame
           // when the app is launched. This is roughly analogous to creating a "world" coordinate system
           // with the origin placed at the device's position as the app is launched.
           referenceFrame = locator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```
* <span data-ttu-id="5a57e-152">I frame di riferimento stazionari sono progettati per fornire una posizione più adatta rispetto allo spazio complessivo.</span><span class="sxs-lookup"><span data-stu-id="5a57e-152">Stationary reference frames are designed to provide a best-fit position relative to the overall space.</span></span> <span data-ttu-id="5a57e-153">Le singole posizioni all'interno del frame di riferimento possono essere leggermente derivate.</span><span class="sxs-lookup"><span data-stu-id="5a57e-153">Individual positions within that reference frame are allowed to drift slightly.</span></span> <span data-ttu-id="5a57e-154">Si tratta di una situazione normale quando il dispositivo apprende altre informazioni sull'ambiente.</span><span class="sxs-lookup"><span data-stu-id="5a57e-154">This is normal as the device learns more about the environment.</span></span>
* <span data-ttu-id="5a57e-155">Quando è richiesto un posizionamento preciso dei singoli ologrammi, è consigliabile usare un SpatialAnchor per ancorare il singolo ologramma a una posizione nel mondo reale, ad esempio un punto che l'utente indica di essere di particolare interesse.</span><span class="sxs-lookup"><span data-stu-id="5a57e-155">When precise placement of individual holograms is required, a SpatialAnchor should be used to anchor the individual hologram to a position in the real world - for example, a point the user indicates to be of special interest.</span></span> <span data-ttu-id="5a57e-156">Le posizioni di ancoraggio non sono derivate, ma possono essere corrette; l'ancoraggio utilizzerà la posizione corretta a partire dal fotogramma successivo dopo che è stata eseguita la correzione.</span><span class="sxs-lookup"><span data-stu-id="5a57e-156">Anchor positions do not drift, but can be corrected; the anchor will use the corrected position starting in the next frame after the correction has occurred.</span></span>

## <a name="place-holograms-in-the-world-using-spatial-anchors"></a><span data-ttu-id="5a57e-157">Posizionare gli ologrammi in tutto il mondo usando ancoraggi spaziali</span><span class="sxs-lookup"><span data-stu-id="5a57e-157">Place holograms in the world using spatial anchors</span></span>

<span data-ttu-id="5a57e-158">Gli [ancoraggi spaziali](coordinate-systems.md#spatial-anchors) sono un ottimo modo per collocare gli ologrammi in una posizione specifica nel mondo reale, con il sistema che garantisce che l'ancoraggio rimanga in vigore nel tempo.</span><span class="sxs-lookup"><span data-stu-id="5a57e-158">[Spatial anchors](coordinate-systems.md#spatial-anchors) are a great way to place holograms at a specific place in the real world, with the system ensuring the anchor stays in place over time.</span></span> <span data-ttu-id="5a57e-159">In questo argomento viene illustrato come creare e utilizzare un ancoraggio e come utilizzare i dati di ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="5a57e-159">This topic explains how to create and use an anchor, and how to work with anchor data.</span></span>

<span data-ttu-id="5a57e-160">È possibile creare un SpatialAnchor in qualsiasi posizione e orientamento all'interno della SpatialCoordinateSystem scelta.</span><span class="sxs-lookup"><span data-stu-id="5a57e-160">You can create a SpatialAnchor at any position and orientation within the SpatialCoordinateSystem of your choosing.</span></span> <span data-ttu-id="5a57e-161">Il dispositivo deve essere in grado di individuare il sistema di coordinate al momento e il sistema non deve avere raggiunto il limite di ancoraggi spaziali.</span><span class="sxs-lookup"><span data-stu-id="5a57e-161">The device must be able to locate that coordinate system at the moment, and the system must not have reached its limit of spatial anchors.</span></span>

<span data-ttu-id="5a57e-162">Una volta definito, il sistema di coordinate di un SpatialAnchor si adatta continuamente per mantenere la posizione e l'orientamento precisi della posizione iniziale.</span><span class="sxs-lookup"><span data-stu-id="5a57e-162">Once defined, the coordinate system of a SpatialAnchor adjusts continually to retain the precise position and orientation of its initial location.</span></span> <span data-ttu-id="5a57e-163">È quindi possibile usare questo SpatialAnchor per eseguire il rendering degli ologrammi che appariranno corretti negli ambienti dell'utente nella posizione esatta.</span><span class="sxs-lookup"><span data-stu-id="5a57e-163">You can then use this SpatialAnchor to render holograms that will appear fixed in the user's surroundings at that exact location.</span></span>

<span data-ttu-id="5a57e-164">Gli effetti delle rettifiche che mantengono l'ancoraggio sul posto vengono ingranditi come distanza dall'ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="5a57e-164">The effects of the adjustments that keep the anchor in place are magnified as distance from the anchor increases.</span></span> <span data-ttu-id="5a57e-165">Pertanto, è consigliabile evitare di eseguire il rendering del contenuto relativo a un ancoraggio maggiore di circa 3 metri dall'origine dell'ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="5a57e-165">Therefore, you should avoid rendering content relative to an anchor that is more than about 3 meters from that anchor's origin.</span></span>

<span data-ttu-id="5a57e-166">La proprietà [CoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.coordinatesystem.aspx) ottiene un sistema di coordinate che consente di posizionare il contenuto relativo all'ancoraggio, con l'interpolazione applicata quando il dispositivo regola la posizione esatta dell'ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="5a57e-166">The [CoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.coordinatesystem.aspx) property gets a coordinate system that lets you place content relative to the anchor, with easing applied when the device adjusts the anchor's precise location.</span></span>

<span data-ttu-id="5a57e-167">Utilizzare la proprietà [RawCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystem.aspx) e l'evento [RawCoordinateSystemAdjusted](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted.aspx) corrispondente per gestire manualmente queste modifiche.</span><span class="sxs-lookup"><span data-stu-id="5a57e-167">Use the [RawCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystem.aspx) property and the corresponding [RawCoordinateSystemAdjusted](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted.aspx) event to manage these adjustments yourself.</span></span>

### <a name="persist-and-share-spatial-anchors"></a><span data-ttu-id="5a57e-168">Mantieni e Condividi ancoraggi spaziali</span><span class="sxs-lookup"><span data-stu-id="5a57e-168">Persist and share spatial anchors</span></span>

<span data-ttu-id="5a57e-169">È possibile salvare in locale una SpatialAnchor usando la classe [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx) e quindi riportarla in una sessione di app futura nello stesso dispositivo HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5a57e-169">You can persist a SpatialAnchor locally using the [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx) class and then get it back in a future app session on the same HoloLens device.</span></span>

<span data-ttu-id="5a57e-170">Usando gli <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">ancoraggi spaziali di Azure</a>, è possibile creare un ancoraggio cloud durevole da un SpatialAnchor locale, che può essere individuato dall'app su più dispositivi HoloLens, iOS e Android.</span><span class="sxs-lookup"><span data-stu-id="5a57e-170">By using <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a>, you can create a durable cloud anchor from a local SpatialAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="5a57e-171">Condividendo un ancoraggio spaziale comune tra più dispositivi, ogni utente può visualizzare il contenuto di cui è stato eseguito il rendering relativo a tale ancoraggio nella stessa posizione fisica.</span><span class="sxs-lookup"><span data-stu-id="5a57e-171">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="5a57e-172">Ciò rende possibili esperienze condivise in tempo reale.</span><span class="sxs-lookup"><span data-stu-id="5a57e-172">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="5a57e-173">Puoi usare <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Ancoraggi nello spazio di Azure</a> anche per la persistenza asincrona degli ologrammi su dispositivi HoloLens, iOS e Android.</span><span class="sxs-lookup"><span data-stu-id="5a57e-173">You can also use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="5a57e-174">Condividendo un ancoraggio durevole nello spazio del cloud, più dispositivi possono osservare nel tempo lo stesso ologramma salvato in modo permanente, anche se tali dispositivi non sono presenti insieme contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="5a57e-174">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices are not present together at the same time.</span></span>

<span data-ttu-id="5a57e-175">Per iniziare a creare esperienze condivise nell'app HoloLens, provare la <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Guida introduttiva di Azure Spatial Anchors HoloLens</a>di 5 minuti.</span><span class="sxs-lookup"><span data-stu-id="5a57e-175">To get started building shared experiences in your HoloLens app, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure Spatial Anchors HoloLens quickstart</a>.</span></span>

<span data-ttu-id="5a57e-176">Una volta che si è in esecuzione con gli ancoraggi spaziali di Azure, è possibile <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">creare e individuare ancoraggi in HoloLens</a>.</span><span class="sxs-lookup"><span data-stu-id="5a57e-176">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">create and locate anchors on HoloLens</a>.</span></span>  <span data-ttu-id="5a57e-177">Le procedure dettagliate sono disponibili anche per <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android e iOS</a> , consentendo di condividere gli stessi ancoraggi in tutti i dispositivi.</span><span class="sxs-lookup"><span data-stu-id="5a57e-177">Walkthroughs are available for <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android and iOS</a> as well, enabling you to share the same anchors on all devices.</span></span>

### <a name="create-spatialanchors-for-holographic-content"></a><span data-ttu-id="5a57e-178">Crea SpatialAnchors per contenuto olografico</span><span class="sxs-lookup"><span data-stu-id="5a57e-178">Create SpatialAnchors for holographic content</span></span>

<span data-ttu-id="5a57e-179">Per questo esempio di codice, il modello di applicazione Windows olografico è stato modificato per creare ancoraggi quando viene rilevato il movimento **premuto** .</span><span class="sxs-lookup"><span data-stu-id="5a57e-179">For this code sample, we modified the Windows Holographic app template to create anchors when the **Pressed** gesture is detected.</span></span> <span data-ttu-id="5a57e-180">Il cubo viene quindi inserito in corrispondenza dell'ancoraggio durante il passaggio di rendering.</span><span class="sxs-lookup"><span data-stu-id="5a57e-180">The cube is then placed at the anchor during the render pass.</span></span>

<span data-ttu-id="5a57e-181">Poiché più ancoraggi sono supportati dalla classe helper, è possibile inserire tutti i cubi desiderati usando questo esempio di codice.</span><span class="sxs-lookup"><span data-stu-id="5a57e-181">Since multiple anchors are supported by the helper class, we can place as many cubes as we want using this code sample!</span></span>

<span data-ttu-id="5a57e-182">Si noti che gli ID per gli ancoraggi sono elementi che è possibile controllare nell'app.</span><span class="sxs-lookup"><span data-stu-id="5a57e-182">Note that the IDs for anchors are something you control in your app.</span></span> <span data-ttu-id="5a57e-183">In questo esempio è stato creato uno schema di denominazione sequenziale in base al numero di ancoraggi attualmente archiviati nella raccolta di ancoraggi dell'app.</span><span class="sxs-lookup"><span data-stu-id="5a57e-183">In this example, we have created a naming scheme that is sequential based on the number of anchors currently stored in the app's collection of anchors.</span></span>

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

### <a name="asynchronously-load-and-cache-the-spatialanchorstore"></a><span data-ttu-id="5a57e-184">Caricare e memorizzare nella cache in modo asincrono SpatialAnchorStore</span><span class="sxs-lookup"><span data-stu-id="5a57e-184">Asynchronously load, and cache, the SpatialAnchorStore</span></span>

<span data-ttu-id="5a57e-185">Viene ora illustrato come scrivere una classe SampleSpatialAnchorHelper che consente di gestire questa persistenza, tra cui:</span><span class="sxs-lookup"><span data-stu-id="5a57e-185">Let's see how to write a SampleSpatialAnchorHelper class that helps handle this persistence, including:</span></span>
* <span data-ttu-id="5a57e-186">Archiviazione di una raccolta di ancoraggi in memoria, indicizzati da una chiave Platform:: String.</span><span class="sxs-lookup"><span data-stu-id="5a57e-186">Storing a collection of in-memory anchors, indexed by a Platform::String key.</span></span>
* <span data-ttu-id="5a57e-187">Caricamento di ancoraggi dal SpatialAnchorStore del sistema, mantenuto separato dalla raccolta locale in memoria.</span><span class="sxs-lookup"><span data-stu-id="5a57e-187">Loading anchors from the system's SpatialAnchorStore, which is kept separate from the local in-memory collection.</span></span>
* <span data-ttu-id="5a57e-188">Salvataggio della raccolta in memoria locale degli ancoraggi in SpatialAnchorStore quando l'app sceglie di eseguire questa operazione.</span><span class="sxs-lookup"><span data-stu-id="5a57e-188">Saving the local in-memory collection of anchors to the SpatialAnchorStore when the app chooses to do so.</span></span>

<span data-ttu-id="5a57e-189">Di seguito viene illustrato come salvare gli oggetti [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) in [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).</span><span class="sxs-lookup"><span data-stu-id="5a57e-189">Here's how to save [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) objects in the [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).</span></span>

<span data-ttu-id="5a57e-190">Quando la classe viene avviata, viene richiesto il SpatialAnchorStore in modo asincrono.</span><span class="sxs-lookup"><span data-stu-id="5a57e-190">When the class starts up, we request the SpatialAnchorStore asynchronously.</span></span> <span data-ttu-id="5a57e-191">Ciò implica l'I/O di sistema, perché l'API carica l'archivio di ancoraggio e questa API viene resa asincrona in modo che l'I/O non sia bloccante.</span><span class="sxs-lookup"><span data-stu-id="5a57e-191">This involves system I/O as the API loads the anchor store, and this API is made asynchronous so that the I/O is non-blocking.</span></span>

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

<span data-ttu-id="5a57e-192">Verrà fornito un SpatialAnchorStore che è possibile usare per salvare gli ancoraggi.</span><span class="sxs-lookup"><span data-stu-id="5a57e-192">You will be given a SpatialAnchorStore that you can use to save the anchors.</span></span> <span data-ttu-id="5a57e-193">Si tratta di un IMapView che associa i valori di chiave che sono stringhe, con valori di dati SpatialAnchors.</span><span class="sxs-lookup"><span data-stu-id="5a57e-193">This is an IMapView that associates key values that are Strings, with data values that are SpatialAnchors.</span></span> <span data-ttu-id="5a57e-194">Nel codice di esempio, viene archiviato in una variabile membro della classe privata accessibile tramite una funzione pubblica della classe helper.</span><span class="sxs-lookup"><span data-stu-id="5a57e-194">In our sample code, we store this in a private class member variable that is accessible through a public function of our helper class.</span></span>

```
   SampleSpatialAnchorHelper::SampleSpatialAnchorHelper(SpatialAnchorStore^ anchorStore)
   {
       m_anchorStore = anchorStore;
       m_anchorMap = ref new Platform::Collections::Map<String^, SpatialAnchor^>();
   }
```

>[!NOTE]
><span data-ttu-id="5a57e-195">Non dimenticare di associare gli eventi di sospensione/ripresa per salvare e caricare l'archivio di ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="5a57e-195">Don't forget to hook up the suspend/resume events to save and load the anchor store.</span></span>

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

### <a name="save-content-to-the-anchor-store"></a><span data-ttu-id="5a57e-196">Salva contenuto nell'archivio di ancoraggio</span><span class="sxs-lookup"><span data-stu-id="5a57e-196">Save content to the anchor store</span></span>

<span data-ttu-id="5a57e-197">Quando il sistema sospende l'app, è necessario salvare gli ancoraggi spaziali nell'archivio di ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="5a57e-197">When the system suspends your app, you need to save your spatial anchors to the anchor store.</span></span> <span data-ttu-id="5a57e-198">È anche possibile scegliere di salvare gli ancoraggi nell'archivio di ancoraggio in altri momenti, perché si ritiene che siano necessari per l'implementazione dell'app.</span><span class="sxs-lookup"><span data-stu-id="5a57e-198">You may also choose to save anchors to the anchor store at other times, as you find to be necessary for your app's implementation.</span></span>

<span data-ttu-id="5a57e-199">Quando si è pronti per provare a salvare gli ancoraggi in memoria in SpatialAnchorStore, è possibile eseguire il ciclo della raccolta e provare a salvarli.</span><span class="sxs-lookup"><span data-stu-id="5a57e-199">When you're ready to try saving the in-memory anchors to the SpatialAnchorStore, you can loop through your collection and try to save each one.</span></span>

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

### <a name="load-content-from-the-anchor-store-when-the-app-resumes"></a><span data-ttu-id="5a57e-200">Carica il contenuto dall'archivio di ancoraggio quando l'app riprende</span><span class="sxs-lookup"><span data-stu-id="5a57e-200">Load content from the anchor store when the app resumes</span></span>

<span data-ttu-id="5a57e-201">Quando l'app riprende o in qualsiasi altro momento necessario per il implementaiton dell'app, è possibile ripristinare gli ancoraggi salvati in precedenza nel AnchorStore trasferendo i file dal IMapView dell'archivio di ancoraggio nel database in memoria di SpatialAnchors.</span><span class="sxs-lookup"><span data-stu-id="5a57e-201">When your app resumes, or at any other time necessary for your app's implementaiton, you can restore anchors that were previously saved to the AnchorStore by transferring them from the anchor store's IMapView to your own in-memory database of SpatialAnchors.</span></span>

<span data-ttu-id="5a57e-202">Per ripristinare gli ancoraggi dal SpatialAnchorStore, ripristinare ognuno di essi interessato alla raccolta in memoria.</span><span class="sxs-lookup"><span data-stu-id="5a57e-202">To restore anchors from the SpatialAnchorStore, restore each one that you are interested in to your own in-memory collection.</span></span>

<span data-ttu-id="5a57e-203">È necessario un database in memoria personalizzato di SpatialAnchors; un modo per associare le stringhe al SpatialAnchors creato.</span><span class="sxs-lookup"><span data-stu-id="5a57e-203">You need your own in-memory database of SpatialAnchors; some way to associate Strings with the SpatialAnchors that you create.</span></span> <span data-ttu-id="5a57e-204">Nel codice di esempio si sceglie di usare Windows:: Foundation:: Collections:: IMap per archiviare gli ancoraggi, che semplifica l'uso della stessa chiave e del valore di dati per SpatialAnchorStore.</span><span class="sxs-lookup"><span data-stu-id="5a57e-204">In our sample code, we choose to use a Windows::Foundation::Collections::IMap to store the anchors, which makes it easy to use the same key and data value for the SpatialAnchorStore.</span></span>

```
   // This is an in-memory anchor list that is separate from the anchor store.
   // These anchors may be used, reasoned about, and so on before committing the collection to the store.
   Windows::Foundation::Collections::IMap<Platform::String^, Windows::Perception::Spatial::SpatialAnchor^>^ m_anchorMap;
```

>[!NOTE]
><span data-ttu-id="5a57e-205">Un ancoraggio ripristinato potrebbe non essere locatable immediatamente.</span><span class="sxs-lookup"><span data-stu-id="5a57e-205">An anchor that is restored might not be locatable right away.</span></span> <span data-ttu-id="5a57e-206">Ad esempio, potrebbe trattarsi di un ancoraggio in una stanza separata o in una compilazione diversa.</span><span class="sxs-lookup"><span data-stu-id="5a57e-206">For example, it might be an anchor in a separate room or in a different building altogether.</span></span> <span data-ttu-id="5a57e-207">Gli ancoraggi recuperati da AnchorStore devono essere testati per locatability prima di usarli.</span><span class="sxs-lookup"><span data-stu-id="5a57e-207">Anchors retrieved from the AnchorStore should be tested for locatability before using them.</span></span>

<br>

>[!NOTE]
><span data-ttu-id="5a57e-208">In questo esempio di codice, vengono recuperati tutti gli ancoraggi da AnchorStore.</span><span class="sxs-lookup"><span data-stu-id="5a57e-208">In this example code, we retrieve all anchors from the AnchorStore.</span></span> <span data-ttu-id="5a57e-209">Questo non è un requisito; l'app potrebbe anche selezionare e scegliere un certo subset di ancoraggi usando valori di chiave di stringa significativi per l'implementazione.</span><span class="sxs-lookup"><span data-stu-id="5a57e-209">This is not a requirement; your app could just as well pick and choose a certain subset of anchors by using String key values that are meaningful to your implementation.</span></span>

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

### <a name="clear-the-anchor-store-when-needed"></a><span data-ttu-id="5a57e-210">Cancellare l'archivio di ancoraggio, quando necessario</span><span class="sxs-lookup"><span data-stu-id="5a57e-210">Clear the anchor store, when needed</span></span>

<span data-ttu-id="5a57e-211">In alcuni casi è necessario cancellare lo stato dell'app e scrivere nuovi dati.</span><span class="sxs-lookup"><span data-stu-id="5a57e-211">Sometimes, you need to clear app state and write new data.</span></span> <span data-ttu-id="5a57e-212">Ecco come si esegue questa operazione con [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).</span><span class="sxs-lookup"><span data-stu-id="5a57e-212">Here's how you do that with the [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).</span></span>

<span data-ttu-id="5a57e-213">Con la classe helper è quasi inutile eseguire il wrapping della funzione Clear.</span><span class="sxs-lookup"><span data-stu-id="5a57e-213">Using our helper class, it's almost unnecessary to wrap the Clear function.</span></span> <span data-ttu-id="5a57e-214">Si sceglie di eseguire questa operazione nell'implementazione di esempio, perché la classe helper è responsabile del proprietario dell'istanza di SpatialAnchorStore.</span><span class="sxs-lookup"><span data-stu-id="5a57e-214">We choose to do so in our sample implementation, because our helper class is given the responsibility of owning the SpatialAnchorStore instance.</span></span>

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

### <a name="example-relating-anchor-coordinate-systems-to-stationary-reference-frame-coordinate-systems"></a><span data-ttu-id="5a57e-215">Esempio: correlazione di sistemi di coordinate di ancoraggio a sistemi di coordinate dei frame di riferimento stazionari</span><span class="sxs-lookup"><span data-stu-id="5a57e-215">Example: Relating anchor coordinate systems to stationary reference frame coordinate systems</span></span>

<span data-ttu-id="5a57e-216">Supponiamo di avere un ancoraggio e di voler mettere in relazione un elemento del sistema di coordinate dell'ancoraggio alla SpatialStationaryReferenceFrame che si sta già usando per la maggior parte degli altri contenuti.</span><span class="sxs-lookup"><span data-stu-id="5a57e-216">Let's say that you have an anchor, and you want to relate something in your anchor's coordinate system to the SpatialStationaryReferenceFrame that you’re already using for most of your other content.</span></span> <span data-ttu-id="5a57e-217">È possibile usare [TryGetTransformTo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.trygettransformto.aspx) per ottenere una trasformazione dal sistema di coordinate dell'ancoraggio a quello del frame di riferimento fisso:</span><span class="sxs-lookup"><span data-stu-id="5a57e-217">You can use [TryGetTransformTo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.trygettransformto.aspx) to obtain a transform from the anchor’s coordinate system to that of the stationary reference frame:</span></span>

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

<span data-ttu-id="5a57e-218">Questo processo è utile in due modi:</span><span class="sxs-lookup"><span data-stu-id="5a57e-218">This process is useful to you in two ways:</span></span>
1. <span data-ttu-id="5a57e-219">Indica se i due frame di riferimento possono essere compresi tra loro e;</span><span class="sxs-lookup"><span data-stu-id="5a57e-219">It tells you if the two reference frames can be understood relative to one another, and;</span></span>
2. <span data-ttu-id="5a57e-220">In tal caso, viene fornita una trasformazione per passare direttamente da un sistema di coordinate all'altro.</span><span class="sxs-lookup"><span data-stu-id="5a57e-220">If so, it provides you a transform to go directly from one coordinate system to the other.</span></span>

<span data-ttu-id="5a57e-221">Con queste informazioni, è possibile comprendere la relazione spaziale tra gli oggetti tra i due frame di riferimento.</span><span class="sxs-lookup"><span data-stu-id="5a57e-221">With this information, you have an understanding of the spatial relation between objects between the two reference frames.</span></span>

<span data-ttu-id="5a57e-222">Per il rendering, è spesso possibile ottenere risultati migliori raggruppando gli oggetti in base al frame di riferimento originale o all'ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="5a57e-222">For rendering, you can often obtain better results by grouping objects according to their original reference frame or anchor.</span></span> <span data-ttu-id="5a57e-223">Eseguire un passaggio di disegno separato per ogni gruppo.</span><span class="sxs-lookup"><span data-stu-id="5a57e-223">Perform a separate drawing pass for each group.</span></span> <span data-ttu-id="5a57e-224">Le matrici di visualizzazione sono più accurate per gli oggetti con trasformazioni del modello create inizialmente con lo stesso sistema di coordinate.</span><span class="sxs-lookup"><span data-stu-id="5a57e-224">The view matrices are more accurate for objects with model transforms that are created initially using the same coordinate system.</span></span>

## <a name="create-holograms-using-a-device-attached-frame-of-reference"></a><span data-ttu-id="5a57e-225">Creare ologrammi usando un frame di riferimento collegato al dispositivo</span><span class="sxs-lookup"><span data-stu-id="5a57e-225">Create holograms using a device-attached frame of reference</span></span>

<span data-ttu-id="5a57e-226">In alcuni casi si desidera eseguire il rendering di un ologramma che [rimane collegato](coordinate-systems.md#attached-frame-of-reference) alla posizione del dispositivo, ad esempio un pannello con informazioni di debug o un messaggio informativo quando il dispositivo è in grado di determinare solo l'orientamento e non la posizione in spazio.</span><span class="sxs-lookup"><span data-stu-id="5a57e-226">There are times when you want to render a hologram that [remains attached](coordinate-systems.md#attached-frame-of-reference) to the device's location, for example a panel with debugging information or an informational message when the device is only able to determine its orientation and not its position in space.</span></span> <span data-ttu-id="5a57e-227">A tale scopo, viene usato un frame di riferimento allegato.</span><span class="sxs-lookup"><span data-stu-id="5a57e-227">To accomplish this, we use an attached frame of reference.</span></span>

<span data-ttu-id="5a57e-228">La classe SpatialLocatorAttachedFrameOfReference definisce i sistemi di coordinate relativi al dispositivo anziché al mondo reale.</span><span class="sxs-lookup"><span data-stu-id="5a57e-228">The SpatialLocatorAttachedFrameOfReference class defines coordinate systems which are relative to the device rather than to the real-world.</span></span> <span data-ttu-id="5a57e-229">Questo frame dispone di un'intestazione fissa rispetto all'area circostante dell'utente che punta alla posizione in cui l'utente si trovava al momento della creazione del frame di riferimento.</span><span class="sxs-lookup"><span data-stu-id="5a57e-229">This frame has a fixed heading relative to the user's surroundings that points in the direction the user was facing when the reference frame was created.</span></span> <span data-ttu-id="5a57e-230">Da questo punto in poi, tutti gli orientamenti in questo frame di riferimento sono relativi a tale intestazione fissa, anche quando l'utente ruota il dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5a57e-230">From then on, all orientations in this frame of reference are relative to that fixed heading, even as the user rotates the device.</span></span>

<span data-ttu-id="5a57e-231">Per HoloLens, l'origine del sistema di coordinate del frame si trova al centro della rotazione della testa dell'utente, in modo che la relativa posizione non sia interessata dalla rotazione della testa.</span><span class="sxs-lookup"><span data-stu-id="5a57e-231">For HoloLens, the origin of this frame's coordinate system is located at the center of rotation of the user's head, so that its position is not affected by head rotation.</span></span> <span data-ttu-id="5a57e-232">L'app può specificare un offset rispetto a questo punto per posizionare gli ologrammi davanti all'utente.</span><span class="sxs-lookup"><span data-stu-id="5a57e-232">Your app can specify an offset relative to this point to position holograms in front of the user.</span></span>

<span data-ttu-id="5a57e-233">Per ottenere un SpatialLocatorAttachedFrameOfReference, usare la classe SpatialLocator e chiamare CreateAttachedFrameOfReferenceAtCurrentHeading.</span><span class="sxs-lookup"><span data-stu-id="5a57e-233">To get a SpatialLocatorAttachedFrameOfReference, use the SpatialLocator class and call CreateAttachedFrameOfReferenceAtCurrentHeading.</span></span>

<span data-ttu-id="5a57e-234">Si noti che questo vale per l'intero intervallo di dispositivi di realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="5a57e-234">Note that this applies to the entire range of Windows Mixed Reality devices.</span></span>

### <a name="use-a-reference-frame-attached-to-the-device"></a><span data-ttu-id="5a57e-235">Usare un frame di riferimento collegato al dispositivo</span><span class="sxs-lookup"><span data-stu-id="5a57e-235">Use a reference frame attached to the device</span></span>

<span data-ttu-id="5a57e-236">In queste sezioni vengono illustrate le modifiche apportate al modello di app olografico di Windows per abilitare un frame di riferimento collegato al dispositivo tramite questa API.</span><span class="sxs-lookup"><span data-stu-id="5a57e-236">These sections talk about what we changed in the Windows Holographic app template to enable a device-attached frame of reference using this API.</span></span> <span data-ttu-id="5a57e-237">Si noti che questo ologramma "collegato" funziona insieme a ologrammi fissi o ancorati e può essere usato anche quando il dispositivo non è temporaneamente in grado di trovare la propria posizione nel mondo.</span><span class="sxs-lookup"><span data-stu-id="5a57e-237">Note that this "attached" hologram will work alongside stationary or anchored holograms, and may also be used when the device is temporarily unable to find its position in the world.</span></span>

<span data-ttu-id="5a57e-238">In primo luogo, il modello è stato modificato per archiviare un SpatialLocatorAttachedFrameOfReference anziché un SpatialStationaryFrameOfReference:</span><span class="sxs-lookup"><span data-stu-id="5a57e-238">First, we changed the template to store a SpatialLocatorAttachedFrameOfReference instead of a SpatialStationaryFrameOfReference:</span></span>

<span data-ttu-id="5a57e-239">Da **HolographicTagAlongSampleMain. h**:</span><span class="sxs-lookup"><span data-stu-id="5a57e-239">From **HolographicTagAlongSampleMain.h**:</span></span>

```
   // A reference frame attached to the holographic camera.
   Windows::Perception::Spatial::SpatialLocatorAttachedFrameOfReference^   m_referenceFrame;
```

<span data-ttu-id="5a57e-240">Da **HolographicTagAlongSampleMain. cpp**:</span><span class="sxs-lookup"><span data-stu-id="5a57e-240">From **HolographicTagAlongSampleMain.cpp**:</span></span>

```
   // In this example, we create a reference frame attached to the device.
   m_referenceFrame = m_locator->CreateAttachedFrameOfReferenceAtCurrentHeading();
```

<span data-ttu-id="5a57e-241">Durante l'aggiornamento, viene ora ottenuto il sistema di coordinate al timestamp ottenuto da con la stima del frame.</span><span class="sxs-lookup"><span data-stu-id="5a57e-241">During the update, we now obtain the coordinate system at the time stamp obtained from with the frame prediction.</span></span>

```
   // Next, we get a coordinate system from the attached frame of reference that is
   // associated with the current frame. Later, this coordinate system is used for
   // for creating the stereo view matrices when rendering the sample content.
   SpatialCoordinateSystem^ currentCoordinateSystem =
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp);
```

### <a name="get-a-spatial-pointer-pose-and-follow-the-users-gaze"></a><span data-ttu-id="5a57e-242">Ottenere un indicatore di misura spaziale e seguire lo sguardo dell'utente</span><span class="sxs-lookup"><span data-stu-id="5a57e-242">Get a spatial pointer pose, and follow the user's Gaze</span></span>

<span data-ttu-id="5a57e-243">Si vuole che l'ologramma di esempio segua lo [sguardo](gaze-and-commit.md)dell'utente, in modo analogo a come la shell olografica può seguire lo sguardo dell'utente.</span><span class="sxs-lookup"><span data-stu-id="5a57e-243">We want our example hologram to follow the user's [gaze](gaze-and-commit.md), similar to how the holographic shell can follow the user's gaze.</span></span> <span data-ttu-id="5a57e-244">A questo punto, è necessario ottenere il SpatialPointerPose dallo stesso timestamp.</span><span class="sxs-lookup"><span data-stu-id="5a57e-244">For this, we need to get the SpatialPointerPose from the same time stamp.</span></span>

```
SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
```

<span data-ttu-id="5a57e-245">Questo SpatialPointerPose contiene le informazioni necessarie per posizionare l'ologramma in base all' [intestazione corrente dell'utente](gaze-in-directx.md).</span><span class="sxs-lookup"><span data-stu-id="5a57e-245">This SpatialPointerPose has the information needed to position the hologram according to the [user's current heading](gaze-in-directx.md).</span></span>

<span data-ttu-id="5a57e-246">Per motivi di comodità dell'utente, viene usata l'interpolazione lineare ("Lerp") per smussare la modifica nella posizione in modo tale che si verifichi in un determinato periodo di tempo.</span><span class="sxs-lookup"><span data-stu-id="5a57e-246">For reasons of user comfort, we use linear interpolation ("lerp") to smooth the change in position such that it occurs over a period of time.</span></span> <span data-ttu-id="5a57e-247">Si tratta di un'operazione più comoda per l'utente rispetto al blocco degli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="5a57e-247">This is more comfortable for the user than locking the hologram to their gaze.</span></span> <span data-ttu-id="5a57e-248">Lerping la posizione dell'ologramma tag-along consente anche di stabilizzare l'ologramma smorzando il movimento; Se questa operazione non è stata eseguita, l'utente vedrà la jitter dell'ologramma a causa di ciò che in genere è considerato un movimento impercettibile della testa dell'utente.</span><span class="sxs-lookup"><span data-stu-id="5a57e-248">Lerping the tag-along hologram's position also allows us to stabilize the hologram by dampening the movement; if we did not do this dampening, the user would see the hologram jitter because of what are normally considered to be imperceptible movements of the user's head.</span></span>

<span data-ttu-id="5a57e-249">Da **StationaryQuadRenderer::P ositionhologram**:</span><span class="sxs-lookup"><span data-stu-id="5a57e-249">From **StationaryQuadRenderer::PositionHologram**:</span></span>

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
><span data-ttu-id="5a57e-250">Nel caso di un pannello di debug, è possibile scegliere di riposizionare l'ologramma sul lato leggermente, in modo che non ostacoli la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="5a57e-250">In the case of a debugging panel, you might choose to reposition the hologram off to the side a little so that it does not obstruct your view.</span></span> <span data-ttu-id="5a57e-251">Ecco un esempio di come è possibile eseguire questa operazione.</span><span class="sxs-lookup"><span data-stu-id="5a57e-251">Here's an example of how you might do that.</span></span>

<span data-ttu-id="5a57e-252">Per **StationaryQuadRenderer::P ositionhologram**:</span><span class="sxs-lookup"><span data-stu-id="5a57e-252">For **StationaryQuadRenderer::PositionHologram**:</span></span>

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

### <a name="rotate-the-hologram-to-face-the-camera"></a><span data-ttu-id="5a57e-253">Ruotare l'ologramma per far fronte alla fotocamera</span><span class="sxs-lookup"><span data-stu-id="5a57e-253">Rotate the hologram to face the camera</span></span>

<span data-ttu-id="5a57e-254">Non è sufficiente posizionare semplicemente l'ologramma, che in questo caso è un quad; è anche necessario ruotare l'oggetto per far fronte all'utente.</span><span class="sxs-lookup"><span data-stu-id="5a57e-254">It is not enough to simply position the hologram, which in this case is a quad; we must also rotate the object to face the user.</span></span> <span data-ttu-id="5a57e-255">Si noti che questa rotazione si verifica nello spazio globale, perché questo tipo di tabellone consente all'ologramma di rimanere parte dell'ambiente dell'utente.</span><span class="sxs-lookup"><span data-stu-id="5a57e-255">Note that this rotation occurs in world space, because this type of billboarding allows the hologram to remain a part of the user's environment.</span></span> <span data-ttu-id="5a57e-256">Il tabellone degli spazi di visualizzazione non è altrettanto comodo perché l'ologramma viene bloccato sull'orientamento della visualizzazione. in tal caso, è anche necessario interpolare tra le matrici di visualizzazione a sinistra e a destra per acquisire una trasformazione di Billboard dello spazio di visualizzazione che non interrompa il rendering stereo.</span><span class="sxs-lookup"><span data-stu-id="5a57e-256">View-space billboarding is not as comfortable because the hologram becomes locked to the display orientation; in that case, you would also have to interpolate between the left and right view matrices in order to acquire a view-space billboard transform that does not disrupt stereo rendering.</span></span> <span data-ttu-id="5a57e-257">In questo caso, gli assi X e Z vengono ruotati in modo da far fronte all'utente.</span><span class="sxs-lookup"><span data-stu-id="5a57e-257">Here, we rotate on the X and Z axes to face the user.</span></span>

<span data-ttu-id="5a57e-258">Da **StationaryQuadRenderer:: Update**:</span><span class="sxs-lookup"><span data-stu-id="5a57e-258">From **StationaryQuadRenderer::Update**:</span></span>

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

### <a name="render-the-attached-hologram"></a><span data-ttu-id="5a57e-259">Eseguire il rendering dell'ologramma collegato</span><span class="sxs-lookup"><span data-stu-id="5a57e-259">Render the attached hologram</span></span>

<span data-ttu-id="5a57e-260">Per questo esempio, si sceglie anche di eseguire il rendering dell'ologramma nel sistema di coordinate del SpatialLocatorAttachedReferenceFrame, che è il punto in cui è stato posizionato l'ologramma.</span><span class="sxs-lookup"><span data-stu-id="5a57e-260">For this example, we also choose to render the hologram in the coordinate system of the SpatialLocatorAttachedReferenceFrame, which is where we positioned the hologram.</span></span> <span data-ttu-id="5a57e-261">(Se si è deciso di eseguire il rendering usando un altro sistema di coordinate, è necessario acquisire una trasformazione dal sistema di coordinate del frame di riferimento collegato al dispositivo a tale sistema di coordinate).</span><span class="sxs-lookup"><span data-stu-id="5a57e-261">(If we had decided to render using another coordinate system, we would need to acquire a transform from the device-attached reference frame's coordinate system to that coordinate system.)</span></span>

<span data-ttu-id="5a57e-262">Da **HolographicTagAlongSampleMain:: Render**:</span><span class="sxs-lookup"><span data-stu-id="5a57e-262">From **HolographicTagAlongSampleMain::Render**:</span></span>

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

<span data-ttu-id="5a57e-263">Ecco fatto!</span><span class="sxs-lookup"><span data-stu-id="5a57e-263">That's it!</span></span> <span data-ttu-id="5a57e-264">L'ologramma ora "inseguisce" una posizione che è di 2 metri davanti alla direzione dello sguardo dell'utente.</span><span class="sxs-lookup"><span data-stu-id="5a57e-264">The hologram will now "chase" a position that is 2 meters in front of the user's gaze direction.</span></span>

>[!NOTE]
><span data-ttu-id="5a57e-265">Questo esempio carica anche contenuto aggiuntivo. vedere StationaryQuadRenderer. cpp.</span><span class="sxs-lookup"><span data-stu-id="5a57e-265">This example also loads additional content - see StationaryQuadRenderer.cpp.</span></span>

## <a name="handling-tracking-loss"></a><span data-ttu-id="5a57e-266">Gestione della perdita di rilevamento</span><span class="sxs-lookup"><span data-stu-id="5a57e-266">Handling tracking loss</span></span>

<span data-ttu-id="5a57e-267">Quando il dispositivo non è in grado di trovarsi nel mondo, l'app riscontra una "perdita di rilevamento".</span><span class="sxs-lookup"><span data-stu-id="5a57e-267">When the device cannot locate itself in the world, the app experiences "tracking loss".</span></span> <span data-ttu-id="5a57e-268">Le app per la realtà mista di Windows dovrebbero essere in grado di gestire tali rotture per il sistema di rilevamento posizionale.</span><span class="sxs-lookup"><span data-stu-id="5a57e-268">Windows Mixed Reality apps should be able to handle such disruptions to the positional tracking system.</span></span> <span data-ttu-id="5a57e-269">Queste rotture possono essere osservate e le risposte create usando l'evento LocatabilityChanged sul SpatialLocator predefinito.</span><span class="sxs-lookup"><span data-stu-id="5a57e-269">These disruptions can be observed, and responses created, by using the LocatabilityChanged event on the default SpatialLocator.</span></span>

<span data-ttu-id="5a57e-270">Da **AppMain:: SetHolographicSpace:**</span><span class="sxs-lookup"><span data-stu-id="5a57e-270">From **AppMain::SetHolographicSpace:**</span></span>

```
   // Be able to respond to changes in the positional tracking state.
   m_locatabilityChangedToken =
       m_locator->LocatabilityChanged +=
           ref new Windows::Foundation::TypedEventHandler<SpatialLocator^, Object^>(
               std::bind(&HolographicApp1Main::OnLocatabilityChanged, this, _1, _2)
               );
```

<span data-ttu-id="5a57e-271">Quando l'app riceve un evento LocatabilityChanged, può modificare il comportamento in base alle esigenze.</span><span class="sxs-lookup"><span data-stu-id="5a57e-271">When your app receives a LocatabilityChanged event, it can change behavior as needed.</span></span> <span data-ttu-id="5a57e-272">Ad esempio, nello stato PositionalTrackingInhibited, l'app può sospendere l'operazione normale ed eseguire il rendering di un [ologramma con tag lungo](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) che visualizza un messaggio di avviso.</span><span class="sxs-lookup"><span data-stu-id="5a57e-272">For example, in the PositionalTrackingInhibited state, your app can pause normal operation and render a [tag-along hologram](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) that displays a warning message.</span></span>

<span data-ttu-id="5a57e-273">Il modello di app olografico di Windows viene creato con un gestore LocatabilityChanged già creato automaticamente.</span><span class="sxs-lookup"><span data-stu-id="5a57e-273">The Windows Holographic app template comes with a LocatabilityChanged handler already created for you.</span></span> <span data-ttu-id="5a57e-274">Per impostazione predefinita, viene visualizzato un avviso nella console di debug quando il rilevamento posizionale non è disponibile.</span><span class="sxs-lookup"><span data-stu-id="5a57e-274">By default, it displays a warning in the debug console when positional tracking is unavailable.</span></span> <span data-ttu-id="5a57e-275">È possibile aggiungere codice a questo gestore per fornire una risposta in base alle esigenze dell'app.</span><span class="sxs-lookup"><span data-stu-id="5a57e-275">You can add code to this handler to provide a response as needed from your app.</span></span>

<span data-ttu-id="5a57e-276">Da **AppMain. cpp:**</span><span class="sxs-lookup"><span data-stu-id="5a57e-276">From **AppMain.cpp:**</span></span>

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

## <a name="spatial-mapping"></a><span data-ttu-id="5a57e-277">Mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="5a57e-277">Spatial mapping</span></span>

<span data-ttu-id="5a57e-278">Le API di [mapping spaziale](spatial-mapping-in-directx.md) utilizzano i sistemi di coordinate per ottenere le trasformazioni del modello per le mesh di superficie.</span><span class="sxs-lookup"><span data-stu-id="5a57e-278">The [spatial mapping](spatial-mapping-in-directx.md) APIs make use of coordinate systems to get model transforms for surface meshes.</span></span>

## <a name="see-also"></a><span data-ttu-id="5a57e-279">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="5a57e-279">See also</span></span>
* [<span data-ttu-id="5a57e-280">Sistemi di coordinate</span><span class="sxs-lookup"><span data-stu-id="5a57e-280">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="5a57e-281">Ancoraggi nello spazio</span><span class="sxs-lookup"><span data-stu-id="5a57e-281">Spatial anchors</span></span>](spatial-anchors.md)
* <span data-ttu-id="5a57e-282"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Ancoraggi nello spazio di Azure</a></span><span class="sxs-lookup"><span data-stu-id="5a57e-282"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* [<span data-ttu-id="5a57e-283">Puntamento con la testa e sguardo fisso in DirectX</span><span class="sxs-lookup"><span data-stu-id="5a57e-283">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="5a57e-284">Mani e controller del movimento in DirectX</span><span class="sxs-lookup"><span data-stu-id="5a57e-284">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="5a57e-285">Mapping spaziale in DirectX</span><span class="sxs-lookup"><span data-stu-id="5a57e-285">Spatial mapping in DirectX</span></span>](spatial-mapping-in-directx.md)

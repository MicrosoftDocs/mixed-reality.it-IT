---
title: Mapping spaziale in DirectX
description: Viene illustrato come implementare il mapping spaziale nell'app DirectX. Questo include una spiegazione dettagliata dell'applicazione di esempio di mapping spaziale inclusa con l'SDK piattaforma UWP (Universal Windows Platform).
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, mapping spaziale, ambiente, interazione, DirectX, WinRT, API, codice di esempio, UWP, SDK, procedura dettagliata
ms.openlocfilehash: db3f1464158c04127e456cadd5fb633336909344
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63550692"
---
# <a name="spatial-mapping-in-directx"></a><span data-ttu-id="7ae55-105">Mapping spaziale in DirectX</span><span class="sxs-lookup"><span data-stu-id="7ae55-105">Spatial mapping in DirectX</span></span>

<span data-ttu-id="7ae55-106">Questo argomento descrive come implementare il [mapping spaziale](spatial-mapping.md) nell'app DirectX.</span><span class="sxs-lookup"><span data-stu-id="7ae55-106">This topic describes how to implement [spatial mapping](spatial-mapping.md) in your DirectX app.</span></span> <span data-ttu-id="7ae55-107">Questo include una spiegazione dettagliata dell'applicazione di esempio di mapping spaziale inclusa con l'SDK piattaforma UWP (Universal Windows Platform).</span><span class="sxs-lookup"><span data-stu-id="7ae55-107">This includes a detailed explanation of the spatial mapping sample application that is included with the Universal Windows Platform SDK.</span></span>

<span data-ttu-id="7ae55-108">Questo argomento usa il codice dell'esempio di codice UWP di [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) .</span><span class="sxs-lookup"><span data-stu-id="7ae55-108">This topic uses code from the [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) UWP code sample.</span></span>

>[!NOTE]
><span data-ttu-id="7ae55-109">I frammenti di codice in questo articolo illustrano attualmente l' C++uso di/CX, invece di/WinRT conformi C++a C + 17 come usato nel modello di [ C++ progetto olografico](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="7ae55-109">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="7ae55-110">I concetti sono equivalenti per C++un progetto/WinRT, anche se sarà necessario tradurre il codice.</span><span class="sxs-lookup"><span data-stu-id="7ae55-110">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="directx-development-overview"></a><span data-ttu-id="7ae55-111">Panoramica sullo sviluppo di DirectX</span><span class="sxs-lookup"><span data-stu-id="7ae55-111">DirectX development overview</span></span>

<span data-ttu-id="7ae55-112">Lo sviluppo di applicazioni native per il mapping spaziale USA le API nello spazio dei nomi [Windows. Perception. Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) .</span><span class="sxs-lookup"><span data-stu-id="7ae55-112">Native application development for spatial mapping uses the APIs under the [Windows.Perception.Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) namespace.</span></span> <span data-ttu-id="7ae55-113">Queste API offrono il controllo completo della funzionalità di mapping spaziale, in modo direttamente analogo alle API di mapping spaziale esposte da [Unity](spatial-mapping-in-unity.md).</span><span class="sxs-lookup"><span data-stu-id="7ae55-113">These APIs provide full control of spatial mapping functionality, in a manner directly analogous to the spatial mapping APIs exposed by [Unity](spatial-mapping-in-unity.md).</span></span>

### <a name="perception-apis"></a><span data-ttu-id="7ae55-114">API di percezione</span><span class="sxs-lookup"><span data-stu-id="7ae55-114">Perception APIs</span></span>

<span data-ttu-id="7ae55-115">I tipi primari forniti per lo sviluppo di mapping spaziale sono i seguenti:</span><span class="sxs-lookup"><span data-stu-id="7ae55-115">The primary types provided for spatial mapping development are as follows:</span></span>
* <span data-ttu-id="7ae55-116">[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) fornisce informazioni sulle superfici in aree di spazio specificate dall'applicazione in prossimità dell'utente, sotto forma di oggetti SpatialSurfaceInfo.</span><span class="sxs-lookup"><span data-stu-id="7ae55-116">[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) provides information about surfaces in application-specified regions of space near the user, in the form of SpatialSurfaceInfo objects.</span></span>
* <span data-ttu-id="7ae55-117">[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) descrive una singola superficie spaziale esistente, incluso un ID univoco, il volume di delimitazione e l'ora dell'Ultima modifica.</span><span class="sxs-lookup"><span data-stu-id="7ae55-117">[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) describes a single extant spatial surface, including a unique ID, bounding volume and time of last change.</span></span> <span data-ttu-id="7ae55-118">Fornirà un SpatialSurfaceMesh in modo asincrono su richiesta.</span><span class="sxs-lookup"><span data-stu-id="7ae55-118">It will provide a SpatialSurfaceMesh asynchronously upon request.</span></span>
* <span data-ttu-id="7ae55-119">[SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) contiene i parametri usati per personalizzare gli oggetti SpatialSurfaceMesh richiesti da SpatialSurfaceInfo.</span><span class="sxs-lookup"><span data-stu-id="7ae55-119">[SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) contains parameters used to customize the SpatialSurfaceMesh objects requested from SpatialSurfaceInfo.</span></span>
* <span data-ttu-id="7ae55-120">[SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) rappresenta i dati mesh per una singola superficie spaziale.</span><span class="sxs-lookup"><span data-stu-id="7ae55-120">[SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) represents the mesh data for a single spatial surface.</span></span> <span data-ttu-id="7ae55-121">I dati per le posizioni del vertice, le normali dei vertici e gli indici dei triangoli sono contenuti negli oggetti SpatialSurfaceMeshBuffer del membro.</span><span class="sxs-lookup"><span data-stu-id="7ae55-121">The data for vertex positions, vertex normals and triangle indices is contained in member SpatialSurfaceMeshBuffer objects.</span></span>
* <span data-ttu-id="7ae55-122">[SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) esegue il wrapping di un singolo tipo di dati mesh.</span><span class="sxs-lookup"><span data-stu-id="7ae55-122">[SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) wraps a single type of mesh data.</span></span>

<span data-ttu-id="7ae55-123">Quando si sviluppa un'applicazione con queste API, il flusso del programma di base sarà simile al seguente (come illustrato nell'applicazione di esempio descritta di seguito):</span><span class="sxs-lookup"><span data-stu-id="7ae55-123">When developing an application using these APIs, your basic program flow will look like this (as demonstrated in the sample application described below):</span></span>
- <span data-ttu-id="7ae55-124">**Configurare il SpatialSurfaceObserver**</span><span class="sxs-lookup"><span data-stu-id="7ae55-124">**Set up your SpatialSurfaceObserver**</span></span>
  - <span data-ttu-id="7ae55-125">Chiamare [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx)per assicurarsi che l'utente disponga dell'autorizzazione per l'uso delle funzionalità di mapping spaziale del dispositivo da parte dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="7ae55-125">Call [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx), to ensure that the user has given permission for your application to use the device's spatial mapping capabilities.</span></span>
  - <span data-ttu-id="7ae55-126">Creare un'istanza di un oggetto SpatialSurfaceObserver.</span><span class="sxs-lookup"><span data-stu-id="7ae55-126">Instantiate a SpatialSurfaceObserver object.</span></span>
  - <span data-ttu-id="7ae55-127">Chiamare [SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) per specificare le aree di spazio in cui si desiderano informazioni sulle superfici spaziali.</span><span class="sxs-lookup"><span data-stu-id="7ae55-127">Call [SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) to specify the regions of space in which you want information about spatial surfaces.</span></span> <span data-ttu-id="7ae55-128">È possibile modificare queste aree in futuro chiamando semplicemente questa funzione.</span><span class="sxs-lookup"><span data-stu-id="7ae55-128">You may modify these regions in the future by simply calling this function again.</span></span> <span data-ttu-id="7ae55-129">Ogni area viene specificata usando un [SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx).</span><span class="sxs-lookup"><span data-stu-id="7ae55-129">Each region is specified using a [SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx).</span></span>
  - <span data-ttu-id="7ae55-130">Eseguire la registrazione per l'evento [ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) , che verrà attivato ogni volta che sono disponibili nuove informazioni sulle superfici spaziali nelle aree di spazio specificate.</span><span class="sxs-lookup"><span data-stu-id="7ae55-130">Register for the [ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) event, which will fire whenever new information is available about the spatial surfaces in the regions of space you have specified.</span></span>
- <span data-ttu-id="7ae55-131">**Elabora eventi ObservedSurfacesChanged**</span><span class="sxs-lookup"><span data-stu-id="7ae55-131">**Process ObservedSurfacesChanged events**</span></span>
  - <span data-ttu-id="7ae55-132">Nel gestore eventi chiamare [GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) per ricevere una mappa di oggetti SpatialSurfaceInfo.</span><span class="sxs-lookup"><span data-stu-id="7ae55-132">In your event handler, call [GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) to receive a map of SpatialSurfaceInfo objects.</span></span> <span data-ttu-id="7ae55-133">Utilizzando questa mappa, è possibile aggiornare i record delle superfici spaziali [presenti nell'ambiente dell'utente](spatial-mapping.md#mesh-caching).</span><span class="sxs-lookup"><span data-stu-id="7ae55-133">Using this map, you can update your records of which spatial surfaces [exist in the user's environment](spatial-mapping.md#mesh-caching).</span></span>
  - <span data-ttu-id="7ae55-134">Per ogni oggetto SpatialSurfaceInfo, è possibile eseguire una query su [TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) per determinare gli extent spaziali della superficie, espressa in un [sistema di coordinate spaziali](coordinate-systems.md) a scelta.</span><span class="sxs-lookup"><span data-stu-id="7ae55-134">For each SpatialSurfaceInfo object, you may query [TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) to determine the spatial extents of the surface, expressed in a [spatial coordinate system](coordinate-systems.md) of your choosing.</span></span>
  - <span data-ttu-id="7ae55-135">Se si decide di richiedere una mesh per una superficie spaziale, chiamare [TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx).</span><span class="sxs-lookup"><span data-stu-id="7ae55-135">If you decide to request mesh for a spatial surface, call [TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx).</span></span> <span data-ttu-id="7ae55-136">È possibile specificare opzioni che specificano la densità desiderata dei triangoli e il formato dei dati della mesh restituiti.</span><span class="sxs-lookup"><span data-stu-id="7ae55-136">You may provide options specifying the desired density of triangles, and the format of the returned mesh data.</span></span>
- <span data-ttu-id="7ae55-137">**Rete di ricezione ed elaborazione**</span><span class="sxs-lookup"><span data-stu-id="7ae55-137">**Receive and process mesh**</span></span>
  - <span data-ttu-id="7ae55-138">Ogni chiamata a TryComputeLatestMeshAsync restituirà aysnchronously un oggetto SpatialSurfaceMesh.</span><span class="sxs-lookup"><span data-stu-id="7ae55-138">Each call to TryComputeLatestMeshAsync will aysnchronously return one SpatialSurfaceMesh object.</span></span>
  - <span data-ttu-id="7ae55-139">Da questo oggetto è possibile accedere agli oggetti SpatialSurfaceMeshBuffer contenuti per accedere agli indici triangolari, alle posizioni dei vertici e alle normali del vertice, se richiesti, della mesh.</span><span class="sxs-lookup"><span data-stu-id="7ae55-139">From this object you can access the contained SpatialSurfaceMeshBuffer objects in order to access the triangle indices, vertex positions and (if requested) vertex normals of the mesh.</span></span> <span data-ttu-id="7ae55-140">Questi dati saranno in un formato compatibile direttamente con le [API Direct3D 11](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) usate per il rendering dei mesh.</span><span class="sxs-lookup"><span data-stu-id="7ae55-140">This data will be in a format directly compatible with the [Direct3D 11 APIs](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) used for rendering meshes.</span></span>
  - <span data-ttu-id="7ae55-141">Da qui l'applicazione può facoltativamente eseguire l'analisi o l' [elaborazione](spatial-mapping.md#mesh-processing) dei dati di rete e usarla per il [rendering](spatial-mapping.md#rendering) e la Raycasting fisica [e il conflitto](spatial-mapping.md#raycasting-and-collision).</span><span class="sxs-lookup"><span data-stu-id="7ae55-141">From here your application can optionally perform analysis or [processing](spatial-mapping.md#mesh-processing) of the mesh data, and use it for [rendering](spatial-mapping.md#rendering) and physics [raycasting and collision](spatial-mapping.md#raycasting-and-collision).</span></span>
  - <span data-ttu-id="7ae55-142">Un dettaglio importante da tenere presente è che è necessario applicare una scala alle posizioni dei vertici della mesh, ad esempio nel vertex shader usato per il rendering delle mesh, per convertirle dalle unità Integer ottimizzate in cui sono archiviate nel buffer, ai contatori.</span><span class="sxs-lookup"><span data-stu-id="7ae55-142">One important detail to note is that you must apply a scale to the mesh vertex positions (for example in the vertex shader used for rendering the meshes), to convert them from the optimized integer units in which they are stored in the buffer, to meters.</span></span> <span data-ttu-id="7ae55-143">È possibile recuperare questa scala chiamando [VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx).</span><span class="sxs-lookup"><span data-stu-id="7ae55-143">You can retrieve this scale by calling [VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx).</span></span>

### <a name="troubleshooting"></a><span data-ttu-id="7ae55-144">Risoluzione dei problemi</span><span class="sxs-lookup"><span data-stu-id="7ae55-144">Troubleshooting</span></span>
* <span data-ttu-id="7ae55-145">Non dimenticare di ridimensionare le posizioni dei vertici mesh nel vertex shader, usando la scala restituita da [SpatialSurfaceMesh. VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)</span><span class="sxs-lookup"><span data-stu-id="7ae55-145">Don't forget to scale mesh vertex positions in your vertex shader, using the scale returned by [SpatialSurfaceMesh.VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)</span></span>

## <a name="spatial-mapping-code-sample-walkthrough"></a><span data-ttu-id="7ae55-146">Procedura dettagliata di esempio di codice di mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="7ae55-146">Spatial Mapping code sample walkthrough</span></span>

<span data-ttu-id="7ae55-147">L'esempio di codice di [mapping spaziale olografico](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) include codice che è possibile usare per iniziare a caricare mesh di superficie nell'app, inclusa l'infrastruttura per la gestione e il rendering di mesh di superficie.</span><span class="sxs-lookup"><span data-stu-id="7ae55-147">The [Holographic Spatial Mapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) code sample includes code that you can use to get started loading surface meshes into your app, including infrastructure for managing and rendering surface meshes.</span></span>

<span data-ttu-id="7ae55-148">A questo punto, viene illustrato come aggiungere la funzionalità di mapping della superficie all'app DirectX.</span><span class="sxs-lookup"><span data-stu-id="7ae55-148">Now, we walk through how to add surface mapping capability to your DirectX app.</span></span> <span data-ttu-id="7ae55-149">È possibile aggiungere questo codice al progetto di [modello di app Windows olografico](creating-a-holographic-directx-project.md) oppure è possibile seguire l'esempio di codice riportato in precedenza.</span><span class="sxs-lookup"><span data-stu-id="7ae55-149">You can add this code to your [Windows Holographic app template](creating-a-holographic-directx-project.md) project, or you can follow along by browsing through the code sample mentioned above.</span></span> <span data-ttu-id="7ae55-150">Questo esempio di codice è basato sul modello di app olografico di Windows.</span><span class="sxs-lookup"><span data-stu-id="7ae55-150">This code sample is based on the Windows Holographic app template.</span></span>

### <a name="set-up-your-app-to-use-the-spatialperception-capability"></a><span data-ttu-id="7ae55-151">Configurare l'app per l'uso della funzionalità spatialPerception</span><span class="sxs-lookup"><span data-stu-id="7ae55-151">Set up your app to use the spatialPerception capability</span></span>

<span data-ttu-id="7ae55-152">L'app deve essere in grado di usare la funzionalità di mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="7ae55-152">Your app must be able to use the spatial mapping capability.</span></span> <span data-ttu-id="7ae55-153">Questa operazione è necessaria perché la mesh spaziale è una rappresentazione dell'ambiente dell'utente, che può essere considerato dati privati.</span><span class="sxs-lookup"><span data-stu-id="7ae55-153">This is necessary because the spatial mesh is a representation of the user's environment, which may be considered private data.</span></span> <span data-ttu-id="7ae55-154">Dichiarare questa funzionalità nel file Package. appxmanifest per l'app.</span><span class="sxs-lookup"><span data-stu-id="7ae55-154">Declare this capability in the package.appxmanifest file for your app.</span></span> <span data-ttu-id="7ae55-155">Di seguito è riportato un esempio:</span><span class="sxs-lookup"><span data-stu-id="7ae55-155">Here's an example:</span></span>

```xml
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

<span data-ttu-id="7ae55-156">La funzionalità deriva dallo spazio dei nomi **uap2** .</span><span class="sxs-lookup"><span data-stu-id="7ae55-156">The capability comes from the **uap2** namespace.</span></span> <span data-ttu-id="7ae55-157">Per ottenere l'accesso a questo spazio dei nomi nel manifesto, includerlo come attributo *xlmns* nell' &lt;elemento > del pacchetto.</span><span class="sxs-lookup"><span data-stu-id="7ae55-157">To get access to this namespace in your manifest, include it as an *xlmns* attribute in the &lt;Package> element.</span></span> <span data-ttu-id="7ae55-158">Di seguito è riportato un esempio:</span><span class="sxs-lookup"><span data-stu-id="7ae55-158">Here's an example:</span></span>

```xml
<Package
    xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap uap2 mp"
    >
```

### <a name="check-for-spatial-mapping-feature-support"></a><span data-ttu-id="7ae55-159">Verificare il supporto della funzionalità di mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="7ae55-159">Check for spatial mapping feature support</span></span>

<span data-ttu-id="7ae55-160">La realtà mista di Windows supporta un'ampia gamma di dispositivi, inclusi i dispositivi che non supportano il mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="7ae55-160">Windows Mixed Reality supports a wide range of devices, including devices which do not support spatial mapping.</span></span> <span data-ttu-id="7ae55-161">Se l'app può usare il mapping spaziale o deve usare il mapping spaziale per fornire funzionalità, deve verificare che il mapping spaziale sia supportato prima di provare a usarlo.</span><span class="sxs-lookup"><span data-stu-id="7ae55-161">If your app can use spatial mapping, or must use spatial mapping, to provide functionality, it should check to make sure that spatial mapping is supported before trying to use it.</span></span> <span data-ttu-id="7ae55-162">Se, ad esempio, il mapping spaziale è richiesto dall'app per la realtà mista, viene visualizzato un messaggio in tal senso se un utente prova a eseguirlo su un dispositivo senza mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="7ae55-162">For example, if spatial mapping is required by your mixed reality app, it should display a message to that effect if a user tries running it on a device without spatial mapping.</span></span> <span data-ttu-id="7ae55-163">In alternativa, l'app potrebbe essere in grado di eseguire il rendering del proprio ambiente virtuale al posto dell'ambiente dell'utente, offrendo un'esperienza simile a quella che sarebbe accaduto se fosse disponibile il mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="7ae55-163">Or, your app may be able to render its own virtual environment in place of the user's environment, providing an experience that is similar to what would happen if spatial mapping were available.</span></span> <span data-ttu-id="7ae55-164">In ogni caso, questa API consente all'app di essere a conoscenza del momento in cui non otterrà dati di mapping spaziali e risponderà nel modo appropriato.</span><span class="sxs-lookup"><span data-stu-id="7ae55-164">In any event, this API allows your app to be aware of when it will not get spatial mapping data and respond in the appropriate way.</span></span>

<span data-ttu-id="7ae55-165">Per controllare il dispositivo corrente per il supporto del mapping spaziale, verificare prima di tutto che il contratto UWP sia al livello 4 o superiore, quindi chiamare SpatialSurfaceObserver:: di supporto ().</span><span class="sxs-lookup"><span data-stu-id="7ae55-165">To check the current device for spatial mapping support, first make sure the UWP contract is at level 4 or greater and then call SpatialSurfaceObserver::IsSupported().</span></span> <span data-ttu-id="7ae55-166">Di seguito viene illustrato come eseguire questa operazione nel contesto dell'esempio di codice di [mapping spaziale olografico](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) .</span><span class="sxs-lookup"><span data-stu-id="7ae55-166">Here's how to do so in the context of the [Holographic Spatial Mapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) code sample.</span></span> <span data-ttu-id="7ae55-167">Il supporto viene verificato immediatamente prima di richiedere l'accesso.</span><span class="sxs-lookup"><span data-stu-id="7ae55-167">Support is checked just before requesting access.</span></span>

<span data-ttu-id="7ae55-168">L'API SpatialSurfaceObserver:: di supporto () è disponibile a partire dalla versione 15063 dell'SDK.</span><span class="sxs-lookup"><span data-stu-id="7ae55-168">The SpatialSurfaceObserver::IsSupported() API is available starting in SDK version 15063.</span></span> <span data-ttu-id="7ae55-169">Se necessario, ridestinare il progetto alla versione della piattaforma 15063 prima di usare questa API.</span><span class="sxs-lookup"><span data-stu-id="7ae55-169">If necessary, retarget your project to platform version 15063 before using this API.</span></span>

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

<span data-ttu-id="7ae55-170">Si noti che quando il contratto UWP è inferiore al livello 4, l'app deve continuare come se il dispositivo fosse in grado di eseguire il mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="7ae55-170">Note that when the UWP contract is less than level 4, the app should proceed as though the device is capable of doing spatial mapping.</span></span>

### <a name="request-access-to-spatial-mapping-data"></a><span data-ttu-id="7ae55-171">Richiedere l'accesso ai dati di mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="7ae55-171">Request access to spatial mapping data</span></span>

<span data-ttu-id="7ae55-172">L'app deve richiedere l'autorizzazione per accedere ai dati di mapping spaziale prima di provare a creare gli osservatori di superficie.</span><span class="sxs-lookup"><span data-stu-id="7ae55-172">Your app needs to request permission to access spatial mapping data before trying to create any surface observers.</span></span> <span data-ttu-id="7ae55-173">Di seguito è riportato un esempio basato sull'esempio di codice Surface mapping, con ulteriori dettagli disponibili più avanti in questa pagina:</span><span class="sxs-lookup"><span data-stu-id="7ae55-173">Here's an example based upon our Surface Mapping code sample, with more details provided later on this page:</span></span>

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

### <a name="create-a-surface-observer"></a><span data-ttu-id="7ae55-174">Creare un osservatore di superficie</span><span class="sxs-lookup"><span data-stu-id="7ae55-174">Create a surface observer</span></span>

<span data-ttu-id="7ae55-175">Lo spazio dei nomi **Windows::P erception:: Spatial:: Surfaces** include la classe [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) , che osserva uno o più volumi specificati in un [SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx).</span><span class="sxs-lookup"><span data-stu-id="7ae55-175">The **Windows::Perception::Spatial::Surfaces** namespace includes the [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) class, which observes one or more volumes that you specify in a [SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx).</span></span> <span data-ttu-id="7ae55-176">Usare un'istanza di [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) per accedere ai dati di Surface Mesh in tempo reale.</span><span class="sxs-lookup"><span data-stu-id="7ae55-176">Use a [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) instance to access surface mesh data in real time.</span></span>

<span data-ttu-id="7ae55-177">Da **AppMain. h**:</span><span class="sxs-lookup"><span data-stu-id="7ae55-177">From **AppMain.h**:</span></span>

```cpp
// Obtains surface mapping data from the device in real time.
Windows::Perception::Spatial::Surfaces::SpatialSurfaceObserver^     m_surfaceObserver;
Windows::Perception::Spatial::Surfaces::SpatialSurfaceMeshOptions^  m_surfaceMeshOptions;
```

<span data-ttu-id="7ae55-178">Come indicato nella sezione precedente, è necessario richiedere l'accesso ai dati di mapping spaziale prima che l'app possa usarla.</span><span class="sxs-lookup"><span data-stu-id="7ae55-178">As noted in the previous section, you must request access to spatial mapping data before your app can use it.</span></span> <span data-ttu-id="7ae55-179">Questo accesso viene concesso automaticamente in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7ae55-179">This access is granted automatically on the HoloLens.</span></span>

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

<span data-ttu-id="7ae55-180">Successivamente, è necessario configurare l'osservatore della superficie per osservare un volume di delimitazione specifico.</span><span class="sxs-lookup"><span data-stu-id="7ae55-180">Next, you need to configure the surface observer to observe a specific bounding volume.</span></span> <span data-ttu-id="7ae55-181">Qui viene osservato un riquadro 20x20x5 metri, centrato sull'origine del sistema di coordinate.</span><span class="sxs-lookup"><span data-stu-id="7ae55-181">Here, we observe a box that is 20x20x5 meters, centered at the origin of the coordinate system.</span></span>

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

<span data-ttu-id="7ae55-182">Si noti che è invece possibile impostare più volumi di delimitazione.</span><span class="sxs-lookup"><span data-stu-id="7ae55-182">Note that you can set multiple bounding volumes instead.</span></span>

<span data-ttu-id="7ae55-183">*Si tratta di pseudocodice:*</span><span class="sxs-lookup"><span data-stu-id="7ae55-183">*This is pseudocode:*</span></span>

```cpp
m_surfaceObserver->SetBoundingVolumes(/* iterable collection of bounding volumes*/);
```

<span data-ttu-id="7ae55-184">È anche possibile usare altre forme di delimitazione, ad esempio una vista tronco, o un rettangolo di delimitazione che non è allineato all'asse.</span><span class="sxs-lookup"><span data-stu-id="7ae55-184">It is also possible to use other bounding shapes - such as a view frustum, or a bounding box that is not axis aligned.</span></span>

<span data-ttu-id="7ae55-185">*Si tratta di pseudocodice:*</span><span class="sxs-lookup"><span data-stu-id="7ae55-185">*This is pseudocode:*</span></span>

```cpp
m_surfaceObserver->SetBoundingVolume(
            SpatialBoundingVolume::FromFrustum(/*SpatialCoordinateSystem*/, /*SpatialBoundingFrustum*/)
            );
```

<span data-ttu-id="7ae55-186">Se l'app deve eseguire operazioni in modo diverso quando i dati di mapping di superficie non sono disponibili, è possibile scrivere codice per rispondere al caso in cui il [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) non è **consentito** , ad esempio, non sarà consentito nei PC con immersive dispositivi collegati perché i dispositivi non hanno hardware per il mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="7ae55-186">If your app needs to do anything differently when surface mapping data is not available, you can write code to respond to the case where the [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) is not **Allowed** - for example, it will not be allowed on PCs with immersive devices attached because those devices don't have hardware for spatial mapping.</span></span> <span data-ttu-id="7ae55-187">Per questi dispositivi, è invece necessario basarsi sulla fase spaziale per ottenere informazioni sull'ambiente e la configurazione del dispositivo dell'utente.</span><span class="sxs-lookup"><span data-stu-id="7ae55-187">For these devices, you should instead rely on the spatial stage for information about the user's environment and device configuration.</span></span>

### <a name="initialize-and-update-the-surface-mesh-collection"></a><span data-ttu-id="7ae55-188">Inizializzare e aggiornare la raccolta Surface Mesh</span><span class="sxs-lookup"><span data-stu-id="7ae55-188">Initialize and update the surface mesh collection</span></span>

<span data-ttu-id="7ae55-189">Se l'osservatore della superficie è stato creato correttamente, è possibile procedere con l'inizializzazione della raccolta di mesh della superficie.</span><span class="sxs-lookup"><span data-stu-id="7ae55-189">If the surface observer was successfully created, we can proceed to initialize our surface mesh collection.</span></span> <span data-ttu-id="7ae55-190">Qui viene usata l'API del modello pull per ottenere immediatamente il set corrente di superfici osservate:</span><span class="sxs-lookup"><span data-stu-id="7ae55-190">Here, we use the pull model API to get the current set of observed surfaces right away:</span></span>

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

<span data-ttu-id="7ae55-191">Per ottenere i dati di Surface Mesh è disponibile anche un modello push.</span><span class="sxs-lookup"><span data-stu-id="7ae55-191">There is also a push model available to get surface mesh data.</span></span> <span data-ttu-id="7ae55-192">È possibile progettare l'applicazione in modo che usi solo il modello pull, se si sceglie, nel qual caso verrà eseguito il polling dei dati ogni tanto spesso, ad esempio per ogni fotogramma o durante un periodo di tempo specifico, ad esempio durante l'installazione del gioco.</span><span class="sxs-lookup"><span data-stu-id="7ae55-192">You are free to design your app to use only the pull model if you choose, in which case you'll poll for data every so often - say, once per frame - or during a specific time period, such as during game setup.</span></span> <span data-ttu-id="7ae55-193">In tal caso, il codice precedente è quello che ti serve.</span><span class="sxs-lookup"><span data-stu-id="7ae55-193">If so, the above code is what you need.</span></span>

<span data-ttu-id="7ae55-194">Nell'esempio di codice si è scelto di illustrare l'uso di entrambi i modelli a scopo pedagogico.</span><span class="sxs-lookup"><span data-stu-id="7ae55-194">In our code sample, we chose to demonstrate the use of both models for pedagogical purposes.</span></span> <span data-ttu-id="7ae55-195">Qui viene sottoscritto un evento per ricevere dati di Surface Mesh aggiornati ogni volta che il sistema riconosce una modifica.</span><span class="sxs-lookup"><span data-stu-id="7ae55-195">Here, we subscribe to an event to receive up-to-date surface mesh data whenever the system recognizes a change.</span></span>

```cpp
m_surfaceObserver->ObservedSurfacesChanged += ref new TypedEventHandler<SpatialSurfaceObserver^, Platform::Object^>(
            bind(&HolographicDesktopAppMain::OnSurfacesChanged, this, _1, _2)
            );
```

<span data-ttu-id="7ae55-196">Il codice di esempio è inoltre configurato per rispondere a questi eventi.</span><span class="sxs-lookup"><span data-stu-id="7ae55-196">Our code sample is also configured to respond to these events.</span></span> <span data-ttu-id="7ae55-197">Esaminiamo ora come eseguire questa operazione.</span><span class="sxs-lookup"><span data-stu-id="7ae55-197">Let's walk through how we do this.</span></span>

<span data-ttu-id="7ae55-198">**NOTA:** Questo potrebbe non essere il modo più efficiente per gestire i dati della mesh nell'app.</span><span class="sxs-lookup"><span data-stu-id="7ae55-198">**NOTE:** This might not be the most efficient way for your app to handle mesh data.</span></span> <span data-ttu-id="7ae55-199">Questo codice viene scritto per maggiore chiarezza e non è ottimizzato.</span><span class="sxs-lookup"><span data-stu-id="7ae55-199">This code is written for clarity and is not optimized.</span></span>

<span data-ttu-id="7ae55-200">I dati della superficie mesh sono disponibili in una mappa di sola lettura che archivia gli oggetti [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) usando [Platform:: GUID](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) come valori chiave.</span><span class="sxs-lookup"><span data-stu-id="7ae55-200">The surface mesh data is provided in a read-only map that stores [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) objects using [Platform::Guids](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) as key values.</span></span>

```cpp
IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection = sender->GetObservedSurfaces();
```

<span data-ttu-id="7ae55-201">Per elaborare questi dati, si cerca prima i valori di chiave che non sono presenti nella raccolta.</span><span class="sxs-lookup"><span data-stu-id="7ae55-201">To process this data, we look first for key values that aren't in our collection.</span></span> <span data-ttu-id="7ae55-202">Informazioni dettagliate sulla modalità di archiviazione dei dati nell'app di esempio verranno illustrate più avanti in questo argomento.</span><span class="sxs-lookup"><span data-stu-id="7ae55-202">Details on how the data is stored in our sample app will be presented later in this topic.</span></span>

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

<span data-ttu-id="7ae55-203">È anche necessario rimuovere le mesh di superficie presenti nella raccolta di mesh della superficie, ma che non sono più presenti nella raccolta di sistema.</span><span class="sxs-lookup"><span data-stu-id="7ae55-203">We also have to remove surface meshes that are in our surface mesh collection, but that aren't in the system collection anymore.</span></span> <span data-ttu-id="7ae55-204">A tale scopo, è necessario eseguire un'operazione analoga al contrario di quanto appena illustrato per l'aggiunta e l'aggiornamento delle mesh; viene visualizzato un ciclo nella raccolta dell'app e viene verificato se il **GUID** è presente nella raccolta di sistema.</span><span class="sxs-lookup"><span data-stu-id="7ae55-204">To do so, we need to do something akin to the opposite of what we just showed for adding and updating meshes; we loop on our app's collection, and check to see if the **Guid** we have is in the system collection.</span></span> <span data-ttu-id="7ae55-205">Se non è presente nella raccolta di sistema, viene rimossa dalla nostra.</span><span class="sxs-lookup"><span data-stu-id="7ae55-205">If it's not in the system collection, we remove it from ours.</span></span>

<span data-ttu-id="7ae55-206">Dal gestore eventi in AppMain. cpp:</span><span class="sxs-lookup"><span data-stu-id="7ae55-206">From our event handler in AppMain.cpp:</span></span>

```cpp
m_meshCollection->PruneMeshCollection(surfaceCollection);
```

<span data-ttu-id="7ae55-207">Implementazione della potatura mesh in RealtimeSurfaceMeshRenderer. cpp:</span><span class="sxs-lookup"><span data-stu-id="7ae55-207">The implementation of mesh pruning in RealtimeSurfaceMeshRenderer.cpp:</span></span>

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

### <a name="acquire-and-use-surface-mesh-data-buffers"></a><span data-ttu-id="7ae55-208">Acquisire e usare i buffer di dati di Surface Mesh</span><span class="sxs-lookup"><span data-stu-id="7ae55-208">Acquire and use surface mesh data buffers</span></span>

<span data-ttu-id="7ae55-209">Il recupero delle informazioni sulla mesh della superficie è semplice quanto il pull di una raccolta di dati e l'elaborazione degli aggiornamenti in tale raccolta.</span><span class="sxs-lookup"><span data-stu-id="7ae55-209">Getting the surface mesh information was as easy as pulling a data collection and processing updates to that collection.</span></span> <span data-ttu-id="7ae55-210">A questo punto, verranno fornite informazioni dettagliate su come è possibile usare i dati.</span><span class="sxs-lookup"><span data-stu-id="7ae55-210">Now, we'll go into detail on how you can use the data.</span></span>

<span data-ttu-id="7ae55-211">Nell'esempio di codice si è scelto di usare le mesh di superficie per il rendering.</span><span class="sxs-lookup"><span data-stu-id="7ae55-211">In our code example, we chose to use the surface meshes for rendering.</span></span> <span data-ttu-id="7ae55-212">Si tratta di uno scenario comune per gli ologrammi occlusione dietro le superfici reali.</span><span class="sxs-lookup"><span data-stu-id="7ae55-212">This is a common scenario for occluding holograms behind real-world surfaces.</span></span> <span data-ttu-id="7ae55-213">È anche possibile eseguire il rendering delle mesh o eseguire il rendering delle versioni elaborate di tali mesh per mostrare all'utente quali aree della chat vengono analizzate prima di iniziare a fornire funzionalità per app o giochi.</span><span class="sxs-lookup"><span data-stu-id="7ae55-213">You can also render the meshes, or render processed versions of them, to show the user what areas of the room are scanned before you start providing app or game functionality.</span></span>

<span data-ttu-id="7ae55-214">L'esempio di codice avvia il processo quando riceve gli aggiornamenti di Surface Mesh dal gestore eventi descritto nella sezione precedente.</span><span class="sxs-lookup"><span data-stu-id="7ae55-214">The code sample starts the process when it receives surface mesh updates from the event handler that we described in the previous section.</span></span> <span data-ttu-id="7ae55-215">La riga di codice importante in questa funzione è la chiamata a Update the Surface *mesh*: da questo momento abbiamo già elaborato le informazioni di mesh e stiamo per ottenere i dati relativi ai vertici e agli indici da usare nel modo appropriato.</span><span class="sxs-lookup"><span data-stu-id="7ae55-215">The important line of code in this function is the call to update the surface *mesh*: by this time we have already processed the mesh info, and we are about to get the vertex and index data for use as we see fit.</span></span>

<span data-ttu-id="7ae55-216">Da RealtimeSurfaceMeshRenderer. cpp:</span><span class="sxs-lookup"><span data-stu-id="7ae55-216">From RealtimeSurfaceMeshRenderer.cpp:</span></span>

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

<span data-ttu-id="7ae55-217">Il codice di esempio è progettato in modo che una classe di dati, **SurfaceMesh**, gestisca l'elaborazione e il rendering dei dati di rete.</span><span class="sxs-lookup"><span data-stu-id="7ae55-217">Our sample code is designed so that a data class, **SurfaceMesh**, handles mesh data processing and rendering.</span></span> <span data-ttu-id="7ae55-218">Questi mesh sono gli elementi di cui **RealtimeSurfaceMeshRenderer** mantiene effettivamente una mappa.</span><span class="sxs-lookup"><span data-stu-id="7ae55-218">These meshes are what the **RealtimeSurfaceMeshRenderer** actually keeps a map of.</span></span> <span data-ttu-id="7ae55-219">Ognuno di essi contiene un riferimento al SpatialSurfaceMesh da cui proviene e viene usato ogni volta che è necessario accedere al vertice mesh o ai buffer di indice oppure ottenere una trasformazione per la mesh.</span><span class="sxs-lookup"><span data-stu-id="7ae55-219">Each one has a reference to the SpatialSurfaceMesh it came from, and we use it any time that we need to access the mesh vertex or index buffers, or get a transform for the mesh.</span></span> <span data-ttu-id="7ae55-220">Per il momento, la mesh viene contrassegnata in modo da richiedere un aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="7ae55-220">For now, we flag the mesh as needing an update.</span></span>

<span data-ttu-id="7ae55-221">Da SurfaceMesh. cpp:</span><span class="sxs-lookup"><span data-stu-id="7ae55-221">From SurfaceMesh.cpp:</span></span>

```cpp
void SurfaceMesh::UpdateSurface(SpatialSurfaceMesh^ surfaceMesh)
{
    m_surfaceMesh = surfaceMesh;
    m_updateNeeded = true;
}
```

<span data-ttu-id="7ae55-222">Alla successiva richiesta di tracciatura da parte della mesh, il flag verrà prima controllato.</span><span class="sxs-lookup"><span data-stu-id="7ae55-222">Next time the mesh is asked to draw itself, it will check the flag first.</span></span> <span data-ttu-id="7ae55-223">Se è necessario un aggiornamento, i buffer di Vertex e index verranno aggiornati nella GPU.</span><span class="sxs-lookup"><span data-stu-id="7ae55-223">If an update is needed, the vertex and index buffers will be updated on the GPU.</span></span>

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

<span data-ttu-id="7ae55-224">In primo luogo, vengono acquisiti i buffer di dati non elaborati:</span><span class="sxs-lookup"><span data-stu-id="7ae55-224">First, we acquire the raw data buffers:</span></span>

```cpp
Windows::Storage::Streams::IBuffer^ positions = m_surfaceMesh->VertexPositions->Data;
    Windows::Storage::Streams::IBuffer^ normals   = m_surfaceMesh->VertexNormals->Data;
    Windows::Storage::Streams::IBuffer^ indices   = m_surfaceMesh->TriangleIndices->Data;
```

<span data-ttu-id="7ae55-225">Quindi, creiamo buffer del dispositivo Direct3D con i dati mesh forniti da HoloLens:</span><span class="sxs-lookup"><span data-stu-id="7ae55-225">Then, we create Direct3D device buffers with the mesh data provided by the HoloLens:</span></span>

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

<span data-ttu-id="7ae55-226">**NOTA:** Per la funzione helper CreateDirectXBuffer usata nel frammento di codice precedente, vedere l'esempio di codice di mapping di Surface: SurfaceMesh. cpp, GetDataFromIBuffer. h.</span><span class="sxs-lookup"><span data-stu-id="7ae55-226">**NOTE:** For the CreateDirectXBuffer helper function used in the previous snippet, see the Surface Mapping code sample: SurfaceMesh.cpp, GetDataFromIBuffer.h.</span></span> <span data-ttu-id="7ae55-227">A questo punto, la creazione delle risorse del dispositivo è stata completata e il mesh viene considerato caricato e pronto per l'aggiornamento e il rendering.</span><span class="sxs-lookup"><span data-stu-id="7ae55-227">Now the device resource creation is complete, and the mesh is considered to be loaded and ready for update and render.</span></span>

### <a name="update-and-render-surface-meshes"></a><span data-ttu-id="7ae55-228">Aggiornare ed eseguire il rendering delle mesh di superficie</span><span class="sxs-lookup"><span data-stu-id="7ae55-228">Update and render surface meshes</span></span>

<span data-ttu-id="7ae55-229">La classe SurfaceMesh dispone di una funzione di aggiornamento specializzata.</span><span class="sxs-lookup"><span data-stu-id="7ae55-229">Our SurfaceMesh class has a specialized update function.</span></span> <span data-ttu-id="7ae55-230">Ogni [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) ha una propria trasformazione e l'esempio usa il sistema di coordinate corrente per il **SpatialStationaryReferenceFrame** per acquisire la trasformazione.</span><span class="sxs-lookup"><span data-stu-id="7ae55-230">Each [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) has its own transform, and our sample uses the current coordinate system for our **SpatialStationaryReferenceFrame** to acquire the transform.</span></span> <span data-ttu-id="7ae55-231">Aggiorna quindi il buffer costante del modello nella GPU.</span><span class="sxs-lookup"><span data-stu-id="7ae55-231">Then it updates the model constant buffer on the GPU.</span></span>

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

<span data-ttu-id="7ae55-232">Quando è il momento di eseguire il rendering delle mesh della superficie, le operazioni di preparazione vengono eseguite prima del rendering della raccolta.</span><span class="sxs-lookup"><span data-stu-id="7ae55-232">When it's time to render surface meshes, we do some prep work before rendering the collection.</span></span> <span data-ttu-id="7ae55-233">Viene configurata la pipeline dello shader per la configurazione di rendering corrente e viene configurata la fase dell'assembler di input.</span><span class="sxs-lookup"><span data-stu-id="7ae55-233">We set up the shader pipeline for the current rendering configuration, and we set up the input assembler stage.</span></span> <span data-ttu-id="7ae55-234">Si noti che la classe helper della fotocamera olografica **CameraResources. cpp** ha già configurato il buffer costante di visualizzazione/proiezione da ora.</span><span class="sxs-lookup"><span data-stu-id="7ae55-234">Note that the holographic camera helper class **CameraResources.cpp** already has set up the view/projection constant buffer by now.</span></span>

<span data-ttu-id="7ae55-235">Da **RealtimeSurfaceMeshRenderer:: Render**:</span><span class="sxs-lookup"><span data-stu-id="7ae55-235">From **RealtimeSurfaceMeshRenderer::Render**:</span></span>

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

<span data-ttu-id="7ae55-236">Al termine di questa operazione, viene eseguito il loop sulle mesh e si indica a ognuno di disegnarlo.</span><span class="sxs-lookup"><span data-stu-id="7ae55-236">Once this is done, we loop on our meshes and tell each one to draw itself.</span></span> <span data-ttu-id="7ae55-237">**NOTA:** Questo codice di esempio non è ottimizzato per l'uso di qualsiasi tipo di eliminazione di tronco, ma è necessario includere questa funzionalità nell'app.</span><span class="sxs-lookup"><span data-stu-id="7ae55-237">**NOTE:** This sample code is not optimized to use any sort of frustum culling, but you should include this feature in your app.</span></span>

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

<span data-ttu-id="7ae55-238">Le singole mesh sono responsabili della configurazione del buffer di Vertex e index buffer, stride e della trasformazione del modello.</span><span class="sxs-lookup"><span data-stu-id="7ae55-238">The individual meshes are responsible for setting up the vertex and index buffer, stride, and model transform constant buffer.</span></span> <span data-ttu-id="7ae55-239">Come per il cubo rotante nel modello di app olografico di Windows, viene eseguito il rendering nei buffer stereoscopici usando le istanze.</span><span class="sxs-lookup"><span data-stu-id="7ae55-239">As with the spinning cube in the Windows Holographic app template, we render to stereoscopic buffers using instancing.</span></span>

<span data-ttu-id="7ae55-240">Da **SurfaceMesh::D RAW**:</span><span class="sxs-lookup"><span data-stu-id="7ae55-240">From **SurfaceMesh::Draw**:</span></span>

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

### <a name="rendering-choices-with-surface-mapping"></a><span data-ttu-id="7ae55-241">Opzioni di rendering con mapping di superficie</span><span class="sxs-lookup"><span data-stu-id="7ae55-241">Rendering choices with Surface Mapping</span></span>

<span data-ttu-id="7ae55-242">Il codice di esempio Surface mapping fornisce il codice per il rendering di solo occlusione dei dati di Surface Mesh e per il rendering su schermo dei dati della superficie mesh.</span><span class="sxs-lookup"><span data-stu-id="7ae55-242">The Surface Mapping code sample offers code for occlusion-only rendering of surface mesh data, and for on-screen rendering of surface mesh data.</span></span> <span data-ttu-id="7ae55-243">Il percorso scelto, o entrambi, dipende dall'applicazione.</span><span class="sxs-lookup"><span data-stu-id="7ae55-243">Which path you choose - or both - depends on your application.</span></span> <span data-ttu-id="7ae55-244">In questo documento verranno illustrate in dettaglio entrambe le configurazioni.</span><span class="sxs-lookup"><span data-stu-id="7ae55-244">We'll walk through both configurations in this document.</span></span>

<span data-ttu-id="7ae55-245">**Rendering dei buffer di occlusione per effetto olografico**</span><span class="sxs-lookup"><span data-stu-id="7ae55-245">**Rendering occlusion buffers for holographic effect**</span></span>

<span data-ttu-id="7ae55-246">Per iniziare, deselezionare la visualizzazione della destinazione di rendering per la fotocamera virtuale corrente.</span><span class="sxs-lookup"><span data-stu-id="7ae55-246">Start by clearing the render target view for the current virtual camera.</span></span>

<span data-ttu-id="7ae55-247">Da AppMain. cpp:</span><span class="sxs-lookup"><span data-stu-id="7ae55-247">From AppMain.cpp:</span></span>

```cpp
context->ClearRenderTargetView(pCameraResources->GetBackBufferRenderTargetView(), DirectX::Colors::Transparent);
```

<span data-ttu-id="7ae55-248">Si tratta di un passaggio di pre-rendering.</span><span class="sxs-lookup"><span data-stu-id="7ae55-248">This is a "pre-rendering" pass.</span></span> <span data-ttu-id="7ae55-249">Qui viene creato un buffer di occlusione chiedendo al renderer mesh di eseguire il rendering solo della profondità.</span><span class="sxs-lookup"><span data-stu-id="7ae55-249">Here, we create an occlusion buffer by asking the mesh renderer to render only depth.</span></span> <span data-ttu-id="7ae55-250">In questa configurazione non viene collegata una visualizzazione della destinazione di rendering e il renderer di mesh imposta la fase pixel shader su **nullptr** in modo che la GPU non preferisca disegnare pixel.</span><span class="sxs-lookup"><span data-stu-id="7ae55-250">In this configuration, we don't attach a render target view, and the mesh renderer sets the pixel shader stage to **nullptr** so that the GPU doesn't bother to draw pixels.</span></span> <span data-ttu-id="7ae55-251">La geometria verrà rasterizzata nel buffer di profondità e la pipeline grafica verrà arrestata.</span><span class="sxs-lookup"><span data-stu-id="7ae55-251">The geometry will be rasterized to the depth buffer, and the graphics pipeline will stop there.</span></span>

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

<span data-ttu-id="7ae55-252">È possibile creare ologrammi con un test di profondità aggiuntivo sul buffer di occlusione del mapping della superficie.</span><span class="sxs-lookup"><span data-stu-id="7ae55-252">We can draw holograms with an extra depth test against the Surface Mapping occlusion buffer.</span></span> <span data-ttu-id="7ae55-253">In questo esempio di codice viene eseguito il rendering dei pixel sul cubo con un colore diverso se si trovano dietro una superficie.</span><span class="sxs-lookup"><span data-stu-id="7ae55-253">In this code sample, we render pixels on the cube a different color if they are behind a surface.</span></span>

<span data-ttu-id="7ae55-254">Da AppMain. cpp:</span><span class="sxs-lookup"><span data-stu-id="7ae55-254">From AppMain.cpp:</span></span>

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

<span data-ttu-id="7ae55-255">In base al codice di SpecialEffectPixelShader. HLSL:</span><span class="sxs-lookup"><span data-stu-id="7ae55-255">Based on code from SpecialEffectPixelShader.hlsl:</span></span>

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

<span data-ttu-id="7ae55-256">**Nota:** Per la routine **GatherDepthLess** , vedere l'esempio di codice di mapping di Surface: SpecialEffectPixelShader. HLSL.</span><span class="sxs-lookup"><span data-stu-id="7ae55-256">**Note:** For our **GatherDepthLess** routine, see the Surface Mapping code sample: SpecialEffectPixelShader.hlsl.</span></span>

<span data-ttu-id="7ae55-257">**Rendering dei dati di Surface Mesh sullo schermo**</span><span class="sxs-lookup"><span data-stu-id="7ae55-257">**Rendering surface mesh data to the display**</span></span>

<span data-ttu-id="7ae55-258">È anche possibile creare solo le mesh della superficie nei buffer di visualizzazione stereo.</span><span class="sxs-lookup"><span data-stu-id="7ae55-258">We can also just draw the surface meshes to the stereo display buffers.</span></span> <span data-ttu-id="7ae55-259">Abbiamo scelto di creare i visi completi con l'illuminazione, ma è possibile creare wireframe, elaborare mesh prima del rendering, applicare una mappa di trama e così via.</span><span class="sxs-lookup"><span data-stu-id="7ae55-259">We chose to draw full faces with lighting, but you're free to draw wireframe, process meshes before rendering, apply a texture map, and so on.</span></span>

<span data-ttu-id="7ae55-260">Qui, l'esempio di codice indica al renderer mesh di creare la raccolta.</span><span class="sxs-lookup"><span data-stu-id="7ae55-260">Here, our code sample tells the mesh renderer to draw the collection.</span></span> <span data-ttu-id="7ae55-261">Questa volta non viene specificato un passaggio di sola profondità, quindi si collegherà una pixel shader e si completerà la pipeline di rendering usando le destinazioni specificate per la fotocamera virtuale corrente.</span><span class="sxs-lookup"><span data-stu-id="7ae55-261">This time we don't specify a depth-only pass, so it will attach a pixel shader and complete the rendering pipeline using the targets that we specified for the current virtual camera.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="7ae55-262">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7ae55-262">See also</span></span>
* [<span data-ttu-id="7ae55-263">Creazione di un progetto DirectX olografico</span><span class="sxs-lookup"><span data-stu-id="7ae55-263">Creating a holographic DirectX project</span></span>](creating-a-holographic-directx-project.md)
* [<span data-ttu-id="7ae55-264">API Windows. Perception. Spatial</span><span class="sxs-lookup"><span data-stu-id="7ae55-264">Windows.Perception.Spatial API</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)

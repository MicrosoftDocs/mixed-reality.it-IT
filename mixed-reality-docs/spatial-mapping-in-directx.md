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
# <a name="spatial-mapping-in-directx"></a><span data-ttu-id="a32d8-105">Mapping spaziale DirectX</span><span class="sxs-lookup"><span data-stu-id="a32d8-105">Spatial mapping in DirectX</span></span>

<span data-ttu-id="a32d8-106">In questo argomento descrive come implementare [mapping spaziale](spatial-mapping.md) nell'app DirectX.</span><span class="sxs-lookup"><span data-stu-id="a32d8-106">This topic describes how to implement [spatial mapping](spatial-mapping.md) in your DirectX app.</span></span> <span data-ttu-id="a32d8-107">Ciò include una spiegazione dettagliata dell'applicazione di esempio di mapping spaziale inclusa in Universal Windows Platform SDK.</span><span class="sxs-lookup"><span data-stu-id="a32d8-107">This includes a detailed explanation of the spatial mapping sample application that is included with the Universal Windows Platform SDK.</span></span>

<span data-ttu-id="a32d8-108">Questo argomento viene usato dal codice il [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) esempio di codice di piattaforma UWP.</span><span class="sxs-lookup"><span data-stu-id="a32d8-108">This topic uses code from the [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) UWP code sample.</span></span>

>[!NOTE]
><span data-ttu-id="a32d8-109">I frammenti di codice in questo articolo illustrano attualmente l'utilizzo di C++/CX invece di C + + 17 conformi C++/WinRT usato nel [ C++ modello di progetto holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="a32d8-109">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="a32d8-110">I concetti sono equivalenti per un C++progetto /WinRT, anche se è necessario convertire il codice.</span><span class="sxs-lookup"><span data-stu-id="a32d8-110">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="directx-development-overview"></a><span data-ttu-id="a32d8-111">Panoramica dello sviluppo DirectX</span><span class="sxs-lookup"><span data-stu-id="a32d8-111">DirectX development overview</span></span>

<span data-ttu-id="a32d8-112">Sviluppo di applicazioni native per mapping spaziale Usa le API con il [Windows.Perception.Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) dello spazio dei nomi.</span><span class="sxs-lookup"><span data-stu-id="a32d8-112">Native application development for spatial mapping uses the APIs under the [Windows.Perception.Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) namespace.</span></span> <span data-ttu-id="a32d8-113">Queste API forniscono il controllo completo di funzionalità di mapping spaziale, in modo analogo direttamente per le API esposte dal mapping spaziale [Unity](spatial-mapping-in-unity.md).</span><span class="sxs-lookup"><span data-stu-id="a32d8-113">These APIs provide full control of spatial mapping functionality, in a manner directly analogous to the spatial mapping APIs exposed by [Unity](spatial-mapping-in-unity.md).</span></span>

### <a name="perception-apis"></a><span data-ttu-id="a32d8-114">API di percezione</span><span class="sxs-lookup"><span data-stu-id="a32d8-114">Perception APIs</span></span>

<span data-ttu-id="a32d8-115">Come indicato di seguito sono riportati i tipi primari disponibili per lo sviluppo di mapping spaziale:</span><span class="sxs-lookup"><span data-stu-id="a32d8-115">The primary types provided for spatial mapping development are as follows:</span></span>
* <span data-ttu-id="a32d8-116">[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) fornisce informazioni su superfici in aree specificata dall'applicazione di spazio quasi l'utente, sotto forma di oggetti SpatialSurfaceInfo.</span><span class="sxs-lookup"><span data-stu-id="a32d8-116">[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) provides information about surfaces in application-specified regions of space near the user, in the form of SpatialSurfaceInfo objects.</span></span>
* <span data-ttu-id="a32d8-117">[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) descrive una singola superficie spaziale rilevarle incluso un ID univoco, volume e l'ora dell'ultima modifica di delimitazione.</span><span class="sxs-lookup"><span data-stu-id="a32d8-117">[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) describes a single extant spatial surface, including a unique ID, bounding volume and time of last change.</span></span> <span data-ttu-id="a32d8-118">Fornirà un SpatialSurfaceMesh in modo asincrono su richiesta.</span><span class="sxs-lookup"><span data-stu-id="a32d8-118">It will provide a SpatialSurfaceMesh asynchronously upon request.</span></span>
* <span data-ttu-id="a32d8-119">[SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) contiene parametri utilizzati per personalizzare gli oggetti SpatialSurfaceMesh richiesti dal SpatialSurfaceInfo.</span><span class="sxs-lookup"><span data-stu-id="a32d8-119">[SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) contains parameters used to customize the SpatialSurfaceMesh objects requested from SpatialSurfaceInfo.</span></span>
* <span data-ttu-id="a32d8-120">[SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) rappresenta i dati di rete per una singola superficie spaziale.</span><span class="sxs-lookup"><span data-stu-id="a32d8-120">[SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) represents the mesh data for a single spatial surface.</span></span> <span data-ttu-id="a32d8-121">I dati per le posizioni di vertice, normali vertici e gli indici del triangolo sono contenuti negli oggetti SpatialSurfaceMeshBuffer membro.</span><span class="sxs-lookup"><span data-stu-id="a32d8-121">The data for vertex positions, vertex normals and triangle indices is contained in member SpatialSurfaceMeshBuffer objects.</span></span>
* <span data-ttu-id="a32d8-122">[SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) esegue il wrapping di un singolo tipo di dati di trama.</span><span class="sxs-lookup"><span data-stu-id="a32d8-122">[SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) wraps a single type of mesh data.</span></span>

<span data-ttu-id="a32d8-123">Quando si sviluppa un'applicazione che Usa queste API, il flusso di programma di base avrà un aspetto simile al seguente (come illustrato nell'applicazione di esempio descritta di seguito):</span><span class="sxs-lookup"><span data-stu-id="a32d8-123">When developing an application using these APIs, your basic program flow will look like this (as demonstrated in the sample application described below):</span></span>
- <span data-ttu-id="a32d8-124">**Configurare il SpatialSurfaceObserver**</span><span class="sxs-lookup"><span data-stu-id="a32d8-124">**Set up your SpatialSurfaceObserver**</span></span>
  - <span data-ttu-id="a32d8-125">Chiamare [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx), per assicurarsi che l'utente ha dato l'autorizzazione per l'applicazione per usare le funzionalità di mapping spaziale del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a32d8-125">Call [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx), to ensure that the user has given permission for your application to use the device's spatial mapping capabilities.</span></span>
  - <span data-ttu-id="a32d8-126">Creare un'istanza di un oggetto SpatialSurfaceObserver.</span><span class="sxs-lookup"><span data-stu-id="a32d8-126">Instantiate a SpatialSurfaceObserver object.</span></span>
  - <span data-ttu-id="a32d8-127">Chiamare [SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) per specificare le aree di spazio in cui si desiderano informazioni su superfici spaziale.</span><span class="sxs-lookup"><span data-stu-id="a32d8-127">Call [SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) to specify the regions of space in which you want information about spatial surfaces.</span></span> <span data-ttu-id="a32d8-128">È possibile modificare queste aree in futuro semplicemente chiamando di nuovo questa funzione.</span><span class="sxs-lookup"><span data-stu-id="a32d8-128">You may modify these regions in the future by simply calling this function again.</span></span> <span data-ttu-id="a32d8-129">Ogni area viene specificato usando un [SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx).</span><span class="sxs-lookup"><span data-stu-id="a32d8-129">Each region is specified using a [SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx).</span></span>
  - <span data-ttu-id="a32d8-130">Registrarsi per il [ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) evento, che viene attivato ogni volta nuove informazioni sono disponibili sulle aree di spaziale nelle aree dello spazio è stato specificato.</span><span class="sxs-lookup"><span data-stu-id="a32d8-130">Register for the [ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) event, which will fire whenever new information is available about the spatial surfaces in the regions of space you have specified.</span></span>
- <span data-ttu-id="a32d8-131">**Elaborare eventi ObservedSurfacesChanged**</span><span class="sxs-lookup"><span data-stu-id="a32d8-131">**Process ObservedSurfacesChanged events**</span></span>
  - <span data-ttu-id="a32d8-132">Nel gestore eventi, chiamare [GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) per ricevere una mappa di oggetti SpatialSurfaceInfo.</span><span class="sxs-lookup"><span data-stu-id="a32d8-132">In your event handler, call [GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) to receive a map of SpatialSurfaceInfo objects.</span></span> <span data-ttu-id="a32d8-133">Utilizzando questa mappa, è possibile aggiornare i record di quali dispositivi Surface spaziale [presenti nell'ambiente dell'utente](spatial-mapping.md#mesh-caching).</span><span class="sxs-lookup"><span data-stu-id="a32d8-133">Using this map, you can update your records of which spatial surfaces [exist in the user's environment](spatial-mapping.md#mesh-caching).</span></span>
  - <span data-ttu-id="a32d8-134">Per ogni oggetto SpatialSurfaceInfo, è possibile eseguire una query [TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) per determinare gli extent spaziali della superficie, espressa in un [spaziale sistema di coordinate](coordinate-systems.md) di propria scelta.</span><span class="sxs-lookup"><span data-stu-id="a32d8-134">For each SpatialSurfaceInfo object, you may query [TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) to determine the spatial extents of the surface, expressed in a [spatial coordinate system](coordinate-systems.md) of your choosing.</span></span>
  - <span data-ttu-id="a32d8-135">Se si decide di richieste di rete per una superficie spaziale, chiamare [TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx).</span><span class="sxs-lookup"><span data-stu-id="a32d8-135">If you decide to request mesh for a spatial surface, call [TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx).</span></span> <span data-ttu-id="a32d8-136">È possibile fornire le opzioni che specifica la densità di triangoli desiderata e il formato dei dati restituiti mesh.</span><span class="sxs-lookup"><span data-stu-id="a32d8-136">You may provide options specifying the desired density of triangles, and the format of the returned mesh data.</span></span>
- <span data-ttu-id="a32d8-137">**Ricevere ed elaborare mesh**</span><span class="sxs-lookup"><span data-stu-id="a32d8-137">**Receive and process mesh**</span></span>
  - <span data-ttu-id="a32d8-138">Ogni chiamata a TryComputeLatestMeshAsync will aysnchronously restituire un oggetto SpatialSurfaceMesh.</span><span class="sxs-lookup"><span data-stu-id="a32d8-138">Each call to TryComputeLatestMeshAsync will aysnchronously return one SpatialSurfaceMesh object.</span></span>
  - <span data-ttu-id="a32d8-139">Da questo oggetto, è possibile accedere gli oggetti SpatialSurfaceMeshBuffer contenuti per poter accedere il indici del triangolo, posizioni di vertice e (se richiesto) normali vertici della mesh.</span><span class="sxs-lookup"><span data-stu-id="a32d8-139">From this object you can access the contained SpatialSurfaceMeshBuffer objects in order to access the triangle indices, vertex positions and (if requested) vertex normals of the mesh.</span></span> <span data-ttu-id="a32d8-140">I dati andranno in un formato direttamente compatibile con il [Direct3D 11 API](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) usati per il rendering mesh.</span><span class="sxs-lookup"><span data-stu-id="a32d8-140">This data will be in a format directly compatible with the [Direct3D 11 APIs](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) used for rendering meshes.</span></span>
  - <span data-ttu-id="a32d8-141">A questo punto l'applicazione può anche eseguire analisi o [elaborazione](spatial-mapping.md#mesh-processing) dei dati di trama e usarlo per [rendering](spatial-mapping.md#rendering) fisica e [raycasting e collisione](spatial-mapping.md#raycasting-and-collision).</span><span class="sxs-lookup"><span data-stu-id="a32d8-141">From here your application can optionally perform analysis or [processing](spatial-mapping.md#mesh-processing) of the mesh data, and use it for [rendering](spatial-mapping.md#rendering) and physics [raycasting and collision](spatial-mapping.md#raycasting-and-collision).</span></span>
  - <span data-ttu-id="a32d8-142">Un dettaglio importante da notare è che è necessario applicare un scalabilità per le posizioni dei vertici mesh (ad esempio in vertex shader usati per il rendering mesh), per convertire tali dalle unità di integer ottimizzato in cui sono archiviati nel buffer, a contatori.</span><span class="sxs-lookup"><span data-stu-id="a32d8-142">One important detail to note is that you must apply a scale to the mesh vertex positions (for example in the vertex shader used for rendering the meshes), to convert them from the optimized integer units in which they are stored in the buffer, to meters.</span></span> <span data-ttu-id="a32d8-143">È possibile recuperare questa scala chiamando [VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx).</span><span class="sxs-lookup"><span data-stu-id="a32d8-143">You can retrieve this scale by calling [VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx).</span></span>

### <a name="troubleshooting"></a><span data-ttu-id="a32d8-144">Risoluzione dei problemi</span><span class="sxs-lookup"><span data-stu-id="a32d8-144">Troubleshooting</span></span>
* <span data-ttu-id="a32d8-145">Non dimenticare di posizioni di vertice trama allo shader vertice, tramite la scala restituita da ridimensionare [SpatialSurfaceMesh.VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)</span><span class="sxs-lookup"><span data-stu-id="a32d8-145">Don't forget to scale mesh vertex positions in your vertex shader, using the scale returned by [SpatialSurfaceMesh.VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)</span></span>

## <a name="spatial-mapping-code-sample-walkthrough"></a><span data-ttu-id="a32d8-146">Procedura di esempio di codice Mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="a32d8-146">Spatial Mapping code sample walkthrough</span></span>

<span data-ttu-id="a32d8-147">Il [Mapping spaziale Holographic](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) codice di esempio include codice che è possibile usare per iniziare a usare il caricamento di superficie mesh in un'app, nonché l'infrastruttura per la gestione e la superficie di rendering mesh.</span><span class="sxs-lookup"><span data-stu-id="a32d8-147">The [Holographic Spatial Mapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) code sample includes code that you can use to get started loading surface meshes into your app, including infrastructure for managing and rendering surface meshes.</span></span>

<span data-ttu-id="a32d8-148">A questo punto, viene illustrato come aggiungere funzionalità di mapping superficie all'App DirectX.</span><span class="sxs-lookup"><span data-stu-id="a32d8-148">Now, we walk through how to add surface mapping capability to your DirectX app.</span></span> <span data-ttu-id="a32d8-149">È possibile aggiungere questo codice per il [modello di app Windows Holographic](creating-a-holographic-directx-project.md) progetto oppure è possibile seguire la procedura esplorando il codice di esempio indicato in precedenza.</span><span class="sxs-lookup"><span data-stu-id="a32d8-149">You can add this code to your [Windows Holographic app template](creating-a-holographic-directx-project.md) project, or you can follow along by browsing through the code sample mentioned above.</span></span> <span data-ttu-id="a32d8-150">Questo esempio di codice si basa sul modello di app Windows Holographic.</span><span class="sxs-lookup"><span data-stu-id="a32d8-150">This code sample is based on the Windows Holographic app template.</span></span>

### <a name="set-up-your-app-to-use-the-spatialperception-capability"></a><span data-ttu-id="a32d8-151">Configurare l'app per usare la funzionalità spatialPerception</span><span class="sxs-lookup"><span data-stu-id="a32d8-151">Set up your app to use the spatialPerception capability</span></span>

<span data-ttu-id="a32d8-152">L'app deve essere in grado di usare la funzionalità di mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="a32d8-152">Your app must be able to use the spatial mapping capability.</span></span> <span data-ttu-id="a32d8-153">Ciò è necessario perché il reticolato spaziale è una rappresentazione dell'ambiente dell'utente, che può essere considerato dati privati.</span><span class="sxs-lookup"><span data-stu-id="a32d8-153">This is necessary because the spatial mesh is a representation of the user's environment, which may be considered private data.</span></span> <span data-ttu-id="a32d8-154">Dichiarare questa funzionalità nel file package. appxmanifest per l'app.</span><span class="sxs-lookup"><span data-stu-id="a32d8-154">Declare this capability in the package.appxmanifest file for your app.</span></span> <span data-ttu-id="a32d8-155">Di seguito è riportato un esempio:</span><span class="sxs-lookup"><span data-stu-id="a32d8-155">Here's an example:</span></span>

```xml
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

<span data-ttu-id="a32d8-156">La funzionalità proviene il **uap2** dello spazio dei nomi.</span><span class="sxs-lookup"><span data-stu-id="a32d8-156">The capability comes from the **uap2** namespace.</span></span> <span data-ttu-id="a32d8-157">Per poter accedere a questo spazio dei nomi nel manifesto, includerlo come un *xlmns* attributo il &lt;pacchetto > elemento.</span><span class="sxs-lookup"><span data-stu-id="a32d8-157">To get access to this namespace in your manifest, include it as an *xlmns* attribute in the &lt;Package> element.</span></span> <span data-ttu-id="a32d8-158">Di seguito è riportato un esempio:</span><span class="sxs-lookup"><span data-stu-id="a32d8-158">Here's an example:</span></span>

```xml
<Package
    xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap uap2 mp"
    >
```

### <a name="check-for-spatial-mapping-feature-support"></a><span data-ttu-id="a32d8-159">Verificare il supporto di funzionalità di mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="a32d8-159">Check for spatial mapping feature support</span></span>

<span data-ttu-id="a32d8-160">Realtà mista di Windows supporta un'ampia gamma di dispositivi, inclusi quelli che non supportano il mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="a32d8-160">Windows Mixed Reality supports a wide range of devices, including devices which do not support spatial mapping.</span></span> <span data-ttu-id="a32d8-161">Se l'app può usare il mapping spaziale o necessario usare mapping spaziale, per fornire funzionalità, è necessario verificare per assicurarsi che il mapping spaziale è supportato prima di provare a usarlo.</span><span class="sxs-lookup"><span data-stu-id="a32d8-161">If your app can use spatial mapping, or must use spatial mapping, to provide functionality, it should check to make sure that spatial mapping is supported before trying to use it.</span></span> <span data-ttu-id="a32d8-162">Ad esempio, se mapping spaziale è richiesto dall'app per realtà mista, visualizzerà un messaggio in tal senso se un utente tenta di eseguirlo in un dispositivo senza mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="a32d8-162">For example, if spatial mapping is required by your mixed reality app, it should display a message to that effect if a user tries running it on a device without spatial mapping.</span></span> <span data-ttu-id="a32d8-163">In alternativa, l'app potrebbe essere in grado di eseguire il rendering di un proprio ambiente virtuale al posto di ambiente dell'utente, offrendo un'esperienza simile a che cosa accadrebbe se mapping spaziale non erano disponibili.</span><span class="sxs-lookup"><span data-stu-id="a32d8-163">Or, your app may be able to render its own virtual environment in place of the user's environment, providing an experience that is similar to what would happen if spatial mapping were available.</span></span> <span data-ttu-id="a32d8-164">In ogni caso, questa API consente all'app da tenere presenti quando non recuperare i dati di mapping spaziale e rispondere nel modo appropriato.</span><span class="sxs-lookup"><span data-stu-id="a32d8-164">In any event, this API allows your app to be aware of when it will not get spatial mapping data and respond in the appropriate way.</span></span>

<span data-ttu-id="a32d8-165">Per controllare il dispositivo corrente per il supporto di mapping spaziale, prima di tutto assicurarsi che il contratto UWP è al livello 4 o versione successiva e quindi chiamare SpatialSurfaceObserver::IsSupported().</span><span class="sxs-lookup"><span data-stu-id="a32d8-165">To check the current device for spatial mapping support, first make sure the UWP contract is at level 4 or greater and then call SpatialSurfaceObserver::IsSupported().</span></span> <span data-ttu-id="a32d8-166">Ecco come eseguire questa operazione nel contesto del [Mapping spaziale Holographic](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) esempio di codice.</span><span class="sxs-lookup"><span data-stu-id="a32d8-166">Here's how to do so in the context of the [Holographic Spatial Mapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) code sample.</span></span> <span data-ttu-id="a32d8-167">Il supporto viene controllato appena prima che richiede l'accesso.</span><span class="sxs-lookup"><span data-stu-id="a32d8-167">Support is checked just before requesting access.</span></span>

<span data-ttu-id="a32d8-168">L'API SpatialSurfaceObserver::IsSupported() è disponibile a partire da SDK versione 15063.</span><span class="sxs-lookup"><span data-stu-id="a32d8-168">The SpatialSurfaceObserver::IsSupported() API is available starting in SDK version 15063.</span></span> <span data-ttu-id="a32d8-169">Se necessario, è possibile Ridestinare il progetto alla versione della piattaforma 15063 prima di usare questa API.</span><span class="sxs-lookup"><span data-stu-id="a32d8-169">If necessary, retarget your project to platform version 15063 before using this API.</span></span>

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

<span data-ttu-id="a32d8-170">Si noti che, quando il contratto UWP è minore di livello 4, l'app deve continuare come se il dispositivo è in grado di soddisfare mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="a32d8-170">Note that when the UWP contract is less than level 4, the app should proceed as though the device is capable of doing spatial mapping.</span></span>

### <a name="request-access-to-spatial-mapping-data"></a><span data-ttu-id="a32d8-171">Richiedere l'accesso ai dati di mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="a32d8-171">Request access to spatial mapping data</span></span>

<span data-ttu-id="a32d8-172">L'app deve richiedere l'autorizzazione per accedere ai dati di mapping spaziale prima di tentare di creare qualsiasi superficie osservatori.</span><span class="sxs-lookup"><span data-stu-id="a32d8-172">Your app needs to request permission to access spatial mapping data before trying to create any surface observers.</span></span> <span data-ttu-id="a32d8-173">Di seguito è riportato un esempio in base al nostro esempio di codice il Mapping di area, con maggiori dettagli, forniti più avanti in questa pagina:</span><span class="sxs-lookup"><span data-stu-id="a32d8-173">Here's an example based upon our Surface Mapping code sample, with more details provided later on this page:</span></span>

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

### <a name="create-a-surface-observer"></a><span data-ttu-id="a32d8-174">Creare un observer surface</span><span class="sxs-lookup"><span data-stu-id="a32d8-174">Create a surface observer</span></span>

<span data-ttu-id="a32d8-175">Il **Windows::Perception::Spatial::Surfaces** spazio dei nomi include le [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) classe, che rileva uno o più volumi che specificano in un [ SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx).</span><span class="sxs-lookup"><span data-stu-id="a32d8-175">The **Windows::Perception::Spatial::Surfaces** namespace includes the [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) class, which observes one or more volumes that you specify in a [SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx).</span></span> <span data-ttu-id="a32d8-176">Usare un [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) istanza per accedere ai dati di trama della superficie in tempo reale.</span><span class="sxs-lookup"><span data-stu-id="a32d8-176">Use a [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) instance to access surface mesh data in real time.</span></span>

<span data-ttu-id="a32d8-177">Dal **AppMain.h**:</span><span class="sxs-lookup"><span data-stu-id="a32d8-177">From **AppMain.h**:</span></span>

```cpp
// Obtains surface mapping data from the device in real time.
Windows::Perception::Spatial::Surfaces::SpatialSurfaceObserver^     m_surfaceObserver;
Windows::Perception::Spatial::Surfaces::SpatialSurfaceMeshOptions^  m_surfaceMeshOptions;
```

<span data-ttu-id="a32d8-178">Come indicato nella sezione precedente, è necessario richiedere l'accesso ai dati di mapping spaziale prima che l'app può utilizzarlo.</span><span class="sxs-lookup"><span data-stu-id="a32d8-178">As noted in the previous section, you must request access to spatial mapping data before your app can use it.</span></span> <span data-ttu-id="a32d8-179">Questo accesso viene concesso automaticamente nella finestra di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a32d8-179">This access is granted automatically on the HoloLens.</span></span>

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

<span data-ttu-id="a32d8-180">Successivamente, è necessario configurare l'osservatore superficie per osservare un volume specifico di delimitazione.</span><span class="sxs-lookup"><span data-stu-id="a32d8-180">Next, you need to configure the surface observer to observe a specific bounding volume.</span></span> <span data-ttu-id="a32d8-181">In questo caso, riscontrata una finestra che è 20 x 20 x 5 metri, centrato rispetto all'origine del sistema di coordinate.</span><span class="sxs-lookup"><span data-stu-id="a32d8-181">Here, we observe a box that is 20x20x5 meters, centered at the origin of the coordinate system.</span></span>

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

<span data-ttu-id="a32d8-182">Si noti che è possibile impostare più volumi di delimitazione.</span><span class="sxs-lookup"><span data-stu-id="a32d8-182">Note that you can set multiple bounding volumes instead.</span></span>

<span data-ttu-id="a32d8-183">*Si tratta di pseudocodice:*</span><span class="sxs-lookup"><span data-stu-id="a32d8-183">*This is pseudocode:*</span></span>

```cpp
m_surfaceObserver->SetBoundingVolumes(/* iterable collection of bounding volumes*/);
```

<span data-ttu-id="a32d8-184">È anche possibile usare altre forme di delimitazione - ad esempio un cono, vista o un rettangolo di selezione dell'asse non è allineato.</span><span class="sxs-lookup"><span data-stu-id="a32d8-184">It is also possible to use other bounding shapes - such as a view frustum, or a bounding box that is not axis aligned.</span></span>

<span data-ttu-id="a32d8-185">*Si tratta di pseudocodice:*</span><span class="sxs-lookup"><span data-stu-id="a32d8-185">*This is pseudocode:*</span></span>

```cpp
m_surfaceObserver->SetBoundingVolume(
            SpatialBoundingVolume::FromFrustum(/*SpatialCoordinateSystem*/, /*SpatialBoundingFrustum*/)
            );
```

<span data-ttu-id="a32d8-186">Se l'app deve eseguire alcuna operazione in modo diverso quando i dati di mapping surface non sono disponibili, è possibile scrivere codice per rispondere al caso in cui il [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) non è **consentito** , ad esempio non sarà possibile nei PC con immersive periferiche collegate perché non dispone di tali dispositivi hardware per il mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="a32d8-186">If your app needs to do anything differently when surface mapping data is not available, you can write code to respond to the case where the [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) is not **Allowed** - for example, it will not be allowed on PCs with immersive devices attached because those devices don't have hardware for spatial mapping.</span></span> <span data-ttu-id="a32d8-187">Per questi dispositivi, è invece necessario affidarsi a stage spaziali per informazioni sull'ambiente e configurazione del dispositivo dell'utente.</span><span class="sxs-lookup"><span data-stu-id="a32d8-187">For these devices, you should instead rely on the spatial stage for information about the user's environment and device configuration.</span></span>

### <a name="initialize-and-update-the-surface-mesh-collection"></a><span data-ttu-id="a32d8-188">Inizializzare e aggiornare la raccolta di trama della superficie</span><span class="sxs-lookup"><span data-stu-id="a32d8-188">Initialize and update the surface mesh collection</span></span>

<span data-ttu-id="a32d8-189">Se è stato creato correttamente l'osservatore surface, è possibile procedere per inizializzare la raccolta di trama della superficie.</span><span class="sxs-lookup"><span data-stu-id="a32d8-189">If the surface observer was successfully created, we can proceed to initialize our surface mesh collection.</span></span> <span data-ttu-id="a32d8-190">In questo caso, utilizziamo l'API del modello pull per ottenere il set corrente di superfici osservate subito:</span><span class="sxs-lookup"><span data-stu-id="a32d8-190">Here, we use the pull model API to get the current set of observed surfaces right away:</span></span>

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

<span data-ttu-id="a32d8-191">È inoltre disponibile un modello push disponibile per ottenere i dati di trama della superficie.</span><span class="sxs-lookup"><span data-stu-id="a32d8-191">There is also a push model available to get surface mesh data.</span></span> <span data-ttu-id="a32d8-192">Si è liberi di progettare l'applicazione usi solo il modello di pull se si sceglie, nel qual caso si sarà esegue il polling per i dati di tanto in tanto, ad esempio, una volta per frame - o durante un periodo di tempo specifico, ad esempio durante l'installazione del gioco.</span><span class="sxs-lookup"><span data-stu-id="a32d8-192">You are free to design your app to use only the pull model if you choose, in which case you'll poll for data every so often - say, once per frame - or during a specific time period, such as during game setup.</span></span> <span data-ttu-id="a32d8-193">In questo caso, il codice sopra riportato è ciò che è necessario.</span><span class="sxs-lookup"><span data-stu-id="a32d8-193">If so, the above code is what you need.</span></span>

<span data-ttu-id="a32d8-194">Nel nostro esempio di codice, abbiamo scelto illustrare l'utilizzo di entrambi i modelli per a scopo formativo.</span><span class="sxs-lookup"><span data-stu-id="a32d8-194">In our code sample, we chose to demonstrate the use of both models for pedagogical purposes.</span></span> <span data-ttu-id="a32d8-195">In questo caso, si sottoscrive un evento di ricevere i dati di trama della superficie aggiornate ogni volta che il sistema rileva una modifica.</span><span class="sxs-lookup"><span data-stu-id="a32d8-195">Here, we subscribe to an event to receive up-to-date surface mesh data whenever the system recognizes a change.</span></span>

```cpp
m_surfaceObserver->ObservedSurfacesChanged += ref new TypedEventHandler<SpatialSurfaceObserver^, Platform::Object^>(
            bind(&HolographicDesktopAppMain::OnSurfacesChanged, this, _1, _2)
            );
```

<span data-ttu-id="a32d8-196">L'esempio di codice è inoltre configurato per rispondere a tali eventi.</span><span class="sxs-lookup"><span data-stu-id="a32d8-196">Our code sample is also configured to respond to these events.</span></span> <span data-ttu-id="a32d8-197">Di seguito viene illustrato come è eseguire questa operazione.</span><span class="sxs-lookup"><span data-stu-id="a32d8-197">Let's walk through how we do this.</span></span>

<span data-ttu-id="a32d8-198">**NOTA:** Ciò potrebbe non essere il modo più efficiente per l'app per la gestione dei dati di trama.</span><span class="sxs-lookup"><span data-stu-id="a32d8-198">**NOTE:** This might not be the most efficient way for your app to handle mesh data.</span></span> <span data-ttu-id="a32d8-199">Questo codice viene scritto per maggiore chiarezza e non è ottimizzato.</span><span class="sxs-lookup"><span data-stu-id="a32d8-199">This code is written for clarity and is not optimized.</span></span>

<span data-ttu-id="a32d8-200">Vengono forniti in una mappa di sola lettura che archivia dati trama della superficie [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) degli oggetti mediante [Platform::Guids](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) come valori delle chiavi.</span><span class="sxs-lookup"><span data-stu-id="a32d8-200">The surface mesh data is provided in a read-only map that stores [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) objects using [Platform::Guids](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) as key values.</span></span>

```cpp
IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection = sender->GetObservedSurfaces();
```

<span data-ttu-id="a32d8-201">Per elaborare i dati, verranno esaminate prima per valori di chiave che non si trovano nella nostra raccolta.</span><span class="sxs-lookup"><span data-stu-id="a32d8-201">To process this data, we look first for key values that aren't in our collection.</span></span> <span data-ttu-id="a32d8-202">Visualizzerà i dettagli sul modo in cui i dati vengono archiviati nella nostra app di esempio più avanti in questo argomento.</span><span class="sxs-lookup"><span data-stu-id="a32d8-202">Details on how the data is stored in our sample app will be presented later in this topic.</span></span>

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

<span data-ttu-id="a32d8-203">È anche necessario rimuovere superficie trame che sono nella nostra raccolta di trama della superficie, ma che non sono in più la raccolta di sistema.</span><span class="sxs-lookup"><span data-stu-id="a32d8-203">We also have to remove surface meshes that are in our surface mesh collection, but that aren't in the system collection anymore.</span></span> <span data-ttu-id="a32d8-204">A tale scopo, è necessario eseguire un'operazione simile il contrario di ciò che abbiamo appena illustrato per aggiungere e aggiornare le reti mesh di; esegue il ciclo nella raccolta dell'app e verificare se il **Guid** abbiamo è incluso nella raccolta di sistema.</span><span class="sxs-lookup"><span data-stu-id="a32d8-204">To do so, we need to do something akin to the opposite of what we just showed for adding and updating meshes; we loop on our app's collection, and check to see if the **Guid** we have is in the system collection.</span></span> <span data-ttu-id="a32d8-205">Se non è nell'insieme di sistema, abbiamo rimuoverlo da noi.</span><span class="sxs-lookup"><span data-stu-id="a32d8-205">If it's not in the system collection, we remove it from ours.</span></span>

<span data-ttu-id="a32d8-206">Dal nostro gestore di eventi in AppMain.cpp:</span><span class="sxs-lookup"><span data-stu-id="a32d8-206">From our event handler in AppMain.cpp:</span></span>

```cpp
m_meshCollection->PruneMeshCollection(surfaceCollection);
```

<span data-ttu-id="a32d8-207">L'implementazione dell'eliminazione di mesh in RealtimeSurfaceMeshRenderer.cpp:</span><span class="sxs-lookup"><span data-stu-id="a32d8-207">The implementation of mesh pruning in RealtimeSurfaceMeshRenderer.cpp:</span></span>

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

### <a name="acquire-and-use-surface-mesh-data-buffers"></a><span data-ttu-id="a32d8-208">Acquisizione e l'uso di buffer di dati di trama della superficie</span><span class="sxs-lookup"><span data-stu-id="a32d8-208">Acquire and use surface mesh data buffers</span></span>

<span data-ttu-id="a32d8-209">Recupero delle informazioni di trama della superficie era basta eseguire il pull di una raccolta di dati e l'elaborazione degli aggiornamenti alla raccolta.</span><span class="sxs-lookup"><span data-stu-id="a32d8-209">Getting the surface mesh information was as easy as pulling a data collection and processing updates to that collection.</span></span> <span data-ttu-id="a32d8-210">A questo punto, si passerà in modo dettagliato sul modo in cui è possibile usare i dati.</span><span class="sxs-lookup"><span data-stu-id="a32d8-210">Now, we'll go into detail on how you can use the data.</span></span>

<span data-ttu-id="a32d8-211">In questo esempio di codice, abbiamo scelto di usare le reti mesh di surface per il rendering.</span><span class="sxs-lookup"><span data-stu-id="a32d8-211">In our code example, we chose to use the surface meshes for rendering.</span></span> <span data-ttu-id="a32d8-212">Si tratta di uno scenario comune per occluding vntana dietro aree del mondo reale.</span><span class="sxs-lookup"><span data-stu-id="a32d8-212">This is a common scenario for occluding holograms behind real-world surfaces.</span></span> <span data-ttu-id="a32d8-213">È anche possibile eseguire il rendering mesh o eseguire il rendering elaborate versioni di tali, in modo da visualizzare all'utente informazioni sulle aree di chat room viene eseguita l'analisi prima di iniziare la funzionalità di app o giochi.</span><span class="sxs-lookup"><span data-stu-id="a32d8-213">You can also render the meshes, or render processed versions of them, to show the user what areas of the room are scanned before you start providing app or game functionality.</span></span>

<span data-ttu-id="a32d8-214">Nell'esempio di codice avvia il processo quando riceve gli aggiornamenti di trama della superficie dal gestore dell'evento che è descritti nella sezione precedente.</span><span class="sxs-lookup"><span data-stu-id="a32d8-214">The code sample starts the process when it receives surface mesh updates from the event handler that we described in the previous section.</span></span> <span data-ttu-id="a32d8-215">La riga di codice in questa funzione importante è la chiamata per aggiornare l'area *mesh*: a questo punto abbiamo già elaborato le informazioni di rete e si sta tentando di ottenere i dati di vertici e indici per l'uso come si preferisce.</span><span class="sxs-lookup"><span data-stu-id="a32d8-215">The important line of code in this function is the call to update the surface *mesh*: by this time we have already processed the mesh info, and we are about to get the vertex and index data for use as we see fit.</span></span>

<span data-ttu-id="a32d8-216">Da RealtimeSurfaceMeshRenderer.cpp:</span><span class="sxs-lookup"><span data-stu-id="a32d8-216">From RealtimeSurfaceMeshRenderer.cpp:</span></span>

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

<span data-ttu-id="a32d8-217">Il codice di esempio è progettato in modo che una classe di dati **SurfaceMesh**, trama di gestione dei dati di elaborazione e rendering.</span><span class="sxs-lookup"><span data-stu-id="a32d8-217">Our sample code is designed so that a data class, **SurfaceMesh**, handles mesh data processing and rendering.</span></span> <span data-ttu-id="a32d8-218">Queste reti sono ciò che il **RealtimeSurfaceMeshRenderer** effettivamente mantiene una mappa di.</span><span class="sxs-lookup"><span data-stu-id="a32d8-218">These meshes are what the **RealtimeSurfaceMeshRenderer** actually keeps a map of.</span></span> <span data-ttu-id="a32d8-219">Ognuno di essi ha un riferimento al SpatialSurfaceMesh da cui proviene e viene usato ogni volta che è necessario accedere ai buffer di vertice o indice la mesh o ottenere una trasformazione per la rete mesh.</span><span class="sxs-lookup"><span data-stu-id="a32d8-219">Each one has a reference to the SpatialSurfaceMesh it came from, and we use it any time that we need to access the mesh vertex or index buffers, or get a transform for the mesh.</span></span> <span data-ttu-id="a32d8-220">Per ora, abbiamo flag mesh come da un aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="a32d8-220">For now, we flag the mesh as needing an update.</span></span>

<span data-ttu-id="a32d8-221">Da SurfaceMesh.cpp:</span><span class="sxs-lookup"><span data-stu-id="a32d8-221">From SurfaceMesh.cpp:</span></span>

```cpp
void SurfaceMesh::UpdateSurface(SpatialSurfaceMesh^ surfaceMesh)
{
    m_surfaceMesh = surfaceMesh;
    m_updateNeeded = true;
}
```

<span data-ttu-id="a32d8-222">La volta successiva che la trama viene chiesto di disegnarsi da solo, il flag verrà verificata prima di tutto.</span><span class="sxs-lookup"><span data-stu-id="a32d8-222">Next time the mesh is asked to draw itself, it will check the flag first.</span></span> <span data-ttu-id="a32d8-223">Se è necessario un aggiornamento, i buffer vertici e indici verranno aggiornati nella GPU.</span><span class="sxs-lookup"><span data-stu-id="a32d8-223">If an update is needed, the vertex and index buffers will be updated on the GPU.</span></span>

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

<span data-ttu-id="a32d8-224">In primo luogo, acquisizione di buffer di dati non elaborati:</span><span class="sxs-lookup"><span data-stu-id="a32d8-224">First, we acquire the raw data buffers:</span></span>

```cpp
Windows::Storage::Streams::IBuffer^ positions = m_surfaceMesh->VertexPositions->Data;
    Windows::Storage::Streams::IBuffer^ normals   = m_surfaceMesh->VertexNormals->Data;
    Windows::Storage::Streams::IBuffer^ indices   = m_surfaceMesh->TriangleIndices->Data;
```

<span data-ttu-id="a32d8-225">Quindi, creiamo buffer dispositivo Direct3D con i dati di trama forniti da di HoloLens:</span><span class="sxs-lookup"><span data-stu-id="a32d8-225">Then, we create Direct3D device buffers with the mesh data provided by the HoloLens:</span></span>

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

<span data-ttu-id="a32d8-226">**NOTA:** Per la funzione di supporto CreateDirectXBuffer usata nel frammento di codice precedente, vedere l'esempio di codice nell'area di Mapping: SurfaceMesh.cpp, GetDataFromIBuffer.h.</span><span class="sxs-lookup"><span data-stu-id="a32d8-226">**NOTE:** For the CreateDirectXBuffer helper function used in the previous snippet, see the Surface Mapping code sample: SurfaceMesh.cpp, GetDataFromIBuffer.h.</span></span> <span data-ttu-id="a32d8-227">A questo punto è stata completata la creazione di risorse del dispositivo e la trama viene considerata per essere caricati e pronti per l'aggiornamento e il rendering.</span><span class="sxs-lookup"><span data-stu-id="a32d8-227">Now the device resource creation is complete, and the mesh is considered to be loaded and ready for update and render.</span></span>

### <a name="update-and-render-surface-meshes"></a><span data-ttu-id="a32d8-228">Aggiornare ed eseguire il rendering mesh surface</span><span class="sxs-lookup"><span data-stu-id="a32d8-228">Update and render surface meshes</span></span>

<span data-ttu-id="a32d8-229">La classe SurfaceMesh ha una funzione di aggiornamento specializzate.</span><span class="sxs-lookup"><span data-stu-id="a32d8-229">Our SurfaceMesh class has a specialized update function.</span></span> <span data-ttu-id="a32d8-230">Ciascuna [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) ha la propria trasformazione e l'esempio Usa il sistema di coordinate per nostro **SpatialStationaryReferenceFrame** per acquisire la trasformazione.</span><span class="sxs-lookup"><span data-stu-id="a32d8-230">Each [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) has its own transform, and our sample uses the current coordinate system for our **SpatialStationaryReferenceFrame** to acquire the transform.</span></span> <span data-ttu-id="a32d8-231">Quindi aggiorna il buffer costante del modello nella GPU.</span><span class="sxs-lookup"><span data-stu-id="a32d8-231">Then it updates the model constant buffer on the GPU.</span></span>

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

<span data-ttu-id="a32d8-232">Al momento per eseguire il rendering mesh superficie, eseguiamo alcune operazioni di preparazione prima il rendering dell'insieme.</span><span class="sxs-lookup"><span data-stu-id="a32d8-232">When it's time to render surface meshes, we do some prep work before rendering the collection.</span></span> <span data-ttu-id="a32d8-233">Abbiamo configurato la pipeline di shader per la configurazione di rendering corrente, e impostiamo la fase di assemblaggio input.</span><span class="sxs-lookup"><span data-stu-id="a32d8-233">We set up the shader pipeline for the current rendering configuration, and we set up the input assembler stage.</span></span> <span data-ttu-id="a32d8-234">Si noti che la classe helper di fotocamera holographic **CameraResources.cpp** già ha configurato il buffer costante/proiezione vista a questo punto.</span><span class="sxs-lookup"><span data-stu-id="a32d8-234">Note that the holographic camera helper class **CameraResources.cpp** already has set up the view/projection constant buffer by now.</span></span>

<span data-ttu-id="a32d8-235">Dal **RealtimeSurfaceMeshRenderer::Render**:</span><span class="sxs-lookup"><span data-stu-id="a32d8-235">From **RealtimeSurfaceMeshRenderer::Render**:</span></span>

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

<span data-ttu-id="a32d8-236">Al termine, è il ciclo sul nostro mesh e indicare a ognuno di essi di disegnarsi da solo.</span><span class="sxs-lookup"><span data-stu-id="a32d8-236">Once this is done, we loop on our meshes and tell each one to draw itself.</span></span> <span data-ttu-id="a32d8-237">**NOTA:** Questo codice di esempio non è ottimizzato per l'utilizzo una sorta di cono della faccia posteriore, ma è necessario includere questa funzionalità nell'app.</span><span class="sxs-lookup"><span data-stu-id="a32d8-237">**NOTE:** This sample code is not optimized to use any sort of frustum culling, but you should include this feature in your app.</span></span>

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

<span data-ttu-id="a32d8-238">Le singole trame sono responsabili dell'impostazione del buffer di vertici e indici, stride e buffer costante di trasformazione del modello.</span><span class="sxs-lookup"><span data-stu-id="a32d8-238">The individual meshes are responsible for setting up the vertex and index buffer, stride, and model transform constant buffer.</span></span> <span data-ttu-id="a32d8-239">Come per il cubo rotante nel modello di app Windows Holographic, si esegue il rendering nei buffer stereoscopico utilizzando la creazione di istanze.</span><span class="sxs-lookup"><span data-stu-id="a32d8-239">As with the spinning cube in the Windows Holographic app template, we render to stereoscopic buffers using instancing.</span></span>

<span data-ttu-id="a32d8-240">Dal **SurfaceMesh::Draw**:</span><span class="sxs-lookup"><span data-stu-id="a32d8-240">From **SurfaceMesh::Draw**:</span></span>

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

### <a name="rendering-choices-with-surface-mapping"></a><span data-ttu-id="a32d8-241">Opzioni di rendering con il Mapping di area</span><span class="sxs-lookup"><span data-stu-id="a32d8-241">Rendering choices with Surface Mapping</span></span>

<span data-ttu-id="a32d8-242">Nell'esempio di codice di Mapping nell'area offre il codice per il rendering solo relative all'occlusione di dati di trama della superficie e per il rendering sullo schermo di dati di trama della superficie.</span><span class="sxs-lookup"><span data-stu-id="a32d8-242">The Surface Mapping code sample offers code for occlusion-only rendering of surface mesh data, and for on-screen rendering of surface mesh data.</span></span> <span data-ttu-id="a32d8-243">Il percorso scelto - o entrambi - dipende dall'applicazione.</span><span class="sxs-lookup"><span data-stu-id="a32d8-243">Which path you choose - or both - depends on your application.</span></span> <span data-ttu-id="a32d8-244">Si esamineranno entrambe le configurazioni in questo documento.</span><span class="sxs-lookup"><span data-stu-id="a32d8-244">We'll walk through both configurations in this document.</span></span>

<span data-ttu-id="a32d8-245">**Buffer per il rendering occlusione holographic effetto**</span><span class="sxs-lookup"><span data-stu-id="a32d8-245">**Rendering occlusion buffers for holographic effect**</span></span>

<span data-ttu-id="a32d8-246">Iniziare cancellando la vista di destinazione di rendering per la fotocamera virtuale corrente.</span><span class="sxs-lookup"><span data-stu-id="a32d8-246">Start by clearing the render target view for the current virtual camera.</span></span>

<span data-ttu-id="a32d8-247">Da AppMain.cpp:</span><span class="sxs-lookup"><span data-stu-id="a32d8-247">From AppMain.cpp:</span></span>

```cpp
context->ClearRenderTargetView(pCameraResources->GetBackBufferRenderTargetView(), DirectX::Colors::Transparent);
```

<span data-ttu-id="a32d8-248">Si tratta di un passaggio "pre-rendering".</span><span class="sxs-lookup"><span data-stu-id="a32d8-248">This is a "pre-rendering" pass.</span></span> <span data-ttu-id="a32d8-249">In questo caso, creiamo un buffer di occlusione chiedendo il renderer mesh per eseguire il rendering solo profondità.</span><span class="sxs-lookup"><span data-stu-id="a32d8-249">Here, we create an occlusion buffer by asking the mesh renderer to render only depth.</span></span> <span data-ttu-id="a32d8-250">In questa configurazione, si non collega una vista di destinazione di rendering e il programma di rendering mesh imposta la fase pixel shader **nullptr** in modo che la GPU non preoccuparsi di disegnare i pixel.</span><span class="sxs-lookup"><span data-stu-id="a32d8-250">In this configuration, we don't attach a render target view, and the mesh renderer sets the pixel shader stage to **nullptr** so that the GPU doesn't bother to draw pixels.</span></span> <span data-ttu-id="a32d8-251">La geometria sarà rasterizzato al buffer di profondità e la pipeline grafica verrà interrotta non esiste.</span><span class="sxs-lookup"><span data-stu-id="a32d8-251">The geometry will be rasterized to the depth buffer, and the graphics pipeline will stop there.</span></span>

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

<span data-ttu-id="a32d8-252">È possibile trarre vntana con un test di profondità con il buffer di relative all'occlusione di Mapping nell'area.</span><span class="sxs-lookup"><span data-stu-id="a32d8-252">We can draw holograms with an extra depth test against the Surface Mapping occlusion buffer.</span></span> <span data-ttu-id="a32d8-253">Nell'esempio di codice, si esegue il rendering pixel sul cubo un colore diverso se sono protetti da una superficie.</span><span class="sxs-lookup"><span data-stu-id="a32d8-253">In this code sample, we render pixels on the cube a different color if they are behind a surface.</span></span>

<span data-ttu-id="a32d8-254">Da AppMain.cpp:</span><span class="sxs-lookup"><span data-stu-id="a32d8-254">From AppMain.cpp:</span></span>

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

<span data-ttu-id="a32d8-255">Basato su codice da SpecialEffectPixelShader.hlsl:</span><span class="sxs-lookup"><span data-stu-id="a32d8-255">Based on code from SpecialEffectPixelShader.hlsl:</span></span>

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

<span data-ttu-id="a32d8-256">**Nota:** Per i **GatherDepthLess** routine, vedere l'esempio di codice nell'area di Mapping: SpecialEffectPixelShader.hlsl.</span><span class="sxs-lookup"><span data-stu-id="a32d8-256">**Note:** For our **GatherDepthLess** routine, see the Surface Mapping code sample: SpecialEffectPixelShader.hlsl.</span></span>

<span data-ttu-id="a32d8-257">**Dati di trama della superficie di rendering sullo schermo**</span><span class="sxs-lookup"><span data-stu-id="a32d8-257">**Rendering surface mesh data to the display**</span></span>

<span data-ttu-id="a32d8-258">È anche possibile trarre le reti mesh di surface ai buffer di visualizzazione stereo.</span><span class="sxs-lookup"><span data-stu-id="a32d8-258">We can also just draw the surface meshes to the stereo display buffers.</span></span> <span data-ttu-id="a32d8-259">È stato scelto di tracciare i volti completi con illuminazione, ma è possibile disegnare wireframe, elaborare mesh prima del rendering, applicare una mappa di trama e così via.</span><span class="sxs-lookup"><span data-stu-id="a32d8-259">We chose to draw full faces with lighting, but you're free to draw wireframe, process meshes before rendering, apply a texture map, and so on.</span></span>

<span data-ttu-id="a32d8-260">In questo caso, l'esempio di codice indica il renderer mesh per disegnare la raccolta.</span><span class="sxs-lookup"><span data-stu-id="a32d8-260">Here, our code sample tells the mesh renderer to draw the collection.</span></span> <span data-ttu-id="a32d8-261">Questa volta non viene specificato pass solo profondità, in modo che verrà allegare un pixel shader e completare la pipeline di rendering utilizzando le destinazioni che è stata specificata la fotocamera virtuale corrente.</span><span class="sxs-lookup"><span data-stu-id="a32d8-261">This time we don't specify a depth-only pass, so it will attach a pixel shader and complete the rendering pipeline using the targets that we specified for the current virtual camera.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a32d8-262">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a32d8-262">See also</span></span>
* [<span data-ttu-id="a32d8-263">Creazione di un progetto di DirectX holographic</span><span class="sxs-lookup"><span data-stu-id="a32d8-263">Creating a holographic DirectX project</span></span>](creating-a-holographic-directx-project.md)
* [<span data-ttu-id="a32d8-264">Windows.Perception.Spatial API</span><span class="sxs-lookup"><span data-stu-id="a32d8-264">Windows.Perception.Spatial API</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)

---
title: Mapping spaziale in Unity
description: Il rendering e che entrino in conflitto con la geometria del mondo reale si in Unity.
author: davidkline-ms
ms.author: davidkl
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, mapping spaziale, renderer, collider, rete, l'analisi, componente
ms.openlocfilehash: 8f7bad1651ab31b2e83ad9d9c8f465547fbbdc5a
ms.sourcegitcommit: 2f600e5ad00cd447b180b0f89192b4b9d86bbc7e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/15/2019
ms.locfileid: "67148644"
---
# <a name="spatial-mapping-in-unity"></a><span data-ttu-id="557c2-104">Mapping spaziale in Unity</span><span class="sxs-lookup"><span data-stu-id="557c2-104">Spatial mapping in Unity</span></span>

<span data-ttu-id="557c2-105">In questo argomento viene descritto come utilizzare [mapping spaziale](spatial-mapping.md) nel progetto Unity, il recupero triangolari che rappresentano aree nel mondo intorno a un dispositivo HoloLens, per il posizionamento, relative all'occlusione, chat room analisi e altro ancora.</span><span class="sxs-lookup"><span data-stu-id="557c2-105">This topic describes how to use [spatial mapping](spatial-mapping.md) in your Unity project, retrieving triangle meshes that represent the surfaces in the world around a HoloLens device, for placement, occlusion, room analysis and more.</span></span>

<span data-ttu-id="557c2-106">Unity include il supporto completo per il mapping spaziale, che viene esposto agli sviluppatori nei modi seguenti:</span><span class="sxs-lookup"><span data-stu-id="557c2-106">Unity includes full support for spatial mapping, which is exposed to developers in the following ways:</span></span>
1. <span data-ttu-id="557c2-107">I componenti disponibili nel MixedRealityToolkit mapping spaziale, che forniscono un percorso semplice e rapido per iniziare con mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="557c2-107">Spatial mapping components available in the MixedRealityToolkit, which provide a convenient and rapid path for getting started with spatial mapping</span></span>
2. <span data-ttu-id="557c2-108">Mapping spaziale di basso livello API, che forniscono completo controllare e abilitare più sofisticate di personalizzazione specifici dell'applicazione</span><span class="sxs-lookup"><span data-stu-id="557c2-108">Lower-level spatial mapping APIs, which provide full control and enable more sophisticated application specific customization</span></span>

<span data-ttu-id="557c2-109">Per usare mapping spaziale nell'app, la funzionalità spatialPerception deve essere impostata nella finestra di AppxManifest.</span><span class="sxs-lookup"><span data-stu-id="557c2-109">To use spatial mapping in your app, the spatialPerception capability needs to be set in your AppxManifest.</span></span>

## <a name="setting-the-spatialperception-capability"></a><span data-ttu-id="557c2-110">Impostare la funzionalità SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="557c2-110">Setting the SpatialPerception capability</span></span>

<span data-ttu-id="557c2-111">Affinché un'app utilizzare i dati di mapping spaziale, è necessario abilitare la funzionalità SpatialPerception.</span><span class="sxs-lookup"><span data-stu-id="557c2-111">In order for an app to consume spatial mapping data, the SpatialPerception capability must be enabled.</span></span>

<span data-ttu-id="557c2-112">Come abilitare la funzionalità SpatialPerception:</span><span class="sxs-lookup"><span data-stu-id="557c2-112">How to enable the SpatialPerception capability:</span></span>
1. <span data-ttu-id="557c2-113">Nell'Editor di Unity, aprire il **"Windows Media Player Settings"** riquadro (Modifica > Impostazioni di progetto > Windows Media Player)</span><span class="sxs-lookup"><span data-stu-id="557c2-113">In the Unity Editor, open the **"Player Settings"** pane (Edit > Project Settings > Player)</span></span>
2. <span data-ttu-id="557c2-114">Fare clic sui **"Windows Store"** scheda</span><span class="sxs-lookup"><span data-stu-id="557c2-114">Click on the **"Windows Store"** tab</span></span>
3. <span data-ttu-id="557c2-115">Espandere **"Impostazioni di pubblicazione"** e selezionare il **"SpatialPerception"** funzionalità nel **"Funzionalità"** elenco</span><span class="sxs-lookup"><span data-stu-id="557c2-115">Expand **"Publishing Settings"** and check the **"SpatialPerception"** capability in the **"Capabilities"** list</span></span>

<span data-ttu-id="557c2-116">Si noti che se è già stato esportato il progetto di Unity a una soluzione di Visual Studio, è necessario esportare in una nuova cartella o manualmente [impostare questa funzionalità in AppxManifest in Visual Studio](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span><span class="sxs-lookup"><span data-stu-id="557c2-116">Note that if you have already exported your Unity project to a Visual Studio solution, you will need to either export to a new folder or manually [set this capability in the AppxManifest in Visual Studio](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span></span>

<span data-ttu-id="557c2-117">Mapping spaziale richiede inoltre un MaxVersionTested di 10.0.10586.0 almeno:</span><span class="sxs-lookup"><span data-stu-id="557c2-117">Spatial mapping also requires a MaxVersionTested of at least 10.0.10586.0:</span></span>
1. <span data-ttu-id="557c2-118">In Visual Studio, fare clic sulla **package. appxmanifest** in Esplora soluzioni e selezionare **Visualizza codice**</span><span class="sxs-lookup"><span data-stu-id="557c2-118">In Visual Studio, right click on **Package.appxmanifest** in the Solution Explorer and select **View Code**</span></span>
2. <span data-ttu-id="557c2-119">Trovare la riga che specifica **TargetDeviceFamily** e modificare **MaxVersionTested = "10.0.10240.0"** a **MaxVersionTested "Version=10.0.10586.0"**</span><span class="sxs-lookup"><span data-stu-id="557c2-119">Find the line specifying **TargetDeviceFamily** and change **MaxVersionTested="10.0.10240.0"** to **MaxVersionTested="10.0.10586.0"**</span></span>
3. <span data-ttu-id="557c2-120">**Salvare** il package. appxmanifest.</span><span class="sxs-lookup"><span data-stu-id="557c2-120">**Save** the Package.appxmanifest.</span></span>

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a><span data-ttu-id="557c2-121">Introduzione a componenti di mapping spaziale predefiniti di Unity</span><span class="sxs-lookup"><span data-stu-id="557c2-121">Getting started with Unity's built-in spatial mapping components</span></span>

<span data-ttu-id="557c2-122">Unity offre 2 componenti per facilmente aggiunta all'app, mapping spaziale **Renderer Mapping spaziale** e **Collider Mapping spaziale**.</span><span class="sxs-lookup"><span data-stu-id="557c2-122">Unity offers 2 components for easily adding spatial mapping to your app, **Spatial Mapping Renderer** and **Spatial Mapping Collider**.</span></span>

### <a name="spatial-mapping-renderer"></a><span data-ttu-id="557c2-123">Renderer di Mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="557c2-123">Spatial Mapping Renderer</span></span>

<span data-ttu-id="557c2-124">Il Renderer di Mapping spaziale consente la visualizzazione della trama mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="557c2-124">The Spatial Mapping Renderer allows for visualization of the spatial mapping mesh.</span></span>

![Mapping spaziale Renderer in Unity](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a><span data-ttu-id="557c2-126">Mapping spaziale Collider</span><span class="sxs-lookup"><span data-stu-id="557c2-126">Spatial Mapping Collider</span></span>

<span data-ttu-id="557c2-127">L'oggetto Collider Mapping spaziale consente holographic contenuto (o carattere) interazione, ad esempio fisica, con la rete di mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="557c2-127">The Spatial Mapping Collider allows for holographic content (or character) interaction, such as physics, with the spatial mapping mesh.</span></span>

![Mapping spaziale Collider in Unity](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a><span data-ttu-id="557c2-129">Usando i componenti predefiniti mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="557c2-129">Using the built-in spatial mapping components</span></span>

<span data-ttu-id="557c2-130">Se si desidera sia possibile visualizzare e interagire con le superfici fisiche, è possibile aggiungere entrambi i componenti all'app.</span><span class="sxs-lookup"><span data-stu-id="557c2-130">You may add both components to your app if you'd like to both visualize and interact with physical surfaces.</span></span>

<span data-ttu-id="557c2-131">Per usare questi due componenti nell'app Unity:</span><span class="sxs-lookup"><span data-stu-id="557c2-131">To use these two components in your Unity app:</span></span>
1. <span data-ttu-id="557c2-132">Selezionare un GameObject al centro dell'area in cui si desidera rilevare le reti mesh di superficie spaziale.</span><span class="sxs-lookup"><span data-stu-id="557c2-132">Select a GameObject at the center of the area in which you'd like to detect spatial surface meshes.</span></span>
2. <span data-ttu-id="557c2-133">Nella finestra Inspector **Add Component** > **XR** > **Collider Mapping spaziale** o **spaziale Renderer di mapping**.</span><span class="sxs-lookup"><span data-stu-id="557c2-133">In the Inspector window, **Add Component** > **XR** > **Spatial Mapping Collider** or **Spatial Mapping Renderer**.</span></span>

<span data-ttu-id="557c2-134">È possibile trovare altre informazioni su come usare questi componenti al <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">sito della documentazione di Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="557c2-134">You can find more details on how to use these components at the <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity documentation site</a>.</span></span>

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a><span data-ttu-id="557c2-135">Non si limita i componenti predefiniti mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="557c2-135">Going beyond the built-in spatial mapping components</span></span>

<span data-ttu-id="557c2-136">Questi componenti rendono drag-and-drop facile iniziare a usare Mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="557c2-136">These components make it drag-and-drop easy to get started with Spatial Mapping.</span></span> <span data-ttu-id="557c2-137"> Quando si desidera continuare, esistono due modi principali per esplorare:</span><span class="sxs-lookup"><span data-stu-id="557c2-137"> When you want to go further, there are two main paths to explore:</span></span>
* <span data-ttu-id="557c2-138">Per eseguire l'elaborazione di rete di livello inferiore, vedere la sezione seguente sullo script Mapping spaziale a basso livello API.</span><span class="sxs-lookup"><span data-stu-id="557c2-138">To do your own lower-level mesh processing, see the section below about the low-level Spatial Mapping script API.</span></span>
* <span data-ttu-id="557c2-139">Per eseguire analisi di rete di livello superiore, vedere la sezione seguente sulla libreria in SpatialUnderstanding <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>.</span><span class="sxs-lookup"><span data-stu-id="557c2-139">To do higher-level mesh analysis, see the section below about the SpatialUnderstanding library in <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>.</span></span>

## <a name="using-the-low-level-unity-spatial-mapping-api"></a><span data-ttu-id="557c2-140">Con basso livello API di Unity spaziali Mapping</span><span class="sxs-lookup"><span data-stu-id="557c2-140">Using the low-level Unity Spatial Mapping API</span></span>

<span data-ttu-id="557c2-141">Se è necessario maggiore controllo, quella che si dai componenti Renderer Mapping spaziale e Collider Mapping spaziale, è possibile usare lo script Mapping spaziale a basso livello API.</span><span class="sxs-lookup"><span data-stu-id="557c2-141">If you need more control than you get from the Spatial Mapping Renderer and Spatial Mapping Collider components, you can use the low-level Spatial Mapping script APIs.</span></span>

<span data-ttu-id="557c2-142">**Namespace:** *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="557c2-142">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="557c2-143">**Tipi**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*</span><span class="sxs-lookup"><span data-stu-id="557c2-143">**Types**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*</span></span>

<span data-ttu-id="557c2-144">Di seguito è una struttura del flusso di suggerita per un'applicazione che usa l'API di mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="557c2-144">The following is an outline of the suggested flow for an application that uses the spatial mapping APIs.</span></span>

### <a name="set-up-the-surfaceobservers"></a><span data-ttu-id="557c2-145">Configurare il SurfaceObserver(s)</span><span class="sxs-lookup"><span data-stu-id="557c2-145">Set up the SurfaceObserver(s)</span></span>

<span data-ttu-id="557c2-146">Creare un'istanza di un oggetto SurfaceObserver per ogni area definita dall'applicazione di spazio che sono necessari dati di mapping spaziale per.</span><span class="sxs-lookup"><span data-stu-id="557c2-146">Instantiate one SurfaceObserver object for each application-defined region of space that you need spatial mapping data for.</span></span>

```cs
SurfaceObserver surfaceObserver;

 void Start () {
     surfaceObserver = new SurfaceObserver();
 }
```

<span data-ttu-id="557c2-147">Specificare l'area di spazio su ogni oggetto SurfaceObserver verrà recuperati i dati per chiamando SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox o SetVolumeAsFrustum.</span><span class="sxs-lookup"><span data-stu-id="557c2-147">Specify the region of space that each SurfaceObserver object will provide data for by calling either SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox, or SetVolumeAsFrustum.</span></span> <span data-ttu-id="557c2-148">Chiamando semplicemente uno di questi metodi anche in questo caso, è possibile ridefinire l'area di spazio in futuro.</span><span class="sxs-lookup"><span data-stu-id="557c2-148">You can redefine the region of space in the future by simply calling one of these methods again.</span></span>

```cs
void Start () {
    ...
     surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

<span data-ttu-id="557c2-149">Quando si chiama SurfaceObserver.Update(), è necessario fornire un gestore per ogni area spaziale nell'area del SurfaceObserver dello spazio che il sistema di mapping spaziale contiene informazioni per la nuova.</span><span class="sxs-lookup"><span data-stu-id="557c2-149">When you call SurfaceObserver.Update(), you must provide a handler for each spatial surface in the SurfaceObserver's region of space that the spatial mapping system has new information for.</span></span> <span data-ttu-id="557c2-150">Il gestore riceve, per una sola superficie spaziale:</span><span class="sxs-lookup"><span data-stu-id="557c2-150">The handler receives, for one spatial surface:</span></span>

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
 {
    //see Handling Surface Changes
 }
```

### <a name="handling-surface-changes"></a><span data-ttu-id="557c2-151">Gestione delle modifiche di Surface</span><span class="sxs-lookup"><span data-stu-id="557c2-151">Handling Surface Changes</span></span>

<span data-ttu-id="557c2-152">Esistono diversi casi principali per la gestione.</span><span class="sxs-lookup"><span data-stu-id="557c2-152">There are several main cases to handle.</span></span> <span data-ttu-id="557c2-153">Aggiunte e aggiornate che è possono usare lo stesso codice di percorso e rimosso.</span><span class="sxs-lookup"><span data-stu-id="557c2-153">Added & Updated which can use the same code path and Removed.</span></span>
* <span data-ttu-id="557c2-154">Nei casi sono state aggiunte e aggiornate nell'esempio, aggiungere o ottenere il GameObject che rappresenta questo mesh dal dizionario, creare un tipo struct SurfaceData con i componenti necessari, quindi chiamare RequestMeshDataAsync per popolare gli elementi GameObject con i dati di trama e posizione della scena.</span><span class="sxs-lookup"><span data-stu-id="557c2-154">In the Added & Updated cases in the example, we add or get the GameObject representing this mesh from the dictionary, create a SurfaceData struct with the necessary components, then call RequestMeshDataAsync to populate the GameObject with the mesh data and position in the scene.</span></span>
* <span data-ttu-id="557c2-155">In caso di rimozione, è rimuovere gli elementi GameObject che rappresenta questo reticolato dal dizionario ed eliminarla definitivamente.</span><span class="sxs-lookup"><span data-stu-id="557c2-155">In the Removed case, we remove the GameObject representing this mesh from the dictionary and destroy it.</span></span>

```cs
System.Collections.Generic.Dictionary<SurfaceId, GameObject> spatialMeshObjects = 
    new System.Collections.Generic.Dictionary<SurfaceId, GameObject>();

   private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
   {
       switch (changeType)
       {
           case SurfaceChange.Added:
           case SurfaceChange.Updated:
               if (!spatialMeshObjects.ContainsKey(surfaceId))
               {
                   spatialMeshObjects[surfaceId] = new GameObject("spatial-mapping-" + surfaceId);
                   spatialMeshObjects[surfaceId].transform.parent = this.transform;
                   spatialMeshObjects[surfaceId].AddComponent<MeshRenderer>();
               }
               GameObject target = spatialMeshObjects[surfaceId];
               SurfaceData sd = new SurfaceData(
                   //the surface id returned from the system
                   surfaceId,
                   //the mesh filter that is populated with the spatial mapping data for this mesh
                   target.GetComponent<MeshFilter>() ?? target.AddComponent<MeshFilter>(),
                   //the world anchor used to position the spatial mapping mesh in the world
                   target.GetComponent<WorldAnchor>() ?? target.AddComponent<WorldAnchor>(),
                   //the mesh collider that is populated with collider data for this mesh, if true is passed to bakeMeshes below
                   target.GetComponent<MeshCollider>() ?? target.AddComponent<MeshCollider>(),
                   //triangles per cubic meter requested for this mesh
                   1000,
                   //bakeMeshes - if true, the mesh collider is populated, if false, the mesh collider is empty.
                   true
                   );

               SurfaceObserver.RequestMeshAsync(sd, OnDataReady);
               break;
           case SurfaceChange.Removed:
               var obj = spatialMeshObjects[surfaceId];
               spatialMeshObjects.Remove(surfaceId);
               if (obj != null)
               {
                   GameObject.Destroy(obj);
               }
               break;
           default:
               break;
       }
   }
```

### <a name="handling-data-ready"></a><span data-ttu-id="557c2-156">Pronto per la gestione dei dati</span><span class="sxs-lookup"><span data-stu-id="557c2-156">Handling Data Ready</span></span>

<span data-ttu-id="557c2-157">Il gestore OnDataReady riceve un oggetto SurfaceData.</span><span class="sxs-lookup"><span data-stu-id="557c2-157">The OnDataReady handler receives a SurfaceData object.</span></span> <span data-ttu-id="557c2-158">Il WorldAnchor, MeshFilter e (facoltativamente) MeshCollider oggetti in che esso contenuti riflettono lo stato più recente della superficie spaziale associato.</span><span class="sxs-lookup"><span data-stu-id="557c2-158">The WorldAnchor, MeshFilter and (optionally) MeshCollider objects it contains reflect the latest state of the associated spatial surface.</span></span> <span data-ttu-id="557c2-159">Se lo si desidera eseguire l'analisi e/o [elaborazione](spatial-mapping.md#mesh-processing) dei dati per l'accesso al membro della Mesh dell'oggetto MeshFilter mesh.</span><span class="sxs-lookup"><span data-stu-id="557c2-159">Optionally perform analysis and/or [processing](spatial-mapping.md#mesh-processing) of the mesh data by accessing the Mesh member of the MeshFilter object.</span></span> <span data-ttu-id="557c2-160">Il rendering dell'area spaziale con la rete di più recente e (facoltativamente) usato per i conflitti di fisica e raycasts.</span><span class="sxs-lookup"><span data-stu-id="557c2-160">Render the spatial surface with the latest mesh and (optionally) use it for physics collisions and raycasts.</span></span> <span data-ttu-id="557c2-161">È importante verificare che il contenuto della finestra di SurfaceData non sia null.</span><span class="sxs-lookup"><span data-stu-id="557c2-161">It's important to confirm that the contents of the SurfaceData are not null.</span></span>

### <a name="start-processing-on-updates"></a><span data-ttu-id="557c2-162">Iniziare a elaborare gli aggiornamenti</span><span class="sxs-lookup"><span data-stu-id="557c2-162">Start processing on updates</span></span>

<span data-ttu-id="557c2-163">SurfaceObserver.Update() deve essere chiamato su un ritardo, non per ogni fotogramma.</span><span class="sxs-lookup"><span data-stu-id="557c2-163">SurfaceObserver.Update() should be called on a delay, not every frame.</span></span>

```cs
void Start () {
    ...
     StartCoroutine(UpdateLoop());
}

 IEnumerator UpdateLoop()
    {
        var wait = new WaitForSeconds(2.5f);
        while(true)
        {
            surfaceObserver.Update(OnSurfaceChanged);
            yield return wait;
        }
    }
```

## <a name="higher-level-mesh-analysis-spatialunderstanding"></a><span data-ttu-id="557c2-164">Analisi di rete mesh di livello superiore: SpatialUnderstanding</span><span class="sxs-lookup"><span data-stu-id="557c2-164">Higher-level mesh analysis: SpatialUnderstanding</span></span>

<span data-ttu-id="557c2-165">Il <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> è una raccolta di codice di utilità utili per lo sviluppo holographic basato sull'API di Unity holographic.</span><span class="sxs-lookup"><span data-stu-id="557c2-165">The <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> is a collection of helpful utility code for holographic development built upon the holographic Unity APIs.</span></span>

### <a name="spatial-understanding"></a><span data-ttu-id="557c2-166">Understanding spaziali</span><span class="sxs-lookup"><span data-stu-id="557c2-166">Spatial Understanding</span></span>

<span data-ttu-id="557c2-167">Quando si posiziona vntana nel mondo fisico è spesso utile andare oltre mapping spaziale mesh e regolatori della superficie di attacco.</span><span class="sxs-lookup"><span data-stu-id="557c2-167">When placing holograms in the physical world it is often desirable to go beyond spatial mapping’s mesh and surface planes.</span></span> <span data-ttu-id="557c2-168">Al termine posizionamento modo procedurale, è consigliabile un livello superiore di comprensione dell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="557c2-168">When placement is done procedurally, a higher level of environmental understanding is desirable.</span></span> <span data-ttu-id="557c2-169">È in genere necessario prendere decisioni sulle novità walls, floor e ceiling.</span><span class="sxs-lookup"><span data-stu-id="557c2-169">This usually requires making decisions about what is floor, ceiling, and walls.</span></span> <span data-ttu-id="557c2-170">Inoltre, la possibilità di ottimizzare rispetto a un set di vincoli di posizionamento per determinare i percorsi fisici più utile per gli oggetti holographic.</span><span class="sxs-lookup"><span data-stu-id="557c2-170">In addition, the ability to optimize against a set of placement constraints to determining the most desirable physical locations for holographic objects.</span></span>

<span data-ttu-id="557c2-171">Durante lo sviluppo di Conker Young e frammenti, Studios Asobo affrontato head questo problema in sviluppo Risolutore di chat room per questo scopo.</span><span class="sxs-lookup"><span data-stu-id="557c2-171">During the development of Young Conker and Fragments, Asobo Studios faced this problem head on, developing a room solver for this purpose.</span></span> <span data-ttu-id="557c2-172">Ognuno di questi giochi ha esigenze specifiche dei giochi, ma quelle condivise informazioni spaziali sulla tecnologia di base.</span><span class="sxs-lookup"><span data-stu-id="557c2-172">Each of these games had game specific needs, but they shared core spatial understanding technology.</span></span> <span data-ttu-id="557c2-173">Il HoloToolkit.SpatialUnderstanding libreria incapsula questa tecnologia, consentendo di rapidamente trovare gli spazi vuoti nelle pareti, collocare oggetti nel tetto massimo, identificare inserito per carattere per un periodo e una miriade di altre query spaziali comprensione.</span><span class="sxs-lookup"><span data-stu-id="557c2-173">The HoloToolkit.SpatialUnderstanding library encapsulates this technology, allowing you to quickly find empty spaces on the walls, place objects on the ceiling, identify placed for character to sit, and a myriad of other spatial understanding queries.</span></span>

<span data-ttu-id="557c2-174">Tutto il codice sorgente è incluso, consentendo di personalizzarlo in base alle esigenze e condividere i miglioramenti con la community.</span><span class="sxs-lookup"><span data-stu-id="557c2-174">All of the source code is included, allowing you to customize it to your needs and share your improvements with the community.</span></span> <span data-ttu-id="557c2-175">Il codice per il C++ è stato eseguito il wrapping in una dll UWP ed esposto a Unity con una diminuzione prefab contenuti all'interno di MixedRealityToolkit Risolutore.</span><span class="sxs-lookup"><span data-stu-id="557c2-175">The code for the C++ solver has been wrapped into a UWP dll and exposed to Unity with a drop in prefab contained within the MixedRealityToolkit.</span></span>

### <a name="understanding-modules"></a><span data-ttu-id="557c2-176">Informazioni sui moduli</span><span class="sxs-lookup"><span data-stu-id="557c2-176">Understanding Modules</span></span>

<span data-ttu-id="557c2-177">Sono disponibili tre interfacce principali esposte dal modulo: topologia per area semplice e le query spaziali e forma per il rilevamento di oggetti del Risolutore di selezione host per oggetti per la selezione host di vincoli basato del set di oggetti.</span><span class="sxs-lookup"><span data-stu-id="557c2-177">There are three primary interfaces exposed by the module: topology for simple surface and spatial queries, shape for object detection, and the object placement solver for constraint based placement of object sets.</span></span> <span data-ttu-id="557c2-178">Ognuno di questi è descritto di seguito.</span><span class="sxs-lookup"><span data-stu-id="557c2-178">Each of these is described below.</span></span> <span data-ttu-id="557c2-179">Oltre alle tre interfacce modulo primario, un'interfaccia di eseguire il cast di ray è utilizzabile per recuperare i tipi di area con tag e una rete mesh playspace stagni personalizzati possono essere copiate.</span><span class="sxs-lookup"><span data-stu-id="557c2-179">In addition to the three primary module interfaces, a ray casting interface can be used to retrieve tagged surface types and a custom watertight playspace mesh can be copied out.</span></span>

### <a name="ray-casting"></a><span data-ttu-id="557c2-180">Cast di ray</span><span class="sxs-lookup"><span data-stu-id="557c2-180">Ray Casting</span></span>

<span data-ttu-id="557c2-181">Dopo la chat è stata analizzata e finalizzata, le etichette vengono generate internamente per superfici come walls, floor e ceiling.</span><span class="sxs-lookup"><span data-stu-id="557c2-181">After the room has been scanned and finalized, labels are internally generated for surfaces like the floor, ceiling, and walls.</span></span> <span data-ttu-id="557c2-182">La "PlayspaceRaycast" funzione accetta un raggio e restituisce se il raggio è in conflitto con una superficie nota e in tal caso, informazioni che verranno visualizzati sotto forma di un "RaycastResult".</span><span class="sxs-lookup"><span data-stu-id="557c2-182">The “PlayspaceRaycast” function takes a ray and returns if the ray collides with a known surface and if so, information about that surface in the form of a “RaycastResult”.</span></span>

```cpp
struct RaycastResult
{
    enum SurfaceTypes
    {
        Invalid,    // No intersection
        Other,
        Floor,
        FloorLike,  // Not part of the floor topology, 
                    //  but close to the floor and looks like the floor
        Platform,   // Horizontal platform between the ground and 
                    //  the ceiling
        Ceiling,
        WallExternal,
        WallLike,   // Not part of the external wall surface, 
                    //  but vertical surface that looks like a 
                    //  wall structure
    };
    SurfaceTypes SurfaceType;
    float SurfaceArea;  // Zero if unknown 
                        //  (i.e. if not part of the topology analysis)
    DirectX::XMFLOAT3 IntersectPoint;
    DirectX::XMFLOAT3 IntersectNormal;
};
```

<span data-ttu-id="557c2-183">Internamente, viene calcolato il raycast contro la rappresentazione di voxel calcolata cm 8 al cubo del playspace.</span><span class="sxs-lookup"><span data-stu-id="557c2-183">Internally, the raycast is computed against the computed 8cm cubed voxel representation of the playspace.</span></span> <span data-ttu-id="557c2-184">Ogni voxel contiene un set di elementi della superficie con i dati elaborati topologia (noto anche come surfels).</span><span class="sxs-lookup"><span data-stu-id="557c2-184">Each voxel contains a set of surface elements with processed topology data (aka surfels).</span></span> <span data-ttu-id="557c2-185">Vengono confrontate le surfels contenute all'interno delle celle intersecate voxel e la migliore corrispondenza utilizzata per cercare le informazioni sulla topologia.</span><span class="sxs-lookup"><span data-stu-id="557c2-185">The surfels contained within the intersected voxel cell are compared and the best match used to look up the topology information.</span></span> <span data-ttu-id="557c2-186">Data questa topologia contiene l'assegnazione di etichette restituito in forma di enumerazione "SurfaceTypes", nonché la superficie dell'area di intersezione.</span><span class="sxs-lookup"><span data-stu-id="557c2-186">This topology data contains the labeling returned in the form of the “SurfaceTypes” enum, as well as the surface area of the intersected surface.</span></span>

<span data-ttu-id="557c2-187">Nell'esempio di Unity, il cursore viene eseguito il cast un raggio ogni fotogramma.</span><span class="sxs-lookup"><span data-stu-id="557c2-187">In the Unity sample, the cursor casts a ray each frame.</span></span> <span data-ttu-id="557c2-188">Prima di tutto rispetto colliders di Unity.</span><span class="sxs-lookup"><span data-stu-id="557c2-188">First, against Unity’s colliders.</span></span> <span data-ttu-id="557c2-189">In secondo luogo, sulla rappresentazione mondo del modulo comprensione.</span><span class="sxs-lookup"><span data-stu-id="557c2-189">Second, against the understanding module’s world representation.</span></span> <span data-ttu-id="557c2-190">E infine, anche in questo caso elementi dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="557c2-190">And finally, again UI elements.</span></span> <span data-ttu-id="557c2-191">In questa applicazione, dell'interfaccia utente ottiene quindi priorità, il risultato di comprensione e, infine, colliders di Unity.</span><span class="sxs-lookup"><span data-stu-id="557c2-191">In this application, UI gets priority, next the understanding result, and lastly, Unity’s colliders.</span></span> <span data-ttu-id="557c2-192">Il SurfaceType viene segnalato come testo accanto al cursore.</span><span class="sxs-lookup"><span data-stu-id="557c2-192">The SurfaceType is reported as text next to the cursor.</span></span>

<span data-ttu-id="557c2-193">![Tipo di area con l'etichetta accanto al cursore](images/su-raycastresults-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="557c2-193">![Surface type is labeled next to the cursor](images/su-raycastresults-300px.jpg)</span></span><br>
<span data-ttu-id="557c2-194">*Tipo di area con l'etichetta accanto al cursore*</span><span class="sxs-lookup"><span data-stu-id="557c2-194">*Surface type is labeled next to the cursor*</span></span>

### <a name="topology-queries"></a><span data-ttu-id="557c2-195">Query di topologia</span><span class="sxs-lookup"><span data-stu-id="557c2-195">Topology Queries</span></span>

<span data-ttu-id="557c2-196">All'interno della DLL, gestione della topologia gestisce l'assegnazione di etichette dell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="557c2-196">Within the DLL, the topology manager handles labeling of the environment.</span></span> <span data-ttu-id="557c2-197">Come indicato in precedenza, gran parte dei dati verrà archiviata all'interno di surfels, contenuta all'interno di un volume voxel.</span><span class="sxs-lookup"><span data-stu-id="557c2-197">As mentioned above, much of the data is stored within surfels, contained within a voxel volume.</span></span> <span data-ttu-id="557c2-198">Inoltre, la struttura "PlaySpaceInfos" viene utilizzata per archiviare le informazioni sugli playspace, tra cui l'allineamento world (ulteriori dettagli su questo argomento di seguito), floor e ceiling altezza.</span><span class="sxs-lookup"><span data-stu-id="557c2-198">In addition, the “PlaySpaceInfos” structure is used to store information about the playspace, including the world alignment (more details on this below), floor, and ceiling height.</span></span> <span data-ttu-id="557c2-199">Vengono usate le euristiche per determinare walls, floor e ceiling.</span><span class="sxs-lookup"><span data-stu-id="557c2-199">Heuristics are used for determining floor, ceiling, and walls.</span></span> <span data-ttu-id="557c2-200">Ad esempio, la superficie più grande e più basso orizzontale con maggiore di 1 m2 superficie di attacco è considerata il tetto minimo.</span><span class="sxs-lookup"><span data-stu-id="557c2-200">For example, the largest and lowest horizontal surface with greater than 1 m2 surface area is considered the floor.</span></span> <span data-ttu-id="557c2-201">Si noti che il percorso della fotocamera durante il processo di analisi viene usato anche in questo processo.</span><span class="sxs-lookup"><span data-stu-id="557c2-201">Note that the camera path during the scanning process is also used in this process.</span></span>

<span data-ttu-id="557c2-202">Un subset delle query esposte da Gestione della topologia sono esposte tramite la dll.</span><span class="sxs-lookup"><span data-stu-id="557c2-202">A subset of the queries exposed by the Topology manager are exposed out through the dll.</span></span> <span data-ttu-id="557c2-203">Di seguito sono riportate le query di topologia esposto.</span><span class="sxs-lookup"><span data-stu-id="557c2-203">The exposed topology queries are as follows.</span></span>

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

<span data-ttu-id="557c2-204">Ogni query dispone di un set di parametri, specifici per il tipo di query.</span><span class="sxs-lookup"><span data-stu-id="557c2-204">Each of the queries has a set of parameters, specific to the query type.</span></span> <span data-ttu-id="557c2-205">Nell'esempio seguente, l'utente specifica l'altezza minima & larghezza del volume desiderato, altezza minima posizione di sopra la parte intera e la quantità minima di nulla osta davanti il volume.</span><span class="sxs-lookup"><span data-stu-id="557c2-205">In the following example, the user specifies the minimum height & width of the desired volume, minimum placement height above the floor, and the minimum amount of clearance in front of the volume.</span></span> <span data-ttu-id="557c2-206">Tutte le misure sono in metri.</span><span class="sxs-lookup"><span data-stu-id="557c2-206">All measurements are in meters.</span></span>

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

<span data-ttu-id="557c2-207">Ognuna di queste query accetta una matrice di strutture "TopologyResult" pre-allocata.</span><span class="sxs-lookup"><span data-stu-id="557c2-207">Each of these queries takes a pre-allocated array of “TopologyResult” structures.</span></span> <span data-ttu-id="557c2-208">Il parametro "locationCount" Specifica la lunghezza della matrice passata.</span><span class="sxs-lookup"><span data-stu-id="557c2-208">The “locationCount” parameter specifies the length of the passed in array.</span></span> <span data-ttu-id="557c2-209">Il valore restituito indica il numero di percorsi restituiti.</span><span class="sxs-lookup"><span data-stu-id="557c2-209">The return value reports the number of returned locations.</span></span> <span data-ttu-id="557c2-210">Questo numero non è mai maggiore il valore passato nel parametro "locationCount".</span><span class="sxs-lookup"><span data-stu-id="557c2-210">This number is never greater than the passed in “locationCount” parameter.</span></span>

<span data-ttu-id="557c2-211">"TopologyResult" contiene la posizione centrale del volume restituito, la direzione pubblico (ad esempio normale) e le dimensioni dello spazio trovato.</span><span class="sxs-lookup"><span data-stu-id="557c2-211">The “TopologyResult” contains the center position of the returned volume, the facing direction (i.e. normal), and the dimensions of the found space.</span></span>

```cpp
struct TopologyResult 
{ 
    DirectX::XMFLOAT3 position; 
    DirectX::XMFLOAT3 normal; 
    float width; 
    float length;
};
```

<span data-ttu-id="557c2-212">Si noti che nell'esempio di Unity, ognuna di queste query è collegato a un pulsante nel pannello dell'interfaccia utente virtuale.</span><span class="sxs-lookup"><span data-stu-id="557c2-212">Note that in the Unity sample, each of these queries is linked up to a button in the virtual UI panel.</span></span> <span data-ttu-id="557c2-213">L'esempio rigido codici i parametri per ognuna di queste query valori ragionevoli.</span><span class="sxs-lookup"><span data-stu-id="557c2-213">The sample hard codes the parameters for each of these queries to reasonable values.</span></span> <span data-ttu-id="557c2-214">Nell'esempio di codice per altri esempi, vedere SpaceVisualizer.cs.</span><span class="sxs-lookup"><span data-stu-id="557c2-214">See SpaceVisualizer.cs in the sample code for more examples.</span></span>

### <a name="shape-queries"></a><span data-ttu-id="557c2-215">Query di forma</span><span class="sxs-lookup"><span data-stu-id="557c2-215">Shape Queries</span></span>

<span data-ttu-id="557c2-216">All'interno della dll, l'analizzatore di forma ("ShapeAnalyzer_W") usa l'analizzatore di topologia da confrontare con le forme personalizzate definite dall'utente.</span><span class="sxs-lookup"><span data-stu-id="557c2-216">Inside of the dll, the shape analyzer (“ShapeAnalyzer_W”) uses the topology analyzer to match against custom shapes defined by the user.</span></span> <span data-ttu-id="557c2-217">L'esempio di Unity definisce un set di forme ed espone i risultati out tramite il menu di query in-app, all'interno della scheda di forma. L'obiettivo è che l'utente può definire le proprie query forma di oggetto e rendere utilizzo di questi strumenti, in base alle necessità da parte delle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="557c2-217">The Unity sample defines a set of shapes and exposes the results out through the in-app query menu, within the shape tab. The intention is that the user can define their own object shape queries and make use of those, as needed by their application.</span></span>

<span data-ttu-id="557c2-218">Si noti che l'analisi della forma funziona su superfici orizzontale solo.</span><span class="sxs-lookup"><span data-stu-id="557c2-218">Note that the shape analysis works on horizontal surfaces only.</span></span> <span data-ttu-id="557c2-219">Un divano, ad esempio, è definito per l'area di postazione flat e flat cima divano nuovamente.</span><span class="sxs-lookup"><span data-stu-id="557c2-219">A couch, for example, is defined by the flat seat surface and the flat top of the couch back.</span></span> <span data-ttu-id="557c2-220">La query shape è simile per due aree di un determinato intervallo di dimensioni, altezza e aspetto, con due aree delle allineato e connesse.</span><span class="sxs-lookup"><span data-stu-id="557c2-220">The shape query looks for two surfaces of a specific size, height, and aspect range, with the two surfaces aligned and connected.</span></span> <span data-ttu-id="557c2-221">Utilizzando la terminologia di API, il divano postazione e top indietro sono componenti di forma e i requisiti di allineamento sono limitazioni dei componenti di forma.</span><span class="sxs-lookup"><span data-stu-id="557c2-221">Using the APIs terminology, the couch seat and back top are shape components and the alignment requirements are shape component constraints.</span></span>

<span data-ttu-id="557c2-222">Un esempio di query definita nell'esempio di Unity (ShapeDefinition.cs), per gli oggetti "sittable" è come indicato di seguito.</span><span class="sxs-lookup"><span data-stu-id="557c2-222">An example query defined in the Unity sample (ShapeDefinition.cs), for “sittable” objects is as follows.</span></span>

```cs
shapeComponents = new List<ShapeComponent>()
{
    new ShapeComponent(
        new List<ShapeComponentConstraint>()
        {
            ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
            ShapeComponentConstraint.Create_SurfaceCount_Min(1),
            ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
        }
    ),
};
AddShape("Sittable", shapeComponents);
```

<span data-ttu-id="557c2-223">Ogni query shape è definita da un set di componenti di forma, ognuno con un set di limitazioni dei componenti e un set di vincoli di forma che elenca le dipendenze tra i componenti.</span><span class="sxs-lookup"><span data-stu-id="557c2-223">Each shape query is defined by a set of shape components, each with a set of component constraints and a set of shape constraints which listing dependencies between the components.</span></span> <span data-ttu-id="557c2-224">Questo esempio include tre vincoli in una definizione di singoli componenti e senza vincoli di forme tra i componenti (perché è presente un solo componente).</span><span class="sxs-lookup"><span data-stu-id="557c2-224">This example includes three constraints in a single component definition and no shape constraints between components (as there is only one component).</span></span>

<span data-ttu-id="557c2-225">Al contrario, la forma divano presenta due componenti di forma e quattro i vincoli di forma.</span><span class="sxs-lookup"><span data-stu-id="557c2-225">In contrast, the couch shape has two shape components and four shape constraints.</span></span> <span data-ttu-id="557c2-226">Si noti che i componenti vengono identificati tramite il relativo indice nell'elenco dei componenti dell'utente (0 e 1 in questo esempio).</span><span class="sxs-lookup"><span data-stu-id="557c2-226">Note that components are identified by their index in the user’s component list (0 and 1 in this example).</span></span>

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

<span data-ttu-id="557c2-227">Le funzioni wrapper vengono fornite nel modulo di Unity per la creazione di definizioni di forma personalizzata.</span><span class="sxs-lookup"><span data-stu-id="557c2-227">Wrapper functions are provided in the Unity module for easy creation of custom shape definitions.</span></span> <span data-ttu-id="557c2-228">L'elenco completo dei vincoli di componente e la forma è reperibile in "SpatialUnderstandingDll.cs" all'interno di strutture "ShapeConstraint" e "ShapeComponentConstraint".</span><span class="sxs-lookup"><span data-stu-id="557c2-228">The full list of component and shape constraints can be found in “SpatialUnderstandingDll.cs” within the “ShapeComponentConstraint” and the “ShapeConstraint” structures.</span></span>

<span data-ttu-id="557c2-229">![Forma rettangolare è disponibile in questa area](images/su-shapequery-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="557c2-229">![Rectangle shape is found on this surface](images/su-shapequery-300px.jpg)</span></span><br>
<span data-ttu-id="557c2-230">*Forma rettangolare è disponibile in questa area*</span><span class="sxs-lookup"><span data-stu-id="557c2-230">*Rectangle shape is found on this surface*</span></span>

### <a name="object-placement-solver"></a><span data-ttu-id="557c2-231">Oggetto Risolutore di selezione host</span><span class="sxs-lookup"><span data-stu-id="557c2-231">Object Placement Solver</span></span>

<span data-ttu-id="557c2-232">Risolutore di selezione host per l'oggetto è utilizzabile per identificare le posizioni ideale nella chat room fisica per posizionare gli oggetti.</span><span class="sxs-lookup"><span data-stu-id="557c2-232">The object placement solver can be used to identify ideal locations in the physical room to place your objects.</span></span> <span data-ttu-id="557c2-233">Il Risolutore troverà che il miglior fit posizione determinata le regole di oggetti e i vincoli.</span><span class="sxs-lookup"><span data-stu-id="557c2-233">The solver will find the best fit location given the object rules and constraints.</span></span> <span data-ttu-id="557c2-234">Inoltre, le query di oggetto persistono fino a quando l'oggetto è stata rimossa con "Solver_RemoveObject" o "Solver_RemoveAllObjects" chiamate, consentendo vincolata selezione host per oggetti multipli.</span><span class="sxs-lookup"><span data-stu-id="557c2-234">In addition, object queries persist until the object is removed with “Solver_RemoveObject” or “Solver_RemoveAllObjects” calls, allowing constrained multi-object placement.</span></span> <span data-ttu-id="557c2-235">Le query di selezione host per gli oggetti sono costituiti da tre parti: il tipo con parametri, un elenco di regole e un elenco di vincoli di posizionamento.</span><span class="sxs-lookup"><span data-stu-id="557c2-235">Objects placement queries consist of three parts: placement type with parameters, a list of rules, and a list of constraints.</span></span> <span data-ttu-id="557c2-236">Per eseguire una query, usare l'API seguente.</span><span class="sxs-lookup"><span data-stu-id="557c2-236">To run a query, use the following API.</span></span>

```cpp
public static int Solver_PlaceObject(
            [In] string objectName,
            [In] IntPtr placementDefinition,        // ObjectPlacementDefinition
            [In] int placementRuleCount,
            [In] IntPtr placementRules,             // ObjectPlacementRule
            [In] int constraintCount,
            [In] IntPtr placementConstraints,       // ObjectPlacementConstraint
            [Out] IntPtr placementResult)
```

<span data-ttu-id="557c2-237">Questa funzione accetta un nome di oggetto, definizione di selezione host e un elenco delle regole e dei vincoli.</span><span class="sxs-lookup"><span data-stu-id="557c2-237">This function takes an object name, placement definition, and a list of rules and constraints.</span></span> <span data-ttu-id="557c2-238">Il C# wrapper fornisce costruzione funzioni helper per semplificare la costruzione di regole e dei vincoli.</span><span class="sxs-lookup"><span data-stu-id="557c2-238">The C# wrappers provides construction helper functions to make rule and constraint construction easy.</span></span> <span data-ttu-id="557c2-239">La definizione di selezione host contiene il tipo di query, vale a dire, uno dei seguenti.</span><span class="sxs-lookup"><span data-stu-id="557c2-239">The placement definition contains the query type – that is, one of the following.</span></span>

```cpp
public enum PlacementType
            {
                Place_OnFloor,
                Place_OnWall,
                Place_OnCeiling,
                Place_OnShape,
                Place_OnEdge,
                Place_OnFloorAndCeiling,
                Place_RandomInAir,
                Place_InMidAir,
                Place_UnderFurnitureEdge,
            };
```

<span data-ttu-id="557c2-240">Ognuno dei tipi di selezione host dispone di un set di parametri univoci per il tipo.</span><span class="sxs-lookup"><span data-stu-id="557c2-240">Each of the placement types has a set of parameters unique to the type.</span></span> <span data-ttu-id="557c2-241">La struttura "ObjectPlacementDefinition" contiene un set di funzioni di supporto statici per la creazione di queste definizioni.</span><span class="sxs-lookup"><span data-stu-id="557c2-241">The “ObjectPlacementDefinition” structure contains a set of static helper functions for creating these definitions.</span></span> <span data-ttu-id="557c2-242">Per trovare una posizione in cui inserire un oggetto nell'ambiente operativo, ad esempio, è possibile usare la funzione seguente.</span><span class="sxs-lookup"><span data-stu-id="557c2-242">For example, to find a place to put an object on the floor, you can use the following function.</span></span> <span data-ttu-id="557c2-243">pubblico statico ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) oltre al tipo di selezione host, è possibile fornire un set di regole e i vincoli.</span><span class="sxs-lookup"><span data-stu-id="557c2-243">public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) In addition to the placement type, you can provide a set of rules and constraints.</span></span> <span data-ttu-id="557c2-244">Regole non possono essere violate.</span><span class="sxs-lookup"><span data-stu-id="557c2-244">Rules cannot be violated.</span></span> <span data-ttu-id="557c2-245">Percorsi selezione host per possibili che soddisfano il tipo e le regole sono ottimizzati quindi a fronte del set di vincoli per poter selezionare il percorso di posizionamento ottimale.</span><span class="sxs-lookup"><span data-stu-id="557c2-245">Possible placement locations that satisfy the type and rules are then optimized against the set of constraints in order to select the optimal placement location.</span></span> <span data-ttu-id="557c2-246">Ognuna delle regole e i vincoli può essere creata da funzioni di creazione statici specificato.</span><span class="sxs-lookup"><span data-stu-id="557c2-246">Each of the rules and constraints can be created by the provided static creation functions.</span></span> <span data-ttu-id="557c2-247">Una funzione di costruzione regole e dei vincoli di esempio è disponibili sotto.</span><span class="sxs-lookup"><span data-stu-id="557c2-247">An example rule and constraint construction function is provided below.</span></span>

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

<span data-ttu-id="557c2-248">Il seguente oggetto query di selezione host sta cercando una posizione in cui inserire un misuratore metà cubo sul bordo di una superficie, da altra in precedenza posizionare gli oggetti e vicino al centro della chat room.</span><span class="sxs-lookup"><span data-stu-id="557c2-248">The below object placement query is looking for a place to put a half meter cube on the edge of a surface, away from other previously place objects and near the center of the room.</span></span>

```cs
List<ObjectPlacementRule> rules = 
    new List<ObjectPlacementRule>() {
        ObjectPlacementRule.Create_AwayFromOtherObjects(1.0f),
    };

List<ObjectPlacementConstraint> constraints = 
    new List<ObjectPlacementConstraint> {
        ObjectPlacementConstraint.Create_NearCenter(),
    };

Solver_PlaceObject(
    “MyCustomObject”,
    new ObjectPlacementDefinition.Create_OnEdge(
        new Vector3(0.25f, 0.25f, 0.25f), 
        new Vector3(0.25f, 0.25f, 0.25f)),
    rules.Count,
    UnderstandingDLL.PinObject(rules.ToArray()),
    constraints.Count,
    UnderstandingDLL.PinObject(constraints.ToArray()),
    UnderstandingDLL.GetStaticObjectPlacementResultPtr());
```

<span data-ttu-id="557c2-249">Se ha esito positivo, una struttura di "ObjectPlacementResult" contenente la posizione di posizionamento, dimensioni e orientamento viene restituito.</span><span class="sxs-lookup"><span data-stu-id="557c2-249">If successful, a “ObjectPlacementResult” structure containing the placement position, dimensions and orientation is returned.</span></span> <span data-ttu-id="557c2-250">Inoltre, la selezione host viene aggiunto all'elenco interno della dll di oggetti inseriti.</span><span class="sxs-lookup"><span data-stu-id="557c2-250">In addition, the placement is added to the dll’s internal list of placed objects.</span></span> <span data-ttu-id="557c2-251">Le query di selezione successiva dovrà tener conto di questo oggetto.</span><span class="sxs-lookup"><span data-stu-id="557c2-251">Subsequent placement queries will take this object into account.</span></span> <span data-ttu-id="557c2-252">Il file "LevelSolver.cs" nell'esempio di Unity contiene più query di esempio.</span><span class="sxs-lookup"><span data-stu-id="557c2-252">The “LevelSolver.cs” file in the Unity sample contains more example queries.</span></span>

<span data-ttu-id="557c2-253">![Risultati della selezione host per oggetto](images/su-objectplacement-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="557c2-253">![Results of object placement](images/su-objectplacement-1000px.jpg)</span></span><br>
<span data-ttu-id="557c2-254">*Figura 3: Caselle blu come il risultato da tre posizione floor esegue una query con lontano da regole di posizione della fotocamera*</span><span class="sxs-lookup"><span data-stu-id="557c2-254">*Figure 3: The blue boxes how the result from three place on floor queries with away from camera position rules*</span></span>

<span data-ttu-id="557c2-255">Durante la risoluzione per il percorso di posizionamento di più oggetti necessari per uno scenario di applicazione o a un livello, risolvere innanzitutto gli oggetti indispensabili e grandi dimensioni in ordine di ottimizzazione della probabilità che può essere trovato uno spazio.</span><span class="sxs-lookup"><span data-stu-id="557c2-255">When solving for placement location of multiple objects required for a level or application scenario, first solve indispensable and large objects in order to maximizing the probability that a space can be found.</span></span> <span data-ttu-id="557c2-256">Ordine di inserimento è importante.</span><span class="sxs-lookup"><span data-stu-id="557c2-256">Placement order is important.</span></span> <span data-ttu-id="557c2-257">Se selezioni host per oggetti non viene trovato, provare a configurazioni meno vincolate.</span><span class="sxs-lookup"><span data-stu-id="557c2-257">If object placements cannot be found, try less constrained configurations.</span></span> <span data-ttu-id="557c2-258">Un set di configurazioni di fallback è fondamentale per la funzionalità di supporto in molte configurazioni di chat room.</span><span class="sxs-lookup"><span data-stu-id="557c2-258">Having a set of fallback configurations is critical to supporting functionality across many room configurations.</span></span>

### <a name="room-scanning-process"></a><span data-ttu-id="557c2-259">Processo di analisi chat room</span><span class="sxs-lookup"><span data-stu-id="557c2-259">Room Scanning Process</span></span>

<span data-ttu-id="557c2-260">Mentre la soluzione di mapping spaziale fornita da di HoloLens è progettata per essere abbastanza generici per soddisfare le esigenze dell'intera gamma di aree di problemi, il modulo understanding spaziale è stato compilato per supportare le esigenze dei giochi specifiche due.</span><span class="sxs-lookup"><span data-stu-id="557c2-260">While the spatial mapping solution provided by the HoloLens is designed to be generic enough to meet the needs of the entire gamut of problem spaces, the spatial understanding module was built to support the needs of two specific games.</span></span> <span data-ttu-id="557c2-261">La soluzione è strutturata su un processo specifico e un set dei presupposti, riepilogate di seguito.</span><span class="sxs-lookup"><span data-stu-id="557c2-261">Its solution is structured around a specific process and set of assumptions, summarized below.</span></span>

```
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process – 
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace. 
    Query functions will not function until after the scan has been finalized.
```

<span data-ttu-id="557c2-262">Utente basato sui playspace "disegno" – durante la fase di analisi, l'utente si sposta e Cerca intorno al passo, la riproduzione della grafica in modo efficace le aree che devono essere incluse.</span><span class="sxs-lookup"><span data-stu-id="557c2-262">User driven playspace “painting” – During the scanning phase, the user moves and looks around the plays pace, effectively painting the areas which should be included.</span></span> <span data-ttu-id="557c2-263">La trama generata è importante fornire commenti e suggerimenti utente durante questa fase.</span><span class="sxs-lookup"><span data-stu-id="557c2-263">The generated mesh is important to provide user feedback during this phase.</span></span> <span data-ttu-id="557c2-264">In ambienti chiusi home o l'installazione di office: la query funzioni sono progettate sulla base di superfici flat e walls ad angolo retto.</span><span class="sxs-lookup"><span data-stu-id="557c2-264">Indoors home or office setup – The query functions are designed around flat surfaces and walls at right angles.</span></span> <span data-ttu-id="557c2-265">Si tratta di una limitazione temporanea.</span><span class="sxs-lookup"><span data-stu-id="557c2-265">This is a soft limitation.</span></span> <span data-ttu-id="557c2-266">Tuttavia, durante la fase di analisi, un'asse primario viene completata l'analisi per ottimizzare la suddivisione a mosaico di mesh lungo l'asse principale e secondaria.</span><span class="sxs-lookup"><span data-stu-id="557c2-266">However, during the scanning phase, a primary axis analysis is completed to optimize the mesh tessellation along major and minor axis.</span></span> <span data-ttu-id="557c2-267">Il file SpatialUnderstanding.cs incluso gestisce il processo di fase di analisi.</span><span class="sxs-lookup"><span data-stu-id="557c2-267">The included SpatialUnderstanding.cs file manages the scanning phase process.</span></span> <span data-ttu-id="557c2-268">Chiama le funzioni seguenti.</span><span class="sxs-lookup"><span data-stu-id="557c2-268">It calls the following functions.</span></span>

```
SpatialUnderstanding_Init – Called once at the start.

GeneratePlayspace_InitScan – Indicates that the scan phase should begin.

GeneratePlayspace_UpdateScan_DynamicScan – 
    Called each frame to update the scanning process. The camera position and 
    orientation is passed in and is used for the playspace painting process, 
    described above.

GeneratePlayspace_RequestFinish – 
    Called to finalize the playspace. This will use the areas “painted” during 
    the scan phase to define and lock the playspace. The application can query 
    statistics during the scanning phase as well as query the custom mesh for 
    providing user feedback.

Import_UnderstandingMesh – 
    During scanning, the “SpatialUnderstandingCustomMesh” behavior provided by 
    the module and placed on the understanding prefab will periodically query the 
    custom mesh generated by the process. In addition, this is done once more 
    after scanning has been finalized.
```

<span data-ttu-id="557c2-269">Il flusso di analisi, dovuto il comportamento di "SpatialUnderstanding" chiama il metodo InitScan, UpdateScan ogni fotogramma.</span><span class="sxs-lookup"><span data-stu-id="557c2-269">The scanning flow, driven by the “SpatialUnderstanding” behavior calls InitScan, then UpdateScan each frame.</span></span> <span data-ttu-id="557c2-270">Durante la query statistiche report code coverage ragionevole, l'utente è autorizzato a airtap chiamare RequestFinish per indicare la fine della fase di analisi.</span><span class="sxs-lookup"><span data-stu-id="557c2-270">When the statistics query reports reasonable coverage, the user is allowed to airtap to call RequestFinish to indicate the end of the scanning phase.</span></span> <span data-ttu-id="557c2-271">UpdateScan continua a essere chiamato finché non viene restituito il valore indica che la dll è stata completata l'elaborazione.</span><span class="sxs-lookup"><span data-stu-id="557c2-271">UpdateScan continues to be called until it’s return value indicates that the dll has completed processing.</span></span>

### <a name="understanding-mesh"></a><span data-ttu-id="557c2-272">Informazioni sulle Mesh</span><span class="sxs-lookup"><span data-stu-id="557c2-272">Understanding Mesh</span></span>

<span data-ttu-id="557c2-273">Informazioni sulle dll archivia internamente il playspace come una griglia dei cubi voxel 8cm ridimensionato.</span><span class="sxs-lookup"><span data-stu-id="557c2-273">The understanding dll internally stores the playspace as a grid of 8cm sized voxel cubes.</span></span> <span data-ttu-id="557c2-274">Durante la parte iniziale di analisi, per determinare gli assi della chat room viene completata un'analisi in componenti principali.</span><span class="sxs-lookup"><span data-stu-id="557c2-274">During the initial part of scanning, a primary component analysis is completed to determine the axes of the room.</span></span> <span data-ttu-id="557c2-275">Archivia internamente, il relativo spazio voxel allineato a questi assi.</span><span class="sxs-lookup"><span data-stu-id="557c2-275">Internally, it stores its voxel space aligned to these axes.</span></span> <span data-ttu-id="557c2-276">Una rete mesh viene generata circa ogni secondo, estraendo l'oggetto isosurface dal volume voxel.</span><span class="sxs-lookup"><span data-stu-id="557c2-276">A mesh is generated approximately every second by extracting the isosurface from the voxel volume.</span></span> 

<span data-ttu-id="557c2-277">![Mesh generato prodotta dal volume voxel](images/su-custommesh.jpg)</span><span class="sxs-lookup"><span data-stu-id="557c2-277">![Generated mesh produced from the voxel volume](images/su-custommesh.jpg)</span></span><br>
<span data-ttu-id="557c2-278">*Mesh generato prodotta dal volume voxel*</span><span class="sxs-lookup"><span data-stu-id="557c2-278">*Generated mesh produced from the voxel volume*</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="557c2-279">Risoluzione dei problemi</span><span class="sxs-lookup"><span data-stu-id="557c2-279">Troubleshooting</span></span>
* <span data-ttu-id="557c2-280">Assicurarsi di aver impostato la [SpatialPerception](#setting-the-spatialperception-capability) funzionalità</span><span class="sxs-lookup"><span data-stu-id="557c2-280">Ensure you have set the [SpatialPerception](#setting-the-spatialperception-capability) capability</span></span>
* <span data-ttu-id="557c2-281">Quando il rilevamento viene perso, il successivo evento OnSurfaceChanged rimuoverà tutte le reti mesh.</span><span class="sxs-lookup"><span data-stu-id="557c2-281">When tracking is lost, the next OnSurfaceChanged event will remove all meshes.</span></span>

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a><span data-ttu-id="557c2-282">Mapping spaziale nel Toolkit di realtà mista</span><span class="sxs-lookup"><span data-stu-id="557c2-282">Spatial Mapping in Mixed Reality Toolkit</span></span>
<span data-ttu-id="557c2-283">Per altre informazioni sull'uso di Mapping spaziale con v2 Toolkit di realtà mista, vedere la <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">sezione consapevolezza spaziali</a> della documentazione MRTK.</span><span class="sxs-lookup"><span data-stu-id="557c2-283">For more information on using Spatial Mapping with Mixed Reality Toolkit v2, see the <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">Spatial Awareness section</a> of the MRTK docs.</span></span>

## <a name="see-also"></a><span data-ttu-id="557c2-284">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="557c2-284">See also</span></span>
* [<span data-ttu-id="557c2-285">Spaziale MR 230: Mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="557c2-285">MR Spatial 230: Spatial mapping</span></span>](holograms-230.md)
* [<span data-ttu-id="557c2-286">Sistemi di coordinate</span><span class="sxs-lookup"><span data-stu-id="557c2-286">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="557c2-287">Sistemi di coordinate in Unity</span><span class="sxs-lookup"><span data-stu-id="557c2-287">Coordinate systems in Unity</span></span>](coordinate-systems-in-unity.md)
* <span data-ttu-id="557c2-288"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span><span class="sxs-lookup"><span data-stu-id="557c2-288"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span></span>
* <span data-ttu-id="557c2-289"><a href="http://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a></span><span class="sxs-lookup"><span data-stu-id="557c2-289"><a href="http://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a></span></span>
* <span data-ttu-id="557c2-290"><a href="http://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a></span><span class="sxs-lookup"><span data-stu-id="557c2-290"><a href="http://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a></span></span>
* <span data-ttu-id="557c2-291"><a href="http://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a></span><span class="sxs-lookup"><span data-stu-id="557c2-291"><a href="http://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a></span></span>

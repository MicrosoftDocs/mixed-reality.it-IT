---
title: Mapping spaziale in Unity
description: Il rendering e la collisione con la geometria del mondo reale in Unity.
author: davidkline-ms
ms.author: davidkl
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, mapping spaziale, renderer, Collider, mesh, analisi, componente
ms.openlocfilehash: 8f7bad1651ab31b2e83ad9d9c8f465547fbbdc5a
ms.sourcegitcommit: 2f600e5ad00cd447b180b0f89192b4b9d86bbc7e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/15/2019
ms.locfileid: "67148644"
---
# <a name="spatial-mapping-in-unity"></a><span data-ttu-id="332fc-104">Mapping spaziale in Unity</span><span class="sxs-lookup"><span data-stu-id="332fc-104">Spatial mapping in Unity</span></span>

<span data-ttu-id="332fc-105">Questo argomento descrive come usare il [mapping spaziale](spatial-mapping.md) nel progetto Unity, il recupero di mesh triangolari che rappresentano le superfici del mondo intorno a un dispositivo HoloLens, per la selezione, l'occlusione, l'analisi delle chat room e altro ancora.</span><span class="sxs-lookup"><span data-stu-id="332fc-105">This topic describes how to use [spatial mapping](spatial-mapping.md) in your Unity project, retrieving triangle meshes that represent the surfaces in the world around a HoloLens device, for placement, occlusion, room analysis and more.</span></span>

<span data-ttu-id="332fc-106">Unity include il supporto completo per il mapping spaziale, esposto agli sviluppatori nei modi seguenti:</span><span class="sxs-lookup"><span data-stu-id="332fc-106">Unity includes full support for spatial mapping, which is exposed to developers in the following ways:</span></span>
1. <span data-ttu-id="332fc-107">Componenti di mapping spaziale disponibili in MixedRealityToolkit, che offrono un percorso pratico e rapido per iniziare a usare il mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="332fc-107">Spatial mapping components available in the MixedRealityToolkit, which provide a convenient and rapid path for getting started with spatial mapping</span></span>
2. <span data-ttu-id="332fc-108">API di mapping spaziale di basso livello, che offrono il controllo completo e consentono una personalizzazione più sofisticata dell'applicazione</span><span class="sxs-lookup"><span data-stu-id="332fc-108">Lower-level spatial mapping APIs, which provide full control and enable more sophisticated application specific customization</span></span>

<span data-ttu-id="332fc-109">Per usare il mapping spaziale nell'app, è necessario impostare la funzionalità spatialPerception in AppxManifest.</span><span class="sxs-lookup"><span data-stu-id="332fc-109">To use spatial mapping in your app, the spatialPerception capability needs to be set in your AppxManifest.</span></span>

## <a name="setting-the-spatialperception-capability"></a><span data-ttu-id="332fc-110">Impostazione della funzionalità SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="332fc-110">Setting the SpatialPerception capability</span></span>

<span data-ttu-id="332fc-111">Per consentire a un'app di utilizzare i dati di mapping spaziale, è necessario abilitare la funzionalità SpatialPerception.</span><span class="sxs-lookup"><span data-stu-id="332fc-111">In order for an app to consume spatial mapping data, the SpatialPerception capability must be enabled.</span></span>

<span data-ttu-id="332fc-112">Come abilitare la funzionalità SpatialPerception:</span><span class="sxs-lookup"><span data-stu-id="332fc-112">How to enable the SpatialPerception capability:</span></span>
1. <span data-ttu-id="332fc-113">Nell'editor di Unity aprire il riquadro **"Impostazioni lettore"** (modificare > impostazioni progetto > lettore)</span><span class="sxs-lookup"><span data-stu-id="332fc-113">In the Unity Editor, open the **"Player Settings"** pane (Edit > Project Settings > Player)</span></span>
2. <span data-ttu-id="332fc-114">Fare clic sulla scheda **"Windows Store"**</span><span class="sxs-lookup"><span data-stu-id="332fc-114">Click on the **"Windows Store"** tab</span></span>
3. <span data-ttu-id="332fc-115">Espandere **"impostazioni di pubblicazione"** e selezionare la funzionalità **"SpatialPerception"** nell'elenco **"funzionalità"**</span><span class="sxs-lookup"><span data-stu-id="332fc-115">Expand **"Publishing Settings"** and check the **"SpatialPerception"** capability in the **"Capabilities"** list</span></span>

<span data-ttu-id="332fc-116">Si noti che se il progetto Unity è già stato esportato in una soluzione di Visual Studio, sarà necessario eseguire l'esportazione in una nuova cartella o [impostare manualmente questa funzionalità in appxmanifest in Visual Studio](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span><span class="sxs-lookup"><span data-stu-id="332fc-116">Note that if you have already exported your Unity project to a Visual Studio solution, you will need to either export to a new folder or manually [set this capability in the AppxManifest in Visual Studio](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span></span>

<span data-ttu-id="332fc-117">Il mapping spaziale richiede anche un MaxVersionTested di almeno 10.0.10586.0:</span><span class="sxs-lookup"><span data-stu-id="332fc-117">Spatial mapping also requires a MaxVersionTested of at least 10.0.10586.0:</span></span>
1. <span data-ttu-id="332fc-118">In Visual Studio fare clic con il pulsante destro del mouse su **Package. appxmanifest** nel Esplora soluzioni e selezionare **Visualizza codice** .</span><span class="sxs-lookup"><span data-stu-id="332fc-118">In Visual Studio, right click on **Package.appxmanifest** in the Solution Explorer and select **View Code**</span></span>
2. <span data-ttu-id="332fc-119">Trovare la riga che specifica **TargetDeviceFamily** e modificare **MaxVersionTested = "10.0.10240.0"** in **MaxVersionTested = "10.0.10586.0"**</span><span class="sxs-lookup"><span data-stu-id="332fc-119">Find the line specifying **TargetDeviceFamily** and change **MaxVersionTested="10.0.10240.0"** to **MaxVersionTested="10.0.10586.0"**</span></span>
3. <span data-ttu-id="332fc-120">**Salvare** il pacchetto. appxmanifest.</span><span class="sxs-lookup"><span data-stu-id="332fc-120">**Save** the Package.appxmanifest.</span></span>

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a><span data-ttu-id="332fc-121">Introduzione ai componenti di mapping spaziale incorporati di Unity</span><span class="sxs-lookup"><span data-stu-id="332fc-121">Getting started with Unity's built-in spatial mapping components</span></span>

<span data-ttu-id="332fc-122">Unity offre 2 componenti per aggiungere facilmente il mapping spaziale all'app, al **renderer di mapping spaziale** e al **mapping spaziale**.</span><span class="sxs-lookup"><span data-stu-id="332fc-122">Unity offers 2 components for easily adding spatial mapping to your app, **Spatial Mapping Renderer** and **Spatial Mapping Collider**.</span></span>

### <a name="spatial-mapping-renderer"></a><span data-ttu-id="332fc-123">Renderer mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="332fc-123">Spatial Mapping Renderer</span></span>

<span data-ttu-id="332fc-124">Il renderer di mapping spaziale consente la visualizzazione della mesh di mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="332fc-124">The Spatial Mapping Renderer allows for visualization of the spatial mapping mesh.</span></span>

![Renderer di mapping spaziale in Unity](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a><span data-ttu-id="332fc-126">Conflitto di mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="332fc-126">Spatial Mapping Collider</span></span>

<span data-ttu-id="332fc-127">Il mapping spaziale Collider consente l'interazione di contenuto (o carattere) olografico, ad esempio la fisica, con la mesh di mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="332fc-127">The Spatial Mapping Collider allows for holographic content (or character) interaction, such as physics, with the spatial mapping mesh.</span></span>

![Conflitto di mapping spaziale in Unity](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a><span data-ttu-id="332fc-129">Uso dei componenti di mapping spaziale predefiniti</span><span class="sxs-lookup"><span data-stu-id="332fc-129">Using the built-in spatial mapping components</span></span>

<span data-ttu-id="332fc-130">È possibile aggiungere entrambi i componenti all'app se si vuole visualizzare e interagire con le superfici fisiche.</span><span class="sxs-lookup"><span data-stu-id="332fc-130">You may add both components to your app if you'd like to both visualize and interact with physical surfaces.</span></span>

<span data-ttu-id="332fc-131">Per usare questi due componenti nell'app Unity:</span><span class="sxs-lookup"><span data-stu-id="332fc-131">To use these two components in your Unity app:</span></span>
1. <span data-ttu-id="332fc-132">Selezionare un GameObject al centro dell'area in cui si desidera rilevare le mesh della superficie spaziale.</span><span class="sxs-lookup"><span data-stu-id="332fc-132">Select a GameObject at the center of the area in which you'd like to detect spatial surface meshes.</span></span>
2. <span data-ttu-id="332fc-133">Nella finestra di controllo **aggiungere Component** >  > **XR Spatial mapping Spatial** orendererdimapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="332fc-133">In the Inspector window, **Add Component** > **XR** > **Spatial Mapping Collider** or **Spatial Mapping Renderer**.</span></span>

<span data-ttu-id="332fc-134">Per altre informazioni su come usare questi componenti, vedere il sito della <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">documentazione</a>di Unity.</span><span class="sxs-lookup"><span data-stu-id="332fc-134">You can find more details on how to use these components at the <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity documentation site</a>.</span></span>

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a><span data-ttu-id="332fc-135">Superamento dei componenti predefiniti di mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="332fc-135">Going beyond the built-in spatial mapping components</span></span>

<span data-ttu-id="332fc-136">Questi componenti rendono semplice il trascinamento della selezione per iniziare a usare il mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="332fc-136">These components make it drag-and-drop easy to get started with Spatial Mapping.</span></span> <span data-ttu-id="332fc-137"> Quando si vuole proseguire, è possibile esplorare due percorsi principali:</span><span class="sxs-lookup"><span data-stu-id="332fc-137"> When you want to go further, there are two main paths to explore:</span></span>
* <span data-ttu-id="332fc-138">Per eseguire l'elaborazione della mesh di livello inferiore, vedere la sezione seguente sull'API script per il mapping spaziale di basso livello.</span><span class="sxs-lookup"><span data-stu-id="332fc-138">To do your own lower-level mesh processing, see the section below about the low-level Spatial Mapping script API.</span></span>
* <span data-ttu-id="332fc-139">Per eseguire un'analisi della rete di livello superiore, vedere la sezione seguente sulla libreria SpatialUnderstanding in <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>.</span><span class="sxs-lookup"><span data-stu-id="332fc-139">To do higher-level mesh analysis, see the section below about the SpatialUnderstanding library in <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>.</span></span>

## <a name="using-the-low-level-unity-spatial-mapping-api"></a><span data-ttu-id="332fc-140">Uso dell'API di mapping spaziale di Unity di basso livello</span><span class="sxs-lookup"><span data-stu-id="332fc-140">Using the low-level Unity Spatial Mapping API</span></span>

<span data-ttu-id="332fc-141">Se è necessario un maggiore controllo di quanto si ottenga dal renderer di mapping spaziale e dai componenti Collider del mapping spaziale, è possibile usare le API script per il mapping spaziale di basso livello.</span><span class="sxs-lookup"><span data-stu-id="332fc-141">If you need more control than you get from the Spatial Mapping Renderer and Spatial Mapping Collider components, you can use the low-level Spatial Mapping script APIs.</span></span>

<span data-ttu-id="332fc-142">**Spazio dei nomi:** *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="332fc-142">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="332fc-143">**Tipi**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*</span><span class="sxs-lookup"><span data-stu-id="332fc-143">**Types**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*</span></span>

<span data-ttu-id="332fc-144">Di seguito è riportato un contorno del flusso suggerito per un'applicazione che usa le API di mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="332fc-144">The following is an outline of the suggested flow for an application that uses the spatial mapping APIs.</span></span>

### <a name="set-up-the-surfaceobservers"></a><span data-ttu-id="332fc-145">Configurare i SurfaceObserver</span><span class="sxs-lookup"><span data-stu-id="332fc-145">Set up the SurfaceObserver(s)</span></span>

<span data-ttu-id="332fc-146">Creare un'istanza di un oggetto SurfaceObserver per ogni area di spazio definita dall'applicazione per cui sono necessari dati di mapping spaziali.</span><span class="sxs-lookup"><span data-stu-id="332fc-146">Instantiate one SurfaceObserver object for each application-defined region of space that you need spatial mapping data for.</span></span>

```cs
SurfaceObserver surfaceObserver;

 void Start () {
     surfaceObserver = new SurfaceObserver();
 }
```

<span data-ttu-id="332fc-147">Specificare l'area di spazio a cui ogni oggetto SurfaceObserver fornirà i dati chiamando SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox o SetVolumeAsFrustum.</span><span class="sxs-lookup"><span data-stu-id="332fc-147">Specify the region of space that each SurfaceObserver object will provide data for by calling either SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox, or SetVolumeAsFrustum.</span></span> <span data-ttu-id="332fc-148">È possibile ridefinire l'area di spazio in futuro semplicemente richiamando uno di questi metodi.</span><span class="sxs-lookup"><span data-stu-id="332fc-148">You can redefine the region of space in the future by simply calling one of these methods again.</span></span>

```cs
void Start () {
    ...
     surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

<span data-ttu-id="332fc-149">Quando si chiama SurfaceObserver. Update (), è necessario fornire un gestore per ogni superficie spaziale nell'area di spazio di SurfaceObserver per cui il sistema di mapping spaziale dispone di nuove informazioni.</span><span class="sxs-lookup"><span data-stu-id="332fc-149">When you call SurfaceObserver.Update(), you must provide a handler for each spatial surface in the SurfaceObserver's region of space that the spatial mapping system has new information for.</span></span> <span data-ttu-id="332fc-150">Il gestore riceve, per una superficie spaziale:</span><span class="sxs-lookup"><span data-stu-id="332fc-150">The handler receives, for one spatial surface:</span></span>

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
 {
    //see Handling Surface Changes
 }
```

### <a name="handling-surface-changes"></a><span data-ttu-id="332fc-151">Gestione delle modifiche di superficie</span><span class="sxs-lookup"><span data-stu-id="332fc-151">Handling Surface Changes</span></span>

<span data-ttu-id="332fc-152">Esistono diversi casi principali da gestire.</span><span class="sxs-lookup"><span data-stu-id="332fc-152">There are several main cases to handle.</span></span> <span data-ttu-id="332fc-153">Aggiunta & aggiornata che può utilizzare lo stesso percorso di codice e rimossa.</span><span class="sxs-lookup"><span data-stu-id="332fc-153">Added & Updated which can use the same code path and Removed.</span></span>
* <span data-ttu-id="332fc-154">Nei casi aggiunti & aggiornati nell'esempio, si aggiunge o si ottiene il GameObject che rappresenta la mesh dal dizionario, si crea uno struct SurfaceData con i componenti necessari, quindi si chiama RequestMeshDataAsync per popolare il GameObject con i dati mesh e posizione nella scena.</span><span class="sxs-lookup"><span data-stu-id="332fc-154">In the Added & Updated cases in the example, we add or get the GameObject representing this mesh from the dictionary, create a SurfaceData struct with the necessary components, then call RequestMeshDataAsync to populate the GameObject with the mesh data and position in the scene.</span></span>
* <span data-ttu-id="332fc-155">Nel caso rimosso, viene rimosso il GameObject che rappresenta il mesh dal dizionario ed eliminarlo.</span><span class="sxs-lookup"><span data-stu-id="332fc-155">In the Removed case, we remove the GameObject representing this mesh from the dictionary and destroy it.</span></span>

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

### <a name="handling-data-ready"></a><span data-ttu-id="332fc-156">Gestione dei dati pronti</span><span class="sxs-lookup"><span data-stu-id="332fc-156">Handling Data Ready</span></span>

<span data-ttu-id="332fc-157">Il gestore OnDataReady riceve un oggetto SurfaceData.</span><span class="sxs-lookup"><span data-stu-id="332fc-157">The OnDataReady handler receives a SurfaceData object.</span></span> <span data-ttu-id="332fc-158">Gli oggetti WorldAnchor, MeshFilter e (facoltativamente) MeshCollider che contiene riflettono lo stato più recente della superficie spaziale associata.</span><span class="sxs-lookup"><span data-stu-id="332fc-158">The WorldAnchor, MeshFilter and (optionally) MeshCollider objects it contains reflect the latest state of the associated spatial surface.</span></span> <span data-ttu-id="332fc-159">Eseguire facoltativamente l'analisi e/o l' [elaborazione](spatial-mapping.md#mesh-processing) dei dati mesh accedendo al membro mesh dell'oggetto MeshFilter.</span><span class="sxs-lookup"><span data-stu-id="332fc-159">Optionally perform analysis and/or [processing](spatial-mapping.md#mesh-processing) of the mesh data by accessing the Mesh member of the MeshFilter object.</span></span> <span data-ttu-id="332fc-160">Eseguire il rendering della superficie spaziale con la mesh più recente e, facoltativamente, usarla per collisioni fisiche e raycasts.</span><span class="sxs-lookup"><span data-stu-id="332fc-160">Render the spatial surface with the latest mesh and (optionally) use it for physics collisions and raycasts.</span></span> <span data-ttu-id="332fc-161">È importante verificare che il contenuto di SurfaceData non sia null.</span><span class="sxs-lookup"><span data-stu-id="332fc-161">It's important to confirm that the contents of the SurfaceData are not null.</span></span>

### <a name="start-processing-on-updates"></a><span data-ttu-id="332fc-162">Avviare l'elaborazione degli aggiornamenti</span><span class="sxs-lookup"><span data-stu-id="332fc-162">Start processing on updates</span></span>

<span data-ttu-id="332fc-163">SurfaceObserver. Update () deve essere chiamato su un ritardo, non su tutti i frame.</span><span class="sxs-lookup"><span data-stu-id="332fc-163">SurfaceObserver.Update() should be called on a delay, not every frame.</span></span>

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

## <a name="higher-level-mesh-analysis-spatialunderstanding"></a><span data-ttu-id="332fc-164">Analisi mesh di livello superiore: SpatialUnderstanding</span><span class="sxs-lookup"><span data-stu-id="332fc-164">Higher-level mesh analysis: SpatialUnderstanding</span></span>

<span data-ttu-id="332fc-165"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> è una raccolta di utili codici di utilità per lo sviluppo olografico basato sulle API olografiche di Unity.</span><span class="sxs-lookup"><span data-stu-id="332fc-165">The <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> is a collection of helpful utility code for holographic development built upon the holographic Unity APIs.</span></span>

### <a name="spatial-understanding"></a><span data-ttu-id="332fc-166">Conoscenza spaziale</span><span class="sxs-lookup"><span data-stu-id="332fc-166">Spatial Understanding</span></span>

<span data-ttu-id="332fc-167">Quando si posizionano gli ologrammi nel mondo fisico è spesso consigliabile andare oltre i piani di rete e superficie del mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="332fc-167">When placing holograms in the physical world it is often desirable to go beyond spatial mapping’s mesh and surface planes.</span></span> <span data-ttu-id="332fc-168">Quando il posizionamento viene eseguito in maniera procedurale, è auspicabile un livello superiore di comprensione ambientale.</span><span class="sxs-lookup"><span data-stu-id="332fc-168">When placement is done procedurally, a higher level of environmental understanding is desirable.</span></span> <span data-ttu-id="332fc-169">Questa operazione richiede in genere le decisioni relative a pavimenti, massimali e muri.</span><span class="sxs-lookup"><span data-stu-id="332fc-169">This usually requires making decisions about what is floor, ceiling, and walls.</span></span> <span data-ttu-id="332fc-170">Inoltre, la possibilità di eseguire l'ottimizzazione rispetto a un set di vincoli di posizionamento per determinare le posizioni fisiche più desiderate per gli oggetti olografici.</span><span class="sxs-lookup"><span data-stu-id="332fc-170">In addition, the ability to optimize against a set of placement constraints to determining the most desirable physical locations for holographic objects.</span></span>

<span data-ttu-id="332fc-171">Durante lo sviluppo di Conker e frammenti giovani, Asobo Studios ha affrontato questo problema, sviluppando un risolutore di spazio a questo scopo.</span><span class="sxs-lookup"><span data-stu-id="332fc-171">During the development of Young Conker and Fragments, Asobo Studios faced this problem head on, developing a room solver for this purpose.</span></span> <span data-ttu-id="332fc-172">Ognuno di questi giochi ha esigenze specifiche del gioco, ma ha condiviso la tecnologia principale per la comprensione spaziale.</span><span class="sxs-lookup"><span data-stu-id="332fc-172">Each of these games had game specific needs, but they shared core spatial understanding technology.</span></span> <span data-ttu-id="332fc-173">La libreria HoloToolkit. SpatialUnderstanding incapsula questa tecnologia, consentendo di trovare rapidamente gli spazi vuoti sulle pareti, posizionare gli oggetti sul soffitto, identificare posizionati per il carattere da collocare e una miriade di altre query di comprensione spaziale.</span><span class="sxs-lookup"><span data-stu-id="332fc-173">The HoloToolkit.SpatialUnderstanding library encapsulates this technology, allowing you to quickly find empty spaces on the walls, place objects on the ceiling, identify placed for character to sit, and a myriad of other spatial understanding queries.</span></span>

<span data-ttu-id="332fc-174">Tutto il codice sorgente è incluso, consentendo di personalizzarlo in base alle proprie esigenze e condividere i miglioramenti con la community.</span><span class="sxs-lookup"><span data-stu-id="332fc-174">All of the source code is included, allowing you to customize it to your needs and share your improvements with the community.</span></span> <span data-ttu-id="332fc-175">Il codice per il C++ Risolutore è stato sottoposto a incapsulamento in una DLL di UWP ed esposto a Unity con una riduzione della prefabbricata contenuta nel MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="332fc-175">The code for the C++ solver has been wrapped into a UWP dll and exposed to Unity with a drop in prefab contained within the MixedRealityToolkit.</span></span>

### <a name="understanding-modules"></a><span data-ttu-id="332fc-176">Informazioni sui moduli</span><span class="sxs-lookup"><span data-stu-id="332fc-176">Understanding Modules</span></span>

<span data-ttu-id="332fc-177">Sono disponibili tre interfacce primarie esposte dal modulo: topologia per query di superficie e spaziali semplici, forma per il rilevamento di oggetti e il Risolutore di posizionamento degli oggetti per il posizionamento basato sui vincoli dei set di oggetti.</span><span class="sxs-lookup"><span data-stu-id="332fc-177">There are three primary interfaces exposed by the module: topology for simple surface and spatial queries, shape for object detection, and the object placement solver for constraint based placement of object sets.</span></span> <span data-ttu-id="332fc-178">Ognuno di questi è descritto di seguito.</span><span class="sxs-lookup"><span data-stu-id="332fc-178">Each of these is described below.</span></span> <span data-ttu-id="332fc-179">Oltre alle tre interfacce del modulo principale, è possibile usare un'interfaccia di cast di tipo Ray per recuperare i tipi di superficie con tag ed è possibile copiare una mesh playspace stermetica personalizzata.</span><span class="sxs-lookup"><span data-stu-id="332fc-179">In addition to the three primary module interfaces, a ray casting interface can be used to retrieve tagged surface types and a custom watertight playspace mesh can be copied out.</span></span>

### <a name="ray-casting"></a><span data-ttu-id="332fc-180">Casting Ray</span><span class="sxs-lookup"><span data-stu-id="332fc-180">Ray Casting</span></span>

<span data-ttu-id="332fc-181">Dopo che la chat è stata sottoposta a scansione e finalizzata, le etichette vengono generate internamente per superfici quali il piano, il soffitto e i muri.</span><span class="sxs-lookup"><span data-stu-id="332fc-181">After the room has been scanned and finalized, labels are internally generated for surfaces like the floor, ceiling, and walls.</span></span> <span data-ttu-id="332fc-182">La funzione "PlayspaceRaycast" accetta un raggio e restituisce se il raggio è in conflitto con una superficie nota e, in tal caso, le informazioni su tale superficie sotto forma di "RaycastResult".</span><span class="sxs-lookup"><span data-stu-id="332fc-182">The “PlayspaceRaycast” function takes a ray and returns if the ray collides with a known surface and if so, information about that surface in the form of a “RaycastResult”.</span></span>

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

<span data-ttu-id="332fc-183">Internamente, il Raycast viene calcolato rispetto alla rappresentazione voxel del cubo di 8cm calcolata del playspace.</span><span class="sxs-lookup"><span data-stu-id="332fc-183">Internally, the raycast is computed against the computed 8cm cubed voxel representation of the playspace.</span></span> <span data-ttu-id="332fc-184">Ogni voxel contiene un set di elementi Surface con dati della topologia elaborati (noto anche come surfels).</span><span class="sxs-lookup"><span data-stu-id="332fc-184">Each voxel contains a set of surface elements with processed topology data (aka surfels).</span></span> <span data-ttu-id="332fc-185">Il surfels contenuto all'interno della cella voxel intersecata viene confrontato e la migliore corrispondenza utilizzata per cercare le informazioni sulla topologia.</span><span class="sxs-lookup"><span data-stu-id="332fc-185">The surfels contained within the intersected voxel cell are compared and the best match used to look up the topology information.</span></span> <span data-ttu-id="332fc-186">Questi dati della topologia contengono l'etichettatura restituita nel formato dell'enumerazione "SurfaceTypes", nonché la superficie di attacco della superficie intersecata.</span><span class="sxs-lookup"><span data-stu-id="332fc-186">This topology data contains the labeling returned in the form of the “SurfaceTypes” enum, as well as the surface area of the intersected surface.</span></span>

<span data-ttu-id="332fc-187">Nell'esempio Unity il cursore esegue il cast di un raggio per ogni fotogramma.</span><span class="sxs-lookup"><span data-stu-id="332fc-187">In the Unity sample, the cursor casts a ray each frame.</span></span> <span data-ttu-id="332fc-188">In primo luogo, rispetto ai Collider di Unity.</span><span class="sxs-lookup"><span data-stu-id="332fc-188">First, against Unity’s colliders.</span></span> <span data-ttu-id="332fc-189">In secondo luogo, sulla rappresentazione mondiale del modulo di informazioni.</span><span class="sxs-lookup"><span data-stu-id="332fc-189">Second, against the understanding module’s world representation.</span></span> <span data-ttu-id="332fc-190">Infine, di nuovo gli elementi dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="332fc-190">And finally, again UI elements.</span></span> <span data-ttu-id="332fc-191">In questa applicazione, l'interfaccia utente ottiene la priorità, successivamente il risultato della comprensione e infine i Collider di Unity.</span><span class="sxs-lookup"><span data-stu-id="332fc-191">In this application, UI gets priority, next the understanding result, and lastly, Unity’s colliders.</span></span> <span data-ttu-id="332fc-192">SurfaceType viene segnalato come testo accanto al cursore.</span><span class="sxs-lookup"><span data-stu-id="332fc-192">The SurfaceType is reported as text next to the cursor.</span></span>

<span data-ttu-id="332fc-193">![Il tipo di superficie è contrassegnato accanto al cursore](images/su-raycastresults-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="332fc-193">![Surface type is labeled next to the cursor](images/su-raycastresults-300px.jpg)</span></span><br>
<span data-ttu-id="332fc-194">*Il tipo di superficie è contrassegnato accanto al cursore*</span><span class="sxs-lookup"><span data-stu-id="332fc-194">*Surface type is labeled next to the cursor*</span></span>

### <a name="topology-queries"></a><span data-ttu-id="332fc-195">Query sulla topologia</span><span class="sxs-lookup"><span data-stu-id="332fc-195">Topology Queries</span></span>

<span data-ttu-id="332fc-196">All'interno della DLL, Gestione topologia gestisce l'assegnazione di etichette all'ambiente.</span><span class="sxs-lookup"><span data-stu-id="332fc-196">Within the DLL, the topology manager handles labeling of the environment.</span></span> <span data-ttu-id="332fc-197">Come indicato in precedenza, gran parte dei dati viene archiviata in surfels, contenuta in un volume voxel.</span><span class="sxs-lookup"><span data-stu-id="332fc-197">As mentioned above, much of the data is stored within surfels, contained within a voxel volume.</span></span> <span data-ttu-id="332fc-198">Inoltre, la struttura "PlaySpaceInfos" viene usata per archiviare le informazioni relative a playspace, incluso l'allineamento internazionale (altre informazioni su questo argomento), il piano e l'altezza del soffitto.</span><span class="sxs-lookup"><span data-stu-id="332fc-198">In addition, the “PlaySpaceInfos” structure is used to store information about the playspace, including the world alignment (more details on this below), floor, and ceiling height.</span></span> <span data-ttu-id="332fc-199">Vengono usate le regole euristiche per determinare il piano, il soffitto e i muri.</span><span class="sxs-lookup"><span data-stu-id="332fc-199">Heuristics are used for determining floor, ceiling, and walls.</span></span> <span data-ttu-id="332fc-200">Ad esempio, la superficie orizzontale più grande e più bassa con una superficie di attacco maggiore di 1 m2 viene considerata il piano.</span><span class="sxs-lookup"><span data-stu-id="332fc-200">For example, the largest and lowest horizontal surface with greater than 1 m2 surface area is considered the floor.</span></span> <span data-ttu-id="332fc-201">Si noti che in questo processo viene usato anche il percorso della fotocamera durante il processo di analisi.</span><span class="sxs-lookup"><span data-stu-id="332fc-201">Note that the camera path during the scanning process is also used in this process.</span></span>

<span data-ttu-id="332fc-202">Un subset delle query esposte dal gestore della topologia viene esposto tramite la dll.</span><span class="sxs-lookup"><span data-stu-id="332fc-202">A subset of the queries exposed by the Topology manager are exposed out through the dll.</span></span> <span data-ttu-id="332fc-203">Di seguito sono riportate le query topologia esposte.</span><span class="sxs-lookup"><span data-stu-id="332fc-203">The exposed topology queries are as follows.</span></span>

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

<span data-ttu-id="332fc-204">Ogni query ha un set di parametri, specifico del tipo di query.</span><span class="sxs-lookup"><span data-stu-id="332fc-204">Each of the queries has a set of parameters, specific to the query type.</span></span> <span data-ttu-id="332fc-205">Nell'esempio seguente l'utente specifica l'altezza minima & larghezza del volume desiderato, l'altezza minima di posizionamento sopra il piano e la quantità minima di spazio di autorizzazione davanti al volume.</span><span class="sxs-lookup"><span data-stu-id="332fc-205">In the following example, the user specifies the minimum height & width of the desired volume, minimum placement height above the floor, and the minimum amount of clearance in front of the volume.</span></span> <span data-ttu-id="332fc-206">Tutte le misurazioni sono in metri.</span><span class="sxs-lookup"><span data-stu-id="332fc-206">All measurements are in meters.</span></span>

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

<span data-ttu-id="332fc-207">Ognuna di queste query accetta una matrice pre-allocata di strutture "TopologyResult".</span><span class="sxs-lookup"><span data-stu-id="332fc-207">Each of these queries takes a pre-allocated array of “TopologyResult” structures.</span></span> <span data-ttu-id="332fc-208">Il parametro "locationCount" specifica la lunghezza della matrice passata.</span><span class="sxs-lookup"><span data-stu-id="332fc-208">The “locationCount” parameter specifies the length of the passed in array.</span></span> <span data-ttu-id="332fc-209">Il valore restituito indica il numero di posizioni restituite.</span><span class="sxs-lookup"><span data-stu-id="332fc-209">The return value reports the number of returned locations.</span></span> <span data-ttu-id="332fc-210">Questo numero non è mai superiore al parametro "locationCount" passato.</span><span class="sxs-lookup"><span data-stu-id="332fc-210">This number is never greater than the passed in “locationCount” parameter.</span></span>

<span data-ttu-id="332fc-211">"TopologyResult" contiene la posizione centrale del volume restituito, la direzione (ovvero normale) e le dimensioni dello spazio trovato.</span><span class="sxs-lookup"><span data-stu-id="332fc-211">The “TopologyResult” contains the center position of the returned volume, the facing direction (i.e. normal), and the dimensions of the found space.</span></span>

```cpp
struct TopologyResult 
{ 
    DirectX::XMFLOAT3 position; 
    DirectX::XMFLOAT3 normal; 
    float width; 
    float length;
};
```

<span data-ttu-id="332fc-212">Si noti che nell'esempio Unity ogni query è collegata a un pulsante nel pannello dell'interfaccia utente virtuale.</span><span class="sxs-lookup"><span data-stu-id="332fc-212">Note that in the Unity sample, each of these queries is linked up to a button in the virtual UI panel.</span></span> <span data-ttu-id="332fc-213">L'esempio codifica in modo rigido i parametri per ognuna di queste query in valori ragionevoli.</span><span class="sxs-lookup"><span data-stu-id="332fc-213">The sample hard codes the parameters for each of these queries to reasonable values.</span></span> <span data-ttu-id="332fc-214">Per altri esempi, vedere SpaceVisualizer.cs nel codice di esempio.</span><span class="sxs-lookup"><span data-stu-id="332fc-214">See SpaceVisualizer.cs in the sample code for more examples.</span></span>

### <a name="shape-queries"></a><span data-ttu-id="332fc-215">Query di forma</span><span class="sxs-lookup"><span data-stu-id="332fc-215">Shape Queries</span></span>

<span data-ttu-id="332fc-216">All'interno della dll, l'analizzatore di forme ("ShapeAnalyzer_W") utilizza l'analizzatore della topologia per trovare la corrispondenza con le forme personalizzate definite dall'utente.</span><span class="sxs-lookup"><span data-stu-id="332fc-216">Inside of the dll, the shape analyzer (“ShapeAnalyzer_W”) uses the topology analyzer to match against custom shapes defined by the user.</span></span> <span data-ttu-id="332fc-217">L'esempio Unity definisce un set di forme ed espone i risultati tramite il menu query in-app, all'interno della scheda Shape. L'intenzione è che l'utente possa definire le proprie query di forma oggetto e utilizzarle, in base alle esigenze dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="332fc-217">The Unity sample defines a set of shapes and exposes the results out through the in-app query menu, within the shape tab. The intention is that the user can define their own object shape queries and make use of those, as needed by their application.</span></span>

<span data-ttu-id="332fc-218">Si noti che l'analisi delle forme funziona solo su superfici orizzontali.</span><span class="sxs-lookup"><span data-stu-id="332fc-218">Note that the shape analysis works on horizontal surfaces only.</span></span> <span data-ttu-id="332fc-219">Un divano, ad esempio, viene definito dalla superficie della postazione piatta e dalla parte superiore piatta del divano.</span><span class="sxs-lookup"><span data-stu-id="332fc-219">A couch, for example, is defined by the flat seat surface and the flat top of the couch back.</span></span> <span data-ttu-id="332fc-220">La query Shape cerca due superfici di dimensioni, altezze e intervalli di aspetto specifici, con le due superfici allineate e connesse.</span><span class="sxs-lookup"><span data-stu-id="332fc-220">The shape query looks for two surfaces of a specific size, height, and aspect range, with the two surfaces aligned and connected.</span></span> <span data-ttu-id="332fc-221">Con la terminologia relativa alle API, il divano e la parte superiore sono componenti di forma e i requisiti di allineamento sono vincoli dei componenti della forma.</span><span class="sxs-lookup"><span data-stu-id="332fc-221">Using the APIs terminology, the couch seat and back top are shape components and the alignment requirements are shape component constraints.</span></span>

<span data-ttu-id="332fc-222">Di seguito è riportata una query di esempio definita nell'esempio Unity (ShapeDefinition.cs) per gli oggetti "SitTable".</span><span class="sxs-lookup"><span data-stu-id="332fc-222">An example query defined in the Unity sample (ShapeDefinition.cs), for “sittable” objects is as follows.</span></span>

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

<span data-ttu-id="332fc-223">Ogni query di forma è definita da un set di componenti di forma, ognuno con un set di vincoli di componente e un set di vincoli di forma che elencano le dipendenze tra i componenti.</span><span class="sxs-lookup"><span data-stu-id="332fc-223">Each shape query is defined by a set of shape components, each with a set of component constraints and a set of shape constraints which listing dependencies between the components.</span></span> <span data-ttu-id="332fc-224">Questo esempio include tre vincoli in una definizione di componente singolo e nessun vincolo di forma tra i componenti (in quanto è presente un solo componente).</span><span class="sxs-lookup"><span data-stu-id="332fc-224">This example includes three constraints in a single component definition and no shape constraints between components (as there is only one component).</span></span>

<span data-ttu-id="332fc-225">Al contrario, la forma Couch presenta due componenti di forma e quattro vincoli Shape.</span><span class="sxs-lookup"><span data-stu-id="332fc-225">In contrast, the couch shape has two shape components and four shape constraints.</span></span> <span data-ttu-id="332fc-226">Si noti che i componenti sono identificati dal relativo indice nell'elenco dei componenti dell'utente (0 e 1 in questo esempio).</span><span class="sxs-lookup"><span data-stu-id="332fc-226">Note that components are identified by their index in the user’s component list (0 and 1 in this example).</span></span>

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

<span data-ttu-id="332fc-227">Le funzioni wrapper sono disponibili nel modulo Unity per semplificare la creazione di definizioni di forme personalizzate.</span><span class="sxs-lookup"><span data-stu-id="332fc-227">Wrapper functions are provided in the Unity module for easy creation of custom shape definitions.</span></span> <span data-ttu-id="332fc-228">L'elenco completo dei vincoli relativi a componenti e forme si trova in "SpatialUnderstandingDll.cs" all'interno delle strutture "ShapeComponentConstraint" e "ShapeConstraint".</span><span class="sxs-lookup"><span data-stu-id="332fc-228">The full list of component and shape constraints can be found in “SpatialUnderstandingDll.cs” within the “ShapeComponentConstraint” and the “ShapeConstraint” structures.</span></span>

<span data-ttu-id="332fc-229">![Forma rettangolo individuata in questa superficie](images/su-shapequery-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="332fc-229">![Rectangle shape is found on this surface](images/su-shapequery-300px.jpg)</span></span><br>
<span data-ttu-id="332fc-230">*Forma rettangolo individuata in questa superficie*</span><span class="sxs-lookup"><span data-stu-id="332fc-230">*Rectangle shape is found on this surface*</span></span>

### <a name="object-placement-solver"></a><span data-ttu-id="332fc-231">Risolutore posizionamento oggetti</span><span class="sxs-lookup"><span data-stu-id="332fc-231">Object Placement Solver</span></span>

<span data-ttu-id="332fc-232">Il Risolutore posizionamento oggetti può essere usato per identificare le posizioni ideali nella stanza fisica per inserire gli oggetti.</span><span class="sxs-lookup"><span data-stu-id="332fc-232">The object placement solver can be used to identify ideal locations in the physical room to place your objects.</span></span> <span data-ttu-id="332fc-233">Il Risolutore troverà il percorso più adatto in base alle regole e ai vincoli dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="332fc-233">The solver will find the best fit location given the object rules and constraints.</span></span> <span data-ttu-id="332fc-234">Inoltre, le query di oggetto vengono mantenute fino a quando l'oggetto non viene rimosso con chiamate a "Solver_RemoveObject" o "Solver_RemoveAllObjects", consentendo il posizionamento di più oggetti vincolato.</span><span class="sxs-lookup"><span data-stu-id="332fc-234">In addition, object queries persist until the object is removed with “Solver_RemoveObject” or “Solver_RemoveAllObjects” calls, allowing constrained multi-object placement.</span></span> <span data-ttu-id="332fc-235">Le query di posizionamento degli oggetti sono costituite da tre parti: tipo di posizionamento con parametri, un elenco di regole e un elenco di vincoli.</span><span class="sxs-lookup"><span data-stu-id="332fc-235">Objects placement queries consist of three parts: placement type with parameters, a list of rules, and a list of constraints.</span></span> <span data-ttu-id="332fc-236">Per eseguire una query, usare l'API seguente.</span><span class="sxs-lookup"><span data-stu-id="332fc-236">To run a query, use the following API.</span></span>

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

<span data-ttu-id="332fc-237">Questa funzione accetta un nome di oggetto, una definizione di selezione host e un elenco di regole e vincoli.</span><span class="sxs-lookup"><span data-stu-id="332fc-237">This function takes an object name, placement definition, and a list of rules and constraints.</span></span> <span data-ttu-id="332fc-238">I C# wrapper forniscono funzioni di supporto per la costruzione per semplificare la costruzione di regole e vincoli.</span><span class="sxs-lookup"><span data-stu-id="332fc-238">The C# wrappers provides construction helper functions to make rule and constraint construction easy.</span></span> <span data-ttu-id="332fc-239">La definizione di selezione host contiene il tipo di query, ovvero uno dei seguenti.</span><span class="sxs-lookup"><span data-stu-id="332fc-239">The placement definition contains the query type – that is, one of the following.</span></span>

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

<span data-ttu-id="332fc-240">Ognuno dei tipi di posizionamento dispone di un set di parametri univoco per il tipo.</span><span class="sxs-lookup"><span data-stu-id="332fc-240">Each of the placement types has a set of parameters unique to the type.</span></span> <span data-ttu-id="332fc-241">La struttura "ObjectPlacementDefinition" contiene un set di funzioni di supporto statiche per la creazione di queste definizioni.</span><span class="sxs-lookup"><span data-stu-id="332fc-241">The “ObjectPlacementDefinition” structure contains a set of static helper functions for creating these definitions.</span></span> <span data-ttu-id="332fc-242">Ad esempio, per trovare una posizione in cui posizionare un oggetto, è possibile usare la funzione seguente.</span><span class="sxs-lookup"><span data-stu-id="332fc-242">For example, to find a place to put an object on the floor, you can use the following function.</span></span> <span data-ttu-id="332fc-243">public static ObjectPlacementDefinition Create_OnFloor (Vector3 halfDims) oltre al tipo di posizionamento, è possibile fornire un set di regole e vincoli.</span><span class="sxs-lookup"><span data-stu-id="332fc-243">public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) In addition to the placement type, you can provide a set of rules and constraints.</span></span> <span data-ttu-id="332fc-244">Impossibile violare le regole.</span><span class="sxs-lookup"><span data-stu-id="332fc-244">Rules cannot be violated.</span></span> <span data-ttu-id="332fc-245">Le posizioni di posizionamento possibili che soddisfano il tipo e le regole vengono quindi ottimizzate rispetto al set di vincoli per selezionare la posizione ottimale per la selezione host.</span><span class="sxs-lookup"><span data-stu-id="332fc-245">Possible placement locations that satisfy the type and rules are then optimized against the set of constraints in order to select the optimal placement location.</span></span> <span data-ttu-id="332fc-246">Ognuna delle regole e dei vincoli può essere creata dalle funzioni di creazione statiche fornite.</span><span class="sxs-lookup"><span data-stu-id="332fc-246">Each of the rules and constraints can be created by the provided static creation functions.</span></span> <span data-ttu-id="332fc-247">Di seguito è riportata una funzione di costruzione di regole e vincoli di esempio.</span><span class="sxs-lookup"><span data-stu-id="332fc-247">An example rule and constraint construction function is provided below.</span></span>

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

<span data-ttu-id="332fc-248">La query di posizionamento degli oggetti seguente sta cercando una posizione per inserire un cubo a metà metro sul bordo di una superficie, lontano dagli altri oggetti posizionati in precedenza e vicino al centro della stanza.</span><span class="sxs-lookup"><span data-stu-id="332fc-248">The below object placement query is looking for a place to put a half meter cube on the edge of a surface, away from other previously place objects and near the center of the room.</span></span>

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

<span data-ttu-id="332fc-249">In caso di esito positivo, viene restituita una struttura "ObjectPlacementResult" che contiene la posizione, le dimensioni e l'orientamento del posizionamento.</span><span class="sxs-lookup"><span data-stu-id="332fc-249">If successful, a “ObjectPlacementResult” structure containing the placement position, dimensions and orientation is returned.</span></span> <span data-ttu-id="332fc-250">Inoltre, la selezione host viene aggiunta all'elenco interno della dll degli oggetti inseriti.</span><span class="sxs-lookup"><span data-stu-id="332fc-250">In addition, the placement is added to the dll’s internal list of placed objects.</span></span> <span data-ttu-id="332fc-251">Questo oggetto verrà preso in considerazione dalle query di posizionamento successive.</span><span class="sxs-lookup"><span data-stu-id="332fc-251">Subsequent placement queries will take this object into account.</span></span> <span data-ttu-id="332fc-252">Il file "LevelSolver.cs" nell'esempio Unity contiene altre query di esempio.</span><span class="sxs-lookup"><span data-stu-id="332fc-252">The “LevelSolver.cs” file in the Unity sample contains more example queries.</span></span>

<span data-ttu-id="332fc-253">![Risultati del posizionamento degli oggetti](images/su-objectplacement-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="332fc-253">![Results of object placement](images/su-objectplacement-1000px.jpg)</span></span><br>
<span data-ttu-id="332fc-254">*Figura 3: Le caselle blu come il risultato di tre posizioni nelle query sul pavimento con le regole di posizione della fotocamera*</span><span class="sxs-lookup"><span data-stu-id="332fc-254">*Figure 3: The blue boxes how the result from three place on floor queries with away from camera position rules*</span></span>

<span data-ttu-id="332fc-255">Quando si risolve la posizione di selezione host di più oggetti richiesti per uno scenario di livello o di applicazione, risolvere prima di tutto gli oggetti indispensabili e di grandi dimensioni per ottimizzare la probabilità che uno spazio venga trovato.</span><span class="sxs-lookup"><span data-stu-id="332fc-255">When solving for placement location of multiple objects required for a level or application scenario, first solve indispensable and large objects in order to maximizing the probability that a space can be found.</span></span> <span data-ttu-id="332fc-256">L'ordine di posizionamento è importante.</span><span class="sxs-lookup"><span data-stu-id="332fc-256">Placement order is important.</span></span> <span data-ttu-id="332fc-257">Se non è possibile trovare le posizioni degli oggetti, provare a eseguire meno configurazioni vincolate.</span><span class="sxs-lookup"><span data-stu-id="332fc-257">If object placements cannot be found, try less constrained configurations.</span></span> <span data-ttu-id="332fc-258">Avere un set di configurazioni di fallback è fondamentale per supportare le funzionalità in molte configurazioni di chat room.</span><span class="sxs-lookup"><span data-stu-id="332fc-258">Having a set of fallback configurations is critical to supporting functionality across many room configurations.</span></span>

### <a name="room-scanning-process"></a><span data-ttu-id="332fc-259">Processo di analisi chat room</span><span class="sxs-lookup"><span data-stu-id="332fc-259">Room Scanning Process</span></span>

<span data-ttu-id="332fc-260">Sebbene la soluzione di mapping spaziale fornita da HoloLens sia progettata per essere sufficientemente generica per soddisfare le esigenze dell'intera gamma di spazi di problemi, il modulo di comprensione spaziale è stato creato per supportare le esigenze di due giochi specifici.</span><span class="sxs-lookup"><span data-stu-id="332fc-260">While the spatial mapping solution provided by the HoloLens is designed to be generic enough to meet the needs of the entire gamut of problem spaces, the spatial understanding module was built to support the needs of two specific games.</span></span> <span data-ttu-id="332fc-261">La soluzione è strutturata in base a un processo e a un set di presupposti specifici, riepilogati di seguito.</span><span class="sxs-lookup"><span data-stu-id="332fc-261">Its solution is structured around a specific process and set of assumptions, summarized below.</span></span>

```
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process – 
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace. 
    Query functions will not function until after the scan has been finalized.
```

<span data-ttu-id="332fc-262">"Disegno" di playspace basato sull'utente: durante la fase di analisi, l'utente si sposta ed esamina la velocità di riproduzione, disegnando in modo efficace le aree che devono essere incluse.</span><span class="sxs-lookup"><span data-stu-id="332fc-262">User driven playspace “painting” – During the scanning phase, the user moves and looks around the plays pace, effectively painting the areas which should be included.</span></span> <span data-ttu-id="332fc-263">La mesh generata è importante per fornire commenti e suggerimenti degli utenti durante questa fase.</span><span class="sxs-lookup"><span data-stu-id="332fc-263">The generated mesh is important to provide user feedback during this phase.</span></span> <span data-ttu-id="332fc-264">Installazione domestica o di Office: le funzioni di query sono progettate per le superfici piane e i muri con angoli corretti.</span><span class="sxs-lookup"><span data-stu-id="332fc-264">Indoors home or office setup – The query functions are designed around flat surfaces and walls at right angles.</span></span> <span data-ttu-id="332fc-265">Si tratta di una limitazione flessibile.</span><span class="sxs-lookup"><span data-stu-id="332fc-265">This is a soft limitation.</span></span> <span data-ttu-id="332fc-266">Tuttavia, durante la fase di analisi, viene completata un'analisi dell'asse primaria per ottimizzare lo schema a mosaico mesh lungo l'asse principale e secondario.</span><span class="sxs-lookup"><span data-stu-id="332fc-266">However, during the scanning phase, a primary axis analysis is completed to optimize the mesh tessellation along major and minor axis.</span></span> <span data-ttu-id="332fc-267">Il file SpatialUnderstanding.cs incluso gestisce il processo della fase di analisi.</span><span class="sxs-lookup"><span data-stu-id="332fc-267">The included SpatialUnderstanding.cs file manages the scanning phase process.</span></span> <span data-ttu-id="332fc-268">Chiama le funzioni seguenti.</span><span class="sxs-lookup"><span data-stu-id="332fc-268">It calls the following functions.</span></span>

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

<span data-ttu-id="332fc-269">Il flusso di analisi, determinato dal comportamento "SpatialUnderstanding", chiama InitScan e quindi UpdateScan ogni frame.</span><span class="sxs-lookup"><span data-stu-id="332fc-269">The scanning flow, driven by the “SpatialUnderstanding” behavior calls InitScan, then UpdateScan each frame.</span></span> <span data-ttu-id="332fc-270">Quando la query Statistics segnala una ragionevole copertura, l'utente è autorizzato a AirTap per chiamare RequestFinish per indicare la fine della fase di analisi.</span><span class="sxs-lookup"><span data-stu-id="332fc-270">When the statistics query reports reasonable coverage, the user is allowed to airtap to call RequestFinish to indicate the end of the scanning phase.</span></span> <span data-ttu-id="332fc-271">UpdateScan continua a essere chiamato fino a quando non viene restituito il valore indica che l'elaborazione della dll è stata completata.</span><span class="sxs-lookup"><span data-stu-id="332fc-271">UpdateScan continues to be called until it’s return value indicates that the dll has completed processing.</span></span>

### <a name="understanding-mesh"></a><span data-ttu-id="332fc-272">Informazioni su mesh</span><span class="sxs-lookup"><span data-stu-id="332fc-272">Understanding Mesh</span></span>

<span data-ttu-id="332fc-273">La dll informazioni archivia internamente il playspace come griglia di cubi voxel di dimensioni 8 cm.</span><span class="sxs-lookup"><span data-stu-id="332fc-273">The understanding dll internally stores the playspace as a grid of 8cm sized voxel cubes.</span></span> <span data-ttu-id="332fc-274">Durante la fase iniziale di analisi, viene completata un'analisi del componente principale per determinare gli assi della stanza.</span><span class="sxs-lookup"><span data-stu-id="332fc-274">During the initial part of scanning, a primary component analysis is completed to determine the axes of the room.</span></span> <span data-ttu-id="332fc-275">Internamente, archivia lo spazio voxel allineato a questi assi.</span><span class="sxs-lookup"><span data-stu-id="332fc-275">Internally, it stores its voxel space aligned to these axes.</span></span> <span data-ttu-id="332fc-276">Una mesh viene generata approssimativamente ogni secondo estraendo oggetto isosurface dal volume voxel.</span><span class="sxs-lookup"><span data-stu-id="332fc-276">A mesh is generated approximately every second by extracting the isosurface from the voxel volume.</span></span> 

<span data-ttu-id="332fc-277">![Mesh generata prodotta dal volume voxel](images/su-custommesh.jpg)</span><span class="sxs-lookup"><span data-stu-id="332fc-277">![Generated mesh produced from the voxel volume](images/su-custommesh.jpg)</span></span><br>
<span data-ttu-id="332fc-278">*Mesh generata prodotta dal volume voxel*</span><span class="sxs-lookup"><span data-stu-id="332fc-278">*Generated mesh produced from the voxel volume*</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="332fc-279">Risoluzione dei problemi</span><span class="sxs-lookup"><span data-stu-id="332fc-279">Troubleshooting</span></span>
* <span data-ttu-id="332fc-280">Assicurarsi di aver impostato la funzionalità [SpatialPerception](#setting-the-spatialperception-capability)</span><span class="sxs-lookup"><span data-stu-id="332fc-280">Ensure you have set the [SpatialPerception](#setting-the-spatialperception-capability) capability</span></span>
* <span data-ttu-id="332fc-281">Quando il rilevamento viene perso, l'evento OnSurfaceChanged successivo rimuoverà tutte le mesh.</span><span class="sxs-lookup"><span data-stu-id="332fc-281">When tracking is lost, the next OnSurfaceChanged event will remove all meshes.</span></span>

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a><span data-ttu-id="332fc-282">Mapping spaziale nel Toolkit per realtà mista</span><span class="sxs-lookup"><span data-stu-id="332fc-282">Spatial Mapping in Mixed Reality Toolkit</span></span>
<span data-ttu-id="332fc-283">Per altre informazioni sull'uso del mapping spaziale con Mixed Reality toolkit V2, vedere la <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">sezione relativa alla conoscenza spaziale</a> della documentazione di MRTK.</span><span class="sxs-lookup"><span data-stu-id="332fc-283">For more information on using Spatial Mapping with Mixed Reality Toolkit v2, see the <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">Spatial Awareness section</a> of the MRTK docs.</span></span>

## <a name="see-also"></a><span data-ttu-id="332fc-284">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="332fc-284">See also</span></span>
* [<span data-ttu-id="332fc-285">Spaziale MR 230: Mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="332fc-285">MR Spatial 230: Spatial mapping</span></span>](holograms-230.md)
* [<span data-ttu-id="332fc-286">Sistemi di coordinate</span><span class="sxs-lookup"><span data-stu-id="332fc-286">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="332fc-287">Sistemi di coordinate in Unity</span><span class="sxs-lookup"><span data-stu-id="332fc-287">Coordinate systems in Unity</span></span>](coordinate-systems-in-unity.md)
* <span data-ttu-id="332fc-288"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span><span class="sxs-lookup"><span data-stu-id="332fc-288"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span></span>
* <span data-ttu-id="332fc-289"><a href="http://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine. MeshFilter</a></span><span class="sxs-lookup"><span data-stu-id="332fc-289"><a href="http://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a></span></span>
* <span data-ttu-id="332fc-290"><a href="http://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine. MeshCollider</a></span><span class="sxs-lookup"><span data-stu-id="332fc-290"><a href="http://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a></span></span>
* <span data-ttu-id="332fc-291"><a href="http://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine. Bounds</a></span><span class="sxs-lookup"><span data-stu-id="332fc-291"><a href="http://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a></span></span>

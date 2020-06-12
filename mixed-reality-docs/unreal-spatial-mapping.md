---
title: Mapping spaziale in Unreal
description: Guida all'uso del mapping spaziale in Unreal
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, sviluppo, funzionalità, documentazione, guide, ologrammi, mapping spaziale
ms.openlocfilehash: 2bbfc3972acdb9dc7d5ebd23c85ab0ef5532cfb9
ms.sourcegitcommit: ee7f04148d3608b0284c59e33b394a67f0934255
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2020
ms.locfileid: "84428783"
---
# <a name="spatial-mapping-in-unreal"></a><span data-ttu-id="55c62-104">Mapping spaziale in Unreal</span><span class="sxs-lookup"><span data-stu-id="55c62-104">Spatial Mapping in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="55c62-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="55c62-105">Overview</span></span>
<span data-ttu-id="55c62-106">Il mapping spaziale consente di posizionare oggetti sulle superfici reali visualizzando l'ambiente intorno a HoloLens, rendendo gli ologrammi più realistici per l'utente.</span><span class="sxs-lookup"><span data-stu-id="55c62-106">Spatial mapping makes it possible to place objects on surfaces in the physical world by showing the world around the HoloLens, which makes holograms seem more real to the user.</span></span> <span data-ttu-id="55c62-107">Il mapping spaziale consente anche di ancorare gli oggetti nel mondo dell'utente sfruttando i segnali di profondità del mondo reale. In questo modo l'utente avrà l'impressione che questi ologrammi si trovino effettivamente nello spazio che lo circonda; gli ologrammi che fluttuano nello spazio o che si muovono insieme all'utente non vengono percepiti come reali.</span><span class="sxs-lookup"><span data-stu-id="55c62-107">Spatial mapping also anchors objects in the user's world by taking advantage of real world depth cues. This helps convince the user that these holograms are actually in their space; holograms floating in space or moving with the user will not feel as real.</span></span> <span data-ttu-id="55c62-108">È consigliabile inserire elementi di comfort, quando possibile.</span><span class="sxs-lookup"><span data-stu-id="55c62-108">You want to place items for comfort whenever possible.</span></span>

<span data-ttu-id="55c62-109">Per altre informazioni su qualità del mapping spaziale, posizionamento, occlusione, rendering e così via, consulta il documento [Mapping spaziale](spatial-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="55c62-109">You can find more information on spatial mapping quality, placement, occlusion, rendering, and more, in the [Spatial mapping](spatial-mapping.md) document.</span></span>

## <a name="enabling-spatial-mapping"></a><span data-ttu-id="55c62-110">Abilitazione del mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="55c62-110">Enabling Spatial Mapping</span></span>

<span data-ttu-id="55c62-111">Per abilitare il mapping spaziale in HoloLens:</span><span class="sxs-lookup"><span data-stu-id="55c62-111">To enable spatial mapping on HoloLens:</span></span>
- <span data-ttu-id="55c62-112">Apri **Edit > Project Settings** (Modifica > Impostazioni progetto) e scorri fino alla sezione **Platforms** (Piattaforme).</span><span class="sxs-lookup"><span data-stu-id="55c62-112">Open **Edit > Project Settings** and scroll down to the **Platforms** section.</span></span>    
    + <span data-ttu-id="55c62-113">Seleziona **HoloLens** e **Spatial Perception** (Percezione spaziale).</span><span class="sxs-lookup"><span data-stu-id="55c62-113">Select **HoloLens** and check **Spatial Perception**.</span></span>

<span data-ttu-id="55c62-114">Per acconsentire esplicitamente al mapping spaziale ed eseguire il debug di **MRMesh** in un gioco HoloLens:</span><span class="sxs-lookup"><span data-stu-id="55c62-114">To opt into spatial mapping and debug the **MRMesh** in a HoloLens game:</span></span>
1. <span data-ttu-id="55c62-115">Apri **ARSessionConfig** ed espandi la sezione **ARSettings > World Mapping** (ARSettings > Mapping mondo).</span><span class="sxs-lookup"><span data-stu-id="55c62-115">Open the **ARSessionConfig** and expand the **ARSettings > World Mapping** section.</span></span> 

2. <span data-ttu-id="55c62-116">Seleziona **Generate Mesh Data from Tracked Geometry** (Genera dati mesh da geometria rilevata), che indica al plug-in di HoloLens di avviare l'acquisizione asincrona dei dati di mapping spaziale e presentarli ad Unreal tramite **MRMesh**.</span><span class="sxs-lookup"><span data-stu-id="55c62-116">Check **Generate Mesh Data from Tracked Geometry**, which tells the HoloLens plugin to start asynchronously getting spatial mapping data and surface it to Unreal through the **MRMesh**.</span></span> 
3. <span data-ttu-id="55c62-117">Seleziona **Render Mesh Data in Wireframe** (Esegui il rendering dei dati mesh in wireframe) per visualizzare un contorno wireframe bianco di ogni triangolo in **MRMesh**.</span><span class="sxs-lookup"><span data-stu-id="55c62-117">Check **Render Mesh Data in Wireframe** to show a white wireframe outline of every triangle in the **MRMesh**.</span></span> 

![Archivio di ancoraggi nello spazio pronto](images/unreal-spatialmapping-arsettings.PNG)


## <a name="spatial-mapping-at-runtime"></a><span data-ttu-id="55c62-119">Mapping spaziale in fase di runtime</span><span class="sxs-lookup"><span data-stu-id="55c62-119">Spatial Mapping at runtime</span></span>
<span data-ttu-id="55c62-120">Puoi modificare i parametri seguenti per aggiornare il comportamento di runtime del mapping spaziale:</span><span class="sxs-lookup"><span data-stu-id="55c62-120">You can modify the following parameters to update the spatial mapping runtime behavior:</span></span>

- <span data-ttu-id="55c62-121">Apri **Edit > Project Settings** (Modifica > Impostazioni progetto), scorri verso il basso fino alla sezione **Platforms** (Piattaforme) e seleziona **HoloLens > Spatial Mapping** (HoloLens > Mapping spaziale):</span><span class="sxs-lookup"><span data-stu-id="55c62-121">Open **Edit > Project Settings**, scroll down to the **Platforms** section and select **HoloLens > Spatial Mapping**:</span></span> 

![Impostazioni del progetto di ancoraggi nello spazio](images/unreal-spatialmapping-projectsettings.PNG)

- <span data-ttu-id="55c62-123">Il parametro **Max Triangles Per Cubic Meter** (Numero massimo di triangoli per metro cubo) aggiorna la densità dei triangoli nella mesh di mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="55c62-123">**Max Triangles Per Cubic Meter** updates the density of the triangles in the spatial mapping mesh.</span></span>  
- <span data-ttu-id="55c62-124">Il parametro **Spatial Meshing Volume Size** (Dimensioni del volume della mesh spaziale) indica le dimensioni del cubo intorno al giocatore per il rendering e l'aggiornamento dei dati di mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="55c62-124">**Spatial Meshing Volume Size** is the size of the cube around the player to render and update spatial mapping data.</span></span>  
    + <span data-ttu-id="55c62-125">Se prevedi che l'ambiente di runtime dell'applicazione sia di grandi dimensioni, è possibile che questo valore debba essere elevato per poter corrispondere allo spazio reale.</span><span class="sxs-lookup"><span data-stu-id="55c62-125">If the expected application runtime environment is expected to be large, this value may need to be large to match the real-world space.</span></span>  <span data-ttu-id="55c62-126">Viceversa, questo valore può essere più piccolo se l'applicazione deve soltanto posizionare ologrammi sulle superfici immediatamente attorno all'utente.</span><span class="sxs-lookup"><span data-stu-id="55c62-126">On the other hand, this value can be smaller if the application only needs to place holograms on surfaces immediately around the user.</span></span> <span data-ttu-id="55c62-127">Il volume di mapping spaziale si sposterà quindi contestualmente all'utente.</span><span class="sxs-lookup"><span data-stu-id="55c62-127">As the user walks around the world, the spatial mapping volume will move with them.</span></span> 

## <a name="working-with-mrmesh"></a><span data-ttu-id="55c62-128">Uso di MRMesh</span><span class="sxs-lookup"><span data-stu-id="55c62-128">Working with MRMesh</span></span>
<span data-ttu-id="55c62-129">Per ottenere l'accesso a **MRMesh** in fase di runtime:</span><span class="sxs-lookup"><span data-stu-id="55c62-129">To get access to the **MRMesh** at runtime:</span></span>
1. <span data-ttu-id="55c62-130">Aggiungi un componente **ARTrackableNotify** a un attore del progetto.</span><span class="sxs-lookup"><span data-stu-id="55c62-130">Add an **ARTrackableNotify** Component to a Blueprint actor.</span></span> 

![Ancoraggi nello spazio AR Trackable Notify](images/unreal-spatialmapping-artrackablenotify.PNG)

2. <span data-ttu-id="55c62-132">Seleziona il componente **ARTrackableNotify** ed spandi la sezione **Events** (Events) nel pannello **Details** (Dettagli).</span><span class="sxs-lookup"><span data-stu-id="55c62-132">Select the **ARTrackableNotify** component and expand the **Events** section in the **Details** panel.</span></span> 
    - <span data-ttu-id="55c62-133">Fai clic sul pulsante **+** sugli eventi da monitorare.</span><span class="sxs-lookup"><span data-stu-id="55c62-133">Click the **+** button on the events you want to monitor.</span></span> 

![Eventi sugli ancoraggi nello spazio](images/unreal-spatialmapping-events.PNG)

<span data-ttu-id="55c62-135">In questo caso viene monitorato l'evento **On Add Tracked Geometry** (All'aggiunta della geometria rilevata), che cerca mesh reali valide corrispondenti ai dati del mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="55c62-135">In this case, the **On Add Tracked Geometry** event is being monitored, which looks for valid world meshes matching to spatial mapping data.</span></span> <span data-ttu-id="55c62-136">L'elenco completo degli eventi è disponibile nell'API del componente [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html).</span><span class="sxs-lookup"><span data-stu-id="55c62-136">You can find the full list of events in the [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) component API.</span></span> 

<span data-ttu-id="55c62-137">Il materiale della mesh può essere modificato nel grafico eventi del progetto o in C++.</span><span class="sxs-lookup"><span data-stu-id="55c62-137">You can change the mesh’s material in the Blueprint Event Graph or in C++.</span></span> <span data-ttu-id="55c62-138">Nello screenshot seguente è mostrato il percorso del progetto:</span><span class="sxs-lookup"><span data-stu-id="55c62-138">The screenshot below shows the Blueprint route:</span></span> 

![Esempi di ancoraggi nello spazio](images/unreal-spatialmapping-example.PNG)

<span data-ttu-id="55c62-140">In C++ è possibile sottoscrivere il delegato `OnTrackableAdded` per ottenere `ARTrackedGeometry` non appena è disponibile, come mostrato nel codice seguente.</span><span class="sxs-lookup"><span data-stu-id="55c62-140">In C++, you can subscribe to the `OnTrackableAdded` delegate to get the `ARTrackedGeometry` as soon as it is available, shown in the code below.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="55c62-141">Il file build.cs del progetto **DEVE** includere **AugmentedReality** nell'elenco **PublicDependencyModuleNames**.</span><span class="sxs-lookup"><span data-stu-id="55c62-141">The project’s build.cs file **MUST** have **AugmentedReality** in the **PublicDependencyModuleNames** list.</span></span>
> - <span data-ttu-id="55c62-142">Questo comprende **ARBlueprintLibrary.h** e **MRMeshComponent.h**, che consente di ispezionare il componente **MRMesh** di **UARTrackedGeometry**.</span><span class="sxs-lookup"><span data-stu-id="55c62-142">This includes **ARBlueprintLibrary.h** and **MRMeshComponent.h**, which lets you inspect the **MRMesh** component of the **UARTrackedGeometry**.</span></span> 

![Esempio di ancoraggi nello spazio in codice C++](images/unreal-spatialmapping-examplecode.PNG)

<span data-ttu-id="55c62-144">Il mapping spaziale non è l'unico tipo di dati che viene esposto tramite **ARTrackedGeometries**.</span><span class="sxs-lookup"><span data-stu-id="55c62-144">Spatial mapping is not the only type of data that gets surfaced through **ARTrackedGeometries**.</span></span> <span data-ttu-id="55c62-145">Puoi verificare che `EARObjectClassification` è `World`, che indica che si tratta di una geometria di mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="55c62-145">You can check that the `EARObjectClassification` is `World`, which means this is spatial mapping geometry.</span></span> 

<span data-ttu-id="55c62-146">Sono presenti delegati simili per gli eventi aggiornati e rimossi:</span><span class="sxs-lookup"><span data-stu-id="55c62-146">There are similar delegates for updated and removed events:</span></span> 
- `AddOnTrackableUpdatedDelegate_Handle` 
- <span data-ttu-id="55c62-147">`AddOnTrackableRemovedDelegate_Handle`.</span><span class="sxs-lookup"><span data-stu-id="55c62-147">`AddOnTrackableRemovedDelegate_Handle`.</span></span> 

<span data-ttu-id="55c62-148">L'elenco completo degli eventi è disponibile nell'API [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html).</span><span class="sxs-lookup"><span data-stu-id="55c62-148">You can find the full list of events in the [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html) API.</span></span>

## <a name="see-also"></a><span data-ttu-id="55c62-149">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="55c62-149">See also</span></span>
* [<span data-ttu-id="55c62-150">Mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="55c62-150">Spatial mapping</span></span>](spatial-mapping.md)

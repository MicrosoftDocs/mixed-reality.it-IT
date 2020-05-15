---
title: Mapping spaziale in Unreal
description: Guida all'uso del mapping spaziale in Unreal
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, sviluppo, funzionalità, documentazione, guide, ologrammi, mapping spaziale
ms.openlocfilehash: 32f8247010745b23bf73c5161c378bc1284169ef
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840080"
---
# <a name="spatial-mapping-in-unreal"></a><span data-ttu-id="9c96f-104">Mapping spaziale in Unreal</span><span class="sxs-lookup"><span data-stu-id="9c96f-104">Spatial Mapping in Unreal</span></span>

<span data-ttu-id="9c96f-105">Per abilitare il mapping spaziale in HoloLens, verifica che la funzionalità "Percezione spaziale" sia selezionata nell'editor di Unreal in Impostazioni progetto > Piattaforma > HoloLens > Funzionalità.</span><span class="sxs-lookup"><span data-stu-id="9c96f-105">To enable spatial mapping on HoloLens, ensure that the “Spatial Perception” capability is checked in the Unreal editor under Project Settings > Platform > HoloLens > Capabilities.</span></span>  

<span data-ttu-id="9c96f-106">Per acconsentire esplicitamente all'uso del mapping spaziale in un gioco HoloLens, abilita "Generate Mesh Data from Tracked Geometry" (Genera dati mesh dalla geometria rilevata) in ARSessionConfig.</span><span class="sxs-lookup"><span data-stu-id="9c96f-106">To opt into using spatial mapping in a HoloLens game, enable the “Generate Mesh Data from Tracked Geometry” in the ARSessionConfig.</span></span>  <span data-ttu-id="9c96f-107">Il plug-in HoloLens otterrà quindi i dati di mapping spaziale in modo asincrono e li sottoporrà a Unreal attraverso MRMesh.</span><span class="sxs-lookup"><span data-stu-id="9c96f-107">The HoloLens plugin will then asynchronously get spatial mapping data and surface it to Unreal through the MRMesh.</span></span> 

![Archivio di ancoraggi nello spazio pronto](images/unreal-spatialmapping-arsettings.PNG)

<span data-ttu-id="9c96f-109">Per aprire una visualizzazione di debug della mesh di mapping spaziale, abilita la casella di controllo "Render Mesh Data in Wireframe" (Rendering dei dati mesh in Wireframe) in ARSessionConfig, in modo da visualizzare una struttura di wireframe bianca di ogni triangolo in MRMesh.</span><span class="sxs-lookup"><span data-stu-id="9c96f-109">To see a debug visualization of the spatial mapping mesh, enable the “Render Mesh Data in Wireframe” checkbox in the ARSessionConfig to see a white wireframe outline of every triangle in the MRMesh.</span></span> 

<span data-ttu-id="9c96f-110">In Impostazioni progetto > Piattaforma > HoloLens > Mapping spaziale, è possibile modificare i parametri seguenti per aggiornare il comportamento di runtime del mapping spaziale:</span><span class="sxs-lookup"><span data-stu-id="9c96f-110">In Project Settings > Platform > HoloLens > Spatial Mapping, the following parameters can be modified to update spatial mapping’s runtime behavior:</span></span> 

![Impostazioni del progetto di ancoraggi nello spazio](images/unreal-spatialmapping-projectsettings.PNG)

<span data-ttu-id="9c96f-112">Il parametro Max Triangles Per Cubic Meter (Numero massimo di triangoli per metro cubo) aggiornerà la densità dei triangoli nella mesh di mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="9c96f-112">Max Triangles Per Cubic Meter will update the density of the triangles in the spatial mapping mesh.</span></span>  <span data-ttu-id="9c96f-113">Il parametro Spatial Meshing Volume Size (Dimensioni del volume della mesh spaziale) indica le dimensioni del cubo intorno al giocatore in cui poter eseguire il rendering e l'aggiornamento dei dati di mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="9c96f-113">Spatial Meshing Volume Size indicates the size of the cube around the player to render and update spatial mapping data.</span></span>  <span data-ttu-id="9c96f-114">Se prevedi che l'ambiente di runtime dell'applicazione sia di grandi dimensioni, è possibile che questo valore debba essere elevato per poter corrispondere allo spazio reale.</span><span class="sxs-lookup"><span data-stu-id="9c96f-114">If the expected application runtime environment is expected to be large, this field may need to be large to match the real-world space.</span></span>  <span data-ttu-id="9c96f-115">Se invece l'applicazione deve soltanto posizionare ologrammi sulle superfici immediatamente attorno all'utente, questo campo può essere più piccolo.</span><span class="sxs-lookup"><span data-stu-id="9c96f-115">Conversely, if the application only needs to place holograms on surfaces immediately around the user, this field can be smaller.</span></span>  <span data-ttu-id="9c96f-116">Il volume di mapping spaziale si sposterà quindi contestualmente all'utente.</span><span class="sxs-lookup"><span data-stu-id="9c96f-116">As the user walks around the world, the spatial mapping volume will move with them.</span></span> 

<span data-ttu-id="9c96f-117">Per ottenere l'accesso a MRMesh in fase di esecuzione, aggiungi un componente AR Trackable Notify a un attore del progetto:</span><span class="sxs-lookup"><span data-stu-id="9c96f-117">To get access to the MRMesh at runtime, first add an AR Trackable Notify Component to a Blueprint actor:</span></span> 

![Ancoraggi nello spazio AR Trackable Notify](images/unreal-spatialmapping-artrackablenotify.PNG)

<span data-ttu-id="9c96f-119">Passa quindi ai dettagli del componente e fai clic sul pulsante verde "+" per selezionare gli eventi da monitorare.</span><span class="sxs-lookup"><span data-stu-id="9c96f-119">Then go to the component’s details and click on the green “+” button on the events to monitor.</span></span> 

![Eventi sugli ancoraggi nello spazio](images/unreal-spatialmapping-events.PNG)

<span data-ttu-id="9c96f-121">In questo caso viene monitorato l'evento On Add Tracked Geometry, con sui si cercano le mesh globali valide corrispondenti ai dati di mapping spaziale, e viene modificato il materiale della mesh:</span><span class="sxs-lookup"><span data-stu-id="9c96f-121">In this case we monitor the On Add Tracked Geometry event looking for valid world meshes which correspond to spatial mapping data, and change the mesh’s material:</span></span> 

![Esempi di ancoraggi nello spazio](images/unreal-spatialmapping-example.PNG)

<span data-ttu-id="9c96f-123">In C++ è possibile sottoscrivere il delegato OnTrackableAdded per ottenere ARTrackedGeometry non appena risulta disponibile.</span><span class="sxs-lookup"><span data-stu-id="9c96f-123">In C++, we can subscribe to the OnTrackableAdded delegate to get the ARTrackedGeometry as soon as it is available.</span></span>  <span data-ttu-id="9c96f-124">Sono presenti delegati simili per gli eventi aggiornati e rimossi: AddOnTrackableUpdatedDelegate_Handle e AddOnTrackableRemovedDelegate_Handle.</span><span class="sxs-lookup"><span data-stu-id="9c96f-124">There are similar delegates for updated and removed events: AddOnTrackableUpdatedDelegate_Handle and AddOnTrackableRemovedDelegate_Handle.</span></span> 

![Esempio di ancoraggi nello spazio in codice C++](images/unreal-spatialmapping-examplecode.PNG)

<span data-ttu-id="9c96f-126">Il file build.cs del progetto deve contenere "AugmentedReality" nell'elenco PublicDependencyModuleNames in modo da includere "ARBlueprintLibrary.h" e "MRMesh" per l'ispezione del componente MRMesh di UARTrackedGeometry.</span><span class="sxs-lookup"><span data-stu-id="9c96f-126">The project’s build.cs must have “AugmentedReality” in the PublicDependencyModuleNames list to include “ARBlueprintLibrary.h” and “MRMesh” to inspect the MRMesh component of the UARTrackedGeometry.</span></span> 

<span data-ttu-id="9c96f-127">Il mapping spaziale non è l'unico tipo di dati presentato tramite ARTrackedGeometries ed è quindi necessario verificare in primo luogo che EARObjectClassification sia impostato su World, in modo da indicare che si tratta di geometria di mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="9c96f-127">Spatial mapping is not the only type of data that gets surfaced through ARTrackedGeometries, so we first check that the EARObjectClassification is World, which indicates that this is spatial mapping geometry.</span></span> 

## <a name="see-also"></a><span data-ttu-id="9c96f-128">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9c96f-128">See also</span></span>
* [<span data-ttu-id="9c96f-129">Mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="9c96f-129">Spatial mapping</span></span>](spatial-mapping.md)

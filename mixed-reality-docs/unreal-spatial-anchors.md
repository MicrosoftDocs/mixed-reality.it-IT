---
title: Ancoraggi nello spazio in Unreal
description: Guida all'uso degli ancoraggi nello spazio in Unreal
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, sviluppo, funzionalità, documentazione, guide, ologrammi, ancoraggi nello spazio
ms.openlocfilehash: c35d8efc9998aac5b40de833e5acbf7f80353e6b
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840140"
---
# <a name="spatial-anchors-in-unreal"></a><span data-ttu-id="ab7a4-104">Ancoraggi nello spazio in Unreal</span><span class="sxs-lookup"><span data-stu-id="ab7a4-104">Spatial Anchors in Unreal</span></span>

<span data-ttu-id="ab7a4-105">Gli ancoraggi nello spazio consentono di salvare in modo permanente gli ologrammi nel mondo reale tra le sessioni dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="ab7a4-105">Spatial anchors are used to persist holograms in real-world space between application sessions.</span></span>  <span data-ttu-id="ab7a4-106">Questa operazione viene rilevata tramite Unreal come oggetti ARPin e viene salvata nell'archivio di ancoraggio di HoloLens per il caricamento nelle sessioni successive.</span><span class="sxs-lookup"><span data-stu-id="ab7a4-106">This gets surfaced through Unreal as ARPins and gets saved in the HoloLens’ anchor store to be loaded in future sessions.</span></span> 

<span data-ttu-id="ab7a4-107">Prima di salvare o caricare gli ancoraggi, verifica innanzitutto che l'archivio di ancoraggio sia pronto.</span><span class="sxs-lookup"><span data-stu-id="ab7a4-107">Before saving or loading anchors, first check that the anchor store is ready.</span></span>  <span data-ttu-id="ab7a4-108">Il tentativo di chiamare una delle funzioni di ancoraggio di HoloLens prima che l'archivio di ancoraggio sia pronto avrà esito negativo.</span><span class="sxs-lookup"><span data-stu-id="ab7a4-108">Attempting to call any of the HoloLens anchor functions before the anchor store is ready will not succeed.</span></span>  

![Archivio di ancoraggi nello spazio pronto](images/unreal-spatialanchors-store-ready.PNG)

## <a name="save-anchors"></a><span data-ttu-id="ab7a4-110">Salvare gli ancoraggi</span><span class="sxs-lookup"><span data-stu-id="ab7a4-110">Save Anchors</span></span>

<span data-ttu-id="ab7a4-111">Quando l'applicazione dispone di un componente che deve essere aggiunto al mondo reale, può salvarlo nell'archivio di ancoraggio con la sequenza illustrata di seguito:</span><span class="sxs-lookup"><span data-stu-id="ab7a4-111">Once the application has a component that needs to be pinned to the world, it can be saved to the anchor store with the following sequence:</span></span> 

![Salvataggio degli ancoraggi nello spazio](images/unreal-spatialanchors-save.PNG)

<span data-ttu-id="ab7a4-113">In questo esempio, generiamo un attore in una posizione nota, creiamo un oggetto ARPin con tale posizione e un nome basato sulla classe dell'attore, aggiungiamo l'attore all'oggetto ARPin e salviamo il segnaposto nell'archivio di ancoraggio di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ab7a4-113">Here, we are spawning an actor at a known location, creating an ARPin with that location and a name based on the actor’s class, adding the actor to the ARPin, and saving the pin to the HoloLens anchor store.</span></span>  <span data-ttu-id="ab7a4-114">Il nome dell'ancoraggio scelto deve essere univoco, quindi in questo esempio aggiungiamo il timestamp corrente.</span><span class="sxs-lookup"><span data-stu-id="ab7a4-114">The anchor name we choose must be unique, so in this example we append the current timestamp.</span></span>  <span data-ttu-id="ab7a4-115">Se l'ancoraggio viene salvato correttamente nell'archivio di ancoraggio, può essere ispezionato nel portale del dispositivo HoloLens in System > Map manager > Anchor Files Saved On Device (Sistema > Gestore mappe > File di ancoraggio salvati sul dispositivo).</span><span class="sxs-lookup"><span data-stu-id="ab7a4-115">If the anchor successfully saves to the anchor store, it can be inspected in the HoloLens device portal under System > Map manager > Anchor Files Saved On Device.</span></span> 

## <a name="load-anchors"></a><span data-ttu-id="ab7a4-116">Caricare gli ancoraggi</span><span class="sxs-lookup"><span data-stu-id="ab7a4-116">Load Anchors</span></span>

<span data-ttu-id="ab7a4-117">Quando un'applicazione viene avviata, puoi chiamare il progetto seguente per ripristinare i componenti nelle rispettive posizioni di ancoraggio:</span><span class="sxs-lookup"><span data-stu-id="ab7a4-117">When an application starts, the following blueprint can be called to restore components to their anchor locations:</span></span>

![Caricamento degli ancoraggi nello spazio](images/unreal-spatialanchors-load.PNG)

<span data-ttu-id="ab7a4-119">In questo esempio, eseguiamo l'iterazione di tutti gli ancoraggi nell'archivio di ancoraggio, generiamo un attore in corrispondenza dell'identità e aggiungiamo tale attore all'oggetto ARPin dall'archivio di ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="ab7a4-119">In this example, we iterate over all of the anchors in the anchor store, spawn an actor at identity, and pin that actor to the ARPin from the anchor store.</span></span>  <span data-ttu-id="ab7a4-120">È importante generare l'attore in corrispondenza dell'identità, perché l'ancoraggio è responsabile del riposizionamento dell'ologramma nel mondo reale, in base alla posizione in cui è stato salvato; in modo che qualsiasi trasformazione aggiunta qui, aggiunga un offset all'ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="ab7a4-120">It is important to spawn the actor at identity since the anchor is responsible for repositioning the hologram in the world based on where it was saved, so any transform added here will add an offset to the anchor.</span></span> 

<span data-ttu-id="ab7a4-121">Eseguiamo anche una query sull'ID di ancoraggio, in modo che sia possibile generare attori diversi in base al nome salvato dell'ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="ab7a4-121">The anchor ID is also queried so that different actors can be spawned depending on the anchor’s saved name.</span></span> 

## <a name="remove-anchors"></a><span data-ttu-id="ab7a4-122">Rimuovere gli ancoraggi</span><span class="sxs-lookup"><span data-stu-id="ab7a4-122">Remove Anchors</span></span> 

<span data-ttu-id="ab7a4-123">Al termine dell'ancoraggio, puoi cancellare l'intero archivio di ancoraggio oppure rimuovere singoli ancoraggi dall'archivio di ancoraggio, in modo che non vengano inclusi nelle sessioni future:</span><span class="sxs-lookup"><span data-stu-id="ab7a4-123">When done with an anchor, the entire anchor store can be cleared, or individual anchors can be removed from the anchor store so they are not included in future sessions:</span></span> 

![Rimozione degli ancoraggi nello spazio](images/unreal-spatialanchors-remove.PNG)

## <a name="see-also"></a><span data-ttu-id="ab7a4-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ab7a4-125">See also</span></span>
* [<span data-ttu-id="ab7a4-126">Ancoraggi nello spazio</span><span class="sxs-lookup"><span data-stu-id="ab7a4-126">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="ab7a4-127">Sistemi di coordinate</span><span class="sxs-lookup"><span data-stu-id="ab7a4-127">Coordinate systems</span></span>](coordinate-systems.md)

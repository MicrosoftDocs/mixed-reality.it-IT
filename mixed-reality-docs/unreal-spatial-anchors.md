---
title: Ancoraggi nello spazio in Unreal
description: Guida all'uso degli ancoraggi nello spazio in Unreal
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, sviluppo, funzionalità, documentazione, guide, ologrammi, ancoraggi nello spazio
ms.openlocfilehash: 1100704cae40de1997eb869bfc6c82bba3d0dc6e
ms.sourcegitcommit: ee7f04148d3608b0284c59e33b394a67f0934255
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2020
ms.locfileid: "84428737"
---
# <a name="spatial-anchors-in-unreal"></a><span data-ttu-id="89e65-104">Ancoraggi nello spazio in Unreal</span><span class="sxs-lookup"><span data-stu-id="89e65-104">Spatial Anchors in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="89e65-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="89e65-105">Overview</span></span>

<span data-ttu-id="89e65-106">Gli ancoraggi nello spazio consentono di salvare gli ologrammi nel mondo reale in più sessioni dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="89e65-106">Spatial anchors are used to save holograms in real-world space between application sessions.</span></span>  <span data-ttu-id="89e65-107">Questi vengono esposti tramite Unreal come oggetti **ARPin** e salvati nell'archivio degli ancoraggi di HoloLens che viene caricato nelle sessioni future.</span><span class="sxs-lookup"><span data-stu-id="89e65-107">These get surfaced through Unreal as **ARPin**s and saved in the HoloLens’ anchor store, which is loaded in future sessions.</span></span> 

## <a name="checking-the-anchor-store"></a><span data-ttu-id="89e65-108">Verifica dell'archivio degli ancoraggi</span><span class="sxs-lookup"><span data-stu-id="89e65-108">Checking the anchor store</span></span>

<span data-ttu-id="89e65-109">Prima di salvare o caricare gli ancoraggi, verifica che l'archivio degli ancoraggi sia pronto.</span><span class="sxs-lookup"><span data-stu-id="89e65-109">Before saving or loading anchors, you need to check if the anchor store is ready.</span></span>  <span data-ttu-id="89e65-110">Se chiami una delle funzioni di ancoraggio di HoloLens prima che l'archivio degli ancoraggi sia pronto, la chiamata avrà esito negativo.</span><span class="sxs-lookup"><span data-stu-id="89e65-110">Calling any of the HoloLens anchor functions before the anchor store is ready will not succeed.</span></span>  

![Archivio di ancoraggi nello spazio pronto](images/unreal-spatialanchors-store-ready.PNG)

## <a name="saving-anchors"></a><span data-ttu-id="89e65-112">Salvataggio degli ancoraggi</span><span class="sxs-lookup"><span data-stu-id="89e65-112">Saving anchors</span></span>

<span data-ttu-id="89e65-113">Quando l'applicazione dispone di un componente che deve essere aggiunto al mondo reale, può salvarlo nell'archivio di ancoraggio con la sequenza illustrata di seguito:</span><span class="sxs-lookup"><span data-stu-id="89e65-113">Once the application has a component that needs to be pinned to the world, it can be saved to the anchor store with the following sequence:</span></span> 

![Salvataggio degli ancoraggi nello spazio](images/unreal-spatialanchors-save.PNG)

<span data-ttu-id="89e65-115">Operazioni da eseguire:</span><span class="sxs-lookup"><span data-stu-id="89e65-115">Breaking this down:</span></span>
1. <span data-ttu-id="89e65-116">Genera un attore in una posizione nota.</span><span class="sxs-lookup"><span data-stu-id="89e65-116">Spawn an actor at a known location.</span></span>
2. <span data-ttu-id="89e65-117">Crea un oggetto **ARPin** con quella posizione e un nome basato sulla classe dell'attore.</span><span class="sxs-lookup"><span data-stu-id="89e65-117">Create an **ARPin** with that location and a name based on the actor’s class.</span></span> 
3. <span data-ttu-id="89e65-118">Aggiungi l'attore all'oggetto **ARPin** e salva il segnaposto nell'archivio degli ancoraggi di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="89e65-118">Add the actor to the **ARPin** and save the pin to the HoloLens anchor store.</span></span>  
    * <span data-ttu-id="89e65-119">Il nome dell'ancoraggio scelto deve essere univoco. In questo esempio è usato il timestamp corrente.</span><span class="sxs-lookup"><span data-stu-id="89e65-119">The anchor name you choose must be unique, which in this example is the current timestamp.</span></span> 

4. <span data-ttu-id="89e65-120">Se l'ancoraggio viene salvato correttamente nell'archivio degli ancoraggi, puoi ispezionarlo nel portale del dispositivo HoloLens in **System > Map manager > Anchor Files Saved On Device** (Sistema > Gestore mappe > File di ancoraggio salvati sul dispositivo).</span><span class="sxs-lookup"><span data-stu-id="89e65-120">If the anchor is successfully saved to the anchor store, you can be inspect it in the HoloLens device portal under **System > Map manager > Anchor Files Saved On Device**.</span></span> 

## <a name="loading-anchors"></a><span data-ttu-id="89e65-121">Caricamento degli ancoraggi</span><span class="sxs-lookup"><span data-stu-id="89e65-121">Loading anchors</span></span>

<span data-ttu-id="89e65-122">Quando un'applicazione viene avviata, puoi usare il progetto seguente per ripristinare i componenti nelle rispettive posizioni di ancoraggio:</span><span class="sxs-lookup"><span data-stu-id="89e65-122">When an application starts, you can use the following blueprint to restore components to their anchor locations:</span></span>

![Caricamento degli ancoraggi nello spazio](images/unreal-spatialanchors-load.PNG)

<span data-ttu-id="89e65-124">Operazioni da eseguire:</span><span class="sxs-lookup"><span data-stu-id="89e65-124">Breaking this down:</span></span>
1. <span data-ttu-id="89e65-125">Esegui l'iterazione di tutti gli ancoraggi nell'archivio degli ancoraggi.</span><span class="sxs-lookup"><span data-stu-id="89e65-125">Iterate over all of the anchors in the anchor store.</span></span> 
2. <span data-ttu-id="89e65-126">Genera un attore in corrispondenza dell'identità.</span><span class="sxs-lookup"><span data-stu-id="89e65-126">Spawn an actor at identity.</span></span>
3. <span data-ttu-id="89e65-127">Blocca quell'attore sull'oggetto **ARPin** dall'archivio degli ancoraggi.</span><span class="sxs-lookup"><span data-stu-id="89e65-127">Pin that actor to the **ARPin** from the anchor store.</span></span>  

    * <span data-ttu-id="89e65-128">È importante generare l'attore in corrispondenza dell'identità perché l'ancoraggio è responsabile del riposizionamento dell'ologramma nel mondo reale, in base alla posizione in cui è stato salvato.</span><span class="sxs-lookup"><span data-stu-id="89e65-128">It's important to spawn the actor at identity since the anchor is responsible for repositioning the hologram in the world based on where it was saved.</span></span> <span data-ttu-id="89e65-129">Qualsiasi trasformazione aggiunta qui aggiungerà un offset all'ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="89e65-129">Any transform added here will add an offset to the anchor.</span></span> 

<span data-ttu-id="89e65-130">Eseguiamo anche una query sull'ID di ancoraggio, in modo che sia possibile generare attori diversi in base al nome salvato dell'ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="89e65-130">The anchor ID is also queried so that different actors can be spawned depending on the anchor’s saved name.</span></span> 

## <a name="removing-anchors"></a><span data-ttu-id="89e65-131">Rimozione degli ancoraggi</span><span class="sxs-lookup"><span data-stu-id="89e65-131">Removing anchors</span></span> 

<span data-ttu-id="89e65-132">Terminate le operazioni su un ancoraggio, puoi eliminare singoli ancoraggi o l'intero archivio degli ancoraggi con i componenti **Remove ARPin from WMRAnchor Store** (Rimuovi ARPin dall'archivio WMRAnchor) e **Remove All ARPins from WMRAnchor Store** (Rimuovi tutti gli ARPin dall'archivio WMRAnchor).</span><span class="sxs-lookup"><span data-stu-id="89e65-132">When you're done with an anchor you can clear individual anchors or the entire anchor store with the **Remove ARPin from WMRAnchor Store** and **Remove All ARPins from WMRAnchor Store** components.</span></span>

![Rimozione degli ancoraggi nello spazio](images/unreal-spatialanchors-remove.PNG)

> [!NOTE]
> <span data-ttu-id="89e65-134">Tieni presente che gli ancoraggi spaziali sono ancora in versione beta, quindi visualizza di nuovo questa pagina in futuro per verificare se sono presenti informazioni e funzionalità aggiornate.</span><span class="sxs-lookup"><span data-stu-id="89e65-134">Bear in mind that Spatial Anchors are still in Beta, so be sure to check back for updated information and features.</span></span>

## <a name="see-also"></a><span data-ttu-id="89e65-135">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="89e65-135">See also</span></span>
* [<span data-ttu-id="89e65-136">Ancoraggi nello spazio</span><span class="sxs-lookup"><span data-stu-id="89e65-136">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="89e65-137">Sistemi di coordinate</span><span class="sxs-lookup"><span data-stu-id="89e65-137">Coordinate systems</span></span>](coordinate-systems.md)

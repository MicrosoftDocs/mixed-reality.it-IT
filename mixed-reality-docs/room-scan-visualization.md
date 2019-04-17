---
title: Visualizzazione analisi chat room
description: Le applicazioni che richiedono i dati di mapping spaziale si basano sul dispositivo per raccogliere automaticamente i dati nel tempo e tra le sessioni dell'utente esamina il proprio ambiente con il dispositivo attivo.
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, i modelli dell'App, la progettazione, HoloLens, analisi di chat, spaziali mapping, surface, ricostruzione mesh
ms.openlocfilehash: 8ffde9d476e25016f986321377dce8125ee3a596
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604649"
---
# <a name="room-scan-visualization"></a><span data-ttu-id="5d7f9-104">Visualizzazione analisi chat room</span><span class="sxs-lookup"><span data-stu-id="5d7f9-104">Room scan visualization</span></span>

<span data-ttu-id="5d7f9-105">Le applicazioni che richiedono i dati di mapping spaziale si basano sul dispositivo per raccogliere automaticamente i dati nel tempo e tra le sessioni dell'utente esamina il proprio ambiente con il dispositivo attivo.</span><span class="sxs-lookup"><span data-stu-id="5d7f9-105">Applications that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="5d7f9-106">La completezza e la qualità dei dati dipende da diversi fattori tra cui la quantità di esplorazione che l'utente ha eseguito, quanto tempo è trascorso l'esplorazione e se gli oggetti, ad esempio le porte e mobili hanno spostata dal momento che il dispositivo analizzato l'area.</span><span class="sxs-lookup"><span data-stu-id="5d7f9-106">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span>

<span data-ttu-id="5d7f9-107">Per assicurarsi che i dati di mapping spaziale utili, gli sviluppatori di applicazioni dispongono diverse opzioni:</span><span class="sxs-lookup"><span data-stu-id="5d7f9-107">To ensure useful spatial mapping data, applications developers have several options:</span></span>
* <span data-ttu-id="5d7f9-108">Si basano su ciò che potrebbe già raccolti.</span><span class="sxs-lookup"><span data-stu-id="5d7f9-108">Rely on what may have already been collected.</span></span> <span data-ttu-id="5d7f9-109">Inizialmente, i dati potrebbero essere incompleti.</span><span class="sxs-lookup"><span data-stu-id="5d7f9-109">This data may be incomplete initially.</span></span>
* <span data-ttu-id="5d7f9-110">Chiedere all'utente di usare il movimento bloom per ottenere in Windows Mixed Reality casa e poi ne esplorerò l'area in cui che si vuole usare per l'esperienza.</span><span class="sxs-lookup"><span data-stu-id="5d7f9-110">Ask the user to use the bloom gesture to get to the Windows Mixed Reality home and then explore the area they wish to use for the experience.</span></span> <span data-ttu-id="5d7f9-111">Usano indice puntato per confermare che tutta l'area necessario sia note al dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5d7f9-111">They can use air-tap to confirm that all the necessary area is known to the device.</span></span>
* <span data-ttu-id="5d7f9-112">Creare un'esperienza di esplorazione personalizzata nelle proprie applicazioni.</span><span class="sxs-lookup"><span data-stu-id="5d7f9-112">Build a custom exploration experience in their own application.</span></span>

<span data-ttu-id="5d7f9-113">Si noti che in tutti questi casi i dati effettivi raccolti durante l'esplorazione vengano memorizzati dal sistema e l'applicazione non è necessario eseguire questa operazione.</span><span class="sxs-lookup"><span data-stu-id="5d7f9-113">Note that in all these cases the actual data gathered during the exploration is stored by the system and the application does not need to do this.</span></span>

## <a name="device-support"></a><span data-ttu-id="5d7f9-114">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="5d7f9-114">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="5d7f9-115">Funzionalità</span><span class="sxs-lookup"><span data-stu-id="5d7f9-115">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="5d7f9-116"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="5d7f9-116"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="5d7f9-117"><a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></span><span class="sxs-lookup"><span data-stu-id="5d7f9-117"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="5d7f9-118">Visualizzazione analisi chat room</span><span class="sxs-lookup"><span data-stu-id="5d7f9-118">Room scan visualization</span></span></td><td style="text-align: center;"> <span data-ttu-id="5d7f9-119">✔️</span><span class="sxs-lookup"><span data-stu-id="5d7f9-119">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>



## <a name="building-a-custom-scanning-experience"></a><span data-ttu-id="5d7f9-120">Creazione di un'esperienza di analisi personalizzata</span><span class="sxs-lookup"><span data-stu-id="5d7f9-120">Building a custom scanning experience</span></span>

<span data-ttu-id="5d7f9-121">Le applicazioni possono decidere di analizzare i dati di mapping spaziale all'inizio dell'esperienza per giudicare se desiderano all'utente di eseguire passaggi aggiuntivi per migliorare la qualità e la completezza.</span><span class="sxs-lookup"><span data-stu-id="5d7f9-121">Applications may decide to analyze the spatial mapping data at the start of the experience to judge whether they want the user to perform additional steps to improve its completeness and quality.</span></span> <span data-ttu-id="5d7f9-122">Se analisi indicano che occorre migliorare qualità, gli sviluppatori devono fornire una visualizzazione a sovrapposizione nel mondo per indicare:</span><span class="sxs-lookup"><span data-stu-id="5d7f9-122">If analysis indicates quality should be improved, developers should provide a visualization to overlay on the world to indicate:</span></span>
* <span data-ttu-id="5d7f9-123">In che misura il volume totale in prossimità degli utenti deve far parte dell'esperienza</span><span class="sxs-lookup"><span data-stu-id="5d7f9-123">How much of the total volume in the users vicinity needs to be part of the experience</span></span>
* <span data-ttu-id="5d7f9-124">In cui l'utente deve passare per migliorare i dati</span><span class="sxs-lookup"><span data-stu-id="5d7f9-124">Where the user should go to improve data</span></span>

<span data-ttu-id="5d7f9-125">Gli utenti non conosce ciò che rende un'analisi "good".</span><span class="sxs-lookup"><span data-stu-id="5d7f9-125">Users do not know what makes a "good" scan.</span></span> <span data-ttu-id="5d7f9-126">Devono essere visualizzato o indicato cosa cercare se viene chiesto di valutazione di un'analisi – appiattimento, distanza dal pareti effettive, e così via. Lo sviluppatore deve implementare un ciclo di feedback che include l'aggiornamento dei dati di mapping spaziale durante la fase di analisi o esplorazione.</span><span class="sxs-lookup"><span data-stu-id="5d7f9-126">They need to be shown or told what to look for if they’re asked to evaluate a scan – flatness, distance from actual walls, etc. The developer should implement a feedback loop that includes refreshing the spatial mapping data during the scanning or exploration phase.</span></span>

<span data-ttu-id="5d7f9-127">In molti casi, potrebbe essere preferibile informare l'utente ne servano per (ad esempio, esaminare il tetto massimo, cercare dietro mobili), per ottenere la qualità di analisi necessarie.</span><span class="sxs-lookup"><span data-stu-id="5d7f9-127">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

## <a name="cached-versus-continuous-spatial-mapping"></a><span data-ttu-id="5d7f9-128">Memorizzato nella cache rispetto a continuo mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="5d7f9-128">Cached versus continuous spatial mapping</span></span>

<span data-ttu-id="5d7f9-129">I dati di mapping spaziale sono il peso più elevato possono utilizzare le applicazioni di origine dati.</span><span class="sxs-lookup"><span data-stu-id="5d7f9-129">The spatial mapping data is the most heavy weight data source applications can consume.</span></span> <span data-ttu-id="5d7f9-130">Per evitare problemi di prestazioni, ad esempio fotogrammi rimossi o stuttering, il consumo dei dati deve essere eseguito con attenzione.</span><span class="sxs-lookup"><span data-stu-id="5d7f9-130">To avoid performance issues such as dropped frames or stuttering, consumption of this data should be done carefully.</span></span>

<span data-ttu-id="5d7f9-131">La scansione attiva durante un'esperienza può essere sia utile o effetti negativi sulla e lo sviluppatore avrà bisogno decidere quale metodo utilizzare basati sull'esperienza.</span><span class="sxs-lookup"><span data-stu-id="5d7f9-131">Active scanning during an experience can be both beneficial or detrimental and the developer will need to decide which method to use based on the experience.</span></span>

### <a name="cached-spatial-mapping"></a><span data-ttu-id="5d7f9-132">Mapping spaziale memorizzato nella cache</span><span class="sxs-lookup"><span data-stu-id="5d7f9-132">Cached spatial mapping</span></span>

<span data-ttu-id="5d7f9-133">Nel caso di mapping spaziale memorizzato nella cache, l'applicazione in genere uno snapshot dei dati di mapping spaziale e Usa questo snapshot per la durata dell'esperienza.</span><span class="sxs-lookup"><span data-stu-id="5d7f9-133">In the case of cached spatial mapping, the application typically takes a snapshot of the spatial mapping data and uses this snapshot for the duration of the experience.</span></span>

<span data-ttu-id="5d7f9-134">**Vantaggi**</span><span class="sxs-lookup"><span data-stu-id="5d7f9-134">**Benefits**</span></span>
* <span data-ttu-id="5d7f9-135">Ridotto il sovraccarico del sistema durante l'esperienza di esecuzione iniziale alla sostanziale potenza, termico e miglioramento delle prestazioni della cpu.</span><span class="sxs-lookup"><span data-stu-id="5d7f9-135">Reduced overhead on the system while the experience is running leading to dramatic power, thermal and cpu performance gains.</span></span>
* <span data-ttu-id="5d7f9-136">Un'implementazione più semplice dell'esperienza di principale, dal momento che non venga interrotto dalle modifiche apportate ai dati spaziali.</span><span class="sxs-lookup"><span data-stu-id="5d7f9-136">A simpler implementation of the main experience since it is not interrupted by changes in the spatial data.</span></span>
* <span data-ttu-id="5d7f9-137">Un singolo momento i costi qualsiasi post-elaborazione dei dati spaziali per altri scopi, grafica ed effetti fisici.</span><span class="sxs-lookup"><span data-stu-id="5d7f9-137">A single one time cost on any post processing of the spatial data for physics, graphics and other purposes.</span></span>

<span data-ttu-id="5d7f9-138">**Svantaggi**</span><span class="sxs-lookup"><span data-stu-id="5d7f9-138">**Drawbacks**</span></span>
* <span data-ttu-id="5d7f9-139">Lo spostamento di oggetti reali o persone che non si riflette in base ai dati memorizzati nella cache.</span><span class="sxs-lookup"><span data-stu-id="5d7f9-139">The movement of real world objects or people is not reflected by the cached data.</span></span> <span data-ttu-id="5d7f9-140">Ad esempio</span><span class="sxs-lookup"><span data-stu-id="5d7f9-140">E.g.</span></span> <span data-ttu-id="5d7f9-141">l'applicazione potrebbe prendere in considerazione lo sportello di un'aperta quando è effettivamente chiusa ora.</span><span class="sxs-lookup"><span data-stu-id="5d7f9-141">the application might consider a door open when it is actually closed now.</span></span>
* <span data-ttu-id="5d7f9-142">Potenzialmente più memoria dell'applicazione per gestire la versione memorizzata nella cache dei dati.</span><span class="sxs-lookup"><span data-stu-id="5d7f9-142">Potentially more application memory to maintain the cached version of the data.</span></span>

<span data-ttu-id="5d7f9-143">Un buon caso per questo metodo è un ambiente controllato o un gioco tabella principale.</span><span class="sxs-lookup"><span data-stu-id="5d7f9-143">A good case for this method is a controlled environment or a table top game.</span></span>

### <a name="continuous-spatial-mapping"></a><span data-ttu-id="5d7f9-144">Mapping spaziale continuo</span><span class="sxs-lookup"><span data-stu-id="5d7f9-144">Continuous spatial mapping</span></span>

<span data-ttu-id="5d7f9-145">Alcune applicazioni possono basarsi via prosegue l'analisi per aggiornare i dati di mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="5d7f9-145">Certain applications may rely on continues scanning to refresh spatial mapping data.</span></span>

<span data-ttu-id="5d7f9-146">**Vantaggi**</span><span class="sxs-lookup"><span data-stu-id="5d7f9-146">**Benefits**</span></span>
* <span data-ttu-id="5d7f9-147">Non è necessario compilare un' separato la scansione o l'esplorazione esperienza costo anticipato nell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="5d7f9-147">You don't need to build in a separate scanning or exploration experience upfront in your application.</span></span>
* <span data-ttu-id="5d7f9-148">Lo spostamento di oggetti reali può essere ottenuto mediante reflection da gioco, sebbene con un ritardo.</span><span class="sxs-lookup"><span data-stu-id="5d7f9-148">The movement of real world objects can be reflected by the game, although with some delay.</span></span>

<span data-ttu-id="5d7f9-149">**Svantaggi**</span><span class="sxs-lookup"><span data-stu-id="5d7f9-149">**Drawbacks**</span></span>
* <span data-ttu-id="5d7f9-150">Maggiore complessità nell'implementazione dell'esperienza di principale.</span><span class="sxs-lookup"><span data-stu-id="5d7f9-150">Higher complexity in the implementation of the main experience.</span></span>
* <span data-ttu-id="5d7f9-151">Potenziale sovraccarico dell'elaborazione aggiuntiva per l'elemento grafico o fisica come modifiche devono essere inseriti in modo incrementale da questi sistemi.</span><span class="sxs-lookup"><span data-stu-id="5d7f9-151">Potential overhead of the additional processing for graphic or physics as changes need to be incrementally ingested by these systems.</span></span>
* <span data-ttu-id="5d7f9-152">Una capacità superiore, termico e impatto sulla CPU.</span><span class="sxs-lookup"><span data-stu-id="5d7f9-152">Higher power, thermal and CPU impact.</span></span>

<span data-ttu-id="5d7f9-153">Un buon caso per questo metodo è uno in cui è previsti vntana per interagire con lo spostamento di oggetti, ad esempio, un'automobile holographic unità sul pavimento potrebbe voler correttamente si incorra nello sportello di una se è aperto o chiuso.</span><span class="sxs-lookup"><span data-stu-id="5d7f9-153">A good case for this method is one where holograms are expected to interact with moving objects, e.g. a holographic car that drives on the floor may want to correctly bump into a door depending on whether it is open or closed.</span></span>

## <a name="see-also"></a><span data-ttu-id="5d7f9-154">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5d7f9-154">See also</span></span>
* [<span data-ttu-id="5d7f9-155">Progettazione di mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="5d7f9-155">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="5d7f9-156">Sistemi di coordinate</span><span class="sxs-lookup"><span data-stu-id="5d7f9-156">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="5d7f9-157">Progettazione spaziale</span><span class="sxs-lookup"><span data-stu-id="5d7f9-157">Spatial sound design</span></span>](spatial-sound-design.md)

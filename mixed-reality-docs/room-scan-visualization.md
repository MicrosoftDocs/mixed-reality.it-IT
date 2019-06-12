---
title: Visualizzazione analisi chat room
description: Le applicazioni che richiedono i dati di mapping spaziale si basano sul dispositivo per raccogliere automaticamente i dati nel tempo e tra le sessioni dell'utente esamina il proprio ambiente con il dispositivo attivo.
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, i modelli dell'App, la progettazione, HoloLens, analisi di chat, spaziali mapping, surface, ricostruzione mesh
ms.openlocfilehash: 09df4464ea4dac01dfad637886b07b861f468d4d
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829907"
---
# <a name="room-scan-visualization"></a><span data-ttu-id="73bf3-104">Visualizzazione analisi chat room</span><span class="sxs-lookup"><span data-stu-id="73bf3-104">Room scan visualization</span></span>

<span data-ttu-id="73bf3-105">Le applicazioni che richiedono i dati di mapping spaziale si basano sul dispositivo per raccogliere automaticamente i dati nel tempo e tra le sessioni dell'utente esamina il proprio ambiente con il dispositivo attivo.</span><span class="sxs-lookup"><span data-stu-id="73bf3-105">Applications that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="73bf3-106">La completezza e la qualità dei dati dipende da diversi fattori tra cui la quantità di esplorazione che l'utente ha eseguito, quanto tempo è trascorso l'esplorazione e se gli oggetti, ad esempio le porte e mobili hanno spostata dal momento che il dispositivo analizzato l'area.</span><span class="sxs-lookup"><span data-stu-id="73bf3-106">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span>

<span data-ttu-id="73bf3-107">Per assicurarsi che i dati di mapping spaziale utili, gli sviluppatori di applicazioni dispongono diverse opzioni:</span><span class="sxs-lookup"><span data-stu-id="73bf3-107">To ensure useful spatial mapping data, applications developers have several options:</span></span>
* <span data-ttu-id="73bf3-108">Si basano su ciò che potrebbe già raccolti.</span><span class="sxs-lookup"><span data-stu-id="73bf3-108">Rely on what may have already been collected.</span></span> <span data-ttu-id="73bf3-109">Inizialmente, i dati potrebbero essere incompleti.</span><span class="sxs-lookup"><span data-stu-id="73bf3-109">This data may be incomplete initially.</span></span>
* <span data-ttu-id="73bf3-110">Chiedere all'utente di usare il movimento bloom per ottenere in Windows Mixed Reality casa e poi ne esplorerò l'area in cui che si vuole usare per l'esperienza.</span><span class="sxs-lookup"><span data-stu-id="73bf3-110">Ask the user to use the bloom gesture to get to the Windows Mixed Reality home and then explore the area they wish to use for the experience.</span></span> <span data-ttu-id="73bf3-111">Usano indice puntato per confermare che tutta l'area necessario sia note al dispositivo.</span><span class="sxs-lookup"><span data-stu-id="73bf3-111">They can use air-tap to confirm that all the necessary area is known to the device.</span></span>
* <span data-ttu-id="73bf3-112">Creare un'esperienza di esplorazione personalizzata nelle proprie applicazioni.</span><span class="sxs-lookup"><span data-stu-id="73bf3-112">Build a custom exploration experience in their own application.</span></span>

<span data-ttu-id="73bf3-113">Si noti che in tutti questi casi i dati effettivi raccolti durante l'esplorazione vengano memorizzati dal sistema e l'applicazione non è necessario eseguire questa operazione.</span><span class="sxs-lookup"><span data-stu-id="73bf3-113">Note that in all these cases the actual data gathered during the exploration is stored by the system and the application does not need to do this.</span></span>

## <a name="device-support"></a><span data-ttu-id="73bf3-114">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="73bf3-114">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="73bf3-115"><strong>Funzionalità</strong></span><span class="sxs-lookup"><span data-stu-id="73bf3-115"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="73bf3-116"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="73bf3-116"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="73bf3-117"><a href="immersive-headset-hardware-details.md"><strong>Auricolari coinvolgenti</strong></a></span><span class="sxs-lookup"><span data-stu-id="73bf3-117"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="73bf3-118">Visualizzazione analisi chat room</span><span class="sxs-lookup"><span data-stu-id="73bf3-118">Room scan visualization</span></span></td>
        <td><span data-ttu-id="73bf3-119">✔️</span><span class="sxs-lookup"><span data-stu-id="73bf3-119">✔️</span></span></td>
        <td><span data-ttu-id="73bf3-120">❌</span><span class="sxs-lookup"><span data-stu-id="73bf3-120">❌</span></span></td>
    </tr>
</table>



## <a name="building-a-custom-scanning-experience"></a><span data-ttu-id="73bf3-121">Creazione di un'esperienza di analisi personalizzata</span><span class="sxs-lookup"><span data-stu-id="73bf3-121">Building a custom scanning experience</span></span>

<span data-ttu-id="73bf3-122">Le applicazioni possono decidere di analizzare i dati di mapping spaziale all'inizio dell'esperienza per giudicare se desiderano all'utente di eseguire passaggi aggiuntivi per migliorare la qualità e la completezza.</span><span class="sxs-lookup"><span data-stu-id="73bf3-122">Applications may decide to analyze the spatial mapping data at the start of the experience to judge whether they want the user to perform additional steps to improve its completeness and quality.</span></span> <span data-ttu-id="73bf3-123">Se analisi indicano che occorre migliorare qualità, gli sviluppatori devono fornire una visualizzazione a sovrapposizione nel mondo per indicare:</span><span class="sxs-lookup"><span data-stu-id="73bf3-123">If analysis indicates quality should be improved, developers should provide a visualization to overlay on the world to indicate:</span></span>
* <span data-ttu-id="73bf3-124">In che misura il volume totale in prossimità degli utenti deve far parte dell'esperienza</span><span class="sxs-lookup"><span data-stu-id="73bf3-124">How much of the total volume in the users vicinity needs to be part of the experience</span></span>
* <span data-ttu-id="73bf3-125">In cui l'utente deve passare per migliorare i dati</span><span class="sxs-lookup"><span data-stu-id="73bf3-125">Where the user should go to improve data</span></span>

<span data-ttu-id="73bf3-126">Gli utenti non conosce ciò che rende un'analisi "good".</span><span class="sxs-lookup"><span data-stu-id="73bf3-126">Users do not know what makes a "good" scan.</span></span> <span data-ttu-id="73bf3-127">Devono essere visualizzato o indicato cosa cercare se viene chiesto di valutazione di un'analisi – appiattimento, distanza dal pareti effettive, e così via. Lo sviluppatore deve implementare un ciclo di feedback che include l'aggiornamento dei dati di mapping spaziale durante la fase di analisi o esplorazione.</span><span class="sxs-lookup"><span data-stu-id="73bf3-127">They need to be shown or told what to look for if they’re asked to evaluate a scan – flatness, distance from actual walls, etc. The developer should implement a feedback loop that includes refreshing the spatial mapping data during the scanning or exploration phase.</span></span>

<span data-ttu-id="73bf3-128">In molti casi, potrebbe essere preferibile informare l'utente ne servano per (ad esempio, esaminare il tetto massimo, cercare dietro mobili), per ottenere la qualità di analisi necessarie.</span><span class="sxs-lookup"><span data-stu-id="73bf3-128">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

## <a name="cached-versus-continuous-spatial-mapping"></a><span data-ttu-id="73bf3-129">Memorizzato nella cache rispetto a continuo mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="73bf3-129">Cached versus continuous spatial mapping</span></span>

<span data-ttu-id="73bf3-130">I dati di mapping spaziale sono il peso più elevato possono utilizzare le applicazioni di origine dati.</span><span class="sxs-lookup"><span data-stu-id="73bf3-130">The spatial mapping data is the most heavy weight data source applications can consume.</span></span> <span data-ttu-id="73bf3-131">Per evitare problemi di prestazioni, ad esempio fotogrammi rimossi o stuttering, il consumo dei dati deve essere eseguito con attenzione.</span><span class="sxs-lookup"><span data-stu-id="73bf3-131">To avoid performance issues such as dropped frames or stuttering, consumption of this data should be done carefully.</span></span>

<span data-ttu-id="73bf3-132">La scansione attiva durante un'esperienza può essere sia utile o effetti negativi sulla e lo sviluppatore avrà bisogno decidere quale metodo utilizzare basati sull'esperienza.</span><span class="sxs-lookup"><span data-stu-id="73bf3-132">Active scanning during an experience can be both beneficial or detrimental and the developer will need to decide which method to use based on the experience.</span></span>

### <a name="cached-spatial-mapping"></a><span data-ttu-id="73bf3-133">Mapping spaziale memorizzato nella cache</span><span class="sxs-lookup"><span data-stu-id="73bf3-133">Cached spatial mapping</span></span>

<span data-ttu-id="73bf3-134">Nel caso di mapping spaziale memorizzato nella cache, l'applicazione in genere uno snapshot dei dati di mapping spaziale e Usa questo snapshot per la durata dell'esperienza.</span><span class="sxs-lookup"><span data-stu-id="73bf3-134">In the case of cached spatial mapping, the application typically takes a snapshot of the spatial mapping data and uses this snapshot for the duration of the experience.</span></span>

<span data-ttu-id="73bf3-135">**Vantaggi**</span><span class="sxs-lookup"><span data-stu-id="73bf3-135">**Benefits**</span></span>
* <span data-ttu-id="73bf3-136">Ridotto il sovraccarico del sistema durante l'esperienza di esecuzione iniziale alla sostanziale potenza, termico e miglioramento delle prestazioni della cpu.</span><span class="sxs-lookup"><span data-stu-id="73bf3-136">Reduced overhead on the system while the experience is running leading to dramatic power, thermal and cpu performance gains.</span></span>
* <span data-ttu-id="73bf3-137">Un'implementazione più semplice dell'esperienza di principale, dal momento che non venga interrotto dalle modifiche apportate ai dati spaziali.</span><span class="sxs-lookup"><span data-stu-id="73bf3-137">A simpler implementation of the main experience since it is not interrupted by changes in the spatial data.</span></span>
* <span data-ttu-id="73bf3-138">Un singolo momento i costi qualsiasi post-elaborazione dei dati spaziali per altri scopi, grafica ed effetti fisici.</span><span class="sxs-lookup"><span data-stu-id="73bf3-138">A single one time cost on any post processing of the spatial data for physics, graphics and other purposes.</span></span>

<span data-ttu-id="73bf3-139">**Svantaggi**</span><span class="sxs-lookup"><span data-stu-id="73bf3-139">**Drawbacks**</span></span>
* <span data-ttu-id="73bf3-140">Lo spostamento di oggetti reali o persone che non si riflette in base ai dati memorizzati nella cache.</span><span class="sxs-lookup"><span data-stu-id="73bf3-140">The movement of real world objects or people is not reflected by the cached data.</span></span> <span data-ttu-id="73bf3-141">Ad esempio</span><span class="sxs-lookup"><span data-stu-id="73bf3-141">E.g.</span></span> <span data-ttu-id="73bf3-142">l'applicazione potrebbe prendere in considerazione lo sportello di un'aperta quando è effettivamente chiusa ora.</span><span class="sxs-lookup"><span data-stu-id="73bf3-142">the application might consider a door open when it is actually closed now.</span></span>
* <span data-ttu-id="73bf3-143">Potenzialmente più memoria dell'applicazione per gestire la versione memorizzata nella cache dei dati.</span><span class="sxs-lookup"><span data-stu-id="73bf3-143">Potentially more application memory to maintain the cached version of the data.</span></span>

<span data-ttu-id="73bf3-144">Un buon caso per questo metodo è un ambiente controllato o un gioco tabella principale.</span><span class="sxs-lookup"><span data-stu-id="73bf3-144">A good case for this method is a controlled environment or a table top game.</span></span>

### <a name="continuous-spatial-mapping"></a><span data-ttu-id="73bf3-145">Mapping spaziale continuo</span><span class="sxs-lookup"><span data-stu-id="73bf3-145">Continuous spatial mapping</span></span>

<span data-ttu-id="73bf3-146">Alcune applicazioni possono basarsi via prosegue l'analisi per aggiornare i dati di mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="73bf3-146">Certain applications may rely on continues scanning to refresh spatial mapping data.</span></span>

<span data-ttu-id="73bf3-147">**Vantaggi**</span><span class="sxs-lookup"><span data-stu-id="73bf3-147">**Benefits**</span></span>
* <span data-ttu-id="73bf3-148">Non è necessario compilare un' separato la scansione o l'esplorazione esperienza costo anticipato nell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="73bf3-148">You don't need to build in a separate scanning or exploration experience upfront in your application.</span></span>
* <span data-ttu-id="73bf3-149">Lo spostamento di oggetti reali può essere ottenuto mediante reflection da gioco, sebbene con un ritardo.</span><span class="sxs-lookup"><span data-stu-id="73bf3-149">The movement of real world objects can be reflected by the game, although with some delay.</span></span>

<span data-ttu-id="73bf3-150">**Svantaggi**</span><span class="sxs-lookup"><span data-stu-id="73bf3-150">**Drawbacks**</span></span>
* <span data-ttu-id="73bf3-151">Maggiore complessità nell'implementazione dell'esperienza di principale.</span><span class="sxs-lookup"><span data-stu-id="73bf3-151">Higher complexity in the implementation of the main experience.</span></span>
* <span data-ttu-id="73bf3-152">Potenziale sovraccarico dell'elaborazione aggiuntiva per l'elemento grafico o fisica come modifiche devono essere inseriti in modo incrementale da questi sistemi.</span><span class="sxs-lookup"><span data-stu-id="73bf3-152">Potential overhead of the additional processing for graphic or physics as changes need to be incrementally ingested by these systems.</span></span>
* <span data-ttu-id="73bf3-153">Una capacità superiore, termico e impatto sulla CPU.</span><span class="sxs-lookup"><span data-stu-id="73bf3-153">Higher power, thermal and CPU impact.</span></span>

<span data-ttu-id="73bf3-154">Un buon caso per questo metodo è uno in cui è previsti vntana per interagire con lo spostamento di oggetti, ad esempio, un'automobile holographic unità sul pavimento potrebbe voler correttamente si incorra nello sportello di una se è aperto o chiuso.</span><span class="sxs-lookup"><span data-stu-id="73bf3-154">A good case for this method is one where holograms are expected to interact with moving objects, e.g. a holographic car that drives on the floor may want to correctly bump into a door depending on whether it is open or closed.</span></span>

## <a name="see-also"></a><span data-ttu-id="73bf3-155">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="73bf3-155">See also</span></span>
* [<span data-ttu-id="73bf3-156">Progettazione del mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="73bf3-156">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="73bf3-157">Sistemi di coordinate</span><span class="sxs-lookup"><span data-stu-id="73bf3-157">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="73bf3-158">Progettazione dell'audio spaziale</span><span class="sxs-lookup"><span data-stu-id="73bf3-158">Spatial sound design</span></span>](spatial-sound-design.md)

---
title: Visualizzazione analisi chat room
description: Le applicazioni che richiedono dati di mapping spaziali si basano sul dispositivo per raccogliere automaticamente questi dati nel tempo e nelle sessioni mentre l'utente Esplora il proprio ambiente con il dispositivo attivo.
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, modelli di app, progettazione, HoloLens, analisi chat room, mapping spaziale, mesh
ms.openlocfilehash: bdb070407f27d04046bd022894c7a8a01b9658d1
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437520"
---
# <a name="room-scan-visualization"></a><span data-ttu-id="b0f07-104">Visualizzazione analisi chat room</span><span class="sxs-lookup"><span data-stu-id="b0f07-104">Room scan visualization</span></span>

<span data-ttu-id="b0f07-105">Le applicazioni che richiedono dati di mapping spaziali si basano sul dispositivo per raccogliere automaticamente questi dati nel tempo e nelle sessioni mentre l'utente Esplora il proprio ambiente con il dispositivo attivo.</span><span class="sxs-lookup"><span data-stu-id="b0f07-105">Applications that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="b0f07-106">La completezza e la qualità di questi dati dipendono da diversi fattori, tra cui la quantità di esplorazione eseguita dall'utente, il tempo trascorso dall'esplorazione e l'eventuale spostamento degli oggetti, ad esempio mobili e porte, dal momento in cui il dispositivo ha analizzato l'area.</span><span class="sxs-lookup"><span data-stu-id="b0f07-106">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span>

<span data-ttu-id="b0f07-107">Per garantire dati di mapping spaziali utili, gli sviluppatori di applicazioni dispongono di diverse opzioni:</span><span class="sxs-lookup"><span data-stu-id="b0f07-107">To ensure useful spatial mapping data, applications developers have several options:</span></span>
* <span data-ttu-id="b0f07-108">Basarsi su ciò che è già stato raccolto.</span><span class="sxs-lookup"><span data-stu-id="b0f07-108">Rely on what may have already been collected.</span></span> <span data-ttu-id="b0f07-109">Questi dati potrebbero essere inizialmente incompleti.</span><span class="sxs-lookup"><span data-stu-id="b0f07-109">This data may be incomplete initially.</span></span>
* <span data-ttu-id="b0f07-110">Chiedere all'utente di usare il movimento Bloom per ottenere la Home realtà mista di Windows e quindi esplorare l'area che si vuole usare per l'esperienza.</span><span class="sxs-lookup"><span data-stu-id="b0f07-110">Ask the user to use the bloom gesture to get to the Windows Mixed Reality home and then explore the area they wish to use for the experience.</span></span> <span data-ttu-id="b0f07-111">Possono usare il tocco aereo per verificare che tutte le aree necessarie siano note al dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b0f07-111">They can use air-tap to confirm that all the necessary area is known to the device.</span></span>
* <span data-ttu-id="b0f07-112">Crea un'esperienza di esplorazione personalizzata nella propria applicazione.</span><span class="sxs-lookup"><span data-stu-id="b0f07-112">Build a custom exploration experience in their own application.</span></span>

<span data-ttu-id="b0f07-113">Si noti che in tutti questi casi i dati effettivi raccolti durante l'esplorazione vengono archiviati dal sistema e non è necessario che l'applicazione esegua questa operazione.</span><span class="sxs-lookup"><span data-stu-id="b0f07-113">Note that in all these cases the actual data gathered during the exploration is stored by the system and the application does not need to do this.</span></span>

## <a name="device-support"></a><span data-ttu-id="b0f07-114">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="b0f07-114">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b0f07-115"><strong>Funzionalità</strong></span><span class="sxs-lookup"><span data-stu-id="b0f07-115"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="b0f07-116"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="b0f07-116"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="b0f07-117"><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="b0f07-117"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b0f07-118">Visualizzazione analisi chat room</span><span class="sxs-lookup"><span data-stu-id="b0f07-118">Room scan visualization</span></span></td>
        <td><span data-ttu-id="b0f07-119">✔️</span><span class="sxs-lookup"><span data-stu-id="b0f07-119">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>



## <a name="building-a-custom-scanning-experience"></a><span data-ttu-id="b0f07-120">Creazione di un'esperienza di analisi personalizzata</span><span class="sxs-lookup"><span data-stu-id="b0f07-120">Building a custom scanning experience</span></span>

<span data-ttu-id="b0f07-121">Le applicazioni possono decidere di analizzare i dati di mapping spaziali all'inizio dell'esperienza per valutare se desiderano che l'utente esegua ulteriori passaggi per migliorare la sua completezza e qualità.</span><span class="sxs-lookup"><span data-stu-id="b0f07-121">Applications may decide to analyze the spatial mapping data at the start of the experience to judge whether they want the user to perform additional steps to improve its completeness and quality.</span></span> <span data-ttu-id="b0f07-122">Se l'analisi indica che è necessario migliorare la qualità, gli sviluppatori devono fornire una visualizzazione da sovrapporre al mondo per indicare:</span><span class="sxs-lookup"><span data-stu-id="b0f07-122">If analysis indicates quality should be improved, developers should provide a visualization to overlay on the world to indicate:</span></span>
* <span data-ttu-id="b0f07-123">La quantità di volume totale in prossimità degli utenti deve essere parte integrante dell'esperienza</span><span class="sxs-lookup"><span data-stu-id="b0f07-123">How much of the total volume in the users vicinity needs to be part of the experience</span></span>
* <span data-ttu-id="b0f07-124">Dove l'utente deve passare per migliorare i dati</span><span class="sxs-lookup"><span data-stu-id="b0f07-124">Where the user should go to improve data</span></span>

<span data-ttu-id="b0f07-125">Gli utenti non sono a conoscenza di ciò che fa un'analisi "positiva".</span><span class="sxs-lookup"><span data-stu-id="b0f07-125">Users do not know what makes a "good" scan.</span></span> <span data-ttu-id="b0f07-126">È necessario visualizzare o indicare gli elementi da cercare se viene chiesto di valutare un'analisi, ovvero la planarità, la distanza dai muri effettivi e così via. Lo sviluppatore deve implementare un ciclo di feedback che includa l'aggiornamento dei dati di mapping spaziale durante la fase di analisi o di esplorazione.</span><span class="sxs-lookup"><span data-stu-id="b0f07-126">They need to be shown or told what to look for if they’re asked to evaluate a scan – flatness, distance from actual walls, etc. The developer should implement a feedback loop that includes refreshing the spatial mapping data during the scanning or exploration phase.</span></span>

<span data-ttu-id="b0f07-127">In molti casi, può essere preferibile informare l'utente di cosa è necessario fare (ad esempio, osservare il soffitto, guardare dietro la mobilia), per ottenere la qualità di analisi necessaria.</span><span class="sxs-lookup"><span data-stu-id="b0f07-127">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

## <a name="cached-versus-continuous-spatial-mapping"></a><span data-ttu-id="b0f07-128">Memorizzazione nella cache rispetto al mapping spaziale continuo</span><span class="sxs-lookup"><span data-stu-id="b0f07-128">Cached versus continuous spatial mapping</span></span>

<span data-ttu-id="b0f07-129">I dati di mapping spaziali sono le applicazioni che possono essere utilizzate dalle applicazioni di origine dati con maggiore peso.</span><span class="sxs-lookup"><span data-stu-id="b0f07-129">The spatial mapping data is the most heavy weight data source applications can consume.</span></span> <span data-ttu-id="b0f07-130">Per evitare problemi di prestazioni, ad esempio i frame eliminati o la balbuzie, l'utilizzo di questi dati deve essere eseguito con cautela.</span><span class="sxs-lookup"><span data-stu-id="b0f07-130">To avoid performance issues such as dropped frames or stuttering, consumption of this data should be done carefully.</span></span>

<span data-ttu-id="b0f07-131">L'analisi attiva durante un'esperienza può essere utile o dannosa e lo sviluppatore dovrà decidere quale metodo utilizzare in base all'esperienza.</span><span class="sxs-lookup"><span data-stu-id="b0f07-131">Active scanning during an experience can be both beneficial or detrimental and the developer will need to decide which method to use based on the experience.</span></span>

### <a name="cached-spatial-mapping"></a><span data-ttu-id="b0f07-132">Mapping spaziale memorizzato nella cache</span><span class="sxs-lookup"><span data-stu-id="b0f07-132">Cached spatial mapping</span></span>

<span data-ttu-id="b0f07-133">Nel caso del mapping spaziale memorizzato nella cache, l'applicazione esegue in genere uno snapshot dei dati di mapping spaziali e utilizza questo snapshot per la durata dell'esperienza.</span><span class="sxs-lookup"><span data-stu-id="b0f07-133">In the case of cached spatial mapping, the application typically takes a snapshot of the spatial mapping data and uses this snapshot for the duration of the experience.</span></span>

<span data-ttu-id="b0f07-134">**Vantaggi**</span><span class="sxs-lookup"><span data-stu-id="b0f07-134">**Benefits**</span></span>
* <span data-ttu-id="b0f07-135">Riduzione del sovraccarico sul sistema durante l'esecuzione dell'esperienza con un notevole miglioramento delle prestazioni, della temperatura e della CPU.</span><span class="sxs-lookup"><span data-stu-id="b0f07-135">Reduced overhead on the system while the experience is running leading to dramatic power, thermal and cpu performance gains.</span></span>
* <span data-ttu-id="b0f07-136">Un'implementazione più semplice dell'esperienza principale, poiché non viene interrotta dalle modifiche nei dati spaziali.</span><span class="sxs-lookup"><span data-stu-id="b0f07-136">A simpler implementation of the main experience since it is not interrupted by changes in the spatial data.</span></span>
* <span data-ttu-id="b0f07-137">Costo singolo per ogni post elaborazione dei dati spaziali per la fisica, la grafica e altri scopi.</span><span class="sxs-lookup"><span data-stu-id="b0f07-137">A single one time cost on any post processing of the spatial data for physics, graphics and other purposes.</span></span>

<span data-ttu-id="b0f07-138">**Svantaggi**</span><span class="sxs-lookup"><span data-stu-id="b0f07-138">**Drawbacks**</span></span>
* <span data-ttu-id="b0f07-139">Lo spostamento di oggetti o persone reali non viene riflesso dai dati memorizzati nella cache.</span><span class="sxs-lookup"><span data-stu-id="b0f07-139">The movement of real world objects or people is not reflected by the cached data.</span></span> <span data-ttu-id="b0f07-140">Ad esempio</span><span class="sxs-lookup"><span data-stu-id="b0f07-140">E.g.</span></span> <span data-ttu-id="b0f07-141">è possibile che l'applicazione prenda in considerazione uno sportello aperto quando viene effettivamente chiuso.</span><span class="sxs-lookup"><span data-stu-id="b0f07-141">the application might consider a door open when it is actually closed now.</span></span>
* <span data-ttu-id="b0f07-142">Potenzialmente più memoria dell'applicazione per mantenere la versione memorizzata nella cache dei dati.</span><span class="sxs-lookup"><span data-stu-id="b0f07-142">Potentially more application memory to maintain the cached version of the data.</span></span>

<span data-ttu-id="b0f07-143">Un caso valido per questo metodo è un ambiente controllato o una tabella Top Game.</span><span class="sxs-lookup"><span data-stu-id="b0f07-143">A good case for this method is a controlled environment or a table top game.</span></span>

### <a name="continuous-spatial-mapping"></a><span data-ttu-id="b0f07-144">Mapping spaziale continuo</span><span class="sxs-lookup"><span data-stu-id="b0f07-144">Continuous spatial mapping</span></span>

<span data-ttu-id="b0f07-145">Alcune applicazioni possono basarsi sull'analisi continua per aggiornare i dati di mapping spaziali.</span><span class="sxs-lookup"><span data-stu-id="b0f07-145">Certain applications may rely on continues scanning to refresh spatial mapping data.</span></span>

<span data-ttu-id="b0f07-146">**Vantaggi**</span><span class="sxs-lookup"><span data-stu-id="b0f07-146">**Benefits**</span></span>
* <span data-ttu-id="b0f07-147">Non è necessario creare un'esperienza di analisi o esplorazione separata in anticipo nell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="b0f07-147">You don't need to build in a separate scanning or exploration experience upfront in your application.</span></span>
* <span data-ttu-id="b0f07-148">Lo spostamento di oggetti reali può essere riflesso dal gioco, anche se con un certo ritardo.</span><span class="sxs-lookup"><span data-stu-id="b0f07-148">The movement of real world objects can be reflected by the game, although with some delay.</span></span>

<span data-ttu-id="b0f07-149">**Svantaggi**</span><span class="sxs-lookup"><span data-stu-id="b0f07-149">**Drawbacks**</span></span>
* <span data-ttu-id="b0f07-150">Maggiore complessità nell'implementazione dell'esperienza principale.</span><span class="sxs-lookup"><span data-stu-id="b0f07-150">Higher complexity in the implementation of the main experience.</span></span>
* <span data-ttu-id="b0f07-151">Potenziale sovraccarico dell'elaborazione aggiuntiva per la grafica o la fisica, in quanto le modifiche devono essere inserite in modo incrementale da questi sistemi.</span><span class="sxs-lookup"><span data-stu-id="b0f07-151">Potential overhead of the additional processing for graphic or physics as changes need to be incrementally ingested by these systems.</span></span>
* <span data-ttu-id="b0f07-152">Maggiore potenza, temperatura e effetti sulla CPU.</span><span class="sxs-lookup"><span data-stu-id="b0f07-152">Higher power, thermal and CPU impact.</span></span>

<span data-ttu-id="b0f07-153">Un caso ideale per questo metodo è quello in cui gli ologrammi devono interagire con gli oggetti mobili, ad esempio, un'automobile olografica che può inserirsi in uno sportello a seconda che sia aperta o chiusa.</span><span class="sxs-lookup"><span data-stu-id="b0f07-153">A good case for this method is one where holograms are expected to interact with moving objects, e.g. a holographic car that drives on the floor may want to correctly bump into a door depending on whether it is open or closed.</span></span>

## <a name="see-also"></a><span data-ttu-id="b0f07-154">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="b0f07-154">See also</span></span>
* [<span data-ttu-id="b0f07-155">Mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="b0f07-155">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="b0f07-156">Sistemi di coordinate</span><span class="sxs-lookup"><span data-stu-id="b0f07-156">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="b0f07-157">Progettazione dell'audio spaziale</span><span class="sxs-lookup"><span data-stu-id="b0f07-157">Spatial sound design</span></span>](spatial-sound-design.md)

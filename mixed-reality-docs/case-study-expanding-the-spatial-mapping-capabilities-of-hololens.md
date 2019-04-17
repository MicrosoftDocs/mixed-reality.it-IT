---
title: 'Case study: distribuire le funzionalità di mapping spaziale di HoloLens'
description: Quando si crea la prima App per Microsoft HoloLens, siamo felici di poter vedere solo fino a quando è stato possibile oltrepassare i limiti della mapping spaziale nel dispositivo.
author: jevertt
ms.author: jevertt
ms.date: 03/21/2018
ms.topic: article
keywords: Mapping spaziale di realtà mista di Windows, HoloLens,
ms.openlocfilehash: 602b629afa5900ff34c28b3a3a32725af06590b7
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602833"
---
# <a name="case-study---expanding-the-spatial-mapping-capabilities-of-hololens"></a><span data-ttu-id="7e5f7-104">Case study: distribuire le funzionalità di mapping spaziale di HoloLens</span><span class="sxs-lookup"><span data-stu-id="7e5f7-104">Case study - Expanding the spatial mapping capabilities of HoloLens</span></span>

<span data-ttu-id="7e5f7-105">Quando si crea la prima App per Microsoft HoloLens, siamo felici di poter vedere solo fino a quando è stato possibile oltrepassare i limiti della mapping spaziale nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-105">When creating our first apps for Microsoft HoloLens, we were eager to see just how far we could push the boundaries of spatial mapping on the device.</span></span> <span data-ttu-id="7e5f7-106">Jeff Evertt, software engineer presso Microsoft Studios, descrive come una nuova tecnologia sviluppata dalla necessità di maggiore controllo sul modo in cui vntana viene inseriti in un ambiente dell'utente reale.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-106">Jeff Evertt, a software engineer at Microsoft Studios, explains how a new technology was developed out of the need for more control over how holograms are placed in a user's real-world environment.</span></span>

## <a name="watch-the-video"></a><span data-ttu-id="7e5f7-107">Guarda il video</span><span class="sxs-lookup"><span data-stu-id="7e5f7-107">Watch the video</span></span>

>[!VIDEO https://www.youtube.com/embed/iUmTi3_Ynus]

## <a name="beyond-spatial-mapping"></a><span data-ttu-id="7e5f7-108">Oltre a mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="7e5f7-108">Beyond spatial mapping</span></span>

<span data-ttu-id="7e5f7-109">Mentre stavamo lavorando [frammenti](https://www.microsoft.com/p/fragments/9nblggh5ggm8) e [Young Conker](https://www.microsoft.com/p/young-conker/9nblggh5ggk1), due dei giochi prima per HoloLens, abbiamo scoperto che se stessimo posizionamento procedura di vntana nel mondo fisico, è necessario un livello superiore comprensione sull'ambiente dell'utente.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-109">While we were working on [Fragments](https://www.microsoft.com/p/fragments/9nblggh5ggm8) and [Young Conker](https://www.microsoft.com/p/young-conker/9nblggh5ggk1), two of the first games for HoloLens, we found that when we were doing procedural placement of holograms in the physical world, we needed a higher level of understanding about the user's environment.</span></span> <span data-ttu-id="7e5f7-110">Ogni gioco ha esigenze la propria posizione specifica: In frammenti, ad esempio, volevamo essere in grado di distinguere tra diverse superfici, ad esempio una tabella o la parte intera, inserire indizi in località pertinenti.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-110">Each game had its own specific placement needs: In Fragments, for example, we wanted to be able to distinguish between different surfaces—such as the floor or a table—to place clues in relevant locations.</span></span> <span data-ttu-id="7e5f7-111">Desideravamo anche essere in grado di identificare le superfici che caratteri holographic dimensioni reali è stato possibile attendere in, ad esempio un divano o una sedia.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-111">We also wanted to be able to identify surfaces that life-size holographic characters could sit on, such as a couch or a chair.</span></span> <span data-ttu-id="7e5f7-112">In Conker Young, volevamo Conker e il suo avversari per poter usare superfici generate nella chat room del giocatore come piattaforme.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-112">In Young Conker, we wanted Conker and his opponents to be able to use raised surfaces in a player's room as platforms.</span></span>

<span data-ttu-id="7e5f7-113">[Registrazione in Studio Asobo](http://www.asobostudio.com/index.html), il nostro partner di sviluppo per questi giochi, dovuto affrontare il problema; e creato una tecnologia che estende le funzionalità di mapping spaziale di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-113">[Asobo Studios](http://www.asobostudio.com/index.html), our development partner for these games, faced this problem head-on and created a technology that extends the spatial mapping capabilities of HoloLens.</span></span> <span data-ttu-id="7e5f7-114">In questo modo si sarebbe analizza stanza del giocatore e identificare aree, ad esempio pareti, le tabelle, anche di sedie e piani.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-114">Using this, we could analyze a player's room and identify surfaces such as walls, tables, chairs, and floors.</span></span> <span data-ttu-id="7e5f7-115">Ha anche fornito a Microsoft la possibilità di ottimizzare rispetto a un set di vincoli per determinare il posizionamento ottimale per gli oggetti holographic.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-115">It also gave us the ability to optimize against a set of constraints to determine the best placement for holographic objects.</span></span>

## <a name="the-spatial-understanding-code"></a><span data-ttu-id="7e5f7-116">Il codice di conoscenza spaziali</span><span class="sxs-lookup"><span data-stu-id="7e5f7-116">The spatial understanding code</span></span>

<span data-ttu-id="7e5f7-117">Abbiamo impiegato codice originale del Asobo e creato una libreria che incapsula questa tecnologia.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-117">We took Asobo's original code and created a library that encapsulates this technology.</span></span> <span data-ttu-id="7e5f7-118">Microsoft e Asobo abbiamo reso open-source questo codice e averlo reso disponibile nel [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) da usare nei propri progetti.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-118">Microsoft and Asobo have now open-sourced this code and made it available on [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) for you to use in your own projects.</span></span> <span data-ttu-id="7e5f7-119">Tutto il codice sorgente è incluso, consentendo di personalizzarlo in base alle esigenze e condividere i miglioramenti con la community.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-119">All the source code is included, allowing you to customize it to your needs and share your improvements with the community.</span></span> <span data-ttu-id="7e5f7-120">Il codice per il C++ Risolutore è stato eseguito il wrapping in una DLL UWP ed esposto a Unity con una [prefab vera e propria contenute MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding).</span><span class="sxs-lookup"><span data-stu-id="7e5f7-120">The code for the C++ solver has been wrapped into a UWP DLL and exposed to Unity with a [drop-in prefab contained within MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding).</span></span>

<span data-ttu-id="7e5f7-121">Ci sono molte query utili inclusa nell'esempio di Unity che è possibile trovare gli spazi vuoti delle pareti, posizionare gli oggetti al tetto massimo o in spazi di grandi dimensioni sul pavimento, identificare le aree per i caratteri per un periodo e una miriade di altre query spaziali comprensione.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-121">There are many useful queries included in the Unity sample that will allow you to find empty spaces on walls, place objects on the ceiling or on large spaces on the floor, identify places for characters to sit, and a myriad of other spatial understanding queries.</span></span>

<span data-ttu-id="7e5f7-122">Mentre la soluzione di mapping spaziale fornita da HoloLens è progettata per essere abbastanza generici per soddisfare le esigenze dell'intera gamma di aree di problemi, il modulo understanding spaziale è stato compilato per supportare le esigenze dei giochi specifiche due.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-122">While the spatial mapping solution provided by HoloLens is designed to be generic enough to meet the needs of the entire gamut of problem spaces, the spatial understanding module was built to support the needs of two specific games.</span></span> <span data-ttu-id="7e5f7-123">Di conseguenza, la soluzione è strutturata su un processo specifico e un set dei presupposti:</span><span class="sxs-lookup"><span data-stu-id="7e5f7-123">As such, its solution is structured around a specific process and set of assumptions:</span></span>
* <span data-ttu-id="7e5f7-124">**Risolto dimensioni playspace**: L'utente specifica le dimensioni massime playspace nella chiamata di init.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-124">**Fixed size playspace**: The user specifies the maximum playspace size in the init call.</span></span>
* <span data-ttu-id="7e5f7-125">**Processo di analisi occasionale**: Il processo richiede una discreta analizzando fase in cui l'utente scorre attorno a, che definisce il playspace.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-125">**One-time scan process**: The process requires a discrete scanning phase where the user walks around, defining the playspace.</span></span> <span data-ttu-id="7e5f7-126">Funzioni di query non saranno disponibili fino a dopo l'analisi è stata finalizzata.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-126">Query functions will not function until after the scan has been finalized.</span></span>
* <span data-ttu-id="7e5f7-127">**Utente basato sui playspace "disegno"**: Durante la fase di analisi, l'utente si sposta e Cerca intorno playspace, disegno in modo efficace le aree che devono essere incluse.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-127">**User driven playspace “painting”**: During the scanning phase, the user moves and looks around the playspace, effectively painting the areas which should be included.</span></span> <span data-ttu-id="7e5f7-128">La trama generata è importante fornire commenti e suggerimenti utente durante questa fase.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-128">The generated mesh is important to provide user feedback during this phase.</span></span>
* <span data-ttu-id="7e5f7-129">**In ambienti chiusi installazione domestica o aziendale**: Le funzioni di query sono progettate attorno superfici flat e walls ad angolo retto.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-129">**Indoors home or office setup**: The query functions are designed around flat surfaces and walls at right angles.</span></span> <span data-ttu-id="7e5f7-130">Si tratta di una limitazione temporanea.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-130">This is a soft limitation.</span></span> <span data-ttu-id="7e5f7-131">Tuttavia, durante la fase di analisi, un'asse primario viene completata l'analisi per ottimizzare la suddivisione a mosaico di mesh lungo l'asse principale e secondaria.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-131">However, during the scanning phase, a primary axis analysis is completed to optimize the mesh tessellation along major and minor axis.</span></span>

### <a name="room-scanning-process"></a><span data-ttu-id="7e5f7-132">Processo di analisi chat room</span><span class="sxs-lookup"><span data-stu-id="7e5f7-132">Room Scanning Process</span></span>

<span data-ttu-id="7e5f7-133">Quando si carica il modulo spaziali comprensione, la prima cosa è necessario è analizzare lo spazio, in modo che tutte le superfici utilizzabile, ad esempio walls, floor e ceiling, ovvero vengono identificati e con etichetta.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-133">When you load the spatial understanding module, the first thing you'll do is scan your space, so all the usable surfaces—such as the floor, ceiling, and walls—are identified and labeled.</span></span> <span data-ttu-id="7e5f7-134">Durante il processo di analisi Guardatevi intorno la chat e "paint' le aree che devono essere incluse nell'analisi.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-134">During the scanning process, you look around your room and "paint' the areas that should be included in the scan.</span></span>

<span data-ttu-id="7e5f7-135">Il reticolato visualizzato durante questa fase è un componente essenziale della risposta visiva che consente agli utenti di sapere quali parti della chat room vengono sottoposti a scansione.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-135">The mesh seen during this phase is an important piece of visual feedback that lets users know what parts of the room are being scanned.</span></span> <span data-ttu-id="7e5f7-136">La DLL per il modulo di conoscenza spaziali archivia internamente il playspace come una griglia dei cubi voxel 8cm ridimensionato.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-136">The DLL for the spatial understanding module internally stores the playspace as a grid of 8cm sized voxel cubes.</span></span> <span data-ttu-id="7e5f7-137">Durante la parte iniziale di analisi, per determinare gli assi della chat room viene completata un'analisi in componenti principali.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-137">During the initial part of scanning, a primary component analysis is completed to determine the axes of the room.</span></span> <span data-ttu-id="7e5f7-138">Archivia internamente, il relativo spazio voxel allineato a questi assi.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-138">Internally, it stores its voxel space aligned to these axes.</span></span> <span data-ttu-id="7e5f7-139">Una rete mesh viene generata circa ogni secondo, estraendo l'oggetto isosurface dal volume voxel.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-139">A mesh is generated approximately every second by extracting the isosurface from the voxel volume.</span></span>

![Mapping di rete mesh in bianco e le informazioni playspace spaziali mesh in verde](images/spatial-mapping-500px.png)

<span data-ttu-id="7e5f7-141">Mapping di rete mesh in bianco e le informazioni playspace spaziali mesh in verde</span><span class="sxs-lookup"><span data-stu-id="7e5f7-141">Spatial mapping mesh in white and understanding playspace mesh in green</span></span>



<span data-ttu-id="7e5f7-142">Il file SpatialUnderstanding.cs incluso gestisce il processo di fase di analisi.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-142">The included SpatialUnderstanding.cs file manages the scanning phase process.</span></span> <span data-ttu-id="7e5f7-143">Chiama le funzioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="7e5f7-143">It calls the following functions:</span></span>
* <span data-ttu-id="7e5f7-144">**SpatialUnderstanding_Init**: Chiamato una volta all'inizio.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-144">**SpatialUnderstanding_Init**: Called once at the start.</span></span>
* <span data-ttu-id="7e5f7-145">**GeneratePlayspace_InitScan**: Indica che deve iniziare la fase di analisi.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-145">**GeneratePlayspace_InitScan**: Indicates that the scan phase should begin.</span></span>
* <span data-ttu-id="7e5f7-146">**GeneratePlayspace_UpdateScan_DynamicScan**: Chiamata a ogni fotogramma per aggiornare il processo di analisi.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-146">**GeneratePlayspace_UpdateScan_DynamicScan**: Called each frame to update the scanning process.</span></span> <span data-ttu-id="7e5f7-147">La posizione della fotocamera e l'orientamento viene passata e viene usato per il processo di disegno playspace, descritto in precedenza.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-147">The camera position and orientation is passed in and is used for the playspace painting process, described above.</span></span>
* <span data-ttu-id="7e5f7-148">**GeneratePlayspace_RequestFinish**: Chiamato per finalizzare il playspace.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-148">**GeneratePlayspace_RequestFinish**: Called to finalize the playspace.</span></span> <span data-ttu-id="7e5f7-149">Le aree in cui "disegnate" durante la fase di analisi verranno utilizzate per definire e bloccare il playspace.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-149">This will use the areas “painted” during the scan phase to define and lock the playspace.</span></span> <span data-ttu-id="7e5f7-150">L'applicazione può eseguire una query delle statistiche durante la scansione fase nonché query della rete personalizzata per inviare commenti e suggerimenti utente.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-150">The application can query statistics during the scanning phase as well as query the custom mesh for providing user feedback.</span></span>
* <span data-ttu-id="7e5f7-151">**Import_UnderstandingMesh**: Durante l'analisi, il **SpatialUnderstandingCustomMesh** comportamento fornito dal modulo e inserito nel prefab understanding periodicamente eseguirà una query mesh personalizzate generate dal processo.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-151">**Import_UnderstandingMesh**: During scanning, the **SpatialUnderstandingCustomMesh** behavior provided by the module and placed on the understanding prefab will periodically query the custom mesh generated by the process.</span></span> <span data-ttu-id="7e5f7-152">Inoltre, questa operazione viene eseguita ancora una volta dopo l'analisi è stato finalizzato.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-152">In addition, this is done once more after scanning has been finalized.</span></span>

<span data-ttu-id="7e5f7-153">Il flusso di analisi, dovuto la **SpatialUnderstanding** chiama comportamento **InitScan**, quindi **UpdateScan** ogni fotogramma.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-153">The scanning flow, driven by the **SpatialUnderstanding** behavior calls **InitScan**, then **UpdateScan** each frame.</span></span> <span data-ttu-id="7e5f7-154">Durante la query statistiche report code coverage ragionevole, l'utente può chiamare airtap **RequestFinish** per indicare la fine della fase di analisi.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-154">When the statistics query reports reasonable coverage, the user can airtap to call **RequestFinish** to indicate the end of the scanning phase.</span></span> <span data-ttu-id="7e5f7-155">**UpdateScan** continua a essere chiamato finché non viene restituito il valore indica che la DLL è stata completata l'elaborazione.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-155">**UpdateScan** continues to be called until it’s return value indicates that the DLL has completed processing.</span></span>

## <a name="the-queries"></a><span data-ttu-id="7e5f7-156">Le query</span><span class="sxs-lookup"><span data-stu-id="7e5f7-156">The queries</span></span>

<span data-ttu-id="7e5f7-157">Una volta completata l'analisi, sarà in grado di accedere a tre diversi tipi di query nell'interfaccia:</span><span class="sxs-lookup"><span data-stu-id="7e5f7-157">Once the scan is complete, you'll be able to access three different types of queries in the interface:</span></span>
* <span data-ttu-id="7e5f7-158">**Le query di topologia**: Si tratta di query rapide basati sulla topologia della chat room sottoposta ad analisi.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-158">**Topology queries**: These are fast queries that are based on the topology of the scanned room.</span></span>
* <span data-ttu-id="7e5f7-159">**Forma query**: Si utilizzano i risultati delle query di topologia per trovare le superfici orizzontali che sono una corrispondenza soddisfacente a forme personalizzate definite.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-159">**Shape queries**: These utilize the results of your topology queries to find horizontal surfaces that are a good match to custom shapes that you define.</span></span>
* <span data-ttu-id="7e5f7-160">**Selezione host per le query di oggetto**: Si tratta di query più complesse che trovare il percorso di fallback basato su un set di regole e i vincoli per l'oggetto.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-160">**Object placement queries**: These are more complex queries that find the best-fit location based on a set of rules and constraints for the object.</span></span>

<span data-ttu-id="7e5f7-161">Oltre a tre query primaria, è disponibile un'interfaccia raycasting che può essere usata per recuperare i tipi di area con tag e una rete mesh di chat room stagni personalizzati possono essere copiate.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-161">In addition to the three primary queries, there is a raycasting interface which can be used to retrieve tagged surface types and a custom watertight room mesh can be copied out.</span></span>

### <a name="topology-queries"></a><span data-ttu-id="7e5f7-162">Query di topologia</span><span class="sxs-lookup"><span data-stu-id="7e5f7-162">Topology queries</span></span>

<span data-ttu-id="7e5f7-163">All'interno della DLL, gestione della topologia gestisce l'assegnazione di etichette dell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-163">Within the DLL, the topology manager handles labeling of the environment.</span></span> <span data-ttu-id="7e5f7-164">Come indicato in precedenza, gran parte dei dati verrà archiviata all'interno di surfels, che sono contenuti all'interno di un volume voxel.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-164">As mentioned above, much of the data is stored within surfels, which are contained within a voxel volume.</span></span> <span data-ttu-id="7e5f7-165">Inoltre, il **PlaySpaceInfos** struttura viene utilizzata per archiviare le informazioni sugli playspace, tra cui l'allineamento world (ulteriori dettagli su questo argomento di seguito), floor e ceiling altezza.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-165">In addition, the **PlaySpaceInfos** structure is used to store information about the playspace, including the world alignment (more details on this below), floor, and ceiling height.</span></span>

<span data-ttu-id="7e5f7-166">Vengono usate le euristiche per determinare walls, floor e ceiling.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-166">Heuristics are used for determining floor, ceiling, and walls.</span></span> <span data-ttu-id="7e5f7-167">Ad esempio, la superficie più grande e più basso orizzontale con maggiore di 1 m2 superficie di attacco è considerata il tetto minimo.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-167">For example, the largest and lowest horizontal surface with greater than 1 m2 surface area is considered the floor.</span></span> <span data-ttu-id="7e5f7-168">Si noti che il percorso della fotocamera durante il processo di analisi viene usato anche in questo processo.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-168">Note that the camera path during the scanning process is also used in this process.</span></span>

<span data-ttu-id="7e5f7-169">Un subset delle query esposte da Gestione della topologia sono esposte tramite la DLL.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-169">A subset of the queries exposed by the Topology manager are exposed out through the DLL.</span></span> <span data-ttu-id="7e5f7-170">Le query esposte topologia sono come segue:</span><span class="sxs-lookup"><span data-stu-id="7e5f7-170">The exposed topology queries are as follows:</span></span>
* <span data-ttu-id="7e5f7-171">QueryTopology_FindPositionsOnWalls</span><span class="sxs-lookup"><span data-stu-id="7e5f7-171">QueryTopology_FindPositionsOnWalls</span></span>
* <span data-ttu-id="7e5f7-172">QueryTopology_FindLargePositionsOnWalls</span><span class="sxs-lookup"><span data-stu-id="7e5f7-172">QueryTopology_FindLargePositionsOnWalls</span></span>
* <span data-ttu-id="7e5f7-173">QueryTopology_FindLargestWall</span><span class="sxs-lookup"><span data-stu-id="7e5f7-173">QueryTopology_FindLargestWall</span></span>
* <span data-ttu-id="7e5f7-174">QueryTopology_FindPositionsOnFloor</span><span class="sxs-lookup"><span data-stu-id="7e5f7-174">QueryTopology_FindPositionsOnFloor</span></span>
* <span data-ttu-id="7e5f7-175">QueryTopology_FindLargestPositionsOnFloor</span><span class="sxs-lookup"><span data-stu-id="7e5f7-175">QueryTopology_FindLargestPositionsOnFloor</span></span>
* <span data-ttu-id="7e5f7-176">QueryTopology_FindPositionsSittable</span><span class="sxs-lookup"><span data-stu-id="7e5f7-176">QueryTopology_FindPositionsSittable</span></span>

<span data-ttu-id="7e5f7-177">Ogni query dispone di un set di parametri, specifici per il tipo di query.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-177">Each of the queries has a set of parameters, specific to the query type.</span></span> <span data-ttu-id="7e5f7-178">Nell'esempio seguente, l'utente specifica l'altezza minima & larghezza del volume desiderato, altezza minima posizione di sopra la parte intera e la quantità minima di nulla osta davanti il volume.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-178">In the following example, the user specifies the minimum height & width of the desired volume, minimum placement height above the floor, and the minimum amount of clearance in front of the volume.</span></span> <span data-ttu-id="7e5f7-179">Tutte le misure sono in metri.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-179">All measurements are in meters.</span></span>




```
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
          _In_ float minHeightOfWallSpace,
          _In_ float minWidthOfWallSpace,
          _In_ float minHeightAboveFloor,
          _In_ float minFacingClearance,
          _In_ int locationCount,
          _Inout_ Dll_Interface::TopologyResult* locationData)
```

<span data-ttu-id="7e5f7-180">Ognuna di queste query accetta una matrice di pre-allocata **TopologyResult** strutture.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-180">Each of these queries takes a pre-allocated array of **TopologyResult** structures.</span></span> <span data-ttu-id="7e5f7-181">Il **locationCount** parametro specifica la lunghezza della matrice passata.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-181">The **locationCount** parameter specifies the length of the passed-in array.</span></span> <span data-ttu-id="7e5f7-182">Il valore restituito indica il numero di percorsi restituiti.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-182">The return value reports the number of returned locations.</span></span> <span data-ttu-id="7e5f7-183">Questo numero non è mai maggiore passato **locationCount** parametro.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-183">This number is never greater than the passed-in **locationCount** parameter.</span></span>

<span data-ttu-id="7e5f7-184">Il **TopologyResult** contiene la posizione centrale del volume restituito, la direzione pubblico (ad esempio normale) e le dimensioni dello spazio trovato.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-184">The **TopologyResult** contains the center position of the returned volume, the facing direction (i.e. normal), and the dimensions of the found space.</span></span>




```
struct TopologyResult
     {
          DirectX::XMFLOAT3 position;
          DirectX::XMFLOAT3 normal;
          float width;
          float length;
     };
```

<span data-ttu-id="7e5f7-185">Si noti che nell'esempio di Unity, ognuna di queste query è collegato a un pulsante nel pannello dell'interfaccia utente virtuale.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-185">Note that in the Unity sample, each of these queries is linked up to a button in the virtual UI panel.</span></span> <span data-ttu-id="7e5f7-186">L'esempio rigido codici i parametri per ognuna di queste query valori ragionevoli.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-186">The sample hard codes the parameters for each of these queries to reasonable values.</span></span> <span data-ttu-id="7e5f7-187">Visualizzare *SpaceVisualizer.cs* nel codice di esempio per altri esempi.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-187">See *SpaceVisualizer.cs* in the sample code for more examples.</span></span>

### <a name="shape-queries"></a><span data-ttu-id="7e5f7-188">Query di forma</span><span class="sxs-lookup"><span data-stu-id="7e5f7-188">Shape queries</span></span>

<span data-ttu-id="7e5f7-189">All'interno della DLL, l'analizzatore di forma (**ShapeAnalyzer_W**) usa l'analizzatore di topologia da confrontare con le forme personalizzate definite dall'utente.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-189">Inside of the DLL, the shape analyzer (**ShapeAnalyzer_W**) uses the topology analyzer to match against custom shapes defined by the user.</span></span> <span data-ttu-id="7e5f7-190">L'esempio di Unity è un set predefinito di forme che vengono visualizzati nel menu query, nella scheda della forma.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-190">The Unity sample has a pre-defined set of shapes which are shown in the query menu, on the shape tab.</span></span>

<span data-ttu-id="7e5f7-191">Si noti che l'analisi della forma funziona su superfici orizzontale solo.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-191">Note that the shape analysis works on horizontal surfaces only.</span></span> <span data-ttu-id="7e5f7-192">Un divano, ad esempio, è definito per l'area di postazione flat e flat cima divano nuovamente.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-192">A couch, for example, is defined by the flat seat surface and the flat top of the couch back.</span></span> <span data-ttu-id="7e5f7-193">La query shape è simile per due aree di un determinato intervallo di dimensioni, altezza e aspetto, con due aree delle allineato e connesse.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-193">The shape query looks for two surfaces of a specific size, height, and aspect range, with the two surfaces aligned and connected.</span></span> <span data-ttu-id="7e5f7-194">Utilizzando la terminologia di API, la postazione divano e la parte superiore alla parte posteriore del divano sono forme componenti e l'allineamento requisiti sono limitazioni dei componenti di forma.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-194">Using the APIs terminology, the couch seat and the top of the back of the couch are shape components and the alignment requirements are shape component constraints.</span></span>

<span data-ttu-id="7e5f7-195">Un esempio di query definita nell'esempio di Unity (**ShapeDefinition.cs**), per gli oggetti "sittable" è il seguente:</span><span class="sxs-lookup"><span data-stu-id="7e5f7-195">An example query defined in the Unity sample (**ShapeDefinition.cs**), for “sittable” objects is as follows:</span></span>




```
shapeComponents = new List<ShapeComponent>()
     {
          new ShapeComponent(
               new List<ShapeComponentConstraint>()
               {
                    ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
                    ShapeComponentConstraint.Create_SurfaceCount_Min(1),
                    ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
               }),
     };
     AddShape("Sittable", shapeComponents);
```

<span data-ttu-id="7e5f7-196">Ogni query shape è definita da un set di componenti di forma, ognuno con un set di limitazioni dei componenti e un set di vincoli di forma che elenca le dipendenze tra i componenti.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-196">Each shape query is defined by a set of shape components, each with a set of component constraints and a set of shape constraints which lists dependencies between the components.</span></span> <span data-ttu-id="7e5f7-197">Questo esempio include tre vincoli in una definizione di singoli componenti e senza vincoli di forme tra i componenti (perché è presente un solo componente).</span><span class="sxs-lookup"><span data-stu-id="7e5f7-197">This example includes three constraints in a single component definition and no shape constraints between components (as there is only one component).</span></span>

<span data-ttu-id="7e5f7-198">Al contrario, la forma divano presenta due componenti di forma e quattro i vincoli di forma.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-198">In contrast, the couch shape has two shape components and four shape constraints.</span></span> <span data-ttu-id="7e5f7-199">Si noti che i componenti vengono identificati tramite il relativo indice nell'elenco dei componenti dell'utente (0 e 1 in questo esempio).</span><span class="sxs-lookup"><span data-stu-id="7e5f7-199">Note that components are identified by their index in the user’s component list (0 and 1 in this example).</span></span>




```
shapeConstraints = new List<ShapeConstraint>()
        {
              ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
              ShapeConstraint.Create_RectanglesParallel(0, 1),
              ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
              ShapeConstraint.Create_AtBackOf(1, 0),
        };
```

<span data-ttu-id="7e5f7-200">Le funzioni wrapper vengono fornite nel modulo di Unity per la creazione di definizioni di forma personalizzata.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-200">Wrapper functions are provided in the Unity module for easy creation of custom shape definitions.</span></span> <span data-ttu-id="7e5f7-201">L'elenco completo dei vincoli di componente e la forma è reperibile nel **SpatialUnderstandingDll.cs** all'interno di **ShapeComponentConstraint** e il **ShapeConstraint** strutture.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-201">The full list of component and shape constraints can be found in **SpatialUnderstandingDll.cs** within the **ShapeComponentConstraint** and the **ShapeConstraint** structures.</span></span>

![Il rettangolo blu evidenzia i risultati della query shape chair.](images/chair-shape-query-500px.png)

<span data-ttu-id="7e5f7-203">Il rettangolo blu evidenzia i risultati della query shape chair.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-203">The blue rectangle highlights the results of the chair shape query.</span></span>



### <a name="object-placement-solver"></a><span data-ttu-id="7e5f7-204">Risolutore di selezione host per oggetto</span><span class="sxs-lookup"><span data-stu-id="7e5f7-204">Object placement solver</span></span>

<span data-ttu-id="7e5f7-205">Query di selezione host per oggetto è utilizzabile per identificare le posizioni ideale nella chat room fisica per posizionare gli oggetti.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-205">Object placement queries can be used to identify ideal locations in the physical room to place your objects.</span></span> <span data-ttu-id="7e5f7-206">Il Risolutore verrà indicata la posizione con mapping più appropriata data le regole di oggetti e i vincoli.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-206">The solver will find the best-fit location given the object rules and constraints.</span></span> <span data-ttu-id="7e5f7-207">Inoltre, le query di oggetto salvare in modo permanente fino a quando non viene rimosso l'oggetto con **Solver_RemoveObject** oppure **Solver_RemoveAllObjects** chiamate, consentendo vincolata selezione host per oggetti multipli.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-207">In addition, object queries persist until the object is removed with **Solver_RemoveObject** or **Solver_RemoveAllObjects** calls, allowing constrained multi-object placement.</span></span>

<span data-ttu-id="7e5f7-208">Query di selezione host di oggetto sono costituiti da tre parti: il tipo con parametri, un elenco di regole e un elenco di vincoli di posizionamento.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-208">Object placement queries consist of three parts: placement type with parameters, a list of rules, and a list of constraints.</span></span> <span data-ttu-id="7e5f7-209">Per eseguire una query, usare l'API seguente:</span><span class="sxs-lookup"><span data-stu-id="7e5f7-209">To run a query, use the following API:</span></span>




```
public static int Solver_PlaceObject(
                [In] string objectName,
                [In] IntPtr placementDefinition,    // ObjectPlacementDefinition
                [In] int placementRuleCount,
                [In] IntPtr placementRules,         // ObjectPlacementRule
                [In] int constraintCount,
                [In] IntPtr placementConstraints,   // ObjectPlacementConstraint
                [Out] IntPtr placementResult)
```
<span data-ttu-id="7e5f7-210">Questa funzione accetta un nome di oggetto, definizione di selezione host e un elenco delle regole e dei vincoli.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-210">This function takes an object name, placement definition, and a list of rules and constraints.</span></span> <span data-ttu-id="7e5f7-211">Il C# wrapper forniscono costruzione funzioni helper per facilitare la costruzione di regole e dei vincoli.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-211">The C# wrappers provide construction helper functions to make rule and constraint construction easy.</span></span> <span data-ttu-id="7e5f7-212">La definizione di selezione host contiene il tipo di query, vale a dire, uno dei seguenti:</span><span class="sxs-lookup"><span data-stu-id="7e5f7-212">The placement definition contains the query type — that is, one of the following:</span></span>




```
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

<span data-ttu-id="7e5f7-213">Ognuno dei tipi di selezione host dispone di un set di parametri univoci per il tipo.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-213">Each of the placement types has a set of parameters unique to the type.</span></span> <span data-ttu-id="7e5f7-214">Il **ObjectPlacementDefinition** struttura contiene un set di funzioni di supporto statici per la creazione di queste definizioni.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-214">The **ObjectPlacementDefinition** structure contains a set of static helper functions for creating these definitions.</span></span> <span data-ttu-id="7e5f7-215">Per trovare una posizione in cui inserire un oggetto nell'ambiente operativo, ad esempio, è possibile usare la funzione seguente:</span><span class="sxs-lookup"><span data-stu-id="7e5f7-215">For example, to find a place to put an object on the floor, you can use the following function:</span></span> 


```
public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims)
```

<span data-ttu-id="7e5f7-216">Oltre al tipo di selezione host, è possibile fornire un set di regole e i vincoli.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-216">In addition to the placement type, you can provide a set of rules and constraints.</span></span> <span data-ttu-id="7e5f7-217">Regole non possono essere violate.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-217">Rules cannot be violated.</span></span> <span data-ttu-id="7e5f7-218">Percorsi selezione host per possibili che soddisfano il tipo e le regole sono quindi ottimizzati a fronte del set di vincoli per selezionare il percorso di posizionamento ottimale.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-218">Possible placement locations that satisfy the type and rules are then optimized against the set of constraints to select the optimal placement location.</span></span> <span data-ttu-id="7e5f7-219">Ognuna delle regole e i vincoli può essere creata da funzioni di creazione statici specificato.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-219">Each of the rules and constraints can be created by the provided static creation functions.</span></span> <span data-ttu-id="7e5f7-220">Una funzione di costruzione regole e dei vincoli di esempio è disponibili sotto.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-220">An example rule and constraint construction function is provided below.</span></span>




```
public static ObjectPlacementRule Create_AwayFromPosition(
                    Vector3 position, float minDistance)
               public static ObjectPlacementConstraint Create_NearPoint(
                    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

<span data-ttu-id="7e5f7-221">La query di selezione host di oggetto seguente è alla ricerca di una posizione in cui inserire un misuratore metà cubo sul bordo di una superficie, da altra in precedenza posizionare gli oggetti e vicino al centro della chat room.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-221">The object placement query below is looking for a place to put a half meter cube on the edge of a surface, away from other previously place objects and near the center of the room.</span></span>




```
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

<span data-ttu-id="7e5f7-222">Se ha esito positivo, un **ObjectPlacementResult** struttura che contiene la posizione originale, dimensioni e orientamento viene restituita.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-222">If successful, an **ObjectPlacementResult** structure containing the placement position, dimensions and orientation is returned.</span></span> <span data-ttu-id="7e5f7-223">Inoltre, la selezione host viene aggiunto all'elenco interno della DLL di oggetti inseriti.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-223">In addition, the placement is added to the DLL’s internal list of placed objects.</span></span> <span data-ttu-id="7e5f7-224">Le query di selezione successiva dovrà tener conto di questo oggetto.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-224">Subsequent placement queries will take this object into account.</span></span> <span data-ttu-id="7e5f7-225">Il **LevelSolver.cs** file dell'esempio di Unity contiene più query di esempio.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-225">The **LevelSolver.cs** file in the Unity sample contains more example queries.</span></span>

![Le caselle blu mostrano il risultato da tre query unica posizione nel piano con le regole "distanza dalla posizione della fotocamera".](images/away-from-camera-position-500px.png)

<span data-ttu-id="7e5f7-227">Le caselle blu mostrano il risultato da tre query unica posizione nel piano con le regole "distanza dalla posizione della fotocamera".</span><span class="sxs-lookup"><span data-stu-id="7e5f7-227">The blue boxes show the result from three Place On Floor queries with "away from camera position" rules.</span></span>


<span data-ttu-id="7e5f7-228">**Suggerimenti:**</span><span class="sxs-lookup"><span data-stu-id="7e5f7-228">**Tips:**</span></span>
* <span data-ttu-id="7e5f7-229">Durante la risoluzione per il percorso di posizionamento di più oggetti necessari per uno scenario di applicazione o a un livello, risolvere innanzitutto oggetti grandi e indispensabili per ottimizzare la probabilità che può essere trovato uno spazio.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-229">When solving for placement location of multiple objects required for a level or application scenario, first solve indispensable and large objects to maximize the probability that a space can be found.</span></span>
* <span data-ttu-id="7e5f7-230">Ordine di inserimento è importante.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-230">Placement order is important.</span></span> <span data-ttu-id="7e5f7-231">Se selezioni host per oggetti non viene trovato, provare a configurazioni meno vincolate.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-231">If object placements cannot be found, try less constrained configurations.</span></span> <span data-ttu-id="7e5f7-232">Un set di configurazioni di fallback è fondamentale per la funzionalità di supporto in molte configurazioni di chat room.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-232">Having a set of fallback configurations is critical to supporting functionality across many room configurations.</span></span>

### <a name="ray-casting"></a><span data-ttu-id="7e5f7-233">Raggio cast</span><span class="sxs-lookup"><span data-stu-id="7e5f7-233">Ray casting</span></span>

<span data-ttu-id="7e5f7-234">Oltre ai tre query primaria, un'interfaccia di eseguire il cast di ray è utilizzabile per recuperare i tipi di area con tag e una rete mesh playspace stagni personalizzati possono essere copiate out dopo la chat è stata analizzata e finalizzata, le etichette vengono generate internamente, ad esempio le superfici di floor, ceiling e walls.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-234">In addition to the three primary queries, a ray casting interface can be used to retrieve tagged surface types and a custom watertight playspace mesh can be copied out After the room has been scanned and finalized, labels are internally generated for surfaces like the floor, ceiling, and walls.</span></span> <span data-ttu-id="7e5f7-235">Il **PlayspaceRaycast** funzione accetta un raggio e restituisce se il raggio è in conflitto con una superficie nota e in questo caso, informazioni che verranno visualizzati sotto forma di un **RaycastResult**.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-235">The **PlayspaceRaycast** function takes a ray and returns if the ray collides with a known surface and if so, information about that surface in the form of a **RaycastResult**.</span></span> 


```
struct RaycastResult
     {
          enum SurfaceTypes
          {
               Invalid, // No intersection
               Other,
               Floor,
               FloorLike,         // Not part of the floor topology, 
                                  //     but close to the floor and looks like the floor
               Platform,          // Horizontal platform between the ground and 
                                  //     the ceiling
               Ceiling,
               WallExternal,
               WallLike,          // Not part of the external wall surface, 
                                  //     but vertical surface that looks like a 
                                  //    wall structure
               };
               SurfaceTypes SurfaceType;
               float SurfaceArea;   // Zero if unknown 
                                        //  (i.e. if not part of the topology analysis)
               DirectX::XMFLOAT3 IntersectPoint;
               DirectX::XMFLOAT3 IntersectNormal;
     };
```

<span data-ttu-id="7e5f7-236">Internamente, viene calcolato il raycast contro la rappresentazione di voxel calcolata cm 8 al cubo del playspace.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-236">Internally, the raycast is computed against the computed 8cm cubed voxel representation of the playspace.</span></span> <span data-ttu-id="7e5f7-237">Ogni voxel contiene un set di elementi della superficie con i dati elaborati topologia (noto anche come surfels).</span><span class="sxs-lookup"><span data-stu-id="7e5f7-237">Each voxel contains a set of surface elements with processed topology data (also known as surfels).</span></span> <span data-ttu-id="7e5f7-238">Vengono confrontate le surfels contenute all'interno delle celle intersecate voxel e la migliore corrispondenza utilizzata per cercare le informazioni sulla topologia.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-238">The surfels contained within the intersected voxel cell are compared and the best match used to look up the topology information.</span></span> <span data-ttu-id="7e5f7-239">Data questa topologia contiene l'assegnazione di etichette restituiti sotto forma del **SurfaceTypes** enum, nonché la superficie dell'area di intersezione.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-239">This topology data contains the labeling returned in the form of the **SurfaceTypes** enum, as well as the surface area of the intersected surface.</span></span>

<span data-ttu-id="7e5f7-240">Nell'esempio di Unity, il cursore viene eseguito il cast un raggio ogni fotogramma.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-240">In the Unity sample, the cursor casts a ray each frame.</span></span> <span data-ttu-id="7e5f7-241">Prima di tutto rispetto colliders di Unity; in secondo luogo, sulla rappresentazione mondo del modulo understanding; e infine, gli elementi dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-241">First, against Unity’s colliders; second, against the understanding module’s world representation; and finally, against the UI elements.</span></span> <span data-ttu-id="7e5f7-242">In questa applicazione, dell'interfaccia utente ottiene priorità, quindi il risultato di comprensione e infine colliders di Unity.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-242">In this application, UI gets priority, then the understanding result, and finally, Unity’s colliders.</span></span> <span data-ttu-id="7e5f7-243">Il **SurfaceType** viene segnalato come testo accanto al cursore.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-243">The **SurfaceType** is reported as text next to the cursor.</span></span>

![Risultato Raycast reporting intersezione con la parte intera.](images/raycast-result-500px.jpg)

<span data-ttu-id="7e5f7-245">Risultato Raycast reporting intersezione con la parte intera.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-245">Raycast result reporting intersection with the floor.</span></span>


## <a name="get-the-code"></a><span data-ttu-id="7e5f7-246">Ottieni il codice</span><span class="sxs-lookup"><span data-stu-id="7e5f7-246">Get the code</span></span>

<span data-ttu-id="7e5f7-247">Il codice open source è disponibile nel [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity).</span><span class="sxs-lookup"><span data-stu-id="7e5f7-247">The open-source code is available in [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity).</span></span> <span data-ttu-id="7e5f7-248">Commenti nel [forum dedicati allo sviluppo di HoloLens](https://forums.hololens.com/) se si usa il codice in un progetto.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-248">Let us know on the [HoloLens Developer Forums](https://forums.hololens.com/) if you use the code in a project.</span></span> <span data-ttu-id="7e5f7-249">Siamo curiosi di vedere cosa fare con esso.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-249">We can't wait to see what you do with it!</span></span>

## <a name="about-the-author"></a><span data-ttu-id="7e5f7-250">Informazioni sull'autore</span><span class="sxs-lookup"><span data-stu-id="7e5f7-250">About the author</span></span>

<table style="border:0;width:800px">
<tr>
<td style="border:0"> <img alt="Jeff Evertt, Software Engineering Lead at Microsoft" width="200" height="205" src="images/jeff-evertt-200px.jpg" /></td><td style="border:0"> <span data-ttu-id="7e5f7-251"><b>Jeff Evertt</b> è un lead di ingegneria del software che ha lavorato su HoloLens sin dai tempi, dalla incubation per attività di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-251"><b>Jeff Evertt</b> is a software engineering lead who has worked on HoloLens since the early days, from incubation to experience development.</span></span> <span data-ttu-id="7e5f7-252">Prima di HoloLens, ha lavorato su Kinect il Xbox e nel settore dei giochi su una vasta gamma di piattaforme e giochi.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-252">Before HoloLens, he worked on the Xbox Kinect and in the games industry on a wide variety of platforms and games.</span></span> <span data-ttu-id="7e5f7-253">Jeff è passione per la robotica, grafica e cose con luci vistoso che vanno segnale acustico.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-253">Jeff is passionate about robotics, graphics, and things with flashy lights that go beep.</span></span> <span data-ttu-id="7e5f7-254">Ama imparare cose nuove e l'utilizzo del software, hardware e in particolare nello spazio in cui si intersecano le due.</span><span class="sxs-lookup"><span data-stu-id="7e5f7-254">He enjoys learning new things and working on software, hardware, and particularly in the space where the two intersect.</span></span></td>
</tr>
</table>



## <a name="see-also"></a><span data-ttu-id="7e5f7-255">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7e5f7-255">See also</span></span>
* [<span data-ttu-id="7e5f7-256">Mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="7e5f7-256">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="7e5f7-257">Progettazione di mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="7e5f7-257">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="7e5f7-258">Visualizzazione analisi chat room</span><span class="sxs-lookup"><span data-stu-id="7e5f7-258">Room scan visualization</span></span>](room-scan-visualization.md)
* [<span data-ttu-id="7e5f7-259">MixedRealityToolkit-Unity</span><span class="sxs-lookup"><span data-stu-id="7e5f7-259">MixedRealityToolkit-Unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="7e5f7-260">Asobo Studio: Lezioni dalla frontline dello sviluppo di HoloLens</span><span class="sxs-lookup"><span data-stu-id="7e5f7-260">Asobo Studio: Lessons from the frontline of HoloLens development</span></span>](http://www.gamesindustry.biz/articles/2016-05-12-asobo-lessons-from-the-frontline-of-ar-development)

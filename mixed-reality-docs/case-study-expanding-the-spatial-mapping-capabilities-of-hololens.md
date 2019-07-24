---
title: 'Case Study: espansione delle funzionalità di mapping spaziale di HoloLens'
description: Quando si creano le prime app per Microsoft HoloLens, siamo ansiosi di vedere come è possibile eseguire il push dei limiti del mapping spaziale sul dispositivo.
author: jevertt
ms.author: jevertt
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, HoloLens, mapping spaziale
ms.openlocfilehash: 602b629afa5900ff34c28b3a3a32725af06590b7
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522672"
---
# <a name="case-study---expanding-the-spatial-mapping-capabilities-of-hololens"></a><span data-ttu-id="300af-104">Case Study: espansione delle funzionalità di mapping spaziale di HoloLens</span><span class="sxs-lookup"><span data-stu-id="300af-104">Case study - Expanding the spatial mapping capabilities of HoloLens</span></span>

<span data-ttu-id="300af-105">Quando si creano le prime app per Microsoft HoloLens, siamo ansiosi di vedere come è possibile eseguire il push dei limiti del mapping spaziale sul dispositivo.</span><span class="sxs-lookup"><span data-stu-id="300af-105">When creating our first apps for Microsoft HoloLens, we were eager to see just how far we could push the boundaries of spatial mapping on the device.</span></span> <span data-ttu-id="300af-106">Jeff Evertt, un ingegnere del software presso Microsoft Studios, spiega come una nuova tecnologia è stata sviluppata dalla necessità di un maggiore controllo sulla modalità di inserimento degli ologrammi nell'ambiente reale di un utente.</span><span class="sxs-lookup"><span data-stu-id="300af-106">Jeff Evertt, a software engineer at Microsoft Studios, explains how a new technology was developed out of the need for more control over how holograms are placed in a user's real-world environment.</span></span>

## <a name="watch-the-video"></a><span data-ttu-id="300af-107">Guarda il video</span><span class="sxs-lookup"><span data-stu-id="300af-107">Watch the video</span></span>

>[!VIDEO https://www.youtube.com/embed/iUmTi3_Ynus]

## <a name="beyond-spatial-mapping"></a><span data-ttu-id="300af-108">Oltre il mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="300af-108">Beyond spatial mapping</span></span>

<span data-ttu-id="300af-109">Mentre stavamo lavorando per i [frammenti](https://www.microsoft.com/p/fragments/9nblggh5ggm8) e i [Conker giovani](https://www.microsoft.com/p/young-conker/9nblggh5ggk1), due dei primi giochi per HoloLens, abbiamo scoperto che, quando avessimo eseguito il posizionamento procedurale degli ologrammi nel mondo fisico, abbiamo bisogno di un livello superiore di comprensione degli utenti ambiente.</span><span class="sxs-lookup"><span data-stu-id="300af-109">While we were working on [Fragments](https://www.microsoft.com/p/fragments/9nblggh5ggm8) and [Young Conker](https://www.microsoft.com/p/young-conker/9nblggh5ggk1), two of the first games for HoloLens, we found that when we were doing procedural placement of holograms in the physical world, we needed a higher level of understanding about the user's environment.</span></span> <span data-ttu-id="300af-110">Ogni gioco ha esigenze specifiche di selezione host: Nei frammenti, ad esempio, si voleva essere in grado di distinguere tra superfici diverse, ad esempio il piano o una tabella, per inserire gli indizi nelle posizioni pertinenti.</span><span class="sxs-lookup"><span data-stu-id="300af-110">Each game had its own specific placement needs: In Fragments, for example, we wanted to be able to distinguish between different surfaces—such as the floor or a table—to place clues in relevant locations.</span></span> <span data-ttu-id="300af-111">Volevamo anche essere in grado di identificare le superfici su cui potevano poggiare i caratteri olografici di dimensioni reali, ad esempio un divano o una poltrona.</span><span class="sxs-lookup"><span data-stu-id="300af-111">We also wanted to be able to identify surfaces that life-size holographic characters could sit on, such as a couch or a chair.</span></span> <span data-ttu-id="300af-112">In Young Conker volevamo che Conker e i suoi avversari fossero in grado di usare le superfici sollevate nella stanza di un giocatore come piattaforme.</span><span class="sxs-lookup"><span data-stu-id="300af-112">In Young Conker, we wanted Conker and his opponents to be able to use raised surfaces in a player's room as platforms.</span></span>

<span data-ttu-id="300af-113">[Asobo Studios](http://www.asobostudio.com/index.html), il nostro partner di sviluppo per questi giochi, ha affrontato questo problema e ha creato una tecnologia che estende le funzionalità di mapping spaziale di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="300af-113">[Asobo Studios](http://www.asobostudio.com/index.html), our development partner for these games, faced this problem head-on and created a technology that extends the spatial mapping capabilities of HoloLens.</span></span> <span data-ttu-id="300af-114">In questo modo è possibile analizzare la stanza di un giocatore e identificare superfici quali muri, tabelle, poltrone e pavimenti.</span><span class="sxs-lookup"><span data-stu-id="300af-114">Using this, we could analyze a player's room and identify surfaces such as walls, tables, chairs, and floors.</span></span> <span data-ttu-id="300af-115">Inoltre, ci ha consentito di ottimizzare il rispetto di un set di vincoli per determinare la posizione migliore per gli oggetti olografici.</span><span class="sxs-lookup"><span data-stu-id="300af-115">It also gave us the ability to optimize against a set of constraints to determine the best placement for holographic objects.</span></span>

## <a name="the-spatial-understanding-code"></a><span data-ttu-id="300af-116">Codice di conoscenza spaziale</span><span class="sxs-lookup"><span data-stu-id="300af-116">The spatial understanding code</span></span>

<span data-ttu-id="300af-117">Abbiamo preso il codice originale di Asobo e abbiamo creato una libreria che incapsula questa tecnologia.</span><span class="sxs-lookup"><span data-stu-id="300af-117">We took Asobo's original code and created a library that encapsulates this technology.</span></span> <span data-ttu-id="300af-118">Microsoft e Asobo hanno ora aperto questo codice e reso disponibile in [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) per poterlo usare nei propri progetti.</span><span class="sxs-lookup"><span data-stu-id="300af-118">Microsoft and Asobo have now open-sourced this code and made it available on [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) for you to use in your own projects.</span></span> <span data-ttu-id="300af-119">Tutto il codice sorgente è incluso, consentendo di personalizzarlo in base alle proprie esigenze e condividere i miglioramenti con la community.</span><span class="sxs-lookup"><span data-stu-id="300af-119">All the source code is included, allowing you to customize it to your needs and share your improvements with the community.</span></span> <span data-ttu-id="300af-120">Il codice per il C++ Risolutore è stato sottoposto a incapsulamento in una DLL di UWP ed esposto a Unity con una soluzione di [riepilogo a discesa contenuta in MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding).</span><span class="sxs-lookup"><span data-stu-id="300af-120">The code for the C++ solver has been wrapped into a UWP DLL and exposed to Unity with a [drop-in prefab contained within MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding).</span></span>

<span data-ttu-id="300af-121">Nell'esempio Unity sono disponibili numerose query utili che consentono di trovare spazi vuoti sulle pareti, posizionare oggetti sul soffitto o spazi di grandi dimensioni, identificare le posizioni dei caratteri e una miriade di altre query di comprensione spaziale.</span><span class="sxs-lookup"><span data-stu-id="300af-121">There are many useful queries included in the Unity sample that will allow you to find empty spaces on walls, place objects on the ceiling or on large spaces on the floor, identify places for characters to sit, and a myriad of other spatial understanding queries.</span></span>

<span data-ttu-id="300af-122">Sebbene la soluzione di mapping spaziale fornita da HoloLens sia progettata per essere sufficientemente generica per soddisfare le esigenze dell'intera gamma di spazi di problemi, il modulo di comprensione spaziale è stato creato per supportare le esigenze di due giochi specifici.</span><span class="sxs-lookup"><span data-stu-id="300af-122">While the spatial mapping solution provided by HoloLens is designed to be generic enough to meet the needs of the entire gamut of problem spaces, the spatial understanding module was built to support the needs of two specific games.</span></span> <span data-ttu-id="300af-123">In questo modo, la soluzione è strutturata in base a un processo e a un set di presupposti specifici:</span><span class="sxs-lookup"><span data-stu-id="300af-123">As such, its solution is structured around a specific process and set of assumptions:</span></span>
* <span data-ttu-id="300af-124">**Playspace a dimensione fissa**: L'utente specifica le dimensioni massime di playspace nella chiamata init.</span><span class="sxs-lookup"><span data-stu-id="300af-124">**Fixed size playspace**: The user specifies the maximum playspace size in the init call.</span></span>
* <span data-ttu-id="300af-125">**Processo di analisi**monouso: Il processo richiede una fase di analisi discreta in cui l'utente si aggira, definendo la playspace.</span><span class="sxs-lookup"><span data-stu-id="300af-125">**One-time scan process**: The process requires a discrete scanning phase where the user walks around, defining the playspace.</span></span> <span data-ttu-id="300af-126">Le funzioni di query non funzioneranno finché non sarà stata completata l'analisi.</span><span class="sxs-lookup"><span data-stu-id="300af-126">Query functions will not function until after the scan has been finalized.</span></span>
* <span data-ttu-id="300af-127">**"Disegno" di playspace basato sull'utente**: Durante la fase di analisi, l'utente sposta ed esamina la playspace, disegnando in modo efficace le aree che devono essere incluse.</span><span class="sxs-lookup"><span data-stu-id="300af-127">**User driven playspace “painting”**: During the scanning phase, the user moves and looks around the playspace, effectively painting the areas which should be included.</span></span> <span data-ttu-id="300af-128">La mesh generata è importante per fornire commenti e suggerimenti degli utenti durante questa fase.</span><span class="sxs-lookup"><span data-stu-id="300af-128">The generated mesh is important to provide user feedback during this phase.</span></span>
* <span data-ttu-id="300af-129">**Installazione domestica o di Office**: Le funzioni di query sono progettate intorno ad aree piane e muri a angoli retti.</span><span class="sxs-lookup"><span data-stu-id="300af-129">**Indoors home or office setup**: The query functions are designed around flat surfaces and walls at right angles.</span></span> <span data-ttu-id="300af-130">Si tratta di una limitazione flessibile.</span><span class="sxs-lookup"><span data-stu-id="300af-130">This is a soft limitation.</span></span> <span data-ttu-id="300af-131">Tuttavia, durante la fase di analisi, viene completata un'analisi dell'asse primaria per ottimizzare lo schema a mosaico mesh lungo l'asse principale e secondario.</span><span class="sxs-lookup"><span data-stu-id="300af-131">However, during the scanning phase, a primary axis analysis is completed to optimize the mesh tessellation along major and minor axis.</span></span>

### <a name="room-scanning-process"></a><span data-ttu-id="300af-132">Processo di analisi chat room</span><span class="sxs-lookup"><span data-stu-id="300af-132">Room Scanning Process</span></span>

<span data-ttu-id="300af-133">Quando si carica il modulo di conoscenza spaziale, la prima cosa da fare è analizzare lo spazio, in modo che tutte le superfici utilizzabili, ad esempio la pavimentazione, il soffitto e le pareti, siano identificate e con etichetta.</span><span class="sxs-lookup"><span data-stu-id="300af-133">When you load the spatial understanding module, the first thing you'll do is scan your space, so all the usable surfaces—such as the floor, ceiling, and walls—are identified and labeled.</span></span> <span data-ttu-id="300af-134">Durante il processo di analisi, è possibile esaminare la stanza e "dipingere" le aree da includere nell'analisi.</span><span class="sxs-lookup"><span data-stu-id="300af-134">During the scanning process, you look around your room and "paint' the areas that should be included in the scan.</span></span>

<span data-ttu-id="300af-135">La mesh rilevata durante questa fase è una parte importante del feedback visivo che consente agli utenti di sapere quali parti della stanza vengono analizzate.</span><span class="sxs-lookup"><span data-stu-id="300af-135">The mesh seen during this phase is an important piece of visual feedback that lets users know what parts of the room are being scanned.</span></span> <span data-ttu-id="300af-136">La DLL per il modulo di informazioni spaziali archivia internamente playspace come griglia di cubi voxel di dimensioni di 8 cm.</span><span class="sxs-lookup"><span data-stu-id="300af-136">The DLL for the spatial understanding module internally stores the playspace as a grid of 8cm sized voxel cubes.</span></span> <span data-ttu-id="300af-137">Durante la fase iniziale di analisi, viene completata un'analisi del componente principale per determinare gli assi della stanza.</span><span class="sxs-lookup"><span data-stu-id="300af-137">During the initial part of scanning, a primary component analysis is completed to determine the axes of the room.</span></span> <span data-ttu-id="300af-138">Internamente, archivia lo spazio voxel allineato a questi assi.</span><span class="sxs-lookup"><span data-stu-id="300af-138">Internally, it stores its voxel space aligned to these axes.</span></span> <span data-ttu-id="300af-139">Una mesh viene generata approssimativamente ogni secondo estraendo oggetto isosurface dal volume voxel.</span><span class="sxs-lookup"><span data-stu-id="300af-139">A mesh is generated approximately every second by extracting the isosurface from the voxel volume.</span></span>

![Mapping spaziale mesh in bianco e informazioni su playspace mesh in verde](images/spatial-mapping-500px.png)

<span data-ttu-id="300af-141">Mapping spaziale mesh in bianco e informazioni su playspace mesh in verde</span><span class="sxs-lookup"><span data-stu-id="300af-141">Spatial mapping mesh in white and understanding playspace mesh in green</span></span>



<span data-ttu-id="300af-142">Il file SpatialUnderstanding.cs incluso gestisce il processo della fase di analisi.</span><span class="sxs-lookup"><span data-stu-id="300af-142">The included SpatialUnderstanding.cs file manages the scanning phase process.</span></span> <span data-ttu-id="300af-143">Chiama le funzioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="300af-143">It calls the following functions:</span></span>
* <span data-ttu-id="300af-144">**SpatialUnderstanding_Init**: Chiamato una volta all'inizio.</span><span class="sxs-lookup"><span data-stu-id="300af-144">**SpatialUnderstanding_Init**: Called once at the start.</span></span>
* <span data-ttu-id="300af-145">**GeneratePlayspace_InitScan**: Indica che deve iniziare la fase di analisi.</span><span class="sxs-lookup"><span data-stu-id="300af-145">**GeneratePlayspace_InitScan**: Indicates that the scan phase should begin.</span></span>
* <span data-ttu-id="300af-146">**GeneratePlayspace_UpdateScan_DynamicScan**: Chiamato ogni frame per aggiornare il processo di analisi.</span><span class="sxs-lookup"><span data-stu-id="300af-146">**GeneratePlayspace_UpdateScan_DynamicScan**: Called each frame to update the scanning process.</span></span> <span data-ttu-id="300af-147">La posizione e l'orientamento della fotocamera vengono passati e usati per il processo di disegno playspace, descritto in precedenza.</span><span class="sxs-lookup"><span data-stu-id="300af-147">The camera position and orientation is passed in and is used for the playspace painting process, described above.</span></span>
* <span data-ttu-id="300af-148">**GeneratePlayspace_RequestFinish**: Chiamato per finalizzare playspace.</span><span class="sxs-lookup"><span data-stu-id="300af-148">**GeneratePlayspace_RequestFinish**: Called to finalize the playspace.</span></span> <span data-ttu-id="300af-149">Questa operazione utilizzerà le aree "dipinte" durante la fase di analisi per definire e bloccare il playspace.</span><span class="sxs-lookup"><span data-stu-id="300af-149">This will use the areas “painted” during the scan phase to define and lock the playspace.</span></span> <span data-ttu-id="300af-150">L'applicazione può eseguire query sulle statistiche durante la fase di analisi, nonché eseguire query sulla mesh personalizzata per fornire commenti e suggerimenti degli utenti.</span><span class="sxs-lookup"><span data-stu-id="300af-150">The application can query statistics during the scanning phase as well as query the custom mesh for providing user feedback.</span></span>
* <span data-ttu-id="300af-151">**Import_UnderstandingMesh**: Durante l'analisi, il comportamento di **SpatialUnderstandingCustomMesh** fornito dal modulo e inserito nella prefabbricazione di comprensione eseguirà periodicamente una query sulla mesh personalizzata generata dal processo.</span><span class="sxs-lookup"><span data-stu-id="300af-151">**Import_UnderstandingMesh**: During scanning, the **SpatialUnderstandingCustomMesh** behavior provided by the module and placed on the understanding prefab will periodically query the custom mesh generated by the process.</span></span> <span data-ttu-id="300af-152">Inoltre, questa operazione viene eseguita ancora una volta dopo la finalizzazione dell'analisi.</span><span class="sxs-lookup"><span data-stu-id="300af-152">In addition, this is done once more after scanning has been finalized.</span></span>

<span data-ttu-id="300af-153">Il flusso di analisi, determinato dal comportamento **SpatialUnderstanding** , chiama **InitScan**e quindi **UpdateScan** ogni frame.</span><span class="sxs-lookup"><span data-stu-id="300af-153">The scanning flow, driven by the **SpatialUnderstanding** behavior calls **InitScan**, then **UpdateScan** each frame.</span></span> <span data-ttu-id="300af-154">Quando la query Statistics segnala una ragionevole copertura, l'utente può AirTap chiamare **RequestFinish** per indicare la fine della fase di analisi.</span><span class="sxs-lookup"><span data-stu-id="300af-154">When the statistics query reports reasonable coverage, the user can airtap to call **RequestFinish** to indicate the end of the scanning phase.</span></span> <span data-ttu-id="300af-155">**UpdateScan** continua a essere chiamato fino a quando non viene restituito il valore indica che l'elaborazione della dll è stata completata.</span><span class="sxs-lookup"><span data-stu-id="300af-155">**UpdateScan** continues to be called until it’s return value indicates that the DLL has completed processing.</span></span>

## <a name="the-queries"></a><span data-ttu-id="300af-156">Query</span><span class="sxs-lookup"><span data-stu-id="300af-156">The queries</span></span>

<span data-ttu-id="300af-157">Una volta completata l'analisi, sarà possibile accedere a tre tipi diversi di query nell'interfaccia:</span><span class="sxs-lookup"><span data-stu-id="300af-157">Once the scan is complete, you'll be able to access three different types of queries in the interface:</span></span>
* <span data-ttu-id="300af-158">**Query topologia**: Si tratta di query veloci basate sulla topologia della stanza sottoposta a scansione.</span><span class="sxs-lookup"><span data-stu-id="300af-158">**Topology queries**: These are fast queries that are based on the topology of the scanned room.</span></span>
* <span data-ttu-id="300af-159">**Query di forma**: Questi utilizzano i risultati delle query della topologia per trovare superfici orizzontali che corrispondono a forme personalizzate definite dall'utente.</span><span class="sxs-lookup"><span data-stu-id="300af-159">**Shape queries**: These utilize the results of your topology queries to find horizontal surfaces that are a good match to custom shapes that you define.</span></span>
* <span data-ttu-id="300af-160">**Query posizionamento oggetti**: Si tratta di query più complesse che individuano la posizione più adatta in base a un set di regole e vincoli per l'oggetto.</span><span class="sxs-lookup"><span data-stu-id="300af-160">**Object placement queries**: These are more complex queries that find the best-fit location based on a set of rules and constraints for the object.</span></span>

<span data-ttu-id="300af-161">Oltre alle tre query primarie, è disponibile un'interfaccia Raycasting che può essere usata per recuperare i tipi di superficie con tag e una mesh della stanza stermetica personalizzata che può essere copiata.</span><span class="sxs-lookup"><span data-stu-id="300af-161">In addition to the three primary queries, there is a raycasting interface which can be used to retrieve tagged surface types and a custom watertight room mesh can be copied out.</span></span>

### <a name="topology-queries"></a><span data-ttu-id="300af-162">Query sulla topologia</span><span class="sxs-lookup"><span data-stu-id="300af-162">Topology queries</span></span>

<span data-ttu-id="300af-163">All'interno della DLL, Gestione topologia gestisce l'assegnazione di etichette all'ambiente.</span><span class="sxs-lookup"><span data-stu-id="300af-163">Within the DLL, the topology manager handles labeling of the environment.</span></span> <span data-ttu-id="300af-164">Come indicato in precedenza, gran parte dei dati viene archiviata in surfels, che sono contenuti in un volume voxel.</span><span class="sxs-lookup"><span data-stu-id="300af-164">As mentioned above, much of the data is stored within surfels, which are contained within a voxel volume.</span></span> <span data-ttu-id="300af-165">Inoltre, la struttura **PlaySpaceInfos** viene utilizzata per archiviare le informazioni relative a playspace, incluso l'allineamento internazionale (altri dettagli su questo sotto), il piano e l'altezza del soffitto.</span><span class="sxs-lookup"><span data-stu-id="300af-165">In addition, the **PlaySpaceInfos** structure is used to store information about the playspace, including the world alignment (more details on this below), floor, and ceiling height.</span></span>

<span data-ttu-id="300af-166">Vengono usate le regole euristiche per determinare il piano, il soffitto e i muri.</span><span class="sxs-lookup"><span data-stu-id="300af-166">Heuristics are used for determining floor, ceiling, and walls.</span></span> <span data-ttu-id="300af-167">Ad esempio, la superficie orizzontale più grande e più bassa con una superficie di attacco maggiore di 1 m2 viene considerata il piano.</span><span class="sxs-lookup"><span data-stu-id="300af-167">For example, the largest and lowest horizontal surface with greater than 1 m2 surface area is considered the floor.</span></span> <span data-ttu-id="300af-168">Si noti che in questo processo viene usato anche il percorso della fotocamera durante il processo di analisi.</span><span class="sxs-lookup"><span data-stu-id="300af-168">Note that the camera path during the scanning process is also used in this process.</span></span>

<span data-ttu-id="300af-169">Un subset delle query esposte dal gestore della topologia viene esposto tramite la DLL.</span><span class="sxs-lookup"><span data-stu-id="300af-169">A subset of the queries exposed by the Topology manager are exposed out through the DLL.</span></span> <span data-ttu-id="300af-170">Le query di topologia esposte sono le seguenti:</span><span class="sxs-lookup"><span data-stu-id="300af-170">The exposed topology queries are as follows:</span></span>
* <span data-ttu-id="300af-171">QueryTopology_FindPositionsOnWalls</span><span class="sxs-lookup"><span data-stu-id="300af-171">QueryTopology_FindPositionsOnWalls</span></span>
* <span data-ttu-id="300af-172">QueryTopology_FindLargePositionsOnWalls</span><span class="sxs-lookup"><span data-stu-id="300af-172">QueryTopology_FindLargePositionsOnWalls</span></span>
* <span data-ttu-id="300af-173">QueryTopology_FindLargestWall</span><span class="sxs-lookup"><span data-stu-id="300af-173">QueryTopology_FindLargestWall</span></span>
* <span data-ttu-id="300af-174">QueryTopology_FindPositionsOnFloor</span><span class="sxs-lookup"><span data-stu-id="300af-174">QueryTopology_FindPositionsOnFloor</span></span>
* <span data-ttu-id="300af-175">QueryTopology_FindLargestPositionsOnFloor</span><span class="sxs-lookup"><span data-stu-id="300af-175">QueryTopology_FindLargestPositionsOnFloor</span></span>
* <span data-ttu-id="300af-176">QueryTopology_FindPositionsSittable</span><span class="sxs-lookup"><span data-stu-id="300af-176">QueryTopology_FindPositionsSittable</span></span>

<span data-ttu-id="300af-177">Ogni query ha un set di parametri, specifico del tipo di query.</span><span class="sxs-lookup"><span data-stu-id="300af-177">Each of the queries has a set of parameters, specific to the query type.</span></span> <span data-ttu-id="300af-178">Nell'esempio seguente l'utente specifica l'altezza minima & larghezza del volume desiderato, l'altezza minima di posizionamento sopra il piano e la quantità minima di spazio di autorizzazione davanti al volume.</span><span class="sxs-lookup"><span data-stu-id="300af-178">In the following example, the user specifies the minimum height & width of the desired volume, minimum placement height above the floor, and the minimum amount of clearance in front of the volume.</span></span> <span data-ttu-id="300af-179">Tutte le misurazioni sono in metri.</span><span class="sxs-lookup"><span data-stu-id="300af-179">All measurements are in meters.</span></span>




```
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
          _In_ float minHeightOfWallSpace,
          _In_ float minWidthOfWallSpace,
          _In_ float minHeightAboveFloor,
          _In_ float minFacingClearance,
          _In_ int locationCount,
          _Inout_ Dll_Interface::TopologyResult* locationData)
```

<span data-ttu-id="300af-180">Ognuna di queste query accetta una matrice pre-allocata di strutture **TopologyResult** .</span><span class="sxs-lookup"><span data-stu-id="300af-180">Each of these queries takes a pre-allocated array of **TopologyResult** structures.</span></span> <span data-ttu-id="300af-181">Il parametro **locationCount** specifica la lunghezza della matrice passata.</span><span class="sxs-lookup"><span data-stu-id="300af-181">The **locationCount** parameter specifies the length of the passed-in array.</span></span> <span data-ttu-id="300af-182">Il valore restituito indica il numero di posizioni restituite.</span><span class="sxs-lookup"><span data-stu-id="300af-182">The return value reports the number of returned locations.</span></span> <span data-ttu-id="300af-183">Questo numero non è mai superiore al parametro **locationCount** passato.</span><span class="sxs-lookup"><span data-stu-id="300af-183">This number is never greater than the passed-in **locationCount** parameter.</span></span>

<span data-ttu-id="300af-184">Il **TopologyResult** contiene la posizione centrale del volume restituito, la direzione (ovvero normale) e le dimensioni dello spazio trovato.</span><span class="sxs-lookup"><span data-stu-id="300af-184">The **TopologyResult** contains the center position of the returned volume, the facing direction (i.e. normal), and the dimensions of the found space.</span></span>




```
struct TopologyResult
     {
          DirectX::XMFLOAT3 position;
          DirectX::XMFLOAT3 normal;
          float width;
          float length;
     };
```

<span data-ttu-id="300af-185">Si noti che nell'esempio Unity ogni query è collegata a un pulsante nel pannello dell'interfaccia utente virtuale.</span><span class="sxs-lookup"><span data-stu-id="300af-185">Note that in the Unity sample, each of these queries is linked up to a button in the virtual UI panel.</span></span> <span data-ttu-id="300af-186">L'esempio codifica in modo rigido i parametri per ognuna di queste query in valori ragionevoli.</span><span class="sxs-lookup"><span data-stu-id="300af-186">The sample hard codes the parameters for each of these queries to reasonable values.</span></span> <span data-ttu-id="300af-187">Per altri esempi, vedere *SpaceVisualizer.cs* nel codice di esempio.</span><span class="sxs-lookup"><span data-stu-id="300af-187">See *SpaceVisualizer.cs* in the sample code for more examples.</span></span>

### <a name="shape-queries"></a><span data-ttu-id="300af-188">Query di forma</span><span class="sxs-lookup"><span data-stu-id="300af-188">Shape queries</span></span>

<span data-ttu-id="300af-189">All'interno della DLL, l'analizzatore di forme (**ShapeAnalyzer_W**) utilizza l'analizzatore della topologia per trovare la corrispondenza con le forme personalizzate definite dall'utente.</span><span class="sxs-lookup"><span data-stu-id="300af-189">Inside of the DLL, the shape analyzer (**ShapeAnalyzer_W**) uses the topology analyzer to match against custom shapes defined by the user.</span></span> <span data-ttu-id="300af-190">Nell'esempio Unity è disponibile un set predefinito di forme, visualizzate nel menu query, nella scheda forma.</span><span class="sxs-lookup"><span data-stu-id="300af-190">The Unity sample has a pre-defined set of shapes which are shown in the query menu, on the shape tab.</span></span>

<span data-ttu-id="300af-191">Si noti che l'analisi delle forme funziona solo su superfici orizzontali.</span><span class="sxs-lookup"><span data-stu-id="300af-191">Note that the shape analysis works on horizontal surfaces only.</span></span> <span data-ttu-id="300af-192">Un divano, ad esempio, viene definito dalla superficie della postazione piatta e dalla parte superiore piatta del divano.</span><span class="sxs-lookup"><span data-stu-id="300af-192">A couch, for example, is defined by the flat seat surface and the flat top of the couch back.</span></span> <span data-ttu-id="300af-193">La query Shape cerca due superfici di dimensioni, altezze e intervalli di aspetto specifici, con le due superfici allineate e connesse.</span><span class="sxs-lookup"><span data-stu-id="300af-193">The shape query looks for two surfaces of a specific size, height, and aspect range, with the two surfaces aligned and connected.</span></span> <span data-ttu-id="300af-194">Utilizzando la terminologia relativa alle API, la poltrona e la parte superiore della parte posteriore del divano sono componenti di forma e i requisiti di allineamento sono vincoli dei componenti di forma.</span><span class="sxs-lookup"><span data-stu-id="300af-194">Using the APIs terminology, the couch seat and the top of the back of the couch are shape components and the alignment requirements are shape component constraints.</span></span>

<span data-ttu-id="300af-195">Una query di esempio definita nell'esempio Unity (**ShapeDefinition.cs**) per gli oggetti "SitTable" è la seguente:</span><span class="sxs-lookup"><span data-stu-id="300af-195">An example query defined in the Unity sample (**ShapeDefinition.cs**), for “sittable” objects is as follows:</span></span>




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

<span data-ttu-id="300af-196">Ogni query di forma è definita da un set di componenti di forma, ognuno con un set di vincoli di componente e un set di vincoli di forma che elenca le dipendenze tra i componenti.</span><span class="sxs-lookup"><span data-stu-id="300af-196">Each shape query is defined by a set of shape components, each with a set of component constraints and a set of shape constraints which lists dependencies between the components.</span></span> <span data-ttu-id="300af-197">Questo esempio include tre vincoli in una definizione di componente singolo e nessun vincolo di forma tra i componenti (in quanto è presente un solo componente).</span><span class="sxs-lookup"><span data-stu-id="300af-197">This example includes three constraints in a single component definition and no shape constraints between components (as there is only one component).</span></span>

<span data-ttu-id="300af-198">Al contrario, la forma Couch presenta due componenti di forma e quattro vincoli Shape.</span><span class="sxs-lookup"><span data-stu-id="300af-198">In contrast, the couch shape has two shape components and four shape constraints.</span></span> <span data-ttu-id="300af-199">Si noti che i componenti sono identificati dal relativo indice nell'elenco dei componenti dell'utente (0 e 1 in questo esempio).</span><span class="sxs-lookup"><span data-stu-id="300af-199">Note that components are identified by their index in the user’s component list (0 and 1 in this example).</span></span>




```
shapeConstraints = new List<ShapeConstraint>()
        {
              ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
              ShapeConstraint.Create_RectanglesParallel(0, 1),
              ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
              ShapeConstraint.Create_AtBackOf(1, 0),
        };
```

<span data-ttu-id="300af-200">Le funzioni wrapper sono disponibili nel modulo Unity per semplificare la creazione di definizioni di forme personalizzate.</span><span class="sxs-lookup"><span data-stu-id="300af-200">Wrapper functions are provided in the Unity module for easy creation of custom shape definitions.</span></span> <span data-ttu-id="300af-201">L'elenco completo dei vincoli relativi ai componenti e alle forme è disponibile in **SpatialUnderstandingDll.cs** all'interno delle strutture **ShapeComponentConstraint** e **ShapeConstraint** .</span><span class="sxs-lookup"><span data-stu-id="300af-201">The full list of component and shape constraints can be found in **SpatialUnderstandingDll.cs** within the **ShapeComponentConstraint** and the **ShapeConstraint** structures.</span></span>

![Il rettangolo blu evidenzia i risultati della query della forma Chair.](images/chair-shape-query-500px.png)

<span data-ttu-id="300af-203">Il rettangolo blu evidenzia i risultati della query della forma Chair.</span><span class="sxs-lookup"><span data-stu-id="300af-203">The blue rectangle highlights the results of the chair shape query.</span></span>



### <a name="object-placement-solver"></a><span data-ttu-id="300af-204">Risolutore posizionamento oggetti</span><span class="sxs-lookup"><span data-stu-id="300af-204">Object placement solver</span></span>

<span data-ttu-id="300af-205">È possibile usare le query di posizionamento degli oggetti per identificare le posizioni ideali nella stanza fisica per inserire gli oggetti.</span><span class="sxs-lookup"><span data-stu-id="300af-205">Object placement queries can be used to identify ideal locations in the physical room to place your objects.</span></span> <span data-ttu-id="300af-206">Il Risolutore troverà la posizione più adatta in base alle regole e ai vincoli dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="300af-206">The solver will find the best-fit location given the object rules and constraints.</span></span> <span data-ttu-id="300af-207">Inoltre, le query di oggetto vengono mantenute fino a quando l'oggetto non viene rimosso con le chiamate a **Solver_RemoveObject** o **Solver_RemoveAllObjects** , consentendo il posizionamento multioggetto vincolato.</span><span class="sxs-lookup"><span data-stu-id="300af-207">In addition, object queries persist until the object is removed with **Solver_RemoveObject** or **Solver_RemoveAllObjects** calls, allowing constrained multi-object placement.</span></span>

<span data-ttu-id="300af-208">Le query di posizionamento degli oggetti sono costituite da tre parti: tipo di posizionamento con parametri, un elenco di regole e un elenco di vincoli.</span><span class="sxs-lookup"><span data-stu-id="300af-208">Object placement queries consist of three parts: placement type with parameters, a list of rules, and a list of constraints.</span></span> <span data-ttu-id="300af-209">Per eseguire una query, usare l'API seguente:</span><span class="sxs-lookup"><span data-stu-id="300af-209">To run a query, use the following API:</span></span>




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
<span data-ttu-id="300af-210">Questa funzione accetta un nome di oggetto, una definizione di selezione host e un elenco di regole e vincoli.</span><span class="sxs-lookup"><span data-stu-id="300af-210">This function takes an object name, placement definition, and a list of rules and constraints.</span></span> <span data-ttu-id="300af-211">I C# wrapper forniscono funzioni di supporto per la costruzione per semplificare la costruzione di regole e vincoli.</span><span class="sxs-lookup"><span data-stu-id="300af-211">The C# wrappers provide construction helper functions to make rule and constraint construction easy.</span></span> <span data-ttu-id="300af-212">La definizione di selezione host contiene il tipo di query, ovvero uno dei seguenti:</span><span class="sxs-lookup"><span data-stu-id="300af-212">The placement definition contains the query type — that is, one of the following:</span></span>




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

<span data-ttu-id="300af-213">Ognuno dei tipi di posizionamento dispone di un set di parametri univoco per il tipo.</span><span class="sxs-lookup"><span data-stu-id="300af-213">Each of the placement types has a set of parameters unique to the type.</span></span> <span data-ttu-id="300af-214">La struttura **ObjectPlacementDefinition** contiene un set di funzioni di supporto statiche per la creazione di queste definizioni.</span><span class="sxs-lookup"><span data-stu-id="300af-214">The **ObjectPlacementDefinition** structure contains a set of static helper functions for creating these definitions.</span></span> <span data-ttu-id="300af-215">Ad esempio, per trovare una posizione in cui inserire un oggetto a terra, è possibile usare la funzione seguente:</span><span class="sxs-lookup"><span data-stu-id="300af-215">For example, to find a place to put an object on the floor, you can use the following function:</span></span> 


```
public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims)
```

<span data-ttu-id="300af-216">Oltre al tipo di posizionamento, è possibile specificare un set di regole e vincoli.</span><span class="sxs-lookup"><span data-stu-id="300af-216">In addition to the placement type, you can provide a set of rules and constraints.</span></span> <span data-ttu-id="300af-217">Impossibile violare le regole.</span><span class="sxs-lookup"><span data-stu-id="300af-217">Rules cannot be violated.</span></span> <span data-ttu-id="300af-218">Le posizioni di posizionamento possibili che soddisfano il tipo e le regole vengono quindi ottimizzate in base al set di vincoli per selezionare la posizione ottimale del posizionamento.</span><span class="sxs-lookup"><span data-stu-id="300af-218">Possible placement locations that satisfy the type and rules are then optimized against the set of constraints to select the optimal placement location.</span></span> <span data-ttu-id="300af-219">Ognuna delle regole e dei vincoli può essere creata dalle funzioni di creazione statiche fornite.</span><span class="sxs-lookup"><span data-stu-id="300af-219">Each of the rules and constraints can be created by the provided static creation functions.</span></span> <span data-ttu-id="300af-220">Di seguito è riportata una funzione di costruzione di regole e vincoli di esempio.</span><span class="sxs-lookup"><span data-stu-id="300af-220">An example rule and constraint construction function is provided below.</span></span>




```
public static ObjectPlacementRule Create_AwayFromPosition(
                    Vector3 position, float minDistance)
               public static ObjectPlacementConstraint Create_NearPoint(
                    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

<span data-ttu-id="300af-221">La query di posizionamento degli oggetti riportata di seguito sta cercando una posizione per inserire un cubo a metà metro sul bordo di una superficie, lontano dagli altri oggetti posizionati in precedenza e vicino al centro della stanza.</span><span class="sxs-lookup"><span data-stu-id="300af-221">The object placement query below is looking for a place to put a half meter cube on the edge of a surface, away from other previously place objects and near the center of the room.</span></span>




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

<span data-ttu-id="300af-222">In caso di esito positivo, viene restituita una struttura **ObjectPlacementResult** contenente la posizione, le dimensioni e l'orientamento del posizionamento.</span><span class="sxs-lookup"><span data-stu-id="300af-222">If successful, an **ObjectPlacementResult** structure containing the placement position, dimensions and orientation is returned.</span></span> <span data-ttu-id="300af-223">Inoltre, la selezione host viene aggiunta all'elenco interno della DLL degli oggetti inseriti.</span><span class="sxs-lookup"><span data-stu-id="300af-223">In addition, the placement is added to the DLL’s internal list of placed objects.</span></span> <span data-ttu-id="300af-224">Questo oggetto verrà preso in considerazione dalle query di posizionamento successive.</span><span class="sxs-lookup"><span data-stu-id="300af-224">Subsequent placement queries will take this object into account.</span></span> <span data-ttu-id="300af-225">Il file **LevelSolver.cs** nell'esempio Unity contiene altre query di esempio.</span><span class="sxs-lookup"><span data-stu-id="300af-225">The **LevelSolver.cs** file in the Unity sample contains more example queries.</span></span>

![Le caselle blu mostrano il risultato da tre posizioni nelle query del piano con le regole di "disattivazione della fotocamera".](images/away-from-camera-position-500px.png)

<span data-ttu-id="300af-227">Le caselle blu mostrano il risultato da tre posizioni nelle query del piano con le regole di "disattivazione della fotocamera".</span><span class="sxs-lookup"><span data-stu-id="300af-227">The blue boxes show the result from three Place On Floor queries with "away from camera position" rules.</span></span>


<span data-ttu-id="300af-228">**Consigli**</span><span class="sxs-lookup"><span data-stu-id="300af-228">**Tips:**</span></span>
* <span data-ttu-id="300af-229">Quando si risolve la posizione di selezione host per più oggetti richiesti per uno scenario di livello o di applicazione, risolvere prima di tutto gli oggetti indispensabili e di grandi dimensioni per ottimizzare la probabilità che uno spazio possa essere trovato.</span><span class="sxs-lookup"><span data-stu-id="300af-229">When solving for placement location of multiple objects required for a level or application scenario, first solve indispensable and large objects to maximize the probability that a space can be found.</span></span>
* <span data-ttu-id="300af-230">L'ordine di posizionamento è importante.</span><span class="sxs-lookup"><span data-stu-id="300af-230">Placement order is important.</span></span> <span data-ttu-id="300af-231">Se non è possibile trovare le posizioni degli oggetti, provare a eseguire meno configurazioni vincolate.</span><span class="sxs-lookup"><span data-stu-id="300af-231">If object placements cannot be found, try less constrained configurations.</span></span> <span data-ttu-id="300af-232">Avere un set di configurazioni di fallback è fondamentale per supportare le funzionalità in molte configurazioni di chat room.</span><span class="sxs-lookup"><span data-stu-id="300af-232">Having a set of fallback configurations is critical to supporting functionality across many room configurations.</span></span>

### <a name="ray-casting"></a><span data-ttu-id="300af-233">Casting Ray</span><span class="sxs-lookup"><span data-stu-id="300af-233">Ray casting</span></span>

<span data-ttu-id="300af-234">Oltre alle tre query principali, è possibile usare un'interfaccia di cast di tipo Ray per recuperare i tipi di superficie con tag ed è possibile copiare una mesh playspace stermetica personalizzata quando la chat room è stata analizzata e finalizzata, le etichette vengono generate internamente per superfici come Floor, Ceiling e walls.</span><span class="sxs-lookup"><span data-stu-id="300af-234">In addition to the three primary queries, a ray casting interface can be used to retrieve tagged surface types and a custom watertight playspace mesh can be copied out After the room has been scanned and finalized, labels are internally generated for surfaces like the floor, ceiling, and walls.</span></span> <span data-ttu-id="300af-235">La funzione **PlayspaceRaycast** accetta un raggio e restituisce se il raggio è in conflitto con una superficie nota e, in tal caso, le informazioni su tale superficie sotto forma di **RaycastResult**.</span><span class="sxs-lookup"><span data-stu-id="300af-235">The **PlayspaceRaycast** function takes a ray and returns if the ray collides with a known surface and if so, information about that surface in the form of a **RaycastResult**.</span></span> 


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

<span data-ttu-id="300af-236">Internamente, il Raycast viene calcolato rispetto alla rappresentazione voxel del cubo di 8cm calcolata del playspace.</span><span class="sxs-lookup"><span data-stu-id="300af-236">Internally, the raycast is computed against the computed 8cm cubed voxel representation of the playspace.</span></span> <span data-ttu-id="300af-237">Ogni voxel contiene un set di elementi Surface con dati della topologia elaborati (noti anche come surfels).</span><span class="sxs-lookup"><span data-stu-id="300af-237">Each voxel contains a set of surface elements with processed topology data (also known as surfels).</span></span> <span data-ttu-id="300af-238">Il surfels contenuto all'interno della cella voxel intersecata viene confrontato e la migliore corrispondenza utilizzata per cercare le informazioni sulla topologia.</span><span class="sxs-lookup"><span data-stu-id="300af-238">The surfels contained within the intersected voxel cell are compared and the best match used to look up the topology information.</span></span> <span data-ttu-id="300af-239">Questi dati della topologia contengono l'etichettatura restituita sotto forma di enumerazione **SurfaceTypes** , nonché la superficie di attacco della superficie intersecata.</span><span class="sxs-lookup"><span data-stu-id="300af-239">This topology data contains the labeling returned in the form of the **SurfaceTypes** enum, as well as the surface area of the intersected surface.</span></span>

<span data-ttu-id="300af-240">Nell'esempio Unity il cursore esegue il cast di un raggio per ogni fotogramma.</span><span class="sxs-lookup"><span data-stu-id="300af-240">In the Unity sample, the cursor casts a ray each frame.</span></span> <span data-ttu-id="300af-241">Per prima cosa, rispetto ai Collider di Unity; in secondo luogo, sulla rappresentazione mondiale del modulo di informazioni; e infine sugli elementi dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="300af-241">First, against Unity’s colliders; second, against the understanding module’s world representation; and finally, against the UI elements.</span></span> <span data-ttu-id="300af-242">In questa applicazione, l'interfaccia utente ottiene la priorità, quindi il risultato della comprensione e infine i Collider di Unity.</span><span class="sxs-lookup"><span data-stu-id="300af-242">In this application, UI gets priority, then the understanding result, and finally, Unity’s colliders.</span></span> <span data-ttu-id="300af-243">**SurfaceType** viene segnalato come testo accanto al cursore.</span><span class="sxs-lookup"><span data-stu-id="300af-243">The **SurfaceType** is reported as text next to the cursor.</span></span>

![Intersezione di report dei risultati di Raycast con il piano.](images/raycast-result-500px.jpg)

<span data-ttu-id="300af-245">Intersezione di report dei risultati di Raycast con il piano.</span><span class="sxs-lookup"><span data-stu-id="300af-245">Raycast result reporting intersection with the floor.</span></span>


## <a name="get-the-code"></a><span data-ttu-id="300af-246">Ottenere il codice</span><span class="sxs-lookup"><span data-stu-id="300af-246">Get the code</span></span>

<span data-ttu-id="300af-247">Il codice open source è disponibile in [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity).</span><span class="sxs-lookup"><span data-stu-id="300af-247">The open-source code is available in [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity).</span></span> <span data-ttu-id="300af-248">Se si usa il codice in un progetto, segnalare i [forum per sviluppatori di HoloLens](https://forums.hololens.com/) .</span><span class="sxs-lookup"><span data-stu-id="300af-248">Let us know on the [HoloLens Developer Forums](https://forums.hololens.com/) if you use the code in a project.</span></span> <span data-ttu-id="300af-249">Non possiamo attendere per vedere cosa puoi fare!</span><span class="sxs-lookup"><span data-stu-id="300af-249">We can't wait to see what you do with it!</span></span>

## <a name="about-the-author"></a><span data-ttu-id="300af-250">Informazioni sull'autore</span><span class="sxs-lookup"><span data-stu-id="300af-250">About the author</span></span>

<table style="border:0;width:800px">
<tr>
<td style="border:0"> <img alt="Jeff Evertt, Software Engineering Lead at Microsoft" width="200" height="205" src="images/jeff-evertt-200px.jpg" /></td><td style="border:0"> <span data-ttu-id="300af-251"><b>Jeff evertt</b> è un responsabile di ingegneria del software che ha lavorato a HoloLens dai primi giorni, dall'incubazione all'esperienza di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="300af-251"><b>Jeff Evertt</b> is a software engineering lead who has worked on HoloLens since the early days, from incubation to experience development.</span></span> <span data-ttu-id="300af-252">Prima di HoloLens, ha collaborato con Xbox Kinect e nel settore dei giochi in un'ampia gamma di piattaforme e giochi.</span><span class="sxs-lookup"><span data-stu-id="300af-252">Before HoloLens, he worked on the Xbox Kinect and in the games industry on a wide variety of platforms and games.</span></span> <span data-ttu-id="300af-253">Jeff è appassionato di Robotica, grafica e cose con luci appariscenti.</span><span class="sxs-lookup"><span data-stu-id="300af-253">Jeff is passionate about robotics, graphics, and things with flashy lights that go beep.</span></span> <span data-ttu-id="300af-254">Si diverte ad apprendere nuove cose e a lavorare su software, hardware e in particolare nello spazio in cui si intersecano le due.</span><span class="sxs-lookup"><span data-stu-id="300af-254">He enjoys learning new things and working on software, hardware, and particularly in the space where the two intersect.</span></span></td>
</tr>
</table>



## <a name="see-also"></a><span data-ttu-id="300af-255">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="300af-255">See also</span></span>
* [<span data-ttu-id="300af-256">Mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="300af-256">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="300af-257">Progettazione del mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="300af-257">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="300af-258">Visualizzazione della scansione dello spazio</span><span class="sxs-lookup"><span data-stu-id="300af-258">Room scan visualization</span></span>](room-scan-visualization.md)
* [<span data-ttu-id="300af-259">MixedRealityToolkit-Unity</span><span class="sxs-lookup"><span data-stu-id="300af-259">MixedRealityToolkit-Unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="300af-260">Asobo Studio: Lezioni dal Frontline dello sviluppo di HoloLens</span><span class="sxs-lookup"><span data-stu-id="300af-260">Asobo Studio: Lessons from the frontline of HoloLens development</span></span>](http://www.gamesindustry.biz/articles/2016-05-12-asobo-lessons-from-the-frontline-of-ar-development)

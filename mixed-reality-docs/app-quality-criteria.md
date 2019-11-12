---
title: Criteri di qualità delle app
description: Questo documento descrive i principali fattori che influiscono sulla qualità delle app per realtà mista.
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: criteri di qualità delle app, realtà mista, app per realtà mista
ms.openlocfilehash: d167e141b536f9247d22e40afefa718ecc399f5a
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926584"
---
# <a name="app-quality-criteria"></a><span data-ttu-id="92670-104">Criteri di qualità delle app</span><span class="sxs-lookup"><span data-stu-id="92670-104">App quality criteria</span></span>

<span data-ttu-id="92670-105">Questo documento descrive i principali fattori che influiscono sulla qualità delle app per realtà mista.</span><span class="sxs-lookup"><span data-stu-id="92670-105">This document describes the top factors impacting the quality of mixed reality apps.</span></span> <span data-ttu-id="92670-106">Per ogni fattore vengono fornite le informazioni seguenti</span><span class="sxs-lookup"><span data-stu-id="92670-106">For each factor the following information is provided</span></span>
* <span data-ttu-id="92670-107">Panoramica: breve descrizione del fattore di qualità e dei motivi per cui è importante.</span><span class="sxs-lookup"><span data-stu-id="92670-107">Overview – a brief description of the quality factor and why it is important.</span></span>
* <span data-ttu-id="92670-108">Effetto del dispositivo: il tipo di dispositivo di realtà mista della finestra interessato.</span><span class="sxs-lookup"><span data-stu-id="92670-108">Device impact - which type of Window Mixed Reality device is impacted.</span></span>
* <span data-ttu-id="92670-109">Criteri di qualità: come valutare il fattore di qualità.</span><span class="sxs-lookup"><span data-stu-id="92670-109">Quality criteria – how to evaluate the quality factor.</span></span>
* <span data-ttu-id="92670-110">Come misurare, ovvero i metodi per misurare o sperimentare il problema.</span><span class="sxs-lookup"><span data-stu-id="92670-110">How to measure – methods to measure (or experience) the issue.</span></span>
* <span data-ttu-id="92670-111">Suggerimenti: riepilogo degli approcci per offrire un'esperienza utente migliore.</span><span class="sxs-lookup"><span data-stu-id="92670-111">Recommendations – summary of approaches to provide a better user experience.</span></span>
* <span data-ttu-id="92670-112">Risorse: risorse di sviluppo e progettazione pertinenti utili per creare esperienze di app migliori.</span><span class="sxs-lookup"><span data-stu-id="92670-112">Resources – relevant developer and design resources that are useful to create better app experiences.</span></span>

## <a name="frame-rate"></a><span data-ttu-id="92670-113">Frequenza dei fotogrammi</span><span class="sxs-lookup"><span data-stu-id="92670-113">Frame rate</span></span>

<span data-ttu-id="92670-114">La frequenza dei fotogrammi è il primo pilastro della stabilità degli ologrammi e della comodità degli utenti.</span><span class="sxs-lookup"><span data-stu-id="92670-114">Frame rate is the first pillar of hologram stability and user comfort.</span></span> <span data-ttu-id="92670-115">La frequenza dei fotogrammi al di sotto delle destinazioni consigliate può comportare la distorsione degli ologrammi, con un impatto negativo sulla credibilità dell'esperienza e potenzialmente causare affaticamento degli occhi.</span><span class="sxs-lookup"><span data-stu-id="92670-115">Frame rate below the recommended targets can cause holograms to appear jittery, negatively impacting the believability of the experience and potentially causing eye fatigue.</span></span> <span data-ttu-id="92670-116">La frequenza dei fotogrammi di destinazione per la tua esperienza negli auricolari ad alta realtà mista di Windows è 60Hz o 90Hz, a seconda dei computer compatibili con la realtà Windows che desideri supportare.</span><span class="sxs-lookup"><span data-stu-id="92670-116">The target frame rate for your experience on Windows Mixed Reality immersive headsets will be either 60Hz or 90Hz depending on which Windows Mixed Reality Compatible PCs you wish to support.</span></span> <span data-ttu-id="92670-117">Per HoloLens la frequenza dei fotogrammi di destinazione è 60Hz.</span><span class="sxs-lookup"><span data-stu-id="92670-117">For HoloLens the target frame rate is 60Hz.</span></span>

### <a name="device-impact"></a><span data-ttu-id="92670-118">Effetti sul dispositivo</span><span class="sxs-lookup"><span data-stu-id="92670-118">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="92670-119"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="92670-119"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="92670-120"><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="92670-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="92670-121">✔️</span><span class="sxs-lookup"><span data-stu-id="92670-121">✔️</span></span></td>
        <td><span data-ttu-id="92670-122">✔️</span><span class="sxs-lookup"><span data-stu-id="92670-122">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="92670-123">Criteri di qualità</span><span class="sxs-lookup"><span data-stu-id="92670-123">Quality criteria</span></span>

|  <span data-ttu-id="92670-124">Consigliate</span><span class="sxs-lookup"><span data-stu-id="92670-124">Best</span></span>  |  <span data-ttu-id="92670-125">Soddisfi</span><span class="sxs-lookup"><span data-stu-id="92670-125">Meets</span></span> |  <span data-ttu-id="92670-126">Esito negativo</span><span class="sxs-lookup"><span data-stu-id="92670-126">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="92670-127">L'app soddisfa costantemente i frame al secondo (FPS) obiettivo del dispositivo di destinazione: 60fps in HoloLens; 90fps su PC ultra; e 60fps nei PC mainstream.</span><span class="sxs-lookup"><span data-stu-id="92670-127">The app consistently meets frames per second (FPS) goal for target device: 60fps on HoloLens; 90fps on Ultra PCs; and 60fps on mainstream PCs.</span></span> | <span data-ttu-id="92670-128">L'app ha un frame intermittente che non ostacola l'esperienza principale; o FPS è costantemente inferiore all'obiettivo desiderato, ma non impedisce l'esperienza dell'app.</span><span class="sxs-lookup"><span data-stu-id="92670-128">The app has intermittent frame drops not impeding the core experience; or FPS is consistently lower than desired goal but doesn’t impede the app experience.</span></span> | <span data-ttu-id="92670-129">L'app sta riscontrando un calo della frequenza dei fotogrammi in media ogni 10 secondi o meno.</span><span class="sxs-lookup"><span data-stu-id="92670-129">The app is experiencing a drop in frame rate on average every ten seconds or less.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="92670-130">Come misurare</span><span class="sxs-lookup"><span data-stu-id="92670-130">How to measure</span></span>

* <span data-ttu-id="92670-131">Un grafico con frequenza dei fotogrammi in tempo reale viene fornito tramite il [portale per dispositivi Windows](using-the-windows-device-portal.md#system-performance) in "prestazioni del sistema".</span><span class="sxs-lookup"><span data-stu-id="92670-131">A real-time frame rate graph is provided through by the [Windows Device Portal](using-the-windows-device-portal.md#system-performance) under "System Performance".</span></span>
* <span data-ttu-id="92670-132">Per il debug dello sviluppo, aggiungere un contatore di diagnostica della frequenza dei fotogrammi nell'app.</span><span class="sxs-lookup"><span data-stu-id="92670-132">For development debugging, add a frame rate diagnostic counter into the app.</span></span> <span data-ttu-id="92670-133">Vedere risorse per un contatore di esempio.</span><span class="sxs-lookup"><span data-stu-id="92670-133">See Resources for a sample counter.</span></span>
* <span data-ttu-id="92670-134">Le gocce di frequenza dei fotogrammi possono essere rilevate nel dispositivo mentre l'app è in esecuzione spostando l'intestazione da un lato all'altro.</span><span class="sxs-lookup"><span data-stu-id="92670-134">Frame rate drops can be experienced in device while the app is running by moving your head from side to side.</span></span> <span data-ttu-id="92670-135">Se l'ologramma mostra un movimento nervoso imprevisto, è probabile che la frequenza minima dei frame o il piano di stabilità sia la causa.</span><span class="sxs-lookup"><span data-stu-id="92670-135">If the hologram shows unexpected jittery movement, then low frame rate or the stability plane is likely the cause.</span></span>

### <a name="recommendations"></a><span data-ttu-id="92670-136">Consigli</span><span class="sxs-lookup"><span data-stu-id="92670-136">Recommendations</span></span>

* <span data-ttu-id="92670-137">Aggiungere un contatore della frequenza dei fotogrammi all'inizio del lavoro di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="92670-137">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="92670-138">Le modifiche che comportano un calo nella frequenza del frame devono essere valutate e risolte in modo appropriato come bug delle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="92670-138">Changes that incur a drop in frame rate should be evaluated and appropriately resolved as a performance bug.</span></span>

### <a name="resources"></a><span data-ttu-id="92670-139">Risorse</span><span class="sxs-lookup"><span data-stu-id="92670-139">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="92670-140">Documentazione</span><span class="sxs-lookup"><span data-stu-id="92670-140">Documentation</span></span>

* [<span data-ttu-id="92670-141">Informazioni sulle prestazioni per la realtà mista</span><span class="sxs-lookup"><span data-stu-id="92670-141">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="92670-142">Stabilità e framerate degli ologrammi</span><span class="sxs-lookup"><span data-stu-id="92670-142">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="92670-143">Budget per le prestazioni dell'asset</span><span class="sxs-lookup"><span data-stu-id="92670-143">Asset performance budget</span></span>](asset-creation-process.md)
* [<span data-ttu-id="92670-144">Consigli sulle prestazioni per Unity</span><span class="sxs-lookup"><span data-stu-id="92670-144">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="92670-145">Strumenti ed esercitazioni</span><span class="sxs-lookup"><span data-stu-id="92670-145">Tools and tutorials</span></span>

* [<span data-ttu-id="92670-146">MRToolkit, visualizzazione del contatore FPS</span><span class="sxs-lookup"><span data-stu-id="92670-146">MRToolkit, FPS counter display</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [<span data-ttu-id="92670-147">MRToolkit, shader</span><span class="sxs-lookup"><span data-stu-id="92670-147">MRToolkit, Shaders</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a><span data-ttu-id="92670-148">Riferimenti esterni</span><span class="sxs-lookup"><span data-stu-id="92670-148">External references</span></span>

* [<span data-ttu-id="92670-149">Unity, ottimizzazione delle applicazioni per dispositivi mobili</span><span class="sxs-lookup"><span data-stu-id="92670-149">Unity, Optimizing mobile applications</span></span>](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a><span data-ttu-id="92670-150">Stabilità olografica</span><span class="sxs-lookup"><span data-stu-id="92670-150">Hologram stability</span></span>

<span data-ttu-id="92670-151">Gli ologrammi stabili aumenteranno l'usabilità e la credibilità dell'app e creeranno un'esperienza di visualizzazione più comoda per l'utente.</span><span class="sxs-lookup"><span data-stu-id="92670-151">Stable holograms will increase the usability and believability of your app, and create a more comfortable viewing experience for the user.</span></span> <span data-ttu-id="92670-152">La qualità della stabilità dell'ologramma è il risultato dello sviluppo di App valide e della capacità del dispositivo di comprendere (monitorare) il proprio ambiente.</span><span class="sxs-lookup"><span data-stu-id="92670-152">The quality of hologram stability is a result of good app development and the device's ability to understand (track) its environment.</span></span> <span data-ttu-id="92670-153">Sebbene la frequenza dei fotogrammi sia il primo pilastro della stabilità, altri fattori possono influiscono sulla stabilità, tra cui:</span><span class="sxs-lookup"><span data-stu-id="92670-153">While frame rate is the first pillar of stability, other factors can impact stability including:</span></span>

* <span data-ttu-id="92670-154">Uso del piano di stabilizzazione</span><span class="sxs-lookup"><span data-stu-id="92670-154">Use of the stabilization plane</span></span>
* <span data-ttu-id="92670-155">Distanza dagli ancoraggi spaziali</span><span class="sxs-lookup"><span data-stu-id="92670-155">Distance to spatial anchors</span></span>
* <span data-ttu-id="92670-156">Tracking</span><span class="sxs-lookup"><span data-stu-id="92670-156">Tracking</span></span>

### <a name="device-impact"></a><span data-ttu-id="92670-157">Effetti sul dispositivo</span><span class="sxs-lookup"><span data-stu-id="92670-157">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="92670-158"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="92670-158"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="92670-159"><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="92670-159"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="92670-160">✔️</span><span class="sxs-lookup"><span data-stu-id="92670-160">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="92670-161">Criteri di qualità</span><span class="sxs-lookup"><span data-stu-id="92670-161">Quality criteria</span></span>

|  <span data-ttu-id="92670-162">Consigliate</span><span class="sxs-lookup"><span data-stu-id="92670-162">Best</span></span>  |  <span data-ttu-id="92670-163">Soddisfi</span><span class="sxs-lookup"><span data-stu-id="92670-163">Meets</span></span> |  <span data-ttu-id="92670-164">Esito negativo</span><span class="sxs-lookup"><span data-stu-id="92670-164">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="92670-165">Gli ologrammi appaiono costantemente stabili.</span><span class="sxs-lookup"><span data-stu-id="92670-165">Holograms consistently appear stable.</span></span> | <span data-ttu-id="92670-166">Il contenuto secondario presenta un movimento imprevisto; o un movimento imprevisto non ostacola l'esperienza complessiva dell'app.</span><span class="sxs-lookup"><span data-stu-id="92670-166">Secondary content exhibits unexpected movement; or unexpected movement does not impede overall app experience.</span></span> | <span data-ttu-id="92670-167">Il contenuto primario nel frame presenta un movimento imprevisto.</span><span class="sxs-lookup"><span data-stu-id="92670-167">Primary content in frame exhibits unexpected movement.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="92670-168">Come misurare</span><span class="sxs-lookup"><span data-stu-id="92670-168">How to measure</span></span>

<span data-ttu-id="92670-169">Durante l'uso del dispositivo e la visualizzazione dell'esperienza:</span><span class="sxs-lookup"><span data-stu-id="92670-169">While wearing the device and viewing the experience:</span></span>

* <span data-ttu-id="92670-170">Spostare la testa da un lato all'altro, se gli ologrammi mostrano un movimento imprevisto, la frequenza dei fotogrammi ridotta o l'allineamento non corretto del piano di stabilità al piano focale è la causa probabile.</span><span class="sxs-lookup"><span data-stu-id="92670-170">Move your head from side to side, if the holograms show unexpected movement then low frame rate or improper alignment of the stability plane to the focal plane is the likely cause.</span></span>
* <span data-ttu-id="92670-171">Spostarsi tra gli ologrammi e l'ambiente, cercare comportamenti come Swim e nervosismo.</span><span class="sxs-lookup"><span data-stu-id="92670-171">Move around the holograms and environment, look for behaviors such as swim and jumpiness.</span></span> <span data-ttu-id="92670-172">Questo tipo di movimento è probabilmente causato dal fatto che il dispositivo non tiene traccia dell'ambiente o la distanza dall'ancoraggio spaziale.</span><span class="sxs-lookup"><span data-stu-id="92670-172">This type of motion is likely caused by the device not tracking the environment, or the distance to the spatial anchor.</span></span>
* <span data-ttu-id="92670-173">Se nel frame sono presenti ologrammi di grandi dimensioni o più, osservare il comportamento degli ologrammi a diverse profondità spostando la posizione della testa da un lato all'altro, se shakiness è probabilmente causato dal piano di stabilizzazione.</span><span class="sxs-lookup"><span data-stu-id="92670-173">If large or multiple holograms are in the frame, observe hologram behavior at various depths while moving your head position from side to side, if shakiness appears this is likely caused by the stabilization plane.</span></span>

### <a name="recommendations"></a><span data-ttu-id="92670-174">Consigli</span><span class="sxs-lookup"><span data-stu-id="92670-174">Recommendations</span></span>

* <span data-ttu-id="92670-175">Aggiungere un contatore della frequenza dei fotogrammi all'inizio del lavoro di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="92670-175">Add an frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="92670-176">Usare il piano di stabilizzazione.</span><span class="sxs-lookup"><span data-stu-id="92670-176">Use the stabilization plane.</span></span>
* <span data-ttu-id="92670-177">Eseguire sempre il rendering degli ologrammi ancorati all'interno di 3 metri dell'ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="92670-177">Always render anchored holograms within 3 meters of their anchor.</span></span>
* <span data-ttu-id="92670-178">Assicurarsi che l'ambiente sia configurato per il rilevamento appropriato.</span><span class="sxs-lookup"><span data-stu-id="92670-178">Make sure your environment is setup for proper tracking.</span></span>
* <span data-ttu-id="92670-179">Progetta la tua esperienza per evitare gli ologrammi a diversi livelli di profondità focale all'interno del frame.</span><span class="sxs-lookup"><span data-stu-id="92670-179">Design your experience to avoid holograms at various focal depth levels within the frame.</span></span>

### <a name="resources"></a><span data-ttu-id="92670-180">Risorse</span><span class="sxs-lookup"><span data-stu-id="92670-180">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="92670-181">Documentazione</span><span class="sxs-lookup"><span data-stu-id="92670-181">Documentation</span></span>

* [<span data-ttu-id="92670-182">Stabilità e framerate degli ologrammi</span><span class="sxs-lookup"><span data-stu-id="92670-182">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="92670-183">Case Study, uso del piano di stabilizzazione</span><span class="sxs-lookup"><span data-stu-id="92670-183">Case study, Using the stabilization plane</span></span>](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [<span data-ttu-id="92670-184">Informazioni sulle prestazioni per la realtà mista</span><span class="sxs-lookup"><span data-stu-id="92670-184">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="92670-185">Consigli sulle prestazioni per Unity</span><span class="sxs-lookup"><span data-stu-id="92670-185">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="92670-186">Ancoraggi nello spazio</span><span class="sxs-lookup"><span data-stu-id="92670-186">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="92670-187">Gestione degli errori di rilevamento</span><span class="sxs-lookup"><span data-stu-id="92670-187">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="92670-188">Cornice fissa di riferimento</span><span class="sxs-lookup"><span data-stu-id="92670-188">Stationary frame of reference</span></span>](coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="92670-189">Strumenti ed esercitazioni</span><span class="sxs-lookup"><span data-stu-id="92670-189">Tools and tutorials</span></span>

* [<span data-ttu-id="92670-190">Kit MR Companion, Kinect dpi</span><span class="sxs-lookup"><span data-stu-id="92670-190">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a><span data-ttu-id="92670-191">Posizione degli ologrammi su superfici reali</span><span class="sxs-lookup"><span data-stu-id="92670-191">Holograms position on real surfaces</span></span>

<span data-ttu-id="92670-192">I disallineamenti degli ologrammi con oggetti fisici (se destinati a essere posizionati in relazione l'uno con l'altro) sono un'indicazione chiara della mancata unione degli ologrammi e del mondo reale.</span><span class="sxs-lookup"><span data-stu-id="92670-192">Misalignments of holograms with physical objects (if intended to be placed in relation to one another) is a clear indication of the non-union of holograms and real-world.</span></span> <span data-ttu-id="92670-193">L'accuratezza della selezione host deve essere relativa alle esigenze dello scenario; ad esempio, la selezione della superficie generale può utilizzare la mappa spaziale, ma la selezione host più accurata richiede l'utilizzo di marcatori e di calibrazione.</span><span class="sxs-lookup"><span data-stu-id="92670-193">Accuracy of the placement should be relative to the needs of the scenario; for example, general surface placement can use the spatial map, but more accurate placement will require some use of markers and calibration.</span></span>

### <a name="device-impact"></a><span data-ttu-id="92670-194">Effetti sul dispositivo</span><span class="sxs-lookup"><span data-stu-id="92670-194">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="92670-195"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="92670-195"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="92670-196"><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="92670-196"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="92670-197">✔️</span><span class="sxs-lookup"><span data-stu-id="92670-197">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="92670-198">Criteri di qualità</span><span class="sxs-lookup"><span data-stu-id="92670-198">Quality criteria</span></span>

|  <span data-ttu-id="92670-199">Consigliate</span><span class="sxs-lookup"><span data-stu-id="92670-199">Best</span></span>  |  <span data-ttu-id="92670-200">Soddisfi</span><span class="sxs-lookup"><span data-stu-id="92670-200">Meets</span></span> |  <span data-ttu-id="92670-201">Esito negativo</span><span class="sxs-lookup"><span data-stu-id="92670-201">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="92670-202">Gli ologrammi si allineano alla superficie in genere nell'intervallo di centimetri.</span><span class="sxs-lookup"><span data-stu-id="92670-202">Holograms align to the surface typically in the centimeters to inches range.</span></span> <span data-ttu-id="92670-203">Se è necessaria una maggiore accuratezza, l'app deve fornire un modo efficiente per collaborare all'interno della specifica dell'app desiderata.</span><span class="sxs-lookup"><span data-stu-id="92670-203">If more accuracy is required, the app should provide an efficient means for collaboration within the desired app spec.</span></span> | <span data-ttu-id="92670-204">N/D</span><span class="sxs-lookup"><span data-stu-id="92670-204">NA</span></span> | <span data-ttu-id="92670-205">Gli ologrammi appaiono non allineati con l'oggetto di destinazione fisico suddividendo il piano della superficie o facendo in modo che si trovi in un altro modo.</span><span class="sxs-lookup"><span data-stu-id="92670-205">The holograms appear unaligned with the physical target object by either breaking the surface plane or appearing to float away from the surface.</span></span> <span data-ttu-id="92670-206">Se è necessaria l'accuratezza, gli ologrammi dovrebbero soddisfare le specifiche di prossimità dello scenario.</span><span class="sxs-lookup"><span data-stu-id="92670-206">If accuracy is required, Holograms should meet the proximity spec of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="92670-207">Come misurare</span><span class="sxs-lookup"><span data-stu-id="92670-207">How to measure</span></span>

* <span data-ttu-id="92670-208">Gli ologrammi posizionati sulla mappa spaziale non devono essere visualizzati in modo significativo sopra o sotto la superficie.</span><span class="sxs-lookup"><span data-stu-id="92670-208">Holograms that are placed on spatial map should not appear to dramatically float above or below the surface.</span></span>
* <span data-ttu-id="92670-209">Gli ologrammi che richiedono un posizionamento accurato devono avere una forma di sistema di marcatore e di calibrazione accurato per il requisito dello scenario.</span><span class="sxs-lookup"><span data-stu-id="92670-209">Holograms that require accurate placement should have some form of marker and calibration system that is accurate to the scenario's requirement.</span></span>

### <a name="recommendations"></a><span data-ttu-id="92670-210">Consigli</span><span class="sxs-lookup"><span data-stu-id="92670-210">Recommendations</span></span>

* <span data-ttu-id="92670-211">La mappa spaziale è utile per posizionare oggetti sulle superfici quando la precisione non è necessaria.</span><span class="sxs-lookup"><span data-stu-id="92670-211">Spatial map is useful for placing objects on surfaces when precision isn’t required.</span></span>
* <span data-ttu-id="92670-212">Per la massima precisione, usare i marcatori o i poster per impostare gli ologrammi e un controller Xbox (o un meccanismo di allineamento manuale) per la calibrazione finale.</span><span class="sxs-lookup"><span data-stu-id="92670-212">For the best precision, use markers or posters to set the holograms and an Xbox controller (or some manual alignment mechanism) for final calibration.</span></span>
* <span data-ttu-id="92670-213">Prendere in considerazione la possibilità di suddividere ologrammi molto grandi in parti logiche e di allineare ogni parte alla superficie.</span><span class="sxs-lookup"><span data-stu-id="92670-213">Consider breaking extra-large holograms into logical parts and aligning each part to the surface.</span></span>
* <span data-ttu-id="92670-214">L'impostazione non corretta della distanza interpupillare (dpi) può anche influire sull'allineamento degli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="92670-214">Improperly set interpupillary distance (IPD) can also effect hologram alignment.</span></span> <span data-ttu-id="92670-215">Configurare sempre HoloLens sul DPI dell'utente.</span><span class="sxs-lookup"><span data-stu-id="92670-215">Always configure HoloLens to the user's IPD.</span></span>

### <a name="resources"></a><span data-ttu-id="92670-216">Risorse</span><span class="sxs-lookup"><span data-stu-id="92670-216">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="92670-217">Documentazione</span><span class="sxs-lookup"><span data-stu-id="92670-217">Documentation</span></span>

* [<span data-ttu-id="92670-218">Selezione host per mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="92670-218">Spatial mapping placement</span></span>](spatial-mapping.md#placement)
* [<span data-ttu-id="92670-219">Processo di analisi chat room</span><span class="sxs-lookup"><span data-stu-id="92670-219">Room scanning process</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="92670-220">Procedure consigliate per gli ancoraggi spaziali</span><span class="sxs-lookup"><span data-stu-id="92670-220">Spatial anchors best practices</span></span>](spatial-anchors.md#best-practices)
* [<span data-ttu-id="92670-221">Gestione degli errori di rilevamento</span><span class="sxs-lookup"><span data-stu-id="92670-221">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="92670-222">Mapping spaziale in Unity</span><span class="sxs-lookup"><span data-stu-id="92670-222">Spatial mapping in Unity</span></span>](spatial-mapping-in-unity.md)
* [<span data-ttu-id="92670-223">Panoramica sullo sviluppo di Vuforia</span><span class="sxs-lookup"><span data-stu-id="92670-223">Vuforia development overview</span></span>](vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="92670-224">Strumenti ed esercitazioni</span><span class="sxs-lookup"><span data-stu-id="92670-224">Tools and tutorials</span></span>

* [<span data-ttu-id="92670-225">MR Spatial 230: mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="92670-225">MR Spatial 230: Spatial mapping</span></span>](holograms-230.md)
* [<span data-ttu-id="92670-226">MR Toolkit, librerie di mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="92670-226">MR Toolkit, Spatial Mapping Libraries</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [<span data-ttu-id="92670-227">Kit MR Companion, esempio di calibrazione poster</span><span class="sxs-lookup"><span data-stu-id="92670-227">MR Companion Kit, Poster Calibration Sample</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [<span data-ttu-id="92670-228">Kit MR Companion, Kinect dpi</span><span class="sxs-lookup"><span data-stu-id="92670-228">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a><span data-ttu-id="92670-229">Riferimenti esterni</span><span class="sxs-lookup"><span data-stu-id="92670-229">External references</span></span>

* [<span data-ttu-id="92670-230">Case Study di Lowes, allineamento della precisione</span><span class="sxs-lookup"><span data-stu-id="92670-230">Lowes Case Study, Precision alignment</span></span>](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a><span data-ttu-id="92670-231">Visualizzazione della zona di comfort</span><span class="sxs-lookup"><span data-stu-id="92670-231">Viewing zone of comfort</span></span>

<span data-ttu-id="92670-232">Gli sviluppatori di app controllano la posizione di convergenza degli occhi degli utenti inserendo contenuto e ologrammi a diverse profondità.</span><span class="sxs-lookup"><span data-stu-id="92670-232">App developers control where users' eyes converge by placing content and holograms at various depths.</span></span> <span data-ttu-id="92670-233">Gli utenti che indossano HoloLens saranno sempre a 2,0 m per mantenere un'immagine chiara, perché le visualizzazioni HoloLens sono fisse a distanza ottica circa 2,0 m dall'utente.</span><span class="sxs-lookup"><span data-stu-id="92670-233">Users wearing HoloLens will always accommodate to 2.0m to maintain a clear image because HoloLens displays are fixed at an optical distance approximately 2.0m away from the user.</span></span> <span data-ttu-id="92670-234">Una profondità di contenuto impropria può causare disagi visivi o affaticamento.</span><span class="sxs-lookup"><span data-stu-id="92670-234">Improper content depth can lead to visual discomfort or fatigue.</span></span>

### <a name="device-impact"></a><span data-ttu-id="92670-235">Effetti sul dispositivo</span><span class="sxs-lookup"><span data-stu-id="92670-235">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="92670-236"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="92670-236"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="92670-237"><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="92670-237"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="92670-238">✔️</span><span class="sxs-lookup"><span data-stu-id="92670-238">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="92670-239">Criteri di qualità</span><span class="sxs-lookup"><span data-stu-id="92670-239">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="92670-240">Consigliate</span><span class="sxs-lookup"><span data-stu-id="92670-240">Best</span></span> </td><td><ul>
<li><span data-ttu-id="92670-241">Inserire il contenuto a 2m.</span><span class="sxs-lookup"><span data-stu-id="92670-241">Place content at 2m.</span></span></li><li><span data-ttu-id="92670-242">Quando gli ologrammi non possono essere posizionati su 2m e i conflitti tra la convergenza e l'alloggio non possono essere evitati, la zona ottimale per la posizione degli ologrammi è compresa tra 1.25 m e 5m.</span><span class="sxs-lookup"><span data-stu-id="92670-242">When holograms cannot be placed at 2m and conflicts between convergence and accommodation cannot be avoided, the optimal zone for hologram placement is between 1.25m and 5m.</span></span></li><li><span data-ttu-id="92670-243">In ogni caso, i progettisti devono strutturare il contenuto per incoraggiare gli utenti a interagire tra 1 + m (ad esempio, modificare le dimensioni del contenuto e i parametri di posizionamento predefiniti).</span><span class="sxs-lookup"><span data-stu-id="92670-243">In every case, designers should structure content to encourage users to interact 1+ m away (e.g. adjust content size and default placement parameters).</span></span></li><li><span data-ttu-id="92670-244">A meno che non sia specificamente necessario per lo scenario, un piano di ritaglio deve essere implementato con dissolvenza a partire da 1 milione.</span><span class="sxs-lookup"><span data-stu-id="92670-244">Unless specifically not required by the scenario, a clipping plane should be implement with fadeout starting at 1m.</span></span></li><li><span data-ttu-id="92670-245">Nei casi in cui è necessaria un'osservazione più stretta di un ologramma senza movimento, il contenuto non deve essere più vicino a 50cm.</span><span class="sxs-lookup"><span data-stu-id="92670-245">In cases where closer observation of a motionless hologram is required, the content should not be closer than 50cm.</span></span></li>
</ul></td>
</tr><tr>
<td> <span data-ttu-id="92670-246">Soddisfi</span><span class="sxs-lookup"><span data-stu-id="92670-246">Meets</span></span></td><td> <span data-ttu-id="92670-247">Il contenuto si trova all'interno delle linee guida per la visualizzazione e il movimento, ma non è corretto o non utilizza il piano di ritaglio.</span><span class="sxs-lookup"><span data-stu-id="92670-247">Content is within the viewing and motion guidance, but improper use or no use of the clipping plane.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="92670-248">Esito negativo</span><span class="sxs-lookup"><span data-stu-id="92670-248">Fail</span></span> </td><td> <span data-ttu-id="92670-249">Il contenuto viene presentato troppo vicino (in genere &lt;1.25 m o &lt;50cm per gli ologrammi stazionari che richiedono un'osservazione più approfondita).</span><span class="sxs-lookup"><span data-stu-id="92670-249">Content is presented too close (typically &lt;1.25m, or &lt;50cm for stationary holograms requiring closer observation.)</span></span></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="92670-250">Come misurare</span><span class="sxs-lookup"><span data-stu-id="92670-250">How to measure</span></span>

* <span data-ttu-id="92670-251">Il contenuto deve essere in genere 2m, ma non più vicino a 1,25 o più di 5 minuti.</span><span class="sxs-lookup"><span data-stu-id="92670-251">Content should typically be 2m away, but no closer than 1.25 or further than 5m.</span></span>
* <span data-ttu-id="92670-252">Con poche eccezioni, la distanza di rendering del ritaglio HoloLens deve essere impostata su. 85CM con la dissolvenza del contenuto a partire da 1 milione.</span><span class="sxs-lookup"><span data-stu-id="92670-252">With few exceptions, the HoloLens clipping render distance should be set to .85CM with fadeout of content starting at 1m.</span></span> <span data-ttu-id="92670-253">Approccio al contenuto e annotare l'effetto del piano di ritaglio.</span><span class="sxs-lookup"><span data-stu-id="92670-253">Approach the content and note the clipping plane effect.</span></span>
* <span data-ttu-id="92670-254">Il contenuto fisso non deve essere più vicino a 50cm.</span><span class="sxs-lookup"><span data-stu-id="92670-254">Stationary content should not be closer than 50cm away.</span></span>

### <a name="recommendations"></a><span data-ttu-id="92670-255">Consigli</span><span class="sxs-lookup"><span data-stu-id="92670-255">Recommendations</span></span>

* <span data-ttu-id="92670-256">Progettare il contenuto per la distanza di visualizzazione ottimale di 2m.</span><span class="sxs-lookup"><span data-stu-id="92670-256">Design content for the optimal viewing distance of 2m.</span></span>
* <span data-ttu-id="92670-257">Impostare la distanza di rendering del ritaglio su 85cm con la dissolvenza del contenuto a partire da 1 milione.</span><span class="sxs-lookup"><span data-stu-id="92670-257">Set the clipping render distance to 85cm with fadeout of content starting at 1m.</span></span>
* <span data-ttu-id="92670-258">Per gli ologrammi stazionari che necessitano di una visualizzazione più vicina, il piano di ridimensionamento deve essere non più vicino a 30cm e la dissolvenza dovrebbe iniziare da almeno 10 cm dal piano di ritaglio.</span><span class="sxs-lookup"><span data-stu-id="92670-258">For stationary holograms that need closer viewing, the clipping plane should be no closer than 30cm and fadeout should start at least 10cm away from the clipping plane.</span></span>

### <a name="resources"></a><span data-ttu-id="92670-259">Risorse</span><span class="sxs-lookup"><span data-stu-id="92670-259">Resources</span></span>

* [<span data-ttu-id="92670-260">Distanza di rendering</span><span class="sxs-lookup"><span data-stu-id="92670-260">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="92670-261">Punto focale in Unity</span><span class="sxs-lookup"><span data-stu-id="92670-261">Focus point in Unity</span></span>](focus-point-in-unity.md)
* [<span data-ttu-id="92670-262">Sperimentazione con scalabilità</span><span class="sxs-lookup"><span data-stu-id="92670-262">Experimenting with scale</span></span>](scale.md#experimenting-with-scale)
* [<span data-ttu-id="92670-263">Testo, dimensioni del carattere consigliate</span><span class="sxs-lookup"><span data-stu-id="92670-263">Text, Recommended font size</span></span>](typography.md#recommended-font-size)

## <a name="depth-switching"></a><span data-ttu-id="92670-264">Cambio di profondità</span><span class="sxs-lookup"><span data-stu-id="92670-264">Depth switching</span></span>

<span data-ttu-id="92670-265">Indipendentemente dalla visualizzazione della zona di problemi di comfort, l'utente può cambiare spesso o rapidamente tra gli oggetti focali vicini e lontani (inclusi gli ologrammi e il contenuto reale) può causare la fatica oculomotore e il disagio generale.</span><span class="sxs-lookup"><span data-stu-id="92670-265">Regardless of viewing zone of comfort issues, demands for the user to switch frequently or quickly between near and far focal objects (including holograms and real-world content) can lead to oculomotor fatigue, and general discomfort.</span></span>

### <a name="device-impact"></a><span data-ttu-id="92670-266">Effetti sul dispositivo</span><span class="sxs-lookup"><span data-stu-id="92670-266">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="92670-267"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="92670-267"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="92670-268"><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="92670-268"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="92670-269">✔️</span><span class="sxs-lookup"><span data-stu-id="92670-269">✔️</span></span></td>
        <td><span data-ttu-id="92670-270">✔️</span><span class="sxs-lookup"><span data-stu-id="92670-270">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="92670-271">Criteri di qualità</span><span class="sxs-lookup"><span data-stu-id="92670-271">Quality criteria</span></span>

|  <span data-ttu-id="92670-272">Consigliate</span><span class="sxs-lookup"><span data-stu-id="92670-272">Best</span></span>  |  <span data-ttu-id="92670-273">Soddisfi</span><span class="sxs-lookup"><span data-stu-id="92670-273">Meets</span></span> |  <span data-ttu-id="92670-274">Esito negativo</span><span class="sxs-lookup"><span data-stu-id="92670-274">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="92670-275">Cambio di profondità naturale o limitato che non determina una riattivazione non naturale dell'utente.</span><span class="sxs-lookup"><span data-stu-id="92670-275">Limited or natural depth switching that doesn’t cause the user to unnaturally refocus.</span></span> | <span data-ttu-id="92670-276">Cambio di profondità improvviso. si tratta di un elemento di base e progettato nell'esperienza dell'app o di un cambio di profondità improvviso causato da contenuto reale imprevisto.</span><span class="sxs-lookup"><span data-stu-id="92670-276">Abrupt depth switch this is core and designed into the app experience, or abrupt depth switch that is caused by unexpected real-world content.</span></span> | <span data-ttu-id="92670-277">Commutatore di profondità coerente o cambio di profondità improvviso non necessario o di base per l'esperienza dell'app.</span><span class="sxs-lookup"><span data-stu-id="92670-277">Consistent depth switch, or abrupt depth switching that isn’t necessary or core to the app experience.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="92670-278">Come misurare</span><span class="sxs-lookup"><span data-stu-id="92670-278">How to measure</span></span>

* <span data-ttu-id="92670-279">Se l'app richiede all'utente di modificare in modo coerente e/o modificare in modo brusco lo stato attivo, si verifica un problema di cambio di profondità.</span><span class="sxs-lookup"><span data-stu-id="92670-279">If the app requires the user to consistently and/or abruptly change depth focus, there is depth switching problem.</span></span>

### <a name="recommendations"></a><span data-ttu-id="92670-280">Consigli</span><span class="sxs-lookup"><span data-stu-id="92670-280">Recommendations</span></span>

* <span data-ttu-id="92670-281">Mantieni il contenuto primario in un piano focale coerente e assicurati che il piano di stabilizzazione corrisponda al piano focale.</span><span class="sxs-lookup"><span data-stu-id="92670-281">Keep primary content at a consistent focal plane and make sure the stabilization plane matches the focal plane.</span></span> <span data-ttu-id="92670-282">Ciò ridurrà l'affaticamento oculomotore e lo spostamento imprevisto dell'ologramma.</span><span class="sxs-lookup"><span data-stu-id="92670-282">This will alleviate oculomotor fatigue and unexpected hologram movement.</span></span>

### <a name="resources"></a><span data-ttu-id="92670-283">Risorse</span><span class="sxs-lookup"><span data-stu-id="92670-283">Resources</span></span>

* [<span data-ttu-id="92670-284">Distanza di rendering</span><span class="sxs-lookup"><span data-stu-id="92670-284">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="92670-285">Punto focale in Unity</span><span class="sxs-lookup"><span data-stu-id="92670-285">Focus point in Unity</span></span>](focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a><span data-ttu-id="92670-286">Uso del suono spaziale</span><span class="sxs-lookup"><span data-stu-id="92670-286">Use of spatial sound</span></span>

<span data-ttu-id="92670-287">In realtà mista di Windows, il motore audio fornisce il componente uditivo dell'esperienza di realtà mista simulando il suono 3D usando la direzione, la distanza e le simulazioni ambientali.</span><span class="sxs-lookup"><span data-stu-id="92670-287">In Windows Mixed Reality, the audio engine provides the aural component of the mixed reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="92670-288">L'uso di un suono spaziale in un'applicazione consente agli sviluppatori di collocare in modo convincente i suoni in uno spazio tridimensionale (Sphere) intorno all'utente.</span><span class="sxs-lookup"><span data-stu-id="92670-288">Using spatial sound in an application allows developers to convincingly place sounds in a 3 dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="92670-289">Questi suoni sembreranno come se provenissero da oggetti fisici reali o dagli ologrammi della realtà mista nell'ambiente dell'utente.</span><span class="sxs-lookup"><span data-stu-id="92670-289">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="92670-290">Il suono spaziale è uno strumento potente per l'immersione, l'accessibilità e la progettazione dell'esperienza utente nelle applicazioni di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="92670-290">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

### <a name="device-impact"></a><span data-ttu-id="92670-291">Effetti sul dispositivo</span><span class="sxs-lookup"><span data-stu-id="92670-291">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="92670-292"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="92670-292"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="92670-293"><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="92670-293"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="92670-294">✔️</span><span class="sxs-lookup"><span data-stu-id="92670-294">✔️</span></span></td>
        <td><span data-ttu-id="92670-295">✔️</span><span class="sxs-lookup"><span data-stu-id="92670-295">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="92670-296">Criteri di qualità</span><span class="sxs-lookup"><span data-stu-id="92670-296">Quality criteria</span></span>

|  <span data-ttu-id="92670-297">Consigliate</span><span class="sxs-lookup"><span data-stu-id="92670-297">Best</span></span>  |  <span data-ttu-id="92670-298">Soddisfi</span><span class="sxs-lookup"><span data-stu-id="92670-298">Meets</span></span> |  <span data-ttu-id="92670-299">Esito negativo</span><span class="sxs-lookup"><span data-stu-id="92670-299">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="92670-300">Il suono è con spazialità logica e l'esperienza utente utilizza in modo appropriato il suono per facilitare l'individuazione degli oggetti e il feedback degli utenti.</span><span class="sxs-lookup"><span data-stu-id="92670-300">Sound is logically spatialized, and the UX appropriately uses sound to assist with object discovery and user feedback.</span></span> <span data-ttu-id="92670-301">Il suono è naturale e pertinente per gli oggetti e normalizzato in tutto lo scenario.</span><span class="sxs-lookup"><span data-stu-id="92670-301">Sound is natural and relevant to objects and normalized across the scenario.</span></span> | <span data-ttu-id="92670-302">L'audio spaziale viene utilizzato in modo appropriato per ottenere la credibilità, ma mancante come mezzo per facilitare il feedback degli utenti e l'individuabilità.</span><span class="sxs-lookup"><span data-stu-id="92670-302">Spatial audio is used appropriately for believability but missing as means to help with user feedback and discoverability.</span></span> | <span data-ttu-id="92670-303">Il suono non viene spaziato come previsto e/o non è presente alcun suono per assistere l'utente all'interno dell'esperienza utente.</span><span class="sxs-lookup"><span data-stu-id="92670-303">Sound is not spatialized as expected, and/or lack of sound to assist user within the UX.</span></span> <span data-ttu-id="92670-304">O l'audio spaziale non è stato considerato o usato nella progettazione dello scenario.</span><span class="sxs-lookup"><span data-stu-id="92670-304">Or spatial audio was not considered or used in the design of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="92670-305">Come misurare</span><span class="sxs-lookup"><span data-stu-id="92670-305">How to measure</span></span>

* <span data-ttu-id="92670-306">In generale, i suoni rilevanti devono emettere da ologrammi di destinazione (ad esempio, il suono di corteccia proveniente dal cane olografico).</span><span class="sxs-lookup"><span data-stu-id="92670-306">In general, relevant sounds should emit from target holograms (eg., bark sound coming from holographic dog.)</span></span>
* <span data-ttu-id="92670-307">I segnali acustici devono essere usati in tutta l'esperienza utente per aiutare gli utenti a ricevere commenti e suggerimenti o a conoscere le azioni all'esterno del frame olografico.</span><span class="sxs-lookup"><span data-stu-id="92670-307">Sound cues should be used throughout the UX to assist the user with feedback or awareness of actions outside the holographic frame.</span></span>

### <a name="recommendations"></a><span data-ttu-id="92670-308">Consigli</span><span class="sxs-lookup"><span data-stu-id="92670-308">Recommendations</span></span>

* <span data-ttu-id="92670-309">Utilizzare l'audio spaziale per supportare l'individuazione oggetti e le interfacce utente.</span><span class="sxs-lookup"><span data-stu-id="92670-309">Use spatial audio to assist with object discovery and user interfaces.</span></span>
* <span data-ttu-id="92670-310">I suoni reali funzionano meglio rispetto alla sintesi o al suono non naturale.</span><span class="sxs-lookup"><span data-stu-id="92670-310">Real sounds work better than synthesize or unnatural sound.</span></span>
* <span data-ttu-id="92670-311">La maggior parte dei suoni deve essere spaziali.</span><span class="sxs-lookup"><span data-stu-id="92670-311">Most sounds should be spatialized.</span></span>
* <span data-ttu-id="92670-312">Evitare gli emettitori invisibile.</span><span class="sxs-lookup"><span data-stu-id="92670-312">Avoid invisible emitters.</span></span>
* <span data-ttu-id="92670-313">Evitare la maschera spaziale.</span><span class="sxs-lookup"><span data-stu-id="92670-313">Avoid spatial masking.</span></span>
* <span data-ttu-id="92670-314">Normalizzare tutti i suoni.</span><span class="sxs-lookup"><span data-stu-id="92670-314">Normalize all sounds.</span></span>

### <a name="resources"></a><span data-ttu-id="92670-315">Risorse</span><span class="sxs-lookup"><span data-stu-id="92670-315">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="92670-316">Documentazione</span><span class="sxs-lookup"><span data-stu-id="92670-316">Documentation</span></span>

* [<span data-ttu-id="92670-317">Audio spaziale</span><span class="sxs-lookup"><span data-stu-id="92670-317">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="92670-318">Progettazione dell'audio spaziale</span><span class="sxs-lookup"><span data-stu-id="92670-318">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="92670-319">Audio spaziale in Unity</span><span class="sxs-lookup"><span data-stu-id="92670-319">Spatial sound in Unity</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="92670-320">Case Study, audio spaziale per HoloTour</span><span class="sxs-lookup"><span data-stu-id="92670-320">Case study, Spatial sound for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="92670-321">Case Study, uso del suono spaziale in RoboRaid</span><span class="sxs-lookup"><span data-stu-id="92670-321">Case study, Using spatial sound in RoboRaid</span></span>](case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="92670-322">Strumenti ed esercitazioni</span><span class="sxs-lookup"><span data-stu-id="92670-322">Tools and tutorials</span></span>

* [<span data-ttu-id="92670-323">MR Spatial 220: audio spaziale</span><span class="sxs-lookup"><span data-stu-id="92670-323">MR Spatial 220: Spatial sound</span></span>](holograms-220.md)
* [<span data-ttu-id="92670-324">MRToolkit, audio spaziale</span><span class="sxs-lookup"><span data-stu-id="92670-324">MRToolkit, Spatial Audio</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a><span data-ttu-id="92670-325">Concentrarsi sui limiti dei frame olografici (FOV)</span><span class="sxs-lookup"><span data-stu-id="92670-325">Focus on holographic frame (FOV) boundaries</span></span>

<span data-ttu-id="92670-326">L'esperienza utente ben progettata può creare e gestire un contesto utile dell'ambiente virtuale che si estende intorno agli utenti.</span><span class="sxs-lookup"><span data-stu-id="92670-326">Well-designed user experiences can create and maintain useful context of the virtual environment that extends around the users.</span></span> <span data-ttu-id="92670-327">Attenuare l'effetto dei limiti di FOV implica una progettazione accurata della scalabilità del contenuto e del contesto, l'utilizzo di audio spaziale, i sistemi di linee guida e la posizione dell'utente.</span><span class="sxs-lookup"><span data-stu-id="92670-327">Mitigating the effect of the FOV boundaries involves a thoughtful design of content scale and context, use of spatial audio, guidance systems, and the user's position.</span></span> <span data-ttu-id="92670-328">Se questa operazione è stata eseguita correttamente, l'utente risulterà meno disaccoppiato dai limiti di FOV, pur avendo un'esperienza di app comoda.</span><span class="sxs-lookup"><span data-stu-id="92670-328">If done right, the user will feel less impaired by the FOV boundaries while having a comfortable app experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="92670-329">Effetti sul dispositivo</span><span class="sxs-lookup"><span data-stu-id="92670-329">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="92670-330"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="92670-330"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="92670-331"><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="92670-331"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="92670-332">✔️</span><span class="sxs-lookup"><span data-stu-id="92670-332">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="92670-333">Criteri di qualità</span><span class="sxs-lookup"><span data-stu-id="92670-333">Quality criteria</span></span>

|  <span data-ttu-id="92670-334">Consigliate</span><span class="sxs-lookup"><span data-stu-id="92670-334">Best</span></span>  |  <span data-ttu-id="92670-335">Soddisfi</span><span class="sxs-lookup"><span data-stu-id="92670-335">Meets</span></span> |  <span data-ttu-id="92670-336">Esito negativo</span><span class="sxs-lookup"><span data-stu-id="92670-336">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="92670-337">L'utente non perde mai il contesto e la visualizzazione è confortevole.</span><span class="sxs-lookup"><span data-stu-id="92670-337">User never loses context and viewing is comfortable.</span></span> <span data-ttu-id="92670-338">Per gli oggetti di grandi dimensioni viene fornita assistenza del contesto.</span><span class="sxs-lookup"><span data-stu-id="92670-338">Context assistance is provided for large objects.</span></span> <span data-ttu-id="92670-339">L'individuabilità e la visualizzazione delle linee guida vengono fornite per gli oggetti esterni al frame.</span><span class="sxs-lookup"><span data-stu-id="92670-339">Discoverability and viewing guidance is provided for objects outside the frame.</span></span> <span data-ttu-id="92670-340">In generale, la progettazione del movimento e la scala degli ologrammi sono appropriate per un'esperienza di visualizzazione confortevole.</span><span class="sxs-lookup"><span data-stu-id="92670-340">In general, motion design and scale of the holograms are appropriate for a comfortable viewing experience.</span></span> | <span data-ttu-id="92670-341">L'utente non perde mai il contesto, ma potrebbe essere necessario un movimento del collo aggiuntivo in situazioni limitate.</span><span class="sxs-lookup"><span data-stu-id="92670-341">User never loses context, but extra neck motion may be required in limited situations.</span></span> <span data-ttu-id="92670-342">In situazioni limitate la scalabilità induce gli ologrammi a suddividere il frame verticale o orizzontale causando un movimento del collo per visualizzare gli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="92670-342">In limited situations scale causes holograms to break either the vertical or horizontal frame causing some neck motion to view holograms.</span></span> | <span data-ttu-id="92670-343">È necessario che l'utente perda il contesto e/o il movimento del collo coerente per visualizzare gli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="92670-343">User likely to lose context and/or consistent neck motion is required to view holograms.</span></span> <span data-ttu-id="92670-344">Nessuna guida al contesto per oggetti olografici di grandi dimensioni, spostamento di oggetti facili da perdere al di fuori del frame senza alcuna indicazione di individuabilità, o ologrammi alti richiede un movimento del collo normale per la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="92670-344">No context guidance for large holographic objects, moving objects easy to lose outside the frame with no discoverability guidance, or tall holograms requires regular neck motion to view.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="92670-345">Come misurare</span><span class="sxs-lookup"><span data-stu-id="92670-345">How to measure</span></span>

* <span data-ttu-id="92670-346">Il contesto di un ologramma (grande) viene perso o non è compreso perché viene troncato ai limiti.</span><span class="sxs-lookup"><span data-stu-id="92670-346">Context for a (large) hologram is lost or not understood due to being clipped at the boundaries.</span></span>
* <span data-ttu-id="92670-347">La posizione degli ologrammi è difficile da trovare a causa dell'assenza di direttori di attenzione o contenuti che si spostano rapidamente all'interno e all'esterno del frame olografico.</span><span class="sxs-lookup"><span data-stu-id="92670-347">Location of holograms are hard to find due to the lack of attention directors or content that rapidly moves in and out of the holographic frame.</span></span>
* <span data-ttu-id="92670-348">Per visualizzare completamente un ologramma, è necessario che lo scenario sia normale e ripetitivo, in modo da ottenere una riduzione del collo.</span><span class="sxs-lookup"><span data-stu-id="92670-348">Scenario requires regular and repetitive up and down head motion to fully see a hologram resulting in neck fatigue.</span></span>

### <a name="recommendations"></a><span data-ttu-id="92670-349">Consigli</span><span class="sxs-lookup"><span data-stu-id="92670-349">Recommendations</span></span>

* <span data-ttu-id="92670-350">Inizia l'esperienza con piccoli oggetti che si adattano a FOV, quindi passa con segnali visivi a versioni più grandi.</span><span class="sxs-lookup"><span data-stu-id="92670-350">Start the experience with small objects that fit the FOV, then transition with visual cues to larger versions.</span></span>
* <span data-ttu-id="92670-351">Usare i direttori audio e di attenzione spaziali per aiutare l'utente a trovare contenuto esterno a FOV.</span><span class="sxs-lookup"><span data-stu-id="92670-351">Use spatial audio and attention directors to help the user find content that is outside the FOV.</span></span>
* <span data-ttu-id="92670-352">Per quanto possibile, evitare gli ologrammi che ritagliano verticalmente il FOV.</span><span class="sxs-lookup"><span data-stu-id="92670-352">As much as possible, avoid holograms that vertically clip the FOV.</span></span>
* <span data-ttu-id="92670-353">Fornire all'utente informazioni aggiuntive in-app per una migliore visualizzazione del percorso.</span><span class="sxs-lookup"><span data-stu-id="92670-353">Provide the user with in-app guidance for best viewing location.</span></span>

### <a name="resources"></a><span data-ttu-id="92670-354">Risorse</span><span class="sxs-lookup"><span data-stu-id="92670-354">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="92670-355">Documentazione</span><span class="sxs-lookup"><span data-stu-id="92670-355">Documentation</span></span>

* [<span data-ttu-id="92670-356">Frame olografico</span><span class="sxs-lookup"><span data-stu-id="92670-356">Holographic frame</span></span>](holographic-frame.md)
* [<span data-ttu-id="92670-357">Case Study, informazioni sulla progettazione dell'interazione e dell'interfaccia utente di HoloStudio</span><span class="sxs-lookup"><span data-stu-id="92670-357">Case Study, HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [<span data-ttu-id="92670-358">Scala di oggetti e ambienti</span><span class="sxs-lookup"><span data-stu-id="92670-358">Scale of objects and environments</span></span>](scale.md)
* [<span data-ttu-id="92670-359">Cursori, segnali visivi</span><span class="sxs-lookup"><span data-stu-id="92670-359">Cursors, Visual cues</span></span>](cursors.md#visual-cues)

#### <a name="external-references"></a><span data-ttu-id="92670-360">Riferimenti esterni</span><span class="sxs-lookup"><span data-stu-id="92670-360">External references</span></span>

* [<span data-ttu-id="92670-361">Molto ADO sulla FOV</span><span class="sxs-lookup"><span data-stu-id="92670-361">Much ado about the FOV</span></span>](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a><span data-ttu-id="92670-362">Il contenuto reagisce alla posizione dell'utente</span><span class="sxs-lookup"><span data-stu-id="92670-362">Content reacts to user position</span></span>

<span data-ttu-id="92670-363">Gli ologrammi dovrebbero rispondere alla posizione dell'utente approssimativamente nello stesso modo in cui fanno gli oggetti "reali".</span><span class="sxs-lookup"><span data-stu-id="92670-363">Holograms should react to the user position in roughly the same ways that "real" objects do.</span></span> <span data-ttu-id="92670-364">Una considerazione di progettazione notevole è rappresentata dagli elementi dell'interfaccia utente che non possono necessariamente presupporre che la posizione di un utente sia stazionaria e adattata al movimento dell'utente.</span><span class="sxs-lookup"><span data-stu-id="92670-364">A notable design consideration is UI elements that can't necessarily assume a user's position is stationary and adapt to the user's motion.</span></span> <span data-ttu-id="92670-365">La progettazione di un'app che si adatta correttamente alla posizione utente creerà un'esperienza più credibile e ne renderà più semplice l'uso.</span><span class="sxs-lookup"><span data-stu-id="92670-365">Designing an app that correctly adapts to user position will create a more believable experience and make it easier to use.</span></span>

### <a name="device-impact"></a><span data-ttu-id="92670-366">Effetti sul dispositivo</span><span class="sxs-lookup"><span data-stu-id="92670-366">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="92670-367"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="92670-367"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="92670-368"><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="92670-368"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="92670-369">✔️</span><span class="sxs-lookup"><span data-stu-id="92670-369">✔️</span></span></td>
        <td><span data-ttu-id="92670-370">✔️</span><span class="sxs-lookup"><span data-stu-id="92670-370">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="92670-371">Criteri di qualità</span><span class="sxs-lookup"><span data-stu-id="92670-371">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="92670-372">Consigliate</span><span class="sxs-lookup"><span data-stu-id="92670-372">Best</span></span> </td><td> <span data-ttu-id="92670-373">Il contenuto e l'interfaccia utente si adattano a posizioni utente che consentono all'utente di interagire naturalmente con il contenuto nell'ambito del movimento utente previsto.</span><span class="sxs-lookup"><span data-stu-id="92670-373">Content and UI adapt to user positions allowing user to naturally interact with content within the scope of expected user movement.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="92670-374">Soddisfi</span><span class="sxs-lookup"><span data-stu-id="92670-374">Meets</span></span> </td><td> <span data-ttu-id="92670-375">L'interfaccia utente si adatta alla posizione dell'utente, ma può impedire la visualizzazione del contenuto della chiave che richiede all'utente di modificare la posizione.</span><span class="sxs-lookup"><span data-stu-id="92670-375">UI adapts to the user position, but may impede the view of key content requiring the user to adjust their position.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="92670-376">Esito negativo</span><span class="sxs-lookup"><span data-stu-id="92670-376">Fail</span></span> </td><td><ol>
<li><span data-ttu-id="92670-377">Gli elementi dell'interfaccia utente vengono persi o bloccati durante lo spostamento, facendo sì che l'utente ritorni in modo non naturale ai controlli (o trova).</span><span class="sxs-lookup"><span data-stu-id="92670-377">UI elements are lost or locked during movement causing user to unnaturally return to (or find) controls.</span></span></li><li><span data-ttu-id="92670-378">Gli elementi dell'interfaccia utente limitano la visualizzazione del contenuto primario.</span><span class="sxs-lookup"><span data-stu-id="92670-378">UI elements limit the view of primary content.</span></span></li><li><span data-ttu-id="92670-379">Lo spostamento dell'interfaccia utente non è ottimizzato per la visualizzazione della distanza e del momento in particolare con elementi dell'interfaccia utente con <a href="billboarding-and-tag-along.md">tag lungo</a> .</span><span class="sxs-lookup"><span data-stu-id="92670-379">UI movement is not optimized for viewing distance and momentum particularly with <a href="billboarding-and-tag-along.md">tag-along</a> UI elements.</span></span></li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="92670-380">Come misurare</span><span class="sxs-lookup"><span data-stu-id="92670-380">How to measure</span></span>

* <span data-ttu-id="92670-381">Tutte le misurazioni devono essere eseguite in un ambito ragionevole dello scenario.</span><span class="sxs-lookup"><span data-stu-id="92670-381">All measurements should be done within a reasonable scope of the scenario.</span></span> <span data-ttu-id="92670-382">Sebbene lo spostamento dell'utente possa variare, non provare a ingannare l'app con lo spostamento estremo dell'utente.</span><span class="sxs-lookup"><span data-stu-id="92670-382">While user movement will vary, don’t try to trick the app with extreme user movement.</span></span>
* <span data-ttu-id="92670-383">Per gli elementi dell'interfaccia utente, i controlli pertinenti dovrebbero essere disponibili indipendentemente dallo spostamento dell'utente.</span><span class="sxs-lookup"><span data-stu-id="92670-383">For UI elements, relevant controls should be available regardless of user movement.</span></span> <span data-ttu-id="92670-384">Se, ad esempio, l'utente Visualizza e aggira una mappa 3D con lo zoom, il controllo zoom dovrebbe essere prontamente disponibile per l'utente indipendentemente dalla posizione.</span><span class="sxs-lookup"><span data-stu-id="92670-384">For example, if the user is viewing and walking around a 3D map with zoom, the zoom control should be readily available to the user regardless of location.</span></span>

### <a name="recommendations"></a><span data-ttu-id="92670-385">Consigli</span><span class="sxs-lookup"><span data-stu-id="92670-385">Recommendations</span></span>

* <span data-ttu-id="92670-386">L'utente è la fotocamera e controlla lo spostamento.</span><span class="sxs-lookup"><span data-stu-id="92670-386">The user is the camera and they control the movement.</span></span> <span data-ttu-id="92670-387">Consentire l'unità.</span><span class="sxs-lookup"><span data-stu-id="92670-387">Let them drive.</span></span>
* <span data-ttu-id="92670-388">Prendere in considerazione il tabellone per i sistemi di testo e di menu che altrimenti sarebbero bloccati o nascosti se un utente dovesse spostarsi.</span><span class="sxs-lookup"><span data-stu-id="92670-388">Consider billboarding for text and menuing systems that would otherwise be world-locked or obscured if a user were to move around.</span></span>
* <span data-ttu-id="92670-389">Usare tag-along per il contenuto che deve seguire l'utente, consentendo allo stesso tempo all'utente di vedere cosa è davanti a essi.</span><span class="sxs-lookup"><span data-stu-id="92670-389">Use tag-along for content that needs to follow the user while still allowing the user to see what is in front of them.</span></span>

### <a name="resources"></a><span data-ttu-id="92670-390">Risorse</span><span class="sxs-lookup"><span data-stu-id="92670-390">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="92670-391">Documentazione</span><span class="sxs-lookup"><span data-stu-id="92670-391">Documentation</span></span>

* [<span data-ttu-id="92670-392">Progettazione interazione</span><span class="sxs-lookup"><span data-stu-id="92670-392">Interaction design</span></span>](hologram.md)
* [<span data-ttu-id="92670-393">Colore, luce e materiale</span><span class="sxs-lookup"><span data-stu-id="92670-393">Color, light, and material</span></span>](color,-light-and-materials.md)
* [<span data-ttu-id="92670-394">Billboarding e tag-along</span><span class="sxs-lookup"><span data-stu-id="92670-394">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="92670-395">Interazioni istintive</span><span class="sxs-lookup"><span data-stu-id="92670-395">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="92670-396">Auto-Motion e locomozione utente</span><span class="sxs-lookup"><span data-stu-id="92670-396">Self-motion and user locomotion</span></span>](comfort.md#self-motion-and-user-locomotion)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="92670-397">Strumenti ed esercitazioni</span><span class="sxs-lookup"><span data-stu-id="92670-397">Tools and tutorials</span></span>

* [<span data-ttu-id="92670-398">Input MR 210: sguardo</span><span class="sxs-lookup"><span data-stu-id="92670-398">MR Input 210: Gaze</span></span>](holograms-210.md)

## <a name="input-interaction-clarity"></a><span data-ttu-id="92670-399">Chiarezza interazione input</span><span class="sxs-lookup"><span data-stu-id="92670-399">Input interaction clarity</span></span>

<span data-ttu-id="92670-400">La chiarezza dell'interazione di input è essenziale per l'usabilità di un'app e include coerenza di input, accessibilità, individuabilità dei metodi di interazione.</span><span class="sxs-lookup"><span data-stu-id="92670-400">Input interaction clarity is critical to an app's usability and includes input consistency, approachability, discoverability of interaction methods.</span></span> <span data-ttu-id="92670-401">L'utente deve essere in grado di usare interazioni comuni a livello di piattaforma senza riapprendere.</span><span class="sxs-lookup"><span data-stu-id="92670-401">User should be able to use platform-wide common interactions without relearning.</span></span> <span data-ttu-id="92670-402">Se l'app ha un input personalizzato, dovrebbe essere chiaramente comunicata e dimostrata.</span><span class="sxs-lookup"><span data-stu-id="92670-402">If the app has custom input, it should be clearly communicated and demonstrated.</span></span>

### <a name="device-impact"></a><span data-ttu-id="92670-403">Effetti sul dispositivo</span><span class="sxs-lookup"><span data-stu-id="92670-403">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="92670-404"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="92670-404"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="92670-405"><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="92670-405"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="92670-406">✔️</span><span class="sxs-lookup"><span data-stu-id="92670-406">✔️</span></span></td>
        <td><span data-ttu-id="92670-407">✔️</span><span class="sxs-lookup"><span data-stu-id="92670-407">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="92670-408">Criteri di qualità</span><span class="sxs-lookup"><span data-stu-id="92670-408">Quality criteria</span></span>

|  <span data-ttu-id="92670-409">Consigliate</span><span class="sxs-lookup"><span data-stu-id="92670-409">Best</span></span>  |  <span data-ttu-id="92670-410">Soddisfi</span><span class="sxs-lookup"><span data-stu-id="92670-410">Meets</span></span> |  <span data-ttu-id="92670-411">Esito negativo</span><span class="sxs-lookup"><span data-stu-id="92670-411">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="92670-412">I metodi di interazione di input sono coerenti con le [linee guida](interaction-fundamentals.md)fornite dalla realtà mista Windows.</span><span class="sxs-lookup"><span data-stu-id="92670-412">Input interaction methods are consistent with Windows Mixed Reality provided [guidance](interaction-fundamentals.md).</span></span> <span data-ttu-id="92670-413">Qualsiasi input personalizzato non deve essere ridondante con l'input standard (usare invece l'interazione standard) e deve essere chiaramente comunicato e dimostrato all'utente.</span><span class="sxs-lookup"><span data-stu-id="92670-413">Any custom input should not be redundant with standard input (rather use standard interaction) and must be clearly communicated and demonstrated to the user.</span></span> | <span data-ttu-id="92670-414">Analogamente al migliore, ma gli input personalizzati sono ridondanti con i metodi di input standard.</span><span class="sxs-lookup"><span data-stu-id="92670-414">Similar to best, but custom inputs are redundant with standard input methods.</span></span> <span data-ttu-id="92670-415">L'utente può comunque raggiungere l'obiettivo e progredire nell'esperienza dell'app.</span><span class="sxs-lookup"><span data-stu-id="92670-415">User can still achieve the goal and progress through the app experience.</span></span> | <span data-ttu-id="92670-416">Difficile comprensione del metodo di input o del mapping dei pulsanti.</span><span class="sxs-lookup"><span data-stu-id="92670-416">Difficult to understand input method or button mapping.</span></span> <span data-ttu-id="92670-417">L'input è molto personalizzato, non supporta l'input standard, nessuna istruzione o probabilmente causa problemi di affaticamento e comfort.</span><span class="sxs-lookup"><span data-stu-id="92670-417">Input is heavily customized, does not support standard input, no instructions, or likely to cause fatigue and comfort issues.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="92670-418">Come misurare</span><span class="sxs-lookup"><span data-stu-id="92670-418">How to measure</span></span>

* <span data-ttu-id="92670-419">L'app usa [metodi di input standard coerenti.](interaction-fundamentals.md)</span><span class="sxs-lookup"><span data-stu-id="92670-419">The app uses consistent [standard input methods.](interaction-fundamentals.md)</span></span>
* <span data-ttu-id="92670-420">Se l'app ha un input personalizzato, viene chiaramente comunicata tramite:</span><span class="sxs-lookup"><span data-stu-id="92670-420">If the app has custom input, it is clearly communicated through:</span></span>
* <span data-ttu-id="92670-421">Esperienza di prima esecuzione</span><span class="sxs-lookup"><span data-stu-id="92670-421">First-run experience</span></span>
* <span data-ttu-id="92670-422">Schermate introduttive</span><span class="sxs-lookup"><span data-stu-id="92670-422">Introductory screens</span></span>
* <span data-ttu-id="92670-423">Descrizioni comandi</span><span class="sxs-lookup"><span data-stu-id="92670-423">Tooltips</span></span>
* <span data-ttu-id="92670-424">Coach mano</span><span class="sxs-lookup"><span data-stu-id="92670-424">Hand coach</span></span>
* <span data-ttu-id="92670-425">Sezione della Guida</span><span class="sxs-lookup"><span data-stu-id="92670-425">Help section</span></span>
* <span data-ttu-id="92670-426">Voice over</span><span class="sxs-lookup"><span data-stu-id="92670-426">Voice over</span></span>

### <a name="recommendations"></a><span data-ttu-id="92670-427">Consigli</span><span class="sxs-lookup"><span data-stu-id="92670-427">Recommendations</span></span>

* <span data-ttu-id="92670-428">Usare i metodi di input standard quando possibile.</span><span class="sxs-lookup"><span data-stu-id="92670-428">Use standard input methods whenever possible.</span></span>
* <span data-ttu-id="92670-429">Fornire dimostrazioni, esercitazioni e descrizioni comandi per metodi di input non standard.</span><span class="sxs-lookup"><span data-stu-id="92670-429">Provide demonstrations, tutorials, and tooltips for non-standard input methods.</span></span>
* <span data-ttu-id="92670-430">Usare un modello di interazione coerente nell'app.</span><span class="sxs-lookup"><span data-stu-id="92670-430">Use a consistent interaction model throughout the app.</span></span>

### <a name="resources"></a><span data-ttu-id="92670-431">Risorse</span><span class="sxs-lookup"><span data-stu-id="92670-431">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="92670-432">Documentazione</span><span class="sxs-lookup"><span data-stu-id="92670-432">Documentation</span></span>

* [<span data-ttu-id="92670-433">Interazioni istintive</span><span class="sxs-lookup"><span data-stu-id="92670-433">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="92670-434">Oggetti interagibili</span><span class="sxs-lookup"><span data-stu-id="92670-434">Interactable objects</span></span>](interactable-object.md)
* [<span data-ttu-id="92670-435">Puntamento con la testa e attesa</span><span class="sxs-lookup"><span data-stu-id="92670-435">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="92670-436">Cursori</span><span class="sxs-lookup"><span data-stu-id="92670-436">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="92670-437">Comodità e sguardo</span><span class="sxs-lookup"><span data-stu-id="92670-437">Comfort and gaze</span></span>](comfort.md#gaze-direction)
* [<span data-ttu-id="92670-438">Input vocale</span><span class="sxs-lookup"><span data-stu-id="92670-438">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="92670-439">Controller del movimento</span><span class="sxs-lookup"><span data-stu-id="92670-439">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="92670-440">Guida alla conversione dell'input per Unity</span><span class="sxs-lookup"><span data-stu-id="92670-440">Input porting guide for Unity</span></span>](input-porting-guide-for-unity.md)
* [<span data-ttu-id="92670-441">Input da tastiera in Unity</span><span class="sxs-lookup"><span data-stu-id="92670-441">Keyboard input in Unity</span></span>](keyboard-input-in-unity.md)
* [<span data-ttu-id="92670-442">Sguardo fisso in Unity</span><span class="sxs-lookup"><span data-stu-id="92670-442">Gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="92670-443">Movimenti e controller del movimento in Unity</span><span class="sxs-lookup"><span data-stu-id="92670-443">Gestures and motion controllers in Unity</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="92670-444">Input vocale in Unity</span><span class="sxs-lookup"><span data-stu-id="92670-444">Voice input in Unity</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="92670-445">Input da tastiera, mouse e controller in DirectX</span><span class="sxs-lookup"><span data-stu-id="92670-445">Keyboard, mouse, and controller input in DirectX</span></span>](keyboard,-mouse,-and-controller-input-in-directx.md)
* [<span data-ttu-id="92670-446">Puntamento con la testa e sguardo fisso in DirectX</span><span class="sxs-lookup"><span data-stu-id="92670-446">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="92670-447">Mani e controller del movimento in DirectX</span><span class="sxs-lookup"><span data-stu-id="92670-447">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="92670-448">Input vocale in DirectX</span><span class="sxs-lookup"><span data-stu-id="92670-448">Voice input in DirectX</span></span>](voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="92670-449">Strumenti ed esercitazioni</span><span class="sxs-lookup"><span data-stu-id="92670-449">Tools and tutorials</span></span>

* [<span data-ttu-id="92670-450">Case Study: ricerca di più personal computing</span><span class="sxs-lookup"><span data-stu-id="92670-450">Case study: The pursuit of more personal computing</span></span>](case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [<span data-ttu-id="92670-451">Cast Study: apprendimento dell'interfaccia utente e della progettazione dell'interazione HoloStudio</span><span class="sxs-lookup"><span data-stu-id="92670-451">Cast study: HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [<span data-ttu-id="92670-452">App di esempio: tabella periodica degli elementi</span><span class="sxs-lookup"><span data-stu-id="92670-452">Sample app: Periodic table of the elements</span></span>](periodic-table-of-the-elements.md)
* [<span data-ttu-id="92670-453">App di esempio: modulo Lunar</span><span class="sxs-lookup"><span data-stu-id="92670-453">Sample app: Lunar module</span></span>](lunar-module.md)
* [<span data-ttu-id="92670-454">Input MR 210: sguardo</span><span class="sxs-lookup"><span data-stu-id="92670-454">MR Input 210: Gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="92670-455">Input MR 211: movimenti</span><span class="sxs-lookup"><span data-stu-id="92670-455">MR Input 211: Gestures</span></span>](holograms-211.md)
* [<span data-ttu-id="92670-456">Input di MR 212: Voice</span><span class="sxs-lookup"><span data-stu-id="92670-456">MR Input 212: Voice</span></span>](holograms-212.md)

## <a name="interactable-objects"></a><span data-ttu-id="92670-457">Oggetti interagibili</span><span class="sxs-lookup"><span data-stu-id="92670-457">Interactable objects</span></span>

<span data-ttu-id="92670-458">Un pulsante è a lungo una metafora usata per attivare un evento nel mondo astratto 2D.</span><span class="sxs-lookup"><span data-stu-id="92670-458">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="92670-459">Nel mondo della realtà mista tridimensionale, non dobbiamo più limitarci a questo mondo dell'astrazione.</span><span class="sxs-lookup"><span data-stu-id="92670-459">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="92670-460">Qualsiasi elemento può essere un oggetto interagibile che attiva un evento.</span><span class="sxs-lookup"><span data-stu-id="92670-460">Anything can be an Interactable object that triggers an event.</span></span> <span data-ttu-id="92670-461">Un oggetto interactabile può essere rappresentato da qualsiasi elemento da un caffè della tabella a un pallone in aria.</span><span class="sxs-lookup"><span data-stu-id="92670-461">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="92670-462">Indipendentemente dal modulo, gli oggetti interagiscono devono essere chiaramente riconoscibili dall'utente tramite segnali visivi e audio.</span><span class="sxs-lookup"><span data-stu-id="92670-462">Regardless of the form, interactable objects should be clearly recognizable by the user through visual and audio cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="92670-463">Effetti sul dispositivo</span><span class="sxs-lookup"><span data-stu-id="92670-463">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="92670-464"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="92670-464"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="92670-465"><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="92670-465"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="92670-466">✔️</span><span class="sxs-lookup"><span data-stu-id="92670-466">✔️</span></span></td>
        <td><span data-ttu-id="92670-467">✔️</span><span class="sxs-lookup"><span data-stu-id="92670-467">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="92670-468">Criteri di qualità</span><span class="sxs-lookup"><span data-stu-id="92670-468">Quality criteria</span></span>

|  <span data-ttu-id="92670-469">Consigliate</span><span class="sxs-lookup"><span data-stu-id="92670-469">Best</span></span>  |  <span data-ttu-id="92670-470">Soddisfi</span><span class="sxs-lookup"><span data-stu-id="92670-470">Meets</span></span> |  <span data-ttu-id="92670-471">Esito negativo</span><span class="sxs-lookup"><span data-stu-id="92670-471">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="92670-472">Indipendentemente dalla forma, gli oggetti interagibili sono riconoscibili tramite segnali visivi e audio in tre stati: inattivo, di destinazione e selezionato.</span><span class="sxs-lookup"><span data-stu-id="92670-472">Regardless of form, interactable objects are recognizable through visual and audio cues across three states: idle, targeted, and selected.</span></span> <span data-ttu-id="92670-473">"Vedilo, supponiamo che" sia chiaro e costantemente usato in tutta l'esperienza.</span><span class="sxs-lookup"><span data-stu-id="92670-473">"See it, say it" is clear and consistently used throughout the experience.</span></span> <span data-ttu-id="92670-474">Gli oggetti vengono ridimensionati e distribuiti per consentire la destinazione senza errori.</span><span class="sxs-lookup"><span data-stu-id="92670-474">Objects are scaled and distributed to allow for error free targeting.</span></span> | <span data-ttu-id="92670-475">L'utente può riconoscere l'oggetto come interagisci tramite commenti audio o visivi e può fare riferimento all'oggetto e attivarlo.</span><span class="sxs-lookup"><span data-stu-id="92670-475">User can recognize object as interactable through audio or visual feedback, and can target and activate the object.</span></span> | <span data-ttu-id="92670-476">Dato che non sono presenti suggerimenti visivi o audio, l'utente non può riconoscere un oggetto interagibile.</span><span class="sxs-lookup"><span data-stu-id="92670-476">Given no visual or audio cues, user cannot recognize an interactable object.</span></span> <span data-ttu-id="92670-477">Le interazioni sono soggette a errori a causa della scala o della distanza degli oggetti tra oggetti.</span><span class="sxs-lookup"><span data-stu-id="92670-477">Interactions are error prone due to object scale or distance between objects.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="92670-478">Come misurare</span><span class="sxs-lookup"><span data-stu-id="92670-478">How to measure</span></span>

* <span data-ttu-id="92670-479">Gli oggetti interagibili sono riconoscibili come ' interactable '; inclusi i pulsanti, i menu e il contenuto specifico dell'app.</span><span class="sxs-lookup"><span data-stu-id="92670-479">Interactable objects are recognizable as 'interactable'; including buttons, menus, and app specific content.</span></span> <span data-ttu-id="92670-480">Come regola empirica, è necessario un segnale visivo e un segnale audio quando la destinazione è costituita da oggetti interagibili.</span><span class="sxs-lookup"><span data-stu-id="92670-480">As a rule of thumb there should be a visual and audio cue when targeting interactable objects.</span></span>

### <a name="recommendations"></a><span data-ttu-id="92670-481">Consigli</span><span class="sxs-lookup"><span data-stu-id="92670-481">Recommendations</span></span>

* <span data-ttu-id="92670-482">Usare commenti visivi e audio per le interazioni.</span><span class="sxs-lookup"><span data-stu-id="92670-482">Use visual and audio feedback for interactions.</span></span>
* <span data-ttu-id="92670-483">Il feedback visivo deve essere differenziato per ogni stato di input (inattivo, mirato, selezionato)</span><span class="sxs-lookup"><span data-stu-id="92670-483">Visual feedback should be differentiated for each input state (idle, targeted, selected)</span></span>
* <span data-ttu-id="92670-484">Gli oggetti interagibili devono essere ridimensionati e posizionati per la destinazione senza errori.</span><span class="sxs-lookup"><span data-stu-id="92670-484">Interactable objects should be scaled and placed for error free targeting.</span></span>
* <span data-ttu-id="92670-485">Gli oggetti interagiscono raggruppati, ad esempio una barra dei menu o un elenco, devono avere la spaziatura corretta per la destinazione.</span><span class="sxs-lookup"><span data-stu-id="92670-485">Grouped interactable objects (such as a menu bar or list) should have proper spacing for targeting.</span></span>
* <span data-ttu-id="92670-486">I pulsanti e i menu che supportano il comando Voice devono fornire etichette di testo per la parola chiave Command ("vedere, Say it")</span><span class="sxs-lookup"><span data-stu-id="92670-486">Buttons and menus that support voice command should provide text labels for the command keyword ("See it, say it")</span></span>

### <a name="resources"></a><span data-ttu-id="92670-487">Risorse</span><span class="sxs-lookup"><span data-stu-id="92670-487">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="92670-488">Documentazione</span><span class="sxs-lookup"><span data-stu-id="92670-488">Documentation</span></span>

* [<span data-ttu-id="92670-489">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="92670-489">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="92670-490">Testo in Unity</span><span class="sxs-lookup"><span data-stu-id="92670-490">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="92670-491">Rettangolo di selezione e barra dell'app</span><span class="sxs-lookup"><span data-stu-id="92670-491">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="92670-492">Input vocale</span><span class="sxs-lookup"><span data-stu-id="92670-492">Voice input</span></span>](voice-input.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="92670-493">Strumenti ed esercitazioni</span><span class="sxs-lookup"><span data-stu-id="92670-493">Tools and tutorials</span></span>

* [<span data-ttu-id="92670-494">Toolkit per realtà mista-UX</span><span class="sxs-lookup"><span data-stu-id="92670-494">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a><span data-ttu-id="92670-495">Analisi chat room</span><span class="sxs-lookup"><span data-stu-id="92670-495">Room scanning</span></span>

<span data-ttu-id="92670-496">Le app che richiedono dati di mapping spaziale si basano sul dispositivo per raccogliere automaticamente questi dati nel tempo e nelle sessioni mentre l'utente Esplora il proprio ambiente con il dispositivo attivo.</span><span class="sxs-lookup"><span data-stu-id="92670-496">Apps that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="92670-497">La completezza e la qualità di questi dati dipendono da diversi fattori, tra cui la quantità di esplorazione eseguita dall'utente, il tempo trascorso dall'esplorazione e l'eventuale spostamento degli oggetti, ad esempio mobili e porte, dal momento in cui il dispositivo ha analizzato l'area.</span><span class="sxs-lookup"><span data-stu-id="92670-497">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span> <span data-ttu-id="92670-498">Molte app analizzeranno i dati di mapping spaziali all'inizio dell'esperienza per valutare se l'utente deve eseguire passaggi aggiuntivi per migliorare la completezza e la qualità della mappa spaziale.</span><span class="sxs-lookup"><span data-stu-id="92670-498">Many apps will analyze the spatial mapping data at the start of the experience to judge whether the user should perform additional steps to improve the completeness and quality of the spatial map.</span></span> <span data-ttu-id="92670-499">Se l'utente deve analizzare l'ambiente, è necessario fornire indicazioni chiare durante l'esperienza di analisi.</span><span class="sxs-lookup"><span data-stu-id="92670-499">If the user is required to scan the environment, clear guidance should be provided during the scanning experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="92670-500">Effetti sul dispositivo</span><span class="sxs-lookup"><span data-stu-id="92670-500">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="92670-501"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="92670-501"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="92670-502"><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="92670-502"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="92670-503">✔️</span><span class="sxs-lookup"><span data-stu-id="92670-503">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="92670-504">Criteri di qualità</span><span class="sxs-lookup"><span data-stu-id="92670-504">Quality criteria</span></span>

|  <span data-ttu-id="92670-505">Consigliate</span><span class="sxs-lookup"><span data-stu-id="92670-505">Best</span></span>  |  <span data-ttu-id="92670-506">Soddisfi</span><span class="sxs-lookup"><span data-stu-id="92670-506">Meets</span></span> |  <span data-ttu-id="92670-507">Esito negativo</span><span class="sxs-lookup"><span data-stu-id="92670-507">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="92670-508">La visualizzazione della mesh spaziale indica che è in corso l'analisi degli utenti.</span><span class="sxs-lookup"><span data-stu-id="92670-508">Visualization of the spatial mesh tell users scanning is in progress.</span></span> <span data-ttu-id="92670-509">L'utente sa chiaramente cosa fare e quando l'analisi viene avviata e arrestata.</span><span class="sxs-lookup"><span data-stu-id="92670-509">User clearly knows what to do and when the scan starts and stops.</span></span> | <span data-ttu-id="92670-510">Viene fornita la visualizzazione della mesh spaziale, ma l'utente potrebbe non sapere chiaramente cosa fare e non viene fornita alcuna informazione sullo stato di avanzamento.</span><span class="sxs-lookup"><span data-stu-id="92670-510">Visualization of the spatial mesh is provided, but the user may not clearly know what to do and no progress information is provided.</span></span> | <span data-ttu-id="92670-511">Nessuna visualizzazione della rete mesh.</span><span class="sxs-lookup"><span data-stu-id="92670-511">No visualization of mesh.</span></span> <span data-ttu-id="92670-512">Non sono disponibili informazioni aggiuntive per l'utente in merito alla posizione in cui eseguire l'analisi o all'avvio o all'arresto dell'analisi.</span><span class="sxs-lookup"><span data-stu-id="92670-512">No guidance information provided to the user regarding where to look, or when the scan starts/stops.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="92670-513">Come misurare</span><span class="sxs-lookup"><span data-stu-id="92670-513">How to measure</span></span>

* <span data-ttu-id="92670-514">Durante un'analisi dello spazio richiesto, viene fornita una guida visiva e audio che indica il punto di ricerca e quando avviare e arrestare l'analisi.</span><span class="sxs-lookup"><span data-stu-id="92670-514">During a required room scan, visual and audio guidance is provided indicating where to look, and when to start and stop scanning.</span></span>

### <a name="recommendations"></a><span data-ttu-id="92670-515">Consigli</span><span class="sxs-lookup"><span data-stu-id="92670-515">Recommendations</span></span>

* <span data-ttu-id="92670-516">Indicare la quantità di volume totale in prossimità degli utenti che deve far parte dell'esperienza.</span><span class="sxs-lookup"><span data-stu-id="92670-516">Indicate how much of the total volume in the users vicinity needs to be part of the experience.</span></span>
* <span data-ttu-id="92670-517">Comunica quando l'analisi viene avviata e interrotta, ad esempio un indicatore di stato.</span><span class="sxs-lookup"><span data-stu-id="92670-517">Communicate when the scan starts and stops such as a progress indicator.</span></span>
* <span data-ttu-id="92670-518">Usare una visualizzazione della mesh durante l'analisi.</span><span class="sxs-lookup"><span data-stu-id="92670-518">Use a visualization of the mesh during the scan.</span></span>
* <span data-ttu-id="92670-519">Fornire indicazioni visive e audio per invitare l'utente a cercare e spostarsi in una stanza.</span><span class="sxs-lookup"><span data-stu-id="92670-519">Provide visual and audio cues to encourage the user to look and move around the room.</span></span>
* <span data-ttu-id="92670-520">Informare l'utente della posizione per migliorare i dati.</span><span class="sxs-lookup"><span data-stu-id="92670-520">Inform the user where to go to improve the data.</span></span> <span data-ttu-id="92670-521">In molti casi, può essere preferibile informare l'utente di cosa è necessario fare (ad esempio, osservare il soffitto, guardare dietro la mobilia), per ottenere la qualità di analisi necessaria.</span><span class="sxs-lookup"><span data-stu-id="92670-521">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

### <a name="resources"></a><span data-ttu-id="92670-522">Risorse</span><span class="sxs-lookup"><span data-stu-id="92670-522">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="92670-523">Documentazione</span><span class="sxs-lookup"><span data-stu-id="92670-523">Documentation</span></span>

* [<span data-ttu-id="92670-524">Visualizzazione della scansione dello spazio</span><span class="sxs-lookup"><span data-stu-id="92670-524">Room scan visualization</span></span>](room-scan-visualization.md)
* [<span data-ttu-id="92670-525">Case Study: espansione delle funzionalità di mapping spaziale di HoloLens</span><span class="sxs-lookup"><span data-stu-id="92670-525">Case study: Expanding the spatial mapping capabilities of HoloLens</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="92670-526">Case Study: progettazione di suoni spaziali per HoloTour</span><span class="sxs-lookup"><span data-stu-id="92670-526">Case study: Spatial sound design for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="92670-527">Case Study: creazione di un'esperienza immersiva nei frammenti</span><span class="sxs-lookup"><span data-stu-id="92670-527">Case study: Creating an immersive experience in Fragments</span></span>](case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="92670-528">Strumenti ed esercitazioni</span><span class="sxs-lookup"><span data-stu-id="92670-528">Tools and tutorials</span></span>

* [<span data-ttu-id="92670-529">Toolkit per realtà mista-UX</span><span class="sxs-lookup"><span data-stu-id="92670-529">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a><span data-ttu-id="92670-530">Indicatori direzionali</span><span class="sxs-lookup"><span data-stu-id="92670-530">Directional indicators</span></span>

<span data-ttu-id="92670-531">In un'app di realtà mista, il contenuto può essere esterno al campo di visualizzazione o bloccato da oggetti reali.</span><span class="sxs-lookup"><span data-stu-id="92670-531">In a mixed reality app, content may be outside the field of view or occluded by real-world objects.</span></span> <span data-ttu-id="92670-532">Un'app ben progettata renderà più semplice per l'utente trovare contenuto non visibile.</span><span class="sxs-lookup"><span data-stu-id="92670-532">A well designed app will make it easier for the user to find non-visible content.</span></span> <span data-ttu-id="92670-533">Gli indicatori direzionali segnalano a un utente un contenuto importante e forniscono indicazioni sul contenuto relativo alla posizione dell'utente.</span><span class="sxs-lookup"><span data-stu-id="92670-533">Directional indicators alert a user to important content and provide guidance to the content relative to the user's position.</span></span> <span data-ttu-id="92670-534">Le linee guida per il contenuto non visibile possono assumere la forma di emettitori di suoni, frecce direzionali o segnali visivi diretti.</span><span class="sxs-lookup"><span data-stu-id="92670-534">Guidance to non-visible content can take the form of sound emitters, directional arrows, or direct visual cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="92670-535">Effetti sul dispositivo</span><span class="sxs-lookup"><span data-stu-id="92670-535">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="92670-536"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="92670-536"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="92670-537"><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="92670-537"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="92670-538">✔️</span><span class="sxs-lookup"><span data-stu-id="92670-538">✔️</span></span></td>
        <td><span data-ttu-id="92670-539">✔️</span><span class="sxs-lookup"><span data-stu-id="92670-539">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="92670-540">Criteri di qualità</span><span class="sxs-lookup"><span data-stu-id="92670-540">Quality criteria</span></span>

|  <span data-ttu-id="92670-541">Consigliate</span><span class="sxs-lookup"><span data-stu-id="92670-541">Best</span></span>  |  <span data-ttu-id="92670-542">Soddisfi</span><span class="sxs-lookup"><span data-stu-id="92670-542">Meets</span></span> |  <span data-ttu-id="92670-543">Esito negativo</span><span class="sxs-lookup"><span data-stu-id="92670-543">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="92670-544">I suggerimenti visivi e audio indirizzano direttamente l'utente al contenuto pertinente al di fuori del campo di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="92670-544">Visual and audio cues directly guide the user to relevant content outside the field of view.</span></span> | <span data-ttu-id="92670-545">Una freccia o un indicatore che punta l'utente nella direzione generale del contenuto.</span><span class="sxs-lookup"><span data-stu-id="92670-545">An arrow or some indicator that points the user in the general direction of the content.</span></span> | <span data-ttu-id="92670-546">Il contenuto pertinente non è compreso nel campo di visualizzazione e non è stata fornita alcuna indicazione per la posizione dell'utente.</span><span class="sxs-lookup"><span data-stu-id="92670-546">Relevant content is outside of the field of view, and poor or no location guidance is provided to the user.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="92670-547">Come misurare</span><span class="sxs-lookup"><span data-stu-id="92670-547">How to measure</span></span>

* <span data-ttu-id="92670-548">Il contenuto pertinente al di fuori del campo di visualizzazione utente può essere individuato tramite segnali visivi e/o audio.</span><span class="sxs-lookup"><span data-stu-id="92670-548">Relevant content outside of the user field of view is discoverable through visual and/or audio cues.</span></span>

### <a name="recommendations"></a><span data-ttu-id="92670-549">Consigli</span><span class="sxs-lookup"><span data-stu-id="92670-549">Recommendations</span></span>

* <span data-ttu-id="92670-550">Quando il contenuto pertinente è esterno al campo di visualizzazione dell'utente, usare indicatori direzionali e segnali audio per guidare l'utente nel contenuto.</span><span class="sxs-lookup"><span data-stu-id="92670-550">When relevant content is outside the user's field of view, use directional indicators and audio cues to guide the user to the content.</span></span> <span data-ttu-id="92670-551">In molti casi, è preferibile una guida visiva diretta sulle frecce direzionali.</span><span class="sxs-lookup"><span data-stu-id="92670-551">In many cases, a direct visual guide is preferred over directional arrows.</span></span>
* <span data-ttu-id="92670-552">Gli indicatori direzionali non devono essere incorporati nel cursore.</span><span class="sxs-lookup"><span data-stu-id="92670-552">Directional indicators should not be built into the cursor.</span></span>

### <a name="resources"></a><span data-ttu-id="92670-553">Risorse</span><span class="sxs-lookup"><span data-stu-id="92670-553">Resources</span></span>

* [<span data-ttu-id="92670-554">Frame olografico</span><span class="sxs-lookup"><span data-stu-id="92670-554">Holographic frame</span></span>](holographic-frame.md)

## <a name="data-loading"></a><span data-ttu-id="92670-555">Caricamento dati</span><span class="sxs-lookup"><span data-stu-id="92670-555">Data loading</span></span>

<span data-ttu-id="92670-556">Un controllo di stato fornisce all'utente un feedback nel caso in cui sia in corso un'operazione di lunga durata.</span><span class="sxs-lookup"><span data-stu-id="92670-556">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="92670-557">Questo può significare che l'utente non può interagire con l'app quando l'indicatore di stato è visibile e può anche indicare la durata del tempo di attesa.</span><span class="sxs-lookup"><span data-stu-id="92670-557">It can mean that the user cannot interact with the app when the progress indicator is visible and can also indicate how long the wait time might be.</span></span>

### <a name="device-impact"></a><span data-ttu-id="92670-558">Effetti sul dispositivo</span><span class="sxs-lookup"><span data-stu-id="92670-558">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="92670-559"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="92670-559"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="92670-560"><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="92670-560"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="92670-561">✔️</span><span class="sxs-lookup"><span data-stu-id="92670-561">✔️</span></span></td>
        <td><span data-ttu-id="92670-562">✔️</span><span class="sxs-lookup"><span data-stu-id="92670-562">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="92670-563">Criteri di qualità</span><span class="sxs-lookup"><span data-stu-id="92670-563">Quality criteria</span></span>

|  <span data-ttu-id="92670-564">Consigliate</span><span class="sxs-lookup"><span data-stu-id="92670-564">Best</span></span>  |  <span data-ttu-id="92670-565">Soddisfi</span><span class="sxs-lookup"><span data-stu-id="92670-565">Meets</span></span> |  <span data-ttu-id="92670-566">Esito negativo</span><span class="sxs-lookup"><span data-stu-id="92670-566">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="92670-567">Indicatore visivo animato, sotto forma di indicatore di stato o anello, che mostra lo stato di avanzamento durante il caricamento o l'elaborazione dei dati.</span><span class="sxs-lookup"><span data-stu-id="92670-567">Animated visual indicator, in the form of a progress bar or ring, showing progress during any data loading or processing.</span></span> <span data-ttu-id="92670-568">L'indicatore visivo fornisce indicazioni sulla durata dell'attesa.</span><span class="sxs-lookup"><span data-stu-id="92670-568">The visual indicator provides guidance on how long the wait could be.</span></span> | <span data-ttu-id="92670-569">L'utente viene informato che è in corso il caricamento dei dati, ma non è presente alcuna indicazione del tempo di attesa.</span><span class="sxs-lookup"><span data-stu-id="92670-569">User is informed that data loading is in progress, but there is no indication of how long the wait could be.</span></span> | <span data-ttu-id="92670-570">Nessun indicatore di caricamento o elaborazione dei dati per l'attività richiede più di 5 secondi.</span><span class="sxs-lookup"><span data-stu-id="92670-570">No data loading or process indicators for task taking longer than 5 seconds.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="92670-571">Come misurare</span><span class="sxs-lookup"><span data-stu-id="92670-571">How to measure</span></span>

* <span data-ttu-id="92670-572">Durante il caricamento dei dati, verificare che non sia presente alcuno stato vuoto per più di 5 secondi.</span><span class="sxs-lookup"><span data-stu-id="92670-572">During data loading verify there is no blank state for more than 5 seconds.</span></span>

### <a name="recommendations"></a><span data-ttu-id="92670-573">Consigli</span><span class="sxs-lookup"><span data-stu-id="92670-573">Recommendations</span></span>

* <span data-ttu-id="92670-574">Fornire un'animazione per il caricamento dei dati che mostra lo stato di avanzamento in qualsiasi situazione in cui l'utente può percepire che l'app è bloccata o arrestata in modo anomalo.</span><span class="sxs-lookup"><span data-stu-id="92670-574">Provide a data loading animator showing progress in any situation when the user may perceive this app to have stalled or crashed.</span></span> <span data-ttu-id="92670-575">Una regola empirica ragionevole è l'attività di caricamento che può richiedere più di 5 secondi.</span><span class="sxs-lookup"><span data-stu-id="92670-575">A reasonable rule of thumb is any 'loading' activity that could take more than 5 seconds.</span></span>

### <a name="resources"></a><span data-ttu-id="92670-576">Risorse</span><span class="sxs-lookup"><span data-stu-id="92670-576">Resources</span></span>

* [<span data-ttu-id="92670-577">Visualizzazione dello stato</span><span class="sxs-lookup"><span data-stu-id="92670-577">Displaying progress</span></span>](progress.md)

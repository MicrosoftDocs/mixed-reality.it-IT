---
title: Criteri di qualità delle App
description: Questo documento descrive i principali fattori influiscono sulla qualità delle app di realtà mista.
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: criteri di qualità delle App, realtà mista mista app per realtà
ms.openlocfilehash: 756bc148f290aa3406c9ac8bb7003d463c62772c
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974745"
---
# <a name="app-quality-criteria"></a><span data-ttu-id="ff6a8-104">Criteri di qualità delle App</span><span class="sxs-lookup"><span data-stu-id="ff6a8-104">App quality criteria</span></span>

<span data-ttu-id="ff6a8-105">Questo documento descrive i principali fattori influiscono sulla qualità delle app di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-105">This document describes the top factors impacting the quality of mixed reality apps.</span></span> <span data-ttu-id="ff6a8-106">Per ogni fattore viene fornite le informazioni seguenti</span><span class="sxs-lookup"><span data-stu-id="ff6a8-106">For each factor the following information is provided</span></span>
* <span data-ttu-id="ff6a8-107">Panoramica: una breve descrizione del fattore di qualità e perché è importante.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-107">Overview – a brief description of the quality factor and why it is important.</span></span>
* <span data-ttu-id="ff6a8-108">Impatto sul dispositivo - il tipo di dispositivo di realtà mista di finestra è stato interessato.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-108">Device impact - which type of Window Mixed Reality device is impacted.</span></span>
* <span data-ttu-id="ff6a8-109">Criteri di qualità – come valutare il fattore di qualità.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-109">Quality criteria – how to evaluate the quality factor.</span></span>
* <span data-ttu-id="ff6a8-110">Viene descritto come misurare: metodi per misurare il problema (o esperienza).</span><span class="sxs-lookup"><span data-stu-id="ff6a8-110">How to measure – methods to measure (or experience) the issue.</span></span>
* <span data-ttu-id="ff6a8-111">Recommendations di riepilogo degli approcci per offrire una migliore esperienza utente.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-111">Recommendations – summary of approaches to provide a better user experience.</span></span>
* <span data-ttu-id="ff6a8-112">Risorse: sviluppatore pertinenti e le risorse di progettazione che sono utili per creare esperienze migliori app.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-112">Resources – relevant developer and design resources that are useful to create better app experiences.</span></span>

## <a name="frame-rate"></a><span data-ttu-id="ff6a8-113">Frequenza dei fotogrammi</span><span class="sxs-lookup"><span data-stu-id="ff6a8-113">Frame rate</span></span>

<span data-ttu-id="ff6a8-114">Frequenza dei fotogrammi è il primo pilastro dello ologrammi stabilità comodità per l'utente.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-114">Frame rate is the first pillar of hologram stability and user comfort.</span></span> <span data-ttu-id="ff6a8-115">Frequenza dei fotogrammi sotto le destinazioni consigliate può causare vntana visualizzazione instabilità, non hanno conseguenze negative believability dell'esperienza e causando potenzialmente la fatica sotto controllo.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-115">Frame rate below the recommended targets can cause holograms to appear jittery, negatively impacting the believability of the experience and potentially causing eye fatigue.</span></span> <span data-ttu-id="ff6a8-116">La frequenza dei fotogrammi destinazione per la tua esperienza sul auricolari coinvolgenti di realtà mista di Windows sarà 60Hz o 90Hz, a seconda di quale misto realtà compatibile con i PC Windows che si desidera supportare.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-116">The target frame rate for your experience on Windows Mixed Reality immersive headsets will be either 60Hz or 90Hz depending on which Windows Mixed Reality Compatible PCs you wish to support.</span></span> <span data-ttu-id="ff6a8-117">Per HoloLens la frequenza dei fotogrammi di destinazione è 60Hz.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-117">For HoloLens the target frame rate is 60Hz.</span></span>

### <a name="device-impact"></a><span data-ttu-id="ff6a8-118">Impatto di dispositivo</span><span class="sxs-lookup"><span data-stu-id="ff6a8-118">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="ff6a8-119"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="ff6a8-119"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="ff6a8-120"><a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></span><span class="sxs-lookup"><span data-stu-id="ff6a8-120"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="ff6a8-121">✔️</span><span class="sxs-lookup"><span data-stu-id="ff6a8-121">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="ff6a8-122">✔️</span><span class="sxs-lookup"><span data-stu-id="ff6a8-122">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="ff6a8-123">Criteri di qualità</span><span class="sxs-lookup"><span data-stu-id="ff6a8-123">Quality criteria</span></span>

|  <span data-ttu-id="ff6a8-124">Migliore</span><span class="sxs-lookup"><span data-stu-id="ff6a8-124">Best</span></span>  |  <span data-ttu-id="ff6a8-125">Soddisfa</span><span class="sxs-lookup"><span data-stu-id="ff6a8-125">Meets</span></span> |  <span data-ttu-id="ff6a8-126">esito negativo</span><span class="sxs-lookup"><span data-stu-id="ff6a8-126">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="ff6a8-127">L'app risponde in modo coerente fotogrammi al secondo obiettivo (FPS) per il dispositivo di destinazione: 60fps su HoloLens; fps 90 nei PC extra; e 60fps nei PC "Mainstream".</span><span class="sxs-lookup"><span data-stu-id="ff6a8-127">The app consistently meets frames per second (FPS) goal for target device: 60fps on HoloLens; 90fps on Ultra PCs; and 60fps on mainstream PCs.</span></span> | <span data-ttu-id="ff6a8-128">L'app ha cadute cornice intermittente non ostacolare l'esperienza di base; oppure FPS è regolarmente inferiori a obiettivo desiderato, ma non impedisca l'esperienza delle app.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-128">The app has intermittent frame drops not impeding the core experience; or FPS is consistently lower than desired goal but doesn’t impede the app experience.</span></span> | <span data-ttu-id="ff6a8-129">L'app sta riscontrando un calo di frequenza dei fotogrammi in Media ogni dieci secondi o meno.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-129">The app is experiencing a drop in frame rate on average every ten seconds or less.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="ff6a8-130">Consente di misurare</span><span class="sxs-lookup"><span data-stu-id="ff6a8-130">How to measure</span></span>

* <span data-ttu-id="ff6a8-131">Un grafico di frequenza fotogrammi in tempo reale, è possibile per il [Windows Device Portal](using-the-windows-device-portal.md#system-performance) sotto "Le prestazioni del sistema".</span><span class="sxs-lookup"><span data-stu-id="ff6a8-131">A real-time frame rate graph is provided through by the [Windows Device Portal](using-the-windows-device-portal.md#system-performance) under "System Performance".</span></span>
* <span data-ttu-id="ff6a8-132">Per il debug, sviluppo aggiungere un contatore di diagnostica di frequenza di frame nell'app.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-132">For development debugging, add a frame rate diagnostic counter into the app.</span></span> <span data-ttu-id="ff6a8-133">Per un contatore di esempio, vedere le risorse.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-133">See Resources for a sample counter.</span></span>
* <span data-ttu-id="ff6a8-134">Frame velocità scende possono presentarsi nelle dispositivo mentre l'app è in esecuzione tramite lo spostamento di head da un lato a altro.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-134">Frame rate drops can be experienced in device while the app is running by moving your head from side to side.</span></span> <span data-ttu-id="ff6a8-135">Se l'ologrammi Mostra lo spostamento di instabilità imprevisto, quindi a bassa frequenza dei fotogrammi o il piano di stabilità è probabilmente la causa.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-135">If the hologram shows unexpected jittery movement, then low frame rate or the stability plane is likely the cause.</span></span>

### <a name="recommendations"></a><span data-ttu-id="ff6a8-136">Consigli</span><span class="sxs-lookup"><span data-stu-id="ff6a8-136">Recommendations</span></span>

* <span data-ttu-id="ff6a8-137">Aggiungere un contatore di frequenza fotogrammi all'inizio del lavoro di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-137">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="ff6a8-138">Le modifiche che comportano una riduzione della frequenza dei fotogrammi dovrebbero valutare e risolvere in modo appropriato come un bug nelle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-138">Changes that incur a drop in frame rate should be evaluated and appropriately resolved as a performance bug.</span></span>

### <a name="resources"></a><span data-ttu-id="ff6a8-139">Risorse</span><span class="sxs-lookup"><span data-stu-id="ff6a8-139">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="ff6a8-140">Documentazione</span><span class="sxs-lookup"><span data-stu-id="ff6a8-140">Documentation</span></span>

* [<span data-ttu-id="ff6a8-141">Ottenere informazioni sulle prestazioni per realtà mista</span><span class="sxs-lookup"><span data-stu-id="ff6a8-141">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="ff6a8-142">Frequenza dei fotogrammi e la stabilità di ologramma</span><span class="sxs-lookup"><span data-stu-id="ff6a8-142">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="ff6a8-143">Budget di prestazioni di asset</span><span class="sxs-lookup"><span data-stu-id="ff6a8-143">Asset performance budget</span></span>](asset-creation-process.md)
* [<span data-ttu-id="ff6a8-144">Consigli sulle prestazioni per Unity</span><span class="sxs-lookup"><span data-stu-id="ff6a8-144">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="ff6a8-145">Strumenti ed esercitazioni</span><span class="sxs-lookup"><span data-stu-id="ff6a8-145">Tools and tutorials</span></span>

* [<span data-ttu-id="ff6a8-146">MRToolkit, visualizzazione contatore FPS</span><span class="sxs-lookup"><span data-stu-id="ff6a8-146">MRToolkit, FPS counter display</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [<span data-ttu-id="ff6a8-147">MRToolkit, gli shader</span><span class="sxs-lookup"><span data-stu-id="ff6a8-147">MRToolkit, Shaders</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a><span data-ttu-id="ff6a8-148">Riferimenti esterni</span><span class="sxs-lookup"><span data-stu-id="ff6a8-148">External references</span></span>

* [<span data-ttu-id="ff6a8-149">Unity, ottimizzazione delle applicazioni per dispositivi mobili</span><span class="sxs-lookup"><span data-stu-id="ff6a8-149">Unity, Optimizing mobile applications</span></span>](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a><span data-ttu-id="ff6a8-150">Stabilità ologrammi</span><span class="sxs-lookup"><span data-stu-id="ff6a8-150">Hologram stability</span></span>

<span data-ttu-id="ff6a8-151">Ologrammi stabile verranno aumentare l'usabilità e believability dell'app e creare un'esperienza di visualizzazione più a proprio agio per l'utente.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-151">Stable holograms will increase the usability and believability of your app, and create a more comfortable viewing experience for the user.</span></span> <span data-ttu-id="ff6a8-152">La qualità della stabilità ologrammi è il risultato dello sviluppo di app valida e la capacità del dispositivo per comprendere (traccia) relativo ambiente.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-152">The quality of hologram stability is a result of good app development and the device's ability to understand (track) its environment.</span></span> <span data-ttu-id="ff6a8-153">Frequenza dei fotogrammi è il primo pilastro della stabilità, altri fattori possono influire sulle stabilità tra cui:</span><span class="sxs-lookup"><span data-stu-id="ff6a8-153">While frame rate is the first pillar of stability, other factors can impact stability including:</span></span>

* <span data-ttu-id="ff6a8-154">Uso del piano di stabilizzazione</span><span class="sxs-lookup"><span data-stu-id="ff6a8-154">Use of the stabilization plane</span></span>
* <span data-ttu-id="ff6a8-155">Distanza agli ancoraggi spaziali</span><span class="sxs-lookup"><span data-stu-id="ff6a8-155">Distance to spatial anchors</span></span>
* <span data-ttu-id="ff6a8-156">Rilevamento</span><span class="sxs-lookup"><span data-stu-id="ff6a8-156">Tracking</span></span>

### <a name="device-impact"></a><span data-ttu-id="ff6a8-157">Impatto di dispositivo</span><span class="sxs-lookup"><span data-stu-id="ff6a8-157">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="ff6a8-158"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="ff6a8-158"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="ff6a8-159"><a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></span><span class="sxs-lookup"><span data-stu-id="ff6a8-159"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="ff6a8-160">✔️</span><span class="sxs-lookup"><span data-stu-id="ff6a8-160">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="ff6a8-161">Criteri di qualità</span><span class="sxs-lookup"><span data-stu-id="ff6a8-161">Quality criteria</span></span>

|  <span data-ttu-id="ff6a8-162">Migliore</span><span class="sxs-lookup"><span data-stu-id="ff6a8-162">Best</span></span>  |  <span data-ttu-id="ff6a8-163">Soddisfa</span><span class="sxs-lookup"><span data-stu-id="ff6a8-163">Meets</span></span> |  <span data-ttu-id="ff6a8-164">esito negativo</span><span class="sxs-lookup"><span data-stu-id="ff6a8-164">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="ff6a8-165">Ologrammi continuano ad apparire stabile.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-165">Holograms consistently appear stable.</span></span> | <span data-ttu-id="ff6a8-166">Contenuto secondario presenta lo spostamento imprevisto. o spostamento imprevisto non influire esperienza app complessiva.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-166">Secondary content exhibits unexpected movement; or unexpected movement does not impede overall app experience.</span></span> | <span data-ttu-id="ff6a8-167">Il contenuto principale nel frame presenta movimento imprevisto.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-167">Primary content in frame exhibits unexpected movement.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="ff6a8-168">Consente di misurare</span><span class="sxs-lookup"><span data-stu-id="ff6a8-168">How to measure</span></span>

<span data-ttu-id="ff6a8-169">Mentre l'usura del dispositivo e l'esperienza di visualizzazione:</span><span class="sxs-lookup"><span data-stu-id="ff6a8-169">While wearing the device and viewing the experience:</span></span>

* <span data-ttu-id="ff6a8-170">Spostare l'head da un lato a altro, se il vntana indicano lo spostamento dei imprevisto quindi a bassa frequenza dei fotogrammi o allineamento non corretta del piano di stabilità a piano focale è la causa più probabile.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-170">Move your head from side to side, if the holograms show unexpected movement then low frame rate or improper alignment of the stability plane to the focal plane is the likely cause.</span></span>
* <span data-ttu-id="ff6a8-171">Spostare l'ambiente e vntana, cercare i comportamenti, ad esempio nuoto e jumpiness.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-171">Move around the holograms and environment, look for behaviors such as swim and jumpiness.</span></span> <span data-ttu-id="ff6a8-172">Questo tipo di movimento è probabilmente causato dal dispositivo senza il rilevamento dell'ambiente o la distanza in base all'ancoraggio spaziale.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-172">This type of motion is likely caused by the device not tracking the environment, or the distance to the spatial anchor.</span></span>
* <span data-ttu-id="ff6a8-173">Se è grande o più vntana è nel frame, osservare il comportamento di ologramma profondità diverse durante lo spostamento alla posizione di head da un lato a altro, se viene visualizzato bruschi è probabilmente causato dal piano di stabilizzazione.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-173">If large or multiple holograms are in the frame, observe hologram behavior at various depths while moving your head position from side to side, if shakiness appears this is likely caused by the stabilization plane.</span></span>

### <a name="recomendations"></a><span data-ttu-id="ff6a8-174">Consigli sulla</span><span class="sxs-lookup"><span data-stu-id="ff6a8-174">Recomendations</span></span>

* <span data-ttu-id="ff6a8-175">Aggiungere un contatore di frequenza fotogrammi all'inizio del lavoro di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-175">Add an frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="ff6a8-176">Usare il piano di stabilizzazione.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-176">Use the stabilization plane.</span></span>
* <span data-ttu-id="ff6a8-177">Eseguire sempre il rendering vntana ancorata all'interno di 3 misuratori del loro punto di ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-177">Always render anchored holograms within 3 meters of their anchor.</span></span>
* <span data-ttu-id="ff6a8-178">Assicurarsi che l'ambiente sia configurato per il rilevamento corretto.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-178">Make sure your environment is setup for proper tracking.</span></span>
* <span data-ttu-id="ff6a8-179">Progettare l'esperienza per evitare vntana a vari livelli di profondità focale all'interno del frame.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-179">Design your experience to avoid holograms at various focal depth levels within the frame.</span></span>

### <a name="resources"></a><span data-ttu-id="ff6a8-180">Risorse</span><span class="sxs-lookup"><span data-stu-id="ff6a8-180">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="ff6a8-181">Documentazione</span><span class="sxs-lookup"><span data-stu-id="ff6a8-181">Documentation</span></span>

* [<span data-ttu-id="ff6a8-182">Frequenza dei fotogrammi e la stabilità di ologramma</span><span class="sxs-lookup"><span data-stu-id="ff6a8-182">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="ff6a8-183">Case study, utilizzando il piano di stabilizzazione</span><span class="sxs-lookup"><span data-stu-id="ff6a8-183">Case study, Using the stabilization plane</span></span>](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [<span data-ttu-id="ff6a8-184">Ottenere informazioni sulle prestazioni per realtà mista</span><span class="sxs-lookup"><span data-stu-id="ff6a8-184">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="ff6a8-185">Consigli sulle prestazioni per Unity</span><span class="sxs-lookup"><span data-stu-id="ff6a8-185">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="ff6a8-186">Ancoraggi nello spazio</span><span class="sxs-lookup"><span data-stu-id="ff6a8-186">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="ff6a8-187">Gestione degli errori di rilevamento</span><span class="sxs-lookup"><span data-stu-id="ff6a8-187">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="ff6a8-188">Fotogramma di riferimento fisso</span><span class="sxs-lookup"><span data-stu-id="ff6a8-188">Stationary frame of reference</span></span>](coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="ff6a8-189">Strumenti ed esercitazioni</span><span class="sxs-lookup"><span data-stu-id="ff6a8-189">Tools and tutorials</span></span>

* [<span data-ttu-id="ff6a8-190">MR Companion Kit, Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="ff6a8-190">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a><span data-ttu-id="ff6a8-191">Posizione vntana su superfici reali</span><span class="sxs-lookup"><span data-stu-id="ff6a8-191">Holograms position on real surfaces</span></span>

<span data-ttu-id="ff6a8-192">Disallineamenti di vntana con oggetti fisici (se deve essere posizionato in relazione a altra) è una chiara indicazione dell'unione non-ologrammi e reali.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-192">Misalignments of holograms with physical objects (if intended to be placed in relation to one another) is a clear indication of the non-union of holograms and real-world.</span></span> <span data-ttu-id="ff6a8-193">Accuratezza della posizione deve essere relativo alle esigenze dello scenario; ad esempio, posizionamento superficie generale può utilizzare il mapping spaziale, ma il posizionamento più preciso richiederanno utilizzato per scopi di calibrazione e marcatori.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-193">Accuracy of the placement should be relative to the needs of the scenario; for example, general surface placement can use the spatial map, but more accurate placement will require some use of markers and calibration.</span></span>

### <a name="device-impact"></a><span data-ttu-id="ff6a8-194">Impatto di dispositivo</span><span class="sxs-lookup"><span data-stu-id="ff6a8-194">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="ff6a8-195"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="ff6a8-195"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="ff6a8-196"><a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></span><span class="sxs-lookup"><span data-stu-id="ff6a8-196"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="ff6a8-197">✔️</span><span class="sxs-lookup"><span data-stu-id="ff6a8-197">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="ff6a8-198">Criteri di qualità</span><span class="sxs-lookup"><span data-stu-id="ff6a8-198">Quality criteria</span></span>

|  <span data-ttu-id="ff6a8-199">Migliore</span><span class="sxs-lookup"><span data-stu-id="ff6a8-199">Best</span></span>  |  <span data-ttu-id="ff6a8-200">Soddisfa</span><span class="sxs-lookup"><span data-stu-id="ff6a8-200">Meets</span></span> |  <span data-ttu-id="ff6a8-201">esito negativo</span><span class="sxs-lookup"><span data-stu-id="ff6a8-201">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="ff6a8-202">Ologrammi Allinea all'area di in genere nei centimetri all'intervallo di pollici.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-202">Holograms align to the surface typically in the centimeters to inches range.</span></span> <span data-ttu-id="ff6a8-203">Se è necessaria maggiore accuratezza, l'app deve fornire un mezzo efficiente per la collaborazione all'interno di specifica di app desiderata.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-203">If more accuracy is required, the app should provide an efficient means for collaboration within the desired app spec.</span></span> | <span data-ttu-id="ff6a8-204">N/D</span><span class="sxs-lookup"><span data-stu-id="ff6a8-204">NA</span></span> | <span data-ttu-id="ff6a8-205">Il vntana vengono visualizzati non allineati con l'oggetto fisico di destinazione al piano della superficie di rilievo o spostata dall'area di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-205">The holograms appear unaligned with the physical target object by either breaking the surface plane or appearing to float away from the surface.</span></span> <span data-ttu-id="ff6a8-206">Se la precisione è necessaria, Vntana deve soddisfare le specifiche di prossimità dello scenario.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-206">If accuracy is required, Holograms should meet the proximity spec of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="ff6a8-207">Consente di misurare</span><span class="sxs-lookup"><span data-stu-id="ff6a8-207">How to measure</span></span>

* <span data-ttu-id="ff6a8-208">Vntana posizionati sulla mappa spaziale non deve essere visualizzati a float notevolmente di sopra o sotto l'area.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-208">Holograms that are placed on spatial map should not appear to dramatically float above or below the surface.</span></span>
* <span data-ttu-id="ff6a8-209">Ologrammi che richiedono il posizionamento preciso devono avere una forma del marcatore e calibrazione sistema appropriata ai requisiti dello scenario.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-209">Holograms that require accurate placement should have some form of marker and calibration system that is accurate to the scenario's requirement.</span></span>

### <a name="recommendations"></a><span data-ttu-id="ff6a8-210">Consigli</span><span class="sxs-lookup"><span data-stu-id="ff6a8-210">Recommendations</span></span>

* <span data-ttu-id="ff6a8-211">Mapping spaziale è utile per l'inserimento di oggetti su superfici quando la precisione non è obbligatoria.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-211">Spatial map is useful for placing objects on surfaces when precision isn’t required.</span></span>
* <span data-ttu-id="ff6a8-212">Per la precisione migliore, utilizzare gli indicatori o poster per impostare gli ologrammi e un controller Xbox (o un meccanismo di allineamento manuale) per calibrazione finale.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-212">For the best precision, use markers or posters to set the holograms and an Xbox controller (or some manual alignment mechanism) for final calibration.</span></span>
* <span data-ttu-id="ff6a8-213">È consigliabile suddividere vntana molto grande in parti logiche e allineamento di ogni parte all'area di.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-213">Consider breaking extra-large holograms into logical parts and aligning each part to the surface.</span></span>
* <span data-ttu-id="ff6a8-214">In modo non corretto distanza interpupilary set (IPD) può influire inoltre allineamento ologramma.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-214">Improperly set interpupilary distance (IPD) can also effect hologram alignment.</span></span> <span data-ttu-id="ff6a8-215">Configurare sempre HoloLens a IPD dell'utente.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-215">Always configure HoloLens to the user's IPD.</span></span>

### <a name="resources"></a><span data-ttu-id="ff6a8-216">Risorse</span><span class="sxs-lookup"><span data-stu-id="ff6a8-216">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="ff6a8-217">Documentazione</span><span class="sxs-lookup"><span data-stu-id="ff6a8-217">Documentation</span></span>

* [<span data-ttu-id="ff6a8-218">Posizionamento di mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="ff6a8-218">Spatial mapping placement</span></span>](spatial-mapping.md#placement)
* [<span data-ttu-id="ff6a8-219">Spazio di processo di digitalizzazione</span><span class="sxs-lookup"><span data-stu-id="ff6a8-219">Room scanning process</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="ff6a8-220">Procedure consigliate Anchor spaziali</span><span class="sxs-lookup"><span data-stu-id="ff6a8-220">Spatial anchors best practices</span></span>](spatial-anchors.md#best-practices)
* [<span data-ttu-id="ff6a8-221">Gestione degli errori di rilevamento</span><span class="sxs-lookup"><span data-stu-id="ff6a8-221">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="ff6a8-222">Mapping spaziale in Unity</span><span class="sxs-lookup"><span data-stu-id="ff6a8-222">Spatial mapping in Unity</span></span>](spatial-mapping-in-unity.md)
* [<span data-ttu-id="ff6a8-223">Panoramica dello sviluppo Vuforia</span><span class="sxs-lookup"><span data-stu-id="ff6a8-223">Vuforia development overview</span></span>](vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="ff6a8-224">Strumenti ed esercitazioni</span><span class="sxs-lookup"><span data-stu-id="ff6a8-224">Tools and tutorials</span></span>

* [<span data-ttu-id="ff6a8-225">Spaziale MR 230: Mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="ff6a8-225">MR Spatial 230: Spatial mapping</span></span>](holograms-230.md)
* [<span data-ttu-id="ff6a8-226">MR Toolkit, le librerie di Mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="ff6a8-226">MR Toolkit, Spatial Mapping Libraries</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [<span data-ttu-id="ff6a8-227">MR Companion Kit, Poster Calibration Sample</span><span class="sxs-lookup"><span data-stu-id="ff6a8-227">MR Companion Kit, Poster Calibration Sample</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [<span data-ttu-id="ff6a8-228">MR Companion Kit, Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="ff6a8-228">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a><span data-ttu-id="ff6a8-229">Riferimenti esterni</span><span class="sxs-lookup"><span data-stu-id="ff6a8-229">External references</span></span>

* [<span data-ttu-id="ff6a8-230">Lowes Case Study, l'allineamento di precisione</span><span class="sxs-lookup"><span data-stu-id="ff6a8-230">Lowes Case Study, Precision alignment</span></span>](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a><span data-ttu-id="ff6a8-231">Area di visualizzazione del fattore di comfort</span><span class="sxs-lookup"><span data-stu-id="ff6a8-231">Viewing zone of comfort</span></span>

<span data-ttu-id="ff6a8-232">Controllo App per gli sviluppatori in cui eseguire la convergenza occhi degli utenti inserendo il contenuto e vntana profondità diversi.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-232">App developers control where users' eyes converge by placing content and holograms at various depths.</span></span> <span data-ttu-id="ff6a8-233">Gli utenti che portano HoloLens permetteranno sempre a m 2.0 per mantenere un'immagine chiara in quanto consente di visualizzare HoloLens sono fissati a una distanza ottica circa 2.0m lontano dall'utente.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-233">Users wearing HoloLens will always accommodate to 2.0m to maintain a clear image because HoloLens displays are fixed at an optical distance approximately 2.0m away from the user.</span></span> <span data-ttu-id="ff6a8-234">Profondità del contenuto non corretto può causare disturbo visual o fatica.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-234">Improper content depth can lead to visual discomfort or fatigue.</span></span>

### <a name="device-impact"></a><span data-ttu-id="ff6a8-235">Impatto di dispositivo</span><span class="sxs-lookup"><span data-stu-id="ff6a8-235">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="ff6a8-236"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="ff6a8-236"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="ff6a8-237"><a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></span><span class="sxs-lookup"><span data-stu-id="ff6a8-237"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="ff6a8-238">✔️</span><span class="sxs-lookup"><span data-stu-id="ff6a8-238">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="ff6a8-239">Criteri di qualità</span><span class="sxs-lookup"><span data-stu-id="ff6a8-239">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="ff6a8-240">Migliore</span><span class="sxs-lookup"><span data-stu-id="ff6a8-240">Best</span></span> </td><td><ul>
<li><span data-ttu-id="ff6a8-241">Collocare il contenuto a 2 minuti.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-241">Place content at 2m.</span></span></li><li><span data-ttu-id="ff6a8-242">Quando non è possibile inserire vntana 2M e non è possibile evitare conflitti tra la convergenza e alloggio, la zona ottima per la selezione host ologrammi è compreso tra m 1,25 e 5 minuti.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-242">When holograms cannot be placed at 2m and conflicts between convergence and accommodation cannot be avoided, the optimal zone for hologram placement is between 1.25m and 5m.</span></span></li><li><span data-ttu-id="ff6a8-243">In ogni caso, le finestre di progettazione deve strutturare il contenuto per incoraggiare gli utenti di interagire 1 + metri (ad esempio, regolare le dimensioni del contenuto e i parametri di selezione host predefiniti).</span><span class="sxs-lookup"><span data-stu-id="ff6a8-243">In every case, designers should structure content to encourage users to interact 1+ m away (e.g. adjust content size and default placement parameters).</span></span></li><li><span data-ttu-id="ff6a8-244">A meno che specificamente non è necessario per lo scenario, un piano di ritaglio debba essere implementare con fadeout iniziando in corrispondenza di 1 milione.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-244">Unless specifically not required by the scenario, a clipping plane should be implement with fadeout starting at 1m.</span></span></li><li><span data-ttu-id="ff6a8-245">Nei casi in cui è necessario più da vicino osservazione di ologramma ovvero, il contenuto non deve essere inferiore a quello di 50cm.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-245">In cases where closer observation of a motionless hologram is required, the content should not be closer than 50cm.</span></span></li>
</ul></td>
</tr><tr>
<td> <span data-ttu-id="ff6a8-246">Soddisfa</span><span class="sxs-lookup"><span data-stu-id="ff6a8-246">Meets</span></span></td><td> <span data-ttu-id="ff6a8-247">Il contenuto è entro le indicazioni di visualizzazione e animazione, ma un utilizzo improprio o alcun utilizzo del piano di ritaglio.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-247">Content is within the viewing and motion guidance, but improper use or no use of the clipping plane.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="ff6a8-248">esito negativo</span><span class="sxs-lookup"><span data-stu-id="ff6a8-248">Fail</span></span> </td><td> <span data-ttu-id="ff6a8-249">Il contenuto viene visualizzato troppo vicino (in genere &lt;1.25 m e o &lt;50 cm per vntana fermo che richiedono più da vicino osservazione.)</span><span class="sxs-lookup"><span data-stu-id="ff6a8-249">Content is presented too close (typically &lt;1.25m, or &lt;50cm for stationary holograms requiring closer observation.)</span></span></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="ff6a8-250">Consente di misurare</span><span class="sxs-lookup"><span data-stu-id="ff6a8-250">How to measure</span></span>

* <span data-ttu-id="ff6a8-251">Il contenuto deve in genere essere 2M away, ma non inferiore a quello di 1,25 o oltre 5 minuti.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-251">Content should typically be 2m away, but no closer than 1.25 or further than 5m.</span></span>
* <span data-ttu-id="ff6a8-252">Con poche eccezioni, la distanza di rendering HoloLens ritaglio debba essere impostata su .85CM con fadeout del contenuto, iniziando in corrispondenza di 1 milione.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-252">With few exceptions, the HoloLens clipping render distance should be set to .85CM with fadeout of content starting at 1m.</span></span> <span data-ttu-id="ff6a8-253">Raggiungono il contenuto e notare l'effetto di piano di ritaglio.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-253">Approach the content and note the clipping plane effect.</span></span>
* <span data-ttu-id="ff6a8-254">Contenuto fisso non deve essere inferiore a quello di 50cm da subito.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-254">Stationary content should not be closer than 50cm away.</span></span>

### <a name="recommendations"></a><span data-ttu-id="ff6a8-255">Consigli</span><span class="sxs-lookup"><span data-stu-id="ff6a8-255">Recommendations</span></span>

* <span data-ttu-id="ff6a8-256">Progettare il contenuto per la visualizzazione ottimale distanza di 2 minuti.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-256">Design content for the optimal viewing distance of 2m.</span></span>
* <span data-ttu-id="ff6a8-257">Impostare la distanza di rendering ritaglio a 85cm con fadeout del contenuto, iniziando in corrispondenza di 1 milione.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-257">Set the clipping render distance to 85cm with fadeout of content starting at 1m.</span></span>
* <span data-ttu-id="ff6a8-258">Per vntana fermo che devono visualizzare più vicino, il piano di ritaglio debba essere non supera i 30cm e fadeout deve iniziare almeno 10cm dal piano di ritaglio.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-258">For stationary holograms that need closer viewing, the clipping plane should be no closer than 30cm and fadeout should start at least 10cm away from the clipping plane.</span></span>

### <a name="resources"></a><span data-ttu-id="ff6a8-259">Risorse</span><span class="sxs-lookup"><span data-stu-id="ff6a8-259">Resources</span></span>

* [<span data-ttu-id="ff6a8-260">Eseguire il rendering di distanza</span><span class="sxs-lookup"><span data-stu-id="ff6a8-260">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="ff6a8-261">Punto focale in Unity</span><span class="sxs-lookup"><span data-stu-id="ff6a8-261">Focus point in Unity</span></span>](focus-point-in-unity.md)
* [<span data-ttu-id="ff6a8-262">Esperimenti con scala</span><span class="sxs-lookup"><span data-stu-id="ff6a8-262">Experimenting with scale</span></span>](scale.md#experimenting-with-scale)
* [<span data-ttu-id="ff6a8-263">Testo, la dimensione del carattere consigliato</span><span class="sxs-lookup"><span data-stu-id="ff6a8-263">Text, Recommended font size</span></span>](typography.md#recommended-font-size)

## <a name="depth-switching"></a><span data-ttu-id="ff6a8-264">Cambio di profondità</span><span class="sxs-lookup"><span data-stu-id="ff6a8-264">Depth switching</span></span>

<span data-ttu-id="ff6a8-265">Indipendentemente dall'area di visualizzazione dei problemi di fattore di comfort, richiede all'utente di cambiare frequentemente o rapidamente tra vicino e lontano focale oggetti (inclusi ologrammi e il contenuto reale) possono causare fatica oculomotor e disturbo generale.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-265">Regardless of viewing zone of comfort issues, demands for the user to switch frequently or quickly between near and far focal objects (including holograms and real-world content) can lead to oculomotor fatigue, and general discomfort.</span></span>

### <a name="device-impact"></a><span data-ttu-id="ff6a8-266">Impatto di dispositivo</span><span class="sxs-lookup"><span data-stu-id="ff6a8-266">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="ff6a8-267"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="ff6a8-267"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="ff6a8-268"><a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></span><span class="sxs-lookup"><span data-stu-id="ff6a8-268"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="ff6a8-269">✔️</span><span class="sxs-lookup"><span data-stu-id="ff6a8-269">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="ff6a8-270">✔️</span><span class="sxs-lookup"><span data-stu-id="ff6a8-270">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="ff6a8-271">Criteri di qualità</span><span class="sxs-lookup"><span data-stu-id="ff6a8-271">Quality criteria</span></span>

|  <span data-ttu-id="ff6a8-272">Migliore</span><span class="sxs-lookup"><span data-stu-id="ff6a8-272">Best</span></span>  |  <span data-ttu-id="ff6a8-273">Soddisfa</span><span class="sxs-lookup"><span data-stu-id="ff6a8-273">Meets</span></span> |  <span data-ttu-id="ff6a8-274">esito negativo</span><span class="sxs-lookup"><span data-stu-id="ff6a8-274">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="ff6a8-275">Profondità naturale o limitato cambio che non causa l'utente a e innaturali reimpostare lo stato attivo.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-275">Limited or natural depth switching that doesn’t cause the user to unnaturally refocus.</span></span> | <span data-ttu-id="ff6a8-276">Profondità improvviso si tratta di core e progettata nell'esperienza delle app, profondità improvviso switch o che sia causato dal contenuto del mondo reale imprevisto.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-276">Abrupt depth switch this is core and designed into the app experience, or abrupt depth switch that is caused by unexpected real-world content.</span></span> | <span data-ttu-id="ff6a8-277">Opzione profondità coerente, o profondità improvviso cambio che non è necessaria o core per l'esperienza delle app.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-277">Consistent depth switch, or abrupt depth switching that isn’t necessary or core to the app experience.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="ff6a8-278">Consente di misurare</span><span class="sxs-lookup"><span data-stu-id="ff6a8-278">How to measure</span></span>

* <span data-ttu-id="ff6a8-279">Se l'app richiede all'utente in modo coerente e/o in modo anomalo cambiare lo stato attivo di profondità, sussiste profondità cambio problema.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-279">If the app requires the user to consistently and/or abruptly change depth focus, there is depth switching problem.</span></span>

### <a name="recommendations"></a><span data-ttu-id="ff6a8-280">Consigli</span><span class="sxs-lookup"><span data-stu-id="ff6a8-280">Recommendations</span></span>

* <span data-ttu-id="ff6a8-281">Mantenere il contenuto principale a un piano focale coerente e assicurarsi che il piano di stabilizzazione corrisponda al piano focale.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-281">Keep primary content at a consistent focal plane and make sure the stabilization plane matches the focal plane.</span></span> <span data-ttu-id="ff6a8-282">Ciò può ridurre fatica oculomotor e dello spostamento ologrammi imprevisto.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-282">This will alleviate oculomotor fatigue and unexpected hologram movement.</span></span>

### <a name="resources"></a><span data-ttu-id="ff6a8-283">Risorse</span><span class="sxs-lookup"><span data-stu-id="ff6a8-283">Resources</span></span>

* [<span data-ttu-id="ff6a8-284">Eseguire il rendering di distanza</span><span class="sxs-lookup"><span data-stu-id="ff6a8-284">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="ff6a8-285">Punto focale in Unity</span><span class="sxs-lookup"><span data-stu-id="ff6a8-285">Focus point in Unity</span></span>](focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a><span data-ttu-id="ff6a8-286">Utilizzo dell'audio spaziale</span><span class="sxs-lookup"><span data-stu-id="ff6a8-286">Use of spatial sound</span></span>

<span data-ttu-id="ff6a8-287">Nella realtà mista di Windows, il motore di audio fornisce il componente acustico dell'esperienza di realtà mista simulando 3D audio con simulazioni ambientali, distanza e direzione.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-287">In Windows Mixed Reality, the audio engine provides the aural component of the mixed reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="ff6a8-288">Utilizzando spaziale audio in un'applicazione consente agli sviluppatori di inserire convincente suoni in uno spazio dimensionale 3 (sfera) per l'utente.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-288">Using spatial sound in an application allows developers to convincingly place sounds in a 3 dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="ff6a8-289">Tali suoni risulterà quindi come se provenienti da oggetti fisici reali o vntana la realtà mista nelle vicinanze dell'utente.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-289">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="ff6a8-290">Spaziale audio è uno strumento potente per full immersion, accessibilità e progettazione dell'esperienza utente nelle applicazioni di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-290">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

### <a name="device-impact"></a><span data-ttu-id="ff6a8-291">Impatto di dispositivo</span><span class="sxs-lookup"><span data-stu-id="ff6a8-291">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="ff6a8-292"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="ff6a8-292"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="ff6a8-293"><a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></span><span class="sxs-lookup"><span data-stu-id="ff6a8-293"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="ff6a8-294">✔️</span><span class="sxs-lookup"><span data-stu-id="ff6a8-294">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="ff6a8-295">✔️</span><span class="sxs-lookup"><span data-stu-id="ff6a8-295">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="ff6a8-296">Criteri di qualità</span><span class="sxs-lookup"><span data-stu-id="ff6a8-296">Quality criteria</span></span>

|  <span data-ttu-id="ff6a8-297">Migliore</span><span class="sxs-lookup"><span data-stu-id="ff6a8-297">Best</span></span>  |  <span data-ttu-id="ff6a8-298">Soddisfa</span><span class="sxs-lookup"><span data-stu-id="ff6a8-298">Meets</span></span> |  <span data-ttu-id="ff6a8-299">esito negativo</span><span class="sxs-lookup"><span data-stu-id="ff6a8-299">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="ff6a8-300">Audio è logicamente spatialized e l'esperienza utente in modo appropriato Usa suono per assistere con feedback utente e di individuazione oggetti.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-300">Sound is logically spatialized, and the UX appropriately uses sound to assist with object discovery and user feedback.</span></span> <span data-ttu-id="ff6a8-301">Audio è naturale e pertinenti agli oggetti e normalizzati tra lo scenario.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-301">Sound is natural and relevant to objects and normalized across the scenario.</span></span> | <span data-ttu-id="ff6a8-302">Spaziale audio è utilizzata in modo appropriato per believability ma mancante come mezzo per facilitare l'individuazione e commenti degli utenti.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-302">Spatial audio is used appropriately for believability but missing as means to help with user feedback and discoverability.</span></span> | <span data-ttu-id="ff6a8-303">File audio non è spatialized come previsto, e/o mancanza di suono per assistere l'utente entro l'esperienza utente.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-303">Sound is not spatialized as expected, and/or lack of sound to assist user within the UX.</span></span> <span data-ttu-id="ff6a8-304">O audio spaziale non è stato considerato o la progettazione dello scenario.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-304">Or spatial audio was not considered or used in the design of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="ff6a8-305">Consente di misurare</span><span class="sxs-lookup"><span data-stu-id="ff6a8-305">How to measure</span></span>

* <span data-ttu-id="ff6a8-306">In generale, suoni rilevanti devono creare da vntana destinazione (ad es., suono cortecce provenienti da holographic dog.)</span><span class="sxs-lookup"><span data-stu-id="ff6a8-306">In general, relevant sounds should emit from target holograms (eg., bark sound coming from holographic dog.)</span></span>
* <span data-ttu-id="ff6a8-307">Segnali audio devono essere usate in tutta l'esperienza utente per assistere l'utente con commenti e suggerimenti né la conoscenza delle azioni all'esterno della cornice holographic.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-307">Sound cues should be used throughout the UX to assist the user with feedback or awareness of actions outside the holographic frame.</span></span>

### <a name="recommendations"></a><span data-ttu-id="ff6a8-308">Consigli</span><span class="sxs-lookup"><span data-stu-id="ff6a8-308">Recommendations</span></span>

* <span data-ttu-id="ff6a8-309">Usare spaziale audio quale supporto per interfacce utente e di individuazione dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-309">Use spatial audio to assist with object discovery and user interfaces.</span></span>
* <span data-ttu-id="ff6a8-310">Suoni reale funzionano meglio synthesize o file audio non naturale.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-310">Real sounds work better than synthesize or unnatural sound.</span></span>
* <span data-ttu-id="ff6a8-311">La maggior parte dei suoni dovrebbero essere spatialized.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-311">Most sounds should be spatialized.</span></span>
* <span data-ttu-id="ff6a8-312">Evitare di istanze di emissione FixIt invisibile.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-312">Avoid invisible emitters.</span></span>
* <span data-ttu-id="ff6a8-313">Evitare di mascheramento spaziale.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-313">Avoid spatial masking.</span></span>
* <span data-ttu-id="ff6a8-314">Normalizza tutti i file audio.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-314">Normalize all sounds.</span></span>

### <a name="resources"></a><span data-ttu-id="ff6a8-315">Risorse</span><span class="sxs-lookup"><span data-stu-id="ff6a8-315">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="ff6a8-316">Documentazione</span><span class="sxs-lookup"><span data-stu-id="ff6a8-316">Documentation</span></span>

* [<span data-ttu-id="ff6a8-317">Audio spaziale</span><span class="sxs-lookup"><span data-stu-id="ff6a8-317">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="ff6a8-318">Progettazione dell'audio spaziale</span><span class="sxs-lookup"><span data-stu-id="ff6a8-318">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="ff6a8-319">Audio spaziale in Unity</span><span class="sxs-lookup"><span data-stu-id="ff6a8-319">Spatial sound in Unity</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="ff6a8-320">Case study, spaziali audio per HoloTour</span><span class="sxs-lookup"><span data-stu-id="ff6a8-320">Case study, Spatial sound for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="ff6a8-321">Case study, utilizzando spaziale audio in RoboRaid</span><span class="sxs-lookup"><span data-stu-id="ff6a8-321">Case study, Using spatial sound in RoboRaid</span></span>](case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="ff6a8-322">Strumenti ed esercitazioni</span><span class="sxs-lookup"><span data-stu-id="ff6a8-322">Tools and tutorials</span></span>

* [<span data-ttu-id="ff6a8-323">Spaziale MR 220: Audio spaziale</span><span class="sxs-lookup"><span data-stu-id="ff6a8-323">MR Spatial 220: Spatial sound</span></span>](holograms-220.md)
* [<span data-ttu-id="ff6a8-324">MRToolkit, Spatial Audio</span><span class="sxs-lookup"><span data-stu-id="ff6a8-324">MRToolkit, Spatial Audio</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a><span data-ttu-id="ff6a8-325">Concentrarsi sui limiti holographic frame (campo di visualizzazione)</span><span class="sxs-lookup"><span data-stu-id="ff6a8-325">Focus on holographic frame (FOV) boundaries</span></span>

<span data-ttu-id="ff6a8-326">Esperienze utente ben progettata possono creare e gestire un contesto utile dell'ambiente virtuale che si estende sugli utenti.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-326">Well-designed user experiences can create and maintain useful context of the virtual environment that extends around the users.</span></span> <span data-ttu-id="ff6a8-327">Ridurre l'effetto dei limiti del campo di visualizzazione comporta una progettazione attenta della scala del contenuto e contesto, l'uso di spaziale audio, sistemi di informazioni aggiuntive e la posizione dell'utente.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-327">Mitigating the effect of the FOV boundaries involves a thoughtful design of content scale and context, use of spatial audio, guidance systems, and the user's position.</span></span> <span data-ttu-id="ff6a8-328">Se eseguita correttamente, l'utente si sentirà che minore danneggiare i limiti del campo di visualizzazione mantenendo un'esperienza app familiarità.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-328">If done right, the user will feel less impaired by the FOV boundaries while having a comfortable app experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="ff6a8-329">Impatto di dispositivo</span><span class="sxs-lookup"><span data-stu-id="ff6a8-329">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="ff6a8-330"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="ff6a8-330"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="ff6a8-331"><a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></span><span class="sxs-lookup"><span data-stu-id="ff6a8-331"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="ff6a8-332">✔️</span><span class="sxs-lookup"><span data-stu-id="ff6a8-332">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="ff6a8-333">Criteri di qualità</span><span class="sxs-lookup"><span data-stu-id="ff6a8-333">Quality criteria</span></span>

|  <span data-ttu-id="ff6a8-334">Migliore</span><span class="sxs-lookup"><span data-stu-id="ff6a8-334">Best</span></span>  |  <span data-ttu-id="ff6a8-335">Soddisfa</span><span class="sxs-lookup"><span data-stu-id="ff6a8-335">Meets</span></span> |  <span data-ttu-id="ff6a8-336">esito negativo</span><span class="sxs-lookup"><span data-stu-id="ff6a8-336">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="ff6a8-337">Utente non perde mai contesto e la visualizzazione è comodo.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-337">User never loses context and viewing is comfortable.</span></span> <span data-ttu-id="ff6a8-338">Assistenza rapida è disponibile per gli oggetti di grandi dimensioni.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-338">Context assistance is provided for large objects.</span></span> <span data-ttu-id="ff6a8-339">L'individuazione e visualizzazione di indicazioni viene fornito per gli oggetti all'esterno della cornice.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-339">Discoverability and viewing guidance is provided for objects outside the frame.</span></span> <span data-ttu-id="ff6a8-340">In generale, progettazione di movimento e la scala del vntana sono appropriati per una visualizzazione ottimale.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-340">In general, motion design and scale of the holograms are appropriate for a comfortable viewing experience.</span></span> | <span data-ttu-id="ff6a8-341">Utente non perde mai il contesto, ma movimento collo aggiuntivo potrebbe essere necessario in casi limitati.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-341">User never loses context, but extra neck motion may be required in limited situations.</span></span> <span data-ttu-id="ff6a8-342">In alcune situazioni scalabilità comporta interrompere sia il frame verticale o orizzontale provocando alcuni movimenti collo visualizzare ologrammi vntana.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-342">In limited situations scale causes holograms to break either the vertical or horizontal frame causing some neck motion to view holograms.</span></span> | <span data-ttu-id="ff6a8-343">È necessario visualizzare vntana utente potrebbe causare una perdita di contesto e/o movimento collo coerente.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-343">User likely to lose context and/or consistent neck motion is required to view holograms.</span></span> <span data-ttu-id="ff6a8-344">Alcuna indicazione di contesto per gli oggetti grandi holographic, lo spostamento di oggetti facile perdere all'esterno della cornice senza informazioni aggiuntive di individuabilità o vntana altezza non richiede movimento collo regolari da visualizzare.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-344">No context guidance for large holographic objects, moving objects easy to lose outside the frame with no discoverability guidance, or tall holograms requires regular neck motion to view.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="ff6a8-345">Consente di misurare</span><span class="sxs-lookup"><span data-stu-id="ff6a8-345">How to measure</span></span>

* <span data-ttu-id="ff6a8-346">Contesto per ologramma (grande) viene smarrito o non riconosciuto a causa di verrà ritagliato in base ai bordi.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-346">Context for a (large) hologram is lost or not understood due to being clipped at the boundaries.</span></span>
* <span data-ttu-id="ff6a8-347">Posizione del vntana sono difficili da individuare a causa della mancanza di casting di attenzione o contenuto che si sposta rapidamente da e verso il frame holographic.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-347">Location of holograms are hard to find due to the lack of attention directors or content that rapidly moves in and out of the holographic frame.</span></span>
* <span data-ttu-id="ff6a8-348">Scenario è necessario regolare e ripetitive su e giù head movimento per verificare completamente ologramma conseguente fatica collo.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-348">Scenario requires regular and repetitive up and down head motion to fully see a hologram resulting in neck fatigue.</span></span>

### <a name="recommendations"></a><span data-ttu-id="ff6a8-349">Consigli</span><span class="sxs-lookup"><span data-stu-id="ff6a8-349">Recommendations</span></span>

* <span data-ttu-id="ff6a8-350">L'esperienza di avvio con oggetti di piccole dimensioni che adatta il campo di visualizzazione, quindi eseguire la transizione con indicatori visivi alle versioni più grande.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-350">Start the experience with small objects that fit the FOV, then transition with visual cues to larger versions.</span></span>
* <span data-ttu-id="ff6a8-351">Usare directors spaziali audio e attenzione per la ricerca di contenuto utente che non è compreso il campo di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-351">Use spatial audio and attention directors to help the user find content that is outside the FOV.</span></span>
* <span data-ttu-id="ff6a8-352">Per quanto possibile, evitare vntana che tagliano verticalmente il campo di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-352">As much as possible, avoid holograms that vertically clip the FOV.</span></span>
* <span data-ttu-id="ff6a8-353">Fornire all'utente indicazioni nell'app per la miglior visualizzazione del percorso.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-353">Provide the user with in-app guidance for best viewing location.</span></span>

### <a name="resources"></a><span data-ttu-id="ff6a8-354">Risorse</span><span class="sxs-lookup"><span data-stu-id="ff6a8-354">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="ff6a8-355">Documentazione</span><span class="sxs-lookup"><span data-stu-id="ff6a8-355">Documentation</span></span>

* [<span data-ttu-id="ff6a8-356">Frame olografico</span><span class="sxs-lookup"><span data-stu-id="ff6a8-356">Holographic frame</span></span>](holographic-frame.md)
* [<span data-ttu-id="ff6a8-357">Case Study, HoloStudio UI e conoscenze di progettazione di interazione</span><span class="sxs-lookup"><span data-stu-id="ff6a8-357">Case Study, HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [<span data-ttu-id="ff6a8-358">Scalabilità degli oggetti e gli ambienti</span><span class="sxs-lookup"><span data-stu-id="ff6a8-358">Scale of objects and environments</span></span>](scale.md)
* [<span data-ttu-id="ff6a8-359">Cursori, segnali visivi</span><span class="sxs-lookup"><span data-stu-id="ff6a8-359">Cursors, Visual cues</span></span>](cursors.md#visual-cues)

#### <a name="external-references"></a><span data-ttu-id="ff6a8-360">Riferimenti esterni</span><span class="sxs-lookup"><span data-stu-id="ff6a8-360">External references</span></span>

* [<span data-ttu-id="ff6a8-361">Molto discussi sul campo di visualizzazione</span><span class="sxs-lookup"><span data-stu-id="ff6a8-361">Much ado about the FOV</span></span>](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a><span data-ttu-id="ff6a8-362">Contenuto reagisce all'utente di posizionare</span><span class="sxs-lookup"><span data-stu-id="ff6a8-362">Content reacts to user position</span></span>

<span data-ttu-id="ff6a8-363">Ologrammi devono reagire in all'utente di posizionare in approssimativamente stesso modo in cui si "reali" oggetti.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-363">Holograms should react to the user position in roughly the same ways that "real" objects do.</span></span> <span data-ttu-id="ff6a8-364">Una considerazione di progettazione rilevanti è elementi dell'interfaccia utente che non sono necessariamente presuppongono che la posizione dell'utente è fermo e adattare al movimento dell'utente.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-364">A notable design consideration is UI elements that can't necessarily assume a user's position is stationary and adapt to the user's motion.</span></span> <span data-ttu-id="ff6a8-365">Progettazione di un'app che si adatti correttamente alla posizione utente crea un'esperienza più credibile e rendono più semplice da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-365">Designing an app that correctly adapts to user position will create a more believable experience and make it easier to use.</span></span>

### <a name="device-impact"></a><span data-ttu-id="ff6a8-366">Impatto di dispositivo</span><span class="sxs-lookup"><span data-stu-id="ff6a8-366">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="ff6a8-367"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="ff6a8-367"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="ff6a8-368"><a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></span><span class="sxs-lookup"><span data-stu-id="ff6a8-368"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="ff6a8-369">✔️</span><span class="sxs-lookup"><span data-stu-id="ff6a8-369">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="ff6a8-370">✔️</span><span class="sxs-lookup"><span data-stu-id="ff6a8-370">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="ff6a8-371">Criteri di qualità</span><span class="sxs-lookup"><span data-stu-id="ff6a8-371">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="ff6a8-372">Migliore</span><span class="sxs-lookup"><span data-stu-id="ff6a8-372">Best</span></span> </td><td> <span data-ttu-id="ff6a8-373">Il contenuto e interfaccia utente di adattarsi alle posizioni utente consentendo utente interagiscono in modo naturale con contenuto all'interno dell'ambito dello spostamento previsto per l'utente.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-373">Content and UI adapt to user positions allowing user to naturally interact with content within the scope of expected user movement.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="ff6a8-374">Soddisfa</span><span class="sxs-lookup"><span data-stu-id="ff6a8-374">Meets</span></span> </td><td> <span data-ttu-id="ff6a8-375">Interfaccia utente adatta per la posizione dell'utente, ma potrebbe impedire la visualizzazione del contenuto della chiave che richiedono all'utente di modificare la loro posizione.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-375">UI adapts to the user position, but may impede the view of key content requiring the user to adjust their position.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="ff6a8-376">esito negativo</span><span class="sxs-lookup"><span data-stu-id="ff6a8-376">Fail</span></span> </td><td><ol>
<li><span data-ttu-id="ff6a8-377">Elementi dell'interfaccia utente vengono perse o bloccati durante dell'utente che provocano lo spostamento dei controlli e innaturali tornare al (o trovare).</span><span class="sxs-lookup"><span data-stu-id="ff6a8-377">UI elements are lost or locked during movement causing user to unnaturally return to (or find) controls.</span></span></li><li><span data-ttu-id="ff6a8-378">Elementi dell'interfaccia utente limitano la visualizzazione del contenuto principale.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-378">UI elements limit the view of primary content.</span></span></li><li><span data-ttu-id="ff6a8-379">Lo spostamento dell'interfaccia utente non è ottimizzato per la visualizzazione di distanza e in particolare con momentum <a href="billboarding-and-tag-along.md">tag-along</a> elementi dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-379">UI movement is not optimized for viewing distance and momentum particularly with <a href="billboarding-and-tag-along.md">tag-along</a> UI elements.</span></span></li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="ff6a8-380">Consente di misurare</span><span class="sxs-lookup"><span data-stu-id="ff6a8-380">How to measure</span></span>

* <span data-ttu-id="ff6a8-381">Tutte le misure devono essere eseguite all'interno di un ambito ragionevole dello scenario.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-381">All measurements should be done within a reasonable scope of the scenario.</span></span> <span data-ttu-id="ff6a8-382">Durante lo spostamento di utente variano, non provano a ingannare l'app con spostamento utente estremi.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-382">While user movement will vary, don’t try to trick the app with extreme user movement.</span></span>
* <span data-ttu-id="ff6a8-383">Per gli elementi dell'interfaccia utente, controlli rilevanti devono essere disponibili indipendentemente dal movimento utente.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-383">For UI elements, relevant controls should be available regardless of user movement.</span></span> <span data-ttu-id="ff6a8-384">Ad esempio, se l'utente è la visualizzazione e analisi attorno una mappa 3D con zoom, il controllo zoom deve essere immediatamente disponibile per l'utente indipendentemente dalla posizione.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-384">For example, if the user is viewing and walking around a 3D map with zoom, the zoom control should be readily available to the user regardless of location.</span></span>

### <a name="recommendations"></a><span data-ttu-id="ff6a8-385">Consigli</span><span class="sxs-lookup"><span data-stu-id="ff6a8-385">Recommendations</span></span>

* <span data-ttu-id="ff6a8-386">L'utente è la fotocamera e controllano lo spostamento.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-386">The user is the camera and they control the movement.</span></span> <span data-ttu-id="ff6a8-387">"Let" tali unità.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-387">Let them drive.</span></span>
* <span data-ttu-id="ff6a8-388">Prendere in considerazione del billboard per testo e i sistemi consente in caso contrario, potrebbero essere bloccato world o nascosta se un utente sono stati da spostare.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-388">Consider billboarding for text and menuing systems that would otherwise be world-locked or obscured if a user were to move around.</span></span>
* <span data-ttu-id="ff6a8-389">Usare tag-along per il contenuto deve seguire l'utente pur senza impedire all'utente di visualizzare gli elementi davanti a essi.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-389">Use tag-along for content that needs to follow the user while still allowing the user to see what is in front of them.</span></span>

### <a name="resources"></a><span data-ttu-id="ff6a8-390">Risorse</span><span class="sxs-lookup"><span data-stu-id="ff6a8-390">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="ff6a8-391">Documentazione</span><span class="sxs-lookup"><span data-stu-id="ff6a8-391">Documentation</span></span>

* [<span data-ttu-id="ff6a8-392">Progettazione di interazioni</span><span class="sxs-lookup"><span data-stu-id="ff6a8-392">Interaction design</span></span>](hologram.md)
* [<span data-ttu-id="ff6a8-393">Colore, chiaro e materiale</span><span class="sxs-lookup"><span data-stu-id="ff6a8-393">Color, light, and material</span></span>](color,-light-and-materials.md)
* [<span data-ttu-id="ff6a8-394">Billboarding e tag-along</span><span class="sxs-lookup"><span data-stu-id="ff6a8-394">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="ff6a8-395">Interazioni istintive</span><span class="sxs-lookup"><span data-stu-id="ff6a8-395">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="ff6a8-396">Self-animati e locomotion utente</span><span class="sxs-lookup"><span data-stu-id="ff6a8-396">Self-motion and user locomotion</span></span>](comfort.md#self-motion-and-user-locomotion)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="ff6a8-397">Strumenti ed esercitazioni</span><span class="sxs-lookup"><span data-stu-id="ff6a8-397">Tools and tutorials</span></span>

* [<span data-ttu-id="ff6a8-398">Input MR 210: Sguardo fisso</span><span class="sxs-lookup"><span data-stu-id="ff6a8-398">MR Input 210: Gaze</span></span>](holograms-210.md)

## <a name="input-interaction-clarity"></a><span data-ttu-id="ff6a8-399">Maggiore chiarezza l'interazione dell'input</span><span class="sxs-lookup"><span data-stu-id="ff6a8-399">Input interaction clarity</span></span>

<span data-ttu-id="ff6a8-400">L'interazione di input maggiore chiarezza è fondamentale per l'usabilità dell'app e include input coerenza, approachability, l'individuabilità dei metodi di interazione.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-400">Input interaction clarity is critical to an app's usability and includes input consistency, approachability, discoverability of interaction methods.</span></span> <span data-ttu-id="ff6a8-401">Utente sarà in grado di utilizzare le interazioni comuni a livello di piattaforma senza un apprendimento.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-401">User should be able to use platform-wide common interactions without relearning.</span></span> <span data-ttu-id="ff6a8-402">Se l'app ha input personalizzato, deve essere chiaramente comunicato e dimostrato.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-402">If the app has custom input, it should be clearly communicated and demonstrated.</span></span>

### <a name="device-impact"></a><span data-ttu-id="ff6a8-403">Impatto di dispositivo</span><span class="sxs-lookup"><span data-stu-id="ff6a8-403">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="ff6a8-404"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="ff6a8-404"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="ff6a8-405"><a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></span><span class="sxs-lookup"><span data-stu-id="ff6a8-405"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="ff6a8-406">✔️</span><span class="sxs-lookup"><span data-stu-id="ff6a8-406">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="ff6a8-407">✔️</span><span class="sxs-lookup"><span data-stu-id="ff6a8-407">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="ff6a8-408">Criteri di qualità</span><span class="sxs-lookup"><span data-stu-id="ff6a8-408">Quality criteria</span></span>

|  <span data-ttu-id="ff6a8-409">Migliore</span><span class="sxs-lookup"><span data-stu-id="ff6a8-409">Best</span></span>  |  <span data-ttu-id="ff6a8-410">Soddisfa</span><span class="sxs-lookup"><span data-stu-id="ff6a8-410">Meets</span></span> |  <span data-ttu-id="ff6a8-411">esito negativo</span><span class="sxs-lookup"><span data-stu-id="ff6a8-411">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="ff6a8-412">Metodi di interazione di input siano coerenti con realtà mista di Windows fornito [materiale sussidiario](interaction-fundamentals.md).</span><span class="sxs-lookup"><span data-stu-id="ff6a8-412">Input interaction methods are consistent with Windows Mixed Reality provided [guidance](interaction-fundamentals.md).</span></span> <span data-ttu-id="ff6a8-413">Qualsiasi input personalizzato non deve essere ridondante con input standard (piuttosto utilizzo interazione standard) e deve essere chiaramente comunicato e illustrato all'utente.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-413">Any custom input should not be redundant with standard input (rather use standard interaction) and must be clearly communicated and demonstrated to the user.</span></span> | <span data-ttu-id="ff6a8-414">Analogamente agli input migliori, ma personalizzato sono ridondanti con metodi di input standard.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-414">Similar to best, but custom inputs are redundant with standard input methods.</span></span> <span data-ttu-id="ff6a8-415">Utente ancora possibile ottenere l'obiettivo e stato di avanzamento tramite l'esperienza delle app.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-415">User can still achieve the goal and progress through the app experience.</span></span> | <span data-ttu-id="ff6a8-416">Difficile da comprendere il mapping di metodo o il pulsante di input.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-416">Difficult to understand input method or button mapping.</span></span> <span data-ttu-id="ff6a8-417">È altamente personalizzato, non supporta l'input standard, non le istruzioni, di input o può causare problemi di sollecitazioni e fattore di comfort.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-417">Input is heavily customized, does not support standard input, no instructions, or likely to cause fatigue and comfort issues.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="ff6a8-418">Consente di misurare</span><span class="sxs-lookup"><span data-stu-id="ff6a8-418">How to measure</span></span>

* <span data-ttu-id="ff6a8-419">L'app Usa coerente [metodi di input standard.](interaction-fundamentals.md)</span><span class="sxs-lookup"><span data-stu-id="ff6a8-419">The app uses consistent [standard input methods.](interaction-fundamentals.md)</span></span>
* <span data-ttu-id="ff6a8-420">Se l'app ha input personalizzati, è chiaramente comunicata tramite:</span><span class="sxs-lookup"><span data-stu-id="ff6a8-420">If the app has custome input, it is clearly communicated through:</span></span>
* <span data-ttu-id="ff6a8-421">Prima esecuzione</span><span class="sxs-lookup"><span data-stu-id="ff6a8-421">First-run experience</span></span>
* <span data-ttu-id="ff6a8-422">Schermate introduttive</span><span class="sxs-lookup"><span data-stu-id="ff6a8-422">Introductory screens</span></span>
* <span data-ttu-id="ff6a8-423">Descrizioni comandi</span><span class="sxs-lookup"><span data-stu-id="ff6a8-423">Tooltips</span></span>
* <span data-ttu-id="ff6a8-424">Coach mano</span><span class="sxs-lookup"><span data-stu-id="ff6a8-424">Hand coach</span></span>
* <span data-ttu-id="ff6a8-425">Sezione della Guida</span><span class="sxs-lookup"><span data-stu-id="ff6a8-425">Help section</span></span>
* <span data-ttu-id="ff6a8-426">Voce su</span><span class="sxs-lookup"><span data-stu-id="ff6a8-426">Voice over</span></span>

### <a name="recommendations"></a><span data-ttu-id="ff6a8-427">Consigli</span><span class="sxs-lookup"><span data-stu-id="ff6a8-427">Recommendations</span></span>

* <span data-ttu-id="ff6a8-428">Usare i metodi di input standard, laddove possibile.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-428">Use standard input methods whenever possible.</span></span>
* <span data-ttu-id="ff6a8-429">Fornire le dimostrazioni, esercitazioni e le descrizioni comandi per i metodi di input non standard.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-429">Provide demonstrations, tutorials, and tooltips for non-standard input methods.</span></span>
* <span data-ttu-id="ff6a8-430">Usare un modello di interazione coerente in tutta l'app.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-430">Use a consistent interaction model throughout the app.</span></span>

### <a name="resources"></a><span data-ttu-id="ff6a8-431">Risorse</span><span class="sxs-lookup"><span data-stu-id="ff6a8-431">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="ff6a8-432">Documentazione</span><span class="sxs-lookup"><span data-stu-id="ff6a8-432">Documentation</span></span>

* [<span data-ttu-id="ff6a8-433">Interazioni istintive</span><span class="sxs-lookup"><span data-stu-id="ff6a8-433">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="ff6a8-434">Oggetti si</span><span class="sxs-lookup"><span data-stu-id="ff6a8-434">Interactable objects</span></span>](interactable-object.md)
* [<span data-ttu-id="ff6a8-435">Puntamento con la testa e attesa</span><span class="sxs-lookup"><span data-stu-id="ff6a8-435">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="ff6a8-436">Cursori</span><span class="sxs-lookup"><span data-stu-id="ff6a8-436">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="ff6a8-437">Fattore di comfort e sguardo</span><span class="sxs-lookup"><span data-stu-id="ff6a8-437">Comfort and gaze</span></span>](comfort.md#gaze-direction)
* [<span data-ttu-id="ff6a8-438">Movimenti</span><span class="sxs-lookup"><span data-stu-id="ff6a8-438">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="ff6a8-439">Input vocale</span><span class="sxs-lookup"><span data-stu-id="ff6a8-439">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="ff6a8-440">Esecuzione di comandi vocali</span><span class="sxs-lookup"><span data-stu-id="ff6a8-440">Voice commanding</span></span>](voice-design.md)
* [<span data-ttu-id="ff6a8-441">Controller del movimento</span><span class="sxs-lookup"><span data-stu-id="ff6a8-441">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="ff6a8-442">Guida alla conversione dell'input per Unity</span><span class="sxs-lookup"><span data-stu-id="ff6a8-442">Input porting guide for Unity</span></span>](input-porting-guide-for-unity.md)
* [<span data-ttu-id="ff6a8-443">Input da tastiera in Unity</span><span class="sxs-lookup"><span data-stu-id="ff6a8-443">Keyboard input in Unity</span></span>](keyboard-input-in-unity.md)
* [<span data-ttu-id="ff6a8-444">Sguardo fisso in Unity</span><span class="sxs-lookup"><span data-stu-id="ff6a8-444">Gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="ff6a8-445">Movimenti e controller del movimento in Unity</span><span class="sxs-lookup"><span data-stu-id="ff6a8-445">Gestures and motion controllers in Unity</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="ff6a8-446">Input vocale in Unity</span><span class="sxs-lookup"><span data-stu-id="ff6a8-446">Voice input in Unity</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="ff6a8-447">Input da tastiera, mouse e controller in DirectX</span><span class="sxs-lookup"><span data-stu-id="ff6a8-447">Keyboard, mouse, and controller input in DirectX</span></span>](keyboard,-mouse,-and-controller-input-in-directx.md)
* [<span data-ttu-id="ff6a8-448">Puntamento con la testa e sguardo fisso in DirectX</span><span class="sxs-lookup"><span data-stu-id="ff6a8-448">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="ff6a8-449">Mani e controller del movimento in DirectX</span><span class="sxs-lookup"><span data-stu-id="ff6a8-449">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="ff6a8-450">Input vocale in DirectX</span><span class="sxs-lookup"><span data-stu-id="ff6a8-450">Voice input in DirectX</span></span>](voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="ff6a8-451">Strumenti ed esercitazioni</span><span class="sxs-lookup"><span data-stu-id="ff6a8-451">Tools and tutorials</span></span>

* [<span data-ttu-id="ff6a8-452">Case study: L'esercizio di elaborazione più personale</span><span class="sxs-lookup"><span data-stu-id="ff6a8-452">Case study: The pursuit of more personal computing</span></span>](case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [<span data-ttu-id="ff6a8-453">Eseguire il cast di Studio: Insegnamenti di progettazione HoloStudio UI e l'interazione</span><span class="sxs-lookup"><span data-stu-id="ff6a8-453">Cast study: HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [<span data-ttu-id="ff6a8-454">App di esempio: Tabella periodico degli elementi</span><span class="sxs-lookup"><span data-stu-id="ff6a8-454">Sample app: Periodic table of the elements</span></span>](periodic-table-of-the-elements.md)
* [<span data-ttu-id="ff6a8-455">App di esempio: Modulo lunare</span><span class="sxs-lookup"><span data-stu-id="ff6a8-455">Sample app: Lunar module</span></span>](lunar-module.md)
* [<span data-ttu-id="ff6a8-456">Input MR 210: Sguardo fisso</span><span class="sxs-lookup"><span data-stu-id="ff6a8-456">MR Input 210: Gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="ff6a8-457">Input MR 211: Movimenti</span><span class="sxs-lookup"><span data-stu-id="ff6a8-457">MR Input 211: Gestures</span></span>](holograms-211.md)
* [<span data-ttu-id="ff6a8-458">Input MR 212: Voce</span><span class="sxs-lookup"><span data-stu-id="ff6a8-458">MR Input 212: Voice</span></span>](holograms-212.md)

## <a name="interactable-objects"></a><span data-ttu-id="ff6a8-459">Oggetti si</span><span class="sxs-lookup"><span data-stu-id="ff6a8-459">Interactable objects</span></span>

<span data-ttu-id="ff6a8-460">Un pulsante già da tempo, una metafora utilizzata per l'attivazione di un evento in tutto il mondo astratto 2D.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-460">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="ff6a8-461">Nel mondo tridimensionale realtà mista, non dobbiamo riguardare esclusivamente questo mondo di astrazione più.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-461">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="ff6a8-462">Qualsiasi elemento può essere un oggetto si che attiva un evento.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-462">Anything can be an Interactable object that triggers an event.</span></span> <span data-ttu-id="ff6a8-463">Un oggetto si può essere rappresentato come un elemento da una tazza di caffè sulla tabella in un fumetto mobile in modalità wireless.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-463">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="ff6a8-464">Indipendentemente dal formato, gli oggetti si devono essere chiaramente riconoscibili dall'utente tramite segnali audio e video.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-464">Regardless of the form, interactable objects should be clearly recognizable by the user through visual and audio cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="ff6a8-465">Impatto di dispositivo</span><span class="sxs-lookup"><span data-stu-id="ff6a8-465">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="ff6a8-466"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="ff6a8-466"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="ff6a8-467"><a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></span><span class="sxs-lookup"><span data-stu-id="ff6a8-467"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="ff6a8-468">✔️</span><span class="sxs-lookup"><span data-stu-id="ff6a8-468">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="ff6a8-469">✔️</span><span class="sxs-lookup"><span data-stu-id="ff6a8-469">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="ff6a8-470">Criteri di qualità</span><span class="sxs-lookup"><span data-stu-id="ff6a8-470">Quality criteria</span></span>

|  <span data-ttu-id="ff6a8-471">Migliore</span><span class="sxs-lookup"><span data-stu-id="ff6a8-471">Best</span></span>  |  <span data-ttu-id="ff6a8-472">Soddisfa</span><span class="sxs-lookup"><span data-stu-id="ff6a8-472">Meets</span></span> |  <span data-ttu-id="ff6a8-473">esito negativo</span><span class="sxs-lookup"><span data-stu-id="ff6a8-473">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="ff6a8-474">Indipendentemente dal form, gli oggetti si sono riconoscibili tramite segnali audio e video in tre stati: inattiva, destinati e selezionato.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-474">Regardless of form, interactable objects are recognizable through visual and audio cues across three states: idle, targeted, and selected.</span></span> <span data-ttu-id="ff6a8-475">"A vederla, dice" è chiaro e coerente utilizzato nell'intera esperienza di.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-475">"See it, say it" is clear and consistently used throughout the experience.</span></span> <span data-ttu-id="ff6a8-476">Gli oggetti vengono ridimensionati e distribuiti per consentire la destinazione è senza errori.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-476">Objects are scaled and distributed to allow for error free targeting.</span></span> | <span data-ttu-id="ff6a8-477">Utente può riconoscere oggetto come si grazie ai commenti di audio o oggetto visivo e di destinazione e attivare l'oggetto.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-477">User can recognize object as interactable through audio or visual feedback, and can target and activate the object.</span></span> | <span data-ttu-id="ff6a8-478">Non data segnali visivi o audio, utente in grado di riconoscere un oggetto si.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-478">Given no visual or audio cues, user cannot recognize an interactable object.</span></span> <span data-ttu-id="ff6a8-479">Errore soggetta a causa di scala di oggetto o la distanza tra gli oggetti sono interazioni.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-479">Interactions are error prone due to object scale or distance between objects.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="ff6a8-480">Consente di misurare</span><span class="sxs-lookup"><span data-stu-id="ff6a8-480">How to measure</span></span>

* <span data-ttu-id="ff6a8-481">Gli oggetti si sono riconoscibili come 'si;' tra cui pulsanti, menu e app contenuto specifico.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-481">Interactable objects are recognizable as 'interactable'; including buttons, menus, and app specific content.</span></span> <span data-ttu-id="ff6a8-482">Come regola generale non vi sarà un segnale audio e video quando la destinazione si oggetti.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-482">As a rule of thumb there should be a visual and audio cue when targeting interactable objects.</span></span>

### <a name="recommendations"></a><span data-ttu-id="ff6a8-483">Consigli</span><span class="sxs-lookup"><span data-stu-id="ff6a8-483">Recommendations</span></span>

* <span data-ttu-id="ff6a8-484">Utilizzare commenti audio e video per le interazioni.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-484">Use visual and audio feedback for interactions.</span></span>
* <span data-ttu-id="ff6a8-485">Feedback visivo deve essere differenziate per ogni input dello stato (inattivo, destinazione, selezionato)</span><span class="sxs-lookup"><span data-stu-id="ff6a8-485">Visual feedback should be differentiated for each input state (idle, targeted, selected)</span></span>
* <span data-ttu-id="ff6a8-486">Oggetti si devono essere ridimensionati e posizionati per la destinazione è senza errori.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-486">Interactable objects should be scaled and placed for error free targeting.</span></span>
* <span data-ttu-id="ff6a8-487">Gli oggetti raggruppati si (ad esempio una barra dei menu o elenco) devono avere spaziatura corretta per specificare come destinazione.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-487">Grouped interactable objects (such as a menu bar or list) should have proper spacing for targeting.</span></span>
* <span data-ttu-id="ff6a8-488">I pulsanti e menu che supportano i comandi vocali devono fornire le etichette di testo per la parola chiave di comando ("visualizzarlo, dice")</span><span class="sxs-lookup"><span data-stu-id="ff6a8-488">Buttons and menus that support voice command should provide text labels for the command keyword ("See it, say it")</span></span>

### <a name="resources"></a><span data-ttu-id="ff6a8-489">Risorse</span><span class="sxs-lookup"><span data-stu-id="ff6a8-489">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="ff6a8-490">Documentazione</span><span class="sxs-lookup"><span data-stu-id="ff6a8-490">Documentation</span></span>

* [<span data-ttu-id="ff6a8-491">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="ff6a8-491">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="ff6a8-492">Testo in Unity</span><span class="sxs-lookup"><span data-stu-id="ff6a8-492">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="ff6a8-493">Barra dell'app e rettangolo di selezione</span><span class="sxs-lookup"><span data-stu-id="ff6a8-493">App bar and bounding box</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="ff6a8-494">Esecuzione di comandi vocali</span><span class="sxs-lookup"><span data-stu-id="ff6a8-494">Voice commanding</span></span>](voice-design.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="ff6a8-495">Strumenti ed esercitazioni</span><span class="sxs-lookup"><span data-stu-id="ff6a8-495">Tools and tutorials</span></span>

* [<span data-ttu-id="ff6a8-496">Toolkit di realtà mista - UX</span><span class="sxs-lookup"><span data-stu-id="ff6a8-496">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a><span data-ttu-id="ff6a8-497">Chat room l'analisi</span><span class="sxs-lookup"><span data-stu-id="ff6a8-497">Room scanning</span></span>

<span data-ttu-id="ff6a8-498">Le app che richiedono i dati di mapping spaziale si basano sul dispositivo per raccogliere automaticamente i dati nel tempo e tra le sessioni dell'utente esamina il proprio ambiente con il dispositivo attivo.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-498">Apps that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="ff6a8-499">La completezza e la qualità dei dati dipende da diversi fattori tra cui la quantità di esplorazione che l'utente ha eseguito, quanto tempo è trascorso l'esplorazione e se gli oggetti, ad esempio le porte e mobili hanno spostata dal momento che il dispositivo analizzato l'area.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-499">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span> <span data-ttu-id="ff6a8-500">Molte App verranno analizzati i dati di mapping spaziale all'inizio dell'esperienza deve valutare se l'utente deve eseguire passaggi aggiuntivi per migliorare la qualità della mappa spaziale e la completezza.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-500">Many apps will analyze the spatial mapping data at the start of the experience to judge whether the user should perform additional steps to improve the completeness and quality of the spatial map.</span></span> <span data-ttu-id="ff6a8-501">Se l'utente è necessario per analizzare l'ambiente, clear è necessario specificare informazioni aggiuntive durante l'esperienza di analisi.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-501">If the user is required to scan the environment, clear guidance should be provided during the scanning experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="ff6a8-502">Impatto di dispositivo</span><span class="sxs-lookup"><span data-stu-id="ff6a8-502">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="ff6a8-503"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="ff6a8-503"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="ff6a8-504"><a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></span><span class="sxs-lookup"><span data-stu-id="ff6a8-504"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="ff6a8-505">✔️</span><span class="sxs-lookup"><span data-stu-id="ff6a8-505">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="ff6a8-506">Criteri di qualità</span><span class="sxs-lookup"><span data-stu-id="ff6a8-506">Quality criteria</span></span>

|  <span data-ttu-id="ff6a8-507">Migliore</span><span class="sxs-lookup"><span data-stu-id="ff6a8-507">Best</span></span>  |  <span data-ttu-id="ff6a8-508">Soddisfa</span><span class="sxs-lookup"><span data-stu-id="ff6a8-508">Meets</span></span> |  <span data-ttu-id="ff6a8-509">esito negativo</span><span class="sxs-lookup"><span data-stu-id="ff6a8-509">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="ff6a8-510">Visualizzazione della trama spaziale indicare agli utenti l'analisi sono in corso.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-510">Visualization of the spatial mesh tell users scanning is in progress.</span></span> <span data-ttu-id="ff6a8-511">Utente conosca in modo chiaro cosa fare e inizio e la fine dell'analisi.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-511">User clearly knows what to do and when the scan starts and stops.</span></span> | <span data-ttu-id="ff6a8-512">Visualizzazione della trama spaziale viene fornita, ma l'utente potrebbe non chiaramente sapere cosa fare e viene fornita alcuna informazione di stato di avanzamento.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-512">Visualization of the spatial mesh is provided, but the user may not clearly know what to do and no progress information is provided.</span></span> | <span data-ttu-id="ff6a8-513">Nessuna visualizzazione della mesh.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-513">No visualization of mesh.</span></span> <span data-ttu-id="ff6a8-514">Nessuna informazione di materiale sussidiario fornita all'utente sulla posizione in cui cercare oppure quando l'analisi avvia o arresta.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-514">No guidance information provided to the user regarding where to look, or when the scan starts/stops.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="ff6a8-515">Consente di misurare</span><span class="sxs-lookup"><span data-stu-id="ff6a8-515">How to measure</span></span>

* <span data-ttu-id="ff6a8-516">Durante un'analisi di spazio necessaria, vengono fornite istruzioni audio e video che indica dove guardare e quando avviare e arrestare l'analisi.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-516">During a required room scan, visual and audio guidance is provided indicating where to look, and when to start and stop scanning.</span></span>

### <a name="recommendations"></a><span data-ttu-id="ff6a8-517">Consigli</span><span class="sxs-lookup"><span data-stu-id="ff6a8-517">Recommendations</span></span>

* <span data-ttu-id="ff6a8-518">Indicare in che misura il volume totale in prossimità degli utenti deve far parte dell'esperienza.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-518">Indicate how much of the total volume in the users vicinity needs to be part of the experience.</span></span>
* <span data-ttu-id="ff6a8-519">Comunicano quando l'analisi viene avviata e si arresta, ad esempio un indicatore di stato.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-519">Communicate when the scan starts and stops such as a progress indicator.</span></span>
* <span data-ttu-id="ff6a8-520">Usare una visualizzazione della trama durante l'analisi.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-520">Use a visualization of the mesh during the scan.</span></span>
* <span data-ttu-id="ff6a8-521">Fornire segnali audio e video per incoraggiare l'utente di eseguire ricerche e spostarsi nella stanza.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-521">Provide visual and audio cues to encourage the user to look and move around the room.</span></span>
* <span data-ttu-id="ff6a8-522">L'utente che indicano dove è possibile per migliorare i dati.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-522">Inform the user where to go to improve the data.</span></span> <span data-ttu-id="ff6a8-523">In molti casi, potrebbe essere preferibile informare l'utente ne servano per (ad esempio, esaminare il tetto massimo, cercare dietro mobili), per ottenere la qualità di analisi necessarie.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-523">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

### <a name="resources"></a><span data-ttu-id="ff6a8-524">Risorse</span><span class="sxs-lookup"><span data-stu-id="ff6a8-524">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="ff6a8-525">Documentazione</span><span class="sxs-lookup"><span data-stu-id="ff6a8-525">Documentation</span></span>

* [<span data-ttu-id="ff6a8-526">Visualizzazione della scansione dello spazio</span><span class="sxs-lookup"><span data-stu-id="ff6a8-526">Room scan visualization</span></span>](room-scan-visualization.md)
* [<span data-ttu-id="ff6a8-527">Case study: Distribuire le funzionalità di mapping spaziale di HoloLens</span><span class="sxs-lookup"><span data-stu-id="ff6a8-527">Case study: Expanding the spatial mapping capabilities of HoloLens</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="ff6a8-528">Case study: Progettazione per HoloTour spaziale</span><span class="sxs-lookup"><span data-stu-id="ff6a8-528">Case study: Spatial sound design for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="ff6a8-529">Case study: Creazione di un'esperienza coinvolgente su in frammenti</span><span class="sxs-lookup"><span data-stu-id="ff6a8-529">Case study: Creating an immersive experience in Fragments</span></span>](case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="ff6a8-530">Strumenti ed esercitazioni</span><span class="sxs-lookup"><span data-stu-id="ff6a8-530">Tools and tutorials</span></span>

* [<span data-ttu-id="ff6a8-531">Toolkit di realtà mista - UX</span><span class="sxs-lookup"><span data-stu-id="ff6a8-531">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a><span data-ttu-id="ff6a8-532">Indicatori direzionali</span><span class="sxs-lookup"><span data-stu-id="ff6a8-532">Directional indicators</span></span>

<span data-ttu-id="ff6a8-533">In un'app di realtà mista, il contenuto sia all'esterno del campo di visualizzazione o bloccati dagli oggetti reali.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-533">In a mixed reality app, content may be outside the field of view or occluded by real-world objects.</span></span> <span data-ttu-id="ff6a8-534">Un'applicazione ben progettata renderà più facile trovare il contenuto non visibili all'utente.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-534">A well designed app will make it easier for the user to find non-visible content.</span></span> <span data-ttu-id="ff6a8-535">Indicatori direzionali avvisano un utente al contenuto importante e forniscono materiale sussidiario per il contenuto relativo alla posizione dell'utente.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-535">Directional indicators alert a user to important content and provide guidance to the content relative to the user's position.</span></span> <span data-ttu-id="ff6a8-536">Materiale sussidiario per il contenuto non visibili può richiedere la forma di istanze di emissione FixIt audio, le frecce direzionali o segnali visivi diretti.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-536">Guidance to non-visible content can take the form of sound emitters, directional arrows, or direct visual cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="ff6a8-537">Impatto di dispositivo</span><span class="sxs-lookup"><span data-stu-id="ff6a8-537">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="ff6a8-538"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="ff6a8-538"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="ff6a8-539"><a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></span><span class="sxs-lookup"><span data-stu-id="ff6a8-539"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="ff6a8-540">✔️</span><span class="sxs-lookup"><span data-stu-id="ff6a8-540">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="ff6a8-541">✔️</span><span class="sxs-lookup"><span data-stu-id="ff6a8-541">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="ff6a8-542">Criteri di qualità</span><span class="sxs-lookup"><span data-stu-id="ff6a8-542">Quality criteria</span></span>

|  <span data-ttu-id="ff6a8-543">Migliore</span><span class="sxs-lookup"><span data-stu-id="ff6a8-543">Best</span></span>  |  <span data-ttu-id="ff6a8-544">Soddisfa</span><span class="sxs-lookup"><span data-stu-id="ff6a8-544">Meets</span></span> |  <span data-ttu-id="ff6a8-545">esito negativo</span><span class="sxs-lookup"><span data-stu-id="ff6a8-545">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="ff6a8-546">Segnali audio e video direttamente guidano l'utente per il contenuto pertinente di fuori del campo di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-546">Visual and audio cues directly guide the user to relevant content outside the field of view.</span></span> | <span data-ttu-id="ff6a8-547">Una freccia o un indicatore che punta all'utente nella direzione generale del contenuto.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-547">An arrow or some indicator that points the user in the general direction of the content.</span></span> | <span data-ttu-id="ff6a8-548">Il contenuto pertinente è di fuori del campo di visualizzazione e scarsa o alcuna indicazione di percorso non viene fornito all'utente.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-548">Relevant content is outside of the field of view, and poor or no location guidance is provided to the user.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="ff6a8-549">Consente di misurare</span><span class="sxs-lookup"><span data-stu-id="ff6a8-549">How to measure</span></span>

* <span data-ttu-id="ff6a8-550">Il contenuto pertinente di fuori del campo utente visivo è individuabile tramite segnali visivi e/o audio.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-550">Relevant content outside of the user field of view is discoverable through visual and/or audio cues.</span></span>

### <a name="recommendations"></a><span data-ttu-id="ff6a8-551">Consigli</span><span class="sxs-lookup"><span data-stu-id="ff6a8-551">Recommendations</span></span>

* <span data-ttu-id="ff6a8-552">Quando il contenuto pertinente non è compreso il campo di vista dell'utente, usare gli indicatori direzionali e segnali acustici per assistere l'utente al contenuto.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-552">When relevant content is outside the user's field of view, use directional indicators and audio cues to guide the user to the content.</span></span> <span data-ttu-id="ff6a8-553">In molti casi, una guida visiva diretta è preferibile le frecce direzionali.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-553">In many cases, a direct visual guide is preferred over directional arrows.</span></span>
* <span data-ttu-id="ff6a8-554">Gli indicatori direzionali non devono essere creati nel cursore.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-554">Directional indicators should not be built into the cursor.</span></span>

### <a name="resources"></a><span data-ttu-id="ff6a8-555">Risorse</span><span class="sxs-lookup"><span data-stu-id="ff6a8-555">Resources</span></span>

* [<span data-ttu-id="ff6a8-556">Frame olografico</span><span class="sxs-lookup"><span data-stu-id="ff6a8-556">Holographic frame</span></span>](holographic-frame.md)

## <a name="data-loading"></a><span data-ttu-id="ff6a8-557">Caricamento dei dati</span><span class="sxs-lookup"><span data-stu-id="ff6a8-557">Data loading</span></span>

<span data-ttu-id="ff6a8-558">Un controllo di stato fornisce all'utente un feedback nel caso in cui sia in corso un'operazione di lunga durata.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-558">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="ff6a8-559">È possibile che l'utente non è possibile interagire con l'app quando l'indicatore di stato è visibile e può anche indicare quanto tempo il tempo di attesa potrebbe essere.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-559">It can mean that the user cannot interact with the app when the progress indicator is visible and can also indicate how long the wait time might be.</span></span>

### <a name="device-impact"></a><span data-ttu-id="ff6a8-560">Impatto di dispositivo</span><span class="sxs-lookup"><span data-stu-id="ff6a8-560">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="ff6a8-561"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="ff6a8-561"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="ff6a8-562"><a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></span><span class="sxs-lookup"><span data-stu-id="ff6a8-562"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="ff6a8-563">✔️</span><span class="sxs-lookup"><span data-stu-id="ff6a8-563">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="ff6a8-564">✔️</span><span class="sxs-lookup"><span data-stu-id="ff6a8-564">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="ff6a8-565">Criteri di qualità</span><span class="sxs-lookup"><span data-stu-id="ff6a8-565">Quality criteria</span></span>

|  <span data-ttu-id="ff6a8-566">Migliore</span><span class="sxs-lookup"><span data-stu-id="ff6a8-566">Best</span></span>  |  <span data-ttu-id="ff6a8-567">Soddisfa</span><span class="sxs-lookup"><span data-stu-id="ff6a8-567">Meets</span></span> |  <span data-ttu-id="ff6a8-568">esito negativo</span><span class="sxs-lookup"><span data-stu-id="ff6a8-568">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="ff6a8-569">Animata indicatore visivo, sotto forma di un indicatore di stato o un anello, che mostra lo stato di avanzamento durante il caricamento o l'elaborazione dati.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-569">Animated visual indicator, in the form of a progress bar or ring, showing progress during any data loading or processing.</span></span> <span data-ttu-id="ff6a8-570">L'indicatore visivo fornisce indicazioni su quanto tempo può essere l'attesa.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-570">The visual indicator provides guidance on how long the wait could be.</span></span> | <span data-ttu-id="ff6a8-571">Utente viene informato che il caricamento dei dati è in corso, ma è presente alcuna indicazione di quanto tempo può essere l'attesa.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-571">User is informed that data loading is in progress, but there is no indication of how long the wait could be.</span></span> | <span data-ttu-id="ff6a8-572">Non è il caricamento dei dati o indicatori di processo per l'attività richiede più di 5 secondi.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-572">No data loading or process indicators for task taking longer than 5 seconds.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="ff6a8-573">Consente di misurare</span><span class="sxs-lookup"><span data-stu-id="ff6a8-573">How to measure</span></span>

* <span data-ttu-id="ff6a8-574">Durante il caricamento dei dati non verificare lo stato vuoto per più di 5 secondi.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-574">During data loading verify there is no blank state for more than 5 seconds.</span></span>

### <a name="recommendations"></a><span data-ttu-id="ff6a8-575">Consigli</span><span class="sxs-lookup"><span data-stu-id="ff6a8-575">Recommendations</span></span>

* <span data-ttu-id="ff6a8-576">Fornire un animatore durante il caricamento di dati che mostra lo stato di avanzamento in qualsiasi situazione, quando l'utente potrebbe percepire questa app sono bloccati o arrestato in modo anomalo.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-576">Provide a data loading animator showing progress in any situation when the user may perceive this app to have stalled or crashed.</span></span> <span data-ttu-id="ff6a8-577">Una regola generale ragionevole è un'attività 'caricamento in corso' che potrebbe richiedere più di 5 secondi.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-577">A reasonable rule of thumb is any 'loading' activity that could take more than 5 seconds.</span></span>

### <a name="resources"></a><span data-ttu-id="ff6a8-578">Risorse</span><span class="sxs-lookup"><span data-stu-id="ff6a8-578">Resources</span></span>

* [<span data-ttu-id="ff6a8-579">Visualizzazione dello stato</span><span class="sxs-lookup"><span data-stu-id="ff6a8-579">Displaying progress</span></span>](progress.md)

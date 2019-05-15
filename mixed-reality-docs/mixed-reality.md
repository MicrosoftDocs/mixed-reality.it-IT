---
title: Che cos'è impostato su mixed realtà?
description: Questo articolo definisce realtà mista e viene illustrato dove dispositivi AR e VR semplici, nonché i dispositivi di realtà mista di Windows, ad esempio Microsoft HoloLens e auricolari coinvolgenti di realtà mista di Windows, si trovano nell'ambito di realtà mista.
author: BrandonBray
ms.author: branbray
ms.date: 03/21/2018
ms.topic: article
keywords: realtà mista, holographic, ar, vr, mr, xr, realtà aumentata, realtà virtuale, spiegazione
ms.openlocfilehash: 3f6000b3d700d7c13f1efa13a81561464f8fdad1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604810"
---
# <a name="what-is-mixed-reality"></a><span data-ttu-id="f82f8-104">Che cos'è impostato su mixed realtà?</span><span class="sxs-lookup"><span data-stu-id="f82f8-104">What is mixed reality?</span></span>

<span data-ttu-id="f82f8-105">Realtà mista è il risultato della fusione del mondo fisico con il mondo digitale.</span><span class="sxs-lookup"><span data-stu-id="f82f8-105">Mixed reality is the result of blending the physical world with the digital world.</span></span> <span data-ttu-id="f82f8-106">Realtà mista è la prossima evoluzione della interazione umana e computer e dell'ambiente e sblocca le possibilità che, prima d'ora, erano limitate a nostro imaginations.</span><span class="sxs-lookup"><span data-stu-id="f82f8-106">Mixed reality is the next evolution in human, computer, and environment interaction and unlocks possibilities that before now were restricted to our imaginations.</span></span> <span data-ttu-id="f82f8-107">Si è resa possibile da miglioramenti di visione artificiale, potenza di elaborazione grafica, tecnologia di visualizzazione e sistemi di input.</span><span class="sxs-lookup"><span data-stu-id="f82f8-107">It is made possible by advancements in computer vision, graphical processing power, display technology, and input systems.</span></span> <span data-ttu-id="f82f8-108">Il termine *realtà mista* funzionalità originariamente introdotta in un documento 1994 Paul Milgram e Fumio Kishino, "[una tassonomia dei Mixed Visualizza Visual realtà](http://etclab.mie.utoronto.ca/people/paul_dir/IEICE94/ieice.html)."</span><span class="sxs-lookup"><span data-stu-id="f82f8-108">The term *mixed reality* was originally introduced in a 1994 paper by Paul Milgram and Fumio Kishino, "[A Taxonomy of Mixed Reality Visual Displays](http://etclab.mie.utoronto.ca/people/paul_dir/IEICE94/ieice.html)."</span></span> <span data-ttu-id="f82f8-109">Il documento ha introdotto il concetto del *continuum virtuality* e incentrato sulla modalità di visualizzazione la categorizzazione della tassonomia applicato a.</span><span class="sxs-lookup"><span data-stu-id="f82f8-109">Their paper introduced the concept of the *virtuality continuum* and focused on how the categorization of taxonomy applied to displays.</span></span> <span data-ttu-id="f82f8-110">Da allora, le applicazioni di realtà mista va oltre consente di visualizzare ma include anche input ambientali, spaziale audio e posizione.</span><span class="sxs-lookup"><span data-stu-id="f82f8-110">Since then, the application of mixed reality goes beyond displays but also includes environmental input, spatial sound, and location.</span></span>

## <a name="environmental-input-and-perception"></a><span data-ttu-id="f82f8-111">Input ambientali e percezione</span><span class="sxs-lookup"><span data-stu-id="f82f8-111">Environmental input and perception</span></span>

![Diagramma di Venn di visualizzazione delle interazioni tra esseri umani, ambienti e computer](images/mixed-reality-venn-diagram-300px.png)<br> 

<span data-ttu-id="f82f8-113">Failover ultimi decenni, la relazione tra input umani e computer input è stata esplorata anche.</span><span class="sxs-lookup"><span data-stu-id="f82f8-113">Over the past several decades, the relationship between human input and computer input has been well explored.</span></span> <span data-ttu-id="f82f8-114">Contiene anche una disciplina esaminata più nota come *interazione umana computer* o uomo.</span><span class="sxs-lookup"><span data-stu-id="f82f8-114">It even has a widely studied discipline known as *human computer interaction* or HCI.</span></span> <span data-ttu-id="f82f8-115">Input dell'utente avviene tramite svariati modi, tra cui tastiere, mice, touch, input penna, vocale e persino rilevamento di base Kinect.</span><span class="sxs-lookup"><span data-stu-id="f82f8-115">Human input happens through a variety of means including keyboards, mice, touch, ink, voice, and even Kinect skeletal tracking.</span></span>

<span data-ttu-id="f82f8-116">Miglioramenti di elaborazione e i sensori sono che danno luogo a una nuova area di input del computer da ambienti.</span><span class="sxs-lookup"><span data-stu-id="f82f8-116">Advancements in sensors and processing are giving rise to a new area of computer input from environments.</span></span> <span data-ttu-id="f82f8-117">L'interazione tra i computer e gli ambienti è conoscenza dell'ambiente in modo efficace, oppure *percezione*.</span><span class="sxs-lookup"><span data-stu-id="f82f8-117">The interaction between computers and environments is effectively environmental understanding, or *perception*.</span></span> <span data-ttu-id="f82f8-118">Di conseguenza vengono chiamati i nomi delle API di Windows che rivelano informazioni ambientali il [percezione API](https://docs.microsoft.com/uwp/api/Windows.Perception).</span><span class="sxs-lookup"><span data-stu-id="f82f8-118">Hence the API names in Windows that reveal environmental information are called the [perception APIs](https://docs.microsoft.com/uwp/api/Windows.Perception).</span></span> <span data-ttu-id="f82f8-119">Input ambientali acquisisce operazioni come posizione di una persona in tutto il mondo (ad esempio, [rilevamento head](coordinate-systems.md)), aree e confini (ad esempio [mapping spaziale](spatial-mapping.md) e [understanding spaziali](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)), illuminazione, suoni ambientali, riconoscimento dell'oggetto e percorso.</span><span class="sxs-lookup"><span data-stu-id="f82f8-119">Environmental input captures things like a person's position in the world (e.g. [head tracking](coordinate-systems.md)), surfaces and boundaries (e.g. [spatial mapping](spatial-mapping.md) and [spatial understanding](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)), ambient lighting, environmental sound, object recognition, and location.</span></span>

<span data-ttu-id="f82f8-120">A questo punto, la combinazione di tutti i computer tre – l'elaborazione, input umano e ambientali input: imposta la possibilità di creare esperienze di realtà mista true.</span><span class="sxs-lookup"><span data-stu-id="f82f8-120">Now, the combination of all three – computer processing, human input, and environmental input – sets the opportunity to create true mixed reality experiences.</span></span> <span data-ttu-id="f82f8-121">Spostamento all'interno del mondo fisico può essere convertita al movimento del mondo digitale.</span><span class="sxs-lookup"><span data-stu-id="f82f8-121">Movement through the physical world can translate to movement in the digital world.</span></span> <span data-ttu-id="f82f8-122">I limiti nel mondo fisico possono influenzare esperienze delle applicazioni, ad esempio di gioco, in tutto il mondo digitale.</span><span class="sxs-lookup"><span data-stu-id="f82f8-122">Boundaries in the physical world can influence application experiences, such as game play, in the digital world.</span></span> <span data-ttu-id="f82f8-123">Senza l'input dell'ambiente, non è possibile blend esperienze tra alla realtà digitale e fisica.</span><span class="sxs-lookup"><span data-stu-id="f82f8-123">Without environmental input, experiences cannot blend between the physical and digital realities.</span></span>

## <a name="the-mixed-reality-spectrum"></a><span data-ttu-id="f82f8-124">Lo spettro di realtà mista</span><span class="sxs-lookup"><span data-stu-id="f82f8-124">The mixed reality spectrum</span></span>

<span data-ttu-id="f82f8-125">Poiché realtà mista è la combinazione del mondo fisico e mondo digitale, ne consegue definiscono le entità finali polare una gamma noto come il continuum virtuality.</span><span class="sxs-lookup"><span data-stu-id="f82f8-125">Since mixed reality is the blending of the physical world and digital world, these two realities define the polar ends of a spectrum known as the virtuality continuum.</span></span> <span data-ttu-id="f82f8-126">Per semplicità, si fanno riferimento a questo elemento come il *spettro di realtà mista*.</span><span class="sxs-lookup"><span data-stu-id="f82f8-126">For simplicity, we refer to this as the *mixed reality spectrum*.</span></span> <span data-ttu-id="f82f8-127">Sul lato sinistro abbiamo realtà fisico in cui il nostro esseri umani, sono presenti.</span><span class="sxs-lookup"><span data-stu-id="f82f8-127">On the left-hand side we have physical reality in which we, humans, exist.</span></span> <span data-ttu-id="f82f8-128">Sul lato destro abbiamo in realtà digitale corrispondente.</span><span class="sxs-lookup"><span data-stu-id="f82f8-128">Then on the right-hand side we have the corresponding digital reality.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/_xpI0JosYUk]

<span data-ttu-id="f82f8-129">La maggior parte dei telefoni cellulari sul mercato non hanno oggi little a nessuna funzionalità di comprensione dell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="f82f8-129">Most mobile phones on the market today have little to no environmental understanding capabilities.</span></span> <span data-ttu-id="f82f8-130">In questo modo l'esperienza utente che offrono non è possibile combinare tra le realtà digitali e fisiche.</span><span class="sxs-lookup"><span data-stu-id="f82f8-130">Thus the experiences they offer cannot mix between physical and digital realities.</span></span> <span data-ttu-id="f82f8-131">L'esperienza utente della sovrimpressione grafica su flussi video del mondo fisico vengono *realtà aumentata*, e le esperienze che nasconde i colori di visualizzazione per offrire un'esperienza digitale sono *realtà virtuale*.</span><span class="sxs-lookup"><span data-stu-id="f82f8-131">The experiences that overlay graphics on video streams of the physical world are *augmented reality*, and the experiences that occlude your view to present a digital experience are *virtual reality*.</span></span> <span data-ttu-id="f82f8-132">Come si può notare, è l'esperienza utente abilitato tra questi due estremi *realtà mista*:</span><span class="sxs-lookup"><span data-stu-id="f82f8-132">As you can see, the experiences enabled between these two extremes is *mixed reality*:</span></span>
* <span data-ttu-id="f82f8-133">Inizia con il mondo fisico, l'inserimento di un oggetto digitale, ad esempio ologramma, come se fosse effettivamente presente.</span><span class="sxs-lookup"><span data-stu-id="f82f8-133">Starting with the physical world, placing a digital object, such as a hologram, as if it was really there.</span></span>
* <span data-ttu-id="f82f8-134">Inizia con il mondo fisico, una rappresentazione in forma digitale di un'altra persona – un avatar: Mostra la posizione in cui essi sono stati permanente quando si esce da Lotus notes.</span><span class="sxs-lookup"><span data-stu-id="f82f8-134">Starting with the physical world, a digital representation of another person – an avatar – shows the location where they were standing when leaving notes.</span></span> <span data-ttu-id="f82f8-135">In altre parole, esperienze che rappresentano la collaborazione asincrona in diversi momenti nel tempo.</span><span class="sxs-lookup"><span data-stu-id="f82f8-135">In other words, experiences that represent asynchronous collaboration at different points in time.</span></span>
* <span data-ttu-id="f82f8-136">A partire da un mondo digitale, fisici dal mondo fisico, ad esempio pareti e mobili, vengono visualizzati i limiti digitale all'interno di un per consentire agli utenti di evitare gli oggetti fisici.</span><span class="sxs-lookup"><span data-stu-id="f82f8-136">Starting with a digital world, physical boundaries from the physical world, such as walls and furniture, appear digitally within the experience to help users avoid physical objects.</span></span>

![Lo spettro di realtà mista](images/mixed-reality-spectrum-550px.png)

<span data-ttu-id="f82f8-138">Più realtà aumentata e offerte di realtà virtuale disponibili oggi rappresentano una piccola parte di questo spettro.</span><span class="sxs-lookup"><span data-stu-id="f82f8-138">Most augmented reality and virtual reality offerings available today represent a very small part of this spectrum.</span></span> <span data-ttu-id="f82f8-139">Sono, tuttavia, subset dello spettro realtà mista più grande.</span><span class="sxs-lookup"><span data-stu-id="f82f8-139">They are, however, subsets of the larger mixed reality spectrum.</span></span> <span data-ttu-id="f82f8-140">Windows 10 viene compilato con l'intero spettro presente e consente la fusione digitale rappresentazioni delle persone, luoghi e cose con il mondo reale.</span><span class="sxs-lookup"><span data-stu-id="f82f8-140">Windows 10 is built with the entire spectrum in mind, and allows blending digital representations of people, places and things with the real world.</span></span>

![Tipi di dispositivi nello spettro di realtà mista](images/mixed-reality-spectrum-device-types-550px.png)

<span data-ttu-id="f82f8-142">Esistono due tipi principali di dispositivi che offrono esperienze di realtà mista di Windows:</span><span class="sxs-lookup"><span data-stu-id="f82f8-142">There are two main types of devices that deliver Windows Mixed Reality experiences:</span></span>
1. <span data-ttu-id="f82f8-143">**Dispositivi holographic.**</span><span class="sxs-lookup"><span data-stu-id="f82f8-143">**Holographic devices.**</span></span> <span data-ttu-id="f82f8-144">Questi sono caratterizzati dalla capacità del dispositivo di inserire contenuto digitale nel mondo reale, come se fosse effettivamente presente.</span><span class="sxs-lookup"><span data-stu-id="f82f8-144">These are characterized by the device's ability to place digital content in the real world as if it were really there.</span></span>
2. <span data-ttu-id="f82f8-145">**Dispositivi coinvolgente e concreto.**</span><span class="sxs-lookup"><span data-stu-id="f82f8-145">**Immersive devices.**</span></span> <span data-ttu-id="f82f8-146">Questi sono caratterizzati dalla capacità del dispositivo di creazione di un senso di "presenza": se si nasconde il mondo fisico e la relativa sostituzione con un'esperienza digitale.</span><span class="sxs-lookup"><span data-stu-id="f82f8-146">These are characterized by the device's ability to create a sense of "presence" – hiding the physical world and replacing it with a digital experience.</span></span>

<table>
<tr>
<th width="20%"> <span data-ttu-id="f82f8-147">Caratteristica</span><span class="sxs-lookup"><span data-stu-id="f82f8-147">Characteristic</span></span></th><th width="40%"> <span data-ttu-id="f82f8-148">Dispositivi holographic</span><span class="sxs-lookup"><span data-stu-id="f82f8-148">Holographic Devices</span></span></th><th width="40%"> <span data-ttu-id="f82f8-149">Dispositivi coinvolgenti</span><span class="sxs-lookup"><span data-stu-id="f82f8-149">Immersive Devices</span></span></th>
</tr><tr>
<td> <span data-ttu-id="f82f8-150">Dispositivo di esempio</span><span class="sxs-lookup"><span data-stu-id="f82f8-150">Example Device</span></span></td><td> <span data-ttu-id="f82f8-151">Microsoft HoloLens</span><span class="sxs-lookup"><span data-stu-id="f82f8-151">Microsoft HoloLens</span></span><br /> <img alt="Microsoft HoloLens image" width="300" height="169" src="images/mshololens-hero1-whitbg-rgb-300px.png" /></td><td> <span data-ttu-id="f82f8-152">Acer Windows misti realtà Development Edition</span><span class="sxs-lookup"><span data-stu-id="f82f8-152">Acer Windows Mixed Reality Development Edition</span></span><br /> <img alt="Acer Windows Mixed Reality Development Edition image" width="300" height="169" src="images/acer-windows-mixed-reality-development-edition-headset-300px.jpg" /></td>
</tr><tr>
<td> <span data-ttu-id="f82f8-153">Schermo</span><span class="sxs-lookup"><span data-stu-id="f82f8-153">Display</span></span></td><td> <span data-ttu-id="f82f8-154"><i>Trasparente. la visualizzazione.</i></span><span class="sxs-lookup"><span data-stu-id="f82f8-154"><i>See-through display.</i></span></span> <span data-ttu-id="f82f8-155">Consente di vedere ambiente fisico durante indossare l'auricolare.</span><span class="sxs-lookup"><span data-stu-id="f82f8-155">Allows user to see physical environment while wearing the headset.</span></span></td><td> <span data-ttu-id="f82f8-156"><i>Visualizzazione opaca.</i></span><span class="sxs-lookup"><span data-stu-id="f82f8-156"><i>Opaque display.</i></span></span> <span data-ttu-id="f82f8-157">Esclude l'ambiente fisico durante indossare l'auricolare.</span><span class="sxs-lookup"><span data-stu-id="f82f8-157">Blocks out the physical environment while wearing the headset.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="f82f8-158">Spostamento dei</span><span class="sxs-lookup"><span data-stu-id="f82f8-158">Movement</span></span></td><td> <span data-ttu-id="f82f8-159">Completa lo spostamento dei sei gradi di libertà, sia rotazione e traslazione.</span><span class="sxs-lookup"><span data-stu-id="f82f8-159">Full six-degrees-of-freedom movement, both rotation and translation.</span></span></td><td> <span data-ttu-id="f82f8-160">Completa lo spostamento dei sei gradi di libertà, sia rotazione e traslazione.</span><span class="sxs-lookup"><span data-stu-id="f82f8-160">Full six-degrees-of-freedom movement, both rotation and translation.</span></span></td>
</tr>
</table>

<span data-ttu-id="f82f8-161">Si noti che, se un dispositivo è connesso a o Windows con tethering a un computer separato (tramite cavo USB o Wi-Fi) o autonoma non (senza i limiti) non riflettono se un dispositivo è holographic o coinvolgente e concreto.</span><span class="sxs-lookup"><span data-stu-id="f82f8-161">Note, whether a device is connected to or tethered to a separate PC (via USB cable or Wi-Fi) or self-contained (untethered) does not reflect whether a device is holographic or immersive.</span></span> <span data-ttu-id="f82f8-162">Certamente, funzionalità che migliorano la mobilità lead a un'esperienza ottimale e coinvolgenti e holographic dispositivi con tethering oppure illimitata.</span><span class="sxs-lookup"><span data-stu-id="f82f8-162">Certainly, features that improve mobility lead to better experiences and both holographic and immersive devices could be tethered or untethered.</span></span>

## <a name="devices-and-experiences"></a><span data-ttu-id="f82f8-163">I dispositivi e le esperienze</span><span class="sxs-lookup"><span data-stu-id="f82f8-163">Devices and experiences</span></span>

<span data-ttu-id="f82f8-164">Tecnologico è ciò che ha abilitato esperienze di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="f82f8-164">Technological advancement is what has enabled mixed reality experiences.</span></span> <span data-ttu-id="f82f8-165">Non sono presenti dispositivi subito possano eseguibili esperienze nell'intero spettro; Tuttavia, Windows 10 offre una piattaforma comune di realtà mista per i produttori di dispositivi e sviluppatori.</span><span class="sxs-lookup"><span data-stu-id="f82f8-165">There are no devices today that can run experiences across the entire spectrum; however, Windows 10 provides a common mixed reality platform for both device manufacturers and developers.</span></span> <span data-ttu-id="f82f8-166">I dispositivi attualmente possono supportare un intervallo specifico all'interno dell'intervallo di realtà mista e nel corso del tempo i nuovi dispositivi devono espandere tale intervallo.</span><span class="sxs-lookup"><span data-stu-id="f82f8-166">Devices today can support a specific range within the mixed reality spectrum, and over time new devices should expand that range.</span></span> <span data-ttu-id="f82f8-167">In futuro, holographic dispositivi diventerà più coinvolgenti e coinvolgenti dispositivi diventerà più holographic.</span><span class="sxs-lookup"><span data-stu-id="f82f8-167">In the future, holographic devices will become more immersive, and immersive devices will become more holographic.</span></span>

![In cui i dispositivi definire il layout nella gamma delle realtà mista](images/mixed-reality-spectrum-device-placement-550px.png)

<span data-ttu-id="f82f8-169">Spesso, è consigliabile considerare il tipo di esperienza di un'app o giochi sviluppatore desidera creare.</span><span class="sxs-lookup"><span data-stu-id="f82f8-169">Often, it is best to think what type of experience an app or game developer wants to create.</span></span> <span data-ttu-id="f82f8-170">L'esperienza utente verranno in genere eseguita in un momento specifico o una parte nella gamma delle.</span><span class="sxs-lookup"><span data-stu-id="f82f8-170">The experiences will typically target a specific point or part on the spectrum.</span></span> <span data-ttu-id="f82f8-171">Quindi, gli sviluppatori devono prendere in considerazione le funzionalità dei dispositivi che desiderano di destinazione.</span><span class="sxs-lookup"><span data-stu-id="f82f8-171">Then, developers should consider the capabilities of devices they want to target.</span></span> <span data-ttu-id="f82f8-172">Ad esempio, esperienze che si basano sul mondo fisico eseguirà migliore su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f82f8-172">For example, experiences that rely on the physical world will run best on HoloLens.</span></span>
* <span data-ttu-id="f82f8-173">**Verso sinistra (prossimità fisica realtà).**</span><span class="sxs-lookup"><span data-stu-id="f82f8-173">**Towards the left (near physical reality).**</span></span> <span data-ttu-id="f82f8-174">Gli utenti rimarranno disponibili nel proprio ambiente fisico e non vengono apportati a ritenere che hanno lasciato quell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="f82f8-174">Users remain present in their physical environment and are never made to believe they have left that environment.</span></span>
* <span data-ttu-id="f82f8-175">**Nella parte centrale (realtà mista completamente).**</span><span class="sxs-lookup"><span data-stu-id="f82f8-175">**In the middle (fully mixed reality).**</span></span> <span data-ttu-id="f82f8-176">Queste esperienze reali e tutto il mondo digitale perfettamente blend.</span><span class="sxs-lookup"><span data-stu-id="f82f8-176">These experiences perfectly blend the real world and the digital world.</span></span> <span data-ttu-id="f82f8-177">Gli utenti che hanno visto il film [Jumanji](https://en.wikipedia.org/wiki/Jumanji) possono risolvere le differenze tra la modalità della struttura fisica della casa in cui la storia ha avuto luogo è stata combinata con un ambiente di giungla delle.</span><span class="sxs-lookup"><span data-stu-id="f82f8-177">Viewers who have seen the movie [Jumanji](https://en.wikipedia.org/wiki/Jumanji) can reconcile how the physical structure of the house where the story took place was blended with a jungle environment.</span></span>
* <span data-ttu-id="f82f8-178">**Verso destra (vicino digitale realtà).**</span><span class="sxs-lookup"><span data-stu-id="f82f8-178">**Towards the right (near digital reality).**</span></span> <span data-ttu-id="f82f8-179">Gli utenti verificano un ambiente completamente digitale e sono a ciò che avviene durante l'ambiente fisico attorno a esse.</span><span class="sxs-lookup"><span data-stu-id="f82f8-179">Users experience a completely digital environment and are oblivious to what occurs in the physical environment around them.</span></span>


## <a name="see-also"></a><span data-ttu-id="f82f8-180">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f82f8-180">See also</span></span>
* [<span data-ttu-id="f82f8-181">Riferimento all'API: Windows.Perception</span><span class="sxs-lookup"><span data-stu-id="f82f8-181">API Reference: Windows.Perception</span></span>](https://docs.microsoft.com/uwp/api/Windows.Perception)
* [<span data-ttu-id="f82f8-182">Riferimento all'API: Windows.Perception.Spatial</span><span class="sxs-lookup"><span data-stu-id="f82f8-182">API Reference: Windows.Perception.Spatial</span></span>](https://docs.microsoft.com/uwp/api/Windows.Perception.Spatial)
* [<span data-ttu-id="f82f8-183">Riferimento all'API: Windows.Perception.Spatial.Surfaces</span><span class="sxs-lookup"><span data-stu-id="f82f8-183">API Reference: Windows.Perception.Spatial.Surfaces</span></span>](https://docs.microsoft.com/uwp/api/Windows.Perception.Spatial.Surfaces)
---
title: Manipolazione diretta con le mani
description: Panoramica del modello di input manipolazione diretta
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
ms.localizationpriority: high
keywords: realtà mista, sguardo fisso, selezione della destinazione con lo sguardo, interazione, progettazione, a portata di mano, HoloLens
ms.openlocfilehash: ed3b25fe9a7dd404d07073b578b8da13e1984cab
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435985"
---
# <a name="direct-manipulation-with-hands"></a><span data-ttu-id="78da9-104">Manipolazione diretta con le mani</span><span class="sxs-lookup"><span data-stu-id="78da9-104">Direct manipulation with hands</span></span>
<span data-ttu-id="78da9-105">La manipolazione diretta è un modello di input che consiste nel toccare gli ologrammi direttamente con le mani.</span><span class="sxs-lookup"><span data-stu-id="78da9-105">Direct manipulation is an input model that involves touching holograms directly with your hands.</span></span> <span data-ttu-id="78da9-106">L'idea alla base di questo concetto è che il comportamento degli oggetti deve essere uguale a quello che avrebbero nella realtà.</span><span class="sxs-lookup"><span data-stu-id="78da9-106">The idea behind this concept is that objects behave just as they would in the real world.</span></span> <span data-ttu-id="78da9-107">I pulsanti possono essere attivati semplicemente premendoli, gli oggetti possono essere selezionati afferrandoli e il contenuto 2D si comporta come un touchscreen virtuale.</span><span class="sxs-lookup"><span data-stu-id="78da9-107">Buttons can be activated simply by pressing them, objects can be picked up by grabbing them, and 2D content behaves like a virtual touchscreen.</span></span> <span data-ttu-id="78da9-108">Per questo motivo, è facile e anche divertente per gli utenti imparare a usare la manipolazione diretta.</span><span class="sxs-lookup"><span data-stu-id="78da9-108">This makes direct manipulation easy for users to learn, and fun.</span></span> <span data-ttu-id="78da9-109">È considerata un modello di input "da vicino", in quanto è ideale per interagire con contenuto raggiungibile stendendo le braccia.</span><span class="sxs-lookup"><span data-stu-id="78da9-109">It's considered a "near" input model in that it's best used for interacting with content within arms reach.</span></span>

<span data-ttu-id="78da9-110">La manipolazione diretta è basata sull'invito, ovvero è facile da usare.</span><span class="sxs-lookup"><span data-stu-id="78da9-110">Direct manipulation is affordance-based, meaning it's user friendly.</span></span> <span data-ttu-id="78da9-111">Non esistono movimenti simbolici da insegnare agli utenti.</span><span class="sxs-lookup"><span data-stu-id="78da9-111">There are no symbolic gestures to teach users.</span></span> <span data-ttu-id="78da9-112">Tutte le interazioni avvengono intorno a un elemento visivo che è possibile toccare o afferrare.</span><span class="sxs-lookup"><span data-stu-id="78da9-112">All interactions are built around a visual element that you can touch or grab.</span></span>

## <a name="device-support"></a><span data-ttu-id="78da9-113">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="78da9-113">Device support</span></span>

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><span data-ttu-id="78da9-114"><strong>Modello di input</strong></span><span class="sxs-lookup"><span data-stu-id="78da9-114"><strong>Input model</strong></span></span></td>
     <td><span data-ttu-id="78da9-115"><a href="hololens-hardware-details.md"><strong>HoloLens (prima generazione)</strong></a></span><span class="sxs-lookup"><span data-stu-id="78da9-115"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="78da9-116"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="78da9-116"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
     <td><span data-ttu-id="78da9-117"><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="78da9-117"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="78da9-118">Manipolazione diretta con le mani</span><span class="sxs-lookup"><span data-stu-id="78da9-118">Direct manipulation with hands</span></span></td>
     <td><span data-ttu-id="78da9-119">❌ Non supportata</span><span class="sxs-lookup"><span data-stu-id="78da9-119">❌ Not supported</span></span></td>
     <td><span data-ttu-id="78da9-120">✔️ Consigliata</span><span class="sxs-lookup"><span data-stu-id="78da9-120">✔️ Recommended</span></span></td>
     <td><span data-ttu-id="78da9-121">➕ È consigliabile un'alternativa, <a href="point-and-commit.md">puntamento e commit con le mani</a>.</span><span class="sxs-lookup"><span data-stu-id="78da9-121">➕ An alternative, <a href="point-and-commit.md">point and commit with hands</a> is recommended.</span></span></td>
    
</tr>
</table>


<span data-ttu-id="78da9-122">La manipolazione diretta è un modello di input principale in HoloLens 2 che usa il nuovo sistema di tracciamento delle mani articolato.</span><span class="sxs-lookup"><span data-stu-id="78da9-122">Direct manipulation is a primary input model on HoloLens 2, which uses the new articulated hand-tracking system.</span></span> <span data-ttu-id="78da9-123">Il modello di input è disponibile anche su visori VR immersive tramite l'uso di controller del movimento, ma non è consigliato come mezzo principale di interazione al di fuori della manipolazione di oggetti.</span><span class="sxs-lookup"><span data-stu-id="78da9-123">The input model is also available on immersive headsets through the use of motion controllers, but is not recommended as a primary means of interaction outside of object manipulation.</span></span> <span data-ttu-id="78da9-124">La manipolazione diretta non è disponibile in HoloLens (prima generazione).</span><span class="sxs-lookup"><span data-stu-id="78da9-124">Direct manipulation is not available on HoloLens (1st gen).</span></span>

<br>

---

## <a name="collidable-fingertip"></a><span data-ttu-id="78da9-125">Punta del dito di collisione</span><span class="sxs-lookup"><span data-stu-id="78da9-125">Collidable fingertip</span></span>

<span data-ttu-id="78da9-126">In HoloLens 2 le mani dell'utente vengono riconosciute e interpretate come modelli scheletrici delle mani sinistra e destra.</span><span class="sxs-lookup"><span data-stu-id="78da9-126">On HoloLens 2, the user's hands are recognized and interpreted as left and right hand skeletal models.</span></span> <span data-ttu-id="78da9-127">Per implementare l'idea di toccare gli ologrammi direttamente con le mani, in teoria si potrebbero applicare cinque collisori alle cinque punte delle dita del modello scheletrico di ogni mano.</span><span class="sxs-lookup"><span data-stu-id="78da9-127">To implement the idea of touching holograms directly with hands, ideally, five colliders could be attached to the five fingertips of each hand skeletal model.</span></span> <span data-ttu-id="78da9-128">Tuttavia, a causa della mancanza di feedback tattili, 10 punte di dita di collisione possono causare collisioni inaspettate e imprevedibili con gli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="78da9-128">However, due to the lack of tactile feedback, ten collidable fingertips can cause unexpected and unpredictable collisions with holograms.</span></span> 

<span data-ttu-id="78da9-129">Di conseguenza, è consigliabile applicare solo un collisore a ogni dito indice.</span><span class="sxs-lookup"><span data-stu-id="78da9-129">Hence, we suggest only putting a collider on each index finger.</span></span> <span data-ttu-id="78da9-130">Le punte degli indici di collisione possono comunque servire come punti di tocco attivo per i diversi movimenti di tocco che prevedono l'uso di altre dita, ad esempio la pressione con un dito, il tocco con un dito, la pressione con due dita e la pressione con cinque dita, come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="78da9-130">The collidable index fingertips can still serve as active touch points for diverse touch gestures involving other fingers, such as One-finger press, One-finger tap, Two-finger press and Five-finger press, as shown in the image below.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="78da9-131">![Punta del dito di collisione](images/Collidable-Fingertip.jpg)</span><span class="sxs-lookup"><span data-stu-id="78da9-131">![collidable fingertip](images/Collidable-Fingertip.jpg)</span></span><br>
       <span data-ttu-id="78da9-132">**Punta del dito di collisione**</span><span class="sxs-lookup"><span data-stu-id="78da9-132">**Collidable fingertip**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="78da9-133">![Pressione con un dito](images/Collidable-Fingertip-1-finger-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="78da9-133">![One-finger press](images/Collidable-Fingertip-1-finger-press.jpg)</span></span><br>
        <span data-ttu-id="78da9-134">**Pressione con un dito**</span><span class="sxs-lookup"><span data-stu-id="78da9-134">**One-finger press**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="78da9-135">![Tocco con un dito](images/Collidable-Fingertip-1-finger-tap.jpg)</span><span class="sxs-lookup"><span data-stu-id="78da9-135">![One-finger tap](images/Collidable-Fingertip-1-finger-tap.jpg)</span></span><br>
       <span data-ttu-id="78da9-136">**Tocco con un dito**</span><span class="sxs-lookup"><span data-stu-id="78da9-136">**One-finger tap**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="78da9-137">![Pressione con cinque dita](images/Collidable-Fingertip-5-finger-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="78da9-137">![Five-finger press](images/Collidable-Fingertip-5-finger-press.jpg)</span></span><br>
       <span data-ttu-id="78da9-138">**Pressione con cinque dita**</span><span class="sxs-lookup"><span data-stu-id="78da9-138">**Five-finger press**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="sphere-collider"></a><span data-ttu-id="78da9-139">Collisore sfera</span><span class="sxs-lookup"><span data-stu-id="78da9-139">Sphere collider</span></span>

<span data-ttu-id="78da9-140">Invece di usare una forma generica casuale, è consigliabile usare un collisore sferico.</span><span class="sxs-lookup"><span data-stu-id="78da9-140">Instead of using a random generic shape, we suggest you use a sphere collider.</span></span> <span data-ttu-id="78da9-141">È possibile quindi eseguirne il rendering visivo per fornire segnali migliori per la destinazione più vicina.</span><span class="sxs-lookup"><span data-stu-id="78da9-141">Then you can visually render it to provide better cues for near targeting.</span></span> <span data-ttu-id="78da9-142">Il diametro della sfera deve corrispondere allo spessore del dito indice per aumentare l'accuratezza del tocco.</span><span class="sxs-lookup"><span data-stu-id="78da9-142">The sphere's diameter should match the thickness of the index finger to increase touch accuracy.</span></span> <span data-ttu-id="78da9-143">È più facile recuperare la variabile dello spessore di un dito chiamando l'API relativa alla mano.</span><span class="sxs-lookup"><span data-stu-id="78da9-143">It's easier to retrieve the variable of finger thickness by calling the hand API.</span></span>

### <a name="fingertip-cursor"></a><span data-ttu-id="78da9-144">Cursore punta del dito</span><span class="sxs-lookup"><span data-stu-id="78da9-144">Fingertip cursor</span></span>

<span data-ttu-id="78da9-145">Oltre al rendering di una sfera di collisione sulla punta dell'indice, abbiamo creato un cursore avanzato per la punta del dito per migliorare l'esperienza interattiva di selezione della destinazione da vicino.</span><span class="sxs-lookup"><span data-stu-id="78da9-145">In addition to rendering a collidable sphere on the index fingertip, we've created an advanced fingertip cursor to interactively achieve a better near-targeting experience.</span></span> <span data-ttu-id="78da9-146">Si tratta di un cursore a forma di anello associato alla punta dell'indice.</span><span class="sxs-lookup"><span data-stu-id="78da9-146">It is a donut-shaped cursor attached to the index fingertip.</span></span> <span data-ttu-id="78da9-147">In base alla prossimità, reagisce in modo dinamico a una destinazione in termini di orientamento e dimensioni come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="78da9-147">According to proximity, it dynamically reacts to a target in terms of orientation and size as detailed below:</span></span>

* <span data-ttu-id="78da9-148">Quando un indice si sposta verso un ologramma, il cursore è sempre parallelo alla superficie dell'ologramma e si restringe gradualmente.</span><span class="sxs-lookup"><span data-stu-id="78da9-148">When an index finger moves toward a hologram, the cursor is always parallel to the hologram's surface and gradually shrinks its size accordingly.</span></span>
* <span data-ttu-id="78da9-149">Non appena il dito tocca la superficie, il cursore si riduce a un punto ed emette un evento tocco.</span><span class="sxs-lookup"><span data-stu-id="78da9-149">As soon as the finger touches the surface, the cursor shrinks into a dot and emits a touch event.</span></span>

<span data-ttu-id="78da9-150">Con il feedback interattivo, gli utenti possono eseguire attività di selezione della destinazione da vicino ad alta precisione, ad esempio l'attivazione di un collegamento ipertestuale o la pressione di un pulsante, come illustrato di seguito.</span><span class="sxs-lookup"><span data-stu-id="78da9-150">With interactive feedback, users can achieve high precision near-targeting tasks, such as triggering a hyperlink or pressing a button as shown below.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="78da9-151">![Cursore punta del dito da lontano](images/Fingertip-cursor-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="78da9-151">![Fingertip cursor far](images/Fingertip-cursor-far.jpg)</span></span><br>
       <span data-ttu-id="78da9-152">**Cursore punta del dito da lontano**</span><span class="sxs-lookup"><span data-stu-id="78da9-152">**Fingertip cursor far**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="78da9-153">![Cursore punta del dito da vicino](images/Fingertip-cursor-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="78da9-153">![Fingertip cursor near](images/Fingertip-cursor-near.jpg)</span></span><br>
        <span data-ttu-id="78da9-154">**Cursore punta del dito da vicino**</span><span class="sxs-lookup"><span data-stu-id="78da9-154">**Fingertip cursor near**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="78da9-155">![Cursore punta del dito con contatto](images/Fingertip-cursor-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="78da9-155">![Fingertip cursor contact](images/Fingertip-cursor-contact.jpg)</span></span><br>
       <span data-ttu-id="78da9-156">**Cursore punta del dito con contatto**</span><span class="sxs-lookup"><span data-stu-id="78da9-156">**Fingertip cursor contact**</span></span><br>
    :::column-end:::
:::row-end:::

<br>



## <a name="bounding-box-with-proximity-shader"></a><span data-ttu-id="78da9-157">Cubo di delimitazione con shader prossimità</span><span class="sxs-lookup"><span data-stu-id="78da9-157">Bounding box with proximity shader</span></span>

<span data-ttu-id="78da9-158">L'ologramma stesso richiede anche la possibilità di fornire feedback audio e video per compensare la mancanza di feedback tattili.</span><span class="sxs-lookup"><span data-stu-id="78da9-158">The hologram itself also requires the ability to provide both visual and audio feedback to compensate the lack of tactile feedback.</span></span> <span data-ttu-id="78da9-159">Su questa esigenza si basa il concetto di cubo di delimitazione con shader prossimità.</span><span class="sxs-lookup"><span data-stu-id="78da9-159">For that, we generate the concept of a bounding box with a proximity shader.</span></span> <span data-ttu-id="78da9-160">Un cubo di delimitazione è un'area volumetrica minima che racchiude un oggetto 3D.</span><span class="sxs-lookup"><span data-stu-id="78da9-160">A bounding box is a minimum volumetric area that encloses a 3D object.</span></span> <span data-ttu-id="78da9-161">Il cubo di delimitazione è dotato di un meccanismo di rendering interattivo denominato shader prossimità.</span><span class="sxs-lookup"><span data-stu-id="78da9-161">The bounding box has an interactive rendering mechanism called a proximity shader.</span></span> <span data-ttu-id="78da9-162">Comportamento dello shader prossimità:</span><span class="sxs-lookup"><span data-stu-id="78da9-162">The proximity shader behaves:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="78da9-163">![Posizionamento del dito (da lontano) con feedback visivo](images/bounding-box-with-proximity-shader-hover-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="78da9-163">![Hover (far) with visual feedback](images/bounding-box-with-proximity-shader-hover-far.jpg)</span></span><br>
       <span data-ttu-id="78da9-164">**Posizionamento del dito (da lontano)**</span><span class="sxs-lookup"><span data-stu-id="78da9-164">**Hover (far)**</span></span><br>
       <span data-ttu-id="78da9-165">Quando l'indice è all'interno della portata, sulla superficie del cubo di delimitazione viene messo in evidenza un punto luminoso per la punta del dito.</span><span class="sxs-lookup"><span data-stu-id="78da9-165">When the index finger is within a range, a fingertip spotlight is cast on the surface of the bounding box.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="78da9-166">![Avvicinamento del dito con feedback visivo](images/bounding-box-with-proximity-shader-hover-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="78da9-166">![Hover (near) with visual feedback](images/bounding-box-with-proximity-shader-hover-near.jpg)</span></span><br>
        <span data-ttu-id="78da9-167">**Avvicinamento del dito**</span><span class="sxs-lookup"><span data-stu-id="78da9-167">**Hover (near)**</span></span><br>
        <span data-ttu-id="78da9-168">Man mano che la punta del dito si avvicina alla superficie, il punto luminoso si restringe di conseguenza.</span><span class="sxs-lookup"><span data-stu-id="78da9-168">When the fingertip gets closer to the surface, the spotlight shrinks accordingly.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="78da9-169">![Inizio contatto](images/bounding-box-with-proximity-shader-begin-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="78da9-169">![Contact begins](images/bounding-box-with-proximity-shader-begin-contact.jpg)</span></span><br>
       <span data-ttu-id="78da9-170">**Inizio contatto**</span><span class="sxs-lookup"><span data-stu-id="78da9-170">**Contact begins**</span></span><br>
       <span data-ttu-id="78da9-171">Non appena la punta del dito tocca la superficie, l'intero cubo di delimitazione cambia colore o genera un effetto visivo per riflettere lo stato di tocco.</span><span class="sxs-lookup"><span data-stu-id="78da9-171">As soon as the fingertip touches the surface, the entire bounding box changes color or generates visual effects to reflect the touch state.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="78da9-172">![Fine contatto](images/bounding-box-with-proximity-shader-end-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="78da9-172">![Contact ends](images/bounding-box-with-proximity-shader-end-contact.jpg)</span></span><br>
       <span data-ttu-id="78da9-173">**Fine contatto**</span><span class="sxs-lookup"><span data-stu-id="78da9-173">**Contact ends**</span></span><br>
       <span data-ttu-id="78da9-174">È anche possibile attivare un effetto sonoro per migliorare il feedback del tocco visivo.</span><span class="sxs-lookup"><span data-stu-id="78da9-174">A sound effect can also be activated to enhance the visual touch feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="pressable-button"></a><span data-ttu-id="78da9-175">Pulsante a pressione</span><span class="sxs-lookup"><span data-stu-id="78da9-175">Pressable button</span></span>

<span data-ttu-id="78da9-176">Dotati di punta del dito di collisione, gli utenti sono ora pronti per interagire con un componente dell'interfaccia utente olografica di base, ovvero il pulsante a pressione.</span><span class="sxs-lookup"><span data-stu-id="78da9-176">With a collidable fingertip, users are now ready to interact with a fundamental holographic UI component, such as a pressable button.</span></span> <span data-ttu-id="78da9-177">Un pulsante a pressione è un pulsante olografico personalizzato per la pressione diretta con un dito.</span><span class="sxs-lookup"><span data-stu-id="78da9-177">A pressable button is a holographic button tailored for a direct finger press.</span></span> <span data-ttu-id="78da9-178">Anche in questo caso, a causa della mancanza di feedback tattili, un pulsante a pressione è dotato di un paio di meccanismi per ovviare ai problemi correlati al feedback tattile.</span><span class="sxs-lookup"><span data-stu-id="78da9-178">Again, due to the lack of tactile feedback, a pressable button equips a couple mechanisms to tackle tactile feedback-related issues.</span></span>

* <span data-ttu-id="78da9-179">Il primo meccanismo è un cubo di delimitazione con shader prossimità, descritto in dettaglio nella sezione precedente.</span><span class="sxs-lookup"><span data-stu-id="78da9-179">The first mechanism is a bounding box with a proximity shader, which is detailed in the previous section.</span></span> <span data-ttu-id="78da9-180">Serve per fornire un'idea più accurata di prossimità quando gli utenti si avvicinano ed entrano in contatto con un pulsante.</span><span class="sxs-lookup"><span data-stu-id="78da9-180">It gives users a better sense of proximity when they approach and make contact with a button.</span></span>
* <span data-ttu-id="78da9-181">Il secondo meccanismo è la depressione.</span><span class="sxs-lookup"><span data-stu-id="78da9-181">The second mechanism is depression.</span></span> <span data-ttu-id="78da9-182">La depressione crea un senso di pressione dopo che la punta di un dito entra in contatto con un pulsante.</span><span class="sxs-lookup"><span data-stu-id="78da9-182">Depression creates a sense of pressing down after a fingertip contacts a button.</span></span> <span data-ttu-id="78da9-183">Il meccanismo funziona in modo che il pulsante si muova in stretta relazione con la pressione del dito lungo l'asse di profondità.</span><span class="sxs-lookup"><span data-stu-id="78da9-183">The mechanism ensures that the button tightly moves with the fingertip along the depth axis.</span></span> <span data-ttu-id="78da9-184">Il pulsante può essere attivato quando raggiunge una profondità designata (alla pressione) o quando lascia la profondità (al rilascio) dopo averla attraversata.</span><span class="sxs-lookup"><span data-stu-id="78da9-184">The button can be triggered when it reaches a designated depth (on press) or leaves the depth (on release) after passing through it.</span></span>
* <span data-ttu-id="78da9-185">È consigliabile aggiungere l'effetto audio di attivazione del pulsante per migliorare il feedback.</span><span class="sxs-lookup"><span data-stu-id="78da9-185">The sound effect should be added to enhance feedback when the button is triggered.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="78da9-186">![Pulsante a pressione (lontano)](images/pressable-button-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="78da9-186">![pressable button far](images/pressable-button-far.jpg)</span></span><br>
       <span data-ttu-id="78da9-187">**Il dito è lontano**</span><span class="sxs-lookup"><span data-stu-id="78da9-187">**Finger is far away**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="78da9-188">![Pulsante a pressione (vicino)](images/pressable-button-approach.jpg)</span><span class="sxs-lookup"><span data-stu-id="78da9-188">![pressable button near](images/pressable-button-approach.jpg)</span></span><br>
        <span data-ttu-id="78da9-189">**Il dito si avvicina**</span><span class="sxs-lookup"><span data-stu-id="78da9-189">**Finger approaches**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="78da9-190">![Inizio del contatto con il pulsante a pressione](images/pressable-button-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="78da9-190">![pressable button contact begins](images/pressable-button-contact.jpg)</span></span><br>
       <span data-ttu-id="78da9-191">**Inizio contatto**</span><span class="sxs-lookup"><span data-stu-id="78da9-191">**Contact begins**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="78da9-192">![Pressione del pulsante a pressione](images/pressable-button-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="78da9-192">![pressable button press](images/pressable-button-press.jpg)</span></span><br>
       <span data-ttu-id="78da9-193">**Pressione in profondità**</span><span class="sxs-lookup"><span data-stu-id="78da9-193">**Press down**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a><span data-ttu-id="78da9-194">Interazione con uno slate 2D</span><span class="sxs-lookup"><span data-stu-id="78da9-194">2D slate interaction</span></span>

<span data-ttu-id="78da9-195">Uno slate 2D è un contenitore olografico che ospita contenuti di app 2D, ad esempio un Web browser.</span><span class="sxs-lookup"><span data-stu-id="78da9-195">A 2D slate is a holographic container hosting 2D app contents, such as a web browser.</span></span> <span data-ttu-id="78da9-196">Il concetto di progettazione per l'interazione con uno slate 2D tramite manipolazione diretta consiste nello sfruttare il modello mentale di interazione con un touchscreen fisico.</span><span class="sxs-lookup"><span data-stu-id="78da9-196">The design concept for interacting with a 2D slate via direct manipulation is to leverage the mental model of interacting with a physical touch screen.</span></span>

### <a name="to-interact-with-the-slate-contact"></a><span data-ttu-id="78da9-197">Per interagire con il contatto tramite slate</span><span class="sxs-lookup"><span data-stu-id="78da9-197">To interact with the slate contact</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="78da9-198">![Tocco](images/2d-slate-interaction-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="78da9-198">![Touch](images/2d-slate-interaction-touch.jpg)</span></span><br>
       <span data-ttu-id="78da9-199">**Tocco**</span><span class="sxs-lookup"><span data-stu-id="78da9-199">**Touch**</span></span><br>
       <span data-ttu-id="78da9-200">Usa un indice per premere un pulsante o un collegamento ipertestuale.</span><span class="sxs-lookup"><span data-stu-id="78da9-200">Use an index finger to press a hyperlink or a button.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="78da9-201">![Scorrimento](images/2d-slate-interaction-scroll2.jpg)</span><span class="sxs-lookup"><span data-stu-id="78da9-201">![Scroll](images/2d-slate-interaction-scroll2.jpg)</span></span><br>
        <span data-ttu-id="78da9-202">**Scorrimento**</span><span class="sxs-lookup"><span data-stu-id="78da9-202">**Scroll**</span></span><br>
        <span data-ttu-id="78da9-203">Usa un indice per scorrere il contenuto dello slate verso l'alto o verso il basso.</span><span class="sxs-lookup"><span data-stu-id="78da9-203">Use an index finger to scroll a slate content up and down.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="78da9-204">![Zoom](images/2d-slate-interaction-zoom2.jpg)</span><span class="sxs-lookup"><span data-stu-id="78da9-204">![Zoom](images/2d-slate-interaction-zoom2.jpg)</span></span><br>
       <span data-ttu-id="78da9-205">**Zoom**</span><span class="sxs-lookup"><span data-stu-id="78da9-205">**Zoom**</span></span><br>
       <span data-ttu-id="78da9-206">L'utente usa i due indici per eseguire lo zoom avanti e indietro del contenuto dello slate in base al movimento relativo delle dita.</span><span class="sxs-lookup"><span data-stu-id="78da9-206">The user's two index fingers are used to zoom in and out of the slate content, according to the relative motion of the fingers.</span></span>
    :::column-end:::
:::row-end:::


### <a name="for-manipulating-the-2d-slate-itself"></a><span data-ttu-id="78da9-207">Per manipolare lo slate 2D</span><span class="sxs-lookup"><span data-stu-id="78da9-207">For manipulating the 2D slate itself</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="78da9-208">![Sposta](images/manipulate-2d-slate-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="78da9-208">![Move](images/manipulate-2d-slate-move.jpg)</span></span><br>
       <span data-ttu-id="78da9-209">**Sposta**</span><span class="sxs-lookup"><span data-stu-id="78da9-209">**Move**</span></span><br>
       <span data-ttu-id="78da9-210">Sposta le mani verso angoli e i bordi per rivelare gli inviti di manipolazione più vicini.</span><span class="sxs-lookup"><span data-stu-id="78da9-210">Move your hands toward corners and edges to reveal the closest manipulation affordances.</span></span> <span data-ttu-id="78da9-211">Afferra la barra dell'ologramma nella parte superiore dello slate 2D per spostare l'intero slate.</span><span class="sxs-lookup"><span data-stu-id="78da9-211">Grab the Holobar at the top of the 2D slate, which lets you move the whole slate.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="78da9-212">![Ridimensiona](images/manipulate-2d-slate-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="78da9-212">![Scale](images/manipulate-2d-slate-scale.jpg)</span></span><br>
        <span data-ttu-id="78da9-213">**Ridimensiona**</span><span class="sxs-lookup"><span data-stu-id="78da9-213">**Scale**</span></span><br>
        <span data-ttu-id="78da9-214">Afferra gli inviti di manipolazione ed esegui un ridimensionamento uniforme tramite gli inviti degli angoli.</span><span class="sxs-lookup"><span data-stu-id="78da9-214">Grab the manipulation affordances and perform uniform scaling through the corner affordances.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="78da9-215">![Adatta il contenuto in modo dinamico](images/manipulate-2d-slate-reflow.jpg)</span><span class="sxs-lookup"><span data-stu-id="78da9-215">![Reflow](images/manipulate-2d-slate-reflow.jpg)</span></span><br>
       <span data-ttu-id="78da9-216">**Adatta il contenuto in modo dinamico**</span><span class="sxs-lookup"><span data-stu-id="78da9-216">**Reflow**</span></span><br>
       <span data-ttu-id="78da9-217">Afferra gli inviti di manipolazione e adatta il contenuto dinamicamente tramite gli inviti dei bordi.</span><span class="sxs-lookup"><span data-stu-id="78da9-217">Grab the manipulation affordances and perform reflow via the edge affordances.</span></span>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="3d-object-manipulation"></a><span data-ttu-id="78da9-218">Manipolazione di oggetti 3D</span><span class="sxs-lookup"><span data-stu-id="78da9-218">3D object manipulation</span></span>

<span data-ttu-id="78da9-219">HoloLens 2 consente agli utenti di usare le mani per indirizzare e manipolare gli oggetti olografici 3D applicando un cubo di delimitazione a ogni oggetto 3D.</span><span class="sxs-lookup"><span data-stu-id="78da9-219">HoloLens 2 lets users enable their hands to direct and manipulate 3D holographic objects by applying a bounding box to each 3D object.</span></span> <span data-ttu-id="78da9-220">Il cubo di delimitazione fornisce una migliore percezione della profondità tramite lo shader prossimità.</span><span class="sxs-lookup"><span data-stu-id="78da9-220">The bounding box provides better depth perception through its proximity shader.</span></span> <span data-ttu-id="78da9-221">Con il cubo di delimitazione sono disponibili due approcci di progettazione per la manipolazione di oggetti 3D.</span><span class="sxs-lookup"><span data-stu-id="78da9-221">With the bounding box, there are two design approaches for 3D object manipulation.</span></span>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="78da9-222">Manipolazione basata sugli inviti</span><span class="sxs-lookup"><span data-stu-id="78da9-222">Affordance-based manipulation</span></span>

<span data-ttu-id="78da9-223">Permette di manipolare l'oggetto 3D tramite un cubo di delimitazione e gli inviti di manipolazione intorno a esso.</span><span class="sxs-lookup"><span data-stu-id="78da9-223">Affordance-base manipulation lets you manipulate the 3D object through a bounding box along with the manipulation affordances around it.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="78da9-224">![Sposta](images/3d-object-manipulation-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="78da9-224">![Move](images/3d-object-manipulation-move.jpg)</span></span><br>
       <span data-ttu-id="78da9-225">**Sposta**</span><span class="sxs-lookup"><span data-stu-id="78da9-225">**Move**</span></span><br>
       <span data-ttu-id="78da9-226">Nel momento in cui la mano di un utente è vicina a un oggetto 3D, diventano visibili il cubo di delimitazione e l'invito più vicino.</span><span class="sxs-lookup"><span data-stu-id="78da9-226">As soon as a user's hand is close to a 3D object, the bounding box and the nearest affordance are revealed.</span></span> <span data-ttu-id="78da9-227">Gli utenti possono afferrare il cubo di delimitazione per spostare l'intero oggetto.</span><span class="sxs-lookup"><span data-stu-id="78da9-227">Users can grab the bounding box to move the whole object.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="78da9-228">![Ruota](images/3d-object-manipulation-rotate.jpg)</span><span class="sxs-lookup"><span data-stu-id="78da9-228">![Rotate](images/3d-object-manipulation-rotate.jpg)</span></span><br>
        <span data-ttu-id="78da9-229">**Ruota**</span><span class="sxs-lookup"><span data-stu-id="78da9-229">**Rotate**</span></span><br>
        <span data-ttu-id="78da9-230">Gli utenti possono afferrare gli inviti dei bordi per eseguire la rotazione.</span><span class="sxs-lookup"><span data-stu-id="78da9-230">Users can grab the edge affordances to rotate.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="78da9-231">![Ridimensiona](images/3d-object-manipulation-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="78da9-231">![Scale](images/3d-object-manipulation-scale.jpg)</span></span><br>
       <span data-ttu-id="78da9-232">**Ridimensiona**</span><span class="sxs-lookup"><span data-stu-id="78da9-232">**Scale**</span></span><br>
       <span data-ttu-id="78da9-233">Gli utenti possono afferrare gli inviti degli angoli per eseguire un ridimensionamento uniforme.</span><span class="sxs-lookup"><span data-stu-id="78da9-233">Users can grab the corner affordances to scale uniformly.</span></span>
    :::column-end:::
:::row-end:::

<br>


### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="78da9-234">Manipolazione non basata sugli inviti</span><span class="sxs-lookup"><span data-stu-id="78da9-234">Non-affordance based manipulation</span></span>

<span data-ttu-id="78da9-235">Non è associato alcun invito al cubo di delimitazione.</span><span class="sxs-lookup"><span data-stu-id="78da9-235">Non-affordance-based manipulation does not attach affordance to the bounding box.</span></span> <span data-ttu-id="78da9-236">Gli utenti possono solo visualizzare il cubo di delimitazione e quindi interagire direttamente con esso.</span><span class="sxs-lookup"><span data-stu-id="78da9-236">Users can only reveal the bounding box, then directly interact with it.</span></span> <span data-ttu-id="78da9-237">Se il cubo di delimitazione viene afferrato con una mano, lo spostamento e la rotazione dell'oggetto sono associati al movimento e all'orientamento della mano.</span><span class="sxs-lookup"><span data-stu-id="78da9-237">If the bounding box is grabbed with one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="78da9-238">Quando l'oggetto viene afferrato con due mani, gli utenti possono spostarlo, ridimensionarlo e ruotarlo in base al relativi movimenti delle mani.</span><span class="sxs-lookup"><span data-stu-id="78da9-238">When the object is grabbed with two hands, users can translate, scale, and rotate it according to relative motions of two hands.</span></span>

<span data-ttu-id="78da9-239">Una manipolazione specifica richiede precisione.</span><span class="sxs-lookup"><span data-stu-id="78da9-239">Specific manipulation requires precision.</span></span> <span data-ttu-id="78da9-240">È consigliabile usare la **manipolazione basata sugli inviti**, poiché offre un elevato livello di granularità.</span><span class="sxs-lookup"><span data-stu-id="78da9-240">We recommend that you use **affordance-based manipulation** because it provides a high level of granularity.</span></span> <span data-ttu-id="78da9-241">Per una manipolazione flessibile, è consigliabile usare la **manipolazione non basata sugli inviti**, perché trasmette esperienze immediate e divertenti.</span><span class="sxs-lookup"><span data-stu-id="78da9-241">For flexible manipulation, we recommend you use **non-affordance manipulation** as it allows for instant and playful experiences.</span></span>

<br>

---


## <a name="instinctual-gestures"></a><span data-ttu-id="78da9-242">Movimenti istintivi</span><span class="sxs-lookup"><span data-stu-id="78da9-242">Instinctual gestures</span></span>

<span data-ttu-id="78da9-243">Con HoloLens (prima generazione) sono stati insegnati agli utenti un paio di movimenti predefiniti, ad esempio l'apertura della mano a fiore e la simulazione del tocco.</span><span class="sxs-lookup"><span data-stu-id="78da9-243">With HoloLens (1st gen), we taught users a couple of predefined gestures, such as bloom and air tap.</span></span> <span data-ttu-id="78da9-244">Per HoloLens 2 non viene richiesto agli utenti di memorizzare movimenti simbolici.</span><span class="sxs-lookup"><span data-stu-id="78da9-244">For HoloLens 2, we don't ask users to memorize any symbolic gestures.</span></span> <span data-ttu-id="78da9-245">Tutti i movimenti richiesti agli utenti per interagire con ologrammi e contenuti sono istintivi.</span><span class="sxs-lookup"><span data-stu-id="78da9-245">All required user gestures, where users need to interact with holograms and content, are instinctual.</span></span> <span data-ttu-id="78da9-246">Per ottenere il movimento istintivo è sufficiente guidare gli utenti a eseguire gesti in base a come sono progettati gli inviti dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="78da9-246">The way to achieve instinctual gestures is to help users perform gestures through the design of UI affordances.</span></span>

<span data-ttu-id="78da9-247">Se ad esempio un oggetto o un punto di controllo deve essere afferrato avvicinando due dita, l'oggetto o il punto di controllo deve essere piccolo.</span><span class="sxs-lookup"><span data-stu-id="78da9-247">For example, if we encourage the user to grab an object or a control point with a two finger pinch, the object or the control point should be small.</span></span> <span data-ttu-id="78da9-248">Se si vuole che l'utente afferri con cinque dita, l'oggetto o il punto di controllo deve essere relativamente grande.</span><span class="sxs-lookup"><span data-stu-id="78da9-248">If we want the user to perform five finger grab, the object or the control point should be relatively large.</span></span> <span data-ttu-id="78da9-249">Lo stesso vale per i pulsanti. Un pulsante minuscolo può essere premuto solo con un singolo dito, mentre un pulsante grande indurrebbe gli utenti a premerlo con il palmo della mano.</span><span class="sxs-lookup"><span data-stu-id="78da9-249">Similar to buttons, a tiny button would limit users to press it with a single finger; a large button would encourage users to press it with their palms.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="78da9-250">![Sposta](images/instinctual-gestures-smallobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="78da9-250">![Move](images/instinctual-gestures-smallobject.jpg)</span></span><br>
       <span data-ttu-id="78da9-251">**Oggetto piccolo**</span><span class="sxs-lookup"><span data-stu-id="78da9-251">**Small object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="78da9-252">![Ruota](images/instinctual-gestures-mediumobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="78da9-252">![Rotate](images/instinctual-gestures-mediumobject.jpg)</span></span><br>
        <span data-ttu-id="78da9-253">**Oggetto medio**</span><span class="sxs-lookup"><span data-stu-id="78da9-253">**Medium object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="78da9-254">![Ridimensiona](images/instinctual-gestures-largeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="78da9-254">![Scale](images/instinctual-gestures-largeobject.jpg)</span></span><br>
       <span data-ttu-id="78da9-255">**Oggetto grande**</span><span class="sxs-lookup"><span data-stu-id="78da9-255">**Large object**</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---

<br>

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a><span data-ttu-id="78da9-256">Progettazione simmetrica tra mani e controller 6DoF</span><span class="sxs-lookup"><span data-stu-id="78da9-256">Symmetric design between hands and 6 DoF controllers</span></span>

<span data-ttu-id="78da9-257">Avrai notato che sono presenti simmetrie di interazione che è possibile tracciare tra le mani nella realtà aumentata (AR) e i controller del movimento nella realtà virtuale (VR).</span><span class="sxs-lookup"><span data-stu-id="78da9-257">You may have noticed that there are interaction parallels we can draw between hands in AR and motion controllers in VR.</span></span> <span data-ttu-id="78da9-258">Entrambi gli input possono essere usati per avviare manipolazioni dirette nei rispettivi ambienti.</span><span class="sxs-lookup"><span data-stu-id="78da9-258">Both inputs can be used to trigger direct manipulations in their respective environments.</span></span> <span data-ttu-id="78da9-259">In HoloLens 2 afferrare e trascinare con le mani a una distanza ravvicinata funziona praticamente come il pulsante usato per afferrare nei controller del movimento in WMR.</span><span class="sxs-lookup"><span data-stu-id="78da9-259">In HoloLens 2, grabbing and dragging with hands at a close distance works much the same way as the grab button does on WMR motion controllers.</span></span> <span data-ttu-id="78da9-260">In questo modo si offre una familiarità di interazione tra le due piattaforme che può rivelarsi utile se deciderai di convertire la tua applicazione da una all'altra.</span><span class="sxs-lookup"><span data-stu-id="78da9-260">This provides users with interaction familiarity between the two platforms, which might prove useful if you ever decide to port your application from one to the other.</span></span>


<br>

---


<br>

---

## <a name="optimize-with-eye-tracking"></a><span data-ttu-id="78da9-261">Ottimizzare con il tracciamento oculare</span><span class="sxs-lookup"><span data-stu-id="78da9-261">Optimize with eye tracking</span></span>

<span data-ttu-id="78da9-262">La manipolazione diretta può essere fantastica se funziona come previsto.</span><span class="sxs-lookup"><span data-stu-id="78da9-262">Direct manipulation can feel magical if it works as intended.</span></span> <span data-ttu-id="78da9-263">Ma può anche diventare frustrante se non riesci a spostare la mano in una direzione qualunque senza attivare involontariamente un ologramma.</span><span class="sxs-lookup"><span data-stu-id="78da9-263">But it can also become frustrating if you can’t move your hand anywhere without unintentionally triggering a hologram.</span></span> <span data-ttu-id="78da9-264">Il tracciamento oculare aiuta a identificare meglio l'intenzione dell'utente.</span><span class="sxs-lookup"><span data-stu-id="78da9-264">Eye tracking potentially helps to better identify what the user’s intent is.</span></span>

* <span data-ttu-id="78da9-265">**Quando**: per ridurre l'attivazione involontaria di una risposta di manipolazione.</span><span class="sxs-lookup"><span data-stu-id="78da9-265">**When**: Reduce unintentionally triggering a manipulation response.</span></span> <span data-ttu-id="78da9-266">Il tracciamento oculare consente di comprendere meglio l'attività in cui è attualmente impegnato un utente.</span><span class="sxs-lookup"><span data-stu-id="78da9-266">Eye tracking allows for better understanding what a user is currently engaged with.</span></span>
<span data-ttu-id="78da9-267">Supponi ad esempio di essere impegnato nella lettura di un testo olografico (istruzioni) e di sporgerti per afferrare uno strumento di lavoro del mondo reale.</span><span class="sxs-lookup"><span data-stu-id="78da9-267">For example, imagine you are reading through a holographic (instructional) text when reaching over to grab you real-world work tool.</span></span>

<span data-ttu-id="78da9-268">In questo modo sposti accidentalmente la mano su alcuni pulsanti olografici interattivi che non avevi notato prima (forse erano fuori del campo visivo).</span><span class="sxs-lookup"><span data-stu-id="78da9-268">By doing so, you accidentally move your hand across some interactive holographic buttons that you hadn't even noticed before (e.g. it  may be outside the user's field-of-view (FoV)).</span></span>

  <span data-ttu-id="78da9-269">In breve: se l'utente non ha guardato un ologramma per un periodo di tempo ma è stato rilevato un evento di tocco o cattura, è probabile che l'utente non intendesse in realtà interagire con l'ologramma.</span><span class="sxs-lookup"><span data-stu-id="78da9-269">Long story short: If the user hasn't looked at a hologram for a while, yet a touch or grasp event has been detected for it, it is likely that the user wasn't actually intending to interact with that hologram.</span></span>

* <span data-ttu-id="78da9-270">**Quale**:  oltre alla gestione delle attivazioni false positive, un altro esempio include una migliore identificazione degli ologrammi da afferrare o toccare dal momento che il punto di intersezione preciso potrebbe non essere chiaro dalla tua prospettiva, soprattutto in presenza di più ologrammi ravvicinati.</span><span class="sxs-lookup"><span data-stu-id="78da9-270">**Which one**:  Aside from addressing false positive activations, another example includes better identifying which holograms to grab or poke as the precise intersection point may not be clear from your perspective, especially if several holograms are positioned close to each other.</span></span>

  <span data-ttu-id="78da9-271">Anche se il tracciamento oculare in HoloLens 2 presenta limiti sull'accuratezza di determinazione dello sguardo, questa funzionalità può comunque essere molto utile per le interazioni da vicino a causa della disparità di profondità durante l'interazione con l'input mano.</span><span class="sxs-lookup"><span data-stu-id="78da9-271">While eye tracking on HoloLens 2 has limitations based on how accurately it can determine your eye gaze, this can still be very helpful for near interactions due to depth disparity when interacting with hand input.</span></span> <span data-ttu-id="78da9-272">Ciò significa che talvolta è difficile determinare se la mano si trova dietro o davanti a un ologramma, ad esempio per afferrare con precisione un widget di manipolazione.</span><span class="sxs-lookup"><span data-stu-id="78da9-272">This means that it is sometimes difficult to determine whether your hand is behind or in front of a hologram to precisely grab a manipulation widget, for example.</span></span>

* <span data-ttu-id="78da9-273">**Dove**: usa le informazioni su ciò che l'utente sta guardando con movimenti di lancio rapido.</span><span class="sxs-lookup"><span data-stu-id="78da9-273">**Where to**: Use information about what a user is looking at with quick-throwing gestures.</span></span> <span data-ttu-id="78da9-274">Afferra un ologramma e scaglialo verso la destinazione prevista.</span><span class="sxs-lookup"><span data-stu-id="78da9-274">Grab a hologram and roughly toss it toward your intended destination.</span></span>  

    <span data-ttu-id="78da9-275">Anche se questa soluzione a volte funziona correttamente, l'esecuzione di movimenti della mano può avere come risultato delle destinazioni estremamente imprecise.</span><span class="sxs-lookup"><span data-stu-id="78da9-275">While this sometimes works, quickly performing hand gestures may result in highly inaccurate destinations.</span></span> <span data-ttu-id="78da9-276">Il tracciamento oculare tuttavia può migliorare l'accuratezza del movimento.</span><span class="sxs-lookup"><span data-stu-id="78da9-276">However, eye tracking could improve the accuracy of the gesture.</span></span>

## <a name="see-also"></a><span data-ttu-id="78da9-277">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="78da9-277">See also</span></span>

* [<span data-ttu-id="78da9-278">Puntamento con la testa e commit</span><span class="sxs-lookup"><span data-stu-id="78da9-278">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="78da9-279">Puntamento e commit con le mani</span><span class="sxs-lookup"><span data-stu-id="78da9-279">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="78da9-280">Interazioni istintive</span><span class="sxs-lookup"><span data-stu-id="78da9-280">Instinctual interactions</span></span>](interaction-fundamentals.md)

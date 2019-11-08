---
title: Puntamento e commit con le mani
description: Panoramica del modello di input puntamento e commit
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: realtà mista, interazione, progettazione, HoloLens, mani, da lontano, puntamento e commit
ms.openlocfilehash: e454b7f26b402d5c168323762865d10f7feb8a17
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437678"
---
# <a name="point-and-commit-with-hands"></a><span data-ttu-id="69379-104">Puntamento e commit con le mani</span><span class="sxs-lookup"><span data-stu-id="69379-104">Point and commit with hands</span></span>

<span data-ttu-id="69379-105">Puntamento e commit con le mani è un modello di input che consente agli utenti di puntare come destinazione, selezionare e manipolare contenuto 2D e oggetti 3D fuori portata.</span><span class="sxs-lookup"><span data-stu-id="69379-105">Point and commit with hands is an input model that enables users to target, select and manipulate 2D content and 3D objects that are out of reach.</span></span> <span data-ttu-id="69379-106">Questa tecnica di interazione "da lontano" è specifica della realtà mista e non corrisponde al modo in cui le persone interagiscono naturalmente con il mondo reale.</span><span class="sxs-lookup"><span data-stu-id="69379-106">This "far" interaction technique is unique to mixed reality, and is not a way humans naturally interact with the real world.</span></span> <span data-ttu-id="69379-107">Ad esempio, nel film di supereroi *X-Men* il personaggio [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) è in grado di manipolare a distanza un oggetto lontano con le sue mani.</span><span class="sxs-lookup"><span data-stu-id="69379-107">For example, in the super hero movie, *X-Men*, the character [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) is capable of reaching out and manipulating a far object in the distance with his hands.</span></span> <span data-ttu-id="69379-108">Questa non è un'azione che gli esseri umani possono compiere nella realtà.</span><span class="sxs-lookup"><span data-stu-id="69379-108">This is not something humans can do in reality.</span></span> <span data-ttu-id="69379-109">Nella realtà aumentata (AR) e nella realtà mista (VR) di HoloLens, gli utenti vengono dotati di questo potere magico, che consente di superare i vincoli fisici del mondo reale, non solo per vivere esperienze divertenti con contenuti olografici, ma anche per migliorare l'efficacia e l'efficienza delle interazioni.</span><span class="sxs-lookup"><span data-stu-id="69379-109">In both HoloLens (AR) and Mixed Reality (MR), we equip users with this magical power, breaking the physical constraint of the real world, not only to have a fun experience with holographic content but also to make user interactions more effective and efficient.</span></span>

## <a name="device-support"></a><span data-ttu-id="69379-110">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="69379-110">Device support</span></span>

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><span data-ttu-id="69379-111"><strong>Modello di input</strong></span><span class="sxs-lookup"><span data-stu-id="69379-111"><strong>Input model</strong></span></span></td>
     <td><span data-ttu-id="69379-112"><a href="hololens-hardware-details.md"><strong>HoloLens (prima generazione)</strong></a></span><span class="sxs-lookup"><span data-stu-id="69379-112"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="69379-113"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="69379-113"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
     <td><span data-ttu-id="69379-114"><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="69379-114"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="69379-115">Puntamento e commit con le mani</span><span class="sxs-lookup"><span data-stu-id="69379-115">Point and commit with hands</span></span></td>
     <td><span data-ttu-id="69379-116">❌ Non supportato</span><span class="sxs-lookup"><span data-stu-id="69379-116">❌ Not supported</span></span></td>
     <td><span data-ttu-id="69379-117">✔️ Consigliata</span><span class="sxs-lookup"><span data-stu-id="69379-117">✔️ Recommended</span></span></td>
     <td><span data-ttu-id="69379-118">✔️ Consigliata</span><span class="sxs-lookup"><span data-stu-id="69379-118">✔️ Recommended</span></span></td>
</tr>
</table>


<span data-ttu-id="69379-119">_"Puntamento e commit con le mani"_ è una delle nuove funzionalità che si avvale dell'innovativo e articolato sistema di tracciamento delle mani.</span><span class="sxs-lookup"><span data-stu-id="69379-119">_"Point and commit with hands"_ is one of the new features that utilizes the new articulated hand-tracking system.</span></span> <span data-ttu-id="69379-120">Questo modello di input è anche il modello di input usato principalmente nei visori VR immersive mediante l'uso di controller del movimento.</span><span class="sxs-lookup"><span data-stu-id="69379-120">This input model is also the primary input model on immersive headsets through the use of motion controllers.</span></span>

<br>

---

## <a name="hand-rays"></a><span data-ttu-id="69379-121">Raggi mano</span><span class="sxs-lookup"><span data-stu-id="69379-121">Hand rays</span></span>

<span data-ttu-id="69379-122">In HoloLens 2 abbiamo creato un raggio della mano che viene lanciato dal centro del palmo della mano dell'utente.</span><span class="sxs-lookup"><span data-stu-id="69379-122">On HoloLens 2, we created a hand ray that shoots out from the center of the user's palm.</span></span> <span data-ttu-id="69379-123">Questo raggio viene considerato come un'estensione della mano.</span><span class="sxs-lookup"><span data-stu-id="69379-123">This ray is treated as an extension of the hand.</span></span> <span data-ttu-id="69379-124">All'estremità del raggio viene visualizzato un cursore ad anello che indica il punto in cui il raggio interseca un oggetto di destinazione.</span><span class="sxs-lookup"><span data-stu-id="69379-124">A donut-shaped cursor is attached to the end of the ray to indicate the location where the ray intersects with a target object.</span></span> <span data-ttu-id="69379-125">L'oggetto su cui si posa il cursore può quindi ricevere i comandi gestuali dalla mano.</span><span class="sxs-lookup"><span data-stu-id="69379-125">The object that the cursor lands on can then receive gestural commands from the hand.</span></span>

<span data-ttu-id="69379-126">Tale comando gestuale di base viene attivato usando il pollice e il dito indice per eseguire l'azione di simulazione del tocco.</span><span class="sxs-lookup"><span data-stu-id="69379-126">This basic gestural command is triggered by using the thumb and index finger to perform the air-tap action.</span></span> <span data-ttu-id="69379-127">Usando il raggio della mano per il puntamento e la simulazione del tocco per il commit, gli utenti possono attivare un pulsante o un collegamento ipertestuale.</span><span class="sxs-lookup"><span data-stu-id="69379-127">By using the hand ray to point and air tap to commit, users can activate a button or a hyperlink.</span></span> <span data-ttu-id="69379-128">Con movimenti più compositi, gli utenti possono navigare all'interno del contenuto Web e manipolare a distanza gli oggetti 3D.</span><span class="sxs-lookup"><span data-stu-id="69379-128">With more composite gestures, users are capable of navigating web content and manipulating 3D objects from a distance.</span></span> <span data-ttu-id="69379-129">La progettazione visiva del raggio mano dovrebbe anche reagire a questi stati di puntamento e commit come descritto e mostrato di seguito:</span><span class="sxs-lookup"><span data-stu-id="69379-129">The visual design of the hand ray should also react to these point and commit states, as described and shown below:</span></span> 

:::row:::
    :::column:::
        <span data-ttu-id="69379-130">![Puntamento con raggi della mano](images/hand-rays-pointing.jpg)</span><span class="sxs-lookup"><span data-stu-id="69379-130">![hand rays pointing](images/hand-rays-pointing.jpg)</span></span><br>
        <span data-ttu-id="69379-131">**Stato di puntamento**</span><span class="sxs-lookup"><span data-stu-id="69379-131">**Pointing state**</span></span><br>
        <span data-ttu-id="69379-132">Nello stato di *puntamento* il raggio è una linea tratteggiata e il cursore ha una forma ad anello.</span><span class="sxs-lookup"><span data-stu-id="69379-132">In the *pointing* state, the ray is a dash line and the cursor is a donut shape.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="69379-133">![Commit con raggi della mano](images/hand-rays-commit.jpg)</span><span class="sxs-lookup"><span data-stu-id="69379-133">![hand rays commit](images/hand-rays-commit.jpg)</span></span><br>
        <span data-ttu-id="69379-134">**Stato di commit**</span><span class="sxs-lookup"><span data-stu-id="69379-134">**Commit state**</span></span><br>
        <span data-ttu-id="69379-135">Nello stato di *commit* il raggio diventa una linea continua e il cursore si rimpicciolisce diventando un punto.</span><span class="sxs-lookup"><span data-stu-id="69379-135">In the *commit* state, the ray turns into a solid line and the cursor shrinks to a dot.</span></span>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="transition-between-near-and-far"></a><span data-ttu-id="69379-136">Transizione dall'interazione da vicino all'interazione da lontano</span><span class="sxs-lookup"><span data-stu-id="69379-136">Transition between near and far</span></span>

<span data-ttu-id="69379-137">Invece di usare movimenti specifici, come il "puntamento con il dito indice" per indirizzare il raggio, abbiamo progettato il raggio proveniente dal centro del palmo, in modo da lasciare le cinque dita libere per eseguire movimenti più finalizzati alla manipolazione, ad esempio l'avvicinamento delle dita e la cattura.</span><span class="sxs-lookup"><span data-stu-id="69379-137">Instead of using specific gestures, such as "pointing with index finger", to direct the ray, we designed the ray coming out from the center of the palm, releasing and reserving the five fingers for more manipulative gestures, such as pinch and grab.</span></span> <span data-ttu-id="69379-138">Grazie a tale progettazione, viene creato un unico modello mentale che usa esattamente la stessa serie di movimenti della mano per l'interazione da vicino e da lontano.</span><span class="sxs-lookup"><span data-stu-id="69379-138">With this design, we create only one mental model - the same set of hand gestures are used for both near and far interaction.</span></span> <span data-ttu-id="69379-139">Puoi usare lo stesso movimento di cattura per manipolare oggetti a distanze diverse.</span><span class="sxs-lookup"><span data-stu-id="69379-139">You can use the same grab gesture to manipulate objects at different distances.</span></span> <span data-ttu-id="69379-140">I raggi vengono richiamati automaticamente in base alla prossimità, come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="69379-140">The invocation of the rays is automatic and proximity based as follows:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="69379-141">![Manipolazione da vicino](images/transition-near-manipulation.jpg)</span><span class="sxs-lookup"><span data-stu-id="69379-141">![Near manipulation](images/transition-near-manipulation.jpg)</span></span><br>
        <span data-ttu-id="69379-142">**Manipolazione da vicino**</span><span class="sxs-lookup"><span data-stu-id="69379-142">**Near manipulation**</span></span><br>
        <span data-ttu-id="69379-143">Se un oggetto è a portata di braccio (a una distanza di circa 50 cm), i raggi vengono disattivati automaticamente, incoraggiando l'uso dell'interazione da vicino.</span><span class="sxs-lookup"><span data-stu-id="69379-143">When an object is within arm's length (roughly 50 cm), the rays are turned off automatically, encouraging near interaction.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="69379-144">![Manipolazione da lontano](images/transition-far-manipulation.jpg)</span><span class="sxs-lookup"><span data-stu-id="69379-144">![Far manipulation](images/transition-far-manipulation.jpg)</span></span><br>
        <span data-ttu-id="69379-145">**Manipolazione da lontano**</span><span class="sxs-lookup"><span data-stu-id="69379-145">**Far manipulation**</span></span><br>
        <span data-ttu-id="69379-146">Se l'oggetto si trova a una distanza superiore a 50 cm, i raggi vengono attivati.</span><span class="sxs-lookup"><span data-stu-id="69379-146">When the object is farther than 50 cm, the rays are turned on.</span></span> <span data-ttu-id="69379-147">La transizione deve avvenire fluidamente e senza problemi.</span><span class="sxs-lookup"><span data-stu-id="69379-147">The transition should be smooth and seamless.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a><span data-ttu-id="69379-148">Interazione con uno slate 2D</span><span class="sxs-lookup"><span data-stu-id="69379-148">2D slate interaction</span></span>

<span data-ttu-id="69379-149">Uno slate 2D è un contenitore olografico che ospita contenuti di app 2D, ad esempio un Web browser.</span><span class="sxs-lookup"><span data-stu-id="69379-149">A 2D slate is a holographic container hosting 2D app contents, such as a web browser.</span></span> <span data-ttu-id="69379-150">Il concetto di progettazione per l'interazione da lontano con uno slate 2D prevede l'uso dei raggi mano per puntare una destinazione e della simulazione del tocco per effettuare la selezione.</span><span class="sxs-lookup"><span data-stu-id="69379-150">The design concept for far interacting with a 2D slate is to use hand rays to target and air tap to select.</span></span> <span data-ttu-id="69379-151">Dopo aver individuato la destinazione con un raggio mano, gli utenti possono simulare il tocco per attivare un collegamento ipertestuale o un pulsante.</span><span class="sxs-lookup"><span data-stu-id="69379-151">After targeting with a hand ray, users can air tap to trigger a hyperlink or a button.</span></span> <span data-ttu-id="69379-152">Possono usare una mano per "simulare il tocco e trascinare" in modo da scorrere verso l'alto e verso il basso il contenuto dello slate.</span><span class="sxs-lookup"><span data-stu-id="69379-152">They can use one hand to "air tap and drag" to scroll slate content up and down.</span></span> <span data-ttu-id="69379-153">Il movimento relativo associato all'uso di due mani per simulare il tocco e trascinare può causare lo zoom avanti e lo zoom indietro sul contenuto dello slate.</span><span class="sxs-lookup"><span data-stu-id="69379-153">The relative motion of using two hands to air tap and drag can zoom in and out the slate content.</span></span>

<span data-ttu-id="69379-154">Puntando il raggio mano sugli angoli e sui bordi, è possibile vedere l'invito di manipolazione più vicino.</span><span class="sxs-lookup"><span data-stu-id="69379-154">Targeting the hand ray at the corners and edges reveals the closest manipulation affordance.</span></span> <span data-ttu-id="69379-155">"Afferrando e trascinando" gli inviti di manipolazione, gli utenti possono eseguire un ridimensionamento uniforme tramite gli inviti degli angoli, nonché adattare automaticamente il contenuto dello slate tramite gli inviti dei bordi.</span><span class="sxs-lookup"><span data-stu-id="69379-155">By "grab and drag" manipulation affordances, users can perform uniform scaling through the corner affordances, and can reflow the slate via the edge affordances.</span></span> <span data-ttu-id="69379-156">Afferrando e trascinando la barra dell'ologramma nella parte superiore dello slate 2D, gli utenti possono spostare l'intero slate.</span><span class="sxs-lookup"><span data-stu-id="69379-156">Grabbing and dragging the holobar at the top of the 2D slate lets users move the entire slate.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="69379-157">![Interazione con uno slate 2D - clic](images/2d-slate-interaction-click.jpg)</span><span class="sxs-lookup"><span data-stu-id="69379-157">![2d slate interaction click](images/2d-slate-interaction-click.jpg)</span></span><br>
       <span data-ttu-id="69379-158">**Clic**</span><span class="sxs-lookup"><span data-stu-id="69379-158">**Click**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="69379-159">![Interazione con uno slate 2D - scorrimento](images/2d-slate-interaction-scroll.jpg)</span><span class="sxs-lookup"><span data-stu-id="69379-159">![2d slate interaction scroll](images/2d-slate-interaction-scroll.jpg)</span></span><br>
        <span data-ttu-id="69379-160">**Scorrimento**</span><span class="sxs-lookup"><span data-stu-id="69379-160">**Scroll**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="69379-161">![Interazione con uno slate 2D - zoom](images/2d-slate-interaction-zoom.jpg)</span><span class="sxs-lookup"><span data-stu-id="69379-161">![2d slate interaction zoom](images/2d-slate-interaction-zoom.jpg)</span></span><br>
       <span data-ttu-id="69379-162">**Zoom**</span><span class="sxs-lookup"><span data-stu-id="69379-162">**Zoom**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

<span data-ttu-id="69379-163">**Per la manipolazione dello slate 2D**</span><span class="sxs-lookup"><span data-stu-id="69379-163">**For manipulating the 2D slate**</span></span><br>

* <span data-ttu-id="69379-164">Gli utenti puntano il raggio mano sugli angoli o sui bordi per vedere l'invito di manipolazione più vicino.</span><span class="sxs-lookup"><span data-stu-id="69379-164">Users point the hand ray at the corners or edges to reveal the closest manipulation affordance.</span></span> 
* <span data-ttu-id="69379-165">Applicando un movimento di manipolazione all'invito, gli utenti possono eseguire un ridimensionamento uniforme tramite l'invito degli angoli, nonché adattare automaticamente il contenuto dello slate mediante l'invito dei bordi.</span><span class="sxs-lookup"><span data-stu-id="69379-165">By applying a manipulation gesture on the affordance, users can perform uniform scaling through the corner affordance, and can reflow the slate via the edge affordance.</span></span> 
* <span data-ttu-id="69379-166">Applicando un movimento di manipolazione alla barra dell'ologramma nella parte superiore dello slate 2D, gli utenti possono spostare l'intero slate.</span><span class="sxs-lookup"><span data-stu-id="69379-166">By applying a manipulation gesture on the holobar at the top of the 2D slate, users can move the entire slate.</span></span><br>


<br>

---

## <a name="3d-object-manipulation"></a><span data-ttu-id="69379-167">Manipolazione di oggetti 3D</span><span class="sxs-lookup"><span data-stu-id="69379-167">3D object manipulation</span></span>

<span data-ttu-id="69379-168">Nella manipolazione diretta gli utenti possono manipolare gli oggetti 3D in due modi, ovvero con manipolazione basata sugli inviti e non basata sugli inviti.</span><span class="sxs-lookup"><span data-stu-id="69379-168">In direct manipulation, there are two ways for users to manipulate 3D objects: affordance-based manipulation and non-affordance based manipulation.</span></span> <span data-ttu-id="69379-169">Nel modello puntamento e commit gli utenti possono eseguire esattamente le stesse attività mediante i raggi mano.</span><span class="sxs-lookup"><span data-stu-id="69379-169">In the point and commit model, users are capable of achieving exactly the same tasks through the hand rays.</span></span> <span data-ttu-id="69379-170">Non sono necessarie altre conoscenze.</span><span class="sxs-lookup"><span data-stu-id="69379-170">No additional learning is needed.</span></span><br>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="69379-171">Manipolazione basata sugli inviti</span><span class="sxs-lookup"><span data-stu-id="69379-171">Affordance-based manipulation</span></span>
<span data-ttu-id="69379-172">Gli utenti usano i raggi mano per puntare e vedere il cubo di delimitazione e gli inviti di manipolazione.</span><span class="sxs-lookup"><span data-stu-id="69379-172">Users use hand rays to point and reveal the bounding box and manipulation affordances.</span></span> <span data-ttu-id="69379-173">Gli utenti possono applicare il movimento di manipolazione al cubo di delimitazione per spostare l'intero oggetto, agli inviti dei bordi per ruotare e agli inviti degli angoli per ridimensionare in modo uniforme.</span><span class="sxs-lookup"><span data-stu-id="69379-173">Users can apply the manipulation gesture on the bounding box to move the whole object, on the edge affordances to rotate, and on the corner affordances to scale uniformly.</span></span> <br>

:::row:::
    :::column:::
       <span data-ttu-id="69379-174">![Manipolazione di un oggetto 3D - spostamento da lontano](images/3d-object-manipulation-far-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="69379-174">![3d object manipulation far move](images/3d-object-manipulation-far-move.jpg)</span></span><br>
       <span data-ttu-id="69379-175">**Sposta**</span><span class="sxs-lookup"><span data-stu-id="69379-175">**Move**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="69379-176">![Manipolazione di un oggetto 3D - rotazione da lontano](images/3d-object-manipulation-far-rotate.jpg)</span><span class="sxs-lookup"><span data-stu-id="69379-176">![3d object manipulation far rotate](images/3d-object-manipulation-far-rotate.jpg)</span></span><br>
        <span data-ttu-id="69379-177">**Ruota**</span><span class="sxs-lookup"><span data-stu-id="69379-177">**Rotate**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="69379-178">![Manipolazione di un oggetto 3D - ridimensionamento da lontano](images/3d-object-manipulation-far-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="69379-178">![3d object manipulation far scale](images/3d-object-manipulation-far-scale.jpg)</span></span><br>
       <span data-ttu-id="69379-179">**Ridimensiona**</span><span class="sxs-lookup"><span data-stu-id="69379-179">**Scale**</span></span><br>
    :::column-end:::
:::row-end:::


### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="69379-180">Manipolazione non basata sugli inviti</span><span class="sxs-lookup"><span data-stu-id="69379-180">Non-affordance based manipulation</span></span>
<span data-ttu-id="69379-181">Gli utenti puntano con i raggi mano per vedere il cubo di delimitazione e quindi vi applicano direttamente i movimenti di manipolazione.</span><span class="sxs-lookup"><span data-stu-id="69379-181">Users point with hand rays to reveal the bounding box then directly apply manipulation gestures on it.</span></span> <span data-ttu-id="69379-182">Con una mano, la traslazione e la rotazione dell'oggetto sono associati al movimento e all'orientamento della mano.</span><span class="sxs-lookup"><span data-stu-id="69379-182">With one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="69379-183">Con due mani, gli utenti possono spostarlo, ridimensionarlo e ruotarlo in base ai movimenti relativi delle mani.</span><span class="sxs-lookup"><span data-stu-id="69379-183">With two hands, users can translate, scale, and rotate it according to relative motions of two hands.</span></span><br>

<br>

---

## <a name="instinctual-gestures"></a><span data-ttu-id="69379-184">Movimenti istintivi</span><span class="sxs-lookup"><span data-stu-id="69379-184">Instinctual gestures</span></span>
<span data-ttu-id="69379-185">Il concetto di movimenti istintivi per puntamento e commit è analogo a quello per la [manipolazione diretta con le mani](direct-manipulation.md).</span><span class="sxs-lookup"><span data-stu-id="69379-185">The concept of instinctual gestures for point and commit is similar to that for [direct manipulation with hands](direct-manipulation.md).</span></span> <span data-ttu-id="69379-186">I movimenti che gli utenti eseguono su un oggetto 3D vengono guidati dalla progettazione degli inviti dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="69379-186">The gestures users perform on a 3D object are guided by the design of UI affordances.</span></span> <span data-ttu-id="69379-187">Ad esempio, in presenza di un piccolo punto di controllo gli utenti sono portati a usare il pollice e l'indice (ovvero ad avvicinare le dita), mentre davanti a un oggetto più grande possono decidere di afferrarlo usando tutte e cinque le dita.</span><span class="sxs-lookup"><span data-stu-id="69379-187">For example, a small control point might motivate users to pinch with their thumb and index finger, while a user might want to grab a larger object using all five fingers.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="69379-188">![Movimenti istintivi per un oggetto piccolo](images/instinctual-gestures-far-smallobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="69379-188">![instinctual gestures far small object](images/instinctual-gestures-far-smallobject.jpg)</span></span><br>
       <span data-ttu-id="69379-189">**Oggetto piccolo**</span><span class="sxs-lookup"><span data-stu-id="69379-189">**Small object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="69379-190">![Movimenti istintivi per un oggetto medio](images/instinctual-gestures-far-mediumobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="69379-190">![instinctual gestures far medium object](images/instinctual-gestures-far-mediumobject.jpg)</span></span><br>
        <span data-ttu-id="69379-191">**Oggetto medio**</span><span class="sxs-lookup"><span data-stu-id="69379-191">**Medium object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="69379-192">![Movimenti istintivi per un oggetto grande](images/instinctual-gestures-far-largeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="69379-192">![instinctual gestures far large object](images/instinctual-gestures-far-largeobject.jpg)</span></span><br>
       <span data-ttu-id="69379-193">**Oggetto grande**</span><span class="sxs-lookup"><span data-stu-id="69379-193">**Large object**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a><span data-ttu-id="69379-194">Progettazione simmetrica tra le due mani e controller 6DoF</span><span class="sxs-lookup"><span data-stu-id="69379-194">Symmetric design between hands and 6 DoF controller</span></span> 

<span data-ttu-id="69379-195">Il concetto alla base del puntamento e commit per un'interazione da lontano inizialmente era stato creato e definito per il Portale realtà mista, in cui un utente indossa un visore VR immersive e interagisce con gli oggetti 3D tramite controller del movimento.</span><span class="sxs-lookup"><span data-stu-id="69379-195">The concept of point and commit for far interaction was initially created and defined for the Mixed Reality Portal (MRP) where a user wears an immersive headset and interacts with 3D objects via motion controllers.</span></span> <span data-ttu-id="69379-196">Tali controller emettono raggi per il puntamento e la manipolazione degli oggetti lontani.</span><span class="sxs-lookup"><span data-stu-id="69379-196">The motion controllers shoot out rays for pointing and manipulating far objects.</span></span> <span data-ttu-id="69379-197">Sui controller sono presenti pulsanti che consentono di eseguire ulteriormente il commit di azioni diverse.</span><span class="sxs-lookup"><span data-stu-id="69379-197">There are buttons on the controllers for further committing different actions.</span></span> <span data-ttu-id="69379-198">Noi sfruttiamo il modello di interazione dei raggi e lo abbiamo associato a entrambe le mani.</span><span class="sxs-lookup"><span data-stu-id="69379-198">We leverage the interaction model of rays and attached them to both hands.</span></span> <span data-ttu-id="69379-199">Grazie a questa progettazione simmetrica, gli utenti abituati a operare con il Portale realtà mista non dovranno apprendere un altro modello di interazione per il puntamento e la manipolazione da lontano quando usano HoloLens 2 e viceversa.</span><span class="sxs-lookup"><span data-stu-id="69379-199">With this symmetric design, users who are familiar with MRP won't need to learn another interaction model for far pointing and manipulation when they use HoloLen 2, and vice versa.</span></span>    

:::row:::
    :::column:::
        <span data-ttu-id="69379-200">![Progettazione simmetrica per raggi con controller](images/symmetric-design-for-rays-controllers.jpg)</span><span class="sxs-lookup"><span data-stu-id="69379-200">![symmetric design for rays with controllers](images/symmetric-design-for-rays-controllers.jpg)</span></span><br>
        <span data-ttu-id="69379-201">**Raggi del controller**</span><span class="sxs-lookup"><span data-stu-id="69379-201">**Controller rays**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="69379-202">![Progettazione simmetrica per raggi con le mani](images/symmetric-design-for-rays-hands.jpg)</span><span class="sxs-lookup"><span data-stu-id="69379-202">![symmetric design for rays with hands](images/symmetric-design-for-rays-hands.jpg)</span></span><br>
        <span data-ttu-id="69379-203">**Raggi della mano**</span><span class="sxs-lookup"><span data-stu-id="69379-203">**Hand rays**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="69379-204">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="69379-204">See also</span></span>
* [<span data-ttu-id="69379-205">Manipolazione diretta con le mani</span><span class="sxs-lookup"><span data-stu-id="69379-205">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="69379-206">Sguardo fisso e commit</span><span class="sxs-lookup"><span data-stu-id="69379-206">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="69379-207">Mani - Manipolazione diretta</span><span class="sxs-lookup"><span data-stu-id="69379-207">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="69379-208">Mani - Movimenti</span><span class="sxs-lookup"><span data-stu-id="69379-208">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="69379-209">Interazioni istintive</span><span class="sxs-lookup"><span data-stu-id="69379-209">Instinctual interactions</span></span>](interaction-fundamentals.md)
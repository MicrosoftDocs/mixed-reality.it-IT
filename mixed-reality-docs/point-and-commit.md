---
title: Puntamento e commit con le mani
description: Panoramica del modello di input puntamento e commit
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: realtà mista, interazione, progettazione, HoloLens, mani, da lontano, puntamento e commit
ms.openlocfilehash: c7952338c6937e42889a08ee37f6ce8bc1bb9ad3
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334062"
---
# <a name="point-and-commit-with-hands"></a><span data-ttu-id="80e2f-104">Puntamento e commit con le mani</span><span class="sxs-lookup"><span data-stu-id="80e2f-104">Point and commit with hands</span></span>

![Cursori](images/UX/UX_Hero_HandRay.jpg)

<span data-ttu-id="80e2f-106">Puntamento e commit con le mani è un modello di input che consente agli utenti di puntare come destinazione, selezionare e manipolare contenuto 2D e oggetti 3D fuori portata.</span><span class="sxs-lookup"><span data-stu-id="80e2f-106">Point and commit with hands is an input model that enables users to target, select and manipulate 2D content and 3D objects that are out of reach.</span></span> <span data-ttu-id="80e2f-107">Questa tecnica di interazione "da lontano" è specifica della realtà mista e non corrisponde al modo in cui le persone interagiscono naturalmente con il mondo reale.</span><span class="sxs-lookup"><span data-stu-id="80e2f-107">This "far" interaction technique is unique to mixed reality, and is not a way humans naturally interact with the real world.</span></span> <span data-ttu-id="80e2f-108">Ad esempio, nel film di supereroi *X-Men* il personaggio [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) è in grado di manipolare a distanza un oggetto lontano con le sue mani.</span><span class="sxs-lookup"><span data-stu-id="80e2f-108">For example, in the super hero movie, *X-Men*, the character [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) is capable of reaching out and manipulating a far object in the distance with his hands.</span></span> <span data-ttu-id="80e2f-109">Questa non è un'azione che gli esseri umani possono compiere nella realtà.</span><span class="sxs-lookup"><span data-stu-id="80e2f-109">This is not something humans can do in reality.</span></span> <span data-ttu-id="80e2f-110">Nella realtà aumentata (AR) e nella realtà mista (VR) di HoloLens, gli utenti vengono dotati di questo potere magico, che consente di superare i vincoli fisici del mondo reale, non solo per vivere esperienze divertenti con contenuti olografici, ma anche per migliorare l'efficacia e l'efficienza delle interazioni.</span><span class="sxs-lookup"><span data-stu-id="80e2f-110">In both HoloLens (AR) and Mixed Reality (MR), we equip users with this magical power, breaking the physical constraint of the real world, not only to have a fun experience with holographic content but also to make user interactions more effective and efficient.</span></span>

## <a name="device-support"></a><span data-ttu-id="80e2f-111">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="80e2f-111">Device support</span></span>

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><span data-ttu-id="80e2f-112"><strong>Modello di input</strong></span><span class="sxs-lookup"><span data-stu-id="80e2f-112"><strong>Input model</strong></span></span></td>
     <td><span data-ttu-id="80e2f-113"><a href="hololens-hardware-details.md"><strong>HoloLens (prima generazione)</strong></a></span><span class="sxs-lookup"><span data-stu-id="80e2f-113"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="80e2f-114"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="80e2f-114"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
     <td><span data-ttu-id="80e2f-115"><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="80e2f-115"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="80e2f-116">Puntamento e commit con le mani</span><span class="sxs-lookup"><span data-stu-id="80e2f-116">Point and commit with hands</span></span></td>
     <td><span data-ttu-id="80e2f-117">❌ Non supportato</span><span class="sxs-lookup"><span data-stu-id="80e2f-117">❌ Not supported</span></span></td>
     <td><span data-ttu-id="80e2f-118">✔️ Consigliata</span><span class="sxs-lookup"><span data-stu-id="80e2f-118">✔️ Recommended</span></span></td>
     <td><span data-ttu-id="80e2f-119">✔️ Consigliata</span><span class="sxs-lookup"><span data-stu-id="80e2f-119">✔️ Recommended</span></span></td>
</tr>
</table>


<span data-ttu-id="80e2f-120">_"Puntamento e commit con le mani"_ è una delle nuove funzionalità che si avvale dell'innovativo e articolato sistema di tracciamento delle mani.</span><span class="sxs-lookup"><span data-stu-id="80e2f-120">_"Point and commit with hands"_ is one of the new features that utilizes the new articulated hand-tracking system.</span></span> <span data-ttu-id="80e2f-121">Questo modello di input è anche il modello di input usato principalmente nei visori VR immersive mediante l'uso di controller del movimento.</span><span class="sxs-lookup"><span data-stu-id="80e2f-121">This input model is also the primary input model on immersive headsets through the use of motion controllers.</span></span>

<br>

---

## <a name="hand-rays"></a><span data-ttu-id="80e2f-122">Raggi mano</span><span class="sxs-lookup"><span data-stu-id="80e2f-122">Hand rays</span></span>

<span data-ttu-id="80e2f-123">In HoloLens 2 abbiamo creato un raggio della mano che viene lanciato dal centro del palmo della mano dell'utente.</span><span class="sxs-lookup"><span data-stu-id="80e2f-123">On HoloLens 2, we created a hand ray that shoots out from the center of the user's palm.</span></span> <span data-ttu-id="80e2f-124">Questo raggio viene considerato come un'estensione della mano.</span><span class="sxs-lookup"><span data-stu-id="80e2f-124">This ray is treated as an extension of the hand.</span></span> <span data-ttu-id="80e2f-125">All'estremità del raggio viene visualizzato un cursore ad anello che indica il punto in cui il raggio interseca un oggetto di destinazione.</span><span class="sxs-lookup"><span data-stu-id="80e2f-125">A donut-shaped cursor is attached to the end of the ray to indicate the location where the ray intersects with a target object.</span></span> <span data-ttu-id="80e2f-126">L'oggetto su cui si posa il cursore può quindi ricevere i comandi gestuali dalla mano.</span><span class="sxs-lookup"><span data-stu-id="80e2f-126">The object that the cursor lands on can then receive gestural commands from the hand.</span></span>

<span data-ttu-id="80e2f-127">Tale comando gestuale di base viene attivato usando il pollice e il dito indice per eseguire l'azione di simulazione del tocco.</span><span class="sxs-lookup"><span data-stu-id="80e2f-127">This basic gestural command is triggered by using the thumb and index finger to perform the air-tap action.</span></span> <span data-ttu-id="80e2f-128">Usando il raggio della mano per il puntamento e la simulazione del tocco per il commit, gli utenti possono attivare un pulsante o un collegamento ipertestuale.</span><span class="sxs-lookup"><span data-stu-id="80e2f-128">By using the hand ray to point and air tap to commit, users can activate a button or a hyperlink.</span></span> <span data-ttu-id="80e2f-129">Con movimenti più compositi, gli utenti possono navigare all'interno del contenuto Web e manipolare a distanza gli oggetti 3D.</span><span class="sxs-lookup"><span data-stu-id="80e2f-129">With more composite gestures, users are capable of navigating web content and manipulating 3D objects from a distance.</span></span> <span data-ttu-id="80e2f-130">La progettazione visiva del raggio mano dovrebbe anche reagire a questi stati di puntamento e commit come descritto e mostrato di seguito:</span><span class="sxs-lookup"><span data-stu-id="80e2f-130">The visual design of the hand ray should also react to these point and commit states, as described and shown below:</span></span> 

:::row:::
    :::column:::
        <span data-ttu-id="80e2f-131">![Puntamento con raggi della mano](images/hand-rays-pointing.jpg)</span><span class="sxs-lookup"><span data-stu-id="80e2f-131">![hand rays pointing](images/hand-rays-pointing.jpg)</span></span><br>
        <span data-ttu-id="80e2f-132">**Stato di puntamento**</span><span class="sxs-lookup"><span data-stu-id="80e2f-132">**Pointing state**</span></span><br>
        <span data-ttu-id="80e2f-133">Nello stato di *puntamento* il raggio è una linea tratteggiata e il cursore ha una forma ad anello.</span><span class="sxs-lookup"><span data-stu-id="80e2f-133">In the *pointing* state, the ray is a dash line and the cursor is a donut shape.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="80e2f-134">![Commit con raggi della mano](images/hand-rays-commit.jpg)</span><span class="sxs-lookup"><span data-stu-id="80e2f-134">![hand rays commit](images/hand-rays-commit.jpg)</span></span><br>
        <span data-ttu-id="80e2f-135">**Stato di commit**</span><span class="sxs-lookup"><span data-stu-id="80e2f-135">**Commit state**</span></span><br>
        <span data-ttu-id="80e2f-136">Nello stato di *commit* il raggio diventa una linea continua e il cursore si rimpicciolisce diventando un punto.</span><span class="sxs-lookup"><span data-stu-id="80e2f-136">In the *commit* state, the ray turns into a solid line and the cursor shrinks to a dot.</span></span>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="transition-between-near-and-far"></a><span data-ttu-id="80e2f-137">Transizione dall'interazione da vicino all'interazione da lontano</span><span class="sxs-lookup"><span data-stu-id="80e2f-137">Transition between near and far</span></span>

<span data-ttu-id="80e2f-138">Invece di usare movimenti specifici, come il "puntamento con il dito indice" per indirizzare il raggio, abbiamo progettato il raggio in modo che esca dal centro del palmo, lasciando le cinque dita libere di eseguire movimenti più finalizzati alla manipolazione, ad esempio l'avvicinamento delle dita e la cattura.</span><span class="sxs-lookup"><span data-stu-id="80e2f-138">Instead of using specific gestures, such as "pointing with index finger" to direct the ray, we designed the ray coming out from the center of the palm, releasing and reserving the five fingers for more manipulative gestures, such as pinch and grab.</span></span> <span data-ttu-id="80e2f-139">Grazie a tale progettazione, viene creato un unico modello mentale che usa esattamente la stessa serie di movimenti della mano per l'interazione da vicino e da lontano.</span><span class="sxs-lookup"><span data-stu-id="80e2f-139">With this design, we create only one mental model - the same set of hand gestures are used for both near and far interaction.</span></span> <span data-ttu-id="80e2f-140">Puoi usare lo stesso movimento di cattura per manipolare oggetti a distanze diverse.</span><span class="sxs-lookup"><span data-stu-id="80e2f-140">You can use the same grab gesture to manipulate objects at different distances.</span></span> <span data-ttu-id="80e2f-141">I raggi vengono richiamati automaticamente in base alla prossimità, come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="80e2f-141">The invocation of the rays is automatic and proximity-based as follows:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="80e2f-142">![Manipolazione da vicino](images/transition-near-manipulation.jpg)</span><span class="sxs-lookup"><span data-stu-id="80e2f-142">![Near manipulation](images/transition-near-manipulation.jpg)</span></span><br>
        <span data-ttu-id="80e2f-143">**Manipolazione da vicino**</span><span class="sxs-lookup"><span data-stu-id="80e2f-143">**Near manipulation**</span></span><br>
        <span data-ttu-id="80e2f-144">Se un oggetto è a portata di braccio (a una distanza di circa 50 cm), i raggi vengono disattivati automaticamente, incoraggiando l'uso dell'interazione da vicino.</span><span class="sxs-lookup"><span data-stu-id="80e2f-144">When an object is within arm's length (roughly 50 cm), the rays are turned off automatically, encouraging near interaction.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="80e2f-145">![Manipolazione da lontano](images/transition-far-manipulation.jpg)</span><span class="sxs-lookup"><span data-stu-id="80e2f-145">![Far manipulation](images/transition-far-manipulation.jpg)</span></span><br>
        <span data-ttu-id="80e2f-146">**Manipolazione da lontano**</span><span class="sxs-lookup"><span data-stu-id="80e2f-146">**Far manipulation**</span></span><br>
        <span data-ttu-id="80e2f-147">Se l'oggetto si trova a una distanza superiore a 50 cm, i raggi vengono attivati.</span><span class="sxs-lookup"><span data-stu-id="80e2f-147">When the object is farther than 50 cm, the rays are turned on.</span></span> <span data-ttu-id="80e2f-148">La transizione deve avvenire fluidamente e senza problemi.</span><span class="sxs-lookup"><span data-stu-id="80e2f-148">The transition should be smooth and seamless.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a><span data-ttu-id="80e2f-149">Interazione con uno slate 2D</span><span class="sxs-lookup"><span data-stu-id="80e2f-149">2D slate interaction</span></span>

<span data-ttu-id="80e2f-150">Uno slate 2D è un contenitore olografico che ospita contenuti di app 2D, ad esempio un Web browser.</span><span class="sxs-lookup"><span data-stu-id="80e2f-150">A 2D slate is a holographic container hosting 2D app contents, such as a web browser.</span></span> <span data-ttu-id="80e2f-151">Il concetto di progettazione per l'interazione da lontano con uno slate 2D prevede l'uso dei raggi mano per puntare una destinazione e della simulazione del tocco per effettuare la selezione.</span><span class="sxs-lookup"><span data-stu-id="80e2f-151">The design concept for far interacting with a 2D slate is to use hand rays to target and air tap to select.</span></span> <span data-ttu-id="80e2f-152">Dopo aver individuato la destinazione con un raggio mano, gli utenti possono simulare il tocco per attivare un collegamento ipertestuale o un pulsante.</span><span class="sxs-lookup"><span data-stu-id="80e2f-152">After targeting with a hand ray, users can air tap to trigger a hyperlink or a button.</span></span> <span data-ttu-id="80e2f-153">Possono usare una mano per "simulare il tocco e trascinare" in modo da scorrere verso l'alto e verso il basso il contenuto dello slate.</span><span class="sxs-lookup"><span data-stu-id="80e2f-153">They can use one hand to "air tap and drag" to scroll slate content up and down.</span></span> <span data-ttu-id="80e2f-154">Il movimento relativo associato all'uso di due mani per simulare il tocco e trascinare può causare lo zoom avanti e lo zoom indietro sul contenuto dello slate.</span><span class="sxs-lookup"><span data-stu-id="80e2f-154">The relative motion of using two hands to air tap and drag can zoom in and out the slate content.</span></span>

<span data-ttu-id="80e2f-155">Puntando il raggio mano sugli angoli e sui bordi, è possibile vedere l'invito di manipolazione più vicino.</span><span class="sxs-lookup"><span data-stu-id="80e2f-155">Targeting the hand ray at the corners and edges reveals the closest manipulation affordance.</span></span> <span data-ttu-id="80e2f-156">"Afferrando e trascinando" gli inviti di manipolazione, gli utenti possono eseguire un ridimensionamento uniforme tramite gli inviti degli angoli, nonché adattare automaticamente il contenuto dello slate tramite gli inviti dei bordi.</span><span class="sxs-lookup"><span data-stu-id="80e2f-156">By "grab and drag" manipulation affordances, users can perform uniform scaling through the corner affordances, and can reflow the slate via the edge affordances.</span></span> <span data-ttu-id="80e2f-157">Afferrando e trascinando la barra dell'ologramma nella parte superiore dello slate 2D, gli utenti possono spostare l'intero slate.</span><span class="sxs-lookup"><span data-stu-id="80e2f-157">Grabbing and dragging the holobar at the top of the 2D slate lets users move the entire slate.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="80e2f-158">![Interazione con uno slate 2D - clic](images/2d-slate-interaction-click.jpg)</span><span class="sxs-lookup"><span data-stu-id="80e2f-158">![2d slate interaction click](images/2d-slate-interaction-click.jpg)</span></span><br>
       <span data-ttu-id="80e2f-159">**Clic**</span><span class="sxs-lookup"><span data-stu-id="80e2f-159">**Click**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="80e2f-160">![Interazione con uno slate 2D - scorrimento](images/2d-slate-interaction-scroll.jpg)</span><span class="sxs-lookup"><span data-stu-id="80e2f-160">![2d slate interaction scroll](images/2d-slate-interaction-scroll.jpg)</span></span><br>
        <span data-ttu-id="80e2f-161">**Scorrimento**</span><span class="sxs-lookup"><span data-stu-id="80e2f-161">**Scroll**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="80e2f-162">![Interazione con uno slate 2D - zoom](images/2d-slate-interaction-zoom.jpg)</span><span class="sxs-lookup"><span data-stu-id="80e2f-162">![2d slate interaction zoom](images/2d-slate-interaction-zoom.jpg)</span></span><br>
       <span data-ttu-id="80e2f-163">**Zoom**</span><span class="sxs-lookup"><span data-stu-id="80e2f-163">**Zoom**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

<span data-ttu-id="80e2f-164">**Per la manipolazione dello slate 2D**</span><span class="sxs-lookup"><span data-stu-id="80e2f-164">**For manipulating the 2D slate**</span></span><br>

* <span data-ttu-id="80e2f-165">Gli utenti puntano il raggio mano sugli angoli o sui bordi per vedere l'invito di manipolazione più vicino.</span><span class="sxs-lookup"><span data-stu-id="80e2f-165">Users point the hand ray at the corners or edges to reveal the closest manipulation affordance.</span></span> 
* <span data-ttu-id="80e2f-166">Applicando un movimento di manipolazione all'invito, gli utenti possono eseguire un ridimensionamento uniforme tramite l'invito degli angoli, nonché adattare automaticamente il contenuto dello slate mediante l'invito dei bordi.</span><span class="sxs-lookup"><span data-stu-id="80e2f-166">By applying a manipulation gesture on the affordance, users can perform uniform scaling through the corner affordance, and can reflow the slate via the edge affordance.</span></span> 
* <span data-ttu-id="80e2f-167">Applicando un movimento di manipolazione alla barra dell'ologramma nella parte superiore dello slate 2D, gli utenti possono spostare l'intero slate.</span><span class="sxs-lookup"><span data-stu-id="80e2f-167">By applying a manipulation gesture on the holobar at the top of the 2D slate, users can move the entire slate.</span></span><br>


<br>

---

## <a name="3d-object-manipulation"></a><span data-ttu-id="80e2f-168">Manipolazione di oggetti 3D</span><span class="sxs-lookup"><span data-stu-id="80e2f-168">3D object manipulation</span></span>

<span data-ttu-id="80e2f-169">Nella manipolazione diretta gli utenti possono manipolare gli oggetti 3D in due modi, ovvero con manipolazione basata sugli inviti e non basata sugli inviti.</span><span class="sxs-lookup"><span data-stu-id="80e2f-169">In direct manipulation, there are two ways for users to manipulate 3D objects: affordance-based manipulation and non-affordance based manipulation.</span></span> <span data-ttu-id="80e2f-170">Nel modello puntamento e commit gli utenti possono eseguire esattamente le stesse attività mediante i raggi mano.</span><span class="sxs-lookup"><span data-stu-id="80e2f-170">In the point and commit model, users are capable of achieving exactly the same tasks through the hand rays.</span></span> <span data-ttu-id="80e2f-171">Non sono necessarie altre conoscenze.</span><span class="sxs-lookup"><span data-stu-id="80e2f-171">No additional learning is needed.</span></span><br>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="80e2f-172">Manipolazione basata sugli inviti</span><span class="sxs-lookup"><span data-stu-id="80e2f-172">Affordance-based manipulation</span></span>
<span data-ttu-id="80e2f-173">Gli utenti usano i raggi mano per puntare e vedere il cubo di delimitazione e gli inviti di manipolazione.</span><span class="sxs-lookup"><span data-stu-id="80e2f-173">Users use hand rays to point and reveal the bounding box and manipulation affordances.</span></span> <span data-ttu-id="80e2f-174">Gli utenti possono applicare il movimento di manipolazione al cubo di delimitazione per spostare l'intero oggetto, agli inviti dei bordi per ruotare e agli inviti degli angoli per ridimensionare in modo uniforme.</span><span class="sxs-lookup"><span data-stu-id="80e2f-174">Users can apply the manipulation gesture on the bounding box to move the whole object, on the edge affordances to rotate, and on the corner affordances to scale uniformly.</span></span> <br>

:::row:::
    :::column:::
       <span data-ttu-id="80e2f-175">![Manipolazione di un oggetto 3D - spostamento da lontano](images/3d-object-manipulation-far-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="80e2f-175">![3d object manipulation far move](images/3d-object-manipulation-far-move.jpg)</span></span><br>
       <span data-ttu-id="80e2f-176">**Spostamento**</span><span class="sxs-lookup"><span data-stu-id="80e2f-176">**Move**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="80e2f-177">![Manipolazione di un oggetto 3D - rotazione da lontano](images/3d-object-manipulation-far-rotate.jpg)</span><span class="sxs-lookup"><span data-stu-id="80e2f-177">![3d object manipulation far rotate](images/3d-object-manipulation-far-rotate.jpg)</span></span><br>
        <span data-ttu-id="80e2f-178">**Rotazione**</span><span class="sxs-lookup"><span data-stu-id="80e2f-178">**Rotate**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="80e2f-179">![Manipolazione di un oggetto 3D - ridimensionamento da lontano](images/3d-object-manipulation-far-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="80e2f-179">![3d object manipulation far scale](images/3d-object-manipulation-far-scale.jpg)</span></span><br>
       <span data-ttu-id="80e2f-180">**Ridimensionamento**</span><span class="sxs-lookup"><span data-stu-id="80e2f-180">**Scale**</span></span><br>
    :::column-end:::
:::row-end:::


### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="80e2f-181">Manipolazione non basata sugli inviti</span><span class="sxs-lookup"><span data-stu-id="80e2f-181">Non-affordance based manipulation</span></span>
<span data-ttu-id="80e2f-182">Gli utenti puntano con i raggi mano per vedere il cubo di delimitazione e quindi vi applicano direttamente i movimenti di manipolazione.</span><span class="sxs-lookup"><span data-stu-id="80e2f-182">Users point with hand rays to reveal the bounding box then directly apply manipulation gestures on it.</span></span> <span data-ttu-id="80e2f-183">Con una mano, la traslazione e la rotazione dell'oggetto sono associati al movimento e all'orientamento della mano.</span><span class="sxs-lookup"><span data-stu-id="80e2f-183">With one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="80e2f-184">Con due mani, gli utenti possono spostarlo, ridimensionarlo e ruotarlo in base ai movimenti relativi delle mani.</span><span class="sxs-lookup"><span data-stu-id="80e2f-184">With two hands, users can translate, scale, and rotate it according to relative motions of two hands.</span></span><br>

<br>

---

## <a name="instinctual-gestures"></a><span data-ttu-id="80e2f-185">Movimenti istintivi</span><span class="sxs-lookup"><span data-stu-id="80e2f-185">Instinctual gestures</span></span>
<span data-ttu-id="80e2f-186">Il concetto di movimenti istintivi per puntamento e commit è analogo a quello per la [manipolazione diretta con le mani](direct-manipulation.md).</span><span class="sxs-lookup"><span data-stu-id="80e2f-186">The concept of instinctual gestures for point and commit is similar to that for [direct manipulation with hands](direct-manipulation.md).</span></span> <span data-ttu-id="80e2f-187">I movimenti che gli utenti eseguono su un oggetto 3D vengono guidati dalla progettazione degli inviti dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="80e2f-187">The gestures users perform on a 3D object are guided by the design of UI affordances.</span></span> <span data-ttu-id="80e2f-188">Ad esempio, in presenza di un piccolo punto di controllo gli utenti sono portati a usare il pollice e l'indice (ovvero ad avvicinare le dita), mentre davanti a un oggetto più grande possono decidere di afferrarlo usando tutte e cinque le dita.</span><span class="sxs-lookup"><span data-stu-id="80e2f-188">For example, a small control point might motivate users to pinch with their thumb and index finger, while a user might want to grab a larger object using all five fingers.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="80e2f-189">![Movimenti istintivi per un oggetto piccolo](images/instinctual-gestures-far-smallobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="80e2f-189">![instinctual gestures far small object](images/instinctual-gestures-far-smallobject.jpg)</span></span><br>
       <span data-ttu-id="80e2f-190">**Oggetto piccolo**</span><span class="sxs-lookup"><span data-stu-id="80e2f-190">**Small object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="80e2f-191">![Movimenti istintivi per un oggetto medio](images/instinctual-gestures-far-mediumobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="80e2f-191">![instinctual gestures far medium object](images/instinctual-gestures-far-mediumobject.jpg)</span></span><br>
        <span data-ttu-id="80e2f-192">**Oggetto medio**</span><span class="sxs-lookup"><span data-stu-id="80e2f-192">**Medium object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="80e2f-193">![Movimenti istintivi per un oggetto grande](images/instinctual-gestures-far-largeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="80e2f-193">![instinctual gestures far large object](images/instinctual-gestures-far-largeobject.jpg)</span></span><br>
       <span data-ttu-id="80e2f-194">**Oggetto grande**</span><span class="sxs-lookup"><span data-stu-id="80e2f-194">**Large object**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a><span data-ttu-id="80e2f-195">Progettazione simmetrica tra le due mani e controller 6DoF</span><span class="sxs-lookup"><span data-stu-id="80e2f-195">Symmetric design between hands and 6 DoF controller</span></span> 

<span data-ttu-id="80e2f-196">Il concetto alla base del puntamento e commit per un'interazione da lontano inizialmente era stato creato e definito per il Portale realtà mista, in cui un utente indossa un visore VR immersive e interagisce con gli oggetti 3D tramite controller del movimento.</span><span class="sxs-lookup"><span data-stu-id="80e2f-196">The concept of point and commit for far interaction was initially created and defined for the Mixed Reality Portal (MRP) where a user wears an immersive headset and interacts with 3D objects via motion controllers.</span></span> <span data-ttu-id="80e2f-197">Tali controller emettono raggi per il puntamento e la manipolazione degli oggetti lontani.</span><span class="sxs-lookup"><span data-stu-id="80e2f-197">The motion controllers shoot out rays for pointing and manipulating far objects.</span></span> <span data-ttu-id="80e2f-198">Sui controller sono presenti pulsanti che consentono di eseguire ulteriormente il commit di azioni diverse.</span><span class="sxs-lookup"><span data-stu-id="80e2f-198">There are buttons on the controllers for further committing different actions.</span></span> <span data-ttu-id="80e2f-199">Noi sfruttiamo il modello di interazione dei raggi e lo abbiamo associato a entrambe le mani.</span><span class="sxs-lookup"><span data-stu-id="80e2f-199">We leverage the interaction model of rays and attached them to both hands.</span></span> <span data-ttu-id="80e2f-200">Grazie a questa progettazione simmetrica, gli utenti abituati a operare con il Portale realtà mista non dovranno apprendere un altro modello di interazione per il puntamento e la manipolazione da lontano quando usano HoloLens 2 e viceversa.</span><span class="sxs-lookup"><span data-stu-id="80e2f-200">With this symmetric design, users who are familiar with MRP won't need to learn another interaction model for far pointing and manipulation when they use HoloLen 2, and vice versa.</span></span>    

:::row:::
    :::column:::
        <span data-ttu-id="80e2f-201">![Progettazione simmetrica per raggi con controller](images/symmetric-design-for-rays-controllers.jpg)</span><span class="sxs-lookup"><span data-stu-id="80e2f-201">![symmetric design for rays with controllers](images/symmetric-design-for-rays-controllers.jpg)</span></span><br>
        <span data-ttu-id="80e2f-202">**Raggi del controller**</span><span class="sxs-lookup"><span data-stu-id="80e2f-202">**Controller rays**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="80e2f-203">![Progettazione simmetrica per raggi con le mani](images/symmetric-design-for-rays-hands.jpg)</span><span class="sxs-lookup"><span data-stu-id="80e2f-203">![symmetric design for rays with hands](images/symmetric-design-for-rays-hands.jpg)</span></span><br>
        <span data-ttu-id="80e2f-204">**Raggi della mano**</span><span class="sxs-lookup"><span data-stu-id="80e2f-204">**Hand rays**</span></span><br>
    :::column-end:::
:::row-end:::

<br>


---

## <a name="hand-ray-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="80e2f-205">Raggio della mano in MRTK (Mixed Reality Toolkit) per Unity</span><span class="sxs-lookup"><span data-stu-id="80e2f-205">Hand ray in MRTK(Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="80e2f-206">Per impostazione predefinita, MRTK fornisce un file prefab relativo al raggio della mano ([DefaultControllerPointer.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Pointers)) con lo stesso stato di visualizzazione del raggio della mano di sistema della shell.</span><span class="sxs-lookup"><span data-stu-id="80e2f-206">By default, MRTK provides a hand ray prefab([DefaultControllerPointer.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Pointers)) which has the same visual state as the shell's system hand ray.</span></span> <span data-ttu-id="80e2f-207">Tale file viene assegnato in Pointers (Puntatori) nel profilo di input di MRTK.</span><span class="sxs-lookup"><span data-stu-id="80e2f-207">It is assigned in MRTK's Input profile, under Pointers.</span></span> <span data-ttu-id="80e2f-208">Nel visore VR immersive di Windows Mixed Reality gli stessi raggi vengono usati anche per i controller del movimento.</span><span class="sxs-lookup"><span data-stu-id="80e2f-208">In Windows Mixed Reality immersive headset, the same rays are used for the motion controllers, as well.</span></span>

* [<span data-ttu-id="80e2f-209">MRTK - Profilo del puntatore</span><span class="sxs-lookup"><span data-stu-id="80e2f-209">MRTK - Pointer profile</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html#pointer-configuration)
* [<span data-ttu-id="80e2f-210">MRTK - Sistema di input</span><span class="sxs-lookup"><span data-stu-id="80e2f-210">MRTK - Input system</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)
* [<span data-ttu-id="80e2f-211">MRTK - Puntatori</span><span class="sxs-lookup"><span data-stu-id="80e2f-211">MRTK - Pointers</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html)


---

## <a name="see-also"></a><span data-ttu-id="80e2f-212">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="80e2f-212">See also</span></span>
* [<span data-ttu-id="80e2f-213">Manipolazione diretta con le mani</span><span class="sxs-lookup"><span data-stu-id="80e2f-213">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="80e2f-214">Sguardo fisso e commit</span><span class="sxs-lookup"><span data-stu-id="80e2f-214">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="80e2f-215">Mani - Manipolazione diretta</span><span class="sxs-lookup"><span data-stu-id="80e2f-215">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="80e2f-216">Mani - Movimenti</span><span class="sxs-lookup"><span data-stu-id="80e2f-216">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="80e2f-217">Interazioni istintive</span><span class="sxs-lookup"><span data-stu-id="80e2f-217">Instinctual interactions</span></span>](interaction-fundamentals.md)

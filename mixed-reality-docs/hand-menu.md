---
title: Menu a mano
description: I menu a mano consentono agli utenti di visualizzare rapidamente l'interfaccia utente collegata manualmente per le funzioni usate di frequente. Queste sono le procedure consigliate e le raccomandazioni per i menu a mano.
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: mano, menu, pulsante, accesso rapido, layout
ms.openlocfilehash: c0e1800be69a15706e17f40b1601fc79d05e5d75
ms.sourcegitcommit: 6844930427b658ae31f642c395cd8a3b3cdbf857
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/07/2020
ms.locfileid: "75723260"
---
# <a name="hand-menu"></a><span data-ttu-id="bba07-105">Menu a mano</span><span class="sxs-lookup"><span data-stu-id="bba07-105">Hand menu</span></span>

![Posizione della mano del lato ulnare](images/UX/UX_Hero_HandMenu.jpg)

<span data-ttu-id="bba07-107">I menu a mano consentono agli utenti di visualizzare rapidamente l'interfaccia utente collegata manualmente per le funzioni usate di frequente.</span><span class="sxs-lookup"><span data-stu-id="bba07-107">Hand menus allow users to quickly bring up hand-attached UI for frequently used functions.</span></span> 

<span data-ttu-id="bba07-108">Di seguito sono riportate le procedure consigliate per i menu a mano.</span><span class="sxs-lookup"><span data-stu-id="bba07-108">Below are the best practices we have found for hand menus.</span></span> <span data-ttu-id="bba07-109">È anche possibile trovare una scena di esempio che illustra il menu a mano in [MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup).</span><span class="sxs-lookup"><span data-stu-id="bba07-109">You can also find an example scene demonstrating the hand menu in [MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup).</span></span>

<br>

---

## <a name="behavior-best-practices"></a><span data-ttu-id="bba07-110">Procedure consigliate per il comportamento</span><span class="sxs-lookup"><span data-stu-id="bba07-110">Behavior best practices</span></span>
<span data-ttu-id="bba07-111">**A. mantenere il numero di pulsanti piccoli:** a causa della distanza di chiusura tra un menu con blocco manuale e gli occhi e anche la tendenza dell'utente a concentrarsi su un'area visiva relativamente piccola in qualsiasi momento (il cono di attenzione è di circa 10 gradi), si consiglia di mantenere il numero di pulsanti piccoli.</span><span class="sxs-lookup"><span data-stu-id="bba07-111">**A. Keep the number of buttons small:** Due to the close distance between a hand-locked menu and the eyes and also the user's tendency to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), we recommend keeping the number of buttons small.</span></span> <span data-ttu-id="bba07-112">In base all'esplorazione, una colonna con tre pulsanti funziona bene mantenendo tutto il contenuto all'interno del campo di visualizzazione (FOV) anche quando gli utenti spostano le mani al centro del FOV.</span><span class="sxs-lookup"><span data-stu-id="bba07-112">Based on our exploration, one column with three buttons work well by keeping all the content within the field of view (FOV) even when users move their hands to the center of the FOV.</span></span> 

<span data-ttu-id="bba07-113">**B. utilizzare il menu a mano per un'azione rapida:** la generazione di un ARM e la gestione della posizione possono causare un facile affaticamento dell'ARM.</span><span class="sxs-lookup"><span data-stu-id="bba07-113">**B. Utilize hand menu for quick action:** Raising an arm and maintaining the position could easily cause arm fatigue.</span></span> <span data-ttu-id="bba07-114">Usare un metodo con blocco manuale per il menu che richiede una breve interazione.</span><span class="sxs-lookup"><span data-stu-id="bba07-114">Use a hand-locked method for the menu requiring a short interaction.</span></span> <span data-ttu-id="bba07-115">Se il menu è complesso e richiede tempi di interazione estesi, prendere in considerazione l'uso di un blocco globale o del corpo.</span><span class="sxs-lookup"><span data-stu-id="bba07-115">If your menu is complex and requires extended interaction times, consider using world-locked or body-locked instead.</span></span> 

<span data-ttu-id="bba07-116">**C. angolo del pulsante/pannello:** i menu devono essere posizionati nella parte opposta e al centro della testa: ciò consente a una mano naturale di interagire con il menu con la mano opposta, evitando posizioni scomode o scomode quando si toccano i pulsanti.</span><span class="sxs-lookup"><span data-stu-id="bba07-116">**C. Button / Panel angle:** Menus should billboard towards the opposite shoulder and middle of the head: This allows a natural hand move to interact with the menu with the opposite hand and avoids any awkward or uncomfortable hand positions when touching buttons.</span></span> 

<span data-ttu-id="bba07-117">**D. provare a supportare il supporto di una sola mano o di un'operazione senza mani:** non presupporre che entrambe le mani dell'utente siano sempre disponibili.</span><span class="sxs-lookup"><span data-stu-id="bba07-117">**D. Consider supporting one-handed or hands-free operation:** Do not assume both of the user's hands are always available.</span></span> <span data-ttu-id="bba07-118">Prendere in considerazione una vasta gamma di contesti quando una o entrambe le mani non sono disponibili e assicurarsi che gli account di progettazione per tali situazioni.</span><span class="sxs-lookup"><span data-stu-id="bba07-118">Consider a wide range of contexts when one or both hands are not available, and make sure your design accounts for those situations.</span></span> <span data-ttu-id="bba07-119">Per supportare un menu a mano singola, è possibile provare a eseguire la transizione della posizione del menu da Hand-locked a blocco globale quando viene eseguito il capovolgimento della mano (passa a una Palma).</span><span class="sxs-lookup"><span data-stu-id="bba07-119">To support a one-handed hand menu, you can try transitioning the menu placement from hand-locked to world-locked when the hand flips (goes palm down).</span></span> <span data-ttu-id="bba07-120">Per gli scenari pratici, provare a usare un comando vocale per richiamare i pulsanti del menu a forma di mano.</span><span class="sxs-lookup"><span data-stu-id="bba07-120">For hands-free scenarios, consider using a voice command to invoke the hand menu buttons.</span></span>

<span data-ttu-id="bba07-121">**E. chiamata in due passaggi:** se si usa solo il palmare come evento per attivare il menu a mano, è possibile che venga visualizzato accidentalmente quando non è necessario (falso positivo), perché le persone spostano le mani molto intenzionalmente (per la manipolazione delle comunicazioni e degli oggetti) e non intenzionalmente.</span><span class="sxs-lookup"><span data-stu-id="bba07-121">**E. Two-step invocation:** If you use just palm-up as an event to trigger the hand menu, it may accidentally appear when you don't need it (false-positive), because people move their hands a lot both intentionally (for communication and object manipulation) and unintentionally.</span></span> <span data-ttu-id="bba07-122">Se si verificano falsi positivi nell'app, è consigliabile aggiungere un passaggio aggiuntivo oltre all'evento di backup per richiamare il menu a mano, ad esempio le dita completamente aperte.</span><span class="sxs-lookup"><span data-stu-id="bba07-122">If you experience false-positives in your app, consider adding an additional step besides the palm-up event to invoke the hand menu such as fully opened fingers.</span></span>

<span data-ttu-id="bba07-123">**F. evitare di aggiungere pulsanti vicino al polso (pulsante Home System):** se i pulsanti del menu a mano sono posizionati troppo vicino al pulsante Home, è possibile che venga accidentalmente attivato durante l'interazione con il menu a mano.</span><span class="sxs-lookup"><span data-stu-id="bba07-123">**F. Avoid adding buttons near the wrist (system home button):** If the hand menu buttons are placed too close to the home button, it may get accidentally triggered while interacting with the hand menu.</span></span>

<span data-ttu-id="bba07-124">**G. test** , test, test: le persone hanno corpi diversi, con soglie diverse per comodità e disagio e così via. Assicurarsi di testare la progettazione e di ricevere commenti e suggerimenti da un'ampia gamma di persone.</span><span class="sxs-lookup"><span data-stu-id="bba07-124">**G. Test, test, test:** People have different bodies, with different thresholds for comfort and discomfort, etc. Be sure to test out your design on and get feedback from a variety of people.</span></span>

<br>

---

## <a name="hand-menu-placement-best-practices"></a><span data-ttu-id="bba07-125">Procedure consigliate per la selezione dei menu a mano</span><span class="sxs-lookup"><span data-stu-id="bba07-125">Hand menu placement best practices</span></span>

<span data-ttu-id="bba07-126">Nell'anatomia umana, il nervo ulnare è un nervo che viene eseguito in prossimità dell'osso ulna.</span><span class="sxs-lookup"><span data-stu-id="bba07-126">In human anatomy, the ulnar nerve is a nerve that runs near the ulna bone.</span></span> <span data-ttu-id="bba07-127">L'ulna è un osso lungo trovato sull'avambraccio che si estende dal gomito al dito più piccolo.</span><span class="sxs-lookup"><span data-stu-id="bba07-127">The ulna is a long bone found in the forearm that stretches from the elbow to the smallest finger.</span></span>

<span data-ttu-id="bba07-128">Di seguito sono riportati 2 posizionamenti consigliati in base alle esplorazioni:</span><span class="sxs-lookup"><span data-stu-id="bba07-128">Below are 2 recommended placements based on our explorations:</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="bba07-129">![posizione della mano del lato ulnare](images/UlnarSideHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="bba07-129">![Ulnar side hand location](images/UlnarSideHandMenu.gif)</span></span><br>
        <span data-ttu-id="bba07-130">**A. ulnare all'interno di Palm**</span><span class="sxs-lookup"><span data-stu-id="bba07-130">**A. Ulnar inside palm**</span></span><br>
        <span data-ttu-id="bba07-131">Questa posizione è affidabile perché le mani non si sovrappongono.</span><span class="sxs-lookup"><span data-stu-id="bba07-131">This position is reliable because the hands do not overlap each other.</span></span> <span data-ttu-id="bba07-132">Si tratta di un fattore fondamentale per il rilevamento e il rilevamento delle carte accurate.</span><span class="sxs-lookup"><span data-stu-id="bba07-132">This is critical for accurate hand detection and tracking.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="bba07-133">![posizione della mano del lato ulnare](images/UlnarAboveHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="bba07-133">![Ulnar side hand location](images/UlnarAboveHandMenu.gif)</span></span><br>
        <span data-ttu-id="bba07-134">**B. oltre la mano del ulnare**</span><span class="sxs-lookup"><span data-stu-id="bba07-134">**B. Ulnar above hand**</span></span><br>
        <span data-ttu-id="bba07-135">Questa posizione è comoda per gli utenti perché non è necessario aumentare il proprio ARM per interagire con il menu a mano.</span><span class="sxs-lookup"><span data-stu-id="bba07-135">This location is comfortable for users because they don't need to raise their arm too much to interact with the hand menu.</span></span> <span data-ttu-id="bba07-136">È consigliabile posizionare i menu **13cm** sopra la Palma e allineare i pulsanti all'interno della palma ulnar.</span><span class="sxs-lookup"><span data-stu-id="bba07-136">We recommend placing menus **13cm** above the palm and align the buttons inside the ulnar palm.</span></span> [<span data-ttu-id="bba07-137">Altre informazioni sulle dimensioni dei pulsanti ottimali</span><span class="sxs-lookup"><span data-stu-id="bba07-137">Read more about the optimal button size</span></span>](interactable-object.md)<br>
        <br>
        <span data-ttu-id="bba07-138">Per motivi tecnici, è consigliabile usare questa località con un'implementazione richiesta: lo sviluppatore dovrà bloccare il menu una volta che la mano opposta dell'utente si avvicina all'interazione con l'utente.</span><span class="sxs-lookup"><span data-stu-id="bba07-138">For technical reasons we recommend this location with one required implementation: the developer will need to freeze the menu once the user's opposite hand gets close to interacting with it.</span></span> <span data-ttu-id="bba07-139">In questo modo si eviterà che nervosismo si sovrappongano e anche un targeting più rapido dei pulsanti.</span><span class="sxs-lookup"><span data-stu-id="bba07-139">This will avoid jitteriness from overlapping hands and also allows for a faster targeting of the buttons.</span></span><br>
        <br>
        <span data-ttu-id="bba07-140">Le fotocamere HoloLens 2 identificano le mani accuratamente quando sono separate tra loro.</span><span class="sxs-lookup"><span data-stu-id="bba07-140">HoloLens 2 cameras identify hands accurately when they are separate from each other.</span></span> <span data-ttu-id="bba07-141">Qualsiasi mano sovrapposta può causare la disattivazione dei menu a mano dalla posizione di ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="bba07-141">Any overlapping hands can cause hand menus move away from the anchor location.</span></span><br>
    :::column-end:::
:::row-end:::



<br>

---

## <a name="menu-positions-that-are-not-recommended"></a><span data-ttu-id="bba07-142">Posizioni dei menu non consigliate</span><span class="sxs-lookup"><span data-stu-id="bba07-142">Menu positions that are not recommended</span></span>
<span data-ttu-id="bba07-143">La ricerca degli utenti è stata eseguita con layout e percorsi di menu diversi. i percorsi dei menu seguenti **non sono consigliati**. trovare i svantaggi di ogni studio di seguito:</span><span class="sxs-lookup"><span data-stu-id="bba07-143">We have done user research with different menus layouts and locations, the following menu locations are **NOT recommended**, find the cons of each study below:</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="bba07-144">![sopra](images/AboveArm.gif) ARM</span><span class="sxs-lookup"><span data-stu-id="bba07-144">![Above arm](images/AboveArm.gif)</span></span><br>
        <span data-ttu-id="bba07-145">**Sopra il ARM**</span><span class="sxs-lookup"><span data-stu-id="bba07-145">**Above the arm**</span></span><br>
        <span data-ttu-id="bba07-146">1-difficile mantenere il rilevamento della mano corretta</span><span class="sxs-lookup"><span data-stu-id="bba07-146">1 - Difficult to maintain good hand tracking</span></span><br>
        <span data-ttu-id="bba07-147">2-causa la fatica dell'utente a causa di una posizione non naturale</span><span class="sxs-lookup"><span data-stu-id="bba07-147">2 - Causes user fatigue due to unnatural position</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="bba07-148">![sopra le dita](images/AboveFingers.gif)</span><span class="sxs-lookup"><span data-stu-id="bba07-148">![Above fingers](images/AboveFingers.gif)</span></span><br>
        <span data-ttu-id="bba07-149">**Sopra le dita**</span><span class="sxs-lookup"><span data-stu-id="bba07-149">**Above fingers**</span></span><br>
        <span data-ttu-id="bba07-150">affaticamento a una mano dovuta a un periodo di tempo prolungato</span><span class="sxs-lookup"><span data-stu-id="bba07-150">1 - Hand fatigue due to holding hand for long time</span></span><br>
        <span data-ttu-id="bba07-151">problemi di rilevamento a due mani sull'indice e sul dito medio</span><span class="sxs-lookup"><span data-stu-id="bba07-151">2 - Hand tracking issues on index and middle finger</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="bba07-152">![sopra il centro](images/handCenter.gif) Palm</span><span class="sxs-lookup"><span data-stu-id="bba07-152">![Above center palm](images/handCenter.gif)</span></span><br>
        <span data-ttu-id="bba07-153">**Sopra-centro Palm**</span><span class="sxs-lookup"><span data-stu-id="bba07-153">**Above-center palm**</span></span><br>
        <span data-ttu-id="bba07-154">problemi di rilevamento a una mano dovuti a mani sovrapposte</span><span class="sxs-lookup"><span data-stu-id="bba07-154">1 - Hand tracking issues due to overlapping hands</span></span><br>
        <span data-ttu-id="bba07-155">affaticamento a due mani a causa del tempo di attesa lungo per interagire con i menu</span><span class="sxs-lookup"><span data-stu-id="bba07-155">2 - Hand fatigue due to holding hands for long time in order to interact with menus</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="bba07-156">![parte superiore](images/TopFingerTip.gif) a **portata di mano**</span><span class="sxs-lookup"><span data-stu-id="bba07-156">![Top Fingertip](images/TopFingerTip.gif) **Top fingertip**</span></span><br>
        <span data-ttu-id="bba07-157">problemi di rilevamento a una mano</span><span class="sxs-lookup"><span data-stu-id="bba07-157">1 - Hand tracking issues</span></span><br>
        <span data-ttu-id="bba07-158">2-mano di mano che si tiene sotto la postura normale</span><span class="sxs-lookup"><span data-stu-id="bba07-158">2 - Hand fatigue holding hand above normal posture</span></span><br>
        <span data-ttu-id="bba07-159">3-problemi durante la pressione di pulsanti con altre dita per errore a causa dello spazio limitato tra le dita</span><span class="sxs-lookup"><span data-stu-id="bba07-159">3 - Issues pressing buttons with other fingers by accident due to limited space between fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="bba07-160">![back of the ARM](images/BackOfTheArm.gif)</span><span class="sxs-lookup"><span data-stu-id="bba07-160">![Back of the Arm](images/BackOfTheArm.gif)</span></span><br>
        <span data-ttu-id="bba07-161">**Back of the ARM**</span><span class="sxs-lookup"><span data-stu-id="bba07-161">**Back of the arm**</span></span><br>
        <span data-ttu-id="bba07-162">1-è possibile attivare il pulsante Home per errore</span><span class="sxs-lookup"><span data-stu-id="bba07-162">1 - Can trigger home button by accident</span></span><br>
        <span data-ttu-id="bba07-163">2-posizione naturale o comoda per gli utenti</span><span class="sxs-lookup"><span data-stu-id="bba07-163">2 - Not a natural or comfortable position for users</span></span>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="bba07-164">Menu a mano in MRTK (Mixed Reality Toolkit) per Unity</span><span class="sxs-lookup"><span data-stu-id="bba07-164">Hand menu in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="bba07-165">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** fornisce gli script e le scene di esempio per il menu a mano.</span><span class="sxs-lookup"><span data-stu-id="bba07-165">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and example scenes for the hand menu.</span></span> <span data-ttu-id="bba07-166">Lo script del Risolutore HandConstraintPalmUp consente di associare facilmente tutti gli oggetti alle mani con diverse opzioni configurabili.</span><span class="sxs-lookup"><span data-stu-id="bba07-166">HandConstraintPalmUp solver script allows you easily attach any objects to the hands with various configurable options.</span></span>

* [<span data-ttu-id="bba07-167">Menu a MRTK con HandConstraint e HandConstraintPalmUp</span><span class="sxs-lookup"><span data-stu-id="bba07-167">MRTK - Hand Menu with HandConstraint and HandConstraintPalmUp </span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup)


<br>

---


## <a name="see-also"></a><span data-ttu-id="bba07-168">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="bba07-168">See also</span></span>

* [<span data-ttu-id="bba07-169">Cursori</span><span class="sxs-lookup"><span data-stu-id="bba07-169">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="bba07-170">Raggio della mano</span><span class="sxs-lookup"><span data-stu-id="bba07-170">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="bba07-171">Button</span><span class="sxs-lookup"><span data-stu-id="bba07-171">Button</span></span>](button.md)
* [<span data-ttu-id="bba07-172">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="bba07-172">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="bba07-173">Rettangolo di selezione e barra dell'app</span><span class="sxs-lookup"><span data-stu-id="bba07-173">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="bba07-174">Manipolazione</span><span class="sxs-lookup"><span data-stu-id="bba07-174">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="bba07-175">Menu a mano</span><span class="sxs-lookup"><span data-stu-id="bba07-175">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="bba07-176">Menu adiacente</span><span class="sxs-lookup"><span data-stu-id="bba07-176">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="bba07-177">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="bba07-177">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="bba07-178">Comando vocale</span><span class="sxs-lookup"><span data-stu-id="bba07-178">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="bba07-179">Tastiera</span><span class="sxs-lookup"><span data-stu-id="bba07-179">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="bba07-180">Descrizione comando</span><span class="sxs-lookup"><span data-stu-id="bba07-180">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="bba07-181">Slate</span><span class="sxs-lookup"><span data-stu-id="bba07-181">Slate</span></span>](slate.md)
* [<span data-ttu-id="bba07-182">Dispositivo di scorrimento</span><span class="sxs-lookup"><span data-stu-id="bba07-182">Slider</span></span>](slider.md)
* [<span data-ttu-id="bba07-183">Shader</span><span class="sxs-lookup"><span data-stu-id="bba07-183">Shader</span></span>](shader.md)
* [<span data-ttu-id="bba07-184">Billboarding e tag-along</span><span class="sxs-lookup"><span data-stu-id="bba07-184">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="bba07-185">Visualizzazione dello stato</span><span class="sxs-lookup"><span data-stu-id="bba07-185">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="bba07-186">Magnetismo di superficie</span><span class="sxs-lookup"><span data-stu-id="bba07-186">Surface magnetism</span></span>](surface-magnetism.md)

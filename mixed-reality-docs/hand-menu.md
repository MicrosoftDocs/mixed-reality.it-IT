---
title: Menu a mano
description: I menu a mano consentono agli utenti di visualizzare rapidamente l'interfaccia utente collegata manualmente per le funzioni usate di frequente. Queste sono le procedure consigliate e le raccomandazioni per i menu a mano.
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: mano, menu, pulsante, accesso rapido, layout
ms.openlocfilehash: d1d15b36bab2ca2082ca4ba91b9c64862893f80c
ms.sourcegitcommit: fef42e2908e49822f2d13b05d2f9260bf0d72158
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/07/2020
ms.locfileid: "86061169"
---
# <a name="hand-menu"></a><span data-ttu-id="d09c6-105">Menu a mano</span><span class="sxs-lookup"><span data-stu-id="d09c6-105">Hand menu</span></span>

![Posizione della mano del lato ulnare](images/UX/UX_Hero_HandMenu.jpg)

<span data-ttu-id="d09c6-107">Il menu a mano è uno dei modelli UX più esclusivi in HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="d09c6-107">The hand menu is one of the most unique UX patterns in HoloLens 2.</span></span> <span data-ttu-id="d09c6-108">Consente di visualizzare rapidamente l'interfaccia utente collegata manualmente.</span><span class="sxs-lookup"><span data-stu-id="d09c6-108">It allows you to quickly bring up hand-attached UI.</span></span> <span data-ttu-id="d09c6-109">Poiché è accessibile in qualsiasi momento e può essere visualizzato e nascosto facilmente, è ideale per le azioni rapide.</span><span class="sxs-lookup"><span data-stu-id="d09c6-109">Since it's accessible anytime and can be shown and hidden easily, it's great for quick actions.</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAg]

<span data-ttu-id="d09c6-110">Sono disponibili le procedure consigliate per l'uso dei menu a mano nell'elenco seguente.</span><span class="sxs-lookup"><span data-stu-id="d09c6-110">You'll find our recommended best practices for working with hand menus in the list below.</span></span> <span data-ttu-id="d09c6-111">È anche possibile trovare una scena di esempio che illustra il menu a mano in [MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html).</span><span class="sxs-lookup"><span data-stu-id="d09c6-111">You can also find an example scene demonstrating the hand menu in [MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html).</span></span>

<br>


---

## <a name="best-practices"></a><span data-ttu-id="d09c6-112">Procedure consigliate</span><span class="sxs-lookup"><span data-stu-id="d09c6-112">Best practices</span></span>
<span data-ttu-id="d09c6-113">**Mantieni il numero di pulsanti piccoli**</span><span class="sxs-lookup"><span data-stu-id="d09c6-113">**Keep the number of buttons small**</span></span> 

<span data-ttu-id="d09c6-114">A causa della distanza di chiusura tra un menu con blocco manuale e gli occhi e anche la tendenza dell'utente a concentrarsi su un'area visiva relativamente piccola in qualsiasi momento (il cono di attenzione è di circa 10 gradi), è consigliabile mantenere il numero di pulsanti piccoli.</span><span class="sxs-lookup"><span data-stu-id="d09c6-114">Due to the close distance between a hand-locked menu and the eyes and also the user's tendency to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), we recommend keeping the number of buttons small.</span></span> <span data-ttu-id="d09c6-115">In base all'esplorazione, una colonna con tre pulsanti funziona bene mantenendo tutto il contenuto all'interno del campo di visualizzazione (FOV) anche quando un utente sposta le mani al centro di FOV.</span><span class="sxs-lookup"><span data-stu-id="d09c6-115">Based on our exploration, one column with three buttons works well by keeping all the content within the field of view (FOV) even when a user moves their hands to the center of the FOV.</span></span> 

<span data-ttu-id="d09c6-116">**Usare il menu a mano per l'azione rapida**</span><span class="sxs-lookup"><span data-stu-id="d09c6-116">**Utilize hand menu for quick action**</span></span> 

<span data-ttu-id="d09c6-117">La generazione di un ARM e la gestione della posizione possono causare un facile affaticamento del braccio.</span><span class="sxs-lookup"><span data-stu-id="d09c6-117">Raising an arm and maintaining the position could easily cause arm fatigue.</span></span> <span data-ttu-id="d09c6-118">Usare un metodo con blocco manuale per il menu che richiede una breve interazione.</span><span class="sxs-lookup"><span data-stu-id="d09c6-118">Use a hand-locked method for the menu requiring a short interaction.</span></span> <span data-ttu-id="d09c6-119">Se il menu è complesso e richiede tempi di interazione estesi, prendere in considerazione l'uso di un blocco globale o del corpo.</span><span class="sxs-lookup"><span data-stu-id="d09c6-119">If your menu is complex and requires extended interaction times, consider using world-locked or body-locked instead.</span></span> 

<span data-ttu-id="d09c6-120">**Angolo pulsante/pannello**</span><span class="sxs-lookup"><span data-stu-id="d09c6-120">**Button / Panel angle**</span></span>

<span data-ttu-id="d09c6-121">I menu devono essere posizionati sulla spalla opposta e al centro della testa: ciò consente a una mano naturale di interagire con il menu con la mano opposta, evitando eventuali posizioni scomode o scomode quando si toccano i pulsanti.</span><span class="sxs-lookup"><span data-stu-id="d09c6-121">Menus should billboard towards the opposite shoulder and middle of the head: This allows a natural hand move to interact with the menu with the opposite hand and avoids any awkward or uncomfortable hand positions when touching buttons.</span></span> 

<span data-ttu-id="d09c6-122">**Provare a supportare un'operazione a mano o senza mani**</span><span class="sxs-lookup"><span data-stu-id="d09c6-122">**Consider supporting one-handed or hands-free operation**</span></span>

<span data-ttu-id="d09c6-123">Non presupporre che entrambe le mani dell'utente siano sempre disponibili.</span><span class="sxs-lookup"><span data-stu-id="d09c6-123">Do not assume both of the user's hands are always available.</span></span> <span data-ttu-id="d09c6-124">Prendere in considerazione una vasta gamma di contesti quando una o entrambe le mani non sono disponibili e assicurarsi che gli account di progettazione per tali situazioni.</span><span class="sxs-lookup"><span data-stu-id="d09c6-124">Consider a wide range of contexts when one or both hands are not available, and make sure your design accounts for those situations.</span></span> <span data-ttu-id="d09c6-125">Per supportare un menu a mano singola, è possibile provare a eseguire la transizione della posizione del menu da Hand-locked a blocco globale quando viene eseguito il capovolgimento della mano (passa a una Palma).</span><span class="sxs-lookup"><span data-stu-id="d09c6-125">To support a one-handed hand menu, you can try transitioning the menu placement from hand-locked to world-locked when the hand flips (goes palm down).</span></span> <span data-ttu-id="d09c6-126">Per gli scenari senza praticità, provare a usare un comando vocale per richiamare il menu a forma di mano.</span><span class="sxs-lookup"><span data-stu-id="d09c6-126">For hands-free scenarios, consider using a voice command to invoke the hand menu.</span></span>

<span data-ttu-id="d09c6-127">**Evitare di aggiungere pulsanti vicino al polso (pulsante Home System)**</span><span class="sxs-lookup"><span data-stu-id="d09c6-127">**Avoid adding buttons near the wrist (system home button)**</span></span>

<span data-ttu-id="d09c6-128">Se i pulsanti del menu a mano sono posizionati troppo vicino al pulsante Home, è possibile che venga accidentalmente attivato durante l'interazione con il menu a mano.</span><span class="sxs-lookup"><span data-stu-id="d09c6-128">If the hand menu buttons are placed too close to the home button, it may accidentally trigger while interacting with the hand menu.</span></span>

<br>

## <a name="hand-menu-with-large-and-complex-ui-controls"></a><span data-ttu-id="d09c6-129">Menu a mano con controlli dell'interfaccia utente complessi e di grandi dimensioni</span><span class="sxs-lookup"><span data-stu-id="d09c6-129">Hand menu with large and complex UI controls</span></span>
<img src="images/UX/HandMenu_SizeExample.png" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<span data-ttu-id="d09c6-130">È consigliabile limitare il numero di pulsanti o controlli dell'interfaccia utente nei menu collegati manualmente.</span><span class="sxs-lookup"><span data-stu-id="d09c6-130">It's recommended to limit the number of buttons or UI controls on hand-attached menus.</span></span> <span data-ttu-id="d09c6-131">Questo perché l'interazione estesa con un numero elevato di elementi dell'interfaccia utente può causare affaticamento ARM.</span><span class="sxs-lookup"><span data-stu-id="d09c6-131">This is because extended interaction with a large number of UI elements can cause arm fatigue.</span></span> <span data-ttu-id="d09c6-132">Se l'esperienza richiede un menu di grandi dimensioni, è possibile consentire all'utente di bloccare il menu in modo semplice.</span><span class="sxs-lookup"><span data-stu-id="d09c6-132">If your experience requires a large menu, provide an easy way for the user to world lock the menu.</span></span> <span data-ttu-id="d09c6-133">Una tecnica consigliata è quella di bloccare in tutto il mondo quando la mano scende o si capovolge dall'utente.</span><span class="sxs-lookup"><span data-stu-id="d09c6-133">One technique we recommend is to world-lock then menu when the hand drops or flips away from the user.</span></span> <span data-ttu-id="d09c6-134">Una seconda tecnica consiste nel consentire all'utente di acquisire direttamente il menu con l'altra parte.</span><span class="sxs-lookup"><span data-stu-id="d09c6-134">A second technique is to allow the user to directly grab the menu with the other hand.</span></span> <span data-ttu-id="d09c6-135">Quando l'utente rilascia il menu, il menu deve bloccare il mondo.</span><span class="sxs-lookup"><span data-stu-id="d09c6-135">When the user releases the menu, the menu should world lock.</span></span> <span data-ttu-id="d09c6-136">In questo modo, un utente può interagire con diversi elementi dell'interfaccia utente in modo confortevole e sicuro per un lungo periodo di tempo.</span><span class="sxs-lookup"><span data-stu-id="d09c6-136">This way, a user can interact with various UI elements comfortably and confidently over an extended period of time.</span></span> 

<span data-ttu-id="d09c6-137">Quando il menu è bloccato a livello globale, assicurarsi di fornire un modo per spostare il menu e chiudere il menu quando non è più necessario.</span><span class="sxs-lookup"><span data-stu-id="d09c6-137">When the menu is world-locked, make sure to provide a way to move the menu, and close the menu when it's no longer needed.</span></span> <span data-ttu-id="d09c6-138">Rendere il menu mobile fornendo handle sui lati o nella parte superiore del menu.</span><span class="sxs-lookup"><span data-stu-id="d09c6-138">Make the menu movable by providing handles on the sides or top of menu.</span></span> <span data-ttu-id="d09c6-139">Aggiungere un pulsante Chiudi per consentire la chiusura del menu.</span><span class="sxs-lookup"><span data-stu-id="d09c6-139">Add a close button to allow the menu to close.</span></span> <span data-ttu-id="d09c6-140">Consente al menu di ricollegare la mano quando l'utente si trova a far fronte all'utente.</span><span class="sxs-lookup"><span data-stu-id="d09c6-140">Allow for the menu to re-attach to the hand when the user hand faces the user.</span></span> <span data-ttu-id="d09c6-141">Si consiglia inoltre di richiedere che gli utenti si trovino a loro disposizione per evitare le attivazioni false (vedere di seguito).</span><span class="sxs-lookup"><span data-stu-id="d09c6-141">We also recommend requiring that the users gazes at their hand to prevent false activations (see below).</span></span>

<span data-ttu-id="d09c6-142">**Menu di grandi dimensioni che mostra un problema di usabilità**</span><span class="sxs-lookup"><span data-stu-id="d09c6-142">**Large menu that shows a usability issue**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AOPx]

<span data-ttu-id="d09c6-143">**Menu con blocco globale sulla selezione della mano**</span><span class="sxs-lookup"><span data-stu-id="d09c6-143">**World-locked menu on hand drop**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AGZi]

<span data-ttu-id="d09c6-144">**Manuale di & pull per il menu di scelta rapida**</span><span class="sxs-lookup"><span data-stu-id="d09c6-144">**Manual grab & pull to world-lock the menu**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAf]


## <a name="how-to-prevent-false-activation"></a><span data-ttu-id="d09c6-145">Come impedire l'attivazione falsa</span><span class="sxs-lookup"><span data-stu-id="d09c6-145">How to prevent false activation</span></span>

<span data-ttu-id="d09c6-146">Se si usa solo il Palm-up come un evento per attivare il menu a mano, è possibile che venga accidentalmente visualizzato quando non è necessario (falso positivo), perché le persone spostano le mani intenzionalmente (per la manipolazione delle comunicazioni e degli oggetti) e non intenzionalmente.</span><span class="sxs-lookup"><span data-stu-id="d09c6-146">If you use just palm-up as an event to trigger the hand menu, it may accidentally appear when you don't need it (false-positive), because people move their hands both intentionally (for communication and object manipulation) and unintentionally.</span></span> <span data-ttu-id="d09c6-147">Per ridurre le attivazioni false, aggiungere un passaggio aggiuntivo oltre all'evento di backup per richiamare il menu a mano, ad esempio le dita completamente aperte, o l'utente che sta intenzionalmente guardando la mano.</span><span class="sxs-lookup"><span data-stu-id="d09c6-147">To reduce false activations, add an additional step besides the palm-up event to invoke the hand menu (such as fully opened fingers, or the user intentionally gazing at their hand).</span></span>

<span data-ttu-id="d09c6-148">**Richiedi Palma piatta**</span><span class="sxs-lookup"><span data-stu-id="d09c6-148">**Require Flat Palm**</span></span>

<span data-ttu-id="d09c6-149">Richiedendo una mano piatta aperta, è possibile impedire l'attivazione falsa che può verificarsi quando l'utente manipola oggetti o movimenti durante la comunicazione all'interno di un ambiente.</span><span class="sxs-lookup"><span data-stu-id="d09c6-149">By requiring a flat open hand, you can prevent false activation that might occur as the user manipulates objects or gestures while communicating within an environment.</span></span> 

<span data-ttu-id="d09c6-150">**Richiedi lo sguardo**</span><span class="sxs-lookup"><span data-stu-id="d09c6-150">**Require Gaze**</span></span>

<span data-ttu-id="d09c6-151">Richiedendo all'utente di guardare la mano (con lo sguardo o con lo sguardo), impedisce le attivazioni false dovute all'utente che deve indirizzare intenzionalmente la propria attenzione alla mano come passaggio di attivazione secondaria (con una soglia di distanza ottimizzabile usata per consentire la comodità dell'utente).</span><span class="sxs-lookup"><span data-stu-id="d09c6-151">By requiring the user to gaze at their hand (either with eye gaze or head gaze), it prevents false activations due to the user having to intentionally direct their attention to the hand as a secondary activation step (with a tunable distance threshold used to allow for user comfort).</span></span>  

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4Asn4]

---

## <a name="hand-menu-placement-best-practices"></a><span data-ttu-id="d09c6-152">Procedure consigliate per la selezione dei menu a mano</span><span class="sxs-lookup"><span data-stu-id="d09c6-152">Hand menu placement best practices</span></span>

<span data-ttu-id="d09c6-153">Nell'anatomia umana, il nervo ulnare è un nervo che viene eseguito in prossimità dell'osso ulna.</span><span class="sxs-lookup"><span data-stu-id="d09c6-153">In human anatomy, the ulnar nerve is a nerve that runs near the ulna bone.</span></span> <span data-ttu-id="d09c6-154">L'ulna è un osso lungo trovato sull'avambraccio che si estende dal gomito al dito più piccolo.</span><span class="sxs-lookup"><span data-stu-id="d09c6-154">The ulna is a long bone found in the forearm that stretches from the elbow to the smallest finger.</span></span>

<span data-ttu-id="d09c6-155">Di seguito sono riportati 2 posizionamenti consigliati in base alle esplorazioni:</span><span class="sxs-lookup"><span data-stu-id="d09c6-155">Below are 2 recommended placements based on our explorations:</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="d09c6-156">![Posizione della mano del lato ulnare](images/UlnarSideHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="d09c6-156">![Ulnar side hand location](images/UlnarSideHandMenu.gif)</span></span><br>
        <span data-ttu-id="d09c6-157">**A. ulnare all'interno di Palm**</span><span class="sxs-lookup"><span data-stu-id="d09c6-157">**A. Ulnar inside palm**</span></span><br>
        <span data-ttu-id="d09c6-158">Questa posizione è affidabile perché le mani non si sovrappongono.</span><span class="sxs-lookup"><span data-stu-id="d09c6-158">This position is reliable because the hands do not overlap each other.</span></span> <span data-ttu-id="d09c6-159">Si tratta di un fattore fondamentale per il rilevamento e il rilevamento delle carte accurate.</span><span class="sxs-lookup"><span data-stu-id="d09c6-159">This is critical for accurate hand detection and tracking.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="d09c6-160">![Posizione della mano del lato ulnare](images/UlnarAboveHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="d09c6-160">![Ulnar side hand location](images/UlnarAboveHandMenu.gif)</span></span><br>
        <span data-ttu-id="d09c6-161">**B. oltre la mano del ulnare**</span><span class="sxs-lookup"><span data-stu-id="d09c6-161">**B. Ulnar above hand**</span></span><br>
        <span data-ttu-id="d09c6-162">Questa posizione è comoda per gli utenti perché non è necessario aumentare il proprio ARM per interagire con il menu a mano.</span><span class="sxs-lookup"><span data-stu-id="d09c6-162">This location is comfortable for users because they don't need to raise their arm too much to interact with the hand menu.</span></span> <span data-ttu-id="d09c6-163">È consigliabile posizionare i menu **13cm** sopra la Palma e allineare i pulsanti all'interno della palma ulnar.</span><span class="sxs-lookup"><span data-stu-id="d09c6-163">We recommend placing menus **13cm** above the palm and align the buttons inside the ulnar palm.</span></span> [<span data-ttu-id="d09c6-164">Altre informazioni sulle dimensioni dei pulsanti ottimali</span><span class="sxs-lookup"><span data-stu-id="d09c6-164">Read more about the optimal button size</span></span>](interactable-object.md)<br>
        <br>
        <span data-ttu-id="d09c6-165">Per motivi tecnici, è consigliabile usare questa località con un'implementazione richiesta: lo sviluppatore dovrà bloccare il menu una volta che la mano opposta dell'utente si avvicina all'interazione con l'utente.</span><span class="sxs-lookup"><span data-stu-id="d09c6-165">For technical reasons we recommend this location with one required implementation: the developer will need to freeze the menu once the user's opposite hand gets close to interacting with it.</span></span> <span data-ttu-id="d09c6-166">In questo modo si eviterà che nervosismo si sovrappongano e anche un targeting più rapido dei pulsanti.</span><span class="sxs-lookup"><span data-stu-id="d09c6-166">This will avoid jitteriness from overlapping hands and also allows for a faster targeting of the buttons.</span></span><br>
        <br>
        <span data-ttu-id="d09c6-167">Le fotocamere HoloLens 2 identificano le mani accuratamente quando sono separate tra loro.</span><span class="sxs-lookup"><span data-stu-id="d09c6-167">HoloLens 2 cameras identify hands accurately when they are separate from each other.</span></span> <span data-ttu-id="d09c6-168">Qualsiasi mano sovrapposta può causare la disattivazione dei menu a mano dalla posizione di ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="d09c6-168">Any overlapping hands can cause hand menus move away from the anchor location.</span></span><br>
    :::column-end:::
:::row-end:::



<br>

---

## <a name="menu-positions-that-are-not-recommended"></a><span data-ttu-id="d09c6-169">Posizioni dei menu non consigliate</span><span class="sxs-lookup"><span data-stu-id="d09c6-169">Menu positions that are not recommended</span></span>
<span data-ttu-id="d09c6-170">La ricerca degli utenti è stata eseguita con layout e percorsi di menu diversi. i percorsi dei menu seguenti **non sono consigliati**. trovare i svantaggi di ogni studio di seguito:</span><span class="sxs-lookup"><span data-stu-id="d09c6-170">We have done user research with different menus layouts and locations, the following menu locations are **NOT recommended**, find the cons of each study below:</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="d09c6-171">![Sopra ARM](images/AboveArm.gif)</span><span class="sxs-lookup"><span data-stu-id="d09c6-171">![Above arm](images/AboveArm.gif)</span></span><br>
        <span data-ttu-id="d09c6-172">**Sopra il ARM**</span><span class="sxs-lookup"><span data-stu-id="d09c6-172">**Above the arm**</span></span><br>
        <span data-ttu-id="d09c6-173">1-difficile mantenere il rilevamento della mano corretta</span><span class="sxs-lookup"><span data-stu-id="d09c6-173">1 - Difficult to maintain good hand tracking</span></span><br>
        <span data-ttu-id="d09c6-174">2-causa la fatica dell'utente a causa di una posizione non naturale</span><span class="sxs-lookup"><span data-stu-id="d09c6-174">2 - Causes user fatigue due to unnatural position</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="d09c6-175">![Sopra le dita](images/AboveFingers.gif)</span><span class="sxs-lookup"><span data-stu-id="d09c6-175">![Above fingers](images/AboveFingers.gif)</span></span><br>
        <span data-ttu-id="d09c6-176">**Sopra le dita**</span><span class="sxs-lookup"><span data-stu-id="d09c6-176">**Above fingers**</span></span><br>
        <span data-ttu-id="d09c6-177">affaticamento a 1 mano dovuto alla conservazione della mano da molto tempo</span><span class="sxs-lookup"><span data-stu-id="d09c6-177">1 - Hand fatigue due to holding out hand for a long time</span></span><br>
        <span data-ttu-id="d09c6-178">problemi di rilevamento a due mani sull'indice e le dita centrali</span><span class="sxs-lookup"><span data-stu-id="d09c6-178">2 - Hand tracking issues on index and middle fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="d09c6-179">![Sopra il centro Palm](images/handCenter.gif)</span><span class="sxs-lookup"><span data-stu-id="d09c6-179">![Above center palm](images/handCenter.gif)</span></span><br>
        <span data-ttu-id="d09c6-180">**Sopra-centro Palm**</span><span class="sxs-lookup"><span data-stu-id="d09c6-180">**Above-center palm**</span></span><br>
        <span data-ttu-id="d09c6-181">problemi di rilevamento a una mano dovuti a mani sovrapposte</span><span class="sxs-lookup"><span data-stu-id="d09c6-181">1 - Hand tracking issues due to overlapping hands</span></span><br>
        <span data-ttu-id="d09c6-182">affaticamento a due mani a causa del tempo di attesa lungo per interagire con i menu</span><span class="sxs-lookup"><span data-stu-id="d09c6-182">2 - Hand fatigue due to holding hands for long time in order to interact with menus</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="d09c6-183">![Parte superiore ](images/TopFingerTip.gif) della parte superiore **della mano**</span><span class="sxs-lookup"><span data-stu-id="d09c6-183">![Top Fingertip](images/TopFingerTip.gif) **Top fingertip**</span></span><br>
        <span data-ttu-id="d09c6-184">problemi di rilevamento a una mano</span><span class="sxs-lookup"><span data-stu-id="d09c6-184">1 - Hand tracking issues</span></span><br>
        <span data-ttu-id="d09c6-185">un affaticamento a 2 mano da tenere sotto la postura normale</span><span class="sxs-lookup"><span data-stu-id="d09c6-185">2 - Hand fatigue from holding hand above normal posture</span></span><br>
        <span data-ttu-id="d09c6-186">3-problemi durante la pressione di pulsanti con altre dita per errore a causa dello spazio limitato tra le dita</span><span class="sxs-lookup"><span data-stu-id="d09c6-186">3 - Issues pressing buttons with other fingers by accident due to limited space between fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="d09c6-187">![Back of the ARM](images/BackOfTheArm.gif)</span><span class="sxs-lookup"><span data-stu-id="d09c6-187">![Back of the Arm](images/BackOfTheArm.gif)</span></span><br>
        <span data-ttu-id="d09c6-188">**Back of the ARM**</span><span class="sxs-lookup"><span data-stu-id="d09c6-188">**Back of the arm**</span></span><br>
        <span data-ttu-id="d09c6-189">1-è possibile attivare il pulsante Home per errore</span><span class="sxs-lookup"><span data-stu-id="d09c6-189">1 - Can trigger home button by accident</span></span><br>
        <span data-ttu-id="d09c6-190">2-posizione naturale o comoda</span><span class="sxs-lookup"><span data-stu-id="d09c6-190">2 - Not a natural or comfortable position</span></span>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="d09c6-191">Menu a mano in MRTK (Mixed Reality Toolkit) per Unity</span><span class="sxs-lookup"><span data-stu-id="d09c6-191">Hand menu in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="d09c6-192">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** fornisce gli script e le scene di esempio per il menu a mano.</span><span class="sxs-lookup"><span data-stu-id="d09c6-192">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and example scenes for the hand menu.</span></span> <span data-ttu-id="d09c6-193">Lo script del Risolutore HandConstraintPalmUp consente di associare qualsiasi oggetto a mani con diverse opzioni configurabili.</span><span class="sxs-lookup"><span data-stu-id="d09c6-193">The HandConstraintPalmUp solver script allows you to attach any objects to the hands with various configurable options.</span></span> <span data-ttu-id="d09c6-194">Gli esempi di menu della mano di MRTK includono opzioni utili, ad esempio il requisito della palma piatta e lo sguardo per impedire l'attivazione falsa.</span><span class="sxs-lookup"><span data-stu-id="d09c6-194">MRTK's hand menu examples include useful options such as flat palm and gaze requirement for preventing false activation.</span></span>

* [<span data-ttu-id="d09c6-195">Documenti menu a mano</span><span class="sxs-lookup"><span data-stu-id="d09c6-195">Hand Menu Documentations</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html)
* [<span data-ttu-id="d09c6-196">Scena di esempio del menu a mano</span><span class="sxs-lookup"><span data-stu-id="d09c6-196">Hand Menu Example Scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Assets/MRTK/Examples/Demos/HandTracking/Scenes/HandMenuExamples.unity)

<span data-ttu-id="d09c6-197">È possibile provare esempi di menu a mano in HoloLens 2 con l'App Hub esempi di MRTK.</span><span class="sxs-lookup"><span data-stu-id="d09c6-197">You can try hand menu examples in HoloLens 2 with MRTK Examples Hub app.</span></span> 
* [<span data-ttu-id="d09c6-198">Scena menu a mano nell'hub esempi MRTK</span><span class="sxs-lookup"><span data-stu-id="d09c6-198">Hand Menu Scene in MRTK Examples Hub</span></span>](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4?activetab=pivot:overviewtab)

<br>

---


## <a name="see-also"></a><span data-ttu-id="d09c6-199">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d09c6-199">See also</span></span>

* [<span data-ttu-id="d09c6-200">Cursori</span><span class="sxs-lookup"><span data-stu-id="d09c6-200">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="d09c6-201">Raggio della mano</span><span class="sxs-lookup"><span data-stu-id="d09c6-201">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="d09c6-202">Button</span><span class="sxs-lookup"><span data-stu-id="d09c6-202">Button</span></span>](button.md)
* [<span data-ttu-id="d09c6-203">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="d09c6-203">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="d09c6-204">Rettangolo di selezione e barra dell'app</span><span class="sxs-lookup"><span data-stu-id="d09c6-204">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="d09c6-205">Manipolazione</span><span class="sxs-lookup"><span data-stu-id="d09c6-205">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="d09c6-206">Menu a mano</span><span class="sxs-lookup"><span data-stu-id="d09c6-206">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="d09c6-207">Menu adiacente</span><span class="sxs-lookup"><span data-stu-id="d09c6-207">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="d09c6-208">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="d09c6-208">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="d09c6-209">Comando vocale</span><span class="sxs-lookup"><span data-stu-id="d09c6-209">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="d09c6-210">Tastiera</span><span class="sxs-lookup"><span data-stu-id="d09c6-210">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="d09c6-211">Descrizione comando</span><span class="sxs-lookup"><span data-stu-id="d09c6-211">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="d09c6-212">Slate</span><span class="sxs-lookup"><span data-stu-id="d09c6-212">Slate</span></span>](slate.md)
* [<span data-ttu-id="d09c6-213">Dispositivo di scorrimento</span><span class="sxs-lookup"><span data-stu-id="d09c6-213">Slider</span></span>](slider.md)
* [<span data-ttu-id="d09c6-214">Shader</span><span class="sxs-lookup"><span data-stu-id="d09c6-214">Shader</span></span>](shader.md)
* [<span data-ttu-id="d09c6-215">Billboarding e tag-along</span><span class="sxs-lookup"><span data-stu-id="d09c6-215">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="d09c6-216">Visualizzazione dello stato</span><span class="sxs-lookup"><span data-stu-id="d09c6-216">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="d09c6-217">Magnetismo di superficie</span><span class="sxs-lookup"><span data-stu-id="d09c6-217">Surface magnetism</span></span>](surface-magnetism.md)

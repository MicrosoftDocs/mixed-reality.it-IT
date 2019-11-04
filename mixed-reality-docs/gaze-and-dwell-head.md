---
title: Puntamento con la testa e attesa
description: Panoramica del modello di input puntamento con la testa e attesa
author: liamartinez
ms.author: liamar
ms.date: 05/13/2019
ms.topic: article
keywords: realtà mista, sguardo fisso, attesa, interazione, progettazione
ms.openlocfilehash: 6d209d3cc91ceecb4b9feef2925f093288c9f8ac
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73439312"
---
# <a name="head-gaze-and-dwell"></a><span data-ttu-id="da142-104">Puntamento con la testa e attesa</span><span class="sxs-lookup"><span data-stu-id="da142-104">Head-gaze and dwell</span></span>

<span data-ttu-id="da142-105">Quando le mani sono occupate con gli attrezzi e le parti, i movimenti possono risultare difficili o addirittura impossibili.</span><span class="sxs-lookup"><span data-stu-id="da142-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span> <span data-ttu-id="da142-106">I comandi vocali, come i movimenti, possono non essere affidabili in determinati contesti, ad esempio in ambienti particolarmente rumorosi.</span><span class="sxs-lookup"><span data-stu-id="da142-106">Voice commands, like gestures, can be unreliable in certain contexts, for example under excessively loud conditions.</span></span> <span data-ttu-id="da142-107">Inoltre, l'uso della voce per controllare i computer, nonostante conosca una rapida diffusione, non è ancora una pratica comune ovunque.</span><span class="sxs-lookup"><span data-stu-id="da142-107">Additionally, using voice to control computers isn't universally common, but it certainly is gaining steam!</span></span> <span data-ttu-id="da142-108">Il modello di input puntamento con la testa e attesa offre un meccanismo già familiare e di facilissima gestione per lavorare in HoloLens con la testa sollevata e senza avere bisogno di usare le mani.</span><span class="sxs-lookup"><span data-stu-id="da142-108">Head-gaze and dwell offers the most familiar and easy-to-master mechanism for working heads-up and hands-free on HoloLens.</span></span> <span data-ttu-id="da142-109">Questo modello di input è anche affidabile al 100%, indipendentemente dall'interferenza di possibili rumori o da eventuali obblighi di restare in silenzio nell'ambiente operativo.</span><span class="sxs-lookup"><span data-stu-id="da142-109">Additionally, head-gaze and dwell is 100% reliable independent of noise interference nor silence constraints in the operating environment.</span></span>

## <a name="scenarios"></a><span data-ttu-id="da142-110">Scenari</span><span class="sxs-lookup"><span data-stu-id="da142-110">Scenarios</span></span>

<span data-ttu-id="da142-111">Il punto di vista e la permanenza sono eccellenze negli scenari in cui le mani di una persona sono occupate da altre attività e la voce non è del 100% affidabile o disponibile a causa di vincoli ambientali o sociali.</span><span class="sxs-lookup"><span data-stu-id="da142-111">Head-gaze and dwell excels in scenarios where a person's hands are busy with other tasks, and voice isn't 100% reliable or available due to environmental or social constraints.</span></span> <span data-ttu-id="da142-112">Un buon esempio di questo tipo di situazioni è dato da una persona che indossa un dispositivo HoloLens per la sovrimpressione di informazioni di riferimento mentre ripara il motore di un'automobile.</span><span class="sxs-lookup"><span data-stu-id="da142-112">A good example is a person wearing a HoloLens to overlay reference information while repairing a car engine.</span></span> <span data-ttu-id="da142-113">Le sue mani sono occupate con gli attrezzi o devono sostenere il corpo mentre la persona si protende sul vano motore.</span><span class="sxs-lookup"><span data-stu-id="da142-113">Their hands are busy with tools or supporting their body as they lean into the engine compartment.</span></span> <span data-ttu-id="da142-114">L'autofficina è rumorosa a causa dei colpi e del ronzio costanti degli attrezzi da lavoro, quindi l'uso dei comandi vocali risulterebbe particolarmente difficoltoso.</span><span class="sxs-lookup"><span data-stu-id="da142-114">The garage space is loud, with the constant banging and buzzing of tools, making voice commands difficult.</span></span> <span data-ttu-id="da142-115">Head-sguardi e l'abitazione consentono all'utente che usa HoloLens di esplorare in modo sicuro il materiale di riferimento senza interrompere il flusso di lavoro.</span><span class="sxs-lookup"><span data-stu-id="da142-115">Head-gaze and dwell allows the person using the HoloLens to confidently navigate their reference material without interrupting their workflow.</span></span> 

## <a name="device-support"></a><span data-ttu-id="da142-116">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="da142-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="da142-117"><strong>Modello di input</strong></span><span class="sxs-lookup"><span data-stu-id="da142-117"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="da142-118"><a href="hololens-hardware-details.md"><strong>HoloLens (prima generazione)</strong></a></span><span class="sxs-lookup"><span data-stu-id="da142-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="da142-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="da142-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="da142-120"><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="da142-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="da142-121">Puntamento con la testa e attesa</span><span class="sxs-lookup"><span data-stu-id="da142-121">Head-gaze and dwell</span></span></td>
        <td><span data-ttu-id="da142-122">✔️ Consigliata</span><span class="sxs-lookup"><span data-stu-id="da142-122">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="da142-123">✔️ Consigliata</span><span class="sxs-lookup"><span data-stu-id="da142-123">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="da142-124">✔️ Consigliata</span><span class="sxs-lookup"><span data-stu-id="da142-124">✔️ Recommended</span></span></td>
    </tr>
</table>


## <a name="design-principles"></a><span data-ttu-id="da142-125">Principi di progettazione</span><span class="sxs-lookup"><span data-stu-id="da142-125">Design principles</span></span>

<span data-ttu-id="da142-126">**Evitare di "guardare come un'arma"**</span><span class="sxs-lookup"><span data-stu-id="da142-126">**Avoid "Gaze as a weapon"**</span></span>

<span data-ttu-id="da142-127">Il puntamento con la testa e l'attesa richiedono un feedback visivo intuitivo, ma una mole eccessiva di feedback può produrre ansia.</span><span class="sxs-lookup"><span data-stu-id="da142-127">Head-gaze and dwell requires visual feedback to be intuitive, but too much feedback can induce anxiety.</span></span> <span data-ttu-id="da142-128">Il feedback deve aiutare l'utente a capire cosa sta puntando, ma non selezionare automaticamente una destinazione contrariamente alla sua intenzione.</span><span class="sxs-lookup"><span data-stu-id="da142-128">The feedback should help a user know what they're targeting, but not auto-select it against their intent.</span></span> <span data-ttu-id="da142-129">Per leggere un testo, le icone e le etichette servono più tempo e più attenzione, quindi considera questo aspetto per dare alla persona modo di assorbire le informazioni prima di effettuare la selezione.</span><span class="sxs-lookup"><span data-stu-id="da142-129">Reading text, icons, and labels requires extra consideration to provide a person room to absorb the information before selecting.</span></span>
    
<span data-ttu-id="da142-130">**Cerca velocità di ricciolo**</span><span class="sxs-lookup"><span data-stu-id="da142-130">**Seek Goldilocks speed**</span></span>
    
<span data-ttu-id="da142-131">Le interazioni di attesa possono avere timer diversi in base all'impatto sulla navigazione: le funzioni usate con maggiore frequenza in genere traggono vantaggio da tempi di riempimento più ridotti, mentre le funzioni più consequenziali possono trarre vantaggio da tempi di riempimento più lunghi.</span><span class="sxs-lookup"><span data-stu-id="da142-131">Dwell interactions can have different timers based on impact of navigation - more frequently used functions will generally benefit from faster fill times, while more consequential functions may benefit from longer fill times.</span></span> <span data-ttu-id="da142-132">Quando viene usato un effetto di riempimento per mostrare questi timer, le curve di animazione del colore di riempimento possono indurre positivamente la sensazione che i tempi di riempimento siano più rapidi.</span><span class="sxs-lookup"><span data-stu-id="da142-132">When using a fill-effect to show these timers, animation curves of the fill color can positively influence a feeling of faster fill times.</span></span> <span data-ttu-id="da142-133">Considera questi aspetti per consentire all'utente di prendere le sue decisioni scegliendo override della velocità di riempimento alta/media/bassa.</span><span class="sxs-lookup"><span data-stu-id="da142-133">Consideration should be taken to enable user decision from fast/medium/slow fill speed overrides.</span></span>
    
<span data-ttu-id="da142-134">**Pronunciare no-no per l'effetto yo-yo**</span><span class="sxs-lookup"><span data-stu-id="da142-134">**Say no-no to yo-yo effect**</span></span>

<span data-ttu-id="da142-135">L'effetto yo-yo è uno scomodo andamento del movimento della testa che può verificarsi quando la posizione del contenuto e dei controlli per il puntamento con la testa e l'attesa obbligano gli utenti a guardare ripetutamente in alto e in basso.</span><span class="sxs-lookup"><span data-stu-id="da142-135">The yo-yo effect is an uncomfortable pattern of head movement that can emerge when the placement of content and head-gaze and dwell controls forces people to constantly look up and down repeatedly.</span></span> <span data-ttu-id="da142-136">Ad esempio, un elenco di spostamento con il pulsante di selezione e il pulsante di disattivazione nella parte inferiore induce un ciclo di ricerca verso il basso, Cerca i risultati, Cerca giù e così via. Questo modello risultante è scomodo e deve essere evitato posizionando i controlli di navigazione in una posizione centralizzata che richiede meno avanti e indietro.</span><span class="sxs-lookup"><span data-stu-id="da142-136">For example, a list nav with the head-gaze and dwell button at the bottom induces a loop of - look down to dwell, look up at results, look down to dwell, etc. This resulting pattern is uncomfortable and should be avoided by placing navigation controls in a centralized location that requires less back-and-forth.</span></span> <span data-ttu-id="da142-137">Il posizionamento dei pulsanti di attesa in base al loro effetto diventa un fattore importante per il comfort dell'utente.</span><span class="sxs-lookup"><span data-stu-id="da142-137">Placement of dwell buttons relative to their effects becomes important for comfort.</span></span>

<br>

---


## <a name="ux-guidelines-and-best-practices"></a><span data-ttu-id="da142-138">Linee guida e procedure consigliate per l'esperienza utente</span><span class="sxs-lookup"><span data-stu-id="da142-138">UX Guidelines and best practices</span></span>

### <a name="target-sizes"></a><span data-ttu-id="da142-139">Dimensioni delle destinazioni</span><span class="sxs-lookup"><span data-stu-id="da142-139">Target sizes</span></span>
  <span data-ttu-id="da142-140">Per essere facilmente accessibili, gli obiettivi di Head-look e di abitazione devono essere sufficientemente grandi da poter essere esaminati in modo semplice e tenere la sede stabile sulla destinazione per il periodo di tempo previsto.</span><span class="sxs-lookup"><span data-stu-id="da142-140">To be easily accessible, head-gaze and dwell targets need to be large enough to comfortably look at, and hold one's head stable on the target for the prescribed time.</span></span> <span data-ttu-id="da142-141">Per ottenere un'esperienza ottimale, è consigliabile utilizzare una dimensione minima di 2 gradi.</span><span class="sxs-lookup"><span data-stu-id="da142-141">We recommend a minimum target size of 2 degrees to achieve the most comfortable experience.</span></span> 

### <a name="visual-feedback"></a><span data-ttu-id="da142-142">Feedback visivo</span><span class="sxs-lookup"><span data-stu-id="da142-142">Visual feedback</span></span>

<span data-ttu-id="da142-143">Quando usi un riempimento radiale per rappresentare il timer di attesa, inizia dalla parte centrale del pulsante.</span><span class="sxs-lookup"><span data-stu-id="da142-143">When using a radial fill to represent the dwell timer, start from the center of button.</span></span> <span data-ttu-id="da142-144">Una risposta uniforme genera meno confusione di tante indicazioni diverse sui vari pulsanti.</span><span class="sxs-lookup"><span data-stu-id="da142-144">A consistent response is less confusing than all different directions on different buttons.</span></span> 

  * <span data-ttu-id="da142-145">È tuttavia possibile contravvenire a questa regola per le interazioni direzionali, ad esempio per la navigazione verso l'alto, il basso, a sinistra, a destra e così via.</span><span class="sxs-lookup"><span data-stu-id="da142-145">This rule can be broken though for directional interactions (e.g., nav up/down/left/right, etc.).</span></span> <span data-ttu-id="da142-146">Ad esempio, Microsoft Dynamics 365 Guides fa un'eccezione per AVANTI/INDIETRO, trattandosi di riempimenti sinistra-destra.</span><span class="sxs-lookup"><span data-stu-id="da142-146">For example, Microsoft Dynamics 365 Guides makes an exception on NEXT/BACK being left right fills.</span></span>
  * <span data-ttu-id="da142-147">Considera la possibilità di invertire il riempimento radiale dall'esterno per scenari come quelli di disattivazione di un pulsante.</span><span class="sxs-lookup"><span data-stu-id="da142-147">Consider inverting radial fill from outside, for scenarios like toggling a button off.</span></span> <span data-ttu-id="da142-148">La sensazione opposta di premere un pulsante è un effetto visivo piacevole da mantenere.</span><span class="sxs-lookup"><span data-stu-id="da142-148">The inverse feeling of pushing a button is a nice visual pattern to maintain.</span></span> 

### <a name="progressive-disclosure"></a><span data-ttu-id="da142-149">Rivelazione progressiva</span><span class="sxs-lookup"><span data-stu-id="da142-149">Progressive disclosure</span></span>

<span data-ttu-id="da142-150">Con la rilevazione progressiva vengono mostrati solo i dettagli rilevanti in ciascuna fase di un'interazione.</span><span class="sxs-lookup"><span data-stu-id="da142-150">Progressive disclosure means only showing as much detail as is relevant at each stage of an interaction.</span></span> <span data-ttu-id="da142-151">Nel caso dell'attesa, ciò significa rivelare la destinazione con l'evidenziazione, ad esempio in un controllo elenco.</span><span class="sxs-lookup"><span data-stu-id="da142-151">For dwell, that means the dwell target is revealed on highlight (e.g., in a list control).</span></span>

 ### <a name="oversized-targets"></a><span data-ttu-id="da142-152">Destinazioni di dimensioni eccessive</span><span class="sxs-lookup"><span data-stu-id="da142-152">Oversized targets</span></span>
<span data-ttu-id="da142-153">L'area di attesa può essere più grande dell'icona inattiva per agevolare l'uso, come nel caso del pulsante Indietro in Microsoft Dynamics 365 Guides.</span><span class="sxs-lookup"><span data-stu-id="da142-153">Dwell region can be larger than inactive icon to make it easier to use, like the Back button in Microsoft Dynamics 365 Guides.</span></span>

### <a name="prevent-flickering-with-delayed-feedback"></a><span data-ttu-id="da142-154">Evitare lo sfarfallio con un feedback ritardato</span><span class="sxs-lookup"><span data-stu-id="da142-154">Prevent flickering with delayed feedback</span></span>
<span data-ttu-id="da142-155">Aggiungi un breve ritardo prima di avviare il feedback visivo per evitare lo sfarfallio quando qualcuno passa su una destinazione di attesa.</span><span class="sxs-lookup"><span data-stu-id="da142-155">Use a short delay before starting visual feedback to avoid flickering when someone passes over a dwell target.</span></span>
* <span data-ttu-id="da142-156">Per i pulsanti che interagiscono con frequenza frequente, è molto breve, in modo che l'applicazione ritenga riattiva.</span><span class="sxs-lookup"><span data-stu-id="da142-156">For buttons interacted with frequently, keep the delay very short so the application feels reactive.</span></span>
* <span data-ttu-id="da142-157">Per i pulsanti che interagiscono con una frequenza infrequente, un ritardo più lungo può essere appropriato per evitare l'interfaccia.</span><span class="sxs-lookup"><span data-stu-id="da142-157">For buttons that are interacted with infrequently, a longer delay can be appropriate to avoid the interface feeling twitchy.</span></span>


<br>

---

## <a name="ui-patterns"></a><span data-ttu-id="da142-158">Modelli per l'interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="da142-158">UI patterns</span></span>

### <a name="high-frequency-buttons"></a><span data-ttu-id="da142-159">Pulsanti usati frequentemente</span><span class="sxs-lookup"><span data-stu-id="da142-159">High frequency buttons</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="da142-160">I pulsanti ad alta frequenza sono pulsanti usati comunemente in un'applicazione.</span><span class="sxs-lookup"><span data-stu-id="da142-160">High frequency buttons are buttons that are used commonly throughout an application.</span></span> <span data-ttu-id="da142-161">Un buon esempio è rappresentato dai pulsanti Avanti e Indietro in Microsoft Dynamics 365 Guides.</span><span class="sxs-lookup"><span data-stu-id="da142-161">A good example of these are the next and back buttons in Microsoft Dynamics 365 Guides.</span></span><br>
        <br>
        <span data-ttu-id="da142-162">**Raccomandazioni**</span><span class="sxs-lookup"><span data-stu-id="da142-162">**Recommendations**</span></span><br>
  * <span data-ttu-id="da142-163">I pulsanti ad alta frequenza dovrebbero essere di grandi dimensioni, più facili da raggiungere con l'Head-sguardi</span><span class="sxs-lookup"><span data-stu-id="da142-163">High frequency buttons should be large, easier to hit with head-gaze</span></span>
  * <span data-ttu-id="da142-164">Rimanere vicino all'altezza degli occhi per evitare la pressione ergonomica.</span><span class="sxs-lookup"><span data-stu-id="da142-164">Stay near eye height to avoid ergonomic straining.</span></span><br>
        <br>
<span data-ttu-id="da142-165">*Immagine: pulsante Avanti per Microsoft Dynamics 365 guide*</span><span class="sxs-lookup"><span data-stu-id="da142-165">*Image: Microsoft Dynamics 365 Guides next button*</span></span>
    :::column-end:::
        :::column:::
       ![Pulsante Avanti per Microsoft Dynamics 365 guide](images/GuideNextButton.png)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="low-frequency-buttons"></a><span data-ttu-id="da142-167">Pulsanti usati raramente</span><span class="sxs-lookup"><span data-stu-id="da142-167">Low frequency buttons</span></span>
<span data-ttu-id="da142-168">I pulsanti usati raramente sono pulsanti con cui si interagisce con meno regolarità all'interno dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="da142-168">Low frequency buttons are buttons that are not interacted with as regularly throughout the application.</span></span> <span data-ttu-id="da142-169">Un buon esempio è rappresentato da un pulsante che consente di accedere al menu delle impostazioni o di cancellare tutto il lavoro svolto.</span><span class="sxs-lookup"><span data-stu-id="da142-169">A good example might be a button to access the settings menu, or a button to clear all work.</span></span>

* <span data-ttu-id="da142-170">Prova a posizionare questi pulsanti in modo che non intralcino i percorsi di puntamento con la testa di uso frequente per evitare che vengano attivati accidentalmente.</span><span class="sxs-lookup"><span data-stu-id="da142-170">Try to keep these buttons out of the way of frequent head-gaze paths to avoid accidental activation.</span></span> 

<br>

---

### <a name="confirmations"></a><span data-ttu-id="da142-171">Conferme</span><span class="sxs-lookup"><span data-stu-id="da142-171">Confirmations</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="da142-172">Quando un'azione ha un impatto significativo, ad esempio perché determina un addebito di denaro, l'eliminazione del lavoro svolto o l'avvio di un lungo processo, è utile chiedere alla persona di confermare che intendesse effettivamente selezionare un determinato pulsante.</span><span class="sxs-lookup"><span data-stu-id="da142-172">When an action has significant impact, like charging money, deleting work, or starting a long process, it is useful to confirm that a person meant to select a button.</span></span><br>
        <br>
        <span data-ttu-id="da142-173">**Raccomandazioni**</span><span class="sxs-lookup"><span data-stu-id="da142-173">**Recommendations**</span></span><br>
  * <span data-ttu-id="da142-174">Mostra l'evidenziazione della selezione sul pulsante principale.</span><span class="sxs-lookup"><span data-stu-id="da142-174">Show selection highlight on main button.</span></span>
  * <span data-ttu-id="da142-175">Rivela la destinazione dell'attesa contemporaneamente all'evidenziazione della selezione.</span><span class="sxs-lookup"><span data-stu-id="da142-175">Reveal dwell target at same time as selection highlight.</span></span>
  * <span data-ttu-id="da142-176">Per il pulsante secondario, rivela la destinazione dell'attesa al momento del puntamento con la testa.</span><span class="sxs-lookup"><span data-stu-id="da142-176">For the secondary button, reveal the dwell target on head-gaze.</span></span><br>
        <br>
<span data-ttu-id="da142-177">*Immagine: finestra di conferma della Guida di Microsoft Dynamics 365*</span><span class="sxs-lookup"><span data-stu-id="da142-177">*Image: Microsoft Dynamics 365 Guides confirmation dialog*</span></span>
    :::column-end:::
        :::column:::
       ![Finestra di conferma della Guida di Microsoft Dynamics 365](images/GuidesConfirmation.png)<br>
    :::column-end:::
:::row-end:::
        
<br>

---

### <a name="toggle-buttons"></a><span data-ttu-id="da142-179">Interruttori</span><span class="sxs-lookup"><span data-stu-id="da142-179">Toggle buttons</span></span>
<span data-ttu-id="da142-180">Per funzionare correttamente, gli interruttori necessitano di una logica più sottile.</span><span class="sxs-lookup"><span data-stu-id="da142-180">Toggle buttons require some nuanced logic to work properly.</span></span> <span data-ttu-id="da142-181">Quando una persona si sofferma (ovvero resta in attesa) su un interruttore e lo attiva, deve uscire dal pulsante e quindi tornare per riavviare la logica di attesa.</span><span class="sxs-lookup"><span data-stu-id="da142-181">When a person dwells on a toggle button and actives it, they need to exit the button and then return to restart the dwell logic.</span></span> <span data-ttu-id="da142-182">È importante che i pulsanti attivabili o disattivabili come interruttori abbiano uno stato attivo chiaramente diverso dallo stato inattivo.</span><span class="sxs-lookup"><span data-stu-id="da142-182">It is important that togglable buttons have a clear active versus inactive state.</span></span> 

<br>

---

### <a name="list-views"></a><span data-ttu-id="da142-183">Visualizzazioni elenco</span><span class="sxs-lookup"><span data-stu-id="da142-183">List views</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="da142-184">Le visualizzazioni elenco presentano una particolare sfida per l'input di punta e di residenza.</span><span class="sxs-lookup"><span data-stu-id="da142-184">List views present a particular challenge for head-gaze and dwell input.</span></span> <span data-ttu-id="da142-185">Gli utenti devono poter analizzare il contenuto senza avere la sensazione di doversi muovere con cautela tra le destinazioni di attesa.</span><span class="sxs-lookup"><span data-stu-id="da142-185">People need to be able to scan the content without feeling like that have to tiptoe around the dwell targets.</span></span><br>
        <br>
<span data-ttu-id="da142-186">**Raccomandazioni**</span><span class="sxs-lookup"><span data-stu-id="da142-186">**Recommendations**</span></span><br>
  * <span data-ttu-id="da142-187">Far evidenziare l'intera riga quando si è a capo, ma non inizia la permanenza, a meno che l'Head-sguardi si trovi nella destinazione di residenza specifica.</span><span class="sxs-lookup"><span data-stu-id="da142-187">Have the entire row highlight when head-gazed but doesn’t begin dwell unless head-gaze is on the specific dwell target.</span></span>
  * <span data-ttu-id="da142-188">Mostra solo la destinazione di residenza quando la riga viene evidenziata in modo da ridurre il rumore visivo.</span><span class="sxs-lookup"><span data-stu-id="da142-188">Only show the dwell target when the row is highlighted to cut down on visual noise.</span></span>
  * <span data-ttu-id="da142-189">Essere chiari e coerenti con la posizione delle destinazioni di residenza.</span><span class="sxs-lookup"><span data-stu-id="da142-189">Be clear and consistent with the position of dwell targets.</span></span>
  * <span data-ttu-id="da142-190">Non mostrare tutte le destinazioni di residenza in una sola volta per evitare l'interfaccia utente ripetitiva.</span><span class="sxs-lookup"><span data-stu-id="da142-190">Don't show all dwell targets at once to avoid repetitive UI.</span></span>
  * <span data-ttu-id="da142-191">Riutilizzare lo stesso modello il più spesso possibile per stabilire la familiarità con l'esperienza utente.</span><span class="sxs-lookup"><span data-stu-id="da142-191">Re-use the same pattern as often as possible to establish UX familiarity.</span></span><br>
        <br>
<span data-ttu-id="da142-192">*Immagine: elenco delle guide di Microsoft Dynamics 365*</span><span class="sxs-lookup"><span data-stu-id="da142-192">*Image: Microsoft Dynamics 365 Guides list*</span></span>
    :::column-end:::
        :::column:::
       ![Elenco delle guide di Microsoft Dynamics 365](images/GuidesListView.png)<br>
    :::column-end:::
:::row-end:::

<br>

---
 
 ## <a name="see-also"></a><span data-ttu-id="da142-194">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="da142-194">See also</span></span>
* [<span data-ttu-id="da142-195">Sguardo e commit</span><span class="sxs-lookup"><span data-stu-id="da142-195">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="da142-196">Manipolazione diretta</span><span class="sxs-lookup"><span data-stu-id="da142-196">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="da142-197">Movimenti pratici</span><span class="sxs-lookup"><span data-stu-id="da142-197">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="da142-198">Hand-point e commit</span><span class="sxs-lookup"><span data-stu-id="da142-198">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="da142-199">Interazioni istintive</span><span class="sxs-lookup"><span data-stu-id="da142-199">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="da142-200">Input vocale</span><span class="sxs-lookup"><span data-stu-id="da142-200">Voice input</span></span>](voice-input.md)

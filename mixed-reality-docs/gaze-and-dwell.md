---
title: Sguardo e permanenza
description: Panoramica del modello di input sguardo e permanenza
author: liamartinez
ms.author: liamar
ms.date: 03/31/2019
ms.topic: article
keywords: Progettare sguardo, permanenza, interazione, realtà mista
ms.openlocfilehash: d99180b6eb278eb6d7bf322c01a1c7cceb7fad1f
ms.sourcegitcommit: a4a53e6772805d89a47588857e3e8fb1fd8d9710
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/09/2019
ms.locfileid: "65469067"
---
# <a name="gaze-and-dwell"></a><span data-ttu-id="27fac-104">Sguardo e permanenza</span><span class="sxs-lookup"><span data-stu-id="27fac-104">Gaze and dwell</span></span>

<span data-ttu-id="27fac-105">Quando le mani sono occupate con gli strumenti e le parti, i movimenti possono essere difficile o impossibile.</span><span class="sxs-lookup"><span data-stu-id="27fac-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span>  <span data-ttu-id="27fac-106">I comandi vocali, come movimento, è possibile base non è affidabili, ad esempio in condizioni eccessivamente elevate.</span><span class="sxs-lookup"><span data-stu-id="27fac-106">Voice commands, like gesture, can be situationally unreliable, for example under excessively loud conditions.</span></span>  <span data-ttu-id="27fac-107">Inoltre, l'uso di voce, al computer di controllo non è ancora un'interazione di "Mainstream", ma certamente sta per essere steam!</span><span class="sxs-lookup"><span data-stu-id="27fac-107">Additionally, using voice to control computers isn't a mainstream interaction yet, but it certainly is gaining steam!</span></span>  <span data-ttu-id="27fac-108">Permanenza sguardo offre il meccanismo più familiare e facile master per Heads-up lavoro mani libere su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="27fac-108">Gaze dwell offers the most familiar and easy-to-master mechanism for working heads-up hands-free on HoloLens.</span></span>  <span data-ttu-id="27fac-109">Inoltre, permanenza sguardo è 100% affidabile indipendente dai vincoli rumore di interferenze né inattività nell'ambiente operativo.</span><span class="sxs-lookup"><span data-stu-id="27fac-109">Additionally, gaze dwell is 100% reliable independent of noise interference nor silence constraints in the operating environment.</span></span>

## <a name="goals"></a><span data-ttu-id="27fac-110">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="27fac-110">Goals</span></span>

<span data-ttu-id="27fac-111">Forniscono un meccanismo per le interazioni completo invisibile all'utente, senza usare vocali.</span><span class="sxs-lookup"><span data-stu-id="27fac-111">Provide a mechanism for full hands-free interactions, without using voice.</span></span>

## <a name="design-principles"></a><span data-ttu-id="27fac-112">Principi di progettazione</span><span class="sxs-lookup"><span data-stu-id="27fac-112">Design principles</span></span>

1. <span data-ttu-id="27fac-113">Sguardo non è un'arma</span><span class="sxs-lookup"><span data-stu-id="27fac-113">Gaze is not a weapon</span></span>
    
    <span data-ttu-id="27fac-114">Sguardo richiede indicazioni visive per l'interazione intuitiva, ma una quantità eccessiva commenti e suggerimenti possono indurre anxiety.</span><span class="sxs-lookup"><span data-stu-id="27fac-114">Gaze requires visual feedback for intuitive interaction, but too much feedback can induce anxiety.</span></span> <span data-ttu-id="27fac-115">I commenti e suggerimenti dovrebbero aiutare un utente di sapere cosa destinazione, ma non auto-select per il loro scopo.</span><span class="sxs-lookup"><span data-stu-id="27fac-115">The feedback should help a user know what they're targeting, but not auto-select against their intent.</span></span> <span data-ttu-id="27fac-116">Lettura di testo richiede considerazioni aggiuntive per creare un utente di spazio per assorbire le informazioni prima di selezionare.</span><span class="sxs-lookup"><span data-stu-id="27fac-116">Reading text requires extra consideration to provide a user room to absorb the info before selecting.</span></span>
    
2. <span data-ttu-id="27fac-117">Velocità di Riccioli d'oro di ricerca</span><span class="sxs-lookup"><span data-stu-id="27fac-117">Seek Goldilocks speed</span></span>
    
    <span data-ttu-id="27fac-118">Il riempimento di permanenza può avere diversi timer base all'impatto di navigazione: funzioni più utilizzate in genere trarranno vantaggio da tempi di riempimento, mentre le funzioni più CONSEQUENZIALI possono trarre vantaggio da tempi più lunghi di riempimento.</span><span class="sxs-lookup"><span data-stu-id="27fac-118">The dwell fill can have different timers based on impact of navigation - more frequently used functions will generally benefit from faster fill times, while more consequential functions may benefit from longer fill times.</span></span> <span data-ttu-id="27fac-119">Curve di animazione del colore di riempimento possono influire positivamente un sentimento di tempi di riempimento.</span><span class="sxs-lookup"><span data-stu-id="27fac-119">Animation curves of the fill color can positively influence a feeling of faster fill times.</span></span> <span data-ttu-id="27fac-120">Considerazione da eseguire per abilitare la decisione di utente da fast/Media/lente compilare le sostituzioni di velocità.</span><span class="sxs-lookup"><span data-stu-id="27fac-120">Consideration should be taken to enable user decision from fast/medium/slow fill speed overrides.</span></span>
    
3. <span data-ttu-id="27fac-121">Ad esempio no-no effetto yo-yo</span><span class="sxs-lookup"><span data-stu-id="27fac-121">Say no-no to yo-yo effect</span></span>

    <span data-ttu-id="27fac-122">L'effetto di yo-yo (noto anche come "sera in the Roxbury") è uno schema bancario che è possibile che vengano da determinati posizionamento del contenuto e i controlli basati su sguardo.</span><span class="sxs-lookup"><span data-stu-id="27fac-122">The yo-yo effect (also known as "Night at the Roxbury") is an uncomfortable pattern that can emerge from certain  placement of content and gaze-based controls.</span></span> <span data-ttu-id="27fac-123">Barra di spostamento a un elenco con il pulsante riempimento nella parte inferiore, ad esempio, provoca un ciclo di - aspetto verso il basso permanenza, esaminare i risultati, uno sguardo a permanenza e così via. Questo modello risulta è spiacevole e deve essere evitato, inserendo i controlli di navigazione in una posizione centralizzata che richiede meno avanti e indietro.</span><span class="sxs-lookup"><span data-stu-id="27fac-123">For example, a list nav with the fill button at the bottom induces a loop of - look down to dwell, look up at results, look down to dwell, etc. This resulting pattern is uncomfortable and should be avoided by placing navigation controls in a centralized location that requires less back-and-forth.</span></span> <span data-ttu-id="27fac-124">Posizione di sosta pulsanti rispetto alla loro effetti diventa importante per comodità.</span><span class="sxs-lookup"><span data-stu-id="27fac-124">Placement of dwell buttons relative to their effects becomes important for comfort.</span></span>

## <a name="ui-patterns"></a><span data-ttu-id="27fac-125">Modelli dell'interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="27fac-125">UI patterns</span></span>

### <a name="high-frequency-buttons"></a><span data-ttu-id="27fac-126">Pulsanti ad alta frequenza</span><span class="sxs-lookup"><span data-stu-id="27fac-126">High frequency buttons</span></span>
    
* <span data-ttu-id="27fac-127">Pulsanti Avanti/Indietro</span><span class="sxs-lookup"><span data-stu-id="27fac-127">Next/Back buttons</span></span>
  * <span data-ttu-id="27fac-128">Pre-riempimento di molto breve ritardo (memorizzazione nel buffer lo sfarfallio comparsa)</span><span class="sxs-lookup"><span data-stu-id="27fac-128">Very short delay pre-fill (flyover flicker buffer)</span></span>
  * <span data-ttu-id="27fac-129">Pulsanti di dimensioni maggiori sono più facili da colpire con sguardo</span><span class="sxs-lookup"><span data-stu-id="27fac-129">Larger buttons are easier to hit with gaze</span></span>
  * <span data-ttu-id="27fac-130">Interessante non mantenere gli URL in altezza occhio per interagire in modo che pressione</span><span class="sxs-lookup"><span data-stu-id="27fac-130">Nice to keep these at eye height so no strain to interact</span></span>
  * <span data-ttu-id="27fac-131">Permanenza area può essere maggiore di icona inattiva per renderlo più facile da usare (indietro)</span><span class="sxs-lookup"><span data-stu-id="27fac-131">Dwell region can be larger than inactive icon to make it easier to use (Back)</span></span>

### <a name="low-frequency-buttons"></a><span data-ttu-id="27fac-132">Pulsanti di bassa frequenza</span><span class="sxs-lookup"><span data-stu-id="27fac-132">Low frequency buttons</span></span>
    
* <span data-ttu-id="27fac-133">Attivare il menu impostazioni</span><span class="sxs-lookup"><span data-stu-id="27fac-133">Activate settings menu</span></span>
  * <span data-ttu-id="27fac-134">Ritardare più pre-riempimento OK (memorizzazione nel buffer lo sfarfallio comparsa)</span><span class="sxs-lookup"><span data-stu-id="27fac-134">Longer delay pre-fill okay (flyover flicker buffer)</span></span>
  * <span data-ttu-id="27fac-135">Provare a mantenere questi pulsanti dall'area dei percorsi di cursore frequenti</span><span class="sxs-lookup"><span data-stu-id="27fac-135">Try to keep these buttons out of the way of frequent cursor pathways</span></span>

* <span data-ttu-id="27fac-136">Conferme (ad esempio analisi di flusso, le finestre di dialogo)</span><span class="sxs-lookup"><span data-stu-id="27fac-136">Confirmations (i.e. scan flow, dialogs)</span></span>
  * <span data-ttu-id="27fac-137">Mostra evidenziazione della selezione nel pulsante principale</span><span class="sxs-lookup"><span data-stu-id="27fac-137">Show selection highlight on main button</span></span>
  * <span data-ttu-id="27fac-138">Rivelare destinazione permanenza in contemporanea con evidenziazione della selezione</span><span class="sxs-lookup"><span data-stu-id="27fac-138">Reveal dwell target at same time as selection highlight</span></span>
  * <span data-ttu-id="27fac-139">Usare permanenza che circondano icona per mantenere semplice interfaccia di destinazione</span><span class="sxs-lookup"><span data-stu-id="27fac-139">Use dwell target surrounding icon to keep interface simple</span></span>
  * <span data-ttu-id="27fac-140">Decisione importante, in modo che non attiva l'evidenziazione, rivela permanenza della destinazione per volta incluso</span><span class="sxs-lookup"><span data-stu-id="27fac-140">Important decision, so highlight doesn't activate, reveals dwell target for reconsideration time</span></span>
        
### <a name="toggle-buttons"></a><span data-ttu-id="27fac-141">Interruttori</span><span class="sxs-lookup"><span data-stu-id="27fac-141">Toggle buttons</span></span>

* <span data-ttu-id="27fac-142">Pin</span><span class="sxs-lookup"><span data-stu-id="27fac-142">Pin</span></span>
  * <span data-ttu-id="27fac-143">Cancella attive/inattive dello stato di visualizzazione</span><span class="sxs-lookup"><span data-stu-id="27fac-143">Clear active/inactive visual state</span></span>
  * <span data-ttu-id="27fac-144">Riempimento radiale aiuta l'utente lo stato attivo e offre un corso naturale</span><span class="sxs-lookup"><span data-stu-id="27fac-144">Radial fill helps focus user and provides natural progress</span></span> 

* <span data-ttu-id="27fac-145">Singole impostazioni</span><span class="sxs-lookup"><span data-stu-id="27fac-145">Individual settings</span></span>
  * <span data-ttu-id="27fac-146">Stati di deselezionare attive/inattive</span><span class="sxs-lookup"><span data-stu-id="27fac-146">Clear active/inactive states</span></span>
  * <span data-ttu-id="27fac-147">Permanenza destinazioni tutto sull'icona circostante a sinistra</span><span class="sxs-lookup"><span data-stu-id="27fac-147">Dwell targets all on left surrounding icon</span></span>
  * <span data-ttu-id="27fac-148">Permanenza ha come destinazione vengono visualizzati solo quando selezione evidenziare attivo</span><span class="sxs-lookup"><span data-stu-id="27fac-148">Dwell targets only show up when selection highlight active</span></span>
  * <span data-ttu-id="27fac-149">"Il caso di soffermarsi su dispositivo di scorrimento" sul lato destro per le impostazioni di attivazione/disattivazione</span><span class="sxs-lookup"><span data-stu-id="27fac-149">"Dwell on slider" on right side for on/off settings</span></span>

### <a name="list-views"></a><span data-ttu-id="27fac-150">Visualizzazioni elenco</span><span class="sxs-lookup"><span data-stu-id="27fac-150">List views</span></span>

* <span data-ttu-id="27fac-151">Visualizzazione elenco esplorazione - Guida file da aprire</span><span class="sxs-lookup"><span data-stu-id="27fac-151">Browsing list view - guide files to open</span></span>
  * <span data-ttu-id="27fac-152">Cursore Evidenzia riga da un punto qualsiasi sulla riga ma non viene avviata permanenza</span><span class="sxs-lookup"><span data-stu-id="27fac-152">Cursor highlights row from anywhere on row but doesn’t begin dwell</span></span>
  * <span data-ttu-id="27fac-153">Quando sono evidenziata righe dal cursore, permanenza della destinazione viene visualizzata a sinistra</span><span class="sxs-lookup"><span data-stu-id="27fac-153">When row is highlighted by cursor, dwell target appears on left</span></span>
  * <span data-ttu-id="27fac-154">Permanenza destinazione sempre un cerchio sul lato sinistro del testo in tutte le visualizzazioni elenco</span><span class="sxs-lookup"><span data-stu-id="27fac-154">Dwell target always a circle on left side of text in all list views</span></span>
  * <span data-ttu-id="27fac-155">Non vengono visualizzati che tutti permanenza destinazioni in una sola volta per evitare ricorrenti dell'interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="27fac-155">Don't show all dwell targets at once to avoid repetitive UI</span></span>
  * <span data-ttu-id="27fac-156">Usare nuovamente lo stesso modello per stabilire la conoscenza dell'esperienza utente</span><span class="sxs-lookup"><span data-stu-id="27fac-156">Re-use the same pattern to establish UX familiarity</span></span>
        
* <span data-ttu-id="27fac-157">Visualizzazione elenco - gerarchia di attività e i passaggi seguenti in una Guida di esplorazione</span><span class="sxs-lookup"><span data-stu-id="27fac-157">Browsing list view - hierarchy of tasks/steps in a guide</span></span>
  * <span data-ttu-id="27fac-158">Permanenza destinazione sempre un cerchio sul lato sinistro del testo</span><span class="sxs-lookup"><span data-stu-id="27fac-158">Dwell target always a circle on left side of text</span></span>
  * <span data-ttu-id="27fac-159">Intuitività di permanenza della compressione/espansione</span><span class="sxs-lookup"><span data-stu-id="27fac-159">Collapse/expand dwell affordance</span></span>
        
* <span data-ttu-id="27fac-160">Visualizzazione elenco esplorazione - modalità</span><span class="sxs-lookup"><span data-stu-id="27fac-160">Browsing list view - mode select</span></span>
  * <span data-ttu-id="27fac-161">Seguire modelli stabiliti in precedenza</span><span class="sxs-lookup"><span data-stu-id="27fac-161">Follow patterns established above</span></span>

### <a name="contextual-buttons"></a><span data-ttu-id="27fac-162">Pulsanti contestuali</span><span class="sxs-lookup"><span data-stu-id="27fac-162">Contextual buttons</span></span>

* <span data-ttu-id="27fac-163">Mostra/Nascondi 3D - Mostra backup in 3D lungo attacco quasi vntana</span><span class="sxs-lookup"><span data-stu-id="27fac-163">Show/Hide 3D - shows up in 3D along tether near holograms</span></span> 
  * <span data-ttu-id="27fac-164">Cancella attive/inattive dello stato di visualizzazione</span><span class="sxs-lookup"><span data-stu-id="27fac-164">Clear active/inactive visual state</span></span>

### <a name="pivots"></a><span data-ttu-id="27fac-165">Pivot</span><span class="sxs-lookup"><span data-stu-id="27fac-165">Pivots</span></span>

* <span data-ttu-id="27fac-166">Elenco di guide recenti/All</span><span class="sxs-lookup"><span data-stu-id="27fac-166">Recent/All guides list</span></span>
  * <span data-ttu-id="27fac-167">Compilare l'intuitività dell'interfaccia utente che rimane per indicare qual è la scheda è attiva</span><span class="sxs-lookup"><span data-stu-id="27fac-167">Fill the UI affordance that remains to indicate which tab is active</span></span>
  * <span data-ttu-id="27fac-168">Per una singola parola breve pivot, abbiamo scelto di rinunciare il criterio di permanenza di destinazione</span><span class="sxs-lookup"><span data-stu-id="27fac-168">For short single word pivots, we elected to forego the dwell target pattern</span></span>
  * <span data-ttu-id="27fac-169">È preferita interfaccia semplificata tramite un altro cerchio 2 destinazioni e una più ampio dell'interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="27fac-169">We favored the simplified interface over another 2 circle targets and a wider UI</span></span>
  * <span data-ttu-id="27fac-170">In questo caso, le parole sono sufficientemente breve che un ritardo fornisce sufficiente comfort prima del riempimento</span><span class="sxs-lookup"><span data-stu-id="27fac-170">In our case, the words are short enough that a delay provides enough comfort before filling</span></span>


## <a name="ux-guidelines-and-best-practices"></a><span data-ttu-id="27fac-171">Linee guida dell'esperienza utente e le procedure consigliate</span><span class="sxs-lookup"><span data-stu-id="27fac-171">UX guidelines and best practices</span></span>

### <a name="target-sizes"></a><span data-ttu-id="27fac-172">Dimensioni delle destinazioni</span><span class="sxs-lookup"><span data-stu-id="27fac-172">Target sizes</span></span>

  * <span data-ttu-id="27fac-173">Dimensioni minime icona PIN: 6cm nello spazio globale in Unity, 30 MRU (30cm @ 2 minuti)</span><span class="sxs-lookup"><span data-stu-id="27fac-173">Pin icon minimum size: 6cm in world space in Unity, 30 MRUs ( 30cm @ 2m)</span></span>
  * <span data-ttu-id="27fac-174">Sono affatto obiettivi "magnetizzati" o "permanenti"?</span><span class="sxs-lookup"><span data-stu-id="27fac-174">Are the targets "magnetized" or "sticky" at all?</span></span> <span data-ttu-id="27fac-175">(vale a dire estasiati anti-aliasing di cursori)</span><span class="sxs-lookup"><span data-stu-id="27fac-175">(i.e. gaze cursor smoothing)</span></span>

### <a name="animation"></a><span data-ttu-id="27fac-176">Animazione</span><span class="sxs-lookup"><span data-stu-id="27fac-176">Animation</span></span>

  * <span data-ttu-id="27fac-177">Ritardo prima della permanenza visual attiva .5sec</span><span class="sxs-lookup"><span data-stu-id="27fac-177">Delay before dwell visual triggers .5sec</span></span>
  * <span data-ttu-id="27fac-178">Durata della permanenza visual 1,2 sec</span><span class="sxs-lookup"><span data-stu-id="27fac-178">Duration of dwell visual 1.2sec</span></span>
  * <span data-ttu-id="27fac-179">Curva su animazione?</span><span class="sxs-lookup"><span data-stu-id="27fac-179">Curve on animation?</span></span>

### <a name="visual-feedback"></a><span data-ttu-id="27fac-180">Feedback visivo</span><span class="sxs-lookup"><span data-stu-id="27fac-180">Visual feedback</span></span>

  * <span data-ttu-id="27fac-181">Riempimento radiale dalla posizione di inizio del cursore sguardo</span><span class="sxs-lookup"><span data-stu-id="27fac-181">Radial fill from gaze cursor start location</span></span>
  * <span data-ttu-id="27fac-182">Riempimento sempre radiale dal centro del pulsante.</span><span class="sxs-lookup"><span data-stu-id="27fac-182">Always radial fill from center of button.</span></span> <span data-ttu-id="27fac-183">Una risposta coerente è meno ambiguo rispetto a tutte le direzioni diverse in diversi pulsanti.</span><span class="sxs-lookup"><span data-stu-id="27fac-183">A consistent response is less confusing than all different directions on different buttons.</span></span> 
    * <span data-ttu-id="27fac-184">Questa regola può essere interrotta anche se per le interazioni direzionale (ad esempio, nav su/giù/sinistra/destra, ecc.).</span><span class="sxs-lookup"><span data-stu-id="27fac-184">This rule can be broken though for directional interactions (e.g., nav up/down/left/right, etc.).</span></span> <span data-ttu-id="27fac-185">Ad esempio, rende Guide un'eccezione in avanti/indietro verrà mantenuto a destra riempie.</span><span class="sxs-lookup"><span data-stu-id="27fac-185">For example, Guides makes an exception on Next/Back being left right fills.</span></span>
    * <span data-ttu-id="27fac-186">Prendere in considerazione l'inversione radiale riempimento dall'esterno (se l'attivazione/disattivazione).</span><span class="sxs-lookup"><span data-stu-id="27fac-186">Consider inverting radial fill from outside (if toggling off).</span></span> <span data-ttu-id="27fac-187">Il sentimento inversa di pressione di un pulsante è un modello visual interessante per mantenere.</span><span class="sxs-lookup"><span data-stu-id="27fac-187">THe inverse feeling of pushing a button is a nice visual pattern to maintain.</span></span> 

### <a name="progressive-disclosure"></a><span data-ttu-id="27fac-188">Presentazione progressiva delle</span><span class="sxs-lookup"><span data-stu-id="27fac-188">Progressive disclosure</span></span>

 * <span data-ttu-id="27fac-189">Presentazione progressiva delle significa che la destinazione di permanenza viene visualizzata in evidenziazione (ad esempio, in un controllo elenco)</span><span class="sxs-lookup"><span data-stu-id="27fac-189">Progressive disclosure means that the dwell target is revealed on highlight (e.g., in a list control)</span></span>
 * <span data-ttu-id="27fac-190">Testo barra evidenziazioni con spotlight rivelano su sguardo ovunque si trovino con testo</span><span class="sxs-lookup"><span data-stu-id="27fac-190">Text bar highlights with spotlight reveal on gaze anywhere on text</span></span>
 * <span data-ttu-id="27fac-191">Sguardo riempimento destinazione vengono visualizzati sempre a sinistra, ma solo per l'elemento di elenco evidenziato</span><span class="sxs-lookup"><span data-stu-id="27fac-191">Gaze fill target appears always on left, but only for the list item which is highlighted</span></span>
 * <span data-ttu-id="27fac-192">Evitare di inserire tutte le destinazioni di permanenza in qualsiasi momento a causa di un aspetto ripetitiva dei cerchi in pila</span><span class="sxs-lookup"><span data-stu-id="27fac-192">Try to avoid having all dwell targets on at all times due to repetitive look of stacked circles</span></span>
 
 ## <a name="see-also"></a><span data-ttu-id="27fac-193">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="27fac-193">See also</span></span>
* [<span data-ttu-id="27fac-194">Manipolazione diretta</span><span class="sxs-lookup"><span data-stu-id="27fac-194">Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="27fac-195">Puntamento e commit</span><span class="sxs-lookup"><span data-stu-id="27fac-195">Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="27fac-196">Concetti fondamentali delle interazioni</span><span class="sxs-lookup"><span data-stu-id="27fac-196">Interaction fundamentals</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="27fac-197">Puntamento con la testa e commit</span><span class="sxs-lookup"><span data-stu-id="27fac-197">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="27fac-198">Sguardo fisso e voce</span><span class="sxs-lookup"><span data-stu-id="27fac-198">Gaze and voice</span></span>](voice-design.md)

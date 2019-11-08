---
title: Interazioni istintive
description: Scopri la filosofia delle interazioni semplici e istintive alla base di tutta la piattaforma di realtà mista.
author: shengkait
ms.author: shentan
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Realtà mista, sguardo fisso, selezione della destinazione con lo sguardo fisso, interazione, progettazione, HoloLens, MMR, multimodale
ms.openlocfilehash: abd82947be08a2f6aecc4462abc34c4674abfb7a
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437981"
---
# <a name="introducing-instinctual-interactions"></a><span data-ttu-id="51c14-104">Introduzione alle interazioni istintive</span><span class="sxs-lookup"><span data-stu-id="51c14-104">Introducing instinctual interactions</span></span>

<span data-ttu-id="51c14-105">La filosofia delle interazioni semplici e istintive è alla base di tutta la piattaforma di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="51c14-105">The philosophy of simple, instinctual interactions is interwoven throughout the mixed reality (MR) platform.</span></span> <span data-ttu-id="51c14-106">Abbiamo adottato tre accorgimenti per consentire ai progettisti e agli sviluppatori di applicazioni di fornire ai clienti interazioni facili e intuitive.</span><span class="sxs-lookup"><span data-stu-id="51c14-106">We've taken three steps to ensure that application designers and developers can provide their customers with easy and intuitive interactions.</span></span> 

<span data-ttu-id="51c14-107">In primo luogo, ci siamo assicurati che i sensori e le tecnologie di input, tra cui il tracciamento oculare e delle mani e l'input in linguaggio naturale, si combinino in perfetti modelli di interazione multimodale.</span><span class="sxs-lookup"><span data-stu-id="51c14-107">First, we've made sure our sensors and input technologies (which includes hand and eye tracking along with natural language input) combine into seamless, multimodal interaction models.</span></span>  
<span data-ttu-id="51c14-108">In base alle nostre ricerche, le attività di progettazione e sviluppo all'interno di un framework multimodale (e non basate su singoli input) sono la chiave di volta per creare esperienze istintive.</span><span class="sxs-lookup"><span data-stu-id="51c14-108">Based on our research, designing and developing within a multimodal framework (and not based on individual inputs) is the key to creating instinctual experiences.</span></span>

<span data-ttu-id="51c14-109">In secondo luogo, constatiamo che molti sviluppatori destinano le loro applicazioni a più dispositivi HoloLens, come HoloLens 2 e HoloLens (prima generazione) oppure HoloLens e VR.</span><span class="sxs-lookup"><span data-stu-id="51c14-109">Second, we recognize that many developers target multiple HoloLens devices, such as HoloLens 2 and HoloLens (1st gen) or HoloLens and VR.</span></span>  
<span data-ttu-id="51c14-110">Abbiamo quindi progettato modelli di interazione in grado di funzionare in tutti i dispositivi, anche se la tecnologia di input varia da uno all'altro.</span><span class="sxs-lookup"><span data-stu-id="51c14-110">So we've designed our interaction models to work across devices, even if the input technology varies on each device.</span></span>  
<span data-ttu-id="51c14-111">Ad esempio, per l'interazione da lontano con un visore VR immersive di Windows dotato di un controller 6DoF e per l'interazione da lontano con un dispositivo HoloLens 2 vengono usati gli stessi inviti e modelli, semplificando lo sviluppo di applicazioni per più dispositivi e assicurando interazioni più naturali con gli utenti.</span><span class="sxs-lookup"><span data-stu-id="51c14-111">For example, far interaction on a Windows Immersive headset with a 6DoF controller and far interaction on a HoloLens 2 both use identical affordances and patterns, making it easy for cross-device application development and providing a natural feel to user interactions.</span></span> 

<span data-ttu-id="51c14-112">Anche se riconosciamo che possono esistere migliaia di interazioni efficaci, coinvolgenti e magiche nella realtà mista, abbiamo constatato che l'utilizzo intenzionale di un unico modello di interazione end-to-end in un'applicazione è il modo migliore per garantire agli utenti risultati ottimali e un'esperienza eccezionale.</span><span class="sxs-lookup"><span data-stu-id="51c14-112">While we recognize that there are thousands of effective, engaging, and magical interactions possible in MR, we've found that intentionally employing a single interaction model end-to-end in an application is the best way to ensure users are successful and have a great experience.</span></span> <span data-ttu-id="51c14-113">A questo scopo, in queste indicazioni relative all'interazione abbiamo incluso tre aspetti:</span><span class="sxs-lookup"><span data-stu-id="51c14-113">To that end, we've included three things in this interaction guidance:</span></span>
* <span data-ttu-id="51c14-114">Materiale specifico incentrato sui tre principali modelli di interazione e sui componenti e schemi necessari per ciascun modello.</span><span class="sxs-lookup"><span data-stu-id="51c14-114">Specific guidance around the three primary interaction models and the components and patterns required for each.</span></span>
* <span data-ttu-id="51c14-115">Istruzioni supplementari su altri vantaggi offerti dalla piattaforma.</span><span class="sxs-lookup"><span data-stu-id="51c14-115">Supplemental guidance about other benefits that our platform provides.</span></span>
* <span data-ttu-id="51c14-116">Indicazioni di carattere generale, utili per selezionare il modello di interazione appropriato per uno scenario di sviluppo specifico.</span><span class="sxs-lookup"><span data-stu-id="51c14-116">General guidance to help select the appropriate interaction model for your development scenario.</span></span>

## <a name="multimodal-interaction-models"></a><span data-ttu-id="51c14-117">Modelli di interazione multimodale</span><span class="sxs-lookup"><span data-stu-id="51c14-117">Multimodal interaction models</span></span>

<span data-ttu-id="51c14-118">In base alle nostre ricerche e al feedback dei clienti, abbiamo scoperto che la maggior parte delle esperienze di realtà mista viene soddisfatta da tre principali modelli di interazione.</span><span class="sxs-lookup"><span data-stu-id="51c14-118">Based on our research and feedback from customers, we've discovered that three primary interaction models suit the majority of mixed reality experiences.</span></span> <span data-ttu-id="51c14-119">Per molti versi, il modello di interazione è lo schema mentale seguito dall'utente per completare un flusso di lavoro.</span><span class="sxs-lookup"><span data-stu-id="51c14-119">In many ways, the interaction model is the user's mental model for how to complete a workflow.</span></span> <span data-ttu-id="51c14-120">Ognuno di questi modelli di interazione è ottimizzato per una serie di esigenze dei clienti ed è comodo, efficiente e applicabile se usato in modo corretto.</span><span class="sxs-lookup"><span data-stu-id="51c14-120">Each of these interaction models is optimized for a set of customer needs and is convenient, powerful, and usable when used correctly.</span></span> 

<span data-ttu-id="51c14-121">La classifica seguente offre una panoramica semplificata.</span><span class="sxs-lookup"><span data-stu-id="51c14-121">The chart below is a simplified overview.</span></span> <span data-ttu-id="51c14-122">Informazioni dettagliate per l'utilizzo di ogni modello di interazione sono collegate a immagini ed esempi di codice nelle pagine seguenti.</span><span class="sxs-lookup"><span data-stu-id="51c14-122">Detailed information for using each interaction model is linked in the pages below with images and code samples.</span></span> 

<br>
<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="51c14-123"><strong>Modello</strong></span><span class="sxs-lookup"><span data-stu-id="51c14-123"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="51c14-124"><strong>Scenari di esempio</strong></span><span class="sxs-lookup"><span data-stu-id="51c14-124"><strong>Example scenarios</strong></span></span></td>
        <td><span data-ttu-id="51c14-125"><strong>Destinatari</strong></span><span class="sxs-lookup"><span data-stu-id="51c14-125"><strong>Fit</strong></span></span></td>
        <td><span data-ttu-id="51c14-126"><strong>Hardware</strong></span><span class="sxs-lookup"><span data-stu-id="51c14-126"><strong>Hardware</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="51c14-127"><a href="hands-and-tools.md">Mani e controller del movimento</a></span><span class="sxs-lookup"><span data-stu-id="51c14-127"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="51c14-128">Esperienze nello spazio 3D, ad esempio layout e progettazione dello spazio, manipolazione di contenuti o simulazione.</span><span class="sxs-lookup"><span data-stu-id="51c14-128">3D spatial experiences, such as spatial layout and design, content manipulation, or simulation.</span></span></td>
        <td><span data-ttu-id="51c14-129">Ideale per i nuovi utenti, in combinazione con comandi vocali, tracciamento oculare o puntamento con la testa.</span><span class="sxs-lookup"><span data-stu-id="51c14-129">Great for new users coupled with voice, eye tracking or head gaze.</span></span> <span data-ttu-id="51c14-130">Curva di apprendimento bassa.</span><span class="sxs-lookup"><span data-stu-id="51c14-130">Low learning curve.</span></span> <span data-ttu-id="51c14-131">Esperienza utente coerente con tracciamento delle mani e controller 6DoF.</span><span class="sxs-lookup"><span data-stu-id="51c14-131">Consistent UX across hand tracking and 6DoF controllers.</span></span></td>
        <td><span data-ttu-id="51c14-132">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="51c14-132">HoloLens 2</span></span><br><span data-ttu-id="51c14-133">Visori VR immersive</span><span class="sxs-lookup"><span data-stu-id="51c14-133">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="51c14-134"><a href="hands-free.md">Mani libere</a></span><span class="sxs-lookup"><span data-stu-id="51c14-134"><a href="hands-free.md">Hands-free</a></span></span></td>
        <td><span data-ttu-id="51c14-135">Esperienze contestuali in cui le mani dell'utente sono occupate, ad esempio apprendimento sul posto e manutenzione.</span><span class="sxs-lookup"><span data-stu-id="51c14-135">Contextual experiences where a user's hands are occupied, such as on-the-job learning and maintenance.</span></span></td>
        <td><span data-ttu-id="51c14-136">È necessario un certo livello di apprendimento.</span><span class="sxs-lookup"><span data-stu-id="51c14-136">Some learning required.</span></span> <span data-ttu-id="51c14-137">Se le mani non sono disponibili, il dispositivo si adatta bene a comandi vocali e linguaggio naturale.</span><span class="sxs-lookup"><span data-stu-id="51c14-137">If hands are unavailable, the device pairs well with voice and natural language.</span></span></td>
        <td><span data-ttu-id="51c14-138">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="51c14-138">HoloLens 2</span></span><br><span data-ttu-id="51c14-139">HoloLens (prima generazione)</span><span class="sxs-lookup"><span data-stu-id="51c14-139">HoloLens (1st gen)</span></span><br><span data-ttu-id="51c14-140">Visori VR immersive</span><span class="sxs-lookup"><span data-stu-id="51c14-140">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="51c14-141"><a href="gaze-and-commit.md">Sguardo e commit</a></span><span class="sxs-lookup"><span data-stu-id="51c14-141"><a href="gaze-and-commit.md">Gaze and commit</a></span></span></td>
        <td><span data-ttu-id="51c14-142">Esperienze di tipo click-through, ad esempio presentazioni 3D e demo.</span><span class="sxs-lookup"><span data-stu-id="51c14-142">Click-through experiences, e.g. 3D presentations, demos.</span></span></td>
        <td><span data-ttu-id="51c14-143">È necessario eseguire il training in dispositivi HMD, non in dispositivi mobili.</span><span class="sxs-lookup"><span data-stu-id="51c14-143">Requires training on HMDs but not on mobile.</span></span> <span data-ttu-id="51c14-144">Ideale per controller accessibili.</span><span class="sxs-lookup"><span data-stu-id="51c14-144">Best for accessible controllers.</span></span> <span data-ttu-id="51c14-145">Ideale per HoloLens (prima generazione).</span><span class="sxs-lookup"><span data-stu-id="51c14-145">Best for HoloLens (1st gen).</span></span></td>
        <td><span data-ttu-id="51c14-146">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="51c14-146">HoloLens 2</span></span><br><span data-ttu-id="51c14-147">HoloLens (prima generazione)</span><span class="sxs-lookup"><span data-stu-id="51c14-147">HoloLens (1st gen)</span></span><br><span data-ttu-id="51c14-148">Visori VR immersive</span><span class="sxs-lookup"><span data-stu-id="51c14-148">Immersive headsets</span></span><br><span data-ttu-id="51c14-149">AR per dispositivi mobili</span><span class="sxs-lookup"><span data-stu-id="51c14-149">Mobile AR</span></span></td>
    </tr>
</table>
<br>

<span data-ttu-id="51c14-150">Per evitare che siano presenti lacune nell'esperienza di interazione dell'utente, è preferibile seguire le indicazioni per un singolo modello dall'inizio alla fine.</span><span class="sxs-lookup"><span data-stu-id="51c14-150">To ensure that there are no gaps in the user interaction experience, it is best to follow the guidance for a single model from beginning to end.</span></span>

<span data-ttu-id="51c14-151">Le sezioni seguenti illustrano la procedura di selezione e implementazione di uno di questi modelli di interazione.</span><span class="sxs-lookup"><span data-stu-id="51c14-151">The sections below walk through the steps for selecting and implementing one of these interaction models.</span></span>  
 
### <a name="by-the-end-of-this-page-you-will-understand-our-guidance-on"></a><span data-ttu-id="51c14-152">Al termine di questa pagina, avrai appreso a:</span><span class="sxs-lookup"><span data-stu-id="51c14-152">By the end of this page, you will understand our guidance on:</span></span>
 
* <span data-ttu-id="51c14-153">Scegliere un modello di interazione per il cliente</span><span class="sxs-lookup"><span data-stu-id="51c14-153">Choosing an interaction model for your customer</span></span>
* <span data-ttu-id="51c14-154">Implementare il modello di interazione</span><span class="sxs-lookup"><span data-stu-id="51c14-154">Implementing the interaction model</span></span>
* <span data-ttu-id="51c14-155">Passare da un modello di interazione all'altro</span><span class="sxs-lookup"><span data-stu-id="51c14-155">Transitioning between interaction models</span></span>
* <span data-ttu-id="51c14-156">Progettare i passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="51c14-156">Design next steps</span></span>


## <a name="choose-an-interaction-model-for-your-customer"></a><span data-ttu-id="51c14-157">Scegliere un modello di interazione per il cliente</span><span class="sxs-lookup"><span data-stu-id="51c14-157">Choose an interaction model for your customer</span></span>

<span data-ttu-id="51c14-158">In genere, gli sviluppatori e gli autori valutano tutti i tipi di interazione che i clienti possono avere.</span><span class="sxs-lookup"><span data-stu-id="51c14-158">Typically, developers and creators have thought through the types of interactions that their customers can have.</span></span> <span data-ttu-id="51c14-159">Per incoraggiare un approccio alla progettazione incentrato sul cliente, è consigliabile attenersi alle indicazioni seguenti per selezionare il modello di interazione ottimizzato per il cliente specifico.</span><span class="sxs-lookup"><span data-stu-id="51c14-159">To encourage a customer-focused approach to design, we recommend the following guidance for selecting the interaction model that's optimized for your customer.</span></span>

### <a name="why-follow-this-guidance"></a><span data-ttu-id="51c14-160">Perché seguire le indicazioni?</span><span class="sxs-lookup"><span data-stu-id="51c14-160">Why follow this guidance?</span></span>

* <span data-ttu-id="51c14-161">I nostri modelli di interazione sono testati in base a criteri obiettivi e soggettivi, ad esempio lo sforzo fisico e cognitivo, l'intuitività e la capacità di apprendimento.</span><span class="sxs-lookup"><span data-stu-id="51c14-161">Our interaction models are tested for objective and subjective criteria, such as physical and cognitive effort, intuitiveness, and learnability.</span></span> 
* <span data-ttu-id="51c14-162">Poiché esistono diversi tipi di interazione, è possibile che anche gli inviti audio/video e il comportamento degli oggetti siano diversi da un modello di interazione all'altro.</span><span class="sxs-lookup"><span data-stu-id="51c14-162">Because interactions differ, visual/audio affordances and object behavior might differ between interaction models.</span></span>  
* <span data-ttu-id="51c14-163">Combinando parti di diversi modelli di interazione si rischia di ottenere inviti concorrenti, ad esempio raggi della mano simultanei e un cursore di puntamento con la testa.</span><span class="sxs-lookup"><span data-stu-id="51c14-163">Combining parts of multiple interaction models creates the risk of competing affordances, such as simultaneous hand rays and a head-gaze cursor.</span></span> <span data-ttu-id="51c14-164">Tutto questo può inondare l'utente di troppe informazioni e confonderlo.</span><span class="sxs-lookup"><span data-stu-id="51c14-164">This can overwhelm and confuse users.</span></span>

<span data-ttu-id="51c14-165">Ecco alcuni esempi di come sono ottimizzati gli inviti e i comportamenti per ogni modello di interazione.</span><span class="sxs-lookup"><span data-stu-id="51c14-165">Here are some examples of how affordances and behaviors are optimized for each interaction model.</span></span> <span data-ttu-id="51c14-166">Notiamo spesso che le domande dei nuovi utenti sono simili, ad esempio: _"Come si può capire se il sistema funziona?"_ , _"Come si può sapere quali azioni si possono eseguire?"_ e _"Come si può sapere se il sistema ha capito quali azioni sono state eseguite?"_</span><span class="sxs-lookup"><span data-stu-id="51c14-166">We often see new users have similar questions, such as _"how do I know the system is working"_, _"how do I know what I can do"_, and _"how do I know if it understood what I just did?"_</span></span>

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="51c14-167"><strong>Modello</strong></span><span class="sxs-lookup"><span data-stu-id="51c14-167"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="51c14-168"><strong>Come si può capire se il sistema funziona?</strong></span><span class="sxs-lookup"><span data-stu-id="51c14-168"><strong>How do I know it's working?</strong></span></span></td>
        <td><span data-ttu-id="51c14-169"><strong>Come si può sapere quali azioni si possono eseguire?</strong></span><span class="sxs-lookup"><span data-stu-id="51c14-169"><strong>How do I know what I can do?</strong></span></span></td>
        <td><span data-ttu-id="51c14-170"><strong>Come si può sapere quali azioni sono state eseguite?</strong></span><span class="sxs-lookup"><span data-stu-id="51c14-170"><strong>How do I know what I just did?</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="51c14-171"><a href="hands-and-tools.md">Mani e controller del movimento</a></span><span class="sxs-lookup"><span data-stu-id="51c14-171"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="51c14-172">Si vede una mesh mano, un invito punta del dito o raggi della mano/controller.</span><span class="sxs-lookup"><span data-stu-id="51c14-172">I see a hand mesh, a fingertip affordance, or hand/controller rays.</span></span></td>
        <td><span data-ttu-id="51c14-173">Si vedono punti di controllo afferrabili o un riquadro delimitatore quando si avvicina la mano a un oggetto.</span><span class="sxs-lookup"><span data-stu-id="51c14-173">I see grabbable handles, or a bounding box appears when my hand is near an object.</span></span></td>
        <td><span data-ttu-id="51c14-174">Si sentono toni udibili e si vedono animazioni al momento di afferrare e rilasciare oggetti.</span><span class="sxs-lookup"><span data-stu-id="51c14-174">I hear audible tones and see animations on grab and release.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="51c14-175"><a href="gaze-and-commit.md">Puntamento con la testa e commit</a></span><span class="sxs-lookup"><span data-stu-id="51c14-175"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="51c14-176">Si vede un cursore al centro del campo visivo.</span><span class="sxs-lookup"><span data-stu-id="51c14-176">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="51c14-177">Il cursore cambia stato quando è posizionato su determinati oggetti.</span><span class="sxs-lookup"><span data-stu-id="51c14-177">The cursor changes state when it's over certain objects.</span></span></td>
        <td><span data-ttu-id="51c14-178">Si vedono conferme visive e/o si sentono conferme udibili quando si intraprendono azioni.</span><span class="sxs-lookup"><span data-stu-id="51c14-178">I see/hear visual and audible confirmations when I take action.</span></span></td>
    </tr>   
    <tr>
        <td><span data-ttu-id="51c14-179"><a href="hands-free.md">Mani libere (puntamento con la testa e attesa)</a></span><span class="sxs-lookup"><span data-stu-id="51c14-179"><a href="hands-free.md">Hands-free (Head-gaze and dwell)</a></span></span></td>
        <td><span data-ttu-id="51c14-180">Si vede un cursore al centro del campo visivo.</span><span class="sxs-lookup"><span data-stu-id="51c14-180">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="51c14-181">Si vede un indicatore di stato quando ci si sofferma su un oggetto con supporto per interazioni.</span><span class="sxs-lookup"><span data-stu-id="51c14-181">I see a progress indicator when I dwell on an interactable object.</span></span></td>
        <td><span data-ttu-id="51c14-182">Si vedono conferme visive e/o si sentono conferme udibili quando si intraprendono azioni.</span><span class="sxs-lookup"><span data-stu-id="51c14-182">I see/hear visual and audible confirmations when I take action.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="51c14-183"><a href="hands-free.md">Mani libere (esecuzione di comandi vocali)</a></span><span class="sxs-lookup"><span data-stu-id="51c14-183"><a href="hands-free.md">Hands-free (Voice commanding)</a></span></span></td>
        <td><span data-ttu-id="51c14-184">Si vedono un indicatore di ascolto e sottotitoli che mostrano quello che il sistema ha sentito.</span><span class="sxs-lookup"><span data-stu-id="51c14-184">I see a listening indicator and captions that show what the system heard.</span></span></td>
        <td><span data-ttu-id="51c14-185">Si ricevono messaggi vocali e suggerimenti.</span><span class="sxs-lookup"><span data-stu-id="51c14-185">I get voice prompts and hints.</span></span> <span data-ttu-id="51c14-186">Quando si dice: "Cosa posso dire?"</span><span class="sxs-lookup"><span data-stu-id="51c14-186">When I say: "What can I say?"</span></span> <span data-ttu-id="51c14-187">viene visualizzato un messaggio di feedback.</span><span class="sxs-lookup"><span data-stu-id="51c14-187">I see feedback.</span></span></td>
        <td><span data-ttu-id="51c14-188">Si vedono o si sentono conferme visive o udibili quando si dà un comando o si ottiene una disambiguazione dell'esperienza utente, se necessario.</span><span class="sxs-lookup"><span data-stu-id="51c14-188">I see/hear visual and audible confirmations when I give a command, or get disambiguation UX when needed.</span></span></a></td>
    </tr>
</table>

### <a name="below-are-questions-that-weve-found-help-teams-select-an-interaction-model"></a><span data-ttu-id="51c14-189">Di seguito sono riportate alcune domande che, in base ai nostri riscontri, possono aiutare i team a scegliere un modello di interazione:</span><span class="sxs-lookup"><span data-stu-id="51c14-189">Below are questions that we've found help teams select an interaction model:</span></span>
 
1.  <span data-ttu-id="51c14-190">D:  Gli utenti vogliono toccare gli ologrammi ed eseguire manipolazioni olografiche precise?</span><span class="sxs-lookup"><span data-stu-id="51c14-190">Q:  Do my users want to touch holograms and perform precision holographic manipulations?</span></span><br><br>
<span data-ttu-id="51c14-191">R:  Se la risposta è affermativa, scegli il modello di interazione mani e controller del movimento per la selezione della destinazione di precisione e la manipolazione.</span><span class="sxs-lookup"><span data-stu-id="51c14-191">A:  If so, check out the Hands and motion controllers interaction model for precision targeting and manipulation.</span></span>
 
2.  <span data-ttu-id="51c14-192">D:  Gli utenti devono avere le mani libere per poter eseguire attività reali?</span><span class="sxs-lookup"><span data-stu-id="51c14-192">Q:  Do my users need to keep their hands free for real-world tasks?</span></span><br><br>
<span data-ttu-id="51c14-193">R:  In caso affermativo, prendi in considerazione il modello di interazione a mani libere, che offre un'eccezionale esperienza a mani libere attraverso interazioni basate sullo sguardo e sulla voce.</span><span class="sxs-lookup"><span data-stu-id="51c14-193">A:  If so, take a look at the Hands-free interaction model, which provides a great hands-free experience through gaze and voice-based interactions.</span></span>
 
3.  <span data-ttu-id="51c14-194">D:  Gli utenti hanno tempo sufficiente per apprendere le interazioni per le applicazioni di realtà mista o hanno bisogno delle interazioni con la curva di apprendimento più bassa?</span><span class="sxs-lookup"><span data-stu-id="51c14-194">Q:  Do my users have time to learn interactions for my MR application or do they need the interactions with the lowest learning curve possible?</span></span><br><br>
<span data-ttu-id="51c14-195">R:  Per le interazioni più intuitive e con la curva di apprendimento più bassa, è consigliabile scegliere il modello mani e controller del movimento, purché gli utenti possano usare le mani per l'interazione.</span><span class="sxs-lookup"><span data-stu-id="51c14-195">A:  For the lowest learning curve and most intuitive interactions, we recommend the Hands and motion controllers model, as long as users are able to use their hands for interaction.</span></span>
 
4.  <span data-ttu-id="51c14-196">D:  Gli utenti usano i controller del movimento per le azioni di puntamento e manipolazione?</span><span class="sxs-lookup"><span data-stu-id="51c14-196">Q:  Do my users use motion controllers for pointing and manipulation?</span></span><br><br>
<span data-ttu-id="51c14-197">R:  Il modello mani e controller del movimento include tutte le indicazioni per un'esperienza eccezionale con i controller del movimento.</span><span class="sxs-lookup"><span data-stu-id="51c14-197">A:  The Hands and motion controllers model includes all guidance for a great experience with motion controllers.</span></span>
 
5.  <span data-ttu-id="51c14-198">D:  Gli utenti usano un controller di accessibilità o un comune controller Bluetooth, ad esempio un dispositivo Clicker?</span><span class="sxs-lookup"><span data-stu-id="51c14-198">Q:  Do my users use an accessibility controller or a common Bluetooth controller, such as a clicker?</span></span><br><br>
<span data-ttu-id="51c14-199">R:  Per tutti i controller non tracciati è consigliabile usare il modello di puntamento con la testa e commit,</span><span class="sxs-lookup"><span data-stu-id="51c14-199">A:  We recommend the Head-gaze and commit model for all non-tracked controllers.</span></span> <span data-ttu-id="51c14-200">studiato per consentire a un utente di vivere un'intera esperienza in base a un semplice meccanismo di "selezione della destinazione e commit".</span><span class="sxs-lookup"><span data-stu-id="51c14-200">It's designed to allow a user to traverse an entire experience with a simple "target and commit" mechanism.</span></span> 
 
6.  <span data-ttu-id="51c14-201">D: Gli utenti attraversano un'esperienza in modalità "click-through", ad esempio in un ambiente simile a una presentazione 3D, invece di spostarsi all'interno di layout pieni di controlli di interfaccia?</span><span class="sxs-lookup"><span data-stu-id="51c14-201">Q: Do my users only progress through an experience by "clicking through" (for example in a 3D slideshow-like environment), as opposed to navigating dense layouts of UI controls?</span></span><br><br>
<span data-ttu-id="51c14-202">R:  Se non è necessario usare molti controlli di interfaccia, il modello di puntamento con la testa e commit è un'opzione praticabile che consente agli utenti di non doversi preoccupare della selezione della destinazione.</span><span class="sxs-lookup"><span data-stu-id="51c14-202">A:  If users do not need to control a lot of UI, Head-gaze and commit offers a learnable option where users do not have to worry about targeting.</span></span> 
 
7.  <span data-ttu-id="51c14-203">D:  Gli utenti usano sia i visori VR immersive di HoloLens (prima generazione) sia quelli di HoloLens 2/Windows Mixed Reality?</span><span class="sxs-lookup"><span data-stu-id="51c14-203">Q:  Do my users use both HoloLens (1st gen) and HoloLens 2/Windows Mixed Reality immersive headsets (VR)?</span></span><br><br>
<span data-ttu-id="51c14-204">R:  Poiché quello di puntamento con la testa e commit è il modello di interazione per HoloLens (prima generazione), è consigliabile che gli autori che supportano HoloLens (prima generazione) usino questo modello per qualsiasi funzionalità o modalità che gli utenti possono sperimentare con un visore VR HoloLens (prima generazione).</span><span class="sxs-lookup"><span data-stu-id="51c14-204">A:  Since Head-gaze and commit is the interaction model for HoloLens (1st gen), we recommend that creators who support HoloLens (1st gen) use Head-gaze and commit for any features or modes that users will experience on a HoloLens (1st gen) headset.</span></span> <span data-ttu-id="51c14-205">Per informazioni dettagliate sull'eccezionale esperienza offerta da più generazioni di HoloLens, vedere la prossima sezione relativa al *passaggio da un modello di interazione all'altro*.</span><span class="sxs-lookup"><span data-stu-id="51c14-205">Please see the next section below on *Transitioning interaction models* for details on making a great experience for multiple HoloLens generations.</span></span>
 
8.  <span data-ttu-id="51c14-206">D: Quali sono le indicazioni per gli utenti che in genere usano dispositivi mobili, muovendosi in uno spazio di grandi dimensioni o spostandosi da uno spazio all'altro, e per quelli che tendono a operare in un unico spazio?</span><span class="sxs-lookup"><span data-stu-id="51c14-206">Q: What about users who are generally mobile, covering a large space or moving between spaces, versus users who tend to work in a single space?</span></span><br><br>
<span data-ttu-id="51c14-207">R:  Tutti i modelli di interazione sono adatti a questi utenti.</span><span class="sxs-lookup"><span data-stu-id="51c14-207">A:  Any of the interaction models will work for these users.</span></span>  

> [!NOTE]
> <span data-ttu-id="51c14-208">Saranno [presto disponibili](news.md) altre istruzioni di progettazione specifiche per le app.</span><span class="sxs-lookup"><span data-stu-id="51c14-208">More guidance specific to app design [coming soon](news.md).</span></span>


## <a name="transitioning-interaction-models"></a><span data-ttu-id="51c14-209">Passaggio da un modello di interazione all'altro</span><span class="sxs-lookup"><span data-stu-id="51c14-209">Transitioning interaction models</span></span>
<span data-ttu-id="51c14-210">Per alcuni casi d'uso può essere necessario impiegare più modelli di interazione.</span><span class="sxs-lookup"><span data-stu-id="51c14-210">There are also use cases that might require utilizing more than one interaction model.</span></span> <span data-ttu-id="51c14-211">Ad esempio, per il flusso di creazione di un'applicazione viene usato il modello di interazione _"mani e controller del movimento"_ , ma per i tecnici sul campo è preferibile adottare una modalità a mani libere.</span><span class="sxs-lookup"><span data-stu-id="51c14-211">For example, your application's creation flow utilizes the _"hands and motion controllers"_ interaction model, but you want to employ a hands-free mode for field technicians.</span></span>
<span data-ttu-id="51c14-212">Se per un'esperienza sono necessari più modelli di interazione, tieni presente che molti utenti possono avere difficoltà a passare da un modello all'altro, in particolare quelli che hanno scarsa familiarità con la realtà mista.</span><span class="sxs-lookup"><span data-stu-id="51c14-212">If your experience does require multiple interaction models, please keep in mind that many users might encounter difficulty when transitioning from one model to another, especially users who are new to mixed reality.</span></span>

> [!Note]
> <span data-ttu-id="51c14-213">Continueremo a fornire altre indicazioni che saranno rese disponibili per sviluppatori e progettisti per informarli su come, quando e perché usare più modelli di interazione di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="51c14-213">We're constantly working on more guidance that will be available to developers and designers, informing them about the how, when, and why for using multiple MR interaction models.</span></span>
 

## <a name="see-also"></a><span data-ttu-id="51c14-214">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="51c14-214">See also</span></span>
* [<span data-ttu-id="51c14-215">Comodità</span><span class="sxs-lookup"><span data-stu-id="51c14-215">Comfort</span></span>](comfort.md)
* [<span data-ttu-id="51c14-216">Interazione basata sullo sguardo</span><span class="sxs-lookup"><span data-stu-id="51c14-216">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="51c14-217">Tracciamento oculare in HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="51c14-217">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="51c14-218">Sguardo e commit</span><span class="sxs-lookup"><span data-stu-id="51c14-218">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="51c14-219">Sguardo fisso e attesa</span><span class="sxs-lookup"><span data-stu-id="51c14-219">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="51c14-220">Mani - Manipolazione diretta</span><span class="sxs-lookup"><span data-stu-id="51c14-220">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="51c14-221">Mani - Movimenti</span><span class="sxs-lookup"><span data-stu-id="51c14-221">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="51c14-222">Mani - Puntamento e commit</span><span class="sxs-lookup"><span data-stu-id="51c14-222">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="51c14-223">Interazioni istintive</span><span class="sxs-lookup"><span data-stu-id="51c14-223">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="51c14-224">Controller del movimento</span><span class="sxs-lookup"><span data-stu-id="51c14-224">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="51c14-225">Mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="51c14-225">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="51c14-226">Progettazione dell'audio spaziale</span><span class="sxs-lookup"><span data-stu-id="51c14-226">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="51c14-227">Input vocale</span><span class="sxs-lookup"><span data-stu-id="51c14-227">Voice input</span></span>](voice-input.md)



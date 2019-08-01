---
title: Panoramica dell'interazione multimodale
description: Panoramica dell'interazione multimodale
author: shengkait
ms.author: shengkait
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Realtà mista, sguardo fisso, selezione della destinazione con lo sguardo fisso, interazione, progettazione, HoloLens, MMR, multimodale
ms.openlocfilehash: 3ba1a2fc46aa88c856e4cc9531382c479b3fb17a
ms.sourcegitcommit: 76a7aa6e64e114b63ace058dd6d6d662b3c9f09e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/26/2019
ms.locfileid: "68507902"
---
# <a name="introducing-instinctual-interactions"></a><span data-ttu-id="7d996-104">Introduzione alle interazioni istintive</span><span class="sxs-lookup"><span data-stu-id="7d996-104">Introducing instinctual interactions</span></span>

<span data-ttu-id="7d996-105">La filosofia delle interazioni semplici e istintive è alla base di tutta la piattaforma Realtà mista.</span><span class="sxs-lookup"><span data-stu-id="7d996-105">The philosophy of simple, instinctual interactions is interwoven throughout the Mixed Reality platform.</span></span>  <span data-ttu-id="7d996-106">Abbiamo adottato tre accorgimenti per consentire ai progettisti e agli sviluppatori di applicazioni di fornire ai clienti interazioni facili e intuitive.</span><span class="sxs-lookup"><span data-stu-id="7d996-106">We've taken three steps to ensure that application designers and developers can provide their customers with easy and intuitive interactions.</span></span> 

<span data-ttu-id="7d996-107">In primo luogo, ci siamo assicurati che i sensori e le tecnologie di input, tra cui il tracciamento oculare e delle mani e l'input in linguaggio naturale, si combinino in perfetti modelli di interazione multimodale.</span><span class="sxs-lookup"><span data-stu-id="7d996-107">First, we've made sure our sensors and input technologies (which includes hand and eye tracking along with natural language input) combine into seamless, multimodal interaction models.</span></span>  <span data-ttu-id="7d996-108">In base alle nostre ricerche, le attività di progettazione e sviluppo all'interno di un framework multimodale e non basate su singoli input sono la chiave di volta per creare esperienze istintive.</span><span class="sxs-lookup"><span data-stu-id="7d996-108">Based on our research, designing and developing within a multimodal framework, and not based on single inputs, is the key to creating instinctual experiences.</span></span>

<span data-ttu-id="7d996-109">In secondo luogo, constatiamo che molti sviluppatori destinano le loro applicazioni a più dispositivi HoloLens, come HoloLens 2 e HoloLens (prima generazione) oppure HoloLens e VR.</span><span class="sxs-lookup"><span data-stu-id="7d996-109">Second, we recognize that many developers target multiple HoloLens devices, such as HoloLens 2 and HoloLens (1st gen) or HoloLens and VR.</span></span>  <span data-ttu-id="7d996-110">Abbiamo quindi progettato modelli di interazione in grado di funzionare in tutti i dispositivi, anche se la tecnologia di input varia da uno all'altro.</span><span class="sxs-lookup"><span data-stu-id="7d996-110">So we've designed our interaction models to work across devices, even if the input technology varies on each device.</span></span>  <span data-ttu-id="7d996-111">Ad esempio, per l'interazione da lontano con un visore VR immersive di Windows dotato di un controller 6DoF e per l'interazione da lontano con un dispositivo HoloLens 2 vengono usati gli stessi inviti e modelli, semplificando lo sviluppo di applicazioni per più dispositivi che assicurano interazioni più naturali con gli utenti finali.</span><span class="sxs-lookup"><span data-stu-id="7d996-111">For example, far interaction on a Windows Immersive headset with a 6DoF controller and far interaction on a HoloLens 2 both use  identical affordances and patterns, making it easy for cross-device application development that provides a natural feel to end-user interactions.</span></span> 

<span data-ttu-id="7d996-112">Anche se sappiamo che esistono migliaia di interazioni efficaci, coinvolgenti e fantastiche nella realtà mista, abbiamo constatato che l'utilizzo intenzionale di un unico modello di interazione end-to-end in un'applicazione è il modo migliore per garantire agli utenti risultati ottimali e un'esperienza eccezionale.</span><span class="sxs-lookup"><span data-stu-id="7d996-112">While we recognize that there are thousands of effective, engaging, and magical interactions possible in mixed reality (MR), we've found that intentionally employing a single interaction model, end-to-end, in an application is the best way to ensure users are successful and have a great experience.</span></span> <span data-ttu-id="7d996-113">A questo scopo, in queste indicazioni relative all'interazione abbiamo incluso tre aspetti:</span><span class="sxs-lookup"><span data-stu-id="7d996-113">To that end, we've included three things in this interaction guidance:</span></span>
* <span data-ttu-id="7d996-114">Il materiale è strutturato attorno ai tre principali modelli di interazione e ai componenti e agli schemi necessari per ognuno.</span><span class="sxs-lookup"><span data-stu-id="7d996-114">This guidance is structured around the three primary interaction models and the components and patterns required for each.</span></span>
* <span data-ttu-id="7d996-115">Sono state aggiunte istruzioni supplementari su altri vantaggi offerti dalla piattaforma.</span><span class="sxs-lookup"><span data-stu-id="7d996-115">Supplemental guidance has been included about other benefits that our platform provides.</span></span>
* <span data-ttu-id="7d996-116">Sono state inoltre incluse indicazioni per aiutare a selezionare il modello di interazione appropriato per uno scenario specifico.</span><span class="sxs-lookup"><span data-stu-id="7d996-116">Guidance has also been included to help select the appropriate interaction model for your development scenario.</span></span>

## <a name="multimodal-interaction-models"></a><span data-ttu-id="7d996-117">Modelli di interazione multimodale</span><span class="sxs-lookup"><span data-stu-id="7d996-117">Multimodal interaction models</span></span>

<span data-ttu-id="7d996-118">In base alle nostre ricerche e al feedback dei clienti, abbiamo scoperto che la maggior parte delle esperienze di realtà mista viene soddisfatta da tre principali modelli di interazione.</span><span class="sxs-lookup"><span data-stu-id="7d996-118">Based on our research as well as feedback from customers, we've discovered that three primary interaction models suit the majority of mixed reality experiences.</span></span>

<span data-ttu-id="7d996-119">Per molti versi, il modello di interazione è lo schema mentale seguito dall'utente per completare i flussi.</span><span class="sxs-lookup"><span data-stu-id="7d996-119">In many ways, the interaction model is the user's mental model for completing their flows.</span></span> <span data-ttu-id="7d996-120">Ognuno di questi modelli di interazione è ottimizzato per una serie di esigenze dei clienti.</span><span class="sxs-lookup"><span data-stu-id="7d996-120">Each of these interaction models is optimized for a set of customer needs.</span></span> <span data-ttu-id="7d996-121">Ognuno è pratico, efficace e utilizzabile a se stante.</span><span class="sxs-lookup"><span data-stu-id="7d996-121">Each is convenient, powerful, and usable in its own right.</span></span> 

<span data-ttu-id="7d996-122">La classifica seguente offre una panoramica semplificata.</span><span class="sxs-lookup"><span data-stu-id="7d996-122">The chart below is a simplified overview.</span></span> <span data-ttu-id="7d996-123">Informazioni dettagliate per l'utilizzo di ogni modello di interazione sono collegate a immagini ed esempi di codice nelle pagine seguenti.</span><span class="sxs-lookup"><span data-stu-id="7d996-123">Detailed information for using each interaction model is linked in the pages below with images and code samples.</span></span> 

<br>
<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="7d996-124"><strong>Modello</strong></span><span class="sxs-lookup"><span data-stu-id="7d996-124"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="7d996-125"><strong>Scenari di esempio</strong></span><span class="sxs-lookup"><span data-stu-id="7d996-125"><strong>Example scenarios</strong></span></span></td>
        <td><span data-ttu-id="7d996-126"><strong>Destinatari</strong></span><span class="sxs-lookup"><span data-stu-id="7d996-126"><strong>Fit</strong></span></span></td>
        <td><span data-ttu-id="7d996-127"><strong>Hardware</strong></span><span class="sxs-lookup"><span data-stu-id="7d996-127"><strong>Hardware</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="7d996-128"><a href="hands-and-tools.md">Mani e controller del movimento</a></span><span class="sxs-lookup"><span data-stu-id="7d996-128"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="7d996-129">Esperienze nello spazio 3D, ad esempio layout e progettazione dello spazio, manipolazione di contenuti o simulazione.</span><span class="sxs-lookup"><span data-stu-id="7d996-129">3D spatial experiences, such as spatial layout and design, content manipulation, or simulation.</span></span></td>
        <td><span data-ttu-id="7d996-130">Ideale per i nuovi utenti, in combinazione con comandi vocali, tracciamento oculare o puntamento con la testa.</span><span class="sxs-lookup"><span data-stu-id="7d996-130">Great for new users coupled with voice, eye tracking or head gaze.</span></span> <span data-ttu-id="7d996-131">Curva di apprendimento bassa.</span><span class="sxs-lookup"><span data-stu-id="7d996-131">Low learning curve.</span></span> <span data-ttu-id="7d996-132">Esperienza utente coerente con tracciamento delle mani e controller 6DoF.</span><span class="sxs-lookup"><span data-stu-id="7d996-132">Consistent UX across hand tracking and 6DoF controllers.</span></span></td>
        <td><span data-ttu-id="7d996-133">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="7d996-133">HoloLens 2</span></span><br><span data-ttu-id="7d996-134">Visori VR immersive</span><span class="sxs-lookup"><span data-stu-id="7d996-134">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="7d996-135"><a href="hands-free.md">Mani libere</a></span><span class="sxs-lookup"><span data-stu-id="7d996-135"><a href="hands-free.md">Hands-free</a></span></span></td>
        <td><span data-ttu-id="7d996-136">Esperienze contestuali in cui le mani dell'utente sono occupate, ad esempio apprendimento sul posto e manutenzione.</span><span class="sxs-lookup"><span data-stu-id="7d996-136">Contextual experiences where a user's hands are occupied, such as on-the-job learning, and maintenance.</span></span></td>
        <td><span data-ttu-id="7d996-137">È necessario un certo livello di apprendimento.</span><span class="sxs-lookup"><span data-stu-id="7d996-137">Some learning required.</span></span> <span data-ttu-id="7d996-138">Se le mani non sono disponibili, il dispositivo si adatta bene a comandi vocali e linguaggio naturale.</span><span class="sxs-lookup"><span data-stu-id="7d996-138">If hands are unavailable, the device pairs well with voice and natural language.</span></span></td>
        <td><span data-ttu-id="7d996-139">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="7d996-139">HoloLens 2</span></span><br><span data-ttu-id="7d996-140">HoloLens (prima generazione)</span><span class="sxs-lookup"><span data-stu-id="7d996-140">HoloLens (1st gen)</span></span><br><span data-ttu-id="7d996-141">Visori VR immersive</span><span class="sxs-lookup"><span data-stu-id="7d996-141">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="7d996-142"><a href="gaze-and-commit.md">Puntamento con la testa e commit</a></span><span class="sxs-lookup"><span data-stu-id="7d996-142"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="7d996-143">Esperienze di tipo click-through, ad esempio presentazioni 3D e demo.</span><span class="sxs-lookup"><span data-stu-id="7d996-143">Click-through experiences, e.g. 3D presentations, demos.</span></span></td>
        <td><span data-ttu-id="7d996-144">È necessario eseguire il training in dispositivi HMD, non in dispositivi mobili.</span><span class="sxs-lookup"><span data-stu-id="7d996-144">Requires training on HMDs but not on mobile.</span></span> <span data-ttu-id="7d996-145">Ideale per controller accessibili.</span><span class="sxs-lookup"><span data-stu-id="7d996-145">Best for accessible controllers.</span></span> <span data-ttu-id="7d996-146">Ideale per HoloLens (prima generazione).</span><span class="sxs-lookup"><span data-stu-id="7d996-146">Best for HoloLens (1st gen).</span></span></td>
        <td><span data-ttu-id="7d996-147">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="7d996-147">HoloLens 2</span></span><br><span data-ttu-id="7d996-148">HoloLens (prima generazione)</span><span class="sxs-lookup"><span data-stu-id="7d996-148">HoloLens (1st gen)</span></span><br><span data-ttu-id="7d996-149">Visori VR immersive</span><span class="sxs-lookup"><span data-stu-id="7d996-149">Immersive headsets</span></span><br><span data-ttu-id="7d996-150">AR per dispositivi mobili</span><span class="sxs-lookup"><span data-stu-id="7d996-150">Mobile AR</span></span></td>
    </tr>
</table>
<br>

<span data-ttu-id="7d996-151">Per evitare che siano presenti lacune o vuoti nell'interazione dell'esperienza utente, è preferibile seguire le indicazioni per un singolo modello dall'inizio alla fine.</span><span class="sxs-lookup"><span data-stu-id="7d996-151">To ensure that there are no gaps or holes in the user interaction experience, it is best to follow the guidance for a single model from beginning to end.</span></span> 

<span data-ttu-id="7d996-152">Per velocizzare le attività di progettazione e sviluppo, abbiamo incluso informazioni dettagliate e collegamenti a immagini ed esempi di codice all'interno della documentazione relativa a ciascun modello.</span><span class="sxs-lookup"><span data-stu-id="7d996-152">To speed up design and development, we've included detailed information and links to images and code samples within our coverage of each model.</span></span>

<span data-ttu-id="7d996-153">Le sezioni seguenti illustrano la procedura di selezione e implementazione di uno di questi modelli di interazione.</span><span class="sxs-lookup"><span data-stu-id="7d996-153">The sections below walk through the steps for selecting and implementing one of these interaction models.</span></span>  
 
### <a name="by-the-end-of-this-page-you-will-understand-our-guidance-on"></a><span data-ttu-id="7d996-154">Al termine di questa pagina, avrai appreso a:</span><span class="sxs-lookup"><span data-stu-id="7d996-154">By the end of this page, you will understand our guidance on:</span></span>
 
* <span data-ttu-id="7d996-155">Scegliere un modello di interazione per il cliente</span><span class="sxs-lookup"><span data-stu-id="7d996-155">Choosing an interaction model for your customer</span></span>
* <span data-ttu-id="7d996-156">Usare le indicazioni relative al modello di interazione</span><span class="sxs-lookup"><span data-stu-id="7d996-156">Using the interaction model guidance</span></span>
* <span data-ttu-id="7d996-157">Passare da un modello di interazione all'altro</span><span class="sxs-lookup"><span data-stu-id="7d996-157">Transitioning between interaction models</span></span>
* <span data-ttu-id="7d996-158">Progettare i passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="7d996-158">Design next steps</span></span>


## <a name="choose-an-interaction-model-for-your-customer"></a><span data-ttu-id="7d996-159">Scegliere un modello di interazione per il cliente</span><span class="sxs-lookup"><span data-stu-id="7d996-159">Choose an interaction model for your customer</span></span>


<span data-ttu-id="7d996-160">In genere, gli sviluppatori e gli autori valutano tutti i tipi di interazione che i clienti possono avere.</span><span class="sxs-lookup"><span data-stu-id="7d996-160">Typically, developers and creators have thought through the types of interactions that their customers can have.</span></span> <span data-ttu-id="7d996-161">Per incoraggiare un approccio alla progettazione incentrato sul cliente, è consigliabile attenersi alle indicazioni seguenti per selezionare il modello di interazione ottimizzato per il cliente specifico.</span><span class="sxs-lookup"><span data-stu-id="7d996-161">To encourage a customer-focused approach to design, we recommend the following guidance for selecting the interaction model that's optimized for your customer.</span></span>

### <a name="why-follow-this-guidance"></a><span data-ttu-id="7d996-162">Perché seguire le indicazioni?</span><span class="sxs-lookup"><span data-stu-id="7d996-162">Why follow this guidance?</span></span>

* <span data-ttu-id="7d996-163">I nostri modelli di interazione sono testati in base a criteri obiettivi e soggettivi, ad esempio lo sforzo fisico e cognitivo, l'intuitività e la capacità di apprendimento.</span><span class="sxs-lookup"><span data-stu-id="7d996-163">Our interaction models are tested for objective and subjective criteria, such as physical and cognitive effort, intuitiveness, and learnability.</span></span> 
* <span data-ttu-id="7d996-164">Poiché esistono diversi tipi di interazione, è possibile che anche gli inviti audio e video e il comportamento degli oggetti siano diversi da un modello all'altro.</span><span class="sxs-lookup"><span data-stu-id="7d996-164">Because interactions differ, visual and audio affordances and object behavior might differ between interaction models.</span></span>  
* <span data-ttu-id="7d996-165">Combinando parti di diversi modelli di interazione si rischia di ottenere inviti concorrenti, ad esempio raggi della mano simultanei e un cursore di puntamento con la testa, che possono confondere gli utenti.</span><span class="sxs-lookup"><span data-stu-id="7d996-165">Combining parts of multiple interaction models creates the risk of competing affordances, such as simultaneous hand rays and a head-gaze cursor that can overwhelm and confuse users.</span></span>

<span data-ttu-id="7d996-166">Ecco alcuni esempi di come sono ottimizzati gli inviti e i comportamenti per ogni modello di interazione.</span><span class="sxs-lookup"><span data-stu-id="7d996-166">Here are some examples of how affordances and behaviors are optimized for each interaction model.</span></span>  <span data-ttu-id="7d996-167">Notiamo spesso che le domande dei nuovi utenti sono simili, ad esempio: "Come si può capire se il sistema funziona? Come si può sapere quali azioni si possono eseguire? Come si può sapere se il sistema ha capito quali azioni sono state eseguite?"</span><span class="sxs-lookup"><span data-stu-id="7d996-167">We often see new users have similar questions, such as "how do I know the system is working, how do I know what I can do, and how do I know if it understood what I just did?"</span></span>

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="7d996-168"><strong>Modello</strong></span><span class="sxs-lookup"><span data-stu-id="7d996-168"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="7d996-169"><strong>Come si può capire se il sistema funziona?</strong></span><span class="sxs-lookup"><span data-stu-id="7d996-169"><strong>How do I know it's working?</strong></span></span></td>
        <td><span data-ttu-id="7d996-170"><strong>Come si può sapere quali azioni si possono eseguire?</strong></span><span class="sxs-lookup"><span data-stu-id="7d996-170"><strong>How do I know what I can do?</strong></span></span></td>
        <td><span data-ttu-id="7d996-171"><strong>Come si può sapere quali azioni sono state eseguite?</strong></span><span class="sxs-lookup"><span data-stu-id="7d996-171"><strong>How do I know what I just did?</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="7d996-172"><a href="hands-and-tools.md">Mani e controller del movimento</a></span><span class="sxs-lookup"><span data-stu-id="7d996-172"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="7d996-173">Si vede una mesh mano, un invito punta del dito o raggi della mano/controller.</span><span class="sxs-lookup"><span data-stu-id="7d996-173">I see a hand mesh, I see a fingertip affordance or hand/controller rays.</span></span></td>
        <td><span data-ttu-id="7d996-174">Si vedono punti di controllo afferrabili o un riquadro delimitatore quando si avvicina la mano a un oggetto.</span><span class="sxs-lookup"><span data-stu-id="7d996-174">I see grabbable handles or a bounding box appears when my hand is near an object.</span></span></td>
        <td><span data-ttu-id="7d996-175">Si sentono toni udibili e si vedono animazioni al momento di afferrare e rilasciare oggetti.</span><span class="sxs-lookup"><span data-stu-id="7d996-175">I hear audible tones and see animations on grab and release.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="7d996-176"><a href="gaze-and-commit.md">Puntamento con la testa e commit</a></span><span class="sxs-lookup"><span data-stu-id="7d996-176"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="7d996-177">Si vede un cursore al centro del campo visivo.</span><span class="sxs-lookup"><span data-stu-id="7d996-177">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="7d996-178">Il cursore di puntamento con la testa cambia stato quando è posizionato su determinati oggetti.</span><span class="sxs-lookup"><span data-stu-id="7d996-178">The head-gaze cursor changes state when it's over certain objects.</span></span></td>
        <td><span data-ttu-id="7d996-179">Si vedono conferme visive e/o si sentono conferme udibili quando si intraprendono azioni.</span><span class="sxs-lookup"><span data-stu-id="7d996-179">I see/hear visual and audible confirmations when I take action.</span></span></td>
    </tr>   
    <tr>
        <td><span data-ttu-id="7d996-180"><a href="hands-free.md">Mani libere (puntamento con la testa e attesa)</a></span><span class="sxs-lookup"><span data-stu-id="7d996-180"><a href="hands-free.md">Hands-free (Head-gaze and dwell)</a></span></span></td>
        <td><span data-ttu-id="7d996-181">Si vede un cursore al centro del campo visivo.</span><span class="sxs-lookup"><span data-stu-id="7d996-181">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="7d996-182">Si vede un indicatore di stato quando ci si sofferma su un oggetto con supporto per interazioni.</span><span class="sxs-lookup"><span data-stu-id="7d996-182">I see a progress indicator when I dwell on an interactable object.</span></span></td>
        <td><span data-ttu-id="7d996-183">Si vedono conferme visive e/o si sentono conferme udibili quando si intraprendono azioni.</span><span class="sxs-lookup"><span data-stu-id="7d996-183">I see/hear visual and audible confirmations when I take action.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="7d996-184"><a href="hands-free.md">Mani libere (esecuzione di comandi vocali)</a></span><span class="sxs-lookup"><span data-stu-id="7d996-184"><a href="hands-free.md">Hands-free (Voice commanding)</a></span></span></td>
        <td><span data-ttu-id="7d996-185">Si vedono un indicatore di ascolto e sottotitoli che mostrano quello che il sistema ha sentito.</span><span class="sxs-lookup"><span data-stu-id="7d996-185">I see a listening indicator and captions that show what the system heard.</span></span></td>
        <td><span data-ttu-id="7d996-186">Si ricevono messaggi vocali e suggerimenti.</span><span class="sxs-lookup"><span data-stu-id="7d996-186">I get voice prompts and hints.</span></span> <span data-ttu-id="7d996-187">Quando si dice: "Cosa posso dire?"</span><span class="sxs-lookup"><span data-stu-id="7d996-187">When I say: "What can I say?"</span></span> <span data-ttu-id="7d996-188">viene visualizzato un messaggio di feedback.</span><span class="sxs-lookup"><span data-stu-id="7d996-188">I see feedback.</span></span></td>
        <td><span data-ttu-id="7d996-189">Si vedono o si sentono conferme visive o udibili quando si dà un comando o quando si ottiene una disambiguazione dell'esperienza utente, se necessario.</span><span class="sxs-lookup"><span data-stu-id="7d996-189">I see/ hear visual and audible confirmations when I give a command, or get disambiguation UX when needed.</span></span></a></td>
    </tr>
</table>

### <a name="below-are-the-questions-that-weve-found-help-teams-select-an-interaction-model"></a><span data-ttu-id="7d996-190">Di seguito sono riportate le domande che, in base ai nostri riscontri, possono aiutare i team a scegliere un modello di interazione:</span><span class="sxs-lookup"><span data-stu-id="7d996-190">Below are the questions that we've found help teams select an interaction model:</span></span>
 
1.  <span data-ttu-id="7d996-191">D:  Gli utenti vogliono toccare gli ologrammi ed eseguire manipolazioni olografiche precise?</span><span class="sxs-lookup"><span data-stu-id="7d996-191">Q:  Do my users want to touch holograms and perform precision holographic manipulations?</span></span><br><br>
<span data-ttu-id="7d996-192">R:  Se la risposta è affermativa, scegli il modello di interazione mani e controller del movimento per la selezione di precisione della destinazione e la manipolazione con mani e controller del movimento.</span><span class="sxs-lookup"><span data-stu-id="7d996-192">A:  If so, check out the Hands and motion controllers interaction model for precision targeting and manipulation with hands or motion controllers.</span></span>
 
2.  <span data-ttu-id="7d996-193">D:  Gli utenti devono avere le mani libere per poter eseguire attività reali?</span><span class="sxs-lookup"><span data-stu-id="7d996-193">Q:  Do my users need to keep their hands free for real-world tasks?</span></span><br><br>
<span data-ttu-id="7d996-194">R:  In caso affermativo, prendi in considerazione il modello di interazione a mani libere, che offre un'eccezionale esperienza a mani libere attraverso interazioni basate sullo sguardo e sulla voce.</span><span class="sxs-lookup"><span data-stu-id="7d996-194">A:  If so, take a look at the Hands-free interaction model, which provides a great hands-free experience through gaze and voice-based interactions.</span></span>
 
3.  <span data-ttu-id="7d996-195">D:  Gli utenti hanno tempo sufficiente per apprendere le interazioni per le applicazioni di realtà mista o hanno bisogno delle interazioni con la curva di apprendimento più bassa?</span><span class="sxs-lookup"><span data-stu-id="7d996-195">Q:  Do my users have time to learn interactions for my MR application or do they need the interactions with the lowest learning curve possible?</span></span><br><br>
<span data-ttu-id="7d996-196">R:  Per le interazioni più intuitive e con la curva di apprendimento più bassa, è consigliabile scegliere il modello mani e controller del movimento, purché gli utenti possano usare le mani per l'interazione.</span><span class="sxs-lookup"><span data-stu-id="7d996-196">A:  We recommend the Hands and motion controllers model for the lowest learning curve and most intuitive interactions, as long as users are able to use their hands for interaction.</span></span>
 
4.  <span data-ttu-id="7d996-197">D:  Gli utenti usano i controller del movimento per le azioni di puntamento e manipolazione?</span><span class="sxs-lookup"><span data-stu-id="7d996-197">Q:  Do my users use motion controllers for pointing and manipulation?</span></span><br><br>
<span data-ttu-id="7d996-198">R:  Il modello mani e controller del movimento include tutte le indicazioni per un'esperienza eccezionale con i controller del movimento.</span><span class="sxs-lookup"><span data-stu-id="7d996-198">A:  The Hands and motion controllers model includes all guidance for a great experience with motion controllers.</span></span>
 
5.  <span data-ttu-id="7d996-199">D:  Gli utenti usano un controller di accessibilità o un comune controller Bluetooth, ad esempio un dispositivo Clicker?</span><span class="sxs-lookup"><span data-stu-id="7d996-199">Q:  Do my users use an accessibility controller or a common Bluetooth controller, such as a clicker?</span></span><br><br>
<span data-ttu-id="7d996-200">R:  Per tutti i controller non tracciati è consigliabile usare il modello di puntamento con la testa e commit,</span><span class="sxs-lookup"><span data-stu-id="7d996-200">A:  We recommend the Head-gaze and commit model for all non-tracked controllers.</span></span> <span data-ttu-id="7d996-201">studiato per consentire a un utente di vivere un'intera esperienza in base a un semplice meccanismo di "selezione della destinazione e commit".</span><span class="sxs-lookup"><span data-stu-id="7d996-201">It's designed to allow a user to traverse an entire experience with a simple "target and commit" mechanism.</span></span> 
 
6.  <span data-ttu-id="7d996-202">D: Gli utenti attraversano un'esperienza in modalità "click-through", ad esempio in un ambiente simile a una presentazione 3D, invece di spostarsi all'interno di layout pieni di controlli di interfaccia?</span><span class="sxs-lookup"><span data-stu-id="7d996-202">Q: Do my users only progress through an experience by "clicking through" (for example in a 3D slideshow-like environment), as opposed to navigating dense layouts of UI controls?</span></span><br><br>
<span data-ttu-id="7d996-203">R:  Se non è necessario usare molti controlli di interfaccia, il modello di puntamento con la testa e commit è un'opzione praticabile che consente agli utenti di non doversi preoccupare della selezione della destinazione.</span><span class="sxs-lookup"><span data-stu-id="7d996-203">A:  If users do not need to control a lot of UI, Head-gaze and commit offers a learnable option where users do not have to worry about targeting.</span></span> 
 
7.  <span data-ttu-id="7d996-204">D:  Gli utenti usano sia i visori VR immersive di HoloLens (prima generazione) sia quelli di HoloLens 2/Windows Mixed Reality?</span><span class="sxs-lookup"><span data-stu-id="7d996-204">Q:  Do my users use both HoloLens (1st gen) and HoloLens 2/Windows Mixed Reality immersive headsets (VR)?</span></span><br><br>
<span data-ttu-id="7d996-205">R:  Poiché quello di puntamento con la testa e commit è il modello di interazione per HoloLens (prima generazione), è consigliabile che gli autori che supportano HoloLens (prima generazione) usino questo modello per qualsiasi funzionalità o modalità che gli utenti possono sperimentare con un visore VR HoloLens (prima generazione).</span><span class="sxs-lookup"><span data-stu-id="7d996-205">A:  Since Head-gaze and commit is the interaction model for HoloLens (1st gen), we recommend that creators who support HoloLens (1st gen) use Head-gaze and commit for any features or modes that users will experience on a HoloLens (1st gen) headset.</span></span> <span data-ttu-id="7d996-206">Per informazioni dettagliate sull'eccezionale esperienza offerta da più generazioni di HoloLens, vedere la prossima sezione relativa al *passaggio da un modello di interazione all'altro*.</span><span class="sxs-lookup"><span data-stu-id="7d996-206">Please see the next section below on *Transitioning interaction models* for details on making a great experience for multiple HoloLens generations.</span></span>
 
8.  <span data-ttu-id="7d996-207">D: Quali sono le indicazioni per gli utenti che in genere usano dispositivi mobili, muovendosi in uno spazio di grandi dimensioni o spostandosi da uno spazio all'altro, e per quelli che tendono a operare in un unico spazio?</span><span class="sxs-lookup"><span data-stu-id="7d996-207">Q: What about users who are generally mobile, covering a large space or moving between spaces, versus users who tend to work in a single space?</span></span><br><br>
<span data-ttu-id="7d996-208">R:  Tutti i modelli di interazione sono adatti a questi utenti.</span><span class="sxs-lookup"><span data-stu-id="7d996-208">A:  Any of the interaction models will work for these users.</span></span>  

> [!NOTE]
> <span data-ttu-id="7d996-209">Saranno [presto disponibili](index.md#news-and-notes) altre istruzioni di progettazione specifiche per le app.</span><span class="sxs-lookup"><span data-stu-id="7d996-209">More guidance specific to app design [coming soon](index.md#news-and-notes).</span></span>


## <a name="transitioning-interaction-models"></a><span data-ttu-id="7d996-210">Passaggio da un modello di interazione all'altro</span><span class="sxs-lookup"><span data-stu-id="7d996-210">Transitioning interaction models</span></span>
<span data-ttu-id="7d996-211">Per alcuni casi d'uso può essere necessario impiegare più modelli di interazione.</span><span class="sxs-lookup"><span data-stu-id="7d996-211">There are also use cases that might require utilizing more than one interaction model.</span></span> <span data-ttu-id="7d996-212">Ad esempio, per il flusso di creazione di un'applicazione viene utilizzato il modello di interazione mani e controller del movimento, ma per i tecnici sul campo è preferibile adottare una modalità a mani libere.</span><span class="sxs-lookup"><span data-stu-id="7d996-212">For example, your application's creation flow utilizes the Hands and motion controllers interaction model, but you want to employ a hands-free mode for field technicians.</span></span>  

<span data-ttu-id="7d996-213">Se per un'esperienza sono necessari più modelli di interazione, tieni presente che molti utenti finali possono avere difficoltà a passare da un modello all'altro, in particolare quelli che hanno scarsa familiarità con la realtà mista.</span><span class="sxs-lookup"><span data-stu-id="7d996-213">If your experience does require multiple interaction models, keep in mind that many end users might encounter difficulty when transitioning from one model to another--especially for users who are new to mixed reality.</span></span>

> [!Note]
> <span data-ttu-id="7d996-214">Continueremo a fornire altre indicazioni che saranno rese disponibili per sviluppatori e progettisti per informarli su come, quando e perché usare più modelli di interazione di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="7d996-214">We're constantly working on more guidance that will be available to developers and designers, informing them about the how, when, and why for using multiple MR interaction models.</span></span>
 

## <a name="see-also"></a><span data-ttu-id="7d996-215">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="7d996-215">See also</span></span>
* [<span data-ttu-id="7d996-216">Puntamento con la testa e commit</span><span class="sxs-lookup"><span data-stu-id="7d996-216">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="7d996-217">Puntamento con la testa e attesa</span><span class="sxs-lookup"><span data-stu-id="7d996-217">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="7d996-218">Manipolazione diretta con le mani</span><span class="sxs-lookup"><span data-stu-id="7d996-218">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="7d996-219">Puntamento e commit con le mani</span><span class="sxs-lookup"><span data-stu-id="7d996-219">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="7d996-220">Movimenti</span><span class="sxs-lookup"><span data-stu-id="7d996-220">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="7d996-221">Esecuzione di comandi vocali</span><span class="sxs-lookup"><span data-stu-id="7d996-221">Voice commanding</span></span>](voice-design.md)
* [<span data-ttu-id="7d996-222">Controller del movimento</span><span class="sxs-lookup"><span data-stu-id="7d996-222">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="7d996-223">Progettazione dell'audio spaziale</span><span class="sxs-lookup"><span data-stu-id="7d996-223">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="7d996-224">Progettazione del mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="7d996-224">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="7d996-225">Comodità</span><span class="sxs-lookup"><span data-stu-id="7d996-225">Comfort</span></span>](comfort.md)


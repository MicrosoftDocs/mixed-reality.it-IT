---
title: Panoramica di interazione multimodale
description: Panoramica dell'interazione multimodale
author: shengkait
ms.author: shengkait
ms.date: 04/11/2019
ms.topic: article
keywords: Progettare sguardo, sguardo targeting, interazione, realtà mista
ms.openlocfilehash: f52a0cd8ec53bfe0f4c5da2c054c538eda1c93ca
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993596"
---
# <a name="introducing-instinctual-interactions"></a><span data-ttu-id="bfa98-104">Introduzione a instinctual interazioni</span><span class="sxs-lookup"><span data-stu-id="bfa98-104">Introducing instinctual interactions</span></span>
<span data-ttu-id="bfa98-105">La filosofia di interazioni semplice, instinctual sperimentare tutta la piattaforma Microsoft di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="bfa98-105">The philosophy of simple, instinctual interactions is woven throughout the Microsoft Mixed Reality platform.</span></span>  <span data-ttu-id="bfa98-106">Sono state utilizzate tre passaggi per garantire che gli sviluppatori e progettisti di applicazioni possono offrire le interazioni semplice e intuitive per i clienti.</span><span class="sxs-lookup"><span data-stu-id="bfa98-106">We've taken three steps to ensure that application designers and developers can provide easy and intuitive interactions for their customers.</span></span> 

<span data-ttu-id="bfa98-107">In primo luogo, siamo quindi assicurati le straordinari sensori e tecnologie per l'input, tra cui mano rilevamento sotto controllo di rilevamento e linguaggio naturale, combinare in modelli di interazione multimodale invisibile.</span><span class="sxs-lookup"><span data-stu-id="bfa98-107">First, we've made sure our amazing sensors and input technology, including hand tracking, eye tracking, and natural language, combine into seamless multimodal interaction models.</span></span>  <span data-ttu-id="bfa98-108">Basato su ricerca, progettazione e lo sviluppo multimodally e non basati su singoli input, è essenziale per la creazione di esperienze instinctual.</span><span class="sxs-lookup"><span data-stu-id="bfa98-108">Based on our research, designing and developing multimodally -- and not based on single inputs -- is the key to creating instinctual experiences.</span></span>

<span data-ttu-id="bfa98-109">In secondo luogo, è possibile riconoscere che molti sviluppatori di supportare più dispositivi, indipendentemente dal fatto che questa 2 HoloLens e HoloLens (dal 1 ° generazione) o HoloLens e VR.</span><span class="sxs-lookup"><span data-stu-id="bfa98-109">Secondly, we recognize that many developers target multiple devices, whether that means HoloLens 2 and HoloLens (1st gen) or HoloLens and VR.</span></span>  <span data-ttu-id="bfa98-110">In modo che è stato progettato i nostri modelli di interazione per funzionare in diversi dispositivi (anche se la tecnologia input varia in ogni dispositivo).</span><span class="sxs-lookup"><span data-stu-id="bfa98-110">So we've designed our interaction models to work across devices (even if the input technology varies on each device).</span></span>  <span data-ttu-id="bfa98-111">Ad esempio, interazione decisamente su un auricolare coinvolgenti di Windows con un controller 6DOF e interazione decisamente su un 2 HoloLens entrambi usare gli affordance identici e modelli, rendendo più semplice per applicazioni multidispositivo.</span><span class="sxs-lookup"><span data-stu-id="bfa98-111">For example, far interaction on a Windows Immersive headset with a 6DOF controller and far interaction on a HoloLens 2 both use the identical affordances and patterns, making it easy for cross-device applications.</span></span> <span data-ttu-id="bfa98-112">È non solo questo utile per gli sviluppatori e progettisti, ma è scontata agli utenti finali.</span><span class="sxs-lookup"><span data-stu-id="bfa98-112">Not only is this convenient for developers and designers, but it feels natural to end users.</span></span> 

<span data-ttu-id="bfa98-113">Infine, anche se è possibile riconoscere che sono presenti migliaia di validità, coinvolgenti e interazioni magiche presenti possibili in MR, si è constatato che utilizza intenzionalmente un modello di sola interazione end-to-end in un'applicazione è il modo migliore per assicurarsi che gli utenti hanno esito positivo e avere un'esperienza ottimale.</span><span class="sxs-lookup"><span data-stu-id="bfa98-113">Lastly, while we recognize that there are thousands of effective, engaging, and magical interactions possible in MR, we have found that intentionally employing a single interaction model end to end in an application is the best way to ensure users are successful and have a great experience.</span></span>  <span data-ttu-id="bfa98-114">A tale scopo, sono state incluse tre operazioni in questo materiale sussidiario interazione:</span><span class="sxs-lookup"><span data-stu-id="bfa98-114">To that end, we've included three things in this interaction guidance:</span></span>
* <span data-ttu-id="bfa98-115">È stata strutturata questo materiale sussidiario i tre modelli di interazione principale e i componenti e i modelli necessari per ogni</span><span class="sxs-lookup"><span data-stu-id="bfa98-115">We've structured this guidance around the three primary interaction models and the components and patterns required for each</span></span>
* <span data-ttu-id="bfa98-116">Sono state incluse istruzioni aggiuntive su altri vantaggi che la nostra piattaforma di fornisce</span><span class="sxs-lookup"><span data-stu-id="bfa98-116">We've included supplemental guidance on other benefits that our platform provides</span></span>
* <span data-ttu-id="bfa98-117">Sono incluse indicazioni per consentire di selezionare il modello di interazione appropriato per lo scenario</span><span class="sxs-lookup"><span data-stu-id="bfa98-117">We've included guidance to help select the appropriate interaction model for your scenario</span></span>


## <a name="three-multimodal-interaction-models"></a><span data-ttu-id="bfa98-118">Tre modelli di interazione multimodale</span><span class="sxs-lookup"><span data-stu-id="bfa98-118">Three multimodal interaction models</span></span>
<span data-ttu-id="bfa98-119">A seconda della ricerca e il lavoro con i clienti a oggi, abbiamo scoperto che i tre modelli di interazione principale soddisfare la maggior parte delle esperienze di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="bfa98-119">Based on our research and work with customers to date, we've discovered that three primary interaction models suit the majority of Mixed Reality experiences.</span></span>

<span data-ttu-id="bfa98-120">In molti modi, il modello di interazione è modello mentale dell'utente per il completamento dei flussi.</span><span class="sxs-lookup"><span data-stu-id="bfa98-120">In many ways, the interaction model  is the user's mental model for completing their flows.</span></span>  <span data-ttu-id="bfa98-121">Ognuno di questi modelli di interazione è ottimizzato per una serie di esigenze dei clienti e ognuno è conveniente, efficiente ed utilizzabile in sé.</span><span class="sxs-lookup"><span data-stu-id="bfa98-121">Each of these interaction models is optimized for a set of customer needs, and each is convenient, powerful, and usable in its own right.</span></span> 

<span data-ttu-id="bfa98-122">Il grafico seguente viene fornita una panoramica semplificata.</span><span class="sxs-lookup"><span data-stu-id="bfa98-122">The chart below is a simplified overview.</span></span>  <span data-ttu-id="bfa98-123">Informazioni dettagliate per l'utilizzo di ogni modello di interazione sono collegate nelle pagine seguenti con le immagini ed esempi di codice.</span><span class="sxs-lookup"><span data-stu-id="bfa98-123">Detailed information for using each interaction model is linked in the pages below with images and code samples.</span></span>  

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="bfa98-124"><strong>Modello</strong></span><span class="sxs-lookup"><span data-stu-id="bfa98-124"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="bfa98-125"><strong>Scenari di esempio</strong></span><span class="sxs-lookup"><span data-stu-id="bfa98-125"><strong>Example scenarios</strong></span></span></td>
        <td><span data-ttu-id="bfa98-126"><strong>Fit</strong></span><span class="sxs-lookup"><span data-stu-id="bfa98-126"><strong>Fit</strong></span></span></td>
        <td><span data-ttu-id="bfa98-127"><strong>Hardware</strong></span><span class="sxs-lookup"><span data-stu-id="bfa98-127"><strong>Hardware</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="bfa98-128"><a href="hands-and-tools.md">Strumenti e le mani</a></span><span class="sxs-lookup"><span data-stu-id="bfa98-128"><a href="hands-and-tools.md">Hands and tools</a></span></span></td>
        <td><span data-ttu-id="bfa98-129">Esperienze spaziali 3D</span><span class="sxs-lookup"><span data-stu-id="bfa98-129">3D spatial experiences</span></span><br><span data-ttu-id="bfa98-130">ad esempio spaziale layout e progettazione, manipolazione del contenuto o simulazione</span><span class="sxs-lookup"><span data-stu-id="bfa98-130">e.g. spatial layout and design, content manipulation, or simulation</span></span></td>
        <td><span data-ttu-id="bfa98-131">Ottima soluzione per i nuovi utenti</span><span class="sxs-lookup"><span data-stu-id="bfa98-131">Great for new users</span></span><br><span data-ttu-id="bfa98-132">Curva di apprendimento</span><span class="sxs-lookup"><span data-stu-id="bfa98-132">Low learning curve</span></span><br><span data-ttu-id="bfa98-133">Piedi affordance visual semplice</span><span class="sxs-lookup"><span data-stu-id="bfa98-133">Grounded in easy visual affordances</span></span><br><span data-ttu-id="bfa98-134">Esperienza utente coerente in mano di rilevamento e controller i gradi di libertà 6</span><span class="sxs-lookup"><span data-stu-id="bfa98-134">Consistent UX across hand tracking and 6 DoF controllers</span></span><br><span data-ttu-id="bfa98-135">Bene quando è associata vocali, estasiati occhio rilevamento o head</span><span class="sxs-lookup"><span data-stu-id="bfa98-135">Great when coupled with voice, eye tracking, or head gaze</span></span></td>
        <td><span data-ttu-id="bfa98-136">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="bfa98-136">HoloLens 2</span></span><br><span data-ttu-id="bfa98-137">Windows coinvolgenti con 6DOF controller</span><span class="sxs-lookup"><span data-stu-id="bfa98-137">Windows Immersive w/ 6DOF Controllers</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="bfa98-138"><a href="hands-free.md">Mani libere</a></span><span class="sxs-lookup"><span data-stu-id="bfa98-138"><a href="hands-free.md">Hands-free</a></span></span></td>
        <td><span data-ttu-id="bfa98-139">Esperienze contestuale in cui le mani dell'utente sono occupate, ad esempio nel processo di apprendimento, manutenzione</span><span class="sxs-lookup"><span data-stu-id="bfa98-139">Contextual experiences where a user's hands are occupied e.g. on the-job learning, maintenance</span></span></td>
        <td><span data-ttu-id="bfa98-140">Alcuni di apprendimento obbligatorio</span><span class="sxs-lookup"><span data-stu-id="bfa98-140">Some learning required</span></span><br><span data-ttu-id="bfa98-141">Se non sono disponibili le mani</span><span class="sxs-lookup"><span data-stu-id="bfa98-141">If hands are unavailable</span></span><br><span data-ttu-id="bfa98-142">coppie con vocali e il linguaggio naturale</span><span class="sxs-lookup"><span data-stu-id="bfa98-142">pairs well with voice and natural language</span></span></td>
        <td><span data-ttu-id="bfa98-143">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="bfa98-143">HoloLens 2</span></span><br><span data-ttu-id="bfa98-144">HoloLens (dal 1 ° generazione)</span><span class="sxs-lookup"><span data-stu-id="bfa98-144">HoloLens (1st gen)</span></span><br> <span data-ttu-id="bfa98-145">Coinvolgenti di Windows</span><span class="sxs-lookup"><span data-stu-id="bfa98-145">Windows Immersive</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="bfa98-146"><a href="gaze-and-commit.md">Head-sguardo ed eseguire il commit</a></span><span class="sxs-lookup"><span data-stu-id="bfa98-146"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="bfa98-147">Drill-through esperienze, ad esempio 3D presentazioni, demo</span><span class="sxs-lookup"><span data-stu-id="bfa98-147">Click-through experiences e.g. 3D presentations, demos</span></span></td>
        <td><span data-ttu-id="bfa98-148">Richiede la formazione su HMDs ma non su dispositivi mobili</span><span class="sxs-lookup"><span data-stu-id="bfa98-148">Requires training on HMDs but not on mobile</span></span><br><span data-ttu-id="bfa98-149">Ideale per i controller accessibili</span><span class="sxs-lookup"><span data-stu-id="bfa98-149">Best for accessible controllers</span></span><br><span data-ttu-id="bfa98-150">Ideale per HoloLens (dal 1 ° generazione)</span><span class="sxs-lookup"><span data-stu-id="bfa98-150">Best for HoloLens (1st gen)</span></span></td>
        <td><span data-ttu-id="bfa98-151">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="bfa98-151">HoloLens 2</span></span><br><span data-ttu-id="bfa98-152">HoloLens (dal 1 ° generazione)</span><span class="sxs-lookup"><span data-stu-id="bfa98-152">HoloLens (1st gen)</span></span><br> <span data-ttu-id="bfa98-153">Coinvolgenti di Windows</span><span class="sxs-lookup"><span data-stu-id="bfa98-153">Windows Immersive</span></span><br> <span data-ttu-id="bfa98-154">AR per dispositivi mobili</span><span class="sxs-lookup"><span data-stu-id="bfa98-154">Mobile AR</span></span></td>
    </tr>
</table>
<br>

<span data-ttu-id="bfa98-155">Il modo migliore per assicurarsi che non sono presenti gap o difetti nell'interazione per l'esperienza consiste nel seguire le linee guida per un singolo modello dall'inizio alla fine.</span><span class="sxs-lookup"><span data-stu-id="bfa98-155">The best way to ensure there are no gaps or holes in the interaction for your experience is to follow the guidance for a single model from beginning to end.</span></span> 

<span data-ttu-id="bfa98-156">Per aumentare la velocità di progettazione e sviluppo, sono state incluse informazioni dettagliate e collegamenti a esempi di codice e le immagini entro il code coverage di ogni modello.</span><span class="sxs-lookup"><span data-stu-id="bfa98-156">To speed design and development, we've included detailed information and links to images and code samples within our coverage of each model.</span></span>

<span data-ttu-id="bfa98-157">Ma prima di tutto le sezioni seguenti eseguire la procedura di selezione e implementazione di uno di questi modelli di interazione.</span><span class="sxs-lookup"><span data-stu-id="bfa98-157">But first, the sections below walk through the steps of selecting and implementing one of these interaction models.</span></span>  
 
### <a name="by-the-end-of-this-page-you-will-understand-our-guidance-on"></a><span data-ttu-id="bfa98-158">Al termine di questa pagina, è possibile comprendere le linee guida su:</span><span class="sxs-lookup"><span data-stu-id="bfa98-158">By the end of this page, you will understand our guidance on:</span></span>
 
* <span data-ttu-id="bfa98-159">Scelta di un modello di interazione per il cliente</span><span class="sxs-lookup"><span data-stu-id="bfa98-159">Choosing an interaction model for your customer</span></span>
* <span data-ttu-id="bfa98-160">Seguendo le indicazioni fornite del modello di interazione</span><span class="sxs-lookup"><span data-stu-id="bfa98-160">Using the interaction model guidance</span></span>
* <span data-ttu-id="bfa98-161">In fase di transizione tra i modelli di interazione</span><span class="sxs-lookup"><span data-stu-id="bfa98-161">Transitioning between interaction models</span></span>
* <span data-ttu-id="bfa98-162">Passaggi successivi di progettazione</span><span class="sxs-lookup"><span data-stu-id="bfa98-162">Design next steps</span></span>

## <a name="choosing-an-interaction-model-for-your-customer"></a><span data-ttu-id="bfa98-163">Scelta di un modello di interazione per il cliente</span><span class="sxs-lookup"><span data-stu-id="bfa98-163">Choosing an interaction model for your customer</span></span>

<span data-ttu-id="bfa98-164">È probabile che gli sviluppatori e autori già alcune idee mente i tipi di esperienza di interazione che per gli utenti desiderano.</span><span class="sxs-lookup"><span data-stu-id="bfa98-164">Most likely, developers and creators already have some ideas in mind of the kinds of interaction experience they want for their users.</span></span>
<span data-ttu-id="bfa98-165">Per favorire un approccio incentrato sul cliente alla progettazione, è consigliabile seguendo le indicazioni seguenti per selezionare il modello di interazione che è ottimizzato per il cliente.</span><span class="sxs-lookup"><span data-stu-id="bfa98-165">To encourage a customer-focused approach to design, we recommend following the guidance below to select the interaction model that's optimized for your customer.</span></span>

### <a name="why-follow-this-guidance"></a><span data-ttu-id="bfa98-166">Il motivo per cui segue questo materiale sussidiario?</span><span class="sxs-lookup"><span data-stu-id="bfa98-166">Why follow this guidance?</span></span>

* <span data-ttu-id="bfa98-167">I modelli di interazione vengono verificati i criteri soggettivi, ad esempio fisica e cognitiva sforzo e intuitiveness learnability e obiettivo.</span><span class="sxs-lookup"><span data-stu-id="bfa98-167">Our interaction models are tested for objective and subjective criteria such as physical and cognitive effort, intuitiveness, and learnability.</span></span> 
* <span data-ttu-id="bfa98-168">Interazione è diverso, audio e video affordance e comportamento di tali oggetti possono anche differire tra i modelli di interazione.</span><span class="sxs-lookup"><span data-stu-id="bfa98-168">Because interaction differs, visual and audio affordances and object behavior may also differ between the interaction models.</span></span>  
* <span data-ttu-id="bfa98-169">Combinando le parti più modelli di interazione crea il rischio di affordance concorrenti, ad esempio rays mano simultanei e un cursore sguardo, che sovraccaricare e confondere gli utenti.</span><span class="sxs-lookup"><span data-stu-id="bfa98-169">Combining parts of multiple interaction models together creates the risk of competing affordances, such as simultaneous hand rays and a gaze cursor, which overwhelm and confuse users.</span></span>

<span data-ttu-id="bfa98-170">Di seguito sono riportati alcuni esempi del modo in cui affordance e i comportamenti sono ottimizzati per ogni modello di interazione.</span><span class="sxs-lookup"><span data-stu-id="bfa98-170">Here are some examples of how affordances and behaviors are optimized for each interaction model.</span></span>  <span data-ttu-id="bfa98-171">È possibile notare spesso nuovi utenti come domande simili, ad esempio "come faccio a sapere il sistema funziona, come faccio a sapere che cosa può fare, e come si capisce se comprendere ciò che ho appena fatto?"</span><span class="sxs-lookup"><span data-stu-id="bfa98-171">We often see new users as similar questions, such as "how do I know the system is working, how do I know what I can do, and how do I know if it understood what I just did?"</span></span>

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="bfa98-172"><strong>Modello</strong></span><span class="sxs-lookup"><span data-stu-id="bfa98-172"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="bfa98-173"><strong>Come si capisce funziona?</strong></span><span class="sxs-lookup"><span data-stu-id="bfa98-173"><strong>How do I know it's working?</strong></span></span></td>
        <td><span data-ttu-id="bfa98-174"><strong>Come faccio a sapere che cosa posso fare?</strong></span><span class="sxs-lookup"><span data-stu-id="bfa98-174"><strong>How do I know what can I do?</strong></span></span></td>
        <td><span data-ttu-id="bfa98-175"><strong>Come sapere ciò che ho appena fatto?</strong></span><span class="sxs-lookup"><span data-stu-id="bfa98-175"><strong>How do I know what I just did?</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="bfa98-176"><a href="hands-and-tools.md">Strumenti e le mani</a></span><span class="sxs-lookup"><span data-stu-id="bfa98-176"><a href="hands-and-tools.md">Hands and tools</a></span></span></td>
        <td><span data-ttu-id="bfa98-177">Una mano mesh, vedere un intuitività punta del dito o manualmente / rays controller.</span><span class="sxs-lookup"><span data-stu-id="bfa98-177">I see a hand mesh, I see a fingertip affordance or hand/ controller rays.</span></span></td>
        <td><span data-ttu-id="bfa98-178">Viene visualizzato un riquadro vengono visualizzate quando la mano si avvicina o handle grabbable.</span><span class="sxs-lookup"><span data-stu-id="bfa98-178">I see grabbable handles or a bounding box appear when my hand is near.</span></span></td>
        <td><span data-ttu-id="bfa98-179">Posso sentire sonori e visualizzare animazioni in quadratini di ridimensionamento e il rilascio.</span><span class="sxs-lookup"><span data-stu-id="bfa98-179">I hear audible tones and see animations on grab and release.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="bfa98-180"><a href="gaze-and-commit.md">Head-sguardo ed eseguire il commit</a></span><span class="sxs-lookup"><span data-stu-id="bfa98-180"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="bfa98-181">Viene visualizzato un cursore al centro del mio campo visivo.</span><span class="sxs-lookup"><span data-stu-id="bfa98-181">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="bfa98-182">Il cursore sguardo Cambia stato quando su determinati oggetti.</span><span class="sxs-lookup"><span data-stu-id="bfa98-182">The gaze cursor changes state when over certain objects.</span></span></td>
        <td><span data-ttu-id="bfa98-183">Posso vedere o ascolta le conferme e acustico quando intervenire.</span><span class="sxs-lookup"><span data-stu-id="bfa98-183">I see/ hear visual and audible confirmations when I take action.</span></span></td>
    </tr>   
    <tr>
        <td><span data-ttu-id="bfa98-184"><a href="hands-free.md">Mani libere (sguardo e permanenza)</a></span><span class="sxs-lookup"><span data-stu-id="bfa98-184"><a href="hands-free.md">Hands-free (Gaze and dwell)</a></span></span></td>
        <td><span data-ttu-id="bfa98-185">Viene visualizzato un cursore al centro del mio campo visivo.</span><span class="sxs-lookup"><span data-stu-id="bfa98-185">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="bfa98-186">Viene visualizzato un indicatore di stato quando il caso di soffermarsi su un oggetto si.</span><span class="sxs-lookup"><span data-stu-id="bfa98-186">I see a progress indicator when I dwell on an interactable object.</span></span></td>
        <td><span data-ttu-id="bfa98-187">Posso vedere o ascolta le conferme e acustico quando intervenire.</span><span class="sxs-lookup"><span data-stu-id="bfa98-187">I see/ hear visual and audible confirmations when I take action.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="bfa98-188"><a href="hands-free.md">Mani libere (esecuzione di comandi vocali)</a></span><span class="sxs-lookup"><span data-stu-id="bfa98-188"><a href="hands-free.md">Hands-free (Voice commanding)</a></span></span></td>
        <td><span data-ttu-id="bfa98-189">Viene visualizzato un indicatore di attesa e sottotitoli in lingua originale che mostra ciò che il sistema sentito parlare.</span><span class="sxs-lookup"><span data-stu-id="bfa98-189">I see a listening indicator and captions that show what the system heard.</span></span></td>
        <td><span data-ttu-id="bfa98-190">Ricevo messaggi vocali e suggerimenti.</span><span class="sxs-lookup"><span data-stu-id="bfa98-190">I get voice prompts and hints.</span></span>  <span data-ttu-id="bfa98-191">Quando dico "frasi?"</span><span class="sxs-lookup"><span data-stu-id="bfa98-191">When I say "what can I say?"</span></span> <span data-ttu-id="bfa98-192">Vedere commenti e suggerimenti.</span><span class="sxs-lookup"><span data-stu-id="bfa98-192">I see feedback.</span></span></td>
        <td><span data-ttu-id="bfa98-193">Posso vedere o ascolta le conferme e acustico quando dà un comando o ottenere disambiguazione UX quando necessario.</span><span class="sxs-lookup"><span data-stu-id="bfa98-193">I see/ hear visual and audible confirmations when I give a command, or get disambiguation UX when needed.</span></span></a></td>
    </tr>
</table>

### <a name="below-are-the-questions-that-weve-found-help-teams-select-an-interaction-model"></a><span data-ttu-id="bfa98-194">Di seguito sono le domande che abbiamo scoperto help teams selezionare un modello di interazione:</span><span class="sxs-lookup"><span data-stu-id="bfa98-194">Below are the questions that we've found help teams select an interaction model:</span></span>
 
1.  <span data-ttu-id="bfa98-195">D:  Gli utenti desiderano touch ologrammi ed eseguono manipolazioni holographic precisione?</span><span class="sxs-lookup"><span data-stu-id="bfa98-195">Q:  Do my users want to touch holograms and perform precision holographic manipulations?</span></span>
<span data-ttu-id="bfa98-196">R:  In questo caso, consultare il modello di interazione mani e strumenti per la selezione della precisione e manipolazione con controller di movimento o mani.</span><span class="sxs-lookup"><span data-stu-id="bfa98-196">A:  If so, check out the Hands and Tools interaction model for precision targeting and manipulation with hands or motion controllers.</span></span>
 
2.  <span data-ttu-id="bfa98-197">D:  Gli utenti devono mantenere le mani gratuite, per le attività del mondo reale?</span><span class="sxs-lookup"><span data-stu-id="bfa98-197">Q:  Do my users need to keep their hands free, for real-world tasks?</span></span>
<span data-ttu-id="bfa98-198">R:  In questo caso, esaminare il modello di interazione invisibile all'utente, che offre un'esperienza ottimale invisibile all'utente tramite le interazioni basate su sguardo e vocali.</span><span class="sxs-lookup"><span data-stu-id="bfa98-198">A:  If so, take a look at the Hands-Free interaction model, which provides a great hands-free experience through gaze- and voice-based interactions.</span></span>
 
3.  <span data-ttu-id="bfa98-199">D:  Gli utenti devono imparare a utilizzare le interazioni per la mia applicazione di realtà mista, o devono le interazioni con la curva di apprendimento più bassa possibile?</span><span class="sxs-lookup"><span data-stu-id="bfa98-199">Q:  Do my users have time to learn interactions for my mixed reality application, or do they need the interactions with the lowest learning curve possible?</span></span>
<span data-ttu-id="bfa98-200">R:  È consigliabile il modello mani e strumenti per la curva di apprendimento più bassa e le interazioni più intuitive, purché siano in grado di usare le mani per l'interazione con gli utenti.</span><span class="sxs-lookup"><span data-stu-id="bfa98-200">A:  We recommend the Hands and Tools model for the lowest learning curve and most intuitive interactions, as long as users are able to use their hands for interaction.</span></span>
 
4.  <span data-ttu-id="bfa98-201">D:  Gli utenti usano i controller di movimento per la modifica e che puntano?</span><span class="sxs-lookup"><span data-stu-id="bfa98-201">Q:  Do my users use motion controllers for pointing and manipulation?</span></span>
<span data-ttu-id="bfa98-202">R:  Il modello di strumenti e le mani include tutte le linee guida per un'esperienza ottimale con i controller di movimento.</span><span class="sxs-lookup"><span data-stu-id="bfa98-202">A:  The Hands and Tools model includes all guidance for a great experience with motion controllers.</span></span>
 
5.  <span data-ttu-id="bfa98-203">D:  Gli utenti usano un controller di accessibilità o un controller Bluetooth comuni, ad esempio un clicker?</span><span class="sxs-lookup"><span data-stu-id="bfa98-203">Q:  Do my users use an accessibility controller or a common Bluetooth controller, such as a clicker?</span></span>
<span data-ttu-id="bfa98-204">R:  Si consiglia il modello Head sguardo ed eseguire il commit per tutti i controller non rilevate.</span><span class="sxs-lookup"><span data-stu-id="bfa98-204">A:  We recommend the Head-gaze and commit model for all non-tracked controllers.</span></span>  <span data-ttu-id="bfa98-205">È progettato per consentire a un utente attraversare un'intera esperienza con un semplice meccanico "target e commit".</span><span class="sxs-lookup"><span data-stu-id="bfa98-205">It's designed to allow a user to traverse an entire experience with a simple "target and commit" mechanic.</span></span> 
 
6.  <span data-ttu-id="bfa98-206">D: Gli utenti solo l'avanzamento viene eseguito tramite un'esperienza facendo clic su"tramite" (ad esempio in un ambiente simile a presentazione 3d), anziché passare ad alta densità layout dei controlli dell'interfaccia utente?</span><span class="sxs-lookup"><span data-stu-id="bfa98-206">Q: Do my users only progress through an experience by "clicking through" (for example in a 3d slideshow-like environment), as opposed to navigating dense layouts of UI controls?</span></span>
<span data-ttu-id="bfa98-207">R:  Se gli utenti non sono necessario controllare molti dell'interfaccia utente, Head sguardo ed eseguire il commit offrono un'opzione learnable in cui gli utenti non sono necessario preoccuparsi di destinazione.</span><span class="sxs-lookup"><span data-stu-id="bfa98-207">A:  If users do not need to control a lot of UI, Head-gaze and commit offers a learnable option where users do not have to worry about targeting.</span></span> 
 
7.  <span data-ttu-id="bfa98-208">D:  Gli utenti usano entrambi HoloLens (dal 1 ° generazione) e HoloLens 2 / r coinvolgenti di Windows (auricolari VR):  Poiché Head sguardo ed eseguire il commit è il modello di interazione per HoloLens (dal 1 ° generazione), è consigliabile che gli autori che supportano HoloLens (dal 1 ° generazione) usare Head sguardo ed eseguire il commit per qualsiasi funzionalità o le modalità che gli utenti potrebbero riscontrare in un HoloLens (dal 1 ° generazione) visore Vr.</span><span class="sxs-lookup"><span data-stu-id="bfa98-208">Q:  Do my users use both HoloLens (1st gen) and HoloLens 2/ Windows Immersive (VR headsets) A:  Since Head-gaze and commit is the interaction model for HoloLens (1st gen), we recommend that creators who support HoloLens (1st gen) use Head-gaze and commit for any features or modes that users may experience on a HoloLens (1st gen) headset.</span></span>  <span data-ttu-id="bfa98-209">Vedere la sezione seguente nel *modelli di interazione in fase di transizione* per informazioni dettagliate su come rendere una straordinaria esperienza più generazioni di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="bfa98-209">Please see the next section below on *Transitioning interaction models* for details on making a great experience for multiple HoloLens generations.</span></span>
 
8.  <span data-ttu-id="bfa98-210">D: Per quanto riguarda per gli utenti che sono in genere per dispositivi mobili relativi a uno spazio di grandi dimensioni o lo spostamento tra gli spazi, e gli utenti tendono a funzionare in uno spazio singolo?</span><span class="sxs-lookup"><span data-stu-id="bfa98-210">Q: What about for users who are generally mobile (covering a large space or moving between spaces), versus users who tend to work in a single space?</span></span>  
<span data-ttu-id="bfa98-211">R:  Uno dei modelli di interazione funzionerà per questi utenti.</span><span class="sxs-lookup"><span data-stu-id="bfa98-211">A:  Any of the interaction models will work for these users.</span></span>  

> [!NOTE]
> <span data-ttu-id="bfa98-212">Informazioni aggiuntive specifiche per la progettazione di app [presto](index.md#news-and-notes).</span><span class="sxs-lookup"><span data-stu-id="bfa98-212">More guidance specific to app design [coming soon](index.md#news-and-notes).</span></span>


## <a name="transition-interaction-models"></a><span data-ttu-id="bfa98-213">Modelli di interazione di transizione</span><span class="sxs-lookup"><span data-stu-id="bfa98-213">Transition interaction models</span></span>
<span data-ttu-id="bfa98-214">Vi sono anche casi in cui i casi d'uso richieda che utilizzano più di un modello di interazione.</span><span class="sxs-lookup"><span data-stu-id="bfa98-214">There are also cases where your use cases may require that utilizing more than one interaction model.</span></span>  <span data-ttu-id="bfa98-215">Ad esempio, il flusso di app"creazione" utilizza il modello di interazione mani e gli strumenti, ma si desidera utilizzare una modalità invisibile all'utente per i tecnici del campo.</span><span class="sxs-lookup"><span data-stu-id="bfa98-215">For example, your app's "creation flow" utilizes the Hands and tools interaction model, but you want to employ a Hands-free mode for field technicians.</span></span>  

<span data-ttu-id="bfa98-216">Se più modelli di interazione richiede l'esperienza, abbiamo scoperto che molti utenti finali potrebbero riscontrare difficoltà in fase di transizione da un modello a un'altra, in particolare gli utenti finali che hanno familiarità con MR.</span><span class="sxs-lookup"><span data-stu-id="bfa98-216">If your experience does require multiple interaction models, we've found that many end users may encounter difficulty transitioning from one model to another -- especially end users who are new to MR.</span></span>

> [!Note]
> <span data-ttu-id="bfa98-217">Per consentire le finestre di progettazione di Guida e gli sviluppatori attraverso le scelte che possono essere difficile in MR, stiamo lavorando su altre indicazioni per l'uso di più modelli di interazione.</span><span class="sxs-lookup"><span data-stu-id="bfa98-217">To help guide designers and developers through choices that can be difficult in MR, we're working on more guidance for using multiple interaction models.</span></span>
 

## <a name="see-also"></a><span data-ttu-id="bfa98-218">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="bfa98-218">See also</span></span>
* [<span data-ttu-id="bfa98-219">Head-sguardo ed eseguire il commit</span><span class="sxs-lookup"><span data-stu-id="bfa98-219">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="bfa98-220">Manipolazione diretta</span><span class="sxs-lookup"><span data-stu-id="bfa98-220">Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="bfa98-221">Punto e commit</span><span class="sxs-lookup"><span data-stu-id="bfa98-221">Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="bfa98-222">Selezione della destinazione con lo sguardo</span><span class="sxs-lookup"><span data-stu-id="bfa98-222">Gaze targeting</span></span>](gaze-targeting.md)
* [<span data-ttu-id="bfa98-223">Movimenti</span><span class="sxs-lookup"><span data-stu-id="bfa98-223">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="bfa98-224">Progettazione delle interazioni vocali</span><span class="sxs-lookup"><span data-stu-id="bfa98-224">Voice design</span></span>](voice-design.md)
* [<span data-ttu-id="bfa98-225">Controller del movimento</span><span class="sxs-lookup"><span data-stu-id="bfa98-225">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="bfa98-226">Progettazione dell'audio spaziale</span><span class="sxs-lookup"><span data-stu-id="bfa98-226">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="bfa98-227">Progettazione del mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="bfa98-227">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="bfa98-228">Comodità</span><span class="sxs-lookup"><span data-stu-id="bfa98-228">Comfort</span></span>](comfort.md)

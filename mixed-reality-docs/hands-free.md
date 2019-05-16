---
title: Senza mani
description: Ottimizzazione delle app per mani libere
author: liamar
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: Realtà mista, mani libere, estasiati, estasiati targeting, interazione, progettazione
ms.openlocfilehash: 59a460a0c46ace7e633381019d29af54b1061695
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629015"
---
# <a name="hands-free"></a><span data-ttu-id="ced70-104">Senza mani</span><span class="sxs-lookup"><span data-stu-id="ced70-104">Hands-free</span></span>



## <a name="scenarios"></a><span data-ttu-id="ced70-105">Scenari</span><span class="sxs-lookup"><span data-stu-id="ced70-105">Scenarios</span></span>

<span data-ttu-id="ced70-106">Come descritto nel [Cenni preliminari sul modello di interazione](interaction-fundamentals.md), una volta identificati gli utenti e i propri obiettivi, è opportuno porsi le sfide ambientali o di consapevolezza che possono verificarsi mentre lavorano per portare a termine le attività.</span><span class="sxs-lookup"><span data-stu-id="ced70-106">As outlined in the [interaction model overview](interaction-fundamentals.md), once you have identified the users and their goals, ask yourself what environmental or situational challenges they might face as they work to accomplish their tasks.</span></span> <span data-ttu-id="ced70-107">Ad esempio, necessario usare le mani realizzazione dei loro obiettivi reali che molti utenti con difficoltà l'interazione con un'interfaccia basata su mani e controller.</span><span class="sxs-lookup"><span data-stu-id="ced70-107">For example, many users need to use their hands to accomplish their real-world goals and will have difficulty interacting with a hands-and-controllers based interface.</span></span> 

<span data-ttu-id="ced70-108">Potrebbero essere alcuni scenari specifici:</span><span class="sxs-lookup"><span data-stu-id="ced70-108">Some specific scenarios might be:</span></span> 
* <span data-ttu-id="ced70-109">Viene guidato attraverso un'attività, mentre sono occupati</span><span class="sxs-lookup"><span data-stu-id="ced70-109">Being guided through a task, while hands are busy</span></span>
* <span data-ttu-id="ced70-110">Materiali di riferimento mentre le mani sono occupate</span><span class="sxs-lookup"><span data-stu-id="ced70-110">Referencing materials while your hands are busy</span></span>
* <span data-ttu-id="ced70-111">Ricordare di mano</span><span class="sxs-lookup"><span data-stu-id="ced70-111">Hand fatigue</span></span>
* <span data-ttu-id="ced70-112">Guanti che non possono essere rilevate</span><span class="sxs-lookup"><span data-stu-id="ced70-112">Gloves that can't be tracked</span></span>
* <span data-ttu-id="ced70-113">Esecuzione di un elemento</span><span class="sxs-lookup"><span data-stu-id="ced70-113">Carrying something</span></span>


## <a name="hands-free-modalities"></a><span data-ttu-id="ced70-114">Modalità invisibile all'utente</span><span class="sxs-lookup"><span data-stu-id="ced70-114">Hands-free modalities</span></span>

### <a name="voice-commandingvoice-designmd"></a>[<span data-ttu-id="ced70-115">L'esecuzione di comandi vocali</span><span class="sxs-lookup"><span data-stu-id="ced70-115">Voice commanding</span></span>](voice-design.md)

<span data-ttu-id="ced70-116">Utilizzando la voce di comando e controllo di che un'interfaccia può non solo consentono all'utente di operare in viva voce, ma anche ignorare più passaggi.</span><span class="sxs-lookup"><span data-stu-id="ced70-116">Using your voice to command and control an interface can not only allow the user to operate handsfree, but also skip multiple steps.</span></span> <span data-ttu-id="ced70-117">L'utilizzo di questa modalità può variare da consentire all'utente di nome del pulsante, qualsiasi operazione di lettura a voce alta per attivarlo, come vedere-it-say-it, alla conversazione con un agente che consentono di eseguire attività per l'utente.</span><span class="sxs-lookup"><span data-stu-id="ced70-117">The usage of this modality can range from allowing the user to simply reading any button's name out loud to activate it, as in See-it-say-it, to conversing with an agent who can accomplish tasks for you.</span></span>



### <a name="head-gaze-and-dwellgaze-and-dwellmd"></a>[<span data-ttu-id="ced70-118">Head-sguardo e permanenza</span><span class="sxs-lookup"><span data-stu-id="ced70-118">Head-gaze and dwell</span></span>](gaze-and-dwell.md)

<span data-ttu-id="ced70-119">In alcune situazioni invisibile all'utente, utilizzando la voce non è ideale o persino possibile.</span><span class="sxs-lookup"><span data-stu-id="ced70-119">In some hands-free situations, using your voice is not ideal or even possible.</span></span> <span data-ttu-id="ced70-120">Gli ambienti di factory l, sulla privacy o norme social possono essere tutti i vincoli.</span><span class="sxs-lookup"><span data-stu-id="ced70-120">Loud factory environments, privacy, or social norms can all be constraints.</span></span> <span data-ttu-id="ced70-121">Head estasiati + permanenza modello consente all'utente di spostarsi tra l'app usando il vettore head in modo da puntare, mentre il tempo di ritardo, o rimanere su un pulsante verrà attivarlo dopo un determinato periodo di tempo (in genere entro 1 secondo o operazione).</span><span class="sxs-lookup"><span data-stu-id="ced70-121">The head gaze + dwell model allows the user to navigate the app by using their head vector to point, while lingering, or dwelling on a button will activate it after a certain amount of time (typically around 1 second or so).</span></span> 


## <a name="transitioning-in-and-out-of-hands-free"></a><span data-ttu-id="ced70-122">In fase di transizione da e verso mani libere</span><span class="sxs-lookup"><span data-stu-id="ced70-122">Transitioning in and out of hands-free</span></span>

<span data-ttu-id="ced70-123">Per questi scenari, liberando le mani di interagire con vntana per l'esecuzione di comandi e l'esplorazione può variare da in corso di un requisito assoluto all'esecuzione dell'app, end-to-end, per praticità che l'utente può eseguire la transizione in e out di in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="ced70-123">For these scenarios, freeing your hands from interacting with holograms for commanding and navigation can range from being an absolute requirement to operating the app, end-to-end, to an added convenience that the user can transition in and out of at any time.</span></span> 

<span data-ttu-id="ced70-124">Se i requisiti dell'app verrà sempre utilizzata invisibile all'utente, utilizzando sia permanenza, comandi vocali o l'unico comando vocale, "select", quindi assicurarsi di prendere il accomodations appropriata nell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="ced70-124">If the requirement of the app is that it will always be used hands-free, whether by using dwell, voice commands, or the single voice command, "select", then make sure to make the appropriate accomodations in your UI.</span></span> 

<span data-ttu-id="ced70-125">Se l'utente di destinazione deve essere in grado di passare da mani a invisibile all'utente a propria discrezione, quindi è importante tenere conto di questi principi:</span><span class="sxs-lookup"><span data-stu-id="ced70-125">If your target user needs to be able to switch from hands to hands-free at their discretion, then it is important to take these principles into account:</span></span>

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a><span data-ttu-id="ced70-126">Si presuppone che l'utente è già in modalità che desiderano passare a</span><span class="sxs-lookup"><span data-stu-id="ced70-126">Assume the user is already in the mode that they want to switch to</span></span>
<span data-ttu-id="ced70-127">Ad esempio, se l'utente è nell'ambiente di produzione, guardare un video riferimento sul suo Hololens e decide di prelevare una chiave inglese per iniziare a lavorare, Anna molto probabilmente desidera iniziare a lavorare in viva voce senza la necessità di impostare la chiave inglese a premere un pulsante.</span><span class="sxs-lookup"><span data-stu-id="ced70-127">For instance, if your user is on the factory floor, watching a video reference on her Hololens, and decides to pick up a wrench to start working, she most likely would like to begin working in handsfree without having to put down the wrench to press a button.</span></span> <span data-ttu-id="ced70-128">Deve essere in grado di richiamare una sessione vocale con un comando vocale, il caso di soffermarsi su già visibili dell'interfaccia utente per iniziare a permanenza, o ad esempio la parola "select".</span><span class="sxs-lookup"><span data-stu-id="ced70-128">She should be able to invoke a voice session with a voice command, dwell on already-visible UI to begin dwell, or say the word "select".</span></span>

<span data-ttu-id="ced70-129">L'utente deve avere la possibilità di:</span><span class="sxs-lookup"><span data-stu-id="ced70-129">The user should have the ability to:</span></span> 
* <span data-ttu-id="ced70-130">Passare a in viva voce durante in viva voce</span><span class="sxs-lookup"><span data-stu-id="ced70-130">Switch to handsfree while handsfree</span></span>
* <span data-ttu-id="ced70-131">Passare a mani con le mani</span><span class="sxs-lookup"><span data-stu-id="ced70-131">Switch to hands with your hands</span></span>
* <span data-ttu-id="ced70-132">Passare al controller usando un controller</span><span class="sxs-lookup"><span data-stu-id="ced70-132">Switch to the controller using a controller</span></span> 

### <a name="create-redundant-ways-to-switch-modes"></a><span data-ttu-id="ced70-133">Creare metodi ridondanti per cambiare la modalità di</span><span class="sxs-lookup"><span data-stu-id="ced70-133">Create redundant ways to switch modes</span></span>
<span data-ttu-id="ced70-134">Mentre il principio del primo accesso, il secondo è sulla disponibilità.</span><span class="sxs-lookup"><span data-stu-id="ced70-134">While the first principle is about access, the second one is about availability.</span></span> <span data-ttu-id="ced70-135">Non vi non appena sarà un unico modo per eseguire la transizione da e verso una modalità.</span><span class="sxs-lookup"><span data-stu-id="ced70-135">There should not just be a single way to transition in and out of a mode.</span></span> 

<span data-ttu-id="ced70-136">Alcuni esempi sono:</span><span class="sxs-lookup"><span data-stu-id="ced70-136">Some examples would be:</span></span> 
* <span data-ttu-id="ced70-137">Un pulsante per avviare interazioni vocali</span><span class="sxs-lookup"><span data-stu-id="ced70-137">A button to begin voice interactions</span></span>
* <span data-ttu-id="ced70-138">Un comando vocali per la transizione all'utilizzo sguardo + permanenza</span><span class="sxs-lookup"><span data-stu-id="ced70-138">A voice command to transition to using gaze + dwell</span></span>

### <a name="add-a-dash-of-drama"></a><span data-ttu-id="ced70-139">Aggiungere un trattino di drammatico</span><span class="sxs-lookup"><span data-stu-id="ced70-139">Add a dash of drama</span></span>
<span data-ttu-id="ced70-140">Un interruttore è senz'altro un traguardo, è importante che quando si verificano queste transizioni, che tuttavia un'opzione esplicita, anche un significativo, per consentire all'utente di sapere che cosa è successo.</span><span class="sxs-lookup"><span data-stu-id="ced70-140">A mode switch is a big deal -- it is important that when these transitions happen, that they be an explicit, even dramatic switch, to let the user know what happened.</span></span> 


## <a name="usability-checklist"></a><span data-ttu-id="ced70-141">Elenco di controllo di usabilità</span><span class="sxs-lookup"><span data-stu-id="ced70-141">Usability checklist</span></span>

<span data-ttu-id="ced70-142">**L'utente può fare tutto e qualsiasi valore mani libere, end-to-end?**</span><span class="sxs-lookup"><span data-stu-id="ced70-142">**Can the user do everything and anything hands-free, end-to-end?**</span></span>
* <span data-ttu-id="ced70-143">Ogni interactible devono essere accessibili mani libere</span><span class="sxs-lookup"><span data-stu-id="ced70-143">Every interactible should be accessible hands-free</span></span>
* <span data-ttu-id="ced70-144">Verificare che sia presente una sostituzione per tutti i movimenti personalizzati, ad esempio il ridimensionamento, inserendo, tessere magnetiche, tap e così via.</span><span class="sxs-lookup"><span data-stu-id="ced70-144">Ensure that there is a replacement for all custom gestures, such as resizing, placing, swipes, taps, etc.</span></span>
* <span data-ttu-id="ced70-145">Assicurarsi che l'utente abbia certo controllo della presenza dell'interfaccia utente, posizione, il livello di dettaglio in qualsiasi momento</span><span class="sxs-lookup"><span data-stu-id="ced70-145">Ensure that the user has confident control of UI presence, placement, verbosity at all times</span></span>
    * <span data-ttu-id="ced70-146">Introduzione dell'interfaccia utente dall'area di lavoro</span><span class="sxs-lookup"><span data-stu-id="ced70-146">Getting UI out of the way</span></span>
    * <span data-ttu-id="ced70-147">Interfaccia utente di indirizzamento fuori campo visualizzazione)</span><span class="sxs-lookup"><span data-stu-id="ced70-147">Addressing UI that is out of field of view (FOV)</span></span>
    * <span data-ttu-id="ced70-148">Quanto viene visualizzato, dove e quando</span><span class="sxs-lookup"><span data-stu-id="ced70-148">How much I see, where, when</span></span>

<span data-ttu-id="ced70-149">**Vengono tenuti e consolidati con i destro affordance i meccanismi dell'interazione?**</span><span class="sxs-lookup"><span data-stu-id="ced70-149">**Are the mechanics of the interaction being taught and reinforced with the right affordances?**</span></span>

<span data-ttu-id="ced70-150">L'utente comprensione...</span><span class="sxs-lookup"><span data-stu-id="ced70-150">Does the user understand ...</span></span>
* <span data-ttu-id="ced70-151">... Quali modalità si trovano in?</span><span class="sxs-lookup"><span data-stu-id="ced70-151">... What mode they are in?</span></span>
* <span data-ttu-id="ced70-152">... Le operazioni consentite in questa modalità?</span><span class="sxs-lookup"><span data-stu-id="ced70-152">... What they can do in this mode?</span></span>
* <span data-ttu-id="ced70-153">... Che cos'è lo stato corrente?</span><span class="sxs-lookup"><span data-stu-id="ced70-153">... What is the current state?</span></span>
* <span data-ttu-id="ced70-154">... Come è possibile eseguire la transizione?</span><span class="sxs-lookup"><span data-stu-id="ced70-154">... How they can transition out?</span></span>
    
<span data-ttu-id="ced70-155">**L'interfaccia utente ottimizzata per invisibile all'utente?**</span><span class="sxs-lookup"><span data-stu-id="ced70-155">**Is the UI optimized for hands-free?**</span></span>   

* <span data-ttu-id="ced70-156">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="ced70-156">Ex.</span></span> <span data-ttu-id="ced70-157">Permanenza affordance non sono incorporati ai tipici modelli 2D</span><span class="sxs-lookup"><span data-stu-id="ced70-157">Dwell affordances are not built-in to typical 2D patterns</span></span>
* <span data-ttu-id="ced70-158">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="ced70-158">Ex.</span></span> <span data-ttu-id="ced70-159">Destinati Voice è migliore con l'evidenziazione di oggetto</span><span class="sxs-lookup"><span data-stu-id="ced70-159">Voice targeting is better with object highlighting</span></span>
* <span data-ttu-id="ced70-160">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="ced70-160">Ex.</span></span> <span data-ttu-id="ced70-161">Le interazioni vocali sono preferibili con sottotitoli in lingua originale che dovranno essere attivata</span><span class="sxs-lookup"><span data-stu-id="ced70-161">Voice interactions are better with captions that have to be turned on</span></span>


## <a name="see-also"></a><span data-ttu-id="ced70-162">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ced70-162">See also</span></span>
* [<span data-ttu-id="ced70-163">Puntamento con la testa e commit</span><span class="sxs-lookup"><span data-stu-id="ced70-163">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="ced70-164">Manipolazione diretta</span><span class="sxs-lookup"><span data-stu-id="ced70-164">Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="ced70-165">Puntamento e commit</span><span class="sxs-lookup"><span data-stu-id="ced70-165">Point and commit</span></span>](point-and-commit.md)

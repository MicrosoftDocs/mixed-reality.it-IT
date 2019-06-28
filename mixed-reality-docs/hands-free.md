---
title: Senza mani
description: Ottimizzazione delle app per mani libere
author: liamar
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: Realtà mista, mani libere, estasiati, estasiati targeting, interazione, progettazione
ms.openlocfilehash: 7942192f644a7133335f089cfaaccfaebdd9292e
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414388"
---
# <a name="hands-free"></a><span data-ttu-id="087d2-104">Senza mani</span><span class="sxs-lookup"><span data-stu-id="087d2-104">Hands-free</span></span>



## <a name="scenarios"></a><span data-ttu-id="087d2-105">Scenari</span><span class="sxs-lookup"><span data-stu-id="087d2-105">Scenarios</span></span>

<span data-ttu-id="087d2-106">Come descritto nel [Cenni preliminari sul modello di interazione](interaction-fundamentals.md), una volta identificati gli utenti e i propri obiettivi, è opportuno porsi le sfide ambientali o di consapevolezza che possono verificarsi mentre lavorano per portare a termine le attività.</span><span class="sxs-lookup"><span data-stu-id="087d2-106">As outlined in the [Interaction model overview](interaction-fundamentals.md), once you have identified the users and their goals, ask yourself what environmental or situational challenges they might face as they work to accomplish their tasks.</span></span> <span data-ttu-id="087d2-107">Ad esempio, molti utenti è necessario usare le mani per eseguire i propri obiettivi del mondo reale e sarà difficile l'interazione con un'interfaccia basata su mani e controller.</span><span class="sxs-lookup"><span data-stu-id="087d2-107">For example, many users need to use their hands to accomplish their real-world goals, and will have difficulty interacting with a hands-and-controllers based interface.</span></span> 

<span data-ttu-id="087d2-108">Potrebbero essere alcuni scenari specifici:</span><span class="sxs-lookup"><span data-stu-id="087d2-108">Some specific scenarios might be:</span></span> 
* <span data-ttu-id="087d2-109">Viene guidato attraverso un'attività, mentre sono occupati</span><span class="sxs-lookup"><span data-stu-id="087d2-109">Being guided through a task, while hands are busy</span></span>
* <span data-ttu-id="087d2-110">Materiali di riferimento mentre le mani sono occupate</span><span class="sxs-lookup"><span data-stu-id="087d2-110">Referencing materials while your hands are busy</span></span>
* <span data-ttu-id="087d2-111">Ricordare di mano</span><span class="sxs-lookup"><span data-stu-id="087d2-111">Hand fatigue</span></span>
* <span data-ttu-id="087d2-112">Guanti che non possono essere rilevate</span><span class="sxs-lookup"><span data-stu-id="087d2-112">Gloves that can't be tracked</span></span>
* <span data-ttu-id="087d2-113">Esecuzione di un elemento</span><span class="sxs-lookup"><span data-stu-id="087d2-113">Carrying something</span></span>


## <a name="hands-free-modalities"></a><span data-ttu-id="087d2-114">Modalità invisibile all'utente</span><span class="sxs-lookup"><span data-stu-id="087d2-114">Hands-free modalities</span></span>

### <a name="voice-commandingvoice-designmd"></a>[<span data-ttu-id="087d2-115">Esecuzione di comandi vocali</span><span class="sxs-lookup"><span data-stu-id="087d2-115">Voice commanding</span></span>](voice-design.md)

<span data-ttu-id="087d2-116">Utilizzando la voce di comando e controllo di che un'interfaccia può non solo consentono all'utente di operare in viva voce, ma anche ignorare più passaggi.</span><span class="sxs-lookup"><span data-stu-id="087d2-116">Using your voice to command and control an interface can not only allow the user to operate handsfree, but also skip multiple steps.</span></span> <span data-ttu-id="087d2-117">L'utilizzo di questa modalità può variare da consentire all'utente di leggere semplicemente il nome di un pulsante qualsiasi a voce alta per attivarlo, come vedere-it-say-it, alla conversazione con un agente che consentono di eseguire attività per l'utente.</span><span class="sxs-lookup"><span data-stu-id="087d2-117">The usage of this modality can range from allowing the user to simply read any button's name out loud to activate it, as in See-it-say-it, to conversing with an agent who can accomplish tasks for you.</span></span>



### <a name="head-gaze-and-dwellgaze-and-dwellmd"></a>[<span data-ttu-id="087d2-118">Puntamento con la testa e attesa</span><span class="sxs-lookup"><span data-stu-id="087d2-118">Head-gaze and dwell</span></span>](gaze-and-dwell.md)

<span data-ttu-id="087d2-119">In alcune situazioni invisibile all'utente, utilizzando la voce non è ideale o persino possibile.</span><span class="sxs-lookup"><span data-stu-id="087d2-119">In some hands-free situations, using your voice is not ideal or even possible.</span></span> <span data-ttu-id="087d2-120">Gli ambienti di factory l, sulla privacy o norme social possono essere tutti i vincoli.</span><span class="sxs-lookup"><span data-stu-id="087d2-120">Loud factory environments, privacy, or social norms can all be constraints.</span></span> <span data-ttu-id="087d2-121">Head estasiati + permanenza modello consente all'utente di spostarsi tra l'app usando il vettore head in modo da puntare, mentre il tempo di ritardo, o rimanere su un pulsante verrà attivarlo dopo un determinato periodo di tempo, in genere entro 1 secondo o operazione.</span><span class="sxs-lookup"><span data-stu-id="087d2-121">The head gaze + dwell model allows the user to navigate the app by using their head vector to point, while lingering, or dwelling on a button will activate it after a certain amount of time, typically around 1 second or so.</span></span> 


## <a name="transitioning-in-and-out-of-hands-free"></a><span data-ttu-id="087d2-122">In fase di transizione da e verso mani libere</span><span class="sxs-lookup"><span data-stu-id="087d2-122">Transitioning in and out of hands-free</span></span>

<span data-ttu-id="087d2-123">Per questi scenari, liberando le mani di interagire con vntana per l'esecuzione di comandi e la navigazione può essere compreso tra da un requisito assoluto all'esecuzione dell'applicazione, end-to-end, per praticità che l'utente può eseguire la transizione in e out di in corrispondenza di qualsiasi ora.</span><span class="sxs-lookup"><span data-stu-id="087d2-123">For these scenarios, freeing your hands from interacting with holograms for commanding and navigation can range from being an absolute requirement to operating the application, end-to-end, to an added convenience that the user can transition in and out of at any time.</span></span> 

<span data-ttu-id="087d2-124">Se i requisiti dell'applicazione verrà sempre utilizzato invisibile all'utente, utilizzando sia permanenza, comandi vocali o l'unico comando vocale, "select", quindi assicurarsi di prendere il accomodations appropriata nell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="087d2-124">If the requirement of the application is that it will always be used hands-free, whether by using dwell, voice commands, or the single voice command, "select", then make sure to make the appropriate accomodations in your UI.</span></span> 

<span data-ttu-id="087d2-125">Se l'utente di destinazione deve essere in grado di passare da mani a invisibile all'utente a propria discrezione, quindi è importante considerare i seguenti principi.</span><span class="sxs-lookup"><span data-stu-id="087d2-125">If your target user needs to be able to switch from hands to hands-free at their discretion, then it is important to take the following principles into account.</span></span>

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a><span data-ttu-id="087d2-126">Si presuppone che l'utente è già in modalità che desiderano passare a</span><span class="sxs-lookup"><span data-stu-id="087d2-126">Assume the user is already in the mode that they want to switch to</span></span>
<span data-ttu-id="087d2-127">Ad esempio, se l'utente è nell'ambiente di produzione, guardare un video riferimento sul suo Hololens e decide di prelevare una chiave inglese per iniziare a lavorare, Anna molto probabilmente verrebbe iniziare a lavorare in viva voce senza la necessità di impostare la chiave inglese a premere un pulsante.</span><span class="sxs-lookup"><span data-stu-id="087d2-127">For instance, if the user is on the factory floor, watching a video reference on her Hololens, and decides to pick up a wrench to start working, she most likely would start working in handsfree without having to put down the wrench to press a button.</span></span> <span data-ttu-id="087d2-128">Deve essere in grado di richiamare una sessione vocale con un comando vocale, il caso di soffermarsi su un'interfaccia utente già visibili per iniziare a permanenza, o ad esempio la parola "select".</span><span class="sxs-lookup"><span data-stu-id="087d2-128">She should be able to invoke a voice session with a voice command, dwell on an already-visible UI to begin dwell, or say the word "select".</span></span>

<span data-ttu-id="087d2-129">L'utente deve avere la possibilità di:</span><span class="sxs-lookup"><span data-stu-id="087d2-129">The user should have the ability to:</span></span> 
* <span data-ttu-id="087d2-130">Passa a mani libere mentre mani libere</span><span class="sxs-lookup"><span data-stu-id="087d2-130">Switch to hands-free while hands-free</span></span>
* <span data-ttu-id="087d2-131">Passare a mani con le mani</span><span class="sxs-lookup"><span data-stu-id="087d2-131">Switch to hands with your hands</span></span>
* <span data-ttu-id="087d2-132">Passare al controller usando un controller</span><span class="sxs-lookup"><span data-stu-id="087d2-132">Switch to the controller using a controller</span></span> 

### <a name="create-redundant-ways-to-switch-modes"></a><span data-ttu-id="087d2-133">Creare metodi ridondanti per cambiare la modalità di</span><span class="sxs-lookup"><span data-stu-id="087d2-133">Create redundant ways to switch modes</span></span>
<span data-ttu-id="087d2-134">Mentre il principio del primo accesso, il secondo è sulla disponibilità.</span><span class="sxs-lookup"><span data-stu-id="087d2-134">While the first principle is about access, the second one is about availability.</span></span> <span data-ttu-id="087d2-135">Non vi non appena sarà un unico modo per eseguire la transizione da e verso una modalità.</span><span class="sxs-lookup"><span data-stu-id="087d2-135">There should not just be a single way to transition in and out of a mode.</span></span> 

<span data-ttu-id="087d2-136">Alcuni esempi sono:</span><span class="sxs-lookup"><span data-stu-id="087d2-136">Some examples would be:</span></span> 
* <span data-ttu-id="087d2-137">Un pulsante per avviare interazioni vocali</span><span class="sxs-lookup"><span data-stu-id="087d2-137">A button to begin voice interactions</span></span>
* <span data-ttu-id="087d2-138">Un comando vocali per la transizione all'utilizzo sguardo + permanenza</span><span class="sxs-lookup"><span data-stu-id="087d2-138">A voice command to transition to using gaze + dwell</span></span>

### <a name="add-a-dash-of-drama"></a><span data-ttu-id="087d2-139">Aggiungere un trattino di drammatico</span><span class="sxs-lookup"><span data-stu-id="087d2-139">Add a dash of drama</span></span>
<span data-ttu-id="087d2-140">Un interruttore è molto importante, è importante che quando si verificano queste transizioni che tuttavia un'opzione esplicita, anche un significativo, per consentire all'utente di sapere che cosa è successo.</span><span class="sxs-lookup"><span data-stu-id="087d2-140">A mode switch is a big deal--it is important that when these transitions happen that they be an explicit, even dramatic switch, to let the user know what happened.</span></span> 


## <a name="usability-checklist"></a><span data-ttu-id="087d2-141">Elenco di controllo di usabilità</span><span class="sxs-lookup"><span data-stu-id="087d2-141">Usability checklist</span></span>

<span data-ttu-id="087d2-142">**L'utente può fare tutto e qualsiasi valore mani libere, end-to-end?**</span><span class="sxs-lookup"><span data-stu-id="087d2-142">**Can the user do everything and anything hands-free, end-to-end?**</span></span>
* <span data-ttu-id="087d2-143">Ogni interactible devono essere accessibili mani libere</span><span class="sxs-lookup"><span data-stu-id="087d2-143">Every interactible should be accessible hands-free</span></span>
* <span data-ttu-id="087d2-144">Verificare che sia presente una sostituzione per tutti i movimenti personalizzati, ad esempio il ridimensionamento, inserendo, tessere magnetiche, tap e così via.</span><span class="sxs-lookup"><span data-stu-id="087d2-144">Ensure that there is a replacement for all custom gestures, such as resizing, placing, swipes, taps, etc.</span></span>
* <span data-ttu-id="087d2-145">Assicurarsi che l'utente abbia certo controllo della presenza dell'interfaccia utente, posizione e livello di dettaglio in qualsiasi momento</span><span class="sxs-lookup"><span data-stu-id="087d2-145">Ensure that the user has confident control of UI presence, placement, and verbosity at all times</span></span>
    * <span data-ttu-id="087d2-146">Introduzione dell'interfaccia utente dall'area di lavoro</span><span class="sxs-lookup"><span data-stu-id="087d2-146">Getting UI out of the way</span></span>
    * <span data-ttu-id="087d2-147">Interfaccia utente di indirizzamento fuori campo visualizzazione)</span><span class="sxs-lookup"><span data-stu-id="087d2-147">Addressing UI that is out of field of view (FOV)</span></span>
    * <span data-ttu-id="087d2-148">Quanto viene visualizzato, dove e quando</span><span class="sxs-lookup"><span data-stu-id="087d2-148">How much I see, where, when</span></span>

<span data-ttu-id="087d2-149">**Vengono tenuti e consolidati con i destro affordance i meccanismi dell'interazione?**</span><span class="sxs-lookup"><span data-stu-id="087d2-149">**Are the mechanics of the interaction being taught and reinforced with the right affordances?**</span></span>

<span data-ttu-id="087d2-150">L'utente comprensione...</span><span class="sxs-lookup"><span data-stu-id="087d2-150">Does the user understand ...</span></span>
* <span data-ttu-id="087d2-151">... Quali modalità si trovano in?</span><span class="sxs-lookup"><span data-stu-id="087d2-151">... What mode they are in?</span></span>
* <span data-ttu-id="087d2-152">... Le operazioni consentite in questa modalità?</span><span class="sxs-lookup"><span data-stu-id="087d2-152">... What they can do in this mode?</span></span>
* <span data-ttu-id="087d2-153">... Che cos'è lo stato corrente?</span><span class="sxs-lookup"><span data-stu-id="087d2-153">... What is the current state?</span></span>
* <span data-ttu-id="087d2-154">... Come è possibile eseguire la transizione?</span><span class="sxs-lookup"><span data-stu-id="087d2-154">... How they can transition out?</span></span>
    
<span data-ttu-id="087d2-155">**L'interfaccia utente ottimizzata per invisibile all'utente?**</span><span class="sxs-lookup"><span data-stu-id="087d2-155">**Is the UI optimized for hands-free?**</span></span>   

* <span data-ttu-id="087d2-156">Esempio: Permanenza affordance non sono incorporati ai tipici modelli 2D</span><span class="sxs-lookup"><span data-stu-id="087d2-156">Example: Dwell affordances are not built-in to typical 2D patterns</span></span>
* <span data-ttu-id="087d2-157">Esempio: Destinati Voice è migliore con l'evidenziazione di oggetto</span><span class="sxs-lookup"><span data-stu-id="087d2-157">Example: Voice targeting is better with object highlighting</span></span>
* <span data-ttu-id="087d2-158">Esempio: Le interazioni vocali sono preferibili con sottotitoli in lingua originale che dovranno essere attivata</span><span class="sxs-lookup"><span data-stu-id="087d2-158">Example: Voice interactions are better with captions that have to be turned on</span></span>


## <a name="see-also"></a><span data-ttu-id="087d2-159">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="087d2-159">See also</span></span>
* [<span data-ttu-id="087d2-160">Puntamento con la testa e commit</span><span class="sxs-lookup"><span data-stu-id="087d2-160">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="087d2-161">Manipolazione diretta con le mani</span><span class="sxs-lookup"><span data-stu-id="087d2-161">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="087d2-162">Puntamento e commit con le mani</span><span class="sxs-lookup"><span data-stu-id="087d2-162">Point and commit with hands</span></span>](point-and-commit.md)

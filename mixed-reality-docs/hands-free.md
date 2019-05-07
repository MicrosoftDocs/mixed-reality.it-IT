---
title: Ottimizzazione delle app per mani libere
description: Ottimizzazione delle app per mani libere
author: liamar
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: Realtà mista, mani libere, estasiati, estasiati targeting, interazione, progettazione
ms.openlocfilehash: b64dec802d8ed2886021a54f302ba4a948c4f5b9
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2019
ms.locfileid: "64581031"
---
# <a name="optimizing-your-app-for-hands-free"></a><span data-ttu-id="524cb-104">Ottimizzazione delle app per mani libere</span><span class="sxs-lookup"><span data-stu-id="524cb-104">Optimizing your app for hands-free</span></span>



## <a name="scenarios"></a><span data-ttu-id="524cb-105">Scenari</span><span class="sxs-lookup"><span data-stu-id="524cb-105">Scenarios</span></span>

<span data-ttu-id="524cb-106">Come descritto nel [Cenni preliminari sul modello di interazione](interaction-fundamentals.md), una volta identificati gli utenti e i propri obiettivi, è opportuno porsi le sfide ambientali o di consapevolezza che possono verificarsi mentre lavorano per portare a termine le attività.</span><span class="sxs-lookup"><span data-stu-id="524cb-106">As outlined in the [interaction model overview](interaction-fundamentals.md), once you have identified the users and their goals, ask yourself what environmental or situational challenges they might face as they work to accomplish their tasks.</span></span> <span data-ttu-id="524cb-107">Ad esempio, necessario usare le mani realizzazione dei loro obiettivi reali che molti utenti con difficoltà l'interazione con un'interfaccia basata su mani e controller.</span><span class="sxs-lookup"><span data-stu-id="524cb-107">For example, many users need to use their hands to accomplish their real-world goals and will have difficulty interacting with a hands-and-controllers based interface.</span></span> 

<span data-ttu-id="524cb-108">Potrebbero essere alcuni scenari specifici:</span><span class="sxs-lookup"><span data-stu-id="524cb-108">Some specific scenarios might be:</span></span> 
* <span data-ttu-id="524cb-109">Viene guidato attraverso un'attività, mentre sono occupati</span><span class="sxs-lookup"><span data-stu-id="524cb-109">Being guided through a task, while hands are busy</span></span>
* <span data-ttu-id="524cb-110">Materiali di riferimento mentre le mani sono occupate</span><span class="sxs-lookup"><span data-stu-id="524cb-110">Referencing materials while your hands are busy</span></span>
* <span data-ttu-id="524cb-111">Ricordare di mano</span><span class="sxs-lookup"><span data-stu-id="524cb-111">Hand fatigue</span></span>
* <span data-ttu-id="524cb-112">Guanti che non possono essere rilevate</span><span class="sxs-lookup"><span data-stu-id="524cb-112">Gloves that can't be tracked</span></span>
* <span data-ttu-id="524cb-113">Esecuzione di un elemento</span><span class="sxs-lookup"><span data-stu-id="524cb-113">Carrying something</span></span>


## <a name="hands-free-modalities"></a><span data-ttu-id="524cb-114">Modalità invisibile all'utente</span><span class="sxs-lookup"><span data-stu-id="524cb-114">Hands-free modalities</span></span>

### <a name="voice-commanding"></a><span data-ttu-id="524cb-115">L'esecuzione di comandi vocali</span><span class="sxs-lookup"><span data-stu-id="524cb-115">Voice commanding</span></span>

<span data-ttu-id="524cb-116">Utilizzando la voce di comando e controllo di che un'interfaccia può non solo consentono all'utente di operare in viva voce, ma anche ignorare più passaggi.</span><span class="sxs-lookup"><span data-stu-id="524cb-116">Using your voice to command and control an interface can not only allow the user to operate handsfree, but also skip multiple steps.</span></span> <span data-ttu-id="524cb-117">L'utilizzo di questa modalità può variare da consentire all'utente di nome del pulsante, qualsiasi operazione di lettura a voce alta per attivarlo, come vedere-it-say-it, alla conversazione con un agente che consentono di eseguire attività per l'utente.</span><span class="sxs-lookup"><span data-stu-id="524cb-117">The usage of this modality can range from allowing the user to simply reading any button's name out loud to activate it, as in See-it-say-it, to conversing with an agent who can accomplish tasks for you.</span></span>

* [<span data-ttu-id="524cb-118">Progettazione delle interazioni vocali</span><span class="sxs-lookup"><span data-stu-id="524cb-118">Voice design</span></span>](voice-design.md)


### <a name="head-gaze-and-dwell"></a><span data-ttu-id="524cb-119">Head sguardo e permanenza</span><span class="sxs-lookup"><span data-stu-id="524cb-119">Head gaze and dwell</span></span>

<span data-ttu-id="524cb-120">In alcune situazioni invisibile all'utente, utilizzando la voce non è ideale o persino possibile.</span><span class="sxs-lookup"><span data-stu-id="524cb-120">In some hands-free situations, using your voice is not ideal or even possible.</span></span> <span data-ttu-id="524cb-121">Gli ambienti di factory l, sulla privacy o norme social possono essere tutti i vincoli.</span><span class="sxs-lookup"><span data-stu-id="524cb-121">Loud factory environments, privacy, or social norms can all be constraints.</span></span> <span data-ttu-id="524cb-122">Head estasiati + permanenza modello consente all'utente di spostarsi tra l'app usando il vettore head in modo da puntare, mentre il tempo di ritardo, o rimanere su un pulsante verrà attivarlo dopo un determinato periodo di tempo (in genere entro 1 secondo o operazione).</span><span class="sxs-lookup"><span data-stu-id="524cb-122">The head gaze + dwell model allows the user to navigate the app by using their head vector to point, while lingering, or dwelling on a button will activate it after a certain amount of time (typically around 1 second or so).</span></span> 

* [<span data-ttu-id="524cb-123">Sguardo e permanenza</span><span class="sxs-lookup"><span data-stu-id="524cb-123">Gaze and dwell</span></span>](gaze-and-dwell.md)

## <a name="transitioning-in-and-out-of-hands-free"></a><span data-ttu-id="524cb-124">In fase di transizione da e verso mani libere</span><span class="sxs-lookup"><span data-stu-id="524cb-124">Transitioning in and out of hands-free</span></span>

<span data-ttu-id="524cb-125">Per questi scenari, liberando le mani di interagire con vntana per l'esecuzione di comandi e l'esplorazione può variare da in corso di un requisito assoluto all'esecuzione dell'app, end-to-end, per praticità che l'utente può eseguire la transizione in e out di in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="524cb-125">For these scenarios, freeing your hands from interacting with holograms for commanding and navigation can range from being an absolute requirement to operating the app, end-to-end, to an added convenience that the user can transition in and out of at any time.</span></span> 

<span data-ttu-id="524cb-126">Se i requisiti dell'app verrà sempre utilizzata invisibile all'utente, utilizzando sia permanenza, comandi vocali o l'unico comando vocale, "select", quindi assicurarsi di prendere il accomodations appropriata nell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="524cb-126">If the requirement of the app is that it will always be used hands-free, whether by using dwell, voice commands, or the single voice command, "select", then make sure to make the appropriate accomodations in your UI.</span></span> 

<span data-ttu-id="524cb-127">Se l'utente di destinazione deve essere in grado di passare da mani a invisibile all'utente a propria discrezione, quindi è importante tenere conto di questi principi:</span><span class="sxs-lookup"><span data-stu-id="524cb-127">If your target user needs to be able to switch from hands to hands-free at their discretion, then it is important to take these principles into account:</span></span>

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a><span data-ttu-id="524cb-128">Si presuppone che l'utente è già in modalità che desiderano passare a</span><span class="sxs-lookup"><span data-stu-id="524cb-128">Assume the user is already in the mode that they want to switch to</span></span>
<span data-ttu-id="524cb-129">Ad esempio, se l'utente è nell'ambiente di produzione, guardare un video riferimento sul suo Hololens e decide di prelevare una chiave inglese per iniziare a lavorare, Anna molto probabilmente desidera iniziare a lavorare in viva voce senza la necessità di impostare la chiave inglese a premere un pulsante.</span><span class="sxs-lookup"><span data-stu-id="524cb-129">For instance, if your user is on the factory floor, watching a video reference on her Hololens, and decides to pick up a wrench to start working, she most likely would like to begin working in handsfree without having to put down the wrench to press a button.</span></span> <span data-ttu-id="524cb-130">Deve essere in grado di richiamare una sessione vocale con un comando vocale, il caso di soffermarsi su già visibili dell'interfaccia utente per iniziare a permanenza, o ad esempio la parola "select".</span><span class="sxs-lookup"><span data-stu-id="524cb-130">She should be able to invoke a voice session with a voice command, dwell on already-visible UI to begin dwell, or say the word "select".</span></span>

<span data-ttu-id="524cb-131">L'utente deve avere la possibilità di:</span><span class="sxs-lookup"><span data-stu-id="524cb-131">The user should have the ability to:</span></span> 
* <span data-ttu-id="524cb-132">Passare a in viva voce durante in viva voce</span><span class="sxs-lookup"><span data-stu-id="524cb-132">Switch to handsfree while handsfree</span></span>
* <span data-ttu-id="524cb-133">Passare a mani con le mani</span><span class="sxs-lookup"><span data-stu-id="524cb-133">Switch to hands with your hands</span></span>
* <span data-ttu-id="524cb-134">Passare al controller usando un controller</span><span class="sxs-lookup"><span data-stu-id="524cb-134">Switch to the controller using a controller</span></span> 

### <a name="create-redundant-ways-to-switch-modes"></a><span data-ttu-id="524cb-135">Creare metodi ridondanti per cambiare la modalità di</span><span class="sxs-lookup"><span data-stu-id="524cb-135">Create redundant ways to switch modes</span></span>
<span data-ttu-id="524cb-136">Mentre il principio del primo accesso, il secondo è sulla disponibilità.</span><span class="sxs-lookup"><span data-stu-id="524cb-136">While the first principle is about access, the second one is about availability.</span></span> <span data-ttu-id="524cb-137">Non vi non appena sarà un unico modo per eseguire la transizione da e verso una modalità.</span><span class="sxs-lookup"><span data-stu-id="524cb-137">There should not just be a single way to transition in and out of a mode.</span></span> 

<span data-ttu-id="524cb-138">Alcuni esempi sono:</span><span class="sxs-lookup"><span data-stu-id="524cb-138">Some examples would be:</span></span> 
* <span data-ttu-id="524cb-139">Un pulsante per avviare interazioni vocali</span><span class="sxs-lookup"><span data-stu-id="524cb-139">A button to begin voice interactions</span></span>
* <span data-ttu-id="524cb-140">Un comando vocali per la transizione all'utilizzo sguardo + permanenza</span><span class="sxs-lookup"><span data-stu-id="524cb-140">A voice command to transition to using gaze + dwell</span></span>

### <a name="add-a-dash-of-drama"></a><span data-ttu-id="524cb-141">Aggiungere un trattino di drammatico</span><span class="sxs-lookup"><span data-stu-id="524cb-141">Add a dash of drama</span></span>
<span data-ttu-id="524cb-142">Un interruttore è senz'altro un traguardo, è importante che quando si verificano queste transizioni, che tuttavia un'opzione esplicita, anche un significativo, per consentire all'utente di sapere che cosa è successo.</span><span class="sxs-lookup"><span data-stu-id="524cb-142">A mode switch is a big deal -- it is important that when these transitions happen, that they be an explicit, even dramatic switch, to let the user know what happened.</span></span> 


## <a name="usability-checklist"></a><span data-ttu-id="524cb-143">Elenco di controllo di usabilità</span><span class="sxs-lookup"><span data-stu-id="524cb-143">Usability checklist</span></span>

<span data-ttu-id="524cb-144">**L'utente può fare tutto e qualsiasi valore mani libere, end-to-end?**</span><span class="sxs-lookup"><span data-stu-id="524cb-144">**Can the user do everything and anything hands-free, end-to-end?**</span></span>
* <span data-ttu-id="524cb-145">Ogni interactible devono essere accessibili mani libere</span><span class="sxs-lookup"><span data-stu-id="524cb-145">Every interactible should be accessible hands-free</span></span>
* <span data-ttu-id="524cb-146">Verificare che sia presente una sostituzione per tutti i movimenti personalizzati, ad esempio il ridimensionamento, inserendo, tessere magnetiche, tap e così via.</span><span class="sxs-lookup"><span data-stu-id="524cb-146">Ensure that there is a replacement for all custom gestures, such as resizing, placing, swipes, taps, etc.</span></span>
* <span data-ttu-id="524cb-147">Assicurarsi che l'utente abbia certo controllo della presenza dell'interfaccia utente, posizione, il livello di dettaglio in qualsiasi momento</span><span class="sxs-lookup"><span data-stu-id="524cb-147">Ensure that the user has confident control of UI presence, placement, verbosity at all times</span></span>
    * <span data-ttu-id="524cb-148">Introduzione dell'interfaccia utente dall'area di lavoro</span><span class="sxs-lookup"><span data-stu-id="524cb-148">Getting UI out of the way</span></span>
    * <span data-ttu-id="524cb-149">Interfaccia utente di indirizzamento fuori campo visualizzazione)</span><span class="sxs-lookup"><span data-stu-id="524cb-149">Addressing UI that is out of field of view (FOV)</span></span>
    * <span data-ttu-id="524cb-150">Quanto viene visualizzato, dove e quando</span><span class="sxs-lookup"><span data-stu-id="524cb-150">How much I see, where, when</span></span>

<span data-ttu-id="524cb-151">**Vengono tenuti e consolidati con i destro affordance i meccanismi dell'interazione?**</span><span class="sxs-lookup"><span data-stu-id="524cb-151">**Are the mechanics of the interaction being taught and reinforced with the right affordances?**</span></span>

<span data-ttu-id="524cb-152">L'utente comprensione...</span><span class="sxs-lookup"><span data-stu-id="524cb-152">Does the user understand ...</span></span>
* <span data-ttu-id="524cb-153">... Quali modalità si trovano in?</span><span class="sxs-lookup"><span data-stu-id="524cb-153">... What mode they are in?</span></span>
* <span data-ttu-id="524cb-154">... Le operazioni consentite in questa modalità?</span><span class="sxs-lookup"><span data-stu-id="524cb-154">... What they can do in this mode?</span></span>
* <span data-ttu-id="524cb-155">... Che cos'è lo stato corrente?</span><span class="sxs-lookup"><span data-stu-id="524cb-155">... What is the current state?</span></span>
* <span data-ttu-id="524cb-156">... Come è possibile eseguire la transizione?</span><span class="sxs-lookup"><span data-stu-id="524cb-156">... How they can transition out?</span></span>
    
<span data-ttu-id="524cb-157">**L'interfaccia utente ottimizzata per invisibile all'utente?**</span><span class="sxs-lookup"><span data-stu-id="524cb-157">**Is the UI optimized for hands-free?**</span></span>   

* <span data-ttu-id="524cb-158">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="524cb-158">Ex.</span></span> <span data-ttu-id="524cb-159">Permanenza affordance non sono incorporati ai tipici modelli 2D</span><span class="sxs-lookup"><span data-stu-id="524cb-159">Dwell affordances are not built-in to typical 2D patterns</span></span>
* <span data-ttu-id="524cb-160">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="524cb-160">Ex.</span></span> <span data-ttu-id="524cb-161">Destinati Voice è migliore con l'evidenziazione di oggetto</span><span class="sxs-lookup"><span data-stu-id="524cb-161">Voice targeting is better with object highlighting</span></span>
* <span data-ttu-id="524cb-162">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="524cb-162">Ex.</span></span> <span data-ttu-id="524cb-163">Le interazioni vocali sono preferibili con sottotitoli in lingua originale che dovranno essere attivata</span><span class="sxs-lookup"><span data-stu-id="524cb-163">Voice interactions are better with captions that have to be turned on</span></span>


## <a name="see-also"></a><span data-ttu-id="524cb-164">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="524cb-164">See also</span></span>
* [<span data-ttu-id="524cb-165">Sguardo ed eseguire il commit</span><span class="sxs-lookup"><span data-stu-id="524cb-165">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="524cb-166">Manipolazione diretta</span><span class="sxs-lookup"><span data-stu-id="524cb-166">Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="524cb-167">Punto e commit</span><span class="sxs-lookup"><span data-stu-id="524cb-167">Point and commit</span></span>](point-and-commit.md)

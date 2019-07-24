---
title: Case Study-3 informazioni HoloStudio sull'interfaccia utente e sulla progettazione dell'interazione
description: Apprendimento dell'interfaccia utente e della progettazione dell'interazione HoloStudio
author: rwinj
ms.author: marcghal
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, HoloStudio, realtà mista di Windows
ms.openlocfilehash: e01e2ea888398e9982b56fd95f90ef0731ec6bc2
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974823"
---
# <a name="case-study---3-holostudio-ui-and-interaction-design-learnings"></a><span data-ttu-id="588ba-104">Case Study-3 informazioni HoloStudio sull'interfaccia utente e sulla progettazione dell'interazione</span><span class="sxs-lookup"><span data-stu-id="588ba-104">Case study - 3 HoloStudio UI and interaction design learnings</span></span>

<span data-ttu-id="588ba-105">[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) è stata una delle prime app Microsoft per HoloLens.</span><span class="sxs-lookup"><span data-stu-id="588ba-105">[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) was one of the first Microsoft apps for HoloLens.</span></span> <span data-ttu-id="588ba-106">Per questo motivo, era necessario creare nuove procedure consigliate per la progettazione dell'interfaccia utente e dell'interazione 3D.</span><span class="sxs-lookup"><span data-stu-id="588ba-106">Because of this, we had to create new best practices for 3D UI and interaction design.</span></span> <span data-ttu-id="588ba-107">Questa operazione è stata approvata con un numero elevato di test, prototipi ed errori.</span><span class="sxs-lookup"><span data-stu-id="588ba-107">We did this through a lot of user testing, prototyping, and trial and error.</span></span>

<span data-ttu-id="588ba-108">Microsoft sa che non tutti hanno a disposizione le risorse necessarie per eseguire questo tipo di ricerca, quindi abbiamo avuto la nostra finestra di progettazione SR. olografica, Marcus Ghaly, che condividevamo tre elementi appresi durante lo sviluppo di HoloStudio sull'interfaccia utente e sulla progettazione dell'interazione per le app HoloLens.</span><span class="sxs-lookup"><span data-stu-id="588ba-108">We know that not everyone has the resources at their disposal to do this type of research, so we had our Sr. Holographic Designer, Marcus Ghaly, share three things we learned during the development of HoloStudio about UI and interaction design for HoloLens apps.</span></span>

## <a name="watch-the-video"></a><span data-ttu-id="588ba-109">Guarda il video</span><span class="sxs-lookup"><span data-stu-id="588ba-109">Watch the video</span></span>

>[!VIDEO https://www.youtube.com/embed/sX6yKHmN1qM]

## <a name="problem-1-people-didnt-want-to-move-around-their-creations"></a><span data-ttu-id="588ba-110">#1 problema: Non è stato necessario spostare le creazioni</span><span class="sxs-lookup"><span data-stu-id="588ba-110">Problem #1: People didn't want to move around their creations</span></span>

<span data-ttu-id="588ba-111">In origine, il Workbench è stato progettato in HoloStudio come un rettangolo, molto simile a quello che si trovava nel mondo reale.</span><span class="sxs-lookup"><span data-stu-id="588ba-111">We originally designed the workbench in HoloStudio as a rectangle, much like you'd find in the real world.</span></span> <span data-ttu-id="588ba-112">Il problema è che le persone hanno una durata di esperienza che indica di rimanere ancora quando si trovano su una scrivania o lavorano davanti a un computer, quindi non sono stati spostati nel Workbench ed esplorano la creazione 3D da tutti i lati.</span><span class="sxs-lookup"><span data-stu-id="588ba-112">The problem is that people have a lifetime of experience that tells them to stay still when they're sitting at a desk or working in front of a computer, so they weren't moving around the workbench and exploring their 3D creation from all sides.</span></span>

![La progettazione rettangolare del Workbench in HoloStudio ha dissuadere gli utenti a spostarsi e a vedere le proprie creazioni da tutti i lati.](images/rectangular-workbench-500px.jpg)

<span data-ttu-id="588ba-114">Abbiamo avuto le informazioni necessarie per far girare il Workbench, in modo che non ci fosse un "primo" o un posto chiaro che avresti dovuto affrontare.</span><span class="sxs-lookup"><span data-stu-id="588ba-114">We had the insight to make the workbench round, so that there was no "front" or clear place that you were supposed to stand.</span></span> <span data-ttu-id="588ba-115">Quando è stato testato, improvvisamente gli utenti hanno iniziato a esplorare le proprie creazioni.</span><span class="sxs-lookup"><span data-stu-id="588ba-115">When we tested this, suddenly people started moving around and exploring their creations on their own.</span></span>

![La progettazione circolare di Workbench ha incoraggiato gli utenti a esplorare tutto il percorso delle proprie creazioni.](images/circular-workbench-500px.jpg)

<span data-ttu-id="588ba-117">**Cosa abbiamo imparato**</span><span class="sxs-lookup"><span data-stu-id="588ba-117">**What we learned**</span></span>

<span data-ttu-id="588ba-118">Considerare sempre gli elementi più comodi per l'utente.</span><span class="sxs-lookup"><span data-stu-id="588ba-118">Always be thinking about what's comfortable for the user.</span></span> <span data-ttu-id="588ba-119">Sfruttare i vantaggi del proprio spazio fisico è una funzionalità interessante di HoloLens e ciò che non è possibile eseguire con altri dispositivi.</span><span class="sxs-lookup"><span data-stu-id="588ba-119">Taking advantage of their physical space is a cool feature of HoloLens and something you can't do with other devices.</span></span>

## <a name="problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame"></a><span data-ttu-id="588ba-120">#2 problema: A volte le finestre di dialogo modali si trovano fuori dal frame olografico</span><span class="sxs-lookup"><span data-stu-id="588ba-120">Problem #2: Modal dialogs are sometimes out of the holographic frame</span></span>

<span data-ttu-id="588ba-121">In alcuni casi, è possibile che l'utente stia osservando una direzione diversa rispetto a un elemento che necessita di attenzione nell'app.</span><span class="sxs-lookup"><span data-stu-id="588ba-121">Sometimes, your user may be looking in a different direction from something that needs their attention in your app.</span></span> <span data-ttu-id="588ba-122">In un PC è possibile semplicemente visualizzare una finestra di dialogo, ma se si esegue questa operazione nella faccia di un utente in un ambiente 3D, può sembrare che la finestra di dialogo sia in corso.</span><span class="sxs-lookup"><span data-stu-id="588ba-122">On a PC, you can just pop up a dialog, but if you do this in someone's face in a 3D environment, it can feel like the dialog is getting in their way.</span></span> <span data-ttu-id="588ba-123">Sono necessarie per leggere il messaggio, ma il loro istinto è provare ad allontanarsi da questa.</span><span class="sxs-lookup"><span data-stu-id="588ba-123">You need them to read the message, but their instinct is to try to get away from it.</span></span> <span data-ttu-id="588ba-124">Questa reazione è molto utile se si sta giocando a un gioco, ma in uno strumento progettato per il lavoro è meno ideale.</span><span class="sxs-lookup"><span data-stu-id="588ba-124">This reaction is great if you're playing a game, but in a tool designed for work, it's less than ideal.</span></span>

<span data-ttu-id="588ba-125">Dopo aver provato alcuni aspetti diversi, si è finalmente deciso di usare un sistema di "Bubble idea" per le finestre di dialogo e gli elementi che possono essere seguiti dagli utenti in cui l'attenzione è necessaria nell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="588ba-125">After trying a few different things, we finally settled on using a "thought bubble" system for our dialogs and added tendrils that users can follow to where their attention is needed in our application.</span></span> <span data-ttu-id="588ba-126">Si è anche fatto un impulso ai tralci, che implicava un senso di direzionalità, in modo che gli utenti sapessero dove andare.</span><span class="sxs-lookup"><span data-stu-id="588ba-126">We also made the tendrils pulse, which implied a sense of directionality so that users knew where to go.</span></span>

![Il sistema "Bubble Thought" comprendeva i tentacoli che fornivano un senso di direzione, gli utenti leader dovevano attirare l'attenzione nell'app.](images/thought-bubble-500px.jpg)

<span data-ttu-id="588ba-128">**Cosa abbiamo imparato**</span><span class="sxs-lookup"><span data-stu-id="588ba-128">**What we learned**</span></span>

<span data-ttu-id="588ba-129">In 3D è molto più difficile avvertire gli utenti degli elementi a cui è necessario prestare attenzione.</span><span class="sxs-lookup"><span data-stu-id="588ba-129">It's much harder in 3D to alert users to things they need to pay attention to.</span></span> <span data-ttu-id="588ba-130">L'uso di direttori di attenzione, ad esempio [suoni spaziali](spatial-sound.md), raggi luminosi o bolle di pensiero, può consentire agli utenti di dove devono essere.</span><span class="sxs-lookup"><span data-stu-id="588ba-130">Using attention directors such as [spatial sound](spatial-sound.md), light rays, or thought bubbles, can lead users to where they need to be.</span></span>

## <a name="problem-3-sometimes-ui-can-get-blocked-by-other-holograms"></a><span data-ttu-id="588ba-131">#3 problema: A volte l'interfaccia utente può essere bloccata da altri ologrammi</span><span class="sxs-lookup"><span data-stu-id="588ba-131">Problem #3: Sometimes UI can get blocked by other holograms</span></span>

<span data-ttu-id="588ba-132">In alcuni casi un utente vuole interagire con un ologramma e i controlli dell'interfaccia utente associati, ma è bloccato dalla visualizzazione perché un altro ologramma è davanti ad essi.</span><span class="sxs-lookup"><span data-stu-id="588ba-132">There are times when a user wants to interact with a hologram and its associated UI controls, but they are blocked from view because another hologram is in front of them.</span></span> <span data-ttu-id="588ba-133">Durante lo sviluppo di HoloStudio, abbiamo usato la versione di valutazione e l'errore per giungere a una soluzione.</span><span class="sxs-lookup"><span data-stu-id="588ba-133">While we were developing HoloStudio, we used trial and error to come to a solution for this.</span></span>

![Un controllo dell'interfaccia utente associato a un ologramma può essere bloccato se è presente un altro ologramma tra l'utente e l'utente che indossa HoloLens.](images/ui-blocked-500px.jpg)

<span data-ttu-id="588ba-135">Si è provato a trasferire il controllo dell'interfaccia utente più vicino all'utente, in modo che non fosse possibile bloccarlo, ma si è rivelato che non è stato comodo per l'utente esaminare un controllo che era vicino all'utente, esaminando contemporaneamente un ologramma che era lontano.</span><span class="sxs-lookup"><span data-stu-id="588ba-135">We tried moving the UI control closer to the user so it couldn't get blocked, but found that it wasn't comfortable for the user to look at a control that was near to you while simultaneously looking at a hologram that was far away.</span></span> <span data-ttu-id="588ba-136">Se, tuttavia, il controllo è stato spostato in primo piano rispetto all'ologramma più vicino all'utente, sembra che sia stato scollegato dall'ologramma che dovrebbe influire.</span><span class="sxs-lookup"><span data-stu-id="588ba-136">If, however, we moved the control in front of the closest hologram to the user, they felt like it was detached from the hologram it should be affecting.</span></span>

<span data-ttu-id="588ba-137">Infine, il controllo dell'interfaccia utente è stato completato e inserito alla stessa distanza dall'utente come ologramma a cui è associato, in modo che entrambi si sentano connessi.</span><span class="sxs-lookup"><span data-stu-id="588ba-137">We finally ended up ghosting the UI control, and put it at the same distance from the user as the hologram it's associated with, so they both feel connected.</span></span> <span data-ttu-id="588ba-138">Ciò consente all'utente di interagire con il controllo anche se è stato oscurato.</span><span class="sxs-lookup"><span data-stu-id="588ba-138">This allows the user to interact with the control even though it's been obscured.</span></span>

![Soluzione: è stato eseguito il ghosting del controllo dell'interfaccia utente, che consentiva l'interazione con il controllo e si riteneva connesso all'ologramma su cui influisce.](images/ghosting-ui-500px.jpg)

<span data-ttu-id="588ba-140">**Cosa abbiamo imparato**</span><span class="sxs-lookup"><span data-stu-id="588ba-140">**What we learned**</span></span>

<span data-ttu-id="588ba-141">Gli utenti devono essere in grado di accedere facilmente ai controlli dell'interfaccia utente anche se sono stati bloccati, quindi individuare i metodi per assicurarsi che gli utenti possano completare le proprie attività indipendentemente da dove si trovano gli ologrammi nel mondo reale.</span><span class="sxs-lookup"><span data-stu-id="588ba-141">Users need to be able to easily access UI controls even if they've been blocked, so figure out methods to ensure that users can complete their tasks no matter where their holograms are in the real world.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="588ba-142">Informazioni sull'autore</span><span class="sxs-lookup"><span data-stu-id="588ba-142">About the author</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Marcus Ghaly" width="60" height="60" src="images/marcus-ghaly-200px.jpg"></td>
<td style="border-style: none"><span data-ttu-id="588ba-143"><b>Marcus Ghaly</b></span><span class="sxs-lookup"><span data-stu-id="588ba-143"><b>Marcus Ghaly</b></span></span><br><span data-ttu-id="588ba-144">Finestra di progettazione SR. olografica@Microsoft</span><span class="sxs-lookup"><span data-stu-id="588ba-144">Sr. Holographic Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="588ba-145">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="588ba-145">See also</span></span>
* [<span data-ttu-id="588ba-146">Interazioni istintive</span><span class="sxs-lookup"><span data-stu-id="588ba-146">Instinctual interactions</span></span>](interaction-fundamentals.md)

 

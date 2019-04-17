---
title: Case study - HoloStudio 3 dell'interfaccia utente e l'interazione di progettare esperienze
description: Insegnamenti di progettazione HoloStudio UI e l'interazione
author: rwinj
ms.author: marcghal
ms.date: 03/21/2018
ms.topic: article
keywords: Windows HoloLens, HoloStudio, realtà mista
ms.openlocfilehash: 217c489fed3c0588dae1c2753db6ba15da3522c8
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603211"
---
# <a name="case-study---3-holostudio-ui-and-interaction-design-learnings"></a><span data-ttu-id="f7b22-104">Case study - HoloStudio 3 dell'interfaccia utente e l'interazione di progettare esperienze</span><span class="sxs-lookup"><span data-stu-id="f7b22-104">Case study - 3 HoloStudio UI and interaction design learnings</span></span>

<span data-ttu-id="f7b22-105">[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) era una delle App Microsoft prima per HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f7b22-105">[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) was one of the first Microsoft apps for HoloLens.</span></span> <span data-ttu-id="f7b22-106">Per questo motivo, abbiamo dovuto creare nuove procedure consigliate per 3D dell'interfaccia utente e la progettazione di interazione.</span><span class="sxs-lookup"><span data-stu-id="f7b22-106">Because of this, we had to create new best practices for 3D UI and interaction design.</span></span> <span data-ttu-id="f7b22-107">Abbiamo ottenuto questo attraverso molti tentativi ed errori, la creazione di prototipi e il test dell'utente.</span><span class="sxs-lookup"><span data-stu-id="f7b22-107">We did this through a lot of user testing, prototyping, and trial and error.</span></span>

<span data-ttu-id="f7b22-108">Sappiamo che non tutti gli utenti abbiano le risorse a disposizione per eseguire questo tipo di ricerca, abbiamo dovuto Holographic nostro progettazione senior, Marcus Ghaly, condividono tre cose abbiamo appreso durante lo sviluppo di HoloStudio sulla progettazione dell'interfaccia utente e sull'interazione per App di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f7b22-108">We know that not everyone has the resources at their disposal to do this type of research, so we had our Sr. Holographic Designer, Marcus Ghaly, share three things we learned during the development of HoloStudio about UI and interaction design for HoloLens apps.</span></span>

## <a name="watch-the-video"></a><span data-ttu-id="f7b22-109">Guarda il video</span><span class="sxs-lookup"><span data-stu-id="f7b22-109">Watch the video</span></span>

>[!VIDEO https://www.youtube.com/embed/sX6yKHmN1qM]

## <a name="problem-1-people-didnt-want-to-move-around-their-creations"></a><span data-ttu-id="f7b22-110">Problema di #1: Le persone non vuole spostare le operazioni di creazione</span><span class="sxs-lookup"><span data-stu-id="f7b22-110">Problem #1: People didn't want to move around their creations</span></span>

<span data-ttu-id="f7b22-111">È progettato originariamente workbench in HoloStudio come un rettangolo, molto come si trovano nel mondo reale.</span><span class="sxs-lookup"><span data-stu-id="f7b22-111">We originally designed the workbench in HoloStudio as a rectangle, much like you'd find in the real world.</span></span> <span data-ttu-id="f7b22-112">Il problema è che le persone hanno una durata di esperienza di cui si informa rimanere comunque quando sono seduti a una scrivania o utilizzo davanti a un computer, in modo che non siano intorno alle workbench ed esplorazione relativa creazione 3D da tutti i lati.</span><span class="sxs-lookup"><span data-stu-id="f7b22-112">The problem is that people have a lifetime of experience that tells them to stay still when they're sitting at a desk or working in front of a computer, so they weren't moving around the workbench and exploring their 3D creation from all sides.</span></span>

![La struttura rettangolare di workbench in HoloStudio dissuaded agli utenti di spostarsi e visualizzare le operazioni di creazione da tutti i lati.](images/rectangular-workbench-500px.jpg)

<span data-ttu-id="f7b22-114">Avevamo le informazioni per rendere il workbench arrotondare, in modo che si è verificato alcun "inizio" o cancellare che si doveva in evidenza.</span><span class="sxs-lookup"><span data-stu-id="f7b22-114">We had the insight to make the workbench round, so that there was no "front" or clear place that you were supposed to stand.</span></span> <span data-ttu-id="f7b22-115">Quando questo test è stato, improvvisamente persone avviato muove ed esplorare le operazioni di creazione in modo indipendente.</span><span class="sxs-lookup"><span data-stu-id="f7b22-115">When we tested this, suddenly people started moving around and exploring their creations on their own.</span></span>

![La progettazione di workbench circolare incoraggiata gli utenti a camminare completamente le operazioni di creazione.](images/circular-workbench-500px.jpg)

<span data-ttu-id="f7b22-117">**Che cosa abbiamo imparato**</span><span class="sxs-lookup"><span data-stu-id="f7b22-117">**What we learned**</span></span>

<span data-ttu-id="f7b22-118">Essere sempre pensare che cos'è comodo per l'utente.</span><span class="sxs-lookup"><span data-stu-id="f7b22-118">Always be thinking about what's comfortable for the user.</span></span> <span data-ttu-id="f7b22-119">Sfruttando i vantaggi del proprio spazio fisico è una funzionalità interessante di HoloLens e un elemento che non è possibile eseguire con altri dispositivi.</span><span class="sxs-lookup"><span data-stu-id="f7b22-119">Taking advantage of their physical space is a cool feature of HoloLens and something you can't do with other devices.</span></span>

## <a name="problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame"></a><span data-ttu-id="f7b22-120">Problema #2: Non holographic frame sono a volte le finestre di dialogo modale</span><span class="sxs-lookup"><span data-stu-id="f7b22-120">Problem #2: Modal dialogs are sometimes out of the holographic frame</span></span>

<span data-ttu-id="f7b22-121">In alcuni casi, l'utente può effettuare la ricerca in una direzione diversa da un elemento che richiede la loro attenzione nell'app.</span><span class="sxs-lookup"><span data-stu-id="f7b22-121">Sometimes, your user may be looking in a different direction from something that needs their attention in your app.</span></span> <span data-ttu-id="f7b22-122">In un PC, è possibile semplicemente pop backup di una finestra di dialogo, ma se questa operazione in un utente faccia in un ambiente 3D possibile percepisca la finestra di dialogo ottiene in modo.</span><span class="sxs-lookup"><span data-stu-id="f7b22-122">On a PC, you can just pop up a dialog, but if you do this in someone's face in a 3D environment, it can feel like the dialog is getting in their way.</span></span> <span data-ttu-id="f7b22-123">Ti servono per leggere il messaggio, ma loro impulso è di tentare di ottenere dal controllo.</span><span class="sxs-lookup"><span data-stu-id="f7b22-123">You need them to read the message, but their instinct is to try to get away from it.</span></span> <span data-ttu-id="f7b22-124">Questa reazione è molto utile se si sta eseguendo un gioco, ma in uno strumento progettato per il lavoro, è decisamente idonea.</span><span class="sxs-lookup"><span data-stu-id="f7b22-124">This reaction is great if you're playing a game, but in a tool designed for work, it's less than ideal.</span></span>

<span data-ttu-id="f7b22-125">Dopo la valutazione di alcuni aspetti diversi, è infine scelto di utilizzare un sistema "pensato a bolle" per i dialoghi e aggiunta tendrils che gli utenti possono seguire a in cui è necessaria la loro attenzione nella nostra applicazione.</span><span class="sxs-lookup"><span data-stu-id="f7b22-125">After trying a few different things, we finally settled on using a "thought bubble" system for our dialogs and added tendrils that users can follow to where their attention is needed in our application.</span></span> <span data-ttu-id="f7b22-126">Sono stati apportati anche l'impulso tendrils, quale un senso di direzionalità in cui è inclusa in modo che gli utenti sapessero dove trovare le istruzioni.</span><span class="sxs-lookup"><span data-stu-id="f7b22-126">We also made the tendrils pulse, which implied a sense of directionality so that users knew where to go.</span></span>

![Il sistema "Pensato a bolle" incluso tendrils lampeggiante che ha un senso di direzione, consentendo agli utenti di in cui è stata necessaria la loro attenzione nell'app.](images/thought-bubble-500px.jpg)

<span data-ttu-id="f7b22-128">**Che cosa abbiamo imparato**</span><span class="sxs-lookup"><span data-stu-id="f7b22-128">**What we learned**</span></span>

<span data-ttu-id="f7b22-129">È molto più difficile in 3D per avvisare gli utenti elementi che devono prestare attenzione elementi.</span><span class="sxs-lookup"><span data-stu-id="f7b22-129">It's much harder in 3D to alert users to things they need to pay attention to.</span></span> <span data-ttu-id="f7b22-130">Usando come Consiglio di attenzione [spaziale audio](spatial-sound.md), chiaro rays o pensiero viene propagato, può causare agli utenti in cui devono essere.</span><span class="sxs-lookup"><span data-stu-id="f7b22-130">Using attention directors such as [spatial sound](spatial-sound.md), light rays, or thought bubbles, can lead users to where they need to be.</span></span>

## <a name="problem-3-sometimes-ui-can-get-blocked-by-other-holograms"></a><span data-ttu-id="f7b22-131">Problema #3: In alcuni casi dell'interfaccia utente può essere bloccato da altri vntana</span><span class="sxs-lookup"><span data-stu-id="f7b22-131">Problem #3: Sometimes UI can get blocked by other holograms</span></span>

<span data-ttu-id="f7b22-132">Vi sono casi quando un utente desidera utilizzare interagire con un ologrammi e i relativi controlli dell'interfaccia utente associati, ma vengono bloccati dalla visualizzazione perché sono un'altra ologrammi davanti a essi.</span><span class="sxs-lookup"><span data-stu-id="f7b22-132">There are times when a user wants to interact with a hologram and its associated UI controls, but they are blocked from view because another hologram is in front of them.</span></span> <span data-ttu-id="f7b22-133">Anche se sviluppassimo HoloStudio, abbiamo utilizzato prove empiriche per provengono da una soluzione per questo oggetto.</span><span class="sxs-lookup"><span data-stu-id="f7b22-133">While we were developing HoloStudio, we used trial and error to come to a solution for this.</span></span>

![Un controllo dell'interfaccia utente associato ologramma può diventare bloccato se è presente un altro ologrammi tra i dati e l'utente usura HoloLens.](images/ui-blocked-500px.jpg)

<span data-ttu-id="f7b22-135">Si è provato a spostare il controllo dell'interfaccia utente più vicino all'utente in modo che non è stato bloccato, ma trovato che non era proprio agio l'utente deve esaminare un controllo che è stato nelle vicinanze è mentre si esaminano contemporaneamente ologramma che era a portata di mano.</span><span class="sxs-lookup"><span data-stu-id="f7b22-135">We tried moving the UI control closer to the user so it couldn't get blocked, but found that it wasn't comfortable for the user to look at a control that was near to you while simultaneously looking at a hologram that was far away.</span></span> <span data-ttu-id="f7b22-136">Se, tuttavia, si sposta il controllo davanti l'ologrammi più vicino all'utente, è parso è stato scollegato dall'ologrammi che deve riguardare.</span><span class="sxs-lookup"><span data-stu-id="f7b22-136">If, however, we moved the control in front of the closest hologram to the user, they felt like it was detached from the hologram it should be affecting.</span></span>

<span data-ttu-id="f7b22-137">È infine finisce fantasma, controllo dell'interfaccia utente e inserirlo nella stessa distanza da parte dell'utente come l'ologrammi che è associato, in modo che entrambi si sentono connesso.</span><span class="sxs-lookup"><span data-stu-id="f7b22-137">We finally ended up ghosting the UI control, and put it at the same distance from the user as the hologram it's associated with, so they both feel connected.</span></span> <span data-ttu-id="f7b22-138">Ciò consente all'utente di interagire con il controllo anche se è stato nascosto.</span><span class="sxs-lookup"><span data-stu-id="f7b22-138">This allows the user to interact with the control even though it's been obscured.</span></span>

![Soluzione: abbiamo fantasma di controllo dell'interfaccia utente, che sia consentita l'interazione con il controllo che rendeva è connesso a di ologramma era influisce.](images/ghosting-ui-500px.jpg)

<span data-ttu-id="f7b22-140">**Che cosa abbiamo imparato**</span><span class="sxs-lookup"><span data-stu-id="f7b22-140">**What we learned**</span></span>

<span data-ttu-id="f7b22-141">Gli utenti devono essere in grado di accedere facilmente i controlli dell'interfaccia utente, anche se è stati bloccati, quindi scoprire i metodi per garantire che gli utenti possono completare le attività ovunque loro vntana trovi nel mondo reale.</span><span class="sxs-lookup"><span data-stu-id="f7b22-141">Users need to be able to easily access UI controls even if they've been blocked, so figure out methods to ensure that users can complete their tasks no matter where their holograms are in the real world.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="f7b22-142">Informazioni sull'autore</span><span class="sxs-lookup"><span data-stu-id="f7b22-142">About the author</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Marcus Ghaly" width="60" height="60" src="images/marcus-ghaly-200px.jpg"></td>
<td style="border-style: none"><span data-ttu-id="f7b22-143"><b>Marcus Ghaly</b></span><span class="sxs-lookup"><span data-stu-id="f7b22-143"><b>Marcus Ghaly</b></span></span><br><span data-ttu-id="f7b22-144">Finestra di progettazione senior Holographic @Microsoft</span><span class="sxs-lookup"><span data-stu-id="f7b22-144">Sr. Holographic Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="f7b22-145">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f7b22-145">See also</span></span>
* [<span data-ttu-id="f7b22-146">Nozioni fondamentali di interazione</span><span class="sxs-lookup"><span data-stu-id="f7b22-146">Interaction fundamentals</span></span>](interaction-fundamentals.md)

 

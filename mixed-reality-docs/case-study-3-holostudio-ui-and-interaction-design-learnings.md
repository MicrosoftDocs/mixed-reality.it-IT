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
# <a name="case-study---3-holostudio-ui-and-interaction-design-learnings"></a>Case study - HoloStudio 3 dell'interfaccia utente e l'interazione di progettare esperienze

[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) era una delle App Microsoft prima per HoloLens. Per questo motivo, abbiamo dovuto creare nuove procedure consigliate per 3D dell'interfaccia utente e la progettazione di interazione. Abbiamo ottenuto questo attraverso molti tentativi ed errori, la creazione di prototipi e il test dell'utente.

Sappiamo che non tutti gli utenti abbiano le risorse a disposizione per eseguire questo tipo di ricerca, abbiamo dovuto Holographic nostro progettazione senior, Marcus Ghaly, condividono tre cose abbiamo appreso durante lo sviluppo di HoloStudio sulla progettazione dell'interfaccia utente e sull'interazione per App di HoloLens.

## <a name="watch-the-video"></a>Guarda il video

>[!VIDEO https://www.youtube.com/embed/sX6yKHmN1qM]

## <a name="problem-1-people-didnt-want-to-move-around-their-creations"></a>Problema di #1: Le persone non vuole spostare le operazioni di creazione

È progettato originariamente workbench in HoloStudio come un rettangolo, molto come si trovano nel mondo reale. Il problema è che le persone hanno una durata di esperienza di cui si informa rimanere comunque quando sono seduti a una scrivania o utilizzo davanti a un computer, in modo che non siano intorno alle workbench ed esplorazione relativa creazione 3D da tutti i lati.

![La struttura rettangolare di workbench in HoloStudio dissuaded agli utenti di spostarsi e visualizzare le operazioni di creazione da tutti i lati.](images/rectangular-workbench-500px.jpg)

Avevamo le informazioni per rendere il workbench arrotondare, in modo che si è verificato alcun "inizio" o cancellare che si doveva in evidenza. Quando questo test è stato, improvvisamente persone avviato muove ed esplorare le operazioni di creazione in modo indipendente.

![La progettazione di workbench circolare incoraggiata gli utenti a camminare completamente le operazioni di creazione.](images/circular-workbench-500px.jpg)

**Che cosa abbiamo imparato**

Essere sempre pensare che cos'è comodo per l'utente. Sfruttando i vantaggi del proprio spazio fisico è una funzionalità interessante di HoloLens e un elemento che non è possibile eseguire con altri dispositivi.

## <a name="problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame"></a>Problema #2: Non holographic frame sono a volte le finestre di dialogo modale

In alcuni casi, l'utente può effettuare la ricerca in una direzione diversa da un elemento che richiede la loro attenzione nell'app. In un PC, è possibile semplicemente pop backup di una finestra di dialogo, ma se questa operazione in un utente faccia in un ambiente 3D possibile percepisca la finestra di dialogo ottiene in modo. Ti servono per leggere il messaggio, ma loro impulso è di tentare di ottenere dal controllo. Questa reazione è molto utile se si sta eseguendo un gioco, ma in uno strumento progettato per il lavoro, è decisamente idonea.

Dopo la valutazione di alcuni aspetti diversi, è infine scelto di utilizzare un sistema "pensato a bolle" per i dialoghi e aggiunta tendrils che gli utenti possono seguire a in cui è necessaria la loro attenzione nella nostra applicazione. Sono stati apportati anche l'impulso tendrils, quale un senso di direzionalità in cui è inclusa in modo che gli utenti sapessero dove trovare le istruzioni.

![Il sistema "Pensato a bolle" incluso tendrils lampeggiante che ha un senso di direzione, consentendo agli utenti di in cui è stata necessaria la loro attenzione nell'app.](images/thought-bubble-500px.jpg)

**Che cosa abbiamo imparato**

È molto più difficile in 3D per avvisare gli utenti elementi che devono prestare attenzione elementi. Usando come Consiglio di attenzione [spaziale audio](spatial-sound.md), chiaro rays o pensiero viene propagato, può causare agli utenti in cui devono essere.

## <a name="problem-3-sometimes-ui-can-get-blocked-by-other-holograms"></a>Problema #3: In alcuni casi dell'interfaccia utente può essere bloccato da altri vntana

Vi sono casi quando un utente desidera utilizzare interagire con un ologrammi e i relativi controlli dell'interfaccia utente associati, ma vengono bloccati dalla visualizzazione perché sono un'altra ologrammi davanti a essi. Anche se sviluppassimo HoloStudio, abbiamo utilizzato prove empiriche per provengono da una soluzione per questo oggetto.

![Un controllo dell'interfaccia utente associato ologramma può diventare bloccato se è presente un altro ologrammi tra i dati e l'utente usura HoloLens.](images/ui-blocked-500px.jpg)

Si è provato a spostare il controllo dell'interfaccia utente più vicino all'utente in modo che non è stato bloccato, ma trovato che non era proprio agio l'utente deve esaminare un controllo che è stato nelle vicinanze è mentre si esaminano contemporaneamente ologramma che era a portata di mano. Se, tuttavia, si sposta il controllo davanti l'ologrammi più vicino all'utente, è parso è stato scollegato dall'ologrammi che deve riguardare.

È infine finisce fantasma, controllo dell'interfaccia utente e inserirlo nella stessa distanza da parte dell'utente come l'ologrammi che è associato, in modo che entrambi si sentono connesso. Ciò consente all'utente di interagire con il controllo anche se è stato nascosto.

![Soluzione: abbiamo fantasma di controllo dell'interfaccia utente, che sia consentita l'interazione con il controllo che rendeva è connesso a di ologramma era influisce.](images/ghosting-ui-500px.jpg)

**Che cosa abbiamo imparato**

Gli utenti devono essere in grado di accedere facilmente i controlli dell'interfaccia utente, anche se è stati bloccati, quindi scoprire i metodi per garantire che gli utenti possono completare le attività ovunque loro vntana trovi nel mondo reale.

## <a name="about-the-author"></a>Informazioni sull'autore

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Marcus Ghaly" width="60" height="60" src="images/marcus-ghaly-200px.jpg"></td>
<td style="border-style: none"><b>Marcus Ghaly</b><br>Finestra di progettazione senior Holographic @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Vedere anche
* [Nozioni fondamentali di interazione](interaction-fundamentals.md)

 

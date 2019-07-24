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
# <a name="case-study---3-holostudio-ui-and-interaction-design-learnings"></a>Case Study-3 informazioni HoloStudio sull'interfaccia utente e sulla progettazione dell'interazione

[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) è stata una delle prime app Microsoft per HoloLens. Per questo motivo, era necessario creare nuove procedure consigliate per la progettazione dell'interfaccia utente e dell'interazione 3D. Questa operazione è stata approvata con un numero elevato di test, prototipi ed errori.

Microsoft sa che non tutti hanno a disposizione le risorse necessarie per eseguire questo tipo di ricerca, quindi abbiamo avuto la nostra finestra di progettazione SR. olografica, Marcus Ghaly, che condividevamo tre elementi appresi durante lo sviluppo di HoloStudio sull'interfaccia utente e sulla progettazione dell'interazione per le app HoloLens.

## <a name="watch-the-video"></a>Guarda il video

>[!VIDEO https://www.youtube.com/embed/sX6yKHmN1qM]

## <a name="problem-1-people-didnt-want-to-move-around-their-creations"></a>#1 problema: Non è stato necessario spostare le creazioni

In origine, il Workbench è stato progettato in HoloStudio come un rettangolo, molto simile a quello che si trovava nel mondo reale. Il problema è che le persone hanno una durata di esperienza che indica di rimanere ancora quando si trovano su una scrivania o lavorano davanti a un computer, quindi non sono stati spostati nel Workbench ed esplorano la creazione 3D da tutti i lati.

![La progettazione rettangolare del Workbench in HoloStudio ha dissuadere gli utenti a spostarsi e a vedere le proprie creazioni da tutti i lati.](images/rectangular-workbench-500px.jpg)

Abbiamo avuto le informazioni necessarie per far girare il Workbench, in modo che non ci fosse un "primo" o un posto chiaro che avresti dovuto affrontare. Quando è stato testato, improvvisamente gli utenti hanno iniziato a esplorare le proprie creazioni.

![La progettazione circolare di Workbench ha incoraggiato gli utenti a esplorare tutto il percorso delle proprie creazioni.](images/circular-workbench-500px.jpg)

**Cosa abbiamo imparato**

Considerare sempre gli elementi più comodi per l'utente. Sfruttare i vantaggi del proprio spazio fisico è una funzionalità interessante di HoloLens e ciò che non è possibile eseguire con altri dispositivi.

## <a name="problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame"></a>#2 problema: A volte le finestre di dialogo modali si trovano fuori dal frame olografico

In alcuni casi, è possibile che l'utente stia osservando una direzione diversa rispetto a un elemento che necessita di attenzione nell'app. In un PC è possibile semplicemente visualizzare una finestra di dialogo, ma se si esegue questa operazione nella faccia di un utente in un ambiente 3D, può sembrare che la finestra di dialogo sia in corso. Sono necessarie per leggere il messaggio, ma il loro istinto è provare ad allontanarsi da questa. Questa reazione è molto utile se si sta giocando a un gioco, ma in uno strumento progettato per il lavoro è meno ideale.

Dopo aver provato alcuni aspetti diversi, si è finalmente deciso di usare un sistema di "Bubble idea" per le finestre di dialogo e gli elementi che possono essere seguiti dagli utenti in cui l'attenzione è necessaria nell'applicazione. Si è anche fatto un impulso ai tralci, che implicava un senso di direzionalità, in modo che gli utenti sapessero dove andare.

![Il sistema "Bubble Thought" comprendeva i tentacoli che fornivano un senso di direzione, gli utenti leader dovevano attirare l'attenzione nell'app.](images/thought-bubble-500px.jpg)

**Cosa abbiamo imparato**

In 3D è molto più difficile avvertire gli utenti degli elementi a cui è necessario prestare attenzione. L'uso di direttori di attenzione, ad esempio [suoni spaziali](spatial-sound.md), raggi luminosi o bolle di pensiero, può consentire agli utenti di dove devono essere.

## <a name="problem-3-sometimes-ui-can-get-blocked-by-other-holograms"></a>#3 problema: A volte l'interfaccia utente può essere bloccata da altri ologrammi

In alcuni casi un utente vuole interagire con un ologramma e i controlli dell'interfaccia utente associati, ma è bloccato dalla visualizzazione perché un altro ologramma è davanti ad essi. Durante lo sviluppo di HoloStudio, abbiamo usato la versione di valutazione e l'errore per giungere a una soluzione.

![Un controllo dell'interfaccia utente associato a un ologramma può essere bloccato se è presente un altro ologramma tra l'utente e l'utente che indossa HoloLens.](images/ui-blocked-500px.jpg)

Si è provato a trasferire il controllo dell'interfaccia utente più vicino all'utente, in modo che non fosse possibile bloccarlo, ma si è rivelato che non è stato comodo per l'utente esaminare un controllo che era vicino all'utente, esaminando contemporaneamente un ologramma che era lontano. Se, tuttavia, il controllo è stato spostato in primo piano rispetto all'ologramma più vicino all'utente, sembra che sia stato scollegato dall'ologramma che dovrebbe influire.

Infine, il controllo dell'interfaccia utente è stato completato e inserito alla stessa distanza dall'utente come ologramma a cui è associato, in modo che entrambi si sentano connessi. Ciò consente all'utente di interagire con il controllo anche se è stato oscurato.

![Soluzione: è stato eseguito il ghosting del controllo dell'interfaccia utente, che consentiva l'interazione con il controllo e si riteneva connesso all'ologramma su cui influisce.](images/ghosting-ui-500px.jpg)

**Cosa abbiamo imparato**

Gli utenti devono essere in grado di accedere facilmente ai controlli dell'interfaccia utente anche se sono stati bloccati, quindi individuare i metodi per assicurarsi che gli utenti possano completare le proprie attività indipendentemente da dove si trovano gli ologrammi nel mondo reale.

## <a name="about-the-author"></a>Informazioni sull'autore

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Marcus Ghaly" width="60" height="60" src="images/marcus-ghaly-200px.jpg"></td>
<td style="border-style: none"><b>Marcus Ghaly</b><br>Finestra di progettazione SR. olografica@Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Vedere anche
* [Interazioni istintive](interaction-fundamentals.md)

 

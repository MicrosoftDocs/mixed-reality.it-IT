---
title: Su questo materiale sussidiario di progettazione
description: Questo materiale sussidiario è stato creato da finestre di progettazione, gli sviluppatori, i responsabili del programma Microsoft e i ricercatori, la cui attività coinvolge holographic dispositivi (ad esempio, HoloLens) e coinvolgente e concreto (ad esempio le cuffie Acer e realtà mista di HP Windows).
author: MRWied
ms.author: jonwie
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, progettazione, introduzione, il materiale sussidiario
ms.openlocfilehash: ca69118dfeb766c1386420cd81053b9acb485ba7
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974854"
---
# <a name="about-this-design-guidance"></a>Su questo materiale sussidiario di progettazione

## <a name="introduction"></a>Introduzione

**Ciao e Benvenuti alle linee guida di progettazione per realtà mista.**

Questo materiale sussidiario è stato creato da finestre di progettazione, gli sviluppatori, i responsabili del programma Microsoft e i ricercatori, la cui attività coinvolge holographic dispositivi (ad esempio, HoloLens) e coinvolgente e concreto (ad esempio le cuffie Acer e realtà mista di HP Windows). Pertanto, prendere in considerazione questo lavoro come un set di argomenti per 'sulla progettazione per gli schermi azionata Windows'.

Con l'utente, si sta attivando una nuova era dell'informatica estremamente interessante. Ultime innovazioni sul piano head montati vengono visualizzati, spaziale audio, sensori, consapevolezza ambientale, input, e grafica 3D lead Stati Uniti e Stati Uniti, per definire nuovi tipi di esperienze di test... nuova frontiera che è notevolmente più personali, intuitiva, coinvolgenti e contestuali.

Laddove possibile, offriremo indicazioni di progettazione di utilità pratica, con il codice correlato in GitHub. Ciò premesso, poiché si sta apprendimento destra insieme si, sempre non sarà in grado di offrire indicazioni specifiche e utilizzabili. Alcune delle quali distribuiamo sarà nello spirito dei 'lezioni abbiamo imparato' e 'evitare verso la parte inferiore che il percorso'.

E sappiamo che molte innovazioni verranno generate dalla community di progettazione più grande, quindi saremo lieti di ascolto da parte dell'utente, l'apprendimento da parte dell'utente e collaborare strettamente. Per la parte nostra, faremo del nostro meglio per condividere i nostri insights, anche se sono esplorativi e la fase iniziale, con l'intenzione di consentendo agli sviluppatori e progettisti con pensare di progettazione, procedure consigliate e i relativi aprire origine controlli, modelli e le app di esempio che è possibile usare direttamente nel proprio lavoro.

## <a name="overview"></a>Panoramica

Ecco una rapida panoramica del modo in cui è organizzata in questa Guida di progettazione. Le sezioni sono disponibili per ognuna di queste aree, con collegamenti ad articoli più.
* **[Iniziare a progettare](mixed-reality.md)**  : leggere i commenti ad alto livello e comprendere i principi si seguirà.
* **[Interazioni instinctual](interaction-fundamentals.md)**  -informazioni su input, l'esecuzione di comandi, la navigazione e altri concetti di base di interazione per la progettazione delle app.
* **[Stile](typography.md)**  -rendere l'app fantastici tramite colore, tipografia e movimento.
* **[I modelli dell'app](types-of-mixed-reality-apps.md)**  -informazioni su come le app possono estendersi su scenari per gli ambienti coinvolgenti e realistici.
* **[I controlli](interactable-object.md)**  -utilizzo di controlli e modelli come esperienza di blocchi predefiniti per creare la tua app.
* **[App di esempio](design.md#sample-apps)**  -compilare esperienze all'avanguardia dagli esempi progettato e creato dal nostro team.
* **[Strumenti e risorse di progettazione](design.md#design-tools)**  -avviare il progetto con i modelli di progettazione e strumenti.

Per tutti i video, noterete che sono Stati Uniti la sperimentazione con diversi formati e tecniche, tutto con l'intento della distribuzione è necessario e quello precedente, l'obiettivo è fornire la giusta combinazione di testo, illustrazioni e i diagrammi. E nei prossimi mesi, verranno espansi questa tassonomia per includere un set più ampio di progettazione argomenti. Quando possibile, che viene fornito un Heads-up sulle novità in arrivo, ed è quindi necessario mantenere il controllo torna.

## <a name="objectives"></a>Obiettivi

Ecco una breve presentazione alcuni obiettivi di alto livello che sono guidando il lavoro in modo da poter comprendere dove proveniamo dalla:

### <a name="help-solve-customer-challenges"></a>Aiutare a risolvere le problematiche dei clienti

![Aiutare a risolvere le problematiche dei clienti](images/500px-fix-a-broken-switch-with-hololens.jpg) <br>

Si implementeranno con molti degli stessi problemi che sono ed è consapevole è complessa come il proprio lavoro. È interessante esplorare e definire una nuova frontiera nell'ambito... e può anche essere molto complessa. Procedure consigliate e paradigmi precedente devono essere considerate nuovamente; nuove esperienze necessità dei clienti; ed è disponibile molto potenziali per l'innovazione. Ciò detto, applicheremo questo lavoro possa essere quanto più possibile, lo spostamento abbondantemente una Guida di stile completo. L'obiettivo è offrire un set completo di indicazioni di progettazione che copre mista interazione realtà, l'esecuzione di comandi, navigazione, input e lo stile – tutti negli scenari e il comportamento umano basato sul. 

### <a name="point-the-way-towards-a-new-more-human-way-of-computing"></a>Scegliere la strada verso un metodo nuovo, ancora più naturali di computing

![Scegliere la strada verso un metodo nuovo, ancora più naturali di computing](images/500px-man-and-women-with-holograph-on-table.png)<br>

Anche se è importante concentrarsi sui problemi specifici del cliente, vogliamo anche noi stessi pensare rispetto a quello di offrire più eseguire il push. Microsoft ritiene design eccezionale non è "just" Risoluzione dei problemi, ma anche un modo per attivare chiaramente evoluzione risorse umane. Nuove modalità di comportamento umano. nuovi modi di persone relativi a se stessi, la loro attività e i relativi ambienti; nuovi modi di visualizzare il mondo dell'IT... si vuole che le istruzioni riportate in modo da riflettere i questi modi più gratificanti di pensare troppo. 

### <a name="meet-creators-where-they-are"></a>Soddisfa gli autori si trovino

![Soddisfa gli autori si trovino](images/500px-creators.jpg) <br>

Ci auguriamo che molti gruppi di destinatari trovare questo materiale sussidiario per essere utili. Si dispone di diversi set di competenze-(inizio, a livello intermedio, advanced), si utilizzano strumenti diversi (Unity, DirectX, C++, C#, gli altri), sono già note con diverse piattaforme (Windows, iOS, Android), provengono da diversi colori di sfondo (per dispositivi mobili, enterprise, giochi ) e stanno lavorando i team di dimensioni diverse (solo, small, medium, large). Pertanto, verrà visualizzato questo materiale sussidiario con esigenze e prospettive diverse. Quando possibile, si proverà a tenere presente questa diversità e rendere le linee guida come pertinente al massimo al numero di destinatari possibili. Inoltre, sappiamo che molti di voi sono già in GitHub, pertanto si collegherà direttamente al repository GitHub e forum di scendere a cui si è già. 

### <a name="share-as-much-as-possible-from-experimental-to-explicit"></a>Condividere quanto possibile, da esperimento a esplicite

![Condividere quanto possibile, da esperimento a esplicite](images/500px-man-playinggame.jpg) <br>

Una delle difficoltà che offrono indicazioni di progettazione in questo nuovo supporto 3D è che non sempre sono linee guida definitiva di offrire. Solo, ad esempio, si sta learning, sperimentazione, la creazione di prototipi, risoluzione dei problemi e regolando come sono stati raggiunti gli ostacoli. Anziché attendere alcune momento futuro mitico quando abbiamo tutto ha intuito, l'obiettivo è condividere nostro modo di pensare con è in tempo reale, anche se non è esaustivo. Naturalmente, l'obiettivo finale deve essere definitivi laddove possibile, che fornisce indicazioni per la progettazione chiara e flessibili associate al codice open source e interattivi in strumenti di sviluppo e progettazione Microsoft. Ma il recupero fino a quel punto richiede molti cicli di iterazione e l'apprendimento. Si vuole interagire con l'utente e informazioni con l'utente, lungo il percorso, in modo che si eseguiranno la migliore possibile per condividere man mano che si procede, anche il ciò che è in fase sperimentale. 

### <a name="the-right-balance-of-global-and-local-design"></a>Il giusto equilibrio di progettazione globale e locale

![Il giusto equilibrio di progettazione globale e locale](images/500px-fluentdesign.jpg) <br>

Offerti due livelli di linee guida di progettazione: globale e locale. Le indicazioni di progettazione 'global' incorporate nel [Fluent Design sistema](http://fluent.microsoft.com). Dettagli Fluent modo di pensare nozioni di base, ad esempio chiaro, profondità, movimento, materiale e scalabilità tra tutti i Microsoft design: i dispositivi, i prodotti, strumenti e servizi. Che esistono differenze specifiche del dispositivo significative, dette tutto il sistema più grande, in modo che i nostri "local" linee guida di progettazione per azionata Visualizza descriverà la progettazione per dispositivi holographic e coinvolgente e concreto che spesso hanno input diversi e metodi di output, e scenari e le diverse esigenze degli utenti. Pertanto, le indicazioni di progettazione locale vengono trattati argomenti univoci per HMDs, ad esempio 3D ambienti e gli oggetti. ambienti condivisi; l'utilizzo di sensori, rilevamento occhio e mapping spaziale; e le opportunità di spaziale audio. In tutta la linea guida prescrive verrà visualizzato a fare riferimento a questi globale e gli aspetti locali e si spera Ciò consentirà a terra del lavoro in una base più grande della progettazione sfruttando contemporaneamente le differenze di progettazione di dispositivi specifici.

### <a name="have-a-discussion"></a>Dispone di una discussione

![Dispone di una discussione](images/500px-share.jpg) <br>

Forse ancora più importante, si vuole interagire con l'utente, la community di sviluppatori e coinvolgenti e holographic finestre di progettazione per definire questa nuova era interessante di progettazione. Come indicato in precedenza, sappiamo che non abbiamo tutte le risposte e crediamo che molte soluzioni interessanti e innovazioni proverranno da parte dell'utente. L'obiettivo è essere aperta e disponibile per ascoltare su di essi e discutere con l'utente online e gli eventi e aggiungere valore ogni volta che è possibile. Siamo entusiasti di far parte di questa straordinaria community di progettazione, adottare un'avventura insieme. 

## <a name="please-dive-in"></a>Approfondimento.

Ci auguriamo che questo articolo iniziale fornisce un contesto significativo esplorare le indicazioni di progettazione. Approfondimento, e inviare commenti e suggerimenti nei forum di GitHub sono disponibili negli articoli, o al Design Microsoft collegati in [Twitter](https://twitter.com/MicrosoftDesign) e [Facebook](https://www.facebook.com/microsoftdesign/). È possibile condividere progetta il futuro insieme.

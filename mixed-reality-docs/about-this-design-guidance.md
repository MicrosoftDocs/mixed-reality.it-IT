---
title: Su questo materiale sussidiario di progettazione
description: Queste linee guida sono state create da progettisti, sviluppatori, program manager e ricercatori Microsoft impegnati nella realizzazione di dispositivi olografici (come HoloLens) e dispositivi di tipo immersive (come i visori VR di Windows Mixed Reality Acer e HP).
author: MRWied
ms.author: jonwie
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, progettazione, introduzione, il materiale sussidiario
ms.openlocfilehash: 6173f7cd2bcc4280f86f8f5ecaae1e90e01b62a0
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326122"
---
# <a name="about-this-design-guidance"></a>Su questo materiale sussidiario di progettazione

## <a name="introduction"></a>Introduzione

**Ciao e Benvenuti alle linee guida di progettazione per realtà mista.**

Questo materiale sussidiario è stato creato da finestre di progettazione, gli sviluppatori, i responsabili del programma Microsoft e i ricercatori, la cui attività coinvolge holographic dispositivi, come HoloLens e coinvolgenti dispositivi, ad esempio le cuffie Acer e realtà mista di Windows di HP. Prendere in considerazione questo lavoro come un set di argomenti che illustrano come progettare per schermi montato head di Windows.

Con l'utente, si sta attivando una nuova era dell'informatica estremamente interessante. Ultime innovazioni sul piano azionata consente di visualizzare, spaziale audio, sensori, consapevolezza ambientale, grafica 3D e input lead us e stimolare us, per definire nuovi tipi di esperienze - nuova frontiera notevolmente più personale, intuitiva, coinvolgente e contesto.

Laddove possibile, offriremo indicazioni per la progettazione di utilità pratica con il codice correlato in GitHub. Ciò premesso, poiché si sta apprendimento destra insieme si, sempre non sarà in grado di offrire indicazioni specifiche e utilizzabili. Alcune delle quali distribuiamo sarà nello spirito dei 'lezioni abbiamo imparato' e 'evitare verso la parte inferiore che il percorso'.

E si sa, molte innovazioni verranno generate dalla community di progettazione più grande. Pertanto, saremo lieti di ascolto da parte dell'utente, l'apprendimento da parte dell'utente e collaborare strettamente. Per la parte nostra, faremo del nostro meglio per condividere i nostri insights, anche se sono esplorativo e anticipata con l'intenzione di consentendo agli sviluppatori e progettisti con pensare di progettazione, le procedure consigliate, i controlli correlati open source, modelli e le app di esempio che è possibile usare direttamente nel proprio lavoro.

## <a name="overview"></a>Panoramica

Ecco una rapida panoramica del modo in cui è organizzata in questa Guida di progettazione. Le sezioni sono disponibili per ognuna di queste aree con collegamenti ad articoli più.
* **[Iniziare a progettare](mixed-reality.md)**  : leggere i commenti ad alto livello e comprendere i principi si seguirà.
* **[Interazioni instinctual](interaction-fundamentals.md)**  -informazioni su input, l'esecuzione di comandi, la navigazione e altri concetti di base di interazione per la progettazione delle app.
* **[Stile](typography.md)**  -rendere l'applicazione fantastici tramite colore, tipografia e movimento.
* **[I modelli dell'app](types-of-mixed-reality-apps.md)**  -informazioni su come app; ications può estendersi su scenari per gli ambienti coinvolgenti e realistici.
* **[I controlli](interactable-object.md)**  -usare i controlli e modelli come blocchi predefiniti per creare un'esperienza dell'applicazione.
* **[App di esempio](design.md#sample-apps)**  -compilare esperienze all'avanguardia dagli esempi progettato e creato dal nostro team.
* **[Strumenti e risorse di progettazione](design.md#design-tools)**  -avviare il progetto con i modelli di progettazione e strumenti.

Per tutti i video, noterete che sono Stati Uniti la sperimentazione con diversi formati e tecniche, tutto con l'intento della distribuzione è necessario e quello precedente, l'obiettivo è fornire la giusta combinazione di testo, illustrazioni e i diagrammi. E nei prossimi mesi, verranno espansi questa tassonomia per includere un set più ampio di progettazione argomenti. Quando possibile, che viene fornito un Heads-up sulle novità in arrivo, ed è quindi necessario mantenere il controllo torna.

## <a name="objectives"></a>Obiettivi

Di seguito è riportato un rapido controllo di alcuni obiettivi di alto livello che sono guidando il lavoro in modo da poter comprendere dove proveniamo dalla

### <a name="help-solve-customer-challenges"></a>Aiutare a risolvere le problematiche dei clienti

![Aiutare a risolvere le problematiche dei clienti](images/500px-fix-a-broken-switch-with-hololens.jpg) <br>

Si implementeranno con molti degli stessi problemi che sono ed è consapevole è complessa come il proprio lavoro. È interessante esplorare e definire una nuova frontiera nell'ambito... e può anche essere molto complessa. Procedure consigliate e paradigmi precedente devono essere considerate nuovamente; i clienti devono nuove esperienze; ed è disponibile molto potenziali per l'innovazione. Dato che si vuole che questo lavoro possa essere quanto più possibile, lo spostamento abbondantemente una Guida di stile completo. L'obiettivo è offrire un set completo di indicazioni di progettazione che copre mista interazione realtà, l'esecuzione di comandi, navigazione, input e lo stile – tutti negli scenari e il comportamento umano basato sul. 

### <a name="point-the-way-towards-a-new-more-human-way-of-computing"></a>Scegliere la strada verso un metodo nuovo, ancora più naturali di computing

![Scegliere la strada verso un metodo nuovo, ancora più naturali di computing](images/500px-man-and-women-with-holograph-on-table.png)<br>

Anche se è importante concentrarsi sui problemi specifici del cliente, vogliamo anche noi stessi pensare rispetto a quello di offrire più eseguire il push. Microsoft ritiene design eccezionale non è "just" Risoluzione dei problemi, ma anche un modo per attivare chiaramente evoluzione risorse umane. Nuove modalità di comportamento umano. nuovi modi di persone relativi a se stessi, la loro attività e i relativi ambienti; nuovi modi di visualizzare il mondo dell'IT... si vuole che le istruzioni riportate in modo da riflettere i questi modi più gratificanti di pensare troppo. 

### <a name="meet-creators-where-they-are"></a>Soddisfa gli autori si trovino

![Soddisfa gli autori si trovino](images/500px-creators.jpg) <br>

Ci auguriamo che molti gruppi di destinatari trovare questo materiale sussidiario per essere utili. Si dispone di diversi set di competenze-(inizio, a livello intermedio, advanced), si utilizzano strumenti diversi (Unity, DirectX, C++, C#, gli altri), sono già note con diverse piattaforme (Windows, iOS, Android), provengono da diversi colori di sfondo (per dispositivi mobili, enterprise, giochi ) e stanno lavorando i team di dimensioni diverse (solo, small, medium, large). Pertanto, è possibile visualizzare questo materiale sussidiario con esigenze e prospettive diverse. Quando possibile, si proverà a tenere presente questa diversità e rendere le linee guida come pertinente al massimo al numero di destinatari possibili. Inoltre, sappiamo che molti di voi sono già in GitHub. Pertanto, verrà collegata direttamente al repository GitHub e forum di scendere a cui si è già. 

### <a name="share-as-much-as-possible-from-experimental-to-explicit"></a>Condividere quanto possibile, da esperimento a esplicite

![Condividere quanto possibile, da esperimento a esplicite](images/500px-man-playinggame.jpg) <br>

Una delle difficoltà che offrono indicazioni di progettazione in questo nuovo supporto 3D è che non sempre sono linee guida definitiva di offrire. Solo, ad esempio, si sta learning, sperimentazione, la creazione di prototipi, risoluzione dei problemi e regolando come sono stati raggiunti gli ostacoli. Anziché attendere alcune momento futuro mitico quando abbiamo tutto ha intuito, l'obiettivo è condividere nostro modo di pensare con l'utente in tempo reale, anche se non è esaustivo. Naturalmente, l'obiettivo finale è essere considerati definitivi, ovunque si può, chiare e fornendo progettazione flessibile informazioni aggiuntive associate al codice open source e utilizzabili in strumenti di progettazione e sviluppo di Microsoft. Ma il recupero fino a quel punto richiede molti cicli di iterazione e l'apprendimento. Si vuole interagire con l'utente e informazioni con l'utente, lungo il percorso. Con tutte le questa premessa, faremo del nostro meglio per condividere man mano che si procede, anche con i nostri ciò che è in fase sperimentale. 

### <a name="the-right-balance-of-global-and-local-design"></a>Il giusto equilibrio di progettazione globale e locale

![Il giusto equilibrio di progettazione globale e locale](images/500px-fluentdesign.jpg) <br>

Offerti due livelli di linee guida di progettazione: globale e locale. Le indicazioni di progettazione 'global' incorporate nel [Fluent Design sistema](http://fluent.microsoft.com). Dettagli Fluent modo di pensare nozioni di base, ad esempio chiaro, profondità, movimento, materiale e scalabilità tra tutti i Microsoft design: i dispositivi, i prodotti, strumenti e servizi. Ciò premesso, sono presenti differenze significative specifiche del dispositivo in questo sistema più grande. Pertanto, nostro indicazioni di progettazione 'local' per gli schermi azionata descrivono la progettazione per i dispositivi holographic e coinvolgente e concreto che spesso avere diversi input e output i metodi, nonché le diverse esigenze degli utenti e gli scenari. Linee guida di progettazione locale vengono trattati argomenti univoci per HMDs. Ad esempio:  Gli ambienti 3D e gli oggetti. ambienti condivisi; l'utilizzo di sensori, rilevamento occhio e mapping spaziale; e le opportunità di spaziale audio. In tutta la linea guida prescrive verrà visualizzato a fare riferimento a questi globale e gli aspetti locali. Si spera Ciò consentirà a terra del lavoro in una base più grande della progettazione sfruttando contemporaneamente le differenze di progettazione tra dispositivi specifici.

### <a name="have-a-discussion"></a>Dispone di una discussione

![Dispone di una discussione](images/500px-share.jpg) <br>

Forse ancora più importante, si vuole interagire con l'utente, la community di sviluppatori e coinvolgenti e holographic finestre di progettazione per definire questa nuova era interessante di progettazione. Come indicato in precedenza, sappiamo che non abbiamo tutte le risposte. Questo spiega il motivo per cui siamo convinti che molte soluzioni interessanti e innovazioni proverranno da parte dell'utente. L'obiettivo è essere aperta e disponibile per ascoltare su di essi e discutere con l'utente online e gli eventi e aggiungere valore ogni volta che è possibile. Siamo entusiasti di far parte di questa straordinaria community di progettazione, adottare un'avventura insieme. 

## <a name="please-dive-in"></a>Approfondimento.

Ci auguriamo che questo articolo introduttivo fornisce un contesto significativo esplorare le indicazioni di progettazione. Approfondimento, e inviare commenti e suggerimenti nei forum di GitHub sono disponibili negli articoli, o al Design Microsoft collegati in [Twitter](https://twitter.com/MicrosoftDesign) e [Facebook](https://www.facebook.com/microsoftdesign/). È possibile condividere progetta il futuro insieme.

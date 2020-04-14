---
title: Informazioni sulle linee guida di progettazione
description: Queste linee guida sono state create da progettisti, sviluppatori, program manager e ricercatori Microsoft impegnati nella realizzazione di dispositivi olografici (come HoloLens) e dispositivi di tipo immersive (come i visori VR di Windows Mixed Reality Acer e HP).
author: mrwied
ms.author: jonwie
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, progettazione, introduzione, guida
ms.openlocfilehash: 114a3808d57b2bd78044ce743d568bd5effe25bb
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277519"
---
# <a name="about-this-design-guidance"></a>Informazioni sulle linee guida di progettazione

## <a name="introduction"></a>Introduzione

**Salve e Benvenuti alle linee guida di progettazione per la realtà mista.**

Questo materiale sussidiario viene creato da Microsoft designer, sviluppatori, Program Manager e ricercatori, il cui lavoro si estende su dispositivi olografici, come HoloLens e dispositivi immersivi, come ad esempio le cuffie di realtà mista Acer e HP Windows. Considerare questo lavoro come un set di argomenti su come progettare per le visualizzazioni montate su Windows.

Si sta immettendo un'eccezionale nuova era di elaborazione. Le novità negli schermi montati, il suono spaziale, i sensori, la consapevolezza ambientale, l'input e la grafica 3D ci portano e ci sfidano per definire nuovi tipi di esperienze, una nuova frontiera notevolmente più personale, intuitiva, immersiva e contestuale.

Laddove possibile, offriamo linee guida di progettazione di utilità pratica con il codice correlato in GitHub. Detto questo, dal momento che si sta imparando con l'utente, non sarà sempre possibile offrire indicazioni specifiche e fruibili. Una parte di ciò che condividiamo si troverà nello spirito di "lezioni apprese" ed evitando di incorrere in tale percorso.

E sappiamo che molte innovazioni saranno generate dalla più ampia community di progettazione. Quindi, siamo lieti di ricevere notizie da te, imparando da te e lavorando a stretto contatto con te. Per la nostra parte, possiamo condividere le nostre informazioni approfondite, anche se sono esplorative e tempestive, con lo scopo di consentire agli sviluppatori e ai progettisti la progettazione, le procedure consigliate e i controlli, i modelli e le app di esempio correlati, che puoi usare direttamente nel tuo lavoro.

## <a name="overview"></a>Panoramica

Ecco una rapida panoramica del modo in cui sono organizzate le linee guida di progettazione. 
* **[Panoramica](design.md)** : informazioni sul processo di progettazione, i concetti di base e i fattori di interazione da considerare.
* **[Concetti di base](core-concepts-landingpage.md)** : informazioni su comfort, frame olografico, mapping spaziale e altri concetti di base da considerare.
* **[Modelli di interazione](interaction-fundamentals.md)** : questa guida è strutturata intorno a tre modelli di interazione principali.
* **[Elementi UX](app-patterns-landingpage.md)** : usare controlli e comportamenti come blocchi predefiniti per creare un'esperienza di applicazione personalizzata.
* **[Risorse](design.md#choose-a-prototyping-option)** : avviare il progetto con strumenti di progettazione e opzioni di creazione di prototipi.

Per quanto sopra, si mira a offrire il giusto mix di testo, illustrazioni e diagrammi e video, in modo da potervi sperimentare con diversi formati e tecniche, con la finalità di fornire le informazioni necessarie. E nei prossimi mesi, la tassonomia verrà espansa per includere un set più ampio di argomenti di progettazione. Quando possibile, verranno fornite le informazioni relative a ciò che sarà prossimo, quindi è necessario ricontrollarlo.

## <a name="objectives"></a>Obiettivi

Ecco una rapida panoramica di alcuni obiettivi di alto livello che guidano questo lavoro per poter capire da dove provengono

### <a name="help-solve-customer-challenges"></a>Contribuire alla risoluzione delle esigenze dei clienti

![Contribuire alla risoluzione delle esigenze dei clienti](images/500px-fix-a-broken-switch-with-hololens.jpg) <br>

Si affrontano molti degli stessi problemi che è possibile eseguire e si comprende il modo in cui il lavoro è complesso. È entusiasmante esplorare e definire una nuova frontiera... e può anche essere scoraggiante. È necessario ripensare ai paradigmi e alle procedure precedenti. i clienti necessitano di nuove esperienze; e c'è molto potenziale per l'innovazione. Poiché si vuole che il lavoro sia il più completo possibile, andare oltre una guida di stile. Miriamo a offrire un set completo di linee guida per la progettazione che riguardano interazione tra realtà mista, comandi, navigazione, input e stile, il tutto in scenari e comportamenti umani. 

### <a name="point-the-way-towards-a-new-more-human-way-of-computing"></a>Puntare a una nuova modalità di calcolo più umana

![Puntare a una nuova modalità di calcolo più umana](images/500px-man-and-women-with-holograph-on-table.png)<br>

Sebbene sia importante concentrarsi sui problemi specifici dei clienti, è anche possibile effettuare il push in base a quanto previsto, oltre a offrire maggiori possibilità. Ci riteniamo che la progettazione straordinaria non sia "solo" risoluzione dei problemi, ma anche un modo per attivare in modo significativo l'evoluzione umana. Nuovi modi di comportamento umano; nuovi modi di persone correlate a se stessi, alle loro attività e ai rispettivi ambienti; nuovi modi per vedere il nostro mondo... si vuole che le linee guida riflettano tutti questi modi più ambiziosi. 

### <a name="meet-creators-where-they-are"></a>Scopri i creatori in cui sono

![Scopri i creatori in cui sono](images/500px-creators.jpg) <br>

Ci auguriamo che molti destinatari trovino questa guida per essere utile. Sono disponibili diversi set di competenze (inizio, intermedio, avanzato), usare diversi strumenti (Unity, C++DirectX C#,, other), che hanno familiarità con le varie piattaforme (Windows, iOS, Android), provenienti da diversi sfondi (per dispositivi mobili, aziendali e di gioco) e che lavorano su team di dimensioni diverse (solo, piccolo, medio, grande). Questo materiale sussidiario può quindi essere visualizzato con diverse prospettive e esigenze. Quando possibile, si proverà a tenere presente questa diversità e si renderà le indicazioni più rilevanti possibile per il maggior numero di persone possibile. Inoltre, sappiamo che molti di voi si trovano già in GitHub. Ti invieremo direttamente il collegamento ai repository e ai forum di GitHub per soddisfare le tue esigenze. 

### <a name="share-as-much-as-possible-from-experimental-to-explicit"></a>Condividi quanto più possibile, da sperimentale a esplicita

![Condividi quanto più possibile, da sperimentale a esplicita](images/500px-man-playinggame.jpg) <br>

Una delle implicazioni dell'offerta di linee guida di progettazione in questo nuovo supporto 3D è che non è sempre disponibile una guida definitiva da offrire. Proprio come te, stiamo imparando, sperimentando, effettuando prototipi, risolvendo problemi e modificando gli ostacoli che abbiamo raggiunto. Invece di attendere qualche momento futuro, quando abbiamo capito tutto, vogliamo condividere il nostro pensiero in tempo reale, anche se non è conclusivo. Naturalmente, il nostro obiettivo finale è quello di essere definitivo ovunque sia possibile, fornendo linee guida di progettazione chiare e flessibili associate a codice open source e interoperabile negli strumenti di sviluppo e progettazione Microsoft. Tuttavia, raggiungere questo punto richiede molti cicli di iterazione e apprendimento. Si vuole interagire con l'utente e acquisire familiarità con l'utente. Tenendo presente questo aspetto, la nostra soluzione migliore è quella di condividere il nostro lavoro, anche con le nostre cose sperimentali. 

### <a name="the-right-balance-of-global-and-local-design"></a>Il giusto equilibrio tra progettazione globale e locale

![Il giusto equilibrio tra progettazione globale e locale](images/500px-fluentdesign.jpg) <br>

Offriamo due livelli di linee guida per la progettazione: globale e locale. Le linee guida di progettazione "globali" sono incorporate nel [sistema di progettazione Fluent](https://fluent.microsoft.com). Informazioni dettagliate sul modo in cui consideriamo i concetti di base quali luce, profondità, movimento, materiale e scalabilità in tutta la progettazione Microsoft, ovvero dispositivi, prodotti, strumenti e servizi. Detto ciò, esistono differenze significative specifiche del dispositivo in questo sistema più ampio. Quindi, le linee guida di progettazione "locale" per gli schermi montati, descrivono la progettazione di dispositivi olografici e immersivi che spesso hanno metodi di input e output diversi, nonché diversi scenari e esigenze utente. Le linee guida sulla progettazione locale riguardano argomenti specifici di HMDs. Ad esempio: ambienti e oggetti 3D; ambienti condivisi; uso di sensori, monitoraggio degli occhi e mapping spaziale; e le opportunità di audio spaziale. In tutta la guida è probabile che ci si faccia riferimento a questi aspetti globali e locali. Speriamo che ciò consentirà di basare il lavoro in una base di progettazione più ampia sfruttando al contempo le differenze di progettazione tra dispositivi specifici.

### <a name="have-a-discussion"></a>Discussione

![Discussione](images/500px-share.jpg) <br>

Forse più importante, vogliamo collaborare con te, la community di progettisti e sviluppatori olografici e immersivi per definire questa nuova e interessante era di progettazione. Come indicato in precedenza, sappiamo che non sono disponibili tutte le risposte. Questo è il motivo per cui si ritiene che si ritengano molte interessanti soluzioni e innovazioni. L'obiettivo è quello di essere aperti e disponibili per ascoltarli, discutere con l'utente online e gli eventi e aggiungere valore ovunque sia possibile. Siamo entusiasti di essere parte integrante di questa straordinaria community di progettazione, che è stata affrontata insieme a un'avventura. 

## <a name="please-dive-in"></a>Accedi

Ci auguriamo che questo articolo introduttivo fornisca un contesto significativo durante l'esplorazione delle linee guida di progettazione. Per approfondire le proprie opinioni, vedere i forum su GitHub che saranno collegati negli articoli oppure Microsoft Design su [Twitter](https://twitter.com/MicrosoftDesign) e [Facebook](https://www.facebook.com/microsoftdesign/). È ora di co-progettare il futuro insieme.

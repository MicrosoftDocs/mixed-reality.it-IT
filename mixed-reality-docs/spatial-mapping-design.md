---
title: Progettazione di mapping spaziale
description: Uso di mapping spaziale all'interno di HoloLens richiede un'attenta considerazione dei numerosi fattori.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Mapping di realtà mista di Windows, progettazione, spaziali, HoloLens, surface ricostruzione, mesh
ms.openlocfilehash: 451213a79e1d482d64725ce750065611830beec3
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829964"
---
# <a name="spatial-mapping-design"></a>Progettazione di mapping spaziale

Uso di mapping spaziale all'interno di HoloLens richiede un'attenta considerazione dei numerosi fattori.

## <a name="device-support"></a>Supporto di dispositivi

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Funzionalità</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Auricolari coinvolgenti</strong></a></td>
    </tr>
     <tr>
        <td>Progettazione di mapping spaziale</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="why-is-spatial-mapping-important"></a>Perché è importante mapping spaziale?

Mapping spaziale rende possibile posizionare gli oggetti su superfici reali. In questo modo gli oggetti di ancoraggio nel mondo dell'utente e sfrutta i vantaggi di indicatori depth reali. Occluding il vntana basati su altri ologrammi e oggetti reali aiuta a convincere l'utente che questi vntana è effettivamente nel proprio spazio. Ologrammi mobile nello spazio o lo spostamento con l'utente non si sentiranno come tipo real. Quando possibile, gli elementi sul posto per comodità.

Visualizzare le superfici durante l'inserimento o lo spostamento vntana (usare una griglia proiettata semplice). Ciò consentirà all'utente in cui sono meglio possibile posizionare gli ologrammi e viene visualizzato all'utente se il campione stanno tentando di posizionare le ologrammi non è ancora stato eseguito il mapping ancora. È possibile "billboard elementi" verso l'utente se vengono emesse in una quantità eccessiva di un angolo.

## <a name="what-influences-spatial-mapping-quality"></a>Ciò che influenza qualità mapping spaziale?

Per garantire la migliore esperienza utente, è importante comprendere i fattori che influiscono sulla qualità dei dati di mapping spaziale raccolti da HoloLens.

Errori nei dati di mapping spaziale rientrano in una delle tre categorie:
* **Aree libere**: Aree del mondo reale sono presenti i dati di mapping spaziale.
* **Psicosi**: Le superfici esistono nei dati di mapping spaziale che non esistono nel mondo reale.
* **Distorsione**: Superfici nei dati di mapping spaziale modo perfetto sono allineate con le superfici reali, il push o pull.

Molti fattori possono influenzare la frequenza e la gravità di questi errori:

* **Movimento utente**
   * Modo in cui l'utente passa attraverso il proprio ambiente determina come verrà analizzato l'ambiente, in modo che l'utente può richiedere informazioni aggiuntive per ottenere un'analisi valida.
   * Fotocamera usata per l'analisi fornisce i dati all'interno di un cono 70 gradi, da un minimo di 0,8 contatori a un massimo di 3.1 metri di distanza dalla fotocamera. Aree del mondo reale verranno solo analizzate all'interno di questo campo di visualizzazione. Si noti che questi valori sono soggetti a modifiche nelle versioni future.
   * Se l'utente non ottiene mai in metri 3.1 di un oggetto quindi non verrà analizzato.
   * Se l'utente visualizza solo un oggetto da una distanza minore di contatori 0,8, che non verrà analizzato (questo modo si evita l'analisi mani dell'utente).
   * Se l'utente non sembra verso l'alto, ovvero abbastanza normale, quindi il limite massimo probabilmente non verrà analizzato.
   * Se un utente non cerca mai dietro una parete o mobili quindi gli oggetti bloccati da esse non verranno analizzati.
   * Le superfici tendono a essere analizzati con una qualità più elevata quando vengono visualizzati; invece di un angolo superficiale.
   * Se il sistema di rilevamento di head di HoloLens ha esito negativo momentaneamente (che possono verificarsi a causa di un movimento velocizzarne, illuminazione insufficiente, dato walls o le fotocamere diventando coperti), ciò può introdurre errori nei dati di mapping spaziale. Questi errori verranno corretti nel corso del tempo come l'utente continua a spostarsi e analizzare il proprio ambiente.

* **Materiali di Surface**
   * I materiali disponibili nelle aree del mondo reale variano notevolmente. Questi compromettere la qualità dei dati poiché influiscono sul modo in cui infrarossi viene riflessa di mapping spaziale.
   * Le superfici scure potrebbe essere Impossibile eseguire fino a quando non diventano più da vicino alla fotocamera, perché indicano meno chiaro.
   * Alcune aree possono essere pertanto scure che riflettono luce troppo piccolo per essere analizzati da qualsiasi distanza, in modo che verranno introdotti errori hole in corrispondenza della posizione dell'area di e in alcuni casi anche dietro l'area.
   * Le superfici particolarmente shiny possono digitalizzare solo quando viene visualizzato; e non quando viene visualizzato da un angolo superficiale.
   * Mirror, poiché creano illusory riflessi di spazi reali e dalle aree, può causare errori hole sia errori hallucination.

* **Movimento di scena**
   * Mapping spaziale grado di adattarsi rapidamente alle modifiche nell'ambiente, ad esempio lo spostamento di utenti o di apertura e chiusura di porte.
   * Mapping spaziale solo adattabile alle modifiche in un'area quando quell'area è chiaramente visibile alla fotocamera che viene usata per l'analisi.
   * Per questo motivo, è possibile che questo adattamento al ritardo delle realtà, che può causare errori di area libera o hallucination.
   * Ad esempio, un utente esegue l'analisi di un elemento friend e quindi, mentre l'amico lascia la chat. Una rappresentazione 'ghost' di friend (un errore hallucination) verrà mantenuti nei dati di mapping spaziale, fino a quando l'utente riattiva e analizza nuovamente lo spazio in cui è stato permanente di tipo friend.

* **Interferenze di illuminazione**
   * A infrarossi luce nella scena può interferire con l'analisi, ad esempio la luce del sole sicuro passa attraverso una finestra.
   * In particolare shiny superfici possono interferire con la scansione delle superfici nelle vicinanze, la luce rimbalza off loro che provocano errori di compensazione.
   * Shiny superfici che riflettono luce direttamente della fotocamera possono interferire con lo spazio nelle vicinanze, facendo in modo psicosi air medie mobili o rimandando adattamento al movimento di scena.
   * Due dispositivi HoloLens nella stessa stanza non dovrebbero interferire con l'uno da altro, ma la presenza di più di cinque dispositivi HoloLens potrebbe causare l'interferenza.

È possibile evitare o correggere alcuni di questi errori. Tuttavia, è necessario progettare l'applicazione in modo che l'utente è in grado di raggiungere i propri obiettivi anche in presenza di errori nei dati di mapping spaziale.

## <a name="the-environment-scanning-experience"></a>L'ambiente di analisi esperienza

HoloLens scopre le superfici nel proprio ambiente perché l'utente è simile a tali file. Nel corso del tempo di HoloLens tende ad aumentare una scansione di tutte le parti dell'ambiente che sono stati osservati. Aggiorna anche l'analisi perché vengono rispettate le modifiche nell'ambiente. Questa analisi automaticamente verranno mantenuti tra avvii dell'app.

Ogni applicazione che Usa mapping spaziale deve prendere in considerazione per offrire ' analisi '; il processo tramite cui l'applicazione Guida l'utente per analizzare le superfici che sono necessarie per l'applicazione funzioni correttamente.

![Esempio di analisi](images/sr-mixedworld-140429-8pm-00068-1000px.png)<br>
*Esempio di analisi*

La natura di questa esperienza di analisi può variare notevolmente in base alle esigenze di ogni applicazione, ma due principi fondamentali dovrebbero guidare la progettazione.

In primo luogo **Cancella la comunicazione con l'utente è la principale preoccupazione**. L'utente deve essere sempre consapevole che indica se vengono rispettati i requisiti dell'applicazione. Quando essi non sono state soddisfatte, deve essere immediatamente chiaro per l'utente perché in tal caso e deve essere indirizzati rapidamente a eseguire l'azione appropriata.

In secondo luogo **le applicazioni devono provare a raggiungere un equilibrio tra efficienza e affidabilità**. Quando è possibile farlo **in modo affidabile**, le applicazioni automaticamente dovrebbero analizzare i dati di mapping spaziale per risparmiare tempo l'utente. Quando non è possibile eseguire questa operazione in modo affidabile, le applicazioni devono invece consentire all'utente di fornire rapidamente l'applicazione con le informazioni aggiuntive che necessarie.

Per facilitare la progettazione destra l'esperienza di analisi, prendere in considerazione quali le possibilità seguenti sono applicabili all'applicazione:

* **Alcuna esperienza di analisi**
   * Un'applicazione potrebbe funzionare perfettamente senza alcuna esperienza di analisi interattiva; apprenderanno informazioni superfici osservati durante lo spostamento di utente naturali.
   * Ad esempio un'applicazione che consente all'utente di disegnare su superfici 3D con spraypaint holographic richiede conoscenze solo delle superfici attualmente visibili all'utente.
   * L'ambiente può essere completamente analizzato già se si tratta di uno in cui l'utente ha già trascorso molto tempo usando la HoloLens.
   * Tenere presente tuttavia che fotocamera usata dal mapping spaziale può visualizzare solo 3.1m davanti all'utente, in modo mapping spaziale non riconoscerà sulle eventuali aree più distanti, a meno che l'utente ha osservato li a distanza di più da vicino utilizzando passato.
   * In modo che l'utente riconosce che espongono è stati analizzati, l'applicazione deve fornire un feedback visivo che questo effetto, ad esempio il cast virtuale shadows su superfici digitalizzate potrebbe aiutare l'utente Inserisci vntana in tali aree.
   * In questo caso, i volumi di delimitazione dell'osservatore superficie spaziale devono essere aggiornata ogni frame in un corpo di blocco [sistema di coordinate spaziale](coordinate-systems.md), in modo che seguono l'utente.

* **Individuare un percorso appropriato**
   * Un'applicazione può essere progettata per l'uso in un percorso con requisiti specifici.
   * Ad esempio, l'applicazione potrebbe richiedere un'area vuota per l'utente in modo che in modo sicuro possibile esercitarsi kung-fu holographic.
   * Le applicazioni devono comunicare i requisiti specifici per l'utente iniziale ed ribadire li con il feedback visivo chiaro.
   * In questo esempio, l'applicazione deve visualizzare l'ambito di un'area vuota necessaria ed evidenziare visivamente la presenza di eventuali oggetti indesiderati all'interno di quest'area.
   * Per questo caso, i volumi di delimitazione dell'osservatore superficie spaziale devono usare un mondo bloccata [sistema di coordinate spaziale](coordinate-systems.md) nella posizione scelta.

* **Trovare una configurazione appropriata di dispositivi Surface**
   * Un'applicazione richieda una configurazione specifica di aree, ad esempio due grandi dimensioni, di semplice, contrapposte le pareti per creare un hall holographic di mirror.
   * In questi casi l'applicazione sarà necessario analizzare le superfici fornite tramite il mapping spaziale per rilevare le superfici adatte e indirizzare l'utente verso di loro.
   * L'utente deve avere un'opzione di fallback se non è completamente affidabile l'analisi della superficie dell'applicazione. Ad esempio, se l'applicazione identifica in modo errato incoraggiare come una parete flat, l'utente deve un modo semplice per correggere l'errore.

* **Parte dell'ambiente di analisi**
   * Un'applicazione può essere utile acquisire solo parte dell'ambiente, come indicato dall'utente.
   * Ad esempio, l'applicazione esegue l'analisi di parte di una chat room in modo che l'utente può inviare un annuncio pubblicitario holographic per mobili che desiderano vendere.
   * In questo caso, l'applicazione deve acquisire i dati di mapping spaziale all'interno di aree di osservato dall'utente durante le analisi.

* **Analizzare l'intero spazio**
   * Un'applicazione potrebbe richiedere un'analisi di tutte le superfici nella chat room corrente, inclusi quelli dietro l'utente.
   * Ad esempio, un gioco può mettere l'utente nel ruolo di Gulliver, sotto siege di centinaia di piccole dimensioni Lilliputians raggiungendo da tutte le direzioni.
   * In questi casi, l'applicazione sarà necessario determinare il numero di aree di corrente di spazio sufficiente sono già stati analizzati e indirizzare sguardo dell'utente per riempire i gap significativi.
   * La chiave per questo processo consiste nel fornire un feedback visivo che rende per spiegare all'utente che espongono non è ancora stati analizzati. L'applicazione, ad esempio possibile usare [nebbia basate sulla distanza](https://msdn.microsoft.com/library/windows/desktop/bb173401%28v=vs.85%29.aspx) per evidenziare visivamente le aree che non vengono analizzate dalle superfici di mapping spaziale.

* **Eseguire uno snapshot iniziale dell'ambiente**
   * Un'applicazione potrebbe essere necessario ignorare tutte le modifiche nell'ambiente dopo l'esecuzione di uno 'snapshot' iniziale.
   * Questo può essere appropriato per evitare un'interruzione di dati creati dall'utente che sono strettamente collegati allo stato iniziale dell'ambiente.
   * In questo caso, l'applicazione deve creare una copia dei dati di mapping spaziale nello stato iniziale dopo aver completata l'analisi.
   * Le applicazioni devono continuare a ricevere gli aggiornamenti ai dati di mapping spaziale se vntana devono ancora essere bloccati in modo corretto dall'ambiente.
   * Aggiornamenti costanti per i dati di mapping spaziale consentono inoltre di visualizzare tutte le modifiche che si sono verificati, chiarire all'utente le differenze tra precedente e presenti stati dell'ambiente.

* **Creare snapshot avviate dall'utente dell'ambiente**
   * Un'applicazione può essere opportuno solo rispondere a eventuali modifiche ambientali quando richiesto dall'utente.
   * Ad esempio, l'utente è stato possibile creare più 3D 'esplosi' di un amico acquisendo le pose in momenti diversi.

* **Consentire all'utente di modificare l'ambiente**
   * Un'applicazione può essere progettata per rispondere in tempo reale per tutte le modifiche apportate nell'ambiente dell'utente.
   * Ad esempio, l'utente di disegnare una tenda potrebbe attivare 'cambi scena' per un holographic play in esecuzione su altro lato.

* **Guida l'utente per evitare errori nei dati di mapping spaziale**
   * Un'applicazione può essere utile fornire materiale sussidiario per l'utente mentre si esegue l'analisi il proprio ambiente.
   * Ciò può aiutare l'utente a evitare determinati tipi di [errori nei dati di mapping spaziale](spatial-mapping-design.md#what-influences-spatial-mapping-quality), ad esempio, rimanendo lontano da windows illuminata o mirror.

Un dettaglio aggiuntivo da tenere presente è che l'intervallo di dati di mapping spaziale non è illimitato. Pur mapping spaziale compilare un database permanente degli spazi di grandi dimensioni, è solo che i dati disponibili per le applicazioni in una bolla di dimensioni limitate per l'utente. In questo modo se iniziare all'inizio di un corridoio lungo e una procedura sufficientemente grande dall'inizio, quindi alla fine le superfici spaziali torna all'inizio non verranno più visualizzato. È ovviamente possibile attenuare questo problema tali superfici nell'applicazione di memorizzazione nella cache dopo che sono scomparsi dai dati di mapping spaziale disponibile.

## <a name="mesh-processing"></a>Elaborazione di rete

Può essere utile per rilevare tipi di errori comuni in aree e filtrare, rimuovere o modificare i dati di mapping spaziale come appropriato.

Tenere presente tale mapping spaziale dati deve essere fedele possibile alle aree del mondo reale, in modo qualsiasi elaborazione si applicano i rischi spostando le superfici sbagliato' '.

Di seguito sono riportati alcuni esempi di diversi tipi di rete mesh di elaborazione che possono risultare utili:

* **Riempimento area libera**
   * Se un piccolo oggetto di materiale scuro errore durante l'analisi, verrà conservata uno spazio vuoto nell'area di circostante.
   * Aree libere di influire sulle relative all'occlusione: vntana può essere visualizzati tramite uno spazio vuoto in un'area del mondo reale presumibilmente opaco.
   * Aree libere interessano raycasts: se si usa raycasts per consentire agli utenti di interagire con aree, potrebbe essere inaccettabile per questi raggi a pass-through aree libere. Una soluzione consiste nell'usare un'aggregazione di più raycasts che coprono un'area di dimensione appropriate. In questo modo sarà possibile filtrare i risultati 'outlier', in modo che anche se uno raycast passa attraverso un problema di piccole dimensioni, il risultato aggregato sarà comunque valido. Tuttavia, tenere presente che questo approccio comporta un costo di calcolo.
   * Aree libere di influire sulle collisioni fisica: un oggetto controllato da simulazione fisica può eliminare tramite uno spazio vuoto nel tetto minimo e diventare perso.
   * È possibile compilare modo algoritmico tali difetti nella trama della superficie. Tuttavia, è necessario ottimizzare l'algoritmo in modo che 'reale aree libere", ad esempio windows e considerarle non vengono specificati. Può essere difficile distinguere in modo affidabile 'reali fori' da 'immaginari fori', pertanto sarà necessario sperimentare diverse regole euristiche, ad esempio 'size' e 'shape limiti'.

* **Rimozione hallucination**
   * I riflessi, luminosi e lo spostamento di oggetti può lasciare piccole residui 'psicosi' mobile nell'aria intermedio.
   * Psicosi influiscono sulle relative all'occlusione: psicosi potrebbero diventare visibile come forme scure spostando in primo piano e occluding altri vntana.
   * Psicosi interessano raycasts: se si usa raycasts per consentire agli utenti di interagire con aree, questi rays potrebbe implicare un hallucination anziché l'area sottostante. Come con aree libere, una soluzione consiste nell'usare raycasts molti anziché un singolo raycast, ma anche in questo caso verrà sottoposto a un costo di calcolo.
   * Psicosi collisioni di fisica effettiva: un oggetto controllato da simulazione fisica potrebbe bloccarsi su una hallucination e in grado di spostarsi all'interno di un'area di spazio apparentemente non crittografata.
   * È possibile filtrare tali psicosi dalla trama della superficie. Tuttavia, come con aree libere, è necessario ottimizzare l'algoritmo in modo che gli oggetti di piccole reale come lamp-sta e rimossi non gestisce lo sportello della.

* **Anti-aliasing**
   * Mapping spaziale può restituire le superfici che sembrano essere approssimativa o 'fastidiosi' rispetto alle relative controparti reali.
   * La precisione influisce sulle collisioni fisica: se la parte intera è approssimativa, una palla di golf fisicamente simulato potrebbe non eseguire il rollback in modo uniforme su di esso in una linea retta.
   * La precisione influisce sul rendering: se un'area verrà visualizzata direttamente, normali alla superficie ruvida possono influire sull'aspetto e interrompere un'occhiata 'clean'. È possibile risolvere questo problema usando appropriato illuminazione e trame in allo shader di cui viene utilizzato per il rendering dell'area.
   * È possibile smussare asperità in una rete mesh di surface. Tuttavia, si può eseguire il push ulteriormente la superficie dalla superficie reali corrispondente. Gestione di una stretta corrispondenza è importante per produrre occlusione ologrammi accurate e consentire agli utenti di ottenere le interazioni precise e prevedibili con superfici holographic.
   * Se solo una modifica di cosmetica è obbligatoria, potrebbe essere sufficiente per alleggerire i normali vertici senza modificare le posizioni di vertice.

* **Ricerca di piano**
   * Esistono molte forme di analisi che un'applicazione può essere opportuno eseguire nelle aree di forniti da mapping spaziale.
   * Un esempio semplice è 'ricerca del piano'; identificazione di decadimento, principalmente planare aree delle superfici.
   * Planare aree possono essere utilizzate come holographic-superfici di lavoro, le aree in cui può essere posizionato automaticamente holographic contenuto dall'applicazione.
   * Planare aree possono vincolare l'interfaccia utente, per guidare gli utenti per l'interazione con le superfici che meglio adatti alle proprie esigenze.
   * Planare aree è utilizzabile come nel mondo reale, per le controparti holographic agli oggetti funzionali, ad esempio gli schermi LCD, tabelle o una lavagna.
   * Planare aree possono definire le aree di play, che costituiscono la base dei livelli televisione.
   * Planare aree possono essere d'aiuto gli agenti virtuali per esplorare il mondo reale, identificando le aree del piano che probabilmente i fondamenti in persone reali.

## <a name="prototyping-and-debugging"></a>La creazione di prototipi e il debug

### <a name="useful-tools"></a>Strumenti utili
* Il [emulatore HoloLens](using-the-hololens-emulator.md) può essere utilizzato per sviluppare applicazioni usando il mapping spaziale senza accesso a un HoloLens fisico. Consente di simulare una sessione attiva in un HoloLens in un ambiente realistico, con tutti i dati dell'applicazione in genere richiederebbe, tra cui HoloLens movimento, spaziali sistemi di coordinate e le reti mesh di mapping spaziale. Utilizzabile per fornire input affidabili, ripetibili, che può essere utile per il debug di problemi e la valutazione delle modifiche al codice.
* Per riprodurre un scenari, acquisire i dati di mapping spaziale tramite la rete da un HoloLens in tempo reale, quindi salvarlo sul disco e riusarla in sessioni di debug successive.
* Il [vista 3D di Windows device portale](using-the-windows-device-portal.md#3d-view) fornisce un modo per visualizzare tutte le superfici spaziali attualmente disponibile tramite il sistema di mapping spaziale. Questo offre una base di confronto per le superfici spaziale all'interno dell'applicazione. ad esempio è possibile stabilire facilmente se qualsiasi superfici spaziali non sono presenti o sono visualizzate in una posizione errata.

### <a name="general-prototyping-guidance"></a>Materiale sussidiario generale di creazione di prototipi
* In quanto [errori](spatial-mapping-design.md#what-influences-spatial-mapping-quality) nel mapping spaziale dati influisca fortemente l'esperienza utente, è consigliabile testare l'applicazione in un'ampia gamma di ambienti.
* Non rimanere intrappolato prendere l'abitudine di test sempre nello stesso percorso, ad esempio dalla propria scrivania. Assicurarsi di testare in diverse superfici di posizioni diverse, forme, dimensioni e materiali.
* Analogamente, i dati sintetici o registrati possono essere utili per eseguire il debug, non diventano troppo si basa su alcuni test case stesso. Questo può ritardare la ricerca di problemi importanti che informazioni consentono di variare il test avrebbe consentito di intercettare in precedenza.
* È consigliabile eseguire il test con utenti reali (e idealmente non coached), perché non possono utilizzare il HoloLens o l'applicazione in esattamente la stessa modalità utilizzata. In realtà, potrebbe sembrare strano, è il comportamento delle persone come non coerente, possono essere conoscenze e presupposti.

## <a name="see-also"></a>Vedere anche
* [Visualizzazione della scansione dello spazio](room-scan-visualization.md)
* [Progettazione dell'audio spaziale](spatial-sound-design.md)
* [Persistenza in Unity](persistence-in-unity.md)

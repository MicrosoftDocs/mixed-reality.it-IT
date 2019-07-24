---
title: Progettazione di mapping spaziale
description: Un utilizzo efficace del mapping spaziale all'interno di HoloLens richiede un'attenta considerazione di molti fattori.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, progettazione, mapping spaziale, HoloLens, ricostruzione della superficie, mesh
ms.openlocfilehash: 451213a79e1d482d64725ce750065611830beec3
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829964"
---
# <a name="spatial-mapping-design"></a>Progettazione di mapping spaziale

Un utilizzo efficace del mapping spaziale all'interno di HoloLens richiede un'attenta considerazione di molti fattori.

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
        <td><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
    </tr>
     <tr>
        <td>Progettazione di mapping spaziale</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="why-is-spatial-mapping-important"></a>Perché il mapping spaziale è importante?

Il mapping spaziale rende possibile posizionare gli oggetti su superfici reali. In questo modo è possibile agganciare gli oggetti nel mondo dell'utente e sfruttare i vantaggi offerti dai suggerimenti per la profondità del mondo reale. Occlusione gli ologrammi in base ad altri ologrammi e oggetti reali consentono di convincere l'utente che questi ologrammi si trovano effettivamente nello spazio. Gli ologrammi che galleggiano nello spazio o con l'utente non risulteranno reali. Quando possibile, inserire gli elementi per comodità.

Visualizza le superfici quando si posizionano o spostano gli ologrammi (usare una griglia proiettata semplice). Ciò consentirà all'utente di individuare il punto in cui è possibile posizionare i propri ologrammi e Mostra all'utente se la posizione in cui si sta provando a collocare l'ologramma non è ancora stata mappata. È possibile "Billboard Items" verso l'utente se terminano troppo di un angolo.

## <a name="what-influences-spatial-mapping-quality"></a>Che influenza la qualità del mapping spaziale?

Per garantire la migliore esperienza utente, è importante comprendere i fattori che influiscono sulla qualità dei dati di mapping spaziale raccolti da HoloLens.

Gli errori nei dati di mapping spaziale rientrano in una delle tre categorie seguenti:
* **Buchi**: Nei dati di mapping spaziale mancano le superfici reali.
* **Allucinazioni**: Le superfici sono presenti nei dati di mapping spaziali che non esistono nel mondo reale.
* **Distorsione**: Le superfici nei dati di mapping spaziale sono allineate in modo non perfetto con le superfici reali, spostate o estratte.

Molti fattori possono influire sulla frequenza e la gravità degli errori seguenti:

* **Movimento dell'utente**
   * Il modo in cui l'utente passa attraverso il proprio ambiente determina l'accuratezza dell'analisi dell'ambiente, in modo che l'utente possa richiedere informazioni aggiuntive per ottenere una buona analisi.
   * La fotocamera usata per l'analisi fornisce dati all'interno di un cono di 70 gradi, da un minimo di 0,8 metri a un massimo di 3,1 metri di distanza dalla fotocamera. Le aree reali verranno analizzate solo all'interno di questo campo di visualizzazione. Si noti che questi valori sono soggetti a modifiche nelle versioni future.
   * Se l'utente non raggiunge mai entro 3,1 metri di un oggetto, non verrà analizzato.
   * Se l'utente visualizza solo un oggetto da una distanza inferiore a 0,8 metri, non verrà analizzato (in questo modo si evita di analizzare le mani dell'utente).
   * Se l'utente non guarda mai verso l'alto (che è abbastanza normale), probabilmente il limite non verrà analizzato.
   * Se un utente non si trova mai dietro la mobilia o un muro, gli oggetti bloccati da essi non verranno analizzati.
   * Le superfici tendono a essere analizzate con una qualità più elevata quando vengono visualizzate in testa, anziché in un angolo superficiale.
   * Se il sistema di rilevamento Head di HoloLens ha esito negativo (il che può verificarsi a causa del rapido movimento dell'utente, della scarsa illuminazione, dei muri privi di funzionalità o delle fotocamere che vengono analizzate), questo può comportare errori nei dati di mapping spaziali. Eventuali errori di questo tipo verranno corretti nel corso del tempo quando l'utente continua a spostarsi ed eseguire l'analisi dell'ambiente.

* **Materiali di superficie**
   * I materiali presenti nelle superfici reali variano significativamente. Questi influiscono sulla qualità dei dati di mapping spaziali, perché influiscono sulla modalità di riflesso della luce a infrarossi.
   * Le superfici scure potrebbero non essere analizzate fino a quando non si avvicinano alla fotocamera, perché riflettono una minore luminosità.
   * Alcune superfici possono essere così scure che riflettono una luce troppo piccola per essere analizzate da qualsiasi distanza, in modo da introdurre errori di foratura nella posizione della superficie e talvolta anche dietro la superficie.
   * In particolare, le superfici lucide possono essere analizzate solo quando vengono visualizzate dall'inizio e non quando vengono visualizzate da un angolo superficiale.
   * I mirror, perché creano riflessi illusori di spazi e superfici reali, possono causare errori di Hole e allucinazioni.

* **Movimento della scena**
   * Il mapping spaziale si adatta rapidamente alle modifiche nell'ambiente, ad esempio il trasferimento di persone o l'apertura e la chiusura delle porte.
   * Tuttavia, il mapping spaziale può adattarsi solo alle modifiche in un'area quando tale area è chiaramente visibile alla fotocamera usata per l'analisi.
   * Per questo motivo, è possibile che questo adattamento ritardi la realtà, che può causare errori di Hole o allucinazione.
   * Ad esempio, un utente analizza un amico e quindi si sposta mentre l'amico lascia la stanza. Una rappresentazione ' fantasma ' dell'elemento Friend (un errore di allucinazione) rimarrà permanente nei dati del mapping spaziale, fino a quando l'utente non si riattiva e non esegue nuovamente l'analisi dello spazio in cui si trovava l'amico.

* **Interferenze di illuminazione**
   * La luce infrarossa ambientale nella scena potrebbe interferire con l'analisi, ad esempio la luce solare forte in arrivo attraverso una finestra.
   * In particolare, le superfici lucide possono interferire con l'analisi delle superfici adiacenti, la luce che provoca errori di distorsione.
   * Le superfici lucide che riflettono la luce direttamente nella fotocamera possono interferire con lo spazio vicino, causando allucinazioni mobili a mezz'aria o ritardando l'adattamento al movimento della scena.
   * Due dispositivi HoloLens nella stessa stanza non devono interferire tra loro, ma la presenza di più di cinque dispositivi HoloLens può causare un'interferenza.

Potrebbe essere possibile evitare o correggere alcuni di questi errori. Tuttavia, è consigliabile progettare l'applicazione in modo che l'utente sia in grado di raggiungere gli obiettivi anche in presenza di errori nei dati di mapping spaziali.

## <a name="the-environment-scanning-experience"></a>Esperienza di analisi dell'ambiente

HoloLens apprende le superfici nell'ambiente in cui vengono esaminate dall'utente. Nel corso del tempo, il HoloLens crea un'analisi di tutte le parti dell'ambiente che sono state osservate. Aggiorna inoltre l'analisi quando vengono osservate le modifiche nell'ambiente. Questa analisi verrà mantenute automaticamente tra i lanci dell'app.

Ogni applicazione che usa il mapping spaziale deve considerare la possibilità di fornire un'esperienza di analisi. processo attraverso il quale l'applicazione guida l'utente per l'analisi delle superfici necessarie per il corretto funzionamento dell'applicazione.

![Esempio di analisi](images/sr-mixedworld-140429-8pm-00068-1000px.png)<br>
*Esempio di analisi*

La natura di questa esperienza di analisi può variare significativamente a seconda delle esigenze di ogni applicazione, ma due principi principali dovrebbero guidare la progettazione.

In primo luogo, **una comunicazione chiara con l'utente rappresenta il problema principale**. L'utente deve sempre tenere presente se i requisiti dell'applicazione vengono soddisfatti. Quando non vengono soddisfatte, dovrebbe essere immediatamente chiaro all'utente perché questo è così e dovrebbe essere portato rapidamente a intraprendere l'azione appropriata.

In secondo luogo, **le applicazioni devono provare a trovare un equilibrio tra efficienza e affidabilità**. Quando è possibile eseguire questa operazione in modo **affidabile**, le applicazioni devono analizzare automaticamente i dati del mapping spaziale per salvare l'ora utente. Quando non è possibile eseguire questa operazione in modo affidabile, le applicazioni devono invece consentire all'utente di fornire rapidamente all'applicazione le informazioni aggiuntive necessarie.

Per semplificare la progettazione dell'esperienza di analisi corretta, considerare quali delle seguenti possibilità sono applicabili all'applicazione:

* **Nessuna esperienza di analisi**
   * Un'applicazione può funzionare perfettamente senza alcuna esperienza di analisi guidata; verranno fornite informazioni sulle superfici osservate nel corso del movimento naturale dell'utente.
   * Ad esempio, un'applicazione che consente all'utente di creare superfici con spray olografico richiede solo le informazioni sulle superfici attualmente visibili all'utente.
   * È possibile che l'ambiente sia già stato analizzato completamente se ne è uno in cui l'utente ha già impiegato molto tempo a usare HoloLens.
   * Tenere presente, tuttavia, che la fotocamera usata dal mapping spaziale può visualizzare solo 3.1 m davanti all'utente, quindi il mapping spaziale non saprà altre superfici distanti, a meno che l'utente non abbia osservato da una distanza più vicina in passato.
   * Quindi, l'utente riconosce quali superfici sono state analizzate, l'applicazione deve fornire un feedback visivo a questo effetto, ad esempio il cast di ombre virtuali su superfici analizzate può aiutare l'utente a collocare gli ologrammi su tali superfici.
   * Per questo caso, i volumi di delimitazione dell'osservatore della superficie spaziale devono aggiornare ogni frame a un sistema di [coordinate spaziali](coordinate-systems.md)con blocco del corpo, in modo che seguano l'utente.

* **Trovare un percorso adatto**
   * Un'applicazione può essere progettata per essere utilizzata in una posizione con requisiti specifici.
   * Ad esempio, l'applicazione può richiedere un'area vuota per l'utente in modo da poter provare a utilizzare in modo sicuro il kung-fu olografico.
   * Le applicazioni devono comunicare i requisiti specifici per l'utente in primo piano e rinforzarli con un chiaro feedback visivo.
   * In questo esempio, l'applicazione deve visualizzare l'ambito dell'area vuota richiesta e evidenziare visivamente la presenza di oggetti indesiderati all'interno di questa zona.
   * Per questo caso, i volumi di delimitazione dell'osservatore della superficie spaziale devono usare un [sistema di coordinate spaziali](coordinate-systems.md) con blocco globale nella posizione scelta.

* **Trovare una configurazione adatta delle superfici**
   * È possibile che un'applicazione richieda una configurazione specifica delle superfici, ad esempio due pareti grandi, piatte e contrapposte, per creare una sala olografica di mirror.
   * In questi casi, l'applicazione dovrà analizzare le superfici fornite dal mapping spaziale per rilevare le superfici appropriate e indirizzare l'utente verso loro.
   * L'utente deve disporre di un'opzione di fallback se l'analisi della superficie dell'applicazione non è completamente affidabile. Se, ad esempio, l'applicazione identifica erroneamente un portale come un muro Flat, l'utente deve disporre di un modo semplice per correggere l'errore.

* **Analizza parte dell'ambiente**
   * Un'applicazione può voler acquisire solo parte dell'ambiente, come indicato dall'utente.
   * Ad esempio, l'applicazione analizza parte di una stanza, in modo che l'utente possa pubblicare un annuncio olografico per la mobilia che desidera vendere.
   * In questo caso, l'applicazione deve acquisire i dati di mapping spaziali all'interno delle aree osservate dall'utente durante la relativa analisi.

* **Analizza l'intera stanza**
   * Un'applicazione può richiedere un'analisi di tutte le superfici nella stanza corrente, incluse quelle dietro l'utente.
   * Ad esempio, un gioco può mettere l'utente nel ruolo di Gulliver, in assiege da centinaia di piccoli Lillipuziani che si avvicinano da tutte le direzioni.
   * In questi casi, l'applicazione dovrà determinare il numero di superfici presenti nella stanza corrente è già stata analizzata e indicare allo sguardo dell'utente di colmare gap significative.
   * La chiave per questo processo è fornire feedback visivo che rende chiaro all'utente quali superfici non sono state ancora analizzate. L'applicazione può ad esempio usare la [nebbia basata sulla distanza](https://msdn.microsoft.com/library/windows/desktop/bb173401%28v=vs.85%29.aspx) per evidenziare visivamente le aree non coperte dalle superfici di mapping spaziale.

* **Eseguire uno snapshot iniziale dell'ambiente**
   * Un'applicazione potrebbe voler ignorare tutte le modifiche apportate all'ambiente dopo aver eseguito uno snapshot iniziale.
   * Questa operazione può essere utile per evitare l'intralcio di dati creati dall'utente strettamente collegati allo stato iniziale dell'ambiente.
   * In questo caso, l'applicazione deve creare una copia dei dati di mapping spaziale nello stato iniziale al termine dell'analisi.
   * Le applicazioni devono continuare a ricevere gli aggiornamenti dei dati di mapping spaziale se gli ologrammi rimangono ancora correttamente bloccati dall'ambiente.
   * Gli aggiornamenti continui dei dati di mapping spaziali consentono inoltre di visualizzare le modifiche apportate, chiarendo all'utente le differenze tra gli stati precedenti e quelli presenti nell'ambiente.

* **Eseguire snapshot dell'ambiente avviati dall'utente**
   * Un'applicazione può solo voler rispondere alle modifiche ambientali quando richiesto dall'utente.
   * Ad esempio, l'utente può creare più "statue" 3D di un amico acquisendo le loro pose in momenti diversi.

* **Consenti all'utente di modificare l'ambiente**
   * Un'applicazione può essere progettata in modo da rispondere in tempo reale a tutte le modifiche apportate nell'ambiente dell'utente.
   * Ad esempio, l'utente che disegna una tenda potrebbe attivare la "modifica della scena" per una riproduzione olografica che avviene sull'altro lato.

* **Guida dell'utente per evitare errori nei dati di mapping spaziale**
   * Un'applicazione potrebbe voler fornire indicazioni all'utente durante l'analisi dell'ambiente.
   * Ciò consente all'utente di evitare determinati tipi di [errori nei dati di mapping spaziali](spatial-mapping-design.md#what-influences-spatial-mapping-quality), ad esempio rimanendo fuori da finestre o mirror luminosi.

Un ulteriore dettaglio da tenere presente è che il ' intervallo ' dei dati di mapping spaziali non è illimitato. Sebbene il mapping spaziale crei un database permanente di spazi di grandi dimensioni, rende solo i dati disponibili per le applicazioni in una "bolla" di dimensioni limitate per l'utente. Quindi, se si inizia dall'inizio di un lungo corridoio e ci si sposta abbastanza lontano dall'inizio, infine le superfici spaziali all'inizio scompariranno. Naturalmente è possibile mitigare questo problema memorizzando nella cache tali superfici nell'applicazione dopo che sono scomparse dai dati di mapping spaziali disponibili.

## <a name="mesh-processing"></a>Elaborazione mesh

Potrebbe essere utile rilevare tipi comuni di errori nelle superfici e filtrare, rimuovere o modificare i dati del mapping spaziale in base alle esigenze.

Tenere presente che i dati di mapping spaziali sono destinati a essere il più fedele possibile a superfici reali, quindi qualsiasi elaborazione applicata rischia di spostare ulteriormente le superfici dalla "verità".

Di seguito sono riportati alcuni esempi di diversi tipi di elaborazione di mesh che possono risultare utili:

* **Riempimento foro**
   * Se non è possibile eseguire l'analisi di un oggetto di piccole dimensioni con un materiale scuro, questo lascerà un foro nell'area circostante.
   * I buchi influiscono sull'occlusione: gli ologrammi possono essere visualizzati in un foro in una superficie reale opaca.
   * I buchi influiscono su raycasts: se si usa raycasts per aiutare gli utenti a interagire con le superfici, potrebbe essere auspicabile che questi raggi attraversino buchi. Una mitigazione consiste nell'usare un bundle di più raycasts che coprono un'area opportunamente dimensionata. Ciò consentirà di filtrare i risultati "outlier", in modo che anche se un Raycast passa attraverso un piccolo foro, il risultato dell'aggregazione sarà ancora valido. Tuttavia, tenere presente che questo approccio comporta un costo computazionale.
   * I buchi influiscono sui conflitti di fisica: un oggetto controllato dalla simulazione fisica può essere trascinato in una buca al pavimento e perso.
   * È possibile algoritmicamente colmare tali buchi nella mesh della superficie. Tuttavia, sarà necessario ottimizzare l'algoritmo in modo che i "buchi reali", ad esempio le finestre e le porte, non vengano compilati. Può essere difficile distinguere in modo affidabile ' buchi reali ' da' buchi immaginari ', quindi è necessario provare a usare euristiche diverse, ad esempio ' dimensioni ' è forma limite '.

* **Rimozione delle allucinazioni**
   * I riflessi, le luci luminose e gli oggetti mobili possono lasciare "allucinazioni" prolungate, fluttuanti a metà aria.
   * Le allucinazioni influiscono sull'occlusione: le allucinazioni possono essere visibili come forme scure che si avvicinano a e occlusione altri ologrammi.
   * Le allucinazioni influiscono su raycasts: se si usa raycasts per aiutare gli utenti a interagire con le superfici, questi raggi potrebbero raggiungere una allucinazione invece della superficie sottostante. Come per i buchi, una mitigazione consiste nell'usare molti raycasts invece di un singolo Raycast, ma anche in questo caso il costo di calcolo sarà elevato.
   * Le allucinazioni influiscono sui conflitti di fisica: un oggetto controllato dalla simulazione fisica può rimanere bloccato contro un'allucinazione e non essere in grado di spostarsi in un'area di spazio apparentemente chiara.
   * È possibile filtrare tali allucinazioni dalla mesh della superficie. Tuttavia, come per i buchi, sarà necessario ottimizzare l'algoritmo in modo da evitare la rimozione di oggetti di piccole dimensioni, ad esempio luci e maniglie degli sportelli.

* **Smussatura**
   * Il mapping spaziale può restituire superfici che sembrano essere ruvide o ' noisy ' rispetto alle controparti reali.
   * La fluidità influiscono sui conflitti di fisica: se il piano è ruvido, una palla da golf simulata fisicamente potrebbe non essere posizionata senza intoppi in una linea retta.
   * La fluidità influisce sul rendering: se una superficie viene visualizzata direttamente, le normali superfici ruvide possono influire sul proprio aspetto e interferire con l'aspetto "Pulisci". È possibile mitigare questo problema usando l'illuminazione e le trame appropriate nello shader usato per il rendering della superficie.
   * È possibile smussare l'rugosità in una mesh di superficie. Questa operazione può tuttavia comportare la disattivazione della superficie dalla superficie reale corrispondente. La gestione di una corrispondenza di chiusura è importante per produrre un'occlusione olografica accurata e consentire agli utenti di ottenere interazioni precise e prevedibili con le superfici olografiche.
   * Se è necessaria solo una modifica cosmetica, può essere sufficiente per smussare i normali vertici senza modificare le posizioni del vertice.

* **Ricerca del piano**
   * Esistono diverse forme di analisi che un'applicazione può voler eseguire sulle superfici fornite dal mapping spaziale.
   * Un semplice esempio è' ricerca del piano '; identificazione delle aree delimitate e principalmente planari delle superfici.
   * Le aree planari possono essere usate come superfici di lavoro olografiche, aree in cui il contenuto olografico può essere inserito automaticamente dall'applicazione.
   * Le aree planari possono vincolare l'interfaccia utente per guidare gli utenti a interagire con le superfici più adatte alle proprie esigenze.
   * Le aree planari possono essere usate come nel mondo reale, per le controparti olografiche in oggetti funzionali quali schermi LCD, tabelle o lavagne.
   * Le aree piane possono definire aree di riproduzione, che costituiscono la base dei livelli di videogame.
   * Le aree planari possono aiutare gli agenti virtuali a esplorare il mondo reale, identificando le aree del piano su cui è probabile che le persone reali possano procedere.

## <a name="prototyping-and-debugging"></a>Prototipi e debug

### <a name="useful-tools"></a>Strumenti utili
* L' [emulatore di HoloLens](using-the-hololens-emulator.md) può essere usato per sviluppare applicazioni usando il mapping spaziale senza accedere a un HoloLens fisico. Consente di simulare una sessione in tempo reale in un HoloLens in un ambiente realistico, con tutti i dati normalmente utilizzati dall'applicazione, tra cui HoloLens Motion, i sistemi di coordinate spaziali e le mesh di mapping spaziale. Questo può essere usato per fornire un input affidabile e ripetibile, che può essere utile per il debug dei problemi e la valutazione delle modifiche apportate al codice.
* Per riprodurre uno scenario, acquisire i dati di mapping spaziali sulla rete da un HoloLens attivo, quindi salvarli su disco e riutilizzarli nelle sessioni di debug successive.
* La [visualizzazione 3D del portale per dispositivi Windows](using-the-windows-device-portal.md#3d-view) consente di visualizzare tutte le superfici spaziali attualmente disponibili tramite il sistema di mapping spaziale. In questo modo viene fornita una base di confronto per le superfici spaziali all'interno dell'applicazione. ad esempio, è possibile stabilire facilmente se eventuali superfici spaziali risultano mancanti o visualizzate nella posizione sbagliata.

### <a name="general-prototyping-guidance"></a>Indicazioni generali sulla prototipazione
* Poiché gli [errori](spatial-mapping-design.md#what-influences-spatial-mapping-quality) nei dati di mapping spaziali possono influire fortemente sull'esperienza dell'utente, è consigliabile testare l'applicazione in un'ampia gamma di ambienti.
* Non rimanere intrappolato nell'abitudine di testare sempre nella stessa posizione, ad esempio nella propria scrivania. Assicurarsi di eseguire il test su varie superfici di posizioni, forme, dimensioni e materiali differenti.
* Analogamente, mentre i dati sintetici o registrati possono essere utili per il debug, non dipendono troppo dagli stessi test case. Questo può ritardare la ricerca di problemi importanti che potrebbero essere rilevati in precedenza da più test.
* È consigliabile eseguire i test con utenti reali (e preferibilmente senza coach), perché non possono usare il HoloLens o l'applicazione nello stesso modo in cui si esegue. In realtà, potrebbe sorprendere il comportamento, le conoscenze e le ipotesi delle persone divergenti.

## <a name="see-also"></a>Vedere anche
* [Visualizzazione della scansione dello spazio](room-scan-visualization.md)
* [Progettazione dell'audio spaziale](spatial-sound-design.md)
* [Persistenza in Unity](persistence-in-unity.md)

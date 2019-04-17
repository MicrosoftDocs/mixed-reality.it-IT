---
title: Mapping spaziale
description: Mapping spaziale fornisce una rappresentazione dettagliata delle superfici reali nell'ambiente che circonda il HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: mapping spaziale, HoloLens, realtà mista, la ricostruzione della superficie, mesh, sr
ms.openlocfilehash: 31abeca624512f1d5e721dbe879ca2243cf41345
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605040"
---
# <a name="spatial-mapping"></a>Mapping spaziale

Mapping spaziale fornisce una rappresentazione dettagliata delle superfici reali nell'ambiente che circonda HoloLens, permettendo agli sviluppatori di creare un'esperienza di realtà mista convincente. Unendo il mondo reale con il mondo virtuale, un'applicazione può rendere vntana sembra reale. Le applicazioni più naturalmente allineare anche le aspettative degli utenti, fornendo le interazioni e comportamenti reali familiari.

<br>

>[!VIDEO https://www.youtube.com/embed/zff2aQ1RaVo]

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Funzionalità</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (dal 1 ° generazione)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></th>
</tr><tr>
<td> Mapping spaziale</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>



## <a name="conceptual-overview"></a>Panoramica concettuale

![Superfici mesh che coprono una chat room](images/SurfaceReconstruction.jpg)<br>
*Un esempio di una rete mesh di mapping spaziale che coprono una chat room*

I due tipi di oggetto principale usati per il mapping spaziale sono 'Observer di superficie spaziale' e la "superficie spaziale".

L'applicazione fornisce all'osservatore superficie spaziale con uno o più volumi di delimitazione, per definire le aree di spazio in cui l'applicazione desidera ricevere i dati di mapping spaziale. Per ognuno di questi volumi, mapping spaziale fornirà l'applicazione con un set di dispositivi Surface spaziale.

Questi volumi sia fermo (in una posizione fissa rispetto al mondo reale) o può essere collegate a HoloLens (si sposta, ma non ruotano, con la HoloLens durante lo spostamento tramite l'ambiente). Ogni area spaziale descrive superfici reali in un volume dello spazio, rappresentato come una mesh triangolare collegata in un mondo di blocco small [sistema di coordinate spaziale](coordinate-systems.md).

Quando si verificano modifiche all'ambiente, verranno visualizzato spaziali superfici di HoloLens consente di raccogliere nuovi dati sull'ambiente, non vengono più visualizzati e modificare.

## <a name="common-usage-scenarios"></a>Scenari di utilizzo comuni

![Illustrazioni di scenari di utilizzo comuni di Mapping spaziale: Posizionamento, relative all'occlusione, fisica e l'esplorazione](images/sm-concepts-1000px.png)

### <a name="placement"></a>Posizionamento

Mapping spaziale fornisce le applicazioni con la possibilità di presentare naturale e familiare forme di interazione per l'utente. Ciò che potrebbe essere più naturale che verso il basso l'inserimento del telefono sulla scrivania?

Vincolare il posizionamento dei vntana (o più in generale, qualsiasi selezione di percorsi spaziale) si trovi su superfici fornisce un mapping naturale tra 3D (punto nello spazio) a 2D (un punto nell'area). In questo modo si riduce la quantità di informazioni l'utente deve fornire all'applicazione e pertanto le interazioni utente più veloce, semplifica e rende più preciso. Ciò vale soprattutto perché 'distanza' non è un elemento viene usata per eseguire fisicamente comunicare ad altri utenti o ai computer. Quando si posiziona il puntatore con il dito, si specifica una direzione, ma non una distanza.

Un'importante precisazione qui è che, quando un'applicazione deduce distanza dalla direzione (ad esempio eseguendo un raycast lungo la direzione sguardo dell'utente per trovare più vicini superficie spaziale), questa deve restituire i risultati che l'utente è in grado di stimare in modo affidabile. In caso contrario, l'utente perderà il senso di controllo e ciò può risultare frustrante. Un metodo che può essere utile consiste nell'eseguire più raycasts anziché di uno. I risultati aggregati devono essere più fluida e più prevedibile, meno soggetti a influenzare dai risultati temporanei 'outlier' (come può essere causato da raggi che attraversa aree libere di piccole dimensioni o hanno raggiunto piccole parti di geometria di cui l'utente non riconosce). Aggregazione o livellamento può essere eseguita anche nel tempo; è ad esempio possibile limitare la velocità massima in corrispondenza del quale ologramma può variare in termini di distanza dall'utente. Semplicemente limitando il valore della distanza minima e massima può risultare utili, in modo che l'ologrammi lo spostamento non improvvisamente entra la distanza da subito o in modo anomalo in volto dell'utente.

Applicazioni possono anche usare la forma e la direzione delle superfici al posizionamento ologrammi Guida. Presidenti holographic non dovrebbero penetrare attraverso le pareti e devono rimanere flush con la parte intera nemmeno quando risulta leggermente irregolare. Questo tipo di funzionalità sarebbe probabilmente si basano sull'uso di collisioni fisica anziché semplicemente raycasts, problemi simili, tuttavia verranno applicate. Se l'ologrammi inseriti ha molti poligoni piccoli che attaccato, come le gambe su un chair, può avere senso per espandere la rappresentazione fisica di tali poligoni in modo più larghi e più uniforme, in modo che siano più in grado di far scorrere su superfici spaziali senza l'acquisizione.

Input dell'utente può essere semplificato da subito interamente estremo, e superfici spaziale possono essere utilizzate per eseguire il posizionamento di ologramma completamente automatico. Ad esempio, l'applicazione è stato possibile posizionare un cambio di luce holographic in un punto sulla bacheca per l'utente prema. La stessa avvertenza sulla prevedibilità si applica a doppio qui; Se l'utente si aspetta controllo sul posizionamento ologrammi, ma l'applicazione non sempre si impono vntana in cui si aspettano (se il cambio di luce appare in un punto che l'utente non riesce a raggiungere), si tratterà frustrante. Può effettivamente essere peggio eseguire la selezione host automatica che richiede la correzione utente parte del tempo, rispetto al solo richiedere all'utente di eseguire sempre il posizionamento stessi; perché è la selezione host automatica ha esito positivo *previsto*, aspetto correzione manuale di un carico di lavoro.

Si noti inoltre che la capacità di un'applicazione di usare le superfici spaziali per selezione host dipende molto dell'applicazione [scansione esperienza](spatial-mapping-design.md#the-environment-scanning-experience). Se un'area non è stata analizzata, quindi non è utilizzabile per la selezione host. È compito dell'applicazione per chiarire all'utente, in modo che possa essere aiutare nuove superfici di scansione o selezionare un nuovo percorso.

Feedback visivo all'utente è di fondamentale importanza durante la selezione host. L'utente dovrà comprendere dove viene eseguita in relazione l'area più vicina con l'ologrammi [messa a terra effetti](spatial-mapping.md#visualization). È necessario comprendere perché lo spostamento dei loro ologrammi da vincolare (ad esempio, a causa di un conflitto con un altro nelle vicinanze area). Se è possibile posizionare ologramma nel percorso corrente, quindi feedback visivo dovrebbe chiarire perché non. Ad esempio, se l'utente sta tentando di posizionare un divano holographic bloccata a metà alla presa a muro, quindi le parti di divano dietro la parete devono pulsate in un colore pecora. O viceversa, se l'applicazione non è possibile trovare una superficie spaziale in una posizione in cui l'utente può visualizzare un'area del mondo reale, quindi l'applicazione dovrebbe chiarire questo. L'assenza di un effetto di messa a terra in quest'area ovvia potrebbe raggiungere questo scopo.

### <a name="occlusion"></a>Occlusione

Uno degli usi principali delle superfici di mapping spaziale è semplicemente vntana nasconde i colori. Questo comportamento semplice ha un impatto notevole sul realismo percepito del vntana, contribuendo a creare un senso visceral che effettivamente allo stesso spazio fisico dell'utente.

Relative all'occlusione fornisce anche informazioni per l'utente. Quando ologramma sembra essere bloccati da un'area del mondo reale, questo fornisce altre indicazioni visive per quanto riguarda la posizione di tale ologrammi nel mondo. Viceversa, relative all'occlusione può anche utili *nascondere* informazioni da parte dell'utente; vntana occluding dietro walls può ridurre il disordine visual in un modo molto intuitivo. Per nascondere o visualizzare ologramma, l'utente deve semplicemente spostare propria testa.

È anche utilizzabile occlusione preparare gli obiettivi per un'interfaccia utente naturale in base alle interazioni fisiche familiarità; Se ologramma viene bloccato da un'area è perché tale area è in tinta unita, pertanto, l'utente dovrebbe aspettarsi che saranno l'ologrammi *entri in conflitto* con quello della superficie di attacco e non è sufficiente passare attraverso di esso.

In alcuni casi, non è opportuna relative all'occlusione di vntana. Se un utente deve essere in grado di interagire con un ologrammi, devono essere in grado di vederlo - anche se è protetto da un'area del mondo reale. In questi casi, è in genere opportuno eseguire il rendering di questo tipo ologramma in modo diverso quando si viene bloccato (ad esempio, riducendo la luminosità). In questo modo, l'utente sarà in grado di individuare visivamente l'ologrammi, ma si continuerà a essere consapevoli che è protetto da un elemento.

### <a name="physics"></a>Fisica

L'utilizzo della simulazione fisica è un altro modo in cui mapping spaziale può essere utilizzato per potenziare la *presenza* di vntana nello spazio fisico dell'utente. Quando la palla holographic elastica esegue il roll realisticamente off mia scrivania, bounces tra la parte intera e non viene più visualizzata sotto il divano, potrebbe essere difficile per me ritiene che non è disponibile.

Simulazione di effetti fisici fornisce inoltre la possibilità che un'applicazione può utilizzare interazioni naturali e familiare basato sulla fisica. Lo spostamento di una parte di arredi holographic intorno sul pavimento probabilmente risulterà più semplice per l'utente se i mobili risponde come se erano scorrevole tra la parte intera con l'inerzia appropriato e problemi.

Per generare comportamenti fisici realistici, probabilmente sarà necessario eseguire alcune [mesh elaborazione](spatial-mapping.md#mesh-processing) , ad esempio la compilazione aree libere di rimozione mobile psicosi e anti-aliasing approssimativo superfici.

Sarà anche necessario prendere in considerazione la modalità dell'applicazione [scansione esperienza](spatial-mapping-design.md#the-environment-scanning-experience) influenza la simulazione di fisica. In primo luogo, mancante superfici non entri in conflitto con un valore specifico. cosa accade quando la palla elastica esegue il roll verso il basso i corridoi e oltre la fine del mondo noto? In secondo luogo, è necessario decidere se si continuerà a rispondere alle modifiche nell'ambiente nel corso del tempo. In alcuni casi, si dovranno rispondere più rapidamente possibile; ad esempio se l'utente Usa le porte e mobili come mobile pareti o barricate nella difesa contro un tempest delle frecce di Roman in ingresso. In altri casi, tuttavia, è possibile ignorare i nuovi aggiornamenti; guidare l'auto sportiva holographic tutto il tavolo del piano improvvisamente non può essere pertanto divertente se decide il cane posizionata al centro della traccia.

### <a name="navigation"></a>Navigazione

Applicazioni possono usare dati di mapping spaziale concedere holographic caratteri (o gli agenti) la possibilità di esplorare il mondo reale in modo identico a una persona reale. Ciò consente di consolidare la presenza di caratteri holographic da limitandoli allo stesso set di comportamenti familiari e naturali a quelle dell'utente e gli amici.

Funzionalità di navigazione può essere utile anche agli utenti. Dopo aver compilata una mappa di navigazione in una determinata area, può essere condivisa per fornire indicazioni holographic per nuovi utenti familiari con tale posizione. Questa mappa può essere progettata per garantire la tua pedonale '' il flusso di traffico in modo uniforme o per evitare incidenti nelle posizioni pericolose, come siti di costruzione.

I principali problemi tecnici coinvolti nell'implementazione della funzionalità di navigazione sarà affidabile rilevamento delle superfici è percorribile (esseri umani non walk sulle tabelle!) e normale adattamento alle modifiche nell'ambiente (gli esseri umani non illustrati porte chiuse!). Mesh può richiedere alcune [elaborazione](spatial-mapping.md#mesh-processing) prima che sia utilizzabile per la navigazione da un carattere virtuale e la pianificazione percorso. Anti-aliasing della rete e la rimozione psicosi può contribuire a evitare caratteri diventando bloccate. È anche possibile semplifica drasticamente la mesh per velocizzare la pianificazione percorso del carattere e i calcoli di navigazione. Questi problemi hanno ricevuto una grande quantità di attenzione allo sviluppo di tecnologia televisione e molti della documentazione di ricerca disponibili in questi argomenti.

Si noti che la funzionalità NavMesh incorporata in Unity non è utilizzabile con le superfici di mapping spaziale. Infatti, le superfici di mapping spaziale non sono noti fino all'applicazione viene avviata, mentre i file di dati NavMesh devono essere generati dagli asset di origine anticipatamente. Si noti anche che, al sistema di mapping spaziale non fornirà [informazioni su superfici molto lontano](spatial-mapping-design.md#the-environment-scanning-experience) dalla posizione corrente dell'utente. In modo che l'applicazione deve 'ricordare' superfici di se stessa se deve generare una mappa di un'area di dimensioni molto grande.

### <a name="visualization"></a>Visualizzazione

La maggior parte dei casi è opportuno che le superfici spaziale sia invisibile; Per ridurre al minimo confusioni a livello visivo e lasciare il real world parlino da soli. Tuttavia, talvolta è utile visualizzare le superfici di mapping spaziale direttamente, nonostante il fatto che le relative controparti reali siano già visibili.

Ad esempio, quando l'utente sta tentando di posizionare ologramma su una superficie (inserimento di un file CAB holographic su una parete, ad esempio) può essere utile per 'zero' l'ologrammi eseguendo il cast di un'ombreggiatura nell'area. Ciò offre all'utente un molto senso più chiara la prossimità fisica esatta tra l'ologrammi e l'area. Questo è un esempio dell'esercitazione più generale di visivamente 'anteprima' una modifica prima che l'utente esegue il commit a esso.

Visualizzando le superfici, l'applicazione può condividere con l'utente la comprensione dell'ambiente. Ad esempio, un gioco da tavolo holographic è stato possibile visualizzare le superfici orizzontale che lo ha identificato come "tabelle", in modo che l'utente sappia dove dovrebbe passano per interagire.

Le superfici di visualizzazione può essere utile per mostrare l'utente nelle vicinanze spazi che sono nascosti dalla visualizzazione. Questo è stato possibile fornire un modo semplice per consentire all'utente di accedere ai loro cucina (e tutti i relativi contenuti vntana) da loro salotto.

La mesh superficie fornita da mapping spaziale non può essere particolarmente 'clean'. Pertanto è importante per visualizzarle nel modo appropriato. Calcoli di illuminazione tradizionale mettere in evidenza gli errori nelle normali alla superficie in maniera distrazione, mentre 'clean' trame proiettate nell'area può essere utile per conferirgli un aspetto più ordinato. È anche possibile eseguire [mesh elaborazione](spatial-mapping.md#mesh-processing) per migliorare le proprietà di rete, prima del rendering di aree.

## <a name="using-the-surface-observer"></a>Usando l'osservatore Surface

Il punto di partenza per il mapping spaziale è l'osservatore della superficie. Flusso del programma è come segue:
* Creare un oggetto osservatore surface
   * Specificare uno o più volumi spaziali, per definire le aree di interesse in cui l'applicazione desidera ricevere i dati di mapping spaziale. Un volume spaziale è semplicemente una forma che definisce un'area di spazio, ad esempio una finestra o una sfera.
   * Usare un volume spaziale con un sistema di coordinate world-bloccato al spaziale per identificare un'area predefinita del mondo fisico.
   * Usare un volume spaziale, aggiornato a ogni fotogramma con un bloccato corpo spaziale sistema di coordinate, per identificare un'area di spazio che consente di spostare (ma non ruota) con l'utente.
   * Questi volumi spaziali possono essere modificati successivamente in qualsiasi momento, come lo stato dell'applicazione o le modifiche dell'utente.
* Usare il polling o notifica per recuperare informazioni su superfici spaziali
   * Si potrebbe 'esegue il polling' l'osservatore superficie per lo stato di superficie spaziale in qualsiasi momento. In alternativa, è possibile registrarsi per ' superfici "evento di modifica dell'osservatore superficie, che invierà una notifica all'applicazione quando sono state modificate le superfici spaziale.
   * Per un volume dinamico spaziale, ad esempio del cono di visualizzazione, o un volume bloccato corpo, le applicazioni dovranno il polling delle modifiche ogni fotogramma, impostare l'area di interesse e quindi ottenuto il set corrente di superfici spaziale.
   * Per un volume statico, ad esempio un cubo bloccato mondo che coprono una singola stanza, le applicazioni possono registrare per l'evento "superfici modificato" ricevere una notifica quando le superfici spaziale all'interno di tale volume sia stato modificato.
* Processo di replica delle modifiche
   * Scorrere il set specificato di dispositivi Surface spaziale.
   * Classificare spaziali superfici di aggiunta, modificata o rimossa.
   * Per ogni area spaziale aggiunti o modificati, se appropriato, inviare una richiesta asincrona per ricevere mesh aggiornato che rappresenta lo stato corrente dell'area al livello desiderato di dettaglio.
* Elaborare la richiesta asincrona mesh (ulteriori dettagli nelle sezioni seguenti).

## <a name="mesh-caching"></a>La memorizzazione nella cache della rete

Le superfici spaziali sono rappresentate da triangolari ad alta densità. L'archiviazione, il rendering e l'elaborazione di queste trame possono uso intensivo di risorse di calcolo e archiviazione. Di conseguenza, ogni applicazione deve adottare una rete mesh di memorizzazione nella cache lo schema appropriato alle proprie esigenze, per ridurre al minimo le risorse usate per l'elaborazione di rete e archiviazione. Questo schema è necessario determinare quali trame per mantenere e quali eliminare, nonché la modalità di aggiornamento della rete per ogni area spaziale.

Numerose le considerazioni illustrate sono direttamente viene informato del modo in cui l'applicazione dovrebbe raggiungere il mesh di memorizzazione nella cache. È necessario considerare come l'utente si sposta tramite l'ambiente, quali aree sono necessarie, quando sarà possibile osservare diverse superfici e quando le modifiche nell'ambiente devono essere acquisite.

Durante l'interpretazione l'evento 'superfici modificato' fornito da observer surface, la trama di base per la logica di memorizzazione nella cache è come segue:
* Se l'applicazione viene rilevato un ID di superficie spaziale non ha mai visto prima, deve trattarlo come una nuova superficie spaziale.
* Se l'applicazione non vede una superficie spaziale con un ID noto, ma con una nuova ora di aggiornamento, deve trattarlo come una superficie spaziale aggiornata.
* Se l'applicazione non è più visibile un'area spaziale con un ID noto, deve trattarlo come una superficie spaziale rimossa.

In questo caso, ogni applicazione quindi apportare le seguenti opzioni:
* Per nuove superfici spaziali, devono essere richieste mesh?
   * In genere mesh devono essere richieste immediatamente per nuove superfici di spaziale, che possono fornire informazioni utili all'utente.
   * Tuttavia, nuove superfici spaziali quasi e davanti all'utente devono avere la priorità e il mesh devono essere richieste prima di tutto.
   * Se la nuova trama non è necessaria, se ad esempio l'applicazione ha in modo permanente o temporaneo 'bloccato' relativo modello di ambiente, quindi dovrebbe non essere richieste.
* Per le superfici spaziali aggiornate, devono essere richieste mesh?
   * Superfici spaziali aggiornate quasi e davanti all'utente devono avere la priorità e il mesh devono essere richieste prima di tutto.
   * Potrebbe anche essere opportuno dare a priorità più alta a nuove superfici rispetto all'aggiornamento superfici, soprattutto durante l'esperienza di analisi.
   * Per limitare i costi di elaborazione, le applicazioni potrebbero voler limitare la frequenza con cui elaborano gli aggiornamenti alle superfici spaziale.
   * È possibile dedurre che le modifiche apportate a una superficie spaziale sono minori, ad esempio se i limiti dell'area di sono troppo piccoli, nel qual caso l'aggiornamento potrebbe non essere abbastanza importante da processo.
   * Gli aggiornamenti alle superfici spaziale all'esterno dell'area di interesse dell'utente corrente possono essere ignorati, anche se in questo caso, potrebbe risultare più efficiente per modificare i volumi di delimitazione spaziali in uso dall'area osservatore.
* Per le superfici spaziali rimosse, devono essere eliminati mesh?
   * In genere mesh devono essere eliminati immediatamente per superfici spaziali rimosse, in modo che rimanga corretto relative all'occlusione di ologramma.
   * Tuttavia, se l'applicazione ha motivo di ritenere che una superficie spaziale verrà visualizzato nuovamente a breve (ad esempio in base alla progettazione dell'esperienza utente), quindi potrebbe essere più efficiente per il mantenimento di to annullare il mesh e ricrearlo in un secondo momento.
   * Se l'applicazione sta compilando un modello di ambiente dell'utente su larga scala quindi potrebbe non vogliono eliminare tutte le reti mesh affatto. Dovranno comunque limitare dell'utilizzo delle risorse, tuttavia, probabilmente per le reti mesh di spooling su disco come superfici spaziale non vengono più visualizzati.
   * Si noti che alcuni eventi rari relativamente durante la generazione di superficie spaziale possono causare superfici spaziali da sostituire con nuove superfici spaziale in una posizione analoga ma con ID diversi. Di conseguenza, le applicazioni che non si desidera rimuovere un'area rimossa necessario prestare non end backup con più elevata overlapped spaziali superficie mesh che coprono lo stesso percorso.
* Mesh devono essere eliminati per eventuali altre superfici spaziale?
   * Anche se una superficie spaziale non esiste, se non è più utile per l'esperienza dell'utente, quindi deve essere rimossa. Ad esempio, se l'applicazione 'sostituisce' chat room su altro lato di incoraggiare con uno spazio virtuale alternativo quindi le superfici spaziali in tale spazio non è più importante.

Ecco un'esempio mesh strategia di memorizzazione, tramite isteresi spaziali e temporale:
* Si consideri un'applicazione possa usare un volume spaziale a forma di cono di interesse che segue sguardo dell'utente in quanto Guardatevi intorno e spostano.
* Una superficie spaziale può interrompersi temporaneamente da questo volume semplicemente perché l'utente cerca dalla superficie o passaggi più avanzato rispetto... solo per eseguire ricerche indietro oppure si avvicina nuovamente un momento in cui in un secondo momento. In questo caso, eliminando e ricreando il mesh per questa area rappresenta a numerose elaborazioni ridondanti.
* Per ridurre il numero di modifiche elaborato, l'applicazione usa due osservatori di superficie spaziali, uno contenute all'interno di altra. Volume di maggiori dimensioni è sferico e segue l'utente 'in modo differito'; Sposta solo quando necessario, per verificare che il suo centro non superi 2,0 metri dell'utente.
* Mesh superficie spaziale nuove e aggiornate vengono sempre elaborate dalla più piccola osservatore surface interna, ma le reti mesh vengono memorizzati nella cache fino a quando non vengono escluse dall'osservatore superficie outer più grande. In questo modo l'applicazione per evitare l'elaborazione di molte modifiche ridondante a causa di spostamenti di utente locale.
* Poiché una superficie spaziale anche scompaiano temporaneamente a causa di una perdita di rilevamento, l'applicazione può posticipare il scartata superfici spaziali rimosse durante la perdita di rilevamento.
* In genere, un'applicazione deve valutare il compromesso tra l'elaborazione degli aggiornamenti ridotto e una maggiore quantità di memoria per determinare la strategia di memorizzazione ideale.

## <a name="rendering"></a>Per il rendering

Esistono tre modi principali in cui le reti mesh di mapping spaziale tendono a essere utilizzato per il rendering:
* Per la visualizzazione di surface
   * Spesso è utile visualizzare le superfici spaziali direttamente. Ad esempio, cast 'shadows' dagli oggetti su superfici spaziali possono fornire indicazioni visive utili all'utente mentre si inseriscono vntana su superfici.
   * Un aspetto da tenere presente è che mesh spaziali sono diverse per il tipo di trame che potrebbe creare un artista 3D. La topologia di triangolo non sarà come 'clean' come topologia creati dall'uomo e dalla ne risentiranno la mesh [diversi errori](spatial-mapping-design.md#what-influences-spatial-mapping-quality).
   * Per creare un piacevole estetici visual, pertanto è consigliabile eseguire alcune [mesh elaborazione](spatial-mapping.md#mesh-processing), ad esempio in aree libere di riempimento o smooth normali alla superficie. È anche possibile usare uno shader a trame progettato artista progetto nella mesh anziché direttamente visualizzazione topologia a maglia e normali.
* Per occluding vntana dietro aree del mondo reale
   * Superfici spaziali possono eseguire il rendering in un passaggio di profondità della sola che interessa solo il [buffer profondità](https://msdn.microsoft.com/library/windows/desktop/bb219616(v=vs.85).aspx) e non influiscono sulle destinazioni di rendering di colore.
   * Si prepara il buffer di profondità per nasconde i colori vntana successivamente eseguito il rendering dietro superfici spaziale. Accurata relative all'occlusione di vntana migliora il senso che vntana esiste effettivamente all'interno di uno spazio fisico dell'utente.
   * Per abilitare il rendering solo profondità, aggiornare lo stato di blend per impostare il [RenderTargetWriteMask](https://msdn.microsoft.com/library/windows/desktop/hh404492(v=vs.85).aspx) su zero per il colore di tutte le destinazioni di rendering.
* Per la modifica dell'aspetto del vntana bloccati per superfici del mondo reale
   * In genere viene eseguito il rendering della geometria è nascosta quando si viene bloccato. Questo risultato viene ottenuto impostando la funzione di profondità nel [stato stencil profondità](https://msdn.microsoft.com/library/windows/desktop/ff476110(v=vs.85).aspx) a "minore di o uguale", in modo che la geometria siano visibili solo in cui è **più da vicino** alla fotocamera rispetto a tutti precedentemente eseguito il rendering geometria.
   * Tuttavia, può essere utile per mantenere determinati geometry visibile anche quando si viene bloccato e per modificarne l'aspetto quando bloccati allo scopo di fornire un feedback visivo all'utente. Ad esempio, in questo modo l'applicazione mostrare la posizione di un oggetto mentre chiaramente che l'utente è protetto da un'area del mondo reale.
   * A tale scopo, eseguire il rendering della geometria una seconda volta con un diverso dello shader che crea l'aspetto desiderato 'occluded'. Prima di eseguire il rendering della geometria per la seconda volta, apportare due modifiche per il [stato stencil profondità](https://msdn.microsoft.com/library/windows/desktop/ff476110(v=vs.85).aspx). Innanzitutto, impostare la funzione di profondità "maggiore o uguale a" in modo che la geometria saranno visibili solo in cui è **ulteriormente** dalla fotocamera rispetto a tutte le geometrie precedentemente sottoposti a rendering. In secondo luogo, impostare il DepthWriteMask a zero, in modo che il buffer di profondità non verrà modificato (il buffer di profondità continueranno a rappresentare la profondità della geometria **più vicina** alla fotocamera).

[Prestazioni](understanding-performance-for-mixed-reality.md) costituiscono un aspetto importante per il rendering mesh del mapping spaziale. Ecco alcune tecniche di prestazioni di rendering specifiche di rendering mesh del mapping spaziale:
* Regolare la densità triangolo
   * Quando si richiedente superficie spaziale trame dall'osservatore surface, richiedere la densità più bassa di triangolari che è sufficiente per le proprie esigenze.
   * Si può avere senso per variare la densità triangolo in base all'area per area, in base alla distanza della superficie da parte dell'utente e alla sua importanza per l'esperienza dell'utente.
   * Riducendo i conteggi di triangolo ridurrà utilizzo della memoria e i costi di elaborazione del vertice sulla GPU, anche se non verranno influenzati, i costi di elaborazione dei pixel.
* Eseguire il culling cono
   * Eliminazione selettiva di cono Ignora oggetti disegno che non sono visibili perché si trovano all'esterno del cono di visualizzazione corrente. In questo modo si riduce i costi di elaborazione di CPU e GPU.
   * Poiché il culling viene eseguito in base al mesh e superfici spaziali possono avere dimensioni elevate, suddividere ogni trama della superficie spaziale in blocchi più piccoli può comportare più efficiente della faccia posteriore (in quanto il rendering vengono eseguiti un numero inferiore di triangoli fuori schermo). C'è un compromesso tuttavia; i più trame che è necessario, altre chiamate di disegno è necessario apportare, che possono aumentare i costi della CPU. In un caso estremo, di cono della faccia posteriore calcoli stessi anche avere una notevole costo della CPU.
* Modificare l'ordine di rendering
   * Le superfici spaziali tendono a essere di grandi dimensioni, in quanto rappresentano l'intero ambiente dell'utente che li racchiudono. Pixel elaborazione i costi nella GPU in questo modo può essere alto, in particolare nei casi in cui è presente più di un livello di geometria visibile (incluso superfici spaziali e altri vntana). In questo caso, il livello più vicino all'utente verrà essere occluding ulteriormente i livelli, in modo che qualsiasi momento GPU impiegato per il rendering di tali livelli più distante risulta sprecata.
   * Per ridurre il lavoro ridondante nella GPU, consente di eseguire il rendering di superfici opache in ordine da primo a ultimo (quelli più da vicino in primo luogo, più distante quelli last). Per "opaco" si intendono per il quale il DepthWriteMask è impostato su uno in superfici il [stato stencil profondità](https://msdn.microsoft.com/library/windows/desktop/ff476110(v=vs.85).aspx). Quando viene eseguito il rendering le superfici più vicina, essi verranno preparare il buffer di profondità in modo che più distante superfici vengono ignorate in modo efficiente dall'elaboratore di pixel nella GPU.

## <a name="mesh-processing"></a>Elaborazione di rete

Un'applicazione può essere necessario eseguire [varie operazioni](spatial-mapping.md#mesh-processing) nel mesh superficie spaziale in base alle proprie esigenze. I dati di indici e vertici forniti con ogni trama della superficie spaziale usano lo stesso layout familiari come la [buffer vertici e indici](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) che vengono utilizzati per il rendering mesh in tutti i rendering moderne API. Tuttavia, un aspetto chiave da tenere presente è che triangoli mapping spaziale abbiano una **front-in senso orario ordine dei vertici**. Ogni triangolo è rappresentata da tre indici di vertici nel buffer di indice della mesh e tali indici identificherà i vertici del triangolo in un **in senso orario** ordine, quando viene visualizzato il triangolo dalle **front** lato. Inizio lato (o esterna) delle maglie superficie spaziale corrispondente come previsto al lato anteriore (visibile) delle superfici reali.

Le applicazioni devono solo eseguire mesh semplificazione se la densità triangolo minimo fornita dall'osservatore surface è ancora sufficientemente generico, questo lavoro è un'operazione costoso e già in corso dal runtime per generare i vari forniti livelli di dettaglio.

Poiché ogni osservatore area può fornire più superfici spaziale non connesse, alcune applicazioni può essere utile ritagliare questi spaziali nell'area trame su ogni altra, quindi chiusura lampo li insieme. In generale, è necessario, come nelle vicinanze mesh superficie spaziale spesso si sovrappongono leggermente il passaggio di ritaglio.

## <a name="raycasting-and-collision"></a>Raycasting e dei conflitti

Affinché una fisica API (ad esempio [Havok](http://www.havok.com/)) per fornire un'applicazione con funzionalità raycasting e dei conflitti per superfici spaziale, l'applicazione deve fornire superficie spaziale trame per le API di fisica. Mesh usata spesso per fisica hanno le proprietà seguenti:
* Contengono solo un numero limitato di triangoli. Operazioni di fisica sono molto più complesse rispetto alle operazioni di rendering.
* Sono 'd'acqua-severi'. Superfici deve essere solido non devono contenere piccole aree vuote; anche i buchi troppo piccoli per essere visibile possono causare problemi.
* Vengono convertite in saraceno convesso. Saraceno convesso è pochi i poligoni e è liberi di difetti e sono calcolo molto più efficienti per l'elaborazione di trame grezza.

Quando raycasts verrà eseguito su superfici spaziali, tenere presente che queste superfici spesso sono complesse, risulti troppo affollate forme complete dei dettagli disordinati little - soli come il personale tecnico. Ciò significa che un singolo raycast spesso non è sufficiente per fornire informazioni sufficienti per valutare la forma della superficie, nonché la forma dello spazio vuoto accanto al telefono. È pertanto in genere una buona idea per eseguire molti raycasts all'interno di una piccola area e per usare i risultati aggregati per derivare una comprensione più affidabile della superficie. Ad esempio, usando la media di 10 raycasts a Guida ologrammi posizionamento su una superficie genererà un risultato di gran lunga più fluido e meno instabilità che utilizzando solo un singolo raycast.

Tuttavia, tenere presente che ogni raycast può avere un costo di calcolo elevato. Pertanto a seconda dello scenario di utilizzo è necessario compromesso tra il costo di calcolo di raycasts aggiuntive (operazione eseguita per ogni fotogramma) rispetto al costo di calcolo [mesh elaborazione](spatial-mapping.md#mesh-processing) smooth e rimuovere aree libere in superfici spaziale ( eseguito quando vengono aggiornate le reti mesh spaziale).

## <a name="troubleshooting"></a>Risoluzione dei problemi
* Affinché il mesh superficie sia corretto orientamento, ogni GameObject deve essere attivo prima che venga inviato al SurfaceObeserver affinché il mesh costruito. In caso contrario, le trame verranno visualizzato nello spazio di ma ruotata angolazioni strano.
* Gli elementi GameObject che esegue lo script che comunica con il SurfaceObserver deve essere impostato per l'origine. In caso contrario, tutti i Gameobject creata e inviare il SurfaceObserver a disporre le trame costruiti avrà un offset uguale all'offset dell'oggetto gioco padre. Ciò può rendere il mesh visualizzati diversi metri che rende molto difficile eseguire il debug di cosa sta succedendo.

## <a name="see-also"></a>Vedere anche
* [Sistemi di coordinate](coordinate-systems.md)
* [Mapping spaziale DirectX](spatial-mapping-in-directx.md)
* [Mapping spaziale in Unity](spatial-mapping-in-unity.md)
* [Progettazione di mapping spaziale](spatial-mapping-design.md)
* [Case study: ricerca sui difetti nella realtà](case-study-looking-through-holes-in-your-reality.md)

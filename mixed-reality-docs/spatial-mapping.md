---
title: Mapping spaziale
description: Il mapping spaziale fornisce una rappresentazione dettagliata delle superfici reali nell'ambiente intorno alla HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: mapping spaziale, HoloLens, realtà mista, ricostruzione di superficie, mesh, SR
ms.openlocfilehash: 4914cf5b7864ecb2430a39af73729eb6dfc0e2bd
ms.sourcegitcommit: c4c293971bb3205a82121bbfb40d1ac52b5cb38e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/10/2019
ms.locfileid: "68937066"
---
# <a name="spatial-mapping"></a>Mapping spaziale

Il mapping spaziale fornisce una rappresentazione dettagliata delle superfici reali nell'ambiente intorno alla HoloLens, consentendo agli sviluppatori di creare un'esperienza di realtà mista convincente. Unendo il mondo reale con il mondo virtuale, un'applicazione può sembrare reale. Le applicazioni possono anche essere allineate in modo più naturale con le aspettative degli utenti fornendo comportamenti e interazioni reali.

<br>

>[!VIDEO https://www.youtube.com/embed/zff2aQ1RaVo]

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Funzionalità</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (prima generazione)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td> Mapping spaziale</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>



## <a name="conceptual-overview"></a>Panoramica concettuale

![Superficie mesh che copre una stanza](images/SurfaceReconstruction.jpg)<br>
*Esempio di mesh di mapping spaziale che copre una stanza*

I due tipi di oggetti primari usati per il mapping spaziale sono "osservatore della superficie spaziale" e "superficie spaziale".

L'applicazione fornisce l'osservatore della superficie spaziale con uno o più volumi di delimitazione, per definire le aree di spazio in cui l'applicazione desidera ricevere i dati di mapping spaziali. Per ognuno di questi volumi, il mapping spaziale fornirà all'applicazione un set di superfici spaziali.

Questi volumi possono essere stazionari (in una posizione fissa rispetto al mondo reale) oppure possono essere collegati a HoloLens (si spostano, ma non ruotano, con il HoloLens mentre si spostano nell'ambiente). Ogni superficie spaziale descrive le superfici reali in un piccolo volume di spazio, rappresentate come una mesh triangolare collegata a un [sistema di coordinate spaziali](coordinate-systems.md)con blocco globale.

Quando HoloLens raccoglie nuovi dati sull'ambiente e, quando si verificano modifiche all'ambiente, le superfici spaziali vengono visualizzate, scompaiono e cambiano.

## <a name="common-usage-scenarios"></a>Scenari di utilizzo comuni

![Illustrazioni degli scenari comuni di utilizzo del mapping spaziale: Posizionamento, occlusione, fisica e navigazione](images/sm-concepts-1000px.png)

### <a name="placement"></a>Posizionamento

Il mapping spaziale offre alle applicazioni l'opportunità di presentare forme di interazione naturale e familiare con l'utente; che cosa potrebbe essere più naturale rispetto all'inserimento del telefono sulla scrivania?

Vincolando la posizione degli ologrammi (o più in generale, qualsiasi selezione di posizioni spaziali) a cui poggiano le superfici, viene fornito un mapping naturale da 3D (punto nello spazio) a 2D (punto sulla superficie). In questo modo si riduce la quantità di informazioni che l'utente deve fornire all'applicazione, rendendo le interazioni dell'utente più veloci, semplici e precise. Questa situazione è particolarmente vera perché "distance away" non è un elemento che viene usato per la comunicazione fisica con altri utenti o computer. Quando si fa riferimento al dito, viene specificata una direzione, ma non una distanza.

Un avvertimento importante è che, quando un'applicazione deduce la distanza dalla direzione (ad esempio eseguendo un Raycast lungo la direzione dello sguardo dell'utente per trovare la superficie spaziale più vicina), questo deve produrre risultati che l'utente è in grado di stimare in modo affidabile. In caso contrario, l'utente perderà il proprio senso di controllo e questa operazione può diventare rapidamente frustrante. Un metodo che consente di eseguire questa operazione consiste nell'eseguire più raycasts anziché uno solo. I risultati di aggregazione devono essere più uniformi e prevedibili, meno suscettibili a influenzare da risultati temporanei "outlier" (come può essere causato da raggi che passano attraverso piccoli buchi o colpendo piccoli bit di geometria che l'utente non è in grado di riconoscere). L'aggregazione o l'uniformità può essere eseguita anche nel tempo; ad esempio, è possibile limitare la velocità massima a cui un ologramma può variare a distanza dall'utente. È anche possibile limitare la limitazione del valore minimo e massimo della distanza, in modo che l'ologramma spostato non entri improvvisamente nella distanza o venga arrestato di nuovo nel volto dell'utente.

Le applicazioni possono anche usare la forma e la direzione delle superfici per guidare la posizione degli ologrammi. Una poltrona olografica non dovrebbe penetrare tra le pareti e deve essere scaricata con il pavimento anche se è leggermente non uniforme. Questo tipo di funzionalità si basa probabilmente sull'uso di collisioni di fisica piuttosto che su raycasts, tuttavia si verificheranno problemi simili. Se l'ologramma posizionato presenta molti poligoni di piccole dimensioni, ad esempio le gambe su una poltrona, potrebbe essere utile espandere la rappresentazione fisica di tali poligoni in un elemento più ampio e più semplice, in modo da poter scorrere le superfici spaziali senza sbavatura.

A livello estremo, l'input dell'utente può essere completamente semplificato ed è possibile usare le superfici spaziali per eseguire la selezione automatica degli ologrammi. Ad esempio, l'applicazione potrebbe posizionare un interruttore di luce olografico in un punto qualsiasi sul muro per fare in modo che l'utente prema. La stessa avvertenza sulla prevedibilità si applica doppiamente. Se l'utente si aspetta di controllare la posizione degli ologrammi, ma l'applicazione non sempre posiziona gli ologrammi in cui si aspettano (se il Commuter viene visualizzato in un punto in cui l'utente non è in grado di raggiungere), si tratta di un'esperienza frustrante. In realtà, può essere peggiore eseguire la selezione host automatica che richiede la correzione dell'utente in parte del tempo, anziché richiedere che l'utente esegua sempre la selezione host. Poiché è *previsto*un posizionamento automatico corretto, la correzione manuale sembra un carico.

Si noti inoltre che la capacità di un'applicazione di utilizzare le superfici spaziali per la selezione host dipende molto dall' [esperienza di analisi](spatial-mapping-design.md#the-environment-scanning-experience)dell'applicazione. Se una superficie non è stata analizzata, non può essere usata per la selezione host. L'applicazione è in grado di rendere questa operazione chiara all'utente, in modo da consentire l'analisi di nuove superfici o la selezione di una nuova posizione.

Il feedback visivo all'utente è di importanza fondamentale durante la selezione host. L'utente deve essere in grado di individuare il punto in cui l'ologramma è correlato alla superficie più vicina con [effetti di base](spatial-mapping.md#visualization). Devono comprendere perché lo spostamento dell'ologramma è vincolato, ad esempio a causa di un conflitto con un'altra superficie vicina. Se non è possibile inserire un ologramma nella posizione corrente, il feedback visivo dovrebbe renderlo chiaro perché non. Ad esempio, se l'utente sta tentando di collocare un divano olografico a metà strada nella parete, le parti del divano che si trovano dietro la parete dovrebbero pulsare in un colore arrabbiato. Viceversa, se l'applicazione non è in grado di trovare una superficie spaziale in una posizione in cui l'utente può visualizzare una superficie reale, l'applicazione dovrebbe renderla chiaro. L'assenza ovvia di un effetto di base in quest'area può raggiungere questo scopo.

### <a name="occlusion"></a>Occlusione

Uno degli usi principali delle superfici di mapping spaziale è semplicemente occludere gli ologrammi. Questo semplice comportamento ha un notevole effetto sul realismo percepito degli ologrammi, contribuendo a creare un senso viscerale che occupa effettivamente lo stesso spazio fisico dell'utente.

L'occlusione fornisce inoltre informazioni all'utente. Quando un ologramma sembra essere nascosto da una superficie reale, questo fornisce commenti visivi aggiuntivi relativi alla posizione spaziale di tale ologramma nel mondo. Viceversa, l'occlusione può anche *nascondere* le informazioni dall'utente. gli ologrammi occlusione dietro le pareti possono ridurre il disordine visivo in modo intuitivo. Per nascondere o rivelare un ologramma, l'utente deve semplicemente spostare l'intestazione.

L'occlusione può essere usata anche per le prime aspettative per un'interfaccia utente naturale basata su interazioni fisiche note. Se un ologramma è nascosto da una superficie, è perché la superficie è solida, quindi l'utente deve aspettarsi che l'ologramma entri in *conflitto* con tale superficie e non semplicemente passarla.

In alcuni casi, l'occlusione degli ologrammi è indesiderata. Se un utente deve essere in grado di interagire con un ologramma, deve essere in grado di visualizzarlo anche se è dietro una superficie reale. In questi casi, in genere è opportuno eseguire il rendering di un ologramma in modo diverso quando è nascosto (ad esempio, riducendo la luminosità). In questo modo, l'utente potrà individuare visivamente l'ologramma, ma sarà comunque consapevole che è dietro qualcosa.

### <a name="physics"></a>Fisica

L'uso della simulazione fisica è un altro modo in cui il mapping spaziale può essere usato per rafforzare la *presenza* di ologrammi nello spazio fisico dell'utente. Quando la palla di gomma olografica si sposta in modo realistico dalla mia scrivania, rimbalza sul pavimento e scompare sotto il divano, potrebbe essere difficile credere che non sia in realtà.

La simulazione fisica offre inoltre la possibilità per un'applicazione di usare interazioni naturali e familiari basate sulla fisica. Lo spostamento di un pezzo di mobili olografici intorno al pavimento sarà probabilmente più semplice per l'utente se il mobile risponde come se fosse scorrevole in tutto il pavimento con l'inerzia e l'attrito appropriati.

Per generare comportamenti fisici realistici, è probabile che sia necessario eseguire alcune operazioni di [elaborazione di mesh](spatial-mapping.md#mesh-processing) , ad esempio la compilazione di buchi, la rimozione di allucinazioni mobili e l'arrotondamento di superfici ruvide.

Sarà inoltre necessario considerare il modo in cui l' [esperienza di analisi](spatial-mapping-design.md#the-environment-scanning-experience) dell'applicazione influisce sulla simulazione fisica. In primo luogo, le superfici mancanti non si scontrano con niente. cosa accade quando la palla di gomma si sposta verso il basso nel corridoio e al termine del mondo noto? In secondo luogo, è necessario decidere se si continuerà a rispondere alle modifiche nell'ambiente nel tempo. In alcuni casi, è opportuno rispondere il più rapidamente possibile; Supponiamo che l'utente usi porte e mobili come barriere mobili in difesa contro una tempesta di frecce romane in arrivo. In altri casi, tuttavia, potrebbe essere necessario ignorare i nuovi aggiornamenti; guidare le auto sportive olografiche in tutto il circuito può non essere così divertente se il cane decide di sedersi al centro della traccia.

### <a name="navigation"></a>Navigazione

Le applicazioni possono utilizzare i dati di mapping spaziale per concedere ai caratteri olografici (o agenti) la possibilità di esplorare il mondo reale nello stesso modo in cui una persona reale. Questo può contribuire a rafforzare la presenza di caratteri olografici limitando gli stessi allo stesso set di comportamenti naturali e noti di quelli dell'utente e dei relativi amici.

Le funzionalità di navigazione possono essere utili anche per gli utenti. Una volta che una mappa di navigazione è stata compilata in un'area specifica, potrebbe essere condivisa per fornire indicazioni olografiche per i nuovi utenti che non hanno familiarità con tale località. Questa mappa può essere progettata per semplificare il flusso del traffico pedonale o per evitare incidenti in posizioni pericolose come i siti di costruzione.

Le principali problemi tecnici che interessano l'implementazione della funzionalità di navigazione sono il rilevamento affidabile di superfici a scorrimento (gli utenti non sono in grado di esplorare le tabelle) e l'adattamento normale alle modifiche nell'ambiente (gli utenti non passano attraverso le porte chiuse). È possibile che la mesh richieda una certa [elaborazione](spatial-mapping.md#mesh-processing) prima che sia utilizzabile per la pianificazione e la navigazione dei percorsi da parte di un carattere virtuale. La smussatura della rete e la rimozione delle allucinazioni possono aiutare a evitare che i caratteri rimangano bloccati. È anche possibile semplificare notevolmente la mesh per velocizzare i calcoli di spostamento e pianificazione dei percorsi dei caratteri. Questi problemi hanno ricevuto una grande attenzione nello sviluppo della tecnologia per i videogiochi ed è disponibile una vasta gamma di documenti di ricerca su questi argomenti.

Si noti che la funzionalità NavMesh incorporata in Unity non può essere usata con superfici di mapping spaziale. Ciò è dovuto al fatto che le superfici del mapping spaziale sono note solo dopo l'avvio dell'applicazione, mentre i file di dati NavMesh devono essere generati in anticipo dalle risorse di origine. Si noti inoltre che il sistema di mapping spaziale non fornirà [informazioni sulle superfici molto lontani](spatial-mapping-design.md#the-environment-scanning-experience) dalla posizione corrente dell'utente. Quindi, l'applicazione deve ricordare che si tratta di una superficie se è necessario creare una mappa di un'area molto grande.

### <a name="visualization"></a>Visualizzazione

Nella maggior parte dei casi è opportuno che le superfici spaziali siano invisibili; per ridurre al minimo il disordine visivo e lasciare che il mondo reale parli per se stesso. Tuttavia, a volte è utile visualizzare direttamente le superfici del mapping spaziale, nonostante il fatto che le loro controparti reali siano già visibili.

Ad esempio, quando l'utente tenta di posizionare un ologramma su una superficie (posizionando un cabinet olografico sulla parete), può essere utile per "macinare" l'ologramma proiettando un'ombreggiatura sulla superficie. Ciò offre all'utente un senso molto più chiaro della vicinanza fisica esatta tra l'ologramma e la superficie. Questo è anche un esempio della pratica più generale di "anteprima" visiva di una modifica prima che l'utente ne venga eseguito il commit.

Visualizzando le superfici, l'applicazione può condividere con l'utente la conoscenza dell'ambiente. Ad esempio, un gioco della lavagna olografica potrebbe visualizzare le superfici orizzontali identificate come ' Tables ', in modo che l'utente sappia dove devono interagire.

La visualizzazione delle superfici può essere un modo utile per visualizzare gli spazi adiacenti dell'utente nascosti dalla visualizzazione. Questo potrebbe fornire un modo semplice per concedere all'utente l'accesso alla propria cucina (e a tutti gli ologrammi contenuti) dalla loro sala da vivere.

Le mesh di superficie fornite dal mapping spaziale potrebbero non essere particolarmente "pulite". È quindi importante visualizzarli in modo appropriato. I calcoli di illuminazione tradizionali possono evidenziare gli errori nelle normalità della superficie in modo visivo, mentre le trame "pulite" proiettate sulla superficie possono contribuire a fornire un aspetto ordinato. È anche possibile eseguire l' [elaborazione della rete](spatial-mapping.md#mesh-processing) per migliorare le proprietà della mesh, prima che venga eseguito il rendering delle superfici.

## <a name="using-the-surface-observer"></a>Uso di Surface Observer

Il punto di partenza per il mapping spaziale è l'osservatore della superficie. Il flusso di programma è il seguente:
* Creare un oggetto Observer di superficie
   * Fornire uno o più volumi spaziali, per definire le aree di interesse in cui l'applicazione desidera ricevere i dati di mapping spaziali. Un volume spaziale è semplicemente una forma che definisce un'area di spazio, ad esempio una sfera o una casella.
   * Usare un volume spaziale con un sistema di coordinate spaziali con blocco globale per identificare un'area fissa del mondo fisico.
   * Usare un volume spaziale, aggiornare ogni frame con un sistema di coordinate spaziali con blocco del corpo per identificare un'area di spazio che si sposta (ma non ruota) con l'utente.
   * Questi volumi spaziali possono essere modificati in un secondo momento, in caso di modifica dello stato dell'applicazione o dell'utente.
* Usare il polling o la notifica per recuperare informazioni sulle superfici spaziali
   * È possibile eseguire il polling dell'osservatore della superficie per lo stato della superficie spaziale in qualsiasi momento. In alternativa, è possibile registrarsi per l'evento "Surfaces changed" dell'osservatore di superficie che invierà una notifica all'applicazione quando vengono modificate le superfici spaziali.
   * Per un volume spaziale dinamico, ad esempio la vista tronco o un volume con blocco del corpo, le applicazioni dovranno eseguire il polling delle modifiche per ogni frame impostando l'area di interesse e quindi ottenendo il set corrente di superfici spaziali.
   * Per un volume statico, ad esempio un cubo con blocco globale che copre un'unica stanza, è possibile che le applicazioni si registrino per l'evento "Surfaces changed" per ricevere una notifica in caso di modifica delle superfici spaziali all'interno di tale volume.
* Modifiche alle superfici del processo
   * Scorre il set di superfici spaziali fornito.
   * Classificare le superfici spaziali come aggiunte, modificate o rimosse.
   * Per ogni superficie spaziale aggiunta o modificata, se appropriato, inviare una richiesta asincrona per ricevere una mesh aggiornata che rappresenta lo stato corrente della superficie al livello di dettaglio desiderato.
* Elaborare la richiesta di mesh asincrona (altri dettagli nelle sezioni seguenti).

## <a name="mesh-caching"></a>Caching mesh

Le superfici spaziali sono rappresentate da mesh a triangolo denso. L'archiviazione, il rendering e l'elaborazione di tali mesh possono utilizzare risorse di calcolo e di archiviazione significative. Di conseguenza, ogni applicazione deve adottare uno schema di Caching mesh appropriato per le proprie esigenze, allo scopo di ridurre al minimo le risorse usate per l'elaborazione e l'archiviazione di mesh. Questo schema deve determinare quali mesh mantenere e quali annullare, nonché quando aggiornare la mesh per ogni superficie spaziale.

Molte delle considerazioni illustrate in questo articolo indicheranno direttamente il modo in cui l'applicazione deve affrontare la memorizzazione nella cache. È necessario considerare il modo in cui l'utente si sposta nell'ambiente, quali sono le superfici necessarie, quando verranno osservate diverse superfici e quando le modifiche nell'ambiente devono essere acquisite.

Quando si interpreta l'evento "Surfaces changed" fornito da Surface Observer, la logica di base di caching della mesh è la seguente:
* Se l'applicazione rileva un ID di superficie spaziale che non è stato rilevato in precedenza, deve considerarlo come una nuova superficie spaziale.
* Se l'applicazione rileva una superficie spaziale con un ID noto ma con una nuova ora di aggiornamento, deve considerarla come una superficie spaziale aggiornata.
* Se l'applicazione non vede più una superficie spaziale con un ID noto, deve considerarla come una superficie spaziale rimossa.

Ogni applicazione deve quindi effettuare le seguenti scelte:
* Per le nuove superfici spaziali, è necessario richiedere la rete?
   * Generalmente la rete deve essere richiesta immediatamente per le nuove superfici spaziali, che possono fornire informazioni utili per l'utente.
   * Tuttavia, è necessario assegnare la priorità alle nuove superfici spaziali vicino e davanti all'utente e la loro mesh deve essere prima richiesta.
   * Se la nuova mesh non è necessaria, se ad esempio l'applicazione ha "bloccato" in modo permanente o temporaneo il relativo modello di ambiente, non dovrebbe essere richiesto.
* Per le superfici spaziali aggiornate, è necessario richiedere la rete?
   * È necessario assegnare la priorità a una superficie spaziale aggiornata vicina e davanti all'utente e la loro mesh deve essere richiesta per prima.
   * Potrebbe anche essere opportuno assegnare una priorità più alta alle nuove superfici rispetto alle superfici aggiornate, soprattutto durante l'esperienza di analisi.
   * Per limitare i costi di elaborazione, le applicazioni possono limitare la velocità con cui elaborano gli aggiornamenti delle superfici spaziali.
   * Potrebbe essere possibile dedurre che le modifiche apportate a una superficie spaziale sono minori, ad esempio se i limiti della superficie sono ridotti, nel qual caso l'aggiornamento potrebbe non essere sufficientemente importante da elaborare.
   * Gli aggiornamenti alle superfici spaziali al di fuori dell'area di interesse dell'utente possono essere ignorati completamente, anche se in questo caso potrebbe essere più efficiente modificare i volumi di delimitazione spaziali in uso da parte dell'osservatore della superficie.
* Per le superfici spaziali rimosse, il mesh dovrebbe essere scartato?
   * In genere, la mesh deve essere scartata immediatamente per le superfici spaziali rimosse, in modo che l'occlusione ologramma rimanga corretta.
   * Tuttavia, se l'applicazione ha motivo di ritenere che una superficie spaziale verrà visualizzata di nuovo a breve (forse in base alla progettazione dell'esperienza utente), potrebbe essere più efficiente conservarla rispetto a rimuovere la mesh e ricrearla in un secondo momento.
   * Se l'applicazione sta creando un modello su larga scala dell'ambiente dell'utente, potrebbe non voler eliminare alcuna mesh. Sarà comunque necessario limitare l'utilizzo delle risorse, probabilmente mediante lo spooling di mesh su disco quando le superfici spaziali scompaiono.
   * Si noti che alcuni eventi relativamente rari durante la generazione di una superficie spaziale possono causare la sostituzione delle superfici spaziali con nuove superfici spaziali in un percorso simile ma con ID diversi. Di conseguenza, le applicazioni che scelgono di non rimuovere una superficie rimossa dovrebbero prestare attenzione a non finire con più mesh di superficie spaziale altamente sovrapposte che coprono la stessa posizione.
* Il mesh deve essere scartato per qualsiasi altra superficie spaziale?
   * Anche quando esiste una superficie spaziale, se non è più utile per l'esperienza dell'utente, è consigliabile rimuoverla. Se, ad esempio, l'applicazione sostituisce la stanza sull'altro lato di una porta con uno spazio virtuale alternativo, le superfici spaziali di tale spazio non sono più importanti.

Di seguito è riportato un esempio di strategia di Caching mesh, che usa l'isteresi spaziale e temporale:
* Si consideri un'applicazione che vuole usare un volume spaziale a forma di tronco di interesse che segue lo sguardo dell'utente nel modo in cui si aggirano.
* Una superficie spaziale può scomparire temporaneamente da questo volume semplicemente perché l'utente non è più in grado di uscire dalla superficie o da altri passaggi... solo per riprenderlo o ripeterlo più a breve. In questo caso, l'eliminazione e la ricreazione della mesh per questa superficie rappresentano una grande quantità di elaborazione ridondante.
* Per ridurre il numero di modifiche elaborate, l'applicazione utilizza due osservatori di superficie spaziale, uno contenuto all'interno dell'altro. Il volume maggiore è sferico e segue l'utente "pigramente"; si sposta solo quando necessario per garantire che il suo centro sia entro 2,0 metri dall'utente.
* Le mesh di superficie spaziale nuove e aggiornate vengono sempre elaborate dall'osservatore della superficie interna più piccolo, ma le mesh vengono memorizzate nella cache fino a quando non vengono eliminate dal più ampio osservatore della superficie esterna. Ciò consente all'applicazione di evitare l'elaborazione di molte modifiche ridondanti a causa dello spostamento dell'utente locale.
* Poiché anche una superficie spaziale può scomparire temporaneamente a causa di una perdita di rilevamento, l'applicazione rinvia anche le aree spaziali rimosse durante la perdita del rilevamento.
* In generale, un'applicazione deve valutare il compromesso tra l'elaborazione degli aggiornamenti ridotta e un maggiore utilizzo della memoria per determinare la strategia di memorizzazione nella cache ideale.

## <a name="rendering"></a>Rendering

Esistono tre modi principali in cui i mesh di mapping spaziale tendono a essere usati per il rendering:
* Per la visualizzazione della superficie
   * Spesso è utile visualizzare direttamente le superfici spaziali. Ad esempio, il cast di ' Shadows ' da oggetti su superfici spaziali può fornire un utile feedback visivo all'utente mentre sta inserendo ologrammi sulle superfici.
   * Un aspetto da tenere presente è che le mesh spaziali sono diverse dal tipo di mesh che può essere creato da un artista 3D. La topologia del triangolo non sarà' clean ' come topologia creata dall'uomo e la mesh soffrirà di [diversi errori](spatial-mapping-design.md#what-influences-spatial-mapping-quality).
   * Per creare una gradevole estetica visiva, è possibile eseguire alcune operazioni di [elaborazione della rete](spatial-mapping.md#mesh-processing), ad esempio per riempire buchi o normali superfici uniformi. È anche possibile usare uno shader per proiettare le trame progettate dall'artista sulla mesh anziché visualizzare direttamente la topologia mesh e le normali.
* Per gli ologrammi occlusione dietro le superfici reali
   * È possibile eseguire il rendering delle superfici spaziali in un passaggio solo Depth, che influisce solo sul [buffer di profondità](https://msdn.microsoft.com/library/windows/desktop/bb219616(v=vs.85).aspx) e non influisce sulle destinazioni di rendering dei colori.
   * In questo modo, viene generato il buffer di profondità per occludere gli ologrammi sottoposti a rendering successivamente dietro le superfici spaziali. Una corretta occlusione degli ologrammi migliora il senso che gli ologrammi sono effettivamente presenti nello spazio fisico dell'utente.
   * Per abilitare il rendering con solo profondità, aggiornare lo stato di Blend per impostare [RenderTargetWriteMask](https://msdn.microsoft.com/library/windows/desktop/hh404492(v=vs.85).aspx) su zero per tutte le destinazioni di rendering dei colori.
* Per modificare l'aspetto degli ologrammi bloccati dalle superfici reali
   * In genere, la geometria sottoposta a rendering è nascosta quando è nascosta. Questa operazione viene eseguita impostando la funzione depth nello [stato depth-stencil](https://msdn.microsoft.com/library/windows/desktop/ff476110(v=vs.85).aspx) su "minore o uguale a", che fa sì che Geometry sia visibile solo quando è **più vicino** alla fotocamera rispetto a tutte le geometrie precedentemente sottoposte a rendering.
   * Tuttavia, può essere utile tenere visibile una determinata geometria anche quando è bloccato e modificarne l'aspetto quando è bloccato come un modo per fornire un feedback visivo all'utente. Questo consente, ad esempio, all'applicazione di mostrare all'utente la posizione di un oggetto e di renderlo chiaro che si trova dietro una superficie reale.
   * Per ottenere questo risultato, eseguire il rendering della geometria una seconda volta con un shader diverso che crea l'aspetto "nascosto" desiderato. Prima di eseguire il rendering della geometria per la seconda volta, apportare due modifiche allo [stato di stencil Depth](https://msdn.microsoft.com/library/windows/desktop/ff476110(v=vs.85).aspx). Per prima cosa, impostare la funzione depth su "maggiore o uguale a" in modo che la geometria sia visibile solo se è **più lontana** dalla fotocamera rispetto a tutte le geometrie precedentemente sottoposte a rendering. In secondo luogo, impostare DepthWriteMask su zero, in modo che il buffer di profondità non venga modificato (il buffer di profondità deve continuare a rappresentare la profondità della geometria **più vicina** alla fotocamera).

Le [prestazioni](understanding-performance-for-mixed-reality.md) sono un aspetto importante quando si esegue il rendering dei mesh di mapping spaziali. Di seguito sono riportate alcune tecniche di rendering specifiche per il rendering delle mesh di mapping spaziale:
* Regola densità triangolo
   * Quando si richiedono mesh di superficie spaziale dall'osservatore della superficie, richiedere la densità minima di mesh triangolari che è sufficiente per le proprie esigenze.
   * Potrebbe avere senso variare la densità del triangolo in base alla superficie, a seconda della distanza della superficie dall'utente e della relativa pertinenza all'esperienza utente.
   * La riduzione dei conteggi di triangolo ridurrà i costi di utilizzo della memoria e di elaborazione dei vertici sulla GPU, anche se non influirà sui costi di elaborazione dei pixel.
* Eseguire l'eliminazione tronco
   * L'eliminazione di tronco ignora gli oggetti Drawing che non possono essere visualizzati perché sono al di fuori dell'tronco di visualizzazione corrente. In questo modo si riducono i costi di elaborazione della CPU e della GPU.
   * Poiché l'abbassamento di livello viene eseguito in base a mesh e le superfici spaziali possono essere di grandi dimensioni, la suddivisione di ogni mesh della superficie spaziale in blocchi più piccoli può comportare un abbattimento più efficiente (in quanto viene eseguito il rendering di un numero inferiore di triangoli Offscreen). Esiste tuttavia un compromesso; maggiore è il numero di mesh disponibili, maggiore è il numero di chiamate da creare, che possono aumentare i costi della CPU. In un caso estremo, i calcoli per l'eliminazione di tronco possono anche avere un costo della CPU misurabile.
* Modificare l'ordine di rendering
   * Le superfici spaziali tendono a essere di grandi dimensioni, perché rappresentano l'intero ambiente dell'utente che la circonda. I costi di elaborazione dei pixel sulla GPU possono quindi essere elevati, soprattutto nei casi in cui è presente più di un livello di geometria visibile, incluse le superfici spaziali e altri ologrammi. In questo caso, il livello più vicino all'utente occlusione i livelli più lontani, quindi qualsiasi tempo GPU dedicato al rendering di questi livelli più distanti viene sprecato.
   * Per ridurre questo lavoro ridondante sulla GPU, è possibile eseguire il rendering di superfici opache in ordine da primo a indietro (più vicine prima, più distanti le ultime). Per "opaque" si intende la superficie per la quale DepthWriteMask è impostato su uno nello [stato depth-stencil](https://msdn.microsoft.com/library/windows/desktop/ff476110(v=vs.85).aspx). Quando viene eseguito il rendering delle superfici più vicine, il buffer di profondità verrà prima di tutto in modo che le superfici più remote vengano ignorate in modo efficiente dal processore pixel sulla GPU.

## <a name="mesh-processing"></a>Elaborazione mesh

Un'applicazione può voler eseguire [varie operazioni](spatial-mapping.md#mesh-processing) sulle mesh della superficie spaziale in base alle proprie esigenze. I dati relativi a indici e vertici forniti con ogni mesh di superficie spaziale utilizzano lo stesso layout familiare dei [vertex buffer e](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) degli indici utilizzati per il rendering di mesh triangolari in tutte le moderne API di rendering. Tuttavia, un fatto fondamentale da tenere presente è che i triangoli di mapping spaziale hanno un **ordine**di avvolgimento in senso antiorario. Ogni triangolo è rappresentato da tre indici di vertice nel buffer di indice della mesh e questi indici identificano i vertici del triangolo in un ordine **orario** , quando il triangolo viene visualizzato dal lato **anteriore** . Il lato anteriore (o esterno) delle mesh della superficie spaziale corrisponde a quello previsto per il lato anteriore (visibile) delle superfici reali.

Le applicazioni devono eseguire la semplificazione della rete solo se la densità del triangolo più grossolana fornita dall'osservatore della superficie è ancora insufficiente. questo lavoro è dispendioso dal punto di vista del calcolo ed è già eseguito dal runtime per generare le varie livelli di dettaglio forniti.

Poiché ogni osservatore di superficie può fornire più aree spaziali non connesse, alcune applicazioni potrebbero voler ritagliare le mesh della superficie spaziale tra loro, quindi riunirle. In generale, il passaggio di ritaglio è necessario, in quanto le mesh della superficie spaziale sono spesso sovrapposte leggermente.

## <a name="raycasting-and-collision"></a>Raycasting e collisione

Affinché un'API fisica, ad esempio [Havok](http://www.havok.com/), fornisca un'applicazione con funzionalità di Raycasting e collisione per le superfici spaziali, l'applicazione deve fornire mesh di superficie spaziale all'API di fisica. Le mesh usate per la fisica hanno spesso le proprietà seguenti:
* Contengono solo un numero ridotto di triangoli. Le operazioni di fisica sono più complesse dal punto di vista delle operazioni di rendering.
* Si tratta di "Water-Tight". Le superfici destinate a essere solide non devono contenere piccoli buchi; anche i buchi troppo piccoli per essere visibili possono causare problemi.
* Vengono convertite in gusci convessi. Le gusci convessi hanno pochi poligoni e sono privi di buchi e sono molto più efficienti dal punto di vista del calcolo rispetto a mesh triangolari grezzi.

Quando si eseguono raycasts in base alle superfici spaziali, tenere presente che queste superfici sono spesso complesse e ingombranti di dettagli, come la propria scrivania. Ciò significa che un singolo Raycast è spesso insufficiente per fornire informazioni sufficienti sulla forma della superficie e sulla forma dello spazio vuoto vicino. È in genere consigliabile eseguire molti raycasts all'interno di una piccola area e usare i risultati di aggregazione per derivare una conoscenza più affidabile della superficie. Ad esempio, l'uso della media di 10 raycasts per guidare la posizione degli ologrammi su una superficie produrrà un risultato molto più semplice e meno "nervosa" che usa solo un singolo raycast.

Tuttavia, tenere presente che ogni Raycast può avere un elevato costo computazionale. Quindi, a seconda dello scenario di utilizzo, è consigliabile ridurre il costo di calcolo di raycasts aggiuntivi (eseguiti ogni frame) rispetto al costo computazionale dell' [elaborazione della rete](spatial-mapping.md#mesh-processing) per smussare e rimuovere i buchi nelle superfici spaziali (eseguite quando lo spazio le mesh sono aggiornate.

## <a name="troubleshooting"></a>Risoluzione dei problemi
* Affinché le mesh della superficie siano orientate correttamente, ogni GameObject deve essere attivo prima di essere inviato al SurfaceObeserver per costruire la mesh. In caso contrario, le maglie vengono visualizzate nello spazio, ma ruotate a angoli strani.
* Il GameObject che esegue lo script che comunica con il SurfaceObserver deve essere impostato sull'origine. In caso contrario, tutte le GameObject create e inviate al SurfaceObserver per la costruzione delle mesh avranno un offset uguale all'offset dell'oggetto del gioco padre. In questo modo, le mesh possono visualizzare diversi metri che rendono molto difficile eseguire il debug di ciò che accade.

## <a name="see-also"></a>Vedere anche
* [Sistemi di coordinate](coordinate-systems.md)
* [Mapping spaziale in DirectX](spatial-mapping-in-directx.md)
* [Mapping spaziale in Unity](spatial-mapping-in-unity.md)
* [Progettazione del mapping spaziale](spatial-mapping-design.md)
* [Comprensione della scena](scene-understanding.md)
* [Case study - Guardare attraverso fori nella realtà](case-study-looking-through-holes-in-your-reality.md)

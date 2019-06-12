---
title: Sistemi di coordinate
description: I sistemi di coordinate spaziali consente di compilare seduti, la condizione, chat room a scalabilità e su scala mondiale mista realtà esperienze.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: sistema di coordinate, sistema di coordinate spaziale, solo l'orientamento, seduti a scalabilità, la condizione di scalabilità, chat room-scalabilità, mondo della scala, viene posizionata a 360 gradi, e la condizione, chat room, world, scalabilità, posizione, orientamento, stazionaria, collegati, fase, ancoraggio, spaziale ancoraggio, bloccato al mondo, blocco a livello mondiale, bloccato corpo, corpo del blocco, limiti, persistenza, condivisione, rilevamento di perdite, cloud ancoraggio spaziale
ms.openlocfilehash: f4b945a3ffb83b9ac0a94e0d793a19939aece3bb
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829866"
---
# <a name="coordinate-systems"></a>Sistemi di coordinate

Loro core sul posto di App di realtà mista [vntana](hologram.md) nel tuo mondo con l'aspetto e far pensare a oggetti reali. Ciò comporta in modo preciso il posizionamento e orientando tali vntana luoghi nel mondo che sono significative per l'utente, se tutto il mondo è loro spazio fisico o un'area di autenticazione virtuale creato. Quando si ha a che fare la posizione e l'orientamento del vntana o qualsiasi altra geometria, ad esempio il [estasiati](gaze.md) ray oppure [mano posizioni](gestures.md), Windows fornisce vari sistemi di coordinate reali in cui può essere espresso Geometry, noto come **spatial coordinate systems**.

<br>

>[!VIDEO https://www.youtube.com/embed/TneGSeqVAXQ]

## <a name="device-support"></a>Supporto di dispositivi

<table>
    <colgroup>
    <col width="40%" />
    <col width="20%" />
    <col width="20%" />
    <col width="20%" />
    </colgroup>
    <tr>
        <td><strong>Funzionalità</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (dal 1 ° generazione)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Auricolari coinvolgenti</strong></a></td>
    </tr>
     <tr>
        <td><a href="coordinate-systems.md#stationary-frame-of-reference">Fotogramma di riferimento fisso</a></td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="coordinate-systems.md#attached-frame-of-reference">Collegati fotogramma di riferimento</a></td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="coordinate-systems.md#stage-frame-of-reference">Fase fotogramma di riferimento</a></td>
        <td>Non ancora supportato</td>
        <td>Non ancora supportato</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="coordinate-systems.md#spatial-anchors">Ancoraggi nello spazio</a></td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="spatial-mapping.md">Mapping spaziale</a></td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="mixed-reality-experience-scales"></a>Scale di esperienza di realtà mista

Per un'ampia gamma di esperienze utente, dai visualizzatori di video a 360 gradi che sufficiente dell'orientamento della cuffia, in completo world-scalabilità per App e giochi, che devono mapping spaziale e spaziali Anchor possono progettare le App per realtà mista:
<br>

| Esperienza di scalabilità | Requisiti | Esperienza di esempio | 
|----------|----------|----------|
|  **Solo l'orientamento** |  **Orientamento visore Vr** (gravità allineata) |  Visualizzatore di video a 360° | 
|  **Seated-scale** |  In precedenza, plus **posizione visore Vr** rispetto alla posizione zero |  Racing game o spazio simulatore | 
|  **Standing-scale** |  In precedenza, plus **fase origin floor** |  Gioco d'azione in cui siete e scherma posto  | 
|  **Room-scale** |  In precedenza, plus **poligono limiti fase** |  Rompicapo gioco in cui è illustrato tutto il puzzle | 
|  **World-scale** |  **Gli ancoraggi spaziali** (e, in genere [mapping spaziale](spatial-mapping.md)) |  Gioco con nemici provenienti da affisse reale, ad esempio [RoboRaid](https://www.microsoft.com/p/roboraid/9nblggh5fv3j) | 

Questi esperienza scale seguire un modello "nidificazione bambole". Il principio di progettazione chiave qui per realtà mista di Windows è che le cuffie specificata supporta le app create per una scala di esperienza di destinazione, nonché scale tutto minore:
<br>

| Rilevamento 6DOF | Floor definito | rilevamento di 360° | Limiti definiti | Ancoraggi spaziali | Esperienza di massima | 
|----------|----------|----------|----------|----------|----------|
|  No |  - |  - |  - |  - |  **Solo l'orientamento** | 
|  **Sì** |  No |  - |  - |  - |  **Inserita** | 
|  **Sì** |  **Sì** |  No |  - |  - |  **Permanente - Avanti** | 
|  **Sì** |  **Sì** |  **Sì** |  No |  - |  **Permanente - 360°** | 
|  **Sì** |  **Sì** |  **Sì** |  **Sì** |  No |  **Chat room** | 
|  **Sì** |  **Sì** |  **Sì** |  **Sì** |  **Sì** |  **World** | 

Si noti che il fotogramma di riferimento di fase non è ancora supportato in HoloLens. Una chat room-ridimensionare un'app in HoloLens attualmente deve utilizzare [mapping spaziale](spatial-mapping.md) per trovare la parte intera e pareti dell'utente.

## <a name="spatial-coordinate-systems"></a>Sistemi di coordinate spaziali

Usano tutte le applicazioni di grafica 3D [sistemi di coordinate cartesiano](https://docs.microsoft.com/windows/uwp/graphics-concepts/coordinate-systems) per prendere in considerazione le posizioni e gli orientamenti di oggetti nei mondi virtuali eseguono il rendering. Questi sistemi di coordinate stabilire 3 assi perpendicolari lungo il quale posizionare gli oggetti: un asse X, Y e Z.

Nelle [realtà mista](mixed-reality.md), le app verranno motivare i sistemi di coordinate fisici e virtuali. Windows chiama un sistema di coordinate che ha un significato reale nel mondo fisico una **sistema di coordinate spaziale**.

Sistemi di coordinate spaziali esprimere i valori delle coordinate in metri. Ciò significa che gli oggetti inseriti 2 unità distanti entrambi x, Y o Z asse verrà visualizzati 2 metri tra loro quando viene eseguito il rendering nella realtà mista. In questo modo si facilmente eseguire il rendering di oggetti e gli ambienti su larga scala reali.

In generale, i sistemi di coordinate cartesiano possono essere da destra o battitori. Sistemi di coordinate spaziali su Windows sono sempre da destra, il che significa che punta a destra il valore positivo di asse x, y positivo punta verso l'alto (allineato a gravità) e il valore positivo punta all'asse z verso di te.

In entrambi i tipi di sistemi di coordinate, il valore positivo dell'asse x punta a destra e l'asse y positivo punta verso l'alto. La differenza è che l'asse z positivo punta verso o lontano da te. È possibile ricordare direzione in cui fa riferimento all'asse z positivo posizionando le dita di una di sinistra o a destra nella direzione e li a usare CURL per la direzione Y positiva abbia valore positivo. La direzione fa riferimento il controllo thumb, verso o lontano da te, è la direzione che faccia riferimento all'asse z positivo per il sistema di coordinate.

## <a name="building-an-orientation-only-or-seated-scale-experience"></a>Creazione di un'esperienza solo orientamento seduto scala o

La chiave a holographic [rendering](rendering.md) sta cambiando vista dell'app del relativo vntana ogni fotogramma perché l'utente si sposta, in modo che corrisponda il movimento head stimato. È possibile compilare **esperienze su scala seduto** che rispettano cambia la posizione dell'utente head e orientamento head usando un **fotogramma di riferimento fisso**.

Parte del contenuto deve essere ignorato head posizione gli aggiornamenti, rimanendo fissa in un'intestazione scelta e distanza da parte dell'utente in qualsiasi momento. L'esempio principale è a 360 gradi video: poiché il video viene acquisito da un'unica prospettiva fissa, potrebbe danneggiare la l'illusione della posizione di visualizzazione spostare rispetto al contenuto, anche se è necessario modificare l'orientamento di visualizzazione quando l'utente cerca. È possibile compilare tale **orientamento sola esperienze** usando un' **collegato fa riferimento a**.

### <a name="stationary-frame-of-reference"></a>Fotogramma di riferimento fisso

Il sistema di coordinate fornito da un fermo fotogramma di riferimento si impegna per mantenere le posizioni degli oggetti vicino all'utente più stabile rispetto al mondo, rispettando le modifiche nella posizione principale dell'utente.

Per scalabilità seduto esperienze, ad esempio in un motore di gioco [Unity](https://unity3d.com/), un fotogramma di riferimento fisso è ciò che definisce "mondo origin" del motore. Gli oggetti che vengono inseriti in una coordinata globale specifico usano il fotogramma di riferimento fisso per definire la posizione del mondo reale con le stesse coordinate. Il contenuto rimane inseriti nel mondo, anche quando l'utente scorre, è noto come **bloccato world** contenuto.

Un'app verrà in genere creare un fotogramma di riferimento fisso all'avvio e utilizzare il sistema di coordinate per tutta la durata dell'app. Lo sviluppatore di applicazioni in Unity, ed è possibile iniziare a inserire il contenuto di origine, che sarà nella posizione head iniziale e l'orientamento dell'utente. Se l'utente si sposta in una nuova posizione e possa continuare a loro esperienza seduto scalabilità, è possibile centrare di nuovo l'origine del mondo in quella posizione.

Nel corso del tempo, come il sistema apprende più sull'ambiente dell'utente, potrebbe determinare che le distanze tra i vari punti del mondo reale sono più brevi o più lungo rispetto al sistema che sarebbero state diffuse in precedenza. Se si esegue il rendering vntana in un frame di riferimento fisso per un'app in HoloLens in cui gli utenti vagare oltre un'area ampia circa 5 metri, l'app potrebbe osservare deviazione nella posizione di tali vntana osservata. Se l'esperienza ha wandering oltre i contatori di 5 utenti, si sta compilando un [esperienza su scala mondiale](#building-a-world-scale-experience), che richiederà l'uso ulteriori informazioni sulle tecniche per mantenere vntana stabili, come descritto di seguito.

### <a name="attached-frame-of-reference"></a>Collegati fotogramma di riferimento

Un frame di riferimento collegati si sposta con l'utente che illustrano in modo, con un'intestazione fissa definita quando l'app crea innanzitutto il frame. Ciò consente all'utente di comodamente Guardatevi intorno al contenuto inserito all'interno di tale fotogramma di riferimento. Viene chiamato il contenuto sottoposto a rendering in questo modo utente relativi **bloccato corpo** contenuto.

Quando le cuffie non possono scoprire dove sono in tutto il mondo, un frame di riferimento collegati fornisce l'unico sistema di coordinate che può essere utilizzato per eseguire il rendering vntana. Questo rende ideale per la visualizzazione di fallback dell'interfaccia utente per informare l'utente che il dispositivo non è possibile trovarli nel mondo. Le app che sono seduti scalabilità o versione successiva devono includere un fallback solo orientamento che consenta all'utente anche in questo caso, procedere con l'interfaccia utente simile a quella mostrata nella [realtà mista home](navigating-the-windows-mixed-reality-home.md).

## <a name="building-a-standing-scale-or-room-scale-experience"></a>Creazione di un'esperienza su scala permanente o gradazioni di chat room

Andare oltre scala sia inserita in un visore VR immersivi e compilare un **esperienza su scala permanente**, è possibile utilizzare il **fase fotogramma di riferimento**.

Per fornire un **esperienza su scala chat room**e ciò consente agli utenti camminare all'interno del limite di 5 misuratore sono predefiniti, è possibile cercare **fase dei limiti** anche.

### <a name="stage-frame-of-reference"></a>Fase fotogramma di riferimento

Quando si configura prima di tutto un visore VR immersivi, l'utente definisce una **fase**, che rappresenta la chat in cui si verificheranno realtà mista. La fase minima definisce una **fase origin**, un sistema di coordinate spaziale centrato all'utente della scelta posizione floor e l'orientamento diretta in cui si prevede di usare il dispositivo. Posizionando il contenuto in questo sistema di coordinate fase nel piano di floor Y = 0, è possibile garantire il vntana visualizzati comodamente sul pavimento quando l'utente è permanente, offrendo agli utenti con un **esperienza su scala permanente**.

### <a name="stage-bounds"></a>Limiti di fase

L'utente può anche facoltativamente definire **fase limiti**, realtà mista di un'area all'interno di spazio che è stata deselezionata di mobili in cui si intende lo spostamento all'interno. Se, pertanto, è possibile compilare l'app una **esperienza su scala chat room**, utilizzando questi limiti per assicurarsi che vntana viene sempre inserite in cui l'utente di raggiungerli.

Poiché la fase cornice di riferimento fornisce che una singola correzione sistema di coordinate in cui collocare il contenuto relativo alla parte intera, è l'approccio più semplice per scalabilità permanente al porting e chat room applicazioni sviluppate per auricolari realtà virtuale. Tuttavia, poiché con tali piattaforme di realtà virtuale, un singolo sistema di coordinate possono solo si stabilizza contenuti in relativi a un diametro del misuratore 5 (16 piedi), prima levetta-arm effetti che contenuto tutt'altro che spostamento decisamente come il sistema consente di regolare il centro. Per andare oltre i contatori di 5, sono necessari gli ancoraggi spaziali.

## <a name="building-a-world-scale-experience"></a>Creazione di un'esperienza su scala mondiale

True consente di HoloLens **esperienze su scala mondiale** che consentono agli utenti di vagare oltre 5 metri. Per compilare un'app su scala mondiale, è necessario nuove tecniche oltre a quelli usati per le esperienze su scala chat room.

### <a name="why-a-single-rigid-coordinate-system-cannot-be-used-beyond-5-meters"></a>Motivi per cui non è possibile utilizzare un singolo sistema di coordinate rigido oltre i contatori di 5

Attualmente, durante la scrittura di giochi, App di visualizzazione dei dati o le app di realtà virtuale, l'approccio tipico è per stabilire un sistema di coordinate complessive assolute che tutte le altre coordinate in modo affidabile possono eseguire il mapping a. In tale ambiente, è possibile trovare una trasformazione stabile che definisce una relazione tra due oggetti in quell'ambito. Se si hanno deciso di passare tali oggetti, le trasformazioni relative rimarranno sempre gli stessi. Questo tipo di globale sistema di coordinate funziona bene quando il rendering di un mondo virtuale esclusivamente in cui si conoscono tutti della geometria in anticipo. Chat room-ridimensionare le app di realtà virtuale stabiliscono oggi in genere questo tipo di sistema di coordinate assoluto chat room-scalabilità con l'origine sul pavimento.

Al contrario, un dispositivo senza i limiti di realtà mista, ad esempio HoloLens ha una conoscenza dinamica basati su sensori del mondo, in modo continuo modificando le informazioni nel corso del tempo dell'ambiente circostante dell'utente che illustrano in modo molti contatori in un intero piano di un edificio. In un'esperienza su scala mondiale, se tutti i vntana è posizionata in un singolo sistema di coordinate rigido, tali vntana sarebbe deviano necessariamente nel corso del tempo rispetto al mondo o tra di loro.

Ad esempio, le cuffie potrebbero attualmente ritiene che due posizioni nel mondo per essere 4 metri e quindi perfezionare in un secondo momento tale conoscenza, apprendimento che i percorsi siano effettivamente 3.9 metri di distanza. Se tali vntana inizialmente è stata impostata metri 4 distanti in un singolo sistema di coordinate rigido, uno di essi sarebbe quindi vengono sempre visualizzati i contatori di 0,1 disattivata dal mondo reale.

### <a name="spatial-anchors"></a>Ancoraggi spaziali

Realtà mista di Windows è stato risolto il problema descritto nella sezione precedente, consentendo di creare [Anchor spaziali](spatial-anchors.md) per contrassegnare punti importanti in tutto il mondo in cui l'utente ha effettuato vntana. Un punto di ancoraggio spaziale rappresenta un punto importante nel mondo che il sistema deve tenere traccia nel corso del tempo.

Quando il dispositivo scopre tutto il mondo, tali ancoraggi spaziali possono regolare la loro posizione rispetto a un altro in base alle esigenze per garantire che ogni ancoraggio in modo preciso in cui è stato posizionato relativo del mondo reale. Inserendo un punto di ancoraggio spaziale in corrispondenza della posizione in cui l'utente posiziona un ologrammi e posizionamento quindi tali ologrammi rispetto al relativo ancoraggio spaziale, è possibile garantire che l'ologrammi mantenga la stabilità ottima, anche quando l'utente si sposta in decine di misuratori.

Questo adattamento continuo di ancoraggi spaziali una rispetto a altra è la differenza principale tra i frame di riferimento fisso e coordinate systems dai punti di ancoraggio spaziale:

* Ologrammi inseriti nella finestra di tutti i frame di riferimento fisso mantengono una relazione rigida tra loro. Tuttavia, utenti di lavorare lunghe distanze, sistema di coordinate del frame che potrebbe variare rispetto al mondo per verificare che appaiano stabile vntana accanto all'utente.

* Ologrammi inseriti nella fase frame di riferimento anche mantengono una relazione rigida tra loro. A differenza del frame fisso, il frame di fase sempre rimane fisso in posizione rispetto alla sua origine fisica definita. Tuttavia, contenuto sottoposto a rendering nel sistema di coordinate della fase oltre al limite di 5 misuratore viene visualizzato solo stabile mentre è attiva e l'utente all'interno di tale limite.

* Inserita utilizzando uno ancoraggio spaziale potrebbero variare rispetto al ologrammi vntana inserito ancoraggio spaziale un'altra. In questo modo Windows migliorare la comprensione della posizione di ogni punto di ancoraggio spaziale, anche se, ad esempio, un ancoraggio deve adattarsi a sinistra e ancoraggio di un'altra deve rettificare a destra.

A differenza di un frame di riferimento fisso, in modo da ottimizzare sempre per la stabilità vicino all'utente, la fase fotogramma di riferimento e spaziali Anchor garantire la stabilità quasi loro origini. In questo modo tali vntana rimangono esattamente nella stessa posizione nel corso del tempo, ma significa anche che vntana sottoposto a rendering troppo lontani dall'origine del proprio sistema di coordinate si verificherà gli effetti sempre più perseguibile levetta-Azure Resource Manager. Infatti, diventano ancora più evidenti piccole modifiche per la posizione e l'orientamento della fase o ancoraggio proporzionale alla distanza da tale ancoraggio. 

Una buona norma consiste nel verificare che tutto che si esegue il rendering basato sul sistema di coordinate dell'ancoraggio spaziali distante è all'interno di circa 3 misuratori di origine. Per un'origine fase nelle vicinanze, il rendering del contenuto distante è OK, come qualsiasi errore posizionali aumento influirà solo piccole vntana che non si sposterà gran parte in vista dell'utente.

### <a name="spatial-anchor-persistence"></a>Persistenza di ancoraggio spaziali

Gli ancoraggi spaziali possono anche consentire all'app di ricordare un percorso importante anche dopo che l'app sospende o il dispositivo è stato arrestato.

È possibile salvare su disco gli ancoraggi spaziali consente di creare l'app e quindi caricarle nuovamente in seguito, rendendo persistenti per l'app **spaziali store ancoraggio**. Durante il salvataggio o caricamento di un ancoraggio, fornire una chiave di stringa che è significativa per l'app, allo scopo di identificare il punto di ancoraggio in un secondo momento. Questa chiave può essere considerato come il nome del file per l'ancoraggio. Se si desidera associare ad altri dati che definiscono, ad esempio un modello 3D che l'utente inserito nel percorso specificato, che salva in un percorso locale dell'app e associarlo con la chiave che si è scelto.

Per rendere persistenti gli ancoraggi nell'archivio, gli utenti possono collocare vntana singoli oppure un'area di lavoro intorno al quale un'app inserirà relativo vntana diversi e quindi trovare tali vntana in un secondo momento in cui si aspettano, in molti utilizzi delle app.

È anche possibile usare <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Anchor spaziali Azure</a> per la persistenza asincrona ologrammi nei dispositivi Android, iOS e HoloLens.  Condividendo un ancoraggio spaziali cloud durevole, più dispositivi possono osservare le stessi ologrammi persistenti nel corso del tempo, anche se questi dispositivi non sono presenti nello stesso momento.

### <a name="spatial-anchor-sharing"></a>La condivisione di ancoraggio spaziale

L'app può anche condividere un punto di ancoraggio spaziale in tempo reale con altri dispositivi, consentendo in tempo reale condiviso esperienze.

Usando <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Anchor spaziali Azure</a>, le app possono condividere un punto di ancoraggio spaziale tra più HoloLens, dispositivi iOS e Android. Facendo in modo che ogni dispositivo di eseguire il rendering di ologramma usando lo stesso ancoraggio spaziale, tutti gli utenti visualizzeranno l'ologrammi vengono visualizzati nello stesso punto nel mondo reale.

## <a name="avoid-head-locked-content"></a>Evitare il blocco head contenuto

È fortemente sconsigliato il rendering del contenuto blocco head, che rimane un punto fisso nella visualizzazione (ad esempio un HUD). In generale, blocco head contenuto non è quella ottimale per gli utenti non assuma l'aspetto di una parte fisica del proprio mondo.

Blocco head contenuto in genere deve essere sostituito con vntana che è collegati all'utente o inseriti in tutto il mondo stesso. Ad esempio, [cursori](cursors.md) deve in genere essere inviati nel mondo, naturalmente la scalabilità in modo da riflettere la posizione e la distanza dell'oggetto posizionato sotto sguardo dell'utente.

## <a name="handling-tracking-errors"></a>Gestione degli errori di rilevamento

In alcuni ambienti, ad esempio scuri corridoi, potrebbe non essere possibile per le cuffie utilizzando rilevamento interno a esterno a se stesso individuare correttamente nel mondo. Questo può causare vntana non visualizzati o vengono visualizzate in posizioni non corretti se vengono gestite in modo non corretto. Illustreremo ora le condizioni in cui ciò accade, l'impatto sull'esperienza utente, e suggerimenti al meglio gestiscono questa situazione.

### <a name="headset-cannot-track-due-to-insufficient-sensor-data"></a>Impossibile tenere traccia delle cuffie a causa di dati dei sensori insufficiente

In alcuni casi, i sensori della cuffia non sono in grado di capire dove le cuffie sono. Questa situazione può verificarsi se la chat è scura, se vengono analizzati i sensori selettore di precisione o le mani, oppure se l'ambiente circostante non è sufficiente la trama.

In questo caso, le cuffie sarà possibile rilevare la posizione con un'accuratezza sufficienti per eseguire il rendering vntana bloccato al mondo. Sarà possibile capire dove un ancoraggio spaziale, fermo cornice o della fase è rispetto al dispositivo, ma è comunque possibile eseguire il rendering bloccato al corpo del contenuto nel frame di riferimento collegati.

L'app deve informare l'utente come ottenere posizionali di rilevamento, il rendering del contenuto fallback bloccato corpo che descrive alcuni suggerimenti, ad esempio individuando i sensori e attivare più luci.

### <a name="headset-tracks-incorrectly-due-to-dynamic-changes-in-the-environment"></a>Visore VR tiene traccia in modo non corretto a causa di modifiche dinamiche dell'ambiente

In alcuni casi, il dispositivo non è possibile tenere traccia in modo corretto se sono disponibili numerose modifiche dinamiche dell'ambiente, ad esempio molte persone walking intorno nella chat room. In questo caso, può sembrare la vntana jump o deviano come il dispositivo tenta di rilevare se stessa nella situazione dinamica attuale. È consigliabile usare il dispositivo in un ambiente meno dinamico se si riscontra questo scenario.

### <a name="headset-tracks-incorrectly-because-the-environment-has-changed-significantly-over-time"></a>Visore VR tiene traccia in modo non corretto perché l'ambiente è stato modificato in modo significativo nel tempo

In alcuni casi, quando si avvia usando le cuffie, possono in un ambiente che ha subito molte modifiche (ad esempio, lo spostamento significativo di mobili, hangings muro e così via), è possibile che alcuni vntana apparire spostate dai percorsi originali. Il vntana precedenti può spostarsi anche quando l'utente sposta intorno a questo nuovo ambito. Infatti, comprensione del sistema dello spazio non sussiste più e prova a modificare il mapping dell'ambiente durante il tentativo di risolvere le differenze tra le funzionalità della chat room. In questo scenario, è consigliabile invitare gli utenti a inserire nuovamente vntana sono aggiunti nel mondo se non vengono visualizzate posizione prevista.

### <a name="headset-tracks-incorrectly-due-to-identical-spaces-in-an-environment"></a>Visore VR tiene traccia in modo non corretto a causa di spazi identici in un ambiente

In alcuni casi, un indirizzo di base o altri spazi possono avere due aree identiche. Ad esempio, due identici sale riunioni, due identici ad angolo aree, due poster identici di grandi dimensioni che coprono il campo di visualizzazione del dispositivo. In questi scenari, il dispositivo potrebbe, a volte creare confuso tra le parti identiche e contrassegnarli come corrispondente nella rappresentazione interna. Ciò potrebbe causare il vntana da alcune aree per visualizzati in altre posizioni. Il dispositivo può iniziare a perdere rilevamento spesso poiché la rappresentazione interna dell'ambiente è stata danneggiata. In questo caso, è consigliabile reimpostare comprensione dell'ambiente del sistema. Si noti che la reimpostazione della mappa comporta la perdita di tutte le posizioni di ancoraggio spaziale. Ciò causerà il cuffie, possono tenere traccia anche nelle aree dell'ambiente univoche. Tuttavia, il problema può verificarsi nuovamente se il dispositivo può creare confusione tra le aree di identiche.

## <a name="see-also"></a>Vedere anche
* [Presentazione di GDC 2017 on spatial coordinate systems e holographic rendering](https://channel9.msdn.com/events/GDC/GDC-2017/GDC2017-008)
* [Sistemi di coordinate in Unity](coordinate-systems-in-unity.md)
* [Sistemi di coordinate in DirectX](coordinate-systems-in-directx.md)
* [Ancoraggi nello spazio](spatial-anchors.md)
* [Esperienze condivise nella realtà mista](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Ancoraggi nello spazio di Azure</a>
* [Case study: ricerca sui difetti nella realtà](case-study-looking-through-holes-in-your-reality.md)

---
title: Comfort
description: Nella visione naturale, il sistema visivo umano si basa su più fonti di informazioni, o "indizi", per interpretare le forme 3D e la posizione relativa degli oggetti.
author: erickjpaul
ms.author: erpau
ms.date: 04/5/2019
ms.topic: article
ms.localizationpriority: high
keywords: Realtà mista, progettazione, comfort, HoloLens 2, HoloLens (prima generazione)
ms.openlocfilehash: 178044ce8c76de75b7cce5e10664ce65d108f0f8
ms.sourcegitcommit: 4d43a8f40e3132605cee9ece9229e67d985db645
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491152"
---
# <a name="comfort"></a>Comfort

Nella visione naturale, il sistema visivo umano si basa su più fonti di informazioni, o "indizi", per interpretare le forme 3D e le posizioni relative degli oggetti. Alcuni indizi si basano su un solo occhio (indizi monoculari), tra cui [prospettiva lineare](https://en.wikipedia.org/wiki/Perspective_(graphical)), [dimensioni note](https://en.wikipedia.org/wiki/Size#Perception_of_size), occlusione, [sfocatura della profondità di campo](https://en.wikipedia.org/wiki/Depth_of_field) e [accomodazione](https://en.wikipedia.org/wiki/Accommodation_(eye)). Altri indizi si basano su entrambi gli occhi (indizi binoculari) e includono la [convergenza](https://en.wikipedia.org/wiki/Vergence) (essenzialmente le rotazioni relative degli occhi necessarie per guardare un oggetto) e la [disparità binoculare](https://en.wikipedia.org/wiki/Stereopsis) (il modello delle differenze tra le proiezioni della scena sul retro dei due occhi). Per garantire il massimo comfort per i caschi con visore, è importante che i progettisti e gli sviluppatori creino e presentino contenuti in modo da simulare il funzionamento di questi segnali nel mondo naturale. Dal punto di vista fisico, è anche importante progettare contenuto che non richieda movimenti faticosi del collo o delle braccia. In questo articolo esamineremo gli aspetti principali da tenere in considerazione per raggiungere questi obiettivi.

## <a name="vergence-accommodation-conflict"></a>Conflitto tra convergenza e accomodazione

Per visualizzare chiaramente un oggetto, gli utenti devono [accomodare](https://en.wikipedia.org/wiki/Accommodation_%28eye%29), ovvero regolare, la messa a fuoco oculare in base alla distanza dell'oggetto. Allo stesso tempo, la rotazione di entrambi gli occhi deve [convergere](https://en.wikipedia.org/wiki/Convergence_(eye)) in base alla distanza dell'oggetto per evitare la visione di immagini doppie. Nella visione naturale, convergenza e accomodazione sono collegate. Quando si guarda qualcosa da vicino, ad esempio una mosca vicino al naso, gli occhi si incrociano e si accomodano in base a un punto vicino. Viceversa, se si guarda qualcosa all'infinito ottico (che corrisponde circa ad almeno 6 metri di distanza nella visione naturale), le linee visive degli occhi diventano parallele e le lenti degli occhi si accomodano all'infinito. 

Nella maggior parte dei caschi con visore, gli occhi degli utenti si accomodano sempre alla distanza focale del visore (per ottenere un'immagine nitida), ma convergono in base alla distanza dell'oggetto di interesse (per ottenere una singola immagine). Quando l'accomodazione e la convergenza avvengono a distanze diverse, il collegamento naturale tra i due segnali viene interrotto e questo può causare fastidio o affaticamento visivo.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/-606oZKLa_s" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### <a name="guidance-for-holographic-devices"></a>Indicazioni per i dispositivi olografici

I display HoloLens sono fissati a una distanza ottica di circa 2 m dall'utente. Pertanto, gli utenti devono sempre accomodare la visione a circa 2 m per mantenere un'immagine chiara nel dispositivo. Gli sviluppatori di app possono guidare la convergenza degli occhi degli utenti posizionando contenuto e ologrammi a varie profondità. Il disagio provocato dal conflitto tra convergenza e accomodazione può essere evitato o ridotto al minimo mantenendo il contenuto su cui gli utenti convergono lo sguardo il più vicino possibile a 2 m. Ad esempio, in una scena con molta profondità, è opportuno posizionare le aree di interesse a una distanza di circa 2 m dall'utente, quando possibile. Se non è possibile mantenere il contenuto a questa distanza, il disagio provocato dal conflitto tra convergenza e accomodazione è significativo quando lo sguardo dell'utente passa da una distanza all'altra. In altre parole, è molto più confortevole guardare un ologramma che rimane fisso a 50 cm di distanza rispetto a un ologramma distante 50 cm che si avvicina e si allontana nel corso del tempo.

![Distanza ottimale per il posizionamento degli ologrammi rispetto allo sguardo dell'utente.](images/distanceguiderendering-950px.png)<br>
*Distanza ottimale per il posizionamento degli ologrammi rispetto allo sguardo dell'utente*

### <a name="best-practices-for-hololens-1st-gen-and-hololens-2"></a>Procedure consigliate per HoloLens (prima generazione) e HoloLens 2

Per il massimo comfort, **la zona ottimale per il posizionamento degli ologrammi è compresa tra 1,25 e 5 m**. In ogni caso, i progettisti devono cercare di strutturare le scene di contenuto per incoraggiare gli utenti a interagire ad almeno 1 m dal contenuto, ad esempio regolando i [parametri relativi alle dimensioni del contenuto e al posizionamento predefinito](gaze-and-commit.md). 

Anche se talvolta il contenuto deve essere visualizzato a una distanza inferiore a 1 m, è opportuno evitare di presentare ologrammi a meno di 40 cm di distanza. Consigliamo quindi di **applicare un effetto di dissolvenza a 40 cm e posizionare un piano di ritaglio del rendering a 30 cm** per evitare gli oggetti più vicini.

Gli oggetti che si muovono in profondità hanno più probabilità di causare disagio rispetto agli oggetti fissi a causa del conflitto tra convergenza e accomodazione. Analogamente, costringere gli utenti a passare rapidamente tra la messa a fuoco da lontano e quella da vicino, ad esempio a causa di un ologramma popup che richiede l'interazione diretta, può causare disagio e affaticamento visivi. È quindi necessario **stare molto attenti a ridurre la frequenza con cui gli utenti devono visualizzare contenuto che si sta muovendo in profondità o cambiare rapidamente la messa a fuoco tra ologrammi vicini e lontani**. 

### <a name="additional-considerations-for-hololens-2-and-near-interaction-distances"></a>Considerazioni aggiuntive per HoloLens 2 e le distanze di interazione vicina

Quando si progetta contenuto per l'interazione diretta (vicina) in HoloLens 2 o **in qualsiasi applicazione in cui il contenuto deve essere posizionato a una distanza inferiore a 1 m, è necessario prestare particolare attenzione ad assicurare il comfort dell'utente**. La probabilità di disagio a causa del conflitto tra convergenza e accomodazione aumenta in modo esponenziale man mano che si riduce la distanza di visualizzazione. Inoltre, gli utenti possono riscontrare maggiori effetti di sfocatura quando visualizzano il contenuto a distanze di interazione vicine. Consigliamo quindi di testare il contenuto sottoposto a rendering sia entro la zona di posizionamento ottimale dell'ologramma sia più vicino (da meno di 1 m fino al piano di ritaglio) per essere sicuri che rimanga nitido e comodo da visualizzare. 

**Consigliamo quindi di definire un "budget di profondità" per le app in base al periodo di tempo in cui si prevede che un utente visualizzi contenuto che si trova vicino (a meno di 1 m) e che si muove in profondità**. Un esempio consiste nell'evitare di costringere l'utente a rimanere in situazioni di questo tipo per oltre un quarto del tempo. Se questo budget viene superato, è opportuno eseguire con attenzione una serie di test utente per assicurare un'esperienza confortevole costante. 

In generale, è opportuno eseguire anche un attento test per garantire che i requisiti di interazione (come la velocità di spostamento, la raggiungibilità e così via) a distanze vicine risultino confortevoli per gli utenti. 


### <a name="guidance-for-immersive-devices"></a>Indicazioni per i dispositivi di tipo immersive

Per i dispositivi di tipo immersive sono comunque valide le linee guida e le procedure consigliate per HoloLens, ma i valori specifici per la zona di comfort variano a seconda della distanza focale rispetto al display. In generale, le distanze focali rispetto a questi display sono comprese tra 1,25 e 2,5 m. In caso di dubbio, è opportuno evitare di eseguire il rendering di oggetti di interesse troppo vicino agli utenti e provare invece a mantenere la maggior parte del contenuto ad almeno 1 m.

## <a name="interpupillary-distance-and-vertical-offset"></a>Distanza interpupillare e offset verticale

Quando viene visualizzato contenuto digitale sui caschi con visore, la posizione degli occhi dell'utente rispetto alla posizione di visualizzazione del contenuto digitale ha un'importanza critica. In particolare, sia la distanza interpupillare ([IPD](https://en.wikipedia.org/wiki/Pupillary_distance)) sia l'offset verticale (VO) sono importanti per una visualizzazione confortevole di contenuto digitale su caschi di questo tipo. 

Il valore di IPD si riferisce alla distanza tra le pupille, ovvero i punti centrali degli occhi di un individuo. Il valore di VO si riferisce invece al possibile offset verticale del contenuto digitale visualizzato da ogni occhio rispetto all'asse orizzontale degli occhi dell'utente (che NON corrisponde all'offset orizzontale, o disparità binoculare). La corrispondenza errata di almeno uno di questi fattori può peggiorare gli effetti del disagio provato dall'utente a causa del conflitto tra convergenza e accomodazione, ma può causare disturbo anche quando questo conflitto è ridotto al minimo (ad esempio, nel caso di contenuto visualizzato alla distanza focale di 2 m di HoloLens). 

### <a name="guidance-for-holographic-devices"></a>Indicazioni per i dispositivi olografici

#### <a name="hololens-1st-gen"></a>HoloLens (prima generazione)

Per HoloLens (prima generazione), il valore di IPD viene stimato e impostato durante la [calibrazione](calibration.md) del dispositivo. Per i nuovi utenti di un dispositivo già configurato, è necessario eseguire la calibrazione o impostare il valore di IPD manualmente. Il valore di VO dipende completamente dal modo in cui viene indossato il dispositivo. In particolare, per ridurre al minimo il valore di VO, il dispositivo deve essere posizionato sulla testa dell'utente in modo tale che i display si trovino allo stesso livello dell'asse degli occhi. 

#### <a name="hololens-2"></a>HoloLens 2

Per HoloLens 2, il valore di IPD viene stimato e impostato durante la [calibrazione](calibration.md) del dispositivo rispetto agli occhi. Per i nuovi utenti di un dispositivo già configurato, è necessario eseguire la calibrazione per assicurarsi che il valore di IPD sia impostato correttamente. In HoloLens 2 il valore di VO viene calcolato automaticamente. 

### <a name="guidance-for-immersive-devices"></a>Indicazioni per i dispositivi di tipo immersive

I caschi con visore di tipo immersive di Windows Mixed Reality non prevedono la calibrazione automatica per i valori di IPD o VO. Il valore di IPD può essere impostato manualmente nel software (nelle impostazioni del Portale realtà mista, vedi la sezione relativa alla [calibrazione](calibration.md)). In alternativa, alcuni caschi con visore sono dotati di un dispositivo di scorrimento meccanico che consente all'utente di adattare la spaziatura delle lenti a una posizione comoda, che corrisponda approssimativamente alla distanza interpupillare. 

## <a name="rendering-rates"></a>Velocità di rendering

Le app di realtà mista sono veramente straordinarie perché gli utenti possono muoversi liberamente nel mondo e interagire con contenuto virtuale come se fossero oggetti reali. Per mantenere questa impressione, è fondamentale eseguire il rendering degli ologrammi in modo che risultino stabili nel mondo e si muovano senza interruzioni di continuità. Il rendering ad [almeno 60 fotogrammi al secondo (FPS)](understanding-performance-for-mixed-reality.md) consente di raggiungere questo obiettivo. Esistono alcuni dispositivi per la realtà mista che supportano il rendering a una frequenza dei fotogrammi superiore a 60 FPS e per questi dispositivi è fortemente consigliabile eseguire il rendering a una frequenza più elevata per offrire agli utenti un'esperienza ottimale.

**Approfondimenti**

Per disegnare gli ologrammi in modo che appaiano [stabili nel mondo reale o virtuale](hologram-stability.md), le app devono eseguire il rendering delle immagini dalla posizione dell'utente. Poiché il rendering delle immagini richiede tempo, HoloLens e altri dispositivi di Windows Mixed Reality eseguono una stima della posizione in cui si troverà la testa di un utente quando le immagini verranno visualizzate nei display. Questo algoritmo di stima è un'approssimazione. Gli algoritmi e l'hardware di Windows Mixed Reality consentono di regolare l'immagine sottoposta a rendering in modo da tenere conto della discrepanza tra la posizione stimata della testa e quella effettiva. Questo processo ha l'effetto di mostrare l'immagine visualizzata dall'utente come se sottoposta a rendering dalla posizione corretta e gli ologrammi appaiono stabili. Gli aggiornamenti funzionano meglio per le piccole variazioni della posizione della testa e non possono tenere completamente conto di alcune differenze delle immagini sottoposte a rendering, come quelle causate dalla parallasse di movimento.

**Con il rendering a una frequenza dei fotogrammi minima di 60 FPS, due aspetti consentono di rendere stabili gli ologrammi:**
1. Riduzione dell'effetto di tremolio, caratterizzato da immagini doppie o con movimento non uniforme. Un movimento dell'ologramma più veloce e velocità di rendering inferiori determinano un effetto di tremolio più pronunciato. Pertanto, una frequenza dei fotogrammi di 60 FPS (o la massima velocità di rendering del dispositivo) consentirà di evitare questo effetto di tremolio.
2. Riduzione della latenza complessiva. In un motore con un thread di gioco e un thread di rendering eseguiti contemporaneamente, l'esecuzione a 30 FPS può causare un aumento della latenza di 33,3 ms. La riduzione della latenza consente di ridurre l'errore di stima e aumentare la stabilità degli ologrammi.

**Analisi delle prestazioni**

Sono disponibili diversi strumenti per sottoporre a benchmark della frequenza dei fotogrammi dell'applicazione, ad esempio:
* GPUView
* Debugger grafica di Visual Studio
* Profiler integrati nei motori 3D come Frame Debugger in Unity

## <a name="self-motion-and-user-locomotion"></a>Movimento autonomo e locomozione dell'utente

L'unica limitazione è rappresentata dalle dimensioni dello spazio fisico. Se vuoi consentire agli utenti di spostarsi più lontano nell'ambiente virtuale rispetto a quanto è possibile nella stanza reale, devi implementare una forma di movimento puramente virtuale. Tuttavia, un movimento virtuale sostenuto che non corrisponde al movimento fisico dell'utente può spesso provocare una sensazione di mal d'auto. Questo effetto è dovuto agli *indizi visivi* per il movimento autonomo provenienti dal *mondo virtuale* che sono in conflitto con gli [indizi dell'apparato vestibolare](https://en.wikipedia.org/wiki/Vestibular_system) per il movimento autonomo provenienti dal *mondo reale*.

Per fortuna, puoi evitare questo problema seguendo alcuni suggerimenti per l'implementazione della locomozione dell'utente:
* Inserisci sempre l'utente nel controllo dei movimenti: un movimento autonomo imprevisto può risultare particolarmente problematico.
* Gli uomini sono molto sensibili alla direzione della forza di gravità. Pertanto, evita di usare in particolare movimenti verticali non avviati dall'utente.

### <a name="guidance-for-holographic-devices"></a>Indicazioni per i dispositivi olografici

Un metodo per consentire all'utente di spostarsi in un'altra posizione in un ambiente virtuale di grandi dimensioni consiste nel dare l'impressione di stare spostando un piccolo oggetto nella scena. Questo effetto può essere ottenuto nel modo seguente:
   1. Fornisci un'interfaccia in cui l'utente può selezionare un punto nell'ambiente virtuale in cui vuole spostarsi.
   2. Al momento della selezione, compatta il rendering della scena su un'area circolare intorno al punto desiderato.
   3. Mantenendo il punto selezionato, consenti all'utente di spostare l'area circolare come se fosse un oggetto di piccole dimensioni. L'utente potrà quindi spostare la selezione vicino ai piedi.
   4. Al momento della deselezione, riprendi il rendering dell'intera scena.

### <a name="guidance-for-immersive-devices"></a>Indicazioni per i dispositivi di tipo immersive

L'approccio precedente indicato per un dispositivo olografico non funziona altrettanto bene in un dispositivo di tipo immersive perché richiede che l'app esegua il rendering di una grande area nera vuota o di un altro ambiente predefinito mentre viene spostata l'area circolare. Questa modalità di rendering ha l'effetto di disturbare il senso di immersione del dispositivo. Una soluzione per la locomozione dell'utente in un visore VR immersive consiste nell'adottare un approccio di tipo "blink". Questa implementazione consente all'utente di controllare il proprio movimento e offre una breve impressione di spostamento, ma così breve che l'utente si sentirà meno disorientato dal movimento autonomo puramente virtuale:
   1. Fornisci un'interfaccia in cui l'utente può selezionare un punto nell'ambiente virtuale in cui vuole spostarsi.
   2. Al momento della selezione, inizia un movimento simulato molto rapido (100 m/s) verso tale posizione, mentre si dissolve rapidamente il rendering.
   3. Inverti la dissolvenza del rendering dopo aver terminato la traslazione.

## <a name="heads-up-displays"></a>Visori a sovrimpressione

Nei videogiochi in cui si spara in prima persona, i visori a sovrimpressione (HUD, Head-Up Display) presentano costantemente informazioni, come lo stato dei giocatori, piccole mappe e le scorte disponibili, direttamente sullo schermo. Questi visori sono utili per consentire al giocatore di rimanere informato senza alcuna intrusione nell'esperienza di gioco. Nelle esperienze di realtà mista, i visori a sovrimpressione possono causare notevole fastidio e devono essere adattati al contesto più immersivo. In particolare, i visori a sovrimpressione bloccati rigidamente all'orientamento della testa dell'utente possono causare disagio. Se un'app richiede un visore di questo tipo, è preferibile bloccarlo al *corpo* anziché alla testa. Questo approccio può essere implementato come un set di visualizzazioni che si spostano immediatamente con l'utente, ma non vengono ruotate con la sua testa finché non viene raggiunta una soglia di rotazione. Una volta eseguita la rotazione, il visore può essere riorientato in modo da presentare le informazioni nel campo di visione dell'utente. L'implementazione di una rotazione 1:1 per un visore a sovrimpressione rispetto ai movimenti della testa dell'utente deve essere sempre evitata.

## <a name="text-legibility"></a>Leggibilità del testo

La leggibilità ottimale del testo può aiutare a ridurre l'affaticamento oculare e a mantenere una posizione confortevole, soprattutto in applicazioni o scenari che richiedono la lettura di testo usando un casco con visore. La leggibilità del testo dipende da diversi fattori, tra cui varie proprietà di visualizzazione (ad esempio, la densità dei pixel, la luminosità e il contrasto), le proprietà delle lenti (ad esempio, l'aberrazione cromatica) e le proprietà del testo o del tipo di carattere (ad esempio, le caratteristiche specifiche del tipo di carattere, come lo spessore, la spaziatura, la presenza di grazie, il colore del carattere e quello dello sfondo).  

In generale, consigliamo di testare le applicazioni specifiche per determinare la leggibilità del testo e aumentare il più possibile le dimensioni dei caratteri per assicurare un'esperienza confortevole. Di seguito sono riportate alcune indicazioni generali come punto di partenza per lo sviluppo. Tieni presente che tutte le dimensioni dei caratteri sono indicate in gradi di [angolo visivo](https://en.wikipedia.org/wiki/Visual_angle) anziché in specifiche dimensioni fisiche. Questo consente di determinare qualsiasi distanza entro la zona di posizionamento ottimale degli ologrammi perché tiene conto sia delle dimensioni del testo sia della distanza in cui il testo appare all'utente. 

Per istruzioni più dettagliate, vedi gli articoli [Caratteri tipografici](typography.md) e [Testo in Unity](text-in-unity.md).

### <a name="guidance-for-holographic-devices"></a>Indicazioni per i dispositivi olografici

Per i dispositivi olografici, il rendering di testo nero/scuro su uno sfondo bianco/chiaro fornisce il rapporto di contrasto più coerente perché lo sfondo ha l'effetto di occludere l'interferenza del mondo reale dietro il rendering. Il rendering di testo bianco/chiaro su uno sfondo nero/scuro consente una maggiore interferenza del mondo reale, che può influire sulla leggibilità del testo. 

#### <a name="hololens-1st-gen"></a>HoloLens (prima generazione)

La dimensione minima per la leggibilità dei caratteri (dalla linea di base all'estremità dell'asta ascendente) è approssimativamente di 0,35° e il valore più confortevole per questa dimensione è almeno di circa 0,5° per la lettura di contenuto presentato a una distanza di 2 m dall'utente. 

#### <a name="hololens-2"></a>HoloLens 2

Le dimensioni minime per la leggibilità dei caratteri (dalla linea di base all'estremità dell'asta ascendente) sono approssimativamente le seguenti: 
   - 0,4°-0,5° a 45 cm (distanza di manipolazione diretta) 
   - 0,35°-0, 4° a 2 m
   
Le dimensioni confortevoli per la leggibilità dei caratteri (dalla linea di base all'estremità dell'asta ascendente) sono approssimativamente le seguenti: 
   - 0,65°-0,8° a 45 cm (distanza di manipolazione diretta)
   - 0,6°-0,75° a 2 m

Si noti che le dimensioni dei caratteri devono essere leggermente più grandi per il testo a distanza di manipolazione diretta a causa del conflitto tra convergenza e accomodazione descritto in precedenza. Gli occhi degli utenti riescono ad accomodarsi a una distanza di 2 m sul display HoloLens e pertanto il contenuto sottoposto a rendering a una distanza minore, ad esempio 45 cm, può apparire più sfocato agli utenti. 

### <a name="guidance-for-immersive-devices"></a>Indicazioni per i dispositivi di tipo immersive

I dispositivi di tipo immersive presentano in genere rapporti di contrasto più elevati a causa dell'occlusione completa dell'ambiente esterno, ma in parte possono avere una minore densità di pixel effettiva, a causa dell'ingrandimento delle lenti di fronte ai display. 

Per i caschi con visore di tipo immersive di Windows Mixed Reality, la dimensione minima per la leggibilità dei caratteri in verticale (dalla linea di base all'estremità dell'asta ascendente) è approssimativamente di 0,7-0,9° e il valore più confortevole per questa dimensione è di circa 1,0° per la lettura di contenuto presentato a una distanza di 2 m dall'utente.

## <a name="gaze-direction"></a>Direzione dello sguardo

Per evitare l'affaticamento oculare e la tensione a livello cervicale, il contenuto dovrebbe essere progettato in modo da evitare movimenti eccessivi di occhi e collo.
* **Evita** angolature dello sguardo di oltre 10 gradi al di sopra dell'orizzonte (spostamento verticale)
* **Evita** angolature dello sguardo di oltre 60 gradi al di sotto dell'orizzonte (spostamento verticale)
* **Evita** rotazioni del collo di oltre 45 gradi rispetto al centro (spostamento orizzontale)

L'angolo dello sguardo considerato ottimale (condizione di riposo) è compreso tra 10 e 20 gradi al di sotto dell'orizzonte, poiché la testa tende a inclinarsi leggermente verso il basso, soprattutto nel corso delle attività.

![Campo di visualizzazione consentito in base all'intervallo di movimento del collo](images/optimal-field-of-view-2.png)<br>
*Campo di visualizzazione consentito in base all'intervallo di movimento del collo*

## <a name="arm-positions"></a>Posizioni delle braccia

L'affaticamento muscolare può aumentare quando gli utenti devono tenere una mano alzata per tutta la durata di un'esperienza. Può anche essere faticoso per l'utente dover effettuare ripetutamente movimenti di simulazione del tocco con un dito per periodi prolungati. Consigliamo pertanto di evitare di richiedere movimenti ripetuti e costanti. Questo obiettivo può essere raggiunto incorporando brevi interruzioni oppure offrendo la possibilità di interagire con l'app con una combinazione di gesti e input vocale.

## <a name="see-also"></a>Vedi anche
* [Sguardo fisso](gaze-and-commit.md)
* [Stabilità degli ologrammi](hologram-stability.md)
* [Interazioni istintive](interaction-fundamentals.md)
* [Frame olografico](holographic-frame.md)
* [Calibrazione](calibration.md)

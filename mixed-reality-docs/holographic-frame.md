---
title: Frame olografico
description: Gli utenti vedono il mondo della realtà mista tramite il frame olografico.
author: mavitazk
ms.author: mavitazk
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, realtà mista di Windows, frame olografico, campo di visualizzazione
ms.openlocfilehash: c505eadbc16bb59143313aa62dd7c9d95384e0c8
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974920"
---
# <a name="holographic-frame"></a>Frame olografico

Gli utenti vedono il mondo della realtà mista tramite un viewport rettangolare basato sulle cuffie. In HoloLens questa area rettangolare viene chiamata frame olografico e consente agli utenti di visualizzare il contenuto digitale sovrapposto al mondo reale. La progettazione di esperienze ottimizzate per il frame olografico consente di creare opportunità, attenuare le esigenze e migliorare l'esperienza utente di applicazioni di realtà miste.

## <a name="designing-for-content"></a>Progettazione per il contenuto

Spesso gli sviluppatori hanno la necessità di limitare l'ambito della propria esperienza a ciò che l'utente può visualizzare immediatamente, sacrificando la scalabilità reale per garantire che l'utente visualizzi un oggetto nel suo complesso. Analogamente, le finestre di progettazione con applicazioni complesse spesso sovraccaricano il frame olografico con contenuto, che sovraccarica gli utenti con interazioni complesse e interfacce ingombranti. I progettisti che creano contenuto di realtà mista non devono limitare la loro esperienza a direttamente davanti all'utente e all'interno della loro immediata visualizzazione. Se il mondo fisico intorno all'utente è mappato, tutte queste superfici dovrebbero essere considerate come un'area di disegno potenziale per il contenuto digitale e le interazioni. La corretta progettazione di interazioni e contenuto all'interno di un'esperienza deve incoraggiare l'utente a spostarsi nello spazio, indirizzando la loro attenzione ai contenuti chiave e aiutando a vedere il potenziale completo della realtà mista.

Forse la tecnica più importante per incoraggiare lo spostamento e l'esplorazione all'interno di un'app è **consentire agli utenti di adattarsi all'esperienza**. Fornire agli utenti un breve periodo di tempo "senza attività" con il dispositivo. Questa operazione può essere semplice quanto inserire un oggetto nello spazio e consentire agli utenti di spostarsi all'interno o raccontare un'introduzione all'esperienza. Questa volta dovrebbe essere privo di attività critiche o di movimenti specifici, ad esempio l'uso di un tocco aereo, invece lo scopo di consentire agli utenti di adattarsi alla visualizzazione del contenuto attraverso il dispositivo prima di richiedere interattività o avanzare attraverso le fasi dell'applicazione. Se è la prima volta che si tratta di un utente con il dispositivo, questo è particolarmente importante in quanto si familiarizzano con la visualizzazione dei contenuti attraverso la cornice olografica e la natura degli ologrammi.

### <a name="large-objects"></a>Oggetti di grandi dimensioni

Spesso il contenuto che un'esperienza richiede, in particolare il contenuto reale, sarà maggiore del frame olografico. Gli oggetti che in genere non rientrano nel frame olografico devono essere compattati quando vengono introdotti per la prima volta (a una scala più piccola o a distanza). La chiave **consente agli utenti di visualizzare le dimensioni complete dell'oggetto** prima che la scala sovraccarica il frame. Ad esempio, deve essere visualizzato un elefante olografico per adattarlo completamente all'interno del frame, consentendo agli utenti di formare una conoscenza spaziale della forma complessiva dell'animale, prima di ridimensionarlo alla [scalabilità reale](scale.md) in prossimità dell'utente.

Con le dimensioni complete dell'oggetto, gli utenti hanno quindi la speranza di dove spostarsi e cercare parti specifiche di tale oggetto. Analogamente, in un'esperienza con contenuto immersivo, può essere utile per fare riferimento a tutte le dimensioni del contenuto. Se, ad esempio, l'esperienza implica l'esplorazione di un modello di una casa virtuale, potrebbe essere utile avere una versione più piccola delle dimensioni della casa bambola dell'esperienza che gli utenti possono attivare per capire dove si trovano all'interno della casa.

Per un esempio di progettazione di oggetti di grandi dimensioni, vedere [Volvo Cars](holographic-frame.md#volvo-cars).

### <a name="many-objects"></a>Molti oggetti

Le esperienze con molti oggetti o componenti dovrebbero prendere in considerazione l'uso dello spazio completo per l'utente per evitare di ingombrare il frame olografico direttamente davanti all'utente. In generale, è consigliabile introdurre il contenuto a un'esperienza lentamente e ciò è particolarmente vero con le esperienze che prevedono la gestione di molti oggetti per l'utente. Analogamente a quanto avviene con gli oggetti di grandi dimensioni, la chiave consiste nel **consentire agli utenti di comprendere il layout del contenuto** nell'esperienza, aiutandoli a comprendere in modo spaziale le attività che si aggirano quando si aggiungono contenuti all'esperienza.

Una tecnica per ottenere questo risultato è fornire punti persistenti (noti anche come punti di riferimento) nell'esperienza di ancoraggio del contenuto al mondo reale. Ad esempio, un riferimento può essere un oggetto fisico nel mondo reale, ad esempio una tabella in cui viene visualizzato contenuto digitale, o un oggetto digitale, ad esempio un set di schermate digitali in cui viene visualizzato spesso il contenuto. Gli oggetti possono anche essere posizionati nella periferia del frame olografico per incoraggiare l'utente a esaminare il contenuto della chiave, mentre l'individuazione del contenuto oltre la periferia può essere assistita dai [direttori di attenzione](holographic-frame.md#attention-directors).

L'inserimento di oggetti nella periferia può incoraggiare gli utenti a esaminare il lato e questo può essere assistito dai direttori di attenzione, come descritto di seguito.

## <a name="user-comfort"></a>Comodità utente

Per le esperienze di realtà miste con oggetti di grandi dimensioni o con molti oggetti, è fondamentale prendere in considerazione la quantità di movimento della testa e del collo necessaria per interagire con il contenuto. Le esperienze possono essere divise in tre categorie in termini di movimento Head: **Orizzontale** (Side-to-side), **verticale** (verso l'alto e verso il basso) o **immersiva** (orizzontale e verticale). Quando possibile, limitare la maggior parte delle interazioni alle categorie orizzontali o verticali, idealmente con la maggior parte delle esperienze che avvengono al centro del frame olografico mentre la testa dell'utente si trova in una posizione neutra. Evitare le interazioni che consentono all'utente di spostare costantemente la visualizzazione in posizioni Head non naturali (ad esempio, cercando sempre di accedere a un'interazione del menu principale).

![L'area ottimale per il contenuto è da 0 a 35 gradi sotto l'orizzonte](images/optimal-field-of-view-2-750px.png)<br>
*L'area ottimale per il contenuto è da 0 a 35 gradi sotto l'orizzonte*

Lo spostamento della testa orizzontale è più [comodo](comfort.md) per le interazioni frequenti, mentre i movimenti verticali devono essere riservati per gli eventi non comuni. Ad esempio, un'esperienza che interessa una sequenza temporale orizzontale molto estesa deve limitare lo spostamento verticale della testa per le interazioni, ad esempio l'analisi di un menu.

Si consiglia di incoraggiare lo spostamento completo del corpo, anziché semplicemente il movimento Head, posizionando gli oggetti intorno allo spazio dell'utente. Le esperienze con lo spostamento di oggetti o oggetti di grandi dimensioni devono prestare particolare attenzione al movimento Head, soprattutto laddove richiedono un movimento frequente lungo gli assi orizzontali e verticali.

## <a name="interaction-considerations"></a>Considerazioni sull'interazione

Come per il contenuto, le interazioni in un'esperienza di realtà mista non devono essere limitate a ciò che l'utente può visualizzare immediatamente. Le interazioni possono essere inserite ovunque nello spazio reale per l'utente e queste interazioni possono aiutare gli utenti a spostarsi ed esplorare le esperienze.

### <a name="attention-directors"></a>Direttori di attenzione

L'indicazione di punti di interesse o di interazioni chiave può essere fondamentale per progredire gli utenti attraverso un'esperienza. L'attenzione degli utenti e lo spostamento del frame olografico possono essere indirizzati in modi delicati o pesanti. Ricordarsi di bilanciare i direttori di attenzione con periodi di esplorazione gratuita in realtà mista, in particolare all'inizio di un'esperienza, per evitare di sovraccaricare l'utente. In generale, esistono due tipi di amministratori di attenzione:
* **Amministratori visivi:** Il modo più semplice per informare l'utente che deve spostarsi in una direzione specifica è fornire un'indicazione visiva. Questa operazione può essere eseguita tramite un effetto visivo, ad esempio un percorso che l'utente può seguire visivamente verso la parte successiva dell'esperienza, o anche come frecce direzionali semplici. Si noti che tutti gli indicatori visivi devono essere contenuti all'interno dell'ambiente dell'utente, non ' Attached ' al frame olografico o al cursore.
* **Amministratori audio:** Il [suono spaziale](spatial-sound-design.md) può fornire un modo efficace per stabilire gli oggetti in una scena (avvisare gli utenti degli oggetti che entrano in un'esperienza) o per indirizzare l'attenzione a un punto specifico nello spazio (per spostare la visualizzazione dell'utente verso gli oggetti chiave). Usare i direttori audio per guidare l'attenzione dell'utente può essere più sottile e meno intrusivo rispetto ai direttori visivi. In alcuni casi, può essere preferibile iniziare con un direttore audio, quindi passare a un oggetto visivo, se l'utente non riconosce il segnale. I direttori audio possono anche essere abbinati ai direttori visivi per un'ulteriore enfasi.

### <a name="commanding-navigation-and-menus"></a>Comandi, navigazione e menu

Le interfacce in situazioni di realtà mista idealmente sono abbinate strettamente al contenuto digitale che controllano. Di conseguenza, i menu 2D a virgola mobile non sono spesso ideali per l'interazione e possono essere difficili da usare comodamente per gli utenti all'interno del frame olografico. Per le esperienze che richiedono elementi di interfaccia quali menu o campi di testo, è consigliabile usare un [metodo tag-along](billboarding-and-tag-along.md) per seguire il frame olografico dopo un breve ritardo. Evitare di bloccare il contenuto al frame come una visualizzazione Heads-up, in quanto questo può essere disorientato per l'utente e suddividere il senso di immersione per altri oggetti digitali nella scena.

In alternativa, è consigliabile posizionare gli elementi dell'interfaccia direttamente sul contenuto specifico che controllano, consentendo alle interazioni di verificarsi naturalmente intorno allo spazio fisico dell'utente. Ad esempio, suddividere un menu complesso in parti separate. Con ogni pulsante o gruppo di controlli collegato all'oggetto specifico interessato dall'interazione. Per adottare ulteriormente questo concetto, considerare l'uso di [oggetti interagibili](interactable-object.md).

### <a name="gaze-and-gaze-targeting"></a>Selezione mirata e sguardo

Il frame olografico presenta uno strumento che consente allo sviluppatore di attivare le interazioni e di valutare la posizione dell'attenzione dell'utente. [Sguardi](gaze.md) è una delle [interazioni chiave in HoloLens, in](interaction-fundamentals.md)cui lo sguardo può essere abbinato a [movimenti](gestures.md) (ad esempio con il tocco di aria) o [voce](voice-input.md) (che consente interazioni vocali più brevi e più naturali). In questo modo, il frame olografico è uno spazio che consente di osservare il contenuto digitale e di interagire con esso. Se l'esperienza richiede l'interazione con più oggetti intorno allo spazio dell'utente (ad esempio, la selezione multipla di oggetti intorno allo spazio dell'utente con lo sguardo + movimento), provare a portare tali oggetti nella visualizzazione dell'utente o limitare la quantità di intestazione necessaria spostamento per promuovere la [comodità degli utenti](comfort.md).

Lo sguardo può essere usato anche per tenere traccia dell'attenzione degli utenti attraverso un'esperienza e per individuare gli oggetti o le parti della scena a cui l'utente ha fatto la massima attenzione. Questo può essere usato in particolare per il debug di un'esperienza, consentendo a strumenti analitici come Heatmaps di vedere dove gli utenti spendono la maggior parte del tempo o mancano alcuni oggetti o interazioni. Il rilevamento degli sguardi può anche fornire uno strumento potente per i facilitatori delle esperienze (vedere l'esempio [di cucina di Lowe](holographic-frame.md#lowes-kitchen) ).

## <a name="performance"></a>Prestazioni

L'uso corretto del frame olografico è fondamentale per l'esperienza di [qualità delle prestazioni](understanding-performance-for-mixed-reality.md) . Un problema tecnico e di usabilità comune è l'overload del frame dell'utente con contenuto digitale, causando un peggioramento delle prestazioni di rendering. Si consiglia invece di usare lo spazio completo per l'utente per disporre il contenuto digitale, usando le tecniche descritte in precedenza, per ridurre il carico di rendering e garantire una qualità di visualizzazione ottimale.

Il contenuto digitale all'interno del frame olografico della HoloLens può anche essere abbinato al [piano](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md) di stabilizzazione per ottenere prestazioni ottimali e [stabilità olografica](hologram-stability.md).

## <a name="examples"></a>Esempi

### <a name="volvo-cars"></a>Automobili Volvo

>[!VIDEO https://www.youtube.com/embed/DilzwF90vec]

Nell'esperienza showroom di Volvo Cars i clienti sono invitati a conoscere le nuove funzionalità di un'auto in un'esperienza HoloLens guidata da un associo Volvo. Volvo ha affrontato una sfida con il frame olografico: un'auto di dimensioni eccessive è troppo grande per essere posizionata immediatamente accanto a un utente. La soluzione consisteva nell'iniziare l'esperienza con un punto di interesse fisico, una tabella centrale nello showroom, con un modello digitale più piccolo dell'auto posizionata sopra la tabella. In questo modo si garantisce che l'utente visualizzi l'intera automobile quando viene introdotta, consentendo un senso di comprensione spaziale una volta che l'auto raggiunge la scalabilità reale in un secondo momento nell'esperienza.

L'esperienza di Volvo USA anche i direttori visivi, creando un effetto visivo lungo dal modello di auto su scala ridotta sulla tabella a un muro della stanza show. Questo comporta un effetto "Magic Window", che mostra la visualizzazione completa dell'auto a distanza, illustrando altre funzionalità dell'auto su scala reale. Il movimento Head è orizzontale, senza alcuna interazione diretta dell'utente (raccogliendo invece i segnali visivi e dalla narrazione dell'esperienza dell'associazione di Volvo).

### <a name="lowes-kitchen"></a>Cucina di Lowe

Un'esperienza di archiviazione di Lowe invita i clienti a un modello a scalabilità completa di una cucina per presentare diverse opportunità di rimodellazione, come illustrato nella HoloLens. La cucina nello Store fornisce uno sfondo fisico per gli oggetti digitali, un'area di disegno vuota di appliance, piani di appoggio e cabinet per l'esperienza di realtà mista.

Le superfici fisiche fungono da punti di riferimento statici per l'utente nell'esperienza, in quanto l'associazione di un Lowe guida l'utente attraverso diverse opzioni di prodotto e termina. In questo modo, l'associazione può indirizzare verbalmente l'attenzione dell'utente a "frigorifero" o "centro della cucina" per presentare contenuti digitali.

![L'associazione di un Lowe usa un tablet per guidare i clienti nell'esperienza HoloLens.](images/loweskitchen-750px.jpg)<br>
*L'associazione di un Lowe usa un tablet per guidare i clienti nell'esperienza HoloLens.*

L'esperienza dell'utente è gestita, in parte, da un'esperienza tablet controllata dall'associazione di Lowe. In questo caso parte del ruolo di associazione potrebbe anche limitare un movimento di testa eccessivo, indirizzando la loro attenzione in modo uniforme nei punti di interesse della cucina. L'esperienza di tablet fornisce anche l'associazione Lowe ai dati di sguardi sotto forma di una vista mappa termica della cucina, per comprendere dove si trova l'utente, ad esempio in un'area specifica del cabinet, per fornire più accuratamente le linee guida per la rimodellazione.

Per informazioni più approfondite sull'esperienza di cucina di Lowe, vedere l'intervento [di Microsoft a ignite 2016](https://www.youtube.com/watch?v=gC_4JxF0e_k).

### <a name="fragments"></a>Fragments

Nei frammenti di gioco HoloLens, lo spazio di lavoro è trasformato in una scena di criminalità virtuale che mostra indizi ed evidenze, oltre a una sala riunioni virtuale, in cui si parla con caratteri che si siedono sulle poltrone e si appoggiano sulle pareti.

![I frammenti sono stati progettati per essere utilizzati nella Home page di un utente, con caratteri che interagiscono con oggetti e superfici reali.](images/fragments-750px.jpg)<br>
*I frammenti sono stati progettati per essere utilizzati nella Home page di un utente, con caratteri che interagiscono con oggetti e superfici reali.*

Quando gli utenti iniziano inizialmente l'esperienza, viene assegnato un breve periodo di regolazione, in cui è necessaria un'interazione molto limitata, che invece li incoraggia a cercare. Questo consente anche di garantire che la chat sia mappata correttamente per il contenuto interattivo del gioco.

In tutta l'esperienza, i caratteri diventano punti focali e fungono da direttori visivi (movimenti Head tra i caratteri, che si rivelano o eseguono movimenti verso aree di interesse). Il gioco si basa anche su segnali visivi più evidenti quando un utente impiega troppo tempo per trovare un oggetto o un evento e USA in modo intensivo l'audio spaziale, specialmente con le voci dei caratteri quando si immette una scena.

### <a name="destination-mars"></a>Destinazione: Mars

Nella destinazione: Mars Experience in primo piano presso il [Kennedy Space Center della NASA](https://blogs.windows.com/devices/2016/09/19/hololens-experience-destination-mars-now-open-at-kennedy-space-center-visitor-complex/), i visitatori sono stati invitati a un viaggio immersivo alla superficie di Marte, guidato dalla rappresentazione virtuale del leggendario Astronaut Buzz Aldrin.

![Un Buzz virtuale di Buzz diventa il punto focale per gli utenti della destinazione: Mars.](images/destinationmars-750px.png)<br>
*Un Buzz virtuale di Buzz diventa il punto focale per gli utenti della destinazione: Mars.*

Come esperienza immersiva, questi utenti erano invitati a cercare, spostando il capo in tutte le direzioni per vedere il panorama marziano virtuale. Anche se per garantire la comodità degli utenti, la narrazione e la presenza virtuale di Buzz Aldrin hanno fornito un punto focale nell'intera esperienza. Questa registrazione virtuale di Buzz (creata da [Microsoft Mixed Reality Capture Studios](https://www.microsoft.com/mixed-reality/capture-studios)) si trovava in una reale dimensione umana, nell'angolo della stanza, consentendo agli utenti di visualizzarla in una visualizzazione quasi completa. La narrazione di Buzz indirizza gli utenti a concentrarsi su punti diversi dell'ambiente (ad esempio, un set di rocce marziane al piano o un intervallo di Mountain a distanza) con modifiche di scena specifiche o oggetti introdotti da lui.

![I narratori virtuali si attiverà per seguire lo spostamento di un utente, creando un punto focale potente nell'intera esperienza.](images/gazereset-750px.png)<br>
*I narratori virtuali si attiverà per seguire lo spostamento di un utente, creando un punto focale potente nell'intera esperienza.*

La rappresentazione realistica di Buzz ha fornito un punto focale potente, completando tecniche sottili per trasformare il Buzz verso l'utente come se fosse presente, parlando con te. Man mano che l'utente si sposta sull'esperienza, Buzz si sposta verso una soglia prima di tornare a uno stato neutro se l'utente si sposta troppo oltre la periferia. Se l'utente ha l'aspetto di Buzz completamente (ad esempio, per esaminare qualcosa altrove nella scena), quindi torna a Buzz, la posizione direzionale dell'Assistente vocale sarà ancora una volta incentrata sull'utente. Le tecniche come questa forniscono un potente senso di immersione e creano un punto focale all'interno del frame olografico, riducendo lo spostamento di un'intestazione e la promozione della [comodità degli utenti](comfort.md).

## <a name="see-also"></a>Vedere anche
* [Interazioni istintive](interaction-fundamentals.md)
* [Comodità](comfort.md)
* [Ridimensiona](scale.md)
* [Puntamento con la testa e attesa](gaze-and-dwell.md)
* [Stabilità degli ologrammi](hologram-stability.md)

---
title: Frame holographic
description: Gli utenti vedono il mondo delle realtà mista tramite il frame holographic.
author: mavitazk
ms.author: mavitazk
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, realtà mista di Windows, holographic frame, il campo visivo
ms.openlocfilehash: 6773bc03dea471c97d0c6006d2ab7853a5ef3669
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59598792"
---
# <a name="holographic-frame"></a>Frame holographic

Gli utenti vedono il mondo delle realtà mista tramite un viewport rettangolare con tecnologia le cuffie. Su HoloLens, quest'area rettangolare viene chiamato il frame holographic e consente agli utenti di visualizzare contenuto digitale da sovrapporre nel mondo reale attorno a esse. Progettazione di esperienze ottimizzate per la cornice holographic Crea opportunità, riduce le sfide e migliora l'esperienza utente delle applicazioni di realtà mista.

## <a name="designing-for-content"></a>Progettazione per il contenuto

Spesso le finestre di progettazione è la necessità di limitare l'ambito della propria esperienza per ciò che l'utente può visualizzare immediatamente, sacrificare reale scalabilità per assicurarsi che l'utente visualizza un oggetto nel suo complesso. In modo analogo agli sviluppatori di applicazioni complesse spesso sovraccaricare il frame holographic con contenuto, sovraccaricare gli utenti con le interfacce risulti troppo affollate e interazioni difficile. Le finestre di progettazione la creazione di realtà mista contenuto necessario non limitano l'esperienza per presentare direttamente all'utente e all'interno delle loro visualizzazione immediata. Se viene eseguito il mapping del mondo fisico intorno all'utente, quindi tutte queste superfici devono essere considerate un'area di disegno potenziali per le interazioni e contenuti digitali. Corretta progettazione di interazioni e contenuti all'interno di un'esperienza dovrebbe invita l'utente per spostarsi all'interno delle loro spazio, indirizzando la loro attenzione al contenuto della chiave e il supporto a vedere le potenzialità di realtà mista.

La tecnica più importante per incoraggiare lo spostamento e l'esplorazione all'interno di un'app consiste probabilmente nel **consentono agli utenti di modificare l'esperienza**. Dare agli utenti un breve periodo di tempo 'privo di attività' con il dispositivo. Può essere semplice come l'inserimento di un oggetto nello spazio e consentire agli utenti di spostare intorno a esso o il commento di un'introduzione all'esperienza. Questa volta dovrebbe essere libera di qualsiasi attività critiche o specifici di movimenti (ad esempio, aria tocco), ma lo scopo di consentire agli utenti di adattare alla visualizzazione del contenuto tramite il dispositivo prima di richiedere l'interattività o procede attraverso le fasi dell'app. Se si tratta prima volta che un utente con il dispositivo di ciò è particolarmente importante mano a mano che familiarità e visualizzando il contenuto tramite il frame holographic e la natura di vntana.

### <a name="large-objects"></a>Oggetti di grandi dimensioni

Spesso un'esperienza di chiamate per il contenuto, contenuto reali in particolare, sarà più grande della cornice holographic. Gli oggetti che normalmente non possono essere contenuta all'interno della cornice holographic dovrebbero essere ridotta per adattarsi quando vengono introdotti prima di tutto (in scala ridotta o a una distanza). È fondamentale **consentono agli utenti di visualizzare le dimensioni dell'oggetto completa** prima che la scala sovraccarica il frame. Ad esempio, un elefante holographic deve essere visualizzato per adattarsi completamente all'interno del frame, che consente agli utenti in modo da formare una conoscenza spaziale della forma complessiva dell'animale, prima di ridimensionamento per [reale scalabilità](scale.md) vicino all'utente.

Con la dimensione completa dell'oggetto presente, gli utenti hanno quindi una previsione del punto da cui spostarsi e cercare le parti specifiche di tale oggetto. Analogamente, un'esperienza coinvolgente e concreto contenuto, consente di configurare un modo per fare riferimento alla dimensione completa del contenuto. Ad esempio, se l'esperienza riguarda walking attorno a un modello di casa virtuale, può essere utile per avere una versione ridotta di dimensioni doll casa dell'esperienza che gli utenti possono attivare per capire dove si trovano all'interno della casa.

Per un esempio di progettazione per gli oggetti di grandi dimensioni, vedere [Volvo automobili](holographic-frame.md#volvo-cars).

### <a name="many-objects"></a>Numero di oggetti

Esperienze con il numero di oggetti o componenti devono è consigliabile usare lo spazio completo intorno all'utente per evitare di sovraccaricare il frame holographic direttamente davanti all'utente. In generale, è consigliabile introdurre contenuto per un'esperienza lenta e ciò è particolarmente vero con esperienze che prevede di gestire numerosi oggetti per l'utente. Proprio come con gli oggetti di grandi dimensioni, è fondamentale **consentono agli utenti di comprendere il layout del contenuto** nell'esperienza, consentendo di ottenere informazioni su spaziali What ' s attorno a esse come il contenuto viene aggiunto all'esperienza.

Una tecnica per ottenere questo risultato consiste nel fornire punti permanenti (noto anche come punti di riferimento) nell'esperienza di tale contenuto di ancoraggio con il mondo reale. Ad esempio, un punto di riferimento può essere un oggetto fisico nel mondo reale, ad esempio una tabella in cui viene visualizzato contenuto digitale o un oggetto digitale, ad esempio un set di schermate digitale in cui il contenuto viene visualizzato di frequente. Gli oggetti possono essere inseriti anche nel perimetro della cornice per incoraggiare l'utente di cercare verso la chiave del contenuto, mentre l'individuazione del contenuto di là periferia può essere supportato da holographic [directors attenzione](holographic-frame.md#attention-directors).

Impostazione di oggetti nella periferia possono incoraggiare gli utenti per la ricerca sul lato e ciò può essere supportato da directors attenzione, come descritto di seguito.

## <a name="user-comfort"></a>Fattore di comfort utente

Per realtà mista le esperienze con oggetti di grandi dimensioni o molti oggetti, è fondamentale prendere in considerazione quanta head e lo spostamento collo è necessario per interagire con il contenuto. Esperienze possono essere suddivisi in tre categorie in termini di movimento della testina: **Orizzontali** (Avanti e indietro), **verticale** (verticale), o **coinvolgenti** (orizzontali e verticali). Quando possibile, limitare la maggior parte delle interazioni alle categorie orizzontale o verticale, idealmente con la maggior parte delle esperienze che verranno eseguite nel centro del frame holographic mentre head dell'utente è in una posizione neutra. Evitare le interazioni che causano l'utente costantemente muoversi relativa visualizzazione un innaturale posizioni head (ad esempio, cercare sempre per accedere a un'interazione di menu principali).

![Area ottimale per il contenuto è da 0 a 35 gradi sotto horizon](images/optimal-field-of-view-2-750px.png)<br>
*Area ottimale per il contenuto è da 0 a 35 gradi sotto horizon*

Movimento della testina orizzontale è ulteriori [familiarità](comfort.md) per interazioni frequenti, durante gli spostamenti verticali devono essere riservati per eventi non comuni. Ad esempio, un'esperienza che interessano una sequenza temporale orizzontale lungo necessario limitare testina verticale per le interazioni (ad esempio, guardando verso il basso in un menu di scelta).

È consigliabile promuovere il movimento del corpo di full, anziché semplicemente testina, inserendo oggetti tutto lo spazio dell'utente. Esperienze con lo spostamento di oggetti o oggetti di grandi dimensioni è necessario prestare particolare attenzione al movimento della testina, in particolare che richiedono la disponibilità spostamento frequente lungo gli assi orizzontali e verticali.

## <a name="interaction-considerations"></a>Considerazioni sull'interazione

Come con contenuto, le interazioni in un'esperienza di realtà mista non devono essere limitate a ciò che l'utente può visualizzare immediatamente. Interazioni possono avvenire in qualsiasi punto nello spazio del mondo reale intorno all'utente e tali interazioni possono incoraggiare gli utenti per spostarsi all'interno e l'esplorazione esperienze.

### <a name="attention-directors"></a>Consiglio di attenzione

Che indica i punti di interesse o le interazioni chiave possono essere fondamentali per gli utenti di avanzamento tramite un'esperienza. Un intervento dell'utente e lo spostamento del frame holographic possono essere indirizzate in meno evidenti o scoraggiante modi. Ricordarsi di bilanciare directors attenzione con periodi di esplorazione disponibile nella realtà mista (in particolare all'inizio di un'esperienza) per evitare di sovraccaricare l'utente. In generale, esistono due tipi di casting di attenzione:
* **Consiglio Visual:** Il modo più semplice per informare l'utente che è necessario spostare in una direzione specifica è fornire un'indicazione visiva. Ciò può essere eseguita tramite un effetto visivo (ad esempio, un percorso l'utente può seguire visivamente verso la parte successiva dell'esperienza) o persino come frecce direzionali semplice. Nota che qualsiasi indicatore visivo deve basato sull'ambiente dell'utente, non 'connesso' per il frame holographic o il cursore.
* **Consiglio audio:** [Suono spaziale](spatial-sound-design.md) possono fornire un modo potente per stabilire gli oggetti in una scena (agli utenti di oggetti immettendo un'esperienza di avvisi) o per dirigere l'attenzione a un momento specifico in uno spazio (per spostare la visualizzazione dell'utente verso gli oggetti chiave). Uso di casting audio per guidare l'attenzione dell'utente può essere più complessi e meno intrusiva di casting visual. In alcuni casi, può essere consigliabile iniziare con un director audio, per poi passare a un director visual se l'utente non riconosce il segnale. Consiglio audio inoltre può essere associate visual Consiglio per enfasi aggiunto.

### <a name="commanding-navigation-and-menus"></a>Esecuzione dei comandi, navigazione e menu

Interfacce nelle esperienze di realtà mista idealmente sono abbinate strettamente con il contenuto digitale che controllano. Di conseguenza, i menu 2D spesso non sono ideali per l'interazione e possono essere difficili per gli utenti con agevolmente all'interno del fotogramma holographic. Per le esperienze che richiedono gli elementi dell'interfaccia come i menu o i campi di testo, è consigliabile usare un [metodo tag-along](billboarding-and-tag-along.md) seguire il frame holographic dopo un breve ritardo. Evitare di bloccare contenuti al frame, ad esempio una visualizzazione hud, perché ciò può essere disorienting per l'utente e interruzione il senso di full immersion per gli altri oggetti digitali nella scena.

In alternativa, è consigliabile inserire gli elementi dell'interfaccia direttamente sullo specifico contenuto che controllano, consentendo di interazioni a verificarsi naturalmente intorno a uno spazio fisico dell'utente. Ad esempio, suddividere un menu complesso in parti distinte. Con ciascun pulsante o un gruppo di controlli associata all'oggetto specifico che interessa l'interazione. Per sfruttare ulteriormente questo concetto, si consideri l'uso del [oggetti si](interactable-object.md).

### <a name="gaze-and-gaze-targeting"></a>Sguardo e sguardo targeting

Il frame holographic presenta uno strumento per gli sviluppatori per le interazioni di trigger, nonché valutare dove trova attenzione dell'utente. [Estasiati](gaze.md) è uno del [chiave interazioni nel HoloLens](interaction-fundamentals.md), in cui può essere abbinato sguardo [movimenti](gestures.md) (come con air tocco) o [vocale](voice-input.md) (consentendo per breve più naturali interazioni basate su vocali). Di conseguenza, in questo modo il frame holographic sia uno spazio per osservando contenuto digitale, nonché interagire con esso. Se l'esperienza di chiamata per l'interazione con più oggetti tutto lo spazio dell'utente (ad esempio, selezionano più oggetti tutto lo spazio dell'utente con sguardo + movimento), è consigliabile introdurre tali oggetti nella vista dell'utente o limitare la quantità di intestazione necessari lo spostamento di alzare di livello [fattore di comfort utente](comfort.md).

Sguardo anche utilizzabile per tenere traccia di un intervento dell'utente tramite un'esperienza e vedere quali oggetti o parti della scena all'utente la maggior parte dei attenzione ad. Ciò può essere particolarmente utilizzato per il debug di un'esperienza, consentendo di strumenti analitici, ad esempio mappe termiche per vedere dove gli utenti trascorrono più tempo o mancano alcuni oggetti o l'interazione. Sguardo di rilevamento può inoltre fornire uno strumento potente per strumenti di semplificazione nelle esperienze (vedere la [cucina di Lowe](holographic-frame.md#lowes-kitchen) esempio).

## <a name="performance"></a>Prestazioni

Uso corretto del frame holographic è fondamentale per il [qualità delle prestazioni](understanding-performance-for-mixed-reality.md) esperienze. Un problema comune tecnica (e l'usabilità) supporta l'overload frame dell'utente con contenuto digitale, causando una riduzione delle prestazioni per il rendering. Si consideri invece Usa lo spazio completo intorno all'utente per disporre il contenuto digitale, utilizzando le tecniche descritti in precedenza, per ridurre il carico di lavoro di rendering e garantire la qualità di una visualizzazione ottimale.

Contenuto digitale all'interno della cornice della finestra di HoloLens holographic può anche essere abbinato con il [piano di stabilizzazione](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md) per ottenere prestazioni ottimali e [stabilità ologrammi](hologram-stability.md).

## <a name="examples"></a>Esempi

### <a name="volvo-cars"></a>Automobili Volvo

>[!VIDEO https://www.youtube.com/embed/DilzwF90vec]

Nell'esperienza di sala dalle automobili Volvo, i clienti sono invitati a informazioni sulle funzionalità di un'auto di nuovo in un'esperienza di HoloLens guidato da un collega Volvo. Volvo affrontato una sfida il frame holographic: un'auto di grandi dimensioni è eccessiva per inserire subito accanto a un utente. La soluzione era per iniziare l'esperienza con un punto di riferimento fisico, una tabella centrale nella sala, con un modello più piccolo digitale dell'automobile posizionato nella parte superiore della tabella. In questo modo che l'utente visualizzi l'automobile completa quando è stato introdotto, consentendo un senso di spaziali comprendere quando si espande l'auto per la scala del mondo reale in un secondo momento nell'esperienza.

Volvo esperienza anche fa uso di visual Director, la creazione di un effetto visivo lungo dal modello su scala ridotta Auto per la tabella a una parete nella chat room show. Ciò comporta un effetto 'finestra magic', che mostra la visualizzazione completa dell'automobile a una distanza, che illustrano altre funzionalità dell'automobile su larga scala reali. Il movimento della testina in orizzontale, senza alcuna interazione diretta da parte dell'utente (invece di raccolta indicatori visivamente e da un testo descrittivo del venditore Volvo dell'esperienza).

### <a name="lowes-kitchen"></a>Cucina del Lowe

Un'esperienza di archivio del Lowe invita i clienti in un modello su larga scala di un cucina per presentare numerose opportunità di ristrutturazione, come avviene il HoloLens. Cucina nello store fornisce uno sfondo fisico per gli oggetti digitali, un'area di disegno vuota dell'Appliance, countertops e gli archivi per l'esperienza di realtà mista espandere.

Superfici fisiche punteggiate che fungono statici per l'utente a se stessi a terra nell'esperienza di come associare di un Lowe Guida l'utente tramite le opzioni di prodotto diverso e termina. In questo modo, l'associazione possibile verbalmente dirigere l'attenzione dell'utente al 'smartwatch' o 'centro di cucina"per contenuto digitale showcase.

![Associare del Lowe utilizza un tablet per guidare i clienti tramite l'esperienza di HoloLens.](images/loweskitchen-750px.jpg)<br>
*Associare del Lowe utilizza un tablet per guidare i clienti tramite l'esperienza di HoloLens.*

L'esperienza dell'utente è gestito, in parte, da un'esperienza di Tablet PC controllata dall'associazione del Lowe. Parte del ruolo del venditore in questo caso anche sarebbe per limitare un numero eccessivo testina, indirizzando la loro attenzione in modo uniforme tra i punti di interesse in cucina. L'esperienza di Tablet PC offre associato del Lowe sguardo dati sotto forma di una visualizzazione mappa termica di cucina, aiutare a comprendere dove l'utente è appartamento (ad esempio, in un'area specifica di cabinetry) in modo più accurato fornirle con Ristrutturando indicazioni.

Per un approfondimento sul esperienza cucina del Lowe, vedere [intervento di Microsoft in occasione di Ignite 2016](https://www.youtube.com/watch?v=gC_4JxF0e_k).

### <a name="fragments"></a>Frammenti

Frammenti di gioco HoloLens, salotto di si viene trasformato in scena del crimine virtuale che mostra l'evidenza e indicazioni, nonché una sala riunioni virtuale, in cui si parla con i caratteri che si trovano nelle sedie e fare affidamento sulle affisse.

![Frammenti è stato progettato per avvengono nella home page dell'utente, con l'interazione con oggetti reali e le superfici di caratteri.](images/fragments-750px.jpg)<br>
*Frammenti è stato progettato per avvengono nella home page dell'utente, con l'interazione con oggetti reali e le superfici di caratteri.*

Quando gli utenti iniziano inizialmente l'esperienza, essi sono specificati un breve periodo di regolazione, interazione minimo in cui è necessario, invece incoraggiarli alla Guardatevi intorno. Ciò consente di garantire che la chat è mappata correttamente per il contenuto interattivo del gioco.

Nell'intera esperienza di caratteri diventano punti focali e fungono da visual directors (head spostamenti tra i caratteri, l'attivazione per cercare o movimenti verso aree di interesse). Il gioco, inoltre, si basa su segnali visivi più evidenti quando un utente richiede troppo tempo per trovare un oggetto o l'evento e utilizza in modo massiccio di spaziale audio (in particolare con le voci di caratteri quando si immette una scena).

### <a name="destination-mars"></a>Destinazione: MARS

Nella destinazione: Esperienza di MARS disponibili nella [Kennedy spazio Center della NASA](https://blogs.windows.com/devices/2016/09/19/hololens-experience-destination-mars-now-open-at-kennedy-space-center-visitor-complex/), visitatori sono stati invitati a un'ottimizzazione dei viaggi immersive alla superficie del Mars, guidato dalla rappresentazione virtuale di astronautici leggendario Aldrin Buzz.

![Un Aldrin Buzz virtuale diventa il punto focale per gli utenti nell'istanza di destinazione: MARS.](images/destinationmars-750px.png)<br>
*Un Aldrin Buzz virtuale diventa il punto focale per gli utenti nell'istanza di destinazione: MARS.*

Come un'esperienza coinvolgente su, questi utenti erano incoraggiati a cercare, lo spostamento di propria testa in tutte le direzioni per visualizzare il panorama applicativo Martian virtuale. Sebbene per garantire la comodità degli utenti, commenti e presenza virtuale Buzz Aldrin fornito un punto focale nell'intera esperienza di. Questa registrazione virtuale negli ultimi tempi (creato da [misto realtà acquisire Studios di Microsoft](https://www.microsoft.com/mixed-reality/capture-studios)) da dimensioni reali, risorse umane, nell'angolo della chat room consentendo agli utenti per quest'ultimo in visualizzazione pressoché completa. Commento di buzz indirizzate agli utenti di concentrarsi su diversi punti dell'ambiente (ad esempio, un set di Martian rocks sul pavimento o un intervallo di mountain della distanza) con cambi di scena specifico o gli oggetti da lui.

![Gli assistenti virtuali vocali disattiverà seguire lo spostamento di un utente, creazione di un punto focale potenti in tutta l'esperienza.](images/gazereset-750px.png)<br>
*Gli assistenti virtuali vocali disattiverà seguire lo spostamento di un utente, creazione di un punto focale potenti in tutta l'esperienza.*

La rappresentazione realistica di Buzz fornito un punto focale potente, completato con le tecniche di meno evidenti per attivare social bookmarking su verso all'utente la sensazione è presente, parlando all'utente. Quando l'utente sposta relative all'esperienza, social bookmarking su sposterà verso chi guarda su una soglia prima di tornare a uno stato neutro se l'utente sposta troppo oltre il perimetro. Se l'utente avrà l'aspetto da social bookmarking su completamente (ad esempio, per esaminare un elemento in un' posizione nella scena) poi ai social bookmarking su, will posizione direzionale dell'Assistente vocale una sola volta nuovamente essere incentrato sull'utente. Le tecniche simile al seguente forniscono un certo senso potente di full immersion e creare un punto focale all'interno della cornice holographic, riducendo testina eccessivo e innalzamento di livello [fattore di comfort utente](comfort.md).

## <a name="see-also"></a>Vedere anche
* [Nozioni fondamentali di interazione](interaction-fundamentals.md)
* [Comfort](comfort.md)
* [Ridimensiona](scale.md)
* [Sguardo targeting](gaze-targeting.md)
* [Stabilità ologrammi](hologram-stability.md)

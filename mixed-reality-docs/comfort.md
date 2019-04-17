---
title: Comfort
description: Durante la visualizzazione fisica, il sistema di visual umano si basa su più origini di informazioni o "segnali," per interpretare le forme 3D e la posizione relativa degli oggetti.
author: erickjpaul
ms.author: erpau
ms.date: 02/13/2019
ms.topic: article
keywords: Realtà mista, progettazione, il fattore di comfort
ms.openlocfilehash: dbf7080f5b9a2ebafdbd06fca79fae717b3207ed
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604930"
---
# <a name="comfort"></a>Comfort

Durante la visualizzazione fisica, il sistema di visual umano si basa su più origini di informazioni o "segnali," per interpretare le forme 3D e le posizioni relative degli oggetti. Alcuni segnali fare affidamento solo su un singolo occhio (monoculare segnali visivi), tra cui [prospettiva lineari](https://en.wikipedia.org/wiki/Perspective_(graphical)), [dimensioni familiare](https://en.wikipedia.org/wiki/Size#Perception_of_size), relative all'occlusione, [sfocatura profondità del campo](https://en.wikipedia.org/wiki/Depth_of_field), e [ ristorazione](https://en.wikipedia.org/wiki/Accommodation_(eye)). Altre indicazioni si basano su entrambi gli occhi (segnali binoculare) e includere [vergence](https://en.wikipedia.org/wiki/Vergence) (essenzialmente le rotazioni degli occhi necessari per esaminare un oggetto relative) e [disparità binoculare](https://en.wikipedia.org/wiki/Stereopsis) (il modello delle differenze tra le proiezioni della scena sul retro degli occhi). Per garantire la massima comodità sugli schermi montato head, è importante per progettisti e sviluppatori di creare e presentare il contenuto in modo che simula il funzionano di questi segnali al mondo naturale. Dal punto di vista fisico, è anche importante progettare il contenuto che non richiede difficoltoso i movimenti del collo o agli armamenti. In questo articolo verranno prese in riportate alcune considerazioni da tenere a mente per raggiungere questi obiettivi.

## <a name="vergence-accommodation-conflict"></a>Conflitto vergence ristorazione

Per visualizzare gli oggetti in modo chiaro, è necessario esseri umani [adattare](https://en.wikipedia.org/wiki/Accommodation_%28eye%29), o modificare lo stato attivo ai loro stessi occhi, la distanza dell'oggetto. Allo stesso tempo, è necessario la rotazione di entrambi gli occhi [convergono](https://en.wikipedia.org/wiki/Convergence_(eye)) indica la distanza dell'oggetto per evitare la visualizzazione di immagini di double. Nella visualizzazione naturale, vergence e ristorazione sono collegate. Quando si visualizza un valore vicino (ad esempio, un housefly vicino il naso) gli occhi multipiattaforma e adattare a un punto vicino. Viceversa, se si visualizza un elemento all'infinito ottico (a partire approssimativamente a 6 minuti o più lontano per visione artificiale normale), comunicazione tra le righe degli occhi diventano paralleli e lenses degli occhi adattare all'infinito. 

In più azionata consente di visualizzare gli utenti potrà supportare sempre alla distanza focale dello schermo (per ottenere un'immagine ben strutturata), ma la convergenza con la distanza dell'oggetto di interesse (per ottenere una singola immagine). Quando gli utenti di gestire e convergono in distanze diverse, il collegamento naturale tra i due indicatori deve essere interrotto e questo può causare disturbo visual o fatica.

<br>

>[!VIDEO https://www.youtube.com/embed/-606oZKLa_s]

### <a name="guidance-for-holographic-devices"></a>Linee guida per i dispositivi holographic

Consente di visualizzare HoloLens corretti a una distanza ottica circa 2.0m lontano dall'utente. Di conseguenza, gli utenti devono sempre adattarsi quasi 2.0m per mantenere un'immagine chiara del dispositivo. Gli sviluppatori di App possono essere utili in cui eseguire la convergenza occhi degli utenti inserendo il contenuto e vntana profondità diversi. Disturbare dal conflitto vergence facilitazione può essere evitato o ridotta a icona, mantenendo il contenuto a cui gli utenti eseguire la convergenza di più vicino 2.0 m possibile (ad esempio in una scena con molta profondità, posizionare le aree di interesse vicino m 2.0 da parte dell'utente quando possibile). Quando il contenuto non può essere posizionato vicino 2.0 m, disturbare dal conflitto vergence ristorazione è più elevato quando sguardo dell'utente cambia e indietro tra le distanze diverse. In altre parole, è molto più a proprio agio esaminare fermo ologramma che rimane 50cm distanza rispetto al esaminare ologramma 50cm da subito che si sposta verso e lontano da te nel corso del tempo.

![Distanza ottima per il posizionamento vntana da parte dell'utente.](images/distanceguiderendering-950px.png)<br>
*Distanza ottima per il posizionamento vntana da parte dell'utente*

#### <a name="best-practices-for-hololens-1st-gen-and-hololens-2"></a>Procedure consigliate per HoloLens (dal 1 ° generazione) e 2 di HoloLens

Per la massima comodità, **zona ottima per la selezione host ologrammi è compreso tra 5m e m 1,25**. In ogni caso, le finestre di progettazione deve tentare in modo invisibile del contenuto di struttura per incoraggiare gli utenti di interagire 1 milione o più lontano rispetto al contenuto (ad esempio, regolare [le dimensioni del contenuto e i parametri di selezione host predefiniti](gaze-targeting.md)). 

Anche se il contenuto in alcuni casi potrebbe essere necessario deve essere visualizzato più vicini a 1 milione, è consigliabile evitare di presentazione che mai più di 40cm vntana. Di conseguenza, è consigliabile iniziare a **dissolvenza contenuto cm 40 e l'inserimento di un piano di ritaglio per il rendering in 30cm** per evitare qualsiasi più vicino a oggetti.

Gli oggetti che gestiscono lo spostamento in modo approfondito hanno più probabili rispetto agli oggetti fermo per produrre disturbo a causa del conflitto vergence facilitazione. In modo analogo, richiedendo agli utenti di passare rapidamente da quasi messa a fuoco e decisamente lo stato attivo (ad esempio, a causa di ologramma popup che richiede l'interazione diretta) può causare la fatica e disturbo visual. Pertanto **prestare particolare attenzione deve essere prelevato per ridurre al minimo la frequenza gli utenti sono: visualizzazione di contenuto che è in movimento in modo approfondito; o Cambio rapido lo stato attivo tra vntana vicino e lontano**. 

Quando si progetta il contenuto per il parametro direct (quasi) interazione in 2 HoloLens, oppure **in tutte le applicazioni in cui il contenuto deve essere poste più vicino a 1 milione, extra deve prestare attenzione per garantire il comfort utente**. Le probabilità di disturbo a causa del conflitto vergence facilitazione aumentano in modo esponenziale con riduzione distanza di visualizzazione. **Si consiglia di creare un "budget depth" per le App in base alla quantità di tempo è previsto che un utente di visualizzare il contenuto che si avvicina (< 1 milione) e lo spostamento in modo approfondito**. Un esempio consiste nell'evitare di inserire l'utente in tali situazioni più del 25% del tempo. Se viene superato il budget di profondità, è consigliabile un'attenta utente test per garantire che rimane un'esperienza pratica.

> [!NOTE]
> Altre indicazioni specifiche su 2 HoloLens [presto](index.md#news-and-notes).

### <a name="guidance-for-immersive-devices"></a>Linee guida per i dispositivi coinvolgenti

Per i dispositivi coinvolgenti, le linee guida e procedure consigliate per HoloLens comunque applicabili, ma i valori specifici per la zona del fattore di Comfort vengono spostati in base alla distanza focale sullo schermo. In generale, le distanze grazie a queste visualizzazioni sono tra milioni di 1,25-2,5 milioni. In caso di dubbi, evitare di rendering troppo vicino agli utenti di oggetti di interesse e provare invece a mantenere la maggior parte dei contenuti 1 milione o più lontani.

## <a name="interpupillary-distance-and-vertical-offset"></a>Distanza interpupillary e l'offset verticale

Quando la visualizzazione di contenuto digitale in head montato Visualizza (HMD), la posizione di occhi del Visualizzatore relazione alla posizione di visualizzazione di contenuti digitali è fondamentale. In particolare, entrambi distanza interpupillary ([IPD](https://en.wikipedia.org/wiki/Pupillary_distance)) e l'offset verticale (VO) sono importanti per la comoda visualizzazione di contenuti digitali in HMDs. 

IPD fa riferimento la distanza tra l'alunni o Data Center, di occhi di un individuo. VO fa riferimento a potenziali offset verticale del contenuto digitale visualizzato per ciascun occhio rispetto all'asse orizzontale di occhi del visualizzatore (in particolare, questo non è lo stesso come offset orizzontale o disparità binoculare). Non corrispondenza di uno o entrambi questi fattori a un singolo utente può peggiorare gli effetti di disturbo determinato dal conflitto vergence alloggio, ma è possibile anche causa disturbo quando viene ridotto al minimo dei conflitti di V-A (ad esempio, per il contenuto visualizzato nella finestra di m 2.0 focale distanza di HoloLens). 

### <a name="guidance-for-holographic-devices"></a>Linee guida per i dispositivi holographic

#### <a name="hololens-1st-gen"></a>HoloLens (dal 1 ° generazione)

Per HoloLens (dal 1 ° generazione), stimato e impostato durante dispositivo IPD [calibrazione](calibration.md). Per i nuovi utenti a un già impostato di dispositivo, è necessario eseguire calibrazione o IPD deve essere impostato manualmente. VO dipende interamente dal dispositivo adatta. In particolare, per ridurre al minimo VO, il dispositivo deve essere posizionato sul head di un utente in modo che le visualizzazioni sono di livello con l'asse del proprio gli occhi. 

#### <a name="hololens-2"></a>HoloLens 2

> [!NOTE]
> Altre indicazioni specifiche su 2 HoloLens [presto](index.md#news-and-notes).

### <a name="guidance-for-immersive-devices"></a>Linee guida per i dispositivi coinvolgenti

HMDs coinvolgenti di realtà mista di Windows non dispone di alcun calibrazione automatico per IPD o VO. IPD possono essere impostati manualmente nel software (nelle impostazioni del portale di realtà mista, vedere [calibrazione](calibration.md)), o alcuni HMDs dispone di un dispositivo di scorrimento meccanico che consente di regolare la spaziatura degli obiettivi a una posizione comoda (ad esempio, ovvero circa Consente di ricercare i IPD). 

## <a name="rendering-rates"></a>Tariffe per il rendering

Le App per realtà mista sono univoche poiché gli utenti possono spostare liberamente in tutto il mondo e interagire con il contenuto virtuale, ad esempio come se fossero oggetti reali. Per mantenere questo impressione, è fondamentale per il rendering vntana in modo che vengono visualizzati stabile del mondo e aggiungere un'animazione senza problemi. Il rendering in un [minimo di 60 fotogrammi al secondo (FPS)](understanding-performance-for-mixed-reality.md) consente di raggiungere tale obiettivo. Esistono alcuni dispositivi di realtà mista che supportano il rendering al framerate superiori a 60 FPS e per questi dispositivi è fortemente consigliabile eseguire il rendering nei framerate superiore per offrire un'esperienza utente ottimale.

**Approfondimenti**

Per disegnare vntana simile [risultano stabili nel mondo reale o virtuale](hologram-stability.md), le app devono eseguire il rendering di immagini dalla posizione dell'utente. Poiché il rendering delle immagini richiede tempo, HoloLens e altri dispositivi di realtà mista di Windows stimare in cui è head di un utente quando le immagini vengono visualizzate nelle visualizzazioni. Questo algoritmo di previsione è un'approssimazione. Hardware e gli algoritmi di realtà mista di Windows regolare dell'immagine di rendering per tenere conto di questa discrepanza tra la posizione di head stimata e l'effettiva posizione head. Questo processo consente l'immagine visualizzata all'utente vengono visualizzati come se ne sono stati eseguito il rendering dall'indirizzo corretto, l'aspetto vntana stabile. Gli aggiornamenti funzionano meglio per piccole modifiche nella posizione head, e non è completamente conto di alcune differenze di immagine di rendering, come quelli causati dal movimento parallasse.

**Per il rendering in un frequenza minima di 60 FPS, si sono due cose a rendere stabile vntana:**
1. Riduce l'aspetto di sussulto, che è caratterizzata da movimento non uniforme e immagini double. Judder movimento ologrammi più veloce e rendering più bassi tassi di sono associati più evidenti. Pertanto, l'impegno per mantenere sempre 60 FPS (o frequenza massima di rendering del dispositivo) consente di evitare sussulto per lo spostamento vntana.
2. Riducendo al minimo la latenza complessiva. In un modulo di gestione con un thread di gioco e un thread di rendering in esecuzione in lockstep, in esecuzione 30 fps può aggiungere 33.3ms della latenza aggiuntiva. Riducendo la latenza, ciò riduce l'errore di previsione e aumenta la stabilità di ologramma.

**Analisi delle prestazioni**

Sono disponibili numerosi strumenti che può essere utilizzato per valutare la frequenza dei fotogrammi dell'applicazione, ad esempio:
* GPUView
* Debugger grafica di Visual Studio
* Profiler incorporati in 3D motori, ad esempio il Debugger di Frame in Unity

## <a name="self-motion-and-user-locomotion"></a>Self-animati e locomotion utente

L'unica limitazione è la dimensione del tuo spazio fisico; Se si desidera consentire agli utenti di spostare ulteriormente nell'ambiente virtuale rispetto a quelli nei loro chat reali, è necessario implementare un form di movimento puramente virtuale. Tuttavia, sostenuto movimento virtuale che non corrisponde a un movimento reali e fisiche dell'utente spesso può indurre la malattia di movimento. Questo risultato è dovuto al fatto il *segnali visivi* per la modalità self-movimento dal *mondo virtuale* in conflitto con il [segnali vestibular](https://en.wikipedia.org/wiki/Vestibular_system) per Self-animati provenienti dal *realistici*.

Per fortuna, sono disponibili suggerimenti per l'implementazione locomotion utente che consentono di evitare il problema:
* Inserire sempre l'utente nel controllo della loro spostamenti; imprevisto automatico di movimento è particolarmente problematico
* Gli utenti sono molto sensibili alla direzione di gravità. Di conseguenza, i movimenti verticali non avviata dall'utente in particolare devono essere evitati.

### <a name="guidance-for-holographic-devices"></a>Linee guida per i dispositivi holographic

Un metodo per consentire all'utente di spostare in un'altra posizione in un ambiente virtuale di grandi dimensioni consiste nel dare l'impressione che spostano un piccolo oggetto nella scena. È possibile ottenere questo risultato come indicato di seguito:
   1. Fornire un'interfaccia in cui l'utente può selezionare un punto nell'ambiente virtuale in cui si desidera spostare.
   2. Dopo la selezione, compattare il rendering di scene fino a un disco tutto sul punto desiderato.
   3. Mantenendo il campione selezionato, consente all'utente di spostarla come se fosse un piccolo oggetto. L'utente può quindi spostare la selezione vicino a loro piedi.
   4. Dopo la deselezione, riprendere il rendering dell'intera scena.

### <a name="guidance-for-immersive-devices"></a>Linee guida per i dispositivi coinvolgenti

L'approccio holographic dispositivo precedente non funziona anche in un dispositivo immersiva perché è necessaria l'app per eseguire il rendering di un grande void nero o in un altro ambiente predefinito durante lo spostamento del "disco". Questo trattamento dovuta a di uno senso di full immersion. Un espediente per locomotion utente in un visore VR immersivi è l'approccio di "blink". Questa implementazione consente all'utente di controllare i movimenti e offre una breve occhiata dello spostamento dei, ma rende così brevi è meno probabile sentirsi disorientamento che l'utente da virtuale esclusivamente di movimento automatico:
   1. Fornire un'interfaccia in cui l'utente può selezionare un punto nell'ambiente virtuale in cui si desidera spostare.
   2. Dopo la selezione, iniziare un movimento estremamente rapido simulato (100 m/sec) verso tale posizione durante la rapidamente dissolvenza in uscita il rendering.
   3. Dissolvenza nuovamente il rendering dopo il completamento della conversione.

## <a name="heads-up-displays"></a>Consente di visualizzare Heads-up

Nel primo-persona-tiro a segno videogames, Heads-up display (HUDs) presentare in modo permanente informazioni quali la salute dei giocatori, mini mappe e degli inventari direttamente sullo schermo. HUDs funziona bene per mantenere il giocatore informato senza malintenzionato sull'esperienza di gioco. Nelle esperienze di realtà mista, HUDs hanno la possibilità di causare disturbo significativo e devono essere adattati per il contesto più coinvolgente. In particolare, HUDs rigidamente bloccati all'orientamento head dell'utente in genere producono disturbo. Se un'app richiede un HUD, è consigliabile *corpo* blocco anziché il blocco head. Quest ' ultimo può essere implementato come un set di consente di visualizzare immediatamente tradurre con l'utente, ma non esegue alcuna rotazione con head dell'utente fino a quando non viene raggiunta una soglia di rotazione. Una volta che la rotazione viene ottenuta, HUD può modificare l'orientamento per presentare le informazioni all'interno di individuazioni dell'utente. Implementazione 1:1 HUD rotazione e traslazione rispetto all'inizio il suo raggio deve essere sempre evitata.

## <a name="text-legibility"></a>Migliorare la leggibilità testo

Migliorare la leggibilità ottimale testo consente di ridurre agli occhi e mantenere la comodità per l'utente, in particolare negli scenari che richiedono agli utenti di leggere in un HMD o applicazioni. Migliorare la leggibilità testo dipende da diversi fattori tra cui varie le proprietà di visualizzazione (ad esempio, densità in pixel, luminosità, contrasto elevato), proprietà lens (ad esempio, cromatica cromatiche) e le proprietà del tipo di carattere o testo (ad esempio, il tipo di carattere specifico le caratteristiche come spessore, grazie, colore del tipo di carattere, colore di sfondo e così via).  

In generale, è consigliabile testare le applicazioni specifiche per migliorare la leggibilità e rendendo le dimensioni dei caratteri grande quanto è fattibile per un'esperienza pratica. Di seguito sono disponibili linee guida generali come punto di partenza per lo sviluppo. Si noti che tutte le dimensioni del carattere vengono inserite in gradi del [angolo visual](https://en.wikipedia.org/wiki/Visual_angle) anziché fisica di dimensioni specifiche, che fornisce indicazioni per qualsiasi distanza all'interno dell'area di posizionamento ottimale ologrammi perché lo conteggia le dimensioni del il testo e la distanza che viene visualizzato nel Visualizzatore. 

### <a name="guidance-for-holographic-devices"></a>Linee guida per i dispositivi holographic

Per i dispositivi holographic, il rendering del testo scuro/nero su sfondo bianco/leggero offre il contrasto più coerenza perché lo sfondo sarà nasconde i colori del mondo reale dietro il rendering le interferenze. Il rendering del testo bianco/luce su uno sfondo scuro/nero consente più di ambiente reale venga visualizzato, che può interferire con la leggibilità di testo. 

#### <a name="hololens-1st-gen"></a>HoloLens (dal 1 ° generazione)

Le dimensioni minime del carattere verticali leggibile sono circa 0.35° e una dimensione del carattere verticali familiarità è almeno circa 0,5 ° per la lettura del contenuto presentata all'utente a una distanza di 2 minuti. 

#### <a name="hololens-2"></a>HoloLens 2

> [!NOTE]
> Altre indicazioni specifiche su 2 HoloLens [presto](index.md#news-and-notes).

### <a name="guidance-for-immersive-devices"></a>Linee guida per i dispositivi coinvolgenti

Dispositivi coinvolgenti in genere avere contrasto in a causa dell'occlusione completa dell'ambiente esterno, ma minore densità di pixel effettivi in parte a causa l'ingrandimento degli obiettivi davanti verrà visualizzato il. 

Per HMDs coinvolgenti di realtà mista di Windows, le dimensioni minime del carattere verticali leggibile sono circa 0,7-0.9 ° e una dimensione del carattere verticali familiarità è circa 1.0° per la lettura del contenuto presentata all'utente a una distanza di 2 minuti.

## <a name="gaze-direction"></a>Direzione sguardo

Per evitare per occhi e schiena contenuto deve essere progettato in modo da evitare spostamenti eccessivo sotto controllo e il collo.
* **Evitare** sguardo angoli più di 10 gradi sopra all'orizzonte (spostamento verticale)
* **Evitare** sguardo angoli più di 60 gradi sotto all'orizzonte (spostamento verticale)
* **Evitare** rotazioni collo più di 45 gradi fuori centro (spostamento orizzontale)

L'angolo di sguardo ottimale (sospeso) viene considerato tra 10 e 20 gradi sotto orizzontale, come intestazione tende a inclinare verso il basso leggermente, in particolare durante le attività.

![Consentito campo visualizzazione () in base a intervallo collo di movimento](images/optimal-field-of-view-2-750px.png)<br>
*Consentito campo visualizzazione () in base a intervallo collo di movimento*

## <a name="arm-positions"></a>Posizioni di Azure Resource Manager

Quando gli utenti dovrebbero tenere una mano generata per tutta la durata di un'esperienza, può accumulare la fatica di tutto le competenze necessarie. Può anche essere fatiguing per richiedere all'utente di eseguire ripetutamente air toccare i movimenti per periodi prolungati. È quindi consigliabile da esperienze per evitare che richiede l'input costante, ripetute movimento. Questo obiettivo può essere ottenuto che incorpora le interruzioni di breve o offre una combinazione di gesti e riconoscimento vocale per interagire con l'app di input.

## <a name="see-also"></a>Vedere anche
* [Sguardo](gaze.md)
* [Stabilità ologrammi](hologram-stability.md)
* [Nozioni fondamentali di interazione](interaction-fundamentals.md)
* [Frame holographic](holographic-frame.md)
* [Calibrazione](calibration.md)

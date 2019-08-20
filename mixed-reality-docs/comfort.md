---
title: Comfort
description: Durante la visualizzazione naturale, il sistema visuale umano si basa su più origini di informazioni o "suggerimenti" per interpretare le forme 3D e la posizione relativa degli oggetti.
author: erickjpaul
ms.author: erpau
ms.date: 04/5/2019
ms.topic: article
keywords: Realtà mista, progettazione, comodità, HoloLens 2, HoloLens (1a generazione)
ms.openlocfilehash: e3a78e9a990d207b19b287e1897897a5d6dee3ca
ms.sourcegitcommit: 150d258a23130026c8792da383a3993657841fb4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67024439"
---
# <a name="comfort"></a>Comfort

Durante la visualizzazione naturale, il sistema visuale umano si basa su più origini di informazioni o "suggerimenti" per interpretare le forme 3D e le posizioni relative degli oggetti. Alcuni suggerimenti si basano solo su un singolo occhio (indicatori monoculare), tra cui [prospettiva lineare](https://en.wikipedia.org/wiki/Perspective_(graphical)), [dimensioni note](https://en.wikipedia.org/wiki/Size#Perception_of_size), occlusione, [sfocatura della profondità del campo](https://en.wikipedia.org/wiki/Depth_of_field)e [alloggio](https://en.wikipedia.org/wiki/Accommodation_(eye)). Altre indicazioni si basano su entrambi gli occhi (suggerimenti binocoli) e includono [vergence](https://en.wikipedia.org/wiki/Vergence) (essenzialmente le rotazioni relative degli occhi richiesti per esaminare un oggetto) e la disparità [binoculare](https://en.wikipedia.org/wiki/Stereopsis) (il modello di differenze tra le proiezioni della scena nel indietro dei due occhi). Per garantire la massima comodità negli schermi montati, è importante per i progettisti e gli sviluppatori creare e presentare contenuti in modo da simulare il funzionamento di questi suggerimenti nel mondo naturale. Dal punto di vista fisico, è anche importante progettare contenuto che non richiede movimenti faticosi del collo o delle braccia. In questo articolo verranno esaminate le considerazioni principali da tenere in considerazione per raggiungere questi obiettivi.

## <a name="vergence-accommodation-conflict"></a>Vergence-conflitto di alloggi

Per visualizzare gli oggetti in modo chiaro, [è necessario che](https://en.wikipedia.org/wiki/Accommodation_%28eye%29)gli utenti soddisfino o modifichino lo stato attivo degli occhi alla distanza dell'oggetto. Allo stesso tempo, la rotazione di entrambi gli occhi deve [convergere](https://en.wikipedia.org/wiki/Convergence_(eye)) alla distanza dell'oggetto per evitare di visualizzare immagini doppie. Nella visualizzazione naturale, vergence e accommodation sono collegati. Quando si visualizza un elemento vicino, ad esempio un Mosca vicino al naso, gli occhi si incrociano e si adattano a un punto vicino. Viceversa, se si visualizza un elemento a infinito ottico (approssimativamente da 6 a 6 o più per la visione normale), le linee visive degli occhi diventano parallele e le lenti degli occhi sono adatte all'infinito. 

Nella maggior parte dei casi, gli utenti vengono sempre posizionati sulla distanza focale dello schermo (per ottenere un'immagine nitida), ma convergeranno sulla distanza dell'oggetto di interesse (per ottenere una singola immagine). Quando gli utenti sono in grado di adattarsi a diverse distanze, il collegamento naturale tra i due segnali deve essere danneggiato e questo può causare fastidio visivi o affaticarsi.

<br>

>[!VIDEO https://www.youtube.com/embed/-606oZKLa_s]

### <a name="guidance-for-holographic-devices"></a>Linee guida per i dispositivi olografici

Le visualizzazioni di HoloLens sono fisse a distanza ottica circa 2,0 m dall'utente. Pertanto, gli utenti devono sempre adattarsi a circa 2,0 m per mantenere un'immagine chiara nel dispositivo. Gli sviluppatori di app possono guidare la convergenza degli occhi degli utenti inserendo contenuto e ologrammi a diverse profondità. Il disagio del conflitto vergence-accommodation può essere evitato o ridotto a icona mantenendo il contenuto a cui gli utenti si confluiscono più vicino a 2,0 m come possibile (ad esempio, in una scena con molta profondità, inserire le aree di interesse vicino a 2,0 m dall'utente quando possibile). Quando non è possibile posizionare il contenuto vicino a 2,0 m, il disagio del conflitto vergence-Accommodation è maggiore quando lo sguardo dell'utente passa da una distanza all'altra. In altre parole, è molto più semplice esaminare un ologramma stazionario che rimanga a 50 centimetri rispetto a un ologramma che si sposta verso e fuori dal tempo.

![Distanza ottimale per inserire gli ologrammi dall'utente.](images/distanceguiderendering-950px.png)<br>
*Distanza ottimale per inserire gli ologrammi dall'utente*

### <a name="best-practices-for-hololens-1st-gen-and-hololens-2"></a>Procedure consigliate per HoloLens (1a generazione) e HoloLens 2

Per la massima comodità, **la zona ottimale per la posizione degli ologrammi è compresa tra 1.25 m e 5m**. In ogni caso, le finestre di progettazione devono tentare di strutturare gli scenari di contenuto per incoraggiare gli utenti a interagire tra 1 milione o più lontano dal contenuto (ad esempio, modificare le [dimensioni del contenuto e i parametri di posizionamento predefiniti](gaze-targeting.md)). 

Sebbene sia talvolta necessario che il contenuto venga visualizzato più vicino a 1 milione, è consigliabile evitare di presentare ologrammi più vicini a 40cm. È quindi consigliabile iniziare a **dissolvere il contenuto in 40cm e posizionare un piano di ritaglio di rendering a 30cm** per evitare gli oggetti più vicini.

Gli oggetti che si spostano in profondità sono più probabili degli oggetti stazionari per produrre disagio a causa del conflitto vergence-accommodation. Allo stesso modo, richiedere agli utenti di passare rapidamente tra lo stato attivo e lo stato attivo, ad esempio a causa di un ologramma popup che richiede l'interazione diretta, può causare disagio e fatica visivi. È pertanto **necessario prestare particolare attenzione per ridurre al minimo la frequenza con cui gli utenti sono in grado di visualizzare i contenuti che si spostano in profondità; o di passare rapidamente lo stato attivo tra gli ologrammi vicini e lontani**. 

### <a name="additional-considerations-for-hololens-2-and-near-interaction-distances"></a>Considerazioni aggiuntive per le distanze HoloLens 2 e near Interaction

Quando si progettano contenuti per l'interazione diretta (near) in HoloLens 2 o **in tutte le applicazioni in cui il contenuto deve essere più vicino a 1 milione, è necessario prestare particolare attenzione per garantire la comodità degli utenti**. La probabilità di disagio a causa del conflitto di vergence-accommodation aumenta in modo esponenziale con una riduzione della distanza di visualizzazione. Inoltre, gli utenti possono riscontrare un aumento della bluriness quando visualizzano il contenuto in prossimità di interazioni, quindi è consigliabile testare il contenuto sottoposto a rendering sia all'interno della zona della posizione ottimale dell'ologramma, sia più vicino (inferiore a 1,0 m al piano di ritaglio) a Assicurarsi che rimanga chiaro e comodo da visualizzare. 

**Si consiglia di creare un "budget di profondità" per le app in base al periodo di tempo in cui un utente deve visualizzare il contenuto vicino (meno di 1,0 m) e avanzare in profondità**. Un esempio è evitare di inserire l'utente in tali situazioni più del 25% del tempo. Se viene superato il budget di profondità, si consiglia un attento test utente per assicurarsi che rimanga un'esperienza confortevole. 

In generale, si consiglia anche un attento test per garantire che i requisiti di interazione (ad esempio velocità di spostamento, raggiungibilità e così via) rimangano comodi per gli utenti. 


### <a name="guidance-for-immersive-devices"></a>Linee guida per i dispositivi immersivi

Per i dispositivi immersivi, vengono comunque applicate le linee guida e le procedure consigliate per HoloLens, ma i valori specifici per la zona di comfort vengono spostati a seconda della distanza focale alla visualizzazione. In generale, le distanze focali per questi schermi sono comprese tra 1.25 m-2,5 m. In caso di dubbi, evitare di eseguire il rendering di oggetti di interesse troppo vicino agli utenti e provare invece a ridurre la maggior parte del contenuto di 1 milione o più lontano.

## <a name="interpupillary-distance-and-vertical-offset"></a>Distanza interpupillare e offset verticale

Quando si Visualizza il contenuto digitale su schermi montati a capo (HMD), la posizione degli occhi di un visualizzatore rispetto alla posizione di visualizzazione del contenuto digitale è fondamentale. In particolare, sia la distanza interpupillare ([dpi](https://en.wikipedia.org/wiki/Pupillary_distance)) sia l'offset verticale (vo) sono importanti per una visualizzazione confortevole del contenuto digitale in HMDS. 

Il valore di dpi si riferisce alla distanza tra gli occhi degli alunni o i centri degli occhi di un utente. VO si riferisce al potenziale offset verticale del contenuto digitale visualizzato a ogni occhio rispetto all'asse orizzontale degli occhi del Visualizzatore (in particolare, non corrisponde all'offset orizzontale o alla disparità binoculare). La corrispondenza errata di uno o entrambi i fattori per un singolo utente può peggiorare gli effetti del disagio causato da un conflitto di vergence-accommodation, ma può anche causare disagio quando il conflitto V-A è ridotto a icona (ad esempio, per il contenuto visualizzato alla focale di 2,0 m distanza del HoloLens). 

### <a name="guidance-for-holographic-devices"></a>Linee guida per i dispositivi olografici

#### <a name="hololens-1st-gen"></a>HoloLens (prima generazione)

Per HoloLens (1a generazione), il dpi viene stimato e impostato durante la [calibrazione](calibration.md)del dispositivo. Per i nuovi utenti di un dispositivo già configurato, è necessario eseguire la taratura o impostare manualmente. VO dipende interamente dalla idoneità del dispositivo. In particolare, per ridurre il valore di VO, è necessario che il dispositivo si trovi a capo di un utente in modo che gli schermi siano a livello dell'asse degli occhi. 

#### <a name="hololens-2"></a>HoloLens 2

Per HoloLens 2, il dpi viene stimato e impostato durante la [calibrazione](calibration.md)degli occhi e dei dispositivi. Per i nuovi utenti di un dispositivo già configurato, è necessario eseguire la taratura per assicurarsi che la configurazione DPI sia impostata correttamente. VO viene contabilizzato automaticamente in HoloLens 2. 

### <a name="guidance-for-immersive-devices"></a>Linee guida per i dispositivi immersivi

I HMDs di realtà mista di Windows sono privi di calibrazione automatica per dpi o VO. È possibile impostare il valore DIP manualmente nel software (in impostazioni del portale di realtà mista, vedere [calibrazione](calibration.md)) o alcuni HMDS hanno un dispositivo di scorrimento meccanico che consente all'utente di adattare la spaziatura delle lenti a una posizione comoda, ovvero che approssimativamente corrisponde al relativo valore dpi. 

## <a name="rendering-rates"></a>Velocità di rendering

Le app di realtà miste sono univoche perché gli utenti possono muoversi liberamente nel mondo e interagire con contenuto virtuale come se fossero oggetti reali. Per mantenere questa impressione, è fondamentale eseguire il rendering degli ologrammi in modo che risultino stabili in tutto il mondo e animano senza problemi. Il rendering con un [minimo di 60 fotogrammi al secondo (fps) consente di](understanding-performance-for-mixed-reality.md) raggiungere questo obiettivo. Ci sono alcuni dispositivi di realtà mista che supportano il rendering in framerate superiori a 60 FPS e per questi dispositivi è consigliabile eseguire il rendering con framerate più elevati per offrire un'esperienza utente ottimale.

**Approfondimenti**

Per disegnare gli ologrammi in modo [che siano stabili nel mondo reale o virtuale](hologram-stability.md), le app devono eseguire il rendering delle immagini dalla posizione dell'utente. Poiché il rendering delle immagini richiede tempo, HoloLens e altri dispositivi di realtà mista Windows stimano dove si troverà la testa di un utente quando le immagini vengono visualizzate nella visualizzazione. Questo algoritmo di stima è un'approssimazione. Algoritmi di realtà mista di Windows e hardware consentono di regolare l'immagine di rendering per tenere conto della discrepanza tra la posizione della testa stimata e quella effettiva. Questo processo rende l'immagine visualizzata dall'utente come se fosse stata sottoposta a rendering dalla posizione corretta e gli ologrammi si ritengono stabili. Gli aggiornamenti funzionano meglio per le piccole modifiche nella posizione Head e non possono tenere conto completamente di alcune differenze di immagine sottoposte a rendering, come quelle causate da Motion-parallasse.

**Eseguendo il rendering con un framerate minimo di 60 FPS, si eseguono due operazioni per rendere gli ologrammi stabili:**
1. Riduzione dell'aspetto di judder, caratterizzato da immagini di movimento e doppie non uniformi. Un movimento dell'ologramma più veloce e frequenze di rendering inferiori sono associate a judder più pronunciato. Pertanto, il tentativo di mantenere sempre 60 FPS (o la velocità di rendering massima del dispositivo) consentirà di evitare il tremolio degli ologrammi.
2. Riduzione della latenza complessiva. In un motore con un thread di gioco e un thread di rendering in esecuzione in contemporanea, l'esecuzione a 30 fps può aggiungere 33,3 ms di latenza aggiuntiva. Riducendo la latenza, questo riduce l'errore di stima e aumenta la stabilità degli ologrammi.

**Analisi delle prestazioni**

Sono disponibili diversi strumenti che è possibile usare per eseguire il benchmark della frequenza dei fotogrammi dell'applicazione, ad esempio:
* GPUView
* Debugger grafica di Visual Studio
* Profiler incorporati in motori 3D come il debugger frame in Unity

## <a name="self-motion-and-user-locomotion"></a>Auto-Motion e locomozione utente

L'unica limitazione è la dimensione dello spazio fisico. Se si desidera consentire agli utenti di spostarsi più a fondo nell'ambiente virtuale rispetto a quanto possibile nelle loro sale reali, è necessario implementare una forma di movimento puramente virtuale. Tuttavia, un movimento virtuale sostenuto che non corrisponde al movimento fisico dell'utente può spesso provocare la malattia in movimento. Questo risultato è dovuto ai *segnali visivi* per il movimento autonomo dal *mondo virtuale* in conflitto con i [segnali vestibolari](https://en.wikipedia.org/wiki/Vestibular_system) per le automotion provenienti dal *mondo reale*.

Fortunatamente, sono disponibili suggerimenti per l'implementazione di locomozione utente che può contribuire a evitare il problema:
* Inserire sempre l'utente nel controllo dei movimenti; il self-Motion imprevisto è particolarmente problematico
* Gli uomini sono molto sensibili alla direzione di gravità. Pertanto, è consigliabile evitare movimenti verticali non avviati dall'utente, in particolare.

### <a name="guidance-for-holographic-devices"></a>Linee guida per i dispositivi olografici

Un metodo per consentire all'utente di spostarsi in un'altra posizione in un ambiente virtuale di grandi dimensioni consiste nel dare l'impressione che sposti un piccolo oggetto nella scena. Questo effetto può essere ottenuto come segue:
   1. Fornire un'interfaccia in cui l'utente può selezionare una posizione nell'ambiente virtuale in cui si desidera spostarsi.
   2. Al momento della selezione, compattare il rendering della scena su un disco intorno al punto desiderato.
   3. Mantenendo il punto selezionato, consentire all'utente di spostarlo come se fosse un oggetto di piccole dimensioni. L'utente può quindi spostare la selezione vicino ai piedi.
   4. Al momento della deselezione, riprendere il rendering dell'intera scena.

### <a name="guidance-for-immersive-devices"></a>Linee guida per i dispositivi immersivi

L'approccio precedente per i dispositivi olografici non funziona anche in un dispositivo immersivo perché richiede che l'app esegua il rendering di un grande void nero o di un altro ambiente predefinito durante lo stato di trasferimento del disco. Questo trattamento interrompe il senso di un'immersione. Uno stratagemma per la locomozione dell'utente in un headset immersivo è l'approccio "Blink". Questa implementazione consente all'utente di controllare il proprio movimento e offre una breve impressione di spostamento, ma rende così breve che l'utente è meno incline a essere disorientato da un self-Motion puramente virtuale:
   1. Fornire un'interfaccia in cui l'utente può selezionare una posizione nell'ambiente virtuale in cui si desidera spostarsi.
   2. Al momento della selezione, iniziare un movimento simulato (100 m/s) molto rapido verso tale posizione, mentre si dissolve rapidamente il rendering.
   3. Dissolve il rendering dopo aver terminato la traduzione.

## <a name="heads-up-displays"></a>Visualizzazione delle intestazioni

Nei videogiochi per i primi utenti, le intestazioni di visualizzazione (HUDs) presentano in modo permanente informazioni come l'integrità dei giocatori, le mini-mappe e gli inventari direttamente sullo schermo. HUDs funziona bene per fare in modo che il lettore venga informato senza intrusione sull'esperienza di gioco. Nelle esperienze di realtà miste, HUDs possono causare fastidio significativi e devono essere adattati al contesto più immersivo. In particolare, è probabile che i HUDs bloccati rigidamente all'orientamento Head dell'utente possano produrre disagio. Se un'app richiede un HUD, si consiglia il blocco del *corpo* anziché il blocco Head. Questo trattamento può essere implementato come un set di visualizzazioni che vengono immediatamente convertite con l'utente, ma non vengono ruotate con l'intestazione dell'utente finché non viene raggiunta una soglia di rotazione. Una volta eseguita la rotazione, HUD può riorientarsi per presentare le informazioni nel campo di visualizzazione dell'utente. L'implementazione della rotazione e della traduzione di 1:1 HUD rispetto ai movimenti Head dell'utente deve essere sempre evitata.

## <a name="text-legibility"></a>Leggibilità del testo

La leggibilità ottimale del testo può aiutare a ridurre gli occhi e a mantenere la comodità degli utenti, soprattutto in applicazioni o scenari che richiedono agli utenti di leggere in un HMD. La leggibilità del testo dipende da diversi fattori, tra cui varie proprietà di visualizzazione (ad esempio, densità dei pixel, luminosità, contrasto), proprietà dell'obiettivo (ad esempio, aberrazione cromatica) e proprietà Text/Font, ad esempio il tipo di carattere specifico caratteristiche come il peso, la spaziatura, i Serif e così via, il colore del tipo di carattere, il colore dello sfondo.  

In generale, si consiglia di testare le applicazioni specifiche per la leggibilità e le dimensioni dei tipi di carattere per un'esperienza ottimale. Di seguito vengono fornite indicazioni generali come punto di partenza per lo sviluppo. Si noti che tutte le dimensioni dei tipi di carattere vengono segnalate in gradi di [angolo visivo](https://en.wikipedia.org/wiki/Visual_angle) invece che in dimensioni fisiche specifiche, che forniscono indicazioni per qualsiasi distanza all'interno della zona del posizionamento ottimale degli ologrammi, in quanto consente di tenere conto sia della dimensione del testo sia della distanza viene visualizzato nel visualizzatore. 

Per indicazioni più dettagliate, vedere le pagine [tipografia](typography.md) e [testo in Unity](text-in-unity.md).

### <a name="guidance-for-holographic-devices"></a>Linee guida per i dispositivi olografici

Per i dispositivi olografici, il rendering del testo nero/scuro in uno sfondo bianco/chiaro fornisce il rapporto di contrasto più coerente perché lo sfondo occludere le interferenze dal mondo reale dietro il rendering. Il rendering di testo bianco/chiaro su uno sfondo nero/scuro consente la visualizzazione di più ambienti reali, che potrebbero interferire con la leggibilità del testo. 

#### <a name="hololens-1st-gen"></a>HoloLens (prima generazione)

Le dimensioni minime del carattere leggibili (misurazione dalla linea di base del tipo di carattere a ascendente) sono pari a circa 0,35 ° e le dimensioni del carattere sono pari almeno circa 0,5 ° per la lettura del contenuto presentato a una distanza di 2m all'utente. 

#### <a name="hololens-2"></a>HoloLens 2

La dimensione minima del carattere leggibile (misurazione dalla linea di base del tipo di carattere a ascendente) è almeno approssimativamente: 
   - 0.4 °-0,5 ° a 45 cm (distanza di manipolazione diretta) 
   - 0,35 °-0,4 ° a 2,0 m
   
La dimensione del carattere perfettamente leggibile (misurazione dalla linea di base del tipo di carattere a ascendente) è almeno approssimativamente: 
   - 0,65 °-0,8 ° a 45 cm (distanza di manipolazione diretta)
   - 0.6 °-0,75 ° a 2,0 m

Si noti che le dimensioni del carattere devono essere leggermente più grandi per il testo a distanza di manipolazione diretta a causa del conflitto vergence-accommodation descritto in precedenza (gli occhi degli utenti sono in grado di ospitare a una distanza di 2,0 m sulla visualizzazione HoloLens, di conseguenza il rendering del contenuto in, ad esempio, 45 cm può sembrare più sfocata agli utenti. 

### <a name="guidance-for-immersive-devices"></a>Linee guida per i dispositivi immersivi

I dispositivi immersivi in genere presentano rapporti di contrasto più elevati a causa dell'occlusione completa dell'ambiente esterno, ma in parte possono avere una minore densità di pixel effettiva, a causa dell'ingrandimento degli obiettivi davanti alle visualizzazioni. 

Per HMDs di realtà mista di Windows, le dimensioni minime del carattere leggibile (misurazione dalla linea di base del tipo di carattere a ascendente) sono approssimativamente 0.7-0.9 ° e una dimensione verticale comoda è approssimativamente 1,0 ° per la lettura del contenuto presentato a una distanza di 2m al utente.

## <a name="gaze-direction"></a>Direzione dello sguardo

Per evitare che il contenuto di un ceppo di occhio e collo debba essere progettato in modo da evitare movimenti di occhi e collo eccessivi.
* **Evitare** gli angoli degli sguardi più di 10 gradi sopra l'orizzonte (spostamento verticale)
* **Evitare** gli angoli degli sguardi più di 60 gradi sotto l'orizzonte (spostamento verticale)
* **Evitare** le rotazioni del collo più di 45 gradi fuori dal centro (spostamento orizzontale)

L'angolo di sguardo ottimale (in appoggio) viene considerato compreso tra 10-20 gradi al di sotto dell'orizzontale, in quanto la testa tende a inclinarsi leggermente verso il basso, soprattutto durante le attività.

![Campo di visualizzazione consentito (FOV) determinato dall'intervallo di movimento del collo](images/optimal-field-of-view-2-750px.png)<br>
*Campo di visualizzazione consentito (FOV) determinato dall'intervallo di movimento del collo*

## <a name="arm-positions"></a>Posizioni ARM

La fatica muscolare può accumularsi quando si prevede che gli utenti mantengano una mano nel corso della durata dell'esperienza. Può anche essere faticoso richiedere all'utente di effettuare ripetutamente movimenti di tocco aereo nelle durate lunghe. È pertanto consigliabile evitare di richiedere input di movimenti ripetuti e costanti. Questo obiettivo può essere eseguito incorporando brevi interruzioni o offrendo una combinazione di movimento e input vocale per interagire con l'app.

## <a name="see-also"></a>Vedere anche
* [Sguardo fisso](gaze.md)
* [Stabilità degli ologrammi](hologram-stability.md)
* [Interazioni istintive](interaction-fundamentals.md)
* [Frame olografico](holographic-frame.md)
* [Calibrazione](calibration.md)

---
title: Case Study-HoloTour
description: HoloTour per Microsoft HoloLens fornisce tour personali immersivi 3D di posizioni iconiche in tutto il mondo. In questo case study verrà illustrato il processo di acquisizione e creazione del contenuto utilizzato per HoloTour.
author: dannyaskew
ms.author: daaske
ms.date: 03/21/2018
ms.topic: article
keywords: HoloTour, HoloLens, realtà mista di Windows
ms.openlocfilehash: 59c3dffd48009aa792643ea27b59f8f6f85b64d7
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278189"
---
# <a name="case-study---holotour"></a>Case Study-HoloTour

HoloTour per Microsoft HoloLens fornisce tour personali immersivi 3D di posizioni iconiche in tutto il mondo. I progettisti, gli artisti, i produttori, i progettisti e gli sviluppatori che lavorano su questo progetto hanno scoperto che la creazione di un rendering 3D in modo convincente di una posizione nota accetta una combinazione univoca di creazioni guidate creative e tecnologiche. In questo case study verrà illustrato il processo di acquisizione e creazione del contenuto utilizzato per HoloTour.

## <a name="the-tech"></a>Il Tech

Con HoloTour, abbiamo voluto consentire agli utenti di visitare alcune delle destinazioni più straordinarie del mondo, come le [rovine di Machu Picchu](https://en.wikipedia.org/wiki/Machu_Picchu) in Perù o il giorno moderno [Piazza Navona](https://en.wikipedia.org/wiki/Piazza_Navona) in Italia, direttamente dalle proprie chat room. Il nostro team ha fatto in modo che l'obiettivo di HoloTour sia quello di essere veramente in realtà. L'esperienza necessaria per non solo immagini o video. Sfruttando la tecnologia di visualizzazione, rilevamento e audio univoca di HoloLens, abbiamo creduto che avessimo potuto trasmetterti virtualmente in un'altra posizione. Sarebbe necessario acquisire i punti di vista, i suoni e la geometria tridimensionale di ogni località visitata e quindi ricrearla all'interno dell'app.

A tale scopo, era necessario un rig della fotocamera 360 ° con acquisizione audio direzionale. È stato necessario acquisire una risoluzione estremamente elevata, in modo che il metraggio risulti nitido quando viene riprodotto in una HoloLens e le fotocamere devono essere posizionate vicino per ridurre al minimo gli artefatti. È stata voluta una copertura sferica completa, non solo lungo l'orizzonte, ma anche sopra e sotto. Il rig doveva anche essere portabile in modo da poterlo usare in tutto il mondo. Sono state valutate le opzioni disponibili e sono state realizzate che non sono state sufficientemente valide per realizzare la nostra visione, a causa della risoluzione, dei costi o delle dimensioni. Se non è stato possibile trovare un rig della fotocamera che soddisfi le proprie esigenze, è necessario crearne uno.

### <a name="building-the-rig"></a>Creazione del rig

La prima versione, fatta da cartoni, Velcro, Duct Tape e 14 fotocamere GoPro, era una sorta di MacGyver. Dopo aver esaminato tutti gli elementi, dalle soluzioni di basso livello ai rig prodotti personalizzati, le fotocamere GoPro erano alla fine l'opzione migliore per Microsoft perché erano piccole, convenienti e avevano un archivio di memoria di facile utilizzo. Il fattore di forma piccolo è stato particolarmente importante perché ci ha consentito di collocare le fotocamere in modo abbastanza vicino, minore è la distanza tra le fotocamere, minore sarà la distanza degli artefatti. La nostra disposizione esclusiva per la fotocamera ci ha consentito di ottenere la copertura completa della sfera, *oltre* a una sovrapposizione sufficiente per allineare in modo intelligente le fotocamere e smussare alcuni artefatti durante il processo di Unione.

Sfruttare le funzionalità [audio spaziali](spatial-sound.md) in HoloLens è essenziale per la creazione di un'esperienza immersiva convincente. È stato usato un array a quattro microfoni situato sotto le fotocamere sul treppiede, che consente di acquisire un suono dalla posizione della nostra fotocamera in quattro direzioni, dandoci informazioni sufficienti per creare suoni spaziali nelle nostre scene.

![Il nostro rig della fotocamera 360 ° configurato per la cinematografia all'esterno del Pantheon.](images/camera-pantheon-200px.png)

Il nostro rig della fotocamera 360 ° configurato per la cinematografia all'esterno del Pantheon. 


Abbiamo testato il nostro rig casalingo portandolo alla cresta dei serpenti in prossimità di Seattle, acquisendo lo scenario nella parte superiore dell'escursione. Il risultato, sebbene significativamente meno lucido rispetto a quello visualizzato in HoloTour oggi, ci ha confidato che la progettazione di un rig era abbastanza efficace da garantire che ci si trovi davvero.

Il nostro rig è stato aggiornato da Velcro e cartonato a una fotocamera a stampa 3D e hanno acquistato batterie esterne per le fotocamere GoPro per semplificare la gestione della batteria. È stato quindi testato un test più esteso, che è stato girato fino a San Francisco per creare una presentazione in miniatura della costa della città e del Golden Gate Bridge iconico. Questo rig della fotocamera è quello che abbiamo usato per la maggior parte delle nostre acquisizioni dei percorsi visitati in HoloTour.

![Il 360 ° rig della fotocamera che si sta filmando in Machu Picchu.](images/camera-machu-pichu-500px.png)

Il 360 ° rig della fotocamera che si sta filmando in Machu Picchu. 

## <a name="behind-the-scenes"></a>Dietro le quinte

Prima di filmarlo, era necessario scoprire quali sono le località da includere nella nostra presentazione virtuale. Roma è stata la prima sede per la spedizione e volevamo ottenerla, quindi abbiamo deciso di eseguire un viaggio di scouting in anticipo. Abbiamo inviato un team di sei persone, inclusi gli artisti, i progettisti e i produttori, per una visita al posto dei siti considerati. Il viaggio ha richiesto circa 9 giorni, 2,5 per le corse, il resto per il film. Per Machu Picchu abbiamo scelto di non eseguire una corsa Scout, una ricerca preliminare e la prenotazione di alcuni giorni di buffer per il film.

Mentre a Roma, il team ha fotografato le foto di ogni area e ha notato i fatti interessanti, oltre a considerazioni pratiche, ad esempio il modo in cui è difficile passare a ogni punto e quanto è difficile eseguire il film a causa di folle o restrizioni. Questo può sembrare una vacanza, ma è molto lavoro. I giorni sono iniziati prima della mattina e non vengono interrotti fino alla sera. Ogni notte, il metraggio è stato caricato per tornare al team a Seattle. 

![Il nostro team di acquisizione a Roma.](images/holotour-filming-crew-rome-500px.jpg) 

Il nostro team di acquisizione a Roma. 


Al termine del viaggio Scout, è stato creato un piano finale per il filming effettivo. Questa operazione richiedeva un elenco dettagliato di dove ci si stava filmando, il giorno e l'ora. Ogni giorno all'estero è costoso, quindi questi viaggi necessitano di efficienza. Abbiamo prenotato guide e gestori a Roma per aiutarci a usare completamente tutti i giorni da prima dell'alba al tramonto. È necessario ottenere il miglior metraggio possibile per fare in modo che ci si trovi davvero.

### <a name="capturing-the-video"></a>Acquisizione del video

Eseguire alcune operazioni semplici durante l'acquisizione può semplificare notevolmente la post-elaborazione. Ad esempio, ogni volta che si uniscono immagini da più fotocamere, si verificano elementi visivi perché ogni fotocamera ha una visualizzazione leggermente diversa. Gli oggetti più vicini sono la fotocamera, maggiore è la differenza tra le visualizzazioni e più grande sarà l'Unione degli artefatti. Ecco un modo semplice per visualizzare il problema: tenere il dito davanti alla faccia e osservarlo con un solo occhio. Ora cambia gli occhi. Si noterà che il pollice sembra essere spostato rispetto allo sfondo. Se si tiene il cursore oltre il viso e si ripete l'esperimento, il cursore appare meno. Questo movimento apparente è simile al problema che abbiamo affrontato: gli occhi, come le nostre fotocamere, non vedono esattamente la stessa immagine perché sono separati da una distanza minima.

Poiché è molto più semplice evitare gli artefatti peggiori durante il film che è necessario correggere durante la post-elaborazione, si è tentato di evitare la necessità di unire gli oggetti di chiusura alla fotocamera, nella speranza di eliminare la necessità di unire gli oggetti di chiusura. La gestione di una grande deselezione della nostra fotocamera era probabilmente una delle principali problemi riscontrati durante la fase di Shooting. Lavorare con le guide locali è stato un enorme aiuto nella gestione delle folle, ma è stato anche scoperto che l'uso di segni, a volte piccoli coni o sacchetti di fagioli, per contrassegnare lo spazio di film era ragionevolmente efficace, soprattutto perché era necessario solo ottenere una breve quantità di metraggio in ogni posizione. Spesso il modo migliore per ottenere una buona acquisizione è stato quello di raggiungere il primo mattino, prima che la maggior parte delle persone si trovino.

Altre tecniche di acquisizione utili provengono direttamente dalle procedure tradizionali di film. Ad esempio, è stata usata una scheda di correzione dei colori su tutte le fotocamere e sono state acquisite foto di riferimento di trame e oggetti che potrebbero essere necessari in seguito. 

![Un taglio approssimativo di Machu Picchu che mostra la scheda di correzione dei colori.](images/rough-cut-machu-picchu-500px.png)

Una riduzione approssimativa del metraggio Pantheon prima dell'Unione.

### <a name="processing-the-video"></a>Elaborazione del video

L'acquisizione del contenuto di 360 ° è solo il primo passaggio, ma è necessaria una grande elaborazione per convertire il metraggio della fotocamera non elaborato che è stato acquisito nelle risorse finali visualizzate in HoloTour. Una volta tornato a casa, era necessario portare il video da 14 diversi feed della fotocamera e convertirlo in un unico video continuo con elementi minimi. Il nostro team di arte ha usato diversi strumenti per combinare e lucidare il metraggio acquisito ed è stata sviluppata una pipeline per ottimizzare l'elaborazione quanto più possibile. Il metraggio doveva essere assemblato, colorato con correzione e poi composito per rimuovere gli elementi e gli artefatti di dispersione o per aggiungere ulteriori sacche di vita e movimento, il tutto con l'obiettivo di migliorare la sensazione di essere effettivamente disponibili.

![Una riduzione approssimativa del metraggio Pantheon prima dell'Unione.](images/rough-cut-pantheon-500px.png)

Una riduzione approssimativa del metraggio Pantheon prima dell'Unione. 


Per unire i video, è stato usato uno strumento denominato [PTGui](https://www.ptgui.com/) che è stato integrato nella pipeline di elaborazione. Nell'ambito della post-elaborazione abbiamo estratto ancora i frame dai nostri video ed è stato trovato un modello di Unione che sembrava adatto per uno di questi frame. Il modello è stato quindi applicato a un plug-in personalizzato scritto che consentiva ai nostri artisti video di ottimizzare e modificare direttamente il modello di Unione durante la composizione in After Effects. 

![Screenshot di PTGui che mostra il metraggio Pantheon ricamato.](images/stitching-tool-pantheon-500px.png)

Screenshot di PTGui che mostra il metraggio Pantheon ricamato. 


### <a name="video-playback"></a>Riproduzione video

Una volta completata l'elaborazione del metraggio, abbiamo un video senza problemi, ma è eccezionalmente grande, intorno alla risoluzione di 8K. La decodifica del video è costosa e ci sono pochissimi computer che possono gestire un video da 8 a 8, quindi il prossimo problema è stato trovare un modo per riprodurre questo video in HoloLens. Sono state sviluppate diverse strategie per evitare il costo della decodifica, pur continuando a sembrare che l'utente stesse visualizzando l'intero video.

L'ottimizzazione più semplice consiste nell'evitare di decodificare parti del video che non cambiano molto. È stato scritto uno strumento che consente di identificare le aree in ogni scena che hanno un minimo o nessun movimento. Per queste aree viene mostrata un'immagine statica anziché decodificare un video per ogni frame. Per rendere possibile questa operazione, abbiamo diviso il video di grandi dimensioni in blocchi molto più piccoli.

Si è inoltre verificato che ogni pixel decodificato è stato usato in modo più efficace. Abbiamo sperimentato le tecniche di compressione per ridurre le dimensioni del video; le aree video vengono suddivise in base ai poligoni della geometria su cui verrebbe proiettata; sono state modificate le UV e sono stati riconfezionati i video in base alla quantità di dettagli inclusi nei diversi poligoni. Il risultato di questo lavoro è che ciò che è stato avviato come un singolo video a 8 KB si è trasformato in molti blocchi che sembrano quasi incomprensibili fino a quando non vengono riproiettati correttamente nella scena. Per uno sviluppatore di giochi che riconosce il mapping delle trame e la compressione UV, probabilmente avrà un aspetto familiare. 

![Vista completa del Pantheon prima delle ottimizzazioni.](images/pantheon-before-optimization-500px.png) 

Vista completa del Pantheon prima delle ottimizzazioni. 


![Metà destra del Pantheon, elaborata per la riproduzione video.](images/pantheon-process-video-playback-500px.png) 

Metà destra del Pantheon, elaborata per la riproduzione video. 


![Esempio di una singola area video dopo l'ottimizzazione e la compressione.](images/single-video-region-after-optimization-500px.png) 

Esempio di una singola area video dopo l'ottimizzazione e la compressione. 


Un altro espediente usato è stato quello di evitare la decodifica del video non visualizzato attivamente. In HoloTour è possibile visualizzare solo parte della scena completa in un determinato momento. I video vengono decodificati solo all'interno o all'esterno del campo di visualizzazione (FOV). Quando si ruota la testa, si inizia a riprodurre le aree del video che ora si trovano nel FOV e si smette di giocare con quelli che non sono più al suo interno. La maggior parte degli utenti non noterà neanche questo problema, ma se si gira rapidamente, si noterà che il video richiede un secondo avvio, nel frattempo verrà visualizzata un'immagine statica che, successivamente, tornerà a video una volta pronta.

Per far funzionare questa strategia è stato sviluppato un sistema di riproduzione video completo. È stato ottimizzato il codice per la riproduzione di basso livello per rendere estremamente efficiente il cambio video. Inoltre, abbiamo dovuto codificare i nostri video in modo speciale per consentire il passaggio rapido a qualsiasi video in qualsiasi momento. Questa pipeline di riproduzione ha impiegato una quantità significativa di tempo di sviluppo, quindi è stata implementata in fasi. Si è iniziato con un sistema più semplice che era meno efficiente, ma i progettisti e gli artisti consentivano di lavorare sull'esperienza e lo hanno migliorato lentamente in un sistema di riproduzione più affidabile che ci consentiva di fornire alla barra di qualità finale. Questo sistema finale aveva strumenti personalizzati creati in Unity per configurare il video nella scena e monitorare il motore di riproduzione.

### <a name="recreating-near-space-objects-in-3d"></a>Ricreazione di oggetti near-space in 3D

I video rappresentano la maggior parte degli elementi visualizzati in HoloTour, ma sono disponibili numerosi oggetti 3D che si trovano vicino all'utente, ad esempio il disegno in Piazza Navona, la fontana al di fuori del Pantheon o il palloncino ad aria calda per le scene aeree. Questi oggetti 3D sono importanti perché la percezione della profondità umana è molto corretta, ma non molto lontano. Possiamo uscire dalla distanza dei video, ma per consentire agli utenti di aggirare il proprio spazio e come sono in realtà, gli oggetti vicini necessitano di profondità. Questa tecnica è simile a quella che può essere visualizzata in un Museo di cronologia naturale, che illustra un diorama che presenta un landscape fisico, piante e campioni di animali in primo piano, ma si riferisce a un disegno opaco mascherato in background.

Alcuni oggetti sono semplicemente asset 3D creati e aggiunti alla scena per migliorare l'esperienza. Il disegno e la mongolfiera rientrano in questa categoria perché non erano presenti durante il film. Analogamente alle risorse dei giochi, sono state create da un artista 3D del team e con trama appropriata. Questi elementi vengono posizionati nelle nostre scene vicino a dove si trova e il motore di gioco può eseguirne il rendering nelle due visualizzazioni HoloLens in modo che vengano visualizzate come oggetto 3D.

Altre risorse, come la fontana al di fuori del Pantheon, sono oggetti reali presenti nei percorsi in cui stiamo girando video, ma per portare gli oggetti fuori dal video e in 3D, dobbiamo eseguire una serie di operazioni.

Per prima cosa, sono necessarie informazioni aggiuntive su ogni oggetto. In questo caso, il nostro team ha acquisito una grande quantità di filmati di riferimento di questi oggetti in modo da disporre di immagini dettagliate sufficienti per ricreare le trame in modo accurato. Il team ha anche eseguito un'analisi [fotogrammetria](https://en.wikipedia.org/wiki/Photogrammetry) , che costruisce un modello 3D da decine di immagini 2D, offrendo un modello di base dell'oggetto su scala perfetta.

Durante l'elaborazione del nostro metraggio, gli oggetti che verranno sostituiti con una rappresentazione 3D verranno rimossi dal video. L'asset 3D è basato sul modello fotogrammetria, ma è stato pulito e semplificato dagli artisti. Per alcuni oggetti, è possibile usare parti del video, ad esempio la trama dell'acqua sulla Fontana, ma la maggior parte della fontana è ora un oggetto 3D, che consente agli utenti di percepire la profondità e aggirarlo in uno spazio limitato nell'esperienza. La presenza di oggetti near-space come questo consente di aumentare in modo sostanziale il senso di realismo e consente di instradare gli utenti nella posizione virtuale. 

![Metraggio Pantheon con la Fontana rimossa. Verrà sostituito con un asset 3D.](images/object-removal-pantheon-500px.png)

Metraggio Pantheon con la Fontana rimossa. Verrà sostituito con un asset 3D.


## <a name="final-thoughts"></a>Considerazioni finali

Ovviamente, c'era ancora di più per creare questo contenuto rispetto a quello che abbiamo discusso qui. Ci sono alcune scene: ci piace denominarle "prospettive impossibili", tra cui la corsa a mongolfiera e la lotta gladiatore nel Colosseo, che ha adottato un approccio più creativo. Questi verranno affrontati in un case study futuro.

Ci auguriamo che la condivisione di soluzioni ad alcune delle principali problemi riscontrati durante la produzione sia utile per altri sviluppatori e che tu sia ispirato a usare alcune di queste tecniche per creare esperienze immersive per HoloLens. In tal caso, assicurati di condividerlo con noi nel [Forum sullo sviluppo di app per HoloLens](https://forums.hololens.com/).

## <a name="about-the-authors"></a>Informazioni sugli autori

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="David Haley" width="60" height="60" src="images/haley.png" /></td>
<td style="border:0" width="408"> <b>David Haley</b> è uno sviluppatore senior che ha appreso altre informazioni sui rig della fotocamera e la riproduzione video di quanto pensi possa essere usato in HoloTour.</td>
<td style="border:0" width="60px"> <img alt="Danny Askew" width="60" height="60" src="images/askew.png" /></td>
<td style="border:0" width="408"> <b>Danny storta</b> è un artista video che ha avuto la certezza che il suo percorso attraverso Roma fosse il più perfetto possibile.</td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Jason Syltebo" width="60" height="60" src="images/syltebo.png" /></td>
<td style="border:0" width="408"> <b>Jason Syltebo</b> è una finestra di progettazione audio che ha avuto la certezza di poter provare il paesaggio appropriato di ogni destinazione visitata, anche quando si torna indietro nel tempo.</td>
<td style="border:0" width="60px"> <img alt="Travis Steiner" width="60" height="60" src="images/steiner.png" /></td>
<td style="border:0" width="408"> <b>Travis Steiner</b> è un Director di progettazione che ha eseguito ricerche e percorsi Scout, ha creato piani di viaggio e ha diretto il film sul sito.</td>
</tr>
</table>



## <a name="see-also"></a>Vedere anche
* [Video: Microsoft HoloLens: HoloTour](https://www.youtube.com/watch?v=pLd9WPlaMpY)

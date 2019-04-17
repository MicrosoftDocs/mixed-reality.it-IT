---
title: 'Case study: acquisizione e la creazione di contenuto per HoloTour'
description: HoloTour per Microsoft HoloLens fornisce immersive 3D tour personale delle posizioni delle icone in tutto il mondo.
author: DannyAskew
ms.author: daaske
ms.date: 03/21/2018
ms.topic: article
keywords: Windows HoloTour, HoloLens, realtà mista
ms.openlocfilehash: 6c9e5f44c439310883c8b0271187a7b2263b0854
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597633"
---
# <a name="case-study---capturing-and-creating-content-for-holotour"></a>Case study: acquisizione e la creazione di contenuto per HoloTour

HoloTour per Microsoft HoloLens fornisce immersive 3D tour personale delle posizioni delle icone in tutto il mondo. Come le finestre di progettazione, alle creazioni degli artisti, produttori, audio progettisti e gli sviluppatori che lavorano al progetto trovato, la creazione di un rendering 3D convincente reale di un percorso noto richiede una combinazione univoca di wizardry creative e tecnologiche.

## <a name="the-tech"></a>Le tecnologie innovative

Con HoloTour, Desideravamo permette agli utenti di visitare alcune delle destinazioni più incredibile del mondo, come il [calamit di Picchu Machu](https://en.wikipedia.org/wiki/Machu_Picchu) Perù o il giorno moderne [Navona Piazza](https://en.wikipedia.org/wiki/Piazza_Navona) in Italia, direttamente dal chat del propria living. Il nostro team ha l'obiettivo di HoloTour a "ti chiedono di quanto ci siamo davvero." L'esperienza necessario per essere più della semplice immagini o video. Sfruttando la visualizzazione univoco, rilevamento e la tecnologia audio di HoloLens si ritiene che è stato possibile praticamente di trasporto è a un altro luogo. È necessario acquisire i danni derivanti dalla, suoni e geometry tridimensionale di ogni percorso è visitato e quindi ricreare che all'interno di app.

Per eseguire questa operazione, è necessaria una videocamera a 360 ° di rig con acquisizione dell'audio direzionale. È necessario per acquisire risoluzione estremamente elevate, in modo che le riprese avrebbe un aspetto precisi quando riprodotto in un HoloLens e videocamere dovrà essere posizionata ravvicinati per ridurre al minimo gli artefatti di unione (stitching). Volevamo completo sferica code coverage, non solo insieme all'orizzonte, ma sopra e sotto è anche. Rig devono inoltre essere portabile in modo che è stato possibile portarlo in tutto il mondo. Abbiamo valutato le opzioni disponibili sul mercato disponibili e realizzati che semplicemente non fossero sufficiente per realizzare la nostra visione: a causa di risoluzione, costo o dimensioni. Se non sono stati trovati rig della fotocamera che ha soddisfatto le nostre esigenze, è necessario compilare uno noi stessi.

### <a name="building-the-rig"></a>Creare il rig

La prima versione, ovvero effettuate da cartone, Velcro, condotto su nastro e 14 GoPro fotocamere, era qualcosa MacGyver sarebbe stata fiero di. Dopo aver esaminato tutti i dati da soluzioni di fascia bassa per rig prodotti personalizzati, fotocamere GoPro sono state in definitiva l'opzione migliore per noi perché sono stati di piccole dimensioni, conveniente ed era di facile utilizzo memoria. Il fattore di forma piccolo è particolarmente importante perché ci ha permesso di inserire fotocamere abbastanza ravvicinati, minore è la distanza tra le telecamere, sarà minore di elementi unione (stitching). La disposizione della fotocamera univoco ha permesso di ottenere la copertura completa sfera *plus* sufficiente si sovrappongono a in modo intelligente allineare fotocamere e uniformare alcuni elementi durante il processo di unione (stitching).

Sfruttando la [spaziale audio](spatial-sound.md) funzionalità su HoloLens è fondamentale per la creazione di un'esperienza coinvolgente e concreto convincente reale. Abbiamo utilizzato una matrice di quattro microfono situata sotto le fotocamere nel treppiede, che potrebbe acquisire l'audio dalla posizione del nostro fotocamera in quattro direzioni, da fornire informazioni sufficienti per creare i suoni spaziale nel nostro scene.

![Il rig di fotocamera 360° impostato per l'acquisizione, ormai di fuori di Pantheon.](images/camera-pantheon-200px.png)

Il rig di fotocamera 360° impostato per l'acquisizione, ormai di fuori di Pantheon. 


È stato testato out il rig quelli personalizzati portandola fino a Ridge Rattlesnake vicino Seattle e acquisizione di panorami in cima l'escursione. Il risultato, sebbene notevolmente minore redazionali le posizioni che presenti HoloTour oggi, abbiamo certezza che la progettazione di rig era sufficiente per il proprio aspetto ci siamo davvero.

Abbiamo aggiornato il rig da Velcro e cartone a una custodia stampa 3D e acquistato Pack esterni della batteria per le fotocamere GoPro semplificare la gestione della batteria. Quindi abbiamo un test più esteso, che passano a San Francisco per creare una presentazione in miniatura coast della città e il bridge di Golden Gate iconico. Questo rig di fotocamera è quella usata per la maggior parte dei nostri acquisizioni delle posizioni visitati in HoloTour.

![Il rig a 360° della fotocamera ripresa Picchu Machu.](images/camera-machu-pichu-500px.png)

Il rig a 360° della fotocamera ripresa Picchu Machu. 


## <a name="behind-the-scenes"></a>Dietro le quinte

Prima di ripresa, dovevamo figura out le posizioni di voler includere sul nostro viaggio virtuale. Rome è stato il primo percorso che previsto per la spedizione e si vuole ottenere il risultato desiderato, in modo che abbiamo deciso di eseguire in anticipo un viaggio di esplorazione. Ti abbiamo inviato un team di sei operatori, inclusi gli artisti, finestre di progettazione e i Producer, ovvero per la visita ai siti di cui si stanno considerando di persona. L'ottimizzazione dei viaggi ha richiesto circa 9 giorni – 2.5 di viaggio, il resto per riprese. (Per Picchu Machu abbiamo scelto di non è un viaggio di scout, ricerca in anticipo e pochi giorni del buffer per la ripresa di prenotazione.)

In Roma, il team ha impiegato foto di ogni area e annotato aspetti interessanti, nonché considerazioni pratiche, ad esempio di come sia difficile da ogni posizione e quanto sia difficile sia pellicola a causa di restrizioni o folla. Ciò potrebbe sembrare una vacanza, ma è molto lavoro. Giorni avviata nelle prime fasi del mattino e andrebbe senza interruzioni fino alla sera. Ogni notte, riprese è stata caricata per il team in Seattle per esaminare. 

![La squadra di acquisizione Roma.](images/holotour-filming-crew-rome-500px.jpg) 

La squadra di acquisizione Roma. 


Dopo che è stata completata l'ottimizzazione dei viaggi di scout, è stato effettuato un piano finale per la ripresa effettiva. Questa operazione necessaria un elenco dettagliato di in cui abbiamo intenzione di film, il giorno e ora. Ogni giorno all'estero è costoso, in modo che tali roundtrip doveva essere efficiente. Abbiamo prenotato gestori Rome e guide per consentire agli utenti e completamente usati ogni giorno dalla prima alba per dopo la terminazione del servizio. È necessario ottenere le riprese migliore possibile per rendere è quanto ci siamo davvero.

### <a name="capturing-the-video"></a>Acquisizione video

Eseguire alcune semplici operazioni durante l'acquisizione può semplificare la post-elaborazione. Ad esempio, ogni volta che unire le immagini da videocamere di più, si finisce con elementi visivi perché ogni videocamera ha una vista leggermente diversa. Sono gli oggetti più da vicino alla fotocamera, il più grande la differenza tra le visualizzazioni e più grande di unione (stitching) sarà. Ecco un modo semplice per identificare il problema: aspettare che il cursore davanti il viso e osservare con solo un occhio. Passare a questo punto gli occhi. Si noterà che il controllo thumb sembra spostare relativo sfondo. Se si tiene il pollice ulteriormente lontano dal viso e ripetere il test, il controllo thumb risulterà spostare minore. Ovvero apparente dello spostamento è simile al problema di unione (stitching) abbiamo affrontato: Gli occhi, ad esempio le videocamere, non vedranno la stessa immagine esatta in quanto sono separati da un piccolo distanza.

Poiché è molto più semplice impedire i peggiore degli elementi durante la ripresa rispetto al correggerli in post-elaborazione, abbiamo provato a mantenere persone e le risorse a portata di mano dalla fotocamera nella speranza che è stato possibile eliminare la necessità di unire gli oggetti in primo piano. Mantenere una cancellazione elevata intorno la fotocamera è stata probabilmente una delle maggiori sfide che è sono stati rilevati durante la ripresa e avevamo alla creatività per consentire il funzionamento. L'utilizzo con le guide locale è stato un enorme aiuto nella gestione folla, ma abbiamo scoperto anche che con firma e talvolta piccoli coni o contenitori bean, ovvero contrassegnare uno spazio sulla registrazione era ragionevolmente efficiente, soprattutto perché è necessario solo ottenere un breve intervallo di filmato in ogni posizione. Spesso il modo migliore per ottenere un'acquisizione di buon doveva semplicemente per arrivare nelle prime fasi del mattino, prima della maggior parte degli utenti ha bussato.

Alcune altre tecniche di acquisizione utile provengono direttamente practices pellicola tradizionali. Ad esempio, abbiamo utilizzato una scheda di correzione del colore su tutti i nostri fotocamere e foto di riferimento acquisita delle trame e degli oggetti che potrebbe essere necessario in un secondo momento. 

![Una Taglia approssimativa di Picchu Machu che mostra la scheda di correzione del colore.](images/rough-cut-machu-picchu-500px.png)

Una Taglia approssimativa del filmato di Pantheon prima dell'unione.

### <a name="processing-the-video"></a>L'elaborazione del video

Acquisizione di contenuti a 360° è solo il primo passaggio, ovvero una grande quantità di elaborazione è necessaria per convertire la videocamera non elaborati sono acquisite alle risorse presenti HoloTour finale. Dopo che è stato nuovamente home è necessaria per rendere il video dalla fotocamera diversi 14 feed e trasformarlo in un singolo video continuo con gli elementi minimi. Il nostro team art utilizzata una serie di strumenti per combinare e polacco le riprese acquisita e abbiamo sviluppato una pipeline per ottimizzare l'elaborazione quanto più possibile. Le riprese dovevano essere uniti in modalità colore insieme, corretti e quindi compositi per rimuovere un elemento di distrazione elementi e gli artefatti o aggiungere tasca supplementare di vita e il movimento, tutte con l'obiettivo di migliorare tale sensazione di essere effettivamente presenti.

![Una Taglia approssimativa del filmato di Pantheon prima dell'unione.](images/rough-cut-pantheon-500px.png)

Una Taglia approssimativa del filmato di Pantheon prima dell'unione. 


Per unire i video, abbiamo utilizzato uno strumento denominato [PTGui](http://www.ptgui.com/) e si è integrato nella nostra pipeline di elaborazione. Come parte di post-elaborazione è estratto ancora i fotogrammi i video e un modello unione (stitching) bel per uno di tali frame è stato trovato. Tale modello viene quindi applicato a un plug-in personalizzati che abbiamo scritto che consentito nostro video alle creazioni degli artisti ottimizzare e migliorare il modello di unione (stitching) direttamente durante la composizione in effetti dopo. 

![Schermata di PTGui che mostra la ripresa di Pantheon unita.](images/stitching-tool-pantheon-500px.png)

Schermata di PTGui che mostra la ripresa di Pantheon unita. 


### <a name="video-playback"></a>Riproduzione video

Dopo il completamento dell'elaborazione della ripresa, abbiamo un video senza problemi, ma è straordinariamente grandi dimensioni, ovvero la risoluzione di circa 8 K. Decodifica video è costosa e sono presenti pochi computer in grado di gestire un video da 8 KB, in modo sfida era trovare un modo per riprodurre questo video riaccenderle HoloLens. Abbiamo sviluppato una serie di strategie per evitare il costo di decodifica mantenendo comunque l'aspetto utente, ad esempio si stava visualizzando l'intero video.

L'ottimizzazione più semplice consiste nell'evitare decodifica parti del video che non vengono modificati molto. Abbiamo scritto uno strumento per identificare le aree in ogni scena che hanno poco o Nessun movimento. Per tali aree è mostrare un'immagine statica invece di decodifica di un video ogni frame. A tale scopo, abbiamo diviso il video di grandi dimensioni in blocchi di dimensioni inferiori.

Abbiamo anche assicurarsi che ogni pixel che è decodificate sia stato usato in modo più efficace. Abbiamo sperimentato con le tecniche di compressione per ridurre le dimensioni del video; Abbiamo suddiviso le aree di video in base ai poligoni della geometria che potrebbe essere proiettato; Abbiamo regolato UVs e ricompressi i video in base a quanto poligoni diversi dettagli inclusi. Il risultato di questa attività è che è iniziato come una singola 8k video convertiti in numero di blocchi con un aspetto pressoché incomprensibile fino a quando non sono previste correttamente nuovamente nella scena. Per uno sviluppatore di gioco che riconosce il mapping della trama e compressione UV, ciò risulterà probabilmente familiare. 

![Una visualizzazione completa di Pantheon prima le ottimizzazioni.](images/pantheon-before-optimization-500px.png) 

Una visualizzazione completa di Pantheon prima le ottimizzazioni. 


![Parte destra di Pantheon, elaborati per la riproduzione di video.](images/pantheon-process-video-playback-500px.png) 

Parte destra di Pantheon, elaborati per la riproduzione di video. 


![Esempio di una singola area video dopo l'ottimizzazione e compressione.](images/single-video-region-after-optimization-500px.png) 

Esempio di una singola area video dopo l'ottimizzazione e compressione. 


Per evitare la decodifica non sono attivamente di visualizzazione del video è stato un altro trucco che è stato usato. Mentre in HoloTour, è possibile visualizzare solo parte della scena completa in qualsiasi momento. È solo possibile decodificare video all'interno o poco di fuori del campo visualizzazione (). Mente ruoti, iniziamo riproduzione le aree del video che si trovano ora nel campo di visualizzazione e interrompere la riproduzione di quelle che non sono più in esso contenuti. La maggior parte delle persone non noteranno anche ciò che accade, ma se si attiva rapidamente, si noterà il video richiede un secondo per avviare, nel frattempo si noterà un'immagine statica quali dissolvenze quindi eseguire il backup a video quando è pronto.

Per il funzionamento questa strategia abbiamo sviluppato un sistema di riproduzione del video complete. Il codice di basso livello riproduzione è stato ottimizzato per rendere video cambio estremamente efficienti. Inoltre, è stato necessario codificare i video in modo speciale per rendere possibile passare rapidamente a qualsiasi video in qualsiasi momento. Questa pipeline riproduzione ha richiesto una quantità significativa di tempo di sviluppo viene implementato in più fasi. Siamo partiti da un sistema più semplice che era meno efficiente, ma consentiti finestre di progettazione e gli artisti per lavorare sull'esperienza e lentamente migliorata a un sistema di riproduzione più affidabile che ha permesso di fornire la barra qualità finale. Questo sistema finale era strumenti personalizzati che è stato creato all'interno di Unity per configurare il video all'interno della scena e monitorare il motore di riproduzione.

### <a name="recreating-near-space-objects-in-3d"></a>Creazione di oggetti quasi gli spazi in 3D

I video costituiscono la maggior parte di ciò che viene visualizzato in HoloTour, ma esistono una serie di oggetti 3D che vengono visualizzati vicino, ad esempio il disegno in Navona Piazza, quest'opera di fuori di Pantheon o mongolfiera che sei per le scene aeree. Questi oggetti 3D sono importanti perché percezione profondità umana è particolarmente Interagisci, ma non molto valide a portata di mano. È possibile usare senza problemi video nella distanza, ma per consentire agli utenti di camminare loro spazio e sentono non sono disponibili, gli oggetti nelle vicinanze necessitano di profondità. Questa tecnica è simile al tipo di risultato che potrebbe essere visualizzato in un museo naturale cronologia, ovvero un diorama paesaggio fisico, stabilimenti ed esemplari animali in primo piano, ma si allontana in un dipinto grezze prosegue senza soste mascherato in background dell'immagine.

Alcuni oggetti sono asset 3D semplicemente abbiamo creato e aggiunto alla scena per migliorare l'esperienza. Il disegno e la mongolfiera rientrano in questa categoria perché non sono presenti quando si girata. Analogamente a risorse del gioco, sono stati creati per un artista 3D del nostro team e trama in modo appropriato. Inseriamo questi elementi nel nostro scene quasi qual è lo stato e il motore di gioco può eseguirne il rendering per le due visualizzazioni di HoloLens, in modo che vengano visualizzati come un oggetto 3D.

Altri asset, come quest'opera di fuori di Pantheon, sono oggetti reali presenti nelle posizioni in cui si riprende video, ma per visualizzare questi oggetti dai video in 3D, è necessario eseguire una serie di operazioni.

In primo luogo, sono necessarie informazioni aggiuntive su ogni oggetto. Mentre in percorso per la ripresa, il nostro team acquisito una grande quantità di materiale di riferimento di questi oggetti in modo che è stato sufficientemente dettagliate immagini per ricreare accuratamente le trame. Il team ha anche eseguito un [photogrammetry](https://en.wikipedia.org/wiki/Photogrammetry) scan, che costruisce un modello 3D di decine di immagini 2D, offrendo in tal modo un modello approssimativo dell'oggetto su larga scala perfetta.

Quando si elabora il filmato, gli oggetti in un secondo momento verranno sostituiti con una rappresentazione 3D vengono rimossi dal video. L'asset 3D è basato sul modello photogrammetry ma pulito e semplificata dal nostro alle creazioni degli artisti. Per alcuni oggetti, è possibile usare le parti del video, ad esempio la trama di acqua in quest'opera, ma la maggior parte di quest'opera è ora un oggetto 3D, che consente agli utenti di percepire profondità e camminare in uno spazio limitato nell'esperienza di. Gli oggetti di uno spazio quasi simile al seguente con notevolmente aggiunge il senso di realismo e consente di forzare a terra gli utenti nel percorso virtuale. 

![Ripresa di pantheon con quest'opera rimosso. Questo verrà sostituito con un asset 3D.](images/object-removal-pantheon-500px.png)

Ripresa di pantheon con quest'opera rimosso. Questo verrà sostituito con un asset 3D.


## <a name="final-thoughts"></a>Considerazioni finali

Ovviamente, si è verificato più alla creazione di questo contenuto rispetto a ciò che è stata illustrata di seguito. Esistono alcuni scene, desideriamo chiamarli "comunicazione Impossibile prospettive", inclusi riflettesse fumetto aria calda e il gladiator combattere il Colosseo, che ha adottato un approccio più creativo. Verrà presa in un case study di future.

Ci auguriamo che la condivisione di soluzioni ad alcune delle sfide più grande che è stato in fase di produzione è utile ad altri sviluppatori e che si è ispirata usare alcune di queste tecniche per creare esperienze coinvolgenti per HoloLens. (E se, assicurarsi di condividerlo con noi nel [forum di HoloLens App Development](https://forums.hololens.com/)!)

## <a name="about-the-authors"></a>Informazioni sugli autori

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="David Haley" width="60" height="60" src="images/haley.png" /></td>
<td style="border:0" width="408"> <b>David Haley</b> è uno sviluppatore Senior che state fornite rig fotocamera e la riproduzione di video a pensava possibili lavorando HoloTour.</td>
<td style="border:0" width="60px"> <img alt="Danny Askew" width="60" height="60" src="images/askew.png" /></td>
<td style="border:0" width="408"> <b>Danny sghembe</b> è un artista Video che fa in modo che il tuo viaggio attraverso Roma era modo impeccabile possibile.</td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Jason Syltebo" width="60" height="60" src="images/syltebo.png" /></td>
<td style="border:0" width="408"> <b>Jason Syltebo</b> è una finestra di progettazione di Audio che ha effettuato che possono verificarsi soundscape di ogni destinazione visita, anche quando si torna indietro nel tempo.</td>
<td style="border:0" width="60px"> <img alt="Travis Steiner" width="60" height="60" src="images/steiner.png" /></td>
<td style="border:0" width="408"> <b>Travis Steiner</b> è un responsabile di progettazione che analizzate e scouted posizioni, creato i piani di viaggio e indirizzato riprese nel sito.</td>
</tr>
</table>



## <a name="see-also"></a>Vedere anche
* [Video: Microsoft HoloLens: HoloTour](https://www.youtube.com/watch?v=pLd9WPlaMpY)

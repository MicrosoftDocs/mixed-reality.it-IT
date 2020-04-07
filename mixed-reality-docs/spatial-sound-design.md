---
title: Usare il suono spaziale nelle applicazioni di realtà mista
description: Il suono spaziale è uno strumento potente per l'immersione, l'accessibilità e la progettazione dell'esperienza utente nelle applicazioni a realtà mista.
author: kegodin
ms.author: kegodin
ms.date: 11/02/2019
ms.topic: article
keywords: Realtà mista di Windows, audio spaziale, progettazione, stile
ms.openlocfilehash: 08844f6d837407d52ad2ab84b78440ce856151fc
ms.sourcegitcommit: b1ca4194eff452804ce5852208cce9815c6a4500
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80677990"
---
# <a name="how-to-use-sound-in-mixed-reality-applications"></a>Come usare un suono in applicazioni in realtà mista

È possibile usare il suono per informare e rafforzare il modello mentale dell'utente dello stato dell'applicazione. Usare la spazializzazione, quando appropriato, per inserire i suoni nel mondo della realtà mista. Quando si connettono i revisori e l'oggetto visivo in questo modo, si approfondisce la natura intuitiva delle interazioni e si aumenta la confidenza degli utenti.
<br><br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="when-to-add-sounds"></a>Quando aggiungere suoni
Le applicazioni a realtà mista hanno spesso una necessità maggiore di suoni rispetto alle app 2D, a causa della mancanza di un'interfaccia tattile. Aggiungere i suoni quando informano l'utente o rinforzano le interazioni.

### <a name="inform-and-reinforce"></a>Informare e rafforzare
* Per gli eventi che non vengono avviati dall'utente, ad esempio le notifiche, utilizzare il suono per informare l'utente che è stata apportata una modifica.
* Le interazioni possono avere diverse fasi. Usare il suono per rinforzare le transizioni di fase.

Vedere gli esempi seguenti di interazioni, eventi e caratteristiche del suono suggerite.

### <a name="exercise-restraint"></a>Esercizio vincolato
Gli utenti non hanno una capacità illimitata per le informazioni audio.
* Ogni suono deve comunicare informazioni importanti e specifiche.
* Quando l'app riproduce un suono per informare l'utente, ridurre temporaneamente il volume di altri suoni.
* Per i suoni del passaggio del mouse (vedere le informazioni seguenti), aggiungere un ritardo di tempo per impedire l'attivazione di un suono eccessivo.

### <a name="dont-rely-solely-on-sounds"></a>Non fare affidamento esclusivamente su suoni
I suoni usati correttamente sono utili per gli utenti. Verificare tuttavia che l'applicazione sia utilizzabile anche con il suono disattivato.
* È possibile che gli utenti abbiano problemi di udito.
* L'applicazione può essere usata in un ambiente ad alta voce.
* Gli utenti possono avere problemi di privacy o altri motivi per disabilitare l'audio del dispositivo.

## <a name="how-to-sonify-interactions"></a>Come Sonify le interazioni
I tipi di interazione in realtà mista includono movimenti, manipolazione diretta e voce. Usare le caratteristiche suggerite seguenti per selezionare o progettare i suoni per queste interazioni.

### <a name="gesture-interactions"></a>Interazioni tra movimenti
In realtà mista, gli utenti possono interagire con i pulsanti usando il mouse. Le azioni dei pulsanti si verificano in genere quando l'utente rilascia invece di premere il pulsante per dare all'utente la possibilità di annullare l'interazione. Usare i suoni per rafforzare queste fasi. Per aiutare gli utenti a usare i pulsanti distanti, considerare anche l'uso di un suono del passaggio del puntatore.
* Il pulsante-premere suoni dovrebbe essere un breve "clic" tattile.<br/>Esempio: [MRTK_ButtonPress. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_ButtonPress.wav)
* Il pulsante: i suoni "non stampati" devono avere un aspetto tattile simile. Un passo più elevato rispetto al suono della stampa rinforza il senso del completamento.<br/>Esempio: [MRTK_ButtonUnpress. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_ButtonUnpress.wav)
* Per i suoni del passaggio del mouse, provare a usare un suono sottile e non minaccioso, ad esempio un tonfo o un urto a bassa frequenza.

### <a name="direct-manipulation"></a>Manipolazione diretta
In HoloLens 2, il rilevamento a mano articolata supporta la manipolazione diretta degli elementi dell'interfaccia utente. I suoni sono importanti quando non sono presenti altri commenti fisici.

Un suono di pressione di un *pulsante* è importante nella manipolazione diretta perché l'utente non ottiene altre indicazioni quando raggiunge la fine del tratto della chiave. Gli indicatori audio del viaggio di chiave possono essere piccoli, sottili e bloccati. Come per le interazioni con i movimenti, le pressioni dei pulsanti dovrebbero avere un breve suono tattile come un clic. Le dispressioni dovrebbero avere un suono di clic simile ma con un passo elevato.
* Esempio: [MRTK_ButtonPress. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_ButtonPress.wav)
* Esempio: [MRTK_ButtonUnpress. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_ButtonUnpress.wav)

È difficile confermare visivamente un'azione di recupero o rilascio. Spesso l'utente sarà in grado di qualsiasi effetto visivo, mentre gli oggetti con corpo rigido non hanno un analogo strumento visivo reale di "grabbing". I suoni possono comunicare efficacemente le interazioni di recupero e rilascio.
* Le azioni di recupero dovrebbero avere un breve suono tattile, leggermente ovattato, che evoca l'idea di una chiusura delle dita intorno a un oggetto. A volte è presente anche un suono "fruscio" che conduce al suono accattivante per comunicare il movimento della mano.<br/>Esempio: [MRTK_Move_Start. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_Move_Start.wav)
* Le azioni di rilascio dovrebbero ottenere un suono simile breve e tattile. Si tratta in genere di un tono inferiore rispetto al suono della pinza e in ordine inverso, con un effetto e quindi un "fruscio" per comunicare che l'oggetto sta per essere risolto.<br/>Esempio: [MRTK_Move_End. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_Move_End.wav)

Un'interazione di *disegno* deve ottenere un suono persistente di loop il cui volume è determinato dallo spostamento della mano dell'utente. Dovrebbe rimanere invisibile quando la mano dell'utente è ancora e più forte quando la mano si muove rapidamente.

### <a name="voice-interactions"></a>Interazioni vocali
Le interazioni vocali hanno spesso elementi visivi sottili. Usare i suoni per rafforzare le fasi di interazione. Si consiglia di usare suoni più tonali per distinguerli dai suoni movimento e manipolazione diretta.

* Usare un segnale acustico positivo per le *conferme*dei comandi vocali. I toni crescenti e gli intervalli musicali principali sono validi.
* Usare un tono più breve e meno positivo per gli *errori*dei comandi vocali. Evitare i suoni negativi. Usare invece un suono più a percussione, neutro per comunicare che l'applicazione sta procedendo dall'interazione.
* Se l'applicazione ha una parola di riattivazione, usare un tono breve e gentile quando il dispositivo *inizia l'ascolto*. Usare un suono di loop delicato mentre l'applicazione *è* in ascolto.

### <a name="notifications"></a>Notifiche
Le notifiche comunicano le modifiche dello stato dell'applicazione e altri eventi che non vengono avviati dall'utente, ad esempio i completamenti dei processi, i messaggi e le chiamate telefoniche.

In realtà mista, gli oggetti talvolta si spostano fuori dal campo di visualizzazione dell'utente. Accompagna lo spostamento di *oggetti animati* con un suono spaziale che dipende dal tipo di oggetto e dalla velocità di movimento.
* Consente di riprodurre un suono spaziali alla fine di un'animazione per informare l'utente della nuova posizione dell'oggetto.
* Per i movimenti graduali, un suono "fruscio" durante lo spostamento consente all'utente di tenere traccia dell'oggetto.

I suoni di *notifica del messaggio* possono essere ripetuti ripetutamente, a volte in rapida successione. È importante che non si trovino o suonino difficili. I suoni tonali positivi a metà intervallo sono validi.

* I suoni per le chiamate in ingresso devono avere qualità simili a una suoneria del telefono cellulare. Si tratta in genere di frasi musicali in loop che giocano fino a quando l'utente non risponde alla chiamata.
* La connessione e la disconnessione vocale dovrebbero avere un suono tonale breve. Il suono della connessione deve essere un tono positivo per indicare una connessione corretta. Il suono di disconnessione dovrebbe essere un suono neutro per indicare il completamento della chiamata.

## <a name="handle-spatialization"></a>Gestire la spazializzazione
La spazializzazione USA cuffie stereo o altoparlanti per inserire i suoni nel mondo in realtà mista.

### <a name="which-sounds-to-spatialize"></a>Che suoni spatialize
Un suono deve essere spaziali quando è associato a un evento che ha una posizione spaziale. Sono incluse l'interfaccia utente, le voci di intelligenza artificiale incarnate e gli indicatori visivi.

Gli elementi dell' *interfaccia utente* di Spatialize consentono di declutterare lo spazio "Sonic" dell'utente limitando il numero di suoni stereo che sentono. Le interazioni di manipolazione, ad esempio il tocco, l'acquisizione e il rilascio, si sentono più naturali quando il feedback audio è spaziale. Prendere in considerazione le seguenti informazioni sull'attenuazione della distanza per questi elementi.

Spatialize gli *indicatori visivi* e le *voci di intelligenza artificiale* per informare in modo intuitivo gli utenti quando questi elementi non rientrano nel campo di visualizzazione.
    
Al contrario, evitare la spazializzazione per le *voci di intelligenza artificiale senza facet* e altri elementi che non dispongono di una posizione spaziale ben definita. La spazializzazione senza un elemento visivo correlato può distrarre gli utenti in quanto è presente un elemento visivo che non è in grado di trovare.

La spazializzazione viene eseguita con un costo della CPU. Molte applicazioni hanno al massimo due suoni contemporaneamente. Il costo della spazializzazione in tal caso è probabilmente irrilevante. È possibile utilizzare il monitoraggio della frequenza dei fotogrammi MRTK per valutare l'effetto dell'aggiunta della spazializzazione.

### <a name="when-and-how-to-apply-distance-based-attenuation"></a>Quando e come applicare un'attenuazione basata sulla distanza
Nel mondo fisico, i suoni più lontani sono più tranquilli. Il motore audio può modellare questa attenuazione in base alla distanza di origine. Utilizzare l'attenuazione basata sulla distanza per la comunicazione di informazioni rilevanti.

Le distanze per gli *indicatori visivi*, gli *ologrammi animati*e altri suoni informativi sono in genere rilevanti per l'utente. Usare l'attenuazione basata sulla distanza per fornire i segnali in modo intuitivo.

Regolare la curva di attenuazione per ogni origine per adattarla alle dimensioni degli spazi del mondo in realtà mista. La curva predefinita del motore audio è spesso destinata a spazi di dimensioni molto grandi (fino a metà chilometro).

I suoni che rinforzano le *fasi progressive delle azioni dei pulsanti* e altre interazioni non devono essere applicati all'attenuazione. Gli effetti di questi suoni sono in genere più importanti rispetto alla comunicazione della distanza al pulsante. Le variazioni possono essere distracting, soprattutto con le tastiere, quando è possibile che molti clic sui pulsanti vengano uditi in successione.

### <a name="which-spatialization-technology-to-use"></a>Quale tecnologia di spazializzazione usare
Con le cuffie o i relatori HoloLens, usare le tecnologie di spazializzazione basate su HRTF (Head-Related Transfer Function). Queste tecnologie modellano la propagazione sonora intorno all'Head nel mondo fisico. Anche quando un'origine audio si trova all'estrema parte della testa, l'audio si propaga all'orecchio distanti con alcune attenuazioni e ritardo. Il panning degli speaker, al contrario, si basa solo sull'attenuazione e applica l'attenuazione totale nell'orecchio sinistro quando i suoni si trovano sul lato destro (e viceversa). Questa tecnica può risultare scomoda per i listener "normale udito" e inaccessibile per i listener che hanno problemi di udito in un orecchio.

## <a name="next-steps"></a>Passaggi successivi
* [Usare un suono spaziale in Unity](spatial-sound-in-unity.md)
* [Case Study di Roboraid](case-study-using-spatial-sound-in-roboraid.md)
* [Case Study di HoloTour](case-study-spatial-sound-design-for-holotour.md)

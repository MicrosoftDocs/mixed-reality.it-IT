---
title: Uso di suoni nelle applicazioni di realtà mista
description: Il suono spaziale è uno strumento potente per l'immersione, l'accessibilità e la progettazione dell'esperienza utente nelle applicazioni di realtà mista.
author: kegodin
ms.author: kegodin
ms.date: 11/02/2019
ms.topic: article
keywords: Realtà mista di Windows, audio spaziale, progettazione, stile
ms.openlocfilehash: c069095808eaa9d31b1ffa41dbaa29c9f635837b
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641060"
---
# <a name="using-sound-in-mixed-reality-applications"></a>Uso di suoni nelle applicazioni di realtà mista

Usare il suono per informare e rafforzare il modello mentale dell'utente dello stato dell'applicazione. Usare la spazializzazione, quando appropriato, per inserire i suoni nel mondo misto. La connessione del controllo uditivo e dell'oggetto visivo in questo modo consente di approfondire la natura intuitiva di molte interazioni e di aumentare la confidenza degli utenti.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="when-should-i-add-sounds"></a>Quando è necessario aggiungere I suoni?
Le applicazioni di realtà mista spesso hanno una maggiore necessità di suoni rispetto alle applicazioni in una schermata 2D, a causa della mancanza di un'interfaccia fisica. I suoni devono essere aggiunti quando informano l'utente o rinforzano le interazioni.

### <a name="inform-and-reinforce"></a>Informare e rafforzare
* Per gli eventi non avviati dall'utente, ad esempio le notifiche, prendere in considerazione l'aggiunta di suoni per informare l'utente che è stata apportata una modifica.
* Le interazioni possono avere diverse fasi. Provare a usare i suoni per rafforzare le transizioni di fase.

Vedere di seguito per esempi di interazioni, eventi e caratteristiche del suono suggerite.

### <a name="exercise-restraint"></a>Esercizio vincolato
Gli utenti non hanno una capacità illimitata per le informazioni audio:
* Ogni suono deve comunicare informazioni specifiche, utili
* Per la riproduzione di suoni destinati a informare l'utente, ridurre temporaneamente il volume di altri suoni
* Per i suoni del pulsante del mouse (vedere di seguito), aggiungere un ritardo di tempo per impedire l'attivazione di suoni eccessiva

### <a name="dont-rely-solely-on-sounds"></a>Non fare affidamento esclusivamente su suoni
I suoni usati bene saranno utili quando gli utenti possono ascoltarli, ma assicurarsi che l'applicazione sia utilizzabile anche con l'audio disattivato.
* È possibile che gli utenti abbiano problemi di udito
* L'applicazione può essere usata in un ambiente ad alta voce
* Gli utenti possono avere privacy o altri motivi per disabilitare l'audio del dispositivo

## <a name="how-should-i-sonify-interactions"></a>Come si Sonify le interazioni?
I tipi di interazione in realtà mista includono movimenti, manipolazione diretta e voce. Usare le caratteristiche suggerite seguenti per selezionare o progettare i suoni per queste interazioni.

### <a name="gesture-interactions"></a>Interazioni tra movimenti
In realtà mista, gli utenti possono interagire con i pulsanti usando un cursore. Le azioni dei pulsanti vengono in genere eseguite quando l'utente ha rilasciato il pulsante, anziché quando è stato premuto, per consentire all'utente di annullare l'interazione. Usare i suoni per rafforzare queste fasi. Inoltre, per assistere gli utenti nella scelta di pulsanti distanti, è consigliabile utilizzare un cursore al passaggio del mouse.
* I suoni di pressione del pulsante dovrebbero avere un breve clic tattile. Esempio: [MRTK_ButtonPress. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_ButtonPress.wav)
* Il pulsante per la decompressione di suoni dovrebbe avere un aspetto tattile simile. La presenza di un pitch elevato rispetto al suono della pressione rinforza il senso del completamento. Esempio: [MRTK_ButtonUnpress. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_ButtonUnpress.wav)
* Per i suoni del passaggio del mouse, provare a usare un suono sottile e non minaccioso, ad esempio un tonfo o un urto a bassa frequenza.


### <a name="direct-manipulation"></a>Manipolazione diretta
In HoloLens 2, il rilevamento a mano articolata supporta la manipolazione diretta degli elementi dell'interfaccia utente. I suoni sono sostituzioni importanti per la mancanza di commenti fisici.

Un suono di pressione di un **pulsante** è importante nella manipolazione diretta perché l'utente non ha alcuna indicazione fisica quando ha raggiunto la fine del viaggio della chiave. Gli indicatori visivi della corsa della chiave possono essere piccoli, sottili e bloccati. Come per le interazioni con i movimenti, le pressioni dei pulsanti dovrebbero avere un breve suono tattile, come un clic, e le depressioni dovrebbero avere un clic simile con un passo elevato.
* Esempio: [MRTK_ButtonPress. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_ButtonPress.wav)
* Esempio: [MRTK_ButtonUnpress. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_ButtonUnpress)

La conferma di una **cattura** o di una **versione** nella manipolazione diretta è difficile da comunicare visivamente. La mano dell'utente sarà spesso in modo analogo a qualsiasi effetto visivo e gli oggetti con corpo rigido non hanno un analogo oggetto visivo reale di "grabbing". Al contrario, i suoni possono comunicare efficacemente con successo le interazioni di recupero e rilascio.
* Le azioni di recupero dovrebbero avere un breve suono tattile, in qualche modo ovattato, che evoca l'idea di una chiusura delle dita intorno a un oggetto. A volte questo è accompagnato da un suono "fruscio" che determina l'effetto del suono per comunicare il movimento della mano durante l'acquisizione. Esempio: [MRTK_Move_Start. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_Move_Start.wav)
* Le azioni di rilascio dovrebbero avere un suono simile breve e tattile, in genere ricavato dal suono di prelevamento e in un ordine inverso nel tempo, con un effetto e quindi un "fruscio" per comunicare l'oggetto in base alla posizione. Esempio: [MRTK_Move_End. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_Move_End.wav)

Un'interazione di **disegno** deve avere un suono persistente di ciclo, che ha un volume controllato dallo spostamento della mano dell'utente, in modo che sia completamente invisibile quando la mano dell'utente è ancora e al volume massimo quando la mano dell'utente si sposta rapidamente.



### <a name="voice-interactions"></a>Interazioni vocali
Le interazioni vocali hanno spesso elementi visivi sottili. Rafforzare le fasi di interazione utilizzando i suoni. Prendere in considerazione la possibilità di scegliere più suoni tonali per distinguerli da movimenti e suoni di manipolazione diretta.

* Usare un segnale acustico positivo per le **conferme**dei comandi vocali. In questo, i toni crescenti e gli intervalli musicali principali sono effettivi.
* Usare un segnale acustico più breve e meno positivo per l' **errore**del comando vocale. Evitare i suoni negativi; usare invece un suono più a percussione, neutro per comunicare che l'applicazione sta procedendo dall'interazione.
* Se l'applicazione usa una parola di riattivazione, usare un tono breve e gentile quando il dispositivo ha **iniziato l'ascolto**e un suono di loop delicato mentre l'applicazione è in ascolto. 

### <a name="notifications"></a>Notifications
Le notifiche comunicano le modifiche dello stato dell'applicazione e altri eventi non avviati dall'utente, ad esempio i completamenti del processo, i messaggi e le chiamate.

In realtà mista, gli oggetti spostati possono uscire dal campo di visualizzazione dell'utente. Accompagna **gli oggetti animati** con un suono spaziale che dipende dall'oggetto e dalla velocità di movimento.
* Consente inoltre di riprodurre un suono con spazialità alla fine di un'animazione per informare l'utente della nuova posizione
* Per i movimenti graduali, un suono "fruscio" durante lo spostamento consentirà all'utente di tenere traccia dell'oggetto

È probabile che le **notifiche dei messaggi** vengano ascoltate più volte e talvolta in rapida successione. È importante che non si trovi o sia un suono troppo rigido. I suoni tonali positivi a metà intervallo sono validi qui.

* Le chiamate devono avere qualità simili a una suoneria del telefono cellulare. Si tratta in genere di frasi musicali che eseguono il ciclo fino a quando l'utente non ha risposto alla chiamata.
* La connessione e la disconnessione vocale dovrebbero avere un suono tonale breve. Il suono della connessione deve avere un tono positivo, che indica la riuscita della connessione, mentre il suono di disconnessione deve essere un suono neutro che indica il completamento della chiamata.

## <a name="spatialization"></a>Spazializzazione
La spazializzazione USA cuffie stereo o altoparlanti per inserire i suoni nel mondo misto.

### <a name="which-sounds-should-i-spatialize"></a>Quali suoni devo spatialize?
Un suono deve essere spaziali quando è associato a un evento che ha una posizione spaziale. Sono incluse l'interfaccia utente, le voci di intelligenza artificiale incarnate e gli indicatori visivi.

Gli elementi dell' **interfaccia utente** di Spatializing consentono di declutter lo spazio "Sonic" dell'utente limitando il numero di suoni stereo bloccati sulle rispettive intestazioni. In particolare, le interazioni di manipolazione diretta, il tocco, l'acquisizione e il rilascio si ritengono più naturali quando il feedback audio è spaziale. Tuttavia, vedere di seguito per l'attenuazione della distanza per questi elementi.

Spatializing gli **indicatori visivi** e le  **voci di intelligenza artificiale** in modo intuitivo informa gli utenti quando si trovano al di fuori del campo di visualizzazione.
    
Al contrario, evitare la spazializzazione per le **voci di intelligenza artificiale senza _facet_** e altri elementi senza una posizione spaziale ben definita. La spazializzazione senza un elemento visivo correlato può distrarre gli utenti nel pensiero che è presente un elemento visivo che non sono in grado di trovare.

L'aggiunta della spazializzazione prevede un costo della CPU. In molte applicazioni, al massimo, due suoni suonano simultaneamente. Il costo della spazializzazione in questo caso può essere trascurabile. È possibile utilizzare il monitoraggio della frequenza dei fotogrammi MRTK per valutare l'effetto dell'aggiunta della spazializzazione. 

### <a name="when-and-how-should-i-apply-distance-based-attenuation"></a>Quando e come si applica l'attenuazione basata sulla distanza?
Nel mondo fisico, i suoni più lontani sono più tranquilli. Il motore audio può modellare questa attenuazione in base alla distanza di origine. Utilizzare l'attenuazione basata sulla distanza per la comunicazione di informazioni rilevanti.

Le distanze per gli **indicatori visivi**, gli **ologrammi animati**e altri suoni informativi sono in genere rilevanti per l'utente. Usare l'attenuazione basata sulla distanza per fornire in modo intuitivo questa indicazione.
* Modificare la curva di attenuazione per ogni origine per adattarla alle dimensioni degli spazi globali misti. La curva predefinita del motore audio è spesso destinata a spazi di dimensioni molto grandi (fino a metà chilometro).

I suoni che rinforzano le **fasi progressive dei pulsanti** e altre interazioni non devono essere applicati all'attenuazione. Gli effetti di questi suoni sono in genere più importanti rispetto alla comunicazione della distanza al pulsante. Le variazioni possono essere distrazioni, soprattutto con le tastiere, in cui molti clic sui pulsanti verranno uditi in successione.

### <a name="which-spatialization-technology-should-i-use"></a>Quale tecnologia di spazializzazione usare?
Quando si usano le cuffie o i relatori HoloLens, usare le tecnologie di spazializzazione basate su HRTF (Head-Related Transfer Function). Modellano la propagazione del suono intorno all'intestazione nel mondo fisico. Anche quando un'origine audio si trova lungo un lato della testa, l'audio si propaga all'orecchio distanti con alcune attenuazioni e ritardo. La panoramica del relatore, al contrario, si basa solo sull'attenuazione e applica l'attenuazione totale nell'orecchio sinistro quando i suoni sono sul lato destro (e viceversa). Questo può risultare scomodo per i listener di udito normale e non accessibile per i listener con problemi di udito in un orecchio.

## <a name="next-steps"></a>Passaggi successivi
* [Usare un suono spaziale in Unity](spatial-sound-in-unity.md)
* [Case Study di Roboraid](case-study-using-spatial-sound-in-roboraid.md)
* [Case Study di HoloTour](case-study-spatial-sound-design-for-holotour.md)


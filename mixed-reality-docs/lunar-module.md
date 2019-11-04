---
title: Modulo lunare
description: LunarModule è un'app di esempio Open Source di Microsoft Mixed Reality Design Labs. Con questo progetto è possibile apprendere come estendere i movimenti di base di HoloLens con il rilevamento bidirezionale e l'input del controller Xbox, creare oggetti reattivi per il mapping di superficie e la ricerca di piani e implementare semplici sistemi di menu.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, app di esempio, progettazione, HoloLens
ms.openlocfilehash: 1df2b7e9aaf92a7045aa3c378d3029cf09e085a6
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438540"
---
# <a name="lunar-module"></a>Modulo lunare

>[!NOTE]
>Questo articolo illustra un esempio esplorativo creato nei [laboratori di progettazione della realtà mista](https://github.com/Microsoft/MRDesignLabs_Unity), un posto in cui si condividono le informazioni e suggerimenti per lo sviluppo di app di realtà miste. Gli articoli e il codice correlati alla progettazione si evolveranno Man mano che si effettuano nuove individuazioni.

Il [modulo Lunar](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule) è un'app di esempio Open Source di Microsoft Mixed Reality Design Labs. Con questo progetto è possibile apprendere come estendere i movimenti di base di HoloLens con il rilevamento bidirezionale e l'input del controller Xbox, creare oggetti reattivi per il mapping di superficie e la ricerca di piani e implementare semplici sistemi di menu. Tutti i componenti del progetto sono disponibili per l'uso nella propria esperienza di app in realtà mista.

## <a name="rethinking-classic-experiences-for-windows-mixed-reality"></a>Ripensare le esperienze classiche per la realtà mista di Windows

Nel suo ambiente, una piccola nave che ricorda il modulo Apollo analizza metodicamente il terreno frastagliato riportato di seguito. Il nostro pilota impavido è un'area di destinazione adatta. La discesa è ardua ma fortunatamente questo percorso è stato fatto più volte prima...

![interfaccia originale del](images/640px-atari-lunar-lander.png) Lunar Lander di Atari 1979<br>
*Interfaccia originale del lander lunare 1979 di Atari*

[Lunar Lander](https://en.wikipedia.org/wiki/Lunar_Lander_(1979_video_game)) è un classico arcade in cui i giocatori tentano di pilotare una luna Lander in una posizione piatta di terreno lunare. Tutti gli utenti nati negli anni '70 hanno impiegato ore in un arcade con i loro occhi incollati a questa nave vettoriale. Quando un giocatore sposta la propria spedizione verso un'area di destinazione desiderata, la scalabilità del terreno consente di visualizzare progressivamente più dettagli. Success indica l'atterraggio entro la soglia sicura della velocità orizzontale e verticale. I punti vengono assegnati per il tempo impiegato per l'atterraggio e il carburante rimanente, con un moltiplicatore in base alle dimensioni dell'area di destinazione.

Oltre al gameplay, l'era del gioco arcade ha portato a un'innovazione costante degli schemi di controllo. Dalle più semplici configurazioni di pulsanti e joystick a 4 vie (viste nell'icona [Pac-Man](https://en.wikipedia.org/wiki/Pac-Man)) agli schemi estremamente specifici e complicati rilevati negli anni '90 e 00s (come quelli dei simulatori di golf e dei tiratori). Lo schema di input usato nel computer Lunar Lander è particolarmente interessante per due motivi: limitare il fascino e l'immersione.

![la console arcade del Lander Lunar Lander](images/atariconsole.png)<br>
*Console della Galleria Lunar Lander di Atari*

Perché Atari e molte altre aziende di gioco scelgono di ripensare l'input?

Un bambino che cammina attraverso una galleria sarà naturalmente intrigante dal più recente computer sgargiante. Ma Lunar Lander presenta un nuovo meccanico di input che si è rivelato fuori dalla folla.

Lunar Lander usa due pulsanti per ruotare la nave a sinistra e a destra e una **levetta di Spinta** per controllare la quantità di spinta prodotta dalla nave. Questa leva offre agli utenti un certo livello di Finesse che non può essere fornito da un normale joystick. Si tratta anche di un componente comune ai moderni cockpit di aviazione. Atari ha voluto Lunar Lander per immergere l'utente nel sentimento che era in realtà pilota di un modulo lunare. Questo concetto è noto come " **immersione tattile**".

L'immersione tattile è l'esperienza di feedback sensoriale dall'esecuzione di azioni ripetitive. In questo caso, l'azione ripetitiva di regolazione della leva e della rotazione della limitazione che gli occhi vedono e i nostri orecchi ascoltano, aiuta a connettere il lettore all'atto di atterrare una nave sulla superficie della luna. Questo concetto può essere associato al concetto psicologico di "Flow". Quando un utente viene completamente assorbito in un'attività con la giusta combinazione di sfida e ricompensa, o più semplicemente, sono "nella zona".

Probabilmente, il tipo più importante di immersione nella realtà mista è l'immersione spaziale. L'intero punto della realtà mista consiste nel credere che questi oggetti digitali esistano nel mondo reale. Stiamo sintetizzando gli ologrammi negli ambienti, a livello spaziale in tutti gli ambienti e le esperienze. Questo non significa che non possiamo ancora impiegare altri tipi di immersione nelle nostre esperienze, proprio come Atari ha fatto con l'immersione tattile in Lunar Lander.

## <a name="designing-with-immersion"></a>Progettazione con l'immersione

In che modo è possibile applicare l'immersione tattile a un sequel aggiornato e volumetrico al classico di Atari? Prima di affrontare lo schema di input, è necessario risolvere il costrutto di gioco per lo spazio tridimensionale.

![la visualizzazione del mapping delle superfici in HoloLens](images/surfacemapping.png)<br>
*Visualizzazione del mapping spaziale in HoloLens*

Sfruttando gli ambienti di un utente, sono disponibili opzioni di terreno infinite per l'atterraggio del modulo lunare. Per rendere il gioco più simile al titolo originale, un utente potrebbe potenzialmente manipolare e collocare i riscontri di atterraggio con diverse difficoltà nell'ambiente.

![volare il modulo Lunar](images/640px-lm-hero.jpg)<br>
*Flying the Lunar Module*

Richiedere all'utente di apprendere lo schema di input, controllare la spedizione e avere una piccola destinazione su cui atterrare è molto richiesta. Un'esperienza di gioco con successo offre la giusta combinazione di sfida e premi. L'utente deve essere in grado di scegliere un livello di difficoltà, con la modalità più semplice per richiedere all'utente di atterrare correttamente in un'area definita dall'utente in una superficie analizzata da HoloLens. Una volta che un utente ha ottenuto il blocco del gioco, può quindi alzare di livello la difficoltà nel modo più appropriato.

### <a name="adding-input-for-hand-gestures"></a>Aggiunta dell'input per i movimenti della mano

L'input di base di HoloLens ha solo due movimenti: [tocco aereo e Bloom](gaze-and-commit.md#composite-gestures). Gli utenti non devono ricordare le sfumature contestuali o un elenco di movimenti specifici che rendono l'interfaccia della piattaforma sia versatile che facile da imparare. Sebbene il sistema possa esporre solo questi due movimenti, HoloLens come dispositivo è in grado di tenere traccia di due lancette contemporaneamente. Il nostro inno a Lunar Lander è un' [app immersiva](app-model.md) , che significa che abbiamo la possibilità di estendere il set di movimenti di base per sfruttare due mani e aggiungere i nostri mezzi tattili deliziosi per la navigazione dei moduli lunari.

Tornando allo schema di controllo originale, **era necessario risolvere i problemi di spinta e rotazione**. L'avvertenza è la rotazione nel nuovo contesto che aggiunge un asse aggiuntivo (tecnicamente due, ma l'asse Y è meno importante per l'atterraggio). I due movimenti di spedizione distinti si prestano naturalmente per essere mappati a ogni mano:

![toccare e trascinare movimento per ruotare il lander su tutti e tre gli assi](images/module-handdrag.gif)<br>
*Toccare e trascinare movimento per ruotare il lander su tutti e tre gli assi*

**Spinta**

La levetta sul computer arcade originale è stata mappata a una scala di valori, più alta è stata spostata, più la Spinta è stata applicata alla nave. Una sfumatura importante da sottolineare qui è che l'utente può prendere la mano del controllo e mantenere un valore desiderato. Per ottenere lo stesso risultato, è possibile usare efficacemente il comportamento di tocco e di trascinamento. Il valore di Spinta inizia da zero. L'utente tocca e trascina per aumentare il valore. A questo punto, è possibile continuare a gestirlo. Qualsiasi modifica del valore del movimento tocco e trascinamento sarà il Delta del valore originale.

**Rotazione**

Questo è un po' più complesso. Con i pulsanti "ruota" olografici per toccare Crea un'esperienza terribile. Non esiste un controllo fisico da sfruttare, quindi il comportamento deve derivare dalla manipolazione di un oggetto che rappresenta il lander o dal lander stesso. È stato creato un metodo che usa il tocco e il trascinamento, che consente a un utente di eseguire in modo efficace il push e il pull nella direzione desiderata. Ogni volta che un utente tocca e possiede, il punto nello spazio in cui è stato avviato il movimento diventa l'origine per la rotazione. Il trascinamento dall'origine converte il Delta della traslazione della mano (X, Y, Z) e lo applica al delta dei valori di rotazione del lander. O più semplicemente, *il trascinamento di sinistra <-> a destra, verso l'alto < > verso il basso, < > di nuovo negli spazi ruota la nave di conseguenza*.

Poiché il HoloLens può tenere traccia di due mani, la rotazione può essere assegnata a destra mentre la spinta viene controllata da sinistra. Finesse è il fattore determinante per il successo in questo gioco. L' *aspetto* di queste interazioni è la massima priorità assoluta. In particolare nel contesto dell'immersione tattile. Una nave che reagisce troppo rapidamente potrebbe essere inutilmente difficile da gestire, mentre un tempo troppo lento richiederebbe che l'utente "push e pull" sulla nave per un periodo di tempo molto lungo.

### <a name="adding-input-for-game-controllers"></a>Aggiunta dell'input per i controller di gioco

Sebbene i movimenti della mano sul HoloLens forniscano un nuovo metodo di controllo granulare, c'è ancora una certa mancanza di feedback tattile "vero" ottenuto dai controlli analoghi. La connessione di un controller di gioco Xbox consente di riportare questo senso di fisici, sfruttando al tempo stesso i bastoncini di controllo per mantenere un controllo accurato.

Esistono diversi modi per applicare lo schema di controllo relativamente diretto al controller Xbox. Poiché si sta tentando di rimanere nel modo più vicino possibile alla configurazione del arcade originale, le mappe di **Spinta** migliorano con il pulsante trigger. Questi pulsanti sono controlli analoghi, ovvero hanno più di semplici stati *on e off* , rispondono effettivamente al grado di pressione su di essi. In questo modo si ottiene un costrutto simile a quello della **levetta di Spinta**. A differenza del gioco originale e del movimento della mano, questo controllo taglierà la spinta della nave una volta che un utente smette di esercitare pressioni sul trigger. Offre comunque all'utente lo stesso livello di raffinatezza del gioco arcade originale.

![Left levetta è mappato a imbardata e roll, viene eseguito il mapping di right levetta a Pitch and roll](images/thumbsticksidebyside.gif)<br>
*Viene eseguito il mapping di levetta a sinistra per l'imbardata e il roll; il levetta destro è mappato a Pitch and roll*

Il doppio ThumbSticks si presta naturalmente a controllare la rotazione delle spedizioni. Sfortunatamente, sono disponibili 3 assi su cui la nave può ruotare e due ThumbSticks che supportano entrambi due assi. Questa mancata corrispondenza indica che uno levetta controlla un asse; in alternativa, è presente una sovrapposizione di assi per ThumbSticks. La soluzione precedente si è risentita "Broken" poiché ThumbSticks incorporava intrinsecamente i valori X e Y locali. La seconda soluzione richiedeva alcuni test per individuare gli assi ridondanti che si ritengono più naturali. L'esempio finale usa l' *imbardata* e il *Roll* (assi Y e x) per la levetta sinistra e il *pitch* and *Roll* (assi Z e x) per il levetta destro. Si tratta di una cosa più naturale, perché il *Roll* sembra essere abbinato in modo indipendente con *imbardata* e *pitch*. Si noti che l'uso di entrambi ThumbSticks per *Roll* viene eseguito anche per raddoppiare il valore di rotazione. è piuttosto divertente avere i cicli del lander.

Questa app di esempio dimostra come il riconoscimento spaziale e l'immersione tattile possano modificare significativamente un'esperienza grazie alle modalità di input estendibili della realtà mista di Windows. Anche se Lunar Lander può essere prossimo a 40 anni, i concetti esposti con tale piccolo ottagono con le gambe rimarranno sempre attivi. Quando si immagina il futuro, perché non esaminare il passato?

## <a name="technical-details"></a>Dettagli tecnici

È possibile trovare script e prefabbricati per l'app di esempio Lunar Module in [mixed really design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule).

## <a name="about-the-author"></a>Informazioni sull'autore

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Addison Linville" width="60" height="60" src="images/addisonlinville-tile-60px.jpg"></td>
<td style="border-style: none"><b>Addison Linville</b><br>Progettazione UX @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Vedi anche
* [Controller del movimento](motion-controllers.md)
* [Puntamento con la testa e commit](gaze-and-commit.md)
* [Tipi di app di realtà mista](types-of-mixed-reality-apps.md)

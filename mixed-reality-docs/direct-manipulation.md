---
title: Manipolazione diretta
description: Panoramica del modello di input di manipolazione diretta
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
keywords: Mista realtà, sguardo, sguardo targeting, interazione, progettazione
ms.openlocfilehash: d855955d44c1cf074849992e5dd7b36b54675fdd
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2019
ms.locfileid: "64581331"
---
# <a name="direct-manipulation"></a>Manipolazione diretta
Manipolazione diretta è un modello di input che coinvolge tocca vntana direttamente con le mani. L'obiettivo con manipolazione diretta è che gli oggetti si comportano come avviene nel mondo reale. Pulsanti possono essere attivati semplicemente premendo li, gli oggetti possono essere selezionati da essi selezionandola e contenuto 2D si comporta come un touchscreen virtuale.  Per questo motivo, è facile per gli utenti per altre manipolazione diretta, e il relativo divertimento troppo.  Viene considerato un "near" modello di input, vale a dire che viene utilizzato meglio per l'interazione con contenuto che è all'interno di arms raggiungere.

Un elemento fondamentale che rende facile da imparare manipolazione diretta è che è basato su intuitività. Non esistono Nessun movimenti simbolici per insegnare agli utenti. Tutte le interazioni devono essere create in un elemento visivo che può essere modificato o afferrato.

## <a name="device-support"></a>Supporto di dispositivi

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Modello di input</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (dal 1 ° generazione)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Auricolari coinvolgenti</strong></a></td>
    </tr>
     <tr>
        <td>Manipolazione diretta (accanto all'interazione manuale)</td>
        <td>❌ Non supportato</td>
        <td>✔️ Consigliato</td>
        <td>Un'opzione alternativa ➕ ma <a href="point-and-commit.md">punto ed eseguire il commit (distante interazione)</a> è consigliato</td>
    </tr>
</table>

Manipolazione diretta è un modello di input primario su HoloLens 2, che usano l'icona della mano articolati e nuovo sistema di registrazione. Il modello di input è disponibile anche su immersive auricolari tramite l'uso di controller di movimento, ma è consigliabile non significa che una replica primaria di interazione all'esterno di manipolazione dell'oggetto.  Manipluation diretto non è disponibile nella versione 1 di HoloLens.

## <a name="collidable-fingertip"></a>Collidable punta del dito
In 2 HoloLens, mani reale dell'utente vengono riconosciute e interpretate come i modelli di base di sinistra e a destra. Per implementare l'idea di toccare vntana direttamente con le mani, in teoria, 5 colliders può essere collegato a 5 disposizione di ogni modello di base di mano. Tuttavia, in pratica, a causa della mancanza di feedback tattili, disposizione collidable 10 causano un numero elevato di collisioni impreviste e imprevedibili con vntana. Di conseguenza, è consigliabile per inserire solo un collider su ogni dito indice. L'indice collidable disposizione comunque possono essere utilizzato come punti di tocco attivo per i movimenti di tocco diversi che includono altre dita, ad esempio la pressione di un 1 dito, 1 dito tocca, 2 dito premere e 5 con un dito.

![Immagine di collidable punta del dito](images/Collidable-Fingertip-720px.jpg)<br>

### <a name="sphere-collider"></a>Collider sfera
Invece di usare la forma generica casuale, è consigliabile usare un collider sfera e per eseguire il rendering in modo che fornisca segnali migliore per specificare come destinazione più vicino. Diametro della sfera deve corrispondere allo spessore del dito indice per aumentare l'accuratezza di tocco. Sarà facile recuperare la variabile dello spessore di un dito chiamando le API disponibili.

<br>

### <a name="fingertip-cursor"></a>Cursore punta del dito
Oltre a eseguire il rendering di una sfera collidable sulla punta del dito indice, creiamo un soluzioni avanzamento, cursore punta del dito, per ottenere migliori quasi esperienza destinata a in modo interattivo. Si tratta di un cursore di forma di grafico ad anello collegato nella punta del dito indice. In base alla prossimità, in modo dinamico reagisce a una destinazione in termini di orientamento e la dimensione come indicato di seguito:
* Quando si sposta un dito indice verso ologramma, il cursore è sempre parallelo nell'area della finestra di ologrammi e gradualmente ridotta di conseguenza le dimensioni. 
* Non appena il dito tocca l'area, il cursore si riduce in un punto e genera un evento di tocco.

<br> Con il feedback interattivo, raggiungere ad alta precisione quasi come attività, ad esempio l'attivazione di un collegamento ipertestuale in un contenuto web o premendo un pulsante di destinazione. <br>

![Immagine del cursore punta del dito](images/Fingertip-Cursor-720px.jpg)<br>

## <a name="bounding-box-with-proximity-shader"></a>Rettangolo di selezione con shader prossimità
Ologramma stesso richiede anche per fornire commenti e suggerimenti audio e video per compensare la mancanza di feedback tattili. A tal fine, viene generata il concetto del rettangolo con shader prossimità. Un rettangolo di selezione è un'area volumetrici minime che racchiude un oggetto 3D. Il rettangolo di selezione è un meccanismo di rendering interattiva denominato shader prossimità. Lo shader prossimità si comporta come indicato di seguito:

* Una volta il dito indice all'interno di un intervallo, viene eseguito il cast di un riflettore punta del dito sulla superficie del rettangolo di selezione. 
* Quando la punta del dito ottiene più vicino all'area, il riflettore condensa conseguenza. 
* Non appena la punta del dito tocca l'area, l'intero rettangolo di selezione cambia il colore o generare effetto visivo per riflettere lo stato di tocco. 
* Nel frattempo, è possibile attivare un effetto per migliorare il feedback dell'input tocco visual.

![Rettangolo di selezione con immagine di shader di prossimità](images/Bounding-Box-With-Proximity-Shader-720px.jpg)<br>

## <a name="pressable-button"></a>Pulsante pressable
Con punta del dito collidable, gli utenti sono ora pronti per interagire con il componente fondamentale holographic dell'interfaccia utente, pulsante pressable. Un pulsante pressable è un pulsante holographic su misura della pressione diretto con un dito. Anche in questo caso, a causa della mancanza di feedback tattili, un pulsante pressable fornisce due meccanismi per affrontare feedback tattili problemi correlati. 
* Il primo meccanismo è rettangolo con shader di prossimità, che sia già stato indirizzato nel paragrafo precedente. Serve a offrire idea più accurata della prossimità agli utenti di affrontare e rendere in contatto con un pulsante. 
* Il secondo è calo. Crea assimilata press, dopo la punta del dito contatta il pulsante. Il meccanismo è che il pulsante Sposta strettamente con la punta del dito lungo l'asse di profondità. Il pulsante può essere attivato non appena raggiunge una profondità designata (al clic del mouse) o lasciando la profondità (nel rilascio) dopo transita attraverso di esso. 
* L'effetto audio deve essere aggiunti per migliorare i commenti e suggerimenti, quando viene attivato il pulsante. 

![Immagine del pulsante pressable](images/Pressable-Button-720px.jpg)<br>

## <a name="2d-slate-interaction"></a>Interazione dello slate 2D
Uno slate 2D è un contenitore holographic hosting di contenuto dell'app 2D, ad esempio web browser. Il concetto di progettazione per l'interazione con uno slate 2D tramite manipolazione diretta consiste nello sfruttare il modello mentale di interagire con un touchscreen fisico.<br> <br>
Per l'interazione con il contatto dello slate:<br> 
* Gli utenti usano un dito indice di premere un pulsante o un collegamento ipertestuale. 
* Gli utenti utilizzano un dito indice su e giù per scorrere un contenuto dello slate. 
* Gli utenti di usare due dita di indice per fare zoom avanti e indietro il contenuto dello slate in base al relativo movimento della dita. 
![Immagine dello slate 2D](images/2D-Slate-Interaction-720px.jpg)<br>

<br>Per la manipolazione 2D ardesia stesso:<br>
* Gli utenti si avvicina le mani verso angoli e archi per rivelare i più vicino affordance di manipolazione. 
* Utilizzando i affordance manipolazione, gli utenti possono eseguire la scalabilità uniforme tramite affordnaces l'angolo e ridisporre tramite i affordance edge. 
* Cattura la holobar nella parte superiore dello slate 2D possono utenti spostare lo slate intero.<br><br>

![Immagine di manipolazione dello slate](images/Manipulate-2d-slate-720px.jpg)


## <a name="3d-object-manipulation"></a>Modifica di oggetti 3D
In 2 HoloLens, gli utenti vengono abilitati per utilizzare le mani direct modificare oggetti 3D hologramphic applicando un rettangolo a ogni oggetto 3D. Il riquadro delimitatore fornisce migliori percezione di profondità tramite relativo shader prossimità. Con il rettangolo di selezione, esistono due approcci di progettazione per la manipolazione dell'oggetto 3D:      
### <a name="affordance-based-manipulation"></a>Intuitività basato su Modifica:
È un modo per gli utenti modificare l'oggetto 3D tramite la affordance manipolazione intorno a esso e finestra di delimitazione. Come parte dell'utente è vicino a un oggetto 3D, il rettangolo di selezione e il più vicino intuitività sono rivelati. Gli utenti possono recuperare il rettangolo di selezione per spostare l'intero oggetto, i affordance edge la rotazione e di coner affordance ridimensionare in modo uniforme.<br>

![Immagine di manipolazione di oggetti 3D](images/3D-Object-Manipulation-720px.jpg)<br>

### <a name="non-affordance-based-manipulation"></a>Non-intuitività basato su Modifica:
In questo mechanisom, nessun intuitività è associato il riquadro delimitatore. Gli utenti possono solo visualizzare il riquadro delimitatore, quindi interagire direttamente con esso. Se il rettangolo di selezione dell'acquisizione con una mano, sono associati allo spostamento e l'orientamento della mano la traslazione e rotazione dell'oggetto. Quando l'oggetto è stato afferrato con due mani, gli utenti possono tradurre, ridimensionare e ruotarla in base al relativi movimenti di due mani.<br><br> 

<br><br>
Per la modifica richiede la precisione, è consigliabile manipolazione afforance basata, che fornisce elevata a livello di granularità. Per una modifica flessibile, non intuitività manipolazione sarà un'ottima scelta, offrendo esperienze immediate e circondandole agli utenti.


## <a name="instinctual-gestures"></a>Movimenti instinctual
A differenza di HoloLens (dal 1 ° generazione), gli utenti per l'insegnamento predefinito di un paio movimenti, ad esempio Bloom e tocca Air, HoloLens 2, non chiediamo agli utenti di memorizzare qualsiasi movimento simbolico. Tutti i movimenti che gli utenti necessari per l'interazione con ologrammi e il contenuto sono instinctual. Il modo per ottenere instinctual movimento è per guidare gli utenti per eseguire i movimenti tramite la progettazione di affordance dell'interfaccia utente. Ad esempio, se si consiglia agli utenti di quadratini di ridimensionamento un oggetto o un punto di controllo con zoom indietro di due dita, l'oggetto o il punto di controllo deve essere piccolo. Se si desidera agli utenti di eseguire cinque quadratini di ridimensionamento di un dito, l'oggetto o il punto di controllo deve essere relativamente grande. Analogamente ai pulsanti, un piccolo pulsante limiterebbe agli utenti di premere con un singolo dito, mentre un enorme pulsante verrebbe incoraggiare gli utenti a premerlo con le mani.
![](images/Instinctual-Gestures-720px.jpg)<br>

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a>Progettazione simmetrica tra le mani e controller i gradi di libertà 6
Si è notato che ora sono presenti parallels interazione che è possibile trarre tra le mani nel controller AR e movimento in realtà virtuale. Entrambi gli input possono essere utilizzati per avviare manipolazioni dirette nei loro rispettivi ambienti. In 2 HoloLens, selezionandola e trascinando con le mani una distanza Chiudi Works gran parte nello stesso modo come pulsante di quadratini di ridimensionamento non sui controller di movimento in WMR. Ciò fornisce agli utenti la conoscenza di interazione tra le due piattaforme e possa rivelarsi utile se si dovesse decide di convertire la tua app da uno a altro.

## <a name="optimizing-with-eye-tracking"></a>L'ottimizzazione con sotto controllo di rilevamento
Manipolazione diretta può risultare magici se funziona come previsto, ma può anche risultare frustrante se non è non possibile spostare più la mano ovunque senza attivare involontariamente ologramma.
Sotto controllo di rilevamento può potenzialmente offrire una migliore identificazione che cos'è l'intenzione dell'utente. 

* **Quando**: Ridurre negando quindi attivare una risposta di manipolazione. Occhio rilevamento consente di comprendere meglio ciò che un utente attualmente occupato con. Si supponga, ad esempio, che si legge un testo (filmato) holographic quando raggiungono oltre per ricavare è lo strumento di lavoro reali.
In questo modo, la mano accidentalmente spostare tra alcuni pulsanti holographic interattivi che non l'aveste notato anche prima di grande successo (forse che era ancora di fuori della visualizzazione dell'utente di campi).
In breve: Se l'utente non è stato esaminato ologramma per un periodo di tempo, ma è stato rilevato un evento touch o. é quindi per tale, è probabile che l'utente non è stato effettivamente prendendo in considerazione interagire con tale ologramma. 

* **Quello che**: Oltre all'indirizzamento false attivazioni positive, un altro esempio include una migliore identificazione quali vntana per ottenere o guardarsi come il punto di intersezione preciso potrebbe non essere chiaro da una prospettiva locale soprattutto se viene posizionati vntana più vicine Altro. Mentre rilevamento occhio su HoloLens 2 ha una limitazione di determinate in modo accurato sulla può determinare dell'occhio sguardo, questa può comunque essere molto utile per quasi interazioni a causa dell'eterogeneità profondità durante l'interazione con mano di input. Ciò significa che talvolta è difficile determinare se la mano dietro o davanti ologramma precisamente ottenere, ad esempio un widget di manipolazione.

 * **La posizione in cui**: Usa informazioni relative a ciò che un utente sta guardando i movimenti generando un'eccezione rapidi. Afferrare ologramma e metterla approssimativamente verso la destinazione prevista. Sebbene questo approccio potrebbe talvolta funzionare correttamente, eseguire rapidamente i movimenti della mano può comportare destinazioni estremamente imprecise.
Si tratta in cui sotto controllo di rilevamento può essere utile per informazioni sull'icona della mano generazione vettore nuovamente nella posizione desiderata.

## <a name="see-also"></a>Vedere anche
* [Sguardo ed eseguire il commit](gaze-and-commit.md)
* [Punto e commit](point-and-commit.md)
* [Concetti fondamentali delle interazioni](interaction-fundamentals.md)


---
title: Manipolazione diretta con le mani
description: Panoramica del modello di input di manipolazione diretta
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mista realtà, sguardo, sguardo targeting, interazione, progettare, mani near, HoloLens
ms.openlocfilehash: 6e3512eab4070680c48ee8e95240a17e9925822f
ms.sourcegitcommit: 5b4292ef786447549c0199003e041ca48bb454cd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/30/2019
ms.locfileid: "66402388"
---
# <a name="direct-manipulation-with-hands"></a>Manipolazione diretta con le mani
Manipolazione diretta è un modello di input che coinvolge tocca vntana direttamente con le mani. L'obiettivo con manipolazione diretta è che gli oggetti si comportano come avviene nel mondo reale. Pulsanti possono essere attivati semplicemente premendo li, gli oggetti possono essere selezionati da essi selezionandola e contenuto 2D si comporta come un touchscreen virtuale.  Per questo motivo, è facile per gli utenti per altre manipolazione diretta, e il relativo divertimento troppo.  Viene considerato un "near" modello di input, vale a dire che viene utilizzato meglio per l'interazione con contenuto che è all'interno di arms raggiungere.

Manipolazione diretta è basato su intuitività, vale a dire è facili da usare. Non esistono Nessun movimenti simbolici per insegnare agli utenti. Tutte le interazioni vengono compilate intorno a un elemento visivo che è possibile toccare o selezionare.

## <a name="device-support"></a>Supporto di dispositivi


| Modello di input | [HoloLens (dal 1 ° generazione)](hololens-hardware-details.md) | HoloLens 2 |[Auricolari coinvolgenti](immersive-headset-hardware-details.md)|
|:-------- | :-------| :--------| :------------|
| Manipolazione diretta con le mani | ❌ Non supportato | ✔️ Consigliato | ➕ Un'alternativa [punto ed eseguire il commit con le mani](point-and-commit.md) è consigliato.

Manipolazione diretta è un modello di input primario per HoloLens 2 e utilizza il nuovo sistema di rilevamento delle modifiche manuale articolato. Il modello di input è disponibile anche su immersive auricolari tramite l'uso di controller di movimento, ma non è consigliato come mezzo principale per l'interazione di fuori di manipolazione dell'oggetto.  Indirizzare manipluation non è disponibile in HoloLens (dal 1 ° generazione).


## <a name="collidable-fingertip"></a>Collidable punta del dito

In 2 HoloLens, mani reale dell'utente vengono riconosciute e interpretate come i modelli di base di sinistra e a destra. Per implementare l'idea di toccare vntana direttamente con le mani, in teoria, 5 colliders può essere collegato a 5 disposizione di ogni modello di base di mano. Tuttavia, in pratica, a causa della mancanza di feedback tattili, 10 disposizione collidable causato conflitti imprevisti e imprevedibili con vntana. 

Di conseguenza, è consigliabile per inserire solo un collider su ogni dito indice. La portata di mano indice collidable ancora può servire come punti di tocco attivo per i movimenti di tocco diversi che includono altre dita, ad esempio premere 1 dito, 1 dito toccare, premere un dito 2 e 5 dito, come illustrato nell'immagine seguente.

![Immagine di collidable punta del dito](images/Collidable-Fingertip-720px.jpg)

### <a name="sphere-collider"></a>Collider sfera

Invece di usare una forma generica casuale, è consigliabile usare un collider sfera e per eseguire il rendering in modo che fornisca segnali migliore per specificare come destinazione più vicino. Diametro della sfera deve corrispondere allo spessore del dito indice per aumentare l'accuratezza di tocco. Sarà facile recuperare la variabile dello spessore di un dito chiamando le API disponibili.

### <a name="fingertip-cursor"></a>Cursore punta del dito

Oltre a eseguire il rendering di una sfera collidable sulla punta del dito indice, abbiamo creato una soluzione avanzata, cursore punta del dito, per ottenere la migliore esperienza in prossimità di multitargeting in modo interattivo. Si tratta di un cursore a forma di grafico ad anello collegato nella punta del dito indice. In base alla prossimità, in modo dinamico reagisce a una destinazione in termini di orientamento e dimensioni come indicato di seguito:

* Quando si sposta un dito indice verso ologramma, il cursore è sempre alla superficie del ologrammi e gradualmente ridotta di conseguenza le dimensioni.
* Non appena il dito tocca l'area, il cursore si riduce in un punto e genera un evento di tocco.

Con il feedback interattivo, raggiungere ad alta precisione prossimità destinazione attività, ad esempio l'attivazione di un collegamento ipertestuale nel contenuto web o premendo un pulsante, come illustrato, di seguito. 

![Immagine del cursore punta del dito](images/Fingertip-Cursor-720px.jpg)

## <a name="bounding-box-with-proximity-shader"></a>Rettangolo di selezione con shader prossimità

Ologramma stesso richiede anche la possibilità di fornire commenti e suggerimenti audio e video per compensare la mancanza di feedback tattili. A tal fine, viene generata il concetto di un rettangolo con shader prossimità. Un rettangolo di selezione è una superficie volumetrica minima che racchiude un oggetto 3D. Il rettangolo di selezione è un meccanismo di rendering interattiva denominato shader prossimità. Il comportamento dello shader prossimità:

* Una volta il dito indice all'interno di un intervallo, viene eseguito il cast di un riflettore punta del dito sulla superficie del rettangolo di selezione.
* Quando la punta del dito ottiene più vicino all'area, il riflettore condensa conseguenza.
* Non appena la punta del dito tocca l'area, l'intero rettangolo di selezione cambia il colore o generare effetto visivo per riflettere lo stato di tocco.
* Nel frattempo, è possibile attivare un effetto per migliorare il feedback dell'input tocco visual.

![Rettangolo di selezione con immagine di shader di prossimità](images/Bounding-Box-With-Proximity-Shader-720px.jpg)

## <a name="pressable-button"></a>Pulsante pressable

Con punta del dito collidable, gli utenti sono ora pronti per interagire con il componente fondamentale holographic dell'interfaccia utente, pulsante pressable. Un pulsante pressable è un pulsante holographic su misura della pressione diretto con un dito. A causa della mancanza di feedback tattili, anche in questo caso, un pulsante pressable fornisce due meccanismi per affrontare problemi tattili correlate a commenti e suggerimenti.

* Il primo meccanismo è un rettangolo con shader di prossimità, descritta in dettaglio nella sezione precedente. Serve a offrire idea più accurata della prossimità agli utenti di affrontare e rendere in contatto con un pulsante.
* Il secondo è calo. Crea assimilata press, dopo la punta del dito contatta il pulsante. Il meccanismo è che il pulsante Sposta strettamente con la punta del dito lungo l'asse di profondità. Il pulsante può essere attivato quando raggiunge una profondità designata (al clic del mouse) o lascia la profondità (nel rilascio) dopo il passaggio attraverso di esso.
* L'effetto audio deve essere aggiunti per migliorare i commenti e suggerimenti, quando viene attivato il pulsante.

![Immagine del pulsante pressable](images/Pressable-Button-720px.jpg)

## <a name="2d-slate-interaction"></a>Interazione dello slate 2D

Uno slate 2D è un contenitore holographic hosting di contenuto dell'app 2D, ad esempio web browser. Il concetto di progettazione per l'interazione con uno slate 2D tramite manipolazione diretta consiste nello sfruttare il modello mentale di interagire con un touchscreen fisico.

Per interagire con il contatto dello slate:

* Usare un dito indice di premere un pulsante o un collegamento ipertestuale.
* Usare un dito indice su e giù per scorrere un contenuto dello slate.
* Gli utenti di usare due dita di indice per fare zoom avanti e indietro il contenuto dello slate in base al relativo movimento della dita.

![Immagine dello slate 2D](images/2D-Slate-Interaction-720px.jpg)

Per la manipolazione 2D ardesia stesso:

* Approccio le mani verso angoli e archi per rivelare i più vicino affordance di manipolazione.
* Scarica affordance la manipolazione ed eseguire la scalabilità uniforme tramite affordance l'angolo e ridisporre tramite i affordance edge.
* Scarica il holobar nella parte superiore dello slate 2D, che consente di spostare lo slate intero.

![Immagine di manipolazione dello slate](images/Manipulate-2d-slate-720px.jpg)

## <a name="3d-object-manipulation"></a>Modifica di oggetti 3D

HoloLens 2 consente consente agli utenti di abilitare le mani indirizzare manipolare gli oggetti 3D hologramphic applicando un rettangolo a ogni oggetto 3D. Il riquadro delimitatore fornisce migliori percezione di profondità tramite relativo shader prossimità. Con il rettangolo di selezione, esistono due approcci di progettazione per la manipolazione dell'oggetto 3D.

### <a name="affordance-based-manipulation"></a>Basato su intuitività manipulation

Ciò consente di modificare l'oggetto 3D tramite un rettangolo di selezione e la affordance manipolazione intorno a esso. Come parte dell'utente è vicino a un oggetto 3D, il rettangolo di selezione e il più vicino intuitività sono rivelati. Gli utenti possono recuperare il rettangolo di selezione per spostare l'intero oggetto, i affordance edge per ruotare e affordance l'angolo per ridimensionare in modo uniforme.

![Immagine di manipolazione di oggetti 3D](images/3D-Object-Manipulation-720px.jpg)

### <a name="non-affordance-based-manipulation"></a>Manipolazione di base non intuitività

In questo meccanismo, non è associato alcun intuitività per il rettangolo di selezione. Gli utenti possono solo visualizzare il riquadro delimitatore, quindi interagire direttamente con esso. Se il rettangolo di selezione dell'acquisizione con una mano, sono associati allo spostamento e l'orientamento della mano la traslazione e rotazione dell'oggetto. Quando l'oggetto è stato afferrato con due mani, gli utenti possono tradurre, ridimensionare e ruotarla in base al relativi movimenti di due mani.

Richiede una modifica specifica precisione, si consiglia di usare **basato su intuitività manipolazione**, poiché offre un elevato livello di granularità. Per una modifica flessibile, è consigliabile utilizzi **manipolazione non intuitività** è poiché consente l'immediata e circondandole esperienze.

## <a name="instinctual-gestures"></a>Movimenti instinctual

Con HoloLens (gen 1 °,), è tenuti agli utenti un paio movimenti predefiniti, ad esempio Bloom e toccare Air. Per HoloLens 2, non chiediamo agli utenti di memorizzare tutti i movimenti simbolici. Tutti i movimenti richiesto all'utente, gli utenti devono interagire con ologrammi e il contenuto sono instinctual. Il modo per ottenere instinctual movimento è per guidare gli utenti per eseguire i movimenti tramite la progettazione di affordance dell'interfaccia utente.

Ad esempio, se si consiglia di quadratini di ridimensionamento un oggetto o un punto di controllo con zoom indietro di due dita, l'oggetto o il punto di controllo deve essere piccolo. Se si desidera eseguire cinque quadratini di ridimensionamento di un dito, l'oggetto o il punto di controllo deve essere relativamente grande. Analogamente ai pulsanti, un piccolo pulsante limiterebbe agli utenti di premere con un singolo dito, mentre un enorme pulsante verrebbe incoraggiare gli utenti a premerlo con le mani.

![](images/Instinctual-Gestures-720px.jpg)

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a>Progettazione simmetrica tra le mani e controller i gradi di libertà 6

Si è notato che ora sono presenti parallels interazione che è possibile trarre tra le mani nel controller AR e movimento in realtà virtuale. Entrambi gli input possono essere utilizzati per avviare manipolazioni dirette nei loro rispettivi ambienti. In 2 HoloLens, selezionandola e trascinando con le mani una distanza Chiudi Works gran parte nello stesso modo come pulsante di quadratini di ridimensionamento non sui controller di movimento in WMR. Ciò fornisce agli utenti con conoscenza di interazione tra le due piattaforme e possa rivelarsi utile se si dovesse decide di convertire la tua app da uno a altro.

## <a name="optimize-with-eye-tracking"></a>Ottimizzare con sotto controllo di rilevamento

Manipolazione diretta può risultare magici se funziona come previsto, ma può anche risultare frustrante se non è non possibile spostare più la mano ovunque senza attivare involontariamente ologramma.
Sotto controllo di rilevamento può potenzialmente offrire una migliore identificazione che cos'è l'intenzione dell'utente.

* **Quando**: Ridurre negando quindi attivare una risposta di manipolazione. Occhio rilevamento consente di comprendere meglio ciò che un utente attualmente occupato con.
Si supponga, ad esempio, che si legge un testo (filmato) holographic quando raggiungono oltre per ricavare è lo strumento di lavoro reali.

In questo modo, si sposta accidentalmente la mano tra alcuni pulsanti holographic interattivi che non l'aveste notato anche prima di grande successo (forse che era ancora di fuori campo-di-visualizzazione () dell'utente).

  In breve: Se l'utente non è stato esaminato ologramma per un periodo di tempo, ma è stato rilevato un evento touch o. é quindi per tale, è probabile che l'utente non è stato effettivamente prendendo in considerazione interagire con tale ologramma.

* **Quello che**:  Oltre all'indirizzamento false attivazioni positive, un altro esempio include una migliore identificazione quali vntana per ottenere o guardarsi come il punto di intersezione preciso potrebbe non essere chiaro da una prospettiva locale soprattutto se viene posizionati vntana più vicine Altro.

  Mentre rilevamento occhio su HoloLens 2 ha una limitazione di determinate in modo accurato sulla può determinare dell'occhio sguardo, questa può comunque essere molto utile per quasi interazioni a causa dell'eterogeneità profondità durante l'interazione con mano di input.  Ciò significa che talvolta è difficile determinare se la mano dietro o davanti ologramma precisamente ottenere, ad esempio un widget di manipolazione.

* **La posizione in cui**: Usare informazioni su ciò che l'utente viene analizzato i movimenti di quick - generando un'eccezione. Afferrare ologramma e metterla approssimativamente verso la destinazione prevista.  

    Anche se questa situazione può verificarsi a volte funziona correttamente, in modo rapido eseguendo i movimenti della mano può comportare destinazioni estremamente imprecise. Si tratta in cui sotto controllo di rilevamento può essere utile per informazioni sull'icona della mano generazione vettore nuovamente nella posizione desiderata.

## <a name="see-also"></a>Vedere anche

* [Puntamento con la testa e commit](gaze-and-commit.md)
* [Puntamento e commit con le mani](point-and-commit.md)
* [Interazioni istintive](interaction-fundamentals.md)


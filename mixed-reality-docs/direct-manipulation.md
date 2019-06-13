---
title: Manipolazione diretta con le mani
description: Panoramica del modello di input manipolazione diretta
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
ms.localizationpriority: high
keywords: realtà mista, sguardo fisso, selezione della destinazione con lo sguardo, interazione, progettazione, a portata di mano, HoloLens
ms.openlocfilehash: 6e3512eab4070680c48ee8e95240a17e9925822f
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2019
ms.locfileid: "66402388"
---
# <a name="direct-manipulation-with-hands"></a>Manipolazione diretta con le mani
La manipolazione diretta è un modello di input che consiste nel toccare gli ologrammi direttamente con le mani. Con la manipolazione diretta gli oggetti si comportano esattamente come nel mondo reale. I pulsanti possono essere attivati semplicemente premendoli, gli oggetti possono essere selezionati afferrandoli e il contenuto 2D si comporta come un touchscreen virtuale.  Per questo motivo, è facile e anche divertente per gli utenti imparare a usare la manipolazione diretta.  Viene considerata un modello di input "da vicino", in quanto permette di interagire con contenuto raggiungibile stendendo le braccia.

La manipolazione diretta è basata sull'invito, ovvero è facile da usare. Non esistono movimenti simbolici da insegnare agli utenti. Tutte le interazioni avvengono intorno a un elemento visivo che è possibile toccare o afferrare.

## <a name="device-support"></a>Supporto di dispositivi


| Modello di input | [HoloLens (prima generazione)](hololens-hardware-details.md) | HoloLens 2 |[Visori VR immersive](immersive-headset-hardware-details.md)|
|:-------- | :-------| :--------| :------------|
| Manipolazione diretta con le mani | ❌ Non supportata | ✔️ Consigliata | ➕ È consigliabile un'alternativa, [puntamento e commit con le mani](point-and-commit.md).

La manipolazione diretta è il modello di input principale in HoloLens 2 e usa il nuovo sistema di tracciamento delle mani articolate. Il modello di input è disponibile anche su visori VR immersive tramite l'uso di controller del movimento, ma non è consigliato come mezzo principale di interazione al di fuori della manipolazione di oggetti.  La manipolazione diretta non è disponibile in HoloLens (prima generazione).


## <a name="collidable-fingertip"></a>Punta del dito di collisione

In HoloLens 2 le mani reali dell'utente vengono riconosciute e interpretate come modelli scheletrici delle mani sinistra e destra. Per implementare l'idea di toccare gli ologrammi direttamente con le mani, avrebbero potuto essere applicati idealmente cinque collisori alle cinque punte delle dita del modello scheletrico di ogni mano. Tuttavia, nella pratica, a causa della mancanza di feedback tattili, 10 punte di dita di collisione hanno causato collisioni inaspettate e imprevedibili con gli ologrammi. 

Di conseguenza, è consigliabile applicare solo un collisore a ogni dito indice. Le punte degli indici di collisione possono comunque servire come punti di tocco attivo per i diversi movimenti di tocco che prevedono l'uso di altre dita, ad esempio la pressione con un dito, il tocco con un dito, la pressione con due dita e la pressione con cinque dita, come illustrato nell'immagine seguente.

![Immagine della punta del dito di collisione](images/Collidable-Fingertip-720px.jpg)

### <a name="sphere-collider"></a>Collisore sfera

Invece di usare una forma generica casuale, è consigliabile usare un collisore sfera ed eseguirne il rendering visivo in modo da fornire indicazioni migliori per la selezione della destinazione da vicino. Il diametro della sfera deve corrispondere allo spessore del dito indice per aumentare l'accuratezza del tocco. Sarà facile recuperare la variabile dello spessore di un dito chiamando l'API relativa alla mano.

### <a name="fingertip-cursor"></a>Cursore punta del dito

Oltre a eseguire il rendering di una sfera di collisione sulla punta dell'indice, abbiamo creato una soluzione avanzata, ovvero un cursore punta del dito, per ottenere un'esperienza di selezione ottimale della destinazione da vicino in modo interattivo. Si tratta di un cursore a forma di anello associato alla punta dell'indice. In base alla prossimità, reagisce in modo dinamico a una destinazione in termini di orientamento e dimensioni come indicato di seguito:

* Quando sposti un indice verso un ologramma, il cursore è sempre parallelo alla superficie dell'ologramma e si restringe gradualmente.
* Non appena il dito tocca la superficie, il cursore si riduce a un punto ed emette un evento tocco.

Con il feedback interattivo, gli utenti possono eseguire attività di selezione della destinazione da vicino ad alta precisione, ad esempio l'attivazione di un collegamento ipertestuale in contenuto Web o la pressione di un pulsante, come illustrato di seguito. 

![Immagine del cursore punta del dito](images/Fingertip-Cursor-720px.jpg)

## <a name="bounding-box-with-proximity-shader"></a>Cubo di delimitazione con shader prossimità

L'ologramma stesso richiede anche la possibilità di fornire feedback audio e video per compensare la mancanza di feedback tattili. Su questa esigenza si basa il concetto di cubo di delimitazione con shader prossimità. Un cubo di delimitazione è un'area volumetrica minima che racchiude un oggetto 3D. Il cubo di delimitazione è dotato di un meccanismo di rendering interattivo denominato shader prossimità. Comportamento dello shader prossimità:

* Quando l'indice è all'interno della portata, sulla superficie del cubo di delimitazione viene messo in evidenza un punto per la punta del dito.
* Man mano che la punta del dito si avvicina alla superficie, la luminosità del punto si intensifica.
* Non appena la punta del dito tocca la superficie, l'intero cubo di delimitazione cambia colore o genera un effetto visivo per riflettere lo stato di tocco.
* Nel frattempo, è possibile attivare un effetto sonoro per migliorare il feedback del tocco visivo.

![Immagine del cubo di delimitazione con shader prossimità](images/Bounding-Box-With-Proximity-Shader-720px.jpg)

## <a name="pressable-button"></a>Pulsante a pressione

Dotati di punta del dito di collisione, gli utenti sono ora pronti per interagire con il componente dell'interfaccia utente olografica di base, ovvero il pulsante a pressione. Un pulsante a pressione è un pulsante olografico personalizzato per la pressione diretta con un dito. Anche in questo caso, a causa della mancanza di feedback tattili, un pulsante a pressione è dotato di un paio di meccanismi per ovviare ai problemi correlati al feedback tattile.

* Il primo meccanismo è un cubo di delimitazione con shader prossimità, descritto in dettaglio nella sezione precedente. Serve per fornire un'idea di prossimità più accurata e consentire agli utenti di avvicinarsi ed entrare in contatto con un pulsante.
* Il secondo meccanismo è la pressione. Crea l'impressione della pressione dopo che la punta del dito è entrata in contatto con il pulsante. Il meccanismo funziona in modo che il pulsante si muova in stretta relazione con la pressione del dito lungo l'asse di profondità. Il pulsante può essere attivato quando raggiunge una profondità designata (alla pressione) o quando lascia la profondità (al rilascio) dopo averla attraversata.
* È consigliabile aggiungere l'effetto audio di attivazione del pulsante per migliorare il feedback.

![Immagine del pulsante a pressione](images/Pressable-Button-720px.jpg)

## <a name="2d-slate-interaction"></a>Interazione con uno slate 2D

Uno slate 2D è un contenitore olografico che ospita contenuti di app 2D, ad esempio un Web browser. Il concetto di progettazione per l'interazione con uno slate 2D tramite manipolazione diretta consiste nello sfruttare il modello mentale di interazione con un touchscreen fisico.

Per interagire con il contatto tramite slate:

* Usa un indice per premere un pulsante o un collegamento ipertestuale.
* Usa un indice per scorrere il contenuto dello slate verso l'alto o verso il basso.
* Gli utenti usano i due indici per eseguire lo zoom avanti e indietro del contenuto dello slate in base al movimento relativo delle dita.

![Immagine dello slate 2D](images/2D-Slate-Interaction-720px.jpg)

Per la manipolazione dello slate 2D stesso:

* Avvicina le mani verso angoli e i bordi per rivelare gli inviti di manipolazione più vicini.
* Afferra gli inviti di manipolazione ed esegui un ridimensionamento uniforme tramite gli inviti degli angoli e adatta il contenuto dinamicamente tramite gli inviti dei bordi.
* Afferra la barra dell'ologramma nella parte superiore dello slate 2D per spostare l'intero slate.

![Immagine di manipolazione dello slate](images/Manipulate-2d-slate-720px.jpg)

## <a name="3d-object-manipulation"></a>Manipolazione di oggetti 3D

HoloLens 2 consente agli utenti di usare le mani per manipolare direttamente gli oggetti olografici 3D applicando un cubo di delimitazione a ogni oggetto 3D. Il cubo di delimitazione fornisce una migliore percezione della profondità tramite lo shader prossimità. Con il cubo di delimitazione sono disponibili due approcci di progettazione per la manipolazione di oggetti 3D.

### <a name="affordance-based-manipulation"></a>Manipolazione basata sugli inviti

Permette di manipolare l'oggetto 3D tramite un cubo di delimitazione e gli inviti di manipolazione intorno a esso. Nel momento in cui la mano di un utente è vicina a un oggetto 3D, diventano visibili il cubo di delimitazione e l'invito più vicino. Gli utenti possono afferrare il cubo di delimitazione per spostare l'intero oggetto, gli inviti dei bordi per ruotarlo e gli inviti degli angoli per ridimensionarlo in modo uniforme.

![Immagine della manipolazione di un oggetto 3D](images/3D-Object-Manipulation-720px.jpg)

### <a name="non-affordance-based-manipulation"></a>Manipolazione non basata sugli inviti

In questo meccanismo non è associato alcun invito al cubo di delimitazione. Gli utenti possono solo visualizzare il cubo di delimitazione e quindi interagire direttamente con esso. Se il cubo di delimitazione viene afferrato con una mano, lo spostamento e la rotazione dell'oggetto sono associati al movimento e all'orientamento della mano. Quando l'oggetto viene afferrato con due mani, gli utenti possono spostarlo, ridimensionarlo e ruotarlo in base al relativi movimenti delle due mani.

Una manipolazione specifica richiede precisione. È consigliabile usare la **manipolazione basata sugli inviti**, poiché offre un elevato livello di granularità. Per una manipolazione flessibile, è consigliabile usare la **manipolazione non basata sugli inviti** poiché trasmette esperienze immediate e divertenti.

## <a name="instinctual-gestures"></a>Movimenti istintivi

Con HoloLens (prima generazione) sono stati insegnati agli utenti un paio di movimenti predefiniti, ad esempio aprire la mano a fiore e simulare il tocco. Per HoloLens 2 non viene richiesto agli utenti di memorizzare movimenti simbolici. Tutti i movimenti richiesti agli utenti per interagire con ologrammi e contenuti sono istintivi. Per ottenere il movimento istintivo è sufficiente guidare gli utenti all'esecuzione di movimenti in base a come sono progettati gli inviti dell'interfaccia utente.

Se ad esempio un oggetto o un punto di controllo deve essere afferrato avvicinando due dita, l'oggetto o il punto di controllo deve essere piccolo. Se si vuole che l'utente afferri con cinque dita, l'oggetto o il punto di controllo deve essere relativamente grande. Lo stesso vale per i pulsanti. Un piccolo pulsante indurrebbe gli utenti a premerlo con un singolo dito, mentre un grande pulsante indurrebbe gli utenti a premerlo con il palmo delle mani.

![](images/Instinctual-Gestures-720px.jpg)

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a>Progettazione simmetrica tra mani e controller 6DoF

Avrai notato che ora sono presenti simmetrie di interazione che è possibile tracciare tra le mani nella realtà aumentata (AR) e i controller del movimento nella realtà virtuale (VR). Entrambi gli input possono essere usati per avviare manipolazioni dirette nei rispettivi ambienti. In HoloLens 2 afferrare e trascinare con le mani a una distanza ravvicinata funziona praticamente come il pulsante usato per afferrare nei controller del movimento in WMR. In questo modo si offre una familiarità di interazione tra le due piattaforme che può rivelarsi utile se deciderai di convertire la tua app da una piattaforma all'altra.

## <a name="optimize-with-eye-tracking"></a>Ottimizzare con il tracciamento oculare

La manipolazione diretta può essere fantastica se funziona come previsto, ma può anche diventare frustrante se non puoi spostare la mano in una direzione qualunque un po' più del previsto senza attivare involontariamente un ologramma.
Il tracciamento oculare può aiutare a identificare meglio l'intenzione dell'utente.

* **Quando**: per ridurre l'attivazione accidentale di una risposta di manipolazione. Il tracciamento oculare consente di comprendere meglio l'attività in cui è attualmente impegnato un utente.
Supponi ad esempio di essere impegnato nella lettura di un testo olografico (istruzioni) e di sporgerti per afferrare uno strumento di lavoro del mondo reale.

In questo modo sposti accidentalmente la mano su alcuni pulsanti olografici interattivi che non avevi notato prima (forse erano anche fuori del campo visivo).

  In breve: se l'utente non ha guardato un ologramma per un periodo di tempo ma è stato rilevato un evento di tocco o cattura, è probabile che l'utente non intendesse in realtà interagire con l'ologramma.

* **Quale**:  oltre alla gestione delle attivazioni accidentali, un altro esempio include una migliore identificazione degli ologrammi da afferrare o toccare dal momento che il punto di intersezione preciso potrebbe non essere chiaro dalla tua prospettiva, soprattutto in presenza di più ologrammi ravvicinati.

  Anche se il tracciamento oculare in HoloLens 2 presenta alcuni limiti sull'accuratezza di determinazione dello sguardo, questa funzionalità può comunque essere molto utile per le interazioni da vicino a causa della disparità di profondità durante l'interazione con l'input mano.  Ciò significa che talvolta è difficile determinare se la mano si trova dietro o davanti a un ologramma, ad esempio per afferrare con precisione un widget di manipolazione.

* **Dove**: usa le informazioni su ciò che l'utente sta guardando con movimenti di lancio rapido. Afferra un ologramma e scaglialo verso la destinazione prevista.  

    Anche se questa soluzione a volte funziona correttamente, l'esecuzione di movimenti della mano può avere come risultato delle destinazioni estremamente imprecise. In questo caso il tracciamento oculare può essere utile per riportare il vettore di lancio con la mano sulla posizione voluta.

## <a name="see-also"></a>Vedi anche

* [Puntamento con la testa e commit](gaze-and-commit.md)
* [Puntamento e commit con le mani](point-and-commit.md)
* [Interazioni istintive](interaction-fundamentals.md)


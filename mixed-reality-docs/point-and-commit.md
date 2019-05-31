---
title: Punto ed eseguire il commit con le mani
description: Panoramica del modello di input punto ed eseguire il commit
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mista realtà, l'interazione, progettazione, hololens, indicatori, a questo momento, scegliere ed eseguire il commit
ms.openlocfilehash: 30f85d2bb455abab3a533e0a829b4fba8cea0a7a
ms.sourcegitcommit: 5b4292ef786447549c0199003e041ca48bb454cd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/30/2019
ms.locfileid: "66402376"
---
# <a name="point-and-commit-with-hands"></a>Punto ed eseguire il commit con le mani
Punto ed eseguire il commit con le mani è un modello di input che consente agli utenti di destinazione, selezionare e manipolare oggetti 3D e contenuti 2D della distanza. Questa tecnica di interazione "molto" è univoca per realtà mista e non gli esseri umani un modo naturale intereact con tutto il mondo reale. Ad esempio, in questo film eroe *X-uomini*, il carattere [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) è in grado di raggiungere e la modifica di un oggetto decisamente la distanza con il suo mani. Ciò non gli esseri umani eseguibili in realtà. In HoloLens (AR) e realtà mista (VR), abbiamo dotare gli utenti con questo power magico scrivendo, il vincolo fisico del mondo reale non solo avere un'esperienza eccellente ai con contenuto holographic ma anche per rendere l'interazione più efficace ed efficiente di rilievo.

## <a name="device-support"></a>Supporto di dispositivi

Modello di input | [HoloLens (dal 1 ° generazione)](https://docs.microsoft.com/en-us/windows/mixed-reality/hololens-hardware-details) | HoloLens 2 | [Auricolari coinvolgenti](https://docs.microsoft.com/en-us/windows/mixed-reality/immersive-headset-hardware-details) |
| ---------| -----| ----- | ---------|
Punto ed eseguire il commit con le mani | ❌ Non supportato | ✔️ Consigliato | ✔️ Consigliato

Punto e commit, noto anche come mani a questo momento, è una delle nuove funzionalità che utilizza il nuovo sistema di rilevamento delle modifiche manuale articolato. Questo modello di input è anche il modello di input primario su immersive auricolari tramite l'uso di controller di movimento.

## <a name="hand-rays"></a>Raggi mano

In 2 HoloLens, abbiamo creato un raggio di parte che emette dal centro di un dispositivo. Questo ray viene considerato come un'estensione della lancetta. Un cursore a forma di grafico ad anello è collegato alla fine del raggio per indicare il percorso in cui il raggio si interseca con un oggetto di destinazione. L'oggetto che apre il cursore può quindi ricevere comandi gestuali dall'icona della mano.

Questo comando gestuali base viene avviato usando il controllo thumb e con un dito indice per eseguire l'azione indice puntato. Tramite il raggio di mano per puntare e puntare al commit, gli utenti possono attivare un pulsante o un collegamento ipertestuale in un contenuto web. Con gesti composite più, gli utenti sono in grado di esplorazione del contenuto web e la modifica di oggetti 3D da una distanza. La progettazione visiva del raggio mano anche deve reagire in questi stati punto ed eseguire il commit, come descritto e illustrato di seguito: 

* Nel *puntando* lo stato, il raggio è una linea tratteggiata e il cursore si trova una forma di grafico ad anello.
* Nel *commit* lo stato, il raggio si trasforma in una linea continua e il cursore viene ridotta a un punto.

![](images/Hand-Rays-720px.jpg)

## <a name="transition-between-near-and-far"></a>Eseguire la transizione tra vicino e lontano

Invece di usare movimenti specifici, ad esempio "punta verso con dito indice" per indirizzare il raggio, abbiamo progettato il raggio presto out dal centro del palmo, rilasciando e riservare le cinque dita per movimenti manipulative altre, ad esempio avvicinare le dita e prendo. Con questa struttura, creiamo un unico modello mentale, esattamente lo stesso insieme di movimenti della mano di supporto per l'interazione sia vicino. È possibile usare la stessa combinazione di quadratini di ridimensionamento per manipolare gli oggetti alle distanze diverse. La chiamata di raggi è automatico e basati su prossimità:

*  Quando un oggetto all'interno di Azure Resource Manager raggiunto distanza (all'incirca 50 cm), sono disattivati incoraggiando automaticamente per l'interazione con quasi raggi.
*  Quando l'oggetto è un cm 50, i raggi siano accesi. La transizione deve essere diretto e immediato.

![](images/Transition-Between-Near-And-Far-720px.jpg)

## <a name="2d-slate-interaction"></a>Interazione dello slate 2D

Uno Slate 2D è un contenitore holographic hosting di contenuto dell'app 2D, ad esempio web browser. Il concetto di progettazione di gran lunga l'interazione con uno slate 2D consiste nell'usare rays mano a tap air e di destinazione da selezionare. Dopo la destinazione con un raggio di mano, gli utenti possono puntare l'indice per attivare un collegamento ipertestuale o un pulsante. Un lato possono usare per "aria tocco e trascinare" scorrere un contenuto dello slate e ridurre le prestazioni. Il movimento relativo dell'utilizzo di due mani all'aria tocco e trascinare per ingrandire e il contenuto dello slate.

Come destinazione il raggio mano nel bordo e angoli rivela la più vicina intuitività di manipolazione. Per "quadratini di ridimensionamento e trascinare" affordance la manipolazione, gli utenti possono eseguire uniform scalabilità tramite i affordance angolo e ridisporre il lo slate tramite i affordance edge. Selezionandola e trascinando la holobar nella parte superiore dello slate 2D gli utenti possono spostare lo slate intero.

![](images/2D-Slate-Interaction-Far-720px.jpg)

Per la manipolazione 2D ardesia stesso:<br>

* Gli utenti puntano raggio mano negli angoli o bordi per rivelare il più vicino intuitività di manipolazione. 
* Applicando un movimento di manipolazione nell'intuitività, gli utenti possono eseguire la scalabilità uniforme tramite intuitività l'angolo e ridisporre il lo slate tramite l'intuitività edge. 
* Applicando un movimento di manipolazione nel holobar nella parte superiore dello slate 2D, gli utenti possono spostare lo slate intero.<br>

<br>

## <a name="3d-object-manipulation"></a>Modifica di oggetti 3D

Manipolazione diretta, esistono due modi agli utenti di modificare oggetti 3D, basato su intuitività manipolazione e la modifica in base non intuitività. Nel modello di punto e il commit, gli utenti sono in grado di raggiungere esattamente le stesse attività tramite i raggi di mano. Non è necessaria alcuna conoscenza più approfondita.<br>

### <a name="affordance-based-manipulation"></a>Basato su intuitività manipulation
Gli utenti usare rays mano per puntare e individuare il riquadro delimitatore e affordance manipolazione. Gli utenti possono applicare il movimento di manipolazione nel rettangolo di selezione per spostare l'intero oggetto, sul affordance bordo per ruotare e di coner affordance ridimensionare in modo uniforme. <br>

![](images/3D-Object-Manipulation-Far-720px.jpg) <br>


### <a name="non-affordance-based-manipulation"></a>Manipolazione di base non intuitività
Gli utenti punto con rays mano per rivelare il rettangolo di selezione e quindi applicare direttamente i movimenti di manipolazione su di esso. A un lato, la traslazione e rotazione dell'oggetto sono associati al movimento e l'orientamento della lancetta. Con due mani, gli utenti possono traslare, ridimensionare e ruotarla in base al relativi movimenti di due mani.<br>

<br>

## <a name="instinctual-gesturers"></a>Gesturers instinctual
Il concetto di movimenti instinctual per punto e il commit è simile a quella di manipolazione diretta. Per impostazione predefinita di affordance dell'interfaccia utente vengono indirizzati i movimenti che gli utenti dovranno per eseguire su un oggetto 3D. Ad esempio, un punto di controllo di piccole dimensioni potrebbe motivare agli utenti di eseguire il movimento con dito indice e controllo thumb mentre un utente potrebbe voler recuperare un oggetto più grande con tutte le 5 dita.

![](images/Instinctual-Gestures-Far-720px.jpg)<br>

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a>Progettazione simmetrica tra le mani e controller di gradi di libertà 6 
Il concetto di punto e il commit per l'interazione con estrema è stato inizialmente creato e definito per il misto realtà portale (MRP), in cui un utente ha un visore VR immersivi e interagisce con oggetti 3D tramite controller di movimento. I controller di movimento relativi out rays per sta puntando e manipolare oggetti distante. Sono disponibili pulsanti sui controller per ulteriormente il commit delle azioni diverse. Abbiamo sfruttare il modello di interazione di raggi e li collegato a entrambe le mani. Con questa struttura simmetrica, gli utenti che hanno familiari con MRP non sarà necessario per informazioni su un altro modello di interazione per la modifica e che puntano a questo momento, quando vengono usate 2 HoloLen e viceversa.    

![](images/Symmetric-Design-For-Rays-720px.jpg)<br>

## <a name="instinctual-gestures"></a>Movimenti instinctual

![](images/Instinctual-Gestures-Far-720px.jpg)

## <a name="see-also"></a>Vedere anche
* [Puntamento con la testa e commit](gaze-and-commit.md)
* [Manipolazione diretta con le mani](direct-manipulation.md)
* [Interazioni istintive](interaction-fundamentals.md)


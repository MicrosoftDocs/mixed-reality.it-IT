---
title: Punto e commit
description: Panoramica del modello di input punto ed eseguire il commit
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
keywords: Progettare l'interazione, realtà mista
ms.openlocfilehash: e0e9c97053734ac0125fce40be7ffe9afbd2dd68
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2019
ms.locfileid: "64581311"
---
# <a name="point-and-commit"></a>Punto e commit
Punto ed eseguire il commit è un modello di input, che consente agli utenti di destinazione, selezionare e modificare contenuto 2D e 3D oggetti in una distanza. Questa tecnica di interazione di "Asia" è un'esperienza interattiva ombelico che non è risorse umane in corso durante la loro interazione quotidiana con tutto il mondo reale. Ad esempio, in un filmato hero con privilegi avanzati, è in grado di raggiungere e la modifica di un oggetto tramite le mani una distanza decisamente Magneto, ma umane non è possibile farlo in realtà. In Microsoft HoloLens (AR) e la realtà mista di Microsoft (VR), abbiamo dotare utenti questa potenza magico scrivendo, il vincolo fisico del mondo reale non solo di avere esperienza eccellente ai con contenuto holographic ma per rendere più efficace l'interazione di rilievo e efficiente.

## <a name="device-support"></a>Supporto di dispositivi
<table>
    <colgroup>
    <col width="40%" />
    <col width="20%" />
    <col width="20%" />
    <col width="20%" />
    </colgroup>
    <tr>
        <td><strong>Modello di input</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (dal 1 ° generazione)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Auricolari coinvolgenti</strong></a></td>
    </tr>
     <tr>
        <td>Punto ed eseguire il commit (l'interazione manuale distante)</td>
        <td>❌ Non supportato</td>
        <td>✔️ Consigliato</td>
        <td>✔️ Consigliato</td>
    </tr>
</table>
<br>
Punto ed eseguire il commit è stato uno dei modelli di input primari in 2 HoloLens, utilizzando l'icona della mano articolati e nuovo sistema di registrazione. Questo modello di input è anche il modello di input primario su immersive auricolari tramite l'uso di controller di movimento. Punto ed eseguire il Commit è il modello di input che è consigliabile per sostituire l'Head estasiati ed eseguire il Commit in HoloLens (dal 1 ° generazione). 

## <a name="hand-rays"></a>Raggi mano
In 2 HoloLens, creiamo un raggio di mano la ripresa dal centro di un dispositivo. Raggio viene considerato come un'estensione della lancetta. Un cursore di forma di grafico ad anello è collegato all'estremità del raggio implica la posizione in cui il raggio si interseca con un oggetto hitted. L'oggetto che arriva il cursore riceverà comandi gestuali dall'icona della mano. 

Il comando gestuali molto semplice viene avviato usando thumb e con un dito indice eseguire movimento dell'indice puntato. Con ray mano per puntare e puntare al commit, gli utenti possono attivare un pulsante o un collegamento ipertestuale in un contenuto web. Con gesti composite più, gli utenti sono in grado di passare il contenuto web e la modifica di oggetti 3D in una distanza. La progettazione visiva del raggio mano deve reagire anche per scegliere ed eseguire il commit degli stati: <br>
* Nello stato di puntamento, raggio è dash inline e il cursore si trova una forma di grafico ad anello.
* nello stato di commit, il raggio si trasforma in una linea continua e il cursore viene ridotta a un punto.<br><br>
![](images/Hand-Rays-720px.jpg)<br>

## <a name="transition-between-near-and-far"></a>Eseguire la transizione tra vicino e lontano
Invece di usare movimenti specifici, ad esempio puntando con dito indice per indirizzare il raggio, è progettare il raggio prossimamente dal centro del palmo, rilasciando e riservare le dita per manipolazioni gestuali altre cinque. Pertanto, HoloLens 2 supporta esattamente lo stesso insieme di movimenti della mano per l'interazione sia vicino. Quando gli utenti di transito da vicino alle interazioni estrema e viceversa, non è necessaria alcuna conoscenza più approfondita. Gli utenti possono usare la stessa combinazione di quadratini di ridimensionamento per manipolare gli oggetti alle distanze diverse. La chiamata di raggi è automatico e basati su prossimità: <br>
* Quando un oggetto all'interno di Azure Resource Manager raggiunto distanza (all'incirca 50 cm), sono disattivati incoraggiando automaticamente per l'interazione con quasi raggi. 
* Quando l'oggetto è un cm 50, i raggi siano accesi.

Questo meccanismo consente il passaggio diretto e immediato.<br>
![](images/Transition-Between-Near-And-Far-720px.jpg)<br>

## <a name="2d-slate-interaction"></a>Interazione dello slate 2D
Uno slate 2D è un contenitore holographic hosting di contenuto dell'app 2D, ad esempio web browser. Il concetto di progettazione di gran lunga l'interazione con uno slate 2D consiste nell'usare rays mano per puntare e puntare al commit.<br>

Per l'interazione con il contant dello slate:<br>

* Gli utenti possono puntare a un collegamento ipertestuale o un pulsante, quindi indice puntato per attivarlo. 
* Gli utenti possono usare una parte per eseguire un gesto di spostamento di eseguire uno scorrimento verticale di un contenuto dello slate. 
* Gli utenti possono usare due mani per eseguire i movimenti di navigazione per ingrandire e ridurre il contenuto dello slate.<br><br>

![](images/2D-Slate-Interaction-Far-720px.jpg)<br>

Per la manipolazione 2D ardesia stesso:<br>

* Gli utenti puntano raggio mano negli angoli o bordi per rivelare il più vicino intuitività di manipolazione. 
* Applicando un movimento di manipolazione nell'intuitività, gli utenti possono eseguire la scalabilità uniforme tramite intuitività l'angolo e ridisporre il lo slate tramite l'intuitività edge. 
* Applicando un movimento di manipolazione nel holobar nella parte superiore dello slate 2D, gli utenti possono spostare lo slate intero.<br>

<br>

## <a name="3d-object-manipulation"></a>Modifica di oggetti 3D
Manipolazione diretta, esistono due modi per gli utenti modificare un oggetto 3D, intuitività manipolazione di base e Non affordnace basato su Modifica. Nel modello di punto e il commit, gli utenti sono in grado di raggiungere esattamente le stesse attività tramite i raggi di mano. Non è necessaria alcuna conoscenza più approfondita.<br>

### <a name="affordance-based-manipulation"></a>Manipolazione intuitività basato su
Gli utenti usare rays mano per puntare e individuare il riquadro delimitatore e affordance manipolazione. Gli utenti possono applicare il movimento di manipolazione nel rettangolo di selezione per spostare l'intero oggetto, sul affordance bordo per ruotare e di coner affordance ridimensionare in modo uniforme. <br>

![](images/3D-Object-Manipulation-Far-720px.jpg) <br>


### <a name="non-affordance-based-manipulation"></a>Manipolazione di base non intuitività
Gli utenti punto con rays mano per rivelare il rettangolo di selezione e quindi applicare direttamente i movimenti di manipolazione su di esso. A un lato, la traslazione e rotazione dell'oggetto sono associati al movimento e l'orientamento della lancetta. Con due mani, gli utenti possono traslare, ridimensionare e ruotarla in base al relativi movimenti di due mani.<br>

<br>

## <a name="instinctual-gesturers"></a>Gesturers instinctual
Il concetto di movimenti instinctual per punto e il commit è sincronizzato con quella per la modifica diretta. Ciò che gli utenti di movimenti si supponga che per eseguire su un oggetto 3D sono guidato dalla progettazione del affordance dell'interfaccia utente. Un punto di controllo di piccole dimensioni sarebbe motivare agli utenti di eseguire il movimento thumb con dito indice, mentre un oggetto di grandi dimensioni consente agli utenti di ottenere con un dito 5.

![](images/Instinctual-Gestures-Far-720px.jpg)<br>

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a>Progettazione simmetrica tra le mani e controller di gradi di libertà 6 
Il concetto di modello di punto e il commit per l'interazione con estrema in primo luogo viene creato e definito per il misto realtà portale (MRP), in cui gli utenti wear un visore VR immersivi e interagire con l'oggetto 3d tramite controller di movimento. I controller di movimento relativi out rays per sta puntando e manipolare oggetti distante. Sono disponibili pulsanti sui controller per confermare un'ulteriore funzionalità diverse. Abbiamo sfruttare il modello di interazione di raggi e allegarli in entrambe le mani. Con questa struttura simmetrica, non sarà necessario imparare a utilizzare un altro modello di interazione per che punta a questo momento e la manipolazione durante la prima volta usando HoloLen 2, gli utenti che hanno familiari con MRP e viceversa.    

![](images/Symmetric-Design-For-Rays-720px.jpg)<br>


## <a name="see-also"></a>Vedere anche
* [Sguardo ed eseguire il commit](gaze-and-commit.md)
* [Manipolazione diretta](direct-manipulation.md)
* [Concetti fondamentali delle interazioni](interaction-fundamentals.md)

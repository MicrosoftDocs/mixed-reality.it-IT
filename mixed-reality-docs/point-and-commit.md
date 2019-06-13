---
title: Puntamento e commit con le mani
description: Panoramica del modello di input puntamento e commit
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: realtà mista, interazione, progettazione, hololens, mani, da lontano, puntamento e commit
ms.openlocfilehash: 30f85d2bb455abab3a533e0a829b4fba8cea0a7a
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2019
ms.locfileid: "66402376"
---
# <a name="point-and-commit-with-hands"></a>Puntamento e commit con le mani
Puntamento e commit con le mani è un modello di input che consente agli utenti di puntare come destinazione, selezionare e manipolare contenuto 2D e oggetti 3D a distanza. Questa tecnica di interazione "da lontano" è specifica della realtà mista e non corrisponde al modo in cui le persone interagiscono naturalmente con il mondo reale. Ad esempio, nel film di supereroi *X-Men* il personaggio [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) è in grado di manipolare a distanza un oggetto lontano con le sue mani. Questa non è un'azione che gli esseri umani possono compiere nella realtà. Nella realtà aumentata (AR) e nella realtà mista (VR) viene conferito agli utenti questo potere magico che consente di superare i vincoli fisici del mondo reale non solo per godere di esperienze divertenti con contenuti olografici, ma anche per rendere l'interazione più efficace ed efficiente.

## <a name="device-support"></a>Supporto di dispositivi

Modello di input | [HoloLens (prima generazione)](https://docs.microsoft.com/en-us/windows/mixed-reality/hololens-hardware-details) | HoloLens 2 | [Visori VR immersive](https://docs.microsoft.com/en-us/windows/mixed-reality/immersive-headset-hardware-details) |
| ---------| -----| ----- | ---------|
Puntamento e commit con le mani | ❌ Non supportato | ✔️ Consigliato | ✔️ Consigliato

Puntamento e commit, noto anche come uso delle mani da lontano, è una delle nuove funzionalità che si avvale dell'innovativo e articolato sistema di tracciamento delle mani. Questo modello di input è anche il modello di input usato principalmente nei visori VR immersive mediante l'uso di controller del movimento.

## <a name="hand-rays"></a>Raggi mano

In HoloLens 2 è stato creato un raggio mano che viene lanciato dal centro del palmo di una mano. Questo raggio viene considerato come un'estensione della mano. All'estremità del raggio viene visualizzato un cursore ad anello che indica il punto in cui il raggio interseca un oggetto di destinazione. L'oggetto su cui si posa il cursore può quindi ricevere i comandi gestuali dalla mano.

Tale comando gestuale di base viene attivato usando il pollice e il dito indice per eseguire l'azione di simulazione del tocco. Usando il raggio mano per puntare e la simulazione del tocco per eseguire il commit, gli utenti possono attivare un pulsante o un collegamento ipertestuale in un contenuto Web. Con movimenti più compositi, gli utenti possono navigare all'interno del contenuto Web e manipolare a distanza gli oggetti 3D. La progettazione visiva del raggio mano dovrebbe anche reagire a questi stati di puntamento e commit come descritto e mostrato di seguito: 

* Nello stato di *puntamento* il raggio è una linea tratteggiata e il cursore ha una forma ad anello.
* Nello stato di *commit* il raggio diventa una linea continua e il cursore si rimpicciolisce diventando un punto.

![](images/Hand-Rays-720px.jpg)

## <a name="transition-between-near-and-far"></a>Transizione dall'interazione da vicino all'interazione da lontano

Invece di usare un movimento specifico, quale il "puntamento con il dito indice" per indirizzare il raggio, abbiamo progettato il raggio proveniente dal centro del palmo della mano in modo da lasciare le cinque dita libere per eseguire movimenti più finalizzati alla manipolazione, ad esempio l'avvicinamento delle dita e la cattura. Grazie a tale progettazione, viene creato un unico modello mentale in grado di supportare esattamente la stessa serie di movimenti della mano per l'interazione da vicino e da lontano. Puoi usare lo stesso movimento di cattura per manipolare oggetti a distanze diverse. Il raggio viene richiamato automaticamente in base alla prossimità:

*  Se un oggetto si trova a una distanza raggiungibile stendendo le braccia (circa 50 cm), i raggi vengono disattivati automaticamente, incoraggiando l'uso dell'interazione da vicino.
*  Se l'oggetto si trova a una distanza superiore a 50 cm, i raggi vengono attivati. La transizione deve avvenire fluidamente e senza problemi.

![](images/Transition-Between-Near-And-Far-720px.jpg)

## <a name="2d-slate-interaction"></a>Interazione con uno slate 2D

Uno slate 2D è un contenitore olografico che ospita contenuti di app 2D, ad esempio un Web browser. Il concetto di progettazione per l'interazione da lontano con uno slate 2D prevede l'uso dei raggi mano per puntare una destinazione e della simulazione del tocco per effettuare la selezione. Dopo aver individuato la destinazione con un raggio mano, gli utenti possono simulare il tocco per attivare un collegamento ipertestuale o un pulsante. Possono usare una mano per "simulare il tocco e trascinare" in modo da scorrere verso l'alto e verso il basso il contenuto dello slate. Il movimento relativo associato all'uso di due mani per simulare il tocco e trascinare può causare lo zoom avanti e lo zoom indietro sul contenuto dello slate.

Puntando il raggio mano sugli angoli e sui bordi, è possibile vedere l'invito di manipolazione più vicino. "Afferrando e trascinando" gli inviti di manipolazione, gli utenti possono eseguire un ridimensionamento uniforme mediante gli inviti agli angoli, nonché adattare automaticamente il contenuto dello slate mediante gli inviti sui bordi. Afferrando e trascinando la barra dell'ologramma nella parte superiore dello slate 2D, gli utenti possono spostare l'intero slate.

![](images/2D-Slate-Interaction-Far-720px.jpg)

Per manipolare lo slate 2D:<br>

* Gli utenti puntano il raggio mano sugli angoli o sui bordi per vedere l'invito di manipolazione più vicino. 
* Applicando un movimento di manipolazione all'invito, gli utenti possono eseguire un ridimensionamento uniforme mediante l'invito all'angolo, nonché adattare automaticamente il contenuto dello slate mediante l'invito sul bordo. 
* Applicando un movimento di manipolazione alla barra dell'ologramma nella parte superiore dello slate 2D, gli utenti possono spostare l'intero slate.<br>

<br>

## <a name="3d-object-manipulation"></a>Manipolazione di oggetti 3D

Nella manipolazione diretta gli utenti possono manipolare un oggetto 3D in due modi, ovvero con manipolazione basata e non basata sugli inviti. Nel modello puntamento e commit gli utenti possono eseguire esattamente le stesse attività mediante i raggi mano. Non sono necessarie altre conoscenze.<br>

### <a name="affordance-based-manipulation"></a>Manipolazione basata sugli inviti
Gli utenti usano i raggi mano per puntare e vedere il cubo di delimitazione e gli inviti di manipolazione. Gli utenti possono applicare il movimento di manipolazione al cubo di delimitazione per spostare l'intero oggetto, agli inviti sui bordi per ruotare e agli inviti agli angoli per ridimensionare in modo uniforme. <br>

![](images/3D-Object-Manipulation-Far-720px.jpg) <br>


### <a name="non-affordance-based-manipulation"></a>Manipolazione non basata sugli inviti
Gli utenti puntano con i raggi mano per vedere il cubo di delimitazione e quindi vi applicano direttamente i movimenti di manipolazione. Con una mano, la traslazione e la rotazione dell'oggetto sono associati al movimento e all'orientamento della mano. Con due mani, gli utenti possono spostarlo, ridimensionarlo e ruotarlo in base ai movimenti relativi delle due mani.<br>

<br>

## <a name="instinctual-gesturers"></a>Uso dei movimenti istintivi
Il concetto di movimenti istintivi per il puntamento e il commit è analogo a quello per la manipolazione diretta. I movimenti che gli utenti dovrebbero eseguire su un oggetto 3D vengono guidati dalla progettazione degli inviti dell'interfaccia utente. Ad esempio, in presenza di un piccolo punto di controllo gli utenti sono portati a usare il pollice e l'indice (ovvero ad avvicinare le dita), mentre davanti a un oggetto più grande possono decidere di afferrarlo usando tutte e cinque le dita.

![](images/Instinctual-Gestures-Far-720px.jpg)<br>

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a>Progettazione simmetrica tra le due mani e controller 6DoF 
Il concetto alla base del puntamento e del commit per un'interazione da lontano inizialmente era stato creato e definito per il Portale realtà mista, dove un utente indossa un visore VR immersive e interagisce con gli oggetti 3D mediante controller del movimento. Tali controller emettono raggi per il puntamento e la manipolazione degli oggetti lontani. Sui controller sono presenti pulsanti che consentono di eseguire ulteriormente il commit di azioni diverse. Noi sfruttiamo il modello di interazione dei raggi e lo abbiamo associato a entrambe le mani. Grazie a questa progettazione simmetrica, gli utenti abituati a operare con il Portale realtà mista non dovranno apprendere un altro modello di interazione per il puntamento e la manipolazione da lontano quando usano HoloLens 2 e viceversa.    

![](images/Symmetric-Design-For-Rays-720px.jpg)<br>

## <a name="instinctual-gestures"></a>Movimenti istintivi

![](images/Instinctual-Gestures-Far-720px.jpg)

## <a name="see-also"></a>Vedi anche
* [Puntamento con la testa e commit](gaze-and-commit.md)
* [Manipolazione diretta con le mani](direct-manipulation.md)
* [Interazioni istintive](interaction-fundamentals.md)


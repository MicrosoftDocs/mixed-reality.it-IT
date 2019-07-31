---
title: Puntamento e commit con le mani
description: Panoramica del modello di input puntamento e commit
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: realtà mista, interazione, progettazione, hololens, mani, da lontano, puntamento e commit
ms.openlocfilehash: 4e19a7fd95bac42283ce3e3176a1363afda8f220
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414545"
---
# <a name="point-and-commit-with-hands"></a>Puntamento e commit con le mani
Puntamento e commit con le mani è un modello di input che consente agli utenti di puntare come destinazione, selezionare e manipolare contenuto 2D e oggetti 3D a distanza. Questa tecnica di interazione "da lontano" è specifica della realtà mista e non corrisponde al modo in cui le persone interagiscono naturalmente con il mondo reale. Ad esempio, nel film di supereroi *X-Men* il personaggio [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) è in grado di manipolare a distanza un oggetto lontano con le sue mani. Questa non è un'azione che gli esseri umani possono compiere nella realtà. Nella realtà aumentata (AR) e nella realtà mista (VR) di HoloLens, gli utenti vengono dotati di questo potere magico, che consente di superare i vincoli fisici del mondo reale, non solo per vivere esperienze divertenti con contenuti olografici, ma anche per migliorare l'efficacia e l'efficienza delle interazioni.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><strong>Modello di input</strong></td>
     <td><a href="hololens-hardware-details.md"><strong>HoloLens (prima generazione)</strong></a></td>
     <td><strong>HoloLens 2</strong></td>
     <td><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
</tr>
<tr>
     <td>Puntamento e commit con le mani</td>
     <td>❌ Non supportato</td>
     <td>✔️ Consigliato</td>
     <td>✔️ Consigliato</td>
</tr>
</table>


Puntamento e commit, noto anche come uso delle mani da lontano, è una delle nuove funzionalità che si avvale dell'innovativo e articolato sistema di tracciamento delle mani. Questo modello di input è anche il modello di input usato principalmente nei visori VR immersive mediante l'uso di controller del movimento.

## <a name="hand-rays"></a>Raggi mano

In HoloLens 2 abbiamo creato un raggio della mano che viene lanciato dal centro del palmo della mano dell'utente. Questo raggio viene considerato come un'estensione della mano. All'estremità del raggio viene visualizzato un cursore ad anello che indica il punto in cui il raggio interseca un oggetto di destinazione. L'oggetto su cui si posa il cursore può quindi ricevere i comandi gestuali dalla mano.

Tale comando gestuale di base viene attivato usando il pollice e il dito indice per eseguire l'azione di simulazione del tocco. Usando il raggio della mano per il puntamento e la simulazione del tocco per il commit, gli utenti possono attivare un pulsante o un collegamento ipertestuale. Con movimenti più compositi, gli utenti possono navigare all'interno del contenuto Web e manipolare a distanza gli oggetti 3D. La progettazione visiva del raggio mano dovrebbe anche reagire a questi stati di puntamento e commit come descritto e mostrato di seguito: 

* Nello stato di *puntamento* il raggio è una linea tratteggiata e il cursore ha una forma ad anello.
* Nello stato di *commit* il raggio diventa una linea continua e il cursore si rimpicciolisce diventando un punto.

![Stati di puntamento e commit per i raggi della mano](images/Hand-Rays-720px.jpg)<br>
*Stati di puntamento (a sinistra) e commit (a destra) per i raggi della mano*

## <a name="transition-between-near-and-far"></a>Transizione dall'interazione da vicino all'interazione da lontano

Invece di usare movimenti specifici, come il "puntamento con il dito indice" per indirizzare il raggio, abbiamo progettato il raggio proveniente dal centro del palmo, in modo da lasciare le cinque dita libere per eseguire movimenti più finalizzati alla manipolazione, ad esempio l'avvicinamento delle dita e la cattura. Grazie a tale progettazione, viene creato un unico modello mentale in grado di supportare esattamente la stessa serie di movimenti della mano per l'interazione da vicino e da lontano. Puoi usare lo stesso movimento di cattura per manipolare oggetti a distanze diverse. I raggi vengono richiamati automaticamente in base alla prossimità, come indicato di seguito:

*  Se un oggetto è a portata di braccio (a una distanza di circa 50 cm), i raggi vengono disattivati automaticamente, incoraggiando l'uso dell'interazione da vicino.
*  Se l'oggetto si trova a una distanza superiore a 50 cm, i raggi vengono attivati. La transizione deve avvenire fluidamente e senza problemi.

![Lo stesso set di movimenti della mano viene usato per l'interazione da vicino e da lontano](images/Transition-Between-Near-And-Far-720px.jpg)<br>
*Lo stesso set di movimenti della mano viene usato per l'interazione da vicino e da lontano.*

## <a name="2d-slate-interaction"></a>Interazione con uno slate 2D

Uno slate 2D è un contenitore olografico che ospita contenuti di app 2D, ad esempio un Web browser. Il concetto di progettazione per l'interazione da lontano con uno slate 2D prevede l'uso dei raggi mano per puntare una destinazione e della simulazione del tocco per effettuare la selezione. Dopo aver individuato la destinazione con un raggio mano, gli utenti possono simulare il tocco per attivare un collegamento ipertestuale o un pulsante. Possono usare una mano per "simulare il tocco e trascinare" in modo da scorrere verso l'alto e verso il basso il contenuto dello slate. Il movimento relativo associato all'uso di due mani per simulare il tocco e trascinare può causare lo zoom avanti e lo zoom indietro sul contenuto dello slate.

Puntando il raggio mano sugli angoli e sui bordi, è possibile vedere l'invito di manipolazione più vicino. "Afferrando e trascinando" gli inviti di manipolazione, gli utenti possono eseguire un ridimensionamento uniforme tramite gli inviti degli angoli, nonché adattare automaticamente il contenuto dello slate tramite gli inviti dei bordi. Afferrando e trascinando la barra dell'ologramma nella parte superiore dello slate 2D, gli utenti possono spostare l'intero slate.

![Interazione con uno slate 2D](images/2D-Slate-Interaction-Far-720px.jpg)

Per manipolare lo slate 2D:<br>

* Gli utenti puntano il raggio mano sugli angoli o sui bordi per vedere l'invito di manipolazione più vicino. 
* Applicando un movimento di manipolazione all'invito, gli utenti possono eseguire un ridimensionamento uniforme tramite l'invito degli angoli, nonché adattare automaticamente il contenuto dello slate mediante l'invito dei bordi. 
* Applicando un movimento di manipolazione alla barra dell'ologramma nella parte superiore dello slate 2D, gli utenti possono spostare l'intero slate.<br>

<br>

## <a name="3d-object-manipulation"></a>Manipolazione di oggetti 3D

Nella manipolazione diretta gli utenti possono manipolare gli oggetti 3D in due modi, ovvero con manipolazione basata sugli inviti e non basata sugli inviti. Nel modello puntamento e commit gli utenti possono eseguire esattamente le stesse attività mediante i raggi mano. Non sono necessarie altre conoscenze.<br>

### <a name="affordance-based-manipulation"></a>Manipolazione basata sugli inviti
Gli utenti usano i raggi mano per puntare e vedere il cubo di delimitazione e gli inviti di manipolazione. Gli utenti possono applicare il movimento di manipolazione al cubo di delimitazione per spostare l'intero oggetto, agli inviti dei bordi per ruotare e agli inviti degli angoli per ridimensionare in modo uniforme. <br>

![Manipolazione basata sugli inviti](images/3D-Object-Manipulation-Far-720px.jpg) <br>


### <a name="non-affordance-based-manipulation"></a>Manipolazione non basata sugli inviti
Gli utenti puntano con i raggi mano per vedere il cubo di delimitazione e quindi vi applicano direttamente i movimenti di manipolazione. Con una mano, la traslazione e la rotazione dell'oggetto sono associati al movimento e all'orientamento della mano. Con due mani, gli utenti possono spostarlo, ridimensionarlo e ruotarlo in base ai movimenti relativi delle mani.<br>

<br>

## <a name="instinctual-gestures"></a>Movimenti istintivi
Il concetto di movimenti istintivi per puntamento e commit è analogo a quello per la [manipolazione diretta con le mani](direct-manipulation.md). I movimenti che gli utenti eseguono su un oggetto 3D vengono guidati dalla progettazione degli inviti dell'interfaccia utente. Ad esempio, in presenza di un piccolo punto di controllo gli utenti sono portati a usare il pollice e l'indice (ovvero ad avvicinare le dita), mentre davanti a un oggetto più grande possono decidere di afferrarlo usando tutte e cinque le dita.

![Movimenti istintivi](images/Instinctual-Gestures-Far-720px.jpg)<br>

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a>Progettazione simmetrica tra le due mani e controller 6DoF 
Il concetto alla base del puntamento e commit per un'interazione da lontano inizialmente era stato creato e definito per il Portale realtà mista, in cui un utente indossa un visore VR immersive e interagisce con gli oggetti 3D tramite controller del movimento. Tali controller emettono raggi per il puntamento e la manipolazione degli oggetti lontani. Sui controller sono presenti pulsanti che consentono di eseguire ulteriormente il commit di azioni diverse. Noi sfruttiamo il modello di interazione dei raggi e lo abbiamo associato a entrambe le mani. Grazie a questa progettazione simmetrica, gli utenti abituati a operare con il Portale realtà mista non dovranno apprendere un altro modello di interazione per il puntamento e la manipolazione da lontano quando usano HoloLens 2 e viceversa.    

![Progettazione simmetrica tra le due mani e controller 6DoF](images/Symmetric-Design-For-Rays-720px.jpg)<br>


## <a name="see-also"></a>Vedi anche
* [Puntamento con la testa e commit](gaze-and-commit.md)
* [Manipolazione diretta con le mani](direct-manipulation.md)
* [Interazioni istintive](interaction-fundamentals.md)


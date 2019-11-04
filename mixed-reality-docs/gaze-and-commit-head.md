---
title: Puntamento con la testa e commit
description: Panoramica del modello di input puntamento con la testa e commit
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: realtà mista, sguardo fisso, selezione della destinazione con lo sguardo fisso, interazione, progettazione
ms.openlocfilehash: 5fef778dde6852222e098aeb1cbb41fe04e0b744
ms.sourcegitcommit: a5dc182da237f63f0487d40a2e11894027208b6c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/02/2019
ms.locfileid: "73441092"
---
# <a name="head-gaze-and-commit"></a>Puntamento con la testa e commit
_Head-sguardi e commit_ sono un caso speciale del modello di input [sguardo e commit](gaze-and-commit.md) che prevede la destinazione di un oggetto con la direzione della testa che punta verso l'alto (direzione), quindi agisce su di esso con un input secondario, ad esempio il gesto della mano toccare o il comando Voice "Select". 

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
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (prima generazione)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
    </tr>
     <tr>
        <td>Puntamento con la testa e commit</td>
        <td>✔️ Consigliata</td>
        <td>✔️ Consigliato (terza scelta - <a href="interaction-fundamentals.md">Vedi le altre opzioni</a>)</td>
        <td>➕ Opzione alternativa</td>
    </tr>
</table>

---

## <a name="target-sizing-and-feedback"></a>Dimensioni della destinazione e feedback
Il vettore di sguardi a capo è stato visualizzato ripetutamente per poter essere usato per obiettivi mirati, ma spesso funziona meglio per il targeting lordo, ovvero l'acquisizione di destinazioni di dimensioni più grandi. Le dimensioni di destinazione minime da 1 a 1,5 gradi consentono azioni utente riuscite nella maggior parte degli scenari, sebbene le destinazioni di 3 gradi consentano spesso una maggiore velocità. Le dimensioni che l'utente punta come destinazione corrispondono in effetti a un'area 2D persino per gli elementi 3D: qualunque proiezione vi sia di fronte deve essere l'area selezionabile come destinazione. Fornire un segnale saliente che un elemento è "attivo" (che l'utente lo sta indirizzando) è estremamente utile. Questo può includere trattamenti quali effetti "hover" visibili, evidenziazioni audio o clic oppure un chiaro allineamento di un cursore con un elemento.

![Dimensioni ottimali della destinazione a una distanza di 2 metri](images/gazetargeting-size-1000px.jpg)<br>
*Dimensioni ottimali della destinazione a una distanza di 2 metri*

<br>

![Esempio di evidenziazione di un oggetto selezionato come destinazione con lo sguardo fisso](images/gazetargeting-highlighting-940px.jpg)<br>
*Esempio di evidenziazione di un oggetto selezionato come destinazione con lo sguardo fisso*

## <a name="target-placement"></a>Posizionamento della destinazione
Spesso gli utenti non riescono a trovare gli elementi dell'interfaccia utente posizionati in modo molto elevato o molto basso nel proprio campo di visualizzazione, concentrando la maggior parte delle loro attenzioni sulle aree attorno al suo interesse principale, che è approssimativamente a livello di occhio. Può pertanto rivelarsi utile posizionare la maggior parte delle destinazioni in una fascia ragionevole attorno al livello degli occhi. Data la tendenza degli utenti a concentrarsi su un'area visiva relativamente limitata in un determinato momento (il cono attenzionale della visione è all'incirca di 10 gradi), il fatto di raggruppare gli elementi dell'interfaccia utente in base a come sono correlati concettualmente può dare luogo a comportamenti di concatenamento dell'attenzione da un elemento all'altro man mano che l'utente sposta lo sguardo all'interno di un'area. Quando progetti l'interfaccia utente, tieni presente la grande differenza potenziale di campo visivo tra i visori HoloLens e i visori VR immersive.

![Esempio di elementi dell'interfaccia utente raggruppati per facilitare la selezione della destinazione con lo sguardo fisso in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)<br>
*Esempio di elementi dell'interfaccia utente raggruppati per facilitare la selezione della destinazione con lo sguardo fisso in Galaxy Explorer*

## <a name="improving-targeting-behaviors"></a>Miglioramento dei comportamenti di selezione della destinazione
Se è possibile determinare o approssimarsi attentamente gli obiettivi dell'utente per la destinazione di un elemento, può essere molto utile accettare i tentativi vicini di interazione come se fossero destinati correttamente. Ecco alcuni metodi efficaci che possono essere incorporati in esperienze di realtà mista:

### <a name="head-gaze-stabilization-gravity-wells"></a>Stabilizzazione del puntamento con la testa ("pozzi di gravità")
Questa operazione deve essere attivata la maggior parte o tutto il tempo. Questa tecnica elimina la natura naturale e le jittere del collo che possono essere spostate dagli utenti anche a causa di comportamenti di ricerca e di conversazione.

### <a name="closest-link-algorithms"></a>Algoritmi di collegamento più vicino
Funzionano al meglio nelle aree con contenuto interattivo sparso. Se c'è una probabilità elevata che è possibile determinare ciò che un utente ha tentato di interagire, è possibile integrare le proprie capacità di destinazione supponendo un certo livello di INTENTITà.

### <a name="backdating-and-postdating-actions"></a>Azioni di Ridata e di backdating
Questo meccanismo è utile per le attività che richiedono velocità. Quando un utente si sposta in una serie di manovre di targeting e attivazione alla velocità, è utile presupporre un certo scopo e consentire la mancata corrispondenza delle destinazioni in cui l'utente si è concentrato leggermente prima o leggermente dopo il tocco (50 ms before/after era efficace in EA test di rly).

### <a name="smoothing"></a>Definizione di movimenti uniformi
Questo meccanismo è utile per i movimenti di percorso, riducendo il lieve tremolio e le oscillazioni dovute alle caratteristiche di movimento Head naturale. Quando si smussano i movimenti del tracciato, è necessario arrotondare le dimensioni e la distanza dei movimenti anziché nel tempo.

### <a name="magnetism"></a>Magnetismo
Questo meccanismo può essere considerato come una versione più generale degli algoritmi di collegamento più vicini, ovvero disegnare un cursore verso una destinazione o semplicemente aumentare hitboxes, in modo visibile o meno, perché gli utenti si avvicinano a destinazioni potenziali utilizzando una conoscenza del layout interattivo per migliorare finalità utente di approccio. Questa soluzione può risultare particolarmente efficace per le destinazioni di piccole dimensioni.

### <a name="focus-stickiness"></a>Spostamento dello stato attivo in base all'elemento di interesse corrente
Quando si determinano gli elementi interattivi adiacenti a cui dare lo stato attivo, la viscosità dello stato attivo fornisce una distorsione all'elemento attualmente attivo. Questo consente di ridurre i comportamenti di cambio dello stato attivo quando si esegue il mobile a un punto medio tra due elementi con rumore naturale.


## <a name="see-also"></a>Vedi anche
* [Interazione basata sull'occhio](eye-gaze-interaction.md)
* [Sguardo fisso e attesa](gaze-and-dwell.md)
* [Manipolazione diretta](direct-manipulation.md)
* [Movimenti pratici](gaze-and-commit.md#composite-gestures)
* [Hand-point e commit](point-and-commit.md)
* [Interazioni istintive](interaction-fundamentals.md)
* [Input vocale](voice-input.md)




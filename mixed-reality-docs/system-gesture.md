---
title: Movimento di sistema
description: Movimento di sistema per chiamare il menu Start.
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: Realtà mista, movimenti, interazione, progettazione
ms.openlocfilehash: ba543ffe0802d0b95cc539fb0e73c0b4e51fc186
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926731"
---
# <a name="system-gesture"></a>Movimento di sistema

Il gesto del sistema è un movimento della mano usato per richiamare il menu Start. È l'equivalente di premere il tasto Windows sulla tastiera, il pulsante Xbox su un controller Xbox o il pulsante Windows sul controller di movimento per le cuffie immersive. È importante comprendere quali movimenti sono riservati per il sistema in ogni dispositivo di realtà mista per evitare conflitti durante la progettazione delle interazioni.

## <a name="device-support"></a>Supporto di dispositivi

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Funzionalità</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (prima generazione)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
    </tr>
     <tr>
        <td>Bloom</td>
        <td>✔️</td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td>Pulsante polso</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
    <tr>
        <td>Occhio e palmare</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a>Bloom
Per visualizzare il menu Start in HoloLens (1st Gen), abbiamo progettato "Bloom", un gesto simbolico che simula il fiore fiorito. È distinto per l'interazione surefooted, facile da eseguire e rapido da richiamare. Per eseguire il gesto di fioritura su HoloLens (1 ° gen), è necessario passare a un palmo e a una mano insieme, quindi aprire la mano diffondendo le dita.

:::row:::
    :::column:::
        ![Bloom Close](images/bloom-close.png)<br>
        **Passaggio 1: palmare insieme**<br>
    :::column-end:::
    :::column:::
        ![Bloom Open](images/bloom-open.png)<br>
        **Passaggio 2: Palm up con la distribuzione a portata di mano**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="wrist-button"></a>Pulsante polso
In HoloLens 2, il movimento Bloom è stato sostituito con un pulsante di polso virtuale che consente interazioni più istintive che non richiedono ulteriori attività di insegnamento. Visualizzando gli utenti con il pulsante del polso, è possibile accedervi in modo intuitivo e premerlo con l'altra parte.

:::row:::
    :::column:::
        ![pronto per il pulsante del polso](images/wrist-button-ready.png)<br>
        **Passaggio 1: eseguire il Palm up per visualizzare il pulsante del polso**<br>
    :::column-end:::
    :::column:::
        ![premere il pulsante del polso](images/wrist-button-press.png)<br>
        **Passaggio 2: premere il pulsante del polso**<br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="eye-gaze-and-palm-up-pinch"></a>Occhio e palmare
È stata anche progettata una soluzione a mano singola per semplificare l'accesso in HoloLens 2. Questo gesto richiede agli utenti di osservare il pulsante del polso, quindi di usare la stessa mano per eseguire un pizzico di palmare usando il pollice e il dito dell'indice.<br>
:::row:::
    :::column:::
        ![pronto per il pulsante del polso](images/wrist-button-ready.png)<br>
        **Passaggio 1: eseguire il Palm up per visualizzare il pulsante del polso**<br>
    :::column-end:::
    :::column:::
        ](images/wrist-button-pinch.png) pizzico pulsante ![polso<br>
        **Passaggio: occhio al pulsante e quindi pizzicare**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a>Vedi anche

* [Interazioni istintive](interaction-fundamentals.md)
* [Sguardo fisso](eye-tracking.md)
* [Input vocale](voice-input.md)

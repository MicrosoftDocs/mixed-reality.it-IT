---
title: Sguardo fisso
description: Lo sguardo è la prima forma di input e rappresenta una forma principale di destinazione all'interno della realtà mista.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Realtà mista, sguardo, interazione, progettazione
ms.openlocfilehash: 7e65d26d3e9edabbd01d35a887ffc8622a3c6337
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414373"
---
# <a name="gaze"></a>Sguardo fisso

Lo **sguardo** è la prima forma di input e rappresenta una forma principale di destinazione all'interno della realtà mista. Lo sguardo indica il punto in cui l'utente sta cercando nel mondo e consente di determinarne lo scopo. Nel mondo reale, in genere si esamina un oggetto con cui si intende interagire. Questo è lo stesso con lo sguardo.

Gli auricolari per la realtà mista usano la posizione e l'orientamento dell'Head dell'utente per determinare il vettore di sguardi a capo. È possibile considerare questo vettore come un puntatore laser direttamente direttamente tra gli occhi dell'utente. Quando l'utente esamina la stanza, l'applicazione può intersecare questo raggio, sia con i propri ologrammi che con la mesh di [mapping spaziale](spatial-mapping.md) , per determinare l'oggetto virtuale o reale che può essere esaminato dall'utente.

In HoloLens 2, le interazioni possono essere mirate dallo sguardo a capo dell'utente, dallo sguardo a occhi o dalle interazioni quasi o a lungo.
In HoloLens (1st Gen), le interazioni dovrebbero in genere derivare il proprio targeting da quello degli utenti, anziché tentare di eseguire il rendering o interagire direttamente nella posizione della mano. Una volta avviata un'interazione, è possibile usare i movimenti relativi della mano per [controllare il movimento](gestures.md), come per il gesto di [manipolazione o spostamento](gestures.md#composite-gestures) . Con le cuffie di tipo immersivo, è possibile usare uno sguardo a capo o [controller di movimento](motion-controllers.md)che supportano la funzionalità di puntamento.

<br>

>[!VIDEO https://www.youtube.com/embed/zCPiZlWdVws]

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
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
    </tr>
     <tr>
        <td>Sguardo a capo</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
     <tr>
        <td>Occhio</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

> [!NOTE]
> Altre indicazioni specifiche per HoloLens 2 [saranno presto](index.md#news-and-notes)disponibili.


## <a name="uses-of-gaze"></a>Usi di sguardi

In qualità di sviluppatore di realtà mista, è possibile fare molto con la testa o gli sguardi:
* L'app può intersecare sguardi con gli ologrammi nella scena per determinare il punto in cui l'attenzione dell'utente è.
* L'app può essere destinata ai movimenti e alle presse del controller in base allo sguardo dell'utente, consentendo all'utente di selezionare, attivare, acquisire, scorrere o interagire in altro modo con i loro ologrammi.
* L'app può consentire all'utente di posizionare gli ologrammi su superfici reali, intersecando il raggio di sguardi con la mesh di mapping spaziale.
* L'app può sapere quando l'utente *non* sta osservando la direzione di un oggetto importante, che può portare l'app a fornire suggerimenti visivi e audio per la rotazione verso tale oggetto.

## <a name="cursor"></a>Cursor

Per lo sguardo a capo, la maggior parte delle app deve usare un [cursore](cursors.md) (o altre indicazioni visive/visive) per fornire all'utente la confidenza con cui si sta per interagire. In genere, il cursore viene posizionato in tutto il mondo in cui il raggio di sguardo principale interseca un oggetto, che può essere un ologramma o una superficie reale.

![Un cursore visivo di esempio per mostrare lo sguardo](images/cursor.jpg)<br>
*Un cursore visivo di esempio per mostrare lo sguardo*

Per gli occhi, in genere è consigliabile *non* mostrare un cursore, in quanto questa operazione può diventare rapidamente distrazione e fastidioso per l'utente. È invece possibile evidenziare leggermente le destinazioni visive o usare un cursore occhio molto debole per fornire informazioni su ciò che l'utente sta per interagire. Per altre informazioni, vedere le [linee guida di progettazione per l'input basato su occhi](eye-tracking.md) su HoloLens 2.

## <a name="giving-action-to-the-users-gaze"></a>Assegnazione di un'azione allo sguardo dell'utente

Una volta che l'utente ha assegnato un ologramma o un oggetto reale usando il proprio sguardo, il passaggio successivo consiste nell'agire su tale oggetto. Le modalità principali per l'esecuzione di un'azione da parte di un utente sono i [movimenti](gestures.md), i [controller di movimento](motion-controllers.md) e la [voce](voice-input.md).

## <a name="see-also"></a>Vedere anche
* [Input MR 210: Sguardo a capo](holograms-210.md)
* [Puntamento con la testa e sguardo fisso in DirectX](gaze-in-directx.md)
* [Sguardo a testa in Unity](gaze-in-unity.md)
* [Eye-sguardi su HoloLens 2](eye-tracking.md)
* [Sguardo in Unity con il Toolkit di realtà misto](https://aka.ms/mrtk-eyes)

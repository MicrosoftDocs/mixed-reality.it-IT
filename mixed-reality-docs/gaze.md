---
title: Sguardo fisso
description: Sguardo è il primo modulo di input e un modulo primario di destinazione all'interno di realtà mista.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Misto realtà, sguardo, interazione, progettazione
ms.openlocfilehash: 7e65d26d3e9edabbd01d35a887ffc8622a3c6337
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414373"
---
# <a name="gaze"></a>Sguardo fisso

**Estasiati** è il primo modulo di input ed è un modulo primario di destinazione all'interno di realtà mista. Sguardo indica dove l'utente cerca in tutto il mondo e consente di determinare il loro scopo. Nel mondo reale, è in genere verrà esaminato un oggetto che si prevede di interagire con. Questo è lo stesso con sguardo.

Realtà mista auricolari usano la posizione e l'orientamento principale dell'utente di per determinare i vettori sguardo head. È possibile considerare questo vettore come un puntatore laser dritto da direttamente tra gli occhi dell'utente. Quando l'utente cerca nella stanza, l'applicazione può intersecarsi questo ray, con i proprio ologrammi e con il [mapping spaziale](spatial-mapping.md) mesh per determinare quale oggetto reale o virtuale, l'utente potrebbe essere opportuno.

Nel 2 HoloLens, le interazioni possono essere destinate dalle sguardo head dell'utente, sguardo sotto controllo tramite quasi o passare a questo momento le interazioni.
Su HoloLens (dal 1 ° generazione), le interazioni devono derivano in genere la destinazione da sguardo head dell'utente, piuttosto che tentare per eseguire il rendering o interagire direttamente nella posizione dell'icona della mano. Dopo aver avviato un'interazione, relativi movimenti della mano possono essere usata per controllare la [movimento](gestures.md), come con la [manipolazione o la navigazione](gestures.md#composite-gestures) movimento. Con immersive auricolari, è possibile fare riferimento tramite uno sguardo head o che punta in grado di supportare [controller di movimento](motion-controllers.md).

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
        <td>Head sguardo</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
     <tr>
        <td>Sguardo sotto controllo</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

> [!NOTE]
> Altre indicazioni specifiche su 2 HoloLens [presto](index.md#news-and-notes).


## <a name="uses-of-gaze"></a>Utilizzi di sguardo

Qualità di sviluppatore di realtà mista, è possibile eseguire molte con sguardo head o occhio:
* Le app possono intersecarsi sguardo con vntana nella scena per determinare dove è l'attenzione dell'utente.
* L'app può essere indirizzato movimenti e basate sguardo dell'utente, consentendo all'utente di selezionare, attivare, recuperare, scorrere o in caso contrario, interagire con loro vntana pressioni di controller.
* L'app può consentire all'utente di inserire vntana nelle aree del mondo reale, eseguendo che intersecano il ray sguardo con la rete di mapping spaziale.
* L'app è possibile sapere quando l'utente è *non* alla ricerca nella direzione di un oggetto importante, che può comportare l'app per offrire segnali audio e video per attivare verso tale oggetto.

## <a name="cursor"></a>Cursor

Per sguardo head, è consigliabile usare la maggior parte delle App un' [cursore](cursors.md) (o un'altra indicazione acustica/visual) per fornire la fiducia degli utenti sugli aspetti che stanno per interagire con. È in genere posizionare il cursore in tutto il mondo in cui il raggio sguardo head interseca prima di tutto un oggetto, che potrebbe essere ologramma o un'area del mondo reale.

![Un esempio visivo del cursore per mostrare sguardo](images/cursor.jpg)<br>
*Un esempio visivo del cursore per mostrare sguardo*

Per sguardo rossi, è consigliabile in genere *non* mostrare un cursore, perché ciò può risultare poco chiara e indesiderate per l'utente. Invece leggermente evidenziare destinazioni visual o utilizzare un cursore molto Rube occhio per avere la certezza sulle novità per interagire con l'utente. Per altre informazioni, vedere la [indicazioni di progettazione per input basato sulle occhio](eye-tracking.md) in 2 HoloLens.

## <a name="giving-action-to-the-users-gaze"></a>Concessione dell'azione a sguardo dell'utente

Dopo avere l'utente è incluso un ologrammi o un oggetto reale con loro sguardo, il passaggio successivo è intervenire su tale oggetto. Sono i metodi principali per un utente intervenire attraverso [movimenti](gestures.md), [movimento controller](motion-controllers.md) e [vocale](voice-input.md).

## <a name="see-also"></a>Vedere anche
* [Input MR 210: Head sguardo](holograms-210.md)
* [Puntamento con la testa e sguardo fisso in DirectX](gaze-in-directx.md)
* [Head estasiati Unity](gaze-in-unity.md)
* [Visiva in HoloLens 2](eye-tracking.md)
* [Sguardo occhio in Unity usando il Toolkit di realtà mista](https://aka.ms/mrtk-eyes)

---
title: Sguardo fisso
description: Sguardo è il primo modulo di input e un modulo primario di destinazione all'interno di realtà mista.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Realtà mista, sguardo, interazione, progettazione
ms.openlocfilehash: 9a12a5a3b3a583477fd98caeaa2f6890c67e2655
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604970"
---
# <a name="gaze"></a>Sguardo fisso

**Estasiati** è il primo modulo di input ed è un modulo primario di destinazione all'interno di realtà mista. Sguardo indica dove l'utente cerca in tutto il mondo e consente di determinare il loro scopo. Nel mondo reale, è in genere verrà esaminato un oggetto che si prevede di interagire con. Questo è lo stesso con sguardo.

Realtà mista auricolari usano la posizione e l'orientamento principale dell'utente di per determinare i vettori sguardo head. È possibile considerare questo vettore come un puntatore laser dritto da direttamente tra gli occhi dell'utente. Quando l'utente cerca nella stanza, l'applicazione può intersecarsi questo ray, con i proprio ologrammi e con il [mapping spaziale](spatial-mapping.md) mesh per determinare quale oggetto reale o virtuale, l'utente potrebbe essere opportuno.

In 2 HoloLens, le interazioni possono essere destinate dalle sguardo head dell'utente o tramite quasi o molto a mano le interazioni.  Su HoloLens (dal 1 ° generazione), le interazioni devono derivano in genere la destinazione da sguardo head dell'utente, piuttosto che tentare per eseguire il rendering o interagire direttamente nella posizione dell'icona della mano. Dopo aver avviato un'interazione, relativi movimenti della mano possono essere usata per controllare la [movimento](gestures.md), come con la [manipolazione o la navigazione](gestures.md#composite-gestures) movimento. Con immersive auricolari, è possibile fare riferimento tramite uno sguardo o che punta in grado di supportare [controller di movimento](motion-controllers.md).

<br>

>[!VIDEO https://www.youtube.com/embed/zCPiZlWdVws]

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Funzionalità</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (dal 1 ° generazione)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></th>
</tr><tr>
<td> Head sguardo</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr><tr>
<td> Sguardo sotto controllo</td><td></td><td style="text-align: center;">✔️</td><td></td>
</tr>
</table>

> [!NOTE]
> Altre indicazioni specifiche su 2 HoloLens [presto](index.md#news-and-notes).


## <a name="uses-of-gaze"></a>Utilizzi di sguardo

Qualità di sviluppatore di realtà mista, è possibile eseguire molte operazioni con sguardo:
* Le app possono intersecarsi sguardo con vntana nella scena per determinare dove è l'attenzione dell'utente.
* L'app può essere indirizzato movimenti e basate sguardo dell'utente, consentendo all'utente di selezionare, attivare, recuperare, scorrere o in caso contrario, interagire con loro vntana pressioni di controller.
* L'app può consentire all'utente di inserire vntana nelle aree del mondo reale, eseguendo che intersecano il ray sguardo con la rete di mapping spaziale.
* L'app è possibile sapere quando l'utente è *non* alla ricerca nella direzione di un oggetto importante, che può comportare l'app per offrire segnali audio e video per attivare verso tale oggetto.

## <a name="cursor"></a>Cursor

La maggior parte delle App devono usare una [cursore](cursors.md) (o un'altra indicazione acustica/visual) per fornire la fiducia degli utenti sugli aspetti che stanno per interagire con. È in genere posizionare il cursore in tutto il mondo in cui il raggio sguardo interagisce prima di tutto un oggetto, che potrebbe essere ologramma o un'area del mondo reale.

![Un esempio visivo del cursore per mostrare sguardo](images/cursor.jpg)<br>
*Un esempio visivo del cursore per mostrare sguardo*

## <a name="giving-action-to-the-users-gaze"></a>Concessione dell'azione a sguardo dell'utente

Dopo avere l'utente è incluso un ologrammi o un oggetto reale con loro sguardo, il passaggio successivo è intervenire su tale oggetto. Sono i metodi principali per un utente intervenire attraverso [movimenti](gestures.md), [movimento controller](motion-controllers.md) e [vocale](voice-input.md).

## <a name="see-also"></a>Vedere anche
* [Input di MR 210: Sguardo](holograms-210.md)
* [Sguardo, gesti e controller di movimento in DirectX](gaze,-gestures,-and-motion-controllers-in-directx.md)
* [Estasiati Unity](gaze-in-unity.md)

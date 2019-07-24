---
title: Billboard e tag-along
description: Gli oggetti con il tabellone sono sempre orientati a fronte dell'utente.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, Billboard, tag-along
ms.openlocfilehash: e33ab0121398742b2e48553c9cbf2c1debdc6abf
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974782"
---
# <a name="billboarding-and-tag-along"></a>Billboard e tag-along

Il tabellone è un concetto di comportamento che può essere applicato a oggetti in realtà mista. Gli oggetti con il tabellone sono sempre orientati a fronte dell'utente. Questa operazione è particolarmente utile con i sistemi di testo e di menu in cui gli oggetti statici posizionati nell'ambiente dell'utente (con blocco globale) sarebbero altrimenti nascosti o illeggibili se un utente dovesse spostarsi.

![HoloLens punto di vista di un sistema di menu che è sempre volto all'utente](images/billboarding-fragments.gif)<br>
*HoloLens punto di vista di un sistema di menu che è sempre volto all'utente*

Gli oggetti con il tabellone abilitato possono essere ruotati liberamente nell'ambiente dell'utente. Possono anche essere vincolati a un singolo asse, a seconda delle considerazioni di progettazione. Tenere presente che gli oggetti di cui è stato effettuato il Billboard possono ritagliare o occludere se sono posizionati troppo vicino ad altri oggetti o in HoloLens, troppo vicino alle superfici analizzate. Per evitare questo problema, considerare il footprint totale che un oggetto può produrre quando ruotato sull'asse abilitato per il tabellone.

## <a name="what-is-a-tag-along"></a>Che cos'è un tag-along?

Tag-Along è un concetto di comportamento che può essere aggiunto agli ologrammi, inclusi gli oggetti con tabellone. Questa interazione è un modo più naturale e descrittivo per ottenere l'effetto del contenuto con blocco Head. Un oggetto tag-along tenta di non lasciare mai la visualizzazione dell'utente. In questo modo, l'utente può interagire liberamente con le informazioni che li fanno davanti, visualizzando anche gli ologrammi al di fuori della visualizzazione diretta.

![Il pannello HoloLens Pins è un ottimo esempio del comportamento dei tag](images/tagalong-1000px.jpg)<br>
*Il menu Start di HoloLens è un ottimo esempio di comportamento di tag-along*

Gli oggetti tag-along hanno parametri che possono ottimizzare il modo in cui si comportano. Il contenuto può essere all'interno o all'esterno della linea di visione dell'utente nel modo desiderato mentre l'utente si sposta all'interno dell'ambiente. Quando l'utente si sposta, il contenuto tenterà di rimanere all'interno della periferia dell'utente scorrendo verso il bordo della visualizzazione, a seconda della velocità con cui un utente sposta il contenuto temporaneamente fuori dalla visualizzazione. Quando l'utente guarda l'oggetto tag-along, viene visualizzato in modo più completo. Il contenuto è sempre un "colpo d'occhio" in modo che gli utenti non dimentichino mai la direzione in cui si trova il contenuto.

I parametri aggiuntivi possono fare in modo che l'oggetto tag-along si trovi collegato alla testa dell'utente da un elastico. L'attenuazione dell'accelerazione o della decelerazione dà peso all'oggetto che lo rende più fisicamente presente. Questo comportamento primaverile è un'offerta che consente all'utente di creare un modello mentale accurato del funzionamento dei tag. L'audio consente di fornire affordances aggiuntive quando gli utenti hanno oggetti in modalità tag-along. L'audio deve rafforzare la velocità di spostamento; una rotazione a capo veloce dovrebbe offrire un effetto acustico più evidente mentre la velocità naturale dovrebbe avere un audio minimo se si verificano effetti.

Proprio come il contenuto con blocco principale, gli oggetti tag-along possono rivelarsi opprimenti o nauseanti se si muovono in modo sfrenato o troppo lungo nella visualizzazione dell'utente. Quando un utente si trova e quindi si arresta rapidamente, i loro sensi indicano che sono stati arrestati. Il loro saldo informa che la loro testa si è interrotta e la loro visione vede il mondo che si interrompe. Tuttavia, se il tag-along continua a essere spostato quando l'utente si arresta, può confonderne i sensi.

## <a name="see-also"></a>Vedere anche
* [Cursori](cursors.md)
* [Interazioni istintive](interaction-fundamentals.md)
* [Comodità](comfort.md)

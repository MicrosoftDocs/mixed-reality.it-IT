---
title: Del billboard e tag-along
description: Gli oggetti del billboard orientarsi sempre in modo che sia l'utente.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, del billboard, tag-along
ms.openlocfilehash: 8215b96aff1f3c2d43e959f04ad83d41ffd32b2a
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603171"
---
# <a name="billboarding-and-tag-along"></a>Del billboard e tag-along

Del billboard è un concetto di comportamento che può essere applicato agli oggetti nella realtà mista. Gli oggetti del billboard orientarsi sempre in modo che sia l'utente. Questo è particolarmente utile con testo e i sistemi consente in cui gli oggetti statici inseriti nell'ambiente dell'utente (bloccata world) sarebbe altrimenti nascoste o illeggibili se un utente per spostarsi all'interno.

![HoloLens prospettiva di un sistema di menu sempre rivolta all'utente](images/billboarding-fragments.gif)<br>
*HoloLens prospettiva di un sistema di menu sempre rivolta all'utente*

Gli oggetti del billboard abilitata è possono ruotare liberamente nell'ambiente dell'utente. Può anche essere vincolati a un singolo asse in base a considerazioni di progettazione. Tenere presente che gli oggetti billboarded possono tagliare o nasconde i colori autonomamente se sono posizionati troppo vicino ad altri oggetti o in HoloLens, troppo vicino analizzati dalle aree. Per evitare questo problema, considerare il footprint complessivo che può produrre un oggetto quando ruotata sull'asse abilitata per billboard.

## <a name="what-is-a-tag-along"></a>Che cos'è un tag-along?

Tag-Along è un concetto di comportamento che può essere aggiunti a vntana, inclusi gli oggetti billboarded. Questa interazione è un modo più naturale e descrittivo per ottenere l'effetto del blocco head contenuto. Un oggetto tag-along tenta di non lasciare mai vista dell'utente. In questo modo l'utente può liberamente interagire con le risorse front di essi inoltre ancora riscontrare il vntana all'esterno di loro diretto della visualizzazione.

![Pannello pin di HoloLens è un ottimo esempio di come si comporta tag-along](images/tagalong-1000px.jpg)<br>
*Nel menu Start di HoloLens è un ottimo esempio di comportamento tag-along*

Gli oggetti tag-Along includono parametri che è possono ottimizzare il modo in cui che si comportano in maniera. Il contenuto può essere interno o all'esterno visuale dell'utente in base alle esigenze mentre l'utente si sposta il proprio ambiente. Quando l'utente sposta, il contenuto verrà effettuato un tentativo di rimanere entro il perimetro dell'utente facendo scorrere verso il bordo della visualizzazione, a seconda rapidità con cui viene spostato un utente può lasciare il contenuto temporaneamente all'esterno della visualizzazione. Quando l'utente gazes verso l'oggetto tag-along, viene visualizzata più dettagliatamente nella visualizzazione. Pensare "riepilogo subito" devono essere sempre in modo che gli utenti non dimenticano mai la direzione è contenuto nel contenuto.

Parametri aggiuntivi possono rendere l'oggetto tag-along è collegato all'inizio dell'utente da un rettangolo. Attenuazione accelerazione o la decelerazione attribuisce un peso all'oggetto rendendo ritiene più fisicamente presente. Questo comportamento spring è un intuitività che consente di compilare un modello mentale accurato del funzionamento tag-along. Audio consente di offrire affordance aggiuntive per quando gli utenti dispongono di oggetti in modalità tag-along. Audio dovrebbe rafforzare la velocità di spostamento; un turno fast head deve fornire un effetto più evidente mentre walking velocità naturale hanno effetti audio se qualsiasi minimo affatto.

Esattamente come contenuto realmente blocco head, possono rivelarsi oggetti tag-along sovraccaricare o nauseating se spostare largamente o spring eccessiva in vista dell'utente. Quando un utente cerca e quindi rapidamente stop, le emozionanti comunicargli che sono interrotte. Il saldo li informa che propria testa ha arrestato l'attivazione, nonché i vede visione l'arresto del mondo l'attivazione. Tuttavia, se tag-along tiene d' trasferimento quando l'utente è stato arrestato, potrebbe confondere i sensi.

## <a name="see-also"></a>Vedere anche
* [Cursori](cursors.md)
* [Nozioni fondamentali di interazione](interaction-fundamentals.md)
* [Comfort](comfort.md)

---
title: Billboard e tag-along
description: Gli oggetti con il tabellone sono sempre orientati a fronte dell'utente.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, Billboard, tag-along
ms.openlocfilehash: 24c4ca8bdc3c6ea1081311102204d4a7f5a95425
ms.sourcegitcommit: 6844930427b658ae31f642c395cd8a3b3cdbf857
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/07/2020
ms.locfileid: "75723180"
---
# <a name="billboarding-and-tag-along"></a>Billboard e tag-along

<br>

<img src="images/UX/MRTK_TagAlong.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<br>

## <a name="what-is-billboarding"></a>Che cos'è il tabellone?

Il tabellone è un concetto di comportamento che può essere applicato a oggetti in realtà mista. Gli oggetti con il tabellone sono sempre orientati a fronte dell'utente. Questa operazione è particolarmente utile con i sistemi di testo e di menu in cui gli oggetti statici posizionati nell'ambiente dell'utente (con blocco globale) sarebbero altrimenti nascosti o illeggibili se un utente dovesse spostarsi.

Gli oggetti con il tabellone abilitato possono essere ruotati liberamente nell'ambiente dell'utente. Possono anche essere vincolati a un singolo asse, a seconda delle considerazioni di progettazione. Tenere presente che gli oggetti di cui è stato effettuato il Billboard possono ritagliare o occludere se sono posizionati troppo vicino ad altri oggetti o in HoloLens, troppo vicino alle superfici analizzate. Per evitare questo problema, considerare il footprint totale che un oggetto può produrre quando ruotato sull'asse abilitato per il tabellone.

<br>

---
## <a name="what-is-a-tag-along"></a>Che cos'è un tag-along?

Tag-Along è un concetto di comportamento che può essere aggiunto agli ologrammi. Un oggetto tag-along tenta di rimanere in un intervallo che consente all'utente di interagire comodamente.

![il pannello HoloLens Pins è un ottimo esempio di comportamento di tag-along](images/tagalong-1000px.jpg)<br>
*Il menu Start di HoloLens è un ottimo esempio di comportamento di tag-along*

Gli oggetti tag-along hanno parametri che possono ottimizzare il modo in cui si comportano. Il contenuto può essere all'interno o all'esterno della linea di visione dell'utente nel modo desiderato mentre l'utente si sposta all'interno dell'ambiente. Quando l'utente si sposta, il contenuto tenterà di rimanere all'interno della periferia dell'utente scorrendo verso il bordo della visualizzazione, a seconda della velocità con cui un utente sposta il contenuto temporaneamente fuori dalla visualizzazione. Quando l'utente guarda l'oggetto tag-along, viene visualizzato in modo più completo. Il contenuto è sempre un "colpo d'occhio" in modo che gli utenti non dimentichino mai la direzione in cui si trova il contenuto.

I parametri aggiuntivi possono fare in modo che l'oggetto tag-along si trovi collegato alla testa dell'utente da un elastico. L'attenuazione dell'accelerazione o della decelerazione dà peso all'oggetto che lo rende più fisicamente presente. Questo comportamento primaverile è un'offerta che consente all'utente di creare un modello mentale accurato del funzionamento dei tag. L'audio consente di fornire affordances aggiuntive quando gli utenti hanno oggetti in modalità tag-along. L'audio deve rafforzare la velocità di spostamento; una rotazione a capo veloce dovrebbe offrire un effetto acustico più evidente mentre la velocità naturale dovrebbe avere un audio minimo se si verificano effetti.

Proprio come il contenuto con blocco principale, gli oggetti tag-along possono rivelarsi opprimenti o nauseanti se si muovono in modo sfrenato o troppo lungo nella visualizzazione dell'utente. Quando un utente si trova e quindi si arresta rapidamente, i loro sensi indicano che sono stati arrestati. Il loro saldo informa che la loro testa si è interrotta e la loro visione vede il mondo che si interrompe. Tuttavia, se il tag-along continua a essere spostato quando l'utente si arresta, può confonderne i sensi.

<br>

---

## <a name="billboarding-and-tag-along-in-mrtk-mixed-reality-toolkit-for-unity"></a>Billboard e tag-along in MRTK (Mixed Reality Toolkit) per Unity
**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** fornisce script per il comportamento di Billboard e tag-along. È sufficiente assegnare lo script Billboard.cs a qualsiasi oggetto per aggiungere il comportamento di Billboard e fare in modo che l'oggetto faccia sempre fronte all'utente. Per aggiungere un comportamento tag-along, usare lo script RadialView.cs. È possibile modificare varie opzioni, ad esempio lerping tempo, distanza e grado.

* [MRTK-Risolutore viste radiali](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html#radialview)
* [MRTK-script Billboard](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Scripts/Utilities/Billboard.cs)


<br>

---

## <a name="see-also"></a>Vedi anche

* [Cursori](cursors.md)
* [Raggio della mano](point-and-commit.md)
* [Button](button.md)
* [Oggetto che supporta interazioni](interactable-object.md)
* [Rettangolo di selezione e barra dell'app](app-bar-and-bounding-box.md)
* [Manipolazione](direct-manipulation.md)
* [Menu a mano](hand-menu.md)
* [Menu adiacente](near-menu.md)
* [Raccolta di oggetti](object-collection.md)
* [Comando vocale](voice-input.md)
* [Tastiera](keyboard.md)
* [Descrizione comando](tooltip.md)
* [Slate](slate.md)
* [Dispositivo di scorrimento](slider.md)
* [Shader](shader.md)
* [Billboarding e tag-along](billboarding-and-tag-along.md)
* [Visualizzazione dello stato](progress.md)
* [Magnetismo di superficie](surface-magnetism.md)

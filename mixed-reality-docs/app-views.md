---
title: Visualizzazioni delle app
description: I due tipi di visualizzazioni nelle app di realtà mista di Windows sono coinvolgenti visualizzazioni e visualizzazioni 2D.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: visualizzazione coinvolgente e concreto di app visualizzazione 2D, slate,
ms.openlocfilehash: 2cf65941616ac6906d40e4b4616311317ac705d3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604730"
---
# <a name="app-views"></a>Visualizzazioni delle app

Le app di Windows possono contenere due tipi di visualizzazioni, **visualizzazioni coinvolgenti** e **visualizzazioni 2D**. Le app possono passare tra le diverse visualizzazioni coinvolgenti e visualizzazioni 2D, che mostra le visualizzazioni 2D in un monitor come finestra o in un auricolare come uno slate. Le app che hanno almeno una visualizzazione immersiva categorizzate come **le App per realtà mista**. Sono App che non hanno mai una vista coinvolgente **2D app**.

## <a name="immersive-views"></a>Visualizzazioni coinvolgenti

Una vista immersiva consente all'app la possibilità di creare vntana in tutto il mondo si o immersion sull'utente in un ambiente virtuale. Quando si disegna un'app nella visualizzazione coinvolgente, non disegna nessuna altra app nello stesso momento&mdash;vntana da più App è composti non insieme. Regolando continuamente la prospettiva da cui il [app esegue il rendering](rendering.md) la scena in modo che corrispondano spostamenti head dell'utente, l'app può eseguire il rendering [bloccato world](coordinate-systems.md) vntana che rimangono in un punto fisso in realtà World oppure può eseguire il rendering di un mondo virtuale che contiene la posizione, mentre un utente si sposta all'interno di esso.

![Quando in una visualizzazione coinvolgente, vntana può essere inserito in tutto il mondo si.](images/designoverview.jpg)<br>
*Quando in una visualizzazione coinvolgente, vntana può essere inserito in tutto il mondo si*

Sul [HoloLens](hololens-hardware-details.md), l'app esegue il rendering relativi vntana sopra automobilista reale dell'utente. In un [visore VR immersivi di realtà mista di Windows](immersive-headset-hardware-details.md), l'utente non è possibile visualizzare il modo reale e in modo che l'app deve eseguire il rendering di tutto ciò che verrà visualizzato all'utente.

Il [realtà mista di Windows home](navigating-the-windows-mixed-reality-home.md) (incluso nel menu Start e vntana è stato inserito tutto l'ambiente) non esegue il rendering in un coinvolgenti visualizzare entrambi. Le notifiche di sistema che si verificano mentre è visualizzata una vista immersiva verranno inoltrate acustico da parte di Cortana su HoloLens, e l'utente può rispondere con input vocale.

Mentre in una visualizzazione coinvolgente, l'app è anche responsabile della gestione di tutti gli input. Input nella realtà mista di Windows è costituito da [estasiati](gaze.md), [movimento](gestures.md) (solo HoloLens), [vocali](voice-input.md) e [movimento controller](motion-controllers.md) (coinvolgenti auricolari solo).

## <a name="2d-views"></a>Visualizzazioni 2D

![Più visualizzazioni 2D disposto intorno a casa la realtà mista di Windows](images/teleportation-640px.png)<br>
*Più App con una visualizzazione 2D per racchiudere la realtà mista di Windows home*

Viene visualizzata un'app con una visualizzazione 2D il [realtà mista di Windows home](navigating-the-windows-mixed-reality-home.md) (operazione talvolta denominata "shell") come uno slate virtuale, viene eseguito il rendering con l'utilità di avvio di app e altri vntana l'utente ha effettuato nel proprio mondo. L'utente può regolare questa lavagna per spostare e ridimensionare, anche se rimane una risoluzione fissa indipendentemente dalle dimensioni. Se prima visualizzazione dell'app è una visualizzazione 2D, il contenuto 2D riempirà lo slate stesso utilizzato per avviare l'app.

In un auricolare desktop, è possibile eseguire qualsiasi App Universal Windows Platform (UWP) eseguite sullo schermo desktop oggi stesso. Queste App sono già rendering delle visualizzazioni 2D oggi stesso e il relativo contenuto verrà visualizzati automaticamente in un Tablet nel mondo dell'utente all'avvio. Le app UWP 2D possono avere come destinazione il **Universal** famiglia di dispositivi per l'esecuzione in entrambe le cuffie desktop e in HoloLens come Slate.

Uno degli utilizzi principali del visualizzazioni 2D sono illustrare un form di immissione di testo che può rendere l'utilizzo di tastiera del sistema. Poiché la shell non è possibile eseguire il rendering nella parte superiore di una vista coinvolgente, l'app deve passare a una visualizzazione 2D per mostrare i tasti di sistema. Le app che desidera accettare input di testo è possono passare a una visualizzazione 2D con una casella di testo. Mentre tale casella di testo ha lo stato attivo, il sistema visualizza la tastiera del sistema, consentendo all'utente di immettere testo.

Si noti che in un PC desktop, un'app può avere visualizzazioni 2D in entrambi i monitor da tavolo e in un auricolare collegati. Ad esempio, è possibile esplorare Edge sullo schermo desktop usando la relativa visualizzazione 2D principale per trovare un video a 360 gradi. Quando si riproduce video specifico, Edge avvierà una visualizzazione immersiva secondaria all'interno delle cuffie, possono visualizzare il contenuto video coinvolgente.

## <a name="see-also"></a>Vedere anche

* [Modello di App](app-model.md)
* [L'aggiornamento di App UWP 2D per realtà mista](building-2d-apps.md)
* [Ottenere un HolographicSpace](getting-a-holographicspace.md)
* [Esplorazione di realtà mista di Windows home](navigating-the-windows-mixed-reality-home.md)
* [Tipi di App di realtà mista](types-of-mixed-reality-apps.md)

---
title: Visualizzazioni delle app
description: I due tipi di visualizzazioni nelle app di realtà mista di Windows sono viste immersive e visualizzazioni 2D.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: visualizzazione immersiva, visualizzazione 2D, Slate, app
ms.openlocfilehash: 2cf65941616ac6906d40e4b4616311317ac705d3
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516902"
---
# <a name="app-views"></a>Visualizzazioni delle app

Le app di Windows possono contenere due tipi di  Visualizzazioni, viste immersive e **visualizzazioni 2D**. Le app possono passare tra le varie viste immersive e le visualizzazioni 2D, mostrando le visualizzazioni 2D in un monitor come una finestra o in una cuffia come una lavagna. Le app con almeno una visualizzazione immersiva vengono categorizzate come **app realtà miste**. Le app che non hanno mai una visualizzazione immersiva sono **app 2D**.

## <a name="immersive-views"></a>Viste immersive

Una visualizzazione immersiva offre all'app la possibilità di creare ologrammi in tutto il mondo o di immergere l'utente in un ambiente virtuale. Quando un'app viene disegnata nella visualizzazione immersiva, nessun'altra app sta disegnando allo stesso tempo&mdash;gli ologrammi di più app non sono composti insieme. Modificando continuamente la prospettiva da cui l' [app esegue il rendering](rendering.md) della scena in modo che corrisponda ai movimenti Head dell'utente, l'app può eseguire il rendering di ologrammi a [blocchi internazionali](coordinate-systems.md) che rimangono in un punto fisso nel mondo reale oppure possono eseguire il rendering di un mondo virtuale che include la posizione in cui un utente si sposta al suo interno.

![In una visualizzazione immersiva, gli ologrammi possono essere posizionati in tutto il mondo.](images/designoverview.jpg)<br>
*In una visualizzazione immersiva, gli ologrammi possono essere posizionati in tutto il mondo*

In [HoloLens](hololens-hardware-details.md)l'app esegue il rendering degli ologrammi sopra gli ambienti reali dell'utente. In una [serie di cuffie a realtà mista di Windows](immersive-headset-hardware-details.md), l'utente non può vedere il mondo reale, quindi l'app deve eseguire il rendering di tutti gli elementi visualizzati dall'utente.

La [Home realtà mista di Windows](navigating-the-windows-mixed-reality-home.md) (inclusi il menu Start e gli ologrammi posizionati intorno all'ambiente) non esegue il rendering in una visualizzazione immersiva. In HoloLens tutte le notifiche di sistema che si verificano mentre una visualizzazione immersiva vengono visualizzate verranno inoltrate in modo udibile da Cortana e l'utente potrà rispondere con l'input vocale.

In una visualizzazione immersiva, l'app è anche responsabile della gestione di tutti gli input. L'input nella realtà mista di Windows è costituito da [sguardi](gaze.md), [movimenti](gestures.md) (solo HoloLens), controller [voce](voice-input.md) e [movimento](motion-controllers.md) (solo cuffie immersive).

## <a name="2d-views"></a>visualizzazioni 2D

![Più visualizzazioni 2D disposte intorno alla Home realtà mista di Windows](images/teleportation-640px.png)<br>
*Più app con una visualizzazione 2D posizionata intorno alla Home realtà mista di Windows*

Un'app con una visualizzazione 2D viene visualizzata nella [Home realtà mista di Windows](navigating-the-windows-mixed-reality-home.md) (talvolta chiamata "Shell") come Slate virtuale, sottoposta a rendering insieme ai lanci di app e ad altri ologrammi che l'utente ha inserito nel proprio mondo. L'utente può modificare questo Slate per spostarlo e ridimensionarlo, sebbene rimanga a una risoluzione fissa indipendentemente dalle dimensioni. Se la prima visualizzazione dell'app è una visualizzazione 2D, il contenuto 2D verrà riempito dallo stesso Slate usato per avviare l'app.

In una cuffia desktop è possibile eseguire le app piattaforma UWP (Universal Windows Platform) (UWP) che vengono eseguite attualmente sul monitor desktop. Queste app già eseguono il rendering delle visualizzazioni 2D e il relativo contenuto verrà visualizzato automaticamente in uno Slate nel mondo dell'utente all'avvio. le app UWP 2D possono essere destinate alla famiglia di dispositivi **Windows. universali** per l'esecuzione sia su cuffie Desktop sia su HoloLens come Slate.

Un utilizzo chiave delle visualizzazioni 2D consiste nel mostrare un modulo di immissione di testo che può utilizzare la tastiera di sistema. Poiché non è possibile eseguire il rendering della shell sopra una visualizzazione immersiva, l'app deve passare a una visualizzazione 2D per visualizzare la tastiera di sistema. Le app che vogliono accettare input di testo possono passare a una visualizzazione 2D con una casella di testo. Quando tale casella di testo ha lo stato attivo, il sistema Visualizza la tastiera di sistema, consentendo all'utente di immettere testo.

Si noti che in un PC desktop un'app può avere visualizzazioni 2D sia sul monitor desktop che su una cuffia collegata. È possibile, ad esempio, esplorare Edge sul monitor desktop usando la visualizzazione 2D principale per trovare un video di 360 gradi. Quando si riproduce il video, Edge avvierà una visualizzazione immersiva secondaria all'interno dell'auricolare per visualizzare il contenuto video immersivo.

## <a name="see-also"></a>Vedere anche

* [Modello di app](app-model.md)
* [Aggiornamento di app UWP 2D per la realtà mista](building-2d-apps.md)
* [Ottenere un HolographicSpace](getting-a-holographicspace.md)
* [Esplorazione dello spazio iniziale di Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)
* [Tipi di app di realtà mista](types-of-mixed-reality-apps.md)

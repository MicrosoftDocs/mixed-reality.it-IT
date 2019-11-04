---
title: Esercitazione introduttiva-4. Inserimento di contenuto dinamico e utilizzo di risolutori
description: Completa questo corso per apprendere come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 93fcdcdfb7941f377b2f3f7786368783415b1ef2
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438409"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a>4. posizionamento del contenuto dinamico e utilizzo dei risolutori

Gli ologrammi entrano a far parte di HoloLens 2 quando seguono in modo intuitivo l'utente e vengono inseriti nell'ambiente fisico in modo da rendere l'interazione semplice ed elegante. In questa esercitazione vengono illustrate le modalità per posizionare in modo dinamico gli ologrammi usando gli strumenti di posizionamento disponibili di MRTK (noti come risolutori) per risolvere scenari di posizionamento spaziali complessi. In MRTK, i risolutori sono un sistema di script e comportamenti usati per consentire agli elementi dell'interfaccia utente di seguire l'utente, l'utente o altri oggetti del gioco nella scena. Possono anche essere usati per l'ancoraggio rapido a determinate posizioni, rendendo così più intuitiva l'applicazione. 

## <a name="objectives"></a>Obiettivi

* Introdurre i risolutori di MRTK
* Usare i risolutori per fare in modo che una raccolta di pulsanti segua l'utente
* Usare i risolutori per fare in modo che un oggetto gioco segua le mani tracciate dell'utente

## <a name="instructions"></a>Istruzioni

### <a name="location-of-solvers-in-the-mrtk"></a>Posizione dei risolutori in MRTK
 Per trovare i resolver disponibili nel progetto, cercare nella cartella MRTK SDK (cartella MixedRealityToolkit. SDK). Nella cartella Utilities viene visualizzata la cartella solvers, come illustrato nell'immagine seguente.

![Risolutori](images/lesson3_chapter1_step1im.PNG)

>Nota: in questa lezione, verrà esaminata solo l'implementazione del Risolutore orbitale e del Risolutore RadialView. Per altre informazioni sull'intera gamma di risolutori disponibili in MRTK, vedere: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html

### <a name="use-a-solver-to-follow-the-user"></a>Usare un risolutore per seguire l'utente
L'obiettivo di questo capitolo è quello di migliorare la raccolta dei pulsanti creata in precedenza in modo che segua la direzione dello sguardo dell'utente. Nella versione precedente di MRTK e HoloToolkit è stato definito funzionalità Tagalong.

1. Seleziona l'oggetto padre Button Collection (Raccolta pulsanti) della lezione precedente.

![Immagine lezione 3 capitolo 2 passaggio 1](images/Lesson3_chapter2_step1im.PNG)

2. Nel pannello di controllo fare clic sul pulsante Aggiungi componente e cercare Orbital. Verrà visualizzato il componente orbitale. Selezionarlo per aggiungere il componente orbitale all'oggetto del gioco della raccolta dei pulsanti.

![Immagine lezione 3 capitolo 2 passaggio 2](images/Lesson3_Chapter2_step2im.PNG)

>Nota: quando si aggiunge il componente Orbital si noterà che il sistema aggiunge anche il componente SolverHandler, che è un componente obbligatorio. 

3. Per configurare la raccolta di pulsanti in modo che segua l'utente, è necessario implementare le regolazioni seguenti (vedere l'immagine seguente):
- Nello script Orbital impostare l'elenco a discesa tipo orientamento su solo imbardata. In questo modo, un solo asse dell'oggetto ruota seguendo l'utente.
- Imposta l'offset locale su 0 in tutti gli assi. Impostare offset globale su x = 0, y =-0,1 e z = 0,6. Questo blocca lo spostamento dell'oggetto in modo che, quando l'utente cambia l'altezza, l'oggetto rimanga a un'altezza fissa nell'ambiente fisico, consentendo allo stesso tempo di seguire l'utente mentre l'utente si sposta sull'ambiente. Questi valori possono essere modificati per ottenere un'ampia varietà di comportamenti.
- Per un comportamento successivo, in base al quale i pulsanti seguono solo la visualizzazione dell'utente dopo che l'utente ha trasformato la propria intestazione in modo sufficientemente lungo, è possibile selezionare la casella di controllo Usa angolo di avanzamento per l'offset globale (Nota: questo titolo può essere troncato in alcune schermate, come nell'immagine seguente). Ad esempio, per fare in modo che l'oggetto segua l'utente solo ogni 90 gradi, impostare il numero di passaggi uguale a 4 (contrassegnato da una freccia verde nell'esempio seguente). 

![Immagine lezione 3 capitolo 2 passaggio 3](images/Lesson3_chapter2_step3im.PNG)

### <a name="enabling-objects-to-follow-tracked-hands"></a>Abilitazione degli oggetti per seguire le mani tracciate

In questa sezione si configurerà l'oggetto Game Cube creato in precedenza per seguire le mani rilevate dall'utente usando il Risolutore RadialView.

1. Consente di selezionare l'oggetto cubo nella gerarchia BaseScene. Fare clic su Aggiungi componente nel pannello di controllo. 

![Immagine lezione 3 capitolo 3 passaggio 1](images/Lesson3_Chapter3_step1im.PNG)

2. Digitare RadialView nella casella di ricerca e selezionare il componente RadialView per aggiungerlo al cubo. Il componente SolverHandler verrà inoltre aggiunto automaticamente al cubo.

3. Per modificare il RadialView in modo che segua la mano sinistra anziché l'intestazione, selezionare il menu a discesa accanto all'opzione oggetto rilevato per fare riferimento, quindi selezionare giunzione mano sinistra dal menu.

![Immagine lezione 3 capitolo 3 passaggio 3](images/Lesson3_chapter3_step3im.PNG)

4. Dopo aver selezionato l'articolazione della mano, puoi scegliere quale parte della mano dovrà seguire il cubo. In questo esempio, useremo il polso. Accanto all'opzione rilevata congiuntamente, selezionare il menu a discesa e selezionare polso. 

![Immagine lezione 3 capitolo 3 passaggio 4](images/Lesson3_chapter3_step4im.PNG)

5. Imposta la distanza massima e quella minima su 0 in modo che non sia definita alcuna distanza tra il cubo e il polso dell'utente. Una volta impostato, il cubo sarà perfettamente allineato al polso. È inoltre possibile modificare il campo direzione riferimento per regolare il comportamento di orientamento del cubo, ad esempio se si desidera consentire all'oggetto di ruotare con il polso dell'utente impostando la direzione di riferimento su Orient con l'oggetto rilevato.

![Immagine lezione 3 capitolo 3 passaggio 5](images/Lesson3_chapter3_step5im.PNG)

## <a name="congratulations"></a>Lezione completata
In questa esercitazione si è appreso come usare i resolver di MRTK per fare in modo che un'interfaccia utente segua in modo intuitivo l'utente. Hai anche appreso come collegare un risolutore a un oggetto gioco (ad esempio un cubo) in modo che segua le mani tracciate dell'utente. Per altre informazioni su questi e altri risolutori inclusi in MRTK, visita la [pagina della documentazione dei risolutori di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html).

[Lezione successiva: 5. interazione con oggetti 3D](mrlearning-base-ch4.md)


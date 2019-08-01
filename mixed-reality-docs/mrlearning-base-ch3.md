---
title: Esercitazione introduttiva-4. Inserimento di contenuto dinamico e utilizzo di risolutori
description: Completa questo corso per informazioni su come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: a73be40180e582058ae3e9bbaeffebe462042fbb
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/01/2019
ms.locfileid: "68701995"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a>4. Inserimento di contenuto dinamico e utilizzo di risolutori

Gli ologrammi prendono vita in HoloLens 2 quando seguono l'utente in modo intuitivo e vengono posizionati nell'ambiente fisico in modo da rendere l'interazione semplice ed elegante. In questa esercitazione vengono illustrate le modalità per posizionare in modo dinamico gli ologrammi usando gli strumenti di posizionamento disponibili di MRTK, noti come risolutori, per risolvere scenari complessi di posizionamento spaziale. In MRTK, i risolutori sono un sistema di script e comportamenti usati per consentire agli elementi dell'interfaccia utente di seguire l'utente, l'utente o altri oggetti del gioco nella scena. Possono anche essere usati per l'ancoraggio rapido a determinate posizioni, rendendo così più intuitiva l'applicazione. 

## <a name="objectives"></a>Obiettivi

* Introdurre i risolutori di MRTK
* Usare i risolutori per fare in modo che una raccolta di pulsanti segua l'utente
* Usare i risolutori per fare in modo che un oggetto gioco segua le mani tracciate dell'utente

## <a name="instructions"></a>Istruzioni

### <a name="location-of-solvers-in-the-mrtk"></a>Posizione dei risolutori in MRTK
 Per trovare i risolutori disponibili nel progetto, cerca nella cartella di MRTK SDK (MixedRealityToolkit.SDK). Nella cartella Utilities visualizzerai la cartella Solvers, come illustrato nell'immagine seguente.

![Risolutori](images/lesson3_chapter1_step1im.PNG)

>Nota: In questa lezione verrà esaminata solo l'implementazione del Risolutore di Orbital e del Risolutore RadialView. Per altre informazioni sulla gamma completa dei risolutori disponibili in MRTK, vedi: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html

### <a name="use-a-solver-to-follow-the-user"></a>Usare un risolutore per seguire l'utente
L'obiettivo di questo capitolo è quello di migliorare la raccolta dei pulsanti creata in precedenza in modo che segua la direzione dello sguardo dell'utente. Nella versione precedente di MRTK e HoloToolkit, questo è stato definito funzionalità Tagalong.

1. Seleziona l'oggetto padre Button Collection (Raccolta pulsanti) della lezione precedente.

![Immagine lezione 3 capitolo 2 passaggio 1](images/Lesson3_chapter2_step1im.PNG)

2. Nel pannello di controllo fare clic sul pulsante Aggiungi componente e cercare Orbital. Viene visualizzato il componente Orbital (Orbitale). Selezionalo per aggiungere il componente Orbital (Orbitale) all'oggetto gioco Button Collection (Raccolta pulsanti).

![Immagine lezione 3 capitolo 2 passaggio 2](images/Lesson3_Chapter2_step2im.PNG)

>Nota: quando aggiungi il componente noterai che nella scheda di controllo vengono aggiunti automaticamente lo script Orbital (Orbitale) e lo script Solver Handler (Gestore risolutori), un componente obbligatorio. 

3. Per configurare la raccolta di pulsanti in modo che segua l'utente, è necessario implementare le regolazioni seguenti (vedere l'immagine seguente):
- Nello script Orbital impostare l'elenco a discesa tipo orientamento su solo imbardata. In questo modo, un solo asse dell'oggetto ruota seguendo l'utente.
- Imposta l'offset locale su 0 in tutti gli assi. Imposta l'offset globale su x = 0, y = -0.1 e z = 0.6. Questa impostazione blocca il movimento dell'oggetto in modo che, quando l'utente modifica l'altezza, l'oggetto rimane a un'altezza fissa dell'ambiente fisico, continuando comunque a seguire l'utente che si sposta nell'ambiente. Questi valori possono essere modificati per ottenere un'ampia varietà di comportamenti.
- Per un comportamento successivo, in base al quale i pulsanti seguono solo la visualizzazione dell'utente dopo che l'utente ha trasformato la propria intestazione in modo sufficientemente lungo, è possibile selezionare la casella di controllo Usa angolo di avanzamento per l'offset globale (Nota: questo titolo può essere troncato in alcune schermate, come nell'immagine seguente. Ad esempio, affinché l'oggetto segua l'utente solo ogni 90 gradi, imposta il numero di passaggi su 4 (contrassegnati da una freccia verde nell'esempio a sinistra). 

![Immagine lezione 3 capitolo 2 passaggio 3](images/Lesson3_chapter2_step3im.PNG)

### <a name="enabling-objects-to-follow-tracked-hands"></a>Abilitazione degli oggetti per seguire le mani tracciate

In questa sezione configureremo l'oggetto gioco cubo creato in precedenza per seguire le mani tracciate dell'utente con il risolutore RadialView.

1. Seleziona l'oggetto cubo nella gerarchia della scena di base. Fare clic su Aggiungi componente nel pannello di controllo. 

![Immagine lezione 3 capitolo 3 passaggio 1](images/Lesson3_Chapter3_step1im.PNG)

2. Digitare RadialView nella casella di ricerca e selezionare il componente RadialView per aggiungerlo al cubo. Anche il componente Solver Handler (Gestore risolutori) verrà aggiunto automaticamente al cubo.

3. Modifica la vista radiale in modo che non segua la testa, ma la mano sinistra. Selezionare il menu a discesa accanto all'opzione oggetto rilevato per fare riferimento a. Quindi selezionare Hand join Left dal menu.

![Immagine lezione 3 capitolo 3 passaggio 3](images/Lesson3_chapter3_step3im.PNG)

4. Dopo aver selezionato l'articolazione della mano, puoi scegliere quale parte della mano dovrà seguire il cubo. In questo esempio, useremo il polso. Accanto all'opzione rilevata congiunzione della mano selezionare il menu a discesa e selezionare polso. 

![Immagine lezione 3 capitolo 3 passaggio 4](images/Lesson3_chapter3_step4im.PNG)

5. Imposta la distanza massima e quella minima su 0 in modo che non sia definita alcuna distanza tra il cubo e il polso dell'utente. Una volta impostato, il cubo sarà perfettamente allineato al polso. È inoltre possibile modificare il campo direzione riferimento per regolare il comportamento di orientamento del cubo, ad esempio se si desidera consentire all'oggetto di ruotare con il polso dell'utente impostando la direzione di riferimento su Orient con l'oggetto rilevato.

![Immagine lezione 3 capitolo 3 passaggio 5](images/Lesson3_chapter3_step5im.PNG)

## <a name="congratulations"></a>Lezione completata
In questa esercitazione si è appreso come usare i resolver di MRTK per fare in modo che un'interfaccia utente segua in modo intuitivo l'utente. Hai anche appreso come collegare un risolutore a un oggetto gioco (ad esempio un cubo) in modo che segua le mani tracciate dell'utente. Per altre informazioni su questi e altri risolutori inclusi in MRTK, visita la [pagina della documentazione dei risolutori di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html).

[Lezione successiva: 5.    Interazione con oggetti 3D](mrlearning-base-ch4.md)


---
title: Modulo di Base Learning MR - risolutori e posizionamento del contenuto dinamico
description: Completare questo corso di informazioni su come implementare il riconoscimento di volti di Azure all'interno di un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: realtà mista, hololens, esercitazione di unity,
ms.openlocfilehash: 04ed2217c473c5649c1850fcc757d866e23b9b56
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730899"
---
# <a name="mr-learning-base-module---dynamic-content-placement-and-solvers"></a>Modulo di Base Learning MR - risolutori e posizionamento del contenuto dinamico

Ologrammi vita caratterizzati da in 2 HoloLens quando seguire l'utente in modo intuitivo e vengono inseriti nell'ambiente fisico in modo da semplificare l'interazione semplice ed elegante. Nella lezione 3, verranno analizzati i modi per inserire in modo dinamico vntana usando gli strumenti disponibili posizionamento del MRTK, noti come "risolutori". Il modo in cui che vengono risolti gli algoritmi complessi posizionamento spaziali sono note come "risolutori". Nel MRTK risolutori costituiscono un sistema di script e i comportamenti che utilizziamo per essere in grado di consentire agli elementi dell'interfaccia utente seguire l'utente, l'utente o altri oggetti del gioco nella scena. Possono anche essere utilizzati per determinate posizioni allineare in modo rapido, rendendo più intuitivo dell'applicazione. 

## <a name="objectives"></a>Obiettivi

* Introdurre Risolutori di MRTK
* Risolutori di utilizzo per avere una raccolta di pulsanti di seguono l'utente
* Risolutori di utilizzo per avere un oggetto gioco seguono mani registrati dell'utente

## <a name="instructions"></a>Istruzioni

### <a name="location-of-solvers-in-the-mrtk"></a>Posizione dei risolutori nel MRTK
 Per trovare i risolutori disponibili nel progetto, cercare nella cartella MRTK SDK (MixedRealityToolkit.SDK cartella), quindi nella cartella utilities si verrà visualizzata la cartella risolutori, come illustrato nell'immagine seguente.

![Risolutori](images/lesson3_chapter1_step1im.PNG)

>Nota: In questa lezione verranno esaminate solo sull'implementazione del Risolutore "Orbital" e il Risolutore "RadialView". Per altre informazioni sull'intervallo completo di risolutori disponibile nel MRTK, visitare: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html

### <a name="use-a-solver-to-follow-the-user"></a>Usare un Risolutore per seguire l'utente
L'obiettivo di questo capitolo è migliorare l'insieme di pulsanti creata in precedenza in modo che segua direzione sguardo dell'utente. Nella versione precedente del MRTK e HoloToolkit, questa è stata definita come una funzionalità di "taglong".

1. Selezionare l'oggetto padre di insieme di pulsanti nella lezione precedente.

![Lezione 3 Chapter2 Step1im](images/Lesson3_chapter2_step1im.PNG)

2. Nel Pannello di controllo, fare clic sul pulsante "Aggiungi componente" e cercare "orbitali". Il componente orbital dovrebbe essere visualizzato. Selezionare il componente orbital all'oggetto gioco insieme di pulsanti.

![Lezione 3 Chapter2 Step2im](images/Lesson3_Chapter2_step2im.PNG)

>Nota: Quando si aggiunge il componente si noterà che il sistema consente di aggiungere lo script orbital e lo script di gestore del Risolutore nella scheda inspector, che è un componente obbligatorio. 

3. Per configurare l'insieme di pulsanti per seguire l'utente, è necessario implementare le modifiche seguenti (vedere anche l'immagine seguente):
- Nello script Orbital, impostare l'elenco di riepilogo a discesa "tipo di orientamento" a "Solo rotazione". In questo modo, in modo che solo un asse dell'oggetto ruota come indicato di seguito l'utente.
- Impostare l'offset locale su 0 in tutti gli assi. Impostare l'Offset del mondo su x = 0, y = -0.1 e z = 0,6. Questo blocca lo spostamento dell'oggetto in modo che quando l'utente modifica l'altezza, l'oggetto rimarrà abbia un'altezza fissa dell'ambiente fisico, consentendo comunque seguire l'utente quando l'utente sposta sull'ambiente. Questi valori possono essere modificati per ottenere un intervallo wade dei comportamenti.
- Per un comportamento seguire in base al quale i pulsanti seguono solo la visualizzazione dell'utente dopo che l'utente diventa sufficientemente testa la propria, è possibile selezionare la casella di controllo "Usa angolo esecuzione di un'istruzione per l'offset world" (Nota: Questo titolo potrebbe essere troncato in alcune schermate, come nell'immagine seguente.) Ad esempio, affinché l'oggetto seguire l'utente solo ogni 90 gradi, impostare il numero di passaggi uguale a 4 (contrassegnati da una freccia verde nell'esempio a sinistra). 

![Lezione 3 Chapter2 Step3im](images/Lesson3_chapter2_step3im.PNG)

### <a name="enabling-objects-to-follow-tracked-hands"></a>Consentire agli oggetti di seguire le mani rilevate

In questa sezione si configurerà l'oggetto gioco cubo creato in precedenza per seguire le mani rilevate dell'utente con il Risolutore RadialView.

1. Selezionare l'oggetto cubo nella gerarchia di BaseScene. Fare clic su "Aggiungi componente" nel Pannello di controllo. 

![Lezione 3 Chapter3 Step1im](images/Lesson3_Chapter3_step1im.PNG)

2. Digitare "RadialView" nella casella di ricerca e selezionare il componente RadialView per aggiungerlo al cubo. Il componente gestore Risolutore anche verrà aggiunto automaticamente al cubo.

3. Modificare la visualizzazione radiale per non seguire la testa ma si attengono a sinistra. Selezionare il menu a discesa accanto all'opzione "rilevati oggetti per fare riferimento a". Quindi selezionare "passare giunto a sinistra" dal menu di scelta.

![Lezione 3 Chapter3 Step3im](images/Lesson3_chapter3_step3im.PNG)

4. Dopo aver selezionato la giunzione manualmente, è possibile scegliere quale parte della lancetta desiderato del cubo da seguire. In questo esempio si userà il polso. Accanto all'opzione "joint mano rilevate" selezionare il menu a discesa e selezionare polso. 

![Lezione 3 Chapter3 Step4im](images/Lesson3_chapter3_step4im.PNG)

5. Impostare le distanze massime e minime su 0 in modo che il cubo non avrà alcun distanza tra i dati e del polso dell'utente. Una volta impostato, il cubo verrà essere perfettamente allineato con il polso. È anche possibile modificare il campo "Riferimento direzione" per modificare il comportamento del modo in cui il cubo è orientata ai servizi (ad esempio, se si vuole consentire l'oggetto ruota con polso dell'utente, impostare la direzione di riferimento a "Orienta con oggetto rilevate")

![Lezione 3 Chapter3 Step5im](images/Lesson3_chapter3_step5im.PNG)

### <a name="congratulations"></a>È stata completata
La procedura è stata completata. In questa lezione è stato descritto come utilizzare Risolutori di MRTK per avere un'interfaccia utente in modo intuitivo seguire l'utente. Inoltre appreso come collegare un Risolutore a un oggetto gioco (vale a dire, cubo) seguire mani registrati dell'utente. Per altre informazioni su questi e altri risolutori inclusi con il MRTK, è possibile visitare il [pagina della documentazione risolutori MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html).

[Lezione successiva: Interazione dell'oggetto 3D](mrlearning-base-ch4.md)


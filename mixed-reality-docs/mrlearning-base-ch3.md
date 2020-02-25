---
title: Esercitazione introduttiva-4. Inserimento di contenuto dinamico e utilizzo di risolutori
description: Completa questo corso per informazioni su come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 5463f363291790fd5e5d76ffa322a61ca7bf8e31
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553884"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a>4. posizionamento del contenuto dinamico e utilizzo dei risolutori
<!-- Consider renaming to 'Placing dynamic content using Solvers' -->

Gli ologrammi entrano a far parte di HoloLens 2 quando seguono in modo intuitivo l'utente e vengono inseriti nell'ambiente fisico in modo da rendere l'interazione semplice ed elegante. In questa esercitazione vengono illustrate le modalità per posizionare in modo dinamico gli ologrammi usando gli strumenti di posizionamento disponibili di MRTK, noti come risolutori, per risolvere scenari di posizionamento spaziali complessi. In MRTK, i risolutori sono un sistema di script e comportamenti usati per consentire agli elementi dell'interfaccia utente di seguire l'utente, l'utente o altri oggetti del gioco nella scena. Possono anche essere usati per l'ancoraggio rapido a determinate posizioni, rendendo così più intuitiva l'applicazione.

## <a name="objectives"></a>Obiettivi

* Introdurre i risolutori di MRTK
* Usare i resolver per avere una raccolta di pulsanti che seguono l'utente
* Usare i resolver per fare in modo che un oggetto gioco segua le lancette rilevate dall'utente

## <a name="location-of-solvers-in-the-mrtk"></a>Percorso dei risolutori in MRTK

 I risolutori di MRTK si trovano nella cartella SDK di MRTK. Per visualizzare i resolver disponibili nel progetto, nella finestra del progetto passare a **assets** > **MixedRealityToolkit. SDK** > **features** > **Utilities** > **Resolvers**:

![mrlearning-base](images/mrlearning-base/tutorial3-section1-step1-1.png)

In questa esercitazione verrà esaminata l'implementazione del Risolutore orbitale e del Risolutore di viste radiali. Per altre informazioni sull'intera gamma di resolver disponibili in MRTK, vedere la guida per i [risolutori](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) nel portale della documentazione di [MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="use-a-solver-to-follow-the-user"></a>Usare un Risolutore per seguire l'utente
<!-- Consider renaming to 'Use a Solver to have an object follow the user' -->

In questa sezione verrà migliorata la raccolta dei pulsanti creata nell'esercitazione precedente in modo che segua la direzione dello sguardo dell'utente. Inoltre, verrà configurato anche il Risolutore, in modo che la raccolta dei pulsanti sia sempre:

* Ruotato in parallelo alla direzione di lettura dell'utente, per la lettura naturale da sinistra a destra
* Posizionato leggermente sotto la direzione degli sguardi orizzontali dell'utente, quindi non ostruisce gli altri oggetti che verrà aggiunto più avanti in questa esercitazione
* Posizionato approssimativamente a metà del braccio dall'utente, quindi è possibile premere facilmente i pulsanti

A tale scopo, si utilizzerà il **Risolutore orbitale** che blocca l'oggetto in una posizione e un offset specificati dall'oggetto a cui si fa riferimento.

### <a name="1-add-the-orbital-solver"></a>1. aggiungere il Risolutore orbitale

Nella finestra gerarchia selezionare l'oggetto **buttoncollection** , quindi nella finestra di controllo usare il pulsante **Aggiungi componente** per aggiungere il componente **Orbital (script)** all'oggetto buttoncollection.

> [!NOTE]
> Quando si aggiunge un Risolutore, in questo caso il componente Orbital (script), il componente di gestione del Risolutore (script) viene aggiunto automaticamente perché è necessario per il Risolutore.

### <a name="2-configure-the-orbital-solver"></a>2. configurare il Risolutore di orbitali

Configurare il componente **gestore Risolutore (script)** :

* Verificare che il **tipo di destinazione rilevata** sia impostato su **Head**

Configurare il componente **Orbital (script)** :

* Verificare che **tipo orientamento** sia impostato su **Segui oggetto rilevato**
* Reimposta **offset locale** su X = 0, Y = 0, Z = 0
* Imposta **offset globale** su X = 0, Y =-0,4, Z = 0,3

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step2-1.png)

### <a name="3-test-the-orbital-solver-using-the-in-editor-simulation"></a>3. testare il Risolutore Orbital usando la simulazione in-Editor

Premere il pulsante Riproduci per attivare la modalità di gioco e premere e tenere premuto il pulsante destro del mouse per ruotare la direzione dello sguardo e notare quanto segue:

* La posizione di trasformazione di Buttoncollection è ora determinata dalle impostazioni del Risolutore
* Il cubo, che non è influenzato dal Risolutore, rimane nella stessa posizione

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step3-1.png)

> [!TIP]
> Se il raggio della fotocamera non è visibile nella finestra della scena, verificare che il menu gizmos sia abilitato. Per altre informazioni sul menu gizmos e su come usarlo per ottimizzare la visualizzazione della scena, è possibile visitare la documentazione del <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">menu dei gizmo</a> di Unity.
>
> Per visualizzare la scena e la finestra di gioco affiancata, come illustrato nell'immagine precedente, trascinare semplicemente la finestra del gioco sul lato destro della finestra della scena. Per ulteriori informazioni sulla personalizzazione dell'area di lavoro, è possibile visitare la pagina relativa alla <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">personalizzazione dell'area di lavoro</a> di Unity.

## <a name="enabling-objects-to-follow-tracked-hands"></a>Abilitazione degli oggetti per seguire le mani tracciate

In questa sezione si configurerà l'oggetto cubo creato nell'esercitazione precedente, in modo che segua le mani rilevate dall'utente, in particolare il polso destro. Inoltre, il Risolutore viene configurato in modo che il cubo:

* Modifica l'orientamento con la rotazione a mano dell'utente
* Posizionato sul polso dell'utente

A tale scopo, si utilizzerà il **Risolutore di viste radiali** , che consente di mantenere l'oggetto all'interno di un cono di visualizzazione di cui viene eseguito il cast dall'oggetto

### <a name="1-add-the-radial-view-solver"></a>1. aggiungere il Risolutore di visualizzazione radiale

Nella finestra gerarchia selezionare l'oggetto **cubo** , quindi nella finestra di controllo usare il pulsante **Aggiungi componente** per aggiungere l'oggetto del cubo del componente di **visualizzazione radiale (script)** .

### <a name="2-configure-the-radial-view-solver"></a>2. configurare il Risolutore di viste radiali

Configurare il componente **gestore Risolutore (script)** :

* Modificare il **tipo di destinazione rilevata** in **join a mano**
* Modificare la **mano rilevata** a **destra**
* Modificare la **giunzione della mano registrata** fino al **polso**

Configurare il componente **visualizzazione radiale (script)** :

* Modificare la **direzione di riferimento** in **orientata a oggetti**, quindi selezionare la casella di controllo **Orient to Reference Direction**
* Modificare la distanza **minima** e la **distanza massima** con 0

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step2-1.png)

### <a name="3-test-the-radial-view-solver-using-the-in-editor-simulation"></a>3. testare il Risolutore di viste radiali usando la simulazione in-Editor

Premere il pulsante Riproduci per attivare la modalità di gioco e quindi tenere premuto la barra spaziatrice per visualizzare la mano. Spostare il cursore del mouse per spostare la mano, quindi fare clic e tenendo premuto il pulsante sinistro del mouse per ruotare la mano:

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step3-1.png)

## <a name="congratulations"></a>Complimenti

In questa esercitazione si è appreso come usare i resolver di MRTK per fare in modo che un'interfaccia utente segua in modo intuitivo l'utente. Si è inoltre appreso come alleghire un risolutore a un oggetto, ad esempio Cube, per seguire le mani rilevate dall'utente. Per ulteriori informazioni su questi e altri risolutori inclusi in MRTK, è possibile visitare la guida per i [risolutori](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) nel [portale della documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

[Esercitazione successiva: 5. interazione con oggetti 3D](mrlearning-base-ch4.md)

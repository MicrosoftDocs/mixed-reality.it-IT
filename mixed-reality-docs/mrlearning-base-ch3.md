---
title: Esercitazioni introduttive - 4 Inserimento di contenuto dinamico e uso dei risolutori
description: Completa questo corso per informazioni su come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: 8a85ab560d0e6b36b589970b4d5b8a441ed2bbe2
ms.sourcegitcommit: 536fd45b48a70bbeca1454cef517ae007225e533
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/27/2020
ms.locfileid: "80362037"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a>4. Inserimento di contenuto dinamico e uso dei risolutori
<!-- Consider renaming to 'Placing dynamic content using Solvers' -->

Gli ologrammi prendono vita in HoloLens 2 quando seguono l'utente in modo intuitivo e vengono posizionati nell'ambiente fisico in modo da rendere l'interazione semplice ed elegante. In questa esercitazione verranno analizzate le modalità per posizionare in modo dinamico gli ologrammi usando gli strumenti di posizionamento disponibili in MRTK, noti come "risolutori", per risolvere scenari complessi di posizionamento nello spazio. In MRTK i risolutori costituiscono un sistema di script e comportamenti usati per consentire agli elementi dell'interfaccia utente di seguire te, l'utente o altri oggetti gioco nella scena. Possono anche essere usati per l'ancoraggio rapido a determinate posizioni, rendendo così più intuitiva l'applicazione.

## <a name="objectives"></a>Obiettivi

* Illustrare i risolutori di MRTK
* Usare i risolutori per fare in modo che una raccolta di pulsanti segua l'utente
* Usare i risolutori per fare in modo che un oggetto gioco segua le mani tracciate dell'utente

## <a name="location-of-solvers-in-the-mrtk"></a>Posizione dei risolutori in MRTK

 I risolutori di MRTK si trovano nella cartella MRTK SDK. Per visualizzare i risolutori disponibili in un progetto, nella finestra Project (Progetto) passa a **Assets (Asset)**  > **MixedRealityToolkit.SDK** > **Features (Funzionalità)**  > **Utilities (Utilità)**  > **Solvers** (Risolutori):

![mrlearning-base](images/mrlearning-base/tutorial3-section1-step1-1.png)

In questa esercitazione verrà esaminata l'implementazione dei risolutori Orbital (Orbitale) e Radial View (Vista radiale). Per altre informazioni sull'intera gamma di risolutori disponibili in MRTK, puoi fare riferimento alla guida [Risolutori](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) nel [portale della documentazione si MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="use-a-solver-to-follow-the-user"></a>Usare un risolutore per seguire l'utente
<!-- Consider renaming to 'Use a Solver to have an object follow the user' -->

In questa sezione verrà migliorata la raccolta di pulsanti creata nell'esercitazione precedente in modo che segua la direzione dello sguardo dell'utente. Inoltre, il risolutore verrà configurato in modo che la raccolta di pulsanti sia sempre:

* Ruotata in parallelo rispetto alla direzione di lettura dell'utente, per la lettura naturale da sinistra a destra
* Posizionata al di sotto della direzione dello sguardo orizzontale dell'utente in modo da non ostacolare gli altri oggetti che aggiungerai più avanti in questa esercitazione
* Posizionata approssimativamente a metà della portata di braccio dell'utente, in modo che sia possibile selezionare facilmente i pulsanti

A tale scopo, userai il **risolutore Orbital (Orbitale)** che blocca l'oggetto in una posizione e con un offset specifici rispetto all'oggetto di riferimento.

### <a name="1-add-the-orbital-solver"></a>1. Aggiungere il risolutore Orbital (Orbitale)

Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **ButtonCollection**, quindi nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Orbital (Script)** (Orbitale - Script) all'oggetto ButtonCollection.

> [!NOTE]
> Quando aggiungi un risolutore, in questo caso il componente Orbital (Script) (Orbitale - Script), viene aggiunto automaticamente il componente Solver Handler (Script) (Gestore risolutori - Script) perché è richiesto dal risolutore.

### <a name="2-configure-the-orbital-solver"></a>2. Configurare il risolutore Orbital (Orbitale)

Configura il componente **Solver Handler (Script)** (Gestore risolutori - Script):

* Verifica che per **Tracked Target Type** (Tipo destinazione tracciata) sia impostato il valore **Head** (Testa)

Configura il componente **Orbital (Script)** (Orbitale - Script):

* Verifica che per **Orientation Type** (Tipo di orientamento) sia impostato il valore **Follow Tracked Object** (Segui oggetto tracciato)
* Reimposta **Local Offset** (Offset locale) su X = 0, Y = 0, Z = 0
* Modifica il valore di **World Offset** (Offset globale) impostando X = 0, Y = -0.4, Z = 0.3

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step2-1.png)

### <a name="3-test-the-orbital-solver-using-the-in-editor-simulation"></a>3. Testare il risolutore Orbital (Orbitale) usando la simulazione nell'editor

Seleziona il pulsante Play (Riproduci) per attivare la modalità di gioco e tieni premuto il pulsante destro del mouse per ruotare la direzione dello sguardo. Potrai osservare quanto segue:

* La posizione di trasformazione di ButtonCollection è ora determinata dalle impostazioni del risolutore
* L'oggetto Cube, che non è influenzato dal risolutore, rimane nella stessa posizione

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step3-1.png)

> [!TIP]
> Se il raggio della fotocamera non è visibile nella finestra della scena, verifica che sia attivato il menu Gizmos. Per altre informazioni sul menu Gizmos e su come è possibile usarlo per ottimizzare la vista della scena, puoi fare riferimento alla documentazione relativa al <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">menu Gizmos</a> di Unity.
>
> Per visualizzare le finestre della scena e di gioco affiancate, come mostrato nell'immagine precedente, trascina semplicemente la finestra di gioco a destra della finestra della scena. Per altre informazioni sulla personalizzazione dell'area di lavoro, puoi fare riferimento alla documentazione <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Customizing Your Workspace</a> (Personalizzazione dell'area di lavoro) di Unity.

## <a name="enabling-objects-to-follow-tracked-hands"></a>Consentire agli oggetti di seguire le mani tracciate

In questa sezione verrà configurato l'oggetto Cube creato nell'esercitazione precedente in modo che segua le mani tracciate dell'utente, in particolare il polso destro. Inoltre, il risolutore verrà configurato in modo che il cubo:

* Modifichi il proprio orientamento con la rotazione della mano dell'utente
* Sia posizionato sul polso dell'utente

A tale scopo, userai il **risolutore Radial View** (Vista radiale) che mantiene l'oggetto all'interno di un cono di visione formato dall'oggetto di riferimento.

### <a name="1-add-the-radial-view-solver"></a>1. Aggiungere il risolutore Radial View (Vista radiale)

Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **Cube**, quindi nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Radial View (Script)** (Vista radiale - Script) all'oggetto Cube.

### <a name="2-configure-the-radial-view-solver"></a>2. Configurare il risolutore Radial View (Vista radiale)

Configura il componente **Solver Handler (Script)** (Gestore risolutori - Script):

* Modifica il campo **Tracked Target Type** (Tipo destinazione tracciata) impostandolo su **Hand Joint** (Articolazione mano)
* Modifica il campo **Tracked Handness** (Manualità tracciata) impostandolo su **Right** (Destra)
* Modifica il campo **Tracked Hand Joint** (Articolazione mano tracciata) impostandolo su **Wrist** (Polso)

Configura il componente **Radial View (Script)** (Vista radiale - Script):

* Modifica il campo **Reference Direction** (Direzione di riferimento) impostandolo su **Object Oriented** (Orientamento verso l'oggetto), quindi seleziona la casella di controllo **Orient To Reference Direction** (Orienta verso direzione di riferimento)
* Modifica i campi **Min Distance** (Distanza min) e **Max Distance** (Distanza max) impostandoli su 0

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step2-1.png)

### <a name="3-test-the-radial-view-solver-using-the-in-editor-simulation"></a>3. Testare il risolutore Radial View (Vista radiale) usando la simulazione nell'editor

Seleziona il pulsante Play (Riproduci) per attivare la modalità di gioco e quindi tieni premuta la barra spaziatrice per portare in alto la mano. Sposta il cursore del mouse per muovere la mano, quindi fai clic e tieni premuto il pulsante sinistro del mouse per ruotare la mano:

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step3-1.png)

## <a name="congratulations"></a>Lezione completata

In questa esercitazione hai appreso come usare i risolutori di MRTK affinché l'interfaccia utente segua l'utente in modo intuitivo. Hai anche appreso come collegare un risolutore a un oggetto (ad esempio un cubo) per seguire le mani tracciate dell'utente. Per altre informazioni su questi e altri risolutori inclusi in MRTK, puoi fare riferimento alla pagina [Risolutori](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) nel [portale dei risolutori di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

[Esercitazione successiva: 5. Interazione con oggetti 3D](mrlearning-base-ch4.md)

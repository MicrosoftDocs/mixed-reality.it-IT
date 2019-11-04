---
title: MRTK 101-come usare il Toolkit di realtà mista Unity per le interazioni di base (HoloLens 2, HoloLens, realtà mista di Windows, Open VR)
description: Come usare il Toolkit di realtà mista Unity per le interazioni di base (HoloLens 2, HoloLens, realtà mista di Windows, Open VR)
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens, MRTK, Toolkit per realtà mista, realtà mista di Windows, progettazione, app di esempio, controlli
ms.openlocfilehash: 95c81442cc390da8ac7c9a8de218341cb5e7c948
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73439652"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-basic-interactions-hololens-2-hololens-windows-mixed-reality-openvr"></a>MRTK 101: come usare il Toolkit di realtà mista Unity per le interazioni di base (HoloLens 2, HoloLens, realtà mista di Windows, Open VR)

![MRTK](images/MRTK101/MRTK101Cover.png)

Informazioni su come usare MRTK per ottenere alcuni dei modelli di interazione comuni più diffusi in realtà mista.

- Come simulare le interazioni di input nell'editor di Unity?
- Come si acquisisce e si sposta un oggetto?
- Come ridimensionare un oggetto?
- Come spostare o ruotare un oggetto con precisione
- Come fare in modo che un oggetto risponda agli eventi di input?
- Come aggiungere commenti e suggerimenti visivi?
- Come aggiungere commenti e suggerimenti audio?
- Come usare i prefabbricati di pulsanti di stile HoloLens 2?
- Come è possibile fare in modo che un oggetto venga seguito?
- Come far fronte a un oggetto?

## <a name="how-to-simulate-input-interactions-in-unityeditor"></a>Come simulare le interazioni di input nell'editor di Unity?
MRTK supporta la simulazione di input nell'editor. È sufficiente eseguire la scena facendo clic sul pulsante Play di Unity. Usare queste chiavi per simulare l'input.
Premere W, A, S, D tasti per spostare la fotocamera.
Posizionare il pulsante destro del mouse e spostare il puntatore del mouse.
Per visualizzare le mani simulate, premere la barra spaziatrice (destra) o il tasto MAIUSC sinistro (a sinistra) per tenere le mani simulate nella visualizzazione, premere T o Y per ruotare le mani simulate, premere Q o E (orizzontale)/R o F (verticale)

- [Scopri di più sulla simulazione di input nella documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)


## <a name="how-to-grab-and-move-anobject"></a>Come si acquisisce e si sposta un oggetto?
Per rendere un oggetto afferrabile, assegnare questi due script: ManipulationHandler.cs e NearInteractionGrabbable. cs (per l'acquisizione diretta con input di rilevamento a mano articolata) ManipulationHandler supporta sia le interazioni near che quelle più lontane. È possibile acquisire e spostare un oggetto con l'input di rilevamento a mano articolato di HoloLens 2 (near), il raggio di mano (lontano), il raggio del controller di movimento (lontano), il cursore HoloLens sguardo & il tocco di aria (lontano).

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-anobject"></a>Come ridimensionare un oggetto?
ManipulationHandler.cs supporta la scala e la rotazione a due passate. Questa operazione funziona con vari tipi di input, ad esempio l'input della mano articolata di HoloLens 2, l'input dello sguardo + movimento di HoloLens 1 e l'input del controller di movimento dell'auricolare ad alta realtà mista di Windows.

- [Altre informazioni sul gestore di manipolazione nella documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a>Come spostare o ruotare un oggetto con precisione
Assegnare BoundingBox.cs a un oggetto per usare il rettangolo di delimitazione che rappresenta l'interfaccia per la scala e la rotazione di un oggetto. Per impostazione predefinita, vengono visualizzati gli handle e i cavi blu stile HoloLens 1. Per usare handle animati basati sulla prossimità di HoloLens 2, è necessario assegnare prefabbricati e materiali. Per i dettagli di configurazione, fare riferimento alla documentazione del riquadro delimitatore e alla scena BoundingBoxExamples. Unity.

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">


- [Altre informazioni sul riquadro delimitatore nella documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)

## <a name="how-to-make-an-object-respond-to-inputevents"></a>Come fare in modo che un oggetto risponda agli eventi di input?
Assegnare PointerHandler.cs a un oggetto. Nel controllo, sarà possibile usare gli eventi OnPointerDown (), OnPointerUp (), OnPointerClicked (), OnPointerDragged () per usare questi eventi in uno script, implementare IMixedRealityPointerHandler.

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [Altre informazioni sul sistema di input nella documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a>Come aggiungere commenti e suggerimenti visivi?
Assegnare Interactable.cs a un oggetto. Nel controllo creare un nuovo tema. Utilizzando i profili dei temi di Interact, è possibile aggiungere facilmente commenti visivi a tutti gli Stati di interazione di input disponibili.

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Interactable.gif">


Interactable offre diversi tipi di temi, incluso il tema dello shader, che consente di controllare le proprietà dello shader per stato di interazione.

- [Altre informazioni su interactable nella documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

Un altro importante blocco predefinito per i commenti visivi è lo shader standard MRTK. Con MRTK standard shader è possibile aggiungere facilmente effetti visivi di feedback, ad esempio la luce del passaggio del mouse e la luce di prossimità. Poiché MRTK standard shader esegue un calcolo notevolmente inferiore rispetto allo shader standard Unity, è possibile creare un'esperienza di prestazioni elevate.

Creare un nuovo materiale e selezionare lo shader "Mixed Reality Toolkit > standard". In alternativa, è possibile scegliere uno dei materiali esistenti che usano MRTK standard shader.

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [Scopri di più su MRTK standard shader nella documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a>Come aggiungere commenti e suggerimenti audio?
Aggiungere AudioSource a un oggetto. Quindi, negli script che espongono gli eventi di input (ad esempio Interactable.cs o PointerHandler.cs), assegnare l'oggetto all'evento e selezionare AudioSource. PlayOneShot (). È possibile usare i clip audio oppure sceglierne uno dalle risorse audio di MRTK.

<img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-buttonprefabs"></a>Come usare i prefabbricati di pulsanti di stile HoloLens 2?
MRTK fornisce vari tipi di pulsanti di stile della shell (sistema operativo) di HoloLens 2. Fornisce feedback visivi sofisticati, come la luce di prossimità, la compressione e un effetto ondulato sull'area del pulsante.

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Button.gif">

È sufficiente trascinare uno dei prefabbricati del pulsante stampabile di HoloLens 2 nella scena. La prefabbricata USA Interactable.cs, che è stata introdotta in precedenza. È possibile usare eventi esposti, ad esempio OnClick () nelle azioni interactable to trigger.

<img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [Altre informazioni sulle prefabbricati dei pulsanti sono disponibili nella documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-followyou"></a>Come è possibile fare in modo che un oggetto venga seguito?
Assegnare uno script RadialView.cs a un oggetto. Fa parte della serie di script del Risolutore che consente di ottenere vari tipi di posizionamento degli oggetti nello spazio 3D. SolverHandler.cs verrà aggiunto automaticamente.
Di seguito è riportato un esempio di configurazione di RadialView per ottenere un comportamento di tipo ' Lazy follow '-along come il menu Start nella shell di HoloLens. È possibile specificare la distanza minima/massima e i gradi di visualizzazione minimo/massimo. Nell'esempio seguente viene illustrato il posizionamento dell'oggetto tra 0,4 m e 0,8 m nell'intervallo di 15 °. Modificare i valori di Lerp time per rendere l'aggiornamento posizionale più veloce o più lento.

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [Altre informazioni sui resolver nella documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-faceyou"></a>Come far fronte a un oggetto?
Assegnare uno script Billboard.cs a un oggetto. Che verrà sempre affrontata, indipendentemente dalla posizione. È possibile specificare l'opzione asse pivot.

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


Pronti per creare esperienze straordinarie per la realtà mista? Visita le pagine seguenti e Scopri di più su MRTK e realtà mista.

## <a name="about-the-author"></a>Informazioni sull'autore

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Dong Yoon Park</b><br>Progettazione UX @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Vedi anche

* [Toolkit di realtà mista-Unity (MRTK) GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [Portale della documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [Introduzione con MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [Linee guida per la portabilità da HoloToolkit a MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)

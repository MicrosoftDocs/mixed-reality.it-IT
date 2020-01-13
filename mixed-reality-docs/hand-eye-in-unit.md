---
title: Rilevamento mano e occhio articolato in Unity
description: Ci sono due modi principali per agire sullo sguardo in Unity, movimenti della mano e controller di movimento.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: movimenti, controller di movimento, Unity, sguardo, input
ms.openlocfilehash: fc56436cbe71f958b91fec56c5f0f7d93926b2ac
ms.sourcegitcommit: 317653cd8500563c514464f0337c1f230a6f3653
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/28/2019
ms.locfileid: "75503889"
---
# <a name="articulated-hand-and-eye-tracking-in-unity"></a>Rilevamento mano e occhio articolato in Unity

HoloLens 2 ha introdotto alcune nuove e interessanti funzionalità, ad esempio la traccia articolata e il rilevamento degli occhi.

Il modo più semplice per sfruttare la nuova funzionalità in Unity è tramite MRTK V2. Sono inoltre disponibili alcune scene di esempio utili per iniziare.

* [Inizia a usare MRTK V2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/HandTracking.html)
* [Introduzione a Eye Tracking in MRTK V2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html)

## <a name="building-blocks-supporting-hands-eyes-and-others-in-mrtk-v2"></a>Blocchi predefiniti che supportano Hands, Eyes e others in MRTK V2

MRTK v2 fornisce un set di controlli dell'interfaccia utente e blocchi predefiniti che consentono di accelerare lo sviluppo.

|  [![Pulsante](images/MRTK_Button_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) [Pulsante](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) | [![Rettangolo di delimitazione](images/MRTK_BoundingBox_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) [Rettangolo di delimitazione](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) | [gestore di manipolazione](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) del [gestore di manipolazione![](images/MRTK_Manipulation_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) |
|:--- | :--- | :--- |
| Controllo Button che supporta vari metodi di input, tra cui la mano articolata HoloLens2's | Interfaccia utente standard per la modifica di oggetti nello spazio 3D | Script per la modifica di oggetti con una o due mani |
|  [![Ardesia](images/MRTK_Slate_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html) [Ardesia](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html) | [tastiera sistema](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html) [tastiera![sistema](images/MRTK_SystemKeyboard_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html) | [![Interactable](images/InteractableExamples.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html) [Interactable](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html) |
| piano di stile 2D che supporta lo scorrimento con l'input della mano articolata | Script di esempio di uso della tastiera di sistema in Unity  | Uno script per rendere gli oggetti interagiscono con gli stati visivi e il supporto dei temi |
|  [![Risolutore](images/MRTK_Solver_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) [Risolutore](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) | [raccolta di oggetti](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) della [raccolta di oggetti![](images/MRTK_ObjectCollection_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) | [Descrizione](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html) comando [![descrizione comando](images/MRTK_Tooltip_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html) |
| Vari comportamenti di posizionamento degli oggetti, ad esempio tag-along, blocco del corpo, dimensioni della visualizzazione costante e magnetismo della superficie | Script per il layout di una matrice di oggetti in una forma tridimensionale | Interfaccia utente dell'annotazione con sistema di ancoraggio/pivot flessibile, che può essere usata per etichettare i controller di movimento e l'oggetto. |
|  [](images/MRTK_AppBar_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html) [barra dell'app](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html) della barra dell'app![ | [![Puntatori](images/MRTK_Pointer_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html) [Puntatori](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html) | [](images/MRTK_FingertipVisualization_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html) [visualizzazione a portata](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html) di mano della visualizzazione a punta di![ |
| Interfaccia utente per l'attivazione manuale del riquadro delimitatore | Informazioni sui diversi tipi di puntatori | Offerta visiva a portata di mano, che migliora la confidenza per l'interazione diretta |
|  Rilevamento degli occhi di [![: verifica della selezione della destinazione](images/mrtk_et_targetselect.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) [: selezione della destinazione](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) | [Verifica della![:](images/mrtk_et_navigation.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html) esplorazione [degli occhi:](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html) navigazione | [Verifica della![:](images/mrtk_et_heatmaps.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) verifica degli occhi della mappa termica [: mappa termica](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) |
| Combina gli occhi, l'input voce e la mano per selezionare gli ologrammi in modo rapido e semplice nella tua scena | Informazioni su come scorrere automaticamente il testo o ingrandire in modo scorrevole il contenuto con lo stato attivo in base a ciò che si sta esaminando| Esempi per la registrazione, il caricamento e la visualizzazione delle informazioni visualizzate dall'utente nell'app |

## <a name="example-scenes"></a>Scene di esempio

Esplorare i diversi tipi di interazioni e i controlli dell'interfaccia utente di MRTK in [questa scena di esempio](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandInteractionExamples.html).

È possibile trovare altre scene di esempio nel [Toolkit di realtà mista GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity) in **assets/MixedRealityToolkit. examples/Demos**cartella.

[![scena di esempio](images/MRTK_Examples.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandInteractionExamples.html)

## <a name="see-also"></a>Vedi anche

* [Interazione basata sullo sguardo] (eye-gaze-interaction.md)
* [Tracciamento oculare in HoloLens 2] (eye-tracking.md)
* [Sguardo fisso e commit](gaze-and-commit.md)
* [Mani - Manipolazione diretta](direct-manipulation.md)
* [Mani - Movimenti](gaze-and-commit.md#composite-gestures)
* [Mani - Puntamento e commit](point-and-commit.md)
* [Interazioni istintive](interaction-fundamentals.md)
* [Controller del movimento](motion-controllers.md)
* [UnityEngine. XR. WSA. input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine. XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)

---
title: Rilevamento mano e occhio articolato in Unity
description: Ci sono due modi principali per agire sullo sguardo in Unity, movimenti della mano e controller di movimento.
author: thetuvix
ms.author: yoyoz
ms.date: 03/21/2018
ms.topic: article
keywords: movimenti, controller di movimento, Unity, sguardo, input
ms.openlocfilehash: 13016879e47b3b61eb417ce9425e48ea56c1b726
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2019
ms.locfileid: "64580842"
---
# <a name="articulated-hand-and-eye-tracking-in-unity"></a>Rilevamento mano e occhio articolato in Unity

In HoloLens 2 sono state introdotte alcune nuove funzionalità interessanti: il rilevamento delle mani e degli occhi articolati.

Il modo più semplice per sfruttare la nuova funzionalità in Unity è tramite MRTK V2. Sono inoltre disponibili alcune scene di esempio utili per iniziare. 

* [Inizia a usare MRTK V2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSystem/HandTracking.html)
* [Introduzione a Eye Tracking in MRTK V2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html)


# <a name="building-blocks-supporting-hands-eyes-and-others-in-mrtk-v2"></a>Blocchi predefiniti che supportano Hands, Eyes e others in MRTK V2

MRTK v2 fornisce un set di controlli dell'interfaccia utente e blocchi predefiniti che consentono di accelerare lo sviluppo. 

|  [![Pulsante](images/MRTK_Button_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) [Pulsante](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) | [![Rettangolo di delimitazione](images/MRTK_BoundingBox_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) [Rettangolo di delimitazione](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) | [Gestore manipolazione](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) gestione manipolazione [ ![](images/MRTK_Manipulation_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) |
|:--- | :--- | :--- |
| Controllo Button che supporta vari metodi di input, tra cui la mano articolata HoloLens2's | Interfaccia utente standard per la modifica di oggetti nello spazio 3D | Script per la modifica di oggetti con una o due mani |
|  [![Ardesia](images/MRTK_Slate_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html) [Ardesia](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html) | [Tastiera sistema](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html) tastiera sistema [ ![](images/MRTK_SystemKeyboard_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html) | [![Interactable](images/InteractableExamples.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html) [Interactable](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html) |
| piano di stile 2D che supporta lo scorrimento con l'input della mano articolata | Script di esempio di uso della tastiera di sistema in Unity  | Uno script per rendere gli oggetti interagiscono con gli stati visivi e il supporto dei temi |
|  [![Risolutore](images/MRTK_Solver_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) [Risolutore](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) | [Raccolta oggetti](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) raccolta oggetti [ ![](images/MRTK_ObjectCollection_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) | [Descrizione comando](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html) descrizione comando [ ![](images/MRTK_Tooltip_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html) |
| Vari comportamenti di posizionamento degli oggetti, ad esempio tag-along, blocco del corpo, dimensioni della visualizzazione costante e magnetismo della superficie | Script per il layout di una matrice di oggetti in una forma tridimensionale | Interfaccia utente dell'annotazione con sistema di ancoraggio/pivot flessibile che può essere usata per etichettare i controller di movimento e l'oggetto. |
|  [Barra dell'app](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html) barra dell'app [ ![](images/MRTK_AppBar_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html) | [![Puntatori](images/MRTK_Pointer_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html) [Puntatori](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html) | [Visualizzazione a portata](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html) di mano visualizzazione a mano [ ![](images/MRTK_FingertipVisualization_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html) |
| Interfaccia utente per l'attivazione manuale del riquadro delimitatore | Informazioni sui diversi tipi di puntatori | Offerta visiva a portata di mano che migliora la confidenza per l'interazione diretta |
|  [![Rilevamento degli occhi: Rilevamento occhio](images/mrtk_et_targetselect.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) selezione [destinazione: Selezione destinazione](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) | [![Rilevamento degli occhi: Rilevamento](images/mrtk_et_navigation.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html) degli occhi di navigazione [: Navigazione](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html) | [![Rilevamento degli occhi: Verifica degli](images/mrtk_et_heatmaps.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) occhi della mappa [termica: Mappa termica](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) |
| Combina gli occhi, l'input voce e la mano per selezionare gli ologrammi in modo rapido e semplice nella tua scena | Informazioni su come scorrere automaticamente il testo o ingrandire in modo scorrevole il contenuto con lo stato attivo in base a ciò che si sta esaminando| Esempi per la registrazione, il caricamento e la visualizzazione delle informazioni visualizzate dall'utente nell'app |

# <a name="example-scenes"></a>Scene di esempio
Esplorare i diversi tipi di interazioni e i controlli dell'interfaccia utente di MRTK in [questa scena di esempio](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandInteractionExamples.html).

È possibile trovare altre scene di esempio nel [Toolkit di realtà mista GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity) in **assets/MixedRealityToolkit. examples/Demos**cartella.

[![Scena di esempio](images/MRTK_Examples.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandInteractionExamples.html)

## <a name="see-also"></a>Vedere anche

* [Movimenti](gestures.md)
* [Controller del movimento](motion-controllers.md)
* [UnityEngine. XR. WSA. input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine. XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)

---
title: Introduzione a MRTK versione 2
description: Per i nuovi sviluppatori interessati a sfruttare MRTK
author: Yoyoz
ms.author: Yoyoz
ms.date: 05/15/19
ms.topic: article
keywords: Realtà mista di Windows, test, Toolkit per realtà mista, MRTK versione 2, MRTK, strumenti, SDK, HoloLens, HoloLens 2
ms.openlocfilehash: c785498e1533b2117249d3b21952ff56190126c0
ms.sourcegitcommit: c4c293971bb3205a82121bbfb40d1ac52b5cb38e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/10/2019
ms.locfileid: "68937081"
---
# <a name="getting-started-with-mrtk-v2"></a>Introduzione a MRTK V2

## <a name="mrtk-getting-started-guide"></a>Guida Introduzione MRTK
Vedere la [Guida](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) introduttiva a MRTK per informazioni su come iniziare a usare MRTK V2.

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>Che cos'è il Toolkit di realtà mista (MRTK)?
MRTK è un toolkit open source straordinario, che è stato girato da quando il HoloLens è stato rilasciato per la prima volta e non può essere usato oggi senza il lavoro svolto dalla nostra community di sviluppatori che ha contribuito. Negli ultimi tre anni abbiamo ascoltato i commenti e i suggerimenti della nostra community di sviluppatori e abbiamo creato MRTK V2 per tenere conto dei principali problemi.  

MRTK V2 con Unity è un kit di sviluppo multipiattaforma open source per applicazioni di realtà miste.  MRTK versione 2 ha lo scopo di accelerare lo sviluppo di applicazioni destinate a Microsoft HoloLens, auricolari di Windows Mixed Reality immersive (VR) e piattaforma OpenVR. Il progetto mira a ridurre le barriere di accesso alla creazione di applicazioni di realtà mista offrendo inoltre un contributo alla community. 


Per altre informazioni, vedere il [portale della documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) .

## <a name="feature-areas"></a>Aree funzionali

:::row:::
    :::column:::
    <img src="images/MRTK_Icon_InputSystem.png" alt="Input system" title="Sistema di input" width="105"> Sistema di input 
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_HandTracking.png" alt="Hand Tracking (HoloLens 2)" title="Rilevamento della mano (HoloLens 2)" width="105"> Rilevamento della mano (HoloLens 2)
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_EyeTracking.png" alt="Eye Tracking (HoloLens 2)" title="Rilevamento degli occhi (HoloLens 2)" width="105">
    Rilevamento degli occhi (HoloLens 2)
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_VoiceCommand.png" alt="Voice Commanding" title="Comando vocale" width="105"> Comando vocale
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_GazeSelect.png" alt="Gaze + Select (HoloLens (1st gen))" title="Sguardo + Select (HoloLens (1a generazione))" width="105">
    Sguardo + Select (HoloLens (1a generazione))
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Teleportation.png" alt="Teleportation" title="Teletrasporto" width="105"> Teletrasporto
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
    <img src="images/MRTK_Icon_UIControls.png" alt="UI Controls" title="Controlli dell'interfaccia utente" width="105"> Controlli dell'interfaccia utente
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_Solver.png" alt="Solver and Interactions" title="Risolutore e interazioni" width="105"> Risolutore e interazioni
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_ControllerVisualization.png" alt="Controller Visualization" title="Visualizzazione del controller" width="105"> Visualizzazione del controller
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_SpatialUnderstanding.png" alt="Spatial Understanding" title="Conoscenza spaziale" width="105"> Conoscenza spaziale
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Diagnostics.png" alt="Diagnostic Tool" title="Strumento di diagnostica" width="105"> Strumento di diagnostica
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_StandardShader.png" alt="MRTK Standard Shader" title="Shader standard MRTK" width="105"> Shader standard MRTK
    :::column-end:::
:::row-end:::

## <a name="ui-and-interaction-building-blocks"></a>Interfaccia utente e blocchi predefiniti di interazione

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html"><img src="images/MRTK_Button_Main.png" alt="Button" title="Button" width="250"><br>
    **Pulsante**<br>
    Controllo Button che supporta vari metodi di input, tra cui la mano articolata di HoloLens 2<a/>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html"><img src="images/MRTK_BoundingBox_Main.png" alt="Bounding Box" title="Rettangolo di delimitazione" width="250"><br>
    **Rettangolo di delimitazione**<br>
    Interfaccia utente standard per la modifica di oggetti nello spazio 3D<a/>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html"><img src="images/MRTK_Manipulation_Main.png" alt="Manipulation Handler" title="Gestore di manipolazione" width="250"><br>
    **Gestore di manipolazione**<br>
    Script per la modifica di oggetti con una o due mani<a/>
    :::column-end:::
:::row-end:::    
    
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html"><img src="images/MRTK_Slate_Main.png" alt="Slate" title="Slate" width="250"><br>
    **Slate** <br>
    piano di stile 2D che supporta lo scorrimento con l'input della mano articolata<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html"><img src="images/MRTK_SystemKeyboard_Main.png" alt="System Keyboard" title="Tastiera di sistema" width="250"><br>
    **Tastiera di sistema**<br>
    Script di esempio di uso della tastiera di sistema in Unity<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html"><img src="images/InteractableExamples.png" alt="Interactable" title="Con cui" width="250"><br>
     **Con cui** <br>
     Uno script per rendere gli oggetti interagiscono con gli stati visivi e il supporto dei temi<a/>
    :::column-end:::
:::row-end:::       

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html"><img src="images/MRTK_Solver_Main.png" alt="Solver" title="Risolutore" width="250"><br>
    **Risolutore** <br>
    Vari comportamenti di posizionamento degli oggetti, ad esempio tag-along, blocco del corpo, dimensioni della visualizzazione costante e magnetismo della superficie<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html"><img src="images/MRTK_ObjectCollection_Main.png" alt="Object Collection" title="Raccolta di oggetti" width="250"><br>
    **Raccolta di oggetti**<br>
    Script per il layout di una matrice di oggetti in una forma tridimensionale<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html"><img src="images/MRTK_Tooltip_Main.png" alt="Tooltip" title="Descrizione comando" width="250">  <br>
    **Descrizione comando**<br>
    Interfaccia utente dell'annotazione con sistema di ancoraggio/pivot flessibile che può essere usata per etichettare i controller di movimento e l'oggetto<a/>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html"><img src="images/MRTK_AppBar_Main.png" alt="App Bar" title="Barra dell'app" width="250"><br>
    **Barra dell'app**<br>
    Interfaccia utente per l'attivazione manuale del riquadro delimitatore<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html"><img src="images/MRTK_Pointer_Main.png" alt="Pointers" title="Puntatori" width="250"><br>
    **Puntatori**<br>
    Informazioni sui diversi tipi di puntatori<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html"><img src="images/MRTK_FingertipVisualization_Main.png" alt="Fingertip Visualization" title="Visualizzazione a mano" width="250"><br>
     **Visualizzazione a mano**<br>
     Offerta visiva a portata di mano che migliora la confidenza per l'interazione diretta<a/>
    :::column-end:::
:::row-end:::   

:::row:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_Sliders.md"><img src="images/MRTK_UX_Slider_Main.jpg" alt="Slider" title="Slider" width="250"><br>
    **Dispositivo di scorrimento**<br>
    Interfaccia utente Slider per la regolazione dei valori che supportano l'interazione diretta di rilevamento<a/>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md"><img src="images/MRTK_StandardShader.jpg" alt="MRTK Standard Shader" title="Shader standard MRTK" width="250"><br>
    **Shader standard MRTK**<br>
    Lo shader standard di MRTK supporta vari elementi di progettazione fluenti con prestazioni<a/>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_HandJointChaser.md"><img src="images/MRTK_HandJointChaser_Main.jpg" alt="Hand Joint Chaser" title="Chaser giunto mano" width="250"><br>
     **Chaser giunto mano**<br>
     Viene illustrato come utilizzare il Risolutore per alleghi gli oggetti alle giunzioni di mano<a/>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html"><img src="images/mrtk_et_targetselect.png" alt="Eye Tracking: Target Selection" title="Rilevamento degli occhi: Selezione destinazione" width="250"><br>
    **Rilevamento degli occhi: Selezione destinazione**<br>
    Combina gli occhi, l'input voce e la mano per selezionare gli ologrammi in modo rapido e semplice nella tua scena<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html"><img src="images/mrtk_et_navigation.png" alt="Eye Tracking: Navigation" title="Rilevamento degli occhi: Navigazione" width="250"><br>
    **Rilevamento degli occhi: Navigazione**<br>
    Informazioni su come scorrere automaticamente il testo o ingrandire in modo scorrevole il contenuto con lo stato attivo in base a ciò che si sta esaminando<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html"><img src="images/mrtk_et_heatmaps.png" alt="Eye Tracking: Heat Map" title="Rilevamento degli occhi: Mappa termica" width="250"><br>
    **Rilevamento degli occhi: Mappa termica**<br>
    Esempi per la registrazione, il caricamento e la visualizzazione delle informazioni visualizzate dall'utente nell'app<a/>
    :::column-end:::
:::row-end:::           


## <a name="minimum-requirement-for-mrtk-v2"></a>Requisito minimo per MRTK V2
* Unity 2018.4. x
* Microsoft Visual Studio 2017 o versione successiva
* Windows SDK 18362 + 
* Windows 10 1803 o versione successiva

## <a name="new-with-mrtk-v2"></a>Novità con MRTK V2
Vogliamo sottolineare l'impegno a questi strumenti della piattaforma.  In realtà, abbiamo sfruttato MRTK versione 2 per sviluppare le nostre esperienze di posta in arrivo, ad esempio l'esperienza di installazione (OOBE) e l'applicazione di apprendimento in realtà mista.  Puoi anche aspettarti che le nuove funzionalità di HoloLens 2 siano esposte prima di tutto tramite MRTK, perché crediamo che sia il modo migliore per sviluppare sulla nostra piattaforma. 

### <a name="modular"></a>Modulare
Il progetto è stato compilato in modo modulare, quindi non è necessario eseguire ogni bit del Toolkit nel progetto.  Questa operazione è in realtà costituita da alcuni vantaggi.  Mantiene le dimensioni del progetto più ridotte, oltre a renderla più semplice da gestire.  In questo modo, poiché è stato creato con oggetti configurabili tramite script ed è basato sull'interfaccia, è anche possibile sostituire i componenti inclusi nel proprio, per supportare altri servizi, sistemi e piattaforme.


### <a name="cross-platform"></a>Multipiattaforma
Parlando di altre piattaforme, ha un supporto multipiattaforma.  Anche se questo non significa che ogni singola piattaforma è supportata in modo predefinito, è stato verificato che nessuno del codice del Toolkit si interrompe quando si passa alla destinazione di compilazione ad altre piattaforme.  L'affidabilità e l'estendibilità con la progettazione modulare consentiranno di ottenere un percorso valido per supportare più piattaforme, ad esempio ARCore, ARKit e OpenVR.


### <a name="performant"></a>Performante
Con le piattaforme mobili è stato costruito con le prestazioni.  Si tratta di un aspetto molto importante e si vuole assicurare che gli strumenti non funzionino correttamente.


## <a name="see-also"></a>Vedere anche
* [Guida introduttiva a MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [Home page della documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [Installare gli strumenti](install-the-tools.md)
* [Porting da HTK/MRTK a MRTK versione 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)

---
title: Guida introduttiva a MRTK versione 2
description: Per i nuovi sviluppatori che desiderano sfruttare MRTK
author: Yoyoz
ms.author: Yoyoz
ms.date: 05/15/19
ms.topic: article
keywords: Realtà mista di Windows, testare, Toolkit di realtà mista, MRTK versione 2, MRTK, strumenti, SDK, HoloLens, HoloLens 2
ms.openlocfilehash: 249a0ce0e608410983934b75e399d013e1ff1879
ms.sourcegitcommit: c2a5bff423feba7d29d5431c870b6017c2fe1bc2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/06/2019
ms.locfileid: "66750388"
---
# <a name="getting-started-with-mrtk-v2"></a>Guida introduttiva a MRTK v2

## <a name="mrtk-getting-started-guide"></a>Guida introduttiva di MRTK
Vedere le [Guida introduttiva a MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) per informazioni sui concetti introduttivi di MRTK V2.

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>Che cos'è Toolkit di realtà mista (MRTK)?
Il MRTK è un toolkit open source straordinari che era disponibile poiché di HoloLens fu rilasciato e non sarebbe traguardi di oggi senza occupano della nostra community di sviluppatori che hanno contribuito a esso. Negli ultimi 3 anni, abbiamo ascoltato i commenti e suggerimenti della community per sviluppatori e compilato MRTK v2 per tener conto delle principali preoccupazioni.  

La versione 2 MRTK con Unity è un kit di sviluppo multipiattaforma open source per le applicazioni di realtà mista.  Consente di accelerare lo sviluppo di applicazioni destinate a Microsoft HoloLens, auricolari (VR) coinvolgenti di realtà mista di Windows e piattaforma OpenVR MRTK versione 2. Il progetto mira a ridurre gli ostacoli alla voce per creare applicazioni di realtà mista e contribuire alla community di noi crescita. 


Vedere le [portale di documentazione MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) per altre informazioni.

## <a name="feature-areas"></a>Aree di funzionalità

:::row:::
    :::column:::
    <img src="images/MRTK_Icon_InputSystem.png" alt="Input system" title="Sistema di input" width="105"> Sistema di input 
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_HandTracking.png" alt="Hand Tracking (HoloLens 2)" title="Mano rilevamento (HoloLens 2)" width="105"> Mano rilevamento (HoloLens 2)
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_EyeTracking.png" alt="Eye Tracking (HoloLens 2)" title="Occhio rilevamento (HoloLens 2)" width="105">
    Occhio rilevamento (HoloLens 2)
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_VoiceCommand.png" alt="Voice Commanding" title="L'esecuzione di comandi vocali" width="105"> L'esecuzione di comandi vocali
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_GazeSelect.png" alt="Gaze + Select (HoloLens (1st gen))" title="Estasiati + Seleziona (HoloLens (dal 1 ° generazione))" width="105">
    Estasiati + Seleziona (HoloLens (dal 1 ° generazione))
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
    <img src="images/MRTK_Icon_ControllerVisualization.png" alt="Controller Visualization" title="Visualizzazione controller" width="105"> Visualizzazione controller
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_SpatialUnderstanding.png" alt="Spatial Understanding" title="Understanding spaziali" width="105"> Understanding spaziali
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Diagnostics.png" alt="Diagnostic Tool" title="Strumento di diagnostica" width="105"> Strumento di diagnostica
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_StandardShader.png" alt="MRTK Standard Shader" title="MRTK Shader Standard" width="105"> MRTK Shader Standard
    :::column-end:::
:::row-end:::

## <a name="ui-and-interaction-building-blocks"></a>Blocchi dell'interfaccia utente e la compilazione di interazione

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html"><img src="images/MRTK_Button_Main.png" alt="Button" title="Button" width="250"><br>
    **Pulsante**<br>
    Un controllo pulsante che supporta vari metodi di input tra mano articolati e HoloLens 2 <a/>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html"><img src="images/MRTK_BoundingBox_Main.png" alt="Bounding Box" title="Rettangolo di selezione" width="250"><br>
    **Rettangolo di selezione**<br>
    Interfaccia utente standard per la modifica di oggetti nello spazio 3D <a/>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html"><img src="images/MRTK_Manipulation_Main.png" alt="Manipulation Handler" title="Gestore di modifica" width="250"><br>
    **Gestore di modifica**<br>
    Script per la modifica di oggetti con uno o due mani <a/>
    :::column-end:::
:::row-end:::    
    
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html"><img src="images/MRTK_Slate_Main.png" alt="Slate" title="Slate" width="250"><br>
    **Slate** <br>
    Piano 2D stile di visualizzazione che supporta lo scorrimento con mano articolati e input <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html"><img src="images/MRTK_SystemKeyboard_Main.png" alt="System Keyboard" title="Tasti di sistema" width="250"><br>
    **Tasti di sistema**<br>
    Script di esempio dell'uso della tastiera di sistema in Unity <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html"><img src="images/InteractableExamples.png" alt="Interactable" title="Si" width="250"><br>
     **Si** <br>
     Uno script per la creazione di oggetti che si con gli stati di visualizzazione e il supporto dei temi <a/>
    :::column-end:::
:::row-end:::       

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html"><img src="images/MRTK_Solver_Main.png" alt="Solver" title="Risolutore" width="250"><br>
    **Solver** <br>
    Diversi comportamenti di posizionamento, ad esempio tag-along, corpo del blocco, le dimensioni di visualizzazione costante e campi magnetici superficie dell'oggetto <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html"><img src="images/MRTK_ObjectCollection_Main.png" alt="Object Collection" title="Raccolta di oggetti" width="250"><br>
    **Raccolta di oggetti**<br>
    Script per disporre una matrice di oggetti in una forma tridimensionale <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html"><img src="images/MRTK_Tooltip_Main.png" alt="Tooltip" title="Descrizione comando" width="250">  <br>
    **Descrizione comando**<br>
    Annotazione dell'interfaccia utente con il sistema di ancoraggio/pivot flessibile che può essere utilizzato per le etichette di oggetti e i controller di movimento <a/>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html"><img src="images/MRTK_AppBar_Main.png" alt="App Bar" title="App Bar" width="250"><br>
    **App Bar**<br>
    Interfaccia utente per l'attivazione manuale del rettangolo di selezione <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html"><img src="images/MRTK_Pointer_Main.png" alt="Pointers" title="Puntatori" width="250"><br>
    **Puntatori**<br>
    Informazioni sui vari tipi di puntatori <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html"><img src="images/MRTK_FingertipVisualization_Main.png" alt="Fingertip Visualization" title="Visualizzazione di punta del dito" width="250"><br>
     **Visualizzazione di punta del dito**<br>
     Intuitività Visual sulla punta del dito che migliora la sicurezza per l'interazione diretta <a/>
    :::column-end:::
:::row-end:::   

:::row:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_Sliders.md"><img src="images/MRTK_UX_Slider_Main.jpg" alt="Slider" title="Slider" width="250"><br>
    **Dispositivo di scorrimento**<br>
    Dispositivo di scorrimento dell'interfaccia utente per regolare i valori supporto mano diretta interazione di rilevamento <a/>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md"><img src="images/MRTK_StandardShader.jpg" alt="MRTK Standard Shader" title="MRTK Shader Standard" width="250"><br>
    **MRTK Shader Standard**<br>
    Shader Standard del MRTK supporta vari elementi di progettazione Fluent con prestazioni <a/>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_HandJointChaser.md"><img src="images/MRTK_HandJointChaser_Main.jpg" alt="Hand Joint Chaser" title="Tempeste congiunta di mano" width="250"><br>
     **Tempeste congiunta di mano**<br>
     Viene illustrato come utilizzare Risolutore per connettere oggetti alle giunzioni di mano <a/>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html"><img src="images/mrtk_et_targetselect.png" alt="Eye Tracking: Target Selection" title="Occhio rilevamento: Selezione della destinazione" width="250"><br>
    **Occhio rilevamento: Selezione della destinazione**<br>
    Combinare gli occhi, chiamate vocali e mano rapidamente e facilmente selezionare vntana tra la scena di input <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html"><img src="images/mrtk_et_navigation.png" alt="Eye Tracking: Navigation" title="Occhio rilevamento: Navigazione" width="250"><br>
    **Occhio rilevamento: Navigazione**<br>
    Informazioni su come automatica del testo di scorrimento zoom avanti o indietro agevolmente nel contenuto con lo stato attivo basato su ciò che si sta esaminando <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html"><img src="images/mrtk_et_heatmaps.png" alt="Eye Tracking: Heat Map" title="Occhio rilevamento: Mappa termica" width="250"><br>
    **Occhio rilevamento: Mappa termica**<br>
    Esempi per la registrazione, il caricamento e la visualizzazione degli utenti sono stati esaminando nell'app <a/>
    :::column-end:::
:::row-end:::           


## <a name="minimum-requirement-for-mrtk-v2"></a>Requisito minimo per MRTK v2
* Unity 2018.3.x
* Microsoft Visual Studio 2017 o versione successiva
* Windows SDK 18362+ 
* Windows 10 1803 o successiva

## <a name="new-with-mrtk-v2"></a>Novità di MRTK v2
Vogliamo sottolineare il nostro impegno a questi strumenti della piattaforma.  In effetti, abbiamo utilizzato MRTK versione 2 per sviluppare nostre esperienze nella posta in arrivo, ad esempio l'esperienza di installazione (OOBE) e l'applicazione di apprendimento di realtà mista.  È anche possibile prevedere visualizzare le nuove funzionalità di HoloLens 2 prima di tutto esposte tramite MRTK perché Microsoft ritiene che sia il modo migliore per sviluppare sulla piattaforma. 

### <a name="modular"></a>Modulare
È stata progettata in modo modulare, in modo che non è necessario considerare ogni bit del toolkit di progetto.  Esistono effettivamente alcuni vantaggi a questo.  Mantiene più piccole le dimensioni del progetto, nonché rende più facile da gestire.  Per di più, perché viene compilata con gli oggetti gestibili tramite script e si basa interfaccia, è anche possibile per sostituire i componenti che sono inclusi con i propri, per supportare altri servizi, i sistemi e piattaforme.


### <a name="cross-platform"></a>Multipiattaforma
Parlando di altre piattaforme, dispone del supporto multipiattaforma.  E anche se ciò non significa che ogni singola piattaforma supportata impostazione predefinita, sono stati apportati che nessuna parte del codice toolkit verrà interrotta quando si passa la destinazione di compilazione ad altre piattaforme.  L'affidabilità e l'estendibilità con il design modulare Configura è in un percorso valido per essere in grado di supportare più piattaforme, ad esempio ARCore ARKit e OpenVR.


### <a name="performant"></a>Ad alte prestazioni
Lavora con piattaforme per dispositivi mobili, è responsabile della relativa creazione nell'ottica delle prestazioni.  Questo è estremamente importante e si desidera assicurare che gli strumenti non verranno sottoposti a lavorare con è.


## <a name="see-also"></a>Vedere anche
* [Guida introduttiva di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [Documentazione di MRTK home](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [Installare gli strumenti](install-the-tools.md)
* [Porting da HTK/MRTK a MRTK versione 2](mrtk-porting-guide.md)

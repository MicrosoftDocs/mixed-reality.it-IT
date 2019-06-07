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
# <a name="getting-started-with-mrtk-v2"></a><span data-ttu-id="b2298-104">Guida introduttiva a MRTK v2</span><span class="sxs-lookup"><span data-stu-id="b2298-104">Getting started with MRTK v2</span></span>

## <a name="mrtk-getting-started-guide"></a><span data-ttu-id="b2298-105">Guida introduttiva di MRTK</span><span class="sxs-lookup"><span data-stu-id="b2298-105">MRTK Getting Started Guide</span></span>
<span data-ttu-id="b2298-106">Vedere le [Guida introduttiva a MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) per informazioni sui concetti introduttivi di MRTK V2.</span><span class="sxs-lookup"><span data-stu-id="b2298-106">See the [MRTK getting started guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) for information on getting started with MRTK V2.</span></span>

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="b2298-107">Che cos'è Toolkit di realtà mista (MRTK)?</span><span class="sxs-lookup"><span data-stu-id="b2298-107">What is Mixed Reality Toolkit (MRTK)?</span></span>
<span data-ttu-id="b2298-108">Il MRTK è un toolkit open source straordinari che era disponibile poiché di HoloLens fu rilasciato e non sarebbe traguardi di oggi senza occupano della nostra community di sviluppatori che hanno contribuito a esso.</span><span class="sxs-lookup"><span data-stu-id="b2298-108">The MRTK is an amazing open source toolkit that has been around since the HoloLens was first released, and would not be where it is today without the hard work of our developer community who have contributed to it.</span></span> <span data-ttu-id="b2298-109">Negli ultimi 3 anni, abbiamo ascoltato i commenti e suggerimenti della community per sviluppatori e compilato MRTK v2 per tener conto delle principali preoccupazioni.</span><span class="sxs-lookup"><span data-stu-id="b2298-109">Over the past 3 years, we have listened to the feedback of our developer community, and built MRTK v2 to take the biggest concerns into account.</span></span>  

<span data-ttu-id="b2298-110">La versione 2 MRTK con Unity è un kit di sviluppo multipiattaforma open source per le applicazioni di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="b2298-110">The MRTK v2 with Unity is an open source cross-platform development kit for mixed reality applications.</span></span>  <span data-ttu-id="b2298-111">Consente di accelerare lo sviluppo di applicazioni destinate a Microsoft HoloLens, auricolari (VR) coinvolgenti di realtà mista di Windows e piattaforma OpenVR MRTK versione 2.</span><span class="sxs-lookup"><span data-stu-id="b2298-111">MRTK version 2 is intended to accelerate development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets and OpenVR platform.</span></span> <span data-ttu-id="b2298-112">Il progetto mira a ridurre gli ostacoli alla voce per creare applicazioni di realtà mista e contribuire alla community di noi crescita.</span><span class="sxs-lookup"><span data-stu-id="b2298-112">The project is aimed at reducing barriers to entry to create mixed reality applications and contribute back to the community as we all grow.</span></span> 


<span data-ttu-id="b2298-113">Vedere le [portale di documentazione MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) per altre informazioni.</span><span class="sxs-lookup"><span data-stu-id="b2298-113">See the [MRTK documentation portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) to learn more.</span></span>

## <a name="feature-areas"></a><span data-ttu-id="b2298-114">Aree di funzionalità</span><span class="sxs-lookup"><span data-stu-id="b2298-114">Feature areas</span></span>

:::row:::
    :::column:::
    <img src="images/MRTK_Icon_InputSystem.png" alt="Input system" title="Sistema di input" width="105"> <span data-ttu-id="b2298-116">Sistema di input</span><span class="sxs-lookup"><span data-stu-id="b2298-116">Input System</span></span> 
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_HandTracking.png" alt="Hand Tracking (HoloLens 2)" title="Mano rilevamento (HoloLens 2)" width="105"> <span data-ttu-id="b2298-118">Mano rilevamento (HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="b2298-118">Hand Tracking (HoloLens 2)</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_EyeTracking.png" alt="Eye Tracking (HoloLens 2)" title="Occhio rilevamento (HoloLens 2)" width="105">
    <span data-ttu-id="b2298-120">Occhio rilevamento (HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="b2298-120">Eye Tracking (HoloLens 2)</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_VoiceCommand.png" alt="Voice Commanding" title="L'esecuzione di comandi vocali" width="105"> <span data-ttu-id="b2298-122">L'esecuzione di comandi vocali</span><span class="sxs-lookup"><span data-stu-id="b2298-122">Voice Commanding</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_GazeSelect.png" alt="Gaze + Select (HoloLens (1st gen))" title="Estasiati + Seleziona (HoloLens (dal 1 ° generazione))" width="105">
    <span data-ttu-id="b2298-124">Estasiati + Seleziona (HoloLens (dal 1 ° generazione))</span><span class="sxs-lookup"><span data-stu-id="b2298-124">Gaze + Select (HoloLens (1st gen))</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Teleportation.png" alt="Teleportation" title="Teletrasporto" width="105"> <span data-ttu-id="b2298-126">Teletrasporto</span><span class="sxs-lookup"><span data-stu-id="b2298-126">Teleportation</span></span>
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
    <img src="images/MRTK_Icon_UIControls.png" alt="UI Controls" title="Controlli dell'interfaccia utente" width="105"> <span data-ttu-id="b2298-128">Controlli dell'interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="b2298-128">UI Controls</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_Solver.png" alt="Solver and Interactions" title="Risolutore e interazioni" width="105"> <span data-ttu-id="b2298-130">Risolutore e interazioni</span><span class="sxs-lookup"><span data-stu-id="b2298-130">Solver and Interactions</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_ControllerVisualization.png" alt="Controller Visualization" title="Visualizzazione controller" width="105"> <span data-ttu-id="b2298-132">Visualizzazione controller</span><span class="sxs-lookup"><span data-stu-id="b2298-132">Controller Visualization</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_SpatialUnderstanding.png" alt="Spatial Understanding" title="Understanding spaziali" width="105"> <span data-ttu-id="b2298-134">Understanding spaziali</span><span class="sxs-lookup"><span data-stu-id="b2298-134">Spatial Understanding</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Diagnostics.png" alt="Diagnostic Tool" title="Strumento di diagnostica" width="105"> <span data-ttu-id="b2298-136">Strumento di diagnostica</span><span class="sxs-lookup"><span data-stu-id="b2298-136">Diagnostic Tool</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_StandardShader.png" alt="MRTK Standard Shader" title="MRTK Shader Standard" width="105"> <span data-ttu-id="b2298-138">MRTK Shader Standard</span><span class="sxs-lookup"><span data-stu-id="b2298-138">MRTK Standard Shader</span></span>
    :::column-end:::
:::row-end:::

## <a name="ui-and-interaction-building-blocks"></a><span data-ttu-id="b2298-139">Blocchi dell'interfaccia utente e la compilazione di interazione</span><span class="sxs-lookup"><span data-stu-id="b2298-139">UI and Interaction Building blocks</span></span>

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html"><img src="images/MRTK_Button_Main.png" alt="Button" title="Button" width="250"><br>
    <span data-ttu-id="b2298-141">**Pulsante**</span><span class="sxs-lookup"><span data-stu-id="b2298-141">**Button**</span></span><br>
    <span data-ttu-id="b2298-142">Un controllo pulsante che supporta vari metodi di input tra mano articolati e HoloLens 2 <a/></span><span class="sxs-lookup"><span data-stu-id="b2298-142">A button control which supports various input methods including HoloLens 2's articulated hand <a/></span></span>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html"><img src="images/MRTK_BoundingBox_Main.png" alt="Bounding Box" title="Rettangolo di selezione" width="250"><br>
    <span data-ttu-id="b2298-144">**Rettangolo di selezione**</span><span class="sxs-lookup"><span data-stu-id="b2298-144">**Bounding Box**</span></span><br>
    <span data-ttu-id="b2298-145">Interfaccia utente standard per la modifica di oggetti nello spazio 3D <a/></span><span class="sxs-lookup"><span data-stu-id="b2298-145">Standard UI for manipulating objects in 3D space <a/></span></span>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html"><img src="images/MRTK_Manipulation_Main.png" alt="Manipulation Handler" title="Gestore di modifica" width="250"><br>
    <span data-ttu-id="b2298-147">**Gestore di modifica**</span><span class="sxs-lookup"><span data-stu-id="b2298-147">**Manipulation Handler**</span></span><br>
    <span data-ttu-id="b2298-148">Script per la modifica di oggetti con uno o due mani <a/></span><span class="sxs-lookup"><span data-stu-id="b2298-148">Script for manipulating objects with one or two hands <a/></span></span>
    :::column-end:::
:::row-end:::    
    
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html"><img src="images/MRTK_Slate_Main.png" alt="Slate" title="Slate" width="250"><br>
    <span data-ttu-id="b2298-150">**Slate**</span><span class="sxs-lookup"><span data-stu-id="b2298-150">**Slate**</span></span> <br>
    <span data-ttu-id="b2298-151">Piano 2D stile di visualizzazione che supporta lo scorrimento con mano articolati e input <a/></span><span class="sxs-lookup"><span data-stu-id="b2298-151">2D style plane which supports scrolling with articulated hand input <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html"><img src="images/MRTK_SystemKeyboard_Main.png" alt="System Keyboard" title="Tasti di sistema" width="250"><br>
    <span data-ttu-id="b2298-153">**Tasti di sistema**</span><span class="sxs-lookup"><span data-stu-id="b2298-153">**System Keyboard**</span></span><br>
    <span data-ttu-id="b2298-154">Script di esempio dell'uso della tastiera di sistema in Unity <a/></span><span class="sxs-lookup"><span data-stu-id="b2298-154">Example script of using the system keyboard in Unity <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html"><img src="images/InteractableExamples.png" alt="Interactable" title="Si" width="250"><br>
     <span data-ttu-id="b2298-156">**Si**</span><span class="sxs-lookup"><span data-stu-id="b2298-156">**Interactable**</span></span> <br>
     <span data-ttu-id="b2298-157">Uno script per la creazione di oggetti che si con gli stati di visualizzazione e il supporto dei temi <a/></span><span class="sxs-lookup"><span data-stu-id="b2298-157">A script for making objects interactable with visual states and theme support <a/></span></span>
    :::column-end:::
:::row-end:::       

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html"><img src="images/MRTK_Solver_Main.png" alt="Solver" title="Risolutore" width="250"><br>
    <span data-ttu-id="b2298-159">**Solver**</span><span class="sxs-lookup"><span data-stu-id="b2298-159">**Solver**</span></span> <br>
    <span data-ttu-id="b2298-160">Diversi comportamenti di posizionamento, ad esempio tag-along, corpo del blocco, le dimensioni di visualizzazione costante e campi magnetici superficie dell'oggetto <a/></span><span class="sxs-lookup"><span data-stu-id="b2298-160">Various object positioning behaviors such as tag-along, body-lock, constant view size and surface magnetism <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html"><img src="images/MRTK_ObjectCollection_Main.png" alt="Object Collection" title="Raccolta di oggetti" width="250"><br>
    <span data-ttu-id="b2298-162">**Raccolta di oggetti**</span><span class="sxs-lookup"><span data-stu-id="b2298-162">**Object Collection**</span></span><br>
    <span data-ttu-id="b2298-163">Script per disporre una matrice di oggetti in una forma tridimensionale <a/></span><span class="sxs-lookup"><span data-stu-id="b2298-163">Script for lay out an array of objects in a three-dimensional shape <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html"><img src="images/MRTK_Tooltip_Main.png" alt="Tooltip" title="Descrizione comando" width="250">  <br>
    <span data-ttu-id="b2298-165">**Descrizione comando**</span><span class="sxs-lookup"><span data-stu-id="b2298-165">**Tooltip**</span></span><br>
    <span data-ttu-id="b2298-166">Annotazione dell'interfaccia utente con il sistema di ancoraggio/pivot flessibile che può essere utilizzato per le etichette di oggetti e i controller di movimento <a/></span><span class="sxs-lookup"><span data-stu-id="b2298-166">Annotation UI with flexible anchor/pivot system which can be used for labeling motion controllers and object <a/></span></span>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html"><img src="images/MRTK_AppBar_Main.png" alt="App Bar" title="App Bar" width="250"><br>
    <span data-ttu-id="b2298-168">**App Bar**</span><span class="sxs-lookup"><span data-stu-id="b2298-168">**App Bar**</span></span><br>
    <span data-ttu-id="b2298-169">Interfaccia utente per l'attivazione manuale del rettangolo di selezione <a/></span><span class="sxs-lookup"><span data-stu-id="b2298-169">UI for Bounding Box's manual activation <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html"><img src="images/MRTK_Pointer_Main.png" alt="Pointers" title="Puntatori" width="250"><br>
    <span data-ttu-id="b2298-171">**Puntatori**</span><span class="sxs-lookup"><span data-stu-id="b2298-171">**Pointers**</span></span><br>
    <span data-ttu-id="b2298-172">Informazioni sui vari tipi di puntatori <a/></span><span class="sxs-lookup"><span data-stu-id="b2298-172">Learn about various types of pointers <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html"><img src="images/MRTK_FingertipVisualization_Main.png" alt="Fingertip Visualization" title="Visualizzazione di punta del dito" width="250"><br>
     <span data-ttu-id="b2298-174">**Visualizzazione di punta del dito**</span><span class="sxs-lookup"><span data-stu-id="b2298-174">**Fingertip Visualization**</span></span><br>
     <span data-ttu-id="b2298-175">Intuitività Visual sulla punta del dito che migliora la sicurezza per l'interazione diretta <a/></span><span class="sxs-lookup"><span data-stu-id="b2298-175">Visual affordance on the fingertip which improves the confidence for the direct interaction <a/></span></span>
    :::column-end:::
:::row-end:::   

:::row:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_Sliders.md"><img src="images/MRTK_UX_Slider_Main.jpg" alt="Slider" title="Slider" width="250"><br>
    <span data-ttu-id="b2298-177">**Dispositivo di scorrimento**</span><span class="sxs-lookup"><span data-stu-id="b2298-177">**Slider**</span></span><br>
    <span data-ttu-id="b2298-178">Dispositivo di scorrimento dell'interfaccia utente per regolare i valori supporto mano diretta interazione di rilevamento <a/></span><span class="sxs-lookup"><span data-stu-id="b2298-178">Slider UI for adjusting values supporting direct hand tracking interaction <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md"><img src="images/MRTK_StandardShader.jpg" alt="MRTK Standard Shader" title="MRTK Shader Standard" width="250"><br>
    <span data-ttu-id="b2298-180">**MRTK Shader Standard**</span><span class="sxs-lookup"><span data-stu-id="b2298-180">**MRTK Standard Shader**</span></span><br>
    <span data-ttu-id="b2298-181">Shader Standard del MRTK supporta vari elementi di progettazione Fluent con prestazioni <a/></span><span class="sxs-lookup"><span data-stu-id="b2298-181">MRTK's Standard shader supports various Fluent design elements with performance <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_HandJointChaser.md"><img src="images/MRTK_HandJointChaser_Main.jpg" alt="Hand Joint Chaser" title="Tempeste congiunta di mano" width="250"><br>
     <span data-ttu-id="b2298-183">**Tempeste congiunta di mano**</span><span class="sxs-lookup"><span data-stu-id="b2298-183">**Hand Joint Chaser**</span></span><br>
     <span data-ttu-id="b2298-184">Viene illustrato come utilizzare Risolutore per connettere oggetti alle giunzioni di mano <a/></span><span class="sxs-lookup"><span data-stu-id="b2298-184">Demonstrates how to use Solver to attach objects to the hand joints <a/></span></span>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html"><img src="images/mrtk_et_targetselect.png" alt="Eye Tracking: Target Selection" title="Occhio rilevamento: Selezione della destinazione" width="250"><br>
    <span data-ttu-id="b2298-186">**Occhio rilevamento: Selezione della destinazione**</span><span class="sxs-lookup"><span data-stu-id="b2298-186">**Eye Tracking: Target Selection**</span></span><br>
    <span data-ttu-id="b2298-187">Combinare gli occhi, chiamate vocali e mano rapidamente e facilmente selezionare vntana tra la scena di input <a/></span><span class="sxs-lookup"><span data-stu-id="b2298-187">Combine eyes, voice and hand input to quickly and effortlessly select holograms across your scene <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html"><img src="images/mrtk_et_navigation.png" alt="Eye Tracking: Navigation" title="Occhio rilevamento: Navigazione" width="250"><br>
    <span data-ttu-id="b2298-189">**Occhio rilevamento: Navigazione**</span><span class="sxs-lookup"><span data-stu-id="b2298-189">**Eye Tracking: Navigation**</span></span><br>
    <span data-ttu-id="b2298-190">Informazioni su come automatica del testo di scorrimento zoom avanti o indietro agevolmente nel contenuto con lo stato attivo basato su ciò che si sta esaminando <a/></span><span class="sxs-lookup"><span data-stu-id="b2298-190">Learn how to auto scroll text or fluently zoom into focused content based on what you are looking at <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html"><img src="images/mrtk_et_heatmaps.png" alt="Eye Tracking: Heat Map" title="Occhio rilevamento: Mappa termica" width="250"><br>
    <span data-ttu-id="b2298-192">**Occhio rilevamento: Mappa termica**</span><span class="sxs-lookup"><span data-stu-id="b2298-192">**Eye Tracking: Heat Map**</span></span><br>
    <span data-ttu-id="b2298-193">Esempi per la registrazione, il caricamento e la visualizzazione degli utenti sono stati esaminando nell'app <a/></span><span class="sxs-lookup"><span data-stu-id="b2298-193">Examples for logging, loading and visualizing what users have been looking at in your app <a/></span></span>
    :::column-end:::
:::row-end:::           


## <a name="minimum-requirement-for-mrtk-v2"></a><span data-ttu-id="b2298-194">Requisito minimo per MRTK v2</span><span class="sxs-lookup"><span data-stu-id="b2298-194">Minimum Requirement for MRTK v2</span></span>
* <span data-ttu-id="b2298-195">Unity 2018.3.x</span><span class="sxs-lookup"><span data-stu-id="b2298-195">Unity 2018.3.x</span></span>
* <span data-ttu-id="b2298-196">Microsoft Visual Studio 2017 o versione successiva</span><span class="sxs-lookup"><span data-stu-id="b2298-196">Microsoft Visual Studio 2017 or later</span></span>
* <span data-ttu-id="b2298-197">Windows SDK 18362+</span><span class="sxs-lookup"><span data-stu-id="b2298-197">Windows SDK 18362+</span></span> 
* <span data-ttu-id="b2298-198">Windows 10 1803 o successiva</span><span class="sxs-lookup"><span data-stu-id="b2298-198">Windows 10 1803 or later</span></span>

## <a name="new-with-mrtk-v2"></a><span data-ttu-id="b2298-199">Novità di MRTK v2</span><span class="sxs-lookup"><span data-stu-id="b2298-199">New with MRTK v2</span></span>
<span data-ttu-id="b2298-200">Vogliamo sottolineare il nostro impegno a questi strumenti della piattaforma.</span><span class="sxs-lookup"><span data-stu-id="b2298-200">We want to stress our commitment to these platform tools.</span></span>  <span data-ttu-id="b2298-201">In effetti, abbiamo utilizzato MRTK versione 2 per sviluppare nostre esperienze nella posta in arrivo, ad esempio l'esperienza di installazione (OOBE) e l'applicazione di apprendimento di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="b2298-201">In fact, we leveraged MRTK version 2 to develop our inbox experiences, such as the setup experience (OOBE) and our Mixed Reality Learning application.</span></span>  <span data-ttu-id="b2298-202">È anche possibile prevedere visualizzare le nuove funzionalità di HoloLens 2 prima di tutto esposte tramite MRTK perché Microsoft ritiene che sia il modo migliore per sviluppare sulla piattaforma.</span><span class="sxs-lookup"><span data-stu-id="b2298-202">You can also expect to see new HoloLens 2 capabilities first exposed through MRTK because we believe it’s the best way to develop on our platform.</span></span> 

### <a name="modular"></a><span data-ttu-id="b2298-203">Modulare</span><span class="sxs-lookup"><span data-stu-id="b2298-203">Modular</span></span>
<span data-ttu-id="b2298-204">È stata progettata in modo modulare, in modo che non è necessario considerare ogni bit del toolkit di progetto.</span><span class="sxs-lookup"><span data-stu-id="b2298-204">We have built it in a modular way, so that you do not need to take every bit of the toolkit into your project.</span></span>  <span data-ttu-id="b2298-205">Esistono effettivamente alcuni vantaggi a questo.</span><span class="sxs-lookup"><span data-stu-id="b2298-205">There are actually a few benefits to this.</span></span>  <span data-ttu-id="b2298-206">Mantiene più piccole le dimensioni del progetto, nonché rende più facile da gestire.</span><span class="sxs-lookup"><span data-stu-id="b2298-206">It keeps your project size smaller, as well as makes it easier to manage.</span></span>  <span data-ttu-id="b2298-207">Per di più, perché viene compilata con gli oggetti gestibili tramite script e si basa interfaccia, è anche possibile per sostituire i componenti che sono inclusi con i propri, per supportare altri servizi, i sistemi e piattaforme.</span><span class="sxs-lookup"><span data-stu-id="b2298-207">On top of that, because it’s built with scriptable objects and is interface driven, it’s also possible for you to replace the components that are included with your own, to support other services, systems, and platforms.</span></span>


### <a name="cross-platform"></a><span data-ttu-id="b2298-208">Multipiattaforma</span><span class="sxs-lookup"><span data-stu-id="b2298-208">Cross-platform</span></span>
<span data-ttu-id="b2298-209">Parlando di altre piattaforme, dispone del supporto multipiattaforma.</span><span class="sxs-lookup"><span data-stu-id="b2298-209">Speaking of other platforms, it has cross-platform support.</span></span>  <span data-ttu-id="b2298-210">E anche se ciò non significa che ogni singola piattaforma supportata impostazione predefinita, sono stati apportati che nessuna parte del codice toolkit verrà interrotta quando si passa la destinazione di compilazione ad altre piattaforme.</span><span class="sxs-lookup"><span data-stu-id="b2298-210">And while this doesn’t mean every single platform is supported out of the box, we have made sure none of the toolkit code will break when you switch your build target to other platforms.</span></span>  <span data-ttu-id="b2298-211">L'affidabilità e l'estendibilità con il design modulare Configura è in un percorso valido per essere in grado di supportare più piattaforme, ad esempio ARCore ARKit e OpenVR.</span><span class="sxs-lookup"><span data-stu-id="b2298-211">The robustness and extensibility with the modular design sets you up on a good path to be able to support multiple platforms, such as ARCore, ARKit, and OpenVR.</span></span>


### <a name="performant"></a><span data-ttu-id="b2298-212">Ad alte prestazioni</span><span class="sxs-lookup"><span data-stu-id="b2298-212">Performant</span></span>
<span data-ttu-id="b2298-213">Lavora con piattaforme per dispositivi mobili, è responsabile della relativa creazione nell'ottica delle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="b2298-213">Working with mobile platforms, we constructed it with performance in mind.</span></span>  <span data-ttu-id="b2298-214">Questo è estremamente importante e si desidera assicurare che gli strumenti non verranno sottoposti a lavorare con è.</span><span class="sxs-lookup"><span data-stu-id="b2298-214">This is super important, and we wanted to ensure that the tools are not going to work against you.</span></span>


## <a name="see-also"></a><span data-ttu-id="b2298-215">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b2298-215">See also</span></span>
* [<span data-ttu-id="b2298-216">Guida introduttiva di MRTK</span><span class="sxs-lookup"><span data-stu-id="b2298-216">MRTK getting started guide</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [<span data-ttu-id="b2298-217">Documentazione di MRTK home</span><span class="sxs-lookup"><span data-stu-id="b2298-217">MRTK documentation home</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="b2298-218">Installare gli strumenti</span><span class="sxs-lookup"><span data-stu-id="b2298-218">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="b2298-219">Porting da HTK/MRTK a MRTK versione 2</span><span class="sxs-lookup"><span data-stu-id="b2298-219">Porting from HTK/MRTK to MRTK version 2</span></span>](mrtk-porting-guide.md)

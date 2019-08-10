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
# <a name="getting-started-with-mrtk-v2"></a><span data-ttu-id="3978b-104">Introduzione a MRTK V2</span><span class="sxs-lookup"><span data-stu-id="3978b-104">Getting started with MRTK v2</span></span>

## <a name="mrtk-getting-started-guide"></a><span data-ttu-id="3978b-105">Guida Introduzione MRTK</span><span class="sxs-lookup"><span data-stu-id="3978b-105">MRTK Getting Started Guide</span></span>
<span data-ttu-id="3978b-106">Vedere la [Guida](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) introduttiva a MRTK per informazioni su come iniziare a usare MRTK V2.</span><span class="sxs-lookup"><span data-stu-id="3978b-106">See the [MRTK getting started guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) for information on getting started with MRTK V2.</span></span>

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="3978b-107">Che cos'è il Toolkit di realtà mista (MRTK)?</span><span class="sxs-lookup"><span data-stu-id="3978b-107">What is Mixed Reality Toolkit (MRTK)?</span></span>
<span data-ttu-id="3978b-108">MRTK è un toolkit open source straordinario, che è stato girato da quando il HoloLens è stato rilasciato per la prima volta e non può essere usato oggi senza il lavoro svolto dalla nostra community di sviluppatori che ha contribuito.</span><span class="sxs-lookup"><span data-stu-id="3978b-108">The MRTK is an amazing open source toolkit that has been around since the HoloLens was first released, and would not be where it is today without the hard work of our developer community who have contributed to it.</span></span> <span data-ttu-id="3978b-109">Negli ultimi tre anni abbiamo ascoltato i commenti e i suggerimenti della nostra community di sviluppatori e abbiamo creato MRTK V2 per tenere conto dei principali problemi.</span><span class="sxs-lookup"><span data-stu-id="3978b-109">Over the past 3 years, we have listened to the feedback of our developer community, and built MRTK v2 to take the biggest concerns into account.</span></span>  

<span data-ttu-id="3978b-110">MRTK V2 con Unity è un kit di sviluppo multipiattaforma open source per applicazioni di realtà miste.</span><span class="sxs-lookup"><span data-stu-id="3978b-110">The MRTK v2 with Unity is an open source cross-platform development kit for mixed reality applications.</span></span>  <span data-ttu-id="3978b-111">MRTK versione 2 ha lo scopo di accelerare lo sviluppo di applicazioni destinate a Microsoft HoloLens, auricolari di Windows Mixed Reality immersive (VR) e piattaforma OpenVR.</span><span class="sxs-lookup"><span data-stu-id="3978b-111">MRTK version 2 is intended to accelerate development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets and OpenVR platform.</span></span> <span data-ttu-id="3978b-112">Il progetto mira a ridurre le barriere di accesso alla creazione di applicazioni di realtà mista offrendo inoltre un contributo alla community.</span><span class="sxs-lookup"><span data-stu-id="3978b-112">The project is aimed at reducing barriers to entry to create mixed reality applications and contribute back to the community as we all grow.</span></span> 


<span data-ttu-id="3978b-113">Per altre informazioni, vedere il [portale della documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) .</span><span class="sxs-lookup"><span data-stu-id="3978b-113">See the [MRTK documentation portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) to learn more.</span></span>

## <a name="feature-areas"></a><span data-ttu-id="3978b-114">Aree funzionali</span><span class="sxs-lookup"><span data-stu-id="3978b-114">Feature areas</span></span>

:::row:::
    :::column:::
    <img src="images/MRTK_Icon_InputSystem.png" alt="Input system" title="Sistema di input" width="105"> <span data-ttu-id="3978b-116">Sistema di input</span><span class="sxs-lookup"><span data-stu-id="3978b-116">Input System</span></span> 
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_HandTracking.png" alt="Hand Tracking (HoloLens 2)" title="Rilevamento della mano (HoloLens 2)" width="105"> <span data-ttu-id="3978b-118">Rilevamento della mano (HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="3978b-118">Hand Tracking (HoloLens 2)</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_EyeTracking.png" alt="Eye Tracking (HoloLens 2)" title="Rilevamento degli occhi (HoloLens 2)" width="105">
    <span data-ttu-id="3978b-120">Rilevamento degli occhi (HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="3978b-120">Eye Tracking (HoloLens 2)</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_VoiceCommand.png" alt="Voice Commanding" title="Comando vocale" width="105"> <span data-ttu-id="3978b-122">Comando vocale</span><span class="sxs-lookup"><span data-stu-id="3978b-122">Voice Commanding</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_GazeSelect.png" alt="Gaze + Select (HoloLens (1st gen))" title="Sguardo + Select (HoloLens (1a generazione))" width="105">
    <span data-ttu-id="3978b-124">Sguardo + Select (HoloLens (1a generazione))</span><span class="sxs-lookup"><span data-stu-id="3978b-124">Gaze + Select (HoloLens (1st gen))</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Teleportation.png" alt="Teleportation" title="Teletrasporto" width="105"> <span data-ttu-id="3978b-126">Teletrasporto</span><span class="sxs-lookup"><span data-stu-id="3978b-126">Teleportation</span></span>
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
    <img src="images/MRTK_Icon_UIControls.png" alt="UI Controls" title="Controlli dell'interfaccia utente" width="105"> <span data-ttu-id="3978b-128">Controlli dell'interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="3978b-128">UI Controls</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_Solver.png" alt="Solver and Interactions" title="Risolutore e interazioni" width="105"> <span data-ttu-id="3978b-130">Risolutore e interazioni</span><span class="sxs-lookup"><span data-stu-id="3978b-130">Solver and Interactions</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_ControllerVisualization.png" alt="Controller Visualization" title="Visualizzazione del controller" width="105"> <span data-ttu-id="3978b-132">Visualizzazione del controller</span><span class="sxs-lookup"><span data-stu-id="3978b-132">Controller Visualization</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_SpatialUnderstanding.png" alt="Spatial Understanding" title="Conoscenza spaziale" width="105"> <span data-ttu-id="3978b-134">Conoscenza spaziale</span><span class="sxs-lookup"><span data-stu-id="3978b-134">Spatial Understanding</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Diagnostics.png" alt="Diagnostic Tool" title="Strumento di diagnostica" width="105"> <span data-ttu-id="3978b-136">Strumento di diagnostica</span><span class="sxs-lookup"><span data-stu-id="3978b-136">Diagnostic Tool</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_StandardShader.png" alt="MRTK Standard Shader" title="Shader standard MRTK" width="105"> <span data-ttu-id="3978b-138">Shader standard MRTK</span><span class="sxs-lookup"><span data-stu-id="3978b-138">MRTK Standard Shader</span></span>
    :::column-end:::
:::row-end:::

## <a name="ui-and-interaction-building-blocks"></a><span data-ttu-id="3978b-139">Interfaccia utente e blocchi predefiniti di interazione</span><span class="sxs-lookup"><span data-stu-id="3978b-139">UI and Interaction Building blocks</span></span>

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html"><img src="images/MRTK_Button_Main.png" alt="Button" title="Button" width="250"><br>
    <span data-ttu-id="3978b-141">**Pulsante**</span><span class="sxs-lookup"><span data-stu-id="3978b-141">**Button**</span></span><br>
    <span data-ttu-id="3978b-142">Controllo Button che supporta vari metodi di input, tra cui la mano articolata di HoloLens 2<a/></span><span class="sxs-lookup"><span data-stu-id="3978b-142">A button control which supports various input methods including HoloLens 2's articulated hand <a/></span></span>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html"><img src="images/MRTK_BoundingBox_Main.png" alt="Bounding Box" title="Rettangolo di delimitazione" width="250"><br>
    <span data-ttu-id="3978b-144">**Rettangolo di delimitazione**</span><span class="sxs-lookup"><span data-stu-id="3978b-144">**Bounding Box**</span></span><br>
    <span data-ttu-id="3978b-145">Interfaccia utente standard per la modifica di oggetti nello spazio 3D<a/></span><span class="sxs-lookup"><span data-stu-id="3978b-145">Standard UI for manipulating objects in 3D space <a/></span></span>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html"><img src="images/MRTK_Manipulation_Main.png" alt="Manipulation Handler" title="Gestore di manipolazione" width="250"><br>
    <span data-ttu-id="3978b-147">**Gestore di manipolazione**</span><span class="sxs-lookup"><span data-stu-id="3978b-147">**Manipulation Handler**</span></span><br>
    <span data-ttu-id="3978b-148">Script per la modifica di oggetti con una o due mani<a/></span><span class="sxs-lookup"><span data-stu-id="3978b-148">Script for manipulating objects with one or two hands <a/></span></span>
    :::column-end:::
:::row-end:::    
    
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html"><img src="images/MRTK_Slate_Main.png" alt="Slate" title="Slate" width="250"><br>
    <span data-ttu-id="3978b-150">**Slate**</span><span class="sxs-lookup"><span data-stu-id="3978b-150">**Slate**</span></span> <br>
    <span data-ttu-id="3978b-151">piano di stile 2D che supporta lo scorrimento con l'input della mano articolata<a/></span><span class="sxs-lookup"><span data-stu-id="3978b-151">2D style plane which supports scrolling with articulated hand input <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html"><img src="images/MRTK_SystemKeyboard_Main.png" alt="System Keyboard" title="Tastiera di sistema" width="250"><br>
    <span data-ttu-id="3978b-153">**Tastiera di sistema**</span><span class="sxs-lookup"><span data-stu-id="3978b-153">**System Keyboard**</span></span><br>
    <span data-ttu-id="3978b-154">Script di esempio di uso della tastiera di sistema in Unity<a/></span><span class="sxs-lookup"><span data-stu-id="3978b-154">Example script of using the system keyboard in Unity <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html"><img src="images/InteractableExamples.png" alt="Interactable" title="Con cui" width="250"><br>
     <span data-ttu-id="3978b-156">**Con cui**</span><span class="sxs-lookup"><span data-stu-id="3978b-156">**Interactable**</span></span> <br>
     <span data-ttu-id="3978b-157">Uno script per rendere gli oggetti interagiscono con gli stati visivi e il supporto dei temi<a/></span><span class="sxs-lookup"><span data-stu-id="3978b-157">A script for making objects interactable with visual states and theme support <a/></span></span>
    :::column-end:::
:::row-end:::       

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html"><img src="images/MRTK_Solver_Main.png" alt="Solver" title="Risolutore" width="250"><br>
    <span data-ttu-id="3978b-159">**Risolutore**</span><span class="sxs-lookup"><span data-stu-id="3978b-159">**Solver**</span></span> <br>
    <span data-ttu-id="3978b-160">Vari comportamenti di posizionamento degli oggetti, ad esempio tag-along, blocco del corpo, dimensioni della visualizzazione costante e magnetismo della superficie<a/></span><span class="sxs-lookup"><span data-stu-id="3978b-160">Various object positioning behaviors such as tag-along, body-lock, constant view size and surface magnetism <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html"><img src="images/MRTK_ObjectCollection_Main.png" alt="Object Collection" title="Raccolta di oggetti" width="250"><br>
    <span data-ttu-id="3978b-162">**Raccolta di oggetti**</span><span class="sxs-lookup"><span data-stu-id="3978b-162">**Object Collection**</span></span><br>
    <span data-ttu-id="3978b-163">Script per il layout di una matrice di oggetti in una forma tridimensionale<a/></span><span class="sxs-lookup"><span data-stu-id="3978b-163">Script for lay out an array of objects in a three-dimensional shape <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html"><img src="images/MRTK_Tooltip_Main.png" alt="Tooltip" title="Descrizione comando" width="250">  <br>
    <span data-ttu-id="3978b-165">**Descrizione comando**</span><span class="sxs-lookup"><span data-stu-id="3978b-165">**Tooltip**</span></span><br>
    <span data-ttu-id="3978b-166">Interfaccia utente dell'annotazione con sistema di ancoraggio/pivot flessibile che può essere usata per etichettare i controller di movimento e l'oggetto<a/></span><span class="sxs-lookup"><span data-stu-id="3978b-166">Annotation UI with flexible anchor/pivot system which can be used for labeling motion controllers and object <a/></span></span>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html"><img src="images/MRTK_AppBar_Main.png" alt="App Bar" title="Barra dell'app" width="250"><br>
    <span data-ttu-id="3978b-168">**Barra dell'app**</span><span class="sxs-lookup"><span data-stu-id="3978b-168">**App Bar**</span></span><br>
    <span data-ttu-id="3978b-169">Interfaccia utente per l'attivazione manuale del riquadro delimitatore<a/></span><span class="sxs-lookup"><span data-stu-id="3978b-169">UI for Bounding Box's manual activation <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html"><img src="images/MRTK_Pointer_Main.png" alt="Pointers" title="Puntatori" width="250"><br>
    <span data-ttu-id="3978b-171">**Puntatori**</span><span class="sxs-lookup"><span data-stu-id="3978b-171">**Pointers**</span></span><br>
    <span data-ttu-id="3978b-172">Informazioni sui diversi tipi di puntatori<a/></span><span class="sxs-lookup"><span data-stu-id="3978b-172">Learn about various types of pointers <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html"><img src="images/MRTK_FingertipVisualization_Main.png" alt="Fingertip Visualization" title="Visualizzazione a mano" width="250"><br>
     <span data-ttu-id="3978b-174">**Visualizzazione a mano**</span><span class="sxs-lookup"><span data-stu-id="3978b-174">**Fingertip Visualization**</span></span><br>
     <span data-ttu-id="3978b-175">Offerta visiva a portata di mano che migliora la confidenza per l'interazione diretta<a/></span><span class="sxs-lookup"><span data-stu-id="3978b-175">Visual affordance on the fingertip which improves the confidence for the direct interaction <a/></span></span>
    :::column-end:::
:::row-end:::   

:::row:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_Sliders.md"><img src="images/MRTK_UX_Slider_Main.jpg" alt="Slider" title="Slider" width="250"><br>
    <span data-ttu-id="3978b-177">**Dispositivo di scorrimento**</span><span class="sxs-lookup"><span data-stu-id="3978b-177">**Slider**</span></span><br>
    <span data-ttu-id="3978b-178">Interfaccia utente Slider per la regolazione dei valori che supportano l'interazione diretta di rilevamento<a/></span><span class="sxs-lookup"><span data-stu-id="3978b-178">Slider UI for adjusting values supporting direct hand tracking interaction <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md"><img src="images/MRTK_StandardShader.jpg" alt="MRTK Standard Shader" title="Shader standard MRTK" width="250"><br>
    <span data-ttu-id="3978b-180">**Shader standard MRTK**</span><span class="sxs-lookup"><span data-stu-id="3978b-180">**MRTK Standard Shader**</span></span><br>
    <span data-ttu-id="3978b-181">Lo shader standard di MRTK supporta vari elementi di progettazione fluenti con prestazioni<a/></span><span class="sxs-lookup"><span data-stu-id="3978b-181">MRTK's Standard shader supports various Fluent design elements with performance <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_HandJointChaser.md"><img src="images/MRTK_HandJointChaser_Main.jpg" alt="Hand Joint Chaser" title="Chaser giunto mano" width="250"><br>
     <span data-ttu-id="3978b-183">**Chaser giunto mano**</span><span class="sxs-lookup"><span data-stu-id="3978b-183">**Hand Joint Chaser**</span></span><br>
     <span data-ttu-id="3978b-184">Viene illustrato come utilizzare il Risolutore per alleghi gli oggetti alle giunzioni di mano<a/></span><span class="sxs-lookup"><span data-stu-id="3978b-184">Demonstrates how to use Solver to attach objects to the hand joints <a/></span></span>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html"><img src="images/mrtk_et_targetselect.png" alt="Eye Tracking: Target Selection" title="Rilevamento degli occhi: Selezione destinazione" width="250"><br>
    <span data-ttu-id="3978b-186">**Rilevamento degli occhi: Selezione destinazione**</span><span class="sxs-lookup"><span data-stu-id="3978b-186">**Eye Tracking: Target Selection**</span></span><br>
    <span data-ttu-id="3978b-187">Combina gli occhi, l'input voce e la mano per selezionare gli ologrammi in modo rapido e semplice nella tua scena<a/></span><span class="sxs-lookup"><span data-stu-id="3978b-187">Combine eyes, voice and hand input to quickly and effortlessly select holograms across your scene <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html"><img src="images/mrtk_et_navigation.png" alt="Eye Tracking: Navigation" title="Rilevamento degli occhi: Navigazione" width="250"><br>
    <span data-ttu-id="3978b-189">**Rilevamento degli occhi: Navigazione**</span><span class="sxs-lookup"><span data-stu-id="3978b-189">**Eye Tracking: Navigation**</span></span><br>
    <span data-ttu-id="3978b-190">Informazioni su come scorrere automaticamente il testo o ingrandire in modo scorrevole il contenuto con lo stato attivo in base a ciò che si sta esaminando<a/></span><span class="sxs-lookup"><span data-stu-id="3978b-190">Learn how to auto scroll text or fluently zoom into focused content based on what you are looking at <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html"><img src="images/mrtk_et_heatmaps.png" alt="Eye Tracking: Heat Map" title="Rilevamento degli occhi: Mappa termica" width="250"><br>
    <span data-ttu-id="3978b-192">**Rilevamento degli occhi: Mappa termica**</span><span class="sxs-lookup"><span data-stu-id="3978b-192">**Eye Tracking: Heat Map**</span></span><br>
    <span data-ttu-id="3978b-193">Esempi per la registrazione, il caricamento e la visualizzazione delle informazioni visualizzate dall'utente nell'app<a/></span><span class="sxs-lookup"><span data-stu-id="3978b-193">Examples for logging, loading and visualizing what users have been looking at in your app <a/></span></span>
    :::column-end:::
:::row-end:::           


## <a name="minimum-requirement-for-mrtk-v2"></a><span data-ttu-id="3978b-194">Requisito minimo per MRTK V2</span><span class="sxs-lookup"><span data-stu-id="3978b-194">Minimum Requirement for MRTK v2</span></span>
* <span data-ttu-id="3978b-195">Unity 2018.4. x</span><span class="sxs-lookup"><span data-stu-id="3978b-195">Unity 2018.4.x</span></span>
* <span data-ttu-id="3978b-196">Microsoft Visual Studio 2017 o versione successiva</span><span class="sxs-lookup"><span data-stu-id="3978b-196">Microsoft Visual Studio 2017 or later</span></span>
* <span data-ttu-id="3978b-197">Windows SDK 18362 +</span><span class="sxs-lookup"><span data-stu-id="3978b-197">Windows SDK 18362+</span></span> 
* <span data-ttu-id="3978b-198">Windows 10 1803 o versione successiva</span><span class="sxs-lookup"><span data-stu-id="3978b-198">Windows 10 1803 or later</span></span>

## <a name="new-with-mrtk-v2"></a><span data-ttu-id="3978b-199">Novità con MRTK V2</span><span class="sxs-lookup"><span data-stu-id="3978b-199">New with MRTK v2</span></span>
<span data-ttu-id="3978b-200">Vogliamo sottolineare l'impegno a questi strumenti della piattaforma.</span><span class="sxs-lookup"><span data-stu-id="3978b-200">We want to stress our commitment to these platform tools.</span></span>  <span data-ttu-id="3978b-201">In realtà, abbiamo sfruttato MRTK versione 2 per sviluppare le nostre esperienze di posta in arrivo, ad esempio l'esperienza di installazione (OOBE) e l'applicazione di apprendimento in realtà mista.</span><span class="sxs-lookup"><span data-stu-id="3978b-201">In fact, we leveraged MRTK version 2 to develop our inbox experiences, such as the setup experience (OOBE) and our Mixed Reality Learning application.</span></span>  <span data-ttu-id="3978b-202">Puoi anche aspettarti che le nuove funzionalità di HoloLens 2 siano esposte prima di tutto tramite MRTK, perché crediamo che sia il modo migliore per sviluppare sulla nostra piattaforma.</span><span class="sxs-lookup"><span data-stu-id="3978b-202">You can also expect to see new HoloLens 2 capabilities first exposed through MRTK because we believe it’s the best way to develop on our platform.</span></span> 

### <a name="modular"></a><span data-ttu-id="3978b-203">Modulare</span><span class="sxs-lookup"><span data-stu-id="3978b-203">Modular</span></span>
<span data-ttu-id="3978b-204">Il progetto è stato compilato in modo modulare, quindi non è necessario eseguire ogni bit del Toolkit nel progetto.</span><span class="sxs-lookup"><span data-stu-id="3978b-204">We have built it in a modular way, so that you do not need to take every bit of the toolkit into your project.</span></span>  <span data-ttu-id="3978b-205">Questa operazione è in realtà costituita da alcuni vantaggi.</span><span class="sxs-lookup"><span data-stu-id="3978b-205">There are actually a few benefits to this.</span></span>  <span data-ttu-id="3978b-206">Mantiene le dimensioni del progetto più ridotte, oltre a renderla più semplice da gestire.</span><span class="sxs-lookup"><span data-stu-id="3978b-206">It keeps your project size smaller, as well as makes it easier to manage.</span></span>  <span data-ttu-id="3978b-207">In questo modo, poiché è stato creato con oggetti configurabili tramite script ed è basato sull'interfaccia, è anche possibile sostituire i componenti inclusi nel proprio, per supportare altri servizi, sistemi e piattaforme.</span><span class="sxs-lookup"><span data-stu-id="3978b-207">On top of that, because it’s built with scriptable objects and is interface driven, it’s also possible for you to replace the components that are included with your own, to support other services, systems, and platforms.</span></span>


### <a name="cross-platform"></a><span data-ttu-id="3978b-208">Multipiattaforma</span><span class="sxs-lookup"><span data-stu-id="3978b-208">Cross-platform</span></span>
<span data-ttu-id="3978b-209">Parlando di altre piattaforme, ha un supporto multipiattaforma.</span><span class="sxs-lookup"><span data-stu-id="3978b-209">Speaking of other platforms, it has cross-platform support.</span></span>  <span data-ttu-id="3978b-210">Anche se questo non significa che ogni singola piattaforma è supportata in modo predefinito, è stato verificato che nessuno del codice del Toolkit si interrompe quando si passa alla destinazione di compilazione ad altre piattaforme.</span><span class="sxs-lookup"><span data-stu-id="3978b-210">And while this doesn’t mean every single platform is supported out of the box, we have made sure none of the toolkit code will break when you switch your build target to other platforms.</span></span>  <span data-ttu-id="3978b-211">L'affidabilità e l'estendibilità con la progettazione modulare consentiranno di ottenere un percorso valido per supportare più piattaforme, ad esempio ARCore, ARKit e OpenVR.</span><span class="sxs-lookup"><span data-stu-id="3978b-211">The robustness and extensibility with the modular design sets you up on a good path to be able to support multiple platforms, such as ARCore, ARKit, and OpenVR.</span></span>


### <a name="performant"></a><span data-ttu-id="3978b-212">Performante</span><span class="sxs-lookup"><span data-stu-id="3978b-212">Performant</span></span>
<span data-ttu-id="3978b-213">Con le piattaforme mobili è stato costruito con le prestazioni.</span><span class="sxs-lookup"><span data-stu-id="3978b-213">Working with mobile platforms, we constructed it with performance in mind.</span></span>  <span data-ttu-id="3978b-214">Si tratta di un aspetto molto importante e si vuole assicurare che gli strumenti non funzionino correttamente.</span><span class="sxs-lookup"><span data-stu-id="3978b-214">This is super important, and we wanted to ensure that the tools are not going to work against you.</span></span>


## <a name="see-also"></a><span data-ttu-id="3978b-215">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3978b-215">See also</span></span>
* [<span data-ttu-id="3978b-216">Guida introduttiva a MRTK</span><span class="sxs-lookup"><span data-stu-id="3978b-216">MRTK getting started guide</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [<span data-ttu-id="3978b-217">Home page della documentazione di MRTK</span><span class="sxs-lookup"><span data-stu-id="3978b-217">MRTK documentation home</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="3978b-218">Installare gli strumenti</span><span class="sxs-lookup"><span data-stu-id="3978b-218">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="3978b-219">Porting da HTK/MRTK a MRTK versione 2</span><span class="sxs-lookup"><span data-stu-id="3978b-219">Porting from HTK/MRTK to MRTK version 2</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)

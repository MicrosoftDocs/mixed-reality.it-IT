---
title: MRTK 101-come usare il Toolkit di realtà mista Unity per le interazioni di base (HoloLens 2, HoloLens, realtà mista di Windows, Open VR)
description: Come usare il Toolkit di realtà mista Unity per le interazioni di base (HoloLens 2, HoloLens, realtà mista di Windows, Open VR)
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens, MRTK, Toolkit per realtà mista, realtà mista di Windows, progettazione, app di esempio, controlli
ms.openlocfilehash: ad9d2755522c2610ae051fa61f96605e49404d2d
ms.sourcegitcommit: 5054f5c23965ce56599cb29ac9d9c6e48812dabd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/03/2020
ms.locfileid: "75623502"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-basic-interactions-hololens-2-hololens-windows-mixed-reality-openvr"></a><span data-ttu-id="1c805-104">MRTK 101: come usare il Toolkit di realtà mista Unity per le interazioni di base (HoloLens 2, HoloLens, realtà mista di Windows, Open VR)</span><span class="sxs-lookup"><span data-stu-id="1c805-104">MRTK 101: How to use Mixed Reality Toolkit Unity for Basic Interactions (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)</span></span>

![MRTK](images/MRTK101/MRTK101Cover.png)

<span data-ttu-id="1c805-106">Informazioni su come usare MRTK per ottenere alcuni dei modelli di interazione comuni più diffusi in realtà mista.</span><span class="sxs-lookup"><span data-stu-id="1c805-106">Learn about how to use MRTK to achieve some of the most widely used common interaction patterns in mixed reality.</span></span>

- <span data-ttu-id="1c805-107">Come simulare le interazioni di input nell'editor di Unity?</span><span class="sxs-lookup"><span data-stu-id="1c805-107">How to simulate input interactions in Unity editor?</span></span>
- <span data-ttu-id="1c805-108">Come si acquisisce e si sposta un oggetto?</span><span class="sxs-lookup"><span data-stu-id="1c805-108">How to grab and move an object?</span></span>
- <span data-ttu-id="1c805-109">Come ridimensionare un oggetto?</span><span class="sxs-lookup"><span data-stu-id="1c805-109">How to resize an object?</span></span>
- <span data-ttu-id="1c805-110">Come spostare o ruotare un oggetto con precisione</span><span class="sxs-lookup"><span data-stu-id="1c805-110">How to move or rotate an object with precision?</span></span>
- <span data-ttu-id="1c805-111">Come fare in modo che un oggetto risponda agli eventi di input?</span><span class="sxs-lookup"><span data-stu-id="1c805-111">How to make an object respond to input events?</span></span>
- <span data-ttu-id="1c805-112">Come aggiungere commenti e suggerimenti visivi?</span><span class="sxs-lookup"><span data-stu-id="1c805-112">How to add visual feedback?</span></span>
- <span data-ttu-id="1c805-113">Come aggiungere commenti e suggerimenti audio?</span><span class="sxs-lookup"><span data-stu-id="1c805-113">How to add audio feedback?</span></span>
- <span data-ttu-id="1c805-114">Come usare i prefabbricati di pulsanti di stile HoloLens 2?</span><span class="sxs-lookup"><span data-stu-id="1c805-114">How to use HoloLens 2 style button prefabs?</span></span>
- <span data-ttu-id="1c805-115">Come è possibile fare in modo che un oggetto venga seguito?</span><span class="sxs-lookup"><span data-stu-id="1c805-115">How to make an object follow you?</span></span>
- <span data-ttu-id="1c805-116">Come far fronte a un oggetto?</span><span class="sxs-lookup"><span data-stu-id="1c805-116">How to make an object face you?</span></span>

## <a name="how-to-simulate-input-interactions-in-unityeditor"></a><span data-ttu-id="1c805-117">Come simulare le interazioni di input nell'editor di Unity?</span><span class="sxs-lookup"><span data-stu-id="1c805-117">How to simulate input interactions in Unity editor?</span></span>
<span data-ttu-id="1c805-118">MRTK supporta la simulazione di input nell'editor.</span><span class="sxs-lookup"><span data-stu-id="1c805-118">MRTK supports in-editor input simulation.</span></span> <span data-ttu-id="1c805-119">È sufficiente eseguire la scena facendo clic sul pulsante Play di Unity.</span><span class="sxs-lookup"><span data-stu-id="1c805-119">Simply run your scene by clicking Unity's play button.</span></span> <span data-ttu-id="1c805-120">Usare queste chiavi per simulare l'input.</span><span class="sxs-lookup"><span data-stu-id="1c805-120">Use these keys to simulate input.</span></span>
<span data-ttu-id="1c805-121">Premere W, A, S, D tasti per spostare la fotocamera.</span><span class="sxs-lookup"><span data-stu-id="1c805-121">Press W, A, S, D keys to move the camera.</span></span>
<span data-ttu-id="1c805-122">Posizionare il pulsante destro del mouse e spostare il puntatore del mouse.</span><span class="sxs-lookup"><span data-stu-id="1c805-122">Hold the right mouse button and move the mouse to look around.</span></span>
<span data-ttu-id="1c805-123">Per visualizzare le mani simulate, premere la barra spaziatrice (destra) o il tasto MAIUSC sinistro (a sinistra) per tenere le mani simulate nella visualizzazione, premere T o Y per ruotare le mani simulate, premere Q o E (orizzontale)/R o F (verticale)</span><span class="sxs-lookup"><span data-stu-id="1c805-123">To bring up the simulated hands, press Space bar(Right hand) or left Shift key(Left hand) To keep simulated hands in the view, press T or Y key To rotate simulated hands, press Q or E(horizontal) / R or F(vertical)</span></span>

- [<span data-ttu-id="1c805-124">Scopri di più sulla simulazione di input nella documentazione di MRTK</span><span class="sxs-lookup"><span data-stu-id="1c805-124">Learn more about Input Simulation in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)


## <a name="how-to-grab-and-move-anobject"></a><span data-ttu-id="1c805-125">Come si acquisisce e si sposta un oggetto?</span><span class="sxs-lookup"><span data-stu-id="1c805-125">How to grab and move an object?</span></span>
<span data-ttu-id="1c805-126">Per rendere un oggetto afferrabile, assegnare questi due script: ManipulationHandler.cs e NearInteractionGrabbable. cs (per l'acquisizione diretta con input di rilevamento a mano articolata) ManipulationHandler supporta sia le interazioni near che quelle più lontane.</span><span class="sxs-lookup"><span data-stu-id="1c805-126">To make an object grabbable, assign these two scripts: ManipulationHandler.cs and NearInteractionGrabbable.cs(for direct grab with articulated hand tracking input) ManipulationHandler supports both near and far interactions.</span></span> <span data-ttu-id="1c805-127">È possibile acquisire e spostare un oggetto con l'input di rilevamento a mano articolato di HoloLens 2 (near), il raggio di mano (lontano), il raggio del controller di movimento (lontano), il cursore HoloLens sguardo & il tocco di aria (lontano).</span><span class="sxs-lookup"><span data-stu-id="1c805-127">You can grab and move an object with HoloLens 2's articulated hand tracking input(near), hand ray(far), motion controller's beam(far), HoloLens gaze cursor & air-tap(far).</span></span>

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-anobject"></a><span data-ttu-id="1c805-128">Come ridimensionare un oggetto?</span><span class="sxs-lookup"><span data-stu-id="1c805-128">How to resize an object?</span></span>
<span data-ttu-id="1c805-129">ManipulationHandler.cs supporta la scala e la rotazione a due passate.</span><span class="sxs-lookup"><span data-stu-id="1c805-129">ManipulationHandler.cs supports two-handed scale/rotation.</span></span> <span data-ttu-id="1c805-130">Questa operazione funziona con vari tipi di input, ad esempio l'input della mano articolata di HoloLens 2, l'input dello sguardo + movimento di HoloLens 1 e l'input del controller di movimento dell'auricolare ad alta realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="1c805-130">This works with various input types such as HoloLens 2's articulated hand input, HoloLens 1's gaze + gesture input, and Windows Mixed Reality immersive headset's motion controller input.</span></span>

- [<span data-ttu-id="1c805-131">Altre informazioni sul gestore di manipolazione nella documentazione di MRTK</span><span class="sxs-lookup"><span data-stu-id="1c805-131">Learn more about Manipulation Handler in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a><span data-ttu-id="1c805-132">Come spostare o ruotare un oggetto con precisione</span><span class="sxs-lookup"><span data-stu-id="1c805-132">How to move or rotate an object with precision?</span></span>
<span data-ttu-id="1c805-133">Assegnare BoundingBox.cs a un oggetto per usare il rettangolo di delimitazione che rappresenta l'interfaccia per la scala e la rotazione di un oggetto.</span><span class="sxs-lookup"><span data-stu-id="1c805-133">Assign BoundingBox.cs to an object to use Bounding Box which is the interface for scaling and rotating an object.</span></span> <span data-ttu-id="1c805-134">Per impostazione predefinita, vengono visualizzati gli handle e i cavi blu stile HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="1c805-134">By default, it shows HoloLens 1 style blue handles and wires.</span></span> <span data-ttu-id="1c805-135">Per usare handle animati basati sulla prossimità di HoloLens 2, è necessario assegnare prefabbricati e materiali.</span><span class="sxs-lookup"><span data-stu-id="1c805-135">To use HoloLens 2 style proximity-based animated handles, you need to assign prefabs and materials.</span></span> <span data-ttu-id="1c805-136">Per i dettagli di configurazione, fare riferimento alla [documentazione del riquadro delimitatore](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) e alla scena BoundingBoxExamples. Unity.</span><span class="sxs-lookup"><span data-stu-id="1c805-136">Please refer to [Bounding Box documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) and the BoundingBoxExamples.unity scene for the configuration details.</span></span>

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">


- [<span data-ttu-id="1c805-137">Altre informazioni sul riquadro delimitatore nella documentazione di MRTK</span><span class="sxs-lookup"><span data-stu-id="1c805-137">Learn more about Bounding Box in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)

## <a name="how-to-make-an-object-respond-to-inputevents"></a><span data-ttu-id="1c805-138">Come fare in modo che un oggetto risponda agli eventi di input?</span><span class="sxs-lookup"><span data-stu-id="1c805-138">How to make an object respond to input events?</span></span>
<span data-ttu-id="1c805-139">Assegnare PointerHandler.cs a un oggetto.</span><span class="sxs-lookup"><span data-stu-id="1c805-139">Assign PointerHandler.cs to an object.</span></span> <span data-ttu-id="1c805-140">Nel controllo, sarà possibile usare gli eventi OnPointerDown (), OnPointerUp (), OnPointerClicked (), OnPointerDragged () per usare questi eventi in uno script, implementare IMixedRealityPointerHandler.</span><span class="sxs-lookup"><span data-stu-id="1c805-140">In the inspector, you will be able to use events OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged() To use these events in a script, implement IMixedRealityPointerHandler.</span></span>

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [<span data-ttu-id="1c805-141">Altre informazioni sul sistema di input nella documentazione di MRTK</span><span class="sxs-lookup"><span data-stu-id="1c805-141">Learn more about Input System in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a><span data-ttu-id="1c805-142">Come aggiungere commenti e suggerimenti visivi?</span><span class="sxs-lookup"><span data-stu-id="1c805-142">How to add visual feedback?</span></span>
<span data-ttu-id="1c805-143">Assegnare Interactable.cs a un oggetto.</span><span class="sxs-lookup"><span data-stu-id="1c805-143">Assign Interactable.cs to an object.</span></span> <span data-ttu-id="1c805-144">Nel controllo creare un nuovo tema.</span><span class="sxs-lookup"><span data-stu-id="1c805-144">In the inspector, create a new theme.</span></span> <span data-ttu-id="1c805-145">Utilizzando i profili dei temi di Interact, è possibile aggiungere facilmente commenti visivi a tutti gli Stati di interazione di input disponibili.</span><span class="sxs-lookup"><span data-stu-id="1c805-145">Using Interactable's theme profiles, you can easily add visual feedback to all available input interaction states.</span></span>

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Interactable.gif">


<span data-ttu-id="1c805-146">Interactable offre diversi tipi di temi, incluso il tema dello shader, che consente di controllare le proprietà dello shader per stato di interazione.</span><span class="sxs-lookup"><span data-stu-id="1c805-146">Interactable provides various types of themes including the shader theme which allows you to control properties of the shader per interaction state.</span></span>

- [<span data-ttu-id="1c805-147">Altre informazioni su interactable nella documentazione di MRTK</span><span class="sxs-lookup"><span data-stu-id="1c805-147">Learn more about Interactable in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

<span data-ttu-id="1c805-148">Un altro importante blocco predefinito per i commenti visivi è lo shader standard MRTK.</span><span class="sxs-lookup"><span data-stu-id="1c805-148">Another important building block for visual feedback is the MRTK Standard Shader.</span></span> <span data-ttu-id="1c805-149">Con MRTK standard shader è possibile aggiungere facilmente effetti visivi di feedback, ad esempio la luce del passaggio del mouse e la luce di prossimità.</span><span class="sxs-lookup"><span data-stu-id="1c805-149">With MRTK Standard Shader, you can easily add visual feedback effects such as hover light and proximity light.</span></span> <span data-ttu-id="1c805-150">Poiché MRTK standard shader esegue un calcolo notevolmente inferiore rispetto allo shader standard Unity, è possibile creare un'esperienza di prestazioni elevate.</span><span class="sxs-lookup"><span data-stu-id="1c805-150">Since MRTK Standard shader performs significantly less computation than the Unity Standard shader, you can create a performant experience.</span></span>

<span data-ttu-id="1c805-151">Creare un nuovo materiale e selezionare lo shader "Mixed Reality Toolkit > standard".</span><span class="sxs-lookup"><span data-stu-id="1c805-151">Create a new material and select the Shader 'Mixed Reality Toolkit > Standard'.</span></span> <span data-ttu-id="1c805-152">In alternativa, è possibile scegliere uno dei materiali esistenti che usano MRTK standard shader.</span><span class="sxs-lookup"><span data-stu-id="1c805-152">Or you can pick one of the existing materials that use MRTK Standard Shader.</span></span>

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [<span data-ttu-id="1c805-153">Scopri di più su MRTK standard shader nella documentazione di MRTK</span><span class="sxs-lookup"><span data-stu-id="1c805-153">Learn more about MRTK Standard Shader in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a><span data-ttu-id="1c805-154">Come aggiungere commenti e suggerimenti audio?</span><span class="sxs-lookup"><span data-stu-id="1c805-154">How to add audio feedback?</span></span>
<span data-ttu-id="1c805-155">Aggiungere AudioSource a un oggetto.</span><span class="sxs-lookup"><span data-stu-id="1c805-155">Add AudioSource to an object.</span></span> <span data-ttu-id="1c805-156">Quindi, negli script che espongono gli eventi di input (ad esempio Interactable.cs o PointerHandler.cs), assegnare l'oggetto all'evento e selezionare AudioSource. PlayOneShot ().</span><span class="sxs-lookup"><span data-stu-id="1c805-156">Then, in the scripts that exposes input events(e.g. Interactable.cs or PointerHandler.cs), assign the object to the event and select AudioSource.PlayOneShot().</span></span> <span data-ttu-id="1c805-157">È possibile usare i clip audio oppure sceglierne uno dalle risorse audio di MRTK.</span><span class="sxs-lookup"><span data-stu-id="1c805-157">You can use your audio clips or choose one from MRTK's audio assets.</span></span>

<img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-buttonprefabs"></a><span data-ttu-id="1c805-158">Come usare i prefabbricati di pulsanti di stile HoloLens 2?</span><span class="sxs-lookup"><span data-stu-id="1c805-158">How to use HoloLens 2 style button prefabs?</span></span>
<span data-ttu-id="1c805-159">MRTK fornisce vari tipi di pulsanti di stile della shell (sistema operativo) di HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1c805-159">MRTK provides various types of HoloLens 2's shell(OS) style buttons.</span></span> <span data-ttu-id="1c805-160">Fornisce feedback visivi sofisticati, come la luce di prossimità, la compressione e un effetto ondulato sull'area del pulsante.</span><span class="sxs-lookup"><span data-stu-id="1c805-160">It provides sophisticated visual feedbacks such as proximity light, compressing box, and a ripple effect on the button surface.</span></span>

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Button.gif">

<span data-ttu-id="1c805-161">È sufficiente trascinare uno dei prefabbricati del pulsante stampabile di HoloLens 2 nella scena.</span><span class="sxs-lookup"><span data-stu-id="1c805-161">Simply drag and drop one of the HoloLens 2 style pressable button prefab into your scene.</span></span> <span data-ttu-id="1c805-162">La prefabbricata USA Interactable.cs, che è stata introdotta in precedenza.</span><span class="sxs-lookup"><span data-stu-id="1c805-162">The prefab uses Interactable.cs which is introduced above.</span></span> <span data-ttu-id="1c805-163">È possibile usare eventi esposti, ad esempio OnClick () nelle azioni interactable to trigger.</span><span class="sxs-lookup"><span data-stu-id="1c805-163">You can use exposed events such as OnClick() in the Interactable to trigger actions.</span></span>

<img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [<span data-ttu-id="1c805-164">Altre informazioni sulle prefabbricati dei pulsanti sono disponibili nella documentazione di MRTK</span><span class="sxs-lookup"><span data-stu-id="1c805-164">Learn more about Button prefabs in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-followyou"></a><span data-ttu-id="1c805-165">Come è possibile fare in modo che un oggetto venga seguito?</span><span class="sxs-lookup"><span data-stu-id="1c805-165">How to make an object follow you?</span></span>
<span data-ttu-id="1c805-166">Assegnare uno script RadialView.cs a un oggetto.</span><span class="sxs-lookup"><span data-stu-id="1c805-166">Assign RadialView.cs script to an object.</span></span> <span data-ttu-id="1c805-167">Fa parte della serie di script del Risolutore che consente di ottenere vari tipi di posizionamento degli oggetti nello spazio 3D.</span><span class="sxs-lookup"><span data-stu-id="1c805-167">It is part of the Solver script series that allows you to achieve various types of object positioning in 3D space.</span></span> <span data-ttu-id="1c805-168">SolverHandler.cs verrà aggiunto automaticamente.</span><span class="sxs-lookup"><span data-stu-id="1c805-168">SolverHandler.cs will be automatically added.</span></span>
<span data-ttu-id="1c805-169">Di seguito è riportato un esempio di configurazione di RadialView per ottenere un comportamento di tipo ' Lazy follow '-along come il menu Start nella shell di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1c805-169">Below is an example of RadialView configuration to achieve 'lazy follow' tag-along behavior just like the Start menu in the HoloLens shell.</span></span> <span data-ttu-id="1c805-170">È possibile specificare la distanza minima/massima e i gradi di visualizzazione minimo/massimo.</span><span class="sxs-lookup"><span data-stu-id="1c805-170">You can specify the minimum/maximum distance and minimum/maximum view degrees.</span></span> <span data-ttu-id="1c805-171">Nell'esempio seguente viene illustrato il posizionamento dell'oggetto tra 0,4 m e 0,8 m nell'intervallo di 15 °.</span><span class="sxs-lookup"><span data-stu-id="1c805-171">The example below shows positioning the object between 0.4m and 0.8m range within 15°.</span></span> <span data-ttu-id="1c805-172">Modificare i valori di Lerp time per rendere l'aggiornamento posizionale più veloce o più lento.</span><span class="sxs-lookup"><span data-stu-id="1c805-172">Adjust Lerp Time values to make the positional update faster or slower.</span></span>

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [<span data-ttu-id="1c805-173">Altre informazioni sui resolver nella documentazione di MRTK</span><span class="sxs-lookup"><span data-stu-id="1c805-173">Learn more about Solvers in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-faceyou"></a><span data-ttu-id="1c805-174">Come far fronte a un oggetto?</span><span class="sxs-lookup"><span data-stu-id="1c805-174">How to make an object face you?</span></span>
<span data-ttu-id="1c805-175">Assegnare uno script Billboard.cs a un oggetto.</span><span class="sxs-lookup"><span data-stu-id="1c805-175">Assign Billboard.cs script to an object.</span></span> <span data-ttu-id="1c805-176">Che verrà sempre affrontata, indipendentemente dalla posizione.</span><span class="sxs-lookup"><span data-stu-id="1c805-176">It will always face you, regardless of your position.</span></span> <span data-ttu-id="1c805-177">È possibile specificare l'opzione asse pivot.</span><span class="sxs-lookup"><span data-stu-id="1c805-177">You can specify the pivot axis option.</span></span>

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


<span data-ttu-id="1c805-178">Pronti per creare esperienze straordinarie per la realtà mista?</span><span class="sxs-lookup"><span data-stu-id="1c805-178">Ready to create amazing experiences for mixed reality?</span></span> <span data-ttu-id="1c805-179">Visita le pagine seguenti e Scopri di più su MRTK e realtà mista.</span><span class="sxs-lookup"><span data-stu-id="1c805-179">Visit the pages below and learn more about MRTK and mixed reality.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="1c805-180">Informazioni sull'autore</span><span class="sxs-lookup"><span data-stu-id="1c805-180">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="1c805-181"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="1c805-181"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="1c805-182">Progettazione UX @Microsoft</span><span class="sxs-lookup"><span data-stu-id="1c805-182">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="1c805-183">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="1c805-183">See also</span></span>

* [<span data-ttu-id="1c805-184">Toolkit di realtà mista-Unity (MRTK) GitHub</span><span class="sxs-lookup"><span data-stu-id="1c805-184">Mixed Reality Toolkit-Unity (MRTK) GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="1c805-185">Portale della documentazione di MRTK</span><span class="sxs-lookup"><span data-stu-id="1c805-185">MRTK Documentation Portal</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="1c805-186">Introduzione con MRTK</span><span class="sxs-lookup"><span data-stu-id="1c805-186">Getting Started with MRTK</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [<span data-ttu-id="1c805-187">Linee guida per la portabilità da HoloToolkit a MRTK</span><span class="sxs-lookup"><span data-stu-id="1c805-187">HoloToolkit to MRTK Porting Guideline</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)

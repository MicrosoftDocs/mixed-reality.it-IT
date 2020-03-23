---
title: MRTK 101 - Come usare Mixed Reality Toolkit Unity per le interazioni di base (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)
description: Come usare Mixed Reality Toolkit Unity per le interazioni di base (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens, MRTK, Mixed Reality Toolkit, Windows Mixed Reality, progettazione, app di esempio, controlli
ms.localizationpriority: high
ms.openlocfilehash: 4564e7a0c6a717452effacae2587461fe283cf0b
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/10/2020
ms.locfileid: "79028315"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-basic-interactions-hololens-2-hololens-windows-mixed-reality-openvr"></a><span data-ttu-id="5a7b7-104">MRTK 101: Come usare Mixed Reality Toolkit Unity per le interazioni di base (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)</span><span class="sxs-lookup"><span data-stu-id="5a7b7-104">MRTK 101: How to use Mixed Reality Toolkit Unity for Basic Interactions (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)</span></span>

![MRTK](images/MRTK101/MRTK101Cover.png)

<span data-ttu-id="5a7b7-106">Informazioni su come usare MRTK per ottenere alcuni dei comuni modelli di interazione più diffusi per la realtà mista.</span><span class="sxs-lookup"><span data-stu-id="5a7b7-106">Learn about how to use MRTK to achieve some of the most widely used common interaction patterns in mixed reality.</span></span>

- <span data-ttu-id="5a7b7-107">Come simulare le interazioni di input nell'editor di Unity?</span><span class="sxs-lookup"><span data-stu-id="5a7b7-107">How to simulate input interactions in Unity editor?</span></span>
- <span data-ttu-id="5a7b7-108">Come afferrare e spostare un oggetto?</span><span class="sxs-lookup"><span data-stu-id="5a7b7-108">How to grab and move an object?</span></span>
- <span data-ttu-id="5a7b7-109">Come ridimensionare un oggetto?</span><span class="sxs-lookup"><span data-stu-id="5a7b7-109">How to resize an object?</span></span>
- <span data-ttu-id="5a7b7-110">Come spostare o ruotare un oggetto con precisione?</span><span class="sxs-lookup"><span data-stu-id="5a7b7-110">How to move or rotate an object with precision?</span></span>
- <span data-ttu-id="5a7b7-111">Come fare in modo che un oggetto risponda agli eventi di input?</span><span class="sxs-lookup"><span data-stu-id="5a7b7-111">How to make an object respond to input events?</span></span>
- <span data-ttu-id="5a7b7-112">Come aggiungere feedback visivo?</span><span class="sxs-lookup"><span data-stu-id="5a7b7-112">How to add visual feedback?</span></span>
- <span data-ttu-id="5a7b7-113">Come aggiungere feedback audio?</span><span class="sxs-lookup"><span data-stu-id="5a7b7-113">How to add audio feedback?</span></span>
- <span data-ttu-id="5a7b7-114">Come usare i prefab dei pulsanti nello stile di HoloLens 2?</span><span class="sxs-lookup"><span data-stu-id="5a7b7-114">How to use HoloLens 2 style button prefabs?</span></span>
- <span data-ttu-id="5a7b7-115">Come fare in modo che un oggetto ti segua?</span><span class="sxs-lookup"><span data-stu-id="5a7b7-115">How to make an object follow you?</span></span>
- <span data-ttu-id="5a7b7-116">Come fare in modo che un oggetto rimanga rivolto verso di te?</span><span class="sxs-lookup"><span data-stu-id="5a7b7-116">How to make an object face you?</span></span>

## <a name="how-to-simulate-input-interactions-in-unityeditor"></a><span data-ttu-id="5a7b7-117">Come simulare le interazioni di input nell'editor di Unity?</span><span class="sxs-lookup"><span data-stu-id="5a7b7-117">How to simulate input interactions in Unity editor?</span></span>
<span data-ttu-id="5a7b7-118">MRTK supporta la simulazione di input nell'editor.</span><span class="sxs-lookup"><span data-stu-id="5a7b7-118">MRTK supports in-editor input simulation.</span></span> <span data-ttu-id="5a7b7-119">È sufficiente eseguire la scena facendo clic sul pulsante di Unity per la riproduzione.</span><span class="sxs-lookup"><span data-stu-id="5a7b7-119">Simply run your scene by clicking Unity's play button.</span></span> <span data-ttu-id="5a7b7-120">Per simulare l'input, usa i tasti seguenti.</span><span class="sxs-lookup"><span data-stu-id="5a7b7-120">Use these keys to simulate input.</span></span>
<span data-ttu-id="5a7b7-121">Premi W, A, S, D per spostare la fotocamera.</span><span class="sxs-lookup"><span data-stu-id="5a7b7-121">Press W, A, S, D keys to move the camera.</span></span>
<span data-ttu-id="5a7b7-122">Tieni premuto il pulsante destro del mouse e sposta il puntatore del mouse per guardarti attorno.</span><span class="sxs-lookup"><span data-stu-id="5a7b7-122">Hold the right mouse button and move the mouse to look around.</span></span>
<span data-ttu-id="5a7b7-123">Per far comparire le mani simulate, premi la barra spaziatrice (mano destra) o il tasto MAIUSC sinistro (mano sinistra). Per mantenere le mani simulate nella visualizzazione, premi T o Y. Per ruotare le mani simulate, premi Q o E (orizzontale)/R o F (verticale).</span><span class="sxs-lookup"><span data-stu-id="5a7b7-123">To bring up the simulated hands, press Space bar(Right hand) or left Shift key(Left hand) To keep simulated hands in the view, press T or Y key To rotate simulated hands, press Q or E(horizontal) / R or F(vertical)</span></span>

- [<span data-ttu-id="5a7b7-124">Altre informazioni sulla simulazione di input nella documentazione di MRTK</span><span class="sxs-lookup"><span data-stu-id="5a7b7-124">Learn more about Input Simulation in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)


## <a name="how-to-grab-and-move-anobject"></a><span data-ttu-id="5a7b7-125">Come afferrare e spostare un oggetto?</span><span class="sxs-lookup"><span data-stu-id="5a7b7-125">How to grab and move an object?</span></span>
<span data-ttu-id="5a7b7-126">Per rendere afferrabile un oggetto, assegna questi due script: ManipulationHandler.cs e NearInteractionGrabbable.cs (per afferrare l'oggetto direttamente con input di tracciamento della mano articolata). ManipulationHandler supporta sia le interazioni da vicino sia quelle da lontano.</span><span class="sxs-lookup"><span data-stu-id="5a7b7-126">To make an object grabbable, assign these two scripts: ManipulationHandler.cs and NearInteractionGrabbable.cs(for direct grab with articulated hand tracking input) ManipulationHandler supports both near and far interactions.</span></span> <span data-ttu-id="5a7b7-127">Puoi afferrare e spostare un oggetto con l'input di tracciamento della mano articolata di HoloLens 2 (da vicino), il raggio della mano (da lontano), il raggio del controller del movimento (da lontano), il cursore dello sguardo e la simulazione del tocco di HoloLens (da lontano).</span><span class="sxs-lookup"><span data-stu-id="5a7b7-127">You can grab and move an object with HoloLens 2's articulated hand tracking input(near), hand ray(far), motion controller's beam(far), HoloLens gaze cursor & air-tap(far).</span></span>

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-anobject"></a><span data-ttu-id="5a7b7-128">Come ridimensionare un oggetto?</span><span class="sxs-lookup"><span data-stu-id="5a7b7-128">How to resize an object?</span></span>
<span data-ttu-id="5a7b7-129">ManipulationHandler.cs supporta il ridimensionamento e la rotazione a due mani.</span><span class="sxs-lookup"><span data-stu-id="5a7b7-129">ManipulationHandler.cs supports two-handed scale/rotation.</span></span> <span data-ttu-id="5a7b7-130">Questa operazione funziona con vari tipi di input, ad esempio l'input della mano articolata di HoloLens 2, l'input dello sguardo e del movimento di HoloLens 1 e l'input del controller del movimento del visore VR immersive di Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="5a7b7-130">This works with various input types such as HoloLens 2's articulated hand input, HoloLens 1's gaze + gesture input, and Windows Mixed Reality immersive headset's motion controller input.</span></span>

- [<span data-ttu-id="5a7b7-131">Altre informazioni sul gestore di manipolazione nella documentazione di MRTK</span><span class="sxs-lookup"><span data-stu-id="5a7b7-131">Learn more about Manipulation Handler in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a><span data-ttu-id="5a7b7-132">Come spostare o ruotare un oggetto con precisione?</span><span class="sxs-lookup"><span data-stu-id="5a7b7-132">How to move or rotate an object with precision?</span></span>
<span data-ttu-id="5a7b7-133">Assegna BoundingBox.cs a un oggetto in modo da usare il cubo di delimitazione, che costituisce l'interfaccia per il ridimensionamento e la rotazione di un oggetto.</span><span class="sxs-lookup"><span data-stu-id="5a7b7-133">Assign BoundingBox.cs to an object to use Bounding Box which is the interface for scaling and rotating an object.</span></span> <span data-ttu-id="5a7b7-134">Per impostazione predefinita, vengono visualizzati i quadratini e le linee blu nello stile di HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="5a7b7-134">By default, it shows HoloLens 1 style blue handles and wires.</span></span> <span data-ttu-id="5a7b7-135">Per usare i quadratini animati basati su prossimità nello stile di HoloLens 2, devi assegnare prefab e materiali.</span><span class="sxs-lookup"><span data-stu-id="5a7b7-135">To use HoloLens 2 style proximity-based animated handles, you need to assign prefabs and materials.</span></span> <span data-ttu-id="5a7b7-136">Per i dettagli di configurazione, fai riferimento alla [documentazione relativa al cubo di delimitazione](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) e alla scena BoundingBoxExamples.unity.</span><span class="sxs-lookup"><span data-stu-id="5a7b7-136">Please refer to [Bounding Box documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) and the BoundingBoxExamples.unity scene for the configuration details.</span></span>

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">


- [<span data-ttu-id="5a7b7-137">Altre informazioni sul cubo di delimitazione nella documentazione di MRTK</span><span class="sxs-lookup"><span data-stu-id="5a7b7-137">Learn more about Bounding Box in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)

## <a name="how-to-make-an-object-respond-to-inputevents"></a><span data-ttu-id="5a7b7-138">Come fare in modo che un oggetto risponda agli eventi di input?</span><span class="sxs-lookup"><span data-stu-id="5a7b7-138">How to make an object respond to input events?</span></span>
<span data-ttu-id="5a7b7-139">Assegna PointerHandler.cs a un oggetto.</span><span class="sxs-lookup"><span data-stu-id="5a7b7-139">Assign PointerHandler.cs to an object.</span></span> <span data-ttu-id="5a7b7-140">Nella finestra Inspector (Controllo) sarà possibile usare gli eventi OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged(). Per usare questi eventi in uno script, implementa IMixedRealityPointerHandler.</span><span class="sxs-lookup"><span data-stu-id="5a7b7-140">In the inspector, you will be able to use events OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged() To use these events in a script, implement IMixedRealityPointerHandler.</span></span>

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [<span data-ttu-id="5a7b7-141">Altre informazioni sul sistema di input nella documentazione di MRTK</span><span class="sxs-lookup"><span data-stu-id="5a7b7-141">Learn more about Input System in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a><span data-ttu-id="5a7b7-142">Come aggiungere feedback visivo?</span><span class="sxs-lookup"><span data-stu-id="5a7b7-142">How to add visual feedback?</span></span>
<span data-ttu-id="5a7b7-143">Assegna Interactable.cs a un oggetto.</span><span class="sxs-lookup"><span data-stu-id="5a7b7-143">Assign Interactable.cs to an object.</span></span> <span data-ttu-id="5a7b7-144">Nella finestra Inspector (Controllo) crea un nuovo tema.</span><span class="sxs-lookup"><span data-stu-id="5a7b7-144">In the inspector, create a new theme.</span></span> <span data-ttu-id="5a7b7-145">Utilizzando i profili dei temi di Interact, puoi aggiungere facilmente feedback visivo a tutti gli stati di interazione di input disponibili.</span><span class="sxs-lookup"><span data-stu-id="5a7b7-145">Using Interactable's theme profiles, you can easily add visual feedback to all available input interaction states.</span></span>

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Interactable.gif">


<span data-ttu-id="5a7b7-146">Interactable offre diversi tipi di temi, incluso il tema dello shader, che consente di controllare le proprietà dello shader in base allo stato di interazione.</span><span class="sxs-lookup"><span data-stu-id="5a7b7-146">Interactable provides various types of themes including the shader theme which allows you to control properties of the shader per interaction state.</span></span>

- [<span data-ttu-id="5a7b7-147">Altre informazioni su Interactable nella documentazione di MRTK</span><span class="sxs-lookup"><span data-stu-id="5a7b7-147">Learn more about Interactable in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

<span data-ttu-id="5a7b7-148">Un altro componente importante per il feedback visivo è lo shader MRTK Standard.</span><span class="sxs-lookup"><span data-stu-id="5a7b7-148">Another important building block for visual feedback is the MRTK Standard Shader.</span></span> <span data-ttu-id="5a7b7-149">Con questo shader puoi aggiungere facilmente effetti di feedback visivo, ad esempio una luce in movimento e una luce di prossimità.</span><span class="sxs-lookup"><span data-stu-id="5a7b7-149">With MRTK Standard Shader, you can easily add visual feedback effects such as hover light and proximity light.</span></span> <span data-ttu-id="5a7b7-150">Poiché lo shader MRTK Standard esegue molti meno calcoli rispetto allo shader Unity Standard, puoi creare un'esperienza con ottime prestazioni.</span><span class="sxs-lookup"><span data-stu-id="5a7b7-150">Since MRTK Standard shader performs significantly less computation than the Unity Standard shader, you can create a performant experience.</span></span>

<span data-ttu-id="5a7b7-151">Crea un nuovo materiale e seleziona lo shader "Mixed Reality Toolkit > Standard".</span><span class="sxs-lookup"><span data-stu-id="5a7b7-151">Create a new material and select the Shader 'Mixed Reality Toolkit > Standard'.</span></span> <span data-ttu-id="5a7b7-152">Puoi selezionare uno dei materiali esistenti che usano lo shader MRTK Standard.</span><span class="sxs-lookup"><span data-stu-id="5a7b7-152">Or you can pick one of the existing materials that use MRTK Standard Shader.</span></span>

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [<span data-ttu-id="5a7b7-153">Altre informazioni sullo shader MRTK Standard nella documentazione di MRTK</span><span class="sxs-lookup"><span data-stu-id="5a7b7-153">Learn more about MRTK Standard Shader in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a><span data-ttu-id="5a7b7-154">Come aggiungere feedback audio?</span><span class="sxs-lookup"><span data-stu-id="5a7b7-154">How to add audio feedback?</span></span>
<span data-ttu-id="5a7b7-155">Aggiungi AudioSource a un oggetto.</span><span class="sxs-lookup"><span data-stu-id="5a7b7-155">Add AudioSource to an object.</span></span> <span data-ttu-id="5a7b7-156">Successivamente, negli script che espongono eventi di input, ad esempio Interactable.cs o PointerHandler.cs, assegna l'oggetto all'evento e seleziona AudioSource.PlayOneShot().</span><span class="sxs-lookup"><span data-stu-id="5a7b7-156">Then, in the scripts that exposes input events(e.g. Interactable.cs or PointerHandler.cs), assign the object to the event and select AudioSource.PlayOneShot().</span></span> <span data-ttu-id="5a7b7-157">Puoi usare i clip audio oppure sceglierne uno dalle risorse audio di MRTK.</span><span class="sxs-lookup"><span data-stu-id="5a7b7-157">You can use your audio clips or choose one from MRTK's audio assets.</span></span>

<img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-buttonprefabs"></a><span data-ttu-id="5a7b7-158">Come usare i prefab dei pulsanti nello stile di HoloLens 2?</span><span class="sxs-lookup"><span data-stu-id="5a7b7-158">How to use HoloLens 2 style button prefabs?</span></span>
<span data-ttu-id="5a7b7-159">MRTK offre vari tipi di pulsanti nello stile della shell (sistema operativo) di HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5a7b7-159">MRTK provides various types of HoloLens 2's shell(OS) style buttons.</span></span> <span data-ttu-id="5a7b7-160">Sono disponibili feedback visivi sofisticati, come una luce di prossimità, un effetto di compressione e un effetto ondulato sulla superficie del pulsante.</span><span class="sxs-lookup"><span data-stu-id="5a7b7-160">It provides sophisticated visual feedbacks such as proximity light, compressing box, and a ripple effect on the button surface.</span></span>

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Button.gif">

<span data-ttu-id="5a7b7-161">Devi semplicemente selezionare e trascinare nella scena uno dei prefab dei pulsanti a pressione nello stile di HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5a7b7-161">Simply drag and drop one of the HoloLens 2 style pressable button prefab into your scene.</span></span> <span data-ttu-id="5a7b7-162">Il prefab usa lo script Interactable.cs, che è stato introdotto in precedenza.</span><span class="sxs-lookup"><span data-stu-id="5a7b7-162">The prefab uses Interactable.cs which is introduced above.</span></span> <span data-ttu-id="5a7b7-163">Puoi usare gli eventi esposti, ad esempio OnClick(), in Interactable per attivare le azioni.</span><span class="sxs-lookup"><span data-stu-id="5a7b7-163">You can use exposed events such as OnClick() in the Interactable to trigger actions.</span></span>

<img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [<span data-ttu-id="5a7b7-164">Altre informazioni sui prefab dei pulsanti nella documentazione di MRTK</span><span class="sxs-lookup"><span data-stu-id="5a7b7-164">Learn more about Button prefabs in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-followyou"></a><span data-ttu-id="5a7b7-165">Come fare in modo che un oggetto ti segua?</span><span class="sxs-lookup"><span data-stu-id="5a7b7-165">How to make an object follow you?</span></span>
<span data-ttu-id="5a7b7-166">Assegna lo script RadialView.cs all'oggetto.</span><span class="sxs-lookup"><span data-stu-id="5a7b7-166">Assign RadialView.cs script to an object.</span></span> <span data-ttu-id="5a7b7-167">Fa parte della serie di script Solver che consente di ottenere vari tipi di posizionamento degli oggetti nello spazio 3D.</span><span class="sxs-lookup"><span data-stu-id="5a7b7-167">It is part of the Solver script series that allows you to achieve various types of object positioning in 3D space.</span></span> <span data-ttu-id="5a7b7-168">SolverHandler.cs verrà aggiunto automaticamente.</span><span class="sxs-lookup"><span data-stu-id="5a7b7-168">SolverHandler.cs will be automatically added.</span></span>
<span data-ttu-id="5a7b7-169">Di seguito è riportato un esempio di configurazione di RadialView per ottenere un comportamento di tipo "inseguimento lento graduale" proprio come con il menu di avvio della shell di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5a7b7-169">Below is an example of RadialView configuration to achieve 'lazy follow' tag-along behavior just like the Start menu in the HoloLens shell.</span></span> <span data-ttu-id="5a7b7-170">Puoi specificare la distanza minima/massima e i gradi di visualizzazione minimi/massimi.</span><span class="sxs-lookup"><span data-stu-id="5a7b7-170">You can specify the minimum/maximum distance and minimum/maximum view degrees.</span></span> <span data-ttu-id="5a7b7-171">L'esempio seguente mostra il posizionamento dell'oggetto in un intervallo compreso tra 0,4 e 0,8 m entro 15 gradi.</span><span class="sxs-lookup"><span data-stu-id="5a7b7-171">The example below shows positioning the object between 0.4m and 0.8m range within 15°.</span></span> <span data-ttu-id="5a7b7-172">Modifica i valori relativi al tempo di salto per rendere più veloce o più lento l'aggiornamento della posizione.</span><span class="sxs-lookup"><span data-stu-id="5a7b7-172">Adjust Lerp Time values to make the positional update faster or slower.</span></span>

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [<span data-ttu-id="5a7b7-173">Altre informazioni sui Solver nella documentazione di MRTK</span><span class="sxs-lookup"><span data-stu-id="5a7b7-173">Learn more about Solvers in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-faceyou"></a><span data-ttu-id="5a7b7-174">Come fare in modo che un oggetto rimanga rivolto verso di te?</span><span class="sxs-lookup"><span data-stu-id="5a7b7-174">How to make an object face you?</span></span>
<span data-ttu-id="5a7b7-175">Assegna lo script Billboard.cs all'oggetto.</span><span class="sxs-lookup"><span data-stu-id="5a7b7-175">Assign Billboard.cs script to an object.</span></span> <span data-ttu-id="5a7b7-176">In questo modo sarà sempre rivolto verso di te, indipendentemente dalla posizione.</span><span class="sxs-lookup"><span data-stu-id="5a7b7-176">It will always face you, regardless of your position.</span></span> <span data-ttu-id="5a7b7-177">Puoi specificare l'opzione dell'asse pivot.</span><span class="sxs-lookup"><span data-stu-id="5a7b7-177">You can specify the pivot axis option.</span></span>

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


<span data-ttu-id="5a7b7-178">Sei pronto a creare esperienze straordinarie per la realtà mista?</span><span class="sxs-lookup"><span data-stu-id="5a7b7-178">Ready to create amazing experiences for mixed reality?</span></span> <span data-ttu-id="5a7b7-179">Visita le pagine seguenti e scopri di più su MRTK e sulla realtà mista.</span><span class="sxs-lookup"><span data-stu-id="5a7b7-179">Visit the pages below and learn more about MRTK and mixed reality.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="5a7b7-180">Informazioni sull'autore</span><span class="sxs-lookup"><span data-stu-id="5a7b7-180">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="5a7b7-181"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="5a7b7-181"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="5a7b7-182">Designer di esperienza utente @Microsoft</span><span class="sxs-lookup"><span data-stu-id="5a7b7-182">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="5a7b7-183">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5a7b7-183">See also</span></span>

* [<span data-ttu-id="5a7b7-184">Mixed Reality Toolkit-Unity (MRTK) su GitHub</span><span class="sxs-lookup"><span data-stu-id="5a7b7-184">Mixed Reality Toolkit-Unity (MRTK) GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="5a7b7-185">Portale della documentazione di MRTK</span><span class="sxs-lookup"><span data-stu-id="5a7b7-185">MRTK Documentation Portal</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="5a7b7-186">Introduzione a MRTK</span><span class="sxs-lookup"><span data-stu-id="5a7b7-186">Getting Started with MRTK</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [<span data-ttu-id="5a7b7-187">Linee guida per la portabilità da HoloToolkit a MRTK</span><span class="sxs-lookup"><span data-stu-id="5a7b7-187">HoloToolkit to MRTK Porting Guideline</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)

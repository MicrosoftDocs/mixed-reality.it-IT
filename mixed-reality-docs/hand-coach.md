---
title: Coach mano
description: le mani 3D attivate quando il sistema non rileva le mani dell'utente per assisterle.
author: grayclee
ms.author: glee
ms.date: 09/25/2019
ms.topic: article
keywords: Realtà mista di Windows, progettazione, Coach mano, auricolare immersivo, MRTK, Hands, assistenza
ms.openlocfilehash: 38da046256dce3242b464a0741f2afa7fb19ff3c
ms.sourcegitcommit: 7ca383ef1c5dc895ca2a289435f2e9d4c1ee6e65
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/24/2020
ms.locfileid: "85345666"
---
# <a name="hand-coach"></a><span data-ttu-id="28d11-104">Coach mano</span><span class="sxs-lookup"><span data-stu-id="28d11-104">Hand coach</span></span>
![Esempio: Hand Coach](images/HandCoach/MRTK_handCoach.jpg)<br>

<span data-ttu-id="28d11-106">Hand Coach è un modello 3D che viene attivato quando il sistema non rileva le mani dell'utente.</span><span class="sxs-lookup"><span data-stu-id="28d11-106">Hand coach is 3D modeled hands that are triggered when the system does not detect the user’s hands.</span></span> <span data-ttu-id="28d11-107">Viene implementato come componente "didattico" che aiuta a guidare l'utente quando il movimento non è stato insegnato.</span><span class="sxs-lookup"><span data-stu-id="28d11-107">This is implemented as a “teaching” component that helps guide the user when the gesture has not been taught.</span></span> <span data-ttu-id="28d11-108">Se gli utenti non hanno eseguito il movimento specificato per un periodo, il ciclo passa con un ritardo.</span><span class="sxs-lookup"><span data-stu-id="28d11-108">If users have not done the specified gesture for a period, the hands will loop with a delay.</span></span> <span data-ttu-id="28d11-109">Il coach della mano può essere usato per rappresentare la pressione di un pulsante o la selezione di un ologramma.</span><span class="sxs-lookup"><span data-stu-id="28d11-109">The Hand coach could be used to represent pressing a button or picking up a hologram.</span></span>  

## <a name="hand-coach-provided"></a><span data-ttu-id="28d11-110">Hand Coach fornito</span><span class="sxs-lookup"><span data-stu-id="28d11-110">Hand coach provided</span></span>

<span data-ttu-id="28d11-111">Il modello di interazione corrente rappresenta un'ampia gamma di controlli di movimento, ad esempio scorrimento, selezione e prossimità.</span><span class="sxs-lookup"><span data-stu-id="28d11-111">The current interaction model represents a wide variety of gesture controls such as scrolling, far select, and near tap.</span></span> <span data-ttu-id="28d11-112">Di seguito è riportato un elenco completo dei movimenti di mano esistenti disponibili in<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets"> MRTK</a>:</span><span class="sxs-lookup"><span data-stu-id="28d11-112">Below is a full list of existing hand gestures provided in<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets"> MRTK</a>:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="28d11-113">![Esempio di near Select](images/HandCoach/NearSelect.gif)</span><span class="sxs-lookup"><span data-stu-id="28d11-113">![Example of Near Select](images/HandCoach/NearSelect.gif)</span></span><br>
       <span data-ttu-id="28d11-114">**Esempio di near Select-used Mostra come selezionare i pulsanti o chiudere gli oggetti interagibili**</span><span class="sxs-lookup"><span data-stu-id="28d11-114">**Example of Near Select - Used show how to select buttons or close interactable objects**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="28d11-115">![Esempio di rubinetto aereo](images/HandCoach/AirTap.gif)</span><span class="sxs-lookup"><span data-stu-id="28d11-115">![Example of Air Tap](images/HandCoach/AirTap.gif)</span></span><br>
        <span data-ttu-id="28d11-116">**Esempio di tocco aereo: usato per mostrare come selezionare gli oggetti che sono lontani**</span><span class="sxs-lookup"><span data-stu-id="28d11-116">**Example of Air Tap - Used to show how to select objects that are far away**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="28d11-117">![Esempio di spostamento](images/HandCoach/Move.gif)</span><span class="sxs-lookup"><span data-stu-id="28d11-117">![Example of Move](images/HandCoach/Move.gif)</span></span><br>
       <span data-ttu-id="28d11-118">**Esempio di spostamento di un oggetto nello spazio: usato per mostrare come spostare un ologramma nello spazio**</span><span class="sxs-lookup"><span data-stu-id="28d11-118">**Example of Moving an object in space-Used to show how to move a hologram in space**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="28d11-119">![Esempio di rotazione](images/HandCoach/Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="28d11-119">![Example of Rotate](images/HandCoach/Rotate.gif)</span></span><br>
       <span data-ttu-id="28d11-120">**Esempio di rotazione: usata per mostrare come ruotare gli ologrammi o gli oggetti**</span><span class="sxs-lookup"><span data-stu-id="28d11-120">**Example of Rotate-Used to show how to rotate holograms or objects**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="28d11-121">![Esempio di scala](images/HandCoach/Scale.gif)</span><span class="sxs-lookup"><span data-stu-id="28d11-121">![Example of Scale](images/HandCoach/Scale.gif)</span></span><br>
       <span data-ttu-id="28d11-122">**Esempio di scala: usato per illustrare come modificare gli ologrammi in modo che siano più grandi o più piccoli**</span><span class="sxs-lookup"><span data-stu-id="28d11-122">**Example of Scale- Used to show how to manipulate holograms to be bigger or smaller**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="28d11-123">![Esempio di Palm up](images/HandCoach/PalmUp.gif)</span><span class="sxs-lookup"><span data-stu-id="28d11-123">![Example of Palm Up](images/HandCoach/PalmUp.gif)</span></span><br>
        <span data-ttu-id="28d11-124">**Esempio di palmare: uso suggerito per visualizzare i menu a mano**</span><span class="sxs-lookup"><span data-stu-id="28d11-124">**Example of Palm up – Suggested use, to bring up hand menus**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="28d11-125">![Esempio di HandFlip](images/HandCoach/HandFlip.gif)</span><span class="sxs-lookup"><span data-stu-id="28d11-125">![Example of HandFlip](images/HandCoach/HandFlip.gif)</span></span><br>
       <span data-ttu-id="28d11-126">**Esempio of hand Flip: un altro modo per visualizzare i menu a mano**</span><span class="sxs-lookup"><span data-stu-id="28d11-126">**Exmaple of Hand Flip – Another way to bring up Hand Menus**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="28d11-127">![Esempio di scorrimento](images/HandCoach/Scoll.gif)</span><span class="sxs-lookup"><span data-stu-id="28d11-127">![Example of Scroll](images/HandCoach/Scoll.gif)</span></span><br>
       <span data-ttu-id="28d11-128">**Esempio di scorrimento: usato per scorrere un elenco o un documento lungo**</span><span class="sxs-lookup"><span data-stu-id="28d11-128">**Example of Scroll – Used for scrolling a list or a long document**</span></span><br>
    :::column-end:::
:::row-end:::

## <a name="design-concepts"></a><span data-ttu-id="28d11-129">Concetti relativi alla progettazione</span><span class="sxs-lookup"><span data-stu-id="28d11-129">Design concepts</span></span>

<span data-ttu-id="28d11-130">Per Hololens2, abbiamo progettato le interazioni Hand in base a movimenti di mano istintiva e naturale.</span><span class="sxs-lookup"><span data-stu-id="28d11-130">For Hololens2, we designed out hand interactions based on instinctual and natural hand gestures.</span></span> <span data-ttu-id="28d11-131">Si ritiene che questi siano intuitivi per la maggior parte degli utenti e pertanto non hanno creato momenti dedicati per l'apprendimento dei movimenti.</span><span class="sxs-lookup"><span data-stu-id="28d11-131">We believe these to be intuitive to most users and thus did not create dedicated gesture learning moments.</span></span> <span data-ttu-id="28d11-132">Al contrario, abbiamo creato il coach per aiutare gli utenti che potrebbero rimanere bloccati o che non hanno familiarità con l'interazione con gli ologrammi. Scopri questi movimenti.</span><span class="sxs-lookup"><span data-stu-id="28d11-132">Instead, we created the hand coach to help users who might get stuck or are unfamiliar with interacting with holograms learn about these gestures.</span></span> <span data-ttu-id="28d11-133">Senza un momento di apprendimento, abbiamo pensato che gli utenti che mostravano come eseguire un'azione dimostrando che sarebbe l'opzione migliore.</span><span class="sxs-lookup"><span data-stu-id="28d11-133">Without a learning moment, we felt that showing users how to perform an action by demonstrating it would be the best option.</span></span> <span data-ttu-id="28d11-134">Negli studi, abbiamo scoperto che gli utenti erano in grado di capire il gesto ma aveva bisogno di una piccola guida.</span><span class="sxs-lookup"><span data-stu-id="28d11-134">In our studies, we found that users were able to figure out the gesture but needed a little guidance.</span></span> <span data-ttu-id="28d11-135">Se si rileva che un utente non interagisce con un oggetto per un periodo di tempo, viene attivato un coach della mano che mostra la posizione corretta e la posizione del dito.</span><span class="sxs-lookup"><span data-stu-id="28d11-135">If we detect that a user does not interact with an object for a period, a Hand coach would be triggered demonstrating the correct hand and finger placement.</span></span> 

### <a name="intuitive"></a><span data-ttu-id="28d11-136">Intuitivo</span><span class="sxs-lookup"><span data-stu-id="28d11-136">Intuitive</span></span>

<span data-ttu-id="28d11-137">Quando si animano le mani, dovrebbe essere ovvio e shoudn ' t causare confusione.</span><span class="sxs-lookup"><span data-stu-id="28d11-137">When animating hands, it should be obvious and shoudn't cause any confusion.</span></span> <span data-ttu-id="28d11-138">L'animazione delle mani è una rappresentazione del gesto che il tentativo di evocare all'utente per comprenderne lo scopo.</span><span class="sxs-lookup"><span data-stu-id="28d11-138">The animation of the hands is a representation of the gesture your trying to evoke to the user to understand it's purpose.</span></span> 

<span data-ttu-id="28d11-139">Ad esempio, se si vuole che un utente prema un pulsante, viene attivata una mano che preme un pulsante.</span><span class="sxs-lookup"><span data-stu-id="28d11-139">For example, if you wish a user to press a button, a hand pressing a button would be triggered.</span></span>

<span data-ttu-id="28d11-140">![Esempio: coach della mano vicino al tocco](images/HandCoach/NearSelect_unity.gif)</span><span class="sxs-lookup"><span data-stu-id="28d11-140">![Example: Hand coach Near Tap](images/HandCoach/NearSelect_unity.gif)</span></span><br>
<span data-ttu-id="28d11-141">*Coach della mano che illustra quasi un gioiello*</span><span class="sxs-lookup"><span data-stu-id="28d11-141">*Hand Coach demonstrating Near Tapping a Gem*</span></span>  

### <a name="hand-scale"></a><span data-ttu-id="28d11-142">Scalabilità manuale</span><span class="sxs-lookup"><span data-stu-id="28d11-142">Hand scale</span></span>

<span data-ttu-id="28d11-143">Sono state testate diverse dimensioni della mano con i menu dell'interfaccia utente e si ritiene che se le mani erano vere, ha dato una sensazione minacciosa, ma se fosse troppo piccola, era difficile vedere e comprendere il movimento.</span><span class="sxs-lookup"><span data-stu-id="28d11-143">We tested various hand sizes with the UI menus and felt that if the hands were true to size, it gave a menacing feeling but if they were too small then it was hard to see and understand the gesture.</span></span> 

<span data-ttu-id="28d11-144">**Voice over e Hands**</span><span class="sxs-lookup"><span data-stu-id="28d11-144">**Voice over and hands**</span></span>

<span data-ttu-id="28d11-145">Non aspettarsi che gli utenti possano restare in ascolto di un set di istruzioni tramite Voice over e guardare istruzioni diverse tramite il Coach mano.</span><span class="sxs-lookup"><span data-stu-id="28d11-145">Don’t expect users can listen to one set of instructions via voice over and watch different instructions via Hand coach.</span></span> <span data-ttu-id="28d11-146">Sequenziare le istruzioni per aiutare gli utenti a concentrarsi sulla propria attenzione per ridurre il sovraccarico sensoriale.</span><span class="sxs-lookup"><span data-stu-id="28d11-146">Sequence your instructions to help users focus versus compete for their attention to reduce sensory overload.</span></span>


## <a name="can-i-create-my-own"></a><span data-ttu-id="28d11-147">È possibile crearne una personalizzata?</span><span class="sxs-lookup"><span data-stu-id="28d11-147">Can I create my own?</span></span>

<span data-ttu-id="28d11-148">Sì.</span><span class="sxs-lookup"><span data-stu-id="28d11-148">Yes!</span></span> <span data-ttu-id="28d11-149">Si consiglia di creare un proprio gesto univoco per il gioco e contribuire alla community.</span><span class="sxs-lookup"><span data-stu-id="28d11-149">We encourage you to create your own unique gesture for your game and contribute back to the community!</span></span>
<span data-ttu-id="28d11-150">È stato fornito un file Maya di una mano truccata che può essere usata per l'app che può essere scaricata qui: <a href="files/HandCoach_MRTK.zip">scaricare HandCoach_MRTK.zip</a></span><span class="sxs-lookup"><span data-stu-id="28d11-150">We have provided a Maya file of a Rigged hand that can be used for your app which can be downloaded here: <a href="files/HandCoach_MRTK.zip"> Download HandCoach_MRTK.zip</a></span></span>

<span data-ttu-id="28d11-151">![Esempio di mani animate in Maya](images/HandCoach/MayaSelect_Gif.gif)</span><span class="sxs-lookup"><span data-stu-id="28d11-151">![Example of Animated Hands in Maya](images/HandCoach/MayaSelect_Gif.gif)</span></span><br>
<span data-ttu-id="28d11-152">*Esempio di mano animata di una casella in Maya*</span><span class="sxs-lookup"><span data-stu-id="28d11-152">*Example of animated Hand Poking a box in Maya*</span></span>


<span data-ttu-id="28d11-153">**Strumento di creazione consigliato**</span><span class="sxs-lookup"><span data-stu-id="28d11-153">**Recommended authoring tool**</span></span>

<span data-ttu-id="28d11-154">Tra gli artisti 3D, molti scelgono di usare il [Maya di Autodesk, che a sua volta è in grado di usare HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) per trasformare il modo in cui vengono create le risorse.</span><span class="sxs-lookup"><span data-stu-id="28d11-154">Among 3D artists, many choose to use [Autodesk’s Maya which itself is able to use HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) to transform the way assets are created.</span></span> <span data-ttu-id="28d11-155">Il file hands fornito è un file binario Maya, quindi è consigliabile usare Maya per animare ed esportare le mani.</span><span class="sxs-lookup"><span data-stu-id="28d11-155">The hands file provided is a Maya Binary File, so it is recommended to use Maya to animate and export the hands.</span></span> <span data-ttu-id="28d11-156">Se si preferisce usare un altro programma 3D, di seguito è riportato un <b>. FBX</b>: <a href="files/HandCoachMRTK_FBX.zip">scaricare HandCoachMRTK_FBX.zip</a> per creare la configurazione del controller.</span><span class="sxs-lookup"><span data-stu-id="28d11-156">If you prefer to use another 3D program, here is a <b>.FBX</b>: <a href="files/HandCoachMRTK_FBX.zip">           Download HandCoachMRTK_FBX.zip</a> to create your own controller setup.</span></span> 

<span data-ttu-id="28d11-157">Se si usa il file della mano Maya scaricabile fornito, si consiglia di ridimensionare le mani in Unity a 0,6.</span><span class="sxs-lookup"><span data-stu-id="28d11-157">If using the downloadable maya Hand File provided, it is suggested to scale down the hands in unity to 0.6.</span></span>

<span data-ttu-id="28d11-158">![Esempio: rig della mano del coach in Maya](images/HandCoach/MayaExample.png)</span><span class="sxs-lookup"><span data-stu-id="28d11-158">![Example: Hand coach rig in Maya](images/HandCoach/MayaExample.png)</span></span><br>
<span data-ttu-id="28d11-159">*Mani truccate*</span><span class="sxs-lookup"><span data-stu-id="28d11-159">*Rigged Hands*</span></span>

### <a name="technical-specs"></a><span data-ttu-id="28d11-160">Specifiche tecniche</span><span class="sxs-lookup"><span data-stu-id="28d11-160">Technical Specs</span></span>

*   <span data-ttu-id="28d11-161">Il file a due passate è disponibile nel formato Maya ASCII</span><span class="sxs-lookup"><span data-stu-id="28d11-161">Two handed File is available in Maya Ascii format</span></span>
*    <span data-ttu-id="28d11-162">Il lato destro e sinistro è disponibile nel formato binario Maya</span><span class="sxs-lookup"><span data-stu-id="28d11-162">Right and Left Hand is available in Maya Binary format</span></span>
*   <span data-ttu-id="28d11-163">Impostare il file Maya su 24 FPS</span><span class="sxs-lookup"><span data-stu-id="28d11-163">Set your Maya file to 24 FPS</span></span>
*   <span data-ttu-id="28d11-164">All'interno del file è presente una mano sinistra e una destra che può essere usata per due movimenti gestiti o a mano singola.</span><span class="sxs-lookup"><span data-stu-id="28d11-164">Within the file, there is a left and right hand which can be used for two handed or single-handed gestures.</span></span> <span data-ttu-id="28d11-165">La mano destra sarà visibile solo per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="28d11-165">The right hand will only be visible by default.</span></span>
*   <span data-ttu-id="28d11-166">Si consiglia di lasciare un buffer di circa 10 frame all'inizio e di fine per Fades</span><span class="sxs-lookup"><span data-stu-id="28d11-166">It is suggested to leave a buffer of about 10 frames at the beginning and end for fades</span></span>
*   <span data-ttu-id="28d11-167">Se si aggiunge un'animazione a un oggetto con una destinazione specificata, è consigliabile aggiungere un'animazione a una casella predefinita o a un valore null.</span><span class="sxs-lookup"><span data-stu-id="28d11-167">If animating a object with a specified target, its best practice to animate to a Default box or Null.</span></span>
*   <span data-ttu-id="28d11-168">Se la mano sta aggiungendo un'animazione a un oggetto fisico, ad esempio una casella, è consigliabile non animare la traduzione in Maya, ma attendere per animarla in Unity o nel codice.</span><span class="sxs-lookup"><span data-stu-id="28d11-168">If the hand is animating a physical object such as a box, its best practice to not animate the translation in Maya but wait to animate it in Unity or in Code.</span></span>
*   <span data-ttu-id="28d11-169">L'animazione visibile dovrebbe essere 1,5 secondi per la trasmissione di informazioni significative</span><span class="sxs-lookup"><span data-stu-id="28d11-169">Visible Animation should be 1.5 secs for any meaningful information to be conveyed</span></span>
*   <span data-ttu-id="28d11-170">Quando si ritiene soddisfacente l'animazione:</span><span class="sxs-lookup"><span data-stu-id="28d11-170">When you feel satisfied with your animation:</span></span>
    *   <span data-ttu-id="28d11-171">Selezionare tutti i giunti e cuocere i fotogrammi chiave</span><span class="sxs-lookup"><span data-stu-id="28d11-171">Select all joints and bake key frames</span></span>
    *   <span data-ttu-id="28d11-172">Eliminare i controller, selezionare le giunzioni e la mesh ed esportare come FBX</span><span class="sxs-lookup"><span data-stu-id="28d11-172">Delete the Controllers, Select the joints and mesh and export as an FBX</span></span>
    *  <span data-ttu-id="28d11-173">Se sono presenti più animazioni, è possibile usare l'utilità di esportazione del gioco integrata di Maya:https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html</span><span class="sxs-lookup"><span data-stu-id="28d11-173">If there are Multiple Animations, you can use Maya’s built in Game Exporter: https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html</span></span>

## <a name="exporting-from-maya"></a><span data-ttu-id="28d11-174">Esportazione da Maya</span><span class="sxs-lookup"><span data-stu-id="28d11-174">Exporting from Maya</span></span>

<span data-ttu-id="28d11-175">Una volta soddisfatta l'animazione</span><span class="sxs-lookup"><span data-stu-id="28d11-175">After you are satisfied with your animation</span></span>
* <span data-ttu-id="28d11-176">Seleziona tutte le giunzioni: seleziona > gerarchia</span><span class="sxs-lookup"><span data-stu-id="28d11-176">Select all joints: Select > Hierarchy</span></span>

     ![Esempio: posizione del menu](images/HandCoach/Hierarchy.png)<br>
* <span data-ttu-id="28d11-178">Cuocere l'animazione: passare a animazione > chiave > animazione Bake</span><span class="sxs-lookup"><span data-stu-id="28d11-178">Bake out your animation: Switch to Animation > Key > Bake Animation</span></span>

     ![Esempio: posizione del menu](images/HandCoach/BakeAnimation.png)<br>
* <span data-ttu-id="28d11-180">Eliminare il rig del controller: DELINEATORE > MainR_Grp o MainL_Grp</span><span class="sxs-lookup"><span data-stu-id="28d11-180">Delete the Controller Rig: Outliner > MainR_Grp or MainL_Grp</span></span>

     ![Esempio: posizione del menu](images/HandCoach/ControllerRig.png)<br>

* <span data-ttu-id="28d11-182">Esporta come FBX: selezionare JNT + mesh: file > Esporta selezione (casella di opzione) > selezione esportazione</span><span class="sxs-lookup"><span data-stu-id="28d11-182">Export as FBX: Select JNT + Mesh: File > Export Selection (option box) > Export Selection</span></span>

     ![Esempio: posizione del menu](images/HandCoach/OptionBox.png)<br>

     ![Esempio: posizione del menu](images/HandCoach/SelectionExport.png)<br>

     ![Esempio: posizione del menu](images/HandCoach/FBXSelection.png)<br>


 <span data-ttu-id="28d11-186">Quando si esporta come FBX e si inserisce in Unity, ridimensionare le mani fino a 0,6.</span><span class="sxs-lookup"><span data-stu-id="28d11-186">When exporting as a FBX and brought into Unity, scale the hands down to 0.6.</span></span> <span data-ttu-id="28d11-187">Abbiamo scoperto che questo era il giusto equilibrio per la visualizzazione delle mani.</span><span class="sxs-lookup"><span data-stu-id="28d11-187">We found that this was perfect balance for displaying the hands.</span></span> 

<span data-ttu-id="28d11-188">![Esempio: impostazioni Unity](images/HandCoach/HandHintScale.png)</span><span class="sxs-lookup"><span data-stu-id="28d11-188">![Example: Unity Settings](images/HandCoach/HandHintScale.png)</span></span><br>
<span data-ttu-id="28d11-189">*Impostazioni Unity per HandCoach_R prefabbricate trovato in MRTK*</span><span class="sxs-lookup"><span data-stu-id="28d11-189">*Unity Settings for HandCoach_R prefab found in MRTK*</span></span>


## <a name="implementing-hands-into-your-unity-project"></a><span data-ttu-id="28d11-190">Implementazione di Hands nel progetto Unity</span><span class="sxs-lookup"><span data-stu-id="28d11-190">Implementing Hands into your Unity project</span></span>

### <a name="best-practices"></a><span data-ttu-id="28d11-191">Procedure consigliate</span><span class="sxs-lookup"><span data-stu-id="28d11-191">Best practices</span></span>
*    <span data-ttu-id="28d11-192">Si consiglia di ridimensionare le mani in Unity a 0,6</span><span class="sxs-lookup"><span data-stu-id="28d11-192">It is suggested to scale down the hands in unity to 0.6</span></span>
*   <span data-ttu-id="28d11-193">Le mani devono essere riprodotte due volte e se non sono state completate, il ciclo continua fino al completamento del movimento.</span><span class="sxs-lookup"><span data-stu-id="28d11-193">Hands should be played twice and if not completed then continuously looped until gesture is completed.</span></span> <span data-ttu-id="28d11-194">Per assicurarsi che l'utente abbia il tempo necessario per eseguire la registrazione e visualizzare il movimento, è necessario eseguire due volte il ciclo delle mani.</span><span class="sxs-lookup"><span data-stu-id="28d11-194">The hands should be looped twice to ensure the user had time to register and see the gesture.</span></span> <span data-ttu-id="28d11-195">Le mani devono dissolversi tra i cicli.</span><span class="sxs-lookup"><span data-stu-id="28d11-195">The hands should fade in and out between loops.</span></span> 
 *  <span data-ttu-id="28d11-196">Se le mani degli utenti sono visibili dalle fotocamere HL2, ma gli utenti non eseguono l'interazione necessaria, le mani verranno visualizzate dopo 10 secondi.</span><span class="sxs-lookup"><span data-stu-id="28d11-196">If user’s hands are visible by HL2 cameras but users are not doing the interaction needed of them the hands will appear after 10 seconds.</span></span>
*   <span data-ttu-id="28d11-197">Se le mani dell'utente non sono visibili dalle fotocamere HL2, le mani verranno visualizzate dopo 5 secondi.</span><span class="sxs-lookup"><span data-stu-id="28d11-197">If user’s hands are NOT visible by HL2 cameras, the hands will appear after 5 seconds.</span></span>  
*   <span data-ttu-id="28d11-198">Se le mani dell'utente vengono rilevate in maniera visibile dalle fotocamere HL2 al centro dell'animazione, l'animazione verrà completata e sfumata.</span><span class="sxs-lookup"><span data-stu-id="28d11-198">If user’s hands are visibly tracked by HL2 cameras in the middle of the animation, the animation will complete and fade out.</span></span>
*   <span data-ttu-id="28d11-199">Se si include il Voice over, è consigliabile che corrisponda al gesto della mano.</span><span class="sxs-lookup"><span data-stu-id="28d11-199">If you are including voice over, we suggest that it corresponds to the gesture of the hand.</span></span>
*   <span data-ttu-id="28d11-200">Se è stato insegnato almeno una volta, ripetere il movimento solo se è stato rilevato che l'utente è bloccato.</span><span class="sxs-lookup"><span data-stu-id="28d11-200">If you have taught the hands at least once, only repeat the gesture if its detected that the user is stuck.</span></span>
*   <span data-ttu-id="28d11-201">Se sono critiche posizioni specifiche per Finger/Hand, assicurarsi che gli utenti possano vedere chiaramente queste sfumature nell'animazione.</span><span class="sxs-lookup"><span data-stu-id="28d11-201">If specific finger/hand positions are critical, ensure users can clearly see these nuances in the animation.</span></span> <span data-ttu-id="28d11-202">Provare a pescare le mani in modo che le parti più importanti siano chiaramente visibili.</span><span class="sxs-lookup"><span data-stu-id="28d11-202">Try angling the hands so the most important parts are clearly visible.</span></span> 
* <span data-ttu-id="28d11-203">Se si nota la distorsione delle mani, è necessario passare alle impostazioni di qualità di Unity per aumentare la quantità di ossa.</span><span class="sxs-lookup"><span data-stu-id="28d11-203">If you notice distortion on the hands, you need to go to Unity's Quality settings increase the amount of bones.</span></span> 
 <span data-ttu-id="28d11-204">Passare alle impostazioni del progetto modifica > di Unity > qualità > altri pesi > Blend.</span><span class="sxs-lookup"><span data-stu-id="28d11-204">Go to Unity's Edit > Project Settings > Quality > Other > Blend Weights.</span></span> <span data-ttu-id="28d11-205">Assicurarsi che siano selezionate "4 ossa" per visualizzare le giunzioni uniformi.</span><span class="sxs-lookup"><span data-stu-id="28d11-205">Make sure "4 bones" are selected to see Smooth Joints.</span></span> 

   ![Esempio: posizione del menu](images/HandCoach/ProjectSettings.png)<br>





### <a name="what-to-avoid"></a><span data-ttu-id="28d11-207">Da evitare</span><span class="sxs-lookup"><span data-stu-id="28d11-207">What to avoid</span></span>
* <span data-ttu-id="28d11-208">Ridimensionamento delle mani troppo grandi</span><span class="sxs-lookup"><span data-stu-id="28d11-208">Scaling the Hands too large</span></span>
* <span data-ttu-id="28d11-209">Posizionare le mani troppo vicino all'utente</span><span class="sxs-lookup"><span data-stu-id="28d11-209">placing the Hands too close to the user</span></span>
* <span data-ttu-id="28d11-210">Le mani devono essere insegnate una sola volta.</span><span class="sxs-lookup"><span data-stu-id="28d11-210">Hands should only be taught once.</span></span> <span data-ttu-id="28d11-211">Il superamento dell'insegnamento può causare confusione e confusione</span><span class="sxs-lookup"><span data-stu-id="28d11-211">Over teaching can cause confusion and messiness</span></span>
*   <span data-ttu-id="28d11-212">Per portarla in Unity, scaricare la versione più recente di MRTK qui:https://github.com/microsoft/MixedRealityToolkit-Unity</span><span class="sxs-lookup"><span data-stu-id="28d11-212">Bringing it into Unity, please download the latest MRTK  here: https://github.com/microsoft/MixedRealityToolkit-Unity</span></span>
    *   <span data-ttu-id="28d11-213">Materiale: Teaching_Hand2</span><span class="sxs-lookup"><span data-stu-id="28d11-213">Material: Teaching_Hand2</span></span>
    *   <span data-ttu-id="28d11-214">Script: fare riferimento alle linee guida di MRTK per <a href= "https://github.com/MixedRealityToolkit-Unity/blob/'HandCoachUX'/Documentation/README_HandCoach.md">MRTK Hand Coach</a></span><span class="sxs-lookup"><span data-stu-id="28d11-214">Scripts: Refer to MRTK guidelines for <a href= "https://github.com/MixedRealityToolkit-Unity/blob/'HandCoachUX'/Documentation/README_HandCoach.md"> MRTK hand coach </a></span></span>
    *   <span data-ttu-id="28d11-215">Impostazione per progetto</span><span class="sxs-lookup"><span data-stu-id="28d11-215">Per- project setting</span></span>
        *   <span data-ttu-id="28d11-216">Scenografia impostata su UWP: è possibile trovare l'istruzione nel [progetto di Unity](Configure-Unity-Project.md) per la realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="28d11-216">Scene set to UWP: Instruction can be found on the [Configure Unity Project](Configure-Unity-Project.md) for Windows Mixed Reality</span></span>

## <a name="see-also"></a><span data-ttu-id="28d11-217">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="28d11-217">See also</span></span>
* [<span data-ttu-id="28d11-218">Interazione-nozioni fondamentali</span><span class="sxs-lookup"><span data-stu-id="28d11-218">Interaction-fundamentals</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="28d11-219">Processo di creazione dell'asset</span><span class="sxs-lookup"><span data-stu-id="28d11-219">Asset Creation Process</span></span>](asset-creation-process.md)
* [<span data-ttu-id="28d11-220">Movimenti</span><span class="sxs-lookup"><span data-stu-id="28d11-220">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="28d11-221">Installare gli strumenti</span><span class="sxs-lookup"><span data-stu-id="28d11-221">Install the Tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="28d11-222">Configurare il progetto Unity</span><span class="sxs-lookup"><span data-stu-id="28d11-222">Configure Unity Project</span></span>](Configure-Unity-Project.md)
* [<span data-ttu-id="28d11-223">Panoramica dello sviluppo per Unity</span><span class="sxs-lookup"><span data-stu-id="28d11-223">Unity development overview</span></span>](unity-development-overview.md)
* [<span data-ttu-id="28d11-224">MRTK 101</span><span class="sxs-lookup"><span data-stu-id="28d11-224">MRTK 101</span></span>](mrtk-101.md)

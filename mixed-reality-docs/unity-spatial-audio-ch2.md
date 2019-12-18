---
title: Esercitazioni audio spaziali-2. Suoni interazione pulsante Spatializing
description: Aggiungere un pulsante al progetto e spatialize i suoni di interazione dei pulsanti.
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: realtà mista, Unity, esercitazione, hololens2, audio spaziale
ms.openlocfilehash: bd70e3bc88ee39b2c6257089ac3a2b93dfae0ad1
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182778"
---
# <a name="spatializing-button-interaction-sounds"></a><span data-ttu-id="422dd-105">Suoni interazione pulsante Spatializing</span><span class="sxs-lookup"><span data-stu-id="422dd-105">Spatializing button interaction sounds</span></span>

## <a name="objectives"></a><span data-ttu-id="422dd-106">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="422dd-106">Objectives</span></span>
<span data-ttu-id="422dd-107">In questo secondo capitolo del modulo audio spaziale delle esercitazioni di HoloLens 2 è possibile:</span><span class="sxs-lookup"><span data-stu-id="422dd-107">In this second chapter of the spatial audio module of the HoloLens 2 tutorials, you'll:</span></span>
* <span data-ttu-id="422dd-108">Aggiungere un pulsante</span><span class="sxs-lookup"><span data-stu-id="422dd-108">Add a button</span></span>
* <span data-ttu-id="422dd-109">Spatialize i suoni dei clic del pulsante</span><span class="sxs-lookup"><span data-stu-id="422dd-109">Spatialize the button click sounds</span></span>

## <a name="add-a-button"></a><span data-ttu-id="422dd-110">Aggiungere un pulsante</span><span class="sxs-lookup"><span data-stu-id="422dd-110">Add a button</span></span>
<span data-ttu-id="422dd-111">Nel riquadro **progetto** selezionare **Asset** e digitare "PressableButtonHoloLens2" nella barra di ricerca:</span><span class="sxs-lookup"><span data-stu-id="422dd-111">In the **Project** pane, select **Assets** and type "PressableButtonHoloLens2" in the search bar:</span></span>

![Prefabbricato Button negli asset](images/spatial-audio/button-prefab-in-assets.png)

<span data-ttu-id="422dd-113">Il prefabbricato del pulsante è la voce rappresentata da un'icona blu, anziché da un'icona bianca.</span><span class="sxs-lookup"><span data-stu-id="422dd-113">The button prefab is the entry represented by a blue icon, rather than a white icon.</span></span> <span data-ttu-id="422dd-114">Trascinare il prefabbricato denominato **PressableButtonHoloLens2** nel riquadro **gerarchia** .</span><span class="sxs-lookup"><span data-stu-id="422dd-114">Drag the prefab named **PressableButtonHoloLens2** into the **Hierarchy** pane.</span></span> <span data-ttu-id="422dd-115">Nel riquadro **Inspector** del pulsante nuovo impostare la proprietà **position** su (0,-0,4, 2) in modo che venga visualizzata davanti all'utente all'avvio dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="422dd-115">In the **Inspector** pane for your new button, set the **Position** property to (0, -0.4, 2) so that it will appear in front of the user when the application starts.</span></span> <span data-ttu-id="422dd-116">Il componente **Transform** del pulsante sarà simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="422dd-116">The **Transform** component of the button will look like this:</span></span>

![Trasformazione pulsante](images/spatial-audio/button-transform.png)

## <a name="spatialize-button-feedback"></a><span data-ttu-id="422dd-118">Commenti e suggerimenti sul pulsante Spatialize</span><span class="sxs-lookup"><span data-stu-id="422dd-118">Spatialize button feedback</span></span>
<span data-ttu-id="422dd-119">In questo passaggio si spatialize il feedback audio per il pulsante.</span><span class="sxs-lookup"><span data-stu-id="422dd-119">In this step, you'll spatialize the audio feedback for the button.</span></span> <span data-ttu-id="422dd-120">Per suggerimenti sulla progettazione correlati, vedere [progettazione di suoni spaziali](spatial-sound-design.md).</span><span class="sxs-lookup"><span data-stu-id="422dd-120">For related design suggestions, see [spatial sound design](spatial-sound-design.md).</span></span> 

<span data-ttu-id="422dd-121">Il riquadro **mixer audio** è il punto in cui definire le destinazioni, denominate **gruppi di mixer**, per la riproduzione audio dai componenti di **origine audio** .</span><span class="sxs-lookup"><span data-stu-id="422dd-121">The **Audio Mixer** pane is where you'll define destinations, called **Mixer Groups**, for audio playback from **Audio Source** components.</span></span> 
* <span data-ttu-id="422dd-122">Aprire il riquadro **mixer audio** dalla barra dei menu usando la **finestra > audio-> Audio Mixer**</span><span class="sxs-lookup"><span data-stu-id="422dd-122">Open the **Audio Mixer** pane from the menu bar using **Window -> Audio -> Audio Mixer**</span></span>
* <span data-ttu-id="422dd-123">Per creare un **mixer** , fare clic su "+" accanto a **mixer**.</span><span class="sxs-lookup"><span data-stu-id="422dd-123">Create a **Mixer** by clicking the '+' next to **Mixers**.</span></span> <span data-ttu-id="422dd-124">Il nuovo mixer includerà un **gruppo** predefinito denominato **Master**.</span><span class="sxs-lookup"><span data-stu-id="422dd-124">The new mixer will include a default **Group** called **Master**.</span></span>

<span data-ttu-id="422dd-125">Il riquadro del **mixer** sarà ora simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="422dd-125">Your **Mixer** pane will now look like this:</span></span>

![Pannello mixer con primo mixer](images/spatial-audio/mixer-panel-with-first-mixer.png)

> [!NOTE]
> <span data-ttu-id="422dd-127">Fino a quando non viene abilitato il riverbero nel [capitolo 5](unity-spatial-audio-ch5.md), il contatore del volume del mixer non Mostra l'attività per i suoni riprodotti tramite Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="422dd-127">Until reverb is enabled in [Chapter 5](unity-spatial-audio-ch5.md), the mixer's volume meter doesn't show activity for sounds played through the Microsoft Spatializer</span></span>

<span data-ttu-id="422dd-128">Fare clic su **PressableButtonHoloLens2** nel riquadro **gerarchia** .</span><span class="sxs-lookup"><span data-stu-id="422dd-128">Click the **PressableButtonHoloLens2** in the **Hierarchy** pane.</span></span> <span data-ttu-id="422dd-129">Nel riquadro **Inspector** :</span><span class="sxs-lookup"><span data-stu-id="422dd-129">In the **Inspector** pane:</span></span>
1. <span data-ttu-id="422dd-130">Trovare il componente di **origine audio**</span><span class="sxs-lookup"><span data-stu-id="422dd-130">Find the **Audio Source** component</span></span>
2. <span data-ttu-id="422dd-131">Per la proprietà **output** , fare clic sul selettore e scegliere il mixer</span><span class="sxs-lookup"><span data-stu-id="422dd-131">For the **Output** property, click the selector and choose your mixer</span></span>
3. <span data-ttu-id="422dd-132">Selezionare la casella di controllo **Spatialize**</span><span class="sxs-lookup"><span data-stu-id="422dd-132">Check the **Spatialize** checkbox</span></span>
4. <span data-ttu-id="422dd-133">Spostare il dispositivo di scorrimento **Blend spaziale** su 3D (1).</span><span class="sxs-lookup"><span data-stu-id="422dd-133">Move the **Spatial Blend** slider to 3D (1).</span></span>

> [!NOTE]
> <span data-ttu-id="422dd-134">Nelle versioni di Unity precedenti alla 2019, la casella di controllo ' Spatialize ' si trova nella parte inferiore del riquadro **Inspector** per l' **origine audio**.</span><span class="sxs-lookup"><span data-stu-id="422dd-134">In versions of Unity prior to 2019, the 'Spatialize' checkbox is at the bottom of the **Inspector** pane for the **Audio Source**.</span></span>

<span data-ttu-id="422dd-135">Dopo queste modifiche, il componente di **origine audio** del **PressableButtonHoloLens2** sarà simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="422dd-135">After these changes, the **Audio Source** component of your **PressableButtonHoloLens2** will look like this:</span></span>

![Origine audio pulsante](images/spatial-audio/button-audio-source.png)

> [!NOTE]
> <span data-ttu-id="422dd-137">Se si sposta **Blend spaziale** in 1 (3D) senza selezionare la casella di controllo **Spatialize** , Unity utilizzerà il relativo Spatializer di panoramica anziché **Microsoft Spatializer** con HRTFs.</span><span class="sxs-lookup"><span data-stu-id="422dd-137">If you move **Spatial Blend** to 1 (3D) without checking the **Spatialize** checkbox, Unity will use its panning spatializer, instead of the **Microsoft Spatializer** with HRTFs.</span></span>

## <a name="adjust-the-volume-curve"></a><span data-ttu-id="422dd-138">Modificare la curva del volume</span><span class="sxs-lookup"><span data-stu-id="422dd-138">Adjust the Volume curve</span></span>
<span data-ttu-id="422dd-139">Per impostazione predefinita, Unity attenua i suoni spaziali Man mano che si ottengono più lontano dal listener.</span><span class="sxs-lookup"><span data-stu-id="422dd-139">By default, Unity will attenuate spatialized sounds as they get farther from the listener.</span></span> <span data-ttu-id="422dd-140">Quando questa attenuazione viene applicata ai suoni di feedback interazione, l'interfaccia può diventare più difficile da usare.</span><span class="sxs-lookup"><span data-stu-id="422dd-140">When this attenuation is applied to interaction feedback sounds, the interface can become more difficult to use.</span></span>

<span data-ttu-id="422dd-141">Per disabilitare questa attenuazione, modificare la curva del **volume** .</span><span class="sxs-lookup"><span data-stu-id="422dd-141">To disable this attenuation, adjust the **Volume** curve.</span></span> <span data-ttu-id="422dd-142">Nel componente **origine audio** del riquadro **Inspector** per **PressableButtonHoloLens2**è presente una sezione denominata **impostazioni audio 3D**.</span><span class="sxs-lookup"><span data-stu-id="422dd-142">In the **Audio Source** component of the **Inspector** pane for the **PressableButtonHoloLens2**, there is a section called **3D Sound Settings**.</span></span> <span data-ttu-id="422dd-143">In questa sezione:</span><span class="sxs-lookup"><span data-stu-id="422dd-143">In that section:</span></span>
1. <span data-ttu-id="422dd-144">Impostare la proprietà **volume attenuazione** su Linear</span><span class="sxs-lookup"><span data-stu-id="422dd-144">Set the **Volume Rolloff** property to Linear</span></span>
2. <span data-ttu-id="422dd-145">Trascinare l'endpoint sulla curva del **volume** (la curva rossa) da' 0' sull'asse y fino a' 1'</span><span class="sxs-lookup"><span data-stu-id="422dd-145">Drag the endpoint on the **Volume** curve (the red curve) from '0' on the y axis up to '1'</span></span>
3. <span data-ttu-id="422dd-146">Per regolare la forma della curva del **volume** in modo che sia piatta, trascinare il controllo forma curva bianca in modo che sia parallelo all'asse X</span><span class="sxs-lookup"><span data-stu-id="422dd-146">To adjust the shape of the **Volume** curve to be flat, drag the white curve shape control to be parallel to the X axis</span></span>

<span data-ttu-id="422dd-147">Una volta apportate queste modifiche, la sezione **impostazioni audio 3D** delle proprietà di **origine audio** del **PressableButtonHoloLens2** sarà simile alla seguente:</span><span class="sxs-lookup"><span data-stu-id="422dd-147">After these changes, the **3D Sound Settings** section of the **Audio Source** properties of the **PressableButtonHoloLens2** will look like this:</span></span>

![Impostazioni suono 3D pulsante](images/spatial-audio/button-3d-sound-settings.png)

## <a name="next-steps"></a><span data-ttu-id="422dd-149">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="422dd-149">Next steps</span></span>

<span data-ttu-id="422dd-150">Provare l'app in un HoloLens 2 o nell'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="422dd-150">Try out your app on a HoloLens 2, or in the Unity editor.</span></span> <span data-ttu-id="422dd-151">Nell'app è possibile toccare il pulsante e sentire i suoni di interazione dei pulsanti spaziali.</span><span class="sxs-lookup"><span data-stu-id="422dd-151">In the app, you can touch the button and hear the spatialized button interaction sounds.</span></span>

<span data-ttu-id="422dd-152">Quando si esegue il test nell'editor di Unity, premere la barra spaziatrice e scorrere con la rotellina di scorrimento per attivare la simulazione manuale.</span><span class="sxs-lookup"><span data-stu-id="422dd-152">When testing in the Unity editor, press the space bar and scroll with the scroll wheel to activate hand simulation.</span></span> <span data-ttu-id="422dd-153">Per ulteriori informazioni, vedere la [documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene).</span><span class="sxs-lookup"><span data-stu-id="422dd-153">For more info, see the [MRTK documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene).</span></span>

<span data-ttu-id="422dd-154">Continuare con il [capitolo 3](unity-spatial-audio-ch3.md) per aggiungere un video all'app e spatialize l'audio dal video.</span><span class="sxs-lookup"><span data-stu-id="422dd-154">Continue to [Chapter 3](unity-spatial-audio-ch3.md) to add a video to your app, and spatialize the audio from the video.</span></span>


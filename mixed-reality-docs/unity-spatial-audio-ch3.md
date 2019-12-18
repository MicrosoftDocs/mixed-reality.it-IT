---
title: Esercitazioni audio spaziali-3. Spatializing audio da un video
description: Importare un asset video nel progetto Unity e spatialize l'audio dal video.
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: realtà mista, Unity, esercitazione, hololens2, audio spaziale
ms.openlocfilehash: 1e5c84fd7d14cc5edc78839bbdf91590cc7fd8e7
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182748"
---
# <a name="spatializing-audio-from-a-video"></a><span data-ttu-id="4111e-105">Spatializing audio da un video</span><span class="sxs-lookup"><span data-stu-id="4111e-105">Spatializing audio from a video</span></span>
<span data-ttu-id="4111e-106">In questo terzo capitolo del modulo audio spaziale delle esercitazioni di HoloLens 2 Unity è possibile:</span><span class="sxs-lookup"><span data-stu-id="4111e-106">In this 3rd chapter of the spatial audio module of the HoloLens 2 Unity tutorials, you'll:</span></span>
* <span data-ttu-id="4111e-107">Importare un video e aggiungere un lettore video</span><span class="sxs-lookup"><span data-stu-id="4111e-107">Import a video and add a Video Player</span></span>
* <span data-ttu-id="4111e-108">Riprodurre il video su un quadrilatero</span><span class="sxs-lookup"><span data-stu-id="4111e-108">Play the video onto a quadrangle</span></span>
* <span data-ttu-id="4111e-109">Indirizzare l'audio dal video al quadrilatero e spatialize l'audio</span><span class="sxs-lookup"><span data-stu-id="4111e-109">Route audio from the video to the quadrangle, and spatialize the audio</span></span>

## <a name="import-a-video-and-add-a-video-player"></a><span data-ttu-id="4111e-110">Importare un video e aggiungere un lettore video</span><span class="sxs-lookup"><span data-stu-id="4111e-110">Import a video and add a Video Player</span></span>

<span data-ttu-id="4111e-111">Trascinare un file video nel riquadro **progetto** del progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="4111e-111">Drag a video file into the **Project** pane in your Unity project.</span></span> <span data-ttu-id="4111e-112">È possibile utilizzare [questo video](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) dal progetto di esempio di audio spaziale.</span><span class="sxs-lookup"><span data-stu-id="4111e-112">You can use [this video](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) from the spatial audio sample project.</span></span>

![Cartella asset con video](images/spatial-audio/assets-folder-with-video.png)

<span data-ttu-id="4111e-114">La regolazione delle impostazioni di qualità nel clip video può garantire la riproduzione uniforme in HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="4111e-114">Adjusting the quality settings on the video clip can ensure smooth playback on HoloLens 2.</span></span> <span data-ttu-id="4111e-115">Fare clic sul file video nel riquadro **progetto** .</span><span class="sxs-lookup"><span data-stu-id="4111e-115">Click on the video file in the **Project** pane.</span></span> <span data-ttu-id="4111e-116">Quindi, nel riquadro **Inspector** per il file video, sostituire le impostazioni per le app di Windows Store e:</span><span class="sxs-lookup"><span data-stu-id="4111e-116">Then in the **Inspector** pane for the video file, override the settings for Windows Store Apps, and:</span></span>
* <span data-ttu-id="4111e-117">Abilita **transcodifica**</span><span class="sxs-lookup"><span data-stu-id="4111e-117">Enable **Transcode**</span></span>
* <span data-ttu-id="4111e-118">Imposta **codec** su H264</span><span class="sxs-lookup"><span data-stu-id="4111e-118">Set **Codec** to H264</span></span>
* <span data-ttu-id="4111e-119">Impostare la **Modalità bitrate** su low</span><span class="sxs-lookup"><span data-stu-id="4111e-119">Set **Bitrate Mode** to Low</span></span>
* <span data-ttu-id="4111e-120">Impostare la **qualità spaziale** su una qualità media spaziale</span><span class="sxs-lookup"><span data-stu-id="4111e-120">Set **Spatial Quality** to Medium Spatial Quality</span></span>

<span data-ttu-id="4111e-121">Dopo queste modifiche, il riquadro **Inspector** per il file video sarà simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="4111e-121">After these adjustments, the **Inspector** pane for the video file will look like this:</span></span>

![Riquadro proprietà video](images/spatial-audio/video-property-pane.png)

<span data-ttu-id="4111e-123">Successivamente, aggiungere un oggetto **lettore video** alla **gerarchia** facendo clic con il pulsante destro del mouse sul riquadro **gerarchia** e scegliendo **video-> lettore video**:</span><span class="sxs-lookup"><span data-stu-id="4111e-123">Next, add a **Video Player** object to the **Hierarchy** by right-clicking on the **Hierarchy** pane and choosing **Video -> Video Player**:</span></span>

![Lettore video nella gerarchia](images/spatial-audio/video-player-in-hierarchy.png)

## <a name="play-video-onto-a-quadrangle"></a><span data-ttu-id="4111e-125">Riprodurre video su un quadrilatero</span><span class="sxs-lookup"><span data-stu-id="4111e-125">Play video onto a quadrangle</span></span>
<span data-ttu-id="4111e-126">L'oggetto **Player video** necessita di un oggetto gioco con trama su cui eseguire il rendering del video.</span><span class="sxs-lookup"><span data-stu-id="4111e-126">The **Video Player** object needs a textured game object on which to render the video.</span></span> <span data-ttu-id="4111e-127">Per prima cosa, aggiungere un **Quad** alla **gerarchia** facendo clic con il pulsante destro del mouse sul riquadro **gerarchia** e scegliendo **oggetto 3D-> Quad**:</span><span class="sxs-lookup"><span data-stu-id="4111e-127">First, add a **Quad** to your **Hierarchy** by right-clicking on the **Hierarchy** pane and choosing **3D Object -> Quad**:</span></span>

![Aggiungere Quad alla gerarchia](images/spatial-audio/add-quad-to-hierarchy.png)

<span data-ttu-id="4111e-129">Per assicurarsi che il **Quad** venga visualizzato davanti all'utente all'avvio dell'applicazione, impostare la proprietà **position** del **Quad** su (0, 0, 2) e la proprietà **scale** su (1,28, 0,72, 1).</span><span class="sxs-lookup"><span data-stu-id="4111e-129">To ensure the **Quad** appears in front of the user when the application starts, set the **Position** property of the **Quad** to (0, 0, 2), and the **Scale** property to (1.28, 0.72, 1).</span></span> <span data-ttu-id="4111e-130">Una volta apportate queste modifiche, il componente **Transform** nel riquadro **Inspector** per il **Quad** sarà simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="4111e-130">After these changes, the **Transform** component on the **Inspector** pane for the **Quad** will look like this:</span></span>

![Trasformazione quad](images/spatial-audio/quad-transform.png)

<span data-ttu-id="4111e-132">Per creare una trama del **Quad** con video, creare una nuova **trama di rendering**.</span><span class="sxs-lookup"><span data-stu-id="4111e-132">To texture the **Quad** with video, create a new **Render Texture**.</span></span> <span data-ttu-id="4111e-133">Nel riquadro **progetto** , fare clic con il pulsante destro del mouse e scegliere **Crea-> trama di rendering**:</span><span class="sxs-lookup"><span data-stu-id="4111e-133">In the **Project** pane, right-click and choose **Create -> Render Texture**:</span></span>

![Crea trama di rendering](images/spatial-audio/create-render-texture.png)

<span data-ttu-id="4111e-135">Nel riquadro **Inspector** della trama di **rendering**impostare la proprietà **size** in modo che corrisponda alla risoluzione nativa del video 1280x720.</span><span class="sxs-lookup"><span data-stu-id="4111e-135">On the **Inspector** pane of the **Render Texture**, set the **Size** property to match the video's native resolution of 1280x720.</span></span> <span data-ttu-id="4111e-136">Quindi, per garantire prestazioni di rendering ottimali in HoloLens 2, impostare la proprietà **depth buffer** su almeno **16 bit di profondità**.</span><span class="sxs-lookup"><span data-stu-id="4111e-136">Then, to ensure good rendering performance on HoloLens 2, set the **Depth Buffer** property to **At least 16 bits depth**.</span></span> <span data-ttu-id="4111e-137">Dopo queste impostazioni, il riquadro **Inspector** per la **trama di rendering** sarà simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="4111e-137">After these settings, the **Inspector** pane for the **Render Texture** will look like this:</span></span>

![Proprietà trama di rendering](images/spatial-audio/render-texture-properties.png)

<span data-ttu-id="4111e-139">Usare quindi la nuova **trama di rendering** come trama per il **Quad**:</span><span class="sxs-lookup"><span data-stu-id="4111e-139">Next, use your new **Render Texture** as the texture for the **Quad**:</span></span>
1. <span data-ttu-id="4111e-140">Trascinare la **trama di rendering** dal riquadro **progetto** al **quadrato** della **gerarchia**</span><span class="sxs-lookup"><span data-stu-id="4111e-140">Drag the **Render Texture** from the **Project** pane onto the **Quad** in the **Hierarchy**</span></span>
2. <span data-ttu-id="4111e-141">Per garantire prestazioni ottimali in HoloLens 2, nel riquadro **Inspector** per il **Quad**selezionare lo **shader standard del Toolkit di realtà mista**.</span><span class="sxs-lookup"><span data-stu-id="4111e-141">To ensure good performance on HoloLens 2, on the **Inspector** pane for the **Quad**, select the **Mixed Reality Toolkit Standard Shader**.</span></span>

<span data-ttu-id="4111e-142">Con queste impostazioni, il componente **trama** nel riquadro **Inspector** per il **Quad** sarà simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="4111e-142">With these settings, the **Texture** component on the **Inspector** pane for the **Quad** will look like this:</span></span>

![Proprietà trama quad](images/spatial-audio/quad-texture-properties.png)

<span data-ttu-id="4111e-144">Per impostare il nuovo **lettore video** e il **rendering della trama** per riprodurre il clip video, aprire il riquadro **Inspector** per il **lettore video** e:</span><span class="sxs-lookup"><span data-stu-id="4111e-144">To set your new **Video Player** and **Render Texture** to play your video clip, open the **Inspector** pane for the **Video Player** and:</span></span>
* <span data-ttu-id="4111e-145">Imposta la proprietà **video clip** sul file video</span><span class="sxs-lookup"><span data-stu-id="4111e-145">Set the **Video Clip** property to your video file</span></span>
* <span data-ttu-id="4111e-146">Casella di controllo **ciclo**</span><span class="sxs-lookup"><span data-stu-id="4111e-146">Check the **Loop** checkbox</span></span>
* <span data-ttu-id="4111e-147">Imposta la **trama di destinazione** sulla nuova trama di rendering</span><span class="sxs-lookup"><span data-stu-id="4111e-147">Set **Target Texture** to your new render texture</span></span>

<span data-ttu-id="4111e-148">Il riquadro **Inspector** per il **lettore video** sarà ora simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="4111e-148">The **Inspector** pane for the **Video Player** will now look like this:</span></span>

![Proprietà lettore video](images/spatial-audio/video-player-properties.png)

## <a name="spatialize-the-audio-from-the-video"></a><span data-ttu-id="4111e-150">Spatialize l'audio dal video</span><span class="sxs-lookup"><span data-stu-id="4111e-150">Spatialize the audio from the video</span></span>
<span data-ttu-id="4111e-151">Nel riquadro **Inspector** per il **Quad**creare un' **origine audio** a cui indirizzare l'audio dal video:</span><span class="sxs-lookup"><span data-stu-id="4111e-151">In the **Inspector** pane for the **Quad**, create an **Audio Source** to which you'll route the audio from the video:</span></span>
* <span data-ttu-id="4111e-152">Fare clic su **Aggiungi componente** nella parte inferiore del riquadro</span><span class="sxs-lookup"><span data-stu-id="4111e-152">Click **Add Component** at the bottom of the pane</span></span>
* <span data-ttu-id="4111e-153">Aggiungere un' **origine audio**</span><span class="sxs-lookup"><span data-stu-id="4111e-153">Add an **Audio Source**</span></span>

<span data-ttu-id="4111e-154">Quindi, nell' **origine audio**:</span><span class="sxs-lookup"><span data-stu-id="4111e-154">Then, on the **Audio Source**:</span></span>
* <span data-ttu-id="4111e-155">Impostare l' **output** sul mixer</span><span class="sxs-lookup"><span data-stu-id="4111e-155">Set **Output** to your mixer</span></span>
* <span data-ttu-id="4111e-156">Controllare la casella **Spatialize**</span><span class="sxs-lookup"><span data-stu-id="4111e-156">Check the **Spatialize** box</span></span>
* <span data-ttu-id="4111e-157">Spostare il dispositivo di scorrimento di **Blend spaziale** su 1 (3D)</span><span class="sxs-lookup"><span data-stu-id="4111e-157">Move the **Spatial Blend** slider to 1 (3D)</span></span>

<span data-ttu-id="4111e-158">Una volta apportate queste modifiche, il componente di **origine audio** nel riquadro **Inspector** per il **Quad** sarà simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="4111e-158">After these changes, the **Audio Source** component on the **Inspector** pane for the **Quad** will look like this:</span></span>

![Controllo origine audio quad](images/spatial-audio/quad-audio-source-inspector.png)

<span data-ttu-id="4111e-160">Per impostare il **lettore video** in modo da instradare l'audio all' **origine audio** sul **Quad**, aprire il riquadro **Inspector** per il **lettore video** e:</span><span class="sxs-lookup"><span data-stu-id="4111e-160">To set the **Video Player** to route its audio to the **Audio Source** on the **Quad**, open the **Inspector** pane for the **Video Player** and:</span></span>
* <span data-ttu-id="4111e-161">Impostare la **modalità di output audio** su' Audio source '</span><span class="sxs-lookup"><span data-stu-id="4111e-161">Set the **Audio Output Mode** to 'Audio Source'</span></span>
* <span data-ttu-id="4111e-162">Impostare la proprietà di **origine audio** sul quad</span><span class="sxs-lookup"><span data-stu-id="4111e-162">Set the **Audio Source** property to your Quad</span></span>

<span data-ttu-id="4111e-163">Dopo queste modifiche, il riquadro **Inspector** per il **lettore video** sarà simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="4111e-163">After these changes, the **Inspector** pane for the **Video Player** will look like this:</span></span>

![Origine audio del set di lettori video](images/spatial-audio/video-player-set-audio-source.png)

## <a name="next-steps"></a><span data-ttu-id="4111e-165">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="4111e-165">Next steps</span></span>
<span data-ttu-id="4111e-166">Provare l'app in un HoloLens 2 o nell'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="4111e-166">Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="4111e-167">Potrai visualizzare e ascoltare il video e l'audio del video sarà spaziali.</span><span class="sxs-lookup"><span data-stu-id="4111e-167">You'll see and hear the video, and the audio from the video will be spatialized.</span></span>

<span data-ttu-id="4111e-168">Continuare con il [capitolo 4](unity-spatial-audio-ch4.md) per usare il pulsante per abilitare e disabilitare la spazializzazione in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="4111e-168">Continue to [Chapter 4](unity-spatial-audio-ch4.md) to use the button to enable and disable spatialization at run time.</span></span>


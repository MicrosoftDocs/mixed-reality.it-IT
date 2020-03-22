---
title: Audio spaziale in Unity
description: Riprodurre un suono spaziale da uno specifico punto 3D nella scena Unity.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Unity, audio spaziale, HRTF, dimensioni della stanza
ms.openlocfilehash: af3f1486c3e931ad93d7b8960d822653ec740c12
ms.sourcegitcommit: ee8c7e821cb337cbccd8af64b13ee5f50109a776
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/21/2020
ms.locfileid: "80082035"
---
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="a8efa-104">Audio spaziale in Unity</span><span class="sxs-lookup"><span data-stu-id="a8efa-104">Spatial sound in Unity</span></span>

<span data-ttu-id="a8efa-105">Questa pagina contiene collegamenti a risorse per il suono spaziale in Unity.</span><span class="sxs-lookup"><span data-stu-id="a8efa-105">This page links to resources for spatial sound in Unity.</span></span>

## <a name="spatializer-options"></a><span data-ttu-id="a8efa-106">Opzioni di Spatializer</span><span class="sxs-lookup"><span data-stu-id="a8efa-106">Spatializer options</span></span>
<span data-ttu-id="a8efa-107">Le opzioni di Spatializer per le applicazioni di realtà mista includono:</span><span class="sxs-lookup"><span data-stu-id="a8efa-107">Spatializer options for mixed reality applications include:</span></span>
* <span data-ttu-id="a8efa-108">*SPATIALIZER HRTF MS*.</span><span class="sxs-lookup"><span data-stu-id="a8efa-108">The *MS HRTF Spatializer*.</span></span> <span data-ttu-id="a8efa-109">Unity fornisce questo elemento come parte del pacchetto facoltativo di *realtà mista di Windows* .</span><span class="sxs-lookup"><span data-stu-id="a8efa-109">Unity provides this as part of the *Windows Mixed Reality* optional package.</span></span>
  * <span data-ttu-id="a8efa-110">Questa operazione viene eseguita sulla CPU in un'architettura a "singola origine" con costi più elevati.</span><span class="sxs-lookup"><span data-stu-id="a8efa-110">This runs on CPU in a higher-cost 'single-source' architecture.</span></span>
  * <span data-ttu-id="a8efa-111">Questa operazione viene fornita per garantire la compatibilità con le versioni precedenti delle applicazioni HoloLens originali.</span><span class="sxs-lookup"><span data-stu-id="a8efa-111">This is provided for backwards compatibility with original HoloLens applications.</span></span>
* <span data-ttu-id="a8efa-112">*Microsoft Spatializer*.</span><span class="sxs-lookup"><span data-stu-id="a8efa-112">The *Microsoft Spatializer*.</span></span> <span data-ttu-id="a8efa-113">Questa operazione è disponibile dal [repository GitHub Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity).</span><span class="sxs-lookup"><span data-stu-id="a8efa-113">This is available from the [Microsoft spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity).</span></span>
  * <span data-ttu-id="a8efa-114">Questa operazione usa un'architettura a più livelli di costo inferiore.</span><span class="sxs-lookup"><span data-stu-id="a8efa-114">This uses a lower-cost 'multi-source' architecture.</span></span>
  * <span data-ttu-id="a8efa-115">In HoloLens 2 questa operazione viene scaricata in un acceleratore hardware.</span><span class="sxs-lookup"><span data-stu-id="a8efa-115">On HoloLens 2, this is offloaded to a hardware accelerator.</span></span>

<span data-ttu-id="a8efa-116">Per le nuove applicazioni, è consigliabile *Microsoft Spatializer*.</span><span class="sxs-lookup"><span data-stu-id="a8efa-116">For new applications, we recommend the *Microsoft Spatializer*.</span></span>

## <a name="enable-spatialization"></a><span data-ttu-id="a8efa-117">Abilita spazializzazione</span><span class="sxs-lookup"><span data-stu-id="a8efa-117">Enable spatialization</span></span>

<span data-ttu-id="a8efa-118">Usare [NuGet per Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) per installare _Microsoft. SpatialAudio. Spatializer. Unity_ e scegliere **Microsoft Spatializer** nelle impostazioni audio del progetto.</span><span class="sxs-lookup"><span data-stu-id="a8efa-118">Use [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) to install _Microsoft.SpatialAudio.Spatializer.Unity_ and choose **Microsoft Spatializer** in your project's audio settings.</span></span> <span data-ttu-id="a8efa-119">Quindi:</span><span class="sxs-lookup"><span data-stu-id="a8efa-119">Then:</span></span>
* <span data-ttu-id="a8efa-120">Alleghi un' **origine audio** a un oggetto nella gerarchia</span><span class="sxs-lookup"><span data-stu-id="a8efa-120">Attach an **Audio Source** to an object in the hierarchy</span></span>
* <span data-ttu-id="a8efa-121">Selezionare la casella di controllo **Abilita spazializzazione**</span><span class="sxs-lookup"><span data-stu-id="a8efa-121">Check the **Enable spatialization** checkbox</span></span>
* <span data-ttu-id="a8efa-122">Spostare il dispositivo di scorrimento di **Blend spaziale** su "1"</span><span class="sxs-lookup"><span data-stu-id="a8efa-122">Move the **Spatial Blend** slider to '1'</span></span>
* <span data-ttu-id="a8efa-123">Verificare che l'audio spaziale sia abilitato nella workstation per sviluppatori.</span><span class="sxs-lookup"><span data-stu-id="a8efa-123">Ensure spatial audio is enabled on your developer workstation.</span></span> <span data-ttu-id="a8efa-124">Per abilitarla, fare clic con il pulsante destro del mouse sull'icona del volume sulla barra delle applicazioni e verificare che l'audio spaziale sia impostato su un valore diverso da "off".</span><span class="sxs-lookup"><span data-stu-id="a8efa-124">Enable it by right-clicking on the volume icon in the task bar and making sure that Spatial Sound is set to something other than "off."</span></span> <span data-ttu-id="a8efa-125">Per ottenere la migliore rappresentazione delle informazioni su HoloLens 2, scegliere **Windows Sonic per le cuffie**.</span><span class="sxs-lookup"><span data-stu-id="a8efa-125">To get the best representation of what you'll hear on HoloLens 2, choose **Windows Sonic for Headphones**.</span></span>

>[!NOTE]
><span data-ttu-id="a8efa-126">Se si verifica un errore in Unity per non poter caricare il plug-in Microsoft. SpatialAudio. Spatializer. Unity, perché una delle relative dipendenze non è presente, verificare che nel PC sia installata la versione più recente di [Microsoft Visual C++ Redistributable](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) .</span><span class="sxs-lookup"><span data-stu-id="a8efa-126">If you get an error in Unity about not being able to load plugin Microsoft.SpatialAudio.Spatializer.Unity because one of its dependencies is missing, check that you have the latest version of the [Microsoft Visual C++ Redistributable](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) installed on your PC.</span></span>

<span data-ttu-id="a8efa-127">Per altri dettagli, vedi:</span><span class="sxs-lookup"><span data-stu-id="a8efa-127">For more details, see:</span></span>
* [<span data-ttu-id="a8efa-128">Repository GitHub Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="a8efa-128">Microsoft spatializer GitHub repository</span></span>](https://github.com/microsoft/spatialaudio-unity)
* [<span data-ttu-id="a8efa-129">Esercitazione di Spatializer di Microsoft</span><span class="sxs-lookup"><span data-stu-id="a8efa-129">Microsoft's spatializer tutorial</span></span>](unity-spatial-audio-ch1.md)
* [<span data-ttu-id="a8efa-130">Documentazione dell'origine audio di Unity</span><span class="sxs-lookup"><span data-stu-id="a8efa-130">Unity's audio source documentation</span></span>](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [<span data-ttu-id="a8efa-131">Documentazione di Unity Spatializer</span><span class="sxs-lookup"><span data-stu-id="a8efa-131">Unity's spatializer documentation</span></span>](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a><span data-ttu-id="a8efa-132">Attenuazione basata sulla distanza</span><span class="sxs-lookup"><span data-stu-id="a8efa-132">Distance-based attenuation</span></span>
<span data-ttu-id="a8efa-133">Il decadimento basato sulla distanza predefinito di Unity ha una distanza minima di 1 metro e una distanza massima di 500 metri, con un attenuazione logaritmico.</span><span class="sxs-lookup"><span data-stu-id="a8efa-133">Unity's default distance-based decay has a minimum distance of 1 meter and a maximum distance of 500 meters, with a logarithmic rolloff.</span></span> <span data-ttu-id="a8efa-134">Queste impostazioni possono essere usate per lo scenario in uso oppure è possibile che le origini siano attenuate troppo rapidamente o troppo lentamente.</span><span class="sxs-lookup"><span data-stu-id="a8efa-134">These settings may work for your scenario, or you may find that sources attenuate too quickly or too slowly.</span></span> <span data-ttu-id="a8efa-135">Per altri dettagli, vedi:</span><span class="sxs-lookup"><span data-stu-id="a8efa-135">For more details, see:</span></span>
* <span data-ttu-id="a8efa-136">[Progettazione audio in realtà mista](spatial-sound-design.md) per le impostazioni consigliate.</span><span class="sxs-lookup"><span data-stu-id="a8efa-136">[Sound design in mixed reality](spatial-sound-design.md) for recommended settings.</span></span>
* <span data-ttu-id="a8efa-137">[Documentazione dell'origine audio di Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) per istruzioni sull'impostazione di queste curve.</span><span class="sxs-lookup"><span data-stu-id="a8efa-137">[Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) for instructions on setting these curves.</span></span>

## <a name="reverb"></a><span data-ttu-id="a8efa-138">Riverbero</span><span class="sxs-lookup"><span data-stu-id="a8efa-138">Reverb</span></span>
<span data-ttu-id="a8efa-139">_Microsoft Spatializer_ Disabilita gli effetti post-Spatializer per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="a8efa-139">The _Microsoft Spatializer_ disables post-spatializer effects by default.</span></span> <span data-ttu-id="a8efa-140">Per abilitare il riverbero e altri effetti per le origini spaziali:</span><span class="sxs-lookup"><span data-stu-id="a8efa-140">To enable reverb and other effects for spatialized sources:</span></span>
* <span data-ttu-id="a8efa-141">Alleghi il componente del **livello di invio dell'effetto chat** a ogni origine</span><span class="sxs-lookup"><span data-stu-id="a8efa-141">Attach the **Room Effect Send Level** component to each source</span></span>
* <span data-ttu-id="a8efa-142">Modificare la curva del livello di invio per ogni origine, per controllare il guadagno sull'audio restituito al grafico per l'elaborazione degli effetti</span><span class="sxs-lookup"><span data-stu-id="a8efa-142">Adjust the send level curve for each source, to control the gain on the audio sent back to the graph for effects processing</span></span>

<span data-ttu-id="a8efa-143">Per informazioni dettagliate, vedere [il capitolo 5 dell'esercitazione su Spatializer](unity-spatial-audio-ch5.md) .</span><span class="sxs-lookup"><span data-stu-id="a8efa-143">See [Chapter 5 of the spatializer tutorial](unity-spatial-audio-ch5.md) for details.</span></span>

## <a name="unity-spatial-sound-examples"></a><span data-ttu-id="a8efa-144">Esempi di suoni spaziali Unity</span><span class="sxs-lookup"><span data-stu-id="a8efa-144">Unity spatial sound examples</span></span>
<span data-ttu-id="a8efa-145">Per esempi di suoni spaziali in Unity, vedere:</span><span class="sxs-lookup"><span data-stu-id="a8efa-145">For examples of spatial sound in Unity, see:</span></span>
* [<span data-ttu-id="a8efa-146">Demo di MRTK</span><span class="sxs-lookup"><span data-stu-id="a8efa-146">MRTK demos</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* <span data-ttu-id="a8efa-147">[Progetto di esempio Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span><span class="sxs-lookup"><span data-stu-id="a8efa-147">The [Microsoft Spatializer sample project](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span></span>

## <a name="next-steps"></a><span data-ttu-id="a8efa-148">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="a8efa-148">Next steps</span></span>
* [<span data-ttu-id="a8efa-149">Progettazione audio in realtà mista</span><span class="sxs-lookup"><span data-stu-id="a8efa-149">Sound design in mixed reality</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="a8efa-150">Esercitazione di Spatializer di Microsoft</span><span class="sxs-lookup"><span data-stu-id="a8efa-150">Microsoft's spatializer tutorial</span></span>](unity-spatial-audio-ch1.md)


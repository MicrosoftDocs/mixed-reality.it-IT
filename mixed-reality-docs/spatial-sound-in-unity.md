---
title: Audio spaziale in Unity
description: Riprodurre un suono spaziale da uno specifico punto 3D nella scena Unity.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Unity, audio spaziale, HRTF, dimensioni della stanza
ms.openlocfilehash: 3e7d0ea231545d5112d182dffbc02f217ca4a4a7
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181991"
---
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="952c4-104">Audio spaziale in Unity</span><span class="sxs-lookup"><span data-stu-id="952c4-104">Spatial sound in Unity</span></span>

<span data-ttu-id="952c4-105">Questa pagina contiene collegamenti a risorse per il suono spaziale in Unity.</span><span class="sxs-lookup"><span data-stu-id="952c4-105">This page links to resources for spatial sound in Unity.</span></span>

## <a name="spatializer-options"></a><span data-ttu-id="952c4-106">Opzioni di Spatializer</span><span class="sxs-lookup"><span data-stu-id="952c4-106">Spatializer options</span></span>
<span data-ttu-id="952c4-107">Le opzioni di Spatializer per le applicazioni di realtà mista includono:</span><span class="sxs-lookup"><span data-stu-id="952c4-107">Spatializer options for mixed reality applications include:</span></span>
* <span data-ttu-id="952c4-108">*SPATIALIZER HRTF MS*.</span><span class="sxs-lookup"><span data-stu-id="952c4-108">The *MS HRTF Spatializer*.</span></span> <span data-ttu-id="952c4-109">Unity fornisce questo elemento come parte del pacchetto facoltativo di *realtà mista di Windows* .</span><span class="sxs-lookup"><span data-stu-id="952c4-109">Unity provides this as part of the *Windows Mixed Reality* optional package.</span></span>
  * <span data-ttu-id="952c4-110">Questa operazione viene eseguita sulla CPU in un'architettura a "singola origine" con costi più elevati.</span><span class="sxs-lookup"><span data-stu-id="952c4-110">This runs on CPU in a higher-cost 'single-source' architecture.</span></span>
  * <span data-ttu-id="952c4-111">Questa operazione viene fornita per garantire la compatibilità con le versioni precedenti delle applicazioni HoloLens originali.</span><span class="sxs-lookup"><span data-stu-id="952c4-111">This is provided for backwards compatibility with original HoloLens applications.</span></span>
* <span data-ttu-id="952c4-112">*Microsoft Spatializer*.</span><span class="sxs-lookup"><span data-stu-id="952c4-112">The *Microsoft Spatializer*.</span></span> <span data-ttu-id="952c4-113">Questa operazione è disponibile dal [repository GitHub Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity).</span><span class="sxs-lookup"><span data-stu-id="952c4-113">This is available from the [Microsoft spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity).</span></span>
  * <span data-ttu-id="952c4-114">Questa operazione usa un'architettura a più livelli di costo inferiore.</span><span class="sxs-lookup"><span data-stu-id="952c4-114">This uses a lower-cost 'multi-source' architecture.</span></span>
  * <span data-ttu-id="952c4-115">In HoloLens 2 questa operazione viene scaricata in un acceleratore hardware.</span><span class="sxs-lookup"><span data-stu-id="952c4-115">On HoloLens 2, this is offloaded to a hardware accelerator.</span></span>

<span data-ttu-id="952c4-116">Per le nuove applicazioni, è consigliabile *Microsoft Spatializer*.</span><span class="sxs-lookup"><span data-stu-id="952c4-116">For new applications, we recommend the *Microsoft Spatializer*.</span></span>

## <a name="enable-spatialization"></a><span data-ttu-id="952c4-117">Abilita spazializzazione</span><span class="sxs-lookup"><span data-stu-id="952c4-117">Enable spatialization</span></span>

<span data-ttu-id="952c4-118">Usare [NuGet per Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) per installare _Microsoft. SpatialAudio. Spatializer. Unity_ e scegliere **Microsoft Spatializer** nelle impostazioni audio del progetto.</span><span class="sxs-lookup"><span data-stu-id="952c4-118">Use [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) to install _Microsoft.SpatialAudio.Spatializer.Unity_ and choose **Microsoft Spatializer** in your project's audio settings.</span></span> <span data-ttu-id="952c4-119">Quindi:</span><span class="sxs-lookup"><span data-stu-id="952c4-119">Then:</span></span>
* <span data-ttu-id="952c4-120">Alleghi un' **origine audio** a un oggetto nella gerarchia</span><span class="sxs-lookup"><span data-stu-id="952c4-120">Attach an **Audio Source** to an object in the hierarchy</span></span>
* <span data-ttu-id="952c4-121">Selezionare la casella di controllo **Abilita spazializzazione**</span><span class="sxs-lookup"><span data-stu-id="952c4-121">Check the **Enable spatialization** checkbox</span></span>
* <span data-ttu-id="952c4-122">Spostare il dispositivo di scorrimento di **Blend spaziale** su "1"</span><span class="sxs-lookup"><span data-stu-id="952c4-122">Move the **Spatial Blend** slider to '1'</span></span>

<span data-ttu-id="952c4-123">Per altri dettagli, vedi:</span><span class="sxs-lookup"><span data-stu-id="952c4-123">For more details, see:</span></span>
* [<span data-ttu-id="952c4-124">Repository GitHub Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="952c4-124">Microsoft spatializer GitHub repository</span></span>](https://github.com/microsoft/spatialaudio-unity)
* [<span data-ttu-id="952c4-125">Esercitazione di Spatializer di Microsoft</span><span class="sxs-lookup"><span data-stu-id="952c4-125">Microsoft's spatializer tutorial</span></span>](unity-spatial-audio-ch1.md)
* [<span data-ttu-id="952c4-126">Documentazione dell'origine audio di Unity</span><span class="sxs-lookup"><span data-stu-id="952c4-126">Unity's audio source documentation</span></span>](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [<span data-ttu-id="952c4-127">Documentazione di Unity Spatializer</span><span class="sxs-lookup"><span data-stu-id="952c4-127">Unity's spatializer documentation</span></span>](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a><span data-ttu-id="952c4-128">Attenuazione basate sulla distanza</span><span class="sxs-lookup"><span data-stu-id="952c4-128">Distance-based attenuation</span></span>
<span data-ttu-id="952c4-129">Il decadimento basato sulla distanza predefinito di Unity ha una distanza minima di 1 metro e una distanza massima di 500 metri, con un attenuazione logaritmico.</span><span class="sxs-lookup"><span data-stu-id="952c4-129">Unity's default distance-based decay has a minimum distance of 1 meter and a maximum distance of 500 meters, with a logarithmic rolloff.</span></span> <span data-ttu-id="952c4-130">Queste impostazioni possono essere usate per lo scenario in uso oppure è possibile che le origini siano attenuate troppo rapidamente o troppo lentamente.</span><span class="sxs-lookup"><span data-stu-id="952c4-130">These settings may work for your scenario, or you may find that sources attenuate too quickly or too slowly.</span></span> <span data-ttu-id="952c4-131">Per altri dettagli, vedi:</span><span class="sxs-lookup"><span data-stu-id="952c4-131">For more details, see:</span></span>
* <span data-ttu-id="952c4-132">[Progettazione audio in realtà mista](spatial-sound-design.md) per le impostazioni consigliate.</span><span class="sxs-lookup"><span data-stu-id="952c4-132">[Sound design in mixed reality](spatial-sound-design.md) for recommended settings.</span></span>
* <span data-ttu-id="952c4-133">[Documentazione dell'origine audio di Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) per istruzioni sull'impostazione di queste curve.</span><span class="sxs-lookup"><span data-stu-id="952c4-133">[Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) for instructions on setting these curves.</span></span>

## <a name="reverb"></a><span data-ttu-id="952c4-134">Riverbero</span><span class="sxs-lookup"><span data-stu-id="952c4-134">Reverb</span></span>
<span data-ttu-id="952c4-135">_Microsoft Spatializer_ Disabilita gli effetti post-Spatializer per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="952c4-135">The _Microsoft Spatializer_ disables post-spatializer effects by default.</span></span> <span data-ttu-id="952c4-136">Per abilitare il riverbero e altri effetti per le origini spaziali:</span><span class="sxs-lookup"><span data-stu-id="952c4-136">To enable reverb and other effects for spatialized sources:</span></span>
* <span data-ttu-id="952c4-137">Alleghi il componente del **livello di invio dell'effetto chat** a ogni origine</span><span class="sxs-lookup"><span data-stu-id="952c4-137">Attach the **Room Effect Send Level** component to each source</span></span>
* <span data-ttu-id="952c4-138">Modificare la curva del livello di invio per ogni origine, per controllare il guadagno sull'audio restituito al grafico per l'elaborazione degli effetti</span><span class="sxs-lookup"><span data-stu-id="952c4-138">Adjust the send level curve for each source, to control the gain on the audio sent back to the graph for effects processing</span></span>

<span data-ttu-id="952c4-139">Per informazioni dettagliate, vedere [il capitolo 5 dell'esercitazione su Spatializer](unity-spatial-audio-ch5.md) .</span><span class="sxs-lookup"><span data-stu-id="952c4-139">See [Chapter 5 of the spatializer tutorial](unity-spatial-audio-ch5.md) for details.</span></span>

## <a name="unity-spatial-sound-examples"></a><span data-ttu-id="952c4-140">Esempi di suoni spaziali Unity</span><span class="sxs-lookup"><span data-stu-id="952c4-140">Unity spatial sound examples</span></span>
<span data-ttu-id="952c4-141">Per esempi di suoni spaziali in Unity, vedere:</span><span class="sxs-lookup"><span data-stu-id="952c4-141">For examples of spatial sound in Unity, see:</span></span>
* [<span data-ttu-id="952c4-142">Demo di MRTK</span><span class="sxs-lookup"><span data-stu-id="952c4-142">MRTK demos</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* <span data-ttu-id="952c4-143">[Progetto di esempio Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span><span class="sxs-lookup"><span data-stu-id="952c4-143">The [Microsoft Spatializer sample project](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span></span>

## <a name="next-steps"></a><span data-ttu-id="952c4-144">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="952c4-144">Next steps</span></span>
* [<span data-ttu-id="952c4-145">Progettazione audio in realtà mista</span><span class="sxs-lookup"><span data-stu-id="952c4-145">Sound design in mixed reality</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="952c4-146">Esercitazione di Spatializer di Microsoft</span><span class="sxs-lookup"><span data-stu-id="952c4-146">Microsoft's spatializer tutorial</span></span>](unity-spatial-audio-ch1.md)


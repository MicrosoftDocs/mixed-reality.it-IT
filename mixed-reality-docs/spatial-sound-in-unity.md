---
title: Audio spaziale in Unity
description: Riproduzione di un suono spaziale che deriva da uno specifico punto 3D nella scena Unity.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, audio spaziale, HRTF, dimensioni della stanza
ms.openlocfilehash: e2b321d7086314a14a940d57aa17e67636c758b8
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63549091"
---
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="0cc3f-104">Audio spaziale in Unity</span><span class="sxs-lookup"><span data-stu-id="0cc3f-104">Spatial sound in Unity</span></span>

<span data-ttu-id="0cc3f-105">Questo argomento descrive come usare il suono spaziale nei progetti Unity.</span><span class="sxs-lookup"><span data-stu-id="0cc3f-105">This topic describes how to use Spatial Sound in your Unity projects.</span></span> <span data-ttu-id="0cc3f-106">Vengono illustrati i file del plug-in necessari, nonché i componenti e le proprietà Unity che consentono il suono spaziale.</span><span class="sxs-lookup"><span data-stu-id="0cc3f-106">It covers the required plugin files as well as the Unity components and properties that enable Spatial Sound.</span></span>

## <a name="enabling-spatial-sound-in-unity"></a><span data-ttu-id="0cc3f-107">Abilitazione del suono spaziale in Unity</span><span class="sxs-lookup"><span data-stu-id="0cc3f-107">Enabling Spatial Sound in Unity</span></span>

<span data-ttu-id="0cc3f-108">Il suono spaziale, in Unity, viene abilitato con un plug-in Spatializer audio.</span><span class="sxs-lookup"><span data-stu-id="0cc3f-108">Spatial Sound, in Unity, is enabled using an audio spatializer plugin.</span></span> <span data-ttu-id="0cc3f-109">I file del plug-in vengono aggregati direttamente in Unity, quindi l'abilitazione del suono spaziale è semplice come **modificare > impostazioni del progetto > audio** e modificare il plug-in **Spatializer** nel controllo in **MS HRTF Spatializer**.</span><span class="sxs-lookup"><span data-stu-id="0cc3f-109">The plugin files are bundled directly into Unity so enabling spatial sound is as easy as going to **Edit > Project Settings > Audio** and changing the **Spatializer Plugin** in the Inspector to the **MS HRTF Spatializer**.</span></span> <span data-ttu-id="0cc3f-110">Poiché Microsoft Spatializer supporta solo 48000Hz attualmente, è necessario impostare anche la frequenza di campionamento del sistema su 48000 per impedire un errore di HRTF nel caso raro in cui il dispositivo di output del sistema non sia già impostato su 48000:</span><span class="sxs-lookup"><span data-stu-id="0cc3f-110">Since the Microsoft spatializer only supports 48000Hz currently, you should also set your System Sample Rate to 48000 to prevent an HRTF failure in the rare case that your system output device is not set to 48000 already:</span></span>

<span data-ttu-id="0cc3f-111">![Inspector per AudioManager](images/audio-250px.png)</span><span class="sxs-lookup"><span data-stu-id="0cc3f-111">![Inspector for AudioManager](images/audio-250px.png)</span></span><br>
<span data-ttu-id="0cc3f-112">*Inspector per AudioManager*</span><span class="sxs-lookup"><span data-stu-id="0cc3f-112">*Inspector for AudioManager*</span></span>

<span data-ttu-id="0cc3f-113">Il progetto Unity è ora configurato per l'uso di un suono spaziale.</span><span class="sxs-lookup"><span data-stu-id="0cc3f-113">Your Unity project is now configured to use Spatial Sound.</span></span>

>[!NOTE]
><span data-ttu-id="0cc3f-114">Se non si usa un PC Windows 10 per lo sviluppo, non si otterrà un suono spaziale nell'editor né nel dispositivo (anche se si usa Windows 10 SDK).</span><span class="sxs-lookup"><span data-stu-id="0cc3f-114">If you aren't using a Windows 10 PC for development, you won't get Spatial Sound in the editor nor on the device (even if you're using the Windows 10 SDK).</span></span>

## <a name="using-spatial-sound-in-unity"></a><span data-ttu-id="0cc3f-115">Uso del suono spaziale in Unity</span><span class="sxs-lookup"><span data-stu-id="0cc3f-115">Using Spatial Sound in Unity</span></span>

<span data-ttu-id="0cc3f-116">Il suono spaziale viene usato nel progetto Unity regolando tre impostazioni sui componenti di origine audio.</span><span class="sxs-lookup"><span data-stu-id="0cc3f-116">Spatial Sound is used in your Unity project by adjusting three settings on your Audio Source components.</span></span> <span data-ttu-id="0cc3f-117">La procedura seguente consente di configurare i componenti di origine audio per il suono spaziale.</span><span class="sxs-lookup"><span data-stu-id="0cc3f-117">The following steps will configure your Audio Source components for Spatial Sound.</span></span>
* <span data-ttu-id="0cc3f-118">Nel pannello **gerarchia** selezionare l'oggetto Game con un' **origine audio**collegata.</span><span class="sxs-lookup"><span data-stu-id="0cc3f-118">In the **Hierarchy** panel, select the game object that has an attached **Audio Source**.</span></span>
* <span data-ttu-id="0cc3f-119">Nel pannello **Inspector** , sotto il componente **Audio source**</span><span class="sxs-lookup"><span data-stu-id="0cc3f-119">In the **Inspector** panel, under the **Audio Source** component</span></span>
    * <span data-ttu-id="0cc3f-120">Selezionare l'opzione **Spatialize** .</span><span class="sxs-lookup"><span data-stu-id="0cc3f-120">Check the **Spatialize** option.</span></span>
    * <span data-ttu-id="0cc3f-121">Imposta **Spatial Blend** su **3D** (valore numerico 1).</span><span class="sxs-lookup"><span data-stu-id="0cc3f-121">Set **Spatial Blend** to **3D** (numeric value 1).</span></span>
    * <span data-ttu-id="0cc3f-122">Per ottenere risultati ottimali, espandere **impostazioni audio 3D** e impostare **volume attenuazione** su **Custom attenuazione**.</span><span class="sxs-lookup"><span data-stu-id="0cc3f-122">For best results, expand **3D Sound Settings** and set **Volume Rolloff** to **Custom Rolloff**.</span></span>

<span data-ttu-id="0cc3f-123">![Pannello Inspector in Unity che mostra l'origine audio](images/audiosource.png)</span><span class="sxs-lookup"><span data-stu-id="0cc3f-123">![Inspector panel in Unity showing the Audio Source](images/audiosource.png)</span></span><br>
<span data-ttu-id="0cc3f-124">*Pannello Inspector in Unity che mostra l'origine audio*</span><span class="sxs-lookup"><span data-stu-id="0cc3f-124">*Inspector panel in Unity showing the Audio Source*</span></span>

<span data-ttu-id="0cc3f-125">I suoni sono ora realisticamente disponibili nell'ambiente del progetto.</span><span class="sxs-lookup"><span data-stu-id="0cc3f-125">Your sounds now realistically exist inside your project's environment!</span></span>

<span data-ttu-id="0cc3f-126">Si consiglia vivamente di acquisire familiarità con le [linee guida per la progettazione di suoni spaziali](spatial-sound-design.md).</span><span class="sxs-lookup"><span data-stu-id="0cc3f-126">It is strongly recommended that you become familiar with the [Spatial Sound design guidelines](spatial-sound-design.md).</span></span> <span data-ttu-id="0cc3f-127">Queste linee guida consentono di integrare facilmente l'audio nel progetto e di immergere ulteriormente gli utenti nell'esperienza creata.</span><span class="sxs-lookup"><span data-stu-id="0cc3f-127">These guidelines help to integrate your audio seamlessly into your project and to further immerse your users into the experience you have created.</span></span>

## <a name="setting-spatial-sound-settings"></a><span data-ttu-id="0cc3f-128">Impostazione delle impostazioni del suono spaziale</span><span class="sxs-lookup"><span data-stu-id="0cc3f-128">Setting Spatial Sound Settings</span></span>

<span data-ttu-id="0cc3f-129">Il plug-in Microsoft spatial audio fornisce un parametro aggiuntivo che può essere impostato, in base all'origine audio, per consentire un controllo aggiuntivo della simulazione audio.</span><span class="sxs-lookup"><span data-stu-id="0cc3f-129">The Microsoft Spatial Sound plugin provides an additional parameter that can be set, on a per Audio Source basis, to allow additional control of the audio simulation.</span></span> <span data-ttu-id="0cc3f-130">Questo parametro corrisponde alla dimensione della stanza simulata.</span><span class="sxs-lookup"><span data-stu-id="0cc3f-130">This parameter is the size of the simulated room.</span></span>

### <a name="room-size"></a><span data-ttu-id="0cc3f-131">Dimensioni chat room</span><span class="sxs-lookup"><span data-stu-id="0cc3f-131">Room Size</span></span>

<span data-ttu-id="0cc3f-132">Dimensioni della stanza simulata dal suono spaziale.</span><span class="sxs-lookup"><span data-stu-id="0cc3f-132">The size of room that is being simulated by Spatial Sound.</span></span> <span data-ttu-id="0cc3f-133">Le dimensioni approssimative delle chat sono; piccolo (un ufficio per una piccola sala riunioni), media (una sala riunioni di grandi dimensioni) e grandi (Auditorium).</span><span class="sxs-lookup"><span data-stu-id="0cc3f-133">The approximate sizes of the rooms are; small (an office to a small conference room), medium (a large conference room) and large (an auditorium).</span></span> <span data-ttu-id="0cc3f-134">È anche possibile specificare una dimensione della stanza di None per simulare un ambiente esterno.</span><span class="sxs-lookup"><span data-stu-id="0cc3f-134">You can also specify a room size of none to simulate an outdoor environment.</span></span> <span data-ttu-id="0cc3f-135">La dimensione della stanza predefinita è piccola.</span><span class="sxs-lookup"><span data-stu-id="0cc3f-135">The default room size is small.</span></span>

### <a name="example"></a><span data-ttu-id="0cc3f-136">Esempio</span><span class="sxs-lookup"><span data-stu-id="0cc3f-136">Example</span></span>

<span data-ttu-id="0cc3f-137">MixedRealityToolkit per Unity fornisce una classe statica che rende più semplice l'impostazione delle impostazioni audio spaziali.</span><span class="sxs-lookup"><span data-stu-id="0cc3f-137">The MixedRealityToolkit for Unity provides a static class that makes setting the Spatial Sound settings easy.</span></span> <span data-ttu-id="0cc3f-138">Questa classe si trova nella [cartella MixedRealityToolkit\SpatialSound](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound) e può essere chiamata da qualsiasi script nel progetto.</span><span class="sxs-lookup"><span data-stu-id="0cc3f-138">This class can be found in the [MixedRealityToolkit\SpatialSound folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound) and can be called from any script in your project.</span></span> <span data-ttu-id="0cc3f-139">Si consiglia di impostare questi parametri in ogni componente di origine audio nel progetto.</span><span class="sxs-lookup"><span data-stu-id="0cc3f-139">It is recommended that you set these parameters on each Audio Source component in your project.</span></span> <span data-ttu-id="0cc3f-140">Nell'esempio seguente viene illustrata la selezione della dimensione media della stanza per un'origine audio collegata.</span><span class="sxs-lookup"><span data-stu-id="0cc3f-140">The following example shows selecting the medium room size for an attached Audio Source.</span></span>

```cs
AudioSource audioSource = gameObject.GetComponent<AudioSource>()

if (audioSource != null) {
    SpatialSoundSettings.SetRoomSize(audioSource, SpatialMappingRoomSizes.Medium);
}
```

### <a name="directly-accessing-parameters-from-unity"></a><span data-ttu-id="0cc3f-141">Accesso diretto ai parametri da Unity</span><span class="sxs-lookup"><span data-stu-id="0cc3f-141">Directly Accessing Parameters from Unity</span></span>

<span data-ttu-id="0cc3f-142">Se non si vuole usare gli strumenti audio eccellenti in MixedRealityToolkit, di seguito viene illustrato come modificare i parametri di HRTF.</span><span class="sxs-lookup"><span data-stu-id="0cc3f-142">If you don't want to use the excellent Audio tools in the MixedRealityToolkit, here is how you would change HRTF Parameters.</span></span> <span data-ttu-id="0cc3f-143">È possibile copiarlo e incollarlo in uno script denominato *SetHRTF.cs* che si vuole alleghi a ogni HRTF audiosource.</span><span class="sxs-lookup"><span data-stu-id="0cc3f-143">You can copy/paste this into a script called *SetHRTF.cs* that you will want to attach to every HRTF AudioSource.</span></span> <span data-ttu-id="0cc3f-144">Consente di modificare i parametri importanti per HRTF.</span><span class="sxs-lookup"><span data-stu-id="0cc3f-144">It lets you change parameters important to HRTF.</span></span>

```cs
using UnityEngine;
   using System.Collections;
   public class SetHRTF : MonoBehaviour    {
       public enum ROOMSIZE { Small, Medium, Large, None };
       public ROOMSIZE room = ROOMSIZE.Small;  // Small is regarded as the "most average"
       // defaults and docs from MSDN
       // https://msdn.microsoft.com/library/windows/desktop/mt186602(v=vs.85).aspx
       AudioSource audiosource;
       void Awake()
       {
           audiosource = this.gameObject.GetComponent<AudioSource>();
           if (audiosource == null)
           {
               print("SetHRTFParams needs an audio source to do anything.");
               return;
           }
           audiosource.spatialize = 1; // we DO want spatialized audio
           audiosource.spread = 0; // we dont want to reduce our angle of hearing
           audiosource.spatialBlend = 1;   // we do want to hear spatialized audio
           audiosource.SetSpatializerFloat(1, (float)room);    // 1 is the roomsize param
       }
   }
```
### <a name="spatial-sound-in-mixed-reality-toolkit"></a><span data-ttu-id="0cc3f-145">Audio spaziale nel Toolkit per realtà mista</span><span class="sxs-lookup"><span data-stu-id="0cc3f-145">Spatial Sound in Mixed Reality Toolkit</span></span>
- [<span data-ttu-id="0cc3f-146">HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest. Unity</span><span class="sxs-lookup"><span data-stu-id="0cc3f-146">HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity)

<span data-ttu-id="0cc3f-147">Gli esempi seguenti del Toolkit per la realtà mista sono esempi generali di effetti audio che illustrano come rendere le proprie esperienze più immersive usando un suono.</span><span class="sxs-lookup"><span data-stu-id="0cc3f-147">The following examples from the Mixed Reality Toolkit are general audio effect examples that demonstrate ways to make your experiences more immersive by using sound.</span></span>
- [<span data-ttu-id="0cc3f-148">HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest. Unity</span><span class="sxs-lookup"><span data-stu-id="0cc3f-148">HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity)
- [<span data-ttu-id="0cc3f-149">HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest. Unity</span><span class="sxs-lookup"><span data-stu-id="0cc3f-149">HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity)

## <a name="see-also"></a><span data-ttu-id="0cc3f-150">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0cc3f-150">See also</span></span>
* [<span data-ttu-id="0cc3f-151">Audio spaziale</span><span class="sxs-lookup"><span data-stu-id="0cc3f-151">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="0cc3f-152">Progettazione dell'audio spaziale</span><span class="sxs-lookup"><span data-stu-id="0cc3f-152">Spatial sound design</span></span>](spatial-sound-design.md)

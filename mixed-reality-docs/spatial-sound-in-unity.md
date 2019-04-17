---
title: Audio spaziale in Unity
description: La riproduzione di audio spaziale che provengono da un punto 3D specifico all'interno della scena Unity.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, spaziale audio, HRTF, le dimensioni di chat room
ms.openlocfilehash: e2b321d7086314a14a940d57aa17e67636c758b8
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597513"
---
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="7bee5-104">Audio spaziale in Unity</span><span class="sxs-lookup"><span data-stu-id="7bee5-104">Spatial sound in Unity</span></span>

<span data-ttu-id="7bee5-105">In questo argomento viene descritto come usare un suono spaziale nei progetti di Unity.</span><span class="sxs-lookup"><span data-stu-id="7bee5-105">This topic describes how to use Spatial Sound in your Unity projects.</span></span> <span data-ttu-id="7bee5-106">Viene descritto come i file di plug-in obbligatorio, nonché i componenti di Unity e proprietà che consentono il suono spaziale.</span><span class="sxs-lookup"><span data-stu-id="7bee5-106">It covers the required plugin files as well as the Unity components and properties that enable Spatial Sound.</span></span>

## <a name="enabling-spatial-sound-in-unity"></a><span data-ttu-id="7bee5-107">Abilitare l'audio spaziale in Unity</span><span class="sxs-lookup"><span data-stu-id="7bee5-107">Enabling Spatial Sound in Unity</span></span>

<span data-ttu-id="7bee5-108">Spaziale suono, in Unity, viene abilitata tramite un plug-in spaziale audio.</span><span class="sxs-lookup"><span data-stu-id="7bee5-108">Spatial Sound, in Unity, is enabled using an audio spatializer plugin.</span></span> <span data-ttu-id="7bee5-109">I file di plug-in sono inclusi direttamente in Unity in modo che l'abilitazione di suono spaziale è semplice quanto dovrà **Modifica > impostazioni del progetto > Audio** e modificando il **spaziale plug-in** del controllo per il  **MS HRTF spaziale**.</span><span class="sxs-lookup"><span data-stu-id="7bee5-109">The plugin files are bundled directly into Unity so enabling spatial sound is as easy as going to **Edit > Project Settings > Audio** and changing the **Spatializer Plugin** in the Inspector to the **MS HRTF Spatializer**.</span></span> <span data-ttu-id="7bee5-110">Poiché attualmente lo spaziale Microsoft supporta solo 48000Hz, è necessario impostare anche la frequenza di campionamento di sistema per 48000 per evitare un errore HRTF nel raro caso che il dispositivo di output di sistema non è impostato su 48000 già:</span><span class="sxs-lookup"><span data-stu-id="7bee5-110">Since the Microsoft spatializer only supports 48000Hz currently, you should also set your System Sample Rate to 48000 to prevent an HRTF failure in the rare case that your system output device is not set to 48000 already:</span></span>

<span data-ttu-id="7bee5-111">![Controllo per AudioManager](images/audio-250px.png)</span><span class="sxs-lookup"><span data-stu-id="7bee5-111">![Inspector for AudioManager](images/audio-250px.png)</span></span><br>
<span data-ttu-id="7bee5-112">*Controllo per AudioManager*</span><span class="sxs-lookup"><span data-stu-id="7bee5-112">*Inspector for AudioManager*</span></span>

<span data-ttu-id="7bee5-113">Il progetto Unity è ora configurato per usare un suono spaziale.</span><span class="sxs-lookup"><span data-stu-id="7bee5-113">Your Unity project is now configured to use Spatial Sound.</span></span>

>[!NOTE]
><span data-ttu-id="7bee5-114">Se non si usa un PC Windows 10 per lo sviluppo, si otterranno suono spaziale nell'editor, né sul dispositivo (anche se si usa Windows 10 SDK).</span><span class="sxs-lookup"><span data-stu-id="7bee5-114">If you aren't using a Windows 10 PC for development, you won't get Spatial Sound in the editor nor on the device (even if you're using the Windows 10 SDK).</span></span>

## <a name="using-spatial-sound-in-unity"></a><span data-ttu-id="7bee5-115">Uso di suono spaziale in Unity</span><span class="sxs-lookup"><span data-stu-id="7bee5-115">Using Spatial Sound in Unity</span></span>

<span data-ttu-id="7bee5-116">Spaziale suono viene utilizzato nel progetto Unity regolando tre impostazioni sui componenti di origine Audio.</span><span class="sxs-lookup"><span data-stu-id="7bee5-116">Spatial Sound is used in your Unity project by adjusting three settings on your Audio Source components.</span></span> <span data-ttu-id="7bee5-117">La procedura seguente configurerà i componenti di origine Audio per un suono spaziale.</span><span class="sxs-lookup"><span data-stu-id="7bee5-117">The following steps will configure your Audio Source components for Spatial Sound.</span></span>
* <span data-ttu-id="7bee5-118">Nel **gerarchia** panel, selezionare l'oggetto gioco che dispone di un oggetto associato **origine Audio**.</span><span class="sxs-lookup"><span data-stu-id="7bee5-118">In the **Hierarchy** panel, select the game object that has an attached **Audio Source**.</span></span>
* <span data-ttu-id="7bee5-119">Nel **Inspector** nel Pannello di **origine Audio** componente</span><span class="sxs-lookup"><span data-stu-id="7bee5-119">In the **Inspector** panel, under the **Audio Source** component</span></span>
    * <span data-ttu-id="7bee5-120">Verificare i **Spatialize** opzione.</span><span class="sxs-lookup"><span data-stu-id="7bee5-120">Check the **Spatialize** option.</span></span>
    * <span data-ttu-id="7bee5-121">Impostare **Blend spaziali** al **3D** (valore numerico 1).</span><span class="sxs-lookup"><span data-stu-id="7bee5-121">Set **Spatial Blend** to **3D** (numeric value 1).</span></span>
    * <span data-ttu-id="7bee5-122">Per ottenere risultati ottimali, espandere **3D impostazioni audio** e impostare **attenuazione Volume** al **Custom attenuazione**.</span><span class="sxs-lookup"><span data-stu-id="7bee5-122">For best results, expand **3D Sound Settings** and set **Volume Rolloff** to **Custom Rolloff**.</span></span>

<span data-ttu-id="7bee5-123">![Pannello di controllo in Unity che riproduce l'Audio di origine](images/audiosource.png)</span><span class="sxs-lookup"><span data-stu-id="7bee5-123">![Inspector panel in Unity showing the Audio Source](images/audiosource.png)</span></span><br>
<span data-ttu-id="7bee5-124">*Pannello di controllo in Unity che riproduce l'Audio di origine*</span><span class="sxs-lookup"><span data-stu-id="7bee5-124">*Inspector panel in Unity showing the Audio Source*</span></span>

<span data-ttu-id="7bee5-125">I suoni ora realisticamente esistono all'interno di ambiente del progetto.</span><span class="sxs-lookup"><span data-stu-id="7bee5-125">Your sounds now realistically exist inside your project's environment!</span></span>

<span data-ttu-id="7bee5-126">È consigliabile acquisire familiarità con le [linee guida di progettazione suono spaziale](spatial-sound-design.md).</span><span class="sxs-lookup"><span data-stu-id="7bee5-126">It is strongly recommended that you become familiar with the [Spatial Sound design guidelines](spatial-sound-design.md).</span></span> <span data-ttu-id="7bee5-127">Queste linee guida per integrarsi perfettamente l'audio nel progetto e per un'ulteriore immersion sugli utenti nell'esperienza che è stato creato.</span><span class="sxs-lookup"><span data-stu-id="7bee5-127">These guidelines help to integrate your audio seamlessly into your project and to further immerse your users into the experience you have created.</span></span>

## <a name="setting-spatial-sound-settings"></a><span data-ttu-id="7bee5-128">Configurazione delle impostazioni di audio spaziali</span><span class="sxs-lookup"><span data-stu-id="7bee5-128">Setting Spatial Sound Settings</span></span>

<span data-ttu-id="7bee5-129">Il plug-in Microsoft Spatial Sound fornisce un parametro aggiuntivo che è possibile impostare, d'una per ogni singola origine Audio, per consentire un maggiore controllo della simulazione audio.</span><span class="sxs-lookup"><span data-stu-id="7bee5-129">The Microsoft Spatial Sound plugin provides an additional parameter that can be set, on a per Audio Source basis, to allow additional control of the audio simulation.</span></span> <span data-ttu-id="7bee5-130">Questo parametro è la dimensione della chat room simulata.</span><span class="sxs-lookup"><span data-stu-id="7bee5-130">This parameter is the size of the simulated room.</span></span>

### <a name="room-size"></a><span data-ttu-id="7bee5-131">Dimensioni di chat room</span><span class="sxs-lookup"><span data-stu-id="7bee5-131">Room Size</span></span>

<span data-ttu-id="7bee5-132">Le dimensioni della stanza che viene viene simulata dal suono spaziale.</span><span class="sxs-lookup"><span data-stu-id="7bee5-132">The size of room that is being simulated by Spatial Sound.</span></span> <span data-ttu-id="7bee5-133">Le dimensioni approssimative delle sale sono; Small (un ufficio in una sala conferenze small), medie (una grande sala riunioni) o di grandi dimensioni (una magna).</span><span class="sxs-lookup"><span data-stu-id="7bee5-133">The approximate sizes of the rooms are; small (an office to a small conference room), medium (a large conference room) and large (an auditorium).</span></span> <span data-ttu-id="7bee5-134">È anche possibile specificare una dimensione di chat room di none per simulare un ambiente esterno.</span><span class="sxs-lookup"><span data-stu-id="7bee5-134">You can also specify a room size of none to simulate an outdoor environment.</span></span> <span data-ttu-id="7bee5-135">Le dimensioni di spazio predefinite sono piccola.</span><span class="sxs-lookup"><span data-stu-id="7bee5-135">The default room size is small.</span></span>

### <a name="example"></a><span data-ttu-id="7bee5-136">Esempio</span><span class="sxs-lookup"><span data-stu-id="7bee5-136">Example</span></span>

<span data-ttu-id="7bee5-137">Il MixedRealityToolkit per Unity offre una classe statica che rende semplice, impostare le opzioni di segnale acustico spaziale.</span><span class="sxs-lookup"><span data-stu-id="7bee5-137">The MixedRealityToolkit for Unity provides a static class that makes setting the Spatial Sound settings easy.</span></span> <span data-ttu-id="7bee5-138">Questa classe è reperibile nella [MixedRealityToolkit\SpatialSound cartella](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound) e può essere chiamata da qualsiasi script nel progetto.</span><span class="sxs-lookup"><span data-stu-id="7bee5-138">This class can be found in the [MixedRealityToolkit\SpatialSound folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound) and can be called from any script in your project.</span></span> <span data-ttu-id="7bee5-139">È consigliabile impostare questi parametri per ogni componente di origine Audio nel progetto.</span><span class="sxs-lookup"><span data-stu-id="7bee5-139">It is recommended that you set these parameters on each Audio Source component in your project.</span></span> <span data-ttu-id="7bee5-140">Nell'esempio seguente viene illustrato come selezionare le dimensioni medie chat room per un'origine Audio collegata.</span><span class="sxs-lookup"><span data-stu-id="7bee5-140">The following example shows selecting the medium room size for an attached Audio Source.</span></span>

```cs
AudioSource audioSource = gameObject.GetComponent<AudioSource>()

if (audioSource != null) {
    SpatialSoundSettings.SetRoomSize(audioSource, SpatialMappingRoomSizes.Medium);
}
```

### <a name="directly-accessing-parameters-from-unity"></a><span data-ttu-id="7bee5-141">Accesso direttamente ai parametri di Unity</span><span class="sxs-lookup"><span data-stu-id="7bee5-141">Directly Accessing Parameters from Unity</span></span>

<span data-ttu-id="7bee5-142">Se non si desidera utilizzare gli strumenti di Audio eccellente di MixedRealityToolkit, ecco come verrà modificata HRTF parametri.</span><span class="sxs-lookup"><span data-stu-id="7bee5-142">If you don't want to use the excellent Audio tools in the MixedRealityToolkit, here is how you would change HRTF Parameters.</span></span> <span data-ttu-id="7bee5-143">È possibile copiare e incollare questo in uno script chiamato *SetHRTF.cs* che vuoi collegare a ogni AudioSource HRTF.</span><span class="sxs-lookup"><span data-stu-id="7bee5-143">You can copy/paste this into a script called *SetHRTF.cs* that you will want to attach to every HRTF AudioSource.</span></span> <span data-ttu-id="7bee5-144">Consente di modificare i parametri importanti per HRTF.</span><span class="sxs-lookup"><span data-stu-id="7bee5-144">It lets you change parameters important to HRTF.</span></span>

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
### <a name="spatial-sound-in-mixed-reality-toolkit"></a><span data-ttu-id="7bee5-145">Spaziale audio nel Toolkit di realtà mista</span><span class="sxs-lookup"><span data-stu-id="7bee5-145">Spatial Sound in Mixed Reality Toolkit</span></span>
- [<span data-ttu-id="7bee5-146">HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity</span><span class="sxs-lookup"><span data-stu-id="7bee5-146">HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity)

<span data-ttu-id="7bee5-147">Gli esempi seguenti dal Toolkit di realtà mista sono esempi di effetti audio generali che illustrano i modi per rendere le proprie esperienze più coinvolgenti con file audio.</span><span class="sxs-lookup"><span data-stu-id="7bee5-147">The following examples from the Mixed Reality Toolkit are general audio effect examples that demonstrate ways to make your experiences more immersive by using sound.</span></span>
- [<span data-ttu-id="7bee5-148">HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity</span><span class="sxs-lookup"><span data-stu-id="7bee5-148">HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity)
- [<span data-ttu-id="7bee5-149">HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity</span><span class="sxs-lookup"><span data-stu-id="7bee5-149">HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity)

## <a name="see-also"></a><span data-ttu-id="7bee5-150">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7bee5-150">See also</span></span>
* [<span data-ttu-id="7bee5-151">Spaziale audio</span><span class="sxs-lookup"><span data-stu-id="7bee5-151">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="7bee5-152">Progettazione spaziale</span><span class="sxs-lookup"><span data-stu-id="7bee5-152">Spatial sound design</span></span>](spatial-sound-design.md)

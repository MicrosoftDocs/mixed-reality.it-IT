---
title: Esercitazioni audio spaziali-5. Uso di Reverb per aggiungere distanza all'audio spaziale
description: Aggiungere un effetto di riverbero per migliorare il senso della variazione della distanza nell'audio spaziale.
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: realtà mista, Unity, esercitazione, hololens2, audio spaziale
ms.openlocfilehash: abe78417dc231e6228d1942e03418ba699bc0938
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182738"
---
# <a name="using-reverb-to-add-distance-to-spatial-audio"></a><span data-ttu-id="04fbe-105">Uso di Reverb per aggiungere distanza all'audio spaziale</span><span class="sxs-lookup"><span data-stu-id="04fbe-105">Using reverb to add distance to spatial audio</span></span>

## <a name="objectives"></a><span data-ttu-id="04fbe-106">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="04fbe-106">Objectives</span></span>
<span data-ttu-id="04fbe-107">Nei capitoli precedenti è stata aggiunta la spazializzazione ai suoni per dare loro un senso di direzione.</span><span class="sxs-lookup"><span data-stu-id="04fbe-107">In previous chapters, we added spatialization to sounds to give them a sense of direction.</span></span> <span data-ttu-id="04fbe-108">In questo quinto capitolo, si aggiungerà un effetto di riverbero per dare un senso alla distanza.</span><span class="sxs-lookup"><span data-stu-id="04fbe-108">In this 5th chapter, we'll add a reverb effect to give sounds a sense of distance.</span></span> <span data-ttu-id="04fbe-109">I nostri obiettivi sono:</span><span class="sxs-lookup"><span data-stu-id="04fbe-109">Our objectives are to:</span></span>
* <span data-ttu-id="04fbe-110">Migliorare la distanza percepita delle origini audio aggiungendo Reverb</span><span class="sxs-lookup"><span data-stu-id="04fbe-110">Improve perceived distance of sound sources by adding reverb</span></span>
* <span data-ttu-id="04fbe-111">Controllare la distanza percepita del suono usando la distanza del listener con l'ologramma</span><span class="sxs-lookup"><span data-stu-id="04fbe-111">Control perceived distance of the sound using the listener's distance to the hologram</span></span>

## <a name="add-a-mixer-group-and-a-reverb-effect"></a><span data-ttu-id="04fbe-112">Aggiungere un gruppo di mixer e un effetto di riverbero</span><span class="sxs-lookup"><span data-stu-id="04fbe-112">Add a mixer group and a reverb effect</span></span>
<span data-ttu-id="04fbe-113">Nel [capitolo 2](unity-spatial-audio-ch2.md)è stato aggiunto un mixer.</span><span class="sxs-lookup"><span data-stu-id="04fbe-113">In [Chapter 2](unity-spatial-audio-ch2.md), we added a mixer.</span></span> <span data-ttu-id="04fbe-114">Il mixer include un **gruppo** per impostazione predefinita denominato **Master**.</span><span class="sxs-lookup"><span data-stu-id="04fbe-114">The mixer includes one **Group** by default called **Master**.</span></span> <span data-ttu-id="04fbe-115">Poiché si vuole applicare un effetto di riverbero solo ad alcuni suoni, aggiungere un secondo **gruppo** per i suoni.</span><span class="sxs-lookup"><span data-stu-id="04fbe-115">Because we'll only want to apply a reverb effect to some sounds, let's add a second **Group** for those sounds.</span></span> <span data-ttu-id="04fbe-116">Per aggiungere un **gruppo**, fare clic con il pulsante destro del mouse sul gruppo **Master** nel **mixer audio** e scegliere **Aggiungi gruppo figlio**:</span><span class="sxs-lookup"><span data-stu-id="04fbe-116">To add a **Group**, right click on the **Master** group in the **Audio Mixer** and choose **Add child group**:</span></span>

![Aggiungi gruppo figlio](images/spatial-audio/add-child-group.png)

<span data-ttu-id="04fbe-118">In questo esempio è stato denominato il nuovo gruppo "effetto stanza".</span><span class="sxs-lookup"><span data-stu-id="04fbe-118">In this example, we've named the new group "Room Effect".</span></span>

<span data-ttu-id="04fbe-119">Ogni **gruppo** ha un proprio set di effetti.</span><span class="sxs-lookup"><span data-stu-id="04fbe-119">Each **Group** has its own set of effects.</span></span> <span data-ttu-id="04fbe-120">Aggiungere un effetto del riverbero al nuovo gruppo facendo clic su **Aggiungi...** nel nuovo gruppo e scegliendo il **riverbero SFX**:</span><span class="sxs-lookup"><span data-stu-id="04fbe-120">Add a reverb effect to the new group by clicking **Add...** on the new group, and choosing **SFX Reverb**:</span></span>

![Aggiungi Riverb SFX](images/spatial-audio/add-sfx-reverb.png)

<span data-ttu-id="04fbe-122">Nella terminologia audio, l'audio originale, non riverberato, viene chiamato _percorso asciutto_e l'audio dopo l'applicazione di filtri con il filtro del riverbero viene chiamato _percorso bagnato_.</span><span class="sxs-lookup"><span data-stu-id="04fbe-122">In audio terminology, the original, unreverberated audio is called the _dry path_, and the audio after filtering with the reverb filter is called the _wet path_.</span></span> <span data-ttu-id="04fbe-123">Entrambi i percorsi vengono inviati all'output audio e i relativi punti di forza relativi in questa combinazione sono detti _mix bagnato/secco_.</span><span class="sxs-lookup"><span data-stu-id="04fbe-123">Both paths are sent to the audio output, and their relative strengths in this mixture is called the _wet/dry mix_.</span></span> <span data-ttu-id="04fbe-124">La combinazione Wet/Dry influiscono fortemente sul senso della distanza.</span><span class="sxs-lookup"><span data-stu-id="04fbe-124">The wet/dry mix strongly affects the sense of distance.</span></span>

<span data-ttu-id="04fbe-125">Il **riverbero SFX** include i controlli per regolare la combinazione di Wet/Dry nell'effetto.</span><span class="sxs-lookup"><span data-stu-id="04fbe-125">The **SFX Reverb** includes controls to adjust the wet/dry mix within the effect.</span></span> <span data-ttu-id="04fbe-126">Poiché il plug-in **Microsoft Spatializer** gestisce il percorso asciutto, verrà usato il **riverbero SFX** solo per il percorso bagnato.</span><span class="sxs-lookup"><span data-stu-id="04fbe-126">Because the **Microsoft Spatializer** plugin handles the dry path, we'll be using the **SFX Reverb** only for the wet path.</span></span> <span data-ttu-id="04fbe-127">Nel riquadro **Inspector** del **riverbero SFX**:</span><span class="sxs-lookup"><span data-stu-id="04fbe-127">On the **Inspector** pane of your **SFX Reverb**:</span></span>
* <span data-ttu-id="04fbe-128">Impostare la proprietà livello secco sull'impostazione più bassa (-10000 mB)</span><span class="sxs-lookup"><span data-stu-id="04fbe-128">Set the Dry Level property to the lowest setting (-10000 mB)</span></span>
* <span data-ttu-id="04fbe-129">Imposta la proprietà room sull'impostazione massima (0 mB)</span><span class="sxs-lookup"><span data-stu-id="04fbe-129">Set the Room property to the highest setting (0 mB)</span></span>

<span data-ttu-id="04fbe-130">Dopo queste modifiche, il riquadro **Inspector** del **riverbero SFX** sarà simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="04fbe-130">After these changes, the **Inspector** pane of the **SFX Reverb** will look like this:</span></span>

![Proprietà del riverbero SFX](images/spatial-audio/sfx-reverb-properties.png)

<span data-ttu-id="04fbe-132">Le altre impostazioni controllano l'aspetto della stanza simulata.</span><span class="sxs-lookup"><span data-stu-id="04fbe-132">The other settings control the feel of the simulated room.</span></span> <span data-ttu-id="04fbe-133">In particolare, il **tempo di decadimento** è correlato alla dimensione della stanza percepita.</span><span class="sxs-lookup"><span data-stu-id="04fbe-133">In particular, **Decay Time** is related to perceived room size.</span></span> 

## <a name="enable-reverb-on-the-video-playback"></a><span data-ttu-id="04fbe-134">Abilitare il riverbero per la riproduzione video</span><span class="sxs-lookup"><span data-stu-id="04fbe-134">Enable reverb on the video playback</span></span>
<span data-ttu-id="04fbe-135">Per abilitare il riverbero in un'origine audio sono necessari due passaggi:</span><span class="sxs-lookup"><span data-stu-id="04fbe-135">There are two steps to enable reverb on an audio source:</span></span>
* <span data-ttu-id="04fbe-136">Indirizzare l' **origine audio** al **gruppo** appropriato</span><span class="sxs-lookup"><span data-stu-id="04fbe-136">Route the **Audio Source** to the appropriate **Group**</span></span>
* <span data-ttu-id="04fbe-137">Impostare il plug-in **Microsoft Spatializer** per passare l'audio al **gruppo** per l'elaborazione</span><span class="sxs-lookup"><span data-stu-id="04fbe-137">Set the **Microsoft Spatializer** plugin to pass audio into the **Group** for processing</span></span>

<span data-ttu-id="04fbe-138">Nei passaggi seguenti verrà modificato lo script per controllare il routing audio e verrà collegato uno script di controllo fornito con il plug-in **Microsoft Spatializer** per inserire i dati nel Reverbo.</span><span class="sxs-lookup"><span data-stu-id="04fbe-138">In the following steps, we'll adjust our script to control the audio routing, and attach a control script provided with the **Microsoft Spatializer** plugin to feed data into the reverb.</span></span>

<span data-ttu-id="04fbe-139">Nel riquadro di **controllo** per il **Quad**fare clic su **Aggiungi componente** e aggiungere lo script del livello di invio dell' **effetto chat** :</span><span class="sxs-lookup"><span data-stu-id="04fbe-139">On the **Inspector** pane for the **Quad**, click **Add Component** and add the **Room Effect Send Level** script:</span></span>

![Aggiungi script del livello di trasmissione](images/spatial-audio/add-send-level-script.png)

> [!NOTE]
> <span data-ttu-id="04fbe-141">A meno che non si abiliti la funzionalità di **trasmissione dell'effetto spazio** del plug-in **Microsoft Spatializer** , non viene inviato alcun audio al motore audio Unity per l'elaborazione degli effetti.</span><span class="sxs-lookup"><span data-stu-id="04fbe-141">Unless you enable **Room Effect Send Level** feature of the **Microsoft Spatializer** plugin, it doesn't send any audio back to the Unity audio engine for effect processing.</span></span>

<span data-ttu-id="04fbe-142">Il componente del **livello di invio dell'effetto chat** include un controllo grafico che imposta il livello dell'audio inviato al motore audio di Unity per l'elaborazione dei verbi.</span><span class="sxs-lookup"><span data-stu-id="04fbe-142">The **Room Effect Send Level** component includes a graph control that sets the level of the audio sent to the Unity audio engine for reverb processing.</span></span> <span data-ttu-id="04fbe-143">Fare clic e trascinare la curva verso il basso per impostare il livello su about-30dB:</span><span class="sxs-lookup"><span data-stu-id="04fbe-143">Click and drag the curve downwards to set the level to about -30dB:</span></span>

![Modificare la curva del riverbero](images/spatial-audio/adjust-reverb-curve.png)

<span data-ttu-id="04fbe-145">Rimuovere quindi il commento dalle 4 righe commentate nello script **SpatializeOnOff** .</span><span class="sxs-lookup"><span data-stu-id="04fbe-145">Next, uncomment the 4 commented lines in the **SpatializeOnOff** script.</span></span> <span data-ttu-id="04fbe-146">Lo script sarà ora simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="04fbe-146">The script will now look like this:</span></span>
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Audio;

[RequireComponent(typeof(AudioSource))]
public class SpatializeOnOff : MonoBehaviour
{
    public GameObject ButtonTextObject;
    public AudioMixerGroup RoomEffectGroup;
    public AudioMixerGroup MasterGroup;

    private AudioSource m_SourceObject;
    private bool m_IsSpatialized;
    private TMPro.TextMeshPro m_TextMeshPro;

    public void Start()
    {
        m_SourceObject = gameObject.GetComponent<AudioSource>();
        m_TextMeshPro = ButtonTextObject.GetComponent<TMPro.TextMeshPro>();
        SetSpatialized();
    }

    public void SwapSpatialization()
    {
        if (m_IsSpatialized)
        {
            SetStereo();
        }
        else
        {
            SetSpatialized();
        }
    }

    private void SetSpatialized()
    {
        m_IsSpatialized = true;
        m_SourceObject.spatialBlend = 1;
        m_TextMeshPro.SetText("Set Stereo");
        m_SourceObject.outputAudioMixerGroup = RoomEffectGroup;
    }

    private void SetStereo()
    {
        m_IsSpatialized = false;
        m_SourceObject.spatialBlend = 0;
        m_TextMeshPro.SetText("Set Spatialized");
        m_SourceObject.outputAudioMixerGroup = MasterGroup;
    }

}
```

<span data-ttu-id="04fbe-147">Se si rimuove il commento da queste righe, vengono aggiunte due proprietà al riquadro **Inspector** per lo script.</span><span class="sxs-lookup"><span data-stu-id="04fbe-147">Uncommenting these lines adds two properties to the **Inspector** pane for the script.</span></span> <span data-ttu-id="04fbe-148">Per impostare questi elementi, nel riquadro **Inspector** del componente **Spatialize on** of the **Quad**:</span><span class="sxs-lookup"><span data-stu-id="04fbe-148">To set these, on the **Inspector** pane of the **Spatialize On Off** component of the **Quad**:</span></span>
* <span data-ttu-id="04fbe-149">Impostare la proprietà **gruppo effetti Room** sul nuovo gruppo di mixer effetti della stanza</span><span class="sxs-lookup"><span data-stu-id="04fbe-149">Set the **Room Effect Group** property to your new Room Effect mixer group</span></span>
* <span data-ttu-id="04fbe-150">Impostare la proprietà **gruppo Master** sul gruppo di mixer Master</span><span class="sxs-lookup"><span data-stu-id="04fbe-150">Set the **Master Group** property to the Master mixer group</span></span>

<span data-ttu-id="04fbe-151">Una volta apportate queste modifiche, le proprietà **Spatialize on off** hanno un aspetto simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="04fbe-151">After these changes, the **Spatialize On Off** properties will look like this:</span></span>

![Spatialize su off esteso](images/spatial-audio/spatialize-on-off-extended.png)

## <a name="next-steps"></a><span data-ttu-id="04fbe-153">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="04fbe-153">Next steps</span></span>

<span data-ttu-id="04fbe-154">Provare l'app in un HoloLens 2 o nell'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="04fbe-154">Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="04fbe-155">A questo punto, quando si tocca il pulsante nell'app per attivare la spazializzazione, lo script instrada l'audio del video al gruppo di effetti della stanza per aggiungere Reverb.</span><span class="sxs-lookup"><span data-stu-id="04fbe-155">Now, when touching the button in the app to activate spatialization, the script will route the video's audio to the Room Effect Group to add reverb.</span></span> <span data-ttu-id="04fbe-156">Quando si passa a stereo, l'audio viene indirizzato al gruppo Master ed è possibile evitare di aggiungere Reverb.</span><span class="sxs-lookup"><span data-stu-id="04fbe-156">When switching to stereo, it will route the audio to the Master group, and avoid adding reverb.</span></span>

<span data-ttu-id="04fbe-157">Sono state completate le esercitazioni audio spaziali HoloLens 2 per Unity.</span><span class="sxs-lookup"><span data-stu-id="04fbe-157">You've completed the HoloLens 2 spatial audio tutorials for Unity.</span></span> <span data-ttu-id="04fbe-158">Complimenti.</span><span class="sxs-lookup"><span data-stu-id="04fbe-158">Congratulations!</span></span>



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
# <a name="using-reverb-to-add-distance-to-spatial-audio"></a>Uso di Reverb per aggiungere distanza all'audio spaziale

## <a name="objectives"></a>Obiettivi
Nei capitoli precedenti è stata aggiunta la spazializzazione ai suoni per dare loro un senso di direzione. In questo quinto capitolo, si aggiungerà un effetto di riverbero per dare un senso alla distanza. I nostri obiettivi sono:
* Migliorare la distanza percepita delle origini audio aggiungendo Reverb
* Controllare la distanza percepita del suono usando la distanza del listener con l'ologramma

## <a name="add-a-mixer-group-and-a-reverb-effect"></a>Aggiungere un gruppo di mixer e un effetto di riverbero
Nel [capitolo 2](unity-spatial-audio-ch2.md)è stato aggiunto un mixer. Il mixer include un **gruppo** per impostazione predefinita denominato **Master**. Poiché si vuole applicare un effetto di riverbero solo ad alcuni suoni, aggiungere un secondo **gruppo** per i suoni. Per aggiungere un **gruppo**, fare clic con il pulsante destro del mouse sul gruppo **Master** nel **mixer audio** e scegliere **Aggiungi gruppo figlio**:

![Aggiungi gruppo figlio](images/spatial-audio/add-child-group.png)

In questo esempio è stato denominato il nuovo gruppo "effetto stanza".

Ogni **gruppo** ha un proprio set di effetti. Aggiungere un effetto del riverbero al nuovo gruppo facendo clic su **Aggiungi...** nel nuovo gruppo e scegliendo il **riverbero SFX**:

![Aggiungi Riverb SFX](images/spatial-audio/add-sfx-reverb.png)

Nella terminologia audio, l'audio originale, non riverberato, viene chiamato _percorso asciutto_e l'audio dopo l'applicazione di filtri con il filtro del riverbero viene chiamato _percorso bagnato_. Entrambi i percorsi vengono inviati all'output audio e i relativi punti di forza relativi in questa combinazione sono detti _mix bagnato/secco_. La combinazione Wet/Dry influiscono fortemente sul senso della distanza.

Il **riverbero SFX** include i controlli per regolare la combinazione di Wet/Dry nell'effetto. Poiché il plug-in **Microsoft Spatializer** gestisce il percorso asciutto, verrà usato il **riverbero SFX** solo per il percorso bagnato. Nel riquadro **Inspector** del **riverbero SFX**:
* Impostare la proprietà livello secco sull'impostazione più bassa (-10000 mB)
* Imposta la proprietà room sull'impostazione massima (0 mB)

Dopo queste modifiche, il riquadro **Inspector** del **riverbero SFX** sarà simile al seguente:

![Proprietà del riverbero SFX](images/spatial-audio/sfx-reverb-properties.png)

Le altre impostazioni controllano l'aspetto della stanza simulata. In particolare, il **tempo di decadimento** è correlato alla dimensione della stanza percepita. 

## <a name="enable-reverb-on-the-video-playback"></a>Abilitare il riverbero per la riproduzione video
Per abilitare il riverbero in un'origine audio sono necessari due passaggi:
* Indirizzare l' **origine audio** al **gruppo** appropriato
* Impostare il plug-in **Microsoft Spatializer** per passare l'audio al **gruppo** per l'elaborazione

Nei passaggi seguenti verrà modificato lo script per controllare il routing audio e verrà collegato uno script di controllo fornito con il plug-in **Microsoft Spatializer** per inserire i dati nel Reverbo.

Nel riquadro di **controllo** per il **Quad**fare clic su **Aggiungi componente** e aggiungere lo script del livello di invio dell' **effetto chat** :

![Aggiungi script del livello di trasmissione](images/spatial-audio/add-send-level-script.png)

> [!NOTE]
> A meno che non si abiliti la funzionalità di **trasmissione dell'effetto spazio** del plug-in **Microsoft Spatializer** , non viene inviato alcun audio al motore audio Unity per l'elaborazione degli effetti.

Il componente del **livello di invio dell'effetto chat** include un controllo grafico che imposta il livello dell'audio inviato al motore audio di Unity per l'elaborazione dei verbi. Fare clic e trascinare la curva verso il basso per impostare il livello su about-30dB:

![Modificare la curva del riverbero](images/spatial-audio/adjust-reverb-curve.png)

Rimuovere quindi il commento dalle 4 righe commentate nello script **SpatializeOnOff** . Lo script sarà ora simile al seguente:
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

Se si rimuove il commento da queste righe, vengono aggiunte due proprietà al riquadro **Inspector** per lo script. Per impostare questi elementi, nel riquadro **Inspector** del componente **Spatialize on** of the **Quad**:
* Impostare la proprietà **gruppo effetti Room** sul nuovo gruppo di mixer effetti della stanza
* Impostare la proprietà **gruppo Master** sul gruppo di mixer Master

Una volta apportate queste modifiche, le proprietà **Spatialize on off** hanno un aspetto simile al seguente:

![Spatialize su off esteso](images/spatial-audio/spatialize-on-off-extended.png)

## <a name="next-steps"></a>Passaggi successivi

Provare l'app in un HoloLens 2 o nell'editor di Unity. A questo punto, quando si tocca il pulsante nell'app per attivare la spazializzazione, lo script instrada l'audio del video al gruppo di effetti della stanza per aggiungere Reverb. Quando si passa a stereo, l'audio viene indirizzato al gruppo Master ed è possibile evitare di aggiungere Reverb.

Sono state completate le esercitazioni audio spaziali HoloLens 2 per Unity. Complimenti.



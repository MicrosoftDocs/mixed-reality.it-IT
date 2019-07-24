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
# <a name="spatial-sound-in-unity"></a>Audio spaziale in Unity

Questo argomento descrive come usare il suono spaziale nei progetti Unity. Vengono illustrati i file del plug-in necessari, nonché i componenti e le proprietà Unity che consentono il suono spaziale.

## <a name="enabling-spatial-sound-in-unity"></a>Abilitazione del suono spaziale in Unity

Il suono spaziale, in Unity, viene abilitato con un plug-in Spatializer audio. I file del plug-in vengono aggregati direttamente in Unity, quindi l'abilitazione del suono spaziale è semplice come **modificare > impostazioni del progetto > audio** e modificare il plug-in **Spatializer** nel controllo in **MS HRTF Spatializer**. Poiché Microsoft Spatializer supporta solo 48000Hz attualmente, è necessario impostare anche la frequenza di campionamento del sistema su 48000 per impedire un errore di HRTF nel caso raro in cui il dispositivo di output del sistema non sia già impostato su 48000:

![Inspector per AudioManager](images/audio-250px.png)<br>
*Inspector per AudioManager*

Il progetto Unity è ora configurato per l'uso di un suono spaziale.

>[!NOTE]
>Se non si usa un PC Windows 10 per lo sviluppo, non si otterrà un suono spaziale nell'editor né nel dispositivo (anche se si usa Windows 10 SDK).

## <a name="using-spatial-sound-in-unity"></a>Uso del suono spaziale in Unity

Il suono spaziale viene usato nel progetto Unity regolando tre impostazioni sui componenti di origine audio. La procedura seguente consente di configurare i componenti di origine audio per il suono spaziale.
* Nel pannello **gerarchia** selezionare l'oggetto Game con un' **origine audio**collegata.
* Nel pannello **Inspector** , sotto il componente **Audio source**
    * Selezionare l'opzione **Spatialize** .
    * Imposta **Spatial Blend** su **3D** (valore numerico 1).
    * Per ottenere risultati ottimali, espandere **impostazioni audio 3D** e impostare **volume attenuazione** su **Custom attenuazione**.

![Pannello Inspector in Unity che mostra l'origine audio](images/audiosource.png)<br>
*Pannello Inspector in Unity che mostra l'origine audio*

I suoni sono ora realisticamente disponibili nell'ambiente del progetto.

Si consiglia vivamente di acquisire familiarità con le [linee guida per la progettazione di suoni spaziali](spatial-sound-design.md). Queste linee guida consentono di integrare facilmente l'audio nel progetto e di immergere ulteriormente gli utenti nell'esperienza creata.

## <a name="setting-spatial-sound-settings"></a>Impostazione delle impostazioni del suono spaziale

Il plug-in Microsoft spatial audio fornisce un parametro aggiuntivo che può essere impostato, in base all'origine audio, per consentire un controllo aggiuntivo della simulazione audio. Questo parametro corrisponde alla dimensione della stanza simulata.

### <a name="room-size"></a>Dimensioni chat room

Dimensioni della stanza simulata dal suono spaziale. Le dimensioni approssimative delle chat sono; piccolo (un ufficio per una piccola sala riunioni), media (una sala riunioni di grandi dimensioni) e grandi (Auditorium). È anche possibile specificare una dimensione della stanza di None per simulare un ambiente esterno. La dimensione della stanza predefinita è piccola.

### <a name="example"></a>Esempio

MixedRealityToolkit per Unity fornisce una classe statica che rende più semplice l'impostazione delle impostazioni audio spaziali. Questa classe si trova nella [cartella MixedRealityToolkit\SpatialSound](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound) e può essere chiamata da qualsiasi script nel progetto. Si consiglia di impostare questi parametri in ogni componente di origine audio nel progetto. Nell'esempio seguente viene illustrata la selezione della dimensione media della stanza per un'origine audio collegata.

```cs
AudioSource audioSource = gameObject.GetComponent<AudioSource>()

if (audioSource != null) {
    SpatialSoundSettings.SetRoomSize(audioSource, SpatialMappingRoomSizes.Medium);
}
```

### <a name="directly-accessing-parameters-from-unity"></a>Accesso diretto ai parametri da Unity

Se non si vuole usare gli strumenti audio eccellenti in MixedRealityToolkit, di seguito viene illustrato come modificare i parametri di HRTF. È possibile copiarlo e incollarlo in uno script denominato *SetHRTF.cs* che si vuole alleghi a ogni HRTF audiosource. Consente di modificare i parametri importanti per HRTF.

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
### <a name="spatial-sound-in-mixed-reality-toolkit"></a>Audio spaziale nel Toolkit per realtà mista
- [HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest. Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity)

Gli esempi seguenti del Toolkit per la realtà mista sono esempi generali di effetti audio che illustrano come rendere le proprie esperienze più immersive usando un suono.
- [HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest. Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity)
- [HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest. Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity)

## <a name="see-also"></a>Vedere anche
* [Audio spaziale](spatial-sound.md)
* [Progettazione dell'audio spaziale](spatial-sound-design.md)

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
# <a name="spatial-sound-in-unity"></a>Audio spaziale in Unity

In questo argomento viene descritto come usare un suono spaziale nei progetti di Unity. Viene descritto come i file di plug-in obbligatorio, nonché i componenti di Unity e proprietà che consentono il suono spaziale.

## <a name="enabling-spatial-sound-in-unity"></a>Abilitare l'audio spaziale in Unity

Spaziale suono, in Unity, viene abilitata tramite un plug-in spaziale audio. I file di plug-in sono inclusi direttamente in Unity in modo che l'abilitazione di suono spaziale è semplice quanto dovrà **Modifica > impostazioni del progetto > Audio** e modificando il **spaziale plug-in** del controllo per il  **MS HRTF spaziale**. Poiché attualmente lo spaziale Microsoft supporta solo 48000Hz, è necessario impostare anche la frequenza di campionamento di sistema per 48000 per evitare un errore HRTF nel raro caso che il dispositivo di output di sistema non è impostato su 48000 già:

![Controllo per AudioManager](images/audio-250px.png)<br>
*Controllo per AudioManager*

Il progetto Unity è ora configurato per usare un suono spaziale.

>[!NOTE]
>Se non si usa un PC Windows 10 per lo sviluppo, si otterranno suono spaziale nell'editor, né sul dispositivo (anche se si usa Windows 10 SDK).

## <a name="using-spatial-sound-in-unity"></a>Uso di suono spaziale in Unity

Spaziale suono viene utilizzato nel progetto Unity regolando tre impostazioni sui componenti di origine Audio. La procedura seguente configurerà i componenti di origine Audio per un suono spaziale.
* Nel **gerarchia** panel, selezionare l'oggetto gioco che dispone di un oggetto associato **origine Audio**.
* Nel **Inspector** nel Pannello di **origine Audio** componente
    * Verificare i **Spatialize** opzione.
    * Impostare **Blend spaziali** al **3D** (valore numerico 1).
    * Per ottenere risultati ottimali, espandere **3D impostazioni audio** e impostare **attenuazione Volume** al **Custom attenuazione**.

![Pannello di controllo in Unity che riproduce l'Audio di origine](images/audiosource.png)<br>
*Pannello di controllo in Unity che riproduce l'Audio di origine*

I suoni ora realisticamente esistono all'interno di ambiente del progetto.

È consigliabile acquisire familiarità con le [linee guida di progettazione suono spaziale](spatial-sound-design.md). Queste linee guida per integrarsi perfettamente l'audio nel progetto e per un'ulteriore immersion sugli utenti nell'esperienza che è stato creato.

## <a name="setting-spatial-sound-settings"></a>Configurazione delle impostazioni di audio spaziali

Il plug-in Microsoft Spatial Sound fornisce un parametro aggiuntivo che è possibile impostare, d'una per ogni singola origine Audio, per consentire un maggiore controllo della simulazione audio. Questo parametro è la dimensione della chat room simulata.

### <a name="room-size"></a>Dimensioni di chat room

Le dimensioni della stanza che viene viene simulata dal suono spaziale. Le dimensioni approssimative delle sale sono; Small (un ufficio in una sala conferenze small), medie (una grande sala riunioni) o di grandi dimensioni (una magna). È anche possibile specificare una dimensione di chat room di none per simulare un ambiente esterno. Le dimensioni di spazio predefinite sono piccola.

### <a name="example"></a>Esempio

Il MixedRealityToolkit per Unity offre una classe statica che rende semplice, impostare le opzioni di segnale acustico spaziale. Questa classe è reperibile nella [MixedRealityToolkit\SpatialSound cartella](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound) e può essere chiamata da qualsiasi script nel progetto. È consigliabile impostare questi parametri per ogni componente di origine Audio nel progetto. Nell'esempio seguente viene illustrato come selezionare le dimensioni medie chat room per un'origine Audio collegata.

```cs
AudioSource audioSource = gameObject.GetComponent<AudioSource>()

if (audioSource != null) {
    SpatialSoundSettings.SetRoomSize(audioSource, SpatialMappingRoomSizes.Medium);
}
```

### <a name="directly-accessing-parameters-from-unity"></a>Accesso direttamente ai parametri di Unity

Se non si desidera utilizzare gli strumenti di Audio eccellente di MixedRealityToolkit, ecco come verrà modificata HRTF parametri. È possibile copiare e incollare questo in uno script chiamato *SetHRTF.cs* che vuoi collegare a ogni AudioSource HRTF. Consente di modificare i parametri importanti per HRTF.

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
### <a name="spatial-sound-in-mixed-reality-toolkit"></a>Spaziale audio nel Toolkit di realtà mista
- [HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity)

Gli esempi seguenti dal Toolkit di realtà mista sono esempi di effetti audio generali che illustrano i modi per rendere le proprie esperienze più coinvolgenti con file audio.
- [HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity)
- [HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity)

## <a name="see-also"></a>Vedere anche
* [Spaziale audio](spatial-sound.md)
* [Progettazione spaziale](spatial-sound-design.md)

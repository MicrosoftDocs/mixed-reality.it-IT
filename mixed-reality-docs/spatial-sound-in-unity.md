---
title: Audio spaziale in Unity
description: Riproduzione di un suono spaziale che deriva da uno specifico punto 3D nella scena Unity.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Unity, audio spaziale, HRTF, dimensioni della stanza
ms.openlocfilehash: c96717d9df9b89fbb09f0b4466ee3a9bf5c8a149
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641061"
---
# <a name="spatial-sound-in-unity"></a>Audio spaziale in Unity

Questa pagina contiene collegamenti alle risorse che consentono di usare e progettare con Microsoft HRTF Spatializer nei progetti di realtà mista Unity.

## <a name="enable-spatialization"></a>Abilita spazializzazione

Abilitare **MS HRTF Spatializer** nelle impostazioni audio del progetto. Per altri dettagli, vedere [la documentazione di Unity Spatializer](https://docs.unity3d.com/Manual/VRAudioSpatializer.html). 

Alleghi un' **origine audio** a un oggetto nella gerarchia e Abilita la spazializzazione selezionando la casella di controllo **Abilita spazializzazione** e spostando il dispositivo di scorrimento di **Blend spaziale** su "1". Per altri dettagli, vedere [la documentazione relativa all'origine audio di Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html). 

## <a name="design-with-spatialization"></a>Progettare con la spazializzazione

### <a name="distance-based-attenuation"></a>Attenuazione basata sulla distanza
Il decadimento basato sulla distanza predefinito di Unity ha una distanza minima di 1 metro e una distanza massima di 500 metri, con un attenuazione logaritmico. Questo può funzionare per lo scenario in uso oppure è possibile che le origini siano attenuate troppo rapidamente o troppo lentamente. Vedere [progettazione audio in realtà mista](spatial-sound-design.md) per le impostazioni consigliate per le curve di decadimento della distanza e vedere [la documentazione sull'origine audio di Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) per informazioni sull'impostazione di queste curve in Unity.

### <a name="environment"></a>Ambiente
**MS HRTF Spatializer** include un componente Reverb room con [quattro impostazioni di riverbero](https://docs.microsoft.com/windows/win32/api/hrtfapoapi/ne-hrtfapoapi-hrtfenvironment) e il valore predefinito è "Small". L'impostazione Room può essere modificata a livello di codice per ogni origine audio alleghiendo C# lo script seguente a ogni oggetto in Unity con un'origine audio con spazialità:

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

## <a name="unity-spatial-sound-examples"></a>Esempi di suoni spaziali Unity
Il Toolkit di realtà mista (MRTK) include esempi di modalità di applicazione degli effetti audio in realtà mista: [demo MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio).


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
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="0e3ea-104">Audio spaziale in Unity</span><span class="sxs-lookup"><span data-stu-id="0e3ea-104">Spatial Sound in Unity</span></span>

<span data-ttu-id="0e3ea-105">Questa pagina contiene collegamenti alle risorse che consentono di usare e progettare con Microsoft HRTF Spatializer nei progetti di realtà mista Unity.</span><span class="sxs-lookup"><span data-stu-id="0e3ea-105">This page links to resources to help you use and design with the Microsoft HRTF spatializer in your Unity mixed reality projects.</span></span>

## <a name="enable-spatialization"></a><span data-ttu-id="0e3ea-106">Abilita spazializzazione</span><span class="sxs-lookup"><span data-stu-id="0e3ea-106">Enable spatialization</span></span>

<span data-ttu-id="0e3ea-107">Abilitare **MS HRTF Spatializer** nelle impostazioni audio del progetto.</span><span class="sxs-lookup"><span data-stu-id="0e3ea-107">Enable the **MS HRTF Spatializer** in your project's audio settings.</span></span> <span data-ttu-id="0e3ea-108">Per altri dettagli, vedere [la documentazione di Unity Spatializer](https://docs.unity3d.com/Manual/VRAudioSpatializer.html).</span><span class="sxs-lookup"><span data-stu-id="0e3ea-108">For more details, see [Unity's spatializer documentation](https://docs.unity3d.com/Manual/VRAudioSpatializer.html).</span></span> 

<span data-ttu-id="0e3ea-109">Alleghi un' **origine audio** a un oggetto nella gerarchia e Abilita la spazializzazione selezionando la casella di controllo **Abilita spazializzazione** e spostando il dispositivo di scorrimento di **Blend spaziale** su "1".</span><span class="sxs-lookup"><span data-stu-id="0e3ea-109">Attach an **Audio Source** to an object in the hierarchy, and enable spatialization by checking the **Enable spatialization** checkbox and moving the **Spatial Blend** slider to '1'.</span></span> <span data-ttu-id="0e3ea-110">Per altri dettagli, vedere [la documentazione relativa all'origine audio di Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html).</span><span class="sxs-lookup"><span data-stu-id="0e3ea-110">For more details, see [Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html).</span></span> 

## <a name="design-with-spatialization"></a><span data-ttu-id="0e3ea-111">Progettare con la spazializzazione</span><span class="sxs-lookup"><span data-stu-id="0e3ea-111">Design with spatialization</span></span>

### <a name="distance-based-attenuation"></a><span data-ttu-id="0e3ea-112">Attenuazione basata sulla distanza</span><span class="sxs-lookup"><span data-stu-id="0e3ea-112">Distance-based attenuation</span></span>
<span data-ttu-id="0e3ea-113">Il decadimento basato sulla distanza predefinito di Unity ha una distanza minima di 1 metro e una distanza massima di 500 metri, con un attenuazione logaritmico.</span><span class="sxs-lookup"><span data-stu-id="0e3ea-113">Unity's default distance-based decay has a minimum distance of 1 meter and a maximum distance of 500 meters, with a logarithmic rolloff.</span></span> <span data-ttu-id="0e3ea-114">Questo può funzionare per lo scenario in uso oppure è possibile che le origini siano attenuate troppo rapidamente o troppo lentamente.</span><span class="sxs-lookup"><span data-stu-id="0e3ea-114">This may work for your scenario, or you may find sources attenuate too quickly or too slowly.</span></span> <span data-ttu-id="0e3ea-115">Vedere [progettazione audio in realtà mista](spatial-sound-design.md) per le impostazioni consigliate per le curve di decadimento della distanza e vedere [la documentazione sull'origine audio di Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) per informazioni sull'impostazione di queste curve in Unity.</span><span class="sxs-lookup"><span data-stu-id="0e3ea-115">See [sound design in mixed reality](spatial-sound-design.md) for recommended settings for distance decay curves, and see [Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) for information on setting these curves in Unity.</span></span>

### <a name="environment"></a><span data-ttu-id="0e3ea-116">Ambiente</span><span class="sxs-lookup"><span data-stu-id="0e3ea-116">Environment</span></span>
<span data-ttu-id="0e3ea-117">**MS HRTF Spatializer** include un componente Reverb room con [quattro impostazioni di riverbero](https://docs.microsoft.com/windows/win32/api/hrtfapoapi/ne-hrtfapoapi-hrtfenvironment) e il valore predefinito è "Small".</span><span class="sxs-lookup"><span data-stu-id="0e3ea-117">The **MS HRTF Spatializer** includes a room reverb component with [four reverb settings](https://docs.microsoft.com/windows/win32/api/hrtfapoapi/ne-hrtfapoapi-hrtfenvironment) and a default of 'small'.</span></span> <span data-ttu-id="0e3ea-118">L'impostazione Room può essere modificata a livello di codice per ogni origine audio alleghiendo C# lo script seguente a ogni oggetto in Unity con un'origine audio con spazialità:</span><span class="sxs-lookup"><span data-stu-id="0e3ea-118">The room setting can be changed programmatically for each audio source by attaching the following C# script to each object in Unity that has a spatialized Audio Source:</span></span>

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

## <a name="unity-spatial-sound-examples"></a><span data-ttu-id="0e3ea-119">Esempi di suoni spaziali Unity</span><span class="sxs-lookup"><span data-stu-id="0e3ea-119">Unity spatial sound examples</span></span>
<span data-ttu-id="0e3ea-120">Il Toolkit di realtà mista (MRTK) include esempi di modalità di applicazione degli effetti audio in realtà mista: [demo MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio).</span><span class="sxs-lookup"><span data-stu-id="0e3ea-120">The Mixed Reality Toolkit (MRTK) includes examples of ways to apply audio effects in mixed reality: [MRTK demos](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio).</span></span>


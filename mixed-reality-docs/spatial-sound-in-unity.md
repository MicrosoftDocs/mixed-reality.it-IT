---
title: Audio spaziale in Unity
description: Riprodurre un suono spaziale da uno specifico punto 3D nella scena Unity.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Unity, audio spaziale, HRTF, dimensioni della stanza
ms.openlocfilehash: 6720eac30c69ebfcd0f003cf131f60295818d676
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553699"
---
# <a name="spatial-sound-in-unity"></a>Audio spaziale in Unity

Questa pagina contiene collegamenti a risorse per il suono spaziale in Unity.

## <a name="spatializer-options"></a>Opzioni di Spatializer
Le opzioni di Spatializer per le applicazioni di realtà mista includono:
* *SPATIALIZER HRTF MS*. Unity fornisce questo elemento come parte del pacchetto facoltativo di *realtà mista di Windows* .
  * Questa operazione viene eseguita sulla CPU in un'architettura a "singola origine" con costi più elevati.
  * Questa operazione viene fornita per garantire la compatibilità con le versioni precedenti delle applicazioni HoloLens originali.
* *Microsoft Spatializer*. Questa operazione è disponibile dal [repository GitHub Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity).
  * Questa operazione usa un'architettura a più livelli di costo inferiore.
  * In HoloLens 2 questa operazione viene scaricata in un acceleratore hardware.

Per le nuove applicazioni, è consigliabile *Microsoft Spatializer*.

## <a name="enable-spatialization"></a>Abilita spazializzazione

Usare [NuGet per Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) per installare _Microsoft. SpatialAudio. Spatializer. Unity_ e scegliere **Microsoft Spatializer** nelle impostazioni audio del progetto. Quindi:
* Alleghi un' **origine audio** a un oggetto nella gerarchia
* Selezionare la casella di controllo **Abilita spazializzazione**
* Spostare il dispositivo di scorrimento di **Blend spaziale** su "1"
* Verificare che l'audio spaziale sia abilitato nella workstation per sviluppatori. Per abilitarla, fare clic con il pulsante destro del mouse sull'icona del volume sulla barra delle applicazioni e verificare che l'audio spaziale sia impostato su un valore diverso da "off". Per ottenere la migliore rappresentazione delle informazioni su HoloLens 2, scegliere **Windows Sonic per le cuffie**.

Per altri dettagli, vedi:
* [Repository GitHub Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity)
* [Esercitazione di Spatializer di Microsoft](unity-spatial-audio-ch1.md)
* [Documentazione dell'origine audio di Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [Documentazione di Unity Spatializer](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a>Attenuazione basata sulla distanza
Il decadimento basato sulla distanza predefinito di Unity ha una distanza minima di 1 metro e una distanza massima di 500 metri, con un attenuazione logaritmico. Queste impostazioni possono essere usate per lo scenario in uso oppure è possibile che le origini siano attenuate troppo rapidamente o troppo lentamente. Per altri dettagli, vedi:
* [Progettazione audio in realtà mista](spatial-sound-design.md) per le impostazioni consigliate.
* [Documentazione dell'origine audio di Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) per istruzioni sull'impostazione di queste curve.

## <a name="reverb"></a>Riverbero
_Microsoft Spatializer_ Disabilita gli effetti post-Spatializer per impostazione predefinita. Per abilitare il riverbero e altri effetti per le origini spaziali:
* Alleghi il componente del **livello di invio dell'effetto chat** a ogni origine
* Modificare la curva del livello di invio per ogni origine, per controllare il guadagno sull'audio restituito al grafico per l'elaborazione degli effetti

Per informazioni dettagliate, vedere [il capitolo 5 dell'esercitazione su Spatializer](unity-spatial-audio-ch5.md) .

## <a name="unity-spatial-sound-examples"></a>Esempi di suoni spaziali Unity
Per esempi di suoni spaziali in Unity, vedere:
* [Demo di MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* [Progetto di esempio Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)

## <a name="next-steps"></a>Passaggi successivi
* [Progettazione audio in realtà mista](spatial-sound-design.md)
* [Esercitazione di Spatializer di Microsoft](unity-spatial-audio-ch1.md)


---
title: Fotocamera/videocamera HoloLens in Unreal
description: Guida all'uso della fotocamera/videocamera HoloLens in Unreal
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, sviluppo, funzionalità, documentazione, guide, ologrammi, fotocamera, videocamera, MRC
ms.openlocfilehash: 06ceb26d58fe60848e5e90360aa2e05984a901c5
ms.sourcegitcommit: f24ac845e184c2f90e8b15adab9addb913f5cb83
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2020
ms.locfileid: "84451336"
---
# <a name="hololens-photovideo-camera-in-unreal"></a>Fotocamera/videocamera HoloLens in Unreal

HoloLens dispone di una fotocamera/videocamera che viene usata per l'acquisizione in realtà mista (MRC) e può essere usata da un'app per accedere agli oggetti visivi reali.

## <a name="render-from-the-pv-camera-for-mrc"></a>Eseguire il rendering dalla fotocamera/videocamera per MRC

> [!NOTE]
> Questa operazione richiede **Unreal Engine 4.25** o versioni successive.

Il sistema e i registratori MRC personalizzati creano acquisizioni in realtà mista combinando la fotocamera/videocamera con ologrammi sottoposti a rendering dall'app immersiva.

Per impostazione predefinita, l'acquisizione in realtà mista usa l'output olografico dell'occhio destro. Se un'app immersiva sceglie di [eseguire il rendering dalla fotocamera/videocamera](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in), verrà usata quest'ultima. Ciò migliora il mapping tra il mondo reale e gli ologrammi nel video MRC.

Per acconsentire esplicitamente al rendering dalla fotocamera/videocamera:

1. Chiama **SetEnabledMixedRealityCamera** e **ResizeMixedRealityCamera**.
    * Usa i valori **Size X** (Dimensione X) e **Size Y** (Dimensione Y) per impostare le dimensioni video.

![Terza fotocamera](images/unreal-camera-3rd.PNG)

Unreal gestirà quindi le richieste da MRC per eseguire il rendering dal punto di vista della fotocamera/videocamera.

> [!NOTE]
> Solo quando viene attivata [Aquisizione realtà mista](mixed-reality-capture.md) all'app verrà chiesto di eseguire il rendering dal punto di vista della fotocamera/videocamera.

## <a name="using-the-pv-camera"></a>Uso della fotocamera/videocamera

La texture della webcam può essere recuperata nel gioco in fase di runtime, ma deve essere abilitata in **Edit > Project Settings** (Modifica > Impostazioni progetto) nell'editor:
1. Passa a **Platforms > HoloLens > Capabilities** (Piattaforme > HoloLens > Funzionalità) e seleziona **Webcam**.
    * Usa la funzione **StartCameraCapture** per usare la webcam in fase di runtime e la funzione **StopCameraCapture** per arrestare la registrazione.

![Avvio e arresto della fotocamera](images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a>Rendering di un'immagine
Per eseguire il rendering dell'immagine della fotocamera:
1. Crea un'istanza materiale dinamica basata su un materiale nel progetto, denominato **PVCamMat** nello screenshot seguente.  
2. Imposta l'istanza materiale dinamica su una variabile **Material Instance Dynamic Object Reference** (Riferimento all'oggetto dinamico istanza materiale).  
3. Imposta il materiale dell'oggetto nella scena che eseguirà il rendering del feed della fotocamera su questa nuova istanza materiale dinamica.
    * Avvia un timer che verrà usato per associare l'immagine della fotocamera al materiale. 

![Rendering della fotocamera](images/unreal-camera-render.PNG)

4. Crea una nuova funzione per questo timer, in questo caso **MaterialTimer**, e chiama **GetARCameraImage** per ottenere la texture dalla webcam.  
5. Se la texture è valida, imposta un parametro di texture nello shader sull'immagine.  In alternativa, avvia di nuovo il timer del materiale. 

![Texture della fotocamera](images/unreal-camera-texture.PNG)

5. Assicurati che il materiale includa un parametro corrispondente al nome in **SetTextureParameterValue** associato a una voce di colore. In mancanza di questo parametro, l'immagine della fotocamera non potrà essere visualizzata correttamente.

![Texture della fotocamera](images/unreal-camera-material.PNG)

## <a name="see-also"></a>Vedere anche
* [Fotocamera individuabile](locatable-camera.md)
* [Acquisizione realtà mista per sviluppatori](mixed-reality-capture-for-developers.md)

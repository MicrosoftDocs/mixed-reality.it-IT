---
title: Fotocamera HoloLens in Unreal
description: Guida all'uso della fotocamera HoloLens in Unreal
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, sviluppo, funzionalità, documentazione, guide, ologrammi, fotocamera, terza fotocamera, MRC
ms.openlocfilehash: 9ef9ce27d161130c6b9f3aa6bb1dbc47d7608ad9
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840120"
---
# <a name="hololens-camera-in-unreal"></a>Fotocamera HoloLens in Unreal

## <a name="third-camera-mixed-reality-capture"></a>Acquisizione in realtà mista con la terza fotocamera

L'acquisizione in realtà mista con la terza fotocamera può essere usata per eseguire il rendering di un'acquisizione in realtà mista dalla prospettiva di una fotocamera nel visore HoloLens, piuttosto che dalla prospettiva dell'occhio.  Ciò migliora il mapping tra il mondo reale e gli ologrammi nel video MRC. 

Per acconsentire esplicitamente all'uso dell'acquisizione in realtà mista con la terza fotocamera, chiama SetEnabledMixedRealityCamera e ResizeMixedRealityCamera con le dimensioni video desiderate. 

![Terza fotocamera](images/unreal-camera-3rd.PNG)

Registra quindi un video MRC nel portale del dispositivo HoloLens. 

## <a name="pv-camera"></a>Fotocamera/videocamera

La texture della webcam può anche essere recuperata nel gioco in fase di esecuzione.  Per ottenere la texture della webcam in HoloLens, verifica innanzitutto che la funzionalità "Webcam" sia selezionata nell'editor di Unreal in Project Settings > Platform > HoloLens > Capabilities (Impostazioni progetto > Piattaforma > HoloLens > Funzionalità). 

Per acconsentire esplicitamente all'uso della webcam in fase di esecuzione, chiama la funzione StartCameraCapture.  Per arrestare l'acquisizione, chiama la funzione StopCameraCapture. 

![Avvio e arresto della fotocamera](images/unreal-camera-startstop.PNG)

Per eseguire il rendering dell'immagine della fotocamera, crea innanzitutto un'istanza del materiale dinamico basata su un materiale nel progetto.  In questo caso, l'istanza si basa su un materiale denominato PVCamMat.  Imposta questo materiale su una variabile con il tipo Material Instance Dynamic Object Reference (Istanza materiale - Riferimento oggetto dinamico).  Imposta quindi il materiale dell'oggetto nella scena che eseguirà il rendering del feed della fotocamera in questa nuova istanza del materiale dinamico e avvierà un timer che verrà usato per associare l'immagine della fotocamera al materiale. 

![Rendering della fotocamera](images/unreal-camera-render.PNG)

Crea una nuova funzione per questo timer, in questo caso MaterialTimer, e chiama GetARCameraImage per ottenere la texture dalla webcam.  Se la texture è valida, imposta un parametro di texture nello shader su questa immagine.  In alternativa, avvia di nuovo il timer del materiale. 

![Texture della fotocamera](images/unreal-camera-texture.PNG)

Il materiale deve avere un parametro corrispondente al nome in SetTextureParameterValue associato a una voce di colore per visualizzare correttamente l'immagine della fotocamera. 

![Texture della fotocamera](images/unreal-camera-material.PNG)

## <a name="see-also"></a>Vedere anche
* [Fotocamera individuabile](locatable-camera.md)
* [Acquisizione realtà mista per sviluppatori](mixed-reality-capture-for-developers.md)

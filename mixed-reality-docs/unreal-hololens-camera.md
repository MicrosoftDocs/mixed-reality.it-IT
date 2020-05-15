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
# <a name="hololens-camera-in-unreal"></a><span data-ttu-id="514e3-104">Fotocamera HoloLens in Unreal</span><span class="sxs-lookup"><span data-stu-id="514e3-104">HoloLens Camera in Unreal</span></span>

## <a name="third-camera-mixed-reality-capture"></a><span data-ttu-id="514e3-105">Acquisizione in realtà mista con la terza fotocamera</span><span class="sxs-lookup"><span data-stu-id="514e3-105">Third Camera Mixed Reality Capture</span></span>

<span data-ttu-id="514e3-106">L'acquisizione in realtà mista con la terza fotocamera può essere usata per eseguire il rendering di un'acquisizione in realtà mista dalla prospettiva di una fotocamera nel visore HoloLens, piuttosto che dalla prospettiva dell'occhio.</span><span class="sxs-lookup"><span data-stu-id="514e3-106">Third camera Mixed Reality Capture (MRC) can be used to render a mixed reality capture from the perspective of the camera on the HoloLens visor, rather than the perspective of the eye textures.</span></span>  <span data-ttu-id="514e3-107">Ciò migliora il mapping tra il mondo reale e gli ologrammi nel video MRC.</span><span class="sxs-lookup"><span data-stu-id="514e3-107">This improves the mapping between the real world and the holograms in the MRC video.</span></span> 

<span data-ttu-id="514e3-108">Per acconsentire esplicitamente all'uso dell'acquisizione in realtà mista con la terza fotocamera, chiama SetEnabledMixedRealityCamera e ResizeMixedRealityCamera con le dimensioni video desiderate.</span><span class="sxs-lookup"><span data-stu-id="514e3-108">To opt into using third camera MRC, call SetEnabledMixedRealityCamera and ResizeMixedRealityCamera with the desired video dimensions.</span></span> 

![Terza fotocamera](images/unreal-camera-3rd.PNG)

<span data-ttu-id="514e3-110">Registra quindi un video MRC nel portale del dispositivo HoloLens.</span><span class="sxs-lookup"><span data-stu-id="514e3-110">Then record an MRC video in the HoloLens device portal.</span></span> 

## <a name="pv-camera"></a><span data-ttu-id="514e3-111">Fotocamera/videocamera</span><span class="sxs-lookup"><span data-stu-id="514e3-111">PV Camera</span></span>

<span data-ttu-id="514e3-112">La texture della webcam può anche essere recuperata nel gioco in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="514e3-112">The webcam texture can also be retrieved in the game at runtime.</span></span>  <span data-ttu-id="514e3-113">Per ottenere la texture della webcam in HoloLens, verifica innanzitutto che la funzionalità "Webcam" sia selezionata nell'editor di Unreal in Project Settings > Platform > HoloLens > Capabilities (Impostazioni progetto > Piattaforma > HoloLens > Funzionalità).</span><span class="sxs-lookup"><span data-stu-id="514e3-113">To get the webcam texture on HoloLens, first ensure the “Webcam” capability is checked in the Unreal editor under Project Settings > Platform > HoloLens > Capabilities.</span></span> 

<span data-ttu-id="514e3-114">Per acconsentire esplicitamente all'uso della webcam in fase di esecuzione, chiama la funzione StartCameraCapture.</span><span class="sxs-lookup"><span data-stu-id="514e3-114">Opt into using the webcam at runtime with the StartCameraCapture function.</span></span>  <span data-ttu-id="514e3-115">Per arrestare l'acquisizione, chiama la funzione StopCameraCapture.</span><span class="sxs-lookup"><span data-stu-id="514e3-115">Stop capturing with the StopCameraCapture function.</span></span> 

![Avvio e arresto della fotocamera](images/unreal-camera-startstop.PNG)

<span data-ttu-id="514e3-117">Per eseguire il rendering dell'immagine della fotocamera, crea innanzitutto un'istanza del materiale dinamico basata su un materiale nel progetto.</span><span class="sxs-lookup"><span data-stu-id="514e3-117">To render the camera image, first create a dynamic material instance based on a material in the project.</span></span>  <span data-ttu-id="514e3-118">In questo caso, l'istanza si basa su un materiale denominato PVCamMat.</span><span class="sxs-lookup"><span data-stu-id="514e3-118">In this case based on a material named PVCamMat.</span></span>  <span data-ttu-id="514e3-119">Imposta questo materiale su una variabile con il tipo Material Instance Dynamic Object Reference (Istanza materiale - Riferimento oggetto dinamico).</span><span class="sxs-lookup"><span data-stu-id="514e3-119">Set this to a variable with type Material Instance Dynamic Object Reference.</span></span>  <span data-ttu-id="514e3-120">Imposta quindi il materiale dell'oggetto nella scena che eseguirà il rendering del feed della fotocamera in questa nuova istanza del materiale dinamico e avvierà un timer che verrà usato per associare l'immagine della fotocamera al materiale.</span><span class="sxs-lookup"><span data-stu-id="514e3-120">Then set the material of the object in the scene that will render the camera feed to this new dynamic material instance and start a timer that will be used to bind the camera image to the material.</span></span> 

![Rendering della fotocamera](images/unreal-camera-render.PNG)

<span data-ttu-id="514e3-122">Crea una nuova funzione per questo timer, in questo caso MaterialTimer, e chiama GetARCameraImage per ottenere la texture dalla webcam.</span><span class="sxs-lookup"><span data-stu-id="514e3-122">Create a new function for this timer, in this case MaterialTimer, and call GetARCameraImage to get the texture from the webcam.</span></span>  <span data-ttu-id="514e3-123">Se la texture è valida, imposta un parametro di texture nello shader su questa immagine.</span><span class="sxs-lookup"><span data-stu-id="514e3-123">If this texture is valid, set a texture parameter in the shader to this image.</span></span>  <span data-ttu-id="514e3-124">In alternativa, avvia di nuovo il timer del materiale.</span><span class="sxs-lookup"><span data-stu-id="514e3-124">Otherwise, start the material timer again.</span></span> 

![Texture della fotocamera](images/unreal-camera-texture.PNG)

<span data-ttu-id="514e3-126">Il materiale deve avere un parametro corrispondente al nome in SetTextureParameterValue associato a una voce di colore per visualizzare correttamente l'immagine della fotocamera.</span><span class="sxs-lookup"><span data-stu-id="514e3-126">The material should have a parameter matching the name in SetTextureParameterValue bound to a color entry to properly display the camera image.</span></span> 

![Texture della fotocamera](images/unreal-camera-material.PNG)

## <a name="see-also"></a><span data-ttu-id="514e3-128">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="514e3-128">See also</span></span>
* [<span data-ttu-id="514e3-129">Fotocamera individuabile</span><span class="sxs-lookup"><span data-stu-id="514e3-129">Locatable camera</span></span>](locatable-camera.md)
* [<span data-ttu-id="514e3-130">Acquisizione realtà mista per sviluppatori</span><span class="sxs-lookup"><span data-stu-id="514e3-130">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)

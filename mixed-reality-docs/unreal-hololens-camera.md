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
# <a name="hololens-photovideo-camera-in-unreal"></a><span data-ttu-id="ab2ab-104">Fotocamera/videocamera HoloLens in Unreal</span><span class="sxs-lookup"><span data-stu-id="ab2ab-104">HoloLens Photo/Video Camera in Unreal</span></span>

<span data-ttu-id="ab2ab-105">HoloLens dispone di una fotocamera/videocamera che viene usata per l'acquisizione in realtà mista (MRC) e può essere usata da un'app per accedere agli oggetti visivi reali.</span><span class="sxs-lookup"><span data-stu-id="ab2ab-105">The HoloLens has a Photo/Video (PV) Camera that is used for both Mixed Reality Capture (MRC) and can be used by an app to access real-world visuals.</span></span>

## <a name="render-from-the-pv-camera-for-mrc"></a><span data-ttu-id="ab2ab-106">Eseguire il rendering dalla fotocamera/videocamera per MRC</span><span class="sxs-lookup"><span data-stu-id="ab2ab-106">Render from the PV Camera for MRC</span></span>

> [!NOTE]
> <span data-ttu-id="ab2ab-107">Questa operazione richiede **Unreal Engine 4.25** o versioni successive.</span><span class="sxs-lookup"><span data-stu-id="ab2ab-107">This requires **Unreal Engine 4.25** or newer.</span></span>

<span data-ttu-id="ab2ab-108">Il sistema e i registratori MRC personalizzati creano acquisizioni in realtà mista combinando la fotocamera/videocamera con ologrammi sottoposti a rendering dall'app immersiva.</span><span class="sxs-lookup"><span data-stu-id="ab2ab-108">The system, and custom MRC recorders, create mixed reality captures by combining the PV Camera with holograms rendered by the immersive app.</span></span>

<span data-ttu-id="ab2ab-109">Per impostazione predefinita, l'acquisizione in realtà mista usa l'output olografico dell'occhio destro.</span><span class="sxs-lookup"><span data-stu-id="ab2ab-109">By default, mixed reality capture uses the right eye's holographic output.</span></span> <span data-ttu-id="ab2ab-110">Se un'app immersiva sceglie di [eseguire il rendering dalla fotocamera/videocamera](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in), verrà usata quest'ultima.</span><span class="sxs-lookup"><span data-stu-id="ab2ab-110">If an immersive app chooses to [render from the PV Camera](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) then that will be used instead.</span></span> <span data-ttu-id="ab2ab-111">Ciò migliora il mapping tra il mondo reale e gli ologrammi nel video MRC.</span><span class="sxs-lookup"><span data-stu-id="ab2ab-111">This improves the mapping between the real world and the holograms in the MRC video.</span></span>

<span data-ttu-id="ab2ab-112">Per acconsentire esplicitamente al rendering dalla fotocamera/videocamera:</span><span class="sxs-lookup"><span data-stu-id="ab2ab-112">To opt-in to rendering from the PV Camera:</span></span>

1. <span data-ttu-id="ab2ab-113">Chiama **SetEnabledMixedRealityCamera** e **ResizeMixedRealityCamera**.</span><span class="sxs-lookup"><span data-stu-id="ab2ab-113">Call **SetEnabledMixedRealityCamera** and **ResizeMixedRealityCamera**</span></span>
    * <span data-ttu-id="ab2ab-114">Usa i valori **Size X** (Dimensione X) e **Size Y** (Dimensione Y) per impostare le dimensioni video.</span><span class="sxs-lookup"><span data-stu-id="ab2ab-114">Use the **Size X** and **Size Y** values to set the video dimensions.</span></span>

![Terza fotocamera](images/unreal-camera-3rd.PNG)

<span data-ttu-id="ab2ab-116">Unreal gestirà quindi le richieste da MRC per eseguire il rendering dal punto di vista della fotocamera/videocamera.</span><span class="sxs-lookup"><span data-stu-id="ab2ab-116">Unreal will then handle requests from MRC to render from the PV Camera's perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="ab2ab-117">Solo quando viene attivata [Aquisizione realtà mista](mixed-reality-capture.md) all'app verrà chiesto di eseguire il rendering dal punto di vista della fotocamera/videocamera.</span><span class="sxs-lookup"><span data-stu-id="ab2ab-117">Only when [Mixed Reality Capture](mixed-reality-capture.md) is triggered will the app be asked to render from the photo/video camera's perspective.</span></span>

## <a name="using-the-pv-camera"></a><span data-ttu-id="ab2ab-118">Uso della fotocamera/videocamera</span><span class="sxs-lookup"><span data-stu-id="ab2ab-118">Using the PV Camera</span></span>

<span data-ttu-id="ab2ab-119">La texture della webcam può essere recuperata nel gioco in fase di runtime, ma deve essere abilitata in **Edit > Project Settings** (Modifica > Impostazioni progetto) nell'editor:</span><span class="sxs-lookup"><span data-stu-id="ab2ab-119">The webcam texture can be retrieved in the game at runtime, but it needs to be enabled in the editor's **Edit > Project Settings**:</span></span>
1. <span data-ttu-id="ab2ab-120">Passa a **Platforms > HoloLens > Capabilities** (Piattaforme > HoloLens > Funzionalità) e seleziona **Webcam**.</span><span class="sxs-lookup"><span data-stu-id="ab2ab-120">Go to **Platforms > HoloLens > Capabilities** and check **Webcam**.</span></span>
    * <span data-ttu-id="ab2ab-121">Usa la funzione **StartCameraCapture** per usare la webcam in fase di runtime e la funzione **StopCameraCapture** per arrestare la registrazione.</span><span class="sxs-lookup"><span data-stu-id="ab2ab-121">Use the **StartCameraCapture** function to use the webcam at runtime and the **StopCameraCapture** function to stop recording.</span></span>

![Avvio e arresto della fotocamera](images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a><span data-ttu-id="ab2ab-123">Rendering di un'immagine</span><span class="sxs-lookup"><span data-stu-id="ab2ab-123">Rendering an image</span></span>
<span data-ttu-id="ab2ab-124">Per eseguire il rendering dell'immagine della fotocamera:</span><span class="sxs-lookup"><span data-stu-id="ab2ab-124">To render the camera image:</span></span>
1. <span data-ttu-id="ab2ab-125">Crea un'istanza materiale dinamica basata su un materiale nel progetto, denominato **PVCamMat** nello screenshot seguente.</span><span class="sxs-lookup"><span data-stu-id="ab2ab-125">Create a dynamic material instance based on a material in the project, which is named **PVCamMat** in the screenshot below.</span></span>  
2. <span data-ttu-id="ab2ab-126">Imposta l'istanza materiale dinamica su una variabile **Material Instance Dynamic Object Reference** (Riferimento all'oggetto dinamico istanza materiale).</span><span class="sxs-lookup"><span data-stu-id="ab2ab-126">Set the dynamic material instance to a **Material Instance Dynamic Object Reference** variable.</span></span>  
3. <span data-ttu-id="ab2ab-127">Imposta il materiale dell'oggetto nella scena che eseguirà il rendering del feed della fotocamera su questa nuova istanza materiale dinamica.</span><span class="sxs-lookup"><span data-stu-id="ab2ab-127">Set the material of the object in the scene that will render the camera feed to this new dynamic material instance.</span></span>
    * <span data-ttu-id="ab2ab-128">Avvia un timer che verrà usato per associare l'immagine della fotocamera al materiale.</span><span class="sxs-lookup"><span data-stu-id="ab2ab-128">Start a timer that will be used to bind the camera image to the material.</span></span> 

![Rendering della fotocamera](images/unreal-camera-render.PNG)

4. <span data-ttu-id="ab2ab-130">Crea una nuova funzione per questo timer, in questo caso **MaterialTimer**, e chiama **GetARCameraImage** per ottenere la texture dalla webcam.</span><span class="sxs-lookup"><span data-stu-id="ab2ab-130">Create a new function for this timer, in this case **MaterialTimer**, and call **GetARCameraImage** to get the texture from the webcam.</span></span>  
5. <span data-ttu-id="ab2ab-131">Se la texture è valida, imposta un parametro di texture nello shader sull'immagine.</span><span class="sxs-lookup"><span data-stu-id="ab2ab-131">If the texture is valid, set a texture parameter in the shader to the image.</span></span>  <span data-ttu-id="ab2ab-132">In alternativa, avvia di nuovo il timer del materiale.</span><span class="sxs-lookup"><span data-stu-id="ab2ab-132">Otherwise, start the material timer again.</span></span> 

![Texture della fotocamera](images/unreal-camera-texture.PNG)

5. <span data-ttu-id="ab2ab-134">Assicurati che il materiale includa un parametro corrispondente al nome in **SetTextureParameterValue** associato a una voce di colore.</span><span class="sxs-lookup"><span data-stu-id="ab2ab-134">Make sure the material has a parameter matching the name in **SetTextureParameterValue** that's bound to a color entry.</span></span> <span data-ttu-id="ab2ab-135">In mancanza di questo parametro, l'immagine della fotocamera non potrà essere visualizzata correttamente.</span><span class="sxs-lookup"><span data-stu-id="ab2ab-135">Without this, the camera image can't be properly displayed.</span></span>

![Texture della fotocamera](images/unreal-camera-material.PNG)

## <a name="see-also"></a><span data-ttu-id="ab2ab-137">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ab2ab-137">See also</span></span>
* [<span data-ttu-id="ab2ab-138">Fotocamera individuabile</span><span class="sxs-lookup"><span data-stu-id="ab2ab-138">Locatable camera</span></span>](locatable-camera.md)
* [<span data-ttu-id="ab2ab-139">Acquisizione realtà mista per sviluppatori</span><span class="sxs-lookup"><span data-stu-id="ab2ab-139">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)

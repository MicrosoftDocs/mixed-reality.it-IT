---
title: Fotocamera individuabile in Unity
description: Utilizzo della fotocamera individuabili HoloLens in Unity.
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: foto, video, hololens, fotocamera, unity, individuabili
ms.openlocfilehash: f0183400f55b1c6663a9a20ab4992befe5ad0718
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59601772"
---
# <a name="locatable-camera-in-unity"></a><span data-ttu-id="5f1db-104">Fotocamera individuabile in Unity</span><span class="sxs-lookup"><span data-stu-id="5f1db-104">Locatable camera in Unity</span></span>

## <a name="enabling-the-capability-for-photo-video-camera"></a><span data-ttu-id="5f1db-105">Abilitazione della funzionalità per videocamera foto</span><span class="sxs-lookup"><span data-stu-id="5f1db-105">Enabling the capability for Photo Video Camera</span></span>

<span data-ttu-id="5f1db-106">La funzionalità "WebCam" deve essere dichiarata per un'app di usare la [fotocamera](locatable-camera.md).</span><span class="sxs-lookup"><span data-stu-id="5f1db-106">The "WebCam" capability must be declared for an app to use the [camera](locatable-camera.md).</span></span>
1. <span data-ttu-id="5f1db-107">Nell'Editor di Unity, passare alle impostazioni del giocatore, passare alla pagina "Modifica > progetto Impostazioni > Player"</span><span class="sxs-lookup"><span data-stu-id="5f1db-107">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="5f1db-108">Fare clic sulla scheda "Windows Store"</span><span class="sxs-lookup"><span data-stu-id="5f1db-108">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="5f1db-109">Nella sezione "Impostazioni > le funzionalità di pubblicazione", controllare la **WebCam** e **Microphone** funzionalità</span><span class="sxs-lookup"><span data-stu-id="5f1db-109">In the "Publishing Settings > Capabilities" section, check the **WebCam** and **Microphone** capabilities</span></span>

<span data-ttu-id="5f1db-110">Solo una singola operazione può verificarsi con la fotocamera alla volta.</span><span class="sxs-lookup"><span data-stu-id="5f1db-110">Only a single operation can occur with the camera at a time.</span></span> <span data-ttu-id="5f1db-111">Per determinare la modalità (foto, video o none) la fotocamera è attualmente in, è possibile controllare UnityEngine.XR.WSA.WebCam.Mode.</span><span class="sxs-lookup"><span data-stu-id="5f1db-111">To determine which mode (photo, video, or none) the camera is currently in, you can check UnityEngine.XR.WSA.WebCam.Mode.</span></span>

## <a name="photo-capture"></a><span data-ttu-id="5f1db-112">Acquisizione di foto</span><span class="sxs-lookup"><span data-stu-id="5f1db-112">Photo Capture</span></span>

<span data-ttu-id="5f1db-113">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span><span class="sxs-lookup"><span data-stu-id="5f1db-113">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="5f1db-114">**Tipo:** *PhotoCapture*</span><span class="sxs-lookup"><span data-stu-id="5f1db-114">**Type:** *PhotoCapture*</span></span>

<span data-ttu-id="5f1db-115">Il *PhotoCapture* tipo consente di sfruttare comunque fotografie con videocamera foto.</span><span class="sxs-lookup"><span data-stu-id="5f1db-115">The *PhotoCapture* type allows you to take still photographs with the Photo Video Camera.</span></span> <span data-ttu-id="5f1db-116">Il modello generale per l'utilizzo *PhotoCapture* a scattare una foto è come segue:</span><span class="sxs-lookup"><span data-stu-id="5f1db-116">The general pattern for using *PhotoCapture* to take a photo is as follows:</span></span>
1. <span data-ttu-id="5f1db-117">Creare un *PhotoCapture* oggetto</span><span class="sxs-lookup"><span data-stu-id="5f1db-117">Create a *PhotoCapture* object</span></span>
2. <span data-ttu-id="5f1db-118">Creare un *CameraParameters* oggetto con le impostazioni che si desidera</span><span class="sxs-lookup"><span data-stu-id="5f1db-118">Create a *CameraParameters* object with the settings we want</span></span>
3. <span data-ttu-id="5f1db-119">Avviare la modalità di foto tramite *StartPhotoModeAsync*</span><span class="sxs-lookup"><span data-stu-id="5f1db-119">Start Photo Mode via *StartPhotoModeAsync*</span></span>
4. <span data-ttu-id="5f1db-120">Scattare una foto desiderata</span><span class="sxs-lookup"><span data-stu-id="5f1db-120">Take the desired photo</span></span>
    * <span data-ttu-id="5f1db-121">(facoltativo) Interagire con tale immagine</span><span class="sxs-lookup"><span data-stu-id="5f1db-121">(optional) Interact with that picture</span></span>
5. <span data-ttu-id="5f1db-122">Interrompere la modalità di foto e pulire le risorse</span><span class="sxs-lookup"><span data-stu-id="5f1db-122">Stop Photo Mode and clean up resources</span></span>

### <a name="common-set-up-for-photocapture"></a><span data-ttu-id="5f1db-123">Set comune di per PhotoCapture</span><span class="sxs-lookup"><span data-stu-id="5f1db-123">Common Set Up for PhotoCapture</span></span>

<span data-ttu-id="5f1db-124">Per tutti gli tre utilizzi, viene avviata con lo stesso primi 3 passaggi precedenti</span><span class="sxs-lookup"><span data-stu-id="5f1db-124">For all three uses, we start with the same first 3 steps above</span></span>

<span data-ttu-id="5f1db-125">Iniziamo creando un *PhotoCapture* oggetto</span><span class="sxs-lookup"><span data-stu-id="5f1db-125">We start by creating a *PhotoCapture* object</span></span>

```cs
PhotoCapture photoCaptureObject = null;
   void Start()
   {
       PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
   }
```

<span data-ttu-id="5f1db-126">Successivamente è memorizzare l'oggetto, impostare i parametri e avviare la modalità di foto</span><span class="sxs-lookup"><span data-stu-id="5f1db-126">Next we store our object, set our parameters, and start Photo Mode</span></span>

```cs
void OnPhotoCaptureCreated(PhotoCapture captureObject)
   {
       photoCaptureObject = captureObject;

       Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

       CameraParameters c = new CameraParameters();
       c.hologramOpacity = 0.0f;
       c.cameraResolutionWidth = cameraResolution.width;
       c.cameraResolutionHeight = cameraResolution.height;
       c.pixelFormat = CapturePixelFormat.BGRA32;

       captureObject.StartPhotoModeAsync(c, false, OnPhotoModeStarted);
   }
```

<span data-ttu-id="5f1db-127">Al termine, verrà utilizzato anche lo stesso codice presentato qui di pulizia</span><span class="sxs-lookup"><span data-stu-id="5f1db-127">In the end, we will also use the same clean up code presented here</span></span>

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
   {
       photoCaptureObject.Dispose();
       photoCaptureObject = null;
   }
```

<span data-ttu-id="5f1db-128">Dopo questi passaggi, è possibile scegliere il tipo di foto da acquisire.</span><span class="sxs-lookup"><span data-stu-id="5f1db-128">After these steps, you can choose which type of photo to capture.</span></span>

### <a name="capture-a-photo-to-a-file"></a><span data-ttu-id="5f1db-129">Acquisire una foto in un File</span><span class="sxs-lookup"><span data-stu-id="5f1db-129">Capture a Photo to a File</span></span>

<span data-ttu-id="5f1db-130">L'operazione più semplice consiste nell'acquisire una foto direttamente in un file.</span><span class="sxs-lookup"><span data-stu-id="5f1db-130">The simplest operation is to capture a photo directly to a file.</span></span> <span data-ttu-id="5f1db-131">La foto può essere salvata come in formato JPG o PNG.</span><span class="sxs-lookup"><span data-stu-id="5f1db-131">The photo can be saved as a JPG or a PNG.</span></span>

<span data-ttu-id="5f1db-132">Se è stato avviato in modalità di foto, abbiamo ora verrà scattare una foto e archiviarlo sul disco</span><span class="sxs-lookup"><span data-stu-id="5f1db-132">If we successfully started photo mode, we now will take a photo and store it on disk</span></span>

```cs
private void OnPhotoModeStarted(PhotoCapture.PhotoCaptureResult result)
   {
       if (result.success)
       {
           string filename = string.Format(@"CapturedImage{0}_n.jpg", Time.time);
           string filePath = System.IO.Path.Combine(Application.persistentDataPath, filename);

           photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
       }
       else
       {
           Debug.LogError("Unable to start photo mode!");
       }
   }
```

<span data-ttu-id="5f1db-133">Dopo avere acquisito la foto sul disco, si verrà uscire dalla modalità di foto e quindi pulire gli oggetti</span><span class="sxs-lookup"><span data-stu-id="5f1db-133">After capturing the photo to disk, we will exit photo mode and then clean up our objects</span></span>

```cs
void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
   {
       if (result.success)
       {
           Debug.Log("Saved Photo to disk!");
           photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
       }
       else
       {
           Debug.Log("Failed to save Photo to disk");
       }
   }
```

### <a name="capture-a-photo-to-a-texture2d"></a><span data-ttu-id="5f1db-134">Acquisire una foto per un Texture2D</span><span class="sxs-lookup"><span data-stu-id="5f1db-134">Capture a Photo to a Texture2D</span></span>

<span data-ttu-id="5f1db-135">Durante l'acquisizione dei dati per un Texture2D, il processo è molto simile all'acquisizione sul disco.</span><span class="sxs-lookup"><span data-stu-id="5f1db-135">When capturing data to a Texture2D, the process is extremely similar to capturing to disk.</span></span>

<span data-ttu-id="5f1db-136">Verrà seguito il processo di configurazione precedente.</span><span class="sxs-lookup"><span data-stu-id="5f1db-136">We will follow the set up process above.</span></span>

<span data-ttu-id="5f1db-137">Nelle *OnPhotoModeStarted*, si acquisirà una cornice per la memoria.</span><span class="sxs-lookup"><span data-stu-id="5f1db-137">In *OnPhotoModeStarted*, we will capture a frame to memory.</span></span>

```cs
private void OnPhotoModeStarted(PhotoCapture.PhotoCaptureResult result)
   {
       if (result.success)
       {
           photoCaptureObject.TakePhotoAsync(OnCapturedPhotoToMemory);
       }
       else
       {
           Debug.LogError("Unable to start photo mode!");
       }
   }
```

<span data-ttu-id="5f1db-138">Verranno quindi applicare il risultato a una trama e usare più comuni di pulizia di codice precedente.</span><span class="sxs-lookup"><span data-stu-id="5f1db-138">We will then apply our result to a texture and use the common clean up code above.</span></span>

```cs
void OnCapturedPhotoToMemory(PhotoCapture.PhotoCaptureResult result, PhotoCaptureFrame photoCaptureFrame)
   {
       if (result.success)
       {
           // Create our Texture2D for use and set the correct resolution
           Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();
           Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
           // Copy the raw image data into our target texture
           photoCaptureFrame.UploadImageDataToTexture(targetTexture);
           // Do as we wish with the texture such as apply it to a material, etc.
       }
       // Clean up
       photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
   }
```

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a><span data-ttu-id="5f1db-139">Acquisire una foto e interagire con i byte non elaborati</span><span class="sxs-lookup"><span data-stu-id="5f1db-139">Capture a Photo and Interact with the Raw bytes</span></span>

<span data-ttu-id="5f1db-140">Per interagire con i byte non elaborati di un in memoria frame, si seguirà lo stesso set di passaggi come illustrato in precedenza e *OnPhotoModeStarted* come acquisire una foto per un Texture2D.</span><span class="sxs-lookup"><span data-stu-id="5f1db-140">To interact with the raw bytes of an in memory frame, we will follow the same set up steps as above and *OnPhotoModeStarted* as in capturing a photo to a Texture2D.</span></span> <span data-ttu-id="5f1db-141">La differenza risiede nei *OnCapturedPhotoToMemory* dove possiamo ottenere i byte non elaborati e interagire con essi.</span><span class="sxs-lookup"><span data-stu-id="5f1db-141">The difference is in *OnCapturedPhotoToMemory* where we can get the raw bytes and interact with them.</span></span>

<span data-ttu-id="5f1db-142">In questo esempio, si creerà una *elenco<Color>*  che può essere ulteriormente elaborata o applicate a una trama tramite *SetPixels()*</span><span class="sxs-lookup"><span data-stu-id="5f1db-142">In this example, we will create a *List<Color>* which could be further processed or applied to a texture via *SetPixels()*</span></span>

```cs
void OnCapturedPhotoToMemory(PhotoCapture.PhotoCaptureResult result, PhotoCaptureFrame photoCaptureFrame)
   {
       if (result.success)
       {
           List<byte> imageBufferList = new List<byte>();
           // Copy the raw IMFMediaBuffer data into our empty byte list.
           photoCaptureFrame.CopyRawImageDataIntoBuffer(imageBufferList);

           // In this example, we captured the image using the BGRA32 format.
           // So our stride will be 4 since we have a byte for each rgba channel.
           // The raw image data will also be flipped so we access our pixel data
           // in the reverse order.
           int stride = 4;
           float denominator = 1.0f / 255.0f;
           List<Color> colorArray = new List<Color>();
           for (int i = imageBufferList.Count - 1; i >= 0; i -= stride)
           {
               float a = (int)(imageBufferList[i - 0]) * denominator;
               float r = (int)(imageBufferList[i - 1]) * denominator;
               float g = (int)(imageBufferList[i - 2]) * denominator;
               float b = (int)(imageBufferList[i - 3]) * denominator;

               colorArray.Add(new Color(r, g, b, a));
           }
           // Now we could do something with the array such as texture.SetPixels() or run image processing on the list
       }
       photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
   }
```

## <a name="video-capture"></a><span data-ttu-id="5f1db-143">Acquisizione video</span><span class="sxs-lookup"><span data-stu-id="5f1db-143">Video Capture</span></span>

<span data-ttu-id="5f1db-144">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span><span class="sxs-lookup"><span data-stu-id="5f1db-144">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="5f1db-145">**Tipo:** *VideoCapture*</span><span class="sxs-lookup"><span data-stu-id="5f1db-145">**Type:** *VideoCapture*</span></span>

<span data-ttu-id="5f1db-146">*VideoCapture* funziona in modo molto simile a *PhotoCapture*.</span><span class="sxs-lookup"><span data-stu-id="5f1db-146">*VideoCapture* functions very similarly to *PhotoCapture*.</span></span> <span data-ttu-id="5f1db-147">Il solo due differenze sono che è necessario specificare un valore di fotogrammi al secondo (FPS) e che è possibile solo salvare direttamente su disco come file con estensione MP4.</span><span class="sxs-lookup"><span data-stu-id="5f1db-147">The only two differences are that you must specify a Frames Per Second (FPS) value and you can only save directly to disk as an .mp4 file.</span></span> <span data-ttu-id="5f1db-148">I passaggi da seguire *VideoCapture* sono i seguenti:</span><span class="sxs-lookup"><span data-stu-id="5f1db-148">The steps to use *VideoCapture* are as follows:</span></span>
1. <span data-ttu-id="5f1db-149">Creare un *VideoCapture* oggetto</span><span class="sxs-lookup"><span data-stu-id="5f1db-149">Create a *VideoCapture* object</span></span>
2. <span data-ttu-id="5f1db-150">Creare un *CameraParameters* oggetto con le impostazioni che si desidera</span><span class="sxs-lookup"><span data-stu-id="5f1db-150">Create a *CameraParameters* object with the settings we want</span></span>
3. <span data-ttu-id="5f1db-151">Avviare la modalità di Video tramite *StartVideoModeAsync*</span><span class="sxs-lookup"><span data-stu-id="5f1db-151">Start Video Mode via *StartVideoModeAsync*</span></span>
4. <span data-ttu-id="5f1db-152">Avviare la registrazione di video</span><span class="sxs-lookup"><span data-stu-id="5f1db-152">Start recording video</span></span>
5. <span data-ttu-id="5f1db-153">Arrestare la registrazione di video</span><span class="sxs-lookup"><span data-stu-id="5f1db-153">Stop recording video</span></span>
6. <span data-ttu-id="5f1db-154">Interrompere la modalità di Video e pulire le risorse</span><span class="sxs-lookup"><span data-stu-id="5f1db-154">Stop Video Mode and clean up resources</span></span>

<span data-ttu-id="5f1db-155">Iniziamo creando nostri *VideoCapture* oggetto *VideoCapture m_VideoCapture = null.*</span><span class="sxs-lookup"><span data-stu-id="5f1db-155">We start by creating our *VideoCapture* object *VideoCapture m_VideoCapture = null;*</span></span>

```cs
void Start ()
   {
       VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
   }
```

<span data-ttu-id="5f1db-156">Abbiamo quindi configurerà i parametri che è consigliabile per la registrazione e l'inizio.</span><span class="sxs-lookup"><span data-stu-id="5f1db-156">We then will set up the parameters we will want for the recording and start.</span></span>

```cs
void OnVideoCaptureCreated (VideoCapture videoCapture)
   {
       if (videoCapture != null)
       {
           m_VideoCapture = videoCapture;

           Resolution cameraResolution = VideoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();
           float cameraFramerate = VideoCapture.GetSupportedFrameRatesForResolution(cameraResolution).OrderByDescending((fps) => fps).First();

           CameraParameters cameraParameters = new CameraParameters();
           cameraParameters.hologramOpacity = 0.0f;
           cameraParameters.frameRate = cameraFramerate;
           cameraParameters.cameraResolutionWidth = cameraResolution.width;
           cameraParameters.cameraResolutionHeight = cameraResolution.height;
           cameraParameters.pixelFormat = CapturePixelFormat.BGRA32;

           m_VideoCapture.StartVideoModeAsync(cameraParameters,
                                               VideoCapture.AudioState.None,
                                               OnStartedVideoCaptureMode);
       }
       else
       {
           Debug.LogError("Failed to create VideoCapture Instance!");
       }
   }
```

<span data-ttu-id="5f1db-157">Una volta avviata, Microsoft inizierà la registrazione</span><span class="sxs-lookup"><span data-stu-id="5f1db-157">Once started, we will begin the recording</span></span>

```cs
void OnStartedVideoCaptureMode(VideoCapture.VideoCaptureResult result)
   {
       if (result.success)
       {
           string filename = string.Format("MyVideo_{0}.mp4", Time.time);
           string filepath = System.IO.Path.Combine(Application.persistentDataPath, filename);

           m_VideoCapture.StartRecordingAsync(filepath, OnStartedRecordingVideo);
       }
   }
```

<span data-ttu-id="5f1db-158">Dopo aver avviato la registrazione, è Impossibile aggiornare l'interfaccia utente o i comportamenti per consentire l'arresto.</span><span class="sxs-lookup"><span data-stu-id="5f1db-158">After recording has started, you could update your UI or behaviors to enable stopping.</span></span> <span data-ttu-id="5f1db-159">Qui abbiamo solo log</span><span class="sxs-lookup"><span data-stu-id="5f1db-159">Here we just log</span></span>

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Started Recording Video!");
       // We will stop the video from recording via other input such as a timer or a tap, etc.
   }
```

<span data-ttu-id="5f1db-160">In un secondo momento, è consigliabile arrestare la registrazione.</span><span class="sxs-lookup"><span data-stu-id="5f1db-160">At a later point, we will want to stop the recording.</span></span> <span data-ttu-id="5f1db-161">Questo può accadere da un timer o un input utente, ad esempio.</span><span class="sxs-lookup"><span data-stu-id="5f1db-161">This could happen from a timer or user input, for instance.</span></span>

```cs
// The user has indicated to stop recording
   void StopRecordingVideo()
   {
       m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
   }
```

<span data-ttu-id="5f1db-162">Dopo la registrazione è stato arrestato, si arresterà modalità video e pulire le risorse.</span><span class="sxs-lookup"><span data-stu-id="5f1db-162">Once the recording has stopped, we will stop video mode and clean up our resources.</span></span>

```cs
void OnStoppedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Stopped Recording Video!");
       m_VideoCapture.StopVideoModeAsync(OnStoppedVideoCaptureMode);
   }

   void OnStoppedVideoCaptureMode(VideoCapture.VideoCaptureResult result)
   {
       m_VideoCapture.Dispose();
       m_VideoCapture = null;
   }
```

## <a name="troubleshooting"></a><span data-ttu-id="5f1db-163">Risoluzione dei problemi</span><span class="sxs-lookup"><span data-stu-id="5f1db-163">Troubleshooting</span></span>
* <span data-ttu-id="5f1db-164">Nessun soluzioni sono disponibili</span><span class="sxs-lookup"><span data-stu-id="5f1db-164">No resolutions are available</span></span>
    * <span data-ttu-id="5f1db-165">Verificare che il **WebCam** funzionalità viene specificata nel progetto.</span><span class="sxs-lookup"><span data-stu-id="5f1db-165">Ensure the **WebCam** capability is specified in your project.</span></span>

## <a name="see-also"></a><span data-ttu-id="5f1db-166">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5f1db-166">See Also</span></span>
* [<span data-ttu-id="5f1db-167">Fotocamera individuabile</span><span class="sxs-lookup"><span data-stu-id="5f1db-167">Locatable camera</span></span>](locatable-camera.md)

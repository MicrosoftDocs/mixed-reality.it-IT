---
title: Fotocamera locatable in Unity
description: Uso della fotocamera HoloLens locatable in Unity.
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: Foto, video, hololens, fotocamera, Unity, locatable
ms.openlocfilehash: f0183400f55b1c6663a9a20ab4992befe5ad0718
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63515442"
---
# <a name="locatable-camera-in-unity"></a><span data-ttu-id="8ab9e-104">Fotocamera locatable in Unity</span><span class="sxs-lookup"><span data-stu-id="8ab9e-104">Locatable camera in Unity</span></span>

## <a name="enabling-the-capability-for-photo-video-camera"></a><span data-ttu-id="8ab9e-105">Abilitazione della funzionalità per la videocamera video foto</span><span class="sxs-lookup"><span data-stu-id="8ab9e-105">Enabling the capability for Photo Video Camera</span></span>

<span data-ttu-id="8ab9e-106">La funzionalità "WebCam" deve essere dichiarata per l'uso della [fotocamera](locatable-camera.md)da parte di un'app.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-106">The "WebCam" capability must be declared for an app to use the [camera](locatable-camera.md).</span></span>
1. <span data-ttu-id="8ab9e-107">Nell'editor di Unity passare alle impostazioni del lettore passando alla pagina "Edit > Project Settings > Player"</span><span class="sxs-lookup"><span data-stu-id="8ab9e-107">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="8ab9e-108">Fare clic sulla scheda "Windows Store"</span><span class="sxs-lookup"><span data-stu-id="8ab9e-108">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="8ab9e-109">Nella sezione "impostazioni di pubblicazione > funzionalità" controllare le funzionalità di **Webcam** e **microfono**</span><span class="sxs-lookup"><span data-stu-id="8ab9e-109">In the "Publishing Settings > Capabilities" section, check the **WebCam** and **Microphone** capabilities</span></span>

<span data-ttu-id="8ab9e-110">Con la fotocamera può essere eseguita una sola operazione alla volta.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-110">Only a single operation can occur with the camera at a time.</span></span> <span data-ttu-id="8ab9e-111">Per determinare la modalità (foto, video o nessuno) in cui si trova attualmente la fotocamera, è possibile controllare UnityEngine. XR. WSA. WebCam. Mode.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-111">To determine which mode (photo, video, or none) the camera is currently in, you can check UnityEngine.XR.WSA.WebCam.Mode.</span></span>

## <a name="photo-capture"></a><span data-ttu-id="8ab9e-112">Acquisizione foto</span><span class="sxs-lookup"><span data-stu-id="8ab9e-112">Photo Capture</span></span>

<span data-ttu-id="8ab9e-113">**Namespace** *UnityEngine. XR. WSA. WebCam*</span><span class="sxs-lookup"><span data-stu-id="8ab9e-113">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="8ab9e-114">**Tipo** *Acquisizione di fotorileva*</span><span class="sxs-lookup"><span data-stu-id="8ab9e-114">**Type:** *PhotoCapture*</span></span>

<span data-ttu-id="8ab9e-115">Il tipo di *acquisizione* di foto consente di scattare fotografie con la fotocamera del video.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-115">The *PhotoCapture* type allows you to take still photographs with the Photo Video Camera.</span></span> <span data-ttu-id="8ab9e-116">Il modello generale per l'  uso di fotocapture per scattare una foto è il seguente:</span><span class="sxs-lookup"><span data-stu-id="8ab9e-116">The general pattern for using *PhotoCapture* to take a photo is as follows:</span></span>
1. <span data-ttu-id="8ab9e-117">Creare un oggetto di *acquisizione*</span><span class="sxs-lookup"><span data-stu-id="8ab9e-117">Create a *PhotoCapture* object</span></span>
2. <span data-ttu-id="8ab9e-118">Creare un oggetto *CameraParameters* con le impostazioni desiderate</span><span class="sxs-lookup"><span data-stu-id="8ab9e-118">Create a *CameraParameters* object with the settings we want</span></span>
3. <span data-ttu-id="8ab9e-119">Avviare la modalità foto tramite *StartPhotoModeAsync*</span><span class="sxs-lookup"><span data-stu-id="8ab9e-119">Start Photo Mode via *StartPhotoModeAsync*</span></span>
4. <span data-ttu-id="8ab9e-120">Accetta la foto desiderata</span><span class="sxs-lookup"><span data-stu-id="8ab9e-120">Take the desired photo</span></span>
    * <span data-ttu-id="8ab9e-121">opzionale Interagire con l'immagine</span><span class="sxs-lookup"><span data-stu-id="8ab9e-121">(optional) Interact with that picture</span></span>
5. <span data-ttu-id="8ab9e-122">Arrestare la modalità foto e pulire le risorse</span><span class="sxs-lookup"><span data-stu-id="8ab9e-122">Stop Photo Mode and clean up resources</span></span>

### <a name="common-set-up-for-photocapture"></a><span data-ttu-id="8ab9e-123">Configurazione comune per l'acquisizione di un'immagine</span><span class="sxs-lookup"><span data-stu-id="8ab9e-123">Common Set Up for PhotoCapture</span></span>

<span data-ttu-id="8ab9e-124">Per tutti e tre gli usi, iniziamo con gli stessi primi 3 passaggi precedenti</span><span class="sxs-lookup"><span data-stu-id="8ab9e-124">For all three uses, we start with the same first 3 steps above</span></span>

<span data-ttu-id="8ab9e-125">Si inizia creando un oggetto di *acquisizione*</span><span class="sxs-lookup"><span data-stu-id="8ab9e-125">We start by creating a *PhotoCapture* object</span></span>

```cs
PhotoCapture photoCaptureObject = null;
   void Start()
   {
       PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
   }
```

<span data-ttu-id="8ab9e-126">Quindi, si archivia l'oggetto, si impostano i parametri e si avvia la modalità foto</span><span class="sxs-lookup"><span data-stu-id="8ab9e-126">Next we store our object, set our parameters, and start Photo Mode</span></span>

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

<span data-ttu-id="8ab9e-127">Alla fine, si userà anche lo stesso codice di pulizia presentato qui</span><span class="sxs-lookup"><span data-stu-id="8ab9e-127">In the end, we will also use the same clean up code presented here</span></span>

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
   {
       photoCaptureObject.Dispose();
       photoCaptureObject = null;
   }
```

<span data-ttu-id="8ab9e-128">Dopo questa procedura, è possibile scegliere il tipo di foto da acquisire.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-128">After these steps, you can choose which type of photo to capture.</span></span>

### <a name="capture-a-photo-to-a-file"></a><span data-ttu-id="8ab9e-129">Acquisisci una foto in un file</span><span class="sxs-lookup"><span data-stu-id="8ab9e-129">Capture a Photo to a File</span></span>

<span data-ttu-id="8ab9e-130">L'operazione più semplice consiste nell'acquisire una foto direttamente in un file.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-130">The simplest operation is to capture a photo directly to a file.</span></span> <span data-ttu-id="8ab9e-131">La foto può essere salvata come JPG o PNG.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-131">The photo can be saved as a JPG or a PNG.</span></span>

<span data-ttu-id="8ab9e-132">Se la modalità Photo è stata avviata correttamente, viene ora eseguita una foto e la si archivia sul disco</span><span class="sxs-lookup"><span data-stu-id="8ab9e-132">If we successfully started photo mode, we now will take a photo and store it on disk</span></span>

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

<span data-ttu-id="8ab9e-133">Dopo aver acquisito la foto su disco, si esce dalla modalità foto e quindi si puliscono gli oggetti</span><span class="sxs-lookup"><span data-stu-id="8ab9e-133">After capturing the photo to disk, we will exit photo mode and then clean up our objects</span></span>

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

### <a name="capture-a-photo-to-a-texture2d"></a><span data-ttu-id="8ab9e-134">Acquisire una foto in un Texture2D</span><span class="sxs-lookup"><span data-stu-id="8ab9e-134">Capture a Photo to a Texture2D</span></span>

<span data-ttu-id="8ab9e-135">Quando si acquisiscono dati in un Texture2D, il processo è molto simile all'acquisizione su disco.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-135">When capturing data to a Texture2D, the process is extremely similar to capturing to disk.</span></span>

<span data-ttu-id="8ab9e-136">Si seguirà il processo di configurazione precedente.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-136">We will follow the set up process above.</span></span>

<span data-ttu-id="8ab9e-137">In *OnPhotoModeStarted*si acquisirà un frame in memoria.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-137">In *OnPhotoModeStarted*, we will capture a frame to memory.</span></span>

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

<span data-ttu-id="8ab9e-138">Si applicherà quindi il risultato a una trama e si userà il codice di pulizia comune riportato sopra.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-138">We will then apply our result to a texture and use the common clean up code above.</span></span>

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

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a><span data-ttu-id="8ab9e-139">Acquisisci una foto e interagisci con i byte non elaborati</span><span class="sxs-lookup"><span data-stu-id="8ab9e-139">Capture a Photo and Interact with the Raw bytes</span></span>

<span data-ttu-id="8ab9e-140">Per interagire con i byte non elaborati di un frame in memoria, si seguiranno gli stessi passaggi di configurazione descritti in precedenza e *OnPhotoModeStarted* come per acquisire una foto in un Texture2D.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-140">To interact with the raw bytes of an in memory frame, we will follow the same set up steps as above and *OnPhotoModeStarted* as in capturing a photo to a Texture2D.</span></span> <span data-ttu-id="8ab9e-141">La differenza si trova in *OnCapturedPhotoToMemory* , in cui è possibile ottenere i byte non elaborati e interagire con essi.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-141">The difference is in *OnCapturedPhotoToMemory* where we can get the raw bytes and interact with them.</span></span>

<span data-ttu-id="8ab9e-142">In questo esempio verrà creato un *elenco<Color>*  che potrebbe essere ulteriormente elaborato o applicato a una trama tramite sepixels *()*</span><span class="sxs-lookup"><span data-stu-id="8ab9e-142">In this example, we will create a *List<Color>* which could be further processed or applied to a texture via *SetPixels()*</span></span>

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

## <a name="video-capture"></a><span data-ttu-id="8ab9e-143">Acquisizione video</span><span class="sxs-lookup"><span data-stu-id="8ab9e-143">Video Capture</span></span>

<span data-ttu-id="8ab9e-144">**Spazio dei nomi:** *UnityEngine. XR. WSA. WebCam*</span><span class="sxs-lookup"><span data-stu-id="8ab9e-144">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="8ab9e-145">**Tipo** *VideoCapture*</span><span class="sxs-lookup"><span data-stu-id="8ab9e-145">**Type:** *VideoCapture*</span></span>

<span data-ttu-id="8ab9e-146">*VideoCapture* funziona in modo molto simile alla fotoacquisizione.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-146">*VideoCapture* functions very similarly to *PhotoCapture*.</span></span> <span data-ttu-id="8ab9e-147">Le uniche due differenze sono che è necessario specificare un valore per i frame al secondo (FPS) ed è possibile salvare direttamente sul disco come file con estensione MP4.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-147">The only two differences are that you must specify a Frames Per Second (FPS) value and you can only save directly to disk as an .mp4 file.</span></span> <span data-ttu-id="8ab9e-148">I passaggi per usare *VideoCapture* sono i seguenti:</span><span class="sxs-lookup"><span data-stu-id="8ab9e-148">The steps to use *VideoCapture* are as follows:</span></span>
1. <span data-ttu-id="8ab9e-149">Creare un oggetto *VideoCapture*</span><span class="sxs-lookup"><span data-stu-id="8ab9e-149">Create a *VideoCapture* object</span></span>
2. <span data-ttu-id="8ab9e-150">Creare un oggetto *CameraParameters* con le impostazioni desiderate</span><span class="sxs-lookup"><span data-stu-id="8ab9e-150">Create a *CameraParameters* object with the settings we want</span></span>
3. <span data-ttu-id="8ab9e-151">Avviare la modalità video tramite *StartVideoModeAsync*</span><span class="sxs-lookup"><span data-stu-id="8ab9e-151">Start Video Mode via *StartVideoModeAsync*</span></span>
4. <span data-ttu-id="8ab9e-152">Avviare la registrazione del video</span><span class="sxs-lookup"><span data-stu-id="8ab9e-152">Start recording video</span></span>
5. <span data-ttu-id="8ab9e-153">Interrompi registrazione video</span><span class="sxs-lookup"><span data-stu-id="8ab9e-153">Stop recording video</span></span>
6. <span data-ttu-id="8ab9e-154">Arrestare la modalità video e pulire le risorse</span><span class="sxs-lookup"><span data-stu-id="8ab9e-154">Stop Video Mode and clean up resources</span></span>

<span data-ttu-id="8ab9e-155">Si inizia creando l'oggetto *VideoCapture* *VideoCapture m_VideoCapture = null;*</span><span class="sxs-lookup"><span data-stu-id="8ab9e-155">We start by creating our *VideoCapture* object *VideoCapture m_VideoCapture = null;*</span></span>

```cs
void Start ()
   {
       VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
   }
```

<span data-ttu-id="8ab9e-156">Si configureranno quindi i parametri che si desiderano per la registrazione e l'avvio.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-156">We then will set up the parameters we will want for the recording and start.</span></span>

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

<span data-ttu-id="8ab9e-157">Una volta avviata, si inizierà la registrazione</span><span class="sxs-lookup"><span data-stu-id="8ab9e-157">Once started, we will begin the recording</span></span>

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

<span data-ttu-id="8ab9e-158">Dopo l'avvio della registrazione, è possibile aggiornare l'interfaccia utente o i comportamenti per consentire l'arresto.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-158">After recording has started, you could update your UI or behaviors to enable stopping.</span></span> <span data-ttu-id="8ab9e-159">Qui è sufficiente registrare</span><span class="sxs-lookup"><span data-stu-id="8ab9e-159">Here we just log</span></span>

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Started Recording Video!");
       // We will stop the video from recording via other input such as a timer or a tap, etc.
   }
```

<span data-ttu-id="8ab9e-160">In un secondo momento, si vorrà arrestare la registrazione.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-160">At a later point, we will want to stop the recording.</span></span> <span data-ttu-id="8ab9e-161">Questo problema può verificarsi da un timer o da un input utente, ad esempio.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-161">This could happen from a timer or user input, for instance.</span></span>

```cs
// The user has indicated to stop recording
   void StopRecordingVideo()
   {
       m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
   }
```

<span data-ttu-id="8ab9e-162">Una volta arrestata la registrazione, si arresterà la modalità video e si puliranno le risorse.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-162">Once the recording has stopped, we will stop video mode and clean up our resources.</span></span>

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

## <a name="troubleshooting"></a><span data-ttu-id="8ab9e-163">Risoluzione dei problemi</span><span class="sxs-lookup"><span data-stu-id="8ab9e-163">Troubleshooting</span></span>
* <span data-ttu-id="8ab9e-164">Non sono disponibili risoluzioni</span><span class="sxs-lookup"><span data-stu-id="8ab9e-164">No resolutions are available</span></span>
    * <span data-ttu-id="8ab9e-165">Verificare che la funzionalità **Webcam** sia specificata nel progetto.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-165">Ensure the **WebCam** capability is specified in your project.</span></span>

## <a name="see-also"></a><span data-ttu-id="8ab9e-166">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8ab9e-166">See Also</span></span>
* [<span data-ttu-id="8ab9e-167">Fotocamera individuabile</span><span class="sxs-lookup"><span data-stu-id="8ab9e-167">Locatable camera</span></span>](locatable-camera.md)

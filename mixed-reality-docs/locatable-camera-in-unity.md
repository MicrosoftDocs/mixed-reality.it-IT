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
# <a name="locatable-camera-in-unity"></a>Fotocamera individuabile in Unity

## <a name="enabling-the-capability-for-photo-video-camera"></a>Abilitazione della funzionalità per videocamera foto

La funzionalità "WebCam" deve essere dichiarata per un'app di usare la [fotocamera](locatable-camera.md).
1. Nell'Editor di Unity, passare alle impostazioni del giocatore, passare alla pagina "Modifica > progetto Impostazioni > Player"
2. Fare clic sulla scheda "Windows Store"
3. Nella sezione "Impostazioni > le funzionalità di pubblicazione", controllare la **WebCam** e **Microphone** funzionalità

Solo una singola operazione può verificarsi con la fotocamera alla volta. Per determinare la modalità (foto, video o none) la fotocamera è attualmente in, è possibile controllare UnityEngine.XR.WSA.WebCam.Mode.

## <a name="photo-capture"></a>Acquisizione di foto

**Namespace:** *UnityEngine.XR.WSA.WebCam*<br>
**Tipo:** *PhotoCapture*

Il *PhotoCapture* tipo consente di sfruttare comunque fotografie con videocamera foto. Il modello generale per l'utilizzo *PhotoCapture* a scattare una foto è come segue:
1. Creare un *PhotoCapture* oggetto
2. Creare un *CameraParameters* oggetto con le impostazioni che si desidera
3. Avviare la modalità di foto tramite *StartPhotoModeAsync*
4. Scattare una foto desiderata
    * (facoltativo) Interagire con tale immagine
5. Interrompere la modalità di foto e pulire le risorse

### <a name="common-set-up-for-photocapture"></a>Set comune di per PhotoCapture

Per tutti gli tre utilizzi, viene avviata con lo stesso primi 3 passaggi precedenti

Iniziamo creando un *PhotoCapture* oggetto

```cs
PhotoCapture photoCaptureObject = null;
   void Start()
   {
       PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
   }
```

Successivamente è memorizzare l'oggetto, impostare i parametri e avviare la modalità di foto

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

Al termine, verrà utilizzato anche lo stesso codice presentato qui di pulizia

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
   {
       photoCaptureObject.Dispose();
       photoCaptureObject = null;
   }
```

Dopo questi passaggi, è possibile scegliere il tipo di foto da acquisire.

### <a name="capture-a-photo-to-a-file"></a>Acquisire una foto in un File

L'operazione più semplice consiste nell'acquisire una foto direttamente in un file. La foto può essere salvata come in formato JPG o PNG.

Se è stato avviato in modalità di foto, abbiamo ora verrà scattare una foto e archiviarlo sul disco

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

Dopo avere acquisito la foto sul disco, si verrà uscire dalla modalità di foto e quindi pulire gli oggetti

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

### <a name="capture-a-photo-to-a-texture2d"></a>Acquisire una foto per un Texture2D

Durante l'acquisizione dei dati per un Texture2D, il processo è molto simile all'acquisizione sul disco.

Verrà seguito il processo di configurazione precedente.

Nelle *OnPhotoModeStarted*, si acquisirà una cornice per la memoria.

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

Verranno quindi applicare il risultato a una trama e usare più comuni di pulizia di codice precedente.

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

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a>Acquisire una foto e interagire con i byte non elaborati

Per interagire con i byte non elaborati di un in memoria frame, si seguirà lo stesso set di passaggi come illustrato in precedenza e *OnPhotoModeStarted* come acquisire una foto per un Texture2D. La differenza risiede nei *OnCapturedPhotoToMemory* dove possiamo ottenere i byte non elaborati e interagire con essi.

In questo esempio, si creerà una *elenco<Color>*  che può essere ulteriormente elaborata o applicate a una trama tramite *SetPixels()*

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

## <a name="video-capture"></a>Acquisizione video

**Namespace:** *UnityEngine.XR.WSA.WebCam*<br>
**Tipo:** *VideoCapture*

*VideoCapture* funziona in modo molto simile a *PhotoCapture*. Il solo due differenze sono che è necessario specificare un valore di fotogrammi al secondo (FPS) e che è possibile solo salvare direttamente su disco come file con estensione MP4. I passaggi da seguire *VideoCapture* sono i seguenti:
1. Creare un *VideoCapture* oggetto
2. Creare un *CameraParameters* oggetto con le impostazioni che si desidera
3. Avviare la modalità di Video tramite *StartVideoModeAsync*
4. Avviare la registrazione di video
5. Arrestare la registrazione di video
6. Interrompere la modalità di Video e pulire le risorse

Iniziamo creando nostri *VideoCapture* oggetto *VideoCapture m_VideoCapture = null.*

```cs
void Start ()
   {
       VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
   }
```

Abbiamo quindi configurerà i parametri che è consigliabile per la registrazione e l'inizio.

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

Una volta avviata, Microsoft inizierà la registrazione

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

Dopo aver avviato la registrazione, è Impossibile aggiornare l'interfaccia utente o i comportamenti per consentire l'arresto. Qui abbiamo solo log

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Started Recording Video!");
       // We will stop the video from recording via other input such as a timer or a tap, etc.
   }
```

In un secondo momento, è consigliabile arrestare la registrazione. Questo può accadere da un timer o un input utente, ad esempio.

```cs
// The user has indicated to stop recording
   void StopRecordingVideo()
   {
       m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
   }
```

Dopo la registrazione è stato arrestato, si arresterà modalità video e pulire le risorse.

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

## <a name="troubleshooting"></a>Risoluzione dei problemi
* Nessun soluzioni sono disponibili
    * Verificare che il **WebCam** funzionalità viene specificata nel progetto.

## <a name="see-also"></a>Vedere anche
* [Fotocamera individuabile](locatable-camera.md)

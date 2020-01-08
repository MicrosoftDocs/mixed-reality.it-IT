---
title: Fotocamera locatable in Unity
description: Uso della fotocamera HoloLens locatable in Unity.
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: Foto, video, hololens, fotocamera, Unity, locatable
ms.openlocfilehash: b4a1a7e11a7606dab76b954c8d58a335d6bae0ab
ms.sourcegitcommit: d0da0214fdd2bbac5a91a5d895bf0e87413b29b2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597614"
---
# <a name="locatable-camera-in-unity"></a>Fotocamera locatable in Unity

## <a name="enabling-the-capability-for-photo-video-camera"></a>Abilitazione della funzionalità per la videocamera video foto

La funzionalità "WebCam" deve essere dichiarata per l'uso della [fotocamera](locatable-camera.md)da parte di un'app.
1. Nell'editor di Unity passare alle impostazioni del lettore passando alla pagina "Edit > Project Settings > Player"
2. Fare clic sulla scheda "Windows Store"
3. Nella sezione "impostazioni di pubblicazione > funzionalità" controllare le funzionalità di **Webcam** e **microfono**

Con la fotocamera può essere eseguita una sola operazione alla volta. Per determinare la modalità (foto, video o nessuno) in cui si trova attualmente la fotocamera, è possibile controllare UnityEngine. XR. WSA. WebCam. Mode.

## <a name="photo-capture"></a>Acquisizione foto

**Spazio dei nomi:** *UnityEngine. XR. WSA. Webcam*<br>
**Tipo:** *fotoacquisizione*

Il tipo di *acquisizione* di foto consente di scattare fotografie con la fotocamera del video. Il modello generale per l'uso di *fotocapture* per scattare una foto è il seguente:
1. Creare un oggetto di *acquisizione*
2. Creare un oggetto *CameraParameters* con le impostazioni desiderate
3. Avviare la modalità foto tramite *StartPhotoModeAsync*
4. Accetta la foto desiderata
    * opzionale Interagire con l'immagine
5. Arrestare la modalità foto e pulire le risorse

### <a name="common-set-up-for-photocapture"></a>Configurazione comune per l'acquisizione di un'immagine

Per tutti e tre gli usi, iniziare con gli stessi primi 3 passaggi precedenti

Iniziare creando un oggetto di *acquisizione*

```cs
PhotoCapture photoCaptureObject = null;
   void Start()
   {
       PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
   }
```

Quindi, archiviare l'oggetto, impostare i parametri e avviare la modalità foto

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

Alla fine, si userà anche lo stesso codice di pulizia presentato qui

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
   {
       photoCaptureObject.Dispose();
       photoCaptureObject = null;
   }
```

Dopo questa procedura, è possibile scegliere il tipo di foto da acquisire.

### <a name="capture-a-photo-to-a-file"></a>Acquisisci una foto in un file

L'operazione più semplice consiste nell'acquisire una foto direttamente in un file. La foto può essere salvata come JPG o PNG.

Se la modalità Photo è stata avviata correttamente, scattare una foto e archiviarla sul disco

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

Dopo aver acquisito la foto su disco, uscire dalla modalità foto e quindi pulire gli oggetti

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

### <a name="capture-a-photo-to-a-texture2d"></a>Acquisire una foto in un Texture2D

Quando si acquisiscono dati in un Texture2D, il processo è molto simile all'acquisizione su disco.

Seguire il processo di configurazione precedente.

In *OnPhotoModeStarted*acquisire un frame in memoria.

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

Si applicherà quindi il risultato a una trama e si userà il codice di pulizia comune riportato sopra.

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

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a>Acquisisci una foto e interagisci con i byte non elaborati

Per interagire con i byte non elaborati di un frame in memoria, seguire gli stessi passaggi di configurazione descritti in precedenza e *OnPhotoModeStarted* come in acquisizione di una foto in un Texture2D. La differenza si trova in *OnCapturedPhotoToMemory* , in cui è possibile ottenere i byte non elaborati e interagire con essi.

In questo esempio si creerà un *elenco<Color>* che potrebbe essere ulteriormente elaborato o applicato a una trama tramite *sepixels ()*

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

**Spazio dei nomi:** *UnityEngine. XR. WSA. Webcam*<br>
**Tipo:** *VideoCapture*

*VideoCapture* funziona in modo molto simile alla *fotoacquisizione*. Le uniche due differenze sono che è necessario specificare un valore per i frame al secondo (FPS) ed è possibile salvare direttamente sul disco come file con estensione MP4. I passaggi per usare *VideoCapture* sono i seguenti:
1. Creare un oggetto *VideoCapture*
2. Creare un oggetto *CameraParameters* con le impostazioni desiderate
3. Avviare la modalità video tramite *StartVideoModeAsync*
4. Avviare la registrazione del video
5. Interrompi registrazione video
6. Arrestare la modalità video e pulire le risorse

Per iniziare, creare l'oggetto *VideoCapture* *VideoCapture m_VideoCapture = null;*

```cs
void Start ()
   {
       VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
   }
```

Successivamente, impostare i parametri da usare per la registrazione e avviare.

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

Una volta avviata, iniziare la registrazione

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

Dopo l'avvio della registrazione, è possibile aggiornare l'interfaccia utente o i comportamenti per consentire l'arresto. Qui è sufficiente eseguire il log.

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Started Recording Video!");
       // We will stop the video from recording via other input such as a timer or a tap, etc.
   }
```

In un secondo momento, sarà necessario arrestare la registrazione. Questo problema può verificarsi da un timer o da un input utente, ad esempio.

```cs
// The user has indicated to stop recording
   void StopRecordingVideo()
   {
       m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
   }
```

Dopo che la registrazione è stata interrotta, arrestare la modalità video e pulire le risorse.

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
* Non sono disponibili risoluzioni
    * Verificare che la funzionalità **Webcam** sia specificata nel progetto.

## <a name="see-also"></a>Vedi anche
* [Fotocamera individuabile](locatable-camera.md)

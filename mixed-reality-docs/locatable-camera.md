---
title: Fotocamera individuabile
description: Informazioni generali sulla fotocamera anteriore HoloLens, come funziona e i profili e le soluzioni disponibili per gli sviluppatori.
author: wguyman
ms.author: wguyman
ms.date: 06/12/2019
ms.topic: article
keywords: fotocamera, hololens, fotocamera colore, affiancate, hololens, 2, cv, visione artificiale, stima front, marcatori, codice a matrice, a matrice, foto, video
ms.openlocfilehash: cadcd0762b8adf1001896c614451d2e1c9776c65
ms.sourcegitcommit: 79398a6b5b7037babcb05d86a5bcc336fd089ea0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67028606"
---
# <a name="locatable-camera"></a>Fotocamera individuabile

HoloLens include una fotocamera posta sul world nella parte anteriore del dispositivo che consente alle app di vedere ciò che viene visualizzato all'utente. Gli sviluppatori hanno accesso e controllo della fotocamera, esattamente come accade per le fotocamere colore su Smartphone, portatili o desktop. Le stesse finestre universale [acquisizione di media](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx) e foundation supporti windows API utilizzabili sui desktop e mobile funzionano HoloLens. Unity [è anche eseguito il wrapping di queste finestre API](locatable-camera-in-unity.md) astrarre semplice utilizzo della fotocamera su HoloLens per le attività, ad esempio tenendo regolari foto e video (con o senza vntana) e individuare la posizione della fotocamera in e prospettiva nel scena.

## <a name="device-camera-information"></a>Informazioni dispositivo della fotocamera

### <a name="hololens-first-generation"></a>HoloLens (prima generazione)

* Fotocamera foto/video (PV) lo stato attivo predefinito con pipeline di elaborazione di immagini completi, l'esposizione automatica e bilanciamento automatico del bianco.
* LED di Privacy white rivolta verso il mondo si accende ogni volta che la fotocamera è attiva
* La fotocamera supporta le modalità seguenti (tutte le modalità sono proporzioni 16:9) a 5 fps, 24, 20, 15 e 30:

  |  Video  |  Anteprima  |  Ancora  |  Orizzontale campo visualizzazione (H) |  Utilizzo consigliato | 
  |----------|----------|----------|----------|----------|
  |  1280x720 |  1280x720 |  1280x720 |  45deg  |  (modalità predefinita con la stabilizzazione video) | 
  |  N/D |  N/D |  2048x1152 |  67deg |  Immagini più elevata risoluzione | 
  |  1408x792 |  1408x792 |  1408x792 |  48deg |  Risoluzione overscan (riempimento) prima di stabilizzazione video | 
  |  1344x756 |  1344x756 |  1344x756 |  67deg |  Modalità del campo di visualizzazione video grandi dimensioni con overscan | 
  |  896x504 |  896x504 |  896x504 |  48deg |  Basso consumo / modalità bassa risoluzione per immagine l'elaborazione delle attività | 

### <a name="hololens-2"></a>HoloLens 2

* Fotocamera foto/video (PV) e messa a fuoco con pipeline di elaborazione di immagini completi, l'esposizione automatica e bilanciamento automatico del bianco.
* LED di Privacy white rivolta verso il mondo si accende ogni volta che la fotocamera è attiva.
* HoloLens 2 supporta i profili di fotocamera diversi. Informazioni su come [individuare e selezionare le funzionalità di fotocamera](https://docs.microsoft.com/en-us/windows/uwp/audio-video-camera/camera-profiles).
* La fotocamera supporta i profili e le risoluzioni (tutte le modalità di video sono proporzioni 16:9) seguenti:
  
  | Profilo                                         | Video     | Anteprima   | Ancora     | Frequenze dei fotogrammi | Orizzontale campo visualizzazione (H) | Utilizzo consigliato                             |
  |-------------------------------------------------|-----------|-----------|-----------|-------------|----------------------------------|---------------------------------------------|
  | Legacy,0  BalancedVideoAndPhoto,100             | 2272x1278 | 2272x1278 |           | 15,30       | 64.69                            | Registrazione video di alta qualità                |
  | Legacy,0  BalancedVideoAndPhoto,100             |           |           | 3904x2196 |             | 64.69                            | Acquisizione di foto di qualità elevata                  |
  | BalancedVideoAndPhoto,120                       | 1952x1100 | 1952x1100 | 1952x1100 | 15,30       | 64.69                            | Scenari di lunga durata                     |
  | BalancedVideoAndPhoto,120                       | 1504x846  | 1504x846  |           | 15,30       | 64.69                            | Scenari di lunga durata                     |
  | Applicazioni di videoconferenza, 100                           | 1952x1100 | 1952x1100 | 1952x1100 | 15,30,60    | 64.69                            | Videoconferenza, gli scenari di lunga durata |
  | Applicazioni di videoconferenza, 100                           | 1504x846  | 1504x846  |           | 5,15,30,60  | 64.69                            | Videoconferenza, gli scenari di lunga durata |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 1920x1080 | 1920x1080 | 1920x1080 | 15,30       | 64.69                            | Videoconferenza, gli scenari di lunga durata |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 1280x720  | 1280x720  | 1280x720  | 15,30       | 64.69                            | Videoconferenza, gli scenari di lunga durata |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 1128x635  |           |           | 15,30       | 64.69                            | Videoconferenza, gli scenari di lunga durata |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 960 x 540   |           |           | 15,30       | 64.69                            | Videoconferenza, gli scenari di lunga durata |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 760x428   |           |           | 15,30       | 64.69                            | Videoconferenza, gli scenari di lunga durata |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 640x360   |           |           | 15,30       | 64.69                            | Videoconferenza, gli scenari di lunga durata |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 500x282   |           |           | 15,30       | 64.69                            | Videoconferenza, gli scenari di lunga durata |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 424x240   |           |           | 15,30       | 64.69                            | Videoconferenza, gli scenari di lunga durata |

>[!NOTE]
>I clienti possono sfruttare [acquisizione di realtà mista](mixed-reality-capture.md) foto della tua app, tra cui ologrammi e stabilizzazione video o video.
>
>Gli sviluppatori, ci sono considerazioni che è necessario tenere conto quando si crea l'app se si desidera eseguire la ricerca ottimale, quando un cliente consente di acquisire il contenuto. È possibile anche attivare (e personalizzare) l'acquisizione di realtà mista da direttamente all'interno dell'app. Altre informazioni, vedi [mista acquisizione realtà per gli sviluppatori](mixed-reality-capture-for-developers.md).

## <a name="locating-the-device-camera-in-the-world"></a>Individuare la fotocamera del dispositivo in tutto il mondo

Quando HoloLens richiede foto e video, i frame acquisiti includono la posizione della fotocamera in tutto il mondo, come pure la proiezione prospettiva della fotocamera. Ciò consente alle applicazioni di motivo sulla posizione della fotocamera nel mondo reale per gli scenari di creazione dell'immagine ottimizzati. Gli sviluppatori possono implementare modo creativo i propri scenari usando i propri l'elaborazione di immagini preferita o librerie di visione artificiale personalizzato.

"Fotocamera" in un' posizione nella documentazione di HoloLens può fare riferimento a "gioco fotocamera virtuale" (cono l'app esegue il rendering). Se non indicato diversamente, "fotocamera" in questa pagina si intende la fotocamera di colore RGB reali.

I dettagli sulla copertina pagina [attributi di Media Foundation](https://msdn.microsoft.com/library/windows/desktop/mt740395(v=vs.85).aspx), tuttavia sono disponibili anche API per eseguire il pull della fotocamera usando le funzioni intrinseche [WinRT APIs](https://msdn.microsoft.com/library/windows/apps/windows.media.devices.core.cameraintrinsics).  

### <a name="images-with-coordinate-systems"></a>Immagini con sistemi di Coordinate

Ogni frame di immagini (se foto o video) include un sistema di coordinate, nonché due trasformazioni importanti. La "visualizzazione" Trasforma mappe dal sistema di coordinate specificato per la fotocamera e le mappe "proiezione" dalla fotocamera ai pixel nell'immagine. Insieme, queste trasformazioni definiscono per ogni pixel un raggio nello spazio 3D che rappresenta il percorso seguito dal fotoni che ha prodotto il pixel. I raggi possono essere correlati ad altri contenuti nell'app ottenendo la trasformazione dal sistema di coordinate del frame a un altro sistema di coordinate (ad esempio, da un [fotogramma di riferimento fisso](coordinate-systems.md#stationary-frame-of-reference)). Per riepilogare, ogni frame di immagini fornisce quanto segue:
* Dati di pixel (nel formato RGB/NV12/JPEG/e così via)
* 3 parti di metadati (archiviati come [IMFAttributes](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx)) che rendono ogni frame "individuabili":

|  Nome attributo  |  Type  |  GUID  |  Descrizione | 
|----------|----------|----------|----------|
|  MFSampleExtension_Spatial_CameraCoordinateSystem  |  IUnknown ([SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx))  |  {9D13C82F-2199-4E67-91CD-D1A4181F2534}  |  Archivia le [sistema di coordinate](coordinate-systems-in-directx.md) del frame acquisito | 
|  MFSampleExtension_Spatial_CameraViewTransform  |  Blob ([Matrix4x4](https://msdn.microsoft.com/library/windows/apps/windows.foundation.numerics.matrix4x4.aspx))  |  {4E251FA4-830F-4770-859A-4B8D99AA809B}  |  Archivia trasformazione estrinseche della fotocamera nel sistema di coordinate | 
|  MFSampleExtension_Spatial_CameraProjectionTransform  |  Blob ([Matrix4x4](https://msdn.microsoft.com/library/windows/apps/windows.foundation.numerics.matrix4x4.aspx))  |  {47F9FCB5-2A02-4F26-A477-792FDF95886A}  |  Archivia la trasformazione di proiezione della fotocamera | 

La trasformazione di proiezione rappresenta le proprietà intrinseche (focale, centro di proiezione, inclinare) della sezione mappato a un piano di immagine che si estende da -1 e + 1 nell'asse X e Y.

```
Matrix4x4 format          Terms
   m11 m12 m13 m14      fx    0   0   0
   m21 m22 m23 m24     skew  fy   0   0
   m31 m32 m33 m34      cx   cy   A  -1
   m41 m42 m43 m44       0    0   B   0
```

Diverse applicazioni avranno diversi sistemi di coordinate. Di seguito viene fornita una panoramica del flusso per individuare un pixel della fotocamera per una singola applicazione:

![Trasformazioni applicate a sistemi di coordinate della fotocamera](images/pvcameratransform5-500px.png)

### <a name="camera-to-application-specified-coordinate-system"></a>Fotocamera al sistema di Coordinate specificato dall'applicazione

Per passare dalla 'visualizzazione inquadratura' e 'CameraCoordinateSystem' per il sistema di coordinate world/applicazione, è necessario quanto segue:

[Fotocamera individuabile in Unity](locatable-camera-in-unity.md): CameraToWorldMatrix viene automaticamente fornito dalla classe PhotoCaptureFrame (in modo non occorre preoccuparsi di trasformazioni CameraCoordinateSystem).

[Fotocamera individuabile in DirectX](locatable-camera-in-directx.md): Viene illustrato il modo piuttosto semplice per eseguire query per la trasformazione tra il proprio coordinate system(s) dell'applicazione e sistema di coordinate della camera.

### <a name="application-specified-coordinate-system-to-pixel-coordinates"></a>Specificato dall'applicazione di sistema di Coordinate in pixel

Si supponga di che voler trovare o disegnare su un'immagine di fotocamera in una posizione specifica 3d:

Le trasformazioni di proiezione e di visualizzazione, mentre entrambe le 4x4 matrici, devono essere utilizzati in modo leggermente diverso. Vale a dire dopo aver eseguito la proiezione, uno sarebbe 'normalizzare dal w', questo passaggio aggiuntivo nella proiezione simula più posizioni 3d diverse possono finire come la stessa posizione 2d in una schermata (ad esempio qualsiasi elemento lungo un raggio determinati verrà visualizzati nello stesso pixel). Punti chiave così (nel codice dello shader):

```
// Usual 3d math:
 float4x4 WorldToCamera = inverse( CameraToWorld );
 float4 CameraSpacePos = mul( WorldToCamera, float4( WorldSpacePos.xyz, 1 ) ); // use 1 as the W component
 // Projection math:
 float4 ImagePosUnnormalized = mul( CameraProjection, float4( CameraSpacePos.xyz, 1 ) ); // use 1 as the W component
 float2 ImagePosProjected = ImagePosUnnormalized.xy / ImagePosUnnormalized.w; // normalize by W, gives -1 to 1 space
 float2 ImagePosZeroToOne = ( ImagePosProjected * 0.5 ) + float2( 0.5, 0.5 ); // good for GPU textures
 int2 PixelPos = int2( ImagePosZeroToOne.x * ImageWidth, ( 1 - ImagePosZeroToOne.y ) * ImageHeight ); // good for CPU textures
```

### <a name="pixel-to-application-specified-coordinate-system"></a>Pixel al sistema di Coordinate specificato dall'applicazione

Passando da pixel a coordinate internazionali è un po' più complicato:

```
float2 ImagePosZeroToOne = float2( PixelPos.x / ImageWidth, 1.0 - (PixelPos.y / ImageHeight ) );
 float2 ImagePosProjected = ( ( ImagePosZeroToOne * 2.0 ) - float2(1,1) ); // -1 to 1 space
 float3 CameraSpacePos = UnProjectVector( Projection, float3( ImagePosProjected, 1) );
 float3 WorldSpaceRayPoint1 = mul( CameraToWorld, float4(0,0,0,1) ); // camera location in world space
 float3 WorldSpaceRayPoint2 = mul( CameraToWorld, CameraSpacePos ); // ray point in world space
```

Si definiscono UnProject come:

```
public static Vector3 UnProjectVector(Matrix4x4 proj, Vector3 to)
 {
   Vector3 from = new Vector3(0, 0, 0);
   var axsX = proj.GetRow(0);
   var axsY = proj.GetRow(1);
   var axsZ = proj.GetRow(2);
   from.z = to.z / axsZ.z;
   from.y = (to.y - (from.z * axsY.z)) / axsY.y;
   from.x = (to.x - (from.z * axsX.z)) / axsX.x;
   return from;
 }
```

Per trovare la posizione del mondo reale di un punto, saranno necessari: world due raggi e trovare rilevandone l'intersezione o dimensioni note dei punti.

### <a name="distortion-error"></a>Errore di una distorsione

Su HoloLens, video e ancora flussi immagine sono non distorte nella pipeline di elaborazione di immagini del sistema prima che i frame vengono resi disponibili per l'applicazione (il flusso di anteprima contiene i frame distorti originali). Poiché solo la matrice di proiezione viene resa disponibile, applicazioni devono presupporre immagine frame rappresentano una fotocamera foro iniezione perfetto, tuttavia il undistortion funzionare nell'elaborazione di immagini può lasciare un errore di un massimo di 10 pixel ancora quando si utilizza la matrice di proiezione in i metadati di frame. In molti casi d'uso, questo errore verrà non è rilevante, ma se si sta eseguendo l'allineamento vntana al mondo reale poster/marcatori, ad esempio, e si nota una < 10px offset (circa 11mm per vntana posizionato 2 metri) una distorsione questo errore potrebbe essere la causa.

## <a name="locatable-camera-usage-scenarios"></a>Scenari di utilizzo della fotocamera individuabili

### <a name="show-a-photo-or-video-in-the-world-where-it-was-captured"></a>Mostra una foto o video in tutto il mondo in cui è stato acquisito

I frame fotocamera del dispositivo sono dotate di una trasformazione "Fotocamera per World", che può essere utilizzata per visualizzare esattamente dove il dispositivo è stato quando è stato creato l'immagine. Ad esempio è possibile posizionare una piccola icona holographic in questa posizione (CameraToWorld.MultiplyPoint(Vector3.zero)) e persino Disegna una freccia di poco nella direzione che la fotocamera è stata rivolta (CameraToWorld.MultiplyVector(Vector3.forward)).

### <a name="painting-the-world-using-a-camera-shader"></a>Disegno del mondo usando uno shader con fotocamera

In questa sezione si creerà un materiale 'shader con' tale i colori in tutto il mondo base in cui mostrato nella visualizzazione della fotocamera del dispositivo. In modo efficace ciò che faremo è che ogni vertice riconoscerà il percorso in relazione alla fotocamera e quindi ogni pixel utilizzeranno la matrice di proiezione' ' alla figura out quale immagine texel è associato. Infine e, facoltativamente, si sarà dissolvenza gli angoli dell'immagine in modo da renderlo più come una memoria simile a sogno:

```
// In the vertex shader:
 float4 worldSpace = mul( ObjectToWorld, float4( vertexPos.xyz, 1));
 float4 cameraSpace = mul( CameraWorldToLocal, float4(worldSpace.xyz, 1));

 // In the pixel shader:
 float4 unprojectedTex = mul( CameraProjection, float4( cameraSpace .xyz, 1));
 float2 projectedTex = (unprojectedTex.xy / unprojectedTex.w);
 float2 unitTexcoord = ((projectedTex * 0.5) + float4(0.5, 0.5, 0, 0));
 float4 cameraTextureColor = tex2D(_CameraTex, unitTexcoord);
 // Fade out edges for better look:
 float pctInView = saturate((1.0 - length(projectedTex.xy)) * 3.0);
 float4 finalColor = float4( cameraTextureColor.rgb, pctInView );
```

### <a name="tag--pattern--poster--object-tracking"></a>Modello / tag / Poster / rilevamento degli oggetti

Molte applicazioni di realtà mista utilizzano un'immagine riconoscibile o un modello visual per creare un punto tracciabile nello spazio. Viene quindi utilizzato per eseguire il rendering di oggetti rispetto a quella scegliere o creare una posizione nota. Alcuni usi di HoloLens includono ricerca di un oggetto reale contrassegnato con fiducials (ad esempio, un monitoraggio TV con un codice a matrice), posizionare vntana su fiducials e associazione visivamente con i dispositivi non HoloLens, ad esempio Tablet che sia stato configurato per comunicare con HoloLens tramite Wi-Fi.

Per riconoscere un modello visual e quindi inserire tale oggetto nello spazio complessivo delle applicazioni, è necessario alcuni aspetti:
1. Un toolkit di riconoscimento modello di tipo immagine, ad esempio codice a matrice, tag AR, finder viso, rilevazioni cerchio, OCR e così via.
2. Raccogliere i fotogrammi dell'immagine in fase di esecuzione e passarle al livello di riconoscimento
3. Unproject nei percorsi di immagine nel mondo posizioni o rays world probabile. Vedere la pagina relativa alla
4. Posizionare i modelli virtuali in queste posizioni world

Alcuni collegamenti di elaborazione immagini importanti:
* [OpenCV](http://opencv.org/)
* [Tag di codici a matrice](https://en.wikipedia.org/wiki/QR_code)
* [FaceSDK](http://research.microsoft.com/projects/facesdk/)
* [Microsoft Translator](https://www.microsoft.com/translator/business)

Mantenere un'applicazione interattiva-frequenza dei fotogrammi è critico, soprattutto quando si usano algoritmi di riconoscimento di immagini con esecuzione prolungata. Per questo motivo utilizziamo comunemente il modello seguente:
1. Thread principale: gestisce l'oggetto della fotocamera
2. Thread principale: richieste nuovo frame (asincrona)
3. Thread principale: nuovo frame di passare ai thread di rilevamento
4. Rilevamento Thread: immagine i processi per raccogliere punti chiave
5. Thread principale: modello virtuale si sposta in modo che corrisponda trovata i punti chiave
6. Thread principale: ripetere il passaggio 2

Alcuni sistemi di marcatore immagine solo forniscono un percorso singolo pixel (altri forniscono la trasformazione completa in questo caso questa sezione non sarà necessario), che equivale a un raggio di posizioni possibili. Per ottenere un'unica posizione 3d è quindi possibile sfruttare rays più e trovare il risultato finale dal loro punto di intersezione approssimativo. A tale scopo è necessario:
1. Ottenere un ciclo passando la raccolta di più immagini di fotocamera
2. Trovare il [punti di funzionalità associati](#pixel-to-application-specified-coordinate-system)e i raggi world
3. Quando si dispone di un dizionario di funzionalità, ognuno con più rays world, è possibile utilizzare il codice seguente per risolvere l'intersezione di tali raggi:

```
public static Vector3 ClosestPointBetweenRays(
   Vector3 point1, Vector3 normalizedDirection1,
   Vector3 point2, Vector3 normalizedDirection2) {
   float directionProjection = Vector3.Dot(normalizedDirection1, normalizedDirection2);
   if (directionProjection == 1) {
     return point1; // parallel lines
   }
   float projection1 = Vector3.Dot(point2 - point1, normalizedDirection1);
   float projection2 = Vector3.Dot(point2 - point1, normalizedDirection2);
   float distanceAlongLine1 = (projection1 - directionProjection * projection2) / (1 - directionProjection * directionProjection);
   float distanceAlongLine2 = (projection2 - directionProjection * projection1) / (directionProjection * directionProjection - 1);
   Vector3 pointOnLine1 = point1 + distanceAlongLine1 * normalizedDirection1;
   Vector3 pointOnLine2 = point2 + distanceAlongLine2 * normalizedDirection2;
   return Vector3.Lerp(pointOnLine2, pointOnLine1, 0.5f);
 }
```

Ha due o più posizioni di tag rilevate, è possibile posizionare una scena modelled per adattare lo scenario corrente degli utenti. Se non è possibile presupporre la gravità, è necessario tre posizioni di tag. In molti casi che si usa una combinazione di colori semplice in cui sfere bianche rappresentano in tempo reale rilevati percorsi di tag e sfere blu rappresentano posizioni tag modellati, ciò consente all'utente di valutare visivamente la qualità di allineamento. Si presuppone che la configurazione seguente in tutte le applicazioni:
* Due o più posizioni modellate tag
* Una "area di calibrazione" che, nella scena, è il padre dei tag
* Identificatore delle funzionalità della fotocamera
* Comportamento che consente di spostare lo spazio di calibrazione per allineare i tag modelled con i tag in tempo reale (siamo attenzione spostare lo spazio di padre, non i marcatori modelled se stessi, perché altri connect è posizioni rispetto a essi).

```
// In the two tags case:
 Vector3 idealDelta = (realTags[1].EstimatedWorldPos - realTags[0].EstimatedWorldPos);
 Vector3 curDelta = (modelledTags[1].transform.position - modelledTags[0].transform.position);
 if (IsAssumeGravity) {
   idealDelta.y = 0;
   curDelta.y = 0;
 }
 Quaternion deltaRot = Quaternion.FromToRotation(curDelta, idealDelta);
 trans.rotation = Quaternion.LookRotation(deltaRot * trans.forward, trans.up);
 trans.position += realTags[0].EstimatedWorldPos - modelledTags[0].transform.position;
```

### <a name="render-holograms-from-the-cameras-position"></a>Eseguire il rendering vntana dalla posizione della fotocamera

Nota: Se si sta tentando di creare il proprio [mista acquisizione realtà (MRC)](mixed-reality-capture.md), che combina vntana con il flusso della fotocamera, è possibile utilizzare il [effetti MRC](mixed-reality-capture-for-developers.md) oppure abilitare la proprietà showHolograms in [ Fotocamera individuabile in Unity](locatable-camera-in-unity.md).

Se vuoi eseguire un rendering direttamente nel flusso di fotocamera RGB speciale, è possibile eseguire il rendering vntana nello spazio dalla posizione della Camera sincronizzato con un feed di video per fornire un'anteprima dinamica/registrazione ologrammi personalizzato.

In Skype, facciamo questa opzione per mostrare il client remoto di ciò che viene visualizzato all'utente di HoloLens e consentire loro di interagire con la stessa vntana. Prima dell'invio in ogni intervallo di video tramite il servizio di Skype, si ottiene dati fotocamera corrispondenti di ogni fotogramma. Abbiamo quindi pacchetto metadati estrinseche e intrinseco della fotocamera, il frame video e quindi inviarlo tramite il servizio di Skype.

Sul lato ricevente, con Unity, è stato già sincronizzati tutti vntana nello spazio dell'utente HoloLens utilizzando lo stesso sistema di coordinate. Ciò consente di usare i metadati estrinseche della fotocamera per posizionare la fotocamera di Unity in alla posizione esatta del mondo (rispetto al resto del vntana) che l'utente di HoloLens è stato permanente quando quel frame video è stato acquisito e usare le informazioni di intrinseco della fotocamera per Verificare che la visualizzazione è lo stesso.

Dopo aver ottenuto la fotocamera impostato in modo corretto, si combina quali vntana vede la fotocamera nel frame che sono stati ricevuti dal Skype, creazione di una vista di realtà mista di ciò che l'utente di HoloLens rileva utilizzo Graphics.Blit.

```cs
private void OnFrameReceived(Texture frameTexture, Vector3 cameraPosition, Quaternion cameraRotation, Matrix4x4 cameraProjectionMatrix)
{
    //set material that will be blitted onto the RenderTexture
    this.compositeMaterial.SetTexture(CompositeRenderer.CameraTextureMaterialProperty, frameTexture);
    //set the camera to be that of the HoloLens's device camera
    this.Camera.transform.position = cameraPosition;
    this.Camera.transform.rotation = cameraRotation;
    this.Camera.projectionMatrix = cameraProjectionMatrix;
    //trigger the Graphics's Blit now that the frame and camera are set up
    this.TextureReady = false;
}
private void OnRenderImage(RenderTexture source, RenderTexture destination)
{
    if (!this.TextureReady)
    {
        Graphics.Blit(source, destination, this.compositeMaterial);
        this.TextureReady = true;
    }
}
```

### <a name="track-or-identify-tagged-stationary-or-moving-real-world-objectsfaces-using-leds-or-other-recognizer-libraries"></a>Track o identificare fermo contrassegnata o in movimento del mondo reale oggetti/visi usando i LED o altre librerie di sistema di riconoscimento

Esempi:
* Controllare i robot industriali con LED (o gli oggetti di codici a matrice per lo spostamento di più lenta)
* Individuare e riconoscere gli oggetti nella chat room
* Identificare e riconoscere le persone nella chat room (ad esempio luogo holographic biglietti da visita su facce)

## <a name="see-also"></a>Vedere anche
* [Fotocamera individuabile in DirectX](locatable-camera-in-directx.md)
* [Fotocamera individuabile in Unity](locatable-camera-in-unity.md)
* [Acquisizione realtà mista](mixed-reality-capture.md)
* [Acquisizione realtà mista per sviluppatori](mixed-reality-capture-for-developers.md)
* [Introduzione di acquisizione di Media](https://msdn.microsoft.com/library/windows/apps/mt243896.aspx)

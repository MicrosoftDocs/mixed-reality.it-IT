---
title: Fotocamera individuabile
description: Informazioni generali sulla fotocamera anteriore HoloLens, come funziona e i profili e le soluzioni disponibili per gli sviluppatori.
author: cdedmonds
ms.author: wguyman, cdedmonds
ms.date: 06/12/2019
ms.topic: article
keywords: fotocamera, hololens, fotocamera, colore di primo piano con connessione
ms.openlocfilehash: f661fc82fbeab9a870e8ccf7044c9bb375bed7e3
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326294"
---
# <a name="locatable-camera"></a>Fotocamera individuabile

HoloLens include una fotocamera posta sul world nella parte anteriore del dispositivo che consente alle app di vedere ciò che viene visualizzato all'utente. Gli sviluppatori hanno accesso e controllo della fotocamera, esattamente come accade per le fotocamere colore su Smartphone, portatili o desktop. Le stesse finestre universale [acquisizione di media](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx) e foundation supporti windows API utilizzabili sui desktop e mobile funzionano HoloLens. Unity [è anche eseguito il wrapping di queste finestre API](locatable-camera-in-unity.md) astrarre semplice utilizzo della fotocamera su HoloLens per le attività, ad esempio tenendo regolari foto e video (con o senza vntana) e individuare la posizione della fotocamera in e prospettiva nel scena.

## <a name="device-camera-information"></a>Informazioni dispositivo della fotocamera

### <a name="hololens-first-generation"></a>HoloLens (prima generazione)

* Fotocamera foto/video (PV) lo stato attivo predefinito, con bilanciamento automatico del bianco, l'esposizione automatica e pipe di elaborazione di immagini completi
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

* Fotocamera foto/video (PV) e messa a fuoco, con bilanciamento automatico del bianco, l'esposizione automatica e pipe di elaborazione di immagini completi
* LED di Privacy white rivolta verso il mondo si accende ogni volta che la fotocamera è attiva
* La fotocamera supporta le modalità seguenti (tutte le modalità di video sono proporzioni 16:9):

  >[!NOTE]
  >Queste modalità sono soggetti a modifiche prima della disponibilità generale di HoloLens 2.

  |  Video  |  Anteprima  |  Ancora  |  Frequenze dei fotogrammi  |  Orizzontale campo visualizzazione (H) |  Utilizzo consigliato | 
  |----------|----------|----------|----------|----------|----------|
  |  1920x1080 |  1920x1080 |  N/D |  30, 15 fps  |  54deg  |  (modalità predefinita con la stabilizzazione video) | 
  |  N/D |  N/D |  3904X2196 |  N/D  |  64deg |  Immagini più elevata risoluzione | 
  |  2272x1278 |  2272x1278 |  N/D |  30, 15 fps  |  64deg |  Risoluzione overscan (riempimento) prima di stabilizzazione video | 
  |  1952x1100 |  1952x1100 |  1952x1100  |  30, 15 fps  |  64deg |  Alta qualità di streaming | 
  |  1280x720 |  1280x720 |  N/D |  30, 15, 5 fps  |  64deg |  Modalità di bassa alimentazione/risoluzione per lo streaming e l'attività di elaborazione di immagini | 

## <a name="locating-the-device-camera-in-the-world"></a>Individuare la fotocamera del dispositivo in tutto il mondo

Quando HoloLens richiede foto e video, i frame acquisiti includono la posizione della fotocamera in tutto il mondo, nonché il modello di obiettivo della camera. Ciò consente alle applicazioni di motivo sulla posizione della fotocamera nel mondo reale per gli scenari di creazione dell'immagine ottimizzati. Gli sviluppatori possono implementare modo creativo i propri scenari usando i propri l'elaborazione di immagini preferita o librerie di visione artificiale personalizzato.

"Fotocamera" in un' posizione nella documentazione di HoloLens può fare riferimento a "gioco fotocamera virtuale" (cono l'app esegue il rendering). Se non indicato diversamente, "fotocamera" in questa pagina si intende la fotocamera di colore RGB reali.

I dettagli su questa pagina cover utilizzando il [MediaFrameReference](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.mediaframereference) classe, tuttavia sono disponibili anche API a pull fotocamera intrinseci e i percorsi usando [Media Foundation attributi](https://msdn.microsoft.com/library/windows/desktop/mt740395(v=vs.85).aspx). Consultare il [viso Holographic esempio rilevamento](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking) per altre informazioni.

### <a name="images-with-coordinate-systems"></a>Immagini con sistemi di Coordinate

Ogni frame di immagini (se foto o video) include un' [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) rooted in corrispondenza della fotocamera al momento dell'acquisizione di cui è possibile accedere tramite il [sistema di coordinate](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.mediaframereference.coordinatesystem#Windows_Media_Capture_Frames_MediaFrameReference_CoordinateSystem) proprietà di [MediaFrameReference](https://docs.microsoft.com/en-us/uwp/api/Windows.Media.Capture.Frames.MediaFrameReference). Inoltre, ogni fotogramma contiene una descrizione del modello di obiettivo della fotocamera che può trovarsi nel [CameraIntrinsics](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) proprietà. Insieme, queste trasformazioni definiscono per ogni pixel un raggio nello spazio 3D che rappresenta il percorso seguito dal fotoni che ha prodotto il pixel. I raggi possono essere correlati ad altri contenuti nell'app ottenendo la trasformazione dal sistema di coordinate del frame a un altro sistema di coordinate (ad esempio, da un [fotogramma di riferimento fisso](coordinate-systems.md#stationary-frame-of-reference)). Per riepilogare, ogni frame di immagini fornisce quanto segue:
* Dati di pixel (nel formato RGB/NV12/JPEG/e così via)
* Oggetto [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) dal percorso di acquisizione
* Oggetto [CameraIntrinsics](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) classe che contiene la modalità dell'obiettivo della fotocamera

### <a name="camera-to-application-specified-coordinate-system"></a>Fotocamera al sistema di Coordinate specificato dall'applicazione

Per passare dal 'CameraIntrinsics' e 'CameraCoordinateSystem' per il sistema di coordinate world/applicazione, è necessario quanto segue:

[Fotocamera individuabile in Unity](locatable-camera-in-unity.md): CameraToWorldMatrix viene automaticamente fornito dalla classe PhotoCaptureFrame (in modo non occorre preoccuparsi di trasformazioni CameraCoordinateSystem).

[Fotocamera individuabile in DirectX](locatable-camera-in-directx.md): Viene illustrato il modo piuttosto semplice per eseguire query per la trasformazione tra il proprio coordinate system(s) dell'applicazione e sistema di coordinate della camera.

### <a name="distortion-error"></a>Errore di una distorsione

Su HoloLens, video e ancora flussi immagine sono non distorte nella pipeline di elaborazione di immagini del sistema prima che i frame vengono resi disponibili per l'applicazione (il flusso di anteprima contiene i frame distorti originali). Perché solo il CameraIntrinsics vengono resi disponibili, applicazioni devono presupporre immagine frame rappresentano una fotocamera foro iniezione perfetto, tuttavia il undistortion funzionare nell'elaborazione di immagini possono comunque mantenere un errore di un massimo di 10 pixel nella HoloLens (prima generazione) Quando si usa il CameraIntrinsics nei metadati del frame. In molti casi d'uso, questo errore verrà non è rilevante, ma se si sta eseguendo l'allineamento vntana al mondo reale poster/marcatori, ad esempio, e si nota una < 10px offset (circa 11mm per vntana posizionato 2 metri) una distorsione questo errore potrebbe essere la causa. 

## <a name="locatable-camera-usage-scenarios"></a>Scenari di utilizzo della fotocamera individuabili

### <a name="show-a-photo-or-video-in-the-world-where-it-was-captured"></a>Mostra una foto o video in tutto il mondo in cui è stato acquisito

I frame fotocamera del dispositivo sono dotate di una trasformazione "Fotocamera per World", che può essere utilizzata per visualizzare esattamente dove il dispositivo è stato quando è stato creato l'immagine. Ad esempio è possibile posizionare una piccola icona holographic in questa posizione (CameraToWorld.MultiplyPoint(Vector3.zero)) e persino Disegna una freccia di poco nella direzione che la fotocamera è stata rivolta (CameraToWorld.MultiplyVector(Vector3.forward)).

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
2. Trovare i punti di funzionalità associata e i raggi world
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
* [Esempio di rilevamento viso holographic](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)

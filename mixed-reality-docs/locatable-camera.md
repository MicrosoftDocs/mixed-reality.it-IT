---
title: Fotocamera individuabile
description: Informazioni generali sulla fotocamera HoloLens front-end, il suo funzionamento e i profili e le risoluzioni disponibili per gli sviluppatori.
author: cdedmonds
ms.author: wguyman
ms.date: 06/12/2019
ms.topic: article
keywords: fotocamera, hololens, fotocamera a colori, anteriore, hololens 2, CV, visione artificiale, fiduciale, marcatori, codice a matrice, QR, foto, video
ms.openlocfilehash: e158eb2e708164cbd68620f3f46d3039c2eaa730
ms.sourcegitcommit: 4282d92e93869e4829338bdf7d981c3ee0260bfd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85216222"
---
# <a name="locatable-camera"></a>Fotocamera individuabile

HoloLens include una fotocamera riguardante il mondo montata sulla parte anteriore del dispositivo, che consente alle app di visualizzare i dati visualizzati dall'utente. Gli sviluppatori possono accedere e controllare la fotocamera, proprio come per le fotocamere a colori su smartphone, portatili o desktop. Le stesse API Windows [Media Capture](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx) e Windows Media Foundation che funzionano su lavoro per dispositivi mobili e desktop in HoloLens. Unity [ha inoltre eseguito il wrapper di queste API Windows](locatable-camera-in-unity.md) per astrarre un semplice utilizzo della fotocamera in HoloLens per attività quali l'esecuzione di foto e video regolari (con o senza ologrammi) e l'individuazione della posizione della fotocamera in e della prospettiva sulla scena.

## <a name="device-camera-information"></a>Informazioni sulla fotocamera del dispositivo

### <a name="hololens-first-generation"></a>HoloLens (prima generazione)

* Fotocamera fissa foto/video (PV) con bilanciamento del carico automatico, esposizione automatica e pipeline per l'elaborazione di immagini complete.
* Il LED per la privacy bianca per il mondo si illuminerà ogni volta che la fotocamera è attiva
* La videocamera supporta le modalità seguenti (tutte le modalità sono 16:9 proporzioni) a 30, 24, 20, 15 e 5 fps:

  |  Video  |  Anteprima  |  Ancora  |  Campo di visualizzazione orizzontale (H-FOV) |  Utilizzo suggerito | 
  |----------|----------|----------|----------|----------|
  |  1280x720 |  1280x720 |  1280x720 |  45deg  |  (modalità predefinita con stabilizzazione video) | 
  |  N/D |  N/D |  2048x1152 |  67deg |  Immagine ancora a risoluzione massima | 
  |  1408x792 |  1408x792 |  1408x792 |  48deg |  Risoluzione Overscan (riempimento) prima della stabilizzazione del video | 
  |  1344x756 |  1344x756 |  1344x756 |  67deg |  Modalità video FOV grande con overscan | 
  |  896x504 |  896x504 |  896x504 |  48deg |  Bassa potenza/modalità di risoluzione bassa per le attività di elaborazione delle immagini | 

### <a name="hololens-2"></a>HoloLens 2

* Fotocamera con messa a fuoco automatica per foto/video (PV) con bilanciamento del carico automatico, esposizione automatica e pipeline per l'elaborazione di immagini complete.
* Il LED per la privacy bianca per il mondo si illuminerà ogni volta che la fotocamera è attiva.
* HoloLens 2 supporta diversi profili fotocamera. Informazioni su come [individuare e selezionare le funzionalità della fotocamera](https://docs.microsoft.com//windows/uwp/audio-video-camera/camera-profiles).
* La videocamera supporta i profili e le risoluzioni seguenti (tutte le modalità video sono 16:9 proporzioni):
  
  | Profilo                                         | Video     | Anteprima   | Ancora     | Frequenza fotogrammi | Campo di visualizzazione orizzontale (H-FOV) | Utilizzo suggerito                             |
  |-------------------------------------------------|-----------|-----------|-----------|-------------|----------------------------------|---------------------------------------------|
  | Legacy, 0 BalancedVideoAndPhoto, 100             | 2272x1278 | 2272x1278 |           | 15, 30       | 64,69                            | Registrazione video di alta qualità                |
  | Legacy, 0 BalancedVideoAndPhoto, 100             | 896x504   | 896x504   |           | 15, 30       | 64,69                            | Flusso di anteprima per acquisizione foto di alta qualità |
  | Legacy, 0 BalancedVideoAndPhoto, 100             |           |           | 3904x2196 |             | 64,69                            | Acquisizione foto di alta qualità                  |
  | BalancedVideoAndPhoto, 120                       | 1952x1100 | 1952x1100 | 1952x1100 | 15, 30       | 64,69                            | Scenari a lunga durata                     |
  | BalancedVideoAndPhoto, 120                       | 1504x846  | 1504x846  |           | 15, 30       | 64,69                            | Scenari a lunga durata                     |
  | Videoconferenza, 100                           | 1952x1100 | 1952x1100 | 1952x1100 | 15, 30, 60    | 64,69                            | Conferenze video, scenari con lunga durata |
  | Videoconferenza, 100                           | 1504x846  | 1504x846  |           | 5, 15, 30, 60  | 64,69                            | Conferenze video, scenari con lunga durata |
  | Videoconferenza, 100 BalancedVideoAndPhoto, 120 | 1920x1080 | 1920x1080 | 1920x1080 | 15, 30       | 64,69                            | Conferenze video, scenari con lunga durata |
  | Videoconferenza, 100 BalancedVideoAndPhoto, 120 | 1280x720  | 1280x720  | 1280x720  | 15, 30       | 64,69                            | Conferenze video, scenari con lunga durata |
  | Videoconferenza, 100 BalancedVideoAndPhoto, 120 | 1128x636  |           |           | 15, 30       | 64,69                            | Conferenze video, scenari con lunga durata |
  | Videoconferenza, 100 BalancedVideoAndPhoto, 120 | 960x540   |           |           | 15, 30       | 64,69                            | Conferenze video, scenari con lunga durata |
  | Videoconferenza, 100 BalancedVideoAndPhoto, 120 | 760x428   |           |           | 15, 30       | 64,69                            | Conferenze video, scenari con lunga durata |
  | Videoconferenza, 100 BalancedVideoAndPhoto, 120 | 640x360   |           |           | 15, 30       | 64,69                            | Conferenze video, scenari con lunga durata |
  | Videoconferenza, 100 BalancedVideoAndPhoto, 120 | 500x282   |           |           | 15, 30       | 64,69                            | Conferenze video, scenari con lunga durata |
  | Videoconferenza, 100 BalancedVideoAndPhoto, 120 | 424x240   |           |           | 15, 30       | 64,69                            | Conferenze video, scenari con lunga durata |

>[!NOTE]
>I clienti possono sfruttare la funzionalità di [acquisizione di realtà mista](mixed-reality-capture.md) per scattare video o foto dell'app, tra cui ologrammi e stabilizzazione video.
>
>In qualità di sviluppatore, è necessario tenere conto di quando si crea l'app se si vuole che l'app risulti più adatta possibile quando un cliente acquisisce il contenuto. È anche possibile abilitare e personalizzare l'acquisizione di realtà mista direttamente dall'interno dell'app. Scopri di più su [acquisizione di realtà mista per gli sviluppatori](mixed-reality-capture-for-developers.md).

## <a name="locating-the-device-camera-in-the-world"></a>Individuazione della fotocamera del dispositivo nel mondo

Quando HoloLens acquisisce foto e video, i frame acquisiti includono il percorso della fotocamera nel mondo, oltre al modello di obiettivo della fotocamera. Questo consente alle applicazioni di ragionare sulla posizione della fotocamera nel mondo reale per gli scenari di creazione di immagini potenziati. Gli sviluppatori possono eseguire il Rolling dei propri scenari in modo creativo usando l'elaborazione di immagini preferite o librerie personalizzate per la visione del computer.

"La fotocamera" altrove nella documentazione di HoloLens può riferirsi alla "fotocamera virtuale del gioco" (tronco a cui viene eseguito il rendering dell'app). Se non indicato diversamente, "camera" in questa pagina si riferisce alla fotocamera a colori RGB del mondo reale.

### <a name="using-unity"></a>Uso di Unity

Per passare da "CameraIntrinsics" e "CameraCoordinateSystem" al sistema di coordinate dell'applicazione o del mondo, seguire le istruzioni riportate nell'articolo sulla [fotocamera di locatable in Unity](locatable-camera-in-unity.md) .  CameraToWorldMatrix viene fornito automaticamente dalla classe PhotoCaptureFrame e pertanto non è necessario preoccuparsi delle trasformazioni CameraCoordinateSystem descritte di seguito.

### <a name="using-mediaframereference"></a>Uso di MediaFrameReference

Queste istruzioni si applicano se si usa la classe [MediaFrameReference](https://docs.microsoft.com//uwp/api/windows.media.capture.frames.mediaframereference) per leggere i frame immagine dalla fotocamera.

Ogni fotogramma immagine (foto o video) include un [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) radice alla fotocamera al momento dell'acquisizione, a cui è possibile accedere usando la proprietà [CoordinateSystem](https://docs.microsoft.com//uwp/api/windows.media.capture.frames.mediaframereference.coordinatesystem#Windows_Media_Capture_Frames_MediaFrameReference_CoordinateSystem) di [MediaFrameReference](https://docs.microsoft.com//uwp/api/Windows.Media.Capture.Frames.MediaFrameReference). Ogni frame contiene inoltre una descrizione del modello di obiettivo della fotocamera, che è possibile trovare nella proprietà [CameraIntrinsics](https://docs.microsoft.com//uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) . Insieme, queste trasformazioni definiscono per ogni pixel un raggio nello spazio 3D che rappresenta il percorso utilizzato dai fotoni che hanno prodotto il pixel. Questi raggi possono essere correlati ad altro contenuto nell'app ottenendo la trasformazione dal sistema di coordinate del frame a un altro sistema di coordinate, ad esempio da un [frame di riferimento](coordinate-systems.md#stationary-frame-of-reference)fisso. Per riepilogare, ogni frame dell'immagine offre quanto segue:
* Dati pixel (in formato RGB/NV12/JPEG/ecc.)
* [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) dalla posizione di acquisizione
* Classe [CameraIntrinsics](https://docs.microsoft.com//uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) che contiene la modalità Lens della fotocamera

Nell' [esempio HolographicFaceTracking](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking) viene illustrato il modo piuttosto semplice per eseguire una query per la trasformazione tra il sistema di coordinate della fotocamera e i sistemi di coordinate dell'applicazione.

### <a name="using-media-foundation"></a>Utilizzo di Media Foundation

Se si usa direttamente Media Foundation per leggere i frame di immagini dalla fotocamera, è possibile usare l' [attributo MFSampleExtension_CameraExtrinsics](https://docs.microsoft.com/windows/win32/medfound/mfsampleextension-cameraextrinsics) di ogni frame e [MFSampleExtension_PinholeCameraIntrinsics attributo](https://docs.microsoft.com/windows/win32/medfound/mfsampleextension-pinholecameraintrinsics) per individuare i frame della fotocamera rispetto agli altri sistemi di coordinate dell'applicazione, come illustrato nel codice di esempio seguente:

```cpp
#include <winrt/windows.perception.spatial.preview.h>
#include <mfapi.h>
#include <mfidl.h>
 
using namespace winrt::Windows::Foundation;
using namespace winrt::Windows::Foundation::Numerics;
using namespace winrt::Windows::Perception;
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
 
class CameraFrameLocator
{
public:
    struct CameraFrameLocation
    {
        SpatialCoordinateSystem CoordinateSystem;
        float4x4 CameraViewToCoordinateSytemTransform;
        MFPinholeCameraIntrinsics Intrinsics;
    };
 
    std::optional<CameraFrameLocation> TryLocateCameraFrame(IMFSample* pSample)
    {
        MFCameraExtrinsics cameraExtrinsics;
        MFPinholeCameraIntrinsics cameraIntrinsics;
        UINT32 sizeCameraExtrinsics = 0;
        UINT32 sizeCameraIntrinsics = 0;
        UINT64 sampleTimeHns = 0;
 
        // query sample for calibration and validate
        if (FAILED(pSample->GetUINT64(MFSampleExtension_DeviceTimestamp, &sampleTimeHns)) ||
            FAILED(pSample->GetBlob(MFSampleExtension_CameraExtrinsics, (UINT8*)& cameraExtrinsics, sizeof(cameraExtrinsics), &sizeCameraExtrinsics)) ||
            FAILED(pSample->GetBlob(MFSampleExtension_PinholeCameraIntrinsics, (UINT8*)& cameraIntrinsics, sizeof(cameraIntrinsics), &sizeCameraIntrinsics)) ||
            (sizeCameraExtrinsics != sizeof(cameraExtrinsics)) ||
            (sizeCameraIntrinsics != sizeof(cameraIntrinsics)) ||
            (cameraExtrinsics.TransformCount == 0))
        {
            return std::nullopt;
        }
 
        // compute extrinsic transform
        const auto& calibratedTransform = cameraExtrinsics.CalibratedTransforms[0];
        const GUID& dynamicNodeId = calibratedTransform.CalibrationId;
        const float4x4 cameraToDynamicNode =
            make_float4x4_from_quaternion(quaternion{ calibratedTransform.Orientation.x, calibratedTransform.Orientation.y, calibratedTransform.Orientation.z, calibratedTransform.Orientation.w }) *
            make_float4x4_translation(calibratedTransform.Position.x, calibratedTransform.Position.y, calibratedTransform.Position.z);
 
        // update locator cache for dynamic node
        if (dynamicNodeId != m_currentDynamicNodeId || !m_locator)
        {
            m_locator = SpatialGraphInteropPreview::CreateLocatorForNode(dynamicNodeId);
            if (!m_locator)
            {
                return std::nullopt;
            }
 
            m_frameOfReference = m_locator.CreateAttachedFrameOfReferenceAtCurrentHeading();
            m_currentDynamicNodeId = dynamicNodeId;
        }
 
        // locate dynamic node
        auto timestamp = PerceptionTimestampHelper::FromSystemRelativeTargetTime(TimeSpan{ sampleTimeHns });
        auto coordinateSystem = m_frameOfReference.GetStationaryCoordinateSystemAtTimestamp(timestamp);
        auto location = m_locator.TryLocateAtTimestamp(timestamp, coordinateSystem);
        if (!location)
        {
            return std::nullopt;
        }
 
        const float4x4 dynamicNodeToCoordinateSystem = make_float4x4_from_quaternion(location.Orientation()) * make_float4x4_translation(location.Position());
 
        return CameraFrameLocation{ coordinateSystem, cameraToDynamicNode * dynamicNodeToCoordinateSystem, cameraIntrinsics };
    }

private:
    GUID m_currentDynamicNodeId{ GUID_NULL };
    SpatialLocator m_locator{ nullptr };
    SpatialLocatorAttachedFrameOfReference m_frameOfReference{ nullptr };
};
```

### <a name="distortion-error"></a>Errore di distorsione

In HoloLens il video e i flussi di immagini ancora non sono distorti nella pipeline di elaborazione delle immagini del sistema prima che i frame siano resi disponibili per l'applicazione (il flusso di anteprima contiene i frame distorti originali). Poiché vengono resi disponibili solo i CameraIntrinsics, le applicazioni devono presupporre che i fotogrammi immagine rappresentino una fotocamera pinhole perfetta.

In HoloLens (prima generazione) la funzione di disdistorsione nel processore di immagini può comunque lasciare un errore fino a 10 pixel quando si usa il CameraIntrinsics nei metadati del frame. In molti casi d'uso, questo errore non è rilevante, ma se si allineano gli ologrammi a manifesti/marcatori reali, ad esempio, si nota un <offset 10px (approssimativamente 11mm per gli ologrammi posizionati a 2 metri), questo errore di distorsione potrebbe essere la ragione. 

## <a name="locatable-camera-usage-scenarios"></a>Scenari di utilizzo della fotocamera locatable

### <a name="show-a-photo-or-video-in-the-world-where-it-was-captured"></a>Mostra una foto o un video nel mondo in cui è stato acquisito

I frame della fotocamera del dispositivo presentano una trasformazione "da fotocamera a mondo", che può essere usata per visualizzare esattamente il punto in cui si trovava il dispositivo quando l'immagine è stata acquisita. Ad esempio, è possibile posizionare una piccola icona olografica in questa posizione (CameraToWorld. MultiplyPoint (Vector3. zero)) e persino creare una piccola freccia nella direzione della fotocamera (CameraToWorld. MultiplyVector (Vector3. avanti)).

### <a name="tag--pattern--poster--object-tracking"></a>Rilevamento di Tag/modelli/poster/oggetti

Molte applicazioni di realtà mista usano un'immagine riconoscibile o un modello visivo per creare un punto di rilevamento nello spazio. Questa operazione viene quindi utilizzata per eseguire il rendering degli oggetti relativi a tale punto o creare un percorso noto. Alcuni usi per HoloLens includono la ricerca di un oggetto reale con tag fiducials (ad esempio, un monitor TV con codice a matrice), il posizionamento di ologrammi su fiducials e l'associazione visiva di dispositivi non HoloLens come i tablet che sono stati impostati per comunicare con HoloLens tramite Wi-Fi.

Per riconoscere un modello visivo e quindi inserire l'oggetto nello spazio globale delle applicazioni, è necessario eseguire alcune operazioni:
1. Un toolkit di riconoscimento delle immagini, ad esempio codice a matrice, tag AR, ricerca viso, Tracker Circle, OCR e così via.
2. Raccogliere i frame dell'immagine in fase di esecuzione e passarli al livello di riconoscimento
3. Riportare i percorsi delle immagini nelle posizioni internazionali o nei possibili raggi internazionali. 
4. Posizionare i modelli virtuali in queste posizioni internazionali

Alcuni collegamenti importanti per l'elaborazione delle immagini:
* [OpenCV](https://opencv.org/)
* [Tag QR](https://en.wikipedia.org/wiki/QR_code)
* [FaceSDK](https://research.microsoft.com/projects/facesdk/)
* [Microsoft Translator](https://www.microsoft.com/translator/business)

Mantenere una frequenza dei fotogrammi dell'applicazione interattiva è fondamentale, soprattutto quando si gestiscono algoritmi di riconoscimento delle immagini con esecuzione prolungata. Per questo motivo, viene comunemente usato il modello seguente:
1. Thread principale: gestisce l'oggetto fotocamera
2. Thread principale: richieste nuovi frame (asincrono)
3. Thread principale: passa nuovi frame al thread di rilevamento
4. Thread di rilevamento: elabora l'immagine per raccogliere punti chiave
5. Thread principale: sposta il modello virtuale in modo che corrisponda ai punti chiave trovati
6. Thread principale: ripetere il passaggio 2

Alcuni sistemi di marcatori di immagini forniscono solo una posizione in un singolo pixel (altri forniscono la trasformazione completa, nel qual caso questa sezione non sarà necessaria), che corrisponde a un raggio di posizioni possibili. Per accedere a una singola posizione 3D, è possibile sfruttare più raggi e trovare il risultato finale in base all'intersezione approssimativa. A tale scopo è necessario:
1. Ottenere un ciclo per la raccolta di più immagini della fotocamera
2. Individuare i punti di funzionalità associati e i relativi raggi internazionali
3. Quando si dispone di un dizionario di funzionalità, ognuna con più raggi internazionali, è possibile usare il codice seguente per risolvere l'intersezione dei raggi:

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

Date due o più posizioni dei tag rilevati, è possibile posizionare una scena modellata in modo da adattarsi allo scenario corrente dell'utente. Se non è possibile presupporre gravità, saranno necessari tre percorsi di tag. In molti casi, si usa una combinazione di colori semplice in cui le sfere bianche rappresentano posizioni dei tag rilevati in tempo reale e le sfere blu rappresentano i percorsi dei tag modellati. Ciò consente all'utente di misurare visivamente la qualità dell'allineamento. Si presuppone che la configurazione seguente sia in tutte le applicazioni:
* Due o più percorsi di tag modellati
* Uno "spazio di calibrazione" che nella scena è l'elemento padre dei tag
* Identificatore funzionalità fotocamera
* Comportamento che sposta lo spazio di calibrazione per allineare i tag modellati con i tag in tempo reale (è necessario spostare lo spazio padre, non i marcatori modellati in modo autonomo, perché altre connessioni sono posizioni relative a esse).

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

### <a name="track-or-identify-tagged-stationary-or-moving-real-world-objectsfaces-using-leds-or-other-recognizer-libraries"></a>Tenere traccia o identificare gli oggetti o i visi del mondo reale con tag con i LED o altre librerie di riconoscimento

Esempi:
* Robot industriali con LED (o codici a matrice per oggetti mobili più lenti)
* Identificare e riconoscere gli oggetti nella chat room
* Identificare e riconoscere persone nella stanza (ad esempio, inserire schede di contatto olografiche sui visi)

## <a name="see-also"></a>Vedere anche
* [Esempio di fotocamera locatable](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)
* [Fotocamera individuabile in Unity](locatable-camera-in-unity.md)
* [Acquisizione di realtà mista](mixed-reality-capture.md)
* [Acquisizione realtà mista per sviluppatori](mixed-reality-capture-for-developers.md)
* [Introduzione a Media Capture](https://msdn.microsoft.com/library/windows/apps/mt243896.aspx)
* [Esempio di rilevamento facciale olografico](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)

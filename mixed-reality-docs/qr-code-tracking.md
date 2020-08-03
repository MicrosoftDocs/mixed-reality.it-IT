---
title: Rilevamento di codici a matrice
description: Informazioni su come rilevare i codici a matrice in HoloLens 2.
author: dorreneb
ms.author: dobrown
ms.date: 05/15/2019
ms.topic: article
keywords: VR, LBE, location based Entertainment, VR Arcade, Arcade, immersive, QR, QR code, hololens2
ms.openlocfilehash: 6d3dc442c28e498cc00e14325398de2026261a17
ms.sourcegitcommit: ef0bf03833eda826ed0b884859b4573775112aba
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2020
ms.locfileid: "87476763"
---
# <a name="qr-code-tracking"></a>Rilevamento di codici a matrice

HoloLens 2 è in grado di rilevare i codici a matrice nell'ambiente intorno all'auricolare, stabilendo un sistema di coordinate in base alla posizione reale del codice.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Funzionalità</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (prima generazione)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td> Rilevamento del codice a matrice</td><td style="text-align: center;">️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;">✔️</td>
</tr>
</table>

>[!NOTE]
>Il rilevamento del codice a matrice con auricolari a realtà mista di Windows su PC desktop è supportato in Windows 10 versione 2004 e successive. Usare l'API Microsoft. MixedReality. QRCodeWatcher. non supportata () per determinare se la funzionalità è supportata nel dispositivo corrente.

## <a name="getting-the-qr-package"></a>Recupero del pacchetto QR
È possibile scaricare il pacchetto NuGet per il rilevamento del codice QR [qui](https://nuget.org/Packages/Microsoft.MixedReality.QR).

## <a name="detecting-qr-codes"></a>Rilevamento di codici QR

### <a name="adding-the-webcam-capability"></a>Aggiunta della funzionalità webcam
Per rilevare i codici QR, è necessario aggiungere la funzionalità `webcam` al manifesto. Questa funzionalità è necessaria perché i dati nei codici rilevati nell'ambiente dell'utente possono contenere informazioni riservate.

È possibile richiedere l'autorizzazione chiamando `QRCodeWatcher.RequestAccessAsync()` :

_C#_
```cs
await QRCodeWatcher.RequestAccessAsync();
```

_C++_
```cpp
co_await QRCodeWatcher.RequestAccessAsync();
```

Prima di creare un oggetto QRCodeWatcher, è necessario richiedere l'autorizzazione.

Sebbene il rilevamento del codice a matrice richieda la `webcam` funzionalità, il rilevamento si verifica usando le fotocamere di rilevamento del dispositivo. Questo fornisce un rilevamento più ampio FOV e una migliore durata della batteria rispetto al rilevamento con la fotocamera Photo/video (PV) del dispositivo.

### <a name="detecting-qr-codes-in-unity"></a>Rilevamento di codici QR in Unity

È possibile usare l'API di rilevamento del codice a matrice in Unity senza dipendere da MRTK. A tale scopo, è necessario installare il pacchetto NuGet usando [NuGet per Unity](https://github.com/GlitchEnzo/NuGetForUnity).

È disponibile un'app Unity di esempio che visualizza un quadrato olografico su codici a matrice, insieme ai dati associati, ad esempio GUID, dimensioni fisiche, timestamp e dati decodificati. Questa app si trova in https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes .

### <a name="detecting-qr-codes-in-c"></a>Rilevamento di codici QR in C++

```cpp
using namespace winrt::Windows::Foundation;
using namespace winrt::Microsoft::MixedReality::QR;

class QRListHelper
{
public:
    QRListHelper(MyApplication& app) :
        m_app(app)
    {}

    IAsyncAction SetUpQRCodes()
    {
        if (QRCodeWatcher::IsSupported())
        {
            QRCodeWatcherAccessStatus status = co_await QRCodeWatcher::RequestAccessAsync();
            InitializeQR(status);
        }
    }

private:
    void OnAddedQRCode(const IInspectable&, const QRCodeAddedEventArgs& args)
    {
        m_app.OnAddedQRCode(args);
    }

    void OnUpdatedQRCode(const IInspectable&, const QRCodeUpdatedEventArgs& args)
    {
        m_app.OnUpdatedQRCode(args);
    }

    void OnEnumerationComplete(const IInspectable&, const IInspectable&)
    {
        m_app.OnEnumerationComplete();
    }

    MyApplication& m_app;
    QRCodeWatcher m_qrWatcher{ nullptr };

    void InitializeQR(QRCodeWatcherAccessStatus status)
    {
        if (status == QRCodeWatcherAccessStatus::Allowed)
        {
            m_qrWatcher = QRCodeWatcher();
            m_qrWatcher.Added({ this, &QRListHelper::OnAddedQRCode });
            m_qrWatcher.Updated({ this, &QRListHelper::OnUpdatedQRCode });
            m_qrWatcher.EnumerationCompleted({ this, &QRListHelper::OnEnumerationComplete });
            m_qrWatcher.Start();
        }
        else
        {
            // Permission denied by system or user
            // Handle the failures
        }
    }
};
```

## <a name="getting-the-coordinate-system-for-a-qr-code"></a>Recupero del sistema di coordinate per un codice a matrice

Ogni codice a matrice rilevato espone un [sistema di coordinate spaziali](coordinate-systems.md) allineato al codice a matrice nell'angolo superiore sinistro del quadrato di rilevamento rapido in alto a sinistra, come illustrato di seguito.  Quando si usa direttamente il QR SDK, l'asse Z punta alla carta (non mostrata): quando viene convertito in coordinate Unity, l'asse Z punta all'esterno della carta ed è a sinistra.

Il SpatialCoordinateSystem del codice a matrice viene allineato come illustrato. Questo sistema di coordinate può essere ottenuto dalla piattaforma chiamando <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview:: CreateCoordinateSystemForNode</a> e passando il SpatialGraphNodeId del codice.

![Sistema di coordinate del codice a matrice](images/Qr-coordinatesystem.png) 

Per un oggetto QRCode, nel codice C++ riportato di seguito viene illustrato come creare un rettangolo e posizionarlo utilizzando il sistema di coordinate del codice a matrice:

```cpp
// Creates a 2D rectangle in the x-y plane, with the specified properties.
std::vector<float3> MyApplication::CreateRectangle(float width, float height)
{
    std::vector<float3> vertices(4);

    vertices[0] = { 0, 0, 0 };
    vertices[1] = { width, 0, 0 };
    vertices[2] = { width, height, 0 };
    vertices[3] = { 0, height, 0 };

    return vertices;
}
```

È possibile utilizzare le dimensioni fisiche per creare il rettangolo QR:

```cpp
std::vector<float3> qrVertices = CreateRectangle(code.PhysicalSideLength(), code.PhysicalSideLength()); 
```

Il sistema di coordinate può essere usato per creare il codice a matrice o per alleghire gli ologrammi al percorso:

```cpp
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
SpatialCoordinateSystem qrCoordinateSystem = SpatialGraphInteropPreview::CreateCoordinateSystemForNode(code.SpatialGraphNodeId());
```

Il *QRCodeAddedHandler* potrebbe avere un aspetto simile al seguente:

```cpp
void MyApplication::OnAddedQRCode(const QRCodeAddedEventArgs& args)
{
    QRCode code = args.Code();
    std::vector<float3> qrVertices = CreateRectangle(code.PhysicalSideLength(), code.PhysicalSideLength());
    std::vector<unsigned short> qrCodeIndices = TriangulatePoints(qrVertices);
    XMFLOAT3 qrAreaColor = XMFLOAT3(DirectX::Colors::Aqua);

    SpatialCoordinateSystem qrCoordinateSystem = SpatialGraphInteropPreview::CreateCoordinateSystemForNode(code.SpatialGraphNodeId());
    std::shared_ptr<SceneObject> m_qrShape =
        std::make_shared<SceneObject>(
            m_deviceResources,
            qrVertices,
            qrCodeIndices,
            qrAreaColor,
            qrCoordinateSystem);

    m_sceneController->AddSceneObject(m_qrShape);
}
```

## <a name="best-practices-for-qr-code-detection"></a>Procedure consigliate per il rilevamento del codice a matrice

### <a name="quiet-zones-around-qr-codes"></a>Zone tranquille intorno ai codici QR

Per la lettura corretta, i codici a matrice richiedono un margine intorno a tutti i lati del codice. Questo margine non deve contenere contenuto stampato e deve essere costituito da quattro moduli (un singolo quadrato nero nel codice). 

La [specifica QR](https://www.qrcode.com/en/howto/code.html) contiene altre informazioni sulle zone tranquile.

### <a name="lighting-and-backdrop"></a>Illuminazione e sfondo
La qualità del rilevamento del codice a matrice è soggetta a variazioni di illuminazione e sfondo. 

In una scena con illuminazione particolarmente luminosa, stampare un codice nero su uno sfondo grigio. In caso contrario, stampare un codice a matrice nero su uno sfondo bianco.

Se lo sfondo del codice è particolarmente scuro, provare a usare un codice nero in grigio se la frequenza di rilevamento è bassa. Se lo sfondo è relativamente chiaro, un codice normale dovrebbe funzionare correttamente.

### <a name="size-of-qr-codes"></a>Dimensioni dei codici QR
I dispositivi di realtà mista di Windows non funzionano con codici a matrice con lati inferiori a 5 cm.

Per i codici a matrice con lunghezza compresa tra 5 e 10 cm, è necessario essere abbastanza vicini per rilevare il codice. Sarà inoltre necessario più tempo per rilevare i codici in questa dimensione. 

Il tempo esatto per rilevare i codici dipende non solo dalle dimensioni dei codici a matrice, ma dalla distanza del codice. Lo spostamento più vicino al codice consente di compensare i problemi con le dimensioni.

### <a name="distance-and-angular-position-from-the-qr-code"></a>Posizione angolare e distanza dal codice a matrice
Le videocamere di rilevamento possono rilevare solo un certo livello di dettaglio. Per i codici molto piccoli, < 10cm lungo i lati, è necessario essere abbastanza vicini. Per un codice a matrice di versione 1 variabile da 10 a 25 cm di larghezza, la distanza di rilevamento minima varia da 0,15 metri a 0,5 metri. 

La distanza di rilevamento per le dimensioni aumenta in modo lineare. 

Il rilevamento a matrice funziona con un intervallo di angoli + = 45deg. Ciò consente di verificare la corretta risoluzione per il rilevamento del codice.

### <a name="qr-codes-with-logos"></a>Codici QR con logo
I codici QR con logo non sono stati testati e non sono attualmente supportati.

### <a name="managing-qr-code-data"></a>Gestione dei dati del codice QR
I dispositivi di realtà mista Windows rilevano codici QR a livello di sistema nel driver. Quando il dispositivo viene riavviato, i codici QR rilevati vengono eliminati e verranno rilevati nuovamente come nuovi oggetti la volta successiva.

Si consiglia di configurare l'app in modo da ignorare i codici QR precedenti a un timestamp specifico. Attualmente, l'API non supporta la cancellazione della cronologia del codice QR.

### <a name="qr-code-placement-in-a-space"></a>Posizionamento del codice a matrice in uno spazio
Per consigli su dove e come collocare i codici QR, vedere Considerazioni sull' [ambiente per HoloLens](environment-considerations-for-hololens.md).

## <a name="qr-api-reference"></a>Riferimento all'API QR

```cs
namespace Microsoft.MixedReality.QR
{
    /// <summary>
    /// Represents a detected QR code.
    /// </remarks>
    public class QRCode
    {
        /// <summary>
        /// Unique id that identifies this QR code for this session.
        /// </summary>
        public Guid Id { get; }

        /// <summary>
        /// Spatial graph node id for this QR code to create a coordinate system.
        /// </summary>
        public Guid SpatialGraphNodeId { get; }

        /// <summary>
        /// Version of this QR code. Version 1-40 are regular QR codes and M1 to M4 are Micro QR code formats 1-4.
        /// </summary>
        public QRVersion Version { get; }

        /// <summary>
        /// Physical width and height of this QR code in meters.
        /// </summary>
        public float PhysicalSideLength { get; }

        /// <summary>
        /// Decoded QR code data.
        /// </summary>
        public String Data { get; }

        /// <summary>
        /// Size of the RawData of this QR code.
        /// </summary>
        public UInt32 RawDataSize { get; }

        /// <summary>
        /// Gets the error-corrected raw data bytes.
        /// Used when the platform is unable to decode the code's format,
        /// allowing your app to decode as needed.
        /// </summary>
        public void GetRawData(byte[] buffer);

        /// <summary>
        /// The last detected time in 100ns QPC ticks.
        /// </summary>
        public System.TimeSpan SystemRelativeLastDetectedTime { get; }

        /// <summary>
        /// The last detected time.
        /// </summary>
        public System.DateTimeOffset LastDetectedTime { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Added event.
    /// </summary>
    public class QRCodeAddedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was added
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Removed event.
    /// </summary>
    public class QRCodeRemovedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was removed.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Updated event.
    /// </summary>
    public class QRCodeUpdatedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was updated.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Represents the status of an access request for QR code detection.
    /// </summary>
    public enum QRCodeWatcherAccessStatus
    {
        /// <summary>
        /// The system has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedBySystem = 0,
        /// <summary>
        /// The app has not declared the webcam capability in its manifest.
        /// </summary>
        NotDeclaredByApp = 1,
        /// <summary>
        /// The user has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedByUser = 2,
        /// <summary>
        /// A user prompt is required to get permission to detect QR codes.
        /// </summary>
        UserPromptRequired = 3,
        /// <summary>
        /// The user has given permission to detect QR codes.
        /// </summary>
        Allowed = 4,
    }

    /// <summary>
    /// Detects QR codes in the user's environment.
    /// </summary>
    public class QRCodeWatcher
    {
        /// <summary>
        /// Gets whether QR code detection is supported on the current device.
        /// </summary>
        public static bool IsSupported();

        /// <summary>
        /// Request user consent before using QR code detection.
        /// </summary>
        public static IAsyncOperation<QRCodeWatcherAccessStatus> RequestAccessAsync();

        /// <summary>
        /// Constructs a new QRCodeWatcher.
        /// </summary>
        public QRCodeWatcher();

        /// <summary>
        /// Starts detecting QR codes.
        /// </summary>
        /// <remarks>
        /// Start should only be called once RequestAccessAsync has succeeded.
        /// Start should not be called if QR code detection is not supported.
        /// Check that IsSupported returns true before calling Start.
        /// </remarks>
        public void Start();

        /// <summary>
        /// Stops detecting QR codes.
        /// </summary>
        public void Stop();

        /// <summary>
        /// Get the list of QR codes detected.
        /// </summary>
        /// <remarks>
        /// </remarks>
        public IList<QRCode> GetList();

        /// <summary>
        /// Event representing the addition of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeAddedEventArgs> Added;

        /// <summary>
        /// Event representing the removal of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeRemovedEventArgs> Removed;

        /// <summary>
        /// Event representing the update of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeUpdatedEventArgs> Updated;

        /// <summary>
        /// Event representing the enumeration of QR Codes completing after a Start call.
        /// </summary>
        public event EventHandler<Object> EnumerationCompleted;
    }

    /// <summary>
    /// Version info for QR codes, including Micro QR codes.
    /// </summary>
    public enum QRVersion
    {
        QR1 = 1,
        QR2 = 2,
        QR3 = 3,
        QR4 = 4,
        QR5 = 5,
        QR6 = 6,
        QR7 = 7,
        QR8 = 8,
        QR9 = 9,
        QR10 = 10,
        QR11 = 11,
        QR12 = 12,
        QR13 = 13,
        QR14 = 14,
        QR15 = 15,
        QR16 = 16,
        QR17 = 17,
        QR18 = 18,
        QR19 = 19,
        QR20 = 20,
        QR21 = 21,
        QR22 = 22,
        QR23 = 23,
        QR24 = 24,
        QR25 = 25,
        QR26 = 26,
        QR27 = 27,
        QR28 = 28,
        QR29 = 29,
        QR30 = 30,
        QR31 = 31,
        QR32 = 32,
        QR33 = 33,
        QR34 = 34,
        QR35 = 35,
        QR36 = 36,
        QR37 = 37,
        QR38 = 38,
        QR39 = 39,
        QR40 = 40,
        MicroQRM1 = 41,
        MicroQRM2 = 42,
        MicroQRM3 = 43,
        MicroQRM4 = 44,
    }
}
```

## <a name="see-also"></a>Vedere anche
* [Sistemi di coordinate](coordinate-systems.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Ancoraggi nello spazio di Azure</a>

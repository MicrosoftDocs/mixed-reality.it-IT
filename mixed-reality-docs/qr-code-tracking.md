---
title: Rilevamento del codice a matrice
description: Informazioni su come attivare il rilevamento del codice a matrice per l'auricolare di Windows misto Reality (VR) e implementare la funzionalità nelle app VR.
author: yoyozilla
ms.author: yoyoz
ms.date: 11/06/2018
ms.topic: article
keywords: VR, LBE, location based Entertainment, VR Arcade, Arcade, immersive, QR, QR code
ms.openlocfilehash: 465056cf645a8b9dc9e0e2d3f9dacf887df67c52
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829979"
---
# <a name="qr-code-tracking"></a>Rilevamento del codice a matrice

Il rilevamento del codice a matrice viene implementato nel driver di realtà mista di Windows per gli auricolari immersivi (VR). Abilitando il tracker del codice a matrice nel driver della cuffia, l'auricolare analizza i codici a matrice e viene segnalato alle app interessate. Questa funzionalità è disponibile solo in [Windows 10 ottobre 2018 aggiornamento (noto anche come RS5)](release-notes-october-2018.md).

>[!NOTE]
>I frammenti di codice in questo articolo illustrano attualmente l' C++uso di/CX, invece di/WinRT conformi C++a C + 17 come usato nel modello di [ C++ progetto olografico](creating-a-holographic-directx-project.md).  I concetti sono equivalenti per C++un progetto/WinRT, anche se sarà necessario tradurre il codice.

## <a name="device-support"></a>Supporto di dispositivi

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Funzionalità</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
    </tr>
     <tr>
        <td>Rilevamento del codice a matrice</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="enabling-and-disabling-qr-code-tracking-for-your-headset"></a>Abilitazione e disabilitazione del rilevamento del codice QR per l'auricolare
Nota: Questa sezione è valida solo per l' [aggiornamento di Windows 10 ottobre 2018 (noto anche come RS5)](release-notes-october-2018.md). A partire dalle build di 19h1, non sarà necessario eseguire questa operazione.
Che tu stia sviluppando un'app per realtà mista che utilizzerà il rilevamento del codice a matrice o che sei un cliente di una di queste app, dovrai attivare manualmente il rilevamento del codice a matrice nel driver dell'auricolare.

Per **attivare il rilevamento del codice** a matrice per l'auricolare immersiva (VR):

1. Chiudere l'app del portale per la realtà mista nel PC.
2. Scollegare l'auricolare dal PC.
3. Eseguire lo script seguente nel prompt dei comandi:<br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 1 /F`
4. Riconnettere l'auricolare al PC.

Per disattivare il **rilevamento del codice QR** per l'auricolare immersiva (VR):

1. Chiudere l'app del portale per la realtà mista nel PC.
2. Scollegare l'auricolare dal PC.
3. Eseguire lo script seguente nel prompt dei comandi:<br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 0 /F`
4. Riconnettere l'auricolare al PC. In questo modo tutti i codici QR individuati "non locatable".

## <a name="printing-codes"></a>Codici di stampa

Prima di tutto, la [specifica per i codici](https://www.qrcode.com/en/howto/code.html) a matrice indica che l'area dei simboli del codice a matrice richiede un margine o una "zona non interattiva" per poter essere usata. Il margine è un'area chiara intorno a un simbolo che non viene stampato. Il codice a matrice richiede un margine Wide a quattro moduli a tutti i lati di un simbolo ". Questo deve avere una larghezza, a ogni lato, di quattro volte la dimensione di un modulo, un singolo quadrato nero nel codice. La pagina delle specifiche contiene suggerimenti su come stampare codici QR e individuare l'area necessaria per creare un codice a matrice di dimensioni specifiche.

Attualmente la qualità del rilevamento del codice a matrice è soggetta a variazioni di illuminazione e sfondo. Per contrastare questo problema, prendere nota dell'illuminazione e stampare il codice appropriato. In una scena con illuminazione particolarmente luminosa, stampare un codice nero su uno sfondo grigio. In una scena di scarsa luminosità, il nero sul bianco funziona. Analogamente, se lo sfondo del codice è particolarmente scuro, provare a usare un codice nero in grigio se la frequenza di rilevamento è bassa. In caso contrario, se lo sfondo è più chiaro, un codice normale dovrebbe funzionare correttamente.

## <a name="qrtracking-api"></a>API QRTracking

Il plug-in QRTracking espone le API per il rilevamento del codice a matrice. Per usare il plug-in, è necessario usare i tipi seguenti dello spazio dei nomi *QRCodesTrackerPlugin* .

```cs
 // QRTracker plugin namespace
 namespace QRCodesTrackerPlugin
 {
    // Encapsulates information about a labeled QR code element.
    public class QRCode
    {        
        // Unique id that identifies this QR code for this session.
        public Guid Id { get; private set; }
           
        // Version of this QR code.
        public Int32 Version { get; private set; }
        
        // PhysicalSizeMeters of this QR code.
        public float PhysicalSizeMeters { get; private set; }
        
        // QR code Data.
        public string Code { get; private set; }
        
        // QR code DataStream this is the error corrected data stream
        public Byte[] CodeStream { get; private set; }
        
        // QR code last detected QPC ticks.
        public Int64 LastDetectedQPCTicks { get; private set; }
    };
    
    // The type of a QR Code added event.
    public class QRCodeAddedEventArgs
    {   
        // Gets the QR Code that was added
        public QRCode Code { get; private set; }
    };
    
    // The type of a QR Code removed event.
    public class QRCodeRemovedEventArgs
    {
        // Gets the QR Code that was removed.
        public QRCode Code { get; private set; }
    };
    
    // The type of a QR Code updated event.
    public class QRCodeUpdatedEventArgs
    {
        // Gets the QR Code that was updated.
        public QRCode Code { get; private set; }
    };
    
    // A callback for handling the QR Code added event.
    public delegate void QRCodeAddedHandler(QRCodeAddedEventArgs args);
    
    // A callback for handling the QR Code removed event.
    public delegate void QRCodeRemovedHandler(QRCodeRemovedEventArgs args);
    
    // A callback for handling the QR Code updated event.
    public delegate void QRCodeUpdatedHandler(QRCodeUpdatedEventArgs args);
    
    // Enumerates the possible results of a start of QRTracker.
    public enum QRTrackerStartResult
    {
        // The start has succeeded.
        Success = 0,
        
        //  The currently no device is connected.
        DeviceNotConnected = 1,
        
        // The QRTracking Feature is not supported by the current HMD driver
        // systems
        FeatureNotSupported = 2,
        
        // The access is denide. Administrator needs to enable QR tracker feature.
        AccessDenied = 3,
    };
    
    // QRTracker
    public class QRTracker
    {
        // Constructs a new QRTracker.
        public QRTracker(){}
        
        // Gets the QRTracker.
        public static QRTracker Get()
        {
            return new QRTracker();
        }
        
        // Start the QRTracker. Returns QRTrackerStartResult.
        public QRTrackerStartResult Start()
        {
            throw new NotImplementedException();
        }
        
        // Stops tracking QR codes.
        public void Stop() {}

        // Not Implemented
        Windows.Foundation.Collections.IVector<QRCode> GetList() { throw new NotImplementedException(); }
        
        // Event representing the addition of a QR Code.
        public event QRCodeAddedHandler Added = delegate { };
        
        // Event representing the removal of a QR Code.
        public event QRCodeRemovedHandler Removed = delegate { };
        
        // Event representing the update of a QR Code.
        public event QRCodeUpdatedHandler Updated = delegate { };
    };
}
```

## <a name="implementing-qr-code-tracking-in-unity"></a>Implementazione del rilevamento del codice a matrice in Unity

### <a name="sample-unity-scenes-in-mrtk-mixed-reality-toolkit"></a>Scene Unity di esempio in MRTK (Toolkit realtà mista)

È possibile trovare un esempio di come usare l'API di rilevamento a matrice nel [sito GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker)di Mixed Reality Toolkit.

MRTK ha implementato gli script necessari per simpilify l'utilizzo del rilevamento a barre. Tutte le risorse necessarie per lo sviluppo di app di rilevamento a barre si trovano nella cartella "QRTracker". Ci sono due scene: il primo è un esempio che mostra semplicemente i dettagli dei codici a matrice quando vengono rilevati e il secondo illustra come usare il sistema di coordinate collegato al codice a matrice per visualizzare gli ologrammi.
È disponibile un "QRScanner" prefabbricato che ha aggiunto tutti gli script necessari per l'uso di QRCodes. Lo script QRCodeManager è una classe singleton che implementa l'API QRCode. Questa operazione deve essere aggiunta alla scena. Lo script "AttachToQRCode" viene usato per alleghire gli ologrammi ai sistemi di coordinate del codice a matrice. questo script può essere aggiunto a qualsiasi ologramma. In "SpatialGraphCoordinateSystem" viene illustrato come utilizzare il sistema di coordinate QRCode. Questi script possono essere usati così come sono nelle scene del progetto oppure è possibile scrivere direttamente usando il plug-in come descritto in precedenza.

### <a name="implementing-qr-code-tracking-in-unity-without-mrtk"></a>Implementazione del rilevamento del codice a matrice in Unity senza MRTK

È anche possibile usare l'API di rilevamento a matrice in Unity senza dipendere da MRTK. Per usare l'API, sarà necessario preparare il progetto con l'istruzione seguente:

1. Creare una nuova cartella nella cartella assets del progetto Unity con il nome: "Plug-in".
2. Copiare tutti i file necessari da [questa cartella](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins) nella cartella "plugins" locale appena creata.
3. È possibile usare gli script di rilevamento a matrice nella [cartella degli script di MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts) o scrivere i propri.
Nota: Questi plug-in sono solo per le compilazioni di [aggiornamento 2018 di Windows 10 ottobre (noto anche come RS5)](release-notes-october-2018.md) . I plug-in verranno aggiornati con la versione successiva di Windows. I plug-in correnti sono sperimentali e non funzioneranno per la versione futura di Windows. Verranno pubblicati nuovi plug-in che possono essere usati dalla versione successiva di Windows e non saranno compatibili con le versioni precedenti e non funzioneranno con RS5.

## <a name="implementing-qr-code-tracking-in-directx"></a>Implementazione del rilevamento del codice a matrice in DirectX

Per usare QRTrackingPlugin in Visual Studio, è necessario aggiungere il riferimento di QRTrackingPlugin a. winmd. Qui è possibile trovare i [file necessari per le piattaforme supportate](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA).

```cpp
// MyClass.h
public ref class MyClass
{
    private:
      QRCodesTrackerPlugin::QRTracker^ m_qrtracker;
      // Handlers
      void OnAddedQRCode(QRCodesTrackerPlugin::QRCodeAddedEventArgs ^args);
      void OnUpdatedQRCode(QRCodesTrackerPlugin::QRCodeUpdatedEventArgs ^args);
      void OnRemovedQRCode(QRCodesTrackerPlugin::QRCodeRemovedEventArgs ^args);
    ..
};
```

```cpp
// MyClass.cpp
MyClass::MyClass()
{
    // Create the tracker and register the callbacks
    m_qrtracker = ref new QRCodesTrackerPlugin::QRTracker();
    m_qrtracker->Added += ref new QRCodesTrackerPlugin::QRCodeAddedHandler(this, &OnAddedQRCode);
    m_qrtracker->Updated += ref new QRCodesTrackerPlugin::QRCodeUpdatedHandler(this, &OnUpdatedQRCode);
    m_qrtracker->Removed += ref new QRCodesTrackerPlugin::QRCodeRemovedHandler(this, &QOnRemovedQRCode);

    // Start the tracker
    if (m_qrtracker->Start() != QRCodesTrackerPlugin::QRTrackerStartResult::Success)
    {
      // Handle the failure
      // It can fail for multiple reasons and can be handled properly 
    }
}

void MyClass::OnAddedQRCode(QRCodesTrackerPlugin::QRCodeAddedEventArgs ^args)
{
    // use args->Code add to own list  
}

void MyClass::OnUpdatedQRCode(QRCodesTrackerPlugin::QRCodeUpdatedEventArgs ^args)
{
    // use args->Code update the existing one with the new one in own list 
}

void MyClass::OnRemovedQRCode(QRCodesTrackerPlugin::QRCodeRemovedEventArgs ^args)
{
    // use args->Code remove from own list.
}
```

## <a name="getting-a-coordinate-system"></a>Recupero di un sistema di coordinate

Si definisce un sistema di coordinate di destra allineato con il codice a matrice nell'angolo superiore sinistro del quadrato di rilevamento rapido in alto a sinistra. Il sistema di coordinate è illustrato di seguito. L'asse Z punta alla carta (non mostrata), ma in Unity l'asse z è esterno alla carta e a sinistra.

Viene definito un SpatialCoordinateSystem che è allineato come illustrato. Questo sistema di coordinate può essere ottenuto dalla piattaforma usando le *finestre API::P erception:: Spatial::P Review:: SpatialGraphInteropPreview:: CreateCoordinateSystemForNode*.

![Sistema di coordinate del codice a matrice](images/Qr-coordinatesystem.png) 

Dall'oggetto di codice QRCode ^, il codice seguente illustra come creare un rettangolo e inserirlo nel sistema di coordinate QR:

```cpp
// Creates a 2D rectangle in the x-y plane, with the specified properties.
std::vector<float3> SpatialStageManager::CreateRectangle(float width, float height)
{
    std::vector<float3> vertices(4);

    vertices[0] = { 0,  0, 0 };
    vertices[1] = { width,  0, 0 };
    vertices[2] = { width,  height, 0 };
    vertices[3] = { 0,  height, 0 };

    return vertices;
}
```

È possibile utilizzare le dimensioni fisiche per creare il rettangolo QR:

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

Il sistema di coordinate può essere usato per creare il codice a matrice o per alleghire gli ologrammi al percorso:

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->Id);
```

Il valore di *QRCodesTrackerPlugin:: QRCodeAddedHandler* potrebbe essere simile al seguente:

```cpp
void MyClass::OnAddedQRCode(QRCodesTrackerPlugin::QRCodeAddedEventArgs ^args)
{
    std::vector<float3> qrVertices = CreateRectangle(args->Code->PhysicalSizeMeters, args->Code->PhysicalSizeMeters);
    std::vector<unsigned short> qrCodeIndices = TriangulatePoints(qrVertices);
    XMFLOAT3 qrAreaColor = XMFLOAT3(DirectX::Colors::Aqua);

    Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem =  Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(args->Code->Id);
    std::shared_ptr<SceneObject> m_qrShape =
        std::make_shared<SceneObject>(
            m_deviceResources,
            reinterpret_cast<std::vector<XMFLOAT3>&>(qrVertices),
            qrCodeIndices,
            qrAreaColor,
            qrCoordinateSystem);

    m_sceneController->AddSceneObject(m_qrShape);
}
```

## <a name="troubleshooting-and-faq"></a>Risoluzione dei problemi e domande frequenti

**Risoluzione dei problemi generali**

* Il PC esegue l'aggiornamento di Windows 10 ottobre 2018?
* Si è impostato il tasto reg? Il dispositivo è stato riavviato in seguito?
* La versione del codice a matrice è supportata? L'API corrente supporta fino a QR Code versione 20. È consigliabile usare la versione 5 per l'utilizzo generale. 
* Il codice a matrice è sufficientemente vicino? Più si avvicina la fotocamera al codice a matrice, più alta è la versione del codice a matrice che l'API può supportare.  

**Quanto è necessario essere vicini al codice a matrice per rilevarlo?**

Ciò dipende dalle dimensioni del codice a matrice e dalla versione. Per un codice a matrice di versione 1 che varia da 5 cm a 25 cm, la distanza di rilevamento minima varia da 0,15 metri a 0,5 metri. Il più lontano di questi possono essere rilevati da circa 0,3 metri per le destinazioni di codice a matrice più piccole a 1,4 metri per il più grande. Per i codici QR di dimensioni maggiori, è possibile stimare; la distanza di rilevamento per le dimensioni aumenta in modo lineare. Lo strumento di individuazione non funziona con codici a matrice con lati inferiori a 5 cm.

**I codici QR con logo funzionano?**

I codici QR con logo non sono stati testati e non sono attualmente supportati.

**Ricerca per categorie cancellare i codici a matrice dall'app, in modo che non vengano mantenuti?**

* I codici a matrice sono conservati solo nella sessione di avvio. Dopo aver riavviato (o riavviato il driver), questi verranno rilevati come nuovi oggetti la prossima volta.
* La cronologia del codice a matrice viene salvata a livello di sistema nella sessione del driver, ma è possibile configurare l'app in modo da ignorare i codici QR più vecchi di un timestamp specifico, se necessario. Attualmente l'API supporta la cancellazione della cronologia del codice QR, in quanto più app potrebbero essere interessate ai dati.

**I plug-in per RS5 e le versioni future non sono compatibili** La versione del plug-in RS5 funziona solo per RS5 e non funzionerà per le versioni future. Il plug-in expermental verrà sostituito con il plug-in reale e dovrebbe essere quello che è possibile usare nelle versioni future di Windows.

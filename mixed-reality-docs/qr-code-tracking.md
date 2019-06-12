---
title: Codice a matrice di rilevamento
description: Informazioni su come attivare la scansione del codice di rilevamento per le cuffie (VR) coinvolgenti di realtà mista di Windows e implementare la funzionalità nelle app di realtà virtuale.
author: yoyozilla
ms.author: yoyoz
ms.date: 11/06/2018
ms.topic: article
keywords: realtà virtuale, lbe, intrattenimento basato su posizione, vr arcade, codice a matrice arcade, coinvolgenti, codici a matrice,
ms.openlocfilehash: 465056cf645a8b9dc9e0e2d3f9dacf887df67c52
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829979"
---
# <a name="qr-code-tracking"></a>Codice a matrice di rilevamento

Codice a matrice di rilevamento viene implementato nel driver realtà mista di Windows per immersive auricolari (VR). Abilitando il tracker di codice a matrice nel driver le cuffie, le cuffie esegue l'analisi dei codici a matrice e vengono segnalati per le app interessate. Questa funzionalità è disponibile come di solo il [Windows 10 ottobre 2018 Update (noto anche come RS5)](release-notes-october-2018.md).

>[!NOTE]
>I frammenti di codice in questo articolo illustrano attualmente l'utilizzo di C++/CX invece di C + + 17 conformi C++/WinRT usato nel [ C++ modello di progetto holographic](creating-a-holographic-directx-project.md).  I concetti sono equivalenti per un C++progetto /WinRT, anche se è necessario convertire il codice.

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
        <td><a href="immersive-headset-hardware-details.md"><strong>Auricolari coinvolgenti</strong></a></td>
    </tr>
     <tr>
        <td>Codice a matrice di rilevamento</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="enabling-and-disabling-qr-code-tracking-for-your-headset"></a>Abilitazione e disabilitazione di codici a matrice di rilevamento per le cuffie codice
Nota: In questa sezione è valida solo per [Windows 10 ottobre 2018 Update (noto anche come RS5)](release-notes-october-2018.md). Dalle build di 19 ore 1 o versione successiva non è necessario eseguire questa operazione.
Se si sta sviluppando un'app di realtà mista che userà codice a matrice di rilevamento o sei un cliente di una di queste App, è necessario attivare manualmente la scansione del codice di rilevamento nel driver del auricolare.

Al fine di **attivare la scansione del codice di rilevamento** per le cuffie (VR) immersive:

1. Chiudere l'app del portale di realtà mista nel PC.
2. Scollegare il visore VR dal PC.
3. Eseguire lo script seguente nel Prompt dei comandi:<br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 1 /F`
4. Riconnettere le cuffie al computer.

Al fine di **disattivare la scansione del codice di rilevamento** per le cuffie (VR) immersive:

1. Chiudere l'app del portale di realtà mista nel PC.
2. Scollegare il visore VR dal PC.
3. Eseguire lo script seguente nel Prompt dei comandi:<br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 0 /F`
4. Riconnettere le cuffie al computer. In questo modo tutti i codici a matrice individuati "non individuabili."

## <a name="printing-codes"></a>Codici di stampa

In primo luogo, il [specifiche per i codici a matrice](https://www.qrcode.com/en/howto/code.html) afferma "l'area di simboli di codice a matrice è necessario un margine o una"zona quiet"intorno a esso da utilizzare. Il margine è un'area chiara intorno a un simbolo in cui viene stampato niente. Codice a matrice è necessario un ampio margine di quattro-module in tutti i lati di un simbolo". Questa operazione deve avere una larghezza, in ogni lato di quattro volte le dimensioni di un modulo - un singolo quadrato nero nel codice. La pagina specifica contiene consigli su come stampare i codici a matrice e individuare l'area richiesta per rendere un determinato codice a matrice con dimensione.

La qualità del rilevamento di codice a matrice è attualmente soggetta a vari illuminazione e sfondo. Per evitare questo inconveniente, si noti l'illuminazione e stampare il codice appropriato. In una scena con estrema particolarmente luminosità, stampa un codice che è nero su sfondo grigio. In una scena scarsa luminosità nera su bianco works. Analogamente, se lo sfondo per il codice è particolarmente scuro, provare a nero sul codice grigia se la frequenza di rilevamento è bassa. In caso contrario, se lo sfondo più chiaro, un codice regolare dovrebbe funzionare correttamente.

## <a name="qrtracking-api"></a>QRTracking API

Il plug-in QRTracking espone le API per il codice a matrice di rilevamento. Per usare il plug-in, è necessario usare i tipi di seguito il *QRCodesTrackerPlugin* dello spazio dei nomi.

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

## <a name="implementing-qr-code-tracking-in-unity"></a>Implementazione di codice a matrice di rilevamento in Unity

### <a name="sample-unity-scenes-in-mrtk-mixed-reality-toolkit"></a>In background di Unity di esempio nelle MRTK (Toolkit di realtà mista)

È possibile trovare un esempio di come usare l'API di gestione di codici a matrice nel Toolkit di realtà mista [sito GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker).

MRTK ha implementato gli script necessari per simpilify i codici a matrice per tracciare l'utilizzo. Tutte le risorse necessarie per sviluppare a matrice di tenere traccia delle applicazioni si trovano nella cartella "QRTracker". Esistono due scene: il primo è un esempio per visualizzare semplicemente i dettagli dei codici QR quando vengono rilevati e la seconda viene illustrato come utilizzare il sistema di coordinate collegato del codice a matrice per visualizzare vntana.
È presente un prefab "QRScanner" aggiunto tutti gli script necessari per le scene usare QRCodes. Lo script QRCodeManager è una classe singleton che implementa l'API QRCode. Questa operazione deve essere aggiunto alla scena. Lo script "AttachToQRCode" viene usato per collegare vntana ai sistemi di coordinate del codice a matrice, questo script può essere aggiunto a uno qualsiasi dei vntana. "SpatialGraphCoordinateSystem" viene illustrato come utilizzare il sistema di coordinate QRCode. Questi script possono essere usati come-è nel progetto scene oppure è possibile scrivere il proprio direttamente usando il plug-in come descritto in precedenza.

### <a name="implementing-qr-code-tracking-in-unity-without-mrtk"></a>Implementazione di codice a matrice in Unity senza MRTK di rilevamento

È anche possibile usare l'API di gestione di codici a matrice in Unity senza creare una dipendenza da MRTK. Per usare l'API, è necessario preparare il progetto con l'istruzione seguente:

1. Creare una nuova cartella nella cartella assets del progetto unity con il nome: "I"plug-in.
2. Copiare tutti i file richiesti da [in questa cartella](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins) nella cartella "Plug-in" locale appena creato.
3. È possibile usare i codici a matrice di rilevamento degli script nel [cartella scripts MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts) o scriverne uno proprio.
Nota: Questi plug-in sono solo per [Windows 10 ottobre 2018 Update (noto anche come RS5)](release-notes-october-2018.md) compilazioni. I plug-in verrà aggiornato con la prossima versione di windows. I plug-in correnti sono sperimentali e non funzioneranno per versioni future di windows. Verranno pubblicati nuovi plug-in che può essere usato dalla prossima versione di windows e non sarà con le versioni precedenti compatibile e non funzionerà con RS5).

## <a name="implementing-qr-code-tracking-in-directx"></a>Implementazione di codice a matrice di rilevamento in DirectX

Per usare il QRTrackingPlugin in Visual Studio, è necessario aggiungere il riferimento del QRTrackingPlugin ai. winmd. È possibile trovare il [i file richiesti per le piattaforme supportate qui](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA).

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

Definiamo un sistema di coordinate di destra allineato con il codice a matrice nell'angolo superiore sinistro del quadrato rilevamento rapido in alto a sinistra. Il sistema di coordinate è illustrato di seguito. L'asse z fa riferimento nel documento di (non illustrato), ma in Unity all'asse z è la carta esaurita e battitori.

Viene definito un SpatialCoordinateSystem allineata come illustrato. Questo sistema di coordinate può essere ottenuto dalla piattaforma usando l'API *Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode*.

![Sistema di coordinate del codice a matrice](images/Qr-coordinatesystem.png) 

Da QRCode ^ codice oggetto, il codice seguente viene illustrato come creare un rettangolo e inserirlo nel sistema di coordinate di codici a matrice:

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

La dimensione fisica è possibile usare per creare il rettangolo di codici a matrice:

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

Il sistema di coordinate è utilizzabile per disegnare la scansione del codice o collegare vntana nel percorso:

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->Id);
```

Completamente, il *QRCodesTrackerPlugin::QRCodeAddedHandler* potrebbe avere un aspetto simile:

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

* Sia i PC che eseguono Windows 10 ottobre 2018 Update?
* È stata impostata la chiave reg? Riavviare il dispositivo in un secondo momento?
* È la versione del codice a matrice di una versione supportata? Supporto di API corrente fino a 20 versione di codice a matrice. È consigliabile usare la versione 5 per l'utilizzo generale. 
* Si abbastanza ravvicinati per la scansione del codice? È vicino alla fotocamera del codice a matrice, maggiore sarà la versione di codice l'API di codici a matrice può supportare.  

**La distanza è necessario essere al codice a matrice per individuarlo?**

Ciò dipende la dimensione del codice a matrice e inoltre quale versione è. Per un codice a matrice di versione 1 compreso tra i lati cm 5 e i lati 25 cm, la distanza minima di rilevamento compreso tra 0,15 metri e metri 0,5. Il più lontano da subito questi possono essere rilevati da passa da circa 0.3 contatori per le destinazioni di codice a matrice inferiori a 1,4 i contatori per il più grande. Per i codici a matrice più grandi rispetto a quello, è possibile stimare; la distanza di rilevamento per le dimensioni aumenta in modo lineare. La registrazione non funziona con i codici a matrice con i lati inferiori a 5 cm.

**Eseguire i codici a matrice con logo lavoro?**

I codici a matrice con logo non sono stati testati e sono attualmente supportati.

**Come si cancella i codici a matrice dall'app in modo che non vengono mantenute?**

* I codici a matrice vengono resi persistenti solo nella sessione di avvio. Dopo il riavvio (o riavviare il driver), verranno eseguiti e rilevati come nuovi oggetti successivo.
* Cronologia del codice a matrice viene salvata a livello di sistema nella sessione di driver, ma è possibile configurare l'app per ignorare i codici a matrice antecedenti a un timestamp specifico, se si desidera. Attualmente l'API supporta cronologia del codice a matrice di cancellazione, come le app più potrebbero essere interessate a dati.

**I plug-in per RS5 e nelle versioni future non sono compatibile** versione RS5 del plug-in funziona solo per RS5 e non funzioneranno per le versioni future. Il plug-in expermental verrà sostituito con il plug-in reali e deve essere quello che è possibile usare nelle future versioni di windows.

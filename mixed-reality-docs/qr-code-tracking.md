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
# <a name="qr-code-tracking"></a><span data-ttu-id="a5299-104">Rilevamento del codice a matrice</span><span class="sxs-lookup"><span data-stu-id="a5299-104">QR code tracking</span></span>

<span data-ttu-id="a5299-105">Il rilevamento del codice a matrice viene implementato nel driver di realtà mista di Windows per gli auricolari immersivi (VR).</span><span class="sxs-lookup"><span data-stu-id="a5299-105">QR code tracking is implemented in the Windows Mixed Reality driver for immersive (VR) headsets.</span></span> <span data-ttu-id="a5299-106">Abilitando il tracker del codice a matrice nel driver della cuffia, l'auricolare analizza i codici a matrice e viene segnalato alle app interessate.</span><span class="sxs-lookup"><span data-stu-id="a5299-106">By enabling the QR code tracker in the headset driver, the headset scans for QR codes and they are reported to interested apps.</span></span> <span data-ttu-id="a5299-107">Questa funzionalità è disponibile solo in [Windows 10 ottobre 2018 aggiornamento (noto anche come RS5)](release-notes-october-2018.md).</span><span class="sxs-lookup"><span data-stu-id="a5299-107">This feature is only available as of the [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md).</span></span>

>[!NOTE]
><span data-ttu-id="a5299-108">I frammenti di codice in questo articolo illustrano attualmente l' C++uso di/CX, invece di/WinRT conformi C++a C + 17 come usato nel modello di [ C++ progetto olografico](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="a5299-108">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="a5299-109">I concetti sono equivalenti per C++un progetto/WinRT, anche se sarà necessario tradurre il codice.</span><span class="sxs-lookup"><span data-stu-id="a5299-109">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="device-support"></a><span data-ttu-id="a5299-110">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="a5299-110">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="a5299-111"><strong>Funzionalità</strong></span><span class="sxs-lookup"><span data-stu-id="a5299-111"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="a5299-112"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="a5299-112"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="a5299-113"><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="a5299-113"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="a5299-114">Rilevamento del codice a matrice</span><span class="sxs-lookup"><span data-stu-id="a5299-114">QR code tracking</span></span></td>
        <td><span data-ttu-id="a5299-115">❌</span><span class="sxs-lookup"><span data-stu-id="a5299-115">❌</span></span></td>
        <td><span data-ttu-id="a5299-116">✔️</span><span class="sxs-lookup"><span data-stu-id="a5299-116">✔️</span></span></td>
    </tr>
</table>

## <a name="enabling-and-disabling-qr-code-tracking-for-your-headset"></a><span data-ttu-id="a5299-117">Abilitazione e disabilitazione del rilevamento del codice QR per l'auricolare</span><span class="sxs-lookup"><span data-stu-id="a5299-117">Enabling and disabling QR code tracking for your headset</span></span>
<span data-ttu-id="a5299-118">Nota: Questa sezione è valida solo per l' [aggiornamento di Windows 10 ottobre 2018 (noto anche come RS5)](release-notes-october-2018.md).</span><span class="sxs-lookup"><span data-stu-id="a5299-118">Note: This section is only valid for [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md).</span></span> <span data-ttu-id="a5299-119">A partire dalle build di 19h1, non sarà necessario eseguire questa operazione.</span><span class="sxs-lookup"><span data-stu-id="a5299-119">From 19h1 builds onwards you will not have to do this.</span></span>
<span data-ttu-id="a5299-120">Che tu stia sviluppando un'app per realtà mista che utilizzerà il rilevamento del codice a matrice o che sei un cliente di una di queste app, dovrai attivare manualmente il rilevamento del codice a matrice nel driver dell'auricolare.</span><span class="sxs-lookup"><span data-stu-id="a5299-120">Whether you're developing a mixed reality app that will leverage QR code tracking, or you're a customer of one of these apps, you'll need to manually turn on QR code tracking in your headset's driver.</span></span>

<span data-ttu-id="a5299-121">Per **attivare il rilevamento del codice** a matrice per l'auricolare immersiva (VR):</span><span class="sxs-lookup"><span data-stu-id="a5299-121">In order to **turn on QR code tracking** for your immersive (VR) headset:</span></span>

1. <span data-ttu-id="a5299-122">Chiudere l'app del portale per la realtà mista nel PC.</span><span class="sxs-lookup"><span data-stu-id="a5299-122">Close the Mixed Reality Portal app on your PC.</span></span>
2. <span data-ttu-id="a5299-123">Scollegare l'auricolare dal PC.</span><span class="sxs-lookup"><span data-stu-id="a5299-123">Unplug the headset from your PC.</span></span>
3. <span data-ttu-id="a5299-124">Eseguire lo script seguente nel prompt dei comandi:</span><span class="sxs-lookup"><span data-stu-id="a5299-124">Run the following script in the Command Prompt:</span></span><br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 1 /F`
4. <span data-ttu-id="a5299-125">Riconnettere l'auricolare al PC.</span><span class="sxs-lookup"><span data-stu-id="a5299-125">Reconnect your headset to your PC.</span></span>

<span data-ttu-id="a5299-126">Per disattivare il **rilevamento del codice QR** per l'auricolare immersiva (VR):</span><span class="sxs-lookup"><span data-stu-id="a5299-126">In order to **turn off QR code tracking** for your immersive (VR) headset:</span></span>

1. <span data-ttu-id="a5299-127">Chiudere l'app del portale per la realtà mista nel PC.</span><span class="sxs-lookup"><span data-stu-id="a5299-127">Close the Mixed Reality Portal app on your PC.</span></span>
2. <span data-ttu-id="a5299-128">Scollegare l'auricolare dal PC.</span><span class="sxs-lookup"><span data-stu-id="a5299-128">Unplug the headset from your PC.</span></span>
3. <span data-ttu-id="a5299-129">Eseguire lo script seguente nel prompt dei comandi:</span><span class="sxs-lookup"><span data-stu-id="a5299-129">Run the following script in the Command Prompt:</span></span><br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 0 /F`
4. <span data-ttu-id="a5299-130">Riconnettere l'auricolare al PC.</span><span class="sxs-lookup"><span data-stu-id="a5299-130">Reconnect your headset to your PC.</span></span> <span data-ttu-id="a5299-131">In questo modo tutti i codici QR individuati "non locatable".</span><span class="sxs-lookup"><span data-stu-id="a5299-131">This will make any discovered QR codes "non-locatable."</span></span>

## <a name="printing-codes"></a><span data-ttu-id="a5299-132">Codici di stampa</span><span class="sxs-lookup"><span data-stu-id="a5299-132">Printing codes</span></span>

<span data-ttu-id="a5299-133">Prima di tutto, la [specifica per i codici](https://www.qrcode.com/en/howto/code.html) a matrice indica che l'area dei simboli del codice a matrice richiede un margine o una "zona non interattiva" per poter essere usata.</span><span class="sxs-lookup"><span data-stu-id="a5299-133">First and foremost, the [spec for QR codes](https://www.qrcode.com/en/howto/code.html) says "The QR Code symbol area requires a margin or "quiet zone" around it to be used.</span></span> <span data-ttu-id="a5299-134">Il margine è un'area chiara intorno a un simbolo che non viene stampato.</span><span class="sxs-lookup"><span data-stu-id="a5299-134">The margin is a clear area around a symbol where nothing is printed.</span></span> <span data-ttu-id="a5299-135">Il codice a matrice richiede un margine Wide a quattro moduli a tutti i lati di un simbolo ".</span><span class="sxs-lookup"><span data-stu-id="a5299-135">QR Code requires a four-module wide margin at all sides of a symbol."</span></span> <span data-ttu-id="a5299-136">Questo deve avere una larghezza, a ogni lato, di quattro volte la dimensione di un modulo, un singolo quadrato nero nel codice.</span><span class="sxs-lookup"><span data-stu-id="a5299-136">This needs to have a width, on every side, of four times the size of a module - a single black square in the code.</span></span> <span data-ttu-id="a5299-137">La pagina delle specifiche contiene suggerimenti su come stampare codici QR e individuare l'area necessaria per creare un codice a matrice di dimensioni specifiche.</span><span class="sxs-lookup"><span data-stu-id="a5299-137">The spec page contains advice on how to print QR codes and figure out the area required to make a certain sized QR code.</span></span>

<span data-ttu-id="a5299-138">Attualmente la qualità del rilevamento del codice a matrice è soggetta a variazioni di illuminazione e sfondo.</span><span class="sxs-lookup"><span data-stu-id="a5299-138">Currently QR code detection quality is susceptible to varying illumination and backdrop.</span></span> <span data-ttu-id="a5299-139">Per contrastare questo problema, prendere nota dell'illuminazione e stampare il codice appropriato.</span><span class="sxs-lookup"><span data-stu-id="a5299-139">To combat this, note your illumination and print the appropriate code.</span></span> <span data-ttu-id="a5299-140">In una scena con illuminazione particolarmente luminosa, stampare un codice nero su uno sfondo grigio.</span><span class="sxs-lookup"><span data-stu-id="a5299-140">In a scene with particularly bright lighting, print a code that is black on a gray background.</span></span> <span data-ttu-id="a5299-141">In una scena di scarsa luminosità, il nero sul bianco funziona.</span><span class="sxs-lookup"><span data-stu-id="a5299-141">Under a low-light scene, black on white works.</span></span> <span data-ttu-id="a5299-142">Analogamente, se lo sfondo del codice è particolarmente scuro, provare a usare un codice nero in grigio se la frequenza di rilevamento è bassa.</span><span class="sxs-lookup"><span data-stu-id="a5299-142">Likewise, if the backdrop to the code is particularly dark, try a black on gray code if your detection rate is low.</span></span> <span data-ttu-id="a5299-143">In caso contrario, se lo sfondo è più chiaro, un codice normale dovrebbe funzionare correttamente.</span><span class="sxs-lookup"><span data-stu-id="a5299-143">Otherwise, if the backdrop is lighter, a regular code should work fine.</span></span>

## <a name="qrtracking-api"></a><span data-ttu-id="a5299-144">API QRTracking</span><span class="sxs-lookup"><span data-stu-id="a5299-144">QRTracking API</span></span>

<span data-ttu-id="a5299-145">Il plug-in QRTracking espone le API per il rilevamento del codice a matrice.</span><span class="sxs-lookup"><span data-stu-id="a5299-145">The QRTracking plugin exposes the APIs for QR code tracking.</span></span> <span data-ttu-id="a5299-146">Per usare il plug-in, è necessario usare i tipi seguenti dello spazio dei nomi *QRCodesTrackerPlugin* .</span><span class="sxs-lookup"><span data-stu-id="a5299-146">To use the plugin, you will need to use the following types from the *QRCodesTrackerPlugin* namespace.</span></span>

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

## <a name="implementing-qr-code-tracking-in-unity"></a><span data-ttu-id="a5299-147">Implementazione del rilevamento del codice a matrice in Unity</span><span class="sxs-lookup"><span data-stu-id="a5299-147">Implementing QR code tracking in Unity</span></span>

### <a name="sample-unity-scenes-in-mrtk-mixed-reality-toolkit"></a><span data-ttu-id="a5299-148">Scene Unity di esempio in MRTK (Toolkit realtà mista)</span><span class="sxs-lookup"><span data-stu-id="a5299-148">Sample Unity scenes in MRTK (Mixed Reality Toolkit)</span></span>

<span data-ttu-id="a5299-149">È possibile trovare un esempio di come usare l'API di rilevamento a matrice nel [sito GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker)di Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="a5299-149">You can find an example for how to use the QR Tracking API in the Mixed Reality Toolkit [GitHub site](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker).</span></span>

<span data-ttu-id="a5299-150">MRTK ha implementato gli script necessari per simpilify l'utilizzo del rilevamento a barre.</span><span class="sxs-lookup"><span data-stu-id="a5299-150">MRTK has implemented the needed scripts to simpilify the QR tracking usage.</span></span> <span data-ttu-id="a5299-151">Tutte le risorse necessarie per lo sviluppo di app di rilevamento a barre si trovano nella cartella "QRTracker".</span><span class="sxs-lookup"><span data-stu-id="a5299-151">All necessary assets to develop QR tracking apps are in the "QRTracker" folder.</span></span> <span data-ttu-id="a5299-152">Ci sono due scene: il primo è un esempio che mostra semplicemente i dettagli dei codici a matrice quando vengono rilevati e il secondo illustra come usare il sistema di coordinate collegato al codice a matrice per visualizzare gli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="a5299-152">There are two scenes: the first is a sample to simply show details of the QR codes as they are detected, and the second demonstrates how to use the coordinate system attached to the QR code to display holograms.</span></span>
<span data-ttu-id="a5299-153">È disponibile un "QRScanner" prefabbricato che ha aggiunto tutti gli script necessari per l'uso di QRCodes.</span><span class="sxs-lookup"><span data-stu-id="a5299-153">There is a prefab "QRScanner" which added all the necessary scripts to the scenes to use QRCodes.</span></span> <span data-ttu-id="a5299-154">Lo script QRCodeManager è una classe singleton che implementa l'API QRCode.</span><span class="sxs-lookup"><span data-stu-id="a5299-154">The script QRCodeManager is a singleton class that implements the QRCode API.</span></span> <span data-ttu-id="a5299-155">Questa operazione deve essere aggiunta alla scena.</span><span class="sxs-lookup"><span data-stu-id="a5299-155">This needs to be added to your scene.</span></span> <span data-ttu-id="a5299-156">Lo script "AttachToQRCode" viene usato per alleghire gli ologrammi ai sistemi di coordinate del codice a matrice. questo script può essere aggiunto a qualsiasi ologramma.</span><span class="sxs-lookup"><span data-stu-id="a5299-156">The script "AttachToQRCode" is used to attach holograms to the QR Code coordinate systems, this script can be added to any of your holograms.</span></span> <span data-ttu-id="a5299-157">In "SpatialGraphCoordinateSystem" viene illustrato come utilizzare il sistema di coordinate QRCode.</span><span class="sxs-lookup"><span data-stu-id="a5299-157">The "SpatialGraphCoordinateSystem" shows how to use the QRCode coordinate system.</span></span> <span data-ttu-id="a5299-158">Questi script possono essere usati così come sono nelle scene del progetto oppure è possibile scrivere direttamente usando il plug-in come descritto in precedenza.</span><span class="sxs-lookup"><span data-stu-id="a5299-158">These scripts can be used as-is in your project scenes or you can write your own directly using the plugin as described above.</span></span>

### <a name="implementing-qr-code-tracking-in-unity-without-mrtk"></a><span data-ttu-id="a5299-159">Implementazione del rilevamento del codice a matrice in Unity senza MRTK</span><span class="sxs-lookup"><span data-stu-id="a5299-159">Implementing QR code tracking in Unity without MRTK</span></span>

<span data-ttu-id="a5299-160">È anche possibile usare l'API di rilevamento a matrice in Unity senza dipendere da MRTK.</span><span class="sxs-lookup"><span data-stu-id="a5299-160">You can also use the QR Tracking API in Unity without taking a dependency on MRTK.</span></span> <span data-ttu-id="a5299-161">Per usare l'API, sarà necessario preparare il progetto con l'istruzione seguente:</span><span class="sxs-lookup"><span data-stu-id="a5299-161">In order to use the API, you will need to prepare your project with the following instruction:</span></span>

1. <span data-ttu-id="a5299-162">Creare una nuova cartella nella cartella assets del progetto Unity con il nome: "Plug-in".</span><span class="sxs-lookup"><span data-stu-id="a5299-162">Create a new folder in the assets folder of your unity project with the name: "Plugins".</span></span>
2. <span data-ttu-id="a5299-163">Copiare tutti i file necessari da [questa cartella](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins) nella cartella "plugins" locale appena creata.</span><span class="sxs-lookup"><span data-stu-id="a5299-163">Copy all the required files from [this folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins) into the local "Plugins" folder you just created.</span></span>
3. <span data-ttu-id="a5299-164">È possibile usare gli script di rilevamento a matrice nella [cartella degli script di MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts) o scrivere i propri.</span><span class="sxs-lookup"><span data-stu-id="a5299-164">You can use the QR tracking scripts in the [MRTK scripts folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts) or write your own.</span></span>
<span data-ttu-id="a5299-165">Nota: Questi plug-in sono solo per le compilazioni di [aggiornamento 2018 di Windows 10 ottobre (noto anche come RS5)](release-notes-october-2018.md) .</span><span class="sxs-lookup"><span data-stu-id="a5299-165">Note: These plugins are only for [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md) builds.</span></span> <span data-ttu-id="a5299-166">I plug-in verranno aggiornati con la versione successiva di Windows.</span><span class="sxs-lookup"><span data-stu-id="a5299-166">The plugins will be updated with the next windows release.</span></span> <span data-ttu-id="a5299-167">I plug-in correnti sono sperimentali e non funzioneranno per la versione futura di Windows.</span><span class="sxs-lookup"><span data-stu-id="a5299-167">The current plugins were experimental and will not work for future version of the windows.</span></span> <span data-ttu-id="a5299-168">Verranno pubblicati nuovi plug-in che possono essere usati dalla versione successiva di Windows e non saranno compatibili con le versioni precedenti e non funzioneranno con RS5.</span><span class="sxs-lookup"><span data-stu-id="a5299-168">New plugins will be published which can be used from next windows release and they will not be backwards compatable and will not work with RS5).</span></span>

## <a name="implementing-qr-code-tracking-in-directx"></a><span data-ttu-id="a5299-169">Implementazione del rilevamento del codice a matrice in DirectX</span><span class="sxs-lookup"><span data-stu-id="a5299-169">Implementing QR code tracking in DirectX</span></span>

<span data-ttu-id="a5299-170">Per usare QRTrackingPlugin in Visual Studio, è necessario aggiungere il riferimento di QRTrackingPlugin a. winmd.</span><span class="sxs-lookup"><span data-stu-id="a5299-170">To use the QRTrackingPlugin in Visual Studio, you will need to add reference of the QRTrackingPlugin to the .winmd.</span></span> <span data-ttu-id="a5299-171">Qui è possibile trovare i [file necessari per le piattaforme supportate](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA).</span><span class="sxs-lookup"><span data-stu-id="a5299-171">You can find the [required files for supported platforms here](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA).</span></span>

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

## <a name="getting-a-coordinate-system"></a><span data-ttu-id="a5299-172">Recupero di un sistema di coordinate</span><span class="sxs-lookup"><span data-stu-id="a5299-172">Getting a coordinate system</span></span>

<span data-ttu-id="a5299-173">Si definisce un sistema di coordinate di destra allineato con il codice a matrice nell'angolo superiore sinistro del quadrato di rilevamento rapido in alto a sinistra.</span><span class="sxs-lookup"><span data-stu-id="a5299-173">We define a right-hand coordinate system aligned with the QR code at the top left corner of the fast detection square in the top left.</span></span> <span data-ttu-id="a5299-174">Il sistema di coordinate è illustrato di seguito.</span><span class="sxs-lookup"><span data-stu-id="a5299-174">The coordinate system is shown below.</span></span> <span data-ttu-id="a5299-175">L'asse Z punta alla carta (non mostrata), ma in Unity l'asse z è esterno alla carta e a sinistra.</span><span class="sxs-lookup"><span data-stu-id="a5299-175">The Z-axis is pointing into the paper (not shown), but in Unity the z-axis is out of the paper and left-handed.</span></span>

<span data-ttu-id="a5299-176">Viene definito un SpatialCoordinateSystem che è allineato come illustrato.</span><span class="sxs-lookup"><span data-stu-id="a5299-176">A SpatialCoordinateSystem is defined that is aligned as shown.</span></span> <span data-ttu-id="a5299-177">Questo sistema di coordinate può essere ottenuto dalla piattaforma usando le *finestre API::P erception:: Spatial::P Review:: SpatialGraphInteropPreview:: CreateCoordinateSystemForNode*.</span><span class="sxs-lookup"><span data-stu-id="a5299-177">This coordinate system can be obtained from the platform using the API *Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode*.</span></span>

![Sistema di coordinate del codice a matrice](images/Qr-coordinatesystem.png) 

<span data-ttu-id="a5299-179">Dall'oggetto di codice QRCode ^, il codice seguente illustra come creare un rettangolo e inserirlo nel sistema di coordinate QR:</span><span class="sxs-lookup"><span data-stu-id="a5299-179">From QRCode^ Code object, the following code shows how to create a rectangle and put it in QR coordinate system:</span></span>

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

<span data-ttu-id="a5299-180">È possibile utilizzare le dimensioni fisiche per creare il rettangolo QR:</span><span class="sxs-lookup"><span data-stu-id="a5299-180">You can use the physical size to create the QR rectangle:</span></span>

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

<span data-ttu-id="a5299-181">Il sistema di coordinate può essere usato per creare il codice a matrice o per alleghire gli ologrammi al percorso:</span><span class="sxs-lookup"><span data-stu-id="a5299-181">The coordinate system can be used to draw the QR code or attach holograms to the location:</span></span>

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->Id);
```

<span data-ttu-id="a5299-182">Il valore di *QRCodesTrackerPlugin:: QRCodeAddedHandler* potrebbe essere simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="a5299-182">Altogether, your *QRCodesTrackerPlugin::QRCodeAddedHandler* may look something like this:</span></span>

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

## <a name="troubleshooting-and-faq"></a><span data-ttu-id="a5299-183">Risoluzione dei problemi e domande frequenti</span><span class="sxs-lookup"><span data-stu-id="a5299-183">Troubleshooting and FAQ</span></span>

<span data-ttu-id="a5299-184">**Risoluzione dei problemi generali**</span><span class="sxs-lookup"><span data-stu-id="a5299-184">**General troubleshooting**</span></span>

* <span data-ttu-id="a5299-185">Il PC esegue l'aggiornamento di Windows 10 ottobre 2018?</span><span class="sxs-lookup"><span data-stu-id="a5299-185">Is your PC running the Windows 10 October 2018 Update?</span></span>
* <span data-ttu-id="a5299-186">Si è impostato il tasto reg?</span><span class="sxs-lookup"><span data-stu-id="a5299-186">Have you set the reg key?</span></span> <span data-ttu-id="a5299-187">Il dispositivo è stato riavviato in seguito?</span><span class="sxs-lookup"><span data-stu-id="a5299-187">Restarted the device afterwards?</span></span>
* <span data-ttu-id="a5299-188">La versione del codice a matrice è supportata?</span><span class="sxs-lookup"><span data-stu-id="a5299-188">Is the QR code version a supported version?</span></span> <span data-ttu-id="a5299-189">L'API corrente supporta fino a QR Code versione 20.</span><span class="sxs-lookup"><span data-stu-id="a5299-189">Current API supports up to QR Code Version 20.</span></span> <span data-ttu-id="a5299-190">È consigliabile usare la versione 5 per l'utilizzo generale.</span><span class="sxs-lookup"><span data-stu-id="a5299-190">We recommend using version 5 for general usage.</span></span> 
* <span data-ttu-id="a5299-191">Il codice a matrice è sufficientemente vicino?</span><span class="sxs-lookup"><span data-stu-id="a5299-191">Are you close enough to the QR code?</span></span> <span data-ttu-id="a5299-192">Più si avvicina la fotocamera al codice a matrice, più alta è la versione del codice a matrice che l'API può supportare.</span><span class="sxs-lookup"><span data-stu-id="a5299-192">The closer the camera is to the QR code, the higher the QR code version the API can support.</span></span>  

<span data-ttu-id="a5299-193">**Quanto è necessario essere vicini al codice a matrice per rilevarlo?**</span><span class="sxs-lookup"><span data-stu-id="a5299-193">**How close do I need to be to the QR code to detect it?**</span></span>

<span data-ttu-id="a5299-194">Ciò dipende dalle dimensioni del codice a matrice e dalla versione.</span><span class="sxs-lookup"><span data-stu-id="a5299-194">This will depend on the size of the QR code, and also what version it is.</span></span> <span data-ttu-id="a5299-195">Per un codice a matrice di versione 1 che varia da 5 cm a 25 cm, la distanza di rilevamento minima varia da 0,15 metri a 0,5 metri.</span><span class="sxs-lookup"><span data-stu-id="a5299-195">For a version 1 QR code varying from 5 cm sides to 25 cm sides, the minimum detection distance ranges from 0.15 meters to 0.5 meters.</span></span> <span data-ttu-id="a5299-196">Il più lontano di questi possono essere rilevati da circa 0,3 metri per le destinazioni di codice a matrice più piccole a 1,4 metri per il più grande.</span><span class="sxs-lookup"><span data-stu-id="a5299-196">The farthest away these can be detected from goes from about 0.3 meters for the smaller QR code targets to 1.4 meters for the bigger.</span></span> <span data-ttu-id="a5299-197">Per i codici QR di dimensioni maggiori, è possibile stimare; la distanza di rilevamento per le dimensioni aumenta in modo lineare.</span><span class="sxs-lookup"><span data-stu-id="a5299-197">For QR codes bigger than that, you can estimate; the detection distance for size increases linearly.</span></span> <span data-ttu-id="a5299-198">Lo strumento di individuazione non funziona con codici a matrice con lati inferiori a 5 cm.</span><span class="sxs-lookup"><span data-stu-id="a5299-198">Our tracker does not work with QR codes with sides smaller than 5 cm.</span></span>

<span data-ttu-id="a5299-199">**I codici QR con logo funzionano?**</span><span class="sxs-lookup"><span data-stu-id="a5299-199">**Do QR codes with logos work?**</span></span>

<span data-ttu-id="a5299-200">I codici QR con logo non sono stati testati e non sono attualmente supportati.</span><span class="sxs-lookup"><span data-stu-id="a5299-200">QR codes with logos have not been tested and are currently unsupported.</span></span>

<span data-ttu-id="a5299-201">**Ricerca per categorie cancellare i codici a matrice dall'app, in modo che non vengano mantenuti?**</span><span class="sxs-lookup"><span data-stu-id="a5299-201">**How do I clear QR codes from my app so they don't persist?**</span></span>

* <span data-ttu-id="a5299-202">I codici a matrice sono conservati solo nella sessione di avvio.</span><span class="sxs-lookup"><span data-stu-id="a5299-202">QR codes are only persisted in the boot session.</span></span> <span data-ttu-id="a5299-203">Dopo aver riavviato (o riavviato il driver), questi verranno rilevati come nuovi oggetti la prossima volta.</span><span class="sxs-lookup"><span data-stu-id="a5299-203">Once you reboot (or restart the driver), they will be gone and detected as new objects next time.</span></span>
* <span data-ttu-id="a5299-204">La cronologia del codice a matrice viene salvata a livello di sistema nella sessione del driver, ma è possibile configurare l'app in modo da ignorare i codici QR più vecchi di un timestamp specifico, se necessario.</span><span class="sxs-lookup"><span data-stu-id="a5299-204">QR code history is saved at the system level in the driver session, but you can configure your app to ignore QR codes older than a specific timestamp if you want.</span></span> <span data-ttu-id="a5299-205">Attualmente l'API supporta la cancellazione della cronologia del codice QR, in quanto più app potrebbero essere interessate ai dati.</span><span class="sxs-lookup"><span data-stu-id="a5299-205">Currently the API does support clearing QR code history, as multiple apps might be interested in the data.</span></span>

<span data-ttu-id="a5299-206">**I plug-in per RS5 e le versioni future non sono compatibili** La versione del plug-in RS5 funziona solo per RS5 e non funzionerà per le versioni future.</span><span class="sxs-lookup"><span data-stu-id="a5299-206">**The plugins for RS5 and future versions are not compatable** RS5 version of the plugin only works for RS5 and will not work for future versions.</span></span> <span data-ttu-id="a5299-207">Il plug-in expermental verrà sostituito con il plug-in reale e dovrebbe essere quello che è possibile usare nelle versioni future di Windows.</span><span class="sxs-lookup"><span data-stu-id="a5299-207">The expermental plugin will be replaced with the real plugin and should be the one that we can use in future versions of the windows.</span></span>

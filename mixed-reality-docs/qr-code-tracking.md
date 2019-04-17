---
title: Codice a matrice di rilevamento
description: Informazioni su come attivare la scansione del codice di rilevamento per le cuffie (VR) coinvolgenti di realtà mista di Windows e implementare la funzionalità nelle app di realtà virtuale.
author: yoyozilla
ms.author: yoyoz
ms.date: 11/06/2018
ms.topic: article
keywords: realtà virtuale, lbe, intrattenimento basato su posizione, vr arcade, codice a matrice arcade, coinvolgenti, codici a matrice,
ms.openlocfilehash: b0f4480496c15f811979f76143acbd456d89e249
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605119"
---
# <a name="qr-code-tracking"></a><span data-ttu-id="8ecd8-104">Codice a matrice di rilevamento</span><span class="sxs-lookup"><span data-stu-id="8ecd8-104">QR code tracking</span></span>

<span data-ttu-id="8ecd8-105">Codice a matrice di rilevamento viene implementato nel driver realtà mista di Windows per immersive auricolari (VR).</span><span class="sxs-lookup"><span data-stu-id="8ecd8-105">QR code tracking is implemented in the Windows Mixed Reality driver for immersive (VR) headsets.</span></span> <span data-ttu-id="8ecd8-106">Abilitando il tracker di codice a matrice nel driver le cuffie, le cuffie esegue l'analisi dei codici a matrice e vengono segnalati per le app interessate.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-106">By enabling the QR code tracker in the headset driver, the headset scans for QR codes and they are reported to interested apps.</span></span> <span data-ttu-id="8ecd8-107">Questa funzionalità è disponibile come di solo il [Windows 10 ottobre 2018 Update (noto anche come RS5)](release-notes-october-2018.md).</span><span class="sxs-lookup"><span data-stu-id="8ecd8-107">This feature is only available as of the [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md).</span></span>

>[!NOTE]
><span data-ttu-id="8ecd8-108">I frammenti di codice in questo articolo illustrano attualmente l'utilizzo di C++/CX invece di C + + 17 conformi C++/WinRT usato nel [ C++ modello di progetto holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="8ecd8-108">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="8ecd8-109">I concetti sono equivalenti per un C++progetto /WinRT, anche se è necessario convertire il codice.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-109">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="device-support"></a><span data-ttu-id="8ecd8-110">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="8ecd8-110">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="8ecd8-111">Funzionalità</span><span class="sxs-lookup"><span data-stu-id="8ecd8-111">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="8ecd8-112"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="8ecd8-112"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="8ecd8-113"><a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></span><span class="sxs-lookup"><span data-stu-id="8ecd8-113"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="8ecd8-114">Codice a matrice di rilevamento</span><span class="sxs-lookup"><span data-stu-id="8ecd8-114">QR code tracking</span></span></td><td style="text-align: center;"></td><td style="text-align: center;"><span data-ttu-id="8ecd8-115">✔️</span><span class="sxs-lookup"><span data-stu-id="8ecd8-115">✔️</span></span></td>
</tr>
</table>

## <a name="enabling-and-disabling-qr-code-tracking-for-your-headset"></a><span data-ttu-id="8ecd8-116">Abilitazione e disabilitazione di codici a matrice di rilevamento per le cuffie codice</span><span class="sxs-lookup"><span data-stu-id="8ecd8-116">Enabling and disabling QR code tracking for your headset</span></span>
<span data-ttu-id="8ecd8-117">Nota: In questa sezione è valida solo per [Windows 10 ottobre 2018 Update (noto anche come RS5)](release-notes-october-2018.md).</span><span class="sxs-lookup"><span data-stu-id="8ecd8-117">Note: This section is only valid for [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md).</span></span> <span data-ttu-id="8ecd8-118">Dalle build di 19 ore 1 o versione successiva non è necessario eseguire questa operazione.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-118">From 19h1 builds onwards you will not have to do this.</span></span>
<span data-ttu-id="8ecd8-119">Se si sta sviluppando un'app di realtà mista che userà codice a matrice di rilevamento o sei un cliente di una di queste App, è necessario attivare manualmente la scansione del codice di rilevamento nel driver del auricolare.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-119">Whether you're developing a mixed reality app that will leverage QR code tracking, or you're a customer of one of these apps, you'll need to manually turn on QR code tracking in your headset's driver.</span></span>

<span data-ttu-id="8ecd8-120">Al fine di **attivare la scansione del codice di rilevamento** per le cuffie (VR) immersive:</span><span class="sxs-lookup"><span data-stu-id="8ecd8-120">In order to **turn on QR code tracking** for your immersive (VR) headset:</span></span>

1. <span data-ttu-id="8ecd8-121">Chiudere l'app del portale di realtà mista nel PC.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-121">Close the Mixed Reality Portal app on your PC.</span></span>
2. <span data-ttu-id="8ecd8-122">Scollegare il visore VR dal PC.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-122">Unplug the headset from your PC.</span></span>
3. <span data-ttu-id="8ecd8-123">Eseguire lo script seguente nel Prompt dei comandi:</span><span class="sxs-lookup"><span data-stu-id="8ecd8-123">Run the following script in the Command Prompt:</span></span><br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 1 /F`
4. <span data-ttu-id="8ecd8-124">Riconnettere le cuffie al computer.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-124">Reconnect your headset to your PC.</span></span>

<span data-ttu-id="8ecd8-125">Al fine di **disattivare la scansione del codice di rilevamento** per le cuffie (VR) immersive:</span><span class="sxs-lookup"><span data-stu-id="8ecd8-125">In order to **turn off QR code tracking** for your immersive (VR) headset:</span></span>

1. <span data-ttu-id="8ecd8-126">Chiudere l'app del portale di realtà mista nel PC.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-126">Close the Mixed Reality Portal app on your PC.</span></span>
2. <span data-ttu-id="8ecd8-127">Scollegare il visore VR dal PC.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-127">Unplug the headset from your PC.</span></span>
3. <span data-ttu-id="8ecd8-128">Eseguire lo script seguente nel Prompt dei comandi:</span><span class="sxs-lookup"><span data-stu-id="8ecd8-128">Run the following script in the Command Prompt:</span></span><br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 0 /F`
4. <span data-ttu-id="8ecd8-129">Riconnettere le cuffie al computer.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-129">Reconnect your headset to your PC.</span></span> <span data-ttu-id="8ecd8-130">In questo modo tutti i codici a matrice individuati "non individuabili."</span><span class="sxs-lookup"><span data-stu-id="8ecd8-130">This will make any discovered QR codes "non-locatable."</span></span>

## <a name="printing-codes"></a><span data-ttu-id="8ecd8-131">Codici di stampa</span><span class="sxs-lookup"><span data-stu-id="8ecd8-131">Printing codes</span></span>

<span data-ttu-id="8ecd8-132">In primo luogo, il [specifiche per i codici a matrice](https://www.qrcode.com/en/howto/code.html) afferma "l'area di simboli di codice a matrice è necessario un margine o una"zona quiet"intorno a esso da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-132">First and foremost, the [spec for QR codes](https://www.qrcode.com/en/howto/code.html) says "The QR Code symbol area requires a margin or "quiet zone" around it to be used.</span></span> <span data-ttu-id="8ecd8-133">Il margine è un'area chiara intorno a un simbolo in cui viene stampato niente.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-133">The margin is a clear area around a symbol where nothing is printed.</span></span> <span data-ttu-id="8ecd8-134">Codice a matrice è necessario un ampio margine di quattro-module in tutti i lati di un simbolo".</span><span class="sxs-lookup"><span data-stu-id="8ecd8-134">QR Code requires a four-module wide margin at all sides of a symbol."</span></span> <span data-ttu-id="8ecd8-135">Questa operazione deve avere una larghezza, in ogni lato di quattro volte le dimensioni di un modulo - un singolo quadrato nero nel codice.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-135">This needs to have a width, on every side, of four times the size of a module - a single black square in the code.</span></span> <span data-ttu-id="8ecd8-136">La pagina specifica contiene consigli su come stampare i codici a matrice e individuare l'area richiesta per rendere un determinato codice a matrice con dimensione.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-136">The spec page contains advice on how to print QR codes and figure out the area required to make a certain sized QR code.</span></span>

<span data-ttu-id="8ecd8-137">La qualità del rilevamento di codice a matrice è attualmente soggetta a vari illuminazione e sfondo.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-137">Currently QR code detection quality is susceptible to varying illumination and backdrop.</span></span> <span data-ttu-id="8ecd8-138">Per evitare questo inconveniente, si noti l'illuminazione e stampare il codice appropriato.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-138">To combat this, note your illumination and print the appropriate code.</span></span> <span data-ttu-id="8ecd8-139">In una scena con estrema particolarmente luminosità, stampa un codice che è nero su sfondo grigio.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-139">In a scene with particularly bright lighting, print a code that is black on a gray background.</span></span> <span data-ttu-id="8ecd8-140">In una scena scarsa luminosità nera su bianco works.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-140">Under a low-light scene, black on white works.</span></span> <span data-ttu-id="8ecd8-141">Analogamente, se lo sfondo per il codice è particolarmente scuro, provare a nero sul codice grigia se la frequenza di rilevamento è bassa.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-141">Likewise, if the backdrop to the code is particularly dark, try a black on gray code if your detection rate is low.</span></span> <span data-ttu-id="8ecd8-142">In caso contrario, se lo sfondo più chiaro, un codice regolare dovrebbe funzionare correttamente.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-142">Otherwise, if the backdrop is lighter, a regular code should work fine.</span></span>

## <a name="qrtracking-api"></a><span data-ttu-id="8ecd8-143">QRTracking API</span><span class="sxs-lookup"><span data-stu-id="8ecd8-143">QRTracking API</span></span>

<span data-ttu-id="8ecd8-144">Il plug-in QRTracking espone le API per il codice a matrice di rilevamento.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-144">The QRTracking plugin exposes the APIs for QR code tracking.</span></span> <span data-ttu-id="8ecd8-145">Per usare il plug-in, è necessario usare i tipi di seguito il *QRCodesTrackerPlugin* dello spazio dei nomi.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-145">To use the plugin, you will need to use the following types from the *QRCodesTrackerPlugin* namespace.</span></span>

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

## <a name="implementing-qr-code-tracking-in-unity"></a><span data-ttu-id="8ecd8-146">Implementazione di codice a matrice di rilevamento in Unity</span><span class="sxs-lookup"><span data-stu-id="8ecd8-146">Implementing QR code tracking in Unity</span></span>

### <a name="sample-unity-scenes-in-mrtk-mixed-reality-toolkit"></a><span data-ttu-id="8ecd8-147">In background di Unity di esempio nelle MRTK (Toolkit di realtà mista)</span><span class="sxs-lookup"><span data-stu-id="8ecd8-147">Sample Unity scenes in MRTK (Mixed Reality Toolkit)</span></span>

<span data-ttu-id="8ecd8-148">È possibile trovare un esempio di come usare l'API di gestione di codici a matrice nel Toolkit di realtà mista [sito GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker).</span><span class="sxs-lookup"><span data-stu-id="8ecd8-148">You can find an example for how to use the QR Tracking API in the Mixed Reality Toolkit [GitHub site](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker).</span></span>

<span data-ttu-id="8ecd8-149">MRTK ha implementato gli script necessari per simpilify i codici a matrice per tracciare l'utilizzo.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-149">MRTK has implemented the needed scripts to simpilify the QR tracking usage.</span></span> <span data-ttu-id="8ecd8-150">Tutte le risorse necessarie per sviluppare a matrice di tenere traccia delle applicazioni si trovano nella cartella "QRTracker".</span><span class="sxs-lookup"><span data-stu-id="8ecd8-150">All necessary assets to develop QR tracking apps are in the "QRTracker" folder.</span></span> <span data-ttu-id="8ecd8-151">Esistono due scene: il primo è un esempio per visualizzare semplicemente i dettagli dei codici QR quando vengono rilevati e la seconda viene illustrato come utilizzare il sistema di coordinate collegato del codice a matrice per visualizzare vntana.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-151">There are two scenes: the first is a sample to simply show details of the QR codes as they are detected, and the second demonstrates how to use the coordinate system attached to the QR code to display holograms.</span></span>
<span data-ttu-id="8ecd8-152">È presente un prefab "QRScanner" che aggiunto tutti i scrips necessari per le scene usare QRCodes.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-152">There is a prefab "QRScanner" which added all the necessary scrips to the scenes to use QRCodes.</span></span> <span data-ttu-id="8ecd8-153">Lo script QRCodeManager è una classe singileton che implementa l'API QRCode è possibile aggiungerlo alla scena si.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-153">The script QRCodeManager is a singileton class that implements the QRCode API you can add it to you scene.</span></span> <span data-ttu-id="8ecd8-154">Gli script "AttachToQRCode" viene usata per collegare vntana ai sistemi coodridnate codice a matrice, questo script può essere aggiunto a uno qualsiasi dei vntana.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-154">The scripts "AttachToQRCode" is used to attach holograms to the QR Code coodridnate systems, this script can be added to any of your holograms.</span></span> <span data-ttu-id="8ecd8-155">"SpatialGraphCoordinateSystem" viene illustrato come utilizzare il sistema di coordinate QRCode.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-155">The "SpatialGraphCoordinateSystem" shows how to use the QRCode coordinate system.</span></span> <span data-ttu-id="8ecd8-156">Questi script possono essere usati quando è nelle scene progetto oppure è possibile scrivere il proprio direttamente usando il plug-in come descritto in precedenza.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-156">These scripts can be used as is in your project scenes or you can write your own directly using the plugin as described above.</span></span>

### <a name="implementing-qr-code-tracking-in-unity-without-mrtk"></a><span data-ttu-id="8ecd8-157">Implementazione di codice a matrice in Unity senza MRTK di rilevamento</span><span class="sxs-lookup"><span data-stu-id="8ecd8-157">Implementing QR code tracking in Unity without MRTK</span></span>

<span data-ttu-id="8ecd8-158">È anche possibile usare l'API di gestione di codici a matrice in Unity senza creare una dipendenza da MRTK.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-158">You can also use the QR Tracking API in Unity without taking a dependency on MRTK.</span></span> <span data-ttu-id="8ecd8-159">Per usare l'API, è necessario preparare il progetto con l'istruzione seguente:</span><span class="sxs-lookup"><span data-stu-id="8ecd8-159">In order to use the API, you will need to prepare your project with the following instruction:</span></span>

1. <span data-ttu-id="8ecd8-160">Creare una nuova cartella nella cartella assets del progetto unity con il nome: "I"plug-in.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-160">Create a new folder in the assets folder of your unity project with the name: "Plugins".</span></span>
2. <span data-ttu-id="8ecd8-161">Copiare tutti i file richiesti da [in questa cartella](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins) nella cartella "Plug-in" locale appena creato.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-161">Copy all the required files from [this folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins) into the local "Plugins" folder you just created.</span></span>
3. <span data-ttu-id="8ecd8-162">È possibile usare i codici a matrice di rilevamento degli script nel [cartella scripts MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts) o scriverne uno proprio.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-162">You can use the QR tracking scripts in the [MRTK scripts folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts) or write your own.</span></span>
<span data-ttu-id="8ecd8-163">Nota: Questi plug-in sono solo per [Windows 10 ottobre 2018 Update (noto anche come RS5)](release-notes-october-2018.md) compilazioni.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-163">Note: These plugins are only for [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md) builds.</span></span> <span data-ttu-id="8ecd8-164">I plug-in verrà aggiornato con la prossima versione di windows.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-164">The plugins will be updated with the next windows release.</span></span> <span data-ttu-id="8ecd8-165">I plug-in correnti sono sperimentali e non funzioneranno per versioni future di windows.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-165">The current plugins were experimental and will not work for future version of the windows.</span></span> <span data-ttu-id="8ecd8-166">Verranno pubblicati nuovi plug-in che può essere usato dalla prossima versione di windows e non sarà con le versioni precedenti compatibile e non funzionerà con RS5).</span><span class="sxs-lookup"><span data-stu-id="8ecd8-166">New plugins will be published which can be used from next windows release and they will not be backwards compatable and will not work with RS5).</span></span>

## <a name="implementing-qr-code-tracking-in-directx"></a><span data-ttu-id="8ecd8-167">Implementazione di codice a matrice di rilevamento in DirectX</span><span class="sxs-lookup"><span data-stu-id="8ecd8-167">Implementing QR code tracking in DirectX</span></span>

<span data-ttu-id="8ecd8-168">Per usare il QRTrackingPlugin in Visual Studio, è necessario aggiungere il riferimento del QRTrackingPlugin ai. winmd.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-168">To use the QRTrackingPlugin in Visual Studio, you will need to add reference of the QRTrackingPlugin to the .winmd.</span></span> <span data-ttu-id="8ecd8-169">È possibile trovare il [i file richiesti per le piattaforme supportate qui](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA).</span><span class="sxs-lookup"><span data-stu-id="8ecd8-169">You can find the [required files for supported platforms here](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA).</span></span>

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

## <a name="getting-a-coordinate-system"></a><span data-ttu-id="8ecd8-170">Recupero di un sistema di coordinate</span><span class="sxs-lookup"><span data-stu-id="8ecd8-170">Getting a coordinate system</span></span>

<span data-ttu-id="8ecd8-171">Definiamo un sistema di coordinate di destra allineato con il codice a matrice nell'angolo superiore sinistro del quadrato rilevamento rapido in alto a sinistra.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-171">We define a right-hand coordinate system aligned with the QR code at the top left corner of the fast detection square in the top left.</span></span> <span data-ttu-id="8ecd8-172">Il sistema di coordinate è illustrato di seguito.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-172">The coordinate system is shown below.</span></span> <span data-ttu-id="8ecd8-173">L'asse z fa riferimento nel documento di (non illustrato), ma in Unity all'asse z è la carta esaurita e battitori.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-173">The Z-axis is pointing into the paper (not shown), but in Unity the z-axis is out of the paper and left-handed.</span></span>

<span data-ttu-id="8ecd8-174">Viene definito un SpatialCoordinateSystem allineata come illustrato.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-174">A SpatialCoordinateSystem is defined that is aligned as shown.</span></span> <span data-ttu-id="8ecd8-175">Questo sistema di coordinate può essere ottenuto dalla piattaforma usando l'API *Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode*.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-175">This coordinate system can be obtained from the platform using the API *Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode*.</span></span>

![Sistema di coordinate del codice a matrice](images/Qr-coordinatesystem.png) 

<span data-ttu-id="8ecd8-177">Da QRCode ^ codice oggetto, il codice seguente viene illustrato come creare un rettangolo e inserirlo nel sistema di coordinate di codici a matrice:</span><span class="sxs-lookup"><span data-stu-id="8ecd8-177">From QRCode^ Code object, the following code shows how to create a rectangle and put it in QR coordinate system:</span></span>

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

<span data-ttu-id="8ecd8-178">La dimensione fisica è possibile usare per creare il rettangolo di codici a matrice:</span><span class="sxs-lookup"><span data-stu-id="8ecd8-178">You can use the physical size to create the QR rectangle:</span></span>

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

<span data-ttu-id="8ecd8-179">Il sistema di coordinate è utilizzabile per disegnare la scansione del codice o collegare vntana nel percorso:</span><span class="sxs-lookup"><span data-stu-id="8ecd8-179">The coordinate system can be used to draw the QR code or attach holograms to the location:</span></span>

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->Id);
```

<span data-ttu-id="8ecd8-180">Completamente, il *QRCodesTrackerPlugin::QRCodeAddedHandler* potrebbe avere un aspetto simile:</span><span class="sxs-lookup"><span data-stu-id="8ecd8-180">Altogether, your *QRCodesTrackerPlugin::QRCodeAddedHandler* may look something like this:</span></span>

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

## <a name="troubleshooting-and-faq"></a><span data-ttu-id="8ecd8-181">Risoluzione dei problemi e domande frequenti</span><span class="sxs-lookup"><span data-stu-id="8ecd8-181">Troubleshooting and FAQ</span></span>

<span data-ttu-id="8ecd8-182">**Risoluzione dei problemi generali**</span><span class="sxs-lookup"><span data-stu-id="8ecd8-182">**General troubleshooting**</span></span>

* <span data-ttu-id="8ecd8-183">Sia i PC che eseguono Windows 10 ottobre 2018 Update?</span><span class="sxs-lookup"><span data-stu-id="8ecd8-183">Is your PC running the Windows 10 October 2018 Update?</span></span>
* <span data-ttu-id="8ecd8-184">È stata impostata la chiave reg?</span><span class="sxs-lookup"><span data-stu-id="8ecd8-184">Have you set the reg key?</span></span> <span data-ttu-id="8ecd8-185">Riavviare il dispositivo in un secondo momento?</span><span class="sxs-lookup"><span data-stu-id="8ecd8-185">Restarted the device afterwards?</span></span>
* <span data-ttu-id="8ecd8-186">È la versione del codice a matrice di una versione supportata?</span><span class="sxs-lookup"><span data-stu-id="8ecd8-186">Is the QR code version a supported version?</span></span> <span data-ttu-id="8ecd8-187">Supporto di API corrente fino a 20 versione di codice a matrice.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-187">Current API supports up to QR Code Version 20.</span></span> <span data-ttu-id="8ecd8-188">È consigliabile usare la versione 5 per l'utilizzo generale.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-188">We recommend using version 5 for general usage.</span></span> 
* <span data-ttu-id="8ecd8-189">Si abbastanza ravvicinati per la scansione del codice?</span><span class="sxs-lookup"><span data-stu-id="8ecd8-189">Are you close enough to the QR code?</span></span> <span data-ttu-id="8ecd8-190">È vicino alla fotocamera del codice a matrice, maggiore sarà la versione di codice l'API di codici a matrice può supportare.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-190">The closer the camera is to the QR code, the higher the QR code version the API can support.</span></span>  

<span data-ttu-id="8ecd8-191">**La distanza è necessario essere al codice a matrice per individuarlo?**</span><span class="sxs-lookup"><span data-stu-id="8ecd8-191">**How close do I need to be to the QR code to detect it?**</span></span>

<span data-ttu-id="8ecd8-192">Ciò dipende la dimensione del codice a matrice e inoltre quale versione è.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-192">This will depend on the size of the QR code, and also what version it is.</span></span> <span data-ttu-id="8ecd8-193">Per un codice a matrice di versione 1 compreso tra i lati cm 5 e i lati 25 cm, la distanza minima di rilevamento compreso tra 0,15 metri e metri 0,5.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-193">For a version 1 QR code varying from 5 cm sides to 25 cm sides, the minimum detection distance ranges from 0.15 meters to 0.5 meters.</span></span> <span data-ttu-id="8ecd8-194">Il più lontano da subito questi possono essere rilevati da passa da circa 0.3 contatori per le destinazioni di codice a matrice inferiori a 1,4 i contatori per il più grande.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-194">The farthest away these can be detected from goes from about 0.3 meters for the smaller QR code targets to 1.4 meters for the bigger.</span></span> <span data-ttu-id="8ecd8-195">Per i codici a matrice più grandi rispetto a quello, è possibile stimare; la distanza di rilevamento per le dimensioni aumenta in modo lineare.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-195">For QR codes bigger than that, you can estimate; the detection distance for size increases linearly.</span></span> <span data-ttu-id="8ecd8-196">La registrazione non funziona con i codici a matrice con i lati inferiori a 5 cm.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-196">Our tracker does not work with QR codes with sides smaller than 5 cm.</span></span>

<span data-ttu-id="8ecd8-197">**Eseguire i codici a matrice con logo lavoro?**</span><span class="sxs-lookup"><span data-stu-id="8ecd8-197">**Do QR codes with logos work?**</span></span>

<span data-ttu-id="8ecd8-198">I codici a matrice con logo non sono stati testati e sono attualmente supportati.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-198">QR codes with logos have not been tested and are currently unsupported.</span></span>

<span data-ttu-id="8ecd8-199">**Come si cancella i codici a matrice dall'app in modo che non vengono mantenute?**</span><span class="sxs-lookup"><span data-stu-id="8ecd8-199">**How do I clear QR codes from my app so they don't persist?**</span></span>

* <span data-ttu-id="8ecd8-200">I codici a matrice vengono resi persistenti solo nella sessione di avvio.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-200">QR codes are only persisted in the boot session.</span></span> <span data-ttu-id="8ecd8-201">Dopo il riavvio (o riavviare il driver), verranno eseguiti e rilevati come nuovi oggetti successivo.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-201">Once you reboot (or restart the driver), they will be gone and detected as new objects next time.</span></span>
* <span data-ttu-id="8ecd8-202">Cronologia del codice a matrice viene salvata a livello di sistema nella sessione di driver, ma è possibile configurare l'app per ignorare i codici a matrice antecedenti a un timestamp specifico, se si desidera.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-202">QR code history is saved at the system level in the driver session, but you can configure your app to ignore QR codes older than a specific timestamp if you want.</span></span> <span data-ttu-id="8ecd8-203">Attualmente l'API supporta cronologia del codice a matrice di cancellazione, come le app più potrebbero essere interessate a dati.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-203">Currently the API does support clearing QR code history, as multiple apps might be interested in the data.</span></span>

<span data-ttu-id="8ecd8-204">**I plug-in per RS5 e nelle versioni future non sono compatibile** versione RS5 del plug-in funziona solo per RS5 e non funzioneranno per le versioni future.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-204">**The plugins for RS5 and future versions are not compatable** RS5 version of the plugin only works for RS5 and will not work for future versions.</span></span> <span data-ttu-id="8ecd8-205">Il plug-in expermental verrà sostituito con il plug-in reali e deve essere quello che è possibile usare nelle future versioni di windows.</span><span class="sxs-lookup"><span data-stu-id="8ecd8-205">The expermental plugin will be replaced with the real plugin and should be the one that we can use in future versions of the windows.</span></span>

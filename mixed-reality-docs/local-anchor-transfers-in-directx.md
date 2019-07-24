---
title: Trasferimenti di ancoraggio locali in DirectX
description: Viene illustrato come sincronizzare due dispositivi HoloLens trasferendo ancoraggi spaziali.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, Synchronize, ancoraggio spaziale, trasferimento, multiplayer, visualizzazione, scenario, procedura dettagliata, codice di esempio, trasferimento, trasferimento di ancoraggio locale, esportazione di ancoraggio, importazione di ancoraggio
ms.openlocfilehash: 5d03f4bfa764b9948ec4718bce86127cfcc3e303
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63515477"
---
# <a name="local-anchor-transfers-in-directx"></a><span data-ttu-id="416be-104">Trasferimenti di ancoraggio locali in DirectX</span><span class="sxs-lookup"><span data-stu-id="416be-104">Local anchor transfers in DirectX</span></span>

<span data-ttu-id="416be-105">Nei casi in cui non è possibile usare gli <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">ancoraggi spaziali di Azure</a>, i trasferimenti di ancoraggio locali consentono a un dispositivo HoloLens di esportare un ancoraggio per l'importazione da parte di un secondo dispositivo HoloLens.</span><span class="sxs-lookup"><span data-stu-id="416be-105">In situations where you cannot use <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, local anchor transfers enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>

>[!NOTE]
><span data-ttu-id="416be-106">I trasferimenti di ancoraggio locali forniscono un richiamo di ancoraggio meno affidabile rispetto agli <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">ancoraggi spaziali di Azure</a>e i dispositivi iOS e Android non sono supportati da questo approccio.</span><span class="sxs-lookup"><span data-stu-id="416be-106">Local anchor transfers provide less robust anchor recall than <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, and iOS and Android devices are not supported by this approach.</span></span>

>[!NOTE]
><span data-ttu-id="416be-107">I frammenti di codice in questo articolo illustrano attualmente l' C++uso di/CX, invece di/WinRT conformi C++a C + 17 come usato nel modello di [ C++ progetto olografico](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="416be-107">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="416be-108">I concetti sono equivalenti per C++un progetto/WinRT, anche se sarà necessario tradurre il codice.</span><span class="sxs-lookup"><span data-stu-id="416be-108">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="transferring-spatial-anchors"></a><span data-ttu-id="416be-109">Trasferimento di ancoraggi spaziali</span><span class="sxs-lookup"><span data-stu-id="416be-109">Transferring spatial anchors</span></span>

<span data-ttu-id="416be-110">È possibile trasferire gli ancoraggi spaziali tra i dispositivi di realtà mista di Windows usando [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx).</span><span class="sxs-lookup"><span data-stu-id="416be-110">You can transfer spatial anchors between Windows Mixed Reality devices by using the [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx).</span></span> <span data-ttu-id="416be-111">Questa API consente di aggregare un ancoraggio con tutti i dati del sensore di supporto necessari per trovare la posizione esatta del mondo e quindi importare il bundle in un altro dispositivo.</span><span class="sxs-lookup"><span data-stu-id="416be-111">This API lets you bundle up an anchor with all the supporting sensor data needed to find that exact place in the world, and then import that bundle on another device.</span></span> <span data-ttu-id="416be-112">Dopo che l'app nel secondo dispositivo ha importato l'ancoraggio, ogni app può eseguire il rendering degli ologrammi usando il sistema di coordinate dell'ancoraggio spaziale condiviso, che verrà quindi visualizzato nella stessa posizione del mondo reale.</span><span class="sxs-lookup"><span data-stu-id="416be-112">Once the app on the second device has imported that anchor, each app can render holograms using that shared spatial anchor's coordinate system, which will then appear in the same place in the real world.</span></span>

<span data-ttu-id="416be-113">Si noti che gli ancoraggi spaziali non sono in grado di trasferire tra tipi di dispositivi diversi, ad esempio un ancoraggio spaziale HoloLens potrebbe non essere locatable usando un auricolare immersivo.</span><span class="sxs-lookup"><span data-stu-id="416be-113">Note that spatial anchors are not able to transfer between different device types, for example a HoloLens spatial anchor may not be locatable using an immersive headset.</span></span>  <span data-ttu-id="416be-114">Anche gli ancoraggi trasferiti non sono compatibili con i dispositivi iOS o Android.</span><span class="sxs-lookup"><span data-stu-id="416be-114">Transferred anchors are also not compatible with iOS or Android devices.</span></span>

## <a name="set-up-your-app-to-use-the-spatialperception-capability"></a><span data-ttu-id="416be-115">Configurare l'app per l'uso della funzionalità spatialPerception</span><span class="sxs-lookup"><span data-stu-id="416be-115">Set up your app to use the spatialPerception capability</span></span>

<span data-ttu-id="416be-116">È necessario concedere all'app l'autorizzazione per usare la funzionalità spatialPerception prima di poter usare [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx).</span><span class="sxs-lookup"><span data-stu-id="416be-116">Your app must be granted permission to use the spatialPerception capability before it can use the [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx).</span></span> <span data-ttu-id="416be-117">Questa operazione è necessaria perché il trasferimento di un ancoraggio spaziale comporta la condivisione delle immagini del sensore raccolte nel tempo in prossimità di tale ancoraggio, che potrebbero includere informazioni riservate.</span><span class="sxs-lookup"><span data-stu-id="416be-117">This is necessary because transferring a spatial anchor involves sharing sensor images gathered over time in vicinity of that anchor, which might include sensitive information.</span></span>

<span data-ttu-id="416be-118">Dichiarare questa funzionalità nel file Package. appxmanifest per l'app.</span><span class="sxs-lookup"><span data-stu-id="416be-118">Declare this capability in the package.appxmanifest file for your app.</span></span> <span data-ttu-id="416be-119">Di seguito è riportato un esempio:</span><span class="sxs-lookup"><span data-stu-id="416be-119">Here's an example:</span></span>

```
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

<span data-ttu-id="416be-120">La funzionalità deriva dallo spazio dei nomi **uap2** .</span><span class="sxs-lookup"><span data-stu-id="416be-120">The capability comes from the **uap2** namespace.</span></span> <span data-ttu-id="416be-121">Per ottenere l'accesso a questo spazio dei nomi nel manifesto, includerlo come attributo *xlmns* nell' &lt;elemento > del pacchetto.</span><span class="sxs-lookup"><span data-stu-id="416be-121">To get access to this namespace in your manifest, include it as an *xlmns* attribute in the &lt;Package> element.</span></span> <span data-ttu-id="416be-122">Di seguito è riportato un esempio:</span><span class="sxs-lookup"><span data-stu-id="416be-122">Here's an example:</span></span>

```
<Package
    xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap mp"
    >
```

<span data-ttu-id="416be-123">**NOTA:** L'app dovrà richiedere la funzionalità in fase di esecuzione prima di poter accedere alle API di esportazione/importazione SpatialAnchor.</span><span class="sxs-lookup"><span data-stu-id="416be-123">**NOTE:** Your app will need to request the capability at runtime before it can access SpatialAnchor export/import APIs.</span></span> <span data-ttu-id="416be-124">Vedere [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync.aspx) negli esempi seguenti.</span><span class="sxs-lookup"><span data-stu-id="416be-124">See [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync.aspx) in the examples below.</span></span>

## <a name="serialize-anchor-data-by-exporting-it-with-the-spatialanchortransfermanager"></a><span data-ttu-id="416be-125">Serializzare i dati di ancoraggio esportandoli con SpatialAnchorTransferManager</span><span class="sxs-lookup"><span data-stu-id="416be-125">Serialize anchor data by exporting it with the SpatialAnchorTransferManager</span></span>

<span data-ttu-id="416be-126">Nell'esempio di codice viene inclusa una funzione di supporto per esportare (serializzare) i dati [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) .</span><span class="sxs-lookup"><span data-stu-id="416be-126">A helper function is included in the code sample to export (serialize) [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) data.</span></span> <span data-ttu-id="416be-127">Questa API di esportazione serializza tutti gli ancoraggi in una raccolta di coppie chiave-valore che associa stringhe a ancoraggi.</span><span class="sxs-lookup"><span data-stu-id="416be-127">This export API serializes all anchors in a collection of key-value pairs associating strings with anchors.</span></span>

```
// ExportAnchorDataAsync: Exports a byte buffer containing all of the anchors in the given collection.
//
// This function will place data in a buffer using a std::vector<byte>. The ata buffer contains one or more
// Anchors if one or more Anchors were successfully imported; otherwise, it is ot modified.
//
task<bool> SpatialAnchorImportExportHelper::ExportAnchorDataAsync(
    vector<byte>* anchorByteDataOut,
    IMap<String^, SpatialAnchor^>^ anchorsToExport
    )
{
```

<span data-ttu-id="416be-128">Prima di tutto, è necessario configurare il flusso di dati.</span><span class="sxs-lookup"><span data-stu-id="416be-128">First, we need to set up the data stream.</span></span> <span data-ttu-id="416be-129">Questa operazione consentirà di eseguire 1. usare TryExportAnchorsAsync per inserire i dati in un buffer di proprietà dell'app e 2. leggere i dati dal flusso del buffer di byte esportato, che è un flusso di dati WinRT, nel buffer di memoria, che è un&lt;byte std:: Vector >.</span><span class="sxs-lookup"><span data-stu-id="416be-129">This will allow us to 1.) use TryExportAnchorsAsync to put the data in a buffer owned by the app, and 2.) read data from the exported byte buffer stream - which is a WinRT data stream - into our own memory buffer, which is a std::vector&lt;byte>.</span></span>

```
// Create a random access stream to process the anchor byte data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor byte stream.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
```

<span data-ttu-id="416be-130">È necessario richiedere l'autorizzazione per accedere ai dati spaziali, inclusi i Anchor esportati dal sistema.</span><span class="sxs-lookup"><span data-stu-id="416be-130">We need to ask permission to access spatial data, including anchors that are exported by the system.</span></span>

```
// Request access to spatial data.
auto accessRequestedTask = create_taskSpatialAnchorTransferManager::RequestAccessAsync()).then([anchorsToExport, utputStream](SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Access is allowed.
        // Export the indicated set of anchors.
        return create_task(SpatialAnchorTransferManager::TryExportAnchorsAsync(
            anchorsToExport,
            outputStream
            ));
    }
    else
    {
        // Access is denied.
        return task_from_result<bool>(false);
    }
});
```

<span data-ttu-id="416be-131">Se si esportano le autorizzazioni e si esportano ancoraggi, è possibile leggere il flusso di dati.</span><span class="sxs-lookup"><span data-stu-id="416be-131">If we do get permission and anchors are exported, we can read the data stream.</span></span> <span data-ttu-id="416be-132">Qui viene illustrato anche come creare DataReader e InputStream da usare per leggere i dati.</span><span class="sxs-lookup"><span data-stu-id="416be-132">Here, we also show how to create the DataReader and InputStream we will use to read the data.</span></span>

```
// Get the input stream for the anchor byte stream.
IInputStream^ inputStream = stream->GetInputStreamAt(0);
// Create a DataReader, to get bytes from the anchor byte stream.
DataReader^ reader = ref new DataReader(inputStream);
return accessRequestedTask.then([anchorByteDataOut, stream, reader](bool nchorsExported)
{
    if (anchorsExported)
    {
        // Get the size of the exported anchor byte stream.
        size_t bufferSize = static_cast<size_t>(stream->Size);
        // Resize the output buffer to accept the data from the stream.
        anchorByteDataOut->reserve(bufferSize);
        anchorByteDataOut->resize(bufferSize);
        // Read the exported anchor store into the stream.
        return create_task(reader->LoadAsync(bufferSize));
    }
    else
    {
        return task_from_result<size_t>(0);
    }
```

<span data-ttu-id="416be-133">Dopo aver letto i byte dal flusso, è possibile salvarli nel proprio buffer di dati, come indicato di seguito.</span><span class="sxs-lookup"><span data-stu-id="416be-133">After we read bytes from the stream, we can save them to our own data buffer like so.</span></span>

```
}).then([anchorByteDataOut, reader](size_t bytesRead)
{
    if (bytesRead > 0)
    {
        // Read the bytes from the stream, into our data output buffer.
        reader->ReadBytes(Platform::ArrayReference<byte>(&(*anchorByteDataOut)[0], bytesRead));
        return true;
    }
    else
    {
        return false;
    }
});
};
```

## <a name="deserialize-anchor-data-by-importing-it-into-the-system-using-the-spatialanchortransfermanager"></a><span data-ttu-id="416be-134">Deserializzare i dati di ancoraggio importandoli nel sistema usando SpatialAnchorTransferManager</span><span class="sxs-lookup"><span data-stu-id="416be-134">Deserialize anchor data by importing it into the system using the SpatialAnchorTransferManager</span></span>

<span data-ttu-id="416be-135">Nell'esempio di codice viene inclusa una funzione di supporto per caricare i dati esportati in precedenza.</span><span class="sxs-lookup"><span data-stu-id="416be-135">A helper function is included in the code sample to load previously exported data.</span></span> <span data-ttu-id="416be-136">Questa funzione di deserializzazione fornisce una raccolta di coppie chiave-valore, analogamente a quanto fornito da SpatialAnchorStore, ad eccezione del fatto che sono stati ottenuti questi dati da un'altra origine, ad esempio un socket di rete.</span><span class="sxs-lookup"><span data-stu-id="416be-136">This deserialization function provides a collection of key-value pairs, similar to what the SpatialAnchorStore provides - except that we got this data from another source, such as a network socket.</span></span> <span data-ttu-id="416be-137">È possibile elaborare e ragionare su questi dati prima di archiviarli offline, usando la memoria in-app o (se applicabile) SpatialAnchorStore dell'app.</span><span class="sxs-lookup"><span data-stu-id="416be-137">You can process and reason about this data before storing it offline, using in-app memory, or (if applicable) your app's SpatialAnchorStore.</span></span>

```
// ImportAnchorDataAsync: Imports anchors from a byte buffer that was previously exported.
//
// This function will import all anchors from a data buffer into an in-memory ollection of key, value
// pairs that maps String objects to SpatialAnchor objects. The Spatial nchorStore is not affected by
// this function unless you provide it as the target collection for import.
//
task<bool> SpatialAnchorImportExportHelper::ImportAnchorDataAsync(
    std::vector<byte>& anchorByteDataIn,
    IMap<String^, SpatialAnchor^>^ anchorMapOut
    )
{
```

<span data-ttu-id="416be-138">Per prima cosa, è necessario creare oggetti flusso per accedere ai dati di ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="416be-138">First, we need to create stream objects to access the anchor data.</span></span> <span data-ttu-id="416be-139">Verranno scritti i dati dal buffer a un buffer di sistema, quindi verrà creato un DataWriter che scrive in un flusso di dati in memoria per raggiungere l'obiettivo di ottenere gli ancoraggi da un buffer di byte nel sistema come SpatialAnchors.</span><span class="sxs-lookup"><span data-stu-id="416be-139">We will be writing the data from our buffer to a system buffer, so we will create a DataWriter that writes to an in-memory data stream in order to accomplish our goal of getting anchors from a byte buffer into the system as SpatialAnchors.</span></span>

```
// Create a random access stream for the anchor data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor data.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
// Create a writer, to put the bytes in the stream.
DataWriter^ writer = ref new DataWriter(outputStream);
```

<span data-ttu-id="416be-140">Ancora una volta, è necessario assicurarsi che l'app disponga dell'autorizzazione per esportare i dati di ancoraggio spaziali, che possono includere informazioni private sull'ambiente dell'utente.</span><span class="sxs-lookup"><span data-stu-id="416be-140">Once again, we need to ensure the app has permission to export spatial anchor data, which could include private information about the user's environment.</span></span>

```
// Request access to transfer spatial anchors.
return create_task(SpatialAnchorTransferManager::RequestAccessAsync()).then(
    [&anchorByteDataIn, writer](SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Access is allowed.
```

<span data-ttu-id="416be-141">Se l'accesso è consentito, è possibile scrivere byte dal buffer in un flusso di dati di sistema.</span><span class="sxs-lookup"><span data-stu-id="416be-141">If access is allowed, we can write bytes from the buffer to a system data stream.</span></span>

```
// Write the bytes to the stream.
        byte* anchorDataFirst = &anchorByteDataIn[0];
        size_t anchorDataSize = anchorByteDataIn.size();
        writer->WriteBytes(Platform::ArrayReference<byte>(anchorDataFirst, anchorDataSize));
        // Store the stream.
        return create_task(writer->StoreAsync());
    }
    else
    {
        // Access is denied.
        return task_from_result<size_t>(0);
    }
```

<span data-ttu-id="416be-142">Se l'archiviazione dei byte nel flusso di dati è riuscita, è possibile provare a importare i dati usando SpatialAnchorTransferManager.</span><span class="sxs-lookup"><span data-stu-id="416be-142">If we were successful in storing bytes in the data stream, we can try to import that data using the SpatialAnchorTransferManager.</span></span>

```
}).then([writer, stream](unsigned int bytesWritten)
{
    if (bytesWritten > 0)
    {
        // Try to import anchors from the byte stream.
        return create_task(writer->FlushAsync())
            .then([stream](bool dataWasFlushed)
        {
            if (dataWasFlushed)
            {
                // Get the input stream for the anchor data.
                IInputStream^ inputStream = stream->GetInputStreamAt(0);
                return create_task(SpatialAnchorTransferManager::TryImportAnchorsAsync(inputStream));
            }
            else
            {
                return task_from_result<IMapView<String^, SpatialAnchor^>^>(nullptr);
            }
        });
    }
    else
    {
        return task_from_result<IMapView<String^, SpatialAnchor^>^>(nullptr);
    }
```

<span data-ttu-id="416be-143">Se i dati possono essere importati, si ottiene una visualizzazione mappa delle coppie chiave-valore che associa stringhe a ancoraggi.</span><span class="sxs-lookup"><span data-stu-id="416be-143">If the data is able to be imported, we get a map view of key-value pairs associating strings with anchors.</span></span> <span data-ttu-id="416be-144">È possibile caricarlo nella raccolta dei dati in memoria e usare tale raccolta per cercare gli ancoraggi che sono interessati a usare.</span><span class="sxs-lookup"><span data-stu-id="416be-144">We can load this into our own in-memory data collection, and use that collection to look for anchors that we are interested in using.</span></span>

```
}).then([anchorMapOut](task<Windows::Foundation::Collections::IMapView<String^, SpatialAnchor^>^>  previousTask)
{
    try
    {
        auto importedAnchorsMap = previousTask.get();
        // If the operation was successful, we get a set of imported anchors.
        if (importedAnchorsMap != nullptr)
        {
            for each (auto& pair in importedAnchorsMap)
            {
                // Note that you could look for specific anchors here, if you know their key values.
                auto const& id = pair->Key;
                auto const& anchor = pair->Value;
                // Append "Remote" to the end of the anchor name for disambiguation.
                std::wstring idRemote(id->Data());
                idRemote += L"Remote";
                String^ idRemoteConst = ref new String (idRemote.c_str());
                // Store the anchor in the current in-memory anchor map.
                anchorMapOut->Insert(idRemoteConst, anchor);
            }
            return true;
        }
    }
    catch (Exception^ exception)
    {
        OutputDebugString(L"Error: Unable to import the anchor data buffer bytes into the in-memory anchor collection.\n");
    }
    return false;
});
}
```

<span data-ttu-id="416be-145">**NOTA:** Solo perché è possibile importare un ancoraggio, non significa necessariamente che sia possibile utilizzarlo immediatamente.</span><span class="sxs-lookup"><span data-stu-id="416be-145">**NOTE:** Just because you can import an anchor, doesn't necessarily mean that you can use it right away.</span></span> <span data-ttu-id="416be-146">L'ancoraggio potrebbe trovarsi in una stanza diversa o in un'altra posizione fisica. l'ancoraggio non verrà locatable fino a quando il dispositivo che lo ha ricevuto dispone di informazioni visive sufficienti sull'ambiente in cui è stato creato l'ancoraggio, per ripristinare la posizione dell'ancoraggio rispetto all'ambiente corrente noto.</span><span class="sxs-lookup"><span data-stu-id="416be-146">The anchor might be in a different room, or another physical location entirely; the anchor won't be locatable until the device that received it has enough visual information about the environment the anchor was created in, to restore the anchor's position relative to the known current environment.</span></span> <span data-ttu-id="416be-147">L'implementazione client dovrebbe provare a individuare l'ancoraggio rispetto al sistema di coordinate locale o al frame di riferimento prima di continuare a usare per il contenuto Live.</span><span class="sxs-lookup"><span data-stu-id="416be-147">The client implementation should try locating the anchor relative to your local coordinate system or reference frame before continuing on to try to use it for live content.</span></span> <span data-ttu-id="416be-148">Ad esempio, provare a individuare periodicamente l'ancoraggio rispetto a un sistema di coordinate corrente fino a quando l'ancoraggio inizia a essere locatable.</span><span class="sxs-lookup"><span data-stu-id="416be-148">For example, try locating the anchor relative to a current coordinate system periodically until the anchor begins to be locatable.</span></span>

## <a name="special-considerations"></a><span data-ttu-id="416be-149">Considerazioni speciali</span><span class="sxs-lookup"><span data-stu-id="416be-149">Special Considerations</span></span>

<span data-ttu-id="416be-150">L'API [TryExportAnchorsAsync](https://msdn.microsoft.com/library/windows/apps/mt592763.aspx) consente l'esportazione di più [SpatialAnchors](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) nello stesso BLOB binario opaco.</span><span class="sxs-lookup"><span data-stu-id="416be-150">The [TryExportAnchorsAsync](https://msdn.microsoft.com/library/windows/apps/mt592763.aspx) API allows multiple [SpatialAnchors](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) to be exported into the same opaque binary blob.</span></span> <span data-ttu-id="416be-151">Tuttavia, esiste una lieve differenza nei dati che verranno inclusi nel BLOB, a seconda che un singolo SpatialAnchor o più SpatialAnchors vengano esportati in una singola chiamata.</span><span class="sxs-lookup"><span data-stu-id="416be-151">However, there is a subtle difference in what data the blob will include, depending on whether a single SpatialAnchor or multiple SpatialAnchors are exported in a single call.</span></span>

### <a name="export-of-a-single-spatialanchor"></a><span data-ttu-id="416be-152">Esportazione di un singolo SpatialAnchor</span><span class="sxs-lookup"><span data-stu-id="416be-152">Export of a single SpatialAnchor</span></span>

<span data-ttu-id="416be-153">Il BLOB contiene una rappresentazione dell'ambiente nella vicinanza del SpatialAnchor, in modo che l'ambiente possa essere riconosciuto nel dispositivo che importa il SpatialAnchor.</span><span class="sxs-lookup"><span data-stu-id="416be-153">The blob contains a representation of the environment in the vicinity of the SpatialAnchor so that the environment can be recognized on the device that imports the SpatialAnchor.</span></span> <span data-ttu-id="416be-154">Al termine dell'importazione, il nuovo SpatialAnchor sarà disponibile per il dispositivo.</span><span class="sxs-lookup"><span data-stu-id="416be-154">After the import completes, the new SpatialAnchor will be available to the device.</span></span> <span data-ttu-id="416be-155">Supponendo che l'utente sia stato recentemente in prossimità dell'ancoraggio, sarà locatable ed è possibile eseguire il rendering degli ologrammi collegati al SpatialAnchor.</span><span class="sxs-lookup"><span data-stu-id="416be-155">Assuming the user has recently been in vicinity of the anchor, it will be locatable and holograms attached to the SpatialAnchor can be rendered.</span></span> <span data-ttu-id="416be-156">Questi ologrammi verranno visualizzati nella stessa posizione fisica del dispositivo originale che ha esportato il SpatialAnchor.</span><span class="sxs-lookup"><span data-stu-id="416be-156">These holograms will show up in the same physical location that they did on the original device which exported the SpatialAnchor.</span></span>

![Esportazione di un singolo SpatialAnchor](images/singleanchor.png)

### <a name="export-of-multiple-spatialanchors"></a><span data-ttu-id="416be-158">Esportazione di più SpatialAnchors</span><span class="sxs-lookup"><span data-stu-id="416be-158">Export of multiple SpatialAnchors</span></span>

<span data-ttu-id="416be-159">Analogamente all'esportazione di un singolo SpatialAnchor, il BLOB contiene una rappresentazione dell'ambiente in prossimità di tutti i SpatialAnchors specificati.</span><span class="sxs-lookup"><span data-stu-id="416be-159">Like the export of a single SpatialAnchor, the blob contains a representation of the environment in the vicinity of all the specified SpatialAnchors.</span></span> <span data-ttu-id="416be-160">Inoltre, il BLOB contiene informazioni sulle connessioni tra il SpatialAnchors incluso, se si trovano nello stesso spazio fisico.</span><span class="sxs-lookup"><span data-stu-id="416be-160">In addition, the blob contains information about the connections between the included SpatialAnchors, if they are located in the same physical space.</span></span> <span data-ttu-id="416be-161">Ciò significa che se vengono importati due SpatialAnchors adiacenti, un ologramma collegato alla *seconda* SpatialAnchor sarà locatable anche se il dispositivo riconosce solo l'ambiente intorno al *primo* SpatialAnchor, perché i dati sono sufficienti per la trasformazione di calcolo tra i due SpatialAnchors è stata inclusa nel BLOB.</span><span class="sxs-lookup"><span data-stu-id="416be-161">This means that if two nearby SpatialAnchors are imported, then a hologram attached to the *second* SpatialAnchor would be locatable even if the device only recognizes the environment around the *first* SpatialAnchor, because enough data to compute transform between the two SpatialAnchors was included in the blob.</span></span> <span data-ttu-id="416be-162">Se i due SpatialAnchors sono stati esportati singolarmente (due chiamate separate a TryExportSpatialAnchors), potrebbero non essere disponibili dati sufficienti nel BLOB per gli ologrammi collegati al secondo SpatialAnchor per essere locatable quando il primo si trova.</span><span class="sxs-lookup"><span data-stu-id="416be-162">If the two SpatialAnchors were exported individually (two separate calls to TryExportSpatialAnchors) then there may not be enough data included in the blob for holograms attached to the second SpatialAnchor to be locatable when the first one is located.</span></span>

![Più ancoraggi esportati con una singola chiamata TryExportAnchorsAsync](images/multipleanchors.png) ![Più ancoraggi esportati con una chiamata TryExportAnchorsAsync separata per ogni ancoraggio](images/separateanchors.png)

## <a name="example-send-anchor-data-using-a-windowsnetworkingstreamsocket"></a><span data-ttu-id="416be-165">Esempio: Inviare dati di ancoraggio usando Windows:: Networking:: StreamSocket</span><span class="sxs-lookup"><span data-stu-id="416be-165">Example: Send anchor data using a Windows::Networking::StreamSocket</span></span>

<span data-ttu-id="416be-166">In questo esempio viene fornito un esempio di come usare i dati di ancoraggio esportati inviando i dati attraverso una rete TCP.</span><span class="sxs-lookup"><span data-stu-id="416be-166">Here, we provide an example of how to use exported anchor data by sending it across a TCP network.</span></span> <span data-ttu-id="416be-167">Si tratta di un HolographicSpatialAnchorTransferSample.</span><span class="sxs-lookup"><span data-stu-id="416be-167">This is from the HolographicSpatialAnchorTransferSample.</span></span>

<span data-ttu-id="416be-168">La classe WinRT StreamSocket usa la libreria di attività PPL.</span><span class="sxs-lookup"><span data-stu-id="416be-168">The WinRT StreamSocket class uses the PPL task library.</span></span> <span data-ttu-id="416be-169">In caso di errori di rete, l'errore viene restituito all'attività successiva nella catena usando un'eccezione generata nuovamente.</span><span class="sxs-lookup"><span data-stu-id="416be-169">In the case of network errors, the error is returned to the next task in the chain using an exception that is re-thrown.</span></span> <span data-ttu-id="416be-170">L'eccezione contiene un valore HRESULT che indica lo stato di errore.</span><span class="sxs-lookup"><span data-stu-id="416be-170">The exception contains an HRESULT indicating the error status.</span></span>

### <a name="use-a-windowsnetworkingstreamsocketlistener-with-tcp-to-send-exported-anchor-data"></a><span data-ttu-id="416be-171">Usare Windows:: Networking:: StreamSocketListener con TCP per inviare dati di ancoraggio esportati</span><span class="sxs-lookup"><span data-stu-id="416be-171">Use a Windows::Networking::StreamSocketListener with TCP to send exported anchor data</span></span>

<span data-ttu-id="416be-172">Creare un'istanza del server che sia in ascolto di una connessione.</span><span class="sxs-lookup"><span data-stu-id="416be-172">Create a server instance that listens for a connection.</span></span>

```
void SampleAnchorTcpServer::ListenForConnection()
{
    // Make a local copy to avoid races with Closed events.
    StreamSocketListener^ streamSocketListener = m_socketServer;
    if (streamSocketListener == nullptr)
    {
        OutputDebugString(L"Server listening for client.\n");
        // Create the web socket connection.
        streamSocketListener = ref new StreamSocketListener();
        streamSocketListener->Control->KeepAlive = true;
        streamSocketListener->BindEndpointAsync(
            SampleAnchorTcpCommon::m_serverHost,
            SampleAnchorTcpCommon::m_tcpPort
            );
        streamSocketListener->ConnectionReceived +=
            ref new Windows::Foundation::TypedEventHandler<StreamSocketListener^, StreamSocketListenerConnectionReceivedEventArgs^>(
                std::bind(&SampleAnchorTcpServer::OnConnectionReceived, this, _1, _2)
                );
        m_socketServer = streamSocketListener;
    }
    else
    {
        OutputDebugString(L"Error: Stream socket listener not created.\n");
    }
}
```

<span data-ttu-id="416be-173">Quando viene ricevuta una connessione, usare la connessione socket client per inviare i dati di ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="416be-173">When a connection is received, use the client socket connection to send anchor data.</span></span>

```
void SampleAnchorTcpServer::OnConnectionReceived(StreamSocketListener^ listener, StreamSocketListenerConnectionReceivedEventArgs^ args)
{
    m_socketForClient = args->Socket;
    if (m_socketForClient != nullptr)
    {
        // In this example, when the client first connects, we catch it up to the current state of our anchor set.
        OutputToClientSocket(m_spatialAnchorHelper->GetAnchorMap());
    }
}
```

<span data-ttu-id="416be-174">A questo punto, è possibile iniziare a inviare un flusso di dati che contiene i dati di ancoraggio esportati.</span><span class="sxs-lookup"><span data-stu-id="416be-174">Now, we can begin to send a data stream that contains the exported anchor data.</span></span>

```
void SampleAnchorTcpServer::OutputToClientSocket(IMap<String^, SpatialAnchor^>^ anchorsToSend)
{
    m_anchorTcpSocketStreamWriter = ref new DataWriter(m_socketForClient->OutputStream);
    OutputDebugString(L"Sending stream to client.\n");
    SendAnchorDataStream(anchorsToSend).then([this](task<bool> previousTask)
    {
        try
        {
            bool success = previousTask.get();
            if (success)
            {
                OutputDebugString(L"Anchor data sent!\n");
            }
            else
            {
                OutputDebugString(L"Error: Anchor data not sent.\n");
            }
        }
        catch (Exception^ exception)
        {
            HandleException(exception);
            OutputDebugString(L"Error: Anchor data was not sent.\n");
        }
    });
}
```

<span data-ttu-id="416be-175">Prima di poter inviare il flusso, è necessario prima inviare un pacchetto di intestazione.</span><span class="sxs-lookup"><span data-stu-id="416be-175">Before we can send the stream itself, we must first send a header packet.</span></span> <span data-ttu-id="416be-176">Questo pacchetto di intestazione deve avere una lunghezza fissa e deve indicare anche la lunghezza della matrice di variabili di byte che rappresenta il flusso di dati di ancoraggio. nel caso di questo esempio non sono disponibili altri dati di intestazione da inviare, quindi l'intestazione ha una lunghezza di 4 byte e contiene un Unsigned Integer a 32 bit.</span><span class="sxs-lookup"><span data-stu-id="416be-176">This header packet must be of fixed length, and it must also indicate the length of the variable array of bytes that is the anchor data stream; in the case of this example we have no other header data to send, so our header is 4 bytes long and contains a 32-bit unsigned integer.</span></span>

```
Concurrency::task<bool> SampleAnchorTcpServer::SendAnchorDataLengthMessage(size_t dataStreamLength)
{
    unsigned int arrayLength = dataStreamLength;
    byte* data = reinterpret_cast<byte*>(&arrayLength);
    m_anchorTcpSocketStreamWriter->WriteBytes(Platform::ArrayReference<byte>(data, SampleAnchorTcpCommon::c_streamHeaderByteArrayLength));
    return create_task(m_anchorTcpSocketStreamWriter->StoreAsync()).then([this](unsigned int bytesStored)
    {
        if (bytesStored > 0)
        {
            OutputDebugString(L"Anchor data length stored in stream; Flushing stream.\n");
            return create_task(m_anchorTcpSocketStreamWriter->FlushAsync());
        }
        else
        {
            OutputDebugString(L"Error: Anchor data length not stored in stream.\n");
            return task_from_result<bool>(false);
        }
    });
}
Concurrency::task<bool> SampleAnchorTcpServer::SendAnchorDataStreamIMap<String^, SpatialAnchor^>^ anchorsToSend)
{
    return SpatialAnchorImportExportHelper::ExportAnchorDataAsync(
        &m_exportedAnchorStoreBytes,
        anchorsToSend
        ).then([this](bool anchorDataExported)
    {
        if (anchorDataExported)
        {
            const size_t arrayLength = m_exportedAnchorStoreBytes.size();
            if (arrayLength > 0)
            {
                OutputDebugString(L"Anchor data was exported; sending data stream length message.\n");
                return SendAnchorDataLengthMessage(arrayLength);
            }
        }
        OutputDebugString(L"Error: Anchor data was not exported.\n");
        // No data to send.
        return task_from_result<bool>(false);
```

<span data-ttu-id="416be-177">Una volta che la lunghezza del flusso, in byte, è stata inviata al client, è possibile continuare a scrivere il flusso di dati nel flusso di socket.</span><span class="sxs-lookup"><span data-stu-id="416be-177">Once the stream length, in bytes, has been sent to the client, we can proceed to write the data stream itself to the socket stream.</span></span> <span data-ttu-id="416be-178">In questo modo i byte dell'archivio di ancoraggio vengono inviati al client.</span><span class="sxs-lookup"><span data-stu-id="416be-178">This will cause the anchor store bytes to get sent to the client.</span></span>

```
}).then([this](bool dataLengthSent)
    {
        if (dataLengthSent)
        {
            OutputDebugString(L"Data stream length message sent; writing exported anchor store bytes to stream.\n");
            m_anchorTcpSocketStreamWriter->WriteBytes(Platform::ArrayReference<byte>(&m_exportedAnchorStoreBytes[0], m_exportedAnchorStoreBytes.size()));
            return create_task(m_anchorTcpSocketStreamWriter->StoreAsync());
        }
        else
        {
            OutputDebugString(L"Error: Data stream length message not sent.\n");
            return task_from_result<size_t>(0);
        }
    }).then([this](unsigned int bytesStored)
    {
        if (bytesStored > 0)
        {
            PrintWstringToDebugConsole(
                std::to_wstring(bytesStored) +
                L" bytes of anchor data written and stored to stream; flushing stream.\n"
                );
        }
        else
        {
            OutputDebugString(L"Error: No anchor data bytes were written to the stream.\n");
        }
        return task_from_result<bool>(false);
    });
}
```

<span data-ttu-id="416be-179">Come indicato in precedenza in questo argomento, è necessario essere pronti a gestire le eccezioni contenenti messaggi di stato di errore di rete.</span><span class="sxs-lookup"><span data-stu-id="416be-179">As noted earlier in this topic, we must be prepared to handle exceptions containing network error status messages.</span></span> <span data-ttu-id="416be-180">Per gli errori non previsti, è possibile scrivere le informazioni sull'eccezione nella console di debug come segue.</span><span class="sxs-lookup"><span data-stu-id="416be-180">For errors that are not expected, we can write the exception info to the debug console like so.</span></span> <span data-ttu-id="416be-181">Ciò consentirà di ottenere informazioni sugli eventi che si sono verificati se l'esempio di codice non è in grado di completare la connessione o se non è in grado di completare l'invio di dati di ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="416be-181">This will give us a clue as to what happened if our code sample is unable to complete the connection, or if it is unable to finish sending the anchor data.</span></span>

```
void SampleAnchorTcpServer::HandleException(Exception^ exception)
{
    PrintWstringToDebugConsole(
        std::wstring(L"Connection error: ") +
        exception->ToString()->Data() +
        L"\n"
        );
}
```

### <a name="use-a-windowsnetworkingstreamsocket-with-tcp-to-receive-exported-anchor-data"></a><span data-ttu-id="416be-182">Usare Windows:: Networking:: StreamSocket con TCP per ricevere i dati di ancoraggio esportati</span><span class="sxs-lookup"><span data-stu-id="416be-182">Use a Windows::Networking::StreamSocket with TCP to receive exported anchor data</span></span>

<span data-ttu-id="416be-183">Prima di tutto, è necessario connettersi al server.</span><span class="sxs-lookup"><span data-stu-id="416be-183">First, we have to connect to the server.</span></span> <span data-ttu-id="416be-184">In questo esempio di codice viene illustrato come creare e configurare un StreamSocket e creare un DataReader che è possibile utilizzare per acquisire i dati di rete tramite la connessione socket.</span><span class="sxs-lookup"><span data-stu-id="416be-184">This code sample shows how to create and configure a StreamSocket, and create a DataReader that you can use to acquire network data using the socket connection.</span></span>

<span data-ttu-id="416be-185">**NOTA:** Se si esegue questo codice di esempio, assicurarsi di configurare e avviare il server prima di avviare il client.</span><span class="sxs-lookup"><span data-stu-id="416be-185">**NOTE:** If you run this sample code, ensure that you configure and launch the server before starting the client.</span></span>

```
task<bool> SampleAnchorTcpClient::ConnectToServer()
{
    // Make a local copy to avoid races with Closed events.
    StreamSocket^ streamSocket = m_socketClient;
    // Have we connected yet?
    if (m_socketClient == nullptr)
    {
        OutputDebugString(L"Client is attempting to connect to server.\n");
        EndpointPair^ endpointPair = ref new EndpointPair(
            SampleAnchorTcpCommon::m_clientHost,
            SampleAnchorTcpCommon::m_tcpPort,
            SampleAnchorTcpCommon::m_serverHost,
            SampleAnchorTcpCommon::m_tcpPort
            );
        // Create the web socket connection.
        m_socketClient = ref new StreamSocket();
        // The client connects to the server.
        return create_task(m_socketClient->ConnectAsync(endpointPair, SocketProtectionLevel::PlainSocket)).then([this](task<void> previousTask)
        {
            try
            {
                // Try getting all exceptions from the continuation chain above this point.
                previousTask.get();
                m_anchorTcpSocketStreamReader = ref new DataReader(m_socketClient->InputStream);
                OutputDebugString(L"Client connected!\n");
                m_anchorTcpSocketStreamReader->InputStreamOptions = InputStreamOptions::ReadAhead;
                WaitForAnchorDataStream();
                return true;
            }
            catch (Exception^ exception)
            {
                if (exception->HResult == 0x80072741)
                {
                    // This code sample includes a very simple implementation of client/server
                    // endpoint detection: if the current instance tries to connect to itself,
                    // it is determined to be the server.
                    OutputDebugString(L"Starting up the server instance.\n");
                    // When we return false, we'll start up the server instead.
                    return false;
                }
                else if ((exception->HResult == 0x8007274c) || // connection timed out
                    (exception->HResult == 0x80072740)) // connection maxed at server end
                {
                    // If the connection timed out, try again.
                    ConnectToServer();
                }
                else if (exception->HResult == 0x80072741)
                {
                    // No connection is possible.
                }
                HandleException(exception);
                return true;
            }
        });
    }
    else
    {
        OutputDebugString(L"A StreamSocket connection to a server already exists.\n");
        return task_from_result<bool>(true);
    }
}
```

<span data-ttu-id="416be-186">Quando si dispone di una connessione, è possibile attendere che il server invii i dati.</span><span class="sxs-lookup"><span data-stu-id="416be-186">Once we have a connection, we can wait for the server to send data.</span></span> <span data-ttu-id="416be-187">Questa operazione viene eseguita chiamando LoadAsync sul lettore dati del flusso.</span><span class="sxs-lookup"><span data-stu-id="416be-187">We do this by calling LoadAsync on the stream data reader.</span></span>

<span data-ttu-id="416be-188">Il primo set di byte ricevuto deve essere sempre il pacchetto di intestazione, che indica la lunghezza in byte del flusso di dati di ancoraggio, come descritto nella sezione precedente.</span><span class="sxs-lookup"><span data-stu-id="416be-188">The first set of bytes we receive should always be the header packet, which indicates the anchor data stream byte length as described in the previous section.</span></span>

```
void SampleAnchorTcpClient::WaitForAnchorDataStream()
{
    if (m_anchorTcpSocketStreamReader == nullptr)
    {
        // We have not connected yet.
        return;
    }
    OutputDebugString(L"Waiting for server message.\n");
    // Wait for the first message, which specifies the byte length of the string data.
    create_task(m_anchorTcpSocketStreamReader->LoadAsync(SampleAnchorTcpCommon::c_streamHeaderByteArrayLength)).then([this](unsigned int numberOfBytes)
    {
        if (numberOfBytes > 0)
        {
            OutputDebugString(L"Server message incoming.\n");
            return ReceiveAnchorDataLengthMessage();
        }
        else
        {
            OutputDebugString(L"0-byte async task received, awaiting server message again.\n");
            WaitForAnchorDataStream();
            return task_from_result<size_t>(0);
        }
```

<span data-ttu-id="416be-189">...</span><span class="sxs-lookup"><span data-stu-id="416be-189">...</span></span>

```
task<size_t> SampleAnchorTcpClient::ReceiveAnchorDataLengthMessage()
{
    byte data[4];
    m_anchorTcpSocketStreamReader->ReadBytes(Platform::ArrayReference<byte>(data, SampleAnchorTcpCommon::c_streamHeaderByteArrayLength));
    unsigned int lengthMessageSize = *reinterpret_cast<unsigned int*>(data);
    if (lengthMessageSize > 0)
    {
        OutputDebugString(L"One or more anchors to be received.\n");
        return task_from_result<size_t>(lengthMessageSize);
    }
    else
    {
        OutputDebugString(L"No anchors to be received.\n");
        ConnectToServer();
    }
    return task_from_result<size_t>(0);
}
```

<span data-ttu-id="416be-190">Dopo aver ricevuto il pacchetto di intestazione, è noto il numero di byte di dati di ancoraggio che ci si aspetta.</span><span class="sxs-lookup"><span data-stu-id="416be-190">After we have received the header packet, we know how many bytes of anchor data we should expect.</span></span> <span data-ttu-id="416be-191">È possibile procedere con la lettura di tali byte dal flusso.</span><span class="sxs-lookup"><span data-stu-id="416be-191">We can proceed to read those bytes from the stream.</span></span>

```
}).then([this](size_t dataStreamLength)
    {
        if (dataStreamLength > 0)
        {
            std::wstring debugMessage = std::to_wstring(dataStreamLength);
            debugMessage += L" bytes of anchor data incoming.\n";
            OutputDebugString(debugMessage.c_str());
            // Prepare to receive the data stream in one or more pieces.
            m_anchorStreamLength = dataStreamLength;
            m_exportedAnchorStoreBytes.clear();
            m_exportedAnchorStoreBytes.resize(m_anchorStreamLength);
            OutputDebugString(L"Loading byte stream.\n");
            return ReceiveAnchorDataStream();
        }
        else
        {
            OutputDebugString(L"Error: Anchor data size not received.\n");
            ConnectToServer();
            return task_from_result<bool>(false);
        }
    });
}
```

<span data-ttu-id="416be-192">Ecco il nostro codice per la ricezione del flusso di dati di ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="416be-192">Here's our code for receiving the anchor data stream.</span></span> <span data-ttu-id="416be-193">Prima di tutto, i byte vengono caricati dal flusso. il completamento di questa operazione può richiedere del tempo perché il StreamSocket attende la ricezione della quantità di byte dalla rete.</span><span class="sxs-lookup"><span data-stu-id="416be-193">Again, we will first load the bytes from the stream; this operation may take some time to complete as the StreamSocket waits to receive that amount of bytes from the network.</span></span>

<span data-ttu-id="416be-194">Al termine dell'operazione di caricamento, è possibile leggere il numero di byte.</span><span class="sxs-lookup"><span data-stu-id="416be-194">When the loading operation is complete, we can read that number of bytes.</span></span> <span data-ttu-id="416be-195">Se è stato ricevuto il numero di byte previsto per il flusso di dati di ancoraggio, è possibile procedere e importare i dati di ancoraggio. in caso contrario, è necessario che si sia verificato un errore.</span><span class="sxs-lookup"><span data-stu-id="416be-195">If we received the number of bytes that we expect for the anchor data stream, we can go ahead and import the anchor data; if not, there must have been some sort of error.</span></span> <span data-ttu-id="416be-196">Questo problema può verificarsi, ad esempio, quando l'istanza del server termina prima che sia possibile completare l'invio del flusso di dati oppure la rete si arresta prima che il client possa ricevere l'intero flusso di dati.</span><span class="sxs-lookup"><span data-stu-id="416be-196">For example, this can happen when the server instance terminates before it can finish sending the data stream, or the network goes down before the entire data stream can be received by the client.</span></span>

```
task<bool> SampleAnchorTcpClient::ReceiveAnchorDataStream()
{
    if (m_anchorStreamLength > 0)
    {
        // First, we load the bytes from the network socket.
        return create_task(m_anchorTcpSocketStreamReader->LoadAsync(m_anchorStreamLength)).then([this](size_t bytesLoadedByStreamReader)
        {
            if (bytesLoadedByStreamReader > 0)
            {
                // Once the bytes are loaded, we can read them from the stream.
                m_anchorTcpSocketStreamReader->ReadBytes(Platform::ArrayReference<byte>(&m_exportedAnchorStoreBytes[0],
                    bytesLoadedByStreamReader));
                // Check status.
                if (bytesLoadedByStreamReader == m_anchorStreamLength)
                {
                    // The whole stream has arrived. We can process the data.
                    // Informational message of progress complete.
                    std::wstring infoMessage = std::to_wstring(bytesLoadedByStreamReader);
                    infoMessage += L" bytes read out of ";
                    infoMessage += std::to_wstring(m_anchorStreamLength);
                    infoMessage += L" total bytes; importing the data.\n";
                    OutputDebugStringW(infoMessage.c_str());
                    // Kick off a thread to wait for a new message indicating another incoming anchor data stream.
                    WaitForAnchorDataStream();
                    // Process the data for the stream we just received.
                    return SpatialAnchorImportExportHelper::ImportAnchorDataAsync(m_exportedAnchorStoreBytes, m_spatialAnchorHelper->GetAnchorMap());
                }
                else
                {
                    OutputDebugString(L"Error: Fewer than expected anchor data bytes were received.\n");
                }
            }
            else
            {
                OutputDebugString(L"Error: No anchor bytes were received.\n");
            }
            return task_from_result<bool>(false);
        });
    }
    else
    {
        OutputDebugString(L"Warning: A zero-length data buffer was sent.\n");
        return task_from_result<bool>(false);
    }
}
```

<span data-ttu-id="416be-197">Anche in questo caso, è necessario essere pronti a gestire gli errori di rete sconosciuti.</span><span class="sxs-lookup"><span data-stu-id="416be-197">Again, we must be prepared to handle unknown network errors.</span></span>

```
void SampleAnchorTcpClient::HandleException(Exception^ exception)
{
    std::wstring error = L"Connection error: ";
    error += exception->ToString()->Data();
    error += L"\n";
    OutputDebugString(error.c_str());
}
```

<span data-ttu-id="416be-198">La procedura è terminata.</span><span class="sxs-lookup"><span data-stu-id="416be-198">That's it!</span></span> <span data-ttu-id="416be-199">A questo punto, è necessario disporre di informazioni sufficienti per provare a individuare gli ancoraggi ricevuti sulla rete.</span><span class="sxs-lookup"><span data-stu-id="416be-199">Now, you should have enough information to try locating the anchors received over the network.</span></span> <span data-ttu-id="416be-200">Anche in questo caso, si noti che il client deve disporre di un numero sufficiente di dati di rilevamento visivi per lo spazio per individuare correttamente l'ancoraggio. Se non funziona immediatamente, provare a spostarsi per un po'.</span><span class="sxs-lookup"><span data-stu-id="416be-200">Again, note that the client must have enough visual tracking data for the space to successfully locate the anchor; if it doesn't work right away, try walking around for a while.</span></span> <span data-ttu-id="416be-201">Se ancora non funziona, fare in modo che il server invii più ancoraggi e usare le comunicazioni di rete per concordare su uno che funzioni per il client.</span><span class="sxs-lookup"><span data-stu-id="416be-201">If it still doesn't work, have the server send more anchors, and use network communications to agree on one that works for the client.</span></span> <span data-ttu-id="416be-202">È possibile provare a eseguire questa operazione scaricando HolographicSpatialAnchorTransferSample, configurando gli indirizzi IP del client e del server e distribuendo il server a dispositivi HoloLens client e server.</span><span class="sxs-lookup"><span data-stu-id="416be-202">You can try this out by downloading the HolographicSpatialAnchorTransferSample, configuring your client and server IPs, and deploying it to client and server HoloLens devices.</span></span>

## <a name="see-also"></a><span data-ttu-id="416be-203">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="416be-203">See also</span></span>
* [<span data-ttu-id="416be-204">PPL (Parallel Patterns Library)</span><span class="sxs-lookup"><span data-stu-id="416be-204">Parallel Patterns Library (PPL)</span></span>](https://msdn.microsoft.com/library/dd492418.aspx)
* [<span data-ttu-id="416be-205">Windows. Networking. StreamSocket</span><span class="sxs-lookup"><span data-stu-id="416be-205">Windows.Networking.StreamSocket</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocket.aspx)
* [<span data-ttu-id="416be-206">Windows. Networking. StreamSocketListener</span><span class="sxs-lookup"><span data-stu-id="416be-206">Windows.Networking.StreamSocketListener</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocketlistener.aspx)

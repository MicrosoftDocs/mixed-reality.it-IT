---
title: Trasferimenti di ancoraggio locale in DirectX
description: Viene illustrato come sincronizzare i dispositivi HoloLens due trasferendo gli ancoraggi spaziali.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, sincronizzare, ancoraggio spaziale, il trasferimento, multiplayer, visualizzare, scenario, procedura dettagliata, codice di esempio, transfer, trasferimento locale di ancoraggio, esportazione di ancoraggio, importazione di ancoraggio
ms.openlocfilehash: 5d03f4bfa764b9948ec4718bce86127cfcc3e303
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605069"
---
# <a name="local-anchor-transfers-in-directx"></a><span data-ttu-id="354d6-104">Trasferimenti di ancoraggio locale in DirectX</span><span class="sxs-lookup"><span data-stu-id="354d6-104">Local anchor transfers in DirectX</span></span>

<span data-ttu-id="354d6-105">In situazioni in cui non è possibile usare <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Anchor spaziali Azure</a>, trasferimenti di ancoraggio locale abilitare un dispositivo HoloLens esportare un ancoraggio per essere importati da un secondo dispositivo HoloLens.</span><span class="sxs-lookup"><span data-stu-id="354d6-105">In situations where you cannot use <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, local anchor transfers enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>

>[!NOTE]
><span data-ttu-id="354d6-106">I trasferimenti di ancoraggio locale forniscono richiamo ancoraggio meno affidabile rispetto <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Anchor spaziali Azure</a>, e dispositivi iOS e Android non sono supportati da questo approccio.</span><span class="sxs-lookup"><span data-stu-id="354d6-106">Local anchor transfers provide less robust anchor recall than <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, and iOS and Android devices are not supported by this approach.</span></span>

>[!NOTE]
><span data-ttu-id="354d6-107">I frammenti di codice in questo articolo illustrano attualmente l'utilizzo di C++/CX invece di C + + 17 conformi C++/WinRT usato nel [ C++ modello di progetto holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="354d6-107">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="354d6-108">I concetti sono equivalenti per un C++progetto /WinRT, anche se è necessario convertire il codice.</span><span class="sxs-lookup"><span data-stu-id="354d6-108">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="transferring-spatial-anchors"></a><span data-ttu-id="354d6-109">Trasferire gli ancoraggi spaziali</span><span class="sxs-lookup"><span data-stu-id="354d6-109">Transferring spatial anchors</span></span>

<span data-ttu-id="354d6-110">È possibile trasferire gli ancoraggi spaziali tra i dispositivi di realtà mista di Windows usando il [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx).</span><span class="sxs-lookup"><span data-stu-id="354d6-110">You can transfer spatial anchors between Windows Mixed Reality devices by using the [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx).</span></span> <span data-ttu-id="354d6-111">Questa API consente di raggruppare un ancoraggio con tutti i dati del sensore supporto necessari per trovare la posizione esatta nel mondo e quindi importare tale pacchetto in un altro dispositivo.</span><span class="sxs-lookup"><span data-stu-id="354d6-111">This API lets you bundle up an anchor with all the supporting sensor data needed to find that exact place in the world, and then import that bundle on another device.</span></span> <span data-ttu-id="354d6-112">Una volta l'app nel dispositivo secondo ha importato l'ancoraggio, ogni app è possibile eseguire il rendering di vntana usando che condivisi sistema di coordinate dell'ancoraggio spaziale, che verranno quindi visualizzati nella stessa posizione nel mondo reale.</span><span class="sxs-lookup"><span data-stu-id="354d6-112">Once the app on the second device has imported that anchor, each app can render holograms using that shared spatial anchor's coordinate system, which will then appear in the same place in the real world.</span></span>

<span data-ttu-id="354d6-113">Si noti che gli ancoraggi spaziali non sono in grado di trasferire tra i diversi tipi di dispositivi, ad esempio un punto di ancoraggio HoloLens spaziale potrebbe non essere individuabili tramite un visore VR immersivi.</span><span class="sxs-lookup"><span data-stu-id="354d6-113">Note that spatial anchors are not able to transfer between different device types, for example a HoloLens spatial anchor may not be locatable using an immersive headset.</span></span>  <span data-ttu-id="354d6-114">Gli ancoraggi trasferiti non sono compatibili con dispositivi iOS o Android.</span><span class="sxs-lookup"><span data-stu-id="354d6-114">Transferred anchors are also not compatible with iOS or Android devices.</span></span>

## <a name="set-up-your-app-to-use-the-spatialperception-capability"></a><span data-ttu-id="354d6-115">Configurare l'app per usare la funzionalità spatialPerception</span><span class="sxs-lookup"><span data-stu-id="354d6-115">Set up your app to use the spatialPerception capability</span></span>

<span data-ttu-id="354d6-116">L'app deve disporre dell'autorizzazione per usare la funzionalità spatialPerception prima che possa usare la [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx).</span><span class="sxs-lookup"><span data-stu-id="354d6-116">Your app must be granted permission to use the spatialPerception capability before it can use the [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx).</span></span> <span data-ttu-id="354d6-117">Ciò è necessario perché il trasferimento di un punto di ancoraggio spaziale prevede la condivisione di immagini di sensori raccolte nel tempo in prossimità di tale punto di ancoraggio, che può contenere informazioni sensibili.</span><span class="sxs-lookup"><span data-stu-id="354d6-117">This is necessary because transferring a spatial anchor involves sharing sensor images gathered over time in vicinity of that anchor, which might include sensitive information.</span></span>

<span data-ttu-id="354d6-118">Dichiarare questa funzionalità nel file package. appxmanifest per l'app.</span><span class="sxs-lookup"><span data-stu-id="354d6-118">Declare this capability in the package.appxmanifest file for your app.</span></span> <span data-ttu-id="354d6-119">Di seguito è riportato un esempio:</span><span class="sxs-lookup"><span data-stu-id="354d6-119">Here's an example:</span></span>

```
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

<span data-ttu-id="354d6-120">La funzionalità proviene il **uap2** dello spazio dei nomi.</span><span class="sxs-lookup"><span data-stu-id="354d6-120">The capability comes from the **uap2** namespace.</span></span> <span data-ttu-id="354d6-121">Per poter accedere a questo spazio dei nomi nel manifesto, includerlo come un *xlmns* attributo il &lt;pacchetto > elemento.</span><span class="sxs-lookup"><span data-stu-id="354d6-121">To get access to this namespace in your manifest, include it as an *xlmns* attribute in the &lt;Package> element.</span></span> <span data-ttu-id="354d6-122">Di seguito è riportato un esempio:</span><span class="sxs-lookup"><span data-stu-id="354d6-122">Here's an example:</span></span>

```
<Package
    xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap mp"
    >
```

<span data-ttu-id="354d6-123">**NOTA:** L'app dovrà richiedere la funzionalità in fase di esecuzione prima di poter accedere SpatialAnchor le API di importazione/esportazione.</span><span class="sxs-lookup"><span data-stu-id="354d6-123">**NOTE:** Your app will need to request the capability at runtime before it can access SpatialAnchor export/import APIs.</span></span> <span data-ttu-id="354d6-124">Visualizzare [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync.aspx) negli esempi seguenti.</span><span class="sxs-lookup"><span data-stu-id="354d6-124">See [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync.aspx) in the examples below.</span></span>

## <a name="serialize-anchor-data-by-exporting-it-with-the-spatialanchortransfermanager"></a><span data-ttu-id="354d6-125">Serializzare i dati di ancoraggio tramite l'esportazione con il SpatialAnchorTransferManager</span><span class="sxs-lookup"><span data-stu-id="354d6-125">Serialize anchor data by exporting it with the SpatialAnchorTransferManager</span></span>

<span data-ttu-id="354d6-126">Una funzione di supporto è incluso nell'esempio di codice da esportare (serializzazione) [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) dati.</span><span class="sxs-lookup"><span data-stu-id="354d6-126">A helper function is included in the code sample to export (serialize) [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) data.</span></span> <span data-ttu-id="354d6-127">Questa API esportazione serializza tutti i punti di ancoraggio in una raccolta di coppie chiave-valore, associare gli ancoraggi stringhe.</span><span class="sxs-lookup"><span data-stu-id="354d6-127">This export API serializes all anchors in a collection of key-value pairs associating strings with anchors.</span></span>

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

<span data-ttu-id="354d6-128">In primo luogo, è necessario configurare il flusso di dati.</span><span class="sxs-lookup"><span data-stu-id="354d6-128">First, we need to set up the data stream.</span></span> <span data-ttu-id="354d6-129">Ciò permetterà a 1.) usare TryExportAnchorsAsync per inserire i dati in un buffer di proprietà dell'app e 2). leggere dati dal flusso, che è un flusso di dati WinRT - buffer byte esportato in un buffer di memoria, ovvero un std:: Vector&lt;byte >.</span><span class="sxs-lookup"><span data-stu-id="354d6-129">This will allow us to 1.) use TryExportAnchorsAsync to put the data in a buffer owned by the app, and 2.) read data from the exported byte buffer stream - which is a WinRT data stream - into our own memory buffer, which is a std::vector&lt;byte>.</span></span>

```
// Create a random access stream to process the anchor byte data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor byte stream.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
```

<span data-ttu-id="354d6-130">È necessario chiedere l'autorizzazione per accedere ai dati spaziali, inclusi gli ancoraggi esportati dal sistema.</span><span class="sxs-lookup"><span data-stu-id="354d6-130">We need to ask permission to access spatial data, including anchors that are exported by the system.</span></span>

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

<span data-ttu-id="354d6-131">Se viene visualizzata l'autorizzazione e vengono esportati gli ancoraggi, è possibile leggere il flusso di dati.</span><span class="sxs-lookup"><span data-stu-id="354d6-131">If we do get permission and anchors are exported, we can read the data stream.</span></span> <span data-ttu-id="354d6-132">In questo caso, viene anche illustrato come creare il DataReader e InputStream si userà per leggere i dati.</span><span class="sxs-lookup"><span data-stu-id="354d6-132">Here, we also show how to create the DataReader and InputStream we will use to read the data.</span></span>

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

<span data-ttu-id="354d6-133">Dopo la lettura dal flusso di byte, è possibile salvarli in un buffer di dati come illustrato di seguito.</span><span class="sxs-lookup"><span data-stu-id="354d6-133">After we read bytes from the stream, we can save them to our own data buffer like so.</span></span>

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

## <a name="deserialize-anchor-data-by-importing-it-into-the-system-using-the-spatialanchortransfermanager"></a><span data-ttu-id="354d6-134">Deserializzare i dati di ancoraggio importandolo nel sistema tramite il SpatialAnchorTransferManager</span><span class="sxs-lookup"><span data-stu-id="354d6-134">Deserialize anchor data by importing it into the system using the SpatialAnchorTransferManager</span></span>

<span data-ttu-id="354d6-135">Una funzione di supporto è incluso nell'esempio di codice per caricare i dati esportati in precedenza.</span><span class="sxs-lookup"><span data-stu-id="354d6-135">A helper function is included in the code sample to load previously exported data.</span></span> <span data-ttu-id="354d6-136">Questa funzione di deserializzazione fornisce una raccolta di coppie chiave-valore, simile a ciò che fornisce il SpatialAnchorStore - ad eccezione del fatto che abbiamo i dati da un'altra origine, ad esempio un socket di rete.</span><span class="sxs-lookup"><span data-stu-id="354d6-136">This deserialization function provides a collection of key-value pairs, similar to what the SpatialAnchorStore provides - except that we got this data from another source, such as a network socket.</span></span> <span data-ttu-id="354d6-137">È possibile elaborare e prendere in considerazione i dati prima dell'archiviazione offline, l'uso della memoria, in-app oppure (se applicabile) SpatialAnchorStore dell'app.</span><span class="sxs-lookup"><span data-stu-id="354d6-137">You can process and reason about this data before storing it offline, using in-app memory, or (if applicable) your app's SpatialAnchorStore.</span></span>

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

<span data-ttu-id="354d6-138">In primo luogo, dobbiamo creare gli oggetti di flusso per accedere ai dati di ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="354d6-138">First, we need to create stream objects to access the anchor data.</span></span> <span data-ttu-id="354d6-139">Si scriverà i dati dal nostro buffer in un buffer del sistema, in modo che si creerà un DataWriter che scrive in un flusso di dati in memoria per poter raggiungere l'obiettivo prefissato di entrare nel sistema come SpatialAnchors Anchor da un buffer di byte.</span><span class="sxs-lookup"><span data-stu-id="354d6-139">We will be writing the data from our buffer to a system buffer, so we will create a DataWriter that writes to an in-memory data stream in order to accomplish our goal of getting anchors from a byte buffer into the system as SpatialAnchors.</span></span>

```
// Create a random access stream for the anchor data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor data.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
// Create a writer, to put the bytes in the stream.
DataWriter^ writer = ref new DataWriter(outputStream);
```

<span data-ttu-id="354d6-140">Ancora una volta, è necessario assicurarsi che l'app disponga dell'autorizzazione per esportare i dati spaziali di ancoraggio, che potrebbe includere informazioni riservate sull'ambiente dell'utente.</span><span class="sxs-lookup"><span data-stu-id="354d6-140">Once again, we need to ensure the app has permission to export spatial anchor data, which could include private information about the user's environment.</span></span>

```
// Request access to transfer spatial anchors.
return create_task(SpatialAnchorTransferManager::RequestAccessAsync()).then(
    [&anchorByteDataIn, writer](SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Access is allowed.
```

<span data-ttu-id="354d6-141">Se è consentito l'accesso, è possibile scrivere i byte dal buffer in un flusso di dati di sistema.</span><span class="sxs-lookup"><span data-stu-id="354d6-141">If access is allowed, we can write bytes from the buffer to a system data stream.</span></span>

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

<span data-ttu-id="354d6-142">Se si hanno avuto esito positivo nell'archiviazione dei byte nel flusso di dati, è possibile provare a importare i dati usando il SpatialAnchorTransferManager.</span><span class="sxs-lookup"><span data-stu-id="354d6-142">If we were successful in storing bytes in the data stream, we can try to import that data using the SpatialAnchorTransferManager.</span></span>

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

<span data-ttu-id="354d6-143">Sono possibile importare i dati, si ottiene una visualizzazione mappa di coppie chiave-valore associando le stringhe con punti di ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="354d6-143">If the data is able to be imported, we get a map view of key-value pairs associating strings with anchors.</span></span> <span data-ttu-id="354d6-144">È possibile caricarlo in un insieme di dati in memoria e utilizzare tale raccolta per individuare i punti di ancoraggio che siamo interessati all'uso.</span><span class="sxs-lookup"><span data-stu-id="354d6-144">We can load this into our own in-memory data collection, and use that collection to look for anchors that we are interested in using.</span></span>

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

<span data-ttu-id="354d6-145">**NOTA:** Solo perché è possibile importare un ancoraggio, non significa necessariamente che è possibile utilizzare sin da subito.</span><span class="sxs-lookup"><span data-stu-id="354d6-145">**NOTE:** Just because you can import an anchor, doesn't necessarily mean that you can use it right away.</span></span> <span data-ttu-id="354d6-146">L'ancoraggio potrebbe trovarsi in una stanza diversa o un'altra posizione fisica interamente; il punto di ancoraggio non saranno individuabile fino a quando il dispositivo che lo ha ricevuto ha informazioni sufficienti visual per valutare l'ambiente che è stato creato il punto di ancoraggio, per ripristinare la posizione dell'ancoraggio rispetto all'ambiente corrente noto.</span><span class="sxs-lookup"><span data-stu-id="354d6-146">The anchor might be in a different room, or another physical location entirely; the anchor won't be locatable until the device that received it has enough visual information about the environment the anchor was created in, to restore the anchor's position relative to the known current environment.</span></span> <span data-ttu-id="354d6-147">L'implementazione client deve provare a individuare il punto di ancoraggio rispetto al sistema di coordinate locale o un frame di riferimento prima di proseguire provare a usarlo per il contenuto in tempo reale.</span><span class="sxs-lookup"><span data-stu-id="354d6-147">The client implementation should try locating the anchor relative to your local coordinate system or reference frame before continuing on to try to use it for live content.</span></span> <span data-ttu-id="354d6-148">Ad esempio, provare a individuare il punto di ancoraggio rispetto al sistema di coordinate corrente periodicamente fino a quando il punto di ancoraggio inizia a essere individuabili.</span><span class="sxs-lookup"><span data-stu-id="354d6-148">For example, try locating the anchor relative to a current coordinate system periodically until the anchor begins to be locatable.</span></span>

## <a name="special-considerations"></a><span data-ttu-id="354d6-149">Considerazioni speciali</span><span class="sxs-lookup"><span data-stu-id="354d6-149">Special Considerations</span></span>

<span data-ttu-id="354d6-150">Il [TryExportAnchorsAsync](https://msdn.microsoft.com/library/windows/apps/mt592763.aspx) API consente selezioni multiple [SpatialAnchors](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) possono essere esportate nello stesso blob binari opachi.</span><span class="sxs-lookup"><span data-stu-id="354d6-150">The [TryExportAnchorsAsync](https://msdn.microsoft.com/library/windows/apps/mt592763.aspx) API allows multiple [SpatialAnchors](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) to be exported into the same opaque binary blob.</span></span> <span data-ttu-id="354d6-151">Tuttavia, vi è una sottile differenza nei quali dati include il blob, a seconda del fatto che un singolo SpatialAnchor o SpatialAnchors più vengono esportati in una singola chiamata.</span><span class="sxs-lookup"><span data-stu-id="354d6-151">However, there is a subtle difference in what data the blob will include, depending on whether a single SpatialAnchor or multiple SpatialAnchors are exported in a single call.</span></span>

### <a name="export-of-a-single-spatialanchor"></a><span data-ttu-id="354d6-152">Esportazione di un singolo SpatialAnchor</span><span class="sxs-lookup"><span data-stu-id="354d6-152">Export of a single SpatialAnchor</span></span>

<span data-ttu-id="354d6-153">Il blob contiene una rappresentazione dell'ambiente in prossimità di SpatialAnchor in modo che l'ambiente può essere riconosciuto nel dispositivo, che importa il SpatialAnchor.</span><span class="sxs-lookup"><span data-stu-id="354d6-153">The blob contains a representation of the environment in the vicinity of the SpatialAnchor so that the environment can be recognized on the device that imports the SpatialAnchor.</span></span> <span data-ttu-id="354d6-154">Al termine dell'importazione, il nuovo SpatialAnchor saranno disponibili per il dispositivo.</span><span class="sxs-lookup"><span data-stu-id="354d6-154">After the import completes, the new SpatialAnchor will be available to the device.</span></span> <span data-ttu-id="354d6-155">Supponendo che l'utente è stato recentemente in prossimità dell'ancoraggio, renderlo individuabile e vntana collegati al SpatialAnchor possibile eseguire il rendering.</span><span class="sxs-lookup"><span data-stu-id="354d6-155">Assuming the user has recently been in vicinity of the anchor, it will be locatable and holograms attached to the SpatialAnchor can be rendered.</span></span> <span data-ttu-id="354d6-156">Questi vntana appariranno nella stessa posizione fisica che supportavano nel dispositivo originale che esportato il SpatialAnchor.</span><span class="sxs-lookup"><span data-stu-id="354d6-156">These holograms will show up in the same physical location that they did on the original device which exported the SpatialAnchor.</span></span>

![Esportazione di un singolo SpatialAnchor](images/singleanchor.png)

### <a name="export-of-multiple-spatialanchors"></a><span data-ttu-id="354d6-158">Esportazione di più SpatialAnchors</span><span class="sxs-lookup"><span data-stu-id="354d6-158">Export of multiple SpatialAnchors</span></span>

<span data-ttu-id="354d6-159">Ad esempio l'esportazione di un singolo SpatialAnchor, il blob contiene una rappresentazione dell'ambiente in prossimità di tutti i SpatialAnchors specificato.</span><span class="sxs-lookup"><span data-stu-id="354d6-159">Like the export of a single SpatialAnchor, the blob contains a representation of the environment in the vicinity of all the specified SpatialAnchors.</span></span> <span data-ttu-id="354d6-160">Inoltre, il blob contiene informazioni sulle connessioni tra SpatialAnchors incluso, se si trovano nello stesso spazio fisico.</span><span class="sxs-lookup"><span data-stu-id="354d6-160">In addition, the blob contains information about the connections between the included SpatialAnchors, if they are located in the same physical space.</span></span> <span data-ttu-id="354d6-161">Ciò significa che se si importano due SpatialAnchors nelle vicinanze, quindi ologramma collegato per il *secondo* SpatialAnchor sarebbe individuabili anche se il dispositivo riconosce solo l'ambiente che circonda il *prima* SpatialAnchor, perché i dati sufficienti per calcolare la trasformazione tra i due SpatialAnchors è stata inclusa nel blob.</span><span class="sxs-lookup"><span data-stu-id="354d6-161">This means that if two nearby SpatialAnchors are imported, then a hologram attached to the *second* SpatialAnchor would be locatable even if the device only recognizes the environment around the *first* SpatialAnchor, because enough data to compute transform between the two SpatialAnchors was included in the blob.</span></span> <span data-ttu-id="354d6-162">Se i due SpatialAnchors sono state esportate singolarmente (due chiamate separate al TryExportSpatialAnchors), si potrebbe non essere sufficiente dati inclusi nell'oggetto blob per vntana collegati per la seconda SpatialAnchor essere individuabili quando il primo elemento si trova.</span><span class="sxs-lookup"><span data-stu-id="354d6-162">If the two SpatialAnchors were exported individually (two separate calls to TryExportSpatialAnchors) then there may not be enough data included in the blob for holograms attached to the second SpatialAnchor to be locatable when the first one is located.</span></span>

![Più punti di ancoraggio esportati utilizzando una singola chiamata TryExportAnchorsAsync](images/multipleanchors.png) ![Più punti di ancoraggio esportati utilizzando una chiamata TryExportAnchorsAsync separata per ogni ancoraggio](images/separateanchors.png)

## <a name="example-send-anchor-data-using-a-windowsnetworkingstreamsocket"></a><span data-ttu-id="354d6-165">Esempio: Inviare dati di ancoraggio con un Windows::Networking::StreamSocket</span><span class="sxs-lookup"><span data-stu-id="354d6-165">Example: Send anchor data using a Windows::Networking::StreamSocket</span></span>

<span data-ttu-id="354d6-166">In questo caso, viene fornito un esempio di come usare i dati esportati ancoraggio inviandolo attraverso una rete TCP.</span><span class="sxs-lookup"><span data-stu-id="354d6-166">Here, we provide an example of how to use exported anchor data by sending it across a TCP network.</span></span> <span data-ttu-id="354d6-167">Si tratta dal HolographicSpatialAnchorTransferSample.</span><span class="sxs-lookup"><span data-stu-id="354d6-167">This is from the HolographicSpatialAnchorTransferSample.</span></span>

<span data-ttu-id="354d6-168">La classe WinRT StreamSocket Usa la libreria di attività PPL.</span><span class="sxs-lookup"><span data-stu-id="354d6-168">The WinRT StreamSocket class uses the PPL task library.</span></span> <span data-ttu-id="354d6-169">Nel caso di errori di rete, viene restituito l'errore all'attività successiva nella catena di utilizzando un'eccezione che viene generata nuovamente.</span><span class="sxs-lookup"><span data-stu-id="354d6-169">In the case of network errors, the error is returned to the next task in the chain using an exception that is re-thrown.</span></span> <span data-ttu-id="354d6-170">L'eccezione contiene un valore HRESULT che indica lo stato di errore.</span><span class="sxs-lookup"><span data-stu-id="354d6-170">The exception contains an HRESULT indicating the error status.</span></span>

### <a name="use-a-windowsnetworkingstreamsocketlistener-with-tcp-to-send-exported-anchor-data"></a><span data-ttu-id="354d6-171">Usare un Windows::Networking::StreamSocketListener con TCP per inviare i dati esportati ancoraggio</span><span class="sxs-lookup"><span data-stu-id="354d6-171">Use a Windows::Networking::StreamSocketListener with TCP to send exported anchor data</span></span>

<span data-ttu-id="354d6-172">Creare un'istanza del server che è in attesa di una connessione.</span><span class="sxs-lookup"><span data-stu-id="354d6-172">Create a server instance that listens for a connection.</span></span>

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

<span data-ttu-id="354d6-173">Quando viene ricevuta una connessione, usare la connessione di socket client per inviare dati di ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="354d6-173">When a connection is received, use the client socket connection to send anchor data.</span></span>

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

<span data-ttu-id="354d6-174">A questo punto, è possibile iniziare a inviare un flusso di dati che contiene i dati esportati ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="354d6-174">Now, we can begin to send a data stream that contains the exported anchor data.</span></span>

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

<span data-ttu-id="354d6-175">Prima di inviare il flusso stesso, è prima necessario inviare un pacchetto di intestazione.</span><span class="sxs-lookup"><span data-stu-id="354d6-175">Before we can send the stream itself, we must first send a header packet.</span></span> <span data-ttu-id="354d6-176">Questo pacchetto di intestazione deve essere di lunghezza fissa e file deve indicare anche la lunghezza della matrice variabile di byte che rappresenta il flusso di dati di ancoraggio; nel caso di questo esempio è non disponibile alcun altri dati di intestazione da inviare, pertanto, l'intestazione è lungo 4 byte e contiene un intero senza segno a 32 bit.</span><span class="sxs-lookup"><span data-stu-id="354d6-176">This header packet must be of fixed length, and it must also indicate the length of the variable array of bytes that is the anchor data stream; in the case of this example we have no other header data to send, so our header is 4 bytes long and contains a 32-bit unsigned integer.</span></span>

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

<span data-ttu-id="354d6-177">Dopo che la lunghezza del flusso, in byte, è stata inviata al client, è possibile procedere a scrivere il flusso di dati nel flusso di socket.</span><span class="sxs-lookup"><span data-stu-id="354d6-177">Once the stream length, in bytes, has been sent to the client, we can proceed to write the data stream itself to the socket stream.</span></span> <span data-ttu-id="354d6-178">In questo modo i byte di archivio di ancoraggio di essere inviata al client.</span><span class="sxs-lookup"><span data-stu-id="354d6-178">This will cause the anchor store bytes to get sent to the client.</span></span>

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

<span data-ttu-id="354d6-179">Come indicato in precedenza in questo argomento, è necessario essere preparati a gestire le eccezioni che contiene i messaggi di stato di errore di rete.</span><span class="sxs-lookup"><span data-stu-id="354d6-179">As noted earlier in this topic, we must be prepared to handle exceptions containing network error status messages.</span></span> <span data-ttu-id="354d6-180">Per gli errori non previsti, è possibile scrivere le informazioni sull'eccezione nella console di debug come illustrato di seguito.</span><span class="sxs-lookup"><span data-stu-id="354d6-180">For errors that are not expected, we can write the exception info to the debug console like so.</span></span> <span data-ttu-id="354d6-181">Ciò fornirà un'indicazione per che cosa è successo se l'esempio di codice è in grado di completare la connessione o se non è in grado di completare l'invio dei dati di ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="354d6-181">This will give us a clue as to what happened if our code sample is unable to complete the connection, or if it is unable to finish sending the anchor data.</span></span>

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

### <a name="use-a-windowsnetworkingstreamsocket-with-tcp-to-receive-exported-anchor-data"></a><span data-ttu-id="354d6-182">Usare un Windows::Networking::StreamSocket con TCP per ricevere i dati esportati ancoraggio</span><span class="sxs-lookup"><span data-stu-id="354d6-182">Use a Windows::Networking::StreamSocket with TCP to receive exported anchor data</span></span>

<span data-ttu-id="354d6-183">In primo luogo, è necessario connettersi al server.</span><span class="sxs-lookup"><span data-stu-id="354d6-183">First, we have to connect to the server.</span></span> <span data-ttu-id="354d6-184">Questo esempio di codice viene illustrato come creare e configurare un StreamSocket e creare un oggetto DataReader che è possibile usare per acquisire dati di rete tramite la connessione socket.</span><span class="sxs-lookup"><span data-stu-id="354d6-184">This code sample shows how to create and configure a StreamSocket, and create a DataReader that you can use to acquire network data using the socket connection.</span></span>

<span data-ttu-id="354d6-185">**NOTA:** Se si esegue questo codice di esempio, assicurarsi di configurare e avviare il server prima di avviare il client.</span><span class="sxs-lookup"><span data-stu-id="354d6-185">**NOTE:** If you run this sample code, ensure that you configure and launch the server before starting the client.</span></span>

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

<span data-ttu-id="354d6-186">Dopo aver ottenuto una connessione, è possibile attendere che il server inviare dati.</span><span class="sxs-lookup"><span data-stu-id="354d6-186">Once we have a connection, we can wait for the server to send data.</span></span> <span data-ttu-id="354d6-187">Facciamo chiamando LoadAsync nel lettore del flusso di dati.</span><span class="sxs-lookup"><span data-stu-id="354d6-187">We do this by calling LoadAsync on the stream data reader.</span></span>

<span data-ttu-id="354d6-188">Il primo set di byte ricevuti devono essere sempre il pacchetto di intestazione, che indica una che lunghezza in byte del flusso di dati di ancoraggio come descritto nella sezione precedente.</span><span class="sxs-lookup"><span data-stu-id="354d6-188">The first set of bytes we receive should always be the header packet, which indicates the anchor data stream byte length as described in the previous section.</span></span>

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

<span data-ttu-id="354d6-189">...</span><span class="sxs-lookup"><span data-stu-id="354d6-189">...</span></span>

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

<span data-ttu-id="354d6-190">Dopo aver ricevuto il pacchetto di intestazione, sappiamo che il numero di byte di dati di ancoraggio è dovrebbero.</span><span class="sxs-lookup"><span data-stu-id="354d6-190">After we have received the header packet, we know how many bytes of anchor data we should expect.</span></span> <span data-ttu-id="354d6-191">È possibile procedere con la lettura dei byte dal flusso.</span><span class="sxs-lookup"><span data-stu-id="354d6-191">We can proceed to read those bytes from the stream.</span></span>

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

<span data-ttu-id="354d6-192">Ecco il nostro codice per la ricezione del flusso di dati di ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="354d6-192">Here's our code for receiving the anchor data stream.</span></span> <span data-ttu-id="354d6-193">Anche in questo caso, si caricherà prima di tutto i byte dal flusso. Questa operazione potrebbe richiedere alcuni minuti perché il StreamSocket attende la ricezione di tale quantità di byte dalla rete.</span><span class="sxs-lookup"><span data-stu-id="354d6-193">Again, we will first load the bytes from the stream; this operation may take some time to complete as the StreamSocket waits to receive that amount of bytes from the network.</span></span>

<span data-ttu-id="354d6-194">Una volta completata l'operazione di caricamento, è possibile leggere tale numero di byte.</span><span class="sxs-lookup"><span data-stu-id="354d6-194">When the loading operation is complete, we can read that number of bytes.</span></span> <span data-ttu-id="354d6-195">Se si riceve il numero di byte che si prevede che per il flusso di dati di ancoraggio, è possibile procedere e importare i dati di ancoraggio. in caso contrario, deve essere stato una sorta di errore.</span><span class="sxs-lookup"><span data-stu-id="354d6-195">If we received the number of bytes that we expect for the anchor data stream, we can go ahead and import the anchor data; if not, there must have been some sort of error.</span></span> <span data-ttu-id="354d6-196">Questa situazione può verificarsi, ad esempio, quando l'istanza del server termina prima che possa essere completato l'invio del flusso di dati o la rete viene interrotta prima che l'intero flusso di dati può essere ricevuto dal client.</span><span class="sxs-lookup"><span data-stu-id="354d6-196">For example, this can happen when the server instance terminates before it can finish sending the data stream, or the network goes down before the entire data stream can be received by the client.</span></span>

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

<span data-ttu-id="354d6-197">Anche in questo caso, è necessario essere preparati a gestire gli errori di rete sconosciuto.</span><span class="sxs-lookup"><span data-stu-id="354d6-197">Again, we must be prepared to handle unknown network errors.</span></span>

```
void SampleAnchorTcpClient::HandleException(Exception^ exception)
{
    std::wstring error = L"Connection error: ";
    error += exception->ToString()->Data();
    error += L"\n";
    OutputDebugString(error.c_str());
}
```

<span data-ttu-id="354d6-198">La procedura è terminata.</span><span class="sxs-lookup"><span data-stu-id="354d6-198">That's it!</span></span> <span data-ttu-id="354d6-199">A questo punto, è necessario disporre di informazioni sufficienti per provare a individuare gli ancoraggi ricevuti in rete.</span><span class="sxs-lookup"><span data-stu-id="354d6-199">Now, you should have enough information to try locating the anchors received over the network.</span></span> <span data-ttu-id="354d6-200">Anche in questo caso, si noti che il client deve avere dati sufficienti rilevamento visual per lo spazio individuare correttamente il punto di ancoraggio; Se non funziona sin da subito, provare a operazioni per un periodo di tempo.</span><span class="sxs-lookup"><span data-stu-id="354d6-200">Again, note that the client must have enough visual tracking data for the space to successfully locate the anchor; if it doesn't work right away, try walking around for a while.</span></span> <span data-ttu-id="354d6-201">Se ancora non funziona, che il server invia ulteriori punti di ancoraggio e usare le comunicazioni di rete per concordare uno che funziona per il client.</span><span class="sxs-lookup"><span data-stu-id="354d6-201">If it still doesn't work, have the server send more anchors, and use network communications to agree on one that works for the client.</span></span> <span data-ttu-id="354d6-202">È possibile provare questa procedura scaricando il HolographicSpatialAnchorTransferSample, configurazione dei client e gli IP del server e distribuirlo ai dispositivi HoloLens client e server.</span><span class="sxs-lookup"><span data-stu-id="354d6-202">You can try this out by downloading the HolographicSpatialAnchorTransferSample, configuring your client and server IPs, and deploying it to client and server HoloLens devices.</span></span>

## <a name="see-also"></a><span data-ttu-id="354d6-203">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="354d6-203">See also</span></span>
* [<span data-ttu-id="354d6-204">Parallel Patterns Library (PPL)</span><span class="sxs-lookup"><span data-stu-id="354d6-204">Parallel Patterns Library (PPL)</span></span>](https://msdn.microsoft.com/library/dd492418.aspx)
* [<span data-ttu-id="354d6-205">Windows.Networking.StreamSocket</span><span class="sxs-lookup"><span data-stu-id="354d6-205">Windows.Networking.StreamSocket</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocket.aspx)
* [<span data-ttu-id="354d6-206">Windows.Networking.StreamSocketListener</span><span class="sxs-lookup"><span data-stu-id="354d6-206">Windows.Networking.StreamSocketListener</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocketlistener.aspx)

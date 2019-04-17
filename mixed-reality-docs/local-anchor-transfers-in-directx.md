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
# <a name="local-anchor-transfers-in-directx"></a>Trasferimenti di ancoraggio locale in DirectX

In situazioni in cui non è possibile usare <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Anchor spaziali Azure</a>, trasferimenti di ancoraggio locale abilitare un dispositivo HoloLens esportare un ancoraggio per essere importati da un secondo dispositivo HoloLens.

>[!NOTE]
>I trasferimenti di ancoraggio locale forniscono richiamo ancoraggio meno affidabile rispetto <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Anchor spaziali Azure</a>, e dispositivi iOS e Android non sono supportati da questo approccio.

>[!NOTE]
>I frammenti di codice in questo articolo illustrano attualmente l'utilizzo di C++/CX invece di C + + 17 conformi C++/WinRT usato nel [ C++ modello di progetto holographic](creating-a-holographic-directx-project.md).  I concetti sono equivalenti per un C++progetto /WinRT, anche se è necessario convertire il codice.

## <a name="transferring-spatial-anchors"></a>Trasferire gli ancoraggi spaziali

È possibile trasferire gli ancoraggi spaziali tra i dispositivi di realtà mista di Windows usando il [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx). Questa API consente di raggruppare un ancoraggio con tutti i dati del sensore supporto necessari per trovare la posizione esatta nel mondo e quindi importare tale pacchetto in un altro dispositivo. Una volta l'app nel dispositivo secondo ha importato l'ancoraggio, ogni app è possibile eseguire il rendering di vntana usando che condivisi sistema di coordinate dell'ancoraggio spaziale, che verranno quindi visualizzati nella stessa posizione nel mondo reale.

Si noti che gli ancoraggi spaziali non sono in grado di trasferire tra i diversi tipi di dispositivi, ad esempio un punto di ancoraggio HoloLens spaziale potrebbe non essere individuabili tramite un visore VR immersivi.  Gli ancoraggi trasferiti non sono compatibili con dispositivi iOS o Android.

## <a name="set-up-your-app-to-use-the-spatialperception-capability"></a>Configurare l'app per usare la funzionalità spatialPerception

L'app deve disporre dell'autorizzazione per usare la funzionalità spatialPerception prima che possa usare la [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx). Ciò è necessario perché il trasferimento di un punto di ancoraggio spaziale prevede la condivisione di immagini di sensori raccolte nel tempo in prossimità di tale punto di ancoraggio, che può contenere informazioni sensibili.

Dichiarare questa funzionalità nel file package. appxmanifest per l'app. Di seguito è riportato un esempio:

```
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

La funzionalità proviene il **uap2** dello spazio dei nomi. Per poter accedere a questo spazio dei nomi nel manifesto, includerlo come un *xlmns* attributo il &lt;pacchetto > elemento. Di seguito è riportato un esempio:

```
<Package
    xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap mp"
    >
```

**NOTA:** L'app dovrà richiedere la funzionalità in fase di esecuzione prima di poter accedere SpatialAnchor le API di importazione/esportazione. Visualizzare [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync.aspx) negli esempi seguenti.

## <a name="serialize-anchor-data-by-exporting-it-with-the-spatialanchortransfermanager"></a>Serializzare i dati di ancoraggio tramite l'esportazione con il SpatialAnchorTransferManager

Una funzione di supporto è incluso nell'esempio di codice da esportare (serializzazione) [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) dati. Questa API esportazione serializza tutti i punti di ancoraggio in una raccolta di coppie chiave-valore, associare gli ancoraggi stringhe.

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

In primo luogo, è necessario configurare il flusso di dati. Ciò permetterà a 1.) usare TryExportAnchorsAsync per inserire i dati in un buffer di proprietà dell'app e 2). leggere dati dal flusso, che è un flusso di dati WinRT - buffer byte esportato in un buffer di memoria, ovvero un std:: Vector&lt;byte >.

```
// Create a random access stream to process the anchor byte data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor byte stream.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
```

È necessario chiedere l'autorizzazione per accedere ai dati spaziali, inclusi gli ancoraggi esportati dal sistema.

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

Se viene visualizzata l'autorizzazione e vengono esportati gli ancoraggi, è possibile leggere il flusso di dati. In questo caso, viene anche illustrato come creare il DataReader e InputStream si userà per leggere i dati.

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

Dopo la lettura dal flusso di byte, è possibile salvarli in un buffer di dati come illustrato di seguito.

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

## <a name="deserialize-anchor-data-by-importing-it-into-the-system-using-the-spatialanchortransfermanager"></a>Deserializzare i dati di ancoraggio importandolo nel sistema tramite il SpatialAnchorTransferManager

Una funzione di supporto è incluso nell'esempio di codice per caricare i dati esportati in precedenza. Questa funzione di deserializzazione fornisce una raccolta di coppie chiave-valore, simile a ciò che fornisce il SpatialAnchorStore - ad eccezione del fatto che abbiamo i dati da un'altra origine, ad esempio un socket di rete. È possibile elaborare e prendere in considerazione i dati prima dell'archiviazione offline, l'uso della memoria, in-app oppure (se applicabile) SpatialAnchorStore dell'app.

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

In primo luogo, dobbiamo creare gli oggetti di flusso per accedere ai dati di ancoraggio. Si scriverà i dati dal nostro buffer in un buffer del sistema, in modo che si creerà un DataWriter che scrive in un flusso di dati in memoria per poter raggiungere l'obiettivo prefissato di entrare nel sistema come SpatialAnchors Anchor da un buffer di byte.

```
// Create a random access stream for the anchor data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor data.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
// Create a writer, to put the bytes in the stream.
DataWriter^ writer = ref new DataWriter(outputStream);
```

Ancora una volta, è necessario assicurarsi che l'app disponga dell'autorizzazione per esportare i dati spaziali di ancoraggio, che potrebbe includere informazioni riservate sull'ambiente dell'utente.

```
// Request access to transfer spatial anchors.
return create_task(SpatialAnchorTransferManager::RequestAccessAsync()).then(
    [&anchorByteDataIn, writer](SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Access is allowed.
```

Se è consentito l'accesso, è possibile scrivere i byte dal buffer in un flusso di dati di sistema.

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

Se si hanno avuto esito positivo nell'archiviazione dei byte nel flusso di dati, è possibile provare a importare i dati usando il SpatialAnchorTransferManager.

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

Sono possibile importare i dati, si ottiene una visualizzazione mappa di coppie chiave-valore associando le stringhe con punti di ancoraggio. È possibile caricarlo in un insieme di dati in memoria e utilizzare tale raccolta per individuare i punti di ancoraggio che siamo interessati all'uso.

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

**NOTA:** Solo perché è possibile importare un ancoraggio, non significa necessariamente che è possibile utilizzare sin da subito. L'ancoraggio potrebbe trovarsi in una stanza diversa o un'altra posizione fisica interamente; il punto di ancoraggio non saranno individuabile fino a quando il dispositivo che lo ha ricevuto ha informazioni sufficienti visual per valutare l'ambiente che è stato creato il punto di ancoraggio, per ripristinare la posizione dell'ancoraggio rispetto all'ambiente corrente noto. L'implementazione client deve provare a individuare il punto di ancoraggio rispetto al sistema di coordinate locale o un frame di riferimento prima di proseguire provare a usarlo per il contenuto in tempo reale. Ad esempio, provare a individuare il punto di ancoraggio rispetto al sistema di coordinate corrente periodicamente fino a quando il punto di ancoraggio inizia a essere individuabili.

## <a name="special-considerations"></a>Considerazioni speciali

Il [TryExportAnchorsAsync](https://msdn.microsoft.com/library/windows/apps/mt592763.aspx) API consente selezioni multiple [SpatialAnchors](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) possono essere esportate nello stesso blob binari opachi. Tuttavia, vi è una sottile differenza nei quali dati include il blob, a seconda del fatto che un singolo SpatialAnchor o SpatialAnchors più vengono esportati in una singola chiamata.

### <a name="export-of-a-single-spatialanchor"></a>Esportazione di un singolo SpatialAnchor

Il blob contiene una rappresentazione dell'ambiente in prossimità di SpatialAnchor in modo che l'ambiente può essere riconosciuto nel dispositivo, che importa il SpatialAnchor. Al termine dell'importazione, il nuovo SpatialAnchor saranno disponibili per il dispositivo. Supponendo che l'utente è stato recentemente in prossimità dell'ancoraggio, renderlo individuabile e vntana collegati al SpatialAnchor possibile eseguire il rendering. Questi vntana appariranno nella stessa posizione fisica che supportavano nel dispositivo originale che esportato il SpatialAnchor.

![Esportazione di un singolo SpatialAnchor](images/singleanchor.png)

### <a name="export-of-multiple-spatialanchors"></a>Esportazione di più SpatialAnchors

Ad esempio l'esportazione di un singolo SpatialAnchor, il blob contiene una rappresentazione dell'ambiente in prossimità di tutti i SpatialAnchors specificato. Inoltre, il blob contiene informazioni sulle connessioni tra SpatialAnchors incluso, se si trovano nello stesso spazio fisico. Ciò significa che se si importano due SpatialAnchors nelle vicinanze, quindi ologramma collegato per il *secondo* SpatialAnchor sarebbe individuabili anche se il dispositivo riconosce solo l'ambiente che circonda il *prima* SpatialAnchor, perché i dati sufficienti per calcolare la trasformazione tra i due SpatialAnchors è stata inclusa nel blob. Se i due SpatialAnchors sono state esportate singolarmente (due chiamate separate al TryExportSpatialAnchors), si potrebbe non essere sufficiente dati inclusi nell'oggetto blob per vntana collegati per la seconda SpatialAnchor essere individuabili quando il primo elemento si trova.

![Più punti di ancoraggio esportati utilizzando una singola chiamata TryExportAnchorsAsync](images/multipleanchors.png) ![Più punti di ancoraggio esportati utilizzando una chiamata TryExportAnchorsAsync separata per ogni ancoraggio](images/separateanchors.png)

## <a name="example-send-anchor-data-using-a-windowsnetworkingstreamsocket"></a>Esempio: Inviare dati di ancoraggio con un Windows::Networking::StreamSocket

In questo caso, viene fornito un esempio di come usare i dati esportati ancoraggio inviandolo attraverso una rete TCP. Si tratta dal HolographicSpatialAnchorTransferSample.

La classe WinRT StreamSocket Usa la libreria di attività PPL. Nel caso di errori di rete, viene restituito l'errore all'attività successiva nella catena di utilizzando un'eccezione che viene generata nuovamente. L'eccezione contiene un valore HRESULT che indica lo stato di errore.

### <a name="use-a-windowsnetworkingstreamsocketlistener-with-tcp-to-send-exported-anchor-data"></a>Usare un Windows::Networking::StreamSocketListener con TCP per inviare i dati esportati ancoraggio

Creare un'istanza del server che è in attesa di una connessione.

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

Quando viene ricevuta una connessione, usare la connessione di socket client per inviare dati di ancoraggio.

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

A questo punto, è possibile iniziare a inviare un flusso di dati che contiene i dati esportati ancoraggio.

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

Prima di inviare il flusso stesso, è prima necessario inviare un pacchetto di intestazione. Questo pacchetto di intestazione deve essere di lunghezza fissa e file deve indicare anche la lunghezza della matrice variabile di byte che rappresenta il flusso di dati di ancoraggio; nel caso di questo esempio è non disponibile alcun altri dati di intestazione da inviare, pertanto, l'intestazione è lungo 4 byte e contiene un intero senza segno a 32 bit.

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

Dopo che la lunghezza del flusso, in byte, è stata inviata al client, è possibile procedere a scrivere il flusso di dati nel flusso di socket. In questo modo i byte di archivio di ancoraggio di essere inviata al client.

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

Come indicato in precedenza in questo argomento, è necessario essere preparati a gestire le eccezioni che contiene i messaggi di stato di errore di rete. Per gli errori non previsti, è possibile scrivere le informazioni sull'eccezione nella console di debug come illustrato di seguito. Ciò fornirà un'indicazione per che cosa è successo se l'esempio di codice è in grado di completare la connessione o se non è in grado di completare l'invio dei dati di ancoraggio.

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

### <a name="use-a-windowsnetworkingstreamsocket-with-tcp-to-receive-exported-anchor-data"></a>Usare un Windows::Networking::StreamSocket con TCP per ricevere i dati esportati ancoraggio

In primo luogo, è necessario connettersi al server. Questo esempio di codice viene illustrato come creare e configurare un StreamSocket e creare un oggetto DataReader che è possibile usare per acquisire dati di rete tramite la connessione socket.

**NOTA:** Se si esegue questo codice di esempio, assicurarsi di configurare e avviare il server prima di avviare il client.

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

Dopo aver ottenuto una connessione, è possibile attendere che il server inviare dati. Facciamo chiamando LoadAsync nel lettore del flusso di dati.

Il primo set di byte ricevuti devono essere sempre il pacchetto di intestazione, che indica una che lunghezza in byte del flusso di dati di ancoraggio come descritto nella sezione precedente.

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

...

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

Dopo aver ricevuto il pacchetto di intestazione, sappiamo che il numero di byte di dati di ancoraggio è dovrebbero. È possibile procedere con la lettura dei byte dal flusso.

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

Ecco il nostro codice per la ricezione del flusso di dati di ancoraggio. Anche in questo caso, si caricherà prima di tutto i byte dal flusso. Questa operazione potrebbe richiedere alcuni minuti perché il StreamSocket attende la ricezione di tale quantità di byte dalla rete.

Una volta completata l'operazione di caricamento, è possibile leggere tale numero di byte. Se si riceve il numero di byte che si prevede che per il flusso di dati di ancoraggio, è possibile procedere e importare i dati di ancoraggio. in caso contrario, deve essere stato una sorta di errore. Questa situazione può verificarsi, ad esempio, quando l'istanza del server termina prima che possa essere completato l'invio del flusso di dati o la rete viene interrotta prima che l'intero flusso di dati può essere ricevuto dal client.

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

Anche in questo caso, è necessario essere preparati a gestire gli errori di rete sconosciuto.

```
void SampleAnchorTcpClient::HandleException(Exception^ exception)
{
    std::wstring error = L"Connection error: ";
    error += exception->ToString()->Data();
    error += L"\n";
    OutputDebugString(error.c_str());
}
```

La procedura è terminata. A questo punto, è necessario disporre di informazioni sufficienti per provare a individuare gli ancoraggi ricevuti in rete. Anche in questo caso, si noti che il client deve avere dati sufficienti rilevamento visual per lo spazio individuare correttamente il punto di ancoraggio; Se non funziona sin da subito, provare a operazioni per un periodo di tempo. Se ancora non funziona, che il server invia ulteriori punti di ancoraggio e usare le comunicazioni di rete per concordare uno che funziona per il client. È possibile provare questa procedura scaricando il HolographicSpatialAnchorTransferSample, configurazione dei client e gli IP del server e distribuirlo ai dispositivi HoloLens client e server.

## <a name="see-also"></a>Vedere anche
* [Parallel Patterns Library (PPL)](https://msdn.microsoft.com/library/dd492418.aspx)
* [Windows.Networking.StreamSocket](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocket.aspx)
* [Windows.Networking.StreamSocketListener](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocketlistener.aspx)

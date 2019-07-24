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
# <a name="local-anchor-transfers-in-directx"></a>Trasferimenti di ancoraggio locali in DirectX

Nei casi in cui non è possibile usare gli <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">ancoraggi spaziali di Azure</a>, i trasferimenti di ancoraggio locali consentono a un dispositivo HoloLens di esportare un ancoraggio per l'importazione da parte di un secondo dispositivo HoloLens.

>[!NOTE]
>I trasferimenti di ancoraggio locali forniscono un richiamo di ancoraggio meno affidabile rispetto agli <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">ancoraggi spaziali di Azure</a>e i dispositivi iOS e Android non sono supportati da questo approccio.

>[!NOTE]
>I frammenti di codice in questo articolo illustrano attualmente l' C++uso di/CX, invece di/WinRT conformi C++a C + 17 come usato nel modello di [ C++ progetto olografico](creating-a-holographic-directx-project.md).  I concetti sono equivalenti per C++un progetto/WinRT, anche se sarà necessario tradurre il codice.

## <a name="transferring-spatial-anchors"></a>Trasferimento di ancoraggi spaziali

È possibile trasferire gli ancoraggi spaziali tra i dispositivi di realtà mista di Windows usando [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx). Questa API consente di aggregare un ancoraggio con tutti i dati del sensore di supporto necessari per trovare la posizione esatta del mondo e quindi importare il bundle in un altro dispositivo. Dopo che l'app nel secondo dispositivo ha importato l'ancoraggio, ogni app può eseguire il rendering degli ologrammi usando il sistema di coordinate dell'ancoraggio spaziale condiviso, che verrà quindi visualizzato nella stessa posizione del mondo reale.

Si noti che gli ancoraggi spaziali non sono in grado di trasferire tra tipi di dispositivi diversi, ad esempio un ancoraggio spaziale HoloLens potrebbe non essere locatable usando un auricolare immersivo.  Anche gli ancoraggi trasferiti non sono compatibili con i dispositivi iOS o Android.

## <a name="set-up-your-app-to-use-the-spatialperception-capability"></a>Configurare l'app per l'uso della funzionalità spatialPerception

È necessario concedere all'app l'autorizzazione per usare la funzionalità spatialPerception prima di poter usare [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx). Questa operazione è necessaria perché il trasferimento di un ancoraggio spaziale comporta la condivisione delle immagini del sensore raccolte nel tempo in prossimità di tale ancoraggio, che potrebbero includere informazioni riservate.

Dichiarare questa funzionalità nel file Package. appxmanifest per l'app. Di seguito è riportato un esempio:

```
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

La funzionalità deriva dallo spazio dei nomi **uap2** . Per ottenere l'accesso a questo spazio dei nomi nel manifesto, includerlo come attributo *xlmns* nell' &lt;elemento > del pacchetto. Di seguito è riportato un esempio:

```
<Package
    xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap mp"
    >
```

**NOTA:** L'app dovrà richiedere la funzionalità in fase di esecuzione prima di poter accedere alle API di esportazione/importazione SpatialAnchor. Vedere [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync.aspx) negli esempi seguenti.

## <a name="serialize-anchor-data-by-exporting-it-with-the-spatialanchortransfermanager"></a>Serializzare i dati di ancoraggio esportandoli con SpatialAnchorTransferManager

Nell'esempio di codice viene inclusa una funzione di supporto per esportare (serializzare) i dati [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) . Questa API di esportazione serializza tutti gli ancoraggi in una raccolta di coppie chiave-valore che associa stringhe a ancoraggi.

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

Prima di tutto, è necessario configurare il flusso di dati. Questa operazione consentirà di eseguire 1. usare TryExportAnchorsAsync per inserire i dati in un buffer di proprietà dell'app e 2. leggere i dati dal flusso del buffer di byte esportato, che è un flusso di dati WinRT, nel buffer di memoria, che è un&lt;byte std:: Vector >.

```
// Create a random access stream to process the anchor byte data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor byte stream.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
```

È necessario richiedere l'autorizzazione per accedere ai dati spaziali, inclusi i Anchor esportati dal sistema.

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

Se si esportano le autorizzazioni e si esportano ancoraggi, è possibile leggere il flusso di dati. Qui viene illustrato anche come creare DataReader e InputStream da usare per leggere i dati.

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

Dopo aver letto i byte dal flusso, è possibile salvarli nel proprio buffer di dati, come indicato di seguito.

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

## <a name="deserialize-anchor-data-by-importing-it-into-the-system-using-the-spatialanchortransfermanager"></a>Deserializzare i dati di ancoraggio importandoli nel sistema usando SpatialAnchorTransferManager

Nell'esempio di codice viene inclusa una funzione di supporto per caricare i dati esportati in precedenza. Questa funzione di deserializzazione fornisce una raccolta di coppie chiave-valore, analogamente a quanto fornito da SpatialAnchorStore, ad eccezione del fatto che sono stati ottenuti questi dati da un'altra origine, ad esempio un socket di rete. È possibile elaborare e ragionare su questi dati prima di archiviarli offline, usando la memoria in-app o (se applicabile) SpatialAnchorStore dell'app.

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

Per prima cosa, è necessario creare oggetti flusso per accedere ai dati di ancoraggio. Verranno scritti i dati dal buffer a un buffer di sistema, quindi verrà creato un DataWriter che scrive in un flusso di dati in memoria per raggiungere l'obiettivo di ottenere gli ancoraggi da un buffer di byte nel sistema come SpatialAnchors.

```
// Create a random access stream for the anchor data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor data.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
// Create a writer, to put the bytes in the stream.
DataWriter^ writer = ref new DataWriter(outputStream);
```

Ancora una volta, è necessario assicurarsi che l'app disponga dell'autorizzazione per esportare i dati di ancoraggio spaziali, che possono includere informazioni private sull'ambiente dell'utente.

```
// Request access to transfer spatial anchors.
return create_task(SpatialAnchorTransferManager::RequestAccessAsync()).then(
    [&anchorByteDataIn, writer](SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Access is allowed.
```

Se l'accesso è consentito, è possibile scrivere byte dal buffer in un flusso di dati di sistema.

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

Se l'archiviazione dei byte nel flusso di dati è riuscita, è possibile provare a importare i dati usando SpatialAnchorTransferManager.

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

Se i dati possono essere importati, si ottiene una visualizzazione mappa delle coppie chiave-valore che associa stringhe a ancoraggi. È possibile caricarlo nella raccolta dei dati in memoria e usare tale raccolta per cercare gli ancoraggi che sono interessati a usare.

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

**NOTA:** Solo perché è possibile importare un ancoraggio, non significa necessariamente che sia possibile utilizzarlo immediatamente. L'ancoraggio potrebbe trovarsi in una stanza diversa o in un'altra posizione fisica. l'ancoraggio non verrà locatable fino a quando il dispositivo che lo ha ricevuto dispone di informazioni visive sufficienti sull'ambiente in cui è stato creato l'ancoraggio, per ripristinare la posizione dell'ancoraggio rispetto all'ambiente corrente noto. L'implementazione client dovrebbe provare a individuare l'ancoraggio rispetto al sistema di coordinate locale o al frame di riferimento prima di continuare a usare per il contenuto Live. Ad esempio, provare a individuare periodicamente l'ancoraggio rispetto a un sistema di coordinate corrente fino a quando l'ancoraggio inizia a essere locatable.

## <a name="special-considerations"></a>Considerazioni speciali

L'API [TryExportAnchorsAsync](https://msdn.microsoft.com/library/windows/apps/mt592763.aspx) consente l'esportazione di più [SpatialAnchors](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) nello stesso BLOB binario opaco. Tuttavia, esiste una lieve differenza nei dati che verranno inclusi nel BLOB, a seconda che un singolo SpatialAnchor o più SpatialAnchors vengano esportati in una singola chiamata.

### <a name="export-of-a-single-spatialanchor"></a>Esportazione di un singolo SpatialAnchor

Il BLOB contiene una rappresentazione dell'ambiente nella vicinanza del SpatialAnchor, in modo che l'ambiente possa essere riconosciuto nel dispositivo che importa il SpatialAnchor. Al termine dell'importazione, il nuovo SpatialAnchor sarà disponibile per il dispositivo. Supponendo che l'utente sia stato recentemente in prossimità dell'ancoraggio, sarà locatable ed è possibile eseguire il rendering degli ologrammi collegati al SpatialAnchor. Questi ologrammi verranno visualizzati nella stessa posizione fisica del dispositivo originale che ha esportato il SpatialAnchor.

![Esportazione di un singolo SpatialAnchor](images/singleanchor.png)

### <a name="export-of-multiple-spatialanchors"></a>Esportazione di più SpatialAnchors

Analogamente all'esportazione di un singolo SpatialAnchor, il BLOB contiene una rappresentazione dell'ambiente in prossimità di tutti i SpatialAnchors specificati. Inoltre, il BLOB contiene informazioni sulle connessioni tra il SpatialAnchors incluso, se si trovano nello stesso spazio fisico. Ciò significa che se vengono importati due SpatialAnchors adiacenti, un ologramma collegato alla *seconda* SpatialAnchor sarà locatable anche se il dispositivo riconosce solo l'ambiente intorno al *primo* SpatialAnchor, perché i dati sono sufficienti per la trasformazione di calcolo tra i due SpatialAnchors è stata inclusa nel BLOB. Se i due SpatialAnchors sono stati esportati singolarmente (due chiamate separate a TryExportSpatialAnchors), potrebbero non essere disponibili dati sufficienti nel BLOB per gli ologrammi collegati al secondo SpatialAnchor per essere locatable quando il primo si trova.

![Più ancoraggi esportati con una singola chiamata TryExportAnchorsAsync](images/multipleanchors.png) ![Più ancoraggi esportati con una chiamata TryExportAnchorsAsync separata per ogni ancoraggio](images/separateanchors.png)

## <a name="example-send-anchor-data-using-a-windowsnetworkingstreamsocket"></a>Esempio: Inviare dati di ancoraggio usando Windows:: Networking:: StreamSocket

In questo esempio viene fornito un esempio di come usare i dati di ancoraggio esportati inviando i dati attraverso una rete TCP. Si tratta di un HolographicSpatialAnchorTransferSample.

La classe WinRT StreamSocket usa la libreria di attività PPL. In caso di errori di rete, l'errore viene restituito all'attività successiva nella catena usando un'eccezione generata nuovamente. L'eccezione contiene un valore HRESULT che indica lo stato di errore.

### <a name="use-a-windowsnetworkingstreamsocketlistener-with-tcp-to-send-exported-anchor-data"></a>Usare Windows:: Networking:: StreamSocketListener con TCP per inviare dati di ancoraggio esportati

Creare un'istanza del server che sia in ascolto di una connessione.

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

Quando viene ricevuta una connessione, usare la connessione socket client per inviare i dati di ancoraggio.

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

A questo punto, è possibile iniziare a inviare un flusso di dati che contiene i dati di ancoraggio esportati.

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

Prima di poter inviare il flusso, è necessario prima inviare un pacchetto di intestazione. Questo pacchetto di intestazione deve avere una lunghezza fissa e deve indicare anche la lunghezza della matrice di variabili di byte che rappresenta il flusso di dati di ancoraggio. nel caso di questo esempio non sono disponibili altri dati di intestazione da inviare, quindi l'intestazione ha una lunghezza di 4 byte e contiene un Unsigned Integer a 32 bit.

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

Una volta che la lunghezza del flusso, in byte, è stata inviata al client, è possibile continuare a scrivere il flusso di dati nel flusso di socket. In questo modo i byte dell'archivio di ancoraggio vengono inviati al client.

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

Come indicato in precedenza in questo argomento, è necessario essere pronti a gestire le eccezioni contenenti messaggi di stato di errore di rete. Per gli errori non previsti, è possibile scrivere le informazioni sull'eccezione nella console di debug come segue. Ciò consentirà di ottenere informazioni sugli eventi che si sono verificati se l'esempio di codice non è in grado di completare la connessione o se non è in grado di completare l'invio di dati di ancoraggio.

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

### <a name="use-a-windowsnetworkingstreamsocket-with-tcp-to-receive-exported-anchor-data"></a>Usare Windows:: Networking:: StreamSocket con TCP per ricevere i dati di ancoraggio esportati

Prima di tutto, è necessario connettersi al server. In questo esempio di codice viene illustrato come creare e configurare un StreamSocket e creare un DataReader che è possibile utilizzare per acquisire i dati di rete tramite la connessione socket.

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

Quando si dispone di una connessione, è possibile attendere che il server invii i dati. Questa operazione viene eseguita chiamando LoadAsync sul lettore dati del flusso.

Il primo set di byte ricevuto deve essere sempre il pacchetto di intestazione, che indica la lunghezza in byte del flusso di dati di ancoraggio, come descritto nella sezione precedente.

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

Dopo aver ricevuto il pacchetto di intestazione, è noto il numero di byte di dati di ancoraggio che ci si aspetta. È possibile procedere con la lettura di tali byte dal flusso.

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

Ecco il nostro codice per la ricezione del flusso di dati di ancoraggio. Prima di tutto, i byte vengono caricati dal flusso. il completamento di questa operazione può richiedere del tempo perché il StreamSocket attende la ricezione della quantità di byte dalla rete.

Al termine dell'operazione di caricamento, è possibile leggere il numero di byte. Se è stato ricevuto il numero di byte previsto per il flusso di dati di ancoraggio, è possibile procedere e importare i dati di ancoraggio. in caso contrario, è necessario che si sia verificato un errore. Questo problema può verificarsi, ad esempio, quando l'istanza del server termina prima che sia possibile completare l'invio del flusso di dati oppure la rete si arresta prima che il client possa ricevere l'intero flusso di dati.

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

Anche in questo caso, è necessario essere pronti a gestire gli errori di rete sconosciuti.

```
void SampleAnchorTcpClient::HandleException(Exception^ exception)
{
    std::wstring error = L"Connection error: ";
    error += exception->ToString()->Data();
    error += L"\n";
    OutputDebugString(error.c_str());
}
```

La procedura è terminata. A questo punto, è necessario disporre di informazioni sufficienti per provare a individuare gli ancoraggi ricevuti sulla rete. Anche in questo caso, si noti che il client deve disporre di un numero sufficiente di dati di rilevamento visivi per lo spazio per individuare correttamente l'ancoraggio. Se non funziona immediatamente, provare a spostarsi per un po'. Se ancora non funziona, fare in modo che il server invii più ancoraggi e usare le comunicazioni di rete per concordare su uno che funzioni per il client. È possibile provare a eseguire questa operazione scaricando HolographicSpatialAnchorTransferSample, configurando gli indirizzi IP del client e del server e distribuendo il server a dispositivi HoloLens client e server.

## <a name="see-also"></a>Vedere anche
* [PPL (Parallel Patterns Library)](https://msdn.microsoft.com/library/dd492418.aspx)
* [Windows. Networking. StreamSocket](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocket.aspx)
* [Windows. Networking. StreamSocketListener](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocketlistener.aspx)

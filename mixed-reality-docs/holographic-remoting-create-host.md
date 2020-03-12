---
title: Scrittura di un'app remota olografica remota
description: Creando un contenuto remoto dell'app remota olografica, di cui viene eseguito il rendering in un computer remoto, può essere trasmesso a HoloLens 2. Questo articolo descrive il modo in cui è possibile ottenere questo risultato.
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens, comunicazione remota, comunicazione remota olografica
ms.openlocfilehash: 76e37499fd32a82e6846c6c7cac1a292ef6b553a
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/11/2020
ms.locfileid: "79092315"
---
# <a name="writing-a-holographic-remoting-remote-app"></a>Scrittura di un'app remota olografica remota

>[!IMPORTANT]
>Questo documento descrive la creazione di un'applicazione remota per HoloLens 2. Le applicazioni remote per **HoloLens (1a Gen)** devono usare il pacchetto NuGet versione **1. x. x**. Ciò implica che le applicazioni remote scritte per HoloLens 2 non sono compatibili con HoloLens 1 e viceversa. La documentazione per HoloLens 1 è disponibile [qui](add-holographic-remoting.md).

Grazie alla creazione di un'app remota olografica remota, il contenuto remoto di cui viene eseguito il rendering in un computer remoto può essere trasmesso a HoloLens 2. Questo articolo descrive il modo in cui è possibile ottenere questo risultato. Tutto il codice in questa pagina e i progetti di lavoro sono disponibili nel [repository GitHub degli esempi di comunicazione remota olografica](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

La comunicazione remota olografica consente a un'app di fare riferimento a HoloLens 2 con contenuto olografico sottoposto a rendering in un computer desktop o in un dispositivo UWP come Xbox One, consentendo l'accesso a più risorse di sistema e rendendo possibile l'integrazione di [visualizzazioni immersive](app-views.md) remote in software per PC desktop esistenti. Un'app remota riceve un flusso di dati di input da HoloLens 2, esegue il rendering del contenuto in una visualizzazione immersiva virtuale e trasmette nuovamente i frame di contenuto a HoloLens 2. La connessione viene eseguita usando il Wi-Fi standard. La comunicazione remota olografica viene aggiunta a un'app desktop o UWP tramite un pacchetto NuGet. È necessario codice aggiuntivo che gestisce la connessione e ne esegue il rendering in una visualizzazione immersiva.

Una tipica connessione remota avrà una bassa di 50 ms di latenza. L'App Player può segnalare la latenza in tempo reale.

## <a name="prerequisites"></a>Prerequisiti

Un punto di partenza efficace è un'app desktop o UWP basata su DirectX funzionante che è destinata all'API di realtà mista di Windows. Per informazioni dettagliate, vedere [Cenni preliminari sullo sviluppo DirectX](directx-development-overview.md). Il [ C++ modello di progetto olografico](creating-a-holographic-directx-project.md) è un punto di partenza valido.

>[!IMPORTANT]
>Qualsiasi app che usa la comunicazione remota olografica deve essere creata per usare un [Apartment](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments)multithread. L'uso di un [Apartment a thread singolo](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) è supportato, ma comporta prestazioni ottimali e possibilmente balbettanti durante la riproduzione. Quando si C++USA/WinRT [WinRT:: init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) un apartment multithread è il valore predefinito.



## <a name="get-the-holographic-remoting-nuget-package"></a>Ottenere il pacchetto NuGet per la comunicazione remota olografica

I passaggi seguenti sono necessari per aggiungere il pacchetto NuGet a un progetto in Visual Studio.
1. Apri il progetto in Visual Studio.
2. Fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Gestisci pacchetti NuGet...**
3. Nel pannello visualizzato fare clic su **Sfoglia** e quindi cercare "comunicazione remota olografica".
4. Selezionare **Microsoft. olografic. Remoting**, assicurarsi di selezionare la versione **2. x.** x più recente e fare clic su **Installa**.
5. Se viene visualizzata la finestra di dialogo **Anteprima** , fare clic su **OK**.
6. La finestra di dialogo successiva visualizzata è il contratto di licenza. Fare clic su **Accetto** per accettare il contratto di licenza.

>[!NOTE]
>La versione **1. x.** x del pacchetto NuGet è ancora disponibile per gli sviluppatori che desiderano utilizzare HoloLens 1. Per informazioni dettagliate, vedere [aggiungere la comunicazione remota olografica (HoloLens (1st Gen))](add-holographic-remoting.md).

## <a name="create-the-remote-context"></a>Creare il contesto remoto

Come primo passaggio, l'applicazione deve creare un contesto remoto.

```cpp
// class declaration
#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
    // RemoteContext used to connect with a Holographic Remoting player and display rendered frames
    winrt::Microsoft::Holographic::AppRemoting::RemoteContext m_remoteContext = nullptr;
```


```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

```

>[!WARNING]
>La comunicazione remota olografica funziona sostituendo il runtime della realtà mista di Windows che fa parte di Windows con un runtime specifico di .NET Remoting. Questa operazione viene eseguita durante la creazione del contesto remoto. Per questo motivo qualsiasi chiamata a qualsiasi API di realtà mista di Windows prima di creare il contesto remoto può causare un comportamento imprevisto. L'approccio consigliato consiste nel creare il contesto remoto il prima possibile prima di interagire con qualsiasi API di realtà mista. Non combinare mai oggetti creati o recuperati tramite qualsiasi API di realtà mista di Windows prima della chiamata a CreateRemoteContext con gli oggetti creati o recuperati in seguito.

Successivamente, è necessario creare lo spazio olografico. Non è necessario specificare un CoreWindow. Le app desktop che non dispongono di un CoreWindow possono semplicemente passare un ```nullptr```.

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(nullptr);
```

## <a name="connect-to-the-device"></a>Connetti al dispositivo

Quando l'app remota è pronta per il rendering del contenuto, è possibile stabilire una connessione al dispositivo.

La connessione può essere eseguita in uno dei due modi seguenti.
1) L'app remota si connette al lettore in esecuzione sul dispositivo.
2) Il lettore in esecuzione sul dispositivo si connette all'app remota.

Per stabilire una connessione dall'app remota a HoloLens 2, chiamare il metodo ```Connect``` nel contesto remoto specificando il nome host e la porta. La porta usata dal lettore di comunicazione remota olografica è **8265**.

```cpp
try
{
    m_remoteContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    DebugLog(L"Connect failed with hr = 0x%08X", e.code());
}
```

>[!IMPORTANT]
>Come per qualsiasi C++API/WinRT ```Connect``` possibile generare un WinRT:: hresult_error che deve essere gestito.

>[!TIP]
>Per evitare di [ C++](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/) usare la proiezione del linguaggio/WinRT, è possibile includere il file ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` che si trova all'interno del pacchetto NuGet remoto olografico. Contiene le dichiarazioni delle interfacce COM sottostanti. Tuttavia, è C++consigliabile usare/WinRT.

L'ascolto delle connessioni in ingresso nell'app remota può essere eseguito chiamando il metodo ```Listen```. Durante questa chiamata è possibile specificare sia la porta di handshake che la porta di trasporto. La porta di handshake viene utilizzata per l'handshake iniziale. I dati vengono quindi inviati tramite la porta di trasporto. Per impostazione predefinita vengono usati **8265** e **8266** .

```cpp
try
{
    m_remoteContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    DebugLog(L"Listen failed with hr = 0x%08X", e.code());
}
```

>[!IMPORTANT]
>Il ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` nel pacchetto NuGet contiene la documentazione dettagliata per l'API esposta dalla comunicazione remota olografica.

## <a name="handling-remoting-specific-events"></a>Gestione di eventi specifici della comunicazione remota

Il contesto remoto espone tre eventi che sono importanti per monitorare lo stato di una connessione.
1) OnConnected: attivato quando una connessione al dispositivo è stata stabilita correttamente.
```cpp
winrt::weak_ref<winrt::Microsoft::Holographic::AppRemoting::IRemoteContext> remoteContextWeakRef = m_remoteContext;

m_onConnectedEventRevoker = m_remoteContext.OnConnected(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```
2) Disconnected: attivato se una connessione stabilita è chiusa o non è stato possibile stabilire una connessione.
```cpp
m_onDisconnectedEventRevoker =
    m_remoteContext.OnDisconnected(winrt::auto_revoke, [this, remoteContextWeakRef](ConnectionFailureReason failureReason) {
        if (auto remoteContext = remoteContextWeakRef.get())
        {
            DebugLog(L"Disconnected with reason %d", failureReason);
            // Update UI

            // Reconnect if this is a transient failure.
            if (failureReason == ConnectionFailureReason::HandshakeUnreachable ||
                failureReason == ConnectionFailureReason::TransportUnreachable ||
                failureReason == ConnectionFailureReason::ConnectionLost)
            {
                DebugLog(L"Reconnecting...");

                ConnectOrListen();
            }
            // Failure reason None indicates a normal disconnect.
            else if (failureReason != ConnectionFailureReason::None)
            {
                DebugLog(L"Disconnected with unrecoverable error, not attempting to reconnect.");
            }
        }
    });
```
3) Onlistening: durante l'ascolto delle connessioni in ingresso viene avviato.
```cpp
m_onListeningEventRevoker = m_remoteContext.OnListening(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```

Inoltre, è possibile eseguire query sullo stato della connessione utilizzando la proprietà ```ConnectionState``` nel contesto remoto.
```cpp
auto connectionState = m_remoteContext.ConnectionState();
```

## <a name="handling-speech-events"></a>Gestione degli eventi di sintesi vocale

Usando l'interfaccia di sintesi vocale remota è possibile registrare trigger di sintesi vocale con HoloLens 2 e renderli remoti all'applicazione remota.

Questo membro aggiuntivo è necessario per tenere traccia dello stato del discorso remoto.

```cpp
winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker m_onRecognizedSpeechRevoker;

```

Prima di tutto è necessario recuperare l'interfaccia vocale remota.

```cpp
if (auto remoteSpeech = m_remoteContext.GetRemoteSpeech())
{
    InitializeSpeechAsync(remoteSpeech, m_onRecognizedSpeechRevoker, weak_from_this());
}
```

Utilizzando un metodo helper asincrono è quindi possibile inizializzare il riconoscimento vocale remoto. Questa operazione deve essere eseguita in modo asincrono perché l'inizializzazione potrebbe richiedere una quantità di tempo considerevole. [Le operazioni di concorrenza e asincrone C++con/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) spiegano come creare funzioni asincrone C++con/WinRT.

```cpp
winrt::Windows::Foundation::IAsyncOperation<winrt::Windows::Storage::StorageFile> LoadGrammarFileAsync()
{
    const wchar_t* speechGrammarFile = L"SpeechGrammar.xml";
    auto rootFolder = winrt::Windows::ApplicationModel::Package::Current().InstalledLocation();
    return rootFolder.GetFileAsync(speechGrammarFile);
}

winrt::fire_and_forget InitializeSpeechAsync(
    winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech remoteSpeech,
    winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker& onRecognizedSpeechRevoker,
    std::weak_ptr<SampleRemoteMain> sampleRemoteMainWeak)
{
    onRecognizedSpeechRevoker = remoteSpeech.OnRecognizedSpeech(
        winrt::auto_revoke, [sampleRemoteMainWeak](const winrt::Microsoft::Holographic::AppRemoting::RecognizedSpeech& recognizedSpeech) {
            if (auto sampleRemoteMain = sampleRemoteMainWeak.lock())
            {
                sampleRemoteMain->OnRecognizedSpeech(recognizedSpeech.RecognizedText);
            }
        });

    auto grammarFile = co_await LoadGrammarFileAsync();

    std::vector<winrt::hstring> dictionary;
    dictionary.push_back(L"Red");
    dictionary.push_back(L"Blue");
    dictionary.push_back(L"Green");
    dictionary.push_back(L"Default");
    dictionary.push_back(L"Aquamarine");

    remoteSpeech.ApplyParameters(L"", grammarFile, dictionary);
}
```

Esistono due modi per specificare le frasi da riconoscere.
1) Specifica all'interno di un file XML di grammatica vocale. Per informazioni dettagliate, vedere [come creare una grammatica XML di base](https://docs.microsoft.com//previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) .
2) Specificare passandoli all'interno del vettore del dizionario per ```ApplyParameters```.

All'interno del callback OnRecognizedSpeech è possibile elaborare gli eventi di riconoscimento vocale:

```cpp
void SampleRemoteMain::OnRecognizedSpeech(const winrt::hstring& recognizedText)
{
    bool changedColor = false;
    DirectX::XMFLOAT4 color = {1, 1, 1, 1};

    if (recognizedText == L"Red")
    {
        color = {1, 0, 0, 1};
        changedColor = true;
    }
    else if (recognizedText == L"Blue")
    {
        color = {0, 0, 1, 1};
        changedColor = true;
    }
    else if (recognizedText == L"Green")
    {
        ...
    }

    ...
}
```

## <a name="preview-streamed-content-locally"></a>Anteprima del contenuto trasmesso localmente

Per visualizzare lo stesso contenuto nell'app remota che viene inviata al dispositivo, è possibile usare ```OnSendFrame``` evento del contesto remoto. L'evento ```OnSendFrame``` viene attivato ogni volta che la libreria remota olografica invia il frame corrente al dispositivo remoto. Questo è il momento ideale per eseguire il contenuto, blit anche nella finestra desktop o UWP.

```cpp
#include <windows.graphics.directx.direct3d11.interop.h>

...

m_onSendFrameEventRevoker = m_remoteContext.OnSendFrame(
    winrt::auto_revoke, [this](const winrt::Windows::Graphics::DirectX::Direct3D11::IDirect3DSurface& texture) {
        winrt::com_ptr<ID3D11Texture2D> texturePtr;
        {
            winrt::com_ptr<ID3D11Resource> resource;
            winrt::com_ptr<::IInspectable> inspectable = texture.as<::IInspectable>();
            winrt::com_ptr<Windows::Graphics::DirectX::Direct3D11::IDirect3DDxgiInterfaceAccess> dxgiInterfaceAccess;
            winrt::check_hresult(inspectable->QueryInterface(__uuidof(dxgiInterfaceAccess), dxgiInterfaceAccess.put_void()));
            winrt::check_hresult(dxgiInterfaceAccess->GetInterface(__uuidof(resource), resource.put_void()));
            resource.as(texturePtr);
        }

        // Copy / blit texturePtr into the back buffer here.
    });
```

## <a name="depth-reprojection"></a>Riproiezione profondità

A partire dalla versione [2.1.0](holographic-remoting-version-history.md#v2.1.0), la comunicazione remota olografica supporta la [riproiezione approfondita](hologram-stability.md#reprojection). Questa operazione richiede, oltre al buffer dei colori, di trasmettere anche il buffer di profondità dall'applicazione remota a HoloLens 2. Per impostazione predefinita, il buffer di profondità viene trasmesso a metà della risoluzione del buffer dei colori. Questo può essere modificato come segue:

```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

// Configure for half-resolution depth.
m_remoteContext.ConfigureDepthVideoStream(DepthBufferStreamResolution::Half_Resolution);

```

Si noti che ```ConfigureDepthVideoStream``` necessario chiamare prima di stabilire una connessione a HoloLens 2. Il posto migliore è quello giusto dopo aver creato il contesto remoto. I valori possibili sono full, Half e Quarter Resolution. Il valore predefinito è la metà della risoluzione. Tenere presente che l'uso di un buffer di profondità di risoluzione completa influiscono anche sui requisiti della larghezza di banda e deve essere considerato nel valore della larghezza di banda massimo fornito per ```CreateRemoteContext```.

Oltre a configurare la risoluzione è anche necessario eseguire il commit di un buffer di profondità tramite [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).

```cpp

void SampleRemoteMain::Render(HolographicFrame holographicFrame)
{
    ...

    m_deviceResources->UseHolographicCameraResources([this, holographicFrame](auto& cameraResourceMap) {
        
        ...

        for (auto cameraPose : prediction.CameraPoses())
        {
            DXHelper::CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();

            ...

            m_deviceResources->UseD3DDeviceContext([&](ID3D11DeviceContext3* context) {
                
                ...

                // Commit depth buffer if available and enabled.
                if (m_canCommitDirect3D11DepthBuffer && m_commitDirect3D11DepthBuffer)
                {
                    auto interopSurface = pCameraResources->GetDepthStencilTextureInteropObject();
                    HolographicCameraRenderingParameters renderingParameters = holographicFrame.GetRenderingParameters(cameraPose);
                    renderingParameters.CommitDirect3D11DepthBuffer(interopSurface);
                }
            });
        }
    });
}

```

Per verificare se la riproiezione approfondita è siano che funziona in HoloLens 2, è possibile abilitare un visualizzatore di profondità tramite il portale del dispositivo. Per informazioni dettagliate, vedere [Verifica della profondità](hologram-stability.md#verifying-depth-is-set-correctly) .

## <a name="optional-custom-data-channels"></a>Facoltativo: canali di dati personalizzati

I canali di dati personalizzati possono essere utilizzati per inviare dati utente tramite la connessione remota già stabilita. Per ulteriori informazioni, vedere [canali di dati personalizzati](holographic-remoting-custom-data-channels.md) .

## <a name="see-also"></a>Vedere anche
* [Scrittura di un'app lettore di comunicazione remota olografica personalizzata](holographic-remoting-create-player.md)
* [Canali di dati di Holographic Remoting personalizzati](holographic-remoting-custom-data-channels.md)
* [Stabilire una connessione sicura con la comunicazione remota olografica](holographic-remoting-secure-connection.md)
* [Limitazioni e risoluzione dei problemi di comunicazione remota olografica](holographic-remoting-troubleshooting.md)
* [Condizioni di licenza software per Holographic Remoting](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Informativa sulla privacy Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)

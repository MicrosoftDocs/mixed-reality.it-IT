---
title: Scrittura di un lettore di comunicazione remota olografica personalizzata
description: Grazie alla creazione di un'app lettore di comunicazione remota olografica personalizzata è possibile creare un'applicazione personalizzata in grado di visualizzare il contenuto di cui è stato eseguito il rendering in un computer remoto in HoloLens 2. Questo articolo descrive il modo in cui è possibile ottenere questo risultato.
author: NPohl-MSFT
ms.author: nopohl
ms.date: 08/01/2019
ms.topic: article
keywords: HoloLens, comunicazione remota, comunicazione remota olografica
ms.openlocfilehash: fdc3d3bbd72d0812377d6a70c975f2111e1a2224
ms.sourcegitcommit: ca949efe0279995a376750d89e23d7123eb44846
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/01/2019
ms.locfileid: "68718095"
---
# <a name="writing-a-custom-holographic-remoting-player-app"></a>Scrittura di un'app lettore di comunicazione remota olografica personalizzata

>[!IMPORTANT]
>Questo documento descrive la creazione di un'applicazione lettore personalizzata per HoloLens 2. I lettori personalizzati scritti per HoloLens 2 non sono compatibili con le applicazioni host scritte per HoloLens 1. Questo implica che entrambe le applicazioni devono usare il pacchetto NuGet versione **2.** x. x.

Grazie alla creazione di un'app lettore di comunicazione remota olografica personalizzata è possibile creare un'applicazione personalizzata in grado di visualizzare [visualizzazioni immersive](app-views.md) da in un computer remoto nel HoloLens 2. Questo articolo descrive il modo in cui è possibile ottenere questo risultato. Tutto il codice in questa pagina e i progetti di lavoro sono disponibili nel [repository GitHub degli esempi di comunicazione remota olografica](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

Un lettore di comunicazione remota olografica consente all'app di visualizzare il contenuto olografico [eseguito](rendering.md) su un computer desktop o su un dispositivo UWP, ad esempio la Xbox One, consentendo l'accesso a più risorse di sistema. Un'app lettore di comunicazione remota olografica trasmette i dati di input a un'applicazione host di comunicazione remota olografica e riceve una visualizzazione immersiva come flusso video e audio. La connessione viene eseguita usando il Wi-Fi standard. Per creare un'app per giocatori, si userà un pacchetto NuGet per aggiungere la comunicazione remota olografica all'app UWP e scrivere il codice per gestire la connessione e per visualizzare una visualizzazione immersiva. 

## <a name="prerequisites"></a>Prerequisiti

Un punto di partenza valido è un'app UWP basata su DirectX funzionante che ha già come destinazione l'API di realtà mista di Windows. Per informazioni dettagliate, vedere [Cenni preliminari sullo sviluppo DirectX](directx-development-overview.md). Se non si dispone di un'app esistente e si desidera iniziare da zero, il [ C++ modello di progetto olografico](creating-a-holographic-directx-project.md) è un punto di partenza valido.

>[!IMPORTANT]
>Qualsiasi app che usa la comunicazione remota olografica deve essere creata per usare un [Apartment](https://docs.microsoft.com/en-us/windows/win32/com/multithreaded-apartments)multithread. L'uso di un [Appartamento a thread singolo](https://docs.microsoft.com/en-us/windows/win32/com/single-threaded-apartments) è supportato, ma comporta prestazioni ottimali e possibilmente balbettanti durante la riproduzione. Quando si C++USA/WinRT [WinRT:: init_apartment](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/get-started) , un apartment multithread è il valore predefinito.

## <a name="get-the-holographic-remoting-nuget-package"></a>Ottenere il pacchetto NuGet per la comunicazione remota olografica

I passaggi seguenti sono necessari per aggiungere il pacchetto NuGet a un progetto in Visual Studio.
1. Aprire il progetto in Visual Studio.
2. Fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Gestisci pacchetti NuGet...**
3. Nel pannello visualizzato fare clic su **Sfoglia** e quindi cercare "comunicazione remota olografica".
4. Selezionare **Microsoft. olografic. Remoting**, assicurarsi di selezionare la versione **2. x.** x più recente e fare clic su **Installa**.
5. Se viene visualizzata la finestra di dialogo **Anteprima** , fare clic su **OK**.
6. La finestra di dialogo successiva visualizzata è il contratto di licenza. Fare clic su **Accetto** per accettare il contratto di licenza.

>[!IMPORTANT]
><a name="idl"></a>Il ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` contenuto del pacchetto NuGet contiene la documentazione dettagliata per l'API esposta dalla comunicazione remota olografica.

## <a name="modify-the-packageappxmanifest-of-the-application"></a>Modificare il pacchetto. appxmanifest dell'applicazione

Per fare in modo che l'applicazione sia in grado di riconoscere Microsoft. Olografic. AppRemoting. dll aggiunto dal pacchetto NuGet, è necessario eseguire i passaggi seguenti nel progetto:

1. Nella Esplora soluzioni fare clic con il pulsante destro del mouse sul file **Package. appxmanifest** e scegliere **Apri con...**
2. Selezionare l' **editor XML (testo)** e fare clic su OK.
3. Aggiungere le righe seguenti al file e salvare
```xml
  </Capabilities>

  <!--Add lines below -->
  <Extensions>
    <Extension Category="windows.activatableClass.inProcessServer">
      <InProcessServer>
        <Path>Microsoft.Holographic.AppRemoting.dll</Path>
        <ActivatableClass ActivatableClassId="Microsoft.Holographic.AppRemoting.PlayerContext" ThreadingModel="both" />
      </InProcessServer>
    </Extension>
  </Extensions>
  <!--Add lines above -->

</Package>
```
## <a name="create-the-player-context"></a>Creare il contesto del lettore

Come primo passaggio, l'applicazione deve creare un contesto del lettore.

```cpp
// class declaration:

#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
// PlayerContext used to connect with a Holographic Remoting host and display remotely rendered frames
winrt::Microsoft::Holographic::AppRemoting::PlayerContext m_playerContext = nullptr;
```


```cpp
// class implementation:

// Create the player context
// IMPORTANT: This must be done before creating the HolographicSpace (or any other call to the Holographic API).
m_playerContext = winrt::Microsoft::Holographic::AppRemoting::PlayerContext::Create();

```

>[!WARNING]
>La comunicazione remota olografica funziona sostituendo il runtime della realtà mista di Windows che fa parte di Windows con un runtime specifico di .NET Remoting. Questa operazione viene eseguita durante la creazione del contesto del lettore. Per questo motivo qualsiasi chiamata a qualsiasi API di realtà mista di Windows prima di creare il contesto del lettore può causare un comportamento imprevisto. L'approccio consigliato consiste nel creare il contesto del lettore il prima possibile prima di interagire con qualsiasi API di realtà mista. Non combinare mai oggetti creati o recuperati tramite qualsiasi API di realtà mista di ```PlayerContext::Create()``` Windows prima della chiamata a con gli oggetti creati o recuperati in seguito.

Successivamente, è possibile creare HolographicSpace, chiamando [HolographicSpace. CreateForCoreWindow](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow).

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(window);
```

## <a name="connect-to-the-host"></a>Connetti all'host

Quando l'App Player è pronta per il rendering del contenuto, è possibile stabilire una connessione all'host.

La connessione può essere stabilita in uno dei modi follwing:
1) L'App Player in esecuzione su HoloLens 2 si connette all'app host.
2) L'app host si connette all'App Player in esecuzione su HoloLens 2.

Per connettersi dall'App Player all'host, chiamare il ```Connect``` metodo sul contesto del lettore specificando il nome host e la porta. La porta predefinita è **8265**.

```cpp
try
{
    m_playerContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    // Failed to connect. Get an error details via e.code() and e.message()
}
```

>[!IMPORTANT]
>Come per qualsiasi C++API ```Connect``` /WinRT, può generare un WinRT:: hresult_error che deve essere gestito.

L'ascolto delle connessioni in ingresso nell'App Player può essere eseguito chiamando il ```Listen``` metodo. Durante questa chiamata è possibile specificare sia la porta di handshake che la porta di trasporto. La porta di handshake viene utilizzata per l'handshake iniziale. I dati vengono quindi inviati tramite la porta di trasporto. Per impostazione predefinita vengono usati il numero di porta **8265** e **8266** .

```cpp
try
{
    m_playerContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    // Failed to listen. Get an error details via e.code() and e.message()
}
```


## <a name="handling-connection-related-events"></a>Gestione degli eventi correlati alla connessione

```PlayerContext``` Espone tre eventi per monitorare lo stato della connessione.
1) OnConnected: Attivato quando una connessione all'host viene stabilita correttamente.
```cpp
m_onConnectedEventToken = m_playerContext.OnConnected([]() 
{
    // Handle connection successfully established
});
```
2) Disconnected: Attivato se una connessione stabilita viene terminata o non è stato possibile stabilire una connessione.
```cpp
m_onDisconnectedEventToken = m_playerContext.OnDisconnected([](ConnectionFailureReason failureReason)
{
    switch (failureReason)
    {
        // Handle connection failed or terminated.
        // See ConnectionFailureReason for possible reasons.
    }
}
```
>[!NOTE]
>I ```ConnectionFailureReason``` valori possibili sono documentati ```Microsoft.Holographic.AppRemoting.idl``` nel [file](#idl).

3) Onlistening: In attesa dell'avvio delle connessioni in ingresso.
```cpp
m_onListeningEventToken = m_playerContext.OnListening([]()
{
    // Handle start listening for incoming connections
});
```

Inoltre, è possibile eseguire query sullo stato della connessione ```ConnectionState``` utilizzando la proprietà nel contesto del lettore.
```cpp
winrt::Microsoft::Holographic::AppRemoting::ConnectionState state = m_playerContext.ConnectionState();
```

## <a name="display-the-remotely-rendered-frame"></a>Visualizzare il frame sottoposto a rendering remoto

Per visualizzare il contenuto di cui è stato eseguito ```PlayerContext::BlitRemoteFrame()``` il rendering in remoto, chiamare durante il rendering di un [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe). 

```BlitRemoteFrame()```richiede che il buffer nascosto per la HolographicFrame corrente sia associato come destinazione di rendering. Il buffer nascosto può essere ricevuto da [HolographicCameraRenderingParameters](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) tramite la proprietà [Direct3D11BackBuffer](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer) .

Quando viene chiamato ```BlitRemoteFrame()``` , copia l'ultimo frame ricevuto dall'applicazione host nel buffer di HolographicFrame. Inoltre, il set di punti di interesse è impostato, se l'applicazione remota ha specificato un punto di attivazione durante il rendering del frame remoto.

```cpp
// Blit the remote frame into the backbuffer for the HolographicFrame.
winrt::Microsoft::Holographic::AppRemoting::BlitResult result = m_playerContext.BlitRemoteFrame();
```

>[!NOTE]
>```PlayerContext::BlitRemoteFrame()```potenzialmente sovrascrive il punto di messa a fuoco per il frame corrente. 
>- Per specificare un punto di attivazione di fallback, chiamare [HolographicCameraRenderingParameters:: SetFocusPoint](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) prima ```PlayerContext::BlitRemoteFrame()```di. 
>- Per overrwrite il punto di attivazione remota, chiamare [HolographicCameraRenderingParameters:: SetFocusPoint](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) dopo ```PlayerContext::BlitRemoteFrame()```.

Se l'operazione ```BlitRemoteFrame()``` riesce ```BlitResult::Success_Color```, restituisce. In caso contrario, restituisce il motivo dell'errore:
- ```BlitResult::Failed_NoRemoteFrameAvailable```: Operazione non riuscita perché non è disponibile un frame remoto.
- ```BlitResult::Failed_NoCamera```: Operazione non riuscita perché non è presente alcuna fotocamera.

## <a name="optional-get-statistics-about-the-last-remote-frame"></a>Facoltativo: Ottenere le statistiche sull'ultimo frame remoto

Per diagnosticare problemi di prestazioni o di rete, è possibile recuperare le statistiche sull'ultimo frame remoto ```PlayerContext::LastFrameStatistics``` tramite la proprietà. Le statistiche vengono aggiornate durante la chiamata a [HolographicFrame::P resentusingcurrentprediction](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction).

```cpp
// Get statistics for the last presented frame.
winrt::Microsoft::Holographic::AppRemoting::PlayerFrameStatistics statistics = m_playerContext.LastFrameStatistics();
```

Per ulteriori informazioni, vedere la ```PlayerFrameStatistics``` documentazione ```Microsoft.Holographic.AppRemoting.idl``` nel [file](#idl).

## <a name="optional-custom-data-channels"></a>Facoltativo: Canali di dati personalizzati

I canali di dati personalizzati possono essere utilizzati per inviare dati utente tramite la connessione remota già stabilita. Per ulteriori informazioni, vedere [canali di dati personalizzati](holographic-remoting-custom-data-channels.md) .

## <a name="see-also"></a>Vedere anche
* [Scrittura di un'app host di comunicazione remota olografica](holographic-remoting-create-host.md)
* [Canali di dati di comunicazione remota olografica personalizzati](holographic-remoting-custom-data-channels.md)
* [Stabilire una connessione sicura con la comunicazione remota olografica](holographic-remoting-secure-connection.md)
* [Limitazioni e risoluzione dei problemi di comunicazione remota olografica](holographic-remoting-troubleshooting.md)
* [Condizioni di licenza software per la comunicazione remota olografica](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Informativa sulla privacy Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
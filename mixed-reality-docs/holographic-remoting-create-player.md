---
title: Scrittura di un lettore di comunicazione remota olografica personalizzata
description: Grazie alla creazione di un'app lettore di comunicazione remota olografica personalizzata è possibile creare un'applicazione personalizzata in grado di visualizzare il contenuto di cui è stato eseguito il rendering in un computer remoto in HoloLens 2. Questo articolo descrive il modo in cui è possibile ottenere questo risultato.
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens, comunicazione remota, comunicazione remota olografica
ms.openlocfilehash: eaa6549eb34d3a37c21b3decb348bf43594a110f
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/11/2020
ms.locfileid: "79092418"
---
# <a name="writing-a-custom-holographic-remoting-player-app"></a><span data-ttu-id="1d57a-105">Scrittura di un'app lettore di comunicazione remota olografica personalizzata</span><span class="sxs-lookup"><span data-stu-id="1d57a-105">Writing a custom Holographic Remoting player app</span></span>

>[!IMPORTANT]
><span data-ttu-id="1d57a-106">Questo documento descrive la creazione di un'applicazione lettore personalizzata per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1d57a-106">This document describes the creation of a custom player application for HoloLens 2.</span></span> <span data-ttu-id="1d57a-107">I lettori personalizzati scritti per HoloLens 2 non sono compatibili con le applicazioni remote scritte per HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="1d57a-107">Custom players written for HoloLens 2 are not compatible with remote applications written for HoloLens 1.</span></span> <span data-ttu-id="1d57a-108">Questo implica che entrambe le applicazioni devono usare il pacchetto NuGet versione **2.** x. x.</span><span class="sxs-lookup"><span data-stu-id="1d57a-108">This implies that both applications must use NuGet package version **2.x.x**.</span></span>

<span data-ttu-id="1d57a-109">Grazie alla creazione di un'app lettore di comunicazione remota olografica personalizzata è possibile creare un'applicazione personalizzata in grado di visualizzare [visualizzazioni immersive](app-views.md) da in un computer remoto nel HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1d57a-109">By creating a custom Holographic Remoting player app you can create a custom application capable of displaying [immersive views](app-views.md) from on a remote machine on your HoloLens 2.</span></span> <span data-ttu-id="1d57a-110">Questo articolo descrive il modo in cui è possibile ottenere questo risultato.</span><span class="sxs-lookup"><span data-stu-id="1d57a-110">This article describes how this can be achieved.</span></span> <span data-ttu-id="1d57a-111">Tutto il codice in questa pagina e i progetti di lavoro sono disponibili nel [repository GitHub degli esempi di comunicazione remota olografica](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span><span class="sxs-lookup"><span data-stu-id="1d57a-111">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

<span data-ttu-id="1d57a-112">Un lettore di comunicazione remota olografica consente all'app di visualizzare il contenuto olografico [eseguito](rendering.md) su un computer desktop o su un dispositivo UWP, ad esempio la Xbox One, consentendo l'accesso a più risorse di sistema.</span><span class="sxs-lookup"><span data-stu-id="1d57a-112">A Holographic Remoting player allows your app to display holographic content [rendered](rendering.md) on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources.</span></span> <span data-ttu-id="1d57a-113">Un'app lettore di comunicazione remota olografica trasmette i dati di input a un'applicazione remota olografica remota e riceve una visualizzazione immersiva come flusso video e audio.</span><span class="sxs-lookup"><span data-stu-id="1d57a-113">A Holographic Remoting player app streams input data to a Holographic Remoting remote application and receives back an immersive view as video and audio stream.</span></span> <span data-ttu-id="1d57a-114">La connessione viene eseguita usando il Wi-Fi standard.</span><span class="sxs-lookup"><span data-stu-id="1d57a-114">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="1d57a-115">Per creare un'app per giocatori, si userà un pacchetto NuGet per aggiungere la comunicazione remota olografica all'app UWP e scrivere il codice per gestire la connessione e per visualizzare una visualizzazione immersiva.</span><span class="sxs-lookup"><span data-stu-id="1d57a-115">To create a player app, you will use a NuGet package to add Holographic Remoting to your UWP app, and write code to handle the connection and to display an immersive view.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="1d57a-116">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="1d57a-116">Prerequisites</span></span>

<span data-ttu-id="1d57a-117">Un punto di partenza valido è un'app UWP basata su DirectX funzionante che ha già come destinazione l'API di realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="1d57a-117">A good starting point is a working DirectX based UWP app that already targets the Windows Mixed Reality API.</span></span> <span data-ttu-id="1d57a-118">Per informazioni dettagliate, vedere [Cenni preliminari sullo sviluppo DirectX](directx-development-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1d57a-118">For details see [DirectX development overview](directx-development-overview.md).</span></span> <span data-ttu-id="1d57a-119">Se non si dispone di un'app esistente e si desidera iniziare da zero, il [ C++ modello di progetto olografico](creating-a-holographic-directx-project.md) è un punto di partenza valido.</span><span class="sxs-lookup"><span data-stu-id="1d57a-119">If you do not have an existing app and want to start from scratch the [C++ holographic project template](creating-a-holographic-directx-project.md) is a good starting point.</span></span>

>[!IMPORTANT]
><span data-ttu-id="1d57a-120">Qualsiasi app che usa la comunicazione remota olografica deve essere creata per usare un [Apartment](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments)multithread.</span><span class="sxs-lookup"><span data-stu-id="1d57a-120">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="1d57a-121">L'uso di un [Appartamento a thread singolo](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) è supportato, ma comporta prestazioni ottimali e possibilmente balbettanti durante la riproduzione.</span><span class="sxs-lookup"><span data-stu-id="1d57a-121">The use of a [single-threaded appartment](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="1d57a-122">Quando si C++USA/WinRT [WinRT:: init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) un apartment multithread è il valore predefinito.</span><span class="sxs-lookup"><span data-stu-id="1d57a-122">When using C++/WinRT [winrt::init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>

## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="1d57a-123">Ottenere il pacchetto NuGet per la comunicazione remota olografica</span><span class="sxs-lookup"><span data-stu-id="1d57a-123">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="1d57a-124">I passaggi seguenti sono necessari per aggiungere il pacchetto NuGet a un progetto in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1d57a-124">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="1d57a-125">Apri il progetto in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1d57a-125">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="1d57a-126">Fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Gestisci pacchetti NuGet...**</span><span class="sxs-lookup"><span data-stu-id="1d57a-126">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="1d57a-127">Nel pannello visualizzato fare clic su **Sfoglia** e quindi cercare "comunicazione remota olografica".</span><span class="sxs-lookup"><span data-stu-id="1d57a-127">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="1d57a-128">Selezionare **Microsoft. olografic. Remoting**, assicurarsi di selezionare la versione **2. x.** x più recente e fare clic su **Installa**.</span><span class="sxs-lookup"><span data-stu-id="1d57a-128">Select **Microsoft.Holographic.Remoting**, ensure to pick the latest **2.x.x** version and click **Install**.</span></span>
5. <span data-ttu-id="1d57a-129">Se viene visualizzata la finestra di dialogo **Anteprima** , fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="1d57a-129">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="1d57a-130">La finestra di dialogo successiva visualizzata è il contratto di licenza.</span><span class="sxs-lookup"><span data-stu-id="1d57a-130">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="1d57a-131">Fare clic su **Accetto** per accettare il contratto di licenza.</span><span class="sxs-lookup"><span data-stu-id="1d57a-131">Click on **I Accept** to accept the license agreement.</span></span>

>[!IMPORTANT]
><a name="idl"></a><span data-ttu-id="1d57a-132">Il ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` nel pacchetto NuGet contiene la documentazione dettagliata per l'API esposta dalla comunicazione remota olografica.</span><span class="sxs-lookup"><span data-stu-id="1d57a-132">The ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` inside the NuGet package contains detailed documentation for the API exposed by Holographic Remoting.</span></span>

## <a name="modify-the-packageappxmanifest-of-the-application"></a><span data-ttu-id="1d57a-133">Modificare il pacchetto. appxmanifest dell'applicazione</span><span class="sxs-lookup"><span data-stu-id="1d57a-133">Modify the Package.appxmanifest of the application</span></span>

<span data-ttu-id="1d57a-134">Per fare in modo che l'applicazione sia in grado di riconoscere Microsoft. Olografic. AppRemoting. dll aggiunto dal pacchetto NuGet, è necessario eseguire i passaggi seguenti nel progetto:</span><span class="sxs-lookup"><span data-stu-id="1d57a-134">To make the application aware of the Microsoft.Holographic.AppRemoting.dll added by the NuGet package, the following steps need to be taken on the project:</span></span>

1. <span data-ttu-id="1d57a-135">Nella Esplora soluzioni fare clic con il pulsante destro del mouse sul file **Package. appxmanifest** e scegliere **Apri con...**</span><span class="sxs-lookup"><span data-stu-id="1d57a-135">In the Solution Explorer right-click on the **Package.appxmanifest** file and select **Open With...**</span></span>
2. <span data-ttu-id="1d57a-136">Selezionare l' **editor XML (testo)** e fare clic su OK.</span><span class="sxs-lookup"><span data-stu-id="1d57a-136">Select **XML (Text) Editor** and click OK</span></span>
3. <span data-ttu-id="1d57a-137">Aggiungere le righe seguenti al file e salvare</span><span class="sxs-lookup"><span data-stu-id="1d57a-137">Add the following lines to the file and save</span></span>
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
## <a name="create-the-player-context"></a><span data-ttu-id="1d57a-138">Creare il contesto del lettore</span><span class="sxs-lookup"><span data-stu-id="1d57a-138">Create the player context</span></span>

<span data-ttu-id="1d57a-139">Come primo passaggio, l'applicazione deve creare un contesto del lettore.</span><span class="sxs-lookup"><span data-stu-id="1d57a-139">As a first step the application should create a player context.</span></span>

```cpp
// class declaration:

#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
// PlayerContext used to connect with a Holographic Remoting remote app and display remotely rendered frames
winrt::Microsoft::Holographic::AppRemoting::PlayerContext m_playerContext = nullptr;
```


```cpp
// class implementation:

// Create the player context
// IMPORTANT: This must be done before creating the HolographicSpace (or any other call to the Holographic API).
m_playerContext = winrt::Microsoft::Holographic::AppRemoting::PlayerContext::Create();

```

>[!WARNING]
><span data-ttu-id="1d57a-140">La comunicazione remota olografica funziona sostituendo il runtime della realtà mista di Windows che fa parte di Windows con un runtime specifico di .NET Remoting.</span><span class="sxs-lookup"><span data-stu-id="1d57a-140">Holographic Remoting works by replacing the Windows Mixed Reality runtime which is part of Windows with a remoting specific runtime.</span></span> <span data-ttu-id="1d57a-141">Questa operazione viene eseguita durante la creazione del contesto del lettore.</span><span class="sxs-lookup"><span data-stu-id="1d57a-141">This is done during the creation of the player context.</span></span> <span data-ttu-id="1d57a-142">Per questo motivo qualsiasi chiamata a qualsiasi API di realtà mista di Windows prima di creare il contesto del lettore può causare un comportamento imprevisto.</span><span class="sxs-lookup"><span data-stu-id="1d57a-142">For that reason any call on any Windows Mixed Reality API before creating the player context can result in unexpected behavior.</span></span> <span data-ttu-id="1d57a-143">L'approccio consigliato consiste nel creare il contesto del lettore il prima possibile prima di interagire con qualsiasi API di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="1d57a-143">The recommended approach is to create the player context as early as possible before interaction with any Mixed Reality API.</span></span> <span data-ttu-id="1d57a-144">Non combinare mai oggetti creati o recuperati tramite qualsiasi API di realtà mista di Windows prima della chiamata a ```PlayerContext::Create``` con gli oggetti creati o recuperati in seguito.</span><span class="sxs-lookup"><span data-stu-id="1d57a-144">Never mix objects created or retrieved through any Windows Mixed Reality API before the call to ```PlayerContext::Create``` with objects created or retrieved afterwards.</span></span>

<span data-ttu-id="1d57a-145">Successivamente, è possibile creare HolographicSpace, chiamando [HolographicSpace. CreateForCoreWindow](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow).</span><span class="sxs-lookup"><span data-stu-id="1d57a-145">Next the HolographicSpace can be created, by calling [HolographicSpace.CreateForCoreWindow](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow).</span></span>

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(window);
```

## <a name="connect-to-the-remote-app"></a><span data-ttu-id="1d57a-146">Connettersi all'app remota</span><span class="sxs-lookup"><span data-stu-id="1d57a-146">Connect to the remote app</span></span>

<span data-ttu-id="1d57a-147">Quando l'App Player è pronta per il rendering del contenuto, è possibile stabilire una connessione all'app remota.</span><span class="sxs-lookup"><span data-stu-id="1d57a-147">Once the player app is ready for rendering content a connection to the remote app can be established.</span></span>

<span data-ttu-id="1d57a-148">La connessione può essere stabilita in uno dei modi seguenti:</span><span class="sxs-lookup"><span data-stu-id="1d57a-148">The connection can be established in one of the following ways:</span></span>
1) <span data-ttu-id="1d57a-149">L'App Player in esecuzione su HoloLens 2 si connette all'app remota.</span><span class="sxs-lookup"><span data-stu-id="1d57a-149">The player app running on HoloLens 2 connects to the remote app.</span></span>
2) <span data-ttu-id="1d57a-150">L'app remota si connette all'App Player in esecuzione su HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1d57a-150">The remote app connects to the player app running on HoloLens 2.</span></span>

<span data-ttu-id="1d57a-151">Per connettersi dall'App Player all'app remota, chiamare il metodo ```Connect``` nel contesto del lettore specificando il nome host e la porta.</span><span class="sxs-lookup"><span data-stu-id="1d57a-151">To connect from the player app to the remote app call the ```Connect``` method on the player context specifying the hostname and port.</span></span> <span data-ttu-id="1d57a-152">La porta predefinita è **8265**.</span><span class="sxs-lookup"><span data-stu-id="1d57a-152">The default port is **8265**.</span></span>

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
><span data-ttu-id="1d57a-153">Come per qualsiasi C++API/WinRT ```Connect``` possibile generare un WinRT:: hresult_error che deve essere gestito.</span><span class="sxs-lookup"><span data-stu-id="1d57a-153">As with any C++/WinRT API ```Connect``` might throw an winrt::hresult_error which needs to be handled.</span></span>

<span data-ttu-id="1d57a-154">L'ascolto delle connessioni in ingresso nell'App Player può essere eseguito chiamando il metodo ```Listen```.</span><span class="sxs-lookup"><span data-stu-id="1d57a-154">Listening for incoming connections on the player app can be done by calling the ```Listen``` method.</span></span> <span data-ttu-id="1d57a-155">Durante questa chiamata è possibile specificare sia la porta di handshake che la porta di trasporto.</span><span class="sxs-lookup"><span data-stu-id="1d57a-155">Both the handshake port and transport port can be specified during this call.</span></span> <span data-ttu-id="1d57a-156">La porta di handshake viene utilizzata per l'handshake iniziale.</span><span class="sxs-lookup"><span data-stu-id="1d57a-156">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="1d57a-157">I dati vengono quindi inviati tramite la porta di trasporto.</span><span class="sxs-lookup"><span data-stu-id="1d57a-157">The data is then send over the transport port.</span></span> <span data-ttu-id="1d57a-158">Per impostazione predefinita vengono usati il numero di porta **8265** e **8266** .</span><span class="sxs-lookup"><span data-stu-id="1d57a-158">By default port number **8265** and **8266** are used.</span></span>

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


## <a name="handling-connection-related-events"></a><span data-ttu-id="1d57a-159">Gestione degli eventi correlati alla connessione</span><span class="sxs-lookup"><span data-stu-id="1d57a-159">Handling connection related events</span></span>

<span data-ttu-id="1d57a-160">Il ```PlayerContext``` espone tre eventi per monitorare lo stato della connessione</span><span class="sxs-lookup"><span data-stu-id="1d57a-160">The ```PlayerContext``` exposes three events to monitor the state of the connection</span></span>
1) <span data-ttu-id="1d57a-161">OnConnected: attivato quando una connessione all'app remota è stata stabilita correttamente.</span><span class="sxs-lookup"><span data-stu-id="1d57a-161">OnConnected: Triggered when a connection to the remote app has been successfully established.</span></span>
```cpp
m_onConnectedEventToken = m_playerContext.OnConnected([]() 
{
    // Handle connection successfully established
});
```
2) <span data-ttu-id="1d57a-162">Disconnected: attivato se una connessione stabilita viene terminata o non è stato possibile stabilire una connessione.</span><span class="sxs-lookup"><span data-stu-id="1d57a-162">OnDisconnected: Triggered if an established connection is terminated or a connection could not be established.</span></span>
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
><span data-ttu-id="1d57a-163">I valori ```ConnectionFailureReason``` possibili sono documentati nel [file](#idl)di ```Microsoft.Holographic.AppRemoting.idl```.</span><span class="sxs-lookup"><span data-stu-id="1d57a-163">Possible ```ConnectionFailureReason``` values are documented in the ```Microsoft.Holographic.AppRemoting.idl``` [file](#idl).</span></span>

3) <span data-ttu-id="1d57a-164">Onlistening: durante l'ascolto delle connessioni in ingresso viene avviato.</span><span class="sxs-lookup"><span data-stu-id="1d57a-164">OnListening: When listening for incoming connections starts.</span></span>
```cpp
m_onListeningEventToken = m_playerContext.OnListening([]()
{
    // Handle start listening for incoming connections
});
```

<span data-ttu-id="1d57a-165">Inoltre, è possibile eseguire query sullo stato della connessione utilizzando la proprietà ```ConnectionState``` nel contesto del lettore.</span><span class="sxs-lookup"><span data-stu-id="1d57a-165">Additionally the connection state can be queried using the ```ConnectionState``` property on the player context.</span></span>
```cpp
winrt::Microsoft::Holographic::AppRemoting::ConnectionState state = m_playerContext.ConnectionState();
```

## <a name="display-the-remotely-rendered-frame"></a><span data-ttu-id="1d57a-166">Visualizzare il frame sottoposto a rendering remoto</span><span class="sxs-lookup"><span data-stu-id="1d57a-166">Display the remotely rendered frame</span></span>

<span data-ttu-id="1d57a-167">Per visualizzare il contenuto di cui è stato eseguito il rendering in remoto, chiamare ```PlayerContext::BlitRemoteFrame``` durante il rendering di un [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe).</span><span class="sxs-lookup"><span data-stu-id="1d57a-167">To display the remotely rendered content, call ```PlayerContext::BlitRemoteFrame``` while rendering a [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe).</span></span> 

<span data-ttu-id="1d57a-168">```BlitRemoteFrame``` richiede che il buffer nascosto per la HolographicFrame corrente sia associato come destinazione di rendering.</span><span class="sxs-lookup"><span data-stu-id="1d57a-168">```BlitRemoteFrame``` requires that the back buffer for the current HolographicFrame is bound as render target.</span></span> <span data-ttu-id="1d57a-169">Il buffer nascosto può essere ricevuto da [HolographicCameraRenderingParameters](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) tramite la proprietà [Direct3D11BackBuffer](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer) .</span><span class="sxs-lookup"><span data-stu-id="1d57a-169">The back buffer can be received from the [HolographicCameraRenderingParameters](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) via the [Direct3D11BackBuffer](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer) property.</span></span>

<span data-ttu-id="1d57a-170">Quando viene chiamato, ```BlitRemoteFrame``` copia il frame ricevuto più recente dall'applicazione remota nel buffer di HolographicFrame.</span><span class="sxs-lookup"><span data-stu-id="1d57a-170">When called, ```BlitRemoteFrame``` copies the latest received frame from the remote application into the BackBuffer of the HolographicFrame.</span></span> <span data-ttu-id="1d57a-171">Inoltre, il set di punti di interesse è impostato, se l'applicazione remota ha specificato un punto di attivazione durante il rendering del frame remoto.</span><span class="sxs-lookup"><span data-stu-id="1d57a-171">Additionally the focus point set is set, if the remote application has specified a focus point during the rendering of the remote frame.</span></span>

```cpp
// Blit the remote frame into the backbuffer for the HolographicFrame.
winrt::Microsoft::Holographic::AppRemoting::BlitResult result = m_playerContext.BlitRemoteFrame();
```

>[!NOTE]
><span data-ttu-id="1d57a-172">```PlayerContext::BlitRemoteFrame``` potenzialmente sovrascrive il punto di messa a fuoco per il frame corrente.</span><span class="sxs-lookup"><span data-stu-id="1d57a-172">```PlayerContext::BlitRemoteFrame``` potentially overwrites the focus point for the current frame.</span></span> 
>- <span data-ttu-id="1d57a-173">Per specificare un punto di attivazione di fallback, chiamare [HolographicCameraRenderingParameters:: SetFocusPoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) prima di ```PlayerContext::BlitRemoteFrame```.</span><span class="sxs-lookup"><span data-stu-id="1d57a-173">To specify a fallback focus point, call [HolographicCameraRenderingParameters::SetFocusPoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) before ```PlayerContext::BlitRemoteFrame```.</span></span> 
>- <span data-ttu-id="1d57a-174">Per sovrascrivere il punto di attivazione remota, chiamare [HolographicCameraRenderingParameters:: SetFocusPoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) dopo ```PlayerContext::BlitRemoteFrame```.</span><span class="sxs-lookup"><span data-stu-id="1d57a-174">To overwrite the remote focus point, call [HolographicCameraRenderingParameters::SetFocusPoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)  after ```PlayerContext::BlitRemoteFrame```.</span></span>

<span data-ttu-id="1d57a-175">In seguito all'esito positivo, ```BlitRemoteFrame``` restituisce ```BlitResult::Success_Color```.</span><span class="sxs-lookup"><span data-stu-id="1d57a-175">On success, ```BlitRemoteFrame``` returns ```BlitResult::Success_Color```.</span></span> <span data-ttu-id="1d57a-176">In caso contrario, restituisce il motivo dell'errore:</span><span class="sxs-lookup"><span data-stu-id="1d57a-176">Otherwise it returns the failure reason:</span></span>
- <span data-ttu-id="1d57a-177">```BlitResult::Failed_NoRemoteFrameAvailable```: operazione non riuscita perché non è disponibile un frame remoto.</span><span class="sxs-lookup"><span data-stu-id="1d57a-177">```BlitResult::Failed_NoRemoteFrameAvailable```: Failed because no remote frame is available.</span></span>
- <span data-ttu-id="1d57a-178">```BlitResult::Failed_NoCamera```: operazione non riuscita perché non è presente alcuna fotocamera.</span><span class="sxs-lookup"><span data-stu-id="1d57a-178">```BlitResult::Failed_NoCamera```: Failed because no camera present.</span></span>
- <span data-ttu-id="1d57a-179">```BlitResult::Failed_RemoteFrameTooOld```: operazione non riuscita perché il frame remoto è troppo vecchio (vedere la proprietà PlayerContext:: BlitRemoteFrameTimeout).</span><span class="sxs-lookup"><span data-stu-id="1d57a-179">```BlitResult::Failed_RemoteFrameTooOld```: Failed because remote frame is too old (see PlayerContext::BlitRemoteFrameTimeout property).</span></span>

>[!IMPORTANT]
> <span data-ttu-id="1d57a-180">A partire dalla versione [2.1.0](holographic-remoting-version-history.md#v2.1.0) è possibile usare un lettore personalizzato per usare la riproiezione di profondità tramite la comunicazione remota olografica.</span><span class="sxs-lookup"><span data-stu-id="1d57a-180">Starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0) it is possible with a custom player to use depth reprojection via Holographic Remoting.</span></span>

<span data-ttu-id="1d57a-181">```BlitResult``` inoltre può restituire ```BlitResult::Success_Color_Depth``` nelle condizioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="1d57a-181">```BlitResult``` can also return ```BlitResult::Success_Color_Depth``` under the following conditions:</span></span>

- <span data-ttu-id="1d57a-182">L'app remota ha eseguito il commit di un buffer di profondità tramite [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span><span class="sxs-lookup"><span data-stu-id="1d57a-182">The remote app has committed a depth buffer via [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span></span>
- <span data-ttu-id="1d57a-183">L'App Player personalizzata ha associato un buffer di profondità valido prima di chiamare ```BlitRemoteFrame```.</span><span class="sxs-lookup"><span data-stu-id="1d57a-183">The custom player app has bound a valid depth buffer before calling ```BlitRemoteFrame```.</span></span>

<span data-ttu-id="1d57a-184">Se queste condizioni vengono soddisfatte ```BlitRemoteFrame``` blit la profondità remota nel buffer di profondità locale attualmente associato.</span><span class="sxs-lookup"><span data-stu-id="1d57a-184">If these conditions are met ```BlitRemoteFrame``` will blit the remote depth into the currently bound local depth buffer.</span></span> <span data-ttu-id="1d57a-185">È quindi possibile eseguire il rendering di contenuto locale aggiuntivo che avrà un'intersezione di profondità con il contenuto di cui è stato eseguito il rendering remoto.</span><span class="sxs-lookup"><span data-stu-id="1d57a-185">You can then render additional local content which will have depth intersection with the remote rendered content.</span></span> <span data-ttu-id="1d57a-186">Inoltre, è possibile eseguire il commit del buffer di profondità locale tramite [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) nel lettore personalizzato per ottenere una riproiezione della profondità per il contenuto remoto e locale di cui è stato eseguito il rendering.</span><span class="sxs-lookup"><span data-stu-id="1d57a-186">Additionally you can commit the local depth buffer via [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) in your custom player to have depth reprojection for remote and local rendered content.</span></span> <span data-ttu-id="1d57a-187">Per informazioni dettagliate, vedere [riproiezione approfondita](hologram-stability.md#reprojection) .</span><span class="sxs-lookup"><span data-stu-id="1d57a-187">See [Depth Reprojection](hologram-stability.md#reprojection) for details.</span></span>

### <a name="projection-transform-mode"></a><span data-ttu-id="1d57a-188">Modalità di trasformazione proiezione</span><span class="sxs-lookup"><span data-stu-id="1d57a-188">Projection Transform Mode</span></span>

<span data-ttu-id="1d57a-189">Un problema che si verifica quando si usa la riproiezione di profondità tramite la comunicazione remota olografica è che è possibile eseguire il rendering del contenuto remoto con una trasformazione di proiezione diversa rispetto al contenuto locale di cui è stato eseguito il rendering direttamente dall'App Player personalizzata.</span><span class="sxs-lookup"><span data-stu-id="1d57a-189">One problem which surfaces when using depth reprojection via Holographic Remoting is that the remote content can be rendered with a different projection transform than local content directly rendered by your custom player app.</span></span> <span data-ttu-id="1d57a-190">Un caso d'uso comune è quello di specificare valori diversi per il piano near e lontano (tramite [HolographicCamera:: SetNearPlaneDistance](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.setnearplanedistance) e [HolographicCamera:: SetFarPlaneDistance](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.setfarplanedistance)) sul lato Player e sul lato remoto.</span><span class="sxs-lookup"><span data-stu-id="1d57a-190">A common use-case is to specify different values for near and far plane (via [HolographicCamera::SetNearPlaneDistance](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.setnearplanedistance) and [HolographicCamera::SetFarPlaneDistance](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.setfarplanedistance)) on the player side and the remote side.</span></span> <span data-ttu-id="1d57a-191">In questo caso non è chiaro se la trasformazione della proiezione sul lato Player deve riflettere le distanze del piano remoto vicino/lontano o quelle locali.</span><span class="sxs-lookup"><span data-stu-id="1d57a-191">In this case it's not clear if the projection transform on the player side should reflect the remote near/far plane distances or the local ones.</span></span>

<span data-ttu-id="1d57a-192">A partire dalla versione [2.1.0](holographic-remoting-version-history.md#v2.1.0) è possibile controllare la modalità di trasformazione della proiezione tramite ```PlayerContext::ProjectionTransformConfig```.</span><span class="sxs-lookup"><span data-stu-id="1d57a-192">Starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0) you can control the projection transform mode via ```PlayerContext::ProjectionTransformConfig```.</span></span> <span data-ttu-id="1d57a-193">I valori supportati sono:</span><span class="sxs-lookup"><span data-stu-id="1d57a-193">Supported values are:</span></span>

- <span data-ttu-id="1d57a-194">```Local``` - [HolographicCameraPose::P rojectiontransform](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.projectiontransform) restituisce una trasformazione di proiezione che riflette le distanze del piano vicino/lontano impostate dall'app per giocatori personalizzata nel HolographicCamera.</span><span class="sxs-lookup"><span data-stu-id="1d57a-194">```Local``` - [HolographicCameraPose::ProjectionTransform](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.projectiontransform) returns a projection transform which reflects the near/far plane distances set by your custom player app on the HolographicCamera.</span></span>
- <span data-ttu-id="1d57a-195">la trasformazione ```Remote```-Projection riflette le distanze del piano vicino/lontano specificate dall'app remota.</span><span class="sxs-lookup"><span data-stu-id="1d57a-195">```Remote``` - Projection transform reflects the near/far plane distances specified by the remote app.</span></span>
- <span data-ttu-id="1d57a-196">```Merged``` le distanze del piano vicino/estremo dall'app remota e l'app per giocatori personalizzata vengono unite.</span><span class="sxs-lookup"><span data-stu-id="1d57a-196">```Merged``` - Near/Far plane distances from your remote app and your custom player app are merged.</span></span> <span data-ttu-id="1d57a-197">Per impostazione predefinita, questa operazione viene eseguita impostando il valore minimo delle distanze vicino al piano e il valore massimo delle distanze del piano lontano.</span><span class="sxs-lookup"><span data-stu-id="1d57a-197">By default this is done by taking the minimum of the near plane distances and the maximum of the far plane distances.</span></span> <span data-ttu-id="1d57a-198">Nel caso in cui il lato remoto o locale sia invertito, ad esempio lontano < vicino, le distanze del piano remoto vicino/lontano vengono capovolte.</span><span class="sxs-lookup"><span data-stu-id="1d57a-198">In case either the remote or local side are inverted, say far < near, the remote near/far plane distances are flipped.</span></span>

## <span data-ttu-id="1d57a-199">Facoltativo: set BlitRemoteFrameTimeout<a name="BlitRemoteFrameTimeout"></a></span><span class="sxs-lookup"><span data-stu-id="1d57a-199">Optional: Set BlitRemoteFrameTimeout <a name="BlitRemoteFrameTimeout"></a></span></span>
>[!IMPORTANT]
> <span data-ttu-id="1d57a-200">```PlayerContext::BlitRemoteFrameTimeout``` è supportato a partire dalla versione [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span><span class="sxs-lookup"><span data-stu-id="1d57a-200">```PlayerContext::BlitRemoteFrameTimeout``` is supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 

<span data-ttu-id="1d57a-201">La proprietà ```PlayerContext::BlitRemoteFrameTimeout``` specifica l'intervallo di tempo in cui un frame remoto viene riutilizzato se non viene ricevuto alcun nuovo frame remoto.</span><span class="sxs-lookup"><span data-stu-id="1d57a-201">The ```PlayerContext::BlitRemoteFrameTimeout``` property specifies the amount of time a remote frame is reused if no new remote frame is received.</span></span> 

<span data-ttu-id="1d57a-202">Un caso d'uso comune è quello di abilitare il timeout BlitRemoteFrame per visualizzare una schermata vuota se non vengono ricevuti nuovi frame per un determinato periodo di tempo.</span><span class="sxs-lookup"><span data-stu-id="1d57a-202">A common use-case is to enable the BlitRemoteFrame timeout to display a blank screen if no new frames are received for a certain amount of time.</span></span> <span data-ttu-id="1d57a-203">Quando è abilitata, è possibile usare il tipo restituito del metodo ```BlitRemoteFrame``` anche per passare a un contenuto di fallback sottoposto a rendering in locale.</span><span class="sxs-lookup"><span data-stu-id="1d57a-203">When enabled the return type of the ```BlitRemoteFrame``` method can also be used to switch to a locally rendered fallback content.</span></span> 

<span data-ttu-id="1d57a-204">Per abilitare il timeout, impostare il valore della proprietà su una durata uguale o maggiore di 100 ms.</span><span class="sxs-lookup"><span data-stu-id="1d57a-204">To enable the timeout, set the property value to a duration equal or greater than 100ms.</span></span> <span data-ttu-id="1d57a-205">Per disabilitare il timeout, impostare la proprietà su zero Duration.</span><span class="sxs-lookup"><span data-stu-id="1d57a-205">To disable the timeout, set the property to zero duration.</span></span> <span data-ttu-id="1d57a-206">Se il timeout è abilitato e non viene ricevuto un frame remoto per la durata impostata, BlitRemoteFrame avrà esito negativo e restituirà ```Failed_RemoteFrameTooOld``` fino a quando non viene ricevuto un nuovo frame remoto.</span><span class="sxs-lookup"><span data-stu-id="1d57a-206">If the timeout is enabled and no remote frame is received for the set duration, BlitRemoteFrame will fail and return ```Failed_RemoteFrameTooOld``` until a new remote frame is received.</span></span>

```cpp
using namespace std::chrono_literals;

// Set the BlitRemoteFrame timeout to 0.5s
m_playerContext.BlitRemoteFrameTimeout(500ms);
```

## <a name="optional-get-statistics-about-the-last-remote-frame"></a><span data-ttu-id="1d57a-207">Facoltativo: ottenere le statistiche sull'ultimo frame remoto</span><span class="sxs-lookup"><span data-stu-id="1d57a-207">Optional: Get statistics about the last remote frame</span></span>

<span data-ttu-id="1d57a-208">Per diagnosticare problemi di prestazioni o di rete, è possibile recuperare le statistiche sull'ultimo frame remoto tramite la proprietà ```PlayerContext::LastFrameStatistics```.</span><span class="sxs-lookup"><span data-stu-id="1d57a-208">To diagnose performance or network issues, statistics about the last remote frame can be retrieved via the ```PlayerContext::LastFrameStatistics``` property.</span></span> <span data-ttu-id="1d57a-209">Le statistiche vengono aggiornate durante la chiamata a [HolographicFrame::P resentusingcurrentprediction](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction).</span><span class="sxs-lookup"><span data-stu-id="1d57a-209">Statistics are updated during the call to [HolographicFrame::PresentUsingCurrentPrediction](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction).</span></span>

```cpp
// Get statistics for the last presented frame.
winrt::Microsoft::Holographic::AppRemoting::PlayerFrameStatistics statistics = m_playerContext.LastFrameStatistics();
```

<span data-ttu-id="1d57a-210">Per ulteriori informazioni, vedere la documentazione ```PlayerFrameStatistics``` nel [file](#idl)di ```Microsoft.Holographic.AppRemoting.idl```.</span><span class="sxs-lookup"><span data-stu-id="1d57a-210">For more details, see the ```PlayerFrameStatistics``` documentation in the ```Microsoft.Holographic.AppRemoting.idl``` [file](#idl).</span></span>

## <a name="optional-custom-data-channels"></a><span data-ttu-id="1d57a-211">Facoltativo: canali di dati personalizzati</span><span class="sxs-lookup"><span data-stu-id="1d57a-211">Optional: Custom data channels</span></span>

<span data-ttu-id="1d57a-212">I canali di dati personalizzati possono essere utilizzati per inviare dati utente tramite la connessione remota già stabilita.</span><span class="sxs-lookup"><span data-stu-id="1d57a-212">Custom data channels can be used to send user data over the already established remoting connection.</span></span> <span data-ttu-id="1d57a-213">Per ulteriori informazioni, vedere [canali di dati personalizzati](holographic-remoting-custom-data-channels.md) .</span><span class="sxs-lookup"><span data-stu-id="1d57a-213">See [custom data channels](holographic-remoting-custom-data-channels.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="1d57a-214">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1d57a-214">See Also</span></span>
* [<span data-ttu-id="1d57a-215">Scrittura di un'app remota olografica remota</span><span class="sxs-lookup"><span data-stu-id="1d57a-215">Writing a Holographic Remoting remote app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="1d57a-216">Canali di dati di Holographic Remoting personalizzati</span><span class="sxs-lookup"><span data-stu-id="1d57a-216">Custom Holographic Remoting data channels</span></span>](holographic-remoting-custom-data-channels.md)
* [<span data-ttu-id="1d57a-217">Stabilire una connessione sicura con la comunicazione remota olografica</span><span class="sxs-lookup"><span data-stu-id="1d57a-217">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="1d57a-218">Limitazioni e risoluzione dei problemi di comunicazione remota olografica</span><span class="sxs-lookup"><span data-stu-id="1d57a-218">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="1d57a-219">Condizioni di licenza software per Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="1d57a-219">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="1d57a-220">Informativa sulla privacy Microsoft</span><span class="sxs-lookup"><span data-stu-id="1d57a-220">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)

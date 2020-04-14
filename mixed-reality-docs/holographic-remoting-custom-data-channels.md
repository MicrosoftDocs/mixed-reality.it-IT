---
title: Canali di dati di comunicazione remota olografica personalizzati
description: I canali di dati personalizzati possono essere usati per inviare dati utente tramite la connessione remota olografica già stabilita.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens, comunicazione remota, comunicazione remota olografica
ms.openlocfilehash: 12fa47b6b3a46521a9e6029cab61fa1c628c06e9
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278099"
---
# <a name="custom-holographic-remoting-data-channels"></a><span data-ttu-id="a2fed-104">Canali di dati di comunicazione remota olografica personalizzati</span><span class="sxs-lookup"><span data-stu-id="a2fed-104">Custom Holographic Remoting data channels</span></span>

>[!NOTE]
><span data-ttu-id="a2fed-105">Queste linee guida sono specifiche per la comunicazione remota olografica in HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="a2fed-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

<span data-ttu-id="a2fed-106">Utilizzare canali di dati personalizzati per inviare dati personalizzati tramite una connessione remota consolidata.</span><span class="sxs-lookup"><span data-stu-id="a2fed-106">Use custom data channels to send custom data over an established remoting connection.</span></span>

>[!IMPORTANT]
><span data-ttu-id="a2fed-107">I canali di dati personalizzati richiedono un'app remota personalizzata e un'app per lettore personalizzata, perché consente la comunicazione tra le due app personalizzate.</span><span class="sxs-lookup"><span data-stu-id="a2fed-107">Custom data channels require a custom remote app and a custom player app, as it allows for communication between the two custom apps.</span></span>

>[!TIP]
><span data-ttu-id="a2fed-108">È possibile trovare un semplice esempio di ping-pong negli esempi remote e Player all'interno del [repository GitHub degli esempi di comunicazione remota olografica](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span><span class="sxs-lookup"><span data-stu-id="a2fed-108">A simple ping-pong example can be found in the remote and player samples inside the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span> <span data-ttu-id="a2fed-109">Rimuovere il commento ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` all'interno dei file SampleRemoteMain. h/SamplePlayerMain. h per abilitare il codice di esempio.</span><span class="sxs-lookup"><span data-stu-id="a2fed-109">Uncomment ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` inside the SampleRemoteMain.h / SamplePlayerMain.h files to enable the sample code.</span></span>


## <a name="create-a-custom-data-channel"></a><span data-ttu-id="a2fed-110">Creare un canale di dati personalizzato</span><span class="sxs-lookup"><span data-stu-id="a2fed-110">Create a custom data channel</span></span>


<span data-ttu-id="a2fed-111">Per creare un canale di dati personalizzato, sono necessari i campi seguenti:</span><span class="sxs-lookup"><span data-stu-id="a2fed-111">To create a custom data channel, the following fields are required:</span></span>
```cpp
std::recursive_mutex m_customDataChannelLock;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel m_customDataChannel = nullptr;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnDataReceived_revoker m_customChannelDataReceivedEventRevoker;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnClosed_revoker m_customChannelClosedEventRevoker;
```

<span data-ttu-id="a2fed-112">Dopo che una connessione è stata stabilita correttamente, la creazione di nuovi canali di dati può essere avviata dal lato remoto e/o dal lettore.</span><span class="sxs-lookup"><span data-stu-id="a2fed-112">After a connection was successfully established, the creation of new data channels can be initiated from either the remote side and/or the player side.</span></span> <span data-ttu-id="a2fed-113">Sia RemoteContext che PlayerContext forniscono un metodo ```CreateDataChannel()``` a tale scopo.</span><span class="sxs-lookup"><span data-stu-id="a2fed-113">Both the RemoteContext and the PlayerContext provide a ```CreateDataChannel()``` method to do this.</span></span> <span data-ttu-id="a2fed-114">Il primo parametro è l'ID del canale utilizzato per identificare il canale dati nelle operazioni successive.</span><span class="sxs-lookup"><span data-stu-id="a2fed-114">The first parameter is the channel ID which is used to identify the data channel in subsequent operations.</span></span> <span data-ttu-id="a2fed-115">Il secondo parametro è la priorità che specifica la priorità con cui i dati di questo canale vengono trasferiti sull'altro lato.</span><span class="sxs-lookup"><span data-stu-id="a2fed-115">The second parameter is the priority which specifies the priority with which data of this channel is transferred to the other side.</span></span> <span data-ttu-id="a2fed-116">L'intervallo valido per gli ID del canale è 0 fino a e compreso 63 per il lato remoto e 64 fino a 127 per il lato Player.</span><span class="sxs-lookup"><span data-stu-id="a2fed-116">The valid range for channel IDs is 0 up to and including 63 for the remote side and 64 up to and including 127 for the player side.</span></span> <span data-ttu-id="a2fed-117">Le priorità valide sono ```Low```, ```Medium``` o ```High``` (su entrambi i lati).</span><span class="sxs-lookup"><span data-stu-id="a2fed-117">Valid priorities are ```Low```, ```Medium``` or ```High``` (on both sides).</span></span>

<span data-ttu-id="a2fed-118">Per avviare la creazione di un canale dati sul lato **remoto** :</span><span class="sxs-lookup"><span data-stu-id="a2fed-118">To initiate the creation of a data channel on the **remote** side:</span></span>
```cpp
// Valid channel ids for channels created on the remote side are 0 up to and including 63
m_remoteContext.CreateDataChannel(0, DataChannelPriority::Low);
```

<span data-ttu-id="a2fed-119">Per avviare la creazione di un canale dati sul lato **Player** :</span><span class="sxs-lookup"><span data-stu-id="a2fed-119">To initiate the creation of a data channel on the **player** side:</span></span>
```cpp
// Valid channel ids for channels created on the player side are 64 up to and including 127
m_playerContext.CreateDataChannel(64, DataChannelPriority::Low);
```

>[!NOTE]
><span data-ttu-id="a2fed-120">Per creare un nuovo canale di dati personalizzato, è necessario che un solo lato, ovvero remoto o lettore, chiami il metodo ```CreateDataChannel```.</span><span class="sxs-lookup"><span data-stu-id="a2fed-120">To create a new custom data channel, only one side (either remote or player) needs to call the ```CreateDataChannel``` method.</span></span>

## <a name="handling-custom-data-channel-events"></a><span data-ttu-id="a2fed-121">Gestione degli eventi del canale dati personalizzati</span><span class="sxs-lookup"><span data-stu-id="a2fed-121">Handling custom data channel events</span></span>

<span data-ttu-id="a2fed-122">Per stabilire un canale di dati personalizzato, è necessario gestire l'evento ```OnDataChannelCreated``` (sia sul lettore che sul lato remoto).</span><span class="sxs-lookup"><span data-stu-id="a2fed-122">To establish a custom data channel, the ```OnDataChannelCreated``` event needs to be handled (on both the player and the remote side).</span></span> <span data-ttu-id="a2fed-123">Viene attivato quando un canale dati utente viene creato da entrambi i lati e fornisce un oggetto ```IDataChannel```, che può essere utilizzato per inviare e ricevere dati su questo canale.</span><span class="sxs-lookup"><span data-stu-id="a2fed-123">It triggers when a user data channel has been created by either side and provides a ```IDataChannel``` object, which can be used to send and receive data over this channel.</span></span>

<span data-ttu-id="a2fed-124">Per registrare un listener nell'evento ```OnDataChannelCreated```:</span><span class="sxs-lookup"><span data-stu-id="a2fed-124">To register a listener on the ```OnDataChannelCreated``` event:</span></span>
```cpp
m_onDataChannelCreatedEventRevoker = m_remoteContext.OnDataChannelCreated(winrt::auto_revoke,
    [this](const IDataChannel& dataChannel, uint8_t channelId)
    {
        std::lock_guard lock(m_customDataChannelLock);
        m_customDataChannel = dataChannel;

        // Register to OnDataReceived and OnClosed event of the data channel here, see below...
    });
```

<span data-ttu-id="a2fed-125">Per ricevere una notifica quando vengono ricevuti i dati, effettuare la registrazione all'evento ```OnDataReceived``` sull'oggetto ```IDataChannel``` fornito dal gestore ```OnDataChannelCreated```.</span><span class="sxs-lookup"><span data-stu-id="a2fed-125">To get notified when data is received, register to the ```OnDataReceived``` event on the ```IDataChannel``` object provided by the ```OnDataChannelCreated``` handler.</span></span> <span data-ttu-id="a2fed-126">Eseguire la registrazione all'evento ```OnClosed``` per ricevere una notifica quando il canale dati è stato chiuso.</span><span class="sxs-lookup"><span data-stu-id="a2fed-126">Register to the ```OnClosed``` event, to get notified when the data channel has been closed.</span></span>

```cpp
m_customChannelDataReceivedEventRevoker = m_customDataChannel.OnDataReceived(winrt::auto_revoke, 
    [this]()
    {
        // React on data received via the custom data channel here.
    });

m_customChannelClosedEventRevoker = m_customDataChannel.OnClosed(winrt::auto_revoke,
    [this]()
    {
        // React on data channel closed here.

        std::lock_guard lock(m_customDataChannelLock);
        if (m_customDataChannel)
        {
            m_customDataChannel = nullptr;
        }
    });
```

## <a name="sending-data"></a><span data-ttu-id="a2fed-127">Invio di dati</span><span class="sxs-lookup"><span data-stu-id="a2fed-127">Sending data</span></span>

<span data-ttu-id="a2fed-128">Per inviare dati su un canale di dati personalizzato, utilizzare il metodo ```IDataChannel::SendData()```.</span><span class="sxs-lookup"><span data-stu-id="a2fed-128">To send data over a custom data channel, use the ```IDataChannel::SendData()``` method.</span></span> <span data-ttu-id="a2fed-129">Il primo parametro è un ```winrt::array_view<const uint8_t>``` ai dati che devono essere inviati.</span><span class="sxs-lookup"><span data-stu-id="a2fed-129">The first parameter is a ```winrt::array_view<const uint8_t>``` to the data that should be send.</span></span> <span data-ttu-id="a2fed-130">Il secondo parametro specifica la posizione in cui i dati devono essere inviati di nuovo, fino a quando l'altro lato non riconosce la ricezione.</span><span class="sxs-lookup"><span data-stu-id="a2fed-130">The second parameter specifies where the data should be resend, until the other side acknowledge the reception.</span></span> 

>[!IMPORTANT]
><span data-ttu-id="a2fed-131">In caso di condizioni di rete non valide, lo stesso pacchetto di dati potrebbe arrivare più di una volta.</span><span class="sxs-lookup"><span data-stu-id="a2fed-131">In case of bad network conditions, the same data packet might arrive more than once.</span></span> <span data-ttu-id="a2fed-132">Il codice ricevente deve essere in grado di gestire questa situazione.</span><span class="sxs-lookup"><span data-stu-id="a2fed-132">The receiving code must be able to handle this situation.</span></span>

```cpp
uint8_t data[] = {1};
m_customDataChannel.SendData(data, true);
```

## <a name="closing-a-custom-data-channel"></a><span data-ttu-id="a2fed-133">Chiusura di un canale di dati personalizzato</span><span class="sxs-lookup"><span data-stu-id="a2fed-133">Closing a custom data channel</span></span>

<span data-ttu-id="a2fed-134">Per chiudere un canale di dati personalizzato, utilizzare il metodo ```IDataChannel::Close()```.</span><span class="sxs-lookup"><span data-stu-id="a2fed-134">To close a custom data channel, use the ```IDataChannel::Close()``` method.</span></span> <span data-ttu-id="a2fed-135">Entrambi i lati riceveranno una notifica tramite l'evento ```OnClosed``` dopo la chiusura del canale dati personalizzato.</span><span class="sxs-lookup"><span data-stu-id="a2fed-135">Both sides will be notified by the ```OnClosed``` event once the custom data channel has been closed.</span></span>

```cpp
m_customDataChannel.Close();
```

## <a name="see-also"></a><span data-ttu-id="a2fed-136">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="a2fed-136">See Also</span></span>
* [<span data-ttu-id="a2fed-137">Scrittura di un'app remota olografica remota</span><span class="sxs-lookup"><span data-stu-id="a2fed-137">Writing a Holographic Remoting remote app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="a2fed-138">Scrittura di un'app lettore di comunicazione remota olografica personalizzata</span><span class="sxs-lookup"><span data-stu-id="a2fed-138">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="a2fed-139">Limitazioni e risoluzione dei problemi di comunicazione remota olografica</span><span class="sxs-lookup"><span data-stu-id="a2fed-139">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="a2fed-140">Condizioni di licenza software per Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="a2fed-140">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="a2fed-141">Informativa sulla privacy Microsoft</span><span class="sxs-lookup"><span data-stu-id="a2fed-141">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)

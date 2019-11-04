---
title: Canali di dati di comunicazione remota olografica personalizzati
description: I canali di dati personalizzati possono essere usati per inviare dati utente tramite la connessione remota olografica già stabilita.
author: NPohl-MSFT
ms.author: nopohl
ms.date: 10/21/2019
ms.topic: article
keywords: HoloLens, comunicazione remota, comunicazione remota olografica
ms.openlocfilehash: a862fa52695c7bfb94b58c6c0b85606a112835da
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434279"
---
# <a name="custom-holographic-remoting-data-channels"></a><span data-ttu-id="41371-104">Canali di dati di comunicazione remota olografica personalizzati</span><span class="sxs-lookup"><span data-stu-id="41371-104">Custom Holographic Remoting data channels</span></span>

>[!NOTE]
><span data-ttu-id="41371-105">Queste linee guida sono specifiche per la comunicazione remota olografica in HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="41371-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

<span data-ttu-id="41371-106">Utilizzare canali di dati personalizzati per inviare dati personalizzati tramite una connessione remota consolidata.</span><span class="sxs-lookup"><span data-stu-id="41371-106">Use custom data channels to send custom data over an established remoting connection.</span></span>

>[!IMPORTANT]
><span data-ttu-id="41371-107">I canali di dati personalizzati richiedono un'app host personalizzata e un'app per lettore personalizzata, perché consente la comunicazione tra le due app personalizzate.</span><span class="sxs-lookup"><span data-stu-id="41371-107">Custom data channels require a custom host app and a custom player app, as it allows for communication between the two custom apps.</span></span>

>[!TIP]
><span data-ttu-id="41371-108">Un esempio di ping-pong semplice è disponibile negli esempi di host e lettore all'interno del [repository GitHub degli esempi di comunicazione remota olografica](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span><span class="sxs-lookup"><span data-stu-id="41371-108">A simple ping-pong example can be found in the host and player samples inside the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span> <span data-ttu-id="41371-109">Rimuovere il commento ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` all'interno dei file SampleHostMain. h/SamplePlayerMain. h per abilitare il codice di esempio.</span><span class="sxs-lookup"><span data-stu-id="41371-109">Uncomment ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` inside the SampleHostMain.h / SamplePlayerMain.h files to enable the sample code.</span></span>


## <a name="create-a-custom-data-channel"></a><span data-ttu-id="41371-110">Creare un canale di dati personalizzato</span><span class="sxs-lookup"><span data-stu-id="41371-110">Create a custom data channel</span></span>


<span data-ttu-id="41371-111">Per creare un canale di dati personalizzato, sono necessari i campi seguenti:</span><span class="sxs-lookup"><span data-stu-id="41371-111">To create a custom data channel, the following fields are required:</span></span>
```cpp
std::recursive_mutex m_customDataChannelLock;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel m_customDataChannel = nullptr;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnDataReceived_revoker m_customChannelDataReceivedEventRevoker;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnClosed_revoker m_customChannelClosedEventRevoker;
```

<span data-ttu-id="41371-112">Una volta stabilita una connessione, è possibile avviare la creazione di nuovi canali di dati dal lato host e/o dal lato Player.</span><span class="sxs-lookup"><span data-stu-id="41371-112">After a connection was successfully established, the creation of new data channels can be initiated from either the host side and/or the player side.</span></span> <span data-ttu-id="41371-113">Sia RemoteContext che PlayerContext forniscono un metodo ```CreateDataChannel()``` a tale scopo.</span><span class="sxs-lookup"><span data-stu-id="41371-113">Both the RemoteContext and the PlayerContext provide a ```CreateDataChannel()``` method to do this.</span></span> <span data-ttu-id="41371-114">Il primo parametro è l'ID del canale utilizzato per identificare il canale dati nelle operazioni susequent.</span><span class="sxs-lookup"><span data-stu-id="41371-114">The first parameter is the channel ID which is used to identify the data channel in susequent operations.</span></span> <span data-ttu-id="41371-115">Il secondo parametro è la priorità che specifica la priorità con cui i dati di questo canale vengono trasferiti sull'altro lato.</span><span class="sxs-lookup"><span data-stu-id="41371-115">The second paramter is the priority which specifies the priority with which data of this channel is transfered to the other side.</span></span> <span data-ttu-id="41371-116">L'intervallo valido per gli ID del canale è 0 fino a e compreso 63 per il lato host e 64 fino a 127, incluso il lato Player.</span><span class="sxs-lookup"><span data-stu-id="41371-116">The valid range for channel IDs is 0 up to and including 63 for the host side and 64 up to and including 127 for the player side.</span></span> <span data-ttu-id="41371-117">Le priorità valide sono ```Low```, ```Medium``` o ```High``` (su entrambi i lati).</span><span class="sxs-lookup"><span data-stu-id="41371-117">Valid priorities are ```Low```, ```Medium``` or ```High``` (on both sides).</span></span>

<span data-ttu-id="41371-118">Per avviare la creazione di un canale dati sul lato **host** :</span><span class="sxs-lookup"><span data-stu-id="41371-118">To initiate the creation of a data channel on the **host** side:</span></span>
```cpp
// Valid channel ids for channels created on the host side are 0 up to and including 63
m_remoteContext.CreateDataChannel(0, DataChannelPriority::Low);
```

<span data-ttu-id="41371-119">Per avviare la creazione di un canale dati sul lato **Player** :</span><span class="sxs-lookup"><span data-stu-id="41371-119">To initiate the creation of a data channel on the **player** side:</span></span>
```cpp
// Valid channel ids for channels created on the player side are 64 up to and including 127
m_playerContext.CreateDataChannel(64, DataChannelPriority::Low);
```

>[!NOTE]
><span data-ttu-id="41371-120">Per creare un nuovo canale dati personalizzato, solo uno dei due lati (host o Player) deve chiamare il metodo ```CreateDataChannel```.</span><span class="sxs-lookup"><span data-stu-id="41371-120">To create a new custom data channel, only one side (either host or player) needs to call the ```CreateDataChannel``` method.</span></span>

## <a name="handling-custom-data-channel-events"></a><span data-ttu-id="41371-121">Gestione degli eventi del canale dati personalizzati</span><span class="sxs-lookup"><span data-stu-id="41371-121">Handling custom data channel events</span></span>

<span data-ttu-id="41371-122">Per stabilire un canale di dati personalizzato, è necessario gestire l'evento ```OnDataChannelCreated``` (sia sul lettore che sul lato host).</span><span class="sxs-lookup"><span data-stu-id="41371-122">To establish a custom data channel, the ```OnDataChannelCreated``` event needs to be handled (on both the player and the host side).</span></span> <span data-ttu-id="41371-123">Viene attivato quando un canale dati utente viene creato da entrambi i lati e fornisce un oggetto ```IDataChannel```, che può essere utilizzato per inviare e ricevere dati su questo canale.</span><span class="sxs-lookup"><span data-stu-id="41371-123">It triggers when a user data channel has been created by either side and provides a ```IDataChannel``` object, which can be used to send and receive data over this channel.</span></span>

<span data-ttu-id="41371-124">Per registrare un listener nell'evento ```OnDataChannelCreated```:</span><span class="sxs-lookup"><span data-stu-id="41371-124">To register a listener on the ```OnDataChannelCreated``` event:</span></span>
```cpp
m_onDataChannelCreatedEventRevoker = m_remoteContext.OnDataChannelCreated(winrt::auto_revoke,
    [this](const IDataChannel& dataChannel, uint8_t channelId)
    {
        std::lock_guard lock(m_customDataChannelLock);
        m_customDataChannel = dataChannel;

        // Register to OnDataReceived and OnClosed event of the data channel here, see below...
    });
```

<span data-ttu-id="41371-125">Per ricevere una notifica quando vengono ricevuti i dati, effettuare la registrazione all'evento ```OnDataReceived``` sull'oggetto ```IDataChannel``` fornito dal gestore ```OnDataChannelCreated```.</span><span class="sxs-lookup"><span data-stu-id="41371-125">To get notified when data is received, register to the ```OnDataReceived``` event on the ```IDataChannel``` object provided by the ```OnDataChannelCreated``` handler.</span></span> <span data-ttu-id="41371-126">Eseguire la registrazione all'evento ```OnClosed``` per ricevere una notifica quando il canale dati è stato chiuso.</span><span class="sxs-lookup"><span data-stu-id="41371-126">Register to the ```OnClosed``` event, to get notified when the data channel has been closed.</span></span>

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

## <a name="sending-data"></a><span data-ttu-id="41371-127">Invio di dati</span><span class="sxs-lookup"><span data-stu-id="41371-127">Sending data</span></span>

<span data-ttu-id="41371-128">Per inviare dati su un canale di dati personalizzato, utilizzare il metodo ```IDataChannel::SendData()```.</span><span class="sxs-lookup"><span data-stu-id="41371-128">To send data over a custom data channel, use the ```IDataChannel::SendData()``` method.</span></span> <span data-ttu-id="41371-129">Il primo parametro è un ```winrt::array_view<const uint8_t>``` ai dati che devono essere inviati.</span><span class="sxs-lookup"><span data-stu-id="41371-129">The first paramter is a ```winrt::array_view<const uint8_t>``` to the data that should be send.</span></span> <span data-ttu-id="41371-130">Il secondo parametro specifica wheter. i dati devono essere inviati di nuovo, fino a quando l'altro lato non riconosce la ricezione.</span><span class="sxs-lookup"><span data-stu-id="41371-130">The second parameter specifies wheter the data should be resend, until the other side acknowledge the reception.</span></span> 

>[!IMPORTANT]
><span data-ttu-id="41371-131">In caso di condizioni di rete non valide, lo stesso pacchetto di dati potrebbe arrivare più di una volta.</span><span class="sxs-lookup"><span data-stu-id="41371-131">In case of bad network conditions, the same data packet might arrive more than once.</span></span> <span data-ttu-id="41371-132">Il codice ricevente deve essere in grado di gestire questa situazione.</span><span class="sxs-lookup"><span data-stu-id="41371-132">The receiving code must be able to handle this situation.</span></span>

```cpp
uint8_t data[] = {1};
m_customDataChannel.SendData(data, true);
```

## <a name="closing-a-custom-data-channel"></a><span data-ttu-id="41371-133">Chiusura di un canale di dati personalizzato</span><span class="sxs-lookup"><span data-stu-id="41371-133">Closing a custom data channel</span></span>

<span data-ttu-id="41371-134">Per chiudere un canale di dati personalizzato, utilizzare il metodo ```IDataChannel::Close()```.</span><span class="sxs-lookup"><span data-stu-id="41371-134">To close a custom data channel, use the ```IDataChannel::Close()``` method.</span></span> <span data-ttu-id="41371-135">Entrambi i lati riceveranno una notifica tramite l'evento ```OnClosed``` dopo la chiusura del canale dati personalizzato.</span><span class="sxs-lookup"><span data-stu-id="41371-135">Both sides will be notified by the ```OnClosed``` event once the custom data channel has been closed.</span></span>

```cpp
m_customDataChannel.Close();
```

## <a name="see-also"></a><span data-ttu-id="41371-136">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="41371-136">See Also</span></span>
* [<span data-ttu-id="41371-137">Scrittura di un'app host di comunicazione remota olografica</span><span class="sxs-lookup"><span data-stu-id="41371-137">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="41371-138">Scrittura di un'app lettore di comunicazione remota olografica personalizzata</span><span class="sxs-lookup"><span data-stu-id="41371-138">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="41371-139">Limitazioni e risoluzione dei problemi di comunicazione remota olografica</span><span class="sxs-lookup"><span data-stu-id="41371-139">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="41371-140">Condizioni di licenza software per Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="41371-140">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="41371-141">Informativa sulla privacy Microsoft</span><span class="sxs-lookup"><span data-stu-id="41371-141">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)

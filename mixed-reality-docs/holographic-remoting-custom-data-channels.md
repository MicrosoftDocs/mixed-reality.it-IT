---
title: Canali di dati di comunicazione remota olografica personalizzati
description: I canali di dati personalizzati possono essere usati per inviare dati utente tramite la connessione remota olografica già stabilita.
author: NPohl-MSFT
ms.author: nopohl
ms.date: 08/01/2019
ms.topic: article
keywords: HoloLens, comunicazione remota, comunicazione remota olografica
ms.openlocfilehash: 9f7f20023d496412b331606e03d0c5110bb4864f
ms.sourcegitcommit: ca949efe0279995a376750d89e23d7123eb44846
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/01/2019
ms.locfileid: "68718085"
---
# <a name="custom-holographic-remoting-data-channels"></a>Canali di dati di comunicazione remota olografica personalizzati

>[!NOTE]
>Queste linee guida sono specifiche per la comunicazione remota olografica in HoloLens 2.

Utilizzare canali di dati personalizzati per inviare dati personalizzati tramite una connessione remota consolidata.

>[!IMPORTANT]
>I canali di dati personalizzati richiedono un'app host personalizzata e un'app per lettore personalizzata, perché consente la comunicazione tra le due app personalizzate.

>[!TIP]
>Un esempio di ping-pong semplice è disponibile negli esempi di host e lettore all'interno del [repository GitHub degli esempi di comunicazione remota olografica](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples). Rimuovere il ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` commento dai file SampleHostMain. h/SamplePlayerMain. h per abilitare il codice di esempio.


# <a name="create-a-custom-data-channel"></a>Creare un canale di dati personalizzato


Per creare un canale di dati personalizzato, sono necessari i campi seguenti:
```cpp
std::recursive_mutex m_customDataChannelLock;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel m_customDataChannel = nullptr;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnDataReceived_revoker m_customChannelDataReceivedEventRevoker;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnClosed_revoker m_customChannelClosedEventRevoker;
```

Una volta stabilita una connessione, è possibile avviare la creazione di nuovi canali di dati dal lato host e/o dal lato Player. Sia RemoteContext che PlayerContext forniscono un ```CreateDataChannel()``` metodo per eseguire questa operazione. Il primo parametro è l'ID del canale utilizzato per identificare il canale dati nelle operazioni susequent. Il secondo parametro è la priorità che specifica la priorità con cui i dati di questo canale vengono trasferiti sull'altro lato. L'intervallo valido per gli ID del canale è 0 fino a e compreso 63 per il lato host e 64 fino a 127, incluso il lato Player. Le priorità valide ```Low```sono ```Medium``` o ```High``` (su entrambi i lati).

Per avviare la creazione di un canale dati sul lato **host** :
```cpp
// Valid channel ids for channels created on the host side are 0 up to and including 63
m_remoteContext.CreateDataChannel(0, DataChannelPriority::Low);
```

Per avviare la creazione di un canale dati sul lato **Player** :
```cpp
// Valid channel ids for channels created on the player side are 64 up to and including 127
m_playerContext.CreateDataChannel(64, DataChannelPriority::Low);
```

>[!NOTE]
>Per creare un nuovo canale dati personalizzato, è necessario che un solo lato (host o Player) chiami il ```CreateDataChannel``` metodo.

## <a name="handling-custom-data-channel-events"></a>Gestione degli eventi del canale dati personalizzati

Per stabilire un canale di dati personalizzato, ```OnDataChannelCreated``` è necessario gestire l'evento (sia per il lettore che per il lato host). Viene attivato quando un canale dati utente viene creato da entrambi i lati e fornisce un ```IDataChannel``` oggetto che può essere utilizzato per inviare e ricevere dati su questo canale.

Per registrare un listener per l' ```OnDataChannelCreated``` evento:
```cpp
m_onDataChannelCreatedEventRevoker = m_remoteContext.OnDataChannelCreated(winrt::auto_revoke,
    [this](const IDataChannel& dataChannel, uint8_t channelId)
    {
        std::lock_guard lock(m_customDataChannelLock);
        m_customDataChannel = dataChannel;

        // Register to OnDataReceived and OnClosed event of the data channel here, see below...
    });
```

Per ricevere una ```OnDataReceived``` notifica quando vengono ricevuti i dati, effettuare la registrazione all' ```IDataChannel``` evento nell'oggetto fornito ```OnDataChannelCreated``` dal gestore. Eseguire la ```OnClosed``` registrazione all'evento per ricevere una notifica quando il canale dati è stato chiuso.

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

## <a name="sending-data"></a>Invio di dati

Per inviare dati su un canale di dati personalizzato, utilizzare ```IDataChannel::SendData()``` il metodo. Il primo parametro è un ```winrt::array_view<const uint8_t>``` per i dati che devono essere inviati. Il secondo parametro specifica wheter. i dati devono essere inviati di nuovo, fino a quando l'altro lato non riconosce la ricezione. 

>[!IMPORTANT]
>In caso di condizioni di rete non valide, lo stesso pacchetto di dati potrebbe arrivare più di una volta. Il codice ricevente deve essere in grado di gestire questa situazione.

```cpp
uint8_t data[] = {1};
m_customDataChannel.SendData(data, true);
```

## <a name="closing-a-custom-data-channel"></a>Chiusura di un canale di dati personalizzato

Per chiudere un canale di dati personalizzato, utilizzare ```IDataChannel::Close()``` il metodo. Entrambi i lati verranno informati dall' ```OnClosed``` evento dopo la chiusura del canale dati personalizzato.

```cpp
m_customDataChannel.Close();
```

## <a name="see-also"></a>Vedere anche
* [Scrittura di un'app host di comunicazione remota olografica](holographic-remoting-create-host.md)
* [Scrittura di un'app lettore di comunicazione remota olografica personalizzata](holographic-remoting-create-player.md)
* [Limitazioni e risoluzione dei problemi di comunicazione remota olografica](holographic-remoting-troubleshooting.md)
* [Condizioni di licenza software per la comunicazione remota olografica](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Informativa sulla privacy Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
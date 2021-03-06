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
# <a name="custom-holographic-remoting-data-channels"></a>Canali di dati di comunicazione remota olografica personalizzati

>[!NOTE]
>Queste linee guida sono specifiche per la comunicazione remota olografica in HoloLens 2.

Utilizzare canali di dati personalizzati per inviare dati personalizzati tramite una connessione remota consolidata.

>[!IMPORTANT]
>I canali di dati personalizzati richiedono un'app remota personalizzata e un'app per lettore personalizzata, perché consente la comunicazione tra le due app personalizzate.

>[!TIP]
>È possibile trovare un semplice esempio di ping-pong negli esempi remote e Player all'interno del [repository GitHub degli esempi di comunicazione remota olografica](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples). Rimuovere il commento ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` all'interno dei file SampleRemoteMain. h/SamplePlayerMain. h per abilitare il codice di esempio.


## <a name="create-a-custom-data-channel"></a>Creare un canale di dati personalizzato


Per creare un canale di dati personalizzato, sono necessari i campi seguenti:
```cpp
std::recursive_mutex m_customDataChannelLock;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel m_customDataChannel = nullptr;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnDataReceived_revoker m_customChannelDataReceivedEventRevoker;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnClosed_revoker m_customChannelClosedEventRevoker;
```

Dopo che una connessione è stata stabilita correttamente, la creazione di nuovi canali di dati può essere avviata dal lato remoto e/o dal lettore. Sia RemoteContext che PlayerContext forniscono un metodo ```CreateDataChannel()``` a tale scopo. Il primo parametro è l'ID del canale utilizzato per identificare il canale dati nelle operazioni successive. Il secondo parametro è la priorità che specifica la priorità con cui i dati di questo canale vengono trasferiti sull'altro lato. L'intervallo valido per gli ID del canale è 0 fino a e compreso 63 per il lato remoto e 64 fino a 127 per il lato Player. Le priorità valide sono ```Low```, ```Medium``` o ```High``` (su entrambi i lati).

Per avviare la creazione di un canale dati sul lato **remoto** :
```cpp
// Valid channel ids for channels created on the remote side are 0 up to and including 63
m_remoteContext.CreateDataChannel(0, DataChannelPriority::Low);
```

Per avviare la creazione di un canale dati sul lato **Player** :
```cpp
// Valid channel ids for channels created on the player side are 64 up to and including 127
m_playerContext.CreateDataChannel(64, DataChannelPriority::Low);
```

>[!NOTE]
>Per creare un nuovo canale di dati personalizzato, è necessario che un solo lato, ovvero remoto o lettore, chiami il metodo ```CreateDataChannel```.

## <a name="handling-custom-data-channel-events"></a>Gestione degli eventi del canale dati personalizzati

Per stabilire un canale di dati personalizzato, è necessario gestire l'evento ```OnDataChannelCreated``` (sia sul lettore che sul lato remoto). Viene attivato quando un canale dati utente viene creato da entrambi i lati e fornisce un oggetto ```IDataChannel```, che può essere utilizzato per inviare e ricevere dati su questo canale.

Per registrare un listener nell'evento ```OnDataChannelCreated```:
```cpp
m_onDataChannelCreatedEventRevoker = m_remoteContext.OnDataChannelCreated(winrt::auto_revoke,
    [this](const IDataChannel& dataChannel, uint8_t channelId)
    {
        std::lock_guard lock(m_customDataChannelLock);
        m_customDataChannel = dataChannel;

        // Register to OnDataReceived and OnClosed event of the data channel here, see below...
    });
```

Per ricevere una notifica quando vengono ricevuti i dati, effettuare la registrazione all'evento ```OnDataReceived``` sull'oggetto ```IDataChannel``` fornito dal gestore ```OnDataChannelCreated```. Eseguire la registrazione all'evento ```OnClosed``` per ricevere una notifica quando il canale dati è stato chiuso.

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

Per inviare dati su un canale di dati personalizzato, utilizzare il metodo ```IDataChannel::SendData()```. Il primo parametro è un ```winrt::array_view<const uint8_t>``` ai dati che devono essere inviati. Il secondo parametro specifica la posizione in cui i dati devono essere inviati di nuovo, fino a quando l'altro lato non riconosce la ricezione. 

>[!IMPORTANT]
>In caso di condizioni di rete non valide, lo stesso pacchetto di dati potrebbe arrivare più di una volta. Il codice ricevente deve essere in grado di gestire questa situazione.

```cpp
uint8_t data[] = {1};
m_customDataChannel.SendData(data, true);
```

## <a name="closing-a-custom-data-channel"></a>Chiusura di un canale di dati personalizzato

Per chiudere un canale di dati personalizzato, utilizzare il metodo ```IDataChannel::Close()```. Entrambi i lati riceveranno una notifica tramite l'evento ```OnClosed``` dopo la chiusura del canale dati personalizzato.

```cpp
m_customDataChannel.Close();
```

## <a name="see-also"></a>Vedi anche
* [Scrittura di un'app remota olografica remota](holographic-remoting-create-host.md)
* [Scrittura di un'app lettore di comunicazione remota olografica personalizzata](holographic-remoting-create-player.md)
* [Limitazioni e risoluzione dei problemi di comunicazione remota olografica](holographic-remoting-troubleshooting.md)
* [Condizioni di licenza software per Holographic Remoting](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Informativa sulla privacy Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)

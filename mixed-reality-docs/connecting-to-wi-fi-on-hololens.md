---
title: Connessione al Wi-Fi su HoloLens
description: Istruzioni su come connettersi a Internet wireless con HoloLens e come identificare l'indirizzo IP del dispositivo.
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: HoloLens, WiFi, wireless, Internet, IP, indirizzo IP
ms.openlocfilehash: b064514124d861c0734ca51b3878d4a68b592fab
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670119"
---
# <a name="connecting-to-wi-fi-on-hololens"></a>Connessione al Wi-Fi su HoloLens

HoloLens contiene una radio Wi-Fi con supporto 802.11 AC. La connessione di HoloLens a una rete Wi-Fi è simile alla connessione di un dispositivo Windows 10 desktop o mobile a una rete Wi-Fi.

![Impostazioni Wi-Fi HoloLens](images/wifi-hololens-600px.jpg)

## <a name="connecting-to-a-wi-fi-network-on-hololens"></a>Connessione a una rete Wi-Fi su HoloLens

1. [Sbocciare](gestures.md#bloom) sul menu **Start** .
2. Selezionare l'app **Impostazioni** dall'inizio o dall'elenco **tutte le app** a destra del menu Start.
3. L'app **Impostazioni** verrà automaticamente posizionata in primo piano.
4. Selezionare **rete & Internet**.
5. Verifica che il Wi-Fi sia attivato.
6. Selezionare una rete Wi-Fi nell'elenco.
7. Digitare la password della rete Wi-Fi (se necessario).

## <a name="disabling-wi-fi-on-hololens"></a>Disabilitazione di Wi-Fi su HoloLens

### <a name="using-the-settings-app-on-hololens"></a>Uso dell'app Settings in HoloLens

1. [Sbocciare](gestures.md#bloom) sul menu **Start** .
2. Selezionare l'app **Impostazioni** dall'inizio o dall'elenco **tutte le app** a destra del menu Start.
3. L'app **Impostazioni** verrà automaticamente posizionata in primo piano.
4. Selezionare **rete & Internet**.
5. Selezionare il dispositivo di scorrimento Wi-Fi per spostarlo nella posizione "off". Questa operazione Disabilita i componenti RF della radio Wi-Fi e disattiva tutte le funzionalità Wi-Fi in HoloLens. 

    >[!WARNING]
    >HoloLens non sarà in grado di caricare automaticamente gli [spazi](environment-considerations-for-hololens.md#WiFi fingerprint considerations) quando la radio Wi-Fi è disabilitata.
    
6. Spostare il dispositivo di scorrimento nella posizione "on" per attivare la funzionalità radio Wi-Fi e ripristinare la funzionalità Wi-Fi in Microsoft HoloLens. Lo stato di radio Wi-Fi selezionato ("on" di "off") viene mantenuto tra i riavvii.

## <a name="how-to-confirm-you-are-connected-to-a-wi-fi-network"></a>Come verificare di essere connessi a una rete Wi-Fi

1. [Bloom](gestures.md#bloom) per visualizzare il menu **Start** .
2. Esaminare la parte superiore sinistra del menu Start per lo stato Wi-Fi. Verrà visualizzato lo stato di Wi-Fi e SSID della rete connessa.

## <a name="identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network"></a>Identificazione dell'indirizzo IP della HoloLens nella rete Wi-Fi

### <a name="using-the-settings-app"></a>Uso dell'app Settings

1. [Sbocciare](gestures.md#bloom) sul menu **Start** .
2. Selezionare l'app **Impostazioni** dall'inizio o dall'elenco **tutte le app** a destra del menu Start.
3. L'app **Impostazioni** verrà automaticamente posizionata in primo piano.
4. Selezionare **rete & Internet**.
5. Scorrere fino a sotto l'elenco delle reti Wi-Fi disponibili e selezionare **proprietà hardware**.

    ![Proprietà hardware nelle impostazioni Wi-Fi](images/wifi-hololens-hwdetails.jpg)

L'indirizzo IP verrà visualizzato accanto a **indirizzo IPv4**.

### <a name="using-cortana"></a>Uso di Cortana

Pronunciare "*Hey Cortana, qual è il mio indirizzo IP?* " Cortana visualizzerà e leggerà l'indirizzo IP.

### <a name="using-windows-device-portal"></a>Uso del portale per dispositivi Windows

1. Aprire il [portale del dispositivo](using-the-windows-device-portal.md#networking) in un Web browser sul PC.
2. Passare alla sezione **rete** .

Verrà visualizzato l'indirizzo IP e altre informazioni di rete. Questo metodo consente di copiare e incollare facilmente l'indirizzo IP nel PC di sviluppo.

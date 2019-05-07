---
title: La connessione alla rete Wi-Fi in HoloLens
description: Istruzioni su come connettersi a internet senza fili con HoloLens e su come identificare l'indirizzo IP del dispositivo.
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: HoloLens, Wi-Fi, senza fili, internet, ip, indirizzo ip
ms.openlocfilehash: b064514124d861c0734ca51b3878d4a68b592fab
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670119"
---
# <a name="connecting-to-wi-fi-on-hololens"></a>La connessione alla rete Wi-Fi in HoloLens

HoloLens contiene un 802.11ac-in grado di supportare, 2 x 2 radio Wi-Fi. La connessione di HoloLens a una rete Wi-Fi è simile alla connessione di un dispositivo Windows 10 Desktop o per dispositivi mobili a una rete Wi-Fi.

![Impostazioni Wi-Fi HoloLens](images/wifi-hololens-600px.jpg)

## <a name="connecting-to-a-wi-fi-network-on-hololens"></a>La connessione a una rete Wi-Fi in HoloLens

1. [Bloom](gestures.md#bloom) per il **avviare** menu.
2. Selezionare il **le impostazioni** app dall'inizio o dalle **tutte le app** elenco a destra del menu Start.
3. Il **impostazioni** app saranno posizionati automaticamente portata di mano.
4. Selezionare **rete e Internet**.
5. Verifica che il Wi-Fi sia attivato.
6. Selezionare una rete Wi-Fi nell'elenco.
7. Digitare la password di rete Wi-Fi (se necessario).

## <a name="disabling-wi-fi-on-hololens"></a>La disabilitazione di Wi-Fi in HoloLens

### <a name="using-the-settings-app-on-hololens"></a>Usando l'app impostazioni su HoloLens

1. [Bloom](gestures.md#bloom) per il **avviare** menu.
2. Selezionare il **le impostazioni** app dall'inizio o dalle **tutte le app** elenco a destra del menu Start.
3. Il **impostazioni** app saranno posizionati automaticamente portata di mano.
4. Selezionare **rete e Internet**.
5. Selezionare l'opzione di dispositivo di scorrimento Wi-Fi per spostarlo nella posizione "Off". Verrà disattivare i componenti RF della radio Wi-Fi e disabilitare tutte le funzionalità Wi-Fi nei HoloLens. 

    >[!WARNING]
    >HoloLens non sarà in grado di caricare automaticamente il [spazi](environment-considerations-for-hololens.md#WiFi fingerprint considerations) quando l'opzione Wi-Fi è disabilitato.
    
6. Spostare il commutatore di dispositivo di scorrimento in una posizione "On" per attivare l'opzione Wi-Fi e ripristinare la funzionalità Wi-Fi in Microsoft HoloLens. Lo stato di radio Wi-Fi selezionato ("On" di "Off") vengono mantenute tra i riavvii.

## <a name="how-to-confirm-you-are-connected-to-a-wi-fi-network"></a>Come verificare che si è connessi a una rete Wi-Fi

1. [Bloom](gestures.md#bloom) per visualizzare il **avviare** menu.
2. Nella parte superiore sinistra del menu Start per lo stato del Wi-Fi. Verrà visualizzato lo stato del Wi-Fi e l'identificatore SSID di rete connessa.

## <a name="identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network"></a>Che identifica l'indirizzo IP di HoloLens nella rete Wi-Fi

### <a name="using-the-settings-app"></a>Usando l'app impostazioni

1. [Bloom](gestures.md#bloom) per il **avviare** menu.
2. Selezionare il **le impostazioni** app dall'inizio o dalle **tutte le app** elenco a destra del menu Start.
3. Il **impostazioni** app saranno posizionati automaticamente portata di mano.
4. Selezionare **rete e Internet**.
5. Scorrere verso il basso, sotto l'elenco delle reti Wi-Fi disponibili e selezionare **le proprietà Hardware**.

    ![Proprietà hardware nelle impostazioni Wi-Fi](images/wifi-hololens-hwdetails.jpg)

L'indirizzo IP verrà visualizzato accanto a **indirizzo IPv4**.

### <a name="using-cortana"></a>Uso di Cortana

Ad esempio "*Ehi Cortana, qual è l'indirizzo IP?*" e Cortana visualizzerà e leggere l'indirizzo IP.

### <a name="using-windows-device-portal"></a>Utilizzo di Windows Device Portal

1. Aprire il [dispositivo portale](using-the-windows-device-portal.md#networking) in un web browser sul PC.
2. Passare il **Networking** sezione.

Verrà visualizzati l'indirizzo IP e altre informazioni di rete non esiste. Questo metodo consente facile copiare e incollare l'indirizzo IP del computer di sviluppo.

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
# <a name="connecting-to-wi-fi-on-hololens"></a><span data-ttu-id="7d1e8-104">La connessione alla rete Wi-Fi in HoloLens</span><span class="sxs-lookup"><span data-stu-id="7d1e8-104">Connecting to Wi-Fi on HoloLens</span></span>

<span data-ttu-id="7d1e8-105">HoloLens contiene un 802.11ac-in grado di supportare, 2 x 2 radio Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="7d1e8-105">HoloLens contains a 802.11ac-capable, 2x2 Wi-Fi radio.</span></span> <span data-ttu-id="7d1e8-106">La connessione di HoloLens a una rete Wi-Fi è simile alla connessione di un dispositivo Windows 10 Desktop o per dispositivi mobili a una rete Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="7d1e8-106">Connecting HoloLens to a Wi-Fi network is similar to connecting a Windows 10 Desktop or Mobile device to a Wi-Fi network.</span></span>

![Impostazioni Wi-Fi HoloLens](images/wifi-hololens-600px.jpg)

## <a name="connecting-to-a-wi-fi-network-on-hololens"></a><span data-ttu-id="7d1e8-108">La connessione a una rete Wi-Fi in HoloLens</span><span class="sxs-lookup"><span data-stu-id="7d1e8-108">Connecting to a Wi-Fi network on HoloLens</span></span>

1. <span data-ttu-id="7d1e8-109">[Bloom](gestures.md#bloom) per il **avviare** menu.</span><span class="sxs-lookup"><span data-stu-id="7d1e8-109">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="7d1e8-110">Selezionare il **le impostazioni** app dall'inizio o dalle **tutte le app** elenco a destra del menu Start.</span><span class="sxs-lookup"><span data-stu-id="7d1e8-110">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="7d1e8-111">Il **impostazioni** app saranno posizionati automaticamente portata di mano.</span><span class="sxs-lookup"><span data-stu-id="7d1e8-111">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="7d1e8-112">Selezionare **rete e Internet**.</span><span class="sxs-lookup"><span data-stu-id="7d1e8-112">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="7d1e8-113">Verifica che il Wi-Fi sia attivato.</span><span class="sxs-lookup"><span data-stu-id="7d1e8-113">Make sure Wi-Fi is turned on.</span></span>
6. <span data-ttu-id="7d1e8-114">Selezionare una rete Wi-Fi nell'elenco.</span><span class="sxs-lookup"><span data-stu-id="7d1e8-114">Select a Wi-Fi network from the list.</span></span>
7. <span data-ttu-id="7d1e8-115">Digitare la password di rete Wi-Fi (se necessario).</span><span class="sxs-lookup"><span data-stu-id="7d1e8-115">Type in the Wi-Fi network password (if needed).</span></span>

## <a name="disabling-wi-fi-on-hololens"></a><span data-ttu-id="7d1e8-116">La disabilitazione di Wi-Fi in HoloLens</span><span class="sxs-lookup"><span data-stu-id="7d1e8-116">Disabling Wi-Fi on HoloLens</span></span>

### <a name="using-the-settings-app-on-hololens"></a><span data-ttu-id="7d1e8-117">Usando l'app impostazioni su HoloLens</span><span class="sxs-lookup"><span data-stu-id="7d1e8-117">Using the Settings app on HoloLens</span></span>

1. <span data-ttu-id="7d1e8-118">[Bloom](gestures.md#bloom) per il **avviare** menu.</span><span class="sxs-lookup"><span data-stu-id="7d1e8-118">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="7d1e8-119">Selezionare il **le impostazioni** app dall'inizio o dalle **tutte le app** elenco a destra del menu Start.</span><span class="sxs-lookup"><span data-stu-id="7d1e8-119">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="7d1e8-120">Il **impostazioni** app saranno posizionati automaticamente portata di mano.</span><span class="sxs-lookup"><span data-stu-id="7d1e8-120">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="7d1e8-121">Selezionare **rete e Internet**.</span><span class="sxs-lookup"><span data-stu-id="7d1e8-121">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="7d1e8-122">Selezionare l'opzione di dispositivo di scorrimento Wi-Fi per spostarlo nella posizione "Off".</span><span class="sxs-lookup"><span data-stu-id="7d1e8-122">Select the Wi-Fi slider switch to move it to the "Off" position.</span></span> <span data-ttu-id="7d1e8-123">Verrà disattivare i componenti RF della radio Wi-Fi e disabilitare tutte le funzionalità Wi-Fi nei HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7d1e8-123">This will turn off the RF components of the Wi-Fi radio and disable all Wi-Fi functionality on HoloLens.</span></span> 

    >[!WARNING]
    ><span data-ttu-id="7d1e8-124">HoloLens non sarà in grado di caricare automaticamente il [spazi](environment-considerations-for-hololens.md#WiFi fingerprint considerations) quando l'opzione Wi-Fi è disabilitato.</span><span class="sxs-lookup"><span data-stu-id="7d1e8-124">HoloLens will not be able to automatically load your [spaces](environment-considerations-for-hololens.md#WiFi fingerprint considerations) when the Wi-Fi radio is disabled.</span></span>
    
6. <span data-ttu-id="7d1e8-125">Spostare il commutatore di dispositivo di scorrimento in una posizione "On" per attivare l'opzione Wi-Fi e ripristinare la funzionalità Wi-Fi in Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7d1e8-125">Move the slider switch to the "On" position to turn on the Wi-Fi radio and restore Wi-Fi functionality on Microsoft HoloLens.</span></span> <span data-ttu-id="7d1e8-126">Lo stato di radio Wi-Fi selezionato ("On" di "Off") vengono mantenute tra i riavvii.</span><span class="sxs-lookup"><span data-stu-id="7d1e8-126">The selected Wi-Fi radio state ("On" of "Off") will persist across reboots.</span></span>

## <a name="how-to-confirm-you-are-connected-to-a-wi-fi-network"></a><span data-ttu-id="7d1e8-127">Come verificare che si è connessi a una rete Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="7d1e8-127">How to confirm you are connected to a Wi-Fi network</span></span>

1. <span data-ttu-id="7d1e8-128">[Bloom](gestures.md#bloom) per visualizzare il **avviare** menu.</span><span class="sxs-lookup"><span data-stu-id="7d1e8-128">[Bloom](gestures.md#bloom) to bring up the **Start** menu.</span></span>
2. <span data-ttu-id="7d1e8-129">Nella parte superiore sinistra del menu Start per lo stato del Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="7d1e8-129">Look at the top left of the Start menu for Wi-Fi status.</span></span> <span data-ttu-id="7d1e8-130">Verrà visualizzato lo stato del Wi-Fi e l'identificatore SSID di rete connessa.</span><span class="sxs-lookup"><span data-stu-id="7d1e8-130">The state of Wi-Fi and the SSID of the connected network will be shown.</span></span>

## <a name="identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network"></a><span data-ttu-id="7d1e8-131">Che identifica l'indirizzo IP di HoloLens nella rete Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="7d1e8-131">Identifying the IP Address of your HoloLens on the Wi-Fi network</span></span>

### <a name="using-the-settings-app"></a><span data-ttu-id="7d1e8-132">Usando l'app impostazioni</span><span class="sxs-lookup"><span data-stu-id="7d1e8-132">Using the Settings app</span></span>

1. <span data-ttu-id="7d1e8-133">[Bloom](gestures.md#bloom) per il **avviare** menu.</span><span class="sxs-lookup"><span data-stu-id="7d1e8-133">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="7d1e8-134">Selezionare il **le impostazioni** app dall'inizio o dalle **tutte le app** elenco a destra del menu Start.</span><span class="sxs-lookup"><span data-stu-id="7d1e8-134">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="7d1e8-135">Il **impostazioni** app saranno posizionati automaticamente portata di mano.</span><span class="sxs-lookup"><span data-stu-id="7d1e8-135">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="7d1e8-136">Selezionare **rete e Internet**.</span><span class="sxs-lookup"><span data-stu-id="7d1e8-136">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="7d1e8-137">Scorrere verso il basso, sotto l'elenco delle reti Wi-Fi disponibili e selezionare **le proprietà Hardware**.</span><span class="sxs-lookup"><span data-stu-id="7d1e8-137">Scroll down to beneath the list of available Wi-Fi networks and select **Hardware properties**.</span></span>

    ![Proprietà hardware nelle impostazioni Wi-Fi](images/wifi-hololens-hwdetails.jpg)

<span data-ttu-id="7d1e8-139">L'indirizzo IP verrà visualizzato accanto a **indirizzo IPv4**.</span><span class="sxs-lookup"><span data-stu-id="7d1e8-139">The IP address will be shown next to **IPv4 address**.</span></span>

### <a name="using-cortana"></a><span data-ttu-id="7d1e8-140">Uso di Cortana</span><span class="sxs-lookup"><span data-stu-id="7d1e8-140">Using Cortana</span></span>

<span data-ttu-id="7d1e8-141">Ad esempio "*Ehi Cortana, qual è l'indirizzo IP?*"</span><span class="sxs-lookup"><span data-stu-id="7d1e8-141">Say "*Hey Cortana, What's my IP address?*"</span></span> <span data-ttu-id="7d1e8-142">e Cortana visualizzerà e leggere l'indirizzo IP.</span><span class="sxs-lookup"><span data-stu-id="7d1e8-142">and Cortana will display and read out your IP address.</span></span>

### <a name="using-windows-device-portal"></a><span data-ttu-id="7d1e8-143">Utilizzo di Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="7d1e8-143">Using Windows Device Portal</span></span>

1. <span data-ttu-id="7d1e8-144">Aprire il [dispositivo portale](using-the-windows-device-portal.md#networking) in un web browser sul PC.</span><span class="sxs-lookup"><span data-stu-id="7d1e8-144">Open the [device portal](using-the-windows-device-portal.md#networking) in a web browser on your PC.</span></span>
2. <span data-ttu-id="7d1e8-145">Passare il **Networking** sezione.</span><span class="sxs-lookup"><span data-stu-id="7d1e8-145">Navigate to the **Networking** section.</span></span>

<span data-ttu-id="7d1e8-146">Verrà visualizzati l'indirizzo IP e altre informazioni di rete non esiste.</span><span class="sxs-lookup"><span data-stu-id="7d1e8-146">Your IP address and other network information will be displayed there.</span></span> <span data-ttu-id="7d1e8-147">Questo metodo consente facile copiare e incollare l'indirizzo IP del computer di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="7d1e8-147">This method allows for easy copy and paste of the IP address on your development PC.</span></span>
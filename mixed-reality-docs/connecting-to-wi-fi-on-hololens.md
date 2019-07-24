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
# <a name="connecting-to-wi-fi-on-hololens"></a><span data-ttu-id="9410c-104">Connessione al Wi-Fi su HoloLens</span><span class="sxs-lookup"><span data-stu-id="9410c-104">Connecting to Wi-Fi on HoloLens</span></span>

<span data-ttu-id="9410c-105">HoloLens contiene una radio Wi-Fi con supporto 802.11 AC.</span><span class="sxs-lookup"><span data-stu-id="9410c-105">HoloLens contains a 802.11ac-capable, 2x2 Wi-Fi radio.</span></span> <span data-ttu-id="9410c-106">La connessione di HoloLens a una rete Wi-Fi è simile alla connessione di un dispositivo Windows 10 desktop o mobile a una rete Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="9410c-106">Connecting HoloLens to a Wi-Fi network is similar to connecting a Windows 10 Desktop or Mobile device to a Wi-Fi network.</span></span>

![Impostazioni Wi-Fi HoloLens](images/wifi-hololens-600px.jpg)

## <a name="connecting-to-a-wi-fi-network-on-hololens"></a><span data-ttu-id="9410c-108">Connessione a una rete Wi-Fi su HoloLens</span><span class="sxs-lookup"><span data-stu-id="9410c-108">Connecting to a Wi-Fi network on HoloLens</span></span>

1. <span data-ttu-id="9410c-109">[Sbocciare](gestures.md#bloom) sul menu **Start** .</span><span class="sxs-lookup"><span data-stu-id="9410c-109">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="9410c-110">Selezionare l'app **Impostazioni** dall'inizio o dall'elenco **tutte le app** a destra del menu Start.</span><span class="sxs-lookup"><span data-stu-id="9410c-110">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="9410c-111">L'app **Impostazioni** verrà automaticamente posizionata in primo piano.</span><span class="sxs-lookup"><span data-stu-id="9410c-111">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="9410c-112">Selezionare **rete & Internet**.</span><span class="sxs-lookup"><span data-stu-id="9410c-112">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="9410c-113">Verifica che il Wi-Fi sia attivato.</span><span class="sxs-lookup"><span data-stu-id="9410c-113">Make sure Wi-Fi is turned on.</span></span>
6. <span data-ttu-id="9410c-114">Selezionare una rete Wi-Fi nell'elenco.</span><span class="sxs-lookup"><span data-stu-id="9410c-114">Select a Wi-Fi network from the list.</span></span>
7. <span data-ttu-id="9410c-115">Digitare la password della rete Wi-Fi (se necessario).</span><span class="sxs-lookup"><span data-stu-id="9410c-115">Type in the Wi-Fi network password (if needed).</span></span>

## <a name="disabling-wi-fi-on-hololens"></a><span data-ttu-id="9410c-116">Disabilitazione di Wi-Fi su HoloLens</span><span class="sxs-lookup"><span data-stu-id="9410c-116">Disabling Wi-Fi on HoloLens</span></span>

### <a name="using-the-settings-app-on-hololens"></a><span data-ttu-id="9410c-117">Uso dell'app Settings in HoloLens</span><span class="sxs-lookup"><span data-stu-id="9410c-117">Using the Settings app on HoloLens</span></span>

1. <span data-ttu-id="9410c-118">[Sbocciare](gestures.md#bloom) sul menu **Start** .</span><span class="sxs-lookup"><span data-stu-id="9410c-118">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="9410c-119">Selezionare l'app **Impostazioni** dall'inizio o dall'elenco **tutte le app** a destra del menu Start.</span><span class="sxs-lookup"><span data-stu-id="9410c-119">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="9410c-120">L'app **Impostazioni** verrà automaticamente posizionata in primo piano.</span><span class="sxs-lookup"><span data-stu-id="9410c-120">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="9410c-121">Selezionare **rete & Internet**.</span><span class="sxs-lookup"><span data-stu-id="9410c-121">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="9410c-122">Selezionare il dispositivo di scorrimento Wi-Fi per spostarlo nella posizione "off".</span><span class="sxs-lookup"><span data-stu-id="9410c-122">Select the Wi-Fi slider switch to move it to the "Off" position.</span></span> <span data-ttu-id="9410c-123">Questa operazione Disabilita i componenti RF della radio Wi-Fi e disattiva tutte le funzionalità Wi-Fi in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9410c-123">This will turn off the RF components of the Wi-Fi radio and disable all Wi-Fi functionality on HoloLens.</span></span> 

    >[!WARNING]
    ><span data-ttu-id="9410c-124">HoloLens non sarà in grado di caricare automaticamente gli [spazi](environment-considerations-for-hololens.md#WiFi fingerprint considerations) quando la radio Wi-Fi è disabilitata.</span><span class="sxs-lookup"><span data-stu-id="9410c-124">HoloLens will not be able to automatically load your [spaces](environment-considerations-for-hololens.md#WiFi fingerprint considerations) when the Wi-Fi radio is disabled.</span></span>
    
6. <span data-ttu-id="9410c-125">Spostare il dispositivo di scorrimento nella posizione "on" per attivare la funzionalità radio Wi-Fi e ripristinare la funzionalità Wi-Fi in Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9410c-125">Move the slider switch to the "On" position to turn on the Wi-Fi radio and restore Wi-Fi functionality on Microsoft HoloLens.</span></span> <span data-ttu-id="9410c-126">Lo stato di radio Wi-Fi selezionato ("on" di "off") viene mantenuto tra i riavvii.</span><span class="sxs-lookup"><span data-stu-id="9410c-126">The selected Wi-Fi radio state ("On" of "Off") will persist across reboots.</span></span>

## <a name="how-to-confirm-you-are-connected-to-a-wi-fi-network"></a><span data-ttu-id="9410c-127">Come verificare di essere connessi a una rete Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="9410c-127">How to confirm you are connected to a Wi-Fi network</span></span>

1. <span data-ttu-id="9410c-128">[Bloom](gestures.md#bloom) per visualizzare il menu **Start** .</span><span class="sxs-lookup"><span data-stu-id="9410c-128">[Bloom](gestures.md#bloom) to bring up the **Start** menu.</span></span>
2. <span data-ttu-id="9410c-129">Esaminare la parte superiore sinistra del menu Start per lo stato Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="9410c-129">Look at the top left of the Start menu for Wi-Fi status.</span></span> <span data-ttu-id="9410c-130">Verrà visualizzato lo stato di Wi-Fi e SSID della rete connessa.</span><span class="sxs-lookup"><span data-stu-id="9410c-130">The state of Wi-Fi and the SSID of the connected network will be shown.</span></span>

## <a name="identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network"></a><span data-ttu-id="9410c-131">Identificazione dell'indirizzo IP della HoloLens nella rete Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="9410c-131">Identifying the IP Address of your HoloLens on the Wi-Fi network</span></span>

### <a name="using-the-settings-app"></a><span data-ttu-id="9410c-132">Uso dell'app Settings</span><span class="sxs-lookup"><span data-stu-id="9410c-132">Using the Settings app</span></span>

1. <span data-ttu-id="9410c-133">[Sbocciare](gestures.md#bloom) sul menu **Start** .</span><span class="sxs-lookup"><span data-stu-id="9410c-133">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="9410c-134">Selezionare l'app **Impostazioni** dall'inizio o dall'elenco **tutte le app** a destra del menu Start.</span><span class="sxs-lookup"><span data-stu-id="9410c-134">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="9410c-135">L'app **Impostazioni** verrà automaticamente posizionata in primo piano.</span><span class="sxs-lookup"><span data-stu-id="9410c-135">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="9410c-136">Selezionare **rete & Internet**.</span><span class="sxs-lookup"><span data-stu-id="9410c-136">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="9410c-137">Scorrere fino a sotto l'elenco delle reti Wi-Fi disponibili e selezionare **proprietà hardware**.</span><span class="sxs-lookup"><span data-stu-id="9410c-137">Scroll down to beneath the list of available Wi-Fi networks and select **Hardware properties**.</span></span>

    ![Proprietà hardware nelle impostazioni Wi-Fi](images/wifi-hololens-hwdetails.jpg)

<span data-ttu-id="9410c-139">L'indirizzo IP verrà visualizzato accanto a **indirizzo IPv4**.</span><span class="sxs-lookup"><span data-stu-id="9410c-139">The IP address will be shown next to **IPv4 address**.</span></span>

### <a name="using-cortana"></a><span data-ttu-id="9410c-140">Uso di Cortana</span><span class="sxs-lookup"><span data-stu-id="9410c-140">Using Cortana</span></span>

<span data-ttu-id="9410c-141">Pronunciare "*Hey Cortana, qual è il mio indirizzo IP?* "</span><span class="sxs-lookup"><span data-stu-id="9410c-141">Say "*Hey Cortana, What's my IP address?*"</span></span> <span data-ttu-id="9410c-142">Cortana visualizzerà e leggerà l'indirizzo IP.</span><span class="sxs-lookup"><span data-stu-id="9410c-142">and Cortana will display and read out your IP address.</span></span>

### <a name="using-windows-device-portal"></a><span data-ttu-id="9410c-143">Uso del portale per dispositivi Windows</span><span class="sxs-lookup"><span data-stu-id="9410c-143">Using Windows Device Portal</span></span>

1. <span data-ttu-id="9410c-144">Aprire il [portale del dispositivo](using-the-windows-device-portal.md#networking) in un Web browser sul PC.</span><span class="sxs-lookup"><span data-stu-id="9410c-144">Open the [device portal](using-the-windows-device-portal.md#networking) in a web browser on your PC.</span></span>
2. <span data-ttu-id="9410c-145">Passare alla sezione **rete** .</span><span class="sxs-lookup"><span data-stu-id="9410c-145">Navigate to the **Networking** section.</span></span>

<span data-ttu-id="9410c-146">Verrà visualizzato l'indirizzo IP e altre informazioni di rete.</span><span class="sxs-lookup"><span data-stu-id="9410c-146">Your IP address and other network information will be displayed there.</span></span> <span data-ttu-id="9410c-147">Questo metodo consente di copiare e incollare facilmente l'indirizzo IP nel PC di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="9410c-147">This method allows for easy copy and paste of the IP address on your development PC.</span></span>

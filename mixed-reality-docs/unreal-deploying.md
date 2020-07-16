---
title: Distribuire nel dispositivo in Unreal
description: Guida alla distribuzione di un dispositivo in Unreal a HoloLens 2
author: sw5813
ms.author: suwu
ms.date: 7/10/2020
ms.topic: article
keywords: Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, distribuzione nel dispositivo, PC, documentazione
appliesto:
- HoloLens 2
ms.openlocfilehash: 2d0cd67db79c1970695334d826fbbaf0f2f92ec0
ms.sourcegitcommit: 2813f5b3027d47f7c6e9772338935eeccfa2aaec
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/16/2020
ms.locfileid: "86408179"
---
# <a name="deploy-to-device-in-unreal"></a><span data-ttu-id="cf6ff-104">Distribuire nel dispositivo in Unreal</span><span class="sxs-lookup"><span data-stu-id="cf6ff-104">Deploy to device in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="cf6ff-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="cf6ff-105">Overview</span></span>
<span data-ttu-id="cf6ff-106">Esistono due modi per distribuire un'applicazione Unreal in HoloLens 2:</span><span class="sxs-lookup"><span data-stu-id="cf6ff-106">There are two ways to deploy an Unreal application to HoloLens 2:</span></span> 
* <span data-ttu-id="cf6ff-107">Direttamente dall'editor non reale</span><span class="sxs-lookup"><span data-stu-id="cf6ff-107">Directly from the Unreal editor</span></span>
* <span data-ttu-id="cf6ff-108">Come pacchetto caricato tramite il portale del dispositivo</span><span class="sxs-lookup"><span data-stu-id="cf6ff-108">As a package uploaded via the device portal</span></span>

<span data-ttu-id="cf6ff-109">Per entrambe le opzioni è necessario configurare il HoloLens per l'uso del portale per lo sviluppo del [dispositivo](using-the-windows-device-portal.md) .</span><span class="sxs-lookup"><span data-stu-id="cf6ff-109">Both options require you to set up your HoloLens to use the [device portal](using-the-windows-device-portal.md) for development.</span></span> 

## <a name="deploying-to-device-from-the-unreal-editor"></a><span data-ttu-id="cf6ff-110">Distribuzione nel dispositivo da un editor non reale</span><span class="sxs-lookup"><span data-stu-id="cf6ff-110">Deploying to device from the Unreal editor</span></span>

1. <span data-ttu-id="cf6ff-111">Fare clic sulla freccia a discesa accanto al pulsante **Avvia** .</span><span class="sxs-lookup"><span data-stu-id="cf6ff-111">Click the dropdown arrow next to the **Launch** button.</span></span> <span data-ttu-id="cf6ff-112">Inizialmente, l'opzione del dispositivo HoloLens sarà disabilitata.</span><span class="sxs-lookup"><span data-stu-id="cf6ff-112">Initially, the HoloLens device option will be grayed out.</span></span>

![Opzioni menu a discesa Avvia](images/unreal/launch-dropdown.png)

2. <span data-ttu-id="cf6ff-114">Aprire il **Device Manager**.</span><span class="sxs-lookup"><span data-stu-id="cf6ff-114">Open the **Device Manager**.</span></span> <span data-ttu-id="cf6ff-115">Si noti che il HoloLens non verrà visualizzato automaticamente nell'elenco dei dispositivi.</span><span class="sxs-lookup"><span data-stu-id="cf6ff-115">Note that your HoloLens won't automatically appear in the device list.</span></span>

3. <span data-ttu-id="cf6ff-116">Espandere la sezione **aggiungere un dispositivo** non in elenco.</span><span class="sxs-lookup"><span data-stu-id="cf6ff-116">Expand the **Add An Unlisted Device** section.</span></span>

4. <span data-ttu-id="cf6ff-117">Selezionare **HoloLens** come **piattaforma**.</span><span class="sxs-lookup"><span data-stu-id="cf6ff-117">Select **HoloLens** as your **Platform**.</span></span>

5. <span data-ttu-id="cf6ff-118">Immettere le informazioni sull'indirizzo IP e sulla porta dei dispositivi separati da due punti come identificatore del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="cf6ff-118">Enter your devices' IP address and port information separated by a colon as the device identifier.</span></span> <span data-ttu-id="cf6ff-119">Ad esempio, "127.0.0.1:10080" (quando si è connessi tramite USB).</span><span class="sxs-lookup"><span data-stu-id="cf6ff-119">For example, "127.0.0.1:10080" (when connected via USB).</span></span> <span data-ttu-id="cf6ff-120">Usare le credenziali del nome utente e della password del portale del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="cf6ff-120">Use your Device Portal username and password credentials.</span></span>

6. <span data-ttu-id="cf6ff-121">Premere **Aggiungi** e chiudere Gestione dispositivi.</span><span class="sxs-lookup"><span data-stu-id="cf6ff-121">Hit **Add** and close the device manager.</span></span> 
    * <span data-ttu-id="cf6ff-122">In caso di errore, ad esempio un indirizzo errato, un nome utente o una password, verrà visualizzato un messaggio nel log di output.</span><span class="sxs-lookup"><span data-stu-id="cf6ff-122">In the case of an error (such as wrong address, user name or password), a message will be printed to the Output Log.</span></span>

![Aggiunta di un dispositivo non in elenco](images/unreal/add-unlisted-device.png)

7. <span data-ttu-id="cf6ff-124">Fare clic sulla freccia a discesa accanto al pulsante **Launch (avvia** ). questa volta dovrebbe essere visualizzato il dispositivo HoloLens appena aggiunto.</span><span class="sxs-lookup"><span data-stu-id="cf6ff-124">Click the dropdown arrow next to the **Launch** button again - this time you should see the HoloLens device you just added.</span></span> <span data-ttu-id="cf6ff-125">Selezionare il dispositivo HoloLens da compilare e distribuire in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="cf6ff-125">Select the HoloLens device to build and deploy to your HoloLens.</span></span> 

>[!NOTE]
><span data-ttu-id="cf6ff-126">La compilazione per il dispositivo può comportare la ricompilazione degli shader (soprattutto alla prima esecuzione). questa operazione può richiedere alcuni minuti.</span><span class="sxs-lookup"><span data-stu-id="cf6ff-126">Building for the device may involve recompiling shaders (especially on the first run)- this can take a while.</span></span> <span data-ttu-id="cf6ff-127">Non lasciare che il dispositivo vada a dormire fino a quando l'app non è in esecuzione (potrebbe essere necessario investirla).</span><span class="sxs-lookup"><span data-stu-id="cf6ff-127">Don't let the device go to sleep until the app is running (you may have to wear it).</span></span> <span data-ttu-id="cf6ff-128">In caso contrario, la compilazione dello shader non riuscirà.</span><span class="sxs-lookup"><span data-stu-id="cf6ff-128">Otherwise shader compilation will fail!</span></span>

## <a name="deploying-to-device-via-device-portal"></a><span data-ttu-id="cf6ff-129">Distribuzione nel dispositivo tramite il portale del dispositivo</span><span class="sxs-lookup"><span data-stu-id="cf6ff-129">Deploying to device via device portal</span></span>

<span data-ttu-id="cf6ff-130">Per istruzioni dettagliate sulla creazione di [pacchetti e sulla distribuzione di un'app,](unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) vedere l'ultima sezione del introduzione con la serie di esercitazioni Unreal.</span><span class="sxs-lookup"><span data-stu-id="cf6ff-130">You can find detailed instructions on [packaging and deploying an app](unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) in the last section of the Getting Started with Unreal tutorial series.</span></span>

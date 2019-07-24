---
title: Ottenere le app per HoloLens
description: Descrive l'installazione di app per HoloLens, sia tramite il Microsoft Store che il caricamento laterale.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: sideload, carico laterale, caricamento laterale, archivio, UWP, app, installazione
ms.openlocfilehash: 5042c380e3a548e5001e045676190c2349a835a0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522554"
---
# <a name="get-apps-for-hololens"></a><span data-ttu-id="685d7-104">Ottenere le app per HoloLens</span><span class="sxs-lookup"><span data-stu-id="685d7-104">Get apps for HoloLens</span></span>

<span data-ttu-id="685d7-105">Come dispositivo Windows 10, HoloLens supporta molte applicazioni UWP esistenti dall'App Store, oltre a nuove app compilate in modo specifico per HoloLens.</span><span class="sxs-lookup"><span data-stu-id="685d7-105">As a Windows 10 device, HoloLens supports many existing UWP applications from the app store, as well as new apps built specifically for HoloLens.</span></span> <span data-ttu-id="685d7-106">Oltre a questi elementi, è anche possibile [sviluppare](development-overview.md) e installare le proprie app o gli amici.</span><span class="sxs-lookup"><span data-stu-id="685d7-106">On top of these, you may even want to [develop](development-overview.md) and install your own apps or those of your friends!</span></span>

## <a name="installing-apps"></a><span data-ttu-id="685d7-107">Installazione di app</span><span class="sxs-lookup"><span data-stu-id="685d7-107">Installing Apps</span></span>

<span data-ttu-id="685d7-108">Sono disponibili tre modi per installare le nuove app in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="685d7-108">There are three ways to install new apps on your HoloLens.</span></span> <span data-ttu-id="685d7-109">Il metodo principale consisterà nell'installare nuove applicazioni da Windows Store.</span><span class="sxs-lookup"><span data-stu-id="685d7-109">The primary method will be to install new applications from the Windows Store.</span></span> <span data-ttu-id="685d7-110">Tuttavia, è anche possibile installare applicazioni personalizzate usando il portale del dispositivo o distribuendo tali applicazioni da Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="685d7-110">However, you can also install your own applications using either the Device Portal or by deploying them from Visual Studio.</span></span>

### <a name="from-the-microsoft-store"></a><span data-ttu-id="685d7-111">Dal Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="685d7-111">From the Microsoft Store</span></span>
1. <span data-ttu-id="685d7-112">Eseguire un movimento [Bloom](gestures.md#bloom) per aprire il [menu Start](navigating-the-windows-mixed-reality-home.md#start-menu).</span><span class="sxs-lookup"><span data-stu-id="685d7-112">Perform a [bloom](gestures.md#bloom) gesture to open the [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu).</span></span>
2. <span data-ttu-id="685d7-113">Selezionare l'App Store e quindi toccare per inserire il riquadro nel mondo.</span><span class="sxs-lookup"><span data-stu-id="685d7-113">Select the Store app and then tap to place this tile into your world.</span></span>
3. <span data-ttu-id="685d7-114">Quando si apre l'App Store, usare la barra di ricerca per cercare le applicazioni desiderate.</span><span class="sxs-lookup"><span data-stu-id="685d7-114">Once the Store app opens, use the search bar to look for any desired application.</span></span>
4. <span data-ttu-id="685d7-115">Selezionare **Get** o **Install** nella pagina dell'applicazione (potrebbe essere necessario un acquisto).</span><span class="sxs-lookup"><span data-stu-id="685d7-115">Select **Get** or **Install** on the application's page (a purchase may be required).</span></span>

### <a name="installing-an-application-package-with-the-device-portal"></a><span data-ttu-id="685d7-116">Installazione di un pacchetto dell'applicazione con il portale del dispositivo</span><span class="sxs-lookup"><span data-stu-id="685d7-116">Installing an application package with the Device Portal</span></span>
1. <span data-ttu-id="685d7-117">Stabilire una connessione dal [portale del dispositivo](using-the-windows-device-portal.md) al HoloLens di destinazione.</span><span class="sxs-lookup"><span data-stu-id="685d7-117">Establish a connection from [Device Portal](using-the-windows-device-portal.md) to the target HoloLens.</span></span>
2. <span data-ttu-id="685d7-118">Passare alla pagina **app** nel percorso di spostamento a sinistra.</span><span class="sxs-lookup"><span data-stu-id="685d7-118">Navigate to the **Apps** page in the left navigation.</span></span>
3. <span data-ttu-id="685d7-119">In **pacchetto app** selezionare il file con estensione appx associato all'applicazione.</span><span class="sxs-lookup"><span data-stu-id="685d7-119">Under **App Package** Browse to the .appx file associated with your application.</span></span>
  >[!IMPORTANT]
  ><span data-ttu-id="685d7-120">Assicurarsi di fare riferimento ai file di dipendenza e di certificato associati.</span><span class="sxs-lookup"><span data-stu-id="685d7-120">Make sure to reference any associated dependency and certificate files.</span></span>

4. <span data-ttu-id="685d7-121">Fare clic su **Vai**.</span><span class="sxs-lookup"><span data-stu-id="685d7-121">Click **Go**.</span></span>

<span data-ttu-id="685d7-122">![Installare il modulo dell'app nel portale per dispositivi Windows in Microsoft HoloLens](images/deviceportal-appmanager.jpg)</span><span class="sxs-lookup"><span data-stu-id="685d7-122">![Install app form in Windows Device Portal on Microsoft HoloLens](images/deviceportal-appmanager.jpg)</span></span><br>
<span data-ttu-id="685d7-123">Uso del portale per dispositivi Windows per installare un'app in HoloLens</span><span class="sxs-lookup"><span data-stu-id="685d7-123">Using Windows Device Portal to install an app on HoloLens</span></span>

### <a name="deploying-from-microsoft-visual-studio-2015"></a><span data-ttu-id="685d7-124">Distribuzione da Microsoft Visual Studio 2015</span><span class="sxs-lookup"><span data-stu-id="685d7-124">Deploying from Microsoft Visual Studio 2015</span></span>
1. <span data-ttu-id="685d7-125">Aprire la soluzione Visual Studio dell'app (file con estensione sln).</span><span class="sxs-lookup"><span data-stu-id="685d7-125">Open your app's Visual Studio solution (.sln file).</span></span>
2. <span data-ttu-id="685d7-126">Aprire le **Proprietà** del progetto.</span><span class="sxs-lookup"><span data-stu-id="685d7-126">Open the project's **Properties** .</span></span>
3. <span data-ttu-id="685d7-127">Selezionare la configurazione di compilazione seguente: Master/x86/computer remoto.</span><span class="sxs-lookup"><span data-stu-id="685d7-127">Select the following build configuration: Master/x86/Remote Machine.</span></span>
4. <span data-ttu-id="685d7-128">Quando si seleziona computer remoto:</span><span class="sxs-lookup"><span data-stu-id="685d7-128">When you select Remote Machine:</span></span>
   * <span data-ttu-id="685d7-129">Assicurarsi che l'indirizzo punti all'indirizzo IP Wi-Fi HoloLens '.</span><span class="sxs-lookup"><span data-stu-id="685d7-129">Make sure the address points to the HoloLens' WiFi IP address.</span></span>
   * <span data-ttu-id="685d7-130">Impostare l'autenticazione su universale (protocollo non crittografato).</span><span class="sxs-lookup"><span data-stu-id="685d7-130">Set authentication to Universal (Unencrypted Protocol).</span></span>
5. <span data-ttu-id="685d7-131">Compilare la soluzione.</span><span class="sxs-lookup"><span data-stu-id="685d7-131">Build your solution.</span></span>
6. <span data-ttu-id="685d7-132">Fare clic sul pulsante **computer remoto** per distribuire l'app dal computer di sviluppo a HoloLens.</span><span class="sxs-lookup"><span data-stu-id="685d7-132">Click the **Remote Machine** button to deploy the app from your development PC to your HoloLens.</span></span> <span data-ttu-id="685d7-133">Se si dispone già di una compilazione esistente nel HoloLens, selezionare Sì per reinstallare la versione più recente.</span><span class="sxs-lookup"><span data-stu-id="685d7-133">If you already have an existing build on the HoloLens, select yes to re-install this newer version.</span></span><br>
  <span data-ttu-id="685d7-134">![Distribuzione del computer remoto per le app in Microsoft HoloLens in Visual Studio](images/vs2015-remotedeployment.jpg)</span><span class="sxs-lookup"><span data-stu-id="685d7-134">![Remote Machine deployment for apps to Microsoft HoloLens in Visual Studio](images/vs2015-remotedeployment.jpg)</span></span><br>
7. <span data-ttu-id="685d7-135">L'applicazione viene installata e avviata automaticamente nella HoloLens.</span><span class="sxs-lookup"><span data-stu-id="685d7-135">The application will install and auto launch on your HoloLens.</span></span>

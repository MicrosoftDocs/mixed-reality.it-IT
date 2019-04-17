---
title: Ottenere le App per HoloLens
description: Descrive installare le App per HoloLens, sia tramite il Microsoft Store e il caricamento laterale.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: sideload delle applicazioni, carico lato, trasferire localmente, store, uwp, app, installare
ms.openlocfilehash: 5042c380e3a548e5001e045676190c2349a835a0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597553"
---
# <a name="get-apps-for-hololens"></a><span data-ttu-id="a95ec-104">Ottenere le App per HoloLens</span><span class="sxs-lookup"><span data-stu-id="a95ec-104">Get apps for HoloLens</span></span>

<span data-ttu-id="a95ec-105">Come un dispositivo Windows 10, HoloLens supporta molte applicazioni UWP esistenti dall'archivio app, nonché nuove app sviluppata appositamente per HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a95ec-105">As a Windows 10 device, HoloLens supports many existing UWP applications from the app store, as well as new apps built specifically for HoloLens.</span></span> <span data-ttu-id="a95ec-106">Su questi elementi, si potrebbe anche voler [sviluppare](development-overview.md) e installare App personalizzate o quelli dei tuoi amici.</span><span class="sxs-lookup"><span data-stu-id="a95ec-106">On top of these, you may even want to [develop](development-overview.md) and install your own apps or those of your friends!</span></span>

## <a name="installing-apps"></a><span data-ttu-id="a95ec-107">Installazione di App</span><span class="sxs-lookup"><span data-stu-id="a95ec-107">Installing Apps</span></span>

<span data-ttu-id="a95ec-108">Esistono tre modi per installare nuove app in di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a95ec-108">There are three ways to install new apps on your HoloLens.</span></span> <span data-ttu-id="a95ec-109">Il metodo principale sarà possibile installare le nuove applicazioni da Store di Windows.</span><span class="sxs-lookup"><span data-stu-id="a95ec-109">The primary method will be to install new applications from the Windows Store.</span></span> <span data-ttu-id="a95ec-110">Tuttavia, è anche possibile installare applicazioni personalizzate tramite il portale di dispositivo o distribuirli da Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a95ec-110">However, you can also install your own applications using either the Device Portal or by deploying them from Visual Studio.</span></span>

### <a name="from-the-microsoft-store"></a><span data-ttu-id="a95ec-111">Da di Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="a95ec-111">From the Microsoft Store</span></span>
1. <span data-ttu-id="a95ec-112">Eseguire un' [bloom](gestures.md#bloom) movimento per aprire il [dal Menu Start](navigating-the-windows-mixed-reality-home.md#start-menu).</span><span class="sxs-lookup"><span data-stu-id="a95ec-112">Perform a [bloom](gestures.md#bloom) gesture to open the [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu).</span></span>
2. <span data-ttu-id="a95ec-113">Selezionare l'app Store e quindi toccare per inserire questo riquadro nel tuo mondo.</span><span class="sxs-lookup"><span data-stu-id="a95ec-113">Select the Store app and then tap to place this tile into your world.</span></span>
3. <span data-ttu-id="a95ec-114">Quando si apre l'app Store, usare la barra di ricerca per cercare qualsiasi applicazione desiderata.</span><span class="sxs-lookup"><span data-stu-id="a95ec-114">Once the Store app opens, use the search bar to look for any desired application.</span></span>
4. <span data-ttu-id="a95ec-115">Selezionare **ottenere** oppure **installare** nella pagina dell'applicazione (un acquisto potrebbe essere necessario).</span><span class="sxs-lookup"><span data-stu-id="a95ec-115">Select **Get** or **Install** on the application's page (a purchase may be required).</span></span>

### <a name="installing-an-application-package-with-the-device-portal"></a><span data-ttu-id="a95ec-116">Installazione di un pacchetto di applicazione con il portale del dispositivo</span><span class="sxs-lookup"><span data-stu-id="a95ec-116">Installing an application package with the Device Portal</span></span>
1. <span data-ttu-id="a95ec-117">Stabilire una connessione tra [dispositivo portale](using-the-windows-device-portal.md) alla destinazione HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a95ec-117">Establish a connection from [Device Portal](using-the-windows-device-portal.md) to the target HoloLens.</span></span>
2. <span data-ttu-id="a95ec-118">Passare il **app** pagina nel riquadro di spostamento a sinistra.</span><span class="sxs-lookup"><span data-stu-id="a95ec-118">Navigate to the **Apps** page in the left navigation.</span></span>
3. <span data-ttu-id="a95ec-119">Sotto **pacchetto dell'App** individuare il file con estensione AppX associato all'applicazione.</span><span class="sxs-lookup"><span data-stu-id="a95ec-119">Under **App Package** Browse to the .appx file associated with your application.</span></span>
  >[!IMPORTANT]
  ><span data-ttu-id="a95ec-120">Assicurarsi di fare riferimento a tutti i file delle dipendenze e il certificato associati.</span><span class="sxs-lookup"><span data-stu-id="a95ec-120">Make sure to reference any associated dependency and certificate files.</span></span>

4. <span data-ttu-id="a95ec-121">Fare clic su **Vai**.</span><span class="sxs-lookup"><span data-stu-id="a95ec-121">Click **Go**.</span></span>

<span data-ttu-id="a95ec-122">![Installa modulo dell'app in Windows Device Portal in Microsoft HoloLens](images/deviceportal-appmanager.jpg)</span><span class="sxs-lookup"><span data-stu-id="a95ec-122">![Install app form in Windows Device Portal on Microsoft HoloLens](images/deviceportal-appmanager.jpg)</span></span><br>
<span data-ttu-id="a95ec-123">Utilizzo di Windows Device Portal per installare un'app in HoloLens</span><span class="sxs-lookup"><span data-stu-id="a95ec-123">Using Windows Device Portal to install an app on HoloLens</span></span>

### <a name="deploying-from-microsoft-visual-studio-2015"></a><span data-ttu-id="a95ec-124">Distribuzione da Microsoft Visual Studio 2015</span><span class="sxs-lookup"><span data-stu-id="a95ec-124">Deploying from Microsoft Visual Studio 2015</span></span>
1. <span data-ttu-id="a95ec-125">Aprire la soluzione di Visual Studio della tua app (file con estensione sln).</span><span class="sxs-lookup"><span data-stu-id="a95ec-125">Open your app's Visual Studio solution (.sln file).</span></span>
2. <span data-ttu-id="a95ec-126">Aprire il progetto **proprietà** .</span><span class="sxs-lookup"><span data-stu-id="a95ec-126">Open the project's **Properties** .</span></span>
3. <span data-ttu-id="a95ec-127">Selezionare la configurazione di compilazione seguenti: Macchina master/x86/Remote.</span><span class="sxs-lookup"><span data-stu-id="a95ec-127">Select the following build configuration: Master/x86/Remote Machine.</span></span>
4. <span data-ttu-id="a95ec-128">Quando si seleziona computer remoto:</span><span class="sxs-lookup"><span data-stu-id="a95ec-128">When you select Remote Machine:</span></span>
   * <span data-ttu-id="a95ec-129">Assicurarsi che l'indirizzo punti all'indirizzo IP WiFi degli HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a95ec-129">Make sure the address points to the HoloLens' WiFi IP address.</span></span>
   * <span data-ttu-id="a95ec-130">Impostare l'autenticazione universale (protocollo non crittografato).</span><span class="sxs-lookup"><span data-stu-id="a95ec-130">Set authentication to Universal (Unencrypted Protocol).</span></span>
5. <span data-ttu-id="a95ec-131">Compilare la soluzione.</span><span class="sxs-lookup"><span data-stu-id="a95ec-131">Build your solution.</span></span>
6. <span data-ttu-id="a95ec-132">Scegliere il **computer remoto** pulsante per distribuire l'app dal computer di sviluppo di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a95ec-132">Click the **Remote Machine** button to deploy the app from your development PC to your HoloLens.</span></span> <span data-ttu-id="a95ec-133">Se si dispone già di una compilazione esistente nella finestra di HoloLens, selezionare Sì per reinstallare la versione più recente.</span><span class="sxs-lookup"><span data-stu-id="a95ec-133">If you already have an existing build on the HoloLens, select yes to re-install this newer version.</span></span><br>
  <span data-ttu-id="a95ec-134">![Distribuzione della macchina remota per le App per Microsoft HoloLens in Visual Studio](images/vs2015-remotedeployment.jpg)</span><span class="sxs-lookup"><span data-stu-id="a95ec-134">![Remote Machine deployment for apps to Microsoft HoloLens in Visual Studio](images/vs2015-remotedeployment.jpg)</span></span><br>
7. <span data-ttu-id="a95ec-135">L'applicazione venga installata ed auto avvio di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a95ec-135">The application will install and auto launch on your HoloLens.</span></span>

---
title: 6. Creazione di pacchetti e distribuzione nel dispositivo o nell'emulatore
description: Parte 6 di un'esercitazione per la creazione di una semplice app di scacchi con Unreal Engine 4 e il plug-in UX Tools di Mixed Reality Toolkit
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, esercitazione, guida introduttiva, mrtk, uxt, UX Tools, documentazione
ms.openlocfilehash: b3f0b5f9ca5347c337091539b1cc0e214515c989
ms.sourcegitcommit: 09d9fa153cd9072f60e33a5f83ced8167496fcd7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/18/2020
ms.locfileid: "83519968"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a><span data-ttu-id="e4b86-104">6. Creazione di pacchetti e distribuzione nel dispositivo o nell'emulatore</span><span class="sxs-lookup"><span data-stu-id="e4b86-104">6. Packaging & deploying to device or emulator</span></span>

<span data-ttu-id="e4b86-105">Questa sezione illustra i passaggi necessari per preparare l'app per l'esecuzione in un dispositivo o un emulatore HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="e4b86-105">This section walks you through the steps of preparing your app to run on a HoloLens 2 device or Emulator.</span></span> <span data-ttu-id="e4b86-106">Se usi un dispositivo, puoi eseguire il flusso dal computer al dispositivo oppure configurare l'app in modo da poter essere eseguita direttamente sul dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e4b86-106">If you have a device, you can either stream from your computer to the device or package the app to run directly on the device.</span></span> <span data-ttu-id="e4b86-107">Se invece non usi un dispositivo, dovrai configurare l'app affinché venga eseguita nell'emulatore.</span><span class="sxs-lookup"><span data-stu-id="e4b86-107">If you do not have a device, you will need to package the app for it to run on the Emulator.</span></span> 

## <a name="objectives"></a><span data-ttu-id="e4b86-108">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="e4b86-108">Objectives</span></span>

* <span data-ttu-id="e4b86-109">[Solo dispositivo] Eseguire lo streaming dell'app in HoloLens 2 da remoto tramite un'app olografica</span><span class="sxs-lookup"><span data-stu-id="e4b86-109">[Device only] Stream your app to HoloLens 2 via holographic app remoting</span></span>
* <span data-ttu-id="e4b86-110">Creare il pacchetto e distribuire l'app in un dispositivo o un emulatore HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="e4b86-110">Package and deploy your app to a HoloLens 2 device or emulator</span></span>

## <a name="device-only-stream"></a><span data-ttu-id="e4b86-111">[Solo dispositivo] Eseguire lo streaming</span><span class="sxs-lookup"><span data-stu-id="e4b86-111">[Device Only] Stream</span></span>

1.  <span data-ttu-id="e4b86-112">Installa **Holographic Remoting Player** dal Microsoft Store in HoloLens 2 ed esegui l'app</span><span class="sxs-lookup"><span data-stu-id="e4b86-112">Install the **Holographic Remoting Player** from the Microsoft Store on your HoloLens 2 and run the app</span></span>

2.  <span data-ttu-id="e4b86-113">Passa a **Edit > Project Settings** (Modifica > Impostazioni progetto).</span><span class="sxs-lookup"><span data-stu-id="e4b86-113">Go to **Edit > Project Settings**.</span></span> <span data-ttu-id="e4b86-114">Nella sezione Holographic Remoting seleziona la casella per abilitare la comunicazione remota e riavviare l'editor.</span><span class="sxs-lookup"><span data-stu-id="e4b86-114">In the Holographic Remoting section, check the box to enable remoting and restart the editor.</span></span>

3.  <span data-ttu-id="e4b86-115">Immetti l'indirizzo IP del dispositivo e fai clic su Connect (Connetti).</span><span class="sxs-lookup"><span data-stu-id="e4b86-115">Input the IP address of your device and click Connect.</span></span>

4.  <span data-ttu-id="e4b86-116">Dopo esserti connesso, nell'editor di UE4 fai clic sulla freccia a discesa a destra del pulsante di riproduzione e seleziona VR Preview (Anteprima VR).</span><span class="sxs-lookup"><span data-stu-id="e4b86-116">Once you’re connected, in your UE4 Editor, click the drop-down arrow to the right of the Play button and select VR Preview.</span></span>

## <a name="package-and-deploy-your-app"></a><span data-ttu-id="e4b86-117">Creare il pacchetto e distribuire l'app</span><span class="sxs-lookup"><span data-stu-id="e4b86-117">Package and deploy your app</span></span> 

>[!NOTE]
><span data-ttu-id="e4b86-118">Se è la prima volta esegui il packaging di un'app Unreal per HoloLens, dovrai scaricare i file di supporto dall'utilità di avvio Epic.</span><span class="sxs-lookup"><span data-stu-id="e4b86-118">If this is your first time packaging an Unreal app for HoloLens, you'll need to download supporting files from the Epic Launcher.</span></span> <span data-ttu-id="e4b86-119">A tale scopo, passa alla scheda **Library** (Libreria) nell'utilità di avvio Epic Games.</span><span class="sxs-lookup"><span data-stu-id="e4b86-119">To do so, go to the **Library** tab in the Epic Games Launcher.</span></span> <span data-ttu-id="e4b86-120">Seleziona la freccia a discesa accanto a **Launch** (Avvia) quindi **Options** (Opzioni).</span><span class="sxs-lookup"><span data-stu-id="e4b86-120">Select the dropdown arrow next to **Launch** and select **Options**.</span></span> <span data-ttu-id="e4b86-121">In **Target Platforms** (Piattaforme di destinazione) seleziona **HoloLens 2** e fai clic su **Apply** (Applica).</span><span class="sxs-lookup"><span data-stu-id="e4b86-121">Under **Target Platforms**, select **HoloLens 2** and click **Apply**.</span></span> 
><span data-ttu-id="e4b86-122">![Impostazioni del progetto - Descrizione](images/unreal-uxt/6-installationoptions.PNG)</span><span class="sxs-lookup"><span data-stu-id="e4b86-122">![Project Settings - Description](images/unreal-uxt/6-installationoptions.PNG)</span></span>

1.  <span data-ttu-id="e4b86-123">Passa a **Edit > Project Settings** (Modifica > Impostazioni progetto).</span><span class="sxs-lookup"><span data-stu-id="e4b86-123">Go to **Edit > Project Settings**.</span></span> <span data-ttu-id="e4b86-124">In **Project > Description > About > Project Name** (Progetto > Descrizione > Informazioni -> Nome progetto) assegna un nome al progetto.</span><span class="sxs-lookup"><span data-stu-id="e4b86-124">Under **Project > Description > About > Project Name**, give your project a name.</span></span> <span data-ttu-id="e4b86-125">In **Project > Description > Publisher > Company Distinguished Name** Progetto > Descrizione > Autore > Nome distinto società inserisci "CN={INSERISCI NOME SOCIETÀ}".</span><span class="sxs-lookup"><span data-stu-id="e4b86-125">Under **Project > Description > Publisher > Company Distinguished Name** put “CN={INSERT COMPANY NAME}”.</span></span> <span data-ttu-id="e4b86-126">Se lasci vuoto uno di questi campi, verrà generato un errore.</span><span class="sxs-lookup"><span data-stu-id="e4b86-126">Leaving either of these fields blank will result in an error.</span></span> 

![Impostazioni del progetto - Descrizione](images/unreal-uxt/6-cn.PNG)

2.  <span data-ttu-id="e4b86-128">In **Platforms > HoloLens** (Piattaforma > HoloLens) scegli l'emulazione e/o il dispositivo, in base al tipo di destinazione desiderato.</span><span class="sxs-lookup"><span data-stu-id="e4b86-128">Under **Platforms > HoloLens** choose Emulation and/or Device based on which you want to target.</span></span>

3.  <span data-ttu-id="e4b86-129">Nella sezione **Packaging** (Creazione del pacchetto), accanto a **Signing Certificate** (Certificato di firma), fai clic sul pulsante **Generate new** (Genera nuovo) per generare un nuovo certificato di firma.</span><span class="sxs-lookup"><span data-stu-id="e4b86-129">In the **Packaging** section, next to **Signing Certificate**, click the **Generate new** button to generate a new signing certificate.</span></span> <span data-ttu-id="e4b86-130">Torna alla finestra principale.</span><span class="sxs-lookup"><span data-stu-id="e4b86-130">Return to the Main window.</span></span>

![Impostazioni di progetto - Piattaforme - HoloLens](images/unreal-uxt/6-packaging.PNG)

4.  <span data-ttu-id="e4b86-132">Passa a **File > Package Project** (File > Crea pacchetto progetto) e seleziona **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="e4b86-132">Go to **File > Package Project** and select **HoloLens**.</span></span> <span data-ttu-id="e4b86-133">Crea una nuova cartella in cui salvare il pacchetto e fare clic su **Select Folder** (Seleziona cartella).</span><span class="sxs-lookup"><span data-stu-id="e4b86-133">Create a new folder to save your package in and click **Select Folder**.</span></span> 

5.  <span data-ttu-id="e4b86-134">Dopo aver creato il pacchetto dell'app, apri **Windows Device Portal**, passa a **Views > Apps** (Viste > App) e trova la sezione **Deploy apps** (Distribuzione delle app).</span><span class="sxs-lookup"><span data-stu-id="e4b86-134">Once the app has been successfully packaged, open the **Windows Device Portal**, go to **Views > Apps**, and find the **Deploy apps** section.</span></span>

6.  <span data-ttu-id="e4b86-135">Fai clic su **Browse...** (Sfoglia...) e passa al file **ChessApp.appxbundle**.</span><span class="sxs-lookup"><span data-stu-id="e4b86-135">Click**Browse...** and navigate to your **ChessApp.appxbundle** file.</span></span> <span data-ttu-id="e4b86-136">Fare clic su **Apri**.</span><span class="sxs-lookup"><span data-stu-id="e4b86-136">Click **Open**.</span></span> 

    * <span data-ttu-id="e4b86-137">Se è la prima volta che installi l'app sul dispositivo, seleziona la casella accanto a **Allow me to select framework packages** (Consenti di selezionare i pacchetti del framework).</span><span class="sxs-lookup"><span data-stu-id="e4b86-137">If this is the first time you are installing the app on your device, check the box next to **Allow me to select framework packages**.</span></span> <span data-ttu-id="e4b86-138">Nella finestra di dialogo successiva, includi il file VCLibs.appx appropriato (arm64 per il dispositivo, x64 per l'emulatore).</span><span class="sxs-lookup"><span data-stu-id="e4b86-138">In the next dialogue, include the appropriate VCLibs appx file (arm64 for device, x64 for emulator).</span></span> 

7.  <span data-ttu-id="e4b86-139">Fai clic su **Install** (Installa).</span><span class="sxs-lookup"><span data-stu-id="e4b86-139">Click **Install**</span></span>

<span data-ttu-id="e4b86-140">Congratulazioni per aver completato questa esercitazione.</span><span class="sxs-lookup"><span data-stu-id="e4b86-140">Congratulations on finishing this tutorial!</span></span>  
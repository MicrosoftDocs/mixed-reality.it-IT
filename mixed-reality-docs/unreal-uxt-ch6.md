---
title: 6. Creazione di pacchetti e distribuzione nel dispositivo o nell'emulatore
description: Parte 6 di un'esercitazione per la creazione di una semplice app di scacchi con Unreal Engine 4 e il plug-in UX Tools di Mixed Reality Toolkit
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, esercitazione, guida introduttiva, mrtk, uxt, UX Tools, documentazione
ms.openlocfilehash: 35b18e4bb289438f94433827846e94d1014385db
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840380"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a><span data-ttu-id="7c124-104">6. Creazione di pacchetti e distribuzione nel dispositivo o nell'emulatore</span><span class="sxs-lookup"><span data-stu-id="7c124-104">6. Packaging & deploying to device or emulator</span></span>

<span data-ttu-id="7c124-105">Questa sezione illustra i passaggi necessari per preparare l'app per l'esecuzione in un dispositivo o un emulatore HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="7c124-105">This section walks you through the steps of preparing your app to run on a HoloLens 2 device or Emulator.</span></span> <span data-ttu-id="7c124-106">Se usi un dispositivo, puoi eseguire il flusso dal computer al dispositivo oppure configurare l'app in modo da poter essere eseguita direttamente sul dispositivo.</span><span class="sxs-lookup"><span data-stu-id="7c124-106">If you have a device, you can either stream from your computer to the device or package the app to run directly on the device.</span></span> <span data-ttu-id="7c124-107">Se invece non usi un dispositivo, dovrai configurare l'app affinché venga eseguita nell'emulatore.</span><span class="sxs-lookup"><span data-stu-id="7c124-107">If you do not have a device, you will need to package the app for it to run on the Emulator.</span></span> 

## <a name="objectives"></a><span data-ttu-id="7c124-108">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="7c124-108">Objectives</span></span>

* <span data-ttu-id="7c124-109">[Solo dispositivo] Eseguire lo streaming dell'app in HoloLens 2 da remoto tramite un'app olografica</span><span class="sxs-lookup"><span data-stu-id="7c124-109">[Device only] Stream your app to HoloLens 2 via holographic app remoting</span></span>
* <span data-ttu-id="7c124-110">Creare il pacchetto e distribuire l'app in un dispositivo o un emulatore HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="7c124-110">Package and deploy your app to a HoloLens 2 device or emulator</span></span>

## <a name="device-only-stream"></a><span data-ttu-id="7c124-111">[Solo dispositivo] Eseguire lo streaming</span><span class="sxs-lookup"><span data-stu-id="7c124-111">[Device Only] Stream</span></span>

1.  <span data-ttu-id="7c124-112">Installa **Holographic Remoting Player** dal Microsoft Store in HoloLens 2 ed esegui l'app</span><span class="sxs-lookup"><span data-stu-id="7c124-112">Install the **Holographic Remoting Player** from the Microsoft Store on your HoloLens 2 and run the app</span></span>

2.  <span data-ttu-id="7c124-113">Passa a **Edit > Project Settings** (Modifica > Impostazioni progetto).</span><span class="sxs-lookup"><span data-stu-id="7c124-113">Go to **Edit > Project Settings**.</span></span> <span data-ttu-id="7c124-114">Nella sezione Holographic Remoting seleziona la casella per abilitare la comunicazione remota e riavviare l'editor.</span><span class="sxs-lookup"><span data-stu-id="7c124-114">In the Holographic Remoting section, check the box to enable remoting and restart the editor.</span></span>

3.  <span data-ttu-id="7c124-115">Immetti l'indirizzo IP del dispositivo e fai clic su Connect (Connetti).</span><span class="sxs-lookup"><span data-stu-id="7c124-115">Input the IP address of your device and click Connect.</span></span>

4.  <span data-ttu-id="7c124-116">Dopo esserti connesso, nell'editor di UE4 fai clic sulla freccia a discesa a destra del pulsante di riproduzione e seleziona VR Preview (Anteprima VR).</span><span class="sxs-lookup"><span data-stu-id="7c124-116">Once you’re connected, in your UE4 Editor, click the drop-down arrow to the right of the Play button and select VR Preview.</span></span>

## <a name="package-and-deploy-your-app"></a><span data-ttu-id="7c124-117">Creare il pacchetto e distribuire l'app</span><span class="sxs-lookup"><span data-stu-id="7c124-117">Package and deploy your app</span></span> 

1.  <span data-ttu-id="7c124-118">Passa a **Edit > Project Settings** (Modifica > Impostazioni progetto).</span><span class="sxs-lookup"><span data-stu-id="7c124-118">Go to **Edit > Project Settings**.</span></span> <span data-ttu-id="7c124-119">In **Project > Description > About > Project Name** (Progetto > Descrizione > Informazioni -> Nome progetto) assegna un nome al progetto.</span><span class="sxs-lookup"><span data-stu-id="7c124-119">Under **Project > Description > About > Project Name**, give your project a name.</span></span> <span data-ttu-id="7c124-120">In **Project > Description > Publisher > Company Distinguished Name** Progetto > Descrizione > Autore > Nome distinto società inserisci "CN={INSERISCI NOME SOCIETÀ}".</span><span class="sxs-lookup"><span data-stu-id="7c124-120">Under **Project > Description > Publisher > Company Distinguished Name** put “CN={INSERT COMPANY NAME}”.</span></span> <span data-ttu-id="7c124-121">Se lasci vuoto uno di questi campi, verrà generato un errore.</span><span class="sxs-lookup"><span data-stu-id="7c124-121">Leaving either of these fields blank will result in an error.</span></span> 

![Impostazioni del progetto - Descrizione](images/unreal-uxt/6-cn.PNG)

2.  <span data-ttu-id="7c124-123">In **Platforms > HoloLens** (Piattaforma > HoloLens) scegli l'emulazione e/o il dispositivo, in base al tipo di destinazione desiderato.</span><span class="sxs-lookup"><span data-stu-id="7c124-123">Under **Platforms > HoloLens** choose Emulation and/or Device based on which you want to target.</span></span>

3.  <span data-ttu-id="7c124-124">Nella sezione **Packaging** (Creazione del pacchetto), accanto a **Signing Certificate** (Certificato di firma), fai clic sul pulsante **Generate new** (Genera nuovo) per generare un nuovo certificato di firma.</span><span class="sxs-lookup"><span data-stu-id="7c124-124">In the **Packaging** section, next to **Signing Certificate**, click the **Generate new** button to generate a new signing certificate.</span></span> <span data-ttu-id="7c124-125">Torna alla finestra principale.</span><span class="sxs-lookup"><span data-stu-id="7c124-125">Return to the Main window.</span></span>

![Impostazioni di progetto - Piattaforme - HoloLens](images/unreal-uxt/6-packaging.PNG)

4.  <span data-ttu-id="7c124-127">Passa a **File > Package Project** (File > Crea pacchetto progetto) e seleziona **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="7c124-127">Go to **File > Package Project** and select **HoloLens**.</span></span> <span data-ttu-id="7c124-128">Crea una nuova cartella in cui salvare il pacchetto e fare clic su **Select Folder** (Seleziona cartella).</span><span class="sxs-lookup"><span data-stu-id="7c124-128">Create a new folder to save your package in and click **Select Folder**.</span></span> 

5.  <span data-ttu-id="7c124-129">Dopo aver creato il pacchetto dell'app, apri **Windows Device Portal**, passa a **Views > Apps** (Viste > App) e trova la sezione **Deploy apps** (Distribuzione delle app).</span><span class="sxs-lookup"><span data-stu-id="7c124-129">Once the app has been successfully packaged, open the **Windows Device Portal**, go to **Views > Apps**, and find the **Deploy apps** section.</span></span>

6.  <span data-ttu-id="7c124-130">Fai clic su **Browse...** (Sfoglia...) e passa al file **ChessApp.appxbundle**.</span><span class="sxs-lookup"><span data-stu-id="7c124-130">Click**Browse...** and navigate to your **ChessApp.appxbundle** file.</span></span> <span data-ttu-id="7c124-131">Fare clic su **Apri**.</span><span class="sxs-lookup"><span data-stu-id="7c124-131">Click **Open**.</span></span> 

    * <span data-ttu-id="7c124-132">Se è la prima volta che installi l'app sul dispositivo, seleziona la casella accanto a **Allow me to select framework packages** (Consenti di selezionare i pacchetti del framework).</span><span class="sxs-lookup"><span data-stu-id="7c124-132">If this is the first time you are installing the app on your device, check the box next to **Allow me to select framework packages**.</span></span> <span data-ttu-id="7c124-133">Nella finestra di dialogo successiva, includi il file VCLibs.appx appropriato (arm64 per il dispositivo, x64 per l'emulatore).</span><span class="sxs-lookup"><span data-stu-id="7c124-133">In the next dialogue, include the appropriate VCLibs appx file (arm64 for device, x64 for emulator).</span></span> 

7.  <span data-ttu-id="7c124-134">Fai clic su **Install** (Installa).</span><span class="sxs-lookup"><span data-stu-id="7c124-134">Click **Install**</span></span>

<span data-ttu-id="7c124-135">Congratulazioni per aver completato questa esercitazione.</span><span class="sxs-lookup"><span data-stu-id="7c124-135">Congratulations on finishing this tutorial!</span></span>  
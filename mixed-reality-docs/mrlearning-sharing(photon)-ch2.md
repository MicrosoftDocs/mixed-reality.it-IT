---
title: Esercitazioni sulle funzionalità multiutente-2. Preparazione di Unity per lo sviluppo
description: Completare questo corso per apprendere come implementare esperienze condivise multiutente all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 6abf4fa8fc87afc7007d6f7c76becfbd88ed7a12
ms.sourcegitcommit: 2bfe9b1af4ee2cc0d668caeccb8ebc3137cbc20b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901510"
---
# <a name="2-getting-unity-ready-for-development"></a><span data-ttu-id="1a084-105">2. recupero di Unity pronto per lo sviluppo</span><span class="sxs-lookup"><span data-stu-id="1a084-105">2. Getting Unity ready for development</span></span>

<span data-ttu-id="1a084-106">In questa esercitazione si apprenderà come preparare e configurare Unity per lo sviluppo di applicazioni, tra cui importare il Toolkit di realtà mista, configurare le impostazioni di compilazione e preparare la scena.</span><span class="sxs-lookup"><span data-stu-id="1a084-106">In this tutorial, you will learn how to prepare and configure Unity for application development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing your scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="1a084-107">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="1a084-107">Objectives</span></span>

* <span data-ttu-id="1a084-108">Configurare Unity per lo sviluppo di applicazioni</span><span class="sxs-lookup"><span data-stu-id="1a084-108">Configure Unity for application development</span></span>
* <span data-ttu-id="1a084-109">Importare Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="1a084-109">Import the Mixed Reality Toolkit</span></span>
* <span data-ttu-id="1a084-110">Preparare la scena del progetto</span><span class="sxs-lookup"><span data-stu-id="1a084-110">Prepare your project scene</span></span>

## <a name="instructions"></a><span data-ttu-id="1a084-111">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="1a084-111">Instructions</span></span>

1. <span data-ttu-id="1a084-112">Scaricare e salvare il pacchetto Mixed Reality Toolkit Foundation Unity facendo clic [qui.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="1a084-112">Download and save the Mixed Reality Toolkit Foundation unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)</span></span>

2. <span data-ttu-id="1a084-113">In Unity fare clic sul menu assets e selezionare Import Package, quindi fare clic su Custom Package.</span><span class="sxs-lookup"><span data-stu-id="1a084-113">In Unity, click the Assets menu and select Import Package, then click on Custom Package.</span></span>

    ![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="1a084-115">Selezionare il pacchetto Unity appena scaricato dal collegamento fornito nel passaggio 1.</span><span class="sxs-lookup"><span data-stu-id="1a084-115">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="1a084-116">Una volta visualizzata la finestra popup importa in Unity, fare clic sul pulsante Import (importa) per avviare l'importazione del MRTK.</span><span class="sxs-lookup"><span data-stu-id="1a084-116">Once the import pop-up window appears in Unity, click the Import button to begin importing the MRTK.</span></span> <span data-ttu-id="1a084-117">Questa operazione può richiedere alcuni minuti.</span><span class="sxs-lookup"><span data-stu-id="1a084-117">This may take several minutes.</span></span>

    ![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

    >[!NOTE]
    ><span data-ttu-id="1a084-119">Il pacchetto scaricato si trova nella cartella locale in cui è stato salvato il file.</span><span class="sxs-lookup"><span data-stu-id="1a084-119">The downloaded package is in your local folder, where you have saved the file.</span></span> <span data-ttu-id="1a084-120">L'immagine precedente non rappresenta la posizione in cui si troverà il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="1a084-120">The image above does not portray where you will find the package.</span></span>

4. <span data-ttu-id="1a084-121">Creare una nuova scena.</span><span class="sxs-lookup"><span data-stu-id="1a084-121">Create a new scene.</span></span> <span data-ttu-id="1a084-122">Questa operazione può essere eseguita facendo clic su file e selezionando nuova scena.</span><span class="sxs-lookup"><span data-stu-id="1a084-122">This can be done by clicking File and selecting New Scene".</span></span> <span data-ttu-id="1a084-123">Salvarlo come HLSharedProjectMain.</span><span class="sxs-lookup"><span data-stu-id="1a084-123">Save it as HLSharedProjectMain.</span></span>

    <span data-ttu-id="1a084-124">È possibile che venga visualizzato un popup simile all'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="1a084-124">You may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="1a084-125">Per il momento, fare clic su No.</span><span class="sxs-lookup"><span data-stu-id="1a084-125">For now, click No.</span></span>
    <span data-ttu-id="1a084-126">![Module3Chapter2note1im](images/module3chapter2note1im.PNG)</span><span class="sxs-lookup"><span data-stu-id="1a084-126">![Module3Chapter2note1im](images/module3chapter2note1im.PNG)</span></span>

5. <span data-ttu-id="1a084-127">In Mixed Reality Toolkit fare clic su Aggiungi a scena e configurare.</span><span class="sxs-lookup"><span data-stu-id="1a084-127">Under Mixed Reality Toolkit, click on Add to Scene and Configure.</span></span>

    ![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="1a084-129">Una volta completato, viene visualizzato un nuovo file di configurazione che consente di scegliere di personalizzare il profilo.</span><span class="sxs-lookup"><span data-stu-id="1a084-129">Once that is complete, a new configuration file appears, giving you the choice to customize the profile.</span></span>

    ![Module2Chapter1step4ima](images/Module2Chapter1step4ima.PNG)

7. <span data-ttu-id="1a084-131">Selezionare il Toolkit di realtà mista (MRTK) dalla gerarchia.</span><span class="sxs-lookup"><span data-stu-id="1a084-131">Select Mixed-Reality Toolkit (MRTK) from the  hierarchy.</span></span> <span data-ttu-id="1a084-132">Nel pannello Inspector cercare lo script Mixed Reality Toolkit e premere il pulsante "copy & Customize", come illustrato nella figura seguente.</span><span class="sxs-lookup"><span data-stu-id="1a084-132">In the inspector panel, look for the Mixed Reality Toolkit Script and press the "Copy & Customize" button  as shown in the figure below.</span></span>  <span data-ttu-id="1a084-133">Un pop verrà visualizzato dopo questo e selezionare l'opzione Clona nel menu a comparsa.</span><span class="sxs-lookup"><span data-stu-id="1a084-133">A pop will appear after this and select clone option in the pop up menu.</span></span>

    ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

    ![Module3Chapter2step6imd](images/module3chapter2step6imd.PNG)

8. <span data-ttu-id="1a084-136">Scorrere verso il basso e deselezionare Abilita sistema di diagnostica se si desidera nascondere la finestra di diagnostica.</span><span class="sxs-lookup"><span data-stu-id="1a084-136">Scroll down and uncheck Enable Diagnostics system if you want to hide the diagnostics window.</span></span> <span data-ttu-id="1a084-137">È consigliabile mantenere la finestra di diagnostica abilitata durante lo sviluppo di applicazioni per monitorare le prestazioni e quindi disabilitarla durante le dimostrazioni di produzione o di applicazioni.</span><span class="sxs-lookup"><span data-stu-id="1a084-137">We recommend keeping the diagnostics window enabled during application development to monitor performance, and then disabling it during production or application demonstrations.</span></span> 

    ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

9. <span data-ttu-id="1a084-139">Per aprire le impostazioni di compilazione, premere CTRL + MAIUSC + B o passare a file-> impostazioni di compilazione.</span><span class="sxs-lookup"><span data-stu-id="1a084-139">Open the build settings by pressing control+shift+B or going to File->Build Settings.</span></span> <span data-ttu-id="1a084-140">Si noti che il programma è attualmente impostato nel computer, Mac e piattaforma autonoma Linux.</span><span class="sxs-lookup"><span data-stu-id="1a084-140">Notice that the program is currently set under the PC, Mac and Linux standalone platform.</span></span> <span data-ttu-id="1a084-141">Per lo sviluppo HoloLens 2, impostare la piattaforma da piattaforma UWP (Universal Windows Platform).</span><span class="sxs-lookup"><span data-stu-id="1a084-141">For HoloLens 2 development, set the platform to be Universal Windows Platform.</span></span> <span data-ttu-id="1a084-142">Selezionarlo e fare clic su switch Platform.</span><span class="sxs-lookup"><span data-stu-id="1a084-142">Select it and click Switch Platform.</span></span>

    ![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

10. <span data-ttu-id="1a084-144">Al termine, fare clic sulla casella denominata Aggiungi scene aperte.</span><span class="sxs-lookup"><span data-stu-id="1a084-144">Once complete, click the box called Add Open Scenes.</span></span> <span data-ttu-id="1a084-145">Passare ora al pannello Inspector e verificare che la casella di controllo a destra della realtà virtuale supportata (come illustrato nell'immagine seguente) sia selezionata.</span><span class="sxs-lookup"><span data-stu-id="1a084-145">Now go to the Inspector panel and ensure that the check box to the right of Virtual Reality Supported (as shown in the image below) is checked.</span></span> <span data-ttu-id="1a084-146">Assicurarsi inoltre che sia selezionata anche la casella di controllo accanto a Scenes/HLSharedProjectMain, come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="1a084-146">Also ensure that the check box next to scenes/HLSharedProjectMain is also checked, as shown in the image below.</span></span>

    ![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

11. <span data-ttu-id="1a084-148">Nella sezione impostazioni di pubblicazione del pannello Inspector scorrere fino a funzionalità e verificare che le caselle di controllo seguenti siano contrassegnate:</span><span class="sxs-lookup"><span data-stu-id="1a084-148">Under the Publishing Settings section in the Inspector panel, scroll down to Capabilities and ensure the following check boxes are marked:</span></span>

    ![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

12. <span data-ttu-id="1a084-150">Importare i pacchetti personalizzati elencati:</span><span class="sxs-lookup"><span data-stu-id="1a084-150">Import the listed custom packages:</span></span>

    <span data-ttu-id="1a084-151">a.</span><span class="sxs-lookup"><span data-stu-id="1a084-151">a.</span></span> <span data-ttu-id="1a084-152">[AzureSpatialAnchors. file unitypackage Tools](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.0.0/AzureSpatialAnchors.unitypackage) (versione 2.0.0)</span><span class="sxs-lookup"><span data-stu-id="1a084-152">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.0.0/AzureSpatialAnchors.unitypackage) (version 2.0.0)</span></span>

    <span data-ttu-id="1a084-153">b.</span><span class="sxs-lookup"><span data-stu-id="1a084-153">b.</span></span> [<span data-ttu-id="1a084-154">MRTK. HoloLens2. Unity. Esercitations. assets. GettingStarted. 2.1.0.1. file unitypackage Tools</span><span class="sxs-lookup"><span data-stu-id="1a084-154">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.1.0.1.unitypackage)

    <span data-ttu-id="1a084-155">c.</span><span class="sxs-lookup"><span data-stu-id="1a084-155">c.</span></span> [<span data-ttu-id="1a084-156">MRTK. HoloLens2. Unity. Esercitations. assets. AzureSpatialAnchors. 2.1.0.1. file unitypackage Tools</span><span class="sxs-lookup"><span data-stu-id="1a084-156">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.1.0.1.unitypackage)

    <span data-ttu-id="1a084-157">d.</span><span class="sxs-lookup"><span data-stu-id="1a084-157">d.</span></span> [<span data-ttu-id="1a084-158">MRTK. HoloLens2. Unity. Esercitations. assets. MultiUserCapabilities. 2.1.0.1. file unitypackage Tools</span><span class="sxs-lookup"><span data-stu-id="1a084-158">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage)

    >[!TIP]
    ><span data-ttu-id="1a084-159">Per un promemoria su come configurare un progetto Unity per gli ancoraggi spaziali di Azure, è possibile fare riferimento all'esercitazione [Introduzione all'ancoraggio spaziale](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) di Azure che fa parte della serie di esercitazioni sugli [ancoraggi spaziali di Azure](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) .</span><span class="sxs-lookup"><span data-stu-id="1a084-159">For a reminder on how to configure a Unity project for Azure Spatial Anchors, you can refer to the [Getting started with Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) tutorial which is part of the the [Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) tutorial series.</span></span>

    ![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

13. <span data-ttu-id="1a084-161">Nel pannello progetto passare alla cartella prefabbricates.</span><span class="sxs-lookup"><span data-stu-id="1a084-161">In the Project panel, go to the Prefabs folder.</span></span> <span data-ttu-id="1a084-162">Nei passaggi seguenti vengono implementati alcuni prefabbricati nella scena.</span><span class="sxs-lookup"><span data-stu-id="1a084-162">In the following steps, you will implement a few prefabs into the scene.</span></span> <span data-ttu-id="1a084-163">Nella cartella prefabbricati, fare clic e trascinare la finestra prefabbricata, debug nella gerarchia.</span><span class="sxs-lookup"><span data-stu-id="1a084-163">In the Prefabs folder, click and drag the prefab, Debug Window into the hierarchy.</span></span> <span data-ttu-id="1a084-164">Al termine, salvare il progetto facendo clic su file, quindi su Salva o premere CTRL + S.</span><span class="sxs-lookup"><span data-stu-id="1a084-164">Once finished, save the project by clicking File, then Save or press Control+S.</span></span>

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

    <span data-ttu-id="1a084-166">È possibile che venga visualizzato un messaggio popup quando si fa clic sul prefabbricato, che richiede informazioni su TMP Essentials.</span><span class="sxs-lookup"><span data-stu-id="1a084-166">You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="1a084-167">Fare clic su Importa TMP Essentials in base alle esigenze.</span><span class="sxs-lookup"><span data-stu-id="1a084-167">Click Import TMP Essentials as they are needed.</span></span> <span data-ttu-id="1a084-168">Se viene visualizzato questo popup, potrebbe essere necessario eliminare il prefabbricato dalla gerarchia e trascinarlo nella gerarchia per evitare potenziali errori correlati al testo.</span><span class="sxs-lookup"><span data-stu-id="1a084-168">If this pop-up appears, you might need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>

    ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="1a084-170">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="1a084-170">Congratulations</span></span>

<span data-ttu-id="1a084-171">Il progetto Unity è ora pronto per Photon.</span><span class="sxs-lookup"><span data-stu-id="1a084-171">Your Unity Project is now ready for Photon.</span></span> <span data-ttu-id="1a084-172">Nelle esercitazioni riportate di seguito verrà creata questa scena e il progetto Unity per un'esperienza condivisa completa.</span><span class="sxs-lookup"><span data-stu-id="1a084-172">In the coming tutorials, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="1a084-173">[Esercitazione successiva: 3. connessione di più utenti](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="1a084-173">[Next tutorial: 3. Connecting multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>

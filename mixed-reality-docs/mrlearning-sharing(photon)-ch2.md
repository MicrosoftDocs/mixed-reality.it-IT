---
title: Esercitazioni sulle funzionalità multiutente - 2. Preparazione di Unity per lo sviluppo
description: Completa questo corso per imparare a implementare esperienze condivise multiutente all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: f7ae77d6978b5da860d890bcfe5b6f7c3d4640c8
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031233"
---
# <a name="2-getting-unity-ready-for-development"></a><span data-ttu-id="cdc7d-105">2. Preparazione di Unity per lo sviluppo</span><span class="sxs-lookup"><span data-stu-id="cdc7d-105">2. Getting Unity ready for development</span></span>

<span data-ttu-id="cdc7d-106">In questa esercitazione imparerai a preparare e configurare Unity per lo sviluppo di applicazioni, incluse l'importazione di Mixed Reality Toolkit, la configurazione delle impostazioni di compilazione e la preparazione della scena.</span><span class="sxs-lookup"><span data-stu-id="cdc7d-106">In this tutorial, you will learn how to prepare and configure Unity for application development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing your scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="cdc7d-107">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="cdc7d-107">Objectives</span></span>

* <span data-ttu-id="cdc7d-108">Configurare Unity per lo sviluppo di applicazioni</span><span class="sxs-lookup"><span data-stu-id="cdc7d-108">Configure Unity for application development</span></span>
* <span data-ttu-id="cdc7d-109">Importare Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="cdc7d-109">Import the Mixed Reality Toolkit</span></span>
* <span data-ttu-id="cdc7d-110">Preparare la scena del progetto</span><span class="sxs-lookup"><span data-stu-id="cdc7d-110">Prepare your project scene</span></span>

## <a name="instructions"></a><span data-ttu-id="cdc7d-111">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="cdc7d-111">Instructions</span></span>

1. <span data-ttu-id="cdc7d-112">Scarica e salva il pacchetto Mixed Reality Toolkit Foundation per Unity facendo clic [qui](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="cdc7d-112">Download and save the Mixed Reality Toolkit Foundation unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage)</span></span>

2. <span data-ttu-id="cdc7d-113">In Unity fai clic sul menu Assets (Asset), scegli Import Package (Importa pacchetto) e quindi Custom Package (Pacchetto personalizzato).</span><span class="sxs-lookup"><span data-stu-id="cdc7d-113">In Unity, click the Assets menu and select Import Package, then click on Custom Package.</span></span>

    ![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="cdc7d-115">Seleziona il pacchetto per Unity scaricato dal collegamento fornito nel passaggio 1.</span><span class="sxs-lookup"><span data-stu-id="cdc7d-115">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="cdc7d-116">Dopo che la finestra popup di importazione è stata visualizzata in Unity, fai clic sul pulsante Import (Importa) per iniziare a importare MRTK.</span><span class="sxs-lookup"><span data-stu-id="cdc7d-116">Once the import pop-up window appears in Unity, click the Import button to begin importing the MRTK.</span></span> <span data-ttu-id="cdc7d-117">Questa operazione può richiedere alcuni minuti.</span><span class="sxs-lookup"><span data-stu-id="cdc7d-117">This may take several minutes.</span></span>

    ![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

    >[!NOTE]
    ><span data-ttu-id="cdc7d-119">Il pacchetto scaricato si trova nella cartella locale in cui hai salvato il file.</span><span class="sxs-lookup"><span data-stu-id="cdc7d-119">The downloaded package is in your local folder, where you have saved the file.</span></span> <span data-ttu-id="cdc7d-120">L'immagine riportata sopra non indica la posizione in cui troverai il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="cdc7d-120">The image above does not portray where you will find the package.</span></span>

    <span data-ttu-id="cdc7d-121">Dopo che il pacchetto è stato importato, dovrebbe venire visualizzata la finestra MRTK Project Configurator (Configuratore del progetto MRTK).</span><span class="sxs-lookup"><span data-stu-id="cdc7d-121">After the package has been imported, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="cdc7d-122">In caso contrario, apri tale finestra scegliendo Mixed Reality Toolkit > Utilities > Configure Unity Project (Mixed Reality Toolkit > Utilità > Configura progetto Unity) dal menu Unity.</span><span class="sxs-lookup"><span data-stu-id="cdc7d-122">If it does not, open it by selecting Mixed Reality Toolkit > Utilities > Configure Unity Project in the Unity menu.</span></span>

    <span data-ttu-id="cdc7d-123">Nella finestra MRTK Project Configurator (Configuratore del progetto MRTK) espandi la sezione Modify Configurations (Modifica configurazioni), deseleziona la casella di controllo Enable MSBuild for Unity (Abilita MSBuild per Unity), verifica che tutte le altre opzioni siano selezionate e fai clic sul pulsante Apply (Applica) per applicare le impostazioni.</span><span class="sxs-lookup"><span data-stu-id="cdc7d-123">In the MRTK Project Configurator window, expand the Modify Configurations section, uncheck the Enable MSBuild for Unity checkbox, ensure all other options are checked, and click the Apply button to apply the settings.</span></span>

    ![Module3Chapter2note1im](images/module3chapter2note1im-missing01.png)

    > [!CAUTION]
    > <span data-ttu-id="cdc7d-125">MSBuild per Unity potrebbe non supportare tutti gli SDK che userai ed essere difficile da disabilitare dopo che è stato abilitato.</span><span class="sxs-lookup"><span data-stu-id="cdc7d-125">MSBuild for Unity may not support all SDKs you will be using and can be challenging to disable after it has been enabled.</span></span> <span data-ttu-id="cdc7d-126">Di conseguenza, è consigliabile non abilitare MSBuild per Unity.</span><span class="sxs-lookup"><span data-stu-id="cdc7d-126">Consequently, it is strongly recommended to not enable MSBuild for Unity.</span></span>
    
4. <span data-ttu-id="cdc7d-127">Crea una nuova scena.</span><span class="sxs-lookup"><span data-stu-id="cdc7d-127">Create a new scene.</span></span> <span data-ttu-id="cdc7d-128">A tale scopo, fai clic su File e scegli New Scene (Nuova scena).</span><span class="sxs-lookup"><span data-stu-id="cdc7d-128">This can be done by clicking File and selecting New Scene".</span></span> <span data-ttu-id="cdc7d-129">Salva la scena con il nome HLSharedProjectMain.</span><span class="sxs-lookup"><span data-stu-id="cdc7d-129">Save it as HLSharedProjectMain.</span></span>

5. <span data-ttu-id="cdc7d-130">In Mixed Reality Toolkit fai clic su Add to Scene and Configure (Aggiungi alla scena e configura).</span><span class="sxs-lookup"><span data-stu-id="cdc7d-130">Under Mixed Reality Toolkit, click on Add to Scene and Configure.</span></span>

    ![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="cdc7d-132">Al termine, seleziona Mixed-Reality Toolkit (MRTK) nella gerarchia.</span><span class="sxs-lookup"><span data-stu-id="cdc7d-132">Once that is complete, select Mixed-Reality Toolkit (MRTK) from the hierarchy.</span></span> <span data-ttu-id="cdc7d-133">Nel riquadro Inspector (Controllo) modifica il profilo di configurazione di MRTK in DefaultHoloLens2ConfigurationProfile.</span><span class="sxs-lookup"><span data-stu-id="cdc7d-133">In the inspector panel, change the MRTK configuration profile to DefaultHoloLens2ConfigurationProfile.</span></span>

    ![Module2Chapter1step4ima](images/Module2Chapter1step4ima-missing01.png)

7. <span data-ttu-id="cdc7d-135">Seleziona Mixed-Reality Toolkit (MRTK) nella gerarchia.</span><span class="sxs-lookup"><span data-stu-id="cdc7d-135">Select Mixed-Reality Toolkit (MRTK) from the  hierarchy.</span></span> <span data-ttu-id="cdc7d-136">Nel riquadro Inspector (Controllo) cerca Mixed Reality Toolkit (Script) e premi il pulsante "Copy & Customize" (Copia e personalizza), come illustrato nella figura seguente.</span><span class="sxs-lookup"><span data-stu-id="cdc7d-136">In the inspector panel, look for the Mixed Reality Toolkit Script and press the "Copy & Customize" button  as shown in the figure below.</span></span>  <span data-ttu-id="cdc7d-137">Successivamente verrà visualizzata una finestra popup. Seleziona l'opzione Clone (Clona) nel menu a comparsa.</span><span class="sxs-lookup"><span data-stu-id="cdc7d-137">A pop will appear after this and select clone option in the pop up menu.</span></span>

    ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

    ![Module3Chapter2step6imd](images/module3chapter2step6imd.PNG)

8. <span data-ttu-id="cdc7d-140">Scorri verso il basso e deseleziona Enable Diagnostics System (Abilita sistema di diagnostica) per nascondere la finestra di diagnostica.</span><span class="sxs-lookup"><span data-stu-id="cdc7d-140">Scroll down and uncheck Enable Diagnostics system if you want to hide the diagnostics window.</span></span> <span data-ttu-id="cdc7d-141">Consigliamo di mantenere abilitata la finestra di diagnostica durante lo sviluppo delle applicazioni per monitorare le prestazioni e quindi disabilitarla durante la produzione o le dimostrazioni delle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="cdc7d-141">We recommend keeping the diagnostics window enabled during application development to monitor performance, and then disabling it during production or application demonstrations.</span></span> 

    ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

9. <span data-ttu-id="cdc7d-143">Per aprire le impostazioni di compilazione, premi CTRL+MAIUSC+B oppure passa a File->Build Settings (Impostazioni di compilazione).</span><span class="sxs-lookup"><span data-stu-id="cdc7d-143">Open the build settings by pressing control+shift+B or going to File->Build Settings.</span></span> <span data-ttu-id="cdc7d-144">Si noti che il programma è attualmente impostato nella piattaforma autonoma PC, Mac e Linux.</span><span class="sxs-lookup"><span data-stu-id="cdc7d-144">Notice that the program is currently set under the PC, Mac and Linux standalone platform.</span></span> <span data-ttu-id="cdc7d-145">Per lo sviluppo HoloLens 2, imposta la piattaforma Universal Windows Platform.</span><span class="sxs-lookup"><span data-stu-id="cdc7d-145">For HoloLens 2 development, set the platform to be Universal Windows Platform.</span></span> <span data-ttu-id="cdc7d-146">Selezionala e fai clic su Switch Platform (Cambia piattaforma).</span><span class="sxs-lookup"><span data-stu-id="cdc7d-146">Select it and click Switch Platform.</span></span>

    ![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

10. <span data-ttu-id="cdc7d-148">Al termine, fai clic sulla casella denominata Add Open Scenes (Aggiungi scene aperte).</span><span class="sxs-lookup"><span data-stu-id="cdc7d-148">Once complete, click the box called Add Open Scenes.</span></span> <span data-ttu-id="cdc7d-149">Passa ora al riquadro Inspector (Controllo) e verifica che la casella di controllo a destra di Virtual Reality Supported (Realtà virtuale supportata) (come illustrato nell'immagine seguente) sia selezionata.</span><span class="sxs-lookup"><span data-stu-id="cdc7d-149">Now go to the Inspector panel and ensure that the check box to the right of Virtual Reality Supported (as shown in the image below) is checked.</span></span> <span data-ttu-id="cdc7d-150">Verifica inoltre che sia selezionata anche la casella di controllo accanto a Scenes/HLSharedProjectMain, come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="cdc7d-150">Also ensure that the check box next to scenes/HLSharedProjectMain is also checked, as shown in the image below.</span></span>

    ![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

11. <span data-ttu-id="cdc7d-152">Nella sezione Publishing Settings (Impostazioni di pubblicazione) del riquadro Inspector (Controllo) scorri verso il basso fino a Capabilities (Funzionalità) e verifica che siano selezionate le caselle di controllo seguenti:</span><span class="sxs-lookup"><span data-stu-id="cdc7d-152">Under the Publishing Settings section in the Inspector panel, scroll down to Capabilities and ensure the following check boxes are marked:</span></span>

    ![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

12. <span data-ttu-id="cdc7d-154">Importa i pacchetti personalizzati elencati:</span><span class="sxs-lookup"><span data-stu-id="cdc7d-154">Import the listed custom packages:</span></span>

    * <span data-ttu-id="cdc7d-155">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (versione 2.1.1)</span><span class="sxs-lookup"><span data-stu-id="cdc7d-155">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (version 2.1.1)</span></span>
    * [<span data-ttu-id="cdc7d-156">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span><span class="sxs-lookup"><span data-stu-id="cdc7d-156">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)
    * [<span data-ttu-id="cdc7d-157">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="cdc7d-157">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage)
    * [<span data-ttu-id="cdc7d-158">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage</span><span class="sxs-lookup"><span data-stu-id="cdc7d-158">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage)

    >[!TIP]
    ><span data-ttu-id="cdc7d-159">Per rivedere la procedura di configurazione di un progetto Unity per Ancoraggi nello spazio di Azure, vedi l'esercitazione [Introduzione ad Ancoraggi nello spazio di Azure](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) che fa parte della serie di esercitazioni relative ad [Ancoraggi dello spazio di Azure](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1).</span><span class="sxs-lookup"><span data-stu-id="cdc7d-159">For a reminder on how to configure a Unity project for Azure Spatial Anchors, you can refer to the [Getting started with Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) tutorial which is part of the the [Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) tutorial series.</span></span>


13. <span data-ttu-id="cdc7d-160">Nel riquadro Project (Progetto) passa alla cartella Prefabs (Prefab).</span><span class="sxs-lookup"><span data-stu-id="cdc7d-160">In the Project panel, go to the Prefabs folder.</span></span> <span data-ttu-id="cdc7d-161">Nei passaggi seguenti implementerai alcuni prefab nella scena.</span><span class="sxs-lookup"><span data-stu-id="cdc7d-161">In the following steps, you will implement a few prefabs into the scene.</span></span> <span data-ttu-id="cdc7d-162">Nella cartella Prefabs (Prefab) fai clic e trascina il prefab DebugWindow nella gerarchia.</span><span class="sxs-lookup"><span data-stu-id="cdc7d-162">In the Prefabs folder, click and drag the prefab, Debug Window into the hierarchy.</span></span> <span data-ttu-id="cdc7d-163">Al termine, salva il progetto facendo clic su File e quindi su Save (Salva) oppure premendo CTRL+S.</span><span class="sxs-lookup"><span data-stu-id="cdc7d-163">Once finished, save the project by clicking File, then Save or press Control+S.</span></span>

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

    <span data-ttu-id="cdc7d-165">Potrai notare che, facendo clic sul prefab, viene visualizzata una finestra popup in cui vengono chieste informazioni su TMP Essentials.</span><span class="sxs-lookup"><span data-stu-id="cdc7d-165">You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="cdc7d-166">Fai clic su Import TMP Essentials (Importa TMP Essentials) perché è necessario.</span><span class="sxs-lookup"><span data-stu-id="cdc7d-166">Click Import TMP Essentials as they are needed.</span></span> <span data-ttu-id="cdc7d-167">Se viene visualizzata questa finestra popup, potrebbe essere necessario eliminare il prefab dalla gerarchia e ritrascinarlo nella gerarchia per evitare potenziali errori correlati al testo.</span><span class="sxs-lookup"><span data-stu-id="cdc7d-167">If this pop-up appears, you might need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>

    ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="cdc7d-169">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="cdc7d-169">Congratulations</span></span>

<span data-ttu-id="cdc7d-170">Il progetto Unity è ora pronto per Photon.</span><span class="sxs-lookup"><span data-stu-id="cdc7d-170">Your Unity Project is now ready for Photon.</span></span> <span data-ttu-id="cdc7d-171">Nelle prossime esercitazioni svilupperemo questa scena e il progetto Unity per la realizzazione di un'esperienza condivisa completa.</span><span class="sxs-lookup"><span data-stu-id="cdc7d-171">In the coming tutorials, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="cdc7d-172">[Esercitazione successiva: 3. Connessione di più utenti](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="cdc7d-172">[Next tutorial: 3. Connecting multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>

---
title: Esercitazioni su Ancoraggi nello spazio di Azure - 5. Ancoraggi nello spazio di Azure per Android e iOS
description: Completare questo corso per imparare a distribuire un progetto Unity con Mixed Reality Toolkit e Ancoraggi nello spazio di Azure in Android e iOS.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, android, ios
ms.localizationpriority: high
ms.openlocfilehash: 8c63204948b3e4aa3d25e5b2ca948798726f0838
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376543"
---
# <a name="5-azure-spatial-anchors-for-android-and-ios"></a><span data-ttu-id="5f5e4-105">5. Ancoraggi nello spazio di Azure per Android e iOS</span><span class="sxs-lookup"><span data-stu-id="5f5e4-105">5. Azure Spatial Anchors for Android and iOS</span></span>

<span data-ttu-id="5f5e4-106">Questa esercitazione illustra come compilare il progetto nei dispositivi Android e iOS usando AR Foundation, ARCore XR Plugin e ARKit XR Plugin.</span><span class="sxs-lookup"><span data-stu-id="5f5e4-106">In this tutorial, you will learn how to build your project to Android and iOS devices using AR Foundation, ARCore XR Plugin, and ARKit XR Plugin.</span></span>

## <a name="objectives"></a><span data-ttu-id="5f5e4-107">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="5f5e4-107">Objectives</span></span>

* <span data-ttu-id="5f5e4-108">Imparare a compilare il progetto in un dispositivo Android usando Unity AR Foundation e ARCore XR Plugin</span><span class="sxs-lookup"><span data-stu-id="5f5e4-108">Learn how to build your project to your Android device using Unity's AR Foundation and ARCore XR Plugin</span></span>
* <span data-ttu-id="5f5e4-109">Imparare a compilare il progetto in un dispositivo iOS usando Unity AR Foundation e ARKit XR Plugin</span><span class="sxs-lookup"><span data-stu-id="5f5e4-109">Learn how to build your project to your iOS device using Unity's AR Foundation and ARKit XR Plugin</span></span>

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="5f5e4-110">Installazione di pacchetti di Unity incorporati</span><span class="sxs-lookup"><span data-stu-id="5f5e4-110">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="5f5e4-111">In questa sezione verrà eseguito l'aggiornamento e l'installazione dei seguenti pacchetti incorporati:</span><span class="sxs-lookup"><span data-stu-id="5f5e4-111">In this section, you will upgrade and install the following inbuilt packages:</span></span>

* <span data-ttu-id="5f5e4-112">AR Foundation 3.1.3</span><span class="sxs-lookup"><span data-stu-id="5f5e4-112">AR Foundation 3.1.3</span></span>
* <span data-ttu-id="5f5e4-113">Legacy Input Helpers 2.1.4</span><span class="sxs-lookup"><span data-stu-id="5f5e4-113">Legacy Input Helpers 2.1.4</span></span>
* <span data-ttu-id="5f5e4-114">ARCore XR Plugin 3.1.3 per il supporto Android</span><span class="sxs-lookup"><span data-stu-id="5f5e4-114">ARCore XR Plugin 3.1.3 for Android support</span></span>
* <span data-ttu-id="5f5e4-115">ARKit XR plugin 3.1.3 per il supporto iOS</span><span class="sxs-lookup"><span data-stu-id="5f5e4-115">ARKit XR plugin 3.1.3 for iOS support</span></span>

> [!CAUTION]
> <span data-ttu-id="5f5e4-116">Non tutte le versioni sono compatibili con MRTK e solo alcune versioni interagiscono tra loro, quindi è importante assicurarsi di installare le versioni esatte elencate sopra.</span><span class="sxs-lookup"><span data-stu-id="5f5e4-116">Not all version are compatible with MRTK and only certain version works together, so make sure you install the exact versions listed above.</span></span>

<span data-ttu-id="5f5e4-117">Scegliere **Window** (Finestra)  > **Package Manager** (Gestione pacchetti) dal menu Unity per aprire la finestra Package Manager(Gestione pacchetti), quindi selezionare **AR Foundation** > **3.1.3** e fare clic sul pulsante **Update to 3.1.3** (Aggiorna a 3.1.3) per aggiornare il pacchetto:</span><span class="sxs-lookup"><span data-stu-id="5f5e4-117">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** > **3.1.3** and click the **Update to 3.1.3** button to update the package:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section1-step1-1.png)

<span data-ttu-id="5f5e4-119">Seguire lo stesso processo per importare i pacchetti rimanenti, in base alle esigenze.</span><span class="sxs-lookup"><span data-stu-id="5f5e4-119">Follow the same process to import the remaining packages as needed.</span></span>

> [!NOTE]
> <span data-ttu-id="5f5e4-120">Se sviluppi il progetto per Android, non è necessario installare il pacchetto ARKit XR Plugin.</span><span class="sxs-lookup"><span data-stu-id="5f5e4-120">If you are developing this project for Android, there is no need to install the ARKit XR Plugin package.</span></span> <span data-ttu-id="5f5e4-121">Analogamente, se sviluppi il progetto per iOS, non è necessario installare ARCore XR Plugin.</span><span class="sxs-lookup"><span data-stu-id="5f5e4-121">Similarly, if you are developing this project for iOS, you do not need to install the ARCore XR Plugin.</span></span>

## <a name="configure-mrtk-for-ar-foundation-camera"></a><span data-ttu-id="5f5e4-122">Configurare MRTK per AR Foundation Camera</span><span class="sxs-lookup"><span data-stu-id="5f5e4-122">Configure MRTK for AR Foundation Camera</span></span>

<span data-ttu-id="5f5e4-123">In questa sezione verrà illustrato come configurare MRTK per la distribuzione in un dispositivo mobile.</span><span class="sxs-lookup"><span data-stu-id="5f5e4-123">In this section, you will learn how to configure MRTK for deploying to a mobile device.</span></span>

<span data-ttu-id="5f5e4-124">Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **MixedRealityToolkit**.</span><span class="sxs-lookup"><span data-stu-id="5f5e4-124">In the Hierarchy window, select the **MixedRealityToolkit** object.</span></span> <span data-ttu-id="5f5e4-125">Quindi, nella finestra Inspector (Controllo) selezionare la scheda **Camera** (Fotocamera), clonare i profilo della fotocamera e assegnare un nome adatto, ad esempio **AzureSpatialAnchors_ARCameraProfile**:</span><span class="sxs-lookup"><span data-stu-id="5f5e4-125">Then in the Inspector window, select the **Camera** tab, clone the camera profile, and give it a suitable name, for example, **AzureSpatialAnchors_ARCameraProfile**:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="5f5e4-127">Per rivedere la procedura di clonazione dei profili MRTK, fare riferimento alle istruzioni contenute in [Configurazione dei profili di Mixed Reality Toolkit](mr-learning-base-03.md).</span><span class="sxs-lookup"><span data-stu-id="5f5e4-127">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the Mixed Reality Toolkit profiles](mr-learning-base-03.md) instructions.</span></span>

<span data-ttu-id="5f5e4-128">Con la scheda **Camera** (Fotocamera) ancora selezionata nella finestra Inspector (Controllo), espandere **Camera Setting Providers** (Provider impostazioni fotocamera) e fare clic sul pulsante **+ Add Camera Setting Provider** (+ Aggiungi provider impostazioni fotocamera), quindi espandere **New data provider 1** (Nuovo provider di dati 1):</span><span class="sxs-lookup"><span data-stu-id="5f5e4-128">With the **Camera** tab still selected in the Inspector window, expand the **Camera Setting Providers** and click the **+ Add Camera Setting Provider** button, then expand the newly added **New data provider 1**:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-2.png)

<span data-ttu-id="5f5e4-130">Usando l'elenco a discesa **Type** (Tipo), cambiare il tipo in **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > **UnityARCameraSettings**:</span><span class="sxs-lookup"><span data-stu-id="5f5e4-130">Using the **Type** dropdown, change the type to **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > **UnityARCameraSettings**:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-3.png)

<span data-ttu-id="5f5e4-132">Con l'oggetto **MixedRealityToolkit** ancora selezionato nella finestra Hierarchy (Gerarchia), usare il pulsante **Add Component** (Aggiungi componente) nella finestra Inspector (Controllo) per aggiungere i componenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="5f5e4-132">With the **MixedRealityToolkit** object still selected in the Hierarchy window, use the **Add Component** button in the Inspector window to add the following components:</span></span>

* <span data-ttu-id="5f5e4-133">AR Anchor Manager (Script)</span><span class="sxs-lookup"><span data-stu-id="5f5e4-133">AR Anchor Manager (Script)</span></span>
* <span data-ttu-id="5f5e4-134">DisableDiagnosticsSystem (Script)</span><span class="sxs-lookup"><span data-stu-id="5f5e4-134">DisableDiagnosticsSystem (Script)</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-4.png)

> [!NOTE]
> <span data-ttu-id="5f5e4-136">Quando si aggiunge il componente AR Reference Point Manager (Script), viene aggiunto automaticamente il componente AR Session Origin (Script) perché è richiesto dal componente AR Reference Point Manager (Script).</span><span class="sxs-lookup"><span data-stu-id="5f5e4-136">When you add the AR Reference Point Manager (Script) component, the AR Session Origin (Script) component is automatically added because it is required by the AR Reference Point Manager (Script) component.</span></span>

## <a name="building-your-application-to-your-android-device"></a><span data-ttu-id="5f5e4-137">Compilazione dell'applicazione in un dispositivo Android</span><span class="sxs-lookup"><span data-stu-id="5f5e4-137">Building your application to your Android device</span></span>

<span data-ttu-id="5f5e4-138">In questa sezione verrà illustrato come configurare il progetto per la compilazione e la distribuzione in un dispositivo Android.</span><span class="sxs-lookup"><span data-stu-id="5f5e4-138">In this section, you will learn how to configure your project to build and deploy it to an Android device.</span></span>

<span data-ttu-id="5f5e4-139">Dal menu di Unity scegli **File** > **Build Settings** (Impostazioni di compilazione) per visualizzare la finestra corrispondente, quindi impostare la piattaforma su Android:</span><span class="sxs-lookup"><span data-stu-id="5f5e4-139">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window and then switch the platform to Android:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="5f5e4-141">Per rivedere la procedura per cambiare piattaforma di compilazione, fare riferimento alle istruzioni contenute in [Passaggio a un'altra piattaforma di compilazione](mr-learning-base-02.md#switching-the-build-platform).</span><span class="sxs-lookup"><span data-stu-id="5f5e4-141">For a reminder on how to switch build platform, you can refer to the [Switching the build platform](mr-learning-base-02.md#switching-the-build-platform) instructions.</span></span>

<span data-ttu-id="5f5e4-142">Chiudere la finestra Build Settings (Impostazioni di compilazione).</span><span class="sxs-lookup"><span data-stu-id="5f5e4-142">Close the Build Settings window.</span></span>

<span data-ttu-id="5f5e4-143">Nel menu di Unity selezionare **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Mixed Reality Toolkit > Utilità > Configura progetto Unity) per aprire la finestra **MRTK Project Configurator** (Configuratore progetto MRTK), verificare che tutte le opzioni siano selezionate, quindi fare clic sul pulsante **Apply** (Applica) per applicare le impostazioni:</span><span class="sxs-lookup"><span data-stu-id="5f5e4-143">In the Unity menu, select **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** to open the **MRTK Project Configurator** window, ensure all options are selected, then click the **Apply** button to apply the settings:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-2.png)

<span data-ttu-id="5f5e4-145">Dal menu Unity scegliere **Edit** > **Project Settings...** (Modifica > Impostazioni del progetto) per aprire la finestra Player Settings (Impostazioni lettore) e quindi individuare la sezione **Player** >  **Other Settings** (Lettore > Altre impostazioni), selezionare **Vulkan** e rimuoverlo facendo clic sul simbolo **"-"** :</span><span class="sxs-lookup"><span data-stu-id="5f5e4-145">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Other Settings** section, select **Vulkan** and remove it by clicking the **"-"** symbol:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-3.png)

<span data-ttu-id="5f5e4-147">Chiudere la finestra Player Settings (Impostazioni giocatore) e aprire di nuovo la finestra Build Settings (Impostazioni di compilazione).</span><span class="sxs-lookup"><span data-stu-id="5f5e4-147">Close the Player Settings window and open the Build Settings window again.</span></span>

<span data-ttu-id="5f5e4-148">Nella finestra Build Settings (Impostazioni di compilazione) fare clic sul pulsante **Add Open Scenes** (Aggiungi scene aperte) per aggiungere la scena corrente all'elenco **Scenes In Build** (Scene nella compilazione).</span><span class="sxs-lookup"><span data-stu-id="5f5e4-148">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list.</span></span> <span data-ttu-id="5f5e4-149">Quindi, usare un cavo USB, connettere il dispositivo Android al computer e selezionarlo nell'elenco a discesa **Run Device** (Esegui dispositivo):</span><span class="sxs-lookup"><span data-stu-id="5f5e4-149">Then, use a USB cable, connect your Android device to your computer and select it from the **Run Device** dropdown:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-4.png)

>[!NOTE]
> <span data-ttu-id="5f5e4-151">Se il dispositivo non è presente nell'elenco a discesa Run Device (Esegui dispositivo), potrebbe essere necessario premere il pulsante Refresh (Aggiorna) accanto all'elenco a discesa.</span><span class="sxs-lookup"><span data-stu-id="5f5e4-151">If your device does not appear in the Run Device dropdown, you might need to press the Refresh button next to the dropdown.</span></span>

<span data-ttu-id="5f5e4-152">Nella finestra delle impostazioni di compilazione fare clic sul pulsante **Build And Run** (Compila ed esegui) per aprire la finestra Build Android (Compila in Android).</span><span class="sxs-lookup"><span data-stu-id="5f5e4-152">In the Build Settings window, click the **Build And Run** button to open the Build Android window.</span></span>

<span data-ttu-id="5f5e4-153">Scegliere il percorso in cui archiviare la build, ad esempio _D:\MixedRealityLearning\Builds_, quindi assegnare un nome adeguato all'apk, ad esempio _MRTKTutorials-AzureSpatialAnchors_, e fare clic sul pulsante **Save** (Salva) per avviare il processo di compilazione:</span><span class="sxs-lookup"><span data-stu-id="5f5e4-153">Choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, then give the apk a suitable name, for example, _MRTKTutorials-AzureSpatialAnchors_, and click the **Save** button to start the build process:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-5.png)

> [!NOTE]
<span data-ttu-id="5f5e4-155">Se nella finestra della console Unity viene visualizzato un errore relativo ai moduli Android SDK, NDK o JDK, è necessario aprire Unity Hub e installare i moduli Android Build Support associati.</span><span class="sxs-lookup"><span data-stu-id="5f5e4-155">If you get any error in the Unity Console window related to Android SDK, NDK, or JDK modules, you need to open Unity Hub and install the associated Android Build Support modules.</span></span>

<span data-ttu-id="5f5e4-156">Al termine del processo di compilazione, le app dovrebbero essere caricate automaticamente nel dispositivo Android.</span><span class="sxs-lookup"><span data-stu-id="5f5e4-156">When the build process is complete, your apps should automatically load on your Android device.</span></span>

## <a name="building-your-application-to-your-ios-device"></a><span data-ttu-id="5f5e4-157">Compilazione dell'applicazione in un dispositivo iOS</span><span class="sxs-lookup"><span data-stu-id="5f5e4-157">Building your application to your iOS device</span></span>

<span data-ttu-id="5f5e4-158">In questa sezione verrà illustrato come configurare il progetto per la compilazione e la distribuzione in un dispositivo iOS.</span><span class="sxs-lookup"><span data-stu-id="5f5e4-158">In this section, you will learn how to configure your project, to build and deploy it to your iOS device.</span></span>

<span data-ttu-id="5f5e4-159">Dal menu di Unity scegli **File** > **Build Settings** (Impostazioni di compilazione) per visualizzare la finestra corrispondente e impostare la piattaforma su iOS:</span><span class="sxs-lookup"><span data-stu-id="5f5e4-159">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window and switch platform to iOS:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="5f5e4-161">Per rivedere la procedura per cambiare piattaforma di compilazione, fare riferimento alle istruzioni contenute in [Passaggio a un'altra piattaforma di compilazione](mr-learning-base-02.md#switching-the-build-platform).</span><span class="sxs-lookup"><span data-stu-id="5f5e4-161">For a reminder on how to switch build platform, you can refer to the [Switching the build platform](mr-learning-base-02.md#switching-the-build-platform) instructions.</span></span>

<span data-ttu-id="5f5e4-162">Chiudere la finestra Build Settings (Impostazioni di compilazione).</span><span class="sxs-lookup"><span data-stu-id="5f5e4-162">Close the Build Settings window.</span></span>

<span data-ttu-id="5f5e4-163">Nel menu di Unity selezionare **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Mixed Reality Toolkit > Utilità > Configura progetto Unity) per aprire la finestra **MRTK Project Configurator** (Configuratore progetto MRTK), verificare che tutte le opzioni siano selezionate, quindi fare clic sul pulsante **Apply** (Applica) per applicare le impostazioni:</span><span class="sxs-lookup"><span data-stu-id="5f5e4-163">In the Unity menu, select **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** to open the **MRTK Project Configurator** window, ensure all options are selected, then click the **Apply** button to apply the settings:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-2.png)

<span data-ttu-id="5f5e4-165">Dal menu Unity scegliere **Edit** > **Project Settings...** (Modifica > Impostazioni del progetto) per aprire la finestra Player Settings (Impostazioni lettore) e quindi individuare la sezione **Player** >  **Other Settings** (Lettore > Altre impostazioni), deselezionare la casella di controllo **Strip Engine Code** (Rimuovi codice motore) per disabilitarla:</span><span class="sxs-lookup"><span data-stu-id="5f5e4-165">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Other Settings** section, uncheck the **Strip Engine Code** checkbox to disable it:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-3.png)

<span data-ttu-id="5f5e4-167">Chiudere la finestra Player Settings (Impostazioni lettore) e aprire di nuovo la finestra **Build Settings** (Impostazioni di compilazione).</span><span class="sxs-lookup"><span data-stu-id="5f5e4-167">Close the Player Settings window and open the **Build Settings** window again.</span></span>

<span data-ttu-id="5f5e4-168">Nella finestra Build Settings (Impostazioni di compilazione) fare clic sul pulsante **Add Open Scenes** (Aggiungi scene aperte) per aggiungere la scena corrente all'elenco **Scenes In Build** (Scene nella compilazione):</span><span class="sxs-lookup"><span data-stu-id="5f5e4-168">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-4.png)

<span data-ttu-id="5f5e4-170">Nella finestra delle impostazioni di compilazione fare clic sul pulsante **Build** (Compila) per aprire la finestra Build iOS (Compila in iOS).</span><span class="sxs-lookup"><span data-stu-id="5f5e4-170">In the Build Settings window, click the **Build** button to open the Build iOS window.</span></span>

<span data-ttu-id="5f5e4-171">Scegliere un percorso appropriato in cui archiviare il progetto Xcode, ad esempio _D:\MixedRealityLearning\Builds_, creare una nuova cartella e assegnarle un nome adatto, ad esempio, _MRTKTutorials-AzureSpatialAnchors_, e quindi fare clic sul pulsante **Select Folder** (Seleziona cartella) per avviare il processo di compilazione:</span><span class="sxs-lookup"><span data-stu-id="5f5e4-171">Choose a suitable location to store your Xcode project, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _MRTKTutorials-AzureSpatialAnchors_, and then click the **Select Folder** button to start the build process:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-5.png)

<span data-ttu-id="5f5e4-173">Al termine del processo di compilazione, seguire le istruzioni in [Esportare il progetto Xcode](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) per informazioni su come distribuire il progetto Xcode in un dispositivo iOS.</span><span class="sxs-lookup"><span data-stu-id="5f5e4-173">When the build process is complete, follow the [Export the Xcode project](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) instructions to learn to deploy your Xcode project to your iOS device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="5f5e4-174">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="5f5e4-174">Congratulations</span></span>

<span data-ttu-id="5f5e4-175">In questa esercitazione è stato descritto come compilare il progetto nei dispositivi Android e iOS usando AR Foundation, ARCore XR Plugin e ARKit XR Plugin.</span><span class="sxs-lookup"><span data-stu-id="5f5e4-175">In this tutorial, you learned how to build your project to Android and iOS devices using AR Foundation, ARCore XR Plugin, and ARKit XR Plugin.</span></span>

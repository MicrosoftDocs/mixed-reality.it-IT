---
title: Esercitazioni su Ancoraggi nello spazio di Azure - 4. Ancoraggi nello spazio di Azure per Android e iOS
description: Completa questa esercitazione per imparare a implementare Azure Speech SDK in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 05/18/2020
ms.topic: article
keywords: realtà mista, unity, esercitazione, corso, hololens, azure, ancoraggi nello spazio
ms.localizationpriority: high
ms.openlocfilehash: a35f73ae5aee493182f0f4990aa345d990c3f513
ms.sourcegitcommit: e65f1463aec3c040a1cd042e61fc2bd156a42ff8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/26/2020
ms.locfileid: "83867623"
---
# <a name="4-azure-spatial-anchors-for-android-and-ios"></a><span data-ttu-id="bddd2-105">4. Ancoraggi nello spazio di Azure per Android e iOS</span><span class="sxs-lookup"><span data-stu-id="bddd2-105">4. Azure Spatial Anchors for Android and iOS</span></span>

<span data-ttu-id="bddd2-106">Questa esercitazione illustra come compilare il progetto nei dispositivi Android e iOS usando AR Foundation, ARCore XR Plugin e ARKit XR Plugin.</span><span class="sxs-lookup"><span data-stu-id="bddd2-106">In this tutorial, you will learn how to build your project to Android and iOS devices using AR Foundation, ARCore XR Plugin, and ARKit XR Plugin.</span></span>

## <a name="objectives"></a><span data-ttu-id="bddd2-107">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="bddd2-107">Objectives</span></span>

* <span data-ttu-id="bddd2-108">Imparare a compilare il progetto in un dispositivo Android usando Unity AR Foundation e ARCore XR Plugin.</span><span class="sxs-lookup"><span data-stu-id="bddd2-108">Learn how to build your project to Android device using Unity AR Foundation and ARCore XR Plugin.</span></span>
* <span data-ttu-id="bddd2-109">Imparare a compilare il progetto in un dispositivo iOS usando Unity AR Foundation e ARKit XR Plugin.</span><span class="sxs-lookup"><span data-stu-id="bddd2-109">Learn how to build your project to an iOS device using Unity AR Foundation and ARKit XR Plugin.</span></span>

[!NOTE] <span data-ttu-id="bddd2-110">Per completare questa esercitazione, è importante avere completato Esercitazioni su Ancoraggi nello spazio di Azure > [Introduzione ad Ancoraggi nello spazio di Azure](mrlearning-asa-ch1.md).</span><span class="sxs-lookup"><span data-stu-id="bddd2-110">To complete this tutorial, make sure you have completed Azure Spatial Anchors Tutorials -> [Getting started with Azure Spatial Anchors](mrlearning-asa-ch1.md).</span></span>

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="bddd2-111">Aggiunta di pacchetti di Unity incorporati</span><span class="sxs-lookup"><span data-stu-id="bddd2-111">Adding inbuilt Unity packages</span></span>

<span data-ttu-id="bddd2-112">In questa sezione installerai i pacchetti AR Foundation, ARCore XR Plugin e ARKit XR Plugin di Unity incorporati che sono necessari per supportare i dispositivi Android e iOS.</span><span class="sxs-lookup"><span data-stu-id="bddd2-112">In this section, you will install Unity's inbuilt AR Foundation, ARCore XR Plugin, and ARKit XR Plugin packages required to support Android and iOS devices.</span></span>

<span data-ttu-id="bddd2-113">Assicurati di installare le versioni corrette di questi pacchetti Unity indicate di seguito:</span><span class="sxs-lookup"><span data-stu-id="bddd2-113">Make sure you install the correct version of these Unity packages as listed below:</span></span>

* <span data-ttu-id="bddd2-114">**AR Foundation 2.1.4**</span><span class="sxs-lookup"><span data-stu-id="bddd2-114">**AR Foundation 2.1.4**</span></span>
* <span data-ttu-id="bddd2-115">**ARCore XR plugin 2.2.0 preview 2**</span><span class="sxs-lookup"><span data-stu-id="bddd2-115">**ARCore XR plugin 2.2.0 preview 2**</span></span>
* <span data-ttu-id="bddd2-116">**ARKit XR plugin 2.1.1**</span><span class="sxs-lookup"><span data-stu-id="bddd2-116">**ARKit XR plugin 2.1.1**</span></span>

[!NOTE] <span data-ttu-id="bddd2-117">Se sviluppi il progetto per Android, non è necessario installare il pacchetto ARKit XR Plugin.</span><span class="sxs-lookup"><span data-stu-id="bddd2-117">If you are developing this project for Android, there is no need to install the ARKit XR Plugin package.</span></span> <span data-ttu-id="bddd2-118">Analogamente, se sviluppi il progetto per iOS, non è necessario installare ARCore XR Plugin.</span><span class="sxs-lookup"><span data-stu-id="bddd2-118">Similarly, if you are developing this project for iOS, you do not need to install the ARCore XR Plugin.</span></span>

<span data-ttu-id="bddd2-119">Nel menu di Unity seleziona **Window** (Finestra) > **Package Manager** (Gestione pacchetti):</span><span class="sxs-lookup"><span data-stu-id="bddd2-119">In the Unity menu, select **Window** > **Package Manager**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-1.png)

<span data-ttu-id="bddd2-121">Potrebbero essere necessari alcuni secondi prima che tutti i pacchetti vengano visualizzati nell'elenco.</span><span class="sxs-lookup"><span data-stu-id="bddd2-121">It might take a few seconds before all packages appear in the list.</span></span> <span data-ttu-id="bddd2-122">Per visualizzare i pacchetti in anteprima, fai clic sull'opzione Advanced (Avanzate) e scegli **Show preview packages** (Mostra pacchetti in anteprima).</span><span class="sxs-lookup"><span data-stu-id="bddd2-122">Display preview packages by clicking on Advanced option and select "**Show preview packages.**"</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-2.png)

<span data-ttu-id="bddd2-124">Nella finestra Package Manager (Gestione pacchetti) seleziona **AR Foundation**. Tra le diverse versioni presenti, seleziona la versione 2.1.4, quindi aggiorna il pacchetto facendo clic sul pulsante **Update to 2.1.4** (Aggiorna a 2.1.4):</span><span class="sxs-lookup"><span data-stu-id="bddd2-124">In the Package Manager window, select **AR Foundation**, here you see many version and need to select version 2.1.4 and update the package by clicking the **Update to 2.1.4** button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-3.png)

<span data-ttu-id="bddd2-126">Per supportare i dispositivi Android, segui la stessa procedura per importare ARCore XR Plugin 2.2.0 preview 2.</span><span class="sxs-lookup"><span data-stu-id="bddd2-126">To support Android devices, follow the same process to import ARCore XR Plugin 2.2.0 preview 2.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-4.png)

<span data-ttu-id="bddd2-128">Per supportare i dispositivi iOS, devi importare il pacchetto Unity **ARKit XR plugin 2.1.1** da Package Manager (Gestione pacchetti).</span><span class="sxs-lookup"><span data-stu-id="bddd2-128">To support iOS devices, you should import the **ARKit XR plugin 2.1.1** Unity package from the Package Manager.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-5.png)

## <a name="customize-mrtk-to-support-ar-foundation-camera"></a><span data-ttu-id="bddd2-130">Personalizzare MRTK per supportare la fotocamera AR Foundation</span><span class="sxs-lookup"><span data-stu-id="bddd2-130">Customize MRTK to support AR Foundation camera</span></span>

<span data-ttu-id="bddd2-131">Personalizza le impostazioni di MRTK per supportare AR Foundation selezionando MixedRealityToolKit nella finestra Hierarchy (Gerarchia) e facendo clic sul pulsante **Clone** (Clona) in Mixed Reality ToolKit, nella finestra Inspector (Controllo).</span><span class="sxs-lookup"><span data-stu-id="bddd2-131">Customize MRTK settings to support AR Foundation by selecting MixedRealityToolKit in the Hierarchy window and click the **Clone** button in Mixed Reality ToolKit in the Inspector window.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-1.png)

<span data-ttu-id="bddd2-133">Quando fai clic sul pulsante **Clone** (Clona), viene visualizzata una nuova finestra Clone Profile (Clona profilo). Fai di nuovo clic sul pulsante Clone (Clona) per clonare il profilo DefaultMixedRealityToolkitProfile.</span><span class="sxs-lookup"><span data-stu-id="bddd2-133">When you click the **Clone** button, a new Clone Profile window will appear, click on the Clone button again to clone the DefaultMixedRealityToolkitProfile.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-2.png)

<span data-ttu-id="bddd2-135">Analogamente, clona il profilo della fotocamera nella finestra Inspector (Controllo), assegna il nome "UnityARConfigurationProfile" al profilo e fai clic sul pulsante **Clone** (Clona).</span><span class="sxs-lookup"><span data-stu-id="bddd2-135">Similarly, clone the camera profile in the Inspector window and rename the profile to “UnityARConfigurationProfile” and click on the **Clone** button.</span></span> <span data-ttu-id="bddd2-136">Nella finestra Inspector (Controllo) individua MixedReality e seleziona la scheda Camera (Fotocamera). Espandi i provider di impostazioni della fotocamera nella finestra Inspector (Controllo) e fai clic su **+Add Camera Setting Provider** (+Aggiungi provider impostazioni fotocamera) > espandi **New data provider 1** (Nuovo provider di dati 1) > in Type (Tipo) seleziona **None** (Nessuno) > seleziona **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > seleziona **UnityARCameraSettings**.</span><span class="sxs-lookup"><span data-stu-id="bddd2-136">In the Inspector window, locate the MixedReality, select the Camera tab Expand the camera setting providers in the inspector window and click on **+Add Camera Setting Provider** > expand **New data provider 1**> select Type **None** >select **Microsoft .MixedReality.Toolkit.Experimental.UnityAR** > Select **UnityARCameraSettings**.</span></span>


![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-3.png)

<span data-ttu-id="bddd2-138">Con l'oggetto MixedRealityToolKit selezionato nella finestra Hierarchy (Gerarchia), nella finestra Inspector (Controllo), associa gli script di supporto. A questo scopo, fai clic sul pulsante **Add component** (Aggiungi componente), digita AR Reference Point Manager (Gestione punto di riferimento AR) e seleziona lo script.</span><span class="sxs-lookup"><span data-stu-id="bddd2-138">With the MixedRealityToolKit object selected in the Hierarchy window, in the Inspector window, attach supporting scripts by clicking on the **Add component** button and type in AR reference Point manager and select the script.</span></span>

<span data-ttu-id="bddd2-139">Quando aggiungi lo script "AR Reference Point Manager" (Gestione punto di riferimento AR), viene aggiunto automaticamente anche lo script "AR Session Origin" (Origine sessione AR) nella finestra Inspector (Controllo).</span><span class="sxs-lookup"><span data-stu-id="bddd2-139">Adding the  "AR Reference Point Manager" script will automatically add "AR session origin" along with it in the Inspector window.</span></span> <span data-ttu-id="bddd2-140">Dopo aver aggiunto gli script di supporto, la finestra Inspector (Controllo) dovrebbe risultare analoga alla seguente.</span><span class="sxs-lookup"><span data-stu-id="bddd2-140">After adding the supporting scripts, the Inspector window should look like this.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-4.png)

## <a name="build-application-to-android-device"></a><span data-ttu-id="bddd2-142">Compilare l'applicazione in un dispositivo Android</span><span class="sxs-lookup"><span data-stu-id="bddd2-142">Build application to Android device</span></span>

<span data-ttu-id="bddd2-143">Per compilare l'applicazione in un dispositivo Android, fai clic su **File** nella parte superiore della finestra e seleziona **Build Settings** (Impostazioni di compilazione).</span><span class="sxs-lookup"><span data-stu-id="bddd2-143">To build this application to your Android device, click on **File** at the top of the window and select **Build Settings.**</span></span> <span data-ttu-id="bddd2-144">Viene visualizzata una nuova finestra. Seleziona **Android** e fai clic su **Switch Platform** (Cambia piattaforma).</span><span class="sxs-lookup"><span data-stu-id="bddd2-144">A new window will appear on the screen, select **Android,** and click on the **Switch Platform**.</span></span> <span data-ttu-id="bddd2-145">Il cambio di piattaforma richiederà qualche minuto.</span><span class="sxs-lookup"><span data-stu-id="bddd2-145">It will take a few minutes to switch platform.</span></span> <span data-ttu-id="bddd2-146">Dopo il passaggio alla piattaforma Android, fai clic su **Add Open Scene** (Aggiungi scena aperta) e verifica che la scena corrente sia l'unica scena selezionata nell'elenco **Scenes In Build** (Scene nella compilazione).</span><span class="sxs-lookup"><span data-stu-id="bddd2-146">After switching to the Android platform, click on **Add Open Scenes** and make sure your current scene is the only selected scene in the **Scenes In Build** list.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-1.png)

<span data-ttu-id="bddd2-148">Chiudi la finestra **Build Settings** (Impostazioni di compilazione).</span><span class="sxs-lookup"><span data-stu-id="bddd2-148">Close the **Build Settings** window.</span></span> <span data-ttu-id="bddd2-149">Nel menu di Unity seleziona **Mixed Reality Toolkit** > **Utilities** >  (Utilità) **Configure Unity Project** (Configura progetto Unity) e fai clic su **Apply** (Applica) per configurare il progetto Unity per la piattaforma Android.</span><span class="sxs-lookup"><span data-stu-id="bddd2-149">In the Unity menu, select **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** and click on **Apply** to configure the Unity project for the Android platform.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-2.png)

<span data-ttu-id="bddd2-151">Nel menu di Unity scegli **Edit** (Modifica)  > **Project Settings** (Impostazioni progetto) per visualizzare la finestra corrispondente.</span><span class="sxs-lookup"><span data-stu-id="bddd2-151">In the Unity menu, select **Edit** > **Project Settings** to open the Project Settings window.</span></span> <span data-ttu-id="bddd2-152">Nella finestra Project Settings (Impostazioni progetto) seleziona la scheda **Player** (Giocatore), espandi la sezione Other Settings (Altre impostazioni), seleziona **Vulkan** e rimuovila facendo clic sul simbolo "-".</span><span class="sxs-lookup"><span data-stu-id="bddd2-152">In the Project Settings, window selects the **Player** tab, expand the Other Settings section, select **Vulkan,** and remove it by clicking the "-" symbol.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-3.png)

<span data-ttu-id="bddd2-154">Chiudi la finestra Player Settings (Impostazioni giocatore) e apri di nuovo la finestra Build Settings (Impostazioni di compilazione).</span><span class="sxs-lookup"><span data-stu-id="bddd2-154">Close the Player Settings window and open the Build Settings window again.</span></span> <span data-ttu-id="bddd2-155">A questo punto, usando un cavo USB, connetti il dispositivo Android al computer e seleziona il dispositivo nell'elenco a discesa **Build and Run on** (Compila ed esegui in), quindi fai clic su **Build And Run** (Compila ed esegui).</span><span class="sxs-lookup"><span data-stu-id="bddd2-155">Then, using a USB cable, connect your Android device to your computer and select your device in the **Build and Run on** the dropdown, then click **Build And Run**.</span></span> <span data-ttu-id="bddd2-156">Ti verrà chiesto di salvare un file APK con un nome qualsiasi.</span><span class="sxs-lookup"><span data-stu-id="bddd2-156">You will be asked to save a .apk file, which you can pick any name.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-4.png)

> [!NOTE]
> <span data-ttu-id="bddd2-158">Se nella finestra della console Unity viene visualizzato un errore relativo ai moduli Android SDK, NDK e JDK, è necessario aprire Unity Hub e installare i moduli SDK, NDK e JDK associati per il modulo Android Build Support.</span><span class="sxs-lookup"><span data-stu-id="bddd2-158">If you get any error in the Unity Console window related to Android SDK, NDK, and or JDK modules, you need to open Unity Hub and install the associated SDK, NDK, and JDK modules for the Android Build Support module.</span></span>

<span data-ttu-id="bddd2-159">Al termine del processo di compilazione, le applicazioni dovrebbero essere caricate automaticamente sul dispositivo Android.</span><span class="sxs-lookup"><span data-stu-id="bddd2-159">When the build process is complete, your applications should automatically load on your Android device.</span></span>

## <a name="build-application-to-ios-device"></a><span data-ttu-id="bddd2-160">Compilare l'applicazione in un dispositivo iOS</span><span class="sxs-lookup"><span data-stu-id="bddd2-160">Build application to iOS Device</span></span>

<span data-ttu-id="bddd2-161">Per compilare l'applicazione in un dispositivo iOS, fai clic su **File** nella parte superiore della finestra e seleziona **Build Settings** (Impostazioni di compilazione).</span><span class="sxs-lookup"><span data-stu-id="bddd2-161">To build this application to your iOS device, click on **File** at the top of the window and select **Build Settings.**</span></span> <span data-ttu-id="bddd2-162">Viene visualizzata una nuova finestra. Seleziona **iOS** e fai clic su **Switch Platform** (Cambia piattaforma).</span><span class="sxs-lookup"><span data-stu-id="bddd2-162">A new window will appear on the screen, then select **iOS** and click on the **Switch Platform**.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section4-step1-1.png)

<span data-ttu-id="bddd2-164">Chiudi la finestra **Build Settings** (Impostazioni di compilazione).</span><span class="sxs-lookup"><span data-stu-id="bddd2-164">Close the **Build Settings** window.</span></span> <span data-ttu-id="bddd2-165">Nel menu di Unity seleziona **Mixed Reality Toolkit** > **Utilities** >  (Utilità) **Configure Unity Project** (Configura progetto Unity) e fai clic su **Apply** (Applica) per configurare il progetto Unity per la piattaforma iOS.</span><span class="sxs-lookup"><span data-stu-id="bddd2-165">In the Unity menu, select **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** and click on **Apply** to configure the Unity project for the iOS platform.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section4-step1-2.png)

<span data-ttu-id="bddd2-167">Per compilare il progetto iOS XCode, passa a Build Settings (Impostazioni di compilazione) e fai clic su **Build** (Compila).</span><span class="sxs-lookup"><span data-stu-id="bddd2-167">To build the iOS XCode project, go to Build Settings and, click on **Build**.</span></span>

<span data-ttu-id="bddd2-168">Segui [questa guida](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) per scoprire come distribuire il progetto in un dispositivo iOS.</span><span class="sxs-lookup"><span data-stu-id="bddd2-168">Follow [this guide](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) to learn how to deploy this project to your iOS device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="bddd2-169">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="bddd2-169">Congratulations</span></span>

<span data-ttu-id="bddd2-170">In questa esercitazione hai imparato a compilare il progetto per dispositivi Android e iOS.</span><span class="sxs-lookup"><span data-stu-id="bddd2-170">In this tutorial, you learned how to build your project for Android and iOS devices.</span></span> <span data-ttu-id="bddd2-171">Hai anche appreso come usare AR Foundation, ARCore XR Plugin e ARKit XR Plugin per fare in modo che il progetto sia utilizzabile su dispositivi Android e iOS.</span><span class="sxs-lookup"><span data-stu-id="bddd2-171">You also learned how to use AR Foundation, ARCore XR Plugin, and ARKit XR Plugin to make your project work for Android and iOS devices.</span></span>
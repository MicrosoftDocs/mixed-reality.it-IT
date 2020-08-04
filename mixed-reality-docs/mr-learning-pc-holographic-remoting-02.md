---
title: Esercitazioni su Holographic Remoting per PC - 2 Creare un'applicazione Holographic Remoting per PC
description: Completare questo corso per apprendere come usare in remoto l'esperienza di realtà mista da PC a HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: 6d11d91a0e08c48c09f676171dcb9bb8a0ff74de
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376373"
---
# <a name="2-creating-a-holographic-remoting-pc-application"></a><span data-ttu-id="f898f-105">2. Creazione di un'applicazione Holographic Remoting per PC</span><span class="sxs-lookup"><span data-stu-id="f898f-105">2. Creating a Holographic Remoting PC application</span></span>

<span data-ttu-id="f898f-106">In questa esercitazione si apprenderà come creare un'app Holographic Remoting per PC e connettere HoloLens 2 in qualsiasi momento, offrendo un modo per visualizzare il contenuto 3D in realtà mista.</span><span class="sxs-lookup"><span data-stu-id="f898f-106">In this tutorial, you will learn how to create a PC app for Holographic Remoting and connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span>

## <a name="objectives"></a><span data-ttu-id="f898f-107">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="f898f-107">Objectives</span></span>

* <span data-ttu-id="f898f-108">Configurare Unity per Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="f898f-108">Configure Unity for Holographic Remoting</span></span>
* <span data-ttu-id="f898f-109">Imparare a compilare e distribuire l'applicazione con Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f898f-109">Learn how to build and deploy the application with Visual Studio</span></span>
* <span data-ttu-id="f898f-110">Sviluppare un'applicazione Holographic Remoting e connetterla a HoloLens</span><span class="sxs-lookup"><span data-stu-id="f898f-110">Developing Holographic Remoting application and connecting to HoloLens</span></span>

## <a name="configuring-your-scene-for-holographic-remoting"></a><span data-ttu-id="f898f-111">Configurazione della scena per Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="f898f-111">Configuring your scene for Holographic Remoting</span></span>

<span data-ttu-id="f898f-112">In questa sezione si configurerà il progetto in modo da trasmettere l'esperienza di realtà mista al dispositivo HoloLens 2 dal PC in tempo reale tramite una connessione Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="f898f-112">In this section, you will configure your project to stream your Mixed Reality experience to your HoloLens 2 device from your PC in real-time over a Wi-Fi connection.</span></span>

<span data-ttu-id="f898f-113">Nella finestra Project (Progetto) passare alla cartella **Assets** (Asset)  > **MRTK.Tutorials.PCHolograhicRemoting** > **Prefabs** (Prefab) e selezionare e trascinare il prefab **HolographicRemoting** nella scena.</span><span class="sxs-lookup"><span data-stu-id="f898f-113">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.PCHolograhicRemoting** > **Prefabs** folder, and click and drag **HolographicRemoting** prefab into your scene.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section1-Step1-1.png)

## <a name="build-your-application-to-pc"></a><span data-ttu-id="f898f-115">Compilare l'applicazione nel PC</span><span class="sxs-lookup"><span data-stu-id="f898f-115">Build your application to PC</span></span>

<span data-ttu-id="f898f-116">L'app Holographic Remoting è ora pronta per la compilazione nel PC.</span><span class="sxs-lookup"><span data-stu-id="f898f-116">Your Holographic Remoting app is now ready to build on your PC.</span></span> <span data-ttu-id="f898f-117">Attenersi ai passaggi seguenti e apportare queste modifiche per compilare l'applicazione nel PC.</span><span class="sxs-lookup"><span data-stu-id="f898f-117">Follow the below steps and make these changes to build this application on to your PC.</span></span>

### <a name="1-set-the-player-settings"></a><span data-ttu-id="f898f-118">1. Configurare le impostazioni del lettore</span><span class="sxs-lookup"><span data-stu-id="f898f-118">1. Set the player settings</span></span>

<span data-ttu-id="f898f-119">Nel menu di Unity scegliere Edit (Modifica) > Project Settings (Impostazioni del progetto) per visualizzare la finestra Player Settings (Impostazioni lettore).</span><span class="sxs-lookup"><span data-stu-id="f898f-119">In the Unity menu, select Edit > Project Settings to open the Player Settings window.</span></span>

<span data-ttu-id="f898f-120">Nella sezione **XR Settings** (Impostazioni XR) selezionare la casella di controllo **WSA Holographic Remoting Supported** e abilitare Holographic Remoting.</span><span class="sxs-lookup"><span data-stu-id="f898f-120">In the **XR Settings** section, select the **WSA Holographic Remoting Supported** checkbox and enable the Holographic Remoting.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step1-1.png)

### <a name="2-build-the-unity-project"></a><span data-ttu-id="f898f-122">2. Compilare il progetto Unity</span><span class="sxs-lookup"><span data-stu-id="f898f-122">2. Build the Unity Project</span></span>

<span data-ttu-id="f898f-123">Dal menu di Unity scegliere File > Build Settings (Impostazioni di compilazione) per visualizzare la finestra corrispondente.</span><span class="sxs-lookup"><span data-stu-id="f898f-123">In the Unity menu, select File > Build Settings to open the Build Settings window.</span></span>

<span data-ttu-id="f898f-124">Nella finestra Build Settings (Impostazioni di compilazione) fare clic sul pulsante ***Add Open Scenes*** (Aggiungi scene aperte) per aggiungere la scena corrente alle scene.</span><span class="sxs-lookup"><span data-stu-id="f898f-124">In the Build Settings window, click the ***Add Open Scenes*** button to add your current scene to the Scenes.</span></span> <span data-ttu-id="f898f-125">Nell'elenco Build (Compilazione) fare clic sul pulsante ***Build*** (Compila) per aprire la finestra Build Universal Windows Platform (Compilazione UWP):</span><span class="sxs-lookup"><span data-stu-id="f898f-125">In the Build list, then click the ***Build button*** to open the Build Universal Windows Platform window:</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-1.png)

<span data-ttu-id="f898f-127">Nella finestra Build Universal Windows Platform (Compilazione UWP) scegliere un percorso adatto per archiviare la compilazione, ad esempio Documenti\MixedRealityLearning.</span><span class="sxs-lookup"><span data-stu-id="f898f-127">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, Documents\MixedRealityLearning.</span></span> <span data-ttu-id="f898f-128">Creare una nuova cartella e assegnarle un nome appropriato, ad esempio PCHolographicRemoting.</span><span class="sxs-lookup"><span data-stu-id="f898f-128">Create a new folder and give it a suitable name, for example, PCHolographicRemoting.</span></span> <span data-ttu-id="f898f-129">Fare quindi clic sul pulsante ***Select Folder*** (Seleziona cartella) per avviare il processo di compilazione:</span><span class="sxs-lookup"><span data-stu-id="f898f-129">Then click the ***Select Folder*** button to start the build process:</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-2.png)

<span data-ttu-id="f898f-131">Attendere che Unity completi il processo di compilazione.</span><span class="sxs-lookup"><span data-stu-id="f898f-131">Wait for Unity to finish the build process.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-3.png)

### <a name="3-build-and-deploy-the-application"></a><span data-ttu-id="f898f-133">3. Compilare e distribuire l'applicazione</span><span class="sxs-lookup"><span data-stu-id="f898f-133">3. Build and deploy the application</span></span>

<span data-ttu-id="f898f-134">Al termine del processo di compilazione, Unity richiederà a Esplora file di Windows di aprire il percorso in cui è stata archiviata la compilazione.</span><span class="sxs-lookup"><span data-stu-id="f898f-134">When the build process is completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="f898f-135">Spostarsi all'interno della cartella e fare doppio clic sul file con estensione sln per aprirlo in Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="f898f-135">Navigate inside the folder, and double-click the .sln file to open it in Visual Studio:</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-1.png)

> [!NOTE]
> <span data-ttu-id="f898f-137">Se Visual Studio chiede di installare nuovi componenti, dedicare qualche minuto a verificare che siano installati tutti i componenti indispensabili, come specificato nell'argomento Installare gli strumenti.</span><span class="sxs-lookup"><span data-stu-id="f898f-137">If Visual Studio asks you to install new components, take a moment to ensure that all prerequisite components are installed as specified in the Install the Tools documentation.</span></span>

<span data-ttu-id="f898f-138">Configurare Visual Studio per PC selezionando la configurazione Release, l'architettura x64 e Local Machine (Computer locale) come destinazione:</span><span class="sxs-lookup"><span data-stu-id="f898f-138">Configure Visual Studio for PC by selecting the Release configuration, the x64 architecture, and Local Machine as target:</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-2.png)

<span data-ttu-id="f898f-140">Fare clic sul pulsante ***Local Machine*** (Computer locale).</span><span class="sxs-lookup"><span data-stu-id="f898f-140">Click the button that says ***Local Machine***.</span></span> <span data-ttu-id="f898f-141">Viene avviata la compilazione e la distribuzione dell'applicazione nel PC.</span><span class="sxs-lookup"><span data-stu-id="f898f-141">It starts to build and deploy the application on to your PC.</span></span> <span data-ttu-id="f898f-142">L'applicazione verrà installata nel PC per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="f898f-142">The application will be installed in your PC by default.</span></span>

## <a name="testing-holographic-remoting-remote-application"></a><span data-ttu-id="f898f-143">Test di un'applicazione remota Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="f898f-143">Testing Holographic Remoting remote application</span></span>

<span data-ttu-id="f898f-144">Per connettere l'applicazione PC a HoloLens 2, seguire questa procedura:</span><span class="sxs-lookup"><span data-stu-id="f898f-144">To connect your PC application to your HoloLens 2, follow the below process:</span></span>

### <a name="1-install-the-remoting-player-application-on-hololens-2-device"></a><span data-ttu-id="f898f-145">1. Installare l'applicazione Remoting Player nel dispositivo HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="f898f-145">1. Install the Remoting Player application on HoloLens 2 device</span></span>

* <span data-ttu-id="f898f-146">In HoloLens 2 visitare l'app dello Store e cercare "**Remoting Player**".</span><span class="sxs-lookup"><span data-stu-id="f898f-146">On your HoloLens 2, visit the Store app and search for "**Remoting Player**."</span></span>
* <span data-ttu-id="f898f-147">Selezionare l'app **Remoting Player**.</span><span class="sxs-lookup"><span data-stu-id="f898f-147">Select the **Remoting Player** app.</span></span>
* <span data-ttu-id="f898f-148">Toccare **Install** (Installa) per scaricare e installare l'app.</span><span class="sxs-lookup"><span data-stu-id="f898f-148">Tap **Install** to download and install the app.</span></span>

### <a name="2-connect-the-holographic-remoting-pc-app-to-the-remoting-player"></a><span data-ttu-id="f898f-149">2. Connettere l'app del PC Holographic Remoting a Remoting Player</span><span class="sxs-lookup"><span data-stu-id="f898f-149">2. Connect the Holographic remoting PC app to the Remoting Player</span></span>

* <span data-ttu-id="f898f-150">Avviare **Remoting Player** in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f898f-150">Start the **Remoting Player** on your HoloLens.</span></span>
* <span data-ttu-id="f898f-151">Prendere nota dell'**indirizzo IP** di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f898f-151">Take note of the HoloLens **IP address**.</span></span> <span data-ttu-id="f898f-152">Verrà visualizzato come ologramma da **Remoting Player** non appena viene avviato.</span><span class="sxs-lookup"><span data-stu-id="f898f-152">It will be displayed as a hologram by the **Remoting Player** as soon as it launches.</span></span>
* <span data-ttu-id="f898f-153">Aprire l'applicazione Holographic Remoting per PC nel PC in uso.</span><span class="sxs-lookup"><span data-stu-id="f898f-153">Open the Holographic Remoting PC application on your PC.</span></span>
* <span data-ttu-id="f898f-154">Una volta avviata l'applicazione, immettere l'**indirizzo IP** e fare clic sul pulsante **Connect** (Connetti) per connettersi.</span><span class="sxs-lookup"><span data-stu-id="f898f-154">Once the application is launched, enter the **IP address** and click on the **Connect**  button to connect.</span></span>

## <a name="congratulations"></a><span data-ttu-id="f898f-155">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="f898f-155">Congratulations</span></span>

<span data-ttu-id="f898f-156">In questa esercitazione si è appreso come creare un'app remota Holographic Remoting e connetterla a HoloLens 2 in qualsiasi momento, offrendo un modo per visualizzare il contenuto 3D in realtà mista.</span><span class="sxs-lookup"><span data-stu-id="f898f-156">In this tutorial, you learned how to create a Holographic Remoting remote app and connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span> <span data-ttu-id="f898f-157">Dopo aver connesso HoloLens all'applicazione PC Holographic Remoting, si noterà che l'esperienza di realtà mista è in streaming nel dispositivo HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="f898f-157">Once the HoloLens connected to the Holographic Remoting PC application, you should see the mixed reality experience streaming into your HoloLens 2 device.</span></span>

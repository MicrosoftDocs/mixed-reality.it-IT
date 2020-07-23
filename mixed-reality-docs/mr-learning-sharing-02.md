---
title: Esercitazioni sulle funzionalità multiutente - 2. Configurazione di Photon Unity Networking
description: Completa questo corso per imparare a implementare esperienze condivise multiutente all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: e5817338dbed944232664a86f8b0625bc9d3e1e7
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/14/2020
ms.locfileid: "86305710"
---
# <a name="2-setting-up-photon-unity-networking"></a><span data-ttu-id="952fc-105">2. Configurazione di Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="952fc-105">2. Setting up Photon Unity Networking</span></span>

## <a name="overview"></a><span data-ttu-id="952fc-106">Panoramica</span><span class="sxs-lookup"><span data-stu-id="952fc-106">Overview</span></span>

<span data-ttu-id="952fc-107">In questa esercitazione si preparerà l'ambiente per la creazione di un'esperienza condivisa tramite Photon Unity Networking (PUN).</span><span class="sxs-lookup"><span data-stu-id="952fc-107">In this tutorial, you will prepare for creating a shared experience using Photon Unity Networking (PUN).</span></span> <span data-ttu-id="952fc-108">Si apprenderà come creare un'app PUN, importare asset di PUN nel progetto Unity e connettere il progetto Unity all'app PUN.</span><span class="sxs-lookup"><span data-stu-id="952fc-108">You will learn how to create a PUN app, import PUN assets into your Unity project, and connect your Unity project to the PUN app.</span></span>

## <a name="objectives"></a><span data-ttu-id="952fc-109">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="952fc-109">Objectives</span></span>

* <span data-ttu-id="952fc-110">Imparare a creare un'app PUN</span><span class="sxs-lookup"><span data-stu-id="952fc-110">Learn how to create a PUN app</span></span>
* <span data-ttu-id="952fc-111">Imparare a trovare e importare gli asset di PUN</span><span class="sxs-lookup"><span data-stu-id="952fc-111">Learn how to find and import the PUN assets</span></span>
* <span data-ttu-id="952fc-112">Imparare a connettere il progetto Unity all'app PUN</span><span class="sxs-lookup"><span data-stu-id="952fc-112">Learn how to connect your Unity project to the PUN app</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="952fc-113">Creazione e preparazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="952fc-113">Creating and preparing the Unity project</span></span>

<span data-ttu-id="952fc-114">In questa sezione creerai un nuovo progetto Unity per prepararti allo sviluppo con MRTK.</span><span class="sxs-lookup"><span data-stu-id="952fc-114">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="952fc-115">A questo scopo, seguire prima l'esercitazione [Inizializzazione del progetto e distribuzione della prima applicazione](mr-learning-base-02.md), escluse le istruzioni della sezione [Compilare l'applicazione nel dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2). L'esercitazione include i passaggi seguenti:</span><span class="sxs-lookup"><span data-stu-id="952fc-115">For this, first follow the [Initializing your project and deploying your first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="952fc-116">[Creazione del progetto Unity](mr-learning-base-02.md#creating-the-unity-project) e assegnazione di un nome appropriato, ad esempio *MRTK Tutorials*</span><span class="sxs-lookup"><span data-stu-id="952fc-116">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
1. [<span data-ttu-id="952fc-117">Passaggio alla piattaforma di compilazione</span><span class="sxs-lookup"><span data-stu-id="952fc-117">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
1. [<span data-ttu-id="952fc-118">Importazione delle risorse essenziali TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="952fc-118">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
1. [<span data-ttu-id="952fc-119">Importazione di Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="952fc-119">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
1. [<span data-ttu-id="952fc-120">Configurazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="952fc-120">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
1. <span data-ttu-id="952fc-121">[Creazione e configurazione della scena](mr-learning-base-02.md#creating-and-configuring-the-scene) e assegnazione di un nome appropriato, ad esempio *MultiUserCapabilities*</span><span class="sxs-lookup"><span data-stu-id="952fc-121">[Creating and configuring the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *MultiUserCapabilities*</span></span>

<span data-ttu-id="952fc-122">Seguire quindi le istruzioni riportate in [Modifica delle opzioni di visualizzazione di consapevolezza spaziale](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) per:</span><span class="sxs-lookup"><span data-stu-id="952fc-122">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to:</span></span>

1. <span data-ttu-id="952fc-123">Impostare **MRTK configuration profile** (Profilo di configurazione di MRTK) su **DefaultHoloLens2ConfigurationProfile**</span><span class="sxs-lookup"><span data-stu-id="952fc-123">Change the **MRTK configuration profile** for to the **DefaultHoloLens2ConfigurationProfile**</span></span>
1. <span data-ttu-id="952fc-124">Impostare le **opzioni di visualizzazione mesh di consapevolezza spaziale** su **Occlusion** (Occlusione).</span><span class="sxs-lookup"><span data-stu-id="952fc-124">Change the **spatial awareness mesh display options** to **Occlusion**.</span></span>

## <a name="enabling-additional-capabilities"></a><span data-ttu-id="952fc-125">Abilitazione delle funzionalità aggiuntive</span><span class="sxs-lookup"><span data-stu-id="952fc-125">Enabling additional capabilities</span></span>

<span data-ttu-id="952fc-126">Dal menu Unity scegli **Edit** > **Project Settings...** (Modifica > Impostazioni del progetto) per aprire la finestra Project Settings (Impostazioni del progetto) e quindi individua la sezione **Player** >  **Publishing Settings** (Lettore > Impostazioni di pubblicazione):</span><span class="sxs-lookup"><span data-stu-id="952fc-126">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Publishing Settings** section:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section2-step1-1.png)

<span data-ttu-id="952fc-128">In **Publishing Settings** (Impostazioni di pubblicazione) scorrere verso il basso fino alla sezione **Capabilities** (Funzionalità) e verificare che siano abilitate le funzionalità **InternetClient**, **Microphone**, **SpatialPerception**, e **GazeInput**, abilitate al passaggio [Configurazione del progetto Unity](mr-learning-base-02.md#configuring-the-unity-project) precedente.</span><span class="sxs-lookup"><span data-stu-id="952fc-128">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, **SpatialPerception**, and **GazeInput** capabilities, which you enabled during the [Configuring the Unity project](mr-learning-base-02.md#configuring-the-unity-project) step above, are enabled.</span></span>

<span data-ttu-id="952fc-129">Abilitare quindi le funzionalità aggiuntive seguenti:</span><span class="sxs-lookup"><span data-stu-id="952fc-129">Then enable the following additional capabilities:</span></span>

* <span data-ttu-id="952fc-130">Funzionalità **InternetClientServer**</span><span class="sxs-lookup"><span data-stu-id="952fc-130">**InternetClientServer** capability</span></span>
* <span data-ttu-id="952fc-131">Funzionalità **PrivateNetworkClientServer**</span><span class="sxs-lookup"><span data-stu-id="952fc-131">**PrivateNetworkClientServer** capability</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section2-step1-2.png)

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="952fc-133">Installazione di pacchetti di Unity incorporati</span><span class="sxs-lookup"><span data-stu-id="952fc-133">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="952fc-134">Scegliere **Window** > **Package Manager** (Finestra > Gestione pacchetti) dal menu Unity per aprire la finestra Package Manager(Gestione pacchetti) e quindi selezionare **AR Foundation** e fare clic sul pulsante **Install** (Installa) per installare il pacchetto:</span><span class="sxs-lookup"><span data-stu-id="952fc-134">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** and click the **Install** button to install the package:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section3-step1-1.png)

> [!NOTE]
> <span data-ttu-id="952fc-136">Si sta installando il pacchetto AR Foundation richiesto da Azure Spatial Anchors SDK, che verrà importato nella sezione successiva.</span><span class="sxs-lookup"><span data-stu-id="952fc-136">You are installing the AR Foundation package because it is required by the Azure Spatial Anchors SDK you will import in the next section.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="952fc-137">Importazione degli asset dell'esercitazione</span><span class="sxs-lookup"><span data-stu-id="952fc-137">Importing the tutorial assets</span></span>

<span data-ttu-id="952fc-138">Scarica e **importa** i pacchetti personalizzati di Unity seguenti, **nell'ordine in cui sono elencati**:</span><span class="sxs-lookup"><span data-stu-id="952fc-138">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="952fc-139">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage) (versione 2.2.1)</span><span class="sxs-lookup"><span data-stu-id="952fc-139">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage) (version 2.2.1)</span></span>
* [<span data-ttu-id="952fc-140">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="952fc-140">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [<span data-ttu-id="952fc-141">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="952fc-141">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage)
* [<span data-ttu-id="952fc-142">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="952fc-142">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage)

<span data-ttu-id="952fc-143">Dopo l'importazione degli asset dell'esercitazione, la finestra Project (Progetto) avrà un aspetto simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="952fc-143">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="952fc-145">Per rivedere la procedura di importazione di un pacchetto personalizzato di Unity, è possibile fare riferimento alle istruzioni riportate in [Importazione di Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="952fc-145">For a reminder on how to import a Unity custom package, you can refer to the [Importing the Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) instructions.</span></span>

> [!NOTE]
> <span data-ttu-id="952fc-146">Dopo aver importato il pacchetto di asset dell'esercitazione MultiUserCapabilities, nella finestra della console verranno visualizzati alcuni errori [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246) che indicano che manca il tipo o lo spazio dei nomi.</span><span class="sxs-lookup"><span data-stu-id="952fc-146">After importing the MultiUserCapabilities tutorial assets package, you will see several [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246) errors in the Console window stating that the type or namespace is missing.</span></span> <span data-ttu-id="952fc-147">Si tratta di un comportamento previsto, che verrà risolto nella prossima sezione quando verranno importati gli asset di PUN.</span><span class="sxs-lookup"><span data-stu-id="952fc-147">This is expected and will be resolved in the next section when you import the PUN assets.</span></span>

## <a name="importing-the-pun-assets"></a><span data-ttu-id="952fc-148">Importazione degli asset di PUN</span><span class="sxs-lookup"><span data-stu-id="952fc-148">Importing the PUN assets</span></span>

<span data-ttu-id="952fc-149">Nel menu di Unity selezionare **Window** > **Asset Store** (Finestra > Store degli asset) per aprire la finestra Asset Store (Store degli asset), cercare e selezionare **PUN 2 - FREE** (PUN 2 - GRATUITO) in Exit Games (Giochi in uscita) e fare clic sul pulsante **Download** (Scarica) per scaricare il pacchetto di asset nell'account Unity.</span><span class="sxs-lookup"><span data-stu-id="952fc-149">In the Unity menu, select **Window** > **Asset Store** to open the Asset Store window, search for and select **PUN 2 - FREE** from Exit Games, click the **Download** button to download the asset package to your Unity account.</span></span>

<span data-ttu-id="952fc-150">Al termine del download, fai clic sul pulsante **Import** (Importa) per aprire la finestra Import Unity Package (Importa pacchetto Unity):</span><span class="sxs-lookup"><span data-stu-id="952fc-150">When the download is complete, click the **Import** button to open the Import Unity Package window:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section5-step1-1.png)

<span data-ttu-id="952fc-152">Nella finestra Import Unity Package (Importa il pacchetto Unity), fai clic sul pulsante **All** (Tutti) per assicurarti che vengano selezionati tutti gli asset e quindi fai clic sul pulsante **Import** (Importa) per importare gli asset:</span><span class="sxs-lookup"><span data-stu-id="952fc-152">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section5-step1-2.png)

<span data-ttu-id="952fc-154">Dopo che Unity ha completato il processo di importazione, verrà visualizzata la finestra PUN Wizard (Creazione guidata PUN) con il menu PUN Setup (Configurazione PUN) caricato. Per il momento puoi ignorare o chiudere questa finestra:</span><span class="sxs-lookup"><span data-stu-id="952fc-154">Once Unity has completed the import process, the Pun Wizard window will appear with the PUN Setup menu loaded, you can ignore or close this window for now:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section5-step1-3.png)

## <a name="creating-the-pun-application"></a><span data-ttu-id="952fc-156">Creazione dell'applicazione PUN</span><span class="sxs-lookup"><span data-stu-id="952fc-156">Creating the PUN application</span></span>

<span data-ttu-id="952fc-157">In questa sezione si creerà un account Photon, se non esiste già, e una nuova app PUN.</span><span class="sxs-lookup"><span data-stu-id="952fc-157">In this section, you will create a Photon account, if you don't already have one, and create a new PUN app.</span></span>

<span data-ttu-id="952fc-158">Passa al <a href="https://dashboard.photonengine.com/account/signin" target="_blank">dashboard</a> di Photon ed esegui l'accesso se hai già un account che vuoi usare. In caso contrario, fai clic sul collegamento **Create One** (Creane uno) e segui le istruzioni per la registrazione di un nuovo account:</span><span class="sxs-lookup"><span data-stu-id="952fc-158">Navigate to the Photon <a href="https://dashboard.photonengine.com/account/signin" target="_blank">dashboard</a> and sign in if you already have an account you want to use, otherwise, click the **Create One** link and follow the instructions to register a new account:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section6-step1-1.png)

<span data-ttu-id="952fc-160">Una volta eseguito l'accesso, fai clic sul pulsante **Create a New App** (Crea una nuova app):</span><span class="sxs-lookup"><span data-stu-id="952fc-160">Once signed in, click the **Create a New App** button:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section6-step1-2.png)

<span data-ttu-id="952fc-162">Nella pagina Create a New Application (Crea una nuova applicazione) immetti i valori seguenti:</span><span class="sxs-lookup"><span data-stu-id="952fc-162">On the Create a New Application page, enter the following values:</span></span>

* <span data-ttu-id="952fc-163">In Photon Type (Tipo Photon) selezionare PUN</span><span class="sxs-lookup"><span data-stu-id="952fc-163">For Photon Type, select PUN</span></span>
* <span data-ttu-id="952fc-164">In Name (Nome) immetti un nome appropriato, ad esempio _MRTK Tutorials_</span><span class="sxs-lookup"><span data-stu-id="952fc-164">For Name, enter a suitable name, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="952fc-165">In Description (Descrizione) immetti facoltativamente una descrizione appropriata</span><span class="sxs-lookup"><span data-stu-id="952fc-165">For Description, optionally enter a suitable description</span></span>
* <span data-ttu-id="952fc-166">In Url lascia il campo vuoto</span><span class="sxs-lookup"><span data-stu-id="952fc-166">For Url, leave the field empty</span></span>

<span data-ttu-id="952fc-167">Fare quindi clic sul pulsante **Create** (Crea) per creare la nuova app:</span><span class="sxs-lookup"><span data-stu-id="952fc-167">Then click the **Create** button to create the new app:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section6-step1-3.png)

<span data-ttu-id="952fc-169">Al termine del processo di creazione, nel dashboard verrà visualizzata la nuova app PUN:</span><span class="sxs-lookup"><span data-stu-id="952fc-169">Once Photon has finished the creation process, the new PUN app will appear on your dashboard:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section6-step1-4.png)

## <a name="connecting-the-unity-project-to-the-pun-application"></a><span data-ttu-id="952fc-171">Connessione del progetto Unity all'applicazione PUN</span><span class="sxs-lookup"><span data-stu-id="952fc-171">Connecting the Unity project to the PUN application</span></span>

<span data-ttu-id="952fc-172">In questa sezione si connetterà il progetto Unity all'app PUN creata nella sezione precedente.</span><span class="sxs-lookup"><span data-stu-id="952fc-172">In this section, you will connect your Unity project to the PUN app you created in the previous section.</span></span>

<span data-ttu-id="952fc-173">Nel dashboard di Photon fai clic sul campo **App ID** (ID app) per visualizzare l'ID dell'app e quindi copialo negli Appunti:</span><span class="sxs-lookup"><span data-stu-id="952fc-173">On the Photon dashboard, click the **App ID** field to reveal the app ID, then copy it to your clipboard:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section7-step1-1.png)

<span data-ttu-id="952fc-175">Nel menu di Unity seleziona **Window** (Finestra) > **Photon Unity Networking** > **PUN Wizard** (Creazione guidata PUN) per aprire la finestra PUN Wizard (Creazione guidata PUN), fai clic sul pulsante **Setup Project** (Configura progetto) per aprire il menu PUN Setup (Configurazione PUN) ed esegui la configurazione nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="952fc-175">In the Unity menu, select **Window** > **Photon Unity Networking** > **PUN Wizard** to open the Pun Wizard window, click the **Setup Project** button to open the PUN Setup menu, and configure it as follows:</span></span>

* <span data-ttu-id="952fc-176">Nel campo **AppId or Email** (ID app o e-mail) incolla l'ID dell'app PUN copiato nel passaggio precedente</span><span class="sxs-lookup"><span data-stu-id="952fc-176">In the **AppId or Email** field, paste the PUN app ID you copied in the previous step</span></span>

<span data-ttu-id="952fc-177">Fai quindi clic sul pulsante **Setup Project** (Configura progetto) per applicare l'ID dell'app:</span><span class="sxs-lookup"><span data-stu-id="952fc-177">Then click the **Setup Project** button to apply the app ID:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section7-step1-2.png)

<span data-ttu-id="952fc-179">Dopo che Unity ha terminato il processo di configurazione di PUN, nel menu PUN Setup (Configurazione PUN) verrà visualizzato il messaggio **Done!** (Fatto)</span><span class="sxs-lookup"><span data-stu-id="952fc-179">Once Unity has finished the PUN setup process, the PUN Setup menu will display the message **Done!**</span></span> <span data-ttu-id="952fc-180">e nella finestra Project (Progetto) verrà selezionato automaticamente l'asset **PhotonServerSettings**, in modo che le relative proprietà siano visualizzate nella finestra Inspector (Controllo):</span><span class="sxs-lookup"><span data-stu-id="952fc-180">and automatically select the **PhotonServerSettings** asset in the Project window, so its properties are displayed in the Inspector window:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section7-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="952fc-182">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="952fc-182">Congratulations</span></span>

<span data-ttu-id="952fc-183">È stata creata un'app PUN ed è stata connessa al progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="952fc-183">You have successfully created a PUN app and connected it to your Unity project.</span></span> <span data-ttu-id="952fc-184">Il passaggio successivo consiste nel consentire connessioni con altri utenti, in modo che ogni utente possa visualizzare il lavoro svolto dagli altri.</span><span class="sxs-lookup"><span data-stu-id="952fc-184">Your next step is to allow connections with other users so that multiple users can see each other.</span></span>

[<span data-ttu-id="952fc-185">Esercitazione successiva: 3. Connessione di più utenti</span><span class="sxs-lookup"><span data-stu-id="952fc-185">Next Tutorial: 3. Connecting multiple users</span></span>](mr-learning-sharing-03.md)

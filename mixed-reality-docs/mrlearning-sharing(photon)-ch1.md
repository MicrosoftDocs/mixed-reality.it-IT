---
title: Esercitazioni sulle funzionalità multiutente - 1. Configurazione di Photon Unity Networking
description: Completa questo corso per imparare a implementare esperienze condivise multiutente all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: 2f5b55fe9c54e9e2c08177266c04a97d2302230e
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610681"
---
# <a name="1-setting-up-photon-unity-networking"></a><span data-ttu-id="ecc27-105">1. Configurazione di Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="ecc27-105">1. Setting up Photon Unity Networking</span></span>

## <a name="overview"></a><span data-ttu-id="ecc27-106">Panoramica</span><span class="sxs-lookup"><span data-stu-id="ecc27-106">Overview</span></span>

<span data-ttu-id="ecc27-107">In questa esercitazione imparerai a prepararti per la creazione di un'esperienza condivisa tramite Photon Unity Networking (PUN).</span><span class="sxs-lookup"><span data-stu-id="ecc27-107">In this tutorial, you will learn how to prepare for creating a shared experience using Photon Unity Networking (PUN).</span></span> <span data-ttu-id="ecc27-108">Photon è una delle diverse opzioni di rete disponibili per gli sviluppatori di Realtà mista per creare esperienze condivise.</span><span class="sxs-lookup"><span data-stu-id="ecc27-108">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="ecc27-109">Scoprirai come creare un'applicazione Photon PUN, importare asset di Photon PUN nel progetto Unity e connettere il progetto Unity all'applicazione Photon PUN.</span><span class="sxs-lookup"><span data-stu-id="ecc27-109">You will learn how to create a Photon PUN application, import Photon PUN assets into your Unity project, and connect your Unity project to the Photon PUN application.</span></span>

## <a name="objectives"></a><span data-ttu-id="ecc27-110">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="ecc27-110">Objectives</span></span>

* <span data-ttu-id="ecc27-111">Imparare a creare un'applicazione Photon PUN</span><span class="sxs-lookup"><span data-stu-id="ecc27-111">Learn how to create a Photon PUN application</span></span>
* <span data-ttu-id="ecc27-112">Imparare a trovare e importare gli asset di Photon PUN</span><span class="sxs-lookup"><span data-stu-id="ecc27-112">Learn how to find and import the Photon PUN assets</span></span>
* <span data-ttu-id="ecc27-113">Imparare a connettere il progetto Unity all'applicazione Photon PUN</span><span class="sxs-lookup"><span data-stu-id="ecc27-113">Learn how to connect your Unity project to the Photon PUN application</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ecc27-114">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="ecc27-114">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="ecc27-115">Se non hai ancora completato le serie di [Esercitazioni introduttive](mrlearning-base.md) ed [Esercitazioni su Ancoraggi nello spazio di Azure](mrlearning-asa-ch1.md), è consigliabile completare prima queste esercitazioni.</span><span class="sxs-lookup"><span data-stu-id="ecc27-115">If you have not completed the [Getting started tutorials](mrlearning-base.md) and [Azure Spatial Anchors tutorials](mrlearning-asa-ch1.md) tutorial series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="ecc27-116">Un PC Windows 10 configurato in cui siano [installati gli strumenti](install-the-tools.md) corretti</span><span class="sxs-lookup"><span data-stu-id="ecc27-116">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="ecc27-117">Windows 10 SDK 10.0.18362.0 o versioni successive</span><span class="sxs-lookup"><span data-stu-id="ecc27-117">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="ecc27-118">Alcune funzionalità di programmazione C# di base</span><span class="sxs-lookup"><span data-stu-id="ecc27-118">Some basic C# programming ability</span></span>
* <span data-ttu-id="ecc27-119">Un dispositivo HoloLens 2 [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="ecc27-119">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="ecc27-120"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.2.X installato e il modulo di supporto delle compilazioni UWP (Universal Windows Platform) aggiunto</span><span class="sxs-lookup"><span data-stu-id="ecc27-120"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="ecc27-121">Completa la sezione [Creare una risorsa di Ancoraggi nello spazio](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) dell'esercitazione [Avvio rapido: Creare un'app HoloLens in Unity che usa Ancoraggi nello spazio di Azure](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)</span><span class="sxs-lookup"><span data-stu-id="ecc27-121">Complete the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ecc27-122">La versione di Unity consigliata per questa serie di esercitazioni è Unity 2019.2.X.</span><span class="sxs-lookup"><span data-stu-id="ecc27-122">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="ecc27-123">Questa istruzione sostituisce gli eventuali requisiti o suggerimenti relativi alla versione di Unity indicati negli argomenti visualizzabili facendo clic sui collegamenti dei prerequisiti sopra riportati.</span><span class="sxs-lookup"><span data-stu-id="ecc27-123">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="ecc27-124">Creazione e preparazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="ecc27-124">Creating and preparing the Unity project</span></span>

<span data-ttu-id="ecc27-125">In questa sezione creerai un nuovo progetto Unity per prepararti allo sviluppo con MRTK.</span><span class="sxs-lookup"><span data-stu-id="ecc27-125">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="ecc27-126">A questo scopo, segui prima l'esercitazione [Inizializzazione del progetto e prima applicazione](mrlearning-base-ch1.md), escluse le istruzioni della sezione [Compilare l'applicazione nel dispositivo](mrlearning-base-ch1.md#build-your-application-to-your-device), che include i passaggi seguenti:</span><span class="sxs-lookup"><span data-stu-id="ecc27-126">For this, first follow the [Initializing your project and first application](mrlearning-base-ch1.md), excluding the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="ecc27-127">[Creare un nuovo progetto Unity](mrlearning-base-ch1.md#create-new-unity-project) e assegnargli un nome appropriato, ad esempio *MRTK Tutorials*</span><span class="sxs-lookup"><span data-stu-id="ecc27-127">[Create new Unity project](mrlearning-base-ch1.md#create-new-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>

2. [<span data-ttu-id="ecc27-128">Configurare il progetto Unity per Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ecc27-128">Configure the Unity project for Windows Mixed Reality</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [<span data-ttu-id="ecc27-129">Importare le risorse essenziali TextMesh Pro</span><span class="sxs-lookup"><span data-stu-id="ecc27-129">Import TextMesh Pro Essential Resources</span></span>](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [<span data-ttu-id="ecc27-130">Importare Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="ecc27-130">Import the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [<span data-ttu-id="ecc27-131">Configurare il progetto Unity per Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="ecc27-131">Configure the Unity project for the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. <span data-ttu-id="ecc27-132">[Aggiungere Mixed Reality Toolkit alla scena di Unity](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) e assegnare alla scena un nome appropriato, ad esempio *MultiUserCapabilities*</span><span class="sxs-lookup"><span data-stu-id="ecc27-132">[Add the Mixed Reality Toolkit to the Unity scene](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) and give the scene a suitable name, for example, *MultiUserCapabilities*</span></span>

<span data-ttu-id="ecc27-133">Segui quindi le istruzioni riportate in [Come configurare i profili di Mixed Reality Toolkit (modifica dell'opzione di visualizzazione della mesh di consapevolezza spaziale)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) per impostare **DefaultHoloLens2ConfigurationProfile** come profilo di configurazione MRTK per la scena e modificare in **Occlusion** (Occlusione) le opzioni di visualizzazione per la mesh di consapevolezza spaziale.</span><span class="sxs-lookup"><span data-stu-id="ecc27-133">Then follow the [How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

> [!CAUTION]
> <span data-ttu-id="ecc27-134">Come indicato nelle istruzioni contenute in [Configurare il progetto Unity per Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit), è fortemente sconsigliabile abilitare MSBuild per Unity.</span><span class="sxs-lookup"><span data-stu-id="ecc27-134">As mentioned in the [Configure the Unity project for the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) instructions linked above, it is strongly recommended to not enable MSBuild for Unity.</span></span>

## <a name="configuring-the-capabilities"></a><span data-ttu-id="ecc27-135">Configurazione delle funzionalità</span><span class="sxs-lookup"><span data-stu-id="ecc27-135">Configuring the capabilities</span></span>

<span data-ttu-id="ecc27-136">Dal menu Unity scegli **Edit** > **Project Settings...** (Modifica > Impostazioni del progetto) per aprire la finestra Project Settings (Impostazioni del progetto) e quindi individua la sezione **Player** >  **Publishing Settings** (Lettore > Impostazioni di pubblicazione):</span><span class="sxs-lookup"><span data-stu-id="ecc27-136">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Publishing Settings** section:</span></span>

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial1-section2-step1-1.png)

<span data-ttu-id="ecc27-138">In **Publishing Settings** (Impostazioni di pubblicazione) scorri verso il basso fino alla sezione **Capabilities** (Funzionalità) e verifica che siano abilitate le funzionalità **InternetClient**, **Microphone** e **SpatialPerception**, che hai abilitato al momento della creazione del progetto all'inizio dell'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="ecc27-138">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="ecc27-139">Abilita quindi le funzionalità **InternetClientServer**, **PrivateNetworkClientServer** e **RemovableStorage**:</span><span class="sxs-lookup"><span data-stu-id="ecc27-139">Then, enable the **InternetClientServer**, **PrivateNetworkClientServer**, and **RemovableStorage** capabilities:</span></span>

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial1-section2-step1-2.png)

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="ecc27-141">Aggiunta di pacchetti di Unity incorporati</span><span class="sxs-lookup"><span data-stu-id="ecc27-141">Adding inbuilt Unity packages</span></span>
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

<span data-ttu-id="ecc27-142">In questa sezione installerai il pacchetto AR Foundation incorporato di Unity perché è un prerequisito dell'SDK di Ancoraggi nello spazio di Azure che importerai nella sezione successiva.</span><span class="sxs-lookup"><span data-stu-id="ecc27-142">In this section, you will install Unity's inbuilt AR Foundation package because it is required by the Azure Spatial Anchors SDK you will import in the next section.</span></span>

<span data-ttu-id="ecc27-143">Nel menu di Unity seleziona **Window** (Finestra) > **Package Manager** (Gestione pacchetti):</span><span class="sxs-lookup"><span data-stu-id="ecc27-143">In the Unity menu, select **Window** > **Package Manager**:</span></span>

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial1-section3-step1-1.png)

> [!NOTE]
> <span data-ttu-id="ecc27-145">Potrebbero essere necessari alcuni secondi prima che il pacchetto AR Foundation venga visualizzato nell'elenco.</span><span class="sxs-lookup"><span data-stu-id="ecc27-145">It might take a few seconds before the AR Foundation package appears in the list.</span></span>

<span data-ttu-id="ecc27-146">Nella finestra Package Manager (Gestione pacchetti) seleziona **AR Foundation** e installa il pacchetto facendo clic sul pulsante **Install** (Installa):</span><span class="sxs-lookup"><span data-stu-id="ecc27-146">In the Package Manager window, select **AR Foundation** and install the package by clicking the **Install** button:</span></span>

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="ecc27-148">Importazione degli asset dell'esercitazione</span><span class="sxs-lookup"><span data-stu-id="ecc27-148">Importing the tutorial assets</span></span>

<span data-ttu-id="ecc27-149">Scarica e **importa** i pacchetti personalizzati di Unity seguenti, **nell'ordine in cui sono elencati**:</span><span class="sxs-lookup"><span data-stu-id="ecc27-149">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="ecc27-150">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (versione 2.1.1)</span><span class="sxs-lookup"><span data-stu-id="ecc27-150">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (version 2.1.1)</span></span>
* [<span data-ttu-id="ecc27-151">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span><span class="sxs-lookup"><span data-stu-id="ecc27-151">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [<span data-ttu-id="ecc27-152">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage</span><span class="sxs-lookup"><span data-stu-id="ecc27-152">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage)
* [<span data-ttu-id="ecc27-153">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.3.0.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="ecc27-153">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.3.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.3.0.0.unitypackage)

> [!TIP]
> <span data-ttu-id="ecc27-154">Per rivedere la procedura di importazione di un pacchetto personalizzato di Unity, puoi fare riferimento alle istruzioni contenute in [Importare Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="ecc27-154">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="ecc27-155">Dopo l'importazione degli asset dell'esercitazione, la finestra Project (Progetto) avrà un aspetto simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="ecc27-155">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial1-section4-step1-1.png)

> [!NOTE]
> <span data-ttu-id="ecc27-157">Dopo aver importato il pacchetto di asset dell'esercitazione MultiUserCapabilities, nella finestra della console verranno visualizzati alcuni errori [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246) che indicano che manca il tipo o lo spazio dei nomi.</span><span class="sxs-lookup"><span data-stu-id="ecc27-157">After importing the MultiUserCapabilities tutorial assets package, you will see several [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246) errors in the Console window stating that the type or namespace is missing.</span></span> <span data-ttu-id="ecc27-158">Si tratta di un comportamento previsto, che verrà risolto nella prossima sezione quando importerai gli asset di Photon.</span><span class="sxs-lookup"><span data-stu-id="ecc27-158">This is to be expected and will be resolved in the next section when you import the Photon assets.</span></span>

## <a name="importing-the-photon-assets"></a><span data-ttu-id="ecc27-159">Importazione degli asset di Photon</span><span class="sxs-lookup"><span data-stu-id="ecc27-159">Importing the Photon assets</span></span>

<span data-ttu-id="ecc27-160">In questa sezione importerai gli asset di Photon Unity Network (PUN) da Unity Asset Store.</span><span class="sxs-lookup"><span data-stu-id="ecc27-160">In this section, you will import the Photon Unity Network (PUN) assets from Unity's Asset Store.</span></span>

<span data-ttu-id="ecc27-161">Nel menu di Unity seleziona **Window** (Finestra) > **Asset Store** per aprire la finestra di Asset Store, cerca e seleziona **PUN 2 - FREE** in Exit Games (Giochi in uscita) e quindi fai clic sul pulsante **Download** (Scarica) per scaricare il pacchetto di asset nel tuo account Unity:</span><span class="sxs-lookup"><span data-stu-id="ecc27-161">In the Unity menu, select **Window** > **Asset Store** to open the Asset Store window, search for and select **PUN 2 - FREE** from Exit Games, and then click the **Download** button to download the asset package to your Unity account:</span></span>

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial1-section5-step1-1.png)

<span data-ttu-id="ecc27-163">Al termine del download, fai clic sul pulsante **Import** (Importa) per aprire la finestra Import Unity Package (Importa pacchetto Unity):</span><span class="sxs-lookup"><span data-stu-id="ecc27-163">When the download is complete, click the **Import** button to open the Import Unity Package window:</span></span>

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial1-section5-step1-2.png)

<span data-ttu-id="ecc27-165">Nella finestra Import Unity Package (Importa il pacchetto Unity), fai clic sul pulsante **All** (Tutti) per assicurarti che vengano selezionati tutti gli asset e quindi fai clic sul pulsante **Import** (Importa) per importare gli asset:</span><span class="sxs-lookup"><span data-stu-id="ecc27-165">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial1-section5-step1-3.png)

<span data-ttu-id="ecc27-167">Dopo che Unity ha completato il processo di importazione, verrà visualizzata la finestra PUN Wizard (Creazione guidata PUN) con il menu PUN Setup (Configurazione PUN) caricato. Per il momento puoi ignorare o chiudere questa finestra:</span><span class="sxs-lookup"><span data-stu-id="ecc27-167">Once Unity has completed the import process, the Pun Wizard window will appear with the PUN Setup menu loaded, you can ignore or close this window for now:</span></span>

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial1-section5-step1-4.png)

## <a name="setting-up-photon"></a><span data-ttu-id="ecc27-169">Configurazione di Photon</span><span class="sxs-lookup"><span data-stu-id="ecc27-169">Setting up Photon</span></span>

<span data-ttu-id="ecc27-170">In questa sezione creerai un account Photon, se non ne hai già uno, e una nuova applicazione PUN.</span><span class="sxs-lookup"><span data-stu-id="ecc27-170">In this section, you will create a Photon account, if you don't already have one, and create a new PUN application.</span></span>

<span data-ttu-id="ecc27-171">Passa al <a href="https://dashboard.photonengine.com/account/signin" target="_blank">dashboard</a> di Photon ed esegui l'accesso se hai già un account che vuoi usare. In caso contrario, fai clic sul collegamento **Create One** (Creane uno) e segui le istruzioni per la registrazione di un nuovo account:</span><span class="sxs-lookup"><span data-stu-id="ecc27-171">Navigate to the Photon <a href="https://dashboard.photonengine.com/account/signin" target="_blank">dashboard</a> and sign in if you already have an account you want to use, otherwise, click the **Create One** link and follow the instructions to register a new account:</span></span>

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial1-section6-step1-1.png)

<span data-ttu-id="ecc27-173">Una volta eseguito l'accesso, fai clic sul pulsante **Create a New App** (Crea una nuova app):</span><span class="sxs-lookup"><span data-stu-id="ecc27-173">Once signed in, click the **Create a New App** button:</span></span>

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial1-section6-step1-2.png)

<span data-ttu-id="ecc27-175">Nella pagina Create a New Application (Crea una nuova applicazione) immetti i valori seguenti:</span><span class="sxs-lookup"><span data-stu-id="ecc27-175">On the Create a New Application page, enter the following values:</span></span>

* <span data-ttu-id="ecc27-176">In Photon Type (Tipo Photon) seleziona Photon PUN</span><span class="sxs-lookup"><span data-stu-id="ecc27-176">For Photon Type, select Photon PUN</span></span>
* <span data-ttu-id="ecc27-177">In Name (Nome) immetti un nome appropriato, ad esempio _MRTK Tutorials_</span><span class="sxs-lookup"><span data-stu-id="ecc27-177">For Name, enter a suitable name, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="ecc27-178">In Description (Descrizione) immetti facoltativamente una descrizione appropriata</span><span class="sxs-lookup"><span data-stu-id="ecc27-178">For Description, optionally enter a suitable description</span></span>
* <span data-ttu-id="ecc27-179">In Url lascia il campo vuoto</span><span class="sxs-lookup"><span data-stu-id="ecc27-179">For Url, leave the field empty</span></span>

<span data-ttu-id="ecc27-180">Fai quindi clic sul pulsante **Create** (Crea) per creare la nuova applicazione:</span><span class="sxs-lookup"><span data-stu-id="ecc27-180">Then click the **Create** button to create the new application:</span></span>

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial1-section6-step1-3.png)

<span data-ttu-id="ecc27-182">Al termine del processo di creazione, nel dashboard verrà visualizzata la nuova applicazione PUN:</span><span class="sxs-lookup"><span data-stu-id="ecc27-182">Once Photon has finished the creation process, the new PUN application will appear on your dashboard:</span></span>

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial1-section6-step1-4.png)

## <a name="connecting-the-unity-project-to-the-pun-application"></a><span data-ttu-id="ecc27-184">Connessione del progetto Unity all'applicazione PUN</span><span class="sxs-lookup"><span data-stu-id="ecc27-184">Connecting the Unity project to the PUN application</span></span>

<span data-ttu-id="ecc27-185">In questa sezione connetterai il progetto Unity all'applicazione PUN creata nella sezione precedente.</span><span class="sxs-lookup"><span data-stu-id="ecc27-185">In this section, you will connect your Unity project to the PUN application you created in the previous section.</span></span>

<span data-ttu-id="ecc27-186">Nel dashboard di Photon fai clic sul campo **App ID** (ID app) per visualizzare l'ID dell'app e quindi copialo negli Appunti:</span><span class="sxs-lookup"><span data-stu-id="ecc27-186">On the Photon dashboard, click the **App ID** field to reveal the app ID, then copy it to your clipboard:</span></span>

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial1-section7-step1-1.png)

<span data-ttu-id="ecc27-188">Nel menu di Unity seleziona **Window** (Finestra) > **Photon Unity Networking** > **PUN Wizard** (Creazione guidata PUN) per aprire la finestra PUN Wizard (Creazione guidata PUN), fai clic sul pulsante **Setup Project** (Configura progetto) per aprire il menu PUN Setup (Configurazione PUN) ed esegui la configurazione nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="ecc27-188">In the Unity menu, select **Window** > **Photon Unity Networking** > **PUN Wizard** to open the Pun Wizard window, click the **Setup Project** button to open the PUN Setup menu, and configure it as follows:</span></span>

* <span data-ttu-id="ecc27-189">Nel campo **AppId or Email** (ID app o e-mail) incolla l'ID dell'app PUN copiato nel passaggio precedente</span><span class="sxs-lookup"><span data-stu-id="ecc27-189">In the **AppId or Email** field, paste the PUN app ID you copied in the previous step</span></span>

<span data-ttu-id="ecc27-190">Fai quindi clic sul pulsante **Setup Project** (Configura progetto) per applicare l'ID dell'app:</span><span class="sxs-lookup"><span data-stu-id="ecc27-190">Then click the **Setup Project** button to apply the app ID:</span></span>

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial1-section7-step1-2.png)

<span data-ttu-id="ecc27-192">Dopo che Unity ha terminato il processo di configurazione di PUN, nel menu PUN Setup (Configurazione PUN) verrà visualizzato il messaggio **Done!** (Fatto)</span><span class="sxs-lookup"><span data-stu-id="ecc27-192">Once Unity has finished the PUN setup process, the PUN Setup menu will display the message **Done!**</span></span> <span data-ttu-id="ecc27-193">e nella finestra Project (Progetto) verrà selezionato automaticamente l'asset **PhotonServerSettings** in modo che le relative proprietà siano visualizzate nella finestra Inspector (Controllo):</span><span class="sxs-lookup"><span data-stu-id="ecc27-193">and automatically select the **PhotonServerSettings** asset in the Project window so its properties are displayed in the Inspector window:</span></span>

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial1-section7-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="ecc27-195">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="ecc27-195">Congratulations</span></span>

<span data-ttu-id="ecc27-196">Hai creato un'applicazione Photon PUN e l'hai connessa al progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="ecc27-196">You have successfully created a Photon PUN application and connected it to your Unity project.</span></span> <span data-ttu-id="ecc27-197">Il passaggio successivo consiste nel consentire connessioni con altri utenti, in modo che ogni utente possa visualizzare il lavoro svolto dagli altri.</span><span class="sxs-lookup"><span data-stu-id="ecc27-197">Your next step is to allow connections with other users so that multiple users can see each other.</span></span>

<span data-ttu-id="ecc27-198">[Esercitazione successiva: 2. Connessione di più utenti](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="ecc27-198">[Next tutorial: 2. Connecting multiple users](mrlearning-sharing(photon)-ch2.md)</span></span>

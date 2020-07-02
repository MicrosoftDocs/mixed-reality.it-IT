---
title: Esercitazioni su Ancoraggi nello spazio di Azure - 1. Introduzione ad Ancoraggi nello spazio di Azure
description: Completa questo corso per informazioni su come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: 385b302f3a2b9ad80527387353746947d91e3aa3
ms.sourcegitcommit: 4282d92e93869e4829338bdf7d981c3ee0260bfd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85216302"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="441df-105">1. Introduzione ad Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="441df-105">1. Getting started with Azure Spatial Anchors</span></span>

## <a name="overview"></a><span data-ttu-id="441df-106">Panoramica</span><span class="sxs-lookup"><span data-stu-id="441df-106">Overview</span></span>

<span data-ttu-id="441df-107">Questa è la seconda serie di esercitazioni su HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="441df-107">Welcome to the second series of the HoloLens 2 tutorials.</span></span> <span data-ttu-id="441df-108">In questa serie di esercitazioni, suddivisa in quattro parti, apprenderai le nozioni fondamentali su Ancoraggi nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="441df-108">In this four-part tutorial series, you will learn the fundamentals of Azure Spatial Anchors.</span></span>

<span data-ttu-id="441df-109">Questa prima esercitazione, [Introduzione ad Ancoraggi nello spazio di Azure](mrlearning-asa-ch1.md), illustra i diversi passaggi da seguire per avviare e arrestare una sessione di Azure e per creare, caricare e scaricare gli ancoraggi di Azure in un singolo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="441df-109">In this first tutorial, [Getting started with Azure Spatial Anchors](mrlearning-asa-ch1.md), you will explore the various steps required to start and stop an Azure session and create, upload, and download Azure anchors on a single device.</span></span>

<span data-ttu-id="441df-110">La seconda esercitazione, [Salvataggio, recupero e condivisione di ancoraggi nello spazio di Azure](mrlearning-asa-ch2.md), illustra come salvare gli ancoraggi nello spazio di Azure in più sessioni di app salvando le informazioni sugli ancoraggi nello spazio di archiviazione di HoloLens 2 e come condividere queste informazioni con altri dispositivi per l'allineamento degli ancoraggi su più dispositivi.</span><span class="sxs-lookup"><span data-stu-id="441df-110">In the second tutorial, [Saving, retrieving, and sharing Azure Spatial Anchors](mrlearning-asa-ch2.md), you will learn how to save Azure Spatial Anchors across multiple app sessions by saving anchor information to the HoloLens 2's storage and how to share this anchor information to other devices for a multi-device anchor alignment.</span></span>

<span data-ttu-id="441df-111">La terza esercitazione, [Visualizzazione del feedback su Ancoraggi nello spazio di Azure](mrlearning-asa-ch3.md), illustra come fornire agli utenti feedback sugli eventi e sullo stato degli ancoraggi con Ancoraggi nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="441df-111">In the third tutorial, [Displaying Azure Spatial Anchor feedback](mrlearning-asa-ch3.md), you will learn how to provide users with feedback about anchor events and statuses when using Azure Spatial Anchors.</span></span>

<span data-ttu-id="441df-112">La quarta esercitazione, [Ancoraggi nello spazio di Azure per Android e iOS](mrlearning-asa-ch4.md), illustra come creare e distribuire il progetto nei dispositivi Android e iOS.</span><span class="sxs-lookup"><span data-stu-id="441df-112">In the fourth tutorial, [Azure Spatial Anchors for Android and iOS](mrlearning-asa-ch4.md), you will learn how to build and deploy your project to Android and iOS devices.</span></span>

## <a name="objectives"></a><span data-ttu-id="441df-113">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="441df-113">Objectives</span></span>

* <span data-ttu-id="441df-114">Scopri le nozioni fondamentali sullo sviluppo con Ancoraggi nello spazio di Azure per HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="441df-114">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="441df-115">Creare, caricare e scaricare ancoraggi nello spazio</span><span class="sxs-lookup"><span data-stu-id="441df-115">Create, upload, and download spatial anchors</span></span>

## <a name="prerequisites"></a><span data-ttu-id="441df-116">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="441df-116">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="441df-117">Se non hai ancora completato la serie di [Esercitazioni introduttive](mrlearning-base.md), è consigliabile completare prima queste esercitazioni.</span><span class="sxs-lookup"><span data-stu-id="441df-117">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="441df-118">Un PC Windows 10 configurato in cui siano [installati gli strumenti](install-the-tools.md) corretti</span><span class="sxs-lookup"><span data-stu-id="441df-118">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="441df-119">Windows 10 SDK 10.0.18362.0 o versioni successive</span><span class="sxs-lookup"><span data-stu-id="441df-119">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="441df-120">Alcune funzionalità di programmazione C# di base</span><span class="sxs-lookup"><span data-stu-id="441df-120">Some basic C# programming ability</span></span>
* <span data-ttu-id="441df-121">Un dispositivo HoloLens (prima generazione) o HoloLens 2 [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="441df-121">A HoloLens (1st Gen) or HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="441df-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.2.X installato e il modulo di supporto delle compilazioni UWP (Universal Windows Platform) aggiunto</span><span class="sxs-lookup"><span data-stu-id="441df-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="441df-123">Completa la sezione [Creare una risorsa di Ancoraggi nello spazio](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) dell'esercitazione di [avvio rapido per HoloLens](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens).</span><span class="sxs-lookup"><span data-stu-id="441df-123">Complete the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [HoloLens quickstart](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial.</span></span>

<span data-ttu-id="441df-124">Se è prevista la distribuzione su Android</span><span class="sxs-lookup"><span data-stu-id="441df-124">If you intend to deploy to Android</span></span>
* <span data-ttu-id="441df-125">Un dispositivo Android <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">con le opzioni di sviluppo abilitate</a> e <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">supportato da ARCore</a> con connessione USB a un computer con Windows o macOS</span><span class="sxs-lookup"><span data-stu-id="441df-125">A <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">developer enabled</a> and <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore capable</a> Android device with USB connection to your Windows or macOS computer</span></span>
* <span data-ttu-id="441df-126"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.2.X installato e il modulo Android Build Support aggiunto</span><span class="sxs-lookup"><span data-stu-id="441df-126"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Android Build Support module added</span></span>

<span data-ttu-id="441df-127">Se è prevista la distribuzione su iOS</span><span class="sxs-lookup"><span data-stu-id="441df-127">If you intend to deploy to iOS</span></span>
* <span data-ttu-id="441df-128">Un computer macOS con la versione più recente di <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> e <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installata</span><span class="sxs-lookup"><span data-stu-id="441df-128">A macOS computer with the the latest version of <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> and <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installed</span></span>
* <span data-ttu-id="441df-129">Un dispositivo iOS <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">compatibile con ARKit</a> con connessione USB al computer macOS</span><span class="sxs-lookup"><span data-stu-id="441df-129">An <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit compatible</a> iOS device with USB connection to your macOS computer</span></span>
* <span data-ttu-id="441df-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.2.X installato e il modulo iOS Build Support aggiunto</span><span class="sxs-lookup"><span data-stu-id="441df-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the iOS Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="441df-131">La versione di Unity consigliata per questa serie di esercitazioni è Unity 2019.2.X.</span><span class="sxs-lookup"><span data-stu-id="441df-131">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="441df-132">Questa istruzione sostituisce gli eventuali requisiti o suggerimenti relativi alla versione di Unity indicati negli argomenti visualizzabili facendo clic sui collegamenti dei prerequisiti sopra riportati.</span><span class="sxs-lookup"><span data-stu-id="441df-132">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="441df-133">Creazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="441df-133">Creating the Unity project</span></span>
<!-- TODO: Consider renaming to 'Creating and preparing the Unity project'-->

<span data-ttu-id="441df-134">In questa sezione creerai un nuovo progetto Unity per prepararti allo sviluppo con MRTK.</span><span class="sxs-lookup"><span data-stu-id="441df-134">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="441df-135">A questo scopo, segui prima l'esercitazione [Inizializzazione del progetto e prima applicazione](mrlearning-base-ch1.md), escluse le istruzioni della sezione [Compilare l'applicazione nel dispositivo](mrlearning-base-ch1.md#build-your-application-to-your-device), che include i passaggi seguenti:</span><span class="sxs-lookup"><span data-stu-id="441df-135">For this, first follow the [Initializing your project and first application](mrlearning-base-ch1.md), excluding the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="441df-136">[Creare un nuovo progetto Unity](mrlearning-base-ch1.md#create-new-unity-project) e assegnargli un nome appropriato, ad esempio *MRTK Tutorials*</span><span class="sxs-lookup"><span data-stu-id="441df-136">[Create new Unity project](mrlearning-base-ch1.md#create-new-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>

2. [<span data-ttu-id="441df-137">Configurare il progetto Unity per Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="441df-137">Configure the Unity project for Windows Mixed Reality</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [<span data-ttu-id="441df-138">Importare le risorse essenziali TextMesh Pro</span><span class="sxs-lookup"><span data-stu-id="441df-138">Import TextMesh Pro Essential Resources</span></span>](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [<span data-ttu-id="441df-139">Importare Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="441df-139">Import the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [<span data-ttu-id="441df-140">Configurare il progetto Unity per Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="441df-140">Configure the Unity project for the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. <span data-ttu-id="441df-141">[Aggiungere Mixed Reality Toolkit alla scena di Unity](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) e assegnare alla scena un nome appropriato, ad esempio *AzureSpatialAnchors*</span><span class="sxs-lookup"><span data-stu-id="441df-141">[Add the Mixed Reality Toolkit to the Unity scene](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) and give the scene a suitable name, for example, *AzureSpatialAnchors*</span></span>

<span data-ttu-id="441df-142">Segui quindi le istruzioni riportate in [Come configurare i profili di Mixed Reality Toolkit (modifica dell'opzione di visualizzazione della mesh di consapevolezza spaziale)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) per impostare **DefaultHoloLens2ConfigurationProfile** come profilo di configurazione MRTK per la scena e modificare in **Occlusion** (Occlusione) le opzioni di visualizzazione per la mesh di consapevolezza spaziale.</span><span class="sxs-lookup"><span data-stu-id="441df-142">Then follow the [How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

> [!CAUTION]
> <span data-ttu-id="441df-143">Come indicato nelle istruzioni contenute in [Configurare il progetto Unity per Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit), è fortemente sconsigliabile abilitare MSBuild per Unity.</span><span class="sxs-lookup"><span data-stu-id="441df-143">As mentioned in the [Configure the Unity project for the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) instructions linked above, it is strongly recommended to not enable MSBuild for Unity.</span></span>

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="441df-144">Aggiunta di pacchetti di Unity incorporati</span><span class="sxs-lookup"><span data-stu-id="441df-144">Adding inbuilt Unity packages</span></span>
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

<span data-ttu-id="441df-145">In questa sezione installerai il pacchetto AR Foundation incorporato di Unity perché è un prerequisito dell'SDK di Ancoraggi nello spazio di Azure che importerai nella sezione successiva.</span><span class="sxs-lookup"><span data-stu-id="441df-145">In this section, you will install Unity's inbuilt AR Foundation package because it is required by the Azure Spatial Anchors SDK you will import in the next section.</span></span>

<span data-ttu-id="441df-146">Nel menu di Unity seleziona **Window** (Finestra) > **Package Manager** (Gestione pacchetti):</span><span class="sxs-lookup"><span data-stu-id="441df-146">In the Unity menu, select **Window** > **Package Manager**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="441df-148">Potrebbero essere necessari alcuni secondi prima che il pacchetto AR Foundation venga visualizzato nell'elenco.</span><span class="sxs-lookup"><span data-stu-id="441df-148">It might take a few seconds before the AR Foundation package appears in the list.</span></span>

<span data-ttu-id="441df-149">Nella finestra Package Manager (Gestione pacchetti) seleziona **AR Foundation** e installa il pacchetto facendo clic sul pulsante **Install** (Installa):</span><span class="sxs-lookup"><span data-stu-id="441df-149">In the Package Manager window, select **AR Foundation** and install the package by clicking the **Install** button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="441df-151">Importazione degli asset dell'esercitazione</span><span class="sxs-lookup"><span data-stu-id="441df-151">Importing the tutorial assets</span></span>

<span data-ttu-id="441df-152">Scarica e **importa** i pacchetti personalizzati di Unity seguenti, **nell'ordine in cui sono elencati**:</span><span class="sxs-lookup"><span data-stu-id="441df-152">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="441df-153">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (versione 2.1.1)</span><span class="sxs-lookup"><span data-stu-id="441df-153">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (version 2.1.1)</span></span>
* [<span data-ttu-id="441df-154">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span><span class="sxs-lookup"><span data-stu-id="441df-154">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [<span data-ttu-id="441df-155">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage</span><span class="sxs-lookup"><span data-stu-id="441df-155">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage)

> [!TIP]
> <span data-ttu-id="441df-156">Per rivedere la procedura di importazione di un pacchetto personalizzato di Unity, puoi fare riferimento alle istruzioni contenute in [Importare Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="441df-156">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="441df-157">Dopo l'importazione degli asset dell'esercitazione, la finestra Project (Progetto) avrà un aspetto simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="441df-157">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section3-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a><span data-ttu-id="441df-159">Creazione e preparazione della scena</span><span class="sxs-lookup"><span data-stu-id="441df-159">Creating and preparing the scene</span></span>
<!-- TODO: Consider renaming to 'Preparing the scene' -->

<span data-ttu-id="441df-160">In questa sezione preparerai la scena aggiungendo alcuni dei prefab dell'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="441df-160">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="441df-161">Nella finestra Project (Progetto) passa alla cartella **Assets** (Asset) > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** (Prefab).</span><span class="sxs-lookup"><span data-stu-id="441df-161">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder.</span></span> <span data-ttu-id="441df-162">Tenendo premuto CTRL, fai clic su **ButtonParent**, **DebugWindow**, **Instructions** e **ParentAnchor** per selezionare i quattro prefab:</span><span class="sxs-lookup"><span data-stu-id="441df-162">While holding down the CTRL button, click on **ButtonParent**, **DebugWindow**, **Instructions**, and **ParentAnchor** to select the four prefabs:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-1.png)

<span data-ttu-id="441df-164">Trascina i quattro prefab selezionati nella finestra Hierarchy (Gerarchia) per aggiungerli alla scena:</span><span class="sxs-lookup"><span data-stu-id="441df-164">With the four prefabs still selected, drag them into the Hierarchy window to add them to the scene:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-2.png)

<span data-ttu-id="441df-166">Per concentrarti sugli oggetti nella scena, puoi fare doppio clic sull'oggetto ParentAnchor e quindi fare di nuovo leggermente zoom indietro:</span><span class="sxs-lookup"><span data-stu-id="441df-166">To focus in on the objects in the scene, you can double-click on the ParentAnchor object, and then zoom slightly out again:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-3.png)

> [!TIP]
> <span data-ttu-id="441df-168">Se trovi che le icone grandi nella scena, come quelle a forma di "T", siano motivo di distrazione, puoi nasconderle <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">disattivando i gizmo</a>.</span><span class="sxs-lookup"><span data-stu-id="441df-168">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="441df-169">Configurazione dei pulsanti per il funzionamento della scena</span><span class="sxs-lookup"><span data-stu-id="441df-169">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="441df-170">In questa sezione aggiungerai script alla scena per creare una serie di eventi Button che illustrano le nozioni fondamentali sul comportamento degli ancoraggi locali e di Ancoraggi nello spazio di Azure in un'applicazione.</span><span class="sxs-lookup"><span data-stu-id="441df-170">In this section, you will add scripts into the scene to create a series of button events that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an application.</span></span>

### <a name="1-configure-the-pressable-button-holo-lens-2-script-component"></a><span data-ttu-id="441df-171">1. Configurare il componente Pressable Button Holo Lens 2 (Script)</span><span class="sxs-lookup"><span data-stu-id="441df-171">1. Configure the Pressable Button Holo Lens 2 (Script) component</span></span>

<span data-ttu-id="441df-172">Nella finestra Hierarchy (Gerarchia) espandi l'oggetto **ButtonParent** e seleziona il primo oggetto figlio denominato **StartAzureSession**:</span><span class="sxs-lookup"><span data-stu-id="441df-172">In the Hierarchy window, expand the **ButtonParent** object and select the first child object named **StartAzureSession**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-1.png)

<span data-ttu-id="441df-174">Nella finestra Inspector (Controllo) individua il componente **Pressable Button Holo Lens 2 (Script)** e aggiungi un nuovo listener di eventi all'evento **Button Pressed ()** facendo clic sull'icona **+** :</span><span class="sxs-lookup"><span data-stu-id="441df-174">In the Inspector window, locate the **Pressable Button Holo Lens 2 (Script)** component and add a new event listener to the **Button Pressed ()** event by clicking the **+** icon:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-2.png)

<span data-ttu-id="441df-176">Con l'oggetto StartAzureSession ancora selezionato nella finestra Hierarchy (Gerarchia), fai clic e trascina l'oggetto **ParentAnchor** dalla finestra Hierarchy (Gerarchia) nel campo vuoto **None (Object)** (Nessuno - Oggetto) del listener di eventi appena aggiunto per fare in modo che l'oggetto ParentAnchor rimanga in ascolto degli eventi di pressione attivati da questo pulsante:</span><span class="sxs-lookup"><span data-stu-id="441df-176">With the StartAzureSession object still selected in the Hierarchy window, click-and-drag the **ParentAnchor** object from the Hierarchy window into the empty **None (Object)** field of the event listener you just added to make the ParentAnchor object listen for button pressed events from this button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-3.png)

<span data-ttu-id="441df-178">Fai clic sull'elenco a discesa **No Function** (Nessuna funzione) dello stesso listener di eventi e quindi seleziona **AnchorModuleScript** > **StartAzureSession ()** per impostare la funzione StartAzureSession () come azione da eseguire quando vengono attivati eventi di pressione da questo pulsante:</span><span class="sxs-lookup"><span data-stu-id="441df-178">Click the **No Function** dropdown of the same event listener, then select **AnchorModuleScript** > **StartAzureSession ()** to set the StartAzureSession () function as the action that is triggered when the button pressed events is fired from this button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-4.png)

### <a name="2-configure-the-interactable-script-component"></a><span data-ttu-id="441df-180">2. Configurare il componente Interactable (Script)</span><span class="sxs-lookup"><span data-stu-id="441df-180">2. Configure the Interactable (Script) component</span></span>

<span data-ttu-id="441df-181">Con l'oggetto StartAzureSession ancora selezionato nella finestra Hierarchy (Gerarchia), nella finestra Inspector (Controllo) individua il componente **Interactable (script)** e ripeti la stessa procedura descritta nel passaggio 1 per l'evento **OnClick ()** :</span><span class="sxs-lookup"><span data-stu-id="441df-181">With the StartAzureSession object still selected in the Hierarchy window, in the Inspector window, locate the **Interactable (Script)** component and repeat the same process as in step 1 above for the **OnClick ()** event:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step2-1.png)

### <a name="3-configure-the-remaining-buttons"></a><span data-ttu-id="441df-183">3. Configurare i pulsanti rimanenti</span><span class="sxs-lookup"><span data-stu-id="441df-183">3. Configure the remaining buttons</span></span>

<span data-ttu-id="441df-184">Per ognuno dei pulsanti rimanenti, completa il processo descritto nei passaggi 1 e 2 precedenti per assegnare funzioni a entrambi gli eventi **Button Pressed ()** e **OnClick ()** :</span><span class="sxs-lookup"><span data-stu-id="441df-184">For each of the remaining buttons, complete the process outlined in step 1 and 2 above to assign functions to both the **Button Pressed ()** and **OnClick ()** events:</span></span>

* <span data-ttu-id="441df-185">Per l'oggetto **StopAzureSession**, assegna la funzione AnchorModuleScript > **StopAzureSession ()** .</span><span class="sxs-lookup"><span data-stu-id="441df-185">For the **StopAzureSession** object, assign the AnchorModuleScript > **StopAzureSession ()** function.</span></span>
* <span data-ttu-id="441df-186">Per l'oggetto **CreateAzureAnchor**, assegna la funzione AnchorModuleScript > **CreateAzureAnchor ()** ,</span><span class="sxs-lookup"><span data-stu-id="441df-186">For the **CreateAzureAnchor** object, assign the AnchorModuleScript > **CreateAzureAnchor ()** function,</span></span>
  * <span data-ttu-id="441df-187">quindi trascina di nuovo **ParentAnchor** nel campo vuoto **None (Game Object)** (Nessuno - Oggetto gioco).</span><span class="sxs-lookup"><span data-stu-id="441df-187">then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
* <span data-ttu-id="441df-188">Per l'oggetto **RemoveLocalAnchor**, assegna la funzione AnchorModuleScript > **RemoveLocalAnchor ()** ,</span><span class="sxs-lookup"><span data-stu-id="441df-188">For the **RemoveLocalAnchor** object, assign the AnchorModuleScript > **RemoveLocalAnchor ()** function,</span></span>
  * <span data-ttu-id="441df-189">quindi trascina di nuovo **ParentAnchor** nel campo vuoto **None (Game Object)** (Nessuno - Oggetto gioco).</span><span class="sxs-lookup"><span data-stu-id="441df-189">then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
* <span data-ttu-id="441df-190">Per l'oggetto **FindAzureAnchor**, assegna la funzione AnchorModuleScript > **FindAzureAnchor ()** .</span><span class="sxs-lookup"><span data-stu-id="441df-190">For the **FindAzureAnchor** object, assign the AnchorModuleScript > **FindAzureAnchor ()** function.</span></span>
* <span data-ttu-id="441df-191">Per l'oggetto **DeleteAzureAnchor**, assegna la funzione AnchorModuleScript > **DeleteAzureAnchor ()** .</span><span class="sxs-lookup"><span data-stu-id="441df-191">For the **DeleteAzureAnchor** object, assign the AnchorModuleScript > **DeleteAzureAnchor ()** function.</span></span>

### <a name="4-connect-the-scene-to-the-azure-resource"></a><span data-ttu-id="441df-192">4. Connettere la scena alla risorsa di Azure</span><span class="sxs-lookup"><span data-stu-id="441df-192">4. Connect the scene to the Azure resource</span></span>

<span data-ttu-id="441df-193">Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **ParentAnchor** e nella finestra Inspector (Controllo) scorri verso il basso fino al componente **Spatial Anchor Manager (Script)** .</span><span class="sxs-lookup"><span data-stu-id="441df-193">In the Hierarchy window, select the **ParentAnchor** object and in the Inspector window, scroll down to the **Spatial Anchor Manager (Script)** component.</span></span>

<span data-ttu-id="441df-194">Nella sezione **Credentials** (Credenziali) incolla l'ID e la chiave dell'account di Ancoraggi nello spazio, che hai creato come parte dei [prerequisiti](mrlearning-asa-ch1.md#prerequisites) di questa esercitazione, nei corrispondenti campi **Spatial Anchors Account Id** (ID account Ancoraggi nello spazio) e **Spatial Anchors Account Key** (Chiave account Ancoraggi nello spazio):</span><span class="sxs-lookup"><span data-stu-id="441df-194">Then, in the **Credentials** section, paste your Spatial Anchors Account ID and Key, which you created as part of this tutorial's [Prerequisites](mrlearning-asa-ch1.md#prerequisites), into the corresponding **Spatial Anchors Account Id** and **Spatial Anchors Account Key** fields:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step4-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="441df-196">Test dei comportamenti di base di Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="441df-196">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="441df-197">Ora che la scena è configurata in modo da illustrare gli elementi di base di Ancoraggi nello spazio di Azure, è il momento di distribuire l'app per poter provare Ancoraggi nello spazio di Azure in prima persona.</span><span class="sxs-lookup"><span data-stu-id="441df-197">Now that your scene is configured to demonstrate the basics of Azure Spatial Anchors, it is time to deploy the app so you can experience Azure Spatial Anchors firsthand.</span></span>

### <a name="1-add-additional-required-capabilities"></a><span data-ttu-id="441df-198">1. Aggiungere altre funzionalità necessarie</span><span class="sxs-lookup"><span data-stu-id="441df-198">1. Add additional required capabilities</span></span>

<span data-ttu-id="441df-199">Dal menu di Unity scegli **Edit** (Modifica) > **Project Settings** (Impostazioni del progetto) per visualizzare la finestra corrispondente:</span><span class="sxs-lookup"><span data-stu-id="441df-199">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-1.png)

<span data-ttu-id="441df-201">Nella finestra Project Settings (Impostazioni del progetto) seleziona **Player** (Lettore) e quindi **Publishing Settings** (Impostazioni di pubblicazione):</span><span class="sxs-lookup"><span data-stu-id="441df-201">In the Player Settings window, select **Player** and then **Publishing Settings**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-2.png)

<span data-ttu-id="441df-203">In **Publishing Settings** (Impostazioni di pubblicazione) scorri verso il basso fino alla sezione **Capabilities** (Funzionalità) e verifica che siano abilitate le funzionalità **InternetClient**, **Microphone** e **SpatialPerception**, che hai abilitato al momento della creazione del progetto all'inizio dell'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="441df-203">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="441df-204">Abilita quindi le funzionalità **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage** e **Webcam**:</span><span class="sxs-lookup"><span data-stu-id="441df-204">Then, enable the **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage**, and **Webcam** capabilities:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a><span data-ttu-id="441df-206">2. Distribuire l'app nel dispositivo HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="441df-206">2. Deploy the app to your HoloLens 2</span></span>

<span data-ttu-id="441df-207">Non è possibile eseguire Ancoraggi nello spazio di Azure in Unity. Pertanto, per testare la funzionalità di questo servizio devi distribuire il progetto nel tuo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="441df-207">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to deploy the project to your device.</span></span>

> [!TIP]
> <span data-ttu-id="441df-208">Per un promemoria su come compilare e distribuire il progetto Unity in HoloLens 2, puoi fare riferimento alle istruzioni riportate in [Compilare l'applicazione nel dispositivo](mrlearning-base-ch1.md#build-your-application-to-your-device).</span><span class="sxs-lookup"><span data-stu-id="441df-208">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions.</span></span>

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a><span data-ttu-id="441df-209">3. Eseguire l'app in HoloLens 2 e seguire le istruzioni in-app</span><span class="sxs-lookup"><span data-stu-id="441df-209">3. Run the app on your HoloLens 2 and follow the in-app instructions</span></span>

> [!CAUTION]
> <span data-ttu-id="441df-210">Ancoraggi nello spazio di Azure usa Internet per salvare e caricare i dati di ancoraggio. Assicurati quindi che il dispositivo sia connesso a Internet.</span><span class="sxs-lookup"><span data-stu-id="441df-210">Azure Spatial Anchors uses the internet to save and load the anchor data so make sure your device is connected to the internet.</span></span>

<span data-ttu-id="441df-211">Quando l'applicazione è in esecuzione nel dispositivo, segui le istruzioni visualizzate nel pannello Azure Spatial Anchor Tutorial Instructions (Istruzioni per l'esercitazione su Ancoraggi nello spazio di Azure):</span><span class="sxs-lookup"><span data-stu-id="441df-211">When the application is running on your device, follow the on-screen instructions displayed on the Azure Spatial Anchor Tutorial Instructions panel:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step3-1.png)

## <a name="anchoring-an-experience"></a><span data-ttu-id="441df-213">Ancoraggio di un'esperienza</span><span class="sxs-lookup"><span data-stu-id="441df-213">Anchoring an experience</span></span>

<span data-ttu-id="441df-214">Nelle sezioni precedenti hai appreso le nozioni fondamentali di Ancoraggi nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="441df-214">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="441df-215">È stato usato un cubo per rappresentare e visualizzare l'oggetto gioco padre con l'ancoraggio collegato.</span><span class="sxs-lookup"><span data-stu-id="441df-215">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="441df-216">In questa sezione apprenderai come ancorare un'intera esperienza inserendola come figlio dell'oggetto ParentAnchor.</span><span class="sxs-lookup"><span data-stu-id="441df-216">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

### <a name="1-add-the-rocket-launcher-experience"></a><span data-ttu-id="441df-217">1. Aggiungere l'esperienza di Rocket Launcher</span><span class="sxs-lookup"><span data-stu-id="441df-217">1. Add the Rocket Launcher experience</span></span>

<span data-ttu-id="441df-218">Nella finestra Project (Progetto) passa alla cartella **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** e seleziona il prefab **RocketLauncher_Complete**:</span><span class="sxs-lookup"><span data-stu-id="441df-218">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder and select the **RocketLauncher_Complete** prefab:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-1.png)

<span data-ttu-id="441df-220">Trascina il prefab RocketLauncher_Complete selezionato sopra l'oggetto **ParentAnchor** nella finestra Hierarchy (Gerarchia) per configurarlo come figlio dell'oggetto ParentAnchor:</span><span class="sxs-lookup"><span data-stu-id="441df-220">With the RocketLauncher_Complete prefab still selected, drag it on top of the **ParentAnchor** object in the Hierarchy window to make it a child of the ParentAnchor object:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-2.png)

### <a name="2-reposition-the-rocket-launcher-experience"></a><span data-ttu-id="441df-222">2. Riposizionare l'esperienza di Rocket Launcher</span><span class="sxs-lookup"><span data-stu-id="441df-222">2. Reposition the Rocket Launcher experience</span></span>

<span data-ttu-id="441df-223">Posiziona, ruota e ridimensiona l'oggetto **RocketLauncher_Complete** in base a un fattore di scala e a un orientamento appropriati, assicurando allo stesso tempo che l'oggetto **ParentAnchor** rimanga esposto, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="441df-223">Position, rotate, and scale the **RocketLauncher_Complete** object to a suitable scale and orientation, while also ensuring the **ParentAnchor** object is still exposed, for example:</span></span>

* <span data-ttu-id="441df-224">Trasforma la **posizione** X = 0, Y = -0, Z = 3.75</span><span class="sxs-lookup"><span data-stu-id="441df-224">Transform **Position** X = 0, Y = 0, Z = 3.75</span></span>
* <span data-ttu-id="441df-225">Trasforma la **rotazione** X = 0, Y = 90, Z = 0</span><span class="sxs-lookup"><span data-stu-id="441df-225">Transform **Rotation** X = 0, Y = 90, Z = 0</span></span>
* <span data-ttu-id="441df-226">Trasforma la **scala** X = 10, Y = 10, Z = 10</span><span class="sxs-lookup"><span data-stu-id="441df-226">Transform **Scale** X = 10, Y = 10, Z = 10</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step2-1.png)

<span data-ttu-id="441df-228">Nell'applicazione, gli utenti possono ora riposizionare l'intera esperienza di Rocket Launcher spostando il cubo.</span><span class="sxs-lookup"><span data-stu-id="441df-228">In the application, users may now reposition the entire Rocket Launcher experience by moving the cube.</span></span>

> [!TIP]
> <span data-ttu-id="441df-229">Sono disponibili diversi flussi di esperienza utente per il riposizionamento, tra cui l'uso di un oggetto di riposizionamento (come il cubo usato in questa esercitazione), l'uso di un pulsante per attivare e disattivare un cubo di delimitazione attorno all'esperienza, l'uso di gizmo di posizione e rotazione e altro ancora.</span><span class="sxs-lookup"><span data-stu-id="441df-229">There are a variety of user experience flows for repositioning experiences including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounding box that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="441df-230">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="441df-230">Congratulations</span></span>

<span data-ttu-id="441df-231">In questa esercitazione hai appreso le nozioni fondamentali di Ancoraggi nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="441df-231">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="441df-232">L'esercitazione ha consentito di esaminare i diversi passaggi da seguire per avviare e arrestare una sessione di Ancoraggi nello spazio di Azure e per creare, caricare e scaricare gli ancoraggi nello spazio di Azure in un singolo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="441df-232">The tutorial provided you with several buttons that let you explore the various steps required to start and stop an Azure Spatial Anchors session and create, upload and download Azure Spatial Anchors on a single device.</span></span>

<span data-ttu-id="441df-233">Nella lezione successiva apprenderai come salvare gli ID di ancoraggio di Azure in HoloLens 2 per il recupero, anche dopo il riavvio dell'applicazione, e come trasferire gli ID di ancoraggio tra più dispositivi per ottenere l'allineamento nello spazio.</span><span class="sxs-lookup"><span data-stu-id="441df-233">In the next lesson, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the application is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

[<span data-ttu-id="441df-234">Lezione successiva: 2. Salvataggio, recupero e condivisione di Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="441df-234">Next Lesson: 2. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mrlearning-asa-ch2.md)

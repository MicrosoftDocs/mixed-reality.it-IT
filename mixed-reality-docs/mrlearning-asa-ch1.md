---
title: Esercitazioni sugli ancoraggi spaziali di Azure-1. Introduzione agli ancoraggi spaziali di Azure
description: Completa questo corso per apprendere come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 861c42f9449fcb3cf038258af91088fc927941e5
ms.sourcegitcommit: f4812e1312c4751a22a2de56771c475b22a4ba24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/09/2019
ms.locfileid: "74940979"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="a5a00-105">1. Introduzione agli ancoraggi spaziali di Azure</span><span class="sxs-lookup"><span data-stu-id="a5a00-105">1. Getting started with Azure Spatial Anchors</span></span>

## <a name="overview"></a><span data-ttu-id="a5a00-106">Panoramica</span><span class="sxs-lookup"><span data-stu-id="a5a00-106">Overview</span></span>

<span data-ttu-id="a5a00-107">Benvenuti alla seconda serie di esercitazioni su HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="a5a00-107">Welcome to the second series of the HoloLens 2 tutorials.</span></span> <span data-ttu-id="a5a00-108">In questa serie di esercitazioni in tre parti si apprenderanno le nozioni di base degli ancoraggi spaziali di Azure.</span><span class="sxs-lookup"><span data-stu-id="a5a00-108">In this three-part tutorial series, you will learn the fundamentals of Azure Spatial Anchors.</span></span>

<span data-ttu-id="a5a00-109">Questa prima esercitazione illustra i diversi passaggi necessari per avviare e arrestare una sessione di Azure e creare, caricare e scaricare i punti [di ancoraggio di](mrlearning-asa-ch1.md)Azure in un singolo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a5a00-109">In this first tutorial, [Getting started with Azure Spatial Anchors](mrlearning-asa-ch1.md), you will explore the various steps required to start and stop an Azure session and create, upload, and download Azure anchors on a single device.</span></span>

<span data-ttu-id="a5a00-110">Nella seconda esercitazione, salvare [, recuperare e condividere gli ancoraggi spaziali di Azure](mrlearning-asa-ch2.md), si apprenderà come salvare gli ancoraggi spaziali di Azure tra più sessioni di App salvando le informazioni di ancoraggio nell'archiviazione di HoloLens 2 e come condividere le informazioni di ancoraggio ad altri dispositivi per un allineamento di ancoraggio a più dispositivi.</span><span class="sxs-lookup"><span data-stu-id="a5a00-110">In the second tutorial, [Saving, retrieving, and sharing Azure Spatial Anchors](mrlearning-asa-ch2.md), you will learn how to save Azure Spatial Anchors across multiple app sessions by saving anchor information to the HoloLens 2's storage and how to share this anchor information to other devices for a multi-device anchor alignment.</span></span>

<span data-ttu-id="a5a00-111">Nella terza esercitazione, in cui viene [visualizzato il feedback di ancoraggio spaziale di Azure](mrlearning-asa-ch3.md), si apprenderà come fornire agli utenti feedback sugli eventi e gli Stati di ancoraggio quando si usano gli ancoraggi spaziali di Azure.</span><span class="sxs-lookup"><span data-stu-id="a5a00-111">In the third tutorial, [Displaying Azure Spatial Anchor feedback](mrlearning-asa-ch3.md), you will learn how to provide users with feedback about anchor events and statuses when using Azure Spatial Anchors.</span></span>

## <a name="objectives"></a><span data-ttu-id="a5a00-112">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="a5a00-112">Objectives</span></span>

* <span data-ttu-id="a5a00-113">Scopri le nozioni di base sullo sviluppo con gli ancoraggi spaziali di Azure per HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="a5a00-113">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="a5a00-114">Creare, caricare e scaricare ancoraggi spaziali</span><span class="sxs-lookup"><span data-stu-id="a5a00-114">Create, upload, and download spatial anchors</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a5a00-115">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="a5a00-115">Prerequisites</span></span>

* <span data-ttu-id="a5a00-116">Soddisfare i requisiti elencati nella sezione [prerequisiti](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#prerequisites) della [Guida introduttiva: creare un'app HoloLens Unity che usa](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) l'esercitazione sugli ancoraggi spaziali di Azure.</span><span class="sxs-lookup"><span data-stu-id="a5a00-116">Meet the requirements listed in the [Prerequisites](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#prerequisites) section of the  [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial.</span></span>
* <span data-ttu-id="a5a00-117">Completare la sezione [creare una risorsa ancoraggi spaziali](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) della [Guida introduttiva: creare un'app HoloLens Unity che usa l'esercitazione sugli ancoraggi spaziali di Azure](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) .</span><span class="sxs-lookup"><span data-stu-id="a5a00-117">Complete the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial.</span></span>
* <span data-ttu-id="a5a00-118">Se non è ancora stata completata la serie di [esercitazioni introduttive](mrlearning-base.md) , è consigliabile completare prima queste esercitazioni.</span><span class="sxs-lookup"><span data-stu-id="a5a00-118">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="a5a00-119">Creazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="a5a00-119">Creating the Unity project</span></span>

<span data-ttu-id="a5a00-120">In questa sezione si creerà un nuovo progetto Unity e lo si configurerà per la realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="a5a00-120">In this section, you will create a new Unity project and configure it for Windows Mixed Reality.</span></span>

1. <span data-ttu-id="a5a00-121">Creare un progetto Unity e assegnargli un nome appropriato, ad esempio, l' _esercitazione sugli ancoraggi spaziali di Azure_.</span><span class="sxs-lookup"><span data-stu-id="a5a00-121">Create a Unity project and give it a suitable name, for example, _Azure Spatial Anchors tutorial_.</span></span>

2. <span data-ttu-id="a5a00-122">Configurare il progetto Unity per la realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="a5a00-122">Configure the Unity project for Windows Mixed Reality.</span></span>

    >[!TIP]
    ><span data-ttu-id="a5a00-123">Per un promemoria su come creare un progetto Unity e configurarlo per la realtà mista di Windows, è possibile vedere le sezioni [Create New Unity](mrlearning-base-ch1.md#create-new-unity-project) Project e [Configure the Unity for Windows Mixed Reality](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality) dell'esercitazione sull' [inizializzazione del progetto e della prima applicazione](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) , che fa parte della serie di [esercitazioni introduttive](mrlearning-base.md) .</span><span class="sxs-lookup"><span data-stu-id="a5a00-123">For a reminder on how to create a Unity project and configure it for Windows Mixed Reality, you can refer to the [Create new Unity project](mrlearning-base-ch1.md#create-new-unity-project) and the [Configure the Unity project for Windows Mixed Reality](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality) sections of the [Initializing your project and first application](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) tutorial which is part of the the [Getting started tutorials](mrlearning-base.md) series.</span></span>

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="a5a00-124">Aggiunta di pacchetti Unity incorporati</span><span class="sxs-lookup"><span data-stu-id="a5a00-124">Adding inbuilt Unity packages</span></span>

<span data-ttu-id="a5a00-125">In questa sezione verranno aggiunti i pacchetti e gli asset Unity incorporati richiesti dai Toolkit e dagli SDK che verranno usati nel progetto.</span><span class="sxs-lookup"><span data-stu-id="a5a00-125">In this section, you will add inbuilt Unity assets and packages required by the toolkits and SDKs you will be using in the project.</span></span>

1. <span data-ttu-id="a5a00-126">Importare le risorse essenziali TMP.</span><span class="sxs-lookup"><span data-stu-id="a5a00-126">Import TMP Essential Resources.</span></span>

    >[!NOTE]
    ><span data-ttu-id="a5a00-127">Questo pacchetto è stato aggiunto perché è richiesto dal Toolkit per la realtà mista.</span><span class="sxs-lookup"><span data-stu-id="a5a00-127">We are adding this package because it is required by the Mixed Reality Toolkit.</span></span>

    <span data-ttu-id="a5a00-128">Nel menu Unity selezionare **Window** > **TEXTMESHPRO** > **Import tmp Essential Resources**.</span><span class="sxs-lookup"><span data-stu-id="a5a00-128">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources**.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-2-1.1.png)

    <span data-ttu-id="a5a00-130">Nella finestra popup importa pacchetto Unity, verificare innanzitutto che tutti gli asset siano selezionati facendo clic sul pulsante **tutti** , quindi importare gli asset facendo clic sul pulsante **Importa** .</span><span class="sxs-lookup"><span data-stu-id="a5a00-130">In the Import Unity Package pop-up window, first make sure all the assets are selected by clicking the **All** button, then import the assets by clicking the **Import** button.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-2-1.2.png)

2. <span data-ttu-id="a5a00-132">Installare AR Foundation.</span><span class="sxs-lookup"><span data-stu-id="a5a00-132">Install AR Foundation.</span></span>

    >[!NOTE]
    ><span data-ttu-id="a5a00-133">Questo pacchetto è stato aggiunto perché è richiesto da Azure Spatial Anchors SDK.</span><span class="sxs-lookup"><span data-stu-id="a5a00-133">We are adding this package because it is required by the Azure Spatial Anchors SDK.</span></span>

    <span data-ttu-id="a5a00-134">Nel menu Unity selezionare **Window** > **Package Manager**.</span><span class="sxs-lookup"><span data-stu-id="a5a00-134">In the Unity menu, select **Window** > **Package Manager**.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-2-2.1.png)

    <span data-ttu-id="a5a00-136">Nella finestra Gestione pacchetti selezionare **AR Foundation** e installare il pacchetto facendo clic sul pulsante **Installa** .</span><span class="sxs-lookup"><span data-stu-id="a5a00-136">In the Package Manager window, select **AR Foundation** and install the package by clicking the **Install** button.</span></span>

    >[!IMPORTANT]
    ><span data-ttu-id="a5a00-137">Potrebbero essere necessari alcuni secondi prima che il pacchetto AR Foundation venga visualizzato nell'elenco.</span><span class="sxs-lookup"><span data-stu-id="a5a00-137">It might take a few seconds before the AR Foundation package appears in the list.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-2-2.2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="a5a00-139">Importazione delle risorse dell'esercitazione</span><span class="sxs-lookup"><span data-stu-id="a5a00-139">Importing the tutorial assets</span></span>

<span data-ttu-id="a5a00-140">In questa sezione vengono scaricati e importati tutti gli asset dell'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="a5a00-140">In this section, you will download and import all the tutorial assets.</span></span>

1. <span data-ttu-id="a5a00-141">Scaricare gli asset.</span><span class="sxs-lookup"><span data-stu-id="a5a00-141">Download the assets.</span></span>

    * <span data-ttu-id="a5a00-142">[AzureSpatialAnchors. file unitypackage Tools](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.0.0/AzureSpatialAnchors.unitypackage) (versione 2.0.0)</span><span class="sxs-lookup"><span data-stu-id="a5a00-142">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.0.0/AzureSpatialAnchors.unitypackage) (version 2.0.0)</span></span>
    * [<span data-ttu-id="a5a00-143">Microsoft. MixedReality. Toolkit. Unity. Foundation. 2.1.0. file unitypackage Tools</span><span class="sxs-lookup"><span data-stu-id="a5a00-143">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)
    * [<span data-ttu-id="a5a00-144">MRTK. HoloLens2. Unity. Esercitations. assets. GettingStarted. 2.1.0.1. file unitypackage Tools</span><span class="sxs-lookup"><span data-stu-id="a5a00-144">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.1.0.1.unitypackage)
    * [<span data-ttu-id="a5a00-145">MRTK. HoloLens2. Unity. Esercitations. assets. AzureSpatialAnchors. 2.1.0.1. file unitypackage Tools</span><span class="sxs-lookup"><span data-stu-id="a5a00-145">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.1.0.1.unitypackage)

2. <span data-ttu-id="a5a00-146">Importare gli asset.</span><span class="sxs-lookup"><span data-stu-id="a5a00-146">Import the assets.</span></span>

    <span data-ttu-id="a5a00-147">Nel menu Unity selezionare **asset** > **Importa pacchetto** > **pacchetto personalizzato...** .</span><span class="sxs-lookup"><span data-stu-id="a5a00-147">In the Unity menu, select **Assets** > **Import Package** > **Custom Package...**.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-3-2.1.png)

    <span data-ttu-id="a5a00-149">Nel pacchetto di importazione... finestra popup, selezionare **AzureSpatialAnchors. file unitypackage Tools** e fare clic sul pulsante **Apri** .</span><span class="sxs-lookup"><span data-stu-id="a5a00-149">In the Import package... pop-up window, select the **AzureSpatialAnchors.unitypackage** and click the **Open** button.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-3-2.2.png)

    <span data-ttu-id="a5a00-151">Nella finestra popup importa pacchetto Unity, verificare innanzitutto che tutti gli asset siano selezionati facendo clic sul pulsante **tutti** , quindi importare gli asset facendo clic sul pulsante **Importa** .</span><span class="sxs-lookup"><span data-stu-id="a5a00-151">In the Import Unity Package pop-up window, first make sure all the assets are selected by clicking the **All** button, then import the assets by clicking the **Import** button.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-3-2.3.png)

    <span data-ttu-id="a5a00-153">Ripetere questi passaggi per importare i pacchetti di asset rimanenti.</span><span class="sxs-lookup"><span data-stu-id="a5a00-153">Repeat these steps to import the remaining asset packages.</span></span> <span data-ttu-id="a5a00-154">Al termine, la cartella **assets** del progetto Unity deve contenere le sottocartelle.</span><span class="sxs-lookup"><span data-stu-id="a5a00-154">Once complete, your Unity project's **Assets** folder should contain these sub-folders.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-3-2.4.png)

## <a name="creating-and-preparing-the-scene"></a><span data-ttu-id="a5a00-156">Creazione e preparazione della scena</span><span class="sxs-lookup"><span data-stu-id="a5a00-156">Creating and preparing the scene</span></span>

<span data-ttu-id="a5a00-157">In questa sezione verrà creata e preparata la scena aggiungendo il Toolkit di realtà mista e alcune delle prefabbricazioni dell'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="a5a00-157">In this section, you will create and prepare the scene by adding the Mixed Reality Toolkit and some of the tutorial prefabs.</span></span>

1. <span data-ttu-id="a5a00-158">Creare una nuova scena.</span><span class="sxs-lookup"><span data-stu-id="a5a00-158">Create a new scene.</span></span>

    <span data-ttu-id="a5a00-159">Scegliere **File** > **nuova scena**dal menu di Unity.</span><span class="sxs-lookup"><span data-stu-id="a5a00-159">In the Unity menu, select **File** > **New Scene**.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-1.1.png)

    <span data-ttu-id="a5a00-161">Nel menu Unity selezionare **File** > **Salva con nome...** .</span><span class="sxs-lookup"><span data-stu-id="a5a00-161">In the Unity menu, select **File** > **Save As...**.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-1.2.png)

    <span data-ttu-id="a5a00-163">Nella finestra popup Salva scena passare alla cartella **scene** del progetto, assegnare alla scena un nome appropriato, ad esempio _ASATutorialScene_, e salvare la scena facendo clic sul pulsante **Salva** .</span><span class="sxs-lookup"><span data-stu-id="a5a00-163">In the Save Scene pop-up window, navigate to your project's **Scenes** folder, give your scene a suitable name, for example, _ASATutorialScene_, and save the scene by clicking the **Save** button.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-1.3.png)

    >[!TIP]
    ><span data-ttu-id="a5a00-165">È possibile salvare la scena ovunque si trovino, purché si trovino nella cartella assets del progetto.</span><span class="sxs-lookup"><span data-stu-id="a5a00-165">You can save the scene anywhere you like as long as it is inside the project's Assets folder.</span></span> <span data-ttu-id="a5a00-166">Tuttavia, per rendere organizzato il progetto, è in genere consigliabile salvarlo nella cartella scene del progetto.</span><span class="sxs-lookup"><span data-stu-id="a5a00-166">However, to keep your project organized, it's generally recommended to save it in the project's Scenes folder.</span></span>

2. <span data-ttu-id="a5a00-167">Aggiungere il Toolkit per la realtà mista.</span><span class="sxs-lookup"><span data-stu-id="a5a00-167">Add the Mixed Reality Toolkit.</span></span>

    <span data-ttu-id="a5a00-168">Nel menu Unity selezionare **Toolkit realtà mista** > **Aggiungi a scena e configura...** .</span><span class="sxs-lookup"><span data-stu-id="a5a00-168">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...**.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-2.1.png)

    <span data-ttu-id="a5a00-170">Nella finestra popup seleziona MixedRealityToolkitConfigurationProfile fare clic su **DefaultHoloLens2ConfigurationProfile** per impostarlo come profilo di configurazione MRTK della scena.</span><span class="sxs-lookup"><span data-stu-id="a5a00-170">In the Select MixedRealityToolkitConfigurationProfile pop-up window, click the **DefaultHoloLens2ConfigurationProfile** to set it as the scene's MRTK configuration profile.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-2.2.png)

    <span data-ttu-id="a5a00-172">Nel menu Unity selezionare **File** > **Salva** per salvare la scena.</span><span class="sxs-lookup"><span data-stu-id="a5a00-172">In the Unity menu, select **File** > **Save** to save the scene.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-2.3.png)

    >[!TIP]
    ><span data-ttu-id="a5a00-174">È possibile usare il tasto di scelta rapida CTRL + S (Command + S in macOS) per salvare rapidamente la scena mentre si lavora in questa esercitazione.</span><span class="sxs-lookup"><span data-stu-id="a5a00-174">You can use the keyboard shortcut CTRL+S (command + S on macOS) to quickly save your scene as you are working through this tutorial.</span></span>

3. <span data-ttu-id="a5a00-175">Aggiungere i prefabbricati dell'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="a5a00-175">Add the tutorial prefabs.</span></span>

    <span data-ttu-id="a5a00-176">Nel pannello progetto passare a **asset** > **MRTK. Tutorials. AzureSpatialAnchors** > cartella **prefabbricates** .</span><span class="sxs-lookup"><span data-stu-id="a5a00-176">In the Project panel, navigate to **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder.</span></span> <span data-ttu-id="a5a00-177">Tenendo premuto il pulsante CTRL (comando in macOS), fare clic su **ButtonParent**, **DebugWindow**e **ParentAnchor** per selezionare i tre prefabbricati.</span><span class="sxs-lookup"><span data-stu-id="a5a00-177">While holding down the CTRL button (command on macOS), click on **ButtonParent**, **DebugWindow**, and **ParentAnchor** to select the three prefabs.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-3.1.png)

    <span data-ttu-id="a5a00-179">Con i tre prefabbricati ancora selezionati, trascinarli nel pannello gerarchia per aggiungerli alla scena.</span><span class="sxs-lookup"><span data-stu-id="a5a00-179">With the three prefabs still selected, drag them into the Hierarchy panel to add them to the scene.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-3.2.png)

    <span data-ttu-id="a5a00-181">Per concentrarsi sugli oggetti nella scena, è possibile fare doppio clic sull'oggetto ParentAnchor e quindi eseguire di nuovo lo zoom indietro.</span><span class="sxs-lookup"><span data-stu-id="a5a00-181">To focus in on the objects in the scene, you can double-click on the ParentAnchor object, and then zoom slightly out again.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-3.3.png)

    >[!TIP]
    ><span data-ttu-id="a5a00-183">Se si trovano le icone grandi nella scena, ad esempio, le icone con frame ' t'di grandi dimensioni, è possibile nasconderle impostando <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">i gizmo</a> sulla posizione OFF.</span><span class="sxs-lookup"><span data-stu-id="a5a00-183">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="a5a00-184">Configurazione dei pulsanti per il funzionamento della scena</span><span class="sxs-lookup"><span data-stu-id="a5a00-184">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="a5a00-185">In questa sezione si aggiungeranno i prefabbricati e gli script nella scena per creare una serie di pulsanti che dimostrano le nozioni di base relative al comportamento degli ancoraggi locali e degli ancoraggi spaziali di Azure in un'applicazione.</span><span class="sxs-lookup"><span data-stu-id="a5a00-185">In this section, you will add prefabs and scripts into the scene to create a series of buttons that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an application.</span></span>

1. <span data-ttu-id="a5a00-186">Configurare il componente Button (script) di Holo Lens 2 (script).</span><span class="sxs-lookup"><span data-stu-id="a5a00-186">Configure the Pressable Button Holo Lens 2 (script) component.</span></span>

    <span data-ttu-id="a5a00-187">Nel pannello gerarchia espandere l'oggetto **ButtonParent** e selezionare il primo oggetto figlio denominato **StartAzureSession**.</span><span class="sxs-lookup"><span data-stu-id="a5a00-187">In the Hierarchy panel, expand the **ButtonParent** object and select the first child object named **StartAzureSession**.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-5-1.1.png)

    <span data-ttu-id="a5a00-189">Nel pannello Inspector scorrere verso il basso fino al **pulsante stampabile pulsante Holo Lens 2 (script)** e aggiungere un nuovo listener di eventi all'evento **Button premuto ()** facendo clic sull'icona **+** .</span><span class="sxs-lookup"><span data-stu-id="a5a00-189">In the Inspector panel, scroll down to the **Pressable Button Holo Lens 2 (script)** component and add a new event listener to the **Button Pressed ()** event by clicking the **+** icon.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-5-1.2.png)

    <span data-ttu-id="a5a00-191">Con l'oggetto StartAzureSession ancora selezionato nel pannello gerarchia, fare clic e trascinare l'oggetto **ParentAnchor** dal pannello gerarchia nel campo vuoto **None (oggetto)** del listener di eventi appena aggiunto per fare in modo che l'oggetto ParentAnchor attenda gli eventi di pulsante premuto da questo pulsante.</span><span class="sxs-lookup"><span data-stu-id="a5a00-191">With the StartAzureSession object still selected in the Hierarchy panel, click-and-drag the **ParentAnchor** object from the Hierarchy panel into the empty **None (Object)** field of the event listener you just added to make the ParentAnchor object listen for button pressed events from this button.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-5-1.3.png)

    <span data-ttu-id="a5a00-193">Fare clic sull'elenco a discesa **Nessuna funzione** dello stesso listener di eventi, quindi selezionare **AnchorModuleScript** > **StartAzureSession ()** per impostare la funzione StartAzureSession () come azione attivata quando viene attivato il pulsante eventi premuti da questo pulsante.</span><span class="sxs-lookup"><span data-stu-id="a5a00-193">Click the **No Function** dropdown of the same event listener, then select **AnchorModuleScript** > **StartAzureSession ()** to set the StartAzureSession () function as the action that is triggered when the button pressed events is fired from this button.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-5-1.4.png)

2. <span data-ttu-id="a5a00-195">Configurare il componente interactable (script).</span><span class="sxs-lookup"><span data-stu-id="a5a00-195">Configure the Interactable (script) component.</span></span>

    <span data-ttu-id="a5a00-196">Con l'oggetto StartAzureSession ancora selezionato nel pannello gerarchia, nel pannello Inspector scorrere verso il basso fino al componente **interagibile (script)** e ripetere lo stesso processo descritto nel passaggio 1 per l'evento **OnClick ()** .</span><span class="sxs-lookup"><span data-stu-id="a5a00-196">With the StartAzureSession object still selected in the Hierarchy panel, in the Inspector panel, scroll down to the **Interactable (Script)** component and repeat the same process as in step 1 above for the **OnClick ()** event.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-5-2.1.png)

3. <span data-ttu-id="a5a00-198">Configurare i pulsanti rimanenti</span><span class="sxs-lookup"><span data-stu-id="a5a00-198">Configure the remaining buttons</span></span>

    <span data-ttu-id="a5a00-199">Per ognuno dei pulsanti rimanenti, completare il processo descritto nel passaggio 1 e 2 precedente per assegnare funzioni a entrambi gli eventi del pulsante premuto () e OnClick () seguenti:</span><span class="sxs-lookup"><span data-stu-id="a5a00-199">For each of the remaining buttons, complete the process outlined in step 1 and 2 above to assign functions to both the Button Pressed () and OnClick () events following:</span></span>

    * <span data-ttu-id="a5a00-200">Per l'oggetto **StopAzureSession** , assegnare la funzione **StopAzureSession ()** .</span><span class="sxs-lookup"><span data-stu-id="a5a00-200">For the **StopAzureSession** object, assign the **StopAzureSession()** function.</span></span>
    * <span data-ttu-id="a5a00-201">Per l'oggetto **CreateAnchor** , assegnare la funzione **CreateAzureAnchor ()** , quindi trascinare di nuovo il **ParentAnchor** nel campo vuoto **None (oggetto gioco)** .</span><span class="sxs-lookup"><span data-stu-id="a5a00-201">For the **CreateAnchor** object, assign the **CreateAzureAnchor()** function, then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
    * <span data-ttu-id="a5a00-202">Per iniziare a cercare l'oggetto **di ancoraggio** , assegnare la funzione **FindAzureAnchor ()** .</span><span class="sxs-lookup"><span data-stu-id="a5a00-202">For the **Start Looking for Anchor** object, assign the **FindAzureAnchor()** function.</span></span>
    * <span data-ttu-id="a5a00-203">Per l'oggetto **Delete Azure Anchor** assegnare la funzione **DeleteAzureAnchor ()** .</span><span class="sxs-lookup"><span data-stu-id="a5a00-203">For the **Delete Azure Anchor** object, assign the **DeleteAzureAnchor()** function.</span></span>
    * <span data-ttu-id="a5a00-204">Per l'oggetto **Elimina ancoraggio locale** assegnare la funzione **RemoveLocalAnchor ()** , quindi trascinare nuovamente il **ParentAnchor** nel campo vuoto **None (oggetto gioco)** .</span><span class="sxs-lookup"><span data-stu-id="a5a00-204">For the **Delete Local Anchor** object, assign the **RemoveLocalAnchor()** function, then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>

4. <span data-ttu-id="a5a00-205">Connettere la scena alla risorsa di Azure</span><span class="sxs-lookup"><span data-stu-id="a5a00-205">Connect the scene to the Azure resource</span></span>

    <span data-ttu-id="a5a00-206">Nel pannello gerarchia selezionare l'oggetto **ParentAnchor** e nel pannello Inspector scorrere verso il basso fino al componente **Spatial Anchor Manager (script)** .</span><span class="sxs-lookup"><span data-stu-id="a5a00-206">In the Hierarchy panel, select the **ParentAnchor** object and in the Inspector panel, scroll down to the **Spatial Anchor Manager (Script)** component.</span></span>

    <span data-ttu-id="a5a00-207">Quindi, nella sezione **Credentials (credenziali** ) incollare l'ID e la chiave dell'account di ancoraggio spaziale nei campi dell' **ID** dell'account di ancoraggio spaziale e dei campi **chiave dell'account** di ancoraggio spaziale corrispondente.</span><span class="sxs-lookup"><span data-stu-id="a5a00-207">Then, in the **Credentials** section, paste your Spatial Anchors Account ID and Key into the corresponding **Spatial Anchors Account Id** and **Spatial Anchors Account Key** fields.</span></span>

    >[!NOTE]
    ><span data-ttu-id="a5a00-208">Sono stati creati l'ID e la chiave dell'account di ancoraggio spaziali come parte dei [prerequisiti](mrlearning-asa-ch1.md#prerequisites)di questa esercitazione.</span><span class="sxs-lookup"><span data-stu-id="a5a00-208">You created your Spatial Anchors Account Id and Key as part of this tutorial's [Prerequisites](mrlearning-asa-ch1.md#prerequisites).</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-5-4.1.png)

    >[!CAUTION]
    ><span data-ttu-id="a5a00-210">Assicurarsi di salvare la scena.</span><span class="sxs-lookup"><span data-stu-id="a5a00-210">Make sure you save your scene.</span></span>

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="a5a00-211">Provare i comportamenti di base degli ancoraggi spaziali di Azure</span><span class="sxs-lookup"><span data-stu-id="a5a00-211">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="a5a00-212">Ora che la scena è configurata in modo da illustrare gli elementi di base degli ancoraggi spaziali di Azure, è necessario distribuire l'app per poter provare i Anchor spaziali di Azure in prima persona.</span><span class="sxs-lookup"><span data-stu-id="a5a00-212">Now that your scene is configured to demonstrate the basics of Azure Spatial Anchors, it is time to deploy the app so you can experience Azure Spatial Anchors firsthand.</span></span>

1. <span data-ttu-id="a5a00-213">Aggiungere altre funzionalità necessarie.</span><span class="sxs-lookup"><span data-stu-id="a5a00-213">Add additional required capabilities.</span></span>

    <span data-ttu-id="a5a00-214">Nel menu Unity selezionare **modifica** > **Impostazioni progetto...** per aprire il pannello Impostazioni lettore.</span><span class="sxs-lookup"><span data-stu-id="a5a00-214">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings panel.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-6-1.1.png)

    <span data-ttu-id="a5a00-216">Nel pannello Impostazioni lettore selezionare **Player** e quindi impostazioni di **pubblicazione**.</span><span class="sxs-lookup"><span data-stu-id="a5a00-216">In the Player Settings panel, select **Player** and then **Publishing Settings**.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-6-1.2.png)

    <span data-ttu-id="a5a00-218">Nelle **impostazioni di pubblicazione**scorrere verso il basso fino alla sezione **funzionalità** e verificare che **SpatialPerception**, che è stato abilitato al momento della creazione del progetto all'inizio dell'esercitazione, sia abilitato.</span><span class="sxs-lookup"><span data-stu-id="a5a00-218">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that **SpatialPerception**, which you enabled when you created the project at the beginning of the tutorial, is enabled.</span></span> <span data-ttu-id="a5a00-219">Quindi, abilitate le funzionalità **internetClient**, **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage**, **Webcam**e **microfono** .</span><span class="sxs-lookup"><span data-stu-id="a5a00-219">Then, enabled the **InternetClient**, **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage**, **Webcam**, and **Microphone** capabilities.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-6-1.3.png)

2. <span data-ttu-id="a5a00-221">Distribuire l'app in HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="a5a00-221">Deploy the app to your HoloLens 2.</span></span>

    >[!TIP]
    ><span data-ttu-id="a5a00-222">Per un promemoria su come compilare e distribuire il progetto Unity in HoloLens 2, è possibile fare riferimento alle sezioni [compilare l'applicazione nel dispositivo](mrlearning-base-ch1.md#build-your-application-to-your-device) dell'esercitazione [inizializzazione del progetto e della prima applicazione](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) , che fa parte della serie di [esercitazioni introduttive](mrlearning-base.md) .</span><span class="sxs-lookup"><span data-stu-id="a5a00-222">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) sections of the [Initializing your project and first application](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) tutorial which is part of the the [Getting started tutorials](mrlearning-base.md) series.</span></span>

3. <span data-ttu-id="a5a00-223">Eseguire l'app e seguire le istruzioni in-app.</span><span class="sxs-lookup"><span data-stu-id="a5a00-223">Run the app and follow the in-app instructions.</span></span>

    >[!CAUTION]
    ><span data-ttu-id="a5a00-224">Gli ancoraggi spaziali di Azure usano Internet per salvare e caricare i dati di ancoraggio, quindi assicurarsi che il dispositivo sia connesso a Internet.</span><span class="sxs-lookup"><span data-stu-id="a5a00-224">Azure Spatial Anchors uses the internet to save and load the anchor data so make sure your device is connected to the internet.</span></span>

    <span data-ttu-id="a5a00-225">Quando l'applicazione è in esecuzione nel dispositivo, seguire le istruzioni visualizzate nel pannello **istruzioni del modulo di ancoraggio spaziale di Azure** .</span><span class="sxs-lookup"><span data-stu-id="a5a00-225">When the application is running on your device, follow the on-screen instructions displayed on the **Azure Spatial Anchor Module Instructions** panel.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-6-3.1.png)

## <a name="anchoring-an-experience"></a><span data-ttu-id="a5a00-227">Ancoraggio di un'esperienza</span><span class="sxs-lookup"><span data-stu-id="a5a00-227">Anchoring an experience</span></span>

<span data-ttu-id="a5a00-228">Nelle sezioni precedenti sono state apprese le nozioni di base degli ancoraggi spaziali di Azure.</span><span class="sxs-lookup"><span data-stu-id="a5a00-228">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="a5a00-229">È stato usato un cubo per rappresentare e visualizzare l'oggetto del gioco padre con l'ancoraggio collegato.</span><span class="sxs-lookup"><span data-stu-id="a5a00-229">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="a5a00-230">In questa sezione si apprenderà come ancorare un'intera esperienza inserendola come figlio dell'oggetto ParentAnchor.</span><span class="sxs-lookup"><span data-stu-id="a5a00-230">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

1. <span data-ttu-id="a5a00-231">Aggiungere l'esperienza di avvio Rocket.</span><span class="sxs-lookup"><span data-stu-id="a5a00-231">Add the Rocket Launcher experience.</span></span>

    <span data-ttu-id="a5a00-232">Nel pannello progetto passare a **asset** > **MRTK. Tutorials. GettingStarted** > cartella **prefabbricates** e selezionare il **Rocket Launcher_Complete** prefabbricate.</span><span class="sxs-lookup"><span data-stu-id="a5a00-232">In the Project panel, navigate to **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder and select the **Rocket Launcher_Complete** prefab.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-7-1.1.png)

    <span data-ttu-id="a5a00-234">Con il Rocket Launcher_Complete prefabbricato ancora selezionato, trascinarlo sopra l'oggetto **ParentAnchor** nel pannello gerarchia per impostarlo come figlio dell'oggetto ParentAnchor.</span><span class="sxs-lookup"><span data-stu-id="a5a00-234">With the Rocket Launcher_Complete prefab still selected, drag it on top of the **ParentAnchor** object in the Hierarchy panel to make it a child of the ParentAnchor object.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-7-1.2.png)

2. <span data-ttu-id="a5a00-236">Riposizionare l'esperienza di avvio Rocket.</span><span class="sxs-lookup"><span data-stu-id="a5a00-236">Reposition the Rocket Launcher experience.</span></span>

    <span data-ttu-id="a5a00-237">Spostare il modulo **Rocket Launcher_Complete** oggetto in modo che il **ParentAnchor** (cubo) sia ancora esposto.</span><span class="sxs-lookup"><span data-stu-id="a5a00-237">Move module **Rocket Launcher_Complete** object so that the **ParentAnchor** (the cube) is still exposed.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-7-2.1.png)

    <span data-ttu-id="a5a00-239">Nell'applicazione, gli utenti possono ora riposizionare l'intera esperienza di avvio del lanciarazzi spostando il cubo.</span><span class="sxs-lookup"><span data-stu-id="a5a00-239">In the application, users may now reposition the entire Rocket Launcher experience by moving the cube.</span></span>

    >[!TIP]
    ><span data-ttu-id="a5a00-240">Sono disponibili diversi flussi di esperienza utente per il riposizionamento, incluso l'uso di un oggetto di riposizionamento (ad esempio il cubo usato in questa esercitazione), l'uso di un pulsante per alternare un rettangolo di selezione che racchiude l'esperienza, l'uso della posizione e della rotazione Gizmo e altro ancora.</span><span class="sxs-lookup"><span data-stu-id="a5a00-240">There are a variety of user experience flows for repositioning experiences including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounding box that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="a5a00-241">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="a5a00-241">Congratulations</span></span>

<span data-ttu-id="a5a00-242">In questa esercitazione sono state apprese le nozioni di base degli ancoraggi spaziali di Azure.</span><span class="sxs-lookup"><span data-stu-id="a5a00-242">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="a5a00-243">Questa lezione ha fornito diversi pulsanti che consentono di esplorare i diversi passaggi necessari per avviare e arrestare una sessione di Azure e creare, caricare e scaricare gli ancoraggi di Azure in un singolo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a5a00-243">This Lesson provided you with several buttons that let you  explore the various steps required to start and stop an Azure session and create, upload and download azure anchors on a single device.</span></span>

<span data-ttu-id="a5a00-244">Nella lezione successiva si apprenderà come salvare gli ID di ancoraggio di Azure in HoloLens 2 per il recupero, anche dopo il riavvio dell'applicazione e come trasferire gli ID di ancoraggio tra più dispositivi per ottenere l'allineamento spaziale.</span><span class="sxs-lookup"><span data-stu-id="a5a00-244">In the next lesson, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the application is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

[<span data-ttu-id="a5a00-245">Lezione successiva: 2. salvataggio, recupero e condivisione di ancoraggi spaziali di Azure</span><span class="sxs-lookup"><span data-stu-id="a5a00-245">Next Lesson: 2. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mrlearning-asa-ch2.md)

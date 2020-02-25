---
title: Esercitazioni sugli ancoraggi spaziali di Azure-1. Introduzione agli ancoraggi spaziali di Azure
description: Completa questo corso per informazioni su come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 0163b61bfbf8bd583532092581d94f63e1c2a624
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2020
ms.locfileid: "77554680"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="9e335-105">1. Introduzione agli ancoraggi spaziali di Azure</span><span class="sxs-lookup"><span data-stu-id="9e335-105">1. Getting started with Azure Spatial Anchors</span></span>

## <a name="overview"></a><span data-ttu-id="9e335-106">Panoramica</span><span class="sxs-lookup"><span data-stu-id="9e335-106">Overview</span></span>

<span data-ttu-id="9e335-107">Benvenuti alla seconda serie di esercitazioni su HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="9e335-107">Welcome to the second series of the HoloLens 2 tutorials.</span></span> <span data-ttu-id="9e335-108">In questa serie di esercitazioni in tre parti si apprenderanno le nozioni di base degli ancoraggi spaziali di Azure.</span><span class="sxs-lookup"><span data-stu-id="9e335-108">In this three-part tutorial series, you will learn the fundamentals of Azure Spatial Anchors.</span></span>

<span data-ttu-id="9e335-109">Questa prima esercitazione illustra i diversi passaggi necessari per avviare e arrestare una sessione di Azure e creare, caricare e scaricare i punti [di ancoraggio di](mrlearning-asa-ch1.md)Azure in un singolo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9e335-109">In this first tutorial, [Getting started with Azure Spatial Anchors](mrlearning-asa-ch1.md), you will explore the various steps required to start and stop an Azure session and create, upload, and download Azure anchors on a single device.</span></span>

<span data-ttu-id="9e335-110">Nella seconda esercitazione, salvare [, recuperare e condividere gli ancoraggi spaziali di Azure](mrlearning-asa-ch2.md), si apprenderà come salvare gli ancoraggi spaziali di Azure tra più sessioni di App salvando le informazioni di ancoraggio nell'archiviazione di HoloLens 2 e come condividere le informazioni di ancoraggio ad altri dispositivi per un allineamento di ancoraggio a più dispositivi.</span><span class="sxs-lookup"><span data-stu-id="9e335-110">In the second tutorial, [Saving, retrieving, and sharing Azure Spatial Anchors](mrlearning-asa-ch2.md), you will learn how to save Azure Spatial Anchors across multiple app sessions by saving anchor information to the HoloLens 2's storage and how to share this anchor information to other devices for a multi-device anchor alignment.</span></span>

<span data-ttu-id="9e335-111">Nella terza esercitazione, in cui viene [visualizzato il feedback di ancoraggio spaziale di Azure](mrlearning-asa-ch3.md), si apprenderà come fornire agli utenti feedback sugli eventi e gli Stati di ancoraggio quando si usano gli ancoraggi spaziali di Azure.</span><span class="sxs-lookup"><span data-stu-id="9e335-111">In the third tutorial, [Displaying Azure Spatial Anchor feedback](mrlearning-asa-ch3.md), you will learn how to provide users with feedback about anchor events and statuses when using Azure Spatial Anchors.</span></span>

## <a name="objectives"></a><span data-ttu-id="9e335-112">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="9e335-112">Objectives</span></span>

* <span data-ttu-id="9e335-113">Scopri le nozioni di base sullo sviluppo con gli ancoraggi spaziali di Azure per HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="9e335-113">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="9e335-114">Creare, caricare e scaricare ancoraggi spaziali</span><span class="sxs-lookup"><span data-stu-id="9e335-114">Create, upload, and download spatial anchors</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9e335-115">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="9e335-115">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="9e335-116">Se non è ancora stata completata la serie di [esercitazioni introduttive](mrlearning-base.md) , è consigliabile completare prima queste esercitazioni.</span><span class="sxs-lookup"><span data-stu-id="9e335-116">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="9e335-117">Un PC Windows 10 configurato in cui siano [installati gli strumenti](install-the-tools.md) corretti</span><span class="sxs-lookup"><span data-stu-id="9e335-117">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="9e335-118">Windows 10 SDK 10.0.18362.0 o versioni successive</span><span class="sxs-lookup"><span data-stu-id="9e335-118">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="9e335-119">Alcune funzionalità di programmazione C# di base</span><span class="sxs-lookup"><span data-stu-id="9e335-119">Some basic C# programming ability</span></span>
* <span data-ttu-id="9e335-120">Un dispositivo HoloLens 2 [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="9e335-120">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="9e335-121"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.2.X installato e il modulo di supporto delle compilazioni UWP (Universal Windows Platform) aggiunto</span><span class="sxs-lookup"><span data-stu-id="9e335-121"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="9e335-122">Completare la sezione [creare una risorsa ancoraggi spaziali](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) della [Guida introduttiva: creare un'app HoloLens Unity che usa l'esercitazione sugli ancoraggi spaziali di Azure](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) .</span><span class="sxs-lookup"><span data-stu-id="9e335-122">Complete the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9e335-123">La versione di Unity consigliata per questa serie di esercitazioni è Unity 2019.2.X.</span><span class="sxs-lookup"><span data-stu-id="9e335-123">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="9e335-124">Questa istruzione sostituisce gli eventuali requisiti o suggerimenti relativi alla versione di Unity indicati negli argomenti visualizzabili facendo clic sui collegamenti dei prerequisiti sopra riportati.</span><span class="sxs-lookup"><span data-stu-id="9e335-124">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="9e335-125">Creazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="9e335-125">Creating the Unity project</span></span>
<!-- TODO: Consider renaming to 'Creating and preparing the Unity scene and project'-->

<span data-ttu-id="9e335-126">In questa sezione si creerà un nuovo progetto Unity per prepararsi allo sviluppo MRTK.</span><span class="sxs-lookup"><span data-stu-id="9e335-126">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="9e335-127">A questo proposito, seguire prima l' [inizializzazione del progetto e della prima applicazione](mrlearning-base-ch1.md), escluse le istruzioni [per la compilazione dell'applicazione nel dispositivo](mrlearning-base-ch1.md#build-your-application-to-your-device) , che include i passaggi seguenti:</span><span class="sxs-lookup"><span data-stu-id="9e335-127">For this, first follow the [Initializing your project and first application](mrlearning-base-ch1.md), excluding the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="9e335-128">[Creare un nuovo progetto Unity](mrlearning-base-ch1.md#create-new-unity-project) e assegnargli un nome appropriato, ad esempio le *esercitazioni di MRTK*.</span><span class="sxs-lookup"><span data-stu-id="9e335-128">[Create new Unity project](mrlearning-base-ch1.md#create-new-unity-project) and give it a suitable name, for example, *MRTK Tutorials*.</span></span>

2. [<span data-ttu-id="9e335-129">Configurare il progetto Unity per la realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="9e335-129">Configure the Unity project for Windows Mixed Reality</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [<span data-ttu-id="9e335-130">Importare risorse essenziali di TextMesh Pro</span><span class="sxs-lookup"><span data-stu-id="9e335-130">Import TextMesh Pro Essential Resources</span></span>](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [<span data-ttu-id="9e335-131">Importare il Toolkit di realtà mista</span><span class="sxs-lookup"><span data-stu-id="9e335-131">Import the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [<span data-ttu-id="9e335-132">Configurare il progetto Unity per il Toolkit di realtà mista</span><span class="sxs-lookup"><span data-stu-id="9e335-132">Configure the Unity project for the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. <span data-ttu-id="9e335-133">[Aggiungere il Toolkit di realtà mista alla scena Unity](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) e assegnare alla scena un nome appropriato, ad esempio *AzureSpatialAnchors*</span><span class="sxs-lookup"><span data-stu-id="9e335-133">[Add the Mixed Reality Toolkit to the Unity scene](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) and give the scene a suitable name, for example, *AzureSpatialAnchors*</span></span>

<span data-ttu-id="9e335-134">Seguire quindi le istruzioni [come configurare i profili del Toolkit di realtà mista (modificare l'opzione di visualizzazione di riconoscimento spaziale)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) per modificare il profilo di configurazione MRTK per la scena in **DefaultHoloLens2ConfigurationProfile** e modificare le opzioni di visualizzazione per la mesh di riconoscimento spaziale in **occlusione**.</span><span class="sxs-lookup"><span data-stu-id="9e335-134">Then follow the [How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

> [!CAUTION]
> <span data-ttu-id="9e335-135">Come indicato nella pagina [relativa alla configurazione del progetto Unity per le istruzioni del Toolkit di realtà mista](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) collegate in precedenza, è consigliabile non abilitare MSBuild per Unity.</span><span class="sxs-lookup"><span data-stu-id="9e335-135">As mentioned in the [Configure the Unity project for the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) instructions linked above, it is strongly recommended to not enable MSBuild for Unity.</span></span>

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="9e335-136">Aggiunta di pacchetti Unity incorporati</span><span class="sxs-lookup"><span data-stu-id="9e335-136">Adding inbuilt Unity packages</span></span>
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

<span data-ttu-id="9e335-137">In questa sezione verrà installato il pacchetto AR Foundation incorporato di Unity perché è richiesto dall'SDK di Azure Spatial Anchors che verrà importato nella sezione successiva.</span><span class="sxs-lookup"><span data-stu-id="9e335-137">In this section, you will install Unity's inbuilt AR Foundation package because it is required by the Azure Spatial Anchors SDK you will import in the next section.</span></span>

<span data-ttu-id="9e335-138">Nel menu Unity selezionare **Window** > **Package Manager**:</span><span class="sxs-lookup"><span data-stu-id="9e335-138">In the Unity menu, select **Window** > **Package Manager**:</span></span>

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="9e335-140">Potrebbero essere necessari alcuni secondi prima che il pacchetto AR Foundation venga visualizzato nell'elenco.</span><span class="sxs-lookup"><span data-stu-id="9e335-140">It might take a few seconds before the AR Foundation package appears in the list.</span></span>

<span data-ttu-id="9e335-141">Nella finestra Gestione pacchetti selezionare **AR Foundation** e installare il pacchetto facendo clic sul pulsante **Install (installa** ):</span><span class="sxs-lookup"><span data-stu-id="9e335-141">In the Package Manager window, select **AR Foundation** and install the package by clicking the **Install** button:</span></span>

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section2-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="9e335-143">Importazione delle risorse dell'esercitazione</span><span class="sxs-lookup"><span data-stu-id="9e335-143">Importing the tutorial assets</span></span>

<span data-ttu-id="9e335-144">Scaricare e **importare** i pacchetti personalizzati di Unity seguenti **nell'ordine in cui sono elencati**:</span><span class="sxs-lookup"><span data-stu-id="9e335-144">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="9e335-145">[AzureSpatialAnchors. file unitypackage Tools](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (versione 2.1.1)</span><span class="sxs-lookup"><span data-stu-id="9e335-145">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (version 2.1.1)</span></span>
* [<span data-ttu-id="9e335-146">MRTK. HoloLens2. Unity. Esercitations. assets. GettingStarted. 2.3.0.2. file unitypackage Tools</span><span class="sxs-lookup"><span data-stu-id="9e335-146">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)
* [<span data-ttu-id="9e335-147">MRTK. HoloLens2. Unity. Esercitations. assets. AzureSpatialAnchors. 2.3.0.0. file unitypackage Tools</span><span class="sxs-lookup"><span data-stu-id="9e335-147">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage)

> [!TIP]
> <span data-ttu-id="9e335-148">Per un promemoria su come importare un pacchetto personalizzato Unity, è possibile fare riferimento alle istruzioni [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) .</span><span class="sxs-lookup"><span data-stu-id="9e335-148">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="9e335-149">Dopo aver importato le risorse dell'esercitazione, la finestra del progetto avrà un aspetto simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="9e335-149">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section3-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a><span data-ttu-id="9e335-151">Creazione e preparazione della scena</span><span class="sxs-lookup"><span data-stu-id="9e335-151">Creating and preparing the scene</span></span>
<!-- TODO: Consider renaming to 'Preparing the scene' -->

<span data-ttu-id="9e335-152">In questa sezione verrà preparata la scena aggiungendo alcune delle prefabbricate dell'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="9e335-152">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="9e335-153">Nella finestra del progetto passare a **assets** > **MRTK. Tutorials. AzureSpatialAnchors** > cartella **prefabbricates** .</span><span class="sxs-lookup"><span data-stu-id="9e335-153">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder.</span></span> <span data-ttu-id="9e335-154">Tenendo premuto il pulsante CTRL, fare clic su **ButtonParent**, **DebugWindow**, **instructions**e **ParentAnchor** per selezionare i quattro prefabbricati:</span><span class="sxs-lookup"><span data-stu-id="9e335-154">While holding down the CTRL button, click on **ButtonParent**, **DebugWindow**, **Instructions**, and **ParentAnchor** to select the four prefabs:</span></span>

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section4-step1-1.png)

<span data-ttu-id="9e335-156">Con le quattro prefabbricate ancora selezionate, trascinarle nella finestra della gerarchia per aggiungerle alla scena:</span><span class="sxs-lookup"><span data-stu-id="9e335-156">With the four prefabs still selected, drag them into the Hierarchy window to add them to the scene:</span></span>

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section4-step1-2.png)

<span data-ttu-id="9e335-158">Per concentrarsi sugli oggetti nella scena, è possibile fare doppio clic sull'oggetto ParentAnchor e quindi eseguire di nuovo lo zoom indietro:</span><span class="sxs-lookup"><span data-stu-id="9e335-158">To focus in on the objects in the scene, you can double-click on the ParentAnchor object, and then zoom slightly out again:</span></span>

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section4-step1-3.png)

> [!TIP]
> <span data-ttu-id="9e335-160">Se si trovano le icone grandi nella scena, ad esempio, le icone con frame ' t'di grandi dimensioni, è possibile nasconderle impostando <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">i gizmo</a> sulla posizione OFF.</span><span class="sxs-lookup"><span data-stu-id="9e335-160">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="9e335-161">Configurazione dei pulsanti per il funzionamento della scena</span><span class="sxs-lookup"><span data-stu-id="9e335-161">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="9e335-162">In questa sezione si aggiungeranno script alla scena per creare una serie di eventi Button che dimostrano le nozioni di base del comportamento di entrambi gli ancoraggi locali e degli ancoraggi spaziali di Azure in un'applicazione.</span><span class="sxs-lookup"><span data-stu-id="9e335-162">In this section, you will add scripts into the scene to create a series of button events that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an application.</span></span>

### <a name="1-configure-the-pressable-button-holo-lens-2-script-component"></a><span data-ttu-id="9e335-163">1. configurare il componente (script) del pulsante stampabile di Holo Lens 2 (script)</span><span class="sxs-lookup"><span data-stu-id="9e335-163">1. Configure the Pressable Button Holo Lens 2 (Script) component</span></span>

<span data-ttu-id="9e335-164">Nella finestra gerarchia espandere l'oggetto **ButtonParent** e selezionare il primo oggetto figlio denominato **StartAzureSession**:</span><span class="sxs-lookup"><span data-stu-id="9e335-164">In the Hierarchy window, expand the **ButtonParent** object and select the first child object named **StartAzureSession**:</span></span>

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section5-step1-1.png)

<span data-ttu-id="9e335-166">Nella finestra di controllo individuare il componente **Button (script) di Holo Lens 2 (script)** e aggiungere un nuovo listener di eventi all'evento **Pressed () del pulsante** facendo clic sull'icona **+** :</span><span class="sxs-lookup"><span data-stu-id="9e335-166">In the Inspector window, locate the **Pressable Button Holo Lens 2 (Script)** component and add a new event listener to the **Button Pressed ()** event by clicking the **+** icon:</span></span>

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section5-step1-2.png)

<span data-ttu-id="9e335-168">Con l'oggetto StartAzureSession ancora selezionato nella finestra gerarchia, fare clic e trascinare l'oggetto **ParentAnchor** dalla finestra gerarchia nel campo vuoto **None (oggetto)** del listener di eventi appena aggiunto per fare in modo che l'oggetto ParentAnchor attenda gli eventi di pressione del pulsante da questo pulsante:</span><span class="sxs-lookup"><span data-stu-id="9e335-168">With the StartAzureSession object still selected in the Hierarchy window, click-and-drag the **ParentAnchor** object from the Hierarchy window into the empty **None (Object)** field of the event listener you just added to make the ParentAnchor object listen for button pressed events from this button:</span></span>

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section5-step1-3.png)

<span data-ttu-id="9e335-170">Fare clic sull'elenco a discesa **Nessuna funzione** dello stesso listener di eventi, quindi selezionare **AnchorModuleScript** > **StartAzureSession ()** per impostare la funzione StartAzureSession () come azione attivata quando viene attivato il pulsante eventi premuti da questo pulsante:</span><span class="sxs-lookup"><span data-stu-id="9e335-170">Click the **No Function** dropdown of the same event listener, then select **AnchorModuleScript** > **StartAzureSession ()** to set the StartAzureSession () function as the action that is triggered when the button pressed events is fired from this button:</span></span>

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section5-step1-4.png)

### <a name="2-configure-the-interactable-script-component"></a><span data-ttu-id="9e335-172">2. configurare il componente interactable (script)</span><span class="sxs-lookup"><span data-stu-id="9e335-172">2. Configure the Interactable (Script) component</span></span>

<span data-ttu-id="9e335-173">Con l'oggetto StartAzureSession ancora selezionato nella finestra gerarchia, nella finestra di controllo individuare il componente **interactable (script)** e ripetere lo stesso processo descritto nel passaggio 1 per l'evento **OnClick ()** :</span><span class="sxs-lookup"><span data-stu-id="9e335-173">With the StartAzureSession object still selected in the Hierarchy window, in the Inspector window, locate the **Interactable (Script)** component and repeat the same process as in step 1 above for the **OnClick ()** event:</span></span>

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section5-step2-1.png)

### <a name="3-configure-the-remaining-buttons"></a><span data-ttu-id="9e335-175">3. configurare i pulsanti rimanenti</span><span class="sxs-lookup"><span data-stu-id="9e335-175">3. Configure the remaining buttons</span></span>

<span data-ttu-id="9e335-176">Per ognuno dei pulsanti rimanenti, completare il processo descritto nel passaggio 1 e 2 precedente per assegnare funzioni agli eventi di pressione del **pulsante ()** e **OnClick ()** :</span><span class="sxs-lookup"><span data-stu-id="9e335-176">For each of the remaining buttons, complete the process outlined in step 1 and 2 above to assign functions to both the **Button Pressed ()** and **OnClick ()** events:</span></span>

* <span data-ttu-id="9e335-177">Per l'oggetto **StopAzureSession** , assegnare la funzione AnchorModuleScript > **StopAzureSession ()** .</span><span class="sxs-lookup"><span data-stu-id="9e335-177">For the **StopAzureSession** object, assign the AnchorModuleScript > **StopAzureSession ()** function.</span></span>
* <span data-ttu-id="9e335-178">Per l'oggetto **CreateAzureAnchor** , assegnare la funzione AnchorModuleScript > **CreateAzureAnchor ()**</span><span class="sxs-lookup"><span data-stu-id="9e335-178">For the **CreateAzureAnchor** object, assign the AnchorModuleScript > **CreateAzureAnchor ()** function,</span></span>
  * <span data-ttu-id="9e335-179">quindi trascinare nuovamente il **ParentAnchor** nel campo vuoto **None (oggetto gioco)** .</span><span class="sxs-lookup"><span data-stu-id="9e335-179">then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
* <span data-ttu-id="9e335-180">Per l'oggetto **RemoveLocalAnchor** , assegnare la funzione AnchorModuleScript > **RemoveLocalAnchor ()**</span><span class="sxs-lookup"><span data-stu-id="9e335-180">For the **RemoveLocalAnchor** object, assign the AnchorModuleScript > **RemoveLocalAnchor ()** function,</span></span>
  * <span data-ttu-id="9e335-181">quindi trascinare nuovamente il **ParentAnchor** nel campo vuoto **None (oggetto gioco)** .</span><span class="sxs-lookup"><span data-stu-id="9e335-181">then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
* <span data-ttu-id="9e335-182">Per l'oggetto **FindAzureAnchor** , assegnare la funzione AnchorModuleScript > **FindAzureAnchor ()** .</span><span class="sxs-lookup"><span data-stu-id="9e335-182">For the **FindAzureAnchor** object, assign the AnchorModuleScript > **FindAzureAnchor ()** function.</span></span>
* <span data-ttu-id="9e335-183">Per l'oggetto **DeleteAzureAnchor** , assegnare la funzione AnchorModuleScript > **DeleteAzureAnchor ()** .</span><span class="sxs-lookup"><span data-stu-id="9e335-183">For the **DeleteAzureAnchor** object, assign the AnchorModuleScript > **DeleteAzureAnchor ()** function.</span></span>

### <a name="4-connect-the-scene-to-the-azure-resource"></a><span data-ttu-id="9e335-184">4. Connettere la scena alla risorsa di Azure</span><span class="sxs-lookup"><span data-stu-id="9e335-184">4. Connect the scene to the Azure resource</span></span>

<span data-ttu-id="9e335-185">Nella finestra gerarchia selezionare l'oggetto **ParentAnchor** e nella finestra di controllo scorrere verso il basso fino al componente **Spatial Anchor Manager (script)** .</span><span class="sxs-lookup"><span data-stu-id="9e335-185">In the Hierarchy window, select the **ParentAnchor** object and in the Inspector window, scroll down to the **Spatial Anchor Manager (Script)** component.</span></span>

<span data-ttu-id="9e335-186">Quindi, nella sezione **Credentials (credenziali** ) incollare l'ID e la chiave dell'account di ancoraggio spaziali, che è stato creato come parte dei [prerequisiti](mrlearning-asa-ch1.md#prerequisites)di questa esercitazione, nei campi dell'ID dell'account di ancoraggio **spaziale** e nei campi **chiave dell'account** degli ancoraggi spaziali corrispondenti:</span><span class="sxs-lookup"><span data-stu-id="9e335-186">Then, in the **Credentials** section, paste your Spatial Anchors Account ID and Key, which you created as part of this tutorial's [Prerequisites](mrlearning-asa-ch1.md#prerequisites), into the corresponding **Spatial Anchors Account Id** and **Spatial Anchors Account Key** fields:</span></span>

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section5-step4-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="9e335-188">Provare i comportamenti di base degli ancoraggi spaziali di Azure</span><span class="sxs-lookup"><span data-stu-id="9e335-188">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="9e335-189">Ora che la scena è configurata in modo da illustrare gli elementi di base degli ancoraggi spaziali di Azure, è necessario distribuire l'app per poter provare i Anchor spaziali di Azure in prima persona.</span><span class="sxs-lookup"><span data-stu-id="9e335-189">Now that your scene is configured to demonstrate the basics of Azure Spatial Anchors, it is time to deploy the app so you can experience Azure Spatial Anchors firsthand.</span></span>

### <a name="1-add-additional-required-capabilities"></a><span data-ttu-id="9e335-190">1. aggiungere altre funzionalità necessarie</span><span class="sxs-lookup"><span data-stu-id="9e335-190">1. Add additional required capabilities</span></span>

<span data-ttu-id="9e335-191">Nel menu Unity selezionare **modifica** > **Impostazioni progetto...** per aprire la finestra Impostazioni lettore:</span><span class="sxs-lookup"><span data-stu-id="9e335-191">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window:</span></span>

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section6-step1-1.png)

<span data-ttu-id="9e335-193">Nella finestra Impostazioni lettore selezionare **Player** e quindi impostazioni di **pubblicazione**:</span><span class="sxs-lookup"><span data-stu-id="9e335-193">In the Player Settings window, select **Player** and then **Publishing Settings**:</span></span>

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section6-step1-2.png)

<span data-ttu-id="9e335-195">Nelle **impostazioni di pubblicazione**scorrere verso il basso fino alla sezione **funzionalità** e verificare che le funzionalità **internetClient**, **Microphone**e **SpatialPerception** , abilitate al momento della creazione del progetto all'inizio dell'esercitazione, siano abilitate.</span><span class="sxs-lookup"><span data-stu-id="9e335-195">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="9e335-196">Abilitare quindi le funzionalità **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage**e **Webcam** :</span><span class="sxs-lookup"><span data-stu-id="9e335-196">Then, enable the **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage**, and **Webcam** capabilities:</span></span>

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section6-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a><span data-ttu-id="9e335-198">2. distribuire l'app in HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="9e335-198">2. Deploy the app to your HoloLens 2</span></span>

<span data-ttu-id="9e335-199">Gli ancoraggi spaziali di Azure non possono essere eseguiti in Unity, quindi per testare la funzionalità degli ancoraggi spaziali di Azure è necessario distribuire il progetto nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9e335-199">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to deploy the project to your device.</span></span>

> [!TIP]
> <span data-ttu-id="9e335-200">Per un promemoria su come compilare e distribuire il progetto Unity in HoloLens 2, è possibile fare riferimento alle istruzioni per la [compilazione dell'applicazione per il dispositivo](mrlearning-base-ch1.md#build-your-application-to-your-device) .</span><span class="sxs-lookup"><span data-stu-id="9e335-200">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions.</span></span>

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a><span data-ttu-id="9e335-201">3. eseguire l'app in HoloLens 2 e seguire le istruzioni in-app</span><span class="sxs-lookup"><span data-stu-id="9e335-201">3. Run the app on your HoloLens 2 and follow the in-app instructions</span></span>

> [!CAUTION]
> <span data-ttu-id="9e335-202">Gli ancoraggi spaziali di Azure usano Internet per salvare e caricare i dati di ancoraggio, quindi assicurarsi che il dispositivo sia connesso a Internet.</span><span class="sxs-lookup"><span data-stu-id="9e335-202">Azure Spatial Anchors uses the internet to save and load the anchor data so make sure your device is connected to the internet.</span></span>

<span data-ttu-id="9e335-203">Quando l'applicazione è in esecuzione nel dispositivo, seguire le istruzioni sullo schermo visualizzate nel pannello istruzioni dell'esercitazione sull'ancoraggio spaziale di Azure:</span><span class="sxs-lookup"><span data-stu-id="9e335-203">When the application is running on your device, follow the on-screen instructions displayed on the Azure Spatial Anchor Tutorial Instructions panel:</span></span>

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section6-step3-1.png)

## <a name="anchoring-an-experience"></a><span data-ttu-id="9e335-205">Ancoraggio di un'esperienza</span><span class="sxs-lookup"><span data-stu-id="9e335-205">Anchoring an experience</span></span>

<span data-ttu-id="9e335-206">Nelle sezioni precedenti sono state apprese le nozioni di base degli ancoraggi spaziali di Azure.</span><span class="sxs-lookup"><span data-stu-id="9e335-206">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="9e335-207">È stato usato un cubo per rappresentare e visualizzare l'oggetto del gioco padre con l'ancoraggio collegato.</span><span class="sxs-lookup"><span data-stu-id="9e335-207">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="9e335-208">In questa sezione si apprenderà come ancorare un'intera esperienza inserendola come figlio dell'oggetto ParentAnchor.</span><span class="sxs-lookup"><span data-stu-id="9e335-208">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

### <a name="1-add-the-rocket-launcher-experience"></a><span data-ttu-id="9e335-209">1. aggiungere l'esperienza di avvio Rocket</span><span class="sxs-lookup"><span data-stu-id="9e335-209">1. Add the Rocket Launcher experience</span></span>

<span data-ttu-id="9e335-210">Nella finestra del progetto passare al **asset** > **MRTK. Tutorials. GettingStarted** > **prefabbricati** > cartella **RocketLauncher** e selezionare il **RocketLauncher_Complete** prefabbricato:</span><span class="sxs-lookup"><span data-stu-id="9e335-210">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder and select the **RocketLauncher_Complete** prefab:</span></span>

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section7-step1-1.png)

<span data-ttu-id="9e335-212">Con il RocketLauncher_Complete prefabbricato ancora selezionato, trascinarlo sopra l'oggetto **ParentAnchor** nella finestra gerarchia per impostarlo come figlio dell'oggetto ParentAnchor:</span><span class="sxs-lookup"><span data-stu-id="9e335-212">With the RocketLauncher_Complete prefab still selected, drag it on top of the **ParentAnchor** object in the Hierarchy window to make it a child of the ParentAnchor object:</span></span>

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section7-step1-2.png)

### <a name="2-reposition-the-rocket-launcher-experience"></a><span data-ttu-id="9e335-214">2. Riposizionare l'esperienza di avvio Rocket</span><span class="sxs-lookup"><span data-stu-id="9e335-214">2. Reposition the Rocket Launcher experience</span></span>

<span data-ttu-id="9e335-215">Posizionare, ruotare e ridimensionare l'oggetto **RocketLauncher_Complete** a una scala e un orientamento appropriati, assicurando allo stesso tempo che l'oggetto **ParentAnchor** sia ancora esposto, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="9e335-215">Position, rotate, and scale the **RocketLauncher_Complete** object to a suitable scale and orientation, while also ensuring the **ParentAnchor** object is still exposed, for example:</span></span>

* <span data-ttu-id="9e335-216">**Posizione** di trasformazione X = 0, Y = 0, Z = 3,75</span><span class="sxs-lookup"><span data-stu-id="9e335-216">Transform **Position** X = 0, Y = 0, Z = 3.75</span></span>
* <span data-ttu-id="9e335-217">**Rotazione** trasformazione X = 0, Y = 90, Z = 0</span><span class="sxs-lookup"><span data-stu-id="9e335-217">Transform **Rotation** X = 0, Y = 90, Z = 0</span></span>
* <span data-ttu-id="9e335-218">Trasforma **scala** X = 10, Y = 10, Z = 10</span><span class="sxs-lookup"><span data-stu-id="9e335-218">Transform **Scale** X = 10, Y = 10, Z = 10</span></span>

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section7-step2-1.png)

<span data-ttu-id="9e335-220">Nell'applicazione, gli utenti possono ora riposizionare l'intera esperienza di avvio del lanciarazzi spostando il cubo.</span><span class="sxs-lookup"><span data-stu-id="9e335-220">In the application, users may now reposition the entire Rocket Launcher experience by moving the cube.</span></span>

> [!TIP]
> <span data-ttu-id="9e335-221">Sono disponibili diversi flussi di esperienza utente per il riposizionamento, incluso l'uso di un oggetto di riposizionamento (ad esempio il cubo usato in questa esercitazione), l'uso di un pulsante per alternare un rettangolo di selezione che racchiude l'esperienza, l'uso della posizione e della rotazione Gizmo e altro ancora.</span><span class="sxs-lookup"><span data-stu-id="9e335-221">There are a variety of user experience flows for repositioning experiences including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounding box that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="9e335-222">Complimenti</span><span class="sxs-lookup"><span data-stu-id="9e335-222">Congratulations</span></span>

<span data-ttu-id="9e335-223">In questa esercitazione sono state apprese le nozioni di base degli ancoraggi spaziali di Azure.</span><span class="sxs-lookup"><span data-stu-id="9e335-223">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="9e335-224">L'esercitazione ha fornito diversi pulsanti che consentono di esaminare i diversi passaggi necessari per avviare e arrestare una sessione di ancoraggi spaziali di Azure e creare, caricare e scaricare gli ancoraggi spaziali di Azure in un singolo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9e335-224">The tutorial provided you with several buttons that let you explore the various steps required to start and stop an Azure Spatial Anchors session and create, upload and download Azure Spatial Anchors on a single device.</span></span>

<span data-ttu-id="9e335-225">Nella lezione successiva si apprenderà come salvare gli ID di ancoraggio di Azure in HoloLens 2 per il recupero, anche dopo il riavvio dell'applicazione e come trasferire gli ID di ancoraggio tra più dispositivi per ottenere l'allineamento spaziale.</span><span class="sxs-lookup"><span data-stu-id="9e335-225">In the next lesson, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the application is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

[<span data-ttu-id="9e335-226">Lezione successiva: 2. salvataggio, recupero e condivisione di ancoraggi spaziali di Azure</span><span class="sxs-lookup"><span data-stu-id="9e335-226">Next Lesson: 2. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mrlearning-asa-ch2.md)

---
title: Esercitazioni su Ancoraggi nello spazio di Azure - 2. Introduzione ad Ancoraggi nello spazio di Azure
description: Completa questo corso per apprendere come implementare ancoraggi nello spazio di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: a24b6b03ce75a57db49b3d0c875d123ea87c8162
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/14/2020
ms.locfileid: "86305103"
---
# <a name="2-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="9b6bb-105">2. Introduzione ad Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="9b6bb-105">2. Getting started with Azure Spatial Anchors</span></span>

## <a name="overview"></a><span data-ttu-id="9b6bb-106">Panoramica</span><span class="sxs-lookup"><span data-stu-id="9b6bb-106">Overview</span></span>

<span data-ttu-id="9b6bb-107">In questa esercitazione esaminerai i diversi passaggi necessari per avviare e arrestare una sessione di ancoraggi nello spazio di Azure e per creare, caricare e scaricare in un singolo dispositivo gli ancoraggi nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-107">In this tutorial, you will explore the various steps required to start and stop an Azure Spatial Anchors session and to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

## <a name="objectives"></a><span data-ttu-id="9b6bb-108">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="9b6bb-108">Objectives</span></span>

* <span data-ttu-id="9b6bb-109">Scopri le nozioni fondamentali sullo sviluppo con Ancoraggi nello spazio di Azure per HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="9b6bb-109">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="9b6bb-110">Apprendi come creare ancoraggi nello spazio e recuperarli da Azure</span><span class="sxs-lookup"><span data-stu-id="9b6bb-110">Learn how to create spatial anchors and fetch them from Azure</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="9b6bb-111">Creazione e preparazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="9b6bb-111">Creating and preparing the Unity project</span></span>

<span data-ttu-id="9b6bb-112">In questa sezione creerai un nuovo progetto Unity per prepararti allo sviluppo con MRTK.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-112">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="9b6bb-113">A questo scopo, segui prima l'esercitazione [Inizializzazione del progetto e distribuzione della prima applicazione](mr-learning-base-02.md), escluse le istruzioni della sezione [Compilare l'applicazione nel dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2). L'esercitazione include i passaggi seguenti:</span><span class="sxs-lookup"><span data-stu-id="9b6bb-113">For this, first follow the [Initializing your project and deploying your first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="9b6bb-114">[Creazione del progetto Unity](mr-learning-base-02.md#creating-the-unity-project) e assegnazione di un nome appropriato, ad esempio *MRTK Tutorials*</span><span class="sxs-lookup"><span data-stu-id="9b6bb-114">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
1. [<span data-ttu-id="9b6bb-115">Passaggio a un'altra piattaforma di compilazione</span><span class="sxs-lookup"><span data-stu-id="9b6bb-115">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
1. [<span data-ttu-id="9b6bb-116">Importazione delle risorse essenziali TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="9b6bb-116">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
1. [<span data-ttu-id="9b6bb-117">Importazione di Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="9b6bb-117">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
1. [<span data-ttu-id="9b6bb-118">Configurazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="9b6bb-118">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
1. <span data-ttu-id="9b6bb-119">[Creazione e configurazione della scena](mr-learning-base-02.md#creating-and-configuring-the-scene) e assegnazione di un nome appropriato, ad esempio *AzureSpatialAnchors*</span><span class="sxs-lookup"><span data-stu-id="9b6bb-119">[Creating and configuring the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *AzureSpatialAnchors*</span></span>

<span data-ttu-id="9b6bb-120">Segui quindi le istruzioni riportate in [Modifica delle opzioni di visualizzazione di consapevolezza spaziale](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) per:</span><span class="sxs-lookup"><span data-stu-id="9b6bb-120">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to:</span></span>

1. <span data-ttu-id="9b6bb-121">Modificare l'impostazione di **MRTK configuration profile** (Profilo di configurazione di MRTK) configurando **DefaultHoloLens2ConfigurationProfile**</span><span class="sxs-lookup"><span data-stu-id="9b6bb-121">Change the **MRTK configuration profile** for to the **DefaultHoloLens2ConfigurationProfile**</span></span>
1. <span data-ttu-id="9b6bb-122">Modificare le **opzioni di visualizzazione mesh di consapevolezza spaziale** impostando **Occlusion** (Occlusione).</span><span class="sxs-lookup"><span data-stu-id="9b6bb-122">Change the **spatial awareness mesh display options** to **Occlusion**.</span></span>

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="9b6bb-123">Installazione di pacchetti di Unity incorporati</span><span class="sxs-lookup"><span data-stu-id="9b6bb-123">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="9b6bb-124">Scegli **Window (Finestra)**  > **Package Manager (Gestione pacchetti)** dal menu Unity per aprire la finestra Package Manager(Gestione pacchetti), quindi seleziona **AR Foundation** e fai clic sul pulsante **Install** (Installa) per installare il pacchetto:</span><span class="sxs-lookup"><span data-stu-id="9b6bb-124">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** and click the **Install** button to install the package:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="9b6bb-126">Stai installando il pacchetto AR Foundation perché è richiesto da Azure Spatial Anchors SDK, che verrà importato nella sezione successiva.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-126">You are installing the AR Foundation package because the Azure Spatial Anchors SDK requires it, which you will import in the next section.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="9b6bb-127">Importazione degli asset dell'esercitazione</span><span class="sxs-lookup"><span data-stu-id="9b6bb-127">Importing the tutorial assets</span></span>

<span data-ttu-id="9b6bb-128">Scarica e **importa** i pacchetti personalizzati di Unity seguenti, **nell'ordine in cui sono elencati**:</span><span class="sxs-lookup"><span data-stu-id="9b6bb-128">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="9b6bb-129">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage) (versione 2.2.1)</span><span class="sxs-lookup"><span data-stu-id="9b6bb-129">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage) (version 2.2.1)</span></span>
* [<span data-ttu-id="9b6bb-130">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="9b6bb-130">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [<span data-ttu-id="9b6bb-131">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="9b6bb-131">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage)

<span data-ttu-id="9b6bb-132">Dopo l'importazione degli asset dell'esercitazione, la finestra Project (Progetto) avrà un aspetto simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="9b6bb-132">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="9b6bb-134">Per rivedere la procedura di importazione di un pacchetto personalizzato di Unity, puoi fare riferimento alle istruzioni contenute in [Importazione di Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="9b6bb-134">For a reminder on how to import a Unity custom package, you can refer to the [Importing the Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="9b6bb-135">Preparazione della scena</span><span class="sxs-lookup"><span data-stu-id="9b6bb-135">Preparing the scene</span></span>

<span data-ttu-id="9b6bb-136">In questa sezione preparerai la scena aggiungendo alcuni dei prefab dell'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-136">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="9b6bb-137">Nella finestra Project (Progetto) passa ad **Assets (Asset)**  > **MRTK.Tutorials.AzureSpeechServices** > **Prefabs** (Prefab) e quindi fai clic e trascina i prefab seguenti sulla finestra Hierarchy (Gerarchia) per aggiungerli alla scena:</span><span class="sxs-lookup"><span data-stu-id="9b6bb-137">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder, then click-and-drag the following prefabs into the Hierarchy window to add them to your scene:</span></span>

* <span data-ttu-id="9b6bb-138">Prefab **ButtonParent**</span><span class="sxs-lookup"><span data-stu-id="9b6bb-138">**ButtonParent** prefabs</span></span>
* <span data-ttu-id="9b6bb-139">Prefab **DebugWindow**</span><span class="sxs-lookup"><span data-stu-id="9b6bb-139">**DebugWindow** prefabs</span></span>
* <span data-ttu-id="9b6bb-140">Prefab **Instructions**</span><span class="sxs-lookup"><span data-stu-id="9b6bb-140">**Instructions** prefabs</span></span>
* <span data-ttu-id="9b6bb-141">Prefab **ParentAnchor**</span><span class="sxs-lookup"><span data-stu-id="9b6bb-141">**ParentAnchor** prefabs</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="9b6bb-143">Se trovi che le icone grandi nella scena, come quelle a forma di "T", siano motivo di distrazione, puoi nasconderle <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">disattivando il menu Gizmos</a>, come mostrato nell'immagine precedente.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-143">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position, as shown in the image above.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="9b6bb-144">Configurazione dei pulsanti per il funzionamento della scena</span><span class="sxs-lookup"><span data-stu-id="9b6bb-144">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="9b6bb-145">In questa sezione aggiungerai script alla scena per creare una serie di eventi Button che illustrano le nozioni fondamentali sul comportamento degli ancoraggi locali e degli ancoraggi nello spazio di Azure in un'app.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-145">In this section, you will add scripts to the scene to create a series of button events that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an app.</span></span>

<span data-ttu-id="9b6bb-146">Nella finestra Hierarchy (Gerarchia) espandi l'oggetto **ButtonParent** e seleziona il primo oggetto figlio denominato **StartAzureSession**. Nella finestra Inspector (Controllo) configura l'evento **On Click ()** (Al clic) del componente **Button Config Helper (Script)** (Helper configurazione pulsanti - script) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="9b6bb-146">In the Hierarchy window, expand the **ButtonParent** object and select the first child object named **StartAzureSession**, in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="9b6bb-147">Assegna l'oggetto **ParentAnchor** al campo **None (Object)** (Nessuno - Oggetto)</span><span class="sxs-lookup"><span data-stu-id="9b6bb-147">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="9b6bb-148">Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **AnchorModuleScript** > **StartAzureSession ()** per impostare questa funzione come l'azione da eseguire quando viene attivato l'evento</span><span class="sxs-lookup"><span data-stu-id="9b6bb-148">From the **No Function** dropdown, select **AnchorModuleScript** > **StartAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-1.png)

<span data-ttu-id="9b6bb-150">Nella finestra Hierarchy (Gerarchia) seleziona il pulsante successivo denominato **StopAzureSession** e quindi nella finestra Inspector (Controllo) configura l'evento **On Click ()** (Al clic) del componente **Button Config Helper (Script)** (Helper configurazione pulsanti - script) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="9b6bb-150">In the Hierarchy window, select the next button named **StopAzureSession**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="9b6bb-151">Assegna l'oggetto **ParentAnchor** al campo **None (Object)** (Nessuno - Oggetto)</span><span class="sxs-lookup"><span data-stu-id="9b6bb-151">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="9b6bb-152">Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **AnchorModuleScript** > **StopAzureSession ()** per impostare questa funzione come l'azione da eseguire quando viene attivato l'evento</span><span class="sxs-lookup"><span data-stu-id="9b6bb-152">From the **No Function** dropdown, select **AnchorModuleScript** > **StopAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-2.png)

<span data-ttu-id="9b6bb-154">Nella finestra Hierarchy (Gerarchia) seleziona il pulsante successivo denominato **CreateAzureAnchor** e quindi nella finestra Inspector (Controllo) configura l'evento **On Click ()** (Al clic) del componente **Button Config Helper (Script)** (Helper configurazione pulsanti - script) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="9b6bb-154">In the Hierarchy window, select the next button named **CreateAzureAnchor**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="9b6bb-155">Assegna l'oggetto **ParentAnchor** al campo **None (Object)** (Nessuno - Oggetto)</span><span class="sxs-lookup"><span data-stu-id="9b6bb-155">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="9b6bb-156">Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **AnchorModuleScript** > **CreateAzureAnchor ()** per impostare questa funzione come l'azione da eseguire quando viene attivato l'evento</span><span class="sxs-lookup"><span data-stu-id="9b6bb-156">From the **No Function** dropdown, select **AnchorModuleScript** > **CreateAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="9b6bb-157">Assegna l'oggetto **ParentAnchor** al campo **None (Game Object)** (Nessuno - Oggetto gioco) vuoto per impostarlo come argomento della funzione CreateAzureAnchor ()</span><span class="sxs-lookup"><span data-stu-id="9b6bb-157">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the CreateAzureAnchor () function</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-3.png)

<span data-ttu-id="9b6bb-159">Nella finestra Hierarchy (Gerarchia) seleziona il pulsante successivo denominato **RemoveLocalAnchor** e quindi nella finestra Inspector (Controllo) configura l'evento **On Click ()** (Al clic) del componente **Button Config Helper (Script)** (Helper configurazione pulsanti - script) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="9b6bb-159">In the Hierarchy window, select the next button named **RemoveLocalAnchor**,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="9b6bb-160">Assegna l'oggetto **ParentAnchor** al campo **None (Object)** (Nessuno - Oggetto)</span><span class="sxs-lookup"><span data-stu-id="9b6bb-160">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="9b6bb-161">Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **AnchorModuleScript** > **RemoveLocalAnchor ()** per impostare questa funzione come l'azione da eseguire quando viene attivato l'evento</span><span class="sxs-lookup"><span data-stu-id="9b6bb-161">From the **No Function** dropdown, select **AnchorModuleScript** > **RemoveLocalAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="9b6bb-162">Assegna l'oggetto **ParentAnchor** al campo vuoto **None (Game Object)** (Nessuno - Oggetto gioco) per impostarlo come argomento della funzione RemoveLocalAnchor ()</span><span class="sxs-lookup"><span data-stu-id="9b6bb-162">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the RemoveLocalAnchor () function</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-4.png)

<span data-ttu-id="9b6bb-164">Nella finestra Hierarchy (Gerarchia) seleziona il pulsante successivo denominato **FindAzureAnchor** e quindi nella finestra Inspector (Controllo) configura l'evento **On Click ()** (Al clic) del componente **Button Config Helper (Script)** (Helper configurazione pulsanti - script) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="9b6bb-164">In the Hierarchy window, select the next button named **FindAzureAnchor**,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="9b6bb-165">Assegna l'oggetto **ParentAnchor** al campo **None (Object)** (Nessuno - Oggetto)</span><span class="sxs-lookup"><span data-stu-id="9b6bb-165">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="9b6bb-166">Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **AnchorModuleScript** > **FindAzureAnchor ()** per impostare questa funzione come l'azione da eseguire quando viene attivato l'evento</span><span class="sxs-lookup"><span data-stu-id="9b6bb-166">From the **No Function** dropdown, select **AnchorModuleScript** > **FindAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-5.png)

<span data-ttu-id="9b6bb-168">Nella finestra Hierarchy (Gerarchia) seleziona il pulsante successivo denominato **DeleteAzureAnchor** e quindi nella finestra Inspector (Controllo) configura l'evento **On Click ()** (Al clic) del componente **Button Config Helper (Script)** (Helper configurazione pulsanti - script) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="9b6bb-168">In the Hierarchy window, select the next button named **DeleteAzureAnchor**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="9b6bb-169">Assegna l'oggetto **ParentAnchor** al campo **None (Object)** (Nessuno - Oggetto)</span><span class="sxs-lookup"><span data-stu-id="9b6bb-169">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="9b6bb-170">Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **AnchorModuleScript** > **DeleteAzureAnchor ()** per impostare questa funzione come l'azione da eseguire quando viene attivato l'evento</span><span class="sxs-lookup"><span data-stu-id="9b6bb-170">From the **No Function** dropdown, select **AnchorModuleScript** > **DeleteAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-6.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a><span data-ttu-id="9b6bb-172">Connessione della scena alla risorsa di Azure</span><span class="sxs-lookup"><span data-stu-id="9b6bb-172">Connecting the scene to the Azure resource</span></span>

<span data-ttu-id="9b6bb-173">Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **ParentAnchor** e quindi nella finestra Inspector (Controllo) individua il componente **Spatial Anchor Manager (Script)** (Gestione ancoraggi nello spazio - script).</span><span class="sxs-lookup"><span data-stu-id="9b6bb-173">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, locate the **Spatial Anchor Manager (Script)** component.</span></span> <span data-ttu-id="9b6bb-174">Configura la sezione **Credentials** (Credenziali) con le credenziali dell'account di ancoraggi nello spazio di Azure creato in fase di definizione dei [Prerequisiti](mr-learning-asa-01.md#prerequisites) per questa serie di esercitazioni:</span><span class="sxs-lookup"><span data-stu-id="9b6bb-174">Configure the **Credentials** section with the credentials from the Azure Spatial Anchors account created as part of the [Prerequisites](mr-learning-asa-01.md#prerequisites) for this tutorial series:</span></span>

* <span data-ttu-id="9b6bb-175">Nel campo **Spatial Anchors Account ID** (ID account Ancoraggi nello spazio) incolla il valore di **Account ID** (ID account) del tuo account di Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="9b6bb-175">In the **Spatial Anchors Account ID** field, paste the **Account ID** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="9b6bb-176">Nel campo **Spatial Anchors Account Key** (Chiave account Ancoraggi nello spazio) incolla il valore di **Access Key** (Chiave di accesso) primario o secondario del tuo account di Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="9b6bb-176">In the **Spatial Anchors Account Key** field, paste the primary or secondary **Access Key** from your Azure Spatial Anchors account</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section6-step1-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="9b6bb-178">Test dei comportamenti di base di Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="9b6bb-178">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="9b6bb-179">Poiché non è possibile eseguire ancoraggi nello spazio di Azure in Unity, per testare la funzionalità di questo servizio devi compilare il progetto e distribuire l'app nel tuo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-179">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to build the project and deploy the app to your device.</span></span>

> [!TIP]
> <span data-ttu-id="9b6bb-180">Per rivedere la procedura di compilazione e distribuzione di un progetto Unity in HoloLens 2, puoi fare riferimento alle istruzioni riportate in [Compilazione dell'applicazione nel dispositivo HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="9b6bb-180">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your application to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

<span data-ttu-id="9b6bb-181">Quando l'app è in esecuzione nel dispositivo, segui le istruzioni visualizzate nel pannello Azure Spatial Anchor Tutorial Instructions (Istruzioni per l'esercitazione su ancoraggi nello spazio di Azure):</span><span class="sxs-lookup"><span data-stu-id="9b6bb-181">When the app runs on your device, follow the on-screen instructions displayed on the Azure Spatial Anchor Tutorial Instructions panel:</span></span>

1. <span data-ttu-id="9b6bb-182">Sposta il cubo in un'altra posizione</span><span class="sxs-lookup"><span data-stu-id="9b6bb-182">Move the cube to a different location</span></span>
1. <span data-ttu-id="9b6bb-183">Avvia la sessione di Azure</span><span class="sxs-lookup"><span data-stu-id="9b6bb-183">Start Azure Session</span></span>
1. <span data-ttu-id="9b6bb-184">Crea l'ancoraggio di Azure (viene creato un ancoraggio nella posizione del cubo)</span><span class="sxs-lookup"><span data-stu-id="9b6bb-184">Create Azure Anchor (creates an anchor at the location of the cube).</span></span>
1. <span data-ttu-id="9b6bb-185">Arresta la sessione di Azure</span><span class="sxs-lookup"><span data-stu-id="9b6bb-185">Stop Azure Session</span></span>
1. <span data-ttu-id="9b6bb-186">Rimuovi l'ancoraggio locale (consente all'utente di spostare il cubo)</span><span class="sxs-lookup"><span data-stu-id="9b6bb-186">Remove Local Anchor (allows the user to move the cube)</span></span>
1. <span data-ttu-id="9b6bb-187">Sposta il cubo altrove</span><span class="sxs-lookup"><span data-stu-id="9b6bb-187">Move the cube somewhere else</span></span>
1. <span data-ttu-id="9b6bb-188">Avvia la sessione di Azure</span><span class="sxs-lookup"><span data-stu-id="9b6bb-188">Start Azure Session</span></span>
1. <span data-ttu-id="9b6bb-189">Trova l'ancoraggio di Azure (il cubo viene collocato nella posizione del passaggio 3)</span><span class="sxs-lookup"><span data-stu-id="9b6bb-189">Find Azure Anchor (positions the cube at the location from step 3)</span></span>
1. <span data-ttu-id="9b6bb-190">Elimina l'ancoraggio di Azure</span><span class="sxs-lookup"><span data-stu-id="9b6bb-190">Delete Azure Anchor</span></span>
1. <span data-ttu-id="9b6bb-191">Arresta la sessione di Azure</span><span class="sxs-lookup"><span data-stu-id="9b6bb-191">Stop Azure session</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section7-step1-1.png)

> [!CAUTION]
> <span data-ttu-id="9b6bb-193">Poiché per gli ancoraggi nello spazio di Azure viene usato Internet per salvare e caricare i dati di ancoraggio, assicurati che il dispositivo sia connesso a Internet.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-193">Azure Spatial Anchors uses the internet to save and load the anchor data, so make sure your device is connected to the internet.</span></span>

## <a name="anchoring-an-experience"></a><span data-ttu-id="9b6bb-194">Ancoraggio di un'esperienza</span><span class="sxs-lookup"><span data-stu-id="9b6bb-194">Anchoring an experience</span></span>

<span data-ttu-id="9b6bb-195">Nelle sezioni precedenti hai appreso le nozioni fondamentali di Ancoraggi nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-195">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="9b6bb-196">È stato usato un cubo per rappresentare e visualizzare l'oggetto gioco padre con l'ancoraggio collegato.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-196">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="9b6bb-197">In questa sezione apprenderai come ancorare un'intera esperienza inserendola come figlio dell'oggetto ParentAnchor.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-197">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

<span data-ttu-id="9b6bb-198">Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **ParentAnchor** e quindi nella finestra Inspector (Controllo) configura i componenti **Transform** (Trasformazione) come segue:</span><span class="sxs-lookup"><span data-stu-id="9b6bb-198">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, configure the **Transform** components as follows:</span></span>

* <span data-ttu-id="9b6bb-199">Imposta **Scale X** (Scala X) su 1,1</span><span class="sxs-lookup"><span data-stu-id="9b6bb-199">Change **Scale X** to 1.1</span></span>
* <span data-ttu-id="9b6bb-200">Imposta **Scale Z** (Scala Z) su 1,1</span><span class="sxs-lookup"><span data-stu-id="9b6bb-200">Change **Scale Z** to 1.1</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-1.png)

<span data-ttu-id="9b6bb-202">Nella finestra Project (Progetto) passa alla cartella **Assets (Asset)**  > **MRTK.Tutorials.GettingStarted** > **Prefabs (Prefab)**  > **Rover** e quindi fai clic e trascina il prefab **RoverExplorer_Complete** sulla finestra Hierarchy (Gerarchia) per aggiungerlo alla scena:</span><span class="sxs-lookup"><span data-stu-id="9b6bb-202">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **Rover** folder, then click-and-drag the **RoverExplorer_Complete** prefab into the Hierarchy window to add it to the scene:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-2.png)

<span data-ttu-id="9b6bb-204">Con l'oggetto RoverModule_Complete appena aggiunto ancora selezionato nella finestra Hierarchy (Gerarchia), trascinalo sull'oggetto **ParentAnchor** per configurarlo come figlio dell'oggetto ParentAnchor:</span><span class="sxs-lookup"><span data-stu-id="9b6bb-204">With the newly added RoverModule_Complete object still selected in the Hierarchy window, drag it onto the **ParentAnchor** object to make it a child of the ParentAnchor object:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-3.png)

<span data-ttu-id="9b6bb-206">Se ora ricompili il progetto e distribuisci l'app nel dispositivo, puoi riposizionare l'intera esperienza Rover Explorer (Esplora rover) spostando il cubo ridimensionato.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-206">If you now rebuild the project and deploy the app to your device, you can now reposition the entire Rover Explorer experience by moving the resized cube.</span></span>

> [!TIP]
> <span data-ttu-id="9b6bb-207">Sono disponibili diversi flussi di esperienza utente per il riposizionamento, tra cui l'uso di un oggetto di riposizionamento (come il cubo usato in questa esercitazione), l'uso di un pulsante per attivare e disattivare un cubo di delimitazione intorno all'esperienza, l'uso di gizmo di posizione e rotazione e altro ancora.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-207">A variety of user experience flows for repositioning experiences, including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounding box that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="9b6bb-208">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="9b6bb-208">Congratulations</span></span>

<span data-ttu-id="9b6bb-209">In questa esercitazione hai appreso le nozioni fondamentali di Ancoraggi nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-209">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="9b6bb-210">In questa esercitazione hai usato diversi pulsanti per esaminare i vari passaggi da seguire per avviare e arrestare una sessione di ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="9b6bb-210">This tutorial provided you with several buttons to let you explore the various steps required to start and stop an Azure Spatial Anchors session.</span></span> <span data-ttu-id="9b6bb-211">e per creare, caricare e scaricare gli ancoraggi nello spazio di Azure in un singolo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-211">Also, to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

<span data-ttu-id="9b6bb-212">Nell'esercitazione successiva apprenderai come salvare gli ID di ancoraggio di Azure in HoloLens 2 per il recupero, anche dopo il riavvio dell'app, e come trasferire gli ID di ancoraggio tra più dispositivi per ottenere l'allineamento nello spazio.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-212">In the next tutorial, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the app is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

[<span data-ttu-id="9b6bb-213">Esercitazione successiva: 3. Salvataggio, recupero e condivisione di Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="9b6bb-213">Next Tutorial: 3. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mr-learning-asa-03.md)

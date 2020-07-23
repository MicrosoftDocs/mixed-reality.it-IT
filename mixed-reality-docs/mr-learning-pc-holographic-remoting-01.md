---
title: Esercitazioni su Holographic Remoting per PC - 1. Introduzione a Holographic Remoting per PC
description: Completa questo corso per apprendere come usare in remoto l'esperienza di realtà mista da PC a HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 05/19/2020
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: cbbad9548abeb1b8392b99d187b5b051d5b4ddd4
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/14/2020
ms.locfileid: "86305779"
---
# <a name="1-getting-started-with-pc-holographic-remoting"></a><span data-ttu-id="b44bb-105">1. Introduzione a Holographic Remoting per PC</span><span class="sxs-lookup"><span data-stu-id="b44bb-105">1. Getting started with PC Holographic Remoting</span></span>

## <a name="overview"></a><span data-ttu-id="b44bb-106">Panoramica</span><span class="sxs-lookup"><span data-stu-id="b44bb-106">Overview</span></span>

  <span data-ttu-id="b44bb-107">Queste sono le esercitazioni su HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b44bb-107">Welcome to the HoloLens 2 tutorials.</span></span> <span data-ttu-id="b44bb-108">In questa serie di esercitazioni in due parti verrà illustrato come creare una dimostrazione dell'esperienza di realtà mista e come creare un'app per PC per Holographic Remoting.</span><span class="sxs-lookup"><span data-stu-id="b44bb-108">In this two-part tutorial series, you will learn how to create a mixed reality experience demonstration and how to create a PC app for Holographic Remoting.</span></span>

   <span data-ttu-id="b44bb-109">In questa esercitazione, [Creare un'esperienza di realtà mista](mr-learning-pc-holographic-remoting-01.md), apprenderai come creare tale esperienza.</span><span class="sxs-lookup"><span data-stu-id="b44bb-109">In this tutorial, [Create mixed reality experience](mr-learning-pc-holographic-remoting-01.md), you will learn how to create a mixed reality experience.</span></span> <span data-ttu-id="b44bb-110">Verranno infatti illustrati gli elementi dell'interfaccia utente e le funzionalità di manipolazione del modello 3D, ritaglio del modello e tracciamento oculare.</span><span class="sxs-lookup"><span data-stu-id="b44bb-110">It will demonstrate UI elements, 3D model manipulation, model clipping, and eye-tracking features.</span></span>

  <span data-ttu-id="b44bb-111">Nella seconda esercitazione, [Creare un'applicazione per Holographic Remoting](mr-learning-pc-holographic-remoting-02.md), apprenderai come creare un'app per PC per Holographic Remoting.</span><span class="sxs-lookup"><span data-stu-id="b44bb-111">In the second tutorial, [Create a Holographic Remoting application](mr-learning-pc-holographic-remoting-02.md), you will learn how to create a PC app for Holographic Remoting.</span></span> <span data-ttu-id="b44bb-112">Apprenderai inoltre come effettuare la connessione a HoloLens 2 in qualsiasi momento, fornendo un modo per visualizzare il contenuto 3D in realtà mista.</span><span class="sxs-lookup"><span data-stu-id="b44bb-112">And connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span>

## <a name="objectives"></a><span data-ttu-id="b44bb-113">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="b44bb-113">Objectives</span></span>

* <span data-ttu-id="b44bb-114">Importare gli asset e configurare la scena</span><span class="sxs-lookup"><span data-stu-id="b44bb-114">Import assets and set up the scene</span></span>
* <span data-ttu-id="b44bb-115">Interagire con gli ologrammi usando pulsanti ed elementi dell'interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="b44bb-115">Interact with holograms using UI elements and buttons</span></span>
* <span data-ttu-id="b44bb-116">Configurare gli oggetti 3D per la funzionalità di ritaglio</span><span class="sxs-lookup"><span data-stu-id="b44bb-116">Configure 3D objects for the clipping feature</span></span>
* <span data-ttu-id="b44bb-117">Apprendere come attivare le descrizioni comandi con il tracciamento oculare</span><span class="sxs-lookup"><span data-stu-id="b44bb-117">Learn about activating tooltips with eye-tracking</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b44bb-118">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="b44bb-118">Prerequisites</span></span>

* <span data-ttu-id="b44bb-119">Un PC Windows 10 configurato in cui siano [installati gli strumenti](install-the-tools.md) corretti</span><span class="sxs-lookup"><span data-stu-id="b44bb-119">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="b44bb-120">Conoscenza della programmazione C# di base</span><span class="sxs-lookup"><span data-stu-id="b44bb-120">Basic c# programming knowledge</span></span>
* <span data-ttu-id="b44bb-121">Un dispositivo HoloLens 2 [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="b44bb-121">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="b44bb-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.3.X montato e il modulo di supporto delle compilazioni UWP (Universal Windows Platform) aggiunto</span><span class="sxs-lookup"><span data-stu-id="b44bb-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.X mounted, and the Universal Windows Platform Build Support module added</span></span>

>[!ASSOLUTAMENTE CONSIGLIATO]<span data-ttu-id="b44bb-123"> Completamento della serie di esercitazioni introduttive o esperienza di base precedente con Unity e MRTK</span><span class="sxs-lookup"><span data-stu-id="b44bb-123"> Completed the Getting started tutorials series or some basic prior experience with Unity and MRTK</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b44bb-124">La versione di Unity consigliata per questa serie di esercitazioni è Unity 2019.3.X.</span><span class="sxs-lookup"><span data-stu-id="b44bb-124">The recommended Unity version for this tutorial series is Unity 2019.3.X.</span></span> <span data-ttu-id="b44bb-125">Questa istruzione sostituisce gli eventuali requisiti o suggerimenti relativi alla versione di Unity indicati negli argomenti visualizzabili facendo clic sui collegamenti dei prerequisiti sopra riportati.</span><span class="sxs-lookup"><span data-stu-id="b44bb-125">It supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="b44bb-126">Creazione e preparazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="b44bb-126">Creating and preparing the Unity project</span></span>

<span data-ttu-id="b44bb-127">In questa sezione creerai un nuovo progetto Unity per prepararti allo sviluppo con MRTK.</span><span class="sxs-lookup"><span data-stu-id="b44bb-127">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="b44bb-128">A questo scopo, segui prima l'esercitazione [Inizializzazione del progetto e prima applicazione](mr-learning-base-02.md), escluse le istruzioni della sezione [Compilare l'applicazione nel dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), che include i passaggi seguenti:</span><span class="sxs-lookup"><span data-stu-id="b44bb-128">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="b44bb-129">[Creazione del progetto Unity](mr-learning-base-02.md#creating-the-unity-project) e assegnazione di un nome appropriato, ad esempio *MRTK Tutorials*</span><span class="sxs-lookup"><span data-stu-id="b44bb-129">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>

1. [<span data-ttu-id="b44bb-130">Passaggio a un'altra piattaforma di compilazione</span><span class="sxs-lookup"><span data-stu-id="b44bb-130">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)

1. [<span data-ttu-id="b44bb-131">Importazione delle risorse essenziali TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="b44bb-131">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)

1. [<span data-ttu-id="b44bb-132">Importazione di Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="b44bb-132">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)

1. [<span data-ttu-id="b44bb-133">Configurazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="b44bb-133">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)

1. <span data-ttu-id="b44bb-134">[Creazione e impostazione della scena](mr-learning-base-02.md#creating-and-configuring-the-scene) e assegnazione di un nome appropriato, ad esempio **PC Holographic Remoting**</span><span class="sxs-lookup"><span data-stu-id="b44bb-134">[Creating and setting the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, **PC Holographic Remoting**</span></span>

<span data-ttu-id="b44bb-135">Segui quindi le istruzioni riportate in [Modifica delle opzioni di visualizzazione di consapevolezza spaziale](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) per impostare **DefaultHoloLens2ConfigurationProfile** come profilo di configurazione MRTK per la scena.</span><span class="sxs-lookup"><span data-stu-id="b44bb-135">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile**.</span></span> <span data-ttu-id="b44bb-136">Modifica le opzioni di visualizzazione per la mesh di consapevolezza spaziale impostando **Occlusion** (Occlusione).</span><span class="sxs-lookup"><span data-stu-id="b44bb-136">Change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="b44bb-137">Importazione degli asset dell'esercitazione</span><span class="sxs-lookup"><span data-stu-id="b44bb-137">Importing the tutorial assets</span></span>

<span data-ttu-id="b44bb-138">Scarica e **importa** [MRTK.Tutorials.PCHolographicRemoting.unitypackage](https://github.com/onginnovations/MixedRealityLearning/releases/download/pc-holographic-remoting-v2.4.0.0/MRTK.Tutorials.PCHolographicRemoting.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="b44bb-138">Download and **import** the [MRTK.Tutorials.PCHolographicRemoting.unitypackage](https://github.com/onginnovations/MixedRealityLearning/releases/download/pc-holographic-remoting-v2.4.0.0/MRTK.Tutorials.PCHolographicRemoting.unitypackage).</span></span>

>[!TIP]
> <span data-ttu-id="b44bb-139">Per rivedere la procedura di importazione di un pacchetto personalizzato di Unity, puoi fare riferimento alle istruzioni contenute in [Importare Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="b44bb-139">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="b44bb-140">Dopo l'importazione degli asset dell'esercitazione, la finestra Project (Progetto) avrà un aspetto simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="b44bb-140">After importing the tutorial assets, your Project window should look similar to this:</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section2-Step1-1.png)

## <a name="configuring-and-preparing-the-scene"></a><span data-ttu-id="b44bb-142">Configurazione e preparazione della scena</span><span class="sxs-lookup"><span data-stu-id="b44bb-142">Configuring and preparing the scene</span></span>

<span data-ttu-id="b44bb-143">In questa sezione preparerai la scena aggiungendo alcuni dei prefab dell'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="b44bb-143">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="b44bb-144">Nella finestra Project (Progetto) passa alla cartella **Assets** (Asset)  > **MRTK.Tutorials.PCHolograhicRemoting** > **Prefabs** (Prefab).</span><span class="sxs-lookup"><span data-stu-id="b44bb-144">In the Project window, navigate to **Assets** > **MRTK.Tutorials.PCHolograhicRemoting** > **Prefabs** folder.</span></span> <span data-ttu-id="b44bb-145">Tenendo premuto il pulsante CTRL, fai clic sui sei prefab riportati di seguito.</span><span class="sxs-lookup"><span data-stu-id="b44bb-145">While holding down the CTRL button, click on the below six prefabs.</span></span>

* <span data-ttu-id="b44bb-146">ButtonParent</span><span class="sxs-lookup"><span data-stu-id="b44bb-146">ButtonParent</span></span>
* <span data-ttu-id="b44bb-147">ClippingObjects</span><span class="sxs-lookup"><span data-stu-id="b44bb-147">ClippingObjects</span></span>
* <span data-ttu-id="b44bb-148">HandSpatialMapButton</span><span class="sxs-lookup"><span data-stu-id="b44bb-148">HandSpatialMapButton</span></span>
* <span data-ttu-id="b44bb-149">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="b44bb-149">Instructions</span></span>
* <span data-ttu-id="b44bb-150">ModelParent</span><span class="sxs-lookup"><span data-stu-id="b44bb-150">ModelParent</span></span>
* <span data-ttu-id="b44bb-151">Piattaforma</span><span class="sxs-lookup"><span data-stu-id="b44bb-151">Platform</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-1.png)

<span data-ttu-id="b44bb-153">Trascina e rilascia questi modelli dalla cartella dei prefab nella **finestra Hierarchy** (Gerarchia).</span><span class="sxs-lookup"><span data-stu-id="b44bb-153">Drag-and-drop these models from the prefabs folder into the **Hierarchy window**.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-2.png)

<span data-ttu-id="b44bb-155">Per concentrarti sugli oggetti nella scena, puoi fare doppio clic sull'oggetto **ModelParent** e quindi fare di nuovo leggermente zoom avanti:</span><span class="sxs-lookup"><span data-stu-id="b44bb-155">To focus in on the objects in the scene, you can double-click on the **ModelParent** object, and then zoom slightly in again:</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-3.png)

> [!TIP]
> <span data-ttu-id="b44bb-157">Se trovi che le icone grandi nella scena, come quelle a forma di "T", siano motivo di distrazione, puoi nasconderle <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">disattivando i gizmo</a>.</span><span class="sxs-lookup"><span data-stu-id="b44bb-157">If you find the large icons in your scene, such as, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="b44bb-158">Configurazione dei pulsanti per il funzionamento della scena</span><span class="sxs-lookup"><span data-stu-id="b44bb-158">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="b44bb-159">In questa sezione aggiungerai nella scena gli script per creare eventi pulsante a dimostrazione delle nozioni di base sul passaggio a un altro modello e sulla funzionalità di ritaglio.</span><span class="sxs-lookup"><span data-stu-id="b44bb-159">In this section, you will add scripts into the scene to create button events demonstrating the fundamentals of model switching and clipping functionality.</span></span>

### <a name="1-configuring-the-interactable-script-component"></a><span data-ttu-id="b44bb-160">1. Configurazione del componente Interactable (Script) (Con supporto per interazioni - Script)</span><span class="sxs-lookup"><span data-stu-id="b44bb-160">1. Configuring the Interactable (Script) component</span></span>

<span data-ttu-id="b44bb-161">Nella finestra Hierarchy (Gerarchia) espandi l'oggetto **ButtonParent** e seleziona **NextButton**.</span><span class="sxs-lookup"><span data-stu-id="b44bb-161">In the Hierarchy window, expand the **ButtonParent** object and select the **NextButton**.</span></span> <span data-ttu-id="b44bb-162">Nella finestra Inspector (Controllo) individua il componente **Interactable (Script)** (Con supporto per interazioni - Script) e fai clic sull'icona **+** sotto l'evento **OnClick ()** .</span><span class="sxs-lookup"><span data-stu-id="b44bb-162">In the Inspector window, locate the **Interactable (Script)** component and click on **+** icon under **OnClick ()** event.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-1.png)

<span data-ttu-id="b44bb-164">Con l'oggetto **NextButton** ancora selezionato nella finestra Hierarchy (Gerarchia), fai clic e trascina l'oggetto **ButtonParent** dalla finestra Hierarchy (Gerarchia) nel campo **None (Object)** (Nessuno - Oggetto) vuoto dell'evento appena aggiunto per fare in modo che l'oggetto ButtonParent rimanga in ascolto dell'evento di clic del pulsante attivato a partire da questo pulsante:</span><span class="sxs-lookup"><span data-stu-id="b44bb-164">With the **NextButton** object still selected in the Hierarchy window, click-and-drag the **ButtonParent** object from the Hierarchy window into the empty **None (Object)** field of the event you just added to make the ButtonParent object listen for button click event from this button:</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-2.png)

<span data-ttu-id="b44bb-166">Fai clic sull'elenco a discesa **No Function** (Nessuna funzione) dello stesso evento.</span><span class="sxs-lookup"><span data-stu-id="b44bb-166">Click the **No Function** dropdown of the same event.</span></span> <span data-ttu-id="b44bb-167">Seleziona quindi **ViewButtonControl** > **NextModel ()** per impostare la funzione **NextModel ()** come l'azione che viene attivata quando l'evento di pulsante premuto viene attivato a partire da questo pulsante:</span><span class="sxs-lookup"><span data-stu-id="b44bb-167">Then select **ViewButtonControl** > **NextModel ()** to set the **NextModel ()** function as the action that is triggered when the button pressed events is fired from this button:</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-3.png)

### <a name="2-configuring-the-remaining-buttons"></a><span data-ttu-id="b44bb-169">2. Configurazione dei pulsanti rimanenti</span><span class="sxs-lookup"><span data-stu-id="b44bb-169">2. Configuring the remaining buttons</span></span>

<span data-ttu-id="b44bb-170">Per ognuno dei pulsanti rimanenti, completa il processo descritto in precedenza per assegnare funzioni agli eventi **OnClick ()** :</span><span class="sxs-lookup"><span data-stu-id="b44bb-170">For each of the remaining buttons, complete the process outlined above to assign functions to the **OnClick ()** events:</span></span>

* <span data-ttu-id="b44bb-171">Per l'oggetto PreviousButton, assegna la funzione **ViewButtonControl** > **PreviousModel ()** .</span><span class="sxs-lookup"><span data-stu-id="b44bb-171">For PreviousButton object, assign the **ViewButtonContro**l > **PreviousModel ()** function.</span></span>

* <span data-ttu-id="b44bb-172">Per ClippingButton, seleziona la funzione **ToggleButton** > **ToggleClipping ()** .</span><span class="sxs-lookup"><span data-stu-id="b44bb-172">For ClippingButton select **ToggleButton** > **ToggleClipping ()** function.</span></span>

### <a name="3-configuring-the-view-button-control-script--and-toggle-button-script-components"></a><span data-ttu-id="b44bb-173">3. Configurazione dei componenti View Button Control (Script) (Controllo pulsante di visualizzazione - Script) e Toggle Button (Script) (Interruttore - Script)</span><span class="sxs-lookup"><span data-stu-id="b44bb-173">3. Configuring the View Button Control (Script)  and Toggle Button (Script) components</span></span>

<span data-ttu-id="b44bb-174">Ora i pulsanti sono configurati per illustrare il funzionamento del passaggio a un altro modello e la funzionalità di ritaglio.</span><span class="sxs-lookup"><span data-stu-id="b44bb-174">Now your buttons are configured to demonstrate the model switching and clipping functionality.</span></span> <span data-ttu-id="b44bb-175">È il momento di aggiungere modelli 3D e gli oggetti di ritaglio allo script.</span><span class="sxs-lookup"><span data-stu-id="b44bb-175">It is time to add 3D models and the clipping objects to the script.</span></span>

<span data-ttu-id="b44bb-176">Sono stati forniti sei modelli 3D diversi per la dimostrazione. Espandi ***ModelParentobject*** per esporre questi modelli 3D.</span><span class="sxs-lookup"><span data-stu-id="b44bb-176">We have provided six different 3D models for demonstration, expand the ***ModelParentobject*** to expose these 3D models.</span></span>

<span data-ttu-id="b44bb-177">Con l'oggetto ButtonParent ancora selezionato nella finestra Hierarchy (Gerarchia), individua nella finestra Inspector (Controllo) il componente **View Button Control (Script)** (Controllo pulsante di visualizzazione - Script) ed espandi la variabile **Models** (Modelli).</span><span class="sxs-lookup"><span data-stu-id="b44bb-177">With the ButtonParent object still selected in the Hierarchy window, in the Inspector window, locate the **View Button Control (Script)** component and expand the **Models** variable.</span></span>

<span data-ttu-id="b44bb-178">Nel campo **Size** (Dimensione) immetti il numero di modelli 3D che vuoi avere nella scena.</span><span class="sxs-lookup"><span data-stu-id="b44bb-178">In the **Size** field, enter the number of 3D models you would like to have in your scene.</span></span> <span data-ttu-id="b44bb-179">In questo caso, 6.</span><span class="sxs-lookup"><span data-stu-id="b44bb-179">In this case, it would be six.</span></span> <span data-ttu-id="b44bb-180">Verranno creati i campi per l'aggiunta di nuovi modelli 3D.</span><span class="sxs-lookup"><span data-stu-id="b44bb-180">It will create fields for adding new 3D models.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-1.png)

<span data-ttu-id="b44bb-182">Trascina e rilascia ogni oggetto figlio dell'oggetto ModelParent in questi campi.</span><span class="sxs-lookup"><span data-stu-id="b44bb-182">Drag and drop each child object of ModelParent Object into these fields.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-2.png)

<span data-ttu-id="b44bb-184">Trascina e rilascia l'oggetto **ClippingObjects** dalla finestra Hierarchy (Gerarchia) nel campo **Clipping Object** (Oggetto di ritaglio) del componente **Toggle Button (Script)** (Interruttore - Script).</span><span class="sxs-lookup"><span data-stu-id="b44bb-184">Drag and drop the  **ClippingObjects** object from the Hierarchy window to the  **Toggle Button (Script)** component **Clipping Object** field.</span></span>
>[!NOTE]
><span data-ttu-id="b44bb-185">Rimani solo nell'oggetto padre del pulsante.</span><span class="sxs-lookup"><span data-stu-id="b44bb-185">Stay in button parent object only.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-3.png)

<span data-ttu-id="b44bb-187">Nella finestra Hierarchy (Gerarchia) seleziona il prefab **ClippingObjects** e abilitalo nella finestra Inspector (Controllo) per attivare gli oggetti di ritaglio.</span><span class="sxs-lookup"><span data-stu-id="b44bb-187">In the Hierarchy window, select the **ClippingObjects** prefab and enable it in the Inspector window to turn on the Clipping objects.</span></span>

## <a name="configuring-the-clipping-objects-to-enable-clipping-feature"></a><span data-ttu-id="b44bb-188">Configurazione degli oggetti di ritaglio per abilitare la funzionalità di ritaglio</span><span class="sxs-lookup"><span data-stu-id="b44bb-188">Configuring the clipping objects to enable clipping feature</span></span>

<span data-ttu-id="b44bb-189">In questa sezione aggiungerai il renderer degli oggetti figlio dell'oggetto MarsCuriosityRover in un singolo oggetto di ritaglio per illustrare il funzionamento del ritaglio del modello MarsCuriosityRover.</span><span class="sxs-lookup"><span data-stu-id="b44bb-189">In this section, you will add MarsCuriosityRover object's child objects renderer into an individual clipping object to demonstrate the clipping of the MarsCuriosityRover model.</span></span>

<span data-ttu-id="b44bb-190">Nella finestra Hierarchy (Gerarchia) espandi l'oggetto **ClippingObjects** per esporre i tre diversi oggetti di ritaglio che userai in questo progetto.</span><span class="sxs-lookup"><span data-stu-id="b44bb-190">In the Hierarchy window, expand the **ClippingObjects** object to expose the three different clipping objects that you will be using in this project.</span></span>

<span data-ttu-id="b44bb-191">Per configurare l'oggetto **ClippingSphere**, fai clic su di esso e nella finestra Inspector (Controllo) individua il componente **Clipping Sphere (Script)** (Sfera di ritaglio - Script).</span><span class="sxs-lookup"><span data-stu-id="b44bb-191">To configure the **ClippingSphere** object, click on it, and in the Inspector window, locate the **Clipping Sphere (Script)** component.</span></span> <span data-ttu-id="b44bb-192">Nel campo della dimensione immetti il numero di renderer che è necessario aggiungere per il modello 3D.</span><span class="sxs-lookup"><span data-stu-id="b44bb-192">Enter the number of renderers in the size field that you need to add for your 3D model.</span></span> <span data-ttu-id="b44bb-193">In questo caso, aggiungi 10 per gli oggetti figlio di MarsCuriosityRover.</span><span class="sxs-lookup"><span data-stu-id="b44bb-193">In this case, add 10 for MarsCuriosityRover child objects.</span></span> <span data-ttu-id="b44bb-194">Verranno creati i campi per l'aggiunta dei renderer. Trascina e rilascia gli oggetti modello figlio dell'oggetto MarsCuriosityRover in questi campi.</span><span class="sxs-lookup"><span data-stu-id="b44bb-194">It will create fields for adding renderers, drag and drop MarsCuriosityRover Object's child model objects into these fields.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section5-Step1-1.png)

<span data-ttu-id="b44bb-196">Segui lo stesso processo e aggiungi i renderer degli oggetti figlio di MarsCuriosityRover agli oggetti **ClippingBox** e **ClippingPlane**.</span><span class="sxs-lookup"><span data-stu-id="b44bb-196">Follow the same process and add MarsCuriosityRover's child objects renderers to the **ClippingBox** and **ClippingPlane** objects.</span></span>

<span data-ttu-id="b44bb-197">In questa esercitazione verrà usato solo il modello MarsCuriosityRover per illustrare la funzionalità di ritaglio.</span><span class="sxs-lookup"><span data-stu-id="b44bb-197">In this tutorial, only the MarsCuriosityRover model will be used for demonstrating the clipping feature.</span></span> <span data-ttu-id="b44bb-198">Sono state comunque aggiunte funzionalità di ritaglio anche ad altri modelli, aumentando la dimensione del renderer, e sono stati aggiunti i singoli renderer mesh corrispondenti.</span><span class="sxs-lookup"><span data-stu-id="b44bb-198">They were adding clipping features to more models, increasing the size of the renderer, and adding their individual mesh renderers.</span></span>

## <a name="configuring-eye-tracking-to-highlight-tooltips"></a><span data-ttu-id="b44bb-199">Configurazione del tracciamento oculare per evidenziare le descrizioni comandi</span><span class="sxs-lookup"><span data-stu-id="b44bb-199">Configuring eye-tracking to highlight tooltips</span></span>

<span data-ttu-id="b44bb-200">In questa sezione esaminerai come abilitare il tracciamento oculare nel tuo progetto.</span><span class="sxs-lookup"><span data-stu-id="b44bb-200">In this section, you will explore how to enable eye tracking in your project.</span></span> <span data-ttu-id="b44bb-201">Ad esempio, implementerai la funzionalità per evidenziare le descrizioni comandi associate alle parti di MarsCuriosityRover quando le guardi e per nasconderle quando distogli lo sguardo da esse.</span><span class="sxs-lookup"><span data-stu-id="b44bb-201">For example, you will implement the functionality to highlight tooltips attached to MarsCuriosityRover's parts while looking at them and hiding them, while you are looking away from them.</span></span>

### <a name="1-identify-target-objects-and-associated-tooltips"></a><span data-ttu-id="b44bb-202">1. Identificare gli oggetti di destinazione e le descrizioni comandi associate.</span><span class="sxs-lookup"><span data-stu-id="b44bb-202">1. Identify target objects and associated tooltips.</span></span>

<span data-ttu-id="b44bb-203">Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto ModelParent.</span><span class="sxs-lookup"><span data-stu-id="b44bb-203">In the Hierarchy window, select the ModelParent object.</span></span> <span data-ttu-id="b44bb-204">Espandi ***MarsCuriosity -> Rover*** per trovare cinque parti principali di MarsCuriosityRover: **POI-Camera**, **POI-Wheels**, **POI-Antena**, **POI-Spectrometer** e **POI-RUHF Antenna**.</span><span class="sxs-lookup"><span data-stu-id="b44bb-204">Expand the ***MarsCuriosity -> Rover*** to find five main parts of the MarsCuriosityRover: **POI-Camera**, **POI-Wheels**, **POI-Antena**, **POI-Spectrometer**, **POI-RUHF Antenna**.</span></span>

* <span data-ttu-id="b44bb-205">Osserva cinque oggetti descrizione comando corrispondenti associati a parti di MarsCuriosityRover nella finestra Hierarchy (Gerarchia).</span><span class="sxs-lookup"><span data-stu-id="b44bb-205">Observe five corresponding tooltip objects associated with MarsCuriosityRover parts in the Hierarchy window.</span></span> 
* <span data-ttu-id="b44bb-206">Configurerai questi oggetti per evidenziare l'esperienza quando guardi le parti di MarsCuriosityRover.</span><span class="sxs-lookup"><span data-stu-id="b44bb-206">You will be configuring these objects to highlight the experience when you look at the MarsCuriosityRover parts.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step1-1.png)

### <a name="2-implement-while-looking-at-target-----on-look-away--events"></a><span data-ttu-id="b44bb-208">2. Implementare gli eventi Looking At Target () (Mentre viene guardata la destinazione) e On Look Away () (Quando viene distolto lo sguardo)</span><span class="sxs-lookup"><span data-stu-id="b44bb-208">2. Implement While Looking At Target ()  &  On Look Away () events</span></span>

<span data-ttu-id="b44bb-209">Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto ***POI-Camera***.</span><span class="sxs-lookup"><span data-stu-id="b44bb-209">In the Hierarchy window, select the ***POI-Camera*** object.</span></span> <span data-ttu-id="b44bb-210">Nella finestra Inspector (Controllo) individua il componente **Eye Tracking Target (Script)** (Destinazione tracciamento oculare - Script) e configura gli eventi **While Looking At Target ()** (Mentre viene guardata la destinazione) & **On Look Away ()** (Quando viene distolto lo sguardo) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="b44bb-210">In the Inspector window, locate the **Eye Tracking Target (Script)** component and configure the **While Looking At Target ()** & **On Look Away ()** events as follows:</span></span>

* <span data-ttu-id="b44bb-211">Al campo **None (Object)** (Nessuno - Oggetto) assegna l'oggetto **POI-Camera ToolTip**</span><span class="sxs-lookup"><span data-stu-id="b44bb-211">To **None (Object)** field, assign the **POI-Camera ToolTip** object</span></span>
* <span data-ttu-id="b44bb-212">Dall'elenco a discesa **No Function** (Nessuna funzione) dell'evento **While Looking At Target ()** (Mentre viene guardata la destinazione) seleziona **GameObject** > **SetActive (bool).**</span><span class="sxs-lookup"><span data-stu-id="b44bb-212">From **No Function** dropdown of **While Looking At Target ()** event, select **GameObject** > **SetActive (bool).**</span></span> <span data-ttu-id="b44bb-213">Seleziona la **casella di controllo** sottostante per evidenziare la descrizione comando come l'azione che viene attivata quando guardi l'oggetto di destinazione.</span><span class="sxs-lookup"><span data-stu-id="b44bb-213">Select the **Checkbox** under it to highlight the tooltip as the action that is triggered when you look at the target object.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-1.png)

* <span data-ttu-id="b44bb-215">Segui lo stesso processo e fai clic sull'elenco a discesa **No Function** (Nessuna funzione) del listener di eventi **On Look Away ()** (Quando viene distolto lo sguardo).</span><span class="sxs-lookup"><span data-stu-id="b44bb-215">Follow the same process and click on the **No Function** dropdown of the **On Look Away ()** event listener.</span></span> <span data-ttu-id="b44bb-216">Seleziona quindi **GameObject** > **SetActive (bool**) e lascia vuota la **casella di controllo** per nascondere la descrizione comando come l'azione che viene attivata quando distogli lo sguardo dall'oggetto di destinazione.</span><span class="sxs-lookup"><span data-stu-id="b44bb-216">Then select **GameObject** > **SetActive (bool**) and leave the **Checkbox** empty to hide the tooltip as the action that is triggered when you look away from the target object.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-2.png)

<span data-ttu-id="b44bb-218">Segui lo stesso processo e assegna i rispettivi oggetti descrizione comando agli eventi **While Looking At Target ()** (Mentre viene guardata la destinazione) & **On Look Away ()** (Quando viene distolto lo sguardo) delle parti corrispondenti di **MarsCuriosityRover**.</span><span class="sxs-lookup"><span data-stu-id="b44bb-218">Follow the same process and assign respective tooltip objects to their same **MarsCuriosityRover** parts **While Looking At Target ()** & **On Look Away ()** events.</span></span>

<span data-ttu-id="b44bb-219">Per abilitare il tracciamento oculare, segui queste [linee guida](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch5#5-enable-simulated-eye-tracking-for-in-editor-simulations).</span><span class="sxs-lookup"><span data-stu-id="b44bb-219">To enable eye tracking, please follow these [guidelines](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch5#5-enable-simulated-eye-tracking-for-in-editor-simulations).</span></span>

## <a name="congratulations"></a><span data-ttu-id="b44bb-220">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="b44bb-220">Congratulations</span></span>

<span data-ttu-id="b44bb-221">In questa esercitazione hai appreso come creare un'esperienza di realtà mista con la dimostrazione del funzionamento degli elementi dell'interfaccia utente e delle funzionalità di manipolazione del modello 3D, di ritaglio del modello e di tracciamento oculare.</span><span class="sxs-lookup"><span data-stu-id="b44bb-221">In this tutorial, you learned to build a mixed reality experience demonstrating UI elements, 3D model manipulation, model clipping, and eye-tracking features.</span></span> <span data-ttu-id="b44bb-222">Nell'esercitazione sono stati forniti NextButton e PreviousButton che ti consentono di esplorare l'esperienza di visualizzazione del modello 3D.</span><span class="sxs-lookup"><span data-stu-id="b44bb-222">The tutorial provided you with NextButton and PreviousButton that let you explore the 3D model viewer experience.</span></span> <span data-ttu-id="b44bb-223">Con ClippingObjectButton hai attivato gli oggetti di ritaglio e visto come opera la funzionalità di ritaglio.</span><span class="sxs-lookup"><span data-stu-id="b44bb-223">The ClippingObjectButton made you turn on clipping objects and experience clipping feature.</span></span> <span data-ttu-id="b44bb-224">Nell'esercitazione è stato inoltre fornito un elemento di tracciamento oculare che consente di evidenziare le descrizioni comandi nell'esperienza.</span><span class="sxs-lookup"><span data-stu-id="b44bb-224">The tutorial also provided you with an eye-tracking element to enable highlighting the tooltips in the experience.</span></span>

<span data-ttu-id="b44bb-225">Nella lezione successiva apprenderai come creare un'applicazione per Holographic Remoting per PC per connettere HoloLens 2 in qualsiasi momento, offrendo un modo per visualizzare il contenuto 3D in realtà mista.</span><span class="sxs-lookup"><span data-stu-id="b44bb-225">In the next lesson, you will learn how to create a Holographic Remoting application for PC to connect HoloLens 2 at any point, providing a way to Visualize 3D content in mixed reality.</span></span>

[<span data-ttu-id="b44bb-226">Lezione successiva: 2. Creare un'applicazione per Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="b44bb-226">Next Lesson: 2. Create Holographic Remoting application</span></span>](mr-learning-pc-holographic-remoting-02.md)

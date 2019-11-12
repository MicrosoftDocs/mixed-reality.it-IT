---
title: Input MR 213
description: Seguire questa esercitazione di codifica usando Unity, Visual Studio e auricolari immersivi per apprendere i dettagli dei controller di movimento.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, immersive, Motion controller, Academy, esercitazione
ms.openlocfilehash: 273d1bf384d588ab24bfe29e30f299b7a41fe541
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926815"
---
>[!NOTE]
><span data-ttu-id="47f53-104">Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.</span><span class="sxs-lookup"><span data-stu-id="47f53-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="47f53-105">Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.</span><span class="sxs-lookup"><span data-stu-id="47f53-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="47f53-106">Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="47f53-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="47f53-107">Verranno mantenuti per continuare a usare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="47f53-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="47f53-108">Per HoloLens 2 è stata pubblicata [una nuova serie di esercitazioni](mrlearning-base.md) .</span><span class="sxs-lookup"><span data-stu-id="47f53-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

# <a name="mr-input-213-motion-controllers"></a><span data-ttu-id="47f53-109">Input MR 213: controller di movimento</span><span class="sxs-lookup"><span data-stu-id="47f53-109">MR Input 213: Motion controllers</span></span>

<span data-ttu-id="47f53-110">I controller di movimento nel mondo della realtà mista aggiungono un altro livello di interattività.</span><span class="sxs-lookup"><span data-stu-id="47f53-110">Motion controllers in the mixed reality world add another level of interactivity.</span></span> <span data-ttu-id="47f53-111">Con i [controller di movimento](motion-controllers.md)è possibile interagire direttamente con gli oggetti in modo più naturale, in modo analogo alle interazioni fisiche nella vita reale, aumentando l'immersione e la soddisfazione nell'esperienza dell'app.</span><span class="sxs-lookup"><span data-stu-id="47f53-111">With [motion controllers](motion-controllers.md), we can directly interact with objects in a more natural way, similar to our physical interactions in real life, increasing immersion and delight in your app experience.</span></span>

<span data-ttu-id="47f53-112">In MR input 213 gli eventi di input del controller di movimento vengono esaminati creando una semplice esperienza di disegno spaziale.</span><span class="sxs-lookup"><span data-stu-id="47f53-112">In MR Input 213, we will explore the motion controller's input events by creating a simple spatial painting experience.</span></span> <span data-ttu-id="47f53-113">Con questa app, gli utenti possono disegnare nello spazio tridimensionale con diversi tipi di pennelli e colori.</span><span class="sxs-lookup"><span data-stu-id="47f53-113">With this app, users can paint in three-dimensional space with various types of brushes and colors.</span></span>

## <a name="topics-covered-in-this-tutorial"></a><span data-ttu-id="47f53-114">Argomenti trattati in questa esercitazione</span><span class="sxs-lookup"><span data-stu-id="47f53-114">Topics covered in this tutorial</span></span>

|![Topic1 MixedReality213](images/mr213-topic1.png)|![MixedReality213 Topic2](images/mr213-topic2.png)|![MixedReality213 Topic3](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|<span data-ttu-id="47f53-118">**Visualizzazione del controller**</span><span class="sxs-lookup"><span data-stu-id="47f53-118">**Controller visualization**</span></span>|<span data-ttu-id="47f53-119">**Eventi di input del controller**</span><span class="sxs-lookup"><span data-stu-id="47f53-119">**Controller input events**</span></span>|<span data-ttu-id="47f53-120">**Controller e interfaccia utente personalizzati**</span><span class="sxs-lookup"><span data-stu-id="47f53-120">**Custom controller and UI**</span></span>|
|<span data-ttu-id="47f53-121">Informazioni su come eseguire il rendering dei modelli di controller di movimento in modalità di gioco e runtime di Unity.</span><span class="sxs-lookup"><span data-stu-id="47f53-121">Learn how to render motion controller models in Unity's game mode and runtime.</span></span>|<span data-ttu-id="47f53-122">Informazioni sui diversi tipi di eventi dei pulsanti e sulle relative applicazioni.</span><span class="sxs-lookup"><span data-stu-id="47f53-122">Understand different types of button events and their applications.</span></span>|<span data-ttu-id="47f53-123">Informazioni su come sovrapporre gli elementi dell'interfaccia utente all'inizio del controller o personalizzarlo completamente.</span><span class="sxs-lookup"><span data-stu-id="47f53-123">Learn how to overlay UI elements on top of the controller or fully customize it.</span></span>|

## <a name="device-support"></a><span data-ttu-id="47f53-124">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="47f53-124">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="47f53-125">Corso</span><span class="sxs-lookup"><span data-stu-id="47f53-125">Course</span></span></th><th style="width:150px"> <span data-ttu-id="47f53-126"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="47f53-126"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="47f53-127"><a href="immersive-headset-hardware-details.md">Visori VR immersive</a></span><span class="sxs-lookup"><span data-stu-id="47f53-127"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="47f53-128">Input MR 213: controller di movimento</span><span class="sxs-lookup"><span data-stu-id="47f53-128">MR Input 213: Motion controllers</span></span></td><td style="text-align: center;"> </td><td style="text-align: center;"> <span data-ttu-id="47f53-129">✔️</span><span class="sxs-lookup"><span data-stu-id="47f53-129">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="47f53-130">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="47f53-130">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="47f53-131">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="47f53-131">Prerequisites</span></span>

<span data-ttu-id="47f53-132">Vedere l'elenco di controllo per l'installazione di auricolari immersivi in [Questa pagina](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="47f53-132">See the installation checklist for immersive headsets on [this page](install-the-tools.md).</span></span>

* <span data-ttu-id="47f53-133">Questa esercitazione richiede [Unity 2017.2.1 P2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)</span><span class="sxs-lookup"><span data-stu-id="47f53-133">This tutorial requires [Unity 2017.2.1p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)</span></span>

### <a name="project-files"></a><span data-ttu-id="47f53-134">File di progetto</span><span class="sxs-lookup"><span data-stu-id="47f53-134">Project files</span></span>

* <span data-ttu-id="47f53-135">[Scaricare i file](https://github.com/Microsoft/MixedReality213/archive/master.zip) richiesti dal progetto ed estrarre i file sul desktop.</span><span class="sxs-lookup"><span data-stu-id="47f53-135">[Download the files](https://github.com/Microsoft/MixedReality213/archive/master.zip) required by the project and extract the files to the Desktop.</span></span>

>[!NOTE]
><span data-ttu-id="47f53-136">Se si vuole esaminare il codice sorgente prima del download, è [disponibile in GitHub](https://github.com/Microsoft/MixedReality213).</span><span class="sxs-lookup"><span data-stu-id="47f53-136">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/MixedReality213).</span></span>

## <a name="unity-setup"></a><span data-ttu-id="47f53-137">Configurazione di Unity</span><span class="sxs-lookup"><span data-stu-id="47f53-137">Unity setup</span></span>

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a><span data-ttu-id="47f53-138">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="47f53-138">Objectives</span></span>

* <span data-ttu-id="47f53-139">Ottimizzare Unity per lo sviluppo di realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="47f53-139">Optimize Unity for Windows Mixed Reality development</span></span>
* <span data-ttu-id="47f53-140">Configurare la fotocamera della realtà mista</span><span class="sxs-lookup"><span data-stu-id="47f53-140">Setup Mixed Reality Camera</span></span>
* <span data-ttu-id="47f53-141">Ambiente di installazione</span><span class="sxs-lookup"><span data-stu-id="47f53-141">Setup environment</span></span>

### <a name="instructions"></a><span data-ttu-id="47f53-142">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="47f53-142">Instructions</span></span>

* <span data-ttu-id="47f53-143">Avvia Unity.</span><span class="sxs-lookup"><span data-stu-id="47f53-143">Start Unity.</span></span>
* <span data-ttu-id="47f53-144">Selezionare **Apri**.</span><span class="sxs-lookup"><span data-stu-id="47f53-144">Select **Open**.</span></span>
* <span data-ttu-id="47f53-145">Passare al desktop e trovare la cartella **MixedReality213-Master** precedentemente non archiviata.</span><span class="sxs-lookup"><span data-stu-id="47f53-145">Navigate to your Desktop and find the **MixedReality213-master** folder you previously unarchived.</span></span>
* <span data-ttu-id="47f53-146">Fare clic su **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="47f53-146">Click **Select Folder**.</span></span>
* <span data-ttu-id="47f53-147">Al termine del caricamento dei file di progetto Unity, sarà possibile visualizzare l'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="47f53-147">Once Unity finishes loading project files, you will be able to see Unity editor.</span></span>
* <span data-ttu-id="47f53-148">In Unity selezionare **File > impostazioni di compilazione**.</span><span class="sxs-lookup"><span data-stu-id="47f53-148">In Unity, select **File > Build Settings**.</span></span>

    ![MR213_BuildSettings](images/mr213-buildsettings-450px.png)

* <span data-ttu-id="47f53-150">Selezionare **piattaforma UWP (Universal Windows Platform)** nell'elenco **piattaforma** e fare clic sul pulsante **Switch Platform** .</span><span class="sxs-lookup"><span data-stu-id="47f53-150">Select **Universal Windows Platform** in the **Platform** list and click the **Switch Platform** button.</span></span>
* <span data-ttu-id="47f53-151">Impostare il dispositivo di destinazione su **qualsiasi dispositivo**</span><span class="sxs-lookup"><span data-stu-id="47f53-151">Set Target Device to **Any device**</span></span>
* <span data-ttu-id="47f53-152">Imposta tipo di compilazione su **D3D**</span><span class="sxs-lookup"><span data-stu-id="47f53-152">Set Build Type to **D3D**</span></span>
* <span data-ttu-id="47f53-153">Impostare SDK sull' **ultima versione installata**</span><span class="sxs-lookup"><span data-stu-id="47f53-153">Set SDK to **Latest Installed**</span></span>
* <span data-ttu-id="47f53-154">Verifica **progetti C# Unity**</span><span class="sxs-lookup"><span data-stu-id="47f53-154">Check **Unity C# Projects**</span></span>
    * <span data-ttu-id="47f53-155">In questo modo è possibile modificare i file di script nel progetto di Visual Studio senza ricompilare il progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="47f53-155">This allows you modify script files in the Visual Studio project without rebuilding Unity project.</span></span>
* <span data-ttu-id="47f53-156">Fare clic su **Impostazioni lettore**.</span><span class="sxs-lookup"><span data-stu-id="47f53-156">Click **Player Settings**.</span></span>
* <span data-ttu-id="47f53-157">Nel pannello **Inspector** scorrere fino alla fine</span><span class="sxs-lookup"><span data-stu-id="47f53-157">In the **Inspector** panel, scroll down to the bottom</span></span>
* <span data-ttu-id="47f53-158">In impostazioni XR controllare la **realtà virtuale supportata**</span><span class="sxs-lookup"><span data-stu-id="47f53-158">In XR Settings, check **Virtual Reality Supported**</span></span>
* <span data-ttu-id="47f53-159">In Virtual Reality SDK selezionare **realtà mista di Windows**</span><span class="sxs-lookup"><span data-stu-id="47f53-159">Under Virtual Reality SDKs, select **Windows Mixed Reality**</span></span>

    ![MR213_XRSettings](images/mr213-xrsettings-500px.png)

* <span data-ttu-id="47f53-161">Chiudi finestra **impostazioni di compilazione** .</span><span class="sxs-lookup"><span data-stu-id="47f53-161">Close **Build Settings** window.</span></span>

### <a name="project-structure"></a><span data-ttu-id="47f53-162">Struttura del progetto</span><span class="sxs-lookup"><span data-stu-id="47f53-162">Project structure</span></span>

<span data-ttu-id="47f53-163">Questa esercitazione USA **[mixed reality Toolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** .</span><span class="sxs-lookup"><span data-stu-id="47f53-163">This tutorial uses **[Mixed Reality Toolkit - Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)**.</span></span> <span data-ttu-id="47f53-164">È possibile trovare le versioni in [Questa pagina](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).</span><span class="sxs-lookup"><span data-stu-id="47f53-164">You can find the releases on [this page](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).</span></span>

![ProjectStructure](images/mr213-projectstructure-650px.png)

<span data-ttu-id="47f53-166">**Scene completate per il riferimento**</span><span class="sxs-lookup"><span data-stu-id="47f53-166">**Completed scenes for your reference**</span></span>

* <span data-ttu-id="47f53-167">Sono disponibili due scene Unity completate nella cartella **Scenes** .</span><span class="sxs-lookup"><span data-stu-id="47f53-167">You will find two completed Unity scenes under **Scenes** folder.</span></span>
    * <span data-ttu-id="47f53-168">**MixedReality213**: scena completata con pennello singolo</span><span class="sxs-lookup"><span data-stu-id="47f53-168">**MixedReality213**: Completed scene with single brush</span></span>
    * <span data-ttu-id="47f53-169">**MixedReality213Advanced**: scenario completato per la progettazione avanzata con più pennelli</span><span class="sxs-lookup"><span data-stu-id="47f53-169">**MixedReality213Advanced**: Completed scene for advanced design with multiple brushes</span></span>

<span data-ttu-id="47f53-170">**Nuova configurazione della scena per l'esercitazione**</span><span class="sxs-lookup"><span data-stu-id="47f53-170">**New Scene setup for the tutorial**</span></span>

* <span data-ttu-id="47f53-171">In Unity fare clic su **File > nuova scena**</span><span class="sxs-lookup"><span data-stu-id="47f53-171">In Unity, click **File > New Scene**</span></span>
* <span data-ttu-id="47f53-172">Elimina la **fotocamera principale** e la **luce direzionale**</span><span class="sxs-lookup"><span data-stu-id="47f53-172">Delete **Main Camera** and **Directional Light**</span></span>
* <span data-ttu-id="47f53-173">Dal **pannello progetto**, cercare e trascinare le seguenti prefabbricati nel pannello **gerarchia** :</span><span class="sxs-lookup"><span data-stu-id="47f53-173">From the **Project panel**, search and drag the following prefabs into the **Hierarchy** panel:</span></span>
    * <span data-ttu-id="47f53-174">Assets/HoloToolkit/input/prefabbricates/**MixedRealityCamera**</span><span class="sxs-lookup"><span data-stu-id="47f53-174">Assets/HoloToolkit/Input/Prefabs/**MixedRealityCamera**</span></span>
    * <span data-ttu-id="47f53-175">Assets/AppPrefabs/**Environment**</span><span class="sxs-lookup"><span data-stu-id="47f53-175">Assets/AppPrefabs/**Environment**</span></span>

    ![Fotocamera e ambiente](images/mr213-cameraenvironment-300px.jpg)

* <span data-ttu-id="47f53-177">Nel Toolkit per realtà mista sono disponibili due prefabbricati della fotocamera:</span><span class="sxs-lookup"><span data-stu-id="47f53-177">There are two camera prefabs in Mixed Reality Toolkit:</span></span>
    * <span data-ttu-id="47f53-178">**MixedRealityCamera. prefabbricator**: solo fotocamera</span><span class="sxs-lookup"><span data-stu-id="47f53-178">**MixedRealityCamera.prefab**: Camera only</span></span>
    * <span data-ttu-id="47f53-179">**MixedRealityCameraParent. prefabricable**: fotocamera + Teleporting + limite</span><span class="sxs-lookup"><span data-stu-id="47f53-179">**MixedRealityCameraParent.prefab**: Camera + Teleportation + Boundary</span></span>
    * <span data-ttu-id="47f53-180">In questa esercitazione si userà **MixedRealityCamera** senza funzionalità di Teleporting.</span><span class="sxs-lookup"><span data-stu-id="47f53-180">In this tutorial, we will use **MixedRealityCamera** without teleportation feature.</span></span> <span data-ttu-id="47f53-181">Per questo motivo, è stata aggiunta una semplice prefabbricata dell' **ambiente** che contiene un piano di base per fare in modo che l'utente si trovi a terra.</span><span class="sxs-lookup"><span data-stu-id="47f53-181">Because of this, we added simple **Environment** prefab which contains a basic floor to make the user feel grounded.</span></span>
    * <span data-ttu-id="47f53-182">Per altre informazioni sulla teleportazione con **MixedRealityCameraParent**, vedere [Advanced Design-Teleporting and locomotion](#advanced-design---teleportation-and-locomotion)</span><span class="sxs-lookup"><span data-stu-id="47f53-182">To learn more about the teleportation with **MixedRealityCameraParent**, see [Advanced design - Teleportation and locomotion](#advanced-design---teleportation-and-locomotion)</span></span>

<span data-ttu-id="47f53-183">**Installazione di SKYBOX**</span><span class="sxs-lookup"><span data-stu-id="47f53-183">**Skybox setup**</span></span>

* <span data-ttu-id="47f53-184">Fare clic su **finestra > illuminazione impostazioni >**</span><span class="sxs-lookup"><span data-stu-id="47f53-184">Click **Window > Lighting > Settings**</span></span>
* <span data-ttu-id="47f53-185">Fare clic sul cerchio sul lato destro del **campo materiale SKYBOX**</span><span class="sxs-lookup"><span data-stu-id="47f53-185">Click the circle on the right side of the **Skybox Material field**</span></span>
* <span data-ttu-id="47f53-186">Digitare ' Gray ' e selezionare **SkyboxGray** (assets/AppPrefabs/Support/Materials/SkyboxGray. mat)</span><span class="sxs-lookup"><span data-stu-id="47f53-186">Type in ‘gray’ and select **SkyboxGray** (Assets/AppPrefabs/Support/Materials/SkyboxGray.mat)</span></span>

    ![Impostazione di SKYBOX](images/mr123-skyboxsetting-400px.jpg)

* <span data-ttu-id="47f53-188">Selezionare l'opzione **SKYBOX** per visualizzare la sfumatura grigia assegnata SKYBOX</span><span class="sxs-lookup"><span data-stu-id="47f53-188">Check **Skybox** option to be able to see assigned gray gradient skybox</span></span>

    ![Opzione interruttore SKYBOX](images/mr213-skyboxcheck-400px.jpg)

* <span data-ttu-id="47f53-190">La scena con MixedRealityCamera, Environment e SKYBOX grigio sarà simile alla seguente.</span><span class="sxs-lookup"><span data-stu-id="47f53-190">The scene with MixedRealityCamera, Environment and gray skybox will look like this.</span></span>

    ![Ambiente MixedReality213](images/mr213-environment-600px.jpg)

* <span data-ttu-id="47f53-192">Fare clic su **File > Salva scena come**</span><span class="sxs-lookup"><span data-stu-id="47f53-192">Click **File > Save Scene as**</span></span>
* <span data-ttu-id="47f53-193">**Salva** la scena nella cartella Scenes con qualsiasi nome</span><span class="sxs-lookup"><span data-stu-id="47f53-193">**Save** your scene under Scenes folder with any name</span></span>

## <a name="chapter-1---controller-visualization"></a><span data-ttu-id="47f53-194">Capitolo 1-Visualizzazione del controller</span><span class="sxs-lookup"><span data-stu-id="47f53-194">Chapter 1 - Controller visualization</span></span>

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a><span data-ttu-id="47f53-195">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="47f53-195">Objectives</span></span>

* <span data-ttu-id="47f53-196">Informazioni su come eseguire il rendering dei modelli di controller di movimento in modalità gioco di Unity e in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="47f53-196">Learn how to render motion controller models in Unity's game mode and at runtime.</span></span>

<span data-ttu-id="47f53-197">La realtà mista di Windows fornisce un modello di controller animato per la visualizzazione del controller.</span><span class="sxs-lookup"><span data-stu-id="47f53-197">Windows Mixed Reality provides an animated controller model for controller visualization.</span></span> <span data-ttu-id="47f53-198">È possibile adottare diversi approcci per la visualizzazione del controller nell'app:</span><span class="sxs-lookup"><span data-stu-id="47f53-198">There are several approaches you can take for controller visualization in your app:</span></span>

* <span data-ttu-id="47f53-199">Impostazione predefinita: utilizzo del controller predefinito senza modifiche</span><span class="sxs-lookup"><span data-stu-id="47f53-199">Default - Using default controller without modification</span></span>
* <span data-ttu-id="47f53-200">Ibrido: uso del controller predefinito, ma personalizzazione di alcuni elementi o sovrapposizione di componenti dell'interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="47f53-200">Hybrid - Using default controller, but customizing some of its elements or overlaying UI components</span></span>
* <span data-ttu-id="47f53-201">Sostituzione: uso del modello 3D personalizzato per il controller</span><span class="sxs-lookup"><span data-stu-id="47f53-201">Replacement - Using your own customized 3D model for the controller</span></span>

<span data-ttu-id="47f53-202">In questo capitolo vengono fornite informazioni sugli esempi di queste personalizzazioni del controller.</span><span class="sxs-lookup"><span data-stu-id="47f53-202">In this chapter, we will learn about the examples of these controller customizations.</span></span>

### <a name="instructions"></a><span data-ttu-id="47f53-203">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="47f53-203">Instructions</span></span>

* <span data-ttu-id="47f53-204">Nel pannello **progetto** digitare **MotionControllers** nella casella di ricerca.</span><span class="sxs-lookup"><span data-stu-id="47f53-204">In the **Project** panel, type **MotionControllers** in the search box .</span></span> <span data-ttu-id="47f53-205">È possibile trovarlo anche in assets/HoloToolkit/input/prefabrics/.</span><span class="sxs-lookup"><span data-stu-id="47f53-205">You can also find it under Assets/HoloToolkit/Input/Prefabs/.</span></span>
* <span data-ttu-id="47f53-206">Trascinare **MotionControllers** prefabbricate nel pannello **gerarchia** .</span><span class="sxs-lookup"><span data-stu-id="47f53-206">Drag the **MotionControllers** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="47f53-207">Fare clic su **MotionControllers** prefabbricate nel pannello **gerarchia** .</span><span class="sxs-lookup"><span data-stu-id="47f53-207">Click on the **MotionControllers** prefab in the **Hierarchy** panel.</span></span>

<span data-ttu-id="47f53-208">**MotionControllers prefabbricato**</span><span class="sxs-lookup"><span data-stu-id="47f53-208">**MotionControllers prefab**</span></span>

<span data-ttu-id="47f53-209">**MotionControllers** prefabbricate include uno script **MotionControllerVisualizer** che fornisce gli slot per i modelli di controller alternativi.</span><span class="sxs-lookup"><span data-stu-id="47f53-209">**MotionControllers** prefab has a **MotionControllerVisualizer** script which provides the slots for alternate controller models.</span></span> <span data-ttu-id="47f53-210">Se si assegnano modelli 3D personalizzati, ad esempio una mano o una spada e si seleziona "Usa sempre il modello alternativo sinistro/destro", vengono visualizzati anziché il modello predefinito.</span><span class="sxs-lookup"><span data-stu-id="47f53-210">If you assign your own custom 3D models such as a hand or a sword and check 'Always Use Alternate Left/Right Model', you will see them instead of the default model.</span></span> <span data-ttu-id="47f53-211">Questo slot verrà usato nel capitolo 4 per sostituire il modello di controller con un pennello.</span><span class="sxs-lookup"><span data-stu-id="47f53-211">We will use this slot in Chapter 4 to replace the controller model with a brush.</span></span>

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

<span data-ttu-id="47f53-213">**Istruzioni**</span><span class="sxs-lookup"><span data-stu-id="47f53-213">**Instructions**</span></span>

* <span data-ttu-id="47f53-214">Nel pannello di **controllo** fare doppio clic su **MotionControllerVisualizer** script per visualizzare il codice in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="47f53-214">In the **Inspector** panel, double click **MotionControllerVisualizer** script to see the code in the Visual Studio</span></span>

<span data-ttu-id="47f53-215">**Script MotionControllerVisualizer**</span><span class="sxs-lookup"><span data-stu-id="47f53-215">**MotionControllerVisualizer script**</span></span>

<span data-ttu-id="47f53-216">Le classi **MotionControllerVisualizer** e **MotionControllerInfo** forniscono i mezzi per accedere & modificare i modelli di controller predefiniti.</span><span class="sxs-lookup"><span data-stu-id="47f53-216">The **MotionControllerVisualizer** and **MotionControllerInfo** classes provide the means to access & modify the default controller models.</span></span> <span data-ttu-id="47f53-217">**MotionControllerVisualizer** sottoscrive l'evento **InteractionSourceDetected** di Unity e crea automaticamente un'istanza dei modelli di controller quando vengono trovati.</span><span class="sxs-lookup"><span data-stu-id="47f53-217">**MotionControllerVisualizer** subscribes to Unity's **InteractionSourceDetected** event and automatically instantiates controller models when they are found.</span></span>

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

<span data-ttu-id="47f53-218">I modelli del controller vengono recapitati in base alla [specifica glTF](https://github.com/KhronosGroup/glTF).</span><span class="sxs-lookup"><span data-stu-id="47f53-218">The controller models are delivered according to [the glTF specification](https://github.com/KhronosGroup/glTF).</span></span> <span data-ttu-id="47f53-219">Questo formato è stato creato per fornire un formato comune, migliorando al tempo stesso il processo di trasmissione e decompressione degli asset 3D.</span><span class="sxs-lookup"><span data-stu-id="47f53-219">This format has been created to provide a common format, while improving the process behind transmitting and unpacking 3D assets.</span></span> <span data-ttu-id="47f53-220">In questo caso, è necessario recuperare e caricare i modelli di controller in fase di esecuzione, poiché si vuole rendere l'esperienza utente il più semplice possibile e non è garantita la versione dei controller di movimento che l'utente potrebbe usare.</span><span class="sxs-lookup"><span data-stu-id="47f53-220">In this case, we need to retrieve and load the controller models at runtime, as we want to make the user's experience as seamless as possible, and it's not guaranteed which version of the motion controllers the user might be using.</span></span> <span data-ttu-id="47f53-221">Questo corso, tramite il Toolkit di realtà mista, usa una versione del [progetto UnityGLTF](https://github.com/KhronosGroup/UnityGLTF)del gruppo Khronos.</span><span class="sxs-lookup"><span data-stu-id="47f53-221">This course, via the Mixed Reality Toolkit, uses a version of the Khronos Group's [UnityGLTF project](https://github.com/KhronosGroup/UnityGLTF).</span></span>

<span data-ttu-id="47f53-222">Una volta che il controller è stato recapitato, gli script possono usare **MotionControllerInfo** per trovare le trasformazioni per elementi controller specifici, in modo che possano posizionarsi correttamente.</span><span class="sxs-lookup"><span data-stu-id="47f53-222">Once the controller has been delivered, scripts can use **MotionControllerInfo** to find the transforms for specific controller elements so they can correctly position themselves.</span></span>

<span data-ttu-id="47f53-223">In un capitolo successivo si apprenderà come usare questi script per alleghi gli elementi dell'interfaccia utente ai controller.</span><span class="sxs-lookup"><span data-stu-id="47f53-223">In a later chapter, we will learn how to use these scripts to attach UI elements to the controllers.</span></span>

<span data-ttu-id="47f53-224">*In alcuni script, i blocchi di codice vengono trovati con **#if. UNITY_EDITOR** o **UNITY_WSA**. Questi blocchi di codice vengono eseguiti solo nel runtime UWP quando si esegue la distribuzione in Windows. Questo perché il set di API usate dall'editor di Unity e dal runtime dell'app UWP sono diversi.*</span><span class="sxs-lookup"><span data-stu-id="47f53-224">*In some scripts, you will find code blocks with **#if !UNITY_EDITOR** or **UNITY_WSA**. These code blocks run only on the UWP runtime when you deploy to Windows. This is because the set of APIs used by the Unity editor and the UWP app runtime are different.*</span></span>

* <span data-ttu-id="47f53-225">**Salva** la scena e fai clic sul pulsante **Riproduci** .</span><span class="sxs-lookup"><span data-stu-id="47f53-225">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="47f53-226">Sarà possibile visualizzare la scena con i controller di movimento nell'auricolare.</span><span class="sxs-lookup"><span data-stu-id="47f53-226">You will be able to see the scene with motion controllers in your headset.</span></span> <span data-ttu-id="47f53-227">È possibile visualizzare le animazioni dettagliate per i clic dei pulsanti, lo spostamento levetta e l'evidenziazione tocco touchpad.</span><span class="sxs-lookup"><span data-stu-id="47f53-227">You can see detailed animations for button clicks, thumbstick movement, and touchpad touch highlighting.</span></span>

![Impostazione predefinita visualizzazione MR213_Controller](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a><span data-ttu-id="47f53-229">Capitolo 2-connessione di elementi dell'interfaccia utente al controller</span><span class="sxs-lookup"><span data-stu-id="47f53-229">Chapter 2 - Attaching UI elements to the controller</span></span>

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a><span data-ttu-id="47f53-230">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="47f53-230">Objectives</span></span>

* <span data-ttu-id="47f53-231">Informazioni sugli elementi dei controller di movimento</span><span class="sxs-lookup"><span data-stu-id="47f53-231">Learn about the elements of the motion controllers</span></span>
* <span data-ttu-id="47f53-232">Informazioni su come aggiungere oggetti a parti specifiche dei controller</span><span class="sxs-lookup"><span data-stu-id="47f53-232">Learn how to attach objects to specific parts of the controllers</span></span>

<span data-ttu-id="47f53-233">In questo capitolo verrà illustrato come aggiungere elementi dell'interfaccia utente al controller che l'utente può facilmente accedere e modificare in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="47f53-233">In this chapter, you will learn how to add user interface elements to the controller which the user can easily access and manipulate at anytime.</span></span> <span data-ttu-id="47f53-234">Si apprenderà anche come aggiungere una semplice interfaccia utente della selezione colori usando l'input del touchpad.</span><span class="sxs-lookup"><span data-stu-id="47f53-234">You will also learn how to add a simple color picker UI using the touchpad input.</span></span>

### <a name="instructions"></a><span data-ttu-id="47f53-235">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="47f53-235">Instructions</span></span>

* <span data-ttu-id="47f53-236">Nel pannello del **progetto** cercare script **MotionControllerInfo** .</span><span class="sxs-lookup"><span data-stu-id="47f53-236">In the **Project** panel, search **MotionControllerInfo** script.</span></span>
* <span data-ttu-id="47f53-237">Nei risultati della ricerca fare doppio clic su **MotionControllerInfo** script per visualizzare il codice in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="47f53-237">From the search result, double click **MotionControllerInfo** script to see the code in Visual Studio.</span></span>

<span data-ttu-id="47f53-238">**Script MotionControllerInfo**</span><span class="sxs-lookup"><span data-stu-id="47f53-238">**MotionControllerInfo script**</span></span>

<span data-ttu-id="47f53-239">Il primo passaggio consiste nel scegliere l'elemento del controller a cui si vuole aggiungere l'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="47f53-239">The first step is to choose which element of the controller you want the UI to attach to.</span></span> <span data-ttu-id="47f53-240">Questi elementi sono definiti in **ControllerElementEnum** in **MotionControllerInfo.cs**.</span><span class="sxs-lookup"><span data-stu-id="47f53-240">These elements are defined in **ControllerElementEnum** in **MotionControllerInfo.cs**.</span></span>

![MR213 MotionControllerElements](images/mr213-motioncontrollerelements-1000px.jpg)

* <span data-ttu-id="47f53-242">**Casa**</span><span class="sxs-lookup"><span data-stu-id="47f53-242">**Home**</span></span>
* <span data-ttu-id="47f53-243">**Menu**</span><span class="sxs-lookup"><span data-stu-id="47f53-243">**Menu**</span></span>
* <span data-ttu-id="47f53-244">**Comprendere**</span><span class="sxs-lookup"><span data-stu-id="47f53-244">**Grasp**</span></span>
* <span data-ttu-id="47f53-245">**Levetta**</span><span class="sxs-lookup"><span data-stu-id="47f53-245">**Thumbstick**</span></span>
* <span data-ttu-id="47f53-246">**Selezionare**</span><span class="sxs-lookup"><span data-stu-id="47f53-246">**Select**</span></span>
* <span data-ttu-id="47f53-247">**Touchpad**</span><span class="sxs-lookup"><span data-stu-id="47f53-247">**Touchpad**</span></span>
* <span data-ttu-id="47f53-248">**Puntamento di pose** : questo elemento rappresenta il suggerimento della direzione di avanzamento del controller.</span><span class="sxs-lookup"><span data-stu-id="47f53-248">**Pointing pose** – this element represents the tip of the controller pointing forward direction.</span></span>

<span data-ttu-id="47f53-249">**Istruzioni**</span><span class="sxs-lookup"><span data-stu-id="47f53-249">**Instructions**</span></span>

* <span data-ttu-id="47f53-250">Nel pannello del **progetto** cercare script **AttachToController** .</span><span class="sxs-lookup"><span data-stu-id="47f53-250">In the **Project** panel, search **AttachToController** script.</span></span>
* <span data-ttu-id="47f53-251">Nei risultati della ricerca fare doppio clic su **AttachToController** script per visualizzare il codice in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="47f53-251">From the search result, double click **AttachToController** script to see the code in Visual Studio.</span></span>

<span data-ttu-id="47f53-252">**Script AttachToController**</span><span class="sxs-lookup"><span data-stu-id="47f53-252">**AttachToController script**</span></span>

<span data-ttu-id="47f53-253">Lo script **AttachToController** fornisce un modo semplice per alleghire tutti gli oggetti a un elemento e a una manualità del controller specificati.</span><span class="sxs-lookup"><span data-stu-id="47f53-253">The **AttachToController** script provides a simple way to attach any objects to a specified controller handedness and element.</span></span>

<span data-ttu-id="47f53-254">In **AttachElementToController ()** ,</span><span class="sxs-lookup"><span data-stu-id="47f53-254">In **AttachElementToController()**,</span></span>

* <span data-ttu-id="47f53-255">Controllare la manualità usando **MotionControllerInfo. manualità**</span><span class="sxs-lookup"><span data-stu-id="47f53-255">Check handedness using **MotionControllerInfo.Handedness**</span></span>
* <span data-ttu-id="47f53-256">Ottenere un elemento specifico del controller usando **MotionControllerInfo. TryGetElement ()**</span><span class="sxs-lookup"><span data-stu-id="47f53-256">Get specific element of the controller using **MotionControllerInfo.TryGetElement()**</span></span>
* <span data-ttu-id="47f53-257">Dopo aver recuperato la trasformazione dell'elemento dal modello del controller, è necessario impostare come elemento padre l'oggetto sottostante e impostare la posizione locale dell'oggetto & rotazione su zero.</span><span class="sxs-lookup"><span data-stu-id="47f53-257">After retrieving the element's transform from the controller model, parent the object under it and set object's local position & rotation to zero.</span></span>

```cs
public MotionControllerInfo.ControllerElementEnum Element { get { return element; } }

private void AttachElementToController(MotionControllerInfo newController)
{
     if (!IsAttached && newController.Handedness == handedness)
     {
          if (!newController.TryGetElement(element, out elementTransform))
          {
               Debug.LogError("Unable to find element of type " + element + " under controller " + newController.ControllerParent.name + "; not attaching.");
               return;
          }

          controller = newController;

          SetChildrenActive(true);

          // Parent ourselves under the element and set our offsets
          transform.parent = elementTransform;
          transform.localPosition = positionOffset;
          transform.localEulerAngles = rotationOffset;
          if (setScaleOnAttach)
          {
               transform.localScale = scale;
          }

          // Announce that we're attached
          OnAttachToController();
          IsAttached = true;
     }
}
```

<span data-ttu-id="47f53-258">Il modo più semplice per usare lo script **AttachToController** consiste nell'ereditare da esso, come è stato fatto nel caso di **ColorPickerWheel.**</span><span class="sxs-lookup"><span data-stu-id="47f53-258">The simplest way to use **AttachToController** script is to inherit from it, as we've done in the case of **ColorPickerWheel.**</span></span> <span data-ttu-id="47f53-259">È sufficiente eseguire l'override delle funzioni **OnAttachToController** e **OnDetachFromController** per eseguire l'installazione o la ripartizione quando il controller viene rilevato/disconnesso.</span><span class="sxs-lookup"><span data-stu-id="47f53-259">Simply override the **OnAttachToController** and **OnDetachFromController** functions to perform your setup / breakdown when the controller is detected / disconnected.</span></span>

<span data-ttu-id="47f53-260">**Istruzioni**</span><span class="sxs-lookup"><span data-stu-id="47f53-260">**Instructions**</span></span>

* <span data-ttu-id="47f53-261">Nel pannello **progetto** Digitare nella casella di ricerca **ColorPickerWheel**.</span><span class="sxs-lookup"><span data-stu-id="47f53-261">In the **Project** panel, type in the search box **ColorPickerWheel**.</span></span> <span data-ttu-id="47f53-262">È possibile trovarlo anche in assets/AppPrefabs/.</span><span class="sxs-lookup"><span data-stu-id="47f53-262">You can also find it under Assets/AppPrefabs/.</span></span>
* <span data-ttu-id="47f53-263">Trascinare **ColorPickerWheel** prefabbricate nel pannello **gerarchia** .</span><span class="sxs-lookup"><span data-stu-id="47f53-263">Drag **ColorPickerWheel** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="47f53-264">Fare clic su **ColorPickerWheel** prefabbricate nel pannello **gerarchia** .</span><span class="sxs-lookup"><span data-stu-id="47f53-264">Click the **ColorPickerWheel** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="47f53-265">Nel pannello di **controllo** fare doppio clic su **ColorPickerWheel** script per visualizzare il codice in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="47f53-265">In the **Inspector** panel, double click **ColorPickerWheel** Script to see the code in Visual Studio.</span></span>

![ColorPickerWheel prefabbricato](images/mr213-colorpickerwheel-1000px.jpg)

<span data-ttu-id="47f53-267">**Script ColorPickerWheel**</span><span class="sxs-lookup"><span data-stu-id="47f53-267">**ColorPickerWheel script**</span></span>

<span data-ttu-id="47f53-268">Poiché **ColorPickerWheel** eredita **AttachToController**, Mostra la **manualità** e l' **elemento** nel pannello **Inspector** .</span><span class="sxs-lookup"><span data-stu-id="47f53-268">Since **ColorPickerWheel** inherits **AttachToController**, it shows **Handedness** and **Element** in the **Inspector** panel.</span></span> <span data-ttu-id="47f53-269">L'interfaccia utente verrà collegata all'elemento touchpad sul controller di sinistra.</span><span class="sxs-lookup"><span data-stu-id="47f53-269">We'll be attaching the UI to the Touchpad element on the left controller.</span></span>

![Script ColorPickerWheel](images/mr213-attachtocontroller-300px.jpg)

<span data-ttu-id="47f53-271">**ColorPickerWheel** esegue l'override di **OnAttachToController** e **OnDetachFromController** per sottoscrivere l'evento di input che verrà usato nel capitolo successivo per la selezione dei colori con input touchpad.</span><span class="sxs-lookup"><span data-stu-id="47f53-271">**ColorPickerWheel** overrides the **OnAttachToController** and **OnDetachFromController** to subscribe to the input event which will be used in next chapter for color selection with touchpad input.</span></span>

```cs
public class ColorPickerWheel : AttachToController, IPointerTarget
{
    protected override void OnAttachToController()
    {
        // Subscribe to input now that we're parented under the controller
        InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
    }

    protected override void OnDetachFromController()
    {
        Visible = false;

        // Unsubscribe from input now that we've detached from the controller
        InteractionManager.InteractionSourceUpdated -= InteractionSourceUpdated;
    }
    ...
}
```

* <span data-ttu-id="47f53-272">**Salva** la scena e fai clic sul pulsante **Riproduci** .</span><span class="sxs-lookup"><span data-stu-id="47f53-272">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="47f53-273">**Metodo alternativo per il fissaggio di oggetti ai controller**</span><span class="sxs-lookup"><span data-stu-id="47f53-273">**Alternative method for attaching objects to the controllers**</span></span>

<span data-ttu-id="47f53-274">È consigliabile che gli script ereditino da **AttachToController** ed eseguano l'override di **OnAttachToController**.</span><span class="sxs-lookup"><span data-stu-id="47f53-274">We recommend that your scripts inherit from **AttachToController** and override **OnAttachToController**.</span></span> <span data-ttu-id="47f53-275">Tuttavia, questo potrebbe non essere sempre possibile.</span><span class="sxs-lookup"><span data-stu-id="47f53-275">However, this may not always be possible.</span></span> <span data-ttu-id="47f53-276">Un'alternativa viene utilizzata come componente autonomo.</span><span class="sxs-lookup"><span data-stu-id="47f53-276">An alternative is using it as a standalone component.</span></span> <span data-ttu-id="47f53-277">Questa operazione può essere utile quando si vuole alleghi un prefabbricato esistente a un controller senza effettuare il refactoring degli script.</span><span class="sxs-lookup"><span data-stu-id="47f53-277">This can be useful when you want to attach an existing prefab to a controller without refactoring your scripts.</span></span> <span data-ttu-id="47f53-278">È sufficiente che la classe attenda che sia impostato su true prima di eseguire qualsiasi installazione.</span><span class="sxs-lookup"><span data-stu-id="47f53-278">Simply have your class wait for IsAttached to be set to true before performing any setup.</span></span> <span data-ttu-id="47f53-279">Il modo più semplice per eseguire questa operazione consiste nell'usare una coroutine per "Start".</span><span class="sxs-lookup"><span data-stu-id="47f53-279">The simplest way to do this is by using a coroutine for 'Start.'</span></span>

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a><span data-ttu-id="47f53-280">Capitolo 3-uso dell'input di touchpad</span><span class="sxs-lookup"><span data-stu-id="47f53-280">Chapter 3 - Working with touchpad input</span></span>

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a><span data-ttu-id="47f53-281">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="47f53-281">Objectives</span></span>

* <span data-ttu-id="47f53-282">Informazioni su come ottenere gli eventi di dati di input di touchpad</span><span class="sxs-lookup"><span data-stu-id="47f53-282">Learn how to get touchpad input data events</span></span>
* <span data-ttu-id="47f53-283">Informazioni su come usare le informazioni sulla posizione dell'asse del touchpad per l'esperienza dell'app</span><span class="sxs-lookup"><span data-stu-id="47f53-283">Learn how to use touchpad axis position information for your app experience</span></span>

### <a name="instructions"></a><span data-ttu-id="47f53-284">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="47f53-284">Instructions</span></span>

* <span data-ttu-id="47f53-285">Nel pannello **gerarchia** fare clic su **ColorPickerWheel**</span><span class="sxs-lookup"><span data-stu-id="47f53-285">In the **Hierarchy** panel, click **ColorPickerWheel**</span></span>
* <span data-ttu-id="47f53-286">Nel pannello **Inspector** , in **Animator**, fare doppio clic su **ColorPickerWheelController**</span><span class="sxs-lookup"><span data-stu-id="47f53-286">In the **Inspector** panel, under **Animator**, double click **ColorPickerWheelController**</span></span>
* <span data-ttu-id="47f53-287">Sarà possibile visualizzare la scheda **Animator** aperta</span><span class="sxs-lookup"><span data-stu-id="47f53-287">You will be able to see **Animator** tab opened</span></span>

<span data-ttu-id="47f53-288">**Visualizzazione/occultamento dell'interfaccia utente con il controller di animazione di Unity**</span><span class="sxs-lookup"><span data-stu-id="47f53-288">**Showing/hiding UI with Unity's Animation controller**</span></span>

<span data-ttu-id="47f53-289">Per mostrare e nascondere l'interfaccia utente di **ColorPickerWheel** con animazione, viene usato il [sistema di animazione di Unity](https://docs.unity3d.com/Manual/AnimationOverview.html).</span><span class="sxs-lookup"><span data-stu-id="47f53-289">To show and hide the **ColorPickerWheel** UI with animation, we are using [Unity's animation system](https://docs.unity3d.com/Manual/AnimationOverview.html).</span></span> <span data-ttu-id="47f53-290">Impostando la proprietà **Visible** di **ColorPickerWheel**su true o false, i trigger **mostrano** e **nascondono** i trigger di animazione.</span><span class="sxs-lookup"><span data-stu-id="47f53-290">Setting the **ColorPickerWheel**'s **Visible** property to true or false triggers **Show** and **Hide** animation triggers.</span></span> <span data-ttu-id="47f53-291">I parametri **show** e **Hide** sono definiti nel controller di animazione **ColorPickerWheelController** .</span><span class="sxs-lookup"><span data-stu-id="47f53-291">**Show** and **Hide** parameters are defined in the **ColorPickerWheelController** animation controller.</span></span>

![Controller animazione Unity](images/mr123-animationcontroller-550px.jpg)

<span data-ttu-id="47f53-293">**Istruzioni**</span><span class="sxs-lookup"><span data-stu-id="47f53-293">**Instructions**</span></span>

* <span data-ttu-id="47f53-294">Nel pannello **gerarchia** selezionare **ColorPickerWheel** prefabbricate</span><span class="sxs-lookup"><span data-stu-id="47f53-294">In the **Hierarchy** panel, select **ColorPickerWheel** prefab</span></span>
* <span data-ttu-id="47f53-295">Nel pannello di **controllo** fare doppio clic su **ColorPickerWheel** script per visualizzare il codice in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="47f53-295">In the **Inspector** panel, double click **ColorPickerWheel** script to see the code in the Visual Studio</span></span>

<span data-ttu-id="47f53-296">**Script ColorPickerWheel**</span><span class="sxs-lookup"><span data-stu-id="47f53-296">**ColorPickerWheel script**</span></span>

<span data-ttu-id="47f53-297">**ColorPickerWheel** sottoscrive l'evento **InteractionSourceUpdated** di Unity per ascoltare gli eventi del touchpad.</span><span class="sxs-lookup"><span data-stu-id="47f53-297">**ColorPickerWheel** subscribes to Unity's **InteractionSourceUpdated** event to listen for touchpad events.</span></span>

<span data-ttu-id="47f53-298">In **InteractionSourceUpdated ()** , lo script verifica prima di tutto che:</span><span class="sxs-lookup"><span data-stu-id="47f53-298">In **InteractionSourceUpdated()**, the script first checks to ensure that it:</span></span>

* <span data-ttu-id="47f53-299">è in realtà un evento touchpad (obj. state. **touchpadTouched**)</span><span class="sxs-lookup"><span data-stu-id="47f53-299">is actually a touchpad event (obj.state.**touchpadTouched**)</span></span>
* <span data-ttu-id="47f53-300">ha origine dal controller sinistro (obj. state. Source. **manualità**)</span><span class="sxs-lookup"><span data-stu-id="47f53-300">originates from the left controller (obj.state.source.**handedness**)</span></span>

<span data-ttu-id="47f53-301">Se entrambi sono true, la posizione del touchpad (obj. state. **touchpadPosition**) viene assegnato a **selectorPosition**.</span><span class="sxs-lookup"><span data-stu-id="47f53-301">If both are true, the touchpad position (obj.state.**touchpadPosition**) is assigned to **selectorPosition**.</span></span>

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness && obj.state.touchpadTouched)
    {
        Visible = true;
        selectorPosition = obj.state.touchpadPosition;
    }
}
```

<span data-ttu-id="47f53-302">In **Update ()** , in base alla proprietà **Visible** , attiva i trigger Show e Hide Animation nel componente Animator della selezione colori</span><span class="sxs-lookup"><span data-stu-id="47f53-302">In **Update()**, based on **visible** property, it triggers Show and Hide animation triggers in the color picker's animator component</span></span>

```cs
if (visible != visibleLastFrame)
{
    if (visible)
    {
        animator.SetTrigger("Show");
    }
    else
    {
        animator.SetTrigger("Hide");
    }
}
```

<span data-ttu-id="47f53-303">In **Update ()** , **selectorPosition** viene usato per eseguire il cast di un raggio nella mesh Collider della rotellina dei colori, che restituisce una posizione UV.</span><span class="sxs-lookup"><span data-stu-id="47f53-303">In **Update()**, **selectorPosition** is used to cast a ray at the color wheel's mesh collider, which returns a UV position.</span></span> <span data-ttu-id="47f53-304">Questa posizione può quindi essere usata per trovare la coordinata del pixel e il valore del colore della trama della rotellina dei colori.</span><span class="sxs-lookup"><span data-stu-id="47f53-304">This position can then be used to find the pixel coordinate and color value of the color wheel's texture.</span></span> <span data-ttu-id="47f53-305">Questo valore è accessibile ad altri script tramite la proprietà **SelectedColor** .</span><span class="sxs-lookup"><span data-stu-id="47f53-305">This value is accessible to other scripts via the **SelectedColor** property.</span></span>

![Rotellina selezione colori Raycasting](images/mr213-colorpickerwheel-raycast-700px.png)

```cs
...
    // Clamp selector position to a radius of 1
    Vector3 localPosition = new Vector3(selectorPosition.x * inputScale, 0.15f, selectorPosition.y * inputScale);
    if (localPosition.magnitude > 1)
    {
        localPosition = localPosition.normalized;
    }
    selectorTransform.localPosition = localPosition;

    // Raycast the wheel mesh and get its UV coordinates
    Vector3 raycastStart = selectorTransform.position + selectorTransform.up * 0.15f;
    RaycastHit hit;
    Debug.DrawLine(raycastStart, raycastStart - (selectorTransform.up * 0.25f));

    if (Physics.Raycast(raycastStart, -selectorTransform.up, out hit, 0.25f, 1 << colorWheelObject.layer, QueryTriggerInteraction.Ignore))
    {
        // Get pixel from the color wheel texture using UV coordinates
        Vector2 uv = hit.textureCoord;
        int pixelX = Mathf.FloorToInt(colorWheelTexture.width * uv.x);
        int pixelY = Mathf.FloorToInt(colorWheelTexture.height * uv.y);
        selectedColor = colorWheelTexture.GetPixel(pixelX, pixelY);
        selectedColor.a = 1f;
    }
    // Set the selector's color and blend it with white to make it visible on top of the wheel
    selectorRenderer.material.color = Color.Lerp (selectedColor, Color.white, 0.5f);
}
```

## <a name="chapter-4---overriding-controller-model"></a><span data-ttu-id="47f53-307">Capitolo 4-override del modello di controller</span><span class="sxs-lookup"><span data-stu-id="47f53-307">Chapter 4 - Overriding controller model</span></span>

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a><span data-ttu-id="47f53-308">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="47f53-308">Objectives</span></span>

* <span data-ttu-id="47f53-309">Informazioni su come eseguire l'override del modello di controller con un modello 3D personalizzato.</span><span class="sxs-lookup"><span data-stu-id="47f53-309">Learn how to override the controller model with a custom 3D model.</span></span>

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a><span data-ttu-id="47f53-311">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="47f53-311">Instructions</span></span>

* <span data-ttu-id="47f53-312">Fare clic su **MotionControllers** nel pannello **gerarchia** .</span><span class="sxs-lookup"><span data-stu-id="47f53-312">Click **MotionControllers** in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="47f53-313">Fare clic sul cerchio sul lato destro del campo del **controller alternativo a destra** .</span><span class="sxs-lookup"><span data-stu-id="47f53-313">Click the circle on the right side of the **Alternate Right Controller** field.</span></span>
* <span data-ttu-id="47f53-314">Digitare **"BrushController**" e selezionare il prefabbricato dal risultato.</span><span class="sxs-lookup"><span data-stu-id="47f53-314">Type in **'BrushController**' and select the prefab from the result.</span></span> <span data-ttu-id="47f53-315">È possibile trovarlo in assets/AppPrefabs/**BrushController**.</span><span class="sxs-lookup"><span data-stu-id="47f53-315">You can find it under Assets/AppPrefabs/**BrushController**.</span></span>
* <span data-ttu-id="47f53-316">Selezionare **Usa sempre il modello alternativo destro**</span><span class="sxs-lookup"><span data-stu-id="47f53-316">Check **Always Use Alternate Right Model**</span></span>

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

<span data-ttu-id="47f53-318">Il prefabbricato **BrushController** non deve essere incluso nel pannello **gerarchia** .</span><span class="sxs-lookup"><span data-stu-id="47f53-318">The **BrushController** prefab does not have to be included in the **Hierarchy** panel.</span></span> <span data-ttu-id="47f53-319">Tuttavia, per estrarre i componenti figlio:</span><span class="sxs-lookup"><span data-stu-id="47f53-319">However, to check out its child components:</span></span>

* <span data-ttu-id="47f53-320">Nel pannello **progetto** digitare **BrushController** e trascinare **BrushController** prefabbricate nel pannello **gerarchia** .</span><span class="sxs-lookup"><span data-stu-id="47f53-320">In the **Project** panel, type in **BrushController** and drag **BrushController** prefab into the **Hierarchy** panel.</span></span>

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

<span data-ttu-id="47f53-322">Il componente **Tip** è presente in **BrushController**.</span><span class="sxs-lookup"><span data-stu-id="47f53-322">You will find the **Tip** component in **BrushController**.</span></span> <span data-ttu-id="47f53-323">Si userà la relativa trasformazione per avviare/arrestare il disegno delle linee.</span><span class="sxs-lookup"><span data-stu-id="47f53-323">We will use its transform to start/stop drawing lines.</span></span>

* <span data-ttu-id="47f53-324">Eliminare il **BrushController** dal pannello **gerarchia** .</span><span class="sxs-lookup"><span data-stu-id="47f53-324">Delete the **BrushController** from the **Hierarchy** panel.</span></span>
* <span data-ttu-id="47f53-325">**Salva** la scena e fai clic sul pulsante **Riproduci** .</span><span class="sxs-lookup"><span data-stu-id="47f53-325">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="47f53-326">Sarà possibile vedere il modello di pennello sostituito dal controller di movimento a destra.</span><span class="sxs-lookup"><span data-stu-id="47f53-326">You will be able to see the brush model replaced the right-hand motion controller.</span></span>

## <a name="chapter-5---painting-with-select-input"></a><span data-ttu-id="47f53-327">Capitolo 5-disegno con SELECT input</span><span class="sxs-lookup"><span data-stu-id="47f53-327">Chapter 5 - Painting with Select input</span></span>

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a><span data-ttu-id="47f53-328">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="47f53-328">Objectives</span></span>

* <span data-ttu-id="47f53-329">Informazioni su come usare l'evento seleziona pulsante per avviare e arrestare un disegno a linee</span><span class="sxs-lookup"><span data-stu-id="47f53-329">Learn how to use the Select button event to start and stop a line drawing</span></span>

### <a name="instructions"></a><span data-ttu-id="47f53-330">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="47f53-330">Instructions</span></span>

* <span data-ttu-id="47f53-331">Cercare **BrushController** prefabbricate nel pannello del **progetto** .</span><span class="sxs-lookup"><span data-stu-id="47f53-331">Search **BrushController** prefab in the **Project** panel.</span></span>
* <span data-ttu-id="47f53-332">Nel pannello di **controllo** fare doppio clic su **BrushController** script per visualizzare il codice in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="47f53-332">In the **Inspector** panel, double click **BrushController** Script to see the code in Visual Studio</span></span>

<span data-ttu-id="47f53-333">**Script BrushController**</span><span class="sxs-lookup"><span data-stu-id="47f53-333">**BrushController script**</span></span>

<span data-ttu-id="47f53-334">**BrushController** sottoscrive gli eventi **InteractionSourcePressed** e **InteractionSourceReleased** di InteractionManager.</span><span class="sxs-lookup"><span data-stu-id="47f53-334">**BrushController** subscribes to the InteractionManager's **InteractionSourcePressed** and **InteractionSourceReleased** events.</span></span> <span data-ttu-id="47f53-335">Quando viene attivato l'evento **InteractionSourcePressed** , la proprietà di **disegno** del pennello è impostata su true; Quando viene attivato l'evento **InteractionSourceReleased** , la proprietà di **disegno** del pennello è impostata su false.</span><span class="sxs-lookup"><span data-stu-id="47f53-335">When **InteractionSourcePressed** event is triggered, the brush's **Draw** property is set to true; when **InteractionSourceReleased** event is triggered, the brush's **Draw** property is set to false.</span></span>

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = true;
    }
}

private void InteractionSourceReleased(InteractionSourceReleasedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = false;
    }
}
```

<span data-ttu-id="47f53-336">Mentre il **disegno** è impostato su true, il pennello genererà punti in un **LineRenderer**Unity di cui è stata creata un'istanza.</span><span class="sxs-lookup"><span data-stu-id="47f53-336">While **Draw** is set to true, the brush will generate points in an instantiated Unity **LineRenderer**.</span></span> <span data-ttu-id="47f53-337">Un riferimento a questo prefabbricato viene mantenuto nel campo **prefabbricato Stroke** del pennello.</span><span class="sxs-lookup"><span data-stu-id="47f53-337">A reference to this prefab is kept in the brush's **Stroke Prefab** field.</span></span>

```cs
private IEnumerator DrawOverTime()
{
    // Get the position of the tip
    Vector3 lastPointPosition = tip.position;

    ...

    // Create a new brush stroke
    GameObject newStroke = Instantiate(strokePrefab);
    LineRenderer line = newStroke.GetComponent<LineRenderer>();
    newStroke.transform.position = startPosition;
    line.SetPosition(0, tip.position);
    float initialWidth = line.widthMultiplier;

    // Generate points in an instantiated Unity LineRenderer
    while (draw)
    {
        // Move the last point to the draw point position
        line.SetPosition(line.positionCount - 1, tip.position);
        line.material.color = colorPicker.SelectedColor;
        brushRenderer.material.color = colorPicker.SelectedColor;
        lastPointAddedTime = Time.unscaledTime;
        // Adjust the width between 1x and 2x width based on strength of trigger pull
        line.widthMultiplier = Mathf.Lerp(initialWidth, initialWidth * 2, width);

        if (Vector3.Distance(lastPointPosition, tip.position) > minPositionDelta || Time.unscaledTime > lastPointAddedTime + maxTimeDelta)
        {
            // Spawn a new point
            lastPointAddedTime = Time.unscaledTime;
            lastPointPosition = tip.position;
            line.positionCount += 1;
            line.SetPosition(line.positionCount - 1, lastPointPosition);
        }
        yield return null;
    }
}
```

<span data-ttu-id="47f53-338">Per usare il colore attualmente selezionato dall'interfaccia utente della rotellina della selezione colori, **BrushController** deve avere un riferimento all'oggetto **ColorPickerWheel** .</span><span class="sxs-lookup"><span data-stu-id="47f53-338">To use the currently selected color from the color picker wheel UI, **BrushController** needs to have a reference to the **ColorPickerWheel** object.</span></span> <span data-ttu-id="47f53-339">Dato che viene creata un'istanza del prefabbricato **BrushController** in fase di esecuzione come controller sostitutivo, tutti i riferimenti agli oggetti nella scena dovranno essere impostati in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="47f53-339">Because the **BrushController** prefab is instantiated at runtime as a replacement controller, any references to objects in the scene will have to be set at runtime.</span></span> <span data-ttu-id="47f53-340">In questo caso si usa **GameObject. FindObjectOfType** per individuare il **ColorPickerWheel**:</span><span class="sxs-lookup"><span data-stu-id="47f53-340">In this case we use **GameObject.FindObjectOfType** to locate the **ColorPickerWheel**:</span></span>

```cs
private void OnEnable()
{
    // Locate the ColorPickerWheel
    colorPicker = FindObjectOfType<ColorPickerWheel>();

    // Assign currently selected color to the brush’s material color
    brushRenderer.material.color = colorPicker.SelectedColor;
    ...
}
```

* <span data-ttu-id="47f53-341">**Salva** la scena e fai clic sul pulsante **Riproduci** .</span><span class="sxs-lookup"><span data-stu-id="47f53-341">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="47f53-342">Sarà possibile disegnare le linee e il disegno usando il pulsante Seleziona sul controller a destra.</span><span class="sxs-lookup"><span data-stu-id="47f53-342">You will be able to draw the lines and paint using the select button on the right-hand controller.</span></span>

## <a name="chapter-6---object-spawning-with-select-input"></a><span data-ttu-id="47f53-343">Capitolo 6-generazione di oggetti con l'input selezionato</span><span class="sxs-lookup"><span data-stu-id="47f53-343">Chapter 6 - Object spawning with Select input</span></span>

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a><span data-ttu-id="47f53-344">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="47f53-344">Objectives</span></span>

* <span data-ttu-id="47f53-345">Informazioni su come usare gli eventi di input del pulsante Seleziona e afferra</span><span class="sxs-lookup"><span data-stu-id="47f53-345">Learn how to use Select and Grasp button input events</span></span>
* <span data-ttu-id="47f53-346">Informazioni su come creare un'istanza di oggetti</span><span class="sxs-lookup"><span data-stu-id="47f53-346">Learn how to instantiate objects</span></span>

### <a name="instructions"></a><span data-ttu-id="47f53-347">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="47f53-347">Instructions</span></span>

* <span data-ttu-id="47f53-348">Nel pannello **progetto** digitare **ObjectSpawner** nella casella di ricerca.</span><span class="sxs-lookup"><span data-stu-id="47f53-348">In the **Project** panel, type **ObjectSpawner** in the search box.</span></span> <span data-ttu-id="47f53-349">È possibile trovarlo anche in assets/AppPrefabs/</span><span class="sxs-lookup"><span data-stu-id="47f53-349">You can also find it under Assets/AppPrefabs/</span></span>
* <span data-ttu-id="47f53-350">Trascinare **ObjectSpawner** prefabbricate nel pannello **gerarchia** .</span><span class="sxs-lookup"><span data-stu-id="47f53-350">Drag the **ObjectSpawner** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="47f53-351">Fare clic su **ObjectSpawner** nel pannello **gerarchia** .</span><span class="sxs-lookup"><span data-stu-id="47f53-351">Click **ObjectSpawner** in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="47f53-352">**ObjectSpawner** dispone di un campo denominato **source color**.</span><span class="sxs-lookup"><span data-stu-id="47f53-352">**ObjectSpawner** has a field named **Color Source**.</span></span>
* <span data-ttu-id="47f53-353">Dal pannello **gerarchia** trascinare il riferimento **ColorPickerWheel** in questo campo.</span><span class="sxs-lookup"><span data-stu-id="47f53-353">From the **Hierarchy** panel, drag the **ColorPickerWheel** reference into this field.</span></span>

    ![Controllo generatore oggetti](images/mr213-objectspawnercolorpickerwheel-650px.jpg)

* <span data-ttu-id="47f53-355">Fare clic su **ObjectSpawner** prefabbricate nel pannello **gerarchia** .</span><span class="sxs-lookup"><span data-stu-id="47f53-355">Click the **ObjectSpawner** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="47f53-356">Nel pannello di **controllo** fare doppio clic su **ObjectSpawner** script per visualizzare il codice in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="47f53-356">In the **Inspector** panel, double click **ObjectSpawner** Script to see the code in Visual Studio.</span></span>

<span data-ttu-id="47f53-357">**Script ObjectSpawner**</span><span class="sxs-lookup"><span data-stu-id="47f53-357">**ObjectSpawner script**</span></span>

<span data-ttu-id="47f53-358">**ObjectSpawner** crea un'istanza delle copie di una mesh primitiva (cubo, sfera, cilindro) nello spazio.</span><span class="sxs-lookup"><span data-stu-id="47f53-358">The **ObjectSpawner** instantiates copies of a primitive mesh (cube, sphere, cylinder) into the space.</span></span> <span data-ttu-id="47f53-359">Quando viene rilevato un **InteractionSourcePressed** , controlla la manualità e se si tratta di un evento **InteractionSourcePressType. afferrare** o **InteractionSourcePressType. Select** .</span><span class="sxs-lookup"><span data-stu-id="47f53-359">When a **InteractionSourcePressed** is detected it checks the handedness and if it's an **InteractionSourcePressType.Grasp** or **InteractionSourcePressType.Select** event.</span></span>

<span data-ttu-id="47f53-360">Per un evento di **comprensione** , incrementa l'indice del tipo di mesh corrente (Sphere, Cube, Cylinder)</span><span class="sxs-lookup"><span data-stu-id="47f53-360">For a **Grasp** event, it increments the index of current mesh type (sphere, cube, cylinder)</span></span>

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    // Check handedness, see if it is left controller
    if (obj.state.source.handedness == handedness)
    {
        switch (obj.pressType)
        {
            // If it is Select button event, spawn object
            case InteractionSourcePressType.Select:
                if (state == StateEnum.Idle)
                {
                    // We've pressed the grasp - enter spawning state
                    state = StateEnum.Spawning;
                    SpawnObject();
                }
                break;

            // If it is Grasp button event
            case InteractionSourcePressType.Grasp:

                // Increment the index of current mesh type (sphere, cube, cylinder)
                meshIndex++;
                if (meshIndex >= NumAvailableMeshes)
                {
                    meshIndex = 0;
                }
                break;

            default:
                break;
        }
    }
}
```

<span data-ttu-id="47f53-361">Per un evento **Select** , in **SpawnObject ()** , viene creata un'istanza di un nuovo oggetto, senza padre e rilasciato nel mondo.</span><span class="sxs-lookup"><span data-stu-id="47f53-361">For a **Select** event, in **SpawnObject()**, a new object is instantiated, un-parented and released into the world.</span></span>

```cs
private void SpawnObject()
{
    // Instantiate the spawned object
    GameObject newObject = Instantiate(displayObject.gameObject, spawnParent);
    // Detach the newly spawned object
    newObject.transform.parent = null;
    // Reset the scale transform to 1
    scaleParent.localScale = Vector3.one;
    // Set its material color so its material gets instantiated
    newObject.GetComponent<Renderer>().material.color = colorSource.SelectedColor;
}
```

<span data-ttu-id="47f53-362">**ObjectSpawner** utilizza **ColorPickerWheel** per impostare il colore del materiale dell'oggetto visualizzato.</span><span class="sxs-lookup"><span data-stu-id="47f53-362">The **ObjectSpawner** uses the **ColorPickerWheel** to set the color of the display object's material.</span></span> <span data-ttu-id="47f53-363">Agli oggetti generati viene assegnata un'istanza di questo materiale in modo che mantengano il colore.</span><span class="sxs-lookup"><span data-stu-id="47f53-363">Spawned objects are given an instance of this material so they will retain their color.</span></span>

* <span data-ttu-id="47f53-364">**Salva** la scena e fai clic sul pulsante **Riproduci** .</span><span class="sxs-lookup"><span data-stu-id="47f53-364">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="47f53-365">Sarà possibile modificare gli oggetti con il pulsante di selezione e generare oggetti con il pulsante Seleziona.</span><span class="sxs-lookup"><span data-stu-id="47f53-365">You will be able to change the objects with the Grasp button and spawn objects with the Select button.</span></span>

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a><span data-ttu-id="47f53-366">Creare e distribuire app nel portale di realtà mista</span><span class="sxs-lookup"><span data-stu-id="47f53-366">Build and deploy app to Mixed Reality Portal</span></span>

* <span data-ttu-id="47f53-367">In Unity selezionare **File > impostazioni di compilazione**.</span><span class="sxs-lookup"><span data-stu-id="47f53-367">In Unity, select **File > Build Settings**.</span></span>
* <span data-ttu-id="47f53-368">Fare clic su **Aggiungi scene aperte** per aggiungere la scena corrente alle **scene nella compilazione**.</span><span class="sxs-lookup"><span data-stu-id="47f53-368">Click **Add Open Scenes** to add current scene to the **Scenes In Build**.</span></span>
* <span data-ttu-id="47f53-369">Fai clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="47f53-369">Click **Build**.</span></span>
* <span data-ttu-id="47f53-370">Creare una **nuova cartella** denominata "app".</span><span class="sxs-lookup"><span data-stu-id="47f53-370">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="47f53-371">Fare clic sulla cartella dell' **app** .</span><span class="sxs-lookup"><span data-stu-id="47f53-371">Single click the **App** folder.</span></span>
* <span data-ttu-id="47f53-372">Fare clic su **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="47f53-372">Click **Select Folder**.</span></span>
* <span data-ttu-id="47f53-373">Quando si esegue Unity, viene visualizzata una finestra Esplora file.</span><span class="sxs-lookup"><span data-stu-id="47f53-373">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="47f53-374">Aprire la cartella dell' **app** .</span><span class="sxs-lookup"><span data-stu-id="47f53-374">Open the **App** folder.</span></span>
* <span data-ttu-id="47f53-375">Fare doppio clic sul file della soluzione Visual Studio **YourSceneName. sln** .</span><span class="sxs-lookup"><span data-stu-id="47f53-375">Double click **YourSceneName.sln** Visual Studio Solution file.</span></span>
* <span data-ttu-id="47f53-376">Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione da debug a **Release** e da ARM a **x64**.</span><span class="sxs-lookup"><span data-stu-id="47f53-376">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X64**.</span></span>
* <span data-ttu-id="47f53-377">Fare clic sulla freccia a discesa accanto al pulsante dispositivo e selezionare **computer locale**.</span><span class="sxs-lookup"><span data-stu-id="47f53-377">Click on the drop-down arrow next to the Device button, and select **Local Machine**.</span></span>
* <span data-ttu-id="47f53-378">Fare clic su **debug-> avvia senza eseguire debug** nel menu o premere **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="47f53-378">Click **Debug -> Start Without debugging** in the menu or press **Ctrl + F5**.</span></span>

<span data-ttu-id="47f53-379">A questo punto l'app viene compilata e installata nel portale per la realtà mista.</span><span class="sxs-lookup"><span data-stu-id="47f53-379">Now the app is built and installed in Mixed Reality Portal.</span></span> <span data-ttu-id="47f53-380">È possibile riavviarlo tramite il menu Start nel portale per la realtà mista.</span><span class="sxs-lookup"><span data-stu-id="47f53-380">You can launch it again through Start menu in Mixed Reality Portal.</span></span>

## <a name="advanced-design---brush-tools-with-radial-layout"></a><span data-ttu-id="47f53-381">Strumenti di progettazione avanzati con layout radiale</span><span class="sxs-lookup"><span data-stu-id="47f53-381">Advanced design - Brush tools with radial layout</span></span>

![MixedReality213 principale](images/mr213-main-600px.jpg)

<span data-ttu-id="47f53-383">In questo capitolo verrà illustrato come sostituire il modello di controller di movimento predefinito con una raccolta di strumenti di pennelli personalizzati.</span><span class="sxs-lookup"><span data-stu-id="47f53-383">In this chapter, you will learn how to replace the default motion controller model with a custom brush tool collection.</span></span> <span data-ttu-id="47f53-384">Per informazioni di riferimento, è possibile trovare la scena completa **MixedReality213Advanced** nella cartella **Scenes** .</span><span class="sxs-lookup"><span data-stu-id="47f53-384">For your reference, you can find the completed scene **MixedReality213Advanced** under **Scenes** folder.</span></span>

### <a name="instructions"></a><span data-ttu-id="47f53-385">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="47f53-385">Instructions</span></span>

* <span data-ttu-id="47f53-386">Nel pannello **progetto** digitare **BrushSelector** nella casella di ricerca.</span><span class="sxs-lookup"><span data-stu-id="47f53-386">In the **Project** panel, type **BrushSelector** in the search box .</span></span> <span data-ttu-id="47f53-387">È possibile trovarlo anche in assets/AppPrefabs/</span><span class="sxs-lookup"><span data-stu-id="47f53-387">You can also find it under Assets/AppPrefabs/</span></span>
* <span data-ttu-id="47f53-388">Trascinare **BrushSelector** prefabbricate nel pannello **gerarchia** .</span><span class="sxs-lookup"><span data-stu-id="47f53-388">Drag the **BrushSelector** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="47f53-389">Per l'organizzazione, creare un GameObject vuoto denominato **pennelli**</span><span class="sxs-lookup"><span data-stu-id="47f53-389">For organization, create an empty GameObject called **Brushes**</span></span>
* <span data-ttu-id="47f53-390">Trascinare i prefabbricati seguenti dal pannello del **progetto** in **pennelli**</span><span class="sxs-lookup"><span data-stu-id="47f53-390">Drag following prefabs from the **Project** panel into **Brushes**</span></span>
    * <span data-ttu-id="47f53-391">Assets/AppPrefabs/**BrushFat**</span><span class="sxs-lookup"><span data-stu-id="47f53-391">Assets/AppPrefabs/**BrushFat**</span></span>
    * <span data-ttu-id="47f53-392">Assets/AppPrefabs/**BrushThin**</span><span class="sxs-lookup"><span data-stu-id="47f53-392">Assets/AppPrefabs/**BrushThin**</span></span>
    * <span data-ttu-id="47f53-393">Asset/AppPrefabs/**gomma**</span><span class="sxs-lookup"><span data-stu-id="47f53-393">Assets/AppPrefabs/**Eraser**</span></span>
    * <span data-ttu-id="47f53-394">Assets/AppPrefabs/**MarkerFat**</span><span class="sxs-lookup"><span data-stu-id="47f53-394">Assets/AppPrefabs/**MarkerFat**</span></span>
    * <span data-ttu-id="47f53-395">Assets/AppPrefabs/**MarkerThin**</span><span class="sxs-lookup"><span data-stu-id="47f53-395">Assets/AppPrefabs/**MarkerThin**</span></span>
    * <span data-ttu-id="47f53-396">Asset/AppPrefabs/**matita**</span><span class="sxs-lookup"><span data-stu-id="47f53-396">Assets/AppPrefabs/**Pencil**</span></span>

    ![Pennelli](images/mixedreality213-brushes-250px.png)

* <span data-ttu-id="47f53-398">Fare clic su **MotionControllers** prefabbricate nel pannello **gerarchia** .</span><span class="sxs-lookup"><span data-stu-id="47f53-398">Click **MotionControllers** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="47f53-399">Nel pannello **Inspector** deselezionare **Usa sempre il modello alternativo a destra** nel Visualizzatore del **controller di movimento**</span><span class="sxs-lookup"><span data-stu-id="47f53-399">In the **Inspector** panel, uncheck **Always Use Alternate Right Model** on the **Motion Controller Visualizer**</span></span>
* <span data-ttu-id="47f53-400">Nel pannello **gerarchia** fare clic su **BrushSelector**</span><span class="sxs-lookup"><span data-stu-id="47f53-400">In the **Hierarchy** panel, click **BrushSelector**</span></span>
* <span data-ttu-id="47f53-401">**BrushSelector** dispone di un campo denominato **ColorPicker**</span><span class="sxs-lookup"><span data-stu-id="47f53-401">**BrushSelector** has a field named **ColorPicker**</span></span>
* <span data-ttu-id="47f53-402">Dal pannello **gerarchia** trascinare il **ColorPickerWheel** nel campo **ColorPicker** nel pannello **Inspector** .</span><span class="sxs-lookup"><span data-stu-id="47f53-402">From the **Hierarchy** panel, drag the **ColorPickerWheel** into **ColorPicker** field in the **Inspector** panel.</span></span>

    ![Assegnare ColorPickerWheel al selettore di pennelli](images/mr213-brushselector-500px.jpg)

* <span data-ttu-id="47f53-404">Nel pannello **gerarchia** , in **BrushSelector** prefabbricate, selezionare l'oggetto **menu** .</span><span class="sxs-lookup"><span data-stu-id="47f53-404">In the **Hierarchy** panel, under **BrushSelector** prefab, select the **Menu** object.</span></span>
* <span data-ttu-id="47f53-405">Nel pannello **Inspector** , sotto il componente **LineObjectCollection** , aprire l'elenco a discesa **objects** Array.</span><span class="sxs-lookup"><span data-stu-id="47f53-405">In the **Inspector** panel, under the **LineObjectCollection** component, open the **Objects** array dropdown.</span></span> <span data-ttu-id="47f53-406">Vengono visualizzati 6 slot vuoti.</span><span class="sxs-lookup"><span data-stu-id="47f53-406">You will see 6 empty slots.</span></span>
* <span data-ttu-id="47f53-407">Dal pannello **gerarchia** trascinare ognuna delle prefabbricate con l'elemento padre nei **pennelli** GameObject in questi slot in qualsiasi ordine.</span><span class="sxs-lookup"><span data-stu-id="47f53-407">From the **Hierarchy** panel, drag each of the prefabs parented under the **Brushes** GameObject into these slots in any order.</span></span> <span data-ttu-id="47f53-408">Assicurarsi di trascinare le prefabbricati dalla scena, non i prefabbricati nella cartella del progetto.</span><span class="sxs-lookup"><span data-stu-id="47f53-408">(Make sure you're dragging the prefabs from the scene, not the prefabs in the project folder.)</span></span>

![Selettore di pennelli](images/mr213-brushselectorbrushes-700px.jpg)

<span data-ttu-id="47f53-410">**BrushSelector prefabbricato**</span><span class="sxs-lookup"><span data-stu-id="47f53-410">**BrushSelector prefab**</span></span>

<span data-ttu-id="47f53-411">Poiché **BrushSelector** eredita **AttachToController**, Mostra la **manualità** e le opzioni degli **elementi** nel pannello **Inspector** .</span><span class="sxs-lookup"><span data-stu-id="47f53-411">Since the **BrushSelector** inherits **AttachToController**, it shows **Handedness** and **Element** options in the **Inspector** panel.</span></span> <span data-ttu-id="47f53-412">È stato selezionato il pulsante **destro** del mouse e si fa **riferimento a pose** per associare gli strumenti del pennello al controller destro con la direzione</span><span class="sxs-lookup"><span data-stu-id="47f53-412">We selected **Right** and **Pointing Pose** to attach brush tools to the right hand controller with forward direction.</span></span>

<span data-ttu-id="47f53-413">**BrushSelector** utilizza due utilità:</span><span class="sxs-lookup"><span data-stu-id="47f53-413">The **BrushSelector** makes use of two utilities:</span></span>

* <span data-ttu-id="47f53-414">**Ellisse**: utilizzata per generare punti nello spazio lungo una forma ellisse.</span><span class="sxs-lookup"><span data-stu-id="47f53-414">**Ellipse**: used to generate points in space along an ellipse shape.</span></span>
* <span data-ttu-id="47f53-415">**LineObjectCollection**: distribuisce gli oggetti usando i punti generati da qualsiasi classe di riga (ad esempio, ellisse).</span><span class="sxs-lookup"><span data-stu-id="47f53-415">**LineObjectCollection**: distributes objects using the points generated by any Line class (eg, Ellipse).</span></span> <span data-ttu-id="47f53-416">Questo è ciò che verrà usato per inserire i pennelli lungo la forma ellisse.</span><span class="sxs-lookup"><span data-stu-id="47f53-416">This is what we'll be using to place our brushes along the Ellipse shape.</span></span>

<span data-ttu-id="47f53-417">In combinazione, è possibile usare queste utilità per creare un menu radiale.</span><span class="sxs-lookup"><span data-stu-id="47f53-417">When combined, these utilities can be used to create a radial menu.</span></span>

<span data-ttu-id="47f53-418">**Script LineObjectCollection**</span><span class="sxs-lookup"><span data-stu-id="47f53-418">**LineObjectCollection script**</span></span>

<span data-ttu-id="47f53-419">**LineObjectCollection** dispone di controlli per le dimensioni, la posizione e la rotazione degli oggetti distribuiti lungo la relativa riga.</span><span class="sxs-lookup"><span data-stu-id="47f53-419">**LineObjectCollection** has controls for the size, position and rotation of objects distributed along its line.</span></span> <span data-ttu-id="47f53-420">Questa operazione è utile per creare menu radiali come il selettore di pennelli.</span><span class="sxs-lookup"><span data-stu-id="47f53-420">This is useful for creating radial menus like the brush selector.</span></span> <span data-ttu-id="47f53-421">Per creare l'aspetto dei pennelli che aumentano da nulla quando si avvicinano alla posizione selezionata al centro, la curva **scalaogg** punta al centro e ai nastri in corrispondenza dei bordi.</span><span class="sxs-lookup"><span data-stu-id="47f53-421">To create the appearance of brushes that scale up from nothing as they approach the center selected position, the **ObjectScale** curve peaks in the center and tapers off at the edges.</span></span>

<span data-ttu-id="47f53-422">**Script BrushSelector**</span><span class="sxs-lookup"><span data-stu-id="47f53-422">**BrushSelector script**</span></span>

<span data-ttu-id="47f53-423">Nel caso di **BrushSelector**, è stato scelto di usare un'animazione procedurale.</span><span class="sxs-lookup"><span data-stu-id="47f53-423">In the case of the **BrushSelector**, we've chosen to use procedural animation.</span></span> <span data-ttu-id="47f53-424">In primo luogo, i modelli di pennelli vengono distribuiti in un'ellisse dallo script **LineObjectCollection** .</span><span class="sxs-lookup"><span data-stu-id="47f53-424">First, brush models are distributed in an ellipse by the **LineObjectCollection** script.</span></span> <span data-ttu-id="47f53-425">Quindi, ogni pennello è responsabile della gestione della propria posizione nella mano dell'utente in base al relativo valore **DisplayMode** , che cambia in base alla selezione.</span><span class="sxs-lookup"><span data-stu-id="47f53-425">Then, each brush is responsible for maintaining its position in the user's hand based on its **DisplayMode** value, which changes based on the selection.</span></span> <span data-ttu-id="47f53-426">È stato scelto un approccio procedurale a causa dell'elevata probabilità che le transizioni di posizione del pennello vengano interrotte quando l'utente seleziona pennelli.</span><span class="sxs-lookup"><span data-stu-id="47f53-426">We chose a procedural approach because of the high probability of brush position transitions being interrupted as the user selects brushes.</span></span> <span data-ttu-id="47f53-427">Le animazioni Mecanim possono gestire le interruzioni normalmente, ma tendono a essere più complesse rispetto a una semplice operazione Lerp.</span><span class="sxs-lookup"><span data-stu-id="47f53-427">Mecanim animations can handle interruptions gracefully, but it tends to be more complicated than a simple Lerp operation.</span></span>

<span data-ttu-id="47f53-428">**BrushSelector** usa una combinazione di entrambi.</span><span class="sxs-lookup"><span data-stu-id="47f53-428">**BrushSelector** uses a combination of both.</span></span> <span data-ttu-id="47f53-429">Quando viene rilevato un input del touchpad, le opzioni del pennello diventano visibili e aumentano di livello lungo il menu radiale.</span><span class="sxs-lookup"><span data-stu-id="47f53-429">When touchpad input is detected, brush options become visible and scale up along the radial menu.</span></span> <span data-ttu-id="47f53-430">Dopo un periodo di timeout (che indica che l'utente ha effettuato una selezione), le opzioni del pennello diminuiscono di nuovo, lasciando solo il pennello selezionato.</span><span class="sxs-lookup"><span data-stu-id="47f53-430">After a timeout period (which indicates that the user has made a selection) the brush options scale down again, leaving only the selected brush.</span></span>

<span data-ttu-id="47f53-431">**Visualizzazione dell'input di touchpad**</span><span class="sxs-lookup"><span data-stu-id="47f53-431">**Visualizing touchpad input**</span></span>

<span data-ttu-id="47f53-432">Anche nei casi in cui il modello di controller è stato completamente sostituito, può essere utile visualizzare l'input sugli input del modello originale.</span><span class="sxs-lookup"><span data-stu-id="47f53-432">Even in cases where the controller model has been completely replaced, it can be helpful to show input on the original model inputs.</span></span> <span data-ttu-id="47f53-433">In questo modo, le azioni dell'utente vengono instradate in realtà.</span><span class="sxs-lookup"><span data-stu-id="47f53-433">This helps to ground the user's actions in reality.</span></span> <span data-ttu-id="47f53-434">Per il **BrushSelector** è stato scelto di rendere il touchpad brevemente visibile quando viene ricevuto l'input.</span><span class="sxs-lookup"><span data-stu-id="47f53-434">For the **BrushSelector** we've chosen to make the touchpad briefly visible when the input is received.</span></span> <span data-ttu-id="47f53-435">Questa operazione è stata eseguita recuperando l'elemento touchpad dal controller, sostituendo il materiale con un materiale personalizzato, quindi applicando una sfumatura al colore del materiale basato sull'ultima volta in cui è stato ricevuto l'input del touchpad.</span><span class="sxs-lookup"><span data-stu-id="47f53-435">This was done by retrieving the Touchpad element from the controller, replacing its material with a custom material, then applying a gradient to that material's color based on the last time touchpad input was received.</span></span>

```cs
protected override void OnAttachToController()
{
    // Turn off the default controller's renderers
    controller.SetRenderersVisible(false);

    // Get the touchpad and assign our custom material to it
    Transform touchpad;
    if (controller.TryGetElement(MotionControllerInfo.ControllerElementEnum.Touchpad, out touchpad))
    {
        touchpadRenderer = touchpad.GetComponentInChildren<MeshRenderer>();
        originalTouchpadMaterial = touchpadRenderer.material;
        touchpadRenderer.material = touchpadMaterial;
        touchpadRenderer.enabled = true;
    }

    // Subscribe to input now that we're parented under the controller
    InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
}

private void Update()
{
    ...
    // Update our touchpad material
    Color glowColor = touchpadColor.Evaluate((Time.unscaledTime - touchpadTouchTime) / touchpadGlowLossTime);
    touchpadMaterial.SetColor("_EmissionColor", glowColor);
    touchpadMaterial.SetColor("_Color", glowColor);
    ...
}
```

<span data-ttu-id="47f53-436">**Selezione dello strumento pennello con input touchpad**</span><span class="sxs-lookup"><span data-stu-id="47f53-436">**Brush tool selection with touchpad input**</span></span>

<span data-ttu-id="47f53-437">Quando il selettore di pennelli rileva l'input premuto del touchpad, controlla la posizione dell'input per determinare se si trovava a sinistra o a destra.</span><span class="sxs-lookup"><span data-stu-id="47f53-437">When the brush selector detects touchpad's pressed input, it checks the position of the input to determine if it was to the left or right.</span></span>

<span data-ttu-id="47f53-438">**Spessore tratto con selectPressedAmount**</span><span class="sxs-lookup"><span data-stu-id="47f53-438">**Stroke thickness with selectPressedAmount**</span></span>

<span data-ttu-id="47f53-439">Anziché l'evento **InteractionSourcePressType. Select** in **InteractionSourcePressed ()** , è possibile ottenere il valore analogo della quantità premuta tramite **selectPressedAmount**.</span><span class="sxs-lookup"><span data-stu-id="47f53-439">Instead of the **InteractionSourcePressType.Select** event in the **InteractionSourcePressed()**, you can get the analog value of the pressed amount through **selectPressedAmount**.</span></span> <span data-ttu-id="47f53-440">Questo valore può essere recuperato in **InteractionSourceUpdated ()** .</span><span class="sxs-lookup"><span data-stu-id="47f53-440">This value can be retrieved in **InteractionSourceUpdated()**.</span></span>

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness)
    {
        if (obj.state.touchpadPressed)
        {
            // Check which side we clicked
            if (obj.state.touchpadPosition.x < 0)
            {
                currentAction = SwipeEnum.Left;
            }
            else
            {
                currentAction = SwipeEnum.Right;
            }

            // Ping the touchpad material so it gets bright
            touchpadTouchTime = Time.unscaledTime;
        }

        if (activeBrush != null)
        {
            // If the pressed amount is greater than our threshold, draw
            if (obj.state.selectPressedAmount >= selectPressedDrawThreshold)
            {
                activeBrush.Draw = true;
                activeBrush.Width = ProcessSelectPressedAmount(obj.state.selectPressedAmount);
            }
            else
            {
                // Otherwise, stop drawing
                activeBrush.Draw = false;
                selectPressedSmooth = 0f;
            }
        }
    }
}
```

<span data-ttu-id="47f53-441">**Script di gomma**</span><span class="sxs-lookup"><span data-stu-id="47f53-441">**Eraser script**</span></span>

<span data-ttu-id="47f53-442">**Eraser** è un tipo speciale di pennello che esegue l'override della funzione **DrawOverTime ()** del **pennello**di base.</span><span class="sxs-lookup"><span data-stu-id="47f53-442">**Eraser** is a special type of brush that overrides the base **Brush**'s **DrawOverTime()** function.</span></span> <span data-ttu-id="47f53-443">Mentre il disegno è true, la gomma viene controllata per verificare se il suggerimento si interseca con eventuali tratti di pennelli esistenti.</span><span class="sxs-lookup"><span data-stu-id="47f53-443">While Draw is true, the eraser checks to see if its tip intersects with any existing brush strokes.</span></span> <span data-ttu-id="47f53-444">In tal caso, vengono aggiunti a una coda per la compattazione e l'eliminazione.</span><span class="sxs-lookup"><span data-stu-id="47f53-444">If it does, they are added to a queue to be shrunk down and deleted.</span></span>

## <a name="advanced-design---teleportation-and-locomotion"></a><span data-ttu-id="47f53-445">Progettazione avanzata: teleporte e locomozione</span><span class="sxs-lookup"><span data-stu-id="47f53-445">Advanced design - Teleportation and locomotion</span></span>

<span data-ttu-id="47f53-446">Se si vuole consentire all'utente di spostarsi nella scena con la teleportazione con levetta, usare **MixedRealityCameraParent** anziché **MixedRealityCamera**.</span><span class="sxs-lookup"><span data-stu-id="47f53-446">If you want to allow the user to move around the scene with teleportation using thumbstick, use **MixedRealityCameraParent** instead of **MixedRealityCamera**.</span></span> <span data-ttu-id="47f53-447">È anche necessario aggiungere **InputManager** e **DefaultCursor**.</span><span class="sxs-lookup"><span data-stu-id="47f53-447">You also need to add **InputManager** and **DefaultCursor**.</span></span> <span data-ttu-id="47f53-448">Poiché **MixedRealityCameraParent** include già **MotionControllers** e **Boundary** come componenti figlio, è necessario rimuovere i prefabbricati **MotionControllers** e **Environment** esistenti.</span><span class="sxs-lookup"><span data-stu-id="47f53-448">Since **MixedRealityCameraParent** already includes **MotionControllers** and **Boundary** as child components, you should remove existing **MotionControllers** and **Environment** prefab.</span></span>

### <a name="instructions"></a><span data-ttu-id="47f53-449">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="47f53-449">Instructions</span></span>

* <span data-ttu-id="47f53-450">Nel pannello **gerarchia** eliminare **MixedRealityCamera**, **Environment** e **MotionControllers**</span><span class="sxs-lookup"><span data-stu-id="47f53-450">In the **Hierarchy** panel, delete **MixedRealityCamera**, **Environment** and **MotionControllers**</span></span>
* <span data-ttu-id="47f53-451">Dal **pannello progetto**, cercare e trascinare le seguenti prefabbricati nel pannello **gerarchia** :</span><span class="sxs-lookup"><span data-stu-id="47f53-451">From the **Project panel**, search and drag the following prefabs into the **Hierarchy** panel:</span></span>
    * <span data-ttu-id="47f53-452">Assets/AppPrefabs/input/prefabbricates/**MixedRealityCameraParent**</span><span class="sxs-lookup"><span data-stu-id="47f53-452">Assets/AppPrefabs/Input/Prefabs/**MixedRealityCameraParent**</span></span>
    * <span data-ttu-id="47f53-453">Assets/AppPrefabs/input/prefabbricates/**InputManager**</span><span class="sxs-lookup"><span data-stu-id="47f53-453">Assets/AppPrefabs/Input/Prefabs/**InputManager**</span></span>
    * <span data-ttu-id="47f53-454">Assets/AppPrefabs/input/prefabrics/Cursor/**DefaultCursor**</span><span class="sxs-lookup"><span data-stu-id="47f53-454">Assets/AppPrefabs/Input/Prefabs/Cursor/**DefaultCursor**</span></span>

    ![Padre della fotocamera della realtà mista](images/mr213-cameraparent-300px.png)

* <span data-ttu-id="47f53-456">Nel pannello **gerarchia** fare clic su **Gestione input** .</span><span class="sxs-lookup"><span data-stu-id="47f53-456">In the **Hierarchy** panel, click **Input Manager**</span></span>
* <span data-ttu-id="47f53-457">Nel pannello **Inspector** scorrere verso il basso fino alla sezione **semplice selettore puntatore singolo**</span><span class="sxs-lookup"><span data-stu-id="47f53-457">In the **Inspector** panel, scroll down to the **Simple Single Pointer Selector** section</span></span>
* <span data-ttu-id="47f53-458">Dal pannello **gerarchia** trascinare **DefaultCursor** in campo **cursore**</span><span class="sxs-lookup"><span data-stu-id="47f53-458">From the **Hierarchy** panel, drag **DefaultCursor** into **Cursor** field</span></span>

    ![Assegnazione di DefaultCursor](images/mr213-defaultcursor-500px.png)

* <span data-ttu-id="47f53-460">**Salva** la scena e fai clic sul pulsante **Riproduci** .</span><span class="sxs-lookup"><span data-stu-id="47f53-460">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="47f53-461">Sarà possibile usare levetta per ruotare verso sinistra o verso destra o Teleport.</span><span class="sxs-lookup"><span data-stu-id="47f53-461">You will be able to use the thumbstick to rotate left/right or teleport.</span></span>

## <a name="the-end"></a><span data-ttu-id="47f53-462">La fine</span><span class="sxs-lookup"><span data-stu-id="47f53-462">The end</span></span>

<span data-ttu-id="47f53-463">Questa è la fine di questa esercitazione.</span><span class="sxs-lookup"><span data-stu-id="47f53-463">And that's the end of this tutorial!</span></span> <span data-ttu-id="47f53-464">Si è appreso quanto segue:</span><span class="sxs-lookup"><span data-stu-id="47f53-464">You learned:</span></span>

* <span data-ttu-id="47f53-465">Come usare i modelli di motion controller in modalità di gioco e runtime di Unity.</span><span class="sxs-lookup"><span data-stu-id="47f53-465">How to work with motion controller models in Unity's game mode and runtime.</span></span>
* <span data-ttu-id="47f53-466">Come usare tipi diversi di eventi dei pulsanti e le relative applicazioni.</span><span class="sxs-lookup"><span data-stu-id="47f53-466">How to use different types of button events and their applications.</span></span>
* <span data-ttu-id="47f53-467">Come sovrapporre gli elementi dell'interfaccia utente all'inizio del controller o personalizzarlo completamente.</span><span class="sxs-lookup"><span data-stu-id="47f53-467">How to overlay UI elements on top of the controller or fully customize it.</span></span>

<span data-ttu-id="47f53-468">A questo punto è possibile iniziare a creare un'esperienza immersiva con i controller di movimento.</span><span class="sxs-lookup"><span data-stu-id="47f53-468">You are now ready to start creating your own immersive experience with motion controllers!</span></span>

## <a name="completed-scenes"></a><span data-ttu-id="47f53-469">Scene completate</span><span class="sxs-lookup"><span data-stu-id="47f53-469">Completed scenes</span></span>

* <span data-ttu-id="47f53-470">Nel pannello del **progetto** di Unity fare clic sulla cartella **Scenes** .</span><span class="sxs-lookup"><span data-stu-id="47f53-470">In Unity's **Project** panel click on the **Scenes** folder.</span></span>
* <span data-ttu-id="47f53-471">Sono disponibili due scene Unity **MixedReality213** e **MixedReality213Advanced**.</span><span class="sxs-lookup"><span data-stu-id="47f53-471">You will find two Unity scenes **MixedReality213** and **MixedReality213Advanced**.</span></span>
    * <span data-ttu-id="47f53-472">**MixedReality213**: scena completata con pennello singolo</span><span class="sxs-lookup"><span data-stu-id="47f53-472">**MixedReality213**: Completed scene with single brush</span></span>
    * <span data-ttu-id="47f53-473">**MixedReality213Advanced**: sequenza completa con più pennelli con l'esempio di pressione del pulsante di selezione</span><span class="sxs-lookup"><span data-stu-id="47f53-473">**MixedReality213Advanced**: Completed scene with multiple brush with select button's press amount example</span></span>

## <a name="see-also"></a><span data-ttu-id="47f53-474">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="47f53-474">See also</span></span>

* [<span data-ttu-id="47f53-475">File di progetto MR input 213</span><span class="sxs-lookup"><span data-stu-id="47f53-475">MR Input 213 project files</span></span>](https://github.com/Microsoft/MixedReality213)
* [<span data-ttu-id="47f53-476">Toolkit di realtà mista-scena di test del controller di movimento</span><span class="sxs-lookup"><span data-stu-id="47f53-476">Mixed Reality Toolkit - Motion Controller Test scene</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [<span data-ttu-id="47f53-477">Toolkit per realtà mista-meccanismi di recupero</span><span class="sxs-lookup"><span data-stu-id="47f53-477">Mixed Reality Toolkit - Grab Mechanics</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [<span data-ttu-id="47f53-478">Linee guida per lo sviluppo di controller di movimento</span><span class="sxs-lookup"><span data-stu-id="47f53-478">Motion controller development guidelines</span></span>](motion-controllers.md)

---
title: Input MR 213
description: Seguire questa esercitazione di scrittura del codice grazie a Unity, Visual Studio e auricolari coinvolgenti per informazioni dettagliate sui controller di movimento.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, coinvolgenti, movimento controller, academy, esercitazione
ms.openlocfilehash: 85449795a4fb3d182101cb5b4c4ce3fe85b009c0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604700"
---
>[!NOTE]
><span data-ttu-id="b9369-104">Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.</span><span class="sxs-lookup"><span data-stu-id="b9369-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="b9369-105">Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.</span><span class="sxs-lookup"><span data-stu-id="b9369-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="b9369-106">Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.</span><span class="sxs-lookup"><span data-stu-id="b9369-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="b9369-107">Essi verranno mantenute per continuare a utilizzare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="b9369-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="b9369-108">Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b9369-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="b9369-109">Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.</span><span class="sxs-lookup"><span data-stu-id="b9369-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-input-213-motion-controllers"></a><span data-ttu-id="b9369-110">Input di MR 213: Controller di movimento</span><span class="sxs-lookup"><span data-stu-id="b9369-110">MR Input 213: Motion controllers</span></span>

<span data-ttu-id="b9369-111">I controller di movimento in tutto il mondo delle realtà mista aggiungono un ulteriore livello di interattività.</span><span class="sxs-lookup"><span data-stu-id="b9369-111">Motion controllers in the mixed reality world add another level of interactivity.</span></span> <span data-ttu-id="b9369-112">Con [controller di movimento](motion-controllers.md), possiamo direttamente interagire con gli oggetti in modo più naturale, simile alle interazioni fisiche in uno scenario reale, l'aumento di full immersion e maggiori opportunità di sorprendere durante l'utilizzo di app.</span><span class="sxs-lookup"><span data-stu-id="b9369-112">With [motion controllers](motion-controllers.md), we can directly interact with objects in a more natural way, similar to our physical interactions in real life, increasing immersion and delight in your app experience.</span></span>

<span data-ttu-id="b9369-113">MR 213 Input, verrà illustra gli eventi di input del movimento controller tramite la creazione di un'esperienza semplice disegno spaziale.</span><span class="sxs-lookup"><span data-stu-id="b9369-113">In MR Input 213, we will explore the motion controller's input events by creating a simple spatial painting experience.</span></span> <span data-ttu-id="b9369-114">Con questa app, gli utenti possono disegnare nello spazio tridimensionale con vari tipi di pennelli e i colori.</span><span class="sxs-lookup"><span data-stu-id="b9369-114">With this app, users can paint in three-dimensional space with various types of brushes and colors.</span></span>

## <a name="topics-covered-in-this-tutorial"></a><span data-ttu-id="b9369-115">Argomenti trattati in questa esercitazione</span><span class="sxs-lookup"><span data-stu-id="b9369-115">Topics covered in this tutorial</span></span>

|![MixedReality213 Topic1](images/mr213-topic1.png)|![MixedReality213 Topic2](images/mr213-topic2.png)|![MixedReality213 Topic3](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|<span data-ttu-id="b9369-119">**Visualizzazione controller**</span><span class="sxs-lookup"><span data-stu-id="b9369-119">**Controller visualization**</span></span>|<span data-ttu-id="b9369-120">**Eventi di input controller**</span><span class="sxs-lookup"><span data-stu-id="b9369-120">**Controller input events**</span></span>|<span data-ttu-id="b9369-121">**Controller personalizzato e l'interfaccia utente**</span><span class="sxs-lookup"><span data-stu-id="b9369-121">**Custom controller and UI**</span></span>|
|<span data-ttu-id="b9369-122">Informazioni su come eseguire il rendering di modelli di controller di movimento in modalità di gioco Unity e runtime.</span><span class="sxs-lookup"><span data-stu-id="b9369-122">Learn how to render motion controller models in Unity's game mode and runtime.</span></span>|<span data-ttu-id="b9369-123">Comprendere i diversi tipi di eventi del pulsante e le relative applicazioni.</span><span class="sxs-lookup"><span data-stu-id="b9369-123">Understand different types of button events and their applications.</span></span>|<span data-ttu-id="b9369-124">Informazioni su come sovrimpressione elementi dell'interfaccia utente nella parte superiore del controller o completamente personalizzarlo.</span><span class="sxs-lookup"><span data-stu-id="b9369-124">Learn how to overlay UI elements on top of the controller or fully customize it.</span></span>|

## <a name="device-support"></a><span data-ttu-id="b9369-125">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="b9369-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="b9369-126">Corso</span><span class="sxs-lookup"><span data-stu-id="b9369-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="b9369-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="b9369-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="b9369-128"><a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></span><span class="sxs-lookup"><span data-stu-id="b9369-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="b9369-129">Input di MR 213: Controller di movimento</span><span class="sxs-lookup"><span data-stu-id="b9369-129">MR Input 213: Motion controllers</span></span></td><td style="text-align: center;"> </td><td style="text-align: center;"> <span data-ttu-id="b9369-130">✔️</span><span class="sxs-lookup"><span data-stu-id="b9369-130">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="b9369-131">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="b9369-131">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="b9369-132">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="b9369-132">Prerequisites</span></span>

<span data-ttu-id="b9369-133">Vedere l'elenco di controllo di installazione per auricolari immersive sul [questa pagina](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="b9369-133">See the installation checklist for immersive headsets on [this page](install-the-tools.md).</span></span>

* <span data-ttu-id="b9369-134">Questa esercitazione richiede [2017.2.1p2 Unity](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)</span><span class="sxs-lookup"><span data-stu-id="b9369-134">This tutorial requires [Unity 2017.2.1p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)</span></span>

### <a name="project-files"></a><span data-ttu-id="b9369-135">File di progetto</span><span class="sxs-lookup"><span data-stu-id="b9369-135">Project files</span></span>

* <span data-ttu-id="b9369-136">[Scaricare i file](https://github.com/Microsoft/MixedReality213/archive/master.zip) necessarie per il progetto ed estrarre i file sul desktop.</span><span class="sxs-lookup"><span data-stu-id="b9369-136">[Download the files](https://github.com/Microsoft/MixedReality213/archive/master.zip) required by the project and extract the files to the Desktop.</span></span>

>[!NOTE]
><span data-ttu-id="b9369-137">Se si desidera esaminare il codice sorgente prima di scaricare, ha [disponibile in GitHub](https://github.com/Microsoft/MixedReality213).</span><span class="sxs-lookup"><span data-stu-id="b9369-137">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/MixedReality213).</span></span>

## <a name="unity-setup"></a><span data-ttu-id="b9369-138">Programma di installazione di Unity</span><span class="sxs-lookup"><span data-stu-id="b9369-138">Unity setup</span></span>

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a><span data-ttu-id="b9369-139">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="b9369-139">Objectives</span></span>

* <span data-ttu-id="b9369-140">Ottimizzare lo sviluppo di Unity per realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="b9369-140">Optimize Unity for Windows Mixed Reality development</span></span>
* <span data-ttu-id="b9369-141">Il programma di installazione realtà mista fotocamera</span><span class="sxs-lookup"><span data-stu-id="b9369-141">Setup Mixed Reality Camera</span></span>
* <span data-ttu-id="b9369-142">Configurare l'ambiente</span><span class="sxs-lookup"><span data-stu-id="b9369-142">Setup environment</span></span>

### <a name="instructions"></a><span data-ttu-id="b9369-143">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="b9369-143">Instructions</span></span>

* <span data-ttu-id="b9369-144">Avviare Unity.</span><span class="sxs-lookup"><span data-stu-id="b9369-144">Start Unity.</span></span>
* <span data-ttu-id="b9369-145">Selezionare **aperto**.</span><span class="sxs-lookup"><span data-stu-id="b9369-145">Select **Open**.</span></span>
* <span data-ttu-id="b9369-146">Passare al Desktop e trovare il **MixedReality213-master** cartella precedentemente non archiviati.</span><span class="sxs-lookup"><span data-stu-id="b9369-146">Navigate to your Desktop and find the **MixedReality213-master** folder you previously unarchived.</span></span>
* <span data-ttu-id="b9369-147">Fare clic su **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="b9369-147">Click **Select Folder**.</span></span>
* <span data-ttu-id="b9369-148">Una volta Unity ha terminato di caricare i file di progetto, sarà possibile visualizzare l'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="b9369-148">Once Unity finishes loading project files, you will be able to see Unity editor.</span></span>
* <span data-ttu-id="b9369-149">In Unity, selezionare **File > Build Settings**.</span><span class="sxs-lookup"><span data-stu-id="b9369-149">In Unity, select **File > Build Settings**.</span></span>

![MR213_BuildSettings](images/mr213-buildsettings-450px.png)
* <span data-ttu-id="b9369-151">Selezionare **Universal Windows Platform** nel **piattaforma** elenco e fare clic sui **commutatore piattaforma** pulsante.</span><span class="sxs-lookup"><span data-stu-id="b9369-151">Select **Universal Windows Platform** in the **Platform** list and click the **Switch Platform** button.</span></span>
* <span data-ttu-id="b9369-152">Impostare il dispositivo di destinazione **qualsiasi dispositivo**</span><span class="sxs-lookup"><span data-stu-id="b9369-152">Set Target Device to **Any device**</span></span>
* <span data-ttu-id="b9369-153">Impostare il tipo di compilazione su **D3D**</span><span class="sxs-lookup"><span data-stu-id="b9369-153">Set Build Type to **D3D**</span></span>
* <span data-ttu-id="b9369-154">Impostare SDK su **installata più recente**</span><span class="sxs-lookup"><span data-stu-id="b9369-154">Set SDK to **Latest Installed**</span></span>
* <span data-ttu-id="b9369-155">Controllare **Unity C# progetti**</span><span class="sxs-lookup"><span data-stu-id="b9369-155">Check **Unity C# Projects**</span></span>
    * <span data-ttu-id="b9369-156">Ciò permette di che modificare i file di script nel progetto di Visual Studio senza ricompilare il progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="b9369-156">This allows you modify script files in the Visual Studio project without rebuilding Unity project.</span></span>
* <span data-ttu-id="b9369-157">Fare clic su **le impostazioni del giocatore**.</span><span class="sxs-lookup"><span data-stu-id="b9369-157">Click **Player Settings**.</span></span>
* <span data-ttu-id="b9369-158">Nel **Inspector** pannello, scorrere fino alla parte inferiore</span><span class="sxs-lookup"><span data-stu-id="b9369-158">In the **Inspector** panel, scroll down to the bottom</span></span>
* <span data-ttu-id="b9369-159">XR impostazioni controllare **supportato di realtà virtuale**</span><span class="sxs-lookup"><span data-stu-id="b9369-159">In XR Settings, check **Virtual Reality Supported**</span></span>
* <span data-ttu-id="b9369-160">Nel SDK di realtà virtuale, selezionare **realtà mista di Windows**</span><span class="sxs-lookup"><span data-stu-id="b9369-160">Under Virtual Reality SDKs, select **Windows Mixed Reality**</span></span>

![MR213_XRSettings](images/mr213-xrsettings-500px.png)
* <span data-ttu-id="b9369-162">Chiusura **Build Settings** finestra.</span><span class="sxs-lookup"><span data-stu-id="b9369-162">Close **Build Settings** window.</span></span>

### <a name="project-structure"></a><span data-ttu-id="b9369-163">Struttura del progetto</span><span class="sxs-lookup"><span data-stu-id="b9369-163">Project structure</span></span>

<span data-ttu-id="b9369-164">Questa esercitazione viene usato  **[Toolkit di realtà mista - Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)**.</span><span class="sxs-lookup"><span data-stu-id="b9369-164">This tutorial uses **[Mixed Reality Toolkit - Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)**.</span></span> <span data-ttu-id="b9369-165">È possibile trovare le versioni sul [questa pagina](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).</span><span class="sxs-lookup"><span data-stu-id="b9369-165">You can find the releases on [this page](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).</span></span>

![ProjectStructure](images/mr213-projectstructure-650px.png)

<span data-ttu-id="b9369-167">**Scene completate per riferimento**</span><span class="sxs-lookup"><span data-stu-id="b9369-167">**Completed scenes for your reference**</span></span>
* <span data-ttu-id="b9369-168">Si troveranno due scene Unity completate sotto **scene** cartella.</span><span class="sxs-lookup"><span data-stu-id="b9369-168">You will find two completed Unity scenes under **Scenes** folder.</span></span>
    * <span data-ttu-id="b9369-169">**MixedReality213**: Completato scena con pennello singolo</span><span class="sxs-lookup"><span data-stu-id="b9369-169">**MixedReality213**: Completed scene with single brush</span></span>
    * <span data-ttu-id="b9369-170">**MixedReality213Advanced**: Completato scena per progettazione avanzata con più pennelli</span><span class="sxs-lookup"><span data-stu-id="b9369-170">**MixedReality213Advanced**: Completed scene for advanced design with multiple brushes</span></span>

<span data-ttu-id="b9369-171">**Nuova scena il programma di installazione per l'esercitazione**</span><span class="sxs-lookup"><span data-stu-id="b9369-171">**New Scene setup for the tutorial**</span></span>
* <span data-ttu-id="b9369-172">In Unity, fare clic su **File > nuova scena**</span><span class="sxs-lookup"><span data-stu-id="b9369-172">In Unity, click **File > New Scene**</span></span>
* <span data-ttu-id="b9369-173">Eliminare **fotocamera principale** e **luce direzionale**</span><span class="sxs-lookup"><span data-stu-id="b9369-173">Delete **Main Camera** and **Directional Light**</span></span>
* <span data-ttu-id="b9369-174">Dal **pannello progetto**, la ricerca e trascinare il prefabs seguenti nel **gerarchia** pannello:</span><span class="sxs-lookup"><span data-stu-id="b9369-174">From the **Project panel**, search and drag the following prefabs into the **Hierarchy** panel:</span></span>
    * <span data-ttu-id="b9369-175">Assets/HoloToolkit/Input/Prefabs/**MixedRealityCamera**</span><span class="sxs-lookup"><span data-stu-id="b9369-175">Assets/HoloToolkit/Input/Prefabs/**MixedRealityCamera**</span></span>
    * <span data-ttu-id="b9369-176">Assets/AppPrefabs/**Environment**</span><span class="sxs-lookup"><span data-stu-id="b9369-176">Assets/AppPrefabs/**Environment**</span></span>

![Fotocamere e ambiente](images/mr213-cameraenvironment-300px.jpg)
* <span data-ttu-id="b9369-178">Esistono due prefabs fotocamera nel Toolkit di realtà mista:</span><span class="sxs-lookup"><span data-stu-id="b9369-178">There are two camera prefabs in Mixed Reality Toolkit:</span></span>
    * <span data-ttu-id="b9369-179">**MixedRealityCamera.prefab**: Solo della fotocamera</span><span class="sxs-lookup"><span data-stu-id="b9369-179">**MixedRealityCamera.prefab**: Camera only</span></span>
    * <span data-ttu-id="b9369-180">**MixedRealityCameraParent.prefab**: Fotocamera + teletrasporto + limite</span><span class="sxs-lookup"><span data-stu-id="b9369-180">**MixedRealityCameraParent.prefab**: Camera + Teleportation + Boundary</span></span>
    * <span data-ttu-id="b9369-181">In questa esercitazione si userà **MixedRealityCamera** senza teletrasporto funzionalità.</span><span class="sxs-lookup"><span data-stu-id="b9369-181">In this tutorial, we will use **MixedRealityCamera** without teleportation feature.</span></span> <span data-ttu-id="b9369-182">Per questo motivo, abbiamo aggiunto semplice **ambiente** prefab che contiene un piano di base per rendere l'utente ritiene terra.</span><span class="sxs-lookup"><span data-stu-id="b9369-182">Because of this, we added simple **Environment** prefab which contains a basic floor to make the user feel grounded.</span></span>
    * <span data-ttu-id="b9369-183">Per altre informazioni su con il teletrasporto **MixedRealityCameraParent**, vedere [Advanced design - teletrasporto e locomotion](#advanced-design---teleportation-and-locomotion)</span><span class="sxs-lookup"><span data-stu-id="b9369-183">To learn more about the teleportation with **MixedRealityCameraParent**, see [Advanced design - Teleportation and locomotion](#advanced-design---teleportation-and-locomotion)</span></span>

<span data-ttu-id="b9369-184">**Programma di installazione skybox**</span><span class="sxs-lookup"><span data-stu-id="b9369-184">**Skybox setup**</span></span>
* <span data-ttu-id="b9369-185">Fare clic su **finestra > illuminazione > Impostazioni**</span><span class="sxs-lookup"><span data-stu-id="b9369-185">Click **Window > Lighting > Settings**</span></span>
* <span data-ttu-id="b9369-186">Fare clic sul cerchio sul lato destro del **campo Skybox materiale**</span><span class="sxs-lookup"><span data-stu-id="b9369-186">Click the circle on the right side of the **Skybox Material field**</span></span>
* <span data-ttu-id="b9369-187">Digitare "gray" e selezionare **SkyboxGray**</span><span class="sxs-lookup"><span data-stu-id="b9369-187">Type in ‘gray’ and select **SkyboxGray**</span></span>

<span data-ttu-id="b9369-188">(Assets/AppPrefabs/Support/Materials/SkyboxGray.mat)</span><span class="sxs-lookup"><span data-stu-id="b9369-188">(Assets/AppPrefabs/Support/Materials/SkyboxGray.mat)</span></span>

![Impostazione skybox](images/mr123-skyboxsetting-400px.jpg)
* <span data-ttu-id="b9369-190">Controllare **Skybox** possibilità di essere in grado di vedere assegnato skybox della sfumatura di colore grigio</span><span class="sxs-lookup"><span data-stu-id="b9369-190">Check **Skybox** option to be able to see assigned gray gradient skybox</span></span>

![Attiva/Disattiva skybox opzione](images/mr213-skyboxcheck-400px.jpg)
* <span data-ttu-id="b9369-192">La scena con MixedRealityCamera, ambiente e skybox grigio avrà un aspetto simile al seguente.</span><span class="sxs-lookup"><span data-stu-id="b9369-192">The scene with MixedRealityCamera, Environment and gray skybox will look like this.</span></span>

![Ambiente MixedReality213](images/mr213-environment-600px.jpg)
* <span data-ttu-id="b9369-194">Fare clic su **File > Salva scena come**</span><span class="sxs-lookup"><span data-stu-id="b9369-194">Click **File > Save Scene as**</span></span>
* <span data-ttu-id="b9369-195">**Salvare** scena nella cartella di scene con qualsiasi nome</span><span class="sxs-lookup"><span data-stu-id="b9369-195">**Save** your scene under Scenes folder with any name</span></span>

## <a name="chapter-1---controller-visualization"></a><span data-ttu-id="b9369-196">Capitolo 1 - visualizzazione Controller</span><span class="sxs-lookup"><span data-stu-id="b9369-196">Chapter 1 - Controller visualization</span></span>

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a><span data-ttu-id="b9369-197">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="b9369-197">Objectives</span></span>

* <span data-ttu-id="b9369-198">Informazioni su come eseguire il rendering di modelli di controller in modalità di gioco Unity e in fase di esecuzione di movimento.</span><span class="sxs-lookup"><span data-stu-id="b9369-198">Learn how to render motion controller models in Unity's game mode and at runtime.</span></span>

<span data-ttu-id="b9369-199">Realtà mista di Windows fornisce un modello animato controller per la visualizzazione di controller.</span><span class="sxs-lookup"><span data-stu-id="b9369-199">Windows Mixed Reality provides an animated controller model for controller visualization.</span></span> <span data-ttu-id="b9369-200">Esistono diversi approcci per la visualizzazione controller nell'app:</span><span class="sxs-lookup"><span data-stu-id="b9369-200">There are several approaches you can take for controller visualization in your app:</span></span>
* <span data-ttu-id="b9369-201">Default - tramite il controller predefinito senza modifiche</span><span class="sxs-lookup"><span data-stu-id="b9369-201">Default - Using default controller without modification</span></span>
* <span data-ttu-id="b9369-202">Ibrido - usando controller predefinito, ma la personalizzazione di alcuni dei suoi elementi o la sovrapposizione di componenti dell'interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="b9369-202">Hybrid - Using default controller, but customizing some of its elements or overlaying UI components</span></span>
* <span data-ttu-id="b9369-203">Sostituzione - usare il proprio personalizzato un modello 3D per il controller</span><span class="sxs-lookup"><span data-stu-id="b9369-203">Replacement - Using your own customized 3D model for the controller</span></span>

<span data-ttu-id="b9369-204">In questo capitolo, si apprenderanno informazioni sugli esempi di queste personalizzazioni di controller.</span><span class="sxs-lookup"><span data-stu-id="b9369-204">In this chapter, we will learn about the examples of these controller customizations.</span></span>

### <a name="instructions"></a><span data-ttu-id="b9369-205">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="b9369-205">Instructions</span></span>

* <span data-ttu-id="b9369-206">Nel **Project** panel, digitare **MotionControllers** nella casella di ricerca.</span><span class="sxs-lookup"><span data-stu-id="b9369-206">In the **Project** panel, type **MotionControllers** in the search box .</span></span> <span data-ttu-id="b9369-207">È anche possibile trovarlo in asset/HoloToolkit/Input/Prefabs /.</span><span class="sxs-lookup"><span data-stu-id="b9369-207">You can also find it under Assets/HoloToolkit/Input/Prefabs/.</span></span>
* <span data-ttu-id="b9369-208">Trascinare il **MotionControllers** prefab nel **gerarchia** pannello.</span><span class="sxs-lookup"><span data-stu-id="b9369-208">Drag the **MotionControllers** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="b9369-209">Fare clic sui **MotionControllers** prefab nel **gerarchia** pannello.</span><span class="sxs-lookup"><span data-stu-id="b9369-209">Click on the **MotionControllers** prefab in the **Hierarchy** panel.</span></span>

<span data-ttu-id="b9369-210">**Prefab MotionControllers**</span><span class="sxs-lookup"><span data-stu-id="b9369-210">**MotionControllers prefab**</span></span>

<span data-ttu-id="b9369-211">**MotionControllers** prefab ha un **MotionControllerVisualizer** script che fornisce gli slot per i modelli di controller alternativo.</span><span class="sxs-lookup"><span data-stu-id="b9369-211">**MotionControllers** prefab has a **MotionControllerVisualizer** script which provides the slots for alternate controller models.</span></span> <span data-ttu-id="b9369-212">Se si assegna i tuoi modelli 3D personalizzati, ad esempio una mano o una sua spada per il e controllare 'Sempre usare alternative sinistra/destra Model', si verrà visualizzato invece il modello predefinito.</span><span class="sxs-lookup"><span data-stu-id="b9369-212">If you assign your own custom 3D models such as a hand or a sword and check 'Always Use Alternate Left/Right Model', you will see them instead of the default model.</span></span> <span data-ttu-id="b9369-213">Si userà questo slot nel capitolo 4 per sostituire il modello controller con un pennello.</span><span class="sxs-lookup"><span data-stu-id="b9369-213">We will use this slot in Chapter 4 to replace the controller model with a brush.</span></span>

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

<span data-ttu-id="b9369-215">**Istruzioni**</span><span class="sxs-lookup"><span data-stu-id="b9369-215">**Instructions**</span></span>
* <span data-ttu-id="b9369-216">Nel **Inspector** del pannello, fare doppio clic **MotionControllerVisualizer** script per visualizzare il codice in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b9369-216">In the **Inspector** panel, double click **MotionControllerVisualizer** script to see the code in the Visual Studio</span></span>

<span data-ttu-id="b9369-217">**Script MotionControllerVisualizer**</span><span class="sxs-lookup"><span data-stu-id="b9369-217">**MotionControllerVisualizer script**</span></span>

<span data-ttu-id="b9369-218">Il **MotionControllerVisualizer** e **MotionControllerInfo** classi forniscono i mezzi per accedere e modificare i modelli di controller predefinito.</span><span class="sxs-lookup"><span data-stu-id="b9369-218">The **MotionControllerVisualizer** and **MotionControllerInfo** classes provide the means to access & modify the default controller models.</span></span> <span data-ttu-id="b9369-219">**MotionControllerVisualizer** sottoscrive di Unity **InteractionSourceDetected** eventi e crea automaticamente modelli controller quando vengono individuate.</span><span class="sxs-lookup"><span data-stu-id="b9369-219">**MotionControllerVisualizer** subscribes to Unity's **InteractionSourceDetected** event and automatically instantiates controller models when they are found.</span></span>

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

<span data-ttu-id="b9369-220">I modelli di controller vengano recapitati in base alla [la specifica glTF](https://github.com/KhronosGroup/glTF).</span><span class="sxs-lookup"><span data-stu-id="b9369-220">The controller models are delivered according to [the glTF specification](https://github.com/KhronosGroup/glTF).</span></span> <span data-ttu-id="b9369-221">Questo formato è stato creato per offrire un formato comune, migliorando il processo dietro la trasmissione e la decompressione automaticamente gli asset 3D.</span><span class="sxs-lookup"><span data-stu-id="b9369-221">This format has been created to provide a common format, while improving the process behind transmitting and unpacking 3D assets.</span></span> <span data-ttu-id="b9369-222">In questo caso, è necessario recuperare e caricare i modelli di controller in fase di esecuzione perché vogliamo migliorare l'esperienza dell'utente più semplice possibile, e non è possibile garantire quale versione del controller di movimento l'utente potrebbe essere utilizzato.</span><span class="sxs-lookup"><span data-stu-id="b9369-222">In this case, we need to retrieve and load the controller models at runtime, as we want to make the user's experience as seamless as possible, and it's not guaranteed which version of the motion controllers the user might be using.</span></span> <span data-ttu-id="b9369-223">Questo corso, tramite il Toolkit di realtà mista, utilizza una versione del gruppo di Khronos [UnityGLTF progetto](https://github.com/KhronosGroup/UnityGLTF).</span><span class="sxs-lookup"><span data-stu-id="b9369-223">This course, via the Mixed Reality Toolkit, uses a version of the Khronos Group's [UnityGLTF project](https://github.com/KhronosGroup/UnityGLTF).</span></span>

<span data-ttu-id="b9369-224">Una volta che il controller è stato recapitato, gli script possono utilizzare **MotionControllerInfo** per trovare le trasformazioni per gli elementi di un controller specifico in modo che è possibile posizionarsi in modo corretto.</span><span class="sxs-lookup"><span data-stu-id="b9369-224">Once the controller has been delivered, scripts can use **MotionControllerInfo** to find the transforms for specific controller elements so they can correctly position themselves.</span></span>

<span data-ttu-id="b9369-225">In un capitolo successivo, si apprenderà come usare questi script per collegare gli elementi dell'interfaccia utente per i controller.</span><span class="sxs-lookup"><span data-stu-id="b9369-225">In a later chapter, we will learn how to use these scripts to attach UI elements to the controllers.</span></span>

<span data-ttu-id="b9369-226">*In alcuni alfabeti, sono disponibili i blocchi di codice con **#if! UNITY_EDITOR** oppure **UNITY_WSA**. Questi blocchi di codice eseguiti solo sul runtime di UWP durante la distribuzione in Windows. Questo avviene perché il set di API utilizzate dall'editor di Unity e dal runtime di app UWP sono diversi.*</span><span class="sxs-lookup"><span data-stu-id="b9369-226">*In some scripts, you will find code blocks with **#if !UNITY_EDITOR** or **UNITY_WSA**. These code blocks run only on the UWP runtime when you deploy to Windows. This is because the set of APIs used by the Unity editor and the UWP app runtime are different.*</span></span>
* <span data-ttu-id="b9369-227">**Salvare** di scena e selezionare il **Riproduci** pulsante.</span><span class="sxs-lookup"><span data-stu-id="b9369-227">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="b9369-228">Sarà in grado di visualizzare la scena con i controller di movimento nelle cuffie.</span><span class="sxs-lookup"><span data-stu-id="b9369-228">You will be able to see the scene with motion controllers in your headset.</span></span> <span data-ttu-id="b9369-229">È possibile visualizzare dettagliate animazioni per clic sui pulsanti, spostamento thumbstick ed evidenziazione touch touchpad.</span><span class="sxs-lookup"><span data-stu-id="b9369-229">You can see detailed animations for button clicks, thumbstick movement, and touchpad touch highlighting.</span></span>

![MR213_Controller visualizzazione predefinita](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a><span data-ttu-id="b9369-231">Capitolo 2 - associare elementi dell'interfaccia utente per il controller</span><span class="sxs-lookup"><span data-stu-id="b9369-231">Chapter 2 - Attaching UI elements to the controller</span></span>

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a><span data-ttu-id="b9369-232">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="b9369-232">Objectives</span></span>

* <span data-ttu-id="b9369-233">Informazioni sugli elementi dei controller di movimento</span><span class="sxs-lookup"><span data-stu-id="b9369-233">Learn about the elements of the motion controllers</span></span>
* <span data-ttu-id="b9369-234">Informazioni su come connettere gli oggetti a parti specifiche dei controller</span><span class="sxs-lookup"><span data-stu-id="b9369-234">Learn how to attach objects to specific parts of the controllers</span></span>

<span data-ttu-id="b9369-235">In questo capitolo, si apprenderà come aggiungere elementi dell'interfaccia utente per il controller che l'utente può accedere e modificare in qualsiasi momento facilmente.</span><span class="sxs-lookup"><span data-stu-id="b9369-235">In this chapter, you will learn how to add user interface elements to the controller which the user can easily access and manipulate at anytime.</span></span> <span data-ttu-id="b9369-236">Si apprenderà anche come aggiungere una selezione colori semplice interfaccia utente usando il touchpad di input.</span><span class="sxs-lookup"><span data-stu-id="b9369-236">You will also learn how to add a simple color picker UI using the touchpad input.</span></span>

### <a name="instructions"></a><span data-ttu-id="b9369-237">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="b9369-237">Instructions</span></span>

* <span data-ttu-id="b9369-238">Nel **Project** del pannello, cercare **MotionControllerInfo** script.</span><span class="sxs-lookup"><span data-stu-id="b9369-238">In the **Project** panel, search **MotionControllerInfo** script.</span></span>
* <span data-ttu-id="b9369-239">Dai risultati della ricerca, fare doppio clic **MotionControllerInfo** script per visualizzare il codice in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b9369-239">From the search result, double click **MotionControllerInfo** script to see the code in Visual Studio.</span></span>

<span data-ttu-id="b9369-240">**Script MotionControllerInfo**</span><span class="sxs-lookup"><span data-stu-id="b9369-240">**MotionControllerInfo script**</span></span>

<span data-ttu-id="b9369-241">Il primo passaggio consiste nello scegliere quale elemento del controller l'interfaccia utente a cui connettersi.</span><span class="sxs-lookup"><span data-stu-id="b9369-241">The first step is to choose which element of the controller you want the UI to attach to.</span></span> <span data-ttu-id="b9369-242">Questi elementi sono definiti nello **ControllerElementEnum** nelle **MotionControllerInfo.cs**.</span><span class="sxs-lookup"><span data-stu-id="b9369-242">These elements are defined in **ControllerElementEnum** in **MotionControllerInfo.cs**.</span></span>

![MR213 MotionControllerElements](images/mr213-motioncontrollerelements-1000px.jpg)
* <span data-ttu-id="b9369-244">**Home**</span><span class="sxs-lookup"><span data-stu-id="b9369-244">**Home**</span></span>
* <span data-ttu-id="b9369-245">**Menu**</span><span class="sxs-lookup"><span data-stu-id="b9369-245">**Menu**</span></span>
* <span data-ttu-id="b9369-246">**Afferrare**</span><span class="sxs-lookup"><span data-stu-id="b9369-246">**Grasp**</span></span>
* <span data-ttu-id="b9369-247">**Thumbstick**</span><span class="sxs-lookup"><span data-stu-id="b9369-247">**Thumbstick**</span></span>
* <span data-ttu-id="b9369-248">**Selezionare**</span><span class="sxs-lookup"><span data-stu-id="b9369-248">**Select**</span></span>
* <span data-ttu-id="b9369-249">**Touchpad**</span><span class="sxs-lookup"><span data-stu-id="b9369-249">**Touchpad**</span></span>
* <span data-ttu-id="b9369-250">**Puntamento posa** : questo elemento rappresenta la punta del controller che puntano direzione in avanti.</span><span class="sxs-lookup"><span data-stu-id="b9369-250">**Pointing pose** – this element represents the tip of the controller pointing forward direction.</span></span>

<span data-ttu-id="b9369-251">**Istruzioni**</span><span class="sxs-lookup"><span data-stu-id="b9369-251">**Instructions**</span></span>
* <span data-ttu-id="b9369-252">Nel **Project** del pannello, cercare **AttachToController** script.</span><span class="sxs-lookup"><span data-stu-id="b9369-252">In the **Project** panel, search **AttachToController** script.</span></span>
* <span data-ttu-id="b9369-253">Dai risultati della ricerca, fare doppio clic **AttachToController** script per visualizzare il codice in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b9369-253">From the search result, double click **AttachToController** script to see the code in Visual Studio.</span></span>

<span data-ttu-id="b9369-254">**Script AttachToController**</span><span class="sxs-lookup"><span data-stu-id="b9369-254">**AttachToController script**</span></span>

<span data-ttu-id="b9369-255">Il **AttachToController** script fornisce un modo semplice per collegare tutti gli oggetti di una mano del controller specificato e un elemento.</span><span class="sxs-lookup"><span data-stu-id="b9369-255">The **AttachToController** script provides a simple way to attach any objects to a specified controller handedness and element.</span></span>

<span data-ttu-id="b9369-256">In **AttachElementToController()**,</span><span class="sxs-lookup"><span data-stu-id="b9369-256">In **AttachElementToController()**,</span></span>
* <span data-ttu-id="b9369-257">Controllare con mano **MotionControllerInfo.Handedness**</span><span class="sxs-lookup"><span data-stu-id="b9369-257">Check handedness using **MotionControllerInfo.Handedness**</span></span>
* <span data-ttu-id="b9369-258">Ottenere l'elemento specifico di controller usando **MotionControllerInfo.TryGetElement()**</span><span class="sxs-lookup"><span data-stu-id="b9369-258">Get specific element of the controller using **MotionControllerInfo.TryGetElement()**</span></span>
* <span data-ttu-id="b9369-259">Dopo aver recuperato l'elemento trasformano dal modello di controller, padre dell'oggetto posizionato sotto il e impostare la posizione locale e rotazione dell'oggetto su zero.</span><span class="sxs-lookup"><span data-stu-id="b9369-259">After retrieving the element's transform from the controller model, parent the object under it and set object's local position & rotation to zero.</span></span>

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

<span data-ttu-id="b9369-260">Il modo più semplice per usare **AttachToController** script consiste nell'ereditare da quest'ultimo, come illustrato nel caso di **ColorPickerWheel.**</span><span class="sxs-lookup"><span data-stu-id="b9369-260">The simplest way to use **AttachToController** script is to inherit from it, as we've done in the case of **ColorPickerWheel.**</span></span> <span data-ttu-id="b9369-261">È sufficiente eseguire l'override di **OnAttachToController** e **OnDetatchFromController** funzioni per eseguire il programma di installazione / scomposizione quando il controller è rilevato o disconnesso.</span><span class="sxs-lookup"><span data-stu-id="b9369-261">Simply override the **OnAttachToController** and **OnDetatchFromController** functions to perform your setup / breakdown when the controller is detected / disconnected.</span></span>

<span data-ttu-id="b9369-262">**Istruzioni**</span><span class="sxs-lookup"><span data-stu-id="b9369-262">**Instructions**</span></span>
* <span data-ttu-id="b9369-263">Nel **Project** panel, digitare nella casella di ricerca **ColorPickerWheel**.</span><span class="sxs-lookup"><span data-stu-id="b9369-263">In the **Project** panel, type in the search box **ColorPickerWheel**.</span></span> <span data-ttu-id="b9369-264">È anche possibile trovarlo in asset/AppPrefabs /.</span><span class="sxs-lookup"><span data-stu-id="b9369-264">You can also find it under Assets/AppPrefabs/.</span></span>
* <span data-ttu-id="b9369-265">Trascinare **ColorPickerWheel** prefab nel **gerarchia** pannello.</span><span class="sxs-lookup"><span data-stu-id="b9369-265">Drag **ColorPickerWheel** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="b9369-266">Fare clic sui **ColorPickerWheel** prefab nel **gerarchia** pannello.</span><span class="sxs-lookup"><span data-stu-id="b9369-266">Click the **ColorPickerWheel** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="b9369-267">Nel **Inspector** del pannello, fare doppio clic **ColorPickerWheel** Script per visualizzare il codice in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b9369-267">In the **Inspector** panel, double click **ColorPickerWheel** Script to see the code in Visual Studio.</span></span>

![Prefab ColorPickerWheel](images/mr213-colorpickerwheel-1000px.jpg)

<span data-ttu-id="b9369-269">**Script ColorPickerWheel**</span><span class="sxs-lookup"><span data-stu-id="b9369-269">**ColorPickerWheel script**</span></span>

<span data-ttu-id="b9369-270">Poiché **ColorPickerWheel** eredita **AttachToController**, Mostra **mano** e **elemento** nel  **Inspector** pannello.</span><span class="sxs-lookup"><span data-stu-id="b9369-270">Since **ColorPickerWheel** inherits **AttachToController**, it shows **Handedness** and **Element** in the **Inspector** panel.</span></span> <span data-ttu-id="b9369-271">È l'interfaccia utente verrà collegamento all'elemento Touchpad nel controller a sinistra.</span><span class="sxs-lookup"><span data-stu-id="b9369-271">We'll be attaching the UI to the Touchpad element on the left controller.</span></span>

![Script ColorPickerWheel](images/mr213-attachtocontroller-300px.jpg)

<span data-ttu-id="b9369-273">**ColorPickerWheel** esegue l'override di **OnAttachToController** e **OnDetatchFromController** per sottoscrivere l'evento di input che verrà usato nel capitolo successivo per la selezione di colore con touchpad di input.</span><span class="sxs-lookup"><span data-stu-id="b9369-273">**ColorPickerWheel** overrides the **OnAttachToController** and **OnDetatchFromController** to subscribe to the input event which will be used in next chapter for color selection with touchpad input.</span></span>

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
* <span data-ttu-id="b9369-274">**Salvare** di scena e selezionare il **Riproduci** pulsante.</span><span class="sxs-lookup"><span data-stu-id="b9369-274">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="b9369-275">**Metodo alternativo per la connessione di oggetti per i controller**</span><span class="sxs-lookup"><span data-stu-id="b9369-275">**Alternative method for attaching objects to the controllers**</span></span>

<span data-ttu-id="b9369-276">È consigliabile che gli script di ereditano **AttachToController** ed eseguire l'override **OnAttachToController**.</span><span class="sxs-lookup"><span data-stu-id="b9369-276">We recommend that your scripts inherit from **AttachToController** and override **OnAttachToController**.</span></span> <span data-ttu-id="b9369-277">Tuttavia, ciò potrebbe non essere sempre possibile.</span><span class="sxs-lookup"><span data-stu-id="b9369-277">However, this may not always be possible.</span></span> <span data-ttu-id="b9369-278">In alternativa lo usa come componente autonomo.</span><span class="sxs-lookup"><span data-stu-id="b9369-278">An alternative is using it as a standalone component.</span></span> <span data-ttu-id="b9369-279">Ciò risulta utile quando si desidera collegare un prefab esistente a un controller senza eseguire il refactoring gli script.</span><span class="sxs-lookup"><span data-stu-id="b9369-279">This can be useful when you want to attach an existing prefab to a controller without refactoring your scripts.</span></span> <span data-ttu-id="b9369-280">È sufficiente definire la classe attendere IsAttached sia impostato su true prima di eseguire qualsiasi programma di installazione.</span><span class="sxs-lookup"><span data-stu-id="b9369-280">Simply have your class wait for IsAttached to be set to true before performing any setup.</span></span> <span data-ttu-id="b9369-281">Il modo più semplice per eseguire questa operazione consiste nell'usare una coroutine per 'Start'.</span><span class="sxs-lookup"><span data-stu-id="b9369-281">The simplest way to do this is by using a coroutine for 'Start.'</span></span>

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a><span data-ttu-id="b9369-282">Capitolo 3 - uso di input touchpad</span><span class="sxs-lookup"><span data-stu-id="b9369-282">Chapter 3 - Working with touchpad input</span></span>

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a><span data-ttu-id="b9369-283">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="b9369-283">Objectives</span></span>

* <span data-ttu-id="b9369-284">Informazioni su come ottenere gli eventi di dati di input touchpad</span><span class="sxs-lookup"><span data-stu-id="b9369-284">Learn how to get touchpad input data events</span></span>
* <span data-ttu-id="b9369-285">Informazioni su come usare le informazioni sulla posizione di asse touchpad per l'esperienza di app</span><span class="sxs-lookup"><span data-stu-id="b9369-285">Learn how to use touchpad axis position information for your app experience</span></span>

### <a name="instructions"></a><span data-ttu-id="b9369-286">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="b9369-286">Instructions</span></span>

* <span data-ttu-id="b9369-287">Nel **gerarchia** del pannello, fare clic su **ColorPickerWheel**</span><span class="sxs-lookup"><span data-stu-id="b9369-287">In the **Hierarchy** panel, click **ColorPickerWheel**</span></span>
* <span data-ttu-id="b9369-288">Nel **Inspector** nel pannello **Animatior**, fare doppio clic **ColorPickerWheelController**</span><span class="sxs-lookup"><span data-stu-id="b9369-288">In the **Inspector** panel, under **Animatior**, double click **ColorPickerWheelController**</span></span>
* <span data-ttu-id="b9369-289">Sarà in grado di visualizzare **animatore** scheda aperta</span><span class="sxs-lookup"><span data-stu-id="b9369-289">You will be able to see **Animator** tab opened</span></span>

<span data-ttu-id="b9369-290">**Interfaccia utente di mostrare/nascondere con controller di animazione di Unity**</span><span class="sxs-lookup"><span data-stu-id="b9369-290">**Showing/hiding UI with Unity's Animation controller**</span></span>

<span data-ttu-id="b9369-291">Per mostrare e nascondere il **ColorPickerWheel** dell'interfaccia utente con un'animazione, utilizziamo [sistema di animazione di Unity](https://docs.unity3d.com/Manual/AnimationOverview.html).</span><span class="sxs-lookup"><span data-stu-id="b9369-291">To show and hide the **ColorPickerWheel** UI with animation, we are using [Unity's animation system](https://docs.unity3d.com/Manual/AnimationOverview.html).</span></span> <span data-ttu-id="b9369-292">Impostando il **ColorPickerWheel**del **Visible** proprietà su true o false trigger **Mostra** e **nascondere** trigger animazione.</span><span class="sxs-lookup"><span data-stu-id="b9369-292">Setting the **ColorPickerWheel**'s **Visible** property to true or false triggers **Show** and **Hide** animation triggers.</span></span> <span data-ttu-id="b9369-293">**Mostrare** e **Nascondi** i parametri sono definiti nel **ColorPickerWheelController** controller dell'animazione.</span><span class="sxs-lookup"><span data-stu-id="b9369-293">**Show** and **Hide** parameters are defined in the **ColorPickerWheelController** animation controller.</span></span>

![Controller di animazione di Unity](images/mr123-animationcontroller-550px.jpg)

<span data-ttu-id="b9369-295">**Istruzioni**</span><span class="sxs-lookup"><span data-stu-id="b9369-295">**Instructions**</span></span>
* <span data-ttu-id="b9369-296">Nel **gerarchia** Pannello di selezione **ColorPickerWheel** prefab</span><span class="sxs-lookup"><span data-stu-id="b9369-296">In the **Hierarchy** panel, select **ColorPickerWheel** prefab</span></span>
* <span data-ttu-id="b9369-297">Nel **Inspector** del pannello, fare doppio clic **ColorPickerWheel** script per visualizzare il codice in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b9369-297">In the **Inspector** panel, double click **ColorPickerWheel** script to see the code in the Visual Studio</span></span>

<span data-ttu-id="b9369-298">**Script ColorPickerWheel**</span><span class="sxs-lookup"><span data-stu-id="b9369-298">**ColorPickerWheel script**</span></span>

<span data-ttu-id="b9369-299">**ColorPickerWheel** sottoscrive di Unity **InteractionSourceUpdated** evento da ascoltare gli eventi touchpad.</span><span class="sxs-lookup"><span data-stu-id="b9369-299">**ColorPickerWheel** subscribes to Unity's **InteractionSourceUpdated** event to listen for touchpad events.</span></span>

<span data-ttu-id="b9369-300">Nelle **InteractionSourceUpdated()**, lo script prima controlla per verificare che l'it:</span><span class="sxs-lookup"><span data-stu-id="b9369-300">In **InteractionSourceUpdated()**, the script first checks to ensure that it:</span></span>
* <span data-ttu-id="b9369-301">è effettivamente un evento touchpad (obj.state. **touchpadTouched**)</span><span class="sxs-lookup"><span data-stu-id="b9369-301">is actually a touchpad event (obj.state.**touchpadTouched**)</span></span>
* <span data-ttu-id="b9369-302">proveniente dal controller di sinistra (obj.state.source. **mano**)</span><span class="sxs-lookup"><span data-stu-id="b9369-302">originates from the left controller (obj.state.source.**handedness**)</span></span>

<span data-ttu-id="b9369-303">Se entrambi sono true, posizionare il touchpad (obj.state. **touchpadPosition**) viene assegnato a **selectorPosition**.</span><span class="sxs-lookup"><span data-stu-id="b9369-303">If both are true, the touchpad position (obj.state.**touchpadPosition**) is assigned to **selectorPosition**.</span></span>

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

<span data-ttu-id="b9369-304">Nelle **Update ()**, in base **visibile** proprietà, l'avviso si attiverà mostrare e nascondere i trigger animazione nel componente animatore del controllo di selezione colore</span><span class="sxs-lookup"><span data-stu-id="b9369-304">In **Update()**, based on **visible** property, it triggers Show and Hide animation triggers in the color picker's animator component</span></span>

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

<span data-ttu-id="b9369-305">Nelle **Update ()**, **selectorPosition** viene utilizzato per eseguire il cast di un raggio in collider mesh del selettore colori, che restituisce una posizione UV.</span><span class="sxs-lookup"><span data-stu-id="b9369-305">In **Update()**, **selectorPosition** is used to cast a ray at the color wheel's mesh collider, which returns a UV position.</span></span> <span data-ttu-id="b9369-306">Questa posizione è quindi utilizzabile per trovare la coordinata in pixel e valore di trama del selettore colori del colore.</span><span class="sxs-lookup"><span data-stu-id="b9369-306">This position can then be used to find the pixel coordinate and color value of the color wheel's texture.</span></span> <span data-ttu-id="b9369-307">Questo valore è accessibile da altri script tramite il **SelectedColor** proprietà.</span><span class="sxs-lookup"><span data-stu-id="b9369-307">This value is accessible to other scripts via the **SelectedColor** property.</span></span>

![Colore selezione rotellina Raycasting](images/mr213-colorpickerwheel-raycast-700px.png)

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

## <a name="chapter-4---overriding-controller-model"></a><span data-ttu-id="b9369-309">Capitolo 4 - eseguire l'override di model controller</span><span class="sxs-lookup"><span data-stu-id="b9369-309">Chapter 4 - Overriding controller model</span></span>

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a><span data-ttu-id="b9369-310">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="b9369-310">Objectives</span></span>

* <span data-ttu-id="b9369-311">Informazioni su come eseguire l'override del modello controller con un modello 3D di personalizzati.</span><span class="sxs-lookup"><span data-stu-id="b9369-311">Learn how to override the controller model with a custom 3D model.</span></span>

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a><span data-ttu-id="b9369-313">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="b9369-313">Instructions</span></span>

* <span data-ttu-id="b9369-314">Fare clic su **MotionControllers** nel **gerarchia** pannello.</span><span class="sxs-lookup"><span data-stu-id="b9369-314">Click **MotionControllers** in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="b9369-315">Fare clic sul cerchio sul lato destro del **alternativo destra Controller** campo.</span><span class="sxs-lookup"><span data-stu-id="b9369-315">Click the circle on the right side of the **Alternate Right Controller** field.</span></span>
* <span data-ttu-id="b9369-316">Digitare **' BrushController**' e selezionare il prefab dal risultato.</span><span class="sxs-lookup"><span data-stu-id="b9369-316">Type in **'BrushController**' and select the prefab from the result.</span></span> <span data-ttu-id="b9369-317">È possibile trovarla nel Assets/AppPrefabs/**BrushController**.</span><span class="sxs-lookup"><span data-stu-id="b9369-317">You can find it under Assets/AppPrefabs/**BrushController**.</span></span>
* <span data-ttu-id="b9369-318">Controllare **sempre usare alternativo modello appropriato**</span><span class="sxs-lookup"><span data-stu-id="b9369-318">Check **Always Use Alternate Right Model**</span></span>

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

<span data-ttu-id="b9369-320">Il **BrushController** prefab non deve essere incluso nel **gerarchia** pannello.</span><span class="sxs-lookup"><span data-stu-id="b9369-320">The **BrushController** prefab does not have to be included in the **Hierarchy** panel.</span></span> <span data-ttu-id="b9369-321">Tuttavia, per estrarre i componenti figlio:</span><span class="sxs-lookup"><span data-stu-id="b9369-321">However, to check out its child components:</span></span>
* <span data-ttu-id="b9369-322">Nel **progetto** panel, digitare **BrushController** trascinare **BrushController** prefab nel **gerarchia** pannello.</span><span class="sxs-lookup"><span data-stu-id="b9369-322">In the **Project** panel, type in **BrushController** and drag **BrushController** prefab into the **Hierarchy** panel.</span></span>

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

<span data-ttu-id="b9369-324">Si noterà il **suggerimento** componente nelle **BrushController**.</span><span class="sxs-lookup"><span data-stu-id="b9369-324">You will find the **Tip** component in **BrushController**.</span></span> <span data-ttu-id="b9369-325">Si userà la trasformazione corrispondente per l'avvio/arresto disegno di linee.</span><span class="sxs-lookup"><span data-stu-id="b9369-325">We will use its transform to start/stop drawing lines.</span></span>
* <span data-ttu-id="b9369-326">Eliminare il **BrushController** dalle **gerarchia** pannello.</span><span class="sxs-lookup"><span data-stu-id="b9369-326">Delete the **BrushController** from the **Hierarchy** panel.</span></span>
* <span data-ttu-id="b9369-327">**Salvare** di scena e selezionare il **Riproduci** pulsante.</span><span class="sxs-lookup"><span data-stu-id="b9369-327">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="b9369-328">Sarà in grado di visualizzare che il modello di pennello sostituito il controller di movimento a destra.</span><span class="sxs-lookup"><span data-stu-id="b9369-328">You will be able to see the brush model replaced the right-hand motion controller.</span></span>

## <a name="chapter-5---painting-with-select-input"></a><span data-ttu-id="b9369-329">Disegno con l'istruzione Select di capitolo 5 - input</span><span class="sxs-lookup"><span data-stu-id="b9369-329">Chapter 5 - Painting with Select input</span></span>

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a><span data-ttu-id="b9369-330">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="b9369-330">Objectives</span></span>

* <span data-ttu-id="b9369-331">Informazioni su come usare l'evento del pulsante Seleziona per avviare e arrestare un disegno di linee</span><span class="sxs-lookup"><span data-stu-id="b9369-331">Learn how to use the Select button event to start and stop a line drawing</span></span>

### <a name="instructions"></a><span data-ttu-id="b9369-332">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="b9369-332">Instructions</span></span>

* <span data-ttu-id="b9369-333">Ricerca **BrushController** prefab nel **progetto** pannello.</span><span class="sxs-lookup"><span data-stu-id="b9369-333">Search **BrushController** prefab in the **Project** panel.</span></span>
* <span data-ttu-id="b9369-334">Nel **Inspector** del pannello, fare doppio clic **BrushController** Script per visualizzare il codice in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b9369-334">In the **Inspector** panel, double click **BrushController** Script to see the code in Visual Studio</span></span>

<span data-ttu-id="b9369-335">**Script BrushController**</span><span class="sxs-lookup"><span data-stu-id="b9369-335">**BrushController script**</span></span>

<span data-ttu-id="b9369-336">**BrushController** sottoscrive il InteractionManager **InteractionSourcePressed** e **InteractionSourceReleased** gli eventi.</span><span class="sxs-lookup"><span data-stu-id="b9369-336">**BrushController** subscribes to the InteractionManager's **InteractionSourcePressed** and **InteractionSourceReleased** events.</span></span> <span data-ttu-id="b9369-337">Quando **InteractionSourcePressed** evento viene generato, il pennello **disegnare** viene impostata su true; quando **InteractionSourceReleased** evento viene generato, il pennello **Disegnare** proprietà è impostata su false.</span><span class="sxs-lookup"><span data-stu-id="b9369-337">When **InteractionSourcePressed** event is triggered, the brush's **Draw** property is set to true; when **InteractionSourceReleased** event is triggered, the brush's **Draw** property is set to false.</span></span>

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

<span data-ttu-id="b9369-338">Sebbene **disegnare** è impostata su true, il pennello genereranno i punti in un'istanza Unity **LineRenderer**.</span><span class="sxs-lookup"><span data-stu-id="b9369-338">While **Draw** is set to true, the brush will generate points in an instantiated Unity **LineRenderer**.</span></span> <span data-ttu-id="b9369-339">Un riferimento a questa prefab viene mantenuto nel pennello **Stroke Prefab** campo.</span><span class="sxs-lookup"><span data-stu-id="b9369-339">A reference to this prefab is kept in the brush's **Stroke Prefab** field.</span></span>

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

<span data-ttu-id="b9369-340">Usare il colore attualmente selezionato dalla rotellina di selezione dell'interfaccia utente, colore **BrushController** deve avere un riferimento al **ColorPickerWheel** oggetto.</span><span class="sxs-lookup"><span data-stu-id="b9369-340">To use the currently selected color from the color picker wheel UI, **BrushController** needs to have a reference to the **ColorPickerWheel** object.</span></span> <span data-ttu-id="b9369-341">Poiché il **BrushController** prefab viene creata un'istanza in fase di esecuzione come controller di sostituzione, tutti i riferimenti agli oggetti nella scena dovrà essere impostata in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="b9369-341">Because the **BrushController** prefab is instantiated at runtime as a replacement controller, any references to objects in the scene will have to be set at runtime.</span></span> <span data-ttu-id="b9369-342">In questo caso usiamo **GameObject.FindObjectOfType** per individuare le **ColorPickerWheel**:</span><span class="sxs-lookup"><span data-stu-id="b9369-342">In this case we use **GameObject.FindObjectOfType** to locate the **ColorPickerWheel**:</span></span>

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
* <span data-ttu-id="b9369-343">**Salvare** di scena e selezionare il **Riproduci** pulsante.</span><span class="sxs-lookup"><span data-stu-id="b9369-343">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="b9369-344">Sarà in grado di disegnare le linee e disegnare con il pulsante di selezione sul controller a destra.</span><span class="sxs-lookup"><span data-stu-id="b9369-344">You will be able to draw the lines and paint using the select button on the right-hand controller.</span></span>

## <a name="chapter-6---object-spawning-with-select-input"></a><span data-ttu-id="b9369-345">Capitolo 6 - oggetto durante la generazione con l'istruzione Select di input</span><span class="sxs-lookup"><span data-stu-id="b9369-345">Chapter 6 - Object spawning with Select input</span></span>

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a><span data-ttu-id="b9369-346">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="b9369-346">Objectives</span></span>

* <span data-ttu-id="b9369-347">Informazioni su come usare Select e comprendere gli eventi di input di pulsante</span><span class="sxs-lookup"><span data-stu-id="b9369-347">Learn how to use Select and Grasp button input events</span></span>
* <span data-ttu-id="b9369-348">Informazioni su come creare istanze degli oggetti</span><span class="sxs-lookup"><span data-stu-id="b9369-348">Learn how to instantiate objects</span></span>

### <a name="instructions"></a><span data-ttu-id="b9369-349">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="b9369-349">Instructions</span></span>

* <span data-ttu-id="b9369-350">Nel **Project** panel, digitare **ObjectSpawner** nella casella di ricerca.</span><span class="sxs-lookup"><span data-stu-id="b9369-350">In the **Project** panel, type **ObjectSpawner** in the search box.</span></span> <span data-ttu-id="b9369-351">È anche possibile trovarlo in asset/AppPrefabs /</span><span class="sxs-lookup"><span data-stu-id="b9369-351">You can also find it under Assets/AppPrefabs/</span></span>
* <span data-ttu-id="b9369-352">Trascinare il **ObjectSpawner** prefab nel **gerarchia** pannello.</span><span class="sxs-lookup"><span data-stu-id="b9369-352">Drag the **ObjectSpawner** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="b9369-353">Fare clic su **ObjectSpawner** nel **gerarchia** pannello.</span><span class="sxs-lookup"><span data-stu-id="b9369-353">Click **ObjectSpawner** in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="b9369-354">**ObjectSpawner** ha un campo denominato **colore origine**.</span><span class="sxs-lookup"><span data-stu-id="b9369-354">**ObjectSpawner** has a field named **Color Source**.</span></span>
* <span data-ttu-id="b9369-355">Dal **gerarchia** panel, trascinare le **ColorPickerWheel** riferimento in questo campo.</span><span class="sxs-lookup"><span data-stu-id="b9369-355">From the **Hierarchy** panel, drag the **ColorPickerWheel** reference into this field.</span></span>

![Oggetto Spawner Inspector](images/mr213-objectspawnercolorpickerwheel-650px.jpg)
* <span data-ttu-id="b9369-357">Fare clic sui **ObjectSpawner** prefab nel **gerarchia** pannello.</span><span class="sxs-lookup"><span data-stu-id="b9369-357">Click the **ObjectSpawner** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="b9369-358">Nel **Inspector** del pannello, fare doppio clic **ObjectSpawner** Script per visualizzare il codice in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b9369-358">In the **Inspector** panel, double click **ObjectSpawner** Script to see the code in Visual Studio.</span></span>

<span data-ttu-id="b9369-359">**Script ObjectSpawner**</span><span class="sxs-lookup"><span data-stu-id="b9369-359">**ObjectSpawner script**</span></span>

<span data-ttu-id="b9369-360">Il **ObjectSpawner** crea un'istanza di copie di una primitiva mesh (cubo, sfera, cilindro) nello spazio.</span><span class="sxs-lookup"><span data-stu-id="b9369-360">The **ObjectSpawner** instantiates copies of a primitive mesh (cube, sphere, cylinder) into the space.</span></span> <span data-ttu-id="b9369-361">Quando un **InteractionSourcePressed** viene rilevato controlla la mano utilizzata per scrivere e se è un **InteractionSourcePressType.Grasp** oppure **InteractionSourcePressType.Select** evento.</span><span class="sxs-lookup"><span data-stu-id="b9369-361">When a **InteractionSourcePressed** is detected it checks the handedness and if it's an **InteractionSourcePressType.Grasp** or **InteractionSourcePressType.Select** event.</span></span>

<span data-ttu-id="b9369-362">Per un **afferrare** evento, incrementa l'indice del tipo di rete corrente (sfera, cubi, cilindro)</span><span class="sxs-lookup"><span data-stu-id="b9369-362">For a **Grasp** event, it increments the index of current mesh type (sphere, cube, cylinder)</span></span>

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

<span data-ttu-id="b9369-363">Per un **selezionate** evento, nel **SpawnObject()**, un nuovo oggetto è stata creata un'istanza, senza padre e vengono rilasciati in tutto il mondo.</span><span class="sxs-lookup"><span data-stu-id="b9369-363">For a **Select** event, in **SpawnObject()**, a new object is instantiated, un-parented and released into the world.</span></span>

```cs
private void SpawnObject()
{
    // Instantiate the spawned object
    GameObject newObject = Instantiate(displayObject.gameObject, spawnParent);
    // Detatch the newly spawned object
    newObject.transform.parent = null;
    // Reset the scale transform to 1
    scaleParent.localScale = Vector3.one;
    // Set its material color so its material gets instantiated
    newObject.GetComponent<Renderer>().material.color = colorSource.SelectedColor;
}
```

<span data-ttu-id="b9369-364">Il **ObjectSpawner** Usa le **ColorPickerWheel** per impostare il colore del materiale dell'oggetto di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="b9369-364">The **ObjectSpawner** uses the **ColorPickerWheel** to set the color of the display object's material.</span></span> <span data-ttu-id="b9369-365">Oggetti generati ha un'istanza di questo materiale in modo che manterrà i colori.</span><span class="sxs-lookup"><span data-stu-id="b9369-365">Spawned objects are given an instance of this material so they will retain their color.</span></span>
* <span data-ttu-id="b9369-366">**Salvare** di scena e selezionare il **Riproduci** pulsante.</span><span class="sxs-lookup"><span data-stu-id="b9369-366">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="b9369-367">Sarà possibile modificare gli oggetti con il pulsante. é quindi e generare gli oggetti con il pulsante di selezione.</span><span class="sxs-lookup"><span data-stu-id="b9369-367">You will be able to change the objects with the Grasp button and spawn objects with the Select button.</span></span>

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a><span data-ttu-id="b9369-368">Compilare e distribuire app al portale di realtà mista</span><span class="sxs-lookup"><span data-stu-id="b9369-368">Build and deploy app to Mixed Reality Portal</span></span>
* <span data-ttu-id="b9369-369">In Unity, selezionare **File > Build Settings**.</span><span class="sxs-lookup"><span data-stu-id="b9369-369">In Unity, select **File > Build Settings**.</span></span>
* <span data-ttu-id="b9369-370">Fare clic su **aggiungere scene Open** per aggiungere scena corrente per il **scene nella compilazione**.</span><span class="sxs-lookup"><span data-stu-id="b9369-370">Click **Add Open Scenes** to add current scene to the **Scenes In Build**.</span></span>
* <span data-ttu-id="b9369-371">Fai clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="b9369-371">Click **Build**.</span></span>
* <span data-ttu-id="b9369-372">Creare un **nuova cartella** denominato "App".</span><span class="sxs-lookup"><span data-stu-id="b9369-372">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="b9369-373">Solo clic i **App** cartella.</span><span class="sxs-lookup"><span data-stu-id="b9369-373">Single click the **App** folder.</span></span>
* <span data-ttu-id="b9369-374">Fare clic su **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="b9369-374">Click **Select Folder**.</span></span>
* <span data-ttu-id="b9369-375">Quando Unity viene eseguita, verrà visualizzata una finestra di Esplora File.</span><span class="sxs-lookup"><span data-stu-id="b9369-375">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="b9369-376">Aprire il **App** cartella.</span><span class="sxs-lookup"><span data-stu-id="b9369-376">Open the **App** folder.</span></span>
* <span data-ttu-id="b9369-377">Fare doppio clic su **YourSceneName.sln** file di soluzione di Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b9369-377">Double click **YourSceneName.sln** Visual Studio Solution file.</span></span>
* <span data-ttu-id="b9369-378">Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione di debug per **Release** e da ARM a **X64**.</span><span class="sxs-lookup"><span data-stu-id="b9369-378">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X64**.</span></span>
* <span data-ttu-id="b9369-379">Fare clic sulla freccia giù accanto al pulsante di dispositivo e selezionare **computer locale**.</span><span class="sxs-lookup"><span data-stu-id="b9369-379">Click on the drop-down arrow next to the Device button, and select **Local Machine**.</span></span>
* <span data-ttu-id="b9369-380">Fare clic su **Debug -> Avvia senza eseguire debug** nel menu o premere **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="b9369-380">Click **Debug -> Start Without debugging** in the menu or press **Ctrl + F5**.</span></span>

<span data-ttu-id="b9369-381">Ora l'app viene compilata e installata nel portale di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="b9369-381">Now the app is built and installed in Mixed Reality Portal.</span></span> <span data-ttu-id="b9369-382">È possibile avviarlo nuovamente tramite il menu Start nel portale di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="b9369-382">You can launch it again through Start menu in Mixed Reality Portal.</span></span>

## <a name="advanced-design---brush-tools-with-radial-layout"></a><span data-ttu-id="b9369-383">Progettazione avanzata - strumenti di pennello con layout Radiale</span><span class="sxs-lookup"><span data-stu-id="b9369-383">Advanced design - Brush tools with radial layout</span></span>

![MixedReality213 Main](images/mr213-main-600px.jpg)

<span data-ttu-id="b9369-385">In questo capitolo, si apprenderà come sostituire il modello di controller di movimento predefiniti con una raccolta di strumento pennello personalizzato.</span><span class="sxs-lookup"><span data-stu-id="b9369-385">In this chapter, you will learn how to replace the default motion controller model with a custom brush tool collection.</span></span> <span data-ttu-id="b9369-386">Per riferimento, è possibile trovare la scena completata **MixedReality213Advanced** sotto **scene** cartella.</span><span class="sxs-lookup"><span data-stu-id="b9369-386">For your reference, you can find the completed scene **MixedReality213Advanced** under **Scenes** folder.</span></span>

### <a name="instructions"></a><span data-ttu-id="b9369-387">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="b9369-387">Instructions</span></span>

* <span data-ttu-id="b9369-388">Nel **Project** panel, digitare **BrushSelector** nella casella di ricerca.</span><span class="sxs-lookup"><span data-stu-id="b9369-388">In the **Project** panel, type **BrushSelector** in the search box .</span></span> <span data-ttu-id="b9369-389">È anche possibile trovarlo in asset/AppPrefabs /</span><span class="sxs-lookup"><span data-stu-id="b9369-389">You can also find it under Assets/AppPrefabs/</span></span>
* <span data-ttu-id="b9369-390">Trascinare il **BrushSelector** prefab nel **gerarchia** pannello.</span><span class="sxs-lookup"><span data-stu-id="b9369-390">Drag the **BrushSelector** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="b9369-391">Per l'organizzazione, creare un GameObject vuoto denominato **pennelli**</span><span class="sxs-lookup"><span data-stu-id="b9369-391">For organization, create an empty GameObject called **Brushes**</span></span>
* <span data-ttu-id="b9369-392">Trascinare in seguito prefabs dal **Project** nel pannello **pennelli**</span><span class="sxs-lookup"><span data-stu-id="b9369-392">Drag following prefabs from the **Project** panel into **Brushes**</span></span>
    * <span data-ttu-id="b9369-393">Assets/AppPrefabs/**BrushFat**</span><span class="sxs-lookup"><span data-stu-id="b9369-393">Assets/AppPrefabs/**BrushFat**</span></span>
    * <span data-ttu-id="b9369-394">Assets/AppPrefabs/**BrushThin**</span><span class="sxs-lookup"><span data-stu-id="b9369-394">Assets/AppPrefabs/**BrushThin**</span></span>
    * <span data-ttu-id="b9369-395">Assets/AppPrefabs/**Eraser**</span><span class="sxs-lookup"><span data-stu-id="b9369-395">Assets/AppPrefabs/**Eraser**</span></span>
    * <span data-ttu-id="b9369-396">Assets/AppPrefabs/**MarkerFat**</span><span class="sxs-lookup"><span data-stu-id="b9369-396">Assets/AppPrefabs/**MarkerFat**</span></span>
    * <span data-ttu-id="b9369-397">Assets/AppPrefabs/**MarkerThin**</span><span class="sxs-lookup"><span data-stu-id="b9369-397">Assets/AppPrefabs/**MarkerThin**</span></span>
    * <span data-ttu-id="b9369-398">Assets/AppPrefabs/**Pencil**</span><span class="sxs-lookup"><span data-stu-id="b9369-398">Assets/AppPrefabs/**Pencil**</span></span>

![Pennelli](images/mixedreality213-brushes-250px.png)
* <span data-ttu-id="b9369-400">Fare clic su **MotionControllers** prefab nel **gerarchia** pannello.</span><span class="sxs-lookup"><span data-stu-id="b9369-400">Click **MotionControllers** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="b9369-401">Nel **Inspector** panel, deselezionare l'opzione **sempre utilizzo alternativo a destra del modello** sul **movimento Controller Visualizzatore**</span><span class="sxs-lookup"><span data-stu-id="b9369-401">In the **Inspector** panel, uncheck **Always Use Alternate Right Model** on the **Motion Controller Visualizer**</span></span>
* <span data-ttu-id="b9369-402">Nel **gerarchia** del pannello, fare clic su **BrushSelector**</span><span class="sxs-lookup"><span data-stu-id="b9369-402">In the **Hierarchy** panel, click **BrushSelector**</span></span>
* <span data-ttu-id="b9369-403">**BrushSelector** ha un campo denominato **ColorPicker**</span><span class="sxs-lookup"><span data-stu-id="b9369-403">**BrushSelector** has a field named **ColorPicker**</span></span>
* <span data-ttu-id="b9369-404">Dal **gerarchia** panel, trascinare le **ColorPickerWheel** in **ColorPicker** campo il **Inspector** pannello.</span><span class="sxs-lookup"><span data-stu-id="b9369-404">From the **Hierarchy** panel, drag the **ColorPickerWheel** into **ColorPicker** field in the **Inspector** panel.</span></span>

![Assegnare ColorPickerWheel al selettore del pennello](images/mr213-brushselector-500px.jpg)
* <span data-ttu-id="b9369-406">Nel **gerarchia** nel pannello **BrushSelector** prefab, selezionare il **Menu** oggetto.</span><span class="sxs-lookup"><span data-stu-id="b9369-406">In the **Hierarchy** panel, under **BrushSelector** prefab, select the **Menu** object.</span></span>
* <span data-ttu-id="b9369-407">Nel **Inspector** nel pannello il **LineObjectCollection** componente, aprire il **oggetti** matrice elenco a discesa.</span><span class="sxs-lookup"><span data-stu-id="b9369-407">In the **Inspector** panel, under the **LineObjectCollection** component, open the **Objects** array dropdown.</span></span> <span data-ttu-id="b9369-408">Si noterà 6 slot vuoto.</span><span class="sxs-lookup"><span data-stu-id="b9369-408">You will see 6 empty slots.</span></span>
* <span data-ttu-id="b9369-409">Dal **gerarchia** panel, trascinare ogni il prefabs impostata come figlio sotto il **pennelli** GameObject in questi slot in qualsiasi ordine.</span><span class="sxs-lookup"><span data-stu-id="b9369-409">From the **Hierarchy** panel, drag each of the prefabs parented under the **Brushes** GameObject into these slots in any order.</span></span> <span data-ttu-id="b9369-410">(Assicurarsi che si sta trascinando il prefabs dalla scena, non il prefabs nella cartella del progetto).</span><span class="sxs-lookup"><span data-stu-id="b9369-410">(Make sure you're dragging the prefabs from the scene, not the prefabs in the project folder.)</span></span>

![Selettore di pennello](images/mr213-brushselectorbrushes-700px.jpg)

<span data-ttu-id="b9369-412">**Prefab BrushSelector**</span><span class="sxs-lookup"><span data-stu-id="b9369-412">**BrushSelector prefab**</span></span>

<span data-ttu-id="b9369-413">Poiché il **BrushSelector** eredita **AttachToController**, Mostra **mano** e **elemento** le opzioni presenti nella  **Inspector** pannello.</span><span class="sxs-lookup"><span data-stu-id="b9369-413">Since the **BrushSelector** inherits **AttachToController**, it shows **Handedness** and **Element** options in the **Inspector** panel.</span></span> <span data-ttu-id="b9369-414">È stato selezionato **a destra** e **puntando comportare** per collegare gli strumenti di pennello per il controller a destra con direzione in avanti.</span><span class="sxs-lookup"><span data-stu-id="b9369-414">We selected **Right** and **Pointing Pose** to attach brush tools to the right hand controller with forward direction.</span></span>

<span data-ttu-id="b9369-415">Il **BrushSelector** usa due utilità:</span><span class="sxs-lookup"><span data-stu-id="b9369-415">The **BrushSelector** makes use of two utilities:</span></span>
* <span data-ttu-id="b9369-416">**Ellisse**: usato per generare i punti nello spazio lungo una forma di ellisse.</span><span class="sxs-lookup"><span data-stu-id="b9369-416">**Ellipse**: used to generate points in space along an ellipse shape.</span></span>
* <span data-ttu-id="b9369-417">**LineObjectCollection**: distribuisce gli oggetti utilizzando i punti generati da qualsiasi classe di riga (ad esempio, puntini di sospensione).</span><span class="sxs-lookup"><span data-stu-id="b9369-417">**LineObjectCollection**: distributes objects using the points generated by any Line class (eg, Ellipse).</span></span> <span data-ttu-id="b9369-418">Questo è ciò che verrà usato per inserire i pennelli lungo la forma di ellisse.</span><span class="sxs-lookup"><span data-stu-id="b9369-418">This is what we'll be using to place our brushes along the Ellipse shape.</span></span>

<span data-ttu-id="b9369-419">Insieme, queste utilità è utilizzabile per creare un menu radiale.</span><span class="sxs-lookup"><span data-stu-id="b9369-419">When combined, these utilities can be used to create a radial menu.</span></span>

<span data-ttu-id="b9369-420">**LineObjectCollection script**</span><span class="sxs-lookup"><span data-stu-id="b9369-420">**LineObjectCollection script**</span></span>

<span data-ttu-id="b9369-421">**LineObjectCollection** include controlli per la dimensione, posizione e la rotazione di oggetti distribuiti su una riga a sé.</span><span class="sxs-lookup"><span data-stu-id="b9369-421">**LineObjectCollection** has controls for the size, position and rotation of objects distributed along its line.</span></span> <span data-ttu-id="b9369-422">Ciò è utile per la creazione di menu radiali, ad esempio il selettore di pennello.</span><span class="sxs-lookup"><span data-stu-id="b9369-422">This is useful for creating radial menus like the brush selector.</span></span> <span data-ttu-id="b9369-423">Per creare l'aspetto dei pennelli scalabili da nothing stanno per raggiungere la posizione di center selezionato, il **ObjectScale** curva picchi al centro e tapers disattivata in corrispondenza dei bordi.</span><span class="sxs-lookup"><span data-stu-id="b9369-423">To create the appearance of brushes that scale up from nothing as they approach the center selected position, the **ObjectScale** curve peaks in the center and tapers off at the edges.</span></span>

<span data-ttu-id="b9369-424">**Script BrushSelector**</span><span class="sxs-lookup"><span data-stu-id="b9369-424">**BrushSelector script**</span></span>

<span data-ttu-id="b9369-425">Nel caso del **BrushSelector**, abbiamo scelto di utilizzare l'animazione procedurale.</span><span class="sxs-lookup"><span data-stu-id="b9369-425">In the case of the **BrushSelector**, we've chosen to use procedural animation.</span></span> <span data-ttu-id="b9369-426">In primo luogo, vengono distribuiti i modelli pennello un'ellisse per il **LineObjectCollection** script.</span><span class="sxs-lookup"><span data-stu-id="b9369-426">First, brush models are distributed in an ellipse by the **LineObjectCollection** script.</span></span> <span data-ttu-id="b9369-427">Quindi, ogni pennello è responsabile della propria posizione a disposizione dell'utente in base relativa **DisplayMode** valore, che cambia in base alla selezione.</span><span class="sxs-lookup"><span data-stu-id="b9369-427">Then, each brush is responsible for maintaining its position in the user's hand based on its **DisplayMode** value, which changes based on the selection.</span></span> <span data-ttu-id="b9369-428">Abbiamo scelto un approccio procedurale a causa di elevata probabilità delle transizioni di posizione pennello viene interrotto, in quanto l'utente seleziona i pennelli.</span><span class="sxs-lookup"><span data-stu-id="b9369-428">We chose a procedural approach because of the high probability of brush position transitions being interrupted as the user selects brushes.</span></span> <span data-ttu-id="b9369-429">Animazioni Mecanim possono gestire le interruzioni correttamente, ma tende a essere più complesso rispetto a una semplice operazione Lerp.</span><span class="sxs-lookup"><span data-stu-id="b9369-429">Mecanim animations can handle interruptions gracefully, but it tends to be more complicated than a simple Lerp operation.</span></span>

<span data-ttu-id="b9369-430">**BrushSelector** Usa una combinazione di entrambi.</span><span class="sxs-lookup"><span data-stu-id="b9369-430">**BrushSelector** uses a combination of both.</span></span> <span data-ttu-id="b9369-431">Quando viene rilevato l'input touchpad, le opzioni diventano visibili e scalabilità verticale lungo il menu radiale.</span><span class="sxs-lookup"><span data-stu-id="b9369-431">When touchpad input is detected, brush options become visible and scale up along the radial menu.</span></span> <span data-ttu-id="b9369-432">Dopo un periodo di timeout, che indica che l'utente ha effettuato una selezione, il pennello Opzioni scala verso il basso anche in questo caso, lasciando solo del pennello selezionato.</span><span class="sxs-lookup"><span data-stu-id="b9369-432">After a timeout period (which indicates that the user has made a selection) the brush options scale down again, leaving only the selected brush.</span></span>

<span data-ttu-id="b9369-433">**La visualizzazione input touchpad**</span><span class="sxs-lookup"><span data-stu-id="b9369-433">**Visualizing touchpad input**</span></span>

<span data-ttu-id="b9369-434">Anche nei casi in cui il modello di controller è stato completamente sostituito, può essere utile visualizzare input sull'input del modello originale.</span><span class="sxs-lookup"><span data-stu-id="b9369-434">Even in cases where the controller model has been completely replaced, it can be helpful to show input on the original model inputs.</span></span> <span data-ttu-id="b9369-435">Ciò consente di forzare a terra in realtà le azioni dell'utente.</span><span class="sxs-lookup"><span data-stu-id="b9369-435">This helps to ground the user's actions in reality.</span></span> <span data-ttu-id="b9369-436">Per il **BrushSelector** abbiamo scelto di rendere il touchpad brevemente visibile quando viene ricevuto l'input.</span><span class="sxs-lookup"><span data-stu-id="b9369-436">For the **BrushSelector** we've chosen to make the touchpad briefly visible when the input is received.</span></span> <span data-ttu-id="b9369-437">Tale operazione viene eseguita recuperando l'elemento Touchpad dal controller, sostituendo il materiale con un materiale personalizzato, quindi applicare una sfumatura di colore del materiale tale basata il touchpad ora ultimo stato ricevuto l'input.</span><span class="sxs-lookup"><span data-stu-id="b9369-437">This was done by retrieving the Touchpad element from the controller, replacing its material with a custom material, then applying a gradient to that material's color based on the last time touchpad input was received.</span></span>

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

<span data-ttu-id="b9369-438">**Pennello di selezione degli strumenti con input touchpad**</span><span class="sxs-lookup"><span data-stu-id="b9369-438">**Brush tool selection with touchpad input**</span></span>

<span data-ttu-id="b9369-439">Quando il selettore di pennello rileva un input premuto del touchpad, controlla la posizione dell'input per stabilire se questo è a sinistra o destra.</span><span class="sxs-lookup"><span data-stu-id="b9369-439">When the brush selector detects touchpad's pressed input, it checks the position of the input to determine if it was to the left or right.</span></span>

<span data-ttu-id="b9369-440">**Spessore del tratto con selectPressedAmount**</span><span class="sxs-lookup"><span data-stu-id="b9369-440">**Stroke thickness with selectPressedAmount**</span></span>

<span data-ttu-id="b9369-441">Anziché il **InteractionSourcePressType.Select** evento nel **InteractionSourcePressed()**, è possibile ottenere il valore della quantità premuto tramite analogico **selectPressedAmount**.</span><span class="sxs-lookup"><span data-stu-id="b9369-441">Instead of the **InteractionSourcePressType.Select** event in the **InteractionSourcePressed()**, you can get the analog value of the pressed amount through **selectPressedAmount**.</span></span> <span data-ttu-id="b9369-442">Questo valore può essere recuperato **InteractionSourceUpdated()**.</span><span class="sxs-lookup"><span data-stu-id="b9369-442">This value can be retrieved in **InteractionSourceUpdated()**.</span></span>

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

<span data-ttu-id="b9369-443">**Script di gomma**</span><span class="sxs-lookup"><span data-stu-id="b9369-443">**Eraser script**</span></span>

<span data-ttu-id="b9369-444">**Gomma** è un tipo speciale di pennello che esegue l'override della base **pennello**del **DrawOverTime()** (funzione).</span><span class="sxs-lookup"><span data-stu-id="b9369-444">**Eraser** is a special type of brush that overrides the base **Brush**'s **DrawOverTime()** function.</span></span> <span data-ttu-id="b9369-445">Mentre disegno è true, la gomma controlla se il suggerimento si interseca con tutte le tracce di pennello esistente.</span><span class="sxs-lookup"><span data-stu-id="b9369-445">While Draw is true, the eraser checks to see if its tip intersects with any existing brush strokes.</span></span> <span data-ttu-id="b9369-446">In caso affermativo, vengono aggiunti a una coda che si desidera compattare verso il basso ed eliminati.</span><span class="sxs-lookup"><span data-stu-id="b9369-446">If it does, they are added to a queue to be shrunk down and deleted.</span></span>

## <a name="advanced-design---teleportation-and-locomotion"></a><span data-ttu-id="b9369-447">Progettazione avanzata - teletrasporto e locomotion</span><span class="sxs-lookup"><span data-stu-id="b9369-447">Advanced design - Teleportation and locomotion</span></span>

<span data-ttu-id="b9369-448">Se si vuole consentire all'utente di spostarsi all'interno della scena con teletrasporto usando thumbstick, usare **MixedRealityCameraParent** invece di **MixedRealityCamera**.</span><span class="sxs-lookup"><span data-stu-id="b9369-448">If you want to allow the user to move around the scene with teleportation using thumbstick, use **MixedRealityCameraParent** instead of **MixedRealityCamera**.</span></span> <span data-ttu-id="b9369-449">È inoltre necessario aggiungere **InputManager** e **DefaultCusor**.</span><span class="sxs-lookup"><span data-stu-id="b9369-449">You also need to add **InputManager** and **DefaultCusor**.</span></span> <span data-ttu-id="b9369-450">Poiché **MixedRealityCameraParent** include già **MotionControllers** e **limite** come componenti figlio, è necessario rimuovere esistente  **MotionControllers** e **ambiente** prefab.</span><span class="sxs-lookup"><span data-stu-id="b9369-450">Since **MixedRealityCameraParent** already includes **MotionControllers** and **Boundary** as child components, you should remove existing **MotionControllers** and **Environment** prefab.</span></span>

### <a name="instructions"></a><span data-ttu-id="b9369-451">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="b9369-451">Instructions</span></span>

* <span data-ttu-id="b9369-452">Nel **gerarchia** panel, eliminare **MixedRealityCamera**, **ambiente** e **MotionControllers**</span><span class="sxs-lookup"><span data-stu-id="b9369-452">In the **Hierarchy** panel, delete **MixedRealityCamera**, **Environment** and **MotionControllers**</span></span>
* <span data-ttu-id="b9369-453">Dal **pannello progetto**, la ricerca e trascinare il prefabs seguenti nel **gerarchia** pannello:</span><span class="sxs-lookup"><span data-stu-id="b9369-453">From the **Project panel**, search and drag the following prefabs into the **Hierarchy** panel:</span></span>
    * <span data-ttu-id="b9369-454">Assets/AppPrefabs/Input/Prefabs/**MixedRealityCameraParent**</span><span class="sxs-lookup"><span data-stu-id="b9369-454">Assets/AppPrefabs/Input/Prefabs/**MixedRealityCameraParent**</span></span>
    * <span data-ttu-id="b9369-455">Assets/AppPrefabs/Input/Prefabs/**InputManager**</span><span class="sxs-lookup"><span data-stu-id="b9369-455">Assets/AppPrefabs/Input/Prefabs/**InputManager**</span></span>
    * <span data-ttu-id="b9369-456">Assets/AppPrefabs/Input/Prefabs/Cursor/**DefaultCursor**</span><span class="sxs-lookup"><span data-stu-id="b9369-456">Assets/AppPrefabs/Input/Prefabs/Cursor/**DefaultCursor**</span></span>

![Realtà mista fotocamera padre](images/mr213-cameraparent-300px.png)
* <span data-ttu-id="b9369-458">Nel **gerarchia** del pannello, fare clic su **Input Manager**</span><span class="sxs-lookup"><span data-stu-id="b9369-458">In the **Hierarchy** panel, click **Input Manager**</span></span>
* <span data-ttu-id="b9369-459">Nel **Inspector** panel, scorrere verso il basso il **semplice selettore puntatore singolo** sezione</span><span class="sxs-lookup"><span data-stu-id="b9369-459">In the **Inspector** panel, scroll down to the **Simple Single Pointer Selector** section</span></span>
* <span data-ttu-id="b9369-460">Dal **gerarchia** panel, trascinare **DefaultCursor** nelle **cursore** campo</span><span class="sxs-lookup"><span data-stu-id="b9369-460">From the **Hierarchy** panel, drag **DefaultCursor** into **Cursor** field</span></span>

![Assegnazione di DefaultCursor](images/mr213-defaultcursor-500px.png)
* <span data-ttu-id="b9369-462">**Salvare** di scena e selezionare il **Riproduci** pulsante.</span><span class="sxs-lookup"><span data-stu-id="b9369-462">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="b9369-463">Sarà possibile usare il thumbstick la rotazione a sinistra/destra o teleport.</span><span class="sxs-lookup"><span data-stu-id="b9369-463">You will be able to use the thumbstick to rotate left/right or teleport.</span></span>

## <a name="the-end"></a><span data-ttu-id="b9369-464">La fine</span><span class="sxs-lookup"><span data-stu-id="b9369-464">The end</span></span>

<span data-ttu-id="b9369-465">E questo è il termine di questa esercitazione.</span><span class="sxs-lookup"><span data-stu-id="b9369-465">And that's the end of this tutorial!</span></span> <span data-ttu-id="b9369-466">Si è appreso:</span><span class="sxs-lookup"><span data-stu-id="b9369-466">You learned:</span></span>
* <span data-ttu-id="b9369-467">Come lavorare con i modelli di controller di movimento in modalità di gioco e runtime di Unity.</span><span class="sxs-lookup"><span data-stu-id="b9369-467">How to work with motion controller models in Unity's game mode and runtime.</span></span>
* <span data-ttu-id="b9369-468">Come usare diversi tipi di eventi del pulsante e le relative applicazioni.</span><span class="sxs-lookup"><span data-stu-id="b9369-468">How to use different types of button events and their applications.</span></span>
* <span data-ttu-id="b9369-469">Procedure per sovrapporre gli elementi dell'interfaccia utente nella parte superiore del controller o completamente personalizzarlo.</span><span class="sxs-lookup"><span data-stu-id="b9369-469">How to overlay UI elements on top of the controller or fully customize it.</span></span>

<span data-ttu-id="b9369-470">Si è ora pronti per iniziare a creare un'esperienza coinvolgente e concreto con i controller di movimento.</span><span class="sxs-lookup"><span data-stu-id="b9369-470">You are now ready to start creating your own immersive experience with motion controllers!</span></span>

## <a name="completed-scenes"></a><span data-ttu-id="b9369-471">Scene completate</span><span class="sxs-lookup"><span data-stu-id="b9369-471">Completed scenes</span></span>

* <span data-ttu-id="b9369-472">Nella finestra di Unity **Project** pannello fare clic sui **scene** cartella.</span><span class="sxs-lookup"><span data-stu-id="b9369-472">In Unity's **Project** panel click on the **Scenes** folder.</span></span>
* <span data-ttu-id="b9369-473">Sono disponibili due Unity sceens **MixedReality213** e **MixedReality213Advanced**.</span><span class="sxs-lookup"><span data-stu-id="b9369-473">You will find two Unity sceens **MixedReality213** and **MixedReality213Advanced**.</span></span>
    * <span data-ttu-id="b9369-474">**MixedReality213**: Completato scena con pennello singolo</span><span class="sxs-lookup"><span data-stu-id="b9369-474">**MixedReality213**: Completed scene with single brush</span></span>
    * <span data-ttu-id="b9369-475">**MixedReality213Advanced**: Completato scena con più pennello con esempio di quantità pressione del pulsante di selezione</span><span class="sxs-lookup"><span data-stu-id="b9369-475">**MixedReality213Advanced**: Completed scene with multiple brush with select button's press amount example</span></span>

## <a name="see-also"></a><span data-ttu-id="b9369-476">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b9369-476">See also</span></span>

* [<span data-ttu-id="b9369-477">File di progetto MR Input 213</span><span class="sxs-lookup"><span data-stu-id="b9369-477">MR Input 213 project files</span></span>](https://github.com/Microsoft/MixedReality213)
* [<span data-ttu-id="b9369-478">Toolkit di realtà mista - scena movimento Controller Test</span><span class="sxs-lookup"><span data-stu-id="b9369-478">Mixed Reality Toolkit - Motion Controller Test scene</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [<span data-ttu-id="b9369-479">Toolkit di realtà mista - Mechanics quadratini di ridimensionamento</span><span class="sxs-lookup"><span data-stu-id="b9369-479">Mixed Reality Toolkit - Grab Mechanics</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [<span data-ttu-id="b9369-480">Linee guida sullo sviluppo di controller di movimento</span><span class="sxs-lookup"><span data-stu-id="b9369-480">Motion controller development guidelines</span></span>](motion-controllers.md)

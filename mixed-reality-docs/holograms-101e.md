---
title: Nozioni di base su 101E-completare il progetto con l'emulatore
description: Seguire questa procedura dettagliata di codifica usando Unity, Visual Studio e l'emulatore HoloLens per apprendere le nozioni di base di un'applicazione olografica.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: realtà mista, realtà mista di Windows, HoloLens, ologramma, Accademia, esercitazione, emulatore
ms.openlocfilehash: b1d8e1f3f272051bdd6f69ab88c3aef4f86f13ef
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434709"
---
>[!NOTE]
><span data-ttu-id="5327b-104">Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.</span><span class="sxs-lookup"><span data-stu-id="5327b-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="5327b-105">Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.</span><span class="sxs-lookup"><span data-stu-id="5327b-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="5327b-106">Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5327b-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="5327b-107">Verranno mantenuti per continuare a usare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="5327b-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="5327b-108">Per HoloLens 2 è stata pubblicata [una nuova serie di esercitazioni](mrlearning-base.md) .</span><span class="sxs-lookup"><span data-stu-id="5327b-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

# <a name="mr-basics-101e-complete-project-with-emulator"></a><span data-ttu-id="5327b-109">Nozioni di base su 101E: completare il progetto con l'emulatore</span><span class="sxs-lookup"><span data-stu-id="5327b-109">MR Basics 101E: Complete project with emulator</span></span>

 >[!VIDEO https://www.youtube.com/embed/Xzm8_s05mm8]

<span data-ttu-id="5327b-110">Questa esercitazione illustra in dettaglio un progetto completo, integrato in Unity, che illustra le funzionalità di base della realtà mista di Windows su HoloLens, tra cui lo [sguardo](gaze-and-commit.md), i [movimenti](gaze-and-commit.md#composite-gestures), l' [input vocale](voice-input.md), il mapping di [suoni spaziali](spatial-sound.md) e [spaziali](spatial-mapping.md) .</span><span class="sxs-lookup"><span data-stu-id="5327b-110">This tutorial will walk you through a complete project, built in Unity, that demonstrates core Windows Mixed Reality features on HoloLens including [gaze](gaze-and-commit.md), [gestures](gaze-and-commit.md#composite-gestures), [voice input](voice-input.md), [spatial sound](spatial-sound.md) and [spatial mapping](spatial-mapping.md).</span></span> <span data-ttu-id="5327b-111">Il completamento dell'esercitazione richiede circa 1 ora.</span><span class="sxs-lookup"><span data-stu-id="5327b-111">The tutorial will take approximately 1 hour to complete.</span></span>

## <a name="device-support"></a><span data-ttu-id="5327b-112">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="5327b-112">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="5327b-113">Corso</span><span class="sxs-lookup"><span data-stu-id="5327b-113">Course</span></span></th><th style="width:150px"> <span data-ttu-id="5327b-114"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="5327b-114"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="5327b-115"><a href="immersive-headset-hardware-details.md">Visori VR immersive</a></span><span class="sxs-lookup"><span data-stu-id="5327b-115"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="5327b-116">Nozioni di base su 101E: completare il progetto con l'emulatore</span><span class="sxs-lookup"><span data-stu-id="5327b-116">MR Basics 101E: Complete project with emulator</span></span></td><td style="text-align: center;"> <span data-ttu-id="5327b-117">✔️</span><span class="sxs-lookup"><span data-stu-id="5327b-117">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="5327b-118">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="5327b-118">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="5327b-119">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="5327b-119">Prerequisites</span></span>

* <span data-ttu-id="5327b-120">Un PC Windows 10 configurato con gli [strumenti corretti installati](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="5327b-120">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>

### <a name="project-files"></a><span data-ttu-id="5327b-121">File di progetto</span><span class="sxs-lookup"><span data-stu-id="5327b-121">Project files</span></span>

* <span data-ttu-id="5327b-122">Scaricare i [file](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) richiesti dal progetto.</span><span class="sxs-lookup"><span data-stu-id="5327b-122">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) required by the project.</span></span><span data-ttu-id="5327b-123"> Richiede Unity 2017,2 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="5327b-123"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="5327b-124">Se è ancora necessario il supporto per Unity 5,6, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span><span class="sxs-lookup"><span data-stu-id="5327b-124">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span></span>
  * <span data-ttu-id="5327b-125">Se è ancora necessario il supporto per Unity 5,5, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span><span class="sxs-lookup"><span data-stu-id="5327b-125">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span></span>
  * <span data-ttu-id="5327b-126">Se è ancora necessario il supporto per Unity 5,4, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span><span class="sxs-lookup"><span data-stu-id="5327b-126">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span></span>
* <span data-ttu-id="5327b-127">Annullare l'archiviazione dei file sul desktop o in un'altra posizione facile da raggiungere.</span><span class="sxs-lookup"><span data-stu-id="5327b-127">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="5327b-128">Mantiene il nome della cartella come **origami**.</span><span class="sxs-lookup"><span data-stu-id="5327b-128">Keep the folder name as **Origami**.</span></span>

>[!NOTE]
><span data-ttu-id="5327b-129">Se si vuole esaminare il codice sorgente prima del download, è [disponibile in GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span><span class="sxs-lookup"><span data-stu-id="5327b-129">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="5327b-130">Capitolo 1-"Holo" World</span><span class="sxs-lookup"><span data-stu-id="5327b-130">Chapter 1 - "Holo" world</span></span>

>[!VIDEO https://www.youtube.com/embed/qotpUpIQxVU]

<span data-ttu-id="5327b-131">In questo capitolo verrà configurato il primo progetto Unity ed eseguiamo il processo di compilazione e distribuzione.</span><span class="sxs-lookup"><span data-stu-id="5327b-131">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="5327b-132">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="5327b-132">Objectives</span></span>

* <span data-ttu-id="5327b-133">Configurare Unity per lo sviluppo olografico.</span><span class="sxs-lookup"><span data-stu-id="5327b-133">Set up Unity for holographic development.</span></span>
* <span data-ttu-id="5327b-134">Creare un ologramma.</span><span class="sxs-lookup"><span data-stu-id="5327b-134">Make a hologram.</span></span>
* <span data-ttu-id="5327b-135">Vedere un ologramma creato.</span><span class="sxs-lookup"><span data-stu-id="5327b-135">See a hologram that you made.</span></span>

### <a name="instructions"></a><span data-ttu-id="5327b-136">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="5327b-136">Instructions</span></span>

* <span data-ttu-id="5327b-137">Avvia Unity.</span><span class="sxs-lookup"><span data-stu-id="5327b-137">Start Unity.</span></span>
* <span data-ttu-id="5327b-138">Selezionare **Apri**.</span><span class="sxs-lookup"><span data-stu-id="5327b-138">Select **Open**.</span></span>
* <span data-ttu-id="5327b-139">Immettere il percorso come cartella **origami** precedentemente non archiviata.</span><span class="sxs-lookup"><span data-stu-id="5327b-139">Enter location as the **Origami** folder you previously un-archived.</span></span>
* <span data-ttu-id="5327b-140">Selezionare **origami** e fare clic su **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="5327b-140">Select **Origami** and click **Select Folder**.</span></span>
* <span data-ttu-id="5327b-141">Salvare la nuova scena: **File** / **Salva scena con nome**.</span><span class="sxs-lookup"><span data-stu-id="5327b-141">Save the new scene: **File** / **Save Scene As**.</span></span>
* <span data-ttu-id="5327b-142">Assegnare un nome alla scena **origami** e premere il pulsante **Salva** .</span><span class="sxs-lookup"><span data-stu-id="5327b-142">Name the scene **Origami** and press the **Save** button.</span></span>

#### <a name="setup-the-main-camera"></a><span data-ttu-id="5327b-143">Configurare la fotocamera principale</span><span class="sxs-lookup"><span data-stu-id="5327b-143">Setup the main camera</span></span>

* <span data-ttu-id="5327b-144">Nel **Pannello gerarchia**selezionare **Main camera**.</span><span class="sxs-lookup"><span data-stu-id="5327b-144">In the **Hierarchy Panel**, select **Main Camera**.</span></span>
* <span data-ttu-id="5327b-145">Nel **controllo** impostare la relativa posizione di trasformazione su **0, 0, 0**.</span><span class="sxs-lookup"><span data-stu-id="5327b-145">In the **Inspector** set its transform position to **0,0,0**.</span></span>
* <span data-ttu-id="5327b-146">Trovare la proprietà **Clear Flags** e modificare l'elenco a discesa da **SKYBOX** a **tinta unita**.</span><span class="sxs-lookup"><span data-stu-id="5327b-146">Find the **Clear Flags** property, and change the dropdown from **Skybox** to **Solid color**.</span></span>
* <span data-ttu-id="5327b-147">Fare clic sul campo **sfondo** per aprire una selezione colori.</span><span class="sxs-lookup"><span data-stu-id="5327b-147">Click on the **Background** field to open a color picker.</span></span>
* <span data-ttu-id="5327b-148">Impostare **R, G, B e** a su **0**.</span><span class="sxs-lookup"><span data-stu-id="5327b-148">Set **R, G, B, and A** to **0**.</span></span>

#### <a name="setup-the-scene"></a><span data-ttu-id="5327b-149">Configurare la scena</span><span class="sxs-lookup"><span data-stu-id="5327b-149">Setup the scene</span></span>

* <span data-ttu-id="5327b-150">Nel **Pannello gerarchia**fare clic su **Crea** e **Crea vuoto**.</span><span class="sxs-lookup"><span data-stu-id="5327b-150">In the **Hierarchy Panel**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="5327b-151">Fare clic con il pulsante destro del mouse sul nuovo **GameObject** e scegliere Rinomina.</span><span class="sxs-lookup"><span data-stu-id="5327b-151">Right-click the new **GameObject** and select Rename.</span></span> <span data-ttu-id="5327b-152">Rinominare GameObject in **origamicollection**.</span><span class="sxs-lookup"><span data-stu-id="5327b-152">Rename the GameObject to **OrigamiCollection**.</span></span>
* <span data-ttu-id="5327b-153">Dalla cartella **ologrammi** nel pannello del **progetto**:</span><span class="sxs-lookup"><span data-stu-id="5327b-153">From the **Holograms** folder in the **Project Panel**:</span></span>
  * <span data-ttu-id="5327b-154">Trascinare la **fase** nella gerarchia in modo che sia un elemento figlio di **origamicollection**.</span><span class="sxs-lookup"><span data-stu-id="5327b-154">Drag **Stage** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="5327b-155">Trascinare **Sphere1** nella gerarchia in modo che sia un elemento figlio di **origamicollection**.</span><span class="sxs-lookup"><span data-stu-id="5327b-155">Drag **Sphere1** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="5327b-156">Trascinare **Sphere2** nella gerarchia in modo che sia un elemento figlio di **origamicollection**.</span><span class="sxs-lookup"><span data-stu-id="5327b-156">Drag **Sphere2** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="5327b-157">Fare clic con il pulsante destro del mouse sull'oggetto **direzionale chiaro** nel **Pannello gerarchia** e scegliere **Elimina**.</span><span class="sxs-lookup"><span data-stu-id="5327b-157">Right-click the **Directional Light** object in the **Hierarchy Panel** and select **Delete**.</span></span>
* <span data-ttu-id="5327b-158">Dalla cartella **ologrammi** trascinare le **spie** nella radice del **Pannello gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="5327b-158">From the **Holograms** folder, drag **Lights** into the root of the **Hierarchy Panel**.</span></span>
* <span data-ttu-id="5327b-159">Nella **gerarchia**selezionare **origamicollection**.</span><span class="sxs-lookup"><span data-stu-id="5327b-159">In the **Hierarchy**, select the **OrigamiCollection**.</span></span>
* <span data-ttu-id="5327b-160">Nel **controllo**impostare la posizione di trasformazione su **0,-0,5, 2,0**.</span><span class="sxs-lookup"><span data-stu-id="5327b-160">In the **Inspector**, set the transform position to **0, -0.5, 2.0**.</span></span>
* <span data-ttu-id="5327b-161">Premere il pulsante **Play** in Unity per visualizzare l'anteprima degli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="5327b-161">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="5327b-162">Nella finestra di anteprima verranno visualizzati gli oggetti origami.</span><span class="sxs-lookup"><span data-stu-id="5327b-162">You should see the Origami objects in the preview window.</span></span>
* <span data-ttu-id="5327b-163">Premere **Riproduci** una seconda volta per arrestare la modalità di anteprima.</span><span class="sxs-lookup"><span data-stu-id="5327b-163">Press **Play** a second time to stop preview mode.</span></span>

#### <a name="export-the-project-from-unity-to-visual-studio"></a><span data-ttu-id="5327b-164">Esportare il progetto da Unity a Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5327b-164">Export the project from Unity to Visual Studio</span></span>

* <span data-ttu-id="5327b-165">In Unity selezionare **File > impostazioni di compilazione**.</span><span class="sxs-lookup"><span data-stu-id="5327b-165">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="5327b-166">Selezionare **Windows Store** nell'elenco **piattaforma** e fare clic su **Cambia piattaforma**.</span><span class="sxs-lookup"><span data-stu-id="5327b-166">Select **Windows Store** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="5327b-167">Impostare **SDK** su **Universal 10** e **tipo di compilazione** su **D3D**.</span><span class="sxs-lookup"><span data-stu-id="5327b-167">Set **SDK** to **Universal 10** and **Build Type** to **D3D**.</span></span>
* <span data-ttu-id="5327b-168">Controllare **i C# progetti Unity**.</span><span class="sxs-lookup"><span data-stu-id="5327b-168">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="5327b-169">Fare clic su **Aggiungi scene aperte** per aggiungere la scena.</span><span class="sxs-lookup"><span data-stu-id="5327b-169">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="5327b-170">Fare clic su **Impostazioni lettore...** .</span><span class="sxs-lookup"><span data-stu-id="5327b-170">Click **Player Settings...**.</span></span>
* <span data-ttu-id="5327b-171">Nel pannello Inspector selezionare il **logo di Windows Store**.</span><span class="sxs-lookup"><span data-stu-id="5327b-171">In the Inspector Panel select the **Windows Store logo**.</span></span> <span data-ttu-id="5327b-172">Quindi selezionare **impostazioni di pubblicazione**.</span><span class="sxs-lookup"><span data-stu-id="5327b-172">Then select **Publishing Settings**.</span></span>
* <span data-ttu-id="5327b-173">Nella sezione **funzionalità** selezionare le funzionalità **Microphone** e **SpatialPerception** .</span><span class="sxs-lookup"><span data-stu-id="5327b-173">In the **Capabilities** section, select the **Microphone** and **SpatialPerception** capabilities.</span></span>
* <span data-ttu-id="5327b-174">Tornare alla finestra Impostazioni compilazione, fare clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="5327b-174">Back in the Build Settings window, click **Build**.</span></span>
* <span data-ttu-id="5327b-175">Creare una **nuova cartella** denominata "app".</span><span class="sxs-lookup"><span data-stu-id="5327b-175">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="5327b-176">Fare clic sulla **cartella dell'app**.</span><span class="sxs-lookup"><span data-stu-id="5327b-176">Single click the **App Folder**.</span></span>
* <span data-ttu-id="5327b-177">Premere **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="5327b-177">Press **Select Folder**.</span></span>
* <span data-ttu-id="5327b-178">Quando si esegue Unity, viene visualizzata una finestra Esplora file.</span><span class="sxs-lookup"><span data-stu-id="5327b-178">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="5327b-179">Aprire la cartella dell' **app** .</span><span class="sxs-lookup"><span data-stu-id="5327b-179">Open the **App** folder.</span></span>
* <span data-ttu-id="5327b-180">Aprire la **soluzione origami di Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="5327b-180">Open the **Origami Visual Studio Solution**.</span></span>
* <span data-ttu-id="5327b-181">Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione da debug a **Release** e da ARM a **x86**.</span><span class="sxs-lookup"><span data-stu-id="5327b-181">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
  * <span data-ttu-id="5327b-182">Fare clic sulla freccia accanto al pulsante Device (dispositivo) e selezionare **HoloLens Emulator (emulatore**).</span><span class="sxs-lookup"><span data-stu-id="5327b-182">Click on the arrow next to the Device button, and select **HoloLens Emulator**.</span></span>
  * <span data-ttu-id="5327b-183">Fare clic su **debug-> avvia senza eseguire debug** o premere **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="5327b-183">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
  * <span data-ttu-id="5327b-184">Dopo un po' di tempo l'emulatore inizierà con il progetto origami.</span><span class="sxs-lookup"><span data-stu-id="5327b-184">After some time the emulator will start with the Origami project.</span></span> <span data-ttu-id="5327b-185">Quando l' [emulatore](using-the-hololens-emulator.md)viene avviato per la prima volta, possono essere necessari fino a 15 minuti per l'avvio dell'emulatore.</span><span class="sxs-lookup"><span data-stu-id="5327b-185">When first launching the [emulator](using-the-hololens-emulator.md), it can take as long as 15 minutes for the emulator to start up.</span></span> <span data-ttu-id="5327b-186">Una volta avviata, non chiuderla.</span><span class="sxs-lookup"><span data-stu-id="5327b-186">Once it starts, do not close it.</span></span>

## <a name="chapter-2---gaze"></a><span data-ttu-id="5327b-187">Capitolo 2: sguardo</span><span class="sxs-lookup"><span data-stu-id="5327b-187">Chapter 2 - Gaze</span></span>

>[!VIDEO https://www.youtube.com/embed/BPWTbAC210k]

<span data-ttu-id="5327b-188">In questo capitolo, verranno introdotti i primi tre modi per interagire con gli ologrammi [.](gaze-and-commit.md)</span><span class="sxs-lookup"><span data-stu-id="5327b-188">In this chapter, we are going to introduce the first of three ways of interacting with your holograms -- [gaze](gaze-and-commit.md).</span></span>

### <a name="objectives"></a><span data-ttu-id="5327b-189">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="5327b-189">Objectives</span></span>

* <span data-ttu-id="5327b-190">Visualizza lo sguardo usando un cursore con blocco globale.</span><span class="sxs-lookup"><span data-stu-id="5327b-190">Visualize your gaze using a world-locked cursor.</span></span>

### <a name="instructions"></a><span data-ttu-id="5327b-191">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="5327b-191">Instructions</span></span>

* <span data-ttu-id="5327b-192">Tornare al progetto Unity e chiudere la finestra impostazioni di compilazione se è ancora aperta.</span><span class="sxs-lookup"><span data-stu-id="5327b-192">Go back to your Unity project, and close the Build Settings window if it's still open.</span></span>
* <span data-ttu-id="5327b-193">Selezionare la cartella **ologrammi** nel **Pannello del progetto**.</span><span class="sxs-lookup"><span data-stu-id="5327b-193">Select the **Holograms** folder in the **Project panel**.</span></span>
* <span data-ttu-id="5327b-194">Trascinare l'oggetto **cursore** nel **Pannello gerarchia** a livello di radice.</span><span class="sxs-lookup"><span data-stu-id="5327b-194">Drag the **Cursor** object into the **Hierarchy panel** at the root level.</span></span>
* <span data-ttu-id="5327b-195">Fare doppio clic sull'oggetto **cursore** per esaminarlo più da vicino.</span><span class="sxs-lookup"><span data-stu-id="5327b-195">Double-click on the **Cursor** object to take a closer look at it.</span></span>
* <span data-ttu-id="5327b-196">Fare clic con il pulsante destro del mouse sulla cartella **Scripts** nel pannello Project.</span><span class="sxs-lookup"><span data-stu-id="5327b-196">Right-click on the **Scripts** folder in the Project panel.</span></span>
* <span data-ttu-id="5327b-197">Fare clic sul sottomenu **Crea** .</span><span class="sxs-lookup"><span data-stu-id="5327b-197">Click the **Create** sub-menu.</span></span>
* <span data-ttu-id="5327b-198">Selezionare  **C# script**.</span><span class="sxs-lookup"><span data-stu-id="5327b-198">Select **C# Script**.</span></span>
* <span data-ttu-id="5327b-199">Denominare lo script **WorldCursor**.</span><span class="sxs-lookup"><span data-stu-id="5327b-199">Name the script **WorldCursor**.</span></span> <span data-ttu-id="5327b-200">Nota: il nome fa distinzione tra maiuscole e minuscole.</span><span class="sxs-lookup"><span data-stu-id="5327b-200">Note: The name is case-sensitive.</span></span> <span data-ttu-id="5327b-201">Non è necessario aggiungere l'estensione. cs.</span><span class="sxs-lookup"><span data-stu-id="5327b-201">You do not need to add the .cs extension.</span></span>
* <span data-ttu-id="5327b-202">Selezionare l'oggetto **cursore** nel **Pannello gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="5327b-202">Select the **Cursor** object in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="5327b-203">Trascinare e rilasciare lo script **WorldCursor** nel **pannello Inspector**.</span><span class="sxs-lookup"><span data-stu-id="5327b-203">Drag and drop the **WorldCursor** script into the **Inspector panel**.</span></span>
* <span data-ttu-id="5327b-204">Fare doppio clic sullo script **WorldCursor** per aprirlo in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5327b-204">Double-click the **WorldCursor** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="5327b-205">Copiare e incollare questo codice in **WorldCursor.cs** e **salvare tutti**.</span><span class="sxs-lookup"><span data-stu-id="5327b-205">Copy and paste this code into **WorldCursor.cs** and **Save All**.</span></span>

```cs
using UnityEngine;

public class WorldCursor : MonoBehaviour
{
    private MeshRenderer meshRenderer;

    // Use this for initialization
    void Start()
    {
        // Grab the mesh renderer that's on the same object as this script.
        meshRenderer = this.gameObject.GetComponentInChildren<MeshRenderer>();
    }

    // Update is called once per frame
    void Update()
    {
        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;

        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram...
            // Display the cursor mesh.
            meshRenderer.enabled = true;

            // Move thecursor to the point where the raycast hit.
            this.transform.position = hitInfo.point;

            // Rotate the cursor to hug the surface of the hologram.
            this.transform.rotation = Quaternion.FromToRotation(Vector3.up, hitInfo.normal);
        }
        else
        {
            // If the raycast did not hit a hologram, hide the cursor mesh.
            meshRenderer.enabled = false;
        }
    }
}
```

* <span data-ttu-id="5327b-206">Ricompilare l'app da **File > impostazioni di compilazione**.</span><span class="sxs-lookup"><span data-stu-id="5327b-206">Rebuild the app from **File > Build Settings**.</span></span>
* <span data-ttu-id="5327b-207">Tornare alla soluzione di Visual Studio usata in precedenza per la distribuzione nell'emulatore.</span><span class="sxs-lookup"><span data-stu-id="5327b-207">Return to the Visual Studio solution previously used to deploy to the emulator.</span></span>
* <span data-ttu-id="5327b-208">Quando richiesto, selezionare "ricarica tutto".</span><span class="sxs-lookup"><span data-stu-id="5327b-208">Select 'Reload All' when prompted.</span></span>
* <span data-ttu-id="5327b-209">Fare clic su **debug-> avvia senza eseguire debug** o premere **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="5327b-209">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="5327b-210">Usare il controller Xbox per esaminare la scena.</span><span class="sxs-lookup"><span data-stu-id="5327b-210">Use the Xbox controller to look around the scene.</span></span> <span data-ttu-id="5327b-211">Si noti come il cursore interagisce con la forma degli oggetti.</span><span class="sxs-lookup"><span data-stu-id="5327b-211">Notice how the cursor interacts with the shape of objects.</span></span>

## <a name="chapter-3---gestures"></a><span data-ttu-id="5327b-212">Capitolo 3-movimenti</span><span class="sxs-lookup"><span data-stu-id="5327b-212">Chapter 3 - Gestures</span></span>

>[!VIDEO https://www.youtube.com/embed/6d-0RHeKHq4]

<span data-ttu-id="5327b-213">In questo capitolo verrà aggiunto il supporto per i [movimenti](gaze-and-commit.md#composite-gestures).</span><span class="sxs-lookup"><span data-stu-id="5327b-213">In this chapter, we'll add support for [gestures](gaze-and-commit.md#composite-gestures).</span></span> <span data-ttu-id="5327b-214">Quando l'utente seleziona una sfera della carta, la sfera viene ricadeta attivando la gravità usando il motore di fisica di Unity.</span><span class="sxs-lookup"><span data-stu-id="5327b-214">When the user selects a paper sphere, we'll make the sphere fall by turning on gravity using Unity's physics engine.</span></span>

### <a name="objectives"></a><span data-ttu-id="5327b-215">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="5327b-215">Objectives</span></span>

* <span data-ttu-id="5327b-216">Controllare gli ologrammi con il gesto di selezione.</span><span class="sxs-lookup"><span data-stu-id="5327b-216">Control your holograms with the Select gesture.</span></span>

### <a name="instructions"></a><span data-ttu-id="5327b-217">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="5327b-217">Instructions</span></span>

<span data-ttu-id="5327b-218">Si inizierà creando uno script che può rilevare il gesto di selezione.</span><span class="sxs-lookup"><span data-stu-id="5327b-218">We'll start by creating a script than can detect the Select gesture.</span></span>

* <span data-ttu-id="5327b-219">Nella cartella **Scripts** creare uno script denominato **GazeGestureManager**.</span><span class="sxs-lookup"><span data-stu-id="5327b-219">In the **Scripts** folder, create a script named **GazeGestureManager**.</span></span>
* <span data-ttu-id="5327b-220">Trascinare lo script **GazeGestureManager** sull'oggetto **origamicollection** nella gerarchia.</span><span class="sxs-lookup"><span data-stu-id="5327b-220">Drag the **GazeGestureManager** script onto the **OrigamiCollection** object in the Hierarchy.</span></span>
* <span data-ttu-id="5327b-221">Aprire lo script **GazeGestureManager** in Visual Studio e aggiungere il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="5327b-221">Open the **GazeGestureManager** script in Visual Studio and add the following code:</span></span>

```cs
using UnityEngine;
using UnityEngine.XR.WSA.Input;

public class GazeGestureManager : MonoBehaviour
{
    public static GazeGestureManager Instance { get; private set; }

    // Represents the hologram that is currently being gazed at.
    public GameObject FocusedObject { get; private set; }

    GestureRecognizer recognizer;

    // Use this for initialization
    void Start()
    {
        Instance = this;

        // Set up a GestureRecognizer to detect Select gestures.
        recognizer = new GestureRecognizer();
        recognizer.Tapped += (args) =>
        {
            // Send an OnSelect message to the focused object and its ancestors.
            if (FocusedObject != null)
            {
                FocusedObject.SendMessageUpwards("OnSelect", SendMessageOptions.DontRequireReceiver);
            }
        };
        recognizer.StartCapturingGestures();
    }

    // Update is called once per frame
    void Update()
    {
        // Figure out which hologram is focused this frame.
        GameObject oldFocusObject = FocusedObject;

        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;
        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram, use that as the focused object.
            FocusedObject = hitInfo.collider.gameObject;
        }
        else
        {
            // If the raycast did not hit a hologram, clear the focused object.
            FocusedObject = null;
        }

        // If the focused object changed this frame,
        // start detecting fresh gestures again.
        if (FocusedObject != oldFocusObject)
        {
            recognizer.CancelGestures();
            recognizer.StartCapturingGestures();
        }
    }
}
```

* <span data-ttu-id="5327b-222">Creare un altro script nella cartella Scripts, questa volta denominata **SphereCommands**.</span><span class="sxs-lookup"><span data-stu-id="5327b-222">Create another script in the Scripts folder, this time named **SphereCommands**.</span></span>
* <span data-ttu-id="5327b-223">Espandere l'oggetto **origamicollection** nella visualizzazione gerarchia.</span><span class="sxs-lookup"><span data-stu-id="5327b-223">Expand the **OrigamiCollection** object in the Hierarchy view.</span></span>
* <span data-ttu-id="5327b-224">Trascinare lo script **SphereCommands** sull'oggetto **Sphere1** nel pannello gerarchia.</span><span class="sxs-lookup"><span data-stu-id="5327b-224">Drag the **SphereCommands** script onto the **Sphere1** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="5327b-225">Trascinare lo script **SphereCommands** sull'oggetto **Sphere2** nel pannello gerarchia.</span><span class="sxs-lookup"><span data-stu-id="5327b-225">Drag the **SphereCommands** script onto the **Sphere2** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="5327b-226">Aprire lo script in Visual Studio per la modifica e sostituire il codice predefinito con il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="5327b-226">Open the script in Visual Studio for editing, and replace the default code with this:</span></span>

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }
}
```

* <span data-ttu-id="5327b-227">Esportare, compilare e distribuire l'app nell'emulatore di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5327b-227">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="5327b-228">Osservare la scena e centrare su una delle sfere.</span><span class="sxs-lookup"><span data-stu-id="5327b-228">Look around the scene, and center on one of the spheres.</span></span>
* <span data-ttu-id="5327b-229">Premere il **pulsante a del controller** Xbox o premere la barra spaziatrice per simulare il movimento di selezione.</span><span class="sxs-lookup"><span data-stu-id="5327b-229">Press the **A** button on the Xbox controller or press the Spacebar to simulate the Select gesture.</span></span>

## <a name="chapter-4---voice"></a><span data-ttu-id="5327b-230">Capitolo 4-Voice</span><span class="sxs-lookup"><span data-stu-id="5327b-230">Chapter 4 - Voice</span></span>

>[!VIDEO https://www.youtube.com/embed/LxbOhnd2_GM]

<span data-ttu-id="5327b-231">In questo capitolo, verrà aggiunto il supporto per due [comandi vocali](voice-input.md): "Reimposta mondo" per restituire le sfere eliminate alla posizione originale e "drop Sphere" per far precipitare la sfera.</span><span class="sxs-lookup"><span data-stu-id="5327b-231">In this chapter, we'll add support for two [voice commands](voice-input.md): "Reset world" to returns the dropped spheres to their original location, and "Drop sphere" to make the sphere fall.</span></span>

### <a name="objectives"></a><span data-ttu-id="5327b-232">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="5327b-232">Objectives</span></span>

* <span data-ttu-id="5327b-233">Aggiungere i comandi vocali che sono sempre in ascolto in background.</span><span class="sxs-lookup"><span data-stu-id="5327b-233">Add voice commands that always listen in the background.</span></span>
* <span data-ttu-id="5327b-234">Creare un ologramma che reagisca a un comando Voice.</span><span class="sxs-lookup"><span data-stu-id="5327b-234">Create a hologram that reacts to a voice command.</span></span>

### <a name="instructions"></a><span data-ttu-id="5327b-235">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="5327b-235">Instructions</span></span>

* <span data-ttu-id="5327b-236">Nella cartella **Scripts** creare uno script denominato **SpeechManager**.</span><span class="sxs-lookup"><span data-stu-id="5327b-236">In the **Scripts** folder, create a script named **SpeechManager**.</span></span>
* <span data-ttu-id="5327b-237">Trascinare lo script **SpeechManager** sull'oggetto **Origamicollection** nella gerarchia</span><span class="sxs-lookup"><span data-stu-id="5327b-237">Drag the **SpeechManager** script onto the **OrigamiCollection** object in the Hierarchy</span></span>
* <span data-ttu-id="5327b-238">Aprire lo script **SpeechManager** in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5327b-238">Open the **SpeechManager** script in Visual Studio.</span></span>
* <span data-ttu-id="5327b-239">Copiare e incollare questo codice in **SpeechManager.cs** e **salvare tutti**:</span><span class="sxs-lookup"><span data-stu-id="5327b-239">Copy and paste this code into **SpeechManager.cs** and **Save All**:</span></span>

```cs
using System.Collections.Generic;
using System.Linq;
using UnityEngine;
using UnityEngine.Windows.Speech;

public class SpeechManager : MonoBehaviour
{
    KeywordRecognizer keywordRecognizer = null;
    Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();

    // Use this for initialization
    void Start()
    {
        keywords.Add("Reset world", () =>
        {
            // Call the OnReset method on every descendant object.
            this.BroadcastMessage("OnReset");
        });

        keywords.Add("Drop Sphere", () =>
        {
            var focusObject = GazeGestureManager.Instance.FocusedObject;
            if (focusObject != null)
            {
                // Call the OnDrop method on just the focused object.
                focusObject.SendMessage("OnDrop", SendMessageOptions.DontRequireReceiver);
            }
        });

        // Tell the KeywordRecognizer about our keywords.
        keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());

        // Register a callback for the KeywordRecognizer and start recognizing!
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        System.Action keywordAction;
        if (keywords.TryGetValue(args.text, out keywordAction))
        {
            keywordAction.Invoke();
        }
    }
}
```

* <span data-ttu-id="5327b-240">Aprire lo script **SphereCommands** in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5327b-240">Open the **SphereCommands** script in Visual Studio.</span></span>
* <span data-ttu-id="5327b-241">Aggiornare lo script in modo da leggere:</span><span class="sxs-lookup"><span data-stu-id="5327b-241">Update the script to read as follows:</span></span>

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    Vector3 originalPosition;

    // Use this for initialization
    void Start()
    {
        // Grab the original local position of the sphere when the app starts.
        originalPosition = this.transform.localPosition;
    }

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }

    // Called by SpeechManager when the user says the "Reset world" command
    void OnReset()
    {
        // If the sphere has a Rigidbody component, remove it to disable physics.
        var rigidbody = this.GetComponent<Rigidbody>();
        if (rigidbody != null)
        {
            rigidbody.isKinematic = true;
            Destroy(rigidbody);
        }

        // Put the sphere back into its original local position.
        this.transform.localPosition = originalPosition;
    }

    // Called by SpeechManager when the user says the "Drop sphere" command
    void OnDrop()
    {
        // Just do the same logic as a Select gesture.
        OnSelect();
    }
}
```

* <span data-ttu-id="5327b-242">Esportare, compilare e distribuire l'app nell'emulatore di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5327b-242">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="5327b-243">L'emulatore supporterà il microfono del PC e risponderà alla voce: modificare la visualizzazione in modo che il cursore si trovi in una delle sfere e pronunciare "drop Sphere".</span><span class="sxs-lookup"><span data-stu-id="5327b-243">The emulator will support your PC's microphone and respond to your voice: adjust the view so the cursor is on one of the spheres, and say "Drop Sphere".</span></span>
* <span data-ttu-id="5327b-244">Pronunciare "**Reimposta tutto il mondo**" per riportare le posizioni iniziali.</span><span class="sxs-lookup"><span data-stu-id="5327b-244">Say "**Reset World**" to bring them back to their initial positions.</span></span>

## <a name="chapter-5---spatial-sound"></a><span data-ttu-id="5327b-245">Capitolo 5-audio spaziale</span><span class="sxs-lookup"><span data-stu-id="5327b-245">Chapter 5 - Spatial sound</span></span>

>[!VIDEO https://www.youtube.com/embed/Xc3C4VA10w4]

<span data-ttu-id="5327b-246">In questo capitolo verrà aggiunta la musica all'app e quindi verranno generati effetti acustici su determinate azioni.</span><span class="sxs-lookup"><span data-stu-id="5327b-246">In this chapter, we'll add music to the app, and then trigger sound effects on certain actions.</span></span> <span data-ttu-id="5327b-247">Verrà usato il [suono spaziale](spatial-sound.md) per dare un suono a una posizione specifica nello spazio 3D.</span><span class="sxs-lookup"><span data-stu-id="5327b-247">We'll be using [spatial sound](spatial-sound.md) to give sounds a specific location in 3D space.</span></span>

### <a name="objectives"></a><span data-ttu-id="5327b-248">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="5327b-248">Objectives</span></span>

* <span data-ttu-id="5327b-249">Ascolta gli ologrammi nel tuo mondo.</span><span class="sxs-lookup"><span data-stu-id="5327b-249">Hear holograms in your world.</span></span>

### <a name="instructions"></a><span data-ttu-id="5327b-250">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="5327b-250">Instructions</span></span>

* <span data-ttu-id="5327b-251">In Unity selezionare dal menu in alto **modificare > impostazioni progetto > audio**</span><span class="sxs-lookup"><span data-stu-id="5327b-251">In the Unity select from the top menu **Edit > Project Settings > Audio**</span></span>
* <span data-ttu-id="5327b-252">Trovare l'impostazione del plug-in **Spatializer** e selezionare **MS HRTF Spatializer**.</span><span class="sxs-lookup"><span data-stu-id="5327b-252">Find the **Spatializer Plugin** setting and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="5327b-253">Dalla cartella **ologrammi** trascinare l'oggetto **ambiente** nell'oggetto **origamicollection** nel pannello gerarchia.</span><span class="sxs-lookup"><span data-stu-id="5327b-253">From the **Holograms** folder, drag the **Ambience** object onto the **OrigamiCollection** object in the Hierarchy Panel.</span></span>
* <span data-ttu-id="5327b-254">Selezionare **origamicollection** e trovare il componente di **origine audio** .</span><span class="sxs-lookup"><span data-stu-id="5327b-254">Select **OrigamiCollection** and find the **Audio Source** component.</span></span> <span data-ttu-id="5327b-255">Modificare le proprietà seguenti:</span><span class="sxs-lookup"><span data-stu-id="5327b-255">Change these properties:</span></span>
  * <span data-ttu-id="5327b-256">Controllare la proprietà **Spatialize** .</span><span class="sxs-lookup"><span data-stu-id="5327b-256">Check the **Spatialize** property.</span></span>
  * <span data-ttu-id="5327b-257">Verificare la **riproduzione**.</span><span class="sxs-lookup"><span data-stu-id="5327b-257">Check the **Play On Awake**.</span></span>
  * <span data-ttu-id="5327b-258">Modificare **Blend spaziali** in **3D** trascinando il dispositivo di scorrimento a destra.</span><span class="sxs-lookup"><span data-stu-id="5327b-258">Change **Spatial Blend** to **3D** by dragging the slider all the way to the right.</span></span>
  * <span data-ttu-id="5327b-259">Controllare la proprietà del **ciclo** .</span><span class="sxs-lookup"><span data-stu-id="5327b-259">Check the **Loop** property.</span></span>
  * <span data-ttu-id="5327b-260">Espandere **impostazioni audio 3D**e immettere **0,1** per **livello Doppler**.</span><span class="sxs-lookup"><span data-stu-id="5327b-260">Expand **3D Sound Settings**, and enter **0.1** for **Doppler Level**.</span></span>
  * <span data-ttu-id="5327b-261">Impostare **volume attenuazione** su **attenuazione logaritmico**.</span><span class="sxs-lookup"><span data-stu-id="5327b-261">Set **Volume Rolloff** to **Logarithmic Rolloff**.</span></span>
  * <span data-ttu-id="5327b-262">Impostare la **distanza massima** su **20**.</span><span class="sxs-lookup"><span data-stu-id="5327b-262">Set **Max Distance** to **20**.</span></span>
* <span data-ttu-id="5327b-263">Nella cartella **Scripts** creare uno script denominato **SphereSounds**.</span><span class="sxs-lookup"><span data-stu-id="5327b-263">In the **Scripts** folder, create a script named **SphereSounds**.</span></span>
* <span data-ttu-id="5327b-264">Trascinare **SphereSounds** negli oggetti **Sphere1** e **Sphere2** della gerarchia.</span><span class="sxs-lookup"><span data-stu-id="5327b-264">Drag **SphereSounds** to the **Sphere1** and **Sphere2** objects in the Hierarchy.</span></span>
* <span data-ttu-id="5327b-265">Aprire **SphereSounds** in Visual Studio, aggiornare il codice seguente e **salvare tutto**.</span><span class="sxs-lookup"><span data-stu-id="5327b-265">Open **SphereSounds** in Visual Studio, update the following code and **Save All**.</span></span>

```cs
using UnityEngine;

public class SphereSounds : MonoBehaviour
{
    AudioSource impactAudioSource = null;
    AudioSource rollingAudioSource = null;

    bool rolling = false;

    void Start()
    {
        // Add an AudioSource component and set up some defaults
        impactAudioSource = gameObject.AddComponent<AudioSource>();
        impactAudioSource.playOnAwake = false;
        impactAudioSource.spatialize = true;
        impactAudioSource.spatialBlend = 1.0f;
        impactAudioSource.dopplerLevel = 0.0f;
        impactAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        impactAudioSource.maxDistance = 20f;

        rollingAudioSource = gameObject.AddComponent<AudioSource>();
        rollingAudioSource.playOnAwake = false;
        rollingAudioSource.spatialize = true;
        rollingAudioSource.spatialBlend = 1.0f;
        rollingAudioSource.dopplerLevel = 0.0f;
        rollingAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        rollingAudioSource.maxDistance = 20f;
        rollingAudioSource.loop = true;

        // Load the Sphere sounds from the Resources folder
        impactAudioSource.clip = Resources.Load<AudioClip>("Impact");
        rollingAudioSource.clip = Resources.Load<AudioClip>("Rolling");
    }

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Play an impact sound if the sphere impacts strongly enough.
        if (collision.relativeVelocity.magnitude >= 0.1f)
        {
            impactAudioSource.Play();
        }
    }

    // Occurs each frame that this object continues to collide with another object
    void OnCollisionStay(Collision collision)
    {
        Rigidbody rigid = gameObject.GetComponent<Rigidbody>();

        // Play a rolling sound if the sphere is rolling fast enough.
        if (!rolling && rigid.velocity.magnitude >= 0.01f)
        {
            rolling = true;
            rollingAudioSource.Play();
        }
        // Stop the rolling sound if rolling slows down.
        else if (rolling && rigid.velocity.magnitude < 0.01f)
        {
            rolling = false;
            rollingAudioSource.Stop();
        }
    }

    // Occurs when this object stops colliding with another object
    void OnCollisionExit(Collision collision)
    {
        // Stop the rolling sound if the object falls off and stops colliding.
        if (rolling)
        {
            rolling = false;
            impactAudioSource.Stop();
            rollingAudioSource.Stop();
        }
    }
}
```

* <span data-ttu-id="5327b-266">Salvare lo script e tornare a Unity.</span><span class="sxs-lookup"><span data-stu-id="5327b-266">Save the script, and return to Unity.</span></span>
* <span data-ttu-id="5327b-267">Esportare, compilare e distribuire l'app nell'emulatore di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5327b-267">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="5327b-268">Indossa le cuffie per ottenere l'effetto completo e passa da una fase all'altra in modo da essere in grado di sentire la variazione dei suoni.</span><span class="sxs-lookup"><span data-stu-id="5327b-268">Wear headphones to get the full effect, and move closer and further from the Stage to hear the sounds change.</span></span>

## <a name="chapter-6---spatial-mapping"></a><span data-ttu-id="5327b-269">Capitolo 6-mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="5327b-269">Chapter 6 - Spatial mapping</span></span>

>[!VIDEO https://www.youtube.com/embed/S-517Y63Cnk]

<span data-ttu-id="5327b-270">Ora verrà usato il [mapping spaziale](spatial-mapping.md) per collocare la lavagna del gioco su un oggetto reale nel mondo reale.</span><span class="sxs-lookup"><span data-stu-id="5327b-270">Now we are going to use [spatial mapping](spatial-mapping.md) to place the game board on a real object in the real world.</span></span>

### <a name="objectives"></a><span data-ttu-id="5327b-271">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="5327b-271">Objectives</span></span>

* <span data-ttu-id="5327b-272">Usa il mondo reale nel mondo virtuale.</span><span class="sxs-lookup"><span data-stu-id="5327b-272">Bring your real world into the virtual world.</span></span>
* <span data-ttu-id="5327b-273">Posizionare gli ologrammi in cui è importante.</span><span class="sxs-lookup"><span data-stu-id="5327b-273">Place your holograms where they matter most to you.</span></span>

### <a name="instructions"></a><span data-ttu-id="5327b-274">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="5327b-274">Instructions</span></span>

* <span data-ttu-id="5327b-275">Fare clic sulla cartella **olografici** nel pannello del progetto.</span><span class="sxs-lookup"><span data-stu-id="5327b-275">Click on the **Holograms** folder in the Project panel.</span></span>
* <span data-ttu-id="5327b-276">Trascinare l'asset di **mapping spaziale** nella radice della **gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="5327b-276">Drag the **Spatial Mapping** asset into the root of the **Hierarchy**.</span></span>
* <span data-ttu-id="5327b-277">Fare clic sull'oggetto **mapping spaziale** nella gerarchia.</span><span class="sxs-lookup"><span data-stu-id="5327b-277">Click on the **Spatial Mapping** object in the Hierarchy.</span></span>
* <span data-ttu-id="5327b-278">Nel **pannello Inspector**modificare le proprietà seguenti:</span><span class="sxs-lookup"><span data-stu-id="5327b-278">In the **Inspector panel**, change the following properties:</span></span>
  * <span data-ttu-id="5327b-279">Selezionare la casella per la **visualizzazione dei mesh** .</span><span class="sxs-lookup"><span data-stu-id="5327b-279">Check the **Draw Visual Meshes** box.</span></span>
  * <span data-ttu-id="5327b-280">Individuare il **materiale di estrazione** e fare clic sul cerchio a destra.</span><span class="sxs-lookup"><span data-stu-id="5327b-280">Locate **Draw Material** and click the circle on the right.</span></span> <span data-ttu-id="5327b-281">Digitare "**wireframe**" nel campo di ricerca nella parte superiore.</span><span class="sxs-lookup"><span data-stu-id="5327b-281">Type "**wireframe**" into the search field at the top.</span></span> <span data-ttu-id="5327b-282">Fare clic sul risultato, quindi chiudere la finestra.</span><span class="sxs-lookup"><span data-stu-id="5327b-282">Click on the result and then close the window.</span></span>
* <span data-ttu-id="5327b-283">Esportare, compilare e distribuire l'app nell'emulatore di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5327b-283">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="5327b-284">Quando viene eseguita l'app, viene eseguito il rendering in wireframe di una rete di una stanza reale di una stanza reale sottoposta a scansione.</span><span class="sxs-lookup"><span data-stu-id="5327b-284">When the app runs, a mesh of a previously scanned real-world living room will be rendered in wireframe.</span></span>
* <span data-ttu-id="5327b-285">Guarda in che modo una sfera in sequenza ricade sulla fase e sul pavimento!</span><span class="sxs-lookup"><span data-stu-id="5327b-285">Watch how a rolling sphere will fall off the stage, and onto the floor!</span></span>

<span data-ttu-id="5327b-286">Ora verrà illustrato come spostare l'oggetto Origamicollection in una nuova posizione:</span><span class="sxs-lookup"><span data-stu-id="5327b-286">Now we'll show you how to move the OrigamiCollection to a new location:</span></span>

* <span data-ttu-id="5327b-287">Nella cartella **Scripts** creare uno script denominato **TapToPlaceParent**.</span><span class="sxs-lookup"><span data-stu-id="5327b-287">In the **Scripts** folder, create a script named **TapToPlaceParent**.</span></span>
* <span data-ttu-id="5327b-288">Nella **gerarchia**espandere **origamicollection** e selezionare l'oggetto **stage** .</span><span class="sxs-lookup"><span data-stu-id="5327b-288">In the **Hierarchy**, expand the **OrigamiCollection** and select the **Stage** object.</span></span>
* <span data-ttu-id="5327b-289">Trascinare lo script **TapToPlaceParent** nell'oggetto Stage.</span><span class="sxs-lookup"><span data-stu-id="5327b-289">Drag the **TapToPlaceParent** script onto the Stage object.</span></span>
* <span data-ttu-id="5327b-290">Aprire lo script **TapToPlaceParent** in Visual Studio e aggiornarlo come segue:</span><span class="sxs-lookup"><span data-stu-id="5327b-290">Open the **TapToPlaceParent** script in Visual Studio, and update it to be the following:</span></span>

```cs
using UnityEngine;

public class TapToPlaceParent : MonoBehaviour
{
    bool placing = false;

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // On each Select gesture, toggle whether the user is in placing mode.
        placing = !placing;

        // If the user is in placing mode, display the spatial mapping mesh.
        if (placing)
        {
            SpatialMapping.Instance.DrawVisualMeshes = true;
        }
        // If the user is not in placing mode, hide the spatial mapping mesh.
        else
        {
            SpatialMapping.Instance.DrawVisualMeshes = false;
        }
    }

    // Update is called once per frame
    void Update()
    {
        // If the user is in placing mode,
        // update the placement to match the user's gaze.

        if (placing)
        {
            // Do a raycast into the world that will only hit the Spatial Mapping mesh.
            var headPosition = Camera.main.transform.position;
            var gazeDirection = Camera.main.transform.forward;

            RaycastHit hitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out hitInfo,
                30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // Move this object's parent object to
                // where the raycast hit the Spatial Mapping mesh.
                this.transform.parent.position = hitInfo.point;

                // Rotate this object's parent object to face the user.
                Quaternion toQuat = Camera.main.transform.localRotation;
                toQuat.x = 0;
                toQuat.z = 0;
                this.transform.parent.rotation = toQuat;
            }
        }
    }
}
```

* <span data-ttu-id="5327b-291">Esportare, compilare e distribuire l'app.</span><span class="sxs-lookup"><span data-stu-id="5327b-291">Export, build and deploy the app.</span></span>
* <span data-ttu-id="5327b-292">A questo punto dovrebbe essere possibile collocare il gioco in una posizione specifica guardandolo, usando il gesto selezionato (**a** o barra spaziatrice), quindi passando a una nuova posizione e usando di nuovo il movimento di selezione.</span><span class="sxs-lookup"><span data-stu-id="5327b-292">Now you should now be able to place the game in a specific location by gazing at it, using the Select gesture (**A** or Spacebar) and then moving to a new location, and using the Select gesture again.</span></span>

## <a name="the-end"></a><span data-ttu-id="5327b-293">La fine</span><span class="sxs-lookup"><span data-stu-id="5327b-293">The end</span></span>

<span data-ttu-id="5327b-294">Questa è la fine di questa esercitazione.</span><span class="sxs-lookup"><span data-stu-id="5327b-294">And that's the end of this tutorial!</span></span>

<span data-ttu-id="5327b-295">Si è appreso quanto segue:</span><span class="sxs-lookup"><span data-stu-id="5327b-295">You learned:</span></span>

* <span data-ttu-id="5327b-296">Come creare un'app olografica in Unity.</span><span class="sxs-lookup"><span data-stu-id="5327b-296">How to create a holographic app in Unity.</span></span>
* <span data-ttu-id="5327b-297">Come usare lo sguardo, il movimento, la voce, i suoni e il mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="5327b-297">How to make use of gaze, gesture, voice, sounds, and spatial mapping.</span></span>
* <span data-ttu-id="5327b-298">Come compilare e distribuire un'app con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5327b-298">How to build and deploy an app using Visual Studio.</span></span>

<span data-ttu-id="5327b-299">A questo punto è possibile iniziare a creare le proprie app olografiche.</span><span class="sxs-lookup"><span data-stu-id="5327b-299">You are now ready to start creating your own holographic apps!</span></span>

## <a name="see-also"></a><span data-ttu-id="5327b-300">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="5327b-300">See also</span></span>

* [<span data-ttu-id="5327b-301">Nozioni fondamentali 101: completare il progetto con il dispositivo</span><span class="sxs-lookup"><span data-stu-id="5327b-301">MR Basics 101: Complete project with device</span></span>](holograms-101.md)
* [<span data-ttu-id="5327b-302">Sguardo fisso</span><span class="sxs-lookup"><span data-stu-id="5327b-302">Gaze</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="5327b-303">Puntamento con la testa e commit</span><span class="sxs-lookup"><span data-stu-id="5327b-303">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="5327b-304">Input vocale</span><span class="sxs-lookup"><span data-stu-id="5327b-304">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="5327b-305">Audio spaziale</span><span class="sxs-lookup"><span data-stu-id="5327b-305">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="5327b-306">Mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="5327b-306">Spatial mapping</span></span>](spatial-mapping.md)

---
title: Nozioni di base 101-completare il progetto con il dispositivo
description: Segui questa procedura dettagliata di codifica usando Unity, Visual Studio e HoloLens per apprendere le nozioni di base della realtà mista di Windows.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: realtà mista, realtà mista di Windows, HoloLens, ologramma, Accademia, esercitazione
ms.openlocfilehash: 456aeea88b0d7f51acb52156d8139ec2df06883a
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434714"
---
>[!NOTE]
><span data-ttu-id="0ac36-104">Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.</span><span class="sxs-lookup"><span data-stu-id="0ac36-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="0ac36-105">Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.</span><span class="sxs-lookup"><span data-stu-id="0ac36-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="0ac36-106">Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="0ac36-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="0ac36-107">Verranno mantenuti per continuare a usare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="0ac36-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="0ac36-108">Per HoloLens 2 è stata pubblicata [una nuova serie di esercitazioni](mrlearning-base.md) .</span><span class="sxs-lookup"><span data-stu-id="0ac36-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

# <a name="mr-basics-101-complete-project-with-device"></a><span data-ttu-id="0ac36-109">Nozioni fondamentali 101: completare il progetto con il dispositivo</span><span class="sxs-lookup"><span data-stu-id="0ac36-109">MR Basics 101: Complete project with device</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/XKIIEC5BMWg]

<span data-ttu-id="0ac36-110">Questa esercitazione illustra in dettaglio un progetto completo, integrato in Unity, che illustra le funzionalità di base della realtà mista di Windows su HoloLens, tra cui lo [sguardo](gaze-and-commit.md), i [movimenti](gaze-and-commit.md#composite-gestures), l' [input vocale](voice-input.md), il mapping di [suoni spaziali](spatial-sound.md) e [spaziali](spatial-mapping.md) .</span><span class="sxs-lookup"><span data-stu-id="0ac36-110">This tutorial will walk you through a complete project, built in Unity, that demonstrates core Windows Mixed Reality features on HoloLens including [gaze](gaze-and-commit.md), [gestures](gaze-and-commit.md#composite-gestures), [voice input](voice-input.md), [spatial sound](spatial-sound.md) and [spatial mapping](spatial-mapping.md).</span></span>

<span data-ttu-id="0ac36-111">Il completamento dell'esercitazione richiede circa 1 ora.</span><span class="sxs-lookup"><span data-stu-id="0ac36-111">The tutorial will take approximately 1 hour to complete.</span></span>

## <a name="device-support"></a><span data-ttu-id="0ac36-112">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="0ac36-112">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="0ac36-113">Corso</span><span class="sxs-lookup"><span data-stu-id="0ac36-113">Course</span></span></th><th style="width:150px"> <span data-ttu-id="0ac36-114"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="0ac36-114"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="0ac36-115"><a href="immersive-headset-hardware-details.md">Visori VR immersive</a></span><span class="sxs-lookup"><span data-stu-id="0ac36-115"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="0ac36-116">Nozioni fondamentali 101: completare il progetto con il dispositivo</span><span class="sxs-lookup"><span data-stu-id="0ac36-116">MR Basics 101: Complete project with device</span></span></td><td style="text-align: center;"> <span data-ttu-id="0ac36-117">✔️</span><span class="sxs-lookup"><span data-stu-id="0ac36-117">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="0ac36-118">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="0ac36-118">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="0ac36-119">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="0ac36-119">Prerequisites</span></span>

* <span data-ttu-id="0ac36-120">Un PC Windows 10 configurato con gli [strumenti corretti installati](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="0ac36-120">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="0ac36-121">Un dispositivo HoloLens [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="0ac36-121">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="0ac36-122">File di progetto</span><span class="sxs-lookup"><span data-stu-id="0ac36-122">Project files</span></span>

* <span data-ttu-id="0ac36-123">Scaricare i [file](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) richiesti dal progetto.</span><span class="sxs-lookup"><span data-stu-id="0ac36-123">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) required by the project.</span></span><span data-ttu-id="0ac36-124"> Richiede Unity 2017,2 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="0ac36-124"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="0ac36-125">Se è ancora necessario il supporto per Unity 5,6, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span><span class="sxs-lookup"><span data-stu-id="0ac36-125">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span></span>
  * <span data-ttu-id="0ac36-126">Se è ancora necessario il supporto per Unity 5,5, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span><span class="sxs-lookup"><span data-stu-id="0ac36-126">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span></span>
  * <span data-ttu-id="0ac36-127">Se è ancora necessario il supporto per Unity 5,4, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span><span class="sxs-lookup"><span data-stu-id="0ac36-127">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span></span>
* <span data-ttu-id="0ac36-128">Annullare l'archiviazione dei file sul desktop o in un'altra posizione facile da raggiungere.</span><span class="sxs-lookup"><span data-stu-id="0ac36-128">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="0ac36-129">Mantiene il nome della cartella come **origami**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-129">Keep the folder name as **Origami**.</span></span>

>[!NOTE]
><span data-ttu-id="0ac36-130">Se si vuole esaminare il codice sorgente prima del download, è [disponibile in GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span><span class="sxs-lookup"><span data-stu-id="0ac36-130">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="0ac36-131">Capitolo 1-"Holo" World</span><span class="sxs-lookup"><span data-stu-id="0ac36-131">Chapter 1 - "Holo" world</span></span>

>[!VIDEO https://www.youtube.com/embed/PmtZGjYFroY]

<span data-ttu-id="0ac36-132">In questo capitolo verrà configurato il primo progetto Unity ed eseguiamo il processo di compilazione e distribuzione.</span><span class="sxs-lookup"><span data-stu-id="0ac36-132">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="0ac36-133">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="0ac36-133">Objectives</span></span>

* <span data-ttu-id="0ac36-134">Configurare Unity per lo sviluppo olografico.</span><span class="sxs-lookup"><span data-stu-id="0ac36-134">Set up Unity for holographic development.</span></span>
* <span data-ttu-id="0ac36-135">Creare un ologramma.</span><span class="sxs-lookup"><span data-stu-id="0ac36-135">Make a hologram.</span></span>
* <span data-ttu-id="0ac36-136">Vedere un ologramma creato.</span><span class="sxs-lookup"><span data-stu-id="0ac36-136">See a hologram that you made.</span></span>

### <a name="instructions"></a><span data-ttu-id="0ac36-137">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="0ac36-137">Instructions</span></span>

* <span data-ttu-id="0ac36-138">Avvia Unity.</span><span class="sxs-lookup"><span data-stu-id="0ac36-138">Start Unity.</span></span>
* <span data-ttu-id="0ac36-139">Selezionare **Apri**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-139">Select **Open**.</span></span>
* <span data-ttu-id="0ac36-140">Immettere il percorso come cartella **origami** precedentemente non archiviata.</span><span class="sxs-lookup"><span data-stu-id="0ac36-140">Enter location as the **Origami** folder you previously un-archived.</span></span>
* <span data-ttu-id="0ac36-141">Selezionare **origami** e fare clic su **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-141">Select **Origami** and click **Select Folder**.</span></span>
* <span data-ttu-id="0ac36-142">Poiché il progetto **origami** non contiene una scena, salvare la scena predefinita vuota in un nuovo file usando: **file** / **Salva scena con nome**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-142">Since the **Origami** project does not contain a scene, save the empty default scene to a new file using: **File** / **Save Scene As**.</span></span>
* <span data-ttu-id="0ac36-143">Assegnare alla nuova scena il nome **origami** e premere il pulsante **Salva** .</span><span class="sxs-lookup"><span data-stu-id="0ac36-143">Name the new scene **Origami** and press the **Save** button.</span></span>

#### <a name="setup-the-main-virtual-camera"></a><span data-ttu-id="0ac36-144">Configurare la fotocamera virtuale principale</span><span class="sxs-lookup"><span data-stu-id="0ac36-144">Setup the main virtual camera</span></span>

* <span data-ttu-id="0ac36-145">Nel **Pannello gerarchia**selezionare **Main camera**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-145">In the **Hierarchy Panel**, select **Main Camera**.</span></span>
* <span data-ttu-id="0ac36-146">Nel **controllo** impostare la relativa posizione di trasformazione su **0, 0, 0**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-146">In the **Inspector** set its transform position to **0,0,0**.</span></span>
* <span data-ttu-id="0ac36-147">Trovare la proprietà **Clear Flags** e modificare l'elenco a discesa da **SKYBOX** a **tinta unita**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-147">Find the **Clear Flags** property, and change the dropdown from **Skybox** to **Solid color**.</span></span>
* <span data-ttu-id="0ac36-148">Fare clic sul campo **sfondo** per aprire una selezione colori.</span><span class="sxs-lookup"><span data-stu-id="0ac36-148">Click on the **Background** field to open a color picker.</span></span>
* <span data-ttu-id="0ac36-149">Impostare **R, G, B e** a su **0**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-149">Set **R, G, B, and A** to **0**.</span></span>

#### <a name="setup-the-scene"></a><span data-ttu-id="0ac36-150">Configurare la scena</span><span class="sxs-lookup"><span data-stu-id="0ac36-150">Setup the scene</span></span>

* <span data-ttu-id="0ac36-151">Nel **Pannello gerarchia**fare clic su **Crea** e **Crea vuoto**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-151">In the **Hierarchy Panel**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="0ac36-152">Fare clic con il pulsante destro del mouse sul nuovo **GameObject** e scegliere Rinomina.</span><span class="sxs-lookup"><span data-stu-id="0ac36-152">Right-click the new **GameObject** and select Rename.</span></span> <span data-ttu-id="0ac36-153">Rinominare GameObject in **origamicollection**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-153">Rename the GameObject to **OrigamiCollection**.</span></span>
* <span data-ttu-id="0ac36-154">Dalla cartella **olografici** nel pannello del progetto (espandere asset e selezionare ologrammi oppure fare doppio clic sulla cartella ologrammi nel pannello del progetto):</span><span class="sxs-lookup"><span data-stu-id="0ac36-154">From the **Holograms** folder in the Project Panel (expand Assets and select Holograms or double click the Holograms folder in the Project Panel):</span></span>
  * <span data-ttu-id="0ac36-155">Trascinare la **fase** nella gerarchia in modo che sia un elemento figlio di **origamicollection**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-155">Drag **Stage** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="0ac36-156">Trascinare **Sphere1** nella gerarchia in modo che sia un elemento figlio di **origamicollection**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-156">Drag **Sphere1** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="0ac36-157">Trascinare **Sphere2** nella gerarchia in modo che sia un elemento figlio di **origamicollection**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-157">Drag **Sphere2** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="0ac36-158">Fare clic con il pulsante destro del mouse sull'oggetto **direzionale chiaro** nel **Pannello gerarchia** e scegliere **Elimina**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-158">Right-click the **Directional Light** object in the **Hierarchy Panel** and select **Delete**.</span></span>
* <span data-ttu-id="0ac36-159">Dalla cartella **ologrammi** trascinare le **spie** nella radice del **Pannello gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-159">From the **Holograms** folder, drag **Lights** into the root of the **Hierarchy Panel**.</span></span>
* <span data-ttu-id="0ac36-160">Nella **gerarchia**selezionare **origamicollection**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-160">In the **Hierarchy**, select the **OrigamiCollection**.</span></span>
* <span data-ttu-id="0ac36-161">Nel **controllo**impostare la posizione di trasformazione su **0,-0,5, 2,0**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-161">In the **Inspector**, set the transform position to **0, -0.5, 2.0**.</span></span>
* <span data-ttu-id="0ac36-162">Premere il pulsante **Play** in Unity per visualizzare l'anteprima degli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="0ac36-162">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="0ac36-163">Nella finestra di anteprima verranno visualizzati gli oggetti origami.</span><span class="sxs-lookup"><span data-stu-id="0ac36-163">You should see the Origami objects in the preview window.</span></span>
* <span data-ttu-id="0ac36-164">Premere **Riproduci** una seconda volta per arrestare la modalità di anteprima.</span><span class="sxs-lookup"><span data-stu-id="0ac36-164">Press **Play** a second time to stop preview mode.</span></span>

#### <a name="export-the-project-from-unity-to-visual-studio"></a><span data-ttu-id="0ac36-165">Esportare il progetto da Unity a Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0ac36-165">Export the project from Unity to Visual Studio</span></span>

* <span data-ttu-id="0ac36-166">In Unity selezionare **File > impostazioni di compilazione**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-166">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="0ac36-167">Selezionare **piattaforma UWP (Universal Windows Platform)** nell'elenco **piattaforma** e fare clic su **Cambia piattaforma**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-167">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="0ac36-168">Impostare **SDK** su **Universal 10** e **tipo di compilazione** su **D3D**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-168">Set **SDK** to **Universal 10** and **Build Type** to **D3D**.</span></span>
* <span data-ttu-id="0ac36-169">Controllare **i C# progetti Unity**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-169">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="0ac36-170">Fare clic su **Aggiungi scene aperte** per aggiungere la scena.</span><span class="sxs-lookup"><span data-stu-id="0ac36-170">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="0ac36-171">Fai clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-171">Click **Build**.</span></span>
* <span data-ttu-id="0ac36-172">Nella finestra Esplora file visualizzata creare una **nuova cartella** denominata "app".</span><span class="sxs-lookup"><span data-stu-id="0ac36-172">In the file explorer window that appears, create a **New Folder** named "App".</span></span>
* <span data-ttu-id="0ac36-173">Fare clic sulla **cartella dell'app**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-173">Single click the **App Folder**.</span></span>
* <span data-ttu-id="0ac36-174">Premere **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-174">Press **Select Folder**.</span></span>
* <span data-ttu-id="0ac36-175">Quando si esegue Unity, viene visualizzata una finestra Esplora file.</span><span class="sxs-lookup"><span data-stu-id="0ac36-175">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="0ac36-176">Aprire la cartella dell' **app** .</span><span class="sxs-lookup"><span data-stu-id="0ac36-176">Open the **App** folder.</span></span>
* <span data-ttu-id="0ac36-177">Aprire (doppio clic) **origami. sln**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-177">Open (double click) **Origami.sln**.</span></span>
* <span data-ttu-id="0ac36-178">Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione da debug a **Release** e da ARM a **x86**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-178">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
* <span data-ttu-id="0ac36-179">Fare clic sulla freccia accanto al pulsante Device (dispositivo) e selezionare **computer remoto** per la distribuzione tramite Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="0ac36-179">Click on the arrow next to the Device button, and select **Remote Machine** to deploy over Wi-Fi.</span></span>
  * <span data-ttu-id="0ac36-180">Impostare l' **Indirizzo** sul nome o sull'indirizzo IP del HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0ac36-180">Set the **Address** to the name or IP address of your HoloLens.</span></span> <span data-ttu-id="0ac36-181">Se non si conosce l'indirizzo IP del dispositivo, controllare **le impostazioni > rete & Internet > opzioni avanzate** o richiedere a Cortana **"Hey Cortana, qual è il mio indirizzo IP?"**</span><span class="sxs-lookup"><span data-stu-id="0ac36-181">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** or ask Cortana **"Hey Cortana, What's my IP address?"**</span></span>
  * <span data-ttu-id="0ac36-182">Se il HoloLens è collegato tramite USB, è possibile invece selezionare il **dispositivo** per la distribuzione su USB.</span><span class="sxs-lookup"><span data-stu-id="0ac36-182">If the HoloLens is attached over USB, you may instead select **Device** to deploy over USB.</span></span>
  * <span data-ttu-id="0ac36-183">Lasciare la **modalità di autenticazione** impostata su **universale**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-183">Leave the **Authentication Mode** set to **Universal**.</span></span>
  * <span data-ttu-id="0ac36-184">Fare clic su **Seleziona**</span><span class="sxs-lookup"><span data-stu-id="0ac36-184">Click **Select**</span></span>

* <span data-ttu-id="0ac36-185">Fare clic su **debug > avvia senza eseguire debug** o premere **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-185">Click **Debug > Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="0ac36-186">Se questa è la prima volta che si esegue la distribuzione nel dispositivo, sarà necessario [associarla a Visual Studio](using-visual-studio.md#pairing-your-device).</span><span class="sxs-lookup"><span data-stu-id="0ac36-186">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device).</span></span>

* <span data-ttu-id="0ac36-187">Il progetto Origami verrà ora compilato, distribuito nella HoloLens e quindi eseguito.</span><span class="sxs-lookup"><span data-stu-id="0ac36-187">The Origami project will now build, deploy to your HoloLens, and then run.</span></span>
* <span data-ttu-id="0ac36-188">Inserire il HoloLens e cercare i nuovi ologrammi.</span><span class="sxs-lookup"><span data-stu-id="0ac36-188">Put on your HoloLens and look around to see your new holograms.</span></span>

## <a name="chapter-2---gaze"></a><span data-ttu-id="0ac36-189">Capitolo 2: sguardo</span><span class="sxs-lookup"><span data-stu-id="0ac36-189">Chapter 2 - Gaze</span></span>

>[!VIDEO https://www.youtube.com/embed/MSO2BoFSQbM]

<span data-ttu-id="0ac36-190">In questo capitolo, verranno introdotti i primi tre modi per interagire con gli ologrammi [.](gaze-and-commit.md)</span><span class="sxs-lookup"><span data-stu-id="0ac36-190">In this chapter, we are going to introduce the first of three ways of interacting with your holograms -- [gaze](gaze-and-commit.md).</span></span>

### <a name="objectives"></a><span data-ttu-id="0ac36-191">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="0ac36-191">Objectives</span></span>

* <span data-ttu-id="0ac36-192">Visualizza lo sguardo usando un cursore con blocco globale.</span><span class="sxs-lookup"><span data-stu-id="0ac36-192">Visualize your gaze using a world-locked cursor.</span></span>

### <a name="instructions"></a><span data-ttu-id="0ac36-193">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="0ac36-193">Instructions</span></span>

* <span data-ttu-id="0ac36-194">Tornare al progetto Unity e chiudere la finestra impostazioni di compilazione se è ancora aperta.</span><span class="sxs-lookup"><span data-stu-id="0ac36-194">Go back to your Unity project, and close the Build Settings window if it's still open.</span></span>
* <span data-ttu-id="0ac36-195">Selezionare la cartella **ologrammi** nel **Pannello del progetto**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-195">Select the **Holograms** folder in the **Project panel**.</span></span>
* <span data-ttu-id="0ac36-196">Trascinare l'oggetto **cursore** nel **Pannello gerarchia** a livello di radice.</span><span class="sxs-lookup"><span data-stu-id="0ac36-196">Drag the **Cursor** object into the **Hierarchy panel** at the root level.</span></span>
* <span data-ttu-id="0ac36-197">Fare doppio clic sull'oggetto **cursore** per esaminarlo più da vicino.</span><span class="sxs-lookup"><span data-stu-id="0ac36-197">Double-click on the **Cursor** object to take a closer look at it.</span></span>
* <span data-ttu-id="0ac36-198">Fare clic con il pulsante destro del mouse sulla cartella **Scripts** nel pannello Project.</span><span class="sxs-lookup"><span data-stu-id="0ac36-198">Right-click on the **Scripts** folder in the Project panel.</span></span>
* <span data-ttu-id="0ac36-199">Fare clic sul sottomenu **Crea** .</span><span class="sxs-lookup"><span data-stu-id="0ac36-199">Click the **Create** sub-menu.</span></span>
* <span data-ttu-id="0ac36-200">Selezionare  **C# script**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-200">Select **C# Script**.</span></span>
* <span data-ttu-id="0ac36-201">Denominare lo script **WorldCursor**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-201">Name the script **WorldCursor**.</span></span> <span data-ttu-id="0ac36-202">Nota: il nome fa distinzione tra maiuscole e minuscole.</span><span class="sxs-lookup"><span data-stu-id="0ac36-202">Note: The name is case-sensitive.</span></span> <span data-ttu-id="0ac36-203">Non è necessario aggiungere l'estensione. cs.</span><span class="sxs-lookup"><span data-stu-id="0ac36-203">You do not need to add the .cs extension.</span></span>
* <span data-ttu-id="0ac36-204">Selezionare l'oggetto **cursore** nel **Pannello gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-204">Select the **Cursor** object in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="0ac36-205">Trascinare e rilasciare lo script **WorldCursor** nel **pannello Inspector**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-205">Drag and drop the **WorldCursor** script into the **Inspector panel**.</span></span>
* <span data-ttu-id="0ac36-206">Fare doppio clic sullo script **WorldCursor** per aprirlo in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0ac36-206">Double-click the **WorldCursor** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="0ac36-207">Copiare e incollare questo codice in **WorldCursor.cs** e **salvare tutti**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-207">Copy and paste this code into **WorldCursor.cs** and **Save All**.</span></span>

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

            // Move the cursor to the point where the raycast hit.
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

* <span data-ttu-id="0ac36-208">Ricompilare l'app da **File > impostazioni di compilazione**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-208">Rebuild the app from **File > Build Settings**.</span></span>
* <span data-ttu-id="0ac36-209">Tornare alla soluzione di Visual Studio usata in precedenza per eseguire la distribuzione in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0ac36-209">Return to the Visual Studio solution previously used to deploy to your HoloLens.</span></span>
* <span data-ttu-id="0ac36-210">Quando richiesto, selezionare "ricarica tutto".</span><span class="sxs-lookup"><span data-stu-id="0ac36-210">Select 'Reload All' when prompted.</span></span>
* <span data-ttu-id="0ac36-211">Fare clic su **debug-> avvia senza eseguire debug** o premere **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-211">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="0ac36-212">Osservare ora la scena e notare come il cursore interagisce con la forma degli oggetti.</span><span class="sxs-lookup"><span data-stu-id="0ac36-212">Now look around the scene and notice how the cursor interacts with the shape of objects.</span></span>

## <a name="chapter-3---gestures"></a><span data-ttu-id="0ac36-213">Capitolo 3-movimenti</span><span class="sxs-lookup"><span data-stu-id="0ac36-213">Chapter 3 - Gestures</span></span>

>[!VIDEO https://www.youtube.com/embed/kW3ThJ2MbvQ]

<span data-ttu-id="0ac36-214">In questo capitolo verrà aggiunto il supporto per i [movimenti](gaze-and-commit.md#composite-gestures).</span><span class="sxs-lookup"><span data-stu-id="0ac36-214">In this chapter, we'll add support for [gestures](gaze-and-commit.md#composite-gestures).</span></span> <span data-ttu-id="0ac36-215">Quando l'utente seleziona una sfera della carta, la sfera viene ricadeta attivando la gravità usando il motore di fisica di Unity.</span><span class="sxs-lookup"><span data-stu-id="0ac36-215">When the user selects a paper sphere, we'll make the sphere fall by turning on gravity using Unity's physics engine.</span></span>

### <a name="objectives"></a><span data-ttu-id="0ac36-216">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="0ac36-216">Objectives</span></span>

* <span data-ttu-id="0ac36-217">Controllare gli ologrammi con il gesto di selezione.</span><span class="sxs-lookup"><span data-stu-id="0ac36-217">Control your holograms with the Select gesture.</span></span>

### <a name="instructions"></a><span data-ttu-id="0ac36-218">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="0ac36-218">Instructions</span></span>

<span data-ttu-id="0ac36-219">Si inizierà creando uno script, quindi è possibile rilevare il gesto di selezione.</span><span class="sxs-lookup"><span data-stu-id="0ac36-219">We'll start by creating a script then can detect the Select gesture.</span></span>

* <span data-ttu-id="0ac36-220">Nella cartella **Scripts** creare uno script denominato **GazeGestureManager**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-220">In the **Scripts** folder, create a script named **GazeGestureManager**.</span></span>
* <span data-ttu-id="0ac36-221">Trascinare lo script **GazeGestureManager** sull'oggetto **origamicollection** nella gerarchia.</span><span class="sxs-lookup"><span data-stu-id="0ac36-221">Drag the **GazeGestureManager** script onto the **OrigamiCollection** object in the Hierarchy.</span></span>
* <span data-ttu-id="0ac36-222">Aprire lo script **GazeGestureManager** in Visual Studio e aggiungere il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="0ac36-222">Open the **GazeGestureManager** script in Visual Studio and add the following code:</span></span>

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
    void Awake()
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

* <span data-ttu-id="0ac36-223">Creare un altro script nella cartella Scripts, questa volta denominata **SphereCommands**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-223">Create another script in the Scripts folder, this time named **SphereCommands**.</span></span>
* <span data-ttu-id="0ac36-224">Espandere l'oggetto **origamicollection** nella visualizzazione gerarchia.</span><span class="sxs-lookup"><span data-stu-id="0ac36-224">Expand the **OrigamiCollection** object in the Hierarchy view.</span></span>
* <span data-ttu-id="0ac36-225">Trascinare lo script **SphereCommands** sull'oggetto **Sphere1** nel pannello gerarchia.</span><span class="sxs-lookup"><span data-stu-id="0ac36-225">Drag the **SphereCommands** script onto the **Sphere1** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="0ac36-226">Trascinare lo script **SphereCommands** sull'oggetto **Sphere2** nel pannello gerarchia.</span><span class="sxs-lookup"><span data-stu-id="0ac36-226">Drag the **SphereCommands** script onto the **Sphere2** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="0ac36-227">Aprire lo script in Visual Studio per la modifica e sostituire il codice predefinito con il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="0ac36-227">Open the script in Visual Studio for editing, and replace the default code with this:</span></span>

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

* <span data-ttu-id="0ac36-228">Esportare, compilare e distribuire l'app in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0ac36-228">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="0ac36-229">Esaminare una delle sfere.</span><span class="sxs-lookup"><span data-stu-id="0ac36-229">Look at one of the spheres.</span></span>
* <span data-ttu-id="0ac36-230">Eseguire il gesto di selezione e osservare il calo della sfera nell'area sottostante.</span><span class="sxs-lookup"><span data-stu-id="0ac36-230">Perform the select gesture and watch the sphere drop onto the surface below.</span></span>

## <a name="chapter-4---voice"></a><span data-ttu-id="0ac36-231">Capitolo 4-Voice</span><span class="sxs-lookup"><span data-stu-id="0ac36-231">Chapter 4 - Voice</span></span>

>[!VIDEO https://www.youtube.com/embed/1-Aq0VVtHM8]

<span data-ttu-id="0ac36-232">In questo capitolo verrà aggiunto il supporto per due [comandi vocali](voice-input.md): "Reimposta tutto il mondo" per restituire le sfere eliminate alla posizione originale e "drop Sphere" per far precipitare la sfera.</span><span class="sxs-lookup"><span data-stu-id="0ac36-232">In this chapter, we'll add support for two [voice commands](voice-input.md): "Reset world" to return the dropped spheres to their original location, and "Drop sphere" to make the sphere fall.</span></span>

### <a name="objectives"></a><span data-ttu-id="0ac36-233">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="0ac36-233">Objectives</span></span>

* <span data-ttu-id="0ac36-234">Aggiungere i comandi vocali che sono sempre in ascolto in background.</span><span class="sxs-lookup"><span data-stu-id="0ac36-234">Add voice commands that always listen in the background.</span></span>
* <span data-ttu-id="0ac36-235">Creare un ologramma che reagisca a un comando Voice.</span><span class="sxs-lookup"><span data-stu-id="0ac36-235">Create a hologram that reacts to a voice command.</span></span>

### <a name="instructions"></a><span data-ttu-id="0ac36-236">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="0ac36-236">Instructions</span></span>

* <span data-ttu-id="0ac36-237">Nella cartella **Scripts** creare uno script denominato **SpeechManager**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-237">In the **Scripts** folder, create a script named **SpeechManager**.</span></span>
* <span data-ttu-id="0ac36-238">Trascinare lo script **SpeechManager** sull'oggetto **Origamicollection** nella gerarchia</span><span class="sxs-lookup"><span data-stu-id="0ac36-238">Drag the **SpeechManager** script onto the **OrigamiCollection** object in the Hierarchy</span></span>
* <span data-ttu-id="0ac36-239">Aprire lo script **SpeechManager** in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0ac36-239">Open the **SpeechManager** script in Visual Studio.</span></span>
* <span data-ttu-id="0ac36-240">Copiare e incollare questo codice in **SpeechManager.cs** e **salvare tutti**:</span><span class="sxs-lookup"><span data-stu-id="0ac36-240">Copy and paste this code into **SpeechManager.cs** and **Save All**:</span></span>

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

* <span data-ttu-id="0ac36-241">Aprire lo script **SphereCommands** in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0ac36-241">Open the **SphereCommands** script in Visual Studio.</span></span>
* <span data-ttu-id="0ac36-242">Aggiornare lo script in modo da leggere:</span><span class="sxs-lookup"><span data-stu-id="0ac36-242">Update the script to read as follows:</span></span>

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

* <span data-ttu-id="0ac36-243">Esportare, compilare e distribuire l'app in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0ac36-243">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="0ac36-244">Esaminare una delle sfere e pronunciare "**Drop Sphere**".</span><span class="sxs-lookup"><span data-stu-id="0ac36-244">Look at one of the spheres, and say "**Drop Sphere**".</span></span>
* <span data-ttu-id="0ac36-245">Pronunciare "**Reimposta tutto il mondo**" per riportare le posizioni iniziali.</span><span class="sxs-lookup"><span data-stu-id="0ac36-245">Say "**Reset World**" to bring them back to their initial positions.</span></span>

## <a name="chapter-5---spatial-sound"></a><span data-ttu-id="0ac36-246">Capitolo 5-audio spaziale</span><span class="sxs-lookup"><span data-stu-id="0ac36-246">Chapter 5 - Spatial sound</span></span>

>[!VIDEO https://www.youtube.com/embed/Aj4de5Ncbfo]

<span data-ttu-id="0ac36-247">In questo capitolo verrà aggiunta la musica all'app e quindi verranno generati effetti acustici su determinate azioni.</span><span class="sxs-lookup"><span data-stu-id="0ac36-247">In this chapter, we'll add music to the app, and then trigger sound effects on certain actions.</span></span> <span data-ttu-id="0ac36-248">Verrà usato il [suono spaziale](spatial-sound.md) per dare un suono a una posizione specifica nello spazio 3D.</span><span class="sxs-lookup"><span data-stu-id="0ac36-248">We'll be using [spatial sound](spatial-sound.md) to give sounds a specific location in 3D space.</span></span>

### <a name="objectives"></a><span data-ttu-id="0ac36-249">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="0ac36-249">Objectives</span></span>

* <span data-ttu-id="0ac36-250">Ascolta gli ologrammi nel tuo mondo.</span><span class="sxs-lookup"><span data-stu-id="0ac36-250">Hear holograms in your world.</span></span>

### <a name="instructions"></a><span data-ttu-id="0ac36-251">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="0ac36-251">Instructions</span></span>

* <span data-ttu-id="0ac36-252">In Unity selezionare dal menu in alto **modificare > impostazioni progetto > audio**</span><span class="sxs-lookup"><span data-stu-id="0ac36-252">In Unity select from the top menu **Edit > Project Settings > Audio**</span></span>
* <span data-ttu-id="0ac36-253">Nel pannello Inspector sul lato destro trovare l'impostazione del plug-in **Spatializer** e selezionare **MS HRTF Spatializer**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-253">In the Inspector Panel on the right side, find the **Spatializer Plugin** setting and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="0ac36-254">Dalla cartella **olografici** nel pannello del progetto trascinare l'oggetto **ambiente** nell'oggetto **origamicollection** nel pannello gerarchia.</span><span class="sxs-lookup"><span data-stu-id="0ac36-254">From the **Holograms** folder in the Project panel, drag the **Ambience** object onto the **OrigamiCollection** object in the Hierarchy Panel.</span></span>
* <span data-ttu-id="0ac36-255">Selezionare **origamicollection** e trovare il componente **origine audio** nel pannello di controllo.</span><span class="sxs-lookup"><span data-stu-id="0ac36-255">Select **OrigamiCollection** and find the **Audio Source** component in the Inspector panel.</span></span> <span data-ttu-id="0ac36-256">Modificare le proprietà seguenti:</span><span class="sxs-lookup"><span data-stu-id="0ac36-256">Change these properties:</span></span>
  * <span data-ttu-id="0ac36-257">Controllare la proprietà **Spatialize** .</span><span class="sxs-lookup"><span data-stu-id="0ac36-257">Check the **Spatialize** property.</span></span>
  * <span data-ttu-id="0ac36-258">Verificare la **riproduzione**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-258">Check the **Play On Awake**.</span></span>
  * <span data-ttu-id="0ac36-259">Modificare **Blend spaziali** in **3D** trascinando il dispositivo di scorrimento a destra.</span><span class="sxs-lookup"><span data-stu-id="0ac36-259">Change **Spatial Blend** to **3D** by dragging the slider all the way to the right.</span></span> <span data-ttu-id="0ac36-260">Quando si sposta il dispositivo di scorrimento, il valore deve variare da 0 a 1.</span><span class="sxs-lookup"><span data-stu-id="0ac36-260">The value should change from 0 to 1 when you move the slider.</span></span>
  * <span data-ttu-id="0ac36-261">Controllare la proprietà del **ciclo** .</span><span class="sxs-lookup"><span data-stu-id="0ac36-261">Check the **Loop** property.</span></span>
  * <span data-ttu-id="0ac36-262">Espandere **impostazioni audio 3D**e immettere **0,1** per **livello Doppler**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-262">Expand **3D Sound Settings**, and enter **0.1** for **Doppler Level**.</span></span>
  * <span data-ttu-id="0ac36-263">Impostare **volume attenuazione** su **attenuazione logaritmico**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-263">Set **Volume Rolloff** to **Logarithmic Rolloff**.</span></span>
  * <span data-ttu-id="0ac36-264">Impostare la **distanza massima** su **20**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-264">Set **Max Distance** to **20**.</span></span>
* <span data-ttu-id="0ac36-265">Nella cartella **Scripts** creare uno script denominato **SphereSounds**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-265">In the **Scripts** folder, create a script named **SphereSounds**.</span></span>
* <span data-ttu-id="0ac36-266">Trascinare **SphereSounds** negli oggetti **Sphere1** e **Sphere2** della gerarchia.</span><span class="sxs-lookup"><span data-stu-id="0ac36-266">Drag and drop **SphereSounds** to the **Sphere1** and **Sphere2** objects in the Hierarchy.</span></span>
* <span data-ttu-id="0ac36-267">Aprire **SphereSounds** in Visual Studio, aggiornare il codice seguente e **salvare tutto**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-267">Open **SphereSounds** in Visual Studio, update the following code and **Save All**.</span></span>

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

* <span data-ttu-id="0ac36-268">Salvare lo script e tornare a Unity.</span><span class="sxs-lookup"><span data-stu-id="0ac36-268">Save the script, and return to Unity.</span></span>
* <span data-ttu-id="0ac36-269">Esportare, compilare e distribuire l'app in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0ac36-269">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="0ac36-270">Passare da una fase all'altra e da un lato all'altro per ascoltare le modifiche apportate ai suoni.</span><span class="sxs-lookup"><span data-stu-id="0ac36-270">Move closer and further from the Stage and turn side-to-side to hear the sounds change.</span></span>

## <a name="chapter-6---spatial-mapping"></a><span data-ttu-id="0ac36-271">Capitolo 6-mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="0ac36-271">Chapter 6 - Spatial mapping</span></span>

>[!VIDEO https://www.youtube.com/embed/Pkt1_wNLLXY]

<span data-ttu-id="0ac36-272">Ora verrà usato il [mapping spaziale](spatial-mapping.md) per collocare la lavagna del gioco su un oggetto reale nel mondo reale.</span><span class="sxs-lookup"><span data-stu-id="0ac36-272">Now we are going to use [spatial mapping](spatial-mapping.md) to place the game board on a real object in the real world.</span></span>

### <a name="objectives"></a><span data-ttu-id="0ac36-273">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="0ac36-273">Objectives</span></span>

* <span data-ttu-id="0ac36-274">Usa il mondo reale nel mondo virtuale.</span><span class="sxs-lookup"><span data-stu-id="0ac36-274">Bring your real world into the virtual world.</span></span>
* <span data-ttu-id="0ac36-275">Posizionare gli ologrammi in cui è importante.</span><span class="sxs-lookup"><span data-stu-id="0ac36-275">Place your holograms where they matter most to you.</span></span>

### <a name="instructions"></a><span data-ttu-id="0ac36-276">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="0ac36-276">Instructions</span></span>

* <span data-ttu-id="0ac36-277">In Unity fare clic sulla cartella **ologrammi** nel pannello del progetto.</span><span class="sxs-lookup"><span data-stu-id="0ac36-277">In Unity, click on the **Holograms** folder in the Project panel.</span></span>
* <span data-ttu-id="0ac36-278">Trascinare l'asset di **mapping spaziale** nella radice della **gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-278">Drag the **Spatial Mapping** asset into the root of the **Hierarchy**.</span></span>
* <span data-ttu-id="0ac36-279">Fare clic sull'oggetto **mapping spaziale** nella gerarchia.</span><span class="sxs-lookup"><span data-stu-id="0ac36-279">Click on the **Spatial Mapping** object in the Hierarchy.</span></span>
* <span data-ttu-id="0ac36-280">Nel **pannello Inspector**modificare le proprietà seguenti:</span><span class="sxs-lookup"><span data-stu-id="0ac36-280">In the **Inspector panel**, change the following properties:</span></span>
  * <span data-ttu-id="0ac36-281">Selezionare la casella per la **visualizzazione dei mesh** .</span><span class="sxs-lookup"><span data-stu-id="0ac36-281">Check the **Draw Visual Meshes** box.</span></span>
  * <span data-ttu-id="0ac36-282">Individuare il **materiale di estrazione** e fare clic sul cerchio a destra.</span><span class="sxs-lookup"><span data-stu-id="0ac36-282">Locate **Draw Material** and click the circle on the right.</span></span> <span data-ttu-id="0ac36-283">Digitare "**wireframe**" nel campo di ricerca nella parte superiore.</span><span class="sxs-lookup"><span data-stu-id="0ac36-283">Type "**wireframe**" into the search field at the top.</span></span> <span data-ttu-id="0ac36-284">Fare clic sul risultato, quindi chiudere la finestra.</span><span class="sxs-lookup"><span data-stu-id="0ac36-284">Click on the result and then close the window.</span></span> <span data-ttu-id="0ac36-285">Quando si esegue questa operazione, il valore per il materiale di estrazione dovrebbe essere impostato su wireframe.</span><span class="sxs-lookup"><span data-stu-id="0ac36-285">When you do this, the value for Draw Material should get set to Wireframe.</span></span>
* <span data-ttu-id="0ac36-286">Esportare, compilare e distribuire l'app in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0ac36-286">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="0ac36-287">Quando l'app viene eseguita, una mesh wireframe si sovrappone al mondo reale.</span><span class="sxs-lookup"><span data-stu-id="0ac36-287">When the app runs, a wireframe mesh will overlay your real world.</span></span>
* <span data-ttu-id="0ac36-288">Guarda in che modo una sfera in sequenza ricade sulla fase e sul pavimento!</span><span class="sxs-lookup"><span data-stu-id="0ac36-288">Watch how a rolling sphere will fall off the stage, and onto the floor!</span></span>

<span data-ttu-id="0ac36-289">Ora verrà illustrato come spostare l'oggetto Origamicollection in una nuova posizione:</span><span class="sxs-lookup"><span data-stu-id="0ac36-289">Now we'll show you how to move the OrigamiCollection to a new location:</span></span>

* <span data-ttu-id="0ac36-290">Nella cartella **Scripts** creare uno script denominato **TapToPlaceParent**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-290">In the **Scripts** folder, create a script named **TapToPlaceParent**.</span></span>
* <span data-ttu-id="0ac36-291">Nella **gerarchia**espandere **origamicollection** e selezionare l'oggetto **stage** .</span><span class="sxs-lookup"><span data-stu-id="0ac36-291">In the **Hierarchy**, expand the **OrigamiCollection** and select the **Stage** object.</span></span>
* <span data-ttu-id="0ac36-292">Trascinare lo script **TapToPlaceParent** nell'oggetto Stage.</span><span class="sxs-lookup"><span data-stu-id="0ac36-292">Drag the **TapToPlaceParent** script onto the Stage object.</span></span>
* <span data-ttu-id="0ac36-293">Aprire lo script **TapToPlaceParent** in Visual Studio e aggiornarlo come segue:</span><span class="sxs-lookup"><span data-stu-id="0ac36-293">Open the **TapToPlaceParent** script in Visual Studio, and update it to be the following:</span></span>

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

* <span data-ttu-id="0ac36-294">Esportare, compilare e distribuire l'app.</span><span class="sxs-lookup"><span data-stu-id="0ac36-294">Export, build and deploy the app.</span></span>
* <span data-ttu-id="0ac36-295">A questo punto dovrebbe essere possibile collocare il gioco in una posizione specifica guardandolo, usando il gesto di selezione e quindi passando a una nuova posizione e usando di nuovo il movimento di selezione.</span><span class="sxs-lookup"><span data-stu-id="0ac36-295">Now you should now be able to place the game in a specific location by gazing at it, using the Select gesture and then moving to a new location, and using the Select gesture again.</span></span>

## <a name="chapter-7---holographic-fun"></a><span data-ttu-id="0ac36-296">Capitolo 7-di divertimento olografico</span><span class="sxs-lookup"><span data-stu-id="0ac36-296">Chapter 7 - Holographic fun</span></span>

### <a name="objectives"></a><span data-ttu-id="0ac36-297">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="0ac36-297">Objectives</span></span>

* <span data-ttu-id="0ac36-298">Rivelare l'ingresso a un Sottomondo olografico.</span><span class="sxs-lookup"><span data-stu-id="0ac36-298">Reveal the entrance to a holographic underworld.</span></span>

### <a name="instructions"></a><span data-ttu-id="0ac36-299">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="0ac36-299">Instructions</span></span>

<span data-ttu-id="0ac36-300">Ora verrà illustrato come scoprire il Sottomondo olografico:</span><span class="sxs-lookup"><span data-stu-id="0ac36-300">Now we'll show you how to uncover the holographic underworld:</span></span>

* <span data-ttu-id="0ac36-301">Dalla cartella **ologrammi** nel pannello del progetto:</span><span class="sxs-lookup"><span data-stu-id="0ac36-301">From the **Holograms** folder in the Project Panel:</span></span>
  * <span data-ttu-id="0ac36-302">Trascinare **Underworld** nella gerarchia in modo che sia un elemento figlio di **origamicollection**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-302">Drag **Underworld** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="0ac36-303">Nella cartella **Scripts** creare uno script denominato **HitTarget**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-303">In the **Scripts** folder, create a script named **HitTarget**.</span></span>
* <span data-ttu-id="0ac36-304">Nella **gerarchia**espandere **origamicollection**.</span><span class="sxs-lookup"><span data-stu-id="0ac36-304">In the **Hierarchy**, expand the **OrigamiCollection**.</span></span>
* <span data-ttu-id="0ac36-305">Espandere l'oggetto **fase** e selezionare l'oggetto di **destinazione** (ventola blu).</span><span class="sxs-lookup"><span data-stu-id="0ac36-305">Expand the **Stage** object and select the **Target** object (blue fan).</span></span>
* <span data-ttu-id="0ac36-306">Trascinare lo script **HitTarget** nell'oggetto di **destinazione** .</span><span class="sxs-lookup"><span data-stu-id="0ac36-306">Drag the **HitTarget** script onto the **Target** object.</span></span>
* <span data-ttu-id="0ac36-307">Aprire lo script **HitTarget** in Visual Studio e aggiornarlo come segue:</span><span class="sxs-lookup"><span data-stu-id="0ac36-307">Open the **HitTarget** script in Visual Studio, and update it to be the following:</span></span>

```cs
using UnityEngine;

public class HitTarget : MonoBehaviour
{
    // These public fields become settable properties in the Unity editor.
    public GameObject underworld;
    public GameObject objectToHide;

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Hide the stage and show the underworld.
        objectToHide.SetActive(false);
        underworld.SetActive(true);

        // Disable Spatial Mapping to let the spheres enter the underworld.
        SpatialMapping.Instance.MappingEnabled = false;
    }
}
```

* <span data-ttu-id="0ac36-308">In Unity selezionare l'oggetto di **destinazione** .</span><span class="sxs-lookup"><span data-stu-id="0ac36-308">In Unity, select the **Target** object.</span></span>
* <span data-ttu-id="0ac36-309">Due proprietà pubbliche sono ora visibili nel componente **hit target** ed è necessario fare riferimento agli oggetti nella scena:</span><span class="sxs-lookup"><span data-stu-id="0ac36-309">Two public properties are now visible on the **Hit Target** component and need to reference objects in our scene:</span></span>
  * <span data-ttu-id="0ac36-310">Trascinare **Underworld** dal pannello **gerarchia** alla proprietà **Underworld** sul componente **hit target** .</span><span class="sxs-lookup"><span data-stu-id="0ac36-310">Drag **Underworld** from the **Hierarchy** panel to the **Underworld** property on the **Hit Target** component.</span></span>
  * <span data-ttu-id="0ac36-311">Trascinare **stage** dal pannello **gerarchia** all' **oggetto per nascondere** la proprietà nel componente **hit target** .</span><span class="sxs-lookup"><span data-stu-id="0ac36-311">Drag **Stage** from the **Hierarchy** panel to the **Object to Hide** property on the **Hit Target** component.</span></span>
* <span data-ttu-id="0ac36-312">Esportare, compilare e distribuire l'app.</span><span class="sxs-lookup"><span data-stu-id="0ac36-312">Export, build and deploy the app.</span></span>
* <span data-ttu-id="0ac36-313">Posizionare la raccolta origami sul pavimento e quindi usare il gesto di selezione per creare una Drop della sfera.</span><span class="sxs-lookup"><span data-stu-id="0ac36-313">Place the Origami Collection on the floor, and then use the Select gesture to make a sphere drop.</span></span>
* <span data-ttu-id="0ac36-314">Quando la sfera raggiunge la destinazione (ventola blu), si verificherà un'esplosione.</span><span class="sxs-lookup"><span data-stu-id="0ac36-314">When the sphere hits the target (blue fan), an explosion will occur.</span></span> <span data-ttu-id="0ac36-315">La raccolta verrà nascosta e verrà visualizzato un foro nel Sottomondo.</span><span class="sxs-lookup"><span data-stu-id="0ac36-315">The collection will be hidden and a hole to the underworld will appear.</span></span>

## <a name="the-end"></a><span data-ttu-id="0ac36-316">La fine</span><span class="sxs-lookup"><span data-stu-id="0ac36-316">The end</span></span>

<span data-ttu-id="0ac36-317">Questa è la fine di questa esercitazione.</span><span class="sxs-lookup"><span data-stu-id="0ac36-317">And that's the end of this tutorial!</span></span>

<span data-ttu-id="0ac36-318">Si è appreso quanto segue:</span><span class="sxs-lookup"><span data-stu-id="0ac36-318">You learned:</span></span>

* <span data-ttu-id="0ac36-319">Come creare un'app olografica in Unity.</span><span class="sxs-lookup"><span data-stu-id="0ac36-319">How to create a holographic app in Unity.</span></span>
* <span data-ttu-id="0ac36-320">Come usare lo sguardo, il movimento, la voce, il suono e il mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="0ac36-320">How to make use of gaze, gesture, voice, sound, and spatial mapping.</span></span>
* <span data-ttu-id="0ac36-321">Come compilare e distribuire un'app con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0ac36-321">How to build and deploy an app using Visual Studio.</span></span>

<span data-ttu-id="0ac36-322">A questo punto è possibile iniziare a creare una propria esperienza olografica.</span><span class="sxs-lookup"><span data-stu-id="0ac36-322">You are now ready to start creating your own holographic experience!</span></span>

## <a name="see-also"></a><span data-ttu-id="0ac36-323">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="0ac36-323">See also</span></span>

* [<span data-ttu-id="0ac36-324">Nozioni di base su 101E: completare il progetto con l'emulatore</span><span class="sxs-lookup"><span data-stu-id="0ac36-324">MR Basics 101E: Complete project with emulator</span></span>](holograms-101e.md)
* [<span data-ttu-id="0ac36-325">Sguardo fisso</span><span class="sxs-lookup"><span data-stu-id="0ac36-325">Gaze</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="0ac36-326">Puntamento con la testa e commit</span><span class="sxs-lookup"><span data-stu-id="0ac36-326">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="0ac36-327">Input vocale</span><span class="sxs-lookup"><span data-stu-id="0ac36-327">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="0ac36-328">Audio spaziale</span><span class="sxs-lookup"><span data-stu-id="0ac36-328">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="0ac36-329">Mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="0ac36-329">Spatial mapping</span></span>](spatial-mapping.md)

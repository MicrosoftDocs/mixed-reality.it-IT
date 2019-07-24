---
title: MR sharing 240-più dispositivi HoloLens
description: Seguire questa procedura dettagliata di codifica usando Unity, Visual Studio e HoloLens per informazioni dettagliate sulla condivisione degli ologrammi.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, condivisione, rete, Accademia, esercitazione
ms.openlocfilehash: 70a39a739d360a5032bc8df76b6f0bd57521d9ec
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522338"
---
>[!NOTE]
><span data-ttu-id="c3aa2-104">Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="c3aa2-105">Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="c3aa2-106">Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="c3aa2-107">Verranno mantenuti per continuare a usare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="c3aa2-108">In futuro sarà disponibile una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="c3aa2-109">Questo avviso verrà aggiornato con un collegamento a queste esercitazioni quando vengono pubblicate.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-sharing-240-multiple-hololens-devices"></a><span data-ttu-id="c3aa2-110">MR sharing 240: Più dispositivi HoloLens</span><span class="sxs-lookup"><span data-stu-id="c3aa2-110">MR Sharing 240: Multiple HoloLens devices</span></span>

<span data-ttu-id="c3aa2-111">Gli ologrammi ricevono una presenza nel nostro mondo rimanendo al posto mentre ci si sposta nello spazio.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-111">Holograms are given presence in our world by remaining in place as we move about in space.</span></span> <span data-ttu-id="c3aa2-112">HoloLens mantiene gli ologrammi sul posto usando vari [sistemi di coordinate](coordinate-systems.md) per tenere traccia della posizione e dell'orientamento degli oggetti.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-112">HoloLens keeps holograms in place by using various [coordinate systems](coordinate-systems.md) to keep track of the location and orientation of objects.</span></span> <span data-ttu-id="c3aa2-113">Quando si condividono questi sistemi di coordinate tra i dispositivi, è possibile creare un'esperienza condivisa che ci consenta di partecipare a un mondo olografico condiviso.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-113">When we share these coordinate systems between devices, we can create a shared experience that allows us to take part in a shared holographic world.</span></span>

<span data-ttu-id="c3aa2-114">In questa esercitazione verrà:</span><span class="sxs-lookup"><span data-stu-id="c3aa2-114">In this tutorial, we will:</span></span>

* <span data-ttu-id="c3aa2-115">Configurare una rete per un'esperienza condivisa.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-115">Setup a network for a shared experience.</span></span>
* <span data-ttu-id="c3aa2-116">Condividere gli ologrammi tra i dispositivi HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-116">Share holograms across HoloLens devices.</span></span>
* <span data-ttu-id="c3aa2-117">Scopri altre persone nel nostro mondo olografico condiviso.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-117">Discover other people in our shared holographic world.</span></span>
* <span data-ttu-id="c3aa2-118">Consente di creare un'esperienza interattiva condivisa in cui è possibile fare riferimento ad altri giocatori e avviare i loro proiettili.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-118">Create a shared interactive experience where you can target other players - and launch projectiles at them!</span></span>

## <a name="device-support"></a><span data-ttu-id="c3aa2-119">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="c3aa2-119">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="c3aa2-120">Corso</span><span class="sxs-lookup"><span data-stu-id="c3aa2-120">Course</span></span></th><th style="width:150px"> <span data-ttu-id="c3aa2-121"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="c3aa2-121"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="c3aa2-122"><a href="immersive-headset-hardware-details.md">Visori VR immersive</a></span><span class="sxs-lookup"><span data-stu-id="c3aa2-122"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="c3aa2-123">MR sharing 240: Più dispositivi HoloLens</span><span class="sxs-lookup"><span data-stu-id="c3aa2-123">MR Sharing 240: Multiple HoloLens devices</span></span></td><td style="text-align: center;"> <span data-ttu-id="c3aa2-124">✔️</span><span class="sxs-lookup"><span data-stu-id="c3aa2-124">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="c3aa2-125">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="c3aa2-125">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="c3aa2-126">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="c3aa2-126">Prerequisites</span></span>

* <span data-ttu-id="c3aa2-127">Un PC Windows 10 configurato con gli [strumenti corretti installati](install-the-tools.md) con accesso a Internet.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-127">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md) with Internet access.</span></span>
* <span data-ttu-id="c3aa2-128">Almeno due dispositivi HoloLens configurati [per lo sviluppo](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="c3aa2-128">At least two HoloLens devices [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="c3aa2-129">File di progetto</span><span class="sxs-lookup"><span data-stu-id="c3aa2-129">Project files</span></span>

* <span data-ttu-id="c3aa2-130">Scaricare i [file](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) richiesti dal progetto.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-130">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) required by the project.</span></span> <span data-ttu-id="c3aa2-131">Richiede Unity 2017,2 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-131">Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="c3aa2-132">Se è ancora necessario il supporto per Unity 5,6, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).</span><span class="sxs-lookup"><span data-stu-id="c3aa2-132">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).</span></span>
  * <span data-ttu-id="c3aa2-133">Se è ancora necessario il supporto per Unity 5,5, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).</span><span class="sxs-lookup"><span data-stu-id="c3aa2-133">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).</span></span>
  * <span data-ttu-id="c3aa2-134">Se è ancora necessario il supporto per Unity 5,4, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).</span><span class="sxs-lookup"><span data-stu-id="c3aa2-134">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).</span></span>
* <span data-ttu-id="c3aa2-135">Annullare l'archiviazione dei file sul desktop o in un'altra posizione facile da raggiungere.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-135">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="c3aa2-136">Mantenendo il nome della cartella **SharedHolograms**.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-136">Keep the folder name as **SharedHolograms**.</span></span>

>[!NOTE]
><span data-ttu-id="c3aa2-137">Se si vuole esaminare il codice sorgente prima del download, è [disponibile in GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).</span><span class="sxs-lookup"><span data-stu-id="c3aa2-137">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="c3aa2-138">Capitolo 1-Holo World</span><span class="sxs-lookup"><span data-stu-id="c3aa2-138">Chapter 1 - Holo World</span></span>

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

<span data-ttu-id="c3aa2-139">In questo capitolo verrà configurato il primo progetto Unity ed eseguiamo il processo di compilazione e distribuzione.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-139">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="c3aa2-140">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="c3aa2-140">Objectives</span></span>

* <span data-ttu-id="c3aa2-141">Configurare Unity per sviluppare app olografiche.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-141">Setup Unity to develop holographic apps.</span></span>
* <span data-ttu-id="c3aa2-142">Vedi l'ologramma!</span><span class="sxs-lookup"><span data-stu-id="c3aa2-142">See your hologram!</span></span>

### <a name="instructions"></a><span data-ttu-id="c3aa2-143">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="c3aa2-143">Instructions</span></span>

* <span data-ttu-id="c3aa2-144">Avvia Unity.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-144">Start Unity.</span></span>
* <span data-ttu-id="c3aa2-145">Selezionare **Apri**.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-145">Select **Open**.</span></span>
* <span data-ttu-id="c3aa2-146">Immettere il percorso come cartella **SharedHolograms** precedentemente non archiviata.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-146">Enter location as the **SharedHolograms** folder you previously unarchived.</span></span>
* <span data-ttu-id="c3aa2-147">Selezionare **nome progetto** e fare clic su **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-147">Select **Project Name** and click **Select Folder**.</span></span>
* <span data-ttu-id="c3aa2-148">Nella **gerarchia**, fare clic con il pulsante destro del mouse sulla **fotocamera principale** e scegliere **Elimina**.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-148">In the **Hierarchy**, right-click the **Main Camera** and select **Delete**.</span></span>
* <span data-ttu-id="c3aa2-149">Nella cartella **HoloToolkit-sharing-240/Prefabbricates/camera** trovare la prefabbricata **principale della fotocamera** .</span><span class="sxs-lookup"><span data-stu-id="c3aa2-149">In the **HoloToolkit-Sharing-240/Prefabs/Camera** folder, find the **Main Camera** prefab.</span></span>
* <span data-ttu-id="c3aa2-150">Trascinare e rilasciare la **fotocamera principale** nella **gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-150">Drag and drop the **Main Camera** into the **Hierarchy**.</span></span>
* <span data-ttu-id="c3aa2-151">Nella **gerarchia**fare clic su **Crea** e **Crea vuoto**.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-151">In the **Hierarchy**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="c3aa2-152">Fare clic con il pulsante destro del mouse sul nuovo **GameObject** e scegliere **Rinomina**.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-152">Right-click the new **GameObject** and select **Rename**.</span></span>
* <span data-ttu-id="c3aa2-153">Rinominare GameObject in **ologrammcollection**.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-153">Rename the GameObject to **HologramCollection**.</span></span>
* <span data-ttu-id="c3aa2-154">Selezionare l'  oggetto ologrammcollection nella **gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-154">Select the **HologramCollection** object in the **Hierarchy**.</span></span>
* <span data-ttu-id="c3aa2-155">Nel **controllo** impostare la **posizione di trasformazione** su: **X 0, Y:-0,25, Z: 2**.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-155">In the **Inspector** set the **transform position** to: **X: 0, Y: -0.25, Z: 2**.</span></span>
* <span data-ttu-id="c3aa2-156">Nella cartella **olografici** del pannello del **progetto**individuare l'asset **EnergyHub** .</span><span class="sxs-lookup"><span data-stu-id="c3aa2-156">In the **Holograms** folder in the **Project panel**, find the **EnergyHub** asset.</span></span>
* <span data-ttu-id="c3aa2-157">Trascinare e rilasciare l'oggetto **EnergyHub** dal **pannello progetto** alla **gerarchia** come **elemento figlio di ologrammcollection**.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-157">Drag and drop the **EnergyHub** object from the **Project panel** to the **Hierarchy** as a **child of HologramCollection**.</span></span>
* <span data-ttu-id="c3aa2-158">Seleziona **File > Salva scena con nome...**</span><span class="sxs-lookup"><span data-stu-id="c3aa2-158">Select **File > Save Scene As...**</span></span>
* <span data-ttu-id="c3aa2-159">Assegnare alla scena il nome **SharedHolograms** e fare clic su **Save**.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-159">Name the scene **SharedHolograms** and click **Save**.</span></span>
* <span data-ttu-id="c3aa2-160">Premere il pulsante **Play** in Unity per visualizzare l'anteprima degli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-160">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="c3aa2-161">Premere  Riproduci una seconda volta per arrestare la modalità di anteprima.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-161">Press **Play** a second time to stop preview mode.</span></span>

<span data-ttu-id="c3aa2-162">**Esportare il progetto da Unity a Visual Studio**</span><span class="sxs-lookup"><span data-stu-id="c3aa2-162">**Export the project from Unity to Visual Studio**</span></span>
* <span data-ttu-id="c3aa2-163">In Unity selezionare **File > impostazioni di compilazione**.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-163">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="c3aa2-164">Fare clic su **Aggiungi scene aperte** per aggiungere la scena.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-164">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="c3aa2-165">Selezionare **piattaforma UWP (Universal Windows Platform)** nell'elenco **piattaforma** e fare clic su **Cambia piattaforma**.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-165">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="c3aa2-166">Impostare **SDK** su **Universal 10**.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-166">Set **SDK** to **Universal 10**.</span></span>
* <span data-ttu-id="c3aa2-167">Impostare il **dispositivo di destinazione** su **HoloLens** e il **tipo di compilazione UWP** su **D3D**.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-167">Set **Target device** to **HoloLens** and **UWP Build Type** to **D3D**.</span></span>
* <span data-ttu-id="c3aa2-168">Controllare **i C# progetti Unity**.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-168">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="c3aa2-169">Fai clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-169">Click **Build**.</span></span>
* <span data-ttu-id="c3aa2-170">Nella finestra Esplora file visualizzata creare una **nuova cartella** denominata "app".</span><span class="sxs-lookup"><span data-stu-id="c3aa2-170">In the file explorer window that appears, create a **New Folder** named "App".</span></span>
* <span data-ttu-id="c3aa2-171">Fare clic sulla cartella dell' **app** .</span><span class="sxs-lookup"><span data-stu-id="c3aa2-171">Single click the **App** folder.</span></span>
* <span data-ttu-id="c3aa2-172">Premere **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-172">Press **Select Folder**.</span></span>
* <span data-ttu-id="c3aa2-173">Quando si esegue Unity, viene visualizzata una finestra Esplora file.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-173">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="c3aa2-174">Aprire la cartella dell' **app** .</span><span class="sxs-lookup"><span data-stu-id="c3aa2-174">Open the **App** folder.</span></span>
* <span data-ttu-id="c3aa2-175">Aprire **SharedHolograms. sln** per avviare Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-175">Open **SharedHolograms.sln** to launch Visual Studio.</span></span>
* <span data-ttu-id="c3aa2-176">Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione da debug a **Release** e da ARM a **x86**.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-176">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
* <span data-ttu-id="c3aa2-177">Fare clic sulla freccia a discesa accanto a computer locale e selezionare **dispositivo remoto**.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-177">Click on the drop-down arrow next to Local Machine, and select **Remote Device**.</span></span>
    * <span data-ttu-id="c3aa2-178">Impostare l' **Indirizzo** sul nome o sull'indirizzo IP del HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-178">Set the **Address** to the name or IP address of your HoloLens.</span></span> <span data-ttu-id="c3aa2-179">Se non si conosce l'indirizzo IP del dispositivo, controllare **le impostazioni > rete & Internet > opzioni avanzate** o richiedere a Cortana **"Hey Cortana, qual è il mio indirizzo IP?"**</span><span class="sxs-lookup"><span data-stu-id="c3aa2-179">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** or ask Cortana **"Hey Cortana, What's my IP address?"**</span></span>
    * <span data-ttu-id="c3aa2-180">Lasciare la **modalità di autenticazione** impostata su **universale**.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-180">Leave the **Authentication Mode** set to **Universal**.</span></span>
    * <span data-ttu-id="c3aa2-181">Fare clic su **Seleziona**</span><span class="sxs-lookup"><span data-stu-id="c3aa2-181">Click **Select**</span></span>
* <span data-ttu-id="c3aa2-182">Fare clic su **debug > avvia senza eseguire debug** o premere **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-182">Click **Debug > Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="c3aa2-183">Se questa è la prima volta che si esegue la distribuzione nel dispositivo, sarà necessario associarla a [Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span><span class="sxs-lookup"><span data-stu-id="c3aa2-183">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
* <span data-ttu-id="c3aa2-184">Inserire il HoloLens e trovare l'ologramma di EnergyHub.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-184">Put on your HoloLens and find the EnergyHub hologram.</span></span>

## <a name="chapter-2---interaction"></a><span data-ttu-id="c3aa2-185">Capitolo 2-interazione</span><span class="sxs-lookup"><span data-stu-id="c3aa2-185">Chapter 2 - Interaction</span></span>

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

<span data-ttu-id="c3aa2-186">In questo capitolo si interagisce con gli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-186">In this chapter, we'll interact with our holograms.</span></span> <span data-ttu-id="c3aa2-187">Prima di tutto, verrà aggiunto un cursore per visualizzare lo [sguardo](gaze.md).</span><span class="sxs-lookup"><span data-stu-id="c3aa2-187">First, we'll add a cursor to visualize our [Gaze](gaze.md).</span></span> <span data-ttu-id="c3aa2-188">Quindi, aggiungiamo i [movimenti](gestures.md) e usiamo la mano per inserire gli ologrammi nello spazio.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-188">Then, we'll add [Gestures](gestures.md) and use our hand to place our holograms in space.</span></span>

### <a name="objectives"></a><span data-ttu-id="c3aa2-189">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="c3aa2-189">Objectives</span></span>

* <span data-ttu-id="c3aa2-190">Utilizzare l'input di sguardi per controllare un cursore.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-190">Use gaze input to control a cursor.</span></span>
* <span data-ttu-id="c3aa2-191">Usare l'input dei movimenti per interagire con gli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-191">Use gesture input to interact with holograms.</span></span>

### <a name="instructions"></a><span data-ttu-id="c3aa2-192">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="c3aa2-192">Instructions</span></span>

<span data-ttu-id="c3aa2-193">**Sguardo fisso**</span><span class="sxs-lookup"><span data-stu-id="c3aa2-193">**Gaze**</span></span>
* <span data-ttu-id="c3aa2-194">Nel **Pannello gerarchia** selezionare l'oggetto **ologrammcollection** .</span><span class="sxs-lookup"><span data-stu-id="c3aa2-194">In the **Hierarchy panel** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="c3aa2-195">Nel **Pannello di controllo** fare clic sul pulsante **Aggiungi componente** .</span><span class="sxs-lookup"><span data-stu-id="c3aa2-195">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="c3aa2-196">Nel menu digitare nella casella di ricerca lo **sguardo Manager**.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-196">In the menu, type in the search box **Gaze Manager**.</span></span> <span data-ttu-id="c3aa2-197">Selezionare il risultato della ricerca.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-197">Select the search result.</span></span>
* <span data-ttu-id="c3aa2-198">Nella cartella **HoloToolkit-sharing-240\Prefabs\Input** trovare il **cursore** asset.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-198">In the **HoloToolkit-Sharing-240\Prefabs\Input** folder, find the **Cursor** asset.</span></span>
* <span data-ttu-id="c3aa2-199">Trascinare e rilasciare l'asset del **cursore** nella **gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-199">Drag and drop the **Cursor** asset onto the **Hierarchy**.</span></span>

<span data-ttu-id="c3aa2-200">**Gesto**</span><span class="sxs-lookup"><span data-stu-id="c3aa2-200">**Gesture**</span></span>
* <span data-ttu-id="c3aa2-201">Nel **Pannello gerarchia** selezionare l'oggetto **ologrammcollection** .</span><span class="sxs-lookup"><span data-stu-id="c3aa2-201">In the **Hierarchy panel** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="c3aa2-202">Fare clic su **Aggiungi componente** e digitare **gestione movimenti** nel campo di ricerca.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-202">Click **Add Component** and type **Gesture Manager** in the search field.</span></span> <span data-ttu-id="c3aa2-203">Selezionare il risultato della ricerca.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-203">Select the search result.</span></span>
* <span data-ttu-id="c3aa2-204">Nel **Pannello gerarchia**espandere ologrammcollection .</span><span class="sxs-lookup"><span data-stu-id="c3aa2-204">In the **Hierarchy panel**, expand **HologramCollection**.</span></span>
* <span data-ttu-id="c3aa2-205">Selezionare l'oggetto **EnergyHub** figlio.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-205">Select the child **EnergyHub** object.</span></span>
* <span data-ttu-id="c3aa2-206">Nel **Pannello di controllo** fare clic sul pulsante **Aggiungi componente** .</span><span class="sxs-lookup"><span data-stu-id="c3aa2-206">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="c3aa2-207">Nel menu digitare nella casella di ricerca **posizionamento ologrammi**.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-207">In the menu, type in the search box **Hologram Placement**.</span></span> <span data-ttu-id="c3aa2-208">Selezionare il risultato della ricerca.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-208">Select the search result.</span></span>
* <span data-ttu-id="c3aa2-209">Salvare la scena selezionando **File > Salva scena**.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-209">Save the scene by selecting **File > Save Scene**.</span></span>

<span data-ttu-id="c3aa2-210">**Distribuisci e goditi**</span><span class="sxs-lookup"><span data-stu-id="c3aa2-210">**Deploy and enjoy**</span></span>
* <span data-ttu-id="c3aa2-211">Eseguire la compilazione e la distribuzione nella HoloLens usando le istruzioni del capitolo precedente.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-211">Build and deploy to your HoloLens, using the instructions from the previous chapter.</span></span>
* <span data-ttu-id="c3aa2-212">Una volta avviata l'app nella HoloLens, sposta la tua parte e osserva il modo in cui il EnergyHub segue il tuo sguardo.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-212">Once the app launches on your HoloLens, move your head around and notice how the EnergyHub follows your gaze.</span></span>
* <span data-ttu-id="c3aa2-213">Si noti come viene visualizzato il cursore quando si guarda l'ologramma e si passa a una luce puntiforme senza guardare un ologramma.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-213">Notice how the cursor appears when you gaze upon the hologram, and changes to a point light when not gazing at a hologram.</span></span>
* <span data-ttu-id="c3aa2-214">Eseguire un tocco aereo per posizionare l'ologramma.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-214">Perform an air-tap to place the hologram.</span></span> <span data-ttu-id="c3aa2-215">Al momento del progetto, è possibile inserire l'ologramma una sola volta (Ridistribuisci per riprovare).</span><span class="sxs-lookup"><span data-stu-id="c3aa2-215">At this time in our project, you can only place the hologram once (redeploy to try again).</span></span>

## <a name="chapter-3---shared-coordinates"></a><span data-ttu-id="c3aa2-216">Capitolo 3-Coordinate condivise</span><span class="sxs-lookup"><span data-stu-id="c3aa2-216">Chapter 3 - Shared Coordinates</span></span>

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

<span data-ttu-id="c3aa2-217">È divertente vedere e interagire con gli ologrammi, ma andiamo oltre.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-217">It's fun to see and interact with holograms, but let's go further.</span></span> <span data-ttu-id="c3aa2-218">Verrà configurata la prima esperienza condivisa, ovvero un ologramma che tutti gli utenti possono vedere insieme.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-218">We'll set up our first shared experience - a hologram everyone can see together.</span></span>

### <a name="objectives"></a><span data-ttu-id="c3aa2-219">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="c3aa2-219">Objectives</span></span>

* <span data-ttu-id="c3aa2-220">Configurare una rete per un'esperienza condivisa.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-220">Setup a network for a shared experience.</span></span>
* <span data-ttu-id="c3aa2-221">Stabilire un punto di riferimento comune.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-221">Establish a common reference point.</span></span>
* <span data-ttu-id="c3aa2-222">Condividere i sistemi di coordinate tra dispositivi.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-222">Share coordinate systems across devices.</span></span>
* <span data-ttu-id="c3aa2-223">Tutti gli utenti vedono lo stesso ologramma!</span><span class="sxs-lookup"><span data-stu-id="c3aa2-223">Everyone sees the same hologram!</span></span>

>[!NOTE]
><span data-ttu-id="c3aa2-224">Per la connessione di un'app al server di condivisione, è necessario dichiarare le funzionalità **InternetClientServer** e **PrivateNetworkClientServer** .</span><span class="sxs-lookup"><span data-stu-id="c3aa2-224">The **InternetClientServer** and **PrivateNetworkClientServer** capabilities must be declared for an app to connect to the sharing server.</span></span> <span data-ttu-id="c3aa2-225">Questa operazione viene eseguita per gli ologrammi 240, ma è necessario tenerla presente per i propri progetti.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-225">This is done for you already in Holograms 240, but keep this in mind for your own projects.</span></span>
>1. <span data-ttu-id="c3aa2-226">Nell'editor di Unity passare a Impostazioni lettore passando a "Modifica > Impostazioni progetto > lettore"</span><span class="sxs-lookup"><span data-stu-id="c3aa2-226">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="c3aa2-227">Fare clic sulla scheda "Windows Store"</span><span class="sxs-lookup"><span data-stu-id="c3aa2-227">Click on the "Windows Store" tab</span></span>
>3. <span data-ttu-id="c3aa2-228">Nella sezione "impostazioni di pubblicazione > funzionalità" controllare la funzionalità **InternetClientServer** e la funzionalità **PrivateNetworkClientServer**</span><span class="sxs-lookup"><span data-stu-id="c3aa2-228">In the "Publishing Settings > Capabilities" section, check the **InternetClientServer** capability and the **PrivateNetworkClientServer** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="c3aa2-229">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="c3aa2-229">Instructions</span></span>

* <span data-ttu-id="c3aa2-230">Nel **Pannello del progetto** passare alla cartella **HoloToolkit-sharing-240\Prefabs\Sharing**</span><span class="sxs-lookup"><span data-stu-id="c3aa2-230">In the **Project panel** navigate to the **HoloToolkit-Sharing-240\Prefabs\Sharing** folder.</span></span>
* <span data-ttu-id="c3aa2-231">Trascinare e rilasciare il prefabbricato di **condivisione** nel **Pannello gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-231">Drag and drop the **Sharing** prefab into the **Hierarchy panel**.</span></span>

<span data-ttu-id="c3aa2-232">Successivamente, è necessario avviare il servizio di condivisione.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-232">Next we need to launch the sharing service.</span></span> <span data-ttu-id="c3aa2-233">È necessario eseguire questo passaggio solo per **un PC** nell'esperienza condivisa.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-233">Only **one PC** in the shared experience needs to do this step.</span></span>
* <span data-ttu-id="c3aa2-234">In Unity-nel menu in alto a destra selezionare il **menu HoloToolkit-sharing-240**.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-234">In Unity - in the top-hand menu - select the **HoloToolkit-Sharing-240 menu**.</span></span>
* <span data-ttu-id="c3aa2-235">Selezionare l'elemento **avvio condivisione servizio** nell'elenco a discesa.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-235">Select the **Launch Sharing Service** item in the drop-down.</span></span>
* <span data-ttu-id="c3aa2-236">Selezionare l'opzione **rete privata** e fare clic su **Consenti accesso** quando viene visualizzato il prompt del firewall.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-236">Check the **Private Network** option and click **Allow Access** when the firewall prompt appears.</span></span>
* <span data-ttu-id="c3aa2-237">Annotare l'indirizzo IPv4 visualizzato nella finestra della console del servizio di condivisione.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-237">Note down the IPv4 address displayed in the Sharing Service console window.</span></span> <span data-ttu-id="c3aa2-238">Si tratta dello stesso IP del computer in cui viene eseguito il servizio.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-238">This is the same IP as the machine the service is being run on.</span></span>

<span data-ttu-id="c3aa2-239">Seguire le istruzioni restanti in **tutti i PC** che faranno parte dell'esperienza condivisa.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-239">Follow the rest of the instructions on **all PCs** that will join the shared experience.</span></span>
* <span data-ttu-id="c3aa2-240">Nella **gerarchia**selezionare l'oggetto di **condivisione** .</span><span class="sxs-lookup"><span data-stu-id="c3aa2-240">In the **Hierarchy**, select the **Sharing** object.</span></span>
* <span data-ttu-id="c3aa2-241">In **controllo**, nel componente **fase di condivisione** , modificare l' **indirizzo del server** da "localhost" all'indirizzo IPv4 del computer che esegue SharingService. exe.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-241">In the **Inspector**, on the **Sharing Stage** component, change the **Server Address** from 'localhost' to the IPv4 address of the machine running SharingService.exe.</span></span>
* <span data-ttu-id="c3aa2-242">Nella **gerarchia** selezionare l'oggetto **ologrammcollection** .</span><span class="sxs-lookup"><span data-stu-id="c3aa2-242">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="c3aa2-243">Nel **controllo** fare clic sul pulsante **Aggiungi componente** .</span><span class="sxs-lookup"><span data-stu-id="c3aa2-243">In the **Inspector** click the **Add Component** button.</span></span>
* <span data-ttu-id="c3aa2-244">Nella casella di ricerca digitare **Import Export Anchor Manager**.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-244">In the search box, type **Import Export Anchor Manager**.</span></span> <span data-ttu-id="c3aa2-245">Selezionare il risultato della ricerca.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-245">Select the search result.</span></span>
* <span data-ttu-id="c3aa2-246">Nel **pannello progetto** passare alla cartella **script** .</span><span class="sxs-lookup"><span data-stu-id="c3aa2-246">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="c3aa2-247">Fare doppio clic sullo script **HologramPlacement** per aprirlo in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-247">Double-click the **HologramPlacement** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="c3aa2-248">Sostituire il contenuto con il codice seguente.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-248">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the anchor model.
    /// The anchor model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    private bool animationPlayed = false;

    void Start()
    {
        // We care about getting updates for the anchor transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the anchor transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the anchor if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    void Update()
    {
        if (GotTransform)
        {
            if (ImportExportAnchorManager.Instance.AnchorEstablished &&
                animationPlayed == false)
            {
                // This triggers the animation sequence for the anchor model and 
                // puts the cool materials on the model.
                GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                animationPlayed = true;
            }
        }
        else
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the anchor 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;
        
        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the anchor to do its animation and
        // swap its materials.
        if (GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* <span data-ttu-id="c3aa2-249">Tornare in Unity, selezionare **ologrammcollection** nel **Pannello gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-249">Back in Unity, select the **HologramCollection** in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="c3aa2-250">Nel **Pannello di controllo** fare clic sul pulsante **Aggiungi componente** .</span><span class="sxs-lookup"><span data-stu-id="c3aa2-250">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="c3aa2-251">Nel menu digitare nella casella di ricerca **Gestione stato app**.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-251">In the menu, type in the search box **App State Manager**.</span></span> <span data-ttu-id="c3aa2-252">Selezionare il risultato della ricerca.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-252">Select the search result.</span></span>

<span data-ttu-id="c3aa2-253">**Distribuisci e goditi**</span><span class="sxs-lookup"><span data-stu-id="c3aa2-253">**Deploy and enjoy**</span></span>
* <span data-ttu-id="c3aa2-254">Compilare il progetto per i dispositivi HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-254">Build the project for your HoloLens devices.</span></span>
* <span data-ttu-id="c3aa2-255">Designare un HoloLens per la distribuzione iniziale.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-255">Designate one HoloLens to deploy to first.</span></span> <span data-ttu-id="c3aa2-256">È necessario attendere che il punto di ancoraggio venga caricato nel servizio prima di poter inserire il EnergyHub (questa operazione può richiedere circa 30-60 secondi).</span><span class="sxs-lookup"><span data-stu-id="c3aa2-256">You will need to wait for the Anchor to be uploaded to the service before you can place the EnergyHub (this can take ~30-60 seconds).</span></span> <span data-ttu-id="c3aa2-257">Fino al termine del caricamento, i movimenti Tap verranno ignorati.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-257">Until the upload is done, your tap gestures will be ignored.</span></span>
* <span data-ttu-id="c3aa2-258">Dopo aver inserito il EnergyHub, il relativo percorso verrà caricato nel servizio ed è quindi possibile distribuirlo a tutti gli altri dispositivi HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-258">After the EnergyHub has been placed, its location will be uploaded to the service and you can then deploy to all other HoloLens devices.</span></span>
* <span data-ttu-id="c3aa2-259">Quando una nuova HoloLens viene aggiunta per la prima volta alla sessione, il percorso di EnergyHub potrebbe non essere corretto nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-259">When a new HoloLens first joins the session, the location of the EnergyHub may not be correct on that device.</span></span> <span data-ttu-id="c3aa2-260">Tuttavia, non appena i percorsi di ancoraggio e EnergyHub sono stati scaricati dal servizio, EnergyHub dovrebbe passare al nuovo percorso condiviso.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-260">However, as soon as the anchor and EnergyHub locations have been downloaded from the service, the EnergyHub should jump to the new, shared location.</span></span> <span data-ttu-id="c3aa2-261">Se questo non avviene entro ~ 30-60 secondi, passare alla posizione in cui si trovava il HoloLens originale durante l'impostazione dell'ancoraggio per raccogliere più indizi sull'ambiente.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-261">If this does not happen within ~30-60 seconds, walk to where the original HoloLens was when setting the anchor to gather more environment clues.</span></span> <span data-ttu-id="c3aa2-262">Se il percorso non è ancora bloccato, ridistribuirlo nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-262">If the location still does not lock on, redeploy to the device.</span></span>
* <span data-ttu-id="c3aa2-263">Quando i dispositivi sono tutti pronti ed eseguono l'app, cercare il EnergyHub.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-263">When the devices are all ready and running the app, look for the EnergyHub.</span></span> <span data-ttu-id="c3aa2-264">È possibile accordare tutti sulla posizione dell'ologramma e sulla direzione del testo.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-264">Can you all agree on the hologram's location and which direction the text is facing?</span></span>

## <a name="chapter-4---discovery"></a><span data-ttu-id="c3aa2-265">Capitolo 4-individuazione</span><span class="sxs-lookup"><span data-stu-id="c3aa2-265">Chapter 4 - Discovery</span></span>

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

<span data-ttu-id="c3aa2-266">Tutti gli utenti possono ora visualizzare lo stesso ologramma!</span><span class="sxs-lookup"><span data-stu-id="c3aa2-266">Everyone can now see the same hologram!</span></span> <span data-ttu-id="c3aa2-267">A questo punto, vediamo tutti gli altri utenti connessi al nostro mondo olografico condiviso.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-267">Now let's see everyone else connected to our shared holographic world.</span></span> <span data-ttu-id="c3aa2-268">In questo capitolo si otterrà la posizione della testa e la rotazione di tutti gli altri dispositivi HoloLens nella stessa sessione di condivisione.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-268">In this chapter, we'll grab the head location and rotation of all other HoloLens devices in the same sharing session.</span></span>

### <a name="objectives"></a><span data-ttu-id="c3aa2-269">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="c3aa2-269">Objectives</span></span>

* <span data-ttu-id="c3aa2-270">Scopri le altre nell'esperienza condivisa.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-270">Discover each other in our shared experience.</span></span>
* <span data-ttu-id="c3aa2-271">Scegliere e condividere un avatar del lettore.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-271">Choose and share a player avatar.</span></span>
* <span data-ttu-id="c3aa2-272">Alleghi l'avatar del lettore accanto alle intestazioni di tutti.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-272">Attach the player avatar next to everyone's heads.</span></span>

### <a name="instructions"></a><span data-ttu-id="c3aa2-273">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="c3aa2-273">Instructions</span></span>

* <span data-ttu-id="c3aa2-274">Nel **Pannello del progetto** passare alla cartella **ologrammi** .</span><span class="sxs-lookup"><span data-stu-id="c3aa2-274">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="c3aa2-275">Trascinare e rilasciare **PlayerAvatarStore** nella **gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-275">Drag and drop the **PlayerAvatarStore** into the **Hierarchy**.</span></span>
* <span data-ttu-id="c3aa2-276">Nel **pannello progetto** passare alla cartella **script** .</span><span class="sxs-lookup"><span data-stu-id="c3aa2-276">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="c3aa2-277">Fare doppio clic sullo script **AvatarSelector** per aprirlo in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-277">Double-click the **AvatarSelector** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="c3aa2-278">Sostituire il contenuto con il codice seguente.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-278">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Script to handle the user selecting the avatar.
/// </summary>
public class AvatarSelector : MonoBehaviour
{
    /// <summary>
    /// This is the index set by the PlayerAvatarStore for the avatar.
    /// </summary>
    public int AvatarIndex { get; set; }

    /// <summary>
    /// Called when the user is gazing at this avatar and air-taps it.
    /// This sends the user's selection to the rest of the devices in the experience.
    /// </summary>
    void OnSelect()
    {
        PlayerAvatarStore.Instance.DismissAvatarPicker();

        LocalPlayerManager.Instance.SetUserAvatar(AvatarIndex);        
    }

    void Start()
    {
        // Add Billboard component so the avatar always faces the user.
        Billboard billboard = gameObject.GetComponent<Billboard>();
        if (billboard == null)
        {
            billboard = gameObject.AddComponent<Billboard>();
        }

        // Lock rotation along the Y axis.
        billboard.PivotAxis = PivotAxis.Y;
    }
}
```

* <span data-ttu-id="c3aa2-279">Nella **gerarchia** selezionare l'oggetto **ologrammcollection** .</span><span class="sxs-lookup"><span data-stu-id="c3aa2-279">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="c3aa2-280">Nel **controllo** fare clic su **Aggiungi componente**.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-280">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="c3aa2-281">Nella casella di ricerca digitare **local Player Manager**.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-281">In the search box, type **Local Player Manager**.</span></span> <span data-ttu-id="c3aa2-282">Selezionare il risultato della ricerca.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-282">Select the search result.</span></span>
* <span data-ttu-id="c3aa2-283">Nella **gerarchia** selezionare l'oggetto **ologrammcollection** .</span><span class="sxs-lookup"><span data-stu-id="c3aa2-283">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="c3aa2-284">Nel **controllo** fare clic su **Aggiungi componente**.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-284">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="c3aa2-285">Nella casella di ricerca digitare **Remote Player Manager**.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-285">In the search box, type **Remote Player Manager**.</span></span> <span data-ttu-id="c3aa2-286">Selezionare il risultato della ricerca.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-286">Select the search result.</span></span>
* <span data-ttu-id="c3aa2-287">Aprire lo script **HologramPlacement** in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-287">Open the **HologramPlacement** script in Visual Studio.</span></span>
* <span data-ttu-id="c3aa2-288">Sostituire il contenuto con il codice seguente.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-288">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and 
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the model 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* <span data-ttu-id="c3aa2-289">Aprire lo script **AppStateManager** in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-289">Open the **AppStateManager** script in Visual Studio.</span></span>
* <span data-ttu-id="c3aa2-290">Sostituire il contenuto con il codice seguente.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-290">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        WaitingForAnchor,
        WaitingForStageTransform,
        PickingAvatar,
        Ready
    }

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // We start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = null;
                }
                break;
        }
    }
}
```

<span data-ttu-id="c3aa2-291">**Distribuisci e goditi**</span><span class="sxs-lookup"><span data-stu-id="c3aa2-291">**Deploy and Enjoy**</span></span>
* <span data-ttu-id="c3aa2-292">Compilare e distribuire il progetto nei dispositivi HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-292">Build and deploy the project to your HoloLens devices.</span></span>
* <span data-ttu-id="c3aa2-293">Quando si sente un suono di ping, trovare il menu di selezione avatar e selezionare un avatar con il gesto di tocco.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-293">When you hear a pinging sound, find the avatar selection menu and select an avatar with the air-tap gesture.</span></span>
* <span data-ttu-id="c3aa2-294">Se non si stanno esaminando gli ologrammi, la luce puntiforme intorno al cursore diventerà un colore diverso quando il HoloLens comunica con il servizio: inizializzazione (viola scuro), download dell'ancoraggio (verde), importazione/esportazione dei dati della località (giallo), caricamento dell'ancoraggio (blu).</span><span class="sxs-lookup"><span data-stu-id="c3aa2-294">If you're not looking at any holograms, the point light around your cursor will turn a different color when your HoloLens is communicating with the service: initializing (dark purple), downloading the anchor (green), importing/exporting location data (yellow), uploading the anchor (blue).</span></span> <span data-ttu-id="c3aa2-295">Se la luce puntiforme intorno al cursore è il colore predefinito (viola chiaro), si è pronti per interagire con gli altri giocatori della sessione.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-295">If your point light around your cursor is the default color (light purple), then you are ready to interact with other players in your session!</span></span>
* <span data-ttu-id="c3aa2-296">Esaminare gli altri utenti connessi allo spazio. ci sarà un robot olografico che si trova al di sopra della spalla e mima i movimenti della testa.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-296">Look at other people connected to your space - there will be a holographic robot floating above their shoulder and mimicking their head motions!</span></span>

## <a name="chapter-5---placement"></a><span data-ttu-id="c3aa2-297">Capitolo 5-selezione host</span><span class="sxs-lookup"><span data-stu-id="c3aa2-297">Chapter 5 - Placement</span></span>

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

<span data-ttu-id="c3aa2-298">In questo capitolo si farà in modo che l'ancoraggio possa essere inserito in superfici reali.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-298">In this chapter, we'll make the anchor able to be placed on real-world surfaces.</span></span> <span data-ttu-id="c3aa2-299">Verranno usate le coordinate condivise per posizionare l'ancoraggio nel punto intermedio tra tutti gli utenti connessi all'esperienza condivisa.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-299">We'll use shared coordinates to place that anchor in the middle point between everyone connected to the shared experience.</span></span>

### <a name="objectives"></a><span data-ttu-id="c3aa2-300">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="c3aa2-300">Objectives</span></span>

* <span data-ttu-id="c3aa2-301">Posizionare gli ologrammi sulla mappa spaziale in base alla posizione della testa dei giocatori.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-301">Place holograms on the spatial map based on players’ head position.</span></span>

### <a name="instructions"></a><span data-ttu-id="c3aa2-302">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="c3aa2-302">Instructions</span></span>

* <span data-ttu-id="c3aa2-303">Nel **Pannello del progetto** passare alla cartella **ologrammi** .</span><span class="sxs-lookup"><span data-stu-id="c3aa2-303">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="c3aa2-304">Trascinare e rilasciare il prefabbricato **CustomSpatialMapping** nella **gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-304">Drag and drop the **CustomSpatialMapping** prefab onto the **Hierarchy**.</span></span>
* <span data-ttu-id="c3aa2-305">Nel **pannello progetto** passare alla cartella **script** .</span><span class="sxs-lookup"><span data-stu-id="c3aa2-305">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="c3aa2-306">Fare doppio clic sullo script **AppStateManager** per aprirlo in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-306">Double-click the **AppStateManager** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="c3aa2-307">Sostituire il contenuto con il codice seguente.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-307">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        PickingAvatar,
        WaitingForAnchor,
        WaitingForStageTransform,
        Ready
    }

    // The object to call to make a projectile.
    GameObject shootHandler = null;

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // The shootHandler shoots projectiles.
        if (GetComponent<ProjectileLauncher>() != null)
        {
            shootHandler = GetComponent<ProjectileLauncher>().gameObject;
        }

        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // Spatial mapping should be disabled when we start up so as not
        // to distract from the avatar picking.
        SpatialMappingManager.Instance.StopObserver();
        SpatialMappingManager.Instance.gameObject.SetActive(false);

        // On device we start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    public void ResetStage()
    {
        // If we fall back to waiting for anchor, everything needed to 
        // get us into setting the target transform state will be setup.
        if (CurrentAppState != AppState.PickingAvatar)
        {
            CurrentAppState = AppState.WaitingForAnchor;
        }

        // Reset the underworld.
        if (UnderworldBase.Instance)
        {
            UnderworldBase.Instance.ResetUnderworld();
        }
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                // Once the anchor is established we need to run spatial mapping for a 
                // little while to build up some meshes.
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;

                    SpatialMappingManager.Instance.gameObject.SetActive(true);
                    SpatialMappingManager.Instance.DrawVisualMeshes = true;
                    SpatialMappingDeformation.Instance.ResetGlobalRendering();
                    SpatialMappingManager.Instance.StartObserver();
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = shootHandler;
                }
                break;
        }
    }
}
```

* <span data-ttu-id="c3aa2-308">Nel **pannello progetto** passare alla cartella **script** .</span><span class="sxs-lookup"><span data-stu-id="c3aa2-308">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="c3aa2-309">Fare doppio clic sullo script **HologramPlacement** per aprirlo in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-309">Double-click the **HologramPlacement** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="c3aa2-310">Sostituire il contenuto con il codice seguente.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-310">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    /// <summary>
    /// We use a voice command to enable moving the target.
    /// </summary>
    KeywordRecognizer keywordRecognizer;

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;

        // And if the users want to reset the stage transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.ResetStage] = this.OnResetStage;

        // Setup a keyword recognizer to enable resetting the target location.
        List<string> keywords = new List<string>();
        keywords.Add("Reset Target");
        keywordRecognizer = new KeywordRecognizer(keywords.ToArray());
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    /// <summary>
    /// When the keyword recognizer hears a command this will be called.  
    /// In this case we only have one keyword, which will re-enable moving the 
    /// target.
    /// </summary>
    /// <param name="args">information to help route the voice command.</param>
    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        ResetStage();
    }

    /// <summary>
    /// Resets the stage transform, so users can place the target again.
    /// </summary>
    public void ResetStage()
    {
        GotTransform = false;

        // AppStateManager needs to know about this so that
        // the right objects get input routed to them.
        AppStateManager.Instance.ResetStage();

        // Other devices in the experience need to know about this as well.
        CustomMessages.Instance.SendResetStage();

        // And we need to reset the object to its start animation state.
        GetComponent<EnergyHubBase>().ResetAnimation();
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and 
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        Vector3 retval;
        // We need to know how many users are in the experience with good transforms.
        Vector3 cumulatedPosition = Camera.main.transform.position;
        int playerCount = 1;
        foreach (RemotePlayerManager.RemoteHeadInfo remoteHead in RemotePlayerManager.Instance.remoteHeadInfos)
        {
            if (remoteHead.Anchored && remoteHead.Active)
            {
                playerCount++;
                cumulatedPosition += remoteHead.HeadObject.transform.position;
            }
        }

        // If we have more than one player ...
        if (playerCount > 1)
        {
            // Put the transform in between the players.
            retval = cumulatedPosition / playerCount;
            RaycastHit hitInfo;

            // And try to put the transform on a surface below the midpoint of the players.
            if (Physics.Raycast(retval, Vector3.down, out hitInfo, 5, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
        }
        // If we are the only player, have the model act as the 'cursor' ...
        else
        {
            // We prefer to put the model on a real world surface.
            RaycastHit hitInfo;

            if (Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, 30, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
            else
            {
                // But if we don't have a ray that intersects the real world, just put the model 2m in
                // front of the user.
                retval = Camera.main.transform.position + Camera.main.transform.forward * 2;
            }
        }
        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    void OnResetStage(NetworkInMessage msg)
    {
        GotTransform = false;

        GetComponent<EnergyHubBase>().ResetAnimation();
        AppStateManager.Instance.ResetStage();
    }
}
```

<span data-ttu-id="c3aa2-311">**Distribuisci e goditi**</span><span class="sxs-lookup"><span data-stu-id="c3aa2-311">**Deploy and enjoy**</span></span>
* <span data-ttu-id="c3aa2-312">Compilare e distribuire il progetto nei dispositivi HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-312">Build and deploy the project to your HoloLens devices.</span></span>
* <span data-ttu-id="c3aa2-313">Quando l'app è pronta, si trova in un cerchio e si noterà che il EnergyHub viene visualizzato al centro di tutti.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-313">When the app is ready, stand in a circle and notice how the EnergyHub appears in the center of everyone.</span></span>
* <span data-ttu-id="c3aa2-314">Toccare per inserire il EnergyHub.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-314">Tap to place the EnergyHub.</span></span>
* <span data-ttu-id="c3aa2-315">Provare il comando vocale ' Reimposta destinazione ' per selezionare il EnergyHub di backup e collaborare come gruppo per spostare l'ologramma in una nuova posizione.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-315">Try the voice command 'Reset Target' to pick the EnergyHub back up and work together as a group to move the hologram to a new location.</span></span>

## <a name="chapter-6---real-world-physics"></a><span data-ttu-id="c3aa2-316">Capitolo 6-fisica reale</span><span class="sxs-lookup"><span data-stu-id="c3aa2-316">Chapter 6 - Real-World Physics</span></span>

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

<span data-ttu-id="c3aa2-317">In questo capitolo verranno aggiunti gli ologrammi che rimbalzano sulle superfici reali.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-317">In this chapter we'll add holograms that bounce off real-world surfaces.</span></span> <span data-ttu-id="c3aa2-318">Guarda lo spazio con i progetti avviati dall'utente e dai tuoi amici.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-318">Watch your space fill up with projects launched by both you and your friends!</span></span>

### <a name="objectives"></a><span data-ttu-id="c3aa2-319">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="c3aa2-319">Objectives</span></span>

* <span data-ttu-id="c3aa2-320">Avvia i proiettili che rimbalzano sulle superfici reali.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-320">Launch projectiles that bounce off real-world surfaces.</span></span>
* <span data-ttu-id="c3aa2-321">Condividere i proiettili in modo che possano essere visualizzati da altri lettori.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-321">Share the projectiles so other players can see them.</span></span>

### <a name="instructions"></a><span data-ttu-id="c3aa2-322">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="c3aa2-322">Instructions</span></span>

* <span data-ttu-id="c3aa2-323">Nella **gerarchia** selezionare l'oggetto **ologrammcollection** .</span><span class="sxs-lookup"><span data-stu-id="c3aa2-323">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="c3aa2-324">Nel **controllo** fare clic su **Aggiungi componente**.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-324">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="c3aa2-325">Nella casella di ricerca digitare **avvio**del proiettile.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-325">In the search box, type **Projectile Launcher**.</span></span> <span data-ttu-id="c3aa2-326">Selezionare il risultato della ricerca.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-326">Select the search result.</span></span>

<span data-ttu-id="c3aa2-327">**Distribuisci e goditi**</span><span class="sxs-lookup"><span data-stu-id="c3aa2-327">**Deploy and enjoy**</span></span>
* <span data-ttu-id="c3aa2-328">Compilare e distribuire nei dispositivi HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-328">Build and deploy to your HoloLens devices.</span></span>
* <span data-ttu-id="c3aa2-329">Quando l'app è in esecuzione in tutti i dispositivi, è possibile eseguire un rubinetto d'aria per avviare il proiettile su superfici reali.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-329">When the app is running on all devices, perform an air-tap to launch projectile at real world surfaces.</span></span>
* <span data-ttu-id="c3aa2-330">Scopri cosa accade quando il proiettile si scontra con l'avatar di un altro giocatore.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-330">See what happens when your projectile collides with another player's avatar!</span></span>

## <a name="chapter-7---grand-finale"></a><span data-ttu-id="c3aa2-331">Capitolo 7-finale finale</span><span class="sxs-lookup"><span data-stu-id="c3aa2-331">Chapter 7 - Grand Finale</span></span>

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

<span data-ttu-id="c3aa2-332">In questo capitolo viene individuato un portale che può essere individuato solo con la collaborazione.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-332">In this chapter, we'll uncover a portal that can only be discovered with collaboration.</span></span>

### <a name="objectives"></a><span data-ttu-id="c3aa2-333">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="c3aa2-333">Objectives</span></span>

* <span data-ttu-id="c3aa2-334">Collaborare per avviare un numero sufficiente di proiettili nell'ancoraggio per individuare un portale segreto.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-334">Work together to launch enough projectiles at the anchor to uncover a secret portal!</span></span>

### <a name="instructions"></a><span data-ttu-id="c3aa2-335">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="c3aa2-335">Instructions</span></span>

* <span data-ttu-id="c3aa2-336">Nel **Pannello del progetto** passare alla cartella **ologrammi** .</span><span class="sxs-lookup"><span data-stu-id="c3aa2-336">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="c3aa2-337">Trascinare e rilasciare l'  asset di Sottomondo come **figlio di ologrammcollection**.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-337">Drag and drop the **Underworld** asset as a **child of HologramCollection**.</span></span>
* <span data-ttu-id="c3aa2-338">Con **ologrammcollection** selezionato, fare clic sul pulsante **Aggiungi componente** nel **controllo**.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-338">With **HologramCollection** selected, click the **Add Component** button in the **Inspector**.</span></span>
* <span data-ttu-id="c3aa2-339">Nel menu digitare nella casella di ricerca **ExplodeTarget**.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-339">In the menu, type in the search box **ExplodeTarget**.</span></span> <span data-ttu-id="c3aa2-340">Selezionare il risultato della ricerca.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-340">Select the search result.</span></span>
* <span data-ttu-id="c3aa2-341">Con **ologrammcollection** selezionato, dalla **gerarchia** trascinare l'oggetto **EnergyHub** nel campo di **destinazione** nel **controllo**.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-341">With **HologramCollection** selected, from the **Hierarchy** drag the **EnergyHub** object to the **Target** field in the **Inspector**.</span></span>
* <span data-ttu-id="c3aa2-342">Con  l'oggetto ologrammcollection selezionato, **dalla gerarchia** trascinare l'oggetto di Sottomondo nel campo Sottomondo del **controllo**.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-342">With **HologramCollection** selected, from the **Hierarchy** drag the **Underworld** object to the **Underworld** field in the **Inspector**.</span></span>

<span data-ttu-id="c3aa2-343">**Distribuisci e goditi**</span><span class="sxs-lookup"><span data-stu-id="c3aa2-343">**Deploy and enjoy**</span></span>
* <span data-ttu-id="c3aa2-344">Compilare e distribuire nei dispositivi HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-344">Build and deploy to your HoloLens devices.</span></span>
* <span data-ttu-id="c3aa2-345">Quando l'app è stata avviata, collaborare insieme per avviare i proiettili nella EnergyHub.</span><span class="sxs-lookup"><span data-stu-id="c3aa2-345">When the app has launched, collaborate together to launch projectiles at the EnergyHub.</span></span>
* <span data-ttu-id="c3aa2-346">Quando viene visualizzato il Sottomondo, avviare i proiettili nei robot di Sottomondo (raggiungere un robot tre volte per divertirsi).</span><span class="sxs-lookup"><span data-stu-id="c3aa2-346">When the underworld appears, launch projectiles at underworld robots (hit a robot three times for extra fun).</span></span>

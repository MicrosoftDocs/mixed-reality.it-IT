---
title: MR condivisione 240 - più dispositivi HoloLens
description: Seguire questa procedura dettagliata con Unity, Visual Studio e HoloLens che informazioni dettagliate su condivisione vntana di codifica.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit unity, condivisione, rete, academy, esercitazione
ms.openlocfilehash: 70a39a739d360a5032bc8df76b6f0bd57521d9ec
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59601392"
---
>[!NOTE]
><span data-ttu-id="aefe6-104">Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.</span><span class="sxs-lookup"><span data-stu-id="aefe6-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="aefe6-105">Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.</span><span class="sxs-lookup"><span data-stu-id="aefe6-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="aefe6-106">Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.</span><span class="sxs-lookup"><span data-stu-id="aefe6-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="aefe6-107">Essi verranno mantenute per continuare a utilizzare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="aefe6-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="aefe6-108">Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="aefe6-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="aefe6-109">Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.</span><span class="sxs-lookup"><span data-stu-id="aefe6-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-sharing-240-multiple-hololens-devices"></a><span data-ttu-id="aefe6-110">MR Sharing 240: Più dispositivi HoloLens</span><span class="sxs-lookup"><span data-stu-id="aefe6-110">MR Sharing 240: Multiple HoloLens devices</span></span>

<span data-ttu-id="aefe6-111">Ologrammi vengono specificati sulla presenza nel mondo tramite rimanenti posto col passaggio nello spazio.</span><span class="sxs-lookup"><span data-stu-id="aefe6-111">Holograms are given presence in our world by remaining in place as we move about in space.</span></span> <span data-ttu-id="aefe6-112">HoloLens mantiene vntana posto utilizzando vari [sistemi di coordinate](coordinate-systems.md) per tenere traccia della posizione e l'orientamento di oggetti.</span><span class="sxs-lookup"><span data-stu-id="aefe6-112">HoloLens keeps holograms in place by using various [coordinate systems](coordinate-systems.md) to keep track of the location and orientation of objects.</span></span> <span data-ttu-id="aefe6-113">Quando si condividono questi sistemi di coordinate tra i dispositivi, è possibile creare un'esperienza condivisa che consente di partecipare a un mondo holographic condiviso.</span><span class="sxs-lookup"><span data-stu-id="aefe6-113">When we share these coordinate systems between devices, we can create a shared experience that allows us to take part in a shared holographic world.</span></span>

<span data-ttu-id="aefe6-114">In questa esercitazione si apprenderà come:</span><span class="sxs-lookup"><span data-stu-id="aefe6-114">In this tutorial, we will:</span></span>

* <span data-ttu-id="aefe6-115">Configurare una rete per un'esperienza condivisa.</span><span class="sxs-lookup"><span data-stu-id="aefe6-115">Setup a network for a shared experience.</span></span>
* <span data-ttu-id="aefe6-116">Condividere vntana tra dispositivi HoloLens.</span><span class="sxs-lookup"><span data-stu-id="aefe6-116">Share holograms across HoloLens devices.</span></span>
* <span data-ttu-id="aefe6-117">Informazioni su altri utenti nel mondo holographic condiviso.</span><span class="sxs-lookup"><span data-stu-id="aefe6-117">Discover other people in our shared holographic world.</span></span>
* <span data-ttu-id="aefe6-118">È possibile creare un'esperienza interattiva condivisa in cui è possibile gli altri giocatori - di destinazione e avviare i proiettili a tali file.</span><span class="sxs-lookup"><span data-stu-id="aefe6-118">Create a shared interactive experience where you can target other players - and launch projectiles at them!</span></span>

## <a name="device-support"></a><span data-ttu-id="aefe6-119">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="aefe6-119">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="aefe6-120">Corso</span><span class="sxs-lookup"><span data-stu-id="aefe6-120">Course</span></span></th><th style="width:150px"> <span data-ttu-id="aefe6-121"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="aefe6-121"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="aefe6-122"><a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></span><span class="sxs-lookup"><span data-stu-id="aefe6-122"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="aefe6-123">MR Sharing 240: Più dispositivi HoloLens</span><span class="sxs-lookup"><span data-stu-id="aefe6-123">MR Sharing 240: Multiple HoloLens devices</span></span></td><td style="text-align: center;"> <span data-ttu-id="aefe6-124">✔️</span><span class="sxs-lookup"><span data-stu-id="aefe6-124">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="aefe6-125">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="aefe6-125">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="aefe6-126">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="aefe6-126">Prerequisites</span></span>

* <span data-ttu-id="aefe6-127">Un PC Windows 10 configurate con i valori corretti [sono installati gli strumenti](install-the-tools.md) con accesso a Internet.</span><span class="sxs-lookup"><span data-stu-id="aefe6-127">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md) with Internet access.</span></span>
* <span data-ttu-id="aefe6-128">Almeno due dispositivi HoloLens [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="aefe6-128">At least two HoloLens devices [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="aefe6-129">File di progetto</span><span class="sxs-lookup"><span data-stu-id="aefe6-129">Project files</span></span>

* <span data-ttu-id="aefe6-130">Scaricare il [file](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) necessarie per il progetto.</span><span class="sxs-lookup"><span data-stu-id="aefe6-130">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) required by the project.</span></span> <span data-ttu-id="aefe6-131">Richiede Unity 2017.2 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="aefe6-131">Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="aefe6-132">Se è comunque necessario il supporto di Unity 5.6, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).</span><span class="sxs-lookup"><span data-stu-id="aefe6-132">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).</span></span>
  * <span data-ttu-id="aefe6-133">Se è comunque necessario il supporto di Unity 5.5, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).</span><span class="sxs-lookup"><span data-stu-id="aefe6-133">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).</span></span>
  * <span data-ttu-id="aefe6-134">Se è ancora necessario supporto 5.4 di Unity, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).</span><span class="sxs-lookup"><span data-stu-id="aefe6-134">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).</span></span>
* <span data-ttu-id="aefe6-135">Annullare la-archive i file sul desktop o altri facile da raggiungere percorso.</span><span class="sxs-lookup"><span data-stu-id="aefe6-135">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="aefe6-136">Mantenere il nome di cartella **SharedHolograms**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-136">Keep the folder name as **SharedHolograms**.</span></span>

>[!NOTE]
><span data-ttu-id="aefe6-137">Se si desidera esaminare il codice sorgente prima di scaricare, ha [disponibile in GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).</span><span class="sxs-lookup"><span data-stu-id="aefe6-137">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="aefe6-138">Capitolo 1 - Holo World</span><span class="sxs-lookup"><span data-stu-id="aefe6-138">Chapter 1 - Holo World</span></span>

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

<span data-ttu-id="aefe6-139">In questo capitolo verranno configurare il primo progetto Unity e procedere con la compilazione e processo di distribuzione.</span><span class="sxs-lookup"><span data-stu-id="aefe6-139">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="aefe6-140">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="aefe6-140">Objectives</span></span>

* <span data-ttu-id="aefe6-141">Configurare Unity per lo sviluppo di App holographic.</span><span class="sxs-lookup"><span data-stu-id="aefe6-141">Setup Unity to develop holographic apps.</span></span>
* <span data-ttu-id="aefe6-142">Scopri le ologrammi!</span><span class="sxs-lookup"><span data-stu-id="aefe6-142">See your hologram!</span></span>

### <a name="instructions"></a><span data-ttu-id="aefe6-143">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="aefe6-143">Instructions</span></span>

* <span data-ttu-id="aefe6-144">Avviare Unity.</span><span class="sxs-lookup"><span data-stu-id="aefe6-144">Start Unity.</span></span>
* <span data-ttu-id="aefe6-145">Selezionare **aperto**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-145">Select **Open**.</span></span>
* <span data-ttu-id="aefe6-146">Immettere il percorso come il **SharedHolograms** cartella precedentemente non archiviati.</span><span class="sxs-lookup"><span data-stu-id="aefe6-146">Enter location as the **SharedHolograms** folder you previously unarchived.</span></span>
* <span data-ttu-id="aefe6-147">Selezionare **nome progetto** e fare clic su **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-147">Select **Project Name** and click **Select Folder**.</span></span>
* <span data-ttu-id="aefe6-148">Nel **gerarchia**, fare doppio clic il **Main Camera** e selezionare **Elimina**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-148">In the **Hierarchy**, right-click the **Main Camera** and select **Delete**.</span></span>
* <span data-ttu-id="aefe6-149">Nel **HoloToolkit-Sharing-240/Prefabs/fotocamera** cartella trovare il **Main Camera** prefab.</span><span class="sxs-lookup"><span data-stu-id="aefe6-149">In the **HoloToolkit-Sharing-240/Prefabs/Camera** folder, find the **Main Camera** prefab.</span></span>
* <span data-ttu-id="aefe6-150">Trascinare e rilasciare il **Main Camera** nel **gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-150">Drag and drop the **Main Camera** into the **Hierarchy**.</span></span>
* <span data-ttu-id="aefe6-151">Nel **gerarchia**, fare clic su **Create** e **Crea vuoto**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-151">In the **Hierarchy**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="aefe6-152">Fare doppio clic su nuova **GameObject** e selezionare **rinominare**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-152">Right-click the new **GameObject** and select **Rename**.</span></span>
* <span data-ttu-id="aefe6-153">Rinominare gli elementi GameObject al **HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-153">Rename the GameObject to **HologramCollection**.</span></span>
* <span data-ttu-id="aefe6-154">Selezionare il **HologramCollection** dell'oggetto nel **gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-154">Select the **HologramCollection** object in the **Hierarchy**.</span></span>
* <span data-ttu-id="aefe6-155">Nel **Inspector** impostare il **trasformare posizione** per: **X: 0, Y: -0,25, Z: 2**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-155">In the **Inspector** set the **transform position** to: **X: 0, Y: -0.25, Z: 2**.</span></span>
* <span data-ttu-id="aefe6-156">Nel **Vntana** cartella la **pannello progetto**, trovare il **EnergyHub** asset.</span><span class="sxs-lookup"><span data-stu-id="aefe6-156">In the **Holograms** folder in the **Project panel**, find the **EnergyHub** asset.</span></span>
* <span data-ttu-id="aefe6-157">Trascinare e rilasciare il **EnergyHub** dell'oggetto dal **pannello progetto** per il **gerarchia** come un **figlio HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-157">Drag and drop the **EnergyHub** object from the **Project panel** to the **Hierarchy** as a **child of HologramCollection**.</span></span>
* <span data-ttu-id="aefe6-158">Selezionare **File > Salva scena come...**</span><span class="sxs-lookup"><span data-stu-id="aefe6-158">Select **File > Save Scene As...**</span></span>
* <span data-ttu-id="aefe6-159">Denominare la scena **SharedHolograms** e fare clic su **salvare**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-159">Name the scene **SharedHolograms** and click **Save**.</span></span>
* <span data-ttu-id="aefe6-160">Premere il **riprodurre** pulsante in Unity per visualizzare in anteprima il vntana.</span><span class="sxs-lookup"><span data-stu-id="aefe6-160">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="aefe6-161">Premere **riprodurre** una seconda volta per arrestare la modalità di anteprima.</span><span class="sxs-lookup"><span data-stu-id="aefe6-161">Press **Play** a second time to stop preview mode.</span></span>

<span data-ttu-id="aefe6-162">**Esporta il progetto di Unity a Visual Studio**</span><span class="sxs-lookup"><span data-stu-id="aefe6-162">**Export the project from Unity to Visual Studio**</span></span>
* <span data-ttu-id="aefe6-163">Nella finestra Seleziona Unity **File > Build Settings**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-163">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="aefe6-164">Fare clic su **aggiungere scene Open** per aggiungere la scena.</span><span class="sxs-lookup"><span data-stu-id="aefe6-164">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="aefe6-165">Selezionare **Universal Windows Platform** nel **Platform** elenco e fare clic su **commutatore piattaforma**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-165">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="aefe6-166">Impostare **SDK** al **10 universale**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-166">Set **SDK** to **Universal 10**.</span></span>
* <span data-ttu-id="aefe6-167">Impostare **dispositivo di destinazione** al **HoloLens** e **tipo di compilazione UWP** al **D3D**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-167">Set **Target device** to **HoloLens** and **UWP Build Type** to **D3D**.</span></span>
* <span data-ttu-id="aefe6-168">Controllare **Unity C# progetti**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-168">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="aefe6-169">Fai clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-169">Click **Build**.</span></span>
* <span data-ttu-id="aefe6-170">Nella finestra di Esplora file che viene visualizzato, creare un **nuova cartella** denominato "App".</span><span class="sxs-lookup"><span data-stu-id="aefe6-170">In the file explorer window that appears, create a **New Folder** named "App".</span></span>
* <span data-ttu-id="aefe6-171">Solo clic i **App** cartella.</span><span class="sxs-lookup"><span data-stu-id="aefe6-171">Single click the **App** folder.</span></span>
* <span data-ttu-id="aefe6-172">Premere **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-172">Press **Select Folder**.</span></span>
* <span data-ttu-id="aefe6-173">Quando Unity viene eseguita, verrà visualizzata una finestra di Esplora File.</span><span class="sxs-lookup"><span data-stu-id="aefe6-173">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="aefe6-174">Aprire il **App** cartella.</span><span class="sxs-lookup"><span data-stu-id="aefe6-174">Open the **App** folder.</span></span>
* <span data-ttu-id="aefe6-175">Aprire **SharedHolograms.sln** per avviare Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="aefe6-175">Open **SharedHolograms.sln** to launch Visual Studio.</span></span>
* <span data-ttu-id="aefe6-176">Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione di debug per **Release** e da ARM a **X86**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-176">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
* <span data-ttu-id="aefe6-177">Fare clic sulla freccia giù accanto al computer locale e selezionare **dispositivo remoto**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-177">Click on the drop-down arrow next to Local Machine, and select **Remote Device**.</span></span>
    * <span data-ttu-id="aefe6-178">Impostare il **indirizzo** al nome o indirizzo IP di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="aefe6-178">Set the **Address** to the name or IP address of your HoloLens.</span></span> <span data-ttu-id="aefe6-179">Se non si conosce l'indirizzo IP del dispositivo, esaminare **Impostazioni > rete e Internet > Opzioni avanzate** o chiedere a Cortana **"Ehi Cortana, qual è l'indirizzo IP?"**</span><span class="sxs-lookup"><span data-stu-id="aefe6-179">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** or ask Cortana **"Hey Cortana, What's my IP address?"**</span></span>
    * <span data-ttu-id="aefe6-180">Lasciare il **modalità di autenticazione** impostata su **universale**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-180">Leave the **Authentication Mode** set to **Universal**.</span></span>
    * <span data-ttu-id="aefe6-181">Fare clic su **selezionare**</span><span class="sxs-lookup"><span data-stu-id="aefe6-181">Click **Select**</span></span>
* <span data-ttu-id="aefe6-182">Fare clic su **Debug > Avvia senza eseguire debug** o premere **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-182">Click **Debug > Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="aefe6-183">Se questa è la prima volta che la distribuzione nel dispositivo, devi [abbinarlo a Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span><span class="sxs-lookup"><span data-stu-id="aefe6-183">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
* <span data-ttu-id="aefe6-184">Inserire nella finestra di HoloLens e trovare l'ologrammi EnergyHub.</span><span class="sxs-lookup"><span data-stu-id="aefe6-184">Put on your HoloLens and find the EnergyHub hologram.</span></span>

## <a name="chapter-2---interaction"></a><span data-ttu-id="aefe6-185">Capitolo 2: interazione</span><span class="sxs-lookup"><span data-stu-id="aefe6-185">Chapter 2 - Interaction</span></span>

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

<span data-ttu-id="aefe6-186">In questo capitolo, è possibile interagire con i nostri vntana.</span><span class="sxs-lookup"><span data-stu-id="aefe6-186">In this chapter, we'll interact with our holograms.</span></span> <span data-ttu-id="aefe6-187">In primo luogo, si aggiungerà un cursore da visualizzare nostri [estasiati](gaze.md).</span><span class="sxs-lookup"><span data-stu-id="aefe6-187">First, we'll add a cursor to visualize our [Gaze](gaze.md).</span></span> <span data-ttu-id="aefe6-188">Quindi, aggiungiamo [movimenti](gestures.md) e utilizzare la mano per inserire i nostri vntana nello spazio.</span><span class="sxs-lookup"><span data-stu-id="aefe6-188">Then, we'll add [Gestures](gestures.md) and use our hand to place our holograms in space.</span></span>

### <a name="objectives"></a><span data-ttu-id="aefe6-189">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="aefe6-189">Objectives</span></span>

* <span data-ttu-id="aefe6-190">Usare sguardo di input per controllare un cursore.</span><span class="sxs-lookup"><span data-stu-id="aefe6-190">Use gaze input to control a cursor.</span></span>
* <span data-ttu-id="aefe6-191">Usare i movimenti di input per interagire con vntana.</span><span class="sxs-lookup"><span data-stu-id="aefe6-191">Use gesture input to interact with holograms.</span></span>

### <a name="instructions"></a><span data-ttu-id="aefe6-192">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="aefe6-192">Instructions</span></span>

<span data-ttu-id="aefe6-193">**Sguardo**</span><span class="sxs-lookup"><span data-stu-id="aefe6-193">**Gaze**</span></span>
* <span data-ttu-id="aefe6-194">Nel **Pannello di gerarchia** selezionare la **HologramCollection** oggetto.</span><span class="sxs-lookup"><span data-stu-id="aefe6-194">In the **Hierarchy panel** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="aefe6-195">Nel **Pannello di controllo** fare clic sui **Add Component** pulsante.</span><span class="sxs-lookup"><span data-stu-id="aefe6-195">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="aefe6-196">Nel menu, digitare nella casella di ricerca **estasiati Manager**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-196">In the menu, type in the search box **Gaze Manager**.</span></span> <span data-ttu-id="aefe6-197">Selezionare il risultato della ricerca.</span><span class="sxs-lookup"><span data-stu-id="aefe6-197">Select the search result.</span></span>
* <span data-ttu-id="aefe6-198">Nel **240\Prefabs\Input condivisione HoloToolkit** cartella trovare il **cursore** asset.</span><span class="sxs-lookup"><span data-stu-id="aefe6-198">In the **HoloToolkit-Sharing-240\Prefabs\Input** folder, find the **Cursor** asset.</span></span>
* <span data-ttu-id="aefe6-199">Trascinare e rilasciare il **cursore** asset nel **gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-199">Drag and drop the **Cursor** asset onto the **Hierarchy**.</span></span>

<span data-ttu-id="aefe6-200">**Movimento**</span><span class="sxs-lookup"><span data-stu-id="aefe6-200">**Gesture**</span></span>
* <span data-ttu-id="aefe6-201">Nel **Pannello di gerarchia** selezionare la **HologramCollection** oggetto.</span><span class="sxs-lookup"><span data-stu-id="aefe6-201">In the **Hierarchy panel** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="aefe6-202">Fare clic su **Add Component** e digitare **movimento Manager** nel campo di ricerca.</span><span class="sxs-lookup"><span data-stu-id="aefe6-202">Click **Add Component** and type **Gesture Manager** in the search field.</span></span> <span data-ttu-id="aefe6-203">Selezionare il risultato della ricerca.</span><span class="sxs-lookup"><span data-stu-id="aefe6-203">Select the search result.</span></span>
* <span data-ttu-id="aefe6-204">Nel **Pannello di gerarchia**, espandere **HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-204">In the **Hierarchy panel**, expand **HologramCollection**.</span></span>
* <span data-ttu-id="aefe6-205">Selezionare l'elemento figlio **EnergyHub** oggetto.</span><span class="sxs-lookup"><span data-stu-id="aefe6-205">Select the child **EnergyHub** object.</span></span>
* <span data-ttu-id="aefe6-206">Nel **Pannello di controllo** fare clic sui **Add Component** pulsante.</span><span class="sxs-lookup"><span data-stu-id="aefe6-206">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="aefe6-207">Nel menu, digitare nella casella di ricerca **posizionamento ologrammi**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-207">In the menu, type in the search box **Hologram Placement**.</span></span> <span data-ttu-id="aefe6-208">Selezionare il risultato della ricerca.</span><span class="sxs-lookup"><span data-stu-id="aefe6-208">Select the search result.</span></span>
* <span data-ttu-id="aefe6-209">Salvare la scena selezionando **File > Salva scena**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-209">Save the scene by selecting **File > Save Scene**.</span></span>

<span data-ttu-id="aefe6-210">**Distribuire e sfrutta i vantaggi**</span><span class="sxs-lookup"><span data-stu-id="aefe6-210">**Deploy and enjoy**</span></span>
* <span data-ttu-id="aefe6-211">Compilare e distribuire il HoloLens, seguendo le istruzioni riportate nel capitolo precedente.</span><span class="sxs-lookup"><span data-stu-id="aefe6-211">Build and deploy to your HoloLens, using the instructions from the previous chapter.</span></span>
* <span data-ttu-id="aefe6-212">Una volta che l'app viene avviata nella finestra di HoloLens, spostarsi all'interno di head e notare il modo in cui il EnergyHub segue lo sguardo.</span><span class="sxs-lookup"><span data-stu-id="aefe6-212">Once the app launches on your HoloLens, move your head around and notice how the EnergyHub follows your gaze.</span></span>
* <span data-ttu-id="aefe6-213">Si noti come il cursore visualizzato quando estasiati al momento di ologramma e passa a una luce puntiforme quando non gazing in ologramma.</span><span class="sxs-lookup"><span data-stu-id="aefe6-213">Notice how the cursor appears when you gaze upon the hologram, and changes to a point light when not gazing at a hologram.</span></span>
* <span data-ttu-id="aefe6-214">Eseguire un puntato per posizionare l'ologramma.</span><span class="sxs-lookup"><span data-stu-id="aefe6-214">Perform an air-tap to place the hologram.</span></span> <span data-ttu-id="aefe6-215">In questo momento nel progetto, è possibile inserire solo una volta l'ologrammi (ridistribuzione per riprovare).</span><span class="sxs-lookup"><span data-stu-id="aefe6-215">At this time in our project, you can only place the hologram once (redeploy to try again).</span></span>

## <a name="chapter-3---shared-coordinates"></a><span data-ttu-id="aefe6-216">Capitolo 3 - condiviso coordina</span><span class="sxs-lookup"><span data-stu-id="aefe6-216">Chapter 3 - Shared Coordinates</span></span>

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

<span data-ttu-id="aefe6-217">Per visualizzare e interagire con vntana divertente, ma è possibile andare oltre.</span><span class="sxs-lookup"><span data-stu-id="aefe6-217">It's fun to see and interact with holograms, but let's go further.</span></span> <span data-ttu-id="aefe6-218">Verrà configurato il primo condividere esperienze - ologramma tutti possono visualizzare insieme.</span><span class="sxs-lookup"><span data-stu-id="aefe6-218">We'll set up our first shared experience - a hologram everyone can see together.</span></span>

### <a name="objectives"></a><span data-ttu-id="aefe6-219">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="aefe6-219">Objectives</span></span>

* <span data-ttu-id="aefe6-220">Configurare una rete per un'esperienza condivisa.</span><span class="sxs-lookup"><span data-stu-id="aefe6-220">Setup a network for a shared experience.</span></span>
* <span data-ttu-id="aefe6-221">Stabilire un punto di riferimento comuni.</span><span class="sxs-lookup"><span data-stu-id="aefe6-221">Establish a common reference point.</span></span>
* <span data-ttu-id="aefe6-222">Condividi i sistemi di coordinate tra i dispositivi.</span><span class="sxs-lookup"><span data-stu-id="aefe6-222">Share coordinate systems across devices.</span></span>
* <span data-ttu-id="aefe6-223">Tutti visualizzino lo stesso ologrammi!</span><span class="sxs-lookup"><span data-stu-id="aefe6-223">Everyone sees the same hologram!</span></span>

>[!NOTE]
><span data-ttu-id="aefe6-224">Il **InternetClientServer** e **PrivateNetworkClientServer** funzionalità devono essere dichiarate per un'app per la connessione al server di condivisione.</span><span class="sxs-lookup"><span data-stu-id="aefe6-224">The **InternetClientServer** and **PrivateNetworkClientServer** capabilities must be declared for an app to connect to the sharing server.</span></span> <span data-ttu-id="aefe6-225">Questa operazione viene eseguita per è già in 240 Vntana, ma tenere a mente per i propri progetti.</span><span class="sxs-lookup"><span data-stu-id="aefe6-225">This is done for you already in Holograms 240, but keep this in mind for your own projects.</span></span>
>1. <span data-ttu-id="aefe6-226">Nell'Editor di Unity, passare alle impostazioni del giocatore, passare a "Modifica > progetto Impostazioni > Player"</span><span class="sxs-lookup"><span data-stu-id="aefe6-226">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="aefe6-227">Fare clic sulla scheda "Windows Store"</span><span class="sxs-lookup"><span data-stu-id="aefe6-227">Click on the "Windows Store" tab</span></span>
>3. <span data-ttu-id="aefe6-228">Nella sezione "Impostazioni > le funzionalità di pubblicazione", controllare la **InternetClientServer** funzionalità e i **PrivateNetworkClientServer** funzionalità</span><span class="sxs-lookup"><span data-stu-id="aefe6-228">In the "Publishing Settings > Capabilities" section, check the **InternetClientServer** capability and the **PrivateNetworkClientServer** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="aefe6-229">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="aefe6-229">Instructions</span></span>

* <span data-ttu-id="aefe6-230">Nel **pannello progetto** passare alle **240\Prefabs\Sharing condivisione HoloToolkit** cartella.</span><span class="sxs-lookup"><span data-stu-id="aefe6-230">In the **Project panel** navigate to the **HoloToolkit-Sharing-240\Prefabs\Sharing** folder.</span></span>
* <span data-ttu-id="aefe6-231">Trascinare e rilasciare il **Sharing** prefab nel **Pannello di gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-231">Drag and drop the **Sharing** prefab into the **Hierarchy panel**.</span></span>

<span data-ttu-id="aefe6-232">Successivamente è necessario avviare il servizio di condivisione.</span><span class="sxs-lookup"><span data-stu-id="aefe6-232">Next we need to launch the sharing service.</span></span> <span data-ttu-id="aefe6-233">Solo **un PC** esperienza condiviso dovrà eseguire questo passaggio.</span><span class="sxs-lookup"><span data-stu-id="aefe6-233">Only **one PC** in the shared experience needs to do this step.</span></span>
* <span data-ttu-id="aefe6-234">In Unity - nel menu superiore-a - selezionare il **dal menu di 240 condivisione HoloToolkit**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-234">In Unity - in the top-hand menu - select the **HoloToolkit-Sharing-240 menu**.</span></span>
* <span data-ttu-id="aefe6-235">Selezionare il **Avvia servizio di condivisione** elemento nell'elenco a discesa.</span><span class="sxs-lookup"><span data-stu-id="aefe6-235">Select the **Launch Sharing Service** item in the drop-down.</span></span>
* <span data-ttu-id="aefe6-236">Controllare la **Private Network** opzione e fare clic su **consentire l'accesso** quando la richiesta di firewall viene visualizzata.</span><span class="sxs-lookup"><span data-stu-id="aefe6-236">Check the **Private Network** option and click **Allow Access** when the firewall prompt appears.</span></span>
* <span data-ttu-id="aefe6-237">Annotare l'indirizzo IPv4 visualizzato nella finestra della console del servizio di condivisione.</span><span class="sxs-lookup"><span data-stu-id="aefe6-237">Note down the IPv4 address displayed in the Sharing Service console window.</span></span> <span data-ttu-id="aefe6-238">Questo è lo stesso indirizzo IP come il servizio è in esecuzione nel computer.</span><span class="sxs-lookup"><span data-stu-id="aefe6-238">This is the same IP as the machine the service is being run on.</span></span>

<span data-ttu-id="aefe6-239">Seguire le istruzioni **tutti i PC** che verranno aggiunte le esperienze condivise.</span><span class="sxs-lookup"><span data-stu-id="aefe6-239">Follow the rest of the instructions on **all PCs** that will join the shared experience.</span></span>
* <span data-ttu-id="aefe6-240">Nel **gerarchia**, selezionare la **Sharing** oggetto.</span><span class="sxs-lookup"><span data-stu-id="aefe6-240">In the **Hierarchy**, select the **Sharing** object.</span></span>
* <span data-ttu-id="aefe6-241">Nel **Inspector**via la **Sharing fase** componente, modifica il **indirizzo del Server** da 'localhost' per l'indirizzo IPv4 del computer che esegue SharingService.exe.</span><span class="sxs-lookup"><span data-stu-id="aefe6-241">In the **Inspector**, on the **Sharing Stage** component, change the **Server Address** from 'localhost' to the IPv4 address of the machine running SharingService.exe.</span></span>
* <span data-ttu-id="aefe6-242">Nel **gerarchia** selezionare la **HologramCollection** oggetto.</span><span class="sxs-lookup"><span data-stu-id="aefe6-242">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="aefe6-243">Nel **Inspector** fare clic sui **Add Component** pulsante.</span><span class="sxs-lookup"><span data-stu-id="aefe6-243">In the **Inspector** click the **Add Component** button.</span></span>
* <span data-ttu-id="aefe6-244">Nella casella di ricerca, digitare **importazione esportazione ancoraggio Manager**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-244">In the search box, type **Import Export Anchor Manager**.</span></span> <span data-ttu-id="aefe6-245">Selezionare il risultato della ricerca.</span><span class="sxs-lookup"><span data-stu-id="aefe6-245">Select the search result.</span></span>
* <span data-ttu-id="aefe6-246">Nel **pannello progetto** passare alle **script** cartella.</span><span class="sxs-lookup"><span data-stu-id="aefe6-246">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="aefe6-247">Fare doppio clic il **HologramPlacement** script per aprirlo in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="aefe6-247">Double-click the **HologramPlacement** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="aefe6-248">Sostituire il contenuto con il codice seguente.</span><span class="sxs-lookup"><span data-stu-id="aefe6-248">Replace the contents with the code below.</span></span>

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

* <span data-ttu-id="aefe6-249">In Unity, selezionare la **HologramCollection** nel **Pannello di gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-249">Back in Unity, select the **HologramCollection** in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="aefe6-250">Nel **Pannello di controllo** fare clic sui **Add Component** pulsante.</span><span class="sxs-lookup"><span data-stu-id="aefe6-250">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="aefe6-251">Nel menu, digitare nella casella di ricerca **App State Manager**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-251">In the menu, type in the search box **App State Manager**.</span></span> <span data-ttu-id="aefe6-252">Selezionare il risultato della ricerca.</span><span class="sxs-lookup"><span data-stu-id="aefe6-252">Select the search result.</span></span>

<span data-ttu-id="aefe6-253">**Distribuire e sfrutta i vantaggi**</span><span class="sxs-lookup"><span data-stu-id="aefe6-253">**Deploy and enjoy**</span></span>
* <span data-ttu-id="aefe6-254">Compilare il progetto per i dispositivi HoloLens.</span><span class="sxs-lookup"><span data-stu-id="aefe6-254">Build the project for your HoloLens devices.</span></span>
* <span data-ttu-id="aefe6-255">Designare uno HoloLens distribuire per prima.</span><span class="sxs-lookup"><span data-stu-id="aefe6-255">Designate one HoloLens to deploy to first.</span></span> <span data-ttu-id="aefe6-256">Sarà necessario attendere l'ancoraggio da caricare nel servizio prima di poter effettuare la EnergyHub (questa operazione può richiedere circa 30 e 60 secondi).</span><span class="sxs-lookup"><span data-stu-id="aefe6-256">You will need to wait for the Anchor to be uploaded to the service before you can place the EnergyHub (this can take ~30-60 seconds).</span></span> <span data-ttu-id="aefe6-257">Fino al completamento del caricamento, verranno ignorati i movimenti di tocco.</span><span class="sxs-lookup"><span data-stu-id="aefe6-257">Until the upload is done, your tap gestures will be ignored.</span></span>
* <span data-ttu-id="aefe6-258">Dopo aver posizionato il EnergyHub, posizione verrà caricata nel servizio e quindi è possibile distribuire a tutti gli altri dispositivi HoloLens.</span><span class="sxs-lookup"><span data-stu-id="aefe6-258">After the EnergyHub has been placed, its location will be uploaded to the service and you can then deploy to all other HoloLens devices.</span></span>
* <span data-ttu-id="aefe6-259">Quando si aggiunge un nuovo HoloLens prima di tutto la sessione, il percorso del EnergyHub potrebbe non essere corretto in tale dispositivo.</span><span class="sxs-lookup"><span data-stu-id="aefe6-259">When a new HoloLens first joins the session, the location of the EnergyHub may not be correct on that device.</span></span> <span data-ttu-id="aefe6-260">Tuttavia, non appena l'ancoraggio e percorsi EnergyHub sono stati scaricati dal servizio, il EnergyHub deve spostarsi in corrispondenza per la nuova posizione condivisa.</span><span class="sxs-lookup"><span data-stu-id="aefe6-260">However, as soon as the anchor and EnergyHub locations have been downloaded from the service, the EnergyHub should jump to the new, shared location.</span></span> <span data-ttu-id="aefe6-261">Se ciò non avviene entro circa 30 e 60 secondi, illustrato a dove il HoloLens originale era quando si imposta l'ancoraggio per raccogliere ulteriori indizi di ambiente.</span><span class="sxs-lookup"><span data-stu-id="aefe6-261">If this does not happen within ~30-60 seconds, walk to where the original HoloLens was when setting the anchor to gather more environment clues.</span></span> <span data-ttu-id="aefe6-262">Se il percorso non blocca, ridistribuire il dispositivo.</span><span class="sxs-lookup"><span data-stu-id="aefe6-262">If the location still does not lock on, redeploy to the device.</span></span>
* <span data-ttu-id="aefe6-263">Quando i dispositivi sono pronti e che esegue l'app, cercare il EnergyHub.</span><span class="sxs-lookup"><span data-stu-id="aefe6-263">When the devices are all ready and running the app, look for the EnergyHub.</span></span> <span data-ttu-id="aefe6-264">Di tutti concordare la posizione del ologrammi e direzione in cui è rivolta verso il testo?</span><span class="sxs-lookup"><span data-stu-id="aefe6-264">Can you all agree on the hologram's location and which direction the text is facing?</span></span>

## <a name="chapter-4---discovery"></a><span data-ttu-id="aefe6-265">Capitolo 4 - individuazione</span><span class="sxs-lookup"><span data-stu-id="aefe6-265">Chapter 4 - Discovery</span></span>

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

<span data-ttu-id="aefe6-266">Tutti possono visualizzare ora lo stesso ologrammi!</span><span class="sxs-lookup"><span data-stu-id="aefe6-266">Everyone can now see the same hologram!</span></span> <span data-ttu-id="aefe6-267">Ora vediamo come everyone else connesso al nostro mondo holographic condiviso.</span><span class="sxs-lookup"><span data-stu-id="aefe6-267">Now let's see everyone else connected to our shared holographic world.</span></span> <span data-ttu-id="aefe6-268">In questo capitolo, si sarà Ottiene la posizione head e la rotazione di tutti gli altri dispositivi HoloLens nella stessa sessione di condivisione.</span><span class="sxs-lookup"><span data-stu-id="aefe6-268">In this chapter, we'll grab the head location and rotation of all other HoloLens devices in the same sharing session.</span></span>

### <a name="objectives"></a><span data-ttu-id="aefe6-269">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="aefe6-269">Objectives</span></span>

* <span data-ttu-id="aefe6-270">Nella nostra esperienza condiviso individuarsi a vicenda.</span><span class="sxs-lookup"><span data-stu-id="aefe6-270">Discover each other in our shared experience.</span></span>
* <span data-ttu-id="aefe6-271">Scegliere e condividere un avatar Windows Media player.</span><span class="sxs-lookup"><span data-stu-id="aefe6-271">Choose and share a player avatar.</span></span>
* <span data-ttu-id="aefe6-272">Collegare l'avatar player accanto teste di tutti.</span><span class="sxs-lookup"><span data-stu-id="aefe6-272">Attach the player avatar next to everyone's heads.</span></span>

### <a name="instructions"></a><span data-ttu-id="aefe6-273">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="aefe6-273">Instructions</span></span>

* <span data-ttu-id="aefe6-274">Nel **pannello progetto** passare per il **Vntana** cartella.</span><span class="sxs-lookup"><span data-stu-id="aefe6-274">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="aefe6-275">Trascinare e rilasciare il **PlayerAvatarStore** nel **gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-275">Drag and drop the **PlayerAvatarStore** into the **Hierarchy**.</span></span>
* <span data-ttu-id="aefe6-276">Nel **pannello progetto** passare alle **script** cartella.</span><span class="sxs-lookup"><span data-stu-id="aefe6-276">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="aefe6-277">Fare doppio clic il **AvatarSelector** script per aprirlo in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="aefe6-277">Double-click the **AvatarSelector** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="aefe6-278">Sostituire il contenuto con il codice seguente.</span><span class="sxs-lookup"><span data-stu-id="aefe6-278">Replace the contents with the code below.</span></span>

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

* <span data-ttu-id="aefe6-279">Nel **gerarchia** selezionare la **HologramCollection** oggetto.</span><span class="sxs-lookup"><span data-stu-id="aefe6-279">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="aefe6-280">Nel **Inspector** fare clic su **Add Component**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-280">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="aefe6-281">Nella casella di ricerca, digitare **gestione di Windows Media Player locale**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-281">In the search box, type **Local Player Manager**.</span></span> <span data-ttu-id="aefe6-282">Selezionare il risultato della ricerca.</span><span class="sxs-lookup"><span data-stu-id="aefe6-282">Select the search result.</span></span>
* <span data-ttu-id="aefe6-283">Nel **gerarchia** selezionare la **HologramCollection** oggetto.</span><span class="sxs-lookup"><span data-stu-id="aefe6-283">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="aefe6-284">Nel **Inspector** fare clic su **Add Component**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-284">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="aefe6-285">Nella casella di ricerca, digitare **gestione remota Windows Media Player**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-285">In the search box, type **Remote Player Manager**.</span></span> <span data-ttu-id="aefe6-286">Selezionare il risultato della ricerca.</span><span class="sxs-lookup"><span data-stu-id="aefe6-286">Select the search result.</span></span>
* <span data-ttu-id="aefe6-287">Aprire il **HologramPlacement** script in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="aefe6-287">Open the **HologramPlacement** script in Visual Studio.</span></span>
* <span data-ttu-id="aefe6-288">Sostituire il contenuto con il codice seguente.</span><span class="sxs-lookup"><span data-stu-id="aefe6-288">Replace the contents with the code below.</span></span>

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

* <span data-ttu-id="aefe6-289">Aprire il **AppStateManager** script in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="aefe6-289">Open the **AppStateManager** script in Visual Studio.</span></span>
* <span data-ttu-id="aefe6-290">Sostituire il contenuto con il codice seguente.</span><span class="sxs-lookup"><span data-stu-id="aefe6-290">Replace the contents with the code below.</span></span>

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

<span data-ttu-id="aefe6-291">**Distribuire e sfrutta i vantaggi**</span><span class="sxs-lookup"><span data-stu-id="aefe6-291">**Deploy and Enjoy**</span></span>
* <span data-ttu-id="aefe6-292">Compilare e distribuire il progetto per i dispositivi HoloLens.</span><span class="sxs-lookup"><span data-stu-id="aefe6-292">Build and deploy the project to your HoloLens devices.</span></span>
* <span data-ttu-id="aefe6-293">Quando si sente un suono ping, individuare il menu di selezione avatar e selezionare un avatar con il movimento indice puntato.</span><span class="sxs-lookup"><span data-stu-id="aefe6-293">When you hear a pinging sound, find the avatar selection menu and select an avatar with the air-tap gesture.</span></span>
* <span data-ttu-id="aefe6-294">Se si osservano non qualsiasi vntana, il punto luce tutto il cursore attiverà un colore diverso quando comunica con il servizio di HoloLens: l'inizializzazione (viola scuro), scaricando il punto di ancoraggio (verde), l'importazione/esportazione di dati sulla località (giallo), caricare il punto di ancoraggio (blu).</span><span class="sxs-lookup"><span data-stu-id="aefe6-294">If you're not looking at any holograms, the point light around your cursor will turn a different color when your HoloLens is communicating with the service: initializing (dark purple), downloading the anchor (green), importing/exporting location data (yellow), uploading the anchor (blue).</span></span> <span data-ttu-id="aefe6-295">Se il punto luce tutto il cursore è il colore predefinito (viola chiaro), è pronti per interagire con gli altri giocatori nella sessione corrente.</span><span class="sxs-lookup"><span data-stu-id="aefe6-295">If your point light around your cursor is the default color (light purple), then you are ready to interact with other players in your session!</span></span>
* <span data-ttu-id="aefe6-296">Esaminare altre persone connesse nello spazio - saranno presenti un robot holographic mobile sopra la spalla e, che rispecchia i movimenti head!</span><span class="sxs-lookup"><span data-stu-id="aefe6-296">Look at other people connected to your space - there will be a holographic robot floating above their shoulder and mimicking their head motions!</span></span>

## <a name="chapter-5---placement"></a><span data-ttu-id="aefe6-297">Capitolo 5 - selezione host</span><span class="sxs-lookup"><span data-stu-id="aefe6-297">Chapter 5 - Placement</span></span>

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

<span data-ttu-id="aefe6-298">In questo capitolo, ci assicureremo di ancoraggio in grado di essere inseriti nelle aree del mondo reale.</span><span class="sxs-lookup"><span data-stu-id="aefe6-298">In this chapter, we'll make the anchor able to be placed on real-world surfaces.</span></span> <span data-ttu-id="aefe6-299">Useremo le coordinate condivise al posto che definiscono il punto medio tra tutti gli utenti connessi a condividere esperienze.</span><span class="sxs-lookup"><span data-stu-id="aefe6-299">We'll use shared coordinates to place that anchor in the middle point between everyone connected to the shared experience.</span></span>

### <a name="objectives"></a><span data-ttu-id="aefe6-300">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="aefe6-300">Objectives</span></span>

* <span data-ttu-id="aefe6-301">Inserire vntana sulla mappa spaziale in base alla posizione head giocatori.</span><span class="sxs-lookup"><span data-stu-id="aefe6-301">Place holograms on the spatial map based on players’ head position.</span></span>

### <a name="instructions"></a><span data-ttu-id="aefe6-302">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="aefe6-302">Instructions</span></span>

* <span data-ttu-id="aefe6-303">Nel **pannello progetto** passare per il **Vntana** cartella.</span><span class="sxs-lookup"><span data-stu-id="aefe6-303">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="aefe6-304">Trascinare e rilasciare il **CustomSpatialMapping** prefab nel **gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-304">Drag and drop the **CustomSpatialMapping** prefab onto the **Hierarchy**.</span></span>
* <span data-ttu-id="aefe6-305">Nel **pannello progetto** passare alle **script** cartella.</span><span class="sxs-lookup"><span data-stu-id="aefe6-305">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="aefe6-306">Fare doppio clic il **AppStateManager** script per aprirlo in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="aefe6-306">Double-click the **AppStateManager** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="aefe6-307">Sostituire il contenuto con il codice seguente.</span><span class="sxs-lookup"><span data-stu-id="aefe6-307">Replace the contents with the code below.</span></span>

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

* <span data-ttu-id="aefe6-308">Nel **pannello progetto** passare alle **script** cartella.</span><span class="sxs-lookup"><span data-stu-id="aefe6-308">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="aefe6-309">Fare doppio clic il **HologramPlacement** script per aprirlo in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="aefe6-309">Double-click the **HologramPlacement** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="aefe6-310">Sostituire il contenuto con il codice seguente.</span><span class="sxs-lookup"><span data-stu-id="aefe6-310">Replace the contents with the code below.</span></span>

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

<span data-ttu-id="aefe6-311">**Distribuire e sfrutta i vantaggi**</span><span class="sxs-lookup"><span data-stu-id="aefe6-311">**Deploy and enjoy**</span></span>
* <span data-ttu-id="aefe6-312">Compilare e distribuire il progetto per i dispositivi HoloLens.</span><span class="sxs-lookup"><span data-stu-id="aefe6-312">Build and deploy the project to your HoloLens devices.</span></span>
* <span data-ttu-id="aefe6-313">Quando l'app è pronta, in un cerchio in evidenza e notare come il EnergyHub viene visualizzato al centro di tutti gli utenti.</span><span class="sxs-lookup"><span data-stu-id="aefe6-313">When the app is ready, stand in a circle and notice how the EnergyHub appears in the center of everyone.</span></span>
* <span data-ttu-id="aefe6-314">Toccare per posizionare il EnergyHub.</span><span class="sxs-lookup"><span data-stu-id="aefe6-314">Tap to place the EnergyHub.</span></span>
* <span data-ttu-id="aefe6-315">Provare il comando vocale 'Reimposta Target' per prelevare il EnergyHub il backup e lavorare insieme come gruppo per spostare l'ologrammi in una nuova posizione.</span><span class="sxs-lookup"><span data-stu-id="aefe6-315">Try the voice command 'Reset Target' to pick the EnergyHub back up and work together as a group to move the hologram to a new location.</span></span>

## <a name="chapter-6---real-world-physics"></a><span data-ttu-id="aefe6-316">Capitolo 6 - fisica reali</span><span class="sxs-lookup"><span data-stu-id="aefe6-316">Chapter 6 - Real-World Physics</span></span>

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

<span data-ttu-id="aefe6-317">In questo capitolo verrà aggiunto vntana che rimbalzano aree del mondo reale.</span><span class="sxs-lookup"><span data-stu-id="aefe6-317">In this chapter we'll add holograms that bounce off real-world surfaces.</span></span> <span data-ttu-id="aefe6-318">Guarda lo spazio riempito di progetti avviati dall'utente e i tuoi amici.</span><span class="sxs-lookup"><span data-stu-id="aefe6-318">Watch your space fill up with projects launched by both you and your friends!</span></span>

### <a name="objectives"></a><span data-ttu-id="aefe6-319">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="aefe6-319">Objectives</span></span>

* <span data-ttu-id="aefe6-320">Avviare i proiettili che rimbalzano aree del mondo reale.</span><span class="sxs-lookup"><span data-stu-id="aefe6-320">Launch projectiles that bounce off real-world surfaces.</span></span>
* <span data-ttu-id="aefe6-321">Condividere i proiettili in modo che gli altri giocatori possono visualizzarli.</span><span class="sxs-lookup"><span data-stu-id="aefe6-321">Share the projectiles so other players can see them.</span></span>

### <a name="instructions"></a><span data-ttu-id="aefe6-322">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="aefe6-322">Instructions</span></span>

* <span data-ttu-id="aefe6-323">Nel **gerarchia** selezionare la **HologramCollection** oggetto.</span><span class="sxs-lookup"><span data-stu-id="aefe6-323">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="aefe6-324">Nel **Inspector** fare clic su **Add Component**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-324">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="aefe6-325">Nella casella di ricerca, digitare **utilità di avvio proiettile**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-325">In the search box, type **Projectile Launcher**.</span></span> <span data-ttu-id="aefe6-326">Selezionare il risultato della ricerca.</span><span class="sxs-lookup"><span data-stu-id="aefe6-326">Select the search result.</span></span>

<span data-ttu-id="aefe6-327">**Distribuire e sfrutta i vantaggi**</span><span class="sxs-lookup"><span data-stu-id="aefe6-327">**Deploy and enjoy**</span></span>
* <span data-ttu-id="aefe6-328">Compilare e distribuire ai dispositivi HoloLens.</span><span class="sxs-lookup"><span data-stu-id="aefe6-328">Build and deploy to your HoloLens devices.</span></span>
* <span data-ttu-id="aefe6-329">Quando l'app è in esecuzione in tutti i dispositivi, eseguire un puntato per avviare proiettile in superfici reali.</span><span class="sxs-lookup"><span data-stu-id="aefe6-329">When the app is running on all devices, perform an air-tap to launch projectile at real world surfaces.</span></span>
* <span data-ttu-id="aefe6-330">Che cosa accade quando il proiettile è in conflitto con avatar del giocatore.</span><span class="sxs-lookup"><span data-stu-id="aefe6-330">See what happens when your projectile collides with another player's avatar!</span></span>

## <a name="chapter-7---grand-finale"></a><span data-ttu-id="aefe6-331">Capitolo 7 - gran</span><span class="sxs-lookup"><span data-stu-id="aefe6-331">Chapter 7 - Grand Finale</span></span>

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

<span data-ttu-id="aefe6-332">In questo capitolo, si sarà scoprire un portale che può essere individuato solamente con la collaborazione.</span><span class="sxs-lookup"><span data-stu-id="aefe6-332">In this chapter, we'll uncover a portal that can only be discovered with collaboration.</span></span>

### <a name="objectives"></a><span data-ttu-id="aefe6-333">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="aefe6-333">Objectives</span></span>

* <span data-ttu-id="aefe6-334">Collaborano per avviare sufficiente i proiettili nel punto di ancoraggio per individuare un portale del segreto.</span><span class="sxs-lookup"><span data-stu-id="aefe6-334">Work together to launch enough projectiles at the anchor to uncover a secret portal!</span></span>

### <a name="instructions"></a><span data-ttu-id="aefe6-335">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="aefe6-335">Instructions</span></span>

* <span data-ttu-id="aefe6-336">Nel **pannello progetto** passare per il **Vntana** cartella.</span><span class="sxs-lookup"><span data-stu-id="aefe6-336">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="aefe6-337">Trascinare e rilasciare il **Underworld** asset come una **figlio HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-337">Drag and drop the **Underworld** asset as a **child of HologramCollection**.</span></span>
* <span data-ttu-id="aefe6-338">Con **HologramCollection** selezionata, fare clic il **Add Component** pulsante il **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-338">With **HologramCollection** selected, click the **Add Component** button in the **Inspector**.</span></span>
* <span data-ttu-id="aefe6-339">Nel menu, digitare nella casella di ricerca **ExplodeTarget**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-339">In the menu, type in the search box **ExplodeTarget**.</span></span> <span data-ttu-id="aefe6-340">Selezionare il risultato della ricerca.</span><span class="sxs-lookup"><span data-stu-id="aefe6-340">Select the search result.</span></span>
* <span data-ttu-id="aefe6-341">Con **HologramCollection** selezionato, dalle **gerarchia** trascinare il **EnergyHub** dell'oggetto per il **destinazione** campo il **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-341">With **HologramCollection** selected, from the **Hierarchy** drag the **EnergyHub** object to the **Target** field in the **Inspector**.</span></span>
* <span data-ttu-id="aefe6-342">Con **HologramCollection** selezionato, dalle **gerarchia** trascinare il **Underworld** dell'oggetto per il **Underworld** campo il  **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="aefe6-342">With **HologramCollection** selected, from the **Hierarchy** drag the **Underworld** object to the **Underworld** field in the **Inspector**.</span></span>

<span data-ttu-id="aefe6-343">**Distribuire e sfrutta i vantaggi**</span><span class="sxs-lookup"><span data-stu-id="aefe6-343">**Deploy and enjoy**</span></span>
* <span data-ttu-id="aefe6-344">Compilare e distribuire ai dispositivi HoloLens.</span><span class="sxs-lookup"><span data-stu-id="aefe6-344">Build and deploy to your HoloLens devices.</span></span>
* <span data-ttu-id="aefe6-345">Quando l'app è stata avviata, collaborare per avviare i proiettili nel EnergyHub.</span><span class="sxs-lookup"><span data-stu-id="aefe6-345">When the app has launched, collaborate together to launch projectiles at the EnergyHub.</span></span>
* <span data-ttu-id="aefe6-346">Quando viene visualizzata la underworld, avviare i proiettili a controllare i robot underworld (riscontri un robot tre volte per divertimento extra).</span><span class="sxs-lookup"><span data-stu-id="aefe6-346">When the underworld appears, launch projectiles at underworld robots (hit a robot three times for extra fun).</span></span>

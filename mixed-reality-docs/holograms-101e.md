---
title: Nozioni fondamentali MR 101E - progetto completo con emulatore
description: Seguire questa procedura dettagliata con Unity, Visual Studio e HoloLens emulatore che informazioni di base di un'applicazione holographic di codifica.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: realtà mista, realtà mista di Windows, HoloLens, ologrammi, emulatore tutorial, academy,
ms.openlocfilehash: 77f7d497396937bf471a69fa514cef84ab0b699d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599403"
---
>[!NOTE]
><span data-ttu-id="a3d9f-104">Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="a3d9f-105">Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="a3d9f-106">Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="a3d9f-107">Essi verranno mantenute per continuare a utilizzare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="a3d9f-108">Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="a3d9f-109">Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-basics-101e-complete-project-with-emulator"></a><span data-ttu-id="a3d9f-110">Nozioni fondamentali di MR 101E: Progetto completo con emulatore</span><span class="sxs-lookup"><span data-stu-id="a3d9f-110">MR Basics 101E: Complete project with emulator</span></span>

 >[!VIDEO https://www.youtube.com/embed/Xzm8_s05mm8]

<span data-ttu-id="a3d9f-111">Questa esercitazione illustrerà un progetto completo, compilato in Unity, che illustra le funzionalità di realtà mista di Windows di core per HoloLens, incluse [estasiati](gaze.md), [movimenti](gestures.md), [inputvocale](voice-input.md), [spaziale audio](spatial-sound.md) e [mapping spaziale](spatial-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="a3d9f-111">This tutorial will walk you through a complete project, built in Unity, that demonstrates core Windows Mixed Reality features on HoloLens including [gaze](gaze.md), [gestures](gestures.md), [voice input](voice-input.md), [spatial sound](spatial-sound.md) and [spatial mapping](spatial-mapping.md).</span></span> <span data-ttu-id="a3d9f-112">L'esercitazione saranno necessari circa 1 ora.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-112">The tutorial will take approximately 1 hour to complete.</span></span>

## <a name="device-support"></a><span data-ttu-id="a3d9f-113">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="a3d9f-113">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="a3d9f-114">Corso</span><span class="sxs-lookup"><span data-stu-id="a3d9f-114">Course</span></span></th><th style="width:150px"> <span data-ttu-id="a3d9f-115"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="a3d9f-115"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="a3d9f-116"><a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></span><span class="sxs-lookup"><span data-stu-id="a3d9f-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="a3d9f-117">Nozioni fondamentali di MR 101E: Progetto completo con emulatore</span><span class="sxs-lookup"><span data-stu-id="a3d9f-117">MR Basics 101E: Complete project with emulator</span></span></td><td style="text-align: center;"> <span data-ttu-id="a3d9f-118">✔️</span><span class="sxs-lookup"><span data-stu-id="a3d9f-118">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="a3d9f-119">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="a3d9f-119">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="a3d9f-120">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="a3d9f-120">Prerequisites</span></span>

* <span data-ttu-id="a3d9f-121">Un PC Windows 10 configurate con i valori corretti [sono installati gli strumenti](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="a3d9f-121">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>

### <a name="project-files"></a><span data-ttu-id="a3d9f-122">File di progetto</span><span class="sxs-lookup"><span data-stu-id="a3d9f-122">Project files</span></span>

* <span data-ttu-id="a3d9f-123">Scaricare il [file](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) necessarie per il progetto.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-123">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) required by the project.</span></span><span data-ttu-id="a3d9f-124"> Richiede Unity 2017.2 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-124"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="a3d9f-125">Se è comunque necessario il supporto di Unity 5.6, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span><span class="sxs-lookup"><span data-stu-id="a3d9f-125">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span></span>
  * <span data-ttu-id="a3d9f-126">Se è comunque necessario il supporto di Unity 5.5, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span><span class="sxs-lookup"><span data-stu-id="a3d9f-126">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span></span>
  * <span data-ttu-id="a3d9f-127">Se è ancora necessario supporto 5.4 di Unity, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span><span class="sxs-lookup"><span data-stu-id="a3d9f-127">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span></span>
* <span data-ttu-id="a3d9f-128">Annullare la-archive i file sul desktop o altri facile da raggiungere percorso.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-128">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="a3d9f-129">Mantenere il nome di cartella **Origami**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-129">Keep the folder name as **Origami**.</span></span>

>[!NOTE]
><span data-ttu-id="a3d9f-130">Se si desidera esaminare il codice sorgente prima di scaricare, ha [disponibile in GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span><span class="sxs-lookup"><span data-stu-id="a3d9f-130">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="a3d9f-131">Capitolo 1 - world "Holo"</span><span class="sxs-lookup"><span data-stu-id="a3d9f-131">Chapter 1 - "Holo" world</span></span>

>[!VIDEO https://www.youtube.com/embed/qotpUpIQxVU]

<span data-ttu-id="a3d9f-132">In questo capitolo verranno configurare il primo progetto Unity e procedere con la compilazione e processo di distribuzione.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-132">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="a3d9f-133">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="a3d9f-133">Objectives</span></span>

* <span data-ttu-id="a3d9f-134">Configurare Unity per lo sviluppo holographic.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-134">Set up Unity for holographic development.</span></span>
* <span data-ttu-id="a3d9f-135">Rendere ologramma.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-135">Make a hologram.</span></span>
* <span data-ttu-id="a3d9f-136">Vedere ologramma apportate.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-136">See a hologram that you made.</span></span>

### <a name="instructions"></a><span data-ttu-id="a3d9f-137">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="a3d9f-137">Instructions</span></span>

* <span data-ttu-id="a3d9f-138">Avviare Unity.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-138">Start Unity.</span></span>
* <span data-ttu-id="a3d9f-139">Selezionare **aperto**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-139">Select **Open**.</span></span>
* <span data-ttu-id="a3d9f-140">Immettere il percorso come il **Origami** cartella è archiviato in precedenza di annullamento.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-140">Enter location as the **Origami** folder you previously un-archived.</span></span>
* <span data-ttu-id="a3d9f-141">Selezionare **Origami** e fare clic su **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-141">Select **Origami** and click **Select Folder**.</span></span>
* <span data-ttu-id="a3d9f-142">Salvare la nuova scena: **File** / **Salva scena come**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-142">Save the new scene: **File** / **Save Scene As**.</span></span>
* <span data-ttu-id="a3d9f-143">Denominare la scena **Origami** e premere il **salvare** pulsante.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-143">Name the scene **Origami** and press the **Save** button.</span></span>

#### <a name="setup-the-main-camera"></a><span data-ttu-id="a3d9f-144">Programma di installazione la fotocamera principale</span><span class="sxs-lookup"><span data-stu-id="a3d9f-144">Setup the main camera</span></span>

* <span data-ttu-id="a3d9f-145">Nel **Pannello di gerarchia**, selezionare **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-145">In the **Hierarchy Panel**, select **Main Camera**.</span></span>
* <span data-ttu-id="a3d9f-146">Nel **Inspector** impostare la posizione di trasformazione **0, 0,0**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-146">In the **Inspector** set its transform position to **0,0,0**.</span></span>
* <span data-ttu-id="a3d9f-147">Trovare il **Cancella flag** proprietà e modificare l'elenco a discesa dal **Skybox** al **colore a tinta unita**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-147">Find the **Clear Flags** property, and change the dropdown from **Skybox** to **Solid color**.</span></span>
* <span data-ttu-id="a3d9f-148">Fare clic sui **sfondo** campo per aprire una selezione colori.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-148">Click on the **Background** field to open a color picker.</span></span>
* <span data-ttu-id="a3d9f-149">Impostare **R, G, B e A** al **0**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-149">Set **R, G, B, and A** to **0**.</span></span>

#### <a name="setup-the-scene"></a><span data-ttu-id="a3d9f-150">Programma di installazione della scena</span><span class="sxs-lookup"><span data-stu-id="a3d9f-150">Setup the scene</span></span>

* <span data-ttu-id="a3d9f-151">Nel **Pannello di gerarchia**, fare clic su **Create** e **Crea vuoto**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-151">In the **Hierarchy Panel**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="a3d9f-152">Fare doppio clic su nuova **GameObject** e scegliere Rinomina.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-152">Right-click the new **GameObject** and select Rename.</span></span> <span data-ttu-id="a3d9f-153">Rinominare gli elementi GameObject al **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-153">Rename the GameObject to **OrigamiCollection**.</span></span>
* <span data-ttu-id="a3d9f-154">Dal **Vntana** cartella le **pannello progetto**:</span><span class="sxs-lookup"><span data-stu-id="a3d9f-154">From the **Holograms** folder in the **Project Panel**:</span></span>
  * <span data-ttu-id="a3d9f-155">Trascinare **Stage** nella gerarchia di un elemento figlio di **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-155">Drag **Stage** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="a3d9f-156">Trascinare **Sphere1** nella gerarchia di un elemento figlio di **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-156">Drag **Sphere1** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="a3d9f-157">Trascinare **Sphere2** nella gerarchia di un elemento figlio di **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-157">Drag **Sphere2** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="a3d9f-158">Fare doppio clic sul **luce direzionale** dell'oggetto nel **Pannello di gerarchia** e selezionare **Elimina**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-158">Right-click the **Directional Light** object in the **Hierarchy Panel** and select **Delete**.</span></span>
* <span data-ttu-id="a3d9f-159">Dal **Vntana** cartella, trascinare **luci** nella radice del **gerarchia pannello**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-159">From the **Holograms** folder, drag **Lights** into the root of the **Hierarchy Panel**.</span></span>
* <span data-ttu-id="a3d9f-160">Nel **gerarchia**, selezionare la **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-160">In the **Hierarchy**, select the **OrigamiCollection**.</span></span>
* <span data-ttu-id="a3d9f-161">Nel **Inspector**, impostare la posizione di trasformazione **0, -0,5, 2.0**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-161">In the **Inspector**, set the transform position to **0, -0.5, 2.0**.</span></span>
* <span data-ttu-id="a3d9f-162">Premere il **riprodurre** pulsante in Unity per visualizzare in anteprima il vntana.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-162">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="a3d9f-163">Si dovrebbero vedere gli oggetti di Origami nella finestra di anteprima.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-163">You should see the Origami objects in the preview window.</span></span>
* <span data-ttu-id="a3d9f-164">Premere **riprodurre** una seconda volta per arrestare la modalità di anteprima.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-164">Press **Play** a second time to stop preview mode.</span></span>

#### <a name="export-the-project-from-unity-to-visual-studio"></a><span data-ttu-id="a3d9f-165">Esporta il progetto di Unity a Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a3d9f-165">Export the project from Unity to Visual Studio</span></span>

* <span data-ttu-id="a3d9f-166">Nella finestra Seleziona Unity **File > Build Settings**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-166">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="a3d9f-167">Selezionare **Windows Store** nel **Platform** elenco e fare clic su **commutatore piattaforma**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-167">Select **Windows Store** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="a3d9f-168">Impostare **SDK** al **10 Universal** e **tipo di compilazione** al **D3D**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-168">Set **SDK** to **Universal 10** and **Build Type** to **D3D**.</span></span>
* <span data-ttu-id="a3d9f-169">Controllare **Unity C# progetti**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-169">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="a3d9f-170">Fare clic su **aggiungere scene Open** per aggiungere la scena.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-170">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="a3d9f-171">Fare clic su **le impostazioni del giocatore...** .</span><span class="sxs-lookup"><span data-stu-id="a3d9f-171">Click **Player Settings...**.</span></span>
* <span data-ttu-id="a3d9f-172">Selezionare il pannello di controllo di **logo di Windows Store**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-172">In the Inspector Panel select the **Windows Store logo**.</span></span> <span data-ttu-id="a3d9f-173">Quindi selezionare **impostazioni di pubblicazione**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-173">Then select **Publishing Settings**.</span></span>
* <span data-ttu-id="a3d9f-174">Nel **capacità** selezionare la **microfono** e **SpatialPerception** funzionalità.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-174">In the **Capabilities** section, select the **Microphone** and **SpatialPerception** capabilities.</span></span>
* <span data-ttu-id="a3d9f-175">Torna nella finestra di impostazioni di compilazione, fare clic su **compilazione**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-175">Back in the Build Settings window, click **Build**.</span></span>
* <span data-ttu-id="a3d9f-176">Creare un **nuova cartella** denominato "App".</span><span class="sxs-lookup"><span data-stu-id="a3d9f-176">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="a3d9f-177">Solo clic i **cartella App**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-177">Single click the **App Folder**.</span></span>
* <span data-ttu-id="a3d9f-178">Premere **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-178">Press **Select Folder**.</span></span>
* <span data-ttu-id="a3d9f-179">Quando Unity viene eseguita, verrà visualizzata una finestra di Esplora File.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-179">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="a3d9f-180">Aprire il **App** cartella.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-180">Open the **App** folder.</span></span>
* <span data-ttu-id="a3d9f-181">Aprire il **soluzione di Visual Studio di Origami**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-181">Open the **Origami Visual Studio Solution**.</span></span>
* <span data-ttu-id="a3d9f-182">Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione di debug per **Release** e da ARM a **X86**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-182">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
  * <span data-ttu-id="a3d9f-183">Fare clic sulla freccia accanto al pulsante di dispositivo e selezionare **HoloLens emulatore**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-183">Click on the arrow next to the Device button, and select **HoloLens Emulator**.</span></span>
  * <span data-ttu-id="a3d9f-184">Fare clic su **Debug -> Avvia senza eseguire debug** o premere **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-184">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
  * <span data-ttu-id="a3d9f-185">Dopo alcuni minuti l'emulatore verrà avviato con il progetto di Origami.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-185">After some time the emulator will start with the Origami project.</span></span> <span data-ttu-id="a3d9f-186">Quando si avvia innanzitutto le [emulatore](using-the-hololens-emulator.md), può richiedere fino a 15 minuti per l'emulatore per l'avvio.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-186">When first launching the [emulator](using-the-hololens-emulator.md), it can take as long as 15 minutes for the emulator to start up.</span></span> <span data-ttu-id="a3d9f-187">Dopo l'avvio, non chiudere.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-187">Once it starts, do not close it.</span></span>

## <a name="chapter-2---gaze"></a><span data-ttu-id="a3d9f-188">Capitolo 2 - sguardo</span><span class="sxs-lookup"><span data-stu-id="a3d9f-188">Chapter 2 - Gaze</span></span>

>[!VIDEO https://www.youtube.com/embed/BPWTbAC210k]

<span data-ttu-id="a3d9f-189">In questo capitolo verrà per introdurre il primo di tre modi di interagire con i vntana: [estasiati](gaze.md).</span><span class="sxs-lookup"><span data-stu-id="a3d9f-189">In this chapter, we are going to introduce the first of three ways of interacting with your holograms -- [gaze](gaze.md).</span></span>

### <a name="objectives"></a><span data-ttu-id="a3d9f-190">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="a3d9f-190">Objectives</span></span>

* <span data-ttu-id="a3d9f-191">Visualizzare lo sguardo utilizzando un cursore bloccato al mondo.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-191">Visualize your gaze using a world-locked cursor.</span></span>

### <a name="instructions"></a><span data-ttu-id="a3d9f-192">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="a3d9f-192">Instructions</span></span>

* <span data-ttu-id="a3d9f-193">Tornare al progetto Unity e chiudere la finestra Impostazioni di compilazione se è ancora aperto.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-193">Go back to your Unity project, and close the Build Settings window if it's still open.</span></span>
* <span data-ttu-id="a3d9f-194">Selezionare il **Vntana** cartella le **pannello progetto**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-194">Select the **Holograms** folder in the **Project panel**.</span></span>
* <span data-ttu-id="a3d9f-195">Trascinare il **cursore** all'oggetto il **Pannello di gerarchia** a livello di radice.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-195">Drag the **Cursor** object into the **Hierarchy panel** at the root level.</span></span>
* <span data-ttu-id="a3d9f-196">Fare doppio clic sulla **cursore** oggetto da ottenere un quadro più da vicino.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-196">Double-click on the **Cursor** object to take a closer look at it.</span></span>
* <span data-ttu-id="a3d9f-197">Fare clic sui **script** cartella nel Pannello di progetto.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-197">Right-click on the **Scripts** folder in the Project panel.</span></span>
* <span data-ttu-id="a3d9f-198">Scegliere il **Create** sottomenu.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-198">Click the **Create** sub-menu.</span></span>
* <span data-ttu-id="a3d9f-199">Selezionare  **C# Script**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-199">Select **C# Script**.</span></span>
* <span data-ttu-id="a3d9f-200">Denominare lo script **WorldCursor**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-200">Name the script **WorldCursor**.</span></span> <span data-ttu-id="a3d9f-201">Nota: Per il nome viene fatta distinzione tra maiuscole e minuscole.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-201">Note: The name is case-sensitive.</span></span> <span data-ttu-id="a3d9f-202">Non devi aggiungere l'estensione. cs.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-202">You do not need to add the .cs extension.</span></span>
* <span data-ttu-id="a3d9f-203">Selezionare il **cursore** dell'oggetto nel **Pannello di gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-203">Select the **Cursor** object in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="a3d9f-204">Trascinare e rilasciare il **WorldCursor** basano gli script delle **Pannello di controllo**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-204">Drag and drop the **WorldCursor** script into the **Inspector panel**.</span></span>
* <span data-ttu-id="a3d9f-205">Fare doppio clic il **WorldCursor** script per aprirlo in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-205">Double-click the **WorldCursor** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="a3d9f-206">Copiare e incollare questo codice nel **WorldCursor.cs** e **Salva tutto**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-206">Copy and paste this code into **WorldCursor.cs** and **Save All**.</span></span>

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

* <span data-ttu-id="a3d9f-207">Ricompilare l'app dalla **File > Impostazioni di compilazione**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-207">Rebuild the app from **File > Build Settings**.</span></span>
* <span data-ttu-id="a3d9f-208">Tornare alla soluzione di Visual Studio usata in precedenza per distribuire l'emulatore.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-208">Return to the Visual Studio solution previously used to deploy to the emulator.</span></span>
* <span data-ttu-id="a3d9f-209">Selezionare "Ricarica tutto" quando richiesto.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-209">Select 'Reload All' when prompted.</span></span>
* <span data-ttu-id="a3d9f-210">Fare clic su **Debug -> Avvia senza eseguire debug** o premere **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-210">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="a3d9f-211">Usare il controller Xbox per cercare la scena.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-211">Use the Xbox controller to look around the scene.</span></span> <span data-ttu-id="a3d9f-212">Si noti come il cursore interagisce con la forma degli oggetti.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-212">Notice how the cursor interacts with the shape of objects.</span></span>

## <a name="chapter-3---gestures"></a><span data-ttu-id="a3d9f-213">Capitolo 3 - movimenti</span><span class="sxs-lookup"><span data-stu-id="a3d9f-213">Chapter 3 - Gestures</span></span>

>[!VIDEO https://www.youtube.com/embed/6d-0RHeKHq4]

<span data-ttu-id="a3d9f-214">In questo capitolo verrà aggiunto il supporto per [movimenti](gestures.md).</span><span class="sxs-lookup"><span data-stu-id="a3d9f-214">In this chapter, we'll add support for [gestures](gestures.md).</span></span> <span data-ttu-id="a3d9f-215">Quando l'utente seleziona una sfera paper, ci assicureremo sfera rientrano attivando la gravità usando il motore di fisica di Unity.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-215">When the user selects a paper sphere, we'll make the sphere fall by turning on gravity using Unity's physics engine.</span></span>

### <a name="objectives"></a><span data-ttu-id="a3d9f-216">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="a3d9f-216">Objectives</span></span>

* <span data-ttu-id="a3d9f-217">Controllare il vntana con il movimento di Select.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-217">Control your holograms with the Select gesture.</span></span>

### <a name="instructions"></a><span data-ttu-id="a3d9f-218">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="a3d9f-218">Instructions</span></span>

<span data-ttu-id="a3d9f-219">Si inizierà creando uno script più in grado di rilevare il movimento di Select.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-219">We'll start by creating a script than can detect the Select gesture.</span></span>

* <span data-ttu-id="a3d9f-220">Nel **gli script** cartella, creare uno script denominato **GazeGestureManager**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-220">In the **Scripts** folder, create a script named **GazeGestureManager**.</span></span>
* <span data-ttu-id="a3d9f-221">Trascinare il **GazeGestureManager** lo script nel **OrigamiCollection** oggetto nella gerarchia.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-221">Drag the **GazeGestureManager** script onto the **OrigamiCollection** object in the Hierarchy.</span></span>
* <span data-ttu-id="a3d9f-222">Aprire il **GazeGestureManager** genera script in Visual Studio e aggiungere il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="a3d9f-222">Open the **GazeGestureManager** script in Visual Studio and add the following code:</span></span>

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

* <span data-ttu-id="a3d9f-223">Creare un altro script nella cartella Scripts, questa volta denominata **SphereCommands**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-223">Create another script in the Scripts folder, this time named **SphereCommands**.</span></span>
* <span data-ttu-id="a3d9f-224">Espandere la **OrigamiCollection** oggetto nella visualizzazione gerarchica.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-224">Expand the **OrigamiCollection** object in the Hierarchy view.</span></span>
* <span data-ttu-id="a3d9f-225">Trascinare il **SphereCommands** nello script le **Sphere1** oggetto nel Pannello di gerarchia.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-225">Drag the **SphereCommands** script onto the **Sphere1** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="a3d9f-226">Trascinare il **SphereCommands** nello script le **Sphere2** oggetto nel Pannello di gerarchia.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-226">Drag the **SphereCommands** script onto the **Sphere2** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="a3d9f-227">Aprire lo script in Visual Studio per la modifica e sostituire il codice predefinito con questo:</span><span class="sxs-lookup"><span data-stu-id="a3d9f-227">Open the script in Visual Studio for editing, and replace the default code with this:</span></span>

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

* <span data-ttu-id="a3d9f-228">Esportare, compilare e distribuire l'app nell'emulatore di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-228">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="a3d9f-229">Guardatevi intorno scena e allineare al centro su uno dei settori.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-229">Look around the scene, and center on one of the spheres.</span></span>
* <span data-ttu-id="a3d9f-230">Premere il **oggetto** sul controller Xbox oppure premere la barra spaziatrice per simulare il movimento di Select.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-230">Press the **A** button on the Xbox controller or press the Spacebar to simulate the Select gesture.</span></span>

## <a name="chapter-4---voice"></a><span data-ttu-id="a3d9f-231">Capitolo 4 - voce</span><span class="sxs-lookup"><span data-stu-id="a3d9f-231">Chapter 4 - Voice</span></span>

>[!VIDEO https://www.youtube.com/embed/LxbOhnd2_GM]

<span data-ttu-id="a3d9f-232">In questo capitolo verrà aggiunto il supporto per due [comandi vocali](voice-input.md): Vengono restituiti "Reimposta world" a sfere eliminati nel percorso originale e "Drop sphere" per rendere la sfera di fallback.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-232">In this chapter, we'll add support for two [voice commands](voice-input.md): "Reset world" to returns the dropped spheres to their original location, and "Drop sphere" to make the sphere fall.</span></span>

### <a name="objectives"></a><span data-ttu-id="a3d9f-233">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="a3d9f-233">Objectives</span></span>

* <span data-ttu-id="a3d9f-234">Aggiungere comandi vocali sempre in ascolto in background.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-234">Add voice commands that always listen in the background.</span></span>
* <span data-ttu-id="a3d9f-235">Creare un ologrammi che reagisce a un comando vocale.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-235">Create a hologram that reacts to a voice command.</span></span>

### <a name="instructions"></a><span data-ttu-id="a3d9f-236">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="a3d9f-236">Instructions</span></span>

* <span data-ttu-id="a3d9f-237">Nel **gli script** cartella, creare uno script denominato **SpeechManager**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-237">In the **Scripts** folder, create a script named **SpeechManager**.</span></span>
* <span data-ttu-id="a3d9f-238">Trascinare il **SpeechManager** nello script le **OrigamiCollection** oggetto nella gerarchia di</span><span class="sxs-lookup"><span data-stu-id="a3d9f-238">Drag the **SpeechManager** script onto the **OrigamiCollection** object in the Hierarchy</span></span>
* <span data-ttu-id="a3d9f-239">Aprire il **SpeechManager** script in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-239">Open the **SpeechManager** script in Visual Studio.</span></span>
* <span data-ttu-id="a3d9f-240">Copiare e incollare questo codice nel **SpeechManager.cs** e **Salva tutto**:</span><span class="sxs-lookup"><span data-stu-id="a3d9f-240">Copy and paste this code into **SpeechManager.cs** and **Save All**:</span></span>

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

* <span data-ttu-id="a3d9f-241">Aprire il **SphereCommands** script in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-241">Open the **SphereCommands** script in Visual Studio.</span></span>
* <span data-ttu-id="a3d9f-242">Aggiornare lo script come segue:</span><span class="sxs-lookup"><span data-stu-id="a3d9f-242">Update the script to read as follows:</span></span>

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

* <span data-ttu-id="a3d9f-243">Esportare, compilare e distribuire l'app nell'emulatore di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-243">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="a3d9f-244">L'emulatore supporterà il microfono del PC e la propria voce: regolare la vista in modo che il cursore si trova in uno dei settori e pronunciare "Drop Sphere".</span><span class="sxs-lookup"><span data-stu-id="a3d9f-244">The emulator will support your PC's microphone and respond to your voice: adjust the view so the cursor is on one of the spheres, and say "Drop Sphere".</span></span>
* <span data-ttu-id="a3d9f-245">Ad esempio "**reimpostare World**" per riportarle posizioni iniziali.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-245">Say "**Reset World**" to bring them back to their initial positions.</span></span>

## <a name="chapter-5---spatial-sound"></a><span data-ttu-id="a3d9f-246">Capitolo 5 - spaziale audio</span><span class="sxs-lookup"><span data-stu-id="a3d9f-246">Chapter 5 - Spatial sound</span></span>

>[!VIDEO https://www.youtube.com/embed/Xc3C4VA10w4]

<span data-ttu-id="a3d9f-247">In questo capitolo, si sarà aggiungere musica all'app e quindi attivare effetti sonori su determinate azioni.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-247">In this chapter, we'll add music to the app, and then trigger sound effects on certain actions.</span></span> <span data-ttu-id="a3d9f-248">Utilizzeremo [spaziale audio](spatial-sound.md) per fornire un percorso specifico nello spazio 3D suoni.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-248">We'll be using [spatial sound](spatial-sound.md) to give sounds a specific location in 3D space.</span></span>

### <a name="objectives"></a><span data-ttu-id="a3d9f-249">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="a3d9f-249">Objectives</span></span>

* <span data-ttu-id="a3d9f-250">Ascolta vntana in tutto il mondo.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-250">Hear holograms in your world.</span></span>

### <a name="instructions"></a><span data-ttu-id="a3d9f-251">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="a3d9f-251">Instructions</span></span>

* <span data-ttu-id="a3d9f-252">In select Unity dal menu in alto **Modifica > Impostazioni di progetto > Audio**</span><span class="sxs-lookup"><span data-stu-id="a3d9f-252">In the Unity select from the top menu **Edit > Project Settings > Audio**</span></span>
* <span data-ttu-id="a3d9f-253">Trovare il **plug-in spaziale** impostazione e selezionare **MS HRTF Spatializer**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-253">Find the **Spatializer Plugin** setting and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="a3d9f-254">Dal **Vntana** cartella, trascinare le **atmosfera** dell'oggetto nel **OrigamiCollection** oggetto nel Pannello di gerarchia.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-254">From the **Holograms** folder, drag the **Ambience** object onto the **OrigamiCollection** object in the Hierarchy Panel.</span></span>
* <span data-ttu-id="a3d9f-255">Selezionare **OrigamiCollection** e trovare il **origine Audio** componente.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-255">Select **OrigamiCollection** and find the **Audio Source** component.</span></span> <span data-ttu-id="a3d9f-256">Modificare queste proprietà:</span><span class="sxs-lookup"><span data-stu-id="a3d9f-256">Change these properties:</span></span>
  * <span data-ttu-id="a3d9f-257">Verificare i **Spatialize** proprietà.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-257">Check the **Spatialize** property.</span></span>
  * <span data-ttu-id="a3d9f-258">Verificare i **Ascolta al attivi**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-258">Check the **Play On Awake**.</span></span>
  * <span data-ttu-id="a3d9f-259">Change **Blend spaziali** al **3D** trascinando il dispositivo di scorrimento fino a destra.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-259">Change **Spatial Blend** to **3D** by dragging the slider all the way to the right.</span></span>
  * <span data-ttu-id="a3d9f-260">Verificare i **ciclo** proprietà.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-260">Check the **Loop** property.</span></span>
  * <span data-ttu-id="a3d9f-261">Espandere **impostazioni 3D suono**e immettere **0,1** per **livello Doppler**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-261">Expand **3D Sound Settings**, and enter **0.1** for **Doppler Level**.</span></span>
  * <span data-ttu-id="a3d9f-262">Impostare **Volume attenuazione** al **attenuazione logaritmica**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-262">Set **Volume Rolloff** to **Logarithmic Rolloff**.</span></span>
  * <span data-ttu-id="a3d9f-263">Impostare **distanza massima** al **20**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-263">Set **Max Distance** to **20**.</span></span>
* <span data-ttu-id="a3d9f-264">Nel **gli script** cartella, creare uno script denominato **SphereSounds**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-264">In the **Scripts** folder, create a script named **SphereSounds**.</span></span>
* <span data-ttu-id="a3d9f-265">Trascinare **SphereSounds** per il **Sphere1** e **Sphere2** gli oggetti nella gerarchia.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-265">Drag **SphereSounds** to the **Sphere1** and **Sphere2** objects in the Hierarchy.</span></span>
* <span data-ttu-id="a3d9f-266">Aprire **SphereSounds** in Visual Studio, aggiornare il codice seguente e **Salva tutto**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-266">Open **SphereSounds** in Visual Studio, update the following code and **Save All**.</span></span>

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

* <span data-ttu-id="a3d9f-267">Salvare lo script e tornare a Unity.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-267">Save the script, and return to Unity.</span></span>
* <span data-ttu-id="a3d9f-268">Esportare, compilare e distribuire l'app nell'emulatore di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-268">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="a3d9f-269">Wear cuffie per ottenere l'effetto completo e spostare più da vicino e più lontano sul palco per ascoltare i suoni di modifica.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-269">Wear headphones to get the full effect, and move closer and further from the Stage to hear the sounds change.</span></span>

## <a name="chapter-6---spatial-mapping"></a><span data-ttu-id="a3d9f-270">Capitolo 6 - spaziali mapping</span><span class="sxs-lookup"><span data-stu-id="a3d9f-270">Chapter 6 - Spatial mapping</span></span>

>[!VIDEO https://www.youtube.com/embed/S-517Y63Cnk]

<span data-ttu-id="a3d9f-271">A questo punto si userà [mapping spaziale](spatial-mapping.md) per inserire la tavola da gioco in un oggetto reale nel mondo reale.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-271">Now we are going to use [spatial mapping](spatial-mapping.md) to place the game board on a real object in the real world.</span></span>

### <a name="objectives"></a><span data-ttu-id="a3d9f-272">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="a3d9f-272">Objectives</span></span>

* <span data-ttu-id="a3d9f-273">Rendere il mondo reale del mondo virtuale.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-273">Bring your real world into the virtual world.</span></span>
* <span data-ttu-id="a3d9f-274">Posizionare il vntana dove sono più importanti.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-274">Place your holograms where they matter most to you.</span></span>

### <a name="instructions"></a><span data-ttu-id="a3d9f-275">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="a3d9f-275">Instructions</span></span>

* <span data-ttu-id="a3d9f-276">Fare clic sui **Vntana** cartella nel Pannello di progetto.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-276">Click on the **Holograms** folder in the Project panel.</span></span>
* <span data-ttu-id="a3d9f-277">Trascinare il **Mapping spaziale** asset nella radice della **gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-277">Drag the **Spatial Mapping** asset into the root of the **Hierarchy**.</span></span>
* <span data-ttu-id="a3d9f-278">Fare clic sui **Mapping spaziale** oggetto nella gerarchia.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-278">Click on the **Spatial Mapping** object in the Hierarchy.</span></span>
* <span data-ttu-id="a3d9f-279">Nel **Pannello di controllo**, modificare le proprietà seguenti:</span><span class="sxs-lookup"><span data-stu-id="a3d9f-279">In the **Inspector panel**, change the following properties:</span></span>
  * <span data-ttu-id="a3d9f-280">Verificare i **disegnare Visual trame** casella.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-280">Check the **Draw Visual Meshes** box.</span></span>
  * <span data-ttu-id="a3d9f-281">Individuare **disegnare materiale** e fare clic sul cerchio nella parte destra.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-281">Locate **Draw Material** and click the circle on the right.</span></span> <span data-ttu-id="a3d9f-282">Tipo "**wireframe**" nel campo di ricerca nella parte superiore.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-282">Type "**wireframe**" into the search field at the top.</span></span> <span data-ttu-id="a3d9f-283">Fare clic sul risultato e quindi chiudere la finestra.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-283">Click on the result and then close the window.</span></span>
* <span data-ttu-id="a3d9f-284">Esportare, compilare e distribuire l'app nell'emulatore di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-284">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="a3d9f-285">Quando si esegue l'app, verrà visualizzata una mesh di una chat room living reali in precedenza sottoposta ad analisi nel wireframe in.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-285">When the app runs, a mesh of a previously scanned real-world living room will be rendered in wireframe.</span></span>
* <span data-ttu-id="a3d9f-286">Guarda come una sfera in sequenza rientrerà il palco e al tetto minimo.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-286">Watch how a rolling sphere will fall off the stage, and onto the floor!</span></span>

<span data-ttu-id="a3d9f-287">A questo punto vi mostreremo come spostare il OrigamiCollection in una nuova posizione:</span><span class="sxs-lookup"><span data-stu-id="a3d9f-287">Now we'll show you how to move the OrigamiCollection to a new location:</span></span>

* <span data-ttu-id="a3d9f-288">Nel **gli script** cartella, creare uno script denominato **TapToPlaceParent**.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-288">In the **Scripts** folder, create a script named **TapToPlaceParent**.</span></span>
* <span data-ttu-id="a3d9f-289">Nel **gerarchia**, espandere il **OrigamiCollection** e selezionare il **fase** oggetto.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-289">In the **Hierarchy**, expand the **OrigamiCollection** and select the **Stage** object.</span></span>
* <span data-ttu-id="a3d9f-290">Trascinare il **TapToPlaceParent** script l'oggetto di fase.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-290">Drag the **TapToPlaceParent** script onto the Stage object.</span></span>
* <span data-ttu-id="a3d9f-291">Aprire il **TapToPlaceParent** script in Visual Studio e aggiornarlo in modo da essere quanto segue:</span><span class="sxs-lookup"><span data-stu-id="a3d9f-291">Open the **TapToPlaceParent** script in Visual Studio, and update it to be the following:</span></span>

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

* <span data-ttu-id="a3d9f-292">Esportare, compilare e distribuire l'app.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-292">Export, build and deploy the app.</span></span>
* <span data-ttu-id="a3d9f-293">A questo punto dovrebbe ora essere possibile posizionare il gioco in una posizione specifica, gazing analizzarlo, tramite il movimento di Select (**oggetto** o barra spaziatrice) e quindi lo spostamento in una nuova posizione e l'utilizzo il movimento seleziona nuovamente.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-293">Now you should now be able to place the game in a specific location by gazing at it, using the Select gesture (**A** or Spacebar) and then moving to a new location, and using the Select gesture again.</span></span>

## <a name="the-end"></a><span data-ttu-id="a3d9f-294">La fine</span><span class="sxs-lookup"><span data-stu-id="a3d9f-294">The end</span></span>

<span data-ttu-id="a3d9f-295">E questo è il termine di questa esercitazione.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-295">And that's the end of this tutorial!</span></span>

<span data-ttu-id="a3d9f-296">Si è appreso:</span><span class="sxs-lookup"><span data-stu-id="a3d9f-296">You learned:</span></span>

* <span data-ttu-id="a3d9f-297">Come creare un'app holographic in Unity.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-297">How to create a holographic app in Unity.</span></span>
* <span data-ttu-id="a3d9f-298">Come rendere utilizzare sguardo, gesti, vocali, suoni e mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-298">How to make use of gaze, gesture, voice, sounds, and spatial mapping.</span></span>
* <span data-ttu-id="a3d9f-299">Come compilare e distribuire un'app usando Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-299">How to build and deploy an app using Visual Studio.</span></span>

<span data-ttu-id="a3d9f-300">Si è ora pronti per iniziare a creare App holographic.</span><span class="sxs-lookup"><span data-stu-id="a3d9f-300">You are now ready to start creating your own holographic apps!</span></span>

## <a name="see-also"></a><span data-ttu-id="a3d9f-301">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a3d9f-301">See also</span></span>

* [<span data-ttu-id="a3d9f-302">Nozioni fondamentali di MR 101: Progetto completo con dispositivo</span><span class="sxs-lookup"><span data-stu-id="a3d9f-302">MR Basics 101: Complete project with device</span></span>](holograms-101.md)
* [<span data-ttu-id="a3d9f-303">Sguardo</span><span class="sxs-lookup"><span data-stu-id="a3d9f-303">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="a3d9f-304">Movimenti</span><span class="sxs-lookup"><span data-stu-id="a3d9f-304">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="a3d9f-305">Input vocale</span><span class="sxs-lookup"><span data-stu-id="a3d9f-305">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="a3d9f-306">Spaziale audio</span><span class="sxs-lookup"><span data-stu-id="a3d9f-306">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="a3d9f-307">Mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="a3d9f-307">Spatial mapping</span></span>](spatial-mapping.md)

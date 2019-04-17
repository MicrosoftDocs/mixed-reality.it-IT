---
title: MR Spatial 230 - Spatial mapping
description: Seguire questa procedura dettagliata con Unity, Visual Studio e HoloLens che informazioni dettagliate sui concetti di mapping spaziale di codifica.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit unity, academy, esercitazione, mapping spaziale, la ricostruzione della superficie, mesh
ms.openlocfilehash: 8d5715337ddd20e9868b18fdf0c63c704f584972
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600923"
---
>[!NOTE]
><span data-ttu-id="a119c-104">Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.</span><span class="sxs-lookup"><span data-stu-id="a119c-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="a119c-105">Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.</span><span class="sxs-lookup"><span data-stu-id="a119c-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="a119c-106">Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.</span><span class="sxs-lookup"><span data-stu-id="a119c-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="a119c-107">Essi verranno mantenute per continuare a utilizzare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="a119c-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="a119c-108">Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="a119c-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="a119c-109">Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.</span><span class="sxs-lookup"><span data-stu-id="a119c-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-spatial-230-spatial-mapping"></a><span data-ttu-id="a119c-110">MR Spatial 230: Mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="a119c-110">MR Spatial 230: Spatial mapping</span></span>

<span data-ttu-id="a119c-111">[Mapping spaziale](spatial-mapping.md) unisce il mondo reale e il mondo virtuale da insegnare vntana sull'ambiente.</span><span class="sxs-lookup"><span data-stu-id="a119c-111">[Spatial mapping](spatial-mapping.md) combines the real world and virtual world together by teaching holograms about the environment.</span></span> <span data-ttu-id="a119c-112">MR spaziali 230 (progetto planetario) si apprenderà come:</span><span class="sxs-lookup"><span data-stu-id="a119c-112">In MR Spatial 230 (Project Planetarium) we'll learn how to:</span></span>

* <span data-ttu-id="a119c-113">Analizzare i dati di ambiente e il trasferimento di HoloLens al computer di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="a119c-113">Scan the environment and transfer data from the HoloLens to your development machine.</span></span>
* <span data-ttu-id="a119c-114">Esplorare gli shader e imparare a usarle per visualizzare lo spazio.</span><span class="sxs-lookup"><span data-stu-id="a119c-114">Explore shaders and learn how to use them for visualizing your space.</span></span>
* <span data-ttu-id="a119c-115">Suddividere la rete mesh di chat room in semplici piani utilizzando l'elaborazione di rete.</span><span class="sxs-lookup"><span data-stu-id="a119c-115">Break down the room mesh into simple planes using mesh processing.</span></span>
* <span data-ttu-id="a119c-116">Andare oltre le tecniche di selezione host abbiamo imparato negli [MR nozioni di base 101](holograms-101.md)e fornire commenti e suggerimenti sulla posizione ologramma nell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="a119c-116">Go beyond the placement techniques we learned in [MR Basics 101](holograms-101.md), and provide feedback about where a hologram can be placed in the environment.</span></span>
* <span data-ttu-id="a119c-117">Esplorare gli effetti di occlusione, in modo che quando l'ologrammi sono protetto da un oggetto reale, è comunque possibile visualizzarlo con raggi x!</span><span class="sxs-lookup"><span data-stu-id="a119c-117">Explore occlusion effects, so when your hologram is behind a real-world object, you can still see it with x-ray vision!</span></span>

>[!VIDEO https://www.youtube.com/embed/NSNYRkUX6Mw]

## <a name="device-support"></a><span data-ttu-id="a119c-118">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="a119c-118">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="a119c-119">Corso</span><span class="sxs-lookup"><span data-stu-id="a119c-119">Course</span></span></th><th style="width:150px"> <span data-ttu-id="a119c-120"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="a119c-120"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="a119c-121"><a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></span><span class="sxs-lookup"><span data-stu-id="a119c-121"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="a119c-122">MR Spatial 230: Mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="a119c-122">MR Spatial 230: Spatial mapping</span></span></td><td style="text-align: center;"> <span data-ttu-id="a119c-123">✔️</span><span class="sxs-lookup"><span data-stu-id="a119c-123">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="a119c-124">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="a119c-124">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="a119c-125">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="a119c-125">Prerequisites</span></span>

* <span data-ttu-id="a119c-126">Un PC Windows 10 configurate con i valori corretti [sono installati gli strumenti](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="a119c-126">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="a119c-127">Alcuni basic C# capacità di programmazione.</span><span class="sxs-lookup"><span data-stu-id="a119c-127">Some basic C# programming ability.</span></span>
* <span data-ttu-id="a119c-128">È necessario avere completato [MR nozioni di base 101](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="a119c-128">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="a119c-129">Un dispositivo HoloLens [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="a119c-129">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="a119c-130">File di progetto</span><span class="sxs-lookup"><span data-stu-id="a119c-130">Project files</span></span>

* <span data-ttu-id="a119c-131">Scaricare il [file](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) necessarie per il progetto.</span><span class="sxs-lookup"><span data-stu-id="a119c-131">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) required by the project.</span></span><span data-ttu-id="a119c-132"> Richiede Unity 2017.2 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="a119c-132"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="a119c-133">Se è comunque necessario il supporto di Unity 5.6, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip).</span><span class="sxs-lookup"><span data-stu-id="a119c-133">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip).</span></span>
  * <span data-ttu-id="a119c-134">Se è comunque necessario il supporto di Unity 5.5, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip).</span><span class="sxs-lookup"><span data-stu-id="a119c-134">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip).</span></span>
  * <span data-ttu-id="a119c-135">Se è ancora necessario supporto 5.4 di Unity, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip).</span><span class="sxs-lookup"><span data-stu-id="a119c-135">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip).</span></span>
* <span data-ttu-id="a119c-136">Annullare la-archive i file sul desktop o altri facile da raggiungere percorso.</span><span class="sxs-lookup"><span data-stu-id="a119c-136">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="a119c-137">Se si desidera esaminare il codice sorgente prima di scaricare, ha [disponibile in GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping).</span><span class="sxs-lookup"><span data-stu-id="a119c-137">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping).</span></span>

### <a name="notes"></a><span data-ttu-id="a119c-138">Note</span><span class="sxs-lookup"><span data-stu-id="a119c-138">Notes</span></span>

* <span data-ttu-id="a119c-139">"Abilita Just My Code" in Visual Studio deve essere disabilitato (*unchecked*) in Strumenti > Opzioni > debug per poter raggiungere punti di interruzione nel codice.</span><span class="sxs-lookup"><span data-stu-id="a119c-139">"Enable Just My Code" in Visual Studio needs to be disabled (*unchecked*) under Tools > Options > Debugging in order to hit breakpoints in your code.</span></span>

## <a name="unity-setup"></a><span data-ttu-id="a119c-140">Programma di installazione di Unity</span><span class="sxs-lookup"><span data-stu-id="a119c-140">Unity setup</span></span>

>[!VIDEO https://www.youtube.com/embed/y2Y4LhK6TEM]

* <span data-ttu-id="a119c-141">Avviare **Unity**.</span><span class="sxs-lookup"><span data-stu-id="a119c-141">Start **Unity**.</span></span>
* <span data-ttu-id="a119c-142">Selezionare **New** per creare un nuovo progetto.</span><span class="sxs-lookup"><span data-stu-id="a119c-142">Select **New** to create a new project.</span></span>
* <span data-ttu-id="a119c-143">Denominare il progetto **planetario**.</span><span class="sxs-lookup"><span data-stu-id="a119c-143">Name the project **Planetarium**.</span></span>
* <span data-ttu-id="a119c-144">Verificare che il **3D** impostazione è selezionata.</span><span class="sxs-lookup"><span data-stu-id="a119c-144">Verify that the **3D** setting is selected.</span></span>
* <span data-ttu-id="a119c-145">Fare clic su **Crea progetto**.</span><span class="sxs-lookup"><span data-stu-id="a119c-145">Click **Create Project**.</span></span>
* <span data-ttu-id="a119c-146">Dopo aver avviato di Unity, passare a **Modifica > Impostazioni di progetto > Player**.</span><span class="sxs-lookup"><span data-stu-id="a119c-146">Once Unity launches, go to **Edit > Project Settings > Player**.</span></span>
* <span data-ttu-id="a119c-147">Nel **Inspector** del pannello individuare e selezionare il colore verde **Windows Store** icona.</span><span class="sxs-lookup"><span data-stu-id="a119c-147">In the **Inspector** panel, find and select the green **Windows Store** icon.</span></span>
* <span data-ttu-id="a119c-148">Espandere **altre impostazioni**.</span><span class="sxs-lookup"><span data-stu-id="a119c-148">Expand **Other Settings**.</span></span>
* <span data-ttu-id="a119c-149">Nel **Rendering** sezione, verificare il **supportato di realtà virtuale** opzione.</span><span class="sxs-lookup"><span data-stu-id="a119c-149">In the **Rendering** section, check the **Virtual Reality Supported** option.</span></span>
* <span data-ttu-id="a119c-150">Verificare che **Windows Holographic** viene visualizzato nell'elenco dei **SDK di realtà virtuale**.</span><span class="sxs-lookup"><span data-stu-id="a119c-150">Verify that **Windows Holographic** appears in the list of **Virtual Reality SDKs**.</span></span> <span data-ttu-id="a119c-151">In caso contrario, selezionare la **+** pulsante nella parte inferiore dell'elenco e scegliere **Windows Holographic**.</span><span class="sxs-lookup"><span data-stu-id="a119c-151">If not, select the **+** button at the bottom of the list and choose **Windows Holographic**.</span></span>
* <span data-ttu-id="a119c-152">Espandere **impostazioni di pubblicazione**.</span><span class="sxs-lookup"><span data-stu-id="a119c-152">Expand **Publishing Settings**.</span></span>
* <span data-ttu-id="a119c-153">Nel **funzionalità** sezione, verificare le impostazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="a119c-153">In the **Capabilities** section, check the following settings:</span></span>
    * <span data-ttu-id="a119c-154">InternetClientServer</span><span class="sxs-lookup"><span data-stu-id="a119c-154">InternetClientServer</span></span>
    * <span data-ttu-id="a119c-155">PrivateNetworkClientServer</span><span class="sxs-lookup"><span data-stu-id="a119c-155">PrivateNetworkClientServer</span></span>
    * <span data-ttu-id="a119c-156">Microfono</span><span class="sxs-lookup"><span data-stu-id="a119c-156">Microphone</span></span>
    * <span data-ttu-id="a119c-157">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="a119c-157">SpatialPerception</span></span>
* <span data-ttu-id="a119c-158">Passare a **Modifica > impostazioni del progetto > qualità**</span><span class="sxs-lookup"><span data-stu-id="a119c-158">Go to **Edit > Project Settings > Quality**</span></span>
* <span data-ttu-id="a119c-159">Nel **Inspector** del pannello, sotto l'icona di Windows Store, seleziona la freccia nera elenco a discesa sotto la riga 'Default' e modificare l'impostazione predefinita al **Fastest**.</span><span class="sxs-lookup"><span data-stu-id="a119c-159">In the **Inspector** panel, under the Windows Store icon, select the black drop-down arrow under the 'Default' row and change the default setting to **Fastest**.</span></span>
* <span data-ttu-id="a119c-160">Passare a **asset > Importa pacchetto > pacchetto personalizzato**.</span><span class="sxs-lookup"><span data-stu-id="a119c-160">Go to **Assets > Import Package > Custom Package**.</span></span>
* <span data-ttu-id="a119c-161">Passare il **...\HolographicAcademy-Holograms-230-SpatialMapping\Starting** cartella.</span><span class="sxs-lookup"><span data-stu-id="a119c-161">Navigate to the **...\HolographicAcademy-Holograms-230-SpatialMapping\Starting** folder.</span></span>
* <span data-ttu-id="a119c-162">Fare clic su **Planetarium.unitypackage**.</span><span class="sxs-lookup"><span data-stu-id="a119c-162">Click on **Planetarium.unitypackage**.</span></span>
* <span data-ttu-id="a119c-163">Fare clic su **Apri**.</span><span class="sxs-lookup"><span data-stu-id="a119c-163">Click **Open**.</span></span>
* <span data-ttu-id="a119c-164">Un' **Importa pacchetto Unity** verrà visualizzata la finestra, fare clic sulla **importazione** pulsante.</span><span class="sxs-lookup"><span data-stu-id="a119c-164">An **Import Unity Package** window should appear, click on the **Import** button.</span></span>
* <span data-ttu-id="a119c-165">Attendere per Unity importare tutte le risorse che è necessario completare questo progetto.</span><span class="sxs-lookup"><span data-stu-id="a119c-165">Wait for Unity to import all of the assets that we will need to complete this project.</span></span>
* <span data-ttu-id="a119c-166">Nel **gerarchia** panel, eliminare il **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="a119c-166">In the **Hierarchy** panel, delete the **Main Camera**.</span></span>
* <span data-ttu-id="a119c-167">Nel **Project** pannello **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** cartella trovare il **Main Camera** oggetto.</span><span class="sxs-lookup"><span data-stu-id="a119c-167">In the **Project** panel, **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** folder, find the **Main Camera** object.</span></span>
* <span data-ttu-id="a119c-168">Trascinare e rilasciare il **Main Camera** prefab nel **gerarchia** pannello.</span><span class="sxs-lookup"><span data-stu-id="a119c-168">Drag and drop the **Main Camera** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="a119c-169">Nel **gerarchia** panel, eliminare il **Directional Light** oggetto.</span><span class="sxs-lookup"><span data-stu-id="a119c-169">In the **Hierarchy** panel, delete the **Directional Light** object.</span></span>
* <span data-ttu-id="a119c-170">Nel **Project** pannello **Vntana** cartella, individuare il **cursore** oggetto.</span><span class="sxs-lookup"><span data-stu-id="a119c-170">In the **Project** panel, **Holograms** folder, locate the **Cursor** object.</span></span>
* <span data-ttu-id="a119c-171">Trascinare e rilasciare il **cursore** prefab nel **gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="a119c-171">Drag & drop the **Cursor** prefab into the **Hierarchy**.</span></span>
* <span data-ttu-id="a119c-172">Nel **gerarchia** riquadro, seleziona la **cursore** oggetto.</span><span class="sxs-lookup"><span data-stu-id="a119c-172">In the **Hierarchy** panel, select the **Cursor** object.</span></span>
* <span data-ttu-id="a119c-173">Nel **Inspector** del pannello, fare clic sul **Layer** elenco a discesa e selezionare **modificare i livelli...** .</span><span class="sxs-lookup"><span data-stu-id="a119c-173">In the **Inspector** panel, click the **Layer** drop-down and select **Edit Layers...**.</span></span>
* <span data-ttu-id="a119c-174">Nome **livello di utente 31** come "**SpatialMapping**".</span><span class="sxs-lookup"><span data-stu-id="a119c-174">Name **User Layer 31** as "**SpatialMapping**".</span></span>
* <span data-ttu-id="a119c-175">Salvare la nuova scena: **File > Salva scena come...**</span><span class="sxs-lookup"><span data-stu-id="a119c-175">Save the new scene: **File > Save Scene As...**</span></span>
* <span data-ttu-id="a119c-176">Fare clic su **nuova cartella** e denominare la cartella **scene**.</span><span class="sxs-lookup"><span data-stu-id="a119c-176">Click **New Folder** and name the folder **Scenes**.</span></span>
* <span data-ttu-id="a119c-177">Denominare il file "**planetario**" e salvarlo nel **scene** cartella.</span><span class="sxs-lookup"><span data-stu-id="a119c-177">Name the file "**Planetarium**" and save it in the **Scenes** folder.</span></span>

## <a name="chapter-1---scanning"></a><span data-ttu-id="a119c-178">Capitolo 1 - l'analisi</span><span class="sxs-lookup"><span data-stu-id="a119c-178">Chapter 1 - Scanning</span></span>

>[!VIDEO https://www.youtube.com/embed/888oW51z_cE]

<span data-ttu-id="a119c-179">**Obiettivi**</span><span class="sxs-lookup"><span data-stu-id="a119c-179">**Objectives**</span></span>
* <span data-ttu-id="a119c-180">Scopri il SurfaceObserver e in che modo l'impatto delle impostazioni esperienza e le prestazioni.</span><span class="sxs-lookup"><span data-stu-id="a119c-180">Learn about the SurfaceObserver and how its settings impact experience and performance.</span></span>
* <span data-ttu-id="a119c-181">Creare una chat room analisi esperienza per raccogliere le trame della chat.</span><span class="sxs-lookup"><span data-stu-id="a119c-181">Create a room scanning experience to collect the meshes of your room.</span></span>

<span data-ttu-id="a119c-182">**Istruzioni**</span><span class="sxs-lookup"><span data-stu-id="a119c-182">**Instructions**</span></span>
* <span data-ttu-id="a119c-183">Nel **Project** pannello **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** cartella trovare il **SpatialMapping** prefab.</span><span class="sxs-lookup"><span data-stu-id="a119c-183">In the **Project** panel **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** folder, find the **SpatialMapping** prefab.</span></span>
* <span data-ttu-id="a119c-184">Trascinare e rilasciare il **SpatialMapping** prefab nel **gerarchia** pannello.</span><span class="sxs-lookup"><span data-stu-id="a119c-184">Drag & drop the **SpatialMapping** prefab into the **Hierarchy** panel.</span></span>

<span data-ttu-id="a119c-185">**Compila e Distribuisci (parte 1)**</span><span class="sxs-lookup"><span data-stu-id="a119c-185">**Build and Deploy (part 1)**</span></span>
* <span data-ttu-id="a119c-186">In Unity, selezionare **File > Build Settings**.</span><span class="sxs-lookup"><span data-stu-id="a119c-186">In Unity, select **File > Build Settings**.</span></span>
* <span data-ttu-id="a119c-187">Fare clic su **aggiungere scene Open** per aggiungere il **planetario** scena alla compilazione.</span><span class="sxs-lookup"><span data-stu-id="a119c-187">Click **Add Open Scenes** to add the **Planetarium** scene to the build.</span></span>
* <span data-ttu-id="a119c-188">Selezionare **Universal Windows Platform** nel **Platform** elenco e fare clic su **commutatore piattaforma**.</span><span class="sxs-lookup"><span data-stu-id="a119c-188">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="a119c-189">Impostare **SDK** al **10 Universal** e **tipo di compilazione UWP** al **D3D**.</span><span class="sxs-lookup"><span data-stu-id="a119c-189">Set **SDK** to **Universal 10** and **UWP Build Type** to **D3D**.</span></span>
* <span data-ttu-id="a119c-190">Controllare **Unity C# progetti**.</span><span class="sxs-lookup"><span data-stu-id="a119c-190">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="a119c-191">Fai clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="a119c-191">Click **Build**.</span></span>
* <span data-ttu-id="a119c-192">Creare un **nuova cartella** denominato "App".</span><span class="sxs-lookup"><span data-stu-id="a119c-192">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="a119c-193">Solo clic i **App** cartella.</span><span class="sxs-lookup"><span data-stu-id="a119c-193">Single click the **App** folder.</span></span>
* <span data-ttu-id="a119c-194">Premere il **selezionare la cartella** pulsante.</span><span class="sxs-lookup"><span data-stu-id="a119c-194">Press the **Select Folder** button.</span></span>
* <span data-ttu-id="a119c-195">Quando l'operazione Unity viene eseguita la compilazione, verrà visualizzata una finestra di Esplora File.</span><span class="sxs-lookup"><span data-stu-id="a119c-195">When Unity is done building, a File Explorer window will appear.</span></span>
* <span data-ttu-id="a119c-196">Fare doppio clic sulla **App** cartella per aprirla.</span><span class="sxs-lookup"><span data-stu-id="a119c-196">Double-click on the **App** folder to open it.</span></span>
* <span data-ttu-id="a119c-197">Fare doppio clic su **Planetarium.sln** per caricare il progetto in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a119c-197">Double-click on **Planetarium.sln** to load the project in Visual Studio.</span></span>
* <span data-ttu-id="a119c-198">In Visual Studio, usare la barra degli strumenti superiore per modificare la configurazione per **rilascio**.</span><span class="sxs-lookup"><span data-stu-id="a119c-198">In Visual Studio, use the top toolbar to change the Configuration to **Release**.</span></span>
* <span data-ttu-id="a119c-199">Modificare la piattaforma **x86**.</span><span class="sxs-lookup"><span data-stu-id="a119c-199">Change the Platform to **x86**.</span></span>
* <span data-ttu-id="a119c-200">Fare clic sulla freccia giù a destra di 'Locale' e selezionare **computer remoto**.</span><span class="sxs-lookup"><span data-stu-id="a119c-200">Click on the drop-down arrow to the right of 'Local Machine', and select **Remote Machine**.</span></span>
* <span data-ttu-id="a119c-201">Immettere [indirizzo IP del dispositivo](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) l'indirizzo del campo e modificare la modalità di autenticazione per **universale (protocollo non crittografato)**.</span><span class="sxs-lookup"><span data-stu-id="a119c-201">Enter [your device's IP address](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) in the Address field and change Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span>
* <span data-ttu-id="a119c-202">Fare clic su **Debug -> Avvia senza eseguire debug** o premere **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="a119c-202">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="a119c-203">Guarda il **Output** pannello in Visual Studio per la compilazione e distribuzione stato.</span><span class="sxs-lookup"><span data-stu-id="a119c-203">Watch the **Output** panel in Visual Studio for build and deploy status.</span></span>
* <span data-ttu-id="a119c-204">Dopo aver distribuito l'app, scorrere nella stanza.</span><span class="sxs-lookup"><span data-stu-id="a119c-204">Once your app has deployed, walk around the room.</span></span> <span data-ttu-id="a119c-205">Si noterà superfici circostante rientrano le reti mesh di wireframe bianco e nero.</span><span class="sxs-lookup"><span data-stu-id="a119c-205">You will see the surrounding surfaces covered by black and white wireframe meshes.</span></span>
* <span data-ttu-id="a119c-206">Analizzare l'ambiente circostante.</span><span class="sxs-lookup"><span data-stu-id="a119c-206">Scan your surroundings.</span></span> <span data-ttu-id="a119c-207">Assicurarsi di esaminare le pareti, limiti e piani.</span><span class="sxs-lookup"><span data-stu-id="a119c-207">Be sure to look at walls, ceilings, and floors.</span></span>

<span data-ttu-id="a119c-208">**Compila e Distribuisci (parte 2)**</span><span class="sxs-lookup"><span data-stu-id="a119c-208">**Build and Deploy (part 2)**</span></span>

<span data-ttu-id="a119c-209">Ora esaminiamo come Mapping spaziale può influire sulle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="a119c-209">Now let's explore how Spatial Mapping can affect performance.</span></span>
* <span data-ttu-id="a119c-210">In Unity, selezionare **finestra > Profiler**.</span><span class="sxs-lookup"><span data-stu-id="a119c-210">In Unity, select **Window > Profiler**.</span></span>
* <span data-ttu-id="a119c-211">Fare clic su **aggiungere Profiler > GPU**.</span><span class="sxs-lookup"><span data-stu-id="a119c-211">Click **Add Profiler > GPU**.</span></span>
* <span data-ttu-id="a119c-212">Fare clic su **Profiler attivo > <Enter IP>** .</span><span class="sxs-lookup"><span data-stu-id="a119c-212">Click **Active Profiler > <Enter IP>**.</span></span>
* <span data-ttu-id="a119c-213">Immettere il **indirizzo IP** di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a119c-213">Enter the **IP address** of your HoloLens.</span></span>
* <span data-ttu-id="a119c-214">Fare clic su **Connetti**.</span><span class="sxs-lookup"><span data-stu-id="a119c-214">Click **Connect**.</span></span>
* <span data-ttu-id="a119c-215">Osservare il numero di millisecondi impiegato per la GPU eseguire il rendering di un frame.</span><span class="sxs-lookup"><span data-stu-id="a119c-215">Observe the number of milliseconds it takes for the GPU to render a frame.</span></span>
* <span data-ttu-id="a119c-216">Interrompere l'applicazione in esecuzione nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a119c-216">Stop the application from running on the device.</span></span>
* <span data-ttu-id="a119c-217">Tornare a Visual Studio e aprire **SpatialMappingObserver.cs**.</span><span class="sxs-lookup"><span data-stu-id="a119c-217">Return to Visual Studio and open **SpatialMappingObserver.cs**.</span></span> <span data-ttu-id="a119c-218">Si troverà nella cartella HoloToolkit\SpatialMapping del progetto di Assembly-CSharp (Windows universale).</span><span class="sxs-lookup"><span data-stu-id="a119c-218">You will find it in the HoloToolkit\SpatialMapping folder of the Assembly-CSharp (Universal Windows) project.</span></span>
* <span data-ttu-id="a119c-219">Trovare il **Awake()** funzione e aggiungere la riga di codice seguente: **TrianglesPerCubicMeter = 1200;**</span><span class="sxs-lookup"><span data-stu-id="a119c-219">Find the **Awake()** function, and add the following line of code: **TrianglesPerCubicMeter = 1200;**</span></span>
* <span data-ttu-id="a119c-220">Ridistribuire il progetto sul dispositivo e quindi **riconnettere il profiler**.</span><span class="sxs-lookup"><span data-stu-id="a119c-220">Re-deploy the project to your device, and then **reconnect the profiler**.</span></span> <span data-ttu-id="a119c-221">Osservare la modifica del numero di millisecondi per il rendering di un frame.</span><span class="sxs-lookup"><span data-stu-id="a119c-221">Observe the change in the number of milliseconds to render a frame.</span></span>
* <span data-ttu-id="a119c-222">Interrompere l'applicazione in esecuzione nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a119c-222">Stop the application from running on the device.</span></span>

<span data-ttu-id="a119c-223">**Salvare e caricare in Unity**</span><span class="sxs-lookup"><span data-stu-id="a119c-223">**Save and load in Unity**</span></span>

<span data-ttu-id="a119c-224">Infine, è possibile salvare la rete mesh di chat e caricarli in Unity.</span><span class="sxs-lookup"><span data-stu-id="a119c-224">Finally, let's save our room mesh and load it into Unity.</span></span>
* <span data-ttu-id="a119c-225">Tornare a Visual Studio e rimuovere i **TrianglesPerCubicMeter** riga aggiunta nel **Awake()** funzione durante la sezione precedente.</span><span class="sxs-lookup"><span data-stu-id="a119c-225">Return to Visual Studio and remove the **TrianglesPerCubicMeter** line that you added in the **Awake()** function during the previous section.</span></span>
* <span data-ttu-id="a119c-226">Ridistribuire il progetto nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a119c-226">Redeploy the project to your device.</span></span> <span data-ttu-id="a119c-227">Si dovrebbe ora essere eseguito con **500** triangoli per metro cubo.</span><span class="sxs-lookup"><span data-stu-id="a119c-227">We should now be running with **500** triangles per cubic meter.</span></span>
* <span data-ttu-id="a119c-228">Aprire un browser e immettere il HoloLens IPAddress per passare al **Windows Device Portal**.</span><span class="sxs-lookup"><span data-stu-id="a119c-228">Open a browser and enter in your HoloLens IPAddress to navigate to the **Windows Device Portal**.</span></span>
* <span data-ttu-id="a119c-229">Selezionare il **vista 3D** opzione nel riquadro sinistro.</span><span class="sxs-lookup"><span data-stu-id="a119c-229">Select the **3D View** option in the left panel.</span></span>
* <span data-ttu-id="a119c-230">Sotto **ricostruzione della superficie di attacco** selezionare la **Update** pulsante.</span><span class="sxs-lookup"><span data-stu-id="a119c-230">Under **Surface reconstruction** select the **Update** button.</span></span>
* <span data-ttu-id="a119c-231">Guarda le aree che sono analizzati in di HoloLens vengono visualizzati nella finestra di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="a119c-231">Watch as the areas that you have scanned on your HoloLens appear in the display window.</span></span>
* <span data-ttu-id="a119c-232">Per salvare le analisi di chat, premere il **salvare** pulsante.</span><span class="sxs-lookup"><span data-stu-id="a119c-232">To save your room scan, press the **Save** button.</span></span>
* <span data-ttu-id="a119c-233">Aprire il **Downloads** nella cartella e individuare il modello di spazio salvato **SRMesh.obj**.</span><span class="sxs-lookup"><span data-stu-id="a119c-233">Open your **Downloads** folder to find the saved room model **SRMesh.obj**.</span></span>
* <span data-ttu-id="a119c-234">Copia **SRMesh.obj** per il **asset** cartella del progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="a119c-234">Copy **SRMesh.obj** to the **Assets** folder of your Unity project.</span></span>
* <span data-ttu-id="a119c-235">In Unity, selezionare la **SpatialMapping** dell'oggetto nel **gerarchia** pannello.</span><span class="sxs-lookup"><span data-stu-id="a119c-235">In Unity, select the **SpatialMapping** object in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="a119c-236">Individuare il **oggetto area osservatore (Script)** componente.</span><span class="sxs-lookup"><span data-stu-id="a119c-236">Locate the **Object Surface Observer (Script)** component.</span></span>
* <span data-ttu-id="a119c-237">Fare clic sul cerchio a destra del **stanza modello** proprietà.</span><span class="sxs-lookup"><span data-stu-id="a119c-237">Click the circle to the right of the **Room Model** property.</span></span>
* <span data-ttu-id="a119c-238">Individuare e selezionare il **SRMesh** dell'oggetto e quindi chiudere la finestra.</span><span class="sxs-lookup"><span data-stu-id="a119c-238">Find and select the **SRMesh** object and then close the window.</span></span>
* <span data-ttu-id="a119c-239">Verificare che il **modello chat Room** proprietà nel **Inspector** pannello è ora impostato su **SRMesh**.</span><span class="sxs-lookup"><span data-stu-id="a119c-239">Verify that the **Room Model** property in the **Inspector** panel is now set to **SRMesh**.</span></span>
* <span data-ttu-id="a119c-240">Premere il **riprodurre** pulsante per attivare la modalità di anteprima di Unity.</span><span class="sxs-lookup"><span data-stu-id="a119c-240">Press the **Play** button to enter Unity's preview mode.</span></span>
* <span data-ttu-id="a119c-241">Il componente SpatialMapping caricherà il mesh dal modello di spazio salvato in modo che è possibile usarli in Unity.</span><span class="sxs-lookup"><span data-stu-id="a119c-241">The SpatialMapping component will load the meshes from the saved room model so you can use them in Unity.</span></span>
* <span data-ttu-id="a119c-242">Passare a **scena** visualizzazione per vedere tutto del modello di chat room visualizzato con lo shader wireframe.</span><span class="sxs-lookup"><span data-stu-id="a119c-242">Switch to **Scene** view to see all of your room model displayed with the wireframe shader.</span></span>
* <span data-ttu-id="a119c-243">Premere il **riprodurre** pulsante per uscire dalla modalità di anteprima.</span><span class="sxs-lookup"><span data-stu-id="a119c-243">Press the **Play** button again to exit preview mode.</span></span>

<span data-ttu-id="a119c-244">**NOTA:** La volta successiva immettere la modalità di anteprima in Unity, caricherà la mesh spazio salvato per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="a119c-244">**NOTE:** The next time that you enter preview mode in Unity, it will load the saved room mesh by default.</span></span>

## <a name="chapter-2---visualization"></a><span data-ttu-id="a119c-245">Capitolo 2 - visualizzazione</span><span class="sxs-lookup"><span data-stu-id="a119c-245">Chapter 2 - Visualization</span></span>

>[!VIDEO https://www.youtube.com/embed/RnkvXl-aXD4]

<span data-ttu-id="a119c-246">**Obiettivi**</span><span class="sxs-lookup"><span data-stu-id="a119c-246">**Objectives**</span></span>
* <span data-ttu-id="a119c-247">Informazioni di base di shader.</span><span class="sxs-lookup"><span data-stu-id="a119c-247">Learn the basics of shaders.</span></span>
* <span data-ttu-id="a119c-248">Visualizzare l'ambiente circostante.</span><span class="sxs-lookup"><span data-stu-id="a119c-248">Visualize your surroundings.</span></span>

<span data-ttu-id="a119c-249">**Istruzioni**</span><span class="sxs-lookup"><span data-stu-id="a119c-249">**Instructions**</span></span>
* <span data-ttu-id="a119c-250">Nella finestra di Unity **gerarchia** riquadro, seleziona la **SpatialMapping** oggetto.</span><span class="sxs-lookup"><span data-stu-id="a119c-250">In Unity's **Hierarchy** panel, select the **SpatialMapping** object.</span></span>
* <span data-ttu-id="a119c-251">Nel **Inspector** panel, trovare il **Manager Mapping spaziale (Script)** componente.</span><span class="sxs-lookup"><span data-stu-id="a119c-251">In the **Inspector** panel, find the **Spatial Mapping Manager (Script)** component.</span></span>
* <span data-ttu-id="a119c-252">Fare clic sul cerchio a destra del **materiale area** proprietà.</span><span class="sxs-lookup"><span data-stu-id="a119c-252">Click the circle to the right of the **Surface Material** property.</span></span>
* <span data-ttu-id="a119c-253">Individuare e selezionare il **BlueLinesOnWalls** materiale e chiudere la finestra.</span><span class="sxs-lookup"><span data-stu-id="a119c-253">Find and select the **BlueLinesOnWalls** material and close the window.</span></span>
* <span data-ttu-id="a119c-254">Nel **Project** pannello **shader** cartella, fare doppio clic su **BlueLinesOnWalls** per aprire lo shader in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a119c-254">In the **Project** panel **Shaders** folder, double-click on **BlueLinesOnWalls** to open the shader in Visual Studio.</span></span>
* <span data-ttu-id="a119c-255">Si tratta di un pixel semplice (vertice per frammentare) shader, che esegue le attività seguenti:</span><span class="sxs-lookup"><span data-stu-id="a119c-255">This is a simple pixel (vertex to fragment) shader, which accomplishes the following tasks:</span></span>
    1. <span data-ttu-id="a119c-256">Converte la posizione del vertice spazio globale.</span><span class="sxs-lookup"><span data-stu-id="a119c-256">Converts a vertex's location to world space.</span></span>
    2. <span data-ttu-id="a119c-257">Controlla che il vertice 's normale per determinare se un pixel è verticale.</span><span class="sxs-lookup"><span data-stu-id="a119c-257">Checks the vertex's normal to determine if a pixel is vertical.</span></span>
    3. <span data-ttu-id="a119c-258">Imposta il colore del pixel per il rendering.</span><span class="sxs-lookup"><span data-stu-id="a119c-258">Sets the color of the pixel for rendering.</span></span>

<span data-ttu-id="a119c-259">**Compilare e distribuire**</span><span class="sxs-lookup"><span data-stu-id="a119c-259">**Build and Deploy**</span></span>
* <span data-ttu-id="a119c-260">Tornare a Unity e premere **riprodurre** per attivare la modalità di anteprima.</span><span class="sxs-lookup"><span data-stu-id="a119c-260">Return to Unity and press **Play** to enter preview mode.</span></span>
* <span data-ttu-id="a119c-261">Verranno eseguito il rendering di linee blu su tutte le superfici verticale della rete locale (che viene caricata automaticamente dai nostri dati analisi salvati).</span><span class="sxs-lookup"><span data-stu-id="a119c-261">Blue lines will be rendered on all vertical surfaces of the room mesh (which automatically loaded from our saved scanning data).</span></span>
* <span data-ttu-id="a119c-262">Passare al **scena** pressione di tab per regolare la vista della chat room e vedere come mesh intero chat room viene visualizzato in Unity.</span><span class="sxs-lookup"><span data-stu-id="a119c-262">Switch to the **Scene** tab to adjust your view of the room and see how the entire room mesh appears in Unity.</span></span>
* <span data-ttu-id="a119c-263">Nel **Project** panel, trovare il **materiali** cartella e selezionare il **BlueLinesOnWalls** materiale.</span><span class="sxs-lookup"><span data-stu-id="a119c-263">In the **Project** panel, find the **Materials** folder and select the **BlueLinesOnWalls** material.</span></span>
* <span data-ttu-id="a119c-264">Modificare alcune proprietà e vedere come vengono visualizzate le modifiche apportate nell'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="a119c-264">Modify some properties and see how the changes appear in the Unity editor.</span></span>
    * <span data-ttu-id="a119c-265">Nel **Inspector** panel, regolare le **LineScale** valore come è possibile visualizzare le righe più spesso o più sottili.</span><span class="sxs-lookup"><span data-stu-id="a119c-265">In the **Inspector** panel, adjust the **LineScale** value to make the lines appear thicker or thinner.</span></span>
    * <span data-ttu-id="a119c-266">Nel **Inspector** del pannello, regolare le **LinesPerMeter** valore per modificare il numero di righe vengono visualizzati su ogni parete.</span><span class="sxs-lookup"><span data-stu-id="a119c-266">In the **Inspector** panel, adjust the **LinesPerMeter** value to change how many lines appear on each wall.</span></span>
* <span data-ttu-id="a119c-267">Fare clic su **riprodurre** per uscire dalla modalità di anteprima.</span><span class="sxs-lookup"><span data-stu-id="a119c-267">Click **Play** again to exit preview mode.</span></span>
* <span data-ttu-id="a119c-268">Compilare e distribuire di HoloLens e osservare l'aspetto dello shader per il rendering su superfici reali.</span><span class="sxs-lookup"><span data-stu-id="a119c-268">Build and deploy to the HoloLens and observe how the shader rendering appears on real surfaces.</span></span>

<span data-ttu-id="a119c-269">Unity offre interessanti di visualizzazione in anteprima dei materiali, ma è sempre una buona idea per il rendering di estrazione nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a119c-269">Unity does a great job of previewing materials, but it's always a good idea to check-out rendering in the device.</span></span>

## <a name="chapter-3---processing"></a><span data-ttu-id="a119c-270">Capitolo 3 - elaborazione</span><span class="sxs-lookup"><span data-stu-id="a119c-270">Chapter 3 - Processing</span></span>

>[!VIDEO https://www.youtube.com/embed/kaUKiNiDxwY]

<span data-ttu-id="a119c-271">**Obiettivi**</span><span class="sxs-lookup"><span data-stu-id="a119c-271">**Objectives**</span></span>
* <span data-ttu-id="a119c-272">Informazioni sulle tecniche per l'elaborazione dati di mapping spaziale da utilizzare nell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="a119c-272">Learn techniques to process spatial mapping data for use in your application.</span></span>
* <span data-ttu-id="a119c-273">Analizzare i dati di mapping spaziale per trovare i piani e rimuovere triangoli.</span><span class="sxs-lookup"><span data-stu-id="a119c-273">Analyze spatial mapping data to find planes and remove triangles.</span></span>
* <span data-ttu-id="a119c-274">Usare i piani per la selezione host di ologramma.</span><span class="sxs-lookup"><span data-stu-id="a119c-274">Use planes for hologram placement.</span></span>

<span data-ttu-id="a119c-275">**Istruzioni**</span><span class="sxs-lookup"><span data-stu-id="a119c-275">**Instructions**</span></span>
* <span data-ttu-id="a119c-276">Nella finestra di Unity **progetto** pannello **Vntana** cartella trovare il **SpatialProcessing** oggetto.</span><span class="sxs-lookup"><span data-stu-id="a119c-276">In Unity's **Project** panel, **Holograms** folder, find the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="a119c-277">Trascinare e rilasciare il **SpatialProcessing** all'oggetto il **gerarchia** pannello.</span><span class="sxs-lookup"><span data-stu-id="a119c-277">Drag & drop the **SpatialProcessing** object into the **Hierarchy** panel.</span></span>

<span data-ttu-id="a119c-278">Il prefab SpatialProcessing include i componenti per l'elaborazione dei dati di mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="a119c-278">The SpatialProcessing prefab includes components for processing the spatial mapping data.</span></span> <span data-ttu-id="a119c-279">**SurfaceMeshesToPlanes.cs** troveranno e generare piani in base ai dati di mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="a119c-279">**SurfaceMeshesToPlanes.cs** will find and generate planes based on the spatial mapping data.</span></span> <span data-ttu-id="a119c-280">Si userà i piani nella nostra applicazione per rappresentare le pareti, piani e parte intera superiore.</span><span class="sxs-lookup"><span data-stu-id="a119c-280">We will use planes in our application to represent walls, floors and ceilings.</span></span> <span data-ttu-id="a119c-281">Include anche questo prefab **RemoveSurfaceVertices.cs** cui poter rimuovere i vertici mesh mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="a119c-281">This prefab also includes **RemoveSurfaceVertices.cs** which can remove vertices from the spatial mapping mesh.</span></span> <span data-ttu-id="a119c-282">Può essere utilizzato per creare aree libere nella mesh o rimuovere in eccesso triangoli che non sono più necessarie (perché è invece possono utilizzare piani).</span><span class="sxs-lookup"><span data-stu-id="a119c-282">This can be used to create holes in the mesh, or to remove excess triangles that are no longer needed (because planes can be used instead).</span></span>
* <span data-ttu-id="a119c-283">Nella finestra di Unity **progetto** pannello **Vntana** cartella trovare il **SpaceCollection** oggetto.</span><span class="sxs-lookup"><span data-stu-id="a119c-283">In Unity's **Project** panel, **Holograms** folder, find the **SpaceCollection** object.</span></span>
* <span data-ttu-id="a119c-284">Trascinare e rilasciare il **SpaceCollection** all'oggetto il **gerarchia** pannello.</span><span class="sxs-lookup"><span data-stu-id="a119c-284">Drag and drop the **SpaceCollection** object into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="a119c-285">Nel **gerarchia** riquadro, seleziona la **SpatialProcessing** oggetto.</span><span class="sxs-lookup"><span data-stu-id="a119c-285">In the **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="a119c-286">Nel **Inspector** panel, trovare il **riprodurre spazio Manager (Script)** componente.</span><span class="sxs-lookup"><span data-stu-id="a119c-286">In the **Inspector** panel, find the **Play Space Manager (Script)** component.</span></span>
* <span data-ttu-id="a119c-287">Fare doppio clic su **PlaySpaceManager.cs** per aprirlo in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a119c-287">Double-click on **PlaySpaceManager.cs** to open it in Visual Studio.</span></span>

<span data-ttu-id="a119c-288">PlaySpaceManager.cs contiene codice specifico dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="a119c-288">PlaySpaceManager.cs contains application-specific code.</span></span> <span data-ttu-id="a119c-289">Si aggiungeranno funzionalità per questo script per abilitare il comportamento seguente:</span><span class="sxs-lookup"><span data-stu-id="a119c-289">We will add functionality to this script to enable the following behavior:</span></span>
1. <span data-ttu-id="a119c-290">Arrestare la raccolta dei dati di mapping spaziale dopo abbiamo superano il limite di tempo di analisi (10 secondi).</span><span class="sxs-lookup"><span data-stu-id="a119c-290">Stop collecting spatial mapping data after we exceed the scanning time limit (10 seconds).</span></span>
2. <span data-ttu-id="a119c-291">Elaborare i dati di mapping spaziale:</span><span class="sxs-lookup"><span data-stu-id="a119c-291">Process the spatial mapping data:</span></span>
    1. <span data-ttu-id="a119c-292">Usare SurfaceMeshesToPlanes per creare una semplice rappresentazione del mondo come piani (walls pavimenti, limiti, e così via).</span><span class="sxs-lookup"><span data-stu-id="a119c-292">Use SurfaceMeshesToPlanes to create a simpler representation of the world as planes (walls, floors, ceilings, etc).</span></span>
    2. <span data-ttu-id="a119c-293">Utilizzare RemoveSurfaceVertices rimuovere superficie triangoli che rientrano nei limiti del piano.</span><span class="sxs-lookup"><span data-stu-id="a119c-293">Use RemoveSurfaceVertices to remove surface triangles that fall within plane boundaries.</span></span>
3. <span data-ttu-id="a119c-294">Generare una raccolta di vntana in tutto il mondo e collocarli in piani muro e floor vicino all'utente.</span><span class="sxs-lookup"><span data-stu-id="a119c-294">Generate a collection of holograms in the world and place them on wall and floor planes near the user.</span></span>

<span data-ttu-id="a119c-295">Eseguire gli esercizi di scrittura di codice contrassegnati in PlaySpaceManager.cs o sostituire lo script con la soluzione finale dal codice seguente:</span><span class="sxs-lookup"><span data-stu-id="a119c-295">Complete the coding exercises marked in PlaySpaceManager.cs, or replace the script with the finished solution from below:</span></span>

```cs
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;

/// <summary>
/// The SurfaceManager class allows applications to scan the environment for a specified amount of time 
/// and then process the Spatial Mapping Mesh (find planes, remove vertices) after that time has expired.
/// </summary>
public class PlaySpaceManager : Singleton<PlaySpaceManager>
{
    [Tooltip("When checked, the SurfaceObserver will stop running after a specified amount of time.")]
    public bool limitScanningByTime = true;

    [Tooltip("How much time (in seconds) that the SurfaceObserver will run after being started; used when 'Limit Scanning By Time' is checked.")]
    public float scanTime = 30.0f;

    [Tooltip("Material to use when rendering Spatial Mapping meshes while the observer is running.")]
    public Material defaultMaterial;

    [Tooltip("Optional Material to use when rendering Spatial Mapping meshes after the observer has been stopped.")]
    public Material secondaryMaterial;

    [Tooltip("Minimum number of floor planes required in order to exit scanning/processing mode.")]
    public uint minimumFloors = 1;

    [Tooltip("Minimum number of wall planes required in order to exit scanning/processing mode.")]
    public uint minimumWalls = 1;

    /// <summary>
    /// Indicates if processing of the surface meshes is complete.
    /// </summary>
    private bool meshesProcessed = false;

    /// <summary>
    /// GameObject initialization.
    /// </summary>
    private void Start()
    {
        // Update surfaceObserver and storedMeshes to use the same material during scanning.
        SpatialMappingManager.Instance.SetSurfaceMaterial(defaultMaterial);

        // Register for the MakePlanesComplete event.
        SurfaceMeshesToPlanes.Instance.MakePlanesComplete += SurfaceMeshesToPlanes_MakePlanesComplete;
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        // Check to see if the spatial mapping data has been processed
        // and if we are limiting how much time the user can spend scanning.
        if (!meshesProcessed && limitScanningByTime)
        {
            // If we have not processed the spatial mapping data
            // and scanning time is limited...

            // Check to see if enough scanning time has passed
            // since starting the observer.
            if (limitScanningByTime && ((Time.time - SpatialMappingManager.Instance.StartTime) < scanTime))
            {
                // If we have a limited scanning time, then we should wait until
                // enough time has passed before processing the mesh.
            }
            else
            {
                // The user should be done scanning their environment,
                // so start processing the spatial mapping data...

                /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

                // 3.a: Check if IsObserverRunning() is true on the
                // SpatialMappingManager.Instance.
                if(SpatialMappingManager.Instance.IsObserverRunning())
                {
                    // 3.a: If running, Stop the observer by calling
                    // StopObserver() on the SpatialMappingManager.Instance.
                    SpatialMappingManager.Instance.StopObserver();
                }

                // 3.a: Call CreatePlanes() to generate planes.
                CreatePlanes();

                // 3.a: Set meshesProcessed to true.
                meshesProcessed = true;
            }
        }
    }

    /// <summary>
    /// Handler for the SurfaceMeshesToPlanes MakePlanesComplete event.
    /// </summary>
    /// <param name="source">Source of the event.</param>
    /// <param name="args">Args for the event.</param>
    private void SurfaceMeshesToPlanes_MakePlanesComplete(object source, System.EventArgs args)
    {
        /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

        // Collection of floor and table planes that we can use to set horizontal items on.
        List<GameObject> horizontal = new List<GameObject>();

        // Collection of wall planes that we can use to set vertical items on.
        List<GameObject> vertical = new List<GameObject>();

        // 3.a: Get all floor and table planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'horizontal' list.
        horizontal = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Table | PlaneTypes.Floor);

        // 3.a: Get all wall planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'vertical' list.
        vertical = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Wall);

        // Check to see if we have enough horizontal planes (minimumFloors)
        // and vertical planes (minimumWalls), to set holograms on in the world.
        if (horizontal.Count >= minimumFloors && vertical.Count >= minimumWalls)
        {
            // We have enough floors and walls to place our holograms on...

            // 3.a: Let's reduce our triangle count by removing triangles
            // from SpatialMapping meshes that intersect with our active planes.
            // Call RemoveVertices().
            // Pass in all activePlanes found by SurfaceMeshesToPlanes.Instance.
            RemoveVertices(SurfaceMeshesToPlanes.Instance.ActivePlanes);

            // 3.a: We can indicate to the user that scanning is over by
            // changing the material applied to the Spatial Mapping meshes.
            // Call SpatialMappingManager.Instance.SetSurfaceMaterial().
            // Pass in the secondaryMaterial.
            SpatialMappingManager.Instance.SetSurfaceMaterial(secondaryMaterial);

            // 3.a: We are all done processing the mesh, so we can now
            // initialize a collection of Placeable holograms in the world
            // and use horizontal/vertical planes to set their starting positions.
            // Call SpaceCollectionManager.Instance.GenerateItemsInWorld().
            // Pass in the lists of horizontal and vertical planes that we found earlier.
            SpaceCollectionManager.Instance.GenerateItemsInWorld(horizontal, vertical);
        }
        else
        {
            // We do not have enough floors/walls to place our holograms on...

            // 3.a: Re-enter scanning mode so the user can find more surfaces by 
            // calling StartObserver() on the SpatialMappingManager.Instance.
            SpatialMappingManager.Instance.StartObserver();

            // 3.a: Re-process spatial data after scanning completes by
            // re-setting meshesProcessed to false.
            meshesProcessed = false;
        }
    }

    /// <summary>
    /// Creates planes from the spatial mapping surfaces.
    /// </summary>
    private void CreatePlanes()
    {
        // Generate planes based on the spatial map.
        SurfaceMeshesToPlanes surfaceToPlanes = SurfaceMeshesToPlanes.Instance;
        if (surfaceToPlanes != null && surfaceToPlanes.enabled)
        {
            surfaceToPlanes.MakePlanes();
        }
    }

    /// <summary>
    /// Removes triangles from the spatial mapping surfaces.
    /// </summary>
    /// <param name="boundingObjects"></param>
    private void RemoveVertices(IEnumerable<GameObject> boundingObjects)
    {
        RemoveSurfaceVertices removeVerts = RemoveSurfaceVertices.Instance;
        if (removeVerts != null && removeVerts.enabled)
        {
            removeVerts.RemoveSurfaceVerticesWithinBounds(boundingObjects);
        }
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        if (SurfaceMeshesToPlanes.Instance != null)
        {
            SurfaceMeshesToPlanes.Instance.MakePlanesComplete -= SurfaceMeshesToPlanes_MakePlanesComplete;
        }
    }
}
```

<span data-ttu-id="a119c-296">**Compilare e distribuire**</span><span class="sxs-lookup"><span data-stu-id="a119c-296">**Build and Deploy**</span></span>
* <span data-ttu-id="a119c-297">Prima di distribuire il HoloLens, premere il **riprodurre** pulsante in Unity per attivare la modalità di riproduzione.</span><span class="sxs-lookup"><span data-stu-id="a119c-297">Before deploying to the HoloLens, press the **Play** button in Unity to enter play mode.</span></span>
* <span data-ttu-id="a119c-298">Al termine della mesh chat room viene caricata da file, attendere 10 secondi prima che inizi l'elaborazione della rete di mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="a119c-298">After the room mesh is loaded from file, wait for 10 seconds before processing starts on the spatial mapping mesh.</span></span>
* <span data-ttu-id="a119c-299">Una volta completata l'elaborazione, i piani verranno visualizzato per rappresentare la parte intera pareti, ceiling, e così via.</span><span class="sxs-lookup"><span data-stu-id="a119c-299">When processing is complete, planes will appear to represent the floor, walls, ceiling, etc.</span></span>
* <span data-ttu-id="a119c-300">Dopo che tutti i piani di sono stati trovati, verrà visualizzato un sistema solare in una tabella di floor vicino alla fotocamera.</span><span class="sxs-lookup"><span data-stu-id="a119c-300">After all of the planes have been found, you should see a solar system appear on a table of floor near the camera.</span></span>
* <span data-ttu-id="a119c-301">Due poster dovrebbe essere visualizzato troppo sui muri vicino alla fotocamera.</span><span class="sxs-lookup"><span data-stu-id="a119c-301">Two posters should appear on walls near the camera too.</span></span> <span data-ttu-id="a119c-302">Passare al **scena** se non è possibile visualizzarli nella **gioco** modalità.</span><span class="sxs-lookup"><span data-stu-id="a119c-302">Switch to the **Scene** tab if you cannot see them in **Game** mode.</span></span>
* <span data-ttu-id="a119c-303">Premere il **riprodurre** pulsante per uscire dalla modalità di gioco.</span><span class="sxs-lookup"><span data-stu-id="a119c-303">Press the **Play** button again to exit play mode.</span></span>
* <span data-ttu-id="a119c-304">Compilare e distribuire per HoloLens, come di consueto.</span><span class="sxs-lookup"><span data-stu-id="a119c-304">Build and deploy to the HoloLens, as usual.</span></span>
* <span data-ttu-id="a119c-305">Attesa per l'analisi e l'elaborazione dei dati spaziali mapping per il completamento.</span><span class="sxs-lookup"><span data-stu-id="a119c-305">Wait for scanning and processing of the spatial mapping data to complete.</span></span>
* <span data-ttu-id="a119c-306">Dopo aver visualizzato i piani, provare a trovare il poster e il sistema solare in tutto il mondo.</span><span class="sxs-lookup"><span data-stu-id="a119c-306">Once you see planes, try to find the solar system and posters in your world.</span></span>

## <a name="chapter-4---placement"></a><span data-ttu-id="a119c-307">Capitolo 4 - Selezione host</span><span class="sxs-lookup"><span data-stu-id="a119c-307">Chapter 4 - Placement</span></span>

>[!VIDEO https://www.youtube.com/embed/Srhtpid1uZc]

<span data-ttu-id="a119c-308">**Obiettivi**</span><span class="sxs-lookup"><span data-stu-id="a119c-308">**Objectives**</span></span>
* <span data-ttu-id="a119c-309">Determinare se ologramma rientrerà in una superficie.</span><span class="sxs-lookup"><span data-stu-id="a119c-309">Determine if a hologram will fit on a surface.</span></span>
* <span data-ttu-id="a119c-310">Fornire un feedback all'utente quando ologramma can/non rientra in una superficie.</span><span class="sxs-lookup"><span data-stu-id="a119c-310">Provide feedback to the user when a hologram can/cannot fit on a surface.</span></span>

<span data-ttu-id="a119c-311">**Istruzioni**</span><span class="sxs-lookup"><span data-stu-id="a119c-311">**Instructions**</span></span>
* <span data-ttu-id="a119c-312">Nella finestra di Unity **gerarchia** riquadro, seleziona la **SpatialProcessing** oggetto.</span><span class="sxs-lookup"><span data-stu-id="a119c-312">In Unity's **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="a119c-313">Nel **Inspector** panel, trovare il **trame per piani area (Script)** componente.</span><span class="sxs-lookup"><span data-stu-id="a119c-313">In the **Inspector** panel, find the **Surface Meshes To Planes (Script)** component.</span></span>
* <span data-ttu-id="a119c-314">Modifica il **disegnare piani** proprietà **Nothing** di deselezione della selezione.</span><span class="sxs-lookup"><span data-stu-id="a119c-314">Change the **Draw Planes** property to **Nothing** to clear the selection.</span></span>
* <span data-ttu-id="a119c-315">Modifica il **disegnare piani** proprietà **parete**, in modo che solo i piani wall verranno sottoposti a rendering.</span><span class="sxs-lookup"><span data-stu-id="a119c-315">Change the **Draw Planes** property to **Wall**, so that only wall planes will be rendered.</span></span>
* <span data-ttu-id="a119c-316">Nel **Project** pannello **script** cartella, fare doppio clic su **Placeable.cs** per aprirlo in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a119c-316">In the **Project** panel, **Scripts** folder, double-click on **Placeable.cs** to open it in Visual Studio.</span></span>

<span data-ttu-id="a119c-317">Il **Placeable** script è già associato ai poster e finestra di proiezione che vengono creati al termine dell'individuazione di piano.</span><span class="sxs-lookup"><span data-stu-id="a119c-317">The **Placeable** script is already attached to the posters and projection box that are created after plane finding completes.</span></span> <span data-ttu-id="a119c-318">Tutto dobbiamo fare è rimuovere il commento del codice e lo script verrà ottenere quanto segue:</span><span class="sxs-lookup"><span data-stu-id="a119c-318">All we need to do is uncomment some code, and this script will achieve the following:</span></span>
1. <span data-ttu-id="a119c-319">Determinare se ologramma rientrerà in una superficie da raycasting dal centro e quattro angoli del rettangolo di selezione cubo.</span><span class="sxs-lookup"><span data-stu-id="a119c-319">Determine if a hologram will fit on a surface by raycasting from the center and four corners of the bounding cube.</span></span>
2. <span data-ttu-id="a119c-320">Verifica per determinare se è abbastanza uniforme per ologrammi attendere flush in normale alla superficie.</span><span class="sxs-lookup"><span data-stu-id="a119c-320">Check the surface normal to determine if it is smooth enough for the hologram to sit flush on.</span></span>
3. <span data-ttu-id="a119c-321">Eseguire il rendering di un cubo di delimitazione intorno ologramma per mostrare l'effettiva dimensione durante l'inserimento.</span><span class="sxs-lookup"><span data-stu-id="a119c-321">Render a bounding cube around the hologram to show its actual size while being placed.</span></span>
4. <span data-ttu-id="a119c-322">Eseguire il cast di ologramma per mostrare in cui verrà inserito sul pavimento/muro sotto e dietro un'ombreggiatura.</span><span class="sxs-lookup"><span data-stu-id="a119c-322">Cast a shadow under/behind the hologram to show where it will be placed on the floor/wall.</span></span>
5. <span data-ttu-id="a119c-323">Eseguire il rendering dell'ombreggiatura in rosso, se l'ologrammi non possono trovarsi sulla superficie, o verde, se possibile.</span><span class="sxs-lookup"><span data-stu-id="a119c-323">Render the shadow as red, if the hologram cannot be placed on the surface, or green, if it can.</span></span>
6. <span data-ttu-id="a119c-324">Orientare nuovamente di ologramma per allinearli con il tipo di area (verticale o orizzontale) che disponga di affinità.</span><span class="sxs-lookup"><span data-stu-id="a119c-324">Re-orient the hologram to align with the surface type (vertical or horizontal) that it has affinity to.</span></span>
7. <span data-ttu-id="a119c-325">Posizionare in modo uniforme l'ologrammi nell'area di selezionato per evitare il passaggio o il comportamento di blocco.</span><span class="sxs-lookup"><span data-stu-id="a119c-325">Smoothly place the hologram on the selected surface to avoid jumping or snapping behavior.</span></span>

<span data-ttu-id="a119c-326">Rimuovere il commento da tutto il codice nell'esercizio scrittura di codice riportato di seguito oppure usare questa soluzione completata nelle **Placeable.cs**:</span><span class="sxs-lookup"><span data-stu-id="a119c-326">Uncomment all code in the coding exercise below, or use this completed solution in **Placeable.cs**:</span></span>

```cs
using System.Collections.Generic;
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Enumeration containing the surfaces on which a GameObject
/// can be placed.  For simplicity of this sample, only one
/// surface type is allowed to be selected.
/// </summary>
public enum PlacementSurfaces
{
    // Horizontal surface with an upward pointing normal.    
    Horizontal = 1,

    // Vertical surface with a normal facing the user.
    Vertical = 2,
}

/// <summary>
/// The Placeable class implements the logic used to determine if a GameObject
/// can be placed on a target surface. Constraints for placement include:
/// * No part of the GameObject's box collider impacts with another object in the scene
/// * The object lays flat (within specified tolerances) against the surface
/// * The object would not fall off of the surface if gravity were enabled.
/// This class also provides the following visualizations.
/// * A transparent cube representing the object's box collider.
/// * Shadow on the target surface indicating whether or not placement is valid.
/// </summary>
public class Placeable : MonoBehaviour
{
    [Tooltip("The base material used to render the bounds asset when placement is allowed.")]
    public Material PlaceableBoundsMaterial = null;

    [Tooltip("The base material used to render the bounds asset when placement is not allowed.")]
    public Material NotPlaceableBoundsMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it allowed.")]
    public Material PlaceableShadowMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it not allowed.")]
    public Material NotPlaceableShadowMaterial = null;

    [Tooltip("The type of surface on which the object can be placed.")]
    public PlacementSurfaces PlacementSurface = PlacementSurfaces.Horizontal;

    [Tooltip("The child object(s) to hide during placement.")]
    public List<GameObject> ChildrenToHide = new List<GameObject>();

    /// <summary>
    /// Indicates if the object is in the process of being placed.
    /// </summary>
    public bool IsPlacing { get; private set; }

    // The most recent distance to the surface.  This is used to 
    // locate the object when the user's gaze does not intersect
    // with the Spatial Mapping mesh.
    private float lastDistance = 2.0f;

    // The distance away from the target surface that the object should hover prior while being placed.
    private float hoverDistance = 0.15f;

    // Threshold (the closer to 0, the stricter the standard) used to determine if a surface is flat.
    private float distanceThreshold = 0.02f;

    // Threshold (the closer to 1, the stricter the standard) used to determine if a surface is vertical.
    private float upNormalThreshold = 0.9f;

    // Maximum distance, from the object, that placement is allowed.
    // This is used when raycasting to see if the object is near a placeable surface.
    private float maximumPlacementDistance = 5.0f;

    // Speed (1.0 being fastest) at which the object settles to the surface upon placement.
    private float placementVelocity = 0.06f;

    // Indicates whether or not this script manages the object's box collider.
    private bool managingBoxCollider = false;

    // The box collider used to determine of the object will fit in the desired location.
    // It is also used to size the bounding cube.
    private BoxCollider boxCollider = null;

    // Visible asset used to show the dimensions of the object. This asset is sized
    // using the box collider's bounds.
    private GameObject boundsAsset = null;

    // Visible asset used to show the where the object is attempting to be placed.
    // This asset is sized using the box collider's bounds.
    private GameObject shadowAsset = null;

    // The location at which the object will be placed.
    private Vector3 targetPosition;

    /// <summary>
    /// Called when the GameObject is created.
    /// </summary>
    private void Awake()
    {
        targetPosition = gameObject.transform.position;

        // Get the object's collider.
        boxCollider = gameObject.GetComponent<BoxCollider>();
        if (boxCollider == null)
        {
            // The object does not have a collider, create one and remember that
            // we are managing it.
            managingBoxCollider = true;
            boxCollider = gameObject.AddComponent<BoxCollider>();
            boxCollider.enabled = false;
        }

        // Create the object that will be used to indicate the bounds of the GameObject.
        boundsAsset = GameObject.CreatePrimitive(PrimitiveType.Cube);
        boundsAsset.transform.parent = gameObject.transform;
        boundsAsset.SetActive(false);

        // Create a object that will be used as a shadow.
        shadowAsset = GameObject.CreatePrimitive(PrimitiveType.Quad);
        shadowAsset.transform.parent = gameObject.transform;
        shadowAsset.SetActive(false);
    }

    /// <summary>
    /// Called when our object is selected.  Generally called by
    /// a gesture management component.
    /// </summary>
    public void OnSelect()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (!IsPlacing)
        {
            OnPlacementStart();
        }
        else
        {
            OnPlacementStop();
        }
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (IsPlacing)
        {
            // Move the object.
            Move();

            // Set the visual elements.
            Vector3 targetPosition;
            Vector3 surfaceNormal;
            bool canBePlaced = ValidatePlacement(out targetPosition, out surfaceNormal);
            DisplayBounds(canBePlaced);
            DisplayShadow(targetPosition, surfaceNormal, canBePlaced);
        }
        else
        {
            // Disable the visual elements.
            boundsAsset.SetActive(false);
            shadowAsset.SetActive(false);

            // Gracefully place the object on the target surface.
            float dist = (gameObject.transform.position - targetPosition).magnitude;
            if (dist > 0)
            {
                gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, targetPosition, placementVelocity / dist);
            }
            else
            {
                // Unhide the child object(s) to make placement easier.
                for (int i = 0; i < ChildrenToHide.Count; i++)
                {
                    ChildrenToHide[i].SetActive(true);
                }
            }
        }
    }

    /// <summary>
    /// Verify whether or not the object can be placed.
    /// </summary>
    /// <param name="position">
    /// The target position on the surface.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the object is to be placed.
    /// </param>
    /// <returns>
    /// True if the target position is valid for placing the object, otherwise false.
    /// </returns>
    private bool ValidatePlacement(out Vector3 position, out Vector3 surfaceNormal)
    {
        Vector3 raycastDirection = gameObject.transform.forward;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            // Raycast from the bottom face of the box collider.
            raycastDirection = -(Vector3.up);
        }

        // Initialize out parameters.
        position = Vector3.zero;
        surfaceNormal = Vector3.zero;

        Vector3[] facePoints = GetColliderFacePoints();

        // The origin points we receive are in local space and we 
        // need to raycast in world space.
        for (int i = 0; i < facePoints.Length; i++)
        {
            facePoints[i] = gameObject.transform.TransformVector(facePoints[i]) + gameObject.transform.position;
        }

        // Cast a ray from the center of the box collider face to the surface.
        RaycastHit centerHit;
        if (!Physics.Raycast(facePoints[0],
                        raycastDirection,
                        out centerHit,
                        maximumPlacementDistance,
                        SpatialMappingManager.Instance.LayerMask))
        {
            // If the ray failed to hit the surface, we are done.
            return false;
        }

        // We have found a surface.  Set position and surfaceNormal.
        position = centerHit.point;
        surfaceNormal = centerHit.normal;

        // Cast a ray from the corners of the box collider face to the surface.
        for (int i = 1; i < facePoints.Length; i++)
        {
            RaycastHit hitInfo;
            if (Physics.Raycast(facePoints[i],
                                raycastDirection,
                                out hitInfo,
                                maximumPlacementDistance,
                                SpatialMappingManager.Instance.LayerMask))
            {
                // To be a valid placement location, each of the corners must have a similar
                // enough distance to the surface as the center point
                if (!IsEquivalentDistance(centerHit.distance, hitInfo.distance))
                {
                    return false;
                }
            }
            else
            {
                // The raycast failed to intersect with the target layer.
                return false;
            }
        }

        return true;
    }

    /// <summary>
    /// Determine the coordinates, in local space, of the box collider face that 
    /// will be placed against the target surface.
    /// </summary>
    /// <returns>
    /// Vector3 array with the center point of the face at index 0.
    /// </returns>
    private Vector3[] GetColliderFacePoints()
    {
        // Get the collider extents.  
        // The size values are twice the extents.
        Vector3 extents = boxCollider.size / 2;

        // Calculate the min and max values for each coordinate.
        float minX = boxCollider.center.x - extents.x;
        float maxX = boxCollider.center.x + extents.x;
        float minY = boxCollider.center.y - extents.y;
        float maxY = boxCollider.center.y + extents.y;
        float minZ = boxCollider.center.z - extents.z;
        float maxZ = boxCollider.center.z + extents.z;

        Vector3 center;
        Vector3 corner0;
        Vector3 corner1;
        Vector3 corner2;
        Vector3 corner3;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            center = new Vector3(boxCollider.center.x, minY, boxCollider.center.z);
            corner0 = new Vector3(minX, minY, minZ);
            corner1 = new Vector3(minX, minY, maxZ);
            corner2 = new Vector3(maxX, minY, minZ);
            corner3 = new Vector3(maxX, minY, maxZ);
        }
        else
        {
            // Placing on vertical surfaces.
            center = new Vector3(boxCollider.center.x, boxCollider.center.y, maxZ);
            corner0 = new Vector3(minX, minY, maxZ);
            corner1 = new Vector3(minX, maxY, maxZ);
            corner2 = new Vector3(maxX, minY, maxZ);
            corner3 = new Vector3(maxX, maxY, maxZ);
        }

        return new Vector3[] { center, corner0, corner1, corner2, corner3 };
    }

    /// <summary>
    /// Put the object into placement mode.
    /// </summary>
    public void OnPlacementStart()
    {
        // If we are managing the collider, enable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = true;
        }

        // Hide the child object(s) to make placement easier.
        for (int i = 0; i < ChildrenToHide.Count; i++)
        {
            ChildrenToHide[i].SetActive(false);
        }

        // Tell the gesture manager that it is to assume
        // all input is to be given to this object.
        GestureManager.Instance.OverrideFocusedObject = gameObject;

        // Enter placement mode.
        IsPlacing = true;
    }

    /// <summary>
    /// Take the object out of placement mode.
    /// </summary>
    /// <remarks>
    /// This method will leave the object in placement mode if called while
    /// the object is in an invalid location.  To determine whether or not
    /// the object has been placed, check the value of the IsPlacing property.
    /// </remarks>
    public void OnPlacementStop()
    {
        // ValidatePlacement requires a normal as an out parameter.
        Vector3 position;
        Vector3 surfaceNormal;

        // Check to see if we can exit placement mode.
        if (!ValidatePlacement(out position, out surfaceNormal))
        {
            return;
        }

        // The object is allowed to be placed.
        // We are placing at a small buffer away from the surface.
        targetPosition = position + (0.01f * surfaceNormal);

        OrientObject(true, surfaceNormal);

        // If we are managing the collider, disable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = false;
        }

        // Tell the gesture manager that it is to resume
        // its normal behavior.
        GestureManager.Instance.OverrideFocusedObject = null;

        // Exit placement mode.
        IsPlacing = false;
    }

    /// <summary>
    /// Positions the object along the surface toward which the user is gazing.
    /// </summary>
    /// <remarks>
    /// If the user's gaze does not intersect with a surface, the object
    /// will remain at the most recently calculated distance.
    /// </remarks>
    private void Move()
    {
        Vector3 moveTo = gameObject.transform.position;
        Vector3 surfaceNormal = Vector3.zero;
        RaycastHit hitInfo;

        bool hit = Physics.Raycast(Camera.main.transform.position,
                                Camera.main.transform.forward,
                                out hitInfo,
                                20f,
                                SpatialMappingManager.Instance.LayerMask);

        if (hit)
        {
            float offsetDistance = hoverDistance;

            // Place the object a small distance away from the surface while keeping 
            // the object from going behind the user.
            if (hitInfo.distance <= hoverDistance)
            {
                offsetDistance = 0f;
            }

            moveTo = hitInfo.point + (offsetDistance * hitInfo.normal);

            lastDistance = hitInfo.distance;
            surfaceNormal = hitInfo.normal;
        }
        else
        {
            // The raycast failed to hit a surface.  In this case, keep the object at the distance of the last
            // intersected surface.
            moveTo = Camera.main.transform.position + (Camera.main.transform.forward * lastDistance);
        }

        // Follow the user's gaze.
        float dist = Mathf.Abs((gameObject.transform.position - moveTo).magnitude);
        gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, moveTo, placementVelocity / dist);

        // Orient the object.
        // We are using the return value from Physics.Raycast to instruct
        // the OrientObject function to align to the vertical surface if appropriate.
        OrientObject(hit, surfaceNormal);
    }

    /// <summary>
    /// Orients the object so that it faces the user.
    /// </summary>
    /// <param name="alignToVerticalSurface">
    /// If true and the object is to be placed on a vertical surface, 
    /// orient parallel to the target surface.  If false, orient the object 
    /// to face the user.
    /// </param>
    /// <param name="surfaceNormal">
    /// The target surface's normal vector.
    /// </param>
    /// <remarks>
    /// The aligntoVerticalSurface parameter is ignored if the object
    /// is to be placed on a horizontalSurface
    /// </remarks>
    private void OrientObject(bool alignToVerticalSurface, Vector3 surfaceNormal)
    {
        Quaternion rotation = Camera.main.transform.localRotation;

        // If the user's gaze does not intersect with the Spatial Mapping mesh,
        // orient the object towards the user.
        if (alignToVerticalSurface && (PlacementSurface == PlacementSurfaces.Vertical))
        {
            // We are placing on a vertical surface.
            // If the normal of the Spatial Mapping mesh indicates that the
            // surface is vertical, orient parallel to the surface.
            if (Mathf.Abs(surfaceNormal.y) <= (1 - upNormalThreshold))
            {
                rotation = Quaternion.LookRotation(-surfaceNormal, Vector3.up);
            }
        }
        else
        {
            rotation.x = 0f;
            rotation.z = 0f;
        }

        gameObject.transform.rotation = rotation;
    }

    /// <summary>
    /// Displays the bounds asset.
    /// </summary>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayBounds(bool canBePlaced)
    {
        // Ensure the bounds asset is sized and positioned correctly.
        boundsAsset.transform.localPosition = boxCollider.center;
        boundsAsset.transform.localScale = boxCollider.size;
        boundsAsset.transform.rotation = gameObject.transform.rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = PlaceableBoundsMaterial;
        }
        else
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableBoundsMaterial;
        }

        // Show the bounds asset.
        boundsAsset.SetActive(true);
    }

    /// <summary>
    /// Displays the placement shadow asset.
    /// </summary>
    /// <param name="position">
    /// The position at which to place the shadow asset.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the asset will be placed
    /// </param>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayShadow(Vector3 position,
                            Vector3 surfaceNormal,
                            bool canBePlaced)
    {
        // Rotate and scale the shadow so that it is displayed on the correct surface and matches the object.
        float rotationX = 0.0f;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            rotationX = 90.0f;
            shadowAsset.transform.localScale = new Vector3(boxCollider.size.x, boxCollider.size.z, 1);
        }
        else
        {
            shadowAsset.transform.localScale = boxCollider.size;
        }

        Quaternion rotation = Quaternion.Euler(rotationX, gameObject.transform.rotation.eulerAngles.y, 0);
        shadowAsset.transform.rotation = rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = PlaceableShadowMaterial;
        }
        else
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableShadowMaterial;
        }

        // Show the shadow asset as appropriate.        
        if (position != Vector3.zero)
        {
            // Position the shadow a small distance from the target surface, along the normal.
            shadowAsset.transform.position = position + (0.01f * surfaceNormal);
            shadowAsset.SetActive(true);
        }
        else
        {
            shadowAsset.SetActive(false);
        }
    }

    /// <summary>
    /// Determines if two distance values should be considered equivalent. 
    /// </summary>
    /// <param name="d1">
    /// Distance to compare.
    /// </param>
    /// <param name="d2">
    /// Distance to compare.
    /// </param>
    /// <returns>
    /// True if the distances are within the desired tolerance, otherwise false.
    /// </returns>
    private bool IsEquivalentDistance(float d1, float d2)
    {
        float dist = Mathf.Abs(d1 - d2);
        return (dist <= distanceThreshold);
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        // Unload objects we have created.
        Destroy(boundsAsset);
        boundsAsset = null;
        Destroy(shadowAsset);
        shadowAsset = null;
    }
}
```

<span data-ttu-id="a119c-327">**Compilare e distribuire**</span><span class="sxs-lookup"><span data-stu-id="a119c-327">**Build and Deploy**</span></span>
* <span data-ttu-id="a119c-328">Come in precedenza, compilare il progetto e distribuire il HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a119c-328">As before, build the project and deploy to the HoloLens.</span></span>
* <span data-ttu-id="a119c-329">Attesa per l'analisi e l'elaborazione dei dati spaziali mapping per il completamento.</span><span class="sxs-lookup"><span data-stu-id="a119c-329">Wait for scanning and processing of the spatial mapping data to complete.</span></span>
* <span data-ttu-id="a119c-330">Quando viene visualizzato il sistema solare, fissare la casella di proiezione seguito ed eseguire un gesto seleziona spostarla all'interno.</span><span class="sxs-lookup"><span data-stu-id="a119c-330">When you see the solar system, gaze at the projection box below and perform a select gesture to move it around.</span></span> <span data-ttu-id="a119c-331">Dopo avere selezionata la casella di proiezione, un cubo di delimitazione sarà visibile intorno alla casella di proiezione.</span><span class="sxs-lookup"><span data-stu-id="a119c-331">While the projection box is selected, a bounding cube will be visible around the projection box.</span></span>
* <span data-ttu-id="a119c-332">Spostare head per fissare un percorso diverso nella chat room.</span><span class="sxs-lookup"><span data-stu-id="a119c-332">Move you head to gaze at a different location in the room.</span></span> <span data-ttu-id="a119c-333">La casella di proiezione deve seguire lo sguardo.</span><span class="sxs-lookup"><span data-stu-id="a119c-333">The projection box should follow your gaze.</span></span> <span data-ttu-id="a119c-334">Quando l'ombreggiatura sotto la casella di proiezione in rosso, è possibile posizionare l'ologrammi in tale area.</span><span class="sxs-lookup"><span data-stu-id="a119c-334">When the shadow below the projection box turns red, you cannot place the hologram on that surface.</span></span> <span data-ttu-id="a119c-335">Quando l'ombreggiatura sotto la casella di proiezione diventa verde, è possibile inserire l'ologrammi eseguendo il movimento di seleziona un altro.</span><span class="sxs-lookup"><span data-stu-id="a119c-335">When the shadow below the projection box turns green, you can place the hologram by performing another select gesture.</span></span>
* <span data-ttu-id="a119c-336">Trovare e selezionare uno dei poster holographic su una parete per spostarlo in una nuova posizione.</span><span class="sxs-lookup"><span data-stu-id="a119c-336">Find and select one of the holographic posters on a wall to move it to a new location.</span></span> <span data-ttu-id="a119c-337">Si noti che non è possibile posizionare il poster per il piano o il limite massimo, e che sia sempre orientamento corretto per ogni muro si sposta all'interno.</span><span class="sxs-lookup"><span data-stu-id="a119c-337">Notice that you cannot place the poster on the floor or ceiling, and that it stays correctly oriented to each wall as you move around.</span></span>

## <a name="chapter-5---occlusion"></a><span data-ttu-id="a119c-338">Capitolo 5 - occlusione</span><span class="sxs-lookup"><span data-stu-id="a119c-338">Chapter 5 - Occlusion</span></span>

>[!VIDEO https://www.youtube.com/embed/6Xrzh_w-7SE]

<span data-ttu-id="a119c-339">**Obiettivi**</span><span class="sxs-lookup"><span data-stu-id="a119c-339">**Objectives**</span></span>
* <span data-ttu-id="a119c-340">Determinare se un ologrammi sono nascosto dalla trama mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="a119c-340">Determine if a hologram is occluded by the spatial mapping mesh.</span></span>
* <span data-ttu-id="a119c-341">Applicare le tecniche relative all'occlusione diversa per ottenere un divertente effetto.</span><span class="sxs-lookup"><span data-stu-id="a119c-341">Apply different occlusion techniques to achieve a fun effect.</span></span>

<span data-ttu-id="a119c-342">**Istruzioni**</span><span class="sxs-lookup"><span data-stu-id="a119c-342">**Instructions**</span></span>

<span data-ttu-id="a119c-343">In primo luogo, si userà per consentire la mesh mapping spaziale nasconde i colori altri vntana senza occluding del mondo reale:</span><span class="sxs-lookup"><span data-stu-id="a119c-343">First, we are going to allow the spatial mapping mesh to occlude other holograms without occluding the real world:</span></span>
* <span data-ttu-id="a119c-344">Nel **gerarchia** riquadro, seleziona la **SpatialProcessing** oggetto.</span><span class="sxs-lookup"><span data-stu-id="a119c-344">In the **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="a119c-345">Nel **Inspector** panel, trovare il **riprodurre spazio Manager (Script)** componente.</span><span class="sxs-lookup"><span data-stu-id="a119c-345">In the **Inspector** panel, find the **Play Space Manager (Script)** component.</span></span>
* <span data-ttu-id="a119c-346">Fare clic sul cerchio a destra del **materiale secondario** proprietà.</span><span class="sxs-lookup"><span data-stu-id="a119c-346">Click the circle to the right of the **Secondary Material** property.</span></span>
* <span data-ttu-id="a119c-347">Individuare e selezionare il **occlusione** materiale e chiudere la finestra.</span><span class="sxs-lookup"><span data-stu-id="a119c-347">Find and select the **Occlusion** material and close the window.</span></span>

<span data-ttu-id="a119c-348">Successivamente, si intende aggiungere un comportamento speciale a terra, in modo che includa un'evidenziazione blu ogni volta che si viene bloccato da un altro ologrammi (ad esempio il sole) o dalla trama mapping spaziale:</span><span class="sxs-lookup"><span data-stu-id="a119c-348">Next, we are going to add a special behavior to Earth, so that it has a blue highlight whenever it becomes occluded by another hologram (like the sun), or by the spatial mapping mesh:</span></span>
* <span data-ttu-id="a119c-349">Nel **Project** pannello il **Vntana** cartella, espandere il **SolarSystem** oggetto.</span><span class="sxs-lookup"><span data-stu-id="a119c-349">In the **Project** panel, in the **Holograms** folder, expand the **SolarSystem** object.</span></span>
* <span data-ttu-id="a119c-350">Fare clic su **terra**.</span><span class="sxs-lookup"><span data-stu-id="a119c-350">Click on **Earth**.</span></span>
* <span data-ttu-id="a119c-351">Nel **Inspector** panel, individuare il materiale della terra (componente).</span><span class="sxs-lookup"><span data-stu-id="a119c-351">In the **Inspector** panel, find the Earth's material (bottom component).</span></span>
* <span data-ttu-id="a119c-352">Nel **discesa Shader**, modificare lo shader **Custom > OcclusionRim**.</span><span class="sxs-lookup"><span data-stu-id="a119c-352">In the **Shader drop-down**, change the shader to **Custom > OcclusionRim**.</span></span> <span data-ttu-id="a119c-353">Questo verrà eseguito il rendering di un'evidenziazione blu attorno a terra ogni volta che viene bloccato da un altro oggetto.</span><span class="sxs-lookup"><span data-stu-id="a119c-353">This will render a blue highlight around Earth whenever it is occluded by another object.</span></span>

<span data-ttu-id="a119c-354">Infine, si intende abilitare un effetto di visione artificiale x-ray per pianeti nel nostro sistema solare.</span><span class="sxs-lookup"><span data-stu-id="a119c-354">Finally, we are going to enable an x-ray vision effect for planets in our solar system.</span></span> <span data-ttu-id="a119c-355">È necessario modificare **PlanetOcclusion.cs** (disponibile nella cartella Scripts\SolarSystem) per ottenere quanto segue:</span><span class="sxs-lookup"><span data-stu-id="a119c-355">We will need to edit **PlanetOcclusion.cs** (found in the Scripts\SolarSystem folder) in order to achieve the following:</span></span>
1. <span data-ttu-id="a119c-356">Determinare se un pianeta è bloccato dal livello SpatialMapping (chat room mesh e piani).</span><span class="sxs-lookup"><span data-stu-id="a119c-356">Determine if a planet is occluded by the SpatialMapping layer (room meshes and planes).</span></span>
2. <span data-ttu-id="a119c-357">Mostra la rappresentazione di wireframe di un mondo ogni volta che si è bloccato dal livello SpatialMapping.</span><span class="sxs-lookup"><span data-stu-id="a119c-357">Show the wireframe representation of a planet whenever it is occluded by the SpatialMapping layer.</span></span>
3. <span data-ttu-id="a119c-358">Nascondere la rappresentazione di wireframe di un pianeta quando non sono bloccata dal livello SpatialMapping.</span><span class="sxs-lookup"><span data-stu-id="a119c-358">Hide the wireframe representation of a planet when it is not blocked by the SpatialMapping layer.</span></span>

<span data-ttu-id="a119c-359">Seguire l'esercizio di scrittura di codice in PlanetOcclusion.cs o usare la soluzione seguente:</span><span class="sxs-lookup"><span data-stu-id="a119c-359">Follow the coding exercise in PlanetOcclusion.cs, or use the following solution:</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Determines when the occluded version of the planet should be visible.
/// This script allows us to do selective occlusion, so the occlusionObject
/// will only be rendered when a Spatial Mapping surface is occluding the planet,
/// not when another hologram is responsible for the occlusion.
/// </summary>
public class PlanetOcclusion : MonoBehaviour
{
    [Tooltip("Object to display when the planet is occluded.")]
    public GameObject occlusionObject;

    /// <summary>
    /// Points to raycast to when checking for occlusion.
    /// </summary>
    private Vector3[] checkPoints;

    // Use this for initialization
    void Start()
    {
        occlusionObject.SetActive(false);

        // Set the check points to use when testing for occlusion.
        MeshFilter filter = gameObject.GetComponent<MeshFilter>();
        Vector3 extents = filter.mesh.bounds.extents;
        Vector3 center = filter.mesh.bounds.center;
        Vector3 top = new Vector3(center.x, center.y + extents.y, center.z);
        Vector3 left = new Vector3(center.x - extents.x, center.y, center.z);
        Vector3 right = new Vector3(center.x + extents.x, center.y, center.z);
        Vector3 bottom = new Vector3(center.x, center.y - extents.y, center.z);

        checkPoints = new Vector3[] { center, top, left, right, bottom };
    }

    // Update is called once per frame
    void Update()
    {
        /* TODO: 5.a DEVELOPER CODING EXERCISE 5.a */

        // Check to see if any of the planet's boundary points are occluded.
        for (int i = 0; i < checkPoints.Length; i++)
        {
            // 5.a: Convert the current checkPoint to world coordinates.
            // Call gameObject.transform.TransformPoint(checkPoints[i]).
            // Assign the result to a new Vector3 variable called 'checkPt'.
            Vector3 checkPt = gameObject.transform.TransformPoint(checkPoints[i]);

            // 5.a: Call Vector3.Distance() to calculate the distance
            // between the Main Camera's position and 'checkPt'.
            // Assign the result to a new float variable called 'distance'.
            float distance = Vector3.Distance(Camera.main.transform.position, checkPt);

            // 5.a: Take 'checkPt' and subtract the Main Camera's position from it.
            // Assign the result to a new Vector3 variable called 'direction'.
            Vector3 direction = checkPt - Camera.main.transform.position;

            // Used to indicate if the call to Physics.Raycast() was successful.
            bool raycastHit = false;

            // 5.a: Check if the planet is occluded by a spatial mapping surface.
            // Call Physics.Raycast() with the following arguments:
            // - Pass in the Main Camera's position as the origin.
            // - Pass in 'direction' for the direction.
            // - Pass in 'distance' for the maxDistance.
            // - Pass in SpatialMappingManager.Instance.LayerMask as layerMask.
            // Assign the result to 'raycastHit'.
            raycastHit = Physics.Raycast(Camera.main.transform.position, direction, distance, SpatialMappingManager.Instance.LayerMask);

            if (raycastHit)
            {
                // 5.a: Our raycast hit a surface, so the planet is occluded.
                // Set the occlusionObject to active.
                occlusionObject.SetActive(true);

                // At least one point is occluded, so break from the loop.
                break;
            }
            else
            {
                // 5.a: The Raycast did not hit, so the planet is not occluded.
                // Deactivate the occlusionObject.
                occlusionObject.SetActive(false);
            }
        }
    }
}
```

<span data-ttu-id="a119c-360">**Compilare e distribuire**</span><span class="sxs-lookup"><span data-stu-id="a119c-360">**Build and Deploy**</span></span>
* <span data-ttu-id="a119c-361">Compilare e distribuire l'applicazione per HoloLens, come di consueto.</span><span class="sxs-lookup"><span data-stu-id="a119c-361">Build and deploy the application to HoloLens, as usual.</span></span>
* <span data-ttu-id="a119c-362">Attesa per l'analisi e l'elaborazione dei dati spaziali mapping per il completamento (visualizzata linee blu vengono visualizzati sui muri).</span><span class="sxs-lookup"><span data-stu-id="a119c-362">Wait for scanning and processing of the spatial mapping data to be complete (you should see blue lines appear on walls).</span></span>
* <span data-ttu-id="a119c-363">Trovare e selezionare casella proiezione del sistema solare e quindi impostare la casella accanto a una parete o dietro un contatore.</span><span class="sxs-lookup"><span data-stu-id="a119c-363">Find and select the solar system's projection box and then set the box next to a wall or behind a counter.</span></span>
* <span data-ttu-id="a119c-364">È possibile visualizzare occlusione base dietro superfici di eseguire il peering nella casella di poster o proiezione.</span><span class="sxs-lookup"><span data-stu-id="a119c-364">You can view basic occlusion by hiding behind surfaces to peer at the poster or projection box.</span></span>
* <span data-ttu-id="a119c-365">Cercare la terra, dovrebbe esserci un effetto di evidenziazione blu ogni volta che diventa protetto da un altro ologrammi o area.</span><span class="sxs-lookup"><span data-stu-id="a119c-365">Look for the Earth, there should be a blue highlight effect whenever it goes behind another hologram or surface.</span></span>
* <span data-ttu-id="a119c-366">Guarda i pianeti spostata dietro la parete o altre superfici nella chat room.</span><span class="sxs-lookup"><span data-stu-id="a119c-366">Watch as the planets move behind the wall or other surfaces in the room.</span></span> <span data-ttu-id="a119c-367">È ora hanno raggi x ed è possibile visualizzare gli scheletri di wireframe.</span><span class="sxs-lookup"><span data-stu-id="a119c-367">You now have x-ray vision and can see their wireframe skeletons!</span></span>

## <a name="the-end"></a><span data-ttu-id="a119c-368">La fine</span><span class="sxs-lookup"><span data-stu-id="a119c-368">The End</span></span>

<span data-ttu-id="a119c-369">La procedura è stata completata.</span><span class="sxs-lookup"><span data-stu-id="a119c-369">Congratulations!</span></span> <span data-ttu-id="a119c-370">Sono stati completati **SIG spaziali 230: Mapping spaziale**.</span><span class="sxs-lookup"><span data-stu-id="a119c-370">You have now completed **MR Spatial 230: Spatial mapping**.</span></span>
* <span data-ttu-id="a119c-371">Si sa come analizzare i dati di ambiente e carico mapping spaziale a Unity.</span><span class="sxs-lookup"><span data-stu-id="a119c-371">You know how to scan your environment and load spatial mapping data to Unity.</span></span>
* <span data-ttu-id="a119c-372">Comprendere le nozioni di base di shader e come materiali possono essere usati per visualizzare nuovamente il mondo.</span><span class="sxs-lookup"><span data-stu-id="a119c-372">You understand the basics of shaders and how materials can be used to re-visualize the world.</span></span>
* <span data-ttu-id="a119c-373">Si è appreso di nuove tecniche di elaborazione per l'individuazione di piani e rimozione triangoli da una rete mesh.</span><span class="sxs-lookup"><span data-stu-id="a119c-373">You learned of new processing techniques for finding planes and removing triangles from a mesh.</span></span>
* <span data-ttu-id="a119c-374">È stato possibile spostare e posizionare vntana nelle aree che non aveva senso.</span><span class="sxs-lookup"><span data-stu-id="a119c-374">You were able to move and place holograms on surfaces that made sense.</span></span>
* <span data-ttu-id="a119c-375">Si è verificato tecniche diverse relative all'occlusione e sfruttate le potenzialità di raggi x!</span><span class="sxs-lookup"><span data-stu-id="a119c-375">You experienced different occlusion techniques and harnessed the power of x-ray vision!</span></span>

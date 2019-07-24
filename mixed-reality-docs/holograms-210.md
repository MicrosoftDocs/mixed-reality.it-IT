---
title: Input MR 210-sguardo
description: Seguire questa procedura dettagliata di codifica usando Unity, Visual Studio e HoloLens per informazioni dettagliate sui concetti relativi a sguardi.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academy, esercitazione, sguardo
ms.openlocfilehash: 076314389ec5ed70347c26d50c6a993f55da0758
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993550"
---
>[!NOTE]
><span data-ttu-id="6e45a-104">Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.</span><span class="sxs-lookup"><span data-stu-id="6e45a-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="6e45a-105">Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.</span><span class="sxs-lookup"><span data-stu-id="6e45a-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="6e45a-106">Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="6e45a-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="6e45a-107">Verranno mantenuti per continuare a usare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="6e45a-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="6e45a-108">In futuro sarà disponibile una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="6e45a-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="6e45a-109">Questo avviso verrà aggiornato con un collegamento a queste esercitazioni quando vengono pubblicate.</span><span class="sxs-lookup"><span data-stu-id="6e45a-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-input-210-gaze"></a><span data-ttu-id="6e45a-110">Input MR 210: Sguardo fisso</span><span class="sxs-lookup"><span data-stu-id="6e45a-110">MR Input 210: Gaze</span></span>

<span data-ttu-id="6e45a-111">Lo [sguardo](gaze.md) è la prima forma di input e rivela le finalità e la consapevolezza dell'utente.</span><span class="sxs-lookup"><span data-stu-id="6e45a-111">[Gaze](gaze.md) is the first form of input and reveals the user's intent and awareness.</span></span> <span data-ttu-id="6e45a-112">MR input 210 (noto anche come Project Explorer) è un approfondimento dei concetti correlati a sguardi per la realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="6e45a-112">MR Input 210 (aka Project Explorer) is a deep dive into gaze-related concepts for Windows Mixed Reality.</span></span> <span data-ttu-id="6e45a-113">Verrà aggiunta la consapevolezza contestuale al cursore e agli ologrammi, sfruttando appieno i vantaggi offerti dall'app per quanto riguarda lo sguardo dell'utente.</span><span class="sxs-lookup"><span data-stu-id="6e45a-113">We will be adding contextual awareness to our cursor and holograms, taking full advantage of what your app knows about the user's gaze.</span></span>

>[!VIDEO https://www.youtube.com/embed/yKAttGduVp0]

<span data-ttu-id="6e45a-114">Qui è disponibile un astronauta che consente di apprendere i concetti di sguardi.</span><span class="sxs-lookup"><span data-stu-id="6e45a-114">We have a friendly astronaut here to help you learn gaze concepts.</span></span> <span data-ttu-id="6e45a-115">In [Mr nozioni di base 101](holograms-101.md), abbiamo un semplice cursore che ha subito seguito lo sguardo.</span><span class="sxs-lookup"><span data-stu-id="6e45a-115">In [MR Basics 101](holograms-101.md), we had a simple cursor that just followed your gaze.</span></span> <span data-ttu-id="6e45a-116">Oggi stiamo muovendo un passaggio oltre il semplice cursore:</span><span class="sxs-lookup"><span data-stu-id="6e45a-116">Today we're moving a step beyond the simple cursor:</span></span>

* <span data-ttu-id="6e45a-117">Il cursore e i nostri ologrammi sono consapevoli del fatto che entrambi cambieranno in base alla posizione dell'utente o alla posizione in cui l'utente *non* è in Cerca.</span><span class="sxs-lookup"><span data-stu-id="6e45a-117">We're making the cursor and our holograms gaze-aware: both will change based on where the user is looking - or where the user is *not* looking.</span></span> <span data-ttu-id="6e45a-118">Che li rende compatibili con il contesto.</span><span class="sxs-lookup"><span data-stu-id="6e45a-118">This makes them context-aware.</span></span>
* <span data-ttu-id="6e45a-119">Si aggiungeranno commenti e suggerimenti al cursore e agli ologrammi per fornire all'utente un maggior contesto sugli elementi di destinazione.</span><span class="sxs-lookup"><span data-stu-id="6e45a-119">We will add feedback to our cursor and holograms to give the user more context on what is being targeted.</span></span> <span data-ttu-id="6e45a-120">Questo feedback può essere costituito da audio e oggetti visivi.</span><span class="sxs-lookup"><span data-stu-id="6e45a-120">This feedback can be audio and visual.</span></span>
* <span data-ttu-id="6e45a-121">Verranno illustrate le tecniche di destinazione per aiutare gli utenti a raggiungere obiettivi più piccoli.</span><span class="sxs-lookup"><span data-stu-id="6e45a-121">We'll show you targeting techniques to help users hit smaller targets.</span></span>
* <span data-ttu-id="6e45a-122">Verrà illustrato come attirare l'attenzione dell'utente sugli ologrammi con un indicatore direzionale.</span><span class="sxs-lookup"><span data-stu-id="6e45a-122">We'll show you how to draw the user's attention to your holograms with a directional indicator.</span></span>
* <span data-ttu-id="6e45a-123">Ti insegneremo le tecniche per portare gli ologrammi all'utente mentre si sposta in tutto il mondo.</span><span class="sxs-lookup"><span data-stu-id="6e45a-123">We'll teach you techniques to take your holograms with the user as she moves around in your world.</span></span>

>[!IMPORTANT]
><span data-ttu-id="6e45a-124">I video incorporati in ognuno dei capitoli seguenti sono stati registrati usando una versione precedente di Unity e il Toolkit di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="6e45a-124">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="6e45a-125">Sebbene le istruzioni dettagliate siano accurate e aggiornate, è possibile visualizzare gli script e gli oggetti visivi nei video corrispondenti non aggiornati.</span><span class="sxs-lookup"><span data-stu-id="6e45a-125">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="6e45a-126">I video rimangono inclusi per i posteri e perché i concetti trattati sono ancora validi.</span><span class="sxs-lookup"><span data-stu-id="6e45a-126">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="6e45a-127">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="6e45a-127">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="6e45a-128">Corso</span><span class="sxs-lookup"><span data-stu-id="6e45a-128">Course</span></span></th><th style="width:150px"> <span data-ttu-id="6e45a-129"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="6e45a-129"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="6e45a-130"><a href="immersive-headset-hardware-details.md">Visori VR immersive</a></span><span class="sxs-lookup"><span data-stu-id="6e45a-130"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="6e45a-131">Input MR 210: Sguardo fisso</span><span class="sxs-lookup"><span data-stu-id="6e45a-131">MR Input 210: Gaze</span></span></td><td style="text-align: center;"> <span data-ttu-id="6e45a-132">✔️</span><span class="sxs-lookup"><span data-stu-id="6e45a-132">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="6e45a-133">✔️</span><span class="sxs-lookup"><span data-stu-id="6e45a-133">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="6e45a-134">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="6e45a-134">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="6e45a-135">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="6e45a-135">Prerequisites</span></span>

* <span data-ttu-id="6e45a-136">Un PC Windows 10 configurato con gli [strumenti corretti installati](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="6e45a-136">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="6e45a-137">Alcune funzionalità C# di programmazione di base.</span><span class="sxs-lookup"><span data-stu-id="6e45a-137">Some basic C# programming ability.</span></span>
* <span data-ttu-id="6e45a-138">Sono state completate le nozioni di [base 101](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="6e45a-138">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="6e45a-139">Un dispositivo HoloLens [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="6e45a-139">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="6e45a-140">File di progetto</span><span class="sxs-lookup"><span data-stu-id="6e45a-140">Project files</span></span>

* <span data-ttu-id="6e45a-141">Scaricare i [file](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) richiesti dal progetto.</span><span class="sxs-lookup"><span data-stu-id="6e45a-141">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) required by the project.</span></span><span data-ttu-id="6e45a-142"> Richiede Unity 2017,2 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="6e45a-142"> Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="6e45a-143">Annullare l'archiviazione dei file sul desktop o in un'altra posizione facile da raggiungere.</span><span class="sxs-lookup"><span data-stu-id="6e45a-143">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="6e45a-144">Se si vuole esaminare il codice sorgente prima del download, è [disponibile in GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze).</span><span class="sxs-lookup"><span data-stu-id="6e45a-144">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="6e45a-145">Errori e note</span><span class="sxs-lookup"><span data-stu-id="6e45a-145">Errata and Notes</span></span>

* <span data-ttu-id="6e45a-146">In Visual Studio, "Just My Code" deve essere disabilitato (deselezionato) in strumenti-Opzioni >-> debug per raggiungere i punti di interruzione nel codice.</span><span class="sxs-lookup"><span data-stu-id="6e45a-146">In Visual Studio, "Just My Code" needs to be disabled (unchecked) under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="6e45a-147">Capitolo 1-installazione di Unity</span><span class="sxs-lookup"><span data-stu-id="6e45a-147">Chapter 1 - Unity Setup</span></span>

>[!VIDEO https://www.youtube.com/embed/_Ccn6riQ6vU]

### <a name="objectives"></a><span data-ttu-id="6e45a-148">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="6e45a-148">Objectives</span></span>

* <span data-ttu-id="6e45a-149">Ottimizzare Unity per lo sviluppo di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="6e45a-149">Optimize Unity for HoloLens development.</span></span>
* <span data-ttu-id="6e45a-150">Importare gli asset e configurare la scena.</span><span class="sxs-lookup"><span data-stu-id="6e45a-150">Import assets and setup the scene.</span></span>
* <span data-ttu-id="6e45a-151">Visualizzare l'astronauta nella HoloLens.</span><span class="sxs-lookup"><span data-stu-id="6e45a-151">View the astronaut in the HoloLens.</span></span>

### <a name="instructions"></a><span data-ttu-id="6e45a-152">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="6e45a-152">Instructions</span></span>

1. <span data-ttu-id="6e45a-153">Avvia Unity.</span><span class="sxs-lookup"><span data-stu-id="6e45a-153">Start Unity.</span></span>
2. <span data-ttu-id="6e45a-154">Selezionare **nuovo progetto**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-154">Select **New Project**.</span></span>
3. <span data-ttu-id="6e45a-155">Denominare il progetto **ModelExplorer**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-155">Name the project **ModelExplorer**.</span></span>
4. <span data-ttu-id="6e45a-156">Immettere location come cartella degli **sguardi** precedentemente non archiviata.</span><span class="sxs-lookup"><span data-stu-id="6e45a-156">Enter location as the **Gaze** folder you previously un-archived.</span></span>
5. <span data-ttu-id="6e45a-157">Assicurati che il progetto sia impostato su **3D**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-157">Make sure the project is set to **3D**.</span></span>
6. <span data-ttu-id="6e45a-158">Fai clic su **Create Project** (Crea progetto).</span><span class="sxs-lookup"><span data-stu-id="6e45a-158">Click **Create Project**.</span></span>

### <a name="unity-settings-for-hololens"></a><span data-ttu-id="6e45a-159">Impostazioni Unity per HoloLens</span><span class="sxs-lookup"><span data-stu-id="6e45a-159">Unity settings for HoloLens</span></span>

<span data-ttu-id="6e45a-160">È necessario informare Unity che l'app che si sta tentando di esportare deve creare una [visualizzazione immersiva](app-views.md) anziché una visualizzazione 2D.</span><span class="sxs-lookup"><span data-stu-id="6e45a-160">We need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="6e45a-161">Questa operazione viene eseguita aggiungendo HoloLens come dispositivo di realtà virtuale.</span><span class="sxs-lookup"><span data-stu-id="6e45a-161">We do that by adding HoloLens as a virtual reality device.</span></span>

1. <span data-ttu-id="6e45a-162">Passare a **Edit > Settings Project > Player**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-162">Go to **Edit > Project Settings > Player**.</span></span>
2. <span data-ttu-id="6e45a-163">Nel **pannello Inspector** per le impostazioni del lettore selezionare l'icona di **Windows Store** .</span><span class="sxs-lookup"><span data-stu-id="6e45a-163">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="6e45a-164">Espandere il gruppo di **Impostazioni XR** .</span><span class="sxs-lookup"><span data-stu-id="6e45a-164">Expand the **XR Settings** group.</span></span>
4. <span data-ttu-id="6e45a-165">Nella sezione **rendering** selezionare la casella di controllo **realtà virtuale supportata** per aggiungere un nuovo elenco **SDK di realtà virtuale** .</span><span class="sxs-lookup"><span data-stu-id="6e45a-165">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality SDKs** list.</span></span>
5. <span data-ttu-id="6e45a-166">Verificare che l'opzione **realtà mista di Windows** sia presente nell'elenco.</span><span class="sxs-lookup"><span data-stu-id="6e45a-166">Verify that **Windows Mixed Reality** appears in the list.</span></span> <span data-ttu-id="6e45a-167">In caso contrario, selezionare **+** il pulsante nella parte inferiore dell'elenco e scegliere **Windows olografico**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-167">If not, select the **+** button at the bottom of the list and choose **Windows Holographic**.</span></span>

<span data-ttu-id="6e45a-168">Successivamente, è necessario impostare il back-end di scripting su .NET.</span><span class="sxs-lookup"><span data-stu-id="6e45a-168">Next, we need to set our scripting backend to .NET.</span></span>

1. <span data-ttu-id="6e45a-169">Passare a **Edit > Settings (Impostazioni progetto) > Player** (è possibile continuare a eseguire questa operazione dal passaggio precedente).</span><span class="sxs-lookup"><span data-stu-id="6e45a-169">Go to **Edit > Project Settings > Player** (you may still have this up from the previous step).</span></span>
2. <span data-ttu-id="6e45a-170">Nel **pannello Inspector** per le impostazioni del lettore selezionare l'icona di **Windows Store** .</span><span class="sxs-lookup"><span data-stu-id="6e45a-170">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="6e45a-171">Nella sezione **altre impostazioni** di configurazione, assicurarsi che **lo scripting backend** sia impostato su **.NET** .</span><span class="sxs-lookup"><span data-stu-id="6e45a-171">In the **Other Settings** Configuration section, make sure that **Scripting Backend** is set to **.NET**</span></span>

<span data-ttu-id="6e45a-172">Infine, verranno aggiornate le impostazioni di qualità per ottenere prestazioni rapide su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="6e45a-172">Finally, we'll update our quality settings to achieve a fast performance on HoloLens.</span></span>

1. <span data-ttu-id="6e45a-173">Passare a **modifica > impostazioni progetto > qualità**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-173">Go to **Edit > Project Settings > Quality**.</span></span>
2. <span data-ttu-id="6e45a-174">Fare clic sulla freccia rivolta verso il basso nella riga **predefinita** sotto l'icona di Windows Store.</span><span class="sxs-lookup"><span data-stu-id="6e45a-174">Click on downward pointing arrow in the **Default** row under the Windows Store icon.</span></span>
3. <span data-ttu-id="6e45a-175">Selezionare **molto basso** per le **app di Windows Store**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-175">Select **Very Low** for **Windows Store Apps**.</span></span>

### <a name="import-project-assets"></a><span data-ttu-id="6e45a-176">Importa asset progetto</span><span class="sxs-lookup"><span data-stu-id="6e45a-176">Import project assets</span></span>

1. <span data-ttu-id="6e45a-177">Fare clic con  il pulsante destro del mouse sulla cartella assets nel pannello **Project** .</span><span class="sxs-lookup"><span data-stu-id="6e45a-177">Right click the **Assets** folder in the **Project** panel.</span></span>
2. <span data-ttu-id="6e45a-178">Fare clic su **Importa pacchetto > pacchetto personalizzato**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-178">Click on **Import Package > Custom Package**.</span></span>
3. <span data-ttu-id="6e45a-179">Individuare i file di progetto scaricati e fare clic su **ModelExplorer. file unitypackage Tools**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-179">Navigate to the project files you downloaded and click on **ModelExplorer.unitypackage**.</span></span>
4. <span data-ttu-id="6e45a-180">Fare clic su **Apri**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-180">Click **Open**.</span></span>
5. <span data-ttu-id="6e45a-181">Al termine del caricamento del pacchetto, fare clic sul pulsante **Importa** .</span><span class="sxs-lookup"><span data-stu-id="6e45a-181">After the package loads, click on the **Import** button.</span></span>

### <a name="setup-the-scene"></a><span data-ttu-id="6e45a-182">Configurare la scena</span><span class="sxs-lookup"><span data-stu-id="6e45a-182">Setup the scene</span></span>

1. <span data-ttu-id="6e45a-183">Nella gerarchia eliminare la **fotocamera principale**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-183">In the Hierarchy, delete the **Main Camera**.</span></span>
2. <span data-ttu-id="6e45a-184">Nella cartella **HoloToolkit** aprire la cartella di **input** , quindi aprire la cartella  prefabbricates.</span><span class="sxs-lookup"><span data-stu-id="6e45a-184">In the **HoloToolkit** folder, open the **Input** folder, then open the **Prefabs** folder.</span></span>
3. <span data-ttu-id="6e45a-185">Trascinare il prefabbricato **MixedRealityCameraParent** dalla cartella  prefabbricates alla **gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-185">Drag and drop the **MixedRealityCameraParent** prefab from the **Prefabs** folder into the **Hierarchy**.</span></span>
4. <span data-ttu-id="6e45a-186">Fare clic con il pulsante destro del mouse sulla **luce direzionale** nella gerarchia e scegliere **Elimina**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-186">Right-click the **Directional Light** in the Hierarchy and select **Delete**.</span></span>
5. <span data-ttu-id="6e45a-187">Nella cartella **ologrammi** trascinare e rilasciare gli asset seguenti nella radice della **gerarchia**:</span><span class="sxs-lookup"><span data-stu-id="6e45a-187">In the **Holograms** folder, drag and drop the following assets into the root of the **Hierarchy**:</span></span>
    * <span data-ttu-id="6e45a-188">**AstroMan**</span><span class="sxs-lookup"><span data-stu-id="6e45a-188">**AstroMan**</span></span>
    * <span data-ttu-id="6e45a-189">**Luci**</span><span class="sxs-lookup"><span data-stu-id="6e45a-189">**Lights**</span></span>
    * <span data-ttu-id="6e45a-190">**SpaceAudioSource**</span><span class="sxs-lookup"><span data-stu-id="6e45a-190">**SpaceAudioSource**</span></span>
    * <span data-ttu-id="6e45a-191">**SpaceBackground**</span><span class="sxs-lookup"><span data-stu-id="6e45a-191">**SpaceBackground**</span></span>
6. <span data-ttu-id="6e45a-192">Avviare la **modalità di riproduzione** ▶ per visualizzare l'astronauta.</span><span class="sxs-lookup"><span data-stu-id="6e45a-192">Start **Play Mode** ▶ to view the astronaut.</span></span>
7. <span data-ttu-id="6e45a-193">Fare clic su **modalità** riproduci ▶ per **arrestare**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-193">Click **Play Mode** ▶ again to **Stop**.</span></span>
8. <span data-ttu-id="6e45a-194">Nella cartella **ologrammi** individuare l'asset **fitbox** e trascinarlo nella radice della **gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-194">In the **Holograms** folder, find the **Fitbox** asset and drag it to the root of the **Hierarchy**.</span></span>
9. <span data-ttu-id="6e45a-195">Selezionare **fitbox** nel pannello **gerarchia** .</span><span class="sxs-lookup"><span data-stu-id="6e45a-195">Select the **Fitbox** in the **Hierarchy** panel.</span></span>
10. <span data-ttu-id="6e45a-196">Trascinare la  raccolta astror dalla **gerarchia** alla proprietà della **raccolta ologramma** di fitbox nel pannello **Inspector** .</span><span class="sxs-lookup"><span data-stu-id="6e45a-196">Drag the **AstroMan** collection from the **Hierarchy** to the **Hologram Collection** property of the Fitbox in the **Inspector** panel.</span></span>

### <a name="save-the-project"></a><span data-ttu-id="6e45a-197">Salvare il progetto</span><span class="sxs-lookup"><span data-stu-id="6e45a-197">Save the project</span></span>

1. <span data-ttu-id="6e45a-198">Salvare la nuova scena: **File > Salva scena come**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-198">Save the new scene: **File > Save Scene As**.</span></span>
2. <span data-ttu-id="6e45a-199">Fare clic su **nuova cartella** e denominare la cartella **Scenes**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-199">Click **New Folder** and name the folder **Scenes**.</span></span>
3. <span data-ttu-id="6e45a-200">Denominare il file "**ModelExplorer**" e salvarlo nella cartella **Scenes** .</span><span class="sxs-lookup"><span data-stu-id="6e45a-200">Name the file “**ModelExplorer**” and save it in the **Scenes** folder.</span></span>

### <a name="build-the-project"></a><span data-ttu-id="6e45a-201">Compilare il progetto</span><span class="sxs-lookup"><span data-stu-id="6e45a-201">Build the project</span></span>

1. <span data-ttu-id="6e45a-202">In Unity selezionare **File > impostazioni di compilazione**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-202">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="6e45a-203">Fare clic su **Aggiungi scene aperte** per aggiungere la scena.</span><span class="sxs-lookup"><span data-stu-id="6e45a-203">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="6e45a-204">Selezionare **piattaforma UWP (Universal Windows Platform)** nell'elenco **piattaforma** e fare clic su **Cambia piattaforma**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-204">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="6e45a-205">Se si sta sviluppando in modo specifico per HoloLens, impostare **dispositivo di destinazione** su **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-205">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="6e45a-206">In caso contrario, lasciarlo in **qualsiasi dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-206">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="6e45a-207">Verificare che **tipo di compilazione** sia impostato su **D3D** e che l' **SDK** sia impostato su **installato più recente** (che deve essere SDK 16299 o versione successiva).</span><span class="sxs-lookup"><span data-stu-id="6e45a-207">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="6e45a-208">Fai clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-208">Click **Build**.</span></span>
7. <span data-ttu-id="6e45a-209">Creare una **nuova cartella** denominata "app".</span><span class="sxs-lookup"><span data-stu-id="6e45a-209">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="6e45a-210">Fare clic sulla cartella dell' **app** .</span><span class="sxs-lookup"><span data-stu-id="6e45a-210">Single click the **App** folder.</span></span>
9. <span data-ttu-id="6e45a-211">Premere **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-211">Press **Select Folder**.</span></span>

<span data-ttu-id="6e45a-212">Quando si esegue Unity, viene visualizzata una finestra Esplora file.</span><span class="sxs-lookup"><span data-stu-id="6e45a-212">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="6e45a-213">Aprire la cartella dell' **app** .</span><span class="sxs-lookup"><span data-stu-id="6e45a-213">Open the **App** folder.</span></span>
2. <span data-ttu-id="6e45a-214">Aprire la **soluzione ModelExplorer di Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-214">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="6e45a-215">Se si esegue la distribuzione in HoloLens:</span><span class="sxs-lookup"><span data-stu-id="6e45a-215">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="6e45a-216">Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione da debug a **Release** e da ARM a **x86**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-216">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="6e45a-217">Fare clic sulla freccia a discesa accanto al pulsante computer locale e selezionare **computer remoto**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-217">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="6e45a-218">Immettere **l'indirizzo IP del dispositivo HoloLens** e impostare la modalità di autenticazione su **universale (protocollo non crittografato)** .</span><span class="sxs-lookup"><span data-stu-id="6e45a-218">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="6e45a-219">Fare clic su **Seleziona**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-219">Click **Select**.</span></span> <span data-ttu-id="6e45a-220">Se non si conosce l'indirizzo IP del dispositivo, vedere **impostazioni > rete & Internet > opzioni avanzate**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-220">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="6e45a-221">Nella barra dei menu superiore fare clic su **debug-> avvia senza eseguire debug** o premere **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-221">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="6e45a-222">Se questa è la prima volta che si esegue la distribuzione nel dispositivo, sarà necessario associarla a [Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span><span class="sxs-lookup"><span data-stu-id="6e45a-222">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
5. <span data-ttu-id="6e45a-223">Quando l'app è stata distribuita, chiudere il **fitbox** con un **movimento di selezione**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-223">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="6e45a-224">Se si esegue la distribuzione in un auricolare immersivo:</span><span class="sxs-lookup"><span data-stu-id="6e45a-224">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="6e45a-225">Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione da debug a **Release** e da ARM a **x64**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-225">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="6e45a-226">Verificare che la destinazione di distribuzione sia impostata su **computer locale**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-226">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="6e45a-227">Nella barra dei menu superiore fare clic su **debug-> avvia senza eseguire debug** o premere **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-227">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="6e45a-228">Quando l'app è stata distribuita, chiudere il **fitbox** estraendo il trigger in un controller di movimento.</span><span class="sxs-lookup"><span data-stu-id="6e45a-228">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

## <a name="chapter-2---cursor-and-target-feedback"></a><span data-ttu-id="6e45a-229">Capitolo 2-feedback del cursore e della destinazione</span><span class="sxs-lookup"><span data-stu-id="6e45a-229">Chapter 2 - Cursor and target feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/S24u0V_T7ZI]

### <a name="objectives"></a><span data-ttu-id="6e45a-230">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="6e45a-230">Objectives</span></span>

* <span data-ttu-id="6e45a-231">Comportamento e progettazione visivi del cursore.</span><span class="sxs-lookup"><span data-stu-id="6e45a-231">Cursor visual design and behavior.</span></span>
* <span data-ttu-id="6e45a-232">Feedback del cursore basato su sguardi.</span><span class="sxs-lookup"><span data-stu-id="6e45a-232">Gaze-based cursor feedback.</span></span>
* <span data-ttu-id="6e45a-233">Feedback dell'ologramma basato su sguardi.</span><span class="sxs-lookup"><span data-stu-id="6e45a-233">Gaze-based hologram feedback.</span></span>

<span data-ttu-id="6e45a-234">Il nostro lavoro verrà basato sui principi di progettazione dei cursori, vale a dire:</span><span class="sxs-lookup"><span data-stu-id="6e45a-234">We're going to base our work on some cursor design principles, namely:</span></span>

* <span data-ttu-id="6e45a-235">Il cursore è sempre presente.</span><span class="sxs-lookup"><span data-stu-id="6e45a-235">The cursor is always present.</span></span>
* <span data-ttu-id="6e45a-236">Non lasciare il cursore troppo piccolo o grande.</span><span class="sxs-lookup"><span data-stu-id="6e45a-236">Don't let the cursor get too small or big.</span></span>
* <span data-ttu-id="6e45a-237">Evitare di ostacolare il contenuto.</span><span class="sxs-lookup"><span data-stu-id="6e45a-237">Avoid obstructing content.</span></span>

### <a name="instructions"></a><span data-ttu-id="6e45a-238">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="6e45a-238">Instructions</span></span>

1. <span data-ttu-id="6e45a-239">Nella cartella **HoloToolkit\Input\Prefabs** trovare l'asset **InputManager** .</span><span class="sxs-lookup"><span data-stu-id="6e45a-239">In the **HoloToolkit\Input\Prefabs** folder, find the **InputManager** asset.</span></span>
2. <span data-ttu-id="6e45a-240">Trascinare e rilasciare **InputManager** nella **gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-240">Drag and drop the **InputManager** onto the **Hierarchy**.</span></span>
3. <span data-ttu-id="6e45a-241">Nella cartella **HoloToolkit\Input\Prefabs** trovare il **cursore** asset.</span><span class="sxs-lookup"><span data-stu-id="6e45a-241">In the **HoloToolkit\Input\Prefabs** folder, find the **Cursor** asset.</span></span>
4. <span data-ttu-id="6e45a-242">Trascinare e rilasciare il **cursore** nella **gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-242">Drag and drop the **Cursor** onto the **Hierarchy**.</span></span>
5. <span data-ttu-id="6e45a-243">Consente di selezionare l'oggetto **InputManager** nella **gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-243">Select the **InputManager** object in the **Hierarchy**.</span></span>
6. <span data-ttu-id="6e45a-244">Trascinare l'oggetto **cursore** dalla **gerarchia** nel campo **cursore** di **SimpleSinglePointerSelector**di InputManager, nella parte inferiore del **controllo**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-244">Drag the **Cursor** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector**'s **Cursor** field, at the bottom of the **Inspector**.</span></span>

![Configurazione semplice del selettore con puntatore singolo](images/holograms210-ssps.png)

### <a name="build-and-deploy"></a><span data-ttu-id="6e45a-246">Compilazione e distribuzione</span><span class="sxs-lookup"><span data-stu-id="6e45a-246">Build and Deploy</span></span>

1. <span data-ttu-id="6e45a-247">Ricompilare l'app da **File > impostazioni di compilazione**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-247">Rebuild the app from **File > Build Settings**.</span></span>
2. <span data-ttu-id="6e45a-248">Aprire la **cartella dell'app**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-248">Open the **App folder**.</span></span>
3. <span data-ttu-id="6e45a-249">Aprire la **soluzione ModelExplorer di Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-249">Open the **ModelExplorer Visual Studio Solution**.</span></span>
4. <span data-ttu-id="6e45a-250">Fare clic su **debug-> avvia senza eseguire debug** o premere **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-250">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
5. <span data-ttu-id="6e45a-251">Osservare il modo in cui viene disegnato il cursore e il modo in cui cambia aspetto se tocca un ologramma.</span><span class="sxs-lookup"><span data-stu-id="6e45a-251">Observe how the cursor is drawn, and how it changes appearance if it is touching a hologram.</span></span>

### <a name="instructions"></a><span data-ttu-id="6e45a-252">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="6e45a-252">Instructions</span></span>

1. <span data-ttu-id="6e45a-253">Nel pannello **gerarchia** espandere l'oggetto ->Astron**GEO_G**->**Back_Center** .</span><span class="sxs-lookup"><span data-stu-id="6e45a-253">In the **Hierarchy** panel, expand the **AstroMan**->**GEO_G**->**Back_Center** object.</span></span>
2. <span data-ttu-id="6e45a-254">Fare doppio clic su **Interactible.cs** per aprirlo in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6e45a-254">Double click on **Interactible.cs** to open it in Visual Studio.</span></span>
3. <span data-ttu-id="6e45a-255">Rimuovere il commento dalle righe nei callback **IFocusable. OnFocusEnter ()** e **IFocusable. OnFocusExit ()** in **Interactible.cs**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-255">Uncomment the lines in the **IFocusable.OnFocusEnter()** and **IFocusable.OnFocusExit()** callbacks in **Interactible.cs**.</span></span> <span data-ttu-id="6e45a-256">Questi vengono chiamati dal InputManager del Toolkit di realtà mista quando lo stato attivo (tramite sguardo o con il puntatore del controller) entra e esce dall'oggetto Collider di GameObject specifico.</span><span class="sxs-lookup"><span data-stu-id="6e45a-256">These are called by the Mixed Reality Toolkit's InputManager when focus (either by gaze or by controller pointing) enters and exits the specific GameObject's collider.</span></span>

```cs
/* TODO: DEVELOPER CODING EXERCISE 2.d */

void IFocusable.OnFocusEnter()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to highlight the material when gaze enters.
        defaultMaterials[i].EnableKeyword("_ENVIRONMENT_COLORING");
    }
}

void IFocusable.OnFocusExit()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to remove highlight on material when gaze exits.
        defaultMaterials[i].DisableKeyword("_ENVIRONMENT_COLORING");
    }
}
```

>[!NOTE]
><span data-ttu-id="6e45a-257">`EnableKeyword` Usiamo e `DisableKeyword` versioni successive.</span><span class="sxs-lookup"><span data-stu-id="6e45a-257">We use `EnableKeyword` and `DisableKeyword` above.</span></span> <span data-ttu-id="6e45a-258">Per usarle nella propria app con lo shader standard del Toolkit, è necessario seguire le [linee guida di Unity per accedere ai materiali tramite script](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html).</span><span class="sxs-lookup"><span data-stu-id="6e45a-258">In order to make use of these in your own app with the Toolkit's Standard shader, you'll need to follow the [Unity guidelines for accessing materials via script](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html).</span></span> <span data-ttu-id="6e45a-259">In questo caso sono già state incluse le [tre varianti del materiale evidenziato](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) necessario nella cartella Resources (ricerca dei tre materiali con evidenziazione nel nome).</span><span class="sxs-lookup"><span data-stu-id="6e45a-259">In this case, we've already included the [three variants of highlighted material](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) needed in the Resources folder (look for the three materials with highlight in the name).</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="6e45a-260">Compilazione e distribuzione</span><span class="sxs-lookup"><span data-stu-id="6e45a-260">Build and Deploy</span></span>

1. <span data-ttu-id="6e45a-261">Come in precedenza, compilare il progetto e distribuirlo in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="6e45a-261">As before, build the project and deploy to the HoloLens.</span></span>
2. <span data-ttu-id="6e45a-262">Osservare cosa accade quando lo sguardo è mirato a un oggetto e in caso contrario.</span><span class="sxs-lookup"><span data-stu-id="6e45a-262">Observe what happens when the gaze is aimed at an object and when it's not.</span></span>

## <a name="chapter-3---targeting-techniques"></a><span data-ttu-id="6e45a-263">Capitolo 3-tecniche di targeting</span><span class="sxs-lookup"><span data-stu-id="6e45a-263">Chapter 3 - Targeting Techniques</span></span>

>[!VIDEO https://www.youtube.com/embed/TFnuLva4VJ0]

### <a name="objectives"></a><span data-ttu-id="6e45a-264">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="6e45a-264">Objectives</span></span>

* <span data-ttu-id="6e45a-265">Semplificare la destinazione degli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="6e45a-265">Make it easier to target holograms.</span></span>
* <span data-ttu-id="6e45a-266">Stabilizzare i movimenti della testa naturale.</span><span class="sxs-lookup"><span data-stu-id="6e45a-266">Stabilize natural head movements.</span></span>

### <a name="instructions"></a><span data-ttu-id="6e45a-267">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="6e45a-267">Instructions</span></span>

1. <span data-ttu-id="6e45a-268">Nel pannello **gerarchia** selezionare l'oggetto **InputManager** .</span><span class="sxs-lookup"><span data-stu-id="6e45a-268">In the **Hierarchy** panel, select the **InputManager** object.</span></span>
2. <span data-ttu-id="6e45a-269">Nel pannello **Inspector** trovare lo script stabilizzatore dello **sguardo** .</span><span class="sxs-lookup"><span data-stu-id="6e45a-269">In the **Inspector** panel, find the **Gaze Stabilizer** script.</span></span> <span data-ttu-id="6e45a-270">Fare clic su di esso per aprirlo in Visual Studio, se si vuole dare un'occhiata.</span><span class="sxs-lookup"><span data-stu-id="6e45a-270">Click it to open in Visual Studio, if you want to take a look.</span></span>
    * <span data-ttu-id="6e45a-271">Questo script scorre gli esempi di dati di Raycast e consente di stabilizzare lo sguardo dell'utente per la destinazione della precisione.</span><span class="sxs-lookup"><span data-stu-id="6e45a-271">This script iterates over samples of Raycast data and helps stabilize the user's gaze for precision targeting.</span></span>
3. <span data-ttu-id="6e45a-272">Nel **controllo**è possibile modificare il valore dei **campioni di stabilità archiviati** .</span><span class="sxs-lookup"><span data-stu-id="6e45a-272">In the **Inspector**, you can edit the **Stored Stability Samples** value.</span></span> <span data-ttu-id="6e45a-273">Questo valore rappresenta il numero di campioni di cui lo stabilizzatore esegue l'iterazione per calcolare il valore stabilizzato.</span><span class="sxs-lookup"><span data-stu-id="6e45a-273">This value represents the number of samples that the stabilizer iterates on to calculate the stabilized value.</span></span>

## <a name="chapter-4---directional-indicator"></a><span data-ttu-id="6e45a-274">Capitolo 4-indicatore direzionale</span><span class="sxs-lookup"><span data-stu-id="6e45a-274">Chapter 4 - Directional indicator</span></span>

>[!VIDEO https://www.youtube.com/embed/htVbJCMlj64]

### <a name="objectives"></a><span data-ttu-id="6e45a-275">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="6e45a-275">Objectives</span></span>

* <span data-ttu-id="6e45a-276">Aggiungere un indicatore direzionale sul cursore per individuare gli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="6e45a-276">Add a directional indicator on the cursor to help find holograms.</span></span>

### <a name="instructions"></a><span data-ttu-id="6e45a-277">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="6e45a-277">Instructions</span></span>

<span data-ttu-id="6e45a-278">Verrà usato il file **DirectionIndicator.cs** che:</span><span class="sxs-lookup"><span data-stu-id="6e45a-278">We're going to use the **DirectionIndicator.cs** file which will:</span></span>

1. <span data-ttu-id="6e45a-279">Mostra l'indicatore direzionale se l'utente non sta guardando gli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="6e45a-279">Show the directional indicator if the user is not gazing at the holograms.</span></span>
2. <span data-ttu-id="6e45a-280">Nascondere l'indicatore direzionale se l'utente sta guardando gli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="6e45a-280">Hide the directional indicator if the user is gazing at the holograms.</span></span>
3. <span data-ttu-id="6e45a-281">Aggiornare l'indicatore direzionale in modo che punti agli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="6e45a-281">Update the directional indicator to point to the holograms.</span></span>

<span data-ttu-id="6e45a-282">Ma veniamo al dunque.</span><span class="sxs-lookup"><span data-stu-id="6e45a-282">Let's get started.</span></span>

1. <span data-ttu-id="6e45a-283">Fare clic sull'  oggetto astror nel pannello **gerarchia** e **fare clic sulla freccia** per espanderlo.</span><span class="sxs-lookup"><span data-stu-id="6e45a-283">Click on the **AstroMan** object in the **Hierarchy** panel and **click the arrow** to expand it.</span></span>
2. <span data-ttu-id="6e45a-284">Nel pannello **gerarchia** selezionare l'oggetto **DirectionalIndicator** in Astron .</span><span class="sxs-lookup"><span data-stu-id="6e45a-284">In the **Hierarchy** panel, select the **DirectionalIndicator** object under **AstroMan**.</span></span>
3. <span data-ttu-id="6e45a-285">Nel pannello **Inspector** fare clic sul pulsante **Add Component** .</span><span class="sxs-lookup"><span data-stu-id="6e45a-285">In the **Inspector** panel, click the **Add Component** button.</span></span>
4. <span data-ttu-id="6e45a-286">Nel menu digitare nell' **indicatore di direzione**della casella di ricerca.</span><span class="sxs-lookup"><span data-stu-id="6e45a-286">In the menu, type in the search box **Direction Indicator**.</span></span> <span data-ttu-id="6e45a-287">Selezionare il risultato della ricerca.</span><span class="sxs-lookup"><span data-stu-id="6e45a-287">Select the search result.</span></span>
5. <span data-ttu-id="6e45a-288">Nel pannello **gerarchia** trascinare e rilasciare l'oggetto **cursore** sulla proprietà **Cursor** del **controllo**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-288">In the **Hierarchy** panel, drag and drop the **Cursor** object onto the **Cursor** property in the **Inspector**.</span></span>
6. <span data-ttu-id="6e45a-289">Nel pannello **progetto** , nella cartella **ologrammi** , trascinare l'asset **DirectionalIndicator** sulla proprietà **indicatore direzionale** nel **controllo**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-289">In the **Project** panel, in the **Holograms** folder, drag and drop the **DirectionalIndicator** asset onto the **Directional Indicator** property in the **Inspector**.</span></span>
7. <span data-ttu-id="6e45a-290">Compilare e distribuire l'app.</span><span class="sxs-lookup"><span data-stu-id="6e45a-290">Build and deploy the app.</span></span>
8. <span data-ttu-id="6e45a-291">Osservare come l'oggetto indicatore direzionale aiuta a trovare l'astronauta.</span><span class="sxs-lookup"><span data-stu-id="6e45a-291">Watch how the directional indicator object helps you find the astronaut.</span></span>

## <a name="chapter-5---billboarding"></a><span data-ttu-id="6e45a-292">Capitolo 5-Billboard</span><span class="sxs-lookup"><span data-stu-id="6e45a-292">Chapter 5 - Billboarding</span></span>

>[!VIDEO https://www.youtube.com/embed/qFiLr_LUACE]

### <a name="objectives"></a><span data-ttu-id="6e45a-293">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="6e45a-293">Objectives</span></span>

* <span data-ttu-id="6e45a-294">Usare il tabellone per fare in modo che gli ologrammi siano sempre volti verso l'utente.</span><span class="sxs-lookup"><span data-stu-id="6e45a-294">Use billboarding to have holograms always face towards you.</span></span>

<span data-ttu-id="6e45a-295">Verrà usato il file **Billboard.cs** per tenere un GameObject orientato in modo che sia sempre attivo per l'utente.</span><span class="sxs-lookup"><span data-stu-id="6e45a-295">We will be using the **Billboard.cs** file to keep a GameObject oriented such that it is facing the user at all times.</span></span>

1. <span data-ttu-id="6e45a-296">Nel pannello **gerarchia** selezionare l'oggetto **Astron** .</span><span class="sxs-lookup"><span data-stu-id="6e45a-296">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
2. <span data-ttu-id="6e45a-297">Nel pannello **Inspector** fare clic sul pulsante **Add Component** .</span><span class="sxs-lookup"><span data-stu-id="6e45a-297">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="6e45a-298">Nel menu digitare nella casella di ricerca **Billboard**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-298">In the menu, type in the search box **Billboard**.</span></span> <span data-ttu-id="6e45a-299">Selezionare il risultato della ricerca.</span><span class="sxs-lookup"><span data-stu-id="6e45a-299">Select the search result.</span></span>
4. <span data-ttu-id="6e45a-300">Nel **controllo** impostare l' **asse pivot** su **Y**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-300">In the **Inspector** set the **Pivot Axis** to **Y**.</span></span>
5. <span data-ttu-id="6e45a-301">Prova!</span><span class="sxs-lookup"><span data-stu-id="6e45a-301">Try it!</span></span> <span data-ttu-id="6e45a-302">Compilare e distribuire l'app come prima.</span><span class="sxs-lookup"><span data-stu-id="6e45a-302">Build and deploy the app as before.</span></span>
6. <span data-ttu-id="6e45a-303">Scopri in che modo l'oggetto Billboard si presenta indipendentemente dalla modalità di modifica del punto di vista.</span><span class="sxs-lookup"><span data-stu-id="6e45a-303">See how the Billboard object faces you no matter how you change the viewpoint.</span></span>
7. <span data-ttu-id="6e45a-304">Eliminare lo script da **astroname** per il momento.</span><span class="sxs-lookup"><span data-stu-id="6e45a-304">Delete the script from the **AstroMan** for now.</span></span>

## <a name="chapter-6---tag-along"></a><span data-ttu-id="6e45a-305">Capitolo 6-tag-along</span><span class="sxs-lookup"><span data-stu-id="6e45a-305">Chapter 6 - Tag-Along</span></span>

>[!VIDEO https://www.youtube.com/embed/Ct8ORZAX5JU]

### <a name="objectives"></a><span data-ttu-id="6e45a-306">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="6e45a-306">Objectives</span></span>

* <span data-ttu-id="6e45a-307">Usare i tag-along per fare in modo che gli ologrammi ci siano nella stanza.</span><span class="sxs-lookup"><span data-stu-id="6e45a-307">Use Tag-Along to have our holograms follow us around the room.</span></span>

<span data-ttu-id="6e45a-308">Quando si lavora su questo problema, verranno illustrati i vincoli di progettazione seguenti:</span><span class="sxs-lookup"><span data-stu-id="6e45a-308">As we work on this issue, we'll be guided by the following design constraints:</span></span>

* <span data-ttu-id="6e45a-309">Il contenuto deve essere sempre un'occhiata.</span><span class="sxs-lookup"><span data-stu-id="6e45a-309">Content should always be a glance away.</span></span>
* <span data-ttu-id="6e45a-310">Il contenuto non deve essere nel modo previsto.</span><span class="sxs-lookup"><span data-stu-id="6e45a-310">Content should not be in the way.</span></span>
* <span data-ttu-id="6e45a-311">Il contenuto del blocco Head è scomodo.</span><span class="sxs-lookup"><span data-stu-id="6e45a-311">Head-locking content is uncomfortable.</span></span>

<span data-ttu-id="6e45a-312">La soluzione usata in questo articolo prevede l'uso di un approccio "tag-along".</span><span class="sxs-lookup"><span data-stu-id="6e45a-312">The solution used here is to use a "tag-along" approach.</span></span>

<span data-ttu-id="6e45a-313">Un oggetto tag-along non lascia completamente la visualizzazione dell'utente.</span><span class="sxs-lookup"><span data-stu-id="6e45a-313">A tag-along object never fully leaves the user's view.</span></span> <span data-ttu-id="6e45a-314">È possibile considerare un tag come un oggetto collegato alla testa dell'utente tramite bande di gomma.</span><span class="sxs-lookup"><span data-stu-id="6e45a-314">You can think of the a tag-along as being an object attached to the user's head by rubber bands.</span></span> <span data-ttu-id="6e45a-315">Quando l'utente si sposta, il contenuto rimarrà in una semplice occhiata scorrendo verso il bordo della visualizzazione senza uscire completamente.</span><span class="sxs-lookup"><span data-stu-id="6e45a-315">As the user moves, the content will stay within an easy glance by sliding towards the edge of the view without completely leaving.</span></span> <span data-ttu-id="6e45a-316">Quando l'utente guarda l'oggetto tag-along, viene visualizzato in modo più completo.</span><span class="sxs-lookup"><span data-stu-id="6e45a-316">When the user gazes towards the tag-along object, it comes more fully into view.</span></span>

<span data-ttu-id="6e45a-317">Verrà usato il file **SimpleTagalong.cs** che:</span><span class="sxs-lookup"><span data-stu-id="6e45a-317">We're going to use the **SimpleTagalong.cs** file which will:</span></span>

1. <span data-ttu-id="6e45a-318">Determinare se l'oggetto tag-along si trova all'interno dei limiti della fotocamera.</span><span class="sxs-lookup"><span data-stu-id="6e45a-318">Determine if the Tag-Along object is within the camera bounds.</span></span>
2. <span data-ttu-id="6e45a-319">Se non è presente nella vista tronco, posizionare il tag-lungo su parzialmente all'interno della vista tronco.</span><span class="sxs-lookup"><span data-stu-id="6e45a-319">If not within the view frustum, position the Tag-Along to partially within the view frustum.</span></span>
3. <span data-ttu-id="6e45a-320">In caso contrario, posizionare il tag su una distanza predefinita dall'utente.</span><span class="sxs-lookup"><span data-stu-id="6e45a-320">Otherwise, position the Tag-Along to a default distance from the user.</span></span>

<span data-ttu-id="6e45a-321">Per eseguire questa operazione, è necessario prima di tutto modificare lo script **Interactible.cs** per chiamare **TagalongAction**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-321">To do this, we first must change the **Interactible.cs** script to call the **TagalongAction**.</span></span>

1. <span data-ttu-id="6e45a-322">Modificare **Interactible.cs** completando il codice esercizio 6. a (rimuovendo il commento dalle righe da 84 a 87).</span><span class="sxs-lookup"><span data-stu-id="6e45a-322">Edit **Interactible.cs** by completing coding exercise 6.a (uncommenting lines 84 to 87).</span></span>

```cs
/* TODO: DEVELOPER CODING EXERCISE 6.a */
// 6.a: Uncomment the lines below to perform a Tagalong action.
if (interactibleAction != null)
{
    interactibleAction.PerformAction();
}
```

<span data-ttu-id="6e45a-323">Lo script **InteractibleAction.cs** , associato a **Interactible.cs** , esegue azioni personalizzate quando si toccano gli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="6e45a-323">The **InteractibleAction.cs** script, paired with **Interactible.cs** performs custom actions when you tap on holograms.</span></span> <span data-ttu-id="6e45a-324">In questo caso, verrà usato uno specifico per il tag-along.</span><span class="sxs-lookup"><span data-stu-id="6e45a-324">In this case, we'll use one specifically for tag-along.</span></span>

* <span data-ttu-id="6e45a-325">Nella cartella **Scripts** fare clic su **TagalongAction.cs** asset per aprirlo in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6e45a-325">In the **Scripts** folder click on **TagalongAction.cs** asset to open in Visual Studio.</span></span>
* <span data-ttu-id="6e45a-326">Completare l'esercizio di codifica o sostituirlo con il seguente:</span><span class="sxs-lookup"><span data-stu-id="6e45a-326">Complete the coding exercise or change it to this:</span></span>
  * <span data-ttu-id="6e45a-327">Nella parte superiore della **gerarchia**, nella barra di ricerca digitare **ChestButton_Center** e selezionare il risultato.</span><span class="sxs-lookup"><span data-stu-id="6e45a-327">At the top of the **Hierarchy**, in the search bar type **ChestButton_Center** and select the result.</span></span>
  * <span data-ttu-id="6e45a-328">Nel pannello **Inspector** fare clic sul pulsante **Add Component** .</span><span class="sxs-lookup"><span data-stu-id="6e45a-328">In the **Inspector** panel, click the **Add Component** button.</span></span>
  * <span data-ttu-id="6e45a-329">Nel menu digitare nella casella di ricerca **azione Tagalong**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-329">In the menu, type in the search box **Tagalong Action**.</span></span> <span data-ttu-id="6e45a-330">Selezionare il risultato della ricerca.</span><span class="sxs-lookup"><span data-stu-id="6e45a-330">Select the search result.</span></span>
  * <span data-ttu-id="6e45a-331">Nella  cartella ologrammi trovare l'asset **Tagalong** .</span><span class="sxs-lookup"><span data-stu-id="6e45a-331">In **Holograms** folder find the **Tagalong** asset.</span></span>
  * <span data-ttu-id="6e45a-332">Consente di selezionare l'oggetto **ChestButton_Center** nella **gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="6e45a-332">Select the **ChestButton_Center** object in the **Hierarchy**.</span></span> <span data-ttu-id="6e45a-333">Trascinare e rilasciare l'oggetto **TagAlong** dal pannello del **progetto** nel **controllo** nella proprietà **oggetto in TagAlong** .</span><span class="sxs-lookup"><span data-stu-id="6e45a-333">Drag and drop the **TagAlong** object from the **Project** panel onto the **Inspector** into the **Object To Tagalong** property.</span></span>
  * <span data-ttu-id="6e45a-334">Trascinare l'oggetto **azione Tagalong** da **Inspector** nel campo **azione Interactible** nello script **Interactible** .</span><span class="sxs-lookup"><span data-stu-id="6e45a-334">Drag the **Tagalong Action** object from the **Inspector** into the **Interactible Action** field on the **Interactible** script.</span></span>
* <span data-ttu-id="6e45a-335">Fare doppio clic sullo script **TagalongAction** per aprirlo in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6e45a-335">Double click the **TagalongAction** script to open it in Visual Studio.</span></span>

![Configurazione di Interactible](images/holograms210-interactible.png)

<span data-ttu-id="6e45a-337">È necessario aggiungere quanto segue:</span><span class="sxs-lookup"><span data-stu-id="6e45a-337">We need to add the following:</span></span>

* <span data-ttu-id="6e45a-338">Aggiungere funzionalità alla funzione PerformAction nello script TagalongAction (Ereditato da InteractibleAction).</span><span class="sxs-lookup"><span data-stu-id="6e45a-338">Add functionality to the PerformAction function in the TagalongAction script (inherited from InteractibleAction).</span></span>
* <span data-ttu-id="6e45a-339">Aggiungere il tabellone all'oggetto guardato su e impostare l'asse pivot su XY.</span><span class="sxs-lookup"><span data-stu-id="6e45a-339">Add billboarding to the gazed-upon object, and set the pivot axis to XY.</span></span>
* <span data-ttu-id="6e45a-340">Aggiungere quindi un semplice tag insieme all'oggetto.</span><span class="sxs-lookup"><span data-stu-id="6e45a-340">Then add simple Tag-Along to the object.</span></span>

<span data-ttu-id="6e45a-341">Ecco la nostra soluzione, di **TagalongAction.cs**:</span><span class="sxs-lookup"><span data-stu-id="6e45a-341">Here's our solution, from **TagalongAction.cs**:</span></span>

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using HoloToolkit.Unity;
using UnityEngine;

public class TagalongAction : InteractibleAction
{
    [SerializeField]
    [Tooltip("Drag the Tagalong prefab asset you want to display.")]
    private GameObject objectToTagalong;

    private void Awake()
    {
        if (objectToTagalong != null)
        {
            objectToTagalong = Instantiate(objectToTagalong);
            objectToTagalong.SetActive(false);

            /* TODO: DEVELOPER CODING EXERCISE 6.b */

            // 6.b: AddComponent Billboard to objectToTagAlong,
            // so it's always facing the user as they move.
            Billboard billboard = objectToTagalong.AddComponent<Billboard>();

            // 6.b: AddComponent SimpleTagalong to objectToTagAlong,
            // so it's always following the user as they move.
            objectToTagalong.AddComponent<SimpleTagalong>();

            // 6.b: Set any public properties you wish to experiment with.
            billboard.PivotAxis = PivotAxis.XY; // Already the default, but provided in case you want to edit
        }
    }

    public override void PerformAction()
    {
        // Recommend having only one tagalong.
        if (objectToTagalong == null || objectToTagalong.activeSelf)
        {
            return;
        }

        objectToTagalong.SetActive(true);
    }
}
```

* <span data-ttu-id="6e45a-342">Prova!</span><span class="sxs-lookup"><span data-stu-id="6e45a-342">Try it!</span></span> <span data-ttu-id="6e45a-343">Compilare e distribuire l'app.</span><span class="sxs-lookup"><span data-stu-id="6e45a-343">Build and deploy the app.</span></span>
* <span data-ttu-id="6e45a-344">Osservare il modo in cui il contenuto segue il centro del punto di controllo, ma non continuamente e senza bloccarlo.</span><span class="sxs-lookup"><span data-stu-id="6e45a-344">Watch how the content follows the center of the gaze point, but not continuously and without blocking it.</span></span>

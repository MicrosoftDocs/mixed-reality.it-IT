---
title: Input MR 210 - sguardo
description: Seguire questa procedura dettagliata con Unity, Visual Studio e HoloLens che informazioni dettagliate su concetti sguardo di codifica.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, sguardo dell'esercitazione, academy,
ms.openlocfilehash: 63c55e8a7a348f2a3e0cc29a9795d7fabcef5df0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599373"
---
>[!NOTE]
><span data-ttu-id="32323-104">Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.</span><span class="sxs-lookup"><span data-stu-id="32323-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="32323-105">Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.</span><span class="sxs-lookup"><span data-stu-id="32323-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="32323-106">Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.</span><span class="sxs-lookup"><span data-stu-id="32323-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="32323-107">Essi verranno mantenute per continuare a utilizzare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="32323-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="32323-108">Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="32323-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="32323-109">Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.</span><span class="sxs-lookup"><span data-stu-id="32323-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-input-210-gaze"></a><span data-ttu-id="32323-110">Input di MR 210: Sguardo fisso</span><span class="sxs-lookup"><span data-stu-id="32323-110">MR Input 210: Gaze</span></span>

<span data-ttu-id="32323-111">[Estasiati](gaze.md) è il primo modulo di input e rivela consapevolezza e finalità dell'utente.</span><span class="sxs-lookup"><span data-stu-id="32323-111">[Gaze](gaze.md) is the first form of input and reveals the user's intent and awareness.</span></span> <span data-ttu-id="32323-112">210 Input MR (noto anche come Esplora progetti) è un'analisi approfondita i concetti correlati sguardo per realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="32323-112">MR Input 210 (aka Project Explorer) is a deep dive into gaze-related concepts for Windows Mixed Reality.</span></span> <span data-ttu-id="32323-113">Verranno aggiunte consapevolezza contestuale per il cursore e vntana, sfruttando al meglio ciò che l'app conosce sguardo dell'utente.</span><span class="sxs-lookup"><span data-stu-id="32323-113">We will be adding contextual awareness to our cursor and holograms, taking full advantage of what your app knows about the user's gaze.</span></span>

>[!VIDEO https://www.youtube.com/embed/yKAttGduVp0]

<span data-ttu-id="32323-114">Abbiamo un astronautici descrittivo qui per scoprire i concetti sguardo.</span><span class="sxs-lookup"><span data-stu-id="32323-114">We have a friendly astronaut here to help you learn gaze concepts.</span></span> <span data-ttu-id="32323-115">Nelle [MR nozioni di base 101](holograms-101.md), avevamo un cursore semplice seguite semplicemente lo sguardo.</span><span class="sxs-lookup"><span data-stu-id="32323-115">In [MR Basics 101](holograms-101.md), we had a simple cursor that just followed your gaze.</span></span> <span data-ttu-id="32323-116">Oggi passiamo ora spinge ulteriormente oltre con il cursore semplice:</span><span class="sxs-lookup"><span data-stu-id="32323-116">Today we're moving a step beyond the simple cursor:</span></span>

* <span data-ttu-id="32323-117">Rendiamo il cursore e i nostri vntana sguardo riconoscere: entrambi cambierà in base a dove sta guardando l'utente - o in cui l'utente viene *non* alla ricerca.</span><span class="sxs-lookup"><span data-stu-id="32323-117">We're making the cursor and our holograms gaze-aware: both will change based on where the user is looking - or where the user is *not* looking.</span></span> <span data-ttu-id="32323-118">Questo li rende sensibili al contesto.</span><span class="sxs-lookup"><span data-stu-id="32323-118">This makes them context-aware.</span></span>
* <span data-ttu-id="32323-119">Si aggiungerà commenti e suggerimenti a cursore e vntana per consentire all'utente altre informazioni sul contesto su ciò che è interessato.</span><span class="sxs-lookup"><span data-stu-id="32323-119">We will add feedback to our cursor and holograms to give the user more context on what is being targeted.</span></span> <span data-ttu-id="32323-120">Questi commenti e suggerimenti possono essere audio e video.</span><span class="sxs-lookup"><span data-stu-id="32323-120">This feedback can be audio and visual.</span></span>
* <span data-ttu-id="32323-121">Ti mostreremo le tecniche di destinazione per consentire agli utenti di raggiungere destinazioni più piccole.</span><span class="sxs-lookup"><span data-stu-id="32323-121">We'll show you targeting techniques to help users hit smaller targets.</span></span>
* <span data-ttu-id="32323-122">Vi mostreremo come attirare l'attenzione dell'utente di vntana con un indicatore direzionale.</span><span class="sxs-lookup"><span data-stu-id="32323-122">We'll show you how to draw the user's attention to your holograms with a directional indicator.</span></span>
* <span data-ttu-id="32323-123">Si saranno di apprendere rapidamente le tecniche per sfruttare il vntana con l'utente come Anna non si sposta il mondo.</span><span class="sxs-lookup"><span data-stu-id="32323-123">We'll teach you techniques to take your holograms with the user as she moves around in your world.</span></span>

>[!IMPORTANT]
><span data-ttu-id="32323-124">I video incorporati in ognuna delle sezioni seguenti sono stati registrati usando una versione precedente di Unity e il Toolkit di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="32323-124">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="32323-125">Anche se le istruzioni dettagliate sono accurate e aggiornate, è possibile visualizzare gli script e gli oggetti visivi nei video corrispondenti che non sono aggiornati.</span><span class="sxs-lookup"><span data-stu-id="32323-125">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="32323-126">I video rimangono inclusi per ci si ricorderà più e perché i concetti illustrati sono applicano.</span><span class="sxs-lookup"><span data-stu-id="32323-126">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="32323-127">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="32323-127">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="32323-128">Corso</span><span class="sxs-lookup"><span data-stu-id="32323-128">Course</span></span></th><th style="width:150px"> <span data-ttu-id="32323-129"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="32323-129"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="32323-130"><a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></span><span class="sxs-lookup"><span data-stu-id="32323-130"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="32323-131">Input di MR 210: Sguardo fisso</span><span class="sxs-lookup"><span data-stu-id="32323-131">MR Input 210: Gaze</span></span></td><td style="text-align: center;"> <span data-ttu-id="32323-132">✔️</span><span class="sxs-lookup"><span data-stu-id="32323-132">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="32323-133">✔️</span><span class="sxs-lookup"><span data-stu-id="32323-133">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="32323-134">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="32323-134">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="32323-135">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="32323-135">Prerequisites</span></span>

* <span data-ttu-id="32323-136">Un PC Windows 10 configurate con i valori corretti [sono installati gli strumenti](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="32323-136">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="32323-137">Alcuni basic C# capacità di programmazione.</span><span class="sxs-lookup"><span data-stu-id="32323-137">Some basic C# programming ability.</span></span>
* <span data-ttu-id="32323-138">È necessario avere completato [MR nozioni di base 101](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="32323-138">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="32323-139">Un dispositivo HoloLens [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="32323-139">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="32323-140">File di progetto</span><span class="sxs-lookup"><span data-stu-id="32323-140">Project files</span></span>

* <span data-ttu-id="32323-141">Scaricare il [file](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) necessarie per il progetto.</span><span class="sxs-lookup"><span data-stu-id="32323-141">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) required by the project.</span></span><span data-ttu-id="32323-142"> Richiede Unity 2017.2 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="32323-142"> Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="32323-143">Annullare la-archive i file sul desktop o altri facile da raggiungere percorso.</span><span class="sxs-lookup"><span data-stu-id="32323-143">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="32323-144">Se si desidera esaminare il codice sorgente prima di scaricare, ha [disponibile in GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze).</span><span class="sxs-lookup"><span data-stu-id="32323-144">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="32323-145">Errori e note</span><span class="sxs-lookup"><span data-stu-id="32323-145">Errata and Notes</span></span>

* <span data-ttu-id="32323-146">In Visual Studio, "Just My Code" deve essere disabilitata (deselezionata) in Strumenti -> Opzioni -> debug per poter raggiungere punti di interruzione nel codice.</span><span class="sxs-lookup"><span data-stu-id="32323-146">In Visual Studio, "Just My Code" needs to be disabled (unchecked) under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="32323-147">Capitolo 1 - il programma di installazione di Unity</span><span class="sxs-lookup"><span data-stu-id="32323-147">Chapter 1 - Unity Setup</span></span>

>[!VIDEO https://www.youtube.com/embed/_Ccn6riQ6vU]

### <a name="objectives"></a><span data-ttu-id="32323-148">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="32323-148">Objectives</span></span>

* <span data-ttu-id="32323-149">L'ottimizzazione di Unity per lo sviluppo di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="32323-149">Optimize Unity for HoloLens development.</span></span>
* <span data-ttu-id="32323-150">Importare le risorse e configurare la scena.</span><span class="sxs-lookup"><span data-stu-id="32323-150">Import assets and setup the scene.</span></span>
* <span data-ttu-id="32323-151">Visualizzare l'astronautici di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="32323-151">View the astronaut in the HoloLens.</span></span>

### <a name="instructions"></a><span data-ttu-id="32323-152">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="32323-152">Instructions</span></span>

1. <span data-ttu-id="32323-153">Avviare Unity.</span><span class="sxs-lookup"><span data-stu-id="32323-153">Start Unity.</span></span>
2. <span data-ttu-id="32323-154">Selezionare **nuovo progetto**.</span><span class="sxs-lookup"><span data-stu-id="32323-154">Select **New Project**.</span></span>
3. <span data-ttu-id="32323-155">Denominare il progetto **ModelExplorer**.</span><span class="sxs-lookup"><span data-stu-id="32323-155">Name the project **ModelExplorer**.</span></span>
4. <span data-ttu-id="32323-156">Immettere il percorso come il **estasiati** cartella è archiviato in precedenza di annullamento.</span><span class="sxs-lookup"><span data-stu-id="32323-156">Enter location as the **Gaze** folder you previously un-archived.</span></span>
5. <span data-ttu-id="32323-157">Verificare che il progetto è impostato su **3D**.</span><span class="sxs-lookup"><span data-stu-id="32323-157">Make sure the project is set to **3D**.</span></span>
6. <span data-ttu-id="32323-158">Fare clic su **Crea progetto**.</span><span class="sxs-lookup"><span data-stu-id="32323-158">Click **Create Project**.</span></span>

### <a name="unity-settings-for-hololens"></a><span data-ttu-id="32323-159">Impostazioni di Unity per HoloLens</span><span class="sxs-lookup"><span data-stu-id="32323-159">Unity settings for HoloLens</span></span>

<span data-ttu-id="32323-160">Dobbiamo informare Unity che deve creare l'app è in corso per esportare un' [vista immersiva](app-views.md) invece di una visualizzazione 2D.</span><span class="sxs-lookup"><span data-stu-id="32323-160">We need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="32323-161">Ciò si ottiene aggiungendo HoloLens come dispositivo di realtà virtuale.</span><span class="sxs-lookup"><span data-stu-id="32323-161">We do that by adding HoloLens as a virtual reality device.</span></span>

1. <span data-ttu-id="32323-162">Passare a **Modifica > impostazioni del progetto > Player**.</span><span class="sxs-lookup"><span data-stu-id="32323-162">Go to **Edit > Project Settings > Player**.</span></span>
2. <span data-ttu-id="32323-163">Nel **Pannello di controllo** per le impostazioni del giocatore, selezionare la **Windows Store** icona.</span><span class="sxs-lookup"><span data-stu-id="32323-163">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="32323-164">Espandere la **XR impostazioni** gruppo.</span><span class="sxs-lookup"><span data-stu-id="32323-164">Expand the **XR Settings** group.</span></span>
4. <span data-ttu-id="32323-165">Nel **Rendering** sezione controllo la **realtà virtuale supportato** casella di controllo per aggiungere un nuovo **gli SDK di realtà virtuale** elenco.</span><span class="sxs-lookup"><span data-stu-id="32323-165">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality SDKs** list.</span></span>
5. <span data-ttu-id="32323-166">Verificare che **realtà mista di Windows** visualizzato nell'elenco.</span><span class="sxs-lookup"><span data-stu-id="32323-166">Verify that **Windows Mixed Reality** appears in the list.</span></span> <span data-ttu-id="32323-167">In caso contrario, selezionare la **+** pulsante nella parte inferiore dell'elenco e scegliere **Windows Holographic**.</span><span class="sxs-lookup"><span data-stu-id="32323-167">If not, select the **+** button at the bottom of the list and choose **Windows Holographic**.</span></span>

<span data-ttu-id="32323-168">Successivamente, è necessario impostare scripting back-end per .NET.</span><span class="sxs-lookup"><span data-stu-id="32323-168">Next, we need to set our scripting backend to .NET.</span></span>

1. <span data-ttu-id="32323-169">Passare a **Modifica > Impostazioni di progetto > Player** (è ancora possibile avere questo nel passaggio precedente).</span><span class="sxs-lookup"><span data-stu-id="32323-169">Go to **Edit > Project Settings > Player** (you may still have this up from the previous step).</span></span>
2. <span data-ttu-id="32323-170">Nel **Pannello di controllo** per le impostazioni del giocatore, selezionare la **Windows Store** icona.</span><span class="sxs-lookup"><span data-stu-id="32323-170">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="32323-171">Nel **altre impostazioni** Configuration sezione, assicurarsi che **Scripting back-end** è impostato su **.NET**</span><span class="sxs-lookup"><span data-stu-id="32323-171">In the **Other Settings** Configuration section, make sure that **Scripting Backend** is set to **.NET**</span></span>

<span data-ttu-id="32323-172">Infine, aggiorneremo le impostazioni di qualità per ottenere una rapida prestazioni su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="32323-172">Finally, we'll update our quality settings to achieve a fast performance on HoloLens.</span></span>

1. <span data-ttu-id="32323-173">Passare a **Modifica > impostazioni del progetto > qualità**.</span><span class="sxs-lookup"><span data-stu-id="32323-173">Go to **Edit > Project Settings > Quality**.</span></span>
2. <span data-ttu-id="32323-174">Fare clic sulla freccia rivolta nel **predefinito** riga sotto l'icona di Windows Store.</span><span class="sxs-lookup"><span data-stu-id="32323-174">Click on downward pointing arrow in the **Default** row under the Windows Store icon.</span></span>
3. <span data-ttu-id="32323-175">Selezionare **veloce** per **le app di Windows Store**.</span><span class="sxs-lookup"><span data-stu-id="32323-175">Select **Fastest** for **Windows Store Apps**.</span></span>

### <a name="import-project-assets"></a><span data-ttu-id="32323-176">Importare le risorse del progetto</span><span class="sxs-lookup"><span data-stu-id="32323-176">Import project assets</span></span>

1. <span data-ttu-id="32323-177">Fare clic il **asset** cartella il **progetto** pannello.</span><span class="sxs-lookup"><span data-stu-id="32323-177">Right click the **Assets** folder in the **Project** panel.</span></span>
2. <span data-ttu-id="32323-178">Fare clic su **Importa pacchetto > pacchetto personalizzato**.</span><span class="sxs-lookup"><span data-stu-id="32323-178">Click on **Import Package > Custom Package**.</span></span>
3. <span data-ttu-id="32323-179">Passare ai file di progetto è stato scaricato e fare clic su **ModelExplorer.unitypackage**.</span><span class="sxs-lookup"><span data-stu-id="32323-179">Navigate to the project files you downloaded and click on **ModelExplorer.unitypackage**.</span></span>
4. <span data-ttu-id="32323-180">Fare clic su **Apri**.</span><span class="sxs-lookup"><span data-stu-id="32323-180">Click **Open**.</span></span>
5. <span data-ttu-id="32323-181">Dopo avere caricato il pacchetto, fare clic sui **importazione** pulsante.</span><span class="sxs-lookup"><span data-stu-id="32323-181">After the package loads, click on the **Import** button.</span></span>

### <a name="setup-the-scene"></a><span data-ttu-id="32323-182">Programma di installazione della scena</span><span class="sxs-lookup"><span data-stu-id="32323-182">Setup the scene</span></span>

1. <span data-ttu-id="32323-183">Nella gerarchia, eliminare il **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="32323-183">In the Hierarchy, delete the **Main Camera**.</span></span>
2. <span data-ttu-id="32323-184">Nel **HoloToolkit** cartella, aprire il **Input** cartella, quindi aprire il **Prefabs** cartella.</span><span class="sxs-lookup"><span data-stu-id="32323-184">In the **HoloToolkit** folder, open the **Input** folder, then open the **Prefabs** folder.</span></span>
3. <span data-ttu-id="32323-185">Trascinare e rilasciare il **MixedRealityCameraParent** prefab dal **Prefabs** nella cartella la **gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="32323-185">Drag and drop the **MixedRealityCameraParent** prefab from the **Prefabs** folder into the **Hierarchy**.</span></span>
4. <span data-ttu-id="32323-186">Fare doppio clic il **luce direzionale** nella gerarchia e selezionare **eliminare**.</span><span class="sxs-lookup"><span data-stu-id="32323-186">Right-click the **Directional Light** in the Hierarchy and select **Delete**.</span></span>
5. <span data-ttu-id="32323-187">Nel **Vntana** cartella, trascinare e rilasciare le risorse seguenti nella radice del **gerarchia**:</span><span class="sxs-lookup"><span data-stu-id="32323-187">In the **Holograms** folder, drag and drop the following assets into the root of the **Hierarchy**:</span></span>
    * <span data-ttu-id="32323-188">**AstroMan**</span><span class="sxs-lookup"><span data-stu-id="32323-188">**AstroMan**</span></span>
    * <span data-ttu-id="32323-189">**luci**</span><span class="sxs-lookup"><span data-stu-id="32323-189">**Lights**</span></span>
    * <span data-ttu-id="32323-190">**SpaceAudioSource**</span><span class="sxs-lookup"><span data-stu-id="32323-190">**SpaceAudioSource**</span></span>
    * <span data-ttu-id="32323-191">**SpaceBackground**</span><span class="sxs-lookup"><span data-stu-id="32323-191">**SpaceBackground**</span></span>
6. <span data-ttu-id="32323-192">Avviare **modalità di riproduzione** ▶ per visualizzare l'astronautici.</span><span class="sxs-lookup"><span data-stu-id="32323-192">Start **Play Mode** ▶ to view the astronaut.</span></span>
7. <span data-ttu-id="32323-193">Fare clic su **modalità di riproduzione** ▶ nuovamente a **arrestare**.</span><span class="sxs-lookup"><span data-stu-id="32323-193">Click **Play Mode** ▶ again to **Stop**.</span></span>
8. <span data-ttu-id="32323-194">Nel **Vntana** cartella trovare il **Fitbox** asset e trascinarlo nella radice del **gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="32323-194">In the **Holograms** folder, find the **Fitbox** asset and drag it to the root of the **Hierarchy**.</span></span>
9. <span data-ttu-id="32323-195">Selezionare il **Fitbox** nel **gerarchia** pannello.</span><span class="sxs-lookup"><span data-stu-id="32323-195">Select the **Fitbox** in the **Hierarchy** panel.</span></span>
10. <span data-ttu-id="32323-196">Trascinare il **AstroMan** raccolta dal **gerarchia** per il **raccolta ologrammi** proprietà del Fitbox nel **Inspector** pannello.</span><span class="sxs-lookup"><span data-stu-id="32323-196">Drag the **AstroMan** collection from the **Hierarchy** to the **Hologram Collection** property of the Fitbox in the **Inspector** panel.</span></span>

### <a name="save-the-project"></a><span data-ttu-id="32323-197">Salvare il progetto</span><span class="sxs-lookup"><span data-stu-id="32323-197">Save the project</span></span>

1. <span data-ttu-id="32323-198">Salvare la nuova scena: **File > Salva scena come**.</span><span class="sxs-lookup"><span data-stu-id="32323-198">Save the new scene: **File > Save Scene As**.</span></span>
2. <span data-ttu-id="32323-199">Fare clic su **nuova cartella** e denominare la cartella **scene**.</span><span class="sxs-lookup"><span data-stu-id="32323-199">Click **New Folder** and name the folder **Scenes**.</span></span>
3. <span data-ttu-id="32323-200">Denominare il file "**ModelExplorer**" e salvarlo nel **scene** cartella.</span><span class="sxs-lookup"><span data-stu-id="32323-200">Name the file “**ModelExplorer**” and save it in the **Scenes** folder.</span></span>

### <a name="build-the-project"></a><span data-ttu-id="32323-201">Compilare il progetto</span><span class="sxs-lookup"><span data-stu-id="32323-201">Build the project</span></span>

1. <span data-ttu-id="32323-202">In Unity, selezionare **File > Build Settings**.</span><span class="sxs-lookup"><span data-stu-id="32323-202">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="32323-203">Fare clic su **aggiungere scene Open** per aggiungere la scena.</span><span class="sxs-lookup"><span data-stu-id="32323-203">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="32323-204">Selezionare **Universal Windows Platform** nel **Platform** elenco e fare clic su **commutatore piattaforma**.</span><span class="sxs-lookup"><span data-stu-id="32323-204">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="32323-205">Se si sta sviluppando in modo specifico per HoloLens, impostare **dispositivo di destinazione** al **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="32323-205">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="32323-206">In caso contrario, ci si trova sulla **tutti i dispositivi**.</span><span class="sxs-lookup"><span data-stu-id="32323-206">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="32323-207">Assicurarsi **tipo di compilazione** è impostata su **D3D** e **SDK** è impostata su **installata più recente** (che deve essere SDK 16299 o versione successiva).</span><span class="sxs-lookup"><span data-stu-id="32323-207">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="32323-208">Fai clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="32323-208">Click **Build**.</span></span>
7. <span data-ttu-id="32323-209">Creare un **nuova cartella** denominato "App".</span><span class="sxs-lookup"><span data-stu-id="32323-209">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="32323-210">Solo clic i **App** cartella.</span><span class="sxs-lookup"><span data-stu-id="32323-210">Single click the **App** folder.</span></span>
9. <span data-ttu-id="32323-211">Premere **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="32323-211">Press **Select Folder**.</span></span>

<span data-ttu-id="32323-212">Quando Unity viene eseguita, verrà visualizzata una finestra di Esplora File.</span><span class="sxs-lookup"><span data-stu-id="32323-212">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="32323-213">Aprire il **App** cartella.</span><span class="sxs-lookup"><span data-stu-id="32323-213">Open the **App** folder.</span></span>
2. <span data-ttu-id="32323-214">Aprire il **soluzione ModelExplorer Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="32323-214">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="32323-215">Se la distribuzione in HoloLens:</span><span class="sxs-lookup"><span data-stu-id="32323-215">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="32323-216">Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione di debug per **Release** e da ARM a **x86**.</span><span class="sxs-lookup"><span data-stu-id="32323-216">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="32323-217">Fare clic sull'elenco a discesa sulla freccia accanto al pulsante computer locale e selezionare **computer remoto**.</span><span class="sxs-lookup"><span data-stu-id="32323-217">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="32323-218">Immettere **l'indirizzo IP del dispositivo HoloLens** e impostare la modalità di autenticazione **universale (protocollo non crittografato)**.</span><span class="sxs-lookup"><span data-stu-id="32323-218">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="32323-219">Fare clic su **Seleziona**.</span><span class="sxs-lookup"><span data-stu-id="32323-219">Click **Select**.</span></span> <span data-ttu-id="32323-220">Se non si conosce l'indirizzo IP del dispositivo, esaminare **Impostazioni > rete e Internet > Opzioni avanzate**.</span><span class="sxs-lookup"><span data-stu-id="32323-220">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="32323-221">Nella barra dei menu superiore, fare clic su **Debug -> Avvia senza eseguire debug** o premere **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="32323-221">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="32323-222">Se questa è la prima volta che la distribuzione nel dispositivo, devi [abbinarlo a Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span><span class="sxs-lookup"><span data-stu-id="32323-222">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
5. <span data-ttu-id="32323-223">Quando l'app è distribuita, ignorare il **Fitbox** con un **movimento selezionare**.</span><span class="sxs-lookup"><span data-stu-id="32323-223">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="32323-224">Se la distribuzione in un visore VR immersivi:</span><span class="sxs-lookup"><span data-stu-id="32323-224">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="32323-225">Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione di debug per **Release** e da ARM a **x64**.</span><span class="sxs-lookup"><span data-stu-id="32323-225">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="32323-226">Verificare che la destinazione di distribuzione è impostata su **computer locale**.</span><span class="sxs-lookup"><span data-stu-id="32323-226">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="32323-227">Nella barra dei menu superiore, fare clic su **Debug -> Avvia senza eseguire debug** o premere **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="32323-227">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="32323-228">Quando l'app è distribuita, ignorare il **Fitbox** spostando il trigger in un controller di movimento.</span><span class="sxs-lookup"><span data-stu-id="32323-228">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

## <a name="chapter-2---cursor-and-target-feedback"></a><span data-ttu-id="32323-229">Capitolo 2 - commenti e suggerimenti del cursore e di destinazione</span><span class="sxs-lookup"><span data-stu-id="32323-229">Chapter 2 - Cursor and target feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/S24u0V_T7ZI]

### <a name="objectives"></a><span data-ttu-id="32323-230">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="32323-230">Objectives</span></span>

* <span data-ttu-id="32323-231">Progettazione visiva del cursore e il comportamento.</span><span class="sxs-lookup"><span data-stu-id="32323-231">Cursor visual design and behavior.</span></span>
* <span data-ttu-id="32323-232">Commenti e suggerimenti basati su sguardo cursore.</span><span class="sxs-lookup"><span data-stu-id="32323-232">Gaze-based cursor feedback.</span></span>
* <span data-ttu-id="32323-233">Commenti e suggerimenti basati su sguardo ologramma.</span><span class="sxs-lookup"><span data-stu-id="32323-233">Gaze-based hologram feedback.</span></span>

<span data-ttu-id="32323-234">Si vuole basare il lavoro su principi di progettazione del cursore, vale a dire:</span><span class="sxs-lookup"><span data-stu-id="32323-234">We're going to base our work on some cursor design principles, namely:</span></span>

* <span data-ttu-id="32323-235">Il cursore è sempre presente.</span><span class="sxs-lookup"><span data-stu-id="32323-235">The cursor is always present.</span></span>
* <span data-ttu-id="32323-236">Non farti cursore troppo piccola o grande.</span><span class="sxs-lookup"><span data-stu-id="32323-236">Don't let the cursor get too small or big.</span></span>
* <span data-ttu-id="32323-237">Evitare ostruendo contenuto.</span><span class="sxs-lookup"><span data-stu-id="32323-237">Avoid obstructing content.</span></span>

### <a name="instructions"></a><span data-ttu-id="32323-238">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="32323-238">Instructions</span></span>

1. <span data-ttu-id="32323-239">Nel **HoloToolkit\Input\Prefabs** cartella trovare il **InputManager** asset.</span><span class="sxs-lookup"><span data-stu-id="32323-239">In the **HoloToolkit\Input\Prefabs** folder, find the **InputManager** asset.</span></span>
2. <span data-ttu-id="32323-240">Trascinare e rilasciare il **InputManager** nel **gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="32323-240">Drag and drop the **InputManager** onto the **Hierarchy**.</span></span>
3. <span data-ttu-id="32323-241">Nel **HoloToolkit\Input\Prefabs** cartella trovare il **cursore** asset.</span><span class="sxs-lookup"><span data-stu-id="32323-241">In the **HoloToolkit\Input\Prefabs** folder, find the **Cursor** asset.</span></span>
4. <span data-ttu-id="32323-242">Trascinare e rilasciare il **cursore** nel **gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="32323-242">Drag and drop the **Cursor** onto the **Hierarchy**.</span></span>
5. <span data-ttu-id="32323-243">Selezionare il **InputManager** dell'oggetto nel **gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="32323-243">Select the **InputManager** object in the **Hierarchy**.</span></span>
6. <span data-ttu-id="32323-244">Trascinare il **cursore** dell'oggetto dal **gerarchia** nel InputManager **SimpleSinglePointerSelector**del **cursore** campo, nel nella parte inferiore del **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="32323-244">Drag the **Cursor** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector**'s **Cursor** field, at the bottom of the **Inspector**.</span></span>

![Configurazione di selettore singolo puntatore semplice](images/holograms210-ssps.png)

### <a name="build-and-deploy"></a><span data-ttu-id="32323-246">Compilare e distribuire</span><span class="sxs-lookup"><span data-stu-id="32323-246">Build and Deploy</span></span>

1. <span data-ttu-id="32323-247">Ricompilare l'app dalla **File > Impostazioni di compilazione**.</span><span class="sxs-lookup"><span data-stu-id="32323-247">Rebuild the app from **File > Build Settings**.</span></span>
2. <span data-ttu-id="32323-248">Aprire il **cartella App**.</span><span class="sxs-lookup"><span data-stu-id="32323-248">Open the **App folder**.</span></span>
3. <span data-ttu-id="32323-249">Aprire il **soluzione ModelExplorer Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="32323-249">Open the **ModelExplorer Visual Studio Solution**.</span></span>
4. <span data-ttu-id="32323-250">Fare clic su **Debug -> Avvia senza eseguire debug** o premere **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="32323-250">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
5. <span data-ttu-id="32323-251">Osservare come viene disegnato il cursore e come cambia aspetto se tocca ologramma.</span><span class="sxs-lookup"><span data-stu-id="32323-251">Observe how the cursor is drawn, and how it changes appearance if it is touching a hologram.</span></span>

### <a name="instructions"></a><span data-ttu-id="32323-252">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="32323-252">Instructions</span></span>

1. <span data-ttu-id="32323-253">Nel **gerarchia** panel, espandere il **AstroMan**->**GEO_G**->**Back_Center** oggetto.</span><span class="sxs-lookup"><span data-stu-id="32323-253">In the **Hierarchy** panel, expand the **AstroMan**->**GEO_G**->**Back_Center** object.</span></span>
2. <span data-ttu-id="32323-254">Fare doppio clic su **Interactible.cs** per aprirlo in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="32323-254">Double click on **Interactible.cs** to open it in Visual Studio.</span></span>
3. <span data-ttu-id="32323-255">Rimuovere il commento le righe di **IFocusable.OnFocusEnter()** e **IFocusable.OnFocusExit()** callback nei **Interactible.cs**.</span><span class="sxs-lookup"><span data-stu-id="32323-255">Uncomment the lines in the **IFocusable.OnFocusEnter()** and **IFocusable.OnFocusExit()** callbacks in **Interactible.cs**.</span></span> <span data-ttu-id="32323-256">Questi vengono chiamati dal InputManager del Toolkit di realtà mista quando lo stato attivo (sguardo oppure posizionando il controller) entra ed esce dalla collider del GameObject specifico.</span><span class="sxs-lookup"><span data-stu-id="32323-256">These are called by the Mixed Reality Toolkit's InputManager when focus (either by gaze or by controller pointing) enters and exits the specific GameObject's collider.</span></span>

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
><span data-ttu-id="32323-257">Usiamo `EnableKeyword` e `DisableKeyword` sopra.</span><span class="sxs-lookup"><span data-stu-id="32323-257">We use `EnableKeyword` and `DisableKeyword` above.</span></span> <span data-ttu-id="32323-258">Per rendere utilizzare questi elementi nella tua app con shader Standard del Toolkit, è necessario seguire le [linee guida di Unity per l'accesso ai materiali tramite script](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html).</span><span class="sxs-lookup"><span data-stu-id="32323-258">In order to make use of these in your own app with the Toolkit's Standard shader, you'll need to follow the [Unity guidelines for accessing materials via script](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html).</span></span> <span data-ttu-id="32323-259">In questo caso, sono già stati inclusi i [tre varianti di materiale evidenziato](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) necessari nella cartella delle risorse (cercare le tre prime con evidenziazione nel nome).</span><span class="sxs-lookup"><span data-stu-id="32323-259">In this case, we've already included the [three variants of highlighted material](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) needed in the Resources folder (look for the three materials with highlight in the name).</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="32323-260">Compilare e distribuire</span><span class="sxs-lookup"><span data-stu-id="32323-260">Build and Deploy</span></span>

1. <span data-ttu-id="32323-261">Come in precedenza, compilare il progetto e distribuire il HoloLens.</span><span class="sxs-lookup"><span data-stu-id="32323-261">As before, build the project and deploy to the HoloLens.</span></span>
2. <span data-ttu-id="32323-262">Osservare cosa accade quando lo sguardo è rivolto a un oggetto e se non lo è.</span><span class="sxs-lookup"><span data-stu-id="32323-262">Observe what happens when the gaze is aimed at an object and when it's not.</span></span>

## <a name="chapter-3---targeting-techniques"></a><span data-ttu-id="32323-263">Capitolo 3 - tecniche come destinazione</span><span class="sxs-lookup"><span data-stu-id="32323-263">Chapter 3 - Targeting Techniques</span></span>

>[!VIDEO https://www.youtube.com/embed/TFnuLva4VJ0]

### <a name="objectives"></a><span data-ttu-id="32323-264">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="32323-264">Objectives</span></span>

* <span data-ttu-id="32323-265">Rendono più semplice vntana di destinazione.</span><span class="sxs-lookup"><span data-stu-id="32323-265">Make it easier to target holograms.</span></span>
* <span data-ttu-id="32323-266">Stabilizzare naturale spostamenti di tipo head.</span><span class="sxs-lookup"><span data-stu-id="32323-266">Stabilize natural head movements.</span></span>

### <a name="instructions"></a><span data-ttu-id="32323-267">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="32323-267">Instructions</span></span>

1. <span data-ttu-id="32323-268">Nel **gerarchia** riquadro, seleziona la **InputManager** oggetto.</span><span class="sxs-lookup"><span data-stu-id="32323-268">In the **Hierarchy** panel, select the **InputManager** object.</span></span>
2. <span data-ttu-id="32323-269">Nel **Inspector** panel, trovare il **estasiati stabilizzatore** script.</span><span class="sxs-lookup"><span data-stu-id="32323-269">In the **Inspector** panel, find the **Gaze Stabilizer** script.</span></span> <span data-ttu-id="32323-270">Fare clic per aprirlo in Visual Studio, se si vuole dare un'occhiata.</span><span class="sxs-lookup"><span data-stu-id="32323-270">Click it to open in Visual Studio, if you want to take a look.</span></span>
    * <span data-ttu-id="32323-271">Questo script esegue l'iterazione su campioni di dati Raycast e consente di stabilizzare sguardo dell'utente per specificare come destinazione di precisione.</span><span class="sxs-lookup"><span data-stu-id="32323-271">This script iterates over samples of Raycast data and helps stabilize the user's gaze for precision targeting.</span></span>
3. <span data-ttu-id="32323-272">Nel **Inspector**, è possibile modificare le **archiviati esempi stabilità** valore.</span><span class="sxs-lookup"><span data-stu-id="32323-272">In the **Inspector**, you can edit the **Stored Stability Samples** value.</span></span> <span data-ttu-id="32323-273">Questo valore rappresenta il numero di campioni che lo stabilizzatore scorre a calcolare il valore di stabilizzazione.</span><span class="sxs-lookup"><span data-stu-id="32323-273">This value represents the number of samples that the stabilizer iterates on to calculate the stabilized value.</span></span>

## <a name="chapter-4---directional-indicator"></a><span data-ttu-id="32323-274">Capitolo 4 - indicatore direzionale</span><span class="sxs-lookup"><span data-stu-id="32323-274">Chapter 4 - Directional indicator</span></span>

>[!VIDEO https://www.youtube.com/embed/htVbJCMlj64]

### <a name="objectives"></a><span data-ttu-id="32323-275">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="32323-275">Objectives</span></span>

* <span data-ttu-id="32323-276">Aggiungere un indicatore direzionale sul cursore per consentire di individuare vntana.</span><span class="sxs-lookup"><span data-stu-id="32323-276">Add a directional indicator on the cursor to help find holograms.</span></span>

### <a name="instructions"></a><span data-ttu-id="32323-277">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="32323-277">Instructions</span></span>

<span data-ttu-id="32323-278">Si userà il **DirectionIndicator.cs** file che conterrà:</span><span class="sxs-lookup"><span data-stu-id="32323-278">We're going to use the **DirectionIndicator.cs** file which will:</span></span>

1. <span data-ttu-id="32323-279">Mostra l'indicatore direzionale se l'utente non è gazing nel vntana.</span><span class="sxs-lookup"><span data-stu-id="32323-279">Show the directional indicator if the user is not gazing at the holograms.</span></span>
2. <span data-ttu-id="32323-280">Consente di nascondere l'indicatore direzionale se l'utente è gazing nel vntana.</span><span class="sxs-lookup"><span data-stu-id="32323-280">Hide the directional indicator if the user is gazing at the holograms.</span></span>
3. <span data-ttu-id="32323-281">Aggiornare l'indicatore direzionale in modo che punti la vntana.</span><span class="sxs-lookup"><span data-stu-id="32323-281">Update the directional indicator to point to the holograms.</span></span>

<span data-ttu-id="32323-282">Cominciamo.</span><span class="sxs-lookup"><span data-stu-id="32323-282">Let's get started.</span></span>

1. <span data-ttu-id="32323-283">Fare clic sui **AstroMan** dell'oggetto nel **gerarchia** pannello e **fare clic sulla freccia** per espanderlo.</span><span class="sxs-lookup"><span data-stu-id="32323-283">Click on the **AstroMan** object in the **Hierarchy** panel and **click the arrow** to expand it.</span></span>
2. <span data-ttu-id="32323-284">Nel **gerarchia** pannello, seleziona la **DirectionalIndicator** dell'oggetto sotto **AstroMan**.</span><span class="sxs-lookup"><span data-stu-id="32323-284">In the **Hierarchy** panel, select the **DirectionalIndicator** object under **AstroMan**.</span></span>
3. <span data-ttu-id="32323-285">Nel **Inspector** del pannello, fare clic sui **Add Component** pulsante.</span><span class="sxs-lookup"><span data-stu-id="32323-285">In the **Inspector** panel, click the **Add Component** button.</span></span>
4. <span data-ttu-id="32323-286">Nel menu, digitare nella casella di ricerca **indicatori di direzione**.</span><span class="sxs-lookup"><span data-stu-id="32323-286">In the menu, type in the search box **Direction Indicator**.</span></span> <span data-ttu-id="32323-287">Selezionare il risultato della ricerca.</span><span class="sxs-lookup"><span data-stu-id="32323-287">Select the search result.</span></span>
5. <span data-ttu-id="32323-288">Nel **gerarchia** del pannello selezionare e trascinare il **cursore** dell'oggetto nel **cursore** proprietà nel **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="32323-288">In the **Hierarchy** panel, drag and drop the **Cursor** object onto the **Cursor** property in the **Inspector**.</span></span>
6. <span data-ttu-id="32323-289">Nel **Project** pannello il **Vntana** cartella, trascinare e rilasciare il **DirectionalIndicator** asset nel **indicatore direzionale**proprietà di **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="32323-289">In the **Project** panel, in the **Holograms** folder, drag and drop the **DirectionalIndicator** asset onto the **Directional Indicator** property in the **Inspector**.</span></span>
7. <span data-ttu-id="32323-290">Compilare e distribuire l'app.</span><span class="sxs-lookup"><span data-stu-id="32323-290">Build and deploy the app.</span></span>
8. <span data-ttu-id="32323-291">Guarda come oggetto indicatore direzionale consente di trovare l'astronautici.</span><span class="sxs-lookup"><span data-stu-id="32323-291">Watch how the directional indicator object helps you find the astronaut.</span></span>

## <a name="chapter-5---billboarding"></a><span data-ttu-id="32323-292">Capitolo 5 - del billboard</span><span class="sxs-lookup"><span data-stu-id="32323-292">Chapter 5 - Billboarding</span></span>

>[!VIDEO https://www.youtube.com/embed/qFiLr_LUACE]

### <a name="objectives"></a><span data-ttu-id="32323-293">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="32323-293">Objectives</span></span>

* <span data-ttu-id="32323-294">Utilizzare del billboard vntana sempre affrontare verso di te.</span><span class="sxs-lookup"><span data-stu-id="32323-294">Use billboarding to have holograms always face towards you.</span></span>

<span data-ttu-id="32323-295">Verrà usato il **Billboard.cs** file per mantenere un GameObject orientata ai servizi in modo che sia rivolto verso l'utente in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="32323-295">We will be using the **Billboard.cs** file to keep a GameObject oriented such that it is facing the user at all times.</span></span>

1. <span data-ttu-id="32323-296">Nel **gerarchia** riquadro, seleziona la **AstroMan** oggetto.</span><span class="sxs-lookup"><span data-stu-id="32323-296">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
2. <span data-ttu-id="32323-297">Nel **Inspector** del pannello, fare clic sui **Add Component** pulsante.</span><span class="sxs-lookup"><span data-stu-id="32323-297">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="32323-298">Nel menu, digitare nella casella di ricerca **Billboard**.</span><span class="sxs-lookup"><span data-stu-id="32323-298">In the menu, type in the search box **Billboard**.</span></span> <span data-ttu-id="32323-299">Selezionare il risultato della ricerca.</span><span class="sxs-lookup"><span data-stu-id="32323-299">Select the search result.</span></span>
4. <span data-ttu-id="32323-300">Nel **Inspector** impostare il **Pivot asse** al **Y**.</span><span class="sxs-lookup"><span data-stu-id="32323-300">In the **Inspector** set the **Pivot Axis** to **Y**.</span></span>
5. <span data-ttu-id="32323-301">Prova!</span><span class="sxs-lookup"><span data-stu-id="32323-301">Try it!</span></span> <span data-ttu-id="32323-302">Compilare e distribuire l'app come prima.</span><span class="sxs-lookup"><span data-stu-id="32323-302">Build and deploy the app as before.</span></span>
6. <span data-ttu-id="32323-303">Vedere come l'oggetto pannello volti indipendentemente da come si modifica il punto di vista.</span><span class="sxs-lookup"><span data-stu-id="32323-303">See how the Billboard object faces you no matter how you change the viewpoint.</span></span>
7. <span data-ttu-id="32323-304">Eliminare lo script dal **AstroMan** per il momento.</span><span class="sxs-lookup"><span data-stu-id="32323-304">Delete the script from the **AstroMan** for now.</span></span>

## <a name="chapter-6---tag-along"></a><span data-ttu-id="32323-305">Capitolo 6 - Tag-Along</span><span class="sxs-lookup"><span data-stu-id="32323-305">Chapter 6 - Tag-Along</span></span>

>[!VIDEO https://www.youtube.com/embed/Ct8ORZAX5JU]

### <a name="objectives"></a><span data-ttu-id="32323-306">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="32323-306">Objectives</span></span>

* <span data-ttu-id="32323-307">Utilizzare Tag-Along del nostro vntana seguici nella stanza.</span><span class="sxs-lookup"><span data-stu-id="32323-307">Use Tag-Along to have our holograms follow us around the room.</span></span>

<span data-ttu-id="32323-308">Quando si lavora su questo problema, abbiamo informazioni dettagliate tramite i vincoli di progettazione seguenti:</span><span class="sxs-lookup"><span data-stu-id="32323-308">As we work on this issue, we'll be guided by the following design constraints:</span></span>

* <span data-ttu-id="32323-309">Contenuto deve essere sempre immediatamente da subito.</span><span class="sxs-lookup"><span data-stu-id="32323-309">Content should always be a glance away.</span></span>
* <span data-ttu-id="32323-310">Contenuto non deve essere nel modo.</span><span class="sxs-lookup"><span data-stu-id="32323-310">Content should not be in the way.</span></span>
* <span data-ttu-id="32323-311">Il contenuto di blocco HEAD è disagio.</span><span class="sxs-lookup"><span data-stu-id="32323-311">Head-locking content is uncomfortable.</span></span>

<span data-ttu-id="32323-312">La soluzione usata in questo esempio consiste nell'utilizzare un approccio "tag-along".</span><span class="sxs-lookup"><span data-stu-id="32323-312">The solution used here is to use a "tag-along" approach.</span></span>

<span data-ttu-id="32323-313">Un oggetto tag-along lascia mai in vista dell'utente.</span><span class="sxs-lookup"><span data-stu-id="32323-313">A tag-along object never fully leaves the user's view.</span></span> <span data-ttu-id="32323-314">È possibile considerare l'allegato un tag-along come un oggetto all'inizio dell'utente da elastici.</span><span class="sxs-lookup"><span data-stu-id="32323-314">You can think of the a tag-along as being an object attached to the user's head by rubber bands.</span></span> <span data-ttu-id="32323-315">Quando l'utente sposta, il contenuto viene mantenuta all'interno di un semplice sguardo facendo scorrere verso il bordo della visualizzazione senza uscire completamente da.</span><span class="sxs-lookup"><span data-stu-id="32323-315">As the user moves, the content will stay within an easy glance by sliding towards the edge of the view without completely leaving.</span></span> <span data-ttu-id="32323-316">Quando l'utente gazes verso l'oggetto tag-along, viene visualizzata più dettagliatamente nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="32323-316">When the user gazes towards the tag-along object, it comes more fully into view.</span></span>

<span data-ttu-id="32323-317">Si userà il **SimpleTagalong.cs** file che conterrà:</span><span class="sxs-lookup"><span data-stu-id="32323-317">We're going to use the **SimpleTagalong.cs** file which will:</span></span>

1. <span data-ttu-id="32323-318">Determinare se l'oggetto Tag-Along è entro i limiti della fotocamera.</span><span class="sxs-lookup"><span data-stu-id="32323-318">Determine if the Tag-Along object is within the camera bounds.</span></span>
2. <span data-ttu-id="32323-319">In caso contrario all'interno del cono di visualizzazione, posizionare il Tag-Along per parzialmente all'interno del cono di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="32323-319">If not within the view frustum, position the Tag-Along to partially within the view frustum.</span></span>
3. <span data-ttu-id="32323-320">In caso contrario, posizionare il Tag-Along a una distanza predefinita da parte dell'utente.</span><span class="sxs-lookup"><span data-stu-id="32323-320">Otherwise, position the Tag-Along to a default distance from the user.</span></span>

<span data-ttu-id="32323-321">A tale scopo, è innanzitutto necessario modificare il **Interactible.cs** script per chiamare le **TagalongAction**.</span><span class="sxs-lookup"><span data-stu-id="32323-321">To do this, we first must change the **Interactible.cs** script to call the **TagalongAction**.</span></span>

1. <span data-ttu-id="32323-322">Modificare **Interactible.cs** esercitare 6.a (rimozione di commenti linee 84 a 87) al completamento della scrittura di codice.</span><span class="sxs-lookup"><span data-stu-id="32323-322">Edit **Interactible.cs** by completing coding exercise 6.a (uncommenting lines 84 to 87).</span></span>

```cs
/* TODO: DEVELOPER CODING EXERCISE 6.a */
// 6.a: Uncomment the lines below to perform a Tagalong action.
if (interactibleAction != null)
{
    interactibleAction.PerformAction();
}
```

<span data-ttu-id="32323-323">Il **InteractibleAction.cs** script, abbinato **Interactible.cs** esegue azioni personalizzate quando si tocca su vntana.</span><span class="sxs-lookup"><span data-stu-id="32323-323">The **InteractibleAction.cs** script, paired with **Interactible.cs** performs custom actions when you tap on holograms.</span></span> <span data-ttu-id="32323-324">In questo caso, si userà uno in particolare per tag-along.</span><span class="sxs-lookup"><span data-stu-id="32323-324">In this case, we'll use one specifically for tag-along.</span></span>

* <span data-ttu-id="32323-325">Nel **gli script** cartella fare clic su **TagalongAction.cs** asset per aprire in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="32323-325">In the **Scripts** folder click on **TagalongAction.cs** asset to open in Visual Studio.</span></span>
* <span data-ttu-id="32323-326">Completare l'esercizio di scrittura di codice o sostituirlo con questo:</span><span class="sxs-lookup"><span data-stu-id="32323-326">Complete the coding exercise or change it to this:</span></span>
  * <span data-ttu-id="32323-327">In cima il **gerarchia**, nel tipo di barra di ricerca **ChestButton_Center** e selezionare il risultato.</span><span class="sxs-lookup"><span data-stu-id="32323-327">At the top of the **Hierarchy**, in the search bar type **ChestButton_Center** and select the result.</span></span>
  * <span data-ttu-id="32323-328">Nel **Inspector** del pannello, fare clic sui **Add Component** pulsante.</span><span class="sxs-lookup"><span data-stu-id="32323-328">In the **Inspector** panel, click the **Add Component** button.</span></span>
  * <span data-ttu-id="32323-329">Nel menu, digitare nella casella di ricerca **abbinato azione**.</span><span class="sxs-lookup"><span data-stu-id="32323-329">In the menu, type in the search box **Tagalong Action**.</span></span> <span data-ttu-id="32323-330">Selezionare il risultato della ricerca.</span><span class="sxs-lookup"><span data-stu-id="32323-330">Select the search result.</span></span>
  * <span data-ttu-id="32323-331">Nelle **Vntana** cartella trovare il **abbinato** asset.</span><span class="sxs-lookup"><span data-stu-id="32323-331">In **Holograms** folder find the **Tagalong** asset.</span></span>
  * <span data-ttu-id="32323-332">Selezionare il **ChestButton_Center** dell'oggetto nel **gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="32323-332">Select the **ChestButton_Center** object in the **Hierarchy**.</span></span> <span data-ttu-id="32323-333">Trascinare e rilasciare il **abbinato** dell'oggetto dal **progetto** pannello il **Inspector** nel **oggetto per abbinato** proprietà.</span><span class="sxs-lookup"><span data-stu-id="32323-333">Drag and drop the **TagAlong** object from the **Project** panel onto the **Inspector** into the **Object To Tagalong** property.</span></span>
  * <span data-ttu-id="32323-334">Trascinare il **azione abbinato** dall'oggetto il **Inspector** nel **azione Interactible** campo il **Interactible** script.</span><span class="sxs-lookup"><span data-stu-id="32323-334">Drag the **Tagalong Action** object from the **Inspector** into the **Interactible Action** field on the **Interactible** script.</span></span>
* <span data-ttu-id="32323-335">Fare doppio clic il **TagalongAction** script per aprirlo in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="32323-335">Double click the **TagalongAction** script to open it in Visual Studio.</span></span>

![Configurazione interactible](images/holograms210-interactible.png)

<span data-ttu-id="32323-337">È necessario aggiungere quanto segue:</span><span class="sxs-lookup"><span data-stu-id="32323-337">We need to add the following:</span></span>

* <span data-ttu-id="32323-338">Aggiungere funzionalità alla funzione PerformAction nello script TagalongAction (ereditato da InteractibleAction).</span><span class="sxs-lookup"><span data-stu-id="32323-338">Add functionality to the PerformAction function in the TagalongAction script (inherited from InteractibleAction).</span></span>
* <span data-ttu-id="32323-339">Aggiungere del billboard all'oggetto gazed a una e impostare l'asse di rotazione a dispersione.</span><span class="sxs-lookup"><span data-stu-id="32323-339">Add billboarding to the gazed-upon object, and set the pivot axis to XY.</span></span>
* <span data-ttu-id="32323-340">Aggiungere quindi Tag-Along semplice all'oggetto.</span><span class="sxs-lookup"><span data-stu-id="32323-340">Then add simple Tag-Along to the object.</span></span>

<span data-ttu-id="32323-341">Ecco la nostra soluzione, dal **TagalongAction.cs**:</span><span class="sxs-lookup"><span data-stu-id="32323-341">Here's our solution, from **TagalongAction.cs**:</span></span>

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

* <span data-ttu-id="32323-342">Prova!</span><span class="sxs-lookup"><span data-stu-id="32323-342">Try it!</span></span> <span data-ttu-id="32323-343">Compilare e distribuire l'app.</span><span class="sxs-lookup"><span data-stu-id="32323-343">Build and deploy the app.</span></span>
* <span data-ttu-id="32323-344">Guarda come il contenuto seguente al centro del punto di sguardo, ma non in modo continuo e senza l'origine del blocco.</span><span class="sxs-lookup"><span data-stu-id="32323-344">Watch how the content follows the center of the gaze point, but not continuously and without blocking it.</span></span>

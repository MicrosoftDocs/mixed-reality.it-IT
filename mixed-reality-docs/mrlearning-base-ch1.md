---
title: Esercitazioni introduttive - 2 Inizializzazione del progetto e prima applicazione
description: Completa questo corso per informazioni su come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 11/01/2019
ms.topic: article
ms.localizationpriority: high
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 9c219313ad6e73cde78efd8e5e718a466ebd6137
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2020
ms.locfileid: "77554401"
---
# <a name="2-initializing-your-project-and-first-application"></a><span data-ttu-id="d4c99-105">2. Inizializzazione del progetto e prima applicazione</span><span class="sxs-lookup"><span data-stu-id="d4c99-105">2. Initializing your project and first application</span></span>

## <a name="overview"></a><span data-ttu-id="d4c99-106">Panoramica</span><span class="sxs-lookup"><span data-stu-id="d4c99-106">Overview</span></span>

<!-- TODO: Consider expanding to include summary of each tutorial in this tutorial series -->
<span data-ttu-id="d4c99-107">In questa prima esercitazione apprenderai alcune delle funzionalità offerte da <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a>, inizierai a creare la tua prima applicazione per HoloLens 2 e la distribuirai nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="d4c99-107">In this first tutorial, you will learn about some of the capabilities the <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> has to offer, start your first application for the HoloLens 2, and deploy it to the device.</span></span>

## <a name="objectives"></a><span data-ttu-id="d4c99-108">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="d4c99-108">Objectives</span></span>

* <span data-ttu-id="d4c99-109">Configurare Unity per lo sviluppo per HoloLens</span><span class="sxs-lookup"><span data-stu-id="d4c99-109">Configure Unity for HoloLens development</span></span>
* <span data-ttu-id="d4c99-110">Importare gli asset e configurare la scena</span><span class="sxs-lookup"><span data-stu-id="d4c99-110">Import assets and set up the scene</span></span>
* <span data-ttu-id="d4c99-111">Visualizzare la mesh di mapping spaziale, le mesh manuali e il contatore della frequenza dei fotogrammi</span><span class="sxs-lookup"><span data-stu-id="d4c99-111">Visualization of the spatial mapping mesh, hand meshes, and the framerate counter</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d4c99-112">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="d4c99-112">Prerequisites</span></span>

* <span data-ttu-id="d4c99-113">Un PC Windows 10 configurato in cui siano [installati gli strumenti](install-the-tools.md) corretti</span><span class="sxs-lookup"><span data-stu-id="d4c99-113">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="d4c99-114">Windows 10 SDK 10.0.18362.0 o versioni successive</span><span class="sxs-lookup"><span data-stu-id="d4c99-114">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="d4c99-115">Alcune funzionalità di programmazione C# di base</span><span class="sxs-lookup"><span data-stu-id="d4c99-115">Some basic C# programming ability</span></span>
* <span data-ttu-id="d4c99-116">Un dispositivo HoloLens 2 [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="d4c99-116">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="d4c99-117"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.2.X installato e il modulo di supporto delle compilazioni UWP (Universal Windows Platform) aggiunto</span><span class="sxs-lookup"><span data-stu-id="d4c99-117"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d4c99-118">La versione di Unity consigliata per questa serie di esercitazioni è Unity 2019.2.X.</span><span class="sxs-lookup"><span data-stu-id="d4c99-118">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="d4c99-119">Questa istruzione sostituisce gli eventuali requisiti o suggerimenti relativi alla versione di Unity indicati negli argomenti visualizzabili facendo clic sui collegamenti dei prerequisiti sopra riportati.</span><span class="sxs-lookup"><span data-stu-id="d4c99-119">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="create-new-unity-project"></a><span data-ttu-id="d4c99-120">Creare un nuovo progetto Unity</span><span class="sxs-lookup"><span data-stu-id="d4c99-120">Create new Unity project</span></span>

<span data-ttu-id="d4c99-121">Avvia **Unity Hub**, seleziona la scheda **Projects** (Progetti) e fai clic sulla **freccia giù** accanto al pulsante **New** (Nuovo):</span><span class="sxs-lookup"><span data-stu-id="d4c99-121">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-1.png)

<span data-ttu-id="d4c99-123">Seleziona la versione di Unity specificata più indietro nella sezione [Prerequisiti](#prerequisites):</span><span class="sxs-lookup"><span data-stu-id="d4c99-123">Select the Unity version specified in the [Prerequisites](#prerequisites) section above:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-2.png)

<span data-ttu-id="d4c99-125">Nella finestra Create a new project (Crea un nuovo progetto):</span><span class="sxs-lookup"><span data-stu-id="d4c99-125">In the Create a new project window:</span></span>

* <span data-ttu-id="d4c99-126">Assicurati che in **Templates** (Modelli) sia impostata l'opzione **3D**</span><span class="sxs-lookup"><span data-stu-id="d4c99-126">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="d4c99-127">Immetti un nome appropriato nel campo **Project Name** (Nome progetto), ad esempio _MRTK Tutorials_</span><span class="sxs-lookup"><span data-stu-id="d4c99-127">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="d4c99-128">Nel campo **Location** (Percorso) scegli un percorso appropriato in cui archiviare il progetto, ad esempio _D:\MixedRealityLearning_</span><span class="sxs-lookup"><span data-stu-id="d4c99-128">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="d4c99-129">Fai clic sul pulsante **Create** (Crea) per creare e avviare il nuovo progetto Unity</span><span class="sxs-lookup"><span data-stu-id="d4c99-129">Click the **Create** button to create and launch your new Unity project</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="d4c99-131">Se lavori in Windows, tieni presente che è previsto un limite (MAX_PATH) di 255 caratteri per il percorso.</span><span class="sxs-lookup"><span data-stu-id="d4c99-131">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="d4c99-132">Questi limiti incidono su Unity, pertanto la compilazione potrebbe avere esito negativo se un percorso file qualsiasi è costituito da più di 255 caratteri.</span><span class="sxs-lookup"><span data-stu-id="d4c99-132">Unity is affected by these limits and may fail to compile if any file path is longer than 255 characters.</span></span> <span data-ttu-id="d4c99-133">Di conseguenza, è consigliabile archiviare il progetto Unity nel percorso più vicino possibile alla radice dell'unità.</span><span class="sxs-lookup"><span data-stu-id="d4c99-133">Consequently, it is strongly recommended to store your Unity project as close to the root of the drive as possible.</span></span>

<span data-ttu-id="d4c99-134">Attendi che Unity crei il progetto:</span><span class="sxs-lookup"><span data-stu-id="d4c99-134">Wait for Unity to create the project:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-4.png)

## <a name="configure-the-unity-project-for-windows-mixed-reality"></a><span data-ttu-id="d4c99-136">Configurare il progetto Unity per Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="d4c99-136">Configure the Unity project for Windows Mixed Reality</span></span>

<!-- TODO: Consider adding info about configuring Unity for WMR vs MRTK, or removing WMR section -->

<span data-ttu-id="d4c99-137">In questa sezione cambierai piattaforma di compilazione e abiliterai sia la realtà virtuale che la percezione spaziale.</span><span class="sxs-lookup"><span data-stu-id="d4c99-137">In this section, you will switch build platform, enable virtual reality, and enable spatial perception.</span></span>

### <a name="1-switch-build-platform"></a><span data-ttu-id="d4c99-138">1. Cambiare piattaforma di compilazione</span><span class="sxs-lookup"><span data-stu-id="d4c99-138">1. Switch build platform</span></span>

<span data-ttu-id="d4c99-139">Dal menu di Unity scegli **File** > **Build Settings** (Impostazioni di compilazione) per visualizzare la finestra corrispondente:</span><span class="sxs-lookup"><span data-stu-id="d4c99-139">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-1.png)

<span data-ttu-id="d4c99-141">Nella finestra Build Settings (Impostazioni di compilazione), seleziona **Universal Windows Platform** e fai clic sul pulsante **Switch Platform** (Cambia piattaforma):</span><span class="sxs-lookup"><span data-stu-id="d4c99-141">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-2.png)

<span data-ttu-id="d4c99-143">Attendi che Unity completi il passaggio all'altra piattaforma:</span><span class="sxs-lookup"><span data-stu-id="d4c99-143">Wait for Unity to finish switching the platform:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-3.png)

<span data-ttu-id="d4c99-145">Una volta completato il passaggio all'altra piattaforma, fai clic sull'icona **x** di colore rosso per chiudere la finestra Build Settings (Impostazioni di compilazione):</span><span class="sxs-lookup"><span data-stu-id="d4c99-145">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-4.png)

### <a name="2-enable-virtual-reality"></a><span data-ttu-id="d4c99-147">2. Abilitare la realtà virtuale</span><span class="sxs-lookup"><span data-stu-id="d4c99-147">2. Enable virtual reality</span></span>

> [!NOTE]
> <span data-ttu-id="d4c99-148">L'abilitazione della realtà virtuale si applica anche ai visori VR di realtà mista e realtà aumentata perché riguarda l'abilitazione della visione stereoscopica, ovvero il rendering di immagini diverse per ogni occhio.</span><span class="sxs-lookup"><span data-stu-id="d4c99-148">Enabling virtual reality also applies to mixed reality and augmented reality headsets because it refers to enabling stereoscopic vision, i.e. rendering different images for each eye.</span></span>

<span data-ttu-id="d4c99-149">Dal menu di Unity scegli **Edit** (Modifica) > **Project Settings** (Impostazioni del progetto) per visualizzare la finestra corrispondente:</span><span class="sxs-lookup"><span data-stu-id="d4c99-149">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-1.png)

<span data-ttu-id="d4c99-151">Nella finestra Project Settings (Impostazioni del progetto), seleziona **Player** (Riproduttore) > **XR Settings** (Impostazioni XR) per espandere tali impostazioni:</span><span class="sxs-lookup"><span data-stu-id="d4c99-151">In the Project Settings window, select **Player** > **XR Settings** to expand the XR Settings:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-2.png)

<span data-ttu-id="d4c99-153">In XR Settings (Impostazioni XR), seleziona la casella di controllo **Virtual Reality Supported** (Realtà virtuale supportata) per abilitare la realtà virtuale e quindi fai clic sull'icona **+** e seleziona **Windows Mixed Reality** per aggiungere Windows Mixed Reality SDK:</span><span class="sxs-lookup"><span data-stu-id="d4c99-153">In the XR Settings, check the **Virtual Reality Supported** checkbox to enable virtual reality, then click the **+** icon and select **Windows Mixed Reality** to add the Windows Mixed Reality SDK:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-3.png)

<span data-ttu-id="d4c99-155">Attendi che Unity termini di aggiungere l'SDK:</span><span class="sxs-lookup"><span data-stu-id="d4c99-155">Wait for Unity to finish adding the SDK:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-4.png)

<span data-ttu-id="d4c99-157">Al termine dell'aggiunta dell'SDK, ottimizza le impostazioni XR come illustrato di seguito:</span><span class="sxs-lookup"><span data-stu-id="d4c99-157">When Unity has finished adding the SDK, optimize the XR Settings as follows:</span></span>

* <span data-ttu-id="d4c99-158">Nella sezione Windows Mixed Reality, imposta il campo **Depth Format** (Formato profondità) su **16-bit depth** (Profondità a 16 bit)</span><span class="sxs-lookup"><span data-stu-id="d4c99-158">Set Windows Mixed Reality **Depth Format** to **16-bit depth**</span></span>
* <span data-ttu-id="d4c99-159">Sempre nella sezione Windows Mixed Reality, seleziona la casella di controllo **Enable Depth Sharing** (Abilita condivisione profondità)</span><span class="sxs-lookup"><span data-stu-id="d4c99-159">Check the Windows Mixed Reality **Enable Depth Sharing** checkbox</span></span>
* <span data-ttu-id="d4c99-160">Imposta il campo **Stereo Rendering Mode\*** (Modalità di rendering stereo) su **Single Pass Instanced** (Con creazione delle istanze in un unico passaggio)</span><span class="sxs-lookup"><span data-stu-id="d4c99-160">Set Stereo **Rendering Mode\*** to **Single Pass Instanced**</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-5.png)

> [!TIP]
> <span data-ttu-id="d4c99-162">Per altre informazioni sull'ottimizzazione di Unity per Windows Mixed Reality, puoi fare riferimento all'argomento [Impostazioni consigliate per Unity](recommended-settings-for-unity.md).</span><span class="sxs-lookup"><span data-stu-id="d4c99-162">To learn more about optimizing Unity for Windows Mixed Reality, you can refer to the [Recommended settings for Unity](recommended-settings-for-unity.md) documentation.</span></span>

### <a name="3-enable-spatial-perception"></a><span data-ttu-id="d4c99-163">3. Abilitare la percezione spaziale</span><span class="sxs-lookup"><span data-stu-id="d4c99-163">3. Enable spatial perception</span></span>

> [!NOTE]
> <span data-ttu-id="d4c99-164">La percezione spaziale consente la visualizzazione della mesh di mapping spaziale nei dispositivi Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="d4c99-164">Spatial perception allows visualization of the spatial mapping mesh on Windows Mixed Reality devices.</span></span>

<span data-ttu-id="d4c99-165">Nella finestra Project Settings (Impostazioni del progetto), seleziona **Player** (Riproduttore) > **Publishing Settings** (Impostazioni di pubblicazione) per espandere tali impostazioni:</span><span class="sxs-lookup"><span data-stu-id="d4c99-165">In the Project Settings window, select **Player** > **Publishing Settings** to expand the Publishing Settings:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step3-1.png)

<span data-ttu-id="d4c99-167">In Publishing Settings (Impostazioni di pubblicazione), scorri verso il basso fino alla sezione **Capabilities** (Funzionalità) e seleziona la casella di controllo **SpatialPerception**:</span><span class="sxs-lookup"><span data-stu-id="d4c99-167">In the Publishing Settings, scroll down to the **Capabilities** section and check the **SpatialPerception** checkbox:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step3-2.png)

<!-- TODO: Consider adding info about audio spatializer plugin setting -->

<span data-ttu-id="d4c99-169">Chiudi la finestra Project Settings (Impostazioni del progetto).</span><span class="sxs-lookup"><span data-stu-id="d4c99-169">Close the Project Settings window.</span></span>

## <a name="import-textmesh-pro-essential-resources"></a><span data-ttu-id="d4c99-170">Importare le risorse essenziali TextMesh Pro</span><span class="sxs-lookup"><span data-stu-id="d4c99-170">Import TextMesh Pro Essential Resources</span></span>

> [!NOTE]
> <span data-ttu-id="d4c99-171">Questo pacchetto viene importato perché è necessario per gli elementi dell'interfaccia utente di Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="d4c99-171">We are importing this package because it is required by Mixed Reality Toolkit's UI elements.</span></span>

<span data-ttu-id="d4c99-172">Dal menu di Unity scegli **Window** (Finestra) > **TextMeshPro** > **Import TMP Essential Resources** (Importa le risorse essenziali TMP):</span><span class="sxs-lookup"><span data-stu-id="d4c99-172">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section3-step1-1.png)

<span data-ttu-id="d4c99-174">Nella finestra Import Unity Package (Importa il pacchetto Unity), fai clic sul pulsante **All** (Tutti) per assicurarti che vengano selezionati tutti gli asset e quindi fai clic sul pulsante **Import** (Importa) per importare gli asset:</span><span class="sxs-lookup"><span data-stu-id="d4c99-174">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section3-step1-2.png)

## <a name="import-the-mixed-reality-toolkit"></a><span data-ttu-id="d4c99-176">Importare Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="d4c99-176">Import the Mixed Reality Toolkit</span></span>

<span data-ttu-id="d4c99-177">Scarica il pacchetto personalizzato di Unity:</span><span class="sxs-lookup"><span data-stu-id="d4c99-177">Download the Unity custom package:</span></span>

* [<span data-ttu-id="d4c99-178">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="d4c99-178">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage)

<span data-ttu-id="d4c99-179">Dal menu di Unity scegli **Assets** (Asset) > **Import Package** (Importa il pacchetto) > **Custom Package** (Pacchetto personalizzato) per visualizzare la finestra Import package (Importa il pacchetto):</span><span class="sxs-lookup"><span data-stu-id="d4c99-179">In the Unity menu, select **Assets** > **Import Package** > **Custom Package...** to open the Import package... window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-1.png)

<span data-ttu-id="d4c99-181">Nella finestra Import package (Importa il pacchetto) seleziona il pacchetto **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage** scaricato e fai clic sul pulsante **Open** (Apri):</span><span class="sxs-lookup"><span data-stu-id="d4c99-181">In the Import package... window, select the **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage** you downloaded and click the **Open** button:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-2.png)

<span data-ttu-id="d4c99-183">Nella finestra Import Unity Package (Importa il pacchetto Unity), fai clic sul pulsante **All** (Tutti) per assicurarti che vengano selezionati tutti gli asset e quindi fai clic sul pulsante **Import** (Importa) per importare gli asset:</span><span class="sxs-lookup"><span data-stu-id="d4c99-183">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-3.png)

## <a name="configure-the-unity-project-for-the-mixed-reality-toolkit"></a><span data-ttu-id="d4c99-185">Configurare il progetto Unity per Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="d4c99-185">Configure the Unity project for the Mixed Reality Toolkit</span></span>

<!-- TODO: Consider adding info about configuring Unity for WMR vs MRTK, or removing WMR section -->

<span data-ttu-id="d4c99-186">Dopo che il pacchetto è stato importato, dovrebbe venire visualizzata la finestra MRTK Project Configurator (Configuratore del progetto MRTK).</span><span class="sxs-lookup"><span data-stu-id="d4c99-186">After the package has been imported, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="d4c99-187">In caso contrario, visualizza tale finestra scegliendo **Mixed Reality Toolkit** > **Utilities** (Utilità) > **Configure Unity Project** (Configura il progetto Unity) dal menu di Unity.</span><span class="sxs-lookup"><span data-stu-id="d4c99-187">If it does not, open it by selecting **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** in the Unity menu.</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section5-step1-1.png)

<span data-ttu-id="d4c99-189">Nella finestra MRTK Project Configurator (Configuratore del progetto MRTK), espandi la sezione **Modify Configurations** (Modifica configurazioni), <u>deseleziona</u> la casella di controllo **Enable MSBuild for Unity** (Abilita MSBuild per Unity), verifica che tutte le altre opzioni siano selezionate e fai clic sul pulsante **Apply** (Applica) per applicare le impostazioni:</span><span class="sxs-lookup"><span data-stu-id="d4c99-189">In the MRTK Project Configurator window, expand the **Modify Configurations** section, <u>uncheck</u> the **Enable MSBuild for Unity** checkbox, ensure all other options are checked, and click the **Apply** button to apply the settings:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section5-step1-2.png)

> [!CAUTION]
> <span data-ttu-id="d4c99-191">MSBuild per Unity potrebbe non supportare tutti gli SDK che userai ed essere difficile da disabilitare dopo che è stato abilitato.</span><span class="sxs-lookup"><span data-stu-id="d4c99-191">MSBuild for Unity may not support all SDKs you will be using and can be challenging to disable after it has been enabled.</span></span> <span data-ttu-id="d4c99-192">Di conseguenza, è consigliabile non abilitare MSBuild per Unity.</span><span class="sxs-lookup"><span data-stu-id="d4c99-192">Consequently, it is strongly recommended to not enable MSBuild for Unity.</span></span>

## <a name="configure-the-mixed-reality-toolkit"></a><span data-ttu-id="d4c99-193">Configurare Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="d4c99-193">Configure the Mixed Reality Toolkit</span></span>
<!-- TODO: Consider renaming to 'Add the Mixed Reality Toolkit to the Unity scene' -->

<span data-ttu-id="d4c99-194">Dal menu di Unity scegli **Mixed Reality Toolkit** > **Add to Scene and Configure** (Aggiungi alla scena e configura) per aggiungere Mixed Reality Toolkit alla scena corrente:</span><span class="sxs-lookup"><span data-stu-id="d4c99-194">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...** to add the Mixed Reality Toolkit to your current scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-1.png)

<span data-ttu-id="d4c99-196">Con l'oggetto MixedRealityToolkit selezionato nella finestra Hierarchy (Gerarchia), nella finestra Inspector (Controllo) verifica che il profilo di configurazione di Mixed Reality Toolkit sia impostato su **DefaultMixedRealityToolkitConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="d4c99-196">With the MixedRealityToolkit object selected in the Hierarchy window, in the Inspector window, verify the Mixed Reality Toolkit configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-2.png)

> [!IMPORTANT]
> <span data-ttu-id="d4c99-198">In genere, durante le attività di sviluppo per HoloLens 2 si usa DefaultHoloLens2ConfigurationProfile.</span><span class="sxs-lookup"><span data-stu-id="d4c99-198">Typically, you will use the DefaultHoloLens2ConfigurationProfile when developing for HoloLens 2.</span></span> <span data-ttu-id="d4c99-199">Tuttavia, ai fini di questa esercitazione, userai DefaultMixedRealityToolkitConfigurationProfile, mentre nell'esercitazione successiva, [Creazione dell'interfaccia utente e configurazione di Mixed Reality Toolkit](mrlearning-base-ch2.md), passerai a DefaultHoloLens2ConfigurationProfile.</span><span class="sxs-lookup"><span data-stu-id="d4c99-199">However, for the purpose of this tutorial, you will use the DefaultMixedRealityToolkitConfigurationProfile, then in the next tutorial, [Creating user interface and configure Mixed Reality Toolkit](mrlearning-base-ch2.md), you will change to the DefaultHoloLens2ConfigurationProfile.</span></span>

<span data-ttu-id="d4c99-200">Dal menu di Unity scegli **File** > **Save As** (Salva con nome) per visualizzare la finestra Save Scene (Salva la scena):</span><span class="sxs-lookup"><span data-stu-id="d4c99-200">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-3.png)

<span data-ttu-id="d4c99-202">Nella finestra Save Scene (Salva la scena) passa alla cartella **Scenes** (Scene) del progetto, assegna alla scena un nome appropriato, ad esempio _GettingStarted_, e fai clic sul pulsante **Save** (Salva) per salvare la scena:</span><span class="sxs-lookup"><span data-stu-id="d4c99-202">In the Save Scene window, navigate to your project's **Scenes** folder, give your scene a suitable name, for example, _GettingStarted_, and click the **Save** button to save the scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-4.png)

## <a name="build-your-application-to-your-device"></a><span data-ttu-id="d4c99-204">Compilare l'applicazione nel dispositivo</span><span class="sxs-lookup"><span data-stu-id="d4c99-204">Build your application to your device</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="d4c99-205">1. Compilare il progetto Unity</span><span class="sxs-lookup"><span data-stu-id="d4c99-205">1. Build the Unity project</span></span>

<span data-ttu-id="d4c99-206">Dal menu di Unity scegli **File** > **Build Settings** (Impostazioni di compilazione) per visualizzare la finestra corrispondente.</span><span class="sxs-lookup"><span data-stu-id="d4c99-206">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="d4c99-207">Nella finestra Build Settings (Impostazioni di compilazione), fai clic sul pulsante **Add Open Scenes** (Aggiungi scene aperte) per aggiungere la scena corrente all'elenco **Scenes In Build** (Scene in compilazione) e quindi fai clic sul pulsante **Build** (Compila) per visualizzare la finestra Build Universal Windows Platform (Compilazione UWP):</span><span class="sxs-lookup"><span data-stu-id="d4c99-207">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-1.png)

<span data-ttu-id="d4c99-209">Nella finestra Build Universal Windows Platform (Compilazione UWP), scegli un percorso appropriato in cui archiviare la compilazione, ad esempio _D:\MixedRealityLearning\Builds_, crea una nuova cartella e assegnale un nome adatto (ad esempio, _GettingStarted_) e quindi fai clic sul pulsante **Select Folder** (Seleziona cartella) per avviare il processo di compilazione:</span><span class="sxs-lookup"><span data-stu-id="d4c99-209">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-2.png)

<span data-ttu-id="d4c99-211">Attendi che Unity completi il processo di compilazione:</span><span class="sxs-lookup"><span data-stu-id="d4c99-211">Wait for Unity to finish the build process:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="d4c99-213">2. Compilare e distribuire l'applicazione</span><span class="sxs-lookup"><span data-stu-id="d4c99-213">2. Build and deploy the application</span></span>

<span data-ttu-id="d4c99-214">Al termine del processo di compilazione, Unity richiederà a Esplora file di Windows di aprire il percorso in cui è stata archiviata la compilazione.</span><span class="sxs-lookup"><span data-stu-id="d4c99-214">When the build process is completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="d4c99-215">Spostati all'interno della cartella e fai doppio clic sul file della soluzione per aprirlo in Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="d4c99-215">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-1.png)

> [!NOTE]
> <span data-ttu-id="d4c99-217">Se Visual Studio chiede di installare nuovi componenti, dedica qualche minuto a verificare che siano installati tutti i componenti indispensabili come specificato nell'argomento [Installare gli strumenti](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="d4c99-217">If Visual Studio asks you to install new components, take a moment to ensure that all prerequisite components are installed as specified in the [Install the Tools](install-the-tools.md) documentation.</span></span>

<span data-ttu-id="d4c99-218">Configura Visual Studio per HoloLens 2 selezionando la configurazione **Master** o **Release**, l'architettura **ARM** e **Dispositivo** come destinazione.</span><span class="sxs-lookup"><span data-stu-id="d4c99-218">Configure Visual Studio for HoloLens 2 by selecting the **Master** or **Release** configuration, the **ARM** architecture, and **Device** as target:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-2.png)

<span data-ttu-id="d4c99-220">Connetti il dispositivo HoloLens 2 al computer.</span><span class="sxs-lookup"><span data-stu-id="d4c99-220">Connect your HoloLens 2 to your computer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d4c99-221">Prima della compilazione nel dispositivo, quest'ultimo deve essere in modalità sviluppatore e associato al computer di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="d4c99-221">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="d4c99-222">Per completare i due passaggi segui [queste istruzioni](using-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="d4c99-222">Both of these steps can be completed by following [these instructions](using-visual-studio.md).</span></span>

<span data-ttu-id="d4c99-223">Il passaggio finale consiste nel compilare e distribuire l'applicazione nel dispositivo selezionando **Debug** > **Avvia senza eseguire debug**:</span><span class="sxs-lookup"><span data-stu-id="d4c99-223">The final step is to build and deploy to your device by selecting **Debug** > **Start Without Debugging**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-3.png)

<span data-ttu-id="d4c99-225">Anche se queste istruzioni presuppongono che tu distribuisca l'applicazione in un dispositivo HoloLens 2, puoi anche distribuirla nell'[emulatore HoloLens 2](using-the-hololens-emulator.md) oppure creare un [pacchetto dell'app per il trasferimento locale](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>).</span><span class="sxs-lookup"><span data-stu-id="d4c99-225">While these instructions assume you will be deploying to a HoloLens 2 device, you can also deploy to the [HoloLens 2 emulator](using-the-hololens-emulator.md) or create an [app package for sideloading](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>).</span></span>

<span data-ttu-id="d4c99-226">Quando selezioni Avvia senza eseguire debug, l'applicazione viene avviata immediatamente nel dispositivo al termine della compilazione (se questa ha esito positivo), ma senza il debugger associato e senza che in Visual Studio vengano visualizzate le informazioni di debug.</span><span class="sxs-lookup"><span data-stu-id="d4c99-226">Selecting Start without Debugging causes the application to immediately start on your device upon a successful build, but without the debugger attached and information appearing in Visual Studio.</span></span> <span data-ttu-id="d4c99-227">Questo significa anche che, mentre l'applicazione è in esecuzione sul dispositivo HoloLens 2, puoi disconnettere il cavo USB senza arrestare l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="d4c99-227">This also means that you can disconnect your USB cable while your application is running on your HoloLens 2 without stopping the application.</span></span>

<span data-ttu-id="d4c99-228">Per distribuire l'applicazione nel dispositivo senza che venga avviata automaticamente, puoi selezionare Compila > Distribuisci soluzione.</span><span class="sxs-lookup"><span data-stu-id="d4c99-228">To deploy to your device without having the application start automatically, you can select Build > Deploy Solution.</span></span>

## <a name="congratulations"></a><span data-ttu-id="d4c99-229">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="d4c99-229">Congratulations</span></span>

<!-- TODO: Consider cleanup and adding in app screenshots -->
<span data-ttu-id="d4c99-230">A questo punto hai distribuito la tua prima applicazione per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="d4c99-230">You have now deployed your first HoloLens 2 application.</span></span> <span data-ttu-id="d4c99-231">Esplorando, noterai una mesh di mapping spaziale che copre tutte le superfici percepite da HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="d4c99-231">As you walk around, you should see a spatial mapping mesh covering all the surfaces that have been perceived by the HoloLens 2.</span></span> <span data-ttu-id="d4c99-232">Dovresti anche vedere indicatori sulle mani e sulle dita per il tracciamento delle mani e un contatore della frequenza dei fotogrammi per tenere sotto controllo le prestazioni dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="d4c99-232">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on application performance.</span></span> <span data-ttu-id="d4c99-233">Questi sono solo alcuni degli elementi fondamentali, inclusi per impostazione predefinita in Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="d4c99-233">These are just a few of the foundational pieces, included out of the box, with the Mixed Reality Toolkit.</span></span> <span data-ttu-id="d4c99-234">Nelle esercitazioni successive inizierai ad aggiungere più contenuti e interattività alla scena, in modo da poter esplorare completamente le funzionalità di HoloLens 2 e Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="d4c99-234">In the tutorials to come, you will start adding more content and interactivity to your scene so that you can fully explore the capabilities of HoloLens 2 and the Mixed Reality Toolkit.</span></span>

> [!NOTE]
> <span data-ttu-id="d4c99-235">Nell'app puoi notare il profiler di diagnostica. Puoi disattivarne la visibilità tramite il comando vocale di **disattivazione diagnostica**.</span><span class="sxs-lookup"><span data-stu-id="d4c99-235">In the app, you may notice the Diagnostics profiler, you can toggle it's visibility using the speech command **Toogle Diagnostics**.</span></span> <span data-ttu-id="d4c99-236">Tuttavia, in genere è consigliabile lasciare visibile il profiler in qualsiasi momento durante le attività di sviluppo per comprendere quando le modifiche apportate all'app possono aver avuto conseguenze sulle prestazioni, ad esempio l'applicazione HoloLens 2 deve essere [eseguita in modo continuo a 60 FPS](understanding-performance-for-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="d4c99-236">However, it is generally recommended to keep the profiler visible at all times during development to understand when changes to the app may have impacted performance, for example, HoloLens 2 application should [continuously run at 60 FPS](understanding-performance-for-mixed-reality.md).</span></span>

[<span data-ttu-id="d4c99-237">Esercitazione successiva: 3. Creazione dell'interfaccia utente e configurazione di Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="d4c99-237">Next Tutorial: 3. Creating user interface and configure Mixed Reality Toolkit</span></span>](mrlearning-base-ch2.md)

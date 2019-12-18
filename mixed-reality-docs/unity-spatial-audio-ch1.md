---
title: Esercitazioni audio spaziali-1. Aggiunta di audio spaziale al progetto
description: Aggiungere il plug-in Microsoft Spatializer al progetto Unity per accedere a HoloLens 2 HRTF hardware offload.
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: realtà mista, Unity, esercitazione, hololens2, audio spaziale
ms.openlocfilehash: 8978017b3ce6c49a81b3eee2fe21e9234f4e71f0
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182798"
---
# <a name="adding-spatial-audio-to-your-unity-project"></a><span data-ttu-id="aee84-105">Aggiunta di audio spaziale al progetto Unity</span><span class="sxs-lookup"><span data-stu-id="aee84-105">Adding spatial audio to your Unity project</span></span>

<span data-ttu-id="aee84-106">Benvenuti in tutioral audio spaziali per Unity in HoloLens2.</span><span class="sxs-lookup"><span data-stu-id="aee84-106">Welcome to the spatial audio tutioral for Unity on HoloLens2.</span></span> <span data-ttu-id="aee84-107">Questa sequenza di esercitazione Mostra:</span><span class="sxs-lookup"><span data-stu-id="aee84-107">This tutorial sequence shows:</span></span>
* <span data-ttu-id="aee84-108">Come usare l'offload HRTF in HoloLens 2 in Unity</span><span class="sxs-lookup"><span data-stu-id="aee84-108">How to use HRTF offload on HoloLens 2 in Unity</span></span>
* <span data-ttu-id="aee84-109">Come abilitare il riverbero quando si usa l'offload HRTF</span><span class="sxs-lookup"><span data-stu-id="aee84-109">How to enable reverb when using HRTF offload</span></span>

<span data-ttu-id="aee84-110">Il [repository GitHub Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity) include un progetto Unity completato di questa sequenza di esercitazione.</span><span class="sxs-lookup"><span data-stu-id="aee84-110">The [Microsoft Spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity) has a completed Unity project of this tutorial sequence.</span></span> 

<span data-ttu-id="aee84-111">Per indicazioni su quando può essere utile per spatialize i suoni, vedere Progettazione di suoni [spaziali](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design).</span><span class="sxs-lookup"><span data-stu-id="aee84-111">For our recommendations on when it can be helpful to spatialize sounds, see [spatial sound design](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design).</span></span>

## <a name="objectives"></a><span data-ttu-id="aee84-112">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="aee84-112">Objectives</span></span>
<span data-ttu-id="aee84-113">In questo primo capitolo, verranno illustrate le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="aee84-113">In this first chapter, you'll:</span></span>
* <span data-ttu-id="aee84-114">Creare un progetto Unity e importare MRTK</span><span class="sxs-lookup"><span data-stu-id="aee84-114">Create a Unity project and import MRTK</span></span>
* <span data-ttu-id="aee84-115">Importare il plug-in Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="aee84-115">Import the Microsoft spatializer plugin</span></span>
* <span data-ttu-id="aee84-116">Abilitare il plug-in Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="aee84-116">Enable the Microsoft spatializer plugin</span></span>
* <span data-ttu-id="aee84-117">Abilitare l'audio spaziale nella workstation per sviluppatori</span><span class="sxs-lookup"><span data-stu-id="aee84-117">Enable spatial audio on your developer workstation</span></span>

## <a name="create-a-project-and-add-nuget-for-unity"></a><span data-ttu-id="aee84-118">Creare un progetto e aggiungere NuGet per Unity</span><span class="sxs-lookup"><span data-stu-id="aee84-118">Create a project and add NuGet for Unity</span></span>
<span data-ttu-id="aee84-119">Iniziare con un progetto Unity vuoto, quindi aggiungere e configurare NuGet per Unity:</span><span class="sxs-lookup"><span data-stu-id="aee84-119">Start with an empty Unity project, then add and configure NuGet for Unity:</span></span>
1. <span data-ttu-id="aee84-120">Scaricare la versione più recente di [NuGetForUnity. file unitypackage Tools](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)</span><span class="sxs-lookup"><span data-stu-id="aee84-120">Download the latest [NuGetForUnity .unitypackage](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)</span></span>
2. <span data-ttu-id="aee84-121">Nella barra dei menu di Unity fare clic su **Asset-> importa pacchetto-> pacchetto personalizzato...** e installare il pacchetto NuGetForUnity:</span><span class="sxs-lookup"><span data-stu-id="aee84-121">In the Unity menu bar, click **Assets -> Import Package -> Custom Package...** and install the NuGetForUnity package:</span></span>

![Importa pacchetto personalizzato](images/spatial-audio/import-custom-package.png)

## <a name="add-the-windows-mixed-reality-package"></a><span data-ttu-id="aee84-123">Aggiungere il pacchetto di realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="aee84-123">Add the Windows Mixed Reality package</span></span>
<span data-ttu-id="aee84-124">Il supporto della realtà mista di Windows in Unity 2019 e versioni successive è incluso in un pacchetto facoltativo.</span><span class="sxs-lookup"><span data-stu-id="aee84-124">Windows Mixed Reality support in Unity 2019 and later is contained in an optional package.</span></span> <span data-ttu-id="aee84-125">Per aggiungerlo al progetto, aprire **Gestione pacchetti di > finestra** dalla barra dei menu di Unity:</span><span class="sxs-lookup"><span data-stu-id="aee84-125">To add it to your project, open **Window -> Package Manager** from the Unity menu bar:</span></span>

![Menu di gestione pacchetti](images/spatial-audio/package-manager-menu.png)

<span data-ttu-id="aee84-127">Individuare e installare il pacchetto di **realtà mista di Windows** :</span><span class="sxs-lookup"><span data-stu-id="aee84-127">Then find and install the **Windows Mixed Reality** package:</span></span>

![Finestra di gestione pacchetti](images/spatial-audio/package-manager-window.png)

## <a name="install-mrtk-and-microsoft-spatializer"></a><span data-ttu-id="aee84-129">Installare MRTK e Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="aee84-129">Install MRTK and Microsoft Spatializer</span></span>
<span data-ttu-id="aee84-130">Usando NuGet per Unity, installare i plug-in MRTK e Microsoft Spatializer:</span><span class="sxs-lookup"><span data-stu-id="aee84-130">Using NuGet for Unity, install the MRTK and Microsoft Spatializer plugins:</span></span>
1. <span data-ttu-id="aee84-131">Nella barra dei menu di Unity fare clic su **NuGet-> Gestisci pacchetti NuGet**.</span><span class="sxs-lookup"><span data-stu-id="aee84-131">In the Unity menu bar, click on **NuGet -> Manage NuGet Packages**.</span></span>

![Gestisci pacchetti NuGet](images/spatial-audio/manage-nuget-packages.png)

2. <span data-ttu-id="aee84-133">Nella casella di **ricerca** immettere "Microsoft. MixedReality. Toolkit" e installare il pacchetto MRTK Core: **Microsoft. MixedReality. Toolkit. Foundation**</span><span class="sxs-lookup"><span data-stu-id="aee84-133">In the **Search** box, enter "Microsoft.MixedReality.Toolkit" and install the MRTK core package: **Microsoft.MixedReality.Toolkit.Foundation**</span></span>

![Pacchetto NuGet MRTK](images/spatial-audio/mrtk-nuget-package.png)

<span data-ttu-id="aee84-135">Il [pacchetto NuGet MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html) dispone di contesto e dettagli aggiuntivi.</span><span class="sxs-lookup"><span data-stu-id="aee84-135">[MRTK NuGet Package](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html) has additional context and details.</span></span>

4. <span data-ttu-id="aee84-136">Nella casella di **ricerca** immettere "Microsoft. SpatialAudio" e installare il pacchetto Microsoft Spatializer: **Microsoft. SpatialAudio. Spatializer. Unity**</span><span class="sxs-lookup"><span data-stu-id="aee84-136">In the **Search** box, enter "Microsoft.SpatialAudio" and install the Microsoft Spatializer package: **Microsoft.SpatialAudio.Spatializer.Unity**</span></span>

![Spatializer plug-in NuGet](images/spatial-audio/spatializer-plugin-nuget.png)

## <a name="set-up-mrtk-in-your-project"></a><span data-ttu-id="aee84-138">Configurare MRTK nel progetto</span><span class="sxs-lookup"><span data-stu-id="aee84-138">Set up MRTK in your project</span></span>

1. <span data-ttu-id="aee84-139">Aprire la finestra impostazioni di compilazione passando a **file-> impostazioni di compilazione**.</span><span class="sxs-lookup"><span data-stu-id="aee84-139">Open the Build Settings window by going to **File -> Build Settings**.</span></span>

2. <span data-ttu-id="aee84-140">Selezionare il _piattaforma UWP (Universal Windows Platform)_ e fare clic su **Cambia piattaforma**.</span><span class="sxs-lookup"><span data-stu-id="aee84-140">Select the _Universal Windows Platform_ and click **Switch Platform**.</span></span>

3. <span data-ttu-id="aee84-141">Fare clic su **Impostazioni lettore** nella **finestra di compilazione** per aprire le proprietà **delle impostazioni del lettore** nel riquadro **controllo** .</span><span class="sxs-lookup"><span data-stu-id="aee84-141">Click **Player Settings** in the **Build Window** to open the **Player Settings** properties in the **Inspector** pane.</span></span>
    * <span data-ttu-id="aee84-142">In **Impostazioni XR**selezionare la casella di controllo **Virtual Reality supported**</span><span class="sxs-lookup"><span data-stu-id="aee84-142">Under **XR Settings**, check the **Virtual Reality Supported** checkbox</span></span>
    * <span data-ttu-id="aee84-143">In **Impostazioni XR**, modificare la **modalità di rendering stereo** in **Single Pass istanza**.</span><span class="sxs-lookup"><span data-stu-id="aee84-143">Under **XR Settings**, change the **Stereo Rendering Mode** to **Single Pass Instanced**.</span></span>
    * <span data-ttu-id="aee84-144">In **impostazioni di pubblicazione**selezionare la casella di controllo **percezione spaziale** nella sezione **funzionalità**</span><span class="sxs-lookup"><span data-stu-id="aee84-144">Under **Publishing Settings**, check the **Spatial Perception** checkbox in the **Capabilities** section</span></span>

4. <span data-ttu-id="aee84-145">Sulla barra dei menu fare clic su **Toolkit realtà mista-> Aggiungi a scena e configura..**</span><span class="sxs-lookup"><span data-stu-id="aee84-145">On the menu bar, click **Mixed Reality Toolkit -> Add to Scene and Configure..**</span></span> <span data-ttu-id="aee84-146">per aggiungere MRTK alla scena.</span><span class="sxs-lookup"><span data-stu-id="aee84-146">to add MRTK to your scene.</span></span>

<span data-ttu-id="aee84-147">Per altre istruzioni, ad esempio su come compilare l'app e distribuirla in un HoloLens 2, vedere [il capitolo 1 del modulo di base per la formazione di Mr Learning](mrlearning-base-ch1.md).</span><span class="sxs-lookup"><span data-stu-id="aee84-147">For additional guidance, including how to build your app and deploy to a HoloLens 2, see [Chapter 1 of the MR Learning Base Module](mrlearning-base-ch1.md).</span></span>

## <a name="enable-the-microsoft-spatializer-plugin"></a><span data-ttu-id="aee84-148">Abilitare il plug-in Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="aee84-148">Enable the Microsoft Spatializer plugin</span></span>
<span data-ttu-id="aee84-149">Abilitare il plug-in **Microsoft Spatializer** .</span><span class="sxs-lookup"><span data-stu-id="aee84-149">Enable the **Microsoft Spatializer** plugin.</span></span> <span data-ttu-id="aee84-150">Aprire **modifica-> impostazioni progetto-> audio**e modificare il **plug** -in Spatializer in "Microsoft Spatializer".</span><span class="sxs-lookup"><span data-stu-id="aee84-150">Open **Edit -> Project Settings -> Audio**, and change **Spatializer Plugin** to "Microsoft Spatializer".</span></span> <span data-ttu-id="aee84-151">La sezione **audio** delle **impostazioni del progetto** sarà ora simile alla seguente:</span><span class="sxs-lookup"><span data-stu-id="aee84-151">The **Audio** section of the **Project Settings** will now look like this:</span></span>

![Impostazioni del progetto che mostrano il plug-in Spatializer](images/spatial-audio/project-settings.png)

## <a name="enable-spatial-audio-on-your-workstation"></a><span data-ttu-id="aee84-153">Abilitare l'audio spaziale nella workstation</span><span class="sxs-lookup"><span data-stu-id="aee84-153">Enable spatial audio on your workstation</span></span>
<span data-ttu-id="aee84-154">Nelle versioni desktop di Windows, l'audio spaziale è disabilitato per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="aee84-154">On desktop versions of Windows, spatial audio is disabled by default.</span></span> <span data-ttu-id="aee84-155">Per abilitarla, fare clic con il pulsante destro del mouse sull'icona del volume sulla barra delle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="aee84-155">Enable it by right-clicking on the volume icon in the task bar.</span></span> <span data-ttu-id="aee84-156">Per ottenere la migliore rappresentazione di ciò che è possibile sentire in HoloLens 2, scegliere **audio spaziale > Windows Sonic per le cuffie**.</span><span class="sxs-lookup"><span data-stu-id="aee84-156">To get the best representation of what you'll hear on HoloLens 2, choose **Spatial sound -> Windows Sonic for Headphones**.</span></span>

![Impostazioni audio spaziali desktop](images/spatial-audio/desktop-audio-settings.png)

> [!NOTE]
> <span data-ttu-id="aee84-158">Questa impostazione è necessaria solo se si prevede di testare il progetto nell'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="aee84-158">This setting is only required if you plan to test your project in the Unity editor.</span></span>

## <a name="next-steps"></a><span data-ttu-id="aee84-159">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="aee84-159">Next steps</span></span>
<span data-ttu-id="aee84-160">Continuare con l' [audio spaziale del capitolo 2](unity-spatial-audio-ch2.md) per spatialize i suoni di interazione con i pulsanti.</span><span class="sxs-lookup"><span data-stu-id="aee84-160">Continue on to [Unity spatial audio chapter 2](unity-spatial-audio-ch2.md) to spatialize button interaction sounds.</span></span>


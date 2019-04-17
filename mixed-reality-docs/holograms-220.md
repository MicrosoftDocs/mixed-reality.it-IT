---
title: MR spaziale 220 - spaziale audio
description: Seguire questa procedura dettagliata codifica con Unity, Visual Studio e HoloLens informazioni dettagliate su concetti audio spaziali.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit unity, academy, esercitazione, spaziale audio
ms.openlocfilehash: 50d17fe8c9a6e3f18b1309a59c9c41af982a7505
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599013"
---
>[!NOTE]
><span data-ttu-id="96b33-104">Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.</span><span class="sxs-lookup"><span data-stu-id="96b33-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="96b33-105">Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.</span><span class="sxs-lookup"><span data-stu-id="96b33-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="96b33-106">Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.</span><span class="sxs-lookup"><span data-stu-id="96b33-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="96b33-107">Essi verranno mantenute per continuare a utilizzare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="96b33-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="96b33-108">Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="96b33-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="96b33-109">Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.</span><span class="sxs-lookup"><span data-stu-id="96b33-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-spatial-220-spatial-sound"></a><span data-ttu-id="96b33-110">MR Spatial 220: Audio spaziale</span><span class="sxs-lookup"><span data-stu-id="96b33-110">MR Spatial 220: Spatial sound</span></span>

<span data-ttu-id="96b33-111">[Suono spaziale](spatial-sound.md) armonioso suscita vita in ologrammi e fornisce a ognuna presenza nel mondo.</span><span class="sxs-lookup"><span data-stu-id="96b33-111">[Spatial sound](spatial-sound.md) breathes life into holograms and gives them presence in our world.</span></span> <span data-ttu-id="96b33-112">Ologrammi sono costituiti sia chiaro e suono e se si perdono del vntana vista, spaziale audio consentono di trovarli.</span><span class="sxs-lookup"><span data-stu-id="96b33-112">Holograms are composed of both light and sound, and if you happen to lose sight of your holograms, spatial sound can help you find them.</span></span> <span data-ttu-id="96b33-113">Suono spaziale non è ad esempio il suono tipico che senti sulla radio, è audio che viene posizionato nello spazio 3D.</span><span class="sxs-lookup"><span data-stu-id="96b33-113">Spatial sound is not like the typical sound that you would hear on the radio, it is sound that is positioned in 3D space.</span></span> <span data-ttu-id="96b33-114">Spaziali audio, è possibile rendere vntana audio, ad esempio si trovano dietro, accanto a si o anche in mente.</span><span class="sxs-lookup"><span data-stu-id="96b33-114">With spatial sound, you can make holograms sound like they're behind you, next to you, or even on your head!</span></span> <span data-ttu-id="96b33-115">In questo corso, si apprenderà come:</span><span class="sxs-lookup"><span data-stu-id="96b33-115">In this course, you will:</span></span>

* <span data-ttu-id="96b33-116">Configurare l'ambiente di sviluppo per usare Microsoft Spatial Sound.</span><span class="sxs-lookup"><span data-stu-id="96b33-116">Configure your development environment to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="96b33-117">Usare un suono spaziale per migliorare le interazioni.</span><span class="sxs-lookup"><span data-stu-id="96b33-117">Use Spatial Sound to enhance interactions.</span></span>
* <span data-ttu-id="96b33-118">Usare un suono spaziale in combinazione con Mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="96b33-118">Use Spatial Sound in conjunction with Spatial Mapping.</span></span>
* <span data-ttu-id="96b33-119">Comprendere la progettazione del suono e combinare le procedure consigliate.</span><span class="sxs-lookup"><span data-stu-id="96b33-119">Understand sound design and mixing best practices.</span></span>
* <span data-ttu-id="96b33-120">Usare un suono per migliorare gli effetti speciali e portare l'utente in tutto il mondo delle realtà mista.</span><span class="sxs-lookup"><span data-stu-id="96b33-120">Use sound to enhance special effects and bring the user into the Mixed Reality world.</span></span>

## <a name="device-support"></a><span data-ttu-id="96b33-121">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="96b33-121">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="96b33-122">Corso</span><span class="sxs-lookup"><span data-stu-id="96b33-122">Course</span></span></th><th style="width:150px"> <span data-ttu-id="96b33-123"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="96b33-123"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="96b33-124"><a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></span><span class="sxs-lookup"><span data-stu-id="96b33-124"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="96b33-125">MR Spatial 220: Audio spaziale</span><span class="sxs-lookup"><span data-stu-id="96b33-125">MR Spatial 220: Spatial sound</span></span></td><td style="text-align: center;"> <span data-ttu-id="96b33-126">✔️</span><span class="sxs-lookup"><span data-stu-id="96b33-126">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="96b33-127">✔️</span><span class="sxs-lookup"><span data-stu-id="96b33-127">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="96b33-128">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="96b33-128">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="96b33-129">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="96b33-129">Prerequisites</span></span>

* <span data-ttu-id="96b33-130">Un PC Windows 10 configurate con i valori corretti [sono installati gli strumenti](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="96b33-130">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="96b33-131">Alcuni basic C# capacità di programmazione.</span><span class="sxs-lookup"><span data-stu-id="96b33-131">Some basic C# programming ability.</span></span>
* <span data-ttu-id="96b33-132">È necessario avere completato [MR nozioni di base 101](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="96b33-132">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="96b33-133">Un dispositivo HoloLens [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="96b33-133">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="96b33-134">File di progetto</span><span class="sxs-lookup"><span data-stu-id="96b33-134">Project files</span></span>

* <span data-ttu-id="96b33-135">Scaricare il [file](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) necessarie per il progetto.</span><span class="sxs-lookup"><span data-stu-id="96b33-135">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) required by the project.</span></span><span data-ttu-id="96b33-136"> Richiede Unity 2017.2 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="96b33-136"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="96b33-137">Se è comunque necessario il supporto di Unity 5.6, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip).</span><span class="sxs-lookup"><span data-stu-id="96b33-137">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip).</span></span> <span data-ttu-id="96b33-138">Questa versione potrebbe non essere più aggiornata.</span><span class="sxs-lookup"><span data-stu-id="96b33-138">This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="96b33-139">Se è comunque necessario il supporto di Unity 5.5, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip).</span><span class="sxs-lookup"><span data-stu-id="96b33-139">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip).</span></span><span data-ttu-id="96b33-140"> Questa versione potrebbe non essere più aggiornata.</span><span class="sxs-lookup"><span data-stu-id="96b33-140"> This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="96b33-141">Se è ancora necessario supporto 5.4 di Unity, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip).</span><span class="sxs-lookup"><span data-stu-id="96b33-141">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip).</span></span><span data-ttu-id="96b33-142"> Questa versione potrebbe non essere più aggiornata.</span><span class="sxs-lookup"><span data-stu-id="96b33-142"> This release may no longer be up-to-date.</span></span>
* <span data-ttu-id="96b33-143">Annullare la-archive i file sul desktop o altri facile da raggiungere percorso.</span><span class="sxs-lookup"><span data-stu-id="96b33-143">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="96b33-144">Se si desidera esaminare il codice sorgente prima di scaricare, ha [disponibile in GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).</span><span class="sxs-lookup"><span data-stu-id="96b33-144">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="96b33-145">Errori e note</span><span class="sxs-lookup"><span data-stu-id="96b33-145">Errata and Notes</span></span>

* <span data-ttu-id="96b33-146">"Abilita Just My Code" deve essere disabilitato (*unchecked*) in Visual Studio in Strumenti -> Opzioni -> debug per poter raggiungere punti di interruzione nel codice.</span><span class="sxs-lookup"><span data-stu-id="96b33-146">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="96b33-147">Capitolo 1 - il programma di installazione di Unity</span><span class="sxs-lookup"><span data-stu-id="96b33-147">Chapter 1 - Unity Setup</span></span>

### <a name="objectives"></a><span data-ttu-id="96b33-148">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="96b33-148">Objectives</span></span>

* <span data-ttu-id="96b33-149">Modificare la configurazione di audio di Unity per usare Microsoft Spatial Sound.</span><span class="sxs-lookup"><span data-stu-id="96b33-149">Change Unity's sound configuration to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="96b33-150">Aggiungere suoni 3D a un oggetto in Unity.</span><span class="sxs-lookup"><span data-stu-id="96b33-150">Add 3D sound to an object in Unity.</span></span>

### <a name="instructions"></a><span data-ttu-id="96b33-151">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="96b33-151">Instructions</span></span>

* <span data-ttu-id="96b33-152">Avviare Unity.</span><span class="sxs-lookup"><span data-stu-id="96b33-152">Start Unity.</span></span>
* <span data-ttu-id="96b33-153">Selezionare **aperto**.</span><span class="sxs-lookup"><span data-stu-id="96b33-153">Select **Open**.</span></span>
* <span data-ttu-id="96b33-154">Passare al Desktop e individuare la cartella è archiviato in precedenza di annullamento.</span><span class="sxs-lookup"><span data-stu-id="96b33-154">Navigate to your Desktop and find the folder you previously un-archived.</span></span>
* <span data-ttu-id="96b33-155">Fare clic sui **Starting\Decibel** cartella e quindi premere il **Seleziona cartella** pulsante.</span><span class="sxs-lookup"><span data-stu-id="96b33-155">Click on the **Starting\Decibel** folder and then press the **Select Folder** button.</span></span>
* <span data-ttu-id="96b33-156">Attendere che il progetto da caricare in Unity.</span><span class="sxs-lookup"><span data-stu-id="96b33-156">Wait for the project to load in Unity.</span></span>
* <span data-ttu-id="96b33-157">Nel **Project** pannello aperto **Scenes\Decibel.unity**.</span><span class="sxs-lookup"><span data-stu-id="96b33-157">In the **Project** panel, open **Scenes\Decibel.unity**.</span></span>
* <span data-ttu-id="96b33-158">Nel **gerarchia** panel, espandere **HologramCollection** e selezionare **P0LY**.</span><span class="sxs-lookup"><span data-stu-id="96b33-158">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="96b33-159">Nella finestra di ispezione, espandere **AudioSource** e notare che non vi è alcun **Spatialize** casella di controllo.</span><span class="sxs-lookup"><span data-stu-id="96b33-159">In the Inspector, expand **AudioSource** and notice that there is no **Spatialize** check box.</span></span>

<span data-ttu-id="96b33-160">Per impostazione predefinita, Unity non viene caricato un plug-in spaziale.</span><span class="sxs-lookup"><span data-stu-id="96b33-160">By default, Unity does not load a spatializer plugin.</span></span> <span data-ttu-id="96b33-161">La procedura seguente consentirà spaziali audio nel progetto.</span><span class="sxs-lookup"><span data-stu-id="96b33-161">The following steps will enable Spatial Sound in the project.</span></span>

* <span data-ttu-id="96b33-162">Nel menu in alto di Unity, passare a **Modifica > Impostazioni di progetto > Audio**.</span><span class="sxs-lookup"><span data-stu-id="96b33-162">In Unity's top menu, go to **Edit > Project Settings > Audio**.</span></span>
* <span data-ttu-id="96b33-163">Trovare il **plug-in spaziale** dal menu a discesa e selezionare **MS HRTF Spatializer**.</span><span class="sxs-lookup"><span data-stu-id="96b33-163">Find the **Spatializer Plugin** dropdown, and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="96b33-164">Nel **gerarchia** Pannello di selezione **HologramCollection > P0LY**.</span><span class="sxs-lookup"><span data-stu-id="96b33-164">In the **Hierarchy** panel, select **HologramCollection > P0LY**.</span></span>
* <span data-ttu-id="96b33-165">Nel **Inspector** panel, trovare il **origine Audio** componente.</span><span class="sxs-lookup"><span data-stu-id="96b33-165">In the **Inspector** panel, find the **Audio Source** component.</span></span>
* <span data-ttu-id="96b33-166">Verificare i **Spatialize** casella di controllo.</span><span class="sxs-lookup"><span data-stu-id="96b33-166">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="96b33-167">Trascinare il **Blend spaziali** dispositivo di scorrimento fino alla **3D**, oppure immettere **1** nella casella di modifica.</span><span class="sxs-lookup"><span data-stu-id="96b33-167">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>

<span data-ttu-id="96b33-168">È ora verrà compilare il progetto in Unity e configurare la soluzione in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="96b33-168">We will now build the project in Unity and configure the solution in Visual Studio.</span></span>

1. <span data-ttu-id="96b33-169">In Unity, selezionare **File > Build Settings**.</span><span class="sxs-lookup"><span data-stu-id="96b33-169">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="96b33-170">Fare clic su **aggiungere scene Open** per aggiungere la scena.</span><span class="sxs-lookup"><span data-stu-id="96b33-170">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="96b33-171">Selezionare **Universal Windows Platform** nel **Platform** elenco e fare clic su **commutatore piattaforma**.</span><span class="sxs-lookup"><span data-stu-id="96b33-171">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="96b33-172">Se si sta sviluppando in modo specifico per HoloLens, impostare **dispositivo di destinazione** al **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="96b33-172">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="96b33-173">In caso contrario, ci si trova sulla **tutti i dispositivi**.</span><span class="sxs-lookup"><span data-stu-id="96b33-173">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="96b33-174">Assicurarsi **tipo di compilazione** è impostata su **D3D** e **SDK** è impostata su **installata più recente** (che deve essere SDK 16299 o versione successiva).</span><span class="sxs-lookup"><span data-stu-id="96b33-174">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="96b33-175">Fai clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="96b33-175">Click **Build**.</span></span>
7. <span data-ttu-id="96b33-176">Creare un **nuova cartella** denominato "App".</span><span class="sxs-lookup"><span data-stu-id="96b33-176">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="96b33-177">Solo clic i **App** cartella.</span><span class="sxs-lookup"><span data-stu-id="96b33-177">Single click the **App** folder.</span></span>
9. <span data-ttu-id="96b33-178">Premere **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="96b33-178">Press **Select Folder**.</span></span>

<span data-ttu-id="96b33-179">Quando Unity viene eseguita, verrà visualizzata una finestra di Esplora File.</span><span class="sxs-lookup"><span data-stu-id="96b33-179">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="96b33-180">Aprire il **App** cartella.</span><span class="sxs-lookup"><span data-stu-id="96b33-180">Open the **App** folder.</span></span>
2. <span data-ttu-id="96b33-181">Aprire il **soluzione di Visual Studio Decibel**.</span><span class="sxs-lookup"><span data-stu-id="96b33-181">Open the **Decibel Visual Studio Solution**.</span></span>

<span data-ttu-id="96b33-182">Se la distribuzione in HoloLens:</span><span class="sxs-lookup"><span data-stu-id="96b33-182">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="96b33-183">Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione di debug per **Release** e da ARM a **x86**.</span><span class="sxs-lookup"><span data-stu-id="96b33-183">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="96b33-184">Fare clic sull'elenco a discesa sulla freccia accanto al pulsante computer locale e selezionare **computer remoto**.</span><span class="sxs-lookup"><span data-stu-id="96b33-184">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="96b33-185">Immettere **l'indirizzo IP del dispositivo HoloLens** e impostare la modalità di autenticazione **universale (protocollo non crittografato)**.</span><span class="sxs-lookup"><span data-stu-id="96b33-185">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="96b33-186">Fare clic su **Seleziona**.</span><span class="sxs-lookup"><span data-stu-id="96b33-186">Click **Select**.</span></span> <span data-ttu-id="96b33-187">Se non si conosce l'indirizzo IP del dispositivo, esaminare **Impostazioni > rete e Internet > Opzioni avanzate**.</span><span class="sxs-lookup"><span data-stu-id="96b33-187">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="96b33-188">Nella barra dei menu superiore, fare clic su **Debug -> Avvia senza eseguire debug** o premere **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="96b33-188">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="96b33-189">Se questa è la prima volta che la distribuzione nel dispositivo, devi [abbinarlo a Visual Studio](using-visual-studio.md#pairing-your-device---hololens-1st-gen).</span><span class="sxs-lookup"><span data-stu-id="96b33-189">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device---hololens-1st-gen).</span></span>

<span data-ttu-id="96b33-190">Se la distribuzione in un visore VR immersivi:</span><span class="sxs-lookup"><span data-stu-id="96b33-190">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="96b33-191">Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione di debug per **Release** e da ARM a **x64**.</span><span class="sxs-lookup"><span data-stu-id="96b33-191">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="96b33-192">Verificare che la destinazione di distribuzione è impostata su **computer locale**.</span><span class="sxs-lookup"><span data-stu-id="96b33-192">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="96b33-193">Nella barra dei menu superiore, fare clic su **Debug -> Avvia senza eseguire debug** o premere **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="96b33-193">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>

## <a name="chapter-2---spatial-sound-and-interaction"></a><span data-ttu-id="96b33-194">Capitolo 2 - spaziale e suono di interazione</span><span class="sxs-lookup"><span data-stu-id="96b33-194">Chapter 2 - Spatial Sound and Interaction</span></span>

### <a name="objectives"></a><span data-ttu-id="96b33-195">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="96b33-195">Objectives</span></span>

* <span data-ttu-id="96b33-196">Migliorare il realismo ologrammi utilizzando audio.</span><span class="sxs-lookup"><span data-stu-id="96b33-196">Enhance hologram realism using sound.</span></span>
* <span data-ttu-id="96b33-197">Indirizzare sguardo dell'utente utilizzando audio.</span><span class="sxs-lookup"><span data-stu-id="96b33-197">Direct the user's gaze using sound.</span></span>
* <span data-ttu-id="96b33-198">Commenti e suggerimenti di movimento tramite file audio.</span><span class="sxs-lookup"><span data-stu-id="96b33-198">Provide gesture feedback using sound.</span></span>

### <a name="part-1---enhancing-realism"></a><span data-ttu-id="96b33-199">Parte 1 - realismo miglioramento</span><span class="sxs-lookup"><span data-stu-id="96b33-199">Part 1 - Enhancing Realism</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="96b33-200">Concetti chiave</span><span class="sxs-lookup"><span data-stu-id="96b33-200">Key Concepts</span></span>

* <span data-ttu-id="96b33-201">Spatialize suoni ologramma.</span><span class="sxs-lookup"><span data-stu-id="96b33-201">Spatialize hologram sounds.</span></span>
* <span data-ttu-id="96b33-202">Origini audio devono essere posizionate in una posizione appropriata di ologramma.</span><span class="sxs-lookup"><span data-stu-id="96b33-202">Sound sources should be placed at an appropriate location on the hologram.</span></span>

<span data-ttu-id="96b33-203">Il percorso appropriato per l'audio verrà variano a seconda di ologramma.</span><span class="sxs-lookup"><span data-stu-id="96b33-203">The appropriate location for the sound is going to depend on the hologram.</span></span> <span data-ttu-id="96b33-204">Ad esempio, se l'ologrammi sono di un essere umano, l'origine audio deve trovarsi quasi bocca e non dei piedi.</span><span class="sxs-lookup"><span data-stu-id="96b33-204">For example, if the hologram is of a human, the sound source should be located near the mouth and not the feet.</span></span>

#### <a name="instructions"></a><span data-ttu-id="96b33-205">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="96b33-205">Instructions</span></span>

<span data-ttu-id="96b33-206">Le istruzioni seguenti collegherà un suono spatialized di ologramma.</span><span class="sxs-lookup"><span data-stu-id="96b33-206">The following instructions will attach a spatialized sound to a hologram.</span></span>

* <span data-ttu-id="96b33-207">Nel **gerarchia** panel, espandere **HologramCollection** e selezionare **P0LY**.</span><span class="sxs-lookup"><span data-stu-id="96b33-207">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="96b33-208">Nel **Inspector** Pannello di **AudioSource**, fare clic sul cerchio accanto a **AudioClip** e selezionare **PolyHover** dalla finestra a comparsa.</span><span class="sxs-lookup"><span data-stu-id="96b33-208">In the **Inspector** panel, in the **AudioSource**, click the circle next to **AudioClip** and select **PolyHover** from the pop-up.</span></span>
* <span data-ttu-id="96b33-209">Fare clic sul cerchio accanto alla **Output** e selezionare **SoundEffects** dalla finestra a comparsa.</span><span class="sxs-lookup"><span data-stu-id="96b33-209">Click the circle next to **Output** and select **SoundEffects** from the pop-up.</span></span>

<span data-ttu-id="96b33-210">Progetto Decibel Usa un'istanza di Unity **AudioMixer** componente per abilitare la modifica dei livelli audio per i gruppi di suoni.</span><span class="sxs-lookup"><span data-stu-id="96b33-210">Project Decibel uses a Unity **AudioMixer** component to enable adjusting sound levels for groups of sounds.</span></span> <span data-ttu-id="96b33-211">È possibile regolare il volume complessivo dal raggruppamento di suoni in questo modo, pur mantenendo il relativo volume di ciascun file audio.</span><span class="sxs-lookup"><span data-stu-id="96b33-211">By grouping sounds this way, the overall volume can be adjusted while maintaining the relative volume of each sound.</span></span>

* <span data-ttu-id="96b33-212">Nel **AudioSource**, espandere **3D impostazioni audio**.</span><span class="sxs-lookup"><span data-stu-id="96b33-212">In the **AudioSource**, expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="96b33-213">Impostare **livello Doppler** al **0**.</span><span class="sxs-lookup"><span data-stu-id="96b33-213">Set **Doppler Level** to **0**.</span></span>

<span data-ttu-id="96b33-214">Impostazione livello Doppler a zero modifiche Disabilita nel passo causati da movimento (entrambi l'ologrammi e l'utente).</span><span class="sxs-lookup"><span data-stu-id="96b33-214">Setting Doppler level to zero disables changes in pitch caused by motion (either of the hologram or the user).</span></span> <span data-ttu-id="96b33-215">Un esempio tipico di utilizzo Doppler è un'auto in rapida evoluzione.</span><span class="sxs-lookup"><span data-stu-id="96b33-215">A classic example of Doppler is a fast-moving car.</span></span> <span data-ttu-id="96b33-216">Come l'auto si avvicina a un listener stazionario, aumenta il tono del motore.</span><span class="sxs-lookup"><span data-stu-id="96b33-216">As the car approaches a stationary listener, the pitch of the engine rises.</span></span> <span data-ttu-id="96b33-217">Quando si passa il listener, il tono scende con distanza.</span><span class="sxs-lookup"><span data-stu-id="96b33-217">When it passes the listener, the pitch lowers with distance.</span></span>

### <a name="part-2---directing-the-users-gaze"></a><span data-ttu-id="96b33-218">Parte 2 - indirizzamento sguardo dell'utente</span><span class="sxs-lookup"><span data-stu-id="96b33-218">Part 2 - Directing the User's Gaze</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="96b33-219">Concetti chiave</span><span class="sxs-lookup"><span data-stu-id="96b33-219">Key Concepts</span></span>

* <span data-ttu-id="96b33-220">Usare un suono per attirare l'attenzione su vntana importanti.</span><span class="sxs-lookup"><span data-stu-id="96b33-220">Use sound to call attention to important holograms.</span></span>
* <span data-ttu-id="96b33-221">Orecchie consentono di indirizzare in cui dovrebbe avere un aspetto dal punto di vista.</span><span class="sxs-lookup"><span data-stu-id="96b33-221">The ears help direct where the eyes should look.</span></span>
* <span data-ttu-id="96b33-222">Il cervello ha alcune aspettative appreso.</span><span class="sxs-lookup"><span data-stu-id="96b33-222">The brain has some learned expectations.</span></span>

<span data-ttu-id="96b33-223">Un esempio delle aspettative acquisite è che sono in genere volatili sopra i capi di esseri umani.</span><span class="sxs-lookup"><span data-stu-id="96b33-223">One example of learned expectations is that birds are generally above the heads of humans.</span></span> <span data-ttu-id="96b33-224">Se un utente ascolta un suono bird, la reazione iniziale consiste nel cercare.</span><span class="sxs-lookup"><span data-stu-id="96b33-224">If a user hears a bird sound, their initial reaction is to look up.</span></span> <span data-ttu-id="96b33-225">Inserimento di uccelli sotto l'utente può portare a essi rivolta nella direzione corretta del suono, ma non riesce a trovare l'ologrammi si prevede di dover cercare in base.</span><span class="sxs-lookup"><span data-stu-id="96b33-225">Placing a bird below the user can lead to them facing the correct direction of the sound, but being unable to find the hologram based on the expectation of needing to look up.</span></span>

#### <a name="instructions"></a><span data-ttu-id="96b33-226">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="96b33-226">Instructions</span></span>

<span data-ttu-id="96b33-227">Le istruzioni seguenti abilitano P0LY nascondere sottostante è, in modo che è possibile usare suono per individuare l'ologramma.</span><span class="sxs-lookup"><span data-stu-id="96b33-227">The following instructions enable P0LY to hide behind you, so that you can use sound to locate the hologram.</span></span>

* <span data-ttu-id="96b33-228">Nel **gerarchia** Pannello di selezione **responsabili**.</span><span class="sxs-lookup"><span data-stu-id="96b33-228">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="96b33-229">Nel **Inspector** panel, trovare **gestore di Input vocale**.</span><span class="sxs-lookup"><span data-stu-id="96b33-229">In the **Inspector** panel, find **Speech Input Handler**.</span></span>
* <span data-ttu-id="96b33-230">Nelle **gestore di Input vocale**, espandere **Vai nascondere**.</span><span class="sxs-lookup"><span data-stu-id="96b33-230">In **Speech Input Handler**, expand **Go Hide**.</span></span>
* <span data-ttu-id="96b33-231">Change **alcuna funzione** al **PolyActions.GoHide**.</span><span class="sxs-lookup"><span data-stu-id="96b33-231">Change **No Function** to **PolyActions.GoHide**.</span></span>

![parola chiave: Nascondi passare](images/gohide.png)

### <a name="part-3---gesture-feedback"></a><span data-ttu-id="96b33-233">Parte 3 - commenti e suggerimenti di movimento</span><span class="sxs-lookup"><span data-stu-id="96b33-233">Part 3 - Gesture Feedback</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="96b33-234">Concetti chiave</span><span class="sxs-lookup"><span data-stu-id="96b33-234">Key Concepts</span></span>

* <span data-ttu-id="96b33-235">Fornire all'utente conferma positivo movimento utilizzando audio</span><span class="sxs-lookup"><span data-stu-id="96b33-235">Provide the user with positive gesture confirmation using sound</span></span>
* <span data-ttu-id="96b33-236">Invece di travolgerci utente - get suoni troppo alti in modo</span><span class="sxs-lookup"><span data-stu-id="96b33-236">Do not overwhelm the user - overly loud sounds get in the way</span></span>
* <span data-ttu-id="96b33-237">Suoni sottili funzionano in modo ottimale - non stonino l'esperienza</span><span class="sxs-lookup"><span data-stu-id="96b33-237">Subtle sounds work best - do not overshadow the experience</span></span>

#### <a name="instructions"></a><span data-ttu-id="96b33-238">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="96b33-238">Instructions</span></span>

* <span data-ttu-id="96b33-239">Nel **gerarchia** panel, espandere **HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="96b33-239">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="96b33-240">Espandere **EnergyHub** e selezionare **Base**.</span><span class="sxs-lookup"><span data-stu-id="96b33-240">Expand **EnergyHub** and select **Base**.</span></span>
* <span data-ttu-id="96b33-241">Nel **Inspector** del pannello, fare clic su **Add Component** e aggiungere **gestore movimenti suono**.</span><span class="sxs-lookup"><span data-stu-id="96b33-241">In the **Inspector** panel, click **Add Component** and add **Gesture Sound Handler**.</span></span>
* <span data-ttu-id="96b33-242">Nella **gestore movimenti suono**, fare clic sul cerchio accanto a **spostamento avviato Clip** e **navigazione aggiornato Clip** e selezionare **RotateClick**dalla finestra a comparsa per entrambi.</span><span class="sxs-lookup"><span data-stu-id="96b33-242">In **Gesture Sound Handler**, click the circle next to **Navigation Started Clip** and **Navigation Updated Clip** and select **RotateClick** from the pop-up for both.</span></span>
* <span data-ttu-id="96b33-243">Fare doppio clic su "GestureSoundHandler" per il caricamento in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="96b33-243">Double click on "GestureSoundHandler" to load in Visual Studio.</span></span>

<span data-ttu-id="96b33-244">Gestore di segnale acustico di movimento esegue le attività seguenti:</span><span class="sxs-lookup"><span data-stu-id="96b33-244">Gesture Sound Handler performs the following tasks:</span></span>

* <span data-ttu-id="96b33-245">Creare e configurare un' **AudioSource**.</span><span class="sxs-lookup"><span data-stu-id="96b33-245">Create and configure an **AudioSource**.</span></span>
* <span data-ttu-id="96b33-246">Sul posto di **AudioSource** in corrispondenza della posizione di appropriato **GameObject**.</span><span class="sxs-lookup"><span data-stu-id="96b33-246">Place the **AudioSource** at the location of the appropriate **GameObject**.</span></span>
* <span data-ttu-id="96b33-247">Riproduce il **AudioClip** associato al movimento.</span><span class="sxs-lookup"><span data-stu-id="96b33-247">Plays the **AudioClip** associated with the gesture.</span></span>

#### <a name="build-and-deploy"></a><span data-ttu-id="96b33-248">Compilare e distribuire</span><span class="sxs-lookup"><span data-stu-id="96b33-248">Build and Deploy</span></span>

1. <span data-ttu-id="96b33-249">In Unity, selezionare **File > Build Settings**.</span><span class="sxs-lookup"><span data-stu-id="96b33-249">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="96b33-250">Fai clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="96b33-250">Click **Build**.</span></span>
3. <span data-ttu-id="96b33-251">Solo clic i **App** cartella.</span><span class="sxs-lookup"><span data-stu-id="96b33-251">Single click the **App** folder.</span></span>
4. <span data-ttu-id="96b33-252">Premere **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="96b33-252">Press **Select Folder**.</span></span>

<span data-ttu-id="96b33-253">Verificare che la barra degli strumenti viene visualizzato "Rilascio", "x86" o "x64" e "Dispositivo remoto".</span><span class="sxs-lookup"><span data-stu-id="96b33-253">Check that the Toolbar says "Release", "x86" or "x64", and "Remote Device".</span></span> <span data-ttu-id="96b33-254">In caso contrario, si tratta dell'istanza di scrittura del codice di Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="96b33-254">If not, this is the coding instance of Visual Studio.</span></span> <span data-ttu-id="96b33-255">Potrebbe essere necessario aprire nuovamente la soluzione dalla cartella dell'App.</span><span class="sxs-lookup"><span data-stu-id="96b33-255">You may need to re-open the solution from the App folder.</span></span>

* <span data-ttu-id="96b33-256">Se richiesto, ricaricare i file di progetto.</span><span class="sxs-lookup"><span data-stu-id="96b33-256">If prompted, reload the project files.</span></span>
* <span data-ttu-id="96b33-257">Come in precedenza, eseguire la distribuzione da Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="96b33-257">As before, deploy from Visual Studio.</span></span>

<span data-ttu-id="96b33-258">Dopo aver distribuita l'applicazione:</span><span class="sxs-lookup"><span data-stu-id="96b33-258">After the application is deployed:</span></span>

* <span data-ttu-id="96b33-259">Osservare come il suono cambia mentre si sposta all'interno di P0LY.</span><span class="sxs-lookup"><span data-stu-id="96b33-259">Observe how the sound changes as you move around P0LY.</span></span>
* <span data-ttu-id="96b33-260">Pronunciare *"Vai Hide"* apportare P0LY spostare in un percorso sottostante è.</span><span class="sxs-lookup"><span data-stu-id="96b33-260">Say *"Go Hide"* to make P0LY move to a location behind you.</span></span> <span data-ttu-id="96b33-261">Cercarla, l'audio.</span><span class="sxs-lookup"><span data-stu-id="96b33-261">Find it by the sound.</span></span>
* <span data-ttu-id="96b33-262">Fissare la base di Hub di energia.</span><span class="sxs-lookup"><span data-stu-id="96b33-262">Gaze at the base of the Energy Hub.</span></span> <span data-ttu-id="96b33-263">Toccare e trascinare destra o sinistra per ruotare l'ologrammi e notare come il suono facendo clic su Conferma il movimento.</span><span class="sxs-lookup"><span data-stu-id="96b33-263">Tap and drag left or right to rotate the hologram and notice how the clicking sound confirms the gesture.</span></span>

<span data-ttu-id="96b33-264">Nota: È presente un pannello di testo che verrà tag-along con l'utente.</span><span class="sxs-lookup"><span data-stu-id="96b33-264">Note: There is a text panel that will tag-along with you.</span></span> <span data-ttu-id="96b33-265">Questa sezione contiene i comandi vocali disponibili che è possibile usare in questo corso.</span><span class="sxs-lookup"><span data-stu-id="96b33-265">This will contain the available voice commands that you can use throughout this course.</span></span>

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a><span data-ttu-id="96b33-266">Capitolo 3 - Mapping spaziale audio e quelli spaziali</span><span class="sxs-lookup"><span data-stu-id="96b33-266">Chapter 3 - Spatial Sound and Spatial Mapping</span></span>

### <a name="objectives"></a><span data-ttu-id="96b33-267">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="96b33-267">Objectives</span></span>

* <span data-ttu-id="96b33-268">Verificare l'interazione tra ologrammi e il mondo reale con file audio.</span><span class="sxs-lookup"><span data-stu-id="96b33-268">Confirm interaction between holograms and the real world using sound.</span></span>
* <span data-ttu-id="96b33-269">Nasconde i colori audio mediante il mondo fisico.</span><span class="sxs-lookup"><span data-stu-id="96b33-269">Occlude sound using the physical world.</span></span>

### <a name="part-1---physical-world-interaction"></a><span data-ttu-id="96b33-270">Part 1 - Physical World Interaction</span><span class="sxs-lookup"><span data-stu-id="96b33-270">Part 1 - Physical World Interaction</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="96b33-271">Concetti chiave</span><span class="sxs-lookup"><span data-stu-id="96b33-271">Key Concepts</span></span>

* <span data-ttu-id="96b33-272">Oggetti fisici generi un suono a livello generale in presenza di un'area o in un altro oggetto.</span><span class="sxs-lookup"><span data-stu-id="96b33-272">Physical objects generally make a sound when encountering a surface or another object.</span></span>
* <span data-ttu-id="96b33-273">Suoni dovrebbero essere appropriato all'interno di un contesto.</span><span class="sxs-lookup"><span data-stu-id="96b33-273">Sounds should be context appropriate within the experience.</span></span>

<span data-ttu-id="96b33-274">Ad esempio, l'impostazione di una tazza di una tabella deve generi un suono risulteranno meno intensi di eliminazione di un boulder su un foglio di metallo.</span><span class="sxs-lookup"><span data-stu-id="96b33-274">For example, setting a cup on a table should make a quieter sound than dropping a boulder on a piece of metal.</span></span>

#### <a name="instructions"></a><span data-ttu-id="96b33-275">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="96b33-275">Instructions</span></span>

* <span data-ttu-id="96b33-276">Nel **gerarchia** panel, espandere **HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="96b33-276">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="96b33-277">Espandere **EnergyHub**, selezionare **Base**.</span><span class="sxs-lookup"><span data-stu-id="96b33-277">Expand **EnergyHub**, select **Base**.</span></span>
* <span data-ttu-id="96b33-278">Nel **Inspector** del pannello, fare clic su **Add Component** e aggiungere **toccare a sul posto con suono e azione**.</span><span class="sxs-lookup"><span data-stu-id="96b33-278">In the **Inspector** panel, click **Add Component** and add **Tap To Place With Sound and Action**.</span></span>
* <span data-ttu-id="96b33-279">Nelle **toccare a con azione e suono**:</span><span class="sxs-lookup"><span data-stu-id="96b33-279">In **Tap To Place With Sound and Action**:</span></span>
  * <span data-ttu-id="96b33-280">Controllare **posizionare padre al tocco**.</span><span class="sxs-lookup"><span data-stu-id="96b33-280">Check **Place Parent On Tap**.</span></span>
  * <span data-ttu-id="96b33-281">Impostare **suono di posizionamento** al **luogo**.</span><span class="sxs-lookup"><span data-stu-id="96b33-281">Set **Placement Sound** to **Place**.</span></span>
  * <span data-ttu-id="96b33-282">Impostare **suono Pickup** al **Pickup**.</span><span class="sxs-lookup"><span data-stu-id="96b33-282">Set **Pickup Sound** to **Pickup**.</span></span>
  * <span data-ttu-id="96b33-283">Premere + in basso a destra sotto entrambi **in azione Pickup** e **azione sul posizionamento**.</span><span class="sxs-lookup"><span data-stu-id="96b33-283">Press the + in the bottom right under both **On Pickup Action** and **On Placement Action**.</span></span> <span data-ttu-id="96b33-284">Trascinare EnergyHub dalla scena nel **Nessuno (oggetto)** campi.</span><span class="sxs-lookup"><span data-stu-id="96b33-284">Drag EnergyHub from the scene into the **None (Object)** fields.</span></span>
    * <span data-ttu-id="96b33-285">Sotto **in azione Pickup**, fare clic su **nessuna funzione** -> **EnergyHubBase** -> **ResetAnimation**.</span><span class="sxs-lookup"><span data-stu-id="96b33-285">Under **On Pickup Action**, click on **No Function** -> **EnergyHubBase** -> **ResetAnimation**.</span></span>
    * <span data-ttu-id="96b33-286">Sotto **azione sul posizionamento**, fare clic su **nessuna funzione** -> **EnergyHubBase** -> **OnSelect**.</span><span class="sxs-lookup"><span data-stu-id="96b33-286">Under **On Placement Action**, click on **No Function** -> **EnergyHubBase** -> **OnSelect**.</span></span>

![Toccare a con azione e suono](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a><span data-ttu-id="96b33-288">Parte 2 - occlusione audio</span><span class="sxs-lookup"><span data-stu-id="96b33-288">Part 2 - Sound Occlusion</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="96b33-289">Concetti chiave</span><span class="sxs-lookup"><span data-stu-id="96b33-289">Key Concepts</span></span>

* <span data-ttu-id="96b33-290">File audio, ad esempio chiaro, possa essere bloccato.</span><span class="sxs-lookup"><span data-stu-id="96b33-290">Sound, like light, can be occluded.</span></span>

<span data-ttu-id="96b33-291">Un esempio classico è un concerti.</span><span class="sxs-lookup"><span data-stu-id="96b33-291">A classic example is a concert hall.</span></span> <span data-ttu-id="96b33-292">Quando un listener è permanente di fuori ufficio e la porta è chiuso, i suoni di musica ovattati.</span><span class="sxs-lookup"><span data-stu-id="96b33-292">When a listener is standing outside of the hall and the door is closed, the music sounds muffled.</span></span> <span data-ttu-id="96b33-293">È inoltre disponibile in genere una riduzione del volume.</span><span class="sxs-lookup"><span data-stu-id="96b33-293">There is also typically a reduction in volume.</span></span> <span data-ttu-id="96b33-294">Quando si apre la porta, la gamma completa dell'audio viene ascoltata al volume effettivo.</span><span class="sxs-lookup"><span data-stu-id="96b33-294">When the door is opened, the full spectrum of the sound is heard at the actual volume.</span></span> <span data-ttu-id="96b33-295">Suoni ad alta frequenza vengono in genere assorbiti più basse frequenze.</span><span class="sxs-lookup"><span data-stu-id="96b33-295">High frequency sounds are generally absorbed more than low frequencies.</span></span>

#### <a name="instructions"></a><span data-ttu-id="96b33-296">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="96b33-296">Instructions</span></span>

* <span data-ttu-id="96b33-297">Nel **gerarchia** panel, espandere **HologramCollection** e selezionare **P0LY**.</span><span class="sxs-lookup"><span data-stu-id="96b33-297">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="96b33-298">Nel **Inspector** del pannello, fare clic su **Add Component** e aggiungere **Audio emettitore**.</span><span class="sxs-lookup"><span data-stu-id="96b33-298">In the **Inspector** panel, click **Add Component** and add **Audio Emitter**.</span></span>

<span data-ttu-id="96b33-299">La classe Audio emettitore fornisce le funzionalità seguenti:</span><span class="sxs-lookup"><span data-stu-id="96b33-299">The Audio Emitter class provides the following features:</span></span>

* <span data-ttu-id="96b33-300">Ripristina tutte le modifiche al volume dei **AudioSource**.</span><span class="sxs-lookup"><span data-stu-id="96b33-300">Restores any changes to the volume of the **AudioSource**.</span></span>
* <span data-ttu-id="96b33-301">Esegue una **Physics.RaycastNonAlloc** dalla posizione dell'utente nella direzione delle **GameObject** a cui il **AudioEmitter** è collegato.</span><span class="sxs-lookup"><span data-stu-id="96b33-301">Performs a **Physics.RaycastNonAlloc** from the user's position in the direction of the **GameObject** to which the **AudioEmitter** is attached.</span></span>

<span data-ttu-id="96b33-302">Il metodo RaycastNonAlloc viene utilizzato come ottimizzare le prestazioni per limitare le allocazioni, nonché il numero di risultati restituiti.</span><span class="sxs-lookup"><span data-stu-id="96b33-302">The RaycastNonAlloc method is used as a performance optimization to limit allocations as well as the number of results returned.</span></span>

* <span data-ttu-id="96b33-303">Per ognuno **IAudioInfluencer** rilevato, chiama il **ApplyEffect** (metodo).</span><span class="sxs-lookup"><span data-stu-id="96b33-303">For each **IAudioInfluencer** encountered, calls the **ApplyEffect** method.</span></span>
* <span data-ttu-id="96b33-304">Per ogni precedente **IAudioInfluencer** vale a dire chiamata non è più rilevato, il **RemoveEffect** (metodo).</span><span class="sxs-lookup"><span data-stu-id="96b33-304">For each previous **IAudioInfluencer** that is no longer encountered, call the **RemoveEffect** method.</span></span>

<span data-ttu-id="96b33-305">Si noti che AudioEmitter Aggiorna in tempi umanamente scale, in contrapposizione a pagamento in base al frame.</span><span class="sxs-lookup"><span data-stu-id="96b33-305">Note that AudioEmitter updates on human time scales, as opposed to on a per frame basis.</span></span> <span data-ttu-id="96b33-306">Ciò avviene perché gli esseri umani in genere non si spostano sufficientemente rapido per l'effetto di dover essere aggiornata con frequenza maggiore rispetto a ogni trimestre o semestre di un secondo.</span><span class="sxs-lookup"><span data-stu-id="96b33-306">This is done because humans generally do not move fast enough for the effect to need to be updated more frequently than every quarter or half of a second.</span></span> <span data-ttu-id="96b33-307">Ologrammi tale teleport rapidamente da una posizione a un'altra può interrompere l'illusione.</span><span class="sxs-lookup"><span data-stu-id="96b33-307">Holograms that teleport rapidly from one location to another can break the illusion.</span></span>

* <span data-ttu-id="96b33-308">Nel **gerarchia** panel, espandere **HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="96b33-308">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="96b33-309">Espandere **EnergyHub** e selezionare **BlobOutside**.</span><span class="sxs-lookup"><span data-stu-id="96b33-309">Expand **EnergyHub** and select **BlobOutside**.</span></span>
* <span data-ttu-id="96b33-310">Nel **Inspector** del pannello, fare clic su **Add Component** e aggiungere **Audio Occluder**.</span><span class="sxs-lookup"><span data-stu-id="96b33-310">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="96b33-311">Nelle **Occluder Audio**, impostare **frequenza di taglio** al **1500**.</span><span class="sxs-lookup"><span data-stu-id="96b33-311">In **Audio Occluder**, set **Cutoff Frequency** to **1500**.</span></span>

<span data-ttu-id="96b33-312">Questa impostazione limita le frequenze AudioSource ad Hz 1500 e versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="96b33-312">This setting limits the AudioSource frequencies to 1500 Hz and below.</span></span>

* <span data-ttu-id="96b33-313">Impostare **Volume Pass-Through** al **0.9**.</span><span class="sxs-lookup"><span data-stu-id="96b33-313">Set **Volume Pass Through** to **0.9**.</span></span>

<span data-ttu-id="96b33-314">Questa impostazione riduce il volume del AudioSource al 90% del relativo livello corrente.</span><span class="sxs-lookup"><span data-stu-id="96b33-314">This setting reduces the volume of the AudioSource to 90% of it's current level.</span></span>

<span data-ttu-id="96b33-315">Audio Occluder implementa IAudioInfluencer per:</span><span class="sxs-lookup"><span data-stu-id="96b33-315">Audio Occluder implements IAudioInfluencer to:</span></span>

* <span data-ttu-id="96b33-316">Applicare un effetto di occlusione usando un **AudioLowPassFilter** che viene associato ai **AudioSource** buy gestito il **AudioEmitter**.</span><span class="sxs-lookup"><span data-stu-id="96b33-316">Apply an occlusion effect using an **AudioLowPassFilter** which gets attached to the **AudioSource** managed buy the **AudioEmitter**.</span></span>
* <span data-ttu-id="96b33-317">Si applica un'attenuazione volume per il AudioSource.</span><span class="sxs-lookup"><span data-stu-id="96b33-317">Applies volume attenuation to the AudioSource.</span></span>
* <span data-ttu-id="96b33-318">Disabilita l'effetto impostando una frequenza di taglio neutra e la disabilitazione del filtro.</span><span class="sxs-lookup"><span data-stu-id="96b33-318">Disables the effect by setting a neutral cutoff frequency and disabling the filter.</span></span>

<span data-ttu-id="96b33-319">La frequenza utilizzata come neutro è kHz 22 (22000 Hz).</span><span class="sxs-lookup"><span data-stu-id="96b33-319">The frequency used as neutral is 22 kHz (22000 Hz).</span></span> <span data-ttu-id="96b33-320">Poiché i file sono di sopra la nominale frequenza massima che può essere ascoltata dai ascoltati dal umani, questa effettua alcun impatto percepibile per l'audio è stato scelto questa frequenza.</span><span class="sxs-lookup"><span data-stu-id="96b33-320">This frequency was chosen due to it being above the nominal maximum frequency that can be heard by the human ear, this making no discernable impact to the sound.</span></span>

* <span data-ttu-id="96b33-321">Nel **gerarchia** Pannello di selezione **SpatialMapping**.</span><span class="sxs-lookup"><span data-stu-id="96b33-321">In the **Hierarchy** panel, select **SpatialMapping**.</span></span>
* <span data-ttu-id="96b33-322">Nel **Inspector** del pannello, fare clic su **Add Component** e aggiungere **Audio Occluder**.</span><span class="sxs-lookup"><span data-stu-id="96b33-322">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="96b33-323">Nelle **Occluder Audio**, impostare **frequenza di taglio** al **750**.</span><span class="sxs-lookup"><span data-stu-id="96b33-323">In **Audio Occluder**, set **Cutoff Frequency** to **750**.</span></span>

<span data-ttu-id="96b33-324">Quando più occluders si trovano nel percorso tra l'utente e la **AudioEmitter**, la frequenza minima viene applicata al filtro.</span><span class="sxs-lookup"><span data-stu-id="96b33-324">When multiple occluders are in the path between the user and the **AudioEmitter**, the lowest frequency is applied to the filter.</span></span>

* <span data-ttu-id="96b33-325">Impostare **Volume Pass-Through** al **0,75**.</span><span class="sxs-lookup"><span data-stu-id="96b33-325">Set **Volume Pass Through** to **0.75**.</span></span>

<span data-ttu-id="96b33-326">Quando più occluders si trovano nel percorso tra l'utente e la **AudioEmitter**, il volume pass-through viene applicato modo additivo.</span><span class="sxs-lookup"><span data-stu-id="96b33-326">When multiple occluders are in the path between the user and the **AudioEmitter**, the volume pass through is applied additively.</span></span>

* <span data-ttu-id="96b33-327">Nel **gerarchia** Pannello di selezione **responsabili**.</span><span class="sxs-lookup"><span data-stu-id="96b33-327">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="96b33-328">Nel **Inspector** panel, espandere **gestore di Input vocale**.</span><span class="sxs-lookup"><span data-stu-id="96b33-328">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="96b33-329">Nelle **gestore di Input vocale**, espandere **Vai addebito**.</span><span class="sxs-lookup"><span data-stu-id="96b33-329">In **Speech Input Handler**, expand **Go Charge**.</span></span>
* <span data-ttu-id="96b33-330">Change **alcuna funzione** al **PolyActions.GoCharge**.</span><span class="sxs-lookup"><span data-stu-id="96b33-330">Change **No Function** to **PolyActions.GoCharge**.</span></span>

![parola chiave: Passare l'addebito](images/gocharge.png)

* <span data-ttu-id="96b33-332">Espandere **qui**.</span><span class="sxs-lookup"><span data-stu-id="96b33-332">Expand **Come Here**.</span></span>
* <span data-ttu-id="96b33-333">Change **alcuna funzione** al **PolyActions.ComeBack**.</span><span class="sxs-lookup"><span data-stu-id="96b33-333">Change **No Function** to **PolyActions.ComeBack**.</span></span>

![parola chiave: In questa pagina](images/comehere.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="96b33-335">Compilare e distribuire</span><span class="sxs-lookup"><span data-stu-id="96b33-335">Build and Deploy</span></span>

* <span data-ttu-id="96b33-336">Come in precedenza, compilare il progetto in Unity e distribuzione in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="96b33-336">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="96b33-337">Dopo aver distribuita l'applicazione:</span><span class="sxs-lookup"><span data-stu-id="96b33-337">After the application is deployed:</span></span>

* <span data-ttu-id="96b33-338">Pronunciare *"Addebito per passare"* per far P0LY entrare nell'Hub di energia.</span><span class="sxs-lookup"><span data-stu-id="96b33-338">Say *"Go Charge"* to have P0LY enter the Energy Hub.</span></span>

<span data-ttu-id="96b33-339">Si noti la modifica dell'audio.</span><span class="sxs-lookup"><span data-stu-id="96b33-339">Note the change in the sound.</span></span> <span data-ttu-id="96b33-340">Necessario un tono sordo e un po' più basse.</span><span class="sxs-lookup"><span data-stu-id="96b33-340">It should sound muffled and a little quieter.</span></span> <span data-ttu-id="96b33-341">Se si è in grado di posizionare manualmente con una parete o un altro oggetto tra l'utente e l'Hub di energia, si dovrebbe notare un'ulteriore muffling del suono a causa dell'occlusione dal mondo reale.</span><span class="sxs-lookup"><span data-stu-id="96b33-341">If you are able to position yourself with a wall or other object between you and the Energy Hub, you should notice a further muffling of the sound due to the occlusion by the real world.</span></span>

* <span data-ttu-id="96b33-342">Pronunciare *"Provengono qui"* affinché P0LY lasciare l'Hub di energia e posizionerà portata di mano.</span><span class="sxs-lookup"><span data-stu-id="96b33-342">Say *"Come Here"* to have P0LY leave the Energy Hub and position itself in front of you.</span></span>

<span data-ttu-id="96b33-343">Si noti che dell'occlusione audio viene rimossa una volta P0LY viene chiuso l'Hub di energia.</span><span class="sxs-lookup"><span data-stu-id="96b33-343">Note that the sound occlusion is removed once P0LY exits the Energy Hub.</span></span> <span data-ttu-id="96b33-344">Se sei ancora occlusione udito, P0LY potrebbero essere bloccati in situazioni reali.</span><span class="sxs-lookup"><span data-stu-id="96b33-344">If you are still hearing occlusion, P0LY may be occluded by the real world.</span></span> <span data-ttu-id="96b33-345">Provare a spostare avere a disposizione un chiaro comunichi P0LY.</span><span class="sxs-lookup"><span data-stu-id="96b33-345">Try moving to ensure you have a clear line of sight to P0LY.</span></span>

### <a name="part-3---room-models"></a><span data-ttu-id="96b33-346">Parte 3: modelli di chat Room</span><span class="sxs-lookup"><span data-stu-id="96b33-346">Part 3 - Room Models</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="96b33-347">Concetti chiave</span><span class="sxs-lookup"><span data-stu-id="96b33-347">Key Concepts</span></span>

* <span data-ttu-id="96b33-348">Le dimensioni dello spazio fornisce code subliminali che contribuiscono alla localizzazione audio.</span><span class="sxs-lookup"><span data-stu-id="96b33-348">The size of the space provides subliminal queues that contribute to sound localization.</span></span>
* <span data-ttu-id="96b33-349">I modelli di chat vengono impostati per ogni-**AudioSource**.</span><span class="sxs-lookup"><span data-stu-id="96b33-349">Room models are set per-**AudioSource**.</span></span>
* <span data-ttu-id="96b33-350">Il [MixedRealityToolkit per Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) fornisce codice per impostare il modello di chat room.</span><span class="sxs-lookup"><span data-stu-id="96b33-350">The [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides code for setting the room model.</span></span>
* <span data-ttu-id="96b33-351">Per le esperienze di realtà mista, selezionare il modello di chat che meglio si adatta lo spazio del mondo reale.</span><span class="sxs-lookup"><span data-stu-id="96b33-351">For Mixed Reality experiences, select the room model that best fits the real world space.</span></span>

<span data-ttu-id="96b33-352">Se si sta creando uno scenario di realtà virtuale, selezionare il modello di chat che meglio si adatta l'ambiente virtuale.</span><span class="sxs-lookup"><span data-stu-id="96b33-352">If you are creating a Virtual Reality scenario, select the room model that best fits the virtual environment.</span></span>

## <a name="chapter-4---sound-design"></a><span data-ttu-id="96b33-353">Capitolo 4 - progettazione</span><span class="sxs-lookup"><span data-stu-id="96b33-353">Chapter 4 - Sound Design</span></span>

### <a name="objectives"></a><span data-ttu-id="96b33-354">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="96b33-354">Objectives</span></span>

* <span data-ttu-id="96b33-355">Considerazioni per la progettazione efficace.</span><span class="sxs-lookup"><span data-stu-id="96b33-355">Understand considerations for effective sound design.</span></span>
* <span data-ttu-id="96b33-356">Altre linee guida e le tecniche di combinazione.</span><span class="sxs-lookup"><span data-stu-id="96b33-356">Learn mixing techniques and guidelines.</span></span>

### <a name="part-1---sound-and-experience-design"></a><span data-ttu-id="96b33-357">Parte 1: progettazione dell'esperienza e suono</span><span class="sxs-lookup"><span data-stu-id="96b33-357">Part 1 - Sound and Experience Design</span></span>

<span data-ttu-id="96b33-358">Questa sezione illustra le linee guida e considerazioni sulla progettazione di esperienza e suono di chiave.</span><span class="sxs-lookup"><span data-stu-id="96b33-358">This section discusses key sound and experience design considerations and guidelines.</span></span>

#### <a name="normalize-all-sounds"></a><span data-ttu-id="96b33-359">Normalizza tutti i file audio</span><span class="sxs-lookup"><span data-stu-id="96b33-359">Normalize all sounds</span></span>

<span data-ttu-id="96b33-360">Questo evita la necessità di codice case speciale regolare i livelli di volume al suono, che può richiedere tempi lunghi e riduce la possibilità di aggiornare facilmente i file audio.</span><span class="sxs-lookup"><span data-stu-id="96b33-360">This avoids the need for special case code to adjust volume levels per sound, which can be time consuming and limits the ability to easily update sound files.</span></span>

#### <a name="design-for-an-untethered-experience"></a><span data-ttu-id="96b33-361">Progettazione per un'esperienza senza i limiti</span><span class="sxs-lookup"><span data-stu-id="96b33-361">Design for an untethered experience</span></span>

<span data-ttu-id="96b33-362">HoloLens è un computer holographic completamente indipendente, senza i limiti.</span><span class="sxs-lookup"><span data-stu-id="96b33-362">HoloLens is a fully contained, untethered holographic computer.</span></span> <span data-ttu-id="96b33-363">Gli utenti possono e userà le proprie esperienze durante lo spostamento.</span><span class="sxs-lookup"><span data-stu-id="96b33-363">Your users can and will use your experiences while moving.</span></span> <span data-ttu-id="96b33-364">Assicurarsi di testare la combinazione di audio scorrendo intorno.</span><span class="sxs-lookup"><span data-stu-id="96b33-364">Be sure to test your audio mix by walking around.</span></span>

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a><span data-ttu-id="96b33-365">Emette un suono da percorsi logici di vntana</span><span class="sxs-lookup"><span data-stu-id="96b33-365">Emit sound from logical locations on your holograms</span></span>

<span data-ttu-id="96b33-366">Nel mondo reale, un cane non abbaiare dalla relativa coda e vocale di un essere umano non proviene dal proprio piedi.</span><span class="sxs-lookup"><span data-stu-id="96b33-366">In the real world, a dog does not bark from its tail and a human's voice does not come from his/her feet.</span></span> <span data-ttu-id="96b33-367">Evitare che i suoni di generano da parti impreviste del vntana.</span><span class="sxs-lookup"><span data-stu-id="96b33-367">Avoid having your sounds emit from unexpected portions of your holograms.</span></span>

<span data-ttu-id="96b33-368">Per piccole vntana, è ammissibile avere suono emit dal centro della geometria.</span><span class="sxs-lookup"><span data-stu-id="96b33-368">For small holograms, it is reasonable to have sound emit from the center of the geometry.</span></span>

#### <a name="familiar-sounds-are-most-localizable"></a><span data-ttu-id="96b33-369">Suoni familiari sono più localizzabili</span><span class="sxs-lookup"><span data-stu-id="96b33-369">Familiar sounds are most localizable</span></span>

<span data-ttu-id="96b33-370">La voce umana e musica sono molto semplici da localizzare.</span><span class="sxs-lookup"><span data-stu-id="96b33-370">The human voice and music are very easy to localize.</span></span> <span data-ttu-id="96b33-371">Se qualcuno chiama il proprio nome, si è in grado di molto accuratamente determinare da quale direzione proviene dalla voce e da come a portata di mano.</span><span class="sxs-lookup"><span data-stu-id="96b33-371">If someone calls your name, you are able to very accurately determine from what direction the voice came and from how far away.</span></span> <span data-ttu-id="96b33-372">Suoni familiarità e breve sono più difficili da localizzare.</span><span class="sxs-lookup"><span data-stu-id="96b33-372">Short, unfamiliar sounds are harder to localize.</span></span>

#### <a name="be-cognizant-of-user-expectations"></a><span data-ttu-id="96b33-373">Tenere conto del fatto delle aspettative dell'utente</span><span class="sxs-lookup"><span data-stu-id="96b33-373">Be cognizant of user expectations</span></span>

<span data-ttu-id="96b33-374">Esperienza riveste un ruolo nella nostra capacità di identificare la posizione di un suono.</span><span class="sxs-lookup"><span data-stu-id="96b33-374">Life experience plays a part in our ability to identify the location of a sound.</span></span> <span data-ttu-id="96b33-375">Questo è il motivo per cui la voce umana è particolarmente semplice da localizzare.</span><span class="sxs-lookup"><span data-stu-id="96b33-375">This is one reason why the human voice is particularly easy to localize.</span></span> <span data-ttu-id="96b33-376">È importante essere a conoscenza delle aspettative appreso dell'utente quando si posiziona i suoni.</span><span class="sxs-lookup"><span data-stu-id="96b33-376">It is important to be aware of your user's learned expectations when placing your sounds.</span></span>

<span data-ttu-id="96b33-377">Ad esempio, quando un utente ascolta un brano musicale bird generalmente risultino verso l'alto, come quelle volatili tendono a essere sopra la linea di visuale sul (volanti o in una struttura ad albero).</span><span class="sxs-lookup"><span data-stu-id="96b33-377">For example, when someone hears a bird song they generally look up, as birds tend to be above the line of sight (flying or in a tree).</span></span> <span data-ttu-id="96b33-378">Non è insolito per un utente di attivare nella direzione corretta di un file audio, ma Cerca in direzione verticale errata e diventare confusi o frustrato quando non è possibile trovare l'ologramma.</span><span class="sxs-lookup"><span data-stu-id="96b33-378">It is not uncommon for a user to turn in the correct direction of a sound, but look in the wrong vertical direction and become confused or frustrated when they are unable to find the hologram.</span></span>

#### <a name="avoid-hidden-emitters"></a><span data-ttu-id="96b33-379">Evitare di istanze di emissione FixIt nascosti</span><span class="sxs-lookup"><span data-stu-id="96b33-379">Avoid hidden emitters</span></span>

<span data-ttu-id="96b33-380">Nel mondo reale, se abbiamo riprodotto un suono, in genere è possibile identificare l'oggetto che sta generando l'audio.</span><span class="sxs-lookup"><span data-stu-id="96b33-380">In the real world, if we hear a sound, we can generally identify the object that is emitting the sound.</span></span> <span data-ttu-id="96b33-381">Questo inoltre deve restituire true nelle proprie esperienze.</span><span class="sxs-lookup"><span data-stu-id="96b33-381">This should also hold true in your experiences.</span></span> <span data-ttu-id="96b33-382">Può costituire un problema molto agli utenti di ascoltare un suono, sapere da dove proviene l'audio e in grado di rilevare un oggetto.</span><span class="sxs-lookup"><span data-stu-id="96b33-382">It can be very disconcerting for users to hear a sound, know from where the sound originates and be unable to see an object.</span></span>

<span data-ttu-id="96b33-383">Esistono alcune eccezioni a questa linea guida.</span><span class="sxs-lookup"><span data-stu-id="96b33-383">There are some exceptions to this guideline.</span></span> <span data-ttu-id="96b33-384">Ad esempio, ambiente suoni, ad esempio crickets in un campo non è necessario visibile.</span><span class="sxs-lookup"><span data-stu-id="96b33-384">For example, ambient sounds such as crickets in a field need not be visible.</span></span> <span data-ttu-id="96b33-385">Esperienza ci offre una certa familiarità con l'origine di queste suoni senza la necessità di visualizzarlo.</span><span class="sxs-lookup"><span data-stu-id="96b33-385">Life experience gives us familiarity with the source of these sounds without the need to see it.</span></span>

### <a name="part-2---sound-mixing"></a><span data-ttu-id="96b33-386">Parte 2 - missaggio audio</span><span class="sxs-lookup"><span data-stu-id="96b33-386">Part 2 - Sound Mixing</span></span>

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a><span data-ttu-id="96b33-387">La combinazione per il 70% di HoloLens volume di destinazione</span><span class="sxs-lookup"><span data-stu-id="96b33-387">Target your mix for 70% volume on the HoloLens</span></span>

<span data-ttu-id="96b33-388">Esperienze di realtà miste consentono vntana affinché sia disponibile nel mondo reale.</span><span class="sxs-lookup"><span data-stu-id="96b33-388">Mixed Reality experiences allow holograms to be seen in the real world.</span></span> <span data-ttu-id="96b33-389">Permettono inoltre suoni reali per far valere.</span><span class="sxs-lookup"><span data-stu-id="96b33-389">They should also allow real world sounds to be heard.</span></span> <span data-ttu-id="96b33-390">Una destinazione di 70% del volume consente all'utente di sentire il mondo attorno a esse insieme al suono di tua esperienza.</span><span class="sxs-lookup"><span data-stu-id="96b33-390">A 70% volume target enables the user to hear the world around them along with the sound of your experience.</span></span>

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a><span data-ttu-id="96b33-391">HoloLens al 100% del volume deve finire travolti dai suoni esterni</span><span class="sxs-lookup"><span data-stu-id="96b33-391">HoloLens at 100% volume should drown out external sounds</span></span>

<span data-ttu-id="96b33-392">Un livello di volume pari a 100% equivale a un'esperienza di realtà virtuale.</span><span class="sxs-lookup"><span data-stu-id="96b33-392">A volume level of 100% is akin to a Virtual Reality experience.</span></span> <span data-ttu-id="96b33-393">In modo visivo, l'utente viene trasportato al mondo.</span><span class="sxs-lookup"><span data-stu-id="96b33-393">Visually, the user is transported to a different world.</span></span> <span data-ttu-id="96b33-394">Lo stesso debba valere anche acustico.</span><span class="sxs-lookup"><span data-stu-id="96b33-394">The same should hold true audibly.</span></span>

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a><span data-ttu-id="96b33-395">Utilizzare il AudioMixer Unity per regolare le categorie di suoni</span><span class="sxs-lookup"><span data-stu-id="96b33-395">Use the Unity AudioMixer to adjust categories of sounds</span></span>

<span data-ttu-id="96b33-396">Quando si progetta la combinazione, è spesso utile creare categorie di audio e hanno la possibilità di aumentare o diminuire il volume come unità.</span><span class="sxs-lookup"><span data-stu-id="96b33-396">When designing your mix, it is often helpful to create sound categories and have the ability to increase or decrease their volume as a unit.</span></span> <span data-ttu-id="96b33-397">Ciò consente di mantenere i livelli relativi di ogni file audio durante l'abilitazione delle modifiche di facile e veloce per la combinazione globale.</span><span class="sxs-lookup"><span data-stu-id="96b33-397">This retains the relative levels of each sound while enabling quick and easy changes to the overall mix.</span></span> <span data-ttu-id="96b33-398">Categorie comuni sono rappresentati da: effetti sonori, atmosfera, passaggi vocali e musica.</span><span class="sxs-lookup"><span data-stu-id="96b33-398">Common categories include; sound effects, ambience, voice overs and background music.</span></span>

#### <a name="mix-sounds-based-on-the-users-gaze"></a><span data-ttu-id="96b33-399">Combinare i suoni basati sguardo dell'utente</span><span class="sxs-lookup"><span data-stu-id="96b33-399">Mix sounds based on the user's gaze</span></span>

<span data-ttu-id="96b33-400">Spesso può essere utile modificare la combinazione di audio durante l'utilizzo basato sulla posizione in cui un utente è (o non) alla ricerca.</span><span class="sxs-lookup"><span data-stu-id="96b33-400">It can often be useful to change the sound mix in your experience based on where a user is (or is not) looking.</span></span> <span data-ttu-id="96b33-401">Uno degli usi comuni per questa tecnica sono per ridurre il livello di volume per vntana esterni al Frame Holographic per renderne più semplice per gli utenti possono concentrarsi sulle informazioni davanti a essi.</span><span class="sxs-lookup"><span data-stu-id="96b33-401">One common use for this technique are to reduce the volume level for holograms that are outside of the Holographic Frame to make it easier for the user to focus on the information in front of them.</span></span> <span data-ttu-id="96b33-402">Un altro utilizzo consiste nell'aumentare il volume di un suono per attirare l'attenzione dell'utente a un evento importante.</span><span class="sxs-lookup"><span data-stu-id="96b33-402">Another use is to increase the volume of a sound to draw the user's attention to an important event.</span></span>

#### <a name="building-your-mix"></a><span data-ttu-id="96b33-403">La combinazione di compilazione</span><span class="sxs-lookup"><span data-stu-id="96b33-403">Building your mix</span></span>

<span data-ttu-id="96b33-404">Quando si compila la combinazione, è consigliabile iniziare con audio in background dell'esperienza e aggiungere i livelli basati importanza.</span><span class="sxs-lookup"><span data-stu-id="96b33-404">When building your mix, it is recommended to start with your experience's background audio and add layers based on importance.</span></span> <span data-ttu-id="96b33-405">Spesso, ciò comporta in ogni livello in quella precedente.</span><span class="sxs-lookup"><span data-stu-id="96b33-405">Often, this results in each layer being louder than the previous.</span></span>

<span data-ttu-id="96b33-406">Immaginando i modi la combinazione come un grafico a imbuto invertito, con meno importante (e in genere silenziosi suoni) nella parte inferiore, è consigliabile per definire la struttura alla combinazione di simile al diagramma seguente.</span><span class="sxs-lookup"><span data-stu-id="96b33-406">Imagining your mix as an inverted funnel, with the least important (and generally quietest sounds) at the bottom, it is recommended to structure your mix similar to the following diagram.</span></span>

![Struttura di combinazione di audio](images/soundlevels.png)

<span data-ttu-id="96b33-408">Voice over di valori sono uno scenario interessante.</span><span class="sxs-lookup"><span data-stu-id="96b33-408">Voice overs are an interesting scenario.</span></span> <span data-ttu-id="96b33-409">Basato sull'esperienza che si sta creando è possibile avere un suono (non localizzato) stereo o spatialize i passaggi di voice.</span><span class="sxs-lookup"><span data-stu-id="96b33-409">Based on the experience you are creating you may wish to have a stereo (not localized) sound or to spatialize your voice overs.</span></span> <span data-ttu-id="96b33-410">Pubblicate da Microsoft due esperienze di illustrare ottimi esempi di ogni scenario.</span><span class="sxs-lookup"><span data-stu-id="96b33-410">Two Microsoft published experiences illustrate excellent examples of each scenario.</span></span>

<span data-ttu-id="96b33-411">[HoloTour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87) utilizza una voce stereo sulla.</span><span class="sxs-lookup"><span data-stu-id="96b33-411">[HoloTour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87) uses a stereo voice over.</span></span> <span data-ttu-id="96b33-412">Quando l'Assistente vocale è descrivere il percorso viene visualizzato, il suono è coerenza e non variare in base alla posizione dell'utente.</span><span class="sxs-lookup"><span data-stu-id="96b33-412">When the narrator is describing the location being viewed, the sound is consistent and does not vary based on the user's position.</span></span> <span data-ttu-id="96b33-413">In questo modo, l'Assistente vocale descrivere la scena senza l'utilizzo di lontano dai suoni spatialized dell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="96b33-413">This enables the narrator to describe the scene without taking away from the spatialized sounds of the environment.</span></span>

<span data-ttu-id="96b33-414">[Frammenti](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) utilizza una voce spatialized su sotto forma di un'indagine.</span><span class="sxs-lookup"><span data-stu-id="96b33-414">[Fragments](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) utilizes a spatialized voice over in the form of a detective.</span></span> <span data-ttu-id="96b33-415">Voce del detective viene utilizzato per portare l'attenzione dell'utente a un indizio importante, come se fosse un uomo effettivo nella chat room.</span><span class="sxs-lookup"><span data-stu-id="96b33-415">The detective's voice is used to help bring the user's attention to an important clue as if an actual human was in the room.</span></span> <span data-ttu-id="96b33-416">In questo modo un senso di full immersion nell'esperienza di risolvere il mistero ancora maggiore.</span><span class="sxs-lookup"><span data-stu-id="96b33-416">This enables an even greater sense of immersion into the experience of solving the mystery.</span></span>

### <a name="part-3--performance"></a><span data-ttu-id="96b33-417">Parte 3 - prestazioni</span><span class="sxs-lookup"><span data-stu-id="96b33-417">Part 3 -Performance</span></span>

#### <a name="cpu-usage"></a><span data-ttu-id="96b33-418">Utilizzo della CPU</span><span class="sxs-lookup"><span data-stu-id="96b33-418">CPU usage</span></span>

<span data-ttu-id="96b33-419">Quando si usa spaziale suono, 10 al 12 istanze di emissione FixIt utilizzerà circa il 12% della CPU.</span><span class="sxs-lookup"><span data-stu-id="96b33-419">When using Spatial Sound, 10 - 12 emitters will consume approximately 12% of the CPU.</span></span>

#### <a name="stream-long-audio-files"></a><span data-ttu-id="96b33-420">File audio lungo Stream</span><span class="sxs-lookup"><span data-stu-id="96b33-420">Stream long audio files</span></span>

<span data-ttu-id="96b33-421">Dati audio possono essere grandi, specialmente le frequenze di campionamento più comuni (48 e 44,1 kHz).</span><span class="sxs-lookup"><span data-stu-id="96b33-421">Audio data can be large, especially at common sample rates (44.1 and 48 kHz).</span></span> <span data-ttu-id="96b33-422">In generale è che i file audio più di circa 5-10 secondi dovrebbero essere trasmessi per ridurre l'utilizzo della memoria dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="96b33-422">A general rule is that audio files longer than 5 - 10 seconds should be streamed to reduce application memory usage.</span></span>

<span data-ttu-id="96b33-423">In Unity, è possibile contrassegnare un file audio per il flusso in impostazioni di importazione del file.</span><span class="sxs-lookup"><span data-stu-id="96b33-423">In Unity, you can mark an audio file for streaming in the file's import settings.</span></span>

![Impostazioni di importazione audio](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a><span data-ttu-id="96b33-425">Capitolo 5 - effetti speciali</span><span class="sxs-lookup"><span data-stu-id="96b33-425">Chapter 5 - Special Effects</span></span>

### <a name="objectives"></a><span data-ttu-id="96b33-426">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="96b33-426">Objectives</span></span>

* <span data-ttu-id="96b33-427">Aggiungere profondità "Magic Windows".</span><span class="sxs-lookup"><span data-stu-id="96b33-427">Add depth to "Magic Windows".</span></span>
* <span data-ttu-id="96b33-428">Rendere l'utente del mondo virtuale.</span><span class="sxs-lookup"><span data-stu-id="96b33-428">Bring the user into the virtual world.</span></span>

### <a name="magic-windows"></a><span data-ttu-id="96b33-429">Magic Windows</span><span class="sxs-lookup"><span data-stu-id="96b33-429">Magic Windows</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="96b33-430">Concetti chiave</span><span class="sxs-lookup"><span data-stu-id="96b33-430">Key Concepts</span></span>

* <span data-ttu-id="96b33-431">Creazione di visualizzazioni in un mondo caratterizzato dalla nascosto, è visivamente accattivanti.</span><span class="sxs-lookup"><span data-stu-id="96b33-431">Creating views into a hidden world, is visually compelling.</span></span>
* <span data-ttu-id="96b33-432">Migliorare il realismo aggiungendo effetti audio quando ologramma oppure l'utente si avvicina al mondo nascosto.</span><span class="sxs-lookup"><span data-stu-id="96b33-432">Enhance realism by adding audio effects when a hologram or the user is near the hidden world.</span></span>

#### <a name="instructions"></a><span data-ttu-id="96b33-433">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="96b33-433">Instructions</span></span>

* <span data-ttu-id="96b33-434">Nel **gerarchia** panel, espandere **HologramCollection** e selezionare **Underworld**.</span><span class="sxs-lookup"><span data-stu-id="96b33-434">In the **Hierarchy** panel, expand **HologramCollection** and select **Underworld**.</span></span>
* <span data-ttu-id="96b33-435">Espandere **Underworld** e selezionare **VoiceSource**.</span><span class="sxs-lookup"><span data-stu-id="96b33-435">Expand **Underworld** and select **VoiceSource**.</span></span>
* <span data-ttu-id="96b33-436">Nel **Inspector** del pannello, fare clic su **Add Component** e aggiungere **utente vocale effetto**.</span><span class="sxs-lookup"><span data-stu-id="96b33-436">In the **Inspector** panel, click **Add Component** and add **User Voice Effect**.</span></span>

<span data-ttu-id="96b33-437">Un' **AudioSource** verrà aggiunto al componente **VoiceSource**.</span><span class="sxs-lookup"><span data-stu-id="96b33-437">An **AudioSource** component will be added to **VoiceSource**.</span></span>

* <span data-ttu-id="96b33-438">Nelle **AudioSource**, impostare **Output** al **UserVoice (Mixer)**.</span><span class="sxs-lookup"><span data-stu-id="96b33-438">In **AudioSource**, set **Output** to **UserVoice (Mixer)**.</span></span>
* <span data-ttu-id="96b33-439">Verificare i **Spatialize** casella di controllo.</span><span class="sxs-lookup"><span data-stu-id="96b33-439">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="96b33-440">Trascinare il **Blend spaziali** dispositivo di scorrimento fino alla **3D**, oppure immettere **1** nella casella di modifica.</span><span class="sxs-lookup"><span data-stu-id="96b33-440">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>
* <span data-ttu-id="96b33-441">Espandere **le impostazioni audio 3D**.</span><span class="sxs-lookup"><span data-stu-id="96b33-441">Expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="96b33-442">Impostare **livello Doppler** al **0**.</span><span class="sxs-lookup"><span data-stu-id="96b33-442">Set **Doppler Level** to **0**.</span></span>
* <span data-ttu-id="96b33-443">Nelle **utente vocale effetto**, impostare **oggetto padre** per il **Underworld** dalla scena.</span><span class="sxs-lookup"><span data-stu-id="96b33-443">In **User Voice Effect**, set **Parent Object** to the **Underworld** from the scene.</span></span>
* <span data-ttu-id="96b33-444">Impostare **distanza massima** al **1**.</span><span class="sxs-lookup"><span data-stu-id="96b33-444">Set **Max Distance** to **1**.</span></span>

<span data-ttu-id="96b33-445">L'impostazione **distanza massima** indica **utente vocale effetto** Chiudi modo in cui l'utente deve essere all'oggetto padre prima che l'effetto è abilitato.</span><span class="sxs-lookup"><span data-stu-id="96b33-445">Setting **Max Distance** tells **User Voice Effect** how close the user must be to the parent object before the effect is enabled.</span></span>

* <span data-ttu-id="96b33-446">Nelle **utente vocale effetto**, espandere **coro parametri**.</span><span class="sxs-lookup"><span data-stu-id="96b33-446">In **User Voice Effect**, expand **Chorus Parameters**.</span></span>
* <span data-ttu-id="96b33-447">Impostare **profondità** al **0,1**.</span><span class="sxs-lookup"><span data-stu-id="96b33-447">Set **Depth** to **0.1**.</span></span>
* <span data-ttu-id="96b33-448">Impostare **1 Volume toccare**, **toccare Volume 2** e **toccare Volume 3** al **0.8**.</span><span class="sxs-lookup"><span data-stu-id="96b33-448">Set **Tap 1 Volume**, **Tap 2 Volume** and **Tap 3 Volume** to **0.8**.</span></span>
* <span data-ttu-id="96b33-449">Impostare **Volume audio originali** al **0,5**.</span><span class="sxs-lookup"><span data-stu-id="96b33-449">Set **Original Sound Volume** to **0.5**.</span></span>

<span data-ttu-id="96b33-450">Le impostazioni precedenti configurano i parametri di Unity **AudioChorusFilter** consente di aggiungere tutti i vantaggi per la voce dell'utente.</span><span class="sxs-lookup"><span data-stu-id="96b33-450">The previous settings configure the parameters of the Unity **AudioChorusFilter** used to add richness to the user's voice.</span></span>

* <span data-ttu-id="96b33-451">Nelle **utente vocale effetto**, espandere **Echo parametri**.</span><span class="sxs-lookup"><span data-stu-id="96b33-451">In **User Voice Effect**, expand **Echo Parameters**.</span></span>
* <span data-ttu-id="96b33-452">Impostare **ritardo** a **300**</span><span class="sxs-lookup"><span data-stu-id="96b33-452">Set **Delay** to **300**</span></span>
* <span data-ttu-id="96b33-453">Impostare **Decay Ratio** al **0.2**.</span><span class="sxs-lookup"><span data-stu-id="96b33-453">Set **Decay Ratio** to **0.2**.</span></span>
* <span data-ttu-id="96b33-454">Impostare **Volume audio originali** al **0**.</span><span class="sxs-lookup"><span data-stu-id="96b33-454">Set **Original Sound Volume** to **0**.</span></span>

<span data-ttu-id="96b33-455">Le impostazioni precedenti configurano i parametri di Unity **AudioEchoFilter** utilizzata per determinare la voce dell'utente da restituire.</span><span class="sxs-lookup"><span data-stu-id="96b33-455">The previous settings configure the parameters of the Unity **AudioEchoFilter** used to cause the user's voice to echo.</span></span>

<span data-ttu-id="96b33-456">Lo script utente vocale effetto è responsabile per:</span><span class="sxs-lookup"><span data-stu-id="96b33-456">The User Voice Effect script is responsible for:</span></span>

* <span data-ttu-id="96b33-457">Misurazione della distanza tra l'utente e la **GameObject** al quale è associato lo script.</span><span class="sxs-lookup"><span data-stu-id="96b33-457">Measuring the distance between the user and the **GameObject** to which the script is attached.</span></span>
* <span data-ttu-id="96b33-458">Che determina se l'utente è rivolta la **GameObject**.</span><span class="sxs-lookup"><span data-stu-id="96b33-458">Determining whether or not the user is facing the **GameObject**.</span></span>

<span data-ttu-id="96b33-459">L'utente deve essere rivolto il GameObject, indipendentemente dalla distanza, per l'effetto deve essere abilitata.</span><span class="sxs-lookup"><span data-stu-id="96b33-459">The user must be facing the GameObject, regardless of distance, for the effect to be enabled.</span></span>

* <span data-ttu-id="96b33-460">Applicazione e configurazione di un' **AudioChorusFilter** e un **AudioEchoFilter** per il **AudioSource**.</span><span class="sxs-lookup"><span data-stu-id="96b33-460">Applying and configuring an **AudioChorusFilter** and an **AudioEchoFilter** to the **AudioSource**.</span></span>
* <span data-ttu-id="96b33-461">Disabilitare l'effetto Disabilitando i filtri.</span><span class="sxs-lookup"><span data-stu-id="96b33-461">Disabling the effect by disabling the filters.</span></span>

<span data-ttu-id="96b33-462">Effetto vocale utente utilizza il componente Mic Stream Selector, dal [MixedRealityToolkit per Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), per selezionare il flusso di qualità elevata vocali e distribuirla nel sistema audio di Unity.</span><span class="sxs-lookup"><span data-stu-id="96b33-462">User Voice Effect uses the Mic Stream Selector component, from the [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), to select the high quality voice stream and route it into Unity's audio system.</span></span>

* <span data-ttu-id="96b33-463">Nel **gerarchia** Pannello di selezione **responsabili**.</span><span class="sxs-lookup"><span data-stu-id="96b33-463">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="96b33-464">Nel **Inspector** panel, espandere **gestore di Input vocale**.</span><span class="sxs-lookup"><span data-stu-id="96b33-464">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="96b33-465">Nelle **gestore di Input vocale**, espandere **Underworld Mostra**.</span><span class="sxs-lookup"><span data-stu-id="96b33-465">In **Speech Input Handler**, expand **Show Underworld**.</span></span>
* <span data-ttu-id="96b33-466">Change **alcuna funzione** al **UnderworldBase.OnEnable**.</span><span class="sxs-lookup"><span data-stu-id="96b33-466">Change **No Function** to **UnderworldBase.OnEnable**.</span></span>

![parola chiave: Underworld Show](images/showunderworld.png)

* <span data-ttu-id="96b33-468">Espandere **nascondere Underworld**.</span><span class="sxs-lookup"><span data-stu-id="96b33-468">Expand **Hide Underworld**.</span></span>
* <span data-ttu-id="96b33-469">Change **alcuna funzione** al **UnderworldBase.OnDisable**.</span><span class="sxs-lookup"><span data-stu-id="96b33-469">Change **No Function** to **UnderworldBase.OnDisable**.</span></span>

![parola chiave: Nascondi Underworld](images/hideunderworld.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="96b33-471">Compilare e distribuire</span><span class="sxs-lookup"><span data-stu-id="96b33-471">Build and Deploy</span></span>

* <span data-ttu-id="96b33-472">Come in precedenza, compilare il progetto in Unity e distribuzione in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="96b33-472">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="96b33-473">Dopo aver distribuita l'applicazione:</span><span class="sxs-lookup"><span data-stu-id="96b33-473">After the application is deployed:</span></span>

* <span data-ttu-id="96b33-474">Devono affrontare una superficie (parete, floor, tabella) e scelgo *"Mostra Underworld"*.</span><span class="sxs-lookup"><span data-stu-id="96b33-474">Face a surface (wall, floor, table) and say *"Show Underworld"*.</span></span>

<span data-ttu-id="96b33-475">Verrà visualizzato il underworld e verrà nascoste tutte le altre vntana.</span><span class="sxs-lookup"><span data-stu-id="96b33-475">The underworld will be shown and all other holograms will be hidden.</span></span> <span data-ttu-id="96b33-476">Se non viene visualizzato il underworld, assicurarsi che si verificano una superficie del mondo reale.</span><span class="sxs-lookup"><span data-stu-id="96b33-476">If you do not see the underworld, ensure that you are facing a real-world surface.</span></span>

* <span data-ttu-id="96b33-477">Approccio interno 1 metro di ologramma underworld e avviare discussioni.</span><span class="sxs-lookup"><span data-stu-id="96b33-477">Approach within 1 meter of the underworld hologram and start talking.</span></span>

<span data-ttu-id="96b33-478">Sono ora disponibili effetti audio per la voce dell'utente.</span><span class="sxs-lookup"><span data-stu-id="96b33-478">There are now audio effects applied to your voice!</span></span>

* <span data-ttu-id="96b33-479">Abbandoneranno l'underworld e notare come l'effetto non è più applicata.</span><span class="sxs-lookup"><span data-stu-id="96b33-479">Turn away from the underworld and notice how the effect is no longer applied.</span></span>
* <span data-ttu-id="96b33-480">Pronunciare *"Nascondi Underworld"* per nascondere il underworld.</span><span class="sxs-lookup"><span data-stu-id="96b33-480">Say *"Hide Underworld"* to hide the underworld.</span></span>

<span data-ttu-id="96b33-481">Sarà nascosto il underworld e verrà visualizzato nuovamente il vntana nascoste in precedenza.</span><span class="sxs-lookup"><span data-stu-id="96b33-481">The underworld will be hidden and the previously hidden holograms will reappear.</span></span>

## <a name="the-end"></a><span data-ttu-id="96b33-482">La fine</span><span class="sxs-lookup"><span data-stu-id="96b33-482">The End</span></span>

<span data-ttu-id="96b33-483">La procedura è stata completata.</span><span class="sxs-lookup"><span data-stu-id="96b33-483">Congratulations!</span></span> <span data-ttu-id="96b33-484">Sono stati completati **SIG spaziali 220: Suono spaziale**.</span><span class="sxs-lookup"><span data-stu-id="96b33-484">You have now completed **MR Spatial 220: Spatial sound**.</span></span>

<span data-ttu-id="96b33-485">Rimanere in ascolto per il mondo e portare le proprie esperienze accattivanti con suono!</span><span class="sxs-lookup"><span data-stu-id="96b33-485">Listen to the world and bring your experiences to life with sound!</span></span>

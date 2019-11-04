---
title: MR Spatial 220-audio spaziale
description: Seguire questa procedura dettagliata di codifica usando Unity, Visual Studio e HoloLens per informazioni dettagliate sui concetti relativi ai suoni spaziali.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academy, esercitazione, spazio audio
ms.openlocfilehash: a3fc054927d73cf9ac21f831caa4ec23875977bd
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434731"
---
>[!NOTE]
><span data-ttu-id="c407f-104">Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.</span><span class="sxs-lookup"><span data-stu-id="c407f-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="c407f-105">Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.</span><span class="sxs-lookup"><span data-stu-id="c407f-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="c407f-106">Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="c407f-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="c407f-107">Verranno mantenuti per continuare a usare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="c407f-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="c407f-108">Per HoloLens 2 è stata pubblicata [una nuova serie di esercitazioni](mrlearning-base.md) .</span><span class="sxs-lookup"><span data-stu-id="c407f-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

# <a name="mr-spatial-220-spatial-sound"></a><span data-ttu-id="c407f-109">MR Spatial 220: audio spaziale</span><span class="sxs-lookup"><span data-stu-id="c407f-109">MR Spatial 220: Spatial sound</span></span>

<span data-ttu-id="c407f-110">Il [suono spaziale](spatial-sound.md) respira la vita negli ologrammi e offre loro la presenza nel nostro mondo.</span><span class="sxs-lookup"><span data-stu-id="c407f-110">[Spatial sound](spatial-sound.md) breathes life into holograms and gives them presence in our world.</span></span> <span data-ttu-id="c407f-111">Gli ologrammi sono costituiti da luci e suoni e, se si perde la visione degli ologrammi, il suono spaziale può aiutarti a trovarli.</span><span class="sxs-lookup"><span data-stu-id="c407f-111">Holograms are composed of both light and sound, and if you happen to lose sight of your holograms, spatial sound can help you find them.</span></span> <span data-ttu-id="c407f-112">Il suono spaziale non è analogo a quello tipico che è possibile sentire sulla radio, è un suono posizionato nello spazio 3D.</span><span class="sxs-lookup"><span data-stu-id="c407f-112">Spatial sound is not like the typical sound that you would hear on the radio, it is sound that is positioned in 3D space.</span></span> <span data-ttu-id="c407f-113">Con il suono spaziale è possibile far sembrare gli ologrammi come se fossero dietro di te, accanto a te o persino in testa!</span><span class="sxs-lookup"><span data-stu-id="c407f-113">With spatial sound, you can make holograms sound like they're behind you, next to you, or even on your head!</span></span> <span data-ttu-id="c407f-114">In questo corso verrà:</span><span class="sxs-lookup"><span data-stu-id="c407f-114">In this course, you will:</span></span>

* <span data-ttu-id="c407f-115">Configurare l'ambiente di sviluppo per l'utilizzo di audio spaziale Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c407f-115">Configure your development environment to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="c407f-116">Usare il suono spaziale per migliorare le interazioni.</span><span class="sxs-lookup"><span data-stu-id="c407f-116">Use Spatial Sound to enhance interactions.</span></span>
* <span data-ttu-id="c407f-117">Utilizzare il suono spaziale insieme al [mapping spaziale](spatial-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="c407f-117">Use Spatial Sound in conjunction with [Spatial Mapping](spatial-mapping.md).</span></span>
* <span data-ttu-id="c407f-118">Comprendere le procedure consigliate per la progettazione e la combinazione di suoni.</span><span class="sxs-lookup"><span data-stu-id="c407f-118">Understand sound design and mixing best practices.</span></span>
* <span data-ttu-id="c407f-119">Usare il suono per migliorare gli effetti speciali e coinvolgere l'utente nel mondo della realtà mista.</span><span class="sxs-lookup"><span data-stu-id="c407f-119">Use sound to enhance special effects and bring the user into the Mixed Reality world.</span></span>

## <a name="device-support"></a><span data-ttu-id="c407f-120">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="c407f-120">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="c407f-121">Corso</span><span class="sxs-lookup"><span data-stu-id="c407f-121">Course</span></span></th><th style="width:150px"> <span data-ttu-id="c407f-122"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="c407f-122"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="c407f-123"><a href="immersive-headset-hardware-details.md">Visori VR immersive</a></span><span class="sxs-lookup"><span data-stu-id="c407f-123"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="c407f-124">MR Spatial 220: audio spaziale</span><span class="sxs-lookup"><span data-stu-id="c407f-124">MR Spatial 220: Spatial sound</span></span></td><td style="text-align: center;"> <span data-ttu-id="c407f-125">✔️</span><span class="sxs-lookup"><span data-stu-id="c407f-125">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="c407f-126">✔️</span><span class="sxs-lookup"><span data-stu-id="c407f-126">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="c407f-127">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="c407f-127">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="c407f-128">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="c407f-128">Prerequisites</span></span>

* <span data-ttu-id="c407f-129">Un PC Windows 10 configurato con gli [strumenti corretti installati](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="c407f-129">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="c407f-130">Alcune funzionalità C# di programmazione di base.</span><span class="sxs-lookup"><span data-stu-id="c407f-130">Some basic C# programming ability.</span></span>
* <span data-ttu-id="c407f-131">Sono state completate le [nozioni di base 101](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="c407f-131">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="c407f-132">Un dispositivo HoloLens [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="c407f-132">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="c407f-133">File di progetto</span><span class="sxs-lookup"><span data-stu-id="c407f-133">Project files</span></span>

* <span data-ttu-id="c407f-134">Scaricare i [file](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) richiesti dal progetto.</span><span class="sxs-lookup"><span data-stu-id="c407f-134">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) required by the project.</span></span><span data-ttu-id="c407f-135"> Richiede Unity 2017,2 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="c407f-135"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="c407f-136">Se è ancora necessario il supporto per Unity 5,6, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip).</span><span class="sxs-lookup"><span data-stu-id="c407f-136">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip).</span></span> <span data-ttu-id="c407f-137">Questa versione potrebbe non essere più aggiornata.</span><span class="sxs-lookup"><span data-stu-id="c407f-137">This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="c407f-138">Se è ancora necessario il supporto per Unity 5,5, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip).</span><span class="sxs-lookup"><span data-stu-id="c407f-138">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip).</span></span><span data-ttu-id="c407f-139"> Questa versione potrebbe non essere più aggiornata.</span><span class="sxs-lookup"><span data-stu-id="c407f-139"> This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="c407f-140">Se è ancora necessario il supporto per Unity 5,4, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip).</span><span class="sxs-lookup"><span data-stu-id="c407f-140">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip).</span></span><span data-ttu-id="c407f-141"> Questa versione potrebbe non essere più aggiornata.</span><span class="sxs-lookup"><span data-stu-id="c407f-141"> This release may no longer be up-to-date.</span></span>
* <span data-ttu-id="c407f-142">Annullare l'archiviazione dei file sul desktop o in un'altra posizione facile da raggiungere.</span><span class="sxs-lookup"><span data-stu-id="c407f-142">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="c407f-143">Se si vuole esaminare il codice sorgente prima del download, è [disponibile in GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).</span><span class="sxs-lookup"><span data-stu-id="c407f-143">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="c407f-144">Errori e note</span><span class="sxs-lookup"><span data-stu-id="c407f-144">Errata and Notes</span></span>

* <span data-ttu-id="c407f-145">"Enable Just My Code" deve essere disabilitato (*deselezionato*) in Visual Studio in strumenti-Opzioni >-> debug per raggiungere i punti di interruzione nel codice.</span><span class="sxs-lookup"><span data-stu-id="c407f-145">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="c407f-146">Capitolo 1-installazione di Unity</span><span class="sxs-lookup"><span data-stu-id="c407f-146">Chapter 1 - Unity Setup</span></span>

### <a name="objectives"></a><span data-ttu-id="c407f-147">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="c407f-147">Objectives</span></span>

* <span data-ttu-id="c407f-148">Modificare la configurazione audio di Unity per l'uso del suono Microsoft Spatial.</span><span class="sxs-lookup"><span data-stu-id="c407f-148">Change Unity's sound configuration to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="c407f-149">Aggiungere un suono 3D a un oggetto in Unity.</span><span class="sxs-lookup"><span data-stu-id="c407f-149">Add 3D sound to an object in Unity.</span></span>

### <a name="instructions"></a><span data-ttu-id="c407f-150">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="c407f-150">Instructions</span></span>

* <span data-ttu-id="c407f-151">Avvia Unity.</span><span class="sxs-lookup"><span data-stu-id="c407f-151">Start Unity.</span></span>
* <span data-ttu-id="c407f-152">Selezionare **Apri**.</span><span class="sxs-lookup"><span data-stu-id="c407f-152">Select **Open**.</span></span>
* <span data-ttu-id="c407f-153">Passare al desktop e trovare la cartella precedentemente non archiviata.</span><span class="sxs-lookup"><span data-stu-id="c407f-153">Navigate to your Desktop and find the folder you previously un-archived.</span></span>
* <span data-ttu-id="c407f-154">Fare clic sulla cartella **Starting\Decibel** , quindi premere il pulsante **Seleziona cartella** .</span><span class="sxs-lookup"><span data-stu-id="c407f-154">Click on the **Starting\Decibel** folder and then press the **Select Folder** button.</span></span>
* <span data-ttu-id="c407f-155">Attendere che il progetto venga caricato in Unity.</span><span class="sxs-lookup"><span data-stu-id="c407f-155">Wait for the project to load in Unity.</span></span>
* <span data-ttu-id="c407f-156">Nel pannello del **progetto** aprire **Scenes\Decibel.Unity**.</span><span class="sxs-lookup"><span data-stu-id="c407f-156">In the **Project** panel, open **Scenes\Decibel.unity**.</span></span>
* <span data-ttu-id="c407f-157">Nel pannello **gerarchia** espandere **ologrammcollection** e selezionare **P0LY**.</span><span class="sxs-lookup"><span data-stu-id="c407f-157">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="c407f-158">Nel controllo espandere **audiosource** e notare che non è presente alcuna casella di controllo **Spatialize** .</span><span class="sxs-lookup"><span data-stu-id="c407f-158">In the Inspector, expand **AudioSource** and notice that there is no **Spatialize** check box.</span></span>

<span data-ttu-id="c407f-159">Per impostazione predefinita, Unity non carica un plug-in Spatializer.</span><span class="sxs-lookup"><span data-stu-id="c407f-159">By default, Unity does not load a spatializer plugin.</span></span> <span data-ttu-id="c407f-160">Nei passaggi seguenti viene abilitato il suono spaziale nel progetto.</span><span class="sxs-lookup"><span data-stu-id="c407f-160">The following steps will enable Spatial Sound in the project.</span></span>

* <span data-ttu-id="c407f-161">Nel menu principale di Unity scegliere **modifica > impostazioni progetto > audio**.</span><span class="sxs-lookup"><span data-stu-id="c407f-161">In Unity's top menu, go to **Edit > Project Settings > Audio**.</span></span>
* <span data-ttu-id="c407f-162">Individuare l'elenco a discesa plug-in **Spatializer** e selezionare **MS HRTF Spatializer**.</span><span class="sxs-lookup"><span data-stu-id="c407f-162">Find the **Spatializer Plugin** dropdown, and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="c407f-163">Nel pannello **gerarchia** selezionare **ologrammcollection > P0LY**.</span><span class="sxs-lookup"><span data-stu-id="c407f-163">In the **Hierarchy** panel, select **HologramCollection > P0LY**.</span></span>
* <span data-ttu-id="c407f-164">Nel pannello **Inspector** trovare il componente di **origine audio** .</span><span class="sxs-lookup"><span data-stu-id="c407f-164">In the **Inspector** panel, find the **Audio Source** component.</span></span>
* <span data-ttu-id="c407f-165">Selezionare la casella di controllo **Spatialize** .</span><span class="sxs-lookup"><span data-stu-id="c407f-165">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="c407f-166">Trascinare il dispositivo di scorrimento di **Blend spaziale** fino a **3D**oppure immettere **1** nella casella di modifica.</span><span class="sxs-lookup"><span data-stu-id="c407f-166">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>

<span data-ttu-id="c407f-167">Il progetto verrà ora compilato in Unity e la soluzione verrà configurata in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c407f-167">We will now build the project in Unity and configure the solution in Visual Studio.</span></span>

1. <span data-ttu-id="c407f-168">In Unity selezionare **File > impostazioni di compilazione**.</span><span class="sxs-lookup"><span data-stu-id="c407f-168">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="c407f-169">Fare clic su **Aggiungi scene aperte** per aggiungere la scena.</span><span class="sxs-lookup"><span data-stu-id="c407f-169">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="c407f-170">Selezionare **piattaforma UWP (Universal Windows Platform)** nell'elenco **piattaforma** e fare clic su **Cambia piattaforma**.</span><span class="sxs-lookup"><span data-stu-id="c407f-170">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="c407f-171">Se si sta sviluppando in modo specifico per HoloLens, impostare **dispositivo di destinazione** su **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="c407f-171">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="c407f-172">In caso contrario, lasciarlo in **qualsiasi dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="c407f-172">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="c407f-173">Verificare che **tipo di compilazione** sia impostato su **D3D** e che l' **SDK** sia impostato su **installato più recente** (che deve essere SDK 16299 o versione successiva).</span><span class="sxs-lookup"><span data-stu-id="c407f-173">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="c407f-174">Fai clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="c407f-174">Click **Build**.</span></span>
7. <span data-ttu-id="c407f-175">Creare una **nuova cartella** denominata "app".</span><span class="sxs-lookup"><span data-stu-id="c407f-175">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="c407f-176">Fare clic sulla cartella dell' **app** .</span><span class="sxs-lookup"><span data-stu-id="c407f-176">Single click the **App** folder.</span></span>
9. <span data-ttu-id="c407f-177">Premere **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="c407f-177">Press **Select Folder**.</span></span>

<span data-ttu-id="c407f-178">Quando si esegue Unity, viene visualizzata una finestra Esplora file.</span><span class="sxs-lookup"><span data-stu-id="c407f-178">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="c407f-179">Aprire la cartella dell' **app** .</span><span class="sxs-lookup"><span data-stu-id="c407f-179">Open the **App** folder.</span></span>
2. <span data-ttu-id="c407f-180">Aprire la **soluzione decibel di Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="c407f-180">Open the **Decibel Visual Studio Solution**.</span></span>

<span data-ttu-id="c407f-181">Se si esegue la distribuzione in HoloLens:</span><span class="sxs-lookup"><span data-stu-id="c407f-181">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="c407f-182">Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione da debug a **Release** e da ARM a **x86**.</span><span class="sxs-lookup"><span data-stu-id="c407f-182">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="c407f-183">Fare clic sulla freccia a discesa accanto al pulsante computer locale e selezionare **computer remoto**.</span><span class="sxs-lookup"><span data-stu-id="c407f-183">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="c407f-184">Immettere **l'indirizzo IP del dispositivo HoloLens** e impostare la modalità di autenticazione su **universale (protocollo non crittografato)** .</span><span class="sxs-lookup"><span data-stu-id="c407f-184">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="c407f-185">Fare clic su **Seleziona**.</span><span class="sxs-lookup"><span data-stu-id="c407f-185">Click **Select**.</span></span> <span data-ttu-id="c407f-186">Se non si conosce l'indirizzo IP del dispositivo, vedere **impostazioni > rete & Internet > opzioni avanzate**.</span><span class="sxs-lookup"><span data-stu-id="c407f-186">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="c407f-187">Nella barra dei menu superiore fare clic su **debug-> avvia senza eseguire debug** o premere **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="c407f-187">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="c407f-188">Se questa è la prima volta che si esegue la distribuzione nel dispositivo, sarà necessario [associarla a Visual Studio](using-visual-studio.md#pairing-your-device).</span><span class="sxs-lookup"><span data-stu-id="c407f-188">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device).</span></span>

<span data-ttu-id="c407f-189">Se si esegue la distribuzione in un auricolare immersivo:</span><span class="sxs-lookup"><span data-stu-id="c407f-189">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="c407f-190">Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione da debug a **Release** e da ARM a **x64**.</span><span class="sxs-lookup"><span data-stu-id="c407f-190">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="c407f-191">Verificare che la destinazione di distribuzione sia impostata su **computer locale**.</span><span class="sxs-lookup"><span data-stu-id="c407f-191">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="c407f-192">Nella barra dei menu superiore fare clic su **debug-> avvia senza eseguire debug** o premere **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="c407f-192">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>

## <a name="chapter-2---spatial-sound-and-interaction"></a><span data-ttu-id="c407f-193">Capitolo 2-audio e interazione spaziali</span><span class="sxs-lookup"><span data-stu-id="c407f-193">Chapter 2 - Spatial Sound and Interaction</span></span>

### <a name="objectives"></a><span data-ttu-id="c407f-194">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="c407f-194">Objectives</span></span>

* <span data-ttu-id="c407f-195">Migliorare il Real ologramma usando il suono.</span><span class="sxs-lookup"><span data-stu-id="c407f-195">Enhance hologram realism using sound.</span></span>
* <span data-ttu-id="c407f-196">Indirizzare lo sguardo dell'utente usando un suono.</span><span class="sxs-lookup"><span data-stu-id="c407f-196">Direct the user's gaze using sound.</span></span>
* <span data-ttu-id="c407f-197">Fornire commenti e suggerimenti sui movimenti usando un suono.</span><span class="sxs-lookup"><span data-stu-id="c407f-197">Provide gesture feedback using sound.</span></span>

### <a name="part-1---enhancing-realism"></a><span data-ttu-id="c407f-198">Parte 1-miglioramento del realismo</span><span class="sxs-lookup"><span data-stu-id="c407f-198">Part 1 - Enhancing Realism</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="c407f-199">Concetti chiave</span><span class="sxs-lookup"><span data-stu-id="c407f-199">Key Concepts</span></span>

* <span data-ttu-id="c407f-200">Spatialize ologrammi.</span><span class="sxs-lookup"><span data-stu-id="c407f-200">Spatialize hologram sounds.</span></span>
* <span data-ttu-id="c407f-201">Le origini audio devono essere posizionate in una posizione appropriata nell'ologramma.</span><span class="sxs-lookup"><span data-stu-id="c407f-201">Sound sources should be placed at an appropriate location on the hologram.</span></span>

<span data-ttu-id="c407f-202">Il percorso appropriato per il suono dipende dall'ologramma.</span><span class="sxs-lookup"><span data-stu-id="c407f-202">The appropriate location for the sound is going to depend on the hologram.</span></span> <span data-ttu-id="c407f-203">Se, ad esempio, l'ologramma è umano, l'origine del suono dovrebbe trovarsi vicino alla bocca e non ai piedi.</span><span class="sxs-lookup"><span data-stu-id="c407f-203">For example, if the hologram is of a human, the sound source should be located near the mouth and not the feet.</span></span>

#### <a name="instructions"></a><span data-ttu-id="c407f-204">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="c407f-204">Instructions</span></span>

<span data-ttu-id="c407f-205">Le istruzioni seguenti allegheranno un suono spaziali a un ologramma.</span><span class="sxs-lookup"><span data-stu-id="c407f-205">The following instructions will attach a spatialized sound to a hologram.</span></span>

* <span data-ttu-id="c407f-206">Nel pannello **gerarchia** espandere **ologrammcollection** e selezionare **P0LY**.</span><span class="sxs-lookup"><span data-stu-id="c407f-206">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="c407f-207">Nel pannello di **controllo** , in **audiosource**, fare clic sul cerchio accanto a **AudioClip** e selezionare **polihover** dal menu a comparsa.</span><span class="sxs-lookup"><span data-stu-id="c407f-207">In the **Inspector** panel, in the **AudioSource**, click the circle next to **AudioClip** and select **PolyHover** from the pop-up.</span></span>
* <span data-ttu-id="c407f-208">Fare clic sul cerchio accanto a **output** e selezionare **SoundEffects** dal menu a comparsa.</span><span class="sxs-lookup"><span data-stu-id="c407f-208">Click the circle next to **Output** and select **SoundEffects** from the pop-up.</span></span>

<span data-ttu-id="c407f-209">Il progetto decibel usa un componente **audiomixer** Unity per abilitare la regolazione dei livelli audio per gruppi di suoni.</span><span class="sxs-lookup"><span data-stu-id="c407f-209">Project Decibel uses a Unity **AudioMixer** component to enable adjusting sound levels for groups of sounds.</span></span> <span data-ttu-id="c407f-210">Raggruppando i suoni in questo modo, è possibile modificare il volume complessivo mantenendo il volume relativo di ogni suono.</span><span class="sxs-lookup"><span data-stu-id="c407f-210">By grouping sounds this way, the overall volume can be adjusted while maintaining the relative volume of each sound.</span></span>

* <span data-ttu-id="c407f-211">In **audiosource**espandere **impostazioni audio 3D**.</span><span class="sxs-lookup"><span data-stu-id="c407f-211">In the **AudioSource**, expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="c407f-212">Impostare il **livello di Doppler** su **0**.</span><span class="sxs-lookup"><span data-stu-id="c407f-212">Set **Doppler Level** to **0**.</span></span>

<span data-ttu-id="c407f-213">L'impostazione del livello di Doppler su zero disabilita le modifiche apportate a un pitch causato da un movimento, ovvero l'ologramma o l'utente.</span><span class="sxs-lookup"><span data-stu-id="c407f-213">Setting Doppler level to zero disables changes in pitch caused by motion (either of the hologram or the user).</span></span> <span data-ttu-id="c407f-214">Un esempio classico di Doppler è un'auto in rapida evoluzione.</span><span class="sxs-lookup"><span data-stu-id="c407f-214">A classic example of Doppler is a fast-moving car.</span></span> <span data-ttu-id="c407f-215">Quando l'auto si avvicina a un listener fisso, il pitch del motore aumenta.</span><span class="sxs-lookup"><span data-stu-id="c407f-215">As the car approaches a stationary listener, the pitch of the engine rises.</span></span> <span data-ttu-id="c407f-216">Quando passa il listener, il passo viene ridotto a distanza.</span><span class="sxs-lookup"><span data-stu-id="c407f-216">When it passes the listener, the pitch lowers with distance.</span></span>

### <a name="part-2---directing-the-users-gaze"></a><span data-ttu-id="c407f-217">Parte 2-indirizzare lo sguardo dell'utente</span><span class="sxs-lookup"><span data-stu-id="c407f-217">Part 2 - Directing the User's Gaze</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="c407f-218">Concetti chiave</span><span class="sxs-lookup"><span data-stu-id="c407f-218">Key Concepts</span></span>

* <span data-ttu-id="c407f-219">Usare il suono per richiamare l'attenzione sugli ologrammi importanti.</span><span class="sxs-lookup"><span data-stu-id="c407f-219">Use sound to call attention to important holograms.</span></span>
* <span data-ttu-id="c407f-220">Gli orecchi consentono di indirizzare il punto di vista.</span><span class="sxs-lookup"><span data-stu-id="c407f-220">The ears help direct where the eyes should look.</span></span>
* <span data-ttu-id="c407f-221">Il cervello ha alcune aspettative acquisite.</span><span class="sxs-lookup"><span data-stu-id="c407f-221">The brain has some learned expectations.</span></span>

<span data-ttu-id="c407f-222">Un esempio di aspettative apprese è che gli uccelli si trovano in genere sopra i capi degli uomini.</span><span class="sxs-lookup"><span data-stu-id="c407f-222">One example of learned expectations is that birds are generally above the heads of humans.</span></span> <span data-ttu-id="c407f-223">Se un utente riceve un segnale acustico, la relativa reazione iniziale è la ricerca.</span><span class="sxs-lookup"><span data-stu-id="c407f-223">If a user hears a bird sound, their initial reaction is to look up.</span></span> <span data-ttu-id="c407f-224">L'inserimento di un uccello sotto l'utente può comportare la direzione corretta del suono, ma non è in grado di trovare l'ologramma in base alla necessità di cercare.</span><span class="sxs-lookup"><span data-stu-id="c407f-224">Placing a bird below the user can lead to them facing the correct direction of the sound, but being unable to find the hologram based on the expectation of needing to look up.</span></span>

#### <a name="instructions"></a><span data-ttu-id="c407f-225">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="c407f-225">Instructions</span></span>

<span data-ttu-id="c407f-226">Le istruzioni seguenti consentono a P0LY di nascondersi dietro l'utente, in modo da poter usare il suono per individuare l'ologramma.</span><span class="sxs-lookup"><span data-stu-id="c407f-226">The following instructions enable P0LY to hide behind you, so that you can use sound to locate the hologram.</span></span>

* <span data-ttu-id="c407f-227">Nel pannello **gerarchia** selezionare **Managers**.</span><span class="sxs-lookup"><span data-stu-id="c407f-227">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="c407f-228">Nel pannello **Inspector** trovare gestore di **input vocale**.</span><span class="sxs-lookup"><span data-stu-id="c407f-228">In the **Inspector** panel, find **Speech Input Handler**.</span></span>
* <span data-ttu-id="c407f-229">In **gestore di input vocale**espandere **Vai a Nascondi**.</span><span class="sxs-lookup"><span data-stu-id="c407f-229">In **Speech Input Handler**, expand **Go Hide**.</span></span>
* <span data-ttu-id="c407f-230">Modificare **Nessuna funzione** in **poliactions. GoHide**.</span><span class="sxs-lookup"><span data-stu-id="c407f-230">Change **No Function** to **PolyActions.GoHide**.</span></span>

![Parola chiave: go Hide](images/gohide.png)

### <a name="part-3---gesture-feedback"></a><span data-ttu-id="c407f-232">Parte 3: commenti e suggerimenti sui movimenti</span><span class="sxs-lookup"><span data-stu-id="c407f-232">Part 3 - Gesture Feedback</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="c407f-233">Concetti chiave</span><span class="sxs-lookup"><span data-stu-id="c407f-233">Key Concepts</span></span>

* <span data-ttu-id="c407f-234">Fornire all'utente una conferma positiva del movimento usando un suono</span><span class="sxs-lookup"><span data-stu-id="c407f-234">Provide the user with positive gesture confirmation using sound</span></span>
* <span data-ttu-id="c407f-235">Non sovraccaricare i suoni eccessivamente rumorosi dell'utente</span><span class="sxs-lookup"><span data-stu-id="c407f-235">Do not overwhelm the user - overly loud sounds get in the way</span></span>
* <span data-ttu-id="c407f-236">I rumori sottili funzionano meglio: non offuscare l'esperienza</span><span class="sxs-lookup"><span data-stu-id="c407f-236">Subtle sounds work best - do not overshadow the experience</span></span>

#### <a name="instructions"></a><span data-ttu-id="c407f-237">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="c407f-237">Instructions</span></span>

* <span data-ttu-id="c407f-238">Nel pannello **gerarchia** espandere **ologrammcollection**.</span><span class="sxs-lookup"><span data-stu-id="c407f-238">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="c407f-239">Espandere **EnergyHub** e selezionare **base**.</span><span class="sxs-lookup"><span data-stu-id="c407f-239">Expand **EnergyHub** and select **Base**.</span></span>
* <span data-ttu-id="c407f-240">Nel pannello di **controllo** fare clic su **Aggiungi componente** e aggiungere il **gestore audio del movimento**.</span><span class="sxs-lookup"><span data-stu-id="c407f-240">In the **Inspector** panel, click **Add Component** and add **Gesture Sound Handler**.</span></span>
* <span data-ttu-id="c407f-241">Nel **gestore del suono del movimento**fare clic sul cerchio accanto al clip avviato per la **navigazione** e selezionare il clip **aggiornato** e selezionare **RotateClick** dal menu a comparsa per entrambe.</span><span class="sxs-lookup"><span data-stu-id="c407f-241">In **Gesture Sound Handler**, click the circle next to **Navigation Started Clip** and **Navigation Updated Clip** and select **RotateClick** from the pop-up for both.</span></span>
* <span data-ttu-id="c407f-242">Fare doppio clic su "GestureSoundHandler" per caricare in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c407f-242">Double click on "GestureSoundHandler" to load in Visual Studio.</span></span>

<span data-ttu-id="c407f-243">Il gestore del suono del movimento esegue le attività seguenti:</span><span class="sxs-lookup"><span data-stu-id="c407f-243">Gesture Sound Handler performs the following tasks:</span></span>

* <span data-ttu-id="c407f-244">Creare e configurare un **audiosource**.</span><span class="sxs-lookup"><span data-stu-id="c407f-244">Create and configure an **AudioSource**.</span></span>
* <span data-ttu-id="c407f-245">Inserire **audiosource** nella posizione del **GameObject**appropriato.</span><span class="sxs-lookup"><span data-stu-id="c407f-245">Place the **AudioSource** at the location of the appropriate **GameObject**.</span></span>
* <span data-ttu-id="c407f-246">Riproduce il **AudioClip** associato al movimento.</span><span class="sxs-lookup"><span data-stu-id="c407f-246">Plays the **AudioClip** associated with the gesture.</span></span>

#### <a name="build-and-deploy"></a><span data-ttu-id="c407f-247">Compilazione e distribuzione</span><span class="sxs-lookup"><span data-stu-id="c407f-247">Build and Deploy</span></span>

1. <span data-ttu-id="c407f-248">In Unity selezionare **File > impostazioni di compilazione**.</span><span class="sxs-lookup"><span data-stu-id="c407f-248">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="c407f-249">Fai clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="c407f-249">Click **Build**.</span></span>
3. <span data-ttu-id="c407f-250">Fare clic sulla cartella dell' **app** .</span><span class="sxs-lookup"><span data-stu-id="c407f-250">Single click the **App** folder.</span></span>
4. <span data-ttu-id="c407f-251">Premere **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="c407f-251">Press **Select Folder**.</span></span>

<span data-ttu-id="c407f-252">Controllare che la barra degli strumenti indichi "versione", "x86" o "x64" e "dispositivo remoto".</span><span class="sxs-lookup"><span data-stu-id="c407f-252">Check that the Toolbar says "Release", "x86" or "x64", and "Remote Device".</span></span> <span data-ttu-id="c407f-253">In caso contrario, si tratta dell'istanza di codifica di Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c407f-253">If not, this is the coding instance of Visual Studio.</span></span> <span data-ttu-id="c407f-254">Potrebbe essere necessario aprire nuovamente la soluzione dalla cartella dell'app.</span><span class="sxs-lookup"><span data-stu-id="c407f-254">You may need to re-open the solution from the App folder.</span></span>

* <span data-ttu-id="c407f-255">Se richiesto, ricaricare i file di progetto.</span><span class="sxs-lookup"><span data-stu-id="c407f-255">If prompted, reload the project files.</span></span>
* <span data-ttu-id="c407f-256">Come in precedenza, eseguire la distribuzione da Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c407f-256">As before, deploy from Visual Studio.</span></span>

<span data-ttu-id="c407f-257">Dopo la distribuzione dell'applicazione:</span><span class="sxs-lookup"><span data-stu-id="c407f-257">After the application is deployed:</span></span>

* <span data-ttu-id="c407f-258">Osservare le modifiche apportate al suono quando ci si sposta intorno a P0LY.</span><span class="sxs-lookup"><span data-stu-id="c407f-258">Observe how the sound changes as you move around P0LY.</span></span>
* <span data-ttu-id="c407f-259">Pronunciare *"go Hide"* per fare in modo che P0LY si sposti in una posizione sottostante.</span><span class="sxs-lookup"><span data-stu-id="c407f-259">Say *"Go Hide"* to make P0LY move to a location behind you.</span></span> <span data-ttu-id="c407f-260">Trovarlo in base al suono.</span><span class="sxs-lookup"><span data-stu-id="c407f-260">Find it by the sound.</span></span>
* <span data-ttu-id="c407f-261">Guardare la base dell'hub energia.</span><span class="sxs-lookup"><span data-stu-id="c407f-261">Gaze at the base of the Energy Hub.</span></span> <span data-ttu-id="c407f-262">Toccare e trascinare verso sinistra o destra per ruotare l'ologramma e notare come il suono di clic confermi il movimento.</span><span class="sxs-lookup"><span data-stu-id="c407f-262">Tap and drag left or right to rotate the hologram and notice how the clicking sound confirms the gesture.</span></span>

<span data-ttu-id="c407f-263">Nota: è presente un pannello di testo che tag insieme all'utente.</span><span class="sxs-lookup"><span data-stu-id="c407f-263">Note: There is a text panel that will tag-along with you.</span></span> <span data-ttu-id="c407f-264">Questo conterrà i comandi vocali disponibili che è possibile usare in questo corso.</span><span class="sxs-lookup"><span data-stu-id="c407f-264">This will contain the available voice commands that you can use throughout this course.</span></span>

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a><span data-ttu-id="c407f-265">Capitolo 3-mapping spaziale e spaziale</span><span class="sxs-lookup"><span data-stu-id="c407f-265">Chapter 3 - Spatial Sound and Spatial Mapping</span></span>

### <a name="objectives"></a><span data-ttu-id="c407f-266">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="c407f-266">Objectives</span></span>

* <span data-ttu-id="c407f-267">Confermare l'interazione tra ologrammi e il mondo reale usando un suono.</span><span class="sxs-lookup"><span data-stu-id="c407f-267">Confirm interaction between holograms and the real world using sound.</span></span>
* <span data-ttu-id="c407f-268">Occludere suono che usa il mondo fisico.</span><span class="sxs-lookup"><span data-stu-id="c407f-268">Occlude sound using the physical world.</span></span>

### <a name="part-1---physical-world-interaction"></a><span data-ttu-id="c407f-269">Parte 1: interazione con il mondo fisico</span><span class="sxs-lookup"><span data-stu-id="c407f-269">Part 1 - Physical World Interaction</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="c407f-270">Concetti chiave</span><span class="sxs-lookup"><span data-stu-id="c407f-270">Key Concepts</span></span>

* <span data-ttu-id="c407f-271">In genere, gli oggetti fisici comportano un suono quando si verifica una superficie o un altro oggetto.</span><span class="sxs-lookup"><span data-stu-id="c407f-271">Physical objects generally make a sound when encountering a surface or another object.</span></span>
* <span data-ttu-id="c407f-272">I suoni devono essere appropriati per il contesto all'interno dell'esperienza.</span><span class="sxs-lookup"><span data-stu-id="c407f-272">Sounds should be context appropriate within the experience.</span></span>

<span data-ttu-id="c407f-273">Ad esempio, l'impostazione di un calice in una tabella dovrebbe rendere un suono più tranquillo rispetto alla rimozione di un masso in un pezzo di metallo.</span><span class="sxs-lookup"><span data-stu-id="c407f-273">For example, setting a cup on a table should make a quieter sound than dropping a boulder on a piece of metal.</span></span>

#### <a name="instructions"></a><span data-ttu-id="c407f-274">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="c407f-274">Instructions</span></span>

* <span data-ttu-id="c407f-275">Nel pannello **gerarchia** espandere **ologrammcollection**.</span><span class="sxs-lookup"><span data-stu-id="c407f-275">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="c407f-276">Espandere **EnergyHub**, selezionare **base**.</span><span class="sxs-lookup"><span data-stu-id="c407f-276">Expand **EnergyHub**, select **Base**.</span></span>
* <span data-ttu-id="c407f-277">Nel pannello di **controllo** fare clic su **Aggiungi componente** e aggiungere **toccare per inserire il suono e l'azione**.</span><span class="sxs-lookup"><span data-stu-id="c407f-277">In the **Inspector** panel, click **Add Component** and add **Tap To Place With Sound and Action**.</span></span>
* <span data-ttu-id="c407f-278">In **Tap per inserire il suono e l'azione**:</span><span class="sxs-lookup"><span data-stu-id="c407f-278">In **Tap To Place With Sound and Action**:</span></span>
  * <span data-ttu-id="c407f-279">Controllare la **posizione dell'elemento padre al tocco**.</span><span class="sxs-lookup"><span data-stu-id="c407f-279">Check **Place Parent On Tap**.</span></span>
  * <span data-ttu-id="c407f-280">Impostare il **suono del posizionamento** sul **posto**.</span><span class="sxs-lookup"><span data-stu-id="c407f-280">Set **Placement Sound** to **Place**.</span></span>
  * <span data-ttu-id="c407f-281">Imposta il **suono del pickup** su **pickup**.</span><span class="sxs-lookup"><span data-stu-id="c407f-281">Set **Pickup Sound** to **Pickup**.</span></span>
  * <span data-ttu-id="c407f-282">Premere + in basso a destra sotto l' **azione di prelievo** e **sull'azione di selezione host**.</span><span class="sxs-lookup"><span data-stu-id="c407f-282">Press the + in the bottom right under both **On Pickup Action** and **On Placement Action**.</span></span> <span data-ttu-id="c407f-283">Trascinare EnergyHub dalla scena ai campi **None (Object)** .</span><span class="sxs-lookup"><span data-stu-id="c407f-283">Drag EnergyHub from the scene into the **None (Object)** fields.</span></span>
    * <span data-ttu-id="c407f-284">In **azione di prelievo**fare clic su **Nessuna funzione** -> **EnergyHubBase** -> **ResetAnimation**.</span><span class="sxs-lookup"><span data-stu-id="c407f-284">Under **On Pickup Action**, click on **No Function** -> **EnergyHubBase** -> **ResetAnimation**.</span></span>
    * <span data-ttu-id="c407f-285">In **azione posizionamento**fare clic su **Nessuna funzione** -> **EnergyHubBase** -> **onselect**.</span><span class="sxs-lookup"><span data-stu-id="c407f-285">Under **On Placement Action**, click on **No Function** -> **EnergyHubBase** -> **OnSelect**.</span></span>

![Toccare per inserire il suono e l'azione](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a><span data-ttu-id="c407f-287">Parte 2-occlusione del suono</span><span class="sxs-lookup"><span data-stu-id="c407f-287">Part 2 - Sound Occlusion</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="c407f-288">Concetti chiave</span><span class="sxs-lookup"><span data-stu-id="c407f-288">Key Concepts</span></span>

* <span data-ttu-id="c407f-289">Il suono, come Light, può essere nascosto.</span><span class="sxs-lookup"><span data-stu-id="c407f-289">Sound, like light, can be occluded.</span></span>

<span data-ttu-id="c407f-290">Un esempio classico è una sala concerti.</span><span class="sxs-lookup"><span data-stu-id="c407f-290">A classic example is a concert hall.</span></span> <span data-ttu-id="c407f-291">Quando un listener si trova al di fuori della hall e la porta viene chiusa, la musica emette un suono ovattato.</span><span class="sxs-lookup"><span data-stu-id="c407f-291">When a listener is standing outside of the hall and the door is closed, the music sounds muffled.</span></span> <span data-ttu-id="c407f-292">In genere è presente anche una riduzione del volume.</span><span class="sxs-lookup"><span data-stu-id="c407f-292">There is also typically a reduction in volume.</span></span> <span data-ttu-id="c407f-293">Quando lo sportello viene aperto, l'intero spettro del suono viene udito nel volume effettivo.</span><span class="sxs-lookup"><span data-stu-id="c407f-293">When the door is opened, the full spectrum of the sound is heard at the actual volume.</span></span> <span data-ttu-id="c407f-294">I suoni ad alta frequenza vengono in genere assorbiti più di frequenze basse.</span><span class="sxs-lookup"><span data-stu-id="c407f-294">High frequency sounds are generally absorbed more than low frequencies.</span></span>

#### <a name="instructions"></a><span data-ttu-id="c407f-295">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="c407f-295">Instructions</span></span>

* <span data-ttu-id="c407f-296">Nel pannello **gerarchia** espandere **ologrammcollection** e selezionare **P0LY**.</span><span class="sxs-lookup"><span data-stu-id="c407f-296">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="c407f-297">Nel pannello di **controllo** fare clic su **Aggiungi componente** e Aggiungi **emettitore audio**.</span><span class="sxs-lookup"><span data-stu-id="c407f-297">In the **Inspector** panel, click **Add Component** and add **Audio Emitter**.</span></span>

<span data-ttu-id="c407f-298">La classe Emittor audio fornisce le funzionalità seguenti:</span><span class="sxs-lookup"><span data-stu-id="c407f-298">The Audio Emitter class provides the following features:</span></span>

* <span data-ttu-id="c407f-299">Ripristina tutte le modifiche apportate al volume del **audiosource**.</span><span class="sxs-lookup"><span data-stu-id="c407f-299">Restores any changes to the volume of the **AudioSource**.</span></span>
* <span data-ttu-id="c407f-300">Esegue un oggetto **Physics. RaycastNonAlloc** dalla posizione dell'utente nella direzione del **GameObject** a cui è collegato il **AudioEmitter** .</span><span class="sxs-lookup"><span data-stu-id="c407f-300">Performs a **Physics.RaycastNonAlloc** from the user's position in the direction of the **GameObject** to which the **AudioEmitter** is attached.</span></span>

<span data-ttu-id="c407f-301">Il metodo RaycastNonAlloc viene utilizzato come ottimizzazione delle prestazioni per limitare le allocazioni e il numero di risultati restituiti.</span><span class="sxs-lookup"><span data-stu-id="c407f-301">The RaycastNonAlloc method is used as a performance optimization to limit allocations as well as the number of results returned.</span></span>

* <span data-ttu-id="c407f-302">Per ogni **IAudioInfluencer** rilevato, chiama il metodo **ApplyEffect** .</span><span class="sxs-lookup"><span data-stu-id="c407f-302">For each **IAudioInfluencer** encountered, calls the **ApplyEffect** method.</span></span>
* <span data-ttu-id="c407f-303">Per ogni **IAudioInfluencer** precedente non più rilevata, chiamare il metodo **RemoveEffect** .</span><span class="sxs-lookup"><span data-stu-id="c407f-303">For each previous **IAudioInfluencer** that is no longer encountered, call the **RemoveEffect** method.</span></span>

<span data-ttu-id="c407f-304">Si noti che AudioEmitter viene aggiornato in base alle scale temporali umane, anziché ai singoli frame.</span><span class="sxs-lookup"><span data-stu-id="c407f-304">Note that AudioEmitter updates on human time scales, as opposed to on a per frame basis.</span></span> <span data-ttu-id="c407f-305">Questa operazione viene eseguita perché gli utenti in genere non si spostano abbastanza rapidamente affinché l'effetto debba essere aggiornato con una frequenza maggiore di ogni trimestre o metà di un secondo.</span><span class="sxs-lookup"><span data-stu-id="c407f-305">This is done because humans generally do not move fast enough for the effect to need to be updated more frequently than every quarter or half of a second.</span></span> <span data-ttu-id="c407f-306">Gli ologrammi che si teletrasportano rapidamente da una posizione a un'altra possono suddividere l'illusione.</span><span class="sxs-lookup"><span data-stu-id="c407f-306">Holograms that teleport rapidly from one location to another can break the illusion.</span></span>

* <span data-ttu-id="c407f-307">Nel pannello **gerarchia** espandere **ologrammcollection**.</span><span class="sxs-lookup"><span data-stu-id="c407f-307">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="c407f-308">Espandere **EnergyHub** e selezionare **BlobOutside**.</span><span class="sxs-lookup"><span data-stu-id="c407f-308">Expand **EnergyHub** and select **BlobOutside**.</span></span>
* <span data-ttu-id="c407f-309">Nel pannello di **controllo** fare clic su **Aggiungi componente** e aggiungere **occlusione audio**.</span><span class="sxs-lookup"><span data-stu-id="c407f-309">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="c407f-310">In **occlusione audio**impostare **frequenza di taglio** su **1500**.</span><span class="sxs-lookup"><span data-stu-id="c407f-310">In **Audio Occluder**, set **Cutoff Frequency** to **1500**.</span></span>

<span data-ttu-id="c407f-311">Questa impostazione limita le frequenze AudioSource a 1500 Hz e inferiori.</span><span class="sxs-lookup"><span data-stu-id="c407f-311">This setting limits the AudioSource frequencies to 1500 Hz and below.</span></span>

* <span data-ttu-id="c407f-312">Impostare **volume pass-through** su **0,9**.</span><span class="sxs-lookup"><span data-stu-id="c407f-312">Set **Volume Pass Through** to **0.9**.</span></span>

<span data-ttu-id="c407f-313">Questa impostazione riduce il volume del AudioSource al 90% del livello corrente.</span><span class="sxs-lookup"><span data-stu-id="c407f-313">This setting reduces the volume of the AudioSource to 90% of it's current level.</span></span>

<span data-ttu-id="c407f-314">Occlusione audio implementa IAudioInfluencer per:</span><span class="sxs-lookup"><span data-stu-id="c407f-314">Audio Occluder implements IAudioInfluencer to:</span></span>

* <span data-ttu-id="c407f-315">Applicare un effetto occlusione usando un **AudioLowPassFilter** che viene collegato al **audiosource** gestito acquistare il **AudioEmitter**.</span><span class="sxs-lookup"><span data-stu-id="c407f-315">Apply an occlusion effect using an **AudioLowPassFilter** which gets attached to the **AudioSource** managed buy the **AudioEmitter**.</span></span>
* <span data-ttu-id="c407f-316">Applica l'attenuazione del volume a AudioSource.</span><span class="sxs-lookup"><span data-stu-id="c407f-316">Applies volume attenuation to the AudioSource.</span></span>
* <span data-ttu-id="c407f-317">Disabilita l'effetto impostando una frequenza di taglio neutra e disabilitando il filtro.</span><span class="sxs-lookup"><span data-stu-id="c407f-317">Disables the effect by setting a neutral cutoff frequency and disabling the filter.</span></span>

<span data-ttu-id="c407f-318">La frequenza utilizzata come neutra è 22 kHz (22000 Hz).</span><span class="sxs-lookup"><span data-stu-id="c407f-318">The frequency used as neutral is 22 kHz (22000 Hz).</span></span> <span data-ttu-id="c407f-319">Questa frequenza è stata scelta perché si trova al di sopra della frequenza massima nominale che può essere ascoltata dall'orecchio umano, che non ha alcun effetto discernente sul suono.</span><span class="sxs-lookup"><span data-stu-id="c407f-319">This frequency was chosen due to it being above the nominal maximum frequency that can be heard by the human ear, this making no discernable impact to the sound.</span></span>

* <span data-ttu-id="c407f-320">Nel pannello **gerarchia** selezionare **SpatialMapping**.</span><span class="sxs-lookup"><span data-stu-id="c407f-320">In the **Hierarchy** panel, select **SpatialMapping**.</span></span>
* <span data-ttu-id="c407f-321">Nel pannello di **controllo** fare clic su **Aggiungi componente** e aggiungere **occlusione audio**.</span><span class="sxs-lookup"><span data-stu-id="c407f-321">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="c407f-322">In **occlusione audio**impostare **frequenza di taglio** su **750**.</span><span class="sxs-lookup"><span data-stu-id="c407f-322">In **Audio Occluder**, set **Cutoff Frequency** to **750**.</span></span>

<span data-ttu-id="c407f-323">Quando più occluders si trovano nel percorso tra l'utente e il **AudioEmitter**, viene applicata la frequenza più bassa al filtro.</span><span class="sxs-lookup"><span data-stu-id="c407f-323">When multiple occluders are in the path between the user and the **AudioEmitter**, the lowest frequency is applied to the filter.</span></span>

* <span data-ttu-id="c407f-324">Impostare **volume pass-through** su **0,75**.</span><span class="sxs-lookup"><span data-stu-id="c407f-324">Set **Volume Pass Through** to **0.75**.</span></span>

<span data-ttu-id="c407f-325">Quando più occluders si trovano nel percorso tra l'utente e il **AudioEmitter**, il pass-through del volume viene applicato in aggiunta.</span><span class="sxs-lookup"><span data-stu-id="c407f-325">When multiple occluders are in the path between the user and the **AudioEmitter**, the volume pass through is applied additively.</span></span>

* <span data-ttu-id="c407f-326">Nel pannello **gerarchia** selezionare **Managers**.</span><span class="sxs-lookup"><span data-stu-id="c407f-326">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="c407f-327">Nel pannello **Inspector** espandere gestore di **input vocale**.</span><span class="sxs-lookup"><span data-stu-id="c407f-327">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="c407f-328">In **gestore di input vocale**espandere **Vai a addebiti**.</span><span class="sxs-lookup"><span data-stu-id="c407f-328">In **Speech Input Handler**, expand **Go Charge**.</span></span>
* <span data-ttu-id="c407f-329">Modificare **Nessuna funzione** in **poliactions. GoCharge**.</span><span class="sxs-lookup"><span data-stu-id="c407f-329">Change **No Function** to **PolyActions.GoCharge**.</span></span>

![Parola chiave: go charge](images/gocharge.png)

* <span data-ttu-id="c407f-331">Espandi **.**</span><span class="sxs-lookup"><span data-stu-id="c407f-331">Expand **Come Here**.</span></span>
* <span data-ttu-id="c407f-332">**Non modificare alcuna funzione** in **poliactions. Comeback**.</span><span class="sxs-lookup"><span data-stu-id="c407f-332">Change **No Function** to **PolyActions.ComeBack**.</span></span>

![Parola chiave: qui](images/comehere.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="c407f-334">Compilazione e distribuzione</span><span class="sxs-lookup"><span data-stu-id="c407f-334">Build and Deploy</span></span>

* <span data-ttu-id="c407f-335">Come in precedenza, compilare il progetto in Unity e distribuirlo in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c407f-335">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="c407f-336">Dopo la distribuzione dell'applicazione:</span><span class="sxs-lookup"><span data-stu-id="c407f-336">After the application is deployed:</span></span>

* <span data-ttu-id="c407f-337">Pronunciare *"go charge"* per fare in modo che P0LY entri nell'hub di energia.</span><span class="sxs-lookup"><span data-stu-id="c407f-337">Say *"Go Charge"* to have P0LY enter the Energy Hub.</span></span>

<span data-ttu-id="c407f-338">Si noti la modifica apportata al suono.</span><span class="sxs-lookup"><span data-stu-id="c407f-338">Note the change in the sound.</span></span> <span data-ttu-id="c407f-339">Dovrebbe sembrare ovattato e leggermente più tranquillo.</span><span class="sxs-lookup"><span data-stu-id="c407f-339">It should sound muffled and a little quieter.</span></span> <span data-ttu-id="c407f-340">Se si è in grado di posizionarsi con un muro o un altro oggetto tra l'utente e l'hub energetico, è necessario notare un ulteriore silenziatore del suono a causa dell'occlusione del mondo reale.</span><span class="sxs-lookup"><span data-stu-id="c407f-340">If you are able to position yourself with a wall or other object between you and the Energy Hub, you should notice a further muffling of the sound due to the occlusion by the real world.</span></span>

* <span data-ttu-id="c407f-341">Pronunciare *"qui"* per fare in modo che P0LY lasci l'hub di energia e la posizione in primo piano.</span><span class="sxs-lookup"><span data-stu-id="c407f-341">Say *"Come Here"* to have P0LY leave the Energy Hub and position itself in front of you.</span></span>

<span data-ttu-id="c407f-342">Si noti che l'occlusione audio viene rimossa quando P0LY esce dall'hub di energia.</span><span class="sxs-lookup"><span data-stu-id="c407f-342">Note that the sound occlusion is removed once P0LY exits the Energy Hub.</span></span> <span data-ttu-id="c407f-343">Se si sta ancora sentendo l'occlusione, P0LY potrebbe essere bloccato dal mondo reale.</span><span class="sxs-lookup"><span data-stu-id="c407f-343">If you are still hearing occlusion, P0LY may be occluded by the real world.</span></span> <span data-ttu-id="c407f-344">Provare a eseguire il passaggio per assicurarsi di avere una chiara linea di visibilità per P0LY.</span><span class="sxs-lookup"><span data-stu-id="c407f-344">Try moving to ensure you have a clear line of sight to P0LY.</span></span>

### <a name="part-3---room-models"></a><span data-ttu-id="c407f-345">Parte 3-modelli di chat room</span><span class="sxs-lookup"><span data-stu-id="c407f-345">Part 3 - Room Models</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="c407f-346">Concetti chiave</span><span class="sxs-lookup"><span data-stu-id="c407f-346">Key Concepts</span></span>

* <span data-ttu-id="c407f-347">La dimensione dello spazio fornisce le code subliminali che contribuiscono alla localizzazione del suono.</span><span class="sxs-lookup"><span data-stu-id="c407f-347">The size of the space provides subliminal queues that contribute to sound localization.</span></span>
* <span data-ttu-id="c407f-348">I modelli room sono impostati per ogni**audiosource**.</span><span class="sxs-lookup"><span data-stu-id="c407f-348">Room models are set per-**AudioSource**.</span></span>
* <span data-ttu-id="c407f-349">[MixedRealityToolkit per Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) fornisce il codice per l'impostazione del modello room.</span><span class="sxs-lookup"><span data-stu-id="c407f-349">The [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides code for setting the room model.</span></span>
* <span data-ttu-id="c407f-350">Per esperienze di realtà mista, selezionare il modello room più adatto allo spazio reale.</span><span class="sxs-lookup"><span data-stu-id="c407f-350">For Mixed Reality experiences, select the room model that best fits the real world space.</span></span>

<span data-ttu-id="c407f-351">Se si sta creando uno scenario di realtà virtuale, selezionare il modello room più adatto all'ambiente virtuale.</span><span class="sxs-lookup"><span data-stu-id="c407f-351">If you are creating a Virtual Reality scenario, select the room model that best fits the virtual environment.</span></span>

## <a name="chapter-4---sound-design"></a><span data-ttu-id="c407f-352">Capitolo 4-progettazione audio</span><span class="sxs-lookup"><span data-stu-id="c407f-352">Chapter 4 - Sound Design</span></span>

### <a name="objectives"></a><span data-ttu-id="c407f-353">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="c407f-353">Objectives</span></span>

* <span data-ttu-id="c407f-354">Comprendere le considerazioni relative alla progettazione di un suono efficace.</span><span class="sxs-lookup"><span data-stu-id="c407f-354">Understand considerations for effective sound design.</span></span>
* <span data-ttu-id="c407f-355">Impara a combinare tecniche e linee guida.</span><span class="sxs-lookup"><span data-stu-id="c407f-355">Learn mixing techniques and guidelines.</span></span>

### <a name="part-1---sound-and-experience-design"></a><span data-ttu-id="c407f-356">Parte 1: progettazione di suoni e esperienza</span><span class="sxs-lookup"><span data-stu-id="c407f-356">Part 1 - Sound and Experience Design</span></span>

<span data-ttu-id="c407f-357">In questa sezione vengono illustrate le linee guida e le considerazioni principali relative alla progettazione.</span><span class="sxs-lookup"><span data-stu-id="c407f-357">This section discusses key sound and experience design considerations and guidelines.</span></span>

#### <a name="normalize-all-sounds"></a><span data-ttu-id="c407f-358">Normalizza tutti i suoni</span><span class="sxs-lookup"><span data-stu-id="c407f-358">Normalize all sounds</span></span>

<span data-ttu-id="c407f-359">In questo modo si evita la necessità di codice del case speciale per modificare i livelli del volume per ogni suono, che può richiedere molto tempo e limita la possibilità di aggiornare facilmente i file audio.</span><span class="sxs-lookup"><span data-stu-id="c407f-359">This avoids the need for special case code to adjust volume levels per sound, which can be time consuming and limits the ability to easily update sound files.</span></span>

#### <a name="design-for-an-untethered-experience"></a><span data-ttu-id="c407f-360">Progettazione per un'esperienza non legata</span><span class="sxs-lookup"><span data-stu-id="c407f-360">Design for an untethered experience</span></span>

<span data-ttu-id="c407f-361">HoloLens è un computer olografico completamente indipendente e non tethered.</span><span class="sxs-lookup"><span data-stu-id="c407f-361">HoloLens is a fully contained, untethered holographic computer.</span></span> <span data-ttu-id="c407f-362">Gli utenti possono e utilizzeranno le proprie esperienze durante lo trasferimento.</span><span class="sxs-lookup"><span data-stu-id="c407f-362">Your users can and will use your experiences while moving.</span></span> <span data-ttu-id="c407f-363">Assicurarsi di testare la combinazione di audio aggirando.</span><span class="sxs-lookup"><span data-stu-id="c407f-363">Be sure to test your audio mix by walking around.</span></span>

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a><span data-ttu-id="c407f-364">Emettere un suono da posizioni logiche sugli ologrammi</span><span class="sxs-lookup"><span data-stu-id="c407f-364">Emit sound from logical locations on your holograms</span></span>

<span data-ttu-id="c407f-365">Nel mondo reale, un cane non abbaia dalla coda e la voce umana non proviene dai suoi piedi.</span><span class="sxs-lookup"><span data-stu-id="c407f-365">In the real world, a dog does not bark from its tail and a human's voice does not come from his/her feet.</span></span> <span data-ttu-id="c407f-366">Evitare di creare suoni da parti impreviste degli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="c407f-366">Avoid having your sounds emit from unexpected portions of your holograms.</span></span>

<span data-ttu-id="c407f-367">Per gli ologrammi di piccole dimensioni, è ragionevole avere suono emesso dal centro della geometria.</span><span class="sxs-lookup"><span data-stu-id="c407f-367">For small holograms, it is reasonable to have sound emit from the center of the geometry.</span></span>

#### <a name="familiar-sounds-are-most-localizable"></a><span data-ttu-id="c407f-368">I suoni noti sono più localizzabili</span><span class="sxs-lookup"><span data-stu-id="c407f-368">Familiar sounds are most localizable</span></span>

<span data-ttu-id="c407f-369">La voce e la musica umana sono molto facili da localizzare.</span><span class="sxs-lookup"><span data-stu-id="c407f-369">The human voice and music are very easy to localize.</span></span> <span data-ttu-id="c407f-370">Se un utente chiama il proprio nome, è possibile determinare in modo molto accurato dalla direzione della voce e dal punto in cui si è lontani.</span><span class="sxs-lookup"><span data-stu-id="c407f-370">If someone calls your name, you are able to very accurately determine from what direction the voice came and from how far away.</span></span> <span data-ttu-id="c407f-371">I suoni brevi e non noti sono più difficili da localizzare.</span><span class="sxs-lookup"><span data-stu-id="c407f-371">Short, unfamiliar sounds are harder to localize.</span></span>

#### <a name="be-cognizant-of-user-expectations"></a><span data-ttu-id="c407f-372">Tenere a conoscenza delle aspettative degli utenti</span><span class="sxs-lookup"><span data-stu-id="c407f-372">Be cognizant of user expectations</span></span>

<span data-ttu-id="c407f-373">L'esperienza di vita gioca una parte della capacità di identificare la posizione di un suono.</span><span class="sxs-lookup"><span data-stu-id="c407f-373">Life experience plays a part in our ability to identify the location of a sound.</span></span> <span data-ttu-id="c407f-374">Questo è uno dei motivi per cui la voce umana è particolarmente facile da localizzare.</span><span class="sxs-lookup"><span data-stu-id="c407f-374">This is one reason why the human voice is particularly easy to localize.</span></span> <span data-ttu-id="c407f-375">È importante essere a conoscenza delle aspettative apprese dall'utente quando si posizionano i suoni.</span><span class="sxs-lookup"><span data-stu-id="c407f-375">It is important to be aware of your user's learned expectations when placing your sounds.</span></span>

<span data-ttu-id="c407f-376">Ad esempio, quando qualcuno ascolta un brano di Bird, in genere cerca, perché gli uccelli tendono a essere al di sopra della linea di vista (Flying o in un albero).</span><span class="sxs-lookup"><span data-stu-id="c407f-376">For example, when someone hears a bird song they generally look up, as birds tend to be above the line of sight (flying or in a tree).</span></span> <span data-ttu-id="c407f-377">Non è insolito che un utente accenda la direzione corretta di un suono, ma si trovi nella direzione verticale errata e si confonde o si frustra quando non è in grado di trovare l'ologramma.</span><span class="sxs-lookup"><span data-stu-id="c407f-377">It is not uncommon for a user to turn in the correct direction of a sound, but look in the wrong vertical direction and become confused or frustrated when they are unable to find the hologram.</span></span>

#### <a name="avoid-hidden-emitters"></a><span data-ttu-id="c407f-378">Evitare gli emettitori nascosti</span><span class="sxs-lookup"><span data-stu-id="c407f-378">Avoid hidden emitters</span></span>

<span data-ttu-id="c407f-379">Nel mondo reale, se viene emesso un segnale acustico, in genere è possibile identificare l'oggetto che emette il suono.</span><span class="sxs-lookup"><span data-stu-id="c407f-379">In the real world, if we hear a sound, we can generally identify the object that is emitting the sound.</span></span> <span data-ttu-id="c407f-380">Questa operazione dovrebbe essere valida anche per le proprie esperienze.</span><span class="sxs-lookup"><span data-stu-id="c407f-380">This should also hold true in your experiences.</span></span> <span data-ttu-id="c407f-381">Per gli utenti può essere molto sconcertante ascoltare un suono, sapere da dove ha origine il suono e non essere in grado di visualizzare un oggetto.</span><span class="sxs-lookup"><span data-stu-id="c407f-381">It can be very disconcerting for users to hear a sound, know from where the sound originates and be unable to see an object.</span></span>

<span data-ttu-id="c407f-382">Esistono alcune eccezioni a questa linea guida.</span><span class="sxs-lookup"><span data-stu-id="c407f-382">There are some exceptions to this guideline.</span></span> <span data-ttu-id="c407f-383">Ad esempio, i suoni di ambiente come i cricket in un campo non devono essere visibili.</span><span class="sxs-lookup"><span data-stu-id="c407f-383">For example, ambient sounds such as crickets in a field need not be visible.</span></span> <span data-ttu-id="c407f-384">L'esperienza di vita offre familiarità con l'origine di questi suoni senza la necessità di visualizzarla.</span><span class="sxs-lookup"><span data-stu-id="c407f-384">Life experience gives us familiarity with the source of these sounds without the need to see it.</span></span>

### <a name="part-2---sound-mixing"></a><span data-ttu-id="c407f-385">Parte 2-combinazione di suoni</span><span class="sxs-lookup"><span data-stu-id="c407f-385">Part 2 - Sound Mixing</span></span>

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a><span data-ttu-id="c407f-386">Specificare come destinazione la combinazione per il volume del 70% nel HoloLens</span><span class="sxs-lookup"><span data-stu-id="c407f-386">Target your mix for 70% volume on the HoloLens</span></span>

<span data-ttu-id="c407f-387">Le esperienze di realtà miste consentono di osservare gli ologrammi nel mondo reale.</span><span class="sxs-lookup"><span data-stu-id="c407f-387">Mixed Reality experiences allow holograms to be seen in the real world.</span></span> <span data-ttu-id="c407f-388">Devono inoltre consentire l'ascolto di suoni reali.</span><span class="sxs-lookup"><span data-stu-id="c407f-388">They should also allow real world sounds to be heard.</span></span> <span data-ttu-id="c407f-389">Una destinazione del volume del 70% consente all'utente di sentire il mondo intorno al suono dell'esperienza.</span><span class="sxs-lookup"><span data-stu-id="c407f-389">A 70% volume target enables the user to hear the world around them along with the sound of your experience.</span></span>

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a><span data-ttu-id="c407f-390">Il volume HoloLens al 100% dovrebbe escludere i suoni esterni</span><span class="sxs-lookup"><span data-stu-id="c407f-390">HoloLens at 100% volume should drown out external sounds</span></span>

<span data-ttu-id="c407f-391">Un livello di volume pari al 100% è analogo a un'esperienza di realtà virtuale.</span><span class="sxs-lookup"><span data-stu-id="c407f-391">A volume level of 100% is akin to a Virtual Reality experience.</span></span> <span data-ttu-id="c407f-392">Visivamente, l'utente viene trasportato in un altro mondo.</span><span class="sxs-lookup"><span data-stu-id="c407f-392">Visually, the user is transported to a different world.</span></span> <span data-ttu-id="c407f-393">Lo stesso vale per il vero udibile.</span><span class="sxs-lookup"><span data-stu-id="c407f-393">The same should hold true audibly.</span></span>

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a><span data-ttu-id="c407f-394">Usare Unity AudioMixer per modificare le categorie di suoni</span><span class="sxs-lookup"><span data-stu-id="c407f-394">Use the Unity AudioMixer to adjust categories of sounds</span></span>

<span data-ttu-id="c407f-395">Quando si progetta la combinazione, è spesso utile creare categorie audio e avere la possibilità di aumentare o diminuire il volume come unità.</span><span class="sxs-lookup"><span data-stu-id="c407f-395">When designing your mix, it is often helpful to create sound categories and have the ability to increase or decrease their volume as a unit.</span></span> <span data-ttu-id="c407f-396">Questo consente di mantenere i livelli relativi di ogni suono, consentendo al tempo stesso di apportare modifiche rapide e semplici alla combinazione complessiva.</span><span class="sxs-lookup"><span data-stu-id="c407f-396">This retains the relative levels of each sound while enabling quick and easy changes to the overall mix.</span></span> <span data-ttu-id="c407f-397">Le categorie comuni includono; effetti audio, ambiente, Voice over e musica in background.</span><span class="sxs-lookup"><span data-stu-id="c407f-397">Common categories include; sound effects, ambience, voice overs and background music.</span></span>

#### <a name="mix-sounds-based-on-the-users-gaze"></a><span data-ttu-id="c407f-398">Combinare i suoni in base allo sguardo dell'utente</span><span class="sxs-lookup"><span data-stu-id="c407f-398">Mix sounds based on the user's gaze</span></span>

<span data-ttu-id="c407f-399">Spesso può essere utile modificare la combinazione di suoni nell'esperienza in base alla posizione dell'utente (o non).</span><span class="sxs-lookup"><span data-stu-id="c407f-399">It can often be useful to change the sound mix in your experience based on where a user is (or is not) looking.</span></span> <span data-ttu-id="c407f-400">Un uso comune di questa tecnica consiste nel ridurre il livello di volume per gli ologrammi esterni al frame olografico, in modo da rendere più semplice per l'utente concentrarsi sulle informazioni in primo piano.</span><span class="sxs-lookup"><span data-stu-id="c407f-400">One common use for this technique are to reduce the volume level for holograms that are outside of the Holographic Frame to make it easier for the user to focus on the information in front of them.</span></span> <span data-ttu-id="c407f-401">Un altro utilizzo consiste nell'aumentare il volume di un suono per attirare l'attenzione dell'utente su un evento importante.</span><span class="sxs-lookup"><span data-stu-id="c407f-401">Another use is to increase the volume of a sound to draw the user's attention to an important event.</span></span>

#### <a name="building-your-mix"></a><span data-ttu-id="c407f-402">Creazione della combinazione</span><span class="sxs-lookup"><span data-stu-id="c407f-402">Building your mix</span></span>

<span data-ttu-id="c407f-403">Quando si compila la combinazione, è consigliabile iniziare con l'audio in background dell'esperienza e aggiungere i livelli in base all'importanza.</span><span class="sxs-lookup"><span data-stu-id="c407f-403">When building your mix, it is recommended to start with your experience's background audio and add layers based on importance.</span></span> <span data-ttu-id="c407f-404">Spesso, il risultato è che ogni livello è più elevato rispetto a quello precedente.</span><span class="sxs-lookup"><span data-stu-id="c407f-404">Often, this results in each layer being louder than the previous.</span></span>

<span data-ttu-id="c407f-405">Immaginando la combinazione di un imbuto invertito, con i suoni meno importanti (e generalmente più tranquilli) nella parte inferiore, si consiglia di strutturare la combinazione in modo analogo al diagramma seguente.</span><span class="sxs-lookup"><span data-stu-id="c407f-405">Imagining your mix as an inverted funnel, with the least important (and generally quietest sounds) at the bottom, it is recommended to structure your mix similar to the following diagram.</span></span>

![Struttura del mix audio](images/soundlevels.png)

<span data-ttu-id="c407f-407">I Voice over sono uno scenario interessante.</span><span class="sxs-lookup"><span data-stu-id="c407f-407">Voice overs are an interesting scenario.</span></span> <span data-ttu-id="c407f-408">In base all'esperienza che si sta creando, potrebbe essere necessario disporre di un audio stereo (non localizzato) o di spatialize.</span><span class="sxs-lookup"><span data-stu-id="c407f-408">Based on the experience you are creating you may wish to have a stereo (not localized) sound or to spatialize your voice overs.</span></span> <span data-ttu-id="c407f-409">Due esperienze pubblicate da Microsoft illustrano esempi eccellenti di ogni scenario.</span><span class="sxs-lookup"><span data-stu-id="c407f-409">Two Microsoft published experiences illustrate excellent examples of each scenario.</span></span>

<span data-ttu-id="c407f-410">[HoloTour](https://www.microsoft.com/store/p/holotour/9nblggh5pj87) usa una voce stereo.</span><span class="sxs-lookup"><span data-stu-id="c407f-410">[HoloTour](https://www.microsoft.com/store/p/holotour/9nblggh5pj87) uses a stereo voice over.</span></span> <span data-ttu-id="c407f-411">Quando l'Assistente vocale descrive la posizione visualizzata, il suono è coerente e non varia in base alla posizione dell'utente.</span><span class="sxs-lookup"><span data-stu-id="c407f-411">When the narrator is describing the location being viewed, the sound is consistent and does not vary based on the user's position.</span></span> <span data-ttu-id="c407f-412">Ciò consente all'Assistente vocale di descrivere la scena senza togliere i suoni spaziali dell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="c407f-412">This enables the narrator to describe the scene without taking away from the spatialized sounds of the environment.</span></span>

<span data-ttu-id="c407f-413">I [frammenti](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) utilizzano una voce con spazialità sotto forma di detective.</span><span class="sxs-lookup"><span data-stu-id="c407f-413">[Fragments](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) utilizes a spatialized voice over in the form of a detective.</span></span> <span data-ttu-id="c407f-414">La voce del detective viene usata per aiutare a attirare l'attenzione dell'utente su un importante indizio come se fosse presente un uomo reale nella stanza.</span><span class="sxs-lookup"><span data-stu-id="c407f-414">The detective's voice is used to help bring the user's attention to an important clue as if an actual human was in the room.</span></span> <span data-ttu-id="c407f-415">Questo consente un senso ancora più approfondito dell'esperienza di risoluzione del mistero.</span><span class="sxs-lookup"><span data-stu-id="c407f-415">This enables an even greater sense of immersion into the experience of solving the mystery.</span></span>

### <a name="part-3--performance"></a><span data-ttu-id="c407f-416">Parte 3: prestazioni</span><span class="sxs-lookup"><span data-stu-id="c407f-416">Part 3 -Performance</span></span>

#### <a name="cpu-usage"></a><span data-ttu-id="c407f-417">Utilizzo CPU</span><span class="sxs-lookup"><span data-stu-id="c407f-417">CPU usage</span></span>

<span data-ttu-id="c407f-418">Quando si usa il suono spaziale, gli emettitori 10-12 utilizzeranno approssimativamente il 12% della CPU.</span><span class="sxs-lookup"><span data-stu-id="c407f-418">When using Spatial Sound, 10 - 12 emitters will consume approximately 12% of the CPU.</span></span>

#### <a name="stream-long-audio-files"></a><span data-ttu-id="c407f-419">Streaming di file audio lunghi</span><span class="sxs-lookup"><span data-stu-id="c407f-419">Stream long audio files</span></span>

<span data-ttu-id="c407f-420">I dati audio possono essere di grandi dimensioni, soprattutto a tariffe di esempio comuni (44,1 e 48 kHz).</span><span class="sxs-lookup"><span data-stu-id="c407f-420">Audio data can be large, especially at common sample rates (44.1 and 48 kHz).</span></span> <span data-ttu-id="c407f-421">Una regola generale è che i file audio più lunghi di 5-10 secondi devono essere trasmessi per ridurre l'utilizzo della memoria dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="c407f-421">A general rule is that audio files longer than 5 - 10 seconds should be streamed to reduce application memory usage.</span></span>

<span data-ttu-id="c407f-422">In Unity è possibile contrassegnare un file audio per il flusso nelle impostazioni di importazione del file.</span><span class="sxs-lookup"><span data-stu-id="c407f-422">In Unity, you can mark an audio file for streaming in the file's import settings.</span></span>

![Impostazioni di importazione audio](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a><span data-ttu-id="c407f-424">Capitolo 5-effetti speciali</span><span class="sxs-lookup"><span data-stu-id="c407f-424">Chapter 5 - Special Effects</span></span>

### <a name="objectives"></a><span data-ttu-id="c407f-425">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="c407f-425">Objectives</span></span>

* <span data-ttu-id="c407f-426">Aggiungere Depth a "Magic Windows".</span><span class="sxs-lookup"><span data-stu-id="c407f-426">Add depth to "Magic Windows".</span></span>
* <span data-ttu-id="c407f-427">Porta l'utente nel mondo virtuale.</span><span class="sxs-lookup"><span data-stu-id="c407f-427">Bring the user into the virtual world.</span></span>

### <a name="magic-windows"></a><span data-ttu-id="c407f-428">Finestre magiche</span><span class="sxs-lookup"><span data-stu-id="c407f-428">Magic Windows</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="c407f-429">Concetti chiave</span><span class="sxs-lookup"><span data-stu-id="c407f-429">Key Concepts</span></span>

* <span data-ttu-id="c407f-430">La creazione di visualizzazioni in un ambiente nascosto è visivamente accattivante.</span><span class="sxs-lookup"><span data-stu-id="c407f-430">Creating views into a hidden world, is visually compelling.</span></span>
* <span data-ttu-id="c407f-431">Migliora il realismo aggiungendo effetti audio quando un ologramma o l'utente è vicino al mondo nascosto.</span><span class="sxs-lookup"><span data-stu-id="c407f-431">Enhance realism by adding audio effects when a hologram or the user is near the hidden world.</span></span>

#### <a name="instructions"></a><span data-ttu-id="c407f-432">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="c407f-432">Instructions</span></span>

* <span data-ttu-id="c407f-433">Nel pannello **gerarchia** espandere **ologrammcollection** e selezionare **Sottomondo**.</span><span class="sxs-lookup"><span data-stu-id="c407f-433">In the **Hierarchy** panel, expand **HologramCollection** and select **Underworld**.</span></span>
* <span data-ttu-id="c407f-434">Espandere **Underworld** e selezionare **VoiceSource**.</span><span class="sxs-lookup"><span data-stu-id="c407f-434">Expand **Underworld** and select **VoiceSource**.</span></span>
* <span data-ttu-id="c407f-435">Nel pannello di **controllo** fare clic su **Aggiungi componente** e aggiungere **effetto voce utente**.</span><span class="sxs-lookup"><span data-stu-id="c407f-435">In the **Inspector** panel, click **Add Component** and add **User Voice Effect**.</span></span>

<span data-ttu-id="c407f-436">Verrà aggiunto un componente **audiosource** a **VoiceSource**.</span><span class="sxs-lookup"><span data-stu-id="c407f-436">An **AudioSource** component will be added to **VoiceSource**.</span></span>

* <span data-ttu-id="c407f-437">In **audiosource**impostare **output** su **UserVoice (mixer)** .</span><span class="sxs-lookup"><span data-stu-id="c407f-437">In **AudioSource**, set **Output** to **UserVoice (Mixer)**.</span></span>
* <span data-ttu-id="c407f-438">Selezionare la casella di controllo **Spatialize** .</span><span class="sxs-lookup"><span data-stu-id="c407f-438">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="c407f-439">Trascinare il dispositivo di scorrimento di **Blend spaziale** fino a **3D**oppure immettere **1** nella casella di modifica.</span><span class="sxs-lookup"><span data-stu-id="c407f-439">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>
* <span data-ttu-id="c407f-440">Espandere **impostazioni audio 3D**.</span><span class="sxs-lookup"><span data-stu-id="c407f-440">Expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="c407f-441">Impostare il **livello di Doppler** su **0**.</span><span class="sxs-lookup"><span data-stu-id="c407f-441">Set **Doppler Level** to **0**.</span></span>
* <span data-ttu-id="c407f-442">In **effetto voce utente**impostare **oggetto padre** sul **Sottomondo** dalla scena.</span><span class="sxs-lookup"><span data-stu-id="c407f-442">In **User Voice Effect**, set **Parent Object** to the **Underworld** from the scene.</span></span>
* <span data-ttu-id="c407f-443">Impostare **distanza massima** su **1**.</span><span class="sxs-lookup"><span data-stu-id="c407f-443">Set **Max Distance** to **1**.</span></span>

<span data-ttu-id="c407f-444">L'impostazione della **distanza massima** indica all' **utente** il modo in cui la chiusura dell'utente deve essere l'oggetto padre prima che l'effetto venga attivato.</span><span class="sxs-lookup"><span data-stu-id="c407f-444">Setting **Max Distance** tells **User Voice Effect** how close the user must be to the parent object before the effect is enabled.</span></span>

* <span data-ttu-id="c407f-445">In **effetto voce utente**espandere **parametri Chorus**.</span><span class="sxs-lookup"><span data-stu-id="c407f-445">In **User Voice Effect**, expand **Chorus Parameters**.</span></span>
* <span data-ttu-id="c407f-446">Impostare **Depth** su **0,1**.</span><span class="sxs-lookup"><span data-stu-id="c407f-446">Set **Depth** to **0.1**.</span></span>
* <span data-ttu-id="c407f-447">Impostare **toccare 1 volume**, **toccare 2 volume** e **toccare 3 volume** su **0,8**.</span><span class="sxs-lookup"><span data-stu-id="c407f-447">Set **Tap 1 Volume**, **Tap 2 Volume** and **Tap 3 Volume** to **0.8**.</span></span>
* <span data-ttu-id="c407f-448">Impostare **volume audio originale** su **0,5**.</span><span class="sxs-lookup"><span data-stu-id="c407f-448">Set **Original Sound Volume** to **0.5**.</span></span>

<span data-ttu-id="c407f-449">Le impostazioni precedenti configurano i parametri del **AudioChorusFilter** Unity usato per aggiungere ricchezza alla voce dell'utente.</span><span class="sxs-lookup"><span data-stu-id="c407f-449">The previous settings configure the parameters of the Unity **AudioChorusFilter** used to add richness to the user's voice.</span></span>

* <span data-ttu-id="c407f-450">In **effetto voce utente**espandere **parametri Echo**.</span><span class="sxs-lookup"><span data-stu-id="c407f-450">In **User Voice Effect**, expand **Echo Parameters**.</span></span>
* <span data-ttu-id="c407f-451">Imposta **ritardo** su **300**</span><span class="sxs-lookup"><span data-stu-id="c407f-451">Set **Delay** to **300**</span></span>
* <span data-ttu-id="c407f-452">Imposta il **rapporto di decadimento** su **0,2**.</span><span class="sxs-lookup"><span data-stu-id="c407f-452">Set **Decay Ratio** to **0.2**.</span></span>
* <span data-ttu-id="c407f-453">Impostare **volume audio originale** su **0**.</span><span class="sxs-lookup"><span data-stu-id="c407f-453">Set **Original Sound Volume** to **0**.</span></span>

<span data-ttu-id="c407f-454">Le impostazioni precedenti configurano i parametri del **AudioEchoFilter** Unity usato per fare in modo che la voce dell'utente sia Echo.</span><span class="sxs-lookup"><span data-stu-id="c407f-454">The previous settings configure the parameters of the Unity **AudioEchoFilter** used to cause the user's voice to echo.</span></span>

<span data-ttu-id="c407f-455">Lo script dell'effetto vocale utente è responsabile di:</span><span class="sxs-lookup"><span data-stu-id="c407f-455">The User Voice Effect script is responsible for:</span></span>

* <span data-ttu-id="c407f-456">Misurazione della distanza tra l'utente e la **GameObject** a cui è associato lo script.</span><span class="sxs-lookup"><span data-stu-id="c407f-456">Measuring the distance between the user and the **GameObject** to which the script is attached.</span></span>
* <span data-ttu-id="c407f-457">Determinare se l'utente si trova o meno a **GameObject**.</span><span class="sxs-lookup"><span data-stu-id="c407f-457">Determining whether or not the user is facing the **GameObject**.</span></span>

<span data-ttu-id="c407f-458">È necessario che l'utente si trovi a fronte del GameObject, indipendentemente dalla distanza, per abilitare l'effetto.</span><span class="sxs-lookup"><span data-stu-id="c407f-458">The user must be facing the GameObject, regardless of distance, for the effect to be enabled.</span></span>

* <span data-ttu-id="c407f-459">Applicazione e configurazione di un **AudioChorusFilter** e di un **AudioEchoFilter** in **audiosource**.</span><span class="sxs-lookup"><span data-stu-id="c407f-459">Applying and configuring an **AudioChorusFilter** and an **AudioEchoFilter** to the **AudioSource**.</span></span>
* <span data-ttu-id="c407f-460">Disabilitare l'effetto disabilitando i filtri.</span><span class="sxs-lookup"><span data-stu-id="c407f-460">Disabling the effect by disabling the filters.</span></span>

<span data-ttu-id="c407f-461">L'effetto voce utente usa il componente MIC Stream Selector, da [MixedRealityToolkit per Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), per selezionare il flusso di voce di qualità elevata e instradarlo nel sistema audio di Unity.</span><span class="sxs-lookup"><span data-stu-id="c407f-461">User Voice Effect uses the Mic Stream Selector component, from the [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), to select the high quality voice stream and route it into Unity's audio system.</span></span>

* <span data-ttu-id="c407f-462">Nel pannello **gerarchia** selezionare **Managers**.</span><span class="sxs-lookup"><span data-stu-id="c407f-462">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="c407f-463">Nel pannello **Inspector** espandere gestore di **input vocale**.</span><span class="sxs-lookup"><span data-stu-id="c407f-463">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="c407f-464">In **gestore di input vocale**espandere **Mostra Sottomondo**.</span><span class="sxs-lookup"><span data-stu-id="c407f-464">In **Speech Input Handler**, expand **Show Underworld**.</span></span>
* <span data-ttu-id="c407f-465">Modificare **Nessuna funzione** in **UnderworldBase. OnEnable**.</span><span class="sxs-lookup"><span data-stu-id="c407f-465">Change **No Function** to **UnderworldBase.OnEnable**.</span></span>

![Parola chiave: Show Underworld](images/showunderworld.png)

* <span data-ttu-id="c407f-467">Espandi **Nascondi Sottomondo**.</span><span class="sxs-lookup"><span data-stu-id="c407f-467">Expand **Hide Underworld**.</span></span>
* <span data-ttu-id="c407f-468">Modificare **Nessuna funzione** in **UnderworldBase. ondisable**.</span><span class="sxs-lookup"><span data-stu-id="c407f-468">Change **No Function** to **UnderworldBase.OnDisable**.</span></span>

![Parola chiave: Hide Underworld](images/hideunderworld.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="c407f-470">Compilazione e distribuzione</span><span class="sxs-lookup"><span data-stu-id="c407f-470">Build and Deploy</span></span>

* <span data-ttu-id="c407f-471">Come in precedenza, compilare il progetto in Unity e distribuirlo in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c407f-471">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="c407f-472">Dopo la distribuzione dell'applicazione:</span><span class="sxs-lookup"><span data-stu-id="c407f-472">After the application is deployed:</span></span>

* <span data-ttu-id="c407f-473">Far fronte a una superficie (Wall, Floor, Table) e pronunciare *"Show Underworld"* .</span><span class="sxs-lookup"><span data-stu-id="c407f-473">Face a surface (wall, floor, table) and say *"Show Underworld"*.</span></span>

<span data-ttu-id="c407f-474">Il Sottomondo verrà visualizzato e tutti gli altri ologrammi verranno nascosti.</span><span class="sxs-lookup"><span data-stu-id="c407f-474">The underworld will be shown and all other holograms will be hidden.</span></span> <span data-ttu-id="c407f-475">Se il Sottomondo non viene visualizzato, assicurarsi di essere connessi a una superficie reale.</span><span class="sxs-lookup"><span data-stu-id="c407f-475">If you do not see the underworld, ensure that you are facing a real-world surface.</span></span>

* <span data-ttu-id="c407f-476">Approccio entro 1 metro dell'ologramma del Sottomondo e iniziare a comunicare.</span><span class="sxs-lookup"><span data-stu-id="c407f-476">Approach within 1 meter of the underworld hologram and start talking.</span></span>

<span data-ttu-id="c407f-477">Sono ora applicati effetti audio alla voce.</span><span class="sxs-lookup"><span data-stu-id="c407f-477">There are now audio effects applied to your voice!</span></span>

* <span data-ttu-id="c407f-478">Allontanarsi dal Sottomondo e notare il modo in cui l'effetto non viene più applicato.</span><span class="sxs-lookup"><span data-stu-id="c407f-478">Turn away from the underworld and notice how the effect is no longer applied.</span></span>
* <span data-ttu-id="c407f-479">Pronunciare *"Hide Underworld"* per nascondere il Sottomondo.</span><span class="sxs-lookup"><span data-stu-id="c407f-479">Say *"Hide Underworld"* to hide the underworld.</span></span>

<span data-ttu-id="c407f-480">Il Sottomondo verrà nascosto e verranno nuovamente visualizzati gli ologrammi nascosti in precedenza.</span><span class="sxs-lookup"><span data-stu-id="c407f-480">The underworld will be hidden and the previously hidden holograms will reappear.</span></span>

## <a name="the-end"></a><span data-ttu-id="c407f-481">La fine</span><span class="sxs-lookup"><span data-stu-id="c407f-481">The End</span></span>

<span data-ttu-id="c407f-482">Complimenti.</span><span class="sxs-lookup"><span data-stu-id="c407f-482">Congratulations!</span></span> <span data-ttu-id="c407f-483">A questo punto è stato completato il comportamento di **spatial 220: Spatial**.</span><span class="sxs-lookup"><span data-stu-id="c407f-483">You have now completed **MR Spatial 220: Spatial sound**.</span></span>

<span data-ttu-id="c407f-484">Ascolta il mondo e fai vivere le tue esperienze con i suoni.</span><span class="sxs-lookup"><span data-stu-id="c407f-484">Listen to the world and bring your experiences to life with sound!</span></span>

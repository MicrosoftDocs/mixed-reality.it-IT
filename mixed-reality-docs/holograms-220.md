---
title: MR Spatial 220-audio spaziale
description: Seguire questa procedura dettagliata di codifica usando Unity, Visual Studio e HoloLens per informazioni dettagliate sui concetti relativi ai suoni spaziali.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academy, esercitazione, spazio audio
ms.openlocfilehash: 50d17fe8c9a6e3f18b1309a59c9c41af982a7505
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63526959"
---
>[!NOTE]
><span data-ttu-id="1a9f4-104">Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="1a9f4-105">Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="1a9f4-106">Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="1a9f4-107">Verranno mantenuti per continuare a usare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="1a9f4-108">In futuro sarà disponibile una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="1a9f4-109">Questo avviso verrà aggiornato con un collegamento a queste esercitazioni quando vengono pubblicate.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-spatial-220-spatial-sound"></a><span data-ttu-id="1a9f4-110">MR Spatial 220: Audio spaziale</span><span class="sxs-lookup"><span data-stu-id="1a9f4-110">MR Spatial 220: Spatial sound</span></span>

<span data-ttu-id="1a9f4-111">Il [suono spaziale](spatial-sound.md) respira la vita negli ologrammi e offre loro la presenza nel nostro mondo.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-111">[Spatial sound](spatial-sound.md) breathes life into holograms and gives them presence in our world.</span></span> <span data-ttu-id="1a9f4-112">Gli ologrammi sono costituiti da luci e suoni e, se si perde la visione degli ologrammi, il suono spaziale può aiutarti a trovarli.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-112">Holograms are composed of both light and sound, and if you happen to lose sight of your holograms, spatial sound can help you find them.</span></span> <span data-ttu-id="1a9f4-113">Il suono spaziale non è analogo a quello tipico che è possibile sentire sulla radio, è un suono posizionato nello spazio 3D.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-113">Spatial sound is not like the typical sound that you would hear on the radio, it is sound that is positioned in 3D space.</span></span> <span data-ttu-id="1a9f4-114">Con il suono spaziale è possibile far sembrare gli ologrammi come se fossero dietro di te, accanto a te o persino in testa!</span><span class="sxs-lookup"><span data-stu-id="1a9f4-114">With spatial sound, you can make holograms sound like they're behind you, next to you, or even on your head!</span></span> <span data-ttu-id="1a9f4-115">In questo corso verrà:</span><span class="sxs-lookup"><span data-stu-id="1a9f4-115">In this course, you will:</span></span>

* <span data-ttu-id="1a9f4-116">Configurare l'ambiente di sviluppo per l'utilizzo di audio spaziale Microsoft.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-116">Configure your development environment to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="1a9f4-117">Usare il suono spaziale per migliorare le interazioni.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-117">Use Spatial Sound to enhance interactions.</span></span>
* <span data-ttu-id="1a9f4-118">Utilizzare il suono spaziale insieme al mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-118">Use Spatial Sound in conjunction with Spatial Mapping.</span></span>
* <span data-ttu-id="1a9f4-119">Comprendere le procedure consigliate per la progettazione e la combinazione di suoni.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-119">Understand sound design and mixing best practices.</span></span>
* <span data-ttu-id="1a9f4-120">Usare il suono per migliorare gli effetti speciali e coinvolgere l'utente nel mondo della realtà mista.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-120">Use sound to enhance special effects and bring the user into the Mixed Reality world.</span></span>

## <a name="device-support"></a><span data-ttu-id="1a9f4-121">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="1a9f4-121">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="1a9f4-122">Corso</span><span class="sxs-lookup"><span data-stu-id="1a9f4-122">Course</span></span></th><th style="width:150px"> <span data-ttu-id="1a9f4-123"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="1a9f4-123"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="1a9f4-124"><a href="immersive-headset-hardware-details.md">Visori VR immersive</a></span><span class="sxs-lookup"><span data-stu-id="1a9f4-124"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="1a9f4-125">MR Spatial 220: Audio spaziale</span><span class="sxs-lookup"><span data-stu-id="1a9f4-125">MR Spatial 220: Spatial sound</span></span></td><td style="text-align: center;"> <span data-ttu-id="1a9f4-126">✔️</span><span class="sxs-lookup"><span data-stu-id="1a9f4-126">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="1a9f4-127">✔️</span><span class="sxs-lookup"><span data-stu-id="1a9f4-127">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="1a9f4-128">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="1a9f4-128">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="1a9f4-129">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="1a9f4-129">Prerequisites</span></span>

* <span data-ttu-id="1a9f4-130">Un PC Windows 10 configurato con gli [strumenti corretti installati](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="1a9f4-130">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="1a9f4-131">Alcune funzionalità C# di programmazione di base.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-131">Some basic C# programming ability.</span></span>
* <span data-ttu-id="1a9f4-132">Sono state completate le nozioni di [base 101](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="1a9f4-132">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="1a9f4-133">Un dispositivo HoloLens [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="1a9f4-133">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="1a9f4-134">File di progetto</span><span class="sxs-lookup"><span data-stu-id="1a9f4-134">Project files</span></span>

* <span data-ttu-id="1a9f4-135">Scaricare i [file](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) richiesti dal progetto.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-135">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) required by the project.</span></span><span data-ttu-id="1a9f4-136"> Richiede Unity 2017,2 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-136"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="1a9f4-137">Se è ancora necessario il supporto per Unity 5,6, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip).</span><span class="sxs-lookup"><span data-stu-id="1a9f4-137">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip).</span></span> <span data-ttu-id="1a9f4-138">Questa versione potrebbe non essere più aggiornata.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-138">This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="1a9f4-139">Se è ancora necessario il supporto per Unity 5,5, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip).</span><span class="sxs-lookup"><span data-stu-id="1a9f4-139">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip).</span></span><span data-ttu-id="1a9f4-140"> Questa versione potrebbe non essere più aggiornata.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-140"> This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="1a9f4-141">Se è ancora necessario il supporto per Unity 5,4, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip).</span><span class="sxs-lookup"><span data-stu-id="1a9f4-141">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip).</span></span><span data-ttu-id="1a9f4-142"> Questa versione potrebbe non essere più aggiornata.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-142"> This release may no longer be up-to-date.</span></span>
* <span data-ttu-id="1a9f4-143">Annullare l'archiviazione dei file sul desktop o in un'altra posizione facile da raggiungere.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-143">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="1a9f4-144">Se si vuole esaminare il codice sorgente prima del download, è [disponibile in GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).</span><span class="sxs-lookup"><span data-stu-id="1a9f4-144">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="1a9f4-145">Errori e note</span><span class="sxs-lookup"><span data-stu-id="1a9f4-145">Errata and Notes</span></span>

* <span data-ttu-id="1a9f4-146">"Enable Just My Code" deve essere disabilitato (deselezionato) in Visual Studio in strumenti-Opzioni >-> debug per raggiungere i punti di interruzione nel codice.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-146">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="1a9f4-147">Capitolo 1-installazione di Unity</span><span class="sxs-lookup"><span data-stu-id="1a9f4-147">Chapter 1 - Unity Setup</span></span>

### <a name="objectives"></a><span data-ttu-id="1a9f4-148">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="1a9f4-148">Objectives</span></span>

* <span data-ttu-id="1a9f4-149">Modificare la configurazione audio di Unity per l'uso del suono Microsoft Spatial.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-149">Change Unity's sound configuration to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="1a9f4-150">Aggiungere un suono 3D a un oggetto in Unity.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-150">Add 3D sound to an object in Unity.</span></span>

### <a name="instructions"></a><span data-ttu-id="1a9f4-151">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="1a9f4-151">Instructions</span></span>

* <span data-ttu-id="1a9f4-152">Avvia Unity.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-152">Start Unity.</span></span>
* <span data-ttu-id="1a9f4-153">Selezionare **Apri**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-153">Select **Open**.</span></span>
* <span data-ttu-id="1a9f4-154">Passare al desktop e trovare la cartella precedentemente non archiviata.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-154">Navigate to your Desktop and find the folder you previously un-archived.</span></span>
* <span data-ttu-id="1a9f4-155">Fare clic sulla cartella **Starting\Decibel** , quindi premere il pulsante **Seleziona cartella** .</span><span class="sxs-lookup"><span data-stu-id="1a9f4-155">Click on the **Starting\Decibel** folder and then press the **Select Folder** button.</span></span>
* <span data-ttu-id="1a9f4-156">Attendere che il progetto venga caricato in Unity.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-156">Wait for the project to load in Unity.</span></span>
* <span data-ttu-id="1a9f4-157">Nel pannello del **progetto** aprire **Scenes\Decibel.Unity**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-157">In the **Project** panel, open **Scenes\Decibel.unity**.</span></span>
* <span data-ttu-id="1a9f4-158">Nel pannello **gerarchia** espandere ologrammcollection  e selezionare **P0LY**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-158">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="1a9f4-159">Nel controllo espandere **audiosource** e notare che non è presente alcuna casella di controllo **Spatialize** .</span><span class="sxs-lookup"><span data-stu-id="1a9f4-159">In the Inspector, expand **AudioSource** and notice that there is no **Spatialize** check box.</span></span>

<span data-ttu-id="1a9f4-160">Per impostazione predefinita, Unity non carica un plug-in Spatializer.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-160">By default, Unity does not load a spatializer plugin.</span></span> <span data-ttu-id="1a9f4-161">Nei passaggi seguenti viene abilitato il suono spaziale nel progetto.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-161">The following steps will enable Spatial Sound in the project.</span></span>

* <span data-ttu-id="1a9f4-162">Nel menu principale di Unity scegliere **modifica > impostazioni progetto > audio**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-162">In Unity's top menu, go to **Edit > Project Settings > Audio**.</span></span>
* <span data-ttu-id="1a9f4-163">Individuare l'elenco a discesa plug-in **Spatializer** e selezionare **MS HRTF Spatializer**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-163">Find the **Spatializer Plugin** dropdown, and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="1a9f4-164">Nel pannello **gerarchia** selezionare ologrammcollection **> P0LY**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-164">In the **Hierarchy** panel, select **HologramCollection > P0LY**.</span></span>
* <span data-ttu-id="1a9f4-165">Nel pannello **Inspector** trovare il componente di **origine audio** .</span><span class="sxs-lookup"><span data-stu-id="1a9f4-165">In the **Inspector** panel, find the **Audio Source** component.</span></span>
* <span data-ttu-id="1a9f4-166">Selezionare la casella di controllo **Spatialize** .</span><span class="sxs-lookup"><span data-stu-id="1a9f4-166">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="1a9f4-167">Trascinare il dispositivo di scorrimento di **Blend spaziale** fino a **3D**oppure immettere **1** nella casella di modifica.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-167">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>

<span data-ttu-id="1a9f4-168">Il progetto verrà ora compilato in Unity e la soluzione verrà configurata in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-168">We will now build the project in Unity and configure the solution in Visual Studio.</span></span>

1. <span data-ttu-id="1a9f4-169">In Unity selezionare **File > impostazioni di compilazione**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-169">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="1a9f4-170">Fare clic su **Aggiungi scene aperte** per aggiungere la scena.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-170">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="1a9f4-171">Selezionare **piattaforma UWP (Universal Windows Platform)** nell'elenco **piattaforma** e fare clic su **Cambia piattaforma**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-171">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="1a9f4-172">Se si sta sviluppando in modo specifico per HoloLens, impostare **dispositivo di destinazione** su **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-172">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="1a9f4-173">In caso contrario, lasciarlo in **qualsiasi dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-173">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="1a9f4-174">Verificare che **tipo di compilazione** sia impostato su **D3D** e che l' **SDK** sia impostato su **installato più recente** (che deve essere SDK 16299 o versione successiva).</span><span class="sxs-lookup"><span data-stu-id="1a9f4-174">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="1a9f4-175">Fai clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-175">Click **Build**.</span></span>
7. <span data-ttu-id="1a9f4-176">Creare una **nuova cartella** denominata "app".</span><span class="sxs-lookup"><span data-stu-id="1a9f4-176">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="1a9f4-177">Fare clic sulla cartella dell' **app** .</span><span class="sxs-lookup"><span data-stu-id="1a9f4-177">Single click the **App** folder.</span></span>
9. <span data-ttu-id="1a9f4-178">Premere **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-178">Press **Select Folder**.</span></span>

<span data-ttu-id="1a9f4-179">Quando si esegue Unity, viene visualizzata una finestra Esplora file.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-179">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="1a9f4-180">Aprire la cartella dell' **app** .</span><span class="sxs-lookup"><span data-stu-id="1a9f4-180">Open the **App** folder.</span></span>
2. <span data-ttu-id="1a9f4-181">Aprire la **soluzione decibel di Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-181">Open the **Decibel Visual Studio Solution**.</span></span>

<span data-ttu-id="1a9f4-182">Se si esegue la distribuzione in HoloLens:</span><span class="sxs-lookup"><span data-stu-id="1a9f4-182">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="1a9f4-183">Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione da debug a **Release** e da ARM a **x86**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-183">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="1a9f4-184">Fare clic sulla freccia a discesa accanto al pulsante computer locale e selezionare **computer remoto**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-184">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="1a9f4-185">Immettere **l'indirizzo IP del dispositivo HoloLens** e impostare la modalità di autenticazione su **universale (protocollo non crittografato)** .</span><span class="sxs-lookup"><span data-stu-id="1a9f4-185">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="1a9f4-186">Fare clic su **Seleziona**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-186">Click **Select**.</span></span> <span data-ttu-id="1a9f4-187">Se non si conosce l'indirizzo IP del dispositivo, vedere **impostazioni > rete & Internet > opzioni avanzate**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-187">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="1a9f4-188">Nella barra dei menu superiore fare clic su **debug-> avvia senza eseguire debug** o premere **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-188">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="1a9f4-189">Se questa è la prima volta che si esegue la distribuzione nel dispositivo, sarà necessario associarla a [Visual Studio](using-visual-studio.md#pairing-your-device---hololens-1st-gen).</span><span class="sxs-lookup"><span data-stu-id="1a9f4-189">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device---hololens-1st-gen).</span></span>

<span data-ttu-id="1a9f4-190">Se si esegue la distribuzione in un auricolare immersivo:</span><span class="sxs-lookup"><span data-stu-id="1a9f4-190">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="1a9f4-191">Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione da debug a **Release** e da ARM a **x64**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-191">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="1a9f4-192">Verificare che la destinazione di distribuzione sia impostata su **computer locale**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-192">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="1a9f4-193">Nella barra dei menu superiore fare clic su **debug-> avvia senza eseguire debug** o premere **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-193">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>

## <a name="chapter-2---spatial-sound-and-interaction"></a><span data-ttu-id="1a9f4-194">Capitolo 2-audio e interazione spaziali</span><span class="sxs-lookup"><span data-stu-id="1a9f4-194">Chapter 2 - Spatial Sound and Interaction</span></span>

### <a name="objectives"></a><span data-ttu-id="1a9f4-195">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="1a9f4-195">Objectives</span></span>

* <span data-ttu-id="1a9f4-196">Migliorare il Real ologramma usando il suono.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-196">Enhance hologram realism using sound.</span></span>
* <span data-ttu-id="1a9f4-197">Indirizzare lo sguardo dell'utente usando un suono.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-197">Direct the user's gaze using sound.</span></span>
* <span data-ttu-id="1a9f4-198">Fornire commenti e suggerimenti sui movimenti usando un suono.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-198">Provide gesture feedback using sound.</span></span>

### <a name="part-1---enhancing-realism"></a><span data-ttu-id="1a9f4-199">Parte 1-miglioramento del realismo</span><span class="sxs-lookup"><span data-stu-id="1a9f4-199">Part 1 - Enhancing Realism</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="1a9f4-200">Concetti chiave</span><span class="sxs-lookup"><span data-stu-id="1a9f4-200">Key Concepts</span></span>

* <span data-ttu-id="1a9f4-201">Spatialize ologrammi.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-201">Spatialize hologram sounds.</span></span>
* <span data-ttu-id="1a9f4-202">Le origini audio devono essere posizionate in una posizione appropriata nell'ologramma.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-202">Sound sources should be placed at an appropriate location on the hologram.</span></span>

<span data-ttu-id="1a9f4-203">Il percorso appropriato per il suono dipende dall'ologramma.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-203">The appropriate location for the sound is going to depend on the hologram.</span></span> <span data-ttu-id="1a9f4-204">Se, ad esempio, l'ologramma è umano, l'origine del suono dovrebbe trovarsi vicino alla bocca e non ai piedi.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-204">For example, if the hologram is of a human, the sound source should be located near the mouth and not the feet.</span></span>

#### <a name="instructions"></a><span data-ttu-id="1a9f4-205">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="1a9f4-205">Instructions</span></span>

<span data-ttu-id="1a9f4-206">Le istruzioni seguenti allegheranno un suono spaziali a un ologramma.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-206">The following instructions will attach a spatialized sound to a hologram.</span></span>

* <span data-ttu-id="1a9f4-207">Nel pannello **gerarchia** espandere ologrammcollection  e selezionare **P0LY**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-207">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="1a9f4-208">Nel pannello di **controllo** , in **audiosource**, fare clic sul cerchio accanto a **AudioClip** e selezionare **polihover** dal menu a comparsa.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-208">In the **Inspector** panel, in the **AudioSource**, click the circle next to **AudioClip** and select **PolyHover** from the pop-up.</span></span>
* <span data-ttu-id="1a9f4-209">Fare clic sul cerchio accanto a **output** e selezionare **SoundEffects** dal menu a comparsa.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-209">Click the circle next to **Output** and select **SoundEffects** from the pop-up.</span></span>

<span data-ttu-id="1a9f4-210">Il progetto decibel usa un componente **audiomixer** Unity per abilitare la regolazione dei livelli audio per gruppi di suoni.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-210">Project Decibel uses a Unity **AudioMixer** component to enable adjusting sound levels for groups of sounds.</span></span> <span data-ttu-id="1a9f4-211">Raggruppando i suoni in questo modo, è possibile modificare il volume complessivo mantenendo il volume relativo di ogni suono.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-211">By grouping sounds this way, the overall volume can be adjusted while maintaining the relative volume of each sound.</span></span>

* <span data-ttu-id="1a9f4-212">In **audiosource**espandere **impostazioni audio 3D**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-212">In the **AudioSource**, expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="1a9f4-213">Impostare il **livello di Doppler** su **0**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-213">Set **Doppler Level** to **0**.</span></span>

<span data-ttu-id="1a9f4-214">L'impostazione del livello di Doppler su zero disabilita le modifiche apportate a un pitch causato da un movimento, ovvero l'ologramma o l'utente.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-214">Setting Doppler level to zero disables changes in pitch caused by motion (either of the hologram or the user).</span></span> <span data-ttu-id="1a9f4-215">Un esempio classico di Doppler è un'auto in rapida evoluzione.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-215">A classic example of Doppler is a fast-moving car.</span></span> <span data-ttu-id="1a9f4-216">Quando l'auto si avvicina a un listener fisso, il pitch del motore aumenta.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-216">As the car approaches a stationary listener, the pitch of the engine rises.</span></span> <span data-ttu-id="1a9f4-217">Quando passa il listener, il passo viene ridotto a distanza.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-217">When it passes the listener, the pitch lowers with distance.</span></span>

### <a name="part-2---directing-the-users-gaze"></a><span data-ttu-id="1a9f4-218">Parte 2-indirizzare lo sguardo dell'utente</span><span class="sxs-lookup"><span data-stu-id="1a9f4-218">Part 2 - Directing the User's Gaze</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="1a9f4-219">Concetti chiave</span><span class="sxs-lookup"><span data-stu-id="1a9f4-219">Key Concepts</span></span>

* <span data-ttu-id="1a9f4-220">Usare il suono per richiamare l'attenzione sugli ologrammi importanti.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-220">Use sound to call attention to important holograms.</span></span>
* <span data-ttu-id="1a9f4-221">Gli orecchi consentono di indirizzare il punto di vista.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-221">The ears help direct where the eyes should look.</span></span>
* <span data-ttu-id="1a9f4-222">Il cervello ha alcune aspettative acquisite.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-222">The brain has some learned expectations.</span></span>

<span data-ttu-id="1a9f4-223">Un esempio di aspettative apprese è che gli uccelli si trovano in genere sopra i capi degli uomini.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-223">One example of learned expectations is that birds are generally above the heads of humans.</span></span> <span data-ttu-id="1a9f4-224">Se un utente riceve un segnale acustico, la relativa reazione iniziale è la ricerca.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-224">If a user hears a bird sound, their initial reaction is to look up.</span></span> <span data-ttu-id="1a9f4-225">L'inserimento di un uccello sotto l'utente può comportare la direzione corretta del suono, ma non è in grado di trovare l'ologramma in base alla necessità di cercare.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-225">Placing a bird below the user can lead to them facing the correct direction of the sound, but being unable to find the hologram based on the expectation of needing to look up.</span></span>

#### <a name="instructions"></a><span data-ttu-id="1a9f4-226">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="1a9f4-226">Instructions</span></span>

<span data-ttu-id="1a9f4-227">Le istruzioni seguenti consentono a P0LY di nascondersi dietro l'utente, in modo da poter usare il suono per individuare l'ologramma.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-227">The following instructions enable P0LY to hide behind you, so that you can use sound to locate the hologram.</span></span>

* <span data-ttu-id="1a9f4-228">Nel pannello **gerarchia** selezionare managers .</span><span class="sxs-lookup"><span data-stu-id="1a9f4-228">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="1a9f4-229">Nel pannello **Inspector** trovare gestore di **input vocale**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-229">In the **Inspector** panel, find **Speech Input Handler**.</span></span>
* <span data-ttu-id="1a9f4-230">In **gestore di input vocale**espandere **Vai a Nascondi**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-230">In **Speech Input Handler**, expand **Go Hide**.</span></span>
* <span data-ttu-id="1a9f4-231">Modificare **Nessuna funzione** in **poliactions. GoHide**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-231">Change **No Function** to **PolyActions.GoHide**.</span></span>

![Parola chiave Nascondi](images/gohide.png)

### <a name="part-3---gesture-feedback"></a><span data-ttu-id="1a9f4-233">Parte 3: commenti e suggerimenti sui movimenti</span><span class="sxs-lookup"><span data-stu-id="1a9f4-233">Part 3 - Gesture Feedback</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="1a9f4-234">Concetti chiave</span><span class="sxs-lookup"><span data-stu-id="1a9f4-234">Key Concepts</span></span>

* <span data-ttu-id="1a9f4-235">Fornire all'utente una conferma positiva del movimento usando un suono</span><span class="sxs-lookup"><span data-stu-id="1a9f4-235">Provide the user with positive gesture confirmation using sound</span></span>
* <span data-ttu-id="1a9f4-236">Non sovraccaricare i suoni eccessivamente rumorosi dell'utente</span><span class="sxs-lookup"><span data-stu-id="1a9f4-236">Do not overwhelm the user - overly loud sounds get in the way</span></span>
* <span data-ttu-id="1a9f4-237">I rumori sottili funzionano meglio: non offuscare l'esperienza</span><span class="sxs-lookup"><span data-stu-id="1a9f4-237">Subtle sounds work best - do not overshadow the experience</span></span>

#### <a name="instructions"></a><span data-ttu-id="1a9f4-238">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="1a9f4-238">Instructions</span></span>

* <span data-ttu-id="1a9f4-239">Nel pannello **gerarchia** espandere ologrammcollection .</span><span class="sxs-lookup"><span data-stu-id="1a9f4-239">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="1a9f4-240">Espandere **EnergyHub** e selezionare **base**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-240">Expand **EnergyHub** and select **Base**.</span></span>
* <span data-ttu-id="1a9f4-241">Nel pannello di **controllo** fare clic su **Aggiungi componente** e aggiungere il **gestore audio del movimento**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-241">In the **Inspector** panel, click **Add Component** and add **Gesture Sound Handler**.</span></span>
* <span data-ttu-id="1a9f4-242">Nel **gestore del suono del movimento**fare clic sul cerchio accanto al clip avviato per la **navigazione** e selezionare il clip **aggiornato** e selezionare **RotateClick** dal menu a comparsa per entrambe.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-242">In **Gesture Sound Handler**, click the circle next to **Navigation Started Clip** and **Navigation Updated Clip** and select **RotateClick** from the pop-up for both.</span></span>
* <span data-ttu-id="1a9f4-243">Fare doppio clic su "GestureSoundHandler" per caricare in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-243">Double click on "GestureSoundHandler" to load in Visual Studio.</span></span>

<span data-ttu-id="1a9f4-244">Il gestore del suono del movimento esegue le attività seguenti:</span><span class="sxs-lookup"><span data-stu-id="1a9f4-244">Gesture Sound Handler performs the following tasks:</span></span>

* <span data-ttu-id="1a9f4-245">Creare e configurare un **audiosource**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-245">Create and configure an **AudioSource**.</span></span>
* <span data-ttu-id="1a9f4-246">Inserire **audiosource** nella posizione del **GameObject**appropriato.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-246">Place the **AudioSource** at the location of the appropriate **GameObject**.</span></span>
* <span data-ttu-id="1a9f4-247">Riproduce il **AudioClip** associato al movimento.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-247">Plays the **AudioClip** associated with the gesture.</span></span>

#### <a name="build-and-deploy"></a><span data-ttu-id="1a9f4-248">Compilazione e distribuzione</span><span class="sxs-lookup"><span data-stu-id="1a9f4-248">Build and Deploy</span></span>

1. <span data-ttu-id="1a9f4-249">In Unity selezionare **File > impostazioni di compilazione**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-249">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="1a9f4-250">Fai clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-250">Click **Build**.</span></span>
3. <span data-ttu-id="1a9f4-251">Fare clic sulla cartella dell' **app** .</span><span class="sxs-lookup"><span data-stu-id="1a9f4-251">Single click the **App** folder.</span></span>
4. <span data-ttu-id="1a9f4-252">Premere **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-252">Press **Select Folder**.</span></span>

<span data-ttu-id="1a9f4-253">Controllare che la barra degli strumenti indichi "versione", "x86" o "x64" e "dispositivo remoto".</span><span class="sxs-lookup"><span data-stu-id="1a9f4-253">Check that the Toolbar says "Release", "x86" or "x64", and "Remote Device".</span></span> <span data-ttu-id="1a9f4-254">In caso contrario, si tratta dell'istanza di codifica di Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-254">If not, this is the coding instance of Visual Studio.</span></span> <span data-ttu-id="1a9f4-255">Potrebbe essere necessario aprire nuovamente la soluzione dalla cartella dell'app.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-255">You may need to re-open the solution from the App folder.</span></span>

* <span data-ttu-id="1a9f4-256">Se richiesto, ricaricare i file di progetto.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-256">If prompted, reload the project files.</span></span>
* <span data-ttu-id="1a9f4-257">Come in precedenza, eseguire la distribuzione da Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-257">As before, deploy from Visual Studio.</span></span>

<span data-ttu-id="1a9f4-258">Dopo la distribuzione dell'applicazione:</span><span class="sxs-lookup"><span data-stu-id="1a9f4-258">After the application is deployed:</span></span>

* <span data-ttu-id="1a9f4-259">Osservare le modifiche apportate al suono quando ci si sposta intorno a P0LY.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-259">Observe how the sound changes as you move around P0LY.</span></span>
* <span data-ttu-id="1a9f4-260">Pronunciare *"go Hide"* per fare in modo che P0LY si sposti in una posizione sottostante.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-260">Say *"Go Hide"* to make P0LY move to a location behind you.</span></span> <span data-ttu-id="1a9f4-261">Trovarlo in base al suono.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-261">Find it by the sound.</span></span>
* <span data-ttu-id="1a9f4-262">Guardare la base dell'hub energia.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-262">Gaze at the base of the Energy Hub.</span></span> <span data-ttu-id="1a9f4-263">Toccare e trascinare verso sinistra o destra per ruotare l'ologramma e notare come il suono di clic confermi il movimento.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-263">Tap and drag left or right to rotate the hologram and notice how the clicking sound confirms the gesture.</span></span>

<span data-ttu-id="1a9f4-264">Nota: È presente un pannello di testo che tag insieme all'utente.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-264">Note: There is a text panel that will tag-along with you.</span></span> <span data-ttu-id="1a9f4-265">Questo conterrà i comandi vocali disponibili che è possibile usare in questo corso.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-265">This will contain the available voice commands that you can use throughout this course.</span></span>

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a><span data-ttu-id="1a9f4-266">Capitolo 3-mapping spaziale e spaziale</span><span class="sxs-lookup"><span data-stu-id="1a9f4-266">Chapter 3 - Spatial Sound and Spatial Mapping</span></span>

### <a name="objectives"></a><span data-ttu-id="1a9f4-267">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="1a9f4-267">Objectives</span></span>

* <span data-ttu-id="1a9f4-268">Confermare l'interazione tra ologrammi e il mondo reale usando un suono.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-268">Confirm interaction between holograms and the real world using sound.</span></span>
* <span data-ttu-id="1a9f4-269">Occludere suono che usa il mondo fisico.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-269">Occlude sound using the physical world.</span></span>

### <a name="part-1---physical-world-interaction"></a><span data-ttu-id="1a9f4-270">Parte 1: interazione con il mondo fisico</span><span class="sxs-lookup"><span data-stu-id="1a9f4-270">Part 1 - Physical World Interaction</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="1a9f4-271">Concetti chiave</span><span class="sxs-lookup"><span data-stu-id="1a9f4-271">Key Concepts</span></span>

* <span data-ttu-id="1a9f4-272">In genere, gli oggetti fisici comportano un suono quando si verifica una superficie o un altro oggetto.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-272">Physical objects generally make a sound when encountering a surface or another object.</span></span>
* <span data-ttu-id="1a9f4-273">I suoni devono essere appropriati per il contesto all'interno dell'esperienza.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-273">Sounds should be context appropriate within the experience.</span></span>

<span data-ttu-id="1a9f4-274">Ad esempio, l'impostazione di un calice in una tabella dovrebbe rendere un suono più tranquillo rispetto alla rimozione di un masso in un pezzo di metallo.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-274">For example, setting a cup on a table should make a quieter sound than dropping a boulder on a piece of metal.</span></span>

#### <a name="instructions"></a><span data-ttu-id="1a9f4-275">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="1a9f4-275">Instructions</span></span>

* <span data-ttu-id="1a9f4-276">Nel pannello **gerarchia** espandere ologrammcollection .</span><span class="sxs-lookup"><span data-stu-id="1a9f4-276">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="1a9f4-277">Espandere **EnergyHub**, selezionare **base**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-277">Expand **EnergyHub**, select **Base**.</span></span>
* <span data-ttu-id="1a9f4-278">Nel pannello di **controllo** fare clic su **Aggiungi componente** e aggiungere **toccare per inserire il suono e l'azione**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-278">In the **Inspector** panel, click **Add Component** and add **Tap To Place With Sound and Action**.</span></span>
* <span data-ttu-id="1a9f4-279">In **Tap per inserire il suono e l'azione**:</span><span class="sxs-lookup"><span data-stu-id="1a9f4-279">In **Tap To Place With Sound and Action**:</span></span>
  * <span data-ttu-id="1a9f4-280">Controllare la **posizione dell'elemento padre al tocco**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-280">Check **Place Parent On Tap**.</span></span>
  * <span data-ttu-id="1a9f4-281">Impostare il **suono del posizionamento** sul **posto**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-281">Set **Placement Sound** to **Place**.</span></span>
  * <span data-ttu-id="1a9f4-282">Imposta il **suono del pickup** su **pickup**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-282">Set **Pickup Sound** to **Pickup**.</span></span>
  * <span data-ttu-id="1a9f4-283">Premere + in basso a destra sotto l' **azione di prelievo** e **sull'azione di selezione host**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-283">Press the + in the bottom right under both **On Pickup Action** and **On Placement Action**.</span></span> <span data-ttu-id="1a9f4-284">Trascinare EnergyHub dalla scena ai campi **None (Object)** .</span><span class="sxs-lookup"><span data-stu-id="1a9f4-284">Drag EnergyHub from the scene into the **None (Object)** fields.</span></span>
    * <span data-ttu-id="1a9f4-285">In **azione di prelievo**fare clic su **Nessuna funzione** -> **EnergyHubBase** -> **ResetAnimation**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-285">Under **On Pickup Action**, click on **No Function** -> **EnergyHubBase** -> **ResetAnimation**.</span></span>
    * <span data-ttu-id="1a9f4-286">In **azione posizionamento**fare clic su **Nessuna funzione** -> **EnergyHubBase** -> **onselect**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-286">Under **On Placement Action**, click on **No Function** -> **EnergyHubBase** -> **OnSelect**.</span></span>

![Toccare per inserire il suono e l'azione](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a><span data-ttu-id="1a9f4-288">Parte 2-occlusione del suono</span><span class="sxs-lookup"><span data-stu-id="1a9f4-288">Part 2 - Sound Occlusion</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="1a9f4-289">Concetti chiave</span><span class="sxs-lookup"><span data-stu-id="1a9f4-289">Key Concepts</span></span>

* <span data-ttu-id="1a9f4-290">Il suono, come Light, può essere nascosto.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-290">Sound, like light, can be occluded.</span></span>

<span data-ttu-id="1a9f4-291">Un esempio classico è una sala concerti.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-291">A classic example is a concert hall.</span></span> <span data-ttu-id="1a9f4-292">Quando un listener si trova al di fuori della hall e la porta viene chiusa, la musica emette un suono ovattato.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-292">When a listener is standing outside of the hall and the door is closed, the music sounds muffled.</span></span> <span data-ttu-id="1a9f4-293">In genere è presente anche una riduzione del volume.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-293">There is also typically a reduction in volume.</span></span> <span data-ttu-id="1a9f4-294">Quando lo sportello viene aperto, l'intero spettro del suono viene udito nel volume effettivo.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-294">When the door is opened, the full spectrum of the sound is heard at the actual volume.</span></span> <span data-ttu-id="1a9f4-295">I suoni ad alta frequenza vengono in genere assorbiti più di frequenze basse.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-295">High frequency sounds are generally absorbed more than low frequencies.</span></span>

#### <a name="instructions"></a><span data-ttu-id="1a9f4-296">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="1a9f4-296">Instructions</span></span>

* <span data-ttu-id="1a9f4-297">Nel pannello **gerarchia** espandere ologrammcollection  e selezionare **P0LY**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-297">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="1a9f4-298">Nel pannello di **controllo** fare clic su **Aggiungi componente** e Aggiungi **emettitore audio**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-298">In the **Inspector** panel, click **Add Component** and add **Audio Emitter**.</span></span>

<span data-ttu-id="1a9f4-299">La classe Emittor audio fornisce le funzionalità seguenti:</span><span class="sxs-lookup"><span data-stu-id="1a9f4-299">The Audio Emitter class provides the following features:</span></span>

* <span data-ttu-id="1a9f4-300">Ripristina tutte le modifiche apportate al volume del **audiosource**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-300">Restores any changes to the volume of the **AudioSource**.</span></span>
* <span data-ttu-id="1a9f4-301">Esegue un oggetto **Physics. RaycastNonAlloc** dalla posizione dell'utente nella direzione del **GameObject** a cui è collegato il **AudioEmitter** .</span><span class="sxs-lookup"><span data-stu-id="1a9f4-301">Performs a **Physics.RaycastNonAlloc** from the user's position in the direction of the **GameObject** to which the **AudioEmitter** is attached.</span></span>

<span data-ttu-id="1a9f4-302">Il metodo RaycastNonAlloc viene utilizzato come ottimizzazione delle prestazioni per limitare le allocazioni e il numero di risultati restituiti.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-302">The RaycastNonAlloc method is used as a performance optimization to limit allocations as well as the number of results returned.</span></span>

* <span data-ttu-id="1a9f4-303">Per ogni **IAudioInfluencer** rilevato, chiama il metodo **ApplyEffect** .</span><span class="sxs-lookup"><span data-stu-id="1a9f4-303">For each **IAudioInfluencer** encountered, calls the **ApplyEffect** method.</span></span>
* <span data-ttu-id="1a9f4-304">Per ogni **IAudioInfluencer** precedente non più rilevata, chiamare il metodo **RemoveEffect** .</span><span class="sxs-lookup"><span data-stu-id="1a9f4-304">For each previous **IAudioInfluencer** that is no longer encountered, call the **RemoveEffect** method.</span></span>

<span data-ttu-id="1a9f4-305">Si noti che AudioEmitter viene aggiornato in base alle scale temporali umane, anziché ai singoli frame.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-305">Note that AudioEmitter updates on human time scales, as opposed to on a per frame basis.</span></span> <span data-ttu-id="1a9f4-306">Questa operazione viene eseguita perché gli utenti in genere non si spostano abbastanza rapidamente affinché l'effetto debba essere aggiornato con una frequenza maggiore di ogni trimestre o metà di un secondo.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-306">This is done because humans generally do not move fast enough for the effect to need to be updated more frequently than every quarter or half of a second.</span></span> <span data-ttu-id="1a9f4-307">Gli ologrammi che si teletrasportano rapidamente da una posizione a un'altra possono suddividere l'illusione.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-307">Holograms that teleport rapidly from one location to another can break the illusion.</span></span>

* <span data-ttu-id="1a9f4-308">Nel pannello **gerarchia** espandere ologrammcollection .</span><span class="sxs-lookup"><span data-stu-id="1a9f4-308">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="1a9f4-309">Espandere **EnergyHub** e selezionare **BlobOutside**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-309">Expand **EnergyHub** and select **BlobOutside**.</span></span>
* <span data-ttu-id="1a9f4-310">Nel pannello di **controllo** fare clic su **Aggiungi componente** e aggiungere **occlusione audio**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-310">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="1a9f4-311">In **occlusione audio**impostare **frequenza di taglio** su **1500**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-311">In **Audio Occluder**, set **Cutoff Frequency** to **1500**.</span></span>

<span data-ttu-id="1a9f4-312">Questa impostazione limita le frequenze AudioSource a 1500 Hz e inferiori.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-312">This setting limits the AudioSource frequencies to 1500 Hz and below.</span></span>

* <span data-ttu-id="1a9f4-313">Impostare **volume pass-through** su **0,9**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-313">Set **Volume Pass Through** to **0.9**.</span></span>

<span data-ttu-id="1a9f4-314">Questa impostazione riduce il volume del AudioSource al 90% del livello corrente.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-314">This setting reduces the volume of the AudioSource to 90% of it's current level.</span></span>

<span data-ttu-id="1a9f4-315">Occlusione audio implementa IAudioInfluencer per:</span><span class="sxs-lookup"><span data-stu-id="1a9f4-315">Audio Occluder implements IAudioInfluencer to:</span></span>

* <span data-ttu-id="1a9f4-316">Applicare un effetto occlusione usando un **AudioLowPassFilter** che viene collegato al **audiosource** gestito acquistare il **AudioEmitter**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-316">Apply an occlusion effect using an **AudioLowPassFilter** which gets attached to the **AudioSource** managed buy the **AudioEmitter**.</span></span>
* <span data-ttu-id="1a9f4-317">Applica l'attenuazione del volume a AudioSource.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-317">Applies volume attenuation to the AudioSource.</span></span>
* <span data-ttu-id="1a9f4-318">Disabilita l'effetto impostando una frequenza di taglio neutra e disabilitando il filtro.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-318">Disables the effect by setting a neutral cutoff frequency and disabling the filter.</span></span>

<span data-ttu-id="1a9f4-319">La frequenza utilizzata come neutra è 22 kHz (22000 Hz).</span><span class="sxs-lookup"><span data-stu-id="1a9f4-319">The frequency used as neutral is 22 kHz (22000 Hz).</span></span> <span data-ttu-id="1a9f4-320">Questa frequenza è stata scelta perché si trova al di sopra della frequenza massima nominale che può essere ascoltata dall'orecchio umano, che non ha alcun effetto discernente sul suono.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-320">This frequency was chosen due to it being above the nominal maximum frequency that can be heard by the human ear, this making no discernable impact to the sound.</span></span>

* <span data-ttu-id="1a9f4-321">Nel pannello **gerarchia** selezionare **SpatialMapping**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-321">In the **Hierarchy** panel, select **SpatialMapping**.</span></span>
* <span data-ttu-id="1a9f4-322">Nel pannello di **controllo** fare clic su **Aggiungi componente** e aggiungere **occlusione audio**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-322">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="1a9f4-323">In **occlusione audio**impostare **frequenza di taglio** su **750**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-323">In **Audio Occluder**, set **Cutoff Frequency** to **750**.</span></span>

<span data-ttu-id="1a9f4-324">Quando più occluders si trovano nel percorso tra l'utente e il **AudioEmitter**, viene applicata la frequenza più bassa al filtro.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-324">When multiple occluders are in the path between the user and the **AudioEmitter**, the lowest frequency is applied to the filter.</span></span>

* <span data-ttu-id="1a9f4-325">Impostare **volume pass-through** su **0,75**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-325">Set **Volume Pass Through** to **0.75**.</span></span>

<span data-ttu-id="1a9f4-326">Quando più occluders si trovano nel percorso tra l'utente e il **AudioEmitter**, il pass-through del volume viene applicato in aggiunta.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-326">When multiple occluders are in the path between the user and the **AudioEmitter**, the volume pass through is applied additively.</span></span>

* <span data-ttu-id="1a9f4-327">Nel pannello **gerarchia** selezionare managers .</span><span class="sxs-lookup"><span data-stu-id="1a9f4-327">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="1a9f4-328">Nel pannello **Inspector** espandere gestore di **input vocale**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-328">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="1a9f4-329">In **gestore di input vocale**espandere **Vai**a addebiti.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-329">In **Speech Input Handler**, expand **Go Charge**.</span></span>
* <span data-ttu-id="1a9f4-330">Modificare **Nessuna funzione** in **poliactions. GoCharge**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-330">Change **No Function** to **PolyActions.GoCharge**.</span></span>

![Parola chiave Ricarica](images/gocharge.png)

* <span data-ttu-id="1a9f4-332">Espandi **.**</span><span class="sxs-lookup"><span data-stu-id="1a9f4-332">Expand **Come Here**.</span></span>
* <span data-ttu-id="1a9f4-333">**Non modificare alcuna funzione** in poliactions **. Comeback**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-333">Change **No Function** to **PolyActions.ComeBack**.</span></span>

![Parola chiave Vieni qui](images/comehere.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="1a9f4-335">Compilazione e distribuzione</span><span class="sxs-lookup"><span data-stu-id="1a9f4-335">Build and Deploy</span></span>

* <span data-ttu-id="1a9f4-336">Come in precedenza, compilare il progetto in Unity e distribuirlo in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-336">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="1a9f4-337">Dopo la distribuzione dell'applicazione:</span><span class="sxs-lookup"><span data-stu-id="1a9f4-337">After the application is deployed:</span></span>

* <span data-ttu-id="1a9f4-338">Pronunciare *"go charge"* per fare in modo che P0LY entri nell'hub di energia.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-338">Say *"Go Charge"* to have P0LY enter the Energy Hub.</span></span>

<span data-ttu-id="1a9f4-339">Si noti la modifica apportata al suono.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-339">Note the change in the sound.</span></span> <span data-ttu-id="1a9f4-340">Dovrebbe sembrare ovattato e leggermente più tranquillo.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-340">It should sound muffled and a little quieter.</span></span> <span data-ttu-id="1a9f4-341">Se si è in grado di posizionarsi con un muro o un altro oggetto tra l'utente e l'hub energetico, è necessario notare un ulteriore silenziatore del suono a causa dell'occlusione del mondo reale.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-341">If you are able to position yourself with a wall or other object between you and the Energy Hub, you should notice a further muffling of the sound due to the occlusion by the real world.</span></span>

* <span data-ttu-id="1a9f4-342">Pronunciare *"qui"* per fare in modo che P0LY lasci l'hub di energia e la posizione in primo piano.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-342">Say *"Come Here"* to have P0LY leave the Energy Hub and position itself in front of you.</span></span>

<span data-ttu-id="1a9f4-343">Si noti che l'occlusione audio viene rimossa quando P0LY esce dall'hub di energia.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-343">Note that the sound occlusion is removed once P0LY exits the Energy Hub.</span></span> <span data-ttu-id="1a9f4-344">Se si sta ancora sentendo l'occlusione, P0LY potrebbe essere bloccato dal mondo reale.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-344">If you are still hearing occlusion, P0LY may be occluded by the real world.</span></span> <span data-ttu-id="1a9f4-345">Provare a eseguire il passaggio per assicurarsi di avere una chiara linea di visibilità per P0LY.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-345">Try moving to ensure you have a clear line of sight to P0LY.</span></span>

### <a name="part-3---room-models"></a><span data-ttu-id="1a9f4-346">Parte 3-modelli di chat room</span><span class="sxs-lookup"><span data-stu-id="1a9f4-346">Part 3 - Room Models</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="1a9f4-347">Concetti chiave</span><span class="sxs-lookup"><span data-stu-id="1a9f4-347">Key Concepts</span></span>

* <span data-ttu-id="1a9f4-348">La dimensione dello spazio fornisce le code subliminali che contribuiscono alla localizzazione del suono.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-348">The size of the space provides subliminal queues that contribute to sound localization.</span></span>
* <span data-ttu-id="1a9f4-349">I modelli room sono impostati per ogni**audiosource**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-349">Room models are set per-**AudioSource**.</span></span>
* <span data-ttu-id="1a9f4-350">[MixedRealityToolkit per Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) fornisce il codice per l'impostazione del modello room.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-350">The [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides code for setting the room model.</span></span>
* <span data-ttu-id="1a9f4-351">Per esperienze di realtà mista, selezionare il modello room più adatto allo spazio reale.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-351">For Mixed Reality experiences, select the room model that best fits the real world space.</span></span>

<span data-ttu-id="1a9f4-352">Se si sta creando uno scenario di realtà virtuale, selezionare il modello room più adatto all'ambiente virtuale.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-352">If you are creating a Virtual Reality scenario, select the room model that best fits the virtual environment.</span></span>

## <a name="chapter-4---sound-design"></a><span data-ttu-id="1a9f4-353">Capitolo 4-progettazione audio</span><span class="sxs-lookup"><span data-stu-id="1a9f4-353">Chapter 4 - Sound Design</span></span>

### <a name="objectives"></a><span data-ttu-id="1a9f4-354">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="1a9f4-354">Objectives</span></span>

* <span data-ttu-id="1a9f4-355">Comprendere le considerazioni relative alla progettazione di un suono efficace.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-355">Understand considerations for effective sound design.</span></span>
* <span data-ttu-id="1a9f4-356">Impara a combinare tecniche e linee guida.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-356">Learn mixing techniques and guidelines.</span></span>

### <a name="part-1---sound-and-experience-design"></a><span data-ttu-id="1a9f4-357">Parte 1: progettazione di suoni e esperienza</span><span class="sxs-lookup"><span data-stu-id="1a9f4-357">Part 1 - Sound and Experience Design</span></span>

<span data-ttu-id="1a9f4-358">In questa sezione vengono illustrate le linee guida e le considerazioni principali relative alla progettazione.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-358">This section discusses key sound and experience design considerations and guidelines.</span></span>

#### <a name="normalize-all-sounds"></a><span data-ttu-id="1a9f4-359">Normalizza tutti i suoni</span><span class="sxs-lookup"><span data-stu-id="1a9f4-359">Normalize all sounds</span></span>

<span data-ttu-id="1a9f4-360">In questo modo si evita la necessità di codice del case speciale per modificare i livelli del volume per ogni suono, che può richiedere molto tempo e limita la possibilità di aggiornare facilmente i file audio.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-360">This avoids the need for special case code to adjust volume levels per sound, which can be time consuming and limits the ability to easily update sound files.</span></span>

#### <a name="design-for-an-untethered-experience"></a><span data-ttu-id="1a9f4-361">Progettazione per un'esperienza non legata</span><span class="sxs-lookup"><span data-stu-id="1a9f4-361">Design for an untethered experience</span></span>

<span data-ttu-id="1a9f4-362">HoloLens è un computer olografico completamente indipendente e non tethered.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-362">HoloLens is a fully contained, untethered holographic computer.</span></span> <span data-ttu-id="1a9f4-363">Gli utenti possono e utilizzeranno le proprie esperienze durante lo trasferimento.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-363">Your users can and will use your experiences while moving.</span></span> <span data-ttu-id="1a9f4-364">Assicurarsi di testare la combinazione di audio aggirando.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-364">Be sure to test your audio mix by walking around.</span></span>

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a><span data-ttu-id="1a9f4-365">Emettere un suono da posizioni logiche sugli ologrammi</span><span class="sxs-lookup"><span data-stu-id="1a9f4-365">Emit sound from logical locations on your holograms</span></span>

<span data-ttu-id="1a9f4-366">Nel mondo reale, un cane non abbaia dalla coda e la voce umana non proviene dai suoi piedi.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-366">In the real world, a dog does not bark from its tail and a human's voice does not come from his/her feet.</span></span> <span data-ttu-id="1a9f4-367">Evitare di creare suoni da parti impreviste degli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-367">Avoid having your sounds emit from unexpected portions of your holograms.</span></span>

<span data-ttu-id="1a9f4-368">Per gli ologrammi di piccole dimensioni, è ragionevole avere suono emesso dal centro della geometria.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-368">For small holograms, it is reasonable to have sound emit from the center of the geometry.</span></span>

#### <a name="familiar-sounds-are-most-localizable"></a><span data-ttu-id="1a9f4-369">I suoni noti sono più localizzabili</span><span class="sxs-lookup"><span data-stu-id="1a9f4-369">Familiar sounds are most localizable</span></span>

<span data-ttu-id="1a9f4-370">La voce e la musica umana sono molto facili da localizzare.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-370">The human voice and music are very easy to localize.</span></span> <span data-ttu-id="1a9f4-371">Se un utente chiama il proprio nome, è possibile determinare in modo molto accurato dalla direzione della voce e dal punto in cui si è lontani.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-371">If someone calls your name, you are able to very accurately determine from what direction the voice came and from how far away.</span></span> <span data-ttu-id="1a9f4-372">I suoni brevi e non noti sono più difficili da localizzare.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-372">Short, unfamiliar sounds are harder to localize.</span></span>

#### <a name="be-cognizant-of-user-expectations"></a><span data-ttu-id="1a9f4-373">Tenere a conoscenza delle aspettative degli utenti</span><span class="sxs-lookup"><span data-stu-id="1a9f4-373">Be cognizant of user expectations</span></span>

<span data-ttu-id="1a9f4-374">L'esperienza di vita gioca una parte della capacità di identificare la posizione di un suono.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-374">Life experience plays a part in our ability to identify the location of a sound.</span></span> <span data-ttu-id="1a9f4-375">Questo è uno dei motivi per cui la voce umana è particolarmente facile da localizzare.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-375">This is one reason why the human voice is particularly easy to localize.</span></span> <span data-ttu-id="1a9f4-376">È importante essere a conoscenza delle aspettative apprese dall'utente quando si posizionano i suoni.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-376">It is important to be aware of your user's learned expectations when placing your sounds.</span></span>

<span data-ttu-id="1a9f4-377">Ad esempio, quando qualcuno ascolta un brano di Bird, in genere cerca, perché gli uccelli tendono a essere al di sopra della linea di vista (Flying o in un albero).</span><span class="sxs-lookup"><span data-stu-id="1a9f4-377">For example, when someone hears a bird song they generally look up, as birds tend to be above the line of sight (flying or in a tree).</span></span> <span data-ttu-id="1a9f4-378">Non è insolito che un utente accenda la direzione corretta di un suono, ma si trovi nella direzione verticale errata e si confonde o si frustra quando non è in grado di trovare l'ologramma.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-378">It is not uncommon for a user to turn in the correct direction of a sound, but look in the wrong vertical direction and become confused or frustrated when they are unable to find the hologram.</span></span>

#### <a name="avoid-hidden-emitters"></a><span data-ttu-id="1a9f4-379">Evitare gli emettitori nascosti</span><span class="sxs-lookup"><span data-stu-id="1a9f4-379">Avoid hidden emitters</span></span>

<span data-ttu-id="1a9f4-380">Nel mondo reale, se viene emesso un segnale acustico, in genere è possibile identificare l'oggetto che emette il suono.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-380">In the real world, if we hear a sound, we can generally identify the object that is emitting the sound.</span></span> <span data-ttu-id="1a9f4-381">Questa operazione dovrebbe essere valida anche per le proprie esperienze.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-381">This should also hold true in your experiences.</span></span> <span data-ttu-id="1a9f4-382">Per gli utenti può essere molto sconcertante ascoltare un suono, sapere da dove ha origine il suono e non essere in grado di visualizzare un oggetto.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-382">It can be very disconcerting for users to hear a sound, know from where the sound originates and be unable to see an object.</span></span>

<span data-ttu-id="1a9f4-383">Esistono alcune eccezioni a questa linea guida.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-383">There are some exceptions to this guideline.</span></span> <span data-ttu-id="1a9f4-384">Ad esempio, i suoni di ambiente come i cricket in un campo non devono essere visibili.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-384">For example, ambient sounds such as crickets in a field need not be visible.</span></span> <span data-ttu-id="1a9f4-385">L'esperienza di vita offre familiarità con l'origine di questi suoni senza la necessità di visualizzarla.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-385">Life experience gives us familiarity with the source of these sounds without the need to see it.</span></span>

### <a name="part-2---sound-mixing"></a><span data-ttu-id="1a9f4-386">Parte 2-combinazione di suoni</span><span class="sxs-lookup"><span data-stu-id="1a9f4-386">Part 2 - Sound Mixing</span></span>

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a><span data-ttu-id="1a9f4-387">Specificare come destinazione la combinazione per il volume del 70% nel HoloLens</span><span class="sxs-lookup"><span data-stu-id="1a9f4-387">Target your mix for 70% volume on the HoloLens</span></span>

<span data-ttu-id="1a9f4-388">Le esperienze di realtà miste consentono di osservare gli ologrammi nel mondo reale.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-388">Mixed Reality experiences allow holograms to be seen in the real world.</span></span> <span data-ttu-id="1a9f4-389">Devono inoltre consentire l'ascolto di suoni reali.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-389">They should also allow real world sounds to be heard.</span></span> <span data-ttu-id="1a9f4-390">Una destinazione del volume del 70% consente all'utente di sentire il mondo intorno al suono dell'esperienza.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-390">A 70% volume target enables the user to hear the world around them along with the sound of your experience.</span></span>

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a><span data-ttu-id="1a9f4-391">Il volume HoloLens al 100% dovrebbe escludere i suoni esterni</span><span class="sxs-lookup"><span data-stu-id="1a9f4-391">HoloLens at 100% volume should drown out external sounds</span></span>

<span data-ttu-id="1a9f4-392">Un livello di volume pari al 100% è analogo a un'esperienza di realtà virtuale.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-392">A volume level of 100% is akin to a Virtual Reality experience.</span></span> <span data-ttu-id="1a9f4-393">Visivamente, l'utente viene trasportato in un altro mondo.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-393">Visually, the user is transported to a different world.</span></span> <span data-ttu-id="1a9f4-394">Lo stesso vale per il vero udibile.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-394">The same should hold true audibly.</span></span>

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a><span data-ttu-id="1a9f4-395">Usare Unity AudioMixer per modificare le categorie di suoni</span><span class="sxs-lookup"><span data-stu-id="1a9f4-395">Use the Unity AudioMixer to adjust categories of sounds</span></span>

<span data-ttu-id="1a9f4-396">Quando si progetta la combinazione, è spesso utile creare categorie audio e avere la possibilità di aumentare o diminuire il volume come unità.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-396">When designing your mix, it is often helpful to create sound categories and have the ability to increase or decrease their volume as a unit.</span></span> <span data-ttu-id="1a9f4-397">Questo consente di mantenere i livelli relativi di ogni suono, consentendo al tempo stesso di apportare modifiche rapide e semplici alla combinazione complessiva.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-397">This retains the relative levels of each sound while enabling quick and easy changes to the overall mix.</span></span> <span data-ttu-id="1a9f4-398">Le categorie comuni includono; effetti audio, ambiente, Voice over e musica in background.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-398">Common categories include; sound effects, ambience, voice overs and background music.</span></span>

#### <a name="mix-sounds-based-on-the-users-gaze"></a><span data-ttu-id="1a9f4-399">Combinare i suoni in base allo sguardo dell'utente</span><span class="sxs-lookup"><span data-stu-id="1a9f4-399">Mix sounds based on the user's gaze</span></span>

<span data-ttu-id="1a9f4-400">Spesso può essere utile modificare la combinazione di suoni nell'esperienza in base alla posizione dell'utente (o non).</span><span class="sxs-lookup"><span data-stu-id="1a9f4-400">It can often be useful to change the sound mix in your experience based on where a user is (or is not) looking.</span></span> <span data-ttu-id="1a9f4-401">Un uso comune di questa tecnica consiste nel ridurre il livello di volume per gli ologrammi esterni al frame olografico, in modo da rendere più semplice per l'utente concentrarsi sulle informazioni in primo piano.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-401">One common use for this technique are to reduce the volume level for holograms that are outside of the Holographic Frame to make it easier for the user to focus on the information in front of them.</span></span> <span data-ttu-id="1a9f4-402">Un altro utilizzo consiste nell'aumentare il volume di un suono per attirare l'attenzione dell'utente su un evento importante.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-402">Another use is to increase the volume of a sound to draw the user's attention to an important event.</span></span>

#### <a name="building-your-mix"></a><span data-ttu-id="1a9f4-403">Creazione della combinazione</span><span class="sxs-lookup"><span data-stu-id="1a9f4-403">Building your mix</span></span>

<span data-ttu-id="1a9f4-404">Quando si compila la combinazione, è consigliabile iniziare con l'audio in background dell'esperienza e aggiungere i livelli in base all'importanza.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-404">When building your mix, it is recommended to start with your experience's background audio and add layers based on importance.</span></span> <span data-ttu-id="1a9f4-405">Spesso, il risultato è che ogni livello è più elevato rispetto a quello precedente.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-405">Often, this results in each layer being louder than the previous.</span></span>

<span data-ttu-id="1a9f4-406">Immaginando la combinazione di un imbuto invertito, con i suoni meno importanti (e generalmente più tranquilli) nella parte inferiore, si consiglia di strutturare la combinazione in modo analogo al diagramma seguente.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-406">Imagining your mix as an inverted funnel, with the least important (and generally quietest sounds) at the bottom, it is recommended to structure your mix similar to the following diagram.</span></span>

![Struttura del mix audio](images/soundlevels.png)

<span data-ttu-id="1a9f4-408">I Voice over sono uno scenario interessante.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-408">Voice overs are an interesting scenario.</span></span> <span data-ttu-id="1a9f4-409">In base all'esperienza che si sta creando, potrebbe essere necessario disporre di un audio stereo (non localizzato) o di spatialize.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-409">Based on the experience you are creating you may wish to have a stereo (not localized) sound or to spatialize your voice overs.</span></span> <span data-ttu-id="1a9f4-410">Due esperienze pubblicate da Microsoft illustrano esempi eccellenti di ogni scenario.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-410">Two Microsoft published experiences illustrate excellent examples of each scenario.</span></span>

<span data-ttu-id="1a9f4-411">[HoloTour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87) usa una voce stereo.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-411">[HoloTour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87) uses a stereo voice over.</span></span> <span data-ttu-id="1a9f4-412">Quando l'Assistente vocale descrive la posizione visualizzata, il suono è coerente e non varia in base alla posizione dell'utente.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-412">When the narrator is describing the location being viewed, the sound is consistent and does not vary based on the user's position.</span></span> <span data-ttu-id="1a9f4-413">Ciò consente all'Assistente vocale di descrivere la scena senza togliere i suoni spaziali dell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-413">This enables the narrator to describe the scene without taking away from the spatialized sounds of the environment.</span></span>

<span data-ttu-id="1a9f4-414">I [frammenti](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) utilizzano una voce con spazialità sotto forma di detective.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-414">[Fragments](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) utilizes a spatialized voice over in the form of a detective.</span></span> <span data-ttu-id="1a9f4-415">La voce del detective viene usata per aiutare a attirare l'attenzione dell'utente su un importante indizio come se fosse presente un uomo reale nella stanza.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-415">The detective's voice is used to help bring the user's attention to an important clue as if an actual human was in the room.</span></span> <span data-ttu-id="1a9f4-416">Questo consente un senso ancora più approfondito dell'esperienza di risoluzione del mistero.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-416">This enables an even greater sense of immersion into the experience of solving the mystery.</span></span>

### <a name="part-3--performance"></a><span data-ttu-id="1a9f4-417">Parte 3: prestazioni</span><span class="sxs-lookup"><span data-stu-id="1a9f4-417">Part 3 -Performance</span></span>

#### <a name="cpu-usage"></a><span data-ttu-id="1a9f4-418">Utilizzo CPU</span><span class="sxs-lookup"><span data-stu-id="1a9f4-418">CPU usage</span></span>

<span data-ttu-id="1a9f4-419">Quando si usa il suono spaziale, gli emettitori 10-12 utilizzeranno approssimativamente il 12% della CPU.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-419">When using Spatial Sound, 10 - 12 emitters will consume approximately 12% of the CPU.</span></span>

#### <a name="stream-long-audio-files"></a><span data-ttu-id="1a9f4-420">Streaming di file audio lunghi</span><span class="sxs-lookup"><span data-stu-id="1a9f4-420">Stream long audio files</span></span>

<span data-ttu-id="1a9f4-421">I dati audio possono essere di grandi dimensioni, soprattutto a tariffe di esempio comuni (44,1 e 48 kHz).</span><span class="sxs-lookup"><span data-stu-id="1a9f4-421">Audio data can be large, especially at common sample rates (44.1 and 48 kHz).</span></span> <span data-ttu-id="1a9f4-422">Una regola generale è che i file audio più lunghi di 5-10 secondi devono essere trasmessi per ridurre l'utilizzo della memoria dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-422">A general rule is that audio files longer than 5 - 10 seconds should be streamed to reduce application memory usage.</span></span>

<span data-ttu-id="1a9f4-423">In Unity è possibile contrassegnare un file audio per il flusso nelle impostazioni di importazione del file.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-423">In Unity, you can mark an audio file for streaming in the file's import settings.</span></span>

![Impostazioni di importazione audio](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a><span data-ttu-id="1a9f4-425">Capitolo 5-effetti speciali</span><span class="sxs-lookup"><span data-stu-id="1a9f4-425">Chapter 5 - Special Effects</span></span>

### <a name="objectives"></a><span data-ttu-id="1a9f4-426">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="1a9f4-426">Objectives</span></span>

* <span data-ttu-id="1a9f4-427">Aggiungere Depth a "Magic Windows".</span><span class="sxs-lookup"><span data-stu-id="1a9f4-427">Add depth to "Magic Windows".</span></span>
* <span data-ttu-id="1a9f4-428">Porta l'utente nel mondo virtuale.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-428">Bring the user into the virtual world.</span></span>

### <a name="magic-windows"></a><span data-ttu-id="1a9f4-429">Finestre magiche</span><span class="sxs-lookup"><span data-stu-id="1a9f4-429">Magic Windows</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="1a9f4-430">Concetti chiave</span><span class="sxs-lookup"><span data-stu-id="1a9f4-430">Key Concepts</span></span>

* <span data-ttu-id="1a9f4-431">La creazione di visualizzazioni in un ambiente nascosto è visivamente accattivante.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-431">Creating views into a hidden world, is visually compelling.</span></span>
* <span data-ttu-id="1a9f4-432">Migliora il realismo aggiungendo effetti audio quando un ologramma o l'utente è vicino al mondo nascosto.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-432">Enhance realism by adding audio effects when a hologram or the user is near the hidden world.</span></span>

#### <a name="instructions"></a><span data-ttu-id="1a9f4-433">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="1a9f4-433">Instructions</span></span>

* <span data-ttu-id="1a9f4-434">Nel pannello **gerarchia** espandere ologrammcollection  e selezionare Sottomondo .</span><span class="sxs-lookup"><span data-stu-id="1a9f4-434">In the **Hierarchy** panel, expand **HologramCollection** and select **Underworld**.</span></span>
* <span data-ttu-id="1a9f4-435">Espandere **Underworld** e selezionare **VoiceSource**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-435">Expand **Underworld** and select **VoiceSource**.</span></span>
* <span data-ttu-id="1a9f4-436">Nel pannello di **controllo** fare clic su **Aggiungi componente** e aggiungere **effetto voce utente**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-436">In the **Inspector** panel, click **Add Component** and add **User Voice Effect**.</span></span>

<span data-ttu-id="1a9f4-437">Verrà aggiunto un componente **audiosource** a **VoiceSource**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-437">An **AudioSource** component will be added to **VoiceSource**.</span></span>

* <span data-ttu-id="1a9f4-438">In **audiosource**impostare **output** su **UserVoice (mixer)** .</span><span class="sxs-lookup"><span data-stu-id="1a9f4-438">In **AudioSource**, set **Output** to **UserVoice (Mixer)**.</span></span>
* <span data-ttu-id="1a9f4-439">Selezionare la casella di controllo **Spatialize** .</span><span class="sxs-lookup"><span data-stu-id="1a9f4-439">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="1a9f4-440">Trascinare il dispositivo di scorrimento di **Blend spaziale** fino a **3D**oppure immettere **1** nella casella di modifica.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-440">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>
* <span data-ttu-id="1a9f4-441">Espandere **impostazioni audio 3D**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-441">Expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="1a9f4-442">Impostare il **livello di Doppler** su **0**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-442">Set **Doppler Level** to **0**.</span></span>
* <span data-ttu-id="1a9f4-443">In **effetto voce utente**impostare **oggetto padre** sul Sottomondo  dalla scena.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-443">In **User Voice Effect**, set **Parent Object** to the **Underworld** from the scene.</span></span>
* <span data-ttu-id="1a9f4-444">Impostare **distanza massima** su **1**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-444">Set **Max Distance** to **1**.</span></span>

<span data-ttu-id="1a9f4-445">L'impostazione della **distanza massima** indica all' **utente** il modo in cui la chiusura dell'utente deve essere l'oggetto padre prima che l'effetto venga attivato.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-445">Setting **Max Distance** tells **User Voice Effect** how close the user must be to the parent object before the effect is enabled.</span></span>

* <span data-ttu-id="1a9f4-446">In **effetto voce utente**espandere **parametri Chorus**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-446">In **User Voice Effect**, expand **Chorus Parameters**.</span></span>
* <span data-ttu-id="1a9f4-447">Impostare **Depth** su **0,1**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-447">Set **Depth** to **0.1**.</span></span>
* <span data-ttu-id="1a9f4-448">Impostare **toccare 1 volume**, **toccare 2 volume** e **toccare 3 volume** su **0,8**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-448">Set **Tap 1 Volume**, **Tap 2 Volume** and **Tap 3 Volume** to **0.8**.</span></span>
* <span data-ttu-id="1a9f4-449">Impostare **volume audio originale** su **0,5**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-449">Set **Original Sound Volume** to **0.5**.</span></span>

<span data-ttu-id="1a9f4-450">Le impostazioni precedenti configurano i parametri del **AudioChorusFilter** Unity usato per aggiungere ricchezza alla voce dell'utente.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-450">The previous settings configure the parameters of the Unity **AudioChorusFilter** used to add richness to the user's voice.</span></span>

* <span data-ttu-id="1a9f4-451">In **effetto voce utente**espandere **parametri Echo**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-451">In **User Voice Effect**, expand **Echo Parameters**.</span></span>
* <span data-ttu-id="1a9f4-452">Imposta **ritardo** su **300**</span><span class="sxs-lookup"><span data-stu-id="1a9f4-452">Set **Delay** to **300**</span></span>
* <span data-ttu-id="1a9f4-453">Imposta il **rapporto** di decadimento su **0,2**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-453">Set **Decay Ratio** to **0.2**.</span></span>
* <span data-ttu-id="1a9f4-454">Impostare **volume audio originale** su **0**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-454">Set **Original Sound Volume** to **0**.</span></span>

<span data-ttu-id="1a9f4-455">Le impostazioni precedenti configurano i parametri del **AudioEchoFilter** Unity usato per fare in modo che la voce dell'utente sia Echo.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-455">The previous settings configure the parameters of the Unity **AudioEchoFilter** used to cause the user's voice to echo.</span></span>

<span data-ttu-id="1a9f4-456">Lo script dell'effetto vocale utente è responsabile di:</span><span class="sxs-lookup"><span data-stu-id="1a9f4-456">The User Voice Effect script is responsible for:</span></span>

* <span data-ttu-id="1a9f4-457">Misurazione della distanza tra l'utente e la **GameObject** a cui è associato lo script.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-457">Measuring the distance between the user and the **GameObject** to which the script is attached.</span></span>
* <span data-ttu-id="1a9f4-458">Determinare se l'utente si trova o meno a **GameObject**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-458">Determining whether or not the user is facing the **GameObject**.</span></span>

<span data-ttu-id="1a9f4-459">È necessario che l'utente si trovi a fronte del GameObject, indipendentemente dalla distanza, per abilitare l'effetto.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-459">The user must be facing the GameObject, regardless of distance, for the effect to be enabled.</span></span>

* <span data-ttu-id="1a9f4-460">Applicazione e configurazione di un **AudioChorusFilter** e di un **AudioEchoFilter** in **audiosource**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-460">Applying and configuring an **AudioChorusFilter** and an **AudioEchoFilter** to the **AudioSource**.</span></span>
* <span data-ttu-id="1a9f4-461">Disabilitare l'effetto disabilitando i filtri.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-461">Disabling the effect by disabling the filters.</span></span>

<span data-ttu-id="1a9f4-462">L'effetto voce utente usa il componente MIC Stream Selector, da [MixedRealityToolkit per Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), per selezionare il flusso di voce di qualità elevata e instradarlo nel sistema audio di Unity.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-462">User Voice Effect uses the Mic Stream Selector component, from the [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), to select the high quality voice stream and route it into Unity's audio system.</span></span>

* <span data-ttu-id="1a9f4-463">Nel pannello **gerarchia** selezionare managers .</span><span class="sxs-lookup"><span data-stu-id="1a9f4-463">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="1a9f4-464">Nel pannello **Inspector** espandere gestore di **input vocale**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-464">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="1a9f4-465">In **gestore di input vocale**espandere **Mostra Sottomondo**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-465">In **Speech Input Handler**, expand **Show Underworld**.</span></span>
* <span data-ttu-id="1a9f4-466">Modificare **Nessuna funzione** in **UnderworldBase. OnEnable**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-466">Change **No Function** to **UnderworldBase.OnEnable**.</span></span>

![Parola chiave Mostra Sottomondo](images/showunderworld.png)

* <span data-ttu-id="1a9f4-468">Espandi **Nascondi Sottomondo**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-468">Expand **Hide Underworld**.</span></span>
* <span data-ttu-id="1a9f4-469">Modificare **Nessuna funzione** in **UnderworldBase. ondisable**.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-469">Change **No Function** to **UnderworldBase.OnDisable**.</span></span>

![Parola chiave Nascondi Sottomondo](images/hideunderworld.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="1a9f4-471">Compilazione e distribuzione</span><span class="sxs-lookup"><span data-stu-id="1a9f4-471">Build and Deploy</span></span>

* <span data-ttu-id="1a9f4-472">Come in precedenza, compilare il progetto in Unity e distribuirlo in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-472">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="1a9f4-473">Dopo la distribuzione dell'applicazione:</span><span class="sxs-lookup"><span data-stu-id="1a9f4-473">After the application is deployed:</span></span>

* <span data-ttu-id="1a9f4-474">Far fronte a una superficie (Wall, Floor, Table) e pronunciare *"Show Underworld"* .</span><span class="sxs-lookup"><span data-stu-id="1a9f4-474">Face a surface (wall, floor, table) and say *"Show Underworld"*.</span></span>

<span data-ttu-id="1a9f4-475">Il Sottomondo verrà visualizzato e tutti gli altri ologrammi verranno nascosti.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-475">The underworld will be shown and all other holograms will be hidden.</span></span> <span data-ttu-id="1a9f4-476">Se il Sottomondo non viene visualizzato, assicurarsi di essere connessi a una superficie reale.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-476">If you do not see the underworld, ensure that you are facing a real-world surface.</span></span>

* <span data-ttu-id="1a9f4-477">Approccio entro 1 metro dell'ologramma del Sottomondo e iniziare a comunicare.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-477">Approach within 1 meter of the underworld hologram and start talking.</span></span>

<span data-ttu-id="1a9f4-478">Sono ora applicati effetti audio alla voce.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-478">There are now audio effects applied to your voice!</span></span>

* <span data-ttu-id="1a9f4-479">Allontanarsi dal Sottomondo e notare il modo in cui l'effetto non viene più applicato.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-479">Turn away from the underworld and notice how the effect is no longer applied.</span></span>
* <span data-ttu-id="1a9f4-480">Pronunciare *"Hide Underworld"* per nascondere il Sottomondo.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-480">Say *"Hide Underworld"* to hide the underworld.</span></span>

<span data-ttu-id="1a9f4-481">Il Sottomondo verrà nascosto e verranno nuovamente visualizzati gli ologrammi nascosti in precedenza.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-481">The underworld will be hidden and the previously hidden holograms will reappear.</span></span>

## <a name="the-end"></a><span data-ttu-id="1a9f4-482">La fine</span><span class="sxs-lookup"><span data-stu-id="1a9f4-482">The End</span></span>

<span data-ttu-id="1a9f4-483">La procedura è stata completata.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-483">Congratulations!</span></span> <span data-ttu-id="1a9f4-484">A questo punto è **stato completato lo spazio di 220: Audio**spaziale.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-484">You have now completed **MR Spatial 220: Spatial sound**.</span></span>

<span data-ttu-id="1a9f4-485">Ascolta il mondo e fai vivere le tue esperienze con i suoni.</span><span class="sxs-lookup"><span data-stu-id="1a9f4-485">Listen to the world and bring your experiences to life with sound!</span></span>

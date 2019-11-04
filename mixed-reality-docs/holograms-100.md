---
title: Nozioni fondamentali 100-Introduzione a Unity
description: Informazioni su come creare la prima applicazione "Hello World" di base per la realtà mista.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: realtà mista, realtà mista di Windows, HoloLens, immersiva, VR, Mr, introduzione, ologramma, Accademia, esercitazione
ms.openlocfilehash: 5e9a90af6b80333addbde2a2e11086372483b7c3
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434781"
---
>[!NOTE]
><span data-ttu-id="aefec-104">Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.</span><span class="sxs-lookup"><span data-stu-id="aefec-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="aefec-105">Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.</span><span class="sxs-lookup"><span data-stu-id="aefec-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="aefec-106">Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="aefec-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="aefec-107">Verranno mantenuti per continuare a usare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="aefec-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="aefec-108">Per HoloLens 2 è stata pubblicata [una nuova serie di esercitazioni](mrlearning-base.md) .</span><span class="sxs-lookup"><span data-stu-id="aefec-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

# <a name="mr-basics-100-getting-started-with-unity"></a><span data-ttu-id="aefec-109">Nozioni fondamentali 100: Introduzione a Unity</span><span class="sxs-lookup"><span data-stu-id="aefec-109">MR Basics 100: Getting started with Unity</span></span>

<span data-ttu-id="aefec-110">Questa esercitazione illustra come creare un'app di base per realtà mista compilata con Unity.</span><span class="sxs-lookup"><span data-stu-id="aefec-110">This tutorial will walk you through creating a basic mixed reality app built with Unity.</span></span>

## <a name="device-support"></a><span data-ttu-id="aefec-111">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="aefec-111">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="aefec-112">Corso</span><span class="sxs-lookup"><span data-stu-id="aefec-112">Course</span></span></th><th style="width:150px"> <span data-ttu-id="aefec-113"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="aefec-113"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="aefec-114"><a href="immersive-headset-hardware-details.md">Visori VR immersive</a></span><span class="sxs-lookup"><span data-stu-id="aefec-114"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="aefec-115">Nozioni fondamentali 100: Introduzione a Unity</span><span class="sxs-lookup"><span data-stu-id="aefec-115">MR Basics 100: Getting started with Unity</span></span></td><td style="text-align: center;"> <span data-ttu-id="aefec-116">✔️</span><span class="sxs-lookup"><span data-stu-id="aefec-116">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="aefec-117">✔️</span><span class="sxs-lookup"><span data-stu-id="aefec-117">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="aefec-118">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="aefec-118">Prerequisites</span></span>

* <span data-ttu-id="aefec-119">Un PC Windows 10 configurato con gli [strumenti corretti installati](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="aefec-119">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>

## <a name="chapter-1---create-a-new-project"></a><span data-ttu-id="aefec-120">Capitolo 1-creare un nuovo progetto</span><span class="sxs-lookup"><span data-stu-id="aefec-120">Chapter 1 - Create a New Project</span></span>

>[!VIDEO https://www.youtube.com/embed/2L5IFO0hnYA]

<span data-ttu-id="aefec-121">Per compilare un'app con Unity, è prima di tutto necessario creare un progetto.</span><span class="sxs-lookup"><span data-stu-id="aefec-121">To build an app with Unity, you first need to create a project.</span></span> <span data-ttu-id="aefec-122">Questo progetto è organizzato in alcune cartelle, il più importante dei quali è la cartella assets.</span><span class="sxs-lookup"><span data-stu-id="aefec-122">This project is organized into a few folders, the most important of which is your Assets folder.</span></span> <span data-ttu-id="aefec-123">Si tratta della cartella che include tutte le risorse importate da strumenti per la creazione di contenuti digitali, ad esempio Maya, max cinema 4D o Photoshop, tutto il codice creato con Visual Studio o l'editor di codice preferito e un numero qualsiasi di file di contenuto creati da Unity durante la composizione di scene , animazioni e altri tipi di asset Unity nell'editor.</span><span class="sxs-lookup"><span data-stu-id="aefec-123">This is the folder that holds all assets you import from digital content creation tools such as Maya, Max Cinema 4D or Photoshop, all code you create with Visual Studio or your favorite code editor, and any number of content files that Unity creates as you compose scenes, animations and other Unity asset types in the editor.</span></span>

<span data-ttu-id="aefec-124">Per compilare e distribuire app UWP, Unity può esportare il progetto come una soluzione di Visual Studio che conterrà tutti i file di asset e di codice necessari.</span><span class="sxs-lookup"><span data-stu-id="aefec-124">To build and deploy UWP apps, Unity can export the project as a Visual Studio solution that will contain all necessary asset and code files.</span></span>

1. <span data-ttu-id="aefec-125">Avvia Unity</span><span class="sxs-lookup"><span data-stu-id="aefec-125">Start Unity</span></span>
2. <span data-ttu-id="aefec-126">Seleziona **nuovo**</span><span class="sxs-lookup"><span data-stu-id="aefec-126">Select **New**</span></span>
3. <span data-ttu-id="aefec-127">Immettere un nome di progetto (ad esempio "MixedRealityIntroduction")</span><span class="sxs-lookup"><span data-stu-id="aefec-127">Enter a project name (e.g. "MixedRealityIntroduction")</span></span>
4. <span data-ttu-id="aefec-128">Immettere un percorso per salvare il progetto</span><span class="sxs-lookup"><span data-stu-id="aefec-128">Enter a location to save your project</span></span>
5. <span data-ttu-id="aefec-129">Verificare che sia selezionato l'interruttore **3D**</span><span class="sxs-lookup"><span data-stu-id="aefec-129">Ensure the **3D** toggle is selected</span></span>
6. <span data-ttu-id="aefec-130">Selezionare **Crea progetto**</span><span class="sxs-lookup"><span data-stu-id="aefec-130">Select **Create project**</span></span>

<span data-ttu-id="aefec-131">Il programma di installazione consente di iniziare subito a usare le personalizzazioni della realtà mista.</span><span class="sxs-lookup"><span data-stu-id="aefec-131">Congrats, you are all setup to get started with your mixed reality customizations now.</span></span>

## <a name="chapter-2---setup-the-camera"></a><span data-ttu-id="aefec-132">Capitolo 2: configurare la fotocamera</span><span class="sxs-lookup"><span data-stu-id="aefec-132">Chapter 2 - Setup the Camera</span></span>

>[!VIDEO https://www.youtube.com/embed/eP1ZwB4wSNA]

<span data-ttu-id="aefec-133">La videocamera principale di Unity gestisce il rilevamento Head e il rendering stereoscopico.</span><span class="sxs-lookup"><span data-stu-id="aefec-133">The Unity Main Camera handles head tracking and stereoscopic rendering.</span></span> <span data-ttu-id="aefec-134">Ci sono alcune modifiche da apportare alla fotocamera principale per utilizzarlo con realtà mista.</span><span class="sxs-lookup"><span data-stu-id="aefec-134">There are a few changes to make to the Main Camera to use it with mixed reality.</span></span>

1. <span data-ttu-id="aefec-135">Seleziona file > nuova scena</span><span class="sxs-lookup"><span data-stu-id="aefec-135">Select File > New Scene</span></span>

<span data-ttu-id="aefec-136">Per prima cosa, sarà più facile stendere l'app se si immagina la posizione iniziale dell'utente come (**X**: 0, **Y**: 0, **Z**: 0).</span><span class="sxs-lookup"><span data-stu-id="aefec-136">First, it will be easier to lay out your app if you imagine the starting position of the user as (**X**: 0, **Y**: 0, **Z**: 0).</span></span> <span data-ttu-id="aefec-137">Poiché la fotocamera principale tiene traccia del movimento della testa dell'utente, è possibile impostare la posizione iniziale dell'utente impostando la posizione iniziale della fotocamera principale.</span><span class="sxs-lookup"><span data-stu-id="aefec-137">Since the Main Camera is tracking movement of the user's head, the starting position of the user can be set by setting the starting position of the Main Camera.</span></span>

1. <span data-ttu-id="aefec-138">Selezionare la **fotocamera principale** nel pannello **gerarchia**</span><span class="sxs-lookup"><span data-stu-id="aefec-138">Select **Main Camera** in the **Hierarchy** panel</span></span>
2. <span data-ttu-id="aefec-139">Nel pannello **Inspector** trovare il componente **Transform** e modificare la **posizione** da (**x**: 0, **Y**: 1, **Z**:-10) a (**x**: 0, **Y**: 0, **Z**: 0)</span><span class="sxs-lookup"><span data-stu-id="aefec-139">In the **Inspector** panel, find the **Transform** component and change the **Position** from (**X**: 0, **Y**: 1, **Z**: -10) to (**X**: 0, **Y**: 0, **Z**: 0)</span></span>

<span data-ttu-id="aefec-140">In secondo luogo, lo sfondo predefinito della fotocamera richiede un certo pensiero.</span><span class="sxs-lookup"><span data-stu-id="aefec-140">Second, the default Camera background needs some thought.</span></span>

<span data-ttu-id="aefec-141">**Per le applicazioni HoloLens**, il mondo reale dovrebbe comparire dietro tutto il rendering della fotocamera, non una trama skybox.</span><span class="sxs-lookup"><span data-stu-id="aefec-141">**For HoloLens applications**, the real world should appear behind everything the camera renders, not a Skybox texture.</span></span>

1. <span data-ttu-id="aefec-142">Con la **fotocamera principale** ancora selezionata nel pannello **gerarchia** , trovare il componente della **fotocamera** nel pannello **Inspector** e modificare l'elenco a discesa **Clear Flags** da **SKYBOX** a **Solid Color**.</span><span class="sxs-lookup"><span data-stu-id="aefec-142">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and change the **Clear Flags** dropdown from **Skybox** to **Solid Color**.</span></span>
2. <span data-ttu-id="aefec-143">Selezionare la selezione dei colori di **sfondo** e modificare i valori di **RGBA** in (0, 0, 0, 0)</span><span class="sxs-lookup"><span data-stu-id="aefec-143">Select the **Background** color picker and change the **RGBA** values to (0, 0, 0, 0)</span></span>

<span data-ttu-id="aefec-144">**Per le applicazioni di realtà miste destinate a auricolari immersivi**, è possibile usare la trama SKYBOX predefinita fornita da Unity.</span><span class="sxs-lookup"><span data-stu-id="aefec-144">**For mixed reality applications targeted to immersive headsets**, we can use the default Skybox texture that Unity provides.</span></span>

1. <span data-ttu-id="aefec-145">Con la **fotocamera principale** ancora selezionata nel pannello **gerarchia** , trovare il componente della **fotocamera** nel pannello **Inspector** e mantenere l'elenco a discesa **Clear Flags** su **SKYBOX**.</span><span class="sxs-lookup"><span data-stu-id="aefec-145">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and keep the **Clear Flags** dropdown to **Skybox**.</span></span>

<span data-ttu-id="aefec-146">In terzo luogo, consideriamo il piano di ritaglio vicino in Unity, evitando che gli oggetti vengano visualizzati troppo vicino agli occhi degli utenti quando un utente si avvicina a un oggetto o a un oggetto che si avvicina a un utente.</span><span class="sxs-lookup"><span data-stu-id="aefec-146">Third, let us consider the near clip plane in Unity and prevent objects from being rendered too close to the users eyes as a user approaches an object or an object approaches a user.</span></span>

<span data-ttu-id="aefec-147">**Per le applicazioni HoloLens**, il piano di ritaglio vicino può essere impostato su HoloLens 0,85 metri [consigliati](camera-in-unity.md#clip-planes) .</span><span class="sxs-lookup"><span data-stu-id="aefec-147">**For HoloLens applications**, the near clip plane can be set to the [HoloLens recommended](camera-in-unity.md#clip-planes) 0.85 meters.</span></span>

1. <span data-ttu-id="aefec-148">Con la **fotocamera principale** ancora selezionata nel pannello **gerarchia** , trovare il componente della **fotocamera** nel pannello **Inspector** e modificare il campo **near clip Plane** dal valore predefinito **0,3** alla HoloLens consigliata **0,85** .</span><span class="sxs-lookup"><span data-stu-id="aefec-148">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and change the **Near Clip Plane** field from the default **0.3** to the HoloLens recommended **0.85**.</span></span>

<span data-ttu-id="aefec-149">**Per le applicazioni di realtà miste destinate a auricolari immersivi**, è possibile usare l'impostazione predefinita fornita da Unity.</span><span class="sxs-lookup"><span data-stu-id="aefec-149">**For mixed reality applications targeted to immersive headsets**, we can use the default setting that Unity provides.</span></span>

1. <span data-ttu-id="aefec-150">Con la **fotocamera principale** ancora selezionata nel pannello **gerarchia** , trovare il componente della **fotocamera** nel pannello **Inspector** e mantenere il campo del **piano di ritaglio vicino** al valore predefinito **0,3**.</span><span class="sxs-lookup"><span data-stu-id="aefec-150">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and keep the **Near Clip Plane** field to the default **0.3**.</span></span>

<span data-ttu-id="aefec-151">Infine, dobbiamo salvare il nostro progresso fino a questo punto.</span><span class="sxs-lookup"><span data-stu-id="aefec-151">Finally, let us save our progress so far.</span></span> <span data-ttu-id="aefec-152">Per salvare le modifiche apportate alla scena, selezionare **File > Salva scena come**, assegnare un nome alla scena **principale**e selezionare **Salva**.</span><span class="sxs-lookup"><span data-stu-id="aefec-152">To save the scene changes, select **File > Save Scene As**, name the scene **Main**, and select **Save**.</span></span>

## <a name="chapter-3---setup-the-project-settings"></a><span data-ttu-id="aefec-153">Capitolo 3: configurare le impostazioni del progetto</span><span class="sxs-lookup"><span data-stu-id="aefec-153">Chapter 3 - Setup the Project Settings</span></span>

>[!VIDEO https://www.youtube.com/embed/ItRoiXccC0g]

<span data-ttu-id="aefec-154">In questo capitolo vengono impostate alcune impostazioni di progetto Unity che ci aiutano a usare Windows Olografic SDK per lo sviluppo.</span><span class="sxs-lookup"><span data-stu-id="aefec-154">In this chapter, we will set some Unity project settings that help us target the Windows Holographic SDK for development.</span></span> <span data-ttu-id="aefec-155">Vengono inoltre impostate alcune impostazioni di qualità per l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="aefec-155">We will also set some quality settings for our application.</span></span> <span data-ttu-id="aefec-156">Infine, si assicurerà che le destinazioni di compilazione siano impostate su Windows Store.</span><span class="sxs-lookup"><span data-stu-id="aefec-156">Finally, we will ensure our build targets are set to Windows Store.</span></span>

### <a name="unity-performance-and-quality-settings"></a><span data-ttu-id="aefec-157">Impostazioni delle prestazioni e della qualità di Unity</span><span class="sxs-lookup"><span data-stu-id="aefec-157">Unity performance and quality settings</span></span>

<span data-ttu-id="aefec-158">**Impostazioni della qualità di Unity per HoloLens**</span><span class="sxs-lookup"><span data-stu-id="aefec-158">**Unity quality settings for HoloLens**</span></span>

![Impostazioni della qualità di Unity per HoloLens](images/qualitysettings.png)

<span data-ttu-id="aefec-160">Poiché la gestione di un framerate elevato su HoloLens è così importante, è opportuno ottimizzare le impostazioni di qualità per ottenere prestazioni più rapide.</span><span class="sxs-lookup"><span data-stu-id="aefec-160">Since maintaining high framerate on HoloLens is so important, we want the quality settings tuned for fastest performance.</span></span> <span data-ttu-id="aefec-161">Per informazioni più dettagliate sulle prestazioni, [consigli sulle prestazioni per Unity](performance-recommendations-for-unity.md).</span><span class="sxs-lookup"><span data-stu-id="aefec-161">For more detailed performance information, [Performance recommendations for Unity](performance-recommendations-for-unity.md).</span></span>

1. <span data-ttu-id="aefec-162">Selezionare **modifica > impostazioni progetto > qualità**</span><span class="sxs-lookup"><span data-stu-id="aefec-162">Select **Edit > Project Settings > Quality**</span></span>
2. <span data-ttu-id="aefec-163">Selezionare l' **elenco a discesa** sotto il logo di **Windows Store** e selezionare **molto basso**.</span><span class="sxs-lookup"><span data-stu-id="aefec-163">Select the **dropdown** under the **Windows Store** logo and select **Very Low**.</span></span> <span data-ttu-id="aefec-164">Si saprà che l'impostazione viene applicata correttamente quando la casella nella colonna Windows Store e con **una riga molto bassa** è verde.</span><span class="sxs-lookup"><span data-stu-id="aefec-164">You'll know the setting is applied correctly when the box in the Windows Store column and **Very Low** row is green.</span></span>

<span data-ttu-id="aefec-165">**Per le applicazioni di realtà miste destinate a schermi**bloccati, è possibile lasciare le impostazioni di qualità ai valori predefiniti.</span><span class="sxs-lookup"><span data-stu-id="aefec-165">**For mixed reality applications targeted to occluded displays**, you can leave the quality settings to its default values.</span></span>

### <a name="target-windows-10-sdk"></a><span data-ttu-id="aefec-166">Windows 10 SDK di destinazione</span><span class="sxs-lookup"><span data-stu-id="aefec-166">Target Windows 10 SDK</span></span>

<span data-ttu-id="aefec-167">**SDK Windows olografico di destinazione**</span><span class="sxs-lookup"><span data-stu-id="aefec-167">**Target Windows Holographic SDK**</span></span>

![SDK Windows olografico di destinazione](images/xrsettings.png)

<span data-ttu-id="aefec-169">È necessario informare Unity che l'app che si sta tentando di esportare deve creare una [visualizzazione immersiva](app-views.md) anziché una visualizzazione 2D.</span><span class="sxs-lookup"><span data-stu-id="aefec-169">We need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="aefec-170">Questa operazione viene eseguita abilitando il supporto della realtà virtuale in Unity per Windows 10 SDK.</span><span class="sxs-lookup"><span data-stu-id="aefec-170">We do this by enabling Virtual Reality support on Unity targeting the Windows 10 SDK.</span></span>

1. <span data-ttu-id="aefec-171">Passare a **Edit > Settings Project > Player**.</span><span class="sxs-lookup"><span data-stu-id="aefec-171">Go to **Edit > Project Settings > Player**.</span></span>
2. <span data-ttu-id="aefec-172">Nel **pannello Inspector** per le impostazioni del lettore selezionare l'icona di **Windows Store** .</span><span class="sxs-lookup"><span data-stu-id="aefec-172">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="aefec-173">Espandere il gruppo di **Impostazioni XR** .</span><span class="sxs-lookup"><span data-stu-id="aefec-173">Expand the **XR Settings** group.</span></span>
4. <span data-ttu-id="aefec-174">Nella sezione **rendering** selezionare la casella di controllo **realtà virtuale supportata** per aggiungere un nuovo elenco **SDK di realtà virtuale** .</span><span class="sxs-lookup"><span data-stu-id="aefec-174">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality SDKs** list.</span></span>
5. <span data-ttu-id="aefec-175">Verificare che l'opzione **realtà mista di Windows** sia presente nell'elenco.</span><span class="sxs-lookup"><span data-stu-id="aefec-175">Verify that **Windows Mixed Reality** appears in the list.</span></span> <span data-ttu-id="aefec-176">In caso contrario, selezionare il pulsante **+** nella parte inferiore dell'elenco e scegliere **realtà mista di Windows**.</span><span class="sxs-lookup"><span data-stu-id="aefec-176">If not, select the **+** button at the bottom of the list and choose **Windows Mixed Reality**.</span></span>

>[!NOTE]
><span data-ttu-id="aefec-177">Se l'icona di **Windows Store** non è visualizzata, verificare di aver selezionato il back-end di scripting .NET di Windows Store prima di procedere all'installazione.</span><span class="sxs-lookup"><span data-stu-id="aefec-177">If you do not see the **Windows Store** icon, double check to make sure you selected the Windows Store .NET Scripting Backend prior to installation.</span></span> <span data-ttu-id="aefec-178">In caso contrario, potrebbe essere necessario reinstallare Unity con l'installazione di Windows corretta.</span><span class="sxs-lookup"><span data-stu-id="aefec-178">If not, you may need to reinstall Unity with the correct Windows installation.</span></span>

<span data-ttu-id="aefec-179">**Verificare la configurazione .NET**</span><span class="sxs-lookup"><span data-stu-id="aefec-179">**Verify .NET Configuration**</span></span>

![Verificare la configurazione .NET](images/configoptions-375px.png)

1. <span data-ttu-id="aefec-181">Passare a **Edit > Settings (Impostazioni progetto) > Player** (è possibile continuare a eseguire questa operazione dal passaggio precedente).</span><span class="sxs-lookup"><span data-stu-id="aefec-181">Go to **Edit > Project Settings > Player** (you may still have this up from the previous step).</span></span>
2. <span data-ttu-id="aefec-182">Nel **pannello Inspector** per le impostazioni del lettore selezionare l'icona di **Windows Store** .</span><span class="sxs-lookup"><span data-stu-id="aefec-182">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="aefec-183">Nella sezione **altre impostazioni** di configurazione, assicurarsi che **lo scripting backend** sia impostato su **.NET** .</span><span class="sxs-lookup"><span data-stu-id="aefec-183">In the **Other Settings** Configuration section, make sure that **Scripting Backend** is set to **.NET**</span></span>

<span data-ttu-id="aefec-184">Un processo straordinario per il recupero di tutte le impostazioni del progetto applicate.</span><span class="sxs-lookup"><span data-stu-id="aefec-184">Awesome job on getting all the project settings applied.</span></span> <span data-ttu-id="aefec-185">Quindi, aggiungiamo un ologramma!</span><span class="sxs-lookup"><span data-stu-id="aefec-185">Next, let us add a hologram!</span></span>

## <a name="chapter-4---create-a-cube"></a><span data-ttu-id="aefec-186">Capitolo 4-creazione di un cubo</span><span class="sxs-lookup"><span data-stu-id="aefec-186">Chapter 4 - Create a cube</span></span>

>[!VIDEO https://www.youtube.com/embed/qKcK1Yuj-HQ]

<span data-ttu-id="aefec-187">La creazione di un cubo nel progetto Unity è simile alla creazione di qualsiasi altro oggetto in Unity.</span><span class="sxs-lookup"><span data-stu-id="aefec-187">Creating a cube in your Unity project is just like creating any other object in Unity.</span></span> <span data-ttu-id="aefec-188">Posizionare un cubo davanti all'utente è facile perché il sistema di coordinate di Unity è mappato al mondo reale, in cui un contatore in Unity è approssimativamente un contatore nel mondo reale.</span><span class="sxs-lookup"><span data-stu-id="aefec-188">Placing a cube in front of the user is easy because Unity's coordinate system is mapped to the real world - where one meter in Unity is approximately one meter in the real world.</span></span>

1. <span data-ttu-id="aefec-189">Nell'angolo in alto a sinistra del pannello **gerarchia** selezionare l'elenco a discesa **Crea** e scegliere **oggetto 3D > cubo**.</span><span class="sxs-lookup"><span data-stu-id="aefec-189">In the top left corner of the **Hierarchy** panel, select the **Create** dropdown and choose **3D Object > Cube**.</span></span>
2. <span data-ttu-id="aefec-190">Selezionare il **cubo** appena creato nel pannello **gerarchia**</span><span class="sxs-lookup"><span data-stu-id="aefec-190">Select the newly created **Cube** in the **Hierarchy** panel</span></span>
3. <span data-ttu-id="aefec-191">Nel **controllo** trovare il componente **Transform** e modificare **position** in (**X**: 0, **Y**: 0, **Z**: 2).</span><span class="sxs-lookup"><span data-stu-id="aefec-191">In the **Inspector** find the **Transform** component and change **Position** to (**X**: 0, **Y**: 0, **Z**: 2).</span></span> <span data-ttu-id="aefec-192">*Questa operazione posiziona il cubo 2 metri davanti alla posizione iniziale dell'utente.*</span><span class="sxs-lookup"><span data-stu-id="aefec-192">*This positions the cube 2 meters in front of the user's starting position.*</span></span>
4. <span data-ttu-id="aefec-193">Nel componente **trasformazione** modificare la **rotazione** in (**x**: 45, **Y**: 45, **Z**: 45) e modificare la **scala** in (**X**: 0,25, **Y**: 0,25, **Z**: 0,25).</span><span class="sxs-lookup"><span data-stu-id="aefec-193">In the **Transform** component, change **Rotation** to (**X**: 45, **Y**: 45, **Z**: 45) and change **Scale** to (**X**: 0.25, **Y**: 0.25, **Z**: 0.25).</span></span> <span data-ttu-id="aefec-194">*Questa operazione consente di ridimensionare il cubo a 0,25 metri.*</span><span class="sxs-lookup"><span data-stu-id="aefec-194">*This scales the cube to 0.25 meters.*</span></span>
5. <span data-ttu-id="aefec-195">Per salvare le modifiche apportate alla scena, selezionare **File > Salva scena**.</span><span class="sxs-lookup"><span data-stu-id="aefec-195">To save the scene changes, select **File > Save Scene**.</span></span>

## <a name="chapter-5---verify-on-device-from-unity-editor"></a><span data-ttu-id="aefec-196">Capitolo 5-verificare nel dispositivo dall'editor Unity</span><span class="sxs-lookup"><span data-stu-id="aefec-196">Chapter 5 - Verify on device from Unity editor</span></span>

>[!VIDEO https://www.youtube.com/embed/vmCfiIdRb6Q]

<span data-ttu-id="aefec-197">A questo punto, dopo aver creato il cubo, è possibile eseguire un controllo rapido nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="aefec-197">Now that we have created our cube, it is time to do a quick check in device.</span></span> <span data-ttu-id="aefec-198">Questa operazione può essere eseguita direttamente dall'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="aefec-198">You can do this directly from within the Unity editor.</span></span>

### <a name="initial-setup"></a><span data-ttu-id="aefec-199">Configurazione iniziale</span><span class="sxs-lookup"><span data-stu-id="aefec-199">Initial setup</span></span>

1. <span data-ttu-id="aefec-200">Nel computer di sviluppo, in Unity, aprire **File > finestra impostazioni di compilazione** .</span><span class="sxs-lookup"><span data-stu-id="aefec-200">On your development PC, in Unity, open **File > Build Settings** window.</span></span>
2. <span data-ttu-id="aefec-201">Modificare la **piattaforma** in **piattaforma UWP (Universal Windows Platform)** e fare clic su **Cambia platfrom**</span><span class="sxs-lookup"><span data-stu-id="aefec-201">Change **Platform** to **Universal Windows Platform** and click **Switch Platfrom**</span></span>

### <a name="for-hololens-use-unity-remoting"></a><span data-ttu-id="aefec-202">Per HoloLens usare la comunicazione remota di Unity</span><span class="sxs-lookup"><span data-stu-id="aefec-202">For HoloLens use Unity Remoting</span></span>

1. <span data-ttu-id="aefec-203">In HoloLens installare ed eseguire il lettore di [comunicazione remota olografico](holographic-remoting-player.md), disponibile in Windows Store.</span><span class="sxs-lookup"><span data-stu-id="aefec-203">On your HoloLens, install and run the [Holographic Remoting Player](holographic-remoting-player.md), available from the Windows Store.</span></span> <span data-ttu-id="aefec-204">Avviare l'applicazione nel dispositivo, che entrerà in uno stato di attesa e visualizzerà l'indirizzo IP del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="aefec-204">Launch the application on the device, and it will enter a waiting state and show the IP address of the device.</span></span> <span data-ttu-id="aefec-205">Prendere nota dell'indirizzo IP.</span><span class="sxs-lookup"><span data-stu-id="aefec-205">Note down the IP.</span></span>
2. <span data-ttu-id="aefec-206">Aprire la **finestra > XR > emulazione olografica**.</span><span class="sxs-lookup"><span data-stu-id="aefec-206">Open **Window > XR > Holographic Emulation**.</span></span>
3. <span data-ttu-id="aefec-207">Modificare la **modalità di emulazione** da **Nessuna** a **remota a dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="aefec-207">Change **Emulation Mode** from **None** to **Remote to Device**.</span></span>
4. <span data-ttu-id="aefec-208">In **computer remoto**, immettere l'indirizzo IP della HoloLens annotata in precedenza.</span><span class="sxs-lookup"><span data-stu-id="aefec-208">In **Remote Machine**, enter the IP address of your HoloLens noted earlier.</span></span>
5. <span data-ttu-id="aefec-209">Fai clic su **Connetti**.</span><span class="sxs-lookup"><span data-stu-id="aefec-209">Click **Connect**.</span></span>
6. <span data-ttu-id="aefec-210">Verificare che lo **stato della connessione** venga modificato in verde **connesso**.</span><span class="sxs-lookup"><span data-stu-id="aefec-210">Ensure the **Connection Status** changes to green **Connected**.</span></span>
7. <span data-ttu-id="aefec-211">A questo punto è possibile fare clic su **Play** nell'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="aefec-211">Now you can now click **Play** in the Unity editor.</span></span>

<span data-ttu-id="aefec-212">A questo punto sarà possibile visualizzare il cubo nel dispositivo e nell'editor.</span><span class="sxs-lookup"><span data-stu-id="aefec-212">You will now be able to see the cube in device and in the editor.</span></span> <span data-ttu-id="aefec-213">È possibile sospendere, ispezionare gli oggetti ed eseguire il debug in modo analogo all'esecuzione di un'app nell'editor, perché si tratta essenzialmente di ciò che accade, ma con video, audio e input del dispositivo trasmessi attraverso la rete tra il computer host e il dispositivo.</span><span class="sxs-lookup"><span data-stu-id="aefec-213">You can pause, inspect objects, and debug just like you are running an app in the editor, because that’s essentially what’s happening, but with video, audio, and device input transmitted back and forth across the network between the host machine and the device.</span></span>

### <a name="for-other-mixed-reality-supported-headsets"></a><span data-ttu-id="aefec-214">Per gli altri tipi di auricolari supportati dalla realtà mista</span><span class="sxs-lookup"><span data-stu-id="aefec-214">For other mixed reality supported headsets</span></span>

1. <span data-ttu-id="aefec-215">Connettere la cuffia al PC di sviluppo usando il cavo USB e il cavo porta HDMI o schermo.</span><span class="sxs-lookup"><span data-stu-id="aefec-215">Connect the headset to your development PC using the USB cable and the HDMI or display port cable.</span></span>
2. <span data-ttu-id="aefec-216">Avviare il **portale di realtà mista** e assicurarsi di avere completato la prima esperienza di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="aefec-216">Launch the **Mixed Reality Portal** and ensure you have completed the first run experience.</span></span>
3. <span data-ttu-id="aefec-217">Da Unity è ora possibile premere il pulsante Play.</span><span class="sxs-lookup"><span data-stu-id="aefec-217">From Unity, you can now press the Play button.</span></span>

<span data-ttu-id="aefec-218">A questo punto, sarà possibile visualizzare il rendering dei cubi nell'auricolare della realtà mista e nell'editor.</span><span class="sxs-lookup"><span data-stu-id="aefec-218">You will now be able to see the cube rendering in your mixed reality headset and in the editor.</span></span>

## <a name="chapter-6---build-and-deploy-to-device-from-visual-studio"></a><span data-ttu-id="aefec-219">Capitolo 6: creare e distribuire nel dispositivo da Visual Studio</span><span class="sxs-lookup"><span data-stu-id="aefec-219">Chapter 6 - Build and deploy to device from Visual Studio</span></span>

>[!VIDEO https://www.youtube.com/embed/USSu8yHUdbk]

<span data-ttu-id="aefec-220">A questo punto è possibile compilare il progetto in Visual Studio e distribuirlo nel dispositivo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="aefec-220">We are now ready to compile our project to Visual Studio and deploy to our target device.</span></span>

### <a name="export-to-the-visual-studio-solution"></a><span data-ttu-id="aefec-221">Esporta nella soluzione di Visual Studio</span><span class="sxs-lookup"><span data-stu-id="aefec-221">Export to the Visual Studio solution</span></span>

1.  <span data-ttu-id="aefec-222">Aprire **File > finestra impostazioni di compilazione** .</span><span class="sxs-lookup"><span data-stu-id="aefec-222">Open **File > Build Settings** window.</span></span>
2.  <span data-ttu-id="aefec-223">Fare clic su **Aggiungi scene aperte** per aggiungere la scena.</span><span class="sxs-lookup"><span data-stu-id="aefec-223">Click **Add Open Scenes** to add the scene.</span></span>
3.  <span data-ttu-id="aefec-224">Modificare la **piattaforma** in **piattaforma UWP (Universal Windows Platform)** e fare clic su **Cambia piattaforma**.</span><span class="sxs-lookup"><span data-stu-id="aefec-224">Change **Platform** to **Universal Windows Platform** and click **Switch Platform**.</span></span>
4.  <span data-ttu-id="aefec-225">Nelle impostazioni di **Windows Store** assicurarsi che **SDK** sia **universale 10**.</span><span class="sxs-lookup"><span data-stu-id="aefec-225">In **Windows Store** settings ensure, **SDK** is **Universal 10**.</span></span>
5.  <span data-ttu-id="aefec-226">Per il dispositivo di destinazione, lasciare a **qualsiasi dispositivo** per visualizzare le schermate o passare a **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="aefec-226">For Target device, leave to **Any Device** for occluded displays or switch to **HoloLens**.</span></span>
6.  <span data-ttu-id="aefec-227">Il **tipo di compilazione UWP** deve essere **D3D**.</span><span class="sxs-lookup"><span data-stu-id="aefec-227">**UWP Build Type** should be **D3D**.</span></span>
7.  <span data-ttu-id="aefec-228">L' **SDK di UWP** potrebbe essere rimasto **installato più di recente**.</span><span class="sxs-lookup"><span data-stu-id="aefec-228">**UWP SDK** could be left at **Latest installed**.</span></span>
8.  <span data-ttu-id="aefec-229">Controllare **i C# progetti Unity** in fase di debug.</span><span class="sxs-lookup"><span data-stu-id="aefec-229">Check **Unity C# Projects** under Debugging.</span></span>
9.  <span data-ttu-id="aefec-230">Fai clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="aefec-230">Click **Build**.</span></span>
10. <span data-ttu-id="aefec-231">In Esplora file fare clic su **nuova cartella** e denominare la cartella **"app"** .</span><span class="sxs-lookup"><span data-stu-id="aefec-231">In the file explorer, click **New Folder** and name the folder **"App"**.</span></span>
11. <span data-ttu-id="aefec-232">Con la cartella **app** selezionata, fare clic sul pulsante **Seleziona cartella** .</span><span class="sxs-lookup"><span data-stu-id="aefec-232">With the **App** folder selected, click the **Select Folder** button.</span></span>
12. <span data-ttu-id="aefec-233">Al termine della compilazione di Unity, viene visualizzata una finestra Esplora file di Windows.</span><span class="sxs-lookup"><span data-stu-id="aefec-233">When Unity is done building, a Windows File Explorer window will appear.</span></span>
13. <span data-ttu-id="aefec-234">Aprire la cartella dell' **app** in Esplora file.</span><span class="sxs-lookup"><span data-stu-id="aefec-234">Open the **App** folder in file explorer.</span></span>
14. <span data-ttu-id="aefec-235">Aprire la soluzione di Visual Studio generata (MixedRealityIntroduction. sln in questo esempio)</span><span class="sxs-lookup"><span data-stu-id="aefec-235">Open the generated Visual Studio solution (MixedRealityIntroduction.sln in this example)</span></span>

### <a name="compile-the-visual-studio-solution"></a><span data-ttu-id="aefec-236">Compilare la soluzione di Visual Studio</span><span class="sxs-lookup"><span data-stu-id="aefec-236">Compile the Visual Studio solution</span></span>

<span data-ttu-id="aefec-237">Infine, la soluzione di Visual Studio esportata verrà compilata, distribuita e provata nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="aefec-237">Finally, we will compile the exported Visual Studio solution, deploy it, and try it out on the device.</span></span>

1. <span data-ttu-id="aefec-238">Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione da **debug** a **Release** e da **ARM** a **x86**.</span><span class="sxs-lookup"><span data-stu-id="aefec-238">Using the top toolbar in Visual Studio, change the target from **Debug** to **Release** and from **ARM** to **X86**.</span></span>

<span data-ttu-id="aefec-239">Le istruzioni sono diverse per la distribuzione in un dispositivo rispetto all'emulatore.</span><span class="sxs-lookup"><span data-stu-id="aefec-239">The instructions differ for deploying to a device versus the emulator.</span></span> <span data-ttu-id="aefec-240">Seguire le istruzioni corrispondenti alla configurazione.</span><span class="sxs-lookup"><span data-stu-id="aefec-240">Follow the instructions that match your setup.</span></span>

### <a name="deploy-to-mixed-reality-device-over-wi-fi"></a><span data-ttu-id="aefec-241">Eseguire la distribuzione in un dispositivo a realtà mista tramite Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="aefec-241">Deploy to mixed reality device over Wi-Fi</span></span>

1. <span data-ttu-id="aefec-242">Fare clic sulla freccia accanto al pulsante **locale del computer** e modificare la destinazione di distribuzione in **computer remoto**.</span><span class="sxs-lookup"><span data-stu-id="aefec-242">Click on the arrow next to the **Local Machine** button, and change the deployment target to **Remote Machine**.</span></span>
2. <span data-ttu-id="aefec-243">Immettere l'indirizzo IP del dispositivo in realtà mista e modificare la **modalità di autenticazione** in Universal (protocollo non crittografato) per HoloLens e **Windows** per altri dispositivi.</span><span class="sxs-lookup"><span data-stu-id="aefec-243">Enter the IP address of your mixed reality device and change **Authentication Mode** to Universal (Unencrypted Protocol) for HoloLens and **Windows** for other devices.</span></span>
3. <span data-ttu-id="aefec-244">Fare clic su **debug > avvia senza eseguire debug**.</span><span class="sxs-lookup"><span data-stu-id="aefec-244">Click **Debug > Start without debugging**.</span></span>

<span data-ttu-id="aefec-245">**Per HoloLens**, se questa è la prima volta che si esegue la distribuzione nel dispositivo, sarà necessario eseguire l'associazione [con Visual Studio](using-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="aefec-245">**For HoloLens**, If this is the first time deploying to your device, you will need to pair [using Visual Studio](using-visual-studio.md).</span></span>

### <a name="deploy-to-mixed-reality-device-over-usb"></a><span data-ttu-id="aefec-246">Distribuisci in un dispositivo a realtà mista tramite USB</span><span class="sxs-lookup"><span data-stu-id="aefec-246">Deploy to mixed reality device over USB</span></span>

<span data-ttu-id="aefec-247">Verificare che il dispositivo sia collegato tramite il cavo USB.</span><span class="sxs-lookup"><span data-stu-id="aefec-247">Ensure you device is plugged in via the USB cable.</span></span>

1. <span data-ttu-id="aefec-248">**Per HoloLens**, fare clic sulla freccia accanto al pulsante **locale del computer** e modificare la destinazione di distribuzione nel **dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="aefec-248">**For HoloLens**, click on the arrow next to the **Local Machine** button, and change the deployment target to **Device**.</span></span>
2. <span data-ttu-id="aefec-249">**Per individuare i dispositivi bloccati collegati al PC**, impostare il computer locale.</span><span class="sxs-lookup"><span data-stu-id="aefec-249">**For targeting occluded devices attached to your PC**, keep the setting to Local Machine.</span></span> <span data-ttu-id="aefec-250">Assicurarsi che sia in esecuzione il **portale di realtà mista** .</span><span class="sxs-lookup"><span data-stu-id="aefec-250">Ensure you have the **Mixed Reality Portal** running.</span></span>
3. <span data-ttu-id="aefec-251">Fare clic su **debug > avvia senza eseguire debug**.</span><span class="sxs-lookup"><span data-stu-id="aefec-251">Click **Debug > Start without debugging**.</span></span>

### <a name="deploy-to-emulator"></a><span data-ttu-id="aefec-252">Distribuisci nell'emulatore</span><span class="sxs-lookup"><span data-stu-id="aefec-252">Deploy to Emulator</span></span>

1. <span data-ttu-id="aefec-253">Fare clic sulla freccia accanto al pulsante **Device (dispositivo** ) e nell'elenco a discesa selezionare **HoloLens Emulator (emulatore**).</span><span class="sxs-lookup"><span data-stu-id="aefec-253">Click on the arrow next to the **Device** button, and from drop down select **HoloLens Emulator**.</span></span>
2. <span data-ttu-id="aefec-254">Fare clic su **debug > avvia senza eseguire debug**.</span><span class="sxs-lookup"><span data-stu-id="aefec-254">Click **Debug > Start without debugging**.</span></span>

### <a name="try-out-your-app"></a><span data-ttu-id="aefec-255">Provare l'app</span><span class="sxs-lookup"><span data-stu-id="aefec-255">Try out your app</span></span>

<span data-ttu-id="aefec-256">Ora che l'app è stata distribuita, provare a spostarsi in tutto il cubo e osservare che rimane nel mondo davanti all'utente.</span><span class="sxs-lookup"><span data-stu-id="aefec-256">Now that your app is deployed, try moving all around the cube and observe that it stays in the world in front of you.</span></span>

## <a name="see-also"></a><span data-ttu-id="aefec-257">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="aefec-257">See also</span></span>

* [<span data-ttu-id="aefec-258">Panoramica dello sviluppo per Unity</span><span class="sxs-lookup"><span data-stu-id="aefec-258">Unity development overview</span></span>](unity-development-overview.md)
* [<span data-ttu-id="aefec-259">Procedure consigliate per l'uso con Unity e Visual Studio</span><span class="sxs-lookup"><span data-stu-id="aefec-259">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)
* [<span data-ttu-id="aefec-260">Nozioni fondamentali 101</span><span class="sxs-lookup"><span data-stu-id="aefec-260">MR Basics 101</span></span>](holograms-101.md)
* [<span data-ttu-id="aefec-261">Nozioni di base su 101E</span><span class="sxs-lookup"><span data-stu-id="aefec-261">MR Basics 101E</span></span>](holograms-101e.md)

---
title: Nozioni fondamentali 100-Introduzione a Unity
description: Informazioni su come creare la prima applicazione "Hello World" di base per la realtà mista.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: realtà mista, realtà mista di Windows, HoloLens, immersiva, VR, Mr, introduzione, ologramma, Accademia, esercitazione
ms.openlocfilehash: 58a1785ef74872c633cf65d6a32e24d517367359
ms.sourcegitcommit: f523b74a549721b6bec69cb5d2eca5b7673a793c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85570308"
---
# <a name="mr-basics-100-getting-started-with-unity"></a><span data-ttu-id="43fa4-104">Nozioni di base MR 100: Introduzione a Unity</span><span class="sxs-lookup"><span data-stu-id="43fa4-104">MR Basics 100: Getting started with Unity</span></span>

>[!IMPORTANT]
><span data-ttu-id="43fa4-105">Le esercitazioni di Mixed Reality Academy sono state progettate in base a HoloLens (prima generazione) e ai visori VR immersive di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="43fa4-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="43fa4-106">Pertanto, riteniamo importante lasciarle a disposizione degli sviluppatori a cui serve ancora materiale sussidiario per lo sviluppo di questi dispositivi.</span><span class="sxs-lookup"><span data-stu-id="43fa4-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="43fa4-107">Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="43fa4-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="43fa4-108">Rimarranno invariate per consentire di continuare a lavorare sui dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="43fa4-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="43fa4-109">Per HoloLens 2 è stata pubblicata [una nuova serie di esercitazioni](mrlearning-base.md).</span><span class="sxs-lookup"><span data-stu-id="43fa4-109">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<span data-ttu-id="43fa4-110">Questa esercitazione illustra come creare un'app di base per realtà mista compilata con Unity.</span><span class="sxs-lookup"><span data-stu-id="43fa4-110">This tutorial will walk you through creating a basic mixed reality app built with Unity.</span></span>

## <a name="device-support"></a><span data-ttu-id="43fa4-111">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="43fa4-111">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="43fa4-112">Corso</span><span class="sxs-lookup"><span data-stu-id="43fa4-112">Course</span></span></th><th style="width:150px"> <span data-ttu-id="43fa4-113"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="43fa4-113"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="43fa4-114"><a href="immersive-headset-hardware-details.md">Visori VR immersive</a></span><span class="sxs-lookup"><span data-stu-id="43fa4-114"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="43fa4-115">Nozioni di base MR 100: Introduzione a Unity</span><span class="sxs-lookup"><span data-stu-id="43fa4-115">MR Basics 100: Getting started with Unity</span></span></td><td style="text-align: center;"> <span data-ttu-id="43fa4-116">✔️</span><span class="sxs-lookup"><span data-stu-id="43fa4-116">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="43fa4-117">✔️</span><span class="sxs-lookup"><span data-stu-id="43fa4-117">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="43fa4-118">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="43fa4-118">Prerequisites</span></span>

* <span data-ttu-id="43fa4-119">Un PC Windows 10 configurato con gli [strumenti corretti installati](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="43fa4-119">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>

## <a name="chapter-1---create-a-new-project"></a><span data-ttu-id="43fa4-120">Capitolo 1-creare un nuovo progetto</span><span class="sxs-lookup"><span data-stu-id="43fa4-120">Chapter 1 - Create a New Project</span></span>

>[!VIDEO https://www.youtube.com/embed/2L5IFO0hnYA]

<span data-ttu-id="43fa4-121">Per compilare un'app con Unity, è prima di tutto necessario creare un progetto.</span><span class="sxs-lookup"><span data-stu-id="43fa4-121">To build an app with Unity, you first need to create a project.</span></span> <span data-ttu-id="43fa4-122">Questo progetto è organizzato in alcune cartelle, il più importante dei quali è la cartella assets.</span><span class="sxs-lookup"><span data-stu-id="43fa4-122">This project is organized into a few folders, the most important of which is your Assets folder.</span></span> <span data-ttu-id="43fa4-123">Si tratta della cartella che include tutte le risorse importate dagli strumenti di creazione di contenuti digitali, ad esempio Maya, max cinema 4D o Photoshop, tutto il codice creato con Visual Studio o l'editor di codice preferito e un numero qualsiasi di file di contenuto creati da Unity durante la composizione di scene, animazioni e altri tipi di asset Unity nell'editor.</span><span class="sxs-lookup"><span data-stu-id="43fa4-123">This is the folder that holds all assets you import from digital content creation tools such as Maya, Max Cinema 4D or Photoshop, all code you create with Visual Studio or your favorite code editor, and any number of content files that Unity creates as you compose scenes, animations and other Unity asset types in the editor.</span></span>

<span data-ttu-id="43fa4-124">Per compilare e distribuire app UWP, Unity può esportare il progetto come una soluzione di Visual Studio che conterrà tutti i file di asset e di codice necessari.</span><span class="sxs-lookup"><span data-stu-id="43fa4-124">To build and deploy UWP apps, Unity can export the project as a Visual Studio solution that will contain all necessary asset and code files.</span></span>

1. <span data-ttu-id="43fa4-125">Avvia Unity</span><span class="sxs-lookup"><span data-stu-id="43fa4-125">Start Unity</span></span>
2. <span data-ttu-id="43fa4-126">Seleziona **nuovo**</span><span class="sxs-lookup"><span data-stu-id="43fa4-126">Select **New**</span></span>
3. <span data-ttu-id="43fa4-127">Immettere un nome di progetto (ad esempio "MixedRealityIntroduction")</span><span class="sxs-lookup"><span data-stu-id="43fa4-127">Enter a project name (e.g. "MixedRealityIntroduction")</span></span>
4. <span data-ttu-id="43fa4-128">Immettere un percorso per salvare il progetto</span><span class="sxs-lookup"><span data-stu-id="43fa4-128">Enter a location to save your project</span></span>
5. <span data-ttu-id="43fa4-129">Verificare che sia selezionato l'interruttore **3D**</span><span class="sxs-lookup"><span data-stu-id="43fa4-129">Ensure the **3D** toggle is selected</span></span>
6. <span data-ttu-id="43fa4-130">Selezionare **Crea progetto**</span><span class="sxs-lookup"><span data-stu-id="43fa4-130">Select **Create project**</span></span>

<span data-ttu-id="43fa4-131">Il programma di installazione consente di iniziare subito a usare le personalizzazioni della realtà mista.</span><span class="sxs-lookup"><span data-stu-id="43fa4-131">Congrats, you are all setup to get started with your mixed reality customizations now.</span></span>

## <a name="chapter-2---setup-the-camera"></a><span data-ttu-id="43fa4-132">Capitolo 2: configurare la fotocamera</span><span class="sxs-lookup"><span data-stu-id="43fa4-132">Chapter 2 - Setup the Camera</span></span>

>[!VIDEO https://www.youtube.com/embed/eP1ZwB4wSNA]

<span data-ttu-id="43fa4-133">La videocamera principale di Unity gestisce il rilevamento Head e il rendering stereoscopico.</span><span class="sxs-lookup"><span data-stu-id="43fa4-133">The Unity Main Camera handles head tracking and stereoscopic rendering.</span></span> <span data-ttu-id="43fa4-134">Ci sono alcune modifiche da apportare alla fotocamera principale per utilizzarlo con realtà mista.</span><span class="sxs-lookup"><span data-stu-id="43fa4-134">There are a few changes to make to the Main Camera to use it with mixed reality.</span></span>

1. <span data-ttu-id="43fa4-135">Seleziona file > nuova scena</span><span class="sxs-lookup"><span data-stu-id="43fa4-135">Select File > New Scene</span></span>

<span data-ttu-id="43fa4-136">Per prima cosa, sarà più facile stendere l'app se si immagina la posizione iniziale dell'utente come (**X**: 0, **Y**: 0, **Z**: 0).</span><span class="sxs-lookup"><span data-stu-id="43fa4-136">First, it will be easier to lay out your app if you imagine the starting position of the user as (**X**: 0, **Y**: 0, **Z**: 0).</span></span> <span data-ttu-id="43fa4-137">Poiché la fotocamera principale tiene traccia del movimento della testa dell'utente, è possibile impostare la posizione iniziale dell'utente impostando la posizione iniziale della fotocamera principale.</span><span class="sxs-lookup"><span data-stu-id="43fa4-137">Since the Main Camera is tracking movement of the user's head, the starting position of the user can be set by setting the starting position of the Main Camera.</span></span>

1. <span data-ttu-id="43fa4-138">Selezionare la **fotocamera principale** nel pannello **gerarchia**</span><span class="sxs-lookup"><span data-stu-id="43fa4-138">Select **Main Camera** in the **Hierarchy** panel</span></span>
2. <span data-ttu-id="43fa4-139">Nel pannello **Inspector** trovare il componente **Transform** e modificare la **posizione** da (**x**: 0, **Y**: 1, **Z**:-10) a (**x**: 0, **Y**: 0, **Z**: 0)</span><span class="sxs-lookup"><span data-stu-id="43fa4-139">In the **Inspector** panel, find the **Transform** component and change the **Position** from (**X**: 0, **Y**: 1, **Z**: -10) to (**X**: 0, **Y**: 0, **Z**: 0)</span></span>

<span data-ttu-id="43fa4-140">In secondo luogo, lo sfondo predefinito della fotocamera richiede un certo pensiero.</span><span class="sxs-lookup"><span data-stu-id="43fa4-140">Second, the default Camera background needs some thought.</span></span>

<span data-ttu-id="43fa4-141">**Per le applicazioni HoloLens**, il mondo reale dovrebbe comparire dietro tutto il rendering della fotocamera, non una trama skybox.</span><span class="sxs-lookup"><span data-stu-id="43fa4-141">**For HoloLens applications**, the real world should appear behind everything the camera renders, not a Skybox texture.</span></span>

1. <span data-ttu-id="43fa4-142">Con la **fotocamera principale** ancora selezionata nel pannello **gerarchia** , trovare il componente della **fotocamera** nel pannello **Inspector** e modificare l'elenco a discesa **Clear Flags** da **SKYBOX** a **Solid Color**.</span><span class="sxs-lookup"><span data-stu-id="43fa4-142">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and change the **Clear Flags** dropdown from **Skybox** to **Solid Color**.</span></span>
2. <span data-ttu-id="43fa4-143">Selezionare la selezione dei colori di **sfondo** e modificare i valori di **RGBA** in (0, 0, 0, 0)</span><span class="sxs-lookup"><span data-stu-id="43fa4-143">Select the **Background** color picker and change the **RGBA** values to (0, 0, 0, 0)</span></span>

<span data-ttu-id="43fa4-144">**Per le applicazioni di realtà miste destinate a auricolari immersivi**, è possibile usare la trama SKYBOX predefinita fornita da Unity.</span><span class="sxs-lookup"><span data-stu-id="43fa4-144">**For mixed reality applications targeted to immersive headsets**, we can use the default Skybox texture that Unity provides.</span></span>

1. <span data-ttu-id="43fa4-145">Con la **fotocamera principale** ancora selezionata nel pannello **gerarchia** , trovare il componente della **fotocamera** nel pannello **Inspector** e mantenere l'elenco a discesa **Clear Flags** su **SKYBOX**.</span><span class="sxs-lookup"><span data-stu-id="43fa4-145">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and keep the **Clear Flags** dropdown to **Skybox**.</span></span>

<span data-ttu-id="43fa4-146">In terzo luogo, consideriamo il piano di ritaglio vicino in Unity, evitando che gli oggetti vengano visualizzati troppo vicino agli occhi degli utenti quando un utente si avvicina a un oggetto o a un oggetto che si avvicina a un utente.</span><span class="sxs-lookup"><span data-stu-id="43fa4-146">Third, let us consider the near clip plane in Unity and prevent objects from being rendered too close to the users eyes as a user approaches an object or an object approaches a user.</span></span>

<span data-ttu-id="43fa4-147">**Per le applicazioni HoloLens**, il piano di ritaglio vicino può essere impostato su HoloLens 0,85 metri [consigliati](camera-in-unity.md#clip-planes) .</span><span class="sxs-lookup"><span data-stu-id="43fa4-147">**For HoloLens applications**, the near clip plane can be set to the [HoloLens recommended](camera-in-unity.md#clip-planes) 0.85 meters.</span></span>

1. <span data-ttu-id="43fa4-148">Con la **fotocamera principale** ancora selezionata nel pannello **gerarchia** , trovare il componente della **fotocamera** nel pannello **Inspector** e modificare il campo **near Clip Plane** dal valore predefinito **0,3** a HoloLens consigliato **0,85**.</span><span class="sxs-lookup"><span data-stu-id="43fa4-148">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and change the **Near Clip Plane** field from the default **0.3** to the HoloLens recommended **0.85**.</span></span>

<span data-ttu-id="43fa4-149">**Per le applicazioni di realtà miste destinate a auricolari immersivi**, è possibile usare l'impostazione predefinita fornita da Unity.</span><span class="sxs-lookup"><span data-stu-id="43fa4-149">**For mixed reality applications targeted to immersive headsets**, we can use the default setting that Unity provides.</span></span>

1. <span data-ttu-id="43fa4-150">Con la **fotocamera principale** ancora selezionata nel pannello **gerarchia** , trovare il componente della **fotocamera** nel pannello **Inspector** e mantenere il campo del **piano di ritaglio vicino** al valore predefinito **0,3**.</span><span class="sxs-lookup"><span data-stu-id="43fa4-150">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and keep the **Near Clip Plane** field to the default **0.3**.</span></span>

<span data-ttu-id="43fa4-151">Infine, dobbiamo salvare il nostro progresso fino a questo punto.</span><span class="sxs-lookup"><span data-stu-id="43fa4-151">Finally, let us save our progress so far.</span></span> <span data-ttu-id="43fa4-152">Per salvare le modifiche apportate alla scena, selezionare **File > Salva scena come**, assegnare un nome alla scena **principale**e selezionare **Salva**.</span><span class="sxs-lookup"><span data-stu-id="43fa4-152">To save the scene changes, select **File > Save Scene As**, name the scene **Main**, and select **Save**.</span></span>

## <a name="chapter-3---setup-the-project-settings"></a><span data-ttu-id="43fa4-153">Capitolo 3: configurare le impostazioni del progetto</span><span class="sxs-lookup"><span data-stu-id="43fa4-153">Chapter 3 - Setup the Project Settings</span></span>

>[!VIDEO https://www.youtube.com/embed/ItRoiXccC0g]

<span data-ttu-id="43fa4-154">In questo capitolo vengono impostate alcune impostazioni di progetto Unity che ci aiutano a usare Windows Olografic SDK per lo sviluppo.</span><span class="sxs-lookup"><span data-stu-id="43fa4-154">In this chapter, we will set some Unity project settings that help us target the Windows Holographic SDK for development.</span></span> <span data-ttu-id="43fa4-155">Vengono inoltre impostate alcune impostazioni di qualità per l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="43fa4-155">We will also set some quality settings for our application.</span></span> <span data-ttu-id="43fa4-156">Infine, si assicurerà che le destinazioni di compilazione siano impostate su piattaforma UWP (Universal Windows Platform).</span><span class="sxs-lookup"><span data-stu-id="43fa4-156">Finally, we will ensure our build targets are set to Universal Windows Platform.</span></span>

### <a name="unity-performance-and-quality-settings"></a><span data-ttu-id="43fa4-157">Impostazioni delle prestazioni e della qualità di Unity</span><span class="sxs-lookup"><span data-stu-id="43fa4-157">Unity performance and quality settings</span></span>

<span data-ttu-id="43fa4-158">**Impostazioni della qualità di Unity per HoloLens**</span><span class="sxs-lookup"><span data-stu-id="43fa4-158">**Unity quality settings for HoloLens**</span></span>

![Impostazioni della qualità di Unity per HoloLens](images/qualitysettings.png)

<span data-ttu-id="43fa4-160">Poiché la gestione di un framerate elevato su HoloLens è così importante, è opportuno ottimizzare le impostazioni di qualità per ottenere prestazioni più rapide.</span><span class="sxs-lookup"><span data-stu-id="43fa4-160">Since maintaining high framerate on HoloLens is so important, we want the quality settings tuned for fastest performance.</span></span> <span data-ttu-id="43fa4-161">Per informazioni più dettagliate sulle prestazioni, [consigli sulle prestazioni per Unity](performance-recommendations-for-unity.md).</span><span class="sxs-lookup"><span data-stu-id="43fa4-161">For more detailed performance information, [Performance recommendations for Unity](performance-recommendations-for-unity.md).</span></span>

1. <span data-ttu-id="43fa4-162">Selezionare **modifica > impostazioni progetto > qualità**</span><span class="sxs-lookup"><span data-stu-id="43fa4-162">Select **Edit > Project Settings > Quality**</span></span>
2. <span data-ttu-id="43fa4-163">Selezionare l' **elenco a discesa** sotto il logo **piattaforma UWP (Universal Windows Platform)** e selezionare **molto basso**.</span><span class="sxs-lookup"><span data-stu-id="43fa4-163">Select the **dropdown** under the **Universal Windows Platform** logo and select **Very Low**.</span></span> <span data-ttu-id="43fa4-164">Si saprà che l'impostazione viene applicata correttamente quando la casella nella colonna piattaforma UWP (Universal Windows Platform) e la riga **molto bassa** è verde.</span><span class="sxs-lookup"><span data-stu-id="43fa4-164">You'll know the setting is applied correctly when the box in the Universal Windows Platform column and **Very Low** row is green.</span></span>

<span data-ttu-id="43fa4-165">**Per le applicazioni di realtà miste destinate a schermi**bloccati, è possibile lasciare le impostazioni di qualità ai valori predefiniti.</span><span class="sxs-lookup"><span data-stu-id="43fa4-165">**For mixed reality applications targeted to occluded displays**, you can leave the quality settings to its default values.</span></span>

### <a name="target-windows-10-sdk"></a><span data-ttu-id="43fa4-166">Windows 10 SDK di destinazione</span><span class="sxs-lookup"><span data-stu-id="43fa4-166">Target Windows 10 SDK</span></span>

<span data-ttu-id="43fa4-167">**SDK Windows olografico di destinazione**</span><span class="sxs-lookup"><span data-stu-id="43fa4-167">**Target Windows Holographic SDK**</span></span>

![SDK Windows olografico di destinazione](images/xrsettings.png)

<span data-ttu-id="43fa4-169">È necessario informare Unity che l'app che si sta tentando di esportare deve creare una [visualizzazione immersiva](app-views.md) anziché una visualizzazione 2D.</span><span class="sxs-lookup"><span data-stu-id="43fa4-169">We need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="43fa4-170">Questa operazione viene eseguita abilitando il supporto della realtà virtuale in Unity per Windows 10 SDK.</span><span class="sxs-lookup"><span data-stu-id="43fa4-170">We do this by enabling Virtual Reality support on Unity targeting the Windows 10 SDK.</span></span>

1. <span data-ttu-id="43fa4-171">Passare a **Edit > Settings Project > Player**.</span><span class="sxs-lookup"><span data-stu-id="43fa4-171">Go to **Edit > Project Settings > Player**.</span></span>
2. <span data-ttu-id="43fa4-172">Nel **pannello Inspector** per le impostazioni del lettore selezionare l'icona **piattaforma UWP (Universal Windows Platform)** .</span><span class="sxs-lookup"><span data-stu-id="43fa4-172">In the **Inspector Panel** for Player Settings, select the **Universal Windows Platform** icon.</span></span>
3. <span data-ttu-id="43fa4-173">Espandere il gruppo **Impostazioni XR**.</span><span class="sxs-lookup"><span data-stu-id="43fa4-173">Expand the **XR Settings** group.</span></span>
4. <span data-ttu-id="43fa4-174">Nella sezione **rendering** selezionare la casella di controllo **realtà virtuale supportata** per aggiungere un nuovo elenco **SDK di realtà virtuale** .</span><span class="sxs-lookup"><span data-stu-id="43fa4-174">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality SDKs** list.</span></span>
5. <span data-ttu-id="43fa4-175">Verificare che **Realtà mista di Windows** sia visualizzato nell'elenco.</span><span class="sxs-lookup"><span data-stu-id="43fa4-175">Verify that **Windows Mixed Reality** appears in the list.</span></span> <span data-ttu-id="43fa4-176">In caso contrario, selezionare il pulsante **+** nella parte inferiore dell'elenco e scegliere **Realtà mista di Windows**.</span><span class="sxs-lookup"><span data-stu-id="43fa4-176">If not, select the **+** button at the bottom of the list and choose **Windows Mixed Reality**.</span></span>

>[!NOTE]
><span data-ttu-id="43fa4-177">Se l'icona **piattaforma UWP (Universal Windows Platform)** non viene visualizzata, verificare di aver selezionato piattaforma UWP (Universal Windows Platform) supporto della compilazione durante l'installazione.</span><span class="sxs-lookup"><span data-stu-id="43fa4-177">If you do not see the **Universal Windows Platform** icon, double check to make sure you selected Universal Windows Platform Build Support during installation.</span></span> <span data-ttu-id="43fa4-178">In caso contrario, potrebbe essere necessario reinstallare Unity con la corretta installazione di Windows.</span><span class="sxs-lookup"><span data-stu-id="43fa4-178">If not, you may need to reinstall Unity with the correct Windows installation.</span></span>

<span data-ttu-id="43fa4-179">Un processo straordinario per il recupero di tutte le impostazioni del progetto applicate.</span><span class="sxs-lookup"><span data-stu-id="43fa4-179">Awesome job on getting all the project settings applied.</span></span> <span data-ttu-id="43fa4-180">Quindi, aggiungiamo un ologramma!</span><span class="sxs-lookup"><span data-stu-id="43fa4-180">Next, let us add a hologram!</span></span>

## <a name="chapter-4---create-a-cube"></a><span data-ttu-id="43fa4-181">Capitolo 4-creazione di un cubo</span><span class="sxs-lookup"><span data-stu-id="43fa4-181">Chapter 4 - Create a cube</span></span>

>[!VIDEO https://www.youtube.com/embed/qKcK1Yuj-HQ]

<span data-ttu-id="43fa4-182">La creazione di un cubo nel progetto Unity è simile alla creazione di qualsiasi altro oggetto in Unity.</span><span class="sxs-lookup"><span data-stu-id="43fa4-182">Creating a cube in your Unity project is just like creating any other object in Unity.</span></span> <span data-ttu-id="43fa4-183">Posizionare un cubo davanti all'utente è facile perché il sistema di coordinate di Unity è mappato al mondo reale, in cui un contatore in Unity è approssimativamente un contatore nel mondo reale.</span><span class="sxs-lookup"><span data-stu-id="43fa4-183">Placing a cube in front of the user is easy because Unity's coordinate system is mapped to the real world - where one meter in Unity is approximately one meter in the real world.</span></span>

1. <span data-ttu-id="43fa4-184">Nell'angolo in alto a sinistra del pannello **gerarchia** selezionare l'elenco a discesa **Crea** e scegliere **oggetto 3D > cubo**.</span><span class="sxs-lookup"><span data-stu-id="43fa4-184">In the top left corner of the **Hierarchy** panel, select the **Create** dropdown and choose **3D Object > Cube**.</span></span>
2. <span data-ttu-id="43fa4-185">Selezionare il **cubo** appena creato nel pannello **gerarchia**</span><span class="sxs-lookup"><span data-stu-id="43fa4-185">Select the newly created **Cube** in the **Hierarchy** panel</span></span>
3. <span data-ttu-id="43fa4-186">Nel **controllo** trovare il componente **Transform** e modificare **position** in (**X**: 0, **Y**: 0, **Z**: 2).</span><span class="sxs-lookup"><span data-stu-id="43fa4-186">In the **Inspector** find the **Transform** component and change **Position** to (**X**: 0, **Y**: 0, **Z**: 2).</span></span> <span data-ttu-id="43fa4-187">*Questa operazione posiziona il cubo 2 metri davanti alla posizione iniziale dell'utente.*</span><span class="sxs-lookup"><span data-stu-id="43fa4-187">*This positions the cube 2 meters in front of the user's starting position.*</span></span>
4. <span data-ttu-id="43fa4-188">Nel componente **trasformazione** modificare la **rotazione** in (**x**: 45, **Y**: 45, **Z**: 45) e modificare la **scala** in (**X**: 0,25, **Y**: 0,25, **Z**: 0,25).</span><span class="sxs-lookup"><span data-stu-id="43fa4-188">In the **Transform** component, change **Rotation** to (**X**: 45, **Y**: 45, **Z**: 45) and change **Scale** to (**X**: 0.25, **Y**: 0.25, **Z**: 0.25).</span></span> <span data-ttu-id="43fa4-189">*Questa operazione consente di ridimensionare il cubo a 0,25 metri.*</span><span class="sxs-lookup"><span data-stu-id="43fa4-189">*This scales the cube to 0.25 meters.*</span></span>
5. <span data-ttu-id="43fa4-190">Per salvare le modifiche apportate alla scena, selezionare **File > Salva scena**.</span><span class="sxs-lookup"><span data-stu-id="43fa4-190">To save the scene changes, select **File > Save Scene**.</span></span>

## <a name="chapter-5---verify-on-device-from-unity-editor"></a><span data-ttu-id="43fa4-191">Capitolo 5-verificare nel dispositivo dall'editor Unity</span><span class="sxs-lookup"><span data-stu-id="43fa4-191">Chapter 5 - Verify on device from Unity editor</span></span>

>[!VIDEO https://www.youtube.com/embed/vmCfiIdRb6Q]

<span data-ttu-id="43fa4-192">A questo punto, dopo aver creato il cubo, è possibile eseguire un controllo rapido nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="43fa4-192">Now that we have created our cube, it is time to do a quick check in device.</span></span> <span data-ttu-id="43fa4-193">Questa operazione può essere eseguita direttamente dall'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="43fa4-193">You can do this directly from within the Unity editor.</span></span>

### <a name="initial-setup"></a><span data-ttu-id="43fa4-194">Configurazione iniziale</span><span class="sxs-lookup"><span data-stu-id="43fa4-194">Initial setup</span></span>

1. <span data-ttu-id="43fa4-195">Nel computer di sviluppo, in Unity, aprire **File > finestra impostazioni di compilazione** .</span><span class="sxs-lookup"><span data-stu-id="43fa4-195">On your development PC, in Unity, open **File > Build Settings** window.</span></span>
2. <span data-ttu-id="43fa4-196">Modificare la **piattaforma** in **piattaforma UWP (Universal Windows Platform)** e fare clic su Cambia **piattaforma**</span><span class="sxs-lookup"><span data-stu-id="43fa4-196">Change **Platform** to **Universal Windows Platform** and click **Switch Platform**</span></span>

### <a name="for-hololens-use-unity-remoting"></a><span data-ttu-id="43fa4-197">Per HoloLens usare la comunicazione remota di Unity</span><span class="sxs-lookup"><span data-stu-id="43fa4-197">For HoloLens use Unity Remoting</span></span>

1. <span data-ttu-id="43fa4-198">In HoloLens installare ed eseguire il lettore di [comunicazione remota olografico](holographic-remoting-player.md), disponibile in Windows Store.</span><span class="sxs-lookup"><span data-stu-id="43fa4-198">On your HoloLens, install and run the [Holographic Remoting Player](holographic-remoting-player.md), available from the Windows Store.</span></span> <span data-ttu-id="43fa4-199">Avviare l'applicazione nel dispositivo, che entrerà in uno stato di attesa e visualizzerà l'indirizzo IP del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="43fa4-199">Launch the application on the device, and it will enter a waiting state and show the IP address of the device.</span></span> <span data-ttu-id="43fa4-200">Prendere nota dell'indirizzo IP.</span><span class="sxs-lookup"><span data-stu-id="43fa4-200">Note down the IP.</span></span>
2. <span data-ttu-id="43fa4-201">Aprire la **finestra > XR > emulazione olografica**.</span><span class="sxs-lookup"><span data-stu-id="43fa4-201">Open **Window > XR > Holographic Emulation**.</span></span>
3. <span data-ttu-id="43fa4-202">Modificare la **modalità di emulazione** da **Nessuna** a **remota a dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="43fa4-202">Change **Emulation Mode** from **None** to **Remote to Device**.</span></span>
4. <span data-ttu-id="43fa4-203">In **computer remoto**, immettere l'indirizzo IP della HoloLens annotata in precedenza.</span><span class="sxs-lookup"><span data-stu-id="43fa4-203">In **Remote Machine**, enter the IP address of your HoloLens noted earlier.</span></span>
5. <span data-ttu-id="43fa4-204">Fare clic su **Connetti**.</span><span class="sxs-lookup"><span data-stu-id="43fa4-204">Click **Connect**.</span></span>
6. <span data-ttu-id="43fa4-205">Verificare che lo **stato della connessione** venga modificato in verde **connesso**.</span><span class="sxs-lookup"><span data-stu-id="43fa4-205">Ensure the **Connection Status** changes to green **Connected**.</span></span>
7. <span data-ttu-id="43fa4-206">A questo punto è possibile fare clic su **Play** nell'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="43fa4-206">Now you can now click **Play** in the Unity editor.</span></span>

<span data-ttu-id="43fa4-207">A questo punto sarà possibile visualizzare il cubo nel dispositivo e nell'editor.</span><span class="sxs-lookup"><span data-stu-id="43fa4-207">You will now be able to see the cube in device and in the editor.</span></span> <span data-ttu-id="43fa4-208">È possibile sospendere, ispezionare gli oggetti ed eseguire il debug in modo analogo all'esecuzione di un'app nell'editor, perché si tratta essenzialmente di ciò che accade, ma con video, audio e input del dispositivo trasmessi attraverso la rete tra il computer host e il dispositivo.</span><span class="sxs-lookup"><span data-stu-id="43fa4-208">You can pause, inspect objects, and debug just like you are running an app in the editor, because that's essentially what's happening, but with video, audio, and device input transmitted back and forth across the network between the host machine and the device.</span></span>

### <a name="for-other-mixed-reality-supported-headsets"></a><span data-ttu-id="43fa4-209">Per gli altri tipi di auricolari supportati dalla realtà mista</span><span class="sxs-lookup"><span data-stu-id="43fa4-209">For other mixed reality supported headsets</span></span>

1. <span data-ttu-id="43fa4-210">Connettere la cuffia al PC di sviluppo usando il cavo USB e il cavo porta HDMI o schermo.</span><span class="sxs-lookup"><span data-stu-id="43fa4-210">Connect the headset to your development PC using the USB cable and the HDMI or display port cable.</span></span>
2. <span data-ttu-id="43fa4-211">Avviare il **portale di realtà mista** e assicurarsi di avere completato la prima esperienza di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="43fa4-211">Launch the **Mixed Reality Portal** and ensure you have completed the first run experience.</span></span>
3. <span data-ttu-id="43fa4-212">Da Unity è ora possibile premere il pulsante Play.</span><span class="sxs-lookup"><span data-stu-id="43fa4-212">From Unity, you can now press the Play button.</span></span>

<span data-ttu-id="43fa4-213">A questo punto, sarà possibile visualizzare il rendering dei cubi nell'auricolare della realtà mista e nell'editor.</span><span class="sxs-lookup"><span data-stu-id="43fa4-213">You will now be able to see the cube rendering in your mixed reality headset and in the editor.</span></span>

## <a name="chapter-6---build-and-deploy-to-device-from-visual-studio"></a><span data-ttu-id="43fa4-214">Capitolo 6: creare e distribuire nel dispositivo da Visual Studio</span><span class="sxs-lookup"><span data-stu-id="43fa4-214">Chapter 6 - Build and deploy to device from Visual Studio</span></span>

>[!VIDEO https://www.youtube.com/embed/USSu8yHUdbk]

<span data-ttu-id="43fa4-215">A questo punto è possibile compilare il progetto in Visual Studio e distribuirlo nel dispositivo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="43fa4-215">We are now ready to compile our project to Visual Studio and deploy to our target device.</span></span>

### <a name="export-to-the-visual-studio-solution"></a><span data-ttu-id="43fa4-216">Esporta nella soluzione di Visual Studio</span><span class="sxs-lookup"><span data-stu-id="43fa4-216">Export to the Visual Studio solution</span></span>

1. <span data-ttu-id="43fa4-217">Aprire **File > finestra impostazioni di compilazione** .</span><span class="sxs-lookup"><span data-stu-id="43fa4-217">Open **File > Build Settings** window.</span></span>
1. <span data-ttu-id="43fa4-218">Fare clic su **Aggiungi scene aperte** per aggiungere la scena.</span><span class="sxs-lookup"><span data-stu-id="43fa4-218">Click **Add Open Scenes** to add the scene.</span></span>
1. <span data-ttu-id="43fa4-219">Modificare la **piattaforma** in **piattaforma UWP (Universal Windows Platform)** e fare clic su **Cambia piattaforma**.</span><span class="sxs-lookup"><span data-stu-id="43fa4-219">Change **Platform** to **Universal Windows Platform** and click **Switch Platform**.</span></span>
1. <span data-ttu-id="43fa4-220">In **piattaforma UWP (Universal Windows Platform)** impostazioni assicurarsi che l' **SDK** sia **universale 10**.</span><span class="sxs-lookup"><span data-stu-id="43fa4-220">In **Universal Windows Platform** settings, ensure **SDK** is **Universal 10**.</span></span>
1. <span data-ttu-id="43fa4-221">Per il dispositivo di destinazione, lasciare a **qualsiasi dispositivo** per visualizzare le schermate o passare a **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="43fa4-221">For Target device, leave to **Any Device** for occluded displays or switch to **HoloLens**.</span></span>
1. <span data-ttu-id="43fa4-222">Il **tipo di compilazione UWP** deve essere **D3D**.</span><span class="sxs-lookup"><span data-stu-id="43fa4-222">**UWP Build Type** should be **D3D**.</span></span>
1. <span data-ttu-id="43fa4-223">L' **SDK di UWP** potrebbe essere rimasto **installato più di recente**.</span><span class="sxs-lookup"><span data-stu-id="43fa4-223">**UWP SDK** could be left at **Latest installed**.</span></span>
1. <span data-ttu-id="43fa4-224">Fare clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="43fa4-224">Click **Build**.</span></span>
1. <span data-ttu-id="43fa4-225">In Esplora file fare clic su **nuova cartella** e denominare la cartella **"app"**.</span><span class="sxs-lookup"><span data-stu-id="43fa4-225">In the file explorer, click **New Folder** and name the folder **"App"**.</span></span>
1. <span data-ttu-id="43fa4-226">Con la cartella **app** selezionata, fare clic sul pulsante **Seleziona cartella** .</span><span class="sxs-lookup"><span data-stu-id="43fa4-226">With the **App** folder selected, click the **Select Folder** button.</span></span>
1. <span data-ttu-id="43fa4-227">Al termine della compilazione di Unity, viene visualizzata una finestra Esplora file di Windows.</span><span class="sxs-lookup"><span data-stu-id="43fa4-227">When Unity is done building, a Windows File Explorer window will appear.</span></span>
1. <span data-ttu-id="43fa4-228">Aprire la cartella dell' **app** in Esplora file.</span><span class="sxs-lookup"><span data-stu-id="43fa4-228">Open the **App** folder in file explorer.</span></span>
1. <span data-ttu-id="43fa4-229">Aprire la soluzione di Visual Studio generata (MixedRealityIntroduction. sln in questo esempio)</span><span class="sxs-lookup"><span data-stu-id="43fa4-229">Open the generated Visual Studio solution (MixedRealityIntroduction.sln in this example)</span></span>

### <a name="compile-the-visual-studio-solution"></a><span data-ttu-id="43fa4-230">Compilare la soluzione di Visual Studio</span><span class="sxs-lookup"><span data-stu-id="43fa4-230">Compile the Visual Studio solution</span></span>

<span data-ttu-id="43fa4-231">Infine, la soluzione di Visual Studio esportata verrà compilata, distribuita e provata nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="43fa4-231">Finally, we will compile the exported Visual Studio solution, deploy it, and try it out on the device.</span></span>

1. <span data-ttu-id="43fa4-232">Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione da **debug** a **Release** e da **ARM** a **x86**.</span><span class="sxs-lookup"><span data-stu-id="43fa4-232">Using the top toolbar in Visual Studio, change the target from **Debug** to **Release** and from **ARM** to **X86**.</span></span>

<span data-ttu-id="43fa4-233">Le istruzioni sono diverse per la distribuzione in un dispositivo rispetto all'emulatore.</span><span class="sxs-lookup"><span data-stu-id="43fa4-233">The instructions differ for deploying to a device versus the emulator.</span></span> <span data-ttu-id="43fa4-234">Seguire le istruzioni corrispondenti alla configurazione.</span><span class="sxs-lookup"><span data-stu-id="43fa4-234">Follow the instructions that match your setup.</span></span>

### <a name="deploy-to-mixed-reality-device-over-wi-fi"></a><span data-ttu-id="43fa4-235">Eseguire la distribuzione in un dispositivo a realtà mista tramite Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="43fa4-235">Deploy to mixed reality device over Wi-Fi</span></span>

1. <span data-ttu-id="43fa4-236">Fare clic sulla freccia accanto al pulsante **locale del computer** e modificare la destinazione di distribuzione in **computer remoto**.</span><span class="sxs-lookup"><span data-stu-id="43fa4-236">Click on the arrow next to the **Local Machine** button, and change the deployment target to **Remote Machine**.</span></span>
2. <span data-ttu-id="43fa4-237">Immettere l'indirizzo IP del dispositivo in realtà mista e modificare la **modalità di autenticazione** in Universal (protocollo non crittografato) per HoloLens e **Windows** per altri dispositivi.</span><span class="sxs-lookup"><span data-stu-id="43fa4-237">Enter the IP address of your mixed reality device and change **Authentication Mode** to Universal (Unencrypted Protocol) for HoloLens and **Windows** for other devices.</span></span>
3. <span data-ttu-id="43fa4-238">Fare clic su **debug > avvia senza eseguire debug**.</span><span class="sxs-lookup"><span data-stu-id="43fa4-238">Click **Debug > Start without debugging**.</span></span>

<span data-ttu-id="43fa4-239">**Per HoloLens**, se questa è la prima volta che si esegue la distribuzione nel dispositivo, sarà necessario eseguire l'associazione [con Visual Studio](using-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="43fa4-239">**For HoloLens**, If this is the first time deploying to your device, you will need to pair [using Visual Studio](using-visual-studio.md).</span></span>

### <a name="deploy-to-mixed-reality-device-over-usb"></a><span data-ttu-id="43fa4-240">Distribuisci in un dispositivo a realtà mista tramite USB</span><span class="sxs-lookup"><span data-stu-id="43fa4-240">Deploy to mixed reality device over USB</span></span>

<span data-ttu-id="43fa4-241">Verificare che il dispositivo sia collegato tramite il cavo USB.</span><span class="sxs-lookup"><span data-stu-id="43fa4-241">Ensure you device is plugged in via the USB cable.</span></span>

1. <span data-ttu-id="43fa4-242">**Per HoloLens**, fare clic sulla freccia accanto al pulsante **locale del computer** e modificare la destinazione di distribuzione nel **dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="43fa4-242">**For HoloLens**, click on the arrow next to the **Local Machine** button, and change the deployment target to **Device**.</span></span>
2. <span data-ttu-id="43fa4-243">**Per individuare i dispositivi bloccati collegati al PC**, impostare il computer locale.</span><span class="sxs-lookup"><span data-stu-id="43fa4-243">**For targeting occluded devices attached to your PC**, keep the setting to Local Machine.</span></span> <span data-ttu-id="43fa4-244">Assicurarsi che sia in esecuzione il **portale di realtà mista** .</span><span class="sxs-lookup"><span data-stu-id="43fa4-244">Ensure you have the **Mixed Reality Portal** running.</span></span>
3. <span data-ttu-id="43fa4-245">Fare clic su **debug > avvia senza eseguire debug**.</span><span class="sxs-lookup"><span data-stu-id="43fa4-245">Click **Debug > Start without debugging**.</span></span>

### <a name="deploy-to-emulator"></a><span data-ttu-id="43fa4-246">Distribuisci nell'emulatore</span><span class="sxs-lookup"><span data-stu-id="43fa4-246">Deploy to Emulator</span></span>

1. <span data-ttu-id="43fa4-247">Fare clic sulla freccia accanto al pulsante **Device (dispositivo** ) e nell'elenco a discesa selezionare **HoloLens Emulator (emulatore**).</span><span class="sxs-lookup"><span data-stu-id="43fa4-247">Click on the arrow next to the **Device** button, and from drop down select **HoloLens Emulator**.</span></span>
2. <span data-ttu-id="43fa4-248">Fare clic su **debug > avvia senza eseguire debug**.</span><span class="sxs-lookup"><span data-stu-id="43fa4-248">Click **Debug > Start without debugging**.</span></span>

### <a name="try-out-your-app"></a><span data-ttu-id="43fa4-249">Provare l'app</span><span class="sxs-lookup"><span data-stu-id="43fa4-249">Try out your app</span></span>

<span data-ttu-id="43fa4-250">Ora che l'app è stata distribuita, provare a spostarsi in tutto il cubo e osservare che rimane nel mondo davanti all'utente.</span><span class="sxs-lookup"><span data-stu-id="43fa4-250">Now that your app is deployed, try moving all around the cube and observe that it stays in the world in front of you.</span></span>

## <a name="see-also"></a><span data-ttu-id="43fa4-251">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="43fa4-251">See also</span></span>

* [<span data-ttu-id="43fa4-252">Panoramica dello sviluppo per Unity</span><span class="sxs-lookup"><span data-stu-id="43fa4-252">Unity development overview</span></span>](unity-development-overview.md)
* [<span data-ttu-id="43fa4-253">Procedure consigliate per l'uso con Unity e Visual Studio</span><span class="sxs-lookup"><span data-stu-id="43fa4-253">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)
* [<span data-ttu-id="43fa4-254">Nozioni di base MR 101</span><span class="sxs-lookup"><span data-stu-id="43fa4-254">MR Basics 101</span></span>](holograms-101.md)
* [<span data-ttu-id="43fa4-255">Nozioni di base MR 101E</span><span class="sxs-lookup"><span data-stu-id="43fa4-255">MR Basics 101E</span></span>](holograms-101e.md)

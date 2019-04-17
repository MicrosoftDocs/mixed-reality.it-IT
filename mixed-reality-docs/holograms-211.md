---
title: Input MR 211 - movimento
description: Seguire questa procedura dettagliata codifica con Unity, Visual Studio e HoloLens informazioni dettagliate sui concetti di movimento.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit unity, academy, esercitazione, movimento
ms.openlocfilehash: 76d2b4c0ac3d0a3783b091f7dc8c39548a18b548
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603387"
---
>[!NOTE]
><span data-ttu-id="f464e-104">Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.</span><span class="sxs-lookup"><span data-stu-id="f464e-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="f464e-105">Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.</span><span class="sxs-lookup"><span data-stu-id="f464e-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="f464e-106">Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.</span><span class="sxs-lookup"><span data-stu-id="f464e-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="f464e-107">Essi verranno mantenute per continuare a utilizzare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="f464e-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="f464e-108">Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="f464e-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="f464e-109">Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.</span><span class="sxs-lookup"><span data-stu-id="f464e-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-input-211-gesture"></a><span data-ttu-id="f464e-110">Input di MR 211: Movimento</span><span class="sxs-lookup"><span data-stu-id="f464e-110">MR Input 211: Gesture</span></span>

<span data-ttu-id="f464e-111">[I movimenti](gestures.md) Trasforma intenzione dell'utente in azione.</span><span class="sxs-lookup"><span data-stu-id="f464e-111">[Gestures](gestures.md) turn user intention into action.</span></span> <span data-ttu-id="f464e-112">I movimenti, gli utenti possono interagire con vntana.</span><span class="sxs-lookup"><span data-stu-id="f464e-112">With gestures, users can interact with holograms.</span></span> <span data-ttu-id="f464e-113">In questo corso, si apprenderà come tenere traccia delle lancette dell'utente, rispondere all'input dell'utente, e forniscono feedback all'utente d' parte dello stato e la posizione.</span><span class="sxs-lookup"><span data-stu-id="f464e-113">In this course, we'll learn how to track the user's hands, respond to user input, and give feedback to the user based on hand state and location.</span></span>

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

<span data-ttu-id="f464e-114">Nelle [MR nozioni di base 101](holograms-101.md), abbiamo utilizzato un movimento puntato semplice per interagire con i nostri vntana.</span><span class="sxs-lookup"><span data-stu-id="f464e-114">In [MR Basics 101](holograms-101.md), we used a simple air-tap gesture to interact with our holograms.</span></span> <span data-ttu-id="f464e-115">A questo punto, verrà oltre il movimento indice puntato e vengono illustrati i concetti nuovi da:</span><span class="sxs-lookup"><span data-stu-id="f464e-115">Now, we'll move beyond the air-tap gesture and explore new concepts to:</span></span>

* <span data-ttu-id="f464e-116">Rilevare quando è sottoposto a rilevamento manuale dell'utente e fornire commenti e suggerimenti all'utente.</span><span class="sxs-lookup"><span data-stu-id="f464e-116">Detect when the user's hand is being tracked and provide feedback to the user.</span></span>
* <span data-ttu-id="f464e-117">Per ruotare il vntana, utilizzare un gesto di spostamento.</span><span class="sxs-lookup"><span data-stu-id="f464e-117">Use a navigation gesture to rotate our holograms.</span></span>
* <span data-ttu-id="f464e-118">Fornire commenti e suggerimenti quando sta per passare dalla visualizzazione manuale dell'utente.</span><span class="sxs-lookup"><span data-stu-id="f464e-118">Provide feedback when the user's hand is about to go out of view.</span></span>
* <span data-ttu-id="f464e-119">Usare gli eventi di manipolazione per consentire agli utenti di spostare vntana con le mani.</span><span class="sxs-lookup"><span data-stu-id="f464e-119">Use manipulation events to allow users to move holograms with their hands.</span></span>

<span data-ttu-id="f464e-120">In questo corso, questo aspetto verrà trattato il progetto di Unity **Esplora modelli**, che è stato creato [MR Input 210](holograms-210.md).</span><span class="sxs-lookup"><span data-stu-id="f464e-120">In this course, we'll revisit the Unity project **Model Explorer**, which we built in [MR Input 210](holograms-210.md).</span></span> <span data-ttu-id="f464e-121">L'amico astronautici è tornato per facilitare l'esplorazione di questi nuovi concetti di movimento.</span><span class="sxs-lookup"><span data-stu-id="f464e-121">Our astronaut friend is back to assist us in our exploration of these new gesture concepts.</span></span>

>[!IMPORTANT]
><span data-ttu-id="f464e-122">I video incorporati in ognuna delle sezioni seguenti sono stati registrati usando una versione precedente di Unity e il Toolkit di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="f464e-122">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="f464e-123">Anche se le istruzioni dettagliate sono accurate e aggiornate, è possibile visualizzare gli script e gli oggetti visivi nei video corrispondenti che non sono aggiornati.</span><span class="sxs-lookup"><span data-stu-id="f464e-123">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="f464e-124">I video rimangono inclusi per ci si ricorderà più e perché i concetti illustrati sono applicano.</span><span class="sxs-lookup"><span data-stu-id="f464e-124">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="f464e-125">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="f464e-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="f464e-126">Corso</span><span class="sxs-lookup"><span data-stu-id="f464e-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="f464e-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="f464e-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="f464e-128"><a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></span><span class="sxs-lookup"><span data-stu-id="f464e-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="f464e-129">Input di MR 211: Movimento</span><span class="sxs-lookup"><span data-stu-id="f464e-129">MR Input 211: Gesture</span></span></td><td style="text-align: center;"> <span data-ttu-id="f464e-130">✔️</span><span class="sxs-lookup"><span data-stu-id="f464e-130">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="f464e-131">✔️</span><span class="sxs-lookup"><span data-stu-id="f464e-131">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="f464e-132">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="f464e-132">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="f464e-133">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="f464e-133">Prerequisites</span></span>

* <span data-ttu-id="f464e-134">Un PC Windows 10 configurate con i valori corretti [sono installati gli strumenti](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="f464e-134">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="f464e-135">Alcuni basic C# capacità di programmazione.</span><span class="sxs-lookup"><span data-stu-id="f464e-135">Some basic C# programming ability.</span></span>
* <span data-ttu-id="f464e-136">È necessario avere completato [MR nozioni di base 101](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="f464e-136">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="f464e-137">È necessario avere completato [MR Input 210](holograms-210.md).</span><span class="sxs-lookup"><span data-stu-id="f464e-137">You should have completed [MR Input 210](holograms-210.md).</span></span>
* <span data-ttu-id="f464e-138">Un dispositivo HoloLens [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="f464e-138">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="f464e-139">File di progetto</span><span class="sxs-lookup"><span data-stu-id="f464e-139">Project files</span></span>

* <span data-ttu-id="f464e-140">Scaricare il [file](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) necessarie per il progetto.</span><span class="sxs-lookup"><span data-stu-id="f464e-140">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) required by the project.</span></span><span data-ttu-id="f464e-141"> Richiede Unity 2017.2 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="f464e-141"> Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="f464e-142">Annullare la-archive i file sul desktop o altri facile da raggiungere percorso.</span><span class="sxs-lookup"><span data-stu-id="f464e-142">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="f464e-143">Se si desidera esaminare il codice sorgente prima di scaricare, ha [disponibile in GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).</span><span class="sxs-lookup"><span data-stu-id="f464e-143">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="f464e-144">Errori e note</span><span class="sxs-lookup"><span data-stu-id="f464e-144">Errata and Notes</span></span>

* <span data-ttu-id="f464e-145">"Abilita Just My Code" deve essere disabilitato (*unchecked*) in Visual Studio in Strumenti -> Opzioni -> debug per poter raggiungere punti di interruzione nel codice.</span><span class="sxs-lookup"><span data-stu-id="f464e-145">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-0---unity-setup"></a><span data-ttu-id="f464e-146">Capitolo 0 - programma di installazione di Unity</span><span class="sxs-lookup"><span data-stu-id="f464e-146">Chapter 0 - Unity Setup</span></span>

### <a name="instructions"></a><span data-ttu-id="f464e-147">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="f464e-147">Instructions</span></span>

1. <span data-ttu-id="f464e-148">Avviare Unity.</span><span class="sxs-lookup"><span data-stu-id="f464e-148">Start Unity.</span></span>
2. <span data-ttu-id="f464e-149">Selezionare **aperto**.</span><span class="sxs-lookup"><span data-stu-id="f464e-149">Select **Open**.</span></span>
3. <span data-ttu-id="f464e-150">Passare al **movimento** cartella è archiviato in precedenza di annullamento.</span><span class="sxs-lookup"><span data-stu-id="f464e-150">Navigate to the **Gesture** folder you previously un-archived.</span></span>
4. <span data-ttu-id="f464e-151">Individuare e selezionare il **Starting**/**Esplora modelli** cartella.</span><span class="sxs-lookup"><span data-stu-id="f464e-151">Find and select the **Starting**/**Model Explorer** folder.</span></span>
5. <span data-ttu-id="f464e-152">Scegliere il **selezionare la cartella** pulsante.</span><span class="sxs-lookup"><span data-stu-id="f464e-152">Click the **Select Folder** button.</span></span>
6. <span data-ttu-id="f464e-153">Nel **Project** panel, espandere il **scene** cartella.</span><span class="sxs-lookup"><span data-stu-id="f464e-153">In the **Project** panel, expand the **Scenes** folder.</span></span>
7. <span data-ttu-id="f464e-154">Fare doppio clic su **ModelExplorer** scena a caricarlo in Unity.</span><span class="sxs-lookup"><span data-stu-id="f464e-154">Double-click **ModelExplorer** scene to load it in Unity.</span></span>

### <a name="building"></a><span data-ttu-id="f464e-155">Compilazione</span><span class="sxs-lookup"><span data-stu-id="f464e-155">Building</span></span>

1. <span data-ttu-id="f464e-156">In Unity, selezionare **File > Build Settings**.</span><span class="sxs-lookup"><span data-stu-id="f464e-156">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="f464e-157">Se **scene/ModelExplorer** non è elencato nella **scene nella compilazione**, fare clic su **aggiungere scene Open** per aggiungere la scena.</span><span class="sxs-lookup"><span data-stu-id="f464e-157">If **Scenes/ModelExplorer** is not listed in **Scenes In Build**, click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="f464e-158">Se si sta sviluppando in modo specifico per HoloLens, impostare **dispositivo di destinazione** al **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="f464e-158">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="f464e-159">In caso contrario, ci si trova sulla **tutti i dispositivi**.</span><span class="sxs-lookup"><span data-stu-id="f464e-159">Otherwise, leave it on **Any device**.</span></span>
4. <span data-ttu-id="f464e-160">Assicurarsi **tipo di compilazione** è impostata su **D3D** e **SDK** è impostata su **installata più recente** (che deve essere SDK 16299 o versione successiva).</span><span class="sxs-lookup"><span data-stu-id="f464e-160">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
5. <span data-ttu-id="f464e-161">Fai clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="f464e-161">Click **Build**.</span></span>
6. <span data-ttu-id="f464e-162">Creare un **nuova cartella** denominato "App".</span><span class="sxs-lookup"><span data-stu-id="f464e-162">Create a **New Folder** named "App".</span></span>
7. <span data-ttu-id="f464e-163">Solo clic i **App** cartella.</span><span class="sxs-lookup"><span data-stu-id="f464e-163">Single click the **App** folder.</span></span>
8. <span data-ttu-id="f464e-164">Premere **selezionare la cartella** e Unity verrà avviata la compilazione del progetto per Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f464e-164">Press **Select Folder** and Unity will start building the project for Visual Studio.</span></span>

<span data-ttu-id="f464e-165">Quando Unity viene eseguita, verrà visualizzata una finestra di Esplora File.</span><span class="sxs-lookup"><span data-stu-id="f464e-165">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="f464e-166">Aprire il **App** cartella.</span><span class="sxs-lookup"><span data-stu-id="f464e-166">Open the **App** folder.</span></span>
2. <span data-ttu-id="f464e-167">Aprire il **soluzione ModelExplorer Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="f464e-167">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="f464e-168">Se la distribuzione in HoloLens:</span><span class="sxs-lookup"><span data-stu-id="f464e-168">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="f464e-169">Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione di debug per **Release** e da ARM a **x86**.</span><span class="sxs-lookup"><span data-stu-id="f464e-169">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="f464e-170">Fare clic sull'elenco a discesa sulla freccia accanto al pulsante computer locale e selezionare **computer remoto**.</span><span class="sxs-lookup"><span data-stu-id="f464e-170">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="f464e-171">Immettere **l'indirizzo IP del dispositivo HoloLens** e impostare la modalità di autenticazione **universale (protocollo non crittografato)**.</span><span class="sxs-lookup"><span data-stu-id="f464e-171">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="f464e-172">Fare clic su **Seleziona**.</span><span class="sxs-lookup"><span data-stu-id="f464e-172">Click **Select**.</span></span> <span data-ttu-id="f464e-173">Se non si conosce l'indirizzo IP del dispositivo, esaminare **Impostazioni > rete e Internet > Opzioni avanzate**.</span><span class="sxs-lookup"><span data-stu-id="f464e-173">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="f464e-174">Nella barra dei menu superiore, fare clic su **Debug -> Avvia senza eseguire debug** o premere **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="f464e-174">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="f464e-175">Se questa è la prima volta che la distribuzione nel dispositivo, devi [abbinarlo a Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span><span class="sxs-lookup"><span data-stu-id="f464e-175">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
5. <span data-ttu-id="f464e-176">Quando l'app è distribuita, ignorare il **Fitbox** con un **movimento selezionare**.</span><span class="sxs-lookup"><span data-stu-id="f464e-176">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="f464e-177">Se la distribuzione in un visore VR immersivi:</span><span class="sxs-lookup"><span data-stu-id="f464e-177">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="f464e-178">Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione di debug per **Release** e da ARM a **x64**.</span><span class="sxs-lookup"><span data-stu-id="f464e-178">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="f464e-179">Verificare che la destinazione di distribuzione è impostata su **computer locale**.</span><span class="sxs-lookup"><span data-stu-id="f464e-179">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="f464e-180">Nella barra dei menu superiore, fare clic su **Debug -> Avvia senza eseguire debug** o premere **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="f464e-180">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="f464e-181">Quando l'app è distribuita, ignorare il **Fitbox** spostando il trigger in un controller di movimento.</span><span class="sxs-lookup"><span data-stu-id="f464e-181">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

>[!NOTE]
><span data-ttu-id="f464e-182">È possibile riscontrare alcuni errori rosso nel Pannello di errori di Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f464e-182">You might notice some red errors in the Visual Studio Errors panel.</span></span> <span data-ttu-id="f464e-183">È possibile ignorarli.</span><span class="sxs-lookup"><span data-stu-id="f464e-183">It is safe to ignore them.</span></span> <span data-ttu-id="f464e-184">Passare al pannello di Output per visualizzare effettivamente lo stato della compilazione.</span><span class="sxs-lookup"><span data-stu-id="f464e-184">Switch to the Output panel to view actual build progress.</span></span> <span data-ttu-id="f464e-185">Gli errori nel Pannello di Output è necessario rendere una correzione (più spesso che sono causati da un errore in uno script).</span><span class="sxs-lookup"><span data-stu-id="f464e-185">Errors in the Output panel will require you to make a fix (most often they are caused by a mistake in a script).</span></span>

## <a name="chapter-1---hand-detected-feedback"></a><span data-ttu-id="f464e-186">Capitolo 1 - mano rilevato commenti e suggerimenti</span><span class="sxs-lookup"><span data-stu-id="f464e-186">Chapter 1 - Hand detected feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a><span data-ttu-id="f464e-187">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="f464e-187">Objectives</span></span>

* <span data-ttu-id="f464e-188">Gli eventi di rilevamento per presentare la sottoscrizione.</span><span class="sxs-lookup"><span data-stu-id="f464e-188">Subscribe to hand tracking events.</span></span>
* <span data-ttu-id="f464e-189">Usare risposta del cursore da visualizzare agli utenti quando è sottoposto a rilevamento una mano.</span><span class="sxs-lookup"><span data-stu-id="f464e-189">Use cursor feedback to show users when a hand is being tracked.</span></span>

### <a name="instructions"></a><span data-ttu-id="f464e-190">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="f464e-190">Instructions</span></span>

* <span data-ttu-id="f464e-191">Nel **gerarchia** panel, espandere il **InputManager** oggetto.</span><span class="sxs-lookup"><span data-stu-id="f464e-191">In the **Hierarchy** panel, expand the **InputManager** object.</span></span>
* <span data-ttu-id="f464e-192">Cercare e selezionare il **GesturesInput** oggetto.</span><span class="sxs-lookup"><span data-stu-id="f464e-192">Look for and select the **GesturesInput** object.</span></span>

<span data-ttu-id="f464e-193">Il **InteractionInputSource.cs** script esegue queste operazioni:</span><span class="sxs-lookup"><span data-stu-id="f464e-193">The **InteractionInputSource.cs** script performs these steps:</span></span>

1. <span data-ttu-id="f464e-194">Sottoscrive gli eventi InteractionSourceDetected e InteractionSourceLost.</span><span class="sxs-lookup"><span data-stu-id="f464e-194">Subscribes to the InteractionSourceDetected and InteractionSourceLost events.</span></span>
2. <span data-ttu-id="f464e-195">Imposta lo stato HandDetected.</span><span class="sxs-lookup"><span data-stu-id="f464e-195">Sets the HandDetected state.</span></span>
3. <span data-ttu-id="f464e-196">Annulla la sottoscrizione dagli eventi InteractionSourceDetected e InteractionSourceLost.</span><span class="sxs-lookup"><span data-stu-id="f464e-196">Unsubscribes from the InteractionSourceDetected and InteractionSourceLost events.</span></span>

<span data-ttu-id="f464e-197">Successivamente, aggiornamento verrà eseguito il cursore a partire dal [MR Input 210](holograms-210.md) in un unico che mostra i commenti e suggerimenti a seconda delle azioni dell'utente.</span><span class="sxs-lookup"><span data-stu-id="f464e-197">Next, we'll upgrade our cursor from [MR Input 210](holograms-210.md) into one that shows feedback depending on the user's actions.</span></span>

1. <span data-ttu-id="f464e-198">Nel **gerarchia** riquadro, seleziona il **cursore** dell'oggetto e lo elimini.</span><span class="sxs-lookup"><span data-stu-id="f464e-198">In the **Hierarchy** panel, select the **Cursor** object and delete it.</span></span>
2. <span data-ttu-id="f464e-199">Nel **Project** del pannello, cercare **CursorWithFeedback** e trascinarlo nel **gerarchia** pannello.</span><span class="sxs-lookup"><span data-stu-id="f464e-199">In the **Project** panel, search for **CursorWithFeedback** and drag it into the **Hierarchy** panel.</span></span>
3. <span data-ttu-id="f464e-200">Fare clic su **InputManager** nel **gerarchia** pannello, quindi trascinare il **CursorWithFeedback** dell'oggetto dal **gerarchia** nel Del InputManager **SimpleSinglePointerSelector**del **cursore** campo, nella parte inferiore della **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="f464e-200">Click on **InputManager** in the **Hierarchy** panel, then drag the **CursorWithFeedback** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector**'s **Cursor** field, at the bottom of the **Inspector**.</span></span>
4. <span data-ttu-id="f464e-201">Fare clic sui **CursorWithFeedback** nel **gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="f464e-201">Click on the **CursorWithFeedback** in the **Hierarchy**.</span></span>
5. <span data-ttu-id="f464e-202">Nel **Inspector** panel, espandere **i dati sullo stato del cursore** sul **oggetto cursore** script.</span><span class="sxs-lookup"><span data-stu-id="f464e-202">In the **Inspector** panel, expand **Cursor State Data** on the **Object Cursor** script.</span></span>

<span data-ttu-id="f464e-203">Il **i dati sullo stato del cursore** funziona come segue:</span><span class="sxs-lookup"><span data-stu-id="f464e-203">The **Cursor State Data** works like this:</span></span>

* <span data-ttu-id="f464e-204">Eventuali **osservazione** stato significa che non viene rilevata alcuna mano e l'utente viene semplicemente esaminato.</span><span class="sxs-lookup"><span data-stu-id="f464e-204">Any **Observe** state means that no hand is detected and the user is simply looking around.</span></span>
* <span data-ttu-id="f464e-205">Eventuali **Interact** stato significa che una mano o un controller è stato rilevato.</span><span class="sxs-lookup"><span data-stu-id="f464e-205">Any **Interact** state means that a hand or controller is detected.</span></span>
* <span data-ttu-id="f464e-206">Eventuali **passa il mouse** stato indica che l'utente sta guardando ologramma.</span><span class="sxs-lookup"><span data-stu-id="f464e-206">Any **Hover** state means the user is looking at a hologram.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="f464e-207">Compilare e distribuire</span><span class="sxs-lookup"><span data-stu-id="f464e-207">Build and Deploy</span></span>

* <span data-ttu-id="f464e-208">In Unity, usare **File > Build Settings** per ricompili l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="f464e-208">In Unity, use **File > Build Settings** to rebuild the application.</span></span>
* <span data-ttu-id="f464e-209">Aprire il **App** cartella.</span><span class="sxs-lookup"><span data-stu-id="f464e-209">Open the **App** folder.</span></span>
* <span data-ttu-id="f464e-210">Se non è già aperto, aprire il **soluzione di Visual Studio ModelExplorer**.</span><span class="sxs-lookup"><span data-stu-id="f464e-210">If it's not already open, open the **ModelExplorer Visual Studio Solution**.</span></span>
  * <span data-ttu-id="f464e-211">(Se è stato creato o distribuito questo progetto in Visual Studio durante la configurazione, quindi è possibile aprire quell'istanza di Visual Studio e fare clic su 'Ricarica tutto' quando viene richiesto).</span><span class="sxs-lookup"><span data-stu-id="f464e-211">(If you already built/deployed this project in Visual Studio during set-up, then you can open that instance of VS and click 'Reload All' when prompted).</span></span>
* <span data-ttu-id="f464e-212">In Visual Studio, fare clic su **Debug -> Avvia senza eseguire debug** o premere **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="f464e-212">In Visual Studio, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="f464e-213">Dopo la distribuzione dell'applicazione per il HoloLens, ignorare il fitbox tramite il movimento indice puntato.</span><span class="sxs-lookup"><span data-stu-id="f464e-213">After the application deploys to the HoloLens, dismiss the fitbox using the air-tap gesture.</span></span>
* <span data-ttu-id="f464e-214">Spostare la mano in visualizzazione e puntare il dito indice le possibilità di avviare manualmente di rilevamento.</span><span class="sxs-lookup"><span data-stu-id="f464e-214">Move your hand into view and point your index finger to the sky to start hand tracking.</span></span>
* <span data-ttu-id="f464e-215">Spostare la mano a sinistra, destra, alto e verso il basso.</span><span class="sxs-lookup"><span data-stu-id="f464e-215">Move your hand left, right, up and down.</span></span>
* <span data-ttu-id="f464e-216">Guarda come il cursore cambia quando viene rilevata e quindi perso dalla visualizzazione la mano.</span><span class="sxs-lookup"><span data-stu-id="f464e-216">Watch how the cursor changes when your hand is detected and then lost from view.</span></span>
* <span data-ttu-id="f464e-217">Se si usa un visore VR immersivi, è possibile connettere e disconnettere il controller.</span><span class="sxs-lookup"><span data-stu-id="f464e-217">If you're on an immersive headset, you'll have to connect and disconnect your controller.</span></span> <span data-ttu-id="f464e-218">Questo feedback diventa meno interessanti in un dispositivo coinvolgente, come un controller connesso sarà sempre "disponibile".</span><span class="sxs-lookup"><span data-stu-id="f464e-218">This feedback becomes less interesting on an immersive device, as a connected controller will always be "available".</span></span>

## <a name="chapter-2---navigation"></a><span data-ttu-id="f464e-219">Capitolo 2 - navigazione</span><span class="sxs-lookup"><span data-stu-id="f464e-219">Chapter 2 - Navigation</span></span>

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a><span data-ttu-id="f464e-220">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="f464e-220">Objectives</span></span>

* <span data-ttu-id="f464e-221">Usare gli eventi di movimento di navigazione per ruotare l'astronautici.</span><span class="sxs-lookup"><span data-stu-id="f464e-221">Use Navigation gesture events to rotate the astronaut.</span></span>

### <a name="instructions"></a><span data-ttu-id="f464e-222">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="f464e-222">Instructions</span></span>

<span data-ttu-id="f464e-223">Per usare i movimenti di navigazione nell'app, si intende modificare **GestureAction.cs** ruotare gli oggetti quando si verifica il movimento di navigazione.</span><span class="sxs-lookup"><span data-stu-id="f464e-223">To use Navigation gestures in our app, we are going to edit **GestureAction.cs** to rotate objects when the Navigation gesture occurs.</span></span> <span data-ttu-id="f464e-224">Inoltre, si aggiungerà commenti e suggerimenti per il cursore da visualizzare quando l'esplorazione è disponibile.</span><span class="sxs-lookup"><span data-stu-id="f464e-224">Additionally, we'll add feedback to the cursor to display when Navigation is available.</span></span>

1. <span data-ttu-id="f464e-225">Nel **gerarchia** panel, espandere **CursorWithFeedback**.</span><span class="sxs-lookup"><span data-stu-id="f464e-225">In the **Hierarchy** panel, expand **CursorWithFeedback**.</span></span>
2. <span data-ttu-id="f464e-226">Nel **Vntana** cartella trovare il **ScrollFeedback** asset.</span><span class="sxs-lookup"><span data-stu-id="f464e-226">In the **Holograms** folder, find the **ScrollFeedback** asset.</span></span>
3. <span data-ttu-id="f464e-227">Trascinare e rilasciare il **ScrollFeedback** prefab nel **CursorWithFeedback** GameObject nel **gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="f464e-227">Drag and drop the **ScrollFeedback** prefab onto the **CursorWithFeedback** GameObject in the **Hierarchy**.</span></span>
4. <span data-ttu-id="f464e-228">Fare clic su **CursorWithFeedback**.</span><span class="sxs-lookup"><span data-stu-id="f464e-228">Click on **CursorWithFeedback**.</span></span>
5. <span data-ttu-id="f464e-229">Nel **Inspector** del pannello, fare clic sui **Add Component** pulsante.</span><span class="sxs-lookup"><span data-stu-id="f464e-229">In the **Inspector** panel, click the **Add Component** button.</span></span>
6. <span data-ttu-id="f464e-230">Nel menu, digitare nella casella di ricerca **CursorFeedback**.</span><span class="sxs-lookup"><span data-stu-id="f464e-230">In the menu, type in the search box **CursorFeedback**.</span></span> <span data-ttu-id="f464e-231">Selezionare il risultato della ricerca.</span><span class="sxs-lookup"><span data-stu-id="f464e-231">Select the search result.</span></span>
7. <span data-ttu-id="f464e-232">Trascinare e rilasciare il **ScrollFeedback** dall'oggetto il **gerarchia** nel **scorrimento rilevato Game Object** proprietà nel **risposta del cursore**nel componente di **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="f464e-232">Drag and drop the **ScrollFeedback** object from the **Hierarchy** onto the **Scroll Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>
8. <span data-ttu-id="f464e-233">Nel **gerarchia** riquadro, seleziona la **AstroMan** oggetto.</span><span class="sxs-lookup"><span data-stu-id="f464e-233">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
9. <span data-ttu-id="f464e-234">Nel **Inspector** del pannello, fare clic sui **Add Component** pulsante.</span><span class="sxs-lookup"><span data-stu-id="f464e-234">In the **Inspector** panel, click the **Add Component** button.</span></span>
10. <span data-ttu-id="f464e-235">Nel menu, digitare nella casella di ricerca **azione gesto**.</span><span class="sxs-lookup"><span data-stu-id="f464e-235">In the menu, type in the search box **Gesture Action**.</span></span> <span data-ttu-id="f464e-236">Selezionare il risultato della ricerca.</span><span class="sxs-lookup"><span data-stu-id="f464e-236">Select the search result.</span></span>

<span data-ttu-id="f464e-237">Successivamente, aprire **GestureAction.cs** in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f464e-237">Next, open **GestureAction.cs** in Visual Studio.</span></span> <span data-ttu-id="f464e-238">Nella codifica esercitare 2.c, modificare lo script per eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="f464e-238">In coding exercise 2.c, edit the script to do the following:</span></span>

1. <span data-ttu-id="f464e-239">**Ruotare la AstroMan** dell'oggetto ogni volta che viene eseguito un movimento di navigazione.</span><span class="sxs-lookup"><span data-stu-id="f464e-239">**Rotate the AstroMan** object whenever a Navigation gesture is performed.</span></span>
2. <span data-ttu-id="f464e-240">Calcolare le **rotationFactor** per controllare la quantità di rotazione applicata all'oggetto.</span><span class="sxs-lookup"><span data-stu-id="f464e-240">Calculate the **rotationFactor** to control the amount of rotation applied to the object.</span></span>
3. <span data-ttu-id="f464e-241">**Ruotare l'oggetto** intorno all'asse y quando l'utente sposta le mani verso sinistra o destra.</span><span class="sxs-lookup"><span data-stu-id="f464e-241">**Rotate the object** around the y-axis when the user moves their hand left or right.</span></span>

<span data-ttu-id="f464e-242">Scrittura di codice completo esercita 2.c nello script, o sostituire il codice con la soluzione completata seguente:</span><span class="sxs-lookup"><span data-stu-id="f464e-242">Complete coding exercises 2.c in the script, or replace the code with the completed solution below:</span></span>

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

<span data-ttu-id="f464e-243">Si noterà che gli altri eventi di navigazione sono già compilati con alcune informazioni.</span><span class="sxs-lookup"><span data-stu-id="f464e-243">You'll notice that the other navigation events are already filled in with some info.</span></span> <span data-ttu-id="f464e-244">Si inserisce gli elementi GameObject nel Toolkit modale dello stack di InputSystem, in modo che l'utente non dispone di mantenere l'attenzione sull'astronautici una volta iniziata la rotazione.</span><span class="sxs-lookup"><span data-stu-id="f464e-244">We push the GameObject onto the Toolkit's InputSystem's modal stack, so the user doesn't have to maintain focus on the Astronaut once rotation has begun.</span></span> <span data-ttu-id="f464e-245">Di conseguenza, viene segnalato il GameObject dallo stack dopo aver completato il movimento.</span><span class="sxs-lookup"><span data-stu-id="f464e-245">Correspondingly, we pop the GameObject off the stack once the gesture is completed.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="f464e-246">Compilare e distribuire</span><span class="sxs-lookup"><span data-stu-id="f464e-246">Build and Deploy</span></span>

1. <span data-ttu-id="f464e-247">Ricompilare l'applicazione in Unity e quindi compilare e distribuire da Visual Studio per eseguirla di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f464e-247">Rebuild the application in Unity and then build and deploy from Visual Studio to run it in the HoloLens.</span></span>
2. <span data-ttu-id="f464e-248">Fissare astronautici, due frecce dovrebbe essere visualizzato su entrambi i lati del cursore.</span><span class="sxs-lookup"><span data-stu-id="f464e-248">Gaze at the astronaut, two arrows should appear on either side of the cursor.</span></span> <span data-ttu-id="f464e-249">Questo nuovo oggetto visivo indica che possono essere ruotate di astronautici.</span><span class="sxs-lookup"><span data-stu-id="f464e-249">This new visual indicates that the astronaut can be rotated.</span></span>
3. <span data-ttu-id="f464e-250">Posizionare la mano nella posizione pronta (dito indice rivolta verso il cielo) in modo di HoloLens avvierà la mano di rilevamento.</span><span class="sxs-lookup"><span data-stu-id="f464e-250">Place your hand in the ready position (index finger pointed towards the sky) so the HoloLens will start tracking your hand.</span></span>
4. <span data-ttu-id="f464e-251">Per ruotare l'astronautici, ridurre il dito indice in una posizione con avvicinamento delle dita e quindi spostare la mano verso sinistra o destra per attivare il movimento NavigationX.</span><span class="sxs-lookup"><span data-stu-id="f464e-251">To rotate the astronaut, lower your index finger to a pinch position, and then move your hand left or right to trigger the NavigationX gesture.</span></span>

## <a name="chapter-3---hand-guidance"></a><span data-ttu-id="f464e-252">Capitolo 3 - linee guida di mano</span><span class="sxs-lookup"><span data-stu-id="f464e-252">Chapter 3 - Hand Guidance</span></span>

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a><span data-ttu-id="f464e-253">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="f464e-253">Objectives</span></span>

* <span data-ttu-id="f464e-254">Uso **punteggio di informazioni aggiuntive a mano** per aiutare a stimare quando mano rilevamento andranno perse.</span><span class="sxs-lookup"><span data-stu-id="f464e-254">Use **hand guidance score** to help predict when hand tracking will be lost.</span></span>
* <span data-ttu-id="f464e-255">Fornire **commenti e suggerimenti sul cursore** da visualizzare quando il manuale dell'utente si avvicina al bordo della camera della visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="f464e-255">Provide **feedback on the cursor** to show when the user's hand nears the camera's edge of view.</span></span>

### <a name="instructions"></a><span data-ttu-id="f464e-256">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="f464e-256">Instructions</span></span>

1. <span data-ttu-id="f464e-257">Nel **gerarchia** riquadro, seleziona la **CursorWithFeedback** oggetto.</span><span class="sxs-lookup"><span data-stu-id="f464e-257">In the **Hierarchy** panel, select the **CursorWithFeedback** object.</span></span>
2. <span data-ttu-id="f464e-258">Nel **Inspector** del pannello, fare clic sui **Add Component** pulsante.</span><span class="sxs-lookup"><span data-stu-id="f464e-258">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="f464e-259">Nel menu, digitare nella casella di ricerca **mano indicazioni**.</span><span class="sxs-lookup"><span data-stu-id="f464e-259">In the menu, type in the search box **Hand Guidance**.</span></span> <span data-ttu-id="f464e-260">Selezionare il risultato della ricerca.</span><span class="sxs-lookup"><span data-stu-id="f464e-260">Select the search result.</span></span>
4. <span data-ttu-id="f464e-261">Nel **Project** pannello **Vntana** cartella trovare il **HandGuidanceFeedback** asset.</span><span class="sxs-lookup"><span data-stu-id="f464e-261">In the **Project** panel **Holograms** folder, find the **HandGuidanceFeedback** asset.</span></span>
5. <span data-ttu-id="f464e-262">Trascinare e rilasciare il **HandGuidanceFeedback** asset nel **mano indicazioni indicatore** proprietà nel **Inspector** pannello.</span><span class="sxs-lookup"><span data-stu-id="f464e-262">Drag and drop the **HandGuidanceFeedback** asset onto the **Hand Guidance Indicator** property in the **Inspector** panel.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="f464e-263">Compilare e distribuire</span><span class="sxs-lookup"><span data-stu-id="f464e-263">Build and Deploy</span></span>

* <span data-ttu-id="f464e-264">Ricompilare l'applicazione in Unity e quindi compilare e distribuire da Visual Studio per provare l'app in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f464e-264">Rebuild the application in Unity and then build and deploy from Visual Studio to experience the app on HoloLens.</span></span>
* <span data-ttu-id="f464e-265">Portare la mano in visualizzazione e generare il dito indice alla volta registrato.</span><span class="sxs-lookup"><span data-stu-id="f464e-265">Bring your hand into view and raise your index finger to get tracked.</span></span>
* <span data-ttu-id="f464e-266">Avviare la rotazione di astronautici con il movimento di navigazione (il dito indice indietro e Avanti thumb insieme).</span><span class="sxs-lookup"><span data-stu-id="f464e-266">Start rotating the astronaut with the Navigation gesture (pinch your index finger and thumb together).</span></span>
* <span data-ttu-id="f464e-267">Spostare la mano estrema sinistra, destra, freccia su e freccia giù.</span><span class="sxs-lookup"><span data-stu-id="f464e-267">Move your hand far left, right, up, and down.</span></span>
* <span data-ttu-id="f464e-268">Come la mano si avvicina il bordo del frame movimento, viene visualizzata una freccia accanto al cursore per avvisare l'utente mano in corso di rilevamento andranno perso.</span><span class="sxs-lookup"><span data-stu-id="f464e-268">As your hand nears the edge of the gesture frame, an arrow should appear next to the cursor to warn you that hand tracking will be lost.</span></span> <span data-ttu-id="f464e-269">La freccia indica la direzione per spostare la mano per evitare che verifica la perdita.</span><span class="sxs-lookup"><span data-stu-id="f464e-269">The arrow indicates which direction to move your hand in order to prevent tracking from being lost.</span></span>

## <a name="chapter-4---manipulation"></a><span data-ttu-id="f464e-270">Capitolo 4 - modifica</span><span class="sxs-lookup"><span data-stu-id="f464e-270">Chapter 4 - Manipulation</span></span>

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a><span data-ttu-id="f464e-271">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="f464e-271">Objectives</span></span>

* <span data-ttu-id="f464e-272">Usare gli eventi di manipolazione per spostare l'astronautici con le mani.</span><span class="sxs-lookup"><span data-stu-id="f464e-272">Use Manipulation events to move the astronaut with your hands.</span></span>
* <span data-ttu-id="f464e-273">Fornire commenti e suggerimenti sul cursore per informare l'utente quando la manipolazione può essere utilizzata.</span><span class="sxs-lookup"><span data-stu-id="f464e-273">Provide feedback on the cursor to let the user know when Manipulation can be used.</span></span>

### <a name="instructions"></a><span data-ttu-id="f464e-274">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="f464e-274">Instructions</span></span>

<span data-ttu-id="f464e-275">GestureManager.cs e AstronautManager.cs ci consentirà di eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="f464e-275">GestureManager.cs and AstronautManager.cs will allow us to do the following:</span></span>

1. <span data-ttu-id="f464e-276">Usare la parola chiave vocale "**spostare astronautici**" per abilitare **Manipulation** movimenti e "**ruotare astronautici**" per disabilitarli.</span><span class="sxs-lookup"><span data-stu-id="f464e-276">Use the speech keyword "**Move Astronaut**" to enable **Manipulation** gestures and "**Rotate Astronaut**" to disable them.</span></span>
2. <span data-ttu-id="f464e-277">Passare alla risposta per il **riconoscitore di movimento manipolazione**.</span><span class="sxs-lookup"><span data-stu-id="f464e-277">Switch to responding to the **Manipulation Gesture Recognizer**.</span></span>

<span data-ttu-id="f464e-278">Cominciamo.</span><span class="sxs-lookup"><span data-stu-id="f464e-278">Let's get started.</span></span>

1. <span data-ttu-id="f464e-279">Nel **gerarchia** panel, creare un nuovo GameObject vuoto.</span><span class="sxs-lookup"><span data-stu-id="f464e-279">In the **Hierarchy** panel, create a new empty GameObject.</span></span> <span data-ttu-id="f464e-280">Denominarla "**AstronautManager**".</span><span class="sxs-lookup"><span data-stu-id="f464e-280">Name it "**AstronautManager**".</span></span>
2. <span data-ttu-id="f464e-281">Nel **Inspector** del pannello, fare clic sui **Add Component** pulsante.</span><span class="sxs-lookup"><span data-stu-id="f464e-281">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="f464e-282">Nel menu, digitare nella casella di ricerca **astronautici Manager**.</span><span class="sxs-lookup"><span data-stu-id="f464e-282">In the menu, type in the search box **Astronaut Manager**.</span></span> <span data-ttu-id="f464e-283">Selezionare il risultato della ricerca.</span><span class="sxs-lookup"><span data-stu-id="f464e-283">Select the search result.</span></span>
4. <span data-ttu-id="f464e-284">Nel **Inspector** del pannello, fare clic sui **Add Component** pulsante.</span><span class="sxs-lookup"><span data-stu-id="f464e-284">In the **Inspector** panel, click the **Add Component** button.</span></span>
5. <span data-ttu-id="f464e-285">Nel menu, digitare nella casella di ricerca **origine di Input vocale**.</span><span class="sxs-lookup"><span data-stu-id="f464e-285">In the menu, type in the search box **Speech Input Source**.</span></span> <span data-ttu-id="f464e-286">Selezionare il risultato della ricerca.</span><span class="sxs-lookup"><span data-stu-id="f464e-286">Select the search result.</span></span>

<span data-ttu-id="f464e-287">A questo punto si aggiungerà i comandi vocali necessari per controllare lo stato di astronautici l'interazione.</span><span class="sxs-lookup"><span data-stu-id="f464e-287">We'll now add the speech commands required to control the interaction state of the astronaut.</span></span>

1. <span data-ttu-id="f464e-288">Espandere la **parole chiave** sezione il **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="f464e-288">Expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="f464e-289">Scegliere il **+** sul lato destro per aggiungere una nuova parola chiave.</span><span class="sxs-lookup"><span data-stu-id="f464e-289">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="f464e-290">Digitare la parola chiave as **spostare astronautici**.</span><span class="sxs-lookup"><span data-stu-id="f464e-290">Type the Keyword as **Move Astronaut**.</span></span> <span data-ttu-id="f464e-291">È possibile aggiungere un tasto di scelta rapida se si desidera.</span><span class="sxs-lookup"><span data-stu-id="f464e-291">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="f464e-292">Scegliere il **+** sul lato destro per aggiungere una nuova parola chiave.</span><span class="sxs-lookup"><span data-stu-id="f464e-292">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="f464e-293">Digitare la parola chiave as **ruotare astronautici**.</span><span class="sxs-lookup"><span data-stu-id="f464e-293">Type the Keyword as **Rotate Astronaut**.</span></span> <span data-ttu-id="f464e-294">È possibile aggiungere un tasto di scelta rapida se si desidera.</span><span class="sxs-lookup"><span data-stu-id="f464e-294">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="f464e-295">Il codice del gestore corrispondente è reperibile nel **GestureAction.cs**, nella **ISpeechHandler.OnSpeechKeywordRecognized** gestore.</span><span class="sxs-lookup"><span data-stu-id="f464e-295">The corresponding handler code can be found in **GestureAction.cs**, in the **ISpeechHandler.OnSpeechKeywordRecognized** handler.</span></span>

![Come configurare l'origine di Input vocale per capitolo 4](images/holograms211-speech.png)

<span data-ttu-id="f464e-297">Si verranno successivamente, configurare i commenti e suggerimenti di manipolazione sul cursore.</span><span class="sxs-lookup"><span data-stu-id="f464e-297">Next, we'll setup the manipulation feedback on the cursor.</span></span>

1. <span data-ttu-id="f464e-298">Nel **Project** pannello **Vntana** cartella trovare il **PathingFeedback** asset.</span><span class="sxs-lookup"><span data-stu-id="f464e-298">In the **Project** panel **Holograms** folder, find the **PathingFeedback** asset.</span></span>
2. <span data-ttu-id="f464e-299">Trascinare e rilasciare il **PathingFeedback** prefab nel **CursorWithFeedback** dell'oggetto nel **gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="f464e-299">Drag and drop the **PathingFeedback** prefab onto the **CursorWithFeedback** object in the **Hierarchy**.</span></span>
3. <span data-ttu-id="f464e-300">Nel **gerarchia** del pannello, fare clic su **CursorWithFeedback**.</span><span class="sxs-lookup"><span data-stu-id="f464e-300">In the **Hierarchy** panel, click on **CursorWithFeedback**.</span></span>
4. <span data-ttu-id="f464e-301">Trascinare e rilasciare il **PathingFeedback** dall'oggetto il **gerarchia** nel **ricerca del percorso rilevato Game Object** proprietà nel **risposta del cursore**nel componente di **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="f464e-301">Drag and drop the **PathingFeedback** object from the **Hierarchy** onto the **Pathing Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>

<span data-ttu-id="f464e-302">È ora necessario aggiungere codice al **GestureAction.cs** per abilitare le opzioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="f464e-302">Now we need to add code to **GestureAction.cs** to enable the following:</span></span>

1. <span data-ttu-id="f464e-303">Aggiungere il codice per il **IManipulationHandler.OnManipulationUpdated** funzione, che verrà spostato l'astronautici quando una **manipolazione** viene rilevato movimento.</span><span class="sxs-lookup"><span data-stu-id="f464e-303">Add code to the **IManipulationHandler.OnManipulationUpdated** function, which will move the astronaut when a **Manipulation** gesture is detected.</span></span>
2. <span data-ttu-id="f464e-304">Calcolare le **vettore di movimento** per determinare dove devono essere spostati gli astronautici basato d' parte posizione.</span><span class="sxs-lookup"><span data-stu-id="f464e-304">Calculate the **movement vector** to determine where the astronaut should be moved to based on hand position.</span></span>
3. <span data-ttu-id="f464e-305">**Spostare** l'astronautici nella nuova posizione.</span><span class="sxs-lookup"><span data-stu-id="f464e-305">**Move** the astronaut to the new position.</span></span>

<span data-ttu-id="f464e-306">Scrittura di codice completo esercitare 4.a nel **GestureAction.cs**, oppure usare la nostra soluzione completata riportato di seguito:</span><span class="sxs-lookup"><span data-stu-id="f464e-306">Complete coding exercise 4.a in **GestureAction.cs**, or use our completed solution below:</span></span>

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
            transform.position = manipulationOriginalPosition + eventData.CumulativeDelta;
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

### <a name="build-and-deploy"></a><span data-ttu-id="f464e-307">Compilare e distribuire</span><span class="sxs-lookup"><span data-stu-id="f464e-307">Build and Deploy</span></span>

* <span data-ttu-id="f464e-308">Ricompilazione in Unity e quindi compilare e distribuire da Visual Studio per eseguire l'app in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f464e-308">Rebuild in Unity and then build and deploy from Visual Studio to run the app in HoloLens.</span></span>
* <span data-ttu-id="f464e-309">Spostare la mano davanti il HoloLens e generare il dito indice in modo che sia possibile il rilevamento.</span><span class="sxs-lookup"><span data-stu-id="f464e-309">Move your hand in front of the HoloLens and raise your index finger so that it can be tracked.</span></span>
* <span data-ttu-id="f464e-310">Lo stato attivo del cursore tramite l'astronautici.</span><span class="sxs-lookup"><span data-stu-id="f464e-310">Focus the cursor over the astronaut.</span></span>
* <span data-ttu-id="f464e-311">Ad esempio 'Spostare astronautici' per spostare l'astronautici con un gesto di manipolazione.</span><span class="sxs-lookup"><span data-stu-id="f464e-311">Say 'Move Astronaut' to move the astronaut with a Manipulation gesture.</span></span>
* <span data-ttu-id="f464e-312">Quattro frecce apparirà attorno al cursore per indicare che il programma ora risponderanno a eventi di manipolazione.</span><span class="sxs-lookup"><span data-stu-id="f464e-312">Four arrows should appear around the cursor to indicate that the program will now respond to Manipulation events.</span></span>
* <span data-ttu-id="f464e-313">Ridurre il dito indice down il pollice e mantenerli estratte insieme.</span><span class="sxs-lookup"><span data-stu-id="f464e-313">Lower your index finger down to your thumb, and keep them pinched together.</span></span>
* <span data-ttu-id="f464e-314">Quando si sposta la mano tutto, l'astronautici sposterà troppo (si tratta di modifica).</span><span class="sxs-lookup"><span data-stu-id="f464e-314">As you move your hand around, the astronaut will move too (this is Manipulation).</span></span>
* <span data-ttu-id="f464e-315">Generare il dito indice per interrompere la modifica di astronautici.</span><span class="sxs-lookup"><span data-stu-id="f464e-315">Raise your index finger to stop manipulating the astronaut.</span></span>
* <span data-ttu-id="f464e-316">Nota: Se non dirà piuttosto 'Spostare astronautici' prima di spostare la mano verrà invece utilizzato il movimento di navigazione.</span><span class="sxs-lookup"><span data-stu-id="f464e-316">Note: If you do not say 'Move Astronaut' before moving your hand, then the Navigation gesture will be used instead.</span></span>
* <span data-ttu-id="f464e-317">Ad esempio 'Ruotare astronautici' per tornare allo stato orientamento modificabile.</span><span class="sxs-lookup"><span data-stu-id="f464e-317">Say 'Rotate Astronaut' to return to the rotatable state.</span></span>

## <a name="chapter-5---model-expansion"></a><span data-ttu-id="f464e-318">Capitolo 5: espansione del modello</span><span class="sxs-lookup"><span data-stu-id="f464e-318">Chapter 5 - Model expansion</span></span>

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a><span data-ttu-id="f464e-319">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="f464e-319">Objectives</span></span>

* <span data-ttu-id="f464e-320">Espandere il modello astronautici in più, componenti più piccoli che l'utente può interagire con.</span><span class="sxs-lookup"><span data-stu-id="f464e-320">Expand the Astronaut model into multiple, smaller pieces that the user can interact with.</span></span>
* <span data-ttu-id="f464e-321">Spostare ogni componente singolarmente utilizzando i movimenti di navigazione e modifica.</span><span class="sxs-lookup"><span data-stu-id="f464e-321">Move each piece individually using Navigation and Manipulation gestures.</span></span>

### <a name="instructions"></a><span data-ttu-id="f464e-322">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="f464e-322">Instructions</span></span>

<span data-ttu-id="f464e-323">In questa sezione, si completeranno le attività seguenti:</span><span class="sxs-lookup"><span data-stu-id="f464e-323">In this section, we will accomplish the following tasks:</span></span>

1. <span data-ttu-id="f464e-324">Aggiungere una nuova parola chiave "**modello espandere**" per espandere il modello astronautici.</span><span class="sxs-lookup"><span data-stu-id="f464e-324">Add a new keyword "**Expand Model**" to expand the astronaut model.</span></span>
2. <span data-ttu-id="f464e-325">Aggiungere una nuova parola chiave "**reimpostare modello**" per restituire il modello nel formato originale.</span><span class="sxs-lookup"><span data-stu-id="f464e-325">Add a new Keyword "**Reset Model**" to return the model to its original form.</span></span>

<span data-ttu-id="f464e-326">Faremo mediante l'aggiunta di due più parole chiave per l'origine di Input vocale nel capitolo precedente.</span><span class="sxs-lookup"><span data-stu-id="f464e-326">We'll do this by adding two more keywords to the Speech Input Source from the previous chapter.</span></span> <span data-ttu-id="f464e-327">Illustreremo anche un altro modo per gestire gli eventi di riconoscimento.</span><span class="sxs-lookup"><span data-stu-id="f464e-327">We'll also demonstrate another way to handle recognition events.</span></span>

1. <span data-ttu-id="f464e-328">Fare clic nuovamente sul **AstronautManager** nel **Inspector** ed espandere il **parole chiave** sezione la **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="f464e-328">Click back on **AstronautManager** in the **Inspector** and expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="f464e-329">Scegliere il **+** sul lato destro per aggiungere una nuova parola chiave.</span><span class="sxs-lookup"><span data-stu-id="f464e-329">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="f464e-330">Digitare la parola chiave as **espande modello**.</span><span class="sxs-lookup"><span data-stu-id="f464e-330">Type the Keyword as **Expand Model**.</span></span> <span data-ttu-id="f464e-331">È possibile aggiungere un tasto di scelta rapida se si desidera.</span><span class="sxs-lookup"><span data-stu-id="f464e-331">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="f464e-332">Scegliere il **+** sul lato destro per aggiungere una nuova parola chiave.</span><span class="sxs-lookup"><span data-stu-id="f464e-332">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="f464e-333">Digitare la parola chiave as **reimpostare modello**.</span><span class="sxs-lookup"><span data-stu-id="f464e-333">Type the Keyword as **Reset Model**.</span></span> <span data-ttu-id="f464e-334">È possibile aggiungere un tasto di scelta rapida se si desidera.</span><span class="sxs-lookup"><span data-stu-id="f464e-334">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="f464e-335">Nel **Inspector** del pannello, fare clic sui **Add Component** pulsante.</span><span class="sxs-lookup"><span data-stu-id="f464e-335">In the **Inspector** panel, click the **Add Component** button.</span></span>
7. <span data-ttu-id="f464e-336">Nel menu, digitare nella casella di ricerca **gestore di Input vocale**.</span><span class="sxs-lookup"><span data-stu-id="f464e-336">In the menu, type in the search box **Speech Input Handler**.</span></span> <span data-ttu-id="f464e-337">Selezionare il risultato della ricerca.</span><span class="sxs-lookup"><span data-stu-id="f464e-337">Select the search result.</span></span>
8. <span data-ttu-id="f464e-338">Controllare **Listener globale è**, dal momento che intendiamo utilizzare questi comandi al indipendentemente dal fatto il GameObject parliamo.</span><span class="sxs-lookup"><span data-stu-id="f464e-338">Check **Is Global Listener**, since we want these commands to work regardless of the GameObject we're focusing.</span></span>
9. <span data-ttu-id="f464e-339">Scegliere il **+** e selezionare **espandere modello** dall'elenco a discesa parola chiave.</span><span class="sxs-lookup"><span data-stu-id="f464e-339">Click the **+** button and select **Expand Model** from the Keyword dropdown.</span></span>
10. <span data-ttu-id="f464e-340">Fare clic sui **+** nella risposta e quindi trascinare il **AstronautManager** dal **gerarchia** nel **None (oggetto)** campo.</span><span class="sxs-lookup"><span data-stu-id="f464e-340">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
11. <span data-ttu-id="f464e-341">A questo punto, fare clic sui **funzione No** elenco a discesa, seleziona **AstronautManager**, quindi **ExpandModelCommand**.</span><span class="sxs-lookup"><span data-stu-id="f464e-341">Now, click the **No Function** dropdown, select **AstronautManager**, then **ExpandModelCommand**.</span></span>
12. <span data-ttu-id="f464e-342">Scegliere il gestore di Input vocale **+** e selezionare **reimpostazione modello** dall'elenco a discesa parola chiave.</span><span class="sxs-lookup"><span data-stu-id="f464e-342">Click the Speech Input Handler's **+** button and select **Reset Model** from the Keyword dropdown.</span></span>
13. <span data-ttu-id="f464e-343">Fare clic sui **+** nella risposta e quindi trascinare il **AstronautManager** dal **gerarchia** nel **None (oggetto)** campo.</span><span class="sxs-lookup"><span data-stu-id="f464e-343">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
14. <span data-ttu-id="f464e-344">A questo punto, fare clic sui **funzione No** elenco a discesa, seleziona **AstronautManager**, quindi **ResetModelCommand**.</span><span class="sxs-lookup"><span data-stu-id="f464e-344">Now, click the **No Function** dropdown, select **AstronautManager**, then **ResetModelCommand**.</span></span>

![Come configurare l'origine di Input vocale e gestore per il capitolo 5](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a><span data-ttu-id="f464e-346">Compilare e distribuire</span><span class="sxs-lookup"><span data-stu-id="f464e-346">Build and Deploy</span></span>

* <span data-ttu-id="f464e-347">Prova!</span><span class="sxs-lookup"><span data-stu-id="f464e-347">Try it!</span></span> <span data-ttu-id="f464e-348">Compilare e distribuire l'app per la HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f464e-348">Build and deploy the app to the HoloLens.</span></span>
* <span data-ttu-id="f464e-349">Pronunciare **modello espandere** per visualizzare il modello astronautici espanso.</span><span class="sxs-lookup"><span data-stu-id="f464e-349">Say **Expand Model** to see the expanded astronaut model.</span></span>
* <span data-ttu-id="f464e-350">Uso **navigazione** ruotare singole parti del seme astronautici.</span><span class="sxs-lookup"><span data-stu-id="f464e-350">Use **Navigation** to rotate individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="f464e-351">Pronunciare **spostare astronautici** e quindi usare **manipolazione** spostare singole parti del seme astronautici.</span><span class="sxs-lookup"><span data-stu-id="f464e-351">Say **Move Astronaut** and then use **Manipulation** to move individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="f464e-352">Pronunciare **ruotare astronautici** per ruotare le parti nuovamente.</span><span class="sxs-lookup"><span data-stu-id="f464e-352">Say **Rotate Astronaut** to rotate the pieces again.</span></span>
* <span data-ttu-id="f464e-353">Pronunciare **reimpostare modello** per restituire l'astronautici nel formato originale.</span><span class="sxs-lookup"><span data-stu-id="f464e-353">Say **Reset Model** to return the astronaut to its original form.</span></span>

## <a name="the-end"></a><span data-ttu-id="f464e-354">La fine</span><span class="sxs-lookup"><span data-stu-id="f464e-354">The End</span></span>

<span data-ttu-id="f464e-355">La procedura è stata completata.</span><span class="sxs-lookup"><span data-stu-id="f464e-355">Congratulations!</span></span> <span data-ttu-id="f464e-356">Sono stati completati **SIG Input 211: Movimento**.</span><span class="sxs-lookup"><span data-stu-id="f464e-356">You have now completed **MR Input 211: Gesture**.</span></span>

* <span data-ttu-id="f464e-357">Sai come rilevare e rispondere per presentare gli eventi di rilevamento, navigazione e modifica.</span><span class="sxs-lookup"><span data-stu-id="f464e-357">You know how to detect and respond to hand tracking, navigation and manipulation events.</span></span>
* <span data-ttu-id="f464e-358">Comprendere la differenza tra i movimenti di navigazione e modifica.</span><span class="sxs-lookup"><span data-stu-id="f464e-358">You understand the difference between Navigation and Manipulation gestures.</span></span>
* <span data-ttu-id="f464e-359">Si sa come modificare il cursore per fornire indicazioni visive per quando viene rilevata una mano, quando una mano sta per essere perso e quando un oggetto supporta diverse interazioni (spostamento vs manipolazione).</span><span class="sxs-lookup"><span data-stu-id="f464e-359">You know how to change the cursor to provide visual feedback for when a hand is detected, when a hand is about to be lost, and for when an object supports different interactions (Navigation vs Manipulation).</span></span>

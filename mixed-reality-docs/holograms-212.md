---
title: Input MR 212-Voice
description: Seguire questa procedura dettagliata di codifica usando Unity, Visual Studio e HoloLens per informazioni dettagliate sui concetti vocali.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academy, esercitazione, Voice
ms.openlocfilehash: 9db503ea4c7db9a3eb272ad9663024ca3a407dda
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434594"
---
>[!NOTE]
><span data-ttu-id="c455d-104">Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.</span><span class="sxs-lookup"><span data-stu-id="c455d-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="c455d-105">Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.</span><span class="sxs-lookup"><span data-stu-id="c455d-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="c455d-106">Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="c455d-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="c455d-107">Verranno mantenuti per continuare a usare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="c455d-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="c455d-108">Per HoloLens 2 è stata pubblicata [una nuova serie di esercitazioni](mrlearning-base.md) .</span><span class="sxs-lookup"><span data-stu-id="c455d-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

# <a name="mr-input-212-voice"></a><span data-ttu-id="c455d-109">Input di MR 212: Voice</span><span class="sxs-lookup"><span data-stu-id="c455d-109">MR Input 212: Voice</span></span>

<span data-ttu-id="c455d-110">L' [input vocale](voice-input.md) ci offre un altro modo per interagire con gli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="c455d-110">[Voice input](voice-input.md) gives us another way to interact with our holograms.</span></span> <span data-ttu-id="c455d-111">I comandi vocali funzionano in modo molto naturale e semplice.</span><span class="sxs-lookup"><span data-stu-id="c455d-111">Voice commands work in a very natural and easy way.</span></span> <span data-ttu-id="c455d-112">Progettare i comandi vocali in modo che siano:</span><span class="sxs-lookup"><span data-stu-id="c455d-112">Design your voice commands so that they are:</span></span>

* <span data-ttu-id="c455d-113">Naturale</span><span class="sxs-lookup"><span data-stu-id="c455d-113">Natural</span></span>
* <span data-ttu-id="c455d-114">Facile da ricordare</span><span class="sxs-lookup"><span data-stu-id="c455d-114">Easy to remember</span></span>
* <span data-ttu-id="c455d-115">Contesto appropriato</span><span class="sxs-lookup"><span data-stu-id="c455d-115">Context appropriate</span></span>
* <span data-ttu-id="c455d-116">Sufficientemente distinto dalle altre opzioni nello stesso contesto</span><span class="sxs-lookup"><span data-stu-id="c455d-116">Sufficiently distinct from other options within the same context</span></span>

>[!VIDEO https://www.youtube.com/embed/BYpYsVFYjdw]

<span data-ttu-id="c455d-117">In [Mr nozioni di base 101](holograms-101.md)è stato usato KeywordRecognizer per creare due semplici comandi vocali.</span><span class="sxs-lookup"><span data-stu-id="c455d-117">In [MR Basics 101](holograms-101.md), we used the KeywordRecognizer to build two simple voice commands.</span></span> <span data-ttu-id="c455d-118">In MR input 212 verrà illustrato in dettaglio come:</span><span class="sxs-lookup"><span data-stu-id="c455d-118">In MR Input 212, we'll dive deeper and learn how to:</span></span>

* <span data-ttu-id="c455d-119">Progettare comandi vocali ottimizzati per il motore di sintesi vocale HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c455d-119">Design voice commands that are optimized for the HoloLens speech engine.</span></span>
* <span data-ttu-id="c455d-120">Informare l'utente di quali comandi vocali sono disponibili.</span><span class="sxs-lookup"><span data-stu-id="c455d-120">Make the user aware of what voice commands are available.</span></span>
* <span data-ttu-id="c455d-121">Confermare che è stato ascoltato il comando Voice dell'utente.</span><span class="sxs-lookup"><span data-stu-id="c455d-121">Acknowledge that we've heard the user's voice command.</span></span>
* <span data-ttu-id="c455d-122">Comprendere le informazioni che l'utente sta dicendo, usando un riconoscimento di dettatura.</span><span class="sxs-lookup"><span data-stu-id="c455d-122">Understand what the user is saying, using a Dictation Recognizer.</span></span>
* <span data-ttu-id="c455d-123">Usare un sistema di riconoscimento della grammatica per restare in ascolto dei comandi basati su un file SRGS o una specifica della grammatica del riconoscimento vocale.</span><span class="sxs-lookup"><span data-stu-id="c455d-123">Use a Grammar Recognizer to listen for commands based on an SRGS, or Speech Recognition Grammar Specification, file.</span></span>

<span data-ttu-id="c455d-124">In questo corso, viene rivisitata Esplora modelli, che è stata compilata in [Mr input 210](holograms-210.md) e [Mr input 211](holograms-211.md).</span><span class="sxs-lookup"><span data-stu-id="c455d-124">In this course, we'll revisit Model Explorer, which we built in [MR Input 210](holograms-210.md) and [MR Input 211](holograms-211.md).</span></span>

>[!IMPORTANT]
><span data-ttu-id="c455d-125">I video incorporati in ognuno dei capitoli seguenti sono stati registrati usando una versione precedente di Unity e il Toolkit di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="c455d-125">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="c455d-126">Sebbene le istruzioni dettagliate siano accurate e aggiornate, è possibile visualizzare gli script e gli oggetti visivi nei video corrispondenti non aggiornati.</span><span class="sxs-lookup"><span data-stu-id="c455d-126">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="c455d-127">I video rimangono inclusi per i posteri e perché i concetti trattati sono ancora validi.</span><span class="sxs-lookup"><span data-stu-id="c455d-127">The videos remain included for posterity and because the concepts covered still apply.</span></span>


## <a name="device-support"></a><span data-ttu-id="c455d-128">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="c455d-128">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="c455d-129">Corso</span><span class="sxs-lookup"><span data-stu-id="c455d-129">Course</span></span></th><th style="width:150px"> <span data-ttu-id="c455d-130"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="c455d-130"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="c455d-131"><a href="immersive-headset-hardware-details.md">Visori VR immersive</a></span><span class="sxs-lookup"><span data-stu-id="c455d-131"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="c455d-132">Input di MR 212: Voice</span><span class="sxs-lookup"><span data-stu-id="c455d-132">MR Input 212: Voice</span></span></td><td style="text-align: center;"> <span data-ttu-id="c455d-133">✔️</span><span class="sxs-lookup"><span data-stu-id="c455d-133">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="c455d-134">✔️</span><span class="sxs-lookup"><span data-stu-id="c455d-134">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="c455d-135">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="c455d-135">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="c455d-136">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="c455d-136">Prerequisites</span></span>

* <span data-ttu-id="c455d-137">Un PC Windows 10 configurato con gli [strumenti corretti installati](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="c455d-137">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="c455d-138">Alcune funzionalità C# di programmazione di base.</span><span class="sxs-lookup"><span data-stu-id="c455d-138">Some basic C# programming ability.</span></span>
* <span data-ttu-id="c455d-139">Sono state completate le [nozioni di base 101](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="c455d-139">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="c455d-140">È necessario aver completato il [sig. Input 210](holograms-210.md).</span><span class="sxs-lookup"><span data-stu-id="c455d-140">You should have completed [MR Input 210](holograms-210.md).</span></span>
* <span data-ttu-id="c455d-141">È necessario aver completato il [sig. Input 211](holograms-211.md).</span><span class="sxs-lookup"><span data-stu-id="c455d-141">You should have completed [MR Input 211](holograms-211.md).</span></span>
* <span data-ttu-id="c455d-142">Un dispositivo HoloLens [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="c455d-142">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="c455d-143">File di progetto</span><span class="sxs-lookup"><span data-stu-id="c455d-143">Project files</span></span>

* <span data-ttu-id="c455d-144">Scaricare i [file](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) richiesti dal progetto.</span><span class="sxs-lookup"><span data-stu-id="c455d-144">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) required by the project.</span></span> <span data-ttu-id="c455d-145">Richiede Unity 2017,2 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="c455d-145">Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="c455d-146">Annullare l'archiviazione dei file sul desktop o in un'altra posizione facile da raggiungere.</span><span class="sxs-lookup"><span data-stu-id="c455d-146">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="c455d-147">Se si vuole esaminare il codice sorgente prima del download, è [disponibile in GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).</span><span class="sxs-lookup"><span data-stu-id="c455d-147">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="c455d-148">Errori e note</span><span class="sxs-lookup"><span data-stu-id="c455d-148">Errata and Notes</span></span>

* <span data-ttu-id="c455d-149">"Enable Just My Code" deve essere disabilitato (*deselezionato*) in Visual Studio in strumenti-Opzioni >-> debug per raggiungere i punti di interruzione nel codice.</span><span class="sxs-lookup"><span data-stu-id="c455d-149">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="unity-setup"></a><span data-ttu-id="c455d-150">Configurazione di Unity</span><span class="sxs-lookup"><span data-stu-id="c455d-150">Unity Setup</span></span>

### <a name="instructions"></a><span data-ttu-id="c455d-151">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="c455d-151">Instructions</span></span>

1. <span data-ttu-id="c455d-152">Avvia Unity.</span><span class="sxs-lookup"><span data-stu-id="c455d-152">Start Unity.</span></span>
2. <span data-ttu-id="c455d-153">Selezionare **Apri**.</span><span class="sxs-lookup"><span data-stu-id="c455d-153">Select **Open**.</span></span>
3. <span data-ttu-id="c455d-154">Passare alla cartella **HolographicAcademy-ologrammes-212-Voice** precedentemente non archiviata.</span><span class="sxs-lookup"><span data-stu-id="c455d-154">Navigate to the **HolographicAcademy-Holograms-212-Voice** folder you previously un-archived.</span></span>
4. <span data-ttu-id="c455d-155">Individuare e selezionare la cartella **avvio**/**Esplora modelli** .</span><span class="sxs-lookup"><span data-stu-id="c455d-155">Find and select the **Starting**/**Model Explorer** folder.</span></span>
5. <span data-ttu-id="c455d-156">Fare clic sul pulsante **Seleziona cartella** .</span><span class="sxs-lookup"><span data-stu-id="c455d-156">Click the **Select Folder** button.</span></span>
6. <span data-ttu-id="c455d-157">Nel pannello **progetto** espandere la cartella **Scenes** .</span><span class="sxs-lookup"><span data-stu-id="c455d-157">In the **Project** panel, expand the **Scenes** folder.</span></span>
7. <span data-ttu-id="c455d-158">Fare doppio clic su **ModelExplorer** scene per caricarla in Unity.</span><span class="sxs-lookup"><span data-stu-id="c455d-158">Double-click **ModelExplorer** scene to load it in Unity.</span></span>

### <a name="building"></a><span data-ttu-id="c455d-159">Build</span><span class="sxs-lookup"><span data-stu-id="c455d-159">Building</span></span>

1. <span data-ttu-id="c455d-160">In Unity selezionare **File > impostazioni di compilazione**.</span><span class="sxs-lookup"><span data-stu-id="c455d-160">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="c455d-161">Se **Scenes/ModelExplorer** non è elencato in **Scenes in Build**, fare clic su **Aggiungi scene aperte** per aggiungere la scena.</span><span class="sxs-lookup"><span data-stu-id="c455d-161">If **Scenes/ModelExplorer** is not listed in **Scenes In Build**, click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="c455d-162">Se si sta sviluppando in modo specifico per HoloLens, impostare **dispositivo di destinazione** su **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="c455d-162">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="c455d-163">In caso contrario, lasciarlo in **qualsiasi dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="c455d-163">Otherwise, leave it on **Any device**.</span></span>
4. <span data-ttu-id="c455d-164">Verificare che **tipo di compilazione** sia impostato su **D3D** e che l' **SDK** sia impostato su **installato più recente** (che deve essere SDK 16299 o versione successiva).</span><span class="sxs-lookup"><span data-stu-id="c455d-164">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
5. <span data-ttu-id="c455d-165">Fai clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="c455d-165">Click **Build**.</span></span>
6. <span data-ttu-id="c455d-166">Creare una **nuova cartella** denominata "app".</span><span class="sxs-lookup"><span data-stu-id="c455d-166">Create a **New Folder** named "App".</span></span>
7. <span data-ttu-id="c455d-167">Fare clic sulla cartella dell' **app** .</span><span class="sxs-lookup"><span data-stu-id="c455d-167">Single click the **App** folder.</span></span>
8. <span data-ttu-id="c455d-168">Premere **Seleziona cartella** e Unity avvierà la compilazione del progetto per Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c455d-168">Press **Select Folder** and Unity will start building the project for Visual Studio.</span></span>

<span data-ttu-id="c455d-169">Quando si esegue Unity, viene visualizzata una finestra Esplora file.</span><span class="sxs-lookup"><span data-stu-id="c455d-169">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="c455d-170">Aprire la cartella dell' **app** .</span><span class="sxs-lookup"><span data-stu-id="c455d-170">Open the **App** folder.</span></span>
2. <span data-ttu-id="c455d-171">Aprire la **soluzione ModelExplorer di Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="c455d-171">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="c455d-172">Se si esegue la distribuzione in HoloLens:</span><span class="sxs-lookup"><span data-stu-id="c455d-172">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="c455d-173">Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione da debug a **Release** e da ARM a **x86**.</span><span class="sxs-lookup"><span data-stu-id="c455d-173">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="c455d-174">Fare clic sulla freccia a discesa accanto al pulsante computer locale e selezionare **computer remoto**.</span><span class="sxs-lookup"><span data-stu-id="c455d-174">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="c455d-175">Immettere **l'indirizzo IP del dispositivo HoloLens** e impostare la modalità di autenticazione su **universale (protocollo non crittografato)** .</span><span class="sxs-lookup"><span data-stu-id="c455d-175">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="c455d-176">Fare clic su **Seleziona**.</span><span class="sxs-lookup"><span data-stu-id="c455d-176">Click **Select**.</span></span> <span data-ttu-id="c455d-177">Se non si conosce l'indirizzo IP del dispositivo, vedere **impostazioni > rete & Internet > opzioni avanzate**.</span><span class="sxs-lookup"><span data-stu-id="c455d-177">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="c455d-178">Nella barra dei menu superiore fare clic su **debug-> avvia senza eseguire debug** o premere **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="c455d-178">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="c455d-179">Se questa è la prima volta che si esegue la distribuzione nel dispositivo, sarà necessario [associarla a Visual Studio](using-visual-studio.md#pairing-your-device).</span><span class="sxs-lookup"><span data-stu-id="c455d-179">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device).</span></span>
5. <span data-ttu-id="c455d-180">Quando l'app è stata distribuita, chiudere il **fitbox** con un **movimento di selezione**.</span><span class="sxs-lookup"><span data-stu-id="c455d-180">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="c455d-181">Se si esegue la distribuzione in un auricolare immersivo:</span><span class="sxs-lookup"><span data-stu-id="c455d-181">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="c455d-182">Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione da debug a **Release** e da ARM a **x64**.</span><span class="sxs-lookup"><span data-stu-id="c455d-182">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="c455d-183">Verificare che la destinazione di distribuzione sia impostata su **computer locale**.</span><span class="sxs-lookup"><span data-stu-id="c455d-183">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="c455d-184">Nella barra dei menu superiore fare clic su **debug-> avvia senza eseguire debug** o premere **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="c455d-184">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="c455d-185">Quando l'app è stata distribuita, chiudere il **fitbox** estraendo il trigger in un controller di movimento.</span><span class="sxs-lookup"><span data-stu-id="c455d-185">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

>[!NOTE]
><span data-ttu-id="c455d-186">Si potrebbero notare alcuni errori rossi nel pannello Errori di Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c455d-186">You might notice some red errors in the Visual Studio Errors panel.</span></span> <span data-ttu-id="c455d-187">È possibile ignorarli.</span><span class="sxs-lookup"><span data-stu-id="c455d-187">It is safe to ignore them.</span></span> <span data-ttu-id="c455d-188">Passare al pannello output per visualizzare lo stato di avanzamento della compilazione.</span><span class="sxs-lookup"><span data-stu-id="c455d-188">Switch to the Output panel to view actual build progress.</span></span> <span data-ttu-id="c455d-189">Per gli errori nel pannello di output sarà necessario eseguire una correzione (la maggior parte delle volte è causata da un errore in uno script).</span><span class="sxs-lookup"><span data-stu-id="c455d-189">Errors in the Output panel will require you to make a fix (most often they are caused by a mistake in a script).</span></span>

## <a name="chapter-1---awareness"></a><span data-ttu-id="c455d-190">Capitolo 1-riconoscimento</span><span class="sxs-lookup"><span data-stu-id="c455d-190">Chapter 1 - Awareness</span></span>

>[!VIDEO https://www.youtube.com/embed/fDwijJWuEc0]

### <a name="objectives"></a><span data-ttu-id="c455d-191">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="c455d-191">Objectives</span></span>

* <span data-ttu-id="c455d-192">Informazioni su **DOS e non** sulla progettazione dei comandi vocali.</span><span class="sxs-lookup"><span data-stu-id="c455d-192">Learn the **Dos and Don'ts** of voice command design.</span></span>
* <span data-ttu-id="c455d-193">Usare **KeywordRecognizer** per aggiungere comandi vocali basati su sguardi.</span><span class="sxs-lookup"><span data-stu-id="c455d-193">Use **KeywordRecognizer** to add gaze based voice commands.</span></span>
* <span data-ttu-id="c455d-194">Consentire agli utenti di riconoscere i comandi vocali utilizzando il **feedback**del cursore.</span><span class="sxs-lookup"><span data-stu-id="c455d-194">Make users aware of voice commands using cursor **feedback**.</span></span>

### <a name="voice-command-design"></a><span data-ttu-id="c455d-195">Progettazione comando vocale</span><span class="sxs-lookup"><span data-stu-id="c455d-195">Voice Command Design</span></span>

<span data-ttu-id="c455d-196">In questo capitolo verrà illustrato come progettare comandi vocali.</span><span class="sxs-lookup"><span data-stu-id="c455d-196">In this chapter, you'll learn about designing voice commands.</span></span> <span data-ttu-id="c455d-197">Quando si creano comandi vocali:</span><span class="sxs-lookup"><span data-stu-id="c455d-197">When creating voice commands:</span></span>

#### <a name="do"></a><span data-ttu-id="c455d-198">DO</span><span class="sxs-lookup"><span data-stu-id="c455d-198">DO</span></span>

* <span data-ttu-id="c455d-199">Creare comandi concisi.</span><span class="sxs-lookup"><span data-stu-id="c455d-199">Create concise commands.</span></span> <span data-ttu-id="c455d-200">Non si vuole usare *"Riproduci il video attualmente selezionato"* , perché questo comando non è conciso e può essere facilmente dimenticato dall'utente.</span><span class="sxs-lookup"><span data-stu-id="c455d-200">You don't want to use *"Play the currently selected video"*, because that command is not concise and would easily be forgotten by the user.</span></span> <span data-ttu-id="c455d-201">È invece consigliabile usare: *"riprodurre video"* , perché è conciso e presenta più sillabe.</span><span class="sxs-lookup"><span data-stu-id="c455d-201">Instead, you should use: *"Play Video"*, because it is concise and has multiple syllables.</span></span>
* <span data-ttu-id="c455d-202">Usare un vocabolario semplice.</span><span class="sxs-lookup"><span data-stu-id="c455d-202">Use a simple vocabulary.</span></span> <span data-ttu-id="c455d-203">Provare sempre a usare parole e frasi comuni che possono essere facilmente individuate e memorizzate dall'utente.</span><span class="sxs-lookup"><span data-stu-id="c455d-203">Always try to use common words and phrases that are easy for the user to discover and remember.</span></span> <span data-ttu-id="c455d-204">Se, ad esempio, l'applicazione dispone di un oggetto nota che potrebbe essere visualizzato o nascosto, non è possibile utilizzare il comando *"Mostra cartello"* , perché "cartello" è un termine raramente utilizzato.</span><span class="sxs-lookup"><span data-stu-id="c455d-204">For example, if your application had a note object that could be displayed or hidden from view, you would not use the command *"Show Placard"*, because "placard" is a rarely used term.</span></span> <span data-ttu-id="c455d-205">Usare invece il comando: *"show note"* per rivelare la nota nell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="c455d-205">Instead, you would use the command: *"Show Note"*, to reveal the note in your application.</span></span>
* <span data-ttu-id="c455d-206">Mantenere la coerenza.</span><span class="sxs-lookup"><span data-stu-id="c455d-206">Be consistent.</span></span> <span data-ttu-id="c455d-207">I comandi vocali devono essere mantenuti coerenti nell'intera applicazione.</span><span class="sxs-lookup"><span data-stu-id="c455d-207">Voice commands should be kept consistent across your application.</span></span> <span data-ttu-id="c455d-208">Si supponga di avere due scene nell'applicazione e che entrambe le scene includano un pulsante per la chiusura dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="c455d-208">Imagine that you have two scenes in your application and both scenes contain a button for closing the application.</span></span> <span data-ttu-id="c455d-209">Se la prima scena usava il comando *"Exit"* per attivare il pulsante, ma la seconda scena usava il comando *"close app"* , l'utente sarà molto confuso.</span><span class="sxs-lookup"><span data-stu-id="c455d-209">If the first scene used the command *"Exit"* to trigger the button, but the second scene used the command *"Close App"*, then the user is going to get very confused.</span></span> <span data-ttu-id="c455d-210">Se la stessa funzionalità viene mantenute tra più scene, è necessario usare lo stesso comando Voice per attivarlo.</span><span class="sxs-lookup"><span data-stu-id="c455d-210">If the same functionality persists across multiple scenes, then the same voice command should be used to trigger it.</span></span>

#### <a name="dont"></a><span data-ttu-id="c455d-211">Non</span><span class="sxs-lookup"><span data-stu-id="c455d-211">DON'T</span></span>

* <span data-ttu-id="c455d-212">Usare i comandi a sillaba singola.</span><span class="sxs-lookup"><span data-stu-id="c455d-212">Use single syllable commands.</span></span> <span data-ttu-id="c455d-213">Ad esempio, se si crea un comando vocale per riprodurre un video, è consigliabile evitare di usare il semplice comando *"Play"* , poiché si tratta solo di una singola sillaba e potrebbe essere facilmente persa dal sistema.</span><span class="sxs-lookup"><span data-stu-id="c455d-213">As an example, if you were creating a voice command to play a video, you should avoid using the simple command *"Play"*, as it is only a single syllable and could easily be missed by the system.</span></span> <span data-ttu-id="c455d-214">È invece consigliabile usare: *"riprodurre video"* , perché è conciso e presenta più sillabe.</span><span class="sxs-lookup"><span data-stu-id="c455d-214">Instead, you should use: *"Play Video"*, because it is concise and has multiple syllables.</span></span>
* <span data-ttu-id="c455d-215">Usare i comandi di sistema.</span><span class="sxs-lookup"><span data-stu-id="c455d-215">Use system commands.</span></span> <span data-ttu-id="c455d-216">Il comando *"Select"* è riservato dal sistema per attivare un evento tap per l'oggetto attualmente attivo.</span><span class="sxs-lookup"><span data-stu-id="c455d-216">The *"Select"* command is reserved by the system to trigger a Tap event for the currently focused object.</span></span> <span data-ttu-id="c455d-217">Non usare nuovamente il comando *"Select"* in una parola chiave o in una frase, perché potrebbe non funzionare come previsto.</span><span class="sxs-lookup"><span data-stu-id="c455d-217">Do not re-use the *"Select"* command in a keyword or phrase, as it might not work as you expect.</span></span> <span data-ttu-id="c455d-218">Se, ad esempio, il comando Voice per la selezione di un cubo nell'applicazione era *"Select Cube"* , ma l'utente stava osservando una sfera quando ha pronunciato il comando, viene invece selezionata la sfera.</span><span class="sxs-lookup"><span data-stu-id="c455d-218">For example, if the voice command for selecting a cube in your application was *"Select cube"*, but the user was looking at a sphere when they uttered the command, then the sphere would be selected instead.</span></span> <span data-ttu-id="c455d-219">Analogamente, i comandi della barra dell'app sono abilitati.</span><span class="sxs-lookup"><span data-stu-id="c455d-219">Similarly app bar commands are voice enabled.</span></span> <span data-ttu-id="c455d-220">Non usare i comandi di riconoscimento vocale seguenti nella visualizzazione CoreWindow:</span><span class="sxs-lookup"><span data-stu-id="c455d-220">Don't use the following speech commands in your CoreWindow View:</span></span>
    1. <span data-ttu-id="c455d-221">Indietro</span><span class="sxs-lookup"><span data-stu-id="c455d-221">Go Back</span></span>
    2. <span data-ttu-id="c455d-222">Strumento di scorrimento</span><span class="sxs-lookup"><span data-stu-id="c455d-222">Scroll Tool</span></span>
    3. <span data-ttu-id="c455d-223">Strumento Zoom</span><span class="sxs-lookup"><span data-stu-id="c455d-223">Zoom Tool</span></span>
    4. <span data-ttu-id="c455d-224">Strumento di trascinamento</span><span class="sxs-lookup"><span data-stu-id="c455d-224">Drag Tool</span></span>
    5. <span data-ttu-id="c455d-225">Adjust</span><span class="sxs-lookup"><span data-stu-id="c455d-225">Adjust</span></span>
    6. <span data-ttu-id="c455d-226">Remove</span><span class="sxs-lookup"><span data-stu-id="c455d-226">Remove</span></span>
* <span data-ttu-id="c455d-227">Usare suoni simili.</span><span class="sxs-lookup"><span data-stu-id="c455d-227">Use similar sounds.</span></span> <span data-ttu-id="c455d-228">Provare a evitare di usare comandi vocali che fanno rima.</span><span class="sxs-lookup"><span data-stu-id="c455d-228">Try to avoid using voice commands that rhyme.</span></span> <span data-ttu-id="c455d-229">Se si dispone di un'applicazione di acquisto che supporta *"Mostra archivio"* e *"Mostra più"* come comandi vocali, è necessario disabilitare uno dei comandi mentre l'altro è in uso.</span><span class="sxs-lookup"><span data-stu-id="c455d-229">If you had a shopping application which supported *"Show Store"* and *"Show More"* as voice commands, then you would want to disable one of the commands while the other was in use.</span></span> <span data-ttu-id="c455d-230">Ad esempio, è possibile usare il pulsante *"Mostra archivio"* per aprire l'archivio e quindi disabilitare il comando quando l'archivio è stato visualizzato in modo che il comando *"Mostra più"* possa essere usato per l'esplorazione.</span><span class="sxs-lookup"><span data-stu-id="c455d-230">For example, you could use the *"Show Store"* button to open the store, and then disable that command when the store was displayed so that the *"Show More"* command could be used for browsing.</span></span>

### <a name="instructions"></a><span data-ttu-id="c455d-231">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="c455d-231">Instructions</span></span>

* <span data-ttu-id="c455d-232">Nel pannello **gerarchia** di Unity usare lo strumento di ricerca per trovare l'oggetto **holoComm_screen_mesh** .</span><span class="sxs-lookup"><span data-stu-id="c455d-232">In Unity's **Hierarchy** panel, use the search tool to find the **holoComm_screen_mesh** object.</span></span>
* <span data-ttu-id="c455d-233">Fare doppio clic sull'oggetto **holoComm_screen_mesh** per visualizzarlo nella **scena**.</span><span class="sxs-lookup"><span data-stu-id="c455d-233">Double-click on the **holoComm_screen_mesh** object to view it in the **Scene**.</span></span> <span data-ttu-id="c455d-234">Si tratta dell'espressione di controllo dell'astronauta, che risponderà ai comandi vocali.</span><span class="sxs-lookup"><span data-stu-id="c455d-234">This is the astronaut's watch, which will respond to our voice commands.</span></span>
* <span data-ttu-id="c455d-235">Nel pannello **Inspector** individuare il componente di **origine input vocale (script)** .</span><span class="sxs-lookup"><span data-stu-id="c455d-235">In the **Inspector** panel, locate the **Speech Input Source (Script)** component.</span></span>
* <span data-ttu-id="c455d-236">Espandere la sezione **Keywords (parole chiave** ) per visualizzare il comando Voice supportato: **Open Communicator**.</span><span class="sxs-lookup"><span data-stu-id="c455d-236">Expand the **Keywords** section to see the supported voice command: **Open Communicator**.</span></span>
* <span data-ttu-id="c455d-237">Fare clic sull'ingranaggio a destra, quindi selezionare **Modifica script**.</span><span class="sxs-lookup"><span data-stu-id="c455d-237">Click the cog to the right side, then select **Edit Script**.</span></span>
* <span data-ttu-id="c455d-238">Esplorare **SpeechInputSource.cs** per comprendere in che modo Usa **KeywordRecognizer** per aggiungere comandi vocali.</span><span class="sxs-lookup"><span data-stu-id="c455d-238">Explore **SpeechInputSource.cs** to understand how it uses the **KeywordRecognizer** to add voice commands.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="c455d-239">Compilazione e distribuzione</span><span class="sxs-lookup"><span data-stu-id="c455d-239">Build and Deploy</span></span>

* <span data-ttu-id="c455d-240">In Unity, usare **File > impostazioni di compilazione** per ricompilare l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="c455d-240">In Unity, use **File > Build Settings** to rebuild the application.</span></span>
* <span data-ttu-id="c455d-241">Aprire la cartella dell' **app** .</span><span class="sxs-lookup"><span data-stu-id="c455d-241">Open the **App** folder.</span></span>
* <span data-ttu-id="c455d-242">Aprire la **soluzione ModelExplorer di Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="c455d-242">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="c455d-243">Se il progetto è già stato compilato o distribuito in Visual Studio durante la configurazione, è possibile aprire l'istanza di VS e fare clic su' ricarica tutto ' quando richiesto.</span><span class="sxs-lookup"><span data-stu-id="c455d-243">(If you already built/deployed this project in Visual Studio during set-up, then you can open that instance of VS and click 'Reload All' when prompted).</span></span>

* <span data-ttu-id="c455d-244">In Visual Studio fare clic su **debug-> avvia senza eseguire debug** o premere **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="c455d-244">In Visual Studio, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="c455d-245">Dopo la distribuzione dell'applicazione in HoloLens, chiudere la casella adatta usando il gesto di [tocco](gaze-and-commit.md#composite-gestures) .</span><span class="sxs-lookup"><span data-stu-id="c455d-245">After the application deploys to the HoloLens, dismiss the fit box using the [air-tap](gaze-and-commit.md#composite-gestures) gesture.</span></span>
* <span data-ttu-id="c455d-246">Guarda l'orologio dell'astronauta.</span><span class="sxs-lookup"><span data-stu-id="c455d-246">Gaze at the astronaut's watch.</span></span>
* <span data-ttu-id="c455d-247">Quando l'espressione di controllo ha lo stato attivo, verificare che il cursore venga modificato in un microfono.</span><span class="sxs-lookup"><span data-stu-id="c455d-247">When the watch has focus, verify that the cursor changes to a microphone.</span></span> <span data-ttu-id="c455d-248">Questo fornisce il feedback che l'applicazione è in ascolto dei comandi vocali.</span><span class="sxs-lookup"><span data-stu-id="c455d-248">This provides feedback that the application is listening for voice commands.</span></span>
* <span data-ttu-id="c455d-249">Verificare che nell'espressione di controllo sia presente una descrizione comando.</span><span class="sxs-lookup"><span data-stu-id="c455d-249">Verify that a tooltip appears on the watch.</span></span> <span data-ttu-id="c455d-250">Questo consente agli utenti di individuare il comando *"Apri Communicator"* .</span><span class="sxs-lookup"><span data-stu-id="c455d-250">This helps users discover the *"Open Communicator"* command.</span></span>
* <span data-ttu-id="c455d-251">Quando si guarda l'orologio, si dice *"Apri Communicator"* per aprire il pannello Communicator.</span><span class="sxs-lookup"><span data-stu-id="c455d-251">While gazing at the watch, say *"Open Communicator"* to open the communicator panel.</span></span>

## <a name="chapter-2---acknowledgement"></a><span data-ttu-id="c455d-252">Capitolo 2-riconoscimento</span><span class="sxs-lookup"><span data-stu-id="c455d-252">Chapter 2 - Acknowledgement</span></span>

>[!VIDEO https://www.youtube.com/embed/87ViteoPpyU]

### <a name="objectives"></a><span data-ttu-id="c455d-253">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="c455d-253">Objectives</span></span>

* <span data-ttu-id="c455d-254">Registrare un messaggio usando l'input del microfono.</span><span class="sxs-lookup"><span data-stu-id="c455d-254">Record a message using the Microphone input.</span></span>
* <span data-ttu-id="c455d-255">Fornire un feedback all'utente che l'applicazione sta ascoltando la propria voce.</span><span class="sxs-lookup"><span data-stu-id="c455d-255">Give feedback to the user that the application is listening to their voice.</span></span>

>[!NOTE]
><span data-ttu-id="c455d-256">Per registrare un app dal microfono, è necessario dichiarare la funzionalità del **microfono** .</span><span class="sxs-lookup"><span data-stu-id="c455d-256">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="c455d-257">Questa operazione viene eseguita per l'utente già nell'input 212, ma è opportuno tenerla presente per i propri progetti.</span><span class="sxs-lookup"><span data-stu-id="c455d-257">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="c455d-258">Nell'editor di Unity passare a Impostazioni lettore passando a "Modifica > Impostazioni progetto > lettore"</span><span class="sxs-lookup"><span data-stu-id="c455d-258">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="c455d-259">Fare clic sulla scheda "piattaforma UWP (Universal Windows Platform)"</span><span class="sxs-lookup"><span data-stu-id="c455d-259">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="c455d-260">Nella sezione "impostazioni di pubblicazione > funzionalità" controllare la funzionalità del **microfono**</span><span class="sxs-lookup"><span data-stu-id="c455d-260">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="c455d-261">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="c455d-261">Instructions</span></span>

* <span data-ttu-id="c455d-262">Nel pannello **gerarchia** di Unity verificare che sia selezionato l'oggetto **holoComm_screen_mesh** .</span><span class="sxs-lookup"><span data-stu-id="c455d-262">In Unity's **Hierarchy** panel, verify that the **holoComm_screen_mesh** object is selected.</span></span>
* <span data-ttu-id="c455d-263">Nel pannello **Inspector** trovare il componente **Watch Astronaut (script)** .</span><span class="sxs-lookup"><span data-stu-id="c455d-263">In the **Inspector** panel, find the **Astronaut Watch (Script)** component.</span></span>
* <span data-ttu-id="c455d-264">Fare clic sul piccolo cubo blu che viene impostato come valore della proprietà **prefabbricata di Communicator** .</span><span class="sxs-lookup"><span data-stu-id="c455d-264">Click on the small, blue cube which is set as the value of the **Communicator Prefab** property.</span></span>
* <span data-ttu-id="c455d-265">Nel pannello del **progetto** , la prefabbricata di **Communicator** dovrebbe ora avere lo stato attivo.</span><span class="sxs-lookup"><span data-stu-id="c455d-265">In the **Project** panel, the **Communicator** prefab should now have focus.</span></span>
* <span data-ttu-id="c455d-266">Fare clic sul prefabbricato di **Communicator** nel pannello del **progetto** per visualizzare i relativi componenti nel **controllo**.</span><span class="sxs-lookup"><span data-stu-id="c455d-266">Click on the **Communicator** prefab in the **Project** panel to view its components in the **Inspector**.</span></span>
* <span data-ttu-id="c455d-267">Si osservi il componente **Microphone Manager (script)** , che consente di registrare la voce dell'utente.</span><span class="sxs-lookup"><span data-stu-id="c455d-267">Look at the **Microphone Manager (Script)** component, this will allow us to record the user's voice.</span></span>
* <span data-ttu-id="c455d-268">Si noti che l'oggetto **Communicator** dispone di un componente del **gestore di input vocale (script)** per rispondere al comando **Send Message** .</span><span class="sxs-lookup"><span data-stu-id="c455d-268">Notice that the **Communicator** object has a **Speech Input Handler (Script)** component for responding to the **Send Message** command.</span></span>
* <span data-ttu-id="c455d-269">Esaminare il componente **Communicator (script)** e fare doppio clic sullo script per aprirlo in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c455d-269">Look at the **Communicator (Script)** component and double-click on the script to open it in Visual Studio.</span></span>

<span data-ttu-id="c455d-270">Communicator.cs è responsabile dell'impostazione degli Stati dei pulsanti appropriati sul dispositivo Communicator.</span><span class="sxs-lookup"><span data-stu-id="c455d-270">Communicator.cs is responsible for setting the proper button states on the communicator device.</span></span> <span data-ttu-id="c455d-271">Questo consentirà agli utenti di registrare un messaggio, riprodurlo e inviare il messaggio all'astronauta.</span><span class="sxs-lookup"><span data-stu-id="c455d-271">This will allow our users to record a message, play it back, and send the message to the astronaut.</span></span> <span data-ttu-id="c455d-272">Verrà avviato e arrestato anche un modulo Wave animato, per confermare all'utente che la voce è stata ascoltata.</span><span class="sxs-lookup"><span data-stu-id="c455d-272">It will also start and stop an animated wave form, to acknowledge to the user that their voice was heard.</span></span>

* <span data-ttu-id="c455d-273">In **Communicator.cs**eliminare le righe seguenti (81 e 82) dal metodo **Start** .</span><span class="sxs-lookup"><span data-stu-id="c455d-273">In **Communicator.cs**, delete the following lines (81 and 82) from the **Start** method.</span></span> <span data-ttu-id="c455d-274">In questo modo verrà abilitato il pulsante "record" in Communicator.</span><span class="sxs-lookup"><span data-stu-id="c455d-274">This will enable the 'Record' button on the communicator.</span></span>

```cs
// TODO: 2.a Delete the following two lines:
RecordButton.SetActive(false);
MessageUIRenderer.gameObject.SetActive(false);
```

### <a name="build-and-deploy"></a><span data-ttu-id="c455d-275">Compilazione e distribuzione</span><span class="sxs-lookup"><span data-stu-id="c455d-275">Build and Deploy</span></span>

* <span data-ttu-id="c455d-276">In Visual Studio ricompilare l'applicazione e distribuirla nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c455d-276">In Visual Studio, rebuild your application and deploy to the device.</span></span>
* <span data-ttu-id="c455d-277">Guarda l'orologio dell'astronauta e pronuncia *"Open Communicator"* per visualizzare il Communicator.</span><span class="sxs-lookup"><span data-stu-id="c455d-277">Gaze at the astronaut's watch and say *"Open Communicator"* to show the communicator.</span></span>
* <span data-ttu-id="c455d-278">Premere il pulsante di **registrazione** (microfono) per avviare la registrazione di un messaggio verbale per l'astronauta.</span><span class="sxs-lookup"><span data-stu-id="c455d-278">Press the **Record** button (microphone) to start recording a verbal message for the astronaut.</span></span>
* <span data-ttu-id="c455d-279">Iniziare a parlare e verificare che l'animazione Wave riproduca sul Communicator, che fornisce commenti e suggerimenti all'utente per ascoltare la voce.</span><span class="sxs-lookup"><span data-stu-id="c455d-279">Start speaking, and verify that the wave animation plays on the communicator, which provides feedback to the user that their voice is heard.</span></span>
* <span data-ttu-id="c455d-280">Premere il pulsante **Interrompi** (riquadro a sinistra) e verificare che l'animazione Wave venga arrestata.</span><span class="sxs-lookup"><span data-stu-id="c455d-280">Press the **Stop** button (left square), and verify that the wave animation stops running.</span></span>
* <span data-ttu-id="c455d-281">Premere il pulsante **Play** (triangolo a destra) per riprodurre il messaggio registrato e ascoltarlo sul dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c455d-281">Press the **Play** button (right triangle) to play back the recorded message and hear it on the device.</span></span>
* <span data-ttu-id="c455d-282">Premere il pulsante **Arresta** (quadrato destro) per arrestare la riproduzione del messaggio registrato.</span><span class="sxs-lookup"><span data-stu-id="c455d-282">Press the **Stop** button (right square) to stop playback of the recorded message.</span></span>
* <span data-ttu-id="c455d-283">Pronunciare *"Send Message"* per chiudere il Communicator e ricevere una risposta "message received" dall'astronauta.</span><span class="sxs-lookup"><span data-stu-id="c455d-283">Say *"Send Message"* to close the communicator and receive a 'Message Received' response from the astronaut.</span></span>

## <a name="chapter-3---understanding-and-the-dictation-recognizer"></a><span data-ttu-id="c455d-284">Capitolo 3-informazioni e riconoscimento della dettatura</span><span class="sxs-lookup"><span data-stu-id="c455d-284">Chapter 3 - Understanding and the Dictation Recognizer</span></span>

>[!VIDEO https://www.youtube.com/embed/TIMddr-HqEU]

### <a name="objectives"></a><span data-ttu-id="c455d-285">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="c455d-285">Objectives</span></span>

* <span data-ttu-id="c455d-286">Usare il riconoscimento di dettatura per convertire il riconoscimento vocale dell'utente in testo.</span><span class="sxs-lookup"><span data-stu-id="c455d-286">Use the Dictation Recognizer to convert the user's speech to text.</span></span>
* <span data-ttu-id="c455d-287">Mostra i risultati finali e ipotizzati del riconoscimento di dettatura in Communicator.</span><span class="sxs-lookup"><span data-stu-id="c455d-287">Show the Dictation Recognizer's hypothesized and final results in the communicator.</span></span>

<span data-ttu-id="c455d-288">In questo capitolo verrà usato il riconoscimento di dettatura per creare un messaggio per l'astronauta.</span><span class="sxs-lookup"><span data-stu-id="c455d-288">In this chapter, we'll use the Dictation Recognizer to create a message for the astronaut.</span></span> <span data-ttu-id="c455d-289">Quando si usa il riconoscimento di dettatura, tenere presente quanto segue:</span><span class="sxs-lookup"><span data-stu-id="c455d-289">When using the Dictation Recognizer, keep in mind that:</span></span>

* <span data-ttu-id="c455d-290">È necessario essere connessi al Wi-Fi affinché il sistema di riconoscimento della dettatura funzioni.</span><span class="sxs-lookup"><span data-stu-id="c455d-290">You must be connected to WiFi for the Dictation Recognizer to work.</span></span>
* <span data-ttu-id="c455d-291">I timeout si verificano dopo un determinato periodo di tempo.</span><span class="sxs-lookup"><span data-stu-id="c455d-291">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="c455d-292">È necessario tenere presenti due timeout:</span><span class="sxs-lookup"><span data-stu-id="c455d-292">There are two timeouts to be aware of:</span></span>
  * <span data-ttu-id="c455d-293">Se il riconoscimento viene avviato e non viene sentito alcun audio per i primi cinque secondi, il timeout verrà attivato.</span><span class="sxs-lookup"><span data-stu-id="c455d-293">If the recognizer starts and doesn't hear any audio for the first five seconds, it will timeout.</span></span>
  * <span data-ttu-id="c455d-294">Se il riconoscimento ha dato un risultato, ma in seguito viene ascoltato il silenzio per 20 secondi, il timeout verrà completato.</span><span class="sxs-lookup"><span data-stu-id="c455d-294">If the recognizer has given a result but then hears silence for twenty seconds, it will timeout.</span></span>
* <span data-ttu-id="c455d-295">È possibile eseguire un solo tipo di riconoscimento (parola chiave o dettatura) alla volta.</span><span class="sxs-lookup"><span data-stu-id="c455d-295">Only one type of recognizer (Keyword or Dictation) can run at a time.</span></span>

>[!NOTE]
><span data-ttu-id="c455d-296">Per registrare un app dal microfono, è necessario dichiarare la funzionalità del **microfono** .</span><span class="sxs-lookup"><span data-stu-id="c455d-296">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="c455d-297">Questa operazione viene eseguita per l'utente già nell'input 212, ma è opportuno tenerla presente per i propri progetti.</span><span class="sxs-lookup"><span data-stu-id="c455d-297">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="c455d-298">Nell'editor di Unity passare a Impostazioni lettore passando a "Modifica > Impostazioni progetto > lettore"</span><span class="sxs-lookup"><span data-stu-id="c455d-298">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="c455d-299">Fare clic sulla scheda "piattaforma UWP (Universal Windows Platform)"</span><span class="sxs-lookup"><span data-stu-id="c455d-299">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="c455d-300">Nella sezione "impostazioni di pubblicazione > funzionalità" controllare la funzionalità del **microfono**</span><span class="sxs-lookup"><span data-stu-id="c455d-300">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="c455d-301">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="c455d-301">Instructions</span></span>

<span data-ttu-id="c455d-302">**MicrophoneManager.cs** verrà modificato in modo da usare il riconoscimento della dettatura.</span><span class="sxs-lookup"><span data-stu-id="c455d-302">We're going to edit **MicrophoneManager.cs** to use the Dictation Recognizer.</span></span> <span data-ttu-id="c455d-303">Questo è ciò che verrà aggiunto:</span><span class="sxs-lookup"><span data-stu-id="c455d-303">This is what we'll add:</span></span>

1. <span data-ttu-id="c455d-304">Quando si preme il **pulsante record** , si **avvierà il DictationRecognizer**.</span><span class="sxs-lookup"><span data-stu-id="c455d-304">When the **Record button** is pressed, we'll **start the DictationRecognizer**.</span></span>
2. <span data-ttu-id="c455d-305">Mostra l' **ipotesi** di ciò che DictationRecognizer ha compreso.</span><span class="sxs-lookup"><span data-stu-id="c455d-305">Show the **hypothesis** of what the DictationRecognizer understood.</span></span>
3. <span data-ttu-id="c455d-306">Blocca i **risultati** della comprensione del DictationRecognizer.</span><span class="sxs-lookup"><span data-stu-id="c455d-306">Lock in the **results** of what the DictationRecognizer understood.</span></span>
4. <span data-ttu-id="c455d-307">Verificare la presenza di timeout dal DictationRecognizer.</span><span class="sxs-lookup"><span data-stu-id="c455d-307">Check for timeouts from the DictationRecognizer.</span></span>
5. <span data-ttu-id="c455d-308">Quando si preme il **pulsante Interrompi** oppure si verifica il timeout della sessione MIC, **arrestare il DictationRecognizer**.</span><span class="sxs-lookup"><span data-stu-id="c455d-308">When the **Stop button** is pressed, or the mic session times out, **stop the DictationRecognizer**.</span></span>
6. <span data-ttu-id="c455d-309">Riavviare il **KeywordRecognizer**, che resterà in attesa del comando **Send Message** .</span><span class="sxs-lookup"><span data-stu-id="c455d-309">Restart the **KeywordRecognizer**, which will listen for the **Send Message** command.</span></span>

<span data-ttu-id="c455d-310">Cominciamo.</span><span class="sxs-lookup"><span data-stu-id="c455d-310">Let's get started.</span></span> <span data-ttu-id="c455d-311">Completare tutti gli esercizi di codifica per 3. a in **MicrophoneManager.cs**oppure copiare e incollare il codice finito riportato di seguito:</span><span class="sxs-lookup"><span data-stu-id="c455d-311">Complete all coding exercises for 3.a in **MicrophoneManager.cs**, or copy and paste the finished code found below:</span></span>

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using System.Collections;
using System.Text;
using UnityEngine;
using UnityEngine.UI;
using UnityEngine.Windows.Speech;

namespace Academy
{
    public class MicrophoneManager : MonoBehaviour
    {
        [Tooltip("A text area for the recognizer to display the recognized strings.")]
        [SerializeField]
        private Text dictationDisplay;

        private DictationRecognizer dictationRecognizer;

        // Use this string to cache the text currently displayed in the text box.
        private StringBuilder textSoFar;

        // Using an empty string specifies the default microphone.
        private static string deviceName = string.Empty;
        private int samplingRate;
        private const int messageLength = 10;

        // Use this to reset the UI once the Microphone is done recording after it was started.
        private bool hasRecordingStarted;

        void Awake()
        {
            /* TODO: DEVELOPER CODING EXERCISE 3.a */

            // 3.a: Create a new DictationRecognizer and assign it to dictationRecognizer variable.
            dictationRecognizer = new DictationRecognizer();

            // 3.a: Register for dictationRecognizer.DictationHypothesis and implement DictationHypothesis below
            // This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
            dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;

            // 3.a: Register for dictationRecognizer.DictationResult and implement DictationResult below
            // This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;

            // 3.a: Register for dictationRecognizer.DictationComplete and implement DictationComplete below
            // This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
            dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;

            // 3.a: Register for dictationRecognizer.DictationError and implement DictationError below
            // This event is fired when an error occurs.
            dictationRecognizer.DictationError += DictationRecognizer_DictationError;

            // Query the maximum frequency of the default microphone. Use 'unused' to ignore the minimum frequency.
            int unused;
            Microphone.GetDeviceCaps(deviceName, out unused, out samplingRate);

            // Use this string to cache the text currently displayed in the text box.
            textSoFar = new StringBuilder();

            // Use this to reset the UI once the Microphone is done recording after it was started.
            hasRecordingStarted = false;
        }

        void Update()
        {
            // 3.a: Add condition to check if dictationRecognizer.Status is Running
            if (hasRecordingStarted && !Microphone.IsRecording(deviceName) && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                // Reset the flag now that we're cleaning up the UI.
                hasRecordingStarted = false;

                // This acts like pressing the Stop button and sends the message to the Communicator.
                // If the microphone stops as a result of timing out, make sure to manually stop the dictation recognizer.
                // Look at the StopRecording function.
                SendMessage("RecordStop");
            }
        }

        /// <summary>
        /// Turns on the dictation recognizer and begins recording audio from the default microphone.
        /// </summary>
        /// <returns>The audio clip recorded from the microphone.</returns>
        public AudioClip StartRecording()
        {
            // 3.a Shutdown the PhraseRecognitionSystem. This controls the KeywordRecognizers
            PhraseRecognitionSystem.Shutdown();

            // 3.a: Start dictationRecognizer
            dictationRecognizer.Start();

            // 3.a Uncomment this line
            dictationDisplay.text = "Dictation is starting. It may take time to display your text the first time, but begin speaking now...";

            // Set the flag that we've started recording.
            hasRecordingStarted = true;

            // Start recording from the microphone for 10 seconds.
            return Microphone.Start(deviceName, false, messageLength, samplingRate);
        }

        /// <summary>
        /// Ends the recording session.
        /// </summary>
        public void StopRecording()
        {
            // 3.a: Check if dictationRecognizer.Status is Running and stop it if so
            if (dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                dictationRecognizer.Stop();
            }

            Microphone.End(deviceName);
        }

        /// <summary>
        /// This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
        /// </summary>
        /// <param name="text">The currently hypothesized recognition.</param>
        private void DictationRecognizer_DictationHypothesis(string text)
        {
            // 3.a: Set DictationDisplay text to be textSoFar and new hypothesized text
            // We don't want to append to textSoFar yet, because the hypothesis may have changed on the next event
            dictationDisplay.text = textSoFar.ToString() + " " + text + "...";
        }

        /// <summary>
        /// This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
        /// </summary>
        /// <param name="text">The text that was heard by the recognizer.</param>
        /// <param name="confidence">A representation of how confident (rejected, low, medium, high) the recognizer is of this recognition.</param>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // 3.a: Append textSoFar with latest text
            textSoFar.Append(text + ". ");

            // 3.a: Set DictationDisplay text to be textSoFar
            dictationDisplay.text = textSoFar.ToString();
        }

        /// <summary>
        /// This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
        /// Typically, this will simply return "Complete". In this case, we check to see if the recognizer timed out.
        /// </summary>
        /// <param name="cause">An enumerated reason for the session completing.</param>
        private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
        {
            // If Timeout occurs, the user has been silent for too long.
            // With dictation, the default timeout after a recognition is 20 seconds.
            // The default timeout with initial silence is 5 seconds.
            if (cause == DictationCompletionCause.TimeoutExceeded)
            {
                Microphone.End(deviceName);

                dictationDisplay.text = "Dictation has timed out. Please press the record button again.";
                SendMessage("ResetAfterTimeout");
            }
        }

        /// <summary>
        /// This event is fired when an error occurs.
        /// </summary>
        /// <param name="error">The string representation of the error reason.</param>
        /// <param name="hresult">The int representation of the hresult.</param>
        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            // 3.a: Set DictationDisplay text to be the error string
            dictationDisplay.text = error + "\nHRESULT: " + hresult;
        }

        /// <summary>
        /// The dictation recognizer may not turn off immediately, so this call blocks on
        /// the recognizer reporting that it has actually stopped.
        /// </summary>
        public IEnumerator WaitForDictationToStop()
        {
            while (dictationRecognizer != null && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                yield return null;
            }
        }
    }
}
```

### <a name="build-and-deploy"></a><span data-ttu-id="c455d-312">Compilazione e distribuzione</span><span class="sxs-lookup"><span data-stu-id="c455d-312">Build and Deploy</span></span>

* <span data-ttu-id="c455d-313">Ricompilare in Visual Studio e distribuirlo nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c455d-313">Rebuild in Visual Studio and deploy to your device.</span></span>
* <span data-ttu-id="c455d-314">Chiudere la casella adatta con un movimento di tocco aereo.</span><span class="sxs-lookup"><span data-stu-id="c455d-314">Dismiss the fit box with an air-tap gesture.</span></span>
* <span data-ttu-id="c455d-315">Guarda l'orologio dell'astronauta e pronuncia *"Open Communicator"* .</span><span class="sxs-lookup"><span data-stu-id="c455d-315">Gaze at the astronaut's watch and say *"Open Communicator"*.</span></span>
* <span data-ttu-id="c455d-316">Selezionare il pulsante di **registrazione** (microfono) per registrare il messaggio.</span><span class="sxs-lookup"><span data-stu-id="c455d-316">Select the **Record** button (microphone) to record your message.</span></span>
* <span data-ttu-id="c455d-317">Inizia a parlare.</span><span class="sxs-lookup"><span data-stu-id="c455d-317">Start speaking.</span></span> <span data-ttu-id="c455d-318">Il **riconoscimento della dettatura** interpreterà il riconoscimento vocale e visualizzerà il testo ipotizzato in Communicator.</span><span class="sxs-lookup"><span data-stu-id="c455d-318">The **Dictation Recognizer** will interpret your speech and show the hypothesized text in the communicator.</span></span>
* <span data-ttu-id="c455d-319">Provare a pronunciare *"Invia messaggio"* durante la registrazione di un messaggio.</span><span class="sxs-lookup"><span data-stu-id="c455d-319">Try saying *"Send Message"* while you are recording a message.</span></span> <span data-ttu-id="c455d-320">Si noti che la **parola chiave Recognizer** non risponde perché il **riconoscimento della dettatura** è ancora attivo.</span><span class="sxs-lookup"><span data-stu-id="c455d-320">Notice that the **Keyword Recognizer** does not respond because the **Dictation Recognizer** is still active.</span></span>
* <span data-ttu-id="c455d-321">Interrompere la conversazione per alcuni secondi.</span><span class="sxs-lookup"><span data-stu-id="c455d-321">Stop speaking for a few seconds.</span></span> <span data-ttu-id="c455d-322">Osservare come il riconoscimento di dettatura completa l'ipotesi e Mostra il risultato finale.</span><span class="sxs-lookup"><span data-stu-id="c455d-322">Watch as the Dictation Recognizer completes its hypothesis and shows the final result.</span></span>
* <span data-ttu-id="c455d-323">Inizia a parlare e quindi Sospendi per 20 secondi.</span><span class="sxs-lookup"><span data-stu-id="c455d-323">Begin speaking and then pause for 20 seconds.</span></span> <span data-ttu-id="c455d-324">In questo modo il sistema di **riconoscimento della dettatura** verrà sottoposto a timeout.</span><span class="sxs-lookup"><span data-stu-id="c455d-324">This will cause the **Dictation Recognizer** to timeout.</span></span>
* <span data-ttu-id="c455d-325">Si noti che la **parola chiave Recognizer** viene abilitata di nuovo dopo il timeout precedente.</span><span class="sxs-lookup"><span data-stu-id="c455d-325">Notice that the **Keyword Recognizer** is re-enabled after the above timeout.</span></span> <span data-ttu-id="c455d-326">Communicator risponderà ora ai comandi vocali.</span><span class="sxs-lookup"><span data-stu-id="c455d-326">The communicator will now respond to voice commands.</span></span>
* <span data-ttu-id="c455d-327">Pronunciare *"Send Message"* per inviare il messaggio all'astronauta.</span><span class="sxs-lookup"><span data-stu-id="c455d-327">Say *"Send Message"* to send the message to the astronaut.</span></span>

## <a name="chapter-4---grammar-recognizer"></a><span data-ttu-id="c455d-328">Capitolo 4-riconoscimento grammatica</span><span class="sxs-lookup"><span data-stu-id="c455d-328">Chapter 4 - Grammar Recognizer</span></span>

>[!VIDEO https://www.youtube.com/embed/J2dYJNSvv18]

### <a name="objectives"></a><span data-ttu-id="c455d-329">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="c455d-329">Objectives</span></span>

* <span data-ttu-id="c455d-330">Usare il sistema di riconoscimento della grammatica per riconoscere la voce dell'utente in base a un file di SRGS, o specifica della grammatica del riconoscimento vocale.</span><span class="sxs-lookup"><span data-stu-id="c455d-330">Use the Grammar Recognizer to recognize the user's speech according to an SRGS, or Speech Recognition Grammar Specification, file.</span></span>

>[!NOTE]
><span data-ttu-id="c455d-331">Per registrare un app dal microfono, è necessario dichiarare la funzionalità del **microfono** .</span><span class="sxs-lookup"><span data-stu-id="c455d-331">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="c455d-332">Questa operazione viene eseguita per l'utente già nell'input 212, ma è opportuno tenerla presente per i propri progetti.</span><span class="sxs-lookup"><span data-stu-id="c455d-332">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="c455d-333">Nell'editor di Unity passare a Impostazioni lettore passando a "Modifica > Impostazioni progetto > lettore"</span><span class="sxs-lookup"><span data-stu-id="c455d-333">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="c455d-334">Fare clic sulla scheda "piattaforma UWP (Universal Windows Platform)"</span><span class="sxs-lookup"><span data-stu-id="c455d-334">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="c455d-335">Nella sezione "impostazioni di pubblicazione > funzionalità" controllare la funzionalità del **microfono**</span><span class="sxs-lookup"><span data-stu-id="c455d-335">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="c455d-336">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="c455d-336">Instructions</span></span>

1. <span data-ttu-id="c455d-337">Nel pannello **gerarchia** cercare **Jetpack_Center** e selezionarlo.</span><span class="sxs-lookup"><span data-stu-id="c455d-337">In the **Hierarchy** panel, search for **Jetpack_Center** and select it.</span></span>
2. <span data-ttu-id="c455d-338">Cercare lo script dell' **azione Tagalong** nel pannello **Inspector** .</span><span class="sxs-lookup"><span data-stu-id="c455d-338">Look for the **Tagalong Action** script in the **Inspector** panel.</span></span>
3. <span data-ttu-id="c455d-339">Fare clic sul piccolo cerchio a destra dell' **oggetto da contrassegnare lungo** il campo.</span><span class="sxs-lookup"><span data-stu-id="c455d-339">Click the little circle to the right of the **Object To Tag Along** field.</span></span>
4. <span data-ttu-id="c455d-340">Nella finestra visualizzata cercare **SRGSToolbox** e selezionarlo dall'elenco.</span><span class="sxs-lookup"><span data-stu-id="c455d-340">In the window that pops up, search for **SRGSToolbox** and select it from the list.</span></span>
5. <span data-ttu-id="c455d-341">Esaminare il file **SRGSColor. XML** nella cartella **StreamingAssets**</span><span class="sxs-lookup"><span data-stu-id="c455d-341">Take a look at the **SRGSColor.xml** file in the **StreamingAssets** folder.</span></span>
    1. <span data-ttu-id="c455d-342">La specifica di progettazione SRGS è disponibile nel sito Web W3C [qui](https://www.w3.org/TR/speech-grammar/).</span><span class="sxs-lookup"><span data-stu-id="c455d-342">The SRGS design spec can be found on the W3C website [here](https://www.w3.org/TR/speech-grammar/).</span></span>

<span data-ttu-id="c455d-343">Nel file SRGS sono disponibili tre tipi di regole:</span><span class="sxs-lookup"><span data-stu-id="c455d-343">In our SRGS file, we have three types of rules:</span></span>

* <span data-ttu-id="c455d-344">Una regola che consente di indicare un colore da un elenco di dodici colori.</span><span class="sxs-lookup"><span data-stu-id="c455d-344">A rule which lets you say one color from a list of twelve colors.</span></span>
* <span data-ttu-id="c455d-345">Tre regole che restano in ascolto di una combinazione della regola colore e di una delle tre forme.</span><span class="sxs-lookup"><span data-stu-id="c455d-345">Three rules which listen for a combination of the color rule and one of the three shapes.</span></span>
* <span data-ttu-id="c455d-346">Regola radice, colorChooser, che rimane in attesa di una combinazione delle tre regole "colore + forma".</span><span class="sxs-lookup"><span data-stu-id="c455d-346">The root rule, colorChooser, which listens for any combination of the three "color + shape" rules.</span></span> <span data-ttu-id="c455d-347">Le forme possono essere definite in qualsiasi ordine e in qualsiasi quantità da una a tutte e tre.</span><span class="sxs-lookup"><span data-stu-id="c455d-347">The shapes can be said in any order and in any amount from just one to all three.</span></span> <span data-ttu-id="c455d-348">Questa è l'unica regola che viene ascoltata, perché viene specificata come regola radice nella parte superiore del file nel tag &lt;grammatica&gt; iniziale.</span><span class="sxs-lookup"><span data-stu-id="c455d-348">This is the only rule that is listened for, as it's specified as the root rule at the top of the file in the initial &lt;grammar&gt; tag.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="c455d-349">Compilazione e distribuzione</span><span class="sxs-lookup"><span data-stu-id="c455d-349">Build and Deploy</span></span>

* <span data-ttu-id="c455d-350">Ricompilare l'applicazione in Unity, quindi compilare e distribuire da Visual Studio per sperimentare l'app in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c455d-350">Rebuild the application in Unity, then build and deploy from Visual Studio to experience the app on HoloLens.</span></span>
* <span data-ttu-id="c455d-351">Chiudere la casella adatta con un movimento di tocco aereo.</span><span class="sxs-lookup"><span data-stu-id="c455d-351">Dismiss the fit box with an air-tap gesture.</span></span>
* <span data-ttu-id="c455d-352">Osservare il jetpack dell'astronauta ed eseguire un gesto d'aria.</span><span class="sxs-lookup"><span data-stu-id="c455d-352">Gaze at the astronaut's jetpack and perform an air-tap gesture.</span></span>
* <span data-ttu-id="c455d-353">Inizia a parlare.</span><span class="sxs-lookup"><span data-stu-id="c455d-353">Start speaking.</span></span> <span data-ttu-id="c455d-354">Il riconoscimento della **grammatica** interpreterà il riconoscimento vocale e modificherà i colori delle forme in base al riconoscimento.</span><span class="sxs-lookup"><span data-stu-id="c455d-354">The **Grammar Recognizer** will interpret your speech and change the colors of the shapes based on the recognition.</span></span> <span data-ttu-id="c455d-355">Un comando di esempio è "Blue Circle, Yellow Square".</span><span class="sxs-lookup"><span data-stu-id="c455d-355">An example command is "blue circle, yellow square".</span></span>
* <span data-ttu-id="c455d-356">Eseguire un altro gesto di tocco aereo per chiudere la casella degli strumenti.</span><span class="sxs-lookup"><span data-stu-id="c455d-356">Perform another air-tap gesture to dismiss the toolbox.</span></span>

## <a name="the-end"></a><span data-ttu-id="c455d-357">La fine</span><span class="sxs-lookup"><span data-stu-id="c455d-357">The End</span></span>

<span data-ttu-id="c455d-358">Complimenti.</span><span class="sxs-lookup"><span data-stu-id="c455d-358">Congratulations!</span></span> <span data-ttu-id="c455d-359">A questo punto è stato completato il **sig. Input 212: Voice**.</span><span class="sxs-lookup"><span data-stu-id="c455d-359">You have now completed **MR Input 212: Voice**.</span></span>

* <span data-ttu-id="c455d-360">Si conosce il DOS e non i comandi vocali.</span><span class="sxs-lookup"><span data-stu-id="c455d-360">You know the Dos and Don'ts of voice commands.</span></span>
* <span data-ttu-id="c455d-361">Sono state illustrate le modalità di utilizzo delle descrizioni comando per consentire agli utenti di riconoscere i comandi vocali.</span><span class="sxs-lookup"><span data-stu-id="c455d-361">You saw how tooltips were employed to make users aware of voice commands.</span></span>
* <span data-ttu-id="c455d-362">Sono stati rilevati diversi tipi di feedback usati per confermare che la voce dell'utente è stata ascoltata.</span><span class="sxs-lookup"><span data-stu-id="c455d-362">You saw several types of feedback used to acknowledge that the user's voice was heard.</span></span>
* <span data-ttu-id="c455d-363">Si sa come passare tra il riconoscimento delle parole chiave e il riconoscimento di dettatura e come queste due funzionalità comprendono e interpretano la voce.</span><span class="sxs-lookup"><span data-stu-id="c455d-363">You know how to switch between the Keyword Recognizer and the Dictation Recognizer, and how these two features understand and interpret your voice.</span></span>
* <span data-ttu-id="c455d-364">Si è appreso come usare un file SRGS e il riconoscimento della grammatica per il riconoscimento vocale nell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="c455d-364">You learned how to use an SRGS file and the Grammar Recognizer for speech recognition in your application.</span></span>

---
title: Input MR 211-movimento
description: Seguire questa procedura dettagliata di codifica usando Unity, Visual Studio e HoloLens per informazioni dettagliate sui concetti di movimento.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academy, esercitazione, gesto
ms.openlocfilehash: 76d2b4c0ac3d0a3783b091f7dc8c39548a18b548
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522467"
---
>[!NOTE]
><span data-ttu-id="a0338-104">Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.</span><span class="sxs-lookup"><span data-stu-id="a0338-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="a0338-105">Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.</span><span class="sxs-lookup"><span data-stu-id="a0338-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="a0338-106">Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="a0338-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="a0338-107">Verranno mantenuti per continuare a usare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="a0338-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="a0338-108">In futuro sarà disponibile una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="a0338-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="a0338-109">Questo avviso verrà aggiornato con un collegamento a queste esercitazioni quando vengono pubblicate.</span><span class="sxs-lookup"><span data-stu-id="a0338-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-input-211-gesture"></a><span data-ttu-id="a0338-110">Input MR 211: Movimento</span><span class="sxs-lookup"><span data-stu-id="a0338-110">MR Input 211: Gesture</span></span>

<span data-ttu-id="a0338-111">I [movimenti](gestures.md) attivano l'azione dell'utente.</span><span class="sxs-lookup"><span data-stu-id="a0338-111">[Gestures](gestures.md) turn user intention into action.</span></span> <span data-ttu-id="a0338-112">Con i movimenti, gli utenti possono interagire con gli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="a0338-112">With gestures, users can interact with holograms.</span></span> <span data-ttu-id="a0338-113">In questo corso si apprenderà come tenere traccia delle mani dell'utente, rispondere all'input dell'utente e fornire commenti e suggerimenti all'utente in base allo stato e alla posizione della mano.</span><span class="sxs-lookup"><span data-stu-id="a0338-113">In this course, we'll learn how to track the user's hands, respond to user input, and give feedback to the user based on hand state and location.</span></span>

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

<span data-ttu-id="a0338-114">In [Mr nozioni di base 101](holograms-101.md)è stato usato un semplice gesto d'aria per interagire con gli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="a0338-114">In [MR Basics 101](holograms-101.md), we used a simple air-tap gesture to interact with our holograms.</span></span> <span data-ttu-id="a0338-115">A questo punto, si passerà oltre il gesto d'aria e si analizzeranno i nuovi concetti per:</span><span class="sxs-lookup"><span data-stu-id="a0338-115">Now, we'll move beyond the air-tap gesture and explore new concepts to:</span></span>

* <span data-ttu-id="a0338-116">Rilevare quando viene tenuta traccia della mano dell'utente e fornire commenti e suggerimenti all'utente.</span><span class="sxs-lookup"><span data-stu-id="a0338-116">Detect when the user's hand is being tracked and provide feedback to the user.</span></span>
* <span data-ttu-id="a0338-117">Usare un movimento di navigazione per ruotare gli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="a0338-117">Use a navigation gesture to rotate our holograms.</span></span>
* <span data-ttu-id="a0338-118">Invia commenti e suggerimenti quando la mano dell'utente sta per uscire dalla visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="a0338-118">Provide feedback when the user's hand is about to go out of view.</span></span>
* <span data-ttu-id="a0338-119">Usare gli eventi di manipolazione per consentire agli utenti di spostare gli ologrammi con le proprie mani.</span><span class="sxs-lookup"><span data-stu-id="a0338-119">Use manipulation events to allow users to move holograms with their hands.</span></span>

<span data-ttu-id="a0338-120">In questo corso verrà rivisitato **Esplora modelli**di progetto Unity, che è stato compilato in [input Mr 210](holograms-210.md).</span><span class="sxs-lookup"><span data-stu-id="a0338-120">In this course, we'll revisit the Unity project **Model Explorer**, which we built in [MR Input 210](holograms-210.md).</span></span> <span data-ttu-id="a0338-121">Il nostro amico di un astronauta è stato di aiuto nell'esplorazione di questi nuovi concetti di movimento.</span><span class="sxs-lookup"><span data-stu-id="a0338-121">Our astronaut friend is back to assist us in our exploration of these new gesture concepts.</span></span>

>[!IMPORTANT]
><span data-ttu-id="a0338-122">I video incorporati in ognuno dei capitoli seguenti sono stati registrati usando una versione precedente di Unity e il Toolkit di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="a0338-122">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="a0338-123">Sebbene le istruzioni dettagliate siano accurate e aggiornate, è possibile visualizzare gli script e gli oggetti visivi nei video corrispondenti non aggiornati.</span><span class="sxs-lookup"><span data-stu-id="a0338-123">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="a0338-124">I video rimangono inclusi per i posteri e perché i concetti trattati sono ancora validi.</span><span class="sxs-lookup"><span data-stu-id="a0338-124">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="a0338-125">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="a0338-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="a0338-126">Corso</span><span class="sxs-lookup"><span data-stu-id="a0338-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="a0338-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="a0338-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="a0338-128"><a href="immersive-headset-hardware-details.md">Visori VR immersive</a></span><span class="sxs-lookup"><span data-stu-id="a0338-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="a0338-129">Input MR 211: Movimento</span><span class="sxs-lookup"><span data-stu-id="a0338-129">MR Input 211: Gesture</span></span></td><td style="text-align: center;"> <span data-ttu-id="a0338-130">✔️</span><span class="sxs-lookup"><span data-stu-id="a0338-130">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="a0338-131">✔️</span><span class="sxs-lookup"><span data-stu-id="a0338-131">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="a0338-132">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="a0338-132">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="a0338-133">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="a0338-133">Prerequisites</span></span>

* <span data-ttu-id="a0338-134">Un PC Windows 10 configurato con gli [strumenti corretti installati](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="a0338-134">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="a0338-135">Alcune funzionalità C# di programmazione di base.</span><span class="sxs-lookup"><span data-stu-id="a0338-135">Some basic C# programming ability.</span></span>
* <span data-ttu-id="a0338-136">Sono state completate le nozioni di [base 101](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="a0338-136">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="a0338-137">È necessario aver completato il [sig. Input 210](holograms-210.md).</span><span class="sxs-lookup"><span data-stu-id="a0338-137">You should have completed [MR Input 210](holograms-210.md).</span></span>
* <span data-ttu-id="a0338-138">Un dispositivo HoloLens [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="a0338-138">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="a0338-139">File di progetto</span><span class="sxs-lookup"><span data-stu-id="a0338-139">Project files</span></span>

* <span data-ttu-id="a0338-140">Scaricare i [file](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) richiesti dal progetto.</span><span class="sxs-lookup"><span data-stu-id="a0338-140">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) required by the project.</span></span><span data-ttu-id="a0338-141"> Richiede Unity 2017,2 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="a0338-141"> Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="a0338-142">Annullare l'archiviazione dei file sul desktop o in un'altra posizione facile da raggiungere.</span><span class="sxs-lookup"><span data-stu-id="a0338-142">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="a0338-143">Se si vuole esaminare il codice sorgente prima del download, è [disponibile in GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).</span><span class="sxs-lookup"><span data-stu-id="a0338-143">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="a0338-144">Errori e note</span><span class="sxs-lookup"><span data-stu-id="a0338-144">Errata and Notes</span></span>

* <span data-ttu-id="a0338-145">"Enable Just My Code" deve essere disabilitato (deselezionato) in Visual Studio in strumenti-Opzioni >-> debug per raggiungere i punti di interruzione nel codice.</span><span class="sxs-lookup"><span data-stu-id="a0338-145">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-0---unity-setup"></a><span data-ttu-id="a0338-146">Capitolo 0-installazione Unity</span><span class="sxs-lookup"><span data-stu-id="a0338-146">Chapter 0 - Unity Setup</span></span>

### <a name="instructions"></a><span data-ttu-id="a0338-147">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="a0338-147">Instructions</span></span>

1. <span data-ttu-id="a0338-148">Avvia Unity.</span><span class="sxs-lookup"><span data-stu-id="a0338-148">Start Unity.</span></span>
2. <span data-ttu-id="a0338-149">Selezionare **Apri**.</span><span class="sxs-lookup"><span data-stu-id="a0338-149">Select **Open**.</span></span>
3. <span data-ttu-id="a0338-150">Passare alla cartella **movimenti** precedentemente non archiviata.</span><span class="sxs-lookup"><span data-stu-id="a0338-150">Navigate to the **Gesture** folder you previously un-archived.</span></span>
4. <span data-ttu-id="a0338-151">Individuare e selezionare la cartella **avvio**/di**Esplora modelli** .</span><span class="sxs-lookup"><span data-stu-id="a0338-151">Find and select the **Starting**/**Model Explorer** folder.</span></span>
5. <span data-ttu-id="a0338-152">Fare clic sul pulsante **Seleziona cartella** .</span><span class="sxs-lookup"><span data-stu-id="a0338-152">Click the **Select Folder** button.</span></span>
6. <span data-ttu-id="a0338-153">Nel pannello **progetto** espandere la cartella **Scenes** .</span><span class="sxs-lookup"><span data-stu-id="a0338-153">In the **Project** panel, expand the **Scenes** folder.</span></span>
7. <span data-ttu-id="a0338-154">Fare doppio clic su **ModelExplorer** scene per caricarla in Unity.</span><span class="sxs-lookup"><span data-stu-id="a0338-154">Double-click **ModelExplorer** scene to load it in Unity.</span></span>

### <a name="building"></a><span data-ttu-id="a0338-155">Compilazione</span><span class="sxs-lookup"><span data-stu-id="a0338-155">Building</span></span>

1. <span data-ttu-id="a0338-156">In Unity selezionare **File > impostazioni di compilazione**.</span><span class="sxs-lookup"><span data-stu-id="a0338-156">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="a0338-157">Se **Scenes/ModelExplorer** non è elencato in **Scenes in Build**, fare clic su **Aggiungi scene aperte** per aggiungere la scena.</span><span class="sxs-lookup"><span data-stu-id="a0338-157">If **Scenes/ModelExplorer** is not listed in **Scenes In Build**, click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="a0338-158">Se si sta sviluppando in modo specifico per HoloLens, impostare **dispositivo di destinazione** su **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="a0338-158">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="a0338-159">In caso contrario, lasciarlo in **qualsiasi dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="a0338-159">Otherwise, leave it on **Any device**.</span></span>
4. <span data-ttu-id="a0338-160">Verificare che **tipo di compilazione** sia impostato su **D3D** e che l' **SDK** sia impostato su **installato più recente** (che deve essere SDK 16299 o versione successiva).</span><span class="sxs-lookup"><span data-stu-id="a0338-160">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
5. <span data-ttu-id="a0338-161">Fai clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="a0338-161">Click **Build**.</span></span>
6. <span data-ttu-id="a0338-162">Creare una **nuova cartella** denominata "app".</span><span class="sxs-lookup"><span data-stu-id="a0338-162">Create a **New Folder** named "App".</span></span>
7. <span data-ttu-id="a0338-163">Fare clic sulla cartella dell' **app** .</span><span class="sxs-lookup"><span data-stu-id="a0338-163">Single click the **App** folder.</span></span>
8. <span data-ttu-id="a0338-164">Premere **Seleziona cartella** e Unity avvierà la compilazione del progetto per Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a0338-164">Press **Select Folder** and Unity will start building the project for Visual Studio.</span></span>

<span data-ttu-id="a0338-165">Quando si esegue Unity, viene visualizzata una finestra Esplora file.</span><span class="sxs-lookup"><span data-stu-id="a0338-165">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="a0338-166">Aprire la cartella dell' **app** .</span><span class="sxs-lookup"><span data-stu-id="a0338-166">Open the **App** folder.</span></span>
2. <span data-ttu-id="a0338-167">Aprire la **soluzione ModelExplorer di Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="a0338-167">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="a0338-168">Se si esegue la distribuzione in HoloLens:</span><span class="sxs-lookup"><span data-stu-id="a0338-168">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="a0338-169">Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione da debug a **Release** e da ARM a **x86**.</span><span class="sxs-lookup"><span data-stu-id="a0338-169">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="a0338-170">Fare clic sulla freccia a discesa accanto al pulsante computer locale e selezionare **computer remoto**.</span><span class="sxs-lookup"><span data-stu-id="a0338-170">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="a0338-171">Immettere **l'indirizzo IP del dispositivo HoloLens** e impostare la modalità di autenticazione su **universale (protocollo non crittografato)** .</span><span class="sxs-lookup"><span data-stu-id="a0338-171">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="a0338-172">Fare clic su **Seleziona**.</span><span class="sxs-lookup"><span data-stu-id="a0338-172">Click **Select**.</span></span> <span data-ttu-id="a0338-173">Se non si conosce l'indirizzo IP del dispositivo, vedere **impostazioni > rete & Internet > opzioni avanzate**.</span><span class="sxs-lookup"><span data-stu-id="a0338-173">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="a0338-174">Nella barra dei menu superiore fare clic su **debug-> avvia senza eseguire debug** o premere **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="a0338-174">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="a0338-175">Se questa è la prima volta che si esegue la distribuzione nel dispositivo, sarà necessario associarla a [Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span><span class="sxs-lookup"><span data-stu-id="a0338-175">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
5. <span data-ttu-id="a0338-176">Quando l'app è stata distribuita, chiudere il **fitbox** con un **movimento di selezione**.</span><span class="sxs-lookup"><span data-stu-id="a0338-176">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="a0338-177">Se si esegue la distribuzione in un auricolare immersivo:</span><span class="sxs-lookup"><span data-stu-id="a0338-177">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="a0338-178">Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione da debug a **Release** e da ARM a **x64**.</span><span class="sxs-lookup"><span data-stu-id="a0338-178">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="a0338-179">Verificare che la destinazione di distribuzione sia impostata su **computer locale**.</span><span class="sxs-lookup"><span data-stu-id="a0338-179">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="a0338-180">Nella barra dei menu superiore fare clic su **debug-> avvia senza eseguire debug** o premere **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="a0338-180">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="a0338-181">Quando l'app è stata distribuita, chiudere il **fitbox** estraendo il trigger in un controller di movimento.</span><span class="sxs-lookup"><span data-stu-id="a0338-181">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

>[!NOTE]
><span data-ttu-id="a0338-182">Si potrebbero notare alcuni errori rossi nel pannello Errori di Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a0338-182">You might notice some red errors in the Visual Studio Errors panel.</span></span> <span data-ttu-id="a0338-183">È possibile ignorarli.</span><span class="sxs-lookup"><span data-stu-id="a0338-183">It is safe to ignore them.</span></span> <span data-ttu-id="a0338-184">Passare al pannello output per visualizzare lo stato di avanzamento della compilazione.</span><span class="sxs-lookup"><span data-stu-id="a0338-184">Switch to the Output panel to view actual build progress.</span></span> <span data-ttu-id="a0338-185">Per gli errori nel pannello di output sarà necessario eseguire una correzione (la maggior parte delle volte è causata da un errore in uno script).</span><span class="sxs-lookup"><span data-stu-id="a0338-185">Errors in the Output panel will require you to make a fix (most often they are caused by a mistake in a script).</span></span>

## <a name="chapter-1---hand-detected-feedback"></a><span data-ttu-id="a0338-186">Capitolo 1-feedback rilevato</span><span class="sxs-lookup"><span data-stu-id="a0338-186">Chapter 1 - Hand detected feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a><span data-ttu-id="a0338-187">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="a0338-187">Objectives</span></span>

* <span data-ttu-id="a0338-188">Sottoscrivere gli eventi di rilevamento manuale.</span><span class="sxs-lookup"><span data-stu-id="a0338-188">Subscribe to hand tracking events.</span></span>
* <span data-ttu-id="a0338-189">Usare il feedback del cursore per visualizzare gli utenti quando viene tenuta traccia di una mano.</span><span class="sxs-lookup"><span data-stu-id="a0338-189">Use cursor feedback to show users when a hand is being tracked.</span></span>

### <a name="instructions"></a><span data-ttu-id="a0338-190">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="a0338-190">Instructions</span></span>

* <span data-ttu-id="a0338-191">Nel pannello **gerarchia** espandere l'oggetto **InputManager** .</span><span class="sxs-lookup"><span data-stu-id="a0338-191">In the **Hierarchy** panel, expand the **InputManager** object.</span></span>
* <span data-ttu-id="a0338-192">Cercare e selezionare l'oggetto **GesturesInput** .</span><span class="sxs-lookup"><span data-stu-id="a0338-192">Look for and select the **GesturesInput** object.</span></span>

<span data-ttu-id="a0338-193">Lo script **InteractionInputSource.cs** esegue i passaggi seguenti:</span><span class="sxs-lookup"><span data-stu-id="a0338-193">The **InteractionInputSource.cs** script performs these steps:</span></span>

1. <span data-ttu-id="a0338-194">Sottoscrive gli eventi InteractionSourceDetected e InteractionSourceLost.</span><span class="sxs-lookup"><span data-stu-id="a0338-194">Subscribes to the InteractionSourceDetected and InteractionSourceLost events.</span></span>
2. <span data-ttu-id="a0338-195">Imposta lo stato HandDetected.</span><span class="sxs-lookup"><span data-stu-id="a0338-195">Sets the HandDetected state.</span></span>
3. <span data-ttu-id="a0338-196">Annulla la sottoscrizione degli eventi InteractionSourceDetected e InteractionSourceLost.</span><span class="sxs-lookup"><span data-stu-id="a0338-196">Unsubscribes from the InteractionSourceDetected and InteractionSourceLost events.</span></span>

<span data-ttu-id="a0338-197">Successivamente, il cursore verrà aggiornato da [Mr Input 210](holograms-210.md) in uno che mostra il feedback a seconda delle azioni dell'utente.</span><span class="sxs-lookup"><span data-stu-id="a0338-197">Next, we'll upgrade our cursor from [MR Input 210](holograms-210.md) into one that shows feedback depending on the user's actions.</span></span>

1. <span data-ttu-id="a0338-198">Nel pannello **gerarchia** selezionare l'oggetto **cursore** ed eliminarlo.</span><span class="sxs-lookup"><span data-stu-id="a0338-198">In the **Hierarchy** panel, select the **Cursor** object and delete it.</span></span>
2. <span data-ttu-id="a0338-199">Nel pannello **progetto** cercare **CursorWithFeedback** e trascinarlo nel pannello **gerarchia** .</span><span class="sxs-lookup"><span data-stu-id="a0338-199">In the **Project** panel, search for **CursorWithFeedback** and drag it into the **Hierarchy** panel.</span></span>
3. <span data-ttu-id="a0338-200">Fare clic **su InputManager** nel **Pannello gerarchia** , quindi trascinare l'oggetto **CursorWithFeedback** dalla **gerarchia** nel campo **cursore** **SimpleSinglePointerSelector**di InputManager, nella parte inferiore del **Controllo**.</span><span class="sxs-lookup"><span data-stu-id="a0338-200">Click on **InputManager** in the **Hierarchy** panel, then drag the **CursorWithFeedback** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector**'s **Cursor** field, at the bottom of the **Inspector**.</span></span>
4. <span data-ttu-id="a0338-201">Fare clic su **CursorWithFeedback** nella **gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="a0338-201">Click on the **CursorWithFeedback** in the **Hierarchy**.</span></span>
5. <span data-ttu-id="a0338-202">Nel pannello **Inspector** espandere **dati sullo stato del cursore** sullo script del **cursore dell'oggetto** .</span><span class="sxs-lookup"><span data-stu-id="a0338-202">In the **Inspector** panel, expand **Cursor State Data** on the **Object Cursor** script.</span></span>

<span data-ttu-id="a0338-203">I **dati relativi allo stato del cursore** funzionano come segue:</span><span class="sxs-lookup"><span data-stu-id="a0338-203">The **Cursor State Data** works like this:</span></span>

* <span data-ttu-id="a0338-204">Qualsiasi stato di **osservazione** indica che non viene rilevata alcuna mano e che l'utente sta semplicemente cercando.</span><span class="sxs-lookup"><span data-stu-id="a0338-204">Any **Observe** state means that no hand is detected and the user is simply looking around.</span></span>
* <span data-ttu-id="a0338-205">Qualsiasi stato **Interact** indica che viene rilevata una mano o un controller.</span><span class="sxs-lookup"><span data-stu-id="a0338-205">Any **Interact** state means that a hand or controller is detected.</span></span>
* <span data-ttu-id="a0338-206">Qualsiasi stato **hover** indica che l'utente sta esaminando un ologramma.</span><span class="sxs-lookup"><span data-stu-id="a0338-206">Any **Hover** state means the user is looking at a hologram.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="a0338-207">Compilazione e distribuzione</span><span class="sxs-lookup"><span data-stu-id="a0338-207">Build and Deploy</span></span>

* <span data-ttu-id="a0338-208">In Unity, usare **File > impostazioni di compilazione** per ricompilare l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="a0338-208">In Unity, use **File > Build Settings** to rebuild the application.</span></span>
* <span data-ttu-id="a0338-209">Aprire la cartella dell' **app** .</span><span class="sxs-lookup"><span data-stu-id="a0338-209">Open the **App** folder.</span></span>
* <span data-ttu-id="a0338-210">Se non è già aperto, aprire la **soluzione ModelExplorer di Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="a0338-210">If it's not already open, open the **ModelExplorer Visual Studio Solution**.</span></span>
  * <span data-ttu-id="a0338-211">Se il progetto è già stato compilato o distribuito in Visual Studio durante la configurazione, è possibile aprire l'istanza di VS e fare clic su' ricarica tutto ' quando richiesto.</span><span class="sxs-lookup"><span data-stu-id="a0338-211">(If you already built/deployed this project in Visual Studio during set-up, then you can open that instance of VS and click 'Reload All' when prompted).</span></span>
* <span data-ttu-id="a0338-212">In Visual Studio fare clic su **debug-> avvia senza eseguire debug** o premere **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="a0338-212">In Visual Studio, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="a0338-213">Dopo la distribuzione dell'applicazione in HoloLens, chiudere il fitbox usando il gesto di tocco.</span><span class="sxs-lookup"><span data-stu-id="a0338-213">After the application deploys to the HoloLens, dismiss the fitbox using the air-tap gesture.</span></span>
* <span data-ttu-id="a0338-214">Spostare la mano nella visualizzazione e puntare il dito dell'indice al cielo per iniziare a tenere traccia della mano.</span><span class="sxs-lookup"><span data-stu-id="a0338-214">Move your hand into view and point your index finger to the sky to start hand tracking.</span></span>
* <span data-ttu-id="a0338-215">Spostare la mano sinistra, destra, verso l'alto e verso il basso.</span><span class="sxs-lookup"><span data-stu-id="a0338-215">Move your hand left, right, up and down.</span></span>
* <span data-ttu-id="a0338-216">Osservare come cambia il cursore quando la mano viene rilevata e quindi persa dalla visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="a0338-216">Watch how the cursor changes when your hand is detected and then lost from view.</span></span>
* <span data-ttu-id="a0338-217">Se si usa un auricolare immersivo, è necessario connettere e disconnettere il controller.</span><span class="sxs-lookup"><span data-stu-id="a0338-217">If you're on an immersive headset, you'll have to connect and disconnect your controller.</span></span> <span data-ttu-id="a0338-218">Questo feedback diventa meno interessante in un dispositivo immersivo, perché un controller connesso sarà sempre "disponibile".</span><span class="sxs-lookup"><span data-stu-id="a0338-218">This feedback becomes less interesting on an immersive device, as a connected controller will always be "available".</span></span>

## <a name="chapter-2---navigation"></a><span data-ttu-id="a0338-219">Capitolo 2-navigazione</span><span class="sxs-lookup"><span data-stu-id="a0338-219">Chapter 2 - Navigation</span></span>

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a><span data-ttu-id="a0338-220">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="a0338-220">Objectives</span></span>

* <span data-ttu-id="a0338-221">Usare gli eventi del movimento di spostamento per ruotare l'astronauta.</span><span class="sxs-lookup"><span data-stu-id="a0338-221">Use Navigation gesture events to rotate the astronaut.</span></span>

### <a name="instructions"></a><span data-ttu-id="a0338-222">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="a0338-222">Instructions</span></span>

<span data-ttu-id="a0338-223">Per usare i movimenti di navigazione nell'app, è necessario modificare **GestureAction.cs** per ruotare gli oggetti quando si verifica il movimento di navigazione.</span><span class="sxs-lookup"><span data-stu-id="a0338-223">To use Navigation gestures in our app, we are going to edit **GestureAction.cs** to rotate objects when the Navigation gesture occurs.</span></span> <span data-ttu-id="a0338-224">Inoltre, verranno aggiunti commenti e suggerimenti al cursore da visualizzare quando è disponibile la navigazione.</span><span class="sxs-lookup"><span data-stu-id="a0338-224">Additionally, we'll add feedback to the cursor to display when Navigation is available.</span></span>

1. <span data-ttu-id="a0338-225">Nel pannello **gerarchia** espandere **CursorWithFeedback**.</span><span class="sxs-lookup"><span data-stu-id="a0338-225">In the **Hierarchy** panel, expand **CursorWithFeedback**.</span></span>
2. <span data-ttu-id="a0338-226">Nella cartella **ologrammi** trovare l'asset **ScrollFeedback** .</span><span class="sxs-lookup"><span data-stu-id="a0338-226">In the **Holograms** folder, find the **ScrollFeedback** asset.</span></span>
3. <span data-ttu-id="a0338-227">Trascinare e rilasciare la prefabbricazione **ScrollFeedback** in **CursorWithFeedback** GameObject nella **gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="a0338-227">Drag and drop the **ScrollFeedback** prefab onto the **CursorWithFeedback** GameObject in the **Hierarchy**.</span></span>
4. <span data-ttu-id="a0338-228">Fare clic su **CursorWithFeedback**.</span><span class="sxs-lookup"><span data-stu-id="a0338-228">Click on **CursorWithFeedback**.</span></span>
5. <span data-ttu-id="a0338-229">Nel pannello **Inspector** fare clic sul pulsante **Add Component** .</span><span class="sxs-lookup"><span data-stu-id="a0338-229">In the **Inspector** panel, click the **Add Component** button.</span></span>
6. <span data-ttu-id="a0338-230">Nel menu digitare nella casella di ricerca **CursorFeedback**.</span><span class="sxs-lookup"><span data-stu-id="a0338-230">In the menu, type in the search box **CursorFeedback**.</span></span> <span data-ttu-id="a0338-231">Selezionare il risultato della ricerca.</span><span class="sxs-lookup"><span data-stu-id="a0338-231">Select the search result.</span></span>
7. <span data-ttu-id="a0338-232">Trascinare e rilasciare l'oggetto **ScrollFeedback** dalla **gerarchia** sulla proprietà dell' **oggetto gioco rilevato Scroll** nel componente **feedback del cursore** del **controllo**.</span><span class="sxs-lookup"><span data-stu-id="a0338-232">Drag and drop the **ScrollFeedback** object from the **Hierarchy** onto the **Scroll Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>
8. <span data-ttu-id="a0338-233">Nel pannello **gerarchia** selezionare l'oggetto **Astron** .</span><span class="sxs-lookup"><span data-stu-id="a0338-233">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
9. <span data-ttu-id="a0338-234">Nel pannello **Inspector** fare clic sul pulsante **Add Component** .</span><span class="sxs-lookup"><span data-stu-id="a0338-234">In the **Inspector** panel, click the **Add Component** button.</span></span>
10. <span data-ttu-id="a0338-235">Nel menu digitare l' **azione di movimento**della casella di ricerca.</span><span class="sxs-lookup"><span data-stu-id="a0338-235">In the menu, type in the search box **Gesture Action**.</span></span> <span data-ttu-id="a0338-236">Selezionare il risultato della ricerca.</span><span class="sxs-lookup"><span data-stu-id="a0338-236">Select the search result.</span></span>

<span data-ttu-id="a0338-237">Successivamente, aprire **GestureAction.cs** in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a0338-237">Next, open **GestureAction.cs** in Visual Studio.</span></span> <span data-ttu-id="a0338-238">Nel codice esercizio 2. c, modificare lo script per eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="a0338-238">In coding exercise 2.c, edit the script to do the following:</span></span>

1. <span data-ttu-id="a0338-239">**Ruotare l'** oggetto astror ogni volta che viene eseguito un movimento di navigazione.</span><span class="sxs-lookup"><span data-stu-id="a0338-239">**Rotate the AstroMan** object whenever a Navigation gesture is performed.</span></span>
2. <span data-ttu-id="a0338-240">Calcolare **rotationFactor** per controllare la quantità di rotazione applicata all'oggetto.</span><span class="sxs-lookup"><span data-stu-id="a0338-240">Calculate the **rotationFactor** to control the amount of rotation applied to the object.</span></span>
3. <span data-ttu-id="a0338-241">**Ruotare l'oggetto** intorno all'asse y quando l'utente sposta la mano verso sinistra o verso destra.</span><span class="sxs-lookup"><span data-stu-id="a0338-241">**Rotate the object** around the y-axis when the user moves their hand left or right.</span></span>

<span data-ttu-id="a0338-242">Completare gli esercizi di codifica 2. c nello script oppure sostituire il codice con la soluzione completata seguente:</span><span class="sxs-lookup"><span data-stu-id="a0338-242">Complete coding exercises 2.c in the script, or replace the code with the completed solution below:</span></span>

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

<span data-ttu-id="a0338-243">Si noterà che gli altri eventi di navigazione sono già stati compilati con alcune informazioni.</span><span class="sxs-lookup"><span data-stu-id="a0338-243">You'll notice that the other navigation events are already filled in with some info.</span></span> <span data-ttu-id="a0338-244">Viene eseguito il push di GameObject nello stack modale InputSystem's del Toolkit, in modo che l'utente non debba mantenere lo stato attivo sull'astronauta dopo che la rotazione è iniziata.</span><span class="sxs-lookup"><span data-stu-id="a0338-244">We push the GameObject onto the Toolkit's InputSystem's modal stack, so the user doesn't have to maintain focus on the Astronaut once rotation has begun.</span></span> <span data-ttu-id="a0338-245">Al termine, si estrae il GameObject dallo stack una volta completato il movimento.</span><span class="sxs-lookup"><span data-stu-id="a0338-245">Correspondingly, we pop the GameObject off the stack once the gesture is completed.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="a0338-246">Compilazione e distribuzione</span><span class="sxs-lookup"><span data-stu-id="a0338-246">Build and Deploy</span></span>

1. <span data-ttu-id="a0338-247">Ricompilare l'applicazione in Unity e quindi compilare e distribuire da Visual Studio per eseguirla in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a0338-247">Rebuild the application in Unity and then build and deploy from Visual Studio to run it in the HoloLens.</span></span>
2. <span data-ttu-id="a0338-248">Osservando l'astronauta, due frecce dovrebbero apparire su entrambi i lati del cursore.</span><span class="sxs-lookup"><span data-stu-id="a0338-248">Gaze at the astronaut, two arrows should appear on either side of the cursor.</span></span> <span data-ttu-id="a0338-249">Questo nuovo oggetto visivo indica che l'astronauta può essere ruotato.</span><span class="sxs-lookup"><span data-stu-id="a0338-249">This new visual indicates that the astronaut can be rotated.</span></span>
3. <span data-ttu-id="a0338-250">Posizionare la mano nella posizione pronta (indice puntato verso il cielo), in modo che il HoloLens inizi a tenere traccia della mano.</span><span class="sxs-lookup"><span data-stu-id="a0338-250">Place your hand in the ready position (index finger pointed towards the sky) so the HoloLens will start tracking your hand.</span></span>
4. <span data-ttu-id="a0338-251">Per ruotare l'astronauta, abbassare il dito dell'indice in una posizione di pizzico, quindi spostare la mano verso sinistra o destra per attivare il movimento NavigationX.</span><span class="sxs-lookup"><span data-stu-id="a0338-251">To rotate the astronaut, lower your index finger to a pinch position, and then move your hand left or right to trigger the NavigationX gesture.</span></span>

## <a name="chapter-3---hand-guidance"></a><span data-ttu-id="a0338-252">Capitolo 3-linee guida</span><span class="sxs-lookup"><span data-stu-id="a0338-252">Chapter 3 - Hand Guidance</span></span>

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a><span data-ttu-id="a0338-253">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="a0338-253">Objectives</span></span>

* <span data-ttu-id="a0338-254">Usare il **punteggio delle linee guida** per aiutare a prevedere quando il rilevamento mano andrà perso.</span><span class="sxs-lookup"><span data-stu-id="a0338-254">Use **hand guidance score** to help predict when hand tracking will be lost.</span></span>
* <span data-ttu-id="a0338-255">Fornire **commenti e suggerimenti sul cursore** da visualizzare quando l'utente si avvicina al bordo di visualizzazione della fotocamera.</span><span class="sxs-lookup"><span data-stu-id="a0338-255">Provide **feedback on the cursor** to show when the user's hand nears the camera's edge of view.</span></span>

### <a name="instructions"></a><span data-ttu-id="a0338-256">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="a0338-256">Instructions</span></span>

1. <span data-ttu-id="a0338-257">Nel pannello **gerarchia** selezionare l'oggetto **CursorWithFeedback** .</span><span class="sxs-lookup"><span data-stu-id="a0338-257">In the **Hierarchy** panel, select the **CursorWithFeedback** object.</span></span>
2. <span data-ttu-id="a0338-258">Nel pannello **Inspector** fare clic sul pulsante **Add Component** .</span><span class="sxs-lookup"><span data-stu-id="a0338-258">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="a0338-259">Nel menu digitare le **istruzioni**della casella di ricerca.</span><span class="sxs-lookup"><span data-stu-id="a0338-259">In the menu, type in the search box **Hand Guidance**.</span></span> <span data-ttu-id="a0338-260">Selezionare il risultato della ricerca.</span><span class="sxs-lookup"><span data-stu-id="a0338-260">Select the search result.</span></span>
4. <span data-ttu-id="a0338-261">Nella cartella olografici  del pannello del **progetto** individuare l'asset **HandGuidanceFeedback** .</span><span class="sxs-lookup"><span data-stu-id="a0338-261">In the **Project** panel **Holograms** folder, find the **HandGuidanceFeedback** asset.</span></span>
5. <span data-ttu-id="a0338-262">Trascinare e rilasciare l'asset **HandGuidanceFeedback** sulla proprietà **indicatore della mano guida** nel pannello **Inspector** .</span><span class="sxs-lookup"><span data-stu-id="a0338-262">Drag and drop the **HandGuidanceFeedback** asset onto the **Hand Guidance Indicator** property in the **Inspector** panel.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="a0338-263">Compilazione e distribuzione</span><span class="sxs-lookup"><span data-stu-id="a0338-263">Build and Deploy</span></span>

* <span data-ttu-id="a0338-264">Ricompilare l'applicazione in Unity e quindi compilare e distribuire da Visual Studio per sperimentare l'app in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a0338-264">Rebuild the application in Unity and then build and deploy from Visual Studio to experience the app on HoloLens.</span></span>
* <span data-ttu-id="a0338-265">È possibile passare alla visualizzazione e aumentare il dito dell'indice per tenerne traccia.</span><span class="sxs-lookup"><span data-stu-id="a0338-265">Bring your hand into view and raise your index finger to get tracked.</span></span>
* <span data-ttu-id="a0338-266">Iniziare a ruotare l'astronauta con il movimento di navigazione (pizzicare il dito dell'indice e il pollice insieme).</span><span class="sxs-lookup"><span data-stu-id="a0338-266">Start rotating the astronaut with the Navigation gesture (pinch your index finger and thumb together).</span></span>
* <span data-ttu-id="a0338-267">Spostare la mano all'estrema sinistra, a destra, in alto e in basso.</span><span class="sxs-lookup"><span data-stu-id="a0338-267">Move your hand far left, right, up, and down.</span></span>
* <span data-ttu-id="a0338-268">Man mano che si avvicina il bordo del frame di movimento, viene visualizzata una freccia accanto al cursore per avvisare che il rilevamento della mano andrà perso.</span><span class="sxs-lookup"><span data-stu-id="a0338-268">As your hand nears the edge of the gesture frame, an arrow should appear next to the cursor to warn you that hand tracking will be lost.</span></span> <span data-ttu-id="a0338-269">La freccia indica quale direzione spostare la mano per evitare che il rilevamento vada perso.</span><span class="sxs-lookup"><span data-stu-id="a0338-269">The arrow indicates which direction to move your hand in order to prevent tracking from being lost.</span></span>

## <a name="chapter-4---manipulation"></a><span data-ttu-id="a0338-270">Capitolo 4-manipolazione</span><span class="sxs-lookup"><span data-stu-id="a0338-270">Chapter 4 - Manipulation</span></span>

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a><span data-ttu-id="a0338-271">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="a0338-271">Objectives</span></span>

* <span data-ttu-id="a0338-272">Usare gli eventi di manipolazione per spostare l'astronauta con le mani.</span><span class="sxs-lookup"><span data-stu-id="a0338-272">Use Manipulation events to move the astronaut with your hands.</span></span>
* <span data-ttu-id="a0338-273">Fornire commenti e suggerimenti sul cursore per informare l'utente quando è possibile utilizzare la manipolazione.</span><span class="sxs-lookup"><span data-stu-id="a0338-273">Provide feedback on the cursor to let the user know when Manipulation can be used.</span></span>

### <a name="instructions"></a><span data-ttu-id="a0338-274">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="a0338-274">Instructions</span></span>

<span data-ttu-id="a0338-275">GestureManager.cs e AstronautManager.cs ci consentiranno di eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="a0338-275">GestureManager.cs and AstronautManager.cs will allow us to do the following:</span></span>

1. <span data-ttu-id="a0338-276">Usare la parola chiave Speech "**Move Astronaut**" per abilitare i movimenti di **manipolazione** e la "**ruota astronauta**" per disabilitarli.</span><span class="sxs-lookup"><span data-stu-id="a0338-276">Use the speech keyword "**Move Astronaut**" to enable **Manipulation** gestures and "**Rotate Astronaut**" to disable them.</span></span>
2. <span data-ttu-id="a0338-277">Passa a rispondere al riconoscitore del **movimento di manipolazione**.</span><span class="sxs-lookup"><span data-stu-id="a0338-277">Switch to responding to the **Manipulation Gesture Recognizer**.</span></span>

<span data-ttu-id="a0338-278">Ma veniamo al dunque.</span><span class="sxs-lookup"><span data-stu-id="a0338-278">Let's get started.</span></span>

1. <span data-ttu-id="a0338-279">Nel pannello **gerarchia** creare un nuovo GameObject vuoto.</span><span class="sxs-lookup"><span data-stu-id="a0338-279">In the **Hierarchy** panel, create a new empty GameObject.</span></span> <span data-ttu-id="a0338-280">Assegnare al file il nome "**AstronautManager**".</span><span class="sxs-lookup"><span data-stu-id="a0338-280">Name it "**AstronautManager**".</span></span>
2. <span data-ttu-id="a0338-281">Nel pannello **Inspector** fare clic sul pulsante **Add Component** .</span><span class="sxs-lookup"><span data-stu-id="a0338-281">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="a0338-282">Nel menu digitare nella casella di ricerca **gestione astronauti**.</span><span class="sxs-lookup"><span data-stu-id="a0338-282">In the menu, type in the search box **Astronaut Manager**.</span></span> <span data-ttu-id="a0338-283">Selezionare il risultato della ricerca.</span><span class="sxs-lookup"><span data-stu-id="a0338-283">Select the search result.</span></span>
4. <span data-ttu-id="a0338-284">Nel pannello **Inspector** fare clic sul pulsante **Add Component** .</span><span class="sxs-lookup"><span data-stu-id="a0338-284">In the **Inspector** panel, click the **Add Component** button.</span></span>
5. <span data-ttu-id="a0338-285">Nel menu digitare l' **origine input vocale**della casella di ricerca.</span><span class="sxs-lookup"><span data-stu-id="a0338-285">In the menu, type in the search box **Speech Input Source**.</span></span> <span data-ttu-id="a0338-286">Selezionare il risultato della ricerca.</span><span class="sxs-lookup"><span data-stu-id="a0338-286">Select the search result.</span></span>

<span data-ttu-id="a0338-287">Verranno ora aggiunti i comandi vocali necessari per controllare lo stato di interazione dell'astronauta.</span><span class="sxs-lookup"><span data-stu-id="a0338-287">We'll now add the speech commands required to control the interaction state of the astronaut.</span></span>

1. <span data-ttu-id="a0338-288">Espandere la  sezione Keywords nel **controllo**.</span><span class="sxs-lookup"><span data-stu-id="a0338-288">Expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="a0338-289">**+** Fare clic sul lato destro per aggiungere una nuova parola chiave.</span><span class="sxs-lookup"><span data-stu-id="a0338-289">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="a0338-290">Digitare la parola chiave come **Move Astronaut**.</span><span class="sxs-lookup"><span data-stu-id="a0338-290">Type the Keyword as **Move Astronaut**.</span></span> <span data-ttu-id="a0338-291">Se lo si desidera, è possibile aggiungere un tasto di scelta rapida.</span><span class="sxs-lookup"><span data-stu-id="a0338-291">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="a0338-292">**+** Fare clic sul lato destro per aggiungere una nuova parola chiave.</span><span class="sxs-lookup"><span data-stu-id="a0338-292">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="a0338-293">Digitare la parola chiave come **ruota astronauta**.</span><span class="sxs-lookup"><span data-stu-id="a0338-293">Type the Keyword as **Rotate Astronaut**.</span></span> <span data-ttu-id="a0338-294">Se lo si desidera, è possibile aggiungere un tasto di scelta rapida.</span><span class="sxs-lookup"><span data-stu-id="a0338-294">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="a0338-295">Il codice del gestore corrispondente si trova in **GestureAction.cs**nel gestore **ISpeechHandler. OnSpeechKeywordRecognized** .</span><span class="sxs-lookup"><span data-stu-id="a0338-295">The corresponding handler code can be found in **GestureAction.cs**, in the **ISpeechHandler.OnSpeechKeywordRecognized** handler.</span></span>

![Come configurare l'origine di input vocale per il capitolo 4](images/holograms211-speech.png)

<span data-ttu-id="a0338-297">Successivamente, verrà configurato il feedback di manipolazione sul cursore.</span><span class="sxs-lookup"><span data-stu-id="a0338-297">Next, we'll setup the manipulation feedback on the cursor.</span></span>

1. <span data-ttu-id="a0338-298">Nella cartella olografici  del pannello del **progetto** individuare l'asset **PathingFeedback** .</span><span class="sxs-lookup"><span data-stu-id="a0338-298">In the **Project** panel **Holograms** folder, find the **PathingFeedback** asset.</span></span>
2. <span data-ttu-id="a0338-299">Trascinare e rilasciare la prefabbricazione **PathingFeedback** nell'oggetto **CursorWithFeedback** della **gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="a0338-299">Drag and drop the **PathingFeedback** prefab onto the **CursorWithFeedback** object in the **Hierarchy**.</span></span>
3. <span data-ttu-id="a0338-300">Nel pannello **gerarchia** fare clic su **CursorWithFeedback**.</span><span class="sxs-lookup"><span data-stu-id="a0338-300">In the **Hierarchy** panel, click on **CursorWithFeedback**.</span></span>
4. <span data-ttu-id="a0338-301">Trascinare e rilasciare l'oggetto **PathingFeedback** dalla **gerarchia** alla proprietà dell' **oggetto del gioco rilevato nel percorso** nel componente **feedback del cursore** del **controllo**.</span><span class="sxs-lookup"><span data-stu-id="a0338-301">Drag and drop the **PathingFeedback** object from the **Hierarchy** onto the **Pathing Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>

<span data-ttu-id="a0338-302">A questo punto è necessario aggiungere il codice a **GestureAction.cs** per abilitare gli elementi seguenti:</span><span class="sxs-lookup"><span data-stu-id="a0338-302">Now we need to add code to **GestureAction.cs** to enable the following:</span></span>

1. <span data-ttu-id="a0338-303">Aggiungere codice alla funzione **IManipulationHandler. OnManipulationUpdated** che sposta l'astronauta quando viene rilevato un movimento di **manipolazione** .</span><span class="sxs-lookup"><span data-stu-id="a0338-303">Add code to the **IManipulationHandler.OnManipulationUpdated** function, which will move the astronaut when a **Manipulation** gesture is detected.</span></span>
2. <span data-ttu-id="a0338-304">Calcolare il **vettore di spostamento** per determinare il punto in cui deve essere spostato l'astronauta in base alla posizione della mano.</span><span class="sxs-lookup"><span data-stu-id="a0338-304">Calculate the **movement vector** to determine where the astronaut should be moved to based on hand position.</span></span>
3. <span data-ttu-id="a0338-305">**Spostare** l'astronauta nella nuova posizione.</span><span class="sxs-lookup"><span data-stu-id="a0338-305">**Move** the astronaut to the new position.</span></span>

<span data-ttu-id="a0338-306">Completare il codice esercizio 4. a in **GestureAction.cs**o usare la soluzione completa seguente:</span><span class="sxs-lookup"><span data-stu-id="a0338-306">Complete coding exercise 4.a in **GestureAction.cs**, or use our completed solution below:</span></span>

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

### <a name="build-and-deploy"></a><span data-ttu-id="a0338-307">Compilazione e distribuzione</span><span class="sxs-lookup"><span data-stu-id="a0338-307">Build and Deploy</span></span>

* <span data-ttu-id="a0338-308">Ricompilare in Unity e quindi compilare e distribuire da Visual Studio per eseguire l'app in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a0338-308">Rebuild in Unity and then build and deploy from Visual Studio to run the app in HoloLens.</span></span>
* <span data-ttu-id="a0338-309">Spostare la mano davanti alla HoloLens e aumentare il dito dell'indice in modo che possa essere rilevata.</span><span class="sxs-lookup"><span data-stu-id="a0338-309">Move your hand in front of the HoloLens and raise your index finger so that it can be tracked.</span></span>
* <span data-ttu-id="a0338-310">Concentrare il cursore sull'astronauta.</span><span class="sxs-lookup"><span data-stu-id="a0338-310">Focus the cursor over the astronaut.</span></span>
* <span data-ttu-id="a0338-311">Pronunciare ' Move Astronaut ' per spostare l'astronauta con un movimento di manipolazione.</span><span class="sxs-lookup"><span data-stu-id="a0338-311">Say 'Move Astronaut' to move the astronaut with a Manipulation gesture.</span></span>
* <span data-ttu-id="a0338-312">Attorno al cursore verranno visualizzate quattro frecce per indicare che il programma risponderà a eventi di manipolazione.</span><span class="sxs-lookup"><span data-stu-id="a0338-312">Four arrows should appear around the cursor to indicate that the program will now respond to Manipulation events.</span></span>
* <span data-ttu-id="a0338-313">Abbassare il dito dell'indice verso il basso e tenerli insieme.</span><span class="sxs-lookup"><span data-stu-id="a0338-313">Lower your index finger down to your thumb, and keep them pinched together.</span></span>
* <span data-ttu-id="a0338-314">Man mano che ci si sposta, si sposta anche l'astronauta (si tratta di una manipolazione).</span><span class="sxs-lookup"><span data-stu-id="a0338-314">As you move your hand around, the astronaut will move too (this is Manipulation).</span></span>
* <span data-ttu-id="a0338-315">Aumentare il dito dell'indice per interrompere la manipolazione dell'astronauta.</span><span class="sxs-lookup"><span data-stu-id="a0338-315">Raise your index finger to stop manipulating the astronaut.</span></span>
* <span data-ttu-id="a0338-316">Nota: Se non si dice "Sposta astronauta" prima di spostare la mano, verrà usato il movimento di navigazione.</span><span class="sxs-lookup"><span data-stu-id="a0338-316">Note: If you do not say 'Move Astronaut' before moving your hand, then the Navigation gesture will be used instead.</span></span>
* <span data-ttu-id="a0338-317">Pronunciare ' ruota astronauta ' per tornare allo stato girevole.</span><span class="sxs-lookup"><span data-stu-id="a0338-317">Say 'Rotate Astronaut' to return to the rotatable state.</span></span>

## <a name="chapter-5---model-expansion"></a><span data-ttu-id="a0338-318">Capitolo 5-espansione del modello</span><span class="sxs-lookup"><span data-stu-id="a0338-318">Chapter 5 - Model expansion</span></span>

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a><span data-ttu-id="a0338-319">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="a0338-319">Objectives</span></span>

* <span data-ttu-id="a0338-320">Espandere il modello astronauta in più parti più piccole con cui l'utente può interagire.</span><span class="sxs-lookup"><span data-stu-id="a0338-320">Expand the Astronaut model into multiple, smaller pieces that the user can interact with.</span></span>
* <span data-ttu-id="a0338-321">Spostare ogni pezzo singolarmente utilizzando movimenti di spostamento e manipolazione.</span><span class="sxs-lookup"><span data-stu-id="a0338-321">Move each piece individually using Navigation and Manipulation gestures.</span></span>

### <a name="instructions"></a><span data-ttu-id="a0338-322">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="a0338-322">Instructions</span></span>

<span data-ttu-id="a0338-323">In questa sezione vengono eseguite le attività seguenti:</span><span class="sxs-lookup"><span data-stu-id="a0338-323">In this section, we will accomplish the following tasks:</span></span>

1. <span data-ttu-id="a0338-324">Aggiungere una nuova parola chiave "**expand Model**" per espandere il modello Astronaut.</span><span class="sxs-lookup"><span data-stu-id="a0338-324">Add a new keyword "**Expand Model**" to expand the astronaut model.</span></span>
2. <span data-ttu-id="a0338-325">Aggiungere una nuova parola chiave "**Reset Model**" per restituire il modello al formato originale.</span><span class="sxs-lookup"><span data-stu-id="a0338-325">Add a new Keyword "**Reset Model**" to return the model to its original form.</span></span>

<span data-ttu-id="a0338-326">A tale scopo, aggiungere altre due parole chiave all'origine di input vocale del capitolo precedente.</span><span class="sxs-lookup"><span data-stu-id="a0338-326">We'll do this by adding two more keywords to the Speech Input Source from the previous chapter.</span></span> <span data-ttu-id="a0338-327">Verrà inoltre illustrato un altro modo per gestire gli eventi di riconoscimento.</span><span class="sxs-lookup"><span data-stu-id="a0338-327">We'll also demonstrate another way to handle recognition events.</span></span>

1. <span data-ttu-id="a0338-328">Fare clic su Back on **AstronautManager** nel **controllo** ed espandere  la sezione Keywords nel **controllo**.</span><span class="sxs-lookup"><span data-stu-id="a0338-328">Click back on **AstronautManager** in the **Inspector** and expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="a0338-329">**+** Fare clic sul lato destro per aggiungere una nuova parola chiave.</span><span class="sxs-lookup"><span data-stu-id="a0338-329">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="a0338-330">Digitare la parola chiave come **Espandi modello**.</span><span class="sxs-lookup"><span data-stu-id="a0338-330">Type the Keyword as **Expand Model**.</span></span> <span data-ttu-id="a0338-331">Se lo si desidera, è possibile aggiungere un tasto di scelta rapida.</span><span class="sxs-lookup"><span data-stu-id="a0338-331">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="a0338-332">**+** Fare clic sul lato destro per aggiungere una nuova parola chiave.</span><span class="sxs-lookup"><span data-stu-id="a0338-332">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="a0338-333">Digitare la parola chiave come **Reimposta modello**.</span><span class="sxs-lookup"><span data-stu-id="a0338-333">Type the Keyword as **Reset Model**.</span></span> <span data-ttu-id="a0338-334">Se lo si desidera, è possibile aggiungere un tasto di scelta rapida.</span><span class="sxs-lookup"><span data-stu-id="a0338-334">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="a0338-335">Nel pannello **Inspector** fare clic sul pulsante **Add Component** .</span><span class="sxs-lookup"><span data-stu-id="a0338-335">In the **Inspector** panel, click the **Add Component** button.</span></span>
7. <span data-ttu-id="a0338-336">Nel menu digitare il **gestore di input vocale**della casella di ricerca.</span><span class="sxs-lookup"><span data-stu-id="a0338-336">In the menu, type in the search box **Speech Input Handler**.</span></span> <span data-ttu-id="a0338-337">Selezionare il risultato della ricerca.</span><span class="sxs-lookup"><span data-stu-id="a0338-337">Select the search result.</span></span>
8. <span data-ttu-id="a0338-338">Il controllo **è un listener globale**, perché si vuole che questi comandi funzionino indipendentemente dal GameObject che si sta concentrando.</span><span class="sxs-lookup"><span data-stu-id="a0338-338">Check **Is Global Listener**, since we want these commands to work regardless of the GameObject we're focusing.</span></span>
9. <span data-ttu-id="a0338-339">Fare clic **+** sul pulsante e selezionare **Espandi modello** dall'elenco a discesa parola chiave.</span><span class="sxs-lookup"><span data-stu-id="a0338-339">Click the **+** button and select **Expand Model** from the Keyword dropdown.</span></span>
10. <span data-ttu-id="a0338-340">Fare clic su    in risposta e trascinare AstronautManager dalla gerarchia nel campo None **+** (Object).</span><span class="sxs-lookup"><span data-stu-id="a0338-340">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
11. <span data-ttu-id="a0338-341">A questo punto, fare clic sull'elenco a discesa **Nessuna funzione** , selezionare **AstronautManager**, quindi **ExpandModelCommand**.</span><span class="sxs-lookup"><span data-stu-id="a0338-341">Now, click the **No Function** dropdown, select **AstronautManager**, then **ExpandModelCommand**.</span></span>
12. <span data-ttu-id="a0338-342">Fare clic sul pulsante del gestore **+** di input vocale e selezionare **Reimposta modello** dall'elenco a discesa parola chiave.</span><span class="sxs-lookup"><span data-stu-id="a0338-342">Click the Speech Input Handler's **+** button and select **Reset Model** from the Keyword dropdown.</span></span>
13. <span data-ttu-id="a0338-343">Fare clic su    in risposta e trascinare AstronautManager dalla gerarchia nel campo None **+** (Object).</span><span class="sxs-lookup"><span data-stu-id="a0338-343">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
14. <span data-ttu-id="a0338-344">A questo punto, fare clic sull'elenco a discesa **Nessuna funzione** , selezionare **AstronautManager**, quindi **ResetModelCommand**.</span><span class="sxs-lookup"><span data-stu-id="a0338-344">Now, click the **No Function** dropdown, select **AstronautManager**, then **ResetModelCommand**.</span></span>

![Come configurare l'origine e il gestore di input vocale per il capitolo 5](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a><span data-ttu-id="a0338-346">Compilazione e distribuzione</span><span class="sxs-lookup"><span data-stu-id="a0338-346">Build and Deploy</span></span>

* <span data-ttu-id="a0338-347">Prova!</span><span class="sxs-lookup"><span data-stu-id="a0338-347">Try it!</span></span> <span data-ttu-id="a0338-348">Compilare e distribuire l'app in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a0338-348">Build and deploy the app to the HoloLens.</span></span>
* <span data-ttu-id="a0338-349">Supponiamo **Espandi modello** per visualizzare il modello astronauta espanso.</span><span class="sxs-lookup"><span data-stu-id="a0338-349">Say **Expand Model** to see the expanded astronaut model.</span></span>
* <span data-ttu-id="a0338-350">Usare la **navigazione** per ruotare le singole parti del seme degli astronauti.</span><span class="sxs-lookup"><span data-stu-id="a0338-350">Use **Navigation** to rotate individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="a0338-351">Supponiamo di **spostare** l'astronauta e quindi di usare la **manipolazione** per spostare singoli pezzi del seme degli astronauti.</span><span class="sxs-lookup"><span data-stu-id="a0338-351">Say **Move Astronaut** and then use **Manipulation** to move individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="a0338-352">Dire **ruotare** l'astronauta per ruotare nuovamente le parti.</span><span class="sxs-lookup"><span data-stu-id="a0338-352">Say **Rotate Astronaut** to rotate the pieces again.</span></span>
* <span data-ttu-id="a0338-353">Ad esempio **Reimposta modello** per restituire l'astronauta al formato originale.</span><span class="sxs-lookup"><span data-stu-id="a0338-353">Say **Reset Model** to return the astronaut to its original form.</span></span>

## <a name="the-end"></a><span data-ttu-id="a0338-354">La fine</span><span class="sxs-lookup"><span data-stu-id="a0338-354">The End</span></span>

<span data-ttu-id="a0338-355">La procedura è stata completata.</span><span class="sxs-lookup"><span data-stu-id="a0338-355">Congratulations!</span></span> <span data-ttu-id="a0338-356">A questo punto è **stato completato il Sig. input 211: Gesto**.</span><span class="sxs-lookup"><span data-stu-id="a0338-356">You have now completed **MR Input 211: Gesture**.</span></span>

* <span data-ttu-id="a0338-357">Si è in grado di rilevare e rispondere agli eventi di rilevamento, spostamento e manipolazione della mano.</span><span class="sxs-lookup"><span data-stu-id="a0338-357">You know how to detect and respond to hand tracking, navigation and manipulation events.</span></span>
* <span data-ttu-id="a0338-358">Si comprende la differenza tra i movimenti di spostamento e manipolazione.</span><span class="sxs-lookup"><span data-stu-id="a0338-358">You understand the difference between Navigation and Manipulation gestures.</span></span>
* <span data-ttu-id="a0338-359">Si è appreso come modificare il cursore per fornire commenti visivi quando viene rilevata una mano, quando una mano sta per andare persa e quando un oggetto supporta interazioni diverse (spostamento e manipolazione).</span><span class="sxs-lookup"><span data-stu-id="a0338-359">You know how to change the cursor to provide visual feedback for when a hand is detected, when a hand is about to be lost, and for when an object supports different interactions (Navigation vs Manipulation).</span></span>

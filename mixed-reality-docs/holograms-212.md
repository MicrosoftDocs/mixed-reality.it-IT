---
title: Input MR 212 - voce
description: Seguire questa procedura dettagliata di scrittura del codice grazie a Unity, Visual Studio e HoloLens per informazioni dettagliate su concetti vocali.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit unity, academy, esercitazione, vocali
ms.openlocfilehash: 7e792bf40c47d4e1d57898fbe75ad050a030b7e3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59598923"
---
>[!NOTE]
><span data-ttu-id="c4a76-104">Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.</span><span class="sxs-lookup"><span data-stu-id="c4a76-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="c4a76-105">Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.</span><span class="sxs-lookup"><span data-stu-id="c4a76-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="c4a76-106">Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.</span><span class="sxs-lookup"><span data-stu-id="c4a76-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="c4a76-107">Essi verranno mantenute per continuare a utilizzare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="c4a76-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="c4a76-108">Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="c4a76-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="c4a76-109">Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.</span><span class="sxs-lookup"><span data-stu-id="c4a76-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-input-212-voice"></a><span data-ttu-id="c4a76-110">Input di MR 212: Comandi vocali</span><span class="sxs-lookup"><span data-stu-id="c4a76-110">MR Input 212: Voice</span></span>

<span data-ttu-id="c4a76-111">[Input vocale](voice-input.md) offre un altro modo per interagire con i nostri vntana.</span><span class="sxs-lookup"><span data-stu-id="c4a76-111">[Voice input](voice-input.md) gives us another way to interact with our holograms.</span></span> <span data-ttu-id="c4a76-112">I comandi vocali funzionano in modo molto semplice e naturale.</span><span class="sxs-lookup"><span data-stu-id="c4a76-112">Voice commands work in a very natural and easy way.</span></span> <span data-ttu-id="c4a76-113">Progettare i comandi vocali in modo che siano:</span><span class="sxs-lookup"><span data-stu-id="c4a76-113">Design your voice commands so that they are:</span></span>

* <span data-ttu-id="c4a76-114">Naturale</span><span class="sxs-lookup"><span data-stu-id="c4a76-114">Natural</span></span>
* <span data-ttu-id="c4a76-115">Facile da ricordare</span><span class="sxs-lookup"><span data-stu-id="c4a76-115">Easy to remember</span></span>
* <span data-ttu-id="c4a76-116">Contesto adeguato</span><span class="sxs-lookup"><span data-stu-id="c4a76-116">Context appropriate</span></span>
* <span data-ttu-id="c4a76-117">Sufficientemente distinto da altre opzioni nello stesso contesto</span><span class="sxs-lookup"><span data-stu-id="c4a76-117">Sufficiently distinct from other options within the same context</span></span>

>[!VIDEO https://www.youtube.com/embed/BYpYsVFYjdw]

<span data-ttu-id="c4a76-118">Nelle [MR nozioni di base 101](holograms-101.md), abbiamo usato la KeywordRecognizer per creare due comandi vocali semplice.</span><span class="sxs-lookup"><span data-stu-id="c4a76-118">In [MR Basics 101](holograms-101.md), we used the KeywordRecognizer to build two simple voice commands.</span></span> <span data-ttu-id="c4a76-119">In 212 Input MR, verrà illustrato in modo approfonditi e Scopri come:</span><span class="sxs-lookup"><span data-stu-id="c4a76-119">In MR Input 212, we'll dive deeper and learn how to:</span></span>

* <span data-ttu-id="c4a76-120">Progettare i comandi vocali che sono ottimizzati per il motore di sintesi vocale HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c4a76-120">Design voice commands that are optimized for the HoloLens speech engine.</span></span>
* <span data-ttu-id="c4a76-121">Impostare l'utente con riconoscimento della voce che quali comandi sono disponibili.</span><span class="sxs-lookup"><span data-stu-id="c4a76-121">Make the user aware of what voice commands are available.</span></span>
* <span data-ttu-id="c4a76-122">Confermare che sono stati segnalati comando vocale dell'utente.</span><span class="sxs-lookup"><span data-stu-id="c4a76-122">Acknowledge that we've heard the user's voice command.</span></span>
* <span data-ttu-id="c4a76-123">Comprendere che cos'è l'utente che indica che, utilizzando un riconoscimento dettatura.</span><span class="sxs-lookup"><span data-stu-id="c4a76-123">Understand what the user is saying, using a Dictation Recognizer.</span></span>
* <span data-ttu-id="c4a76-124">Consente di restare in attesa per i comandi basati su un file SRGS o specifica della grammatica di riconoscimento vocale, una grammatica di riconoscimento.</span><span class="sxs-lookup"><span data-stu-id="c4a76-124">Use a Grammar Recognizer to listen for commands based on an SRGS, or Speech Recognition Grammar Specification, file.</span></span>

<span data-ttu-id="c4a76-125">In questo corso, questo aspetto verrà trattato Esplora modelli, che è stato creato nel [MR Input 210](holograms-210.md) e [MR Input 211](holograms-211.md).</span><span class="sxs-lookup"><span data-stu-id="c4a76-125">In this course, we'll revisit Model Explorer, which we built in [MR Input 210](holograms-210.md) and [MR Input 211](holograms-211.md).</span></span>

>[!IMPORTANT]
><span data-ttu-id="c4a76-126">I video incorporati in ognuna delle sezioni seguenti sono stati registrati usando una versione precedente di Unity e il Toolkit di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="c4a76-126">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="c4a76-127">Anche se le istruzioni dettagliate sono accurate e aggiornate, è possibile visualizzare gli script e gli oggetti visivi nei video corrispondenti che non sono aggiornati.</span><span class="sxs-lookup"><span data-stu-id="c4a76-127">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="c4a76-128">I video rimangono inclusi per ci si ricorderà più e perché i concetti illustrati sono applicano.</span><span class="sxs-lookup"><span data-stu-id="c4a76-128">The videos remain included for posterity and because the concepts covered still apply.</span></span>


## <a name="device-support"></a><span data-ttu-id="c4a76-129">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="c4a76-129">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="c4a76-130">Corso</span><span class="sxs-lookup"><span data-stu-id="c4a76-130">Course</span></span></th><th style="width:150px"> <span data-ttu-id="c4a76-131"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="c4a76-131"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="c4a76-132"><a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></span><span class="sxs-lookup"><span data-stu-id="c4a76-132"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="c4a76-133">Input di MR 212: Comandi vocali</span><span class="sxs-lookup"><span data-stu-id="c4a76-133">MR Input 212: Voice</span></span></td><td style="text-align: center;"> <span data-ttu-id="c4a76-134">✔️</span><span class="sxs-lookup"><span data-stu-id="c4a76-134">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="c4a76-135">✔️</span><span class="sxs-lookup"><span data-stu-id="c4a76-135">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="c4a76-136">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="c4a76-136">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="c4a76-137">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="c4a76-137">Prerequisites</span></span>

* <span data-ttu-id="c4a76-138">Un PC Windows 10 configurate con i valori corretti [sono installati gli strumenti](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="c4a76-138">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="c4a76-139">Alcuni basic C# capacità di programmazione.</span><span class="sxs-lookup"><span data-stu-id="c4a76-139">Some basic C# programming ability.</span></span>
* <span data-ttu-id="c4a76-140">È necessario avere completato [MR nozioni di base 101](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="c4a76-140">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="c4a76-141">È necessario avere completato [MR Input 210](holograms-210.md).</span><span class="sxs-lookup"><span data-stu-id="c4a76-141">You should have completed [MR Input 210](holograms-210.md).</span></span>
* <span data-ttu-id="c4a76-142">È necessario avere completato [MR Input 211](holograms-211.md).</span><span class="sxs-lookup"><span data-stu-id="c4a76-142">You should have completed [MR Input 211](holograms-211.md).</span></span>
* <span data-ttu-id="c4a76-143">Un dispositivo HoloLens [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="c4a76-143">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="c4a76-144">File di progetto</span><span class="sxs-lookup"><span data-stu-id="c4a76-144">Project files</span></span>

* <span data-ttu-id="c4a76-145">Scaricare il [file](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) necessarie per il progetto.</span><span class="sxs-lookup"><span data-stu-id="c4a76-145">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) required by the project.</span></span> <span data-ttu-id="c4a76-146">Richiede Unity 2017.2 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="c4a76-146">Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="c4a76-147">Annullare la-archive i file sul desktop o altri facile da raggiungere percorso.</span><span class="sxs-lookup"><span data-stu-id="c4a76-147">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="c4a76-148">Se si desidera esaminare il codice sorgente prima di scaricare, ha [disponibile in GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).</span><span class="sxs-lookup"><span data-stu-id="c4a76-148">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="c4a76-149">Errori e note</span><span class="sxs-lookup"><span data-stu-id="c4a76-149">Errata and Notes</span></span>

* <span data-ttu-id="c4a76-150">"Abilita Just My Code" deve essere disabilitato (*unchecked*) in Visual Studio in Strumenti -> Opzioni -> debug per poter raggiungere punti di interruzione nel codice.</span><span class="sxs-lookup"><span data-stu-id="c4a76-150">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="unity-setup"></a><span data-ttu-id="c4a76-151">Programma di installazione di Unity</span><span class="sxs-lookup"><span data-stu-id="c4a76-151">Unity Setup</span></span>

### <a name="instructions"></a><span data-ttu-id="c4a76-152">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="c4a76-152">Instructions</span></span>

1. <span data-ttu-id="c4a76-153">Avviare Unity.</span><span class="sxs-lookup"><span data-stu-id="c4a76-153">Start Unity.</span></span>
2. <span data-ttu-id="c4a76-154">Selezionare **aperto**.</span><span class="sxs-lookup"><span data-stu-id="c4a76-154">Select **Open**.</span></span>
3. <span data-ttu-id="c4a76-155">Passare al **HolographicAcademy-Vntana 212 Voice** cartella è archiviato in precedenza di annullamento.</span><span class="sxs-lookup"><span data-stu-id="c4a76-155">Navigate to the **HolographicAcademy-Holograms-212-Voice** folder you previously un-archived.</span></span>
4. <span data-ttu-id="c4a76-156">Individuare e selezionare il **Starting**/**Esplora modelli** cartella.</span><span class="sxs-lookup"><span data-stu-id="c4a76-156">Find and select the **Starting**/**Model Explorer** folder.</span></span>
5. <span data-ttu-id="c4a76-157">Scegliere il **selezionare la cartella** pulsante.</span><span class="sxs-lookup"><span data-stu-id="c4a76-157">Click the **Select Folder** button.</span></span>
6. <span data-ttu-id="c4a76-158">Nel **Project** panel, espandere il **scene** cartella.</span><span class="sxs-lookup"><span data-stu-id="c4a76-158">In the **Project** panel, expand the **Scenes** folder.</span></span>
7. <span data-ttu-id="c4a76-159">Fare doppio clic su **ModelExplorer** scena a caricarlo in Unity.</span><span class="sxs-lookup"><span data-stu-id="c4a76-159">Double-click **ModelExplorer** scene to load it in Unity.</span></span>

### <a name="building"></a><span data-ttu-id="c4a76-160">Compilazione</span><span class="sxs-lookup"><span data-stu-id="c4a76-160">Building</span></span>

1. <span data-ttu-id="c4a76-161">In Unity, selezionare **File > Build Settings**.</span><span class="sxs-lookup"><span data-stu-id="c4a76-161">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="c4a76-162">Se **scene/ModelExplorer** non è elencato nella **scene nella compilazione**, fare clic su **aggiungere scene Open** per aggiungere la scena.</span><span class="sxs-lookup"><span data-stu-id="c4a76-162">If **Scenes/ModelExplorer** is not listed in **Scenes In Build**, click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="c4a76-163">Se si sta sviluppando in modo specifico per HoloLens, impostare **dispositivo di destinazione** al **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="c4a76-163">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="c4a76-164">In caso contrario, ci si trova sulla **tutti i dispositivi**.</span><span class="sxs-lookup"><span data-stu-id="c4a76-164">Otherwise, leave it on **Any device**.</span></span>
4. <span data-ttu-id="c4a76-165">Assicurarsi **tipo di compilazione** è impostata su **D3D** e **SDK** è impostata su **installata più recente** (che deve essere SDK 16299 o versione successiva).</span><span class="sxs-lookup"><span data-stu-id="c4a76-165">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
5. <span data-ttu-id="c4a76-166">Fai clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="c4a76-166">Click **Build**.</span></span>
6. <span data-ttu-id="c4a76-167">Creare un **nuova cartella** denominato "App".</span><span class="sxs-lookup"><span data-stu-id="c4a76-167">Create a **New Folder** named "App".</span></span>
7. <span data-ttu-id="c4a76-168">Solo clic i **App** cartella.</span><span class="sxs-lookup"><span data-stu-id="c4a76-168">Single click the **App** folder.</span></span>
8. <span data-ttu-id="c4a76-169">Premere **selezionare la cartella** e Unity verrà avviata la compilazione del progetto per Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c4a76-169">Press **Select Folder** and Unity will start building the project for Visual Studio.</span></span>

<span data-ttu-id="c4a76-170">Quando Unity viene eseguita, verrà visualizzata una finestra di Esplora File.</span><span class="sxs-lookup"><span data-stu-id="c4a76-170">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="c4a76-171">Aprire il **App** cartella.</span><span class="sxs-lookup"><span data-stu-id="c4a76-171">Open the **App** folder.</span></span>
2. <span data-ttu-id="c4a76-172">Aprire il **soluzione ModelExplorer Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="c4a76-172">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="c4a76-173">Se la distribuzione in HoloLens:</span><span class="sxs-lookup"><span data-stu-id="c4a76-173">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="c4a76-174">Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione di debug per **Release** e da ARM a **x86**.</span><span class="sxs-lookup"><span data-stu-id="c4a76-174">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="c4a76-175">Fare clic sull'elenco a discesa sulla freccia accanto al pulsante computer locale e selezionare **computer remoto**.</span><span class="sxs-lookup"><span data-stu-id="c4a76-175">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="c4a76-176">Immettere **l'indirizzo IP del dispositivo HoloLens** e impostare la modalità di autenticazione **universale (protocollo non crittografato)**.</span><span class="sxs-lookup"><span data-stu-id="c4a76-176">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="c4a76-177">Fare clic su **Seleziona**.</span><span class="sxs-lookup"><span data-stu-id="c4a76-177">Click **Select**.</span></span> <span data-ttu-id="c4a76-178">Se non si conosce l'indirizzo IP del dispositivo, esaminare **Impostazioni > rete e Internet > Opzioni avanzate**.</span><span class="sxs-lookup"><span data-stu-id="c4a76-178">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="c4a76-179">Nella barra dei menu superiore, fare clic su **Debug -> Avvia senza eseguire debug** o premere **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="c4a76-179">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="c4a76-180">Se questa è la prima volta che la distribuzione nel dispositivo, devi [abbinarlo a Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span><span class="sxs-lookup"><span data-stu-id="c4a76-180">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
5. <span data-ttu-id="c4a76-181">Quando l'app è distribuita, ignorare il **Fitbox** con un **movimento selezionare**.</span><span class="sxs-lookup"><span data-stu-id="c4a76-181">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="c4a76-182">Se la distribuzione in un visore VR immersivi:</span><span class="sxs-lookup"><span data-stu-id="c4a76-182">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="c4a76-183">Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione di debug per **Release** e da ARM a **x64**.</span><span class="sxs-lookup"><span data-stu-id="c4a76-183">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="c4a76-184">Verificare che la destinazione di distribuzione è impostata su **computer locale**.</span><span class="sxs-lookup"><span data-stu-id="c4a76-184">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="c4a76-185">Nella barra dei menu superiore, fare clic su **Debug -> Avvia senza eseguire debug** o premere **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="c4a76-185">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="c4a76-186">Quando l'app è distribuita, ignorare il **Fitbox** spostando il trigger in un controller di movimento.</span><span class="sxs-lookup"><span data-stu-id="c4a76-186">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

>[!NOTE]
><span data-ttu-id="c4a76-187">È possibile riscontrare alcuni errori rosso nel Pannello di errori di Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c4a76-187">You might notice some red errors in the Visual Studio Errors panel.</span></span> <span data-ttu-id="c4a76-188">È possibile ignorarli.</span><span class="sxs-lookup"><span data-stu-id="c4a76-188">It is safe to ignore them.</span></span> <span data-ttu-id="c4a76-189">Passare al pannello di Output per visualizzare effettivamente lo stato della compilazione.</span><span class="sxs-lookup"><span data-stu-id="c4a76-189">Switch to the Output panel to view actual build progress.</span></span> <span data-ttu-id="c4a76-190">Gli errori nel Pannello di Output è necessario rendere una correzione (più spesso che sono causati da un errore in uno script).</span><span class="sxs-lookup"><span data-stu-id="c4a76-190">Errors in the Output panel will require you to make a fix (most often they are caused by a mistake in a script).</span></span>

## <a name="chapter-1---awareness"></a><span data-ttu-id="c4a76-191">Capitolo 1 - riconoscimento</span><span class="sxs-lookup"><span data-stu-id="c4a76-191">Chapter 1 - Awareness</span></span>

>[!VIDEO https://www.youtube.com/embed/fDwijJWuEc0]

### <a name="objectives"></a><span data-ttu-id="c4a76-192">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="c4a76-192">Objectives</span></span>

* <span data-ttu-id="c4a76-193">Scopri le **consigliate e sconsigliate** di progettazione dei comandi vocali.</span><span class="sxs-lookup"><span data-stu-id="c4a76-193">Learn the **Dos and Don'ts** of voice command design.</span></span>
* <span data-ttu-id="c4a76-194">Uso **KeywordRecognizer** aggiungere comandi vocali sguardo basato.</span><span class="sxs-lookup"><span data-stu-id="c4a76-194">Use **KeywordRecognizer** to add gaze based voice commands.</span></span>
* <span data-ttu-id="c4a76-195">Rendere gli utenti consapevoli di comandi vocali tramite cursore **commenti e suggerimenti**.</span><span class="sxs-lookup"><span data-stu-id="c4a76-195">Make users aware of voice commands using cursor **feedback**.</span></span>

### <a name="voice-command-design"></a><span data-ttu-id="c4a76-196">Progettazione dei comandi vocali</span><span class="sxs-lookup"><span data-stu-id="c4a76-196">Voice Command Design</span></span>

<span data-ttu-id="c4a76-197">In questo capitolo, si apprenderà sulla progettazione di comandi vocali.</span><span class="sxs-lookup"><span data-stu-id="c4a76-197">In this chapter, you'll learn about designing voice commands.</span></span> <span data-ttu-id="c4a76-198">Durante la creazione di comandi vocali:</span><span class="sxs-lookup"><span data-stu-id="c4a76-198">When creating voice commands:</span></span>

#### <a name="do"></a><span data-ttu-id="c4a76-199">DO</span><span class="sxs-lookup"><span data-stu-id="c4a76-199">DO</span></span>

* <span data-ttu-id="c4a76-200">Creare comandi concisi.</span><span class="sxs-lookup"><span data-stu-id="c4a76-200">Create concise commands.</span></span> <span data-ttu-id="c4a76-201">Non si vuole usare *"Guarda il video attualmente selezionato"*, perché tale comando non è più conciso e verrebbe rimosse con facilità dall'utente.</span><span class="sxs-lookup"><span data-stu-id="c4a76-201">You don't want to use *"Play the currently selected video"*, because that command is not concise and would easily be forgotten by the user.</span></span> <span data-ttu-id="c4a76-202">In alternativa, è consigliabile utilizzare: *"Riproduci Video"*, in quanto è concisa e ha più sillabe.</span><span class="sxs-lookup"><span data-stu-id="c4a76-202">Instead, you should use: *"Play Video"*, because it is concise and has multiple syllables.</span></span>
* <span data-ttu-id="c4a76-203">Usare un vocabolario semplice.</span><span class="sxs-lookup"><span data-stu-id="c4a76-203">Use a simple vocabulary.</span></span> <span data-ttu-id="c4a76-204">Sempre provare a usare parole e frasi semplici per l'utente di individuare e tenere presente che comuni.</span><span class="sxs-lookup"><span data-stu-id="c4a76-204">Always try to use common words and phrases that are easy for the user to discover and remember.</span></span> <span data-ttu-id="c4a76-205">Ad esempio, se l'applicazione dispone di un oggetto si noti che potrebbe essere visualizzato o nascosto dalla visualizzazione, non utilizzare il comando *"Mostra manifesto"*, perché "manifesto" è un termine usato raramente.</span><span class="sxs-lookup"><span data-stu-id="c4a76-205">For example, if your application had a note object that could be displayed or hidden from view, you would not use the command *"Show Placard"*, because "placard" is a rarely used term.</span></span> <span data-ttu-id="c4a76-206">In alternativa, utilizzare il comando: *"Show nota"*, per visualizzare la nota all'interno dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="c4a76-206">Instead, you would use the command: *"Show Note"*, to reveal the note in your application.</span></span>
* <span data-ttu-id="c4a76-207">Mantenere la coerenza.</span><span class="sxs-lookup"><span data-stu-id="c4a76-207">Be consistent.</span></span> <span data-ttu-id="c4a76-208">I comandi vocali devono essere mantenuti coerenti tra l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="c4a76-208">Voice commands should be kept consistent across your application.</span></span> <span data-ttu-id="c4a76-209">Si supponga di avere due scene nell'applicazione e che entrambe le scene contengono un pulsante della chiusura dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="c4a76-209">Imagine that you have two scenes in your application and both scenes contain a button for closing the application.</span></span> <span data-ttu-id="c4a76-210">Se il comando utilizzato prima scena *"Esci"* per attivare il pulsante, ma il secondo scena utilizzato il comando *"Chiudi App"*, quindi l'utente dovrà verificare alcuni problemi.</span><span class="sxs-lookup"><span data-stu-id="c4a76-210">If the first scene used the command *"Exit"* to trigger the button, but the second scene used the command *"Close App"*, then the user is going to get very confused.</span></span> <span data-ttu-id="c4a76-211">Se la stessa funzionalità vengono mantenute per le scene più, quindi lo stesso comando vocali da utilizzare per attivarlo.</span><span class="sxs-lookup"><span data-stu-id="c4a76-211">If the same functionality persists across multiple scenes, then the same voice command should be used to trigger it.</span></span>

#### <a name="dont"></a><span data-ttu-id="c4a76-212">DON'T</span><span class="sxs-lookup"><span data-stu-id="c4a76-212">DON'T</span></span>

* <span data-ttu-id="c4a76-213">Usare i comandi sillaba singolo.</span><span class="sxs-lookup"><span data-stu-id="c4a76-213">Use single syllable commands.</span></span> <span data-ttu-id="c4a76-214">Ad esempio, se si crea un comando vocale per riprodurre un video, è consigliabile evitare di usare il comando semplice *"Riprodurre"*, perché è solo una sillaba singola e possono andare perse con facilità dal sistema.</span><span class="sxs-lookup"><span data-stu-id="c4a76-214">As an example, if you were creating a voice command to play a video, you should avoid using the simple command *"Play"*, as it is only a single syllable and could easily be missed by the system.</span></span> <span data-ttu-id="c4a76-215">In alternativa, è consigliabile utilizzare: *"Riproduci Video"*, in quanto è concisa e ha più sillabe.</span><span class="sxs-lookup"><span data-stu-id="c4a76-215">Instead, you should use: *"Play Video"*, because it is concise and has multiple syllables.</span></span>
* <span data-ttu-id="c4a76-216">Usare i comandi del sistema.</span><span class="sxs-lookup"><span data-stu-id="c4a76-216">Use system commands.</span></span> <span data-ttu-id="c4a76-217">Il *"Selezionare"* comando è riservato dal sistema per attivare un evento di tocco per l'oggetto attualmente con lo stato attivo.</span><span class="sxs-lookup"><span data-stu-id="c4a76-217">The *"Select"* command is reserved by the system to trigger a Tap event for the currently focused object.</span></span> <span data-ttu-id="c4a76-218">Non usare nuovamente il *"Selezionare"* comando in una parola chiave o una frase, mentre potrebbe non funzionare come previsto.</span><span class="sxs-lookup"><span data-stu-id="c4a76-218">Do not re-use the *"Select"* command in a keyword or phrase, as it might not work as you expect.</span></span> <span data-ttu-id="c4a76-219">Ad esempio, se la voce di comando per la selezione di un cubo all'interno dell'applicazione è stata *"Seleziona cubo"*, ma l'utente è stato esaminando una sfera quando essi pronunciato del comando, quindi verrà selezionata invece la sfera.</span><span class="sxs-lookup"><span data-stu-id="c4a76-219">For example, if the voice command for selecting a cube in your application was *"Select cube"*, but the user was looking at a sphere when they uttered the command, then the sphere would be selected instead.</span></span> <span data-ttu-id="c4a76-220">Allo stesso modo della barra dei comandi di app sono servizio voce abilitato.</span><span class="sxs-lookup"><span data-stu-id="c4a76-220">Similarly app bar commands are voice enabled.</span></span> <span data-ttu-id="c4a76-221">Non usare i comandi seguenti di riconoscimento vocale nella propria visualizzazione CoreWindow:</span><span class="sxs-lookup"><span data-stu-id="c4a76-221">Don't use the following speech commands in your CoreWindow View:</span></span>
    1. <span data-ttu-id="c4a76-222">tornare indietro</span><span class="sxs-lookup"><span data-stu-id="c4a76-222">Go Back</span></span>
    2. <span data-ttu-id="c4a76-223">Strumento di scorrimento</span><span class="sxs-lookup"><span data-stu-id="c4a76-223">Scroll Tool</span></span>
    3. <span data-ttu-id="c4a76-224">Strumento Zoom</span><span class="sxs-lookup"><span data-stu-id="c4a76-224">Zoom Tool</span></span>
    4. <span data-ttu-id="c4a76-225">Strumento di trascinamento</span><span class="sxs-lookup"><span data-stu-id="c4a76-225">Drag Tool</span></span>
    5. <span data-ttu-id="c4a76-226">Regolare</span><span class="sxs-lookup"><span data-stu-id="c4a76-226">Adjust</span></span>
    6. <span data-ttu-id="c4a76-227">Rimuovi</span><span class="sxs-lookup"><span data-stu-id="c4a76-227">Remove</span></span>
* <span data-ttu-id="c4a76-228">Usare suono simile.</span><span class="sxs-lookup"><span data-stu-id="c4a76-228">Use similar sounds.</span></span> <span data-ttu-id="c4a76-229">Provare a evitare di usare i comandi vocali che rhyme.</span><span class="sxs-lookup"><span data-stu-id="c4a76-229">Try to avoid using voice commands that rhyme.</span></span> <span data-ttu-id="c4a76-230">Se si dispone di un'applicazione shopping supportata *"Mostra Store"* e *"Mostra più"* come comandi vocali, sarebbe opportuno disabilitare uno dei comandi, mentre l'altro è in uso.</span><span class="sxs-lookup"><span data-stu-id="c4a76-230">If you had a shopping application which supported *"Show Store"* and *"Show More"* as voice commands, then you would want to disable one of the commands while the other was in use.</span></span> <span data-ttu-id="c4a76-231">Ad esempio, è possibile usare la *"Mostra Store"* pulsante per aprire lo store e quindi disabilitare tale comando quando l'archivio è stato visualizzato in modo che il *"Mostra più"* comando può essere usato per l'esplorazione.</span><span class="sxs-lookup"><span data-stu-id="c4a76-231">For example, you could use the *"Show Store"* button to open the store, and then disable that command when the store was displayed so that the *"Show More"* command could be used for browsing.</span></span>

### <a name="instructions"></a><span data-ttu-id="c4a76-232">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="c4a76-232">Instructions</span></span>

* <span data-ttu-id="c4a76-233">Nella finestra di Unity **gerarchia** del pannello, usare lo strumento di ricerca per trovare il **holoComm_screen_mesh** oggetto.</span><span class="sxs-lookup"><span data-stu-id="c4a76-233">In Unity's **Hierarchy** panel, use the search tool to find the **holoComm_screen_mesh** object.</span></span>
* <span data-ttu-id="c4a76-234">Fare doppio clic sulla **holoComm_screen_mesh** oggetto per la visualizzazione nel **scena**.</span><span class="sxs-lookup"><span data-stu-id="c4a76-234">Double-click on the **holoComm_screen_mesh** object to view it in the **Scene**.</span></span> <span data-ttu-id="c4a76-235">Si tratta di espressioni di controllo del astronautici, che risponderà per i comandi vocali.</span><span class="sxs-lookup"><span data-stu-id="c4a76-235">This is the astronaut's watch, which will respond to our voice commands.</span></span>
* <span data-ttu-id="c4a76-236">Nel **Inspector** panel, individuare il **origine di Input vocale (Script)** componente.</span><span class="sxs-lookup"><span data-stu-id="c4a76-236">In the **Inspector** panel, locate the **Speech Input Source (Script)** component.</span></span>
* <span data-ttu-id="c4a76-237">Espandere la **parole chiave** sezione per visualizzare i comandi vocali supportate: **Aprire Communicator**.</span><span class="sxs-lookup"><span data-stu-id="c4a76-237">Expand the **Keywords** section to see the supported voice command: **Open Communicator**.</span></span>
* <span data-ttu-id="c4a76-238">Fare clic sull'icona dell'ingranaggio a destra, quindi selezionare **modifica Script**.</span><span class="sxs-lookup"><span data-stu-id="c4a76-238">Click the cog to the right side, then select **Edit Script**.</span></span>
* <span data-ttu-id="c4a76-239">Esplorare **SpeechInputSource.cs** per comprendere come viene utilizzato il **KeywordRecognizer** aggiungere comandi vocali.</span><span class="sxs-lookup"><span data-stu-id="c4a76-239">Explore **SpeechInputSource.cs** to understand how it uses the **KeywordRecognizer** to add voice commands.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="c4a76-240">Compilare e distribuire</span><span class="sxs-lookup"><span data-stu-id="c4a76-240">Build and Deploy</span></span>

* <span data-ttu-id="c4a76-241">In Unity, usare **File > Build Settings** per ricompili l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="c4a76-241">In Unity, use **File > Build Settings** to rebuild the application.</span></span>
* <span data-ttu-id="c4a76-242">Aprire il **App** cartella.</span><span class="sxs-lookup"><span data-stu-id="c4a76-242">Open the **App** folder.</span></span>
* <span data-ttu-id="c4a76-243">Aprire il **soluzione ModelExplorer Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="c4a76-243">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="c4a76-244">(Se è stato creato o distribuito questo progetto in Visual Studio durante la configurazione, quindi è possibile aprire quell'istanza di Visual Studio e fare clic su 'Ricarica tutto' quando viene richiesto).</span><span class="sxs-lookup"><span data-stu-id="c4a76-244">(If you already built/deployed this project in Visual Studio during set-up, then you can open that instance of VS and click 'Reload All' when prompted).</span></span>

* <span data-ttu-id="c4a76-245">In Visual Studio, fare clic su **Debug -> Avvia senza eseguire debug** o premere **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="c4a76-245">In Visual Studio, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="c4a76-246">Dopo la distribuzione dell'applicazione per il HoloLens, chiudere la finestra appropriato usando il [puntato](gestures.md#air-tap) movimento.</span><span class="sxs-lookup"><span data-stu-id="c4a76-246">After the application deploys to the HoloLens, dismiss the fit box using the [air-tap](gestures.md#air-tap) gesture.</span></span>
* <span data-ttu-id="c4a76-247">Fissare espressioni di controllo del astronautici.</span><span class="sxs-lookup"><span data-stu-id="c4a76-247">Gaze at the astronaut's watch.</span></span>
* <span data-ttu-id="c4a76-248">Quando l'espressione di controllo ha lo stato attivo, verificare che il cursore assuma un microfono.</span><span class="sxs-lookup"><span data-stu-id="c4a76-248">When the watch has focus, verify that the cursor changes to a microphone.</span></span> <span data-ttu-id="c4a76-249">Ciò fornisce un feedback che l'applicazione è in ascolto per i comandi vocali.</span><span class="sxs-lookup"><span data-stu-id="c4a76-249">This provides feedback that the application is listening for voice commands.</span></span>
* <span data-ttu-id="c4a76-250">Verificare che viene visualizzato un suggerimento sulle espressioni di controllo.</span><span class="sxs-lookup"><span data-stu-id="c4a76-250">Verify that a tooltip appears on the watch.</span></span> <span data-ttu-id="c4a76-251">Ciò consente agli utenti di individuare il *"Communicator Open"* comando.</span><span class="sxs-lookup"><span data-stu-id="c4a76-251">This helps users discover the *"Open Communicator"* command.</span></span>
* <span data-ttu-id="c4a76-252">Mentre gazing all'orologio, pronunciare *"Communicator aprire"* per aprire il pannello di communicator.</span><span class="sxs-lookup"><span data-stu-id="c4a76-252">While gazing at the watch, say *"Open Communicator"* to open the communicator panel.</span></span>

## <a name="chapter-2---acknowledgement"></a><span data-ttu-id="c4a76-253">Capitolo 2 - Acknowledgement</span><span class="sxs-lookup"><span data-stu-id="c4a76-253">Chapter 2 - Acknowledgement</span></span>

>[!VIDEO https://www.youtube.com/embed/87ViteoPpyU]

### <a name="objectives"></a><span data-ttu-id="c4a76-254">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="c4a76-254">Objectives</span></span>

* <span data-ttu-id="c4a76-255">Registrare un messaggio utilizzando l'input del microfono.</span><span class="sxs-lookup"><span data-stu-id="c4a76-255">Record a message using the Microphone input.</span></span>
* <span data-ttu-id="c4a76-256">Fornire commenti e suggerimenti all'utente che l'applicazione è in ascolto di comandi vocali.</span><span class="sxs-lookup"><span data-stu-id="c4a76-256">Give feedback to the user that the application is listening to their voice.</span></span>

>[!NOTE]
><span data-ttu-id="c4a76-257">Il **microfono** funzionalità devono essere dichiarate per un'app per la registrazione dal microfono.</span><span class="sxs-lookup"><span data-stu-id="c4a76-257">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="c4a76-258">Questa operazione viene eseguita per è già in MR Input 212, ma tenere a mente per i propri progetti.</span><span class="sxs-lookup"><span data-stu-id="c4a76-258">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="c4a76-259">Nell'Editor di Unity, passare alle impostazioni del giocatore, passare a "Modifica > progetto Impostazioni > Player"</span><span class="sxs-lookup"><span data-stu-id="c4a76-259">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="c4a76-260">Fare clic sulla scheda "Universal Windows Platform"</span><span class="sxs-lookup"><span data-stu-id="c4a76-260">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="c4a76-261">Nella sezione "Impostazioni > le funzionalità di pubblicazione", controllare la **microfono** funzionalità</span><span class="sxs-lookup"><span data-stu-id="c4a76-261">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="c4a76-262">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="c4a76-262">Instructions</span></span>

* <span data-ttu-id="c4a76-263">Nella finestra di Unity **gerarchia** panel, verificare che il **holoComm_screen_mesh** oggetto selezionato.</span><span class="sxs-lookup"><span data-stu-id="c4a76-263">In Unity's **Hierarchy** panel, verify that the **holoComm_screen_mesh** object is selected.</span></span>
* <span data-ttu-id="c4a76-264">Nel **Inspector** panel, trovare il **astronautici Watch (Script)** componente.</span><span class="sxs-lookup"><span data-stu-id="c4a76-264">In the **Inspector** panel, find the **Astronaut Watch (Script)** component.</span></span>
* <span data-ttu-id="c4a76-265">Fare clic sul cubo blu, di piccole dimensioni che viene impostato come valore dei **Communicator Prefab** proprietà.</span><span class="sxs-lookup"><span data-stu-id="c4a76-265">Click on the small, blue cube which is set as the value of the **Communicator Prefab** property.</span></span>
* <span data-ttu-id="c4a76-266">Nel **Project** pannello, il **Communicator** prefab avranno ora lo stato attivo.</span><span class="sxs-lookup"><span data-stu-id="c4a76-266">In the **Project** panel, the **Communicator** prefab should now have focus.</span></span>
* <span data-ttu-id="c4a76-267">Fare clic sui **Communicator** prefab nel **Project** pannello per visualizzare i relativi componenti nel **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="c4a76-267">Click on the **Communicator** prefab in the **Project** panel to view its components in the **Inspector**.</span></span>
* <span data-ttu-id="c4a76-268">Esaminare i **microfono Manager (Script)** componente, ciò permetterà di registrare la voce dell'utente.</span><span class="sxs-lookup"><span data-stu-id="c4a76-268">Look at the **Microphone Manager (Script)** component, this will allow us to record the user's voice.</span></span>
* <span data-ttu-id="c4a76-269">Si noti che il **Communicator** oggetto dispone di un **gestore di Input vocale (Script)** componente per la risposta per il **Invia messaggio** comando.</span><span class="sxs-lookup"><span data-stu-id="c4a76-269">Notice that the **Communicator** object has a **Speech Input Handler (Script)** component for responding to the **Send Message** command.</span></span>
* <span data-ttu-id="c4a76-270">Esaminare i **Communicator (Script)** componente e fare doppio clic su script per aprirlo in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c4a76-270">Look at the **Communicator (Script)** component and double-click on the script to open it in Visual Studio.</span></span>

<span data-ttu-id="c4a76-271">Communicator.cs è responsabile dell'impostazione gli stati del pulsante appropriato sulla periferica communicator.</span><span class="sxs-lookup"><span data-stu-id="c4a76-271">Communicator.cs is responsible for setting the proper button states on the communicator device.</span></span> <span data-ttu-id="c4a76-272">Ciò consentirà agli utenti di registrare un messaggio, riprodurlo e inviare il messaggio per l'astronautici.</span><span class="sxs-lookup"><span data-stu-id="c4a76-272">This will allow our users to record a message, play it back, and send the message to the astronaut.</span></span> <span data-ttu-id="c4a76-273">Inoltre verrà avviare e arrestare un formato wave animato, per confermare all'utente che è stata valere la loro opinione.</span><span class="sxs-lookup"><span data-stu-id="c4a76-273">It will also start and stop an animated wave form, to acknowledge to the user that their voice was heard.</span></span>

* <span data-ttu-id="c4a76-274">Nelle **Communicator.cs**, eliminare le righe seguenti (81 e 82) dalle **avviare** (metodo).</span><span class="sxs-lookup"><span data-stu-id="c4a76-274">In **Communicator.cs**, delete the following lines (81 and 82) from the **Start** method.</span></span> <span data-ttu-id="c4a76-275">Abilita il pulsante 'Record' di communicator.</span><span class="sxs-lookup"><span data-stu-id="c4a76-275">This will enable the 'Record' button on the communicator.</span></span>

```cs
// TODO: 2.a Delete the following two lines:
RecordButton.SetActive(false);
MessageUIRenderer.gameObject.SetActive(false);
```

### <a name="build-and-deploy"></a><span data-ttu-id="c4a76-276">Compilare e distribuire</span><span class="sxs-lookup"><span data-stu-id="c4a76-276">Build and Deploy</span></span>

* <span data-ttu-id="c4a76-277">In Visual Studio, ricompilare l'applicazione e la distribuzione nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c4a76-277">In Visual Studio, rebuild your application and deploy to the device.</span></span>
* <span data-ttu-id="c4a76-278">Fissare espressioni di controllo del astronautici e scelgo *"Communicator Open"* per mostrare il communicator.</span><span class="sxs-lookup"><span data-stu-id="c4a76-278">Gaze at the astronaut's watch and say *"Open Communicator"* to show the communicator.</span></span>
* <span data-ttu-id="c4a76-279">Premere il **Record** pulsante (microfono) per avviare la registrazione di un messaggio verbale per l'astronautici.</span><span class="sxs-lookup"><span data-stu-id="c4a76-279">Press the **Record** button (microphone) to start recording a verbal message for the astronaut.</span></span>
* <span data-ttu-id="c4a76-280">Inizia a parlare e verificare che l'animazione di wave viene riprodotta in communicator, il che fornisce feedback all'utente che sentire la propria voce.</span><span class="sxs-lookup"><span data-stu-id="c4a76-280">Start speaking, and verify that the wave animation plays on the communicator, which provides feedback to the user that their voice is heard.</span></span>
* <span data-ttu-id="c4a76-281">Premere il **arrestare** pulsante (quadrato a sinistra) e verificare che l'animazione di wave si arresta.</span><span class="sxs-lookup"><span data-stu-id="c4a76-281">Press the **Stop** button (left square), and verify that the wave animation stops running.</span></span>
* <span data-ttu-id="c4a76-282">Premere il **riprodurre** pulsante (triangolo) per riprodurre il messaggio registrato e invita i clienti nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c4a76-282">Press the **Play** button (right triangle) to play back the recorded message and hear it on the device.</span></span>
* <span data-ttu-id="c4a76-283">Premere il **arrestare** pulsante (quadrata a destra) per arrestare la riproduzione del messaggio registrato.</span><span class="sxs-lookup"><span data-stu-id="c4a76-283">Press the **Stop** button (right square) to stop playback of the recorded message.</span></span>
* <span data-ttu-id="c4a76-284">Pronunciare *"Invia messaggio"* per chiudere il communicator e ricevere una risposta di 'Messaggio ricevuto' l'astronautici.</span><span class="sxs-lookup"><span data-stu-id="c4a76-284">Say *"Send Message"* to close the communicator and receive a 'Message Received' response from the astronaut.</span></span>

## <a name="chapter-3---understanding-and-the-dictation-recognizer"></a><span data-ttu-id="c4a76-285">Capitolo 3 - comprensione e il riconoscimento dettatura</span><span class="sxs-lookup"><span data-stu-id="c4a76-285">Chapter 3 - Understanding and the Dictation Recognizer</span></span>

>[!VIDEO https://www.youtube.com/embed/TIMddr-HqEU]

### <a name="objectives"></a><span data-ttu-id="c4a76-286">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="c4a76-286">Objectives</span></span>

* <span data-ttu-id="c4a76-287">Usare il riconoscimento dettatura per convertire il riconoscimento vocale dell'utente in testo.</span><span class="sxs-lookup"><span data-stu-id="c4a76-287">Use the Dictation Recognizer to convert the user's speech to text.</span></span>
* <span data-ttu-id="c4a76-288">Visualizzare i risultati ipotizzati e finali del motore di riconoscimento dettatura di communicator.</span><span class="sxs-lookup"><span data-stu-id="c4a76-288">Show the Dictation Recognizer's hypothesized and final results in the communicator.</span></span>

<span data-ttu-id="c4a76-289">In questo capitolo, si userà il riconoscimento dettatura per creare un messaggio per l'astronautici.</span><span class="sxs-lookup"><span data-stu-id="c4a76-289">In this chapter, we'll use the Dictation Recognizer to create a message for the astronaut.</span></span> <span data-ttu-id="c4a76-290">Quando si usa il riconoscimento dettatura, tenere presente che:</span><span class="sxs-lookup"><span data-stu-id="c4a76-290">When using the Dictation Recognizer, keep in mind that:</span></span>

* <span data-ttu-id="c4a76-291">È necessario essere connessi al Wi-Fi per il riconoscimento dettatura a funzionare.</span><span class="sxs-lookup"><span data-stu-id="c4a76-291">You must be connected to WiFi for the Dictation Recognizer to work.</span></span>
* <span data-ttu-id="c4a76-292">I timeout si verificano dopo un periodo di tempo.</span><span class="sxs-lookup"><span data-stu-id="c4a76-292">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="c4a76-293">Esistono due timeout da tenere presenti:</span><span class="sxs-lookup"><span data-stu-id="c4a76-293">There are two timeouts to be aware of:</span></span>
  * <span data-ttu-id="c4a76-294">Se il riconoscimento viene avviato e non ascolta l'audio per i primi cinque secondi, si verifica un timeout.</span><span class="sxs-lookup"><span data-stu-id="c4a76-294">If the recognizer starts and doesn't hear any audio for the first five seconds, it will timeout.</span></span>
  * <span data-ttu-id="c4a76-295">Se il riconoscimento ha fornito un risultato, ma quindi ascolta silenzio per venti secondi, si verifica un timeout.</span><span class="sxs-lookup"><span data-stu-id="c4a76-295">If the recognizer has given a result but then hears silence for twenty seconds, it will timeout.</span></span>
* <span data-ttu-id="c4a76-296">Un solo tipo di riconoscimento (parola chiave o la dettatura) possa eseguire contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="c4a76-296">Only one type of recognizer (Keyword or Dictation) can run at a time.</span></span>

>[!NOTE]
><span data-ttu-id="c4a76-297">Il **microfono** funzionalità devono essere dichiarate per un'app per la registrazione dal microfono.</span><span class="sxs-lookup"><span data-stu-id="c4a76-297">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="c4a76-298">Questa operazione viene eseguita per è già in MR Input 212, ma tenere a mente per i propri progetti.</span><span class="sxs-lookup"><span data-stu-id="c4a76-298">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="c4a76-299">Nell'Editor di Unity, passare alle impostazioni del giocatore, passare a "Modifica > progetto Impostazioni > Player"</span><span class="sxs-lookup"><span data-stu-id="c4a76-299">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="c4a76-300">Fare clic sulla scheda "Universal Windows Platform"</span><span class="sxs-lookup"><span data-stu-id="c4a76-300">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="c4a76-301">Nella sezione "Impostazioni > le funzionalità di pubblicazione", controllare la **microfono** funzionalità</span><span class="sxs-lookup"><span data-stu-id="c4a76-301">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="c4a76-302">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="c4a76-302">Instructions</span></span>

<span data-ttu-id="c4a76-303">Dobbiamo modificare **MicrophoneManager.cs** usare il riconoscimento dettatura.</span><span class="sxs-lookup"><span data-stu-id="c4a76-303">We're going to edit **MicrophoneManager.cs** to use the Dictation Recognizer.</span></span> <span data-ttu-id="c4a76-304">Questo è ciò che verrà aggiunto:</span><span class="sxs-lookup"><span data-stu-id="c4a76-304">This is what we'll add:</span></span>

1. <span data-ttu-id="c4a76-305">Quando la **pulsante Record** è premuto, ti invieremo **avvia il DictationRecognizer**.</span><span class="sxs-lookup"><span data-stu-id="c4a76-305">When the **Record button** is pressed, we'll **start the DictationRecognizer**.</span></span>
2. <span data-ttu-id="c4a76-306">Mostra le **ipotesi** di ciò che il DictationRecognizer compreso.</span><span class="sxs-lookup"><span data-stu-id="c4a76-306">Show the **hypothesis** of what the DictationRecognizer understood.</span></span>
3. <span data-ttu-id="c4a76-307">Bloccare le **risultati** di ciò che il DictationRecognizer compreso.</span><span class="sxs-lookup"><span data-stu-id="c4a76-307">Lock in the **results** of what the DictationRecognizer understood.</span></span>
4. <span data-ttu-id="c4a76-308">Controllo per i timeout dal DictationRecognizer.</span><span class="sxs-lookup"><span data-stu-id="c4a76-308">Check for timeouts from the DictationRecognizer.</span></span>
5. <span data-ttu-id="c4a76-309">Quando la **pulsante di arresto** viene premuto, o timeout della sessione mic, **arrestare il DictationRecognizer**.</span><span class="sxs-lookup"><span data-stu-id="c4a76-309">When the **Stop button** is pressed, or the mic session times out, **stop the DictationRecognizer**.</span></span>
6. <span data-ttu-id="c4a76-310">Riavviare il **KeywordRecognizer**, che sarà in ascolto per il **Send Message** comando.</span><span class="sxs-lookup"><span data-stu-id="c4a76-310">Restart the **KeywordRecognizer**, which will listen for the **Send Message** command.</span></span>

<span data-ttu-id="c4a76-311">Cominciamo.</span><span class="sxs-lookup"><span data-stu-id="c4a76-311">Let's get started.</span></span> <span data-ttu-id="c4a76-312">Completare Tutti esercizi sulla codifica per 3.a nelle **MicrophoneManager.cs**, oppure copiare e incollare il codice disponibile di seguito:</span><span class="sxs-lookup"><span data-stu-id="c4a76-312">Complete all coding exercises for 3.a in **MicrophoneManager.cs**, or copy and paste the finished code found below:</span></span>

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

### <a name="build-and-deploy"></a><span data-ttu-id="c4a76-313">Compilare e distribuire</span><span class="sxs-lookup"><span data-stu-id="c4a76-313">Build and Deploy</span></span>

* <span data-ttu-id="c4a76-314">Ricompilazione in Visual Studio e distribuire il dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c4a76-314">Rebuild in Visual Studio and deploy to your device.</span></span>
* <span data-ttu-id="c4a76-315">Chiudere la finestra appropriata con un movimento indice puntato.</span><span class="sxs-lookup"><span data-stu-id="c4a76-315">Dismiss the fit box with an air-tap gesture.</span></span>
* <span data-ttu-id="c4a76-316">Fissare espressioni di controllo del astronautici e scelgo *"Communicator Open"*.</span><span class="sxs-lookup"><span data-stu-id="c4a76-316">Gaze at the astronaut's watch and say *"Open Communicator"*.</span></span>
* <span data-ttu-id="c4a76-317">Selezionare il **Record** pulsante (microfono) per registrare il messaggio.</span><span class="sxs-lookup"><span data-stu-id="c4a76-317">Select the **Record** button (microphone) to record your message.</span></span>
* <span data-ttu-id="c4a76-318">Iniziare a parlare.</span><span class="sxs-lookup"><span data-stu-id="c4a76-318">Start speaking.</span></span> <span data-ttu-id="c4a76-319">Il **riconoscimento dettatura** verrà interpretare i comandi vocali e Mostra il testo ipotizzato di Communicator.</span><span class="sxs-lookup"><span data-stu-id="c4a76-319">The **Dictation Recognizer** will interpret your speech and show the hypothesized text in the communicator.</span></span>
* <span data-ttu-id="c4a76-320">Provare a ottimizzazioni *"Invia messaggio"* durante la registrazione di un messaggio.</span><span class="sxs-lookup"><span data-stu-id="c4a76-320">Try saying *"Send Message"* while you are recording a message.</span></span> <span data-ttu-id="c4a76-321">Si noti che il **parola chiave per il riconoscimento** non risponde perché la **riconoscimento dettatura** è ancora attiva.</span><span class="sxs-lookup"><span data-stu-id="c4a76-321">Notice that the **Keyword Recognizer** does not respond because the **Dictation Recognizer** is still active.</span></span>
* <span data-ttu-id="c4a76-322">Interrompi lettura per alcuni secondi.</span><span class="sxs-lookup"><span data-stu-id="c4a76-322">Stop speaking for a few seconds.</span></span> <span data-ttu-id="c4a76-323">Guarda come il riconoscimento dettatura completa relative ipotesi e viene illustrato il risultato finale.</span><span class="sxs-lookup"><span data-stu-id="c4a76-323">Watch as the Dictation Recognizer completes its hypothesis and shows the final result.</span></span>
* <span data-ttu-id="c4a76-324">Iniziare a parlare e quindi viene sospeso per 20 secondi.</span><span class="sxs-lookup"><span data-stu-id="c4a76-324">Begin speaking and then pause for 20 seconds.</span></span> <span data-ttu-id="c4a76-325">Ciò causerà il **riconoscimento dettatura** per timeout.</span><span class="sxs-lookup"><span data-stu-id="c4a76-325">This will cause the **Dictation Recognizer** to timeout.</span></span>
* <span data-ttu-id="c4a76-326">Si noti che il **parola chiave per il riconoscimento** viene abilitata di nuovo dopo il timeout precedente.</span><span class="sxs-lookup"><span data-stu-id="c4a76-326">Notice that the **Keyword Recognizer** is re-enabled after the above timeout.</span></span> <span data-ttu-id="c4a76-327">Di communicator risponderà a questo punto i comandi vocali.</span><span class="sxs-lookup"><span data-stu-id="c4a76-327">The communicator will now respond to voice commands.</span></span>
* <span data-ttu-id="c4a76-328">Pronunciare *"Invia messaggio"* per inviare il messaggio per l'astronautici.</span><span class="sxs-lookup"><span data-stu-id="c4a76-328">Say *"Send Message"* to send the message to the astronaut.</span></span>

## <a name="chapter-4---grammar-recognizer"></a><span data-ttu-id="c4a76-329">Capitolo 4 - riconoscimento di grammatica</span><span class="sxs-lookup"><span data-stu-id="c4a76-329">Chapter 4 - Grammar Recognizer</span></span>

>[!VIDEO https://www.youtube.com/embed/J2dYJNSvv18]

### <a name="objectives"></a><span data-ttu-id="c4a76-330">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="c4a76-330">Objectives</span></span>

* <span data-ttu-id="c4a76-331">Usare il riconoscimento di grammatica di riconoscimento vocale dell'utente in base a un file SRGS o specifica della grammatica di riconoscimento vocale.</span><span class="sxs-lookup"><span data-stu-id="c4a76-331">Use the Grammar Recognizer to recognize the user's speech according to an SRGS, or Speech Recognition Grammar Specification, file.</span></span>

>[!NOTE]
><span data-ttu-id="c4a76-332">Il **microfono** funzionalità devono essere dichiarate per un'app per la registrazione dal microfono.</span><span class="sxs-lookup"><span data-stu-id="c4a76-332">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="c4a76-333">Questa operazione viene eseguita per è già in MR Input 212, ma tenere a mente per i propri progetti.</span><span class="sxs-lookup"><span data-stu-id="c4a76-333">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="c4a76-334">Nell'Editor di Unity, passare alle impostazioni del giocatore, passare a "Modifica > progetto Impostazioni > Player"</span><span class="sxs-lookup"><span data-stu-id="c4a76-334">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="c4a76-335">Fare clic sulla scheda "Universal Windows Platform"</span><span class="sxs-lookup"><span data-stu-id="c4a76-335">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="c4a76-336">Nella sezione "Impostazioni > le funzionalità di pubblicazione", controllare la **microfono** funzionalità</span><span class="sxs-lookup"><span data-stu-id="c4a76-336">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="c4a76-337">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="c4a76-337">Instructions</span></span>

1. <span data-ttu-id="c4a76-338">Nel **gerarchia** del pannello, cercare **Jetpack_Center** e selezionarlo.</span><span class="sxs-lookup"><span data-stu-id="c4a76-338">In the **Hierarchy** panel, search for **Jetpack_Center** and select it.</span></span>
2. <span data-ttu-id="c4a76-339">Cercare il **azione abbinato** creare uno script nel **Inspector** pannello.</span><span class="sxs-lookup"><span data-stu-id="c4a76-339">Look for the **Tagalong Action** script in the **Inspector** panel.</span></span>
3. <span data-ttu-id="c4a76-340">Fare clic sul cerchio piccolo a destra del **oggetto di Tag lungo** campo.</span><span class="sxs-lookup"><span data-stu-id="c4a76-340">Click the little circle to the right of the **Object To Tag Along** field.</span></span>
4. <span data-ttu-id="c4a76-341">Nella finestra visualizzata, cercare **SRGSToolbox** e selezionarlo dall'elenco.</span><span class="sxs-lookup"><span data-stu-id="c4a76-341">In the window that pops up, search for **SRGSToolbox** and select it from the list.</span></span>
5. <span data-ttu-id="c4a76-342">Esaminiamo il **SRGSColor.xml** del file nei **StreamingAssets** cartella.</span><span class="sxs-lookup"><span data-stu-id="c4a76-342">Take a look at the **SRGSColor.xml** file in the **StreamingAssets** folder.</span></span>
* <span data-ttu-id="c4a76-343">La specifica di progettazione SRGS è reperibile sul sito Web W3C [qui](https://www.w3.org/TR/speech-grammar/).</span><span class="sxs-lookup"><span data-stu-id="c4a76-343">The SRGS design spec can be found on the W3C website [here](https://www.w3.org/TR/speech-grammar/).</span></span>
* <span data-ttu-id="c4a76-344">Nel file SRGS, sono disponibili tre tipi di regole:</span><span class="sxs-lookup"><span data-stu-id="c4a76-344">In our SRGS file, we have three types of rules:</span></span>
  * <span data-ttu-id="c4a76-345">Una regola che consente ad esempio un colore da un elenco di dodici colori.</span><span class="sxs-lookup"><span data-stu-id="c4a76-345">A rule which lets you say one color from a list of twelve colors.</span></span>
  * <span data-ttu-id="c4a76-346">Tre regole in ascolto di una combinazione di regola del colore e uno dei tre forme.</span><span class="sxs-lookup"><span data-stu-id="c4a76-346">Three rules which listen for a combination of the color rule and one of the three shapes.</span></span>
  * <span data-ttu-id="c4a76-347">La regola radice, colorChooser, che è in ascolto per qualsiasi combinazione delle tre regole "colore + forma".</span><span class="sxs-lookup"><span data-stu-id="c4a76-347">The root rule, colorChooser, which listens for any combination of the three "color + shape" rules.</span></span> <span data-ttu-id="c4a76-348">Le forme possono avvenire in qualsiasi ordine e in qualsiasi quantità da un unico per tutte e tre.</span><span class="sxs-lookup"><span data-stu-id="c4a76-348">The shapes can be said in any order and in any amount from just one to all three.</span></span> <span data-ttu-id="c4a76-349">Questo è l'unica regola che è in ascolto, come specificato come regola radice nella parte superiore del file in iniziale &lt;grammatica&gt; tag.</span><span class="sxs-lookup"><span data-stu-id="c4a76-349">This is the only rule that is listened for, as it's specified as the root rule at the top of the file in the initial &lt;grammar&gt; tag.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="c4a76-350">Compilare e distribuire</span><span class="sxs-lookup"><span data-stu-id="c4a76-350">Build and Deploy</span></span>

* <span data-ttu-id="c4a76-351">Ricompilare l'applicazione in Unity, quindi compilare e distribuire da Visual Studio per provare l'app in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c4a76-351">Rebuild the application in Unity, then build and deploy from Visual Studio to experience the app on HoloLens.</span></span>
* <span data-ttu-id="c4a76-352">Chiudere la finestra appropriata con un movimento indice puntato.</span><span class="sxs-lookup"><span data-stu-id="c4a76-352">Dismiss the fit box with an air-tap gesture.</span></span>
* <span data-ttu-id="c4a76-353">Fissare jetpack del astronautici ed esegue un movimento indice puntato.</span><span class="sxs-lookup"><span data-stu-id="c4a76-353">Gaze at the astronaut's jetpack and perform an air-tap gesture.</span></span>
* <span data-ttu-id="c4a76-354">Iniziare a parlare.</span><span class="sxs-lookup"><span data-stu-id="c4a76-354">Start speaking.</span></span> <span data-ttu-id="c4a76-355">Il **grammatica di riconoscimento** verrà interpretare i comandi vocali e modificare i colori delle forme di base del riconoscimento.</span><span class="sxs-lookup"><span data-stu-id="c4a76-355">The **Grammar Recognizer** will interpret your speech and change the colors of the shapes based on the recognition.</span></span> <span data-ttu-id="c4a76-356">Un comando di esempio è "quadrato cerchio blu, gialli".</span><span class="sxs-lookup"><span data-stu-id="c4a76-356">An example command is "blue circle, yellow square".</span></span>
* <span data-ttu-id="c4a76-357">Eseguire un altro indice puntato movimento per ignorare la casella degli strumenti.</span><span class="sxs-lookup"><span data-stu-id="c4a76-357">Perform another air-tap gesture to dismiss the toolbox.</span></span>

## <a name="the-end"></a><span data-ttu-id="c4a76-358">La fine</span><span class="sxs-lookup"><span data-stu-id="c4a76-358">The End</span></span>

<span data-ttu-id="c4a76-359">La procedura è stata completata.</span><span class="sxs-lookup"><span data-stu-id="c4a76-359">Congratulations!</span></span> <span data-ttu-id="c4a76-360">Sono stati completati **SIG Input 212: Voce**.</span><span class="sxs-lookup"><span data-stu-id="c4a76-360">You have now completed **MR Input 212: Voice**.</span></span>

* <span data-ttu-id="c4a76-361">Sai cosa fare e dei comandi vocali.</span><span class="sxs-lookup"><span data-stu-id="c4a76-361">You know the Dos and Don'ts of voice commands.</span></span>
* <span data-ttu-id="c4a76-362">Si è visto come le descrizioni comandi sono stati utilizzati per rendere gli utenti consapevoli di comandi vocali.</span><span class="sxs-lookup"><span data-stu-id="c4a76-362">You saw how tooltips were employed to make users aware of voice commands.</span></span>
* <span data-ttu-id="c4a76-363">Si è visto diversi tipi di commenti e suggerimenti usati per confermare che la voce dell'utente è stata sentito parlare.</span><span class="sxs-lookup"><span data-stu-id="c4a76-363">You saw several types of feedback used to acknowledge that the user's voice was heard.</span></span>
* <span data-ttu-id="c4a76-364">Si è certi di come passare tra il riconoscimento (parola chiave) e il riconoscimento dettatura e come queste due funzionalità comprendere e interpretare la voce dell'utente.</span><span class="sxs-lookup"><span data-stu-id="c4a76-364">You know how to switch between the Keyword Recognizer and the Dictation Recognizer, and how these two features understand and interpret your voice.</span></span>
* <span data-ttu-id="c4a76-365">Si è appreso come usare un file SRGS e il riconoscimento di grammatica di riconoscimento vocale nell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="c4a76-365">You learned how to use an SRGS file and the Grammar Recognizer for speech recognition in your application.</span></span>

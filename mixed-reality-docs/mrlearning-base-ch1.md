---
title: Esercitazioni introduttive - 2 Inizializzazione del progetto e prima applicazione
description: Completa questo corso per informazioni su come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 11/01/2019
ms.topic: article
ms.localizationpriority: high
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: d0c166f760884efab9719ecba1ff83285872e2ef
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334415"
---
# <a name="2-initializing-your-project-and-first-application"></a><span data-ttu-id="92f0b-105">2. Inizializzazione del progetto e prima applicazione</span><span class="sxs-lookup"><span data-stu-id="92f0b-105">2. Initializing your project and first application</span></span>

## <a name="overview"></a><span data-ttu-id="92f0b-106">Panoramica</span><span class="sxs-lookup"><span data-stu-id="92f0b-106">Overview</span></span>

<span data-ttu-id="92f0b-107">In questa prima lezione apprenderai alcune delle funzionalità offerte da <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a>, inizierai a creare la tua prima applicazione per HoloLens 2 e la distribuirai nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="92f0b-107">In this first lesson, you'll learn about some of the capabilities the <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> has to offer, start your first application for the HoloLens 2, and deploy it to the device.</span></span>

## <a name="objectives"></a><span data-ttu-id="92f0b-108">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="92f0b-108">Objectives</span></span>

* <span data-ttu-id="92f0b-109">Configurare Unity per lo sviluppo di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="92f0b-109">Configure Unity for HoloLens development.</span></span>
* <span data-ttu-id="92f0b-110">Importare gli asset e configurare la scena.</span><span class="sxs-lookup"><span data-stu-id="92f0b-110">Import assets and set up the scene.</span></span>
* <span data-ttu-id="92f0b-111">Visualizzare la mesh di mapping spaziale, le mesh manuali e il contatore della frequenza dei fotogrammi.</span><span class="sxs-lookup"><span data-stu-id="92f0b-111">Visualization of the spatial mapping mesh, hand meshes, and the framerate counter.</span></span>

## <a name="create-new-unity-project"></a><span data-ttu-id="92f0b-112">Creare un nuovo progetto Unity</span><span class="sxs-lookup"><span data-stu-id="92f0b-112">Create new Unity project</span></span>

1. <span data-ttu-id="92f0b-113">Avvia Unity.</span><span class="sxs-lookup"><span data-stu-id="92f0b-113">Start Unity.</span></span>

2. <span data-ttu-id="92f0b-114">Seleziona **New** (Nuovo).</span><span class="sxs-lookup"><span data-stu-id="92f0b-114">Select **New**.</span></span>

    ![Lezione 1 - Sezione 1 - Passaggio 2](images/mrlearning-base-ch1-1-step2.JPG)

3. <span data-ttu-id="92f0b-116">Immetti un nome di progetto, ad esempio "MixedRealityBase".</span><span class="sxs-lookup"><span data-stu-id="92f0b-116">Enter a project name (e.g. "MixedRealityBase").</span></span>

    ![Lezione 1 - Sezione 1 - Passaggio 3](images/mrlearning-base-ch1-1-step3.JPG)

4. <span data-ttu-id="92f0b-118">Immetti il percorso in cui salvare il progetto.</span><span class="sxs-lookup"><span data-stu-id="92f0b-118">Enter a location to save your project.</span></span>

    ![Lezione 1 - Sezione 1 - Passaggio 4](images/mrlearning-base-ch1-1-step4.JPG)

5. <span data-ttu-id="92f0b-120">Assicurati che il progetto sia impostato su **3D**.</span><span class="sxs-lookup"><span data-stu-id="92f0b-120">Make sure the project is set to **3D**.</span></span>

    ![Lezione 1 - Sezione 1 - Passaggio 5](images/mrlearning-base-ch1-1-step5.JPG)

6. <span data-ttu-id="92f0b-122">Fai clic su **Create Project** (Crea progetto).</span><span class="sxs-lookup"><span data-stu-id="92f0b-122">Click **Create Project**.</span></span>

    ![Lezione 1 - Sezione 1 - Passaggio 6](images/mrlearning-base-ch1-1-step6.JPG)

## <a name="configure-the-unity-project-for-windows-mixed-reality"></a><span data-ttu-id="92f0b-124">Configurare il progetto Unity per Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="92f0b-124">Configure the Unity project for Windows Mixed Reality</span></span>

1. <span data-ttu-id="92f0b-125">Apri la finestra *Build Settings* (Impostazioni di compilazione) selezionando **File** > **Build Settings** (File>Impostazioni di compilazione).</span><span class="sxs-lookup"><span data-stu-id="92f0b-125">Open the *Build Settings* window by going to **File** > **Build Settings**.</span></span>

    ![Lezione 1 - Sezione 2 - Passaggio 1](images/mrlearning-base-ch1-2-step1.JPG)

2. <span data-ttu-id="92f0b-127">Seleziona *Universal Windows Platform* e fai clic sul pulsante **Switch Platform** (Cambia piattaforma) per cambiare piattaforma.</span><span class="sxs-lookup"><span data-stu-id="92f0b-127">Select the *Universal Windows Platform* and click the **Switch Platform** button to switch platforms.</span></span> <span data-ttu-id="92f0b-128">Le applicazioni in esecuzione su HoloLens 2 devono essere compatibili con la piattaforma UWP (Universal Windows Platform).</span><span class="sxs-lookup"><span data-stu-id="92f0b-128">Applications running on HoloLens 2 are required to be Universal Windows Platform (UWP) compatible.</span></span>

    ![Lezione 1 - Sezione 2 - Passaggio 2](images/mrlearning-base-ch1-2-step2.JPG)

3. <span data-ttu-id="92f0b-130">Abilita la realtà virtuale facendo clic sul pulsante **Player Settings** (Impostazioni lettore) nella finestra Build Settings (Impostazioni di compilazione) e quindi abilita la casella di controllo *Virtual Reality Supported* (Realtà virtuale supportata) in XR Settings (Impostazioni XR) dal pannello di controllo, come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="92f0b-130">Enable virtual reality by clicking the **Player Settings** button in the Build Window, and enable the *Virtual Reality Supported* checkbox under XR Settings from the inspector panel, as shown in the image below.</span></span> <span data-ttu-id="92f0b-131">Tieni presente che per visualizzare il pannello di controllo può essere utile spostare la finestra *Build Settings* (Impostazioni di compilazione).</span><span class="sxs-lookup"><span data-stu-id="92f0b-131">Note that you might need to drag the *Build Settings* window out of the way in order to see the inspector panel.</span></span> <span data-ttu-id="92f0b-132">La casella di controllo *Virtual Reality Supported* (Realtà virtuale supportata) si applica anche ai visori VR di realtà mista e realtà aumentata perché fa riferimento all'abilitazione della visione stereoscopica (con il rendering di immagini diverse per ogni occhio).</span><span class="sxs-lookup"><span data-stu-id="92f0b-132">The *Virtual Reality Supported* checkbox also applies to Mixed Reality and Augmented Reality headsets because it refers to the enabling of stereoscopic vision (rendering different images for each eye.)</span></span>

    ![Lezione 1 - Sezione 2 - Passaggio 3](images/mrlearning-base-ch1-2-step3.JPG)

4. <span data-ttu-id="92f0b-134">Sempre in XR Settings (Impostazioni XR), modifica l'impostazione di *Stereo Rendering Mode* (Modalità di rendering stereo) selezionando *Single Pass Instanced* (Con istanze a passaggio singolo).</span><span class="sxs-lookup"><span data-stu-id="92f0b-134">Also under XR Settings, change the *Stereo Rendering Mode* to *Single Pass Instanced*.</span></span> <span data-ttu-id="92f0b-135">Questo [stile della pipeline di rendering](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) è in genere il più efficiente per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="92f0b-135">This [rendering pipeline style](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) is generally most performant for HoloLens 2.</span></span> <span data-ttu-id="92f0b-136">Se ti interessano altre configurazioni con ottime prestazioni per l'ambiente Unity, segui [queste istruzioni](recommended-settings-for-unity.md).</span><span class="sxs-lookup"><span data-stu-id="92f0b-136">If interested in other performant configurations for your Unity environment, follow [these instructions](recommended-settings-for-unity.md).</span></span>

    ![Lezione 1 - Sezione 2 - Passaggio 4](images/mrlearning-base-ch1-2-step4.jpg)

5. <span data-ttu-id="92f0b-138">Dallo stesso pannello di controllo verifica che la casella di controllo *Spatial Perception* (Percezione spaziale) nella sezione Capabilities (Funzionalità) in *Publishing Settings* (Impostazioni di pubblicazione) sia abilitata.</span><span class="sxs-lookup"><span data-stu-id="92f0b-138">From the same inspector panel, ensure that the *Spatial Perception* checkbox in the capabilities section is enabled under *Publishing Settings*.</span></span> <span data-ttu-id="92f0b-139">Spatial Perception (Percezione spaziale) ci consentirà di visualizzare la mesh di mapping spaziale in un dispositivo di realtà mista come HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="92f0b-139">Spatial Perception allows us to visualize the spatial mapping mesh on a mixed reality device, such as HoloLens 2.</span></span> <span data-ttu-id="92f0b-140">Le impostazioni di pubblicazione sono disponibili nel pannello di controllo, sopra XR Settings (Impostazioni XR) e sotto Other Settings (Altre impostazioni).</span><span class="sxs-lookup"><span data-stu-id="92f0b-140">Publishing Settings are found in the inspector panel, above XR Settings and under Other Settings.</span></span>

    ![Lezione 1 - Sezione 2 - Passaggio 5](images/mrlearning-base-ch1-2-step5.JPG)

    >[!NOTE]
    ><span data-ttu-id="92f0b-142">Anche se non vengono usate in questa sezione, tra le altre funzionalità comuni che puoi attivare sono presenti *Microphone* (Microfono) per i comandi vocali e *InternetClient* per la connessione a servizi che richiedono una connessione di rete.</span><span class="sxs-lookup"><span data-stu-id="92f0b-142">While not used in this section, some other common capabilities you might want to enable include the *Microphone* for voice commands, and *InternetClient* for connecting to services requiring a network connection.</span></span>

## <a name="import-the-mixed-reality-toolkit"></a><span data-ttu-id="92f0b-143">Importare Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="92f0b-143">Import the Mixed Reality Toolkit</span></span>

1. <span data-ttu-id="92f0b-144">Scarica il [pacchetto della versione 2.1.0](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage) di [Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) Unity Foundation e salvalo in una cartella nel PC.</span><span class="sxs-lookup"><span data-stu-id="92f0b-144">Download the [Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) Unity [foundation package version 2.1.0](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage) and save it to a folder on your PC.</span></span>

2. <span data-ttu-id="92f0b-145">Importa il pacchetto di *Mixed Reality Toolkit* scaricato nel passaggio precedente.</span><span class="sxs-lookup"><span data-stu-id="92f0b-145">Import the *Mixed Reality Toolkit* package that you downloaded in the previous step.</span></span> <span data-ttu-id="92f0b-146">Per iniziare, fai clic su **Assets** > **Import** > **Custom Package** (Asset>Importa pacchetto>Pacchetto personalizzato), seleziona *Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage* e apri il pacchetto per avviare il processo di importazione.</span><span class="sxs-lookup"><span data-stu-id="92f0b-146">Start by clicking on **Assets** > **Import** > **Custom Package**, select *Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage* and open it to begin the importing process.</span></span> <span data-ttu-id="92f0b-147">Attendi alcuni minuti che il processo di importazione sia completato.</span><span class="sxs-lookup"><span data-stu-id="92f0b-147">Allow a few minutes for the importing process to complete.</span></span>

    ![Lezione 1 - Sezione 3 - Passaggio 2a](images/mrlearning-base-ch1-3-step2a.JPG)

    ![Lezione 1 - Sezione 3 - Passaggio 2b](images/mrlearning-base-ch1-3-step2b.JPG)

3. <span data-ttu-id="92f0b-150">Nella finestra popup successiva fai clic su **Import** (Importa) per avviare l'importazione del pacchetto selezionato nel progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="92f0b-150">In the next pop-up window, click **Import** to begin importing the selected package into the Unity project.</span></span> <span data-ttu-id="92f0b-151">Assicurati che tutti gli elementi siano selezionati, come illustrato nell'immagine.</span><span class="sxs-lookup"><span data-stu-id="92f0b-151">Ensure all items are checked as shown in the image.</span></span>

    ![Lezione 1 - Sezione 3 - Passaggio 3](images/mrlearning-base-ch1-3-step3.JPG)

    > [!NOTE]
    > <span data-ttu-id="92f0b-153">Se vedi una finestra di dialogo popup con la richiesta di applicare le impostazioni predefinite di Mixed Reality Toolkit, fai clic su **Apply** (Applica).</span><span class="sxs-lookup"><span data-stu-id="92f0b-153">If you see a pop-up dialog box asking to apply the Mixed Reality Toolkit default settings, click **Apply**.</span></span> <span data-ttu-id="92f0b-154">MRTK analizza il progetto per individuare le eventuali impostazioni consigliate mancanti durante l'importazione per l'installazione automatica.</span><span class="sxs-lookup"><span data-stu-id="92f0b-154">MRTK analyzes your project for any missing recommended settings when imported for automated setup.</span></span> <span data-ttu-id="92f0b-155">A seconda delle impostazioni, la finestra popup potrebbe essere diversa dall'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="92f0b-155">Depending on your settings, the pop-up might look different than the image below.</span></span>

    ![Lezione 1 - Sezione 3 - Passaggio 4 - Nota 1](images/mrlearning-base-ch1-3-step4-note1.JPG)

## <a name="configure-the-mixed-reality-toolkit"></a><span data-ttu-id="92f0b-157">Configurare Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="92f0b-157">Configure the Mixed Reality Toolkit</span></span>

1. <span data-ttu-id="92f0b-158">Aggiungi *Mixed Reality Toolkit* alla scena corrente selezionando **Mixed Reality Toolkit** > **Add to Scene and Configure** (Aggiungi alla scena e configura)</span><span class="sxs-lookup"><span data-stu-id="92f0b-158">Add the *Mixed Reality Toolkit* to your current scene by selecting **Mixed Reality Toolkit** > **Add to Scene and Configure..**</span></span> <span data-ttu-id="92f0b-159">dalla barra dei menu.</span><span class="sxs-lookup"><span data-stu-id="92f0b-159">from the menu bar.</span></span> <span data-ttu-id="92f0b-160">Se dopo l'importazione di Mixed Reality Toolkit questa voce di menu non è visibile, riavvia Unity.</span><span class="sxs-lookup"><span data-stu-id="92f0b-160">If you don't see this menu item after importing the mixed reality toolkit, restart Unity.</span></span>

    ![Lezione 1 - Sezione 4 - Passaggio 1](images/mrlearning-base-ch1-4-step1.JPG)

    > [!NOTE]
    > <span data-ttu-id="92f0b-162">È possibile che venga visualizzata una finestra di dialogo popup per la selezione di un [profilo per Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html).</span><span class="sxs-lookup"><span data-stu-id="92f0b-162">You may see a pop-up dialog box for selecting a [profile for the Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html).</span></span> <span data-ttu-id="92f0b-163">Scegli il profilo denominato *DefaultHoloLens2ConfigurationProfile* facendo doppio clic su di esso.</span><span class="sxs-lookup"><span data-stu-id="92f0b-163">Choose the profile named *DefaultHoloLens2ConfigurationProfile* by double-clicking it.</span></span>

2. <span data-ttu-id="92f0b-164">Nella scena saranno presenti alcuni nuovi elementi e modifiche.</span><span class="sxs-lookup"><span data-stu-id="92f0b-164">Your scene will have several new items and modifications.</span></span> <span data-ttu-id="92f0b-165">Salva la scena con un nome diverso facendo clic su **File** > **Save As** (File>Salva con nome) e specificando un nome, ad esempio *BaseScene*.</span><span class="sxs-lookup"><span data-stu-id="92f0b-165">Save your scene under a different name by clicking **File** > **Save As...**, and give your scene a name, such as *BaseScene*.</span></span> <span data-ttu-id="92f0b-166">Mantieni la scena organizzata salvandola nella cartella *Scenes* all'interno della cartella *Assets* del progetto.</span><span class="sxs-lookup"><span data-stu-id="92f0b-166">Keep your scene organized by saving it to the *Scenes* folder in your project’s *Assets* folder.</span></span>

    ![Lezione 1 - Sezione 4 - Passaggio 2a](images/mrlearning-base-ch1-4-step2a.JPG)

    ![Lezione 1 - Sezione 4 - Passaggio 2b](images/mrlearning-base-ch1-4-step2b.JPG)

## <a name="build-your-application-to-your-device"></a><span data-ttu-id="92f0b-169">Compilare l'applicazione nel dispositivo</span><span class="sxs-lookup"><span data-stu-id="92f0b-169">Build your application to your device</span></span>

1. <span data-ttu-id="92f0b-170">Se nelle sezioni precedenti hai chiuso la finestra *Build Settings* (Impostazioni di compilazione), apri nuovamente la finestra selezionando **File** > **Build Settings** (File>Impostazioni di compilazione).</span><span class="sxs-lookup"><span data-stu-id="92f0b-170">If you closed the *Build Settings* window from the previous sections, open the *Build Settings* window again by going to **File** > **Build Settings**.</span></span>

    ![Lezione 1 - Sezione 5 - Passaggio 1](images/mrlearning-base-ch1-5-step1.JPG)

2. <span data-ttu-id="92f0b-172">Assicurati che la scena che hai appena creato sia inclusa nell'elenco *Scenes in Build* (Scene nella compilazione) facendo clic sul pulsante **Add Open Scenes** (Aggiungi scene aperte) mentre la scena è aperta in Unity.</span><span class="sxs-lookup"><span data-stu-id="92f0b-172">Ensure the scene you just created is in the *Scenes in Build* list by clicking on the **Add Open Scenes** button while your scene is open in Unity.</span></span>

3. <span data-ttu-id="92f0b-173">Scegli il pulsante **Build** (Compila) per avviare il processo di compilazione.</span><span class="sxs-lookup"><span data-stu-id="92f0b-173">Press the **Build** button to begin the build process.</span></span>

    ![Lezione 1 - Sezione 5 - Passaggio 3](images/mrlearning-base-ch1-5-step3.JPG)

4. <span data-ttu-id="92f0b-175">Crea una nuova cartella per l'applicazione e assegna un nome alla cartella creata.</span><span class="sxs-lookup"><span data-stu-id="92f0b-175">Create and name a new folder for your application.</span></span> <span data-ttu-id="92f0b-176">Nell'immagine seguente è stata creata una cartella con il nome App per contenere l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="92f0b-176">In the image below, a folder with the name App was created to contain the application.</span></span> <span data-ttu-id="92f0b-177">Fai clic su **Select Folder** (Seleziona cartella) per iniziare la compilazione nella cartella appena creata.</span><span class="sxs-lookup"><span data-stu-id="92f0b-177">Click **Select Folder** to begin building to the newly created folder.</span></span> <span data-ttu-id="92f0b-178">Al termine della compilazione, puoi chiudere la finestra *Build Settings* (Impostazioni di compilazione) in Unity.</span><span class="sxs-lookup"><span data-stu-id="92f0b-178">After the build has completed, you can close the *Build Settings* window in Unity.</span></span>

    ![Lezione 1 - Sezione 5 - Passaggio 4](images/mrlearning-base-ch1-5-step4.JPG)

    >[!IMPORTANT]
    ><span data-ttu-id="92f0b-180">se la compilazione ha esito negativo, prova a ripeterla o a riavviare Unity e a ripetere la compilazione.</span><span class="sxs-lookup"><span data-stu-id="92f0b-180">If the build fails, try building again or restarting Unity and building again.</span></span> <span data-ttu-id="92f0b-181">Se viene restituito un errore simile al seguente: "Errore CS0246 = Non è possibile trovare il tipo o il nome dello spazio dei nomi "XX" (direttiva using o riferimento ad assembly mancante?)"</span><span class="sxs-lookup"><span data-stu-id="92f0b-181">If you see an error, such as "Error: CS0246 = The type or namespace name “XX” could not be found (are you missing a using directive or an assembly reference?).</span></span> <span data-ttu-id="92f0b-182">può essere necessario installare [Windows 10 SDK (10.0.18362.0)](https://developer.microsoft.com//windows/downloads/windows-10-sdk).</span><span class="sxs-lookup"><span data-stu-id="92f0b-182">If so, you might need to install [Windows 10 SDK (10.0.18362.0)](https://developer.microsoft.com//windows/downloads/windows-10-sdk)</span></span>

5. <span data-ttu-id="92f0b-183">Al termine della compilazione, apri la nuova cartella creata che contiene i file dell'applicazione appena compilata.</span><span class="sxs-lookup"><span data-stu-id="92f0b-183">After the build is completed, open the newly created folder containing your newly built application files.</span></span> <span data-ttu-id="92f0b-184">Fai doppio clic sulla soluzione *MixedRealityBase.sln*, o sul nome corrispondente se hai usato un nome alternativo per il progetto, per aprire il file della soluzione in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="92f0b-184">Double-click on the *MixedRealityBase.sln* solution, or the corresponding name, if you used an alternative name for your project, to open the solution file in Visual Studio.</span></span>

    >[!NOTE]
    ><span data-ttu-id="92f0b-185">Assicurati di aprire la nuova cartella creata (ad esempio la cartella *App*, se hai seguito le convenzioni di denominazione dei passaggi precedenti) perché fuori da tale cartella sarà presente un file con estensione sln e nome analogo, da non confondere con quello che si trova all'interno della cartella di compilazione.</span><span class="sxs-lookup"><span data-stu-id="92f0b-185">Be sure to open the newly created folder (i.e. the *App* folder, if following the naming conventions from the previous steps), as there will be a similarly named .sln file outside of that folder, that is not to be confused with the .sln file inside the build folder.</span></span> <span data-ttu-id="92f0b-186">La struttura di cartelle dovrebbe avere un aspetto simile al seguente.</span><span class="sxs-lookup"><span data-stu-id="92f0b-186">The folder structure should look similar to the image below.</span></span>
    >
    ><span data-ttu-id="92f0b-187">Se Visual Studio chiede di installare nuovi componenti, dedica qualche minuto a verificare che tutti i componenti indispensabili siano installati come specificato nella pagina [Installare gli strumenti](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="92f0b-187">If Visual Studio asks you to install new components, take a moment to ensure that all prerequisite components are installed as specified in [the "Install the Tools" page](install-the-tools.md)</span></span>

    ![Lezione 1 - Sezione 5 - Passaggio 5](images/mrlearning-base-ch1-5-step5.JPG)

6. <span data-ttu-id="92f0b-189">Connetti il dispositivo HoloLens 2 al PC.</span><span class="sxs-lookup"><span data-stu-id="92f0b-189">Connect your HoloLens 2 into your PC.</span></span> <span data-ttu-id="92f0b-190">Anche se queste istruzioni presuppongono che tu distribuisca l'applicazione in un dispositivo HoloLens 2, puoi anche scegliere di distribuirla nell'[emulatore HoloLens 2](using-the-hololens-emulator.md) oppure creare un [pacchetto dell'applicazione per il sideload](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>).</span><span class="sxs-lookup"><span data-stu-id="92f0b-190">While these instructions assume you will be deploying to a HoloLens 2 device, you might also choose to deploy to the [HoloLens 2 emulator](using-the-hololens-emulator.md) or choose to create an [app package for sideloading](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)</span></span>

    >[!IMPORTANT]
    ><span data-ttu-id="92f0b-191">Prima della compilazione, il dispositivo deve essere in *Modalità sviluppatore* e associato al computer di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="92f0b-191">Before building to your device, the device must be in *Developer Mode* and paired with your development machine.</span></span> <span data-ttu-id="92f0b-192">Per completare i due passaggi segui [queste istruzioni](using-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="92f0b-192">Both of these steps can be completed by following [these instructions](using-visual-studio.md)</span></span>

7. <span data-ttu-id="92f0b-193">Configura Visual Studio per la compilazione nel dispositivo HoloLens 2 selezionando la configurazione *Release* o *Master*, l'architettura *ARM* e *Device* (Dispositivo) come destinazione.</span><span class="sxs-lookup"><span data-stu-id="92f0b-193">Configure Visual Studio for building to your HoloLens 2 by selecting the *Release* or *Master* configuration, the *ARM* architecture, and *Device* as target.</span></span>

    ![Lezione 1 - Sezione 5 - Passaggio 8](images/mrlearning-base-ch1-5-step7.JPG)

8. <span data-ttu-id="92f0b-195">Il passaggio finale consiste nel compilare e distribuire l'applicazione nel dispositivo selezionando **Debug** > **Avvia senza eseguire debug**.</span><span class="sxs-lookup"><span data-stu-id="92f0b-195">The final step is to build and deploy to your device by selecting **Debug** > **Start without debugging**.</span></span> <span data-ttu-id="92f0b-196">Se selezioni *Avvia senza eseguire debug*, l'applicazione viene avviata immediatamente nel dispositivo al termine della compilazione, ma senza il debugger associato e senza che in Visual Studio vengano visualizzate le informazioni di debug.</span><span class="sxs-lookup"><span data-stu-id="92f0b-196">Selecting *Start without Debugging* causes the application to immediately start on your device upon a successful build, but without the debugger attached and information appearing in Visual Studio.</span></span> <span data-ttu-id="92f0b-197">Questo significa anche che, mentre l'applicazione è in esecuzione sul dispositivo HoloLens 2, puoi disconnettere il cavo USB senza arrestare l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="92f0b-197">This also means that you can disconnect your USB cable while your application is running on your HoloLens 2 without stopping the application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="92f0b-198">Puoi anche selezionare **Compila** > **Distribuisci soluzione** per distribuire l'applicazione nel dispositivo senza che venga avviata automaticamente.</span><span class="sxs-lookup"><span data-stu-id="92f0b-198">You might also select **Build** > **Deploy Solution** to deploy to your device without having the application automatically start.</span></span>

    ![Lezione 1 - Sezione 5 - Passaggio 9](images/mrlearning-base-ch1-5-step8.JPG)

## <a name="congratulations"></a><span data-ttu-id="92f0b-200">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="92f0b-200">Congratulations</span></span>

<span data-ttu-id="92f0b-201">A questo punto hai distribuito la tua prima applicazione per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="92f0b-201">You have now deployed your first HoloLens 2 application.</span></span> <span data-ttu-id="92f0b-202">Esplorando, noterai una mesh di mapping spaziale che copre tutte le superfici percepite da HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="92f0b-202">As you walk around, you should see a spatial mapping mesh covering all the surfaces that have been perceived by the HoloLens 2.</span></span> <span data-ttu-id="92f0b-203">Dovresti anche vedere indicatori sulle mani e sulle dita per il tracciamento delle mani e un contatore della frequenza dei fotogrammi per tenere sotto controllo le prestazioni dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="92f0b-203">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on application performance.</span></span> <span data-ttu-id="92f0b-204">Questi sono solo alcuni degli elementi fondamentali, inclusi per impostazione predefinita in Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="92f0b-204">These are just a few of the foundational pieces, included out of the box, with the Mixed Reality Toolkit.</span></span> <span data-ttu-id="92f0b-205">Nelle lezioni successive inizierai ad aggiungere più contenuti e interattività alla scena, in modo da poter esplorare completamente le funzionalità di HoloLens 2 e Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="92f0b-205">In the lessons to come, you will start adding more content and interactivity to your scene so that you can fully explore the capabilities of HoloLens 2 and the Mixed Reality Toolkit.</span></span>

> [!NOTE]
> <span data-ttu-id="92f0b-206">Nell'app potresti notare il profiler visuale.</span><span class="sxs-lookup"><span data-stu-id="92f0b-206">In the app, you may notice the visual profiler.</span></span> <span data-ttu-id="92f0b-207">Nella [lezione 5](mrlearning-base-ch5.md) imparerai come attivare o disattivare il contatore della frequenza dei fotogrammi usando un comando vocale.</span><span class="sxs-lookup"><span data-stu-id="92f0b-207">You will cover how to toggle the frame rate counter using a voice command in [Lesson 5](mrlearning-base-ch5.md).</span></span> <span data-ttu-id="92f0b-208">È in genere consigliabile mantenere sempre visibile il profiler visuale durante lo sviluppo per comprendere quando le modifiche del codice possono avere conseguenze sulle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="92f0b-208">It is generally recommended to keep the visual profiler visible at all times during development to understand when code changes may have impacted perf.</span></span> <span data-ttu-id="92f0b-209">L'applicazione HoloLens 2 deve essere [eseguita costantemente a 60 FPS](understanding-performance-for-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="92f0b-209">HoloLens 2 application should [continuously run at 60 FPS](understanding-performance-for-mixed-reality.md).</span></span>

[<span data-ttu-id="92f0b-210">Lezione successiva: 3. Creazione dell'interfaccia utente e configurazione di Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="92f0b-210">Next Lesson: 3. Creating user interface and configure Mixed Reality Toolkit</span></span>](mrlearning-base-ch2.md)

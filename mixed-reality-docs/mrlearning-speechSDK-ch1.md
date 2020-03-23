---
title: Esercitazioni sui servizi vocali di Azure - 1. Integrazione e uso del riconoscimento vocale e della trascrizione
description: Completa questo corso per imparare a implementare Azure Speech SDK in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: a72eb808adbc14df65c55e694ea985d97f9ec24c
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/10/2020
ms.locfileid: "79032546"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a><span data-ttu-id="7e244-105">1. Integrazione e uso del riconoscimento vocale e della trascrizione</span><span class="sxs-lookup"><span data-stu-id="7e244-105">1. Integrating and using speech recognition and transcription</span></span>

## <a name="overview"></a><span data-ttu-id="7e244-106">Panoramica</span><span class="sxs-lookup"><span data-stu-id="7e244-106">Overview</span></span>


<span data-ttu-id="7e244-107">In questa serie di esercitazioni creerai un'applicazione di Realtà mista per esplorare l'uso dei servizi vocali di Azure con HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="7e244-107">In this tutorial series, you will create a Mixed Reality application that explores the use of Azure Speech Services with the HoloLens 2.</span></span> <span data-ttu-id="7e244-108">Al termine di questa serie di esercitazioni, sarai in grado di usare il microfono del tuo dispositivo per trascrivere il parlato in testo in tempo reale, tradurre il parlato in altre lingue e utilizzare la funzionalità Riconoscimento finalità per comprendere i comandi vocali usando l'intelligenza artificiale.</span><span class="sxs-lookup"><span data-stu-id="7e244-108">When you complete this tutorial series, you will be able to use your device's microphone to transcribe speech to text in real time, translate your speech into other languages, and leverage the Intent recognition feature to understand voice commands using artificial intelligence.</span></span>

## <a name="objectives"></a><span data-ttu-id="7e244-109">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="7e244-109">Objectives</span></span>

* <span data-ttu-id="7e244-110">Imparare a integrare i servizi vocali di Azure con un'applicazione HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="7e244-110">Learn how to integrate Azure Speech Services with a HoloLens 2 application</span></span>
* <span data-ttu-id="7e244-111">Imparare a usare il riconoscimento vocale per trascrivere testo</span><span class="sxs-lookup"><span data-stu-id="7e244-111">Learn how to use speech recognition to transcribe text</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7e244-112">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="7e244-112">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="7e244-113">Se non hai ancora completato la serie di [Esercitazioni introduttive](mrlearning-base.md), è consigliabile completare prima queste esercitazioni.</span><span class="sxs-lookup"><span data-stu-id="7e244-113">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="7e244-114">Un PC Windows 10 configurato in cui siano [installati gli strumenti](install-the-tools.md) corretti</span><span class="sxs-lookup"><span data-stu-id="7e244-114">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="7e244-115">Windows 10 SDK 10.0.18362.0 o versioni successive</span><span class="sxs-lookup"><span data-stu-id="7e244-115">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="7e244-116">Alcune funzionalità di programmazione C# di base</span><span class="sxs-lookup"><span data-stu-id="7e244-116">Some basic C# programming ability</span></span>
* <span data-ttu-id="7e244-117">Un dispositivo HoloLens 2 [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="7e244-117">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="7e244-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.2.X installato e il modulo di supporto delle compilazioni UWP (Universal Windows Platform) aggiunto</span><span class="sxs-lookup"><span data-stu-id="7e244-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7e244-119">La versione di Unity consigliata per questa serie di esercitazioni è Unity 2019.2.X.</span><span class="sxs-lookup"><span data-stu-id="7e244-119">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="7e244-120">Questa istruzione sostituisce gli eventuali requisiti o suggerimenti relativi alla versione di Unity indicati negli argomenti visualizzabili facendo clic sui collegamenti dei prerequisiti sopra riportati.</span><span class="sxs-lookup"><span data-stu-id="7e244-120">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="7e244-121">Creazione e preparazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="7e244-121">Creating and preparing the Unity project</span></span>

<span data-ttu-id="7e244-122">In questa sezione creerai un nuovo progetto Unity per prepararti allo sviluppo con MRTK.</span><span class="sxs-lookup"><span data-stu-id="7e244-122">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="7e244-123">A questo scopo, segui prima l'esercitazione [Inizializzazione del progetto e prima applicazione](mrlearning-base-ch1.md), escluse le istruzioni della sezione [Compilare l'applicazione nel dispositivo](mrlearning-base-ch1.md#build-your-application-to-your-device), che include i passaggi seguenti:</span><span class="sxs-lookup"><span data-stu-id="7e244-123">For this, first follow the [Initializing your project and first application](mrlearning-base-ch1.md), excluding the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="7e244-124">[Creare un nuovo progetto Unity](mrlearning-base-ch1.md#create-new-unity-project) e assegnargli un nome appropriato, ad esempio *MRTK Tutorials*</span><span class="sxs-lookup"><span data-stu-id="7e244-124">[Create new Unity project](mrlearning-base-ch1.md#create-new-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>

2. [<span data-ttu-id="7e244-125">Configurare il progetto Unity per Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="7e244-125">Configure the Unity project for Windows Mixed Reality</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [<span data-ttu-id="7e244-126">Importare le risorse essenziali TextMesh Pro</span><span class="sxs-lookup"><span data-stu-id="7e244-126">Import TextMesh Pro Essential Resources</span></span>](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [<span data-ttu-id="7e244-127">Importare Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="7e244-127">Import the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [<span data-ttu-id="7e244-128">Configurare il progetto Unity per Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="7e244-128">Configure the Unity project for the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. <span data-ttu-id="7e244-129">[Aggiungere Mixed Reality Toolkit alla scena di Unity](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) e assegnare alla scena un nome appropriato, ad esempio *AzureSpeechServices*</span><span class="sxs-lookup"><span data-stu-id="7e244-129">[Add the Mixed Reality Toolkit to the Unity scene](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) and give the scene a suitable name, for example, *AzureSpeechServices*</span></span>

<span data-ttu-id="7e244-130">Segui quindi le istruzioni riportate in [Come configurare i profili di Mixed Reality Toolkit (modifica dell'opzione di visualizzazione della mesh di consapevolezza spaziale)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) per impostare **DefaultHoloLens2ConfigurationProfile** come profilo di configurazione MRTK per la scena e modificare le opzioni di visualizzazione per la mesh di riconoscimento spaziale impostando **Occlusion** (Occlusione).</span><span class="sxs-lookup"><span data-stu-id="7e244-130">Then follow the [How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

> [!CAUTION]
> <span data-ttu-id="7e244-131">Come indicato nelle istruzioni in [Configurare il progetto Unity per Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit), è fortemente sconsigliato abilitare MSBuild per Unity.</span><span class="sxs-lookup"><span data-stu-id="7e244-131">As mentioned in the [Configure the Unity project for the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) instructions linked above, it is strongly recommended to not enable MSBuild for Unity.</span></span>

## <a name="configuring-the-speech-commands-start-behavior"></a><span data-ttu-id="7e244-132">Configurazione del comportamento di avvio dei comandi vocali</span><span class="sxs-lookup"><span data-stu-id="7e244-132">Configuring the speech commands start behavior</span></span>

<span data-ttu-id="7e244-133">Poiché userai Speech SDK per il riconoscimento vocale e la trascrizione, devi configurare i comandi vocali di MRTK in modo che non interferiscano con le funzionalità di Speech SDK.</span><span class="sxs-lookup"><span data-stu-id="7e244-133">Because you will use the Speech SDK for speech recognition and transcription you need to configure the MRTK Speech Commands so they do not interfere with the Speech SDK functionality.</span></span> <span data-ttu-id="7e244-134">A tale scopo, puoi modificare il comportamento di avvio dei comandi vocali da Auto Start (Avvio automatico) a Manual Start (Avvio manuale).</span><span class="sxs-lookup"><span data-stu-id="7e244-134">To achieve this you can change the speech commands start behavior from Auto Start to Manual Start.</span></span>

<span data-ttu-id="7e244-135">Con l'oggetto **MixedRealityToolkit** selezionato nella finestra Hierarchy (Gerarchia), nella finestra Inspector (Controllo) seleziona la scheda **Input**, clona **DefaultHoloLens2InputSystemProfile** e **DefaultMixedRealitySpeechCommandsProfile** e quindi modifica i comandi vocali di **Start Behavior** (Comportamento di avvio) in **Manual Start** (Avvio manuale):</span><span class="sxs-lookup"><span data-stu-id="7e244-135">With the **MixedRealityToolkit** object selected in the Hierarchy window, in the Inspector window, select the **Input** tab, clone the **DefaultHoloLens2InputSystemProfile** and the **DefaultMixedRealitySpeechCommandsProfile**, and then change the speech commands **Start Behavior** to **Manual Start**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="7e244-137">Per rivedere la procedura di clonazione e configurazione di profili MRTK, puoi fare riferimento alle istruzioni contenute in [Come configurare i profili di Mixed Reality Toolkit (modifica dell'opzione di visualizzazione della mesh di consapevolezza spaziale)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option).</span><span class="sxs-lookup"><span data-stu-id="7e244-137">For a reminder on how to clone and configure MRTK profiles, you can refer to the [How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.</span></span>

## <a name="configuring-the-capabilities"></a><span data-ttu-id="7e244-138">Configurazione delle funzionalità</span><span class="sxs-lookup"><span data-stu-id="7e244-138">Configuring the capabilities</span></span>

<span data-ttu-id="7e244-139">Dal menu Unity scegli **Edit** > **Project Settings...** (Modifica > Impostazioni del progetto) per aprire la finestra Project Settings (Impostazioni del progetto) e quindi individua la sezione **Player** >  **Publishing Settings** (Lettore > Impostazioni di pubblicazione):</span><span class="sxs-lookup"><span data-stu-id="7e244-139">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Publishing Settings** section:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section3-step1-1.png)

<span data-ttu-id="7e244-141">In **Publishing Settings** (Impostazioni di pubblicazione) scorri verso il basso fino alla sezione **Capabilities** (Funzionalità) e verifica che siano abilitate le funzionalità **InternetClient**, **Microphone** e **SpatialPerception**, che hai abilitato al momento della creazione del progetto all'inizio dell'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="7e244-141">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="7e244-142">Abilita quindi le funzionalità **InternetClientServer** e **PrivateNetworkClientServer**:</span><span class="sxs-lookup"><span data-stu-id="7e244-142">Then, enable the **InternetClientServer** and **PrivateNetworkClientServer** capabilities:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="7e244-144">Importazione degli asset dell'esercitazione</span><span class="sxs-lookup"><span data-stu-id="7e244-144">Importing the tutorial assets</span></span>

<span data-ttu-id="7e244-145">Scarica e **importa** i pacchetti personalizzati di Unity seguenti, **nell'ordine in cui sono elencati**:</span><span class="sxs-lookup"><span data-stu-id="7e244-145">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="7e244-146">[Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage) (versione più recente)</span><span class="sxs-lookup"><span data-stu-id="7e244-146">[Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage) (latest version)</span></span>
* [<span data-ttu-id="7e244-147">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span><span class="sxs-lookup"><span data-stu-id="7e244-147">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)
* [<span data-ttu-id="7e244-148">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="7e244-148">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-speech-services-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage)

> [!TIP]
> <span data-ttu-id="7e244-149">Per rivedere la procedura di importazione di un pacchetto personalizzato di Unity, puoi fare riferimento alle istruzioni contenute in [Importare Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="7e244-149">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="7e244-150">Dopo l'importazione degli asset dell'esercitazione, la finestra Project (Progetto) avrà un aspetto simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="7e244-150">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section4-step1-1.png)

## <a name="preparing-the-scene"></a><span data-ttu-id="7e244-152">Preparazione della scena</span><span class="sxs-lookup"><span data-stu-id="7e244-152">Preparing the scene</span></span>

<span data-ttu-id="7e244-153">In questa sezione preparerai la scena aggiungendo il prefab dell'esercitazione e configurerai il componente Lunarcom Controller (Script) (Controller Lunarcom - Script) per il controllo della scena.</span><span class="sxs-lookup"><span data-stu-id="7e244-153">In this section, you will prepare the scene by adding the tutorial prefab and configure the Lunarcom Controller (Script) component to control your scene.</span></span>

<span data-ttu-id="7e244-154">Nella finestra Project (Progetto) passa ad **Assets** > **MRTK.Tutorials.AzureSpeechServices** > **Prefabs** (Asset > MRTK.Tutorials.AzureSpeechServices > Prefab) e trascina il prefab **Lunarcom** nella finestra Hierarchy (Gerarchia) per aggiungerlo alla scena:</span><span class="sxs-lookup"><span data-stu-id="7e244-154">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureSpeechServices** > **Prefabs** folder and drag the **Lunarcom** prefab into the Hierarchy window to add it to your scene:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-1.png)

<span data-ttu-id="7e244-156">Con l'oggetto **Lunarcom** ancora selezionato nella finestra Hierarchy (Gerarchia), nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Lunarcom Controller (Script)** (Controller Lunarcom - Script) all'oggetto Lunarcom:</span><span class="sxs-lookup"><span data-stu-id="7e244-156">With the **Lunarcom** object still selected in the Hierarchy window, in the Inspector window, use the **Add Component** button to add the **Lunarcom Controller (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-2.png)

> [!NOTE]
> <span data-ttu-id="7e244-158">Il componente Lunarcom Controller (Script) (Controller Lunarcom - Script) non fa parte di MRTK.</span><span class="sxs-lookup"><span data-stu-id="7e244-158">The Lunarcom Controller (Script) component is not part of MRTK.</span></span> <span data-ttu-id="7e244-159">È stato fornito con gli asset dell'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="7e244-159">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="7e244-160">Con l'oggetto **Lunarcom** ancora selezionato, espandi l'oggetto in modo da visualizzarne gli oggetti figlio e quindi trascina l'oggetto **Terminal** nel campo **Terminal** (Terminale) del componente Lunarcom Controller (Script) (Controller Lunarcom - Script):</span><span class="sxs-lookup"><span data-stu-id="7e244-160">With the **Lunarcom** object still selected, expand it to reveal its child objects, then drag the **Terminal** object into the Lunarcom Controller (Script) component's **Terminal** field:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-3.png)

<span data-ttu-id="7e244-162">Con l'oggetto **Lunarcom** ancora selezionato, espandi l'oggetto Terminal in modo da visualizzarne gli oggetti figlio e quindi trascina l'oggetto **ConnectionLight** nel campo **Connection Light** (Luce di connessione) e l'oggetto **OutputText** nel campo **Output Text** (Testo di output) del componente Lunarcom Controller (Script) (Controller Lunarcom - Script):</span><span class="sxs-lookup"><span data-stu-id="7e244-162">With the **Lunarcom** object still selected, expand the Terminal object to reveal its child objects, then drag the **ConnectionLight** object into the Lunarcom Controller (Script) component's **Connection Light** field and the **OutputText** object into the **Output Text** field:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-4.png)

<span data-ttu-id="7e244-164">Con l'oggetto **Lunarcom** ancora selezionato, espandi l'oggetto Buttons per visualizzarne gli oggetti figlio e quindi nella finestra Inspector (Controllo) espandi l'elenco **Buttons** (Pulsanti), imposta **Size** (Dimensioni) su 3 e trascina gli oggetti **MicButton**, **SatelliteButton** e **RocketButton** rispettivamente nei campi **Element** (Elemento) 0, 1 e 2:</span><span class="sxs-lookup"><span data-stu-id="7e244-164">With the **Lunarcom** object still selected, expand the Buttons object to reveal its child objects, and then in the Inspector window, expand the **Buttons** list, set its **Size** to 3, and drag the **MicButton**, **SatelliteButton**, and **RocketButton** objects into the **Element** 0, 1, and 2 fields respectively:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-5.png)

## <a name="connecting-the-unity-project-to-the-azure-resource"></a><span data-ttu-id="7e244-166">Connessione del progetto Unity alla risorsa di Azure</span><span class="sxs-lookup"><span data-stu-id="7e244-166">Connecting the Unity project to the Azure resource</span></span>

<span data-ttu-id="7e244-167">Per usare i servizi vocali di Azure, devi creare una risorsa di Azure e ottenere una chiave API per il servizio vocale.</span><span class="sxs-lookup"><span data-stu-id="7e244-167">To use Azure Speech Services, you need to create an Azure resource and obtain an API key for the Speech Service.</span></span> <span data-ttu-id="7e244-168">Segui le istruzioni contenute in [Provare gratuitamente il servizio Voce](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started) e prendi nota dell'area geografica del servizio, (definita anche posizione) e della chiave API (definita anche Key1 o Key2).</span><span class="sxs-lookup"><span data-stu-id="7e244-168">Follow the [Try the Speech service for free](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started) instructions and make a note of your service region (also known as Location) and API key (also known as Key1 or Key2).</span></span>

<span data-ttu-id="7e244-169">Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **Lunarcom** e quindi nella finestra Inspector (Controllo) individua la sezione **Speech SDK Credentials** (Credenziali Speech SDK) del componente **Lunarcom Controller (Script)** (Controller Lunarcom - Script) e configurala come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="7e244-169">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, locate the **Lunarcom Controller (Script)** component's **Speech SDK Credentials** section and configure it as follows:</span></span>

* <span data-ttu-id="7e244-170">Nel campo **Speech Service API Key** (Chiave API servizio vocale) immetti la chiave API (Key1 o Key2)</span><span class="sxs-lookup"><span data-stu-id="7e244-170">In the **Speech Service API Key** field, enter your API key (Key1 or Key2)</span></span>
* <span data-ttu-id="7e244-171">Nel campo **Speech Service Region** (Area del servizio vocale) immetti l'area geografica del servizio (posizione) usando lettere minuscole e rimuovendo gli spazi</span><span class="sxs-lookup"><span data-stu-id="7e244-171">In the **Speech Service Region** field, enter your service region (Location) using lowercase letters and spaces removed</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section6-step1-1.png)

## <a name="using-speech-recognition-to-transcribe-speech"></a><span data-ttu-id="7e244-173">Uso del riconoscimento vocale per la trascrizione di testo</span><span class="sxs-lookup"><span data-stu-id="7e244-173">Using speech recognition to transcribe speech</span></span>

<span data-ttu-id="7e244-174">Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **Lunarcom** e quindi nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Lunarcom Speech Recognizer (Script)** (Riconoscimento vocale Lunarcom - Script) all'oggetto Lunarcom:</span><span class="sxs-lookup"><span data-stu-id="7e244-174">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Speech Recognizer (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-1.png)

> [!NOTE]
> <span data-ttu-id="7e244-176">Il componente Lunarcom Speech Recognizer (Script) (Riconoscimento vocale Lunarcom - Script) non fa parte di MRTK.</span><span class="sxs-lookup"><span data-stu-id="7e244-176">The Lunarcom Speech Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="7e244-177">È stato fornito con gli asset dell'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="7e244-177">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="7e244-178">Se ora attivi la modalità gioco, puoi testare il riconoscimento vocale selezionando prima il pulsante del microfono:</span><span class="sxs-lookup"><span data-stu-id="7e244-178">If you now enter Game mode, you can test the speech recognition by first pressing the microphone button:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-2.png)

<span data-ttu-id="7e244-180">Supponendo quindi che il computer disponga di un microfono, quando pronunci una frase, questa verrà trascritta nel pannello del terminale:</span><span class="sxs-lookup"><span data-stu-id="7e244-180">Then, assuming your computer has a microphone, when you say something, your speech will be transcribed on the terminal panel:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-3.png)


> [!CAUTION]
> <span data-ttu-id="7e244-182">Poiché l'applicazione deve connettersi ad Azure, assicurati che il computer o il dispositivo sia connesso a Internet.</span><span class="sxs-lookup"><span data-stu-id="7e244-182">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="7e244-183">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="7e244-183">Congratulations</span></span>

<span data-ttu-id="7e244-184">Hai implementato il riconoscimento vocale basato su Azure.</span><span class="sxs-lookup"><span data-stu-id="7e244-184">You have implemented speech recognition powered by Azure.</span></span> <span data-ttu-id="7e244-185">Esegui l'applicazione nel dispositivo per verificare che la funzionalità venga eseguita correttamente.</span><span class="sxs-lookup"><span data-stu-id="7e244-185">Run the application on your device to ensure the feature is working properly.</span></span>

<span data-ttu-id="7e244-186">Nell'esercitazione successiva apprenderai come eseguire i comandi con il riconoscimento vocale di Azure.</span><span class="sxs-lookup"><span data-stu-id="7e244-186">In the next tutorial, you will learn how to execute commands using Azure speech recognition.</span></span>

[<span data-ttu-id="7e244-187">Esercitazione successiva: 2. Uso del riconoscimento vocale per l'esecuzione di comandi</span><span class="sxs-lookup"><span data-stu-id="7e244-187">Next tutorial: 2. Using speech recognition to execute commands</span></span>](mrlearning-speechSDK-ch2.md)

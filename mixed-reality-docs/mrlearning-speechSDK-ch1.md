---
title: Esercitazioni sui servizi vocali di Azure - 1. Integrazione e uso del riconoscimento vocale e della trascrizione
description: Completa questo corso per imparare a implementare Azure Speech SDK in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: 71a6c2124258f05e80e624b940386db72a36070b
ms.sourcegitcommit: 92ff5478a5c55b4e2c5cc2f44f1588702f4ec5d1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/30/2020
ms.locfileid: "82604982"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a>1. Integrazione e uso del riconoscimento vocale e della trascrizione

## <a name="overview"></a>Panoramica


In questa serie di esercitazioni creerai un'applicazione di Realtà mista per esplorare l'uso dei servizi vocali di Azure con HoloLens 2. Al termine di questa serie di esercitazioni, sarai in grado di usare il microfono del tuo dispositivo per trascrivere il parlato in testo in tempo reale, tradurre il parlato in altre lingue e utilizzare la funzionalità Riconoscimento finalità per comprendere i comandi vocali usando l'intelligenza artificiale.

## <a name="objectives"></a>Obiettivi

* Imparare a integrare i servizi vocali di Azure con un'applicazione HoloLens 2
* Imparare a usare il riconoscimento vocale per trascrivere testo

## <a name="prerequisites"></a>Prerequisiti

>[!TIP]
>Se non hai ancora completato la serie di [Esercitazioni introduttive](mrlearning-base.md), è consigliabile completare prima queste esercitazioni.

* Un PC Windows 10 configurato in cui siano [installati gli strumenti](install-the-tools.md) corretti
* Windows 10 SDK 10.0.18362.0 o versioni successive
* Alcune funzionalità di programmazione C# di base
* Un dispositivo HoloLens 2 [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode)
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.2.X installato e il modulo di supporto delle compilazioni UWP (Universal Windows Platform) aggiunto

> [!IMPORTANT]
> La versione di Unity consigliata per questa serie di esercitazioni è Unity 2019.2.X. Questa istruzione sostituisce gli eventuali requisiti o suggerimenti relativi alla versione di Unity indicati negli argomenti visualizzabili facendo clic sui collegamenti dei prerequisiti sopra riportati.

## <a name="creating-and-preparing-the-unity-project"></a>Creazione e preparazione del progetto Unity

In questa sezione creerai un nuovo progetto Unity per prepararti allo sviluppo con MRTK.

A questo scopo, segui prima l'esercitazione [Inizializzazione del progetto e prima applicazione](mrlearning-base-ch1.md), escluse le istruzioni della sezione [Compilare l'applicazione nel dispositivo](mrlearning-base-ch1.md#build-your-application-to-your-device), che include i passaggi seguenti:

1. [Creare un nuovo progetto Unity](mrlearning-base-ch1.md#create-new-unity-project) e assegnargli un nome appropriato, ad esempio *MRTK Tutorials*

2. [Configurare il progetto Unity per Windows Mixed Reality](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [Importare le risorse essenziali TextMesh Pro](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [Importare Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [Configurare il progetto Unity per Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. [Aggiungere Mixed Reality Toolkit alla scena di Unity](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) e assegnare alla scena un nome appropriato, ad esempio *AzureSpeechServices*

Segui quindi le istruzioni riportate in [Come configurare i profili di Mixed Reality Toolkit (modifica dell'opzione di visualizzazione della mesh di consapevolezza spaziale)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) per impostare **DefaultHoloLens2ConfigurationProfile** come profilo di configurazione MRTK per la scena e modificare le opzioni di visualizzazione per la mesh di riconoscimento spaziale impostando **Occlusion** (Occlusione).

> [!CAUTION]
> Come indicato nelle istruzioni in [Configurare il progetto Unity per Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit), è fortemente sconsigliato abilitare MSBuild per Unity.

## <a name="configuring-the-speech-commands-start-behavior"></a>Configurazione del comportamento di avvio dei comandi vocali

Poiché userai Speech SDK per il riconoscimento vocale e la trascrizione, devi configurare i comandi vocali di MRTK in modo che non interferiscano con le funzionalità di Speech SDK. A tale scopo, puoi modificare il comportamento di avvio dei comandi vocali da Auto Start (Avvio automatico) a Manual Start (Avvio manuale).

Con l'oggetto **MixedRealityToolkit** selezionato nella finestra Hierarchy (Gerarchia), nella finestra Inspector (Controllo) seleziona la scheda **Input**, clona **DefaultHoloLens2InputSystemProfile** e **DefaultMixedRealitySpeechCommandsProfile** e quindi modifica i comandi vocali di **Start Behavior** (Comportamento di avvio) in **Manual Start** (Avvio manuale):

![mrlearning-speech](images/mrlearning-speech/tutorial1-section2-step1-1.png)

> [!TIP]
> Per rivedere la procedura di clonazione e configurazione di profili MRTK, puoi fare riferimento alle istruzioni contenute in [Come configurare i profili di Mixed Reality Toolkit (modifica dell'opzione di visualizzazione della mesh di consapevolezza spaziale)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option).

## <a name="configuring-the-capabilities"></a>Configurazione delle funzionalità

Dal menu Unity scegli **Edit** > **Project Settings...** (Modifica > Impostazioni del progetto) per aprire la finestra Project Settings (Impostazioni del progetto) e quindi individua la sezione **Player** >  **Publishing Settings** (Lettore > Impostazioni di pubblicazione):

![mrlearning-speech](images/mrlearning-speech/tutorial1-section3-step1-1.png)

In **Publishing Settings** (Impostazioni di pubblicazione) scorri verso il basso fino alla sezione **Capabilities** (Funzionalità) e verifica che siano abilitate le funzionalità **InternetClient**, **Microphone** e **SpatialPerception**, che hai abilitato al momento della creazione del progetto all'inizio dell'esercitazione. Abilita quindi le funzionalità **InternetClientServer** e **PrivateNetworkClientServer**:

![mrlearning-speech](images/mrlearning-speech/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a>Importazione degli asset dell'esercitazione

Scarica e **importa** i pacchetti personalizzati di Unity seguenti, **nell'ordine in cui sono elencati**:

* [Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage) (versione più recente)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-speech-services-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage)

> [!TIP]
> Per rivedere la procedura di importazione di un pacchetto personalizzato di Unity, puoi fare riferimento alle istruzioni contenute in [Importare Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).

Dopo l'importazione degli asset dell'esercitazione, la finestra Project (Progetto) avrà un aspetto simile al seguente:

![mrlearning-speech](images/mrlearning-speech/tutorial1-section4-step1-1.png)

## <a name="preparing-the-scene"></a>Preparazione della scena

In questa sezione preparerai la scena aggiungendo il prefab dell'esercitazione e configurerai il componente Lunarcom Controller (Script) (Controller Lunarcom - Script) per il controllo della scena.

Nella finestra Project (Progetto) passa ad **Assets** > **MRTK.Tutorials.AzureSpeechServices** > **Prefabs** (Asset > MRTK.Tutorials.AzureSpeechServices > Prefab) e trascina il prefab **Lunarcom** nella finestra Hierarchy (Gerarchia) per aggiungerlo alla scena:

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-1.png)

Con l'oggetto **Lunarcom** ancora selezionato nella finestra Hierarchy (Gerarchia), nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Lunarcom Controller (Script)** (Controller Lunarcom - Script) all'oggetto Lunarcom:

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-2.png)

> [!NOTE]
> Il componente Lunarcom Controller (Script) (Controller Lunarcom - Script) non fa parte di MRTK. È stato fornito con gli asset dell'esercitazione.

Con l'oggetto **Lunarcom** ancora selezionato, espandi l'oggetto in modo da visualizzarne gli oggetti figlio e quindi trascina l'oggetto **Terminal** nel campo **Terminal** (Terminale) del componente Lunarcom Controller (Script) (Controller Lunarcom - Script):

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-3.png)

Con l'oggetto **Lunarcom** ancora selezionato, espandi l'oggetto Terminal in modo da visualizzarne gli oggetti figlio e quindi trascina l'oggetto **ConnectionLight** nel campo **Connection Light** (Luce di connessione) e l'oggetto **OutputText** nel campo **Output Text** (Testo di output) del componente Lunarcom Controller (Script) (Controller Lunarcom - Script):

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-4.png)

Con l'oggetto **Lunarcom** ancora selezionato, espandi l'oggetto Buttons per visualizzarne gli oggetti figlio e quindi nella finestra Inspector (Controllo) espandi l'elenco **Buttons** (Pulsanti), imposta **Size** (Dimensioni) su 3 e trascina gli oggetti **MicButton**, **SatelliteButton** e **RocketButton** rispettivamente nei campi **Element** (Elemento) 0, 1 e 2:

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-5.png)

## <a name="connecting-the-unity-project-to-the-azure-resource"></a>Connessione del progetto Unity alla risorsa di Azure

Per usare i servizi vocali di Azure, devi creare una risorsa di Azure e ottenere una chiave API per il servizio vocale. Segui le istruzioni contenute in [Provare gratuitamente il servizio Voce](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started) e prendi nota dell'area geografica del servizio, (definita anche posizione) e della chiave API (definita anche Key1 o Key2).

Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **Lunarcom** e quindi nella finestra Inspector (Controllo) individua la sezione **Speech SDK Credentials** (Credenziali Speech SDK) del componente **Lunarcom Controller (Script)** (Controller Lunarcom - Script) e configurala come indicato di seguito:

* Nel campo **Speech Service API Key** (Chiave API servizio vocale) immetti la chiave API (Key1 o Key2)
* Nel campo **Speech Service Region** (Area del servizio vocale) immetti l'area geografica del servizio (posizione) usando lettere minuscole e rimuovendo gli spazi

![mrlearning-speech](images/mrlearning-speech/tutorial1-section6-step1-1.png)

## <a name="using-speech-recognition-to-transcribe-speech"></a>Uso del riconoscimento vocale per la trascrizione di testo

Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **Lunarcom** e quindi nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Lunarcom Speech Recognizer (Script)** (Riconoscimento vocale Lunarcom - Script) all'oggetto Lunarcom:

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-1.png)

> [!NOTE]
> Il componente Lunarcom Speech Recognizer (Script) (Riconoscimento vocale Lunarcom - Script) non fa parte di MRTK. È stato fornito con gli asset dell'esercitazione.

Se ora attivi la modalità gioco, puoi testare il riconoscimento vocale selezionando prima il pulsante del microfono:

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-2.png)

Supponendo quindi che il computer disponga di un microfono, quando pronunci una frase, questa verrà trascritta nel pannello del terminale:

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-3.png)


> [!CAUTION]
> Poiché l'applicazione deve connettersi ad Azure, assicurati che il computer o il dispositivo sia connesso a Internet.

## <a name="congratulations"></a>Lezione completata

Hai implementato il riconoscimento vocale basato su Azure. Esegui l'applicazione nel dispositivo per verificare che la funzionalità venga eseguita correttamente.

Nell'esercitazione successiva apprenderai come eseguire i comandi con il riconoscimento vocale di Azure.

[Esercitazione successiva: 2. Uso del riconoscimento vocale per l'esecuzione di comandi](mrlearning-speechSDK-ch2.md)

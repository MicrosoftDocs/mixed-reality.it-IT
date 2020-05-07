---
title: Esercitazioni sulle funzionalità multiutente - 1. Configurazione di Photon Unity Networking
description: Completa questo corso per imparare a implementare esperienze condivise multiutente all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: 2f5b55fe9c54e9e2c08177266c04a97d2302230e
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610681"
---
# <a name="1-setting-up-photon-unity-networking"></a>1. Configurazione di Photon Unity Networking

## <a name="overview"></a>Panoramica

In questa esercitazione imparerai a prepararti per la creazione di un'esperienza condivisa tramite Photon Unity Networking (PUN). Photon è una delle diverse opzioni di rete disponibili per gli sviluppatori di Realtà mista per creare esperienze condivise. Scoprirai come creare un'applicazione Photon PUN, importare asset di Photon PUN nel progetto Unity e connettere il progetto Unity all'applicazione Photon PUN.

## <a name="objectives"></a>Obiettivi

* Imparare a creare un'applicazione Photon PUN
* Imparare a trovare e importare gli asset di Photon PUN
* Imparare a connettere il progetto Unity all'applicazione Photon PUN

## <a name="prerequisites"></a>Prerequisiti

>[!TIP]
>Se non hai ancora completato le serie di [Esercitazioni introduttive](mrlearning-base.md) ed [Esercitazioni su Ancoraggi nello spazio di Azure](mrlearning-asa-ch1.md), è consigliabile completare prima queste esercitazioni.

* Un PC Windows 10 configurato in cui siano [installati gli strumenti](install-the-tools.md) corretti
* Windows 10 SDK 10.0.18362.0 o versioni successive
* Alcune funzionalità di programmazione C# di base
* Un dispositivo HoloLens 2 [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode)
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.2.X installato e il modulo di supporto delle compilazioni UWP (Universal Windows Platform) aggiunto
* Completa la sezione [Creare una risorsa di Ancoraggi nello spazio](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) dell'esercitazione [Avvio rapido: Creare un'app HoloLens in Unity che usa Ancoraggi nello spazio di Azure](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)

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

6. [Aggiungere Mixed Reality Toolkit alla scena di Unity](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) e assegnare alla scena un nome appropriato, ad esempio *MultiUserCapabilities*

Segui quindi le istruzioni riportate in [Come configurare i profili di Mixed Reality Toolkit (modifica dell'opzione di visualizzazione della mesh di consapevolezza spaziale)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) per impostare **DefaultHoloLens2ConfigurationProfile** come profilo di configurazione MRTK per la scena e modificare in **Occlusion** (Occlusione) le opzioni di visualizzazione per la mesh di consapevolezza spaziale.

> [!CAUTION]
> Come indicato nelle istruzioni contenute in [Configurare il progetto Unity per Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit), è fortemente sconsigliabile abilitare MSBuild per Unity.

## <a name="configuring-the-capabilities"></a>Configurazione delle funzionalità

Dal menu Unity scegli **Edit** > **Project Settings...** (Modifica > Impostazioni del progetto) per aprire la finestra Project Settings (Impostazioni del progetto) e quindi individua la sezione **Player** >  **Publishing Settings** (Lettore > Impostazioni di pubblicazione):

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial1-section2-step1-1.png)

In **Publishing Settings** (Impostazioni di pubblicazione) scorri verso il basso fino alla sezione **Capabilities** (Funzionalità) e verifica che siano abilitate le funzionalità **InternetClient**, **Microphone** e **SpatialPerception**, che hai abilitato al momento della creazione del progetto all'inizio dell'esercitazione. Abilita quindi le funzionalità **InternetClientServer**, **PrivateNetworkClientServer** e **RemovableStorage**:

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial1-section2-step1-2.png)

## <a name="adding-inbuilt-unity-packages"></a>Aggiunta di pacchetti di Unity incorporati
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

In questa sezione installerai il pacchetto AR Foundation incorporato di Unity perché è un prerequisito dell'SDK di Ancoraggi nello spazio di Azure che importerai nella sezione successiva.

Nel menu di Unity seleziona **Window** (Finestra) > **Package Manager** (Gestione pacchetti):

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial1-section3-step1-1.png)

> [!NOTE]
> Potrebbero essere necessari alcuni secondi prima che il pacchetto AR Foundation venga visualizzato nell'elenco.

Nella finestra Package Manager (Gestione pacchetti) seleziona **AR Foundation** e installa il pacchetto facendo clic sul pulsante **Install** (Installa):

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a>Importazione degli asset dell'esercitazione

Scarica e **importa** i pacchetti personalizzati di Unity seguenti, **nell'ordine in cui sono elencati**:

* [AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (versione 2.1.1)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.3.0.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.3.0.0.unitypackage)

> [!TIP]
> Per rivedere la procedura di importazione di un pacchetto personalizzato di Unity, puoi fare riferimento alle istruzioni contenute in [Importare Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).

Dopo l'importazione degli asset dell'esercitazione, la finestra Project (Progetto) avrà un aspetto simile al seguente:

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial1-section4-step1-1.png)

> [!NOTE]
> Dopo aver importato il pacchetto di asset dell'esercitazione MultiUserCapabilities, nella finestra della console verranno visualizzati alcuni errori [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246) che indicano che manca il tipo o lo spazio dei nomi. Si tratta di un comportamento previsto, che verrà risolto nella prossima sezione quando importerai gli asset di Photon.

## <a name="importing-the-photon-assets"></a>Importazione degli asset di Photon

In questa sezione importerai gli asset di Photon Unity Network (PUN) da Unity Asset Store.

Nel menu di Unity seleziona **Window** (Finestra) > **Asset Store** per aprire la finestra di Asset Store, cerca e seleziona **PUN 2 - FREE** in Exit Games (Giochi in uscita) e quindi fai clic sul pulsante **Download** (Scarica) per scaricare il pacchetto di asset nel tuo account Unity:

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial1-section5-step1-1.png)

Al termine del download, fai clic sul pulsante **Import** (Importa) per aprire la finestra Import Unity Package (Importa pacchetto Unity):

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial1-section5-step1-2.png)

Nella finestra Import Unity Package (Importa il pacchetto Unity), fai clic sul pulsante **All** (Tutti) per assicurarti che vengano selezionati tutti gli asset e quindi fai clic sul pulsante **Import** (Importa) per importare gli asset:

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial1-section5-step1-3.png)

Dopo che Unity ha completato il processo di importazione, verrà visualizzata la finestra PUN Wizard (Creazione guidata PUN) con il menu PUN Setup (Configurazione PUN) caricato. Per il momento puoi ignorare o chiudere questa finestra:

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial1-section5-step1-4.png)

## <a name="setting-up-photon"></a>Configurazione di Photon

In questa sezione creerai un account Photon, se non ne hai già uno, e una nuova applicazione PUN.

Passa al <a href="https://dashboard.photonengine.com/account/signin" target="_blank">dashboard</a> di Photon ed esegui l'accesso se hai già un account che vuoi usare. In caso contrario, fai clic sul collegamento **Create One** (Creane uno) e segui le istruzioni per la registrazione di un nuovo account:

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial1-section6-step1-1.png)

Una volta eseguito l'accesso, fai clic sul pulsante **Create a New App** (Crea una nuova app):

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial1-section6-step1-2.png)

Nella pagina Create a New Application (Crea una nuova applicazione) immetti i valori seguenti:

* In Photon Type (Tipo Photon) seleziona Photon PUN
* In Name (Nome) immetti un nome appropriato, ad esempio _MRTK Tutorials_
* In Description (Descrizione) immetti facoltativamente una descrizione appropriata
* In Url lascia il campo vuoto

Fai quindi clic sul pulsante **Create** (Crea) per creare la nuova applicazione:

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial1-section6-step1-3.png)

Al termine del processo di creazione, nel dashboard verrà visualizzata la nuova applicazione PUN:

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial1-section6-step1-4.png)

## <a name="connecting-the-unity-project-to-the-pun-application"></a>Connessione del progetto Unity all'applicazione PUN

In questa sezione connetterai il progetto Unity all'applicazione PUN creata nella sezione precedente.

Nel dashboard di Photon fai clic sul campo **App ID** (ID app) per visualizzare l'ID dell'app e quindi copialo negli Appunti:

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial1-section7-step1-1.png)

Nel menu di Unity seleziona **Window** (Finestra) > **Photon Unity Networking** > **PUN Wizard** (Creazione guidata PUN) per aprire la finestra PUN Wizard (Creazione guidata PUN), fai clic sul pulsante **Setup Project** (Configura progetto) per aprire il menu PUN Setup (Configurazione PUN) ed esegui la configurazione nel modo seguente:

* Nel campo **AppId or Email** (ID app o e-mail) incolla l'ID dell'app PUN copiato nel passaggio precedente

Fai quindi clic sul pulsante **Setup Project** (Configura progetto) per applicare l'ID dell'app:

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial1-section7-step1-2.png)

Dopo che Unity ha terminato il processo di configurazione di PUN, nel menu PUN Setup (Configurazione PUN) verrà visualizzato il messaggio **Done!** (Fatto) e nella finestra Project (Progetto) verrà selezionato automaticamente l'asset **PhotonServerSettings** in modo che le relative proprietà siano visualizzate nella finestra Inspector (Controllo):

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial1-section7-step1-3.png)

## <a name="congratulations"></a>Lezione completata

Hai creato un'applicazione Photon PUN e l'hai connessa al progetto Unity. Il passaggio successivo consiste nel consentire connessioni con altri utenti, in modo che ogni utente possa visualizzare il lavoro svolto dagli altri.

[Esercitazione successiva: 2. Connessione di più utenti](mrlearning-sharing(photon)-ch2.md)

---
title: Esercitazioni sul cloud di Azure - 1. Servizi cloud di Azure per HoloLens 2
description: Completa questo corso per imparare a implementare vari servizi di Azure all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: azure, realtà mista, unity, esercitazione, hololens, hololens 2, archiviazione blob di azure, archiviazione tabelle di azure, ancoraggi nello spazio di azure, azure bot framework
ms.localizationpriority: high
ms.openlocfilehash: 649046f9416c880d6e69b544866fba60d3e43f4c
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/14/2020
ms.locfileid: "86304980"
---
# <a name="1-azure-cloud-services-for-hololens-2"></a>1. Servizi cloud di Azure per HoloLens 2

## <a name="overview"></a>Panoramica

Questa serie di esercitazioni è incentrata sull'inserimento di servizi **cloud di Azure** in un'applicazione **HoloLens 2**. In questa serie di esercitazioni in cinque parti imparerai come integrare diversi servizi **cloud di Azure** in un progetto **Unity** per **HoloLens 2**. Un capitolo dopo l'altro, aggiungerai nuovi servizi **cloud di Azure** per espandere le funzionalità dell'applicazione e l'esperienza utente e allo stesso tempo apprenderai i concetti di base di ciascun servizio **cloud di Azure**.

> [!NOTE]
> Questa serie di esercitazioni verterà soprattutto su **HoloLens 2** ma, data la natura multipiattaforma di Unity, la maggior parte delle nozioni apprese si applicherà anche alle applicazioni desktop e per smartphone.

In questa prima esercitazione, [Introduzione ai servizi cloud di Azure per HoloLens 2](mr-learning-azure-01.md), vengono innanzitutto illustrati gli obiettivi dell'applicazione e vengono brevemente introdotti i singoli servizi cloud di Azure e l'impostazione del progetto Unity.

Nella seconda esercitazione, [Integrazione di Archiviazione di Azure](mr-learning-azure-02.md), potrai integrare Archiviazione di Azure come soluzione di persistenza per l'applicazione demo, apprendere le differenze tra Archiviazione BLOB e archiviazione tabelle, preparare le risorse di progetto necessarie, impostare la scena e verificare le operazioni di lettura, aggiornamento ed eliminazione dei dati.

Continuando con la terza esercitazione, [Integrazione di Visione personalizzata di Azure](mr-learning-azure-03.md), userai questo servizio per eseguire il training e il rilevamento delle immagini nell'applicazione HoloLens 2. Il capitolo comincia con l'impostazione della risorsa Visione personalizzata di Azure e potrai preparare i componenti della scena e iniziare a lavorare eseguendo il training e rilevando le tue immagini dall'interno dell'applicazione.

Potrai quindi passare alla quarta esercitazione, [Integrazione di ancoraggi nello spazio di Azure](mr-learning-azure-04.md), ed esplorare questo servizio per salvare e trovare le posizioni, apprendere i concetti principali, preparare le risorse necessarie, impostare la scena e iniziare a usare la nuova funzionalità nell'applicazione.

Con la quinta esercitazione, [Integrazione del servizio Azure Bot con LUIS](mr-learning-azure-05.md), potrai terminare la tua preparazione fornendo all'applicazione un nuovo metodo di interazione dell'utente: il linguaggio naturale. Questa funzionalità verrà realizzata usando Azure Bot Framework insieme a Language Understanding (LUIS). Questo capitolo finale illustra le nozioni di base del servizio Azure Bot e, per velocizzare il processo, userai Bot Framework Composer come soluzione senza codice. Una volta creato il bot, lo integrerai nella scena e potrai eseguirlo con la fase finale dell'applicazione HoloLens 2.

## <a name="application-goals"></a>Obiettivi dell'applicazione

In questa serie di esercitazioni verrà creata un'applicazione **HoloLens 2** in grado di rilevare oggetti dalle immagini e trovarne la posizione nello spazio. Per definire una terminologia specifica, da questo momento in poi tali entità vengono definite **oggetto tracciato**.
L'utente può creare un **oggetto tracciato** per associare un set di immagini tramite visione artificiale e/o una posizione nello spazio. Tutti i dati devono essere salvati nel cloud. Inoltre, alcuni aspetti dell'applicazione saranno controllati facoltativamente dal linguaggio naturale assistito tramite un bot.

### <a name="features"></a>Caratteristiche

* Gestione di base di dati e immagini
* Training e rilevamento delle immagini
* Archiviazione di una posizione nello spazio e indicazioni per trovarla
* Assistente bot per usare alcune funzionalità tramite linguaggio naturale

## <a name="azure-cloud-services"></a>Servizi cloud di Azure

Per disporre delle funzionalità necessarie per l'applicazione, userai i servizi **cloud di Azure** descritti di seguito:

### <a name="azure-storage"></a>Archiviazione di Azure

Userai [Archiviazione di Azure](https://azure.microsoft.com/services/storage/) per la soluzione di persistenza. Consente di archiviare i dati in una tabella e caricare file binari di grandi dimensioni, ad esempio immagini.

### <a name="azure-custom-vision"></a>Visione personalizzata di Azure

Con [Visione personalizzata di Azure](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/) (che fa parte di [Servizi cognitivi di Azure](https://azure.microsoft.com/services/cognitive-services/)) puoi associare agli *oggetti tracciati* un set di immagini, eseguire il training di un modello di Machine Learning per il set e rilevare l'*oggetto tracciato*.

### <a name="azure-spatial-anchors"></a>Ancoraggi nello spazio di Azure

Per archiviare la posizione di un *oggetto tracciato* e fornire indicazioni guidate per trovarla, puoi usare [ancoraggi nello spazio di Azure](https://azure.microsoft.com/services/spatial-anchors/).

### <a name="azure-bot-service"></a>servizio Azure Bot

L'applicazione è basata principalmente sull'interfaccia utente tradizionale, quindi puoi usare il [servizio Azure Bot](https://azure.microsoft.com/services/bot-service/) per aggiungere personalità e operare con un nuovo metodo di interazione.

## <a name="prerequisites"></a>Prerequisiti

>[!TIP]
>Se non hai ancora completato la serie di [Esercitazioni introduttive](mr-learning-base-01.md), è consigliabile completare prima queste esercitazioni.

* Un PC Windows 10 configurato in cui siano [installati gli strumenti](install-the-tools.md) corretti
* Windows 10 SDK 10.0.18362.0 o versioni successive
* Alcune funzionalità di programmazione C# di base
* Un dispositivo HoloLens 2 [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode)
* Una webcam connessa se vuoi eseguire il test dall'editor di Unity
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.3.X installato e il modulo di supporto delle compilazioni UWP (Universal Windows Platform) aggiunto

> [!CAUTION]
> La versione di Unity consigliata per questa serie di esercitazioni è Unity 2019.3.X. Questa istruzione sostituisce gli eventuali requisiti o suggerimenti relativi alla versione di Unity indicati negli argomenti visualizzabili facendo clic sui collegamenti dei prerequisiti sopra riportati.

## <a name="creating-and-preparing-the-unity-project"></a>Creazione e preparazione del progetto Unity

In questa sezione creerai un nuovo progetto Unity per prepararti allo sviluppo con MRTK.

A questo scopo, segui prima l'esercitazione [Inizializzazione del progetto e prima applicazione](mr-learning-base-02.md), escluse le istruzioni della sezione [Compilare l'applicazione nel dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), che include i passaggi seguenti:

1. [Creazione del progetto Unity](mr-learning-base-02.md#creating-the-unity-project) e assegnazione di un nome appropriato, ad esempio *Azure Cloud Tutorials*
2. [Passaggio a un'altra piattaforma di compilazione](mr-learning-base-02.md#configuring-the-unity-project)
3. [Importazione delle risorse essenziali TextMeshPro](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
4. [Importazione di Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
5. [Configurazione del progetto Unity](mr-learning-base-02.md#configuring-the-unity-project)
6. [Creazione e configurazione della scena](mr-learning-base-02.md#creating-and-configuring-the-scene) e assegnazione di un nome appropriato, ad esempio *AzureCloudServices*

Segui quindi le istruzioni riportate in [Modifica delle opzioni di visualizzazione di consapevolezza spaziale](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) per impostare **DefaultHoloLens2ConfigurationProfile** come profilo di configurazione MRTK per la scena e modificare queste opzioni impostando **Occlusion** (Occlusione).

## <a name="installing-inbuilt-unity-packages"></a>Installazione di pacchetti di Unity incorporati

Scegli **Window** (Finestra)  > **Package Manager** (Gestione pacchetti) dal menu Unity per aprire la finestra Package Manager(Gestione pacchetti), quindi seleziona **AR Foundation** e fai clic sul pulsante **Install** (Installa) per installare il pacchetto:

![mr-learning-azure](images/mr-learning-asa/asa-02-section2-step1-1.png)

> [!NOTE]
> Stai installando il pacchetto AR Foundation perché è richiesto da Azure Spatial Anchors SDK, che verrà importato nella sezione successiva.

## <a name="importing-the-tutorial-assets"></a>Importazione degli asset dell'esercitazione

Scarica e **importa** i pacchetti personalizzati di Unity seguenti, **nell'ordine in cui sono elencati**:

* [Archiviazione di Azure per Unity](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/AzureStorageForUnity.unitypackage)
* [Ancoraggi nello spazio di Azure](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage)
* [MRTK.Tutorials.AzureCloudServices](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/MRTK.Tutorials.AzureCloudServices.unitypackage)

> [!TIP]
> Per rivedere la procedura di importazione di un pacchetto personalizzato di Unity, puoi fare riferimento alle istruzioni contenute in [Importare Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit).

Dopo l'importazione degli asset dell'esercitazione, la finestra Project (Progetto) avrà un aspetto simile al seguente:

![mr-learning-azure](images/mr-learning-azure/tutorial1-section4-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a>Creazione e preparazione della scena
<!-- TODO: Consider renaming to 'Preparing the scene' -->

In questa sezione preparerai la scena aggiungendo alcuni dei prefab dell'esercitazione.

Nella finestra Project (Progetto) passa alla cartella **Assets** (Asset)  > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** (Prefab)  > **Manager**. Tenendo premuto il tasto CTRL, fai clic su **SceneController**, **RootMenu** e **DataManager** per selezionare i tre prefab:

![mr-learning-azure](images/mr-learning-azure/tutorial1-section5-step1-1.png)

**SceneController (prefab)** contiene due script, **SceneController (script)** e **UnityDispatcher (script)** . Il componente script **SceneController** contiene diverse funzioni UX e semplifica la funzionalità di acquisizione foto, mentre **UnityDispatcher** è una classe helper che consente l'esecuzione di azioni sul thread principale di Unity.

**RootMenu (prefab)** è il principale prefab dell'interfaccia utente e include tutte le relative finestre, che sono connesse tra loro tramite vari piccoli componenti script e controllano il flusso UX generale dell'applicazione.

**DataManager (prefab)** è responsabile della comunicazione con Archiviazione di Azure e verrà illustrato più in dettaglio nell'esercitazione successiva.

Ora con i tre prefab ancora selezionati, trascinali nella finestra Hierarchy (Gerarchia) per aggiungerli alla scena:

![mr-learning-azure](images/mr-learning-azure/tutorial1-section5-step1-2.png)

Per concentrarti sugli oggetti nella scena, puoi fare doppio clic sull'oggetto **RootMenu** e quindi fare di nuovo leggermente zoom indietro:

![mr-learning-azure](images/mr-learning-azure/tutorial1-section5-step1-3.png)

> [!TIP]
> Se trovi che le icone grandi nella scena, come quelle a forma di "T", siano motivo di distrazione, puoi nasconderle <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">disattivando i gizmo</a>.

## <a name="configuring-the-scene"></a>Configurazione della scena

In questa sezione connetterai *SceneManager*, *DataManager* e *RootMenu* insieme in modo che una scena di lavoro sia pronta per l'esercitazione successiva, ovvero [Integrazione di Archiviazione di Azure](mr-learning-azure-01.md).

### <a name="connect-the-objects"></a>Connettere gli oggetti

Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **DataManager**:

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-1.png)

Nella finestra Inspector (Controllo) individua il componente **DataManager (Script)** . Verrà visualizzato uno slot vuoto per l'evento **On Data Manager Ready ()** (Quando Data Manager è pronto). Ora dalla finestra Hierarchy (Gerarchia) trascina l'oggetto **SceneController** nell'evento **On Data Manager Ready ()** (Quando Data Manager è pronto).

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-2.png)

Noterai che il menu a discesa dell'evento è diventato attivo. Fai clic su questo menu e passa a **SceneController**, quindi dal sottomenu scegli l'opzione **Init ()** :

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-3.png)

Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **SceneController**. In Inspector (Controllo) sarà disponibile il componente **SceneController** (script).

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-4.png)

Noterai che sono presenti diversi campi non popolati. Ora puoi modificarli. Sposta l'oggetto **DataManager** da Hierarchy (Gerarchia) nel campo *Data Manager*, quindi sposta GameObject di **RootMenu** da Hierarchy (Gerarchia) nel campo *Main Menu* (Menu principale).

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-5.png)

Ora la scena è pronta per le prossime esercitazioni. Non dimenticare di salvarla nel progetto.

## <a name="prepare-project-build-pipeline"></a>Preparare la pipeline di compilazione del progetto

Anche se nel progetto deve essere ancora inserito il contenuto, devi eseguire alcune operazioni di preparazione, in modo che il progetto sia pronto per la compilazione per **HoloLens 2**.

### <a name="1-add-additional-required-capabilities"></a>1. Aggiungere altre funzionalità necessarie

Dal menu di Unity scegli **Edit** (Modifica) > **Project Settings** (Impostazioni del progetto) per visualizzare la finestra corrispondente:

![mr-learning-azure](images/mr-learning-azure/tutorial1-section7-step1-1.png)

Nella finestra Project Settings (Impostazioni progetto) seleziona **Player** (Lettore) e quindi **Publishing Settings** (Impostazioni di pubblicazione):

![mr-learning-azure](images/mr-learning-azure/tutorial1-section7-step1-2.png)

In **Publishing Settings** (Impostazioni di pubblicazione) scorri verso il basso fino alla sezione **Capabilities** (Funzionalità) e riverifica che siano abilitate le funzionalità **InternetClient**, **Microphone** e **SpatialPerception**, che hai abilitato al momento della creazione del progetto all'inizio dell'esercitazione. Abilita quindi le funzionalità **InternetClientServer**, **PrivateNetworkClientServer** e **Webcam**:

![mr-learning-azure](images/mr-learning-azure/tutorial1-section7-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a>2. Distribuire l'app nel dispositivo HoloLens 2

Non tutte le funzionalità che userai in questa serie di esercitazioni possono essere eseguite nell'editor di Unity. Ciò significa che è necessario avere familiarità con la distribuzione dell'applicazione nel dispositivo HoloLens 2.

> [!TIP]
> Per rileggere come creare e distribuire il progetto Unity in HoloLens 2, puoi fare riferimento alle istruzioni riportate in [Esercitazioni introduttive - Compilare l'applicazione nel dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a>3. Eseguire l'app in HoloLens 2 e seguire le istruzioni in-app

> [!CAUTION]
> Tutti i servizi di Azure usano Internet, quindi assicurati che il dispositivo sia connesso a Internet.

Quando l'applicazione è in esecuzione nel dispositivo, accetta l'accesso alle seguenti funzionalità richieste:

* Microfono
* Fotocamera

Queste funzionalità sono necessarie per il corretto funzionamento di servizi quali *Chat bot* e *Visione personalizzata*.

## <a name="congratulations"></a>Lezione completata

In questa esercitazione è stata presentata la serie di esercitazioni, sono state illustrate le funzionalità che implementerai ed è stato spiegato in che modo interagiscono i servizi **cloud di Azure** per far funzionare la tua applicazione *HoloLens 2*. Hai aggiunto i componenti necessari nel progetto e hai preparato la scena per questa serie di esercitazioni.

Nella lezione successiva userai Archiviazione di Azure come soluzione di persistenza basata sul cloud per archiviare dati e immagini.

[Esercitazione successiva: 2. Integrazione di Archiviazione di Azure](mr-learning-azure-02.md)

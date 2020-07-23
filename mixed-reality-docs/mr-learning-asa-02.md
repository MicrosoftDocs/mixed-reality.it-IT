---
title: Esercitazioni su Ancoraggi nello spazio di Azure - 2. Introduzione ad Ancoraggi nello spazio di Azure
description: Completa questo corso per apprendere come implementare ancoraggi nello spazio di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: a24b6b03ce75a57db49b3d0c875d123ea87c8162
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/14/2020
ms.locfileid: "86305103"
---
# <a name="2-getting-started-with-azure-spatial-anchors"></a>2. Introduzione ad Ancoraggi nello spazio di Azure

## <a name="overview"></a>Panoramica

In questa esercitazione esaminerai i diversi passaggi necessari per avviare e arrestare una sessione di ancoraggi nello spazio di Azure e per creare, caricare e scaricare in un singolo dispositivo gli ancoraggi nello spazio di Azure.

## <a name="objectives"></a>Obiettivi

* Scopri le nozioni fondamentali sullo sviluppo con Ancoraggi nello spazio di Azure per HoloLens 2
* Apprendi come creare ancoraggi nello spazio e recuperarli da Azure

## <a name="creating-and-preparing-the-unity-project"></a>Creazione e preparazione del progetto Unity

In questa sezione creerai un nuovo progetto Unity per prepararti allo sviluppo con MRTK.

A questo scopo, segui prima l'esercitazione [Inizializzazione del progetto e distribuzione della prima applicazione](mr-learning-base-02.md), escluse le istruzioni della sezione [Compilare l'applicazione nel dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2). L'esercitazione include i passaggi seguenti:

1. [Creazione del progetto Unity](mr-learning-base-02.md#creating-the-unity-project) e assegnazione di un nome appropriato, ad esempio *MRTK Tutorials*
1. [Passaggio a un'altra piattaforma di compilazione](mr-learning-base-02.md#configuring-the-unity-project)
1. [Importazione delle risorse essenziali TextMeshPro](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
1. [Importazione di Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
1. [Configurazione del progetto Unity](mr-learning-base-02.md#configuring-the-unity-project)
1. [Creazione e configurazione della scena](mr-learning-base-02.md#creating-and-configuring-the-scene) e assegnazione di un nome appropriato, ad esempio *AzureSpatialAnchors*

Segui quindi le istruzioni riportate in [Modifica delle opzioni di visualizzazione di consapevolezza spaziale](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) per:

1. Modificare l'impostazione di **MRTK configuration profile** (Profilo di configurazione di MRTK) configurando **DefaultHoloLens2ConfigurationProfile**
1. Modificare le **opzioni di visualizzazione mesh di consapevolezza spaziale** impostando **Occlusion** (Occlusione).

## <a name="installing-inbuilt-unity-packages"></a>Installazione di pacchetti di Unity incorporati

Scegli **Window (Finestra)**  > **Package Manager (Gestione pacchetti)** dal menu Unity per aprire la finestra Package Manager(Gestione pacchetti), quindi seleziona **AR Foundation** e fai clic sul pulsante **Install** (Installa) per installare il pacchetto:

![mr-learning-asa](images/mr-learning-asa/asa-02-section2-step1-1.png)

> [!NOTE]
> Stai installando il pacchetto AR Foundation perché è richiesto da Azure Spatial Anchors SDK, che verrà importato nella sezione successiva.

## <a name="importing-the-tutorial-assets"></a>Importazione degli asset dell'esercitazione

Scarica e **importa** i pacchetti personalizzati di Unity seguenti, **nell'ordine in cui sono elencati**:

* [AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage) (versione 2.2.1)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage)

Dopo l'importazione degli asset dell'esercitazione, la finestra Project (Progetto) avrà un aspetto simile al seguente:

![mr-learning-asa](images/mr-learning-asa/asa-02-section3-step1-1.png)

> [!TIP]
> Per rivedere la procedura di importazione di un pacchetto personalizzato di Unity, puoi fare riferimento alle istruzioni contenute in [Importazione di Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit).

## <a name="preparing-the-scene"></a>Preparazione della scena

In questa sezione preparerai la scena aggiungendo alcuni dei prefab dell'esercitazione.

Nella finestra Project (Progetto) passa ad **Assets (Asset)**  > **MRTK.Tutorials.AzureSpeechServices** > **Prefabs** (Prefab) e quindi fai clic e trascina i prefab seguenti sulla finestra Hierarchy (Gerarchia) per aggiungerli alla scena:

* Prefab **ButtonParent**
* Prefab **DebugWindow**
* Prefab **Instructions**
* Prefab **ParentAnchor**

![mr-learning-asa](images/mr-learning-asa/asa-02-section4-step1-1.png)

> [!TIP]
> Se trovi che le icone grandi nella scena, come quelle a forma di "T", siano motivo di distrazione, puoi nasconderle <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">disattivando il menu Gizmos</a>, come mostrato nell'immagine precedente.

## <a name="configuring-the-buttons-to-operate-the-scene"></a>Configurazione dei pulsanti per il funzionamento della scena

In questa sezione aggiungerai script alla scena per creare una serie di eventi Button che illustrano le nozioni fondamentali sul comportamento degli ancoraggi locali e degli ancoraggi nello spazio di Azure in un'app.

Nella finestra Hierarchy (Gerarchia) espandi l'oggetto **ButtonParent** e seleziona il primo oggetto figlio denominato **StartAzureSession**. Nella finestra Inspector (Controllo) configura l'evento **On Click ()** (Al clic) del componente **Button Config Helper (Script)** (Helper configurazione pulsanti - script) come indicato di seguito:

* Assegna l'oggetto **ParentAnchor** al campo **None (Object)** (Nessuno - Oggetto)
* Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **AnchorModuleScript** > **StartAzureSession ()** per impostare questa funzione come l'azione da eseguire quando viene attivato l'evento

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-1.png)

Nella finestra Hierarchy (Gerarchia) seleziona il pulsante successivo denominato **StopAzureSession** e quindi nella finestra Inspector (Controllo) configura l'evento **On Click ()** (Al clic) del componente **Button Config Helper (Script)** (Helper configurazione pulsanti - script) come indicato di seguito:

* Assegna l'oggetto **ParentAnchor** al campo **None (Object)** (Nessuno - Oggetto)
* Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **AnchorModuleScript** > **StopAzureSession ()** per impostare questa funzione come l'azione da eseguire quando viene attivato l'evento

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-2.png)

Nella finestra Hierarchy (Gerarchia) seleziona il pulsante successivo denominato **CreateAzureAnchor** e quindi nella finestra Inspector (Controllo) configura l'evento **On Click ()** (Al clic) del componente **Button Config Helper (Script)** (Helper configurazione pulsanti - script) come indicato di seguito:

* Assegna l'oggetto **ParentAnchor** al campo **None (Object)** (Nessuno - Oggetto)
* Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **AnchorModuleScript** > **CreateAzureAnchor ()** per impostare questa funzione come l'azione da eseguire quando viene attivato l'evento
* Assegna l'oggetto **ParentAnchor** al campo **None (Game Object)** (Nessuno - Oggetto gioco) vuoto per impostarlo come argomento della funzione CreateAzureAnchor ()

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-3.png)

Nella finestra Hierarchy (Gerarchia) seleziona il pulsante successivo denominato **RemoveLocalAnchor** e quindi nella finestra Inspector (Controllo) configura l'evento **On Click ()** (Al clic) del componente **Button Config Helper (Script)** (Helper configurazione pulsanti - script) come indicato di seguito:

* Assegna l'oggetto **ParentAnchor** al campo **None (Object)** (Nessuno - Oggetto)
* Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **AnchorModuleScript** > **RemoveLocalAnchor ()** per impostare questa funzione come l'azione da eseguire quando viene attivato l'evento
* Assegna l'oggetto **ParentAnchor** al campo vuoto **None (Game Object)** (Nessuno - Oggetto gioco) per impostarlo come argomento della funzione RemoveLocalAnchor ()

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-4.png)

Nella finestra Hierarchy (Gerarchia) seleziona il pulsante successivo denominato **FindAzureAnchor** e quindi nella finestra Inspector (Controllo) configura l'evento **On Click ()** (Al clic) del componente **Button Config Helper (Script)** (Helper configurazione pulsanti - script) come indicato di seguito:

* Assegna l'oggetto **ParentAnchor** al campo **None (Object)** (Nessuno - Oggetto)
* Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **AnchorModuleScript** > **FindAzureAnchor ()** per impostare questa funzione come l'azione da eseguire quando viene attivato l'evento

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-5.png)

Nella finestra Hierarchy (Gerarchia) seleziona il pulsante successivo denominato **DeleteAzureAnchor** e quindi nella finestra Inspector (Controllo) configura l'evento **On Click ()** (Al clic) del componente **Button Config Helper (Script)** (Helper configurazione pulsanti - script) come indicato di seguito:

* Assegna l'oggetto **ParentAnchor** al campo **None (Object)** (Nessuno - Oggetto)
* Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **AnchorModuleScript** > **DeleteAzureAnchor ()** per impostare questa funzione come l'azione da eseguire quando viene attivato l'evento

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-6.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a>Connessione della scena alla risorsa di Azure

Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **ParentAnchor** e quindi nella finestra Inspector (Controllo) individua il componente **Spatial Anchor Manager (Script)** (Gestione ancoraggi nello spazio - script). Configura la sezione **Credentials** (Credenziali) con le credenziali dell'account di ancoraggi nello spazio di Azure creato in fase di definizione dei [Prerequisiti](mr-learning-asa-01.md#prerequisites) per questa serie di esercitazioni:

* Nel campo **Spatial Anchors Account ID** (ID account Ancoraggi nello spazio) incolla il valore di **Account ID** (ID account) del tuo account di Ancoraggi nello spazio di Azure
* Nel campo **Spatial Anchors Account Key** (Chiave account Ancoraggi nello spazio) incolla il valore di **Access Key** (Chiave di accesso) primario o secondario del tuo account di Ancoraggi nello spazio di Azure

![mr-learning-asa](images/mr-learning-asa/asa-02-section6-step1-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a>Test dei comportamenti di base di Ancoraggi nello spazio di Azure

Poiché non è possibile eseguire ancoraggi nello spazio di Azure in Unity, per testare la funzionalità di questo servizio devi compilare il progetto e distribuire l'app nel tuo dispositivo.

> [!TIP]
> Per rivedere la procedura di compilazione e distribuzione di un progetto Unity in HoloLens 2, puoi fare riferimento alle istruzioni riportate in [Compilazione dell'applicazione nel dispositivo HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

Quando l'app è in esecuzione nel dispositivo, segui le istruzioni visualizzate nel pannello Azure Spatial Anchor Tutorial Instructions (Istruzioni per l'esercitazione su ancoraggi nello spazio di Azure):

1. Sposta il cubo in un'altra posizione
1. Avvia la sessione di Azure
1. Crea l'ancoraggio di Azure (viene creato un ancoraggio nella posizione del cubo)
1. Arresta la sessione di Azure
1. Rimuovi l'ancoraggio locale (consente all'utente di spostare il cubo)
1. Sposta il cubo altrove
1. Avvia la sessione di Azure
1. Trova l'ancoraggio di Azure (il cubo viene collocato nella posizione del passaggio 3)
1. Elimina l'ancoraggio di Azure
1. Arresta la sessione di Azure

![mr-learning-asa](images/mr-learning-asa/asa-02-section7-step1-1.png)

> [!CAUTION]
> Poiché per gli ancoraggi nello spazio di Azure viene usato Internet per salvare e caricare i dati di ancoraggio, assicurati che il dispositivo sia connesso a Internet.

## <a name="anchoring-an-experience"></a>Ancoraggio di un'esperienza

Nelle sezioni precedenti hai appreso le nozioni fondamentali di Ancoraggi nello spazio di Azure. È stato usato un cubo per rappresentare e visualizzare l'oggetto gioco padre con l'ancoraggio collegato. In questa sezione apprenderai come ancorare un'intera esperienza inserendola come figlio dell'oggetto ParentAnchor.

Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **ParentAnchor** e quindi nella finestra Inspector (Controllo) configura i componenti **Transform** (Trasformazione) come segue:

* Imposta **Scale X** (Scala X) su 1,1
* Imposta **Scale Z** (Scala Z) su 1,1

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-1.png)

Nella finestra Project (Progetto) passa alla cartella **Assets (Asset)**  > **MRTK.Tutorials.GettingStarted** > **Prefabs (Prefab)**  > **Rover** e quindi fai clic e trascina il prefab **RoverExplorer_Complete** sulla finestra Hierarchy (Gerarchia) per aggiungerlo alla scena:

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-2.png)

Con l'oggetto RoverModule_Complete appena aggiunto ancora selezionato nella finestra Hierarchy (Gerarchia), trascinalo sull'oggetto **ParentAnchor** per configurarlo come figlio dell'oggetto ParentAnchor:

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-3.png)

Se ora ricompili il progetto e distribuisci l'app nel dispositivo, puoi riposizionare l'intera esperienza Rover Explorer (Esplora rover) spostando il cubo ridimensionato.

> [!TIP]
> Sono disponibili diversi flussi di esperienza utente per il riposizionamento, tra cui l'uso di un oggetto di riposizionamento (come il cubo usato in questa esercitazione), l'uso di un pulsante per attivare e disattivare un cubo di delimitazione intorno all'esperienza, l'uso di gizmo di posizione e rotazione e altro ancora.

## <a name="congratulations"></a>Lezione completata

In questa esercitazione hai appreso le nozioni fondamentali di Ancoraggi nello spazio di Azure. In questa esercitazione hai usato diversi pulsanti per esaminare i vari passaggi da seguire per avviare e arrestare una sessione di ancoraggi nello spazio di Azure e per creare, caricare e scaricare gli ancoraggi nello spazio di Azure in un singolo dispositivo.

Nell'esercitazione successiva apprenderai come salvare gli ID di ancoraggio di Azure in HoloLens 2 per il recupero, anche dopo il riavvio dell'app, e come trasferire gli ID di ancoraggio tra più dispositivi per ottenere l'allineamento nello spazio.

[Esercitazione successiva: 3. Salvataggio, recupero e condivisione di Ancoraggi nello spazio di Azure](mr-learning-asa-03.md)

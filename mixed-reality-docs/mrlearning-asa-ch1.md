---
title: Esercitazioni su Ancoraggi nello spazio di Azure - 1. Introduzione ad Ancoraggi nello spazio di Azure
description: Completa questo corso per informazioni su come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: 47063fbf9a1b9f3a43497a0742deba2c16b53d99
ms.sourcegitcommit: 536fd45b48a70bbeca1454cef517ae007225e533
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/27/2020
ms.locfileid: "80362061"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a>1. Introduzione ad Ancoraggi nello spazio di Azure

## <a name="overview"></a>Panoramica

Questa è la seconda serie di esercitazioni su HoloLens 2. In questa serie di esercitazioni, suddivisa in tre parti, apprenderai le nozioni fondamentali su Ancoraggi nello spazio di Azure.

Questa prima esercitazione, [Introduzione ad Ancoraggi nello spazio di Azure](mrlearning-asa-ch1.md), illustra i diversi passaggi da seguire per avviare e arrestare una sessione di Azure e per creare, caricare e scaricare gli ancoraggi di Azure in un singolo dispositivo.

La seconda esercitazione, [Salvataggio, recupero e condivisione di ancoraggi nello spazio di Azure](mrlearning-asa-ch2.md), illustra come salvare gli ancoraggi nello spazio di Azure in più sessioni di app salvando le informazioni sugli ancoraggi nello spazio di archiviazione di HoloLens 2 e come condividere queste informazioni con altri dispositivi per l'allineamento degli ancoraggi su più dispositivi.

La terza esercitazione, [Visualizzazione del feedback su Ancoraggi nello spazio di Azure](mrlearning-asa-ch3.md), illustra come fornire agli utenti feedback sugli eventi e sullo stato degli ancoraggi con Ancoraggi nello spazio di Azure.

## <a name="objectives"></a>Obiettivi

* Scopri le nozioni fondamentali sullo sviluppo con Ancoraggi nello spazio di Azure per HoloLens 2
* Creare, caricare e scaricare ancoraggi nello spazio

## <a name="prerequisites"></a>Prerequisiti

>[!TIP]
>Se non hai ancora completato la serie di [Esercitazioni introduttive](mrlearning-base.md), è consigliabile completare prima queste esercitazioni.

* Un PC Windows 10 configurato in cui siano [installati gli strumenti](install-the-tools.md) corretti
* Windows 10 SDK 10.0.18362.0 o versioni successive
* Alcune funzionalità di programmazione C# di base
* Un dispositivo HoloLens 2 [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode)
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.2.X installato e il modulo di supporto delle compilazioni UWP (Universal Windows Platform) aggiunto
* Completa la sezione [Creare una risorsa di Ancoraggi nello spazio](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) dell'esercitazione [Avvio rapido: Creare un'app HoloLens in Unity che usa Ancoraggi nello spazio di Azure](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens).

> [!IMPORTANT]
> La versione di Unity consigliata per questa serie di esercitazioni è Unity 2019.2.X. Questa istruzione sostituisce gli eventuali requisiti o suggerimenti relativi alla versione di Unity indicati negli argomenti visualizzabili facendo clic sui collegamenti dei prerequisiti sopra riportati.

## <a name="creating-the-unity-project"></a>Creazione del progetto Unity
<!-- TODO: Consider renaming to 'Creating and preparing the Unity project'-->

In questa sezione creerai un nuovo progetto Unity per prepararti allo sviluppo con MRTK.

A questo scopo, segui prima l'esercitazione [Inizializzazione del progetto e prima applicazione](mrlearning-base-ch1.md), escluse le istruzioni della sezione [Compilare l'applicazione nel dispositivo](mrlearning-base-ch1.md#build-your-application-to-your-device), che include i passaggi seguenti:

1. [Creare un nuovo progetto Unity](mrlearning-base-ch1.md#create-new-unity-project) e assegnargli un nome appropriato, ad esempio *MRTK Tutorials*

2. [Configurare il progetto Unity per Windows Mixed Reality](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [Importare le risorse essenziali TextMesh Pro](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [Importare Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [Configurare il progetto Unity per Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. [Aggiungere Mixed Reality Toolkit alla scena di Unity](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) e assegnare alla scena un nome appropriato, ad esempio *AzureSpatialAnchors*

Segui quindi le istruzioni riportate in [Come configurare i profili di Mixed Reality Toolkit (modifica dell'opzione di visualizzazione della mesh di consapevolezza spaziale)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) per impostare **DefaultHoloLens2ConfigurationProfile** come profilo di configurazione MRTK per la scena e modificare in **Occlusion** (Occlusione) le opzioni di visualizzazione per la mesh di consapevolezza spaziale.

> [!CAUTION]
> Come indicato nelle istruzioni contenute in [Configurare il progetto Unity per Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit), è fortemente sconsigliabile abilitare MSBuild per Unity.

## <a name="adding-inbuilt-unity-packages"></a>Aggiunta di pacchetti di Unity incorporati
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

In questa sezione installerai il pacchetto AR Foundation incorporato di Unity perché è un prerequisito dell'SDK di Ancoraggi nello spazio di Azure che importerai nella sezione successiva.

Nel menu di Unity seleziona **Window** (Finestra) > **Package Manager** (Gestione pacchetti):

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-1.png)

> [!NOTE]
> Potrebbero essere necessari alcuni secondi prima che il pacchetto AR Foundation venga visualizzato nell'elenco.

Nella finestra Package Manager (Gestione pacchetti) seleziona **AR Foundation** e installa il pacchetto facendo clic sul pulsante **Install** (Installa):

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-2.png)

## <a name="importing-the-tutorial-assets"></a>Importazione degli asset dell'esercitazione

Scarica e **importa** i pacchetti personalizzati di Unity seguenti, **nell'ordine in cui sono elencati**:

* [AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (versione 2.1.1)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage)

> [!TIP]
> Per rivedere la procedura di importazione di un pacchetto personalizzato di Unity, puoi fare riferimento alle istruzioni contenute in [Importare Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).

Dopo l'importazione degli asset dell'esercitazione, la finestra Project (Progetto) avrà un aspetto simile al seguente:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section3-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a>Creazione e preparazione della scena
<!-- TODO: Consider renaming to 'Preparing the scene' -->

In questa sezione preparerai la scena aggiungendo alcuni dei prefab dell'esercitazione.

Nella finestra Project (Progetto) passa alla cartella **Assets** (Asset) > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** (Prefab). Tenendo premuto CTRL, fai clic su **ButtonParent**, **DebugWindow**, **Instructions** e **ParentAnchor** per selezionare i quattro prefab:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-1.png)

Trascina i quattro prefab selezionati nella finestra Hierarchy (Gerarchia) per aggiungerli alla scena:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-2.png)

Per concentrarti sugli oggetti nella scena, puoi fare doppio clic sull'oggetto ParentAnchor e quindi fare di nuovo leggermente zoom indietro:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-3.png)

> [!TIP]
> Se trovi che le icone grandi nella scena, come quelle a forma di "T", siano motivo di distrazione, puoi nasconderle <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">disattivando i gizmo</a>.

## <a name="configuring-the-buttons-to-operate-the-scene"></a>Configurazione dei pulsanti per il funzionamento della scena

In questa sezione aggiungerai script alla scena per creare una serie di eventi Button che illustrano le nozioni fondamentali sul comportamento degli ancoraggi locali e di Ancoraggi nello spazio di Azure in un'applicazione.

### <a name="1-configure-the-pressable-button-holo-lens-2-script-component"></a>1. Configurare il componente Pressable Button Holo Lens 2 (Script)

Nella finestra Hierarchy (Gerarchia) espandi l'oggetto **ButtonParent** e seleziona il primo oggetto figlio denominato **StartAzureSession**:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-1.png)

Nella finestra Inspector (Controllo) individua il componente **Pressable Button Holo Lens 2 (Script)** e aggiungi un nuovo listener di eventi all'evento **Button Pressed ()** facendo clic sull'icona **+** :

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-2.png)

Con l'oggetto StartAzureSession ancora selezionato nella finestra Hierarchy (Gerarchia), fai clic e trascina l'oggetto **ParentAnchor** dalla finestra Hierarchy (Gerarchia) nel campo vuoto **None (Object)** (Nessuno - Oggetto) del listener di eventi appena aggiunto per fare in modo che l'oggetto ParentAnchor rimanga in ascolto degli eventi di pressione attivati da questo pulsante:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-3.png)

Fai clic sull'elenco a discesa **No Function** (Nessuna funzione) dello stesso listener di eventi e quindi seleziona **AnchorModuleScript** > **StartAzureSession ()** per impostare la funzione StartAzureSession () come azione da eseguire quando vengono attivati eventi di pressione da questo pulsante:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-4.png)

### <a name="2-configure-the-interactable-script-component"></a>2. Configurare il componente Interactable (Script)

Con l'oggetto StartAzureSession ancora selezionato nella finestra Hierarchy (Gerarchia), nella finestra Inspector (Controllo) individua il componente **Interactable (script)** e ripeti la stessa procedura descritta nel passaggio 1 per l'evento **OnClick ()** :

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step2-1.png)

### <a name="3-configure-the-remaining-buttons"></a>3. Configurare i pulsanti rimanenti

Per ognuno dei pulsanti rimanenti, completa il processo descritto nei passaggi 1 e 2 precedenti per assegnare funzioni a entrambi gli eventi **Button Pressed ()** e **OnClick ()** :

* Per l'oggetto **StopAzureSession**, assegna la funzione AnchorModuleScript > **StopAzureSession ()** .
* Per l'oggetto **CreateAzureAnchor**, assegna la funzione AnchorModuleScript > **CreateAzureAnchor ()** ,
  * quindi trascina di nuovo **ParentAnchor** nel campo vuoto **None (Game Object)** (Nessuno - Oggetto gioco).
* Per l'oggetto **RemoveLocalAnchor**, assegna la funzione AnchorModuleScript > **RemoveLocalAnchor ()** ,
  * quindi trascina di nuovo **ParentAnchor** nel campo vuoto **None (Game Object)** (Nessuno - Oggetto gioco).
* Per l'oggetto **FindAzureAnchor**, assegna la funzione AnchorModuleScript > **FindAzureAnchor ()** .
* Per l'oggetto **DeleteAzureAnchor**, assegna la funzione AnchorModuleScript > **DeleteAzureAnchor ()** .

### <a name="4-connect-the-scene-to-the-azure-resource"></a>4. Connettere la scena alla risorsa di Azure

Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **ParentAnchor** e nella finestra Inspector (Controllo) scorri verso il basso fino al componente **Spatial Anchor Manager (Script)** .

Nella sezione **Credentials** (Credenziali) incolla l'ID e la chiave dell'account di Ancoraggi nello spazio, che hai creato come parte dei [prerequisiti](mrlearning-asa-ch1.md#prerequisites) di questa esercitazione, nei corrispondenti campi **Spatial Anchors Account Id** (ID account Ancoraggi nello spazio) e **Spatial Anchors Account Key** (Chiave account Ancoraggi nello spazio):

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step4-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a>Test dei comportamenti di base di Ancoraggi nello spazio di Azure

Ora che la scena è configurata in modo da illustrare gli elementi di base di Ancoraggi nello spazio di Azure, è il momento di distribuire l'app per poter provare Ancoraggi nello spazio di Azure in prima persona.

### <a name="1-add-additional-required-capabilities"></a>1. Aggiungere altre funzionalità necessarie

Dal menu di Unity scegli **Edit** (Modifica) > **Project Settings** (Impostazioni del progetto) per visualizzare la finestra corrispondente:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-1.png)

Nella finestra Project Settings (Impostazioni del progetto) seleziona **Player** (Lettore) e quindi **Publishing Settings** (Impostazioni di pubblicazione):

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-2.png)

In **Publishing Settings** (Impostazioni di pubblicazione) scorri verso il basso fino alla sezione **Capabilities** (Funzionalità) e verifica che siano abilitate le funzionalità **InternetClient**, **Microphone** e **SpatialPerception**, che hai abilitato al momento della creazione del progetto all'inizio dell'esercitazione. Abilita quindi le funzionalità **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage** e **Webcam**:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a>2. Distribuire l'app nel dispositivo HoloLens 2

Non è possibile eseguire Ancoraggi nello spazio di Azure in Unity. Pertanto, per testare la funzionalità di questo servizio devi distribuire il progetto nel tuo dispositivo.

> [!TIP]
> Per un promemoria su come compilare e distribuire il progetto Unity in HoloLens 2, puoi fare riferimento alle istruzioni riportate in [Compilare l'applicazione nel dispositivo](mrlearning-base-ch1.md#build-your-application-to-your-device).

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a>3. Eseguire l'app in HoloLens 2 e seguire le istruzioni in-app

> [!CAUTION]
> Ancoraggi nello spazio di Azure usa Internet per salvare e caricare i dati di ancoraggio. Assicurati quindi che il dispositivo sia connesso a Internet.

Quando l'applicazione è in esecuzione nel dispositivo, segui le istruzioni visualizzate nel pannello Azure Spatial Anchor Tutorial Instructions (Istruzioni per l'esercitazione su Ancoraggi nello spazio di Azure):

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step3-1.png)

## <a name="anchoring-an-experience"></a>Ancoraggio di un'esperienza

Nelle sezioni precedenti hai appreso le nozioni fondamentali di Ancoraggi nello spazio di Azure. È stato usato un cubo per rappresentare e visualizzare l'oggetto gioco padre con l'ancoraggio collegato. In questa sezione apprenderai come ancorare un'intera esperienza inserendola come figlio dell'oggetto ParentAnchor.

### <a name="1-add-the-rocket-launcher-experience"></a>1. Aggiungere l'esperienza di Rocket Launcher

Nella finestra Project (Progetto) passa alla cartella **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** e seleziona il prefab **RocketLauncher_Complete**:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-1.png)

Trascina il prefab RocketLauncher_Complete selezionato sopra l'oggetto **ParentAnchor** nella finestra Hierarchy (Gerarchia) per configurarlo come figlio dell'oggetto ParentAnchor:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-2.png)

### <a name="2-reposition-the-rocket-launcher-experience"></a>2. Riposizionare l'esperienza di Rocket Launcher

Posiziona, ruota e ridimensiona l'oggetto **RocketLauncher_Complete** in base a un fattore di scala e a un orientamento appropriati, assicurando allo stesso tempo che l'oggetto **ParentAnchor** rimanga esposto, ad esempio:

* Trasforma la **posizione** X = 0, Y = -0, Z = 3.75
* Trasforma la **rotazione** X = 0, Y = 90, Z = 0
* Trasforma la **scala** X = 10, Y = 10, Z = 10

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step2-1.png)

Nell'applicazione, gli utenti possono ora riposizionare l'intera esperienza di Rocket Launcher spostando il cubo.

> [!TIP]
> Sono disponibili diversi flussi di esperienza utente per il riposizionamento, tra cui l'uso di un oggetto di riposizionamento (come il cubo usato in questa esercitazione), l'uso di un pulsante per attivare e disattivare un cubo di delimitazione attorno all'esperienza, l'uso di gizmo di posizione e rotazione e altro ancora.

## <a name="congratulations"></a>Lezione completata

In questa esercitazione hai appreso le nozioni fondamentali di Ancoraggi nello spazio di Azure. L'esercitazione ha consentito di esaminare i diversi passaggi da seguire per avviare e arrestare una sessione di Ancoraggi nello spazio di Azure e per creare, caricare e scaricare gli ancoraggi nello spazio di Azure in un singolo dispositivo.

Nella lezione successiva apprenderai come salvare gli ID di ancoraggio di Azure in HoloLens 2 per il recupero, anche dopo il riavvio dell'applicazione, e come trasferire gli ID di ancoraggio tra più dispositivi per ottenere l'allineamento nello spazio.

[Lezione successiva: 2. Salvataggio, recupero e condivisione di Ancoraggi nello spazio di Azure](mrlearning-asa-ch2.md)

---
title: Esercitazioni sugli ancoraggi spaziali di Azure-1. Introduzione agli ancoraggi spaziali di Azure
description: Completa questo corso per informazioni su come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 0163b61bfbf8bd583532092581d94f63e1c2a624
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2020
ms.locfileid: "77554680"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a>1. Introduzione agli ancoraggi spaziali di Azure

## <a name="overview"></a>Panoramica

Benvenuti alla seconda serie di esercitazioni su HoloLens 2. In questa serie di esercitazioni in tre parti si apprenderanno le nozioni di base degli ancoraggi spaziali di Azure.

Questa prima esercitazione illustra i diversi passaggi necessari per avviare e arrestare una sessione di Azure e creare, caricare e scaricare i punti [di ancoraggio di](mrlearning-asa-ch1.md)Azure in un singolo dispositivo.

Nella seconda esercitazione, salvare [, recuperare e condividere gli ancoraggi spaziali di Azure](mrlearning-asa-ch2.md), si apprenderà come salvare gli ancoraggi spaziali di Azure tra più sessioni di App salvando le informazioni di ancoraggio nell'archiviazione di HoloLens 2 e come condividere le informazioni di ancoraggio ad altri dispositivi per un allineamento di ancoraggio a più dispositivi.

Nella terza esercitazione, in cui viene [visualizzato il feedback di ancoraggio spaziale di Azure](mrlearning-asa-ch3.md), si apprenderà come fornire agli utenti feedback sugli eventi e gli Stati di ancoraggio quando si usano gli ancoraggi spaziali di Azure.

## <a name="objectives"></a>Obiettivi

* Scopri le nozioni di base sullo sviluppo con gli ancoraggi spaziali di Azure per HoloLens 2
* Creare, caricare e scaricare ancoraggi spaziali

## <a name="prerequisites"></a>Prerequisiti

>[!TIP]
>Se non è ancora stata completata la serie di [esercitazioni introduttive](mrlearning-base.md) , è consigliabile completare prima queste esercitazioni.

* Un PC Windows 10 configurato in cui siano [installati gli strumenti](install-the-tools.md) corretti
* Windows 10 SDK 10.0.18362.0 o versioni successive
* Alcune funzionalità di programmazione C# di base
* Un dispositivo HoloLens 2 [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode)
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.2.X installato e il modulo di supporto delle compilazioni UWP (Universal Windows Platform) aggiunto
* Completare la sezione [creare una risorsa ancoraggi spaziali](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) della [Guida introduttiva: creare un'app HoloLens Unity che usa l'esercitazione sugli ancoraggi spaziali di Azure](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) .

> [!IMPORTANT]
> La versione di Unity consigliata per questa serie di esercitazioni è Unity 2019.2.X. Questa istruzione sostituisce gli eventuali requisiti o suggerimenti relativi alla versione di Unity indicati negli argomenti visualizzabili facendo clic sui collegamenti dei prerequisiti sopra riportati.

## <a name="creating-the-unity-project"></a>Creazione del progetto Unity
<!-- TODO: Consider renaming to 'Creating and preparing the Unity scene and project'-->

In questa sezione si creerà un nuovo progetto Unity per prepararsi allo sviluppo MRTK.

A questo proposito, seguire prima l' [inizializzazione del progetto e della prima applicazione](mrlearning-base-ch1.md), escluse le istruzioni [per la compilazione dell'applicazione nel dispositivo](mrlearning-base-ch1.md#build-your-application-to-your-device) , che include i passaggi seguenti:

1. [Creare un nuovo progetto Unity](mrlearning-base-ch1.md#create-new-unity-project) e assegnargli un nome appropriato, ad esempio le *esercitazioni di MRTK*.

2. [Configurare il progetto Unity per la realtà mista di Windows](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [Importare risorse essenziali di TextMesh Pro](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [Importare il Toolkit di realtà mista](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [Configurare il progetto Unity per il Toolkit di realtà mista](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. [Aggiungere il Toolkit di realtà mista alla scena Unity](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) e assegnare alla scena un nome appropriato, ad esempio *AzureSpatialAnchors*

Seguire quindi le istruzioni [come configurare i profili del Toolkit di realtà mista (modificare l'opzione di visualizzazione di riconoscimento spaziale)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) per modificare il profilo di configurazione MRTK per la scena in **DefaultHoloLens2ConfigurationProfile** e modificare le opzioni di visualizzazione per la mesh di riconoscimento spaziale in **occlusione**.

> [!CAUTION]
> Come indicato nella pagina [relativa alla configurazione del progetto Unity per le istruzioni del Toolkit di realtà mista](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) collegate in precedenza, è consigliabile non abilitare MSBuild per Unity.

## <a name="adding-inbuilt-unity-packages"></a>Aggiunta di pacchetti Unity incorporati
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

In questa sezione verrà installato il pacchetto AR Foundation incorporato di Unity perché è richiesto dall'SDK di Azure Spatial Anchors che verrà importato nella sezione successiva.

Nel menu Unity selezionare **Window** > **Package Manager**:

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section2-step1-1.png)

> [!NOTE]
> Potrebbero essere necessari alcuni secondi prima che il pacchetto AR Foundation venga visualizzato nell'elenco.

Nella finestra Gestione pacchetti selezionare **AR Foundation** e installare il pacchetto facendo clic sul pulsante **Install (installa** ):

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section2-step1-2.png)

## <a name="importing-the-tutorial-assets"></a>Importazione delle risorse dell'esercitazione

Scaricare e **importare** i pacchetti personalizzati di Unity seguenti **nell'ordine in cui sono elencati**:

* [AzureSpatialAnchors. file unitypackage Tools](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (versione 2.1.1)
* [MRTK. HoloLens2. Unity. Esercitations. assets. GettingStarted. 2.3.0.2. file unitypackage Tools](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)
* [MRTK. HoloLens2. Unity. Esercitations. assets. AzureSpatialAnchors. 2.3.0.0. file unitypackage Tools](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage)

> [!TIP]
> Per un promemoria su come importare un pacchetto personalizzato Unity, è possibile fare riferimento alle istruzioni [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) .

Dopo aver importato le risorse dell'esercitazione, la finestra del progetto avrà un aspetto simile al seguente:

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section3-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a>Creazione e preparazione della scena
<!-- TODO: Consider renaming to 'Preparing the scene' -->

In questa sezione verrà preparata la scena aggiungendo alcune delle prefabbricate dell'esercitazione.

Nella finestra del progetto passare a **assets** > **MRTK. Tutorials. AzureSpatialAnchors** > cartella **prefabbricates** . Tenendo premuto il pulsante CTRL, fare clic su **ButtonParent**, **DebugWindow**, **instructions**e **ParentAnchor** per selezionare i quattro prefabbricati:

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section4-step1-1.png)

Con le quattro prefabbricate ancora selezionate, trascinarle nella finestra della gerarchia per aggiungerle alla scena:

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section4-step1-2.png)

Per concentrarsi sugli oggetti nella scena, è possibile fare doppio clic sull'oggetto ParentAnchor e quindi eseguire di nuovo lo zoom indietro:

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section4-step1-3.png)

> [!TIP]
> Se si trovano le icone grandi nella scena, ad esempio, le icone con frame ' t'di grandi dimensioni, è possibile nasconderle impostando <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">i gizmo</a> sulla posizione OFF.

## <a name="configuring-the-buttons-to-operate-the-scene"></a>Configurazione dei pulsanti per il funzionamento della scena

In questa sezione si aggiungeranno script alla scena per creare una serie di eventi Button che dimostrano le nozioni di base del comportamento di entrambi gli ancoraggi locali e degli ancoraggi spaziali di Azure in un'applicazione.

### <a name="1-configure-the-pressable-button-holo-lens-2-script-component"></a>1. configurare il componente (script) del pulsante stampabile di Holo Lens 2 (script)

Nella finestra gerarchia espandere l'oggetto **ButtonParent** e selezionare il primo oggetto figlio denominato **StartAzureSession**:

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section5-step1-1.png)

Nella finestra di controllo individuare il componente **Button (script) di Holo Lens 2 (script)** e aggiungere un nuovo listener di eventi all'evento **Pressed () del pulsante** facendo clic sull'icona **+** :

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section5-step1-2.png)

Con l'oggetto StartAzureSession ancora selezionato nella finestra gerarchia, fare clic e trascinare l'oggetto **ParentAnchor** dalla finestra gerarchia nel campo vuoto **None (oggetto)** del listener di eventi appena aggiunto per fare in modo che l'oggetto ParentAnchor attenda gli eventi di pressione del pulsante da questo pulsante:

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section5-step1-3.png)

Fare clic sull'elenco a discesa **Nessuna funzione** dello stesso listener di eventi, quindi selezionare **AnchorModuleScript** > **StartAzureSession ()** per impostare la funzione StartAzureSession () come azione attivata quando viene attivato il pulsante eventi premuti da questo pulsante:

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section5-step1-4.png)

### <a name="2-configure-the-interactable-script-component"></a>2. configurare il componente interactable (script)

Con l'oggetto StartAzureSession ancora selezionato nella finestra gerarchia, nella finestra di controllo individuare il componente **interactable (script)** e ripetere lo stesso processo descritto nel passaggio 1 per l'evento **OnClick ()** :

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section5-step2-1.png)

### <a name="3-configure-the-remaining-buttons"></a>3. configurare i pulsanti rimanenti

Per ognuno dei pulsanti rimanenti, completare il processo descritto nel passaggio 1 e 2 precedente per assegnare funzioni agli eventi di pressione del **pulsante ()** e **OnClick ()** :

* Per l'oggetto **StopAzureSession** , assegnare la funzione AnchorModuleScript > **StopAzureSession ()** .
* Per l'oggetto **CreateAzureAnchor** , assegnare la funzione AnchorModuleScript > **CreateAzureAnchor ()**
  * quindi trascinare nuovamente il **ParentAnchor** nel campo vuoto **None (oggetto gioco)** .
* Per l'oggetto **RemoveLocalAnchor** , assegnare la funzione AnchorModuleScript > **RemoveLocalAnchor ()**
  * quindi trascinare nuovamente il **ParentAnchor** nel campo vuoto **None (oggetto gioco)** .
* Per l'oggetto **FindAzureAnchor** , assegnare la funzione AnchorModuleScript > **FindAzureAnchor ()** .
* Per l'oggetto **DeleteAzureAnchor** , assegnare la funzione AnchorModuleScript > **DeleteAzureAnchor ()** .

### <a name="4-connect-the-scene-to-the-azure-resource"></a>4. Connettere la scena alla risorsa di Azure

Nella finestra gerarchia selezionare l'oggetto **ParentAnchor** e nella finestra di controllo scorrere verso il basso fino al componente **Spatial Anchor Manager (script)** .

Quindi, nella sezione **Credentials (credenziali** ) incollare l'ID e la chiave dell'account di ancoraggio spaziali, che è stato creato come parte dei [prerequisiti](mrlearning-asa-ch1.md#prerequisites)di questa esercitazione, nei campi dell'ID dell'account di ancoraggio **spaziale** e nei campi **chiave dell'account** degli ancoraggi spaziali corrispondenti:

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section5-step4-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a>Provare i comportamenti di base degli ancoraggi spaziali di Azure

Ora che la scena è configurata in modo da illustrare gli elementi di base degli ancoraggi spaziali di Azure, è necessario distribuire l'app per poter provare i Anchor spaziali di Azure in prima persona.

### <a name="1-add-additional-required-capabilities"></a>1. aggiungere altre funzionalità necessarie

Nel menu Unity selezionare **modifica** > **Impostazioni progetto...** per aprire la finestra Impostazioni lettore:

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section6-step1-1.png)

Nella finestra Impostazioni lettore selezionare **Player** e quindi impostazioni di **pubblicazione**:

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section6-step1-2.png)

Nelle **impostazioni di pubblicazione**scorrere verso il basso fino alla sezione **funzionalità** e verificare che le funzionalità **internetClient**, **Microphone**e **SpatialPerception** , abilitate al momento della creazione del progetto all'inizio dell'esercitazione, siano abilitate. Abilitare quindi le funzionalità **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage**e **Webcam** :

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section6-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a>2. distribuire l'app in HoloLens 2

Gli ancoraggi spaziali di Azure non possono essere eseguiti in Unity, quindi per testare la funzionalità degli ancoraggi spaziali di Azure è necessario distribuire il progetto nel dispositivo.

> [!TIP]
> Per un promemoria su come compilare e distribuire il progetto Unity in HoloLens 2, è possibile fare riferimento alle istruzioni per la [compilazione dell'applicazione per il dispositivo](mrlearning-base-ch1.md#build-your-application-to-your-device) .

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a>3. eseguire l'app in HoloLens 2 e seguire le istruzioni in-app

> [!CAUTION]
> Gli ancoraggi spaziali di Azure usano Internet per salvare e caricare i dati di ancoraggio, quindi assicurarsi che il dispositivo sia connesso a Internet.

Quando l'applicazione è in esecuzione nel dispositivo, seguire le istruzioni sullo schermo visualizzate nel pannello istruzioni dell'esercitazione sull'ancoraggio spaziale di Azure:

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section6-step3-1.png)

## <a name="anchoring-an-experience"></a>Ancoraggio di un'esperienza

Nelle sezioni precedenti sono state apprese le nozioni di base degli ancoraggi spaziali di Azure. È stato usato un cubo per rappresentare e visualizzare l'oggetto del gioco padre con l'ancoraggio collegato. In questa sezione si apprenderà come ancorare un'intera esperienza inserendola come figlio dell'oggetto ParentAnchor.

### <a name="1-add-the-rocket-launcher-experience"></a>1. aggiungere l'esperienza di avvio Rocket

Nella finestra del progetto passare al **asset** > **MRTK. Tutorials. GettingStarted** > **prefabbricati** > cartella **RocketLauncher** e selezionare il **RocketLauncher_Complete** prefabbricato:

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section7-step1-1.png)

Con il RocketLauncher_Complete prefabbricato ancora selezionato, trascinarlo sopra l'oggetto **ParentAnchor** nella finestra gerarchia per impostarlo come figlio dell'oggetto ParentAnchor:

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section7-step1-2.png)

### <a name="2-reposition-the-rocket-launcher-experience"></a>2. Riposizionare l'esperienza di avvio Rocket

Posizionare, ruotare e ridimensionare l'oggetto **RocketLauncher_Complete** a una scala e un orientamento appropriati, assicurando allo stesso tempo che l'oggetto **ParentAnchor** sia ancora esposto, ad esempio:

* **Posizione** di trasformazione X = 0, Y = 0, Z = 3,75
* **Rotazione** trasformazione X = 0, Y = 90, Z = 0
* Trasforma **scala** X = 10, Y = 10, Z = 10

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section7-step2-1.png)

Nell'applicazione, gli utenti possono ora riposizionare l'intera esperienza di avvio del lanciarazzi spostando il cubo.

> [!TIP]
> Sono disponibili diversi flussi di esperienza utente per il riposizionamento, incluso l'uso di un oggetto di riposizionamento (ad esempio il cubo usato in questa esercitazione), l'uso di un pulsante per alternare un rettangolo di selezione che racchiude l'esperienza, l'uso della posizione e della rotazione Gizmo e altro ancora.

## <a name="congratulations"></a>Complimenti

In questa esercitazione sono state apprese le nozioni di base degli ancoraggi spaziali di Azure. L'esercitazione ha fornito diversi pulsanti che consentono di esaminare i diversi passaggi necessari per avviare e arrestare una sessione di ancoraggi spaziali di Azure e creare, caricare e scaricare gli ancoraggi spaziali di Azure in un singolo dispositivo.

Nella lezione successiva si apprenderà come salvare gli ID di ancoraggio di Azure in HoloLens 2 per il recupero, anche dopo il riavvio dell'applicazione e come trasferire gli ID di ancoraggio tra più dispositivi per ottenere l'allineamento spaziale.

[Lezione successiva: 2. salvataggio, recupero e condivisione di ancoraggi spaziali di Azure](mrlearning-asa-ch2.md)

---
title: Esercitazioni sugli ancoraggi spaziali di Azure-1. Introduzione agli ancoraggi spaziali di Azure
description: Completa questo corso per apprendere come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: e62d3626ec6f2dbf8b66378212afab7db2f56422
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334457"
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

* Un PC Windows 10 configurato con gli [strumenti corretti installati](install-the-tools.md)
* Windows 10 SDK 10.0.18362.0 o versione successiva
* Funzionalità di C# programmazione di base
* Un dispositivo HoloLens 2 [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode)
* Completare la sezione [creare una risorsa ancoraggi spaziali](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) della [Guida introduttiva: creare un'app HoloLens Unity che usa l'esercitazione sugli ancoraggi spaziali di Azure](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) .

>[!IMPORTANT]
>Questa serie di esercitazioni richiede <a href="https://unity3d.com/get-unity/download/archive" target="_blank">unity 2019,1</a> e la versione consigliata è Unity 2019.1.14. Questa operazione sostituisce i requisiti di versione di Unity o i consigli indicati nei prerequisiti collegati in precedenza.

## <a name="creating-the-unity-project"></a>Creazione del progetto Unity

In questa sezione si creerà un nuovo progetto Unity e lo si configurerà per la realtà mista di Windows.

1. Creare un progetto Unity e assegnargli un nome appropriato, ad esempio, l' _esercitazione sugli ancoraggi spaziali di Azure_.

2. Configurare il progetto Unity per la realtà mista di Windows.

    >[!TIP]
    >Per un promemoria su come creare un progetto Unity e configurarlo per la realtà mista di Windows, è possibile vedere le sezioni [Create New Unity](mrlearning-base-ch1.md#create-new-unity-project) Project e [Configure the Unity for Windows Mixed Reality](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality) dell'esercitazione sull' [inizializzazione del progetto e della prima applicazione](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) , che fa parte della serie di [esercitazioni introduttive](mrlearning-base.md) .

## <a name="adding-inbuilt-unity-packages"></a>Aggiunta di pacchetti Unity incorporati

In questa sezione verranno aggiunti i pacchetti e gli asset Unity incorporati richiesti dai Toolkit e dagli SDK che verranno usati nel progetto.

1. Importare le risorse essenziali TMP.

    >[!NOTE]
    >Questo pacchetto è stato aggiunto perché è richiesto dal Toolkit per la realtà mista.

    Nel menu Unity selezionare **Window** > **TEXTMESHPRO** > **Import tmp Essential Resources**.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-2-1.1.png)

    Nella finestra popup importa pacchetto Unity, verificare innanzitutto che tutti gli asset siano selezionati facendo clic sul pulsante **tutti** , quindi importare gli asset facendo clic sul pulsante **Importa** .

    ![mrlearning-ASA](images/mrlearning-asa-ch1-2-1.2.png)

2. Installare AR Foundation.

    >[!NOTE]
    >Questo pacchetto è stato aggiunto perché è richiesto da Azure Spatial Anchors SDK.

    Nel menu Unity selezionare **Window** > **Package Manager**.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-2-2.1.png)

    Nella finestra Gestione pacchetti selezionare **AR Foundation** e installare il pacchetto facendo clic sul pulsante **Installa** .

    >[!IMPORTANT]
    >Potrebbero essere necessari alcuni secondi prima che il pacchetto AR Foundation venga visualizzato nell'elenco.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-2-2.2.png)

## <a name="importing-the-tutorial-assets"></a>Importazione delle risorse dell'esercitazione

In questa sezione vengono scaricati e importati tutti gli asset dell'esercitazione.

1. Scaricare gli asset.

    * [AzureSpatialAnchors. file unitypackage Tools](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.0.0/AzureSpatialAnchors.unitypackage) (versione 2.0.0)
    * [Microsoft. MixedReality. Toolkit. Unity. Foundation. 2.1.0. file unitypackage Tools](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)
    * [MRTK. HoloLens2. Unity. Esercitations. assets. GettingStarted. 2.1.0.1. file unitypackage Tools](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.1.0.1.unitypackage)
    * [MRTK. HoloLens2. Unity. Esercitations. assets. AzureSpatialAnchors. 2.1.0.1. file unitypackage Tools](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.1.0.1.unitypackage)

2. Importare gli asset.

    Nel menu Unity selezionare **asset** > **Importa pacchetto** > **pacchetto personalizzato...** .

    ![mrlearning-ASA](images/mrlearning-asa-ch1-3-2.1.png)

    Nel pacchetto di importazione... finestra popup, selezionare **AzureSpatialAnchors. file unitypackage Tools** e fare clic sul pulsante **Apri** .

    ![mrlearning-ASA](images/mrlearning-asa-ch1-3-2.2.png)

    Nella finestra popup importa pacchetto Unity, verificare innanzitutto che tutti gli asset siano selezionati facendo clic sul pulsante **tutti** , quindi importare gli asset facendo clic sul pulsante **Importa** .

    ![mrlearning-ASA](images/mrlearning-asa-ch1-3-2.3.png)

    Ripetere questi passaggi per importare i pacchetti di asset rimanenti. Al termine, la cartella **assets** del progetto Unity deve contenere le sottocartelle.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-3-2.4.png)

## <a name="creating-and-preparing-the-scene"></a>Creazione e preparazione della scena

In questa sezione verrà creata e preparata la scena aggiungendo il Toolkit di realtà mista e alcune delle prefabbricazioni dell'esercitazione.

1. Creare una nuova scena.

    Scegliere **File** > **nuova scena**dal menu di Unity.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-1.1.png)

    Nel menu Unity selezionare **File** > **Salva con nome...** .

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-1.2.png)

    Nella finestra popup Salva scena passare alla cartella **scene** del progetto, assegnare alla scena un nome appropriato, ad esempio _ASATutorialScene_, e salvare la scena facendo clic sul pulsante **Salva** .

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-1.3.png)

    >[!TIP]
    >È possibile salvare la scena ovunque si trovino, purché si trovino nella cartella assets del progetto. Tuttavia, per rendere organizzato il progetto, è in genere consigliabile salvarlo nella cartella scene del progetto.

2. Aggiungere il Toolkit per la realtà mista.

    Nel menu Unity selezionare **Toolkit realtà mista** > **Aggiungi a scena e configura...** .

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-2.1.png)

    Nella finestra popup seleziona MixedRealityToolkitConfigurationProfile fare clic su **DefaultHoloLens2ConfigurationProfile** per impostarlo come profilo di configurazione MRTK della scena.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-2.2.png)

    Nel menu Unity selezionare **File** > **Salva** per salvare la scena.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-2.3.png)

    >[!TIP]
    >È possibile usare il tasto di scelta rapida CTRL + S (Command + S in macOS) per salvare rapidamente la scena mentre si lavora in questa esercitazione.

3. Aggiungere i prefabbricati dell'esercitazione.

    Nel pannello progetto passare a **asset** > **MRTK. Tutorials. AzureSpatialAnchors** > cartella **prefabbricates** . Tenendo premuto il pulsante CTRL (comando in macOS), fare clic su **ButtonParent**, **DebugWindow**e **ParentAnchor** per selezionare i tre prefabbricati.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-3.1.png)

    Con i tre prefabbricati ancora selezionati, trascinarli nel pannello gerarchia per aggiungerli alla scena.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-3.2.png)

    Per concentrarsi sugli oggetti nella scena, è possibile fare doppio clic sull'oggetto ParentAnchor e quindi eseguire di nuovo lo zoom indietro.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-3.3.png)

    >[!TIP]
    >Se si trovano le icone grandi nella scena, ad esempio, le icone con frame ' t'di grandi dimensioni, è possibile nasconderle impostando <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">i gizmo</a> sulla posizione OFF.

## <a name="configuring-the-buttons-to-operate-the-scene"></a>Configurazione dei pulsanti per il funzionamento della scena

In questa sezione si aggiungeranno i prefabbricati e gli script nella scena per creare una serie di pulsanti che dimostrano le nozioni di base relative al comportamento degli ancoraggi locali e degli ancoraggi spaziali di Azure in un'applicazione.

1. Configurare il componente Button (script) di Holo Lens 2 (script).

    Nel pannello gerarchia espandere l'oggetto **ButtonParent** e selezionare il primo oggetto figlio denominato **StartAzureSession**.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-5-1.1.png)

    Nel pannello Inspector scorrere verso il basso fino al **pulsante stampabile pulsante Holo Lens 2 (script)** e aggiungere un nuovo listener di eventi all'evento **Button premuto ()** facendo clic sull'icona **+** .

    ![mrlearning-ASA](images/mrlearning-asa-ch1-5-1.2.png)

    Con l'oggetto StartAzureSession ancora selezionato nel pannello gerarchia, fare clic e trascinare l'oggetto **ParentAnchor** dal pannello gerarchia nel campo vuoto **None (oggetto)** del listener di eventi appena aggiunto per fare in modo che l'oggetto ParentAnchor attenda gli eventi di pulsante premuto da questo pulsante.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-5-1.3.png)

    Fare clic sull'elenco a discesa **Nessuna funzione** dello stesso listener di eventi, quindi selezionare **AnchorModuleScript** > **StartAzureSession ()** per impostare la funzione StartAzureSession () come azione attivata quando viene attivato il pulsante eventi premuti da questo pulsante.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-5-1.4.png)

2. Configurare il componente interactable (script).

    Con l'oggetto StartAzureSession ancora selezionato nel pannello gerarchia, nel pannello Inspector scorrere verso il basso fino al componente **interagibile (script)** e ripetere lo stesso processo descritto nel passaggio 1 per l'evento **OnClick ()** .

    ![mrlearning-ASA](images/mrlearning-asa-ch1-5-2.1.png)

3. Configurare i pulsanti rimanenti

    Per ognuno dei pulsanti rimanenti, completare il processo descritto nel passaggio 1 e 2 precedente per assegnare funzioni a entrambi gli eventi del pulsante premuto () e OnClick () seguenti:

    * Per l'oggetto **StopAzureSession** , assegnare la funzione **StopAzureSession ()** .
    * Per l'oggetto **CreateAnchor** , assegnare la funzione **CreateAzureAnchor ()** , quindi trascinare di nuovo il **ParentAnchor** nel campo vuoto **None (oggetto gioco)** .
    * Per iniziare a cercare l'oggetto **di ancoraggio** , assegnare la funzione **FindAzureAnchor ()** .
    * Per l'oggetto **Delete Azure Anchor** assegnare la funzione **DeleteAzureAnchor ()** .
    * Per l'oggetto **Elimina ancoraggio locale** assegnare la funzione **RemoveLocalAnchor ()** , quindi trascinare nuovamente il **ParentAnchor** nel campo vuoto **None (oggetto gioco)** .

4. Connettere la scena alla risorsa di Azure

    Nel pannello gerarchia selezionare l'oggetto **ParentAnchor** e nel pannello Inspector scorrere verso il basso fino al componente **Spatial Anchor Manager (script)** .

    Quindi, nella sezione **Credentials (credenziali** ) incollare l'ID e la chiave dell'account di ancoraggio spaziale nei campi dell' **ID** dell'account di ancoraggio spaziale e dei campi **chiave dell'account** di ancoraggio spaziale corrispondente.

    >[!NOTE]
    >Sono stati creati l'ID e la chiave dell'account di ancoraggio spaziali come parte dei [prerequisiti](mrlearning-asa-ch1.md#prerequisites)di questa esercitazione.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-5-4.1.png)

    >[!CAUTION]
    >Assicurarsi di salvare la scena.

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a>Provare i comportamenti di base degli ancoraggi spaziali di Azure

Ora che la scena è configurata in modo da illustrare gli elementi di base degli ancoraggi spaziali di Azure, è necessario distribuire l'app per poter provare i Anchor spaziali di Azure in prima persona.

1. Aggiungere altre funzionalità necessarie.

    Nel menu Unity selezionare **modifica** > **Impostazioni progetto...** per aprire il pannello Impostazioni lettore.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-6-1.1.png)

    Nel pannello Impostazioni lettore selezionare **Player** e quindi impostazioni di **pubblicazione**.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-6-1.2.png)

    Nelle **impostazioni di pubblicazione**scorrere verso il basso fino alla sezione **funzionalità** e verificare che **SpatialPerception**, che è stato abilitato al momento della creazione del progetto all'inizio dell'esercitazione, sia abilitato. Quindi, abilitate le funzionalità **internetClient**, **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage**, **Webcam**e **microfono** .

    ![mrlearning-ASA](images/mrlearning-asa-ch1-6-1.3.png)

2. Distribuire l'app in HoloLens 2.

    >[!TIP]
    >Per un promemoria su come compilare e distribuire il progetto Unity in HoloLens 2, è possibile fare riferimento alle sezioni [compilare l'applicazione nel dispositivo](mrlearning-base-ch1.md#build-your-application-to-your-device) dell'esercitazione [inizializzazione del progetto e della prima applicazione](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) , che fa parte della serie di [esercitazioni introduttive](mrlearning-base.md) .

3. Eseguire l'app e seguire le istruzioni in-app.

    >[!CAUTION]
    >Gli ancoraggi spaziali di Azure usano Internet per salvare e caricare i dati di ancoraggio, quindi assicurarsi che il dispositivo sia connesso a Internet.

    Quando l'applicazione è in esecuzione nel dispositivo, seguire le istruzioni visualizzate nel pannello **istruzioni del modulo di ancoraggio spaziale di Azure** .

    ![mrlearning-ASA](images/mrlearning-asa-ch1-6-3.1.png)

## <a name="anchoring-an-experience"></a>Ancoraggio di un'esperienza

Nelle sezioni precedenti sono state apprese le nozioni di base degli ancoraggi spaziali di Azure. È stato usato un cubo per rappresentare e visualizzare l'oggetto del gioco padre con l'ancoraggio collegato. In questa sezione si apprenderà come ancorare un'intera esperienza inserendola come figlio dell'oggetto ParentAnchor.

1. Aggiungere l'esperienza di avvio Rocket.

    Nel pannello progetto passare a **asset** > **MRTK. Tutorials. GettingStarted** > cartella **prefabbricates** e selezionare il **Rocket Launcher_Complete** prefabbricate.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-7-1.1.png)

    Con il Rocket Launcher_Complete prefabbricato ancora selezionato, trascinarlo sopra l'oggetto **ParentAnchor** nel pannello gerarchia per impostarlo come figlio dell'oggetto ParentAnchor.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-7-1.2.png)

2. Riposizionare l'esperienza di avvio Rocket.

    Spostare il modulo **Rocket Launcher_Complete** oggetto in modo che il **ParentAnchor** (cubo) sia ancora esposto.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-7-2.1.png)

    Nell'applicazione, gli utenti possono ora riposizionare l'intera esperienza di avvio del lanciarazzi spostando il cubo.

    >[!TIP]
    >Sono disponibili diversi flussi di esperienza utente per il riposizionamento, incluso l'uso di un oggetto di riposizionamento (ad esempio il cubo usato in questa esercitazione), l'uso di un pulsante per alternare un rettangolo di selezione che racchiude l'esperienza, l'uso della posizione e della rotazione Gizmo e altro ancora.

## <a name="congratulations"></a>Lezione completata

In questa esercitazione sono state apprese le nozioni di base degli ancoraggi spaziali di Azure. Questa lezione ha fornito diversi pulsanti che consentono di esplorare i diversi passaggi necessari per avviare e arrestare una sessione di Azure e creare, caricare e scaricare gli ancoraggi di Azure in un singolo dispositivo.

Nella lezione successiva si apprenderà come salvare gli ID di ancoraggio di Azure in HoloLens 2 per il recupero, anche dopo il riavvio dell'applicazione e come trasferire gli ID di ancoraggio tra più dispositivi per ottenere l'allineamento spaziale.

[Lezione successiva: 2. salvataggio, recupero e condivisione di ancoraggi spaziali di Azure](mrlearning-asa-ch2.md)

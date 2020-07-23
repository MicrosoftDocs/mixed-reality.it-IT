---
title: Esercitazioni su Holographic Remoting per PC - 1. Introduzione a Holographic Remoting per PC
description: Completa questo corso per apprendere come usare in remoto l'esperienza di realtà mista da PC a HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 05/19/2020
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: cbbad9548abeb1b8392b99d187b5b051d5b4ddd4
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/14/2020
ms.locfileid: "86305779"
---
# <a name="1-getting-started-with-pc-holographic-remoting"></a>1. Introduzione a Holographic Remoting per PC

## <a name="overview"></a>Panoramica

  Queste sono le esercitazioni su HoloLens 2. In questa serie di esercitazioni in due parti verrà illustrato come creare una dimostrazione dell'esperienza di realtà mista e come creare un'app per PC per Holographic Remoting.

   In questa esercitazione, [Creare un'esperienza di realtà mista](mr-learning-pc-holographic-remoting-01.md), apprenderai come creare tale esperienza. Verranno infatti illustrati gli elementi dell'interfaccia utente e le funzionalità di manipolazione del modello 3D, ritaglio del modello e tracciamento oculare.

  Nella seconda esercitazione, [Creare un'applicazione per Holographic Remoting](mr-learning-pc-holographic-remoting-02.md), apprenderai come creare un'app per PC per Holographic Remoting. Apprenderai inoltre come effettuare la connessione a HoloLens 2 in qualsiasi momento, fornendo un modo per visualizzare il contenuto 3D in realtà mista.

## <a name="objectives"></a>Obiettivi

* Importare gli asset e configurare la scena
* Interagire con gli ologrammi usando pulsanti ed elementi dell'interfaccia utente
* Configurare gli oggetti 3D per la funzionalità di ritaglio
* Apprendere come attivare le descrizioni comandi con il tracciamento oculare

## <a name="prerequisites"></a>Prerequisiti

* Un PC Windows 10 configurato in cui siano [installati gli strumenti](install-the-tools.md) corretti
* Conoscenza della programmazione C# di base
* Un dispositivo HoloLens 2 [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode)
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.3.X montato e il modulo di supporto delle compilazioni UWP (Universal Windows Platform) aggiunto

>[!ASSOLUTAMENTE CONSIGLIATO] Completamento della serie di esercitazioni introduttive o esperienza di base precedente con Unity e MRTK

> [!IMPORTANT]
> La versione di Unity consigliata per questa serie di esercitazioni è Unity 2019.3.X. Questa istruzione sostituisce gli eventuali requisiti o suggerimenti relativi alla versione di Unity indicati negli argomenti visualizzabili facendo clic sui collegamenti dei prerequisiti sopra riportati.

## <a name="creating-and-preparing-the-unity-project"></a>Creazione e preparazione del progetto Unity

In questa sezione creerai un nuovo progetto Unity per prepararti allo sviluppo con MRTK.

A questo scopo, segui prima l'esercitazione [Inizializzazione del progetto e prima applicazione](mr-learning-base-02.md), escluse le istruzioni della sezione [Compilare l'applicazione nel dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), che include i passaggi seguenti:

1. [Creazione del progetto Unity](mr-learning-base-02.md#creating-the-unity-project) e assegnazione di un nome appropriato, ad esempio *MRTK Tutorials*

1. [Passaggio a un'altra piattaforma di compilazione](mr-learning-base-02.md#configuring-the-unity-project)

1. [Importazione delle risorse essenziali TextMeshPro](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)

1. [Importazione di Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)

1. [Configurazione del progetto Unity](mr-learning-base-02.md#configuring-the-unity-project)

1. [Creazione e impostazione della scena](mr-learning-base-02.md#creating-and-configuring-the-scene) e assegnazione di un nome appropriato, ad esempio **PC Holographic Remoting**

Segui quindi le istruzioni riportate in [Modifica delle opzioni di visualizzazione di consapevolezza spaziale](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) per impostare **DefaultHoloLens2ConfigurationProfile** come profilo di configurazione MRTK per la scena. Modifica le opzioni di visualizzazione per la mesh di consapevolezza spaziale impostando **Occlusion** (Occlusione).

## <a name="importing-the-tutorial-assets"></a>Importazione degli asset dell'esercitazione

Scarica e **importa** [MRTK.Tutorials.PCHolographicRemoting.unitypackage](https://github.com/onginnovations/MixedRealityLearning/releases/download/pc-holographic-remoting-v2.4.0.0/MRTK.Tutorials.PCHolographicRemoting.unitypackage).

>[!TIP]
> Per rivedere la procedura di importazione di un pacchetto personalizzato di Unity, puoi fare riferimento alle istruzioni contenute in [Importare Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).

Dopo l'importazione degli asset dell'esercitazione, la finestra Project (Progetto) avrà un aspetto simile al seguente:

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section2-Step1-1.png)

## <a name="configuring-and-preparing-the-scene"></a>Configurazione e preparazione della scena

In questa sezione preparerai la scena aggiungendo alcuni dei prefab dell'esercitazione.

Nella finestra Project (Progetto) passa alla cartella **Assets** (Asset)  > **MRTK.Tutorials.PCHolograhicRemoting** > **Prefabs** (Prefab). Tenendo premuto il pulsante CTRL, fai clic sui sei prefab riportati di seguito.

* ButtonParent
* ClippingObjects
* HandSpatialMapButton
* Istruzioni
* ModelParent
* Piattaforma

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-1.png)

Trascina e rilascia questi modelli dalla cartella dei prefab nella **finestra Hierarchy** (Gerarchia).

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-2.png)

Per concentrarti sugli oggetti nella scena, puoi fare doppio clic sull'oggetto **ModelParent** e quindi fare di nuovo leggermente zoom avanti:

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-3.png)

> [!TIP]
> Se trovi che le icone grandi nella scena, come quelle a forma di "T", siano motivo di distrazione, puoi nasconderle <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">disattivando i gizmo</a>.

## <a name="configuring-the-buttons-to-operate-the-scene"></a>Configurazione dei pulsanti per il funzionamento della scena

In questa sezione aggiungerai nella scena gli script per creare eventi pulsante a dimostrazione delle nozioni di base sul passaggio a un altro modello e sulla funzionalità di ritaglio.

### <a name="1-configuring-the-interactable-script-component"></a>1. Configurazione del componente Interactable (Script) (Con supporto per interazioni - Script)

Nella finestra Hierarchy (Gerarchia) espandi l'oggetto **ButtonParent** e seleziona **NextButton**. Nella finestra Inspector (Controllo) individua il componente **Interactable (Script)** (Con supporto per interazioni - Script) e fai clic sull'icona **+** sotto l'evento **OnClick ()** .

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-1.png)

Con l'oggetto **NextButton** ancora selezionato nella finestra Hierarchy (Gerarchia), fai clic e trascina l'oggetto **ButtonParent** dalla finestra Hierarchy (Gerarchia) nel campo **None (Object)** (Nessuno - Oggetto) vuoto dell'evento appena aggiunto per fare in modo che l'oggetto ButtonParent rimanga in ascolto dell'evento di clic del pulsante attivato a partire da questo pulsante:

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-2.png)

Fai clic sull'elenco a discesa **No Function** (Nessuna funzione) dello stesso evento. Seleziona quindi **ViewButtonControl** > **NextModel ()** per impostare la funzione **NextModel ()** come l'azione che viene attivata quando l'evento di pulsante premuto viene attivato a partire da questo pulsante:

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-3.png)

### <a name="2-configuring-the-remaining-buttons"></a>2. Configurazione dei pulsanti rimanenti

Per ognuno dei pulsanti rimanenti, completa il processo descritto in precedenza per assegnare funzioni agli eventi **OnClick ()** :

* Per l'oggetto PreviousButton, assegna la funzione **ViewButtonControl** > **PreviousModel ()** .

* Per ClippingButton, seleziona la funzione **ToggleButton** > **ToggleClipping ()** .

### <a name="3-configuring-the-view-button-control-script--and-toggle-button-script-components"></a>3. Configurazione dei componenti View Button Control (Script) (Controllo pulsante di visualizzazione - Script) e Toggle Button (Script) (Interruttore - Script)

Ora i pulsanti sono configurati per illustrare il funzionamento del passaggio a un altro modello e la funzionalità di ritaglio. È il momento di aggiungere modelli 3D e gli oggetti di ritaglio allo script.

Sono stati forniti sei modelli 3D diversi per la dimostrazione. Espandi ***ModelParentobject*** per esporre questi modelli 3D.

Con l'oggetto ButtonParent ancora selezionato nella finestra Hierarchy (Gerarchia), individua nella finestra Inspector (Controllo) il componente **View Button Control (Script)** (Controllo pulsante di visualizzazione - Script) ed espandi la variabile **Models** (Modelli).

Nel campo **Size** (Dimensione) immetti il numero di modelli 3D che vuoi avere nella scena. In questo caso, 6. Verranno creati i campi per l'aggiunta di nuovi modelli 3D.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-1.png)

Trascina e rilascia ogni oggetto figlio dell'oggetto ModelParent in questi campi.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-2.png)

Trascina e rilascia l'oggetto **ClippingObjects** dalla finestra Hierarchy (Gerarchia) nel campo **Clipping Object** (Oggetto di ritaglio) del componente **Toggle Button (Script)** (Interruttore - Script).
>[!NOTE]
>Rimani solo nell'oggetto padre del pulsante.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-3.png)

Nella finestra Hierarchy (Gerarchia) seleziona il prefab **ClippingObjects** e abilitalo nella finestra Inspector (Controllo) per attivare gli oggetti di ritaglio.

## <a name="configuring-the-clipping-objects-to-enable-clipping-feature"></a>Configurazione degli oggetti di ritaglio per abilitare la funzionalità di ritaglio

In questa sezione aggiungerai il renderer degli oggetti figlio dell'oggetto MarsCuriosityRover in un singolo oggetto di ritaglio per illustrare il funzionamento del ritaglio del modello MarsCuriosityRover.

Nella finestra Hierarchy (Gerarchia) espandi l'oggetto **ClippingObjects** per esporre i tre diversi oggetti di ritaglio che userai in questo progetto.

Per configurare l'oggetto **ClippingSphere**, fai clic su di esso e nella finestra Inspector (Controllo) individua il componente **Clipping Sphere (Script)** (Sfera di ritaglio - Script). Nel campo della dimensione immetti il numero di renderer che è necessario aggiungere per il modello 3D. In questo caso, aggiungi 10 per gli oggetti figlio di MarsCuriosityRover. Verranno creati i campi per l'aggiunta dei renderer. Trascina e rilascia gli oggetti modello figlio dell'oggetto MarsCuriosityRover in questi campi.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section5-Step1-1.png)

Segui lo stesso processo e aggiungi i renderer degli oggetti figlio di MarsCuriosityRover agli oggetti **ClippingBox** e **ClippingPlane**.

In questa esercitazione verrà usato solo il modello MarsCuriosityRover per illustrare la funzionalità di ritaglio. Sono state comunque aggiunte funzionalità di ritaglio anche ad altri modelli, aumentando la dimensione del renderer, e sono stati aggiunti i singoli renderer mesh corrispondenti.

## <a name="configuring-eye-tracking-to-highlight-tooltips"></a>Configurazione del tracciamento oculare per evidenziare le descrizioni comandi

In questa sezione esaminerai come abilitare il tracciamento oculare nel tuo progetto. Ad esempio, implementerai la funzionalità per evidenziare le descrizioni comandi associate alle parti di MarsCuriosityRover quando le guardi e per nasconderle quando distogli lo sguardo da esse.

### <a name="1-identify-target-objects-and-associated-tooltips"></a>1. Identificare gli oggetti di destinazione e le descrizioni comandi associate.

Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto ModelParent. Espandi ***MarsCuriosity -> Rover*** per trovare cinque parti principali di MarsCuriosityRover: **POI-Camera**, **POI-Wheels**, **POI-Antena**, **POI-Spectrometer** e **POI-RUHF Antenna**.

* Osserva cinque oggetti descrizione comando corrispondenti associati a parti di MarsCuriosityRover nella finestra Hierarchy (Gerarchia). 
* Configurerai questi oggetti per evidenziare l'esperienza quando guardi le parti di MarsCuriosityRover.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step1-1.png)

### <a name="2-implement-while-looking-at-target-----on-look-away--events"></a>2. Implementare gli eventi Looking At Target () (Mentre viene guardata la destinazione) e On Look Away () (Quando viene distolto lo sguardo)

Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto ***POI-Camera***. Nella finestra Inspector (Controllo) individua il componente **Eye Tracking Target (Script)** (Destinazione tracciamento oculare - Script) e configura gli eventi **While Looking At Target ()** (Mentre viene guardata la destinazione) & **On Look Away ()** (Quando viene distolto lo sguardo) come indicato di seguito:

* Al campo **None (Object)** (Nessuno - Oggetto) assegna l'oggetto **POI-Camera ToolTip**
* Dall'elenco a discesa **No Function** (Nessuna funzione) dell'evento **While Looking At Target ()** (Mentre viene guardata la destinazione) seleziona **GameObject** > **SetActive (bool).** Seleziona la **casella di controllo** sottostante per evidenziare la descrizione comando come l'azione che viene attivata quando guardi l'oggetto di destinazione.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-1.png)

* Segui lo stesso processo e fai clic sull'elenco a discesa **No Function** (Nessuna funzione) del listener di eventi **On Look Away ()** (Quando viene distolto lo sguardo). Seleziona quindi **GameObject** > **SetActive (bool**) e lascia vuota la **casella di controllo** per nascondere la descrizione comando come l'azione che viene attivata quando distogli lo sguardo dall'oggetto di destinazione.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-2.png)

Segui lo stesso processo e assegna i rispettivi oggetti descrizione comando agli eventi **While Looking At Target ()** (Mentre viene guardata la destinazione) & **On Look Away ()** (Quando viene distolto lo sguardo) delle parti corrispondenti di **MarsCuriosityRover**.

Per abilitare il tracciamento oculare, segui queste [linee guida](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch5#5-enable-simulated-eye-tracking-for-in-editor-simulations).

## <a name="congratulations"></a>Lezione completata

In questa esercitazione hai appreso come creare un'esperienza di realtà mista con la dimostrazione del funzionamento degli elementi dell'interfaccia utente e delle funzionalità di manipolazione del modello 3D, di ritaglio del modello e di tracciamento oculare. Nell'esercitazione sono stati forniti NextButton e PreviousButton che ti consentono di esplorare l'esperienza di visualizzazione del modello 3D. Con ClippingObjectButton hai attivato gli oggetti di ritaglio e visto come opera la funzionalità di ritaglio. Nell'esercitazione è stato inoltre fornito un elemento di tracciamento oculare che consente di evidenziare le descrizioni comandi nell'esperienza.

Nella lezione successiva apprenderai come creare un'applicazione per Holographic Remoting per PC per connettere HoloLens 2 in qualsiasi momento, offrendo un modo per visualizzare il contenuto 3D in realtà mista.

[Lezione successiva: 2. Creare un'applicazione per Holographic Remoting](mr-learning-pc-holographic-remoting-02.md)

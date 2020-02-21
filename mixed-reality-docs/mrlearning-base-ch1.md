---
title: Esercitazioni introduttive - 2 Inizializzazione del progetto e prima applicazione
description: Completa questo corso per informazioni su come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 11/01/2019
ms.topic: article
ms.localizationpriority: high
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: d3392df9bfad5938d71d3a01999be51834a98a5d
ms.sourcegitcommit: 87aca9c2b73b0e83cb70a46443dcdb08c3621005
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/17/2020
ms.locfileid: "77373453"
---
# <a name="2-initializing-your-project-and-first-application"></a>2. Inizializzazione del progetto e prima applicazione

## <a name="overview"></a>Panoramica

<!-- TODO: Consider expanding to include summary of each tutorial in this tutorial series -->
In questa prima esercitazione apprenderai alcune delle funzionalità offerte da <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a>, inizierai a creare la tua prima applicazione per HoloLens 2 e la distribuirai nel dispositivo.

## <a name="objectives"></a>Obiettivi

* Configurare Unity per lo sviluppo per HoloLens
* Importare gli asset e configurare la scena
* Visualizzare la mesh di mapping spaziale, le mesh manuali e il contatore della frequenza dei fotogrammi

## <a name="prerequisites"></a>Prerequisiti

* Un PC Windows 10 configurato in cui siano [installati gli strumenti](install-the-tools.md) corretti
* Windows 10 SDK 10.0.18362.0 o versioni successive
* Alcune funzionalità di programmazione C# di base
* Un dispositivo HoloLens 2 [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode)
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.2.X installato e il modulo di supporto delle compilazioni UWP (Universal Windows Platform) aggiunto

> [!IMPORTANT]
> La versione di Unity consigliata per questa serie di esercitazioni è Unity 2019.2.X. Questa istruzione sostituisce gli eventuali requisiti o suggerimenti relativi alla versione di Unity indicati negli argomenti visualizzabili facendo clic sui collegamenti dei prerequisiti sopra riportati.

## <a name="create-new-unity-project"></a>Creare un nuovo progetto Unity

Avvia **Unity Hub**, seleziona la scheda **Projects** (Progetti) e fai clic sulla **freccia giù** accanto al pulsante **New** (Nuovo):

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-1.png)

Seleziona la versione di Unity specificata più indietro nella sezione [Prerequisiti](#prerequisites):

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-2.png)

Nella finestra Create a new project (Crea un nuovo progetto):

* Assicurati che in **Templates** (Modelli) sia impostata l'opzione **3D**
* Immetti un nome appropriato nel campo **Project Name** (Nome progetto), ad esempio _MRTK Tutorials_
* Nel campo **Location** (Percorso) scegli un percorso appropriato in cui archiviare il progetto, ad esempio _D:\MixedRealityLearning_
* Fai clic sul pulsante **Create** (Crea) per creare e avviare il nuovo progetto Unity

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-3.png)

> [!CAUTION]
> Se lavori in Windows, tieni presente che è previsto un limite (MAX_PATH) di 255 caratteri per il percorso. Questi limiti incidono su Unity, pertanto la compilazione potrebbe avere esito negativo se un percorso file qualsiasi è costituito da più di 255 caratteri. Di conseguenza, è consigliabile archiviare il progetto Unity nel percorso più vicino possibile alla radice dell'unità.

Attendi che Unity crei il progetto:

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-4.png)

## <a name="configure-the-unity-project-for-windows-mixed-reality"></a>Configurare il progetto Unity per Windows Mixed Reality

<!-- TODO: Consider adding info about configuring Unity for WMR vs MRTK, or removing WMR section -->

In questa sezione cambierai piattaforma di compilazione e abiliterai sia la realtà virtuale che la percezione spaziale.

### <a name="1-switch-build-platform"></a>1. Cambiare piattaforma di compilazione

Dal menu di Unity scegli **File** > **Build Settings** (Impostazioni di compilazione) per visualizzare la finestra corrispondente:

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-1.png)

Nella finestra Build Settings (Impostazioni di compilazione), seleziona **Universal Windows Platform** e fai clic sul pulsante **Switch Platform** (Cambia piattaforma):

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-2.png)

Attendi che Unity completi il passaggio all'altra piattaforma:

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-3.png)

Una volta completato il passaggio all'altra piattaforma, fai clic sull'icona **x** di colore rosso per chiudere la finestra Build Settings (Impostazioni di compilazione):

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-4.png)

### <a name="2-enable-virtual-reality"></a>2. Abilitare la realtà virtuale

> [!NOTE]
> L'abilitazione della realtà virtuale si applica anche ai visori VR di realtà mista e realtà aumentata perché riguarda l'abilitazione della visione stereoscopica, ovvero il rendering di immagini diverse per ogni occhio.

Dal menu di Unity scegli **Edit** (Modifica) > **Project Settings** (Impostazioni del progetto) per visualizzare la finestra corrispondente:

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-1.png)

Nella finestra Project Settings (Impostazioni del progetto), seleziona **Player** (Riproduttore) > **XR Settings** (Impostazioni XR) per espandere tali impostazioni:

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-2.png)

In XR Settings (Impostazioni XR), seleziona la casella di controllo **Virtual Reality Supported** (Realtà virtuale supportata) per abilitare la realtà virtuale e quindi fai clic sull'icona **+** e seleziona **Windows Mixed Reality** per aggiungere Windows Mixed Reality SDK:

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-3.png)

Attendi che Unity termini di aggiungere l'SDK:

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-4.png)

Al termine dell'aggiunta dell'SDK, ottimizza le impostazioni XR come illustrato di seguito:

* Nella sezione Windows Mixed Reality, imposta il campo **Depth Format** (Formato profondità) su **16-bit depth** (Profondità a 16 bit)
* Sempre nella sezione Windows Mixed Reality, seleziona la casella di controllo **Enable Depth Sharing** (Abilita condivisione profondità)
* Imposta il campo **Stereo Rendering Mode\*** (Modalità di rendering stereo) su **Single Pass Instanced** (Con creazione delle istanze in un unico passaggio)

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-5.png)

> [!TIP]
> Per altre informazioni sull'ottimizzazione di Unity per Windows Mixed Reality, puoi fare riferimento all'argomento [Impostazioni consigliate per Unity](recommended-settings-for-unity.md).

### <a name="3-enable-spatial-perception"></a>3. Abilitare la percezione spaziale

> [!NOTE]
> La percezione spaziale consente la visualizzazione della mesh di mapping spaziale nei dispositivi Windows Mixed Reality.

Nella finestra Project Settings (Impostazioni del progetto), seleziona **Player** (Riproduttore) > **Publishing Settings** (Impostazioni di pubblicazione) per espandere tali impostazioni:

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step3-1.png)

In Publishing Settings (Impostazioni di pubblicazione), scorri verso il basso fino alla sezione **Capabilities** (Funzionalità) e seleziona la casella di controllo **SpatialPerception**:

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step3-2.png)

<!-- TODO: Consider adding info about audio spatializer plugin setting -->

Chiudi la finestra Project Settings (Impostazioni del progetto).

## <a name="import-textmesh-pro-essential-resources"></a>Importare le risorse essenziali TextMesh Pro

> [!NOTE]
> Questo pacchetto viene importato perché è necessario per gli elementi dell'interfaccia utente di Mixed Reality Toolkit.

Dal menu di Unity scegli **Window** (Finestra) > **TextMeshPro** > **Import TMP Essential Resources** (Importa le risorse essenziali TMP):

![mrlearning-base](images/mrlearning-base/tutorial1-section3-step1-1.png)

Nella finestra Import Unity Package (Importa il pacchetto Unity), fai clic sul pulsante **All** (Tutti) per assicurarti che vengano selezionati tutti gli asset e quindi fai clic sul pulsante **Import** (Importa) per importare gli asset:

![mrlearning-base](images/mrlearning-base/tutorial1-section3-step1-2.png)

## <a name="import-the-mixed-reality-toolkit"></a>Importare Mixed Reality Toolkit

Scarica il pacchetto personalizzato di Unity:

* [Microsoft.MixedReality.Toolkit.Unity.Foundation.2.2.0.unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.2.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.2.0.unitypackage)

Dal menu di Unity scegli **Assets** (Asset) > **Import Package** (Importa il pacchetto) > **Custom Package** (Pacchetto personalizzato) per visualizzare la finestra Import package (Importa il pacchetto):

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-1.png)

Nella finestra Import package (Importa il pacchetto), seleziona il pacchetto **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.2.0.unitypackage** scaricato e fai clic sul pulsante **Open** (Apri):

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-2.png)

Nella finestra Import Unity Package (Importa il pacchetto Unity), fai clic sul pulsante **All** (Tutti) per assicurarti che vengano selezionati tutti gli asset e quindi fai clic sul pulsante **Import** (Importa) per importare gli asset:

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-3.png)

## <a name="configure-the-unity-project-for-the-mixed-reality-toolkit"></a>Configurare il progetto Unity per Mixed Reality Toolkit

<!-- TODO: Consider adding info about configuring Unity for WMR vs MRTK, or removing WMR section -->

Dopo che il pacchetto è stato importato, dovrebbe venire visualizzata la finestra MRTK Project Configurator (Configuratore del progetto MRTK). In caso contrario, visualizza tale finestra scegliendo **Mixed Reality Toolkit** > **Utilities** (Utilità) > **Configure Unity Project** (Configura il progetto Unity) dal menu di Unity.

![mrlearning-base](images/mrlearning-base/tutorial1-section5-step1-1.png)

Nella finestra MRTK Project Configurator (Configuratore del progetto MRTK), espandi la sezione **Modify Configurations** (Modifica configurazioni), <u>deseleziona</u> la casella di controllo **Enable MSBuild for Unity** (Abilita MSBuild per Unity), verifica che tutte le altre opzioni siano selezionate e fai clic sul pulsante **Apply** (Applica) per applicare le impostazioni:

![mrlearning-base](images/mrlearning-base/tutorial1-section5-step1-2.png)

> [!CAUTION]
> MSBuild per Unity potrebbe non supportare tutti gli SDK che userai ed essere difficile da disabilitare dopo che è stato abilitato. Di conseguenza, è consigliabile non abilitare MSBuild per Unity.

## <a name="configure-the-mixed-reality-toolkit"></a>Configurare Mixed Reality Toolkit
<!-- TODO: Consider renaming to 'Add the Mixed Reality Toolkit to the Unity scene' -->

Dal menu di Unity scegli **Mixed Reality Toolkit** > **Add to Scene and Configure** (Aggiungi alla scena e configura) per aggiungere Mixed Reality Toolkit alla scena corrente:

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-1.png)

Con l'oggetto MixedRealityToolkit selezionato nella finestra Hierarchy (Gerarchia), nella finestra Inspector (Controllo) imposta il profilo di configurazione di Mixed Reality Toolkit su **DefaultHoloLens2ConfigurationProfile**:

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-2.png)

Dal menu di Unity scegli **File** > **Save As** (Salva con nome) per visualizzare la finestra Save Scene (Salva la scena):

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-3.png)

Nella finestra Save Scene (Salva la scena), passa alla cartella **Scenes** (Scene) del progetto, assegna alla scena un nome appropriato, ad esempio _GettingStarted_, e fai clic sul pulsante **Save** (Salva) per salvare la scena:

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-4.png)

## <a name="build-your-application-to-your-device"></a>Compilare l'applicazione nel dispositivo

### <a name="1-build-the-unity-project"></a>1. Compilare il progetto Unity

Dal menu di Unity scegli **File** > **Build Settings** (Impostazioni di compilazione) per visualizzare la finestra corrispondente.

Nella finestra Build Settings (Impostazioni di compilazione), fai clic sul pulsante **Add Open Scenes** (Aggiungi scene aperte) per aggiungere la scena corrente all'elenco **Scenes In Build** (Scene in compilazione) e quindi fai clic sul pulsante **Build** (Compila) per visualizzare la finestra Build Universal Windows Platform (Compilazione UWP):

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-1.png)

Nella finestra Build Universal Windows Platform (Compilazione UWP), scegli un percorso appropriato in cui archiviare la compilazione, ad esempio _D:\MixedRealityLearning\Builds_, crea una nuova cartella e assegnale un nome adatto (ad esempio, _GettingStarted_) e quindi fai clic sul pulsante **Select Folder** (Seleziona cartella) per avviare il processo di compilazione:

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-2.png)

Attendi che Unity completi il processo di compilazione:

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a>2. Compilare e distribuire l'applicazione

Al termine del processo di compilazione, Unity richiederà a Esplora file di Windows di aprire il percorso in cui è stata archiviata la compilazione. Spostati all'interno della cartella e fai doppio clic sul file della soluzione per aprirlo in Visual Studio:

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-1.png)

> [!NOTE]
> Se Visual Studio chiede di installare nuovi componenti, dedica qualche minuto a verificare che siano installati tutti i componenti indispensabili come specificato nell'argomento [Installare gli strumenti](install-the-tools.md).

Configura Visual Studio per HoloLens 2 selezionando la configurazione **Master** o **Release**, l'architettura **ARM** e **Dispositivo** come destinazione.

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-2.png)

Connetti il dispositivo HoloLens 2 al computer.

> [!IMPORTANT]
> Prima della compilazione nel dispositivo, quest'ultimo deve essere in modalità sviluppatore e associato al computer di sviluppo. Per completare i due passaggi segui [queste istruzioni](using-visual-studio.md).

Il passaggio finale consiste nel compilare e distribuire l'applicazione nel dispositivo selezionando **Debug** > **Avvia senza eseguire debug**:

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-3.png)

Anche se queste istruzioni presuppongono che tu distribuisca l'applicazione in un dispositivo HoloLens 2, puoi anche distribuirla nell'[emulatore HoloLens 2](using-the-hololens-emulator.md) oppure creare un [pacchetto dell'app per il trasferimento locale](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>).

Quando selezioni Avvia senza eseguire debug, l'applicazione viene avviata immediatamente nel dispositivo al termine della compilazione (se questa ha esito positivo), ma senza il debugger associato e senza che in Visual Studio vengano visualizzate le informazioni di debug. Questo significa anche che, mentre l'applicazione è in esecuzione sul dispositivo HoloLens 2, puoi disconnettere il cavo USB senza arrestare l'applicazione.

Per distribuire l'applicazione nel dispositivo senza che venga avviata automaticamente, puoi selezionare Compila > Distribuisci soluzione.

## <a name="congratulations"></a>Lezione completata

<!-- TODO: Consider cleanup and adding in app screenshots -->
A questo punto hai distribuito la tua prima applicazione per HoloLens 2. Esplorando, noterai una mesh di mapping spaziale che copre tutte le superfici percepite da HoloLens 2. Dovresti anche vedere indicatori sulle mani e sulle dita per il tracciamento delle mani e un contatore della frequenza dei fotogrammi per tenere sotto controllo le prestazioni dell'applicazione. Questi sono solo alcuni degli elementi fondamentali, inclusi per impostazione predefinita in Mixed Reality Toolkit. Nelle esercitazioni successive inizierai ad aggiungere più contenuti e interattività alla scena, in modo da poter esplorare completamente le funzionalità di HoloLens 2 e Mixed Reality Toolkit.

> [!NOTE]
> Nell'app puoi notare il profiler di diagnostica. Puoi disattivarne la visibilità tramite il comando vocale di **disattivazione diagnostica**. Tuttavia, in genere è consigliabile lasciare visibile il profiler in qualsiasi momento durante le attività di sviluppo per comprendere quando le modifiche apportate all'app possono aver avuto conseguenze sulle prestazioni, ad esempio l'applicazione HoloLens 2 deve essere [eseguita in modo continuo a 60 FPS](understanding-performance-for-mixed-reality.md).

[Esercitazione successiva: 3. Creazione dell'interfaccia utente e configurazione di Mixed Reality Toolkit](mrlearning-base-ch2.md)

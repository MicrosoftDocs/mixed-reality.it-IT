---
title: Esercitazioni introduttive - 2 Inizializzazione del progetto e distribuzione della prima applicazione
description: Questo corso illustra come usare Mixed Reality Toolkit (MRTK) per creare un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: 5cac7d6f776619cbc2a0e0891b7915b656708726
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376653"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a>2. Inizializzazione del progetto e distribuzione della prima applicazione

## <a name="overview"></a>Panoramica

In questa esercitazione apprenderai come creare un nuovo progetto Unity, come configurarlo per lo sviluppo <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> e come importare MRTK. Esaminerai anche i processi di configurazione, compilazione e distribuzione della scena di esempio Unity di base da Visual Studio a HoloLens 2 o all'emulatore.

## <a name="objectives"></a>Obiettivi

* Apprendere come configurare Unity per lo sviluppo per HoloLens
* Apprendere come compilare e distribuire l'app in HoloLens
* Sperimentare la mesh di mapping spaziale, le mesh manuali e il contatore della frequenza dei fotogrammi

## <a name="creating-the-unity-project"></a>Creazione del progetto Unity

Avvia **Unity Hub**, seleziona la scheda **Projects** (Progetti) e fai clic sulla **freccia giù** accanto al pulsante **New** (Nuovo):

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-1.png)

Nell'elenco a discesa seleziona la **versione** di Unity specificata nella sezione [Prerequisiti](mr-learning-base-01.md#prerequisites):

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> Se la versione specifica di Unity non è disponibile in Unity Hub, puoi avviare l'installazione da <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a> (Archivio download) di Unity.

Nella finestra Create a new project (Crea un nuovo progetto):

* Assicurati che in **Templates** (Modelli) sia impostata l'opzione **3D**
* Immetti un nome appropriato nel campo **Project Name** (Nome progetto), ad esempio _MRTK Tutorials_
* Nel campo **Location** (Percorso) scegli un percorso appropriato in cui archiviare il progetto, ad esempio _D:\MixedRealityLearning_
* Fai clic sul pulsante **Create** (Crea) per creare e avviare il nuovo progetto Unity

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-3.png)

> [!CAUTION]
> Se lavori in Windows, tieni presente che è previsto un limite (MAX_PATH) di 255 caratteri per il percorso. Dovresti pertanto salvare il progetto Unity in prossimità della radice dell'unità.

Attendi che Unity crei il progetto:

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a>Passaggio a un'altra piattaforma di compilazione

Dal menu di Unity scegli **File** > **Build Settings** (Impostazioni di compilazione) per visualizzare la finestra corrispondente:

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-1.png)

Nella finestra Build Settings (Impostazioni di compilazione), seleziona **Universal Windows Platform** e fai clic sul pulsante **Switch Platform** (Cambia piattaforma):

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-2.png)

Attendi che Unity completi il passaggio all'altra piattaforma:

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-3.png)

Una volta completato il passaggio all'altra piattaforma, fai clic sull'icona **x** di colore rosso per chiudere la finestra Build Settings (Impostazioni di compilazione):

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-4.png)

## <a name="importing-the-textmeshpro-essential-resources"></a>Importazione delle risorse essenziali TextMeshPro

Scegli **Window (Finestra)**  > **TextMeshPro** > **Import TMP Essential Resources** (Importa le risorse essenziali TMP) dal menu di Unity per aprire la finestra Import Unity Package (Importa pacchetto Unity):

![mr-learning-base](images/mr-learning-base/base-02-section3-step1-1.png)

Nella finestra Import Unity Package (Importa il pacchetto Unity), fai clic sul pulsante **All** (Tutti) per assicurarti che vengano selezionati tutti gli asset e quindi fai clic sul pulsante **Import** (Importa) per importare gli asset:

![mr-learning-base](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> Le risorse essenziali TextMeshPro sono richieste dagli elementi dell'interfaccia utente di MRTK. Puoi ignorare questo passaggio se non prevedi di usare gli elementi dell'interfaccia utente di MRTK nel progetto.

## <a name="importing-the-mixed-reality-toolkit"></a>Importazione di Mixed Reality Toolkit

Scarica il pacchetto personalizzato di Unity:

* [Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage)

Dal menu di Unity scegli **Assets** (Asset) > **Import Package** (Importa il pacchetto) > **Custom Package** (Pacchetto personalizzato) per visualizzare la finestra Import package (Importa il pacchetto):

![mr-learning-base](images/mr-learning-base/base-02-section4-step1-1.png)

Nella finestra Import package (Importa il pacchetto) seleziona il pacchetto **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage** scaricato e fai clic sul pulsante **Open** (Apri):

![mr-learning-base](images/mr-learning-base/base-02-section4-step1-2.png)

Nella finestra Import Unity Package (Importa il pacchetto Unity), fai clic sul pulsante **All** (Tutti) per assicurarti che vengano selezionati tutti gli asset e quindi fai clic sul pulsante **Import** (Importa) per importare gli asset:

![mr-learning-base](images/mr-learning-base/base-02-section4-step1-3.png)

## <a name="configuring-the-unity-project"></a>Configurazione del progetto Unity

### <a name="1-apply-the-mrtk-project-configurator-settings"></a>1. Applicare le impostazioni di MRTK Project Configurator (Configuratore del progetto MRTK)

Al termine dell'importazione del pacchetto dalla sezione precedente, viene visualizzata la finestra MRTK Project Configurator (Configuratore del progetto MRTK). In caso contrario, apri questa finestra scegliendo **Mixed Reality Toolkit** > **Utilities (Utilità)**  > **Configure Unity Project** (Configura progetto Unity) dal menu di Unity:

![mr-learning-base](images/mr-learning-base/base-02-section5-step1-1.png)

Nella finestra MRTK Project Configurator (Configuratore del progetto MRTK) espandi la sezione **Modify Configurations** (Modifica configurazioni), verifica che tutte le opzioni siano selezionate e fai clic sul pulsante **Apply** (Applica) per applicare le impostazioni:

![mr-learning-base](images/mr-learning-base/base-02-section5-step1-2.png)

### <a name="2-configure-additional-project-settings"></a>2. Configurare impostazioni di progetto aggiuntive

Dal menu di Unity scegli **Edit** (Modifica) > **Project Settings** (Impostazioni del progetto) per visualizzare la finestra corrispondente:

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-1.png)

Nella finestra Project Settings (Impostazioni progetto) seleziona **Player (Lettore)**  > **XR Settings** (Impostazioni XR), fai clic sull'icona **+** e seleziona Windows Mixed Reality per aggiungere Windows Mixed Reality SDK:

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-2.png)

Al termine dell'importazione di Windows Mixed Reality SDK, dovrebbe visualizzarsi di nuovo la finestra MRTK Project Configurator (Configuratore del progetto MRTK). In caso contrario, usa il menu di Unity per aprirla.

Nella finestra MRTK Project Configurator (Configuratore del progetto MRTK) usa l'elenco a discesa **Audio spatializer** (Spazializzatore audio) per selezionare **MS HRTF Spatializer** e quindi fai clic sul pulsante **Apply** (Applica) per applicare l'impostazione:

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-3.png)

Nella finestra Project Settings (Impostazioni progetto) seleziona **Player (Lettore)**  > **XR Settings** (Impostazioni XR) e quindi usa l'elenco a discesa **Depth Format** (Formato profondità) per selezionare **16-bit depth** (Profondità a 16 bit):

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-4.png)

Nella finestra Project Settings (Impostazioni progetto) seleziona **Player (Lettore)**  > **Publishing Settings** (Impostazioni di pubblicazione) e quindi nel campo **Package name** (Nome del pacchetto) immetti un nome appropriato, ad esempio _MRTKTutorials-GettingStarted_:

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-5.png)

> [!NOTE]
> Il valore di 'Package name' (Nome del pacchetto) è l'identificatore univoco dell'app. Modifica questo identificatore prima di distribuire l'app per evitare di sovrascrivere app installate in precedenza.

> [!TIP]
> Il valore di 'Product Name' (Nome del prodotto) è il nome visualizzato nel menu di avvio di HoloLens. Per semplificare l'individuazione dell'app durante lo sviluppo, anteponi un carattere di sottolineatura al nome in modo che compaia all'inizio dell'elenco.

## <a name="creating-and-configuring-the-scene"></a>Creazione e configurazione della scena

Scegli **File** > **New Scene** (Nuova scena) dal menu di Unity per creare una nuova scena:

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-1.png)

Scegli **Mixed Reality Toolkit** > **Add to Scene and Configure...** (Aggiungi alla scena e configura) dal menu di Unity per aggiungere MRTK alla scena corrente:

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-2.png)

Con l'oggetto **MixedRealityToolkit** selezionato nella finestra Hierarchy (Gerarchia), nella finestra Inspector (Controllo) verifica che il profilo di configurazione di **Mixed Reality Toolkit** sia impostato su **DefaultMixedRealityToolkitConfigurationProfile**:

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-3.png)

> [!IMPORTANT]
> Durante le attività di sviluppo per HoloLens viene usato in genere DefaultHoloLens2ConfigurationProfile. Per questa esercitazione tuttavia userai DefaultMixedRealityToolkitConfigurationProfile, mentre nell'esercitazione successiva, [Configurazione dei profili di MRTK](mr-learning-base-03.md), passerai a DefaultHoloLens2ConfigurationProfile.

Dal menu di Unity scegli **File** > **Save As** (Salva con nome) per visualizzare la finestra Save Scene (Salva la scena):

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-4.png)

Nella finestra Save Scene (Salva la scena) passa alla cartella **Scenes** (Scene) del progetto, assegna alla scena un nome appropriato, ad esempio _GettingStarted_, e fai clic sul pulsante **Save** (Salva) per salvare la scena:

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="building-your-application-to-your-hololens-2"></a>Compilazione dell'applicazione nel dispositivo HoloLens 2

### <a name="1-build-the-unity-project"></a>1. Compilare il progetto Unity

Dal menu di Unity scegli **File** > **Build Settings** (Impostazioni di compilazione) per visualizzare la finestra corrispondente.

Nella finestra Build Settings (Impostazioni di compilazione), fai clic sul pulsante **Add Open Scenes** (Aggiungi scene aperte) per aggiungere la scena corrente all'elenco **Scenes In Build** (Scene in compilazione) e quindi fai clic sul pulsante **Build** (Compila) per visualizzare la finestra Build Universal Windows Platform (Compilazione UWP):

![mr-learning-base](images/mr-learning-base/base-02-section7-step1-1.png)

Nella finestra Build Universal Windows Platform (Compilazione UWP), scegli un percorso appropriato in cui archiviare la compilazione, ad esempio _D:\MixedRealityLearning\Builds_, crea una nuova cartella e assegnale un nome adatto (ad esempio, _GettingStarted_) e quindi fai clic sul pulsante **Select Folder** (Seleziona cartella) per avviare il processo di compilazione:

![mr-learning-base](images/mr-learning-base/base-02-section7-step1-2.png)

Attendi che Unity completi il processo di compilazione:

![mr-learning-base](images/mr-learning-base/base-02-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a>2. Compilare e distribuire l'applicazione

Al termine del processo di compilazione, Unity richiederà a Esplora file di Windows di aprire il percorso in cui è stata archiviata la compilazione. Spostati all'interno della cartella e fai doppio clic sul file della soluzione per aprirlo in Visual Studio:

![mr-learning-base](images/mr-learning-base/base-02-section8-step1-1.png)

> [!NOTE]
> Se Visual Studio chiede di installare nuovi componenti, dedica qualche minuto a verificare di disporre di tutti i componenti indispensabili come specificato nella documentazione **[Installare gli strumenti](install-the-tools.md)** .

Configura Visual Studio per HoloLens selezionando la configurazione **Master** o **Release**, l'architettura **ARM64** e **Dispositivo** come destinazione:

![mr-learning-base](images/mr-learning-base/base-02-section8-step1-2.png)

> [!TIP]
> Se esegui la distribuzione in HoloLens (1a generazione), seleziona l'architettura **x86**.

> [!NOTE]
> Per HoloLens, in genere la compilazione viene eseguita per l'architettura ARM. Esiste tuttavia un <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>problema noto</strong></a> in Unity 2019.3 che causa errori quando viene selezionata l'architettura di compilazione ARM in Visual Studio. La soluzione consigliata consiste nel compilare per ARM64. Se questa opzione non è applicabile, passa a **Modifica > Impostazioni progetto > Player (Lettore) > Altre impostazioni** e disabilita **Graphics Jobs** (Processi grafici).

> [!NOTE]
> Se non viene visualizzata l'opzione Dispositivo come destinazione, potresti dover modificare il progetto di avvio per la soluzione di Visual Studio passando dal progetto IL2CPP al progetto UWP. A tale scopo, in Esplora soluzioni fai clic con il pulsante destro del mouse su NomeProgetto (Windows universale) e scegli **Imposta come progetto di avvio**.

Connetti HoloLens al computer e quindi seleziona **Debug** > **Avvia senza eseguire il debug** per eseguire la compilazione e la distribuzione nel dispositivo:

![mr-learning-base](images/mr-learning-base/base-02-section8-step1-3.png)

> [!IMPORTANT]
> Prima della compilazione nel dispositivo, quest'ultimo deve essere in modalità sviluppatore e associato al computer di sviluppo. Per completare i due passaggi segui [queste istruzioni](using-visual-studio.md).

> [!TIP]
> Puoi anche eseguire la distribuzione nell'[emulatore HoloLens](using-the-hololens-emulator.md) o creare un [Pacchetto applicazione](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) per il sideload.

Usando Avvia senza eseguire il debug, l'app viene avviata nel dispositivo senza collegare il debugger di Visual Studio.

Seleziona **Compila > Distribuisci soluzione** per eseguire la distribuzione nel dispositivo senza che l'app venga avviata automaticamente.

> [!NOTE]
>Potrebbe essere visibile nell'app il profiler di diagnostica, che può essere attivato o disattivato tramite il comando vocale **Toggle Diagnostics** (Attiva/Disattiva diagnostica). È consigliabile mantenere visibile il profiler la maggior parte del tempo durante lo sviluppo per verificare quando le modifiche apportate all'app possono produrre effetti negativi sulle prestazioni. Le app HoloLens ad esempio devono [essere eseguite costantemente a 60 FPS](understanding-performance-for-mixed-reality.md).

## <a name="congratulations"></a>Lezione completata

A questo punto hai distribuito la tua prima app per HoloLens. Esplorando, noterai una mesh di mapping spaziale che copre le superfici percepite da HoloLens. Dovresti anche vedere indicatori sulle mani e sulle dita per il tracciamento delle mani e un contatore della frequenza dei fotogrammi per tenere sotto controllo le prestazioni dell'app. Queste funzionalità sono solo alcune delle parti fondamentali incluse in MRTK. Nelle esercitazioni successive aggiungerai contenuto alla scena per esplorare le funzionalità di HoloLens e MRTK.

[Esercitazione successiva: 3. Configurazione dei profili di MRTK](mr-learning-base-03.md)

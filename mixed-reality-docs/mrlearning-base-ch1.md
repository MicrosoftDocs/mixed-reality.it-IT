---
title: Esercitazioni introduttive-2. Inizializzazione del progetto e della prima applicazione
description: Completa questo corso per apprendere come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 11/01/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 3bf218b42ea8abed45a80c0dd048e791cdd8372b
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926892"
---
# <a name="2-initializing-your-project-and-first-application"></a>2. inizializzazione del progetto e della prima applicazione

Questa prima lezione illustra alcune delle funzionalità offerte dal [Toolkit di realtà mista (MRTK)]() , avvia la prima applicazione per HoloLens 2 e la distribuisce al dispositivo.

## <a name="objectives"></a>Obiettivi

* Ottimizzare Unity per lo sviluppo di HoloLens.
* Importare gli asset e configurare la scena.
* Visualizzazione del reticolo di mapping spaziale, mesh della mano e del contatore framerate.

## <a name="instructions"></a>Istruzioni

### <a name="create-new-unity-project"></a>Creare un nuovo progetto Unity

1. Avvia Unity.
2. Seleziona **New** (Nuovo).
![dalla lezione 1 sezione1](images/mrlearning-base-ch1-1-step2.JPG) 2

3. Immettere un nome di progetto, ad esempio "MixedRealityBase".
![dalla lezione 1 sezione1 passaggio 3](images/mrlearning-base-ch1-1-step3.JPG)
4. Immetti il percorso in cui salvare il progetto.
![dalla lezione 1 sezione1 passo 4](images/mrlearning-base-ch1-1-step4.JPG)
5. Assicurati che il progetto sia impostato su **3D**.
![dalla lezione 1 sezione1 passaggio 5](images/mrlearning-base-ch1-1-step5.JPG)
6. Fai clic su **Create Project** (Crea progetto).
![dalla lezione 1 sezione1 passaggio 6](images/mrlearning-base-ch1-1-step6.JPG)


### <a name="configure-the-unity-project-for-windows-mixed-reality"></a>Configurare il progetto Unity per Windows Mixed Reality

1. Aprire la finestra *impostazioni di compilazione* passando a **file** > **impostazioni di compilazione**.
![dalla lezione 1 sezione2 Step1](images/mrlearning-base-ch1-2-step1.JPG)
2. Selezionare il *piattaforma UWP (Universal Windows Platform)* e fare clic sul pulsante **Switch Platform (Cambia piattaforma** ) per cambiare le piattaforme. È necessario che le applicazioni in esecuzione in HoloLens 2 siano piattaforma UWP (Universal Windows Platform) (UWP) compatibili.
![dalla lezione 1 sezione2](images/mrlearning-base-ch1-2-step2.JPG) 2
3. Abilitare la realtà virtuale facendo clic sul pulsante **Impostazioni lettore** nella finestra di compilazione e abilitare la casella di controllo *realtà virtuale supportata* in impostazioni XR dal pannello di controllo, come illustrato nell'immagine seguente. Si noti che potrebbe essere necessario trascinare la finestra *impostazioni di compilazione* fuori dalla modalità per visualizzare il pannello del controllo. La casella di controllo *Virtual Reality supported* è applicabile anche a realtà mista e auricolari per la realtà aumentata, perché si riferisce all'abilitazione della visione stereoscopica (rendering di immagini diverse per ogni occhio) ![dalla lezione 1 sezione2 passaggio 3](images/mrlearning-base-ch1-2-step3.JPG)
4. Inoltre, in impostazioni XR, modificare la *modalità di rendering stereo* in *Single Pass istanza*. Questo [stile della pipeline di rendering](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) è in genere più efficiente per HoloLens 2. Se si è interessati ad altre configurazioni ad alte prestazioni per l'ambiente Unity, seguire [queste istruzioni](recommended-settings-for-unity.md).
![dalla lezione 1 sezione2 passo 4](images/mrlearning-base-ch1-2-step4.jpg)
5. Dallo stesso pannello di controllo verificare che la casella di controllo *percezione spaziale* nella sezione funzionalità sia abilitata in *impostazioni di pubblicazione*. La percezione spaziale consente di visualizzare la mesh di mapping spaziale in un dispositivo di realtà mista, ad esempio HoloLens 2. Le impostazioni di pubblicazione si trovano nel pannello Inspector, sopra le impostazioni di XR e in altre impostazioni.
![dalla lezione 1 sezione2 passaggio 5](images/mrlearning-base-ch1-2-step5.JPG)

    > [!NOTE]
    > Sebbene non venga usato in questa sezione, altre funzionalità comuni che è possibile abilitare includono il *microfono* per i comandi vocali e *internetClient* per la connessione ai servizi che richiedono una connessione di rete.

### <a name="import-the-mixed-reality-toolkit"></a>Importare Mixed Reality Toolkit

1. Scaricare la versione del pacchetto di [reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) Unity [Foundation 2.1.0](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage) e salvarla in una cartella del computer.

2. Importare il pacchetto del Toolkit per la *realtà mista* scaricato nel passaggio precedente. Per iniziare, fare clic su **asset** > **Importa** > **pacchetto personalizzato** e selezionare *Microsoft. MixedReality. Toolkit. Unity. Foundation. 2.1.0. file unitypackage Tools* e aprirlo per avviare il processo di importazione. Attendere alcuni minuti per il completamento del processo di importazione.
    ![dalla lezione 1 sezione3 2a](images/mrlearning-base-ch1-3-step2a.JPG) ![dalla lezione 1 sezione3 Step2b](images/mrlearning-base-ch1-3-step2b.JPG)

3. Nella finestra popup successiva fare clic su **Importa** per iniziare a importare il pacchetto selezionato nel progetto Unity. Verificare che tutti gli elementi siano controllati come illustrato nell'immagine.
    ![dalla lezione 1 sezione3 passaggio 3](images/mrlearning-base-ch1-3-step3.JPG)

    > [!NOTE]
    > Se viene visualizzata una finestra di dialogo popup in cui viene chiesto di applicare le impostazioni predefinite del Toolkit di realtà mista, fare clic su **applica**. MRTK analizza il progetto per le impostazioni consigliate mancanti quando viene importato per l'installazione automatica. A seconda delle impostazioni, il popup potrebbe essere diverso dall'immagine seguente.

    ![Dalla lezione 1 sezione3 passo 4 Note1](images/mrlearning-base-ch1-3-step4-note1.JPG)

### <a name="configure-the-mixed-reality-toolkit"></a>Configurare Mixed Reality Toolkit

1. Aggiungere il *Toolkit di realtà mista* alla scena corrente selezionando il **Toolkit di realtà mista** > **Aggiungi alla scena e configura..** dalla barra dei menu. Se dopo l'importazione di Mixed Reality Toolkit questa voce di menu non è visibile, riavvia Unity.
    ![dalla lezione 1 Section4 Step1](images/mrlearning-base-ch1-4-step1.JPG)

    > [!NOTE]
    > È possibile che venga visualizzata una finestra di dialogo popup per la selezione di un [profilo per il Toolkit di realtà mista](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html). Scegliere il profilo denominato *DefaultHoloLens2ConfigurationProfile* facendo doppio clic su di esso.

2. La scena avrà diversi nuovi elementi e modifiche. Salvare la scena con un nome diverso facendo clic su **File** > **Salva con nome...** e assegnare un nome alla scena, ad esempio *BaseScene*. Per organizzare la scena, salvarla nella cartella *Scenes* nella cartella *assets* del progetto.
    ![dalla lezione 1 Section4 2a](images/mrlearning-base-ch1-4-step2a.JPG) ![dalla lezione 1 Section4 Step2b](images/mrlearning-base-ch1-4-step2b.JPG)

### <a name="build-your-application-to-your-device"></a>Compilare l'applicazione nel dispositivo

1. Se è stata chiusa la finestra *impostazioni di compilazione* dalle sezioni precedenti, aprire nuovamente la finestra *impostazioni di compilazione* passando a **file** > **impostazioni di compilazione**.
    ![dalla lezione 1 Section5 Step1](images/mrlearning-base-ch1-5-step1.JPG)

2. Assicurarsi che la scena appena creata si trovi nell'elenco *scene in Build* facendo clic sul pulsante **Aggiungi scene aperte** mentre la scena è aperta in Unity.

3. Premere il pulsante **Compila** per avviare il processo di compilazione.
    ![dalla lezione 1 Section5 passaggio 3](images/mrlearning-base-ch1-5-step3.JPG)

4. Crea una nuova cartella per l'applicazione e assegna un nome alla cartella creata. Nell'immagine seguente è stata creata una cartella con l'app nome per contenere l'applicazione. Fare clic su **Seleziona cartella** per iniziare a compilare la cartella appena creata. Al termine della compilazione, è possibile chiudere la finestra *impostazioni di compilazione* in Unity.
    ![dalla lezione 1 Section5 passo 4](images/mrlearning-base-ch1-5-step4.JPG)

  > [!IMPORTANT]
  > se la compilazione ha esito negativo, prova a ripeterla o a riavviare Unity e a ripetere la compilazione. Se viene visualizzato un errore, ad esempio "errore: CS0246 = Impossibile trovare il tipo o il nome dello spazio dei nomi" XX "(manca una direttiva using o un riferimento a un assembly?). In tal caso, potrebbe essere necessario installare [Windows 10 SDK (10.0.18362.0)](https://developer.microsoft.com//windows/downloads/windows-10-sdk)

5. Al termine della compilazione, apri la nuova cartella creata che contiene i file dell'applicazione appena compilata. Fare doppio clic sulla soluzione *MixedRealityBase. sln* o sul nome corrispondente se è stato usato un nome alternativo per il progetto, per aprire il file della soluzione in Visual Studio.

    > [!NOTE]
    > Assicurarsi di aprire la cartella appena creata (ovvero la cartella dell' *app* , se si seguono le convenzioni di denominazione dei passaggi precedenti), perché sarà presente un file con estensione sln analogo al di fuori della cartella che non deve essere confusa con il file con estensione sln all'interno della cartella di compilazione. La struttura di cartelle dovrebbe essere simile all'immagine seguente.
    >
    > se Visual Studio richiede di installare nuovi componenti, dedica qualche minuto per verificare che tutti i componenti prerequisiti siano installati come specificato nella pagina ["Installare gli strumenti"](install-the-tools.md)

    ![Dalla lezione 1 Section5 passaggio 5](images/mrlearning-base-ch1-5-step5.JPG)

6. Connettere HoloLens 2 nel PC. Queste istruzioni presuppongono che si distribuirà in un dispositivo HoloLens 2, è anche possibile scegliere di eseguire la distribuzione nell' [emulatore HoloLens 2](using-the-hololens-emulator.md) o scegliere di creare un [pacchetto dell'app per sideload](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)

    > [!IMPORTANT]
    > Prima di creare il dispositivo, il dispositivo deve essere in *modalità sviluppatore* e associato al computer di sviluppo. È possibile completare entrambi i passaggi seguendo [queste istruzioni](using-visual-studio.md)

7. Configurare Visual Studio per la compilazione in HoloLens 2 selezionando la *versione* o la configurazione *Master* , l'architettura *ARM* e il *dispositivo* come destinazione.
    ![dalla lezione 1 Section5 Step8](images/mrlearning-base-ch1-5-step7.JPG)

8. Il passaggio finale consiste nel compilare e distribuire nel dispositivo selezionando **Debug** > **Avvia senza eseguire debug**. Se si seleziona *Avvia senza eseguire debug* , l'applicazione viene avviata immediatamente sul dispositivo dopo una compilazione riuscita, ma senza il debugger collegato e le informazioni visualizzate in Visual Studio. Questo significa anche che, mentre l'applicazione è in esecuzione sul dispositivo HoloLens 2, puoi disconnettere il cavo USB senza arrestare l'applicazione.

    > [!NOTE]
    > È anche possibile selezionare **compila** > **Distribuisci soluzione** per eseguire la distribuzione nel dispositivo senza che l'applicazione venga avviata automaticamente.

    ![Dalla lezione 1 Section5 Step9](images/mrlearning-base-ch1-5-step8.JPG)

## <a name="congratulations"></a>Lezione completata

A questo punto è stata distribuita la prima applicazione HoloLens 2. Quando si procede in questo modo, viene visualizzata una mesh di mapping spaziale che copre tutte le superfici percepite da HoloLens 2. Inoltre, dovrebbero essere visualizzati indicatori sulle mani e sulle dita per il rilevamento manuale e un contatore della frequenza dei fotogrammi per tenere sotto controllo le prestazioni dell'applicazione. Questi sono solo alcuni degli elementi fondamentali, inclusi per impostazione predefinita in Mixed Reality Toolkit. Nelle lezioni per iniziare, si inizierà ad aggiungere altro contenuto e interattività alla scena, in modo da poter esplorare completamente le funzionalità di HoloLens 2 e il Toolkit di realtà mista.

> [!NOTE]
> Nell'app è possibile notare Visual Profiler. Si tratterà come impostare il contatore della frequenza dei fotogrammi usando un comando vocale nella [lezione 5](mrlearning-base-ch5.md). È in genere consigliabile tenere sempre visibile il profiler di Visual Profiler durante lo sviluppo per comprendere quando le modifiche del codice potrebbero avere conseguenze sulle prestazioni. L'applicazione HoloLens 2 deve essere [eseguita in modo continuo a 60 fps](understanding-performance-for-mixed-reality.md).

[Lezione successiva: 3. creazione dell'interfaccia utente e configurazione del Toolkit per la realtà mista](mrlearning-base-ch2.md)

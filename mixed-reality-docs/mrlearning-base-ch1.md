---
title: Esercitazioni introduttive - 2 Inizializzazione del progetto e prima applicazione
description: Completa questo corso per informazioni su come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 11/01/2019
ms.topic: article
ms.localizationpriority: high
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: d4e58e2c9236ba35b4394fd80cde3843edaa6f57
ms.sourcegitcommit: 4d43a8f40e3132605cee9ece9229e67d985db645
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491207"
---
# <a name="2-initializing-your-project-and-first-application"></a>2. Inizializzazione del progetto e prima applicazione

In questa prima lezione apprenderai alcune delle funzionalità offerte da [Mixed Reality Toolkit (MRTK)](), inizierai a creare la tua prima applicazione per HoloLens 2 e la distribuirai nel dispositivo.

## <a name="objectives"></a>Obiettivi

* Ottimizzare Unity per lo sviluppo di HoloLens.
* Importare gli asset e configurare la scena.
* Visualizzare la mesh di mapping spaziale, le mesh manuali e il contatore della frequenza dei fotogrammi.

## <a name="instructions"></a>Istruzioni

### <a name="create-new-unity-project"></a>Creare un nuovo progetto Unity

1. Avvia Unity.
2. Seleziona **New** (Nuovo).
![Lezione 1 - Sezione 1 - Passaggio 2](images/mrlearning-base-ch1-1-step2.JPG)

3. Immetti un nome di progetto, ad esempio "MixedRealityBase".
![Lezione 1 - Sezione 1 - Passaggio 3](images/mrlearning-base-ch1-1-step3.JPG)
4. Immetti il percorso in cui salvare il progetto.
![Lezione 1 - Sezione 1 - Passaggio 4](images/mrlearning-base-ch1-1-step4.JPG)
5. Assicurati che il progetto sia impostato su **3D**.
![Lezione 1 - Sezione 1 - Passaggio 5](images/mrlearning-base-ch1-1-step5.JPG)
6. Fai clic su **Create Project** (Crea progetto).
![Lezione 1 - Sezione 1 - Passaggio 6](images/mrlearning-base-ch1-1-step6.JPG)


### <a name="configure-the-unity-project-for-windows-mixed-reality"></a>Configurare il progetto Unity per Windows Mixed Reality

1. Apri la finestra *Build Settings* (Impostazioni di compilazione) selezionando **File** > **Build Settings** (File>Impostazioni di compilazione).
![Lezione 1 - Sezione 2 - Passaggio 1](images/mrlearning-base-ch1-2-step1.JPG)
2. Seleziona *Universal Windows Platform* e fai clic sul pulsante **Switch Platform** (Cambia piattaforma) per cambiare piattaforma. Le applicazioni in esecuzione su HoloLens 2 devono essere compatibili con la piattaforma UWP (Universal Windows Platform).
![Lezione 1 - Sezione 2 - Passaggio 2](images/mrlearning-base-ch1-2-step2.JPG)
3. Abilita la realtà virtuale facendo clic sul pulsante **Player Settings** (Impostazioni lettore) nella finestra Build Settings (Impostazioni di compilazione) e quindi abilita la casella di controllo *Virtual Reality Supported* (Realtà virtuale supportata) in XR Settings (Impostazioni XR) dal pannello di controllo, come illustrato nell'immagine seguente. Tieni presente che per visualizzare il pannello di controllo può essere utile spostare la finestra *Build Settings* (Impostazioni di compilazione). La casella di controllo *Virtual Reality Supported* (Realtà virtuale supportata) si applica anche ai visori VR di realtà mista e realtà aumentata perché fa riferimento all'abilitazione della visione stereoscopica (con il rendering di immagini diverse per ogni occhio). ![Lezione 1 - Sezione 2 - Passaggio 3](images/mrlearning-base-ch1-2-step3.JPG)
4. Sempre in XR Settings (Impostazioni XR), modifica l'impostazione di *Stereo Rendering Mode* (Modalità di rendering stereo) selezionando *Single Pass Instanced* (Con istanze a passaggio singolo). Questo [stile della pipeline di rendering](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) è in genere il più efficiente per HoloLens 2. Se ti interessano altre configurazioni con ottime prestazioni per l'ambiente Unity, segui [queste istruzioni](recommended-settings-for-unity.md).
![Lezione 1 - Sezione 2 - Passaggio 4](images/mrlearning-base-ch1-2-step4.jpg)
5. Dallo stesso pannello di controllo verifica che la casella di controllo *Spatial Perception* (Percezione spaziale) nella sezione Capabilities (Funzionalità) in *Publishing Settings* (Impostazioni di pubblicazione) sia abilitata. Spatial Perception (Percezione spaziale) ci consentirà di visualizzare la mesh di mapping spaziale in un dispositivo di realtà mista come HoloLens 2. Le impostazioni di pubblicazione sono disponibili nel pannello di controllo, sopra XR Settings (Impostazioni XR) e sotto Other Settings (Altre impostazioni).
![Lezione 1 - Sezione 2 - Passaggio 5](images/mrlearning-base-ch1-2-step5.JPG)

    > [!NOTE]
    > Anche se non vengono usate in questa sezione, tra le altre funzionalità comuni che puoi attivare sono presenti *Microphone* (Microfono) per i comandi vocali e *InternetClient* per la connessione a servizi che richiedono una connessione di rete.

### <a name="import-the-mixed-reality-toolkit"></a>Importare Mixed Reality Toolkit

1. Scarica il [pacchetto della versione 2.1.0](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage) di [Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) Unity Foundation e salvalo in una cartella nel PC.

2. Importa il pacchetto di *Mixed Reality Toolkit* scaricato nel passaggio precedente. Per iniziare, fai clic su **Assets** > **Import** > **Custom Package** (Asset>Importa pacchetto>Pacchetto personalizzato), seleziona *Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage* e apri il pacchetto per avviare il processo di importazione. Attendi alcuni minuti che il processo di importazione sia completato.
    ![Lezione 1 - Sezione 3 - Passaggio 2a](images/mrlearning-base-ch1-3-step2a.JPG) ![Lezione 1 - Sezione 3 - Passaggio 2b](images/mrlearning-base-ch1-3-step2b.JPG)

3. Nella finestra popup successiva fai clic su **Import** (Importa) per avviare l'importazione del pacchetto selezionato nel progetto Unity. Assicurati che tutti gli elementi siano selezionati, come illustrato nell'immagine.
    ![Lezione 1 - Sezione 3 - Passaggio 3](images/mrlearning-base-ch1-3-step3.JPG)

    > [!NOTE]
    > Se vedi una finestra di dialogo popup con la richiesta di applicare le impostazioni predefinite di Mixed Reality Toolkit, fai clic su **Apply** (Applica). MRTK analizza il progetto per individuare le eventuali impostazioni consigliate mancanti durante l'importazione per l'installazione automatica. A seconda delle impostazioni, la finestra popup potrebbe essere diversa dall'immagine seguente.

    ![Lezione 1 - Sezione 3 - Passaggio 4 - Nota 1](images/mrlearning-base-ch1-3-step4-note1.JPG)

### <a name="configure-the-mixed-reality-toolkit"></a>Configurare Mixed Reality Toolkit

1. Aggiungi *Mixed Reality Toolkit* alla scena corrente selezionando **Mixed Reality Toolkit** > **Add to Scene and Configure** (Aggiungi alla scena e configura) dalla barra dei menu. Se dopo l'importazione di Mixed Reality Toolkit questa voce di menu non è visibile, riavvia Unity.
    ![Lezione 1 - Sezione 4 - Passaggio 1](images/mrlearning-base-ch1-4-step1.JPG)

    > [!NOTE]
    > È possibile che venga visualizzata una finestra di dialogo popup per la selezione di un [profilo per Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html). Scegli il profilo denominato *DefaultHoloLens2ConfigurationProfile* facendo doppio clic su di esso.

2. Nella scena saranno presenti alcuni nuovi elementi e modifiche. Salva la scena con un nome diverso facendo clic su **File** > **Save As** (File>Salva con nome) e specificando un nome, ad esempio *BaseScene*. Mantieni la scena organizzata salvandola nella cartella *Scenes* all'interno della cartella *Assets* del progetto.
    ![Lezione 1 - Sezione 4 - Passaggio 2a](images/mrlearning-base-ch1-4-step2a.JPG) ![Lezione 1 - Sezione 4 - Passaggio 2b](images/mrlearning-base-ch1-4-step2b.JPG)

### <a name="build-your-application-to-your-device"></a>Compilare l'applicazione nel dispositivo

1. Se nelle sezioni precedenti hai chiuso la finestra *Build Settings* (Impostazioni di compilazione), apri nuovamente la finestra **  selezionando **File** > **Build Settings** (File>Impostazioni di compilazione).
    ![Lezione 1 - Sezione 5 - Passaggio 1](images/mrlearning-base-ch1-5-step1.JPG)

2. Assicurati che la scena che hai appena creato sia inclusa nell'elenco *Scenes in Build* (Scene nella compilazione) facendo clic sul pulsante **Add Open Scenes** (Aggiungi scene aperte) mentre la scena è aperta in Unity.

3. Scegli il pulsante **Build** (Compila) per avviare il processo di compilazione.
    ![Lezione 1 - Sezione 5 - Passaggio 3](images/mrlearning-base-ch1-5-step3.JPG)

4. Crea una nuova cartella per l'applicazione e assegna un nome alla cartella creata. Nell'immagine seguente è stata creata una cartella con il nome App per contenere l'applicazione. Fai clic su **Select Folder** (Seleziona cartella) per iniziare la compilazione nella cartella appena creata. Al termine della compilazione, puoi chiudere la finestra *Build Settings* (Impostazioni di compilazione) in Unity.
    ![Lezione 1 - Sezione 5 - Passaggio 4](images/mrlearning-base-ch1-5-step4.JPG)

  > [!IMPORTANT]
  > se la compilazione ha esito negativo, prova a ripeterla o a riavviare Unity e a ripetere la compilazione. Se viene restituito un errore simile al seguente: "Errore CS0246 = Non è possibile trovare il tipo o il nome dello spazio dei nomi "XX" (direttiva using o riferimento ad assembly mancante?)" può essere necessario installare [Windows 10 SDK (10.0.18362.0)](https://developer.microsoft.com//windows/downloads/windows-10-sdk)

5. Al termine della compilazione, apri la nuova cartella creata che contiene i file dell'applicazione appena compilata. Fai doppio clic sulla soluzione *MixedRealityBase.sln* o sul nome corrispondente, se hai usato un nome alternativo per il progetto, per aprire il file della soluzione in Visual Studio.

    > [!NOTE]
    > Assicurati di aprire la cartella appena creata (ad esempio la cartella *App*, se hai seguito le convenzioni di denominazione dei passaggi precedenti) perché un file con estensione sln e un nome analogo sarà presente al di fuori di tale cartella e non devi confonderlo quello che si trova all'interno della cartella di compilazione. La struttura di cartelle dovrebbe avere un aspetto simile al seguente.
    >
    > se Visual Studio richiede di installare nuovi componenti, dedica qualche minuto per verificare che tutti i componenti prerequisiti siano installati come specificato nella pagina ["Installare gli strumenti"](install-the-tools.md)

    ![Lezione 1 - Sezione 5 - Passaggio 5](images/mrlearning-base-ch1-5-step5.JPG)

6. Connetti il dispositivo HoloLens 2 al PC. Anche se queste istruzioni presuppongono che tu distribuisca l'applicazione in un dispositivo HoloLens 2, puoi anche scegliere di distribuirla nell'[emulatore HoloLens 2](using-the-hololens-emulator.md) oppure creare un [pacchetto dell'applicazione per il sideload](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>).

    > [!IMPORTANT]
    > Prima della compilazione, il dispositivo deve essere in *Modalità sviluppatore* e associato al computer di sviluppo. Per completare i due passaggi segui [queste istruzioni](using-visual-studio.md).

7. Configura Visual Studio per la compilazione nel dispositivo HoloLens 2 selezionando la configurazione *Release* o *Master*, l'architettura *ARM* e *Device* (Dispositivo) come destinazione.
    ![Lezione 1 - Sezione 5 - Passaggio 8](images/mrlearning-base-ch1-5-step7.JPG)

8. Il passaggio finale consiste nel compilare e distribuire l'applicazione nel dispositivo selezionando **Debug** > **Avvia senza eseguire debug**. Se selezioni *Avvia senza eseguire debug*, l'applicazione viene avviata immediatamente nel dispositivo al termine della compilazione, ma senza il debugger associato e senza che in Visual Studio vengano visualizzate le informazioni di debug. Questo significa anche che, mentre l'applicazione è in esecuzione sul dispositivo HoloLens 2, puoi disconnettere il cavo USB senza arrestare l'applicazione.

    > [!NOTE]
    > Puoi anche selezionare **Compila** > **Distribuisci soluzione** per distribuire l'applicazione nel dispositivo senza che venga avviata automaticamente.

    ![Lezione 1 - Sezione 5 - Passaggio 9](images/mrlearning-base-ch1-5-step8.JPG)

## <a name="congratulations"></a>Lezione completata

A questo punto hai distribuito la tua prima applicazione per HoloLens 2. Esplorando, noterai una mesh di mapping spaziale che copre tutte le superfici percepite da HoloLens 2. Dovresti anche vedere indicatori sulle mani e sulle dita per il tracciamento delle mani e un contatore della frequenza dei fotogrammi per tenere sotto controllo le prestazioni dell'applicazione. Questi sono solo alcuni degli elementi fondamentali, inclusi per impostazione predefinita in Mixed Reality Toolkit. Nelle lezioni successive inizierai ad aggiungere più contenuti e interattività alla scena, in modo da poter esplorare completamente le funzionalità di HoloLens 2 e Mixed Reality Toolkit.

> [!NOTE]
> Nell'app potresti notare il profiler visuale. Nella [lezione 5](mrlearning-base-ch5.md) imparerai come attivare o disattivare il contatore della frequenza dei fotogrammi usando un comando vocale. È in genere consigliabile mantenere sempre visibile il profiler visuale durante lo sviluppo per comprendere quando le modifiche del codice possono avere conseguenze sulle prestazioni. L'applicazione HoloLens 2 deve essere [eseguita costantemente a 60 FPS](understanding-performance-for-mixed-reality.md).

[Lezione successiva: 3. Creazione dell'interfaccia utente e configurazione di Mixed Reality Toolkit](mrlearning-base-ch2.md)

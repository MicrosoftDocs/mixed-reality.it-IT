---
title: Modulo di apprendimento di base sulla realtà mista - Inizializzazione del progetto e prima applicazione
description: Completa questo corso per apprendere come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 51cfc123f7da8d25a53eecfb730f60cf10fe7377
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387789"
---
# <a name="2-initializing-your-project-and-first-application"></a>2. Inizializzazione del progetto e della prima applicazione

Questa prima lezione illustra alcune delle funzionalità offerte dal Toolkit di realtà mista (MRTK), avvia la prima applicazione per HoloLens 2 e la distribuisce al dispositivo.

## <a name="objectives"></a>Obiettivi

* Ottimizzare Unity per lo sviluppo di HoloLens.
* Importare gli asset e configurare la scena.
* Visualizzare la mesh spaziale, le mesh manuali e il contatore della frequenza dei fotogrammi.

## <a name="instructions"></a>Istruzioni

### <a name="create-new-unity-project"></a>Creare un nuovo progetto Unity

1. Avvia Unity.
2. Seleziona **New** (Nuovo).
![Lezione 1 capitolo 1 passaggio 2](images/Lesson1Chapter1Step2.JPG)
3. Immetti un nome di progetto, ad esempio "MixedRealityBase".
![Lezione 1 capitolo 1 passaggio 3](images/Lesson1Chapter1Step3.JPG)
4. Immetti il percorso in cui salvare il progetto.
![Lezione 1 capitolo 1 passaggio 4](images/Lesson1Chapter1Step4.JPG)
5. Assicurati che il progetto sia impostato su **3D**.
![Lezione 1 capitolo 1 passaggio 5](images/Lesson1Chapter1Step5.JPG)
6. Fai clic su **Create Project** (Crea progetto).
![Lezione 1 capitolo 1 passaggio 6](images/Lesson1Chapter1Step6.JPG)

### <a name="configure-the-unity-project-for-windows-mixed-reality"></a>Configurare il progetto Unity per Windows Mixed Reality

1. Aprire la finestra impostazioni di compilazione passando a file > impostazioni di compilazione.
![Lezione 1 capitolo 4 passaggio 1](images/Lesson1Chapter4Step1.JPG)
2. Passare a piattaforma UWP (Universal Windows Platform) selezionando piattaforma UWP (Universal Windows Platform). Fare clic sul pulsante switch Platform per cambiare le piattaforme. È necessario che le applicazioni in esecuzione in HoloLens 2 siano piattaforma UWP (Universal Windows Platform) (UWP) compatibili.
![Lezione 1 capitolo 4 passaggio 2](images/Lesson1Chapter4Step2.JPG)
3. Abilitare la realtà virtuale facendo clic su Impostazioni lettore nella finestra di compilazione e abilitare la casella di controllo realtà virtuale supportata in impostazioni XR dal pannello di controllo, come illustrato nell'immagine seguente. Si noti che potrebbe essere necessario trascinare la finestra impostazioni di compilazione fuori dalla modalità per visualizzare il pannello del controllo. La casella di controllo Virtual Reality supported è applicabile anche a realtà mista e auricolari per la realtà aumentata, perché si riferisce all'abilitazione della visione stereoscopica (rendering di immagini diverse per ogni occhio). ![Lezione 1 capitolo 4 passaggio 3](images/Lesson1Chapter4Step3.JPG)
4. Dallo stesso pannello di controllo verificare che la casella di controllo percezione spaziale nella sezione funzionalità sia abilitata in impostazioni di pubblicazione. La percezione spaziale consente di visualizzare la mesh di mapping spaziale in un dispositivo di realtà mista, ad esempio HoloLens 2. Le impostazioni di pubblicazione si trovano nel pannello Inspector, sopra le impostazioni di XR e in altre impostazioni.
![Lezione 1 capitolo 4 passaggio 4](images/Lesson1Chapter4Step4.JPG)

> NOTA: Sebbene non venga usato in questa sezione, altre funzionalità comuni che è possibile abilitare includono il microfono per i comandi vocali e InternetClient per la connessione ai servizi che richiedono una connessione di rete.

### <a name="import-the-mixed-reality-toolkit"></a>Importare Mixed Reality Toolkit

1. Scaricare il pacchetto [mixed reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC1.unitypackage) Unity e salvarlo in una cartella nel PC.

2. Importa il pacchetto Mixed Reality Toolkit facendo clic su Assets>Import Package>Custom Package (Asset>Importa pacchetto>Pacchetto personalizzato). Trova il pacchetto Mixed Reality Toolkit scaricato nel passaggio 1 e aprilo per iniziare il processo di importazione. Attendi alcuni minuti per il completamento del processo di importazione.
    ![Lezione 1 capitolo 2 passaggio 2a](images/Lesson1Chapter2Step2a.JPG) ![Lezione 1 capitolo 2 passaggio 2b](images/Lesson1Chapter2Step2b.JPG)

3. Nella finestra popup successiva fare clic su Importa per avviare l'importazione del Toolkit di realtà mista. Verificare che tutti gli elementi siano controllati come illustrato nell'immagine. Se viene visualizzata una finestra di dialogo popup in cui viene chiesto di applicare le impostazioni predefinite del Toolkit di realtà mista, fare clic su Applica.
    ![Lezione 1 capitolo 2 passaggio 3](images/Lesson1Chapter2Step3.JPG) ![Lezione 1 capitolo 2 passaggio 3](images/Lesson1Chapter2Step3b.JPG)

### <a name="configure-the-mixed-reality-toolkit"></a>Configurare Mixed Reality Toolkit

1. Configurare il MRTK selezionando il Toolkit di realtà misto > configurare dalla barra dei menu. Se dopo l'importazione di Mixed Reality Toolkit questa voce di menu non è visibile, riavvia Unity.
  ![Lezione 1 capitolo 3 passaggio 1](images/Lesson1Chapter3Step1.JPG)

  > Nota: È possibile che venga visualizzata una finestra di dialogo popup in cui viene chiesto di selezionare un profilo per il Toolkit di realtà mista. In tal caso, selezionare OK e scegliere il profilo denominato "DefaultMixedRealityToolkitConfigurationProfile".

2. La scena avrà diversi nuovi elementi e modifiche da MRTK. Salvare la scena con un nome diverso facendo clic su file > Salva con nome e assegnare un nome alla scena, ad esempio BaseScene. Per organizzare la scena, salvarla nella cartella Scenes nella cartella assets del progetto.
  ![Lezione 1 capitolo 3 passaggio 2a](images/Lesson1Chapter3Step2a.JPG)
  ![Lezione 1 capitolo 3 passaggio 2b](images/Lesson1Chapter3Step2b.JPG)

### <a name="build-your-application-to-your-device"></a>Compilare l'applicazione nel dispositivo

1. Se è stata chiusa la finestra impostazioni di compilazione dalle sezioni precedenti, aprire nuovamente la finestra impostazioni di compilazione passando a file > impostazioni di compilazione.
    ![Lezione 1 capitolo 5 passaggio 1](images/Lesson1Chapter5Step1.JPG)

2. Assicurarsi che la scena che si vuole provare si trovi nell'elenco scene in Build facendo clic sul pulsante Aggiungi scene aperte.

3. Scegli il pulsante Build (Compila) per avviare il processo di compilazione.
    ![Lezione 1 capitolo 5 passaggio 3](images/Lesson1Chapter5Step3.JPG)

4. Crea una nuova cartella per l'applicazione e assegna un nome alla cartella creata. Nell'immagine seguente è stata creata una cartella con l'app nome per contenere l'applicazione. Fare clic su Seleziona cartella per iniziare a compilare la cartella appena creata. Al termine della compilazione, è possibile chiudere la finestra impostazioni di compilazione in Unity. 
    ![Lezione 1 capitolo 5 passaggio 4](images/Lesson1Chapter5Step4.JPG)

  > NOTA: se la compilazione ha esito negativo, prova a ripeterla o a riavviare Unity e a ripetere la compilazione. Se viene visualizzato un errore, ad esempio "errore: CS0246 = Impossibile trovare il tipo o il nome dello spazio dei nomi "XX". manca una direttiva using o un riferimento a un assembly. In tal caso, potrebbe essere necessario installare [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)
  >

5. Al termine della compilazione, apri la nuova cartella creata che contiene i file dell'applicazione appena compilata. Fare doppio clic sulla soluzione MixedRealityBase. sln o sul nome corrispondente se è stato usato un nome alternativo per il progetto, per aprire il file della soluzione in Visual Studio.

  > Nota: Assicurarsi di aprire la cartella appena creata (ad esempio, la cartella dell'app, se si seguono le convenzioni di denominazione dei passaggi precedenti), perché sarà presente un file con estensione sln analogo al di fuori della cartella che non deve essere confusa con il file con estensione sln all'interno della cartella di compilazione. 

![Lezione 1 capitolo 5 passaggio 5](images/Lesson1Chapter5Step5.JPG)

  > Nota: se Visual Studio richiede di installare nuovi componenti, dedica qualche minuto per verificare che tutti i componenti prerequisiti siano installati come specificato nella pagina ["Installare gli strumenti"](install-the-tools.md)

6. Connettere HoloLens 2 nel PC. Sebbene queste istruzioni presuppongano che si stia distribuendo un test con un dispositivo HoloLens 2, è anche possibile scegliere di eseguire la distribuzione nell' [emulatore HoloLens 2](using-the-hololens-emulator.md) o scegliere di creare un [pacchetto dell'app per sideload](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)

7. Prima della compilazione, assicurati che il dispositivo sia in modalità sviluppatore. Se questa è la prima volta che si esegue la distribuzione in HoloLens 2, è possibile che in Visual Studio venga richiesto di associare HoloLens 2 a un PIN. Segui [queste istruzioni](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio) se devi abilitare la modalità sviluppatore o eseguire l'associazione con Visual Studio.

8. Configurare Visual Studio per la compilazione in HoloLens 2 selezionando la configurazione di rilascio e l'architettura ARM.
    ![Lezione 1 capitolo 5 passaggio 8](images/Lesson1Chapter5Step8.JPG)

9. Il passaggio finale consiste nel compilare nel dispositivo selezionando Debug > Avvia senza eseguire debug. Se si seleziona Avvia senza eseguire debug, l'applicazione viene avviata immediatamente sul dispositivo dopo una compilazione corretta, ma senza informazioni di debug visualizzate in Visual Studio. Questo significa anche che, mentre l'applicazione è in esecuzione sul dispositivo HoloLens 2, puoi disconnettere il cavo USB senza arrestare l'applicazione. È anche possibile selezionare Compila > Distribuisci soluzione per eseguire la distribuzione nel dispositivo senza che l'applicazione venga avviata automaticamente.
    ![Lezione 1 capitolo 5 passaggio 9](images/Lesson1Chapter5Step9.JPG)

## <a name="congratulations"></a>Lezione completata

A questo punto è stata distribuita la prima applicazione HoloLens 2. Quando si procede in questo modo, viene visualizzata una mesh spaziale che copre tutte le superfici percepite da HoloLens 2. Inoltre, dovrebbero essere visualizzati indicatori sulle mani e sulle dita per il rilevamento manuale e un contatore della frequenza dei fotogrammi per tenere sotto controllo le prestazioni dell'applicazione. Questi sono solo alcuni degli elementi fondamentali, inclusi per impostazione predefinita in Mixed Reality Toolkit. Nelle lezioni da iniziare, si inizia ad aggiungere altro contenuto e interattività alla scena, in modo da poter esplorare completamente le funzionalità di HoloLens 2 e il Toolkit di realtà mista.

>Nota: nella [lezione 5](mrlearning-base-ch5.md) imparerai come attivare o disattivare il contatore della frequenza dei fotogrammi usando un comando vocale.

[Lezione successiva: Interfaccia utente, tracciamento delle mani e configurazione di Mixed Reality Toolkit](mrlearning-base-ch2.md)

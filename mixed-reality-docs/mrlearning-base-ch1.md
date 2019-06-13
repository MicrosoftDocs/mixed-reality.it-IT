---
title: Modulo di apprendimento di base sulla realtà mista - Inizializzazione del progetto e prima applicazione
description: Completa questo corso per apprendere come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: c5490e6a3b542a5ca677b309e5ed1171f8666fe7
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2019
ms.locfileid: "65814006"
---
# <a name="mr-learning-base-module---project-initialization-and-first-application"></a>Modulo di apprendimento di base sulla realtà mista - Inizializzazione del progetto e prima applicazione

In questa prima lezione apprenderai alcune delle funzionalità offerte da Mixed Reality Toolkit, avvierai la prima applicazione per HoloLens 2 e la distribuirai nel dispositivo.

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

1. Apri la finestra delle impostazioni di compilazione passando a File>Build Settings (File>Impostazioni di compilazione).
![Lezione 1 capitolo 4 passaggio 1](images/Lesson1Chapter4Step1.JPG)
2. Passa a "Piattaforma UWP" selezionando "Universal Windows Platform" e quindi fai clic sul pulsante "Switch Platform" (Cambia piattaforma) per passare da una piattaforma all'altra. Le app in esecuzione su HoloLens 2 devono essere compatibili con la piattaforma UWP.
![Lezione 1 capitolo 4 passaggio 2](images/Lesson1Chapter4Step2.JPG)
3. Abilita la realtà virtuale facendo clic su Player Settings (Impostazioni lettore) nella finestra Build Settings (Impostazioni di compilazione) e quindi nel pannello di controllo abilita la casella di controllo "Virtual Reality Supported" (Realtà virtuale supportata) in XR Settings (Impostazioni XR), come illustrato nell'immagine seguente. Tieni presente che può essere utile spostare la finestra "Build Settings" (Impostazioni di compilazione) per visualizzare il pannello di controllo. La casella di controllo "Virtual Reality Supported" (Realtà virtuale supportata) si applica anche ai visori VR di realtà mista/realtà aumentata perché fa riferimento all'abilitazione della visione stereoscopica (con il rendering di immagini diverse per ogni occhio). ![Lezione 1 capitolo 4 passaggio 3](images/Lesson1Chapter4Step3.JPG)
4. Nello stesso pannello di controllo verifica che la casella di controllo "Spatial Perception" (Percezione spaziale) nella sezione Capabilities (Funzionalità) in Publishing Settings (Impostazioni di pubblicazione) sia abilitata. Spatial Perception (Percezione spaziale) ci consentirà di visualizzare la mesh del mapping spaziale in un dispositivo di realtà mista come HoloLens 2. Le impostazioni di pubblicazione sono disponibili nel pannello di controllo, sopra "XR Settings" (Impostazioni XR) e sotto "Other Settings" (Altre impostazioni).
![Lezione 1 capitolo 4 passaggio 4](images/Lesson1Chapter4Step4.JPG)

> NOTA: anche se non vengono usate in questa sezione, tra le altre funzionalità comuni che puoi attivare sono presenti Microphone (Microfono) (per i comandi vocali) e InternetClient (per la connessione a servizi che richiedono una connessione di rete)

### <a name="import-the-mixed-reality-toolkit"></a>Importare Mixed Reality Toolkit

1. Scarica il pacchetto [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC1.unitypackage) per Unity e salvalo in una cartella nel PC.

2. Importa il pacchetto Mixed Reality Toolkit facendo clic su Assets>Import Package>Custom Package (Asset>Importa pacchetto>Pacchetto personalizzato). Trova il pacchetto Mixed Reality Toolkit scaricato nel passaggio 1 e aprilo per iniziare il processo di importazione. Attendi alcuni minuti per il completamento del processo di importazione.
    ![Lezione 1 capitolo 2 passaggio 2a](images/Lesson1Chapter2Step2a.JPG) ![Lezione 1 capitolo 2 passaggio 2b](images/Lesson1Chapter2Step2b.JPG)

3. Nella finestra popup successiva fai clic su "Import" (Importa) per avviare l'importazione di Mixed Reality Toolkit. Assicurati che tutti gli elementi siano selezionati, come illustrato nell'immagine. Se visualizzi una finestra di dialogo popup con la richiesta di applicare le impostazioni predefinite di Mixed Reality Toolkit, fai clic su "Apply" (Applica).
    ![Lezione 1 capitolo 2 passaggio 3](images/Lesson1Chapter2Step3.JPG) ![Lezione 1 capitolo 2 passaggio 3](images/Lesson1Chapter2Step3b.JPG)

### <a name="configure-the-mixed-reality-toolkit"></a>Configurare Mixed Reality Toolkit

1. Configura Mixed Reality Toolkit selezionando Mixed Reality Toolkit>Configure (Mixed Reality Toolkit>Configura) dalla barra dei menu. Se dopo l'importazione di Mixed Reality Toolkit questa voce di menu non è visibile, riavvia Unity.
![Lezione 1 capitolo 3 passaggio 1](images/Lesson1Chapter3Step1.JPG)
2. La scena conterrà ora alcuni nuovi elementi e modifiche provenienti da Mixed Reality Toolkit. Salva la scena con un nome diverso facendo clic su File>Save as (File>Salva con nome) e assegna un nome alla scena, ad esempio BaseScene. Mantieni la scena organizzata salvandola nella cartella "Scenes" all'interno della cartella Assets del progetto.
![Lezione 1 capitolo 3 passaggio 2a](images/Lesson1Chapter3Step2a.JPG)
![Lezione 1 capitolo 3 passaggio 2b](images/Lesson1Chapter3Step2b.JPG)

### <a name="build-your-application-to-your-device"></a>Compilare l'applicazione nel dispositivo

1. Se nelle sezioni precedenti hai chiuso la finestra Build Settings (Impostazioni di compilazione), aprila nuovamente passando a File>Build Settings (File>Impostazioni di compilazione).
    ![Lezione 1 capitolo 5 passaggio 1](images/Lesson1Chapter5Step1.JPG)

2. Assicurati che la scena che vuoi provare sia nell'elenco "Scenes in Build" (Scene nella compilazione) facendo clic sul pulsante "Add Open Scenes" (Aggiungi scene aperte).

3. Scegli il pulsante Build (Compila) per avviare il processo di compilazione.
    ![Lezione 1 capitolo 5 passaggio 3](images/Lesson1Chapter5Step3.JPG)

4. Crea una nuova cartella per l'applicazione e assegna un nome alla cartella creata. Nell'immagine seguente è stata creata una cartella con il nome "App" per contenere l'applicazione. Fai clic su "Select Folder" (Seleziona cartella) per iniziare la compilazione nella cartella appena creata. Al termine della compilazione, puoi chiudere la finestra "Build Settings" (Impostazioni di compilazione) in Unity. 
    ![Lezione 1 capitolo 5 passaggio 4](images/Lesson1Chapter5Step4.JPG)

  > NOTA: se la compilazione ha esito negativo, prova a ripeterla o a riavviare Unity e a ripetere la compilazione. Se visualizzi un errore simile al seguente: "Errore CS0246 = Non è possibile trovare il tipo o il nome dello spazio dei nomi "XX" (direttiva using o riferimento ad assembly mancante?)" può essere necessario installare [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)
  >

5. Al termine della compilazione, apri la nuova cartella creata che contiene i file dell'applicazione appena compilata. Fai doppio clic sulla soluzione "MixedRealityBase.sln" (o il nome corrispondente, se hai usato un nome alternativo per il progetto) per aprire il file della soluzione in Visual Studio.

  > Nota: assicurati di aprire la cartella appena creata (ad esempio la cartella "App", se hai seguito le convenzioni di denominazione dei passaggi precedenti) perché un file con estensione sln denominato in modo analogo sarà presente al di fuori di tale cartella e non devi confonderlo con il file con estensione sln all'interno della cartella di compilazione. 

![Lezione 1 capitolo 5 passaggio 5](images/Lesson1Chapter5Step5.JPG)

  > Nota: se Visual Studio richiede di installare nuovi componenti, dedica qualche minuto per verificare che tutti i componenti prerequisiti siano installati come specificato nella pagina ["Installare gli strumenti"](install-the-tools.md)

6. Collega HoloLens 2 al PC con il cavo USB. Anche se le istruzioni in questa lezione presuppongono che distribuirai un test con un dispositivo HoloLens 2, puoi anche scegliere di distribuire nell'[emulatore HoloLens 2](using-the-hololens-emulator.md) oppure di creare un [pacchetto dell'app per il trasferimento locale](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>).

7. Prima della compilazione, assicurati che il dispositivo sia in modalità sviluppatore. Se questa è la prima volta che esegui la distribuzione nel dispositivo HoloLens 2, Visual Studio può richiedere di associare HoloLens 2 a un PIN. Segui [queste istruzioni](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio) se devi abilitare la modalità sviluppatore o eseguire l'associazione con Visual Studio.

8. Configura Visual Studio per la compilazione nel dispositivo HoloLens 2 selezionando la configurazione "Release" e l'architettura "ARM".
    ![Lezione 1 capitolo 5 passaggio 8](images/Lesson1Chapter5Step8.JPG)

9. Il passaggio finale consiste nella compilazione nel dispositivo selezionando Debug>Avvia senza eseguire debug. Se selezioni "Avvia senza eseguire debug", l'applicazione viene avviata immediatamente nel dispositivo al termine della compilazione, ma senza che in Visual Studio vengano visualizzate le informazioni di debug. Questo significa anche che, mentre l'applicazione è in esecuzione sul dispositivo HoloLens 2, puoi disconnettere il cavo USB senza arrestare l'applicazione. Puoi anche selezionare Compila>Distribuisci soluzione per distribuire l'applicazione nel dispositivo senza che venga avviata automaticamente.
    ![Lezione 1 capitolo 5 passaggio 9](images/Lesson1Chapter5Step9.JPG)

## <a name="congratulations"></a>Complimenti

Hai distribuito la tua prima applicazione per HoloLens2. Esplorando, noterai una mesh spaziale che copre tutte le superfici percepite da HoloLens 2. Dovresti anche vedere indicatori sulle mani e sulle dita per il tracciamento delle mani e un contatore della frequenza dei fotogrammi per tenere sotto controllo le prestazioni dell'app. Questi sono solo alcuni degli elementi fondamentali, inclusi per impostazione predefinita in Mixed Reality Toolkit. Nelle lezioni successive inizierai ad aggiungere più contenuti e interattività alla scena, in modo da poter esplorare completamente le funzionalità di HoloLens 2 e Mixed Reality Toolkit.

>Nota: nella [lezione 5](mrlearning-base-ch5.md) imparerai come attivare o disattivare il contatore della frequenza dei fotogrammi usando un comando vocale.

[Lezione successiva: Interfaccia utente, tracciamento delle mani e configurazione di Mixed Reality Toolkit](mrlearning-base-ch2.md)

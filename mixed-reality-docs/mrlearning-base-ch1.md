---
title: Modulo MR Learning Base - inizializzazione di progetto e la prima applicazione
description: Completare questo corso di informazioni su come implementare il riconoscimento di volti di Azure all'interno di un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, hololens, esercitazione di unity,
ms.openlocfilehash: 95ba00d68eb5fb6c990ddee343ac58ebe00dbb10
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993652"
---
# <a name="mr-learning-base-module---project-initialization-and-first-application"></a>Modulo MR Learning Base - inizializzazione di progetto e la prima applicazione

In questa lezione prima, si apprenderà alcune delle funzionalità di che Toolkit di realtà mista dispone dell'offerta, avviare la prima applicazione per 2 HoloLens e distribuirla nel dispositivo.

## <a name="objectives"></a>Obiettivi

* L'ottimizzazione di Unity per lo sviluppo di HoloLens.
* Importare le risorse e configurare la scena.
* Visualizzazione di mesh spaziale, le reti mesh di mano e il contatore della frequenza dei fotogrammi.

## <a name="instructions"></a>Istruzioni

### <a name="create-new-unity-project"></a>Creare nuovo progetto Unity

1. Avviare Unity.
2. Seleziona **New**.
![Passaggio 2 capitolo 1 dalla lezione 1](images/Lesson1Chapter1Step2.JPG)
3. Immettere un nome di progetto (ad esempio "MixedRealityBase").
![Passaggio 3 capitolo 1 dalla lezione 1](images/Lesson1Chapter1Step3.JPG)
4. Immettere un percorso per salvare il progetto.
![Passaggio 4 capitolo 1 dalla lezione 1](images/Lesson1Chapter1Step4.JPG)
5. Verificare che il progetto è impostato su **3D**.
![Passaggio 5 di capitolo 1 dalla lezione 1](images/Lesson1Chapter1Step5.JPG)
6. Fare clic su **Crea progetto**.
![Passaggio 6 capitolo 1 dalla lezione 1](images/Lesson1Chapter1Step6.JPG)

### <a name="configure-the-unity-project-for-windows-mixed-reality"></a>Configurare il progetto di Unity per realtà mista di Windows

1. Aprire la finestra Impostazioni di compilazione, passare al File > Build Settings.
![Passaggio 1 Chapter4 dalla lezione 1](images/Lesson1Chapter4Step1.JPG)
2. Passare a "Universal Windows Platform" selezionando "Universal Windows Platform" e quindi fare clic sul pulsante "Commutatore piattaforma" per passare le piattaforme. Le App in esecuzione su HoloLens 2 devono essere Universal Windows Platform (UWP).
![Passaggio 2 Chapter4 dalla lezione 1](images/Lesson1Chapter4Step2.JPG)
3. Abilitare la realtà virtuale facendo clic su impostazioni di Windows Media Player nella finestra di compilazione e quindi nel Pannello di controllo Abilita la casella di controllo "Realtà virtuale supportati" in impostazioni XR, come illustrato nell'immagine seguente. Si noti che potrebbe essere necessario trascinare la finestra della "Build Settings" dall'area di lavoro per visualizzare il pannello di controllo. La casella di controllo "Realtà virtuale supportato" si applica anche alle realtà mista / auricolari AR perché fa riferimento per l'abilitazione della visione stereoscopico (per il rendering diverse immagini per ogni eye.) ![Passaggio 3 Chapter4 dalla lezione 1](images/Lesson1Chapter4Step3.JPG)
4. Nel Pannello di controllo stesso, verificare che la casella di controllo "Percezione spaziale" nella sezione funzionalità è abilitata, in impostazioni di pubblicazione. Percezione spaziale ci consentirà di visualizzare la trama mapping spaziale in un dispositivo di realtà mista, ad esempio le 2 HoloLens. Le impostazioni di pubblicazione sono disponibili nel Pannello di controllo, sopra "XR Settings" e nella sezione "Altre impostazioni".
![Passaggio 4 Chapter4 dalla lezione 1](images/Lesson1Chapter4Step4.JPG)

> NOTA: Benché non sia usato in questa sezione, è possibile abilitare altre funzionalità comuni includono microfono (per i comandi vocali) e InternetClient (per la connessione a servizi che richiedono una connessione di rete)

### <a name="import-the-mixed-reality-toolkit"></a>Importare il Toolkit di realtà mista

1. Scaricare il [Toolkit di realtà mista](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC1.unitypackage) unity creare un pacchetto e salvarlo in una cartella nel PC.

2. Importare il pacchetto di Toolkit di realtà mista facendo clic sull'attività > Importa > pacchetto personalizzato. Trovare il pacchetto di Toolkit di realtà mista scaricato nel passaggio 1 e aprirlo per iniziare il processo di importazione. Attendere alcuni minuti prima che il processo di importazione.
    ![Dalla lezione 1 Chapter2 Step2a](images/Lesson1Chapter2Step2a.JPG) ![Step2b Chapter2 dalla lezione 1](images/Lesson1Chapter2Step2b.JPG)

3. Nella finestra popup successiva, fare clic su "Importa" per avviare l'importazione del Toolkit di realtà mista. Assicurarsi che tutti gli elementi vengono controllati, come illustrato nell'immagine. Se viene visualizzata una finestra di dialogo popup che chiede di applicare le impostazioni predefinite di Toolkit di realtà mista, fare clic su "Applica".
    ![Passaggio 3 Chapter2 dalla lezione 1](images/Lesson1Chapter2Step3.JPG) ![passaggio 3 Chapter2 dalla lezione 1](images/Lesson1Chapter2Step3b.JPG)

### <a name="configure-the-mixed-reality-toolkit"></a>Configurare il Toolkit di realtà mista

1. Configurare il Toolkit misto selezionando dal menu della barra di Toolkit di realtà mista > Configura. Se questa voce di menu non viene visualizzata dopo aver importato il toolkit di realtà mista, riavviare Unity.
![Passaggio 1 Chapter3 dalla lezione 1](images/Lesson1Chapter3Step1.JPG)
2. La scena verrà ora contenere alcuni nuovi elementi e le modifiche dal Toolkit di realtà mista. Salva scena con un nome diverso, fare clic sul File > Salva con nome e assegnare un nome, ad esempio, BaseScene scena. Mantenere la scena organizzata per salvarlo nella cartella "Scene" nella cartella Assets del progetto.
![Dalla lezione 1 Chapter3 Step2a](images/Lesson1Chapter3Step2a.JPG)
![Step2b Chapter3 dalla lezione 1](images/Lesson1Chapter3Step2b.JPG)

### <a name="build-your-application-to-your-device"></a>Compila la tua applicazione nel dispositivo

1. Se è stato chiuso la finestra Impostazioni di compilazione delle sezioni precedenti, aprire nuovamente la finestra Impostazioni di compilazione passando a File > Build Settings.
    ![Passaggio 1 Chapter5 dalla lezione 1](images/Lesson1Chapter5Step1.JPG)

2. Assicurarsi che la scena che si desidera provare sia nell'elenco "Scene nella compilazione" facendo clic sul pulsante "Aggiungi Open scene".

3. Premere il pulsante di compilazione per avviare il processo di compilazione.
    ![Passaggio 3 Chapter5 dalla lezione 1](images/Lesson1Chapter5Step3.JPG)

4. Creare e denominare una nuova cartella per l'applicazione. Nell'immagine seguente, una cartella con il nome "App" è stato creato per contenere l'applicazione. Fare clic su "Seleziona cartella" per l'avvio della compilazione alla cartella appena creata. Dopo il completamento della compilazione, è possibile chiudere la finestra "Build Settings" in Unity. 
    ![Passaggio 4 Chapter5 dalla lezione 1](images/Lesson1Chapter5Step4.JPG)

  > NOTA: Se la compilazione non riesce, provare a compilare nuovamente o riavviare Unity e compilare nuovamente. Se viene visualizzato un errore, ad esempio "errore: L'errore CS0246 = il nome del tipo o spazio dei nomi "XX" non è stato trovato (probabilmente manca un utilizzo della direttiva o un riferimento all'assembly?) ", potrebbe essere necessario installare [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)
  >

5. Dopo il completamento della compilazione, aprire la cartella appena creata che contiene i file dell'applicazione appena compilata. Fare doppio clic sulla soluzione "MixedRealityBase.sln" (o il nome corrispondente, se è stato usato un nome alternativo per il progetto) per aprire il file della soluzione in Visual Studio.

  > Nota: Assicurarsi di aprire la cartella appena creata (ad esempio, il "App" cartella, se seguono le convenzioni di denominazione nei passaggi precedenti), come sarà presente un file con estensione sln denominato in modo analogo di fuori di tale cartella non deve essere confusa con il file con estensione sln all'interno della cartella di compilazione. 

![Passaggio 5 Chapter5 dalla lezione 1](images/Lesson1Chapter5Step5.JPG)

  > Nota: Se Visual Studio, viene chiesto di installare i componenti nuovi, dedica qualche minuto per verificare che tutti i componenti prerequisiti vengono installati come specificato in [la pagina "Installa gli strumenti"](install-the-tools.md)

6. Collegare i 2 HoloLens PC con il cavo USB. Anche se queste istruzioni lezione si presuppongono si distribuirà un test con un dispositivo HoloLens 2, si può anche scegliere di distribuire il [HoloLens 2 emulatore](using-the-hololens-emulator.md) oppure scegliere di creare un [pacchetto dell'app per il sideload](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)

7. Prima della compilazione per il dispositivo, assicurarsi che il dispositivo è in modalità sviluppatore. Se questa è la prima volta che la distribuzione per il 2 HoloLens, Visual Studio potrebbe essere richiesto di associare i 2 HoloLens con un pin. Seguire [queste istruzioni](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio) se è necessario abilitare la modalità sviluppatore o l'associazione con Visual Studio.

8. Configurare Visual Studio per la compilazione per il 2 HoloLens, selezionare la configurazione "Release" e l'architettura "ARM".
    ![Step8 Chapter5 dalla lezione 1](images/Lesson1Chapter5Step8.JPG)

9. Il passaggio finale consiste nella compilazione per il dispositivo selezionando Debug > Avvia senza eseguire debug. Selezionando "Avvia senza eseguire debug" causerà l'applicazione venga avviata immediatamente nel dispositivo durante una compilazione corretta, ma senza informazioni di debug sono incluse in Visual Studio. Questo significa anche che, mentre l'applicazione è in esecuzione su 2 di HoloLens senza arrestare l'applicazione, è possibile disconnettere il cavo USB. È inoltre possibile selezionare compilazione > Distribuisci soluzione da distribuire al dispositivo senza che l'applicazione avvia automaticamente.
    ![Step9 Chapter5 dalla lezione 1](images/Lesson1Chapter5Step9.JPG)

## <a name="congratulations"></a>È stata completata

È ora avere distribuito la prima applicazione 2 HoloLens. Nel corso di tutto, si noterà una rete mesh di spaziali coprire tutte le superfici che hanno state percepite da 2 HoloLens. Dovrebbe inoltre, gli indicatori nel mani e dita per la disponibilità di rilevamento e un contatore di frequenza fotogrammi per tenere sotto controllo le prestazioni delle app. Questi sono solo alcuni degli elementi fondamentali, inclusi per impostazione predefinita, con il Toolkit di realtà mista. Nelle lezioni provenire, iniziare aggiungendo più contenuti e interattività alla scena, in modo che è possibile esplorare tutte le funzionalità del Toolkit di realtà mista e il 2 HoloLens.

>Nota: Come attivare o disattivare il contatore della frequenza fotogrammi usando un comando vocali nel libro vengono affrontati [lezione 5](mrlearning-base-ch5.md)

[Lezione successiva: Interfaccia utente, mano di rilevamento e configurazione di Toolkit di realtà mista](mrlearning-base-ch2.md)

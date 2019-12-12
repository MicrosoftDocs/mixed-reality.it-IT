---
title: Uso di Visual Studio per la distribuzione e il debug
description: Informazioni su come compilare, sottoporre a debug e distribuire app per HoloLens e Windows Mixed Reality con Visual Studio.
author: pbarnettms
ms.author: pbarnett
ms.date: 10/24/2019
ms.topic: article
ms.localizationpriority: high
keywords: Visual Studio, HoloLens, realtà mista, debug, distribuzione
ms.openlocfilehash: b7e6a8d538670a53de20a2f3a2850639e756da1a
ms.sourcegitcommit: 05fa75193059a2dac4b580a9eef7b6c4bb64d8d7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74830835"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a>Uso di Visual Studio per la distribuzione e il debug

Indipendentemente dal fatto che tu scelga DirectX o Unity per sviluppare un'app di realtà mista, userai Visual Studio per il debug e la distribuzione. In questa sezione imparerai a eseguire le operazioni seguenti:
* Distribuire applicazioni nel visore VR immersive di HoloLens o Windows Mixed Reality tramite Visual Studio.
* Usare l'emulatore HoloLens incorporato in Visual Studio.
* Eseguire il debug di app di realtà mista.

## <a name="prerequisites"></a>Prerequisiti
1. Per le istruzioni di installazione, vedi [Installare gli strumenti](install-the-tools.md).
2. Crea un progetto di app di Windows universale in Visual Studio.  Per HoloLens (prima generazione), usa Visual Studio 2017 o versione successiva.  Per HoloLens 2, usa Visual Studio 2019 16.2 o versione successiva. C# e C++ sono supportati. In alternativa, segui le istruzioni per [creare un'app in Unity](holograms-100.md).

## <a name="enabling-developer-mode"></a>Abilitazione della modalità sviluppatore

Per iniziare, abilita **Modalità sviluppatore** sul tuo dispositivo per consentire a Visual Studio di connettersi.

### <a name="hololens"></a>HoloLens
1. Accendi HoloLens e il dispositivo.
2. Esegui il gesto [bloom](system-gesture.md#bloom) per avviare il menu principale.
3. Rivolgi lo sguardo al riquadro **Impostazioni** ed esegui il movimento di [simulazione del tocco con un dito](gaze-and-commit.md#composite-gestures). Esegui un secondo gesto identico per posizionare l'app nel tuo ambiente. Una volta posizionata, l'app Impostazioni viene avviata.
4. Scegli la voce di menu **Aggiorna**.
5. Scegli la voce di menu **Per gli sviluppatori**.
6. Abilita **Modalità sviluppatore**. In questo modo potrai [distribuire le app da Visual Studio](using-visual-studio.md) al dispositivo HoloLens.
7. Facoltativo: Scorri verso il basso e abilita **Portale di dispositivi**. In questo modo potrai connetterti al [Portale di dispositivi di Windows](using-the-windows-device-portal.md) sul tuo dispositivo HoloLens anche da un Web browser.

### <a name="windows-pc"></a>PC Windows

Se lavori con un visore VR di Windows Mixed Reality connesso al PC, devi abilitare **Modalità sviluppatore** sul PC.
1. Vai a **Impostazioni**
2. Seleziona **Aggiornamento e sicurezza**
3. Seleziona **Per gli sviluppatori**
4. Abilita **Modalità sviluppatore**, leggi la dichiarazione di non responsabilità relativa all'impostazione scelta e quindi fai clic su Sì per accettare la modifica.

## <a name="deploying-an-app-over-wi-fi---hololens-1st-gen"></a>Distribuzione di un'app su una rete Wi-Fi - HoloLens (prima generazione)
1. Seleziona una configurazione di build **x86** per l'app ![Configurazione di build x86 in Visual Studio](images/x86setting.png)
2. Seleziona **Computer remoto** nel menu a discesa delle destinazioni di distribuzione ![Destinazione di distribuzione Computer remoto in Visual Studio](images/remotemachinesetting.png)
3. Per i progetti C++ e JavaScript, vai a **Progetto > Proprietà > Proprietà di configurazione > Debug**. Per i progetti C#, viene visualizzata automaticamente una finestra di dialogo per configurare la connessione.
  a. Immetti l'indirizzo IP del tuo dispositivo nel campo **Indirizzo** o **Nome computer**. Puoi trovare l'indirizzo IP del tuo dispositivo HoloLens in **Impostazioni > Rete e Internet > Opzioni avanzate** oppure puoi chiedere a Cortana "Qual è il mio indirizzo IP?"
  b. Imposta Modalità di autenticazione su **Universale (protocollo non crittografato)** ![Finestra di dialogo Connessione remota in Visual Studio](images/remotedeploy.png)
4. Seleziona **Debug > Avvia debug** per distribuire l'app e avviare il debug![Avvia senza eseguire debug in Visual Studio](images/deploywithdebugging.png)
5. La prima volta che distribuisci un'app in HoloLens dal PC, ti verrà chiesto di specificare un PIN. Segui le istruzioni riportate di seguito in **Associazione del dispositivo**.

## <a name="deploying-an-app-over-wi-fi---hololens-2"></a>Distribuzione di un'app su una rete Wi-Fi - HoloLens 2
1. Seleziona una configurazione di build **ARM** o **ARM64** per l'app ![Configurazione di build ARM64 in Visual Studio](images/arm64setting.png)
2. Seleziona **Computer remoto** nel menu a discesa delle destinazioni di distribuzione ![Destinazione di distribuzione Computer remoto in Visual Studio](images/remotemachinesetting_arm64.png)
3. Per i progetti C++ e JavaScript, vai a **Progetto > Proprietà > Proprietà di configurazione > Debug**. Per i progetti C#, viene visualizzata automaticamente una finestra di dialogo per configurare la connessione.
  a. Immetti l'indirizzo IP del tuo dispositivo nel campo **Indirizzo** o **Nome computer**. Puoi trovare l'indirizzo IP del tuo dispositivo HoloLens in **Impostazioni > Rete e Internet > Opzioni avanzate** oppure puoi chiedere a Cortana "Qual è il mio indirizzo IP?"
  b. Imposta Modalità di autenticazione su **Universale (protocollo non crittografato)** ![Finestra di dialogo Connessione remota in Visual Studio](images/remotedeploy.png)
4. Seleziona **Debug > Avvia debug** per distribuire l'app e avviare il debug![Avvia senza eseguire debug in Visual Studio](images/deploywithdebugging.png)
5. La prima volta che distribuisci un'app in HoloLens dal PC, ti verrà chiesto di specificare un PIN. Segui le istruzioni riportate di seguito in **Associazione del dispositivo**.

Se l'indirizzo IP di HoloLens cambia, puoi modificare l'indirizzo IP del computer di destinazione scegliendo **Progetto > Proprietà > Proprietà di configurazione > Debug**

## <a name="deploying-an-app-over-usb---hololens-1st-gen"></a>Distribuzione di un'app tramite USB - HoloLens (prima generazione)
1. Seleziona una configurazione di build **x86** per l'app ![Configurazione di build x86 in Visual Studio](images/x86setting.png)
2. Seleziona **Dispositivo** nel menu a discesa delle destinazioni di distribuzione![Distribuzione di dispositivi in Visual Studio](images/buildsettingsusbdeploy.png)
3. Seleziona **Debug > Avvia debug** per distribuire l'app e avviare il debug![Avvia senza eseguire debug in Visual Studio](images/deploywithdebugging.png)
4. La prima volta che distribuisci un'app in HoloLens dal PC, ti verrà chiesto di specificare un PIN. Segui le istruzioni riportate di seguito in **Associazione del dispositivo**.

## <a name="deploying-an-app-over-usb---hololens-2"></a>Distribuzione di un'app tramite USB - HoloLens 2
1. Seleziona una configurazione di build **ARM** o **ARM64** per l'app ![Configurazione di build ARM64 in Visual Studio](images/arm64setting.png)
2. Seleziona **Dispositivo** nel menu a discesa delle destinazioni di distribuzione![Distribuzione di dispositivi in Visual Studio](images/buildsettingsusbdeploy_arm64.png)
3. Seleziona **Debug > Avvia debug** per distribuire l'app e avviare il debug![Avvia senza eseguire debug in Visual Studio](images/deploywithdebugging.png)
4. La prima volta che distribuisci un'app in HoloLens dal PC, ti verrà chiesto di specificare un PIN. Segui le istruzioni riportate di seguito in **Associazione del dispositivo**.

## <a name="deploying-an-app-to-your-local-pc---immersive-headset"></a>Distribuzione di un'app nel PC locale - Visore VR immersive

Segui queste istruzioni quando usi un visore VR immersive di Windows Mixed Reality che si connette al PC o al [simulatore di realtà mista](using-the-windows-mixed-reality-simulator.md). In questi casi, è sufficiente distribuire ed eseguire l'app nel computer locale.
1. Seleziona una configurazione di build **x86** o **x64** per l'app
2. Seleziona **Computer locale** nel menu a discesa delle destinazioni di distribuzione
3. Seleziona **Debug > Avvia debug** per distribuire l'app e avviare il debug

## <a name="pairing-your-device"></a>Associazione del dispositivo

La prima volta che distribuisci un'app da Visual Studio in HoloLens, ti verrà chiesto di specificare un PIN. In HoloLens genera un PIN avviando l'app Impostazioni, quindi vai a **Aggiorna > Per gli sviluppatori** e tocca **Associa**. In HoloLens verrà visualizzato un PIN. Digita il PIN in Visual Studio. Al termine dell'associazione, tocca **Fine** su HoloLens per chiudere la finestra di dialogo. Questo PC è ora associato a HoloLens e sarà possibile distribuire le app automaticamente. Ripeti questi passaggi per tutti i PC successivi usati per distribuire app in HoloLens.

Per annullare l'associazione di HoloLens da tutti i computer a cui è associato, avvia l'app **Impostazioni**, vai a **Aggiorna > Per gli sviluppatori** e tocca **Cancella**.

## <a name="deploying-an-app-to-the-hololens-1st-gen-emulator"></a>Distribuzione di un'app nell'emulatore HoloLens (prima generazione)
1. Assicurati avere **[installato l'emulatore HoloLens](install-the-tools.md)** .
2. Seleziona una configurazione di build **x86** per l'app.
![Configurazione di build x86 in Visual Studio](images/x86setting.png)
3. Seleziona **Emulatore HoloLens** nel menu a discesa delle destinazioni di distribuzione ![Destinazione Emulatore in Visual Studio](images/deployemulator.png)
4. Seleziona **Debug > Avvia debug** per distribuire l'app e avviare il debug![Avvia senza eseguire debug in Visual Studio](images/deploywithdebugging.png)

## <a name="deploying-an-app-to-the-hololens-2-emulator"></a>Distribuzione di un'app nell'emulatore HoloLens 2
1. Assicurati avere **[installato l'emulatore HoloLens](install-the-tools.md)** .
2. Seleziona una configurazione di build **x86** o **x64** per l'app.
![Configurazione di build x86 in Visual Studio](images/x86setting.png)
3. Seleziona **Emulatore HoloLens 2** nel menu a discesa delle destinazioni di distribuzione ![Destinazione Emulatore in Visual Studio](images/deployemulator2.png)
4. Seleziona **Debug > Avvia debug** per distribuire l'app e avviare il debug![Avvia senza eseguire debug in Visual Studio](images/deploywithdebugging.png)

## <a name="graphics-debugger-for-hololens-1st-gen"></a>Debugger grafica per HoloLens (prima generazione)

Gli strumenti Diagnostica della grafica di Visual Studio sono molto utili per la scrittura e l'ottimizzazione di un'app olografica. Per informazioni dettagliate, vedi [Diagnostica della grafica di Visual Studio su MSDN](https://msdn.microsoft.com/library/hh315751.aspx).

**Per avviare Debugger grafica**
1. Segui le istruzioni riportate sopra per specificare come destinazione un dispositivo o un emulatore
2. Vai a **Debug > Grafica > Avvia diagnostica**
3. La prima volta che esegui questa operazione con un dispositivo HoloLens, è possibile che venga restituito un errore di accesso negato. Riavvia il dispositivo HoloLens per rendere effettive le autorizzazioni aggiornate e riprova.

## <a name="profiling"></a>Profilatura

Gli strumenti di profilatura di Visual Studio consentono di analizzare le prestazioni e l'uso delle risorse dell'app. Sono inclusi strumenti per ottimizzare l'uso di CPU, memoria, grafica e rete. Per i dettagli completi, vedi [Eseguire strumenti di diagnostica senza debug in MSDN](https://msdn.microsoft.com/library/dn957936.aspx).

**Per avviare gli strumenti di profilatura con HoloLens**
1. Segui le istruzioni riportate sopra per specificare come destinazione un dispositivo o un emulatore
2. Vai a **Debug > Avvia strumenti di diagnostica senza debug**
3. Seleziona gli strumenti che vuoi usare
4. Fai clic su **Avvia**
5. La prima volta che esegui questa operazione con un dispositivo HoloLens, è possibile che venga restituito un errore di accesso negato. Riavvia il dispositivo HoloLens per rendere effettive le autorizzazioni aggiornate e riprova.

## <a name="debugging-an-installed-or-running-app"></a>Debug di un'app installata o in esecuzione

Puoi usare Visual Studio per eseguire il debug di un'app di Windows universale installata senza distribuirla da un progetto di Visual Studio. Questa opzione è utile se vuoi eseguire il debug di un pacchetto dell'app installato o di un'app già in esecuzione.
1. Vai a **Debug -> Altre destinazioni debug -> Debug del pacchetto dell'app installato**
2. Seleziona la destinazione **Computer remoto** per HoloLens o **Computer locale** per i visori VR immersive.
3. Immetti l'**indirizzo IP** del dispositivo
4. Scegli la modalità di autenticazione **Universale**
5. La finestra mostra le app in esecuzione e inattive. Seleziona quella di cui vuoi eseguire il debug.
6. Scegli il tipo di codice di cui eseguire il debug (gestito, nativo, misto)
7. Fai clic su **Associa** o **Avvia**

## <a name="see-also"></a>Vedi anche
* [Installare gli strumenti](install-the-tools.md)
* [Uso dell'emulatore HoloLens](using-the-hololens-emulator.md)
* [Distribuzione e debug delle app UWP (Universal Windows Platform)](https://msdn.microsoft.com/library/windows/apps/xaml/mt613243.aspx)
* [Abilitare il dispositivo per lo sviluppo](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)

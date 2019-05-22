---
title: Usa Visual Studio per distribuire ed eseguire il debug
description: Come compilare, eseguire il debug e distribuire le App per realtà mista di Windows usando Visual Studio e HoloLens.
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Visual Studio, HoloLens, realtà mista, debug, distribuzione
ms.openlocfilehash: 6bd47d7212d321791a11ff4db91c3e172c91f463
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59601372"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a>Usa Visual Studio per distribuire ed eseguire il debug

Se si desidera usare Unity o DirectX per sviluppare l'app di realtà mista, si userà Visual Studio per il debug e la distribuzione. In questa sezione si apprenderà:
* Come distribuire le applicazioni per le cuffie immersive HoloLens o realtà mista di Windows tramite Visual Studio.
* Come usare l'emulatore di HoloLens incorporato Visual Studio.
* Come eseguire il debug delle app di realtà mista.

## <a name="prerequisites"></a>Prerequisiti
1. Visualizzare [installare gli strumenti](install-the-tools.md) per le istruzioni di installazione.
2. Creare un nuovo progetto di app Windows universali in Visual Studio 2015 Update 1 o Visual Studio 2017. C#, C++, e i progetti in JavaScript sono supportati. (O seguire le istruzioni per [creare una compilazione di un'app in Unity](holograms-100.md).)

## <a name="enabling-developer-mode"></a>Abilitazione della modalità sviluppatore

Iniziare abilitando **modalità sviluppatore** sul dispositivo in modo che Visual Studio può connettersi a esso.

### <a name="hololens"></a>HoloLens
1. Accendere il HoloLens e immesso nel dispositivo.
2. Esegui il gesto [bloom](gestures.md#bloom) per avviare il menu principale.
3. Fissare il **le impostazioni** riquadro ed eseguire il [puntato](gestures.md#air-tap) movimento. Esegui un secondo gesto identico per posizionare l'app nel tuo ambiente. Una volta posizionata, l'app Impostazioni viene avviata.
4. Scegli la voce di menu **Aggiorna**.
5. Scegli la voce di menu **Per gli sviluppatori**.
6. Abilita **Modalità sviluppatore**. In questo modo sarà possibile [distribuire le app da Visual Studio](using-visual-studio.md) a di HoloLens.
7. Facoltativo: Scorrere verso il basso e abilita anche **dispositivo portale**. Ciò consentirà anche di connettersi al [Windows Device Portal](using-the-windows-device-portal.md) di HoloLens da un web browser.

### <a name="windows-pc"></a>PC Windows

Se si lavora con un visore VR realtà mista di Windows connesso al PC, è necessario abilitare **modalità sviluppatore** nel PC.
1. Passare a **impostazioni**
2. Selezionare **aggiornamento e sicurezza**
3. Selezionare **per gli sviluppatori**
4. Abilitare **modalità sviluppatore**, leggere la dichiarazione di non responsabilità per l'impostazione selezionata, quindi fare clic su Sì per confermare la modifica.

## <a name="deploying-an-app-over-wi-fi---hololens-1st-gen"></a>Distribuzione di un'app tramite Wi-Fi - HoloLens (dal 1 ° generazione)
1. Selezionare un **x86** configurazione per l'app build ![x86 creare configurazione in Visual Studio](images/x86setting.png)
2. Selezionare **computer remoto** nel menu a discesa destinazione distribuzione ![destinazione distribuzione computer remoto in Visual Studio](images/remotemachinesetting.png)
3. Per C++ e i progetti in JavaScript, passare a **progetto > Proprietà > proprietà di configurazione > debug**. Per C# progetti, sarà una finestra di dialogo popup automaticamente per configurare la connessione.
  a. Immettere l'indirizzo IP del dispositivo nel **indirizzi** oppure **nome macchina** campo. Trovare l'indirizzo IP su di HoloLens sotto **Impostazioni > rete e Internet > Opzioni avanzate**, oppure è possibile chiedere "Qual è l'indirizzo IP?" Cortana
  b. Impostare la modalità di autenticazione **universale (protocollo non crittografato)**![finestra di dialogo di connessione remota in Visual Studio](images/remotedeploy.png)
4. Selezionare **Debug > Avvia debug** per distribuire l'app e avviare il debug![Avvia senza eseguire debug in Visual Studio](images/deploynodebugging.png)
5. La prima volta che si distribuisce un'app per le HoloLens dal PC, verrà richiesto un PIN. Seguire le **associazione del dispositivo** istruzioni riportate di seguito.

Se l'indirizzo IP di HoloLens cambia, è possibile modificare l'indirizzo IP del computer di destinazione, passare a **progetto > Proprietà > proprietà di configurazione > debug**

## <a name="deploying-an-app-over-usb---hololens-1st-gen"></a>Distribuzione di un'app tramite USB - HoloLens (dal 1 ° generazione)
1. Selezionare un **x86** configurazione per l'app build ![x86 creare configurazione in Visual Studio](images/x86setting.png)
2. Selezionare **periferica** nel menu a discesa destinazione distribuzione![distribuzione del dispositivo in Visual Studio](images/buildsettingsusbdeploy.png)
3. Selezionare **Debug > Avvia debug** per distribuire l'app e avviare il debug![Avvia senza eseguire debug in Visual Studio](images/deploynodebugging.png)
4. La prima volta che si distribuisce un'app per le HoloLens dal PC, verrà richiesto un PIN. Seguire le **associazione del dispositivo** istruzioni riportate di seguito.

## <a name="deploying-an-app-to-your-local-pc---immersive-headset"></a>Distribuzione di un'app nel tuo computer locale - visore VR immersivi

Seguire queste istruzioni quando si usa un visore VR immersivi realtà mista di Windows che si connette al computer o il [simulatore di realtà mista](using-the-windows-mixed-reality-simulator.md). In questi casi, è sufficiente distribuire ed eseguire l'app in un computer locale.
1. Selezionare un **x86** oppure **x64** compilare configurazione dell'app
2. Selezionare **computer locale** nel menu a discesa destinazione distribuzione
3. Selezionare **Debug > Avvia debug** per distribuire l'app e avviare il debug

## <a name="pairing-your-device---hololens-1st-gen"></a>Associazione del dispositivo - HoloLens (dal 1 ° generazione)

La prima volta che si distribuisce un'app da Visual Studio per il HoloLens, verrà richiesto un PIN. Generare un PIN in HoloLens, avviando l'app impostazioni, passare a **Update > per gli sviluppatori** e toccare **coppia**. Un PIN verrà visualizzato nella finestra di HoloLens; Immettere questo PIN in Visual Studio. Al termine dell'associazione, toccare su per chiudere la finestra di dialogo di HoloLens. ****  Questo PC è ora associato ai HoloLens e sarà in grado di distribuire automaticamente le app. Ripetere questi passaggi per ogni PC successivi che consente di distribuire le app di HoloLens.

Per annullare la coppia di HoloLens da tutti i computer a cui è stato associato, avviare il **le impostazioni** app e passare alla **Update > per gli sviluppatori** e toccare **Cancella**.

## <a name="deploying-an-app-to-the-hololens-1st-gen-emulator"></a>Distribuzione di un'app per la HoloLens (dal 1 ° generazione) emulatore
1. Assicurarsi di avere  **[installato l'emulatore di HoloLens](install-the-tools.md)**.
2. Selezionare un **x86** compilare configurazione dell'app.
![configurazione in Visual Studio build x86](images/x86setting.png)
3. Selezionare **HoloLens emulatore** nel menu a discesa destinazione distribuzione![destinazione emulatore in Visual Studio](images/deployemulator.png)
4. Selezionare **Debug > Avvia debug** per distribuire l'app e avviare il debug![Avvia senza eseguire debug in Visual Studio](images/deploynodebugging.png)

## <a name="graphics-debugger"></a>Debugger grafica

Gli strumenti di Visual Studio Graphics Diagnostics sono molto utili durante la scrittura e l'ottimizzazione di un'app Holographic. Visualizzare [diagnostica della grafica di Visual Studio su MSDN](https://msdn.microsoft.com/library/hh315751.aspx) per i dettagli completi.

**Per avviare il Debugger grafica**
1. Seguire le istruzioni precedenti come destinazione un dispositivo o emulatore
2. Passare a **Debug > grafica > avviare la diagnostica**
3. La prima volta che eseguire questa operazione con un HoloLens, si potrebbe verificarsi un errore "accesso negato". Riavviare il HoloLens per consentire autorizzazioni aggiornate diventino effettive e ripetere l'operazione.

## <a name="profiling"></a>Profilatura

Gli strumenti di profilatura di Visual Studio consentono di analizzare il consumo di risorse e le prestazioni dell'app. Sono inclusi strumenti per ottimizzare la CPU, memoria, della grafica e uso di rete. Visualizzare [eseguire strumenti di diagnostica senza debug su MSDN](https://msdn.microsoft.com/library/dn957936.aspx) per i dettagli completi.

**Per avviare gli strumenti di profilatura con HoloLens**
1. Seguire le istruzioni precedenti come destinazione un dispositivo o emulatore
2. Passare a **Debug > Avvia strumenti di diagnostica senza debug...**
3. Selezionare gli strumenti da usare
4. Fare clic su **Start**
5. La prima volta che eseguire questa operazione con un HoloLens, si potrebbe verificarsi un errore "accesso negato". Riavviare il HoloLens per consentire autorizzazioni aggiornate diventino effettive e ripetere l'operazione.

## <a name="debugging-an-installed-or-running-app"></a>Debug di un'app installata o in esecuzione

È possibile usare Visual Studio per eseguire il debug di un'app Windows universali che viene installata senza la distribuzione da un progetto di Visual Studio. Ciò è utile se si desidera eseguire il debug di un pacchetto dell'app installata, o se vuoi eseguire il debug di un'app che è già in esecuzione.
1. Passare a **Debug -> Debug altre destinazioni -> Debug pacchetto dell'App installato**
2. Selezionare il **computer remoto** destinazione per HoloLens o **computer locale** per auricolari coinvolgente e concreto.
3. Immettere il dispositivo **indirizzo IP**
4. Scegliere il **universale** modalità di autenticazione
5. La finestra Visualizza le applicazioni in esecuzione sia inattive. Selezionare quella che cosa si vuole eseguire il debug.
6. Scegliere il tipo di codice per eseguire il debug (gestito, nativo, Mixed)
7. Fare clic su **collegare** o **Start**

## <a name="see-also"></a>Vedere anche
* [Installare gli strumenti](install-the-tools.md)
* [Uso dell'emulatore HoloLens](using-the-hololens-emulator.md)
* [Distribuzione e debug di App Universal Windows Platform (UWP)](https://msdn.microsoft.com/library/windows/apps/xaml/mt613243.aspx)
* [Abilitare il dispositivo per lo sviluppo](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)

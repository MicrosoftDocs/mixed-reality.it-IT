---
title: Uso di Visual Studio per la distribuzione e il debug
description: Come compilare, eseguire il debug e distribuire app per HoloLens e la realtà mista di Windows con Visual Studio.
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Visual Studio, HoloLens, realtà mista, debug, distribuzione
ms.openlocfilehash: 36ed428d69802084c3b953ac2fdce46844dfdc88
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387731"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a>Uso di Visual Studio per la distribuzione e il debug

Se si vuole usare DirectX o Unity per sviluppare un'app per realtà mista, si userà Visual Studio per il debug e la distribuzione. In questa sezione si apprenderà come:
* Modalità di distribuzione delle applicazioni in HoloLens o Windows Mixed Reality con l'auricolare immersivo tramite Visual Studio.
* Come usare l'emulatore di HoloLens incorporato in Visual Studio.
* Come eseguire il debug di app realtà miste.

## <a name="prerequisites"></a>Prerequisiti
1. Vedere [installare gli strumenti](install-the-tools.md) per le istruzioni di installazione.
2. Creare un nuovo progetto di app di Windows universale in Visual Studio 2015 Update 1, Visual Studio 2017 o Visual Studio 2019. C#i C++progetti JavaScript, e sono tutti supportati. In alternativa, seguire le istruzioni per [creare una compilazione di un'app in Unity](holograms-100.md).

## <a name="enabling-developer-mode"></a>Abilitazione della modalità sviluppatore

Per iniziare, abilitare la **modalità sviluppatore** sul dispositivo in modo che Visual Studio possa connettersi.

### <a name="hololens"></a>HoloLens
1. Accendere il HoloLens e mettere sul dispositivo.
2. Esegui il gesto [bloom](gestures.md#bloom) per avviare il menu principale.
3. Osservare il riquadro **Settings (impostazioni** ) ed eseguire il gesto [d'aria](gestures.md#air-tap) . Esegui un secondo gesto identico per posizionare l'app nel tuo ambiente. Una volta posizionata, l'app Impostazioni viene avviata.
4. Scegli la voce di menu **Aggiorna**.
5. Scegli la voce di menu **Per gli sviluppatori**.
6. Abilita **Modalità sviluppatore**. Ciò consentirà di [distribuire le app da Visual Studio](using-visual-studio.md) in HoloLens.
7. Facoltativo: Scorrere verso il basso e abilitare anche il portale per i **dispositivi**. Questo consentirà anche di connettersi al [portale per dispositivi Windows](using-the-windows-device-portal.md) nella HoloLens da un Web browser.

### <a name="windows-pc"></a>PC Windows

Se si lavora con un auricolare di realtà mista di Windows connesso al PC, è necessario abilitare la **modalità di sviluppo** nel computer.
1. Vai a **Impostazioni**
2. Selezionare **aggiornamento e sicurezza**
3. Seleziona **per gli sviluppatori**
4. Abilitare la **modalità sviluppatore**, leggere la dichiarazione di non responsabilità per l'impostazione scelta, quindi fare clic su Sì per accettare la modifica.

## <a name="deploying-an-app-over-wi-fi---hololens-1st-gen"></a>Distribuzione di un'app su Wi-Fi-HoloLens (1a generazione)
1. Selezionare una configurazione di compilazione **x86** per la ![configurazione della build x86 dell'app in Visual Studio](images/x86setting.png)
2. Selezionare **computer remoto** nel menu ![a discesa destinazione distribuzione computer remoto destinazione distribuzione in Visual Studio](images/remotemachinesetting.png)
3. Per C++ i progetti e JavaScript, passare a **progetto > proprietà > proprietà di configurazione > debug**. Per C# i progetti, viene visualizzata automaticamente una finestra di dialogo per configurare la connessione.
  a. Immettere l'indirizzo IP del dispositivo nel campo **Indirizzo** o **nome computer** . Trovare l'indirizzo IP nella HoloLens in **impostazioni > rete & Internet > opzioni avanzate**oppure è possibile richiedere a Cortana "Qual è l'indirizzo IP?"
  b. Impostare la modalità di autenticazione sulla finestra di dialogo connessione remota **universale (protocollo non crittografato)** ![in Visual Studio](images/remotedeploy.png)
4. Selezionare **debug > avviare il debug** per distribuire l'app e avviare![il debug avvia senza eseguire debug in Visual Studio](images/deploynodebugging.png)
5. La prima volta che si distribuisce un'app in HoloLens dal PC, verrà richiesto di specificare un PIN. Seguire le istruzioni di **associazione del dispositivo** riportate di seguito.

Se l'indirizzo IP di HoloLens cambia, è possibile modificare l'indirizzo IP del computer di destinazione passando a **progetto > proprietà > proprietà di configurazione > debug**

## <a name="deploying-an-app-over-usb---hololens-1st-gen"></a>Distribuzione di un'app tramite USB-HoloLens (1a generazione)
1. Selezionare una configurazione di compilazione **x86** per la ![configurazione della build x86 dell'app in Visual Studio](images/x86setting.png)
2. Selezionare il **dispositivo** nel menu![a discesa destinazione distribuzione distribuzione dispositivi in Visual Studio](images/buildsettingsusbdeploy.png)
3. Selezionare **debug > avviare il debug** per distribuire l'app e avviare![il debug avvia senza eseguire debug in Visual Studio](images/deploynodebugging.png)
4. La prima volta che si distribuisce un'app in HoloLens dal PC, verrà richiesto di specificare un PIN. Seguire le istruzioni di **associazione del dispositivo** riportate di seguito.

## <a name="deploying-an-app-to-your-local-pc---immersive-headset"></a>Distribuzione di un'app nel computer locale-auricolare immersivo

Seguire queste istruzioni quando si usa un headset a realtà mista di Windows che si connette al PC o al simulatore di [realtà mista](using-the-windows-mixed-reality-simulator.md). In questi casi, è sufficiente distribuire ed eseguire l'app nel computer locale.
1. Selezionare una configurazione di compilazione **x86** o **x64** per l'app
2. Selezionare **computer locale** nel menu a discesa destinazione distribuzione
3. Selezionare **debug > avviare il debug** per distribuire l'app e avviare il debug

## <a name="pairing-your-device---hololens-1st-gen"></a>Associazione del dispositivo-HoloLens (1a generazione)

La prima volta che si distribuisce un'app da Visual Studio alla HoloLens, verrà richiesto di specificare un PIN. In HoloLens generare un PIN avviando l'app Impostazioni, passare a **aggiorna > per sviluppatori** e toccare **coppia**. Verrà visualizzato un PIN nel HoloLens; digitare questo PIN in Visual Studio. Al termine dell'associazione, toccare su per chiudere la finestra di dialogo di HoloLens. Questo PC è ora abbinato a HoloLens e sarà possibile distribuire le app automaticamente. Ripetere questi passaggi per tutti i PC successivi usati per distribuire le app in HoloLens.

Per annullare l'associazione dei HoloLens da tutti i computer con cui è stata abbinata, avviare l'app **Impostazioni** , passare a **Aggiorna > per gli sviluppatori** e toccare **Cancella**.

## <a name="deploying-an-app-to-the-hololens-1st-gen-emulator"></a>Distribuzione di un'app nell'emulatore HoloLens (1st Gen)
1. Assicurarsi **[di aver installato l'emulatore di HoloLens](install-the-tools.md)** .
2. Selezionare una configurazione di compilazione **x86** per l'app.
![configurazione della build x86 in Visual Studio](images/x86setting.png)
3. Selezionare l'emulatore di **HoloLens** nella destinazione dell'emulatore![del menu a discesa destinazione di distribuzione in Visual Studio](images/deployemulator.png)
4. Selezionare **debug > avviare il debug** per distribuire l'app e avviare![il debug avvia senza eseguire debug in Visual Studio](images/deploynodebugging.png)

## <a name="graphics-debugger"></a>Debugger grafica

Gli strumenti Diagnostica della grafica di Visual Studio sono molto utili per la scrittura e l'ottimizzazione di un'app olografica. Per informazioni dettagliate, vedere [diagnostica della grafica di Visual Studio su MSDN](https://msdn.microsoft.com/library/hh315751.aspx) .

**Per avviare il debugger della grafica**
1. Seguire le istruzioni riportate sopra per specificare come destinazione un dispositivo o un emulatore
2. Passare a **Debug > Graphics > avviare la diagnostica**
3. La prima volta che si esegue questa operazione con un HoloLens, è possibile che venga ricevuto un errore di accesso negato. Riavviare il HoloLens per rendere effettive le autorizzazioni aggiornate e riprovare.

## <a name="profiling"></a>Profilatura

Gli strumenti di profilatura di Visual Studio consentono di analizzare le prestazioni e l'uso delle risorse dell'app. Sono inclusi gli strumenti per ottimizzare l'utilizzo di CPU, memoria, grafica e rete. Per informazioni dettagliate, vedere [eseguire strumenti di diagnostica senza debug su MSDN](https://msdn.microsoft.com/library/dn957936.aspx) .

**Per avviare la Strumenti di profilatura con HoloLens**
1. Seguire le istruzioni riportate sopra per specificare come destinazione un dispositivo o un emulatore
2. Passare a **debug > avvia strumenti di diagnostica senza debug...**
3. Selezionare gli strumenti che si desidera utilizzare
4. Fare clic su **Avvia**
5. La prima volta che si esegue questa operazione con un HoloLens, è possibile che venga ricevuto un errore di accesso negato. Riavviare il HoloLens per rendere effettive le autorizzazioni aggiornate e riprovare.

## <a name="debugging-an-installed-or-running-app"></a>Debug di un'app installata o in esecuzione

È possibile usare Visual Studio per eseguire il debug di un'app di Windows universale installata senza distribuire da un progetto di Visual Studio. Questa opzione è utile se si vuole eseguire il debug di un pacchetto dell'app installato o se si vuole eseguire il debug di un'app già in esecuzione.
1. Passare a **debug-> altre destinazioni di debug-> pacchetto dell'app installato di debug**
2. Selezionare la destinazione del **computer remoto** per HoloLens o il **computer locale** per gli auricolari immersivi.
3. Immettere l' **indirizzo IP** del dispositivo
4. Scegliere la modalità di autenticazione **universale**
5. La finestra Mostra sia le app in esecuzione che quelle inattive. Selezionare quella che si vuole eseguire il debug.
6. Scegliere il tipo di codice di cui eseguire il debug (gestito, nativo, misto)
7. Fare clic su **Connetti** o **Avvia**

## <a name="see-also"></a>Vedere anche
* [Installare gli strumenti](install-the-tools.md)
* [Uso dell'emulatore HoloLens](using-the-hololens-emulator.md)
* [Distribuzione e debug di app piattaforma UWP (Universal Windows Platform) (UWP)](https://msdn.microsoft.com/library/windows/apps/xaml/mt613243.aspx)
* [Abilitare il dispositivo per lo sviluppo](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)

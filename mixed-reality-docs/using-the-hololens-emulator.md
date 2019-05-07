---
title: Usa l'emulatore di HoloLens
description: L'emulatore di HoloLens consente di testare le app di realtà mista sul PC senza un HoloLens fisico.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/25/2019
ms.topic: article
keywords: HoloLens, emulatore
ms.openlocfilehash: 0a8fa6bb7c7c5bb846604b7a1878911f028d8cba
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/28/2019
ms.locfileid: "64580648"
---
# <a name="using-the-hololens-emulator"></a>Usa l'emulatore di HoloLens

L'emulatore di HoloLens consente di testare le app holographic sul PC senza un HoloLens fisico e viene fornito con il set di strumenti di sviluppo di HoloLens. L'emulatore Usa una macchina virtuale Hyper-V. Gli input umani e dell'ambientali che verranno in genere letti dai sensori di HoloLens sono invece simulati usando la tastiera, mouse o controller Xbox. Le app non devono essere modificati per l'esecuzione nell'emulatore e non si conoscono che non sono in esecuzione su un reale HoloLens.

Se intende per sviluppare il App immersive (VR) visore VR realtà mista di Windows o giochi per PC desktop, consultare il [simulatore di realtà mista di Windows](using-the-windows-mixed-reality-simulator.md), che consente di simulare invece auricolari desktop.


## <a name="installing-the-hololens-emulator"></a>Installazione dell'emulatore di HoloLens
Scaricare l'emulatore di HoloLens e i modelli di progetto holographic.

Versioni: 
* [Emulatore 2 HoloLens e i modelli di progetto holographic](https://go.microsoft.com/fwlink/?linkid=2087187).
* [Emulatore HoloLens (dal 1 ° generazione) e i modelli di progetto holographic](https://go.microsoft.com/fwlink/?linkid=2065980).

È possibile trovare le compilazioni meno recenti dell'emulatore di HoloLens sul [archivio dell'emulatore HoloLens](hololens-emulator-archive.md) pagina.

### <a name="hololens-emulator-system-requirements"></a>Requisiti di sistema dell'emulatore di HoloLens

L'emulatore di HoloLens Usa Hyper-V con RemoteFx (emulatore di generazione 1 °) o GPU-PV (emulatore 2 HoloLens) per l'hardware con accelerazione grafica. Per usare l'emulatore, assicurarsi che il computer soddisfa questi requisiti hardware:
* 64-bit Windows 10 Pro, Enterprise o Education 
    >[!NOTE]
    >Windows 10 Home edition non supporta l'emulatore di HoloLens o Hyper-V.  
    >L'emulatore di 2 HoloLens richiede Windows 10 ottobre 2018 update o versione successiva.
* CPU a 64 bit
* CPU 4 core (o più CPU con un totale di 4 core)
* 8 GB di RAM o superiore
* Nel BIOS, devono essere le seguenti funzionalità [supportato e abilitato](http://blogs.technet.com/b/iftekhar/archive/2010/08/09/enable-hardware-settings-in-bios-to-run-hyper-v.aspx):
   * Virtualizzazione basata su hardware
   * SLAT (Second Level Address Translation)
   * Protezione esecuzione programmi basata su hardware
* Requisiti di GPU
   * DirectX 11.0 e versioni successive
   * Driver di grafica WDDM 1.2 o versioni successive (dal 1 ° generazione)
   * Driver WDDM 2.5 (HoloLens 2 emulatore)
   * L'emulatore potrebbe funzionare con una GPU non supportata, ma sarà molto più lenta

Se il sistema soddisfi i requisiti precedenti, **, assicurarsi che la funzionalità "Hyper-V" sia stata abilitata nel sistema** tramite Pannello di controllo -> programmi -> programmi e funzionalità -> Attivazione delle funzionalità di Windows in o off -> verificare che sia selezionato "Hyper-V" per l'installazione dell'emulatore abbia esito positivo.

## <a name="deploying-apps-to-the-hololens-emulator"></a>Distribuzione di App nell'emulatore di HoloLens

1. Carica la soluzione di app in Visual Studio.
    >[!NOTE]
    >Quando si usa Unity, compilare il progetto di Unity e quindi caricare la soluzione compilata in Visual Studio come di consueto.
2. Per l'emulatore di HoloLens (dal 1 ° generazione), assicurarsi che la piattaforma è impostata su **x86**. Per l'emulatore di 2 HoloLens assicurarsi che la piattaforma è impostata su **x86** oppure **x64**.
3. Selezionare il valore desiderato **emulatore HoloLens** versione come dispositivo di destinazione per il debug.
4. Passare a **Debug > Avvia debug** o premere **F5** per avviare l'emulatore e distribuire l'app per il debug.

L'emulatore può richiedere almeno un minuto per l'avvio al primo avvio. È consigliabile mantenere l'emulatore aperto durante la sessione di debug in modo che è possibile distribuire rapidamente le app nell'emulatore in esecuzione.

## <a name="basic-emulator-input"></a>Input di base dell'emulatore

Controllo dell'emulatore è molto simile a molti comuni videogiochi 3D. Sono disponibili opzioni di input usando la tastiera, mouse o controller Xbox. Per controllare l'emulatore, indirizzando le operazioni eseguite da un utente simulato che portano un HoloLens. Le azioni di spostamento che rispondono utente simulato intorno e le App in esecuzione nell'emulatore come si farebbe in un dispositivo reale.

Il cursore su HoloLens (dal 1 ° generazione) segue testina e rotazione.  Nell'emulatore 2 HoloLens, il cursore segue lo spostamento di mano e l'orientamento.

* **Scorrere in avanti, indietro, a sinistra e destra** -W, usare le chiavi A, S e D su tastiera, oppure la levetta sinistra in un controller Xbox.
* **Cercare, in basso a sinistra e con il pulsante destro** -fare clic e trascinare il mouse, usare i tasti freccia su tastiera, oppure la levetta destra in un controller Xbox.
* **Aria gesto tocco** : fare doppio clic del mouse, premere il tasto INVIO sulla tastiera o usare il pulsante in un controller Xbox.
* **Movimento del sistema/Bloom** : premere il tasto Windows o F2 sulla tastiera o fare clic sul pulsante B in un controller Xbox.
* **Movimento di scorrimento a mano** : tenere premuto il tasto Alt, tenere premuto il pulsante destro del mouse e trascinare il puntatore del mouse su / giù, o in un controller Xbox premuto un pulsante e il trigger a destra e spostarsi su e giù sulla destra stick.
* **Passare lo spostamento e l'orientamento** (solo emulatore HoloLens in 2) - tenere premuto il tasto Alt e trascinare il mouse sempre / verso il basso / a sinistra / destro per passare l'icona della mano o utilizzare i tasti di direzione e Q / E ruotare e ruota la lancetta.  Per un controller Xbox, usare il thumbstick sinistro per spostare l'icona della mano a sinistra / destra / avanti / indietro, il thumbstick a destra per ruotarlo e PGSU / PGGIÙ sul tasto direzionale per aumentare o diminuire l'icona della mano tenendo paraurti verso sinistro o destro.

## <a name="anatomy-of-the-hololens-2-emulator"></a>Composizione dell'emulatore di HoloLens 2 

### <a name="main-window"></a>Finestra principale

![Finestra principale dell'emulatore 2 HoloLens](images/emulator2-900px.png)

### <a name="toolbar"></a>Barra degli strumenti

A destra della finestra principale, si noterà la barra degli strumenti dell'emulatore. Barra degli strumenti contiene i pulsanti seguenti:
* ![Icona di chiusura](images/emulator-close.png) **Chiudi**: Chiude l'emulatore.
* ![Icona di riduzione a icona](images/emulator-minimize.png) **Riduci a icona**: Riduce a icona la finestra dell'emulatore.
* ![Simulation_icon](images/emulator-simulation-panel.png) **Pannello di controllo di simulazione**: Mostrare o nascondere il [Pannello di controllo di simulazione](#simulation-control-panel) per la configurazione e il controllo [input all'emulatore](#basic-emulator-input).
* ![Icona adatta allo schermo](images/emulator-fit.png) **adatta allo schermo**: È appropriato per l'emulatore allo schermo.
* ![Icona dello zoom](images/emulator-zoom.png) **Zoom**: Verificare l'emulatore maggiori e minori.
* ![Icona della Guida](images/emulator-help.png) **aiutare**: Aprire la Guida dell'emulatore.
* ![Icona del portale di dispositivo: apertura](images/emulator-deviceportal.png) **aprire il portale di dispositivo**: Aprire il Windows Device Portal per il sistema operativo HoloLens nell'emulatore.
* ![Icona Tools](images/emulator-tools.png) **strumenti**: Aprire il **strumenti aggiuntivi** riquadro.

### <a name="simulation-control-panel"></a>Pannello di controllo di simulazione

Il pannello di controllo di simulazione consente di visualizzare la posizione corrente e l'orientamento di simulato umani e simulati di dispositivi di input.  Consente inoltre di configurare entrambi input simulati, ad esempio mostrare o nascondere uno o entrambi le mani e i dispositivi usati per il controllo dell'input simulati, ad esempio del PC da tastiera e mouse gamepad.

![Pannello di controllo di simulazione](images/emulator-simulation-control-panel.png)

* Per nascondere o visualizzare il pannello di simulazione, fare clic sul pulsante della barra degli strumenti o premere F7 sulla tastiera.
* Posizionare il mouse su un controllo o un campo per visualizzare una descrizione comando che contiene i controlli di tastiera e mouse gamepad appositamente.
* Per mostrare o nascondere una mano, attivare o disattivare l'opzione appropriata in a sinistra o a destra.
* Per controllare l'icona della mano, usare i tasti Alt destro o sinistro sulla tastiera, oppure paraurti verso sinistro o destro nel gamepad.
* Per impostare tutti gli input per una o entrambe le mani, fare clic sul pulsante puntina da disegno sotto il commutatore di attivazione/disattivazione.  Questo è l'equivalente di tenendo premuto il tasto Alt per l'icona della mano.
* Per controllare la direzione di sguardo sotto controllo, fare clic sulla puntina da disegno nella sezione "Occhi".  Questo è l'equivalente di tenendo premuto il tasto "Y" sulla tastiera.
* Per caricare una stanza di registrazione, fare clic sul pulsante "Carica" nella sezione "Registrazione".  Visualizzare [simulated chat](#simulated-rooms) per altre informazioni.
* Per regolare la velocità con cui i dispositivi di input simulati o mediante intervento umani simulati saranno spostare o ruotare in risposta alla tastiera, mouse o gamepad di input, fai clic sull'icona a forma di ingranaggio accanto a "Impostazioni di Input" e modificare i dispositivi di scorrimento.
* Per impostazione predefinita, gli input da tastiera controlla l'input di risorse umane e simulato simulato.  Per ottenere input da tastiera del PC inviato tramite il HoloLens, deselezionare l'opzione "Usate la tastiera per la simulazione di".  F4 è il tasto di scelta rapida per questa impostazione.
* Se il pannello di simulazione è già visibile, premere F8 sposta lo stato attivo a esso.
* Per annullare l'ancoraggio del Pannello di simulazione dalla finestra dell'emulatore, fare clic sul pulsante nella parte inferiore del pannello o premere F9 sulla tastiera.  Chiudere la finestra o premendo F9 nuovamente restituirà la finestra all'emulatore.
* Il pannello di controllo di simulazione può essere avviato come applicazione separata, che consente di connettersi a e controllare l'emulatore di 2 HoloLens, un dispositivo HoloLens 2 o simulazione di realtà mista di Windows eseguendo PerceptionSimulationInput.exe da % ProgramFiles(x86) % \ Windows Kits\10\Microsoft XDE\10.0.18362.0\.

### <a name="account-tab"></a>Scheda Account

Scheda Account consente di configurare l'emulatore di effettuare l'accesso con un Account Microsoft. Ciò è utile per le API che richiedono all'utente di essere eseguito l'accesso aggiuntivo con un account di test.  Attivare e disattivare questa opzione richiede completamente chiudere e riavviare l'emulatore di HoloLens per l'impostazione per rendere effettive.  Se questa opzione è abilitata, gli avvii successivi dell'emulatore di chiederà di accesso, analogamente a un utente verrebbe al primo avvio di HoloLens.  Per immettere rapidamente le credenziali tramite tastiera del computer, disattivare "Uso della tastiera per la simulazione" nel Pannello di controllo di simulazione, o premere F4 sulla tastiera per attivare o disattivare l'impostazione della tastiera attiva o disattiva.

### <a name="optional-settings-tab"></a>Scheda Impostazioni facoltative

Nella scheda Impostazioni facoltative visualizzerà un controllo per abilitare o disabilitare grafica con accelerazione hardware.  Grafica con accelerazione hardware verrà utilizzata per impostazione predefinita se supportate dal driver per scheda grafica del PC.  Se il driver della scheda grafica non supporta la GPU PV, questa opzione non sarà visibile.

### <a name="diagnostics-tab"></a>Scheda diagnostica

La scheda diagnostica Mostra indirizzo IP dell'emulatore sotto forma di un collegamento al Windows Device Portal insieme allo stato della GPU virtuale.


## <a name="anatomy-of-the-hololens-1st-gen-emulator"></a>Anatomia di HoloLens (dal 1 ° generazione) emulatore

### <a name="main-window"></a>Finestra principale

Quando viene avviata nell'emulatore, si verrà visualizzata una finestra che visualizza il sistema operativo HoloLens.

![Finestra principale dell'emulatore di HoloLens](images/emulator-890px.png)

### <a name="toolbar"></a>Barra degli strumenti

A destra della finestra principale, si noterà la barra degli strumenti dell'emulatore. Barra degli strumenti contiene i pulsanti seguenti:
* ![Icona di chiusura](images/emulator-close.png) **Chiudi**: Chiude l'emulatore.
* ![Icona di riduzione a icona](images/emulator-minimize.png) **Riduci a icona**: Riduce a icona la finestra dell'emulatore.
* ![Icona input umano](images/emulator-control.png) **umana Input**: Tastiera e mouse consente di simulare umano [di input per l'emulatore](#basic-emulator-input).
* ![Icona di input da tastiera e mouse](images/emulator-input.png) **Input di Mouse e tastiera**: Tastiera e mouse di input vengono passati direttamente al sistema operativo di HoloLens come eventi di mouse e tastiera come se si è connessi una tastiera Bluetooth e un mouse.
* ![Icona adatta allo schermo](images/emulator-fit.png) **adatta allo schermo**: È appropriato per l'emulatore allo schermo.
* ![Icona dello zoom](images/emulator-zoom.png) **Zoom**: Verificare l'emulatore maggiori e minori.
* ![Icona della Guida](images/emulator-help.png) **aiutare**: Aprire la Guida dell'emulatore.
* ![Icona del portale di dispositivo: apertura](images/emulator-deviceportal.png) **aprire il portale di dispositivo**: Aprire il Windows Device Portal per il sistema operativo HoloLens nell'emulatore.
* ![Icona Tools](images/emulator-tools.png) **strumenti**: Aprire il **strumenti aggiuntivi** riquadro.

### <a name="simulation-tab"></a>Scheda di simulazione

La scheda predefinita all'interno di **strumenti aggiuntivi** riquadro è la **simulazione** scheda.

![Riquadro "Strumenti aggiuntivi" emulatore HoloLens](images/emulator-simulation-500px.png)

La scheda di simulazione Mostra lo stato corrente dei sensori simulati utilizzato per guidare il sistema operativo HoloLens all'interno dell'emulatore. Posizionare il mouse su qualsiasi valore nella scheda della simulazione fornirà una descrizione comando che descrive come controllare tale valore.

### <a name="room-tab"></a>Scheda chat room

L'emulatore simula input world sotto forma di mesh mapping spaziale da simulato "locali". Questa scheda consente di scegliere quale spazio sufficiente per caricare invece la chat room predefinita.

![Scheda 'Room' emulatore HoloLens](images/emulator-room-500px.png)

Visualizzare [simulated chat](#simulated-rooms) per altre informazioni.

### <a name="account-tab"></a>Scheda Account

Scheda Account consente di configurare l'emulatore di effettuare l'accesso con un Account Microsoft. Ciò è utile per il test dell'API che richiedono all'utente di essere eseguito l'accesso aggiuntivo con un account. Dopo avere selezionato la casella in questa pagina, gli avvii successivi dell'emulatore verranno richiesto di accesso, come si farebbe la prima volta che viene avviato il HoloLens.

## <a name="simulated-rooms"></a>Chat simulate

Le chat simulate sono utili per testare l'app in più ambienti. Le chat diversi vengono fornite con l'emulatore e dopo aver installato l'emulazione, questi avvisi sono disponibili in % %\Windows (x86) Kits\10\Microsoft XDE\\\Plugins\Rooms (versione). Tutte queste chat sono state acquisite in ambienti reali usando un HoloLens:
* **DefaultRoom.xef** -un salotto piccole con un televisore, la tabella di caffè e due divani. Caricato per impostazione predefinita quando si avvia l'emulatore.
* **Bedroom1.xef** -una piccola locali con un tecnico.
* **Bedroom2.xef** -un locali con un ambiente di dimensioni regina, cassettiera, nightstands e armadio entrare.
* **GreatRoom.xef** -una stanza di eccezionali grande spazio aperto con domestico, ristorante tabelle e di cucina.
* **LivingRoom.xef** : un salotto con un fireplace, divano, armchairs e un tabella caffè con un vaso.

È anche possibile registrare i proprio locali da usare nell'emulatore tramite la pagina di simulazione del [Windows Device Portal](using-the-windows-device-portal.md) di HoloLens (dal 1 ° generazione).

Nell'emulatore, viene visualizzata solo vntana che si esegue il rendering e non verrà visualizzata la chat simulata dietro il vntana. Ciò viene a differenza di HoloLens reali in cui vengono visualizzate entrambe fusa insieme. Se si desidera visualizzare le chat room simulate nell'emulatore di HoloLens, è necessario aggiornare l'app per eseguire il rendering mesh mapping spaziale nella scena.

## <a name="troubleshooting"></a>Risoluzione dei problemi

Si potrebbe essere visualizzato un errore durante l'installazione dell'emulatore che occorre *"Visual Studio 2015 Update 1 and UWP tools versione 1.2"*. Esistono tre possibili cause dell'errore:
* Non è una versione sufficientemente recente di Visual Studio (Visual Studio 2019, Visual Studio 2017 o Visual Studio 2015 Update 1 o versione successiva). Per risolvere il problema, installare la versione più recente di Visual Studio.
* È installata una versione sufficientemente recente di Visual Studio, ma non è installati gli strumenti di Universal Windows Platform (UWP). Si tratta di una funzionalità facoltativa di Visual Studio.

È inoltre possibile visualizzare un errore durante l'installazione dell'emulatore su un non-Pro e Enterprise/della formazione lo SKU di Windows o se non si è funzionalità Hyper-V abilitato.
* Leggi i [requisiti di sistema](#hololens-emulator-system-requirements) sezione precedente per un set completo di requisiti.
* Assicurarsi anche che funzionalità di Hyper-V è stata abilitata nel sistema.

Se l'installazione viene completata correttamente, ma non viene visualizzato l'emulatore di HoloLens come opzione per la distribuzione e debug, verificare quanto segue:
* La configurazione del progetto Visual Studio è impostata su x86 (Gen 1 ° di HoloLens) o x86 o x64 (emulatore 2 HoloLens).
* Se si usa Visual Studio 2019, il set di strumenti della piattaforma nella configurazione del progetto è impostata su v142.

Se l'installazione viene completata correttamente, ma Visual Studio visualizza un errore durante il tentativo di avviare l'emulatore di HoloLens, provare quanto segue:
* Eseguire Visual Studio come amministratore
* Se si è già usato sempre Visual Studio 2019 installato, verificare che il valore del Registro di sistema "KitsRoot10" in HKEY_LOCAL_MACHINE\Software\Microsoft\Windows Kits\Installed radici punti alla cartella dei file di programma a 32 bit (ad esempio, "C:\Program Files (x86) \Windows Kit \10 ").  In caso contrario, disinstallare l'emulatore di HoloLens, modificare il valore del Registro di sistema per la cartella programmi a 32 bit, quindi reinstallare l'emulatore di HoloLens.  Questo problema viene risolto in Visual Studio 2019 16.0.3.

Se l'emulatore viene visualizzato un messaggio di errore "Codifica Byte non valida" all'avvio:
* Eliminare tutti i file in %localappdata%\Microsoft\XDE\HCS e riprovare.

Se l'elenco di destinazione di debug in Visual Studio è vuoto (ad esempio, "Start" è l'unica opzione) e sono stati eseguiti tutti i passaggi di risoluzione dei problemi precedenti:
* Eliminare la cartella 'ConfigurationCache' in %localappdata%\Microsoft\VisualStudio\\<*id installazione*> \CoreCon e riprovare.

Se il sistema si blocca durante l'avvio dell'emulatore, disattivare l'accelerazione hardware per grafica dell'emulatore.
* Creare un valore DWORD del Registro di sistema denominato "DisableGPU" in HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\XDE\10.0 e impostarne il valore su 1.

## <a name="see-also"></a>Vedere anche
* [Emulatore HoloLens avanzato e input per il simulatore di realtà mista](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [Cronologia di HoloLens emulatore software](hololens-emulator-archive.md)
* [Mapping spaziale in Unity](spatial-mapping-in-unity.md)
* [Mapping spaziale in DirectX](spatial-mapping-in-directx.md)

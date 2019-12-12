---
title: Uso dell'emulatore HoloLens
description: Uso dell'emulatore HoloLens per testare le app di realtà mista nel PC senza un dispositivo HoloLens fisico.
author: pbarnettms
ms.author: pbarnett
ms.date: 12/5/2019
ms.topic: article
ms.localizationpriority: high
keywords: HoloLens, emulatore
ms.openlocfilehash: 49b67530d46edda3c38efd74f03f730c2b2247bd
ms.sourcegitcommit: f4812e1312c4751a22a2de56771c475b22a4ba24
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/09/2019
ms.locfileid: "74940889"
---
# <a name="using-the-hololens-emulator"></a>Uso dell'emulatore HoloLens

L'emulatore HoloLens consente di testare le app olografiche nel PC senza un dispositivo HoloLens fisico. Include anche il set di strumenti di sviluppo HoloLens. L'emulatore usa una macchina virtuale Hyper-V. Gli input umani e ambientali che in genere vengono letti dai sensori di HoloLens vengono invece simulati tramite tastiera, mouse o controller Xbox. Per eseguire le applicazioni nell'emulatore, non è necessario modificarle perché è come se venissero eseguite in un vero dispositivo HoloLens.

Se intendi sviluppare applicazioni per visori VR immersive per Windows Mixed Reality o giochi per PC desktop, vedi le informazioni relative al [simulatore di Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md), che consente di simulare i visori per computer desktop.


## <a name="installing-the-hololens-emulator"></a>Installazione dell'emulatore HoloLens
Scarica l'emulatore HoloLens.

Versioni: 
* [Emulatore HoloLens 2 (aggiornamento di dicembre 2019)](https://go.microsoft.com/fwlink/?linkid=2112589).
* [Emulatore HoloLens (prima generazione) e modelli di progetti olografici](https://go.microsoft.com/fwlink/?linkid=2065980).

Nella pagina relativa all'[archivio dell'emulatore HoloLens](hololens-emulator-archive.md) puoi trovare le note sulla versione e le build meno recenti dell'emulatore.

### <a name="hololens-emulator-system-requirements"></a>Requisiti di sistema per l'emulatore HoloLens

L'emulatore HoloLens usa Hyper-V con RemoteFx (emulatore di prima generazione) o GPU-PV (emulatore HoloLens 2) per grafica con accelerazione hardware. Per usare l'emulatore, assicurati che il PC soddisfi i requisiti hardware seguenti:
* Windows 10 Pro, Enterprise o Education a 64 bit 
    >[!NOTE]
    >Windows 10 Home Edition non supporta Hyper-V o l'emulatore HoloLens.  
    >L'emulatore HoloLens 2 richiede l'aggiornamento di Windows 10 (ottobre 2018) o versione successiva.
* CPU a 64 bit
* CPU con 4 core (o più CPU con un totale di 4 core)
* Almeno 8 GB di RAM
* Nel BIOS devono essere [supportate e abilitate](https://blogs.technet.com/b/iftekhar/archive/2010/08/09/enable-hardware-settings-in-bios-to-run-hyper-v.aspx) le funzionalità seguenti:
   * Virtualizzazione basata su hardware
   * SLAT (Second Level Address Translation)
   * Protezione esecuzione programmi basata su hardware
* Requisiti per la GPU
   * DirectX 11.0 o versioni successive
   * Driver di grafica WDDM 1.2 o versione successiva (prima generazione)
   * Driver di grafica WDDM 2.5 (emulatore HoloLens 2)
   * L'emulatore potrebbe funzionare con una GPU non supportata, ma sarà notevolmente più lento

Se il sistema soddisfa i requisiti sopra riportati, **assicurati che la funzionalità "Hyper-V" sia stata abilitata nel sistema**, scegliendo Pannello di controllo -> Programmi -> Programmi e funzionalità -> Attivazione o disattivazione delle funzionalità Windows e verificando che la voce "Hyper-V" sia selezionata, affinché l'installazione dell'emulatore abbia esito positivo.

## <a name="deploying-apps-to-the-hololens-emulator"></a>Distribuzione delle app all'emulatore HoloLens

1. Carica la soluzione dell'applicazione in Visual Studio.
    >[!NOTE]
    >Se usi Unity, compila il progetto da Unity e quindi carica in Visual Studio la soluzione compilata, come al solito.
2. Per l'emulatore HoloLens (prima generazione), verifica che la piattaforma sia impostata su **x86**. Per l'emulatore HoloLens 2, verifica che la piattaforma sia impostata su **x86** o **x64**.
3. Seleziona la versione desiderata dell'**emulatore HoloLens** come dispositivo di destinazione per il debug.
4. Vai a **Debug > Avvia debug** o premi **F5** per avviare l'emulatore e distribuire l'applicazione per il debug.

Al primo avvio, l'emulatore può impiegare almeno un minuto a partire. È consigliabile mantenere aperto l'emulatore durante la sessione di debug, in modo da potervi distribuire rapidamente le applicazioni.

## <a name="basic-emulator-input"></a>Input di base per l'emulatore

È possibile controllare l'emulatore in modo molto simile a come si controllano molti videogiochi 3D comuni. Usando la tastiera, il mouse o il controller Xbox, sono disponibili diverse opzioni di input. Puoi controllare l'emulatore dirigendo le azioni di un utente simulato che indossa un dispositivo HoloLens. Le azioni spostano l'utente simulato in tutto l'ambiente. Le applicazioni in esecuzione nell'emulatore rispondono come farebbero in un dispositivo reale.

Il cursore in HoloLens (prima generazione) segue il movimento e la rotazione della testa. Nell'emulatore HoloLens 2 il cursore segue il movimento e l'orientamento delle mani.

* **Camminare avanti, indietro, verso sinistra e verso destra**: usa i tasti W, A, S e D della tastiera oppure il joystick sinistro di un controller Xbox.
* **Guardare in alto, in basso, a sinistra e a destra**: fai clic e trascina il mouse, usa i tasti di direzione della tastiera o il joystick destro di un controller Xbox.
* **Simulare il tocco**: fai clic con il pulsante destro del mouse, premi INVIO sulla tastiera oppure usa il pulsante A di un controller Xbox.
* **Aprire la mano a fiore/eseguire il movimento di sistema**: premi il tasto Windows o F2 sulla tastiera oppure il pulsante B su un controller Xbox.
* **Usare un movimento della mano per scorrere**: tieni premuto ALT contemporaneamente al pulsante destro del mouse e trascina il mouse verso l'alto o il basso oppure su un controller Xbox tieni premuti il grilletto destro e il pulsante A e sposta verso l'alto e verso il basso il joystick destro.
* **Usare il movimento e l'orientamento della mano** (solo emulatore HoloLens 2): tieni premuto ALT e trascina il mouse verso l'alto o verso il basso, a sinistra o a destra per spostare la mano oppure usa i tasti di direzione e Q o E per ruotare e inclinare la mano. Per un controller Xbox, tieni premuto il pulsante dorsale sinistro o destro e usa la levetta sinistra per spostare la mano a sinistra, a destra, avanti e indietro, la levetta destra per farla ruotare e su o giù sul Dpad per alzare o abbassare la mano.

## <a name="anatomy-of-the-hololens-2-emulator"></a>Struttura dell'emulatore HoloLens 2 

### <a name="main-window"></a>Finestra principale

![Finestra principale dell'emulatore HoloLens 2](images/emulator2-900px.png)

### <a name="toolbar"></a>Barra degli strumenti

A destra della finestra principale è presente la barra degli strumenti dell'emulatore. La barra degli strumenti contiene i pulsanti seguenti:
* ![Icona di chiusura](images/emulator-close.png) **Close** (Chiudi): chiude l'emulatore.
* ![Icona di riduzione a icona](images/emulator-minimize.png) **Minimize** (Riduci a icona): riduce a icona la finestra dell'emulatore.
* ![Simulation_icon](images/emulator-simulation-panel.png) **Simulation control panel** (Pannello di controllo simulazione): mostra o nasconde il [pannello di controllo simulazione](#simulation-control-panel) per configurare e controllare l'[input per l'emulatore](#basic-emulator-input).
* ![Icona di adattamento allo schermo](images/emulator-fit.png) **Fit to screen** (Adatta allo schermo): adatta l'emulatore allo schermo.
* ![Icona dello zoom](images/emulator-zoom.png) **Zoom**: ingrandisce o riduce l'emulatore.
* ![Icona della Guida](images/emulator-help.png) **Help** (Guida): apre la Guida dell'emulatore.
* ![Icona di apertura del Portale di dispositivi](images/emulator-deviceportal.png) **Open Device Portal** (Apri Portale di dispositivi): apre il Portale di dispositivi di Windows per il sistema operativo di HoloLens nell'emulatore.
* ![Icona degli strumenti](images/emulator-tools.png) **Tools** (Strumenti): apre il riquadro **Additional tools** (Strumenti aggiuntivi).

### <a name="simulation-control-panel"></a>Simulation Control Panel (Pannello di controllo simulazione)

Tale pannello consente di visualizzare la posizione e l'orientamento correnti dell'utente simulato e dei dispositivi di input simulati. Consente anche di configurare sia l'input simulato, ad esempio per mostrare o nascondere una o entrambe le mani, sia i dispositivi usati per controllare l'input simulato, come la tastiera, il mouse e il game pad del PC.

![Simulation Control Panel (Pannello di controllo simulazione)](images/emulator-simulation-control-panel.png)

* Per nascondere o mostrare il pannello di simulazione, fai clic sul pulsante della barra degli strumenti oppure premi F7 sulla tastiera.
* Passa il puntatore del mouse su un controllo o su un campo per visualizzare una descrizione comando contenente i controlli specifici della tastiera, del mouse o del game pad.
* Per mostrare o nascondere una mano, usa l'interruttore appropriato sotto Left hand (Mano sinistra) o Right hand (Mano destra).
* Per controllare la mano, usa il tasto ALT sinistro o destro sulla tastiera oppure il pulsante dorsale sinistro o destro del game pad.
* Per indirizzare tutto l'input a una o a entrambe le mani, fai clic sull'icona a forma di puntina sotto l'interruttore. Ciò equivale a tenere premuto ALT per la mano.
* Per controllare la direzione dello sguardo fisso, fai clic sull'icona a forma di puntina nella sezione Eyes (Occhi). Ciò equivale a tenere premuto Y sulla tastiera.
* Per caricare la registrazione di una stanza, fai clic sul pulsante Load (Carica) nella sezione Recording (Registrazione). Per altre informazioni, vedi [Stanze simulate](#simulated-rooms).
* Per regolare la velocità con cui l'utente simulato o i dispositivi di input simulati si muoveranno o ruoteranno in risposta all'input proveniente dalla tastiera, dal mouse o dal game pad, fai clic sull'icona a forma di ingranaggio accanto a Input settings (Impostazioni input) e regola i dispositivi di scorrimento.
* Per impostazione predefinita, l'input da tastiera controlla l'utente simulato e l'input simulato. Se vuoi che l'input da tastiera del PC venga inviato a HoloLens, deseleziona l'opzione Use keyboard for simulation (Usa tastiera per simulazione). F4 è il tasto di scelta rapida per questa impostazione.
* Se il pannello di simulazione è già visibile, premi F8 per spostarvi lo stato attivo della tastiera.
* Per disancorare il pannello di simulazione dalla finestra dell'emulatore, fai clic sul pulsante nella parte inferiore del pannello oppure premi F9 sulla tastiera.  Se chiudi la finestra o premi ancora F9, tornerai all'emulatore.
* Il pannello di controllo simulazione può essere avviato come applicazione separata. In questo modo potrai connetterti e controllare l'emulatore HoloLens 2, un dispositivo HoloLens 2 o la simulazione di Windows Mixed Reality eseguendo PerceptionSimulationInput.exe da %ProgramFiles(x86)%\Windows Kits\10\Microsoft XDE\10.0.18362.0\.

### <a name="account-tab"></a>Scheda Account

La scheda Account consente di configurare l'emulatore per eseguire l'accesso con un account Microsoft. Ciò è utile per testare le API che richiedono che l'utente sia connesso con un account. Se attivi o disattivi questa opzione, devi chiudere completamente l'emulatore HoloLens e riavviarlo per rendere effettiva l'impostazione. Se questa opzione è abilitata, agli avvii successivi dell'emulatore ti verrà richiesto di eseguire l'accesso, come avverrebbe per un utente al primo avvio di HoloLens. Per immettere le credenziali usando la tastiera del PC, disattiva prima l'opzione Use keyboard for simulation (Usa tastiera per simulazione) nel pannello di controllo simulazione oppure premi F4 per attivare o disattivare l'impostazione della tastiera.

### <a name="optional-settings-tab"></a>Scheda Optional settings (Impostazioni facoltative)

Nella scheda Optional settings (Impostazioni facoltative) viene visualizzato un controllo per abilitare o disabilitare la grafica con accelerazione hardware. Questo tipo di grafica verrà usato per impostazione predefinita, se è supportato dal driver della scheda grafica del PC. Se il driver della scheda grafica non supporta GPU-PV, questa opzione non sarà visibile.

### <a name="diagnostics-tab"></a>Scheda Diagnostics (Diagnostica)

La scheda Diagnostics (Diagnostica) mostra l'indirizzo IP dell'emulatore sotto forma di collegamento al Portale di dispositivi di Windows insieme allo stato della GPU virtuale.

### <a name="network-tab"></a>Scheda Network (Rete)

La scheda Network (Rete) mostra i dettagli della scheda di rete per l'emulatore, nonché i dettagli della scheda di rete per il computer host. Tieni presente che, per l'emulatore HoloLens 2, questa scheda verrà visualizzata solo se l'emulatore viene eseguito nell'Aggiornamento di Windows 10 (maggio 2019) o in versioni successive.

### <a name="nat-configuration-tab"></a>Scheda NAT Configuration (Configurazione NAT)

Questa scheda verrà visualizzata solo se l'emulatore viene eseguito nell'Aggiornamento di Windows 10 (maggio 2019) o in versioni successive.

L'emulatore usa la connessione di rete del PC e si trova dietro un NAT.  Questa scheda consente di eseguire il mapping delle porte dal PC host all'emulatore e, in questo modo, i dispositivi remoti possono connettersi ad applicazioni e servizi in esecuzione nell'emulatore.

Ad esempio, se vuoi accedere al Portale di dispositivi nell'emulatore da un PC remoto:

1. Aggiungi una voce per la porta interna 80 (la porta su cui è in ascolto il Portale di dispositivi) facendo doppio clic su una riga libera nella tabella.  Per altre applicazioni, immetti il numero di porta su cui l'applicazione è in ascolto.
2. Scegli una qualsiasi porta esterna disponibile.  In questo esempio verrà usata la porta 8080 come porta esterna.
3. Seleziona il protocollo.  L'impostazione predefinita è TCP.  Poiché il Portale di dispositivi usa il protocollo TCP, l'impostazione predefinita verrà mantenuta.
4. Fai clic su "Apply Changes" (Applica modifiche) per abilitare il mapping.  Nella colonna "Status" (Stato) lo stato passerà da "Pending" (In attesa) ad "Active" (Attiva).
5. Nel PC remoto apri un browser e passa a (IP-del-PC-che-esegue-emulatore):8080.  Verrà visualizzata l'interfaccia del Portale di dispositivi.  Tieni presente che l'indirizzo IP usato in un PC remoto deve essere l'indirizzo IP del PC che esegue l'emulatore e non dell'emulatore vero e proprio.  Puoi recuperare l'indirizzo IP in diversi modi, ad esempio tramite l'app Impostazioni nel PC nella categoria Rete e Internet, tramite ipconfig al prompt dei comandi e dalla scheda Network (Rete) nella finestra di dialogo degli strumenti dell'emulatore cercando la voce relativa alla scheda desktop.

Considera inoltre che, se aggiungi un mapping di porte per il Portale di dispositivi, puoi controllare l'emulatore in remoto usando lo strumento per il controllo della simulazione della percezione incluso nell'installazione dell'emulatore oppure con le API di simulazione della percezione connettendoti all'indirizzo IP del PC host e alla porta esterna del Portale di dispositivi, ad esempio alla porta 8080 nell'esempio precedente.  Quando usi il controllo della simulazione della percezione per connetterti e controllare l'emulatore in remoto, specifica solo l'indirizzo IP del PC e la porta configurata.  Non includere https://.

Per impostazione predefinita, non sono presenti mapping delle porte.  Tutti gli eventuali mapping configurati vengono mantenuti tra un avvio e l'altro dell'emulatore HoloLens 2 e verranno abilitati automaticamente quando l'emulatore è completamente avviato.

Usa il pulsante Export (Esporta) per salvare i mapping in un file.  Puoi quindi condividere questo file con altri membri del team, che potranno poi usare il pulsante Import (Importa) per configurare automaticamente gli stessi mapping.

![Scheda NAT Configuration (Configurazione NAT) dell'emulatore HoloLens](images/emulator-natconfig-500px.png)

### <a name="updates-tab"></a>Scheda Updates (Aggiornamenti)

Questa scheda verrà visualizzata solo se l'emulatore viene eseguito nell'Aggiornamento di Windows 10 (maggio 2019) o in versioni successive.

All'avvio, l'emulatore verificherà l'eventuale disponibilità di nuove versioni.  Se è disponibile una nuova versione, l'emulatore visualizzerà un prompt che mostra la versione attualmente installata e la versione disponibile e che chiede se vuoi eseguire l'aggiornamento.  Se selezioni 'Yes' (Sì), viene scaricato il programma di installazione per la nuova versione.

La scheda Updates (Aggiornamenti) ti consente di scegliere se l'emulatore deve ricercare o meno le nuove versioni; a tale scopo, selezionare o deselezionare la casella di controllo "Automatically check for updates" (Controlla automaticamente la disponibilità di aggiornamenti).  Ti consente inoltre di visualizzare e scaricare altre versioni disponibili dell'emulatore, a partire dall'aggiornamento di settembre 2019.  Per le versioni diverse da quella attualmente in esecuzione, viene fornito un collegamento per il download.  Fai clic sul collegamento per scaricare il programma di installazione per la versione in questione.

![Scheda Updates (Aggiornamenti) dell'emulatore HoloLens](images/emulator-updates-500px.png)


## <a name="anatomy-of-the-hololens-1st-gen-emulator"></a>Struttura dell'emulatore HoloLens (prima generazione)

### <a name="main-window"></a>Finestra principale

Quando l'emulatore viene avviato, viene visualizzata una finestra con il sistema operativo di HoloLens.

![Finestra principale dell'emulatore HoloLens](images/emulator-890px.png)

### <a name="toolbar"></a>Barra degli strumenti

A destra della finestra principale è presente la barra degli strumenti dell'emulatore. La barra degli strumenti contiene i pulsanti seguenti:
* ![Icona di chiusura](images/emulator-close.png) **Close** (Chiudi): chiude l'emulatore.
* ![Icona di riduzione a icona](images/emulator-minimize.png) **Minimize** (Riduci a icona): riduce a icona la finestra dell'emulatore.
* ![Icona dell'input umano](images/emulator-control.png) **Human input** (Input umano): il mouse e la tastiera vengono usati per simulare l'[input per l'emulatore](#basic-emulator-input) da parte di una persona.
* ![Icona dell'input da tastiera e mouse](images/emulator-input.png) **Keyboard and mouse input** (Input da tastiera e mouse): gli input da tastiera e da mouse vengono passati direttamente al sistema operativo di HoloLens sotto forma di eventi della tastiera e del mouse come se avessi collegato una tastiera e un mouse Bluetooth.
* ![Icona di adattamento allo schermo](images/emulator-fit.png) **Fit to screen** (Adatta allo schermo): adatta l'emulatore allo schermo.
* ![Icona dello zoom](images/emulator-zoom.png) **Zoom**: ingrandisce o riduce l'emulatore.
* ![Icona della Guida](images/emulator-help.png) **Help** (Guida): apre la Guida dell'emulatore.
* ![Icona di apertura del Portale di dispositivi](images/emulator-deviceportal.png) **Open Device Portal** (Apri Portale di dispositivi): apre il Portale di dispositivi di Windows per il sistema operativo di HoloLens nell'emulatore.
* ![Icona degli strumenti](images/emulator-tools.png) **Tools** (Strumenti): apre il riquadro **Additional tools** (Strumenti aggiuntivi).

### <a name="simulation-tab"></a>Scheda Simulation (Simulazione)

La scheda predefinita all'interno del riquadro **Additional tools** (Strumenti aggiuntivi) è la scheda **Simulation** (Simulazione).

![Riquadro Additional tools (Strumenti aggiuntivi) dell'emulatore HoloLens](images/emulator-simulation-500px.png)

La scheda Simulation (Simulazione) mostra lo stato corrente dei sensori simulati usati per controllare il sistema operativo di HoloLens all'interno dell'emulatore. Passando il puntatore su un valore qualsiasi in tale scheda, verrà visualizzata una descrizione comando che spiega come controllare il valore in questione.

### <a name="room-tab"></a>Scheda Room (Stanza)

L'emulatore simula l'input del mondo sotto forma di mesh di mapping spaziale dalle stanze simulate. Questa scheda consente di selezionare quale stanza caricare al posto di quella predefinita.

![Scheda Room (Stanza) dell'emulatore HoloLens](images/emulator-room-500px.png)

Per altre informazioni, vedi [Stanze simulate](#simulated-rooms).

### <a name="account-tab"></a>Scheda Account

La scheda Account consente di configurare l'emulatore per eseguire l'accesso con un account Microsoft. Ciò è utile per testare le API che richiedono che l'utente sia connesso con un account. Dopo aver selezionato la casella in questa pagina, agli avvii successivi dell'emulatore ti verrà richiesto di eseguire l'accesso, come avverrebbe per un utente al primo avvio di HoloLens.

## <a name="simulated-rooms"></a>Stanze simulate

Le stanze simulate sono utili per testare l'applicazione in più ambienti. Con l'emulatore vengono fornite diverse stanze. Dopo aver installato l'emulazione, le troverai in %ProgramFiles(x86)%\Windows Kits\10\Microsoft XDE\\(versione)\Plugins\Rooms. Tutte queste stanze sono state acquisite in ambienti reali usando un dispositivo HoloLens:
* **DefaultRoom.xef**: un piccolo salotto con una TV, un tavolino da caffè e due divani. Viene caricata per impostazione predefinita all'avvio dell'emulatore.
* **Bedroom1.xef**: una piccola stanza da letto con una scrivania.
* **Bedroom2.xef**: una stanza da letto con un letto matrimoniale grande, una cassettiera, i comodini e una cabina armadio.
* **GreatRoom.xef**: un ampio open space comprendente un salotto, un tavolo da pranzo e una cucina.
* **LivingRoom.xef**: un salotto con un caminetto, un divano, poltrone e un tavolino da caffè con un vaso.

Puoi anche registrare le tue stanze per usarle nell'emulatore tramite la pagina di simulazione del [Portale di dispositivi di Windows](using-the-windows-device-portal.md) in HoloLens (prima generazione).

Nell'emulatore vedrai solo gli ologrammi di cui esegui il rendering. Ma non vedrai la stanza simulata dietro gli ologrammi. Ciò non accade con il dispositivo HoloLens effettivo, che mostra entrambi fusi insieme. Se vuoi vedere la stanza simulata nell'emulatore HoloLens, devi aggiornare l'applicazione per eseguire il rendering della mesh di mapping spaziale nella scena.

## <a name="troubleshooting"></a>Risoluzione dei problemi

Durante l'installazione dell'emulatore, può venire visualizzato un messaggio di errore che indica che sono necessari *"Visual Studio 2015 Update 1 e gli strumenti UWP versione 1.2"* . Questo errore può avere tre cause:
* Non disponi di una versione sufficientemente recente di Visual Studio (Visual Studio 2019, Visual Studio 2017 oppure Visual Studio 2015 Update 1 o versioni successive). Per correggere l'errore, installa la versione più recente di Visual Studio.
* Hai una versione di Visual Studio recente, ma non sono installati gli strumenti UWP (Universal Windows Platform). Si tratta di una funzionalità facoltativa di Visual Studio.

Può essere visualizzato un errore anche se installi l'emulatore in uno SKU non Pro/Enterprise/Education di Windows o se la funzionalità Hyper-V non è abilitata.
* Per un elenco completo, leggi più sopra la sezione relativa ai [requisiti di sistema](#hololens-emulator-system-requirements).
* Assicurati anche che la funzionalità Hyper-V sia stata abilitata nel sistema.

Se l'installazione viene completata correttamente ma non vedi l'emulatore HoloLens come opzione per la distribuzione e il debug, verifica quanto segue:
* La configurazione del progetto di Visual Studio deve essere impostata su x86 (HoloLens di prima generazione) oppure su x86 o x64 (emulatore HoloLens 2).
* Se è in uso Visual Studio 2019, il set di strumenti della piattaforma nella configurazione del progetto deve essere impostato su v142.

Se l'installazione viene completata correttamente ma Visual Studio visualizza un errore durante il tentativo di avviare l'emulatore HoloLens, prova a eseguire queste operazioni:
* Esegui Visual Studio come amministratore.
* Se nel computer è stato installato solo Visual Studio 2019, verifica che il valore "KitsRoot10" del Registro di sistema in HKEY_LOCAL_MACHINE\Software\Microsoft\Windows Kits\Installed Roots punti alla cartella Programmi a 32 bit (ad esempio, "C:\Programmi (x86)\Windows Kits\10").  In caso contrario, disinstalla l'emulatore HoloLens, modifica il valore del Registro di sistema impostandolo sulla cartella Programmi a 32 bit e quindi reinstalla l'emulatore HoloLens.  Questo problema viene risolto in Visual Studio 2019 16.0.3.

Se l'emulatore visualizza la finestra di dialogo di errore "La codifica byte non è valida" all'avvio:
* Elimina tutti i file in %localappdata%\Microsoft\XDE\HCS e riprova.

Se l'elenco delle destinazioni di debug in Visual Studio è vuoto (ad esempio, Start è l'unica opzione) e hai eseguito tutti i passaggi di risoluzione dei problemi sopra descritti:
* Elimina la cartella ConfigurationCache in %localappdata%\Microsoft\VisualStudio\\<*ID installazione*>\CoreCon e riprova.

Se il sistema si blocca all'avvio dell'emulatore, disabilita l'accelerazione hardware per la grafica dell'emulatore.
* Nel Registro di sistema crea un valore DWORD denominato "DisableGPU" in HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\XDE\10.0 e impostalo su 1.

## <a name="see-also"></a>Vedi anche
* [Emulatore HoloLens avanzato e input per il simulatore di realtà mista](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [Cronologia del software dell'emulatore HoloLens](hololens-emulator-archive.md)
* [Mapping spaziale in Unity](spatial-mapping-in-unity.md)
* [Mapping spaziale in DirectX](spatial-mapping-in-directx.md)

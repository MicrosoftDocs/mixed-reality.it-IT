---
title: Uso dell'emulatore HoloLens
description: Uso dell'emulatore HoloLens per testare le app di realtà mista nel PC senza un dispositivo HoloLens fisico.
author: hamalawi
ms.author: moelhama
ms.date: 7/13/2020
ms.topic: article
ms.localizationpriority: high
keywords: HoloLens, emulatore
ms.openlocfilehash: 597a0a9103f8313d26449b996c1e7af6f5619b2c
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376663"
---
# <a name="using-the-hololens-emulator"></a>Uso dell'emulatore HoloLens

L'emulatore HoloLens consente di testare le app olografiche nel PC senza un dispositivo HoloLens fisico. Include anche il set di strumenti di sviluppo HoloLens. L'emulatore usa una macchina virtuale Hyper-V. Gli input umani e ambientali che in genere vengono letti dai sensori di HoloLens vengono invece simulati tramite tastiera, mouse o controller Xbox. Per eseguire le applicazioni nell'emulatore, non è necessario modificarle perché è come se venissero eseguite in un vero dispositivo HoloLens.

Se intendi sviluppare applicazioni per visori VR immersive per Windows Mixed Reality o giochi per PC desktop, vedi le informazioni relative al [simulatore di Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md), che consente di simulare i visori per computer desktop.

## <a name="hololens-2-emulator-overview"></a>Panoramica sull'emulatore HoloLens 2

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/HoloLens-2-Emulator-Overview/player?format=ny]

## <a name="installing-the-hololens-emulator"></a>Installazione dell'emulatore HoloLens
Scarica l'emulatore HoloLens.

Versioni: 
* [Emulatore HoloLens 2 (Windows Holographic, versione 2004, aggiornamento di luglio 2020)](https://go.microsoft.com/fwlink/?linkid=2135188).
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
   * Conversione indirizzi di secondo livello (SLAT)
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

Hai un visore VR immersive di Windows Mixed Reality?  A partire dall'emulatore HoloLens 2 (Windows Holographic, versione 2004), puoi usare i controller del movimento e il visore VR immersive di Windows Mixed Reality per controllare l'emulatore HoloLens 2 e visualizzarlo in stereo.  Vedi [Uso di un visore VR immersive di Windows Mixed Reality e di controller del movimento con l'emulatore HoloLens 2](#using-a-windows-mixed-reality-immersive-headset-and-motion-controllers-with-the-hololens-2-emulator)

## <a name="anatomy-of-the-hololens-2-emulator"></a>Struttura dell'emulatore HoloLens 2 

### <a name="main-window"></a>Finestra principale

![Finestra principale dell'emulatore HoloLens 2](images/emulator2-900px.png)

### <a name="toolbar"></a>Barra degli strumenti

A destra della finestra principale è presente la barra degli strumenti dell'emulatore. La barra degli strumenti contiene i pulsanti seguenti:
* ![Icona Chiudi](images/emulator-close.png) **Chiudi**: chiude l'emulatore.
* ![Icona Riduzione a icona](images/emulator-minimize.png) **Riduzione a icona**: riduce a icona la finestra dell'emulatore.
* ![Icona di simulazione](images/emulator-simulation-panel.png) **Pannello di controllo simulazione**: mostra o nasconde il [pannello di controllo simulazione](#simulation-control-panel) per configurare e controllare l'[input per l'emulatore](#basic-emulator-input).
* ![Icona Adatta allo schermo](images/emulator-fit.png) **Adatta allo schermo**: adatta l'emulatore allo schermo.
* ![Icona Zoom](images/emulator-zoom.png) **Zoom**: ingrandisce o riduce l'emulatore.
* ![Icona Guida](images/emulator-help.png) **Guida**: apre la Guida dell'emulatore.
* ![Icona Apri Portale di dispositivi](images/emulator-deviceportal.png) **Apri Portale di dispositivi**: apre il Portale di dispositivi di Windows per il sistema operativo di HoloLens nell'emulatore.
* ![Icona Strumenti](images/emulator-tools.png) **Strumenti**: apre il riquadro **Additional tools** (Strumenti aggiuntivi).

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

### <a name="using-a-windows-mixed-reality-immersive-headset-and-motion-controllers-with-the-hololens-2-emulator"></a>Uso di un visore VR immersive di Windows Mixed Reality e di controller del movimento con l'emulatore HoloLens 2

A partire dall'emulatore HoloLens 2 (Windows Holographic, versione 2004), puoi usare i controller del movimento e il visore VR immersive di Windows Mixed Reality per visualizzare e interagire con l'emulatore HoloLens 2 in stereo.  Questa opzione consente di eseguire movimenti più veloci e naturali con la testa e le mani senza un dispositivo HoloLens 2.  Tieni presente che non si tratta di una sostituzione completa di un dispositivo HoloLens 2, ma della possibilità di usufruire di un'esperienza migliorata in aggiunta all'interazione con l'emulatore tramite tastiera, mouse e game pad in una finestra del desktop 2D.  Per abilitare questa funzionalità:

1. Assicurati che Windows Mixed Reality sia configurato nel PC e che il visore VR immersive di Windows Mixed Reality sia connesso.
2. Avvia l'emulatore HoloLens 2
3. Apri il pannello di simulazione facendo clic sul pulsante della barra degli strumenti o premendo F7.
4. Scorri il pannello in basso.
5. Seleziona la casella "Use HMD for simulation" (Usa HMD per la simulazione).
6. Windows Mixed Reality viene avviato e lo schermo dell'emulatore viene modificato leggermente.  Senza un visore VR, l'emulatore posiziona gli occhi al centro della testa e visualizza un solo occhio.  Con una visore VR, l'emulatore genera un vero output stereo, ma esegue il rendering di un solo occhio nella finestra del desktop, mentre entrambi gli occhi vengono sottoposti a rendering nel visore VR.
7. Facoltativamente, attiva uno o entrambi i controller del movimento.  L'input del controller viene mappato all'input della mano nell'emulatore,  ad esempio per toccare, effettuare il pull del trigger sul controller del movimento.  Per spostarti, usa la levetta.  Per un elenco completo dei controlli, vedi [Emulatore HoloLens avanzato e input per il simulatore di Windows Mixed Reality](advanced-hololens-emulator-and-mixed-reality-simulator-input.md).

Problemi di visualizzazione del contenuto nel visore VR?

- Se la visualizzazione è vuota sia nel visore che nel portale di Mixed Reality, ma nella finestra dell'emulatore HoloLens 2 sul desktop viene visualizzato il contenuto, verifica che l'accelerazione grafica hardware sia abilitata nell'emulatore.  Per il supporto per il visore VR immersive di Windows Mixed Reality devi abilitare l'accelerazione grafica hardware nell'emulatore.
- Se visualizzi contenuto nel visore VR, ma gli ologrammi sono sfocati o se visualizzi un'immagine doppia, segui questa procedura per modificare la visualizzazione stereo per gli occhi:

1. Disattiva temporaneamente "Use HMD for simulation" (Usa HMD per la simulazione).
2. Avvia l'editor del Registro di sistema (regedit.exe).
3. Passa a HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\PerceptionSimulation
4. Crea un nuovo valore DWORD denominato "EnableEyePoseControl" e impostane il valore su 1.
5. Abilita "Use HMD for simulation" (Usa HMD per la simulazione) nell'emulatore.
6. Quando il contenuto viene visualizzato nel visore VR, usa i tasti di direzione per regolare la rotazione dell'occhio.  Tieni premuto il tasto ALT di sinistra per modificare l'occhio sinistro e il tasto ALT di destra per modificare l'occhio destro.  Usa i tasti "Q" ed "E" per regolare la rotazione degli occhi, tenendo premuto il tasto ALT specifico per l'occhio da modificare.  Usa i tasti "+" e "-" per regolare la distanza tra gli occhi.  Tieni presente che i tasti +/- sul tastierino numerico non funzionano.  Usa i pulsanti sulla tastiera principale.
7. Quando la visualizzazione stereo appare corretta, fai clic su "S" per salvare le modifiche.  La nuova configurazione verrà salvata per gli avvi futuri dell'emulatore.
8. Se vuoi abbandonare le modifiche e ripristinare la configurazione precedente, premi il tasto "L" per caricare la configurazione predefinita o precedente.
9. Imposta il valore "EnableEyePoseControl" nel Registro di sistema su 0 e scorri fino all'opzione "Use HMD for simulation" (Usa HMD per la simulazione).

Tieni presente che se hai salvato una configurazione e vuoi rimuoverla, puoi eliminare il valore denominato "DisplayConfiguration" in HKEY_CURRENT_USER \Software\Microsoft\Windows\CurrentVersion\PerceptionSimulation.  Se attualmente usi il visore VR con l'emulatore, dovrai disabilitare l'opzione "Use HMD for simulation" (Usa HMD per la simulazione) e riattivarla per verificare che la modifica abbia effetto.

## <a name="anatomy-of-the-hololens-1st-gen-emulator"></a>Struttura dell'emulatore HoloLens (prima generazione)

### <a name="main-window"></a>Finestra principale

Quando l'emulatore viene avviato, viene visualizzata una finestra con il sistema operativo di HoloLens.

![Finestra principale dell'emulatore HoloLens](images/emulator-890px.png)

### <a name="toolbar"></a>Barra degli strumenti

A destra della finestra principale è presente la barra degli strumenti dell'emulatore. La barra degli strumenti contiene i pulsanti seguenti:
* ![Icona Chiudi](images/emulator-close.png) **Chiudi**: chiude l'emulatore.
* ![Icona Riduzione a icona](images/emulator-minimize.png) **Riduzione a icona**: riduce a icona la finestra dell'emulatore.
* ![Icona dell'input umano](images/emulator-control.png) **Input umano**: il mouse e la tastiera vengono usati per simulare l'[input per l'emulatore](#basic-emulator-input) da parte di una persona.
* ![Icona dell'input da tastiera e mouse](images/emulator-input.png) **Input da tastiera e mouse**: gli input da tastiera e da mouse vengono passati direttamente al sistema operativo di HoloLens sotto forma di eventi della tastiera e del mouse come se avessi collegato una tastiera e un mouse Bluetooth.
* ![Icona Adatta allo schermo](images/emulator-fit.png) **Adatta allo schermo**: adatta l'emulatore allo schermo.
* ![Icona Zoom](images/emulator-zoom.png) **Zoom**: ingrandisce o riduce l'emulatore.
* ![Icona Guida](images/emulator-help.png) **Guida**: apre la Guida dell'emulatore.
* ![Icona Apri Portale di dispositivi](images/emulator-deviceportal.png) **Apri Portale di dispositivi**: apre il Portale di dispositivi di Windows per il sistema operativo di HoloLens nell'emulatore.
* ![Icona Strumenti](images/emulator-tools.png) **Strumenti**: apre il riquadro **Additional tools** (Strumenti aggiuntivi).

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

## <a name="known-issues"></a>Problemi noti

* Quando si disinstalla l'emulatore HoloLens 2, è possibile che l'immagine del disco rigido (Flash.vhdx) rimanga sul disco rigido nella cartella Windows Kits\10\Emulation\HoloLens\<build number>.  È consigliabile eliminare questo file.
* L'accelerazione grafica hardware può causare l'arresto anomalo delle app di Holographic in alcuni sistemi con grafica AMD o Intel.  La disabilitazione dell'accelerazione grafica hardware nella finestra degli strumenti dell'emulatore offre una soluzione a questo problema.
* Dopo aver installato gli aggiornamenti di Windows più recenti da luglio 2020, l'accelerazione grafica hardware dell'emulatore HoloLens (prima generazione) potrebbe non essere più disponibile.
Il componente RemoteFX necessario per l'accelerazione grafica hardware è stato deprecato e verrà rimosso in una versione futura di Windows.  Per abilitare nuovamente l'accelerazione grafica hardware, usare il [cmdlet PowerShell Enable-VMRemoteFXPhysicalVideoAdapter](https://docs.microsoft.com/powershell/module/hyper-v/enable-vmremotefxphysicalvideoadapter?view=win10-ps).  Per altre informazioni, fare riferimento alla [documentazione sulla deprecazione e sulla rimozione del supporto RemoteFX in Windows](https://support.microsoft.com/help/4570006/update-to-disable-and-remove-the-remotefx-vgpu-component). 

## <a name="troubleshooting"></a>Risoluzione dei problemi

Durante l'installazione dell'emulatore, può venire visualizzato un messaggio di errore che indica che sono necessari *"Visual Studio 2015 Update 1 e gli strumenti UWP versione 1.2"* . Questo errore può avere tre cause:
* Non disponi di una versione sufficientemente recente di Visual Studio (Visual Studio 2019, Visual Studio 2017 oppure Visual Studio 2015 Update 1 o versioni successive). Per correggere l'errore, installa la versione più recente di Visual Studio.
* Hai una versione di Visual Studio recente, ma non sono installati gli strumenti UWP (Universal Windows Platform). Si tratta di una funzionalità facoltativa di Visual Studio. Per HoloLens (prima generazione) sono necessari gli strumenti UWP per Visual Studio 2015 o Visual Studio 2017.

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

## <a name="see-also"></a>Vedere anche
* [Emulatore HoloLens avanzato e input per il simulatore di realtà mista](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [Cronologia del software dell'emulatore HoloLens](hololens-emulator-archive.md)
* [Mapping spaziale in Unity](spatial-mapping-in-unity.md)
* [Mapping spaziale in DirectX](spatial-mapping-in-directx.md)

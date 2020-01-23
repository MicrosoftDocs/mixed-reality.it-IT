---
title: Uso del portale per dispositivi Windows
description: Il portale per dispositivi Windows per HoloLens consente di configurare e gestire il dispositivo in modalità remota su Wi-Fi o USB. Device Portal è un server Web in HoloLens a cui è possibile connettersi da un browser Web nel PC. Il portale per i dispositivi include molti strumenti che consentono di gestire HoloLens ed eseguire il debug e ottimizzare le app.
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: Portale per dispositivi Windows, HoloLens
ms.openlocfilehash: b22c70305076e3b2c18f880878b48c3142efdbfe
ms.sourcegitcommit: cf3b662cfcf3fb05a554c302e595eb018f01abf2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/22/2020
ms.locfileid: "76521692"
---
# <a name="using-the-windows-device-portal"></a>Uso del portale per dispositivi Windows

<table>
<tr>
<th>Funzionalità</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (prima generazione)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"><a href="immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td> Portale di dispositivi di Windows</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

Il portale per dispositivi Windows per HoloLens consente di configurare e gestire il dispositivo in modalità remota su Wi-Fi o USB. Device Portal è un server Web in HoloLens a cui è possibile connettersi da un browser Web nel PC. Il portale per i dispositivi include molti strumenti che consentono di gestire HoloLens ed eseguire il debug e ottimizzare le app.

Questa documentazione è specifica del portale per dispositivi Windows per HoloLens. Per usare il portale per dispositivi Windows per desktop (incluso per la realtà mista di Windows), vedere [Panoramica del portale per dispositivi Windows](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal)

## <a name="setting-up-hololens-to-use-windows-device-portal"></a>Configurazione di HoloLens per l'uso del portale per dispositivi Windows

1. Accendi HoloLens e il dispositivo.
2. Eseguire il [movimento di avvio](https://docs.microsoft.com/hololens/hololens2-basic-usage#start-gesture) per HoloLens2 o [Bloom](https://docs.microsoft.com/hololens/hololens1-basic-usage#open-the-start-menu-with-bloom) in HoloLens (1st Gen) per avviare il menu principale. 
3. Esaminare il riquadro **Settings (impostazioni** ) ed eseguire il gesto [d'aria](https://docs.microsoft.com/hololens/hololens1-basic-usage#select-holograms-with-gaze-and-air-tap) su HoloLens (1st Gen) o selezionarlo in HoloLens 2 [toccando il riquadro o usando un raggio di mano](https://docs.microsoft.com/hololens/hololens2-basic-usage). 
4. Scegli la voce di menu **Aggiorna**.
5. Scegli la voce di menu **Per gli sviluppatori**.
6. Abilita **Modalità sviluppatore**.
7. [Scorrere verso il basso](gaze-and-commit.md#composite-gestures) e abilitare il **portale del dispositivo**.
8. Se si sta configurando il portale per dispositivi Windows in modo da poter distribuire le app in questo HoloLens tramite USB o Wi-Fi, fare clic su **associa** per [generare un pin di associazione](using-visual-studio.md). Lasciare l'app Impostazioni nella finestra popup del PIN fino a quando non si immette il PIN in Visual Studio durante la prima distribuzione.

   ![Abilitazione della modalità sviluppatore nell'app impostazioni per Windows olografico](images/deviceportalsettings.png)

## <a name="connecting-over-wi-fi"></a>Connessione tramite Wi-Fi

1. [Connettere la HoloLens al Wi-Fi](connecting-to-wi-fi-on-hololens.md).
2. Cercare l'indirizzo IP del dispositivo.
   * Trovare l'indirizzo IP sul dispositivo in **impostazioni > rete & Internet > le opzioni avanzate di Wi-Fi >** .
3. Da un Web browser sul PC, passare a https://< YOUR_HOLOLENS_IP_ADDRESS >
   * Il browser visualizzerà il messaggio seguente: "si è verificato un problema con il certificato di sicurezza del sito Web". Il motivo è che il certificato rilasciato a Device Portal è un certificato di prova. Per ora puoi ignorare questo errore relativo al certificato e continuare.

## <a name="connecting-over-usb"></a>Connessione su USB

1. [Installare gli strumenti](install-the-tools.md) per assicurarsi di avere installato Visual Studio Update 1 con gli strumenti di sviluppo di Windows 10 installati nel PC. In questo modo, viene abilitata la connettività USB.
2. Connettere la HoloLens al PC con un cavo micro-USB per HoloLens (1a generazione) o USB-C per HoloLens 2.
3. Da un Web browser nel computer, passare a [https://127.0.0.1:10080](https://127.0.0.1:10080).

## <a name="connecting-to-an-emulator"></a>Connessione a un emulatore

Puoi usare Device Portal anche con un emulatore. Per connettersi al portale del dispositivo, usare la [barra degli strumenti](using-the-hololens-emulator.md). Fare clic su questa icona: ![icona Apri portale del dispositivo](images/emulator-deviceportal.png) **Apri portale**del dispositivo: aprire il portale del dispositivo Windows per il sistema operativo HoloLens nell'emulatore.

## <a name="creating-a-username-and-password"></a>Creazione di un nome utente e di una password

![configurare l'accesso al portale per dispositivi Windows](images/windows-device-portal-credentials-reset-page-1000px.png)<br>
*Configurare l'accesso al portale per dispositivi Windows*

La prima volta che ti connetti a Device Portal in HoloLens, devi creare un nome utente e una password.
1. In un Web browser nel PC immetti l'indirizzo IP di HoloLens. Viene visualizzata la pagina di configurazione dell'accesso.
2. Toccare o fare clic su **Richiedi PIN** ed esaminare la visualizzazione HoloLens per ottenere il PIN generato.
3. Immettere il PIN nel **PIN visualizzato** nella casella di testo del dispositivo.
4. Immetti il nome utente che userai per connetterti a Device Portal. Non deve necessariamente essere il nome di un account Microsoft o un nome di dominio.
5. Immetti una password e confermala. La password deve contenere almeno sette caratteri. Non deve necessariamente essere la password di un account Microsoft o una password di dominio.
6. Fare clic su **associa** per connettersi al portale del dispositivo Windows in HoloLens.

Se si vuole modificare il nome utente o la password in qualsiasi momento, è possibile ripetere questo processo visitando la pagina sicurezza del dispositivo passando a: https://< YOUR_HOLOLENS_IP_ADDRESS >/devicepair.htm.

## <a name="security-certificate"></a>Certificato di sicurezza

Se nel browser viene visualizzato un errore di certificato, è possibile correggerlo creando una relazione di trust con il dispositivo.

Ogni dispositivo HoloLens genera un certificato autofirmato univoco per la connessione SSL. Per impostazione predefinita, questo certificato non è ritenuto attendibile dal Web browser del PC e potresti ricevere un messaggio di errore. Scaricando il certificato da HoloLens (tramite USB o una rete Wi-Fi considerata attendibile) e impostandolo come attendibile nel PC, puoi connetterti al dispositivo in modo sicuro.
1. **Assicurarsi di trovarsi in una rete sicura (USB o rete Wi-Fi considerata attendibile).**
2. Scaricare il certificato del dispositivo dalla pagina "sicurezza" nel portale del dispositivo.
   * Passare a: https://< YOUR_HOLOLENS_IP_ADDRESS >/devicepair.htm
3. Installare il certificato nell'archivio "autorità di certificazione radice attendibili" nel PC.
   * Dal menu Windows digitare: Manage computer certificates e avviare l'applet.
   * Espandere la cartella **autorità di certificazione radice attendibile** .
   * Fare clic sulla cartella **Certificati**.
   * Dal menu Azione scegli Tutte le attività &gt; Importa...
   * Completa l'Importazione guidata certificati usando il file di certificato che hai scaricato da Device Portal.
4. Riavvia il browser.

## <a name="device-portal-pages"></a>Pagine di Device Portal

### <a name="home"></a>Home

![home page del portale per dispositivi Windows in Microsoft HoloLens](images/windows-device-portal-home-page-1000px.png)<br>
*home page del portale per dispositivi Windows in Microsoft HoloLens*

La pagina iniziale di una sessione di Device Portal è la home page. Puoi accedere alle altre pagine dalla barra di spostamento sul lato sinistro della home page.

La barra degli strumenti nella parte superiore della pagina permette di accedere allo stato e alle funzionalità che usi di frequente.
* **Online**: indica se il dispositivo è connesso alla rete Wi-Fi.
* **Shutdown**: spegne il dispositivo.
* **Restart**: spegne e quindi riaccende il dispositivo.
* **Security**: apre la pagina Device Security.
* **Cool**: indica la temperatura del dispositivo.
* **A/C**: indica se il dispositivo è collegato e in carica.
* **Help**: apre la pagina della documentazione dell'interfaccia REST.

La home page mostra le informazioni seguenti:
* **Stato del dispositivo:** monitora l'integrità del dispositivo e segnala gli errori critici.
* **Windows Information:** Mostra il nome di HoloLens e la versione attualmente installata di Windows.
* La sezione **Preferences** contiene le impostazioni seguenti:
   * **IPD**: imposta la distanza interpupillare, ovvero la distanza in millimetri tra il centro delle pupille dell'utente quando questi guarda dritto davanti a sé. L'impostazione ha effetto immediatamente. Il valore predefinito è stato calcolato automaticamente quando hai configurato il dispositivo.
   * **Device name**: ti permette di assegnare un nome a HoloLens. Dopo aver modificato questo valore, devi riavviare il dispositivo perché abbia effetto. Dopo aver fatto clic su **Salva**, viene visualizzata una finestra di dialogo che chiede se si desidera riavviare immediatamente il dispositivo o riavviarlo in seguito.
   * **Sleep settings**: imposta l'intervallo di tempo di attesa prima che il dispositivo passi allo stato di sospensione quando è collegato e quando funziona a batteria.

### <a name="3d-view"></a>3D View

![pagina di visualizzazione 3D nel portale per dispositivi Windows in Microsoft HoloLens](images/3dview-1000px.png)<br>
*pagina visualizzazione 3D nel portale per dispositivi Windows in Microsoft HoloLens*

Usa la pagina 3D View per osservare in che modo HoloLens interpreta l'ambiente circostante. Puoi spostarti nella visualizzazione usando il mouse:
* Rotazione: clic con il pulsante sinistro del mouse;
* Panoramica: fare clic con il pulsante destro del mouse;
* Zoom: scorrimento del mouse.
* **Opzioni di rilevamento**
   * Attivare il rilevamento visivo continuo controllando **Forza rilevamento visivo**. 
   * **Pause** interrompe il rilevamento visivo.
* **Opzioni di visualizzazione**: impostare le opzioni nella visualizzazione 3D:
  * **Tracking**: indica se il rilevamento visivo è attivo.
  * **Show floor**: visualizza un pavimento a scacchi.
  * **Show frustum**: visualizza il frustum di vista.
  * **Show stabilization plane**: visualizza il piano usato da HoloLens per stabilizzare il movimento.
  * **Mostra mesh**: Visualizza la mesh di mapping spaziale che rappresenta l'ambiente.
  * **Mostra ancoraggi spaziali**: Visualizza gli ancoraggi spaziali per l'app attiva. È necessario fare clic sul pulsante Aggiorna per ottenere e aggiornare i punti di ancoraggio.
  * **Show details**: visualizza la posizione delle mani, i quaternioni di rotazione della testa e il vettore di origine del dispositivo man mano che cambiano in tempo reale.
  * **Pulsante Full screen**: mostra la visualizzazione 3D in modalità schermo intero. Premi ESC per chiudere la visualizzazione a schermo intero.
* **Ricostruzione della superficie**: toccare o fare clic su **Aggiorna** per visualizzare la mesh di mapping spaziale più recente dal dispositivo. Il completamento di un passaggio completo può richiedere del tempo (fino a pochi secondi). La mesh non viene aggiornata automaticamente nella visualizzazione 3D ed è necessario fare clic manualmente su **Aggiorna** per ottenere la mesh più recente dal dispositivo. Fare clic su **Salva** per salvare la mesh di mapping spaziale corrente come file obj nel PC.
* **Ancoraggi spaziali**: fare clic su Aggiorna per visualizzare o aggiornare gli ancoraggi spaziali per l'app attiva.

### <a name="mixed-reality-capture"></a>Mixed Reality Capture

![pagina di acquisizione di realtà mista nel portale per dispositivi Windows in Microsoft HoloLens](images/windows-device-portal-mixed-reality-capture-page-1000px.png)<br>
*Pagina di acquisizione di realtà mista nel portale per dispositivi Windows in Microsoft HoloLens*

Usa la pagina Mixed Reality Capture per salvare flussi multimediali da HoloLens.
* **Impostazioni**: controllare i flussi multimediali acquisiti controllando le impostazioni seguenti:
  * **Olografici**: acquisisce il contenuto olografico nel flusso video. Il rendering degli ologrammi avviene in modalità mono, non in stereo.
  * **PV camera**: acquisisce il flusso video dalla fotocamera/videocamera.
  * **Mic Audio**: acquisisce l'audio dal gruppo di microfoni.
  * **App Audio**: acquisisce l'audio dall'app attualmente in esecuzione.
  * **Rendering dalla fotocamera**: allinea l'acquisizione dal punto di vista della fotocamera foto/video, se [supportata dall'app in esecuzione](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) (solo HoloLens 2).
  * **Live preview quality**: ti permette di selezionare la risoluzione dello schermo, la frequenza dei fotogrammi e la frequenza di streaming per l'anteprima dinamica.
* Toccare o fare clic sul pulsante **anteprima in tempo reale** per visualizzare il flusso di acquisizione. **Stop Live Preview** arresta il flusso di acquisizione.
* Toccare o fare clic su **record** per avviare la registrazione del flusso di realtà mista usando le impostazioni specificate. **Interrompi registrazione** termina la registrazione e la Salva.
* Toccare o fare clic su Crea **foto** per acquisire un'immagine dal flusso di acquisizione.
* **Videos and photos**: mostra un elenco di acquisizioni di foto e video create nel dispositivo.

> [!NOTE]
> Ci sono alcune [limitazioni alla MRC simultanea](mixed-reality-capture-for-developers.md#simultaneous-mrc-limitations):
> * Se un'app tenta di accedere alla videocamera Photo/video mentre il portale del dispositivo Windows sta registrando un video, la registrazione video si arresterà.
>   * HoloLens 2 non arresterà la registrazione video se l'app accede alla videocamera Photo/video con la modalità SharedReadOnly.
> * Se un'app usa attivamente la fotocamera foto/video, il portale per dispositivi Windows può scattare una foto o registrare un video.
> * Streaming Live:
>   * HoloLens (1st Gen) impedisce a un'app di accedere alla videocamera Photo/video durante lo streaming live dal portale per dispositivi Windows.
>   * Se un'app usa attivamente la fotocamera foto/video, HoloLens (1st Gen) non riuscirà a eseguire lo streaming live.
>   * HoloLens 2 arresta automaticamente lo streaming live quando un'app tenta di accedere alla videocamera Photo/video in modalità ExclusiveControl.
>   * HoloLens 2 è in grado di avviare un flusso Live mentre un'app usa attivamente la fotocamera PV.

### <a name="performance-tracing"></a>Traccia delle prestazioni

![pagina di traccia delle prestazioni nel portale per dispositivi Windows in Microsoft HoloLens](images/windows-device-portal-performance-tracing-page-1000px.png)<br>
*Pagina di traccia delle prestazioni nel portale per dispositivi Windows in Microsoft HoloLens*

Acquisisce tracce WPR ( [Windows Performance Recorder](https://msdn.microsoft.com/library/windows/hardware/hh448205.aspx) ) dalla HoloLens.
* **Available profiles**: seleziona il profilo WPR nell'elenco a discesa e tocca o fai clic su **Start** per avviare la traccia.
* **Custom profiles**: tocca o fai clic su **Browse** per scegliere un profilo WPR dal PC. Tocca o fai clic su **Upload and start** per avviare la traccia.

Per arrestare la traccia, fare clic sul collegamento Interrompi. Rimanere in questa pagina fino al completamento del download del file di traccia.

I file ETL acquisiti possono essere aperti per l'analisi in [Windows Performance Analyzer](https://msdn.microsoft.com/library/windows/hardware/hh448170.aspx).

### <a name="processes"></a>Processi

pagina processi ![nel portale per dispositivi Windows in Microsoft HoloLens](images/windows-device-portal-running-processes-page-1000px.png)<br>
*Pagina processi nel portale per dispositivi Windows in Microsoft HoloLens*

La pagina dei processi mostra i dettagli sui processi attualmente in esecuzione. Sono inclusi sia processi di sistema sia app.

### <a name="system-performance"></a>System Performance

pagina prestazioni ![sistema nel portale per dispositivi Windows in Microsoft HoloLens](images/windows-device-portal-system-performance-page-1000px.png)<br>
*Pagina prestazioni del sistema nel portale per dispositivi Windows in Microsoft HoloLens*

La pagina delle prestazioni mostra grafici in tempo reale con informazioni di diagnostica di sistema, come consumo energetico, frequenza dei fotogrammi e carico della CPU.

Ecco le metriche disponibili:
* **SoC power**: utilizzo dell'alimentazione SoC (System-on-Chip) istantaneo, misurato in media per un minuto
* **System power**: utilizzo dell'alimentazione del sistema istantaneo, misurato in media per un minuto
* **Frame rate**: fotogrammi al secondo, VBlank mancanti al secondo e VBlank mancanti consecutivi
* **GPU**: utilizzo del motore GPU, percentuale del totale disponibile
* **CPU**: percentuale del totale disponibile
* **I/O**: letture e scritture
* **Network**: dati ricevuti e inviati
* **Memoria**: totale, in uso, sottoposta a commit, di paging e non di paging

### <a name="apps"></a>App

Pagina app ![nel portale per dispositivi Windows in Microsoft HoloLens](images/windows-device-portal-apps-page-1000px.png)<br>
*Pagina app nel portale per dispositivi Windows in Microsoft HoloLens*

Gestisce le app installate in HoloLens.
* **Installed apps**: consente di rimuovere e avviare le app.
* **Running apps**: elenca le app attualmente in esecuzione.
* **Installa app**: selezionare i pacchetti dell'app per l'installazione da una cartella nel computer o nella rete.
* **Dependency**: consente di aggiungere dipendenze per l'app che stai per installare.
* **Distribuisci**: consente di distribuire l'app selezionata e le dipendenze in HoloLens.

### <a name="app-crash-dumps"></a>Dump di arresto anomalo dell'app

![pagina dei dump di arresto anomalo dell'app nel portale per dispositivi Windows in Microsoft HoloLens](images/windows-device-portal-dev-apps-crash-dumps-page-1000px.png)<br>
*Pagina dei dump di arresto anomalo dell'app nel portale per dispositivi Windows in Microsoft HoloLens*

In questa pagina puoi raccogliere i dump di arresto anomalo del sistema per le tue app trasferite localmente. Controllare la casella di controllo **dump di arresto anomalo abilitato** per ogni app per cui si vogliono raccogliere i dump di arresto anomalo del sistema. Torna in questa pagina per raccogliere i dump di arresto anomalo del sistema. I file dump possono essere [aperti in Visual Studio per il debug](https://msdn.microsoft.com/library/d5zhxt22.aspx).

### <a name="file-explorer"></a>Esplora file

![pagina Esplora file nel portale per dispositivi Windows in Microsoft HoloLens](images/fileexplorer-1000px.png)<br>
*Pagina Esplora file nel portale per dispositivi Windows in Microsoft HoloLens*

Usare Esplora file per esplorare, caricare e scaricare i file. È possibile usare i file nella cartella documenti, nella cartella immagini e nelle cartelle di archiviazione locale per le app distribuite da Visual Studio o dal portale del dispositivo.

### <a name="kiosk-mode"></a>Modalità tutto schermo

>[!NOTE]
>La modalità tutto schermo è disponibile solo con [Microsoft HoloLens Commercial Suite](commercial-features.md).

Vedere l'articolo [configurare HoloLens in modalità](https://docs.microsoft.com/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803) tutto schermo in Windows IT Pro Center per istruzioni aggiornate sull'abilitazione della modalità tutto schermo tramite il portale per dispositivi Windows.

### <a name="logging"></a>Logging

![la pagina di registrazione nel portale per dispositivi Windows in Microsoft HoloLens](images/windows-device-portal-logging-page-1000px.png)<br>
*Pagina di registrazione nel portale per dispositivi Windows in Microsoft HoloLens*

Gestisce il Event Tracing for Windows in tempo reale (ETW) in HoloLens.

Selezionare **Nascondi provider** per visualizzare solo l'elenco di **eventi** .
* **Registered providers**: consente di selezionare il provider ETW e il livello di traccia. Il valore del livello di traccia può indicare una delle situazioni seguenti:
   1. Chiusura o terminazione anomala
   2. Errori gravi
   3. Avvisi
   4. Avvisi non di errore

Tocca o fai clic su **Enable** per avviare la traccia. Il provider viene aggiunto all'elenco a discesa **Enabled Providers**.
* **Custom providers**: consente di selezionare un provider ETW personalizzato e il livello di traccia. Identifica il provider tramite il relativo GUID. Non includere parentesi nel GUID.
* **Enabled providers**: elenca i provider abilitati. Seleziona un provider nell'elenco a discesa e tocca o fai clic su **Disable** per arrestare la traccia. Tocca o fai clic su **Stop** per sospendere tutte le operazioni di traccia.
* **Providers history**: mostra i provider ETW abilitati durante la sessione corrente. Tocca o fai clic su **Enable** per attivare un provider disabilitato. Tocca o fai clic su **Clear** per cancellare la cronologia.
* **Events**: elenca gli eventi ETW dei provider selezionati in formato di tabella. La tabella viene aggiornata in tempo reale. Sotto la tabella fai clic sul pulsante **Clear** per eliminare tutti gli eventi ETW dalla tabella. Questa operazione non disabilita alcun provider. Puoi fare clic su **Save to file** per esportare gli eventi ETW attualmente raccolti in un file CSV locale.
* **Filtri**: consentono di filtrare gli eventi ETW raccolti in base all'ID, alla parola chiave, al livello, al nome del provider, al nome dell'attività o al testo. È possibile combinare diversi criteri insieme:
   1. Per i criteri applicati alla stessa proprietà, vengono visualizzati gli eventi che possono soddisfare uno di questi criteri.
   2. Per i criteri applicati a una proprietà diversa, gli eventi devono soddisfare tutti i criteri

Ad esempio, è possibile specificare i criteri *(il nome dell'attività contiene ' foo ' o ' bar ') e (il testo contiene ' Error ' o ' Warning ')*

### <a name="simulation"></a>Di simulazione

pagina simulazione ![nel portale per dispositivi Windows in Microsoft HoloLens](images/windows-device-portal-simulation-page-1000px.png)<br>
*Pagina simulazione nel portale per dispositivi Windows in Microsoft HoloLens*

Ti permette di registrare e riprodurre dati di input per il testing.
* **Capture room**: opzione usata per scaricare il file di un ambiente simulato che contiene la mesh di mappatura delle superfici per l'ambiente circostante dell'utente. Assegnare un nome alla stanza e quindi fare clic su **Acquisisci** per salvare i dati come file con estensione XEF nel PC. Questo file può essere caricato nell'emulatore di HoloLens.
* **Registrazione**: controllare i flussi da registrare, assegnare un nome alla registrazione e toccare o fare clic su **record** per avviare la ricodifica. Eseguire azioni con la HoloLens, quindi fare clic su **Interrompi** per salvare i dati come file con estensione XEF nel PC. Questo file può essere caricato nell'emulatore di HoloLens o nel dispositivo stesso.
* **Riproduzione**: toccare o fare clic su **carica registrazione** per selezionare un file XEF dal PC e inviare i dati al HoloLens.
* **Modalità di controllo**: selezionare la **simulazione** o l' **impostazione predefinita** nell'elenco a discesa e fare clic o toccare il pulsante **imposta** per selezionare la modalità in HoloLens. Scegliendo "Simulation" vengono disabilitati i sensori reali in HoloLens e al loro posto vengono usati i dati di simulazione caricati. Se passi a "Simulation", HoloLens non risponde all'utente reale fino a quando non torni a "Default".

### <a name="networking"></a>Funzionalità di rete di

pagina rete ![nel portale per dispositivi Windows in Microsoft HoloLens](images/windows-device-portal-networking-page-1000px.png)<br>
*Pagina rete nel portale per dispositivi Windows in Microsoft HoloLens*

Gestisce le connessioni Wi-Fi in HoloLens.
* **Schede**Wi-Fi: selezionare un adattatore e un profilo Wi-Fi usando i controlli a discesa. Toccare o fare clic su **Connetti** per utilizzare l'adapter selezionato.
* **Reti disponibili**: elenca le reti Wi-Fi a cui il HoloLens è in grado di connettersi. Toccare o fare clic su **Aggiorna** per aggiornare l'elenco.
* **Configurazione IP**: Mostra l'indirizzo IP e altri dettagli della connessione di rete.

### <a name="virtual-input"></a>Virtual Input

![pagina di input virtuale nel portale per dispositivi Windows in Microsoft HoloLens](images/windows-device-portal-virtual-input-page-1000px.png)<br>
*Pagina di input virtuale nel portale per dispositivi Windows in Microsoft HoloLens*

Invia l'input da tastiera dal computer remoto a HoloLens.

Toccare o fare clic sull'area sotto **tastiera virtuale** per abilitare l'invio di sequenze di tasti a HoloLens. Digitare nella casella di **testo input** e fare clic o toccare **Invia** per inviare le sequenze di tasti all'app attiva.

## <a name="device-portal-rest-apis"></a>API REST del portale del dispositivo

Tutti gli elementi nel portale del dispositivo sono basati sulle [API REST](device-portal-api-reference.md) che è possibile usare facoltativamente per accedere ai dati e controllare il dispositivo a livello di codice.

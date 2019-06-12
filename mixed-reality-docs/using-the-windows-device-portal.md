---
title: Utilizzando il Windows Device Portal
description: Il Windows Device Portal per HoloLens è possibile configurare e gestire in remoto il dispositivo tramite USB o Wi-Fi. Device Portal è un server Web in HoloLens a cui è possibile connettersi da un browser Web nel PC. Portale per il dispositivo include molti strumenti che consentono di gestire HoloLens e debug e ottimizzare le app.
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: Windows Device Portal, HoloLens
ms.openlocfilehash: f4319e1efa94d90bfb8cc4e5815ffa87fc865a7f
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829999"
---
# <a name="using-the-windows-device-portal"></a>Utilizzando il Windows Device Portal

<table>
<tr>
<th>Funzionalità</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (dal 1 ° generazione)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"><a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></th>
</tr><tr>
<td> Windows Device Portal</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

Il Windows Device Portal per HoloLens è possibile configurare e gestire in remoto il dispositivo tramite USB o Wi-Fi. Device Portal è un server Web in HoloLens a cui è possibile connettersi da un browser Web nel PC. Portale per il dispositivo include molti strumenti che consentono di gestire HoloLens e debug e ottimizzare le app.

Questa documentazione riguarda in particolare il Windows Device Portal per HoloLens. Per usare il portale del dispositivo Windows per desktop (inclusi per realtà mista di Windows), vedere [Cenni preliminari su Windows Device Portal](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal)

## <a name="setting-up-hololens-to-use-windows-device-portal"></a>Configurazione di HoloLens per utilizzare Windows Device Portal

1. Accendi HoloLens e il dispositivo.
2. Esegui il gesto [bloom](gestures.md#bloom) per avviare il menu principale.
3. Fissare il **le impostazioni** riquadro ed eseguire il [puntato](gestures.md#air-tap) movimento. Eseguire un secondo puntato per inserire l'app nell'ambiente in uso. Una volta posizionata, l'app Impostazioni viene avviata.
4. Scegli la voce di menu **Aggiorna**.
5. Scegli la voce di menu **Per gli sviluppatori**.
6. Abilita **Modalità sviluppatore**.
7. [Scorrere verso il basso](gestures.md#composite-gestures) e abilitare **dispositivo portale**.
8. Se si configura Windows Device Portal in modo che è possibile distribuire App a questa HoloLens tramite USB o Wi-Fi, fare clic su **coppia** al [generare un PIN abbinamento](using-visual-studio.md). Uscire dall'app impostazioni nella finestra popup PIN fino a quando non si immesse il PIN in Visual Studio durante la prima distribuzione.

   ![Abilitazione della modalità sviluppatore nell'app impostazioni per Windows Holographic](images/deviceportalsettings.png)

## <a name="connecting-over-wi-fi"></a>La connessione tramite Wi-Fi

1. [Connettere il HoloLens alla rete Wi-Fi](connecting-to-wi-fi-on-hololens.md).
2. Cercare un indirizzo IP del dispositivo.
   * Trovare l'indirizzo IP del dispositivo sotto **Impostazioni > rete e Internet > Wi-Fi > Opzioni avanzate**.
3. Da un web browser sul PC, passare a https://<YOUR_HOLOLENS_IP_ADDRESS>
   * Il browser visualizzerà il messaggio seguente: "Si è verificato un problema con il certificato di sicurezza di questo sito Web". Il motivo è che il certificato rilasciato a Device Portal è un certificato di prova. Per ora puoi ignorare questo errore relativo al certificato e continuare.

## <a name="connecting-over-usb"></a>La connessione tramite USB

1. [Installare gli strumenti](install-the-tools.md) per assicurarsi di disporre di Visual Studio Update 1 con gli strumenti di sviluppo di Windows 10 installati nel PC. In questo modo, viene abilitata la connettività USB.
2. Collega HoloLens al PC usando un cavo USB micro.
3. Da un Web browser nel PC passa a http://127.0.0.1:10080

## <a name="connecting-to-an-emulator"></a>La connessione a un emulatore

Puoi usare Device Portal anche con un emulatore. Per connettersi al portale del dispositivo, usare il [sulla barra degli strumenti](using-the-hololens-emulator.md). Fai clic su questa icona: ![Icona dispositivo portale aperta](images/emulator-deviceportal.png) **aprire il portale di dispositivo**: Aprire il Windows Device Portal per il sistema operativo HoloLens nell'emulatore.

## <a name="creating-a-username-and-password"></a>Creazione di un nome utente e Password

![Configurare l'accesso a Windows Device Portal](images/windows-device-portal-credentials-reset-page-1000px.png)<br>
*Configurare l'accesso a Windows Device Portal*

La prima volta che ti connetti a Device Portal in HoloLens, devi creare un nome utente e una password.
1. In un Web browser nel PC immetti l'indirizzo IP di HoloLens. Viene visualizzata la pagina di configurazione dell'accesso.
2. Fare clic o toccare **richiesta di pin** ed esaminare la visualizzazione di HoloLens per ottenere il PIN generato.
3. Immettere il PIN nel **PIN visualizzato sul dispositivo** nella casella di testo.
4. Immetti il nome utente che userai per connetterti a Device Portal. Non deve necessariamente essere il nome di un account Microsoft o un nome di dominio.
5. Immetti una password e confermala. La password deve contenere almeno sette caratteri. Non deve necessariamente essere la password di un account Microsoft o una password di dominio.
6. Fare clic su **coppia** per connettersi a Windows Device Portal nel HoloLens.

Se si vuole modificare questo nome utente o password in qualsiasi momento, è possibile ripetere questo processo visitando la pagina di sicurezza del dispositivo passando alla: https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm.

## <a name="security-certificate"></a>Certificato di sicurezza

Se ricevi un messaggio di errore relativo al certificato nel browser, puoi correggerlo creando una relazione di trust con il dispositivo.

Ogni dispositivo HoloLens genera un certificato autofirmato univoco per la connessione SSL. Per impostazione predefinita, questo certificato non è ritenuto attendibile dal Web browser del PC e potresti ricevere un messaggio di errore. Scaricando il certificato da HoloLens (tramite USB o una rete Wi-Fi considerata attendibile) e impostandolo come attendibile nel PC, puoi connetterti al dispositivo in modo sicuro.
1. **Assicurarsi che si usa una rete sicura (USB o una rete Wi-Fi che si considera attendibile).**
2. Scaricare il certificato del dispositivo dalla pagina di "Sicurezza" nel portale del dispositivo.
   * Passare a: https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm
3. Installare il certificato nella "radice autorità di certificazione" archiviare nel PC.
   * Dal menu di Windows, digitare: Gestisci i certificati Computer e avviare l'applet.
   * Espandere la **autorità di certificazione radice attendibile** cartella.
   * Fare clic sui **certificati** cartella.
   * Dal menu azione, selezionare: Tutte le attività > Importa...
   * Completa l'Importazione guidata certificati usando il file di certificato che hai scaricato da Device Portal.
4. Riavvia il browser.

## <a name="device-portal-pages"></a>Pagine di Device Portal

### <a name="home"></a>Home

![Home page di Windows Device Portal in Microsoft HoloLens](images/windows-device-portal-home-page-1000px.png)<br>
*Home page di Windows Device Portal in Microsoft HoloLens*

La pagina iniziale di una sessione di Device Portal è la home page. Puoi accedere alle altre pagine dalla barra di spostamento sul lato sinistro della home page.

La barra degli strumenti nella parte superiore della pagina permette di accedere allo stato e alle funzionalità che usi di frequente.
* **Online**: Indica se il dispositivo è connesso alla rete Wi-Fi.
* **Shutdown**: Consente di disattivare il dispositivo.
* **Riavviare**: I cicli di alimentazione sul dispositivo.
* **Sicurezza**: Apre la pagina di sicurezza del dispositivo.
* **Ad accesso sporadico**: Indica la temperatura del dispositivo.
* **A/C**: Indica se il dispositivo sia connesso e l'addebito.
* **Guida in linea**: Apre la pagina della documentazione dell'interfaccia REST.

La home page mostra le informazioni seguenti:
* **Stato del dispositivo:** monitora l'integrità del dispositivo e segnala gli errori critici.
* **Informazioni di Windows:** Mostra il nome della finestra di HoloLens e la versione attualmente installata di Windows.
* La sezione **Preferences** contiene le impostazioni seguenti:
   * **IPD**: Imposta la distanza interpupillary (IPD), ovvero la distanza, in millimetri, tra il centro di studenti dell'utente durante la ricerca dritto. L'impostazione ha effetto immediatamente. Il valore predefinito è stato calcolato automaticamente quando hai configurato il dispositivo.
   * **Nome del dispositivo**: Assegnare un nome per il HoloLens. Dopo aver modificato questo valore, devi riavviare il dispositivo perché abbia effetto. Dopo aver fatto clic **salvare**, una finestra di dialogo chiederà se si desidera riavviare immediatamente il dispositivo o al successivo riavvio in un secondo momento.
   * **Le impostazioni di sospensione**: Imposta il periodo di tempo di attesa prima che il dispositivo passa alla modalità sospensione quando viene collegato, e quando è alimentato da batteria.

### <a name="3d-view"></a>3D View

![Pagina di visualizzazione 3D in Windows Device Portal in Microsoft HoloLens](images/3dview-1000px.png)<br>
*Pagina di visualizzazione 3D in Windows Device Portal in Microsoft HoloLens*

Usa la pagina 3D View per osservare in che modo HoloLens interpreta l'ambiente circostante. Puoi spostarti nella visualizzazione usando il mouse:
* Ruotare: a sinistra fare clic su + passa il mouse;
* Panoramica: pulsante destro del mouse fare clic su + mouse;
* Zoom: lo scorrimento del mouse.
* **Le opzioni di rilevamento**
   * Attivare rilevamento visual continuo controllando **rilevamento visual Force**. 
   * **Sospendi** arresta rilevamento visual.
* **Visualizzare le opzioni**: Impostare le opzioni per la vista 3D:
  * **Rilevamento**: Indica se il rilevamento visual è attivo.
  * **Mostra floor**: Consente di visualizzare un piano a scacchi floor.
  * **Mostra cono**: Visualizza del cono di visualizzazione.
  * **Mostra piano di stabilizzazione**: Consente di visualizzare il piano di HoloLens Usa per la stabilizzazione del movimento.
  * **Mostra mesh**: Consente di visualizzare la trama mapping spaziale che rappresenta l'ambiente circostante.
  * **Mostra gli ancoraggi spaziali**: Visualizza gli ancoraggi spaziali per l'app attiva. È necessario fare clic sul pulsante Aggiorna per ottenere e aggiornare i punti di ancoraggio.
  * **Mostra dettagli**: Consente di visualizzare a essere passate le posizioni, i quaternioni rotazione head e il vettore di origine del dispositivo quando si modifica in tempo reale.
  * **A schermo intero**: Mostra la visualizzazione 3D in modalità schermo intero. Premi ESC per chiudere la visualizzazione a schermo intero.
* **La ricostruzione della superficie di attacco**: Fare clic o toccare **Update** per visualizzare la trama più recente mapping spaziale dal dispositivo. Un passaggio completo può impiegare una certa quantità di tempo, fino ad alcuni secondi. La trama non viene aggiornato automaticamente nella vista 3D e si dovrà scegliere manualmente **aggiornare** per ottenere la mesh più recente dal dispositivo. Fare clic su **salvare** per salvare la trama mapping spaziale corrente come un file obj nel PC.
* **Gli ancoraggi spaziali**: Fare clic su Aggiorna per visualizzare o aggiornare i punti di ancoraggio spaziali per l'app attiva.

### <a name="mixed-reality-capture"></a>Mixed Reality Capture

![Pagina acquisire realtà mista in Windows Device Portal in Microsoft HoloLens](images/windows-device-portal-mixed-reality-capture-page-1000px.png)<br>
*Pagina acquisire realtà mista in Windows Device Portal in Microsoft HoloLens*

Usare la [acquisire realtà mista](mixed-reality-capture.md) pagina per salvare i flussi multimediali da di HoloLens.
* **Impostazioni**: Controllare i flussi multimediali che sono stati acquisiti controllando le impostazioni seguenti:
  * **Ologrammi**: Consente di acquisire il contenuto nel flusso video holographic. Il rendering degli ologrammi avviene in modalità mono, non in stereo.
  * **Fotocamera PV**: Acquisisce il flusso video dalla fotocamera foto/video.
  * **MIC Audio**: Consente di acquisire audio dalla matrice di microfono.
  * **app Audio**: Consente di acquisire audio da app attualmente in esecuzione.
  * **Live di qualità anteprima**: Selezionare la risoluzione dello schermo, frequenza dei fotogrammi e frequenza di streaming per l'anteprima in tempo reale.
* Fare clic o toccare il **anteprima in tempo reale** pulsante affinché mostri il flusso di acquisizione. **Anteprima in tempo reale Stop** Arresta il flusso di acquisizione.
* Fare clic o toccare **Record** per avviare la registrazione nel flusso di realtà mista, utilizzando le impostazioni specificate. **Arrestare la registrazione** termina la registrazione e di salvarlo.
* Fare clic o toccare **Take photo** portare un'immagine fissa dal flusso di acquisizione.
* **Video e foto**: Visualizza un elenco di foto e video di acquisizioni eseguite nel dispositivo.

Le app per HoloLens non sono in grado di acquisire foto o video MRC durante la registrazione o lo streaming di un'anteprima dinamica da Device Portal.

### <a name="performance-tracing"></a>Traccia delle prestazioni

![Prestazioni traccia pagina in Windows Device Portal in Microsoft HoloLens](images/windows-device-portal-performance-tracing-page-1000px.png)<br>
*Prestazioni traccia pagina in Windows Device Portal in Microsoft HoloLens*

Acquisire [Windows Performance Recorder](https://msdn.microsoft.com/library/windows/hardware/hh448205.aspx) le tracce (WPR) di HoloLens.
* **Profili disponibili**: Selezionare il profilo WPR l'elenco a discesa e fare clic o toccare **avviare** per avviare la registrazione.
* **I profili personalizzati**: Fare clic o toccare **esplorare** per scegliere un profilo WPR dal PC. Tocca o fai clic su **Upload and start** per avviare la traccia.

Per arrestare la traccia fare clic sul collegamento arresta. Non chiudere questa pagina fino a quando non viene completato il download di file di traccia.

I file ETL acquisiti possono essere aperti per l'analisi in [Windows Performance Analyzer](https://msdn.microsoft.com/library/windows/hardware/hh448170.aspx).

### <a name="processes"></a>Processi

![Pagina dei processi in Windows Device Portal in Microsoft HoloLens](images/windows-device-portal-running-processes-page-1000px.png)<br>
*Pagina dei processi in Windows Device Portal in Microsoft HoloLens*

La pagina dei processi mostra i dettagli sui processi attualmente in esecuzione. Sono inclusi sia processi di sistema sia app.

### <a name="system-performance"></a>System Performance

![Pagina delle prestazioni di sistema in Windows Device Portal in Microsoft HoloLens](images/windows-device-portal-system-performance-page-1000px.png)<br>
*Pagina delle prestazioni di sistema in Windows Device Portal in Microsoft HoloLens*

La pagina delle prestazioni mostra grafici in tempo reale con informazioni di diagnostica di sistema, come consumo energetico, frequenza dei fotogrammi e carico della CPU.

Ecco le metriche disponibili:
* **SoC power**: Istantaneo system on chip consumi energetici, calcolato su un minuto
* **Alimentazione del sistema**: Sistema istantaneo i consumi energetici, calcolato su un minuto
* **Frequenza dei fotogrammi**: Fotogrammi al secondo, hai perso VBlanks al secondo e consecutivi VBlanks mancanti
* **GPU**: Utilizzo del motore di GPU, percentuale del totale disponibile
* **CPU**: percentuale del totale disponibile
* **I/O**: Letture e scritture
* **Rete**: Ricevuti e inviati
* **Memoria**: Paging totale, in uso, esegue il commit e non di paging

### <a name="apps"></a>App

![Pagina delle App in Windows Device Portal in Microsoft HoloLens](images/windows-device-portal-apps-page-1000px.png)<br>
*Pagina delle App in Windows Device Portal in Microsoft HoloLens*

Consente di gestire le app installate di HoloLens.
* **Le app installate**: Rimuovere e avviare le app.
* **Esecuzione di app**: Elenca le app che sono in esecuzione.
* **Installare app**: Selezionare i pacchetti dell'app per l'installazione da una cartella in/rete del computer.
* **Dipendenza**: Aggiungere le dipendenze per le app che si desidera installare.
* **Distribuire**: Distribuire l'app selezionata e le dipendenze di HoloLens.

### <a name="app-crash-dumps"></a>Dump di arresto anomalo dell'App

![Pagina esegue il dump di arresto anomalo dell'App in Windows Device Portal in Microsoft HoloLens](images/windows-device-portal-dev-apps-crash-dumps-page-1000px.png)<br>
*Pagina esegue il dump di arresto anomalo dell'App in Windows Device Portal in Microsoft HoloLens*

In questa pagina puoi raccogliere i dump di arresto anomalo del sistema per le tue app trasferite localmente. Verificare i **arresto anomalo del sistema esegue il dump abilitata** casella di controllo per ogni app per la quale si desidera raccogliere dump di arresto anomalo del sistema. Torna in questa pagina per raccogliere i dump di arresto anomalo del sistema. I file di dump possono essere [aperto in Visual Studio per eseguire il debug](https://msdn.microsoft.com/library/d5zhxt22.aspx).

### <a name="file-explorer"></a>Esplora file

![Pagina Esplora file in Windows Device Portal in Microsoft HoloLens](images/fileexplorer-1000px.png)<br>
*Pagina Esplora file in Windows Device Portal in Microsoft HoloLens*

Usare Esplora file per esplorare, caricare e scaricare i file. È possibile lavorare con i file nella cartella documenti, la cartella immagini e nelle cartelle di archiviazione locale per le app che è stato distribuito da Visual Studio o il dispositivo dal portale.

### <a name="kiosk-mode"></a>Modalità tutto schermo

>[!NOTE]
>Modalità schermo intero è disponibile solo con il [Microsoft HoloLens Commercial Suite](commercial-features.md).

Verificare i [configurare HoloLens in modalità tutto schermo](https://docs.microsoft.com/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803) articolo nell'interfaccia Windows IT Pro per aggiornate istruzioni sull'abilitazione della modalità tutto schermo tramite Windows Device Portal.

### <a name="logging"></a>Registrazione

![Pagina di registrazione in Windows Device Portal in Microsoft HoloLens](images/windows-device-portal-logging-page-1000px.png)<br>
*Pagina di registrazione in Windows Device Portal in Microsoft HoloLens*

Consente di gestire in tempo reale Event Tracing for Windows (ETW) su di HoloLens.

Controllare **nascondere i provider** per visualizzare i **eventi** elencare solo.
* **I provider registrati**: Selezionare il provider ETW e il livello di traccia. Il valore del livello di traccia può indicare una delle situazioni seguenti:
   1. Chiusura o terminazione anomala
   2. Errori gravi
   3. Avvisi
   4. Avvisi non di errore

Tocca o fai clic su **Enable** per avviare la traccia. Il provider viene aggiunto all'elenco a discesa **Enabled Providers**.
* **Provider personalizzati**: Selezionare un provider ETW personalizzato e il livello di traccia. Identifica il provider tramite il relativo GUID. Non includere parentesi nel GUID.
* **Provider abilitati**: Elenca i provider attivati. Seleziona un provider nell'elenco a discesa e tocca o fai clic su **Disable** per arrestare la traccia. Tocca o fai clic su **Stop** per sospendere tutte le operazioni di traccia.
* **Cronologia provider**: Mostra i provider ETW che sono stati abilitati durante la sessione corrente. Tocca o fai clic su **Enable** per attivare un provider disabilitato. Tocca o fai clic su **Clear** per cancellare la cronologia.
* **gli eventi**: Elenca gli eventi ETW nell'elenco dei provider selezionati in formato tabella. La tabella viene aggiornata in tempo reale. Sotto la tabella, fare clic sui **chiaro** pulsante per eliminare tutti gli eventi ETW dalla tabella. Questa operazione non disabilita alcun provider. Puoi fare clic su **Save to file** per esportare gli eventi ETW attualmente raccolti in un file CSV locale.
* **I filtri**: Consentono di filtrare gli eventi ETW raccolti dall'ID, parola chiave, livello, nome del Provider, nome dell'attività o testo. È possibile combinare tra loro diversi criteri:
   1. Per applicare criteri alla stessa proprietà - eventi in grado di soddisfare uno di questi criteri vengono visualizzati.
   2. Per i criteri di applicazione a diverse proprietà - eventi devono soddisfare tutti i criteri

Ad esempio, è possibile specificare i criteri *(nome dell'attività contiene 'Foo' o 'Bar') e (testo contiene 'error' o 'warning')*

### <a name="simulation"></a>Di simulazione

![Pagina di simulazione in Windows Device Portal in Microsoft HoloLens](images/windows-device-portal-simulation-page-1000px.png)<br>
*Pagina di simulazione in Windows Device Portal in Microsoft HoloLens*

Ti permette di registrare e riprodurre dati di input per il testing.
* **Acquisire chat room**: Consente di scaricare un file locale simulato che contiene la rete mesh di mapping spaziale per ambiente circostante dell'utente. Nome chat room, quindi scegliere **acquisire** per salvare i dati come file .xef nel PC. Questo file può essere caricato nell'emulatore di HoloLens.
* **La registrazione**: Controllare i flussi di record, la registrazione, assegnare un nome e fare clic o toccare **Record** avviare registrazione. Eseguire le azioni con di HoloLens e quindi fare clic su **arrestare** per salvare i dati come file .xef nel PC. Questo file può essere caricato nell'emulatore di HoloLens o nel dispositivo stesso.
* **La riproduzione**: Fare clic o toccare **caricamento registrazione** per selezionare un file xef dal PC e inviare i dati di HoloLens.
* **Controllo modalità**: Selezionare **predefinite** o **simulazione** dall'elenco a discesa e fare clic o toccare il **impostare** pulsante per selezionare la modalità di HoloLens. Scegliendo "Simulation" vengono disabilitati i sensori reali in HoloLens e al loro posto vengono usati i dati di simulazione caricati. Se passi a "Simulation", HoloLens non risponde all'utente reale fino a quando non torni a "Default".

### <a name="networking"></a>Rete

![Pagina di funzionalità di rete in Windows Device Portal in Microsoft HoloLens](images/windows-device-portal-networking-page-1000px.png)<br>
*Pagina di funzionalità di rete in Windows Device Portal in Microsoft HoloLens*

Gestisce le connessioni Wi-Fi in di HoloLens.
* **Wi-Fi schede**: Selezionare un adattatore Wi-Fi e un profilo utilizzando i controlli elenco a discesa. Fare clic o toccare **Connect** per utilizzare l'adapter selezionato.
* **Reti disponibili**: Elenca le reti Wi-Fi che possono connettersi le HoloLens. Fare clic o toccare **Aggiorna** per aggiornare l'elenco.
* **Configurazione IP**: Mostra l'indirizzo IP e altri dettagli della connessione di rete.

### <a name="virtual-input"></a>Virtual Input

![Pagina di Input virtuale in Windows Device Portal in Microsoft HoloLens](images/windows-device-portal-virtual-input-page-1000px.png)<br>
*Pagina di Input virtuale in Windows Device Portal in Microsoft HoloLens*

Invia l'input da tastiera dal computer remoto a HoloLens.

Fare clic o toccare l'area sotto **tastiera virtuale** per abilitare la sequenza di tasti l'invio di HoloLens. Digitare il **Input di testo** nella casella di testo e fare clic o toccare **inviare** per inviare le pressioni di tasti per l'app attiva.

## <a name="device-portal-rest-apis"></a>Dell'API REST del portale dei dispositivi

Viene creato tutto nel portale di dispositivo in cima [dell'API REST](device-portal-api-reference.md) facoltativamente utilizzabile per accedere ai dati e controllare il dispositivo a livello di codice.

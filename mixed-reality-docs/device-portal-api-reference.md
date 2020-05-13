---
title: Informazioni di riferimento sulle API di Portale di dispositivi
description: Informazioni di riferimento sulle API per il portale per dispositivi Windows in HoloLens
author: jonmlyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, portale per dispositivi Windows, API
ms.openlocfilehash: 8c9d60f458cddd3ba258aed0ee82f7aa16c10ba6
ms.sourcegitcommit: 6d9d01d53137435c787f247f095d5255581695fc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/12/2020
ms.locfileid: "83227961"
---
# <a name="device-portal-api-reference"></a>Informazioni di riferimento sulle API di Portale di dispositivi

Tutti gli elementi del [portale per dispositivi Windows](using-the-windows-device-portal.md) sono basati sulle API REST che è possibile usare per accedere ai dati e controllare il dispositivo a livello di codice.

## <a name="app-deloyment"></a>Deloyment app

**/API/app/PackageManager/Package (DELETE)**

Disinstalla un'app

Parametri
* Package: nome file del pacchetto da disinstallare.

**/API/app/PackageManager/Package (POST)**

Installa un'app

Parametri
* Package: nome file del pacchetto da installare.

Payload
* corpo HTTP conforme a più parti

**/API/app/packagemanager/packages (GET)**

Recupera l'elenco delle app installate nel sistema con i dettagli

Restituisce i dati
* Elenco dei pacchetti installati con i dettagli

**/API/app/PackageManager/state (GET)**

Ottiene lo stato dell'installazione dell'app in corso

## <a name="dump-collection"></a>Raccolta dei dump

**/API/debug/dump/usermode/CrashControl (DELETE)**

Disabilita la raccolta dei dump di arresto anomalo del sistema per un'app sideload

Parametri
* packageFullname: nome pacchetto

**/API/debug/dump/usermode/CrashControl (GET)**

Ottiene le impostazioni per la raccolta di dump di arresto anomalo di sideload

Parametri
* packageFullname: nome pacchetto

**/API/debug/dump/usermode/CrashControl (POST)**

Abilita e imposta le impostazioni di controllo dump per un'app sideload

Parametri
* packageFullname: nome pacchetto

**/API/debug/dump/usermode/crashdump (DELETE)**

Elimina un dump di arresto anomalo del sistema per un'app sideload

Parametri
* packageFullname: nome pacchetto
* fileName: dump nome file

**/API/debug/dump/usermode/crashdump (GET)**

Recupera un dump di arresto anomalo del sistema per un'app sideload

Parametri
* packageFullname: nome pacchetto
* fileName: dump nome file

Restituisce i dati
* File dump. Esaminare con WinDbg o Visual Studio

**/API/debug/dump/usermode/Dumps (GET)**

Restituisce l'elenco di tutti i dump di arresto anomalo del sistema per le app sideload

Restituisce i dati
* Elenco dei dump di arresto anomalo del sistema per app caricata sul lato

## <a name="etw"></a>ETW

**/API/ETW/Providers (GET)**

Enumera i provider registrati

Restituisce i dati
* Elenco di provider, nome descrittivo e GUID

**/API/ETW/Session/realtime (GET/WebSocket)**

Crea una sessione ETW in tempo reale. gestito tramite WebSocket.

Restituisce i dati
* Eventi ETW dai provider abilitati

## <a name="holographic-os"></a>Sistema operativo olografico

**/API/Holographic/OS/ETW/customproviders (GET)**

Restituisce un elenco di provider ETW specifici di HoloLens non registrati con il sistema

**/API/Holographic/OS/Services (GET)**

Restituisce gli Stati di tutti i servizi in esecuzione.

**/API/Holographic/OS/Settings/IPD (GET)**

Ottiene il dip archiviato (distanza interpupillare) in millimetri

**/API/Holographic/OS/Settings/IPD (POST)**

Imposta il dpi

Parametri
* dpi: nuovo valore di DPI da impostare in millimetri

**/API/Holographic/OS/webmanagement/Settings/HTTPS (GET)**

Ottenere richieste HTTPS per Device Portal

**/API/Holographic/OS/webmanagement/Settings/HTTPS (POST)**

Imposta i requisiti HTTPS per il portale del dispositivo

Parametri
* obbligatorio: Sì, no o default

## <a name="holographic-perception"></a>Percezione olografica

**/API/Holographic/Perception/client (GET/WebSocket)**

Accetta gli aggiornamenti WebSocket ed esegue un client di percezione che invia gli aggiornamenti a 30 fps.

Parametri
* ClientMode: "Active" forza la modalità di rilevamento visivo quando non può essere stabilita passivamente

## <a name="holographic-thermal"></a>Termica olografica

**/API/Holographic/Thermal/stage (GET)**

Ottenere la fase termica del dispositivo (0 normale, 1 caldo, 2 critico)

## <a name="perception-simulation-control"></a>Controllo della simulazione della percezione

**/API/Holographic/Simulation/Control/mode (GET)**

Ottenere la modalità di simulazione

**/API/Holographic/Simulation/Control/mode (POST)**

Impostare la modalità di simulazione

Parametri
* Mode: modalità simulazione: predefinita, simulazione, remota, Legacy

**/API/Holographic/Simulation/Control/Stream (DELETE)**

Eliminare un flusso di controllo.

**/API/Holographic/Simulation/Control/Stream (GET/WebSocket)**

Aprire una connessione Web socket per un flusso di controllo.

**/API/Holographic/Simulation/Control/Stream (POST)**

Creare un flusso di controllo (priorità obbligatoria) o pubblicare i dati in un flusso creato (streamId richiesto). È previsto che i dati inviati siano di tipo ' Application/ottetto-Stream '.

**/API/Holographic/Simulation/Display/Stream (GET/WebSocket)**

Richiedere un flusso video di simulazione contenente il contenuto di cui è stato eseguito il rendering nella visualizzazione del sistema in modalità "simulazione".  Inizialmente verrà inviata un'intestazione di descrittore di formato semplice, seguita da trame con codifica H. 264, ognuna preceduta da un'intestazione che indica l'indice degli occhi e le dimensioni della trama.

## <a name="perception-simulation-playback"></a>Riproduzione della simulazione di percezione

**/API/Holographic/Simulation/playback/file (DELETE)**

Eliminare una registrazione.

Parametri
* registrazione: nome della registrazione da eliminare.

**/API/Holographic/Simulation/playback/file (POST)**

Caricare una registrazione.

**/API/Holographic/Simulation/playback/Files (GET)**

Ottenere tutte le registrazioni.

**/API/Holographic/Simulation/playback/Session (GET)**

Ottenere lo stato di riproduzione corrente di una registrazione.

Parametri
* registrazione: nome della registrazione.

**/API/Holographic/Simulation/playback/Session/file (DELETE)**

Scaricare una registrazione.

Parametri
* registrazione: nome della registrazione da scaricare.

**/API/Holographic/Simulation/playback/Session/file (POST)**

Caricare una registrazione.

Parametri
* registrazione: nome della registrazione da caricare.

**/API/Holographic/Simulation/playback/Session/Files (GET)**

Ottenere tutte le registrazioni caricate.

**/API/Holographic/Simulation/playback/Session/pause (POST)**

Sospendere la registrazione.

Parametri
* registrazione: nome della registrazione.

**/API/Holographic/Simulation/playback/Session/Play (POST)**

Riprodurre una registrazione.

Parametri
* registrazione: nome della registrazione.

**/API/Holographic/Simulation/playback/Session/Stop (POST)**

Arrestare una registrazione.

Parametri
* registrazione: nome della registrazione.

**/API/Holographic/Simulation/playback/Session/types (GET)**

Ottenere i tipi di dati in una registrazione caricata.

Parametri
* registrazione: nome della registrazione.

## <a name="perception-simulation-recording"></a>Registrazione della simulazione della percezione

**/API/Holographic/Simulation/Recording/Start (POST)**

Avviare una registrazione. Solo una singola registrazione può essere attiva in una sola volta. È necessario impostare una delle intestazioni Head, Hands, spatialMapping o Environment.

Parametri
* Head: impostare su 1 per registrare i dati Head.
* Hands: impostare su 1 per registrare i dati della mano.
* spatialMapping: impostare su 1 per registrare il mapping spaziale.
* ambiente: impostare su 1 per registrare i dati dell'ambiente.
* Nome: nome della registrazione.
* singleSpatialMappingFrame: impostare su 1 per registrare un singolo frame di mapping spaziale.

**/API/Holographic/Simulation/Recording/status (GET)**

Ottenere lo stato di registrazione.

**/API/Holographic/Simulation/Recording/Stop (GET)**

Arrestare la registrazione corrente. La registrazione verrà restituita come file.

## <a name="mixed-reality-capture"></a>Mixed Reality Capture

**/API/Holographic/MRC/file (GET)**

Scarica un file di realtà mista dal dispositivo. Usare il parametro di query op = Stream per il flusso.

Parametri
* filename: Name, hex64 codificato del file video da ottenere
* op: Stream

**/API/Holographic/MRC/file (DELETE)**

Elimina una registrazione di realtà mista dal dispositivo.

Parametri
* filename: Name, hex64 codificato del file da eliminare

**/API/Holographic/MRC/Files (GET)**

Restituisce l'elenco dei file di realtà mista archiviati nel dispositivo

**/API/Holographic/MRC/Photo (POST)**

Accetta una foto della realtà mista e crea un file nel dispositivo

Parametri
* Holo: Acquisisci ologrammi: true o false (il valore predefinito è false)
* PV: Capture PV fotocamera: true o false (il valore predefinito è false)
* RenderFromCamera: (solo HoloLens 2) Render dal punto di vista della fotocamera Photo/video: true o false (il valore predefinito è true)

**/API/Holographic/MRC/Settings (GET)**

Ottiene le impostazioni predefinite di acquisizione della realtà mista

**/API/Holographic/MRC/Settings (POST)**

Imposta le impostazioni predefinite di acquisizione della realtà mista.  Alcune di queste impostazioni vengono applicate all'acquisizione di foto e video di MRC del sistema.

**/API/Holographic/MRC/status (GET)**

Ottiene lo stato della realtà mista registrata (in esecuzione, arrestata)

**/API/Holographic/MRC/Thumbnail (GET)**

Ottiene l'immagine di anteprima per il file specificato.

Parametri
* filename: Name, hex64 codificato, del file per il quale viene richiesta l'anteprima

**/API/Holographic/MRC/video/Control/Start (POST)**

Avvia una registrazione di realtà mista

Parametri
* Holo: Acquisisci ologrammi: true o false (il valore predefinito è false)
* PV: Capture PV fotocamera: true o false (il valore predefinito è false)
* MIC: Acquisisci microfono: true o false (il valore predefinito è false)
* loopback: Acquisisci audio dell'app: true o false (il valore predefinito è false)
* RenderFromCamera: (solo HoloLens 2) Render dal punto di vista della fotocamera Photo/video: true o false (il valore predefinito è true)
* Vstab: (solo HoloLens 2) Abilita stabilizzazione video: true o false (il valore predefinito è true)
* vstabbuffer: (solo HoloLens 2) latenza buffer di stabilizzazione video: da 0 a 30 fotogrammi (il valore predefinito è 15 fotogrammi)

**/API/Holographic/MRC/video/Control/Stop (POST)**

Arresta la registrazione della realtà mista corrente

## <a name="mixed-reality-streaming"></a>Flusso di realtà mista

HoloLens supporta l'anteprima in tempo reale della realtà mista tramite il download in blocchi di un MP4 frammentato.

I flussi di realtà mista condividono lo stesso set di parametri per controllare gli elementi acquisiti:
* Holo: acquisire gli ologrammi: true o false
* PV: acquisire la fotocamera PV: true o false
* MIC: Acquisisci microfono: true o false
* loopback: Acquisisci audio dell'app: true o false

Se non viene specificato alcun valore, verranno acquisiti gli ologrammi, la fotocamera foto/video e l'audio dell'app.<br>
Se viene specificato any: i parametri non specificati verranno impostati su false.

Parametri facoltativi (solo HoloLens 2)
* RenderFromCamera: rendering dal punto di vista della fotocamera Photo/video: true o false (il valore predefinito è true)
* Vstab: Abilita stabilizzazione video: true o false (il valore predefinito è false)
* vstabbuffer: latenza buffer di stabilizzazione video: da 0 a 30 fotogrammi (il valore predefinito è 15 fotogrammi)

**/API/Holographic/Stream/Live.mp4 (GET)**

Flusso di 5Mbit 1280x720p 30 fps.

**/API/Holographic/Stream/live_high. mp4 (GET)**

Flusso di 5Mbit 1280x720p 30 fps.

**/API/Holographic/Stream/live_med. mp4 (GET)**

Un flusso 854x480p 30 fps da 2 MB.

**/API/Holographic/Stream/live_low. mp4 (GET)**

Flusso 428x240p 15fps 0.6 Mbit.

## <a name="networking"></a>Rete

**/API/networking/ipconfig (GET)**

Ottiene la configurazione IP corrente

## <a name="os-information"></a>Informazioni sul sistema operativo

**/API/OS/info (GET)**

Ottiene le informazioni sul sistema operativo

**/API/OS/MachineName (GET)**

Ottiene il nome del computer

**/API/OS/MachineName (POST)**

Imposta il nome del computer

Parametri
* Nome: nome del nuovo computer, hex64 codificato, per impostare su

## <a name="performance-data"></a>Dati sulle prestazioni

**/API/ResourceManager/processes (GET)**

Restituisce l'elenco dei processi in esecuzione con i dettagli

Restituisce i dati
* JSON con elenco di processi e dettagli per ogni processo

**/API/ResourceManager/systemperf (GET)**

Restituisce le statistiche sulle prestazioni di sistema (lettura/scrittura di I/O, statistiche sulla memoria e così via.

Restituisce i dati
* JSON con informazioni di sistema: CPU, GPU, memoria, rete, IO

## <a name="power"></a>Power

**/API/Power/Battery (GET)**

Ottiene lo stato corrente della batteria

**/API/Power/State (GET)**

Controlla se il sistema è in uno stato di alimentazione basso

## <a name="remote-control"></a>Controllo remoto

**/API/Control/Restart (POST)**

Riavvia il dispositivo di destinazione

**/API/Control/Shutdown (POST)**

Arresta il dispositivo di destinazione

## <a name="task-manager"></a>Gestione attività

**/API/taskmanager/app (DELETE)**

Arresta un'app moderna

Parametri
* pacchetto: nome completo del pacchetto dell'app, codificato in hex64
* forcestop: forza l'arresto di tutti i processi (= Yes)

**/API/taskmanager/app (POST)**

Avvia un'app moderna

Parametri
* AppID: PRAID dell'app da avviare, hex64 codificato
* pacchetto: nome completo del pacchetto dell'app, codificato in hex64

## <a name="wifi-management"></a>Gestione Wi-Fi

**/API/WiFi/Interfaces (GET)**

Enumera le interfacce di rete wireless

Restituisce i dati
* Elenco di interfacce wireless con dettagli (GUID, descrizione e così via)

**/API/WiFi/Network (DELETE)**

Elimina un profilo associato a una rete in un'interfaccia specificata

Parametri
* interfaccia: GUID dell'interfaccia di rete
* profilo: nome profilo

**/API/WiFi/Networks (GET)**

Enumera le reti wireless sull'interfaccia di rete specificata

Parametri
* interfaccia: GUID dell'interfaccia di rete

Restituisce i dati
* Elenco di reti wireless disponibili nell'interfaccia di rete con i dettagli

**/API/WiFi/Network (POST)**

Si connette o si disconnette a una rete sull'interfaccia specificata

Parametri
* interfaccia: GUID dell'interfaccia di rete
* SSID: SSID, hex64 codificato, per la connessione a
* op: connessione o disconnessione
* CreateProfile: Sì o no
* chiave: chiave condivisa, codificato in hex64

## <a name="windows-performance-recorder"></a>Registratore prestazioni Windows

**/API/WPR/customtrace (POST)**

Carica un profilo WPR e avvia la traccia usando il profilo caricato.

Payload
* corpo HTTP conforme a più parti

Restituisce i dati
* Restituisce lo stato della sessione WPR.

**/API/WPR/status (GET)**

Recupera lo stato della sessione WPR

Restituisce i dati
* Stato della sessione WPR.

**/API/WPR/Trace (GET)**

Arresta una sessione di traccia WPR (performance)

Restituisce i dati
* Restituisce il file ETL di traccia

**/API/WPR/Trace (POST)**

Avvia una sessione di traccia WPR (performance)

Parametri
* profilo: nome profilo. I profili disponibili sono archiviati in perfprofiles/Profiles. JSON

Restituisce i dati
* All'avvio, restituisce lo stato della sessione WPR.

## <a name="see-also"></a>Vedere anche
* [Avviare il Portale di dispositivi di Windows](using-the-windows-device-portal.md)
* [Informazioni di riferimento sulle API del portale per dispositivi (UWP)](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)

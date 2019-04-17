---
title: Portale del dispositivo di riferimento all'API
description: Riferimento API per il Windows Device Portal in HoloLens
author: JonMLyons
ms.author: JLyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, Windows Device Portal, API
ms.openlocfilehash: 507ab98734adea80d0aad41d99124e3d91846f28
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603276"
---
# <a name="device-portal-api-reference"></a>Portale del dispositivo di riferimento all'API

Tutti gli elementi di [Windows Device Portal](using-the-windows-device-portal.md) si basa sull'API REST che è possibile usare per accedere ai dati e controllare il dispositivo a livello di codice.

## <a name="app-deloyment"></a>Distribuzione di App

**/API/App/packagemanager/package (DELETE)**

Disinstalla un'app

Parametri
* pacchetto: Nome del file del pacchetto da disinstallare.

**/api/app/packagemanager/package (POST)**

Installa un'App

Parametri
* pacchetto: Nome del file del pacchetto da installare.

payload
* più parti corpo http conforme

**/api/app/packagemanager/packages (GET)**

Recupera l'elenco delle App installate nel sistema, con dettagli

Restituisce i dati
* Elenco dei pacchetti installati con i dettagli

**/api/app/packagemanager/state (GET)**

Ottiene lo stato dell'installazione dell'app lo stato di avanzamento

## <a name="dump-collection"></a>Raccolta dei dump

**/API/debug/dump/usermode/CrashControl (DELETE)**

Disabilita l'arresto anomalo del sistema di raccolta dei dump per un'app con sideload

Parametri
* packageFullname: nome del pacchetto

**/api/debug/dump/usermode/crashcontrol (GET)**

Ottiene le impostazioni per le app con sideload raccolta dei dump di arresto anomalo del sistema

Parametri
* packageFullname: nome del pacchetto

**/api/debug/dump/usermode/crashcontrol (POST)**

Attiva e configura le impostazioni di controllo di dump per un'app con sideload

Parametri
* packageFullname: nome del pacchetto

**/API/debug/dump/usermode/crashdump (DELETE)**

Elimina un dump di arresto anomalo del sistema per un'app con sideload

Parametri
* packageFullname: nome del pacchetto
* nome file: nome del file dump

**/api/debug/dump/usermode/crashdump (GET)**

Recupera un dump di arresto anomalo del sistema per un'app con sideload

Parametri
* packageFullname: nome del pacchetto
* nome file: nome del file dump

Restituisce i dati
* File di dump. Controllare con WinDbg o di Visual Studio

**/api/debug/dump/usermode/dumps (GET)**

Restituisce un elenco di tutti i dettagli di arresto anomalo per le app con sideload

Restituisce i dati
* Elenco di arresto anomalo del sistema esegue il dump per ogni app caricata lato

## <a name="etw"></a>ETW

**/api/etw/providers (GET)**

Enumera i provider registrati

Restituisce i dati
* Elenco dei provider, nome descrittivo e GUID

**/api/etw/session/realtime (GET/WebSocket)**

Crea una sessione ETW in tempo reale. gestita su un websocket.

Restituisce i dati
* Eventi ETW da provider attivati

## <a name="holographic-os"></a>Sistema operativo olografico

**/api/holographic/os/etw/customproviders (GET)**

Restituisce un elenco di provider ETW specifico HoloLens che non sono registrati con il sistema

**/api/holographic/os/services (GET)**

Restituisce gli stati di tutti i servizi in esecuzione.

**/api/holographic/os/settings/ipd (GET)**

Ottiene il IPD stored (Interpupillary distanza) in millimetri

**/api/holographic/os/settings/ipd (POST)**

Imposta IPD

Parametri
* IPD: Nuovo valore IPD vengano impostati in millimetri

**/api/holographic/os/webmanagement/settings/https (GET)**

Ottenere richieste HTTPS per Device Portal

**/api/holographic/os/webmanagement/settings/https (POST)**

Imposta i requisiti di HTTPS per il portale del dispositivo

Parametri
* obbligatorio: Sì, no o default

## <a name="holographic-perception"></a>Percezione holographic

**/api/holographic/perception/client (GET/WebSocket)**

Accetta gli aggiornamenti di websocket ed esegue un client di percezione che invia gli aggiornamenti di 30 fps.

Parametri
* clientmode: "attivo" forza la modalità di rilevamento visual quando non è possibile stabilire passivamente

## <a name="holographic-thermal"></a>Holographic termico

**/api/holographic/thermal/stage (GET)**

Ottenere la fase termica del dispositivo (0 normale, 1 warm, 2 critico)

## <a name="perception-simulation-control"></a>Controllo di simulazione di percezione

**/api/holographic/simulation/control/mode (GET)**

Ottenere la modalità di simulazione

**/api/holographic/simulation/control/mode (POST)**

Impostare la modalità di simulazione

Parametri
* modalità: modalità di simulazione: predefinito, simulazione, remote, legacy

**/API/holographic/Simulation/Control/Stream (DELETE)**

Eliminare un flusso di controllo.

**/api/holographic/simulation/control/stream (GET/WebSocket)**

Aprire una connessione web socket per un flusso di controllo.

**/api/holographic/simulation/control/stream (POST)**

Creare un flusso di controllo (priorità è obbligatorio) o inviare i dati in un flusso creato (streamId richiesto). I dati inseriti dovrebbe essere di tipo ' application/octet-stream'.

## <a name="perception-simulation-playback"></a>Riproduzione di simulazione di percezione

**/API/holographic/Simulation/Playback/file (DELETE)**

Eliminare una registrazione.

Parametri
* la registrazione: Nome della registrazione per eliminare.

**/API/holographic/Simulation/Playback/file (POST)**

Caricare una registrazione.

**/API/holographic/Simulation/Playback/Files (GET)**

Ottenere tutte le registrazioni.

**/API/holographic/Simulation/Playback/Session (GET)**

Ottenere lo stato corrente di riproduzione della registrazione.

Parametri
* la registrazione: Nome della registrazione.

**/API/holographic/Simulation/Playback/Session/file (DELETE)**

Scaricare una registrazione.

Parametri
* la registrazione: Nome della registrazione per scaricare.

**/api/holographic/simulation/playback/session/file (POST)**

Caricare una registrazione.

Parametri
* la registrazione: Nome della registrazione per il caricamento.

**/API/holographic/Simulation/Playback/Session/Files (GET)**

Ottenere registrazioni tutto caricate.

**/API/holographic/Simulation/Playback/Session/pause (POST)**

Sospendere la registrazione.

Parametri
* la registrazione: Nome della registrazione.

**/API/holographic/Simulation/Playback/Session/Play (POST)**

Riprodurre una registrazione.

Parametri
* la registrazione: Nome della registrazione.

**/api/holographic/simulation/playback/session/stop (POST)**

Arrestare la registrazione.

Parametri
* la registrazione: Nome della registrazione.

**/API/holographic/Simulation/Playback/Session/Types (GET)**

Ottenere i tipi di dati in una registrazione caricata.

Parametri
* la registrazione: Nome della registrazione.

## <a name="perception-simulation-recording"></a>Registrazione di simulazione di percezione

**/api/holographic/simulation/recording/start (POST)**

Avviare una registrazione. Solo una singola registrazione può essere attiva contemporaneamente. Head, mani, spatialMapping o ambiente deve essere impostata.

Parametri
* Head: Impostare su 1 per registrare i dati head.
* pratico: Impostare su 1 per registrare manualmente i dati.
* spatialMapping: Impostare su 1 per registrare mapping spaziale.
* ambiente: Impostare su 1 per registrare i dati di ambiente.
* nome: Nome della registrazione.
* singleSpatialMappingFrame: Impostare su 1 per registrare solo un frame solo mapping spaziale.

**/api/holographic/simulation/recording/status (GET)**

Ottenere la registrazione dello stato.

**/api/holographic/simulation/recording/stop (GET)**

Arrestare la registrazione corrente. La registrazione verrà restituita come un file.

## <a name="mixed-reality-capture"></a>Mixed Reality Capture

**/API/holographic/MRC/file (DELETE)**

Elimina una realtà mista di registrazione dal dispositivo.

Parametri
* nome file: Il nome, hex64 codificato, del file da eliminare

**/api/holographic/mrc/settings (GET)**

Ottiene il valore predefinito realtà mista le impostazioni di acquisizione

**/api/holographic/mrc/file (GET)**

Scarica un file di realtà mista dal dispositivo. Op usare = parametro di query di flusso per lo streaming.

Parametri
* nome file: Il nome, hex64 codificato, del file video di introduzione
* Op: flusso

**/api/holographic/mrc/thumbnail (GET)**

Ottiene l'immagine di anteprima per il file specificato.

Parametri
* nome file: Il nome, hex64 codificato, del file per cui viene richiesto l'anteprima

**/api/holographic/mrc/status (GET)**

Ottiene lo stato della realtà mista registrate (in esecuzione, arrestato)

**/API/holographic/MRC/Files (GET)**

Restituisce l'elenco dei file di realtà mista archiviati nel dispositivo

**/api/holographic/mrc/settings (POST)**

Imposta il valore predefinito realtà mista le impostazioni di acquisizione

**/api/holographic/mrc/video/control/start (POST)**

Avvia una registrazione di realtà mista

Parametri
* holo: acquisire vntana: true o false
* PV: acquisizione PV fotocamera: true o false
* MIC: acquisizione microfono: true o false
* loopback: acquisizione di app audio: true o false

**/api/holographic/mrc/video/control/stop (POST)**

Viene arrestata la registrazione di realtà mista di corrente

**/api/holographic/mrc/photo (POST)**

Scatta una foto di realtà mista e crea un file nel dispositivo

Parametri
* holo: acquisire vntana: true o false
* PV: acquisizione PV fotocamera: true o false

Realtà mista di Streaming

**/api/holographic/stream/live.mp4 (GET)**

Avviare un download in blocchi di un file MP4 frammentato

Parametri
* holo: acquisire vntana: true o false
* PV: acquisizione PV fotocamera: true o false
* MIC: acquisizione microfono: true o false
* loopback: acquisizione di app audio: true o false

**/api/holographic/stream/live_high.mp4 (GET)**

Avviare un download in blocchi di un file MP4 frammentato

Parametri
* holo: acquisire vntana: true o false
* PV: acquisizione PV fotocamera: true o false
* MIC: acquisizione microfono: true o false
* loopback: acquisizione di app audio: true o false

**/api/holographic/stream/live_low.mp4 (GET)**

Avviare un download in blocchi di un file MP4 frammentato

Parametri
* holo: acquisire vntana: true o false
* PV: acquisizione PV fotocamera: true o false
* MIC: acquisizione microfono: true o false
* loopback: acquisizione di app audio: true o false

**/api/holographic/stream/live_med.mp4 (GET)**

Avviare un download in blocchi di un file MP4 frammentato

Parametri
* holo: acquisire vntana: true o false
* PV: acquisizione PV fotocamera: true o false
* MIC: acquisizione microfono: true o false
* loopback: acquisizione di app audio: true o false

## <a name="networking"></a>Rete

**/api/networking/ipconfig (GET)**

Ottiene la configurazione ip corrente

## <a name="os-information"></a>Informazioni del sistema operativo

**/api/os/info (GET)**

Ottiene informazioni sul sistema operativo

**/API/OS/MachineName (GET)**

Ottiene il nome del computer

**/api/os/machinename (POST)**

Imposta il nome del computer

Parametri
* nome: Nuovo nome del computer, hex64 codificato, per impostare su

## <a name="performance-data"></a>Dati sulle prestazioni

**/api/resourcemanager/processes (GET)**

Restituisce l'elenco dei processi in esecuzione con i dettagli

Restituisce i dati
* JSON con l'elenco di processi e i dettagli per ogni processo

**/api/resourcemanager/systemperf (GET)**

Restituisce le statistiche delle prestazioni di sistema (i/o lettura/scrittura, statistiche di memoria e così via.

Restituisce i dati
* Struttura JSON con le informazioni di sistema: CPU, GPU, memoria, rete, i/o

## <a name="power"></a>Alimentazione

**/api/power/battery (GET)**

Ottiene lo stato della batteria corrente

**/api/power/state (GET)**

Controlla se il sistema si trova in uno stato di basso consumo energetico

## <a name="remote-control"></a>Controllo remoto

**/api/control/restart (POST)**

Riavvia il dispositivo di destinazione

**/api/control/shutdown (POST)**

Arresta il dispositivo di destinazione

## <a name="task-manager"></a>Gestione attività

**/api/taskmanager/app (DELETE)**

Arresta un'applicazione moderna

Parametri
* pacchetto: Nome completo del pacchetto dell'app, hex64 con codificata
* forcestop: Forzare tutti i processi da arrestare (= Sì)

**/api/taskmanager/app (POST)**

Avvia un'applicazione moderna

Parametri
* ID applicazione: Con codifica hex64 PRAID dell'app per iniziare,
* pacchetto: Nome completo del pacchetto dell'app, hex64 con codificata

## <a name="wifi-management"></a>Gestione connessione Wi-Fi

**/API/WiFi/Interfaces (GET)**

Enumera le interfacce di rete wireless

Restituisce i dati
* Elenco di interfacce senza fili con i dettagli (GUID, description e così via).

**/api/wifi/network (DELETE)**

Elimina un profilo associato a una rete in un'interfaccia specificata

Parametri
* interfaccia: guid dell'interfaccia di rete
* profilo: nome del profilo

**/api/wifi/networks (GET)**

Enumera le reti wireless nell'interfaccia di rete specificato

Parametri
* interfaccia: guid dell'interfaccia di rete

Restituisce i dati
* Elenco delle reti wireless disponibili nell'interfaccia di rete con i dettagli

**/api/wifi/network (POST)**

Si connette o disconnette a una rete nell'interfaccia specificata

Parametri
* interfaccia: guid dell'interfaccia di rete
* SSID: ssid, hex64 codificato, per connettersi a
* Op: connettere o disconnettere
* createprofile: yes o no
* chiave: hex64, chiave condivisa con codificata

## <a name="windows-performance-recorder"></a>Registrazione prestazioni Windows

**/api/wpr/customtrace (POST)**

Carica un profilo WPR e inizia la tracciatura utilizzando il profilo caricato.

payload
* più parti corpo http conforme

Restituisce i dati
* Restituisce lo stato di sessione WPR.

**/api/wpr/status (GET)**

Recupera lo stato della sessione WPR

Restituisce i dati
* Stato della sessione WPR.

**/api/wpr/trace (GET)**

Arresta una sessione di traccia WPR (prestazioni)

Restituisce i dati
* Restituisce il file ETL di traccia

**/api/wpr/trace (POST)**

Avvia una traccia di sessioni WPR (prestazioni)

Parametri
* profilo: Nome del profilo. Profili disponibili vengono archiviati in perfprofiles/profiles.json

Restituisce i dati
* Nel menu start, restituisce lo stato di sessione WPR.

## <a name="see-also"></a>Vedere anche
* [Utilizzando il Windows Device Portal](using-the-windows-device-portal.md)
* [Core portale dispositivo API reference (UWP)](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)

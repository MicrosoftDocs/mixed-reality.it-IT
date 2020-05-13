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
# <a name="device-portal-api-reference"></a><span data-ttu-id="430b0-104">Informazioni di riferimento sulle API di Portale di dispositivi</span><span class="sxs-lookup"><span data-stu-id="430b0-104">Device portal API reference</span></span>

<span data-ttu-id="430b0-105">Tutti gli elementi del [portale per dispositivi Windows](using-the-windows-device-portal.md) sono basati sulle API REST che è possibile usare per accedere ai dati e controllare il dispositivo a livello di codice.</span><span class="sxs-lookup"><span data-stu-id="430b0-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="430b0-106">Deloyment app</span><span class="sxs-lookup"><span data-stu-id="430b0-106">App deloyment</span></span>

<span data-ttu-id="430b0-107">**/API/app/PackageManager/Package (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="430b0-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="430b0-108">Disinstalla un'app</span><span class="sxs-lookup"><span data-stu-id="430b0-108">Uninstalls an app</span></span>

<span data-ttu-id="430b0-109">Parametri</span><span class="sxs-lookup"><span data-stu-id="430b0-109">Parameters</span></span>
* <span data-ttu-id="430b0-110">Package: nome file del pacchetto da disinstallare.</span><span class="sxs-lookup"><span data-stu-id="430b0-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="430b0-111">**/API/app/PackageManager/Package (POST)**</span><span class="sxs-lookup"><span data-stu-id="430b0-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="430b0-112">Installa un'app</span><span class="sxs-lookup"><span data-stu-id="430b0-112">Installs an App</span></span>

<span data-ttu-id="430b0-113">Parametri</span><span class="sxs-lookup"><span data-stu-id="430b0-113">Parameters</span></span>
* <span data-ttu-id="430b0-114">Package: nome file del pacchetto da installare.</span><span class="sxs-lookup"><span data-stu-id="430b0-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="430b0-115">Payload</span><span class="sxs-lookup"><span data-stu-id="430b0-115">Payload</span></span>
* <span data-ttu-id="430b0-116">corpo HTTP conforme a più parti</span><span class="sxs-lookup"><span data-stu-id="430b0-116">multi-part conforming http body</span></span>

<span data-ttu-id="430b0-117">**/API/app/packagemanager/packages (GET)**</span><span class="sxs-lookup"><span data-stu-id="430b0-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="430b0-118">Recupera l'elenco delle app installate nel sistema con i dettagli</span><span class="sxs-lookup"><span data-stu-id="430b0-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="430b0-119">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="430b0-119">Return data</span></span>
* <span data-ttu-id="430b0-120">Elenco dei pacchetti installati con i dettagli</span><span class="sxs-lookup"><span data-stu-id="430b0-120">List of installed packages with details</span></span>

<span data-ttu-id="430b0-121">**/API/app/PackageManager/state (GET)**</span><span class="sxs-lookup"><span data-stu-id="430b0-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="430b0-122">Ottiene lo stato dell'installazione dell'app in corso</span><span class="sxs-lookup"><span data-stu-id="430b0-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="430b0-123">Raccolta dei dump</span><span class="sxs-lookup"><span data-stu-id="430b0-123">Dump collection</span></span>

<span data-ttu-id="430b0-124">**/API/debug/dump/usermode/CrashControl (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="430b0-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="430b0-125">Disabilita la raccolta dei dump di arresto anomalo del sistema per un'app sideload</span><span class="sxs-lookup"><span data-stu-id="430b0-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="430b0-126">Parametri</span><span class="sxs-lookup"><span data-stu-id="430b0-126">Parameters</span></span>
* <span data-ttu-id="430b0-127">packageFullname: nome pacchetto</span><span class="sxs-lookup"><span data-stu-id="430b0-127">packageFullname : package name</span></span>

<span data-ttu-id="430b0-128">**/API/debug/dump/usermode/CrashControl (GET)**</span><span class="sxs-lookup"><span data-stu-id="430b0-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="430b0-129">Ottiene le impostazioni per la raccolta di dump di arresto anomalo di sideload</span><span class="sxs-lookup"><span data-stu-id="430b0-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="430b0-130">Parametri</span><span class="sxs-lookup"><span data-stu-id="430b0-130">Parameters</span></span>
* <span data-ttu-id="430b0-131">packageFullname: nome pacchetto</span><span class="sxs-lookup"><span data-stu-id="430b0-131">packageFullname : package name</span></span>

<span data-ttu-id="430b0-132">**/API/debug/dump/usermode/CrashControl (POST)**</span><span class="sxs-lookup"><span data-stu-id="430b0-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="430b0-133">Abilita e imposta le impostazioni di controllo dump per un'app sideload</span><span class="sxs-lookup"><span data-stu-id="430b0-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="430b0-134">Parametri</span><span class="sxs-lookup"><span data-stu-id="430b0-134">Parameters</span></span>
* <span data-ttu-id="430b0-135">packageFullname: nome pacchetto</span><span class="sxs-lookup"><span data-stu-id="430b0-135">packageFullname : package name</span></span>

<span data-ttu-id="430b0-136">**/API/debug/dump/usermode/crashdump (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="430b0-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="430b0-137">Elimina un dump di arresto anomalo del sistema per un'app sideload</span><span class="sxs-lookup"><span data-stu-id="430b0-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="430b0-138">Parametri</span><span class="sxs-lookup"><span data-stu-id="430b0-138">Parameters</span></span>
* <span data-ttu-id="430b0-139">packageFullname: nome pacchetto</span><span class="sxs-lookup"><span data-stu-id="430b0-139">packageFullname : package name</span></span>
* <span data-ttu-id="430b0-140">fileName: dump nome file</span><span class="sxs-lookup"><span data-stu-id="430b0-140">fileName : dump file name</span></span>

<span data-ttu-id="430b0-141">**/API/debug/dump/usermode/crashdump (GET)**</span><span class="sxs-lookup"><span data-stu-id="430b0-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="430b0-142">Recupera un dump di arresto anomalo del sistema per un'app sideload</span><span class="sxs-lookup"><span data-stu-id="430b0-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="430b0-143">Parametri</span><span class="sxs-lookup"><span data-stu-id="430b0-143">Parameters</span></span>
* <span data-ttu-id="430b0-144">packageFullname: nome pacchetto</span><span class="sxs-lookup"><span data-stu-id="430b0-144">packageFullname : package name</span></span>
* <span data-ttu-id="430b0-145">fileName: dump nome file</span><span class="sxs-lookup"><span data-stu-id="430b0-145">fileName : dump file name</span></span>

<span data-ttu-id="430b0-146">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="430b0-146">Return data</span></span>
* <span data-ttu-id="430b0-147">File dump.</span><span class="sxs-lookup"><span data-stu-id="430b0-147">Dump file.</span></span> <span data-ttu-id="430b0-148">Esaminare con WinDbg o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="430b0-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="430b0-149">**/API/debug/dump/usermode/Dumps (GET)**</span><span class="sxs-lookup"><span data-stu-id="430b0-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="430b0-150">Restituisce l'elenco di tutti i dump di arresto anomalo del sistema per le app sideload</span><span class="sxs-lookup"><span data-stu-id="430b0-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="430b0-151">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="430b0-151">Return data</span></span>
* <span data-ttu-id="430b0-152">Elenco dei dump di arresto anomalo del sistema per app caricata sul lato</span><span class="sxs-lookup"><span data-stu-id="430b0-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="430b0-153">ETW</span><span class="sxs-lookup"><span data-stu-id="430b0-153">ETW</span></span>

<span data-ttu-id="430b0-154">**/API/ETW/Providers (GET)**</span><span class="sxs-lookup"><span data-stu-id="430b0-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="430b0-155">Enumera i provider registrati</span><span class="sxs-lookup"><span data-stu-id="430b0-155">Enumerates registered providers</span></span>

<span data-ttu-id="430b0-156">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="430b0-156">Return data</span></span>
* <span data-ttu-id="430b0-157">Elenco di provider, nome descrittivo e GUID</span><span class="sxs-lookup"><span data-stu-id="430b0-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="430b0-158">**/API/ETW/Session/realtime (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="430b0-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="430b0-159">Crea una sessione ETW in tempo reale. gestito tramite WebSocket.</span><span class="sxs-lookup"><span data-stu-id="430b0-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="430b0-160">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="430b0-160">Return data</span></span>
* <span data-ttu-id="430b0-161">Eventi ETW dai provider abilitati</span><span class="sxs-lookup"><span data-stu-id="430b0-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="430b0-162">Sistema operativo olografico</span><span class="sxs-lookup"><span data-stu-id="430b0-162">Holographic OS</span></span>

<span data-ttu-id="430b0-163">**/API/Holographic/OS/ETW/customproviders (GET)**</span><span class="sxs-lookup"><span data-stu-id="430b0-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="430b0-164">Restituisce un elenco di provider ETW specifici di HoloLens non registrati con il sistema</span><span class="sxs-lookup"><span data-stu-id="430b0-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="430b0-165">**/API/Holographic/OS/Services (GET)**</span><span class="sxs-lookup"><span data-stu-id="430b0-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="430b0-166">Restituisce gli Stati di tutti i servizi in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="430b0-166">Returns the states of all services running.</span></span>

<span data-ttu-id="430b0-167">**/API/Holographic/OS/Settings/IPD (GET)**</span><span class="sxs-lookup"><span data-stu-id="430b0-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="430b0-168">Ottiene il dip archiviato (distanza interpupillare) in millimetri</span><span class="sxs-lookup"><span data-stu-id="430b0-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="430b0-169">**/API/Holographic/OS/Settings/IPD (POST)**</span><span class="sxs-lookup"><span data-stu-id="430b0-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="430b0-170">Imposta il dpi</span><span class="sxs-lookup"><span data-stu-id="430b0-170">Sets the IPD</span></span>

<span data-ttu-id="430b0-171">Parametri</span><span class="sxs-lookup"><span data-stu-id="430b0-171">Parameters</span></span>
* <span data-ttu-id="430b0-172">dpi: nuovo valore di DPI da impostare in millimetri</span><span class="sxs-lookup"><span data-stu-id="430b0-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="430b0-173">**/API/Holographic/OS/webmanagement/Settings/HTTPS (GET)**</span><span class="sxs-lookup"><span data-stu-id="430b0-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="430b0-174">Ottenere richieste HTTPS per Device Portal</span><span class="sxs-lookup"><span data-stu-id="430b0-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="430b0-175">**/API/Holographic/OS/webmanagement/Settings/HTTPS (POST)**</span><span class="sxs-lookup"><span data-stu-id="430b0-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="430b0-176">Imposta i requisiti HTTPS per il portale del dispositivo</span><span class="sxs-lookup"><span data-stu-id="430b0-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="430b0-177">Parametri</span><span class="sxs-lookup"><span data-stu-id="430b0-177">Parameters</span></span>
* <span data-ttu-id="430b0-178">obbligatorio: Sì, no o default</span><span class="sxs-lookup"><span data-stu-id="430b0-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="430b0-179">Percezione olografica</span><span class="sxs-lookup"><span data-stu-id="430b0-179">Holographic Perception</span></span>

<span data-ttu-id="430b0-180">**/API/Holographic/Perception/client (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="430b0-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="430b0-181">Accetta gli aggiornamenti WebSocket ed esegue un client di percezione che invia gli aggiornamenti a 30 fps.</span><span class="sxs-lookup"><span data-stu-id="430b0-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="430b0-182">Parametri</span><span class="sxs-lookup"><span data-stu-id="430b0-182">Parameters</span></span>
* <span data-ttu-id="430b0-183">ClientMode: "Active" forza la modalità di rilevamento visivo quando non può essere stabilita passivamente</span><span class="sxs-lookup"><span data-stu-id="430b0-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="430b0-184">Termica olografica</span><span class="sxs-lookup"><span data-stu-id="430b0-184">Holographic Thermal</span></span>

<span data-ttu-id="430b0-185">**/API/Holographic/Thermal/stage (GET)**</span><span class="sxs-lookup"><span data-stu-id="430b0-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="430b0-186">Ottenere la fase termica del dispositivo (0 normale, 1 caldo, 2 critico)</span><span class="sxs-lookup"><span data-stu-id="430b0-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="430b0-187">Controllo della simulazione della percezione</span><span class="sxs-lookup"><span data-stu-id="430b0-187">Perception Simulation Control</span></span>

<span data-ttu-id="430b0-188">**/API/Holographic/Simulation/Control/mode (GET)**</span><span class="sxs-lookup"><span data-stu-id="430b0-188">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="430b0-189">Ottenere la modalità di simulazione</span><span class="sxs-lookup"><span data-stu-id="430b0-189">Get the simulation mode</span></span>

<span data-ttu-id="430b0-190">**/API/Holographic/Simulation/Control/mode (POST)**</span><span class="sxs-lookup"><span data-stu-id="430b0-190">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="430b0-191">Impostare la modalità di simulazione</span><span class="sxs-lookup"><span data-stu-id="430b0-191">Set the simulation mode</span></span>

<span data-ttu-id="430b0-192">Parametri</span><span class="sxs-lookup"><span data-stu-id="430b0-192">Parameters</span></span>
* <span data-ttu-id="430b0-193">Mode: modalità simulazione: predefinita, simulazione, remota, Legacy</span><span class="sxs-lookup"><span data-stu-id="430b0-193">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="430b0-194">**/API/Holographic/Simulation/Control/Stream (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="430b0-194">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="430b0-195">Eliminare un flusso di controllo.</span><span class="sxs-lookup"><span data-stu-id="430b0-195">Delete a control stream.</span></span>

<span data-ttu-id="430b0-196">**/API/Holographic/Simulation/Control/Stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="430b0-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="430b0-197">Aprire una connessione Web socket per un flusso di controllo.</span><span class="sxs-lookup"><span data-stu-id="430b0-197">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="430b0-198">**/API/Holographic/Simulation/Control/Stream (POST)**</span><span class="sxs-lookup"><span data-stu-id="430b0-198">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="430b0-199">Creare un flusso di controllo (priorità obbligatoria) o pubblicare i dati in un flusso creato (streamId richiesto).</span><span class="sxs-lookup"><span data-stu-id="430b0-199">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="430b0-200">È previsto che i dati inviati siano di tipo ' Application/ottetto-Stream '.</span><span class="sxs-lookup"><span data-stu-id="430b0-200">Posted data is expected to be of type 'application/octet-stream'.</span></span>

<span data-ttu-id="430b0-201">**/API/Holographic/Simulation/Display/Stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="430b0-201">**/api/holographic/simulation/display/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="430b0-202">Richiedere un flusso video di simulazione contenente il contenuto di cui è stato eseguito il rendering nella visualizzazione del sistema in modalità "simulazione".</span><span class="sxs-lookup"><span data-stu-id="430b0-202">Request a simulation video stream containing the content rendered to the system display when in 'Simulation' mode.</span></span>  <span data-ttu-id="430b0-203">Inizialmente verrà inviata un'intestazione di descrittore di formato semplice, seguita da trame con codifica H. 264, ognuna preceduta da un'intestazione che indica l'indice degli occhi e le dimensioni della trama.</span><span class="sxs-lookup"><span data-stu-id="430b0-203">A simple format descriptor header will be sent initially, followed by H.264-encoded textures, each preceded by a header indicating the eye index and texture size.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="430b0-204">Riproduzione della simulazione di percezione</span><span class="sxs-lookup"><span data-stu-id="430b0-204">Perception Simulation Playback</span></span>

<span data-ttu-id="430b0-205">**/API/Holographic/Simulation/playback/file (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="430b0-205">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="430b0-206">Eliminare una registrazione.</span><span class="sxs-lookup"><span data-stu-id="430b0-206">Delete a recording.</span></span>

<span data-ttu-id="430b0-207">Parametri</span><span class="sxs-lookup"><span data-stu-id="430b0-207">Parameters</span></span>
* <span data-ttu-id="430b0-208">registrazione: nome della registrazione da eliminare.</span><span class="sxs-lookup"><span data-stu-id="430b0-208">recording : Name of recording to delete.</span></span>

<span data-ttu-id="430b0-209">**/API/Holographic/Simulation/playback/file (POST)**</span><span class="sxs-lookup"><span data-stu-id="430b0-209">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="430b0-210">Caricare una registrazione.</span><span class="sxs-lookup"><span data-stu-id="430b0-210">Upload a recording.</span></span>

<span data-ttu-id="430b0-211">**/API/Holographic/Simulation/playback/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="430b0-211">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="430b0-212">Ottenere tutte le registrazioni.</span><span class="sxs-lookup"><span data-stu-id="430b0-212">Get all recordings.</span></span>

<span data-ttu-id="430b0-213">**/API/Holographic/Simulation/playback/Session (GET)**</span><span class="sxs-lookup"><span data-stu-id="430b0-213">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="430b0-214">Ottenere lo stato di riproduzione corrente di una registrazione.</span><span class="sxs-lookup"><span data-stu-id="430b0-214">Get the current playback state of a recording.</span></span>

<span data-ttu-id="430b0-215">Parametri</span><span class="sxs-lookup"><span data-stu-id="430b0-215">Parameters</span></span>
* <span data-ttu-id="430b0-216">registrazione: nome della registrazione.</span><span class="sxs-lookup"><span data-stu-id="430b0-216">recording : Name of recording.</span></span>

<span data-ttu-id="430b0-217">**/API/Holographic/Simulation/playback/Session/file (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="430b0-217">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="430b0-218">Scaricare una registrazione.</span><span class="sxs-lookup"><span data-stu-id="430b0-218">Unload a recording.</span></span>

<span data-ttu-id="430b0-219">Parametri</span><span class="sxs-lookup"><span data-stu-id="430b0-219">Parameters</span></span>
* <span data-ttu-id="430b0-220">registrazione: nome della registrazione da scaricare.</span><span class="sxs-lookup"><span data-stu-id="430b0-220">recording : Name of recording to unload.</span></span>

<span data-ttu-id="430b0-221">**/API/Holographic/Simulation/playback/Session/file (POST)**</span><span class="sxs-lookup"><span data-stu-id="430b0-221">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="430b0-222">Caricare una registrazione.</span><span class="sxs-lookup"><span data-stu-id="430b0-222">Load a recording.</span></span>

<span data-ttu-id="430b0-223">Parametri</span><span class="sxs-lookup"><span data-stu-id="430b0-223">Parameters</span></span>
* <span data-ttu-id="430b0-224">registrazione: nome della registrazione da caricare.</span><span class="sxs-lookup"><span data-stu-id="430b0-224">recording : Name of recording to load.</span></span>

<span data-ttu-id="430b0-225">**/API/Holographic/Simulation/playback/Session/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="430b0-225">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="430b0-226">Ottenere tutte le registrazioni caricate.</span><span class="sxs-lookup"><span data-stu-id="430b0-226">Get all loaded recordings.</span></span>

<span data-ttu-id="430b0-227">**/API/Holographic/Simulation/playback/Session/pause (POST)**</span><span class="sxs-lookup"><span data-stu-id="430b0-227">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="430b0-228">Sospendere la registrazione.</span><span class="sxs-lookup"><span data-stu-id="430b0-228">Pause a recording.</span></span>

<span data-ttu-id="430b0-229">Parametri</span><span class="sxs-lookup"><span data-stu-id="430b0-229">Parameters</span></span>
* <span data-ttu-id="430b0-230">registrazione: nome della registrazione.</span><span class="sxs-lookup"><span data-stu-id="430b0-230">recording : Name of recording.</span></span>

<span data-ttu-id="430b0-231">**/API/Holographic/Simulation/playback/Session/Play (POST)**</span><span class="sxs-lookup"><span data-stu-id="430b0-231">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="430b0-232">Riprodurre una registrazione.</span><span class="sxs-lookup"><span data-stu-id="430b0-232">Play a recording.</span></span>

<span data-ttu-id="430b0-233">Parametri</span><span class="sxs-lookup"><span data-stu-id="430b0-233">Parameters</span></span>
* <span data-ttu-id="430b0-234">registrazione: nome della registrazione.</span><span class="sxs-lookup"><span data-stu-id="430b0-234">recording : Name of recording.</span></span>

<span data-ttu-id="430b0-235">**/API/Holographic/Simulation/playback/Session/Stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="430b0-235">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="430b0-236">Arrestare una registrazione.</span><span class="sxs-lookup"><span data-stu-id="430b0-236">Stop a recording.</span></span>

<span data-ttu-id="430b0-237">Parametri</span><span class="sxs-lookup"><span data-stu-id="430b0-237">Parameters</span></span>
* <span data-ttu-id="430b0-238">registrazione: nome della registrazione.</span><span class="sxs-lookup"><span data-stu-id="430b0-238">recording : Name of recording.</span></span>

<span data-ttu-id="430b0-239">**/API/Holographic/Simulation/playback/Session/types (GET)**</span><span class="sxs-lookup"><span data-stu-id="430b0-239">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="430b0-240">Ottenere i tipi di dati in una registrazione caricata.</span><span class="sxs-lookup"><span data-stu-id="430b0-240">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="430b0-241">Parametri</span><span class="sxs-lookup"><span data-stu-id="430b0-241">Parameters</span></span>
* <span data-ttu-id="430b0-242">registrazione: nome della registrazione.</span><span class="sxs-lookup"><span data-stu-id="430b0-242">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="430b0-243">Registrazione della simulazione della percezione</span><span class="sxs-lookup"><span data-stu-id="430b0-243">Perception Simulation Recording</span></span>

<span data-ttu-id="430b0-244">**/API/Holographic/Simulation/Recording/Start (POST)**</span><span class="sxs-lookup"><span data-stu-id="430b0-244">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="430b0-245">Avviare una registrazione.</span><span class="sxs-lookup"><span data-stu-id="430b0-245">Start a recording.</span></span> <span data-ttu-id="430b0-246">Solo una singola registrazione può essere attiva in una sola volta.</span><span class="sxs-lookup"><span data-stu-id="430b0-246">Only a single recording can be active at once.</span></span> <span data-ttu-id="430b0-247">È necessario impostare una delle intestazioni Head, Hands, spatialMapping o Environment.</span><span class="sxs-lookup"><span data-stu-id="430b0-247">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="430b0-248">Parametri</span><span class="sxs-lookup"><span data-stu-id="430b0-248">Parameters</span></span>
* <span data-ttu-id="430b0-249">Head: impostare su 1 per registrare i dati Head.</span><span class="sxs-lookup"><span data-stu-id="430b0-249">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="430b0-250">Hands: impostare su 1 per registrare i dati della mano.</span><span class="sxs-lookup"><span data-stu-id="430b0-250">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="430b0-251">spatialMapping: impostare su 1 per registrare il mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="430b0-251">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="430b0-252">ambiente: impostare su 1 per registrare i dati dell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="430b0-252">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="430b0-253">Nome: nome della registrazione.</span><span class="sxs-lookup"><span data-stu-id="430b0-253">name : Name of the recording.</span></span>
* <span data-ttu-id="430b0-254">singleSpatialMappingFrame: impostare su 1 per registrare un singolo frame di mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="430b0-254">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="430b0-255">**/API/Holographic/Simulation/Recording/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="430b0-255">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="430b0-256">Ottenere lo stato di registrazione.</span><span class="sxs-lookup"><span data-stu-id="430b0-256">Get recording state.</span></span>

<span data-ttu-id="430b0-257">**/API/Holographic/Simulation/Recording/Stop (GET)**</span><span class="sxs-lookup"><span data-stu-id="430b0-257">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="430b0-258">Arrestare la registrazione corrente.</span><span class="sxs-lookup"><span data-stu-id="430b0-258">Stop the current recording.</span></span> <span data-ttu-id="430b0-259">La registrazione verrà restituita come file.</span><span class="sxs-lookup"><span data-stu-id="430b0-259">Recording will be returned as a file.</span></span>

## <a name="mixed-reality-capture"></a><span data-ttu-id="430b0-260">Mixed Reality Capture</span><span class="sxs-lookup"><span data-stu-id="430b0-260">Mixed Reality Capture</span></span>

<span data-ttu-id="430b0-261">**/API/Holographic/MRC/file (GET)**</span><span class="sxs-lookup"><span data-stu-id="430b0-261">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="430b0-262">Scarica un file di realtà mista dal dispositivo.</span><span class="sxs-lookup"><span data-stu-id="430b0-262">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="430b0-263">Usare il parametro di query op = Stream per il flusso.</span><span class="sxs-lookup"><span data-stu-id="430b0-263">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="430b0-264">Parametri</span><span class="sxs-lookup"><span data-stu-id="430b0-264">Parameters</span></span>
* <span data-ttu-id="430b0-265">filename: Name, hex64 codificato del file video da ottenere</span><span class="sxs-lookup"><span data-stu-id="430b0-265">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="430b0-266">op: Stream</span><span class="sxs-lookup"><span data-stu-id="430b0-266">op : stream</span></span>

<span data-ttu-id="430b0-267">**/API/Holographic/MRC/file (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="430b0-267">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="430b0-268">Elimina una registrazione di realtà mista dal dispositivo.</span><span class="sxs-lookup"><span data-stu-id="430b0-268">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="430b0-269">Parametri</span><span class="sxs-lookup"><span data-stu-id="430b0-269">Parameters</span></span>
* <span data-ttu-id="430b0-270">filename: Name, hex64 codificato del file da eliminare</span><span class="sxs-lookup"><span data-stu-id="430b0-270">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="430b0-271">**/API/Holographic/MRC/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="430b0-271">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="430b0-272">Restituisce l'elenco dei file di realtà mista archiviati nel dispositivo</span><span class="sxs-lookup"><span data-stu-id="430b0-272">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="430b0-273">**/API/Holographic/MRC/Photo (POST)**</span><span class="sxs-lookup"><span data-stu-id="430b0-273">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="430b0-274">Accetta una foto della realtà mista e crea un file nel dispositivo</span><span class="sxs-lookup"><span data-stu-id="430b0-274">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="430b0-275">Parametri</span><span class="sxs-lookup"><span data-stu-id="430b0-275">Parameters</span></span>
* <span data-ttu-id="430b0-276">Holo: Acquisisci ologrammi: true o false (il valore predefinito è false)</span><span class="sxs-lookup"><span data-stu-id="430b0-276">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="430b0-277">PV: Capture PV fotocamera: true o false (il valore predefinito è false)</span><span class="sxs-lookup"><span data-stu-id="430b0-277">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="430b0-278">RenderFromCamera: (solo HoloLens 2) Render dal punto di vista della fotocamera Photo/video: true o false (il valore predefinito è true)</span><span class="sxs-lookup"><span data-stu-id="430b0-278">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="430b0-279">**/API/Holographic/MRC/Settings (GET)**</span><span class="sxs-lookup"><span data-stu-id="430b0-279">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="430b0-280">Ottiene le impostazioni predefinite di acquisizione della realtà mista</span><span class="sxs-lookup"><span data-stu-id="430b0-280">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="430b0-281">**/API/Holographic/MRC/Settings (POST)**</span><span class="sxs-lookup"><span data-stu-id="430b0-281">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="430b0-282">Imposta le impostazioni predefinite di acquisizione della realtà mista.</span><span class="sxs-lookup"><span data-stu-id="430b0-282">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="430b0-283">Alcune di queste impostazioni vengono applicate all'acquisizione di foto e video di MRC del sistema.</span><span class="sxs-lookup"><span data-stu-id="430b0-283">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="430b0-284">**/API/Holographic/MRC/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="430b0-284">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="430b0-285">Ottiene lo stato della realtà mista registrata (in esecuzione, arrestata)</span><span class="sxs-lookup"><span data-stu-id="430b0-285">Gets the status of the mixed reality recorded (running, stopped)</span></span>

<span data-ttu-id="430b0-286">**/API/Holographic/MRC/Thumbnail (GET)**</span><span class="sxs-lookup"><span data-stu-id="430b0-286">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="430b0-287">Ottiene l'immagine di anteprima per il file specificato.</span><span class="sxs-lookup"><span data-stu-id="430b0-287">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="430b0-288">Parametri</span><span class="sxs-lookup"><span data-stu-id="430b0-288">Parameters</span></span>
* <span data-ttu-id="430b0-289">filename: Name, hex64 codificato, del file per il quale viene richiesta l'anteprima</span><span class="sxs-lookup"><span data-stu-id="430b0-289">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="430b0-290">**/API/Holographic/MRC/video/Control/Start (POST)**</span><span class="sxs-lookup"><span data-stu-id="430b0-290">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="430b0-291">Avvia una registrazione di realtà mista</span><span class="sxs-lookup"><span data-stu-id="430b0-291">Starts a mixed reality recording</span></span>

<span data-ttu-id="430b0-292">Parametri</span><span class="sxs-lookup"><span data-stu-id="430b0-292">Parameters</span></span>
* <span data-ttu-id="430b0-293">Holo: Acquisisci ologrammi: true o false (il valore predefinito è false)</span><span class="sxs-lookup"><span data-stu-id="430b0-293">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="430b0-294">PV: Capture PV fotocamera: true o false (il valore predefinito è false)</span><span class="sxs-lookup"><span data-stu-id="430b0-294">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="430b0-295">MIC: Acquisisci microfono: true o false (il valore predefinito è false)</span><span class="sxs-lookup"><span data-stu-id="430b0-295">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="430b0-296">loopback: Acquisisci audio dell'app: true o false (il valore predefinito è false)</span><span class="sxs-lookup"><span data-stu-id="430b0-296">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="430b0-297">RenderFromCamera: (solo HoloLens 2) Render dal punto di vista della fotocamera Photo/video: true o false (il valore predefinito è true)</span><span class="sxs-lookup"><span data-stu-id="430b0-297">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="430b0-298">Vstab: (solo HoloLens 2) Abilita stabilizzazione video: true o false (il valore predefinito è true)</span><span class="sxs-lookup"><span data-stu-id="430b0-298">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="430b0-299">vstabbuffer: (solo HoloLens 2) latenza buffer di stabilizzazione video: da 0 a 30 fotogrammi (il valore predefinito è 15 fotogrammi)</span><span class="sxs-lookup"><span data-stu-id="430b0-299">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="430b0-300">**/API/Holographic/MRC/video/Control/Stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="430b0-300">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="430b0-301">Arresta la registrazione della realtà mista corrente</span><span class="sxs-lookup"><span data-stu-id="430b0-301">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="430b0-302">Flusso di realtà mista</span><span class="sxs-lookup"><span data-stu-id="430b0-302">Mixed Reality Streaming</span></span>

<span data-ttu-id="430b0-303">HoloLens supporta l'anteprima in tempo reale della realtà mista tramite il download in blocchi di un MP4 frammentato.</span><span class="sxs-lookup"><span data-stu-id="430b0-303">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="430b0-304">I flussi di realtà mista condividono lo stesso set di parametri per controllare gli elementi acquisiti:</span><span class="sxs-lookup"><span data-stu-id="430b0-304">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="430b0-305">Holo: acquisire gli ologrammi: true o false</span><span class="sxs-lookup"><span data-stu-id="430b0-305">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="430b0-306">PV: acquisire la fotocamera PV: true o false</span><span class="sxs-lookup"><span data-stu-id="430b0-306">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="430b0-307">MIC: Acquisisci microfono: true o false</span><span class="sxs-lookup"><span data-stu-id="430b0-307">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="430b0-308">loopback: Acquisisci audio dell'app: true o false</span><span class="sxs-lookup"><span data-stu-id="430b0-308">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="430b0-309">Se non viene specificato alcun valore, verranno acquisiti gli ologrammi, la fotocamera foto/video e l'audio dell'app.</span><span class="sxs-lookup"><span data-stu-id="430b0-309">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="430b0-310">Se viene specificato any: i parametri non specificati verranno impostati su false.</span><span class="sxs-lookup"><span data-stu-id="430b0-310">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="430b0-311">Parametri facoltativi (solo HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="430b0-311">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="430b0-312">RenderFromCamera: rendering dal punto di vista della fotocamera Photo/video: true o false (il valore predefinito è true)</span><span class="sxs-lookup"><span data-stu-id="430b0-312">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="430b0-313">Vstab: Abilita stabilizzazione video: true o false (il valore predefinito è false)</span><span class="sxs-lookup"><span data-stu-id="430b0-313">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="430b0-314">vstabbuffer: latenza buffer di stabilizzazione video: da 0 a 30 fotogrammi (il valore predefinito è 15 fotogrammi)</span><span class="sxs-lookup"><span data-stu-id="430b0-314">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="430b0-315">**/API/Holographic/Stream/Live.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="430b0-315">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="430b0-316">Flusso di 5Mbit 1280x720p 30 fps.</span><span class="sxs-lookup"><span data-stu-id="430b0-316">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="430b0-317">**/API/Holographic/Stream/live_high. mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="430b0-317">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="430b0-318">Flusso di 5Mbit 1280x720p 30 fps.</span><span class="sxs-lookup"><span data-stu-id="430b0-318">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="430b0-319">**/API/Holographic/Stream/live_med. mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="430b0-319">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="430b0-320">Un flusso 854x480p 30 fps da 2 MB.</span><span class="sxs-lookup"><span data-stu-id="430b0-320">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="430b0-321">**/API/Holographic/Stream/live_low. mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="430b0-321">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="430b0-322">Flusso 428x240p 15fps 0.6 Mbit.</span><span class="sxs-lookup"><span data-stu-id="430b0-322">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="430b0-323">Rete</span><span class="sxs-lookup"><span data-stu-id="430b0-323">Networking</span></span>

<span data-ttu-id="430b0-324">**/API/networking/ipconfig (GET)**</span><span class="sxs-lookup"><span data-stu-id="430b0-324">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="430b0-325">Ottiene la configurazione IP corrente</span><span class="sxs-lookup"><span data-stu-id="430b0-325">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="430b0-326">Informazioni sul sistema operativo</span><span class="sxs-lookup"><span data-stu-id="430b0-326">OS Information</span></span>

<span data-ttu-id="430b0-327">**/API/OS/info (GET)**</span><span class="sxs-lookup"><span data-stu-id="430b0-327">**/api/os/info (GET)**</span></span>

<span data-ttu-id="430b0-328">Ottiene le informazioni sul sistema operativo</span><span class="sxs-lookup"><span data-stu-id="430b0-328">Gets operating system information</span></span>

<span data-ttu-id="430b0-329">**/API/OS/MachineName (GET)**</span><span class="sxs-lookup"><span data-stu-id="430b0-329">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="430b0-330">Ottiene il nome del computer</span><span class="sxs-lookup"><span data-stu-id="430b0-330">Gets the machine name</span></span>

<span data-ttu-id="430b0-331">**/API/OS/MachineName (POST)**</span><span class="sxs-lookup"><span data-stu-id="430b0-331">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="430b0-332">Imposta il nome del computer</span><span class="sxs-lookup"><span data-stu-id="430b0-332">Sets the machine name</span></span>

<span data-ttu-id="430b0-333">Parametri</span><span class="sxs-lookup"><span data-stu-id="430b0-333">Parameters</span></span>
* <span data-ttu-id="430b0-334">Nome: nome del nuovo computer, hex64 codificato, per impostare su</span><span class="sxs-lookup"><span data-stu-id="430b0-334">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="performance-data"></a><span data-ttu-id="430b0-335">Dati sulle prestazioni</span><span class="sxs-lookup"><span data-stu-id="430b0-335">Performance data</span></span>

<span data-ttu-id="430b0-336">**/API/ResourceManager/processes (GET)**</span><span class="sxs-lookup"><span data-stu-id="430b0-336">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="430b0-337">Restituisce l'elenco dei processi in esecuzione con i dettagli</span><span class="sxs-lookup"><span data-stu-id="430b0-337">Returns the list of running processes with details</span></span>

<span data-ttu-id="430b0-338">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="430b0-338">Return data</span></span>
* <span data-ttu-id="430b0-339">JSON con elenco di processi e dettagli per ogni processo</span><span class="sxs-lookup"><span data-stu-id="430b0-339">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="430b0-340">**/API/ResourceManager/systemperf (GET)**</span><span class="sxs-lookup"><span data-stu-id="430b0-340">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="430b0-341">Restituisce le statistiche sulle prestazioni di sistema (lettura/scrittura di I/O, statistiche sulla memoria e così via.</span><span class="sxs-lookup"><span data-stu-id="430b0-341">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="430b0-342">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="430b0-342">Return data</span></span>
* <span data-ttu-id="430b0-343">JSON con informazioni di sistema: CPU, GPU, memoria, rete, IO</span><span class="sxs-lookup"><span data-stu-id="430b0-343">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="430b0-344">Power</span><span class="sxs-lookup"><span data-stu-id="430b0-344">Power</span></span>

<span data-ttu-id="430b0-345">**/API/Power/Battery (GET)**</span><span class="sxs-lookup"><span data-stu-id="430b0-345">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="430b0-346">Ottiene lo stato corrente della batteria</span><span class="sxs-lookup"><span data-stu-id="430b0-346">Gets the current battery state</span></span>

<span data-ttu-id="430b0-347">**/API/Power/State (GET)**</span><span class="sxs-lookup"><span data-stu-id="430b0-347">**/api/power/state (GET)**</span></span>

<span data-ttu-id="430b0-348">Controlla se il sistema è in uno stato di alimentazione basso</span><span class="sxs-lookup"><span data-stu-id="430b0-348">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="430b0-349">Controllo remoto</span><span class="sxs-lookup"><span data-stu-id="430b0-349">Remote Control</span></span>

<span data-ttu-id="430b0-350">**/API/Control/Restart (POST)**</span><span class="sxs-lookup"><span data-stu-id="430b0-350">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="430b0-351">Riavvia il dispositivo di destinazione</span><span class="sxs-lookup"><span data-stu-id="430b0-351">Restarts the target device</span></span>

<span data-ttu-id="430b0-352">**/API/Control/Shutdown (POST)**</span><span class="sxs-lookup"><span data-stu-id="430b0-352">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="430b0-353">Arresta il dispositivo di destinazione</span><span class="sxs-lookup"><span data-stu-id="430b0-353">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="430b0-354">Gestione attività</span><span class="sxs-lookup"><span data-stu-id="430b0-354">Task Manager</span></span>

<span data-ttu-id="430b0-355">**/API/taskmanager/app (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="430b0-355">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="430b0-356">Arresta un'app moderna</span><span class="sxs-lookup"><span data-stu-id="430b0-356">Stops a modern app</span></span>

<span data-ttu-id="430b0-357">Parametri</span><span class="sxs-lookup"><span data-stu-id="430b0-357">Parameters</span></span>
* <span data-ttu-id="430b0-358">pacchetto: nome completo del pacchetto dell'app, codificato in hex64</span><span class="sxs-lookup"><span data-stu-id="430b0-358">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="430b0-359">forcestop: forza l'arresto di tutti i processi (= Yes)</span><span class="sxs-lookup"><span data-stu-id="430b0-359">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="430b0-360">**/API/taskmanager/app (POST)**</span><span class="sxs-lookup"><span data-stu-id="430b0-360">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="430b0-361">Avvia un'app moderna</span><span class="sxs-lookup"><span data-stu-id="430b0-361">Starts a modern app</span></span>

<span data-ttu-id="430b0-362">Parametri</span><span class="sxs-lookup"><span data-stu-id="430b0-362">Parameters</span></span>
* <span data-ttu-id="430b0-363">AppID: PRAID dell'app da avviare, hex64 codificato</span><span class="sxs-lookup"><span data-stu-id="430b0-363">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="430b0-364">pacchetto: nome completo del pacchetto dell'app, codificato in hex64</span><span class="sxs-lookup"><span data-stu-id="430b0-364">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="430b0-365">Gestione Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="430b0-365">WiFi Management</span></span>

<span data-ttu-id="430b0-366">**/API/WiFi/Interfaces (GET)**</span><span class="sxs-lookup"><span data-stu-id="430b0-366">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="430b0-367">Enumera le interfacce di rete wireless</span><span class="sxs-lookup"><span data-stu-id="430b0-367">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="430b0-368">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="430b0-368">Return data</span></span>
* <span data-ttu-id="430b0-369">Elenco di interfacce wireless con dettagli (GUID, descrizione e così via)</span><span class="sxs-lookup"><span data-stu-id="430b0-369">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="430b0-370">**/API/WiFi/Network (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="430b0-370">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="430b0-371">Elimina un profilo associato a una rete in un'interfaccia specificata</span><span class="sxs-lookup"><span data-stu-id="430b0-371">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="430b0-372">Parametri</span><span class="sxs-lookup"><span data-stu-id="430b0-372">Parameters</span></span>
* <span data-ttu-id="430b0-373">interfaccia: GUID dell'interfaccia di rete</span><span class="sxs-lookup"><span data-stu-id="430b0-373">interface : network interface guid</span></span>
* <span data-ttu-id="430b0-374">profilo: nome profilo</span><span class="sxs-lookup"><span data-stu-id="430b0-374">profile : profile name</span></span>

<span data-ttu-id="430b0-375">**/API/WiFi/Networks (GET)**</span><span class="sxs-lookup"><span data-stu-id="430b0-375">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="430b0-376">Enumera le reti wireless sull'interfaccia di rete specificata</span><span class="sxs-lookup"><span data-stu-id="430b0-376">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="430b0-377">Parametri</span><span class="sxs-lookup"><span data-stu-id="430b0-377">Parameters</span></span>
* <span data-ttu-id="430b0-378">interfaccia: GUID dell'interfaccia di rete</span><span class="sxs-lookup"><span data-stu-id="430b0-378">interface : network interface guid</span></span>

<span data-ttu-id="430b0-379">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="430b0-379">Return data</span></span>
* <span data-ttu-id="430b0-380">Elenco di reti wireless disponibili nell'interfaccia di rete con i dettagli</span><span class="sxs-lookup"><span data-stu-id="430b0-380">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="430b0-381">**/API/WiFi/Network (POST)**</span><span class="sxs-lookup"><span data-stu-id="430b0-381">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="430b0-382">Si connette o si disconnette a una rete sull'interfaccia specificata</span><span class="sxs-lookup"><span data-stu-id="430b0-382">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="430b0-383">Parametri</span><span class="sxs-lookup"><span data-stu-id="430b0-383">Parameters</span></span>
* <span data-ttu-id="430b0-384">interfaccia: GUID dell'interfaccia di rete</span><span class="sxs-lookup"><span data-stu-id="430b0-384">interface : network interface guid</span></span>
* <span data-ttu-id="430b0-385">SSID: SSID, hex64 codificato, per la connessione a</span><span class="sxs-lookup"><span data-stu-id="430b0-385">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="430b0-386">op: connessione o disconnessione</span><span class="sxs-lookup"><span data-stu-id="430b0-386">op : connect or disconnect</span></span>
* <span data-ttu-id="430b0-387">CreateProfile: Sì o no</span><span class="sxs-lookup"><span data-stu-id="430b0-387">createprofile : yes or no</span></span>
* <span data-ttu-id="430b0-388">chiave: chiave condivisa, codificato in hex64</span><span class="sxs-lookup"><span data-stu-id="430b0-388">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="430b0-389">Registratore prestazioni Windows</span><span class="sxs-lookup"><span data-stu-id="430b0-389">Windows Performance Recorder</span></span>

<span data-ttu-id="430b0-390">**/API/WPR/customtrace (POST)**</span><span class="sxs-lookup"><span data-stu-id="430b0-390">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="430b0-391">Carica un profilo WPR e avvia la traccia usando il profilo caricato.</span><span class="sxs-lookup"><span data-stu-id="430b0-391">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="430b0-392">Payload</span><span class="sxs-lookup"><span data-stu-id="430b0-392">Payload</span></span>
* <span data-ttu-id="430b0-393">corpo HTTP conforme a più parti</span><span class="sxs-lookup"><span data-stu-id="430b0-393">multi-part conforming http body</span></span>

<span data-ttu-id="430b0-394">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="430b0-394">Return data</span></span>
* <span data-ttu-id="430b0-395">Restituisce lo stato della sessione WPR.</span><span class="sxs-lookup"><span data-stu-id="430b0-395">Returns the WPR session status.</span></span>

<span data-ttu-id="430b0-396">**/API/WPR/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="430b0-396">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="430b0-397">Recupera lo stato della sessione WPR</span><span class="sxs-lookup"><span data-stu-id="430b0-397">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="430b0-398">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="430b0-398">Return data</span></span>
* <span data-ttu-id="430b0-399">Stato della sessione WPR.</span><span class="sxs-lookup"><span data-stu-id="430b0-399">WPR session status.</span></span>

<span data-ttu-id="430b0-400">**/API/WPR/Trace (GET)**</span><span class="sxs-lookup"><span data-stu-id="430b0-400">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="430b0-401">Arresta una sessione di traccia WPR (performance)</span><span class="sxs-lookup"><span data-stu-id="430b0-401">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="430b0-402">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="430b0-402">Return data</span></span>
* <span data-ttu-id="430b0-403">Restituisce il file ETL di traccia</span><span class="sxs-lookup"><span data-stu-id="430b0-403">Returns the trace ETL file</span></span>

<span data-ttu-id="430b0-404">**/API/WPR/Trace (POST)**</span><span class="sxs-lookup"><span data-stu-id="430b0-404">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="430b0-405">Avvia una sessione di traccia WPR (performance)</span><span class="sxs-lookup"><span data-stu-id="430b0-405">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="430b0-406">Parametri</span><span class="sxs-lookup"><span data-stu-id="430b0-406">Parameters</span></span>
* <span data-ttu-id="430b0-407">profilo: nome profilo.</span><span class="sxs-lookup"><span data-stu-id="430b0-407">profile : Profile name.</span></span> <span data-ttu-id="430b0-408">I profili disponibili sono archiviati in perfprofiles/Profiles. JSON</span><span class="sxs-lookup"><span data-stu-id="430b0-408">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="430b0-409">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="430b0-409">Return data</span></span>
* <span data-ttu-id="430b0-410">All'avvio, restituisce lo stato della sessione WPR.</span><span class="sxs-lookup"><span data-stu-id="430b0-410">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="430b0-411">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="430b0-411">See also</span></span>
* [<span data-ttu-id="430b0-412">Avviare il Portale di dispositivi di Windows</span><span class="sxs-lookup"><span data-stu-id="430b0-412">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="430b0-413">Informazioni di riferimento sulle API del portale per dispositivi (UWP)</span><span class="sxs-lookup"><span data-stu-id="430b0-413">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)

---
title: Informazioni di riferimento sull'API del portale del dispositivo
description: Informazioni di riferimento sulle API per il portale per dispositivi Windows in HoloLens
author: jonmlyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, portale per dispositivi Windows, API
ms.openlocfilehash: 236de35c2c736fc5a0289b7be1f1548f0a08fa26
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278239"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="16f65-104">Informazioni di riferimento sull'API del portale del dispositivo</span><span class="sxs-lookup"><span data-stu-id="16f65-104">Device portal API reference</span></span>

<span data-ttu-id="16f65-105">Tutti gli elementi del [portale per dispositivi Windows](using-the-windows-device-portal.md) sono basati sulle API REST che è possibile usare per accedere ai dati e controllare il dispositivo a livello di codice.</span><span class="sxs-lookup"><span data-stu-id="16f65-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="16f65-106">Deloyment app</span><span class="sxs-lookup"><span data-stu-id="16f65-106">App deloyment</span></span>

<span data-ttu-id="16f65-107">**/API/app/PackageManager/Package (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="16f65-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="16f65-108">Disinstalla un'app</span><span class="sxs-lookup"><span data-stu-id="16f65-108">Uninstalls an app</span></span>

<span data-ttu-id="16f65-109">Parametri</span><span class="sxs-lookup"><span data-stu-id="16f65-109">Parameters</span></span>
* <span data-ttu-id="16f65-110">Package: nome file del pacchetto da disinstallare.</span><span class="sxs-lookup"><span data-stu-id="16f65-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="16f65-111">**/API/app/PackageManager/Package (POST)**</span><span class="sxs-lookup"><span data-stu-id="16f65-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="16f65-112">Installa un'app</span><span class="sxs-lookup"><span data-stu-id="16f65-112">Installs an App</span></span>

<span data-ttu-id="16f65-113">Parametri</span><span class="sxs-lookup"><span data-stu-id="16f65-113">Parameters</span></span>
* <span data-ttu-id="16f65-114">Package: nome file del pacchetto da installare.</span><span class="sxs-lookup"><span data-stu-id="16f65-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="16f65-115">Payload</span><span class="sxs-lookup"><span data-stu-id="16f65-115">Payload</span></span>
* <span data-ttu-id="16f65-116">corpo HTTP conforme a più parti</span><span class="sxs-lookup"><span data-stu-id="16f65-116">multi-part conforming http body</span></span>

<span data-ttu-id="16f65-117">**/API/app/packagemanager/packages (GET)**</span><span class="sxs-lookup"><span data-stu-id="16f65-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="16f65-118">Recupera l'elenco delle app installate nel sistema con i dettagli</span><span class="sxs-lookup"><span data-stu-id="16f65-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="16f65-119">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="16f65-119">Return data</span></span>
* <span data-ttu-id="16f65-120">Elenco dei pacchetti installati con i dettagli</span><span class="sxs-lookup"><span data-stu-id="16f65-120">List of installed packages with details</span></span>

<span data-ttu-id="16f65-121">**/API/app/PackageManager/state (GET)**</span><span class="sxs-lookup"><span data-stu-id="16f65-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="16f65-122">Ottiene lo stato dell'installazione dell'app in corso</span><span class="sxs-lookup"><span data-stu-id="16f65-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="16f65-123">Raccolta dei dump</span><span class="sxs-lookup"><span data-stu-id="16f65-123">Dump collection</span></span>

<span data-ttu-id="16f65-124">**/API/debug/dump/usermode/CrashControl (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="16f65-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="16f65-125">Disabilita la raccolta dei dump di arresto anomalo del sistema per un'app sideload</span><span class="sxs-lookup"><span data-stu-id="16f65-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="16f65-126">Parametri</span><span class="sxs-lookup"><span data-stu-id="16f65-126">Parameters</span></span>
* <span data-ttu-id="16f65-127">packageFullname: nome pacchetto</span><span class="sxs-lookup"><span data-stu-id="16f65-127">packageFullname : package name</span></span>

<span data-ttu-id="16f65-128">**/API/debug/dump/usermode/CrashControl (GET)**</span><span class="sxs-lookup"><span data-stu-id="16f65-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="16f65-129">Ottiene le impostazioni per la raccolta di dump di arresto anomalo di sideload</span><span class="sxs-lookup"><span data-stu-id="16f65-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="16f65-130">Parametri</span><span class="sxs-lookup"><span data-stu-id="16f65-130">Parameters</span></span>
* <span data-ttu-id="16f65-131">packageFullname: nome pacchetto</span><span class="sxs-lookup"><span data-stu-id="16f65-131">packageFullname : package name</span></span>

<span data-ttu-id="16f65-132">**/API/debug/dump/usermode/CrashControl (POST)**</span><span class="sxs-lookup"><span data-stu-id="16f65-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="16f65-133">Abilita e imposta le impostazioni di controllo dump per un'app sideload</span><span class="sxs-lookup"><span data-stu-id="16f65-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="16f65-134">Parametri</span><span class="sxs-lookup"><span data-stu-id="16f65-134">Parameters</span></span>
* <span data-ttu-id="16f65-135">packageFullname: nome pacchetto</span><span class="sxs-lookup"><span data-stu-id="16f65-135">packageFullname : package name</span></span>

<span data-ttu-id="16f65-136">**/API/debug/dump/usermode/crashdump (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="16f65-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="16f65-137">Elimina un dump di arresto anomalo del sistema per un'app sideload</span><span class="sxs-lookup"><span data-stu-id="16f65-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="16f65-138">Parametri</span><span class="sxs-lookup"><span data-stu-id="16f65-138">Parameters</span></span>
* <span data-ttu-id="16f65-139">packageFullname: nome pacchetto</span><span class="sxs-lookup"><span data-stu-id="16f65-139">packageFullname : package name</span></span>
* <span data-ttu-id="16f65-140">fileName: dump nome file</span><span class="sxs-lookup"><span data-stu-id="16f65-140">fileName : dump file name</span></span>

<span data-ttu-id="16f65-141">**/API/debug/dump/usermode/crashdump (GET)**</span><span class="sxs-lookup"><span data-stu-id="16f65-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="16f65-142">Recupera un dump di arresto anomalo del sistema per un'app sideload</span><span class="sxs-lookup"><span data-stu-id="16f65-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="16f65-143">Parametri</span><span class="sxs-lookup"><span data-stu-id="16f65-143">Parameters</span></span>
* <span data-ttu-id="16f65-144">packageFullname: nome pacchetto</span><span class="sxs-lookup"><span data-stu-id="16f65-144">packageFullname : package name</span></span>
* <span data-ttu-id="16f65-145">fileName: dump nome file</span><span class="sxs-lookup"><span data-stu-id="16f65-145">fileName : dump file name</span></span>

<span data-ttu-id="16f65-146">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="16f65-146">Return data</span></span>
* <span data-ttu-id="16f65-147">File dump.</span><span class="sxs-lookup"><span data-stu-id="16f65-147">Dump file.</span></span> <span data-ttu-id="16f65-148">Esaminare con WinDbg o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="16f65-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="16f65-149">**/API/debug/dump/usermode/Dumps (GET)**</span><span class="sxs-lookup"><span data-stu-id="16f65-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="16f65-150">Restituisce l'elenco di tutti i dump di arresto anomalo del sistema per le app sideload</span><span class="sxs-lookup"><span data-stu-id="16f65-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="16f65-151">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="16f65-151">Return data</span></span>
* <span data-ttu-id="16f65-152">Elenco dei dump di arresto anomalo del sistema per app caricata sul lato</span><span class="sxs-lookup"><span data-stu-id="16f65-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="16f65-153">ETW</span><span class="sxs-lookup"><span data-stu-id="16f65-153">ETW</span></span>

<span data-ttu-id="16f65-154">**/API/ETW/Providers (GET)**</span><span class="sxs-lookup"><span data-stu-id="16f65-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="16f65-155">Enumera i provider registrati</span><span class="sxs-lookup"><span data-stu-id="16f65-155">Enumerates registered providers</span></span>

<span data-ttu-id="16f65-156">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="16f65-156">Return data</span></span>
* <span data-ttu-id="16f65-157">Elenco di provider, nome descrittivo e GUID</span><span class="sxs-lookup"><span data-stu-id="16f65-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="16f65-158">**/API/ETW/Session/realtime (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="16f65-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="16f65-159">Crea una sessione ETW in tempo reale. gestito tramite WebSocket.</span><span class="sxs-lookup"><span data-stu-id="16f65-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="16f65-160">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="16f65-160">Return data</span></span>
* <span data-ttu-id="16f65-161">Eventi ETW dai provider abilitati</span><span class="sxs-lookup"><span data-stu-id="16f65-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="16f65-162">Sistema operativo olografico</span><span class="sxs-lookup"><span data-stu-id="16f65-162">Holographic OS</span></span>

<span data-ttu-id="16f65-163">**/API/Holographic/OS/ETW/customproviders (GET)**</span><span class="sxs-lookup"><span data-stu-id="16f65-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="16f65-164">Restituisce un elenco di provider ETW specifici di HoloLens non registrati con il sistema</span><span class="sxs-lookup"><span data-stu-id="16f65-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="16f65-165">**/API/Holographic/OS/Services (GET)**</span><span class="sxs-lookup"><span data-stu-id="16f65-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="16f65-166">Restituisce gli Stati di tutti i servizi in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="16f65-166">Returns the states of all services running.</span></span>

<span data-ttu-id="16f65-167">**/API/Holographic/OS/Settings/IPD (GET)**</span><span class="sxs-lookup"><span data-stu-id="16f65-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="16f65-168">Ottiene il dip archiviato (distanza interpupillare) in millimetri</span><span class="sxs-lookup"><span data-stu-id="16f65-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="16f65-169">**/API/Holographic/OS/Settings/IPD (POST)**</span><span class="sxs-lookup"><span data-stu-id="16f65-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="16f65-170">Imposta il dpi</span><span class="sxs-lookup"><span data-stu-id="16f65-170">Sets the IPD</span></span>

<span data-ttu-id="16f65-171">Parametri</span><span class="sxs-lookup"><span data-stu-id="16f65-171">Parameters</span></span>
* <span data-ttu-id="16f65-172">dpi: nuovo valore di DPI da impostare in millimetri</span><span class="sxs-lookup"><span data-stu-id="16f65-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="16f65-173">**/API/Holographic/OS/webmanagement/Settings/HTTPS (GET)**</span><span class="sxs-lookup"><span data-stu-id="16f65-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="16f65-174">Ottenere richieste HTTPS per Device Portal</span><span class="sxs-lookup"><span data-stu-id="16f65-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="16f65-175">**/API/Holographic/OS/webmanagement/Settings/HTTPS (POST)**</span><span class="sxs-lookup"><span data-stu-id="16f65-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="16f65-176">Imposta i requisiti HTTPS per il portale del dispositivo</span><span class="sxs-lookup"><span data-stu-id="16f65-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="16f65-177">Parametri</span><span class="sxs-lookup"><span data-stu-id="16f65-177">Parameters</span></span>
* <span data-ttu-id="16f65-178">obbligatorio: Sì, no o default</span><span class="sxs-lookup"><span data-stu-id="16f65-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="16f65-179">Percezione olografica</span><span class="sxs-lookup"><span data-stu-id="16f65-179">Holographic Perception</span></span>

<span data-ttu-id="16f65-180">**/API/Holographic/Perception/client (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="16f65-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="16f65-181">Accetta gli aggiornamenti WebSocket ed esegue un client di percezione che invia gli aggiornamenti a 30 fps.</span><span class="sxs-lookup"><span data-stu-id="16f65-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="16f65-182">Parametri</span><span class="sxs-lookup"><span data-stu-id="16f65-182">Parameters</span></span>
* <span data-ttu-id="16f65-183">ClientMode: "Active" forza la modalità di rilevamento visivo quando non può essere stabilita passivamente</span><span class="sxs-lookup"><span data-stu-id="16f65-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="16f65-184">Termica olografica</span><span class="sxs-lookup"><span data-stu-id="16f65-184">Holographic Thermal</span></span>

<span data-ttu-id="16f65-185">**/API/Holographic/Thermal/stage (GET)**</span><span class="sxs-lookup"><span data-stu-id="16f65-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="16f65-186">Ottenere la fase termica del dispositivo (0 normale, 1 caldo, 2 critico)</span><span class="sxs-lookup"><span data-stu-id="16f65-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="16f65-187">Controllo della simulazione della percezione</span><span class="sxs-lookup"><span data-stu-id="16f65-187">Perception Simulation Control</span></span>

<span data-ttu-id="16f65-188">**/API/Holographic/Simulation/Control/mode (GET)**</span><span class="sxs-lookup"><span data-stu-id="16f65-188">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="16f65-189">Ottenere la modalità di simulazione</span><span class="sxs-lookup"><span data-stu-id="16f65-189">Get the simulation mode</span></span>

<span data-ttu-id="16f65-190">**/API/Holographic/Simulation/Control/mode (POST)**</span><span class="sxs-lookup"><span data-stu-id="16f65-190">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="16f65-191">Impostare la modalità di simulazione</span><span class="sxs-lookup"><span data-stu-id="16f65-191">Set the simulation mode</span></span>

<span data-ttu-id="16f65-192">Parametri</span><span class="sxs-lookup"><span data-stu-id="16f65-192">Parameters</span></span>
* <span data-ttu-id="16f65-193">Mode: modalità simulazione: predefinita, simulazione, remota, Legacy</span><span class="sxs-lookup"><span data-stu-id="16f65-193">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="16f65-194">**/API/Holographic/Simulation/Control/Stream (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="16f65-194">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="16f65-195">Eliminare un flusso di controllo.</span><span class="sxs-lookup"><span data-stu-id="16f65-195">Delete a control stream.</span></span>

<span data-ttu-id="16f65-196">**/API/Holographic/Simulation/Control/Stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="16f65-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="16f65-197">Aprire una connessione Web socket per un flusso di controllo.</span><span class="sxs-lookup"><span data-stu-id="16f65-197">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="16f65-198">**/API/Holographic/Simulation/Control/Stream (POST)**</span><span class="sxs-lookup"><span data-stu-id="16f65-198">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="16f65-199">Creare un flusso di controllo (priorità obbligatoria) o pubblicare i dati in un flusso creato (streamId richiesto).</span><span class="sxs-lookup"><span data-stu-id="16f65-199">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="16f65-200">È previsto che i dati inviati siano di tipo ' Application/ottetto-Stream '.</span><span class="sxs-lookup"><span data-stu-id="16f65-200">Posted data is expected to be of type 'application/octet-stream'.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="16f65-201">Riproduzione della simulazione di percezione</span><span class="sxs-lookup"><span data-stu-id="16f65-201">Perception Simulation Playback</span></span>

<span data-ttu-id="16f65-202">**/API/Holographic/Simulation/playback/file (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="16f65-202">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="16f65-203">Eliminare una registrazione.</span><span class="sxs-lookup"><span data-stu-id="16f65-203">Delete a recording.</span></span>

<span data-ttu-id="16f65-204">Parametri</span><span class="sxs-lookup"><span data-stu-id="16f65-204">Parameters</span></span>
* <span data-ttu-id="16f65-205">registrazione: nome della registrazione da eliminare.</span><span class="sxs-lookup"><span data-stu-id="16f65-205">recording : Name of recording to delete.</span></span>

<span data-ttu-id="16f65-206">**/API/Holographic/Simulation/playback/file (POST)**</span><span class="sxs-lookup"><span data-stu-id="16f65-206">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="16f65-207">Caricare una registrazione.</span><span class="sxs-lookup"><span data-stu-id="16f65-207">Upload a recording.</span></span>

<span data-ttu-id="16f65-208">**/API/Holographic/Simulation/playback/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="16f65-208">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="16f65-209">Ottenere tutte le registrazioni.</span><span class="sxs-lookup"><span data-stu-id="16f65-209">Get all recordings.</span></span>

<span data-ttu-id="16f65-210">**/API/Holographic/Simulation/playback/Session (GET)**</span><span class="sxs-lookup"><span data-stu-id="16f65-210">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="16f65-211">Ottenere lo stato di riproduzione corrente di una registrazione.</span><span class="sxs-lookup"><span data-stu-id="16f65-211">Get the current playback state of a recording.</span></span>

<span data-ttu-id="16f65-212">Parametri</span><span class="sxs-lookup"><span data-stu-id="16f65-212">Parameters</span></span>
* <span data-ttu-id="16f65-213">registrazione: nome della registrazione.</span><span class="sxs-lookup"><span data-stu-id="16f65-213">recording : Name of recording.</span></span>

<span data-ttu-id="16f65-214">**/API/Holographic/Simulation/playback/Session/file (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="16f65-214">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="16f65-215">Scaricare una registrazione.</span><span class="sxs-lookup"><span data-stu-id="16f65-215">Unload a recording.</span></span>

<span data-ttu-id="16f65-216">Parametri</span><span class="sxs-lookup"><span data-stu-id="16f65-216">Parameters</span></span>
* <span data-ttu-id="16f65-217">registrazione: nome della registrazione da scaricare.</span><span class="sxs-lookup"><span data-stu-id="16f65-217">recording : Name of recording to unload.</span></span>

<span data-ttu-id="16f65-218">**/API/Holographic/Simulation/playback/Session/file (POST)**</span><span class="sxs-lookup"><span data-stu-id="16f65-218">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="16f65-219">Caricare una registrazione.</span><span class="sxs-lookup"><span data-stu-id="16f65-219">Load a recording.</span></span>

<span data-ttu-id="16f65-220">Parametri</span><span class="sxs-lookup"><span data-stu-id="16f65-220">Parameters</span></span>
* <span data-ttu-id="16f65-221">registrazione: nome della registrazione da caricare.</span><span class="sxs-lookup"><span data-stu-id="16f65-221">recording : Name of recording to load.</span></span>

<span data-ttu-id="16f65-222">**/API/Holographic/Simulation/playback/Session/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="16f65-222">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="16f65-223">Ottenere tutte le registrazioni caricate.</span><span class="sxs-lookup"><span data-stu-id="16f65-223">Get all loaded recordings.</span></span>

<span data-ttu-id="16f65-224">**/API/Holographic/Simulation/playback/Session/pause (POST)**</span><span class="sxs-lookup"><span data-stu-id="16f65-224">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="16f65-225">Sospendere la registrazione.</span><span class="sxs-lookup"><span data-stu-id="16f65-225">Pause a recording.</span></span>

<span data-ttu-id="16f65-226">Parametri</span><span class="sxs-lookup"><span data-stu-id="16f65-226">Parameters</span></span>
* <span data-ttu-id="16f65-227">registrazione: nome della registrazione.</span><span class="sxs-lookup"><span data-stu-id="16f65-227">recording : Name of recording.</span></span>

<span data-ttu-id="16f65-228">**/API/Holographic/Simulation/playback/Session/Play (POST)**</span><span class="sxs-lookup"><span data-stu-id="16f65-228">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="16f65-229">Riprodurre una registrazione.</span><span class="sxs-lookup"><span data-stu-id="16f65-229">Play a recording.</span></span>

<span data-ttu-id="16f65-230">Parametri</span><span class="sxs-lookup"><span data-stu-id="16f65-230">Parameters</span></span>
* <span data-ttu-id="16f65-231">registrazione: nome della registrazione.</span><span class="sxs-lookup"><span data-stu-id="16f65-231">recording : Name of recording.</span></span>

<span data-ttu-id="16f65-232">**/API/Holographic/Simulation/playback/Session/Stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="16f65-232">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="16f65-233">Arrestare una registrazione.</span><span class="sxs-lookup"><span data-stu-id="16f65-233">Stop a recording.</span></span>

<span data-ttu-id="16f65-234">Parametri</span><span class="sxs-lookup"><span data-stu-id="16f65-234">Parameters</span></span>
* <span data-ttu-id="16f65-235">registrazione: nome della registrazione.</span><span class="sxs-lookup"><span data-stu-id="16f65-235">recording : Name of recording.</span></span>

<span data-ttu-id="16f65-236">**/API/Holographic/Simulation/playback/Session/types (GET)**</span><span class="sxs-lookup"><span data-stu-id="16f65-236">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="16f65-237">Ottenere i tipi di dati in una registrazione caricata.</span><span class="sxs-lookup"><span data-stu-id="16f65-237">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="16f65-238">Parametri</span><span class="sxs-lookup"><span data-stu-id="16f65-238">Parameters</span></span>
* <span data-ttu-id="16f65-239">registrazione: nome della registrazione.</span><span class="sxs-lookup"><span data-stu-id="16f65-239">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="16f65-240">Registrazione della simulazione della percezione</span><span class="sxs-lookup"><span data-stu-id="16f65-240">Perception Simulation Recording</span></span>

<span data-ttu-id="16f65-241">**/API/Holographic/Simulation/Recording/Start (POST)**</span><span class="sxs-lookup"><span data-stu-id="16f65-241">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="16f65-242">Avviare una registrazione.</span><span class="sxs-lookup"><span data-stu-id="16f65-242">Start a recording.</span></span> <span data-ttu-id="16f65-243">Solo una singola registrazione può essere attiva in una sola volta.</span><span class="sxs-lookup"><span data-stu-id="16f65-243">Only a single recording can be active at once.</span></span> <span data-ttu-id="16f65-244">È necessario impostare una delle intestazioni Head, Hands, spatialMapping o Environment.</span><span class="sxs-lookup"><span data-stu-id="16f65-244">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="16f65-245">Parametri</span><span class="sxs-lookup"><span data-stu-id="16f65-245">Parameters</span></span>
* <span data-ttu-id="16f65-246">Head: impostare su 1 per registrare i dati Head.</span><span class="sxs-lookup"><span data-stu-id="16f65-246">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="16f65-247">Hands: impostare su 1 per registrare i dati della mano.</span><span class="sxs-lookup"><span data-stu-id="16f65-247">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="16f65-248">spatialMapping: impostare su 1 per registrare il mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="16f65-248">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="16f65-249">ambiente: impostare su 1 per registrare i dati dell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="16f65-249">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="16f65-250">Nome: nome della registrazione.</span><span class="sxs-lookup"><span data-stu-id="16f65-250">name : Name of the recording.</span></span>
* <span data-ttu-id="16f65-251">singleSpatialMappingFrame: impostare su 1 per registrare un singolo frame di mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="16f65-251">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="16f65-252">**/API/Holographic/Simulation/Recording/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="16f65-252">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="16f65-253">Ottenere lo stato di registrazione.</span><span class="sxs-lookup"><span data-stu-id="16f65-253">Get recording state.</span></span>

<span data-ttu-id="16f65-254">**/API/Holographic/Simulation/Recording/Stop (GET)**</span><span class="sxs-lookup"><span data-stu-id="16f65-254">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="16f65-255">Arrestare la registrazione corrente.</span><span class="sxs-lookup"><span data-stu-id="16f65-255">Stop the current recording.</span></span> <span data-ttu-id="16f65-256">La registrazione verrà restituita come file.</span><span class="sxs-lookup"><span data-stu-id="16f65-256">Recording will be returned as a file.</span></span>

## <a name="mixed-reality-capture"></a><span data-ttu-id="16f65-257">Mixed Reality Capture</span><span class="sxs-lookup"><span data-stu-id="16f65-257">Mixed Reality Capture</span></span>

<span data-ttu-id="16f65-258">**/API/Holographic/MRC/file (GET)**</span><span class="sxs-lookup"><span data-stu-id="16f65-258">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="16f65-259">Scarica un file di realtà mista dal dispositivo.</span><span class="sxs-lookup"><span data-stu-id="16f65-259">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="16f65-260">Usare il parametro di query op = Stream per il flusso.</span><span class="sxs-lookup"><span data-stu-id="16f65-260">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="16f65-261">Parametri</span><span class="sxs-lookup"><span data-stu-id="16f65-261">Parameters</span></span>
* <span data-ttu-id="16f65-262">filename: Name, hex64 codificato del file video da ottenere</span><span class="sxs-lookup"><span data-stu-id="16f65-262">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="16f65-263">op: Stream</span><span class="sxs-lookup"><span data-stu-id="16f65-263">op : stream</span></span>

<span data-ttu-id="16f65-264">**/API/Holographic/MRC/file (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="16f65-264">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="16f65-265">Elimina una registrazione di realtà mista dal dispositivo.</span><span class="sxs-lookup"><span data-stu-id="16f65-265">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="16f65-266">Parametri</span><span class="sxs-lookup"><span data-stu-id="16f65-266">Parameters</span></span>
* <span data-ttu-id="16f65-267">filename: Name, hex64 codificato del file da eliminare</span><span class="sxs-lookup"><span data-stu-id="16f65-267">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="16f65-268">**/API/Holographic/MRC/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="16f65-268">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="16f65-269">Restituisce l'elenco dei file di realtà mista archiviati nel dispositivo</span><span class="sxs-lookup"><span data-stu-id="16f65-269">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="16f65-270">**/API/Holographic/MRC/Photo (POST)**</span><span class="sxs-lookup"><span data-stu-id="16f65-270">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="16f65-271">Accetta una foto della realtà mista e crea un file nel dispositivo</span><span class="sxs-lookup"><span data-stu-id="16f65-271">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="16f65-272">Parametri</span><span class="sxs-lookup"><span data-stu-id="16f65-272">Parameters</span></span>
* <span data-ttu-id="16f65-273">Holo: Acquisisci ologrammi: true o false (il valore predefinito è false)</span><span class="sxs-lookup"><span data-stu-id="16f65-273">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="16f65-274">PV: Capture PV fotocamera: true o false (il valore predefinito è false)</span><span class="sxs-lookup"><span data-stu-id="16f65-274">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="16f65-275">RenderFromCamera: (solo HoloLens 2) Render dal punto di vista della fotocamera Photo/video: true o false (il valore predefinito è true)</span><span class="sxs-lookup"><span data-stu-id="16f65-275">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="16f65-276">**/API/Holographic/MRC/Settings (GET)**</span><span class="sxs-lookup"><span data-stu-id="16f65-276">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="16f65-277">Ottiene le impostazioni predefinite di acquisizione della realtà mista</span><span class="sxs-lookup"><span data-stu-id="16f65-277">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="16f65-278">**/API/Holographic/MRC/Settings (POST)**</span><span class="sxs-lookup"><span data-stu-id="16f65-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="16f65-279">Imposta le impostazioni predefinite di acquisizione della realtà mista.</span><span class="sxs-lookup"><span data-stu-id="16f65-279">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="16f65-280">Alcune di queste impostazioni vengono applicate all'acquisizione di foto e video di MRC del sistema.</span><span class="sxs-lookup"><span data-stu-id="16f65-280">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="16f65-281">**/API/Holographic/MRC/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="16f65-281">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="16f65-282">Ottiene lo stato della realtà mista registrata (in esecuzione, arrestata)</span><span class="sxs-lookup"><span data-stu-id="16f65-282">Gets the status of the mixed reality recorded (running, stopped)</span></span>

<span data-ttu-id="16f65-283">**/API/Holographic/MRC/Thumbnail (GET)**</span><span class="sxs-lookup"><span data-stu-id="16f65-283">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="16f65-284">Ottiene l'immagine di anteprima per il file specificato.</span><span class="sxs-lookup"><span data-stu-id="16f65-284">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="16f65-285">Parametri</span><span class="sxs-lookup"><span data-stu-id="16f65-285">Parameters</span></span>
* <span data-ttu-id="16f65-286">filename: Name, hex64 codificato, del file per il quale viene richiesta l'anteprima</span><span class="sxs-lookup"><span data-stu-id="16f65-286">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="16f65-287">**/API/Holographic/MRC/video/Control/Start (POST)**</span><span class="sxs-lookup"><span data-stu-id="16f65-287">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="16f65-288">Avvia una registrazione di realtà mista</span><span class="sxs-lookup"><span data-stu-id="16f65-288">Starts a mixed reality recording</span></span>

<span data-ttu-id="16f65-289">Parametri</span><span class="sxs-lookup"><span data-stu-id="16f65-289">Parameters</span></span>
* <span data-ttu-id="16f65-290">Holo: Acquisisci ologrammi: true o false (il valore predefinito è false)</span><span class="sxs-lookup"><span data-stu-id="16f65-290">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="16f65-291">PV: Capture PV fotocamera: true o false (il valore predefinito è false)</span><span class="sxs-lookup"><span data-stu-id="16f65-291">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="16f65-292">MIC: Acquisisci microfono: true o false (il valore predefinito è false)</span><span class="sxs-lookup"><span data-stu-id="16f65-292">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="16f65-293">loopback: Acquisisci audio dell'app: true o false (il valore predefinito è false)</span><span class="sxs-lookup"><span data-stu-id="16f65-293">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="16f65-294">RenderFromCamera: (solo HoloLens 2) Render dal punto di vista della fotocamera Photo/video: true o false (il valore predefinito è true)</span><span class="sxs-lookup"><span data-stu-id="16f65-294">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="16f65-295">Vstab: (solo HoloLens 2) Abilita stabilizzazione video: true o false (il valore predefinito è true)</span><span class="sxs-lookup"><span data-stu-id="16f65-295">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="16f65-296">vstabbuffer: (solo HoloLens 2) latenza buffer di stabilizzazione video: da 0 a 30 fotogrammi (il valore predefinito è 15 fotogrammi)</span><span class="sxs-lookup"><span data-stu-id="16f65-296">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="16f65-297">**/API/Holographic/MRC/video/Control/Stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="16f65-297">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="16f65-298">Arresta la registrazione della realtà mista corrente</span><span class="sxs-lookup"><span data-stu-id="16f65-298">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="16f65-299">Flusso di realtà mista</span><span class="sxs-lookup"><span data-stu-id="16f65-299">Mixed Reality Streaming</span></span>

<span data-ttu-id="16f65-300">HoloLens supporta l'anteprima in tempo reale della realtà mista tramite il download in blocchi di un MP4 frammentato.</span><span class="sxs-lookup"><span data-stu-id="16f65-300">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="16f65-301">I flussi di realtà mista condividono lo stesso set di parametri per controllare gli elementi acquisiti:</span><span class="sxs-lookup"><span data-stu-id="16f65-301">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="16f65-302">Holo: acquisire gli ologrammi: true o false</span><span class="sxs-lookup"><span data-stu-id="16f65-302">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="16f65-303">PV: acquisire la fotocamera PV: true o false</span><span class="sxs-lookup"><span data-stu-id="16f65-303">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="16f65-304">MIC: Acquisisci microfono: true o false</span><span class="sxs-lookup"><span data-stu-id="16f65-304">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="16f65-305">loopback: Acquisisci audio dell'app: true o false</span><span class="sxs-lookup"><span data-stu-id="16f65-305">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="16f65-306">Se non viene specificato alcun valore, verranno acquisiti gli ologrammi, la fotocamera foto/video e l'audio dell'app.</span><span class="sxs-lookup"><span data-stu-id="16f65-306">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="16f65-307">Se viene specificato any: i parametri non specificati verranno impostati su false.</span><span class="sxs-lookup"><span data-stu-id="16f65-307">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="16f65-308">Parametri facoltativi (solo HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="16f65-308">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="16f65-309">RenderFromCamera: rendering dal punto di vista della fotocamera Photo/video: true o false (il valore predefinito è true)</span><span class="sxs-lookup"><span data-stu-id="16f65-309">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="16f65-310">Vstab: Abilita stabilizzazione video: true o false (il valore predefinito è false)</span><span class="sxs-lookup"><span data-stu-id="16f65-310">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="16f65-311">vstabbuffer: latenza buffer di stabilizzazione video: da 0 a 30 fotogrammi (il valore predefinito è 15 fotogrammi)</span><span class="sxs-lookup"><span data-stu-id="16f65-311">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="16f65-312">**/API/Holographic/Stream/Live.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="16f65-312">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="16f65-313">Flusso di 5Mbit 1280x720p 30 fps.</span><span class="sxs-lookup"><span data-stu-id="16f65-313">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="16f65-314">**/API/Holographic/Stream/live_high. mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="16f65-314">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="16f65-315">Flusso di 5Mbit 1280x720p 30 fps.</span><span class="sxs-lookup"><span data-stu-id="16f65-315">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="16f65-316">**/API/Holographic/Stream/live_med. mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="16f65-316">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="16f65-317">Un flusso 854x480p 30 fps da 2 MB.</span><span class="sxs-lookup"><span data-stu-id="16f65-317">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="16f65-318">**/API/Holographic/Stream/live_low. mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="16f65-318">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="16f65-319">Flusso 428x240p 15fps 0.6 Mbit.</span><span class="sxs-lookup"><span data-stu-id="16f65-319">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="16f65-320">Rete</span><span class="sxs-lookup"><span data-stu-id="16f65-320">Networking</span></span>

<span data-ttu-id="16f65-321">**/API/networking/ipconfig (GET)**</span><span class="sxs-lookup"><span data-stu-id="16f65-321">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="16f65-322">Ottiene la configurazione IP corrente</span><span class="sxs-lookup"><span data-stu-id="16f65-322">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="16f65-323">Informazioni sul sistema operativo</span><span class="sxs-lookup"><span data-stu-id="16f65-323">OS Information</span></span>

<span data-ttu-id="16f65-324">**/API/OS/info (GET)**</span><span class="sxs-lookup"><span data-stu-id="16f65-324">**/api/os/info (GET)**</span></span>

<span data-ttu-id="16f65-325">Ottiene le informazioni sul sistema operativo</span><span class="sxs-lookup"><span data-stu-id="16f65-325">Gets operating system information</span></span>

<span data-ttu-id="16f65-326">**/API/OS/MachineName (GET)**</span><span class="sxs-lookup"><span data-stu-id="16f65-326">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="16f65-327">Ottiene il nome del computer</span><span class="sxs-lookup"><span data-stu-id="16f65-327">Gets the machine name</span></span>

<span data-ttu-id="16f65-328">**/API/OS/MachineName (POST)**</span><span class="sxs-lookup"><span data-stu-id="16f65-328">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="16f65-329">Imposta il nome del computer</span><span class="sxs-lookup"><span data-stu-id="16f65-329">Sets the machine name</span></span>

<span data-ttu-id="16f65-330">Parametri</span><span class="sxs-lookup"><span data-stu-id="16f65-330">Parameters</span></span>
* <span data-ttu-id="16f65-331">Nome: nome del nuovo computer, hex64 codificato, per impostare su</span><span class="sxs-lookup"><span data-stu-id="16f65-331">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="performance-data"></a><span data-ttu-id="16f65-332">Dati sulle prestazioni</span><span class="sxs-lookup"><span data-stu-id="16f65-332">Performance data</span></span>

<span data-ttu-id="16f65-333">**/API/ResourceManager/processes (GET)**</span><span class="sxs-lookup"><span data-stu-id="16f65-333">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="16f65-334">Restituisce l'elenco dei processi in esecuzione con i dettagli</span><span class="sxs-lookup"><span data-stu-id="16f65-334">Returns the list of running processes with details</span></span>

<span data-ttu-id="16f65-335">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="16f65-335">Return data</span></span>
* <span data-ttu-id="16f65-336">JSON con elenco di processi e dettagli per ogni processo</span><span class="sxs-lookup"><span data-stu-id="16f65-336">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="16f65-337">**/API/ResourceManager/systemperf (GET)**</span><span class="sxs-lookup"><span data-stu-id="16f65-337">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="16f65-338">Restituisce le statistiche sulle prestazioni di sistema (lettura/scrittura di I/O, statistiche sulla memoria e così via.</span><span class="sxs-lookup"><span data-stu-id="16f65-338">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="16f65-339">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="16f65-339">Return data</span></span>
* <span data-ttu-id="16f65-340">JSON con informazioni di sistema: CPU, GPU, memoria, rete, IO</span><span class="sxs-lookup"><span data-stu-id="16f65-340">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="16f65-341">Alimentazione</span><span class="sxs-lookup"><span data-stu-id="16f65-341">Power</span></span>

<span data-ttu-id="16f65-342">**/API/Power/Battery (GET)**</span><span class="sxs-lookup"><span data-stu-id="16f65-342">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="16f65-343">Ottiene lo stato corrente della batteria</span><span class="sxs-lookup"><span data-stu-id="16f65-343">Gets the current battery state</span></span>

<span data-ttu-id="16f65-344">**/API/Power/State (GET)**</span><span class="sxs-lookup"><span data-stu-id="16f65-344">**/api/power/state (GET)**</span></span>

<span data-ttu-id="16f65-345">Controlla se il sistema è in uno stato di alimentazione basso</span><span class="sxs-lookup"><span data-stu-id="16f65-345">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="16f65-346">Controllo remoto</span><span class="sxs-lookup"><span data-stu-id="16f65-346">Remote Control</span></span>

<span data-ttu-id="16f65-347">**/API/Control/Restart (POST)**</span><span class="sxs-lookup"><span data-stu-id="16f65-347">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="16f65-348">Riavvia il dispositivo di destinazione</span><span class="sxs-lookup"><span data-stu-id="16f65-348">Restarts the target device</span></span>

<span data-ttu-id="16f65-349">**/API/Control/Shutdown (POST)**</span><span class="sxs-lookup"><span data-stu-id="16f65-349">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="16f65-350">Arresta il dispositivo di destinazione</span><span class="sxs-lookup"><span data-stu-id="16f65-350">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="16f65-351">Gestione attività</span><span class="sxs-lookup"><span data-stu-id="16f65-351">Task Manager</span></span>

<span data-ttu-id="16f65-352">**/API/taskmanager/app (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="16f65-352">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="16f65-353">Arresta un'app moderna</span><span class="sxs-lookup"><span data-stu-id="16f65-353">Stops a modern app</span></span>

<span data-ttu-id="16f65-354">Parametri</span><span class="sxs-lookup"><span data-stu-id="16f65-354">Parameters</span></span>
* <span data-ttu-id="16f65-355">pacchetto: nome completo del pacchetto dell'app, codificato in hex64</span><span class="sxs-lookup"><span data-stu-id="16f65-355">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="16f65-356">forcestop: forza l'arresto di tutti i processi (= Yes)</span><span class="sxs-lookup"><span data-stu-id="16f65-356">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="16f65-357">**/API/taskmanager/app (POST)**</span><span class="sxs-lookup"><span data-stu-id="16f65-357">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="16f65-358">Avvia un'app moderna</span><span class="sxs-lookup"><span data-stu-id="16f65-358">Starts a modern app</span></span>

<span data-ttu-id="16f65-359">Parametri</span><span class="sxs-lookup"><span data-stu-id="16f65-359">Parameters</span></span>
* <span data-ttu-id="16f65-360">AppID: PRAID dell'app da avviare, hex64 codificato</span><span class="sxs-lookup"><span data-stu-id="16f65-360">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="16f65-361">pacchetto: nome completo del pacchetto dell'app, codificato in hex64</span><span class="sxs-lookup"><span data-stu-id="16f65-361">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="16f65-362">Gestione Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="16f65-362">WiFi Management</span></span>

<span data-ttu-id="16f65-363">**/API/WiFi/Interfaces (GET)**</span><span class="sxs-lookup"><span data-stu-id="16f65-363">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="16f65-364">Enumera le interfacce di rete wireless</span><span class="sxs-lookup"><span data-stu-id="16f65-364">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="16f65-365">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="16f65-365">Return data</span></span>
* <span data-ttu-id="16f65-366">Elenco di interfacce wireless con dettagli (GUID, descrizione e così via)</span><span class="sxs-lookup"><span data-stu-id="16f65-366">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="16f65-367">**/API/WiFi/Network (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="16f65-367">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="16f65-368">Elimina un profilo associato a una rete in un'interfaccia specificata</span><span class="sxs-lookup"><span data-stu-id="16f65-368">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="16f65-369">Parametri</span><span class="sxs-lookup"><span data-stu-id="16f65-369">Parameters</span></span>
* <span data-ttu-id="16f65-370">interfaccia: GUID dell'interfaccia di rete</span><span class="sxs-lookup"><span data-stu-id="16f65-370">interface : network interface guid</span></span>
* <span data-ttu-id="16f65-371">profilo: nome profilo</span><span class="sxs-lookup"><span data-stu-id="16f65-371">profile : profile name</span></span>

<span data-ttu-id="16f65-372">**/API/WiFi/Networks (GET)**</span><span class="sxs-lookup"><span data-stu-id="16f65-372">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="16f65-373">Enumera le reti wireless sull'interfaccia di rete specificata</span><span class="sxs-lookup"><span data-stu-id="16f65-373">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="16f65-374">Parametri</span><span class="sxs-lookup"><span data-stu-id="16f65-374">Parameters</span></span>
* <span data-ttu-id="16f65-375">interfaccia: GUID dell'interfaccia di rete</span><span class="sxs-lookup"><span data-stu-id="16f65-375">interface : network interface guid</span></span>

<span data-ttu-id="16f65-376">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="16f65-376">Return data</span></span>
* <span data-ttu-id="16f65-377">Elenco di reti wireless disponibili nell'interfaccia di rete con i dettagli</span><span class="sxs-lookup"><span data-stu-id="16f65-377">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="16f65-378">**/API/WiFi/Network (POST)**</span><span class="sxs-lookup"><span data-stu-id="16f65-378">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="16f65-379">Si connette o si disconnette a una rete sull'interfaccia specificata</span><span class="sxs-lookup"><span data-stu-id="16f65-379">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="16f65-380">Parametri</span><span class="sxs-lookup"><span data-stu-id="16f65-380">Parameters</span></span>
* <span data-ttu-id="16f65-381">interfaccia: GUID dell'interfaccia di rete</span><span class="sxs-lookup"><span data-stu-id="16f65-381">interface : network interface guid</span></span>
* <span data-ttu-id="16f65-382">SSID: SSID, hex64 codificato, per la connessione a</span><span class="sxs-lookup"><span data-stu-id="16f65-382">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="16f65-383">op: connessione o disconnessione</span><span class="sxs-lookup"><span data-stu-id="16f65-383">op : connect or disconnect</span></span>
* <span data-ttu-id="16f65-384">CreateProfile: Sì o no</span><span class="sxs-lookup"><span data-stu-id="16f65-384">createprofile : yes or no</span></span>
* <span data-ttu-id="16f65-385">chiave: chiave condivisa, codificato in hex64</span><span class="sxs-lookup"><span data-stu-id="16f65-385">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="16f65-386">Registratore prestazioni Windows</span><span class="sxs-lookup"><span data-stu-id="16f65-386">Windows Performance Recorder</span></span>

<span data-ttu-id="16f65-387">**/API/WPR/customtrace (POST)**</span><span class="sxs-lookup"><span data-stu-id="16f65-387">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="16f65-388">Carica un profilo WPR e avvia la traccia usando il profilo caricato.</span><span class="sxs-lookup"><span data-stu-id="16f65-388">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="16f65-389">Payload</span><span class="sxs-lookup"><span data-stu-id="16f65-389">Payload</span></span>
* <span data-ttu-id="16f65-390">corpo HTTP conforme a più parti</span><span class="sxs-lookup"><span data-stu-id="16f65-390">multi-part conforming http body</span></span>

<span data-ttu-id="16f65-391">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="16f65-391">Return data</span></span>
* <span data-ttu-id="16f65-392">Restituisce lo stato della sessione WPR.</span><span class="sxs-lookup"><span data-stu-id="16f65-392">Returns the WPR session status.</span></span>

<span data-ttu-id="16f65-393">**/API/WPR/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="16f65-393">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="16f65-394">Recupera lo stato della sessione WPR</span><span class="sxs-lookup"><span data-stu-id="16f65-394">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="16f65-395">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="16f65-395">Return data</span></span>
* <span data-ttu-id="16f65-396">Stato della sessione WPR.</span><span class="sxs-lookup"><span data-stu-id="16f65-396">WPR session status.</span></span>

<span data-ttu-id="16f65-397">**/API/WPR/Trace (GET)**</span><span class="sxs-lookup"><span data-stu-id="16f65-397">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="16f65-398">Arresta una sessione di traccia WPR (performance)</span><span class="sxs-lookup"><span data-stu-id="16f65-398">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="16f65-399">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="16f65-399">Return data</span></span>
* <span data-ttu-id="16f65-400">Restituisce il file ETL di traccia</span><span class="sxs-lookup"><span data-stu-id="16f65-400">Returns the trace ETL file</span></span>

<span data-ttu-id="16f65-401">**/API/WPR/Trace (POST)**</span><span class="sxs-lookup"><span data-stu-id="16f65-401">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="16f65-402">Avvia una sessione di traccia WPR (performance)</span><span class="sxs-lookup"><span data-stu-id="16f65-402">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="16f65-403">Parametri</span><span class="sxs-lookup"><span data-stu-id="16f65-403">Parameters</span></span>
* <span data-ttu-id="16f65-404">profilo: nome profilo.</span><span class="sxs-lookup"><span data-stu-id="16f65-404">profile : Profile name.</span></span> <span data-ttu-id="16f65-405">I profili disponibili sono archiviati in perfprofiles/Profiles. JSON</span><span class="sxs-lookup"><span data-stu-id="16f65-405">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="16f65-406">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="16f65-406">Return data</span></span>
* <span data-ttu-id="16f65-407">All'avvio, restituisce lo stato della sessione WPR.</span><span class="sxs-lookup"><span data-stu-id="16f65-407">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="16f65-408">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="16f65-408">See also</span></span>
* [<span data-ttu-id="16f65-409">Avviare il Portale di dispositivi di Windows</span><span class="sxs-lookup"><span data-stu-id="16f65-409">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="16f65-410">Informazioni di riferimento sulle API del portale per dispositivi (UWP)</span><span class="sxs-lookup"><span data-stu-id="16f65-410">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)

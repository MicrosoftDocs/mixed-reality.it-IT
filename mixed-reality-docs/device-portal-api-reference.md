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
# <a name="device-portal-api-reference"></a><span data-ttu-id="1df9b-104">Portale del dispositivo di riferimento all'API</span><span class="sxs-lookup"><span data-stu-id="1df9b-104">Device portal API reference</span></span>

<span data-ttu-id="1df9b-105">Tutti gli elementi di [Windows Device Portal](using-the-windows-device-portal.md) si basa sull'API REST che è possibile usare per accedere ai dati e controllare il dispositivo a livello di codice.</span><span class="sxs-lookup"><span data-stu-id="1df9b-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="1df9b-106">Distribuzione di App</span><span class="sxs-lookup"><span data-stu-id="1df9b-106">App deloyment</span></span>

<span data-ttu-id="1df9b-107">**/API/App/packagemanager/package (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="1df9b-108">Disinstalla un'app</span><span class="sxs-lookup"><span data-stu-id="1df9b-108">Uninstalls an app</span></span>

<span data-ttu-id="1df9b-109">Parametri</span><span class="sxs-lookup"><span data-stu-id="1df9b-109">Parameters</span></span>
* <span data-ttu-id="1df9b-110">pacchetto: Nome del file del pacchetto da disinstallare.</span><span class="sxs-lookup"><span data-stu-id="1df9b-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="1df9b-111">**/api/app/packagemanager/package (POST)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="1df9b-112">Installa un'App</span><span class="sxs-lookup"><span data-stu-id="1df9b-112">Installs an App</span></span>

<span data-ttu-id="1df9b-113">Parametri</span><span class="sxs-lookup"><span data-stu-id="1df9b-113">Parameters</span></span>
* <span data-ttu-id="1df9b-114">pacchetto: Nome del file del pacchetto da installare.</span><span class="sxs-lookup"><span data-stu-id="1df9b-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="1df9b-115">payload</span><span class="sxs-lookup"><span data-stu-id="1df9b-115">Payload</span></span>
* <span data-ttu-id="1df9b-116">più parti corpo http conforme</span><span class="sxs-lookup"><span data-stu-id="1df9b-116">multi-part conforming http body</span></span>

<span data-ttu-id="1df9b-117">**/api/app/packagemanager/packages (GET)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="1df9b-118">Recupera l'elenco delle App installate nel sistema, con dettagli</span><span class="sxs-lookup"><span data-stu-id="1df9b-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="1df9b-119">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="1df9b-119">Return data</span></span>
* <span data-ttu-id="1df9b-120">Elenco dei pacchetti installati con i dettagli</span><span class="sxs-lookup"><span data-stu-id="1df9b-120">List of installed packages with details</span></span>

<span data-ttu-id="1df9b-121">**/api/app/packagemanager/state (GET)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="1df9b-122">Ottiene lo stato dell'installazione dell'app lo stato di avanzamento</span><span class="sxs-lookup"><span data-stu-id="1df9b-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="1df9b-123">Raccolta dei dump</span><span class="sxs-lookup"><span data-stu-id="1df9b-123">Dump collection</span></span>

<span data-ttu-id="1df9b-124">**/API/debug/dump/usermode/CrashControl (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="1df9b-125">Disabilita l'arresto anomalo del sistema di raccolta dei dump per un'app con sideload</span><span class="sxs-lookup"><span data-stu-id="1df9b-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="1df9b-126">Parametri</span><span class="sxs-lookup"><span data-stu-id="1df9b-126">Parameters</span></span>
* <span data-ttu-id="1df9b-127">packageFullname: nome del pacchetto</span><span class="sxs-lookup"><span data-stu-id="1df9b-127">packageFullname : package name</span></span>

<span data-ttu-id="1df9b-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="1df9b-129">Ottiene le impostazioni per le app con sideload raccolta dei dump di arresto anomalo del sistema</span><span class="sxs-lookup"><span data-stu-id="1df9b-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="1df9b-130">Parametri</span><span class="sxs-lookup"><span data-stu-id="1df9b-130">Parameters</span></span>
* <span data-ttu-id="1df9b-131">packageFullname: nome del pacchetto</span><span class="sxs-lookup"><span data-stu-id="1df9b-131">packageFullname : package name</span></span>

<span data-ttu-id="1df9b-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="1df9b-133">Attiva e configura le impostazioni di controllo di dump per un'app con sideload</span><span class="sxs-lookup"><span data-stu-id="1df9b-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="1df9b-134">Parametri</span><span class="sxs-lookup"><span data-stu-id="1df9b-134">Parameters</span></span>
* <span data-ttu-id="1df9b-135">packageFullname: nome del pacchetto</span><span class="sxs-lookup"><span data-stu-id="1df9b-135">packageFullname : package name</span></span>

<span data-ttu-id="1df9b-136">**/API/debug/dump/usermode/crashdump (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="1df9b-137">Elimina un dump di arresto anomalo del sistema per un'app con sideload</span><span class="sxs-lookup"><span data-stu-id="1df9b-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="1df9b-138">Parametri</span><span class="sxs-lookup"><span data-stu-id="1df9b-138">Parameters</span></span>
* <span data-ttu-id="1df9b-139">packageFullname: nome del pacchetto</span><span class="sxs-lookup"><span data-stu-id="1df9b-139">packageFullname : package name</span></span>
* <span data-ttu-id="1df9b-140">nome file: nome del file dump</span><span class="sxs-lookup"><span data-stu-id="1df9b-140">fileName : dump file name</span></span>

<span data-ttu-id="1df9b-141">**/api/debug/dump/usermode/crashdump (GET)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="1df9b-142">Recupera un dump di arresto anomalo del sistema per un'app con sideload</span><span class="sxs-lookup"><span data-stu-id="1df9b-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="1df9b-143">Parametri</span><span class="sxs-lookup"><span data-stu-id="1df9b-143">Parameters</span></span>
* <span data-ttu-id="1df9b-144">packageFullname: nome del pacchetto</span><span class="sxs-lookup"><span data-stu-id="1df9b-144">packageFullname : package name</span></span>
* <span data-ttu-id="1df9b-145">nome file: nome del file dump</span><span class="sxs-lookup"><span data-stu-id="1df9b-145">fileName : dump file name</span></span>

<span data-ttu-id="1df9b-146">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="1df9b-146">Return data</span></span>
* <span data-ttu-id="1df9b-147">File di dump.</span><span class="sxs-lookup"><span data-stu-id="1df9b-147">Dump file.</span></span> <span data-ttu-id="1df9b-148">Controllare con WinDbg o di Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1df9b-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="1df9b-149">**/api/debug/dump/usermode/dumps (GET)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="1df9b-150">Restituisce un elenco di tutti i dettagli di arresto anomalo per le app con sideload</span><span class="sxs-lookup"><span data-stu-id="1df9b-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="1df9b-151">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="1df9b-151">Return data</span></span>
* <span data-ttu-id="1df9b-152">Elenco di arresto anomalo del sistema esegue il dump per ogni app caricata lato</span><span class="sxs-lookup"><span data-stu-id="1df9b-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="1df9b-153">ETW</span><span class="sxs-lookup"><span data-stu-id="1df9b-153">ETW</span></span>

<span data-ttu-id="1df9b-154">**/api/etw/providers (GET)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="1df9b-155">Enumera i provider registrati</span><span class="sxs-lookup"><span data-stu-id="1df9b-155">Enumerates registered providers</span></span>

<span data-ttu-id="1df9b-156">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="1df9b-156">Return data</span></span>
* <span data-ttu-id="1df9b-157">Elenco dei provider, nome descrittivo e GUID</span><span class="sxs-lookup"><span data-stu-id="1df9b-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="1df9b-158">**/api/etw/session/realtime (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="1df9b-159">Crea una sessione ETW in tempo reale. gestita su un websocket.</span><span class="sxs-lookup"><span data-stu-id="1df9b-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="1df9b-160">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="1df9b-160">Return data</span></span>
* <span data-ttu-id="1df9b-161">Eventi ETW da provider attivati</span><span class="sxs-lookup"><span data-stu-id="1df9b-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="1df9b-162">Sistema operativo olografico</span><span class="sxs-lookup"><span data-stu-id="1df9b-162">Holographic OS</span></span>

<span data-ttu-id="1df9b-163">**/api/holographic/os/etw/customproviders (GET)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="1df9b-164">Restituisce un elenco di provider ETW specifico HoloLens che non sono registrati con il sistema</span><span class="sxs-lookup"><span data-stu-id="1df9b-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="1df9b-165">**/api/holographic/os/services (GET)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="1df9b-166">Restituisce gli stati di tutti i servizi in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="1df9b-166">Returns the states of all services running.</span></span>

<span data-ttu-id="1df9b-167">**/api/holographic/os/settings/ipd (GET)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="1df9b-168">Ottiene il IPD stored (Interpupillary distanza) in millimetri</span><span class="sxs-lookup"><span data-stu-id="1df9b-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="1df9b-169">**/api/holographic/os/settings/ipd (POST)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="1df9b-170">Imposta IPD</span><span class="sxs-lookup"><span data-stu-id="1df9b-170">Sets the IPD</span></span>

<span data-ttu-id="1df9b-171">Parametri</span><span class="sxs-lookup"><span data-stu-id="1df9b-171">Parameters</span></span>
* <span data-ttu-id="1df9b-172">IPD: Nuovo valore IPD vengano impostati in millimetri</span><span class="sxs-lookup"><span data-stu-id="1df9b-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="1df9b-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="1df9b-174">Ottenere richieste HTTPS per Device Portal</span><span class="sxs-lookup"><span data-stu-id="1df9b-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="1df9b-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="1df9b-176">Imposta i requisiti di HTTPS per il portale del dispositivo</span><span class="sxs-lookup"><span data-stu-id="1df9b-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="1df9b-177">Parametri</span><span class="sxs-lookup"><span data-stu-id="1df9b-177">Parameters</span></span>
* <span data-ttu-id="1df9b-178">obbligatorio: Sì, no o default</span><span class="sxs-lookup"><span data-stu-id="1df9b-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="1df9b-179">Percezione holographic</span><span class="sxs-lookup"><span data-stu-id="1df9b-179">Holographic Perception</span></span>

<span data-ttu-id="1df9b-180">**/api/holographic/perception/client (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="1df9b-181">Accetta gli aggiornamenti di websocket ed esegue un client di percezione che invia gli aggiornamenti di 30 fps.</span><span class="sxs-lookup"><span data-stu-id="1df9b-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="1df9b-182">Parametri</span><span class="sxs-lookup"><span data-stu-id="1df9b-182">Parameters</span></span>
* <span data-ttu-id="1df9b-183">clientmode: "attivo" forza la modalità di rilevamento visual quando non è possibile stabilire passivamente</span><span class="sxs-lookup"><span data-stu-id="1df9b-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="1df9b-184">Holographic termico</span><span class="sxs-lookup"><span data-stu-id="1df9b-184">Holographic Thermal</span></span>

<span data-ttu-id="1df9b-185">**/api/holographic/thermal/stage (GET)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="1df9b-186">Ottenere la fase termica del dispositivo (0 normale, 1 warm, 2 critico)</span><span class="sxs-lookup"><span data-stu-id="1df9b-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="1df9b-187">Controllo di simulazione di percezione</span><span class="sxs-lookup"><span data-stu-id="1df9b-187">Perception Simulation Control</span></span>

<span data-ttu-id="1df9b-188">**/api/holographic/simulation/control/mode (GET)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-188">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="1df9b-189">Ottenere la modalità di simulazione</span><span class="sxs-lookup"><span data-stu-id="1df9b-189">Get the simulation mode</span></span>

<span data-ttu-id="1df9b-190">**/api/holographic/simulation/control/mode (POST)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-190">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="1df9b-191">Impostare la modalità di simulazione</span><span class="sxs-lookup"><span data-stu-id="1df9b-191">Set the simulation mode</span></span>

<span data-ttu-id="1df9b-192">Parametri</span><span class="sxs-lookup"><span data-stu-id="1df9b-192">Parameters</span></span>
* <span data-ttu-id="1df9b-193">modalità: modalità di simulazione: predefinito, simulazione, remote, legacy</span><span class="sxs-lookup"><span data-stu-id="1df9b-193">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="1df9b-194">**/API/holographic/Simulation/Control/Stream (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-194">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="1df9b-195">Eliminare un flusso di controllo.</span><span class="sxs-lookup"><span data-stu-id="1df9b-195">Delete a control stream.</span></span>

<span data-ttu-id="1df9b-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="1df9b-197">Aprire una connessione web socket per un flusso di controllo.</span><span class="sxs-lookup"><span data-stu-id="1df9b-197">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="1df9b-198">**/api/holographic/simulation/control/stream (POST)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-198">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="1df9b-199">Creare un flusso di controllo (priorità è obbligatorio) o inviare i dati in un flusso creato (streamId richiesto).</span><span class="sxs-lookup"><span data-stu-id="1df9b-199">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="1df9b-200">I dati inseriti dovrebbe essere di tipo ' application/octet-stream'.</span><span class="sxs-lookup"><span data-stu-id="1df9b-200">Posted data is expected to be of type 'application/octet-stream'.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="1df9b-201">Riproduzione di simulazione di percezione</span><span class="sxs-lookup"><span data-stu-id="1df9b-201">Perception Simulation Playback</span></span>

<span data-ttu-id="1df9b-202">**/API/holographic/Simulation/Playback/file (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-202">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="1df9b-203">Eliminare una registrazione.</span><span class="sxs-lookup"><span data-stu-id="1df9b-203">Delete a recording.</span></span>

<span data-ttu-id="1df9b-204">Parametri</span><span class="sxs-lookup"><span data-stu-id="1df9b-204">Parameters</span></span>
* <span data-ttu-id="1df9b-205">la registrazione: Nome della registrazione per eliminare.</span><span class="sxs-lookup"><span data-stu-id="1df9b-205">recording : Name of recording to delete.</span></span>

<span data-ttu-id="1df9b-206">**/API/holographic/Simulation/Playback/file (POST)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-206">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="1df9b-207">Caricare una registrazione.</span><span class="sxs-lookup"><span data-stu-id="1df9b-207">Upload a recording.</span></span>

<span data-ttu-id="1df9b-208">**/API/holographic/Simulation/Playback/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-208">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="1df9b-209">Ottenere tutte le registrazioni.</span><span class="sxs-lookup"><span data-stu-id="1df9b-209">Get all recordings.</span></span>

<span data-ttu-id="1df9b-210">**/API/holographic/Simulation/Playback/Session (GET)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-210">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="1df9b-211">Ottenere lo stato corrente di riproduzione della registrazione.</span><span class="sxs-lookup"><span data-stu-id="1df9b-211">Get the current playback state of a recording.</span></span>

<span data-ttu-id="1df9b-212">Parametri</span><span class="sxs-lookup"><span data-stu-id="1df9b-212">Parameters</span></span>
* <span data-ttu-id="1df9b-213">la registrazione: Nome della registrazione.</span><span class="sxs-lookup"><span data-stu-id="1df9b-213">recording : Name of recording.</span></span>

<span data-ttu-id="1df9b-214">**/API/holographic/Simulation/Playback/Session/file (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-214">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="1df9b-215">Scaricare una registrazione.</span><span class="sxs-lookup"><span data-stu-id="1df9b-215">Unload a recording.</span></span>

<span data-ttu-id="1df9b-216">Parametri</span><span class="sxs-lookup"><span data-stu-id="1df9b-216">Parameters</span></span>
* <span data-ttu-id="1df9b-217">la registrazione: Nome della registrazione per scaricare.</span><span class="sxs-lookup"><span data-stu-id="1df9b-217">recording : Name of recording to unload.</span></span>

<span data-ttu-id="1df9b-218">**/api/holographic/simulation/playback/session/file (POST)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-218">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="1df9b-219">Caricare una registrazione.</span><span class="sxs-lookup"><span data-stu-id="1df9b-219">Load a recording.</span></span>

<span data-ttu-id="1df9b-220">Parametri</span><span class="sxs-lookup"><span data-stu-id="1df9b-220">Parameters</span></span>
* <span data-ttu-id="1df9b-221">la registrazione: Nome della registrazione per il caricamento.</span><span class="sxs-lookup"><span data-stu-id="1df9b-221">recording : Name of recording to load.</span></span>

<span data-ttu-id="1df9b-222">**/API/holographic/Simulation/Playback/Session/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-222">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="1df9b-223">Ottenere registrazioni tutto caricate.</span><span class="sxs-lookup"><span data-stu-id="1df9b-223">Get all loaded recordings.</span></span>

<span data-ttu-id="1df9b-224">**/API/holographic/Simulation/Playback/Session/pause (POST)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-224">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="1df9b-225">Sospendere la registrazione.</span><span class="sxs-lookup"><span data-stu-id="1df9b-225">Pause a recording.</span></span>

<span data-ttu-id="1df9b-226">Parametri</span><span class="sxs-lookup"><span data-stu-id="1df9b-226">Parameters</span></span>
* <span data-ttu-id="1df9b-227">la registrazione: Nome della registrazione.</span><span class="sxs-lookup"><span data-stu-id="1df9b-227">recording : Name of recording.</span></span>

<span data-ttu-id="1df9b-228">**/API/holographic/Simulation/Playback/Session/Play (POST)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-228">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="1df9b-229">Riprodurre una registrazione.</span><span class="sxs-lookup"><span data-stu-id="1df9b-229">Play a recording.</span></span>

<span data-ttu-id="1df9b-230">Parametri</span><span class="sxs-lookup"><span data-stu-id="1df9b-230">Parameters</span></span>
* <span data-ttu-id="1df9b-231">la registrazione: Nome della registrazione.</span><span class="sxs-lookup"><span data-stu-id="1df9b-231">recording : Name of recording.</span></span>

<span data-ttu-id="1df9b-232">**/api/holographic/simulation/playback/session/stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-232">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="1df9b-233">Arrestare la registrazione.</span><span class="sxs-lookup"><span data-stu-id="1df9b-233">Stop a recording.</span></span>

<span data-ttu-id="1df9b-234">Parametri</span><span class="sxs-lookup"><span data-stu-id="1df9b-234">Parameters</span></span>
* <span data-ttu-id="1df9b-235">la registrazione: Nome della registrazione.</span><span class="sxs-lookup"><span data-stu-id="1df9b-235">recording : Name of recording.</span></span>

<span data-ttu-id="1df9b-236">**/API/holographic/Simulation/Playback/Session/Types (GET)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-236">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="1df9b-237">Ottenere i tipi di dati in una registrazione caricata.</span><span class="sxs-lookup"><span data-stu-id="1df9b-237">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="1df9b-238">Parametri</span><span class="sxs-lookup"><span data-stu-id="1df9b-238">Parameters</span></span>
* <span data-ttu-id="1df9b-239">la registrazione: Nome della registrazione.</span><span class="sxs-lookup"><span data-stu-id="1df9b-239">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="1df9b-240">Registrazione di simulazione di percezione</span><span class="sxs-lookup"><span data-stu-id="1df9b-240">Perception Simulation Recording</span></span>

<span data-ttu-id="1df9b-241">**/api/holographic/simulation/recording/start (POST)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-241">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="1df9b-242">Avviare una registrazione.</span><span class="sxs-lookup"><span data-stu-id="1df9b-242">Start a recording.</span></span> <span data-ttu-id="1df9b-243">Solo una singola registrazione può essere attiva contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="1df9b-243">Only a single recording can be active at once.</span></span> <span data-ttu-id="1df9b-244">Head, mani, spatialMapping o ambiente deve essere impostata.</span><span class="sxs-lookup"><span data-stu-id="1df9b-244">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="1df9b-245">Parametri</span><span class="sxs-lookup"><span data-stu-id="1df9b-245">Parameters</span></span>
* <span data-ttu-id="1df9b-246">Head: Impostare su 1 per registrare i dati head.</span><span class="sxs-lookup"><span data-stu-id="1df9b-246">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="1df9b-247">pratico: Impostare su 1 per registrare manualmente i dati.</span><span class="sxs-lookup"><span data-stu-id="1df9b-247">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="1df9b-248">spatialMapping: Impostare su 1 per registrare mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="1df9b-248">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="1df9b-249">ambiente: Impostare su 1 per registrare i dati di ambiente.</span><span class="sxs-lookup"><span data-stu-id="1df9b-249">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="1df9b-250">nome: Nome della registrazione.</span><span class="sxs-lookup"><span data-stu-id="1df9b-250">name : Name of the recording.</span></span>
* <span data-ttu-id="1df9b-251">singleSpatialMappingFrame: Impostare su 1 per registrare solo un frame solo mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="1df9b-251">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="1df9b-252">**/api/holographic/simulation/recording/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-252">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="1df9b-253">Ottenere la registrazione dello stato.</span><span class="sxs-lookup"><span data-stu-id="1df9b-253">Get recording state.</span></span>

<span data-ttu-id="1df9b-254">**/api/holographic/simulation/recording/stop (GET)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-254">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="1df9b-255">Arrestare la registrazione corrente.</span><span class="sxs-lookup"><span data-stu-id="1df9b-255">Stop the current recording.</span></span> <span data-ttu-id="1df9b-256">La registrazione verrà restituita come un file.</span><span class="sxs-lookup"><span data-stu-id="1df9b-256">Recording will be returned as a file.</span></span>

## <a name="mixed-reality-capture"></a><span data-ttu-id="1df9b-257">Mixed Reality Capture</span><span class="sxs-lookup"><span data-stu-id="1df9b-257">Mixed Reality Capture</span></span>

<span data-ttu-id="1df9b-258">**/API/holographic/MRC/file (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-258">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="1df9b-259">Elimina una realtà mista di registrazione dal dispositivo.</span><span class="sxs-lookup"><span data-stu-id="1df9b-259">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="1df9b-260">Parametri</span><span class="sxs-lookup"><span data-stu-id="1df9b-260">Parameters</span></span>
* <span data-ttu-id="1df9b-261">nome file: Il nome, hex64 codificato, del file da eliminare</span><span class="sxs-lookup"><span data-stu-id="1df9b-261">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="1df9b-262">**/api/holographic/mrc/settings (GET)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-262">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="1df9b-263">Ottiene il valore predefinito realtà mista le impostazioni di acquisizione</span><span class="sxs-lookup"><span data-stu-id="1df9b-263">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="1df9b-264">**/api/holographic/mrc/file (GET)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-264">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="1df9b-265">Scarica un file di realtà mista dal dispositivo.</span><span class="sxs-lookup"><span data-stu-id="1df9b-265">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="1df9b-266">Op usare = parametro di query di flusso per lo streaming.</span><span class="sxs-lookup"><span data-stu-id="1df9b-266">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="1df9b-267">Parametri</span><span class="sxs-lookup"><span data-stu-id="1df9b-267">Parameters</span></span>
* <span data-ttu-id="1df9b-268">nome file: Il nome, hex64 codificato, del file video di introduzione</span><span class="sxs-lookup"><span data-stu-id="1df9b-268">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="1df9b-269">Op: flusso</span><span class="sxs-lookup"><span data-stu-id="1df9b-269">op : stream</span></span>

<span data-ttu-id="1df9b-270">**/api/holographic/mrc/thumbnail (GET)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-270">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="1df9b-271">Ottiene l'immagine di anteprima per il file specificato.</span><span class="sxs-lookup"><span data-stu-id="1df9b-271">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="1df9b-272">Parametri</span><span class="sxs-lookup"><span data-stu-id="1df9b-272">Parameters</span></span>
* <span data-ttu-id="1df9b-273">nome file: Il nome, hex64 codificato, del file per cui viene richiesto l'anteprima</span><span class="sxs-lookup"><span data-stu-id="1df9b-273">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="1df9b-274">**/api/holographic/mrc/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-274">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="1df9b-275">Ottiene lo stato della realtà mista registrate (in esecuzione, arrestato)</span><span class="sxs-lookup"><span data-stu-id="1df9b-275">Gets the status of the mixed reality recorded (running, stopped)</span></span>

<span data-ttu-id="1df9b-276">**/API/holographic/MRC/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-276">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="1df9b-277">Restituisce l'elenco dei file di realtà mista archiviati nel dispositivo</span><span class="sxs-lookup"><span data-stu-id="1df9b-277">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="1df9b-278">**/api/holographic/mrc/settings (POST)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="1df9b-279">Imposta il valore predefinito realtà mista le impostazioni di acquisizione</span><span class="sxs-lookup"><span data-stu-id="1df9b-279">Sets the default mixed reality capture settings</span></span>

<span data-ttu-id="1df9b-280">**/api/holographic/mrc/video/control/start (POST)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-280">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="1df9b-281">Avvia una registrazione di realtà mista</span><span class="sxs-lookup"><span data-stu-id="1df9b-281">Starts a mixed reality recording</span></span>

<span data-ttu-id="1df9b-282">Parametri</span><span class="sxs-lookup"><span data-stu-id="1df9b-282">Parameters</span></span>
* <span data-ttu-id="1df9b-283">holo: acquisire vntana: true o false</span><span class="sxs-lookup"><span data-stu-id="1df9b-283">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="1df9b-284">PV: acquisizione PV fotocamera: true o false</span><span class="sxs-lookup"><span data-stu-id="1df9b-284">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="1df9b-285">MIC: acquisizione microfono: true o false</span><span class="sxs-lookup"><span data-stu-id="1df9b-285">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="1df9b-286">loopback: acquisizione di app audio: true o false</span><span class="sxs-lookup"><span data-stu-id="1df9b-286">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="1df9b-287">**/api/holographic/mrc/video/control/stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-287">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="1df9b-288">Viene arrestata la registrazione di realtà mista di corrente</span><span class="sxs-lookup"><span data-stu-id="1df9b-288">Stops the current mixed reality recording</span></span>

<span data-ttu-id="1df9b-289">**/api/holographic/mrc/photo (POST)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-289">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="1df9b-290">Scatta una foto di realtà mista e crea un file nel dispositivo</span><span class="sxs-lookup"><span data-stu-id="1df9b-290">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="1df9b-291">Parametri</span><span class="sxs-lookup"><span data-stu-id="1df9b-291">Parameters</span></span>
* <span data-ttu-id="1df9b-292">holo: acquisire vntana: true o false</span><span class="sxs-lookup"><span data-stu-id="1df9b-292">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="1df9b-293">PV: acquisizione PV fotocamera: true o false</span><span class="sxs-lookup"><span data-stu-id="1df9b-293">pv : capture PV camera: true or false</span></span>

<span data-ttu-id="1df9b-294">Realtà mista di Streaming</span><span class="sxs-lookup"><span data-stu-id="1df9b-294">Mixed Reality Streaming</span></span>

<span data-ttu-id="1df9b-295">**/api/holographic/stream/live.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-295">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="1df9b-296">Avviare un download in blocchi di un file MP4 frammentato</span><span class="sxs-lookup"><span data-stu-id="1df9b-296">Initiates a chunked download of a fragmented mp4</span></span>

<span data-ttu-id="1df9b-297">Parametri</span><span class="sxs-lookup"><span data-stu-id="1df9b-297">Parameters</span></span>
* <span data-ttu-id="1df9b-298">holo: acquisire vntana: true o false</span><span class="sxs-lookup"><span data-stu-id="1df9b-298">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="1df9b-299">PV: acquisizione PV fotocamera: true o false</span><span class="sxs-lookup"><span data-stu-id="1df9b-299">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="1df9b-300">MIC: acquisizione microfono: true o false</span><span class="sxs-lookup"><span data-stu-id="1df9b-300">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="1df9b-301">loopback: acquisizione di app audio: true o false</span><span class="sxs-lookup"><span data-stu-id="1df9b-301">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="1df9b-302">**/api/holographic/stream/live_high.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-302">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="1df9b-303">Avviare un download in blocchi di un file MP4 frammentato</span><span class="sxs-lookup"><span data-stu-id="1df9b-303">Initiates a chunked download of a fragmented mp4</span></span>

<span data-ttu-id="1df9b-304">Parametri</span><span class="sxs-lookup"><span data-stu-id="1df9b-304">Parameters</span></span>
* <span data-ttu-id="1df9b-305">holo: acquisire vntana: true o false</span><span class="sxs-lookup"><span data-stu-id="1df9b-305">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="1df9b-306">PV: acquisizione PV fotocamera: true o false</span><span class="sxs-lookup"><span data-stu-id="1df9b-306">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="1df9b-307">MIC: acquisizione microfono: true o false</span><span class="sxs-lookup"><span data-stu-id="1df9b-307">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="1df9b-308">loopback: acquisizione di app audio: true o false</span><span class="sxs-lookup"><span data-stu-id="1df9b-308">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="1df9b-309">**/api/holographic/stream/live_low.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-309">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="1df9b-310">Avviare un download in blocchi di un file MP4 frammentato</span><span class="sxs-lookup"><span data-stu-id="1df9b-310">Initiates a chunked download of a fragmented mp4</span></span>

<span data-ttu-id="1df9b-311">Parametri</span><span class="sxs-lookup"><span data-stu-id="1df9b-311">Parameters</span></span>
* <span data-ttu-id="1df9b-312">holo: acquisire vntana: true o false</span><span class="sxs-lookup"><span data-stu-id="1df9b-312">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="1df9b-313">PV: acquisizione PV fotocamera: true o false</span><span class="sxs-lookup"><span data-stu-id="1df9b-313">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="1df9b-314">MIC: acquisizione microfono: true o false</span><span class="sxs-lookup"><span data-stu-id="1df9b-314">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="1df9b-315">loopback: acquisizione di app audio: true o false</span><span class="sxs-lookup"><span data-stu-id="1df9b-315">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="1df9b-316">**/api/holographic/stream/live_med.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-316">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="1df9b-317">Avviare un download in blocchi di un file MP4 frammentato</span><span class="sxs-lookup"><span data-stu-id="1df9b-317">Initiates a chunked download of a fragmented mp4</span></span>

<span data-ttu-id="1df9b-318">Parametri</span><span class="sxs-lookup"><span data-stu-id="1df9b-318">Parameters</span></span>
* <span data-ttu-id="1df9b-319">holo: acquisire vntana: true o false</span><span class="sxs-lookup"><span data-stu-id="1df9b-319">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="1df9b-320">PV: acquisizione PV fotocamera: true o false</span><span class="sxs-lookup"><span data-stu-id="1df9b-320">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="1df9b-321">MIC: acquisizione microfono: true o false</span><span class="sxs-lookup"><span data-stu-id="1df9b-321">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="1df9b-322">loopback: acquisizione di app audio: true o false</span><span class="sxs-lookup"><span data-stu-id="1df9b-322">loopback : capture app audio: true or false</span></span>

## <a name="networking"></a><span data-ttu-id="1df9b-323">Rete</span><span class="sxs-lookup"><span data-stu-id="1df9b-323">Networking</span></span>

<span data-ttu-id="1df9b-324">**/api/networking/ipconfig (GET)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-324">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="1df9b-325">Ottiene la configurazione ip corrente</span><span class="sxs-lookup"><span data-stu-id="1df9b-325">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="1df9b-326">Informazioni del sistema operativo</span><span class="sxs-lookup"><span data-stu-id="1df9b-326">OS Information</span></span>

<span data-ttu-id="1df9b-327">**/api/os/info (GET)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-327">**/api/os/info (GET)**</span></span>

<span data-ttu-id="1df9b-328">Ottiene informazioni sul sistema operativo</span><span class="sxs-lookup"><span data-stu-id="1df9b-328">Gets operating system information</span></span>

<span data-ttu-id="1df9b-329">**/API/OS/MachineName (GET)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-329">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="1df9b-330">Ottiene il nome del computer</span><span class="sxs-lookup"><span data-stu-id="1df9b-330">Gets the machine name</span></span>

<span data-ttu-id="1df9b-331">**/api/os/machinename (POST)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-331">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="1df9b-332">Imposta il nome del computer</span><span class="sxs-lookup"><span data-stu-id="1df9b-332">Sets the machine name</span></span>

<span data-ttu-id="1df9b-333">Parametri</span><span class="sxs-lookup"><span data-stu-id="1df9b-333">Parameters</span></span>
* <span data-ttu-id="1df9b-334">nome: Nuovo nome del computer, hex64 codificato, per impostare su</span><span class="sxs-lookup"><span data-stu-id="1df9b-334">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="performance-data"></a><span data-ttu-id="1df9b-335">Dati sulle prestazioni</span><span class="sxs-lookup"><span data-stu-id="1df9b-335">Performance data</span></span>

<span data-ttu-id="1df9b-336">**/api/resourcemanager/processes (GET)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-336">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="1df9b-337">Restituisce l'elenco dei processi in esecuzione con i dettagli</span><span class="sxs-lookup"><span data-stu-id="1df9b-337">Returns the list of running processes with details</span></span>

<span data-ttu-id="1df9b-338">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="1df9b-338">Return data</span></span>
* <span data-ttu-id="1df9b-339">JSON con l'elenco di processi e i dettagli per ogni processo</span><span class="sxs-lookup"><span data-stu-id="1df9b-339">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="1df9b-340">**/api/resourcemanager/systemperf (GET)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-340">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="1df9b-341">Restituisce le statistiche delle prestazioni di sistema (i/o lettura/scrittura, statistiche di memoria e così via.</span><span class="sxs-lookup"><span data-stu-id="1df9b-341">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="1df9b-342">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="1df9b-342">Return data</span></span>
* <span data-ttu-id="1df9b-343">Struttura JSON con le informazioni di sistema: CPU, GPU, memoria, rete, i/o</span><span class="sxs-lookup"><span data-stu-id="1df9b-343">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="1df9b-344">Alimentazione</span><span class="sxs-lookup"><span data-stu-id="1df9b-344">Power</span></span>

<span data-ttu-id="1df9b-345">**/api/power/battery (GET)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-345">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="1df9b-346">Ottiene lo stato della batteria corrente</span><span class="sxs-lookup"><span data-stu-id="1df9b-346">Gets the current battery state</span></span>

<span data-ttu-id="1df9b-347">**/api/power/state (GET)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-347">**/api/power/state (GET)**</span></span>

<span data-ttu-id="1df9b-348">Controlla se il sistema si trova in uno stato di basso consumo energetico</span><span class="sxs-lookup"><span data-stu-id="1df9b-348">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="1df9b-349">Controllo remoto</span><span class="sxs-lookup"><span data-stu-id="1df9b-349">Remote Control</span></span>

<span data-ttu-id="1df9b-350">**/api/control/restart (POST)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-350">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="1df9b-351">Riavvia il dispositivo di destinazione</span><span class="sxs-lookup"><span data-stu-id="1df9b-351">Restarts the target device</span></span>

<span data-ttu-id="1df9b-352">**/api/control/shutdown (POST)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-352">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="1df9b-353">Arresta il dispositivo di destinazione</span><span class="sxs-lookup"><span data-stu-id="1df9b-353">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="1df9b-354">Gestione attività</span><span class="sxs-lookup"><span data-stu-id="1df9b-354">Task Manager</span></span>

<span data-ttu-id="1df9b-355">**/api/taskmanager/app (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-355">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="1df9b-356">Arresta un'applicazione moderna</span><span class="sxs-lookup"><span data-stu-id="1df9b-356">Stops a modern app</span></span>

<span data-ttu-id="1df9b-357">Parametri</span><span class="sxs-lookup"><span data-stu-id="1df9b-357">Parameters</span></span>
* <span data-ttu-id="1df9b-358">pacchetto: Nome completo del pacchetto dell'app, hex64 con codificata</span><span class="sxs-lookup"><span data-stu-id="1df9b-358">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="1df9b-359">forcestop: Forzare tutti i processi da arrestare (= Sì)</span><span class="sxs-lookup"><span data-stu-id="1df9b-359">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="1df9b-360">**/api/taskmanager/app (POST)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-360">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="1df9b-361">Avvia un'applicazione moderna</span><span class="sxs-lookup"><span data-stu-id="1df9b-361">Starts a modern app</span></span>

<span data-ttu-id="1df9b-362">Parametri</span><span class="sxs-lookup"><span data-stu-id="1df9b-362">Parameters</span></span>
* <span data-ttu-id="1df9b-363">ID applicazione: Con codifica hex64 PRAID dell'app per iniziare,</span><span class="sxs-lookup"><span data-stu-id="1df9b-363">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="1df9b-364">pacchetto: Nome completo del pacchetto dell'app, hex64 con codificata</span><span class="sxs-lookup"><span data-stu-id="1df9b-364">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="1df9b-365">Gestione connessione Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="1df9b-365">WiFi Management</span></span>

<span data-ttu-id="1df9b-366">**/API/WiFi/Interfaces (GET)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-366">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="1df9b-367">Enumera le interfacce di rete wireless</span><span class="sxs-lookup"><span data-stu-id="1df9b-367">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="1df9b-368">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="1df9b-368">Return data</span></span>
* <span data-ttu-id="1df9b-369">Elenco di interfacce senza fili con i dettagli (GUID, description e così via).</span><span class="sxs-lookup"><span data-stu-id="1df9b-369">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="1df9b-370">**/api/wifi/network (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-370">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="1df9b-371">Elimina un profilo associato a una rete in un'interfaccia specificata</span><span class="sxs-lookup"><span data-stu-id="1df9b-371">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="1df9b-372">Parametri</span><span class="sxs-lookup"><span data-stu-id="1df9b-372">Parameters</span></span>
* <span data-ttu-id="1df9b-373">interfaccia: guid dell'interfaccia di rete</span><span class="sxs-lookup"><span data-stu-id="1df9b-373">interface : network interface guid</span></span>
* <span data-ttu-id="1df9b-374">profilo: nome del profilo</span><span class="sxs-lookup"><span data-stu-id="1df9b-374">profile : profile name</span></span>

<span data-ttu-id="1df9b-375">**/api/wifi/networks (GET)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-375">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="1df9b-376">Enumera le reti wireless nell'interfaccia di rete specificato</span><span class="sxs-lookup"><span data-stu-id="1df9b-376">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="1df9b-377">Parametri</span><span class="sxs-lookup"><span data-stu-id="1df9b-377">Parameters</span></span>
* <span data-ttu-id="1df9b-378">interfaccia: guid dell'interfaccia di rete</span><span class="sxs-lookup"><span data-stu-id="1df9b-378">interface : network interface guid</span></span>

<span data-ttu-id="1df9b-379">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="1df9b-379">Return data</span></span>
* <span data-ttu-id="1df9b-380">Elenco delle reti wireless disponibili nell'interfaccia di rete con i dettagli</span><span class="sxs-lookup"><span data-stu-id="1df9b-380">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="1df9b-381">**/api/wifi/network (POST)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-381">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="1df9b-382">Si connette o disconnette a una rete nell'interfaccia specificata</span><span class="sxs-lookup"><span data-stu-id="1df9b-382">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="1df9b-383">Parametri</span><span class="sxs-lookup"><span data-stu-id="1df9b-383">Parameters</span></span>
* <span data-ttu-id="1df9b-384">interfaccia: guid dell'interfaccia di rete</span><span class="sxs-lookup"><span data-stu-id="1df9b-384">interface : network interface guid</span></span>
* <span data-ttu-id="1df9b-385">SSID: ssid, hex64 codificato, per connettersi a</span><span class="sxs-lookup"><span data-stu-id="1df9b-385">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="1df9b-386">Op: connettere o disconnettere</span><span class="sxs-lookup"><span data-stu-id="1df9b-386">op : connect or disconnect</span></span>
* <span data-ttu-id="1df9b-387">createprofile: yes o no</span><span class="sxs-lookup"><span data-stu-id="1df9b-387">createprofile : yes or no</span></span>
* <span data-ttu-id="1df9b-388">chiave: hex64, chiave condivisa con codificata</span><span class="sxs-lookup"><span data-stu-id="1df9b-388">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="1df9b-389">Registrazione prestazioni Windows</span><span class="sxs-lookup"><span data-stu-id="1df9b-389">Windows Performance Recorder</span></span>

<span data-ttu-id="1df9b-390">**/api/wpr/customtrace (POST)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-390">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="1df9b-391">Carica un profilo WPR e inizia la tracciatura utilizzando il profilo caricato.</span><span class="sxs-lookup"><span data-stu-id="1df9b-391">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="1df9b-392">payload</span><span class="sxs-lookup"><span data-stu-id="1df9b-392">Payload</span></span>
* <span data-ttu-id="1df9b-393">più parti corpo http conforme</span><span class="sxs-lookup"><span data-stu-id="1df9b-393">multi-part conforming http body</span></span>

<span data-ttu-id="1df9b-394">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="1df9b-394">Return data</span></span>
* <span data-ttu-id="1df9b-395">Restituisce lo stato di sessione WPR.</span><span class="sxs-lookup"><span data-stu-id="1df9b-395">Returns the WPR session status.</span></span>

<span data-ttu-id="1df9b-396">**/api/wpr/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-396">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="1df9b-397">Recupera lo stato della sessione WPR</span><span class="sxs-lookup"><span data-stu-id="1df9b-397">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="1df9b-398">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="1df9b-398">Return data</span></span>
* <span data-ttu-id="1df9b-399">Stato della sessione WPR.</span><span class="sxs-lookup"><span data-stu-id="1df9b-399">WPR session status.</span></span>

<span data-ttu-id="1df9b-400">**/api/wpr/trace (GET)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-400">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="1df9b-401">Arresta una sessione di traccia WPR (prestazioni)</span><span class="sxs-lookup"><span data-stu-id="1df9b-401">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="1df9b-402">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="1df9b-402">Return data</span></span>
* <span data-ttu-id="1df9b-403">Restituisce il file ETL di traccia</span><span class="sxs-lookup"><span data-stu-id="1df9b-403">Returns the trace ETL file</span></span>

<span data-ttu-id="1df9b-404">**/api/wpr/trace (POST)**</span><span class="sxs-lookup"><span data-stu-id="1df9b-404">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="1df9b-405">Avvia una traccia di sessioni WPR (prestazioni)</span><span class="sxs-lookup"><span data-stu-id="1df9b-405">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="1df9b-406">Parametri</span><span class="sxs-lookup"><span data-stu-id="1df9b-406">Parameters</span></span>
* <span data-ttu-id="1df9b-407">profilo: Nome del profilo.</span><span class="sxs-lookup"><span data-stu-id="1df9b-407">profile : Profile name.</span></span> <span data-ttu-id="1df9b-408">Profili disponibili vengono archiviati in perfprofiles/profiles.json</span><span class="sxs-lookup"><span data-stu-id="1df9b-408">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="1df9b-409">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="1df9b-409">Return data</span></span>
* <span data-ttu-id="1df9b-410">Nel menu start, restituisce lo stato di sessione WPR.</span><span class="sxs-lookup"><span data-stu-id="1df9b-410">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="1df9b-411">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1df9b-411">See also</span></span>
* [<span data-ttu-id="1df9b-412">Utilizzando il Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="1df9b-412">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="1df9b-413">Core portale dispositivo API reference (UWP)</span><span class="sxs-lookup"><span data-stu-id="1df9b-413">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)

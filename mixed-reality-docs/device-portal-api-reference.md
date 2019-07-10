---
title: Portale del dispositivo di riferimento all'API
description: Riferimento API per il Windows Device Portal in HoloLens
author: JonMLyons
ms.author: JLyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, Windows Device Portal, API
ms.openlocfilehash: 4b5b48c13b1b7ec8bfdf447f42097a8448b6a0e6
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694439"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="56f6b-104">Portale del dispositivo di riferimento all'API</span><span class="sxs-lookup"><span data-stu-id="56f6b-104">Device portal API reference</span></span>

<span data-ttu-id="56f6b-105">Tutti gli elementi di [Windows Device Portal](using-the-windows-device-portal.md) si basa sull'API REST che è possibile usare per accedere ai dati e controllare il dispositivo a livello di codice.</span><span class="sxs-lookup"><span data-stu-id="56f6b-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="56f6b-106">Distribuzione di App</span><span class="sxs-lookup"><span data-stu-id="56f6b-106">App deloyment</span></span>

<span data-ttu-id="56f6b-107">**/API/App/packagemanager/package (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="56f6b-108">Disinstalla un'app</span><span class="sxs-lookup"><span data-stu-id="56f6b-108">Uninstalls an app</span></span>

<span data-ttu-id="56f6b-109">Parametri</span><span class="sxs-lookup"><span data-stu-id="56f6b-109">Parameters</span></span>
* <span data-ttu-id="56f6b-110">pacchetto: Nome del file del pacchetto da disinstallare.</span><span class="sxs-lookup"><span data-stu-id="56f6b-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="56f6b-111">**/api/app/packagemanager/package (POST)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="56f6b-112">Installa un'App</span><span class="sxs-lookup"><span data-stu-id="56f6b-112">Installs an App</span></span>

<span data-ttu-id="56f6b-113">Parametri</span><span class="sxs-lookup"><span data-stu-id="56f6b-113">Parameters</span></span>
* <span data-ttu-id="56f6b-114">pacchetto: Nome del file del pacchetto da installare.</span><span class="sxs-lookup"><span data-stu-id="56f6b-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="56f6b-115">payload</span><span class="sxs-lookup"><span data-stu-id="56f6b-115">Payload</span></span>
* <span data-ttu-id="56f6b-116">più parti corpo http conforme</span><span class="sxs-lookup"><span data-stu-id="56f6b-116">multi-part conforming http body</span></span>

<span data-ttu-id="56f6b-117">**/api/app/packagemanager/packages (GET)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="56f6b-118">Recupera l'elenco delle App installate nel sistema, con dettagli</span><span class="sxs-lookup"><span data-stu-id="56f6b-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="56f6b-119">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="56f6b-119">Return data</span></span>
* <span data-ttu-id="56f6b-120">Elenco dei pacchetti installati con i dettagli</span><span class="sxs-lookup"><span data-stu-id="56f6b-120">List of installed packages with details</span></span>

<span data-ttu-id="56f6b-121">**/api/app/packagemanager/state (GET)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="56f6b-122">Ottiene lo stato dell'installazione dell'app lo stato di avanzamento</span><span class="sxs-lookup"><span data-stu-id="56f6b-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="56f6b-123">Raccolta dei dump</span><span class="sxs-lookup"><span data-stu-id="56f6b-123">Dump collection</span></span>

<span data-ttu-id="56f6b-124">**/API/debug/dump/usermode/CrashControl (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="56f6b-125">Disabilita l'arresto anomalo del sistema di raccolta dei dump per un'app con sideload</span><span class="sxs-lookup"><span data-stu-id="56f6b-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="56f6b-126">Parametri</span><span class="sxs-lookup"><span data-stu-id="56f6b-126">Parameters</span></span>
* <span data-ttu-id="56f6b-127">packageFullname: nome del pacchetto</span><span class="sxs-lookup"><span data-stu-id="56f6b-127">packageFullname : package name</span></span>

<span data-ttu-id="56f6b-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="56f6b-129">Ottiene le impostazioni per le app con sideload raccolta dei dump di arresto anomalo del sistema</span><span class="sxs-lookup"><span data-stu-id="56f6b-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="56f6b-130">Parametri</span><span class="sxs-lookup"><span data-stu-id="56f6b-130">Parameters</span></span>
* <span data-ttu-id="56f6b-131">packageFullname: nome del pacchetto</span><span class="sxs-lookup"><span data-stu-id="56f6b-131">packageFullname : package name</span></span>

<span data-ttu-id="56f6b-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="56f6b-133">Attiva e configura le impostazioni di controllo di dump per un'app con sideload</span><span class="sxs-lookup"><span data-stu-id="56f6b-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="56f6b-134">Parametri</span><span class="sxs-lookup"><span data-stu-id="56f6b-134">Parameters</span></span>
* <span data-ttu-id="56f6b-135">packageFullname: nome del pacchetto</span><span class="sxs-lookup"><span data-stu-id="56f6b-135">packageFullname : package name</span></span>

<span data-ttu-id="56f6b-136">**/API/debug/dump/usermode/crashdump (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="56f6b-137">Elimina un dump di arresto anomalo del sistema per un'app con sideload</span><span class="sxs-lookup"><span data-stu-id="56f6b-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="56f6b-138">Parametri</span><span class="sxs-lookup"><span data-stu-id="56f6b-138">Parameters</span></span>
* <span data-ttu-id="56f6b-139">packageFullname: nome del pacchetto</span><span class="sxs-lookup"><span data-stu-id="56f6b-139">packageFullname : package name</span></span>
* <span data-ttu-id="56f6b-140">nome file: nome del file dump</span><span class="sxs-lookup"><span data-stu-id="56f6b-140">fileName : dump file name</span></span>

<span data-ttu-id="56f6b-141">**/api/debug/dump/usermode/crashdump (GET)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="56f6b-142">Recupera un dump di arresto anomalo del sistema per un'app con sideload</span><span class="sxs-lookup"><span data-stu-id="56f6b-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="56f6b-143">Parametri</span><span class="sxs-lookup"><span data-stu-id="56f6b-143">Parameters</span></span>
* <span data-ttu-id="56f6b-144">packageFullname: nome del pacchetto</span><span class="sxs-lookup"><span data-stu-id="56f6b-144">packageFullname : package name</span></span>
* <span data-ttu-id="56f6b-145">nome file: nome del file dump</span><span class="sxs-lookup"><span data-stu-id="56f6b-145">fileName : dump file name</span></span>

<span data-ttu-id="56f6b-146">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="56f6b-146">Return data</span></span>
* <span data-ttu-id="56f6b-147">File di dump.</span><span class="sxs-lookup"><span data-stu-id="56f6b-147">Dump file.</span></span> <span data-ttu-id="56f6b-148">Controllare con WinDbg o di Visual Studio</span><span class="sxs-lookup"><span data-stu-id="56f6b-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="56f6b-149">**/api/debug/dump/usermode/dumps (GET)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="56f6b-150">Restituisce un elenco di tutti i dettagli di arresto anomalo per le app con sideload</span><span class="sxs-lookup"><span data-stu-id="56f6b-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="56f6b-151">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="56f6b-151">Return data</span></span>
* <span data-ttu-id="56f6b-152">Elenco di arresto anomalo del sistema esegue il dump per ogni app caricata lato</span><span class="sxs-lookup"><span data-stu-id="56f6b-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="56f6b-153">ETW</span><span class="sxs-lookup"><span data-stu-id="56f6b-153">ETW</span></span>

<span data-ttu-id="56f6b-154">**/api/etw/providers (GET)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="56f6b-155">Enumera i provider registrati</span><span class="sxs-lookup"><span data-stu-id="56f6b-155">Enumerates registered providers</span></span>

<span data-ttu-id="56f6b-156">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="56f6b-156">Return data</span></span>
* <span data-ttu-id="56f6b-157">Elenco dei provider, nome descrittivo e GUID</span><span class="sxs-lookup"><span data-stu-id="56f6b-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="56f6b-158">**/api/etw/session/realtime (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="56f6b-159">Crea una sessione ETW in tempo reale. gestita su un websocket.</span><span class="sxs-lookup"><span data-stu-id="56f6b-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="56f6b-160">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="56f6b-160">Return data</span></span>
* <span data-ttu-id="56f6b-161">Eventi ETW da provider attivati</span><span class="sxs-lookup"><span data-stu-id="56f6b-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="56f6b-162">Sistema operativo olografico</span><span class="sxs-lookup"><span data-stu-id="56f6b-162">Holographic OS</span></span>

<span data-ttu-id="56f6b-163">**/api/holographic/os/etw/customproviders (GET)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="56f6b-164">Restituisce un elenco di provider ETW specifico HoloLens che non sono registrati con il sistema</span><span class="sxs-lookup"><span data-stu-id="56f6b-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="56f6b-165">**/api/holographic/os/services (GET)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="56f6b-166">Restituisce gli stati di tutti i servizi in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="56f6b-166">Returns the states of all services running.</span></span>

<span data-ttu-id="56f6b-167">**/api/holographic/os/settings/ipd (GET)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="56f6b-168">Ottiene il IPD stored (Interpupillary distanza) in millimetri</span><span class="sxs-lookup"><span data-stu-id="56f6b-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="56f6b-169">**/api/holographic/os/settings/ipd (POST)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="56f6b-170">Imposta IPD</span><span class="sxs-lookup"><span data-stu-id="56f6b-170">Sets the IPD</span></span>

<span data-ttu-id="56f6b-171">Parametri</span><span class="sxs-lookup"><span data-stu-id="56f6b-171">Parameters</span></span>
* <span data-ttu-id="56f6b-172">IPD: Nuovo valore IPD vengano impostati in millimetri</span><span class="sxs-lookup"><span data-stu-id="56f6b-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="56f6b-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="56f6b-174">Ottenere richieste HTTPS per Device Portal</span><span class="sxs-lookup"><span data-stu-id="56f6b-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="56f6b-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="56f6b-176">Imposta i requisiti di HTTPS per il portale del dispositivo</span><span class="sxs-lookup"><span data-stu-id="56f6b-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="56f6b-177">Parametri</span><span class="sxs-lookup"><span data-stu-id="56f6b-177">Parameters</span></span>
* <span data-ttu-id="56f6b-178">obbligatorio: Sì, no o default</span><span class="sxs-lookup"><span data-stu-id="56f6b-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="56f6b-179">Percezione holographic</span><span class="sxs-lookup"><span data-stu-id="56f6b-179">Holographic Perception</span></span>

<span data-ttu-id="56f6b-180">**/api/holographic/perception/client (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="56f6b-181">Accetta gli aggiornamenti di websocket ed esegue un client di percezione che invia gli aggiornamenti di 30 fps.</span><span class="sxs-lookup"><span data-stu-id="56f6b-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="56f6b-182">Parametri</span><span class="sxs-lookup"><span data-stu-id="56f6b-182">Parameters</span></span>
* <span data-ttu-id="56f6b-183">clientmode: "attivo" forza la modalità di rilevamento visual quando non è possibile stabilire passivamente</span><span class="sxs-lookup"><span data-stu-id="56f6b-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="56f6b-184">Holographic termico</span><span class="sxs-lookup"><span data-stu-id="56f6b-184">Holographic Thermal</span></span>

<span data-ttu-id="56f6b-185">**/api/holographic/thermal/stage (GET)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="56f6b-186">Ottenere la fase termica del dispositivo (0 normale, 1 warm, 2 critico)</span><span class="sxs-lookup"><span data-stu-id="56f6b-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="56f6b-187">Controllo di simulazione di percezione</span><span class="sxs-lookup"><span data-stu-id="56f6b-187">Perception Simulation Control</span></span>

<span data-ttu-id="56f6b-188">**/api/holographic/simulation/control/mode (GET)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-188">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="56f6b-189">Ottenere la modalità di simulazione</span><span class="sxs-lookup"><span data-stu-id="56f6b-189">Get the simulation mode</span></span>

<span data-ttu-id="56f6b-190">**/api/holographic/simulation/control/mode (POST)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-190">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="56f6b-191">Impostare la modalità di simulazione</span><span class="sxs-lookup"><span data-stu-id="56f6b-191">Set the simulation mode</span></span>

<span data-ttu-id="56f6b-192">Parametri</span><span class="sxs-lookup"><span data-stu-id="56f6b-192">Parameters</span></span>
* <span data-ttu-id="56f6b-193">modalità: modalità di simulazione: predefinito, simulazione, remote, legacy</span><span class="sxs-lookup"><span data-stu-id="56f6b-193">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="56f6b-194">**/API/holographic/Simulation/Control/Stream (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-194">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="56f6b-195">Eliminare un flusso di controllo.</span><span class="sxs-lookup"><span data-stu-id="56f6b-195">Delete a control stream.</span></span>

<span data-ttu-id="56f6b-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="56f6b-197">Aprire una connessione web socket per un flusso di controllo.</span><span class="sxs-lookup"><span data-stu-id="56f6b-197">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="56f6b-198">**/api/holographic/simulation/control/stream (POST)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-198">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="56f6b-199">Creare un flusso di controllo (priorità è obbligatorio) o inviare i dati in un flusso creato (streamId richiesto).</span><span class="sxs-lookup"><span data-stu-id="56f6b-199">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="56f6b-200">I dati inseriti dovrebbe essere di tipo ' application/octet-stream'.</span><span class="sxs-lookup"><span data-stu-id="56f6b-200">Posted data is expected to be of type 'application/octet-stream'.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="56f6b-201">Riproduzione di simulazione di percezione</span><span class="sxs-lookup"><span data-stu-id="56f6b-201">Perception Simulation Playback</span></span>

<span data-ttu-id="56f6b-202">**/API/holographic/Simulation/Playback/file (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-202">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="56f6b-203">Eliminare una registrazione.</span><span class="sxs-lookup"><span data-stu-id="56f6b-203">Delete a recording.</span></span>

<span data-ttu-id="56f6b-204">Parametri</span><span class="sxs-lookup"><span data-stu-id="56f6b-204">Parameters</span></span>
* <span data-ttu-id="56f6b-205">la registrazione: Nome della registrazione per eliminare.</span><span class="sxs-lookup"><span data-stu-id="56f6b-205">recording : Name of recording to delete.</span></span>

<span data-ttu-id="56f6b-206">**/API/holographic/Simulation/Playback/file (POST)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-206">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="56f6b-207">Caricare una registrazione.</span><span class="sxs-lookup"><span data-stu-id="56f6b-207">Upload a recording.</span></span>

<span data-ttu-id="56f6b-208">**/API/holographic/Simulation/Playback/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-208">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="56f6b-209">Ottenere tutte le registrazioni.</span><span class="sxs-lookup"><span data-stu-id="56f6b-209">Get all recordings.</span></span>

<span data-ttu-id="56f6b-210">**/API/holographic/Simulation/Playback/Session (GET)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-210">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="56f6b-211">Ottenere lo stato corrente di riproduzione della registrazione.</span><span class="sxs-lookup"><span data-stu-id="56f6b-211">Get the current playback state of a recording.</span></span>

<span data-ttu-id="56f6b-212">Parametri</span><span class="sxs-lookup"><span data-stu-id="56f6b-212">Parameters</span></span>
* <span data-ttu-id="56f6b-213">la registrazione: Nome della registrazione.</span><span class="sxs-lookup"><span data-stu-id="56f6b-213">recording : Name of recording.</span></span>

<span data-ttu-id="56f6b-214">**/API/holographic/Simulation/Playback/Session/file (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-214">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="56f6b-215">Scaricare una registrazione.</span><span class="sxs-lookup"><span data-stu-id="56f6b-215">Unload a recording.</span></span>

<span data-ttu-id="56f6b-216">Parametri</span><span class="sxs-lookup"><span data-stu-id="56f6b-216">Parameters</span></span>
* <span data-ttu-id="56f6b-217">la registrazione: Nome della registrazione per scaricare.</span><span class="sxs-lookup"><span data-stu-id="56f6b-217">recording : Name of recording to unload.</span></span>

<span data-ttu-id="56f6b-218">**/api/holographic/simulation/playback/session/file (POST)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-218">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="56f6b-219">Caricare una registrazione.</span><span class="sxs-lookup"><span data-stu-id="56f6b-219">Load a recording.</span></span>

<span data-ttu-id="56f6b-220">Parametri</span><span class="sxs-lookup"><span data-stu-id="56f6b-220">Parameters</span></span>
* <span data-ttu-id="56f6b-221">la registrazione: Nome della registrazione per il caricamento.</span><span class="sxs-lookup"><span data-stu-id="56f6b-221">recording : Name of recording to load.</span></span>

<span data-ttu-id="56f6b-222">**/API/holographic/Simulation/Playback/Session/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-222">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="56f6b-223">Ottenere registrazioni tutto caricate.</span><span class="sxs-lookup"><span data-stu-id="56f6b-223">Get all loaded recordings.</span></span>

<span data-ttu-id="56f6b-224">**/API/holographic/Simulation/Playback/Session/pause (POST)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-224">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="56f6b-225">Sospendere la registrazione.</span><span class="sxs-lookup"><span data-stu-id="56f6b-225">Pause a recording.</span></span>

<span data-ttu-id="56f6b-226">Parametri</span><span class="sxs-lookup"><span data-stu-id="56f6b-226">Parameters</span></span>
* <span data-ttu-id="56f6b-227">la registrazione: Nome della registrazione.</span><span class="sxs-lookup"><span data-stu-id="56f6b-227">recording : Name of recording.</span></span>

<span data-ttu-id="56f6b-228">**/API/holographic/Simulation/Playback/Session/Play (POST)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-228">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="56f6b-229">Riprodurre una registrazione.</span><span class="sxs-lookup"><span data-stu-id="56f6b-229">Play a recording.</span></span>

<span data-ttu-id="56f6b-230">Parametri</span><span class="sxs-lookup"><span data-stu-id="56f6b-230">Parameters</span></span>
* <span data-ttu-id="56f6b-231">la registrazione: Nome della registrazione.</span><span class="sxs-lookup"><span data-stu-id="56f6b-231">recording : Name of recording.</span></span>

<span data-ttu-id="56f6b-232">**/api/holographic/simulation/playback/session/stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-232">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="56f6b-233">Arrestare la registrazione.</span><span class="sxs-lookup"><span data-stu-id="56f6b-233">Stop a recording.</span></span>

<span data-ttu-id="56f6b-234">Parametri</span><span class="sxs-lookup"><span data-stu-id="56f6b-234">Parameters</span></span>
* <span data-ttu-id="56f6b-235">la registrazione: Nome della registrazione.</span><span class="sxs-lookup"><span data-stu-id="56f6b-235">recording : Name of recording.</span></span>

<span data-ttu-id="56f6b-236">**/API/holographic/Simulation/Playback/Session/Types (GET)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-236">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="56f6b-237">Ottenere i tipi di dati in una registrazione caricata.</span><span class="sxs-lookup"><span data-stu-id="56f6b-237">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="56f6b-238">Parametri</span><span class="sxs-lookup"><span data-stu-id="56f6b-238">Parameters</span></span>
* <span data-ttu-id="56f6b-239">la registrazione: Nome della registrazione.</span><span class="sxs-lookup"><span data-stu-id="56f6b-239">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="56f6b-240">Registrazione di simulazione di percezione</span><span class="sxs-lookup"><span data-stu-id="56f6b-240">Perception Simulation Recording</span></span>

<span data-ttu-id="56f6b-241">**/api/holographic/simulation/recording/start (POST)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-241">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="56f6b-242">Avviare una registrazione.</span><span class="sxs-lookup"><span data-stu-id="56f6b-242">Start a recording.</span></span> <span data-ttu-id="56f6b-243">Solo una singola registrazione può essere attiva contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="56f6b-243">Only a single recording can be active at once.</span></span> <span data-ttu-id="56f6b-244">Head, mani, spatialMapping o ambiente deve essere impostata.</span><span class="sxs-lookup"><span data-stu-id="56f6b-244">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="56f6b-245">Parametri</span><span class="sxs-lookup"><span data-stu-id="56f6b-245">Parameters</span></span>
* <span data-ttu-id="56f6b-246">Head: Impostare su 1 per registrare i dati head.</span><span class="sxs-lookup"><span data-stu-id="56f6b-246">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="56f6b-247">pratico: Impostare su 1 per registrare manualmente i dati.</span><span class="sxs-lookup"><span data-stu-id="56f6b-247">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="56f6b-248">spatialMapping: Impostare su 1 per registrare mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="56f6b-248">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="56f6b-249">ambiente: Impostare su 1 per registrare i dati di ambiente.</span><span class="sxs-lookup"><span data-stu-id="56f6b-249">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="56f6b-250">nome: Nome della registrazione.</span><span class="sxs-lookup"><span data-stu-id="56f6b-250">name : Name of the recording.</span></span>
* <span data-ttu-id="56f6b-251">singleSpatialMappingFrame: Impostare su 1 per registrare solo un frame solo mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="56f6b-251">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="56f6b-252">**/api/holographic/simulation/recording/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-252">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="56f6b-253">Ottenere la registrazione dello stato.</span><span class="sxs-lookup"><span data-stu-id="56f6b-253">Get recording state.</span></span>

<span data-ttu-id="56f6b-254">**/api/holographic/simulation/recording/stop (GET)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-254">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="56f6b-255">Arrestare la registrazione corrente.</span><span class="sxs-lookup"><span data-stu-id="56f6b-255">Stop the current recording.</span></span> <span data-ttu-id="56f6b-256">La registrazione verrà restituita come un file.</span><span class="sxs-lookup"><span data-stu-id="56f6b-256">Recording will be returned as a file.</span></span>

## <a name="mixed-reality-capture"></a><span data-ttu-id="56f6b-257">Mixed Reality Capture</span><span class="sxs-lookup"><span data-stu-id="56f6b-257">Mixed Reality Capture</span></span>

<span data-ttu-id="56f6b-258">**/api/holographic/mrc/file (GET)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-258">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="56f6b-259">Scarica un file di realtà mista dal dispositivo.</span><span class="sxs-lookup"><span data-stu-id="56f6b-259">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="56f6b-260">Op usare = parametro di query di flusso per lo streaming.</span><span class="sxs-lookup"><span data-stu-id="56f6b-260">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="56f6b-261">Parametri</span><span class="sxs-lookup"><span data-stu-id="56f6b-261">Parameters</span></span>
* <span data-ttu-id="56f6b-262">nome file: Il nome, hex64 codificato, del file video di introduzione</span><span class="sxs-lookup"><span data-stu-id="56f6b-262">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="56f6b-263">Op: flusso</span><span class="sxs-lookup"><span data-stu-id="56f6b-263">op : stream</span></span>

<span data-ttu-id="56f6b-264">**/API/holographic/MRC/file (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-264">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="56f6b-265">Elimina una realtà mista di registrazione dal dispositivo.</span><span class="sxs-lookup"><span data-stu-id="56f6b-265">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="56f6b-266">Parametri</span><span class="sxs-lookup"><span data-stu-id="56f6b-266">Parameters</span></span>
* <span data-ttu-id="56f6b-267">nome file: Il nome, hex64 codificato, del file da eliminare</span><span class="sxs-lookup"><span data-stu-id="56f6b-267">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="56f6b-268">**/API/holographic/MRC/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-268">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="56f6b-269">Restituisce l'elenco dei file di realtà mista archiviati nel dispositivo</span><span class="sxs-lookup"><span data-stu-id="56f6b-269">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="56f6b-270">**/api/holographic/mrc/photo (POST)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-270">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="56f6b-271">Scatta una foto di realtà mista e crea un file nel dispositivo</span><span class="sxs-lookup"><span data-stu-id="56f6b-271">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="56f6b-272">Parametri</span><span class="sxs-lookup"><span data-stu-id="56f6b-272">Parameters</span></span>
* <span data-ttu-id="56f6b-273">holo: acquisire vntana: true o false (valore predefinito è false)</span><span class="sxs-lookup"><span data-stu-id="56f6b-273">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="56f6b-274">PV: acquisizione PV fotocamera: true o false (valore predefinito è false)</span><span class="sxs-lookup"><span data-stu-id="56f6b-274">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="56f6b-275">RenderFromCamera : Rendering (solo 2 HoloLens) dal punto di vista della fotocamera foto/video: true o false (valore predefinito è true)</span><span class="sxs-lookup"><span data-stu-id="56f6b-275">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="56f6b-276">**/api/holographic/mrc/settings (GET)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-276">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="56f6b-277">Ottiene il valore predefinito realtà mista le impostazioni di acquisizione</span><span class="sxs-lookup"><span data-stu-id="56f6b-277">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="56f6b-278">**/api/holographic/mrc/settings (POST)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="56f6b-279">Imposta il valore predefinito realtà mista le impostazioni di acquisizione.</span><span class="sxs-lookup"><span data-stu-id="56f6b-279">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="56f6b-280">Alcune di queste impostazioni vengono applicate a photo MRC e acquisizione video del sistema.</span><span class="sxs-lookup"><span data-stu-id="56f6b-280">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="56f6b-281">**/api/holographic/mrc/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-281">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="56f6b-282">Ottiene lo stato della realtà mista registrate (in esecuzione, arrestato)</span><span class="sxs-lookup"><span data-stu-id="56f6b-282">Gets the status of the mixed reality recorded (running, stopped)</span></span>

<span data-ttu-id="56f6b-283">**/api/holographic/mrc/thumbnail (GET)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-283">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="56f6b-284">Ottiene l'immagine di anteprima per il file specificato.</span><span class="sxs-lookup"><span data-stu-id="56f6b-284">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="56f6b-285">Parametri</span><span class="sxs-lookup"><span data-stu-id="56f6b-285">Parameters</span></span>
* <span data-ttu-id="56f6b-286">nome file: Il nome, hex64 codificato, del file per cui viene richiesto l'anteprima</span><span class="sxs-lookup"><span data-stu-id="56f6b-286">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="56f6b-287">**/api/holographic/mrc/video/control/start (POST)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-287">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="56f6b-288">Avvia una registrazione di realtà mista</span><span class="sxs-lookup"><span data-stu-id="56f6b-288">Starts a mixed reality recording</span></span>

<span data-ttu-id="56f6b-289">Parametri</span><span class="sxs-lookup"><span data-stu-id="56f6b-289">Parameters</span></span>
* <span data-ttu-id="56f6b-290">holo: acquisire vntana: true o false (valore predefinito è false)</span><span class="sxs-lookup"><span data-stu-id="56f6b-290">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="56f6b-291">PV: acquisizione PV fotocamera: true o false (valore predefinito è false)</span><span class="sxs-lookup"><span data-stu-id="56f6b-291">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="56f6b-292">MIC: acquisizione microfono: true o false (valore predefinito è false)</span><span class="sxs-lookup"><span data-stu-id="56f6b-292">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="56f6b-293">loopback: acquisizione di app audio: true o false (valore predefinito è false)</span><span class="sxs-lookup"><span data-stu-id="56f6b-293">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="56f6b-294">RenderFromCamera : Rendering (solo 2 HoloLens) dal punto di vista della fotocamera foto/video: true o false (valore predefinito è true)</span><span class="sxs-lookup"><span data-stu-id="56f6b-294">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="56f6b-295">Vstab: Stabilizzazione video enable (solo 2 HoloLens): true o false (valore predefinito è true)</span><span class="sxs-lookup"><span data-stu-id="56f6b-295">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="56f6b-296">vstabbuffer: Latenza di buffer di stabilizzazione video (solo 2 HoloLens): tra 0 e 30 fotogrammi (impostazione predefinita è 15 fotogrammi)</span><span class="sxs-lookup"><span data-stu-id="56f6b-296">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="56f6b-297">**/api/holographic/mrc/video/control/stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-297">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="56f6b-298">Viene arrestata la registrazione di realtà mista di corrente</span><span class="sxs-lookup"><span data-stu-id="56f6b-298">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="56f6b-299">Realtà mista di Streaming</span><span class="sxs-lookup"><span data-stu-id="56f6b-299">Mixed Reality Streaming</span></span>

<span data-ttu-id="56f6b-300">HoloLens supporta l'anteprima in tempo reale di realtà mista tramite download in blocchi di un file mp4 frammentato.</span><span class="sxs-lookup"><span data-stu-id="56f6b-300">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="56f6b-301">I flussi di realtà mista condividono lo stesso set di parametri per controllare ciò che viene acquisita:</span><span class="sxs-lookup"><span data-stu-id="56f6b-301">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="56f6b-302">holo: acquisire vntana: true o false</span><span class="sxs-lookup"><span data-stu-id="56f6b-302">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="56f6b-303">PV: acquisizione PV fotocamera: true o false</span><span class="sxs-lookup"><span data-stu-id="56f6b-303">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="56f6b-304">MIC: acquisizione microfono: true o false</span><span class="sxs-lookup"><span data-stu-id="56f6b-304">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="56f6b-305">loopback: acquisizione di app audio: true o false</span><span class="sxs-lookup"><span data-stu-id="56f6b-305">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="56f6b-306">Se è stato specificato nessuno di questi elementi: vntana, fotocamera foto/video e audio app verranno acquisite</span><span class="sxs-lookup"><span data-stu-id="56f6b-306">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="56f6b-307">Se viene specificato uno: i parametri non specificati per impostazione predefinita saranno false</span><span class="sxs-lookup"><span data-stu-id="56f6b-307">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="56f6b-308">Parametri facoltativi (solo 2 HoloLens)</span><span class="sxs-lookup"><span data-stu-id="56f6b-308">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="56f6b-309">RenderFromCamera: eseguire il rendering dal punto di vista della fotocamera foto/video: true o false (valore predefinito è true)</span><span class="sxs-lookup"><span data-stu-id="56f6b-309">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="56f6b-310">Vstab: abilitare la stabilizzazione video: true o false (valore predefinito è false)</span><span class="sxs-lookup"><span data-stu-id="56f6b-310">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="56f6b-311">vstabbuffer: latenza di buffer di stabilizzazione video: tra 0 e 30 fotogrammi (impostazione predefinita è 15 fotogrammi)</span><span class="sxs-lookup"><span data-stu-id="56f6b-311">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="56f6b-312">**/api/holographic/stream/live.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-312">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="56f6b-313">Un flusso di 5Mbit 1280x720p 30fps.</span><span class="sxs-lookup"><span data-stu-id="56f6b-313">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="56f6b-314">**/api/holographic/stream/live_high.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-314">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="56f6b-315">Un flusso di 5Mbit 1280x720p 30fps.</span><span class="sxs-lookup"><span data-stu-id="56f6b-315">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="56f6b-316">**/api/holographic/stream/live_med.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-316">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="56f6b-317">Un flusso di 30fps 2.5Mbit 854x480p.</span><span class="sxs-lookup"><span data-stu-id="56f6b-317">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="56f6b-318">**/api/holographic/stream/live_low.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-318">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="56f6b-319">Un flusso di 15fps 0.6Mbit 428x240p.</span><span class="sxs-lookup"><span data-stu-id="56f6b-319">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="56f6b-320">Rete</span><span class="sxs-lookup"><span data-stu-id="56f6b-320">Networking</span></span>

<span data-ttu-id="56f6b-321">**/api/networking/ipconfig (GET)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-321">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="56f6b-322">Ottiene la configurazione ip corrente</span><span class="sxs-lookup"><span data-stu-id="56f6b-322">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="56f6b-323">Informazioni del sistema operativo</span><span class="sxs-lookup"><span data-stu-id="56f6b-323">OS Information</span></span>

<span data-ttu-id="56f6b-324">**/api/os/info (GET)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-324">**/api/os/info (GET)**</span></span>

<span data-ttu-id="56f6b-325">Ottiene informazioni sul sistema operativo</span><span class="sxs-lookup"><span data-stu-id="56f6b-325">Gets operating system information</span></span>

<span data-ttu-id="56f6b-326">**/API/OS/MachineName (GET)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-326">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="56f6b-327">Ottiene il nome del computer</span><span class="sxs-lookup"><span data-stu-id="56f6b-327">Gets the machine name</span></span>

<span data-ttu-id="56f6b-328">**/api/os/machinename (POST)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-328">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="56f6b-329">Imposta il nome del computer</span><span class="sxs-lookup"><span data-stu-id="56f6b-329">Sets the machine name</span></span>

<span data-ttu-id="56f6b-330">Parametri</span><span class="sxs-lookup"><span data-stu-id="56f6b-330">Parameters</span></span>
* <span data-ttu-id="56f6b-331">nome: Nuovo nome del computer, hex64 codificato, per impostare su</span><span class="sxs-lookup"><span data-stu-id="56f6b-331">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="performance-data"></a><span data-ttu-id="56f6b-332">Dati sulle prestazioni</span><span class="sxs-lookup"><span data-stu-id="56f6b-332">Performance data</span></span>

<span data-ttu-id="56f6b-333">**/api/resourcemanager/processes (GET)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-333">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="56f6b-334">Restituisce l'elenco dei processi in esecuzione con i dettagli</span><span class="sxs-lookup"><span data-stu-id="56f6b-334">Returns the list of running processes with details</span></span>

<span data-ttu-id="56f6b-335">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="56f6b-335">Return data</span></span>
* <span data-ttu-id="56f6b-336">JSON con l'elenco di processi e i dettagli per ogni processo</span><span class="sxs-lookup"><span data-stu-id="56f6b-336">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="56f6b-337">**/api/resourcemanager/systemperf (GET)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-337">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="56f6b-338">Restituisce le statistiche delle prestazioni di sistema (i/o lettura/scrittura, statistiche di memoria e così via.</span><span class="sxs-lookup"><span data-stu-id="56f6b-338">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="56f6b-339">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="56f6b-339">Return data</span></span>
* <span data-ttu-id="56f6b-340">Struttura JSON con le informazioni di sistema: CPU, GPU, memoria, rete, i/o</span><span class="sxs-lookup"><span data-stu-id="56f6b-340">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="56f6b-341">Alimentazione</span><span class="sxs-lookup"><span data-stu-id="56f6b-341">Power</span></span>

<span data-ttu-id="56f6b-342">**/api/power/battery (GET)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-342">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="56f6b-343">Ottiene lo stato della batteria corrente</span><span class="sxs-lookup"><span data-stu-id="56f6b-343">Gets the current battery state</span></span>

<span data-ttu-id="56f6b-344">**/api/power/state (GET)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-344">**/api/power/state (GET)**</span></span>

<span data-ttu-id="56f6b-345">Controlla se il sistema si trova in uno stato di basso consumo energetico</span><span class="sxs-lookup"><span data-stu-id="56f6b-345">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="56f6b-346">Controllo remoto</span><span class="sxs-lookup"><span data-stu-id="56f6b-346">Remote Control</span></span>

<span data-ttu-id="56f6b-347">**/api/control/restart (POST)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-347">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="56f6b-348">Riavvia il dispositivo di destinazione</span><span class="sxs-lookup"><span data-stu-id="56f6b-348">Restarts the target device</span></span>

<span data-ttu-id="56f6b-349">**/api/control/shutdown (POST)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-349">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="56f6b-350">Arresta il dispositivo di destinazione</span><span class="sxs-lookup"><span data-stu-id="56f6b-350">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="56f6b-351">Gestione attività</span><span class="sxs-lookup"><span data-stu-id="56f6b-351">Task Manager</span></span>

<span data-ttu-id="56f6b-352">**/api/taskmanager/app (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-352">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="56f6b-353">Arresta un'applicazione moderna</span><span class="sxs-lookup"><span data-stu-id="56f6b-353">Stops a modern app</span></span>

<span data-ttu-id="56f6b-354">Parametri</span><span class="sxs-lookup"><span data-stu-id="56f6b-354">Parameters</span></span>
* <span data-ttu-id="56f6b-355">pacchetto: Nome completo del pacchetto dell'app, hex64 con codificata</span><span class="sxs-lookup"><span data-stu-id="56f6b-355">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="56f6b-356">forcestop: Forzare tutti i processi da arrestare (= Sì)</span><span class="sxs-lookup"><span data-stu-id="56f6b-356">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="56f6b-357">**/api/taskmanager/app (POST)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-357">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="56f6b-358">Avvia un'applicazione moderna</span><span class="sxs-lookup"><span data-stu-id="56f6b-358">Starts a modern app</span></span>

<span data-ttu-id="56f6b-359">Parametri</span><span class="sxs-lookup"><span data-stu-id="56f6b-359">Parameters</span></span>
* <span data-ttu-id="56f6b-360">ID applicazione: Con codifica hex64 PRAID dell'app per iniziare,</span><span class="sxs-lookup"><span data-stu-id="56f6b-360">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="56f6b-361">pacchetto: Nome completo del pacchetto dell'app, hex64 con codificata</span><span class="sxs-lookup"><span data-stu-id="56f6b-361">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="56f6b-362">Gestione connessione Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="56f6b-362">WiFi Management</span></span>

<span data-ttu-id="56f6b-363">**/API/WiFi/Interfaces (GET)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-363">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="56f6b-364">Enumera le interfacce di rete wireless</span><span class="sxs-lookup"><span data-stu-id="56f6b-364">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="56f6b-365">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="56f6b-365">Return data</span></span>
* <span data-ttu-id="56f6b-366">Elenco di interfacce senza fili con i dettagli (GUID, description e così via).</span><span class="sxs-lookup"><span data-stu-id="56f6b-366">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="56f6b-367">**/api/wifi/network (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-367">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="56f6b-368">Elimina un profilo associato a una rete in un'interfaccia specificata</span><span class="sxs-lookup"><span data-stu-id="56f6b-368">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="56f6b-369">Parametri</span><span class="sxs-lookup"><span data-stu-id="56f6b-369">Parameters</span></span>
* <span data-ttu-id="56f6b-370">interfaccia: guid dell'interfaccia di rete</span><span class="sxs-lookup"><span data-stu-id="56f6b-370">interface : network interface guid</span></span>
* <span data-ttu-id="56f6b-371">profilo: nome del profilo</span><span class="sxs-lookup"><span data-stu-id="56f6b-371">profile : profile name</span></span>

<span data-ttu-id="56f6b-372">**/api/wifi/networks (GET)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-372">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="56f6b-373">Enumera le reti wireless nell'interfaccia di rete specificato</span><span class="sxs-lookup"><span data-stu-id="56f6b-373">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="56f6b-374">Parametri</span><span class="sxs-lookup"><span data-stu-id="56f6b-374">Parameters</span></span>
* <span data-ttu-id="56f6b-375">interfaccia: guid dell'interfaccia di rete</span><span class="sxs-lookup"><span data-stu-id="56f6b-375">interface : network interface guid</span></span>

<span data-ttu-id="56f6b-376">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="56f6b-376">Return data</span></span>
* <span data-ttu-id="56f6b-377">Elenco delle reti wireless disponibili nell'interfaccia di rete con i dettagli</span><span class="sxs-lookup"><span data-stu-id="56f6b-377">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="56f6b-378">**/api/wifi/network (POST)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-378">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="56f6b-379">Si connette o disconnette a una rete nell'interfaccia specificata</span><span class="sxs-lookup"><span data-stu-id="56f6b-379">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="56f6b-380">Parametri</span><span class="sxs-lookup"><span data-stu-id="56f6b-380">Parameters</span></span>
* <span data-ttu-id="56f6b-381">interfaccia: guid dell'interfaccia di rete</span><span class="sxs-lookup"><span data-stu-id="56f6b-381">interface : network interface guid</span></span>
* <span data-ttu-id="56f6b-382">SSID: ssid, hex64 codificato, per connettersi a</span><span class="sxs-lookup"><span data-stu-id="56f6b-382">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="56f6b-383">Op: connettere o disconnettere</span><span class="sxs-lookup"><span data-stu-id="56f6b-383">op : connect or disconnect</span></span>
* <span data-ttu-id="56f6b-384">createprofile: yes o no</span><span class="sxs-lookup"><span data-stu-id="56f6b-384">createprofile : yes or no</span></span>
* <span data-ttu-id="56f6b-385">chiave: hex64, chiave condivisa con codificata</span><span class="sxs-lookup"><span data-stu-id="56f6b-385">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="56f6b-386">Registrazione prestazioni Windows</span><span class="sxs-lookup"><span data-stu-id="56f6b-386">Windows Performance Recorder</span></span>

<span data-ttu-id="56f6b-387">**/api/wpr/customtrace (POST)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-387">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="56f6b-388">Carica un profilo WPR e inizia la tracciatura utilizzando il profilo caricato.</span><span class="sxs-lookup"><span data-stu-id="56f6b-388">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="56f6b-389">payload</span><span class="sxs-lookup"><span data-stu-id="56f6b-389">Payload</span></span>
* <span data-ttu-id="56f6b-390">più parti corpo http conforme</span><span class="sxs-lookup"><span data-stu-id="56f6b-390">multi-part conforming http body</span></span>

<span data-ttu-id="56f6b-391">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="56f6b-391">Return data</span></span>
* <span data-ttu-id="56f6b-392">Restituisce lo stato di sessione WPR.</span><span class="sxs-lookup"><span data-stu-id="56f6b-392">Returns the WPR session status.</span></span>

<span data-ttu-id="56f6b-393">**/api/wpr/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-393">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="56f6b-394">Recupera lo stato della sessione WPR</span><span class="sxs-lookup"><span data-stu-id="56f6b-394">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="56f6b-395">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="56f6b-395">Return data</span></span>
* <span data-ttu-id="56f6b-396">Stato della sessione WPR.</span><span class="sxs-lookup"><span data-stu-id="56f6b-396">WPR session status.</span></span>

<span data-ttu-id="56f6b-397">**/api/wpr/trace (GET)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-397">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="56f6b-398">Arresta una sessione di traccia WPR (prestazioni)</span><span class="sxs-lookup"><span data-stu-id="56f6b-398">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="56f6b-399">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="56f6b-399">Return data</span></span>
* <span data-ttu-id="56f6b-400">Restituisce il file ETL di traccia</span><span class="sxs-lookup"><span data-stu-id="56f6b-400">Returns the trace ETL file</span></span>

<span data-ttu-id="56f6b-401">**/api/wpr/trace (POST)**</span><span class="sxs-lookup"><span data-stu-id="56f6b-401">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="56f6b-402">Avvia una traccia di sessioni WPR (prestazioni)</span><span class="sxs-lookup"><span data-stu-id="56f6b-402">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="56f6b-403">Parametri</span><span class="sxs-lookup"><span data-stu-id="56f6b-403">Parameters</span></span>
* <span data-ttu-id="56f6b-404">profilo: Nome del profilo.</span><span class="sxs-lookup"><span data-stu-id="56f6b-404">profile : Profile name.</span></span> <span data-ttu-id="56f6b-405">Profili disponibili vengono archiviati in perfprofiles/profiles.json</span><span class="sxs-lookup"><span data-stu-id="56f6b-405">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="56f6b-406">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="56f6b-406">Return data</span></span>
* <span data-ttu-id="56f6b-407">Nel menu start, restituisce lo stato di sessione WPR.</span><span class="sxs-lookup"><span data-stu-id="56f6b-407">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="56f6b-408">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="56f6b-408">See also</span></span>
* [<span data-ttu-id="56f6b-409">Avviare il Portale di dispositivi di Windows</span><span class="sxs-lookup"><span data-stu-id="56f6b-409">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="56f6b-410">Core portale dispositivo API reference (UWP)</span><span class="sxs-lookup"><span data-stu-id="56f6b-410">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)

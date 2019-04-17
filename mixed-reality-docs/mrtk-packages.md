---
title: Pacchetti MRTK
description: Questo articolo descrive i pacchetti che costituiscono il Toollkit di realtà mista di Microsoft.
author: davidkline-ms
ms.author: davidkl
ms.date: 02/12/19
ms.topic: article
keywords: Realtà mista di Windows, MRTK, componente, pacchetto
ms.openlocfilehash: 7e44d75e1c267cff0ba67dd86dabfaa51bce659d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604640"
---
# <a name="mrtk-packages"></a><span data-ttu-id="469ef-104">Pacchetti MRTK</span><span class="sxs-lookup"><span data-stu-id="469ef-104">MRTK packages</span></span>

<span data-ttu-id="469ef-105">Il Toolkit di realtà mista (MRTK) è una raccolta di pacchetti che consentono lo sviluppo di applicazioni di realtà mista cross-platform fornendo il supporto per l'hardware di realtà mista e piattaforme in modo strutturata in componenti.</span><span class="sxs-lookup"><span data-stu-id="469ef-105">The Mixed Reality Toolkit (MRTK) is a collection of packages that enable cross platform Mixed Reality application development by providing support for Mixed Reality hardware and platforms in a componentized manner.</span></span>

<span data-ttu-id="469ef-106">Esistono tre categorie di pacchetti MRTK:</span><span class="sxs-lookup"><span data-stu-id="469ef-106">There are three categories of MRTK packages:</span></span> 

* [<span data-ttu-id="469ef-107">Foundation</span><span class="sxs-lookup"><span data-stu-id="469ef-107">Foundation</span></span>](#foundation-packages)
* [<span data-ttu-id="469ef-108">Estensione</span><span class="sxs-lookup"><span data-stu-id="469ef-108">Extension</span></span>](#extension-packages)
* [<span data-ttu-id="469ef-109">Sperimentale</span><span class="sxs-lookup"><span data-stu-id="469ef-109">Experimental</span></span>](#experimental-packages)

## <a name="foundation-packages"></a><span data-ttu-id="469ef-110">Pacchetti di base</span><span class="sxs-lookup"><span data-stu-id="469ef-110">Foundation Packages</span></span>

<span data-ttu-id="469ef-111">La base di Toolkit di realtà mista è il set di pacchetti che consentono all'applicazione di sfruttare le funzionalità comuni tra le piattaforme di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="469ef-111">The Mixed Reality Toolkit Foundation is the set of packages that enable your application to leverage common functionality across Mixed Reality Platforms.</span></span> <span data-ttu-id="469ef-112">Questi pacchetti vengono rilasciati e supportati da Microsoft dal codice sorgente nel [mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) ramo in GitHub.</span><span class="sxs-lookup"><span data-stu-id="469ef-112">These packages are released and supported by Microsoft from source code in the [mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) branch on GitHub.</span></span>

![Pacchetti Foundation MRTK](images/mrtk-foundation.jpg)

<span data-ttu-id="469ef-114">*Pacchetti Toolkit Foundation di realtà misti*</span><span class="sxs-lookup"><span data-stu-id="469ef-114">*Mixed Reality Toolkit Foundation packages*</span></span>

<span data-ttu-id="469ef-115">Le basi MRTK è costituita da:</span><span class="sxs-lookup"><span data-stu-id="469ef-115">The MRTK Foundation is comprised of:</span></span>

* [<span data-ttu-id="469ef-116">Pacchetto di base</span><span class="sxs-lookup"><span data-stu-id="469ef-116">Core Package</span></span>](#core-package)
* [<span data-ttu-id="469ef-117">Provider di piattaforma</span><span class="sxs-lookup"><span data-stu-id="469ef-117">Platform Providers</span></span>](#platform-providers)
* [<span data-ttu-id="469ef-118">Servizi di sistema</span><span class="sxs-lookup"><span data-stu-id="469ef-118">System Services</span></span>](#system-services)
* [<span data-ttu-id="469ef-119">Asset di funzionalità</span><span class="sxs-lookup"><span data-stu-id="469ef-119">Feature Assets</span></span>](#feature-assets)

<span data-ttu-id="469ef-120">Le sezioni seguenti descrivono i tipi di pacchetti in ogni categoria.</span><span class="sxs-lookup"><span data-stu-id="469ef-120">The following sections describe the types of packages in each category.</span></span>

### <a name="core-package"></a><span data-ttu-id="469ef-121">Pacchetto di base</span><span class="sxs-lookup"><span data-stu-id="469ef-121">Core Package</span></span>

<span data-ttu-id="469ef-122">Pacchetto di base è un _obbligatorio_ componente e viene eseguita come una dipendenza da tutti i pacchetti di foundation MRTK.</span><span class="sxs-lookup"><span data-stu-id="469ef-122">The core package is a _required_ component and is taken as a dependency by all MRTK foundation packages.</span></span>

<span data-ttu-id="469ef-123">Il pacchetto MRTK Core include:</span><span class="sxs-lookup"><span data-stu-id="469ef-123">The MRTK Core package includes:</span></span>

* [<span data-ttu-id="469ef-124">Tipi di interfacce, classi e dei dati comuni</span><span class="sxs-lookup"><span data-stu-id="469ef-124">Common interfaces, classes and data types</span></span>](#common-interfaces-clases-and-data-types)
* [<span data-ttu-id="469ef-125">Componente di scena MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="469ef-125">MixedRealityToolkit scene component</span></span>](#mixedrealitytoolkit-scene-component)
* [<span data-ttu-id="469ef-126">MRTK Shader Standard</span><span class="sxs-lookup"><span data-stu-id="469ef-126">MRTK Standard Shader</span></span>](#mrtk-standard-shader)
* [<span data-ttu-id="469ef-127">Provider di Input di Unity</span><span class="sxs-lookup"><span data-stu-id="469ef-127">Unity Input Provider</span></span>](#unity-input-provider)
* [<span data-ttu-id="469ef-128">Gestione dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="469ef-128">Package Management</span></span>](#package-management)

#### <a name="common-interfaces-classes-and-data-types"></a><span data-ttu-id="469ef-129">Tipi di interfacce, classi e dei dati comuni</span><span class="sxs-lookup"><span data-stu-id="469ef-129">Common interfaces, classes and data types</span></span>

<span data-ttu-id="469ef-130">Il pacchetto principale di Toolkit di realtà mista contiene le definizioni per tutte le interfacce comuni, le classi e tipi di dati usati da tutti gli altri componenti.</span><span class="sxs-lookup"><span data-stu-id="469ef-130">The Mixed Reality Toolkit Core package contains the definitions for all of the common interfaces, classes and data types that are used by all other components.</span></span> <span data-ttu-id="469ef-131">Si consiglia vivamente che le applicazioni accedono componenti MRTK esclusivamente tramite le interfacce definite per garantire il massimo livello di compatibilità tra piattaforme.</span><span class="sxs-lookup"><span data-stu-id="469ef-131">It is highly recommended that applications access MRTK components exclusively through the defined interfaces to enable the highest level of compatibility across platforms.</span></span>

#### <a name="mixedrealitytoolkit-scene-component"></a><span data-ttu-id="469ef-132">Componente di scena MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="469ef-132">MixedRealityToolkit scene component</span></span>

<span data-ttu-id="469ef-133">Il componente di scena MixedRealityToolkit è la gestione unica risorsa centralizzata per il Toolkit di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="469ef-133">The MixedRealityToolkit scene component is the single, centralized resource manager for the Mixed Reality Toolkit.</span></span> <span data-ttu-id="469ef-134">Questo componente viene caricato e gestisce il ciclo di vita dei moduli di piattaforma e il servizio e vengono fornite risorse per i sistemi accedere alle relative impostazioni di configurazione.</span><span class="sxs-lookup"><span data-stu-id="469ef-134">This component loads and manages the lifespan of the platform and service modules and provides resources for the systems to access their configuration settings.</span></span> 

#### <a name="mrtk-standard-shader"></a><span data-ttu-id="469ef-135">MRTK Shader Standard</span><span class="sxs-lookup"><span data-stu-id="469ef-135">MRTK Standard Shader</span></span>

<span data-ttu-id="469ef-136">Lo Shader Standard MRTK costituisce la base su quasi tutti i materiali forniti dal MRTK.</span><span class="sxs-lookup"><span data-stu-id="469ef-136">The MRTK Standard Shader provides the basis for virtually all of the materials provided by the MRTK.</span></span> <span data-ttu-id="469ef-137">Questo shader è estremamente flessibile e ottimizzato per la vasta gamma di piattaforme in cui MRTK è supportata.</span><span class="sxs-lookup"><span data-stu-id="469ef-137">This shader is extremely flexible and optimized for the variety of platforms on which MRTK is supported.</span></span> <span data-ttu-id="469ef-138">Si tratta _altamente_ consigliabile materiali dell'applicazione usano shader MRTK standard per ottenere prestazioni ottimali.</span><span class="sxs-lookup"><span data-stu-id="469ef-138">It is _highly_ recommended that your application's materials use the MRTK standard shader for optimal performance.</span></span>

#### <a name="unity-input-provider"></a><span data-ttu-id="469ef-139">Provider di Input di Unity</span><span class="sxs-lookup"><span data-stu-id="469ef-139">Unity Input Provider</span></span>

<span data-ttu-id="469ef-140">Il Provider di Input di Unity offre accesso ai dispositivi di input più comuni, ad esempio periferiche di gioco, touch screen e un mouse spaziale 3D.</span><span class="sxs-lookup"><span data-stu-id="469ef-140">The Unity Input Provider provides access to common input devices such as game controllers, touch screens and a 3D spatial mouse.</span></span>

#### <a name="package-management"></a><span data-ttu-id="469ef-141">Gestione dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="469ef-141">Package Management</span></span>

<span data-ttu-id="469ef-142">_Presto disponibili_</span><span class="sxs-lookup"><span data-stu-id="469ef-142">_Coming soon_</span></span>

<span data-ttu-id="469ef-143">Pacchetto di base di Toolkit di realtà mista fornisce il supporto per l'individuazione e la gestione di foundation facoltativo, estensione e pacchetti MRTK sperimentale.</span><span class="sxs-lookup"><span data-stu-id="469ef-143">The Mixed Reality Toolkit Core package provides support for discovering and managing the optional foundation, extension and experimental MRTK packages.</span></span>

### <a name="platform-providers"></a><span data-ttu-id="469ef-144">Provider di piattaforma</span><span class="sxs-lookup"><span data-stu-id="469ef-144">Platform Providers</span></span>

<span data-ttu-id="469ef-145">I pacchetti di Provider di piattaforma MRTK sono componenti che abilitano le funzionalità di piattaforma e il Toolkit di realtà mista alla destinazione dell'hardware di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="469ef-145">The MRTK Platform Provider packages are the components that enable the Mixed Reality Toolkit to target Mixed Reality hardware and platform functionality.</span></span>

<span data-ttu-id="469ef-146">Piattaforme supportate includono:</span><span class="sxs-lookup"><span data-stu-id="469ef-146">Supported platforms include:</span></span>

* [<span data-ttu-id="469ef-147">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="469ef-147">Windows Mixed Reality</span></span>](#windows-mixed-reality)
* [<span data-ttu-id="469ef-148">OpenVR</span><span class="sxs-lookup"><span data-stu-id="469ef-148">OpenVR</span></span>](#openvr)
* [<span data-ttu-id="469ef-149">Casella vocale di Windows</span><span class="sxs-lookup"><span data-stu-id="469ef-149">Windows Voice</span></span>](#windows-voice)

#### <a name="windows-mixed-reality"></a><span data-ttu-id="469ef-150">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="469ef-150">Windows Mixed Reality</span></span>

<span data-ttu-id="469ef-151">Il pacchetto di realtà mista di Windows fornisce supporto per i dispositivi Microsoft HoloLens e coinvolgenti realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="469ef-151">The Windows Mixed Reality package provides support for Microsoft HoloLens and Windows Mixed Reality Immersive devices.</span></span> <span data-ttu-id="469ef-152">Il pacchetto contiene il supporto di intera piattaforma, tra cui:</span><span class="sxs-lookup"><span data-stu-id="469ef-152">The package contains full platform support, including:</span></span>

* <span data-ttu-id="469ef-153">Sguardo targeting</span><span class="sxs-lookup"><span data-stu-id="469ef-153">Gaze targeting</span></span>
* <span data-ttu-id="469ef-154">Movimenti</span><span class="sxs-lookup"><span data-stu-id="469ef-154">Gestures</span></span>
* <span data-ttu-id="469ef-155">Controller di movimento di realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="469ef-155">Windows Mixed Reality Motion controllers</span></span>
* <span data-ttu-id="469ef-156">Mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="469ef-156">Spatial Mapping</span></span>

#### <a name="openvr"></a><span data-ttu-id="469ef-157">OpenVR</span><span class="sxs-lookup"><span data-stu-id="469ef-157">OpenVR</span></span>

<span data-ttu-id="469ef-158">Il pacchetto OpenVR fornisce supporto per i dispositivi con la piattaforma OpenVR hardware e piattaforma.</span><span class="sxs-lookup"><span data-stu-id="469ef-158">The OpenVR package provides hardware and platform support for devices using the OpenVR platform.</span></span>

#### <a name="windows-voice"></a><span data-ttu-id="469ef-159">Casella vocale di Windows</span><span class="sxs-lookup"><span data-stu-id="469ef-159">Windows Voice</span></span>

<span data-ttu-id="469ef-160">Il pacchetto di casella vocale di Windows fornisce supporto per la funzionalità di riconoscimento dettatura e la parola chiave nei dispositivi Microsoft Windows 10.</span><span class="sxs-lookup"><span data-stu-id="469ef-160">The Windows Voice package provides support for keyword recognition and dictation functionality on Microsoft Windows 10 devices.</span></span>

### <a name="system-services"></a><span data-ttu-id="469ef-161">Servizi di sistema</span><span class="sxs-lookup"><span data-stu-id="469ef-161">System Services</span></span>

<span data-ttu-id="469ef-162">Servizi di piattaforma di base sono incluse nei pacchetti del servizio di sistema.</span><span class="sxs-lookup"><span data-stu-id="469ef-162">Core platform services are provided in system service packages.</span></span> <span data-ttu-id="469ef-163">Questi pacchetti contengono le implementazioni predefinite del Toolkit di realtà mista delle interfacce di servizio di sistema, definite nel [core](#core-package) pacchetto.</span><span class="sxs-lookup"><span data-stu-id="469ef-163">These packages contain the Mixed Reality Toolkit's default implementations of the system service interfaces, defined in the [core](#core-package) package.</span></span>

<span data-ttu-id="469ef-164">Le basi MRTK includono i servizi di sistema seguenti:</span><span class="sxs-lookup"><span data-stu-id="469ef-164">The MRTK foundation includes the following system services:</span></span>

* [<span data-ttu-id="469ef-165">Sistema di limiti</span><span class="sxs-lookup"><span data-stu-id="469ef-165">Boundary System</span></span>](#boundary-system)
* [<span data-ttu-id="469ef-166">Sistema di diagnostica</span><span class="sxs-lookup"><span data-stu-id="469ef-166">Diagnostic System</span></span>](#diagnostic-system)
* [<span data-ttu-id="469ef-167">Sistema di input</span><span class="sxs-lookup"><span data-stu-id="469ef-167">Input System</span></span>](#input-system)
* [<span data-ttu-id="469ef-168">Sistema di riconoscimento spaziali</span><span class="sxs-lookup"><span data-stu-id="469ef-168">Spatial Awareness System</span></span>](#spatial-awareness-system)
* [<span data-ttu-id="469ef-169">Sistema teleport</span><span class="sxs-lookup"><span data-stu-id="469ef-169">Teleport System</span></span>](#teleport-system)

#### <a name="boundary-system"></a><span data-ttu-id="469ef-170">Sistema di limiti</span><span class="sxs-lookup"><span data-stu-id="469ef-170">Boundary System</span></span>

<span data-ttu-id="469ef-171">Il sistema limiti MRTK fornisce dati relativi alla realtà virtuale a playspace.</span><span class="sxs-lookup"><span data-stu-id="469ef-171">The MRTK Boundary System provides data about the to virtual reality playspace.</span></span> <span data-ttu-id="469ef-172">Nei sistemi per il quale l'utente ha configurato il limite, il sistema può fornire un piano floor, playspace rettangolare, area tracciata e altro ancora.</span><span class="sxs-lookup"><span data-stu-id="469ef-172">On systems for which the user has configured the boundary, the system can provide a floor plane, rectangular playspace, tracked area, and more.</span></span>

#### <a name="diagnostic-system"></a><span data-ttu-id="469ef-173">Sistema di diagnostica</span><span class="sxs-lookup"><span data-stu-id="469ef-173">Diagnostic System</span></span>

<span data-ttu-id="469ef-174">Il sistema di diagnostica MRTK fornisce i dati sulle prestazioni in tempo reale all'interno dell'esperienza dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="469ef-174">The MRTK Diagnostic System provides real-time performance data within your application experience.</span></span> <span data-ttu-id="469ef-175">In uso, sarà possibile visualizzare frequenza dei fotogrammi, il tempo del processore e altre metriche di prestazioni chiave quando si utilizza l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="469ef-175">At a glace, you will be able to view frame rate, processor time and other key performance metrics as you use your application.</span></span>

#### <a name="input-system"></a><span data-ttu-id="469ef-176">Sistema di input</span><span class="sxs-lookup"><span data-stu-id="469ef-176">Input System</span></span>

<span data-ttu-id="469ef-177">I sistemi di Input MRTK consente alle applicazioni di accedere all'input in modo cross-platform specificando le azioni degli utenti e assegnazione di tali azioni per i pulsanti più appropriati e degli assi nei controller di destinazione.</span><span class="sxs-lookup"><span data-stu-id="469ef-177">The MRTK Input Systems enables applications to access input in a cross platform manner by specifying user actions and assigning those actions to the most appropriate buttons and axes on target controllers.</span></span>

#### <a name="spatial-awareness-system"></a><span data-ttu-id="469ef-178">Sistema di riconoscimento spaziali</span><span class="sxs-lookup"><span data-stu-id="469ef-178">Spatial Awareness System</span></span>

<span data-ttu-id="469ef-179">Il sistema di riconoscimento spaziali MRTK consente l'accesso ai dati dell'ambiente reale da dispositivi, ad esempio il Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="469ef-179">The MRTK Spatial Awareness System enables access to real-world environmental data from devices such as the Microsoft HoloLens.</span></span>

#### <a name="teleport-system"></a><span data-ttu-id="469ef-180">Sistema teleport</span><span class="sxs-lookup"><span data-stu-id="469ef-180">Teleport System</span></span>

<span data-ttu-id="469ef-181">Il sistema Teleport MRTK fornisce il supporto di realtà virtuale locomotion.</span><span class="sxs-lookup"><span data-stu-id="469ef-181">The MRTK Teleport System provides virtual reality locomotion support.</span></span>

### <a name="feature-assets"></a><span data-ttu-id="469ef-182">Asset di funzionalità</span><span class="sxs-lookup"><span data-stu-id="469ef-182">Feature Assets</span></span>

<span data-ttu-id="469ef-183">Gli asset di funzionalità sono raccolte di funzionalità correlate fornite come gli script e gli asset di Unity.</span><span class="sxs-lookup"><span data-stu-id="469ef-183">Feature Assets are collections of related functionality delivered as Unity assets and scripts.</span></span> <span data-ttu-id="469ef-184">Alcune di queste funzionalità includono:</span><span class="sxs-lookup"><span data-stu-id="469ef-184">Some of these features include:</span></span>

* <span data-ttu-id="469ef-185">Controlli dell'interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="469ef-185">User Interface Controls</span></span>
* <span data-ttu-id="469ef-186">Risorse standard</span><span class="sxs-lookup"><span data-stu-id="469ef-186">Standard Assets</span></span>
* <span data-ttu-id="469ef-187">more</span><span class="sxs-lookup"><span data-stu-id="469ef-187">more</span></span>

## <a name="extension-packages"></a><span data-ttu-id="469ef-188">Pacchetti di estensione</span><span class="sxs-lookup"><span data-stu-id="469ef-188">Extension Packages</span></span>

<span data-ttu-id="469ef-189">I pacchetti di estensione MRTK sono una raccolta di pacchetti scritti da Microsoft e dalla Community che estendono e migliorano le funzionalità del Toolkit di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="469ef-189">MRTK Extension packages are a collection of packages written by Microsoft and the Community that extend and enhance the functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="469ef-190">Gli autori delle estensioni dello stato di tutte le dipendenze necessarie, contrassegna il pacchetto come compatibile con il Toolkit di realtà mista e fornire licenze e supportano le istruzioni.</span><span class="sxs-lookup"><span data-stu-id="469ef-190">Extension authors will state any required dependencies, mark the package as compatible with the Mixed Reality Toolkit and provide licensing and support statements.</span></span>

<span data-ttu-id="469ef-191">I pacchetti di estensione possono fornire nuove funzionalità e supporto di nuove piattaforme.</span><span class="sxs-lookup"><span data-stu-id="469ef-191">Extension packages may provide new features and new platform support.</span></span> <span data-ttu-id="469ef-192">Nel corso del tempo, le estensioni possono, con l'assistenza e approvazione degli autori, eseguire la migrazione in base MRTK momento in cui verranno rilasciate e supportate da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="469ef-192">Over time, extensions may, with the assistance and approval of the authors, be migrated into the MRTK Foundation at which time they will be released and supported by Microsoft.</span></span>

![Pacchetto di estensione MRTK](images/mrtk-extensions.jpg)

<span data-ttu-id="469ef-194">*Pacchetti di estensione di Toolkit di realtà misti*</span><span class="sxs-lookup"><span data-stu-id="469ef-194">*Mixed Reality Toolkit Extension packages*</span></span>

## <a name="experimental-packages"></a><span data-ttu-id="469ef-195">Pacchetti sperimentale</span><span class="sxs-lookup"><span data-stu-id="469ef-195">Experimental Packages</span></span>

<span data-ttu-id="469ef-196">I pacchetti sperimentale offrono la possibilità di funzionalità di prototipo dei voli, nelle versioni preliminari e nuove idee straordinarie.</span><span class="sxs-lookup"><span data-stu-id="469ef-196">Experimental packages provide the ability to flight prototype features, pre-releases and exciting new ideas.</span></span> <span data-ttu-id="469ef-197">L'obiettivo di pacchetti più sperimentali è provare qualcosa di nuovo e per valutare l'interesse del cliente.</span><span class="sxs-lookup"><span data-stu-id="469ef-197">The goal of most experimental packages is to try something new and to gauge customer interest.</span></span> <span data-ttu-id="469ef-198">Molte, anche se non tutti, pacchetti sperimentale sarà nuovamente rilasciati come estensioni del termine della creazione di prototipi e fase di test.</span><span class="sxs-lookup"><span data-stu-id="469ef-198">Many, though not all, experimental packages will be re-released as extensions once the prototyping and testing phase completes.</span></span>

![Pacchetti sperimentale MRTK](images/mrtk-experimental.jpg)

<span data-ttu-id="469ef-200">*Pacchetti sperimentale Toolkit di realtà misti*</span><span class="sxs-lookup"><span data-stu-id="469ef-200">*Mixed Reality Toolkit Experimental packages*</span></span>

## <a name="conclusion"></a><span data-ttu-id="469ef-201">Conclusione</span><span class="sxs-lookup"><span data-stu-id="469ef-201">Conclusion</span></span>

<span data-ttu-id="469ef-202">I pacchetti di Toolkit di realtà mista e il sistema di gestione pacchetti sono progettati per consentire un metodo semplice e pulito per poter compilare modo additivo funzionalità nelle tue esperienze senza ricorrere a componenti non necessari da includere nel progetto.</span><span class="sxs-lookup"><span data-stu-id="469ef-202">The Mixed Reality Toolkit packages and package management system are designed to enable a clean and simple method for you to additively build features into your experiences without requiring unnecessary components to be included into the project.</span></span>

<span data-ttu-id="469ef-203">Nel corso del tempo, verrà aggiunto il supporto di gestione pacchetti e migliorato nel Toolkit di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="469ef-203">Over time, package management support will be added and enhanced within the Mixed Reality Toolkit.</span></span> <span data-ttu-id="469ef-204">Se si dispone di commenti e suggerimenti o si vuole ottenere coinvolti, visitare il [Toolkit di realtà mista progetto](https://github.com/Microsoft/MixedRealityToolkit-Unity) su GitHub.</span><span class="sxs-lookup"><span data-stu-id="469ef-204">If you have feedback or wish to get involved, please visit the [Mixed Reality Toolkit project](https://github.com/Microsoft/MixedRealityToolkit-Unity) on GitHub.</span></span> 

## <a name="see-also"></a><span data-ttu-id="469ef-205">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="469ef-205">See also</span></span>

* [<span data-ttu-id="469ef-206">MixedRealityToolkit-Unity (GitHub)</span><span class="sxs-lookup"><span data-stu-id="469ef-206">MixedRealityToolkit-Unity (GitHub)</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)


---
title: Spectator View
description: Visualizzare gli ologrammi da un dispositivo esterno per mostrare un'esperienza di realtà mista su un display esterno o registrare un video di tale esperienza.
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Spectator View, iPhone, iOS, iPad, OpenCV, Camera, ARKit, HoloLens, Realtà mista, MixedRealityToolkit, demo, record
ms.openlocfilehash: 9bc1c2809c7d780d439d9efb58f464b41de3dccd
ms.sourcegitcommit: 4d43a8f40e3132605cee9ece9229e67d985db645
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491167"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a><span data-ttu-id="3bf4e-104">Spectator View per HoloLens e HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="3bf4e-104">Spectator View for HoloLens and HoloLens 2</span></span>

![Marker](images/SpecViewPhoneHero.jpg)

## <a name="overview"></a><span data-ttu-id="3bf4e-106">Panoramica</span><span class="sxs-lookup"><span data-stu-id="3bf4e-106">Overview</span></span>

<span data-ttu-id="3bf4e-107">Quando indossiamo un dispositivo HoloLens, spesso dimentichiamo che le persone che non lo hanno non possono assistere alle cose straordinarie che possiamo vedere.</span><span class="sxs-lookup"><span data-stu-id="3bf4e-107">When wearing a HoloLens, we often forget that a person who does not have it on is unable to experience the wonders that we can.</span></span> <span data-ttu-id="3bf4e-108">Spectator View consente agli altri di visualizzare su uno schermo 2D ciò che un utente di HoloLens può vedere nel proprio mondo.</span><span class="sxs-lookup"><span data-stu-id="3bf4e-108">Spectator View allows others to see on a 2D screen what a HoloLens user sees in their world.</span></span>
<span data-ttu-id="3bf4e-109">Questo strumento offre un approccio rapido e conveniente per registrare ologrammi in HD usando dispositivi mobili.</span><span class="sxs-lookup"><span data-stu-id="3bf4e-109">Spectator View offers a fast and affordable approach to recording holograms in HD with mobile devices.</span></span> <span data-ttu-id="3bf4e-110">Offre inoltre la possibilità di eseguire registrazioni degli ologrammi di qualità professionale con videocamere.</span><span class="sxs-lookup"><span data-stu-id="3bf4e-110">It also offers a professional quality recording of holograms with video cameras.</span></span>

## <a name="key-resources"></a><span data-ttu-id="3bf4e-111">Risorse principali</span><span class="sxs-lookup"><span data-stu-id="3bf4e-111">Key Resources</span></span>

* [<span data-ttu-id="3bf4e-112">**Spectator View su GitHub**</span><span class="sxs-lookup"><span data-stu-id="3bf4e-112">**Spectator View on GitHub**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView)
* [<span data-ttu-id="3bf4e-113">**Documentazione di Spectator View**</span><span class="sxs-lookup"><span data-stu-id="3bf4e-113">**Spectator View Documentation**</span></span>](https://microsoft.github.io/MixedReality-SpectatorView/README.html)
* [<span data-ttu-id="3bf4e-114">**Esempi di Spectator View**</span><span class="sxs-lookup"><span data-stu-id="3bf4e-114">**Spectator View Samples**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)

## <a name="use-cases"></a><span data-ttu-id="3bf4e-115">Casi d'uso</span><span class="sxs-lookup"><span data-stu-id="3bf4e-115">Use Cases</span></span>
* <span data-ttu-id="3bf4e-116">Puoi registrare un'esperienza di realtà mista usando un iPhone o un dispositivo Android.</span><span class="sxs-lookup"><span data-stu-id="3bf4e-116">You can record a mixed reality experience using an iPhone or Android device.</span></span> <span data-ttu-id="3bf4e-117">Esegui una registrazione in Full HD e applica l'anti-aliasing agli ologrammi e persino le ombre.</span><span class="sxs-lookup"><span data-stu-id="3bf4e-117">Record in full HD and apply anti-aliasing to holograms and even shadows.</span></span> <span data-ttu-id="3bf4e-118">È un modo economico e rapido per acquisire video di ologrammi.</span><span class="sxs-lookup"><span data-stu-id="3bf4e-118">It is a cost-effective and quick way to capture video of holograms.</span></span>
* <span data-ttu-id="3bf4e-119">Trasmetti in streaming le esperienze di realtà mista a un dispositivo Apple TV direttamente dal tuo iPhone o iPad, in tempo reale.</span><span class="sxs-lookup"><span data-stu-id="3bf4e-119">Stream live mixed reality experiences to an Apple TV directly from your iPhone or iPad, lag-free!</span></span>
* <span data-ttu-id="3bf4e-120">Condividi l'esperienza con i tuoi ospiti: consenti alle persone che non hanno HoloLens di visualizzare gli ologrammi direttamente dai loro telefoni o tablet.</span><span class="sxs-lookup"><span data-stu-id="3bf4e-120">Share the experience with guests: Let non-HoloLens users experience holograms directly from their phones or tablets.</span></span>

## <a name="current-features"></a><span data-ttu-id="3bf4e-121">Funzionalità attualmente disponibili</span><span class="sxs-lookup"><span data-stu-id="3bf4e-121">Current Features</span></span>

* <span data-ttu-id="3bf4e-122">Sincronizzazione spaziale degli ologrammi, in modo che tutti possano visualizzare gli ologrammi esattamente nella stessa posizione.</span><span class="sxs-lookup"><span data-stu-id="3bf4e-122">Spatial synchronization of Holograms, so everyone sees holograms in the exact same place.</span></span>
* <span data-ttu-id="3bf4e-123">Supporto per iOS (dispositivi abilitati per ARKit) e Android (dispositivi abilitati per ARCore).</span><span class="sxs-lookup"><span data-stu-id="3bf4e-123">iOS (ARKit-enabled devices) and Android (ARCore-enabled devices) support.</span></span>
<span data-ttu-id="3bf4e-124">Più utenti guest iOS.</span><span class="sxs-lookup"><span data-stu-id="3bf4e-124">Multiple iOS guests.</span></span>
<span data-ttu-id="3bf4e-125">Registrazione di video + ologrammi + audio dell'ambiente + audio dell'ologramma.</span><span class="sxs-lookup"><span data-stu-id="3bf4e-125">Recording of video + holograms + ambient sound + hologram sound.</span></span>
<span data-ttu-id="3bf4e-126">Strumento di condivisione per poter salvare video, inviare un messaggio e-mail o condividere l'esperienza con altre app supportate.</span><span class="sxs-lookup"><span data-stu-id="3bf4e-126">Share sheet so you can save video, email it, or share with other supporting apps.</span></span>

<span data-ttu-id="3bf4e-127">![Marker](images/SpecViewPhoneDemo.jpg)
![Marker](images/hololensspectatorview-500px.jpg) ![Marker](images/spectatorview-300px.png)</span><span class="sxs-lookup"><span data-stu-id="3bf4e-127">![Marker](images/SpecViewPhoneDemo.jpg)
![Marker](images/hololensspectatorview-500px.jpg) ![Marker](images/spectatorview-300px.png)</span></span>

<span data-ttu-id="3bf4e-128">La tabella seguente illustra le diverse funzionalità di Spectator View e le opzioni supportate.</span><span class="sxs-lookup"><span data-stu-id="3bf4e-128">The following table shows different Spectator View functionality and their capabilities.</span></span> <span data-ttu-id="3bf4e-129">Scegli l'opzione più adatta alle tue esigenze di registrazione video:</span><span class="sxs-lookup"><span data-stu-id="3bf4e-129">Choose the option that best fits your video recording needs:</span></span>

|                                      | <span data-ttu-id="3bf4e-130">Dispositivi mobili</span><span class="sxs-lookup"><span data-stu-id="3bf4e-130">Mobile</span></span>                  |                    <span data-ttu-id="3bf4e-131">Videocamera</span><span class="sxs-lookup"><span data-stu-id="3bf4e-131">Video Camera</span></span>              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| <span data-ttu-id="3bf4e-132">Qualità HD</span><span class="sxs-lookup"><span data-stu-id="3bf4e-132">HD quality</span></span>                           |         <span data-ttu-id="3bf4e-133">Full HD</span><span class="sxs-lookup"><span data-stu-id="3bf4e-133">Full HD</span></span>         |        <span data-ttu-id="3bf4e-134">Registrazioni di qualità professionale (in base alla videocamera)</span><span class="sxs-lookup"><span data-stu-id="3bf4e-134">Professional quality filming (as determined by video camera)</span></span>      |
| <span data-ttu-id="3bf4e-135">Facilità di spostamento della videocamera</span><span class="sxs-lookup"><span data-stu-id="3bf4e-135">Easy camera movement</span></span>                 |            <span data-ttu-id="3bf4e-136">✔</span><span class="sxs-lookup"><span data-stu-id="3bf4e-136">✔</span></span>            |                      <span data-ttu-id="3bf4e-137">✔</span><span class="sxs-lookup"><span data-stu-id="3bf4e-137">✔</span></span>                      |
| <span data-ttu-id="3bf4e-138">Visualizzazione di altre persone</span><span class="sxs-lookup"><span data-stu-id="3bf4e-138">Third-person view</span></span>                    |            <span data-ttu-id="3bf4e-139">✔</span><span class="sxs-lookup"><span data-stu-id="3bf4e-139">✔</span></span>            |                      <span data-ttu-id="3bf4e-140">✔</span><span class="sxs-lookup"><span data-stu-id="3bf4e-140">✔</span></span>                      |
| <span data-ttu-id="3bf4e-141">Trasmissione in streaming su uno schermo</span><span class="sxs-lookup"><span data-stu-id="3bf4e-141">Can be streamed to screens</span></span>           |            <span data-ttu-id="3bf4e-142">✔</span><span class="sxs-lookup"><span data-stu-id="3bf4e-142">✔</span></span>            |                      <span data-ttu-id="3bf4e-143">✔</span><span class="sxs-lookup"><span data-stu-id="3bf4e-143">✔</span></span>                      |
| <span data-ttu-id="3bf4e-144">Portabile</span><span class="sxs-lookup"><span data-stu-id="3bf4e-144">Portable</span></span>                             |            <span data-ttu-id="3bf4e-145">✔</span><span class="sxs-lookup"><span data-stu-id="3bf4e-145">✔</span></span>            |                                             |
| <span data-ttu-id="3bf4e-146">Wireless</span><span class="sxs-lookup"><span data-stu-id="3bf4e-146">Wireless</span></span>                             |            <span data-ttu-id="3bf4e-147">✔</span><span class="sxs-lookup"><span data-stu-id="3bf4e-147">✔</span></span>            |                                             |
| <span data-ttu-id="3bf4e-148">Altri requisiti hardware</span><span class="sxs-lookup"><span data-stu-id="3bf4e-148">Additional required hardware</span></span>         |     <span data-ttu-id="3bf4e-149">Telefono Android, iPhone</span><span class="sxs-lookup"><span data-stu-id="3bf4e-149">Android phone, iPhone</span></span>    | <span data-ttu-id="3bf4e-150">HoloLens + attrezzatura + treppiede + videocamera + PC + Unity</span><span class="sxs-lookup"><span data-stu-id="3bf4e-150">HoloLens + Rig + Tripod + Video Camera + PC + Unity</span></span> |
| <span data-ttu-id="3bf4e-151">Investimento hardware</span><span class="sxs-lookup"><span data-stu-id="3bf4e-151">Hardware investment</span></span>                  |           <span data-ttu-id="3bf4e-152">Bassa</span><span class="sxs-lookup"><span data-stu-id="3bf4e-152">Low</span></span>            |                     <span data-ttu-id="3bf4e-153">Alto</span><span class="sxs-lookup"><span data-stu-id="3bf4e-153">High</span></span>                    |
| <span data-ttu-id="3bf4e-154">Multipiattaforma</span><span class="sxs-lookup"><span data-stu-id="3bf4e-154">Cross-platform</span></span>                       |           <span data-ttu-id="3bf4e-155">Android, iOS</span><span class="sxs-lookup"><span data-stu-id="3bf4e-155">Android, iOS</span></span>   |                                             |
| <span data-ttu-id="3bf4e-156">Contenuto sincronizzato</span><span class="sxs-lookup"><span data-stu-id="3bf4e-156">Synchronized content</span></span>                 |            <span data-ttu-id="3bf4e-157">✔</span><span class="sxs-lookup"><span data-stu-id="3bf4e-157">✔</span></span>            |                      <span data-ttu-id="3bf4e-158">✔</span><span class="sxs-lookup"><span data-stu-id="3bf4e-158">✔</span></span>                      |
| <span data-ttu-id="3bf4e-159">Durata di configurazione del runtime</span><span class="sxs-lookup"><span data-stu-id="3bf4e-159">Runtime setup duration</span></span>               |         <span data-ttu-id="3bf4e-160">Istantanea</span><span class="sxs-lookup"><span data-stu-id="3bf4e-160">Instant</span></span>          |                     <span data-ttu-id="3bf4e-161">Lenta</span><span class="sxs-lookup"><span data-stu-id="3bf4e-161">Slow</span></span>                    |
## <a name="see-also"></a><span data-ttu-id="3bf4e-162">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="3bf4e-162">See also</span></span>

* [<span data-ttu-id="3bf4e-163">Acquisizione realtà mista</span><span class="sxs-lookup"><span data-stu-id="3bf4e-163">Mixed reality capture</span></span>](mixed-reality-capture.md) 
* [<span data-ttu-id="3bf4e-164">Acquisizione realtà mista per sviluppatori</span><span class="sxs-lookup"><span data-stu-id="3bf4e-164">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
* [<span data-ttu-id="3bf4e-165">Esperienze condivise nella realtà mista</span><span class="sxs-lookup"><span data-stu-id="3bf4e-165">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)

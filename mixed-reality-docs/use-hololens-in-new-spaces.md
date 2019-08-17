---
title: Usare HoloLens in nuovi spazi
description: HoloLens apprende l'aspetto di uno spazio nel tempo. Gli utenti possono semplificare questo processo spostando il HoloLens in determinati modi attraverso lo spazio.
author: dorreneb
ms.author: dobrown
ms.date: 08/16/2019
ms.topic: article
keywords: Realtà mista di Windows, progettazione, mapping spaziale, HoloLens, ricostruzione di superficie, mesh, rilevamento Head, mapping
ms.openlocfilehash: a6a83dfc2c883723e4cd79c0dc46a9cd78f1f604
ms.sourcegitcommit: 60f73ca23023c17c1da833c83d2a02f4dcc4d17b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566020"
---
# <a name="use-hololens-in-new-spaces"></a><span data-ttu-id="b9402-105">Usare HoloLens in nuovi spazi</span><span class="sxs-lookup"><span data-stu-id="b9402-105">Use HoloLens in New Spaces</span></span>

<span data-ttu-id="b9402-106">HoloLens *esegue il mapping*o apprende le informazioni relative all'ambiente quando l'utente si sposta su uno spazio.</span><span class="sxs-lookup"><span data-stu-id="b9402-106">HoloLens *maps*, or learns information about, its environment as the user moves around a space.</span></span> <span data-ttu-id="b9402-107">Nel corso del tempo, il HoloLens crea una *mappa spaziale* di tutte le parti dell'ambiente che sono state osservate.</span><span class="sxs-lookup"><span data-stu-id="b9402-107">Over time, the HoloLens builds up a *spatial map* of all parts of the environment that have been observed.</span></span> <span data-ttu-id="b9402-108">HoloLens aggiorna la mappa in modo che vengano osservate le modifiche nell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="b9402-108">HoloLens updates the map as changes in the environment are observed.</span></span> <span data-ttu-id="b9402-109">Questa analisi verrà mantenute automaticamente tra i lanci dell'app.</span><span class="sxs-lookup"><span data-stu-id="b9402-109">This scan will automatically persist between app launches.</span></span>

<span data-ttu-id="b9402-110">HoloLens creerà e aggiornerà le mappe fino a quando il dispositivo è acceso e un utente è connesso.</span><span class="sxs-lookup"><span data-stu-id="b9402-110">HoloLens will create and update maps as long as the device is on and a user is logged in.</span></span> <span data-ttu-id="b9402-111">Se si tiene o si indossa il dispositivo con le fotocamere puntate a uno spazio, il dispositivo tenterà di eseguire il mapping dell'area.</span><span class="sxs-lookup"><span data-stu-id="b9402-111">If you hold or wear the device with the cameras pointed at a space, the device will try to map the area.</span></span> <span data-ttu-id="b9402-112">Sebbene il HoloLens apprenda uno spazio naturalmente nel tempo, sono disponibili suggerimenti e consigli per eseguire il mapping dello spazio in modo più rapido ed efficiente.</span><span class="sxs-lookup"><span data-stu-id="b9402-112">While the HoloLens will learn a space naturally over time, there are tips and tricks available to map the space faster and more efficiently.</span></span> 

<span data-ttu-id="b9402-113">Se il HoloLens non è in grado di eseguire il mapping dello spazio o non è disponibile, è possibile attivare la modalità Limited.</span><span class="sxs-lookup"><span data-stu-id="b9402-113">If your HoloLens can’t map your space or is out of calibration, you may enter Limited mode.</span></span> <span data-ttu-id="b9402-114">In modalità limitata, non sarà possibile posizionare gli ologrammi nell'ambiente in uso.</span><span class="sxs-lookup"><span data-stu-id="b9402-114">In Limited mode, you won’t be able to place holograms in your surroundings.</span></span>

## <a name="tips-and-tricks-for-mapping-spaces"></a><span data-ttu-id="b9402-115">Suggerimenti e consigli per gli spazi di mapping</span><span class="sxs-lookup"><span data-stu-id="b9402-115">Tips and tricks for mapping spaces</span></span>

### <a name="make-sure-the-space-is-set-up-for-mixed-reality"></a><span data-ttu-id="b9402-116">Verificare che lo spazio sia configurato per la realtà mista</span><span class="sxs-lookup"><span data-stu-id="b9402-116">Make sure the space is set up for mixed reality</span></span>

<span data-ttu-id="b9402-117">Le funzionalità in un ambiente possono rendere difficile per HoloLens interpretare uno spazio.</span><span class="sxs-lookup"><span data-stu-id="b9402-117">Features in an environment can make it difficult for the HoloLens to interpret a space.</span></span> <span data-ttu-id="b9402-118">I livelli leggeri, i materiali nello spazio, il layout degli oggetti e altro ancora possono influire sul modo in cui HoloLens esegue il mapping di un'area.</span><span class="sxs-lookup"><span data-stu-id="b9402-118">Light levels, materials in the space, the layout of objects, and more can all affect how HoloLens maps an area.</span></span>

<span data-ttu-id="b9402-119">Suggerimenti per la configurazione dello spazio per HoloLens e altri dispositivi a realtà mista sono disponibili in [considerazioni sull'ambiente per HoloLens](environment-considerations-for-hololens.md).</span><span class="sxs-lookup"><span data-stu-id="b9402-119">Tips for setting up your space for HoloLens and other mixed reality devices can be found in [Environment considerations for HoloLens](environment-considerations-for-hololens.md).</span></span>

### <a name="understand-the-scenarios-for-the-area"></a><span data-ttu-id="b9402-120">Informazioni sugli scenari per l'area</span><span class="sxs-lookup"><span data-stu-id="b9402-120">Understand the scenarios for the area</span></span>

<span data-ttu-id="b9402-121">È importante dedicare la maggior parte del tempo in cui si utilizzerà il HoloLens in modo che la mappa sia pertinente e completa.</span><span class="sxs-lookup"><span data-stu-id="b9402-121">It is important to spend the most time where you will be using the HoloLens so that the map is relevant and complete.</span></span> 

<span data-ttu-id="b9402-122">Se, ad esempio, uno scenario utente per HoloLens prevede lo spostamento dal punto A al punto B, passare a tale percorso due o tre volte, esaminando tutte le direzioni mentre si sposta.</span><span class="sxs-lookup"><span data-stu-id="b9402-122">For example, if a user scenario for HoloLens involves moving from Point A to Point B, walk that path two to three times, looking in all directions as you move.</span></span> 

### <a name="walk-slowly-around-the-space"></a><span data-ttu-id="b9402-123">Scorrere lentamente intorno allo spazio</span><span class="sxs-lookup"><span data-stu-id="b9402-123">Walk slowly around the space</span></span>

<span data-ttu-id="b9402-124">Se si cammina troppo rapidamente intorno all'area, è probabile che il HoloLens non perda le aree di mapping.</span><span class="sxs-lookup"><span data-stu-id="b9402-124">If you walk too quickly around the area, it's likely that the HoloLens will miss mapping areas.</span></span> <span data-ttu-id="b9402-125">Esaminare lentamente lo spazio, arrestando ogni 5-8 metri di distanza per esplorare l'ambiente in uso.</span><span class="sxs-lookup"><span data-stu-id="b9402-125">Walk slowly around the space, stopping every 5-8 feet to look around at your surroundings.</span></span>

<span data-ttu-id="b9402-126">I movimenti uniformi aiutano anche il HoloLens mappare più effeciently.</span><span class="sxs-lookup"><span data-stu-id="b9402-126">Smooth movements also help the HoloLens map more effeciently.</span></span>

### <a name="look-in-all-directions"></a><span data-ttu-id="b9402-127">Cerca in tutte le direzioni</span><span class="sxs-lookup"><span data-stu-id="b9402-127">Look in all directions</span></span>

<span data-ttu-id="b9402-128">Quando si esegue il mapping dello spazio, il HoloLens offre più dati su cui i punti sono relativi tra loro.</span><span class="sxs-lookup"><span data-stu-id="b9402-128">Looking around as you map the space gives the HoloLens more data on where points are relative to each other.</span></span> 

<span data-ttu-id="b9402-129">Se non si cerca, ad esempio, il HoloLens potrebbe non essere in grado di individuare la posizione in cui si trova il limite massimo in una stanza.</span><span class="sxs-lookup"><span data-stu-id="b9402-129">If you don't look up, for example, the HoloLens may not know where the ceiling in a room is.</span></span> 

<span data-ttu-id="b9402-130">Quando si esegue il mapping dello spazio, non dimenticare di esaminare la superficie.</span><span class="sxs-lookup"><span data-stu-id="b9402-130">Don't forget to look down at the floor as you map the space.</span></span>

### <a name="cover-key-areas-multiple-times"></a><span data-ttu-id="b9402-131">Aree principali di copertura più volte</span><span class="sxs-lookup"><span data-stu-id="b9402-131">Cover key areas multiple times</span></span>

<span data-ttu-id="b9402-132">Spostarsi più volte in un'area consente di prelevare le funzionalità che potrebbero mancare nella prima procedura dettagliata.</span><span class="sxs-lookup"><span data-stu-id="b9402-132">Moving through an area multiple times will help pick up features you may have missed on the first walkthrough.</span></span> <span data-ttu-id="b9402-133">Provare a attraversare un'area da due a tre volte per creare una mappa ideale.</span><span class="sxs-lookup"><span data-stu-id="b9402-133">Try traversing an area two to three times to build an ideal map.</span></span>

<span data-ttu-id="b9402-134">Se possibile, durante la ripetizione di questi movimenti, dedicare tempo a esplorare un'area in una direzione, quindi a tornare indietro nel modo in cui si è arrivati.</span><span class="sxs-lookup"><span data-stu-id="b9402-134">If possible, while repeating these movements, spend time walking through an area in one direction, then turn around and walk back the way you came.</span></span>

### <a name="take-your-time-mapping-the-area"></a><span data-ttu-id="b9402-135">Eseguire il mapping del tempo all'area</span><span class="sxs-lookup"><span data-stu-id="b9402-135">Take your time mapping the area</span></span>

<span data-ttu-id="b9402-136">Possono essere necessari tra 15 e 20 minuti affinché il HoloLens sia completamente mappato e si adatta ai propri dintorni.</span><span class="sxs-lookup"><span data-stu-id="b9402-136">It can take between 15 and 20 minutes for the HoloLens to fully map and adjust itself to its surroundings.</span></span> <span data-ttu-id="b9402-137">Se si dispone di uno spazio in cui si prevede di usare un HoloLens di frequente, il tempo necessario per eseguire il mapping dello spazio può impedire problemi in un secondo momento.</span><span class="sxs-lookup"><span data-stu-id="b9402-137">If you have a space in which you plan to use a HoloLens frequently, taking that time up front to map the space can prevent issues later on.</span></span> 

## <a name="possible-errors-in-the-spatial-map"></a><span data-ttu-id="b9402-138">Possibili errori nella mappa spaziale</span><span class="sxs-lookup"><span data-stu-id="b9402-138">Possible errors in the spatial map</span></span>

<span data-ttu-id="b9402-139">Gli errori nei dati di mapping spaziale rientrano in una delle tre categorie seguenti:</span><span class="sxs-lookup"><span data-stu-id="b9402-139">Errors in spatial mapping data fall into one of three categories:</span></span>

* <span data-ttu-id="b9402-140">*Buchi*: Nei dati di mapping spaziale mancano le superfici reali.</span><span class="sxs-lookup"><span data-stu-id="b9402-140">*Holes*: Real-world surfaces are missing from the spatial mapping data.</span></span>
* <span data-ttu-id="b9402-141">*Allucinazioni*: Le superfici sono presenti nei dati di mapping spaziali che non esistono nel mondo reale.</span><span class="sxs-lookup"><span data-stu-id="b9402-141">*Hallucinations*: Surfaces exist in the spatial mapping data that do not exist in the real world.</span></span>
* <span data-ttu-id="b9402-142">*Wormhole*: HoloLens "perde" parte della mappa spaziale pensando che si trovi in una parte diversa della mappa rispetto al fatto.</span><span class="sxs-lookup"><span data-stu-id="b9402-142">*Wormholes*: HoloLens 'loses' part of the spatial map by thinking it is in a different part of the map than it actually is.</span></span>
* <span data-ttu-id="b9402-143">*Distorsione*: Le superfici nei dati di mapping spaziale sono allineate in modo non perfetto con le superfici reali, spostate o estratte.</span><span class="sxs-lookup"><span data-stu-id="b9402-143">*Bias*: Surfaces in the spatial mapping data are imperfectly aligned with real-world surfaces, either pushed in or pulled out.</span></span>

<span data-ttu-id="b9402-144">Molti di questi errori possono essere attenuati eliminando gli [ologrammi](environment-considerations-for-hololens.md) ed eseguendo di nuovo il mapping dello spazio.</span><span class="sxs-lookup"><span data-stu-id="b9402-144">Many of these errors can be mitigated by [deleting your holograms](environment-considerations-for-hololens.md) and re-mapping the space.</span></span>
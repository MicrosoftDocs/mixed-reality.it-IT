---
title: Sguardo e dimora
description: Panoramica generale del modello di input di tipo (occhio/testa)
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Realtà mista, sguardo, abitazione, interazione, progettazione, rilevamento degli occhi, verifica della testa
ms.openlocfilehash: d87406d0b2695cd86c40f27cb132af54ed525b25
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435359"
---
# <a name="gaze-and-dwell"></a><span data-ttu-id="91719-104">Sguardo e dimora</span><span class="sxs-lookup"><span data-stu-id="91719-104">Gaze and dwell</span></span>

<span data-ttu-id="91719-105">Quando le mani sono occupate con gli attrezzi e le parti, i movimenti possono risultare difficili o addirittura impossibili.</span><span class="sxs-lookup"><span data-stu-id="91719-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span> <span data-ttu-id="91719-106">I comandi vocali possono anche essere inaffidabili in determinati contesti, ad esempio in condizioni troppo potenti.</span><span class="sxs-lookup"><span data-stu-id="91719-106">Voice commands may also be unreliable in certain contexts, for example under excessively loud conditions.</span></span> <span data-ttu-id="91719-107">Sguardi e abitazioni offre un meccanismo familiare e facile da gestire per l'esecuzione di attività di Head-up e hands-free in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="91719-107">Gaze and dwell offers a familiar and easy-to-master mechanism for working heads-up and hands-free on HoloLens.</span></span> <span data-ttu-id="91719-108">Inoltre, lo sguardo e l'abitazione sono un ottimo fallback indipendente dall'interferenza del rumore o dai vincoli di silenzio nell'ambiente operativo.</span><span class="sxs-lookup"><span data-stu-id="91719-108">Additionally, gaze and dwell is a great fallback which is independent of noise interference or silence constraints in the operating environment.</span></span>
<span data-ttu-id="91719-109">Si distinguono due varianti di _sguardo e dimora_, ovvero lo [sguardo](gaze-and-dwell-head.md) e l'abitato e lo [sguardo e l'abitazione](gaze-and-dwell-eyes.md).</span><span class="sxs-lookup"><span data-stu-id="91719-109">We distinguish two variants of _gaze and dwell_: [Head-gaze and dwell](gaze-and-dwell-head.md) and [Eye-gaze and dwell](gaze-and-dwell-eyes.md).</span></span>

## <a name="scenarios"></a><span data-ttu-id="91719-110">Scenari</span><span class="sxs-lookup"><span data-stu-id="91719-110">Scenarios</span></span>

<span data-ttu-id="91719-111">Lo sguardo e l'abitazione sono eccellenti negli scenari in cui le mani di una persona sono occupate da altre attività e la voce non è del 100% affidabile o disponibile a causa di vincoli ambientali o sociali.</span><span class="sxs-lookup"><span data-stu-id="91719-111">Gaze and dwell excels in scenarios where a person's hands are busy with other tasks, and voice isn't 100% reliable or available due to environmental or social constraints.</span></span> <span data-ttu-id="91719-112">Un buon esempio di questo tipo di situazioni è dato da una persona che indossa un dispositivo HoloLens per la sovrimpressione di informazioni di riferimento mentre ripara il motore di un'automobile.</span><span class="sxs-lookup"><span data-stu-id="91719-112">A good example is a person wearing a HoloLens to overlay reference information while repairing a car engine.</span></span> <span data-ttu-id="91719-113">Le sue mani sono occupate con gli attrezzi o devono sostenere il corpo mentre la persona si protende sul vano motore.</span><span class="sxs-lookup"><span data-stu-id="91719-113">Their hands are busy with tools or supporting their body as they lean into the engine compartment.</span></span> <span data-ttu-id="91719-114">L'autofficina è rumorosa a causa dei colpi e del ronzio costanti degli attrezzi da lavoro, quindi l'uso dei comandi vocali risulterebbe particolarmente difficoltoso.</span><span class="sxs-lookup"><span data-stu-id="91719-114">The garage space is loud, with the constant banging and buzzing of tools, making voice commands difficult.</span></span> <span data-ttu-id="91719-115">Lo sguardo e l'abitazione consentono all'utente che usa HoloLens di esplorare in modo sicuro il materiale di riferimento senza interrompere il flusso di lavoro.</span><span class="sxs-lookup"><span data-stu-id="91719-115">Gaze and dwell allows the person using the HoloLens to confidently navigate their reference material without interrupting their workflow.</span></span> 

## <a name="device-support"></a><span data-ttu-id="91719-116">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="91719-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="91719-117"><strong>Modello di input</strong></span><span class="sxs-lookup"><span data-stu-id="91719-117"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="91719-118"><a href="hololens-hardware-details.md"><strong>HoloLens (prima generazione)</strong></a></span><span class="sxs-lookup"><span data-stu-id="91719-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="91719-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="91719-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="91719-120"><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="91719-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="91719-121">Puntamento con la testa e attesa</span><span class="sxs-lookup"><span data-stu-id="91719-121">Head-gaze and dwell</span></span></td>
        <td><span data-ttu-id="91719-122">✔️ Consigliata</span><span class="sxs-lookup"><span data-stu-id="91719-122">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="91719-123">✔️ Consigliata</span><span class="sxs-lookup"><span data-stu-id="91719-123">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="91719-124">✔️ Consigliata</span><span class="sxs-lookup"><span data-stu-id="91719-124">✔️ Recommended</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="91719-125">Sguardo e dimora</span><span class="sxs-lookup"><span data-stu-id="91719-125">Eye-gaze and dwell</span></span></td>
        <td><span data-ttu-id="91719-126">❌ non disponibile</span><span class="sxs-lookup"><span data-stu-id="91719-126">❌ Not available</span></span></td>
        <td><span data-ttu-id="91719-127">✔️ Consigliata</span><span class="sxs-lookup"><span data-stu-id="91719-127">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="91719-128">❌ non disponibile</span><span class="sxs-lookup"><span data-stu-id="91719-128">❌ Not available</span></span></td>
    </tr>
</table>


<br>

---
 
 ## <a name="see-also"></a><span data-ttu-id="91719-129">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="91719-129">See also</span></span>
* [<span data-ttu-id="91719-130">Interazione basata sull'occhio</span><span class="sxs-lookup"><span data-stu-id="91719-130">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="91719-131">Rilevamento degli occhi su HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="91719-131">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="91719-132">Sguardo e commit</span><span class="sxs-lookup"><span data-stu-id="91719-132">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="91719-133">Manipolazione diretta</span><span class="sxs-lookup"><span data-stu-id="91719-133">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="91719-134">Movimenti pratici</span><span class="sxs-lookup"><span data-stu-id="91719-134">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="91719-135">Hand-point e commit</span><span class="sxs-lookup"><span data-stu-id="91719-135">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="91719-136">Interazioni istintive</span><span class="sxs-lookup"><span data-stu-id="91719-136">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="91719-137">Input vocale</span><span class="sxs-lookup"><span data-stu-id="91719-137">Voice input</span></span>](voice-input.md)

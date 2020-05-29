---
title: Azione di avvio
description: Avviare il gesto per chiamare il menu Start.
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: Realtà mista, movimenti, interazione, progettazione
ms.openlocfilehash: 84088156d0c9cdacc421985b922d5e9370f6a87e
ms.sourcegitcommit: fd606e87e3c4785d3ca2a26632be3bb580e39afb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/28/2020
ms.locfileid: "84152518"
---
# <a name="start-gesture"></a><span data-ttu-id="20d2f-104">Azione di avvio</span><span class="sxs-lookup"><span data-stu-id="20d2f-104">Start gesture</span></span>

<span data-ttu-id="20d2f-105">Il gesto di avvio è un movimento della mano usato per richiamare il menu Start.</span><span class="sxs-lookup"><span data-stu-id="20d2f-105">The Start gesture is a hand gesture used to invoke the Start Menu.</span></span> <span data-ttu-id="20d2f-106">È l'equivalente di premere il tasto Windows sulla tastiera, il pulsante Xbox su un controller Xbox o il pulsante Windows sul controller di movimento per le cuffie immersive.</span><span class="sxs-lookup"><span data-stu-id="20d2f-106">It is the equivalent of pressing the Windows key on the keyboard, the Xbox button on an Xbox controller, or the Windows button on the immersive headset motion controller.</span></span> <span data-ttu-id="20d2f-107">È importante comprendere quali movimenti sono riservati per il sistema in ogni dispositivo di realtà mista per evitare conflitti durante la progettazione delle interazioni.</span><span class="sxs-lookup"><span data-stu-id="20d2f-107">It's important to understand which gestures are reserved for the system on each Mixed Reality device to prevent conflicts when designing your interactions.</span></span>

## <a name="device-support"></a><span data-ttu-id="20d2f-108">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="20d2f-108">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="20d2f-109"><strong>Funzionalità</strong></span><span class="sxs-lookup"><span data-stu-id="20d2f-109"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="20d2f-110"><a href="hololens-hardware-details.md"><strong>HoloLens (prima generazione)</strong></a></span><span class="sxs-lookup"><span data-stu-id="20d2f-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="20d2f-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="20d2f-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="20d2f-112"><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="20d2f-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="20d2f-113">Fioritura</span><span class="sxs-lookup"><span data-stu-id="20d2f-113">Bloom</span></span></td>
        <td><span data-ttu-id="20d2f-114">✔️</span><span class="sxs-lookup"><span data-stu-id="20d2f-114">✔️</span></span></td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="20d2f-115">Pulsante polso</span><span class="sxs-lookup"><span data-stu-id="20d2f-115">Wrist button</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="20d2f-116">✔️</span><span class="sxs-lookup"><span data-stu-id="20d2f-116">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="20d2f-117">Occhio e palmare</span><span class="sxs-lookup"><span data-stu-id="20d2f-117">Eye gaze and palm up pinch</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="20d2f-118">✔️</span><span class="sxs-lookup"><span data-stu-id="20d2f-118">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a><span data-ttu-id="20d2f-119">Fioritura</span><span class="sxs-lookup"><span data-stu-id="20d2f-119">Bloom</span></span>
<span data-ttu-id="20d2f-120">Per visualizzare il menu Start in HoloLens (1st Gen), abbiamo progettato "Bloom", un gesto simbolico che simula il fiore fiorito.</span><span class="sxs-lookup"><span data-stu-id="20d2f-120">To bring up the start menu in HoloLens (1st gen), we designed “Bloom”, which is a symbolic gesture mimicking the flower blossom.</span></span> <span data-ttu-id="20d2f-121">È distinto per l'interazione surefooted, facile da eseguire e rapido da richiamare.</span><span class="sxs-lookup"><span data-stu-id="20d2f-121">It's distinctive for surefooted interaction, easy to perform, and quick to recall.</span></span> <span data-ttu-id="20d2f-122">Per eseguire il gesto di fioritura su HoloLens (1 ° gen), è necessario passare a un palmo e a una mano insieme, quindi aprire la mano diffondendo le dita.</span><span class="sxs-lookup"><span data-stu-id="20d2f-122">To do the bloom gesture on HoloLens (1st gen), hold out your hand with your palm up and fingertips together, then open your hand by spreading your fingers.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="20d2f-123">![Bloom close](images/bloom-close.png)</span><span class="sxs-lookup"><span data-stu-id="20d2f-123">![Bloom close](images/bloom-close.png)</span></span><br>
        <span data-ttu-id="20d2f-124">**Passaggio 1: palmare insieme**</span><span class="sxs-lookup"><span data-stu-id="20d2f-124">**Step 1: Palm up with fingertips together**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="20d2f-125">![Sbocciare aperto](images/bloom-open.png)</span><span class="sxs-lookup"><span data-stu-id="20d2f-125">![Bloom open](images/bloom-open.png)</span></span><br>
        <span data-ttu-id="20d2f-126">**Passaggio 2: Palm up con la distribuzione a portata di mano**</span><span class="sxs-lookup"><span data-stu-id="20d2f-126">**Step 2: Palm up with fingertips spread**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="start-gesture"></a><span data-ttu-id="20d2f-127">Azione di avvio</span><span class="sxs-lookup"><span data-stu-id="20d2f-127">Start gesture</span></span>
<span data-ttu-id="20d2f-128">In HoloLens 2, il movimento Bloom è stato sostituito con un pulsante di polso virtuale che consente interazioni più istintive che non richiedono ulteriori attività di insegnamento.</span><span class="sxs-lookup"><span data-stu-id="20d2f-128">In HoloLens 2, we replaced the Bloom gesture with a virtual wrist button that allows for more instinctual interactions that require no additional teaching.</span></span> <span data-ttu-id="20d2f-129">Visualizzando gli utenti con il pulsante del polso, è possibile accedervi in modo intuitivo e premerlo con l'altra parte.</span><span class="sxs-lookup"><span data-stu-id="20d2f-129">By showing users the button on the wrist, they can intuitively reach out and press it with their other hand.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="20d2f-130">![Pulsante del polso pronto](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="20d2f-130">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="20d2f-131">**Passaggio 1: eseguire il Palm up per visualizzare il pulsante del polso**</span><span class="sxs-lookup"><span data-stu-id="20d2f-131">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="20d2f-132">![Pressione del pulsante del polso](images/wrist-button-press.png)</span><span class="sxs-lookup"><span data-stu-id="20d2f-132">![Wrist button press](images/wrist-button-press.png)</span></span><br>
        <span data-ttu-id="20d2f-133">**Passaggio 2: premere il pulsante del polso**</span><span class="sxs-lookup"><span data-stu-id="20d2f-133">**Step 2: Press the wrist button**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="one-handed-start-gesture"></a><span data-ttu-id="20d2f-134">Gesto iniziale a una mano</span><span class="sxs-lookup"><span data-stu-id="20d2f-134">One-handed Start gesture</span></span>

> [!IMPORTANT]
> <span data-ttu-id="20d2f-135">Per il funzionamento del movimento iniziale a una sola mano:</span><span class="sxs-lookup"><span data-stu-id="20d2f-135">For the one-handed Start gesture to work:</span></span>
>
> 1. <span data-ttu-id="20d2f-136">È necessario eseguire l'aggiornamento all'aggiornamento di novembre 2019 (Build 18363,1039) o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="20d2f-136">You must update to the November 2019 update (build 18363.1039) or later.</span></span>
> 1. <span data-ttu-id="20d2f-137">È necessario calibrare gli occhi del dispositivo in modo che funzionino correttamente.</span><span class="sxs-lookup"><span data-stu-id="20d2f-137">Your eyes must be calibrated on the device so that eye tracking functions correctly.</span></span> <span data-ttu-id="20d2f-138">Se non vengono visualizzati punti orbitanti intorno all'icona di avvio quando si esaminano i punti, gli occhi non vengono calibrati sul dispositivo.</span><span class="sxs-lookup"><span data-stu-id="20d2f-138">If you do not see orbiting dots around the Start icon when you look at it, your eyes are not calibrated on the device.</span></span>

<span data-ttu-id="20d2f-139">È anche possibile eseguire il gesto di avvio con una sola mano.</span><span class="sxs-lookup"><span data-stu-id="20d2f-139">You can also perform the Start gesture with only one hand.</span></span> <span data-ttu-id="20d2f-140">A tale scopo, è necessario guardare la Palma con l' **icona di avvio** sul polso interno.</span><span class="sxs-lookup"><span data-stu-id="20d2f-140">To do this, hold out your hand with your palm facing you and look at the **Start icon** on your inner wrist.</span></span> <span data-ttu-id="20d2f-141">**Tenendo sempre d'occhio l'icona**, pizzicare il pollice e l'indice insieme.</span><span class="sxs-lookup"><span data-stu-id="20d2f-141">**While keeping your eye on the icon**, pinch your thumb and index finger together.</span></span><br>
:::row:::
    :::column:::
        <span data-ttu-id="20d2f-142">![Pulsante del polso pronto](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="20d2f-142">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="20d2f-143">**Passaggio 1: eseguire il Palm up per visualizzare il pulsante del polso**</span><span class="sxs-lookup"><span data-stu-id="20d2f-143">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="20d2f-144">![Pizzico pulsante polso](images/wrist-button-pinch.png)</span><span class="sxs-lookup"><span data-stu-id="20d2f-144">![Wrist button pinch](images/wrist-button-pinch.png)</span></span><br>
        <span data-ttu-id="20d2f-145">**Passaggio 2: osservare il pulsante e quindi pizzicare**</span><span class="sxs-lookup"><span data-stu-id="20d2f-145">**Step 2: Eye gaze at the button then pinch**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="20d2f-146">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="20d2f-146">See also</span></span>

* [<span data-ttu-id="20d2f-147">Interazioni istintive</span><span class="sxs-lookup"><span data-stu-id="20d2f-147">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="20d2f-148">Sguardo attento</span><span class="sxs-lookup"><span data-stu-id="20d2f-148">Eye-gaze</span></span>](eye-tracking.md)
* [<span data-ttu-id="20d2f-149">Input vocale</span><span class="sxs-lookup"><span data-stu-id="20d2f-149">Voice input</span></span>](voice-input.md)

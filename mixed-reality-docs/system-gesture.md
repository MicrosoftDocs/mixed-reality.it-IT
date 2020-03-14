---
title: Movimento di sistema
description: Movimento di sistema per chiamare il menu Start.
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: Realtà mista, movimenti, interazione, progettazione
ms.openlocfilehash: 9cfee1104cb9b8135dae51bea73850062fadd25c
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375908"
---
# <a name="system-gesture"></a><span data-ttu-id="86212-104">Movimento di sistema</span><span class="sxs-lookup"><span data-stu-id="86212-104">System gesture</span></span>

<span data-ttu-id="86212-105">Il gesto del sistema è un movimento della mano usato per richiamare il menu Start.</span><span class="sxs-lookup"><span data-stu-id="86212-105">The system gesture is a hand gesture used to invoke the Start Menu.</span></span> <span data-ttu-id="86212-106">È l'equivalente di premere il tasto Windows sulla tastiera, il pulsante Xbox su un controller Xbox o il pulsante Windows sul controller di movimento per le cuffie immersive.</span><span class="sxs-lookup"><span data-stu-id="86212-106">It is the equivalent of pressing the Windows key on the keyboard, the Xbox button on an Xbox controller, or the Windows button on the immersive headset motion controller.</span></span> <span data-ttu-id="86212-107">È importante comprendere quali movimenti sono riservati per il sistema in ogni dispositivo di realtà mista per evitare conflitti durante la progettazione delle interazioni.</span><span class="sxs-lookup"><span data-stu-id="86212-107">It's important to understand which gestures are reserved for the system on each Mixed Reality device to prevent conflicts when designing your interactions.</span></span>

## <a name="device-support"></a><span data-ttu-id="86212-108">Supporto per i dispositivi</span><span class="sxs-lookup"><span data-stu-id="86212-108">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="86212-109"><strong>Funzionalità</strong></span><span class="sxs-lookup"><span data-stu-id="86212-109"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="86212-110"><a href="hololens-hardware-details.md"><strong>HoloLens (prima generazione)</strong></a></span><span class="sxs-lookup"><span data-stu-id="86212-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="86212-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="86212-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="86212-112"><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="86212-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="86212-113">Bloom</span><span class="sxs-lookup"><span data-stu-id="86212-113">Bloom</span></span></td>
        <td><span data-ttu-id="86212-114">✔️</span><span class="sxs-lookup"><span data-stu-id="86212-114">✔️</span></span></td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="86212-115">Pulsante polso</span><span class="sxs-lookup"><span data-stu-id="86212-115">Wrist button</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="86212-116">✔️</span><span class="sxs-lookup"><span data-stu-id="86212-116">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="86212-117">Occhio e palmare</span><span class="sxs-lookup"><span data-stu-id="86212-117">Eye gaze and palm up pinch</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="86212-118">✔️</span><span class="sxs-lookup"><span data-stu-id="86212-118">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a><span data-ttu-id="86212-119">Bloom</span><span class="sxs-lookup"><span data-stu-id="86212-119">Bloom</span></span>
<span data-ttu-id="86212-120">Per visualizzare il menu Start in HoloLens (1st Gen), abbiamo progettato "Bloom", un gesto simbolico che simula il fiore fiorito.</span><span class="sxs-lookup"><span data-stu-id="86212-120">To bring up the start menu in HoloLens (1st gen), we designed “Bloom”, which is a symbolic gesture mimicking the flower blossom.</span></span> <span data-ttu-id="86212-121">È distinto per l'interazione surefooted, facile da eseguire e rapido da richiamare.</span><span class="sxs-lookup"><span data-stu-id="86212-121">It's distinctive for surefooted interaction, easy to perform, and quick to recall.</span></span> <span data-ttu-id="86212-122">Per eseguire il gesto di fioritura su HoloLens (1 ° gen), è necessario passare a un palmo e a una mano insieme, quindi aprire la mano diffondendo le dita.</span><span class="sxs-lookup"><span data-stu-id="86212-122">To do the bloom gesture on HoloLens (1st gen), hold out your hand with your palm up and fingertips together, then open your hand by spreading your fingers.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="86212-123">![Bloom Close](images/bloom-close.png)</span><span class="sxs-lookup"><span data-stu-id="86212-123">![Bloom close](images/bloom-close.png)</span></span><br>
        <span data-ttu-id="86212-124">**Passaggio 1: palmare insieme**</span><span class="sxs-lookup"><span data-stu-id="86212-124">**Step 1: Palm up with fingertips together**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="86212-125">![Bloom Open](images/bloom-open.png)</span><span class="sxs-lookup"><span data-stu-id="86212-125">![Bloom open](images/bloom-open.png)</span></span><br>
        <span data-ttu-id="86212-126">**Passaggio 2: Palm up con la distribuzione a portata di mano**</span><span class="sxs-lookup"><span data-stu-id="86212-126">**Step 2: Palm up with fingertips spread**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="start-gesture"></a><span data-ttu-id="86212-127">Azione di avvio</span><span class="sxs-lookup"><span data-stu-id="86212-127">Start gesture</span></span>
<span data-ttu-id="86212-128">In HoloLens 2, il movimento Bloom è stato sostituito con un pulsante di polso virtuale che consente interazioni più istintive che non richiedono ulteriori attività di insegnamento.</span><span class="sxs-lookup"><span data-stu-id="86212-128">In HoloLens 2, we replaced the Bloom gesture with a virtual wrist button that allows for more instinctual interactions that require no additional teaching.</span></span> <span data-ttu-id="86212-129">Visualizzando gli utenti con il pulsante del polso, è possibile accedervi in modo intuitivo e premerlo con l'altra parte.</span><span class="sxs-lookup"><span data-stu-id="86212-129">By showing users the button on the wrist, they can intuitively reach out and press it with their other hand.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="86212-130">![pronto per il pulsante del polso](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="86212-130">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="86212-131">**Passaggio 1: eseguire il Palm up per visualizzare il pulsante del polso**</span><span class="sxs-lookup"><span data-stu-id="86212-131">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="86212-132">![premere il pulsante del polso](images/wrist-button-press.png)</span><span class="sxs-lookup"><span data-stu-id="86212-132">![Wrist button press](images/wrist-button-press.png)</span></span><br>
        <span data-ttu-id="86212-133">**Passaggio 2: premere il pulsante del polso**</span><span class="sxs-lookup"><span data-stu-id="86212-133">**Step 2: Press the wrist button**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="one-handed-start-gesture"></a><span data-ttu-id="86212-134">Gesto iniziale a una mano</span><span class="sxs-lookup"><span data-stu-id="86212-134">One-handed Start gesture</span></span>

> [!IMPORTANT]
> <span data-ttu-id="86212-135">Per il funzionamento del movimento iniziale a una sola mano:</span><span class="sxs-lookup"><span data-stu-id="86212-135">For the one-handed Start gesture to work:</span></span>
>
> 1. <span data-ttu-id="86212-136">È necessario eseguire l'aggiornamento all'aggiornamento di novembre 2019 (Build 18363,1039) o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="86212-136">You must update to the November 2019 update (build 18363.1039) or later.</span></span>
> 1. <span data-ttu-id="86212-137">È necessario calibrare gli occhi del dispositivo in modo che funzionino correttamente.</span><span class="sxs-lookup"><span data-stu-id="86212-137">Your eyes must be calibrated on the device so that eye tracking functions correctly.</span></span> <span data-ttu-id="86212-138">Se non vengono visualizzati punti orbitanti intorno all'icona di avvio quando si esaminano i punti, gli occhi non vengono calibrati sul dispositivo.</span><span class="sxs-lookup"><span data-stu-id="86212-138">If you do not see orbiting dots around the Start icon when you look at it, your eyes are not calibrated on the device.</span></span>

<span data-ttu-id="86212-139">È anche possibile eseguire il gesto di avvio con una sola mano.</span><span class="sxs-lookup"><span data-stu-id="86212-139">You can also perform the Start gesture with only one hand.</span></span> <span data-ttu-id="86212-140">A tale scopo, è necessario guardare la Palma con l' **icona di avvio** sul polso interno.</span><span class="sxs-lookup"><span data-stu-id="86212-140">To do this, hold out your hand with your palm facing you and look at the **Start icon** on your inner wrist.</span></span> <span data-ttu-id="86212-141">**Tenendo sempre d'occhio l'icona**, pizzicare il pollice e l'indice insieme.</span><span class="sxs-lookup"><span data-stu-id="86212-141">**While keeping your eye on the icon**, pinch your thumb and index finger together.</span></span><br>
:::row:::
    :::column:::
        <span data-ttu-id="86212-142">![pronto per il pulsante del polso](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="86212-142">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="86212-143">**Passaggio 1: eseguire il Palm up per visualizzare il pulsante del polso**</span><span class="sxs-lookup"><span data-stu-id="86212-143">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="86212-144">](images/wrist-button-pinch.png) pizzico pulsante ![polso</span><span class="sxs-lookup"><span data-stu-id="86212-144">![Wrist button pinch](images/wrist-button-pinch.png)</span></span><br>
        <span data-ttu-id="86212-145">**Passaggio 2: osservare il pulsante e quindi pizzicare**</span><span class="sxs-lookup"><span data-stu-id="86212-145">**Step 2: Eye gaze at the button then pinch**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="86212-146">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="86212-146">See also</span></span>

* [<span data-ttu-id="86212-147">Interazioni istintive</span><span class="sxs-lookup"><span data-stu-id="86212-147">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="86212-148">Sguardo fisso</span><span class="sxs-lookup"><span data-stu-id="86212-148">Eye-gaze</span></span>](eye-tracking.md)
* [<span data-ttu-id="86212-149">Input vocale</span><span class="sxs-lookup"><span data-stu-id="86212-149">Voice input</span></span>](voice-input.md)

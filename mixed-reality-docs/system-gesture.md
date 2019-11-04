---
title: Movimento di sistema
description: Movimento di sistema per chiamare il menu Start.
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: Realtà mista, movimenti, interazione, progettazione
ms.openlocfilehash: b46f642babb18387da2e76d5bdbb7631577c85de
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73439822"
---
# <a name="system-gesture"></a><span data-ttu-id="64fe3-104">Movimento di sistema</span><span class="sxs-lookup"><span data-stu-id="64fe3-104">System gesture</span></span>

<span data-ttu-id="64fe3-105">Il gesto del sistema è un movimento della mano usato per richiamare il menu Start.</span><span class="sxs-lookup"><span data-stu-id="64fe3-105">The system gesture is a hand gesture used to invoke the Start Menu.</span></span> <span data-ttu-id="64fe3-106">È l'equivalente di premere il tasto Windows sulla tastiera, il pulsante Xbox su un controller Xbox o il pulsante Windows sul controller di movimento per le cuffie immersive.</span><span class="sxs-lookup"><span data-stu-id="64fe3-106">It is the equivalent of pressing the Windows key on the keyboard, the Xbox button on an Xbox controller, or the Windows button on the immersive headset motion controller.</span></span> <span data-ttu-id="64fe3-107">È importante comprendere quali movimenti sono riservati per il sistema in ogni dispositivo di realtà mista per evitare conflitti durante la progettazione delle interazioni.</span><span class="sxs-lookup"><span data-stu-id="64fe3-107">It's important to understand which gestures are reserved for the system on each Mixed Reality device to prevent conflicts when designing your interactions.</span></span>

## <a name="device-support"></a><span data-ttu-id="64fe3-108">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="64fe3-108">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="64fe3-109"><strong>Funzionalità</strong></span><span class="sxs-lookup"><span data-stu-id="64fe3-109"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="64fe3-110"><a href="hololens-hardware-details.md"><strong>HoloLens (prima generazione)</strong></a></span><span class="sxs-lookup"><span data-stu-id="64fe3-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="64fe3-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="64fe3-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="64fe3-112"><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="64fe3-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="64fe3-113">Bloom</span><span class="sxs-lookup"><span data-stu-id="64fe3-113">Bloom</span></span></td>
        <td><span data-ttu-id="64fe3-114">✔️</span><span class="sxs-lookup"><span data-stu-id="64fe3-114">✔️</span></span></td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="64fe3-115">Pulsante polso</span><span class="sxs-lookup"><span data-stu-id="64fe3-115">Wrist button</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="64fe3-116">✔️</span><span class="sxs-lookup"><span data-stu-id="64fe3-116">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="64fe3-117">Occhio e palmare</span><span class="sxs-lookup"><span data-stu-id="64fe3-117">Eye gaze and palm up pinch</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="64fe3-118">✔️</span><span class="sxs-lookup"><span data-stu-id="64fe3-118">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a><span data-ttu-id="64fe3-119">Bloom</span><span class="sxs-lookup"><span data-stu-id="64fe3-119">Bloom</span></span>
<span data-ttu-id="64fe3-120">Per visualizzare il menu Start in HoloLens (1st Gen), abbiamo progettato "Bloom", un gesto simbolico che simula il fiore fiorito.</span><span class="sxs-lookup"><span data-stu-id="64fe3-120">To bring up the start menu in HoloLens (1st gen), we designed “Bloom”, which is a symbolic gesture mimicking the flower blossom.</span></span> <span data-ttu-id="64fe3-121">È distinto per l'interazione surefooted, facile da eseguire e rapido da richiamare.</span><span class="sxs-lookup"><span data-stu-id="64fe3-121">It's distinctive for surefooted interaction, easy to perform, and quick to recall.</span></span> <span data-ttu-id="64fe3-122">Per eseguire il gesto di fioritura su HoloLens (1 ° gen), è necessario passare a un palmo e a una mano insieme, quindi aprire la mano diffondendo le dita.</span><span class="sxs-lookup"><span data-stu-id="64fe3-122">To do the bloom gesture on HoloLens (1st gen), hold out your hand with your palm up and fingertips together, then open your hand by spreading your fingers.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="64fe3-123">![Bloom Close](images/bloom-close.png)</span><span class="sxs-lookup"><span data-stu-id="64fe3-123">![Bloom close](images/bloom-close.png)</span></span><br>
        <span data-ttu-id="64fe3-124">**Passaggio 1: palmare insieme**</span><span class="sxs-lookup"><span data-stu-id="64fe3-124">**Step 1: Palm up with fingertips together**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="64fe3-125">![Bloom Open](images/bloom-open.png)</span><span class="sxs-lookup"><span data-stu-id="64fe3-125">![Bloom open](images/bloom-open.png)</span></span><br>
        <span data-ttu-id="64fe3-126">**Passaggio 2: palmare con spread a portata di mano**</span><span class="sxs-lookup"><span data-stu-id="64fe3-126">**Step 2: Palm up with fingertips spreaded**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="wrist-button"></a><span data-ttu-id="64fe3-127">Pulsante polso</span><span class="sxs-lookup"><span data-stu-id="64fe3-127">Wrist button</span></span>
<span data-ttu-id="64fe3-128">In HoloLens 2, il movimento Bloom è stato sostituito con un pulsante di polso virtuale che consente interazioni più istintive che non richiedono ulteriori attività di insegnamento.</span><span class="sxs-lookup"><span data-stu-id="64fe3-128">In HoloLens 2, we replaced the Bloom gesture with a virtual wrist button that allows for more instinctual interactions that require no additional teaching.</span></span> <span data-ttu-id="64fe3-129">Visualizzando gli utenti con il pulsante del polso, è possibile accedervi in modo intuitivo e premerlo con l'altra parte.</span><span class="sxs-lookup"><span data-stu-id="64fe3-129">By showing users the button on the wrist, they can intuitively reach out and press it with their other hand.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="64fe3-130">![pronto per il pulsante del polso](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="64fe3-130">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="64fe3-131">**Passaggio 1: eseguire il Palm up per visualizzare il pulsante del polso**</span><span class="sxs-lookup"><span data-stu-id="64fe3-131">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="64fe3-132">![premere il pulsante del polso](images/wrist-button-press.png)</span><span class="sxs-lookup"><span data-stu-id="64fe3-132">![Wrist button press](images/wrist-button-press.png)</span></span><br>
        <span data-ttu-id="64fe3-133">**Passaggio 2: premere il pulsante del polso**</span><span class="sxs-lookup"><span data-stu-id="64fe3-133">**Step 2: Press the wrist button**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="eye-gaze-and-palm-up-pinch"></a><span data-ttu-id="64fe3-134">Occhio e palmare</span><span class="sxs-lookup"><span data-stu-id="64fe3-134">Eye-gaze and palm up pinch</span></span>
<span data-ttu-id="64fe3-135">È stata anche progettata una soluzione a mano singola per semplificare l'accesso in HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="64fe3-135">We have also designed a one-handed solution for ease of access in HoloLens 2.</span></span> <span data-ttu-id="64fe3-136">Questo gesto richiede agli utenti di osservare il pulsante del polso, quindi di usare la stessa mano per eseguire un pizzico di palmare usando il pollice e il dito dell'indice.</span><span class="sxs-lookup"><span data-stu-id="64fe3-136">This gesture requires users to eye gaze at the wrist button, then use the same hand to perform a palm up pinch using their thumb and index finger.</span></span><br>
:::row:::
    :::column:::
        <span data-ttu-id="64fe3-137">![pronto per il pulsante del polso](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="64fe3-137">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="64fe3-138">**Passaggio 1: eseguire il Palm up per visualizzare il pulsante del polso**</span><span class="sxs-lookup"><span data-stu-id="64fe3-138">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="64fe3-139">](images/wrist-button-pinch.png) pizzico pulsante ![polso</span><span class="sxs-lookup"><span data-stu-id="64fe3-139">![Wrist button pinch](images/wrist-button-pinch.png)</span></span><br>
        <span data-ttu-id="64fe3-140">**Passaggio: occhio al pulsante e quindi pizzicare**</span><span class="sxs-lookup"><span data-stu-id="64fe3-140">**Step: Eye gaze at the button then pinch**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="64fe3-141">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="64fe3-141">See also</span></span>

* [<span data-ttu-id="64fe3-142">Interazioni istintive</span><span class="sxs-lookup"><span data-stu-id="64fe3-142">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="64fe3-143">Sguardo fisso</span><span class="sxs-lookup"><span data-stu-id="64fe3-143">Eye-gaze</span></span>](eye-tracking.md)
* [<span data-ttu-id="64fe3-144">Input vocale</span><span class="sxs-lookup"><span data-stu-id="64fe3-144">Voice input</span></span>](voice-input.md)

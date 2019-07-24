---
title: Sguardo fisso
description: Lo sguardo è la prima forma di input e rappresenta una forma principale di destinazione all'interno della realtà mista.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Realtà mista, sguardo, interazione, progettazione
ms.openlocfilehash: 7e65d26d3e9edabbd01d35a887ffc8622a3c6337
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414373"
---
# <a name="gaze"></a><span data-ttu-id="388eb-104">Sguardo fisso</span><span class="sxs-lookup"><span data-stu-id="388eb-104">Gaze</span></span>

<span data-ttu-id="388eb-105">Lo **sguardo** è la prima forma di input e rappresenta una forma principale di destinazione all'interno della realtà mista.</span><span class="sxs-lookup"><span data-stu-id="388eb-105">**Gaze** is the first form of input and is a primary form of targeting within mixed reality.</span></span> <span data-ttu-id="388eb-106">Lo sguardo indica il punto in cui l'utente sta cercando nel mondo e consente di determinarne lo scopo.</span><span class="sxs-lookup"><span data-stu-id="388eb-106">Gaze tells you where the user is looking in the world and lets you determine their intent.</span></span> <span data-ttu-id="388eb-107">Nel mondo reale, in genere si esamina un oggetto con cui si intende interagire.</span><span class="sxs-lookup"><span data-stu-id="388eb-107">In the real world, you'll typically look at an object that you intend to interact with.</span></span> <span data-ttu-id="388eb-108">Questo è lo stesso con lo sguardo.</span><span class="sxs-lookup"><span data-stu-id="388eb-108">This is the same with gaze.</span></span>

<span data-ttu-id="388eb-109">Gli auricolari per la realtà mista usano la posizione e l'orientamento dell'Head dell'utente per determinare il vettore di sguardi a capo.</span><span class="sxs-lookup"><span data-stu-id="388eb-109">Mixed reality headsets use the position and orientation of your user's head to determine their head gaze vector.</span></span> <span data-ttu-id="388eb-110">È possibile considerare questo vettore come un puntatore laser direttamente direttamente tra gli occhi dell'utente.</span><span class="sxs-lookup"><span data-stu-id="388eb-110">You can think of this vector as a laser pointer straight ahead from directly between the user's eyes.</span></span> <span data-ttu-id="388eb-111">Quando l'utente esamina la stanza, l'applicazione può intersecare questo raggio, sia con i propri ologrammi che con la mesh di [mapping spaziale](spatial-mapping.md) , per determinare l'oggetto virtuale o reale che può essere esaminato dall'utente.</span><span class="sxs-lookup"><span data-stu-id="388eb-111">As the user looks around the room, your application can intersect this ray, both with its own holograms and with the [spatial mapping](spatial-mapping.md) mesh to determine what virtual or real-world object your user may be looking at.</span></span>

<span data-ttu-id="388eb-112">In HoloLens 2, le interazioni possono essere mirate dallo sguardo a capo dell'utente, dallo sguardo a occhi o dalle interazioni quasi o a lungo.</span><span class="sxs-lookup"><span data-stu-id="388eb-112">On HoloLens 2, interactions can be targeted by either the user's head gaze, eye gaze or through near or far hand interactions.</span></span>
<span data-ttu-id="388eb-113">In HoloLens (1st Gen), le interazioni dovrebbero in genere derivare il proprio targeting da quello degli utenti, anziché tentare di eseguire il rendering o interagire direttamente nella posizione della mano.</span><span class="sxs-lookup"><span data-stu-id="388eb-113">On HoloLens (1st gen), interactions should generally derive their targeting from the user's head gaze, rather than trying to render or interact at the hand's location directly.</span></span> <span data-ttu-id="388eb-114">Una volta avviata un'interazione, è possibile usare i movimenti relativi della mano per [controllare il movimento](gestures.md), come per il gesto di [manipolazione o spostamento](gestures.md#composite-gestures) .</span><span class="sxs-lookup"><span data-stu-id="388eb-114">Once an interaction has started, relative motions of the hand may be used to control the [gesture](gestures.md), as with the [manipulation or navigation](gestures.md#composite-gestures) gesture.</span></span> <span data-ttu-id="388eb-115">Con le cuffie di tipo immersivo, è possibile usare uno sguardo a capo o [controller di movimento](motion-controllers.md)che supportano la funzionalità di puntamento.</span><span class="sxs-lookup"><span data-stu-id="388eb-115">With immersive headsets, you can target using either head gaze or pointing-capable [motion controllers](motion-controllers.md).</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/zCPiZlWdVws]

## <a name="device-support"></a><span data-ttu-id="388eb-116">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="388eb-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="388eb-117"><strong>Funzionalità</strong></span><span class="sxs-lookup"><span data-stu-id="388eb-117"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="388eb-118"><a href="hololens-hardware-details.md"><strong>HoloLens (prima generazione)</strong></a></span><span class="sxs-lookup"><span data-stu-id="388eb-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="388eb-119"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="388eb-119"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="388eb-120"><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="388eb-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="388eb-121">Sguardo a capo</span><span class="sxs-lookup"><span data-stu-id="388eb-121">Head gaze</span></span></td>
        <td><span data-ttu-id="388eb-122">✔️</span><span class="sxs-lookup"><span data-stu-id="388eb-122">✔️</span></span></td>
        <td><span data-ttu-id="388eb-123">✔️</span><span class="sxs-lookup"><span data-stu-id="388eb-123">✔️</span></span></td>
        <td><span data-ttu-id="388eb-124">✔️</span><span class="sxs-lookup"><span data-stu-id="388eb-124">✔️</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="388eb-125">Occhio</span><span class="sxs-lookup"><span data-stu-id="388eb-125">Eye gaze</span></span></td>
        <td><span data-ttu-id="388eb-126">❌</span><span class="sxs-lookup"><span data-stu-id="388eb-126">❌</span></span></td>
        <td><span data-ttu-id="388eb-127">✔️</span><span class="sxs-lookup"><span data-stu-id="388eb-127">✔️</span></span></td>
        <td><span data-ttu-id="388eb-128">❌</span><span class="sxs-lookup"><span data-stu-id="388eb-128">❌</span></span></td>
    </tr>
</table>

> [!NOTE]
> <span data-ttu-id="388eb-129">Altre indicazioni specifiche per HoloLens 2 [saranno presto](index.md#news-and-notes)disponibili.</span><span class="sxs-lookup"><span data-stu-id="388eb-129">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>


## <a name="uses-of-gaze"></a><span data-ttu-id="388eb-130">Usi di sguardi</span><span class="sxs-lookup"><span data-stu-id="388eb-130">Uses of gaze</span></span>

<span data-ttu-id="388eb-131">In qualità di sviluppatore di realtà mista, è possibile fare molto con la testa o gli sguardi:</span><span class="sxs-lookup"><span data-stu-id="388eb-131">As a mixed reality developer, you can do a lot with head or eye gaze:</span></span>
* <span data-ttu-id="388eb-132">L'app può intersecare sguardi con gli ologrammi nella scena per determinare il punto in cui l'attenzione dell'utente è.</span><span class="sxs-lookup"><span data-stu-id="388eb-132">Your app can intersect gaze with the holograms in your scene to determine where the user's attention is.</span></span>
* <span data-ttu-id="388eb-133">L'app può essere destinata ai movimenti e alle presse del controller in base allo sguardo dell'utente, consentendo all'utente di selezionare, attivare, acquisire, scorrere o interagire in altro modo con i loro ologrammi.</span><span class="sxs-lookup"><span data-stu-id="388eb-133">Your app can target gestures and controller presses based on the user's gaze, letting the user select, activate, grab, scroll, or otherwise interact with their holograms.</span></span>
* <span data-ttu-id="388eb-134">L'app può consentire all'utente di posizionare gli ologrammi su superfici reali, intersecando il raggio di sguardi con la mesh di mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="388eb-134">Your app can let the user place holograms on real-world surfaces, by intersecting their gaze ray with the spatial mapping mesh.</span></span>
* <span data-ttu-id="388eb-135">L'app può sapere quando l'utente *non* sta osservando la direzione di un oggetto importante, che può portare l'app a fornire suggerimenti visivi e audio per la rotazione verso tale oggetto.</span><span class="sxs-lookup"><span data-stu-id="388eb-135">Your app can know when the user is *not* looking in the direction of an important object, which can lead your app to give visual and audio cues to turn towards that object.</span></span>

## <a name="cursor"></a><span data-ttu-id="388eb-136">Cursor</span><span class="sxs-lookup"><span data-stu-id="388eb-136">Cursor</span></span>

<span data-ttu-id="388eb-137">Per lo sguardo a capo, la maggior parte delle app deve usare un [cursore](cursors.md) (o altre indicazioni visive/visive) per fornire all'utente la confidenza con cui si sta per interagire.</span><span class="sxs-lookup"><span data-stu-id="388eb-137">For head gaze, most apps should use a [cursor](cursors.md) (or other auditory/visual indication) to give the user confidence in what they're about to interact with.</span></span> <span data-ttu-id="388eb-138">In genere, il cursore viene posizionato in tutto il mondo in cui il raggio di sguardo principale interseca un oggetto, che può essere un ologramma o una superficie reale.</span><span class="sxs-lookup"><span data-stu-id="388eb-138">You typically position this cursor in the world where their head gaze ray first intersects an object, which may be a hologram or a real-world surface.</span></span>

<span data-ttu-id="388eb-139">![Un cursore visivo di esempio per mostrare lo sguardo](images/cursor.jpg)</span><span class="sxs-lookup"><span data-stu-id="388eb-139">![An example visual cursor to show gaze](images/cursor.jpg)</span></span><br>
<span data-ttu-id="388eb-140">*Un cursore visivo di esempio per mostrare lo sguardo*</span><span class="sxs-lookup"><span data-stu-id="388eb-140">*An example visual cursor to show gaze*</span></span>

<span data-ttu-id="388eb-141">Per gli occhi, in genere è consigliabile *non* mostrare un cursore, in quanto questa operazione può diventare rapidamente distrazione e fastidioso per l'utente.</span><span class="sxs-lookup"><span data-stu-id="388eb-141">For eye gaze, we generally recommend *not* to show a cursor, as this can quickly become distracting and annoying for the user.</span></span> <span data-ttu-id="388eb-142">È invece possibile evidenziare leggermente le destinazioni visive o usare un cursore occhio molto debole per fornire informazioni su ciò che l'utente sta per interagire.</span><span class="sxs-lookup"><span data-stu-id="388eb-142">Instead subtly highlight visual targets or use a very faint eye cursor to provide confidence about what the user is about to interact with.</span></span> <span data-ttu-id="388eb-143">Per altre informazioni, vedere le [linee guida di progettazione per l'input basato su occhi](eye-tracking.md) su HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="388eb-143">For more information, please check out our [design guidance for eye-based input](eye-tracking.md) on HoloLens 2.</span></span>

## <a name="giving-action-to-the-users-gaze"></a><span data-ttu-id="388eb-144">Assegnazione di un'azione allo sguardo dell'utente</span><span class="sxs-lookup"><span data-stu-id="388eb-144">Giving action to the user's gaze</span></span>

<span data-ttu-id="388eb-145">Una volta che l'utente ha assegnato un ologramma o un oggetto reale usando il proprio sguardo, il passaggio successivo consiste nell'agire su tale oggetto.</span><span class="sxs-lookup"><span data-stu-id="388eb-145">Once the user has targeted a hologram or real-world object using their gaze, their next step is to take action on that object.</span></span> <span data-ttu-id="388eb-146">Le modalità principali per l'esecuzione di un'azione da parte di un utente sono i [movimenti](gestures.md), i [controller di movimento](motion-controllers.md) e la [voce](voice-input.md).</span><span class="sxs-lookup"><span data-stu-id="388eb-146">The primary ways for a user to take action are through [gestures](gestures.md), [motion controllers](motion-controllers.md) and [voice](voice-input.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="388eb-147">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="388eb-147">See also</span></span>
* [<span data-ttu-id="388eb-148">Input MR 210: Sguardo a capo</span><span class="sxs-lookup"><span data-stu-id="388eb-148">MR Input 210: Head gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="388eb-149">Puntamento con la testa e sguardo fisso in DirectX</span><span class="sxs-lookup"><span data-stu-id="388eb-149">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="388eb-150">Sguardo a testa in Unity</span><span class="sxs-lookup"><span data-stu-id="388eb-150">Head gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="388eb-151">Eye-sguardi su HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="388eb-151">Eye-gaze on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="388eb-152">Sguardo in Unity con il Toolkit di realtà misto</span><span class="sxs-lookup"><span data-stu-id="388eb-152">Eye gaze in Unity using Mixed Reality Toolkit</span></span>](https://aka.ms/mrtk-eyes)

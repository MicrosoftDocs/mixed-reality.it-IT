---
title: Sguardo fisso
description: Sguardo è il primo modulo di input e un modulo primario di destinazione all'interno di realtà mista.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Misto realtà, sguardo, interazione, progettazione
ms.openlocfilehash: 9e50067f9dfeacf3dce5ea9a928990d1b142e4d0
ms.sourcegitcommit: 60060386305eabfac2758a2c861a43c36286b151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/31/2019
ms.locfileid: "66453712"
---
# <a name="gaze"></a><span data-ttu-id="d6754-104">Sguardo fisso</span><span class="sxs-lookup"><span data-stu-id="d6754-104">Gaze</span></span>

<span data-ttu-id="d6754-105">**Estasiati** è il primo modulo di input ed è un modulo primario di destinazione all'interno di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="d6754-105">**Gaze** is the first form of input and is a primary form of targeting within mixed reality.</span></span> <span data-ttu-id="d6754-106">Sguardo indica dove l'utente cerca in tutto il mondo e consente di determinare il loro scopo.</span><span class="sxs-lookup"><span data-stu-id="d6754-106">Gaze tells you where the user is looking in the world and lets you determine their intent.</span></span> <span data-ttu-id="d6754-107">Nel mondo reale, è in genere verrà esaminato un oggetto che si prevede di interagire con.</span><span class="sxs-lookup"><span data-stu-id="d6754-107">In the real world, you'll typically look at an object that you intend to interact with.</span></span> <span data-ttu-id="d6754-108">Questo è lo stesso con sguardo.</span><span class="sxs-lookup"><span data-stu-id="d6754-108">This is the same with gaze.</span></span>

<span data-ttu-id="d6754-109">Realtà mista auricolari usano la posizione e l'orientamento principale dell'utente di per determinare i vettori sguardo head.</span><span class="sxs-lookup"><span data-stu-id="d6754-109">Mixed reality headsets use the position and orientation of your user's head to determine their head gaze vector.</span></span> <span data-ttu-id="d6754-110">È possibile considerare questo vettore come un puntatore laser dritto da direttamente tra gli occhi dell'utente.</span><span class="sxs-lookup"><span data-stu-id="d6754-110">You can think of this vector as a laser pointer straight ahead from directly between the user's eyes.</span></span> <span data-ttu-id="d6754-111">Quando l'utente cerca nella stanza, l'applicazione può intersecarsi questo ray, con i proprio ologrammi e con il [mapping spaziale](spatial-mapping.md) mesh per determinare quale oggetto reale o virtuale, l'utente potrebbe essere opportuno.</span><span class="sxs-lookup"><span data-stu-id="d6754-111">As the user looks around the room, your application can intersect this ray, both with its own holograms and with the [spatial mapping](spatial-mapping.md) mesh to determine what virtual or real-world object your user may be looking at.</span></span>

<span data-ttu-id="d6754-112">Nel 2 HoloLens, le interazioni possono essere destinate dalle sguardo head dell'utente, sguardo sotto controllo tramite quasi o passare a questo momento le interazioni.</span><span class="sxs-lookup"><span data-stu-id="d6754-112">On HoloLens 2, interactions can be targeted by either the user's head gaze, eye gaze or through near or far hand interactions.</span></span>
<span data-ttu-id="d6754-113">Su HoloLens (dal 1 ° generazione), le interazioni devono derivano in genere la destinazione da sguardo head dell'utente, piuttosto che tentare per eseguire il rendering o interagire direttamente nella posizione dell'icona della mano.</span><span class="sxs-lookup"><span data-stu-id="d6754-113">On HoloLens (1st gen), interactions should generally derive their targeting from the user's head gaze, rather than trying to render or interact at the hand's location directly.</span></span> <span data-ttu-id="d6754-114">Dopo aver avviato un'interazione, relativi movimenti della mano possono essere usata per controllare la [movimento](gestures.md), come con la [manipolazione o la navigazione](gestures.md#composite-gestures) movimento.</span><span class="sxs-lookup"><span data-stu-id="d6754-114">Once an interaction has started, relative motions of the hand may be used to control the [gesture](gestures.md), as with the [manipulation or navigation](gestures.md#composite-gestures) gesture.</span></span> <span data-ttu-id="d6754-115">Con immersive auricolari, è possibile fare riferimento tramite uno sguardo head o che punta in grado di supportare [controller di movimento](motion-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="d6754-115">With immersive headsets, you can target using either head gaze or pointing-capable [motion controllers](motion-controllers.md).</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/zCPiZlWdVws]

## <a name="device-support"></a><span data-ttu-id="d6754-116">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="d6754-116">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="d6754-117">Funzionalità</span><span class="sxs-lookup"><span data-stu-id="d6754-117">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="d6754-118"><a href="hololens-hardware-details.md">HoloLens (dal 1 ° generazione)</a></span><span class="sxs-lookup"><span data-stu-id="d6754-118"><a href="hololens-hardware-details.md">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="d6754-119">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d6754-119">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="d6754-120"><a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></span><span class="sxs-lookup"><span data-stu-id="d6754-120"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="d6754-121">Head sguardo</span><span class="sxs-lookup"><span data-stu-id="d6754-121">Head gaze</span></span></td><td style="text-align: center;"> <span data-ttu-id="d6754-122">✔️</span><span class="sxs-lookup"><span data-stu-id="d6754-122">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="d6754-123">✔️</span><span class="sxs-lookup"><span data-stu-id="d6754-123">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="d6754-124">✔️</span><span class="sxs-lookup"><span data-stu-id="d6754-124">✔️</span></span></td>
</tr><tr>
<td> <span data-ttu-id="d6754-125">Sguardo sotto controllo</span><span class="sxs-lookup"><span data-stu-id="d6754-125">Eye gaze</span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="d6754-126">✔️</span><span class="sxs-lookup"><span data-stu-id="d6754-126">✔️</span></span></td><td></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="d6754-127">Altre indicazioni specifiche su 2 HoloLens [presto](index.md#news-and-notes).</span><span class="sxs-lookup"><span data-stu-id="d6754-127">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>


## <a name="uses-of-gaze"></a><span data-ttu-id="d6754-128">Utilizzi di sguardo</span><span class="sxs-lookup"><span data-stu-id="d6754-128">Uses of gaze</span></span>

<span data-ttu-id="d6754-129">Qualità di sviluppatore di realtà mista, è possibile eseguire molte con sguardo head o occhio:</span><span class="sxs-lookup"><span data-stu-id="d6754-129">As a mixed reality developer, you can do a lot with head or eye gaze:</span></span>
* <span data-ttu-id="d6754-130">Le app possono intersecarsi sguardo con vntana nella scena per determinare dove è l'attenzione dell'utente.</span><span class="sxs-lookup"><span data-stu-id="d6754-130">Your app can intersect gaze with the holograms in your scene to determine where the user's attention is.</span></span>
* <span data-ttu-id="d6754-131">L'app può essere indirizzato movimenti e basate sguardo dell'utente, consentendo all'utente di selezionare, attivare, recuperare, scorrere o in caso contrario, interagire con loro vntana pressioni di controller.</span><span class="sxs-lookup"><span data-stu-id="d6754-131">Your app can target gestures and controller presses based on the user's gaze, letting the user select, activate, grab, scroll, or otherwise interact with their holograms.</span></span>
* <span data-ttu-id="d6754-132">L'app può consentire all'utente di inserire vntana nelle aree del mondo reale, eseguendo che intersecano il ray sguardo con la rete di mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="d6754-132">Your app can let the user place holograms on real-world surfaces, by intersecting their gaze ray with the spatial mapping mesh.</span></span>
* <span data-ttu-id="d6754-133">L'app è possibile sapere quando l'utente è *non* alla ricerca nella direzione di un oggetto importante, che può comportare l'app per offrire segnali audio e video per attivare verso tale oggetto.</span><span class="sxs-lookup"><span data-stu-id="d6754-133">Your app can know when the user is *not* looking in the direction of an important object, which can lead your app to give visual and audio cues to turn towards that object.</span></span>

## <a name="cursor"></a><span data-ttu-id="d6754-134">Cursor</span><span class="sxs-lookup"><span data-stu-id="d6754-134">Cursor</span></span>

<span data-ttu-id="d6754-135">Per sguardo head, è consigliabile usare la maggior parte delle App un' [cursore](cursors.md) (o un'altra indicazione acustica/visual) per fornire la fiducia degli utenti sugli aspetti che stanno per interagire con.</span><span class="sxs-lookup"><span data-stu-id="d6754-135">For head gaze, most apps should use a [cursor](cursors.md) (or other auditory/visual indication) to give the user confidence in what they're about to interact with.</span></span> <span data-ttu-id="d6754-136">È in genere posizionare il cursore in tutto il mondo in cui il raggio sguardo head interseca prima di tutto un oggetto, che potrebbe essere ologramma o un'area del mondo reale.</span><span class="sxs-lookup"><span data-stu-id="d6754-136">You typically position this cursor in the world where their head gaze ray first intersects an object, which may be a hologram or a real-world surface.</span></span>

<span data-ttu-id="d6754-137">![Un esempio visivo del cursore per mostrare sguardo](images/cursor.jpg)</span><span class="sxs-lookup"><span data-stu-id="d6754-137">![An example visual cursor to show gaze](images/cursor.jpg)</span></span><br>
<span data-ttu-id="d6754-138">*Un esempio visivo del cursore per mostrare sguardo*</span><span class="sxs-lookup"><span data-stu-id="d6754-138">*An example visual cursor to show gaze*</span></span>

<span data-ttu-id="d6754-139">Per sguardo rossi, è consigliabile in genere *non* mostrare un cursore, perché ciò può risultare poco chiara e indesiderate per l'utente.</span><span class="sxs-lookup"><span data-stu-id="d6754-139">For eye gaze, we generally recommend *not* to show a cursor, as this can quickly become distracting and annoying for the user.</span></span> <span data-ttu-id="d6754-140">Invece leggermente evidenziare destinazioni visual o utilizzare un cursore molto Rube occhio per avere la certezza sulle novità per interagire con l'utente.</span><span class="sxs-lookup"><span data-stu-id="d6754-140">Instead subtly highlight visual targets or use a very faint eye cursor to provide confidence about what the user is about to interact with.</span></span> <span data-ttu-id="d6754-141">Per altre informazioni, vedere la [indicazioni di progettazione per input basato sulle occhio](eye-tracking.md) in 2 HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d6754-141">For more information, please check out our [design guidance for eye-based input](eye-tracking.md) on HoloLens 2.</span></span>

## <a name="giving-action-to-the-users-gaze"></a><span data-ttu-id="d6754-142">Concessione dell'azione a sguardo dell'utente</span><span class="sxs-lookup"><span data-stu-id="d6754-142">Giving action to the user's gaze</span></span>

<span data-ttu-id="d6754-143">Dopo avere l'utente è incluso un ologrammi o un oggetto reale con loro sguardo, il passaggio successivo è intervenire su tale oggetto.</span><span class="sxs-lookup"><span data-stu-id="d6754-143">Once the user has targeted a hologram or real-world object using their gaze, their next step is to take action on that object.</span></span> <span data-ttu-id="d6754-144">Sono i metodi principali per un utente intervenire attraverso [movimenti](gestures.md), [movimento controller](motion-controllers.md) e [vocale](voice-input.md).</span><span class="sxs-lookup"><span data-stu-id="d6754-144">The primary ways for a user to take action are through [gestures](gestures.md), [motion controllers](motion-controllers.md) and [voice](voice-input.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d6754-145">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d6754-145">See also</span></span>
* [<span data-ttu-id="d6754-146">Input MR 210: Head sguardo</span><span class="sxs-lookup"><span data-stu-id="d6754-146">MR Input 210: Head gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="d6754-147">Puntamento con la testa e sguardo fisso in DirectX</span><span class="sxs-lookup"><span data-stu-id="d6754-147">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="d6754-148">Head estasiati Unity</span><span class="sxs-lookup"><span data-stu-id="d6754-148">Head gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="d6754-149">Occhio rilevamento su HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d6754-149">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="d6754-150">Sguardo occhio in Unity usando il Toolkit di realtà mista</span><span class="sxs-lookup"><span data-stu-id="d6754-150">Eye gaze in Unity using Mixed Reality Toolkit</span></span>](https://aka.ms/mrtk-eyes)

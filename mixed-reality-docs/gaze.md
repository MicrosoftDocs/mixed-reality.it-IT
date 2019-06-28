---
title: Sguardo fisso
description: Sguardo è il primo modulo di input e un modulo primario di destinazione all'interno di realtà mista.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Misto realtà, sguardo, interazione, progettazione
ms.openlocfilehash: 7e65d26d3e9edabbd01d35a887ffc8622a3c6337
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414373"
---
# <a name="gaze"></a><span data-ttu-id="298ba-104">Sguardo fisso</span><span class="sxs-lookup"><span data-stu-id="298ba-104">Gaze</span></span>

<span data-ttu-id="298ba-105">**Estasiati** è il primo modulo di input ed è un modulo primario di destinazione all'interno di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="298ba-105">**Gaze** is the first form of input and is a primary form of targeting within mixed reality.</span></span> <span data-ttu-id="298ba-106">Sguardo indica dove l'utente cerca in tutto il mondo e consente di determinare il loro scopo.</span><span class="sxs-lookup"><span data-stu-id="298ba-106">Gaze tells you where the user is looking in the world and lets you determine their intent.</span></span> <span data-ttu-id="298ba-107">Nel mondo reale, è in genere verrà esaminato un oggetto che si prevede di interagire con.</span><span class="sxs-lookup"><span data-stu-id="298ba-107">In the real world, you'll typically look at an object that you intend to interact with.</span></span> <span data-ttu-id="298ba-108">Questo è lo stesso con sguardo.</span><span class="sxs-lookup"><span data-stu-id="298ba-108">This is the same with gaze.</span></span>

<span data-ttu-id="298ba-109">Realtà mista auricolari usano la posizione e l'orientamento principale dell'utente di per determinare i vettori sguardo head.</span><span class="sxs-lookup"><span data-stu-id="298ba-109">Mixed reality headsets use the position and orientation of your user's head to determine their head gaze vector.</span></span> <span data-ttu-id="298ba-110">È possibile considerare questo vettore come un puntatore laser dritto da direttamente tra gli occhi dell'utente.</span><span class="sxs-lookup"><span data-stu-id="298ba-110">You can think of this vector as a laser pointer straight ahead from directly between the user's eyes.</span></span> <span data-ttu-id="298ba-111">Quando l'utente cerca nella stanza, l'applicazione può intersecarsi questo ray, con i proprio ologrammi e con il [mapping spaziale](spatial-mapping.md) mesh per determinare quale oggetto reale o virtuale, l'utente potrebbe essere opportuno.</span><span class="sxs-lookup"><span data-stu-id="298ba-111">As the user looks around the room, your application can intersect this ray, both with its own holograms and with the [spatial mapping](spatial-mapping.md) mesh to determine what virtual or real-world object your user may be looking at.</span></span>

<span data-ttu-id="298ba-112">Nel 2 HoloLens, le interazioni possono essere destinate dalle sguardo head dell'utente, sguardo sotto controllo tramite quasi o passare a questo momento le interazioni.</span><span class="sxs-lookup"><span data-stu-id="298ba-112">On HoloLens 2, interactions can be targeted by either the user's head gaze, eye gaze or through near or far hand interactions.</span></span>
<span data-ttu-id="298ba-113">Su HoloLens (dal 1 ° generazione), le interazioni devono derivano in genere la destinazione da sguardo head dell'utente, piuttosto che tentare per eseguire il rendering o interagire direttamente nella posizione dell'icona della mano.</span><span class="sxs-lookup"><span data-stu-id="298ba-113">On HoloLens (1st gen), interactions should generally derive their targeting from the user's head gaze, rather than trying to render or interact at the hand's location directly.</span></span> <span data-ttu-id="298ba-114">Dopo aver avviato un'interazione, relativi movimenti della mano possono essere usata per controllare la [movimento](gestures.md), come con la [manipolazione o la navigazione](gestures.md#composite-gestures) movimento.</span><span class="sxs-lookup"><span data-stu-id="298ba-114">Once an interaction has started, relative motions of the hand may be used to control the [gesture](gestures.md), as with the [manipulation or navigation](gestures.md#composite-gestures) gesture.</span></span> <span data-ttu-id="298ba-115">Con immersive auricolari, è possibile fare riferimento tramite uno sguardo head o che punta in grado di supportare [controller di movimento](motion-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="298ba-115">With immersive headsets, you can target using either head gaze or pointing-capable [motion controllers](motion-controllers.md).</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/zCPiZlWdVws]

## <a name="device-support"></a><span data-ttu-id="298ba-116">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="298ba-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="298ba-117"><strong>Funzionalità</strong></span><span class="sxs-lookup"><span data-stu-id="298ba-117"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="298ba-118"><a href="hololens-hardware-details.md"><strong>HoloLens (prima generazione)</strong></a></span><span class="sxs-lookup"><span data-stu-id="298ba-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="298ba-119"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="298ba-119"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="298ba-120"><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="298ba-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="298ba-121">Head sguardo</span><span class="sxs-lookup"><span data-stu-id="298ba-121">Head gaze</span></span></td>
        <td><span data-ttu-id="298ba-122">✔️</span><span class="sxs-lookup"><span data-stu-id="298ba-122">✔️</span></span></td>
        <td><span data-ttu-id="298ba-123">✔️</span><span class="sxs-lookup"><span data-stu-id="298ba-123">✔️</span></span></td>
        <td><span data-ttu-id="298ba-124">✔️</span><span class="sxs-lookup"><span data-stu-id="298ba-124">✔️</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="298ba-125">Sguardo sotto controllo</span><span class="sxs-lookup"><span data-stu-id="298ba-125">Eye gaze</span></span></td>
        <td><span data-ttu-id="298ba-126">❌</span><span class="sxs-lookup"><span data-stu-id="298ba-126">❌</span></span></td>
        <td><span data-ttu-id="298ba-127">✔️</span><span class="sxs-lookup"><span data-stu-id="298ba-127">✔️</span></span></td>
        <td><span data-ttu-id="298ba-128">❌</span><span class="sxs-lookup"><span data-stu-id="298ba-128">❌</span></span></td>
    </tr>
</table>

> [!NOTE]
> <span data-ttu-id="298ba-129">Altre indicazioni specifiche su 2 HoloLens [presto](index.md#news-and-notes).</span><span class="sxs-lookup"><span data-stu-id="298ba-129">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>


## <a name="uses-of-gaze"></a><span data-ttu-id="298ba-130">Utilizzi di sguardo</span><span class="sxs-lookup"><span data-stu-id="298ba-130">Uses of gaze</span></span>

<span data-ttu-id="298ba-131">Qualità di sviluppatore di realtà mista, è possibile eseguire molte con sguardo head o occhio:</span><span class="sxs-lookup"><span data-stu-id="298ba-131">As a mixed reality developer, you can do a lot with head or eye gaze:</span></span>
* <span data-ttu-id="298ba-132">Le app possono intersecarsi sguardo con vntana nella scena per determinare dove è l'attenzione dell'utente.</span><span class="sxs-lookup"><span data-stu-id="298ba-132">Your app can intersect gaze with the holograms in your scene to determine where the user's attention is.</span></span>
* <span data-ttu-id="298ba-133">L'app può essere indirizzato movimenti e basate sguardo dell'utente, consentendo all'utente di selezionare, attivare, recuperare, scorrere o in caso contrario, interagire con loro vntana pressioni di controller.</span><span class="sxs-lookup"><span data-stu-id="298ba-133">Your app can target gestures and controller presses based on the user's gaze, letting the user select, activate, grab, scroll, or otherwise interact with their holograms.</span></span>
* <span data-ttu-id="298ba-134">L'app può consentire all'utente di inserire vntana nelle aree del mondo reale, eseguendo che intersecano il ray sguardo con la rete di mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="298ba-134">Your app can let the user place holograms on real-world surfaces, by intersecting their gaze ray with the spatial mapping mesh.</span></span>
* <span data-ttu-id="298ba-135">L'app è possibile sapere quando l'utente è *non* alla ricerca nella direzione di un oggetto importante, che può comportare l'app per offrire segnali audio e video per attivare verso tale oggetto.</span><span class="sxs-lookup"><span data-stu-id="298ba-135">Your app can know when the user is *not* looking in the direction of an important object, which can lead your app to give visual and audio cues to turn towards that object.</span></span>

## <a name="cursor"></a><span data-ttu-id="298ba-136">Cursor</span><span class="sxs-lookup"><span data-stu-id="298ba-136">Cursor</span></span>

<span data-ttu-id="298ba-137">Per sguardo head, è consigliabile usare la maggior parte delle App un' [cursore](cursors.md) (o un'altra indicazione acustica/visual) per fornire la fiducia degli utenti sugli aspetti che stanno per interagire con.</span><span class="sxs-lookup"><span data-stu-id="298ba-137">For head gaze, most apps should use a [cursor](cursors.md) (or other auditory/visual indication) to give the user confidence in what they're about to interact with.</span></span> <span data-ttu-id="298ba-138">È in genere posizionare il cursore in tutto il mondo in cui il raggio sguardo head interseca prima di tutto un oggetto, che potrebbe essere ologramma o un'area del mondo reale.</span><span class="sxs-lookup"><span data-stu-id="298ba-138">You typically position this cursor in the world where their head gaze ray first intersects an object, which may be a hologram or a real-world surface.</span></span>

<span data-ttu-id="298ba-139">![Un esempio visivo del cursore per mostrare sguardo](images/cursor.jpg)</span><span class="sxs-lookup"><span data-stu-id="298ba-139">![An example visual cursor to show gaze](images/cursor.jpg)</span></span><br>
<span data-ttu-id="298ba-140">*Un esempio visivo del cursore per mostrare sguardo*</span><span class="sxs-lookup"><span data-stu-id="298ba-140">*An example visual cursor to show gaze*</span></span>

<span data-ttu-id="298ba-141">Per sguardo rossi, è consigliabile in genere *non* mostrare un cursore, perché ciò può risultare poco chiara e indesiderate per l'utente.</span><span class="sxs-lookup"><span data-stu-id="298ba-141">For eye gaze, we generally recommend *not* to show a cursor, as this can quickly become distracting and annoying for the user.</span></span> <span data-ttu-id="298ba-142">Invece leggermente evidenziare destinazioni visual o utilizzare un cursore molto Rube occhio per avere la certezza sulle novità per interagire con l'utente.</span><span class="sxs-lookup"><span data-stu-id="298ba-142">Instead subtly highlight visual targets or use a very faint eye cursor to provide confidence about what the user is about to interact with.</span></span> <span data-ttu-id="298ba-143">Per altre informazioni, vedere la [indicazioni di progettazione per input basato sulle occhio](eye-tracking.md) in 2 HoloLens.</span><span class="sxs-lookup"><span data-stu-id="298ba-143">For more information, please check out our [design guidance for eye-based input](eye-tracking.md) on HoloLens 2.</span></span>

## <a name="giving-action-to-the-users-gaze"></a><span data-ttu-id="298ba-144">Concessione dell'azione a sguardo dell'utente</span><span class="sxs-lookup"><span data-stu-id="298ba-144">Giving action to the user's gaze</span></span>

<span data-ttu-id="298ba-145">Dopo avere l'utente è incluso un ologrammi o un oggetto reale con loro sguardo, il passaggio successivo è intervenire su tale oggetto.</span><span class="sxs-lookup"><span data-stu-id="298ba-145">Once the user has targeted a hologram or real-world object using their gaze, their next step is to take action on that object.</span></span> <span data-ttu-id="298ba-146">Sono i metodi principali per un utente intervenire attraverso [movimenti](gestures.md), [movimento controller](motion-controllers.md) e [vocale](voice-input.md).</span><span class="sxs-lookup"><span data-stu-id="298ba-146">The primary ways for a user to take action are through [gestures](gestures.md), [motion controllers](motion-controllers.md) and [voice](voice-input.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="298ba-147">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="298ba-147">See also</span></span>
* [<span data-ttu-id="298ba-148">Input MR 210: Head sguardo</span><span class="sxs-lookup"><span data-stu-id="298ba-148">MR Input 210: Head gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="298ba-149">Puntamento con la testa e sguardo fisso in DirectX</span><span class="sxs-lookup"><span data-stu-id="298ba-149">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="298ba-150">Head estasiati Unity</span><span class="sxs-lookup"><span data-stu-id="298ba-150">Head gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="298ba-151">Visiva in HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="298ba-151">Eye-gaze on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="298ba-152">Sguardo occhio in Unity usando il Toolkit di realtà mista</span><span class="sxs-lookup"><span data-stu-id="298ba-152">Eye gaze in Unity using Mixed Reality Toolkit</span></span>](https://aka.ms/mrtk-eyes)

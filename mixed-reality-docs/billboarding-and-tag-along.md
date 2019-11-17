---
title: Billboard e tag-along
description: Gli oggetti con il tabellone sono sempre orientati a fronte dell'utente.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, Billboard, tag-along
ms.openlocfilehash: ff2b1ce20174b1b9aecbb90b1d1dc3e8896b3761
ms.sourcegitcommit: 17427d4d8c3723d53540f1b7f5bc061bba08c1d6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2019
ms.locfileid: "74143133"
---
# <a name="billboarding-and-tag-along"></a><span data-ttu-id="f3fbd-104">Billboard e tag-along</span><span class="sxs-lookup"><span data-stu-id="f3fbd-104">Billboarding and tag-along</span></span>

<br>

<img src="images/UX/MRTK_TagAlong.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<br>

## <a name="what-is-billboarding"></a><span data-ttu-id="f3fbd-105">Che cos'è il tabellone?</span><span class="sxs-lookup"><span data-stu-id="f3fbd-105">What is billboarding?</span></span>

<span data-ttu-id="f3fbd-106">Il tabellone è un concetto di comportamento che può essere applicato a oggetti in realtà mista.</span><span class="sxs-lookup"><span data-stu-id="f3fbd-106">Billboarding is a behavioral concept that can be applied to objects in mixed reality.</span></span> <span data-ttu-id="f3fbd-107">Gli oggetti con il tabellone sono sempre orientati a fronte dell'utente.</span><span class="sxs-lookup"><span data-stu-id="f3fbd-107">Objects with billboarding always orient themselves to face the user.</span></span> <span data-ttu-id="f3fbd-108">Questa operazione è particolarmente utile con i sistemi di testo e di menu in cui gli oggetti statici posizionati nell'ambiente dell'utente (con blocco globale) sarebbero altrimenti nascosti o illeggibili se un utente dovesse spostarsi.</span><span class="sxs-lookup"><span data-stu-id="f3fbd-108">This is especially helpful with text and menuing systems where static objects placed in the user's environment (world-locked) would be otherwise obscured or unreadable if a user were to move around.</span></span>

<span data-ttu-id="f3fbd-109">Gli oggetti con il tabellone abilitato possono essere ruotati liberamente nell'ambiente dell'utente.</span><span class="sxs-lookup"><span data-stu-id="f3fbd-109">Objects with billboarding enabled can rotate freely in the user's environment.</span></span> <span data-ttu-id="f3fbd-110">Possono anche essere vincolati a un singolo asse, a seconda delle considerazioni di progettazione.</span><span class="sxs-lookup"><span data-stu-id="f3fbd-110">They can also be constrained to a single axis depending on design considerations.</span></span> <span data-ttu-id="f3fbd-111">Tenere presente che gli oggetti di cui è stato effettuato il Billboard possono ritagliare o occludere se sono posizionati troppo vicino ad altri oggetti o in HoloLens, troppo vicino alle superfici analizzate.</span><span class="sxs-lookup"><span data-stu-id="f3fbd-111">Keep in mind, billboarded objects may clip or occlude themselves if they are placed too close to other objects, or in HoloLens, too close scanned surfaces.</span></span> <span data-ttu-id="f3fbd-112">Per evitare questo problema, considerare il footprint totale che un oggetto può produrre quando ruotato sull'asse abilitato per il tabellone.</span><span class="sxs-lookup"><span data-stu-id="f3fbd-112">To avoid this, think about the total footprint an object may produce when rotated on the axis enabled for billboarding.</span></span>

<br>

---
## <a name="what-is-a-tag-along"></a><span data-ttu-id="f3fbd-113">Che cos'è un tag-along?</span><span class="sxs-lookup"><span data-stu-id="f3fbd-113">What is a tag-along?</span></span>

<span data-ttu-id="f3fbd-114">Tag-Along è un concetto di comportamento che può essere aggiunto agli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="f3fbd-114">Tag-along is a behavioral concept that can be added to holograms.</span></span> <span data-ttu-id="f3fbd-115">Un oggetto tag-along tenta di rimanere in un intervallo che consente all'utente di interagire comodamente.</span><span class="sxs-lookup"><span data-stu-id="f3fbd-115">A tag-along object attempts to stay in a range that allows the user to interact comfortably.</span></span>

<span data-ttu-id="f3fbd-116">![il pannello HoloLens Pins è un ottimo esempio di comportamento di tag-along](images/tagalong-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="f3fbd-116">![The HoloLens pins panel is a great example of how tag-along behaves](images/tagalong-1000px.jpg)</span></span><br>
<span data-ttu-id="f3fbd-117">*Il menu Start di HoloLens è un ottimo esempio di comportamento di tag-along*</span><span class="sxs-lookup"><span data-stu-id="f3fbd-117">*The HoloLens Start menu is a great example of tag-along behavior*</span></span>

<span data-ttu-id="f3fbd-118">Gli oggetti tag-along hanno parametri che possono ottimizzare il modo in cui si comportano.</span><span class="sxs-lookup"><span data-stu-id="f3fbd-118">Tag-along objects have parameters which can fine-tune the way they behave.</span></span> <span data-ttu-id="f3fbd-119">Il contenuto può essere all'interno o all'esterno della linea di visione dell'utente nel modo desiderato mentre l'utente si sposta all'interno dell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="f3fbd-119">Content can be in or out of the user’s line of sight as desired while the user moves around their environment.</span></span> <span data-ttu-id="f3fbd-120">Quando l'utente si sposta, il contenuto tenterà di rimanere all'interno della periferia dell'utente scorrendo verso il bordo della visualizzazione, a seconda della velocità con cui un utente sposta il contenuto temporaneamente fuori dalla visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="f3fbd-120">As the user moves, the content will attempt to stay within the user’s periphery by sliding towards the edge of the view, depending on how quickly a user moves may leave the content temporarily out of view.</span></span> <span data-ttu-id="f3fbd-121">Quando l'utente guarda l'oggetto tag-along, viene visualizzato in modo più completo.</span><span class="sxs-lookup"><span data-stu-id="f3fbd-121">When the user gazes towards the tag-along object, it comes more fully into view.</span></span> <span data-ttu-id="f3fbd-122">Il contenuto è sempre un "colpo d'occhio" in modo che gli utenti non dimentichino mai la direzione in cui si trova il contenuto.</span><span class="sxs-lookup"><span data-stu-id="f3fbd-122">Think of content always being "a glance away" so users never forget what direction their content is in.</span></span>

<span data-ttu-id="f3fbd-123">I parametri aggiuntivi possono fare in modo che l'oggetto tag-along si trovi collegato alla testa dell'utente da un elastico.</span><span class="sxs-lookup"><span data-stu-id="f3fbd-123">Additional parameters can make the tag-along object feel attached to the user's head by a rubber band.</span></span> <span data-ttu-id="f3fbd-124">L'attenuazione dell'accelerazione o della decelerazione dà peso all'oggetto che lo rende più fisicamente presente.</span><span class="sxs-lookup"><span data-stu-id="f3fbd-124">Dampening acceleration or deceleration gives weight to the object making it feel more physically present.</span></span> <span data-ttu-id="f3fbd-125">Questo comportamento primaverile è un'offerta che consente all'utente di creare un modello mentale accurato del funzionamento dei tag.</span><span class="sxs-lookup"><span data-stu-id="f3fbd-125">This spring behavior is an affordance that helps the user build an accurate mental model of how tag-along works.</span></span> <span data-ttu-id="f3fbd-126">L'audio consente di fornire affordances aggiuntive quando gli utenti hanno oggetti in modalità tag-along.</span><span class="sxs-lookup"><span data-stu-id="f3fbd-126">Audio helps provide additional affordances for when users have objects in tag-along mode.</span></span> <span data-ttu-id="f3fbd-127">L'audio deve rafforzare la velocità di spostamento; una rotazione a capo veloce dovrebbe offrire un effetto acustico più evidente mentre la velocità naturale dovrebbe avere un audio minimo se si verificano effetti.</span><span class="sxs-lookup"><span data-stu-id="f3fbd-127">Audio should reinforce the speed of movement; a fast head turn should provide a more noticeable sound effect while walking at a natural speed should have minimal audio if any effects at all.</span></span>

<span data-ttu-id="f3fbd-128">Proprio come il contenuto con blocco principale, gli oggetti tag-along possono rivelarsi opprimenti o nauseanti se si muovono in modo sfrenato o troppo lungo nella visualizzazione dell'utente.</span><span class="sxs-lookup"><span data-stu-id="f3fbd-128">Just like truly head-locked content, tag-along objects can prove overwhelming or nauseating if they move wildly or spring too much in the user’s view.</span></span> <span data-ttu-id="f3fbd-129">Quando un utente si trova e quindi si arresta rapidamente, i loro sensi indicano che sono stati arrestati.</span><span class="sxs-lookup"><span data-stu-id="f3fbd-129">As a user looks around and then quickly stop, their senses tell them they have stopped.</span></span> <span data-ttu-id="f3fbd-130">Il loro saldo informa che la loro testa si è interrotta e la loro visione vede il mondo che si interrompe.</span><span class="sxs-lookup"><span data-stu-id="f3fbd-130">Their balance informs them that their head has stopped turning as well as their vision sees the world stop turning.</span></span> <span data-ttu-id="f3fbd-131">Tuttavia, se il tag-along continua a essere spostato quando l'utente si arresta, può confonderne i sensi.</span><span class="sxs-lookup"><span data-stu-id="f3fbd-131">However, if tag-along keeps on moving when the user has stopped, it may confuse their senses.</span></span>

<br>

---

## <a name="billboarding-and-tag-along-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="f3fbd-132">Billboard e tag-along in MRTK (Mixed Reality Toolkit) per Unity</span><span class="sxs-lookup"><span data-stu-id="f3fbd-132">Billboarding and Tag-along in MRTK(Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="f3fbd-133">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** fornisce script per il comportamento di Billboard e tag-along.</span><span class="sxs-lookup"><span data-stu-id="f3fbd-133">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts for the Billboarding and Tag-along behavior.</span></span> <span data-ttu-id="f3fbd-134">È sufficiente assegnare lo script Billboard.cs a qualsiasi oggetto per aggiungere il comportamento di Billboard e fare in modo che l'oggetto faccia sempre fronte all'utente.</span><span class="sxs-lookup"><span data-stu-id="f3fbd-134">Simply assign Billboard.cs script onto any object to add billboarding behavior and make the object always face you.</span></span> <span data-ttu-id="f3fbd-135">Per aggiungere un comportamento tag-along, usare lo script RadialView.cs.</span><span class="sxs-lookup"><span data-stu-id="f3fbd-135">To add tag-along behavior, use RadialView.cs script.</span></span> <span data-ttu-id="f3fbd-136">È possibile modificare varie opzioni, ad esempio lerping tempo, distanza e grado.</span><span class="sxs-lookup"><span data-stu-id="f3fbd-136">You can adjust various options such as lerping time, distance, and degree.</span></span>

* [<span data-ttu-id="f3fbd-137">MRTK-Risolutore viste radiali</span><span class="sxs-lookup"><span data-stu-id="f3fbd-137">MRTK - Radial View Solver</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html#radialview)
* [<span data-ttu-id="f3fbd-138">MRTK-script Billboard</span><span class="sxs-lookup"><span data-stu-id="f3fbd-138">MRTK - Billboard script</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Scripts/Utilities/Billboard.cs)


<br>

---

## <a name="see-also"></a><span data-ttu-id="f3fbd-139">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="f3fbd-139">See also</span></span>

* [<span data-ttu-id="f3fbd-140">Cursori</span><span class="sxs-lookup"><span data-stu-id="f3fbd-140">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="f3fbd-141">Raggio della mano</span><span class="sxs-lookup"><span data-stu-id="f3fbd-141">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="f3fbd-142">Button</span><span class="sxs-lookup"><span data-stu-id="f3fbd-142">Button</span></span>](button.md)
* [<span data-ttu-id="f3fbd-143">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="f3fbd-143">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="f3fbd-144">Rettangolo di selezione e barra dell'app</span><span class="sxs-lookup"><span data-stu-id="f3fbd-144">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="f3fbd-145">Manipolazione</span><span class="sxs-lookup"><span data-stu-id="f3fbd-145">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="f3fbd-146">Menu a mano</span><span class="sxs-lookup"><span data-stu-id="f3fbd-146">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="f3fbd-147">Menu adiacente</span><span class="sxs-lookup"><span data-stu-id="f3fbd-147">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="f3fbd-148">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="f3fbd-148">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="f3fbd-149">Comando vocale</span><span class="sxs-lookup"><span data-stu-id="f3fbd-149">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="f3fbd-150">Tastiera</span><span class="sxs-lookup"><span data-stu-id="f3fbd-150">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="f3fbd-151">Descrizione comando</span><span class="sxs-lookup"><span data-stu-id="f3fbd-151">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="f3fbd-152">Slate</span><span class="sxs-lookup"><span data-stu-id="f3fbd-152">Slate</span></span>](slate.md)
* [<span data-ttu-id="f3fbd-153">Dispositivo di scorrimento</span><span class="sxs-lookup"><span data-stu-id="f3fbd-153">Slider</span></span>](slider.md)
* [<span data-ttu-id="f3fbd-154">Shader</span><span class="sxs-lookup"><span data-stu-id="f3fbd-154">Shader</span></span>](shader.md)
* [<span data-ttu-id="f3fbd-155">Billboarding e tag-along</span><span class="sxs-lookup"><span data-stu-id="f3fbd-155">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="f3fbd-156">Visualizzazione dello stato</span><span class="sxs-lookup"><span data-stu-id="f3fbd-156">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="f3fbd-157">Magnetismo di superficie</span><span class="sxs-lookup"><span data-stu-id="f3fbd-157">Surface magnetism</span></span>](surface-magnetism.md)

---
title: Rettangolo di delimitazione e barra dell'app
description: La barra dell'app è un menu a livello di oggetto contenente una serie di pulsanti visualizzati sul bordo inferiore dei limiti di un ologramma.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Realtà mista di Windows, barra dell'app, rettangolo di delimitazione
ms.openlocfilehash: e4f519cba459efac25f6c1370b07fcda4def30a1
ms.sourcegitcommit: 17427d4d8c3723d53540f1b7f5bc061bba08c1d6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2019
ms.locfileid: "74143169"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="83c98-104">Rettangolo di delimitazione e barra dell'app</span><span class="sxs-lookup"><span data-stu-id="83c98-104">Bounding box and App bar</span></span>
<span data-ttu-id="83c98-105">![delimitatore è l'interfaccia standard per la manipolazione degli oggetti in realtà mista.](images/UX/UX_Hero_BoundingBox.jpg)</span><span class="sxs-lookup"><span data-stu-id="83c98-105">![Bounding is the standard interface for object manipulation in Mixed Reality.](images/UX/UX_Hero_BoundingBox.jpg)</span></span><br>
<br>

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="83c98-106">Che cos'è il rettangolo di delimitazione?</span><span class="sxs-lookup"><span data-stu-id="83c98-106">What is the Bounding box?</span></span>

<span data-ttu-id="83c98-107">Il delimitatore è l'interfaccia standard per la manipolazione di oggetti in realtà mista.</span><span class="sxs-lookup"><span data-stu-id="83c98-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="83c98-108">Fornisce all'utente la convenienza che l'oggetto è attualmente modificabile.</span><span class="sxs-lookup"><span data-stu-id="83c98-108">It provides the user an affordance that the object is currently adjustable.</span></span> <span data-ttu-id="83c98-109">In HoloLens 2 il rettangolo di delimitazione funziona con la manipolazione diretta della mano e risponde alla vicinanza finger's dell'utente.</span><span class="sxs-lookup"><span data-stu-id="83c98-109">On HoloLens 2, the bounding box works with direct hand manipulation and responds to the user's finger's proximity.</span></span> <span data-ttu-id="83c98-110">Mostra commenti visivi per aiutare l'utente a percepire la distanza dall'oggetto.</span><span class="sxs-lookup"><span data-stu-id="83c98-110">It shows visual feedback to help the user perceive the distance from the object.</span></span>

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a><span data-ttu-id="83c98-111">Ridimensionamento di un oggetto</span><span class="sxs-lookup"><span data-stu-id="83c98-111">Scaling an object</span></span><br>
        <span data-ttu-id="83c98-112">Gli angoli del rettangolo di delimitazione indicano all'utente che l'oggetto può essere ridimensionato.</span><span class="sxs-lookup"><span data-stu-id="83c98-112">The corners of the bounding box tell the user that the object can scale.</span></span> <span data-ttu-id="83c98-113">Gli handle seguono un modello molto noto per la regolazione della scala.</span><span class="sxs-lookup"><span data-stu-id="83c98-113">The handles follow a widely understood pattern for adjusting scale.</span></span> <span data-ttu-id="83c98-114">Questa offerta visiva mostra agli utenti l'area totale dell'oggetto, anche se non è visibile al di fuori di una modalità di regolazione.</span><span class="sxs-lookup"><span data-stu-id="83c98-114">This visual affordance shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="83c98-115">Questo è particolarmente importante perché, in caso contrario, un oggetto bloccato a un altro oggetto o a una superficie può sembrare comportarsi come se fosse presente spazio che non dovrebbe essere presente.</span><span class="sxs-lookup"><span data-stu-id="83c98-115">This is especially important because if it weren’t there, an object snapped to another object or surface may appear to behave as if there was space around it that shouldn’t be there.</span></span><br>
        <br>
        <span data-ttu-id="83c98-116">*Ciclo video: ridimensionamento di un oggetto tramite il rettangolo di delimitazione*</span><span class="sxs-lookup"><span data-stu-id="83c98-116">*Video loop: Scaling an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="83c98-117">spazio ![](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="83c98-117">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="83c98-118">![punto di visualizzazione HoloLens di ridimensionamento di un oggetto tramite il rettangolo di delimitazione](images/HoloLens2_BoundingBox.gif)</span><span class="sxs-lookup"><span data-stu-id="83c98-118">![HoloLens point-of-view of scaling an object via bounding box](images/HoloLens2_BoundingBox.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a><span data-ttu-id="83c98-119">Rotazione di un oggetto</span><span class="sxs-lookup"><span data-stu-id="83c98-119">Rotating an object</span></span><br>
        <span data-ttu-id="83c98-120">Il affordances rettangolare verticale sui bordi del rettangolo di delimitazione sono indicatori di rotazione.</span><span class="sxs-lookup"><span data-stu-id="83c98-120">The vertical rectangular affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="83c98-121">In questo modo l'utente garantisce una maggiore regolazione degli ologrammi posizionati.</span><span class="sxs-lookup"><span data-stu-id="83c98-121">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="83c98-122">Non solo è possibile modificare e ridimensionare, ma ora ruotare anche.</span><span class="sxs-lookup"><span data-stu-id="83c98-122">Not only can they adjust and scale, but now rotate as well.</span></span><br>
        <br>
        <span data-ttu-id="83c98-123">*Ciclo video: rotazione di un oggetto tramite il rettangolo di delimitazione*</span><span class="sxs-lookup"><span data-stu-id="83c98-123">*Video loop: Rotating an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="83c98-124">spazio ![](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="83c98-124">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="83c98-125">![punto di visualizzazione HoloLens della rotazione di un oggetto tramite il rettangolo di delimitazione](images/HoloLens2_BoundingBox_Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="83c98-125">![HoloLens point-of-view of rotating an object via bounding box](images/HoloLens2_BoundingBox_Rotate.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a><span data-ttu-id="83c98-126">Feedback visivo sulle prossimità della mano su HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="83c98-126">Visual feedback on hand proximity on HoloLens 2</span></span><br>
        <span data-ttu-id="83c98-127">In HoloLens 2 è presente un segnale visivo aggiuntivo che può aiutare la percezione dell'utente della profondità.</span><span class="sxs-lookup"><span data-stu-id="83c98-127">On HoloLens 2, there is an additional visual cue which can help the user's perception of depth.</span></span> <span data-ttu-id="83c98-128">Un anello vicino alla loro parte viene visualizzato e ridimensionato quando il dito si avvicina all'oggetto.</span><span class="sxs-lookup"><span data-stu-id="83c98-128">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="83c98-129">L'anello alla fine converge in un punto quando viene raggiunto lo stato premuto.</span><span class="sxs-lookup"><span data-stu-id="83c98-129">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="83c98-130">Questa convenienza visiva consente all'utente di comprendere la distanza dall'oggetto.</span><span class="sxs-lookup"><span data-stu-id="83c98-130">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="83c98-131">*Ciclo video: esempio di feedback visivo basato sulla prossimità a un rettangolo di delimitazione*</span><span class="sxs-lookup"><span data-stu-id="83c98-131">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="83c98-132">spazio ![](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="83c98-132">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="83c98-133">![commenti e suggerimenti visivi sulla prossimità della mano](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="83c98-133">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

<span data-ttu-id="83c98-134">**Per lo sviluppo di app Unity, vedere [il riquadro delimitatore in Mixed Reality Toolkit-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**</span><span class="sxs-lookup"><span data-stu-id="83c98-134">**For Unity app development, see [Bounding box in the Mixed Reality Toolkit-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**</span></span>

<br>

---

## <a name="what-is-the-app-bar"></a><span data-ttu-id="83c98-135">Che cos'è la barra dell'app?</span><span class="sxs-lookup"><span data-stu-id="83c98-135">What is the App bar?</span></span>

<span data-ttu-id="83c98-136">La barra dell'app è un menu a livello di oggetto contenente una serie di pulsanti visualizzati sul bordo inferiore dei limiti di un ologramma.</span><span class="sxs-lookup"><span data-stu-id="83c98-136">The App bar is a object-level menu containing a series of buttons that displays on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="83c98-137">Questo modello viene in genere usato per offrire agli utenti la possibilità di rimuovere e modificare gli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="83c98-137">This pattern is commonly used to give users the ability to remove and adjust holograms.</span></span> <span data-ttu-id="83c98-138">La barra dell'app è stata progettata principalmente per gestire gli oggetti posizionati nell'ambiente di un utente.</span><span class="sxs-lookup"><span data-stu-id="83c98-138">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="83c98-139">Insieme al rettangolo di delimitazione, un utente ha il controllo completo sulla posizione e sulla modalità di orientamento degli oggetti in realtà mista.</span><span class="sxs-lookup"><span data-stu-id="83c98-139">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a><span data-ttu-id="83c98-140">La barra dell'app segue l'utente</span><span class="sxs-lookup"><span data-stu-id="83c98-140">The App bar follows the user</span></span><br>
        <span data-ttu-id="83c98-141">Poiché questo modello viene usato con oggetti bloccati dal mondo, quando un utente si sposta intorno all'oggetto, la barra dell'app verrà sempre visualizzata sul lato degli oggetti più vicino all'utente.</span><span class="sxs-lookup"><span data-stu-id="83c98-141">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="83c98-142">Sebbene questo non sia il tabellone, ottiene lo stesso risultato. impedire la posizione di un utente per occludere o bloccare la funzionalità che altrimenti sarebbe disponibile da una posizione diversa nell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="83c98-142">While this isn't billboarding, it effectively achieves the same result; preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span> <br>
        <br>
        <span data-ttu-id="83c98-143">*Ciclo video: aggirare un ologramma, la barra dell'app segue*</span><span class="sxs-lookup"><span data-stu-id="83c98-143">*Video loop: Walking around a hologram, the App bar follows*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="83c98-144">spazio ![](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="83c98-144">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="83c98-145">![aggirare un ologramma.</span><span class="sxs-lookup"><span data-stu-id="83c98-145">![Walking around a hologram.</span></span> <span data-ttu-id="83c98-146">Segue la barra dell'app.](images/HoloLens2_AppBarFollowing.gif)</span><span class="sxs-lookup"><span data-stu-id="83c98-146">The App bar follows.](images/HoloLens2_AppBarFollowing.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>


## <a name="bounding-box-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="83c98-147">Rettangolo di delimitazione in MRTK (Mixed Reality Toolkit) per Unity</span><span class="sxs-lookup"><span data-stu-id="83c98-147">Bounding box in MRTK(Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="83c98-148">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** fornisce script e prefabbricati per il rettangolo di delimitazione e la barra dell'app.</span><span class="sxs-lookup"><span data-stu-id="83c98-148">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and prefabs for the Bounding box and App bar.</span></span> <span data-ttu-id="83c98-149">È possibile aggiungere un rettangolo di delimitazione semplicemente assegnando lo script BoundingBox.cs su qualsiasi oggetto.</span><span class="sxs-lookup"><span data-stu-id="83c98-149">You can add a Bounding box by simply assigning the BoundingBox.cs script onto any object.</span></span>

* [<span data-ttu-id="83c98-150">MRTK-rettangolo di delimitazione</span><span class="sxs-lookup"><span data-stu-id="83c98-150">MRTK - Bounding Box</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)


<br>

---


## <a name="see-also"></a><span data-ttu-id="83c98-151">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="83c98-151">See also</span></span>

* [<span data-ttu-id="83c98-152">Cursori</span><span class="sxs-lookup"><span data-stu-id="83c98-152">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="83c98-153">Raggio della mano</span><span class="sxs-lookup"><span data-stu-id="83c98-153">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="83c98-154">Button</span><span class="sxs-lookup"><span data-stu-id="83c98-154">Button</span></span>](button.md)
* [<span data-ttu-id="83c98-155">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="83c98-155">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="83c98-156">Rettangolo di selezione e barra dell'app</span><span class="sxs-lookup"><span data-stu-id="83c98-156">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="83c98-157">Manipolazione</span><span class="sxs-lookup"><span data-stu-id="83c98-157">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="83c98-158">Menu a mano</span><span class="sxs-lookup"><span data-stu-id="83c98-158">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="83c98-159">Menu adiacente</span><span class="sxs-lookup"><span data-stu-id="83c98-159">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="83c98-160">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="83c98-160">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="83c98-161">Comando vocale</span><span class="sxs-lookup"><span data-stu-id="83c98-161">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="83c98-162">Tastiera</span><span class="sxs-lookup"><span data-stu-id="83c98-162">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="83c98-163">Descrizione comando</span><span class="sxs-lookup"><span data-stu-id="83c98-163">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="83c98-164">Slate</span><span class="sxs-lookup"><span data-stu-id="83c98-164">Slate</span></span>](slate.md)
* [<span data-ttu-id="83c98-165">Dispositivo di scorrimento</span><span class="sxs-lookup"><span data-stu-id="83c98-165">Slider</span></span>](slider.md)
* [<span data-ttu-id="83c98-166">Shader</span><span class="sxs-lookup"><span data-stu-id="83c98-166">Shader</span></span>](shader.md)
* [<span data-ttu-id="83c98-167">Billboarding e tag-along</span><span class="sxs-lookup"><span data-stu-id="83c98-167">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="83c98-168">Visualizzazione dello stato</span><span class="sxs-lookup"><span data-stu-id="83c98-168">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="83c98-169">Magnetismo di superficie</span><span class="sxs-lookup"><span data-stu-id="83c98-169">Surface magnetism</span></span>](surface-magnetism.md)

---
title: Rettangolo di delimitazione e barra dell'app
description: La barra dell'app è un menu a livello di oggetto contenente una serie di pulsanti visualizzati sul bordo inferiore dei limiti di un ologramma.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Realtà mista di Windows, barra dell'app, rettangolo di delimitazione
ms.openlocfilehash: f09187bc2a3969a8f844711052e15433f5449d6d
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437061"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="4e5dd-104">Rettangolo di delimitazione e barra dell'app</span><span class="sxs-lookup"><span data-stu-id="4e5dd-104">Bounding box and App bar</span></span>
![Il delimitatore è l'interfaccia standard per la manipolazione di oggetti in realtà mista.](images/640px-boundingbox-hero.jpg)<br>

<br>

---

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="4e5dd-106">Che cos'è il rettangolo di delimitazione?</span><span class="sxs-lookup"><span data-stu-id="4e5dd-106">What is the Bounding box?</span></span>

<span data-ttu-id="4e5dd-107">Il delimitatore è l'interfaccia standard per la manipolazione di oggetti in realtà mista.</span><span class="sxs-lookup"><span data-stu-id="4e5dd-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="4e5dd-108">Fornisce all'utente la convenienza che l'oggetto è attualmente modificabile.</span><span class="sxs-lookup"><span data-stu-id="4e5dd-108">It provides the user an affordance that the object is currently adjustable.</span></span> <span data-ttu-id="4e5dd-109">In HoloLens 2 il rettangolo di delimitazione funziona con la manipolazione diretta della mano e risponde alla vicinanza finger's dell'utente.</span><span class="sxs-lookup"><span data-stu-id="4e5dd-109">On HoloLens 2, the bounding box works with direct hand manipulation and responds to the user's finger's proximity.</span></span> <span data-ttu-id="4e5dd-110">Mostra commenti visivi per aiutare l'utente a percepire la distanza dall'oggetto.</span><span class="sxs-lookup"><span data-stu-id="4e5dd-110">It shows visual feedback to help the user perceive the distance from the object.</span></span>

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a><span data-ttu-id="4e5dd-111">Ridimensionamento di un oggetto</span><span class="sxs-lookup"><span data-stu-id="4e5dd-111">Scaling an object</span></span><br>
        <span data-ttu-id="4e5dd-112">Gli angoli del rettangolo di delimitazione indicano all'utente che l'oggetto può essere ridimensionato.</span><span class="sxs-lookup"><span data-stu-id="4e5dd-112">The corners of the bounding box tell the user that the object can scale.</span></span> <span data-ttu-id="4e5dd-113">Gli handle seguono un modello molto noto per la regolazione della scala.</span><span class="sxs-lookup"><span data-stu-id="4e5dd-113">The handles follow a widely understood pattern for adjusting scale.</span></span> <span data-ttu-id="4e5dd-114">Questa offerta visiva mostra agli utenti l'area totale dell'oggetto, anche se non è visibile al di fuori di una modalità di regolazione.</span><span class="sxs-lookup"><span data-stu-id="4e5dd-114">This visual affordance shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="4e5dd-115">Questo è particolarmente importante perché, in caso contrario, un oggetto bloccato a un altro oggetto o a una superficie può sembrare comportarsi come se fosse presente spazio che non dovrebbe essere presente.</span><span class="sxs-lookup"><span data-stu-id="4e5dd-115">This is especially important because if it weren’t there, an object snapped to another object or surface may appear to behave as if there was space around it that shouldn’t be there.</span></span><br>
        <br>
        <span data-ttu-id="4e5dd-116">*Ciclo video: ridimensionamento di un oggetto tramite il rettangolo di delimitazione*</span><span class="sxs-lookup"><span data-stu-id="4e5dd-116">*Video loop: Scaling an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="4e5dd-117">spazio ![](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="4e5dd-117">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="4e5dd-118">![punto di visualizzazione HoloLens di ridimensionamento di un oggetto tramite il rettangolo di delimitazione](images/HoloLens2_BoundingBox.gif)</span><span class="sxs-lookup"><span data-stu-id="4e5dd-118">![HoloLens point-of-view of scaling an object via bounding box](images/HoloLens2_BoundingBox.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a><span data-ttu-id="4e5dd-119">Rotazione di un oggetto</span><span class="sxs-lookup"><span data-stu-id="4e5dd-119">Rotating an object</span></span><br>
        <span data-ttu-id="4e5dd-120">Il affordances rettangolare verticale sui bordi del rettangolo di delimitazione sono indicatori di rotazione.</span><span class="sxs-lookup"><span data-stu-id="4e5dd-120">The vertical rectangular affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="4e5dd-121">In questo modo l'utente garantisce una maggiore regolazione degli ologrammi posizionati.</span><span class="sxs-lookup"><span data-stu-id="4e5dd-121">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="4e5dd-122">Non solo è possibile modificare e ridimensionare, ma ora ruotare anche.</span><span class="sxs-lookup"><span data-stu-id="4e5dd-122">Not only can they adjust and scale, but now rotate as well.</span></span><br>
        <br>
        <span data-ttu-id="4e5dd-123">*Ciclo video: rotazione di un oggetto tramite il rettangolo di delimitazione*</span><span class="sxs-lookup"><span data-stu-id="4e5dd-123">*Video loop: Rotating an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="4e5dd-124">spazio ![](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="4e5dd-124">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="4e5dd-125">![punto di visualizzazione HoloLens della rotazione di un oggetto tramite il rettangolo di delimitazione](images/HoloLens2_BoundingBox_Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="4e5dd-125">![HoloLens point-of-view of rotating an object via bounding box](images/HoloLens2_BoundingBox_Rotate.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a><span data-ttu-id="4e5dd-126">Feedback visivo sulle prossimità della mano su HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="4e5dd-126">Visual feedback on hand proximity on HoloLens 2</span></span><br>
        <span data-ttu-id="4e5dd-127">In HoloLens 2 è presente un segnale visivo aggiuntivo che può aiutare la percezione dell'utente della profondità.</span><span class="sxs-lookup"><span data-stu-id="4e5dd-127">On HoloLens 2, there is an additional visual cue which can help the user's perception of depth.</span></span> <span data-ttu-id="4e5dd-128">Un anello vicino alla loro parte viene visualizzato e ridimensionato quando il dito si avvicina all'oggetto.</span><span class="sxs-lookup"><span data-stu-id="4e5dd-128">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="4e5dd-129">L'anello alla fine converge in un punto quando viene raggiunto lo stato premuto.</span><span class="sxs-lookup"><span data-stu-id="4e5dd-129">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="4e5dd-130">Questa convenienza visiva consente all'utente di comprendere la distanza dall'oggetto.</span><span class="sxs-lookup"><span data-stu-id="4e5dd-130">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="4e5dd-131">*Ciclo video: esempio di feedback visivo basato sulla prossimità a un rettangolo di delimitazione*</span><span class="sxs-lookup"><span data-stu-id="4e5dd-131">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="4e5dd-132">spazio ![](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="4e5dd-132">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="4e5dd-133">![commenti e suggerimenti visivi sulla prossimità della mano](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="4e5dd-133">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

<span data-ttu-id="4e5dd-134">**Per lo sviluppo di app Unity, vedere [il riquadro delimitatore in Mixed Reality Toolkit-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**</span><span class="sxs-lookup"><span data-stu-id="4e5dd-134">**For Unity app development, see [Bounding box in the Mixed Reality Toolkit-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**</span></span>

<br>

---

## <a name="what-is-the-app-bar"></a><span data-ttu-id="4e5dd-135">Che cos'è la barra dell'app?</span><span class="sxs-lookup"><span data-stu-id="4e5dd-135">What is the App bar?</span></span>

<span data-ttu-id="4e5dd-136">La barra dell'app è un menu a livello di oggetto contenente una serie di pulsanti visualizzati sul bordo inferiore dei limiti di un ologramma.</span><span class="sxs-lookup"><span data-stu-id="4e5dd-136">The App bar is a object-level menu containing a series of buttons that displays on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="4e5dd-137">Questo modello viene in genere usato per offrire agli utenti la possibilità di rimuovere e modificare gli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="4e5dd-137">This pattern is commonly used to give users the ability to remove and adjust holograms.</span></span> <span data-ttu-id="4e5dd-138">La barra dell'app è stata progettata principalmente per gestire gli oggetti posizionati nell'ambiente di un utente.</span><span class="sxs-lookup"><span data-stu-id="4e5dd-138">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="4e5dd-139">Insieme al rettangolo di delimitazione, un utente ha il controllo completo sulla posizione e sulla modalità di orientamento degli oggetti in realtà mista.</span><span class="sxs-lookup"><span data-stu-id="4e5dd-139">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a><span data-ttu-id="4e5dd-140">La barra dell'app segue l'utente</span><span class="sxs-lookup"><span data-stu-id="4e5dd-140">The App bar follows the user</span></span><br>
        <span data-ttu-id="4e5dd-141">Poiché questo modello viene usato con oggetti bloccati dal mondo, quando un utente si sposta intorno all'oggetto, la barra dell'app verrà sempre visualizzata sul lato degli oggetti più vicino all'utente.</span><span class="sxs-lookup"><span data-stu-id="4e5dd-141">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="4e5dd-142">Sebbene questo non sia il tabellone, ottiene lo stesso risultato. impedire la posizione di un utente per occludere o bloccare la funzionalità che altrimenti sarebbe disponibile da una posizione diversa nell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="4e5dd-142">While this isn't billboarding, it effectively achieves the same result; preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span> <br>
        <br>
        <span data-ttu-id="4e5dd-143">*Ciclo video: aggirare un ologramma, la barra dell'app segue*</span><span class="sxs-lookup"><span data-stu-id="4e5dd-143">*Video loop: Walking around a hologram, the App bar follows*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="4e5dd-144">spazio ![](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="4e5dd-144">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="4e5dd-145">![aggirare un ologramma.</span><span class="sxs-lookup"><span data-stu-id="4e5dd-145">![Walking around a hologram.</span></span> <span data-ttu-id="4e5dd-146">Segue la barra dell'app.](images/HoloLens2_AppBarFollowing.gif)</span><span class="sxs-lookup"><span data-stu-id="4e5dd-146">The App bar follows.](images/HoloLens2_AppBarFollowing.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>



<span data-ttu-id="4e5dd-147">**Per lo sviluppo di app Unity, vedere [barra delle app in Mixed Reality Toolkit-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)**</span><span class="sxs-lookup"><span data-stu-id="4e5dd-147">**For Unity app development, see [App bar in the Mixed Reality Toolkit-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)**</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="4e5dd-148">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="4e5dd-148">See also</span></span>
* [<span data-ttu-id="4e5dd-149">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="4e5dd-149">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="4e5dd-150">Testo in Unity</span><span class="sxs-lookup"><span data-stu-id="4e5dd-150">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="4e5dd-151">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="4e5dd-151">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="4e5dd-152">Visualizzazione dello stato</span><span class="sxs-lookup"><span data-stu-id="4e5dd-152">Displaying progress</span></span>](progress.md)

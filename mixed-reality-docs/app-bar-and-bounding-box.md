---
title: Rettangolo di delimitazione e barra dell'app
description: La barra dell'app è un menu a livello di oggetto contenente una serie di pulsanti visualizzati sul bordo inferiore dei limiti di un ologramma.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Realtà mista di Windows, barra dell'app, rettangolo di delimitazione
ms.openlocfilehash: d289be31129324c6ff419b69dbce52bd8f62eb64
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829680"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="44624-104">Rettangolo di delimitazione e barra dell'app</span><span class="sxs-lookup"><span data-stu-id="44624-104">Bounding box and App bar</span></span>
![Il delimitatore è l'interfaccia standard per la manipolazione di oggetti in realtà mista.](images/640px-boundingbox-hero.jpg)<br>

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="44624-106">Che cos'è il rettangolo di delimitazione?</span><span class="sxs-lookup"><span data-stu-id="44624-106">What is the Bounding box?</span></span>

<span data-ttu-id="44624-107">Il delimitatore è l'interfaccia standard per la manipolazione di oggetti in realtà mista.</span><span class="sxs-lookup"><span data-stu-id="44624-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="44624-108">Fornisce all'utente la convenienza che l'oggetto è attualmente modificabile.</span><span class="sxs-lookup"><span data-stu-id="44624-108">It provides the user an affordance that the object is currently adjustable.</span></span> <span data-ttu-id="44624-109">Gli angoli indicano all'utente che l'oggetto può anche essere ridimensionato.</span><span class="sxs-lookup"><span data-stu-id="44624-109">The corners tell the user that the object can also scale.</span></span> <span data-ttu-id="44624-110">Questa offerta visiva mostra agli utenti l'area totale dell'oggetto, anche se non è visibile al di fuori di una modalità di regolazione.</span><span class="sxs-lookup"><span data-stu-id="44624-110">This visual affordance shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="44624-111">Questo è particolarmente importante perché, in caso contrario, un oggetto bloccato a un altro oggetto o a una superficie può sembrare comportarsi come se fosse presente spazio che non dovrebbe essere presente.</span><span class="sxs-lookup"><span data-stu-id="44624-111">This is especially important because if it weren’t there, an object snapped to another object or surface may appear to behave as if there was space around it that shouldn’t be there.</span></span> <span data-ttu-id="44624-112">In HoloLens 2 il rettangolo di delimitazione funziona con la manipolazione diretta della mano e risponde alla vicinanza finger's dell'utente.</span><span class="sxs-lookup"><span data-stu-id="44624-112">On HoloLens 2, the bounding box works with direct hand manipulation and responds to the user's finger's proximity.</span></span> <span data-ttu-id="44624-113">Mostra commenti visivi per aiutare l'utente a percepire la distanza dall'oggetto.</span><span class="sxs-lookup"><span data-stu-id="44624-113">It shows visual feedback to help the user perceive the distance from the object.</span></span> 

<span data-ttu-id="44624-114">![HoloLens punto di vista della scalabilità di un oggetto tramite il rettangolo di delimitazione](images/HoloLens2_BoundingBox.gif)</span><span class="sxs-lookup"><span data-stu-id="44624-114">![HoloLens point-of-view of scaling an object via bounding box](images/HoloLens2_BoundingBox.gif)</span></span><br>
<span data-ttu-id="44624-115">*Ridimensionamento di un oggetto tramite il rettangolo di delimitazione*</span><span class="sxs-lookup"><span data-stu-id="44624-115">*Scaling an object via bounding box*</span></span>

<span data-ttu-id="44624-116">Gli handle negli angoli del rettangolo di delimitazione seguono un modello molto noto per la regolazione della scala.</span><span class="sxs-lookup"><span data-stu-id="44624-116">The handles in the corners of the bounding box follow a widely understood pattern for adjusting scale.</span></span> 

<span data-ttu-id="44624-117">![HoloLens punto di visualizzazione della rotazione di un oggetto tramite il rettangolo di delimitazione](images/HoloLens2_BoundingBox_Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="44624-117">![HoloLens point-of-view of rotating an object via bounding box](images/HoloLens2_BoundingBox_Rotate.gif)</span></span><br>
<span data-ttu-id="44624-118">*Rotazione di un oggetto tramite il rettangolo di delimitazione*</span><span class="sxs-lookup"><span data-stu-id="44624-118">*Rotating an object via bounding box*</span></span>


<span data-ttu-id="44624-119">![Feedback visivo sulla prossimità della mano](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="44624-119">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
<span data-ttu-id="44624-120">*Feedback visivo basato sulla prossimità*</span><span class="sxs-lookup"><span data-stu-id="44624-120">*Visual feedback based on the proximity*</span></span>

<span data-ttu-id="44624-121">Il affordances rettangolare verticale sui bordi del rettangolo di delimitazione sono indicatori di rotazione.</span><span class="sxs-lookup"><span data-stu-id="44624-121">The vertical rectangular affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="44624-122">In questo modo l'utente garantisce una maggiore regolazione degli ologrammi posizionati.</span><span class="sxs-lookup"><span data-stu-id="44624-122">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="44624-123">Non solo è possibile modificare e ridimensionare, ma ora ruotare anche.</span><span class="sxs-lookup"><span data-stu-id="44624-123">Not only can they adjust and scale, but now rotate as well.</span></span>

* <span data-ttu-id="44624-124">Per lo sviluppo di app Unity, vedere rettangolo [di delimitazione nel Toolkit di realtà mista-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)</span><span class="sxs-lookup"><span data-stu-id="44624-124">For Unity app development, see [Bounding box on Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)</span></span>



## <a name="what-is-the-app-bar"></a><span data-ttu-id="44624-125">Che cos'è la barra dell'app?</span><span class="sxs-lookup"><span data-stu-id="44624-125">What is the App bar?</span></span>

<span data-ttu-id="44624-126">La barra dell'app è un menu a livello di oggetto contenente una serie di pulsanti visualizzati sul bordo inferiore dei limiti di un ologramma.</span><span class="sxs-lookup"><span data-stu-id="44624-126">The App bar is a object-level menu containing a series of buttons that displays on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="44624-127">Questo modello viene in genere usato per offrire agli utenti la possibilità di rimuovere e modificare gli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="44624-127">This pattern is commonly used to give users the ability to remove and adjust holograms.</span></span>

<span data-ttu-id="44624-128">Poiché questo modello viene usato con oggetti bloccati dal mondo, quando un utente si sposta intorno all'oggetto, la barra dell'app verrà sempre visualizzata sul lato degli oggetti più vicino all'utente.</span><span class="sxs-lookup"><span data-stu-id="44624-128">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="44624-129">Sebbene questo non sia il tabellone, ottiene lo stesso risultato. impedire la posizione di un utente per occludere o bloccare la funzionalità che altrimenti sarebbe disponibile da una posizione diversa nell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="44624-129">While this isn't billboarding, it effectively achieves the same result; preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span>

<span data-ttu-id="44624-130">![Aggirare un ologramma.</span><span class="sxs-lookup"><span data-stu-id="44624-130">![Walking around a hologram.</span></span> <span data-ttu-id="44624-131">Segue la barra dell'app.](images/HoloLens2_AppBarFollowing.gif)</span><span class="sxs-lookup"><span data-stu-id="44624-131">The App bar follows.](images/HoloLens2_AppBarFollowing.gif)</span></span><br>
<span data-ttu-id="44624-132">*Aggirare un ologramma, la barra dell'app segue*</span><span class="sxs-lookup"><span data-stu-id="44624-132">*Walking around a hologram, the App bar follows*</span></span>

<span data-ttu-id="44624-133">La barra dell'app è stata progettata principalmente per gestire gli oggetti posizionati nell'ambiente di un utente.</span><span class="sxs-lookup"><span data-stu-id="44624-133">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="44624-134">Insieme al rettangolo di delimitazione, un utente ha il controllo completo sulla posizione e sulla modalità di orientamento degli oggetti in realtà mista.</span><span class="sxs-lookup"><span data-stu-id="44624-134">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

* <span data-ttu-id="44624-135">Per lo sviluppo di app Unity, vedere [barra delle applicazioni nel Toolkit di realtà mista-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)</span><span class="sxs-lookup"><span data-stu-id="44624-135">For Unity app development, see [App bar on Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)</span></span>

## <a name="see-also"></a><span data-ttu-id="44624-136">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="44624-136">See also</span></span>
* [<span data-ttu-id="44624-137">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="44624-137">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="44624-138">Testo in Unity</span><span class="sxs-lookup"><span data-stu-id="44624-138">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="44624-139">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="44624-139">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="44624-140">Visualizzazione dello stato</span><span class="sxs-lookup"><span data-stu-id="44624-140">Displaying progress</span></span>](progress.md)

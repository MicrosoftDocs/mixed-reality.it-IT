---
title: Rettangolo di selezione e barra dell'App
description: Barra dell'App è un menu a livello di oggetto che contiene una serie di pulsanti che viene visualizzato sul bordo inferiore dei limiti di ologramma.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, App a barre, rettangolo di selezione
ms.openlocfilehash: ab472e1c988e6bdfb0a69d90e90280082b3db759
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813867"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="484db-104">Finestra di contenimento e barra dell'App</span><span class="sxs-lookup"><span data-stu-id="484db-104">Bounding box and App bar</span></span>
![Rettangolo di selezione è l'interfaccia standard per la manipolazione dell'oggetto nella realtà mista.](images/640px-boundingbox-hero.jpg)<br>

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="484db-106">Che cos'è la finestra di contenimento?</span><span class="sxs-lookup"><span data-stu-id="484db-106">What is the Bounding box?</span></span>

<span data-ttu-id="484db-107">Rettangolo di selezione è l'interfaccia standard per la manipolazione dell'oggetto nella realtà mista.</span><span class="sxs-lookup"><span data-stu-id="484db-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="484db-108">L'utente fornisce un intuitività che l'oggetto è attualmente modificabile.</span><span class="sxs-lookup"><span data-stu-id="484db-108">It provides the user an affordance that the object is currently adjustable.</span></span> <span data-ttu-id="484db-109">Gli angoli informare l'utente che l'oggetto è possibile scalare anche.</span><span class="sxs-lookup"><span data-stu-id="484db-109">The corners tell the user that the object can also scale.</span></span> <span data-ttu-id="484db-110">Questo intuitività visual Mostra agli utenti l'area totale dell'oggetto, anche se non è visibile all'esterno di una modalità di regolazione.</span><span class="sxs-lookup"><span data-stu-id="484db-110">This visual affordance shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="484db-111">Ciò è particolarmente importante poiché se non esiste, potrebbe apparire un oggetto a un altro oggetto o nell'area ancorato si comporti come se si è verificato lo spazio intorno a esso che non deve essere presenti.</span><span class="sxs-lookup"><span data-stu-id="484db-111">This is especially important because if it weren’t there, an object snapped to another object or surface may appear to behave as if there was space around it that shouldn’t be there.</span></span> <span data-ttu-id="484db-112">In 2 HoloLens, il rettangolo di selezione funziona con la manipolazione diretta mano e risponde alla prossimità del dito dell'utente.</span><span class="sxs-lookup"><span data-stu-id="484db-112">On HoloLens 2, the bounding box works with direct hand manipulation and responds to the user's finger's proximity.</span></span> <span data-ttu-id="484db-113">Mostra commenti visivi per consentire all'utente di percepire la distanza dall'oggetto.</span><span class="sxs-lookup"><span data-stu-id="484db-113">It shows visual feedback to help the user perceive the distance from the object.</span></span> 

<span data-ttu-id="484db-114">![HoloLens punto di vista del ridimensionamento di un oggetto tramite rettangolo di selezione](images/HoloLens2_BoundingBox.gif)</span><span class="sxs-lookup"><span data-stu-id="484db-114">![HoloLens point-of-view of scaling an object via bounding box](images/HoloLens2_BoundingBox.gif)</span></span><br>
<span data-ttu-id="484db-115">*Il ridimensionamento di un oggetto tramite rettangolo di selezione*</span><span class="sxs-lookup"><span data-stu-id="484db-115">*Scaling an object via bounding box*</span></span>

<span data-ttu-id="484db-116">Gli handle negli angoli del rettangolo seguono un modello ampiamente riconosciuto per regolare la scala.</span><span class="sxs-lookup"><span data-stu-id="484db-116">The handles in the corners of the bounding box follow a widely understood pattern for adjusting scale.</span></span> 

<span data-ttu-id="484db-117">![HoloLens punto di vista della rotazione di un oggetto tramite rettangolo di selezione](images/HoloLens2_BoundingBox_Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="484db-117">![HoloLens point-of-view of rotating an object via bounding box](images/HoloLens2_BoundingBox_Rotate.gif)</span></span><br>
<span data-ttu-id="484db-118">*Ruotare un oggetto tramite rettangolo di selezione*</span><span class="sxs-lookup"><span data-stu-id="484db-118">*Rotating an object via bounding box*</span></span>


<span data-ttu-id="484db-119">![Indicazioni visive in prossimità di mano](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="484db-119">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
<span data-ttu-id="484db-120">*Feedback visivo in base alla prossimità*</span><span class="sxs-lookup"><span data-stu-id="484db-120">*Visual feedback based on the proximity*</span></span>

<span data-ttu-id="484db-121">I affordance rettangolare verticale sui bordi del rettangolo di selezione sono indicatori di rotazione.</span><span class="sxs-lookup"><span data-stu-id="484db-121">The vertical rectangular affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="484db-122">Questo account offre all'utente ulteriori regolazione loro vntana inserito.</span><span class="sxs-lookup"><span data-stu-id="484db-122">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="484db-123">Non solo può è regolare e scalabilità, ma ora ruotare anche.</span><span class="sxs-lookup"><span data-stu-id="484db-123">Not only can they adjust and scale, but now rotate as well.</span></span>

* <span data-ttu-id="484db-124">Per lo sviluppo di app Unity, vedere [rettangolo di selezione in Unity-Toolkit realtà mista](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)</span><span class="sxs-lookup"><span data-stu-id="484db-124">For Unity app development, see [Bounding box on Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)</span></span>



## <a name="what-is-the-app-bar"></a><span data-ttu-id="484db-125">Che cos'è barra dell'App?</span><span class="sxs-lookup"><span data-stu-id="484db-125">What is the App bar?</span></span>

<span data-ttu-id="484db-126">Barra dell'App è un menu a livello di oggetto che contiene una serie di pulsanti che viene visualizzato sul bordo inferiore dei limiti di ologramma.</span><span class="sxs-lookup"><span data-stu-id="484db-126">The App bar is a object-level menu containing a series of buttons that displays on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="484db-127">Questo modello viene comunemente usato per concedere agli utenti la possibilità di rimuovere e modificare vntana.</span><span class="sxs-lookup"><span data-stu-id="484db-127">This pattern is commonly used to give users the ability to remove and adjust holograms.</span></span>

<span data-ttu-id="484db-128">Poiché questo modello viene usato con gli oggetti che sono world bloccato, come un utente si sposta l'oggetto barra dell'App viene sempre visualizzato sul lato degli oggetti più vicino all'utente.</span><span class="sxs-lookup"><span data-stu-id="484db-128">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="484db-129">Anche se ciò non è del billboard, in modo efficace raggiunge lo stesso risultato. impedisce la funzionalità di blocco che altrimenti sarebbero disponibile da una posizione diversa nel proprio ambiente o posizione per nasconde i colori di un utente.</span><span class="sxs-lookup"><span data-stu-id="484db-129">While this isn't billboarding, it effectively achieves the same result; preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span>

<span data-ttu-id="484db-130">![Walking intorno ologramma.</span><span class="sxs-lookup"><span data-stu-id="484db-130">![Walking around a hologram.</span></span> <span data-ttu-id="484db-131">Segue barra dell'App.](images/HoloLens2_AppBarFollowing.gif)</span><span class="sxs-lookup"><span data-stu-id="484db-131">The App bar follows.](images/HoloLens2_AppBarFollowing.gif)</span></span><br>
<span data-ttu-id="484db-132">*Walking intorno ologramma, segue barra dell'App*</span><span class="sxs-lookup"><span data-stu-id="484db-132">*Walking around a hologram, the App bar follows*</span></span>

<span data-ttu-id="484db-133">Barra dell'App è stata progettata principalmente come un modo per gestire gli oggetti inseriti in un ambiente dell'utente.</span><span class="sxs-lookup"><span data-stu-id="484db-133">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="484db-134">Usato in combinazione con il rettangolo di selezione, un utente dispone del controllo completo su come e dove gli oggetti sono orientati in realtà mista.</span><span class="sxs-lookup"><span data-stu-id="484db-134">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

* <span data-ttu-id="484db-135">Per lo sviluppo di app Unity, vedere [barra dell'App in Unity-Toolkit realtà mista](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)</span><span class="sxs-lookup"><span data-stu-id="484db-135">For Unity app development, see [App bar on Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)</span></span>

## <a name="see-also"></a><span data-ttu-id="484db-136">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="484db-136">See also</span></span>
* [<span data-ttu-id="484db-137">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="484db-137">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="484db-138">Testo in Unity</span><span class="sxs-lookup"><span data-stu-id="484db-138">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="484db-139">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="484db-139">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="484db-140">Visualizzazione dello stato</span><span class="sxs-lookup"><span data-stu-id="484db-140">Displaying progress</span></span>](progress.md)

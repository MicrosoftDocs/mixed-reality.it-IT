---
title: Raccolta di oggetti
description: La raccolta di oggetti è un controllo di layout che consente di disporre una matrice di oggetti in una forma tridimensionale predefinita.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, controlli, progettazione
ms.openlocfilehash: 7c3bbd82ec909b5a2e3c81f122366be564934f4d
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813876"
---
# <a name="object-collection"></a><span data-ttu-id="23bd2-104">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="23bd2-104">Object collection</span></span>

<span data-ttu-id="23bd2-105">La raccolta di oggetti è un controllo di layout che consente di disporre una matrice di oggetti in una forma tridimensionale predefinita.</span><span class="sxs-lookup"><span data-stu-id="23bd2-105">Object collection is a layout control which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="23bd2-106">Supporta diversi stili di superficie: **piano, cilindro, sfera** e **radiale**.</span><span class="sxs-lookup"><span data-stu-id="23bd2-106">It supports various surface styles - **plane, cylinder, sphere** and **radial**.</span></span> <span data-ttu-id="23bd2-107">È possibile regolare il raggio e le dimensioni degli oggetti e lo spazio tra di essi.</span><span class="sxs-lookup"><span data-stu-id="23bd2-107">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="23bd2-108">La raccolta di oggetti supporta qualsiasi oggetto da Unity, sia 2D che 3D.</span><span class="sxs-lookup"><span data-stu-id="23bd2-108">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="23bd2-109">Nel **[Toolkit di realtà mista](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)** abbiamo creato script Unity ed esempi che consentiranno di creare una raccolta di oggetti.</span><span class="sxs-lookup"><span data-stu-id="23bd2-109">In the **[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)**, we have created Unity script and examples that will help you create an object collection.</span></span>

<span data-ttu-id="23bd2-110">![Raccolta di oggetti usata nella tabella periodica dell'app elementi](images/640px-objectcollection-hero-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="23bd2-110">![Object collection used in the Periodic Table of the Elements app](images/640px-objectcollection-hero-640px.jpg)</span></span><br>
<span data-ttu-id="23bd2-111">*Esempi di utilizzo della raccolta di oggetti*</span><span class="sxs-lookup"><span data-stu-id="23bd2-111">*Examples of using object collection*</span></span>

## <a name="object-collection-examples"></a><span data-ttu-id="23bd2-112">Esempi di raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="23bd2-112">Object collection examples</span></span>

<span data-ttu-id="23bd2-113">[La tabella periodica degli elementi](periodic-table-of-the-elements.md) è un'applicazione di esempio che illustra il funzionamento della raccolta di oggetti.</span><span class="sxs-lookup"><span data-stu-id="23bd2-113">[Periodic Table of the Elements](periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="23bd2-114">Usa la raccolta di oggetti per disporre le caselle di elementi chimici 3D in forme diverse.</span><span class="sxs-lookup"><span data-stu-id="23bd2-114">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="23bd2-115">![Esempi di raccolta di oggetti illustrati nella tabella periodica dell'app elementi](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="23bd2-115">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="23bd2-116">*Esempi di raccolta di oggetti illustrati nella tabella periodica dell'app di esempio Elements*</span><span class="sxs-lookup"><span data-stu-id="23bd2-116">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="23bd2-117">oggetti 3D</span><span class="sxs-lookup"><span data-stu-id="23bd2-117">3D objects</span></span>

<span data-ttu-id="23bd2-118">È possibile usare la raccolta di oggetti per il layout degli oggetti 3D importati.</span><span class="sxs-lookup"><span data-stu-id="23bd2-118">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="23bd2-119">Nell'esempio seguente viene illustrato un piano e un layout cilindrico di alcuni oggetti della poltrona 3D.</span><span class="sxs-lookup"><span data-stu-id="23bd2-119">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="23bd2-120">![Esempi di layout piano e cilindrico degli oggetti 3D](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="23bd2-120">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="23bd2-121">*Esempi di layout piano e cilindrico degli oggetti 3D*</span><span class="sxs-lookup"><span data-stu-id="23bd2-121">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="23bd2-122">oggetti 2D</span><span class="sxs-lookup"><span data-stu-id="23bd2-122">2D objects</span></span>

<span data-ttu-id="23bd2-123">È anche possibile usare immagini 2D con la raccolta di oggetti.</span><span class="sxs-lookup"><span data-stu-id="23bd2-123">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="23bd2-124">Gli esempi seguenti illustrano in che modo le immagini 2D possono essere visualizzate in una griglia.</span><span class="sxs-lookup"><span data-stu-id="23bd2-124">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![Esempio di immagini 2D con raccolta di oggetti](images/640px-layout-3dobjects-3.jpg)

<span data-ttu-id="23bd2-126">![Esempio di immagini 2D con raccolta di oggetti](images/640px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="23bd2-126">![An example of 2D images with Object collection](images/640px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="23bd2-127">*Esempi di utilizzo della raccolta di oggetti con immagini 2D*</span><span class="sxs-lookup"><span data-stu-id="23bd2-127">*Examples of using object collection with 2D images*</span></span>

## <a name="see-also"></a><span data-ttu-id="23bd2-128">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="23bd2-128">See also</span></span>
* [<span data-ttu-id="23bd2-129">Script e prefabbricati per la raccolta di oggetti nel Toolkit di realtà mista in GitHub</span><span class="sxs-lookup"><span data-stu-id="23bd2-129">Scripts and prefabs for Object collection in the Mixed Reality Toolkit on GitHub</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_ObjectCollection.md)
* [<span data-ttu-id="23bd2-130">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="23bd2-130">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="23bd2-131">Rettangolo di delimitazione</span><span class="sxs-lookup"><span data-stu-id="23bd2-131">Bounding Box</span></span>](app-bar-and-bounding-box.md)

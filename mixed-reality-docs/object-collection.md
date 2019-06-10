---
title: Raccolta di oggetti
description: Raccolta di oggetti è un controllo layout che consente di layout di una matrice di oggetti in una forma predefinita tridimensionale.
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
# <a name="object-collection"></a><span data-ttu-id="979de-104">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="979de-104">Object collection</span></span>

<span data-ttu-id="979de-105">Raccolta di oggetti è un controllo layout che consente di layout di una matrice di oggetti in una forma predefinita tridimensionale.</span><span class="sxs-lookup"><span data-stu-id="979de-105">Object collection is a layout control which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="979de-106">Supporta diversi stili di superficie - **piano, cilindro, sphere** e **radiale**.</span><span class="sxs-lookup"><span data-stu-id="979de-106">It supports various surface styles - **plane, cylinder, sphere** and **radial**.</span></span> <span data-ttu-id="979de-107">È possibile regolare il raggio e le dimensioni degli oggetti e lo spazio tra di essi.</span><span class="sxs-lookup"><span data-stu-id="979de-107">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="979de-108">Raccolta di oggetti supporta qualsiasi oggetto di Unity - sia 2D e 3D.</span><span class="sxs-lookup"><span data-stu-id="979de-108">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="979de-109">Nel  **[Toolkit di realtà mista](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)** , abbiamo creato uno script di Unity e gli esempi che consentono di creano una raccolta di oggetti.</span><span class="sxs-lookup"><span data-stu-id="979de-109">In the **[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)**, we have created Unity script and examples that will help you create an object collection.</span></span>

<span data-ttu-id="979de-110">![Raccolta di oggetti utilizzato nella tabella periodico dell'app elementi](images/640px-objectcollection-hero-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="979de-110">![Object collection used in the Periodic Table of the Elements app](images/640px-objectcollection-hero-640px.jpg)</span></span><br>
<span data-ttu-id="979de-111">*Esempi di utilizzo di raccolta di oggetti*</span><span class="sxs-lookup"><span data-stu-id="979de-111">*Examples of using object collection*</span></span>

## <a name="object-collection-examples"></a><span data-ttu-id="979de-112">Esempi di raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="979de-112">Object collection examples</span></span>

<span data-ttu-id="979de-113">[Tabella periodico degli elementi](periodic-table-of-the-elements.md) è un'app di esempio che illustra il funzionamento di raccolta di oggetti.</span><span class="sxs-lookup"><span data-stu-id="979de-113">[Periodic Table of the Elements](periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="979de-114">Raccolta di oggetti Usa per definire il layout caselle elemento chimiche 3D in diverse forme.</span><span class="sxs-lookup"><span data-stu-id="979de-114">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="979de-115">![Esempi di raccolta di oggetti indicati nella tabella periodico dell'app elementi](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="979de-115">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="979de-116">*Esempi di raccolta di oggetti indicati nella tabella periodico dell'app di esempio di elementi*</span><span class="sxs-lookup"><span data-stu-id="979de-116">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="979de-117">Oggetti 3D</span><span class="sxs-lookup"><span data-stu-id="979de-117">3D objects</span></span>

<span data-ttu-id="979de-118">È possibile utilizzare raccolta di oggetti per il layout degli oggetti 3D importati.</span><span class="sxs-lookup"><span data-stu-id="979de-118">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="979de-119">L'esempio seguente viene illustrato un piano e un layout di cilindro di alcuni oggetti chair 3D.</span><span class="sxs-lookup"><span data-stu-id="979de-119">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="979de-120">![Esempi di piano e cilindrico layout degli oggetti 3D](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="979de-120">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="979de-121">*Esempi di piano e cilindrico layout degli oggetti 3D*</span><span class="sxs-lookup"><span data-stu-id="979de-121">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="979de-122">Oggetti 2D</span><span class="sxs-lookup"><span data-stu-id="979de-122">2D objects</span></span>

<span data-ttu-id="979de-123">È inoltre possibile utilizzare immagini 2D con raccolta di oggetti.</span><span class="sxs-lookup"><span data-stu-id="979de-123">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="979de-124">Gli esempi seguenti illustrano come 2D immagini possono essere visualizzati in una griglia.</span><span class="sxs-lookup"><span data-stu-id="979de-124">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![Un esempio di immagini 2D con raccolta di oggetti](images/640px-layout-3dobjects-3.jpg)

<span data-ttu-id="979de-126">![Un esempio di immagini 2D con raccolta di oggetti](images/640px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="979de-126">![An example of 2D images with Object collection](images/640px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="979de-127">*Esempi di utilizzo dell'insieme di oggetti con immagini 2D*</span><span class="sxs-lookup"><span data-stu-id="979de-127">*Examples of using object collection with 2D images*</span></span>

## <a name="see-also"></a><span data-ttu-id="979de-128">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="979de-128">See also</span></span>
* [<span data-ttu-id="979de-129">Gli script e prefabs per la raccolta di oggetti nel Toolkit di realtà mista su GitHub</span><span class="sxs-lookup"><span data-stu-id="979de-129">Scripts and prefabs for Object collection in the Mixed Reality Toolkit on GitHub</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_ObjectCollection.md)
* [<span data-ttu-id="979de-130">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="979de-130">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="979de-131">Rettangolo di selezione</span><span class="sxs-lookup"><span data-stu-id="979de-131">Bounding Box</span></span>](app-bar-and-bounding-box.md)

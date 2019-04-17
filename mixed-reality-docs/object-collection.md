---
title: Raccolta di oggetti
description: Raccolta di oggetti è un controllo layout che consente di layout di una matrice di oggetti in una forma predefinita tridimensionale.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, controlli, progettazione
ms.openlocfilehash: 88ab0359d5083d43d5d6312ef1185f67ca0caa7d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605010"
---
# <a name="object-collection"></a><span data-ttu-id="a49a2-104">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="a49a2-104">Object collection</span></span>

<span data-ttu-id="a49a2-105">Raccolta di oggetti è un controllo layout che consente di layout di una matrice di oggetti in una forma predefinita tridimensionale.</span><span class="sxs-lookup"><span data-stu-id="a49a2-105">Object collection is a layout control which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="a49a2-106">Supporta quattro diversi stili di superficie - **piano, cilindro, sphere** e **dispersione**.</span><span class="sxs-lookup"><span data-stu-id="a49a2-106">It supports four different surface styles - **plane, cylinder, sphere** and **scatter**.</span></span> <span data-ttu-id="a49a2-107">È possibile regolare il raggio e le dimensioni degli oggetti e lo spazio tra di essi.</span><span class="sxs-lookup"><span data-stu-id="a49a2-107">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="a49a2-108">Raccolta di oggetti supporta qualsiasi oggetto di Unity - sia 2D e 3D.</span><span class="sxs-lookup"><span data-stu-id="a49a2-108">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="a49a2-109">Nel  **[Toolkit di realtà mista](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_ObjectCollection.md)**, sono stati creati script di Unity e [scena esempio](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Scenes/ObjectCollectionExample.unity) che consentirà di creare una raccolta di oggetti.</span><span class="sxs-lookup"><span data-stu-id="a49a2-109">In the **[Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_ObjectCollection.md)**, we have created Unity script and [example scene](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Scenes/ObjectCollectionExample.unity) that will help you create an object collection.</span></span>

<span data-ttu-id="a49a2-110">![Raccolta di oggetti utilizzato nella tabella periodico dell'app elementi](images/640px-objectcollection-hero-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="a49a2-110">![Object collection used in the Periodic Table of the Elements app](images/640px-objectcollection-hero-640px.jpg)</span></span><br>
<span data-ttu-id="a49a2-111">*Raccolta di oggetti utilizzato nella tabella periodico dell'app di esempio di elementi*</span><span class="sxs-lookup"><span data-stu-id="a49a2-111">*Object collection used in the Periodic Table of the Elements sample app*</span></span>

## <a name="object-collection-examples"></a><span data-ttu-id="a49a2-112">Esempi di raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="a49a2-112">Object collection examples</span></span>

<span data-ttu-id="a49a2-113">[Tabella periodico degli elementi](periodic-table-of-the-elements.md) è un'app di esempio che illustra il funzionamento di raccolta di oggetti.</span><span class="sxs-lookup"><span data-stu-id="a49a2-113">[Periodic Table of the Elements](periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="a49a2-114">Raccolta di oggetti Usa per definire il layout caselle elemento chimiche 3D in diverse forme.</span><span class="sxs-lookup"><span data-stu-id="a49a2-114">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="a49a2-115">![Esempi di raccolta di oggetti indicati nella tabella periodico dell'app elementi](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="a49a2-115">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="a49a2-116">*Esempi di raccolta di oggetti indicati nella tabella periodico dell'app di esempio di elementi*</span><span class="sxs-lookup"><span data-stu-id="a49a2-116">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="a49a2-117">Oggetti 3D</span><span class="sxs-lookup"><span data-stu-id="a49a2-117">3D objects</span></span>

<span data-ttu-id="a49a2-118">È possibile utilizzare raccolta di oggetti per il layout degli oggetti 3D importati.</span><span class="sxs-lookup"><span data-stu-id="a49a2-118">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="a49a2-119">L'esempio seguente viene illustrato un piano e un layout di cilindro di alcuni oggetti chair 3D.</span><span class="sxs-lookup"><span data-stu-id="a49a2-119">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="a49a2-120">![Esempi di piano e cilindrico layout degli oggetti 3D](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="a49a2-120">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="a49a2-121">*Esempi di piano e cilindrico layout degli oggetti 3D*</span><span class="sxs-lookup"><span data-stu-id="a49a2-121">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="a49a2-122">Oggetti 2D</span><span class="sxs-lookup"><span data-stu-id="a49a2-122">2D objects</span></span>

<span data-ttu-id="a49a2-123">È inoltre possibile utilizzare immagini 2D con raccolta di oggetti.</span><span class="sxs-lookup"><span data-stu-id="a49a2-123">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="a49a2-124">Gli esempi seguenti illustrano come 2D immagini possono essere visualizzati in una griglia.</span><span class="sxs-lookup"><span data-stu-id="a49a2-124">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![Un esempio di immagini 2D con raccolta di oggetti](images/640px-layout-3dobjects-3.jpg)

<span data-ttu-id="a49a2-126">![Un esempio di immagini 2D con raccolta di oggetti](images/640px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="a49a2-126">![An example of 2D images with Object collection](images/640px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="a49a2-127">*Esempi di immagini 2D con raccolta di oggetti*</span><span class="sxs-lookup"><span data-stu-id="a49a2-127">*Examples of 2D images with object collection*</span></span>

## <a name="see-also"></a><span data-ttu-id="a49a2-128">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a49a2-128">See also</span></span>
* [<span data-ttu-id="a49a2-129">Gli script e prefabs per la raccolta di oggetti nel Toolkit di realtà mista su GitHub</span><span class="sxs-lookup"><span data-stu-id="a49a2-129">Scripts and prefabs for Object collection in the Mixed Reality Toolkit on GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)
* [<span data-ttu-id="a49a2-130">Oggetto si</span><span class="sxs-lookup"><span data-stu-id="a49a2-130">Interactable object</span></span>](interactable-object.md)

---
title: Shader
description: ''
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: Realtà mista, controlli, interazione, interfaccia utente, UX
ms.openlocfilehash: 23371ae5d70e5e792415fd25c0d58def0a7cefbb
ms.sourcegitcommit: 17427d4d8c3723d53540f1b7f5bc061bba08c1d6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2019
ms.locfileid: "74143271"
---
# <a name="shader"></a><span data-ttu-id="c1a22-103">Shader</span><span class="sxs-lookup"><span data-stu-id="c1a22-103">Shader</span></span>

![Shader](images/UX/UX_Hero_StandardShader.jpg)

<span data-ttu-id="c1a22-105">Poiché gli oggetti olografici sono combinati con quelli fisici nell'ambiente, fornire un segnale visivo è importante in realtà mista.</span><span class="sxs-lookup"><span data-stu-id="c1a22-105">Since holographic objects are mixed with the physical ones in the environment, providing visual cue is important in mixed reality.</span></span> <span data-ttu-id="c1a22-106">MRTK standard shader fornisce vari tipi di effetti visivi che possono essere usati con gli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="c1a22-106">MRTK Standard shader provides various types of visual effects that can be used with holograms.</span></span> <span data-ttu-id="c1a22-107">Il sistema di ombreggiatura standard MRTK usa un unico shader flessibile che può ottenere oggetti visivi simili allo shader standard di Unity, implementare i principi del sistema di progettazione Fluent e rimanere efficienti nei dispositivi a realtà mista.</span><span class="sxs-lookup"><span data-stu-id="c1a22-107">MRTK Standard shading system utilizes a single, flexible shader that can achieve visuals similar to Unity's Standard Shader, implement Fluent Design System principles, and remain performant on mixed reality devices.</span></span>
<br>

## <a name="examples-of-visual-effects-using-mrtk-standard-shader"></a><span data-ttu-id="c1a22-108">Esempi di effetti visivi con MRTK standard shader</span><span class="sxs-lookup"><span data-stu-id="c1a22-108">Examples of visual effects using MRTK Standard shader</span></span> 
:::row:::
    :::column:::
       <span data-ttu-id="c1a22-109">![Sposta](images/UX/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="c1a22-109">![Move](images/UX/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="c1a22-110">**Luce vicina**</span><span class="sxs-lookup"><span data-stu-id="c1a22-110">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c1a22-111">![Ruota](images/UX/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="c1a22-111">![Rotate](images/UX/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="c1a22-112">**Bordo chiaro**</span><span class="sxs-lookup"><span data-stu-id="c1a22-112">**Border light**</span></span><br>
    :::column-end:::
:::row-end:::

---

## <a name="mrtk-standard-shader-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="c1a22-113">Shader standard MRTK in MRTK (Toolkit realtà mista) per Unity</span><span class="sxs-lookup"><span data-stu-id="c1a22-113">MRTK Standard shader in MRTK(Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="c1a22-114">MRTK-standard shader</span><span class="sxs-lookup"><span data-stu-id="c1a22-114">MRTK - Standard shader</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)


<br>

---

## <a name="see-also"></a><span data-ttu-id="c1a22-115">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="c1a22-115">See also</span></span>

* [<span data-ttu-id="c1a22-116">Cursori</span><span class="sxs-lookup"><span data-stu-id="c1a22-116">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="c1a22-117">Raggio della mano</span><span class="sxs-lookup"><span data-stu-id="c1a22-117">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="c1a22-118">Button</span><span class="sxs-lookup"><span data-stu-id="c1a22-118">Button</span></span>](button.md)
* [<span data-ttu-id="c1a22-119">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="c1a22-119">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="c1a22-120">Rettangolo di selezione e barra dell'app</span><span class="sxs-lookup"><span data-stu-id="c1a22-120">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="c1a22-121">Manipolazione</span><span class="sxs-lookup"><span data-stu-id="c1a22-121">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="c1a22-122">Menu a mano</span><span class="sxs-lookup"><span data-stu-id="c1a22-122">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="c1a22-123">Menu adiacente</span><span class="sxs-lookup"><span data-stu-id="c1a22-123">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="c1a22-124">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="c1a22-124">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="c1a22-125">Comando vocale</span><span class="sxs-lookup"><span data-stu-id="c1a22-125">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="c1a22-126">Tastiera</span><span class="sxs-lookup"><span data-stu-id="c1a22-126">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="c1a22-127">Descrizione comando</span><span class="sxs-lookup"><span data-stu-id="c1a22-127">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="c1a22-128">Slate</span><span class="sxs-lookup"><span data-stu-id="c1a22-128">Slate</span></span>](slate.md)
* [<span data-ttu-id="c1a22-129">Dispositivo di scorrimento</span><span class="sxs-lookup"><span data-stu-id="c1a22-129">Slider</span></span>](slider.md)
* [<span data-ttu-id="c1a22-130">Billboarding e tag-along</span><span class="sxs-lookup"><span data-stu-id="c1a22-130">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="c1a22-131">Visualizzazione dello stato</span><span class="sxs-lookup"><span data-stu-id="c1a22-131">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="c1a22-132">Magnetismo di superficie</span><span class="sxs-lookup"><span data-stu-id="c1a22-132">Surface magnetism</span></span>](surface-magnetism.md)

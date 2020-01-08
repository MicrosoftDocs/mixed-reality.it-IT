---
title: Shader
description: Lo shader standard MRTK fornisce vari tipi di effetti visivi che possono essere usati con gli ologrammi.
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: Realtà mista, controlli, interazione, interfaccia utente, UX
ms.openlocfilehash: 4d95e335b3f7020766beae916423d0588ee66572
ms.sourcegitcommit: 270ca09ec61e1153a83cf44942d7ba3783ef1805
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/07/2020
ms.locfileid: "75694165"
---
# <a name="shader"></a><span data-ttu-id="72de5-104">Shader</span><span class="sxs-lookup"><span data-stu-id="72de5-104">Shader</span></span>

![Shader](images/UX/UX_Hero_StandardShader.jpg)

<span data-ttu-id="72de5-106">Poiché gli oggetti olografici sono combinati con quelli fisici nell'ambiente, è importante fornire segnali visivi in realtà mista.</span><span class="sxs-lookup"><span data-stu-id="72de5-106">Since holographic objects are mixed with the physical ones in the environment, it's important to provide visual cues in mixed reality.</span></span> <span data-ttu-id="72de5-107">Lo shader standard MRTK fornisce vari tipi di effetti visivi che possono essere usati con gli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="72de5-107">The MRTK Standard shader provides various types of visual effects that can be used with holograms.</span></span> <span data-ttu-id="72de5-108">Il sistema di ombreggiatura standard di MRTK usa un unico shader flessibile che può ottenere oggetti visivi simili allo shader standard di Unity, implementa i [principi del sistema di progettazione Fluent](https://www.microsoft.com/design/fluent/#/)e mantiene le prestazioni nei dispositivi a realtà mista.</span><span class="sxs-lookup"><span data-stu-id="72de5-108">The MRTK Standard shading system utilizes a single, flexible shader that can achieve visuals similar to Unity's Standard Shader, implements [Fluent Design System principles](https://www.microsoft.com/design/fluent/#/), and remain performant on mixed reality devices.</span></span>
<br>

## <a name="examples-of-visual-effects-using-mrtk-standard-shader"></a><span data-ttu-id="72de5-109">Esempi di effetti visivi con MRTK standard shader</span><span class="sxs-lookup"><span data-stu-id="72de5-109">Examples of visual effects using MRTK Standard shader</span></span> 
:::row:::
    :::column:::
       <span data-ttu-id="72de5-110">![Sposta](images/UX/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="72de5-110">![Move](images/UX/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="72de5-111">**Luce vicina**</span><span class="sxs-lookup"><span data-stu-id="72de5-111">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="72de5-112">![Ruota](images/UX/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="72de5-112">![Rotate](images/UX/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="72de5-113">**Bordo chiaro**</span><span class="sxs-lookup"><span data-stu-id="72de5-113">**Border light**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="mrtk-standard-shader-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="72de5-114">Shader standard MRTK in MRTK (Toolkit realtà mista) per Unity</span><span class="sxs-lookup"><span data-stu-id="72de5-114">MRTK Standard shader in MRTK (Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="72de5-115">MRTK-standard shader</span><span class="sxs-lookup"><span data-stu-id="72de5-115">MRTK - Standard shader</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)


<br>

---

## <a name="see-also"></a><span data-ttu-id="72de5-116">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="72de5-116">See also</span></span>

* [<span data-ttu-id="72de5-117">Cursori</span><span class="sxs-lookup"><span data-stu-id="72de5-117">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="72de5-118">Raggio della mano</span><span class="sxs-lookup"><span data-stu-id="72de5-118">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="72de5-119">Button</span><span class="sxs-lookup"><span data-stu-id="72de5-119">Button</span></span>](button.md)
* [<span data-ttu-id="72de5-120">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="72de5-120">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="72de5-121">Rettangolo di selezione e barra dell'app</span><span class="sxs-lookup"><span data-stu-id="72de5-121">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="72de5-122">Manipolazione</span><span class="sxs-lookup"><span data-stu-id="72de5-122">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="72de5-123">Menu a mano</span><span class="sxs-lookup"><span data-stu-id="72de5-123">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="72de5-124">Menu adiacente</span><span class="sxs-lookup"><span data-stu-id="72de5-124">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="72de5-125">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="72de5-125">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="72de5-126">Comando vocale</span><span class="sxs-lookup"><span data-stu-id="72de5-126">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="72de5-127">Tastiera</span><span class="sxs-lookup"><span data-stu-id="72de5-127">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="72de5-128">Descrizione comando</span><span class="sxs-lookup"><span data-stu-id="72de5-128">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="72de5-129">Slate</span><span class="sxs-lookup"><span data-stu-id="72de5-129">Slate</span></span>](slate.md)
* [<span data-ttu-id="72de5-130">Dispositivo di scorrimento</span><span class="sxs-lookup"><span data-stu-id="72de5-130">Slider</span></span>](slider.md)
* [<span data-ttu-id="72de5-131">Billboarding e tag-along</span><span class="sxs-lookup"><span data-stu-id="72de5-131">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="72de5-132">Visualizzazione dello stato</span><span class="sxs-lookup"><span data-stu-id="72de5-132">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="72de5-133">Magnetismo di superficie</span><span class="sxs-lookup"><span data-stu-id="72de5-133">Surface magnetism</span></span>](surface-magnetism.md)

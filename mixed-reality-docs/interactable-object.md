---
title: Oggetto si
description: Un pulsante già da tempo, una metafora utilizzata per l'attivazione di un evento in tutto il mondo astratto 2D. Nel mondo tridimensionale realtà mista, non dobbiamo riguardare esclusivamente questo mondo di astrazione più.
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: Realtà mista, controlli, interazione, dell'interfaccia utente, esperienza utente
ms.openlocfilehash: f349d21707375690e00b0f7e465634c62be1537e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59601182"
---
# <a name="interactable-object"></a><span data-ttu-id="2908d-105">Oggetto si</span><span class="sxs-lookup"><span data-stu-id="2908d-105">Interactable object</span></span>

<span data-ttu-id="2908d-106">Un pulsante già da tempo, una metafora utilizzata per l'attivazione di un evento in tutto il mondo astratto 2D.</span><span class="sxs-lookup"><span data-stu-id="2908d-106">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="2908d-107">Nel mondo tridimensionale realtà mista, non dobbiamo riguardare esclusivamente questo mondo di astrazione più.</span><span class="sxs-lookup"><span data-stu-id="2908d-107">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="2908d-108">Qualsiasi elemento può essere un' **oggetto si** che attiva un evento.</span><span class="sxs-lookup"><span data-stu-id="2908d-108">Anything can be an **Interactable object** that triggers an event.</span></span> <span data-ttu-id="2908d-109">Un oggetto si può essere rappresentato come un elemento da una tazza di caffè sulla tabella in un fumetto mobile in modalità wireless.</span><span class="sxs-lookup"><span data-stu-id="2908d-109">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="2908d-110">È comunque effettuare uso dei pulsanti tradizionali in alcune situazioni, ad esempio in finestra di dialogo dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="2908d-110">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="2908d-111">La rappresentazione visiva del pulsante dipende dal contesto.</span><span class="sxs-lookup"><span data-stu-id="2908d-111">The visual representation of the button depends on the context.</span></span>

![Immagine banner interactible oggetto](images/640px-interactibleobject-hero-640px.jpg)


<span data-ttu-id="2908d-113">Nel  **[Toolkit di realtà mista](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, abbiamo creato una serie di script di Unity e prefabs che consenta di creare oggetti si.</span><span class="sxs-lookup"><span data-stu-id="2908d-113">In the **[Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, we have created a series of Unity scripts and prefabs that will help you create Interactable objects.</span></span> <span data-ttu-id="2908d-114">È possibile usare questi per creare qualsiasi tipo di oggetto che l'utente può interagire con, tramite questi stati interazione standard: osservazione, destinazione e premuto.</span><span class="sxs-lookup"><span data-stu-id="2908d-114">You can use these to create any type of object that the user can interact with, using these standard interaction states: observation, targeted and pressed.</span></span> <span data-ttu-id="2908d-115">È possibile personalizzare la progettazione visiva facilmente con le proprie risorse.</span><span class="sxs-lookup"><span data-stu-id="2908d-115">You can easily customize the visual design with your own assets.</span></span> <span data-ttu-id="2908d-116">Le animazioni dettagliate possono essere personalizzate creando e assegnando i clip di animazione corrispondenti per gli stati di interazione nel controller di animazione di Unity o utilizzo di offset e scalabilità.</span><span class="sxs-lookup"><span data-stu-id="2908d-116">Detailed animations can be customized by either creating and assigning corresponding animation clips for the interaction states in the Unity's animation controller or using offset and scale.</span></span> 


## <a name="visual-feedback-for-the-different-input-interaction-states"></a><span data-ttu-id="2908d-117">Indicazioni visive per gli stati di interazione di input diversi</span><span class="sxs-lookup"><span data-stu-id="2908d-117">Visual feedback for the different input interaction states</span></span>

<span data-ttu-id="2908d-118">In realtà mista, poiché gli oggetti holographic vengono combinati con l'ambiente reale, potrebbe essere difficile comprendere quali oggetti sono si.</span><span class="sxs-lookup"><span data-stu-id="2908d-118">In mixed reality, since the holographic objects are mixed with the real-world environment, it could be difficult to understand which objects are interactable.</span></span> <span data-ttu-id="2908d-119">Per gli oggetti si durante l'utilizzo, è importante fornire un feedback visivo differenziato per ogni stato di input.</span><span class="sxs-lookup"><span data-stu-id="2908d-119">For any interactable objects in your experience, it is important to provide differentiated visual feedback for each input state.</span></span> <span data-ttu-id="2908d-120">Ciò consente all'utente di capire quale parte della tua esperienza è si e lo rende la certezza con metodo di interazione tra coerente.</span><span class="sxs-lookup"><span data-stu-id="2908d-120">This helps the user understand which part of your experience is interactable and makes the user confident with consistent interaction method.</span></span>

<span data-ttu-id="2908d-121">Per tutti gli oggetti che l'utente può interagire con, è consigliabile avere diverse indicazioni visive per questi tre stati di input:</span><span class="sxs-lookup"><span data-stu-id="2908d-121">For any objects that user can interact with, we recommended to have different visual feedback for these three input states:</span></span>
* <span data-ttu-id="2908d-122">**Osservazione**: Stato di inattività predefinito dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="2908d-122">**Observation**: Default idle state of the object.</span></span>
* <span data-ttu-id="2908d-123">**Destinazione**: L'oggetto di destinazione con il cursore sguardo, finger puntatore prossimità o movimento del controller.</span><span class="sxs-lookup"><span data-stu-id="2908d-123">**Targeted**: When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
* <span data-ttu-id="2908d-124">**Premuto**: Quando viene premuto l'oggetto con indice puntato movimento, premere un dito o pulsante di selezione del controller di movimento.</span><span class="sxs-lookup"><span data-stu-id="2908d-124">**Pressed**: When the object is pressed with air-tap gesture, finger press or motion controller's select button.</span></span>

<span data-ttu-id="2908d-125">![Pulsante holographic](images/640px-interactibleobject-holographicbutton-650px.jpg)</span><span class="sxs-lookup"><span data-stu-id="2908d-125">![Holographic button](images/640px-interactibleobject-holographicbutton-650px.jpg)</span></span><br>
<span data-ttu-id="2908d-126">*Osservazione dello stato, lo stato di destinazione e lo stato di premuto*</span><span class="sxs-lookup"><span data-stu-id="2908d-126">*Observation state, targeted state, and pressed state*</span></span>

<span data-ttu-id="2908d-127">Nella realtà mista di Windows, è possibile trovare gli esempi dei diversi stati di input nel menu Start e pulsanti della barra di App la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="2908d-127">In Windows Mixed Reality, you can find the examples of visualizing different input states on Start menu and App Bar buttons.</span></span> <span data-ttu-id="2908d-128">È possibile usare tecniche quali l'evidenziazione o la scalabilità per fornire indicazioni visive agli stati di input dell'utente.</span><span class="sxs-lookup"><span data-stu-id="2908d-128">You can use techniques such as highlighting or scaling to provide visual feedback to the user’s input states.</span></span>

<span data-ttu-id="2908d-129">HoloLens 2, poiché supporta mano completamente articolati e rilevamento di input, possiamo fornire affordance aggiuntive in base alla prossimità in messi a disposizione.</span><span class="sxs-lookup"><span data-stu-id="2908d-129">In HoloLens 2, since it supports fully articulated hand tracking input, we can provide additional affordances based on the proximity to the hands.</span></span> <span data-ttu-id="2908d-130">Il [pulsante in 2 HoloLens](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) illustrato in questo esempio.</span><span class="sxs-lookup"><span data-stu-id="2908d-130">The [Button in HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) shows this example.</span></span>

![Pulsante pressable](images/640px-interactibleobject-pressablebutton-650px.jpg)<br>




## <a name="interactable-object-samples"></a><span data-ttu-id="2908d-132">Esempi di oggetti si</span><span class="sxs-lookup"><span data-stu-id="2908d-132">Interactable object samples</span></span>

### <a name="mesh-button"></a><span data-ttu-id="2908d-133">Pulsante mesh</span><span class="sxs-lookup"><span data-stu-id="2908d-133">Mesh button</span></span>

![Pulsante mesh](images/640px-interactibleobject-meshbutton.jpg)

<span data-ttu-id="2908d-135">Questi sono esempi che usano le primitive e maglie 3D importati come oggetti si.</span><span class="sxs-lookup"><span data-stu-id="2908d-135">These are examples using primitives and imported 3D meshes as Interactable objects.</span></span> <span data-ttu-id="2908d-136">È possibile assegnare facilmente diversi valori di scala, offset e il colore per rispondere a ogni stato di interazione di input.</span><span class="sxs-lookup"><span data-stu-id="2908d-136">You can easily assign different scale, offset and color values to respond to each input interaction state.</span></span>

### <a name="toolbar"></a><span data-ttu-id="2908d-137">Barra degli strumenti</span><span class="sxs-lookup"><span data-stu-id="2908d-137">Toolbar</span></span>

![Barra degli strumenti](images/640px-interactibleobject-toolbar.jpg)

<span data-ttu-id="2908d-139">Una barra degli strumenti è un modello diffuso nelle esperienze di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="2908d-139">A toolbar is a widely used pattern in mixed reality experiences.</span></span> <span data-ttu-id="2908d-140">È ad esempio un semplice insieme di pulsanti con altri comportamenti [Billboarding e tag-along](billboarding-and-tag-along.md).</span><span class="sxs-lookup"><span data-stu-id="2908d-140">It is a simple collection of buttons with additional behaviors such as [Billboarding and tag-along](billboarding-and-tag-along.md).</span></span> <span data-ttu-id="2908d-141">Questo esempio usa uno script Billboarding e tag-along dal MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="2908d-141">This example uses a Billboarding and tag-along script from the MixedRealityToolkit.</span></span> <span data-ttu-id="2908d-142">È possibile controllare comportamenti dettagliati inclusi distanza, spostare i valori di velocità e la soglia.</span><span class="sxs-lookup"><span data-stu-id="2908d-142">You can control detailed behaviors including distance, moving speed and threshold values.</span></span>

### <a name="traditional-button"></a><span data-ttu-id="2908d-143">Pulsante tradizionale</span><span class="sxs-lookup"><span data-stu-id="2908d-143">Traditional button</span></span>

![Pulsante tradizionale](images/640px-interactibleobject-traditionalbutton.jpg)

<span data-ttu-id="2908d-145">Questo esempio mostra un pulsante Stile tradizionale 2D.</span><span class="sxs-lookup"><span data-stu-id="2908d-145">This example shows a traditional 2D style button.</span></span> <span data-ttu-id="2908d-146">Ogni stato di input ha una profondità leggermente diverso e una proprietà di animazione.</span><span class="sxs-lookup"><span data-stu-id="2908d-146">Each input state has a slightly different depth and animation property.</span></span>

### <a name="other-examples"></a><span data-ttu-id="2908d-147">Altri esempi</span><span class="sxs-lookup"><span data-stu-id="2908d-147">Other examples</span></span>

<span data-ttu-id="2908d-148">![Pulsante di comando](images/640px-interactibleobject-pushbutton.jpg)</span><span class="sxs-lookup"><span data-stu-id="2908d-148">![Push button](images/640px-interactibleobject-pushbutton.jpg)</span></span><br>
<span data-ttu-id="2908d-149">*Pulsante di comando*</span><span class="sxs-lookup"><span data-stu-id="2908d-149">*Push button*</span></span>
<br>
<span data-ttu-id="2908d-150">![Oggetto vita reale](images/640px-interactibleobject-reallifeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="2908d-150">![Real Life object](images/640px-interactibleobject-reallifeobject.jpg)</span></span><br>
<span data-ttu-id="2908d-151">*Oggetto di uno scenario reale*</span><span class="sxs-lookup"><span data-stu-id="2908d-151">*Real life object*</span></span>

<span data-ttu-id="2908d-152">Con HoloLens, è possibile sfruttare lo spazio fisico.</span><span class="sxs-lookup"><span data-stu-id="2908d-152">With HoloLens, you can leverage physical space.</span></span> <span data-ttu-id="2908d-153">Si immagini un pulsante di comando holographic su una parete fisico.</span><span class="sxs-lookup"><span data-stu-id="2908d-153">Imagine a holographic push button on a physical wall.</span></span> <span data-ttu-id="2908d-154">O che ne dici una tazza di caffè su una tabella reale?</span><span class="sxs-lookup"><span data-stu-id="2908d-154">Or how about a coffee cup on a real table?</span></span> <span data-ttu-id="2908d-155">Uso di modelli 3D importati dalla modellazione del software, è possibile creare un oggetto si che è simile a oggetti di uno scenario reale.</span><span class="sxs-lookup"><span data-stu-id="2908d-155">Using 3D models imported from modeling software, we can create an Interactable object that resembles real life object.</span></span> <span data-ttu-id="2908d-156">Poiché si tratta di un oggetto digitale, possiamo aggiungere interazioni magico scrivendo a esso.</span><span class="sxs-lookup"><span data-stu-id="2908d-156">Since it's a digital object, we can add magical interactions to it.</span></span>

## <a name="interactable-object-in-mixed-reality-toolkit"></a><span data-ttu-id="2908d-157">Oggetto si nel Toolkit di realtà mista</span><span class="sxs-lookup"><span data-stu-id="2908d-157">Interactable object in Mixed Reality Toolkit</span></span>
<span data-ttu-id="2908d-158">È possibile trovare il [esempi di Interactable dell'oggetto nel Toolkit di realtà mista](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)</span><span class="sxs-lookup"><span data-stu-id="2908d-158">You can find the [examples of Interactable object in Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)</span></span>


## <a name="see-also"></a><span data-ttu-id="2908d-159">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2908d-159">See also</span></span>
* [<span data-ttu-id="2908d-160">Pulsante pressable sul Toolkit di realtà mista-Unity</span><span class="sxs-lookup"><span data-stu-id="2908d-160">Pressable Button on Mixed Reality Toolkit-Unity</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [<span data-ttu-id="2908d-161">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="2908d-161">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="2908d-162">Del billboard e tag-along</span><span class="sxs-lookup"><span data-stu-id="2908d-162">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)

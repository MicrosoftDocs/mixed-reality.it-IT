---
title: Visualizzazione dello stato di avanzamento
description: Un controllo di stato fornisce all'utente un feedback nel caso in cui sia in corso un'operazione di lunga durata.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, progettazione, controlli, interfaccia utente, UX
ms.openlocfilehash: d028b8717dae0e04a9a1104a8a4b7803023334ef
ms.sourcegitcommit: 6844930427b658ae31f642c395cd8a3b3cdbf857
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/07/2020
ms.locfileid: "75723210"
---
# <a name="progress-indicator"></a><span data-ttu-id="a036e-104">Indicatore di stato</span><span class="sxs-lookup"><span data-stu-id="a036e-104">Progress indicator</span></span>

<br>

<img src="images/UX/MRTK_ProgressIndicator.gif" alt="Progress ring example in HoloLens" width="940px">

<span data-ttu-id="a036e-105">Un controllo di stato fornisce all'utente un feedback nel caso in cui sia in corso un'operazione di lunga durata.</span><span class="sxs-lookup"><span data-stu-id="a036e-105">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="a036e-106">Può significare che l'utente non può interagire con l'app quando l'indicatore di stato è visibile e può anche indicare quanto è il tempo di attesa stimato, a seconda dell'indicatore usato.</span><span class="sxs-lookup"><span data-stu-id="a036e-106">It can mean that the user cannot interact with the app when the progress indicator is visible, and can also indicate how long the wait time might be, depending on the indicator used.</span></span>

<br>

---

## <a name="types-of-progress"></a><span data-ttu-id="a036e-107">Tipi di stato</span><span class="sxs-lookup"><span data-stu-id="a036e-107">Types of progress</span></span>

<span data-ttu-id="a036e-108">È importante fornire le informazioni sull'utente su ciò che accade.</span><span class="sxs-lookup"><span data-stu-id="a036e-108">It is important to provide the user information about what is happening.</span></span> <span data-ttu-id="a036e-109">In realtà mista gli utenti possono essere facilmente distratti da ambienti fisici o oggetti se l'app non fornisce un feedback visivo efficace.</span><span class="sxs-lookup"><span data-stu-id="a036e-109">In mixed reality users can be easily distracted by physical environment or objects if your app does not gives good visual feedback.</span></span> <span data-ttu-id="a036e-110">Per le situazioni in cui sono necessari alcuni secondi, ad esempio quando i dati vengono caricati o una scena viene aggiornata, è consigliabile visualizzare un indicatore visivo.</span><span class="sxs-lookup"><span data-stu-id="a036e-110">For situations that take a few seconds, such when data is loading or a scene is updating, it is good idea to show a visual indicator.</span></span> <span data-ttu-id="a036e-111">Sono disponibili due opzioni per indicare all'utente che è in corso un'operazione, ovvero un indicatore di **stato** o un **anello di avanzamento**.</span><span class="sxs-lookup"><span data-stu-id="a036e-111">There are two options to show the user that an operation is underway – a **Progress bar** or a **Progress ring**.</span></span>

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a><span data-ttu-id="a036e-112">Barra di stato</span><span class="sxs-lookup"><span data-stu-id="a036e-112">Progress bar</span></span><br>
        <span data-ttu-id="a036e-113">Un indicatore di stato Mostra la percentuale di completamento di un'attività.</span><span class="sxs-lookup"><span data-stu-id="a036e-113">A Progress bar shows the percentage completed of a task.</span></span> <span data-ttu-id="a036e-114">Deve essere usato durante un'operazione la cui durata è nota (determinata), ma lo stato di avanzamento non deve bloccare l'interazione dell'utente con l'app.</span><span class="sxs-lookup"><span data-stu-id="a036e-114">It should be used during an operation whose duration is known (determinate), but it's progress should not block the user's interaction with the app.</span></span><br>
        <br>
        <span data-ttu-id="a036e-115">*Image: esempio di indicatore di stato in HoloLens*</span><span class="sxs-lookup"><span data-stu-id="a036e-115">*Image: Progress bar example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="a036e-116">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="a036e-116">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="a036e-117">esempio ![indicatore di stato in HoloLens](images/640px-progressbar.jpg)</span><span class="sxs-lookup"><span data-stu-id="a036e-117">![Progress bar example in HoloLens](images/640px-progressbar.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-ringbr"></a><span data-ttu-id="a036e-118">Anello di stato</span><span class="sxs-lookup"><span data-stu-id="a036e-118">Progress ring</span></span><br>
        <span data-ttu-id="a036e-119">Un anello di avanzamento ha solo uno stato indeterminato e deve essere usato quando ogni ulteriore interazione con l'utente viene bloccata fino al completamento dell'operazione.</span><span class="sxs-lookup"><span data-stu-id="a036e-119">A Progress ring only has an indeterminate state, and should be used when any further user interaction is blocked until the operation has completed.</span></span><br>
        <br>
        <span data-ttu-id="a036e-120">*Immagine: esempio di anello di stato in HoloLens*</span><span class="sxs-lookup"><span data-stu-id="a036e-120">*Image: Progress ring example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="a036e-121">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="a036e-121">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="a036e-122">esempio di ![dell'anello di stato in HoloLens](images/640px-progressring.jpg)</span><span class="sxs-lookup"><span data-stu-id="a036e-122">![Progress ring example in HoloLens](images/640px-progressring.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-with-a-custom-objectbr"></a><span data-ttu-id="a036e-123">Stato di avanzamento con un oggetto personalizzato</span><span class="sxs-lookup"><span data-stu-id="a036e-123">Progress with a custom object</span></span><br>
        <span data-ttu-id="a036e-124">È possibile aggiungere la personalità e l'identità del marchio dell'app personalizzando il controllo dello stato di avanzamento con oggetti 2D/3D personalizzati.</span><span class="sxs-lookup"><span data-stu-id="a036e-124">You can add to your app's personality and brand identity by customizing the Progress control with your own custom 2D/3D objects.</span></span><br>
        <br>
        <span data-ttu-id="a036e-125">*Immagine: esempio di avanzamento con mesh personalizzato in HoloLens*</span><span class="sxs-lookup"><span data-stu-id="a036e-125">*Image: Progress with custom mesh example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="a036e-126">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="a036e-126">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="a036e-127">esempio di ![stato con mesh personalizzato in HoloLens](images/640px-progresscustom.jpg)</span><span class="sxs-lookup"><span data-stu-id="a036e-127">![Progress with custom mesh example in HoloLens](images/640px-progresscustom.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a><span data-ttu-id="a036e-128">Procedure consigliate</span><span class="sxs-lookup"><span data-stu-id="a036e-128">Best practices</span></span>
* <span data-ttu-id="a036e-129">È strettamente correlato alla visualizzazione dello stato di avanzamento [, in quanto](billboarding-and-tag-along.md) l'utente può facilmente spostarne l'intestazione in uno spazio vuoto e perdere il contesto.</span><span class="sxs-lookup"><span data-stu-id="a036e-129">Tightly couple [billboarding or tag-along](billboarding-and-tag-along.md) to the display of Progress since the user can easily move their head into empty space and lose context.</span></span> <span data-ttu-id="a036e-130">È possibile che l'app si trovi in modo anomalo se l'utente non è in grado di visualizzare alcun elemento.</span><span class="sxs-lookup"><span data-stu-id="a036e-130">Your app might look like it has crashed if the user is unable to see anything.</span></span> <span data-ttu-id="a036e-131">Il tabellone e i tag-along sono incorporati nella prefabbrica di avanzamento.</span><span class="sxs-lookup"><span data-stu-id="a036e-131">Billboarding and tag-along is built into the Progress prefab.</span></span>
* <span data-ttu-id="a036e-132">È sempre opportuno fornire informazioni sullo stato relative a ciò che accade all'utente.</span><span class="sxs-lookup"><span data-stu-id="a036e-132">It's always good to provide status information about what is happening to the user.</span></span> <span data-ttu-id="a036e-133">Il prefabbricato di avanzamento fornisce vari stili visivi, tra cui lo stato di avanzamento del tipo di anello standard di Windows.</span><span class="sxs-lookup"><span data-stu-id="a036e-133">The Progress prefab provides various visual styles including the Windows standard ring-type progress for providing status.</span></span> <span data-ttu-id="a036e-134">È anche possibile usare una mesh personalizzata con un'animazione se si vuole che lo stile dello stato di avanzamento sia allineato al marchio dell'app.</span><span class="sxs-lookup"><span data-stu-id="a036e-134">You can also use a custom mesh with an animation if you want the style of your progress to align to your app’s brand.</span></span>

<br>

---

## <a name="progress-indicator-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="a036e-135">Indicatore di stato in MRTK (Mixed Reality Toolkit) per Unity</span><span class="sxs-lookup"><span data-stu-id="a036e-135">Progress indicator in MRTK (Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="a036e-136">MRTK-prefabbricati indicatore di stato</span><span class="sxs-lookup"><span data-stu-id="a036e-136">MRTK - Progress indicator prefabs</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/ProgressIndicators)
* [<span data-ttu-id="a036e-137">MRTK-servizio di transizione della scena</span><span class="sxs-lookup"><span data-stu-id="a036e-137">MRTK - Scene transition service</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Extensions/SceneTransitionService/SceneTransitionServiceOverview.html)


<br>

---

## <a name="see-also"></a><span data-ttu-id="a036e-138">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="a036e-138">See also</span></span>

* [<span data-ttu-id="a036e-139">Cursori</span><span class="sxs-lookup"><span data-stu-id="a036e-139">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="a036e-140">Raggio della mano</span><span class="sxs-lookup"><span data-stu-id="a036e-140">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="a036e-141">Button</span><span class="sxs-lookup"><span data-stu-id="a036e-141">Button</span></span>](button.md)
* [<span data-ttu-id="a036e-142">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="a036e-142">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="a036e-143">Rettangolo di selezione e barra dell'app</span><span class="sxs-lookup"><span data-stu-id="a036e-143">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="a036e-144">Manipolazione</span><span class="sxs-lookup"><span data-stu-id="a036e-144">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="a036e-145">Menu a mano</span><span class="sxs-lookup"><span data-stu-id="a036e-145">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="a036e-146">Menu adiacente</span><span class="sxs-lookup"><span data-stu-id="a036e-146">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="a036e-147">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="a036e-147">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="a036e-148">Comando vocale</span><span class="sxs-lookup"><span data-stu-id="a036e-148">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="a036e-149">Tastiera</span><span class="sxs-lookup"><span data-stu-id="a036e-149">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="a036e-150">Descrizione comando</span><span class="sxs-lookup"><span data-stu-id="a036e-150">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="a036e-151">Slate</span><span class="sxs-lookup"><span data-stu-id="a036e-151">Slate</span></span>](slate.md)
* [<span data-ttu-id="a036e-152">Dispositivo di scorrimento</span><span class="sxs-lookup"><span data-stu-id="a036e-152">Slider</span></span>](slider.md)
* [<span data-ttu-id="a036e-153">Shader</span><span class="sxs-lookup"><span data-stu-id="a036e-153">Shader</span></span>](shader.md)
* [<span data-ttu-id="a036e-154">Billboarding e tag-along</span><span class="sxs-lookup"><span data-stu-id="a036e-154">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="a036e-155">Visualizzazione dello stato</span><span class="sxs-lookup"><span data-stu-id="a036e-155">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="a036e-156">Magnetismo di superficie</span><span class="sxs-lookup"><span data-stu-id="a036e-156">Surface magnetism</span></span>](surface-magnetism.md)

---
title: Visualizzazione dello stato di avanzamento
description: Un controllo di stato fornisce all'utente un feedback nel caso in cui sia in corso un'operazione di lunga durata.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, progettazione, controlli, interfaccia utente, UX
ms.openlocfilehash: 43b4802e7c821c98c847509ace950f381da12f95
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437533"
---
# <a name="displaying-progress"></a><span data-ttu-id="e7af3-104">Visualizzazione dello stato di avanzamento</span><span class="sxs-lookup"><span data-stu-id="e7af3-104">Displaying progress</span></span>

<br>

<img src="images/HoloLens2_Loader.gif" alt="Progress ring example in HoloLens" width="940px">

<span data-ttu-id="e7af3-105">Un controllo di stato fornisce all'utente un feedback nel caso in cui sia in corso un'operazione di lunga durata.</span><span class="sxs-lookup"><span data-stu-id="e7af3-105">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="e7af3-106">Può significare che l'utente non può interagire con l'app quando l'indicatore di stato è visibile e può anche indicare quanto è il tempo di attesa stimato, a seconda dell'indicatore usato.</span><span class="sxs-lookup"><span data-stu-id="e7af3-106">It can mean that the user cannot interact with the app when the progress indicator is visible, and can also indicate how long the wait time might be, depending on the indicator used.</span></span>

<br>

---

## <a name="types-of-progress"></a><span data-ttu-id="e7af3-107">Tipi di stato</span><span class="sxs-lookup"><span data-stu-id="e7af3-107">Types of progress</span></span>

<span data-ttu-id="e7af3-108">È importante fornire le informazioni sull'utente su ciò che accade.</span><span class="sxs-lookup"><span data-stu-id="e7af3-108">It is important to provide the user information about what is happening.</span></span> <span data-ttu-id="e7af3-109">In realtà mista gli utenti possono essere facilmente distratti da ambienti fisici o oggetti se l'app non fornisce un feedback visivo efficace.</span><span class="sxs-lookup"><span data-stu-id="e7af3-109">In mixed reality users can be easily distracted by physical environment or objects if your app does not gives good visual feedback.</span></span> <span data-ttu-id="e7af3-110">Per le situazioni in cui sono necessari alcuni secondi, ad esempio quando i dati vengono caricati o una scena viene aggiornata, è consigliabile visualizzare un indicatore visivo.</span><span class="sxs-lookup"><span data-stu-id="e7af3-110">For situations that take a few seconds, such when data is loading or a scene is updating, it is good idea to show a visual indicator.</span></span> <span data-ttu-id="e7af3-111">Sono disponibili due opzioni per indicare all'utente che è in corso un'operazione, ovvero un indicatore di **stato** o un **anello di avanzamento**.</span><span class="sxs-lookup"><span data-stu-id="e7af3-111">There are two options to show the user that an operation is underway – a **Progress bar** or a **Progress ring**.</span></span>

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a><span data-ttu-id="e7af3-112">Barra di stato</span><span class="sxs-lookup"><span data-stu-id="e7af3-112">Progress bar</span></span><br>
        <span data-ttu-id="e7af3-113">Un indicatore di stato Mostra la percentuale di completamento di un'attività.</span><span class="sxs-lookup"><span data-stu-id="e7af3-113">A Progress bar shows the percentage completed of a task.</span></span> <span data-ttu-id="e7af3-114">Deve essere usato durante un'operazione la cui durata è nota (determinata), ma lo stato di avanzamento non deve bloccare l'interazione dell'utente con l'app.</span><span class="sxs-lookup"><span data-stu-id="e7af3-114">It should be used during an operation whose duration is known (determinate), but it's progress should not block the user's interaction with the app.</span></span><br>
        <br>
        <span data-ttu-id="e7af3-115">*Image: esempio di indicatore di stato in HoloLens*</span><span class="sxs-lookup"><span data-stu-id="e7af3-115">*Image: Progress bar example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="e7af3-116">spazio ![](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="e7af3-116">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="e7af3-117">esempio ![indicatore di stato in HoloLens](images/640px-progressbar.jpg)</span><span class="sxs-lookup"><span data-stu-id="e7af3-117">![Progress bar example in HoloLens](images/640px-progressbar.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-ringbr"></a><span data-ttu-id="e7af3-118">Anello di stato</span><span class="sxs-lookup"><span data-stu-id="e7af3-118">Progress ring</span></span><br>
        <span data-ttu-id="e7af3-119">Un anello di avanzamento ha solo uno stato indeterminato e deve essere usato quando ogni ulteriore interazione con l'utente viene bloccata fino al completamento dell'operazione.</span><span class="sxs-lookup"><span data-stu-id="e7af3-119">A Progress ring only has an indeterminate state, and should be used when any further user interaction is blocked until the operation has completed.</span></span><br>
        <br>
        <span data-ttu-id="e7af3-120">*Immagine: esempio di anello di stato in HoloLens*</span><span class="sxs-lookup"><span data-stu-id="e7af3-120">*Image: Progress ring example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="e7af3-121">spazio ![](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="e7af3-121">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="e7af3-122">esempio di ![dell'anello di stato in HoloLens](images/640px-progressring.jpg)</span><span class="sxs-lookup"><span data-stu-id="e7af3-122">![Progress ring example in HoloLens](images/640px-progressring.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-with-a-custom-objectbr"></a><span data-ttu-id="e7af3-123">Stato di avanzamento con un oggetto personalizzato</span><span class="sxs-lookup"><span data-stu-id="e7af3-123">Progress with a custom object</span></span><br>
        <span data-ttu-id="e7af3-124">È possibile aggiungere la personalità e l'identità del marchio dell'app personalizzando il controllo dello stato di avanzamento con oggetti 2D/3D personalizzati.</span><span class="sxs-lookup"><span data-stu-id="e7af3-124">You can add to your app's personality and brand identity by customizing the Progress control with your own custom 2D/3D objects.</span></span><br>
        <br>
        <span data-ttu-id="e7af3-125">*Immagine: esempio di avanzamento con mesh personalizzato in HoloLens*</span><span class="sxs-lookup"><span data-stu-id="e7af3-125">*Image: Progress with custom mesh example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="e7af3-126">spazio ![](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="e7af3-126">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="e7af3-127">esempio di ![stato con mesh personalizzato in HoloLens](images/640px-progresscustom.jpg)</span><span class="sxs-lookup"><span data-stu-id="e7af3-127">![Progress with custom mesh example in HoloLens](images/640px-progresscustom.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a><span data-ttu-id="e7af3-128">Procedure consigliate</span><span class="sxs-lookup"><span data-stu-id="e7af3-128">Best practices</span></span>
* <span data-ttu-id="e7af3-129">È strettamente correlato alla visualizzazione dello stato di avanzamento [, in quanto](billboarding-and-tag-along.md) l'utente può facilmente spostarne l'intestazione in uno spazio vuoto e perdere il contesto.</span><span class="sxs-lookup"><span data-stu-id="e7af3-129">Tightly couple [billboarding or tag-along](billboarding-and-tag-along.md) to the display of Progress since the user can easily move their head into empty space and lose context.</span></span> <span data-ttu-id="e7af3-130">È possibile che l'app si trovi in modo anomalo se l'utente non è in grado di visualizzare alcun elemento.</span><span class="sxs-lookup"><span data-stu-id="e7af3-130">Your app might look like it has crashed if the user is unable to see anything.</span></span> <span data-ttu-id="e7af3-131">Il tabellone e i tag-along sono incorporati nella prefabbrica di avanzamento.</span><span class="sxs-lookup"><span data-stu-id="e7af3-131">Billboarding and tag-along is built into the Progress prefab.</span></span>
* <span data-ttu-id="e7af3-132">È sempre opportuno fornire informazioni sullo stato relative a ciò che accade all'utente.</span><span class="sxs-lookup"><span data-stu-id="e7af3-132">It's always good to provide status information about what is happening to the user.</span></span> <span data-ttu-id="e7af3-133">Il prefabbricato di avanzamento fornisce vari stili visivi, tra cui lo stato di avanzamento del tipo di anello standard di Windows.</span><span class="sxs-lookup"><span data-stu-id="e7af3-133">The Progress prefab provides various visual styles including the Windows standard ring-type progress for providing status.</span></span> <span data-ttu-id="e7af3-134">È anche possibile usare una mesh personalizzata con un'animazione se si vuole che lo stile dello stato di avanzamento sia allineato al marchio dell'app.</span><span class="sxs-lookup"><span data-stu-id="e7af3-134">You can also use a custom mesh with an animation if you want the style of your progress to align to your app’s brand.</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="e7af3-135">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="e7af3-135">See also</span></span>
* [<span data-ttu-id="e7af3-136">Script di avanzamento e prefabbricati sul Toolkit di realtà mista</span><span class="sxs-lookup"><span data-stu-id="e7af3-136">Progress scripts and prefabs on Mixed Reality Toolkit</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Loader)
* [<span data-ttu-id="e7af3-137">Rettangolo di delimitazione</span><span class="sxs-lookup"><span data-stu-id="e7af3-137">Bounding box</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="e7af3-138">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="e7af3-138">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="e7af3-139">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="e7af3-139">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="e7af3-140">Billboarding e tag-along</span><span class="sxs-lookup"><span data-stu-id="e7af3-140">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)

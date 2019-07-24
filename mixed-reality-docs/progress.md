---
title: Visualizzazione dello stato di avanzamento
description: Un controllo di stato fornisce all'utente un feedback nel caso in cui sia in corso un'operazione di lunga durata.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, progettazione, controlli, interfaccia utente, UX
ms.openlocfilehash: 84853a23a73bbece30c1f96b83e586642f3ab762
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523258"
---
# <a name="displaying-progress"></a><span data-ttu-id="f800e-104">Visualizzazione dello stato di avanzamento</span><span class="sxs-lookup"><span data-stu-id="f800e-104">Displaying progress</span></span>

<span data-ttu-id="f800e-105">Un controllo di stato fornisce all'utente un feedback nel caso in cui sia in corso un'operazione di lunga durata.</span><span class="sxs-lookup"><span data-stu-id="f800e-105">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="f800e-106">Può significare che l'utente non può interagire con l'app quando l'indicatore di stato è visibile e può anche indicare quanto è il tempo di attesa stimato, a seconda dell'indicatore usato.</span><span class="sxs-lookup"><span data-stu-id="f800e-106">It can mean that the user cannot interact with the app when the progress indicator is visible, and can also indicate how long the wait time might be, depending on the indicator used.</span></span>

<span data-ttu-id="f800e-107">![Esempio di anello di stato in HoloLens](images/HoloLens2_Loader.gif)</span><span class="sxs-lookup"><span data-stu-id="f800e-107">![Progress ring example in HoloLens](images/HoloLens2_Loader.gif)</span></span><br>
<span data-ttu-id="f800e-108">*Esempio di anello di stato in HoloLens*</span><span class="sxs-lookup"><span data-stu-id="f800e-108">*Progress ring example in HoloLens*</span></span>

## <a name="types-of-progress"></a><span data-ttu-id="f800e-109">Tipi di stato</span><span class="sxs-lookup"><span data-stu-id="f800e-109">Types of progress</span></span>

<span data-ttu-id="f800e-110">È importante fornire le informazioni sull'utente su ciò che accade.</span><span class="sxs-lookup"><span data-stu-id="f800e-110">It is important to provide the user information about what is happening.</span></span> <span data-ttu-id="f800e-111">In realtà mista gli utenti possono essere facilmente distratti da ambienti fisici o oggetti se l'app non fornisce un feedback visivo efficace.</span><span class="sxs-lookup"><span data-stu-id="f800e-111">In mixed reality users can be easily distracted by physical environment or objects if your app does not gives good visual feedback.</span></span> <span data-ttu-id="f800e-112">Per le situazioni in cui sono necessari alcuni secondi, ad esempio quando i dati vengono caricati o una scena viene aggiornata, è consigliabile visualizzare un indicatore visivo.</span><span class="sxs-lookup"><span data-stu-id="f800e-112">For situations that take a few seconds, such when data is loading or a scene is updating, it is good idea to show a visual indicator.</span></span> <span data-ttu-id="f800e-113">Sono disponibili due opzioni per indicare all'utente che è in corso un'operazione, ovvero un indicatore di **stato** o un **anello di avanzamento**.</span><span class="sxs-lookup"><span data-stu-id="f800e-113">There are two options to show the user that an operation is underway – a **Progress bar** or a **Progress ring**.</span></span>

### <a name="progress-bar"></a><span data-ttu-id="f800e-114">Indicatore di stato</span><span class="sxs-lookup"><span data-stu-id="f800e-114">Progress bar</span></span>

![Esempio di indicatore di stato in HoloLens](images/640px-progressbar.jpg)

<span data-ttu-id="f800e-116">Un indicatore di stato Mostra la percentuale di completamento di un'attività.</span><span class="sxs-lookup"><span data-stu-id="f800e-116">A Progress bar shows the percentage completed of a task.</span></span> <span data-ttu-id="f800e-117">Deve essere usato durante un'operazione la cui durata è nota (determinata), ma lo stato di avanzamento non deve bloccare l'interazione dell'utente con l'app.</span><span class="sxs-lookup"><span data-stu-id="f800e-117">It should be used during an operation whose duration is known (determinate), but it's progress should not block the user's interaction with the app.</span></span>

### <a name="progress-ring"></a><span data-ttu-id="f800e-118">Anello di stato</span><span class="sxs-lookup"><span data-stu-id="f800e-118">Progress ring</span></span>

![Esempio di anello di stato in HoloLens](images/640px-progressring.jpg)

<span data-ttu-id="f800e-120">Un anello di avanzamento ha solo uno stato indeterminato e deve essere usato quando ogni ulteriore interazione con l'utente viene bloccata fino al completamento dell'operazione.</span><span class="sxs-lookup"><span data-stu-id="f800e-120">A Progress ring only has an indeterminate state, and should be used when any further user interaction is blocked until the operation has completed.</span></span>

### <a name="progress-with-a-custom-object"></a><span data-ttu-id="f800e-121">Stato di avanzamento con un oggetto personalizzato</span><span class="sxs-lookup"><span data-stu-id="f800e-121">Progress with a custom object</span></span>

![Esempio di avanzamento con mesh personalizzato in HoloLens](images/640px-progresscustom.jpg)

<span data-ttu-id="f800e-123">È possibile aggiungere la personalità e l'identità del marchio dell'app personalizzando il controllo dello stato di avanzamento con oggetti 2D/3D personalizzati.</span><span class="sxs-lookup"><span data-stu-id="f800e-123">You can add to your app's personality and brand identity by customizing the Progress control with your own custom 2D/3D objects.</span></span>

## <a name="best-practices"></a><span data-ttu-id="f800e-124">Procedure consigliate</span><span class="sxs-lookup"><span data-stu-id="f800e-124">Best practices</span></span>
* <span data-ttu-id="f800e-125">È strettamente correlato [alla visualizzazione](billboarding-and-tag-along.md) dello stato di avanzamento, in quanto l'utente può facilmente spostarne l'intestazione in uno spazio vuoto e perdere il contesto.</span><span class="sxs-lookup"><span data-stu-id="f800e-125">Tightly couple [billboarding or tag-along](billboarding-and-tag-along.md) to the display of Progress since the user can easily move their head into empty space and lose context.</span></span> <span data-ttu-id="f800e-126">È possibile che l'app si trovi in modo anomalo se l'utente non è in grado di visualizzare alcun elemento.</span><span class="sxs-lookup"><span data-stu-id="f800e-126">Your app might look like it has crashed if the user is unable to see anything.</span></span> <span data-ttu-id="f800e-127">Il tabellone e i tag-along sono incorporati nella prefabbrica di avanzamento.</span><span class="sxs-lookup"><span data-stu-id="f800e-127">Billboarding and tag-along is built into the Progress prefab.</span></span>
* <span data-ttu-id="f800e-128">È sempre opportuno fornire informazioni sullo stato relative a ciò che accade all'utente.</span><span class="sxs-lookup"><span data-stu-id="f800e-128">It's always good to provide status information about what is happening to the user.</span></span> <span data-ttu-id="f800e-129">Il prefabbricato di avanzamento fornisce vari stili visivi, tra cui lo stato di avanzamento del tipo di anello standard di Windows.</span><span class="sxs-lookup"><span data-stu-id="f800e-129">The Progress prefab provides various visual styles including the Windows standard ring-type progress for providing status.</span></span> <span data-ttu-id="f800e-130">È anche possibile usare una mesh personalizzata con un'animazione se si vuole che lo stile dello stato di avanzamento sia allineato al marchio dell'app.</span><span class="sxs-lookup"><span data-stu-id="f800e-130">You can also use a custom mesh with an animation if you want the style of your progress to align to your app’s brand.</span></span>

## <a name="see-also"></a><span data-ttu-id="f800e-131">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f800e-131">See also</span></span>
* [<span data-ttu-id="f800e-132">Script di avanzamento e prefabbricati sul Toolkit di realtà mista</span><span class="sxs-lookup"><span data-stu-id="f800e-132">Progress scripts and prefabs on Mixed Reality Toolkit</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Loader)
* [<span data-ttu-id="f800e-133">Rettangolo di delimitazione</span><span class="sxs-lookup"><span data-stu-id="f800e-133">Bounding box</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="f800e-134">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="f800e-134">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="f800e-135">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="f800e-135">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="f800e-136">Billboarding e tag-along</span><span class="sxs-lookup"><span data-stu-id="f800e-136">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)

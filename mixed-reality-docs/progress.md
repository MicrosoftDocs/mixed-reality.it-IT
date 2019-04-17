---
title: Visualizzazione dello stato
description: Un controllo di stato fornisce all'utente un feedback nel caso in cui sia in corso un'operazione di lunga durata.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, progettazione, i controlli, dell'interfaccia utente, esperienza utente
ms.openlocfilehash: 9edddc7800f0d7334d1ceba97b9a06fd6d4580ac
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603212"
---
# <a name="displaying-progress"></a><span data-ttu-id="1cad9-104">Visualizzazione dello stato</span><span class="sxs-lookup"><span data-stu-id="1cad9-104">Displaying progress</span></span>

<span data-ttu-id="1cad9-105">Un controllo di stato fornisce all'utente un feedback nel caso in cui sia in corso un'operazione di lunga durata.</span><span class="sxs-lookup"><span data-stu-id="1cad9-105">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="1cad9-106">Può significare che l'utente non può interagire con l'app quando l'indicatore di stato è visibile e può anche indicare quanto è il tempo di attesa stimato, a seconda dell'indicatore usato.</span><span class="sxs-lookup"><span data-stu-id="1cad9-106">It can mean that the user cannot interact with the app when the progress indicator is visible, and can also indicate how long the wait time might be, depending on the indicator used.</span></span>

<span data-ttu-id="1cad9-107">![Esempio di anello lo stato di avanzamento in HoloLens](images/640px-progress-hero.jpg)</span><span class="sxs-lookup"><span data-stu-id="1cad9-107">![Progress ring example in HoloLens](images/640px-progress-hero.jpg)</span></span><br>
<span data-ttu-id="1cad9-108">*Esempio di anello lo stato di avanzamento in HoloLens*</span><span class="sxs-lookup"><span data-stu-id="1cad9-108">*Progress ring example in HoloLens*</span></span>

## <a name="types-of-progress"></a><span data-ttu-id="1cad9-109">Tipi di stato</span><span class="sxs-lookup"><span data-stu-id="1cad9-109">Types of progress</span></span>

<span data-ttu-id="1cad9-110">È importante fornire informazioni su ciò che accade.</span><span class="sxs-lookup"><span data-stu-id="1cad9-110">It is important to provide the user information about what is happening.</span></span> <span data-ttu-id="1cad9-111">Nella realtà mista agli utenti possono essere facilmente addirittura distratti dalla presenza ambiente fisico o oggetti se l'app non offre buone feedback visivo.</span><span class="sxs-lookup"><span data-stu-id="1cad9-111">In mixed reality users can be easily distracted by physical environment or objects if your app does not gives good visual feedback.</span></span> <span data-ttu-id="1cad9-112">Situazioni in cui richiedere alcuni secondi, ad esempio durante il caricamento di dati o una scena è l'aggiornamento, è consigliabile per mostrare un indicatore visivo.</span><span class="sxs-lookup"><span data-stu-id="1cad9-112">For situations that take a few seconds, such when data is loading or a scene is updating, it is good idea to show a visual indicator.</span></span> <span data-ttu-id="1cad9-113">Sono disponibili due opzioni per mostrare all'utente che un'operazione è in corso: una **sulla barra di stato di avanzamento** o una **anello di stato**.</span><span class="sxs-lookup"><span data-stu-id="1cad9-113">There are two options to show the user that an operation is underway – a **Progress bar** or a **Progress ring**.</span></span>

### <a name="progress-bar"></a><span data-ttu-id="1cad9-114">Indicatore di stato</span><span class="sxs-lookup"><span data-stu-id="1cad9-114">Progress bar</span></span>

![Esempio di barra di stato di avanzamento in HoloLens](images/640px-progressbar.jpg)

<span data-ttu-id="1cad9-116">Un indicatore di stato Mostra la percentuale di completamento di un'attività.</span><span class="sxs-lookup"><span data-stu-id="1cad9-116">A Progress bar shows the percentage completed of a task.</span></span> <span data-ttu-id="1cad9-117">Deve essere usato durante un'operazione la cui durata è noto (indicatore), ma lo stato di avanzamento non deve bloccare l'interazione dell'utente con l'app.</span><span class="sxs-lookup"><span data-stu-id="1cad9-117">It should be used during an operation whose duration is known (determinate), but it's progress should not block the user's interaction with the app.</span></span>

### <a name="progress-ring"></a><span data-ttu-id="1cad9-118">Anello di stato</span><span class="sxs-lookup"><span data-stu-id="1cad9-118">Progress ring</span></span>

![Esempio di anello lo stato di avanzamento in HoloLens](images/640px-progressring.jpg)

<span data-ttu-id="1cad9-120">Solo un anello di stato ha uno stato indeterminato e deve essere usato quando qualsiasi ulteriore interazione dell'utente viene bloccata fino al completamento dell'operazione.</span><span class="sxs-lookup"><span data-stu-id="1cad9-120">A Progress ring only has an indeterminate state, and should be used when any further user interaction is blocked until the operation has completed.</span></span>

### <a name="progress-with-a-custom-object"></a><span data-ttu-id="1cad9-121">Stato di avanzamento con un oggetto personalizzato</span><span class="sxs-lookup"><span data-stu-id="1cad9-121">Progress with a custom object</span></span>

![Stato di avanzamento con esempio di trama personalizzati in HoloLens](images/640px-progresscustom.jpg)

<span data-ttu-id="1cad9-123">È possibile aggiungere all'app personalità e all'identità del marchio personalizzando il controllo di stato di avanzamento con oggetti 2D e 3D personalizzati.</span><span class="sxs-lookup"><span data-stu-id="1cad9-123">You can add to your app's personality and brand identity by customizing the Progress control with your own custom 2D/3D objects.</span></span>

## <a name="best-practices"></a><span data-ttu-id="1cad9-124">Procedure consigliate</span><span class="sxs-lookup"><span data-stu-id="1cad9-124">Best practices</span></span>
* <span data-ttu-id="1cad9-125">Uno stretto accoppiamento [del billboard o tag-along](billboarding-and-tag-along.md) per la visualizzazione dello stato di avanzamento poiché l'utente può facilmente spostare propria testa in uno spazio vuoto e perdere contesto.</span><span class="sxs-lookup"><span data-stu-id="1cad9-125">Tightly couple [billboarding or tag-along](billboarding-and-tag-along.md) to the display of Progress since the user can easily move their head into empty space and lose context.</span></span> <span data-ttu-id="1cad9-126">L'app potrebbe sembrare che è arrestato in modo anomalo se l'utente non riesce a visualizzare i risultati.</span><span class="sxs-lookup"><span data-stu-id="1cad9-126">Your app might look like it has crashed if the user is unable to see anything.</span></span> <span data-ttu-id="1cad9-127">Billboarding e tag-along è incorporata nel prefab lo stato di avanzamento.</span><span class="sxs-lookup"><span data-stu-id="1cad9-127">Billboarding and tag-along is built into the Progress prefab.</span></span>
* <span data-ttu-id="1cad9-128">È sempre consigliabile fornire informazioni sullo stato relative all'utente ciò che accade.</span><span class="sxs-lookup"><span data-stu-id="1cad9-128">It's always good to provide status information about what is happening to the user.</span></span> <span data-ttu-id="1cad9-129">Il prefab lo stato di avanzamento fornisce diversi stili tra cui lo stato di ring-tipo standard di Windows per fornire lo stato.</span><span class="sxs-lookup"><span data-stu-id="1cad9-129">The Progress prefab provides various visual styles including the Windows standard ring-type progress for providing status.</span></span> <span data-ttu-id="1cad9-130">È anche possibile usare una rete mesh di personalizzati con un'animazione se si desidera che lo stile di avanzamento in modo da allinearsi al marchio dell'app.</span><span class="sxs-lookup"><span data-stu-id="1cad9-130">You can also use a custom mesh with an animation if you want the style of your progress to align to your app’s brand.</span></span>

## <a name="see-also"></a><span data-ttu-id="1cad9-131">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1cad9-131">See also</span></span>
* [<span data-ttu-id="1cad9-132">Gli script e prefabs per lo stato di avanzamento nel Toolkit di realtà mista</span><span class="sxs-lookup"><span data-stu-id="1cad9-132">Scripts and prefabs for Progress on Mixed Reality Toolkit</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_ProgressExample.md)
* [<span data-ttu-id="1cad9-133">Oggetto si</span><span class="sxs-lookup"><span data-stu-id="1cad9-133">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="1cad9-134">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="1cad9-134">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="1cad9-135">Del billboard e tag-along</span><span class="sxs-lookup"><span data-stu-id="1cad9-135">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)

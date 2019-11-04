---
title: Controller di movimento e Hands
description: Panoramica dell'interazione tra controller di movimento e Hands
author: shengkait
ms.author: shentan
ms.date: 04/26/2019
ms.topic: article
keywords: Realtà mista, mani, controller di movimento, interazione, progettazione
ms.openlocfilehash: 395862fe987244e2af70bb6794caa91e243cd076
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435168"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="c3722-104">Controller di movimento e Hands</span><span class="sxs-lookup"><span data-stu-id="c3722-104">Hands and motion controllers</span></span>
## <a name="scenarios"></a><span data-ttu-id="c3722-105">Scenari</span><span class="sxs-lookup"><span data-stu-id="c3722-105">Scenarios</span></span>
<span data-ttu-id="c3722-106">Se si sceglie di adottare questo modello di interazione dopo aver letto la [Panoramica sull'interazione](interaction-fundamentals.md), significa che si sta sviluppando un'applicazione che richiede agli utenti di usare due mani per interagire con il mondo olografico.</span><span class="sxs-lookup"><span data-stu-id="c3722-106">If you choose to adopt this interaction model after reading the [interaction overview](interaction-fundamentals.md), it means that you are developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="c3722-107">L'applicazione è in grado di raggiungere l'obiettivo di rimuovere il limite tra virtuale e fisico.</span><span class="sxs-lookup"><span data-stu-id="c3722-107">Your application is going to achieve the goal of removing the boundary between virtual and physical.</span></span>

<span data-ttu-id="c3722-108">Alcuni scenari specifici potrebbero essere:</span><span class="sxs-lookup"><span data-stu-id="c3722-108">Some specific scenarios might be:</span></span>
* <span data-ttu-id="c3722-109">Fornire schermate virtuali 2D per gli Information Worker con interfaccia utente affordances per visualizzare e controllare il contenuto</span><span class="sxs-lookup"><span data-stu-id="c3722-109">Providing information workers 2D virtual screens with UI affordances to display and control content</span></span>
* <span data-ttu-id="c3722-110">Esercitazione e guide per i ruoli di lavoro di prima linea per le linee di assemblaggio Factory</span><span class="sxs-lookup"><span data-stu-id="c3722-110">Providing first line workers tutorials and guides for factory assembly lines</span></span>
* <span data-ttu-id="c3722-111">Sviluppo di strumenti professionali per assistere e educare professionisti medici</span><span class="sxs-lookup"><span data-stu-id="c3722-111">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="c3722-112">Uso di oggetti virtuali 3D per decorare il mondo reale o creare un secondo mondo</span><span class="sxs-lookup"><span data-stu-id="c3722-112">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="c3722-113">Creazione di servizi e giochi location based usando il mondo reale come sfondo</span><span class="sxs-lookup"><span data-stu-id="c3722-113">Creating location based services and games using the real world as a background</span></span>

<br>

---

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="c3722-114">Modalità di controllo delle mani e del movimento</span><span class="sxs-lookup"><span data-stu-id="c3722-114">Hands and motion controllers modalities</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="c3722-115">[![manipolazione diretta con mani](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)</span><span class="sxs-lookup"><span data-stu-id="c3722-115">[![Direct manipulation with hands](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)</span></span><br>
       ### <a name="direct-manipulation-with-handsdirect-manipulationmdbr"></a>[<span data-ttu-id="c3722-116">Manipolazione diretta con le mani</span><span class="sxs-lookup"><span data-stu-id="c3722-116">Direct manipulation with hands</span></span>](direct-manipulation.md)<br>
       <span data-ttu-id="c3722-117">Si tratta di una modalità sfruttando la potenza di Hands, con cui gli utenti sono in grado di toccare e modificare direttamente gli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="c3722-117">This is a modality leveraging the power of hands, with which users are capable of touching and manipulating the holograms directly.</span></span> <span data-ttu-id="c3722-118">Sfruttando le esperienze quotidiane e fornendo affordances visivi appropriati, gli utenti possono usare lo stesso modo per modificare gli oggetti reali per interagire con quelli virtuali.</span><span class="sxs-lookup"><span data-stu-id="c3722-118">By leveraging daily life experiences and providing proper visual affordances, users are able to use the same way of manipulating real world objects to interact with virtual ones.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c3722-119">[![punto e commit con hands](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)</span><span class="sxs-lookup"><span data-stu-id="c3722-119">[![Point and commit with hands](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)</span></span><br>
        ### <a name="point-and-commit-with-handspoint-and-commitmdbr"></a>[<span data-ttu-id="c3722-120">Puntamento e commit con le mani</span><span class="sxs-lookup"><span data-stu-id="c3722-120">Point and commit with hands</span></span>](point-and-commit.md)<br>
        <span data-ttu-id="c3722-121">Questa modalità consente agli utenti di interagire con gli ologrammi a distanza.</span><span class="sxs-lookup"><span data-stu-id="c3722-121">This modality empowers users to interact with holograms in a distance.</span></span> <span data-ttu-id="c3722-122">Consente agli utenti di sfruttare al meglio i dintorni.</span><span class="sxs-lookup"><span data-stu-id="c3722-122">It enables users to make the best use of surroundings.</span></span> <span data-ttu-id="c3722-123">Gli utenti possono posizionare gli ologrammi ovunque e possono comunque accedervi da qualsiasi distanza.</span><span class="sxs-lookup"><span data-stu-id="c3722-123">Users can place holograms anywhere and can still access them from any distances.</span></span> <span data-ttu-id="c3722-124">I modelli e i movimenti mentali per controllare e modificare gli ologrammi 2D e 3D sono sincronizzati con quelli di manipolazione diretta.</span><span class="sxs-lookup"><span data-stu-id="c3722-124">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c3722-125">[controller di movimento ![](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)</span><span class="sxs-lookup"><span data-stu-id="c3722-125">[![Motion controllers](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)</span></span><br>
       ### <a name="motion-controllersmotion-controllersmdbr"></a>[<span data-ttu-id="c3722-126">Controller del movimento</span><span class="sxs-lookup"><span data-stu-id="c3722-126">Motion controllers</span></span>](motion-controllers.md)<br>
       <span data-ttu-id="c3722-127">I controller di movimento sono strumenti che estendono le funzionalità fisiche dell'utente fornendo interazioni precise in un'ampia gamma di distanze durante l'uso di una o entrambe le mani.</span><span class="sxs-lookup"><span data-stu-id="c3722-127">Motion controllers are tools that extend the user's physical capabilities by providing precise interactions across a large range of distances while using one or both hands.</span></span> <span data-ttu-id="c3722-128">Questi accessori hardware forniscono collegamenti a molte interazioni di uso comune e forniscono surefooted e commenti tattili per diverse azioni.</span><span class="sxs-lookup"><span data-stu-id="c3722-128">These hardware accessories provide shortcuts to many commonly-used interactions and provide surefooted, tactile feedback for a variety of actions.</span></span> <span data-ttu-id="c3722-129">Attualmente, i controller di movimento sono disponibili solo per gli scenari di realtà mista di Windows (WMR).</span><span class="sxs-lookup"><span data-stu-id="c3722-129">Currently, motion controllers are only available for Windows Mixed Reality (WMR) scenarios.</span></span> 
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="c3722-130">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="c3722-130">See also</span></span>
* [<span data-ttu-id="c3722-131">Puntamento con la testa e commit</span><span class="sxs-lookup"><span data-stu-id="c3722-131">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="c3722-132">Puntamento con la testa e attesa</span><span class="sxs-lookup"><span data-stu-id="c3722-132">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="c3722-133">Manipolazione diretta con le mani</span><span class="sxs-lookup"><span data-stu-id="c3722-133">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="c3722-134">Puntamento e commit con le mani</span><span class="sxs-lookup"><span data-stu-id="c3722-134">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="c3722-135">Mani libere</span><span class="sxs-lookup"><span data-stu-id="c3722-135">Hands-free</span></span>](hands-free.md)

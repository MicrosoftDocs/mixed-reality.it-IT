---
title: Controller di movimento e Hands
description: Panoramica dell'interazione tra controller di movimento e Hands
author: shengkait
ms.author: shengkait
ms.date: 04/26/2019
ms.topic: article
keywords: Realtà mista, mani, controlli di movimento, interazione, progettazione
ms.openlocfilehash: d0e54c71ab42a09f2f9c6063a85441b98e729af1
ms.sourcegitcommit: 8d6e5723283c03f984f1fafef81afa5aab5d04bc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/23/2019
ms.locfileid: "66039170"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="b3abe-104">Controller di movimento e Hands</span><span class="sxs-lookup"><span data-stu-id="b3abe-104">Hands and motion controllers</span></span>
## <a name="scenarios"></a><span data-ttu-id="b3abe-105">Scenari</span><span class="sxs-lookup"><span data-stu-id="b3abe-105">Scenarios</span></span>
<span data-ttu-id="b3abe-106">Se si sceglie di adottare questo modello di interazione dopo aver letto le [linee guida di progettazione](interaction-fundamentals.md), significa che si sta sviluppando un'applicazione che richiede agli utenti di usare due mani per interagire con il mondo olografico.</span><span class="sxs-lookup"><span data-stu-id="b3abe-106">If you choose to adopt this interaction model after reading the [design guidelines](interaction-fundamentals.md), it means that you are developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="b3abe-107">L'applicazione sta per raggiungere l'obiettivo di rimuovere la delimitazione tra virtuale e fisica.</span><span class="sxs-lookup"><span data-stu-id="b3abe-107">Your application is going to achieve the goal of removing the boundry between virtual and physical.</span></span>

<span data-ttu-id="b3abe-108">Alcuni scenari specifici potrebbero essere:</span><span class="sxs-lookup"><span data-stu-id="b3abe-108">Some specific scenarios might be:</span></span>
* <span data-ttu-id="b3abe-109">Fornire agli Information Worker schermate e interfacce utente virtuale 2D per visualizzare e controllare il contenuto</span><span class="sxs-lookup"><span data-stu-id="b3abe-109">Providing information workers 2D vitual screens and UIs to display and control contents</span></span>
* <span data-ttu-id="b3abe-110">Esercitazione e guide per i ruoli di lavoro di primo linea nelle linee di assemblaggio delle factory</span><span class="sxs-lookup"><span data-stu-id="b3abe-110">Providing first line workers tutorials and guides in factory assembly lines</span></span>
* <span data-ttu-id="b3abe-111">Sviluppo di strumenti professionali per assistere e educare professionisti medici</span><span class="sxs-lookup"><span data-stu-id="b3abe-111">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="b3abe-112">Uso di oggetti virtuali 3D per decorare il mondo reale o creare un secondo mondo</span><span class="sxs-lookup"><span data-stu-id="b3abe-112">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="b3abe-113">Creazione di servizi e giochi location based usando il mondo reale come sfondo</span><span class="sxs-lookup"><span data-stu-id="b3abe-113">Creating location based services and games using the real world as background</span></span>

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="b3abe-114">Modalità di controllo delle mani e del movimento</span><span class="sxs-lookup"><span data-stu-id="b3abe-114">Hands and motion controllers modalities</span></span>
### <a name="direct-manipulation-with-handsdirect-manipulationmd"></a>[<span data-ttu-id="b3abe-115">Manipolazione diretta con le mani</span><span class="sxs-lookup"><span data-stu-id="b3abe-115">Direct manipulation with hands</span></span>](direct-manipulation.md)
<span data-ttu-id="b3abe-116">Si tratta di una modalità sfruttando la potenza di Hands, con cui gli utenti sono in grado di toccare e modificare direttamente gli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="b3abe-116">This is a modality leveraging the power of hands, with which users are capable of touching and manipulating the holograms directly.</span></span> <span data-ttu-id="b3abe-117">Grazie al Leaveraging delle esperienze quotidiane e alla creazione di affordances visivi appropriati, gli utenti possono usare lo stesso modo per modificare gli oggetti reali per interagire con quelli virtuali.</span><span class="sxs-lookup"><span data-stu-id="b3abe-117">By leaveraging daily life experiences and providing proper visual affordances, users are able to use the same way of manipulating real world objects to interact with virtual ones.</span></span>   

### <a name="point-and-commit-with-handspoint-and-commitmd"></a>[<span data-ttu-id="b3abe-118">Puntamento e commit con le mani</span><span class="sxs-lookup"><span data-stu-id="b3abe-118">Point and commit with hands</span></span>](point-and-commit.md)
<span data-ttu-id="b3abe-119">Questa modalità consente agli utenti di interagire con gli ologrammi a distanza.</span><span class="sxs-lookup"><span data-stu-id="b3abe-119">This modality empowers users to interact with holograms in a distance.</span></span> <span data-ttu-id="b3abe-120">Consente agli utenti di sfruttare al meglio i dintorni.</span><span class="sxs-lookup"><span data-stu-id="b3abe-120">It enables users to make the best use of surroundings.</span></span> <span data-ttu-id="b3abe-121">Gli utenti possono posizionare gli ologrammi ovunque e possono comunque accedervi da qualsiasi distanza.</span><span class="sxs-lookup"><span data-stu-id="b3abe-121">Users can place holograms anywhere and can still access them from any distances.</span></span> <span data-ttu-id="b3abe-122">I modelli e i movimenti mentali per controllare e modificare gli ologrammi 2D e 3D sono sincronizzati con quelli di manipolazione diretta.</span><span class="sxs-lookup"><span data-stu-id="b3abe-122">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>

### <a name="motion-controllersmotion-controllersmd"></a>[<span data-ttu-id="b3abe-123">Controller del movimento</span><span class="sxs-lookup"><span data-stu-id="b3abe-123">Motion controllers</span></span>](motion-controllers.md)
<span data-ttu-id="b3abe-124">I controller di movimento sono strumenti che estendono le funzionalità fisiche degli utenti fornendo interazioni precise in un'ampia gamma di distanze, usando una o entrambe le mani.</span><span class="sxs-lookup"><span data-stu-id="b3abe-124">Motion controllers are tools that extend the users' physical capabilities by providing precise interactions across a large range of distances while using one or both hands.</span></span> <span data-ttu-id="b3abe-125">Questi accessori hardware forniscono collegamenti a molte interazioni di uso comune e forniscono surefooted, il feedback tattile per diverse azioni.</span><span class="sxs-lookup"><span data-stu-id="b3abe-125">These hardware accessories provide shortcuts to many commonly-used interactions and gives surefooted, tactile feedback for a variety of actions.</span></span> <span data-ttu-id="b3abe-126">Attualmente, i controller di movimento sono disponibili solo per gli scenari WMR.</span><span class="sxs-lookup"><span data-stu-id="b3abe-126">Currently, motion controllers are only available for WMR scenarios.</span></span> 

![](images/Hands-and-controllers-720px.jpg)<br>

## <a name="see-also"></a><span data-ttu-id="b3abe-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b3abe-127">See also</span></span>
* [<span data-ttu-id="b3abe-128">Puntamento con la testa e commit</span><span class="sxs-lookup"><span data-stu-id="b3abe-128">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="b3abe-129">Puntamento con la testa e attesa</span><span class="sxs-lookup"><span data-stu-id="b3abe-129">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="b3abe-130">Manipolazione diretta con le mani</span><span class="sxs-lookup"><span data-stu-id="b3abe-130">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="b3abe-131">Puntamento e commit con le mani</span><span class="sxs-lookup"><span data-stu-id="b3abe-131">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="b3abe-132">Mani libere</span><span class="sxs-lookup"><span data-stu-id="b3abe-132">Hands-free</span></span>](hands-free.md)

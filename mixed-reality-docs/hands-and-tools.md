---
title: Controller di movimento e Hands
description: Panoramica dell'interazione tra controller di movimento e Hands
author: shengkait
ms.author: shengkait
ms.date: 04/26/2019
ms.topic: article
keywords: Realtà mista, mani, controlli di movimento, interazione, progettazione
ms.openlocfilehash: b6efb0a9651cad8eee9b80bb130aa1a85b9a9941
ms.sourcegitcommit: 76a7aa6e64e114b63ace058dd6d6d662b3c9f09e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/26/2019
ms.locfileid: "68507866"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="32100-104">Controller di movimento e Hands</span><span class="sxs-lookup"><span data-stu-id="32100-104">Hands and motion controllers</span></span>
## <a name="scenarios"></a><span data-ttu-id="32100-105">Scenari</span><span class="sxs-lookup"><span data-stu-id="32100-105">Scenarios</span></span>
<span data-ttu-id="32100-106">Se si sceglie di adottare questo modello di interazione dopo aver letto le [linee guida di progettazione](interaction-fundamentals.md), significa che si sta sviluppando un'applicazione che richiede agli utenti di usare due mani per interagire con il mondo olografico.</span><span class="sxs-lookup"><span data-stu-id="32100-106">If you choose to adopt this interaction model after reading the [design guidelines](interaction-fundamentals.md), it means that you are developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="32100-107">L'applicazione sta per raggiungere l'obiettivo di rimuovere la delimitazione tra virtuale e fisica.</span><span class="sxs-lookup"><span data-stu-id="32100-107">Your application is going to achieve the goal of removing the boundry between virtual and physical.</span></span>

<span data-ttu-id="32100-108">Alcuni scenari specifici potrebbero essere:</span><span class="sxs-lookup"><span data-stu-id="32100-108">Some specific scenarios might be:</span></span>
* <span data-ttu-id="32100-109">Fornire agli Information Worker schermate e interfacce utente virtuale 2D per visualizzare e controllare il contenuto</span><span class="sxs-lookup"><span data-stu-id="32100-109">Providing information workers 2D vitual screens and UIs to display and control contents</span></span>
* <span data-ttu-id="32100-110">Esercitazione e guide per i ruoli di lavoro di primo linea nelle linee di assemblaggio delle factory</span><span class="sxs-lookup"><span data-stu-id="32100-110">Providing first line workers tutorials and guides in factory assembly lines</span></span>
* <span data-ttu-id="32100-111">Sviluppo di strumenti professionali per assistere e educare professionisti medici</span><span class="sxs-lookup"><span data-stu-id="32100-111">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="32100-112">Uso di oggetti virtuali 3D per decorare il mondo reale o creare un secondo mondo</span><span class="sxs-lookup"><span data-stu-id="32100-112">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="32100-113">Creazione di servizi e giochi location based usando il mondo reale come sfondo</span><span class="sxs-lookup"><span data-stu-id="32100-113">Creating location based services and games using the real world as background</span></span>

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="32100-114">Modalità di controllo delle mani e del movimento</span><span class="sxs-lookup"><span data-stu-id="32100-114">Hands and motion controllers modalities</span></span>
### <a name="direct-manipulation-with-handsdirect-manipulationmd"></a>[<span data-ttu-id="32100-115">Manipolazione diretta con le mani</span><span class="sxs-lookup"><span data-stu-id="32100-115">Direct manipulation with hands</span></span>](direct-manipulation.md)
<span data-ttu-id="32100-116">Si tratta di una modalità sfruttando la potenza di Hands, con cui gli utenti sono in grado di toccare e modificare direttamente gli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="32100-116">This is a modality leveraging the power of hands, with which users are capable of touching and manipulating the holograms directly.</span></span> <span data-ttu-id="32100-117">Grazie al Leaveraging delle esperienze quotidiane e alla creazione di affordances visivi appropriati, gli utenti possono usare lo stesso modo per modificare gli oggetti reali per interagire con quelli virtuali.</span><span class="sxs-lookup"><span data-stu-id="32100-117">By leaveraging daily life experiences and providing proper visual affordances, users are able to use the same way of manipulating real world objects to interact with virtual ones.</span></span>   

### <a name="point-and-commit-with-handspoint-and-commitmd"></a>[<span data-ttu-id="32100-118">Puntamento e commit con le mani</span><span class="sxs-lookup"><span data-stu-id="32100-118">Point and commit with hands</span></span>](point-and-commit.md)
<span data-ttu-id="32100-119">Questa modalità consente agli utenti di interagire con gli ologrammi a distanza.</span><span class="sxs-lookup"><span data-stu-id="32100-119">This modality empowers users to interact with holograms in a distance.</span></span> <span data-ttu-id="32100-120">Consente agli utenti di sfruttare al meglio i dintorni.</span><span class="sxs-lookup"><span data-stu-id="32100-120">It enables users to make the best use of surroundings.</span></span> <span data-ttu-id="32100-121">Gli utenti possono posizionare gli ologrammi ovunque e possono comunque accedervi da qualsiasi distanza.</span><span class="sxs-lookup"><span data-stu-id="32100-121">Users can place holograms anywhere and can still access them from any distances.</span></span> <span data-ttu-id="32100-122">I modelli e i movimenti mentali per controllare e modificare gli ologrammi 2D e 3D sono sincronizzati con quelli di manipolazione diretta.</span><span class="sxs-lookup"><span data-stu-id="32100-122">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>

### <a name="motion-controllersmotion-controllersmd"></a>[<span data-ttu-id="32100-123">Controller del movimento</span><span class="sxs-lookup"><span data-stu-id="32100-123">Motion controllers</span></span>](motion-controllers.md)
<span data-ttu-id="32100-124">I controller di movimento sono strumenti che estendono le funzionalità fisiche dell'utente fornendo interazioni precise in un'ampia gamma di distanze durante l'uso di una o entrambe le mani.</span><span class="sxs-lookup"><span data-stu-id="32100-124">Motion controllers are tools that extend the user's physical capabilities by providing precise interactions across a large range of distances while using one or both hands.</span></span> <span data-ttu-id="32100-125">Questi accessori hardware forniscono collegamenti a molte interazioni di uso comune e forniscono surefooted e commenti tattili per diverse azioni.</span><span class="sxs-lookup"><span data-stu-id="32100-125">These hardware accessories provide shortcuts to many commonly-used interactions and provide surefooted, tactile feedback for a variety of actions.</span></span> <span data-ttu-id="32100-126">Attualmente, i controller di movimento sono disponibili solo per gli scenari di realtà mista di Windows (WMR).</span><span class="sxs-lookup"><span data-stu-id="32100-126">Currently, motion controllers are only available for Windows Mixed Reality (WMR) scenarios.</span></span> 

![Confronto tra le modalità di controllo della mano e del movimento](images/Hands-and-controllers-720px.jpg)<br>

<span data-ttu-id="32100-128">*Confronto tra le modalità di controllo della mano e del movimento*</span><span class="sxs-lookup"><span data-stu-id="32100-128">*Comparison of hands and motion controllers modalities*</span></span>

## <a name="see-also"></a><span data-ttu-id="32100-129">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="32100-129">See also</span></span>
* [<span data-ttu-id="32100-130">Puntamento con la testa e commit</span><span class="sxs-lookup"><span data-stu-id="32100-130">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="32100-131">Puntamento con la testa e attesa</span><span class="sxs-lookup"><span data-stu-id="32100-131">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="32100-132">Manipolazione diretta con le mani</span><span class="sxs-lookup"><span data-stu-id="32100-132">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="32100-133">Puntamento e commit con le mani</span><span class="sxs-lookup"><span data-stu-id="32100-133">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="32100-134">Mani libere</span><span class="sxs-lookup"><span data-stu-id="32100-134">Hands-free</span></span>](hands-free.md)

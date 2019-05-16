---
title: Le mani e controller di movimento
description: Panoramica delle mani e interazione tra i controller di movimento
author: shengkait
ms.author: shengkait
ms.date: 04/26/2019
ms.topic: article
keywords: Realtà, le mani, controller di movimento, interazione, mista progettare
ms.openlocfilehash: 4f4231dd816dc71e42d16aca1b518ad03440116e
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629022"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="b3e22-104">Le mani e controller di movimento</span><span class="sxs-lookup"><span data-stu-id="b3e22-104">Hands and motion controllers</span></span>
## <a name="scenarios"></a><span data-ttu-id="b3e22-105">Scenari</span><span class="sxs-lookup"><span data-stu-id="b3e22-105">Scenarios</span></span>
<span data-ttu-id="b3e22-106">Se si sceglie di adottare questo modello di interazione dopo avere letto le [linee guida di progettazione](interaction-fundamentals.md), significa che si sta sviluppando un'applicazione che richiede agli utenti di usare due mani per interagire con il mondo holographic.</span><span class="sxs-lookup"><span data-stu-id="b3e22-106">If you choose to adopt this interaction model after reading the [design guidelines](interaction-fundamentals.md), it means that you are developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="b3e22-107">L'applicazione sta per raggiungere l'obiettivo della rimozione il confine AS tra fisici e virtuali.</span><span class="sxs-lookup"><span data-stu-id="b3e22-107">Your application is going to achieve the goal of removing the boundry between virtual and physical.</span></span>

<span data-ttu-id="b3e22-108">Potrebbero essere alcuni scenari specifici:</span><span class="sxs-lookup"><span data-stu-id="b3e22-108">Some specific scenarios might be:</span></span>
* <span data-ttu-id="b3e22-109">Fornire informazioni i ruoli di lavoro virtuale 2D schermate e le interfacce utente per visualizzare e controllare i contenuti</span><span class="sxs-lookup"><span data-stu-id="b3e22-109">Providing information workers 2D vitual screens and UIs to display and control contents</span></span>
* <span data-ttu-id="b3e22-110">Fornendo esercitazioni di ruoli di lavoro prima riga e le guide di catene di montaggio factory</span><span class="sxs-lookup"><span data-stu-id="b3e22-110">Providing first line workers tutorials and guides in factory assembly lines</span></span>
* <span data-ttu-id="b3e22-111">Sviluppo di strumenti professionali di assistenza e informare il personale medico</span><span class="sxs-lookup"><span data-stu-id="b3e22-111">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="b3e22-112">L'utilizzo di oggetti 3D virtuali per decorare il mondo reale o per creare un ambiente di secondo</span><span class="sxs-lookup"><span data-stu-id="b3e22-112">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="b3e22-113">Creazione del percorso basato su servizi e i giochi con realtà come sfondo</span><span class="sxs-lookup"><span data-stu-id="b3e22-113">Creating location based services and games using the real world as background</span></span>

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="b3e22-114">Le mani e modalità di controller di movimento</span><span class="sxs-lookup"><span data-stu-id="b3e22-114">Hands and motion controllers modalities</span></span>
### <a name="direct-manipulation-with-handsdirect-manipulationmd"></a>[<span data-ttu-id="b3e22-115">Manipolazione diretta con le mani</span><span class="sxs-lookup"><span data-stu-id="b3e22-115">Direct manipulation with hands</span></span>](direct-manipulation.md)
<span data-ttu-id="b3e22-116">Si tratta di una modalità sfruttando la potenza delle lancette, con cui gli utenti sono in grado di tocco e manipolazione diretta di vntana.</span><span class="sxs-lookup"><span data-stu-id="b3e22-116">This is a modality leveraging the power of hands, with which users are capable of touching and manipulating the holograms directly.</span></span> <span data-ttu-id="b3e22-117">Da leaveraging vita quotidiana esperienze e fornire affordance visual appropriate, gli utenti sono in grado di utilizzare le stesse modalità di modifica di oggetti reali per interagire con quelle virtuali.</span><span class="sxs-lookup"><span data-stu-id="b3e22-117">By leaveraging daily life experiences and providing proper visual affordances, users are able to use the same way of manipulating real world obejcts to interact with virtual ones.</span></span>   

### <a name="point-and-commit-with-handspoint-and-commitmd"></a>[<span data-ttu-id="b3e22-118">Punto ed eseguire il commit con le mani</span><span class="sxs-lookup"><span data-stu-id="b3e22-118">Point and commit with hands</span></span>](point-and-commit.md)
<span data-ttu-id="b3e22-119">Questa modalità permette agli utenti di interagire con vntana in una distanza.</span><span class="sxs-lookup"><span data-stu-id="b3e22-119">This modality empowers users to interact with holograms in a distance.</span></span> <span data-ttu-id="b3e22-120">Consente agli utenti di ottimizzare l'uso dell'ambiente circostante.</span><span class="sxs-lookup"><span data-stu-id="b3e22-120">It enables users to make the best use of surroundings.</span></span> <span data-ttu-id="b3e22-121">Gli utenti possono inserire in qualsiasi punto ologrammi e possono ancora accedere da qualsiasi distanze.</span><span class="sxs-lookup"><span data-stu-id="b3e22-121">Users can place holograms anywhere and can still access them from any distances.</span></span> <span data-ttu-id="b3e22-122">I modelli mentali e i movimenti per il controllo e manipolazione 2D e 3D vntana sono altamente sincronizzati con quelli della manipolazione diretta.</span><span class="sxs-lookup"><span data-stu-id="b3e22-122">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>

### <a name="motion-controllersmotion-controllersmd"></a>[<span data-ttu-id="b3e22-123">Controller del movimento</span><span class="sxs-lookup"><span data-stu-id="b3e22-123">Motion controllers</span></span>](motion-controllers.md)
<span data-ttu-id="b3e22-124">I controller di movimento sono strumenti che estende le funzionalità di fisica degli utenti fornendo precisa delle interazioni tra un'ampia gamma di distanze durante l'uso pratico di uno o entrambi.</span><span class="sxs-lookup"><span data-stu-id="b3e22-124">Motion controllers are tools that extend the users' physical capabilities by providing precise interactions across a large range of distances while using one or both hands.</span></span> <span data-ttu-id="b3e22-125">Queste accessori hardware forniscono collegamenti a molti utilizzate, le interazioni e offre surefooted, tattili commenti e suggerimenti per un'ampia gamma di azioni.</span><span class="sxs-lookup"><span data-stu-id="b3e22-125">These hardware accessories provide shortcuts to many commonly-used interactions and gives surefooted, tactile feedback for a variety of actions.</span></span> <span data-ttu-id="b3e22-126">Attualmente, i controller di movimento sono disponibili solo per gli scenari WMR.</span><span class="sxs-lookup"><span data-stu-id="b3e22-126">Currently, motion controllers are only available for WMR scenarios.</span></span> 

![](images/Hands-and-controllers-720px.jpg)<br>

## <a name="see-also"></a><span data-ttu-id="b3e22-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b3e22-127">See also</span></span>
* [<span data-ttu-id="b3e22-128">Puntamento con la testa e commit</span><span class="sxs-lookup"><span data-stu-id="b3e22-128">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="b3e22-129">Manipolazione diretta (accanto all'interazione manuale)</span><span class="sxs-lookup"><span data-stu-id="b3e22-129">Direct manipulation (Near hand interaction)</span></span>](direct-manipulation.md)
* [<span data-ttu-id="b3e22-130">Punto ed eseguire il commit (l'interazione manuale estremo)</span><span class="sxs-lookup"><span data-stu-id="b3e22-130">Point and commit (Far hand interaction)</span></span>](point-and-commit.md)
* [<span data-ttu-id="b3e22-131">Mani libere</span><span class="sxs-lookup"><span data-stu-id="b3e22-131">Hands-free</span></span>](hands-free.md)
* [<span data-ttu-id="b3e22-132">Sguardo fisso e attesa</span><span class="sxs-lookup"><span data-stu-id="b3e22-132">Gaze and dwell</span></span>](gaze-targeting.md)

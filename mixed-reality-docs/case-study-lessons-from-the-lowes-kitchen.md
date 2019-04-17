---
title: Case study - lezioni da cucina del Lowe
description: Il team di HoloLens vuole condividere alcune delle procedure consigliate che sono state derivate dal progetto HoloLens del Lowe.
author: BrandonBray
ms.author: kevincol
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, del Lowe, HoloLens, cucina, case study
ms.openlocfilehash: 24759f90b8b84ec19e644fb8dff44f64c3ab81d2
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599843"
---
# <a name="case-study---lessons-from-the-lowes-kitchen"></a><span data-ttu-id="d6ecf-104">Case study - lezioni da cucina del Lowe</span><span class="sxs-lookup"><span data-stu-id="d6ecf-104">Case study - Lessons from the Lowe's kitchen</span></span>

<span data-ttu-id="d6ecf-105">Il team di HoloLens vuole condividere alcune delle procedure consigliate che sono state derivate dal progetto HoloLens del Lowe.</span><span class="sxs-lookup"><span data-stu-id="d6ecf-105">The HoloLens team wants to share some of the best practices that were derived from the Lowe's HoloLens project.</span></span> <span data-ttu-id="d6ecf-106">Di seguito è illustrato un video di HoloLens del Lowe proiettati alla presentazione di Ignite 2016 del Satya.</span><span class="sxs-lookup"><span data-stu-id="d6ecf-106">Below is a video of the Lowe's HoloLens projected demonstrated at Satya's 2016 Ignite keynote.</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/gC_4JxF0e_k]

## <a name="lowes-hololens-best-practices"></a><span data-ttu-id="d6ecf-107">Del Lowe HoloLens consigliate</span><span class="sxs-lookup"><span data-stu-id="d6ecf-107">Lowe's HoloLens Best Practices</span></span>

<span data-ttu-id="d6ecf-108">I due video illustrano le procedure consigliate che sono state derivate dal contenuto pilota del Lowe HoloLens che è rimasto in archivi di Lowe due partire da aprile 2016.</span><span class="sxs-lookup"><span data-stu-id="d6ecf-108">The two videos cover best practices that were derived from the Lowe's HoloLens Pilot that has been in two Lowe's stores since April 2016.</span></span> <span data-ttu-id="d6ecf-109">Gli argomenti principali sono:</span><span class="sxs-lookup"><span data-stu-id="d6ecf-109">The key topics are:</span></span>
* <span data-ttu-id="d6ecf-110">Ottimizzare le prestazioni per un dispositivo mobile</span><span class="sxs-lookup"><span data-stu-id="d6ecf-110">Maximize performance for a mobile device</span></span>
* <span data-ttu-id="d6ecf-111">Creare i metodi dell'esperienza utente con un frame holographic completo (2 ° talk)</span><span class="sxs-lookup"><span data-stu-id="d6ecf-111">Create UX methods with a full holographic frame (2nd talk)</span></span>
* <span data-ttu-id="d6ecf-112">Allineamento Precision (2 ° talk)</span><span class="sxs-lookup"><span data-stu-id="d6ecf-112">Precision alignment (2nd talk)</span></span>
* <span data-ttu-id="d6ecf-113">Condividere esperienze holographic (2 ° talk)</span><span class="sxs-lookup"><span data-stu-id="d6ecf-113">Shared holographic experiences (2nd talk)</span></span>
* <span data-ttu-id="d6ecf-114">L'interazione con i clienti (2 ° talk)</span><span class="sxs-lookup"><span data-stu-id="d6ecf-114">Interacting with customers (2nd talk)</span></span>

## <a name="video-1"></a><span data-ttu-id="d6ecf-115">Video 1</span><span class="sxs-lookup"><span data-stu-id="d6ecf-115">Video 1</span></span>

<span data-ttu-id="d6ecf-116">**Ottimizzare le prestazioni per un dispositivo mobile** HoloLens è un dispositivo senza i limiti con tutta l'elaborazione in esecuzione nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="d6ecf-116">**Maximize performance for a mobile device** HoloLens is an untethered device with all the processing taking place in the device.</span></span> <span data-ttu-id="d6ecf-117">Ciò richiede una piattaforma per dispositivi mobili e un modo di pensare simile alla creazione di applicazioni per dispositivi mobili.</span><span class="sxs-lookup"><span data-stu-id="d6ecf-117">This requires a mobile platform and requires a mindset similar to creating mobile applications.</span></span> <span data-ttu-id="d6ecf-118">Microsoft consiglia che l'applicazione di HoloLens mantenere 60FPS per offrire un'esperienza Deliziosa per gli utenti.</span><span class="sxs-lookup"><span data-stu-id="d6ecf-118">Microsoft recommends that your HoloLens application maintain 60FPS to provide a delicious experience for your users.</span></span> <span data-ttu-id="d6ecf-119">Presenza di FPS basso può comportare vntana instabile.</span><span class="sxs-lookup"><span data-stu-id="d6ecf-119">Having low FPS can result in unstable holograms.</span></span>

<span data-ttu-id="d6ecf-120">Alcuni degli aspetti più importanti da osservare quando si sviluppa in HoloLens è ottimizzazione/decimazione asset, mediante shader personalizzato (disponibile gratuitamente nel [HoloLens Toolkit](https://github.com/Microsoft/HoloToolkit-Unity)).</span><span class="sxs-lookup"><span data-stu-id="d6ecf-120">Some of the most important things to look at when developing on HoloLens is asset optimization/decimation, using custom shaders (available for free in the [HoloLens Toolkit](https://github.com/Microsoft/HoloToolkit-Unity)).</span></span> <span data-ttu-id="d6ecf-121">Un'altra importante considerazione è per misurare la frequenza dei fotogrammi sin dall'inizio del progetto.</span><span class="sxs-lookup"><span data-stu-id="d6ecf-121">Another important consideration is to measure the frame rate from the very beginning of your project.</span></span> <span data-ttu-id="d6ecf-122">A seconda del progetto, l'ordine di visualizzazione di asset può anche essere un collaboratore di big Data</span><span class="sxs-lookup"><span data-stu-id="d6ecf-122">Depending on the project, the order of displaying your assets can also be a big contributor</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/o0QIPwgiP9A]

## <a name="video-2"></a><span data-ttu-id="d6ecf-123">Video 2</span><span class="sxs-lookup"><span data-stu-id="d6ecf-123">Video 2</span></span>

<span data-ttu-id="d6ecf-124">**Creare i metodi dell'esperienza utente con un intervallo completo holographic** è importante comprendere il posizionamento di vntana in un mondo fisico.</span><span class="sxs-lookup"><span data-stu-id="d6ecf-124">**Create UX methods with a full holographic frame** It's important to understand the placement of holograms in a physical world.</span></span> <span data-ttu-id="d6ecf-125">Con del Lowe si parla di diversi metodi dell'esperienza utente che consentono agli utenti vntana esperienza di chiusura l'ambiente di dimensioni maggiori di vntana osservare al contempo.</span><span class="sxs-lookup"><span data-stu-id="d6ecf-125">With Lowe's we talk about different UX methods that help users experience holograms up close while still seeing the larger environment of holograms.</span></span>

<span data-ttu-id="d6ecf-126">**Allineamento di precisione** scenario per il Lowe, è fondamentale per l'esperienza di allineamento di precisione del vntana a cucina fisica.</span><span class="sxs-lookup"><span data-stu-id="d6ecf-126">**Precision alignment** For the Lowe's scenario, it was paramount to the experience to have precision alignment of the holograms to the physical kitchen.</span></span> <span data-ttu-id="d6ecf-127">Illustra le tecniche contribuisce a garantire un'esperienza che induce gli utenti che l'ambiente fisico è stato modificato.</span><span class="sxs-lookup"><span data-stu-id="d6ecf-127">We discuss techniques helps ensure an experience that convinces users that their physical environment has changed.</span></span>

<span data-ttu-id="d6ecf-128">**Condividere esperienze holographic** associa rappresentano il modo principale che viene utilizzata l'esperienza del Lowe.</span><span class="sxs-lookup"><span data-stu-id="d6ecf-128">**Shared holographic experiences** Couples are the primary way that the Lowe's experience is consumed.</span></span> <span data-ttu-id="d6ecf-129">Una persona può modificare il piano e l'altra persona visualizzeranno le modifiche.</span><span class="sxs-lookup"><span data-stu-id="d6ecf-129">One person can change the countertop and the other person will see the changes.</span></span> <span data-ttu-id="d6ecf-130">Metodo viene chiamato questo "esperienze condivise".</span><span class="sxs-lookup"><span data-stu-id="d6ecf-130">We called this "shared experiences".</span></span>

<span data-ttu-id="d6ecf-131">**L'interazione con i clienti** finestre di progettazione del Lowe non si usa un HoloLens, ma è necessario vedere ciò che vengono visualizzati i clienti.</span><span class="sxs-lookup"><span data-stu-id="d6ecf-131">**Interacting with customers** Lowe's designers are not using a HoloLens, but they need to see what the customers are seeing.</span></span> <span data-ttu-id="d6ecf-132">Viene illustrato come acquisire ciò che sta visualizzando il cliente in un'applicazione UWP.</span><span class="sxs-lookup"><span data-stu-id="d6ecf-132">We show how to capture what the customer is seeing on a UWP application.</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/LceMdyKZ4PI]

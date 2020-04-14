---
title: 'Case Study: lezioni dalla cucina di Lowe'
description: Il team di HoloLens desidera condividere alcune delle procedure consigliate derivate dal progetto HoloLens di Lowe.
author: brandonbray
ms.author: kevincol
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, Lowe, HoloLens, kitchen, case study
ms.openlocfilehash: a6bd7a09f77fb71dc23dc640525ff250abac8f12
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278129"
---
# <a name="case-study---lessons-from-the-lowes-kitchen"></a><span data-ttu-id="ed11d-104">Case Study: lezioni dalla cucina di Lowe</span><span class="sxs-lookup"><span data-stu-id="ed11d-104">Case study - Lessons from the Lowe's kitchen</span></span>

<span data-ttu-id="ed11d-105">Il team di HoloLens desidera condividere alcune delle procedure consigliate derivate dal progetto HoloLens di Lowe.</span><span class="sxs-lookup"><span data-stu-id="ed11d-105">The HoloLens team wants to share some of the best practices that were derived from the Lowe's HoloLens project.</span></span> <span data-ttu-id="ed11d-106">Di seguito è riportato un video della HoloLens di Lowe proiettato in occasione di 2016 Ignite.</span><span class="sxs-lookup"><span data-stu-id="ed11d-106">Below is a video of the Lowe's HoloLens projected demonstrated at Satya's 2016 Ignite keynote.</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/gC_4JxF0e_k]

## <a name="lowes-hololens-best-practices"></a><span data-ttu-id="ed11d-107">Procedure consigliate per HoloLens di Lowe</span><span class="sxs-lookup"><span data-stu-id="ed11d-107">Lowe's HoloLens Best Practices</span></span>

<span data-ttu-id="ed11d-108">I due video riguardano le procedure consigliate derivate dal progetto pilota HoloLens di Lowe che è stato in due negozi di Lowe a partire dal 2016 aprile.</span><span class="sxs-lookup"><span data-stu-id="ed11d-108">The two videos cover best practices that were derived from the Lowe's HoloLens Pilot that has been in two Lowe's stores since April 2016.</span></span> <span data-ttu-id="ed11d-109">Gli argomenti principali sono:</span><span class="sxs-lookup"><span data-stu-id="ed11d-109">The key topics are:</span></span>
* <span data-ttu-id="ed11d-110">Ottimizzare le prestazioni per un dispositivo mobile</span><span class="sxs-lookup"><span data-stu-id="ed11d-110">Maximize performance for a mobile device</span></span>
* <span data-ttu-id="ed11d-111">Creare metodi UX con un frame olografico completo (seconda conversazione)</span><span class="sxs-lookup"><span data-stu-id="ed11d-111">Create UX methods with a full holographic frame (2nd talk)</span></span>
* <span data-ttu-id="ed11d-112">Allineamento di precisione (secondo colloquio)</span><span class="sxs-lookup"><span data-stu-id="ed11d-112">Precision alignment (2nd talk)</span></span>
* <span data-ttu-id="ed11d-113">Esperienze olografiche condivise (seconda conversazione)</span><span class="sxs-lookup"><span data-stu-id="ed11d-113">Shared holographic experiences (2nd talk)</span></span>
* <span data-ttu-id="ed11d-114">Interazione con i clienti (seconda conversazione)</span><span class="sxs-lookup"><span data-stu-id="ed11d-114">Interacting with customers (2nd talk)</span></span>

## <a name="video-1"></a><span data-ttu-id="ed11d-115">Video 1</span><span class="sxs-lookup"><span data-stu-id="ed11d-115">Video 1</span></span>

<span data-ttu-id="ed11d-116">**Ottimizzare le prestazioni per un dispositivo mobile** HoloLens è un dispositivo senza tethering con tutte le operazioni di elaborazione eseguite nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="ed11d-116">**Maximize performance for a mobile device** HoloLens is an untethered device with all the processing taking place in the device.</span></span> <span data-ttu-id="ed11d-117">Questa operazione richiede una piattaforma mobile e richiede un approccio simile alla creazione di applicazioni per dispositivi mobili.</span><span class="sxs-lookup"><span data-stu-id="ed11d-117">This requires a mobile platform and requires a mindset similar to creating mobile applications.</span></span> <span data-ttu-id="ed11d-118">Microsoft consiglia di mantenere 60FPS per offrire agli utenti un'esperienza deliziosa per l'applicazione HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ed11d-118">Microsoft recommends that your HoloLens application maintain 60FPS to provide a delicious experience for your users.</span></span> <span data-ttu-id="ed11d-119">La presenza di FPS bassi può produrre ologrammi instabili.</span><span class="sxs-lookup"><span data-stu-id="ed11d-119">Having low FPS can result in unstable holograms.</span></span>

<span data-ttu-id="ed11d-120">Alcuni degli aspetti più importanti da considerare durante lo sviluppo in HoloLens sono l'ottimizzazione e la decimazione degli asset, usando shader personalizzati (disponibili gratuitamente in [HoloLens Toolkit](https://github.com/Microsoft/HoloToolkit-Unity)).</span><span class="sxs-lookup"><span data-stu-id="ed11d-120">Some of the most important things to look at when developing on HoloLens is asset optimization/decimation, using custom shaders (available for free in the [HoloLens Toolkit](https://github.com/Microsoft/HoloToolkit-Unity)).</span></span> <span data-ttu-id="ed11d-121">Un altro aspetto importante da considerare è misurare la frequenza dei fotogrammi dall'inizio del progetto.</span><span class="sxs-lookup"><span data-stu-id="ed11d-121">Another important consideration is to measure the frame rate from the very beginning of your project.</span></span> <span data-ttu-id="ed11d-122">A seconda del progetto, l'ordine di visualizzazione degli asset può anche essere un grande collaboratore</span><span class="sxs-lookup"><span data-stu-id="ed11d-122">Depending on the project, the order of displaying your assets can also be a big contributor</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/o0QIPwgiP9A]

## <a name="video-2"></a><span data-ttu-id="ed11d-123">Video 2</span><span class="sxs-lookup"><span data-stu-id="ed11d-123">Video 2</span></span>

<span data-ttu-id="ed11d-124">**Creare metodi UX con un frame olografico completo** È importante comprendere la posizione degli ologrammi in un ambiente fisico.</span><span class="sxs-lookup"><span data-stu-id="ed11d-124">**Create UX methods with a full holographic frame** It's important to understand the placement of holograms in a physical world.</span></span> <span data-ttu-id="ed11d-125">Con Lowe parliamo dei diversi metodi di UX che consentono agli utenti di osservare gli ologrammi in chiusura, pur continuando a osservare l'ambiente più ampio degli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="ed11d-125">With Lowe's we talk about different UX methods that help users experience holograms up close while still seeing the larger environment of holograms.</span></span>

<span data-ttu-id="ed11d-126">**Allineamento di precisione** Per lo scenario di Lowe, era fondamentale per l'esperienza avere un allineamento di precisione degli ologrammi alla cucina fisica.</span><span class="sxs-lookup"><span data-stu-id="ed11d-126">**Precision alignment** For the Lowe's scenario, it was paramount to the experience to have precision alignment of the holograms to the physical kitchen.</span></span> <span data-ttu-id="ed11d-127">Le tecniche consentono di garantire un'esperienza che consenta agli utenti di modificare l'ambiente fisico.</span><span class="sxs-lookup"><span data-stu-id="ed11d-127">We discuss techniques helps ensure an experience that convinces users that their physical environment has changed.</span></span>

<span data-ttu-id="ed11d-128">**Esperienze olografiche condivise** Le coppie rappresentano il modo principale in cui l'esperienza Lowe viene utilizzata.</span><span class="sxs-lookup"><span data-stu-id="ed11d-128">**Shared holographic experiences** Couples are the primary way that the Lowe's experience is consumed.</span></span> <span data-ttu-id="ed11d-129">Una persona può modificare il contropiano e l'altra persona vedrà le modifiche.</span><span class="sxs-lookup"><span data-stu-id="ed11d-129">One person can change the countertop and the other person will see the changes.</span></span> <span data-ttu-id="ed11d-130">Abbiamo chiamato "esperienze condivise".</span><span class="sxs-lookup"><span data-stu-id="ed11d-130">We called this "shared experiences".</span></span>

<span data-ttu-id="ed11d-131">**Interazione con i clienti** I progettisti di Lowe non usano un HoloLens, ma devono vedere cosa vedono i clienti.</span><span class="sxs-lookup"><span data-stu-id="ed11d-131">**Interacting with customers** Lowe's designers are not using a HoloLens, but they need to see what the customers are seeing.</span></span> <span data-ttu-id="ed11d-132">Viene illustrato come acquisire le informazioni visualizzate dal cliente in un'applicazione UWP.</span><span class="sxs-lookup"><span data-stu-id="ed11d-132">We show how to capture what the customer is seeing on a UWP application.</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/LceMdyKZ4PI]

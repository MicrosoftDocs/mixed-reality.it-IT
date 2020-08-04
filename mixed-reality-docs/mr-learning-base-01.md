---
title: Esercitazioni introduttive - 1 Introduzione
description: Questo corso illustra come usare Mixed Reality Toolkit (MRTK) per creare un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: 330863d36abe051e8fe17b87ce913b1b110e2d3d
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376433"
---
# <a name="1-introduction"></a><span data-ttu-id="2fcfd-105">1. Introduzione</span><span class="sxs-lookup"><span data-stu-id="2fcfd-105">1. Introduction</span></span>

## <a name="overview"></a><span data-ttu-id="2fcfd-106">Panoramica</span><span class="sxs-lookup"><span data-stu-id="2fcfd-106">Overview</span></span>

<span data-ttu-id="2fcfd-107">Serie di esercitazioni introduttive</span><span class="sxs-lookup"><span data-stu-id="2fcfd-107">Welcome to the Getting Started tutorial series!</span></span> <span data-ttu-id="2fcfd-108">Nel corso di queste esercitazioni, verranno fornite informazioni su Mixed Reality Toolkit (MRTK) e alcune delle funzionalità che offre.</span><span class="sxs-lookup"><span data-stu-id="2fcfd-108">Over the course of these tutorials, you'll learn about the Mixed Reality Toolkit (MRTK) and some of the features it has to offer.</span></span> <span data-ttu-id="2fcfd-109">Sarà anche possibile creare un'esperienza di realtà mista in cui l'utente può esplorare un ologramma modellato in base a Mars Curiosity Rover della NASA.</span><span class="sxs-lookup"><span data-stu-id="2fcfd-109">You'll also build a mixed reality experience where the user can explore a hologram modeled after NASA's Mars Curiosity Rover.</span></span> <span data-ttu-id="2fcfd-110">Al termine di questa serie, si disporrà di una solida conoscenza di MRTK e dell'utilizzo di questo strumento per accelerare il processo di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="2fcfd-110">By the end of this series, you'll have a firm grasp of MRTK and how it can speed up your development process.</span></span>

<span data-ttu-id="2fcfd-111">Le esercitazioni di questa serie sono sequenziali, consultarle quindi nell'ordine corretto:</span><span class="sxs-lookup"><span data-stu-id="2fcfd-111">Tutorials in this series are meant to be sequential, so please go through them in the correct order:</span></span>

1. [<span data-ttu-id="2fcfd-112">Introduzione</span><span class="sxs-lookup"><span data-stu-id="2fcfd-112">Introduction</span></span>](mr-learning-base-01.md)
2. [<span data-ttu-id="2fcfd-113">Inizializzazione del progetto e distribuzione della prima applicazione</span><span class="sxs-lookup"><span data-stu-id="2fcfd-113">Initializing your project and deploying your first application</span></span>](mr-learning-base-02.md)
3. [<span data-ttu-id="2fcfd-114">Configurazione dei profili di Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="2fcfd-114">Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
4. [<span data-ttu-id="2fcfd-115">Posizionamento degli oggetti nella scena</span><span class="sxs-lookup"><span data-stu-id="2fcfd-115">Positioning objects in the scene</span></span>](mr-learning-base-04.md)
5. [<span data-ttu-id="2fcfd-116">Creazione di contenuto dinamico tramite risolutori</span><span class="sxs-lookup"><span data-stu-id="2fcfd-116">Creating dynamic content using Solvers</span></span>](mr-learning-base-05.md)
6. [<span data-ttu-id="2fcfd-117">Creazione delle interfacce utente</span><span class="sxs-lookup"><span data-stu-id="2fcfd-117">Creating user interfaces</span></span>](mr-learning-base-06.md)
7. [<span data-ttu-id="2fcfd-118">Interazione con oggetti 3D</span><span class="sxs-lookup"><span data-stu-id="2fcfd-118">Interacting with 3D objects</span></span>](mr-learning-base-07.md)
8. [<span data-ttu-id="2fcfd-119">Uso del tracciamento oculare</span><span class="sxs-lookup"><span data-stu-id="2fcfd-119">Using eye-tracking</span></span>](mr-learning-base-08.md)
9. [<span data-ttu-id="2fcfd-120">Uso dei comandi vocali</span><span class="sxs-lookup"><span data-stu-id="2fcfd-120">Using voice commands</span></span>](mr-learning-base-09.md)

## <a name="objectives"></a><span data-ttu-id="2fcfd-121">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="2fcfd-121">Objectives</span></span>

* <span data-ttu-id="2fcfd-122">Imparare a configurare Unity per MRTK</span><span class="sxs-lookup"><span data-stu-id="2fcfd-122">Learn how to configure Unity for MRTK</span></span>
* <span data-ttu-id="2fcfd-123">Imparare a compilare e distribuire nel dispositivo</span><span class="sxs-lookup"><span data-stu-id="2fcfd-123">Learn how to build and deploy to your device</span></span>
* <span data-ttu-id="2fcfd-124">Imparare a usare alcune delle funzionalità chiave di MRTK</span><span class="sxs-lookup"><span data-stu-id="2fcfd-124">Learn how to use some of MRTK's key features</span></span>
* <span data-ttu-id="2fcfd-125">Creare un'esperienza di realtà mista completa</span><span class="sxs-lookup"><span data-stu-id="2fcfd-125">Create a complete mixed reality experience</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2fcfd-126">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="2fcfd-126">Prerequisites</span></span>

* <span data-ttu-id="2fcfd-127">Un PC Windows 10 configurato in cui siano [installati gli strumenti](install-the-tools.md) corretti</span><span class="sxs-lookup"><span data-stu-id="2fcfd-127">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="2fcfd-128">[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) 10.0.18362.0 o versioni successive</span><span class="sxs-lookup"><span data-stu-id="2fcfd-128">[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) 10.0.18362.0 or later</span></span>
* <span data-ttu-id="2fcfd-129">Un dispositivo HoloLens 2 [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="2fcfd-129">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="2fcfd-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.3.15 installato e il modulo Universal Windows Platform Build Support aggiunto</span><span class="sxs-lookup"><span data-stu-id="2fcfd-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Universal Windows Platform Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="2fcfd-131">La versione di MRTK consigliata per questa serie di esercitazioni è MRTK 2.4.0.</span><span class="sxs-lookup"><span data-stu-id="2fcfd-131">The recommended MRTK version for this tutorial series is MRTK 2.4.0.</span></span>

> [!CAUTION]
> <span data-ttu-id="2fcfd-132">La versione di Unity consigliata per questa serie di esercitazioni è Unity 2019.3.15.</span><span class="sxs-lookup"><span data-stu-id="2fcfd-132">The recommended Unity version for this tutorial series is Unity 2019.3.15.</span></span> <span data-ttu-id="2fcfd-133">Questa istruzione sostituisce gli eventuali requisiti relativi alla versione di Unity indicati negli argomenti visualizzabili facendo clic sui collegamenti dei prerequisiti sopra riportati.</span><span class="sxs-lookup"><span data-stu-id="2fcfd-133">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

[<span data-ttu-id="2fcfd-134">Esercitazione successiva: 2. Inizializzazione del progetto e distribuzione della prima applicazione</span><span class="sxs-lookup"><span data-stu-id="2fcfd-134">Next Tutorial: 2. Initializing your project and deploying your first application</span></span>](mr-learning-base-02.md)

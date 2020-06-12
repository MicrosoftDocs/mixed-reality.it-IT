---
title: 1. Guida introduttiva
description: Parte 1 di 6 in una serie di esercitazioni per la creazione di una semplice app di scacchi con Unreal Engine 4 e il plug-in UX Tools di Mixed Reality Toolkit
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, esercitazione, guida introduttiva, mrtk, uxt, UX Tools, documentazione
ms.openlocfilehash: c16671fc8f4233378dafa646786df1f7b5ae18e1
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330168"
---
# <a name="1-getting-started"></a><span data-ttu-id="ceb23-104">1. Guida introduttiva</span><span class="sxs-lookup"><span data-stu-id="ceb23-104">1. Getting started</span></span>

<span data-ttu-id="ceb23-105">Che tu sia alle prime armi o un professionista esperto, questo è il punto di partenza ideale per esplorare [HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/) e [Unreal Engine](https://www.unrealengine.com/en-US/).</span><span class="sxs-lookup"><span data-stu-id="ceb23-105">Whether you're new to mixed reality or a seasoned pro, this is the place to start your journey with [HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/) and [Unreal Engine](https://www.unrealengine.com/en-US/).</span></span> <span data-ttu-id="ceb23-106">Questa serie di esercitazioni ti offrirà una guida dettagliata su come creare un'app di scacchi interattiva con il [plug-in UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal), che fa parte di [Mixed Reality Toolkit per Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal).</span><span class="sxs-lookup"><span data-stu-id="ceb23-106">This tutorial series will give you a step by step guide on how to build an interactive chess app with the [UX Tools plugin](https://github.com/microsoft/MixedReality-UXTools-Unreal) - part of the [Mixed Reality Toolkit for Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal).</span></span> <span data-ttu-id="ceb23-107">Con il plug-in potrai aggiungere comuni funzionalità UX ai tuoi progetti con codice, progetti ed esempi.</span><span class="sxs-lookup"><span data-stu-id="ceb23-107">The plugin will help you add common UX features to your projects with code, blueprints, and examples.</span></span> 

![Schermata finale in viewport](images/unreal-uxt/5-endscene.PNG)

<span data-ttu-id="ceb23-109">Alla fine della serie avrai acquisito esperienza pratica su:</span><span class="sxs-lookup"><span data-stu-id="ceb23-109">By the end of the series you'll have hands-on experience with:</span></span>
* <span data-ttu-id="ceb23-110">Avvio di un nuovo progetto</span><span class="sxs-lookup"><span data-stu-id="ceb23-110">Starting a new project</span></span>
* <span data-ttu-id="ceb23-111">Configurazione per la realtà mista</span><span class="sxs-lookup"><span data-stu-id="ceb23-111">Setting up for mixed reality</span></span>
* <span data-ttu-id="ceb23-112">Gestione dell'input utente</span><span class="sxs-lookup"><span data-stu-id="ceb23-112">Working with user input</span></span>
* <span data-ttu-id="ceb23-113">Aggiunta di pulsanti</span><span class="sxs-lookup"><span data-stu-id="ceb23-113">Adding buttons</span></span>
* <span data-ttu-id="ceb23-114">Riproduzione su un emulatore o dispositivo</span><span class="sxs-lookup"><span data-stu-id="ceb23-114">Playing on an emulator or device</span></span>

<span data-ttu-id="ceb23-115">Per eventuali chiarimenti, vedi [Panoramica dello sviluppo con Unreal](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview).</span><span class="sxs-lookup"><span data-stu-id="ceb23-115">If you have any questions, check out our [Unreal development overview](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ceb23-116">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="ceb23-116">Prerequisites</span></span>
<span data-ttu-id="ceb23-117">Prima di iniziare, è importante verificare che siano soddisfatti questi requisiti:</span><span class="sxs-lookup"><span data-stu-id="ceb23-117">Make sure you've met the following requirements before jumping in:</span></span>
* <span data-ttu-id="ceb23-118">Windows 10 1809 o versioni successive</span><span class="sxs-lookup"><span data-stu-id="ceb23-118">Windows 10 1809 or later</span></span>
* <span data-ttu-id="ceb23-119">Windows 10 SDK 10.0.18362.0 o versioni successive</span><span class="sxs-lookup"><span data-stu-id="ceb23-119">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="ceb23-120">[Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 o versioni successive</span><span class="sxs-lookup"><span data-stu-id="ceb23-120">[Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 or later</span></span>
* <span data-ttu-id="ceb23-121">Dispositivo Microsoft HoloLens 2 [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode) o emulatore</span><span class="sxs-lookup"><span data-stu-id="ceb23-121">Microsoft HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode) or Emulator</span></span>
* <span data-ttu-id="ceb23-122">Visual Studio 2019 con i carichi di lavoro seguenti</span><span class="sxs-lookup"><span data-stu-id="ceb23-122">Visual Studio 2019 with the workloads below</span></span>

### <a name="installing-visual-studio-2019"></a><span data-ttu-id="ceb23-123">Installazione di Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="ceb23-123">Installing Visual Studio 2019</span></span>
<span data-ttu-id="ceb23-124">L'ultimo passaggio consiste nel configurare Visual Studio nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="ceb23-124">The last step is to setup Visual Studio as follows:</span></span>
1. <span data-ttu-id="ceb23-125">Installa la versione più recente di [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)</span><span class="sxs-lookup"><span data-stu-id="ceb23-125">Install the latest version of [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)</span></span>
2. <span data-ttu-id="ceb23-126">Installa i [carichi di lavoro](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?view=vs-2019#modify-workloads) seguenti:</span><span class="sxs-lookup"><span data-stu-id="ceb23-126">Install the following [workloads](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?view=vs-2019#modify-workloads):</span></span>
    * <span data-ttu-id="ceb23-127">Sviluppo per desktop con C++</span><span class="sxs-lookup"><span data-stu-id="ceb23-127">Desktop development with C++</span></span>
    * <span data-ttu-id="ceb23-128">Sviluppo per desktop .NET</span><span class="sxs-lookup"><span data-stu-id="ceb23-128">.NET desktop development</span></span>
    * <span data-ttu-id="ceb23-129">Sviluppo per la piattaforma UWP</span><span class="sxs-lookup"><span data-stu-id="ceb23-129">Universal Windows Platform development</span></span>

3. <span data-ttu-id="ceb23-130">Installa i [componenti](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?view=vs-2019#modify-individual-components) seguenti:</span><span class="sxs-lookup"><span data-stu-id="ceb23-130">Install the following [components](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?view=vs-2019#modify-individual-components):</span></span>
    * <span data-ttu-id="ceb23-131">Compilatori, strumenti di compilazione e runtime > MSVC versione 142 - VS 2019 C++ ARM64 Build Tools (versione più recente)</span><span class="sxs-lookup"><span data-stu-id="ceb23-131">Compilers, build tools, and runtimes > MSVC v142 - VS 2019 C++ ARM64 build tools (latest version)</span></span>

<span data-ttu-id="ceb23-132">Ecco fatto!</span><span class="sxs-lookup"><span data-stu-id="ceb23-132">That's it!</span></span> <span data-ttu-id="ceb23-133">Ora è tutto pronto per iniziare il progetto di app di scacchi.</span><span class="sxs-lookup"><span data-stu-id="ceb23-133">You're all set to move on to starting the chess app project.</span></span>

[<span data-ttu-id="ceb23-134">Sezione successiva: 2. Inizializzazione del progetto e prima applicazione</span><span class="sxs-lookup"><span data-stu-id="ceb23-134">Next section: 2. Initializing your project and first application</span></span>](unreal-uxt-ch2.md)
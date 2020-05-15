---
title: 1. Guida introduttiva
description: Parte 1 di un'esercitazione per la creazione di una semplice app di scacchi con Unreal Engine 4 e il plug-in UX Tools di Mixed Reality Toolkit
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, esercitazione, guida introduttiva, mrtk, uxt, UX Tools, documentazione
ms.openlocfilehash: 3ca47cfe7bb0a733932f3777cc8b531ef9df8e71
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840130"
---
# <a name="1-getting-started"></a><span data-ttu-id="429ff-104">1. Guida introduttiva</span><span class="sxs-lookup"><span data-stu-id="429ff-104">1. Getting started</span></span>

<span data-ttu-id="429ff-105">Questa è un'esercitazione dettagliata che descrive come creare un'app di scacchi interattiva HoloLens 2 con Unreal Engine 4.</span><span class="sxs-lookup"><span data-stu-id="429ff-105">This is a step by step tutorial that will show you how to build an interactive HoloLens 2 chess app using Unreal Engine 4.</span></span> <span data-ttu-id="429ff-106">Imparerai anche come usare il plug-in UX Tools di Mixed Reality Toolkit per Unreal per uno sviluppo più rapido.</span><span class="sxs-lookup"><span data-stu-id="429ff-106">You will also learn how to use the UX Tools plugin from the Mixed Reality Toolkit for Unreal to speed up development.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="429ff-107">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="429ff-107">Prerequisites</span></span>

* <span data-ttu-id="429ff-108">Windows 10 1809 o versioni successive</span><span class="sxs-lookup"><span data-stu-id="429ff-108">Windows 10 1809 or later</span></span>
* <span data-ttu-id="429ff-109">Windows 10 SDK 10.0.18362.0 o versioni successive</span><span class="sxs-lookup"><span data-stu-id="429ff-109">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="429ff-110">Unreal Engine 4.25 o versioni successive</span><span class="sxs-lookup"><span data-stu-id="429ff-110">Unreal Engine 4.25 or later</span></span>
* <span data-ttu-id="429ff-111">Dispositivo Microsoft HoloLens 2 [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode) o emulatore</span><span class="sxs-lookup"><span data-stu-id="429ff-111">Microsoft HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode) or Emulator</span></span>
* <span data-ttu-id="429ff-112">Visual Studio 2019 con i carichi di lavoro e i componenti seguenti</span><span class="sxs-lookup"><span data-stu-id="429ff-112">Visual Studio 2019 (with below workloads and components)</span></span>

### <a name="installing-visual-studio-2019-workloads-and-components"></a><span data-ttu-id="429ff-113">Installazione di Visual Studio 2019, carichi di lavoro e componenti</span><span class="sxs-lookup"><span data-stu-id="429ff-113">Installing Visual Studio 2019, workloads, and components</span></span>
1. <span data-ttu-id="429ff-114">Installa Visual Studio 2019 o aggiorna alla versione più recente</span><span class="sxs-lookup"><span data-stu-id="429ff-114">Install or and update to the latest version of Visual Studio 2019</span></span>
* [<span data-ttu-id="429ff-115">Scarica Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="429ff-115">Download Visual Studio 2019</span></span>](https://visualstudio.microsoft.com/downloads/)
2. <span data-ttu-id="429ff-116">Installa i carichi di lavoro seguenti:</span><span class="sxs-lookup"><span data-stu-id="429ff-116">Install the following workloads:</span></span>
* <span data-ttu-id="429ff-117">Sviluppo per desktop con C++</span><span class="sxs-lookup"><span data-stu-id="429ff-117">Desktop development with C++</span></span>
* <span data-ttu-id="429ff-118">Sviluppo per desktop .NET</span><span class="sxs-lookup"><span data-stu-id="429ff-118">.NET desktop development</span></span>
* <span data-ttu-id="429ff-119">Sviluppo per la piattaforma UWP</span><span class="sxs-lookup"><span data-stu-id="429ff-119">Universal Windows Platform development</span></span>
3. <span data-ttu-id="429ff-120">Installa i singoli componenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="429ff-120">Install the following individual components:</span></span>
* <span data-ttu-id="429ff-121">Compilatori, strumenti di compilazione e runtime > MSVC versione 142 - VS 2019 C++ ARM64 Build Tools (versione più recente)</span><span class="sxs-lookup"><span data-stu-id="429ff-121">Compilers, build tools, and runtimes > MSVC v142 - VS 2019 C++ ARM64 build tools (latest version)</span></span>

[<span data-ttu-id="429ff-122">Sezione successiva: 2. Inizializzazione del progetto e prima applicazione</span><span class="sxs-lookup"><span data-stu-id="429ff-122">Next section: 2. Initializing your project and first application</span></span>](unreal-uxt-ch2.md)
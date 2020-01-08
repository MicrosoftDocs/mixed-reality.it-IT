---
title: Esercitazioni introduttive-1. Panoramica e obiettivi
description: Questo corso illustra come implementare Azure Face Recognition in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: a311fbe377e4a2654c8905276417cf1104fc4754
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334340"
---
# <a name="1-overview-and-objectives"></a><span data-ttu-id="5e364-105">1. Panoramica e obiettivi</span><span class="sxs-lookup"><span data-stu-id="5e364-105">1. Overview and objectives</span></span>

## <a name="device-support"></a><span data-ttu-id="5e364-106">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="5e364-106">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="5e364-107"><strong>Corso</strong></span><span class="sxs-lookup"><span data-stu-id="5e364-107"><strong>Course</strong></span></span></td>
        <td><span data-ttu-id="5e364-108"><a href="hololens-hardware-details.md"><strong>HoloLens (prima generazione)</strong></a></span><span class="sxs-lookup"><span data-stu-id="5e364-108"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="5e364-109"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="5e364-109"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="5e364-110"><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="5e364-110"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td></td>
        <td>❌</td>
        <td><span data-ttu-id="5e364-111">✔️</span><span class="sxs-lookup"><span data-stu-id="5e364-111">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="5e364-112">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="5e364-112">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="5e364-113">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="5e364-113">Prerequisites</span></span>

* <span data-ttu-id="5e364-114">Un PC Windows 10 configurato con gli [strumenti corretti installati](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="5e364-114">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="5e364-115">Windows 10 SDK 10.0.18362.0 o versione successiva</span><span class="sxs-lookup"><span data-stu-id="5e364-115">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="5e364-116">Funzionalità di C# programmazione di base</span><span class="sxs-lookup"><span data-stu-id="5e364-116">Some basic C# programming ability</span></span>
* <span data-ttu-id="5e364-117">Un dispositivo HoloLens 2 [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="5e364-117">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>

>[!IMPORTANT]
><span data-ttu-id="5e364-118">Questa serie di esercitazioni richiede <a href="https://unity3d.com/get-unity/download/archive" target="_blank">unity 2019,1</a> e la versione consigliata è Unity 2019.1.14.</span><span class="sxs-lookup"><span data-stu-id="5e364-118">This tutorial series requires <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Unity 2019.1</a> and the recommended version is Unity 2019.1.14.</span></span> <span data-ttu-id="5e364-119">Questa operazione sostituisce i requisiti di versione di Unity o i consigli indicati nei prerequisiti collegati in precedenza.</span><span class="sxs-lookup"><span data-stu-id="5e364-119">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

[<span data-ttu-id="5e364-120">Lezione successiva: 2. inizializzazione del progetto e della prima applicazione</span><span class="sxs-lookup"><span data-stu-id="5e364-120">Next lesson: 2. Initializing your project and first application</span></span>](mrlearning-base-ch1.md)

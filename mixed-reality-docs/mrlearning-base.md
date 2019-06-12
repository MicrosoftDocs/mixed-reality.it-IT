---
title: Introduzione di modulo Base Learning MR
description: Completare questo corso di informazioni su come implementare il riconoscimento di volti di Azure all'interno di un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, hololens, esercitazione di unity,
ms.openlocfilehash: 2fe07efe87086e9a8c06e1953fcef8544b03c80a
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829881"
---
# <a name="mr-learning-base-module-overview--objectives"></a><span data-ttu-id="6c02b-104">Obiettivi di & Base Learning MR modulo Panoramica</span><span class="sxs-lookup"><span data-stu-id="6c02b-104">MR Learning Base Module Overview & Objectives</span></span>

## <a name="device-support"></a><span data-ttu-id="6c02b-105">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="6c02b-105">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="6c02b-106"><strong>Corso</strong></span><span class="sxs-lookup"><span data-stu-id="6c02b-106"><strong>Course</strong></span></span></td>
        <td><span data-ttu-id="6c02b-107"><a href="hololens-hardware-details.md"><strong>HoloLens (dal 1 ° generazione)</strong></a></span><span class="sxs-lookup"><span data-stu-id="6c02b-107"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="6c02b-108"><a href="https://www.microsoft.com/en-us/hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="6c02b-108"><a href="https://www.microsoft.com/en-us/hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="6c02b-109"><a href="immersive-headset-hardware-details.md"><strong>Auricolari coinvolgenti</strong></a></span><span class="sxs-lookup"><span data-stu-id="6c02b-109"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td></td>
        <td><span data-ttu-id="6c02b-110">❌</span><span class="sxs-lookup"><span data-stu-id="6c02b-110">❌</span></span></td>
        <td><span data-ttu-id="6c02b-111">✔️</span><span class="sxs-lookup"><span data-stu-id="6c02b-111">✔️</span></span></td>
        <td><span data-ttu-id="6c02b-112">❌</span><span class="sxs-lookup"><span data-stu-id="6c02b-112">❌</span></span></td>
    </tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="6c02b-113">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="6c02b-113">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="6c02b-114">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="6c02b-114">Prerequisites</span></span>

* <span data-ttu-id="6c02b-115">Un PC Windows 10 configurate con i valori corretti [sono installati gli strumenti](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="6c02b-115">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="6c02b-116">Windows 10 SDK 10.0.18362.0 o versione successiva</span><span class="sxs-lookup"><span data-stu-id="6c02b-116">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="6c02b-117">Alcuni basic C# capacità di programmazione.</span><span class="sxs-lookup"><span data-stu-id="6c02b-117">Some basic C# programming ability.</span></span>
* <span data-ttu-id="6c02b-118">Un dispositivo HoloLens 2 [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="6c02b-118">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

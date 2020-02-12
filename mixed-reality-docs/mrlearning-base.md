---
title: Esercitazioni introduttive-1. Panoramica e obiettivi
description: Questo corso illustra come implementare Azure Face Recognition in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: dbae7545edb6515b5cf148fbbfb6652595d2fc0d
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/11/2020
ms.locfileid: "77129262"
---
# <a name="1-overview-and-objectives"></a><span data-ttu-id="21e41-105">1. Panoramica e obiettivi</span><span class="sxs-lookup"><span data-stu-id="21e41-105">1. Overview and objectives</span></span>

## <a name="device-support"></a><span data-ttu-id="21e41-106">Supporto per i dispositivi</span><span class="sxs-lookup"><span data-stu-id="21e41-106">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="21e41-107"><strong>Corso</strong></span><span class="sxs-lookup"><span data-stu-id="21e41-107"><strong>Course</strong></span></span></td>
        <td><span data-ttu-id="21e41-108"><a href="hololens-hardware-details.md"><strong>HoloLens (prima generazione)</strong></a></span><span class="sxs-lookup"><span data-stu-id="21e41-108"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="21e41-109"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="21e41-109"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="21e41-110"><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="21e41-110"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td></td>
        <td>❌</td>
        <td><span data-ttu-id="21e41-111">✔️</span><span class="sxs-lookup"><span data-stu-id="21e41-111">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="21e41-112">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="21e41-112">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="21e41-113">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="21e41-113">Prerequisites</span></span>

* <span data-ttu-id="21e41-114">Un PC Windows 10 configurato con gli [strumenti corretti installati](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="21e41-114">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="21e41-115">Windows 10 SDK 10.0.18362.0 o versione successiva</span><span class="sxs-lookup"><span data-stu-id="21e41-115">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="21e41-116">Funzionalità di C# programmazione di base</span><span class="sxs-lookup"><span data-stu-id="21e41-116">Some basic C# programming ability</span></span>
* <span data-ttu-id="21e41-117">Un dispositivo HoloLens 2 [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="21e41-117">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="21e41-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub Unity</a> con Unity 2019.2. X installato e aggiunta del modulo di supporto piattaforma UWP (Universal Windows Platform) Build</span><span class="sxs-lookup"><span data-stu-id="21e41-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="21e41-119">La versione consigliata di Unity per questa serie di esercitazioni è Unity 2019.2. X.</span><span class="sxs-lookup"><span data-stu-id="21e41-119">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="21e41-120">Questa operazione sostituisce i requisiti di versione di Unity o i consigli indicati nei prerequisiti collegati in precedenza.</span><span class="sxs-lookup"><span data-stu-id="21e41-120">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

[<span data-ttu-id="21e41-121">Lezione successiva: 2. inizializzazione del progetto e della prima applicazione</span><span class="sxs-lookup"><span data-stu-id="21e41-121">Next lesson: 2. Initializing your project and first application</span></span>](mrlearning-base-ch1.md)

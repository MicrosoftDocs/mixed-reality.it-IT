---
title: Consigli sulle prestazioni per Unreal
description: Consigli per ottenere prestazioni ottimali per le app di realtà mista in Unreal
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, prestazioni, ottimizzazione, impostazioni, documentazione
ms.openlocfilehash: 1fab2f714628f61a518d89795cf644e90130200a
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840200"
---
# <a name="performance-recommendations-for-unreal"></a><span data-ttu-id="44543-104">Consigli sulle prestazioni per Unreal</span><span class="sxs-lookup"><span data-stu-id="44543-104">Performance recommendations for Unreal</span></span>

<span data-ttu-id="44543-105">Questo articolo si basa sugli argomenti affrontati in [Consigli sulle prestazioni per la realtà mista](understanding-performance-for-mixed-reality.md), ma tratta in particolare i concetti specifici dell'ambiente Unreal Engine.</span><span class="sxs-lookup"><span data-stu-id="44543-105">This article builds on the discussion outlined in [performance recommendations for mixed reality](understanding-performance-for-mixed-reality.md) but focuses on learnings specific to the Unreal Engine environment.</span></span>

## <a name="recommended-unreal-project-settings"></a><span data-ttu-id="44543-106">Impostazioni consigliate per il progetto Unreal</span><span class="sxs-lookup"><span data-stu-id="44543-106">Recommended Unreal project settings</span></span>

- <span data-ttu-id="44543-107">Usa il renderer di realtà virtuale per dispositivi mobili: nelle impostazioni del progetto verifica che la piattaforma di destinazione sia impostata su Mobile/Tablet (Cellulare/Tablet) in Project – Target Hardware (Progetto – Hardware di destinazione)</span><span class="sxs-lookup"><span data-stu-id="44543-107">Use the mobile VR renderer- in your project settings, ensure your target platform is set to "Mobile/Tablet" under "Project – Target Hardware"</span></span>
- <span data-ttu-id="44543-108">Disabilita il culling delle occlusioni: in Engine – Rendering (Motore – Rendering) nella sezione Culling deseleziona Occlusion Culling (Culling di occlusione)</span><span class="sxs-lookup"><span data-stu-id="44543-108">Disable occlusion culling- under "Engine – Rendering" in the "Culling" section, uncheck "Occlusion Culling"</span></span>
    + <span data-ttu-id="44543-109">Se è necessario il culling delle occlusioni perché devi eseguire il rendering di una scena molto dettagliata, consigliamo di abilitare Support Software Occlusion Culling (Culling di occlusione del software di supporto) in Engine – Rendering (Motore – Rendering).</span><span class="sxs-lookup"><span data-stu-id="44543-109">If occlusion culling is required because a very detailed scene needs to be rendered, it is recommended that "Support Software Occlusion Culling" is enabled Under "Engine – Rendering".</span></span> <span data-ttu-id="44543-110">Ciò consente ad Unreal di eseguire il culling delle occlusioni sulla CPU ed evitare query di occlusione della GPU, che influiscono negativamente sulle prestazioni di HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="44543-110">This allows Unreal to do occlusion culling on the CPU and avoid GPU occlusion queries, which perform poorly on HoloLens 2.</span></span>
- <span data-ttu-id="44543-111">Abilita sia Instanced Stereo (Stereo con istanze), sia Mobile Multi-View (Visualizzazioni multiple dispositivi mobili) in Engine – Rendering (Motore – Rendering) nella categoria VR (Realtà virtuale).</span><span class="sxs-lookup"><span data-stu-id="44543-111">Enable both "Instanced Stereo" and "Mobile Multi-View" under "Engine – Rendering" in the "VR" category.</span></span> <span data-ttu-id="44543-112">Potresti dover deselezionare Mobile Post-Processing (Post-elaborazione dispositivi mobili) per poter controllare Mobile Multi-View (Visualizzazioni multiple dispositivi mobili)</span><span class="sxs-lookup"><span data-stu-id="44543-112">You may need to uncheck "Mobile Post-Processing" in order to be able to check "Mobile Multi-View"</span></span>

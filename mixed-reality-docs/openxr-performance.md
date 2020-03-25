---
title: Prestazioni OpenXR
description: Eseguire il debug delle prestazioni GPU delle applicazioni OpenXR.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, nativo, app nativa, motore personalizzato, middleware, prestazioni, ottimizzazione, debug GPU, RenderDoc, PIX
ms.openlocfilehash: 717dc2d534773bd28f5ad2d5c3720bf4177a1480
ms.sourcegitcommit: 9de2cb11321e6517db69e8c93459a205900a2174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163345"
---
# <a name="openxr-performance"></a><span data-ttu-id="2f182-104">Prestazioni OpenXR</span><span class="sxs-lookup"><span data-stu-id="2f182-104">OpenXR performance</span></span>

<span data-ttu-id="2f182-105">In HoloLens 2 sono disponibili diversi modi per inviare i dati di composizione tramite `xrEndFrame` che comporteranno una riduzione delle prestazioni in fase di post-elaborazione.</span><span class="sxs-lookup"><span data-stu-id="2f182-105">On HoloLens 2, there are a number of ways to submit composition data through `xrEndFrame` which will result in post-processing that will have a noticeable performance penalty.</span></span>
<span data-ttu-id="2f182-106">Per evitare la penalizzazione delle prestazioni, [inviare una singola `XrCompositionProjectionLayer`](openxr-best-practices.md#use-a-single-projection-layer) con le caratteristiche seguenti:</span><span class="sxs-lookup"><span data-stu-id="2f182-106">To avoid performance penalities, [submit a single `XrCompositionProjectionLayer`](openxr-best-practices.md#use-a-single-projection-layer) with the following characteristics:</span></span>
* [<span data-ttu-id="2f182-107">Usare una matrice di trama presentazione catena</span><span class="sxs-lookup"><span data-stu-id="2f182-107">Use a texture array swapchain</span></span>](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [<span data-ttu-id="2f182-108">Usa il formato presentazione catena del colore primario</span><span class="sxs-lookup"><span data-stu-id="2f182-108">Use the primary color swapchain format</span></span>](openxr-best-practices.md#select-a-swapchain-format)
* [<span data-ttu-id="2f182-109">Usare le dimensioni di visualizzazione consigliate</span><span class="sxs-lookup"><span data-stu-id="2f182-109">Use the recommended view dimensions</span></span>](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* <span data-ttu-id="2f182-110">Non impostare il flag di `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT`</span><span class="sxs-lookup"><span data-stu-id="2f182-110">Do not set the `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` flag</span></span>
* <span data-ttu-id="2f182-111">Impostare il `XrCompositionLayerDepthInfoKHR` `minDepth` su 0,0 f e `maxDepth` su 1,0 f</span><span class="sxs-lookup"><span data-stu-id="2f182-111">Set the `XrCompositionLayerDepthInfoKHR` `minDepth` to 0.0f and `maxDepth` to 1.0f</span></span>

<span data-ttu-id="2f182-112">Ulteriori considerazioni comporteranno prestazioni migliori:</span><span class="sxs-lookup"><span data-stu-id="2f182-112">Additional considerations will result in better performance:</span></span>
* [<span data-ttu-id="2f182-113">Usare il formato di profondità a 16 bit</span><span class="sxs-lookup"><span data-stu-id="2f182-113">Use the 16-bit depth format</span></span>](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [<span data-ttu-id="2f182-114">Eseguire chiamate di disegni ad istanza</span><span class="sxs-lookup"><span data-stu-id="2f182-114">Make instanced draw calls</span></span>](openxr-best-practices.md#render-with-texture-array-and-vprt)

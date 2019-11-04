---
title: Cronologia delle versioni remota olografica
description: Cronologia delle versioni per la comunicazione remota olografica in HoloLens 2.
author: NPohl-MSFT
ms.author: nopohl
ms.date: 10/21/2019
ms.topic: article
keywords: HoloLens, comunicazione remota, comunicazione remota olografica
ms.openlocfilehash: 75e7c276560b4efbbdcbf2ea7579ed5ad7aadb4d
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73439232"
---
# <a name="holographic-remoting-version-history"></a><span data-ttu-id="8fca6-104">Cronologia delle versioni remota olografica</span><span class="sxs-lookup"><span data-stu-id="8fca6-104">Holographic Remoting Version History</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8fca6-105">Queste linee guida sono specifiche per la comunicazione remota olografica in HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="8fca6-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <span data-ttu-id="8fca6-106">Versione 2.0.14 (26 ottobre 2019)<a name="v2.0.14"></a></span><span class="sxs-lookup"><span data-stu-id="8fca6-106">Version 2.0.14 (October 26, 2019) <a name="v2.0.14"></a></span></span>
* <span data-ttu-id="8fca6-107">Supporto per le nuove API PerceptionDevice (aggiornamento di Windows 10 di novembre 2019).</span><span class="sxs-lookup"><span data-stu-id="8fca6-107">Support for new PerceptionDevice APIs (Windows 10 November 2019 Update).</span></span>
* <span data-ttu-id="8fca6-108">Correzione di un problema che impedisce l'attivazione degli eventi di movimento da SpatialGestureRecognizer.</span><span class="sxs-lookup"><span data-stu-id="8fca6-108">Fixed issue which prevent hold gesture events being triggered by SpatialGestureRecognizer.</span></span>
* <span data-ttu-id="8fca6-109">Correzione del problema Theading quando si utilizza SpatialSurfaceObserver. SetBoundingVolume.</span><span class="sxs-lookup"><span data-stu-id="8fca6-109">Fixed theading issue when using SpatialSurfaceObserver.SetBoundingVolume.</span></span>

## <span data-ttu-id="8fca6-110">Versione 2.0.12 (18 ottobre 2019)<a name="v2.0.12"></a></span><span class="sxs-lookup"><span data-stu-id="8fca6-110">Version 2.0.12 (October 18, 2019) <a name="v2.0.12"></a></span></span>
* <span data-ttu-id="8fca6-111">Correzione di un arresto anomalo in SpatialGestureRecognizer quando si utilizza NavigationRail (X/Y/Z).</span><span class="sxs-lookup"><span data-stu-id="8fca6-111">Fixed crash in SpatialGestureRecognizer when using NavigationRail(X/Y/Z).</span></span>

## <span data-ttu-id="8fca6-112">Versione 2.0.10 (10 ottobre 2019)<a name="v2.0.10"></a></span><span class="sxs-lookup"><span data-stu-id="8fca6-112">Version 2.0.10 (October 10, 2019) <a name="v2.0.10"></a></span></span>
* <span data-ttu-id="8fca6-113">Correzione di un arresto anomalo quando si usa il pulsante trigger dei controller VR.</span><span class="sxs-lookup"><span data-stu-id="8fca6-113">Fixed crash when using trigger button of VR controllers.</span></span> <span data-ttu-id="8fca6-114">La comunicazione remota olografica non supporta completamente i controller, ma solo il pulsante trigger e il pulsante Windows funzionano se abbinati a HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="8fca6-114">Holographic Remoting does not fully support controllers, only the trigger button and the Windows button are working if paired with HoloLens 2.</span></span>

## <span data-ttu-id="8fca6-115">Versione 2.0.9 (19 settembre 2019)<a name="v2.0.9"></a></span><span class="sxs-lookup"><span data-stu-id="8fca6-115">Version 2.0.9 (September 19, 2019) <a name="v2.0.9"></a></span></span>
* <span data-ttu-id="8fca6-116">Aggiunta del supporto per [SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)</span><span class="sxs-lookup"><span data-stu-id="8fca6-116">Added support for [SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)</span></span>
* <span data-ttu-id="8fca6-117">Aggiunta di una nuova interfaccia ```IPlayerContext2``` (implementata da ```PlayerContext```) che fornisce i membri seguenti:</span><span class="sxs-lookup"><span data-stu-id="8fca6-117">Added new interface ```IPlayerContext2``` (implemented by ```PlayerContext```) providing the following members:</span></span>
  - <span data-ttu-id="8fca6-118">Proprietà [BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout) .</span><span class="sxs-lookup"><span data-stu-id="8fca6-118">[BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)  property.</span></span>
* <span data-ttu-id="8fca6-119">Aggiunto ```Failed_RemoteFrameTooOld``` valore per ```BlitResult```</span><span class="sxs-lookup"><span data-stu-id="8fca6-119">Added ```Failed_RemoteFrameTooOld``` value to ```BlitResult```</span></span>
* <span data-ttu-id="8fca6-120">Miglioramenti alla stabilità e all'affidabilità</span><span class="sxs-lookup"><span data-stu-id="8fca6-120">Stability and reliability improvements</span></span>

## <span data-ttu-id="8fca6-121">Versione 2.0.8 (20 agosto 2019)<a name="v2.0.8"></a></span><span class="sxs-lookup"><span data-stu-id="8fca6-121">Version 2.0.8 (August 20, 2019) <a name="v2.0.8"></a></span></span>

* <span data-ttu-id="8fca6-122">Correzione di un arresto anomalo quando si chiama [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) con un [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) come parametro.</span><span class="sxs-lookup"><span data-stu-id="8fca6-122">Fixed crash when calling [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) with a [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) as parameter.</span></span>
* <span data-ttu-id="8fca6-123">Miglioramenti alla stabilità e all'affidabilità</span><span class="sxs-lookup"><span data-stu-id="8fca6-123">Stability and reliability improvements</span></span>

## <span data-ttu-id="8fca6-124">Versione 2.0.7 (26 luglio 2019)<a name="v2.0.7"></a></span><span class="sxs-lookup"><span data-stu-id="8fca6-124">Version 2.0.7 (July 26, 2019) <a name="v2.0.7"></a></span></span>

* <span data-ttu-id="8fca6-125">Prima versione pubblica della comunicazione remota olografica per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="8fca6-125">First public release of Holographic Remoting for HoloLens 2.</span></span>

## <a name="see-also"></a><span data-ttu-id="8fca6-126">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="8fca6-126">See Also</span></span>
* [<span data-ttu-id="8fca6-127">Scrittura di un'app lettore di comunicazione remota olografica personalizzata</span><span class="sxs-lookup"><span data-stu-id="8fca6-127">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="8fca6-128">Scrittura di un'app host di comunicazione remota olografica</span><span class="sxs-lookup"><span data-stu-id="8fca6-128">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="8fca6-129">Limitazioni e risoluzione dei problemi di comunicazione remota olografica</span><span class="sxs-lookup"><span data-stu-id="8fca6-129">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="8fca6-130">Condizioni di licenza software per Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="8fca6-130">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="8fca6-131">Informativa sulla privacy Microsoft</span><span class="sxs-lookup"><span data-stu-id="8fca6-131">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)

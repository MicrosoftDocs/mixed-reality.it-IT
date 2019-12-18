---
title: Cronologia delle versioni remota olografica
description: Cronologia delle versioni per la comunicazione remota olografica in HoloLens 2.
author: NPohl-MSFT
ms.author: nopohl
ms.date: 10/21/2019
ms.topic: article
keywords: HoloLens, comunicazione remota, comunicazione remota olografica
ms.openlocfilehash: f051dbf24cab550470a312933ffb99e1ba595257
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181961"
---
# <a name="holographic-remoting-version-history"></a><span data-ttu-id="4d305-104">Cronologia delle versioni remota olografica</span><span class="sxs-lookup"><span data-stu-id="4d305-104">Holographic Remoting Version History</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4d305-105">Queste linee guida sono specifiche per la comunicazione remota olografica in HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="4d305-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <span data-ttu-id="4d305-106">Versione 2.0.18.0 (17 dicembre 2019)<a name="v2.0.18"></a></span><span class="sxs-lookup"><span data-stu-id="4d305-106">Version 2.0.18.0 (December 17, 2019) <a name="v2.0.18"></a></span></span>
* <span data-ttu-id="4d305-107">Aggiunta del supporto per HolographicViewConfiguration: https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration</span><span class="sxs-lookup"><span data-stu-id="4d305-107">Added support for HolographicViewConfiguration: https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration</span></span>
* <span data-ttu-id="4d305-108">Corretti vari bug che causavano arresti anomali.</span><span class="sxs-lookup"><span data-stu-id="4d305-108">Fixed various bugs that lead to crashes.</span></span>
* <span data-ttu-id="4d305-109">Correzione del bug in cui è necessario un callback HolographicSpace. CameraAdded per l'accettazione di un HolographicCamera e la visualizzazione come fotocamera aggiuntiva in HoloraphicFrame.</span><span class="sxs-lookup"><span data-stu-id="4d305-109">Fixed bug where a HolographicSpace.CameraAdded callback was required for a HolographicCamera to get accepted and show up as added camera in the HoloraphicFrame.</span></span>

## <span data-ttu-id="4d305-110">Versione 2.0.16 (11 novembre 2019)<a name="2.0.16"></a></span><span class="sxs-lookup"><span data-stu-id="4d305-110">Version 2.0.16 (November 11, 2019) <a name="2.0.16"></a></span></span>
* <span data-ttu-id="4d305-111">Correzione di un deadlock nel rilevamento del codice QR.</span><span class="sxs-lookup"><span data-stu-id="4d305-111">Fixed deadlock in QR code tracking.</span></span>
* <span data-ttu-id="4d305-112">Correzione dell'eccezione unhandeld a causa dell'attesa del blocco nel thread principale.</span><span class="sxs-lookup"><span data-stu-id="4d305-112">Fixed unhandeled exception due to blocking wait in main thread.</span></span>

## <span data-ttu-id="4d305-113">Versione 2.0.14 (26 ottobre 2019)<a name="v2.0.14"></a></span><span class="sxs-lookup"><span data-stu-id="4d305-113">Version 2.0.14 (October 26, 2019) <a name="v2.0.14"></a></span></span>
* <span data-ttu-id="4d305-114">Supporto per le nuove API PerceptionDevice (aggiornamento di Windows 10 di novembre 2019).</span><span class="sxs-lookup"><span data-stu-id="4d305-114">Support for new PerceptionDevice APIs (Windows 10 November 2019 Update).</span></span>
* <span data-ttu-id="4d305-115">Correzione di un problema che impedisce l'attivazione degli eventi di movimento da SpatialGestureRecognizer.</span><span class="sxs-lookup"><span data-stu-id="4d305-115">Fixed issue which prevent hold gesture events being triggered by SpatialGestureRecognizer.</span></span>
* <span data-ttu-id="4d305-116">Correzione del problema di threading quando si utilizza SpatialSurfaceObserver. SetBoundingVolume.</span><span class="sxs-lookup"><span data-stu-id="4d305-116">Fixed threading issue when using SpatialSurfaceObserver.SetBoundingVolume.</span></span>

## <span data-ttu-id="4d305-117">Versione 2.0.12 (18 ottobre 2019)<a name="v2.0.12"></a></span><span class="sxs-lookup"><span data-stu-id="4d305-117">Version 2.0.12 (October 18, 2019) <a name="v2.0.12"></a></span></span>
* <span data-ttu-id="4d305-118">Correzione di un arresto anomalo in SpatialGestureRecognizer quando si utilizza NavigationRail (X/Y/Z).</span><span class="sxs-lookup"><span data-stu-id="4d305-118">Fixed crash in SpatialGestureRecognizer when using NavigationRail(X/Y/Z).</span></span>

## <span data-ttu-id="4d305-119">Versione 2.0.10 (10 ottobre 2019)<a name="v2.0.10"></a></span><span class="sxs-lookup"><span data-stu-id="4d305-119">Version 2.0.10 (October 10, 2019) <a name="v2.0.10"></a></span></span>
* <span data-ttu-id="4d305-120">Correzione di un arresto anomalo quando si usa il pulsante trigger dei controller VR.</span><span class="sxs-lookup"><span data-stu-id="4d305-120">Fixed crash when using trigger button of VR controllers.</span></span> <span data-ttu-id="4d305-121">La comunicazione remota olografica non supporta completamente i controller, ma solo il pulsante trigger e il pulsante Windows funzionano se abbinati a HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="4d305-121">Holographic Remoting does not fully support controllers, only the trigger button and the Windows button are working if paired with HoloLens 2.</span></span>

## <span data-ttu-id="4d305-122">Versione 2.0.9 (19 settembre 2019)<a name="v2.0.9"></a></span><span class="sxs-lookup"><span data-stu-id="4d305-122">Version 2.0.9 (September 19, 2019) <a name="v2.0.9"></a></span></span>
* <span data-ttu-id="4d305-123">Aggiunta del supporto per [SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)</span><span class="sxs-lookup"><span data-stu-id="4d305-123">Added support for [SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)</span></span>
* <span data-ttu-id="4d305-124">Aggiunta di una nuova interfaccia ```IPlayerContext2``` (implementata da ```PlayerContext```) che fornisce i membri seguenti:</span><span class="sxs-lookup"><span data-stu-id="4d305-124">Added new interface ```IPlayerContext2``` (implemented by ```PlayerContext```) providing the following members:</span></span>
  - <span data-ttu-id="4d305-125">Proprietà [BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout) .</span><span class="sxs-lookup"><span data-stu-id="4d305-125">[BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)  property.</span></span>
* <span data-ttu-id="4d305-126">Aggiunto ```Failed_RemoteFrameTooOld``` valore per ```BlitResult```</span><span class="sxs-lookup"><span data-stu-id="4d305-126">Added ```Failed_RemoteFrameTooOld``` value to ```BlitResult```</span></span>
* <span data-ttu-id="4d305-127">Miglioramenti alla stabilità e all'affidabilità</span><span class="sxs-lookup"><span data-stu-id="4d305-127">Stability and reliability improvements</span></span>

## <span data-ttu-id="4d305-128">Versione 2.0.8 (20 agosto 2019)<a name="v2.0.8"></a></span><span class="sxs-lookup"><span data-stu-id="4d305-128">Version 2.0.8 (August 20, 2019) <a name="v2.0.8"></a></span></span>

* <span data-ttu-id="4d305-129">Correzione di un arresto anomalo quando si chiama [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) con un [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) come parametro.</span><span class="sxs-lookup"><span data-stu-id="4d305-129">Fixed crash when calling [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) with a [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) as parameter.</span></span>
* <span data-ttu-id="4d305-130">Miglioramenti alla stabilità e all'affidabilità</span><span class="sxs-lookup"><span data-stu-id="4d305-130">Stability and reliability improvements</span></span>

## <span data-ttu-id="4d305-131">Versione 2.0.7 (26 luglio 2019)<a name="v2.0.7"></a></span><span class="sxs-lookup"><span data-stu-id="4d305-131">Version 2.0.7 (July 26, 2019) <a name="v2.0.7"></a></span></span>

* <span data-ttu-id="4d305-132">Prima versione pubblica della comunicazione remota olografica per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="4d305-132">First public release of Holographic Remoting for HoloLens 2.</span></span>

## <a name="see-also"></a><span data-ttu-id="4d305-133">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="4d305-133">See Also</span></span>
* [<span data-ttu-id="4d305-134">Scrittura di un'app lettore di comunicazione remota olografica personalizzata</span><span class="sxs-lookup"><span data-stu-id="4d305-134">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="4d305-135">Scrittura di un'app host di comunicazione remota olografica</span><span class="sxs-lookup"><span data-stu-id="4d305-135">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="4d305-136">Limitazioni e risoluzione dei problemi di comunicazione remota olografica</span><span class="sxs-lookup"><span data-stu-id="4d305-136">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="4d305-137">Condizioni di licenza software per Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="4d305-137">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="4d305-138">Informativa sulla privacy di Microsoft</span><span class="sxs-lookup"><span data-stu-id="4d305-138">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)

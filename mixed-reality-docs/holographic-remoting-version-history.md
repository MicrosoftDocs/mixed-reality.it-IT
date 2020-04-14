---
title: Cronologia delle versioni remota olografica
description: Cronologia delle versioni per la comunicazione remota olografica in HoloLens 2.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens, comunicazione remota, comunicazione remota olografica
ms.openlocfilehash: 5ba3aaa8874dea4418114b331d3d99fc977e982c
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278199"
---
# <a name="holographic-remoting-version-history"></a><span data-ttu-id="f9523-104">Cronologia delle versioni remota olografica</span><span class="sxs-lookup"><span data-stu-id="f9523-104">Holographic Remoting Version History</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f9523-105">Queste linee guida sono specifiche per la comunicazione remota olografica in HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="f9523-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <a name="version-210-march-11-2020"></a><span data-ttu-id="f9523-106">Versione 2.1.0 (11 marzo 2020)<a name="v2.1.0"></a></span><span class="sxs-lookup"><span data-stu-id="f9523-106">Version 2.1.0 (March 11, 2020) <a name="v2.1.0"></a></span></span>
* <span data-ttu-id="f9523-107">Commutazione del trasporto di rete per l'uso di [RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) tramite UDP.</span><span class="sxs-lookup"><span data-stu-id="f9523-107">Switched network transport to use [RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) via UDP.</span></span> <span data-ttu-id="f9523-108">Le connessioni sicure usano [SRTP](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) Now.</span><span class="sxs-lookup"><span data-stu-id="f9523-108">Secure connections use [SRTP](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) now.</span></span> <span data-ttu-id="f9523-109">Si noti che il [lettore di comunicazione remota olografico](holographic-remoting-player.md) è ancora compatibile con tutte le versioni di comunicazione remota olografica precedentemente disponibili.</span><span class="sxs-lookup"><span data-stu-id="f9523-109">Note, the [Holographic Remoting Player](holographic-remoting-player.md) is still compatible with all previously release Holographic Remoting versions.</span></span> <span data-ttu-id="f9523-110">Per trarre vantaggio dal nuovo trasporto di rete, il lettore di comunicazione remota olografica e l'app remota in questione devono usare la versione 2.1.0.</span><span class="sxs-lookup"><span data-stu-id="f9523-110">To benefit from the new network transport both, the Holographic Remoting Player and the remote app in question, have to use version 2.1.0.</span></span>
* <span data-ttu-id="f9523-111">Aggiunta del supporto per [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span><span class="sxs-lookup"><span data-stu-id="f9523-111">Added support for [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span></span> 

## <a name="version-2020-february-2-2020"></a><span data-ttu-id="f9523-112">Versione 2.0.20 (2 febbraio 2020)<a name="v2.0.20"></a></span><span class="sxs-lookup"><span data-stu-id="f9523-112">Version 2.0.20 (February 2, 2020) <a name="v2.0.20"></a></span></span>
* <span data-ttu-id="f9523-113">Corretti vari bug che causavano arresti anomali.</span><span class="sxs-lookup"><span data-stu-id="f9523-113">Fixed various bugs that lead to crashes.</span></span>

## <a name="version-2018-december-17-2019"></a><span data-ttu-id="f9523-114">Versione 2.0.18 (17 dicembre 2019)<a name="v2.0.18"></a></span><span class="sxs-lookup"><span data-stu-id="f9523-114">Version 2.0.18 (December 17, 2019) <a name="v2.0.18"></a></span></span>
* <span data-ttu-id="f9523-115">Aggiunta del supporto per [HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration)</span><span class="sxs-lookup"><span data-stu-id="f9523-115">Added support for [HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration)</span></span>
* <span data-ttu-id="f9523-116">Corretti vari bug che causavano arresti anomali.</span><span class="sxs-lookup"><span data-stu-id="f9523-116">Fixed various bugs that lead to crashes.</span></span>
* <span data-ttu-id="f9523-117">Correzione del bug in cui è necessario un callback HolographicSpace. CameraAdded per l'accettazione di un HolographicCamera e la visualizzazione come fotocamera aggiuntiva in HoloraphicFrame.</span><span class="sxs-lookup"><span data-stu-id="f9523-117">Fixed bug where a HolographicSpace.CameraAdded callback was required for a HolographicCamera to get accepted and show up as added camera in the HoloraphicFrame.</span></span>

## <a name="version-2016-november-11-2019"></a><span data-ttu-id="f9523-118">Versione 2.0.16 (11 novembre 2019)<a name="2.0.16"></a></span><span class="sxs-lookup"><span data-stu-id="f9523-118">Version 2.0.16 (November 11, 2019) <a name="2.0.16"></a></span></span>
* <span data-ttu-id="f9523-119">Correzione di un deadlock nel rilevamento del codice QR.</span><span class="sxs-lookup"><span data-stu-id="f9523-119">Fixed deadlock in QR code tracking.</span></span>
* <span data-ttu-id="f9523-120">Correzione dell'eccezione unhandeld a causa dell'attesa del blocco nel thread principale.</span><span class="sxs-lookup"><span data-stu-id="f9523-120">Fixed unhandeled exception due to blocking wait in main thread.</span></span>

## <a name="version-2014-october-26-2019"></a><span data-ttu-id="f9523-121">Versione 2.0.14 (26 ottobre 2019)<a name="v2.0.14"></a></span><span class="sxs-lookup"><span data-stu-id="f9523-121">Version 2.0.14 (October 26, 2019) <a name="v2.0.14"></a></span></span>
* <span data-ttu-id="f9523-122">Supporto per le nuove API PerceptionDevice (aggiornamento di Windows 10 di novembre 2019).</span><span class="sxs-lookup"><span data-stu-id="f9523-122">Support for new PerceptionDevice APIs (Windows 10 November 2019 Update).</span></span>
* <span data-ttu-id="f9523-123">Correzione di un problema che impedisce l'attivazione degli eventi di movimento da SpatialGestureRecognizer.</span><span class="sxs-lookup"><span data-stu-id="f9523-123">Fixed issue which prevent hold gesture events being triggered by SpatialGestureRecognizer.</span></span>
* <span data-ttu-id="f9523-124">Correzione del problema di threading quando si utilizza SpatialSurfaceObserver. SetBoundingVolume.</span><span class="sxs-lookup"><span data-stu-id="f9523-124">Fixed threading issue when using SpatialSurfaceObserver.SetBoundingVolume.</span></span>

## <a name="version-2012-october-18-2019"></a><span data-ttu-id="f9523-125">Versione 2.0.12 (18 ottobre 2019)<a name="v2.0.12"></a></span><span class="sxs-lookup"><span data-stu-id="f9523-125">Version 2.0.12 (October 18, 2019) <a name="v2.0.12"></a></span></span>
* <span data-ttu-id="f9523-126">Correzione di un arresto anomalo in SpatialGestureRecognizer quando si utilizza NavigationRail (X/Y/Z).</span><span class="sxs-lookup"><span data-stu-id="f9523-126">Fixed crash in SpatialGestureRecognizer when using NavigationRail(X/Y/Z).</span></span>

## <a name="version-2010-october-10-2019"></a><span data-ttu-id="f9523-127">Versione 2.0.10 (10 ottobre 2019)<a name="v2.0.10"></a></span><span class="sxs-lookup"><span data-stu-id="f9523-127">Version 2.0.10 (October 10, 2019) <a name="v2.0.10"></a></span></span>
* <span data-ttu-id="f9523-128">Correzione di un arresto anomalo quando si usa il pulsante trigger dei controller VR.</span><span class="sxs-lookup"><span data-stu-id="f9523-128">Fixed crash when using trigger button of VR controllers.</span></span> <span data-ttu-id="f9523-129">La comunicazione remota olografica non supporta completamente i controller, ma solo il pulsante trigger e il pulsante Windows funzionano se abbinati a HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="f9523-129">Holographic Remoting does not fully support controllers, only the trigger button and the Windows button are working if paired with HoloLens 2.</span></span>

## <a name="version-209-september-19-2019"></a><span data-ttu-id="f9523-130">Versione 2.0.9 (19 settembre 2019)<a name="v2.0.9"></a></span><span class="sxs-lookup"><span data-stu-id="f9523-130">Version 2.0.9 (September 19, 2019) <a name="v2.0.9"></a></span></span>
* <span data-ttu-id="f9523-131">Aggiunta del supporto per [SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)</span><span class="sxs-lookup"><span data-stu-id="f9523-131">Added support for [SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)</span></span>
* <span data-ttu-id="f9523-132">Aggiunta di una nuova interfaccia ```IPlayerContext2``` (implementata da ```PlayerContext```) che fornisce i membri seguenti:</span><span class="sxs-lookup"><span data-stu-id="f9523-132">Added new interface ```IPlayerContext2``` (implemented by ```PlayerContext```) providing the following members:</span></span>
  - <span data-ttu-id="f9523-133">Proprietà [BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout) .</span><span class="sxs-lookup"><span data-stu-id="f9523-133">[BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)  property.</span></span>
* <span data-ttu-id="f9523-134">Aggiunto ```Failed_RemoteFrameTooOld``` valore per ```BlitResult```</span><span class="sxs-lookup"><span data-stu-id="f9523-134">Added ```Failed_RemoteFrameTooOld``` value to ```BlitResult```</span></span>
* <span data-ttu-id="f9523-135">Miglioramenti alla stabilità e all'affidabilità</span><span class="sxs-lookup"><span data-stu-id="f9523-135">Stability and reliability improvements</span></span>

## <a name="version-208-august-20-2019"></a><span data-ttu-id="f9523-136">Versione 2.0.8 (20 agosto 2019)<a name="v2.0.8"></a></span><span class="sxs-lookup"><span data-stu-id="f9523-136">Version 2.0.8 (August 20, 2019) <a name="v2.0.8"></a></span></span>

* <span data-ttu-id="f9523-137">Correzione di un arresto anomalo quando si chiama [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) con un [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) come parametro.</span><span class="sxs-lookup"><span data-stu-id="f9523-137">Fixed crash when calling [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) with a [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) as parameter.</span></span>
* <span data-ttu-id="f9523-138">Miglioramenti alla stabilità e all'affidabilità</span><span class="sxs-lookup"><span data-stu-id="f9523-138">Stability and reliability improvements</span></span>

## <a name="version-207-july-26-2019"></a><span data-ttu-id="f9523-139">Versione 2.0.7 (26 luglio 2019)<a name="v2.0.7"></a></span><span class="sxs-lookup"><span data-stu-id="f9523-139">Version 2.0.7 (July 26, 2019) <a name="v2.0.7"></a></span></span>

* <span data-ttu-id="f9523-140">Prima versione pubblica della comunicazione remota olografica per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="f9523-140">First public release of Holographic Remoting for HoloLens 2.</span></span>

## <a name="see-also"></a><span data-ttu-id="f9523-141">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="f9523-141">See Also</span></span>
* [<span data-ttu-id="f9523-142">Scrittura di un'app lettore di comunicazione remota olografica personalizzata</span><span class="sxs-lookup"><span data-stu-id="f9523-142">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="f9523-143">Scrittura di un'app host di comunicazione remota olografica</span><span class="sxs-lookup"><span data-stu-id="f9523-143">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="f9523-144">Limitazioni e risoluzione dei problemi di comunicazione remota olografica</span><span class="sxs-lookup"><span data-stu-id="f9523-144">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="f9523-145">Condizioni di licenza software per Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="f9523-145">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="f9523-146">Informativa sulla privacy Microsoft</span><span class="sxs-lookup"><span data-stu-id="f9523-146">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)

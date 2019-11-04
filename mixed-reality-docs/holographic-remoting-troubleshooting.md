---
title: Limitazioni e risoluzione dei problemi di comunicazione remota olografica
description: Procedura di risoluzione dei problemi per la comunicazione remota olografica in HoloLens 2.
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 10/28/2019
ms.topic: article
keywords: Realtà mista di Windows, ologrammi, comunicazione remota olografica, rendering remoto, rendering di rete, HoloLens, ologrammi remoti, risoluzione dei problemi, guida
ms.openlocfilehash: 7b438d9169c9306e0056655e561c04b62b1662cf
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434239"
---
# <a name="holographic-remoting-troubleshooting"></a><span data-ttu-id="b9cf5-104">Risoluzione dei problemi di comunicazione remota olografica</span><span class="sxs-lookup"><span data-stu-id="b9cf5-104">Holographic Remoting troubleshooting</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b9cf5-105">Queste linee guida sono specifiche per la comunicazione remota olografica in HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b9cf5-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <a name="spectre-mitigated-libraries-not-found"></a><span data-ttu-id="b9cf5-106">Non sono state trovate librerie mitigate di Spectre.</span><span class="sxs-lookup"><span data-stu-id="b9cf5-106">Spectre mitigated libraries not found.</span></span>

<span data-ttu-id="b9cf5-107">Per le app di esempio per la comunicazione remota olografica è stata abilitata la mitigazione Spectre (/Qspectre) nella configurazione</span><span class="sxs-lookup"><span data-stu-id="b9cf5-107">Holographic Remoting sample apps have Spectre mitigation (/Qspectre) enabled in Release configuration.</span></span>

<span data-ttu-id="b9cf5-108">Se viene visualizzato un errore irreversibile del linker che indica che non è possibile aprire ' vccorlib. lib ', verificare che il carico di lavoro di Visual Studio includa le librerie mitigate di Spectre.</span><span class="sxs-lookup"><span data-stu-id="b9cf5-108">If you get a fatal linker error which states that 'vccorlib.lib' cannot be opened, make sure that your Visual Studio Workload includes the Spectre mitigated libraries.</span></span> <span data-ttu-id="b9cf5-109">Per ulteriori informazioni, vedere https://aka.ms/Ofhn4c.</span><span class="sxs-lookup"><span data-stu-id="b9cf5-109">See https://aka.ms/Ofhn4c for more information.</span></span>

## <a name="limitations"></a><span data-ttu-id="b9cf5-110">Limitazioni</span><span class="sxs-lookup"><span data-stu-id="b9cf5-110">Limitations</span></span>

<span data-ttu-id="b9cf5-111">Le API seguenti **non** sono attualmente supportate quando si usa la comunicazione remota olografica per HoloLens 2 e in viene generato un errore ```ERROR_NOT_SUPPORTED``` se non diversamente specificato:</span><span class="sxs-lookup"><span data-stu-id="b9cf5-111">The following APIs are currently **not** supported when using Holographic Remoting for HoloLens 2 and will raises an ```ERROR_NOT_SUPPORTED``` error unless otherwise stated:</span></span>

[<span data-ttu-id="b9cf5-112">Windows.Graphics.Holographic</span><span class="sxs-lookup"><span data-stu-id="b9cf5-112">Windows.Graphics.Holographic</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic)

* [<span data-ttu-id="b9cf5-113">HolographicCamera.ViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="b9cf5-113">HolographicCamera.ViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
* [<span data-ttu-id="b9cf5-114">HolographicCameraPose.OverrideProjectionTransform</span><span class="sxs-lookup"><span data-stu-id="b9cf5-114">HolographicCameraPose.OverrideProjectionTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [<span data-ttu-id="b9cf5-115">HolographicCameraPose.OverrideViewport</span><span class="sxs-lookup"><span data-stu-id="b9cf5-115">HolographicCameraPose.OverrideViewport</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [<span data-ttu-id="b9cf5-116">HolographicCameraPose.OverrideViewTransform</span><span class="sxs-lookup"><span data-stu-id="b9cf5-116">HolographicCameraPose.OverrideViewTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
* [<span data-ttu-id="b9cf5-117">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span><span class="sxs-lookup"><span data-stu-id="b9cf5-117">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - <span data-ttu-id="b9cf5-118">Non ha esito negativo, ma il buffer di profondità non sarà remoto.</span><span class="sxs-lookup"><span data-stu-id="b9cf5-118">Does not fail but depth buffer will not be remoted.</span></span>
* [<span data-ttu-id="b9cf5-119">HolographicDisplay.TryGetViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="b9cf5-119">HolographicDisplay.TryGetViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
* [<span data-ttu-id="b9cf5-120">HolographicSpace.CreateFramePresentationMonitor</span><span class="sxs-lookup"><span data-stu-id="b9cf5-120">HolographicSpace.CreateFramePresentationMonitor</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)

[<span data-ttu-id="b9cf5-121">Windows.Perception.Spatial</span><span class="sxs-lookup"><span data-stu-id="b9cf5-121">Windows.Perception.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial)

* [<span data-ttu-id="b9cf5-122">SpatialLocation. AbsoluteAngularAcceleration</span><span class="sxs-lookup"><span data-stu-id="b9cf5-122">SpatialLocation.AbsoluteAngularAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [<span data-ttu-id="b9cf5-123">SpatialLocation. AbsoluteAngularAccelerationAxisAngle</span><span class="sxs-lookup"><span data-stu-id="b9cf5-123">SpatialLocation.AbsoluteAngularAccelerationAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [<span data-ttu-id="b9cf5-124">SpatialLocation. AbsoluteAngularVelocity</span><span class="sxs-lookup"><span data-stu-id="b9cf5-124">SpatialLocation.AbsoluteAngularVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [<span data-ttu-id="b9cf5-125">SpatialLocation. AbsoluteAngularVelocityAxisAngle</span><span class="sxs-lookup"><span data-stu-id="b9cf5-125">SpatialLocation.AbsoluteAngularVelocityAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [<span data-ttu-id="b9cf5-126">SpatialLocation. AbsoluteLinearAcceleration</span><span class="sxs-lookup"><span data-stu-id="b9cf5-126">SpatialLocation.AbsoluteLinearAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [<span data-ttu-id="b9cf5-127">SpatialLocation. AbsoluteLinearVelocity</span><span class="sxs-lookup"><span data-stu-id="b9cf5-127">SpatialLocation.AbsoluteLinearVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [<span data-ttu-id="b9cf5-128">SpatialStageFrameOfReference. Current</span><span class="sxs-lookup"><span data-stu-id="b9cf5-128">SpatialStageFrameOfReference.Current</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - <span data-ttu-id="b9cf5-129">Restituisce sempre ```nullptr```.</span><span class="sxs-lookup"><span data-stu-id="b9cf5-129">Always returns ```nullptr```.</span></span>
* [<span data-ttu-id="b9cf5-130">SpatialStageFrameOfReference.RequestNewStageAsync</span><span class="sxs-lookup"><span data-stu-id="b9cf5-130">SpatialStageFrameOfReference.RequestNewStageAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
* [<span data-ttu-id="b9cf5-131">SpatialAnchor.RemovedByUser</span><span class="sxs-lookup"><span data-stu-id="b9cf5-131">SpatialAnchor.RemovedByUser</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [<span data-ttu-id="b9cf5-132">SpatialAnchorExporter. GetDefault</span><span class="sxs-lookup"><span data-stu-id="b9cf5-132">SpatialAnchorExporter.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - <span data-ttu-id="b9cf5-133">Supportato a partire dalla versione [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span><span class="sxs-lookup"><span data-stu-id="b9cf5-133">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="b9cf5-134">Nelle versioni precedenti restituisce sempre ```nullptr```.</span><span class="sxs-lookup"><span data-stu-id="b9cf5-134">On previous versions always returns ```nullptr```.</span></span> 
* [<span data-ttu-id="b9cf5-135">SpatialAnchorExporter.RequestAccessAsync</span><span class="sxs-lookup"><span data-stu-id="b9cf5-135">SpatialAnchorExporter.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - <span data-ttu-id="b9cf5-136">Supportato a partire dalla versione [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span><span class="sxs-lookup"><span data-stu-id="b9cf5-136">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="b9cf5-137">Nelle versioni precedenti l'operazione asincrona è sempre stata completata con ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span><span class="sxs-lookup"><span data-stu-id="b9cf5-137">On previous versions the async operation always completed with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="b9cf5-138">SpatialAnchorTransferManager.RequestAccessAsync</span><span class="sxs-lookup"><span data-stu-id="b9cf5-138">SpatialAnchorTransferManager.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - <span data-ttu-id="b9cf5-139">L'operazione asincrona viene sempre completata con ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span><span class="sxs-lookup"><span data-stu-id="b9cf5-139">Async operation always completes with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="b9cf5-140">SpatialAnchorTransferManager.TryExportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="b9cf5-140">SpatialAnchorTransferManager.TryExportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - <span data-ttu-id="b9cf5-141">L'operazione asincrona viene sempre completata con ```false```.</span><span class="sxs-lookup"><span data-stu-id="b9cf5-141">Async operation always completes with ```false```.</span></span>
* [<span data-ttu-id="b9cf5-142">SpatialAnchorTransferManager.TryImportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="b9cf5-142">SpatialAnchorTransferManager.TryImportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - <span data-ttu-id="b9cf5-143">L'operazione asincrona viene sempre completata con ```nullptr```.</span><span class="sxs-lookup"><span data-stu-id="b9cf5-143">Async operation always completes with ```nullptr```.</span></span>

[<span data-ttu-id="b9cf5-144">Windows.UI.Input.Spatial</span><span class="sxs-lookup"><span data-stu-id="b9cf5-144">Windows.UI.Input.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)

* [<span data-ttu-id="b9cf5-145">SpatialInteractionSource.TryCreateHandMeshObserver</span><span class="sxs-lookup"><span data-stu-id="b9cf5-145">SpatialInteractionSource.TryCreateHandMeshObserver</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [<span data-ttu-id="b9cf5-146">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span><span class="sxs-lookup"><span data-stu-id="b9cf5-146">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)

[<span data-ttu-id="b9cf5-147">Windows.Perception.Spatial.Preview</span><span class="sxs-lookup"><span data-stu-id="b9cf5-147">Windows.Perception.Spatial.Preview</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview)

* [<span data-ttu-id="b9cf5-148">SpatialGraphInteropPreview.CreateLocatorForNode</span><span class="sxs-lookup"><span data-stu-id="b9cf5-148">SpatialGraphInteropPreview.CreateLocatorForNode</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [<span data-ttu-id="b9cf5-149">SpatialGraphInteropPreview.TryCreateFrameOfReference</span><span class="sxs-lookup"><span data-stu-id="b9cf5-149">SpatialGraphInteropPreview.TryCreateFrameOfReference</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)
* [<span data-ttu-id="b9cf5-150">SpatialInteractionSource. controller</span><span class="sxs-lookup"><span data-stu-id="b9cf5-150">SpatialInteractionSource.Controller</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)

## <a name="see-also"></a><span data-ttu-id="b9cf5-151">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="b9cf5-151">See Also</span></span>
* [<span data-ttu-id="b9cf5-152">Cronologia delle versioni remota olografica</span><span class="sxs-lookup"><span data-stu-id="b9cf5-152">Holographic Remoting Version History</span></span>](holographic-remoting-version-history.md)
* [<span data-ttu-id="b9cf5-153">Scrittura di un'app host di comunicazione remota olografica</span><span class="sxs-lookup"><span data-stu-id="b9cf5-153">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="b9cf5-154">Scrittura di un'app lettore di comunicazione remota olografica personalizzata</span><span class="sxs-lookup"><span data-stu-id="b9cf5-154">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="b9cf5-155">Condizioni di licenza software per Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="b9cf5-155">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="b9cf5-156">Informativa sulla privacy Microsoft</span><span class="sxs-lookup"><span data-stu-id="b9cf5-156">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)

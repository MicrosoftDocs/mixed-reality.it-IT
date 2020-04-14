---
title: Limitazioni e risoluzione dei problemi di comunicazione remota olografica
description: Procedura di risoluzione dei problemi per la comunicazione remota olografica in HoloLens 2.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: Realtà mista di Windows, ologrammi, comunicazione remota olografica, rendering remoto, rendering di rete, HoloLens, ologrammi remoti, risoluzione dei problemi, guida
ms.openlocfilehash: c6d8333bf22c3abb254a9f1b6e30a785effa9999
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277349"
---
# <a name="holographic-remoting-troubleshooting"></a><span data-ttu-id="30e9b-104">Risoluzione dei problemi di comunicazione remota olografica</span><span class="sxs-lookup"><span data-stu-id="30e9b-104">Holographic Remoting troubleshooting</span></span>

> [!IMPORTANT]
> <span data-ttu-id="30e9b-105">Queste linee guida sono specifiche per la comunicazione remota olografica in HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="30e9b-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <a name="spectre-mitigated-libraries-not-found"></a><span data-ttu-id="30e9b-106">Non sono state trovate librerie mitigate di Spectre.</span><span class="sxs-lookup"><span data-stu-id="30e9b-106">Spectre mitigated libraries not found.</span></span>

<span data-ttu-id="30e9b-107">Per le app di esempio per la comunicazione remota olografica è stata abilitata la mitigazione Spectre (/Qspectre) nella configurazione</span><span class="sxs-lookup"><span data-stu-id="30e9b-107">Holographic Remoting sample apps have Spectre mitigation (/Qspectre) enabled in Release configuration.</span></span>

<span data-ttu-id="30e9b-108">Se viene visualizzato un errore irreversibile del linker che indica che non è possibile aprire ' vccorlib. lib ', verificare che il carico di lavoro di Visual Studio includa le librerie mitigate di Spectre.</span><span class="sxs-lookup"><span data-stu-id="30e9b-108">If you get a fatal linker error which states that 'vccorlib.lib' cannot be opened, make sure that your Visual Studio Workload includes the Spectre mitigated libraries.</span></span> <span data-ttu-id="30e9b-109">Per ulteriori informazioni, vedere https://aka.ms/Ofhn4c.</span><span class="sxs-lookup"><span data-stu-id="30e9b-109">See https://aka.ms/Ofhn4c for more information.</span></span>

## <a name="limitations"></a><span data-ttu-id="30e9b-110">Limitazioni</span><span class="sxs-lookup"><span data-stu-id="30e9b-110">Limitations</span></span>

<span data-ttu-id="30e9b-111">Le API seguenti **non** sono attualmente supportate quando si usa la comunicazione remota olografica per HoloLens 2 e in viene generato un errore ```ERROR_NOT_SUPPORTED``` se non diversamente specificato:</span><span class="sxs-lookup"><span data-stu-id="30e9b-111">The following APIs are currently **not** supported when using Holographic Remoting for HoloLens 2 and will raises an ```ERROR_NOT_SUPPORTED``` error unless otherwise stated:</span></span>

[<span data-ttu-id="30e9b-112">Windows.Graphics.Holographic</span><span class="sxs-lookup"><span data-stu-id="30e9b-112">Windows.Graphics.Holographic</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic)

* [<span data-ttu-id="30e9b-113">HolographicCamera.ViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="30e9b-113">HolographicCamera.ViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
  - <span data-ttu-id="30e9b-114">Supportato a partire dalla versione [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span><span class="sxs-lookup"><span data-stu-id="30e9b-114">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="30e9b-115">Nelle versioni precedenti genera sempre un errore.</span><span class="sxs-lookup"><span data-stu-id="30e9b-115">On previous versions always raises an error.</span></span>
* [<span data-ttu-id="30e9b-116">HolographicViewConfiguration.RequestRenderTargetSize</span><span class="sxs-lookup"><span data-stu-id="30e9b-116">HolographicViewConfiguration.RequestRenderTargetSize</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration.requestrendertargetsize#Windows_Graphics_Holographic_HolographicViewConfiguration_RequestRenderTargetSize_Windows_Foundation_Size_)
  - <span data-ttu-id="30e9b-117">Non ha esito negativo, ma le dimensioni della destinazione di rendering non verranno modificate.</span><span class="sxs-lookup"><span data-stu-id="30e9b-117">Does not fail, but the render target size will not be changed.</span></span>
* [<span data-ttu-id="30e9b-118">HolographicCameraPose.OverrideProjectionTransform</span><span class="sxs-lookup"><span data-stu-id="30e9b-118">HolographicCameraPose.OverrideProjectionTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [<span data-ttu-id="30e9b-119">HolographicCameraPose.OverrideViewport</span><span class="sxs-lookup"><span data-stu-id="30e9b-119">HolographicCameraPose.OverrideViewport</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [<span data-ttu-id="30e9b-120">HolographicCameraPose.OverrideViewTransform</span><span class="sxs-lookup"><span data-stu-id="30e9b-120">HolographicCameraPose.OverrideViewTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
* [<span data-ttu-id="30e9b-121">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span><span class="sxs-lookup"><span data-stu-id="30e9b-121">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - <span data-ttu-id="30e9b-122">Non ha esito negativo, ma il buffer di profondità non sarà remoto.</span><span class="sxs-lookup"><span data-stu-id="30e9b-122">Does not fail but depth buffer will not be remoted.</span></span>
  - <span data-ttu-id="30e9b-123">Supportato a partire dalla versione [2.1.0](holographic-remoting-version-history.md#v2.1.0)</span><span class="sxs-lookup"><span data-stu-id="30e9b-123">Supported starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0)</span></span>
* [<span data-ttu-id="30e9b-124">HolographicDisplay.TryGetViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="30e9b-124">HolographicDisplay.TryGetViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
  - <span data-ttu-id="30e9b-125">L'esecuzione di query su HolographicViewConfigurationKind. PhotoVideoCamera restituirà sempre un ```nullptr```.</span><span class="sxs-lookup"><span data-stu-id="30e9b-125">Querying HolographicViewConfigurationKind.PhotoVideoCamera will always return a ```nullptr```.</span></span>
  - <span data-ttu-id="30e9b-126">Supportato a partire dalla versione [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span><span class="sxs-lookup"><span data-stu-id="30e9b-126">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="30e9b-127">Nelle versioni precedenti genera sempre un errore.</span><span class="sxs-lookup"><span data-stu-id="30e9b-127">On previous versions always raises an error.</span></span>
* [<span data-ttu-id="30e9b-128">HolographicSpace.CreateFramePresentationMonitor</span><span class="sxs-lookup"><span data-stu-id="30e9b-128">HolographicSpace.CreateFramePresentationMonitor</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)
* [<span data-ttu-id="30e9b-129">HolographicDisplay. GetDefault</span><span class="sxs-lookup"><span data-stu-id="30e9b-129">HolographicDisplay.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.getdefault#Windows_Graphics_Holographic_HolographicDisplay_GetDefault)
  - <span data-ttu-id="30e9b-130">Segnala un errore se chiamato prima che venga stabilita una connessione.</span><span class="sxs-lookup"><span data-stu-id="30e9b-130">Will report an error if called before a connection was established.</span></span>


[<span data-ttu-id="30e9b-131">Windows.Perception.Spatial</span><span class="sxs-lookup"><span data-stu-id="30e9b-131">Windows.Perception.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial)

* [<span data-ttu-id="30e9b-132">SpatialLocation. AbsoluteAngularAcceleration</span><span class="sxs-lookup"><span data-stu-id="30e9b-132">SpatialLocation.AbsoluteAngularAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [<span data-ttu-id="30e9b-133">SpatialLocation. AbsoluteAngularAccelerationAxisAngle</span><span class="sxs-lookup"><span data-stu-id="30e9b-133">SpatialLocation.AbsoluteAngularAccelerationAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [<span data-ttu-id="30e9b-134">SpatialLocation. AbsoluteAngularVelocity</span><span class="sxs-lookup"><span data-stu-id="30e9b-134">SpatialLocation.AbsoluteAngularVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [<span data-ttu-id="30e9b-135">SpatialLocation. AbsoluteAngularVelocityAxisAngle</span><span class="sxs-lookup"><span data-stu-id="30e9b-135">SpatialLocation.AbsoluteAngularVelocityAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [<span data-ttu-id="30e9b-136">SpatialLocation. AbsoluteLinearAcceleration</span><span class="sxs-lookup"><span data-stu-id="30e9b-136">SpatialLocation.AbsoluteLinearAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [<span data-ttu-id="30e9b-137">SpatialLocation. AbsoluteLinearVelocity</span><span class="sxs-lookup"><span data-stu-id="30e9b-137">SpatialLocation.AbsoluteLinearVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [<span data-ttu-id="30e9b-138">SpatialStageFrameOfReference. Current</span><span class="sxs-lookup"><span data-stu-id="30e9b-138">SpatialStageFrameOfReference.Current</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - <span data-ttu-id="30e9b-139">Restituisce sempre ```nullptr```.</span><span class="sxs-lookup"><span data-stu-id="30e9b-139">Always returns ```nullptr```.</span></span>
* [<span data-ttu-id="30e9b-140">SpatialStageFrameOfReference.RequestNewStageAsync</span><span class="sxs-lookup"><span data-stu-id="30e9b-140">SpatialStageFrameOfReference.RequestNewStageAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
* [<span data-ttu-id="30e9b-141">SpatialAnchor.RemovedByUser</span><span class="sxs-lookup"><span data-stu-id="30e9b-141">SpatialAnchor.RemovedByUser</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [<span data-ttu-id="30e9b-142">SpatialAnchorExporter. GetDefault</span><span class="sxs-lookup"><span data-stu-id="30e9b-142">SpatialAnchorExporter.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - <span data-ttu-id="30e9b-143">Supportato a partire dalla versione [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span><span class="sxs-lookup"><span data-stu-id="30e9b-143">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="30e9b-144">Nelle versioni precedenti restituisce sempre ```nullptr```.</span><span class="sxs-lookup"><span data-stu-id="30e9b-144">On previous versions always returns ```nullptr```.</span></span> 
* [<span data-ttu-id="30e9b-145">SpatialAnchorExporter.RequestAccessAsync</span><span class="sxs-lookup"><span data-stu-id="30e9b-145">SpatialAnchorExporter.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - <span data-ttu-id="30e9b-146">Supportato a partire dalla versione [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span><span class="sxs-lookup"><span data-stu-id="30e9b-146">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="30e9b-147">Nelle versioni precedenti l'operazione asincrona è sempre stata completata con ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span><span class="sxs-lookup"><span data-stu-id="30e9b-147">On previous versions the async operation always completed with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="30e9b-148">SpatialAnchorTransferManager.RequestAccessAsync</span><span class="sxs-lookup"><span data-stu-id="30e9b-148">SpatialAnchorTransferManager.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - <span data-ttu-id="30e9b-149">L'operazione asincrona viene sempre completata con ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span><span class="sxs-lookup"><span data-stu-id="30e9b-149">Async operation always completes with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="30e9b-150">SpatialAnchorTransferManager.TryExportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="30e9b-150">SpatialAnchorTransferManager.TryExportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - <span data-ttu-id="30e9b-151">L'operazione asincrona viene sempre completata con ```false```.</span><span class="sxs-lookup"><span data-stu-id="30e9b-151">Async operation always completes with ```false```.</span></span>
* [<span data-ttu-id="30e9b-152">SpatialAnchorTransferManager.TryImportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="30e9b-152">SpatialAnchorTransferManager.TryImportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - <span data-ttu-id="30e9b-153">L'operazione asincrona viene sempre completata con ```nullptr```.</span><span class="sxs-lookup"><span data-stu-id="30e9b-153">Async operation always completes with ```nullptr```.</span></span>

[<span data-ttu-id="30e9b-154">Windows.UI.Input.Spatial</span><span class="sxs-lookup"><span data-stu-id="30e9b-154">Windows.UI.Input.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)

* [<span data-ttu-id="30e9b-155">SpatialInteractionSource.TryCreateHandMeshObserver</span><span class="sxs-lookup"><span data-stu-id="30e9b-155">SpatialInteractionSource.TryCreateHandMeshObserver</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [<span data-ttu-id="30e9b-156">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span><span class="sxs-lookup"><span data-stu-id="30e9b-156">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)

[<span data-ttu-id="30e9b-157">Windows.Perception.Spatial.Preview</span><span class="sxs-lookup"><span data-stu-id="30e9b-157">Windows.Perception.Spatial.Preview</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview)

* [<span data-ttu-id="30e9b-158">SpatialGraphInteropPreview.CreateLocatorForNode</span><span class="sxs-lookup"><span data-stu-id="30e9b-158">SpatialGraphInteropPreview.CreateLocatorForNode</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [<span data-ttu-id="30e9b-159">SpatialGraphInteropPreview.TryCreateFrameOfReference</span><span class="sxs-lookup"><span data-stu-id="30e9b-159">SpatialGraphInteropPreview.TryCreateFrameOfReference</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)
* [<span data-ttu-id="30e9b-160">SpatialInteractionSource. controller</span><span class="sxs-lookup"><span data-stu-id="30e9b-160">SpatialInteractionSource.Controller</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)

## <a name="see-also"></a><span data-ttu-id="30e9b-161">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="30e9b-161">See Also</span></span>
* [<span data-ttu-id="30e9b-162">Cronologia delle versioni remota olografica</span><span class="sxs-lookup"><span data-stu-id="30e9b-162">Holographic Remoting Version History</span></span>](holographic-remoting-version-history.md)
* [<span data-ttu-id="30e9b-163">Scrittura di un'app remota olografica remota</span><span class="sxs-lookup"><span data-stu-id="30e9b-163">Writing a Holographic Remoting remote app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="30e9b-164">Scrittura di un'app lettore di comunicazione remota olografica personalizzata</span><span class="sxs-lookup"><span data-stu-id="30e9b-164">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="30e9b-165">Condizioni di licenza software per Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="30e9b-165">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="30e9b-166">Informativa sulla privacy Microsoft</span><span class="sxs-lookup"><span data-stu-id="30e9b-166">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)

---
title: Limitazioni e risoluzione dei problemi di comunicazione remota olografica
description: Procedura di risoluzione dei problemi per la comunicazione remota olografica in HoloLens 2.
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 12/17/2019
ms.topic: article
keywords: Realtà mista di Windows, ologrammi, comunicazione remota olografica, rendering remoto, rendering di rete, HoloLens, ologrammi remoti, risoluzione dei problemi, guida
ms.openlocfilehash: 05333c8911010945a543cf603b9925eb30c841db
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181971"
---
# <a name="holographic-remoting-troubleshooting"></a><span data-ttu-id="32b35-104">Risoluzione dei problemi di comunicazione remota olografica</span><span class="sxs-lookup"><span data-stu-id="32b35-104">Holographic Remoting troubleshooting</span></span>

> [!IMPORTANT]
> <span data-ttu-id="32b35-105">Queste linee guida sono specifiche per la comunicazione remota olografica in HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="32b35-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <a name="spectre-mitigated-libraries-not-found"></a><span data-ttu-id="32b35-106">Non sono state trovate librerie mitigate di Spectre.</span><span class="sxs-lookup"><span data-stu-id="32b35-106">Spectre mitigated libraries not found.</span></span>

<span data-ttu-id="32b35-107">Per le app di esempio per la comunicazione remota olografica è stata abilitata la mitigazione Spectre (/Qspectre) nella configurazione</span><span class="sxs-lookup"><span data-stu-id="32b35-107">Holographic Remoting sample apps have Spectre mitigation (/Qspectre) enabled in Release configuration.</span></span>

<span data-ttu-id="32b35-108">Se viene visualizzato un errore irreversibile del linker che indica che non è possibile aprire ' vccorlib. lib ', verificare che il carico di lavoro di Visual Studio includa le librerie mitigate di Spectre.</span><span class="sxs-lookup"><span data-stu-id="32b35-108">If you get a fatal linker error which states that 'vccorlib.lib' cannot be opened, make sure that your Visual Studio Workload includes the Spectre mitigated libraries.</span></span> <span data-ttu-id="32b35-109">Per ulteriori informazioni, vedere https://aka.ms/Ofhn4c.</span><span class="sxs-lookup"><span data-stu-id="32b35-109">See https://aka.ms/Ofhn4c for more information.</span></span>

## <a name="limitations"></a><span data-ttu-id="32b35-110">Limitazioni</span><span class="sxs-lookup"><span data-stu-id="32b35-110">Limitations</span></span>

<span data-ttu-id="32b35-111">Le API seguenti **non** sono attualmente supportate quando si usa la comunicazione remota olografica per HoloLens 2 e in viene generato un errore ```ERROR_NOT_SUPPORTED``` se non diversamente specificato:</span><span class="sxs-lookup"><span data-stu-id="32b35-111">The following APIs are currently **not** supported when using Holographic Remoting for HoloLens 2 and will raises an ```ERROR_NOT_SUPPORTED``` error unless otherwise stated:</span></span>

[<span data-ttu-id="32b35-112">Windows.Graphics.Holographic</span><span class="sxs-lookup"><span data-stu-id="32b35-112">Windows.Graphics.Holographic</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic)

* [<span data-ttu-id="32b35-113">HolographicCamera.ViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="32b35-113">HolographicCamera.ViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
  - <span data-ttu-id="32b35-114">Supportato a partire dalla versione [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span><span class="sxs-lookup"><span data-stu-id="32b35-114">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="32b35-115">Nelle versioni precedenti genera sempre un errore.</span><span class="sxs-lookup"><span data-stu-id="32b35-115">On previous versions always raises an error.</span></span>
* [<span data-ttu-id="32b35-116">HolographicViewConfiguration.RequestRenderTargetSize</span><span class="sxs-lookup"><span data-stu-id="32b35-116">HolographicViewConfiguration.RequestRenderTargetSize</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration.requestrendertargetsize#Windows_Graphics_Holographic_HolographicViewConfiguration_RequestRenderTargetSize_Windows_Foundation_Size_)
  - <span data-ttu-id="32b35-117">Non ha esito negativo, ma le dimensioni della destinazione di rendering non verranno modificate.</span><span class="sxs-lookup"><span data-stu-id="32b35-117">Does not fail, but the render target size will not be changed.</span></span>
* [<span data-ttu-id="32b35-118">HolographicCameraPose.OverrideProjectionTransform</span><span class="sxs-lookup"><span data-stu-id="32b35-118">HolographicCameraPose.OverrideProjectionTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [<span data-ttu-id="32b35-119">HolographicCameraPose.OverrideViewport</span><span class="sxs-lookup"><span data-stu-id="32b35-119">HolographicCameraPose.OverrideViewport</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [<span data-ttu-id="32b35-120">HolographicCameraPose.OverrideViewTransform</span><span class="sxs-lookup"><span data-stu-id="32b35-120">HolographicCameraPose.OverrideViewTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
* [<span data-ttu-id="32b35-121">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span><span class="sxs-lookup"><span data-stu-id="32b35-121">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - <span data-ttu-id="32b35-122">Non ha esito negativo, ma il buffer di profondità non sarà remoto.</span><span class="sxs-lookup"><span data-stu-id="32b35-122">Does not fail but depth buffer will not be remoted.</span></span>
* [<span data-ttu-id="32b35-123">HolographicDisplay.TryGetViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="32b35-123">HolographicDisplay.TryGetViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
  - <span data-ttu-id="32b35-124">L'esecuzione di query su HolographicViewConfigurationKind. PhotoVideoCamera restituirà sempre un ```nullptr```.</span><span class="sxs-lookup"><span data-stu-id="32b35-124">Querying HolographicViewConfigurationKind.PhotoVideoCamera will always return a ```nullptr```.</span></span>
  - <span data-ttu-id="32b35-125">Supportato a partire dalla versione [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span><span class="sxs-lookup"><span data-stu-id="32b35-125">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="32b35-126">Nelle versioni precedenti genera sempre un errore.</span><span class="sxs-lookup"><span data-stu-id="32b35-126">On previous versions always raises an error.</span></span>
* [<span data-ttu-id="32b35-127">HolographicSpace.CreateFramePresentationMonitor</span><span class="sxs-lookup"><span data-stu-id="32b35-127">HolographicSpace.CreateFramePresentationMonitor</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)
* [<span data-ttu-id="32b35-128">HolographicDisplay. GetDefault</span><span class="sxs-lookup"><span data-stu-id="32b35-128">HolographicDisplay.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.getdefault#Windows_Graphics_Holographic_HolographicDisplay_GetDefault)
  - <span data-ttu-id="32b35-129">Segnala un errore se chiamato prima che venga stabilita una connessione.</span><span class="sxs-lookup"><span data-stu-id="32b35-129">Will report an error if called before a connection was established.</span></span>


[<span data-ttu-id="32b35-130">Windows.Perception.Spatial</span><span class="sxs-lookup"><span data-stu-id="32b35-130">Windows.Perception.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial)

* [<span data-ttu-id="32b35-131">SpatialLocation. AbsoluteAngularAcceleration</span><span class="sxs-lookup"><span data-stu-id="32b35-131">SpatialLocation.AbsoluteAngularAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [<span data-ttu-id="32b35-132">SpatialLocation. AbsoluteAngularAccelerationAxisAngle</span><span class="sxs-lookup"><span data-stu-id="32b35-132">SpatialLocation.AbsoluteAngularAccelerationAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [<span data-ttu-id="32b35-133">SpatialLocation. AbsoluteAngularVelocity</span><span class="sxs-lookup"><span data-stu-id="32b35-133">SpatialLocation.AbsoluteAngularVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [<span data-ttu-id="32b35-134">SpatialLocation. AbsoluteAngularVelocityAxisAngle</span><span class="sxs-lookup"><span data-stu-id="32b35-134">SpatialLocation.AbsoluteAngularVelocityAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [<span data-ttu-id="32b35-135">SpatialLocation. AbsoluteLinearAcceleration</span><span class="sxs-lookup"><span data-stu-id="32b35-135">SpatialLocation.AbsoluteLinearAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [<span data-ttu-id="32b35-136">SpatialLocation. AbsoluteLinearVelocity</span><span class="sxs-lookup"><span data-stu-id="32b35-136">SpatialLocation.AbsoluteLinearVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [<span data-ttu-id="32b35-137">SpatialStageFrameOfReference. Current</span><span class="sxs-lookup"><span data-stu-id="32b35-137">SpatialStageFrameOfReference.Current</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - <span data-ttu-id="32b35-138">Restituisce sempre ```nullptr```.</span><span class="sxs-lookup"><span data-stu-id="32b35-138">Always returns ```nullptr```.</span></span>
* [<span data-ttu-id="32b35-139">SpatialStageFrameOfReference.RequestNewStageAsync</span><span class="sxs-lookup"><span data-stu-id="32b35-139">SpatialStageFrameOfReference.RequestNewStageAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
* [<span data-ttu-id="32b35-140">SpatialAnchor.RemovedByUser</span><span class="sxs-lookup"><span data-stu-id="32b35-140">SpatialAnchor.RemovedByUser</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [<span data-ttu-id="32b35-141">SpatialAnchorExporter. GetDefault</span><span class="sxs-lookup"><span data-stu-id="32b35-141">SpatialAnchorExporter.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - <span data-ttu-id="32b35-142">Supportato a partire dalla versione [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span><span class="sxs-lookup"><span data-stu-id="32b35-142">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="32b35-143">Nelle versioni precedenti restituisce sempre ```nullptr```.</span><span class="sxs-lookup"><span data-stu-id="32b35-143">On previous versions always returns ```nullptr```.</span></span> 
* [<span data-ttu-id="32b35-144">SpatialAnchorExporter.RequestAccessAsync</span><span class="sxs-lookup"><span data-stu-id="32b35-144">SpatialAnchorExporter.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - <span data-ttu-id="32b35-145">Supportato a partire dalla versione [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span><span class="sxs-lookup"><span data-stu-id="32b35-145">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="32b35-146">Nelle versioni precedenti l'operazione asincrona è sempre stata completata con ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span><span class="sxs-lookup"><span data-stu-id="32b35-146">On previous versions the async operation always completed with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="32b35-147">SpatialAnchorTransferManager.RequestAccessAsync</span><span class="sxs-lookup"><span data-stu-id="32b35-147">SpatialAnchorTransferManager.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - <span data-ttu-id="32b35-148">L'operazione asincrona viene sempre completata con ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span><span class="sxs-lookup"><span data-stu-id="32b35-148">Async operation always completes with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="32b35-149">SpatialAnchorTransferManager.TryExportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="32b35-149">SpatialAnchorTransferManager.TryExportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - <span data-ttu-id="32b35-150">L'operazione asincrona viene sempre completata con ```false```.</span><span class="sxs-lookup"><span data-stu-id="32b35-150">Async operation always completes with ```false```.</span></span>
* [<span data-ttu-id="32b35-151">SpatialAnchorTransferManager.TryImportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="32b35-151">SpatialAnchorTransferManager.TryImportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - <span data-ttu-id="32b35-152">L'operazione asincrona viene sempre completata con ```nullptr```.</span><span class="sxs-lookup"><span data-stu-id="32b35-152">Async operation always completes with ```nullptr```.</span></span>

[<span data-ttu-id="32b35-153">Windows.UI.Input.Spatial</span><span class="sxs-lookup"><span data-stu-id="32b35-153">Windows.UI.Input.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)

* [<span data-ttu-id="32b35-154">SpatialInteractionSource.TryCreateHandMeshObserver</span><span class="sxs-lookup"><span data-stu-id="32b35-154">SpatialInteractionSource.TryCreateHandMeshObserver</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [<span data-ttu-id="32b35-155">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span><span class="sxs-lookup"><span data-stu-id="32b35-155">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)

[<span data-ttu-id="32b35-156">Windows.Perception.Spatial.Preview</span><span class="sxs-lookup"><span data-stu-id="32b35-156">Windows.Perception.Spatial.Preview</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview)

* [<span data-ttu-id="32b35-157">SpatialGraphInteropPreview.CreateLocatorForNode</span><span class="sxs-lookup"><span data-stu-id="32b35-157">SpatialGraphInteropPreview.CreateLocatorForNode</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [<span data-ttu-id="32b35-158">SpatialGraphInteropPreview.TryCreateFrameOfReference</span><span class="sxs-lookup"><span data-stu-id="32b35-158">SpatialGraphInteropPreview.TryCreateFrameOfReference</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)
* [<span data-ttu-id="32b35-159">SpatialInteractionSource. controller</span><span class="sxs-lookup"><span data-stu-id="32b35-159">SpatialInteractionSource.Controller</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)

## <a name="see-also"></a><span data-ttu-id="32b35-160">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="32b35-160">See Also</span></span>
* [<span data-ttu-id="32b35-161">Cronologia delle versioni remota olografica</span><span class="sxs-lookup"><span data-stu-id="32b35-161">Holographic Remoting Version History</span></span>](holographic-remoting-version-history.md)
* [<span data-ttu-id="32b35-162">Scrittura di un'app host di comunicazione remota olografica</span><span class="sxs-lookup"><span data-stu-id="32b35-162">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="32b35-163">Scrittura di un'app lettore di comunicazione remota olografica personalizzata</span><span class="sxs-lookup"><span data-stu-id="32b35-163">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="32b35-164">Condizioni di licenza software per Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="32b35-164">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="32b35-165">Informativa sulla privacy di Microsoft</span><span class="sxs-lookup"><span data-stu-id="32b35-165">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)

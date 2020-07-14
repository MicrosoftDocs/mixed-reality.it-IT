---
title: Limitazioni e risoluzione dei problemi di comunicazione remota olografica
description: Procedura di risoluzione dei problemi per la comunicazione remota olografica in HoloLens 2.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: Realtà mista di Windows, ologrammi, comunicazione remota olografica, rendering remoto, rendering di rete, HoloLens, ologrammi remoti, risoluzione dei problemi, guida
ms.openlocfilehash: 593b242326b83d4596d22a7e1a39ef18c26bc67a
ms.sourcegitcommit: b392847529961ac36bbff154ce0830f8b2dbd766
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/14/2020
ms.locfileid: "86300503"
---
# <a name="holographic-remoting-troubleshooting"></a>Risoluzione dei problemi di comunicazione remota olografica

> [!IMPORTANT]
> Queste linee guida sono specifiche per la comunicazione remota olografica in HoloLens 2.

## <a name="spectre-mitigated-libraries-not-found"></a>Non sono state trovate librerie mitigate di Spectre.

Per le app di esempio per la comunicazione remota olografica è stata abilitata la mitigazione Spectre (/Qspectre) nella configurazione

Se viene visualizzato un errore irreversibile del linker che indica che non è possibile aprire ' vccorlib. lib ', verificare che il carico di lavoro di Visual Studio includa le librerie mitigate di Spectre. Per altre informazioni, vedere https://aka.ms/Ofhn4c.

## <a name="speech"></a>Voce

Il lettore di comunicazione remota olografica supporta una sovrapposizione di diagnostica che può essere abilitata in base a quanto detto ```Enable Diagnostics``` e disabilitato ```Disable Diagnostics``` . Se si riscontrano problemi con questi comandi vocali, è anche possibile avviare il lettore di comunicazione remota olografica tramite un Web browser usando ```ms-holographic-remoting:?stats``` come URL.

## <a name="h265-video-codec-not-available"></a>Codec video H265 non disponibile

È necessario installare le [estensioni video di HEVC](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7) quando si usa il codec video di H265 nell'app remota. Se si verificano problemi in cui il codec è installato ma non può essere usato, consultare la guida alla [risoluzione dei problemi](https://docs.microsoft.com/azure/remote-rendering/resources/troubleshoot#h265-codec-not-available) .

## <a name="limitations"></a>Limitazioni

Le API seguenti **non** sono attualmente supportate quando si usa la comunicazione remota olografica per HoloLens 2 e genera un ```ERROR_NOT_SUPPORTED``` errore se non diversamente specificato:

[Windows.Graphics.Holographic](https://docs.microsoft.com/uwp/api/windows.graphics.holographic)

* [HolographicCamera.ViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
  - Supportato a partire dalla versione [2.0.18](holographic-remoting-version-history.md#v2.0.18)
  - Nelle versioni precedenti genera sempre un errore.
* [HolographicCamera.IsHardwareContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled#Windows_Graphics_Holographic_HolographicCamera_IsHardwareContentProtectionEnabled)
* [HolographicViewConfiguration.RequestRenderTargetSize](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration.requestrendertargetsize#Windows_Graphics_Holographic_HolographicViewConfiguration_RequestRenderTargetSize_Windows_Foundation_Size_)
  - Supportato a partire dalla versione [2.2.0](holographic-remoting-version-history.md#v2.2.0)
  - Nelle versioni precedenti non ha esito negativo, ma le dimensioni della destinazione di rendering non verranno modificate.
* [HolographicCameraPose.OverrideProjectionTransform](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [HolographicCameraPose.OverrideViewport](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [HolographicCameraPose.OverrideViewTransform](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
  - Supportato a partire dalla versione [2.2.0](holographic-remoting-version-history.md#v2.2.0)
* [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - Non ha esito negativo, ma il buffer di profondità non sarà remoto.
  - Supportato a partire dalla versione [2.1.0](holographic-remoting-version-history.md#v2.1.0)
* [HolographicDisplay.TryGetViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
  - L'esecuzione di query su HolographicViewConfigurationKind. PhotoVideoCamera restituirà sempre un ```nullptr``` .
  - Supportato a partire dalla versione [2.0.18](holographic-remoting-version-history.md#v2.0.18)
  - Nelle versioni precedenti genera sempre un errore.
* [HolographicSpace.CreateFramePresentationMonitor](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)
* [HolographicDisplay. GetDefault](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.getdefault#Windows_Graphics_Holographic_HolographicDisplay_GetDefault)
  - Segnala un errore se chiamato prima che venga stabilita una connessione.


[Windows.Perception.Spatial](https://docs.microsoft.com/uwp/api/windows.perception.spatial)

* [SpatialLocation. AbsoluteAngularAcceleration](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [SpatialLocation.AbsoluteAngularAccelerationAxisAngle](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [SpatialLocation. AbsoluteAngularVelocity](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [SpatialLocation.AbsoluteAngularVelocityAxisAngle](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [SpatialLocation. AbsoluteLinearAcceleration](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [SpatialLocation. AbsoluteLinearVelocity](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [SpatialStageFrameOfReference. Current](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - Supportato a partire dalla versione [2.2.0](holographic-remoting-version-history.md#v2.2.0)
  - Nelle versioni precedenti restituisce sempre ```nullptr``` .
* [SpatialStageFrameOfReference.RequestNewStageAsync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
  - Supportato a partire dalla versione [2.2.0](holographic-remoting-version-history.md#v2.2.0)
* [SpatialAnchor.RemovedByUser](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [SpatialAnchorExporter.GetDefault](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - Supportato a partire dalla versione [2.0.9](holographic-remoting-version-history.md#v2.0.9). 
  - Nelle versioni precedenti restituisce sempre ```nullptr``` . 
* [SpatialAnchorExporter.RequestAccessAsync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - Supportato a partire dalla versione [2.0.9](holographic-remoting-version-history.md#v2.0.9). 
  - Nelle versioni precedenti l'operazione asincrona è stata completata sempre con ```SpatialPerceptionAccessStatus.DeniedBySystem``` .
* [SpatialAnchorTransferManager.RequestAccessAsync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - L'operazione asincrona viene sempre completata con ```SpatialPerceptionAccessStatus.DeniedBySystem``` .
* [SpatialAnchorTransferManager.TryExportAnchorsAsync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - L'operazione asincrona viene sempre completata con ```false``` .
* [SpatialAnchorTransferManager.TryImportAnchorsAsync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - L'operazione asincrona viene sempre completata con ```nullptr``` .

[Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)

* [SpatialInteractionSource.TryCreateHandMeshObserver](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [SpatialInteractionSource.TryCreateHandMeshObserverAsync](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)
* [SpatialInteractionSource. controller](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)
  - Supportato a partire dalla versione [2.2.0](holographic-remoting-version-history.md#v2.2.0)

[Windows.Perception.Spatial.Preview](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview)

* [SpatialGraphInteropPreview.CreateLocatorForNode](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [SpatialGraphInteropPreview.TryCreateFrameOfReference](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)

## <a name="see-also"></a>Vedere anche
* [Cronologia delle versioni remota olografica](holographic-remoting-version-history.md)
* [Scrivere un'app remota Holographic Remoting](holographic-remoting-create-host.md)
* [Scrivere un'app lettore Holographic Remoting personalizzata](holographic-remoting-create-player.md)
* [Condizioni di licenza software per Holographic Remoting](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Informativa sulla privacy di Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)

---
title: Cronologia delle versioni remota olografica
description: Cronologia delle versioni per la comunicazione remota olografica in HoloLens 2.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens, comunicazione remota, comunicazione remota olografica
ms.openlocfilehash: 1f4d463ab734cbb627f251486b0058fbf295d2ed
ms.sourcegitcommit: b392847529961ac36bbff154ce0830f8b2dbd766
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/14/2020
ms.locfileid: "86300522"
---
# <a name="holographic-remoting-version-history"></a>Cronologia delle versioni remota olografica

> [!IMPORTANT]
> Queste linee guida sono specifiche per la comunicazione remota olografica in HoloLens 2.

## <a name="version-222-july-10-2020"></a>Versione 2.2.2 (10 luglio 2020)<a name="v2.2.2"></a>
* Correzione di un problema relativo a [HolographicCamera. LeftViewportParameters](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.leftviewportparameters?view=winrt-19041#Windows_Graphics_Holographic_HolographicCamera_LeftViewportParameters) e [HolographicCamera. RightViewportParameters](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.rightviewportparameters?view=winrt-19041#Windows_Graphics_Holographic_HolographicCamera_RightViewportParameters) che non restituisce alcun vertice di mesh di area nascosta durante il flusso da un auricolare a realtà mista di Windows.
* Correzione di un arresto anomalo che può verificarsi con una connessione di rete insufficiente.

## <a name="version-221-july-6-2020"></a>Versione 2.2.1 (6 luglio 2020)<a name="v2.2.1"></a>
> [!IMPORTANT]
> La convalida del [Kit di certificazione app Windows](https://developer.microsoft.com/windows/downloads/app-certification-kit/) con versione [2.2.0](holographic-remoting-version-history.md#v2.2.0) avrà esito negativo. Se si usa la versione [2.2.0](holographic-remoting-version-history.md#v2.2.0) e si vuole inviare l'applicazione a Microsoft Store, aggiornare almeno alla versione 2.2.1.
* Correzione dei problemi di conformità del [Kit di certificazione app Windows](https://developer.microsoft.com/windows/downloads/app-certification-kit/) .

## <a name="version-220-july-1-2020"></a>Versione 2.2.0 (1 luglio 2020)<a name="v2.2.0"></a>
* È ora possibile installare il lettore di comunicazione remota olografica nei PC che eseguono la [realtà mista di Windows](navigating-the-windows-mixed-reality-home.md), rendendo possibile lo streaming di auricolari immersivi.
* I [controller di movimento](motion-controllers.md) sono ora supportati dalla comunicazione remota olografica e i dati specifici del controller possono essere recuperati tramite [SpatialInteractionSource. controller](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller).
* [SpatialStageFrameOfReference](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference) è ora supportato e la fase corrente può essere recuperata tramite [SpatialStageFrameOfReference. Current](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current). Inoltre, è possibile richiedere una nuova fase tramite [SpatialStageFrameOfReference. RequestNewStageAsync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync).
* Nelle versioni precedenti, la stima di pose è stata completamente gestita sul lato Player da parte del lettore di comunicazione remota olografica. A partire dalla versione 2.2.0, la comunicazione remota olografica ha la sincronizzazione dell'ora e la stima viene eseguita completamente dall'applicazione remota. Gli utenti devono inoltre prevedere una maggiore stabilità degli ologrammi in situazioni di rete complesse.

## <a name="version-213-may-25-2020"></a>Versione 2.1.3 (25 maggio 2020)<a name="v2.1.3"></a>
* Comportamento modificato dell'evento [HolographicSpace. CameraAdded](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.cameraadded?view=winrt-18362) . Nelle versioni **precedenti non era garantito che** un [HolographicCamera](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera?view=winrt-18362) aggiunto abbia anche un [HolographicCameraPose](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose?view=winrt-18362) valido durante la creazione del frame successivo tramite [HolographicSpace. CreateNextFrame](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createnextframe?view=winrt-18362#Windows_Graphics_Holographic_HolographicSpace_CreateNextFrame). A partire dalla versione 2.1.3 [HolographicSpace. CameraAdded](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.cameraadded?view=winrt-18362) è sincronizzato con i dati di post provenienti dal lettore di comunicazione remota olografica e gli utenti possono aspettarsi che, quando viene aggiunta una fotocamera, sia disponibile anche un [HolographicCameraPose](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose?view=winrt-18362) valido per tale fotocamera nel frame successivo.
* Aggiunto **disabilitato** a DepthBufferStreamResolution che può essere usato per disabilitare il flusso del buffer di profondità tramite RemoteContext.ConfigureDepthVideoStream. Si noti che se si usa [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer?view=winrt-18362#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) avrà esito negativo con *E_ILLEGAL_METHOD_CALL*.
* La schermata iniziale del lettore di comunicazione remota olografica è stata riprogettata e ora non blocca la visualizzazione degli utenti.
* Miglioramenti alla stabilità e correzioni di bug.

## <a name="version-212-april-5-2020"></a>Versione 2.1.2 (5 aprile 2020)<a name="v2.1.2"></a>
* Correzione del problema di compatibilità con le versioni precedenti dell'audio tra la versione più recente di Remote Remoting Player e le app Remote con una versione inferiore a 2.1.0.
* Problema di ancoraggio spaziale fisso che ha chiuso in modo imprevisto il lettore remoto olografico. Questo problema interessa anche i giocatori personalizzati.

## <a name="version-211-march-20-2020"></a>Versione 2.1.1 (20 marzo 2020)<a name="v2.1.1"></a>
* Correzione del problema di codifica video con le app remote quando si usano GPU AMD.
* Miglioramenti delle prestazioni del lettore di comunicazione remota olografico.

## <a name="version-210-march-11-2020"></a>Versione 2.1.0 (11 marzo 2020)<a name="v2.1.0"></a>
* Commutazione del trasporto di rete per l'uso di [RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) tramite UDP. Le connessioni sicure usano [SRTP](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) Now. Si noti che il [lettore di comunicazione remota olografico](holographic-remoting-player.md) è ancora compatibile con tutte le versioni di comunicazione remota olografica precedentemente disponibili. Per trarre vantaggio dal nuovo trasporto di rete, il lettore di comunicazione remota olografica e l'app remota in questione devono usare la versione 2.1.0.
* Aggiunta del supporto per [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_). 

## <a name="version-2020-february-2-2020"></a>Versione 2.0.20 (2 febbraio 2020)<a name="v2.0.20"></a>
* Corretti vari bug che causavano arresti anomali.

## <a name="version-2018-december-17-2019"></a>Versione 2.0.18 (17 dicembre 2019)<a name="v2.0.18"></a>
* Aggiunta del supporto per [HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration)
* Corretti vari bug che causavano arresti anomali.
* Correzione del bug in cui è necessario un callback HolographicSpace. CameraAdded per l'accettazione di un HolographicCamera e la visualizzazione come fotocamera aggiuntiva in HolographicFrame.

## <a name="version-2016-november-11-2019"></a>Versione 2.0.16 (11 novembre 2019)<a name="2.0.16"></a>
* Correzione di un deadlock nel rilevamento del codice QR.
* Correzione dell'eccezione unhandeld a causa dell'attesa del blocco nel thread principale.

## <a name="version-2014-october-26-2019"></a>Versione 2.0.14 (26 ottobre 2019)<a name="v2.0.14"></a>
* Supporto per le nuove API PerceptionDevice (aggiornamento di Windows 10 di novembre 2019).
* Correzione di un problema che impedisce l'attivazione degli eventi di movimento da SpatialGestureRecognizer.
* Correzione del problema di threading quando si utilizza SpatialSurfaceObserver. SetBoundingVolume.

## <a name="version-2012-october-18-2019"></a>Versione 2.0.12 (18 ottobre 2019)<a name="v2.0.12"></a>
* Correzione di un arresto anomalo in SpatialGestureRecognizer quando si utilizza NavigationRail (X/Y/Z).

## <a name="version-2010-october-10-2019"></a>Versione 2.0.10 (10 ottobre 2019)<a name="v2.0.10"></a>
* Correzione di un arresto anomalo quando si usa il pulsante trigger dei controller VR. La comunicazione remota olografica non supporta completamente i controller, ma solo il pulsante trigger e il pulsante Windows funzionano se abbinati a HoloLens 2.

## <a name="version-209-september-19-2019"></a>Versione 2.0.9 (19 settembre 2019)<a name="v2.0.9"></a>
* Aggiunta del supporto per [SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)
* Aggiunta ```IPlayerContext2``` di una nuova interfaccia (implementata da ```PlayerContext``` ) che fornisce i membri seguenti:
  - Proprietà [BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout) .
* Aggiunto ```Failed_RemoteFrameTooOld``` valore a```BlitResult```
* Miglioramenti alla stabilità e all'affidabilità

## <a name="version-208-august-20-2019"></a>Versione 2.0.8 (20 agosto 2019)<a name="v2.0.8"></a>

* Correzione di un arresto anomalo quando si chiama [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) con un [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) come parametro.
* Miglioramenti alla stabilità e all'affidabilità

## <a name="version-207-july-26-2019"></a>Versione 2.0.7 (26 luglio 2019)<a name="v2.0.7"></a>

* Prima versione pubblica della comunicazione remota olografica per HoloLens 2.

## <a name="see-also"></a>Vedere anche
* [Scrivere un'app lettore Holographic Remoting personalizzata](holographic-remoting-create-player.md)
* [Scrittura di un'app host di comunicazione remota olografica](holographic-remoting-create-host.md)
* [Limitazioni e risoluzione dei problemi di comunicazione remota olografica](holographic-remoting-troubleshooting.md)
* [Condizioni di licenza software per Holographic Remoting](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Informativa sulla privacy di Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)

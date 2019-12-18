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
# <a name="holographic-remoting-version-history"></a>Cronologia delle versioni remota olografica

> [!IMPORTANT]
> Queste linee guida sono specifiche per la comunicazione remota olografica in HoloLens 2.

## Versione 2.0.18.0 (17 dicembre 2019)<a name="v2.0.18"></a>
* Aggiunta del supporto per HolographicViewConfiguration: https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration
* Corretti vari bug che causavano arresti anomali.
* Correzione del bug in cui è necessario un callback HolographicSpace. CameraAdded per l'accettazione di un HolographicCamera e la visualizzazione come fotocamera aggiuntiva in HoloraphicFrame.

## Versione 2.0.16 (11 novembre 2019)<a name="2.0.16"></a>
* Correzione di un deadlock nel rilevamento del codice QR.
* Correzione dell'eccezione unhandeld a causa dell'attesa del blocco nel thread principale.

## Versione 2.0.14 (26 ottobre 2019)<a name="v2.0.14"></a>
* Supporto per le nuove API PerceptionDevice (aggiornamento di Windows 10 di novembre 2019).
* Correzione di un problema che impedisce l'attivazione degli eventi di movimento da SpatialGestureRecognizer.
* Correzione del problema di threading quando si utilizza SpatialSurfaceObserver. SetBoundingVolume.

## Versione 2.0.12 (18 ottobre 2019)<a name="v2.0.12"></a>
* Correzione di un arresto anomalo in SpatialGestureRecognizer quando si utilizza NavigationRail (X/Y/Z).

## Versione 2.0.10 (10 ottobre 2019)<a name="v2.0.10"></a>
* Correzione di un arresto anomalo quando si usa il pulsante trigger dei controller VR. La comunicazione remota olografica non supporta completamente i controller, ma solo il pulsante trigger e il pulsante Windows funzionano se abbinati a HoloLens 2.

## Versione 2.0.9 (19 settembre 2019)<a name="v2.0.9"></a>
* Aggiunta del supporto per [SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)
* Aggiunta di una nuova interfaccia ```IPlayerContext2``` (implementata da ```PlayerContext```) che fornisce i membri seguenti:
  - Proprietà [BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout) .
* Aggiunto ```Failed_RemoteFrameTooOld``` valore per ```BlitResult```
* Miglioramenti alla stabilità e all'affidabilità

## Versione 2.0.8 (20 agosto 2019)<a name="v2.0.8"></a>

* Correzione di un arresto anomalo quando si chiama [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) con un [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) come parametro.
* Miglioramenti alla stabilità e all'affidabilità

## Versione 2.0.7 (26 luglio 2019)<a name="v2.0.7"></a>

* Prima versione pubblica della comunicazione remota olografica per HoloLens 2.

## <a name="see-also"></a>Vedi anche
* [Scrittura di un'app lettore di comunicazione remota olografica personalizzata](holographic-remoting-create-player.md)
* [Scrittura di un'app host di comunicazione remota olografica](holographic-remoting-create-host.md)
* [Limitazioni e risoluzione dei problemi di comunicazione remota olografica](holographic-remoting-troubleshooting.md)
* [Condizioni di licenza software per Holographic Remoting](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Informativa sulla privacy di Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)

---
title: Con realtà mista di Windows mediante WebVR in Microsoft Edge
description: Panoramica dell'uso e lo sviluppo per WebVR in realtà mista di Windows
author: YashMaster
ms.author: yabahman
ms.date: 03/21/2018
ms.topic: article
keywords: WebVR, WebXR, WinMR, WebAR, vr web, web xr, web mr, web ar, 360, 360 video, 360 video, 360 foto, 360 foto, contenuto 360, web coinvolgenti, immersiveweb, IW
ms.openlocfilehash: fab17f4dcecc34d8f1ca4836dce6de90522899cd
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604639"
---
# <a name="using-webvr-in-microsoft-edge-with-windows-mixed-reality"></a>Con realtà mista di Windows mediante WebVR in Microsoft Edge

## <a name="creating-webvr-content-for-windows-mixed-reality-immersive-headsets"></a>Creazione di contenuto WebVR per realtà mista Windows auricolari coinvolgenti

WebVR 1.1 è disponibile in partire da Microsoft Edge di di Windows 10 Fall Creators Update. Gli sviluppatori possono ora usare questa API per creare esperienze VR immersive sul web.

L'API WebVR fornisce i dati di posa HMD alla pagina che può essere utilizzato per eseguire il rendering di un scena WebGL stereo al HMD. Dettagli sul supporto delle API è disponibile nel [pagina dello stato della piattaforma di Microsoft Edge](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/). L'area della superficie API WebVR è presente in tutte le volte all'interno di Microsoft Edge. Tuttavia, una chiamata a getVRDisplays() restituirà solo un auricolare se viene collegata le cuffie o il simulatore è stato attivato.

## <a name="viewing-webvr-content-in-windows-mixed-reality-immersive-headsets"></a>Visualizzazione di contenuto WebVR in auricolari coinvolgenti di realtà mista di Windows

Istruzioni per l'accesso ai contenuti WebVR il visore VR immersivi sono reperibile nella [Guida appassionato](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr).

## <a name="see-also"></a>Vedere anche
* [Informazioni WebVR](http://webvr.info)
* [Specifica WebVR](https://w3c.github.io/webvr/)
* [WebVR API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)
* [WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)
* [Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) e [estensioni su Gamepad](https://w3c.github.io/gamepad/extensions.html)
* [Gestione perdita contesto in WebGL](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [Pointerlock](http://www.w3.org/TR/pointerlock/)
* [glTF](https://www.khronos.org/gltf)
* [Usando Babylon. js per abilitare WebVR](https://docs.microsoft.com/windows/uwp/get-started/adding-webvr-to-a-babylonjs-game)


---
title: Uso di WebVR in Microsoft Edge con la realtà mista di Windows
description: Panoramica dell'uso e dello sviluppo per WebVR in realtà mista di Windows
author: YashMaster
ms.author: yabahman
ms.date: 03/21/2018
ms.topic: article
keywords: WebVR, WebXR, WinMR, WebAR, Web VR, Web XR, Web Mr, Web AR, 360, 360 video, 360 video, 360 Photo, 360 photos, 360 content, immersive Web, immersiveweb, IW
ms.openlocfilehash: fab17f4dcecc34d8f1ca4836dce6de90522899cd
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548767"
---
# <a name="using-webvr-in-microsoft-edge-with-windows-mixed-reality"></a>Uso di WebVR in Microsoft Edge con la realtà mista di Windows

## <a name="creating-webvr-content-for-windows-mixed-reality-immersive-headsets"></a>Creazione di contenuto WebVR per auricolari immersivi di Windows misto reality

WebVR 1,1 è disponibile in Microsoft Edge a partire da Windows 10 Fall Creators Update. Gli sviluppatori possono ora usare questa API per creare esperienze VR immersive sul Web.

L'API WebVR fornisce i dati di post HMD alla pagina, che possono essere usati per eseguire il rendering di una scena WebGL stereo in HMD. Informazioni dettagliate sul supporto delle API sono disponibili nella [pagina stato della piattaforma Microsoft Edge](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/). La superficie di attacco dell'API WebVR è sempre presente in Microsoft Edge. Tuttavia, una chiamata a getVRDisplays () restituirà solo una cuffia se una cuffia è collegata o se il simulatore è stato attivato.

## <a name="viewing-webvr-content-in-windows-mixed-reality-immersive-headsets"></a>Visualizzazione del contenuto di WebVR negli auricolari immersivi a realtà mista di Windows

Le istruzioni per l'accesso al contenuto di WebVR nell'auricolare immersivo sono disponibili nella [Guida per gli appassionati](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr).

## <a name="see-also"></a>Vedere anche
* [Informazioni WebVR](http://webvr.info)
* [Specifica WebVR](https://w3c.github.io/webvr/)
* [API WebVR](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)
* [API WebGL](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)
* Estensioni dell' [API gamepad](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) e del [Gamepad](https://w3c.github.io/gamepad/extensions.html)
* [Gestione del contesto perduto in WebGL](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [Pointerlock](http://www.w3.org/TR/pointerlock/)
* [glTF](https://www.khronos.org/gltf)
* [Uso di Babylon. js per abilitare WebVR](https://docs.microsoft.com/windows/uwp/get-started/adding-webvr-to-a-babylonjs-game)


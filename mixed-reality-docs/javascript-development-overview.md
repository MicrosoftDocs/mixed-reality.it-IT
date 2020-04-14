---
title: Panoramica dello sviluppo di realtà miste JavaScript
description: Panoramica dello sviluppo di realtà miste mediante JavaScript per auricolari Web, per dispositivi mobili e Windows immersivi.
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebXR, WinMR, WebAR, WebVR, WindowsMixedReality, HoloLens, realtà mista di Windows, Web VR, Web XR, Web Mr, Web AR, 360, 360 video, 360 video, 360 foto, 360 foto, 360 contenuto, immersive Web, immersive-Web, IW, immersiveweb
ms.openlocfilehash: 5756af9f48f4bb25477e75fb1f7c09e7239bdab9
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278482"
---
# <a name="mixed-reality-development-with-javascript-overview"></a>Panoramica dello sviluppo di realtà miste con JavaScript

## <a name="mixed-reality-applications-on-the-web"></a>Applicazioni di realtà mista sul Web

Le funzionalità della realtà mista sono disponibili sul Web mediante l'uso delle [API del dispositivo WebXR](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API) e [API WebVR deprecate] ([Panoramica di WebXR](webxr-overview.md). Per i browser che non supportano le funzionalità complete di WebXR, è possibile aggiungere [WebXR di riempimento](https://github.com/immersive-web/webxr-polyfill) al sito Web.

## <a name="what-is-webxr-polyfill"></a>Informazioni su WebXR Refill

Un'implementazione JavaScript dell'API per dispositivi WebXR, oltre al modulo WebXR Gamepad. Questo riempimento consente agli sviluppatori di scrivere in base alla specifica più recente, fornendo supporto per l'esecuzione su browser che implementano la specifica WebVR 1,1 o su dispositivi mobili senza supporto WebVR/WebXR.

## <a name="javascript-libraries-to-build-mixed-reality-applications-on-the-web"></a>Librerie JavaScript per creare applicazioni di realtà mista sul Web

## <a name="babylonjs"></a>Babylon. js

Babylon è un motore 3D JavaScript che rende più semplice lo sviluppo di contenuti 3D e applicazioni immersive. Prima di iniziare a usare le applicazioni immersive, si consiglia di apprendere le nozioni di base dello sviluppo di Babylon. js.

Informazioni su come creare un'applicazione di realtà mista con Babylon nella [sezione](https://doc.babylonjs.com/)introduttiva. Gioca con esempi 3D e il relativo codice sorgente usando [Babylon Playground](https://doc.babylonjs.com/examples/). Approfondimenti sullo sviluppo di realtà mista nella [sezione WebXR](https://doc.babylonjs.com/how_to/introduction_to_webxr) della documentazione. 

## <a name="a-frame"></a>A-frame

Un frame è un framework JavaScript dichiarativo per iniziare a usare la realtà virtuale sul Web. Per altre informazioni, vedere la [documentazione a-frame](https://aframe.io/) .

## <a name="threejs"></a>Tre. js

Three. js è una libreria 3D molto diffusa per la creazione di esperienze immersive. Per altre informazioni su [tre. js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene) , vedere la pagina della documentazione ed esplorare gli [esempi](https://threejs.org/examples/#webgl_animation_cloth).

## <a name="webgl"></a>WebGL

È possibile accedere direttamente alle API del dispositivo WebXR usando le API di WebGL. WebGL (Web Graphics Library) è un'API JavaScript per il rendering di grafica 3D e 2D ad alte prestazioni in qualsiasi Web browser compatibile senza l'uso di plug-in. altre informazioni sulle [API di WebGL](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API).

## <a name="mixed-reality-native-mobile-applications-using-javascript"></a>Applicazioni per dispositivi mobili native di realtà mista con JavaScript

Con l'ausilio di poche librerie JavaScript puoi scrivere una sola volta le tue esperienze di realtà miste e distribuirle nel Web e in piattaforme native come gli auricolari per la realtà mista di Windows, i dispositivi Android e iOS.

## <a name="babylon-native"></a>Nativo Babylon

La piattaforma [nativa di Babylon](https://www.babylonjs.com/native/) consente a chiunque di usare il codice Babylon. js e di compilare un'applicazione nativa con esso, sbloccando la potenza delle tecnologie native. È possibile scaricare [Babylon native su GitHub](https://github.com/BabylonJS/BabylonNative) e leggere altre informazioni sul [Blog di Babylon. js](https://medium.com/@babylonjs/babylon-native-821f1694fffc).

## <a name="react-native"></a>React Native

[React native](https://reactnative.dev/) è un'altra libreria open source che consente agli sviluppatori di compilare con JavaScript e distribuirla su più piattaforme. È possibile scaricare [React native su GitHub](https://github.com/facebook/react-native) e ottenere altre informazioni sul [Blog React native](https://reactnative.dev/blog/).

## <a name="see-also"></a>Vedi anche

* [Panoramica di WebXR](webxr-overview.md)
* [Specifica API del dispositivo WebXR](https://immersive-web.github.io/webxr/)
* [Documentazione dell'API del dispositivo WebXR](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [Immersiveweb. dev](https://immersiveweb.dev/)
* [Esempi di WebXR](https://immersive-web.github.io/webxr-samples/)
* [Uso di Babylon. js per creare esperienze WebXR](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [Realtà mista di Windows e la nuova Microsoft Edge](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [GitHub sul Web W3C immersivo](https://github.com/immersive-web)
* [API WebGL](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)
* Estensioni dell' [API gamepad](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) e del [Gamepad](https://w3c.github.io/gamepad/extensions.html)
* [Panoramica di WebVR](webvr-overview.md)

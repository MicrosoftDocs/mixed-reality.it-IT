---
title: Panoramica dello sviluppo di realtà miste JavaScript
description: Panoramica dello sviluppo di realtà miste mediante JavaScript per auricolari Web, per dispositivi mobili e Windows immersivi.
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebXR, WinMR, WebAR, WebVR, WindowsMixedReality, HoloLens, realtà mista di Windows, Web VR, Web XR, Web Mr, Web AR, 360, 360 video, 360 video, 360 foto, 360 foto, 360 contenuto, immersive Web, immersive-Web, IW, immersiveweb
ms.openlocfilehash: a1288e8f477f42b0937e797623fb83fe8f63685c
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "82835610"
---
# <a name="mixed-reality-development-with-javascript-overview"></a><span data-ttu-id="adcbd-104">Panoramica dello sviluppo di realtà miste con JavaScript</span><span class="sxs-lookup"><span data-stu-id="adcbd-104">Mixed Reality Development with JavaScript Overview</span></span>

## <a name="mixed-reality-applications-on-the-web"></a><span data-ttu-id="adcbd-105">Applicazioni di realtà mista sul Web</span><span class="sxs-lookup"><span data-stu-id="adcbd-105">Mixed Reality applications on the web</span></span>

<span data-ttu-id="adcbd-106">Le funzionalità di realtà mista sono disponibili sul Web mediante l'uso di [API del dispositivo WebXR](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API) e di [API WebVR deprecate](webxr-overview.md).</span><span class="sxs-lookup"><span data-stu-id="adcbd-106">Mixed Reality features are available on the web by the use of [WebXR Device APIs](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API) and [deprecated WebVR APIs](webxr-overview.md).</span></span> <span data-ttu-id="adcbd-107">Per i browser che non supportano le funzionalità complete di WebXR, è possibile aggiungere [WebXR di riempimento](https://github.com/immersive-web/webxr-polyfill) al sito Web.</span><span class="sxs-lookup"><span data-stu-id="adcbd-107">For browsers that do not support full WebXR features, you can add [WebXR Polyfills](https://github.com/immersive-web/webxr-polyfill) to your website.</span></span>

## <a name="what-is-webxr-polyfill"></a><span data-ttu-id="adcbd-108">Informazioni su WebXR Refill</span><span class="sxs-lookup"><span data-stu-id="adcbd-108">What is WebXR Polyfill</span></span>

<span data-ttu-id="adcbd-109">Un'implementazione JavaScript dell'API per dispositivi WebXR, oltre al modulo WebXR Gamepad.</span><span class="sxs-lookup"><span data-stu-id="adcbd-109">A JavaScript implementation of the WebXR Device API, as well as the WebXR Gamepad Module.</span></span> <span data-ttu-id="adcbd-110">Questo riempimento consente agli sviluppatori di scrivere in base alla specifica più recente, fornendo supporto per l'esecuzione su browser che implementano la specifica WebVR 1,1 o su dispositivi mobili senza supporto WebVR/WebXR.</span><span class="sxs-lookup"><span data-stu-id="adcbd-110">This polyfill allows developers to write against the latest specification, providing support when run on browsers that implement the WebVR 1.1 spec, or on mobile devices with no WebVR/WebXR support at all.</span></span>

## <a name="javascript-libraries-to-build-mixed-reality-applications-on-the-web"></a><span data-ttu-id="adcbd-111">Librerie JavaScript per creare applicazioni di realtà mista sul Web</span><span class="sxs-lookup"><span data-stu-id="adcbd-111">JavaScript libraries to build Mixed Reality applications on the web</span></span>

## <a name="babylonjs"></a><span data-ttu-id="adcbd-112">Babylon. js</span><span class="sxs-lookup"><span data-stu-id="adcbd-112">Babylon.js</span></span>

<span data-ttu-id="adcbd-113">Babylon è un motore 3D JavaScript che rende più semplice lo sviluppo di contenuti 3D e applicazioni immersive.</span><span class="sxs-lookup"><span data-stu-id="adcbd-113">Babylon is a JavaScript 3D engine that makes developing 3D content and immersive applications easy.</span></span> <span data-ttu-id="adcbd-114">Prima di iniziare a usare le applicazioni immersive, si consiglia di apprendere le nozioni di base dello sviluppo di Babylon. js.</span><span class="sxs-lookup"><span data-stu-id="adcbd-114">Before getting started with immersive applications, we recommend to learn the basics of Babylon.js development.</span></span>

<span data-ttu-id="adcbd-115">Informazioni su come creare un'applicazione di realtà mista con Babylon nella [sezione](https://doc.babylonjs.com/)introduttiva.</span><span class="sxs-lookup"><span data-stu-id="adcbd-115">Learn how to build a mixed reality application with Babylon in the [getting started section](https://doc.babylonjs.com/).</span></span> <span data-ttu-id="adcbd-116">Gioca con esempi 3D e il relativo codice sorgente usando [Babylon Playground](https://doc.babylonjs.com/examples/).</span><span class="sxs-lookup"><span data-stu-id="adcbd-116">Play with 3D examples and their source code using [Babylon Playground](https://doc.babylonjs.com/examples/).</span></span> <span data-ttu-id="adcbd-117">Approfondimenti sullo sviluppo di realtà mista nella [sezione WebXR](https://doc.babylonjs.com/how_to/introduction_to_webxr) della documentazione.</span><span class="sxs-lookup"><span data-stu-id="adcbd-117">Dive into mixed reality development on the [WebXR section](https://doc.babylonjs.com/how_to/introduction_to_webxr) of the documentation.</span></span> 

## <a name="a-frame"></a><span data-ttu-id="adcbd-118">A-frame</span><span class="sxs-lookup"><span data-stu-id="adcbd-118">A-Frame</span></span>

<span data-ttu-id="adcbd-119">Un frame è un framework JavaScript dichiarativo per iniziare a usare la realtà virtuale sul Web.</span><span class="sxs-lookup"><span data-stu-id="adcbd-119">A-frame is a declarative JavaScript framework to get started with Virtual Reality in the web.</span></span> <span data-ttu-id="adcbd-120">Per altre informazioni, vedere la [documentazione a-frame](https://aframe.io/) .</span><span class="sxs-lookup"><span data-stu-id="adcbd-120">Check out the [A-Frame documentation](https://aframe.io/) to learn more.</span></span>

## <a name="threejs"></a><span data-ttu-id="adcbd-121">Tre. js</span><span class="sxs-lookup"><span data-stu-id="adcbd-121">Three.js</span></span>

<span data-ttu-id="adcbd-122">Three. js è una libreria 3D molto diffusa per la creazione di esperienze immersive.</span><span class="sxs-lookup"><span data-stu-id="adcbd-122">Three.js is a popular 3D library for creating immersive experiences.</span></span> <span data-ttu-id="adcbd-123">Per altre informazioni su [tre. js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene) , vedere la pagina della documentazione ed esplorare gli [esempi](https://threejs.org/examples/#webgl_animation_cloth).</span><span class="sxs-lookup"><span data-stu-id="adcbd-123">Learn more about [three.js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene) in documentation page and by exploring [examples](https://threejs.org/examples/#webgl_animation_cloth).</span></span>

## <a name="webgl"></a><span data-ttu-id="adcbd-124">WebGL</span><span class="sxs-lookup"><span data-stu-id="adcbd-124">WebGL</span></span>

<span data-ttu-id="adcbd-125">È possibile accedere direttamente alle API del dispositivo WebXR usando le API di WebGL.</span><span class="sxs-lookup"><span data-stu-id="adcbd-125">You can access the WebXR Device APIs directly by using WebGL APIs.</span></span> <span data-ttu-id="adcbd-126">WebGL (Web Graphics Library) è un'API JavaScript per il rendering di grafica 3D e 2D ad alte prestazioni in qualsiasi Web browser compatibile senza l'uso di plug-in. altre informazioni sulle [API di WebGL](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API).</span><span class="sxs-lookup"><span data-stu-id="adcbd-126">WebGL (Web Graphics Library) is a JavaScript API for rendering high-performance interactive 3D and 2D graphics within any compatible web browser without the use of plug-ins. Learn more about the [WebGL APIs](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API).</span></span>

## <a name="mixed-reality-native-mobile-applications-using-javascript"></a><span data-ttu-id="adcbd-127">Applicazioni per dispositivi mobili native di realtà mista con JavaScript</span><span class="sxs-lookup"><span data-stu-id="adcbd-127">Mixed Reality native mobile applications using JavaScript</span></span>

<span data-ttu-id="adcbd-128">Con l'ausilio di poche librerie JavaScript puoi scrivere una sola volta le tue esperienze di realtà miste e distribuirle nel Web e in piattaforme native come gli auricolari per la realtà mista di Windows, i dispositivi Android e iOS.</span><span class="sxs-lookup"><span data-stu-id="adcbd-128">With the help of few JavaScript libraries you can write your mixed reality experiences once and deploy it to web and to native platforms like Windows Mixed Reality headsets, Android and iOS devices.</span></span>

## <a name="babylon-native"></a><span data-ttu-id="adcbd-129">Nativo Babylon</span><span class="sxs-lookup"><span data-stu-id="adcbd-129">Babylon Native</span></span>

<span data-ttu-id="adcbd-130">La piattaforma [nativa di Babylon](https://www.babylonjs.com/native/) consente a chiunque di usare il codice Babylon. js e di compilare un'applicazione nativa con esso, sbloccando la potenza delle tecnologie native.</span><span class="sxs-lookup"><span data-stu-id="adcbd-130">[Babylon Native](https://www.babylonjs.com/native/) platform allows anyone to take their Babylon.js code and build a native application with it, unlocking the power of native technologies.</span></span> <span data-ttu-id="adcbd-131">È possibile scaricare [Babylon native su GitHub](https://github.com/BabylonJS/BabylonNative) e leggere altre informazioni sul [Blog di Babylon. js](https://medium.com/@babylonjs/babylon-native-821f1694fffc).</span><span class="sxs-lookup"><span data-stu-id="adcbd-131">You can download [Babylon native on github](https://github.com/BabylonJS/BabylonNative) and read more about it on [Babylon.js blog](https://medium.com/@babylonjs/babylon-native-821f1694fffc).</span></span>

## <a name="react-native"></a><span data-ttu-id="adcbd-132">React Native</span><span class="sxs-lookup"><span data-stu-id="adcbd-132">React Native</span></span>

<span data-ttu-id="adcbd-133">[React native](https://reactnative.dev/) è un'altra libreria open source che consente agli sviluppatori di compilare con JavaScript e distribuirla su più piattaforme.</span><span class="sxs-lookup"><span data-stu-id="adcbd-133">[React Native](https://reactnative.dev/) is another open source library that allows developers to build using JavaScript and deploy to multiple platforms.</span></span> <span data-ttu-id="adcbd-134">È possibile scaricare [React native su GitHub](https://github.com/facebook/react-native) e ottenere altre informazioni sul [Blog React native](https://reactnative.dev/blog/).</span><span class="sxs-lookup"><span data-stu-id="adcbd-134">You can download [React Native on Github](https://github.com/facebook/react-native) and learn more about it in [React Native Blog](https://reactnative.dev/blog/).</span></span>

## <a name="see-also"></a><span data-ttu-id="adcbd-135">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="adcbd-135">See Also</span></span>

* [<span data-ttu-id="adcbd-136">Panoramica di WebXR</span><span class="sxs-lookup"><span data-stu-id="adcbd-136">WebXR Overview</span></span>](webxr-overview.md)
* [<span data-ttu-id="adcbd-137">Specifica API del dispositivo WebXR</span><span class="sxs-lookup"><span data-stu-id="adcbd-137">WebXR Device API specification</span></span>](https://immersive-web.github.io/webxr/)
* [<span data-ttu-id="adcbd-138">Documentazione dell'API del dispositivo WebXR</span><span class="sxs-lookup"><span data-stu-id="adcbd-138">WebXR Device API documentation</span></span>](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [<span data-ttu-id="adcbd-139">Immersiveweb. dev</span><span class="sxs-lookup"><span data-stu-id="adcbd-139">Immersiveweb.dev</span></span>](https://immersiveweb.dev/)
* [<span data-ttu-id="adcbd-140">Esempi di WebXR</span><span class="sxs-lookup"><span data-stu-id="adcbd-140">WebXR Samples</span></span>](https://immersive-web.github.io/webxr-samples/)
* [<span data-ttu-id="adcbd-141">Uso di Babylon. js per creare esperienze WebXR</span><span class="sxs-lookup"><span data-stu-id="adcbd-141">Using Babylon.js to create WebXR experiences</span></span>](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [<span data-ttu-id="adcbd-142">Realtà mista di Windows e la nuova Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="adcbd-142">Windows Mixed Reality and the new Microsoft Edge</span></span>](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [<span data-ttu-id="adcbd-143">GitHub sul Web W3C immersivo</span><span class="sxs-lookup"><span data-stu-id="adcbd-143">Immersive Web W3C Github</span></span>](https://github.com/immersive-web)
* <span data-ttu-id="adcbd-144">[API WebGL](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="adcbd-144">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span></span>
* <span data-ttu-id="adcbd-145">Estensioni dell' [API gamepad](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) e del [Gamepad](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="adcbd-145">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="adcbd-146">Panoramica di WebVR</span><span class="sxs-lookup"><span data-stu-id="adcbd-146">WebVR Overview</span></span>](webvr-overview.md)

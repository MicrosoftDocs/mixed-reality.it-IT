---
title: Uso di WebXR con la realtà mista di Windows
description: Panoramica dell'uso e dello sviluppo per WebXR in realtà mista di Windows
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebXR, WinMR, WebAR, WebVR, WindowsMixedReality, HoloLens, realtà mista di Windows, Web VR, Web XR, Web Mr, Web AR, 360, 360 video, 360 video, 360 foto, 360 foto, 360 contenuto, immersive Web, immersiveweb, IW
ms.openlocfilehash: 01e6cd44e9879cd7fd9b11e178134eaf364cc53c
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278442"
---
# <a name="webxr-overview"></a><span data-ttu-id="c699b-104">Panoramica di WebXR</span><span class="sxs-lookup"><span data-stu-id="c699b-104">WebXR Overview</span></span>

## <a name="what-is-webxr"></a><span data-ttu-id="c699b-105">Informazioni su WebXR</span><span class="sxs-lookup"><span data-stu-id="c699b-105">What is WebXR</span></span>

<span data-ttu-id="c699b-106">L' **API del dispositivo WebXR** consente di accedere ai dispositivi di **realtà virtuale (VR)** e **realtà aumentata (AR)** , inclusi i **sensori** e le **visualizzazioni montate** sul **Web**.</span><span class="sxs-lookup"><span data-stu-id="c699b-106">The **WebXR device API** is for accessing **virtual reality (VR)** and **augmented reality (AR)** devices, including **sensors** and **head-mounted displays** on the **Web**.</span></span> <span data-ttu-id="c699b-107">L'API del dispositivo WebXR è attualmente disponibile in Microsoft Edge e Chrome versione 79 e versioni successive supporta WebXR come valore predefinito.</span><span class="sxs-lookup"><span data-stu-id="c699b-107">WebXR device API is currently available on Microsoft Edge and Chrome version 79 and later versions supports WebXR as a default.</span></span> <span data-ttu-id="c699b-108">È possibile controllare lo stato del supporto del browser più recente per WebXR in [caniuse.com](https://caniuse.com/#search=webxr).</span><span class="sxs-lookup"><span data-stu-id="c699b-108">You can check the latest browser support status for WebXR at [caniuse.com](https://caniuse.com/#search=webxr).</span></span>

<span data-ttu-id="c699b-109">Scopri di più sulla [realtà mista di Windows e sul nuovo Microsoft Edge](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge) [nella sezione novità.](https://docs.microsoft.com/windows/mixed-reality/mrtk-porting-guide)</span><span class="sxs-lookup"><span data-stu-id="c699b-109">Learn more about the [Windows Mixed Reality and the new Microsoft Edge](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)in [What's new](https://docs.microsoft.com/windows/mixed-reality/mrtk-porting-guide) section.</span></span>

## <a name="viewing-webxr"></a><span data-ttu-id="c699b-110">Visualizzazione di WebXR</span><span class="sxs-lookup"><span data-stu-id="c699b-110">Viewing WebXR</span></span>

<span data-ttu-id="c699b-111">Per verificare se il browser supporta WebXR, è possibile passare agli [esempi di WebXR](https://immersive-web.github.io/webxr-samples/) nel browser.</span><span class="sxs-lookup"><span data-stu-id="c699b-111">To test if your browser supports WebXR, you can navigate to [WebXR Samples](https://immersive-web.github.io/webxr-samples/) in your browser.</span></span>

## <a name="see-also"></a><span data-ttu-id="c699b-112">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="c699b-112">See Also</span></span>

* [<span data-ttu-id="c699b-113">Specifica API del dispositivo WebXR</span><span class="sxs-lookup"><span data-stu-id="c699b-113">WebXR Device API specification</span></span>](https://immersive-web.github.io/webxr/)
* [<span data-ttu-id="c699b-114">Documentazione dell'API del dispositivo WebXR</span><span class="sxs-lookup"><span data-stu-id="c699b-114">WebXR Device API documentation</span></span>](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [<span data-ttu-id="c699b-115">Immersiveweb. dev</span><span class="sxs-lookup"><span data-stu-id="c699b-115">Immersiveweb.dev</span></span>](https://immersiveweb.dev/)
* [<span data-ttu-id="c699b-116">Esempi di WebXR</span><span class="sxs-lookup"><span data-stu-id="c699b-116">WebXR Samples</span></span>](https://immersive-web.github.io/webxr-samples/)
* [<span data-ttu-id="c699b-117">Realtà mista di Windows e la nuova Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="c699b-117">Windows Mixed Reality and the new Microsoft Edge</span></span>](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [<span data-ttu-id="c699b-118">GitHub sul Web W3C immersivo</span><span class="sxs-lookup"><span data-stu-id="c699b-118">Immersive Web W3C Github</span></span>](https://github.com/immersive-web)
* <span data-ttu-id="c699b-119">[API WebGL](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="c699b-119">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span></span>
* <span data-ttu-id="c699b-120">Estensioni dell' [API gamepad](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) e del [Gamepad](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="c699b-120">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="c699b-121">Gestione del contesto perduto in WebGL</span><span class="sxs-lookup"><span data-stu-id="c699b-121">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="c699b-122">Pointerlock</span><span class="sxs-lookup"><span data-stu-id="c699b-122">Pointerlock</span></span>](https://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="c699b-123">glTF</span><span class="sxs-lookup"><span data-stu-id="c699b-123">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="c699b-124">Uso di Babylon. js per creare esperienze WebXR</span><span class="sxs-lookup"><span data-stu-id="c699b-124">Using Babylon.js to create WebXR experiences</span></span>](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [<span data-ttu-id="c699b-125">Gruppo di community Web Immersive</span><span class="sxs-lookup"><span data-stu-id="c699b-125">Immersive web community group</span></span>](https://www.w3.org/community/immersive-web/)

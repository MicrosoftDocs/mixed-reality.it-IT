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
# <a name="using-webvr-in-microsoft-edge-with-windows-mixed-reality"></a><span data-ttu-id="fe1e8-104">Con realtà mista di Windows mediante WebVR in Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="fe1e8-104">Using WebVR in Microsoft Edge with Windows Mixed Reality</span></span>

## <a name="creating-webvr-content-for-windows-mixed-reality-immersive-headsets"></a><span data-ttu-id="fe1e8-105">Creazione di contenuto WebVR per realtà mista Windows auricolari coinvolgenti</span><span class="sxs-lookup"><span data-stu-id="fe1e8-105">Creating WebVR content for Windows Mixed reality immersive headsets</span></span>

<span data-ttu-id="fe1e8-106">WebVR 1.1 è disponibile in partire da Microsoft Edge di di Windows 10 Fall Creators Update.</span><span class="sxs-lookup"><span data-stu-id="fe1e8-106">WebVR 1.1 is available in Microsoft Edge beginning with the Windows 10 Fall Creators Update.</span></span> <span data-ttu-id="fe1e8-107">Gli sviluppatori possono ora usare questa API per creare esperienze VR immersive sul web.</span><span class="sxs-lookup"><span data-stu-id="fe1e8-107">Developers can now use this API to create immersive VR experiences on the web.</span></span>

<span data-ttu-id="fe1e8-108">L'API WebVR fornisce i dati di posa HMD alla pagina che può essere utilizzato per eseguire il rendering di un scena WebGL stereo al HMD.</span><span class="sxs-lookup"><span data-stu-id="fe1e8-108">The WebVR API provides HMD pose data to the page which can be used to render a stereo WebGL scene back to the HMD.</span></span> <span data-ttu-id="fe1e8-109">Dettagli sul supporto delle API è disponibile nel [pagina dello stato della piattaforma di Microsoft Edge](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/).</span><span class="sxs-lookup"><span data-stu-id="fe1e8-109">Details on API support is available on the [Microsoft Edge Platform Status page](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/).</span></span> <span data-ttu-id="fe1e8-110">L'area della superficie API WebVR è presente in tutte le volte all'interno di Microsoft Edge.</span><span class="sxs-lookup"><span data-stu-id="fe1e8-110">The WebVR API surface area is present at all times within Microsoft Edge.</span></span> <span data-ttu-id="fe1e8-111">Tuttavia, una chiamata a getVRDisplays() restituirà solo un auricolare se viene collegata le cuffie o il simulatore è stato attivato.</span><span class="sxs-lookup"><span data-stu-id="fe1e8-111">However, a call to getVRDisplays() will only return a headset if either a headset is plugged in or the simulator has been turned on.</span></span>

## <a name="viewing-webvr-content-in-windows-mixed-reality-immersive-headsets"></a><span data-ttu-id="fe1e8-112">Visualizzazione di contenuto WebVR in auricolari coinvolgenti di realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="fe1e8-112">Viewing WebVR content in Windows Mixed Reality immersive headsets</span></span>

<span data-ttu-id="fe1e8-113">Istruzioni per l'accesso ai contenuti WebVR il visore VR immersivi sono reperibile nella [Guida appassionato](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr).</span><span class="sxs-lookup"><span data-stu-id="fe1e8-113">Instructions for accessing WebVR content in your immersive headset can be found in the [Enthusiast's Guide](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr).</span></span>

## <a name="see-also"></a><span data-ttu-id="fe1e8-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="fe1e8-114">See Also</span></span>
* [<span data-ttu-id="fe1e8-115">Informazioni WebVR</span><span class="sxs-lookup"><span data-stu-id="fe1e8-115">WebVR information</span></span>](http://webvr.info)
* [<span data-ttu-id="fe1e8-116">Specifica WebVR</span><span class="sxs-lookup"><span data-stu-id="fe1e8-116">WebVR specification</span></span>](https://w3c.github.io/webvr/)
* <span data-ttu-id="fe1e8-117">[WebVR API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="fe1e8-117">[WebVR API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)</span></span>
* <span data-ttu-id="fe1e8-118">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="fe1e8-118">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span></span>
* <span data-ttu-id="fe1e8-119">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) e [estensioni su Gamepad](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="fe1e8-119">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="fe1e8-120">Gestione perdita contesto in WebGL</span><span class="sxs-lookup"><span data-stu-id="fe1e8-120">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="fe1e8-121">Pointerlock</span><span class="sxs-lookup"><span data-stu-id="fe1e8-121">Pointerlock</span></span>](http://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="fe1e8-122">glTF</span><span class="sxs-lookup"><span data-stu-id="fe1e8-122">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="fe1e8-123">Usando Babylon. js per abilitare WebVR</span><span class="sxs-lookup"><span data-stu-id="fe1e8-123">Using Babylon.js to enable WebVR</span></span>](https://docs.microsoft.com/windows/uwp/get-started/adding-webvr-to-a-babylonjs-game)


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
# <a name="using-webvr-in-microsoft-edge-with-windows-mixed-reality"></a><span data-ttu-id="dc140-104">Uso di WebVR in Microsoft Edge con la realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="dc140-104">Using WebVR in Microsoft Edge with Windows Mixed Reality</span></span>

## <a name="creating-webvr-content-for-windows-mixed-reality-immersive-headsets"></a><span data-ttu-id="dc140-105">Creazione di contenuto WebVR per auricolari immersivi di Windows misto reality</span><span class="sxs-lookup"><span data-stu-id="dc140-105">Creating WebVR content for Windows Mixed reality immersive headsets</span></span>

<span data-ttu-id="dc140-106">WebVR 1,1 è disponibile in Microsoft Edge a partire da Windows 10 Fall Creators Update.</span><span class="sxs-lookup"><span data-stu-id="dc140-106">WebVR 1.1 is available in Microsoft Edge beginning with the Windows 10 Fall Creators Update.</span></span> <span data-ttu-id="dc140-107">Gli sviluppatori possono ora usare questa API per creare esperienze VR immersive sul Web.</span><span class="sxs-lookup"><span data-stu-id="dc140-107">Developers can now use this API to create immersive VR experiences on the web.</span></span>

<span data-ttu-id="dc140-108">L'API WebVR fornisce i dati di post HMD alla pagina, che possono essere usati per eseguire il rendering di una scena WebGL stereo in HMD.</span><span class="sxs-lookup"><span data-stu-id="dc140-108">The WebVR API provides HMD pose data to the page which can be used to render a stereo WebGL scene back to the HMD.</span></span> <span data-ttu-id="dc140-109">Informazioni dettagliate sul supporto delle API sono disponibili nella [pagina stato della piattaforma Microsoft Edge](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/).</span><span class="sxs-lookup"><span data-stu-id="dc140-109">Details on API support is available on the [Microsoft Edge Platform Status page](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/).</span></span> <span data-ttu-id="dc140-110">La superficie di attacco dell'API WebVR è sempre presente in Microsoft Edge.</span><span class="sxs-lookup"><span data-stu-id="dc140-110">The WebVR API surface area is present at all times within Microsoft Edge.</span></span> <span data-ttu-id="dc140-111">Tuttavia, una chiamata a getVRDisplays () restituirà solo una cuffia se una cuffia è collegata o se il simulatore è stato attivato.</span><span class="sxs-lookup"><span data-stu-id="dc140-111">However, a call to getVRDisplays() will only return a headset if either a headset is plugged in or the simulator has been turned on.</span></span>

## <a name="viewing-webvr-content-in-windows-mixed-reality-immersive-headsets"></a><span data-ttu-id="dc140-112">Visualizzazione del contenuto di WebVR negli auricolari immersivi a realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="dc140-112">Viewing WebVR content in Windows Mixed Reality immersive headsets</span></span>

<span data-ttu-id="dc140-113">Le istruzioni per l'accesso al contenuto di WebVR nell'auricolare immersivo sono disponibili nella [Guida per gli appassionati](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr).</span><span class="sxs-lookup"><span data-stu-id="dc140-113">Instructions for accessing WebVR content in your immersive headset can be found in the [Enthusiast's Guide](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr).</span></span>

## <a name="see-also"></a><span data-ttu-id="dc140-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="dc140-114">See Also</span></span>
* [<span data-ttu-id="dc140-115">Informazioni WebVR</span><span class="sxs-lookup"><span data-stu-id="dc140-115">WebVR information</span></span>](http://webvr.info)
* [<span data-ttu-id="dc140-116">Specifica WebVR</span><span class="sxs-lookup"><span data-stu-id="dc140-116">WebVR specification</span></span>](https://w3c.github.io/webvr/)
* <span data-ttu-id="dc140-117">[API WebVR](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="dc140-117">[WebVR API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)</span></span>
* <span data-ttu-id="dc140-118">[API WebGL](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="dc140-118">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span></span>
* <span data-ttu-id="dc140-119">Estensioni dell' [API gamepad](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) e del [Gamepad](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="dc140-119">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="dc140-120">Gestione del contesto perduto in WebGL</span><span class="sxs-lookup"><span data-stu-id="dc140-120">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="dc140-121">Pointerlock</span><span class="sxs-lookup"><span data-stu-id="dc140-121">Pointerlock</span></span>](http://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="dc140-122">glTF</span><span class="sxs-lookup"><span data-stu-id="dc140-122">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="dc140-123">Uso di Babylon. js per abilitare WebVR</span><span class="sxs-lookup"><span data-stu-id="dc140-123">Using Babylon.js to enable WebVR</span></span>](https://docs.microsoft.com/windows/uwp/get-started/adding-webvr-to-a-babylonjs-game)


---
title: Oggetti nativi realtà misti Unity
description: Ottenere l'accesso agli oggetti nativi Holographic sottostanti in Unity.
author: vladkol
ms.author: vladkol
ms.date: 05/20/2018
ms.topic: article
keywords: Unity, mista realtà, nativo, xrdevice, spatialcoordinatesystem, holographicframe, holographiccamera, ispatialcoordinatesystem, iholographicframe, iholographiccamera, getnativeptr
ms.openlocfilehash: 76073f5b2adfdf27cfbb153f95bb3a533d02e196
ms.sourcegitcommit: d565a69a9320e736304372b3f010af1a4d286a62
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/20/2019
ms.locfileid: "65942097"
---
# <a name="mixed-reality-native-objects-in-unity"></a><span data-ttu-id="3bc2f-104">Oggetti nativi realtà misti Unity</span><span class="sxs-lookup"><span data-stu-id="3bc2f-104">Mixed Reality native objects in Unity</span></span>

<span data-ttu-id="3bc2f-105">[Ottenere un HolographicSpace](getting-a-holographicspace.md) è ciò che ogni app esegue prima di avviare la ricezione di dati della fotocamera e il rendering di realtà mista di fotogrammi.</span><span class="sxs-lookup"><span data-stu-id="3bc2f-105">[Getting a HolographicSpace](getting-a-holographicspace.md) is what every Mixed Reality app does before it starts receiving camera data and rendering frames.</span></span> <span data-ttu-id="3bc2f-106">In Unity, il motore si occupa di questi passaggi per l'utente, la gestione degli oggetti Holographic e aggiorna internamente come parte del relativo ciclo di rendering.</span><span class="sxs-lookup"><span data-stu-id="3bc2f-106">In Unity, the engine takes care of those steps for you, handling Holographic objects and updates internally as part of its render loop.</span></span>

<span data-ttu-id="3bc2f-107">Tuttavia, negli scenari avanzati potrebbe essere necessario ottenere l'accesso agli oggetti nativi sottostanti, ad esempio la <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> e correnti <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>.</span><span class="sxs-lookup"><span data-stu-id="3bc2f-107">However, in advanced scenarios you may need to get access to the underlying native objects, such as the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> and current <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>.</span></span> <span data-ttu-id="3bc2f-108"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine.XR.XRDevice</a> è ciò che fornisce accesso a questi oggetti nativi.</span><span class="sxs-lookup"><span data-stu-id="3bc2f-108"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine.XR.XRDevice</a> is what provides access to these native objects.</span></span>

## <a name="xrdevice"></a><span data-ttu-id="3bc2f-109">XRDevice</span><span class="sxs-lookup"><span data-stu-id="3bc2f-109">XRDevice</span></span> 

<span data-ttu-id="3bc2f-110">**Namespace:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="3bc2f-110">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="3bc2f-111">**Tipo:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="3bc2f-111">**Type:** *XRDevice*</span></span>

<span data-ttu-id="3bc2f-112">Il *XRDevice* tipo consente di ottenere l'accesso a oggetti nativi sottostanti usando la <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> (metodo).</span><span class="sxs-lookup"><span data-stu-id="3bc2f-112">The *XRDevice* type allows you to get access to underlying native objects using the <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> method.</span></span> <span data-ttu-id="3bc2f-113">Cosa restituisce GetNativePtr varia tra piattaforme diverse.</span><span class="sxs-lookup"><span data-stu-id="3bc2f-113">What GetNativePtr returns varies between different platforms.</span></span> <span data-ttu-id="3bc2f-114">In Universal Windows Platform, quando la destinazione SDK di XR realtà mista di Windows, XRDevice.GetNativePtr restituisce un puntatore (IntPtr) per la struttura seguente:</span><span class="sxs-lookup"><span data-stu-id="3bc2f-114">On the Universal Windows Platform, when targeting the Windows Mixed Reality XR SDK, XRDevice.GetNativePtr returns a pointer (IntPtr) to the following structure:</span></span> 

```cs
using System;
using System.Runtime.InteropServices;

[StructLayout(LayoutKind.Sequential)]
struct HolographicFrameNativeData
{
    public uint VersionNumber;
    public uint MaxNumberOfCameras;
    public IntPtr ISpatialCoordinateSystemPtr; // Windows::Perception::Spatial::ISpatialCoordinateSystem
    public IntPtr IHolographicFramePtr; // Windows::Graphics::Holographic::IHolographicFrame 
    public IntPtr IHolographicCameraPtr; // // Windows::Graphics::Holographic::IHolographicCamera
}
```
<span data-ttu-id="3bc2f-115">È possibile convertirla in HolographicFrameNativeData mediante Marshal. PtrToStructure causano metodo:</span><span class="sxs-lookup"><span data-stu-id="3bc2f-115">You can convert it to HolographicFrameNativeData using Marshal.PtrToStructure method:</span></span>
```cs
var nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```
<span data-ttu-id="3bc2f-116">***IHolographicCameraPtr** è una matrice di IntPtr sottoposto a marshalling come UnmanagedType. ByValArray con una lunghezza uguale a MaxNumberOfCameras*</span><span class="sxs-lookup"><span data-stu-id="3bc2f-116">***IHolographicCameraPtr** is an array of IntPtr marshaled as UnmanagedType.ByValArray with a length equal to MaxNumberOfCameras*</span></span> 


### <a name="using-holographicframenativedata"></a><span data-ttu-id="3bc2f-117">Usando HolographicFrameNativeData</span><span class="sxs-lookup"><span data-stu-id="3bc2f-117">Using HolographicFrameNativeData</span></span>

> [!NOTE]
> <span data-ttu-id="3bc2f-118">La modifica dello stato degli oggetti nativi ricevuti tramite HolographicFrameNativeData può causare un comportamento imprevedibile ed elementi di rendering, in particolare se Unity anche consenta di valutare tale stato.</span><span class="sxs-lookup"><span data-stu-id="3bc2f-118">Changing the state of the native objects received via HolographicFrameNativeData may cause unpredictable behaviour and rendering artifacts, especially if Unity also reasons about that same state.</span></span>  <span data-ttu-id="3bc2f-119">Ad esempio, non è necessario chiamare HolographicFrame.UpdateCurrentPrediction oppure sarà sincronizzata con la posa che prevede Windows, che consentiranno di ridurre la stima posa che esegue il rendering di Unity con quel frame [stabilità ologrammi](hologram-stability.md).</span><span class="sxs-lookup"><span data-stu-id="3bc2f-119">For example, you should not call HolographicFrame.UpdateCurrentPrediction, or else the pose prediction that Unity renders with that frame will be out of sync with the pose that Windows is expecting, which will reduce [hologram stability](hologram-stability.md).</span></span>

<span data-ttu-id="3bc2f-120">È possibile usare i dati da HolographicFrameNativeData quando è necessario per eseguire il rendering e debug, nel plug-in nativa l'accesso alle interfacce native o C# codice.</span><span class="sxs-lookup"><span data-stu-id="3bc2f-120">You can use data from HolographicFrameNativeData when access to native interfaces is required for rendering or debugging purposes, in your native plugins or C# code.</span></span> 

<span data-ttu-id="3bc2f-121">Di seguito è riportato un esempio di come è possibile utilizzare HolographicFrameNativeData per ottenere una stima del frame corrente per ora photon.</span><span class="sxs-lookup"><span data-stu-id="3bc2f-121">Here is an example of how you can use HolographicFrameNativeData to get the current frame's prediction for photon time.</span></span> 
```cs
using System;
using System.Runtime.InteropServices;

public static bool GetCurrentFrameDateTime(out DateTime frameDateTime)
{
#if (!UNITY_EDITOR && UNITY_WSA) || ENABLE_WINMD_SUPPORT
    IntPtr nativeStruct = UnityEngine.XR.XRDevice.GetNativePtr();

    if (nativeStruct != IntPtr.Zero)
    {
        HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativeStruct);

        if (hfd.IHolographicFramePtr != IntPtr.Zero)
        {
            var holographicFrame = (Windows.Graphics.Holographic.HolographicFrame)Marshal.GetObjectForIUnknown(hfd.IHolographicFramePtr);
            frameDateTime = holographicFrame.CurrentPrediction.Timestamp.TargetTime.DateTime;
            return true;
        }
    }

#endif

    frameDateTime = DateTime.MinValue;
    return false;
}

```

## <a name="see-also"></a><span data-ttu-id="3bc2f-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3bc2f-122">See Also</span></span>
* <span data-ttu-id="3bc2f-123"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span><span class="sxs-lookup"><span data-stu-id="3bc2f-123"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span></span>
* <span data-ttu-id="3bc2f-124"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span><span class="sxs-lookup"><span data-stu-id="3bc2f-124"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span></span>
* <span data-ttu-id="3bc2f-125"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span><span class="sxs-lookup"><span data-stu-id="3bc2f-125"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span></span>
* [<span data-ttu-id="3bc2f-126">Rendering in DirectX</span><span class="sxs-lookup"><span data-stu-id="3bc2f-126">Rendering in DirectX</span></span>](rendering-in-directx.md)

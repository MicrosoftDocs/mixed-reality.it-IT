---
title: Oggetti nativi della realtà mista in Unity
description: Ottenere l'accesso agli oggetti nativi olografici sottostanti in Unity.
author: vladkol
ms.author: vladkol
ms.date: 05/20/2018
ms.topic: article
keywords: Unity, realtà mista, nativa, xrdevice, spatialcoordinatesystem, holographicframe, holographiccamera, ispatialcoordinatesystem, iholographicframe, iholographiccamera, getnativeptr
ms.openlocfilehash: 76073f5b2adfdf27cfbb153f95bb3a533d02e196
ms.sourcegitcommit: d565a69a9320e736304372b3f010af1a4d286a62
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/20/2019
ms.locfileid: "65942097"
---
# <a name="mixed-reality-native-objects-in-unity"></a><span data-ttu-id="989a0-104">Oggetti nativi della realtà mista in Unity</span><span class="sxs-lookup"><span data-stu-id="989a0-104">Mixed Reality native objects in Unity</span></span>

<span data-ttu-id="989a0-105">[Ottenere un HolographicSpace](getting-a-holographicspace.md) è il risultato di ogni app di realtà mista prima che inizi a ricevere i dati della fotocamera e i frame di rendering.</span><span class="sxs-lookup"><span data-stu-id="989a0-105">[Getting a HolographicSpace](getting-a-holographicspace.md) is what every Mixed Reality app does before it starts receiving camera data and rendering frames.</span></span> <span data-ttu-id="989a0-106">In Unity, il motore gestisce automaticamente questi passaggi, gestendo gli oggetti olografici e gli aggiornamenti internamente come parte del relativo ciclo di rendering.</span><span class="sxs-lookup"><span data-stu-id="989a0-106">In Unity, the engine takes care of those steps for you, handling Holographic objects and updates internally as part of its render loop.</span></span>

<span data-ttu-id="989a0-107">Negli scenari avanzati potrebbe tuttavia essere necessario ottenere l'accesso agli oggetti nativi sottostanti, ad esempio <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> e <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>corrente.</span><span class="sxs-lookup"><span data-stu-id="989a0-107">However, in advanced scenarios you may need to get access to the underlying native objects, such as the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> and current <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>.</span></span> <span data-ttu-id="989a0-108"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine. XR. XRDevice</a> fornisce l'accesso a questi oggetti nativi.</span><span class="sxs-lookup"><span data-stu-id="989a0-108"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine.XR.XRDevice</a> is what provides access to these native objects.</span></span>

## <a name="xrdevice"></a><span data-ttu-id="989a0-109">XRDevice</span><span class="sxs-lookup"><span data-stu-id="989a0-109">XRDevice</span></span> 

<span data-ttu-id="989a0-110">**Namespace** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="989a0-110">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="989a0-111">**Tipo** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="989a0-111">**Type:** *XRDevice*</span></span>

<span data-ttu-id="989a0-112">Il tipo *XRDevice* consente di ottenere l'accesso agli oggetti nativi sottostanti usando il metodo <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> .</span><span class="sxs-lookup"><span data-stu-id="989a0-112">The *XRDevice* type allows you to get access to underlying native objects using the <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> method.</span></span> <span data-ttu-id="989a0-113">Il risultato restituito da GetNativePtr varia in base alle diverse piattaforme.</span><span class="sxs-lookup"><span data-stu-id="989a0-113">What GetNativePtr returns varies between different platforms.</span></span> <span data-ttu-id="989a0-114">Nel piattaforma UWP (Universal Windows Platform), quando la destinazione è Windows Mixed Reality XR SDK, XRDevice. GetNativePtr restituisce un puntatore (IntPtr) alla struttura seguente:</span><span class="sxs-lookup"><span data-stu-id="989a0-114">On the Universal Windows Platform, when targeting the Windows Mixed Reality XR SDK, XRDevice.GetNativePtr returns a pointer (IntPtr) to the following structure:</span></span> 

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
<span data-ttu-id="989a0-115">È possibile convertirlo in HolographicFrameNativeData usando il metodo Marshal. PtrToStructure:</span><span class="sxs-lookup"><span data-stu-id="989a0-115">You can convert it to HolographicFrameNativeData using Marshal.PtrToStructure method:</span></span>
```cs
var nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```
<span data-ttu-id="989a0-116">***IHolographicCameraPtr** è una matrice di IntPtr sottoposta a marshalling come UnmanagedType. ByValArray con una lunghezza uguale a MaxNumberOfCameras*</span><span class="sxs-lookup"><span data-stu-id="989a0-116">***IHolographicCameraPtr** is an array of IntPtr marshaled as UnmanagedType.ByValArray with a length equal to MaxNumberOfCameras*</span></span> 


### <a name="using-holographicframenativedata"></a><span data-ttu-id="989a0-117">Uso di HolographicFrameNativeData</span><span class="sxs-lookup"><span data-stu-id="989a0-117">Using HolographicFrameNativeData</span></span>

> [!NOTE]
> <span data-ttu-id="989a0-118">La modifica dello stato degli oggetti nativi ricevuti tramite HolographicFrameNativeData può causare un comportamento imprevedibile e gli artefatti di rendering, soprattutto se Unity ne causa anche lo stesso stato.</span><span class="sxs-lookup"><span data-stu-id="989a0-118">Changing the state of the native objects received via HolographicFrameNativeData may cause unpredictable behaviour and rendering artifacts, especially if Unity also reasons about that same state.</span></span>  <span data-ttu-id="989a0-119">Ad esempio, non è necessario chiamare HolographicFrame. UpdateCurrentPrediction. in caso contrario, la stima di pose che Unity esegue il rendering con tale frame non sarà sincronizzata con la funzione prevista da Windows, riducendo la [stabilità](hologram-stability.md)dell'ologramma.</span><span class="sxs-lookup"><span data-stu-id="989a0-119">For example, you should not call HolographicFrame.UpdateCurrentPrediction, or else the pose prediction that Unity renders with that frame will be out of sync with the pose that Windows is expecting, which will reduce [hologram stability](hologram-stability.md).</span></span>

<span data-ttu-id="989a0-120">È possibile usare i dati di HolographicFrameNativeData quando l'accesso alle interfacce native è necessario a scopo di rendering o debug, nei plug C# -in nativi o nel codice.</span><span class="sxs-lookup"><span data-stu-id="989a0-120">You can use data from HolographicFrameNativeData when access to native interfaces is required for rendering or debugging purposes, in your native plugins or C# code.</span></span> 

<span data-ttu-id="989a0-121">Di seguito è riportato un esempio di come è possibile usare HolographicFrameNativeData per ottenere la stima del frame corrente per il tempo del fotone.</span><span class="sxs-lookup"><span data-stu-id="989a0-121">Here is an example of how you can use HolographicFrameNativeData to get the current frame's prediction for photon time.</span></span> 
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

## <a name="see-also"></a><span data-ttu-id="989a0-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="989a0-122">See Also</span></span>
* <span data-ttu-id="989a0-123"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span><span class="sxs-lookup"><span data-stu-id="989a0-123"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span></span>
* <span data-ttu-id="989a0-124"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span><span class="sxs-lookup"><span data-stu-id="989a0-124"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span></span>
* <span data-ttu-id="989a0-125"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span><span class="sxs-lookup"><span data-stu-id="989a0-125"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span></span>
* [<span data-ttu-id="989a0-126">Rendering in DirectX</span><span class="sxs-lookup"><span data-stu-id="989a0-126">Rendering in DirectX</span></span>](rendering-in-directx.md)

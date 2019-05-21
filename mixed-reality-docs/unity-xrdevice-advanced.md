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
# <a name="mixed-reality-native-objects-in-unity"></a>Oggetti nativi realtà misti Unity

[Ottenere un HolographicSpace](getting-a-holographicspace.md) è ciò che ogni app esegue prima di avviare la ricezione di dati della fotocamera e il rendering di realtà mista di fotogrammi. In Unity, il motore si occupa di questi passaggi per l'utente, la gestione degli oggetti Holographic e aggiorna internamente come parte del relativo ciclo di rendering.

Tuttavia, negli scenari avanzati potrebbe essere necessario ottenere l'accesso agli oggetti nativi sottostanti, ad esempio la <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> e correnti <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>. <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine.XR.XRDevice</a> è ciò che fornisce accesso a questi oggetti nativi.

## <a name="xrdevice"></a>XRDevice 

**Namespace:** *UnityEngine.XR*<br>
**Tipo:** *XRDevice*

Il *XRDevice* tipo consente di ottenere l'accesso a oggetti nativi sottostanti usando la <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> (metodo). Cosa restituisce GetNativePtr varia tra piattaforme diverse. In Universal Windows Platform, quando la destinazione SDK di XR realtà mista di Windows, XRDevice.GetNativePtr restituisce un puntatore (IntPtr) per la struttura seguente: 

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
È possibile convertirla in HolographicFrameNativeData mediante Marshal. PtrToStructure causano metodo:
```cs
var nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```
***IHolographicCameraPtr** è una matrice di IntPtr sottoposto a marshalling come UnmanagedType. ByValArray con una lunghezza uguale a MaxNumberOfCameras* 


### <a name="using-holographicframenativedata"></a>Usando HolographicFrameNativeData

> [!NOTE]
> La modifica dello stato degli oggetti nativi ricevuti tramite HolographicFrameNativeData può causare un comportamento imprevedibile ed elementi di rendering, in particolare se Unity anche consenta di valutare tale stato.  Ad esempio, non è necessario chiamare HolographicFrame.UpdateCurrentPrediction oppure sarà sincronizzata con la posa che prevede Windows, che consentiranno di ridurre la stima posa che esegue il rendering di Unity con quel frame [stabilità ologrammi](hologram-stability.md).

È possibile usare i dati da HolographicFrameNativeData quando è necessario per eseguire il rendering e debug, nel plug-in nativa l'accesso alle interfacce native o C# codice. 

Di seguito è riportato un esempio di come è possibile utilizzare HolographicFrameNativeData per ottenere una stima del frame corrente per ora photon. 
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

## <a name="see-also"></a>Vedere anche
* <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a>
* [Rendering in DirectX](rendering-in-directx.md)

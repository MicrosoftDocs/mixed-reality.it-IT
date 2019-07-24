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
# <a name="mixed-reality-native-objects-in-unity"></a>Oggetti nativi della realtà mista in Unity

[Ottenere un HolographicSpace](getting-a-holographicspace.md) è il risultato di ogni app di realtà mista prima che inizi a ricevere i dati della fotocamera e i frame di rendering. In Unity, il motore gestisce automaticamente questi passaggi, gestendo gli oggetti olografici e gli aggiornamenti internamente come parte del relativo ciclo di rendering.

Negli scenari avanzati potrebbe tuttavia essere necessario ottenere l'accesso agli oggetti nativi sottostanti, ad esempio <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> e <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>corrente. <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine. XR. XRDevice</a> fornisce l'accesso a questi oggetti nativi.

## <a name="xrdevice"></a>XRDevice 

**Namespace** *UnityEngine. XR*<br>
**Tipo** *XRDevice*

Il tipo *XRDevice* consente di ottenere l'accesso agli oggetti nativi sottostanti usando il metodo <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> . Il risultato restituito da GetNativePtr varia in base alle diverse piattaforme. Nel piattaforma UWP (Universal Windows Platform), quando la destinazione è Windows Mixed Reality XR SDK, XRDevice. GetNativePtr restituisce un puntatore (IntPtr) alla struttura seguente: 

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
È possibile convertirlo in HolographicFrameNativeData usando il metodo Marshal. PtrToStructure:
```cs
var nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```
***IHolographicCameraPtr** è una matrice di IntPtr sottoposta a marshalling come UnmanagedType. ByValArray con una lunghezza uguale a MaxNumberOfCameras* 


### <a name="using-holographicframenativedata"></a>Uso di HolographicFrameNativeData

> [!NOTE]
> La modifica dello stato degli oggetti nativi ricevuti tramite HolographicFrameNativeData può causare un comportamento imprevedibile e gli artefatti di rendering, soprattutto se Unity ne causa anche lo stesso stato.  Ad esempio, non è necessario chiamare HolographicFrame. UpdateCurrentPrediction. in caso contrario, la stima di pose che Unity esegue il rendering con tale frame non sarà sincronizzata con la funzione prevista da Windows, riducendo la [stabilità](hologram-stability.md)dell'ologramma.

È possibile usare i dati di HolographicFrameNativeData quando l'accesso alle interfacce native è necessario a scopo di rendering o debug, nei plug C# -in nativi o nel codice. 

Di seguito è riportato un esempio di come è possibile usare HolographicFrameNativeData per ottenere la stima del frame corrente per il tempo del fotone. 
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

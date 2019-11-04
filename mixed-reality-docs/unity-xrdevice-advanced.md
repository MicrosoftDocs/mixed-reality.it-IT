---
title: Oggetti nativi della realtà mista in Unity
description: Ottenere l'accesso agli oggetti nativi olografici sottostanti in Unity.
author: vladkol
ms.author: vladkol
ms.date: 05/20/2018
ms.topic: article
keywords: Unity, realtà mista, nativa, xrdevice, spatialcoordinatesystem, holographicframe, holographiccamera, ispatialcoordinatesystem, iholographicframe, iholographiccamera, getnativeptr
ms.openlocfilehash: 975775f64a19fe5fff4bc395a3e954cbf529dfa9
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437341"
---
# <a name="mixed-reality-native-objects-in-unity"></a>Oggetti nativi della realtà mista in Unity

[Ottenere un HolographicSpace](getting-a-holographicspace.md) è il risultato di ogni app di realtà mista prima che inizi a ricevere i dati della fotocamera e i frame di rendering. In Unity, il motore gestisce automaticamente questi passaggi, gestendo gli oggetti olografici e gli aggiornamenti internamente come parte del relativo ciclo di rendering.

Negli scenari avanzati potrebbe tuttavia essere necessario ottenere l'accesso agli oggetti nativi sottostanti, ad esempio <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> e <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>corrente. <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine. XR. XRDevice</a> fornisce l'accesso a questi oggetti nativi.

## <a name="xrdevice"></a>XRDevice 

**Spazio dei nomi:** *UnityEngine. XR*<br>
**Tipo:** *XRDevice*

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

### <a name="unmarshaling-native-pointers"></a>Unmarshalling di puntatori nativi

Se si usa [Microsoft. Windows. MixedReality. DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) è possibile costruire un oggetto gestito da un puntatore nativo usando il metodo `FromNativePtr()`:

```cs
var worldOrigin = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(hfd.ISpatialCoordinateSystemPtr);
```

In caso contrario, usare `Marshal.GetObjectForIUnknown()` ed eseguire il cast al tipo desiderato:

```cs
#if ENABLE_WINMD_SUPPORT
var worldOrigin = (Windows.Perception.Spatial.SpatialCoordinateSystem)Marshal.GetObjectForIUnknown(hfd.ISpatialCoordinateSystemPtr);
#endif
```

### <a name="converting-between-coordinate-systems"></a>Conversione tra sistemi di coordinate

Unity usa un sistema di coordinate di sinistra, mentre le API di percezione di Windows usano sistemi di coordinate di destra. Per eseguire la conversione tra queste due convenzioni, è possibile usare gli helper seguenti:

```cs
namespace NumericsConversion
{
    public static class NumericsConversionExtensions
    {
        public static UnityEngine.Vector3 ToUnity(this System.Numerics.Vector3 v) => new UnityEngine.Vector3(v.X, v.Y, -v.Z);
        public static UnityEngine.Quaternion ToUnity(this System.Numerics.Quaternion q) => new UnityEngine.Quaternion(-q.X, -q.Y, q.Z, q.W);
        public static UnityEngine.Matrix4x4 ToUnity(this System.Numerics.Matrix4x4 m) => new UnityEngine.Matrix4x4(
            new Vector4( m.M11,  m.M12, -m.M13,  m.M14),
            new Vector4( m.M21,  m.M22, -m.M23,  m.M24),
            new Vector4(-m.M31, -m.M32,  m.M33, -m.M34),
            new Vector4( m.M41,  m.M42, -m.M43,  m.M44));

        public static System.Numerics.Vector3 ToSystem(this UnityEngine.Vector3 v) => new System.Numerics.Vector3(v.x, v.y, -v.z);
        public static System.Numerics.Quaternion ToSystem(this UnityEngine.Quaternion q) => new System.Numerics.Quaternion(-q.x, -q.y, q.z, q.w);
        public static System.Numerics.Matrix4x4 ToSystem(this UnityEngine.Matrix4x4 m) => new System.Numerics.Matrix4x4(
            m.m00,  m.m10, -m.m20,  m.m30,
            m.m01,  m.m11, -m.m21,  m.m31,
           -m.m02, -m.m12,  m.m22, -m.m32,
            m.m03,  m.m13, -m.m23,  m.m33);
    }
}
```

### <a name="using-holographicframe-native-data"></a>Uso di dati nativi HolographicFrame

> [!NOTE]
> La modifica dello stato degli oggetti nativi ricevuti tramite HolographicFrameNativeData può causare un comportamento imprevedibile e gli artefatti di rendering, soprattutto se Unity ne causa anche lo stesso stato.  Ad esempio, non è necessario chiamare HolographicFrame. UpdateCurrentPrediction. in caso contrario, la stima di pose che Unity esegue il rendering con tale frame non sarà sincronizzata con la funzione prevista da Windows, riducendo la [stabilità dell'ologramma](hologram-stability.md).

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

## <a name="see-also"></a>Vedi anche
* [Uso dello spazio dei nomi Windows con le app Unity per HoloLens](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a>
* [Rendering in DirectX](rendering-in-directx.md)

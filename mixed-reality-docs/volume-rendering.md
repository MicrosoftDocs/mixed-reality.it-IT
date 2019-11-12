---
title: Rendering del volume
description: Le immagini volumetriche contengono informazioni dettagliate con opacità e colore in tutto il volume che non possono essere facilmente espresse come superfici. Informazioni su come eseguire il rendering efficiente di immagini volumetriche in realtà mista di Windows.
author: KevinKennedy
ms.author: kkennedy
ms.date: 03/21/2018
ms.topic: article
keywords: immagine volumetrica, rendering del volume, prestazioni, realtà mista
ms.openlocfilehash: 1b3ec59adf4f6449ed3f12d7f98f329c4e963ea5
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926675"
---
# <a name="volume-rendering"></a>Rendering del volume

Per i volumi di ingegneria o MRI medici, vedere [rendering del volume in Wikipedia](https://en.wikipedia.org/wiki/Volume_rendering). Queste immagini volumetriche contengono informazioni dettagliate con opacità e colore in tutto il volume che non possono essere facilmente espresse come superfici come le [mesh poligonali](https://en.wikipedia.org/wiki/Polygon_mesh).

Soluzioni principali per migliorare le prestazioni
1. ERRATO: approccio ingenuo: Mostra volume intero, in genere troppo lento
2. BENE: piano di taglio: Mostra solo una singola sezione del volume
3. BENE: riduzione del volume secondario: Mostra solo pochi livelli del volume
4. BENE: abbassare la risoluzione del rendering del volume (vedere il rendering di una scena di risoluzione mista)

Esiste solo una certa quantità di informazioni che possono essere trasferite dall'applicazione sullo schermo in un particolare frame, ovvero la larghezza di banda totale della memoria. Anche qualsiasi elaborazione (o ' ombreggiatura ') necessaria per trasformare i dati per la presentazione richiede anche tempo. Le considerazioni principali per il rendering del volume sono le seguenti:
* Screen-width * screen-height * screen-count * volume-layers-on-that-pixel = Total-volume-Samples-per-frame
* 1028 * 720 * 2 * 256 = 378961920 (100%) (volume res completo: troppi esempi)
* 1028 * 720 * 2 * 1 = 1480320 (0,3% of Full) (slice sottile: 1 campione per pixel, esecuzione senza problemi)
* 1028 * 720 * 2 * 10 = 14803200 (3,9% della versione completa) (sezione del volume secondario: 10 campioni per pixel, esecuzione abbastanza agevole, aspetto 3D)
* 200 * 200 * 2 * 256 = 20480000 (5% di pieno) (volume res inferiore: un minor numero di pixel, un volume intero, appare 3D ma un bit sfocato)

## <a name="representing-3d-textures"></a>Rappresentazione di trame 3D

Sulla CPU:

```
public struct Int3 { public int X, Y, Z; /* ... */ }
 public class VolumeHeader  {
   public readonly Int3 Size;
   public VolumeHeader(Int3 size) { this.Size = size;  }
   public int CubicToLinearIndex(Int3 index) {
     return index.X + (index.Y * (Size.X)) + (index.Z * (Size.X * Size.Y));
   }
   public Int3 LinearToCubicIndex(int linearIndex)
   {
     return new Int3((linearIndex / 1) % Size.X,
       (linearIndex / Size.X) % Size.Y,
       (linearIndex / (Size.X * Size.Y)) % Size.Z);
   }
   /* ... */
 }
 public class VolumeBuffer<T> {
   public readonly VolumeHeader Header;
   public readonly T[] DataArray;
   public T GetVoxel(Int3 pos)        {
     return this.DataArray[this.Header.CubicToLinearIndex(pos)];
   }
   public void SetVoxel(Int3 pos, T val)        {
     this.DataArray[this.Header.CubicToLinearIndex(pos)] = val;
   }
   public T this[Int3 pos] {
     get { return this.GetVoxel(pos); }
     set { this.SetVoxel(pos, value); }
   }
   /* ... */
 }
```

Sulla GPU:

```
float3 _VolBufferSize;
 int3 UnitVolumeToIntVolume(float3 coord) {
   return (int3)( coord * _VolBufferSize.xyz );
 }
 int IntVolumeToLinearIndex(int3 coord, int3 size) {
   return coord.x + ( coord.y * size.x ) + ( coord.z * ( size.x * size.y ) );
 }
 uniform StructuredBuffer<float> _VolBuffer;
 float SampleVol(float3 coord3 ) {
   int3 intIndex3 = UnitVolumeToIntVolume( coord3 );
   int index1D = IntVolumeToLinearIndex( intIndex3, _VolBufferSize.xyz);
   return __VolBuffer[index1D];
 }
```

## <a name="shading-and-gradients"></a>Ombreggiatura e sfumature

Come ombreggiare un volume, ad esempio MRI, per una visualizzazione utile. Il metodo principale consiste nel disporre di una "finestra intensità" (un valore minimo e massimo) in cui si desidera visualizzare le intensità e semplicemente ridimensionare lo spazio per visualizzare l'intensità del nero e del bianco. È quindi possibile applicare una "rampa di colore" ai valori all'interno di tale intervallo e archiviarli come trama, in modo che le diverse parti dello spettro di intensità possano ombreggiare colori diversi:

```
float4 ShadeVol( float intensity ) {
   float unitIntensity = saturate( intensity - IntensityMin / ( IntensityMax - IntensityMin ) );
   // Simple two point black and white intensity:
   color.rgba = unitIntensity;
   // Color ramp method:
   color.rgba = tex2d( ColorRampTexture, float2( unitIntensity, 0 ) );
```

In molte applicazioni archiviate nel volume sia un valore di intensità RAW che un "indice di segmentazione" (per segmentare parti diverse, ad esempio Skin e Bone, questi segmenti vengono in genere creati dagli esperti in strumenti dedicati). Questa operazione può essere combinata con l'approccio precedente per inserire un colore diverso o persino una rampa di colore diversa per ogni indice di segmento:

```
// Change color to match segment index (fade each segment towards black):
 color.rgb = SegmentColors[ segment_index ] * color.a; // brighter alpha gives brighter color
```

## <a name="volume-slicing-in-a-shader"></a>Sezionamento del volume in uno shader

Il primo passaggio consiste nel creare un "piano di sezionamento" che può spostarsi tra il volume, "sezionamento" e come i valori di analisi in ogni punto. Si presuppone che esista un cubo ' VolumeSpace ', che rappresenta il punto in cui il volume si trova nello spazio globale, che può essere usato come riferimento per inserire i punti:

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos, 1));
```

```
// In the pixel shader:
 float4 color = ShadeVol( SampleVol( volSpace ) );
```

## <a name="volume-tracing-in-shaders"></a>Traccia del volume in shader

Come usare la GPU per eseguire la traccia dei sottovolumi (si tratta di un numero ridotto di voxel, quindi i livelli sui dati da una parte all'altra):

```
float4 AlphaBlend(float4 dst, float4 src) {
   float4 res = (src * src.a) + (dst - dst * src.a);
   res.a = src.a + (dst.a - dst.a*src.a);
   return res;
 }
 float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 0.15; // depth in volume space, customize!!!
   float numLoops = 10; // can be 400 on nice PC
   float4 curColor = float4(0, 0, 0, 0);
   // Figure out front and back volume coords to walk through:
   float3 frontCoord = objPosStart;
   float3 backCoord = frontPos + (normalize(cameraPosVolSpace - objPosStart) * maxDepth);
   float3 stepCoord = (frontCoord - backCoord) / numLoops;
   float3 curCoord = backCoord;
   // Add per-pixel random offset, avoids layer aliasing:
   curCoord += stepCoord * RandomFromPositionFast(objPosStart);
   // Walk from back to front (to make front appear in-front of back):
   for (float i = 0; i < numLoops; i++) {
     float intensity = SampleVol(curCoord);
     float4 shaded = ShadeVol(intensity);
     curColor = AlphaBlend(curColor, shaded);
     curCoord += stepCoord;
   }
   return curColor;
 }
```

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos.xyz, 1));
 float4 cameraInVolSpace = mul(_WorldToVolume, float4(_WorldSpaceCameraPos.xyz, 1));
```

```
// In the pixel shader:
 float4 color = volTraceSubVolume( volSpace, cameraInVolSpace );
```

## <a name="whole-volume-rendering"></a>Rendering intero del volume

Modificando il codice del sottovolume precedente si ottiene:

```
float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 1.73; // sqrt(3), max distance from point on cube to any other point on cube
   int maxSamples = 400; // just in case, keep this value within bounds
   // not shown: trim front and back positions to both be within the cube
   int distanceInVoxels = length(UnitVolumeToIntVolume(frontPos - backPos)); // measure distance in voxels
   int numLoops = min( distanceInVoxels, maxSamples ); // put a min on the voxels to sample
```

## <a name="mixed-resolution-scene-rendering"></a>Rendering di scene con risoluzione mista

Come eseguire il rendering di una parte della scena con una risoluzione bassa e inserirla di nuovo:
1. Configurare due fotocamere fuori schermo, una per seguire ogni occhio che aggiorna ogni frame
2. Configurare due destinazioni di rendering a bassa risoluzione (ad ogni 200x200), in cui viene eseguito il rendering delle fotocamere
3. Configurare un quad che si sposta davanti all'utente

Ogni frame:
1. Disegnare le destinazioni di rendering per ogni occhio a bassa risoluzione (dati del volume, shader costosi e così via)
2. Creare la scena normalmente come risoluzione completa (mesh, interfaccia utente e così via)
3. Disegnare un quad davanti all'utente, sulla scena e proiettare i rendering a bassa risoluzione su tale oggetto.
4. Risultato: combinazione visiva di elementi a risoluzione completa con dati di volume a bassa risoluzione ma ad alta densità.

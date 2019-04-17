---
title: Rendering di volume
description: Immagini volumetrici contengono informazioni avanzate con opacità e il colore in tutto il volume che non può essere espressi facilmente come superfici. Informazioni su come eseguire il rendering in modo efficiente volumetrici immagini all'interno di realtà mista di Windows.
author: KevinKennedy
ms.author: kkennedy
ms.date: 03/21/2018
ms.topic: article
keywords: immagine volumetrici, il rendering di volume, delle prestazioni, realtà mista
ms.openlocfilehash: dc0e75b916ab7cc96be1eccb4ad32ac71f5b75ff
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604099"
---
# <a name="volume-rendering"></a>Rendering di volume

Per i medici MRI o volumi di progettazione, vedere [Volume per il Rendering su Wikipedia](https://en.wikipedia.org/wiki/Volume_rendering). Queste immagini volumetrici contengono informazioni avanzate con i colori in tutto il volume che non possa essere espressi facilmente come aree, ad esempio e opacità [mesh poligonale](https://en.wikipedia.org/wiki/Polygon_mesh).

Soluzioni per migliorare le prestazioni
1. BAD: Approccio di tipo naive: Mostrare l'intero Volume, in genere viene eseguito troppo lenta
2. BUONO: Piano di taglio: Mostra solo un'unica sezione del volume
3. BUONO: Cutting sotto-Volume: Mostra solo alcuni livelli del volume
4. BUONO: Abbassa la risoluzione del rendering volume (vedere 'Misto Rendering di Scene risoluzione')

Non esiste solo una certa quantità di informazioni che possono essere trasferite dall'applicazione sullo schermo in un frame specifico, si tratta della larghezza di banda di memoria totale. Inoltre qualsiasi elaborazione (o 'ombreggiatura') necessarie per trasformare i dati per la presentazione richiede tempo. Considerazioni principali da fare quando si esegue il rendering di volume sono di conseguenza:
* Larghezza dello schermo * altezza dello schermo * schermata-Count * Volume a livelli-sul-che-Pixel = totale-Volume-esempi-Per Frame
* 1028 * 720 * 2 * 256 = 378961920 (100%) (full volume res: troppi esempi)
* 1028 * 720 * 2 * 1 = 1480320 (0,3% di full) (esigua porzione: 1 esempio per ciascun pixel, venga eseguito senza problemi)
* 1028 * 720 * 2 * 10 = 14803200 (% 3.9 di full) (sezione sotto-volume: 10 campioni per ogni pixel, viene eseguito in modo abbastanza uniforme, aspetto 3d)
* 200 * 200 * 2 * 256 = 20480000 (% 5 del full) (abbassarlo res: meno pixel, dell'intero volume aspetto 3d, ma un po' blury)

## <a name="representing-3d-textures"></a>Che rappresenta le trame 3D

Utilizzo di CPU:

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

Nella GPU:

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

Viene illustrato come evidenziare un volume, ad esempio MRI, per la visualizzazione utile. Il metodo principale consiste nel disporre di una finestra dell'intensità' ' (min e max) che si desidera vedere intensità all'interno e puoi semplicemente aumentare a tale spazio per visualizzare l'intensità in bianco e nero. Una barra' colore' può essere applicato ai valori all'interno dell'intervallo e archiviato come una trama, in modo che le parti diverse dello spettro intensità possono ombreggiati colori diversi:

```
float4 ShadeVol( float intensity ) {
   float unitIntensity = saturate( intensity - IntensityMin / ( IntensityMax - IntensityMin ) );
   // Simple two point black and white intensity:
   color.rgba = unitIntensity;
   // Color ramp method:
   color.rgba = tex2d( ColorRampTexture, float2( unitIntensity, 0 ) );
```

In molti nostri applicazioni vengono archiviati nel nostro volume sia un valore non elaborato intensità e un indice di segmentazione' ' (per segmentare, ad esempio le diverse parti dell'interfaccia personalizzata e ossa, questi segmenti vengono in genere creati da esperti gli strumenti dedicati). Questo parametro può essere combinato con l'approccio precedente per inserire un colore diverso o gradazioni di colore diverso anche per ogni indice del segmento:

```
// Change color to match segment index (fade each segment towards black):
 color.rgb = SegmentColors[ segment_index ] * color.a; // brighter alpha gives brighter color
```

## <a name="volume-slicing-in-a-shader"></a>Volume di sezionamento in una trama

Un primo passaggio straordinario consiste nel creare un "piano di sezionamento" che può spostarsi tra il volume 'sezionamento' e come l'analisi valori in ogni punto. Ciò presuppone che sia presente un cubo 'VolumeSpace', che rappresenta in cui il volume è nello spazio globale, che può essere utilizzato come riferimento per i punti di inserimento:

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos, 1));
```

```
// In the pixel shader:
 float4 color = ShadeVol( SampleVol( volSpace ) );
```

## <a name="volume-tracing-in-shaders"></a>Numero di tracce in shader

Come usare la GPU per eseguire la traccia di volume secondario (descrive voxels alcuni livelli di profondità quindi sui dati dal backup in primo piano):

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

## <a name="whole-volume-rendering"></a>Intero Volume per il Rendering

Modificare il codice secondario volume riportato sopra si ottiene:

```
float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 1.73; // sqrt(3), max distance from point on cube to any other point on cube
   int maxSamples = 400; // just in case, keep this value within bounds
   // not shown: trim front and back positions to both be within the cube
   int distanceInVoxels = length(UnitVolumeToIntVolume(frontPos - backPos)); // measure distance in voxels
   int numLoops = min( distanceInVoxels, maxSamples ); // put a min on the voxels to sample
```

## <a name="mixed-resolution-scene-rendering"></a>Rendering di Scene risoluzione misto

Come eseguire il rendering di una parte della scena con una risoluzione inferiore e inserirlo nuovamente nel luogo:
1. Configurare due fotocamere fuori schermo, uno per seguire ogni eye che aggiornano ogni fotogramma
2. Il programma di installazione a bassa risoluzione due eseguire il rendering di destinazioni (ad esempio 200x200 ogni), che le telecamere eseguire il rendering in
3. Un quadrato che sposta davanti all'utente di installazione

Ogni Frame:
1. Disegnare le destinazioni di rendering per ogni occhio a bassa risoluzione (volumi di dati, gli shader costosi e così via)
2. Disegnare la scena in genere come ad alta risoluzione (trame, dell'interfaccia utente e così via.)
3. Disegnare un quad davanti all'utente, sopra la scena e proiettati che esegue il rendering di bassa risoluzione.
4. Risultato: visual combinazione di elementi ad alta risoluzione con i dati di volume a bassa risoluzione ma ad alta densità.

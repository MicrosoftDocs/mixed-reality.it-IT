---
title: Rendering del volume
description: Le immagini volumetriche contengono informazioni dettagliate con opacità e colore in tutto il volume che non possono essere facilmente espresse come superfici. Informazioni su come eseguire il rendering efficiente di immagini volumetriche in realtà mista di Windows.
author: KevinKennedy
ms.author: kkennedy
ms.date: 03/21/2018
ms.topic: article
keywords: immagine volumetrica, rendering del volume, prestazioni, realtà mista
ms.openlocfilehash: 04931df5e4225225e4c11c3f6d72801e2d58f646
ms.sourcegitcommit: 317653cd8500563c514464f0337c1f230a6f3653
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/28/2019
ms.locfileid: "75503830"
---
# <a name="volume-rendering"></a><span data-ttu-id="0d8e4-105">Rendering del volume</span><span class="sxs-lookup"><span data-stu-id="0d8e4-105">Volume rendering</span></span>

<span data-ttu-id="0d8e4-106">Per i volumi di ingegneria o MRI medici, vedere [rendering del volume in Wikipedia](https://en.wikipedia.org/wiki/Volume_rendering).</span><span class="sxs-lookup"><span data-stu-id="0d8e4-106">For medical MRI or engineering volumes, see [Volume Rendering on Wikipedia](https://en.wikipedia.org/wiki/Volume_rendering).</span></span> <span data-ttu-id="0d8e4-107">Queste immagini volumetriche contengono informazioni dettagliate con opacità e colore in tutto il volume che non possono essere facilmente espresse come superfici come le [mesh poligonali](https://en.wikipedia.org/wiki/Polygon_mesh).</span><span class="sxs-lookup"><span data-stu-id="0d8e4-107">These 'volumetric images' contain rich information with opacity and color throughout the volume that cannot be easily expressed as surfaces such as [polygonal meshes](https://en.wikipedia.org/wiki/Polygon_mesh).</span></span>

<span data-ttu-id="0d8e4-108">Soluzioni principali per migliorare le prestazioni</span><span class="sxs-lookup"><span data-stu-id="0d8e4-108">Key solutions to improve performance</span></span>
1. <span data-ttu-id="0d8e4-109">ERRATO: approccio ingenuo: Mostra volume intero, in genere troppo lento</span><span class="sxs-lookup"><span data-stu-id="0d8e4-109">BAD: Naïve Approach: Show Whole Volume, generally runs too slowly</span></span>
2. <span data-ttu-id="0d8e4-110">BENE: piano di taglio: Mostra solo una singola sezione del volume</span><span class="sxs-lookup"><span data-stu-id="0d8e4-110">GOOD: Cutting Plane: Show only a single slice of the volume</span></span>
3. <span data-ttu-id="0d8e4-111">BENE: riduzione del volume secondario: Mostra solo pochi livelli del volume</span><span class="sxs-lookup"><span data-stu-id="0d8e4-111">GOOD: Cutting Sub-Volume: Show only a few layers of the volume</span></span>
4. <span data-ttu-id="0d8e4-112">BENE: abbassare la risoluzione del rendering del volume (vedere il rendering di una scena di risoluzione mista)</span><span class="sxs-lookup"><span data-stu-id="0d8e4-112">GOOD: Lower the resolution of the volume rendering (see 'Mixed Resolution Scene Rendering')</span></span>

<span data-ttu-id="0d8e4-113">È presente una certa quantità di informazioni che possono essere trasferite dall'applicazione alla schermata in un particolare frame, ovvero la larghezza di banda totale della memoria.</span><span class="sxs-lookup"><span data-stu-id="0d8e4-113">There is only a certain amount of information that can be transferred from the application to the screen in any particular frame, which is the total memory bandwidth.</span></span> <span data-ttu-id="0d8e4-114">Inoltre, qualsiasi elaborazione (o ' ombreggiatura ') necessaria per trasformare i dati per la presentazione richiede tempo.</span><span class="sxs-lookup"><span data-stu-id="0d8e4-114">Also, any processing (or 'shading') required to transform that data for presentation requires time.</span></span> <span data-ttu-id="0d8e4-115">Le considerazioni principali per il rendering del volume sono le seguenti:</span><span class="sxs-lookup"><span data-stu-id="0d8e4-115">The primary considerations when doing volume rendering are as such:</span></span>
* <span data-ttu-id="0d8e4-116">Screen-width \* screen-height \* screen-count \* volume-layers-on-that-pixel = Total-volume-Samples-per-frame</span><span class="sxs-lookup"><span data-stu-id="0d8e4-116">Screen-Width \* Screen-Height \* Screen-Count \* Volume-Layers-On-That-Pixel = Total-Volume-Samples-Per-Frame</span></span>
* <span data-ttu-id="0d8e4-117">1028 \* 720 \* 2 \* 256 = 378961920 (100%) (volume res completo: troppi esempi)</span><span class="sxs-lookup"><span data-stu-id="0d8e4-117">1028 \* 720 \* 2 \* 256 = 378961920 (100%) (full res volume: too many samples)</span></span>
* <span data-ttu-id="0d8e4-118">1028 \* 720 \* 2 \* 1 = 1480320 (0,3% of Full) (slice sottile: 1 campione per pixel, esecuzione senza problemi)</span><span class="sxs-lookup"><span data-stu-id="0d8e4-118">1028 \* 720 \* 2 \* 1 = 1480320 (0.3% of full) (thin slice: 1 sample per pixel, runs smoothly)</span></span>
* <span data-ttu-id="0d8e4-119">1028 \* 720 \* 2 \* 10 = 14803200 (3,9% della versione completa) (sezione del volume secondario: 10 campioni per pixel, esecuzione abbastanza agevole, aspetto 3D)</span><span class="sxs-lookup"><span data-stu-id="0d8e4-119">1028 \* 720 \* 2 \* 10 = 14803200 (3.9% of full) (sub-volume slice: 10 samples per pixel, runs fairly smoothly, looks 3d)</span></span>
* <span data-ttu-id="0d8e4-120">200 \* 200 \* 2 \* 256 = 20480000 (5% di pieno) (volume res inferiore: un minor numero di pixel, un volume intero, appare 3D ma un bit sfocato)</span><span class="sxs-lookup"><span data-stu-id="0d8e4-120">200 \* 200 \* 2 \* 256 = 20480000 (5% of full) (lower res volume: fewer pixels, full volume, looks 3d but a bit blurry)</span></span>

## <a name="representing-3d-textures"></a><span data-ttu-id="0d8e4-121">Rappresentazione di trame 3D</span><span class="sxs-lookup"><span data-stu-id="0d8e4-121">Representing 3D Textures</span></span>

<span data-ttu-id="0d8e4-122">Sulla CPU:</span><span class="sxs-lookup"><span data-stu-id="0d8e4-122">On the CPU:</span></span>

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

<span data-ttu-id="0d8e4-123">Sulla GPU:</span><span class="sxs-lookup"><span data-stu-id="0d8e4-123">On the GPU:</span></span>

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

## <a name="shading-and-gradients"></a><span data-ttu-id="0d8e4-124">Ombreggiatura e sfumature</span><span class="sxs-lookup"><span data-stu-id="0d8e4-124">Shading and Gradients</span></span>

<span data-ttu-id="0d8e4-125">Come ombreggiare un volume, ad esempio MRI, per una visualizzazione utile.</span><span class="sxs-lookup"><span data-stu-id="0d8e4-125">How to shade a volume, such as MRI, for useful visualization.</span></span> <span data-ttu-id="0d8e4-126">Il metodo principale consiste nel disporre di una "finestra intensità" (un valore minimo e massimo) in cui si desidera visualizzare le intensità e semplicemente ridimensionare lo spazio per visualizzare l'intensità del nero e del bianco.</span><span class="sxs-lookup"><span data-stu-id="0d8e4-126">The primary method is to have an 'intensity window' (a min and max) that you want to see intensities within, and simply scale into that space to see the black and white intensity.</span></span> <span data-ttu-id="0d8e4-127">È quindi possibile applicare una "rampa di colore" ai valori all'interno di tale intervallo e archiviarli come trama, in modo che le diverse parti dello spettro di intensità possano ombreggiare colori diversi:</span><span class="sxs-lookup"><span data-stu-id="0d8e4-127">A 'color ramp' can then be applied to the values within that range, and stored as a texture, so that different parts of the intensity spectrum can be shaded different colors:</span></span>

```
float4 ShadeVol( float intensity ) {
   float unitIntensity = saturate( intensity - IntensityMin / ( IntensityMax - IntensityMin ) );
   // Simple two point black and white intensity:
   color.rgba = unitIntensity;
   // Color ramp method:
   color.rgba = tex2d( ColorRampTexture, float2( unitIntensity, 0 ) );
```

<span data-ttu-id="0d8e4-128">In molte delle nostre applicazioni viene archiviato nel volume sia un valore di intensità RAW che un "indice di segmentazione" (per segmentare parti diverse, ad esempio Skin e Bone). questi segmenti vengono in genere creati dagli esperti in strumenti dedicati.</span><span class="sxs-lookup"><span data-stu-id="0d8e4-128">In many of our applications, we store in our volume both a raw intensity value and a 'segmentation index' (to segment different parts such as skin and bone; these segments are generally created by experts in dedicated tools).</span></span> <span data-ttu-id="0d8e4-129">Questa operazione può essere combinata con l'approccio precedente per inserire un colore diverso o persino una rampa di colore diversa per ogni indice di segmento:</span><span class="sxs-lookup"><span data-stu-id="0d8e4-129">This can be combined with the approach above to put a different color, or even different color ramp for each segment index:</span></span>

```
// Change color to match segment index (fade each segment towards black):
 color.rgb = SegmentColors[ segment_index ] * color.a; // brighter alpha gives brighter color
```

## <a name="volume-slicing-in-a-shader"></a><span data-ttu-id="0d8e4-130">Sezionamento del volume in uno shader</span><span class="sxs-lookup"><span data-stu-id="0d8e4-130">Volume Slicing in a Shader</span></span>

<span data-ttu-id="0d8e4-131">Il primo passaggio consiste nel creare un "piano di sezionamento" che può spostarsi tra il volume, "sezionamento" e come i valori di analisi in ogni punto.</span><span class="sxs-lookup"><span data-stu-id="0d8e4-131">A great first step is to create a "slicing plane" that can move through the volume, 'slicing it', and how the scan values at each point.</span></span> <span data-ttu-id="0d8e4-132">Si presuppone che esista un cubo ' VolumeSpace ', che rappresenta il punto in cui il volume si trova nello spazio globale, che può essere usato come riferimento per inserire i punti:</span><span class="sxs-lookup"><span data-stu-id="0d8e4-132">This assumes that there is a 'VolumeSpace' cube, which represents where the volume is in world space, that can be used as a reference for placing the points:</span></span>

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos, 1));
```

```
// In the pixel shader:
 float4 color = ShadeVol( SampleVol( volSpace ) );
```

## <a name="volume-tracing-in-shaders"></a><span data-ttu-id="0d8e4-133">Traccia del volume in shader</span><span class="sxs-lookup"><span data-stu-id="0d8e4-133">Volume Tracing in Shaders</span></span>

<span data-ttu-id="0d8e4-134">Come usare la GPU per eseguire la traccia dei sottovolumi (voxel approfondimenti, quindi i livelli sui dati da un ritorno all'inizio):</span><span class="sxs-lookup"><span data-stu-id="0d8e4-134">How to use the GPU to do sub-volume tracing (walks a few voxels deep, then layers on the data from back to front):</span></span>

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

## <a name="whole-volume-rendering"></a><span data-ttu-id="0d8e4-135">Rendering intero del volume</span><span class="sxs-lookup"><span data-stu-id="0d8e4-135">Whole Volume Rendering</span></span>

<span data-ttu-id="0d8e4-136">Modificando il codice del sottovolume riportato sopra, si ottiene:</span><span class="sxs-lookup"><span data-stu-id="0d8e4-136">Modifying the sub-volume code above, we get:</span></span>

```
float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 1.73; // sqrt(3), max distance from point on cube to any other point on cube
   int maxSamples = 400; // just in case, keep this value within bounds
   // not shown: trim front and back positions to both be within the cube
   int distanceInVoxels = length(UnitVolumeToIntVolume(frontPos - backPos)); // measure distance in voxels
   int numLoops = min( distanceInVoxels, maxSamples ); // put a min on the voxels to sample
```

## <a name="mixed-resolution-scene-rendering"></a><span data-ttu-id="0d8e4-137">Rendering di scene con risoluzione mista</span><span class="sxs-lookup"><span data-stu-id="0d8e4-137">Mixed Resolution Scene Rendering</span></span>

<span data-ttu-id="0d8e4-138">Come eseguire il rendering di una parte della scena con una risoluzione bassa e inserirla di nuovo:</span><span class="sxs-lookup"><span data-stu-id="0d8e4-138">How to render a part of the scene with a low resolution and put it back in place:</span></span>
1. <span data-ttu-id="0d8e4-139">Configurare due fotocamere fuori schermo, una per seguire ogni occhio che aggiorna ogni frame</span><span class="sxs-lookup"><span data-stu-id="0d8e4-139">Setup two off-screen cameras, one to follow each eye that update each frame</span></span>
2. <span data-ttu-id="0d8e4-140">Configurare due destinazioni di rendering a bassa risoluzione, ad esempio 200x200 ognuna, in cui vengono sottoposte a rendering le fotocamere</span><span class="sxs-lookup"><span data-stu-id="0d8e4-140">Setup two low-resolution render targets (i.e. 200x200 each) that the cameras render into</span></span>
3. <span data-ttu-id="0d8e4-141">Configurare un quad che si sposta davanti all'utente</span><span class="sxs-lookup"><span data-stu-id="0d8e4-141">Setup a quad that moves in front of the user</span></span>

<span data-ttu-id="0d8e4-142">Ogni frame:</span><span class="sxs-lookup"><span data-stu-id="0d8e4-142">Each Frame:</span></span>
1. <span data-ttu-id="0d8e4-143">Disegnare le destinazioni di rendering per ogni occhio a bassa risoluzione (dati del volume, shader costosi e così via)</span><span class="sxs-lookup"><span data-stu-id="0d8e4-143">Draw the render targets for each eye at low-resolution (volume data, expensive shaders, etc.)</span></span>
2. <span data-ttu-id="0d8e4-144">Creare la scena normalmente come risoluzione completa (mesh, interfaccia utente e così via)</span><span class="sxs-lookup"><span data-stu-id="0d8e4-144">Draw the scene normally as full resolution (meshes, UI, etc.)</span></span>
3. <span data-ttu-id="0d8e4-145">Disegnare un quad davanti all'utente, sulla scena e proiettare i rendering a bassa risoluzione su tale</span><span class="sxs-lookup"><span data-stu-id="0d8e4-145">Draw a quad in front of the user, over the scene, and project the low-res renders onto that</span></span>
4. <span data-ttu-id="0d8e4-146">Risultato: combinazione visiva di elementi a risoluzione completa con dati di volume a bassa risoluzione ma a densità elevata</span><span class="sxs-lookup"><span data-stu-id="0d8e4-146">Result: visual combination of full-resolution elements with low-resolution but high-density volume data</span></span>

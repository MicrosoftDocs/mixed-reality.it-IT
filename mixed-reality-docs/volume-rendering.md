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
# <a name="volume-rendering"></a><span data-ttu-id="7707f-105">Rendering di volume</span><span class="sxs-lookup"><span data-stu-id="7707f-105">Volume rendering</span></span>

<span data-ttu-id="7707f-106">Per i medici MRI o volumi di progettazione, vedere [Volume per il Rendering su Wikipedia](https://en.wikipedia.org/wiki/Volume_rendering).</span><span class="sxs-lookup"><span data-stu-id="7707f-106">For medical MRI or engineering volumes, see [Volume Rendering on Wikipedia](https://en.wikipedia.org/wiki/Volume_rendering).</span></span> <span data-ttu-id="7707f-107">Queste immagini volumetrici contengono informazioni avanzate con i colori in tutto il volume che non possa essere espressi facilmente come aree, ad esempio e opacità [mesh poligonale](https://en.wikipedia.org/wiki/Polygon_mesh).</span><span class="sxs-lookup"><span data-stu-id="7707f-107">These 'volumetric images' contain rich information with opacity and color throughout the volume that cannot be easily expressed as surfaces such as [polygonal meshes](https://en.wikipedia.org/wiki/Polygon_mesh).</span></span>

<span data-ttu-id="7707f-108">Soluzioni per migliorare le prestazioni</span><span class="sxs-lookup"><span data-stu-id="7707f-108">Key solutions to improve performance</span></span>
1. <span data-ttu-id="7707f-109">BAD: Approccio di tipo naive: Mostrare l'intero Volume, in genere viene eseguito troppo lenta</span><span class="sxs-lookup"><span data-stu-id="7707f-109">BAD: Naïve Approach: Show Whole Volume, generally runs too slowly</span></span>
2. <span data-ttu-id="7707f-110">BUONO: Piano di taglio: Mostra solo un'unica sezione del volume</span><span class="sxs-lookup"><span data-stu-id="7707f-110">GOOD: Cutting Plane: Show only a single slice of the volume</span></span>
3. <span data-ttu-id="7707f-111">BUONO: Cutting sotto-Volume: Mostra solo alcuni livelli del volume</span><span class="sxs-lookup"><span data-stu-id="7707f-111">GOOD: Cutting Sub-Volume: Show only a few layers of the volume</span></span>
4. <span data-ttu-id="7707f-112">BUONO: Abbassa la risoluzione del rendering volume (vedere 'Misto Rendering di Scene risoluzione')</span><span class="sxs-lookup"><span data-stu-id="7707f-112">GOOD: Lower the resolution of the volume rendering (see 'Mixed Resolution Scene Rendering')</span></span>

<span data-ttu-id="7707f-113">Non esiste solo una certa quantità di informazioni che possono essere trasferite dall'applicazione sullo schermo in un frame specifico, si tratta della larghezza di banda di memoria totale.</span><span class="sxs-lookup"><span data-stu-id="7707f-113">There is only a certain amount of information that can be transferred from the application to the screen in any particular frame, this is the total memory bandwidth.</span></span> <span data-ttu-id="7707f-114">Inoltre qualsiasi elaborazione (o 'ombreggiatura') necessarie per trasformare i dati per la presentazione richiede tempo.</span><span class="sxs-lookup"><span data-stu-id="7707f-114">Also any processing (or 'shading') required to transform that data for presentation also requires time.</span></span> <span data-ttu-id="7707f-115">Considerazioni principali da fare quando si esegue il rendering di volume sono di conseguenza:</span><span class="sxs-lookup"><span data-stu-id="7707f-115">The primary considerations when doing volume rendering are as such:</span></span>
* <span data-ttu-id="7707f-116">Larghezza dello schermo \* altezza dello schermo \* schermata-Count \* Volume a livelli-sul-che-Pixel = totale-Volume-esempi-Per Frame</span><span class="sxs-lookup"><span data-stu-id="7707f-116">Screen-Width \* Screen-Height \* Screen-Count \* Volume-Layers-On-That-Pixel = Total-Volume-Samples-Per-Frame</span></span>
* <span data-ttu-id="7707f-117">1028 \* 720 \* 2 \* 256 = 378961920 (100%) (full volume res: troppi esempi)</span><span class="sxs-lookup"><span data-stu-id="7707f-117">1028 \* 720 \* 2 \* 256 = 378961920 (100%) (full res volume: too many samples)</span></span>
* <span data-ttu-id="7707f-118">1028 \* 720 \* 2 \* 1 = 1480320 (0,3% di full) (esigua porzione: 1 esempio per ciascun pixel, venga eseguito senza problemi)</span><span class="sxs-lookup"><span data-stu-id="7707f-118">1028 \* 720 \* 2 \* 1 = 1480320 (0.3% of full) (thin slice: 1 sample per pixel, runs smoothly)</span></span>
* <span data-ttu-id="7707f-119">1028 \* 720 \* 2 \* 10 = 14803200 (% 3.9 di full) (sezione sotto-volume: 10 campioni per ogni pixel, viene eseguito in modo abbastanza uniforme, aspetto 3d)</span><span class="sxs-lookup"><span data-stu-id="7707f-119">1028 \* 720 \* 2 \* 10 = 14803200 (3.9% of full) (sub-volume slice: 10 samples per pixel, runs fairly smoothly, looks 3d)</span></span>
* <span data-ttu-id="7707f-120">200 \* 200 \* 2 \* 256 = 20480000 (% 5 del full) (abbassarlo res: meno pixel, dell'intero volume aspetto 3d, ma un po' blury)</span><span class="sxs-lookup"><span data-stu-id="7707f-120">200 \* 200 \* 2 \* 256 = 20480000 (5% of full) (lower res volume: fewer pixels, full volume, looks 3d but a bit blury)</span></span>

## <a name="representing-3d-textures"></a><span data-ttu-id="7707f-121">Che rappresenta le trame 3D</span><span class="sxs-lookup"><span data-stu-id="7707f-121">Representing 3D Textures</span></span>

<span data-ttu-id="7707f-122">Utilizzo di CPU:</span><span class="sxs-lookup"><span data-stu-id="7707f-122">On the CPU:</span></span>

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

<span data-ttu-id="7707f-123">Nella GPU:</span><span class="sxs-lookup"><span data-stu-id="7707f-123">On the GPU:</span></span>

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

## <a name="shading-and-gradients"></a><span data-ttu-id="7707f-124">Ombreggiatura e sfumature</span><span class="sxs-lookup"><span data-stu-id="7707f-124">Shading and Gradients</span></span>

<span data-ttu-id="7707f-125">Viene illustrato come evidenziare un volume, ad esempio MRI, per la visualizzazione utile.</span><span class="sxs-lookup"><span data-stu-id="7707f-125">How to shade an volume, such as MRI, for useful visualization.</span></span> <span data-ttu-id="7707f-126">Il metodo principale consiste nel disporre di una finestra dell'intensità' ' (min e max) che si desidera vedere intensità all'interno e puoi semplicemente aumentare a tale spazio per visualizzare l'intensità in bianco e nero.</span><span class="sxs-lookup"><span data-stu-id="7707f-126">The primary method is to have an 'intensity window' (a min and max) that you want to see intensities within, and simply scale into that space to see the black and white intensity.</span></span> <span data-ttu-id="7707f-127">Una barra' colore' può essere applicato ai valori all'interno dell'intervallo e archiviato come una trama, in modo che le parti diverse dello spettro intensità possono ombreggiati colori diversi:</span><span class="sxs-lookup"><span data-stu-id="7707f-127">A 'color ramp' can then be applied to the values within that range, and stored as a texture, so that different parts of the intensity spectrum can be shaded different colors:</span></span>

```
float4 ShadeVol( float intensity ) {
   float unitIntensity = saturate( intensity - IntensityMin / ( IntensityMax - IntensityMin ) );
   // Simple two point black and white intensity:
   color.rgba = unitIntensity;
   // Color ramp method:
   color.rgba = tex2d( ColorRampTexture, float2( unitIntensity, 0 ) );
```

<span data-ttu-id="7707f-128">In molti nostri applicazioni vengono archiviati nel nostro volume sia un valore non elaborato intensità e un indice di segmentazione' ' (per segmentare, ad esempio le diverse parti dell'interfaccia personalizzata e ossa, questi segmenti vengono in genere creati da esperti gli strumenti dedicati).</span><span class="sxs-lookup"><span data-stu-id="7707f-128">In many our applications we store in our volume both a raw intensity value and a 'segmentation index' (to segment different parts such as skin and bone, these segments are generally created by experts in dedicated tools).</span></span> <span data-ttu-id="7707f-129">Questo parametro può essere combinato con l'approccio precedente per inserire un colore diverso o gradazioni di colore diverso anche per ogni indice del segmento:</span><span class="sxs-lookup"><span data-stu-id="7707f-129">This can be combined with the approach above to put a different color, or even different color ramp for each segment index:</span></span>

```
// Change color to match segment index (fade each segment towards black):
 color.rgb = SegmentColors[ segment_index ] * color.a; // brighter alpha gives brighter color
```

## <a name="volume-slicing-in-a-shader"></a><span data-ttu-id="7707f-130">Volume di sezionamento in una trama</span><span class="sxs-lookup"><span data-stu-id="7707f-130">Volume Slicing in a Shader</span></span>

<span data-ttu-id="7707f-131">Un primo passaggio straordinario consiste nel creare un "piano di sezionamento" che può spostarsi tra il volume 'sezionamento' e come l'analisi valori in ogni punto.</span><span class="sxs-lookup"><span data-stu-id="7707f-131">A great first step is to create a "slicing plane" that can move through the volume, 'slicing it', and how the scan values at each point.</span></span> <span data-ttu-id="7707f-132">Ciò presuppone che sia presente un cubo 'VolumeSpace', che rappresenta in cui il volume è nello spazio globale, che può essere utilizzato come riferimento per i punti di inserimento:</span><span class="sxs-lookup"><span data-stu-id="7707f-132">This assumes that there is a 'VolumeSpace' cube, which represents where the volume is in world space, that can be used as a reference for placing the points:</span></span>

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos, 1));
```

```
// In the pixel shader:
 float4 color = ShadeVol( SampleVol( volSpace ) );
```

## <a name="volume-tracing-in-shaders"></a><span data-ttu-id="7707f-133">Numero di tracce in shader</span><span class="sxs-lookup"><span data-stu-id="7707f-133">Volume Tracing in Shaders</span></span>

<span data-ttu-id="7707f-134">Come usare la GPU per eseguire la traccia di volume secondario (descrive voxels alcuni livelli di profondità quindi sui dati dal backup in primo piano):</span><span class="sxs-lookup"><span data-stu-id="7707f-134">How to use the GPU to do sub-volume tracing (walks a few voxels deep then layers on the data from back to front):</span></span>

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

## <a name="whole-volume-rendering"></a><span data-ttu-id="7707f-135">Intero Volume per il Rendering</span><span class="sxs-lookup"><span data-stu-id="7707f-135">Whole Volume Rendering</span></span>

<span data-ttu-id="7707f-136">Modificare il codice secondario volume riportato sopra si ottiene:</span><span class="sxs-lookup"><span data-stu-id="7707f-136">Modifying the sub-volume code above we get:</span></span>

```
float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 1.73; // sqrt(3), max distance from point on cube to any other point on cube
   int maxSamples = 400; // just in case, keep this value within bounds
   // not shown: trim front and back positions to both be within the cube
   int distanceInVoxels = length(UnitVolumeToIntVolume(frontPos - backPos)); // measure distance in voxels
   int numLoops = min( distanceInVoxels, maxSamples ); // put a min on the voxels to sample
```

## <a name="mixed-resolution-scene-rendering"></a><span data-ttu-id="7707f-137">Rendering di Scene risoluzione misto</span><span class="sxs-lookup"><span data-stu-id="7707f-137">Mixed Resolution Scene Rendering</span></span>

<span data-ttu-id="7707f-138">Come eseguire il rendering di una parte della scena con una risoluzione inferiore e inserirlo nuovamente nel luogo:</span><span class="sxs-lookup"><span data-stu-id="7707f-138">How to render a part of the scene with a low resolution and put it back in place:</span></span>
1. <span data-ttu-id="7707f-139">Configurare due fotocamere fuori schermo, uno per seguire ogni eye che aggiornano ogni fotogramma</span><span class="sxs-lookup"><span data-stu-id="7707f-139">Setup two off-screen cameras, one to follow each eye that update each frame</span></span>
2. <span data-ttu-id="7707f-140">Il programma di installazione a bassa risoluzione due eseguire il rendering di destinazioni (ad esempio 200x200 ogni), che le telecamere eseguire il rendering in</span><span class="sxs-lookup"><span data-stu-id="7707f-140">Setup two low-resolution render targets (say 200x200 each), that the cameras render into</span></span>
3. <span data-ttu-id="7707f-141">Un quadrato che sposta davanti all'utente di installazione</span><span class="sxs-lookup"><span data-stu-id="7707f-141">Setup a quad that moves in front of the user</span></span>

<span data-ttu-id="7707f-142">Ogni Frame:</span><span class="sxs-lookup"><span data-stu-id="7707f-142">Each Frame:</span></span>
1. <span data-ttu-id="7707f-143">Disegnare le destinazioni di rendering per ogni occhio a bassa risoluzione (volumi di dati, gli shader costosi e così via)</span><span class="sxs-lookup"><span data-stu-id="7707f-143">Draw the render targets for each eye at low-resolution (volume data, expensive shaders, etc.)</span></span>
2. <span data-ttu-id="7707f-144">Disegnare la scena in genere come ad alta risoluzione (trame, dell'interfaccia utente e così via.)</span><span class="sxs-lookup"><span data-stu-id="7707f-144">Draw the scene normally as full resolution (meshes, UI, etc.)</span></span>
3. <span data-ttu-id="7707f-145">Disegnare un quad davanti all'utente, sopra la scena e proiettati che esegue il rendering di bassa risoluzione.</span><span class="sxs-lookup"><span data-stu-id="7707f-145">Draw a quad in front of the user, over the scene, and project the low-res renders onto that.</span></span>
4. <span data-ttu-id="7707f-146">Risultato: visual combinazione di elementi ad alta risoluzione con i dati di volume a bassa risoluzione ma ad alta densità.</span><span class="sxs-lookup"><span data-stu-id="7707f-146">Result: visual combination of full-resolution elements with low-resolution but high-density volume data.</span></span>

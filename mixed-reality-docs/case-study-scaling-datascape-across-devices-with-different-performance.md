---
title: 'Case Study: ridimensionamento di DataScape tra dispositivi con prestazioni diverse'
description: Questo case study offre informazioni sul modo in cui gli sviluppatori Microsoft hanno ottimizzato l'app DataScape per offrire un'esperienza accattivante tra i dispositivi con una gamma di funzionalità di prestazioni.
author: danandersson
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: auricolare immersivo, ottimizzazione delle prestazioni, VR, case study
ms.openlocfilehash: 990a5ee6de07b6416e3150a7885220409a9c8d93
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63523363"
---
# <a name="case-study---scaling-datascape-across-devices-with-different-performance"></a><span data-ttu-id="eb360-104">Case Study: ridimensionamento di DataScape tra dispositivi con prestazioni diverse</span><span class="sxs-lookup"><span data-stu-id="eb360-104">Case study - Scaling Datascape across devices with different performance</span></span>

<span data-ttu-id="eb360-105">DataScape è un'applicazione di realtà mista di Windows sviluppata internamente in Microsoft, in cui siamo concentrati sulla visualizzazione dei dati meteorologici sui dati del terreno.</span><span class="sxs-lookup"><span data-stu-id="eb360-105">Datascape is a Windows Mixed Reality application developed internally at Microsoft where we focused on displaying weather data on top of terrain data.</span></span> <span data-ttu-id="eb360-106">L'applicazione esamina gli utenti esclusivi di Insights per individuare i dati in realtà mista, circondando l'utente con la visualizzazione dei dati olografici.</span><span class="sxs-lookup"><span data-stu-id="eb360-106">The application explores the unique insights users gain from discovering data in mixed reality by surrounding the user with holographic data visualization.</span></span>

<span data-ttu-id="eb360-107">Per DataScape si vuole avere come destinazione un'ampia gamma di piattaforme con diverse funzionalità hardware, tra cui Microsoft HoloLens e gli auricolari per la realtà mista di Windows, e dai PC meno potenti ai PC più recenti con GPU di fascia alta.</span><span class="sxs-lookup"><span data-stu-id="eb360-107">For Datascape we wanted to target a variety of platforms with different hardware capabilities ranging from Microsoft HoloLens to Windows Mixed Reality immersive headsets, and from lower-powered PCs to the very latest PCs with high-end GPU.</span></span> <span data-ttu-id="eb360-108">La sfida principale è stata il rendering della nostra scena in una situazione visivamente accattivante sui dispositivi con funzionalità grafiche estremamente diverse durante l'esecuzione con un framerate elevato.</span><span class="sxs-lookup"><span data-stu-id="eb360-108">The main challenge was rendering our scene in a visually appealing matter on devices with wildly different graphics capabilities while executing at a high framerate.</span></span>

<span data-ttu-id="eb360-109">In questo case study verranno illustrati il processo e le tecniche utilizzate per creare alcuni dei sistemi più a elevato utilizzo di GPU, che descrivono i problemi riscontrati e come sono stati superati.</span><span class="sxs-lookup"><span data-stu-id="eb360-109">This case study will walk through the process and techniques used to create some of our more GPU-intensive systems, describing the problems we encountered and how we overcame them.</span></span>

## <a name="transparency-and-overdraw"></a><span data-ttu-id="eb360-110">Trasparenza e sovraestrazione</span><span class="sxs-lookup"><span data-stu-id="eb360-110">Transparency and overdraw</span></span>

<span data-ttu-id="eb360-111">I nostri principali problemi di rendering sono stati affrontati con la trasparenza, perché la trasparenza può essere costosa su una GPU.</span><span class="sxs-lookup"><span data-stu-id="eb360-111">Our main rendering struggles dealt with transparency, since transparency can be expensive on a GPU.</span></span>

<span data-ttu-id="eb360-112">È possibile eseguire il rendering della geometria a tinta unita in primo piano durante la scrittura nel buffer di profondità, arrestando eventuali pixel futuri che si trovano dietro il pixel da eliminare.</span><span class="sxs-lookup"><span data-stu-id="eb360-112">Solid geometry can be rendered front to back while writing to the depth buffer, stopping any future pixels located behind that pixel from being discarded.</span></span> <span data-ttu-id="eb360-113">In questo modo si evita che i pixel nascosti eseguano la pixel shader, velocizzando significativamente il processo.</span><span class="sxs-lookup"><span data-stu-id="eb360-113">This prevents hidden pixels from executing the pixel shader, speeding up the process significantly.</span></span> <span data-ttu-id="eb360-114">Se la geometria è ordinata in modo ottimale, ogni pixel sullo schermo viene disegnato una sola volta.</span><span class="sxs-lookup"><span data-stu-id="eb360-114">If geometry is sorted optimally, each pixel on the screen will be drawn only once.</span></span>

<span data-ttu-id="eb360-115">La geometria trasparente deve essere ordinata di nuovo in primo piano e si basa sulla fusione dell'output del pixel shader al pixel corrente sullo schermo.</span><span class="sxs-lookup"><span data-stu-id="eb360-115">Transparent geometry needs to be sorted back to front and relies on blending the output of the pixel shader to the current pixel on the screen.</span></span> <span data-ttu-id="eb360-116">Questo può comportare la traccia di ogni pixel sullo schermo su più volte per fotogramma, definito sovradisegno.</span><span class="sxs-lookup"><span data-stu-id="eb360-116">This can result in each pixel on the screen being drawn to multiple times per frame, referred to as overdraw.</span></span>

<span data-ttu-id="eb360-117">Per i PC HoloLens e mainstream, la schermata può essere compilata solo alcune volte, rendendo problematico il rendering trasparente.</span><span class="sxs-lookup"><span data-stu-id="eb360-117">For HoloLens and mainstream PCs, the screen can only be filled a handful of times, making transparent rendering problematic.</span></span>

## <a name="introduction-to-datascape-scene-components"></a><span data-ttu-id="eb360-118">Introduzione ai componenti della scena di DataScape</span><span class="sxs-lookup"><span data-stu-id="eb360-118">Introduction to Datascape scene components</span></span>

<span data-ttu-id="eb360-119">Nella nostra scena erano presenti tre componenti principali: **l'interfaccia utente, la mappa**e **il meteo**.</span><span class="sxs-lookup"><span data-stu-id="eb360-119">We had three major components to our scene; **the UI, the map**, and **the weather**.</span></span> <span data-ttu-id="eb360-120">Sapevamo che i nostri effetti meteorologici richiedevano tutto il tempo della GPU, quindi abbiamo progettato intenzionalmente l'interfaccia utente e il terreno in modo da ridurre il sovralievo.</span><span class="sxs-lookup"><span data-stu-id="eb360-120">We knew early on that our weather effects would require all the GPU time it could get, so we purposely designed the UI and terrain in a way that would reduce any overdraw.</span></span>

<span data-ttu-id="eb360-121">L'interfaccia utente è stata rielaborata più volte per ridurre al minimo la quantità di sovragenerazione che produce.</span><span class="sxs-lookup"><span data-stu-id="eb360-121">We reworked the UI several times to minimize the amount of overdraw it would produce.</span></span> <span data-ttu-id="eb360-122">Ci siamo sbagliati sul lato di una geometria più complessa anziché sovrapporre l'arte trasparente sopra l'altra per componenti come pulsanti luminosi e panoramiche mappa.</span><span class="sxs-lookup"><span data-stu-id="eb360-122">We erred on the side of more complex geometry rather than overlaying transparent art on top of each other for components like glowing buttons and map overviews.</span></span>

<span data-ttu-id="eb360-123">Per la mappa, abbiamo usato uno shader personalizzato che rimuoverebbe le funzionalità di Unity standard come le ombre e l'illuminazione complessa, sostituendolo con un semplice modello di illuminazione solare singolo e un calcolo di nebbia personalizzato.</span><span class="sxs-lookup"><span data-stu-id="eb360-123">For the map, we used a custom shader that would strip out standard Unity features such as shadows and complex lighting, replacing them with a simple single sun lighting model and a custom fog calculation.</span></span> <span data-ttu-id="eb360-124">Ciò ha prodotto una semplice pixel shader e libera i cicli della GPU.</span><span class="sxs-lookup"><span data-stu-id="eb360-124">This produced a simple pixel shader and free up GPU cycles.</span></span>

<span data-ttu-id="eb360-125">Abbiamo gestito l'interfaccia utente e la mappa per il rendering in base al budget in cui non sono state necessarie modifiche a seconda dell'hardware; Tuttavia, la visualizzazione Meteo, in particolare il rendering del cloud, si è rivelata una sfida.</span><span class="sxs-lookup"><span data-stu-id="eb360-125">We managed to get both the UI and the map to rendering at budget where we did not need any changes to them depending on the hardware; however, the weather visualization, in particular the cloud rendering, proved to be more of a challenge!</span></span>

## <a name="background-on-cloud-data"></a><span data-ttu-id="eb360-126">Informazioni di base sui dati cloud</span><span class="sxs-lookup"><span data-stu-id="eb360-126">Background on cloud data</span></span>

<span data-ttu-id="eb360-127">I dati del cloud sono stati scaricati dai server http://nomads.ncep.noaa.gov/) NOAA (e sono Stati Uniti in tre distinti livelli 2D, ognuno con l'altezza superiore e inferiore del cloud, nonché la densità del cloud per ogni cella della griglia.</span><span class="sxs-lookup"><span data-stu-id="eb360-127">Our cloud data was downloaded from NOAA servers (http://nomads.ncep.noaa.gov/) and came to us in three distinct 2D layers, each with the top and bottom height of the cloud, as well as the density of the cloud for each cell of the grid.</span></span> <span data-ttu-id="eb360-128">I dati sono stati elaborati in una trama di informazioni cloud in cui ogni componente è stato archiviato nel componente rosso, verde e blu della trama per semplificare l'accesso alla GPU.</span><span class="sxs-lookup"><span data-stu-id="eb360-128">The data got processed into a cloud info texture where each component was stored in the red, green, and blue component of the texture for easy access on the GPU.</span></span>

## <a name="geometry-clouds"></a><span data-ttu-id="eb360-129">Cloud Geometry</span><span class="sxs-lookup"><span data-stu-id="eb360-129">Geometry clouds</span></span>

<span data-ttu-id="eb360-130">Per assicurarsi che i computer meno potenti potessero eseguire il rendering dei cloud, abbiamo deciso di iniziare con un approccio che usa la geometria solida per ridurre al minimo il sovralievo.</span><span class="sxs-lookup"><span data-stu-id="eb360-130">To make sure our lower-powered machines could render our clouds we decided to start with an approach that would use solid geometry to minimize overdraw.</span></span>

<span data-ttu-id="eb360-131">Abbiamo prima provato a produrre i cloud generando una mesh heightmap solida per ogni livello usando il raggio della trama delle informazioni sul cloud per ogni vertice per generare la forma.</span><span class="sxs-lookup"><span data-stu-id="eb360-131">We first tried producing clouds by generating a solid heightmap mesh for each layer using the radius of the cloud info texture per vertex to generate the shape.</span></span> <span data-ttu-id="eb360-132">È stato usato un geometry shader per produrre i vertici sia nella parte superiore che nella parte inferiore del cloud che genera forme cloud solide.</span><span class="sxs-lookup"><span data-stu-id="eb360-132">We used a geometry shader to produce the vertices both at the top and the bottom of the cloud generating solid cloud shapes.</span></span> <span data-ttu-id="eb360-133">È stato usato il valore della densità dalla trama per colorare il cloud con colori più scuri per i cloud più densi.</span><span class="sxs-lookup"><span data-stu-id="eb360-133">We used the density value from the texture to color the cloud with darker colors for more dense clouds.</span></span>

<span data-ttu-id="eb360-134">**Shader per la creazione dei vertici:**</span><span class="sxs-lookup"><span data-stu-id="eb360-134">**Shader for creating the vertices:**</span></span>

```
v2g vert (appdata v)
{
    v2g o;
    o.height = tex2Dlod(_MainTex, float4(v.uv, 0, 0)).x;
    o.vertex = v.vertex;
    return o;
}
 
g2f GetOutput(v2g input, float heightDirection)
{
    g2f ret;
    float4 newBaseVert = input.vertex;
    newBaseVert.y += input.height * heightDirection * _HeigthScale;
    ret.vertex = UnityObjectToClipPos(newBaseVert);
    ret.height = input.height;
    return ret;
}
 
[maxvertexcount(6)]
void geo(triangle v2g p[3], inout TriangleStream<g2f> triStream)
{
    float heightTotal = p[0].height + p[1].height + p[2].height;
    if (heightTotal > 0)
    {
        triStream.Append(GetOutput(p[0], 1));
        triStream.Append(GetOutput(p[1], 1));
        triStream.Append(GetOutput(p[2], 1));
 
        triStream.RestartStrip();
 
        triStream.Append(GetOutput(p[2], -1));
        triStream.Append(GetOutput(p[1], -1));
        triStream.Append(GetOutput(p[0], -1));
    }
}
fixed4 frag (g2f i) : SV_Target
{
    clip(i.height - 0.1f);
 
    float3 finalColor = lerp(_LowColor, _HighColor, i.height);
    return float4(finalColor, 1);
}
```

<span data-ttu-id="eb360-135">È stato introdotto un piccolo modello di disturbo per ottenere maggiori dettagli sui dati reali.</span><span class="sxs-lookup"><span data-stu-id="eb360-135">We introduced a small noise pattern to get more detail on top of the real data.</span></span> <span data-ttu-id="eb360-136">Per produrre i bordi arrotondati del cloud, abbiamo ritagliato i pixel nel pixel shader quando il valore del raggio interpolato raggiunge una soglia per eliminare i valori near zero.</span><span class="sxs-lookup"><span data-stu-id="eb360-136">To produce round cloud edges, we clipped the pixels in the pixel shader when the interpolated radius value hit a threshold to discard near-zero values.</span></span>

![Cloud Geometry](images/datascape-geometry-clouds-700px.jpg)

<span data-ttu-id="eb360-138">Poiché i cloud sono di tipo geometria uniforme, è possibile eseguirne il rendering prima del terreno per nascondere i pixel di mappa costosi sottostanti per migliorare ulteriormente la frequenza fotogrammi.</span><span class="sxs-lookup"><span data-stu-id="eb360-138">Since the clouds are solid geometry, they can be rendered before the terrain to hide any expensive map pixels underneath to further improve framerate.</span></span> <span data-ttu-id="eb360-139">Questa soluzione è stata eseguita correttamente in tutte le schede grafiche da min-spec a schede grafiche di fascia alta, così come in HoloLens, a causa dell'approccio di rendering a geometria solida.</span><span class="sxs-lookup"><span data-stu-id="eb360-139">This solution ran well on all graphics cards from min-spec to high-end graphics cards, as well as on HoloLens, because of the solid geometry rendering approach.</span></span>

## <a name="solid-particle-clouds"></a><span data-ttu-id="eb360-140">Cloud di particelle solide</span><span class="sxs-lookup"><span data-stu-id="eb360-140">Solid particle clouds</span></span>

<span data-ttu-id="eb360-141">Ora è disponibile una soluzione di backup che ha prodotto una rappresentazione decente dei dati del cloud, ma è un po' scialbo nel fattore "Wow" e non ha trasmesso l'aspetto volumetrico che volevamo per i nostri computer di fascia alta.</span><span class="sxs-lookup"><span data-stu-id="eb360-141">We now had a backup solution that produced a decent representation of our cloud data, but was a bit lackluster in the “wow” factor and did not convey the volumetric feel that we wanted for our high-end machines.</span></span>

<span data-ttu-id="eb360-142">Il passaggio successivo consisteva nel creare i cloud, rappresentarli con circa 100.000 particelle per produrre un aspetto più organico e volumetrico.</span><span class="sxs-lookup"><span data-stu-id="eb360-142">Our next step was creating the clouds by representing them with approximately 100,000 particles to produce a more organic and volumetric look.</span></span>

<span data-ttu-id="eb360-143">Se le particelle vengono mantenute solide e ordinate da front-to-back, è comunque possibile trarre vantaggio dall'abbassamento del buffer di profondità dei pixel dietro le particelle precedentemente sottoposte a rendering, riducendo la sovradisegna</span><span class="sxs-lookup"><span data-stu-id="eb360-143">If particles stay solid and sort front-to-back, we can still benefit from depth buffer culling of the pixels behind previously rendered particles, reducing the overdraw.</span></span> <span data-ttu-id="eb360-144">Inoltre, con una soluzione basata su particelle, è possibile modificare la quantità di particelle utilizzata per la destinazione di hardware diverso.</span><span class="sxs-lookup"><span data-stu-id="eb360-144">Also, with a particle-based solution, we can alter the amount of particles used to target different hardware.</span></span> <span data-ttu-id="eb360-145">Tuttavia, tutti i pixel devono comunque essere sottoposti a test di profondità, il che comporta un sovraccarico aggiuntivo.</span><span class="sxs-lookup"><span data-stu-id="eb360-145">However, all pixels still need to be depth tested, which results in some additional overhead.</span></span>

<span data-ttu-id="eb360-146">In primo luogo, abbiamo creato posizioni particellari intorno al punto centrale dell'esperienza all'avvio.</span><span class="sxs-lookup"><span data-stu-id="eb360-146">First, we created particle positions around the center point of the experience at startup.</span></span> <span data-ttu-id="eb360-147">Le particelle sono state distribuite in modo più denso attorno al centro e in meno, a distanza.</span><span class="sxs-lookup"><span data-stu-id="eb360-147">We distributed the particles more densely around the center and less so in the distance.</span></span> <span data-ttu-id="eb360-148">Sono state pre-ordinate tutte le particelle dal centro verso il retro, in modo da eseguire prima il rendering delle particelle più vicine.</span><span class="sxs-lookup"><span data-stu-id="eb360-148">We pre-sorted all particles from the center to the back so that the closest particles would render first.</span></span>

<span data-ttu-id="eb360-149">Un compute shader campiona la trama delle informazioni sul cloud per posizionare ogni particella a un'altezza corretta e colorarla in base alla densità.</span><span class="sxs-lookup"><span data-stu-id="eb360-149">A compute shader would sample the cloud info texture to position each particle at a correct height and color it based on the density.</span></span>

<span data-ttu-id="eb360-150">È stato usato *DrawProcedural* per eseguire il rendering di un quad per particella che consente ai dati particellari di rimanere sempre aggiornati sulla GPU.</span><span class="sxs-lookup"><span data-stu-id="eb360-150">We used *DrawProcedural* to render a quad per particle allowing the particle data to stay on the GPU at all times.</span></span>

<span data-ttu-id="eb360-151">Ogni particella contiene un'altezza e un raggio.</span><span class="sxs-lookup"><span data-stu-id="eb360-151">Each particle contained both a height and a radius.</span></span> <span data-ttu-id="eb360-152">L'altezza è basata sui dati del cloud campionati dalla trama delle informazioni sul cloud e il raggio è basato sulla distribuzione iniziale, in cui verrebbe calcolato per archiviare la distanza orizzontale rispetto al relativo Neighbor più vicino.</span><span class="sxs-lookup"><span data-stu-id="eb360-152">The height was based on the cloud data sampled from the cloud info texture, and the radius was based on the initial distribution where it would be calculated to store the horizontal distance to its closest neighbor.</span></span> <span data-ttu-id="eb360-153">I quad useranno questi dati per orientarsi all'angolo in base all'altezza, in modo che, quando gli utenti li esaminano orizzontalmente, l'altezza venga visualizzata e quando gli utenti li esaminano dall'alto verso il basso, viene analizzata l'area tra gli elementi adiacenti.</span><span class="sxs-lookup"><span data-stu-id="eb360-153">The quads would use this data to orient itself angled by the height so that when users look at it horizontally, the height would be shown, and when users looked at it top-down, the area between its neighbors would be covered.</span></span>

![Forma particella](images/particle-shape-700px.png)

<span data-ttu-id="eb360-155">**Codice dello shader che mostra la distribuzione:**</span><span class="sxs-lookup"><span data-stu-id="eb360-155">**Shader code showing the distribution:**</span></span>

```
ComputeBuffer cloudPointBuffer = new ComputeBuffer(6, quadPointsStride);
cloudPointBuffer.SetData(new[]
{
    new Vector2(-.5f, .5f),
    new Vector2(.5f, .5f),
    new Vector2(.5f, -.5f),
    new Vector2(.5f, -.5f),
    new Vector2(-.5f, -.5f),
    new Vector2(-.5f, .5f)
});
 
StructuredBuffer<float2> quadPoints;
StructuredBuffer<float3> particlePositions;
v2f vert(uint id : SV_VertexID, uint inst : SV_InstanceID)
{
    // Find the center of the quad, from local to world space
    float4 centerPoint = mul(unity_ObjectToWorld, float4(particlePositions[inst], 1));
 
    // Calculate y offset for each quad point
    float3 cameraForward = normalize(centerPoint - _WorldSpaceCameraPos);
    float y = dot(quadPoints[id].xy, cameraForward.xz);
 
    // Read out the particle data
    float radius = ...;
    float height = ...;
 
    // Set the position of the vert
    float4 finalPos = centerPoint + float4(quadPoints[id].x, y * height, quadPoints[id].y, 0) * radius;
    o.pos = mul(UNITY_MATRIX_VP, float4(finalPos.xyz, 1));
    o.uv = quadPoints[id].xy + 0.5;
 
    return o;
}
```

<span data-ttu-id="eb360-156">Poiché le particelle vengono ordinate in primo piano e si usa ancora uno shader di stile solido per ritagliare i pixel trasparenti (non Blend), questa tecnica gestisce una quantità sorprendente di particelle, evitando un costo eccessivo anche per i computer meno potenti.</span><span class="sxs-lookup"><span data-stu-id="eb360-156">Since we sort the particles front-to-back and we still used a solid style shader to clip (not blend) transparent pixels, this technique handles a surprising amount of particles, avoiding costly over-draw even on the lower-powered machines.</span></span>

## <a name="transparent-particle-clouds"></a><span data-ttu-id="eb360-157">Cloud di particelle trasparenti</span><span class="sxs-lookup"><span data-stu-id="eb360-157">Transparent particle clouds</span></span>

<span data-ttu-id="eb360-158">Le particelle solide forniscono una buona sensazione organica alla forma dei cloud, ma hanno comunque bisogno di qualcosa per vendere il lanosità di cloud.</span><span class="sxs-lookup"><span data-stu-id="eb360-158">The solid particles provided a good organic feel to the shape of the clouds but still needed something to sell the fluffiness of clouds.</span></span> <span data-ttu-id="eb360-159">Si è deciso di provare una soluzione personalizzata per le schede grafiche di fascia alta in cui è possibile introdurre la trasparenza.</span><span class="sxs-lookup"><span data-stu-id="eb360-159">We decided to try a custom solution for the high-end graphics cards where we can introduce transparency.</span></span>

<span data-ttu-id="eb360-160">A tale scopo, è sufficiente passare l'ordinamento iniziale delle particelle e modificare lo shader in modo da usare l'alfa delle trame.</span><span class="sxs-lookup"><span data-stu-id="eb360-160">To do this we simply switched the initial sorting order of the particles and changed the shader to use the textures alpha.</span></span>

![Cloud soffici](images/fluffy-clouds-700px.jpg)

<span data-ttu-id="eb360-162">Ha avuto un aspetto notevole, ma si è dimostrata troppo pesante anche per le macchine più dure, perché comporterebbe il rendering di ogni pixel sullo schermo centinaia di volte.</span><span class="sxs-lookup"><span data-stu-id="eb360-162">It looked great but proved to be too heavy for even the toughest machines since it would result in rendering each pixel on the screen hundreds of times!</span></span>

## <a name="render-off-screen-with-lower-resolution"></a><span data-ttu-id="eb360-163">Rendering fuori schermo con risoluzione inferiore</span><span class="sxs-lookup"><span data-stu-id="eb360-163">Render off-screen with lower resolution</span></span>

<span data-ttu-id="eb360-164">Per ridurre il numero di pixel di cui è stato eseguito il rendering dai cloud, abbiamo iniziato a eseguirne il rendering in un buffer di risoluzione trimestre (rispetto allo schermo) e allungando il risultato finale sullo schermo dopo che sono state disegnate tutte le particelle.</span><span class="sxs-lookup"><span data-stu-id="eb360-164">To reduce the number of pixels rendered by the clouds, we started rendering them in a quarter resolution buffer (compared to the screen) and stretching the end result back up onto the screen after all the particles had been drawn.</span></span> <span data-ttu-id="eb360-165">In questo modo è stato fornito approssimativamente un aumento di velocità di 4x, ma sono stati introdotti alcuni aspetti.</span><span class="sxs-lookup"><span data-stu-id="eb360-165">This gave us roughly a 4x speedup, but came with a couple of caveats.</span></span>

<span data-ttu-id="eb360-166">**Codice per il rendering fuori schermo:**</span><span class="sxs-lookup"><span data-stu-id="eb360-166">**Code for rendering off-screen:**</span></span>

```
cloudBlendingCommand = new CommandBuffer();
Camera.main.AddCommandBuffer(whenToComposite, cloudBlendingCommand);
 
cloudCamera.CopyFrom(Camera.main);
cloudCamera.rect = new Rect(0, 0, 1, 1);    //Adaptive rendering can set the main camera to a smaller rect
cloudCamera.clearFlags = CameraClearFlags.Color;
cloudCamera.backgroundColor = new Color(0, 0, 0, 1);
 
currentCloudTexture = RenderTexture.GetTemporary(Camera.main.pixelWidth / 2, Camera.main.pixelHeight / 2, 0);
cloudCamera.targetTexture = currentCloudTexture;
 
// Render clouds to the offscreen buffer
cloudCamera.Render();
cloudCamera.targetTexture = null;
 
// Blend low-res clouds to the main target
cloudBlendingCommand.Blit(currentCloudTexture, new RenderTargetIdentifier(BuiltinRenderTextureType.CurrentActive), blitMaterial);
```

<span data-ttu-id="eb360-167">Per prima cosa, quando si esegue il rendering in un buffer fuori schermo, abbiamo perso tutte le informazioni di profondità dalla nostra scena principale, ottenendo particelle dietro le montagne che si basano sulla montagna.</span><span class="sxs-lookup"><span data-stu-id="eb360-167">First, when rendering into an off-screen buffer, we lost all depth information from our main scene, resulting in particles behind mountains rendering on top of the mountain.</span></span>

<span data-ttu-id="eb360-168">In secondo luogo, l'estensione del buffer ha introdotto anche elementi sui bordi dei cloud in cui la modifica della risoluzione era evidente.</span><span class="sxs-lookup"><span data-stu-id="eb360-168">Second, stretching the buffer also introduced artifacts on the edges of our clouds where the resolution change was noticeable.</span></span> <span data-ttu-id="eb360-169">Nelle due sezioni successive viene illustrato il modo in cui sono stati risolti questi problemi.</span><span class="sxs-lookup"><span data-stu-id="eb360-169">The next two sections talk about how we resolved these issues.</span></span>

## <a name="particle-depth-buffer"></a><span data-ttu-id="eb360-170">Buffer profondità particella</span><span class="sxs-lookup"><span data-stu-id="eb360-170">Particle depth buffer</span></span>

<span data-ttu-id="eb360-171">Per fare in modo che le particelle coesistano con la geometria globale in cui una montagna o un oggetto può coprire le particelle sottostanti, è stato popolato il buffer fuori schermo con un buffer di profondità contenente la geometria della scena principale.</span><span class="sxs-lookup"><span data-stu-id="eb360-171">To make the particles co-exist with the world geometry where a mountain or object could cover particles behind it, we populated the off-screen buffer with a depth buffer containing the geometry of the main scene.</span></span> <span data-ttu-id="eb360-172">Per produrre tale buffer di profondità, è stata creata una seconda fotocamera, che consente di eseguire il rendering solo della geometria solida e della profondità della scena.</span><span class="sxs-lookup"><span data-stu-id="eb360-172">To produce such depth buffer, we created a second camera, rendering only the solid geometry and depth of the scene.</span></span>

<span data-ttu-id="eb360-173">È stata quindi usata la nuova trama nel pixel shader dei cloud per occludere pixel.</span><span class="sxs-lookup"><span data-stu-id="eb360-173">We then used the new texture in the pixel shader of the clouds to occlude pixels.</span></span> <span data-ttu-id="eb360-174">È stata usata la stessa trama per calcolare la distanza alla geometria dietro un pixel del cloud.</span><span class="sxs-lookup"><span data-stu-id="eb360-174">We used the same texture to calculate the distance to the geometry behind a cloud pixel.</span></span> <span data-ttu-id="eb360-175">Usando tale distanza e applicando l'alfa del pixel, ora si è verificato l'effetto dei cloud che si avvicinano al terreno, rimuovendo eventuali tagli rigidi in cui le particelle e il terreno soddisfano.</span><span class="sxs-lookup"><span data-stu-id="eb360-175">By using that distance and applying it to the alpha of the pixel, we now had the effect of clouds fading out as they get close to terrain, removing any hard cuts where particles and terrain meet.</span></span>

![Cloud combinati in un terreno](images/clouds-blended-to-terrain-700px.jpg)

## <a name="sharpening-the-edges"></a><span data-ttu-id="eb360-177">Affilatura dei bordi</span><span class="sxs-lookup"><span data-stu-id="eb360-177">Sharpening the edges</span></span>

<span data-ttu-id="eb360-178">I cloud estesi sembravano quasi identici ai cloud di dimensioni normali al centro delle particelle o dove si sovrappongono, ma mostravano alcuni artefatti ai bordi del cloud.</span><span class="sxs-lookup"><span data-stu-id="eb360-178">The stretched-up clouds looked almost identical to the normal size clouds at the center of the particles or where they overlapped, but showed some artifacts at the cloud edges.</span></span> <span data-ttu-id="eb360-179">In caso contrario, i bordi nitidi appaiono sfocati e sono stati introdotti gli effetti degli alias quando la fotocamera si sposta.</span><span class="sxs-lookup"><span data-stu-id="eb360-179">Otherwise sharp edges would appear blurry and alias effects were introduced when the camera moved.</span></span>

<span data-ttu-id="eb360-180">Per risolvere il problema, è possibile eseguire uno shader semplice sul buffer fuori schermo per determinare il punto in cui si è verificata una grande variazione di contrasto (1).</span><span class="sxs-lookup"><span data-stu-id="eb360-180">We solved this by running a simple shader on the off-screen buffer to determine where big changes in contrast occurred (1).</span></span> <span data-ttu-id="eb360-181">Si inseriscono i pixel con grandi modifiche in un nuovo buffer di stencil (2).</span><span class="sxs-lookup"><span data-stu-id="eb360-181">We put the pixels with big changes into a new stencil buffer (2).</span></span> <span data-ttu-id="eb360-182">È stato quindi usato il buffer dello stencil per mascherare queste aree a contrasto elevato quando si applica il buffer fuori schermo allo schermo, ottenendo buchi in e intorno ai cloud (3).</span><span class="sxs-lookup"><span data-stu-id="eb360-182">We then used the stencil buffer to mask out these high contrast areas when applying the off-screen buffer back to the screen, resulting in holes in and around the clouds (3).</span></span>

<span data-ttu-id="eb360-183">È stato quindi eseguito il rendering di tutte le particelle in modalità a schermo intero, ma questa volta usava il buffer dello stencil per mascherare tutti gli elementi, tranne i bordi, ottenendo un set minimo di pixel interessati (4).</span><span class="sxs-lookup"><span data-stu-id="eb360-183">We then rendered all the particles again in full-screen mode, but this time used the stencil buffer to mask out everything but the edges, resulting in a minimal set of pixels touched (4).</span></span> <span data-ttu-id="eb360-184">Poiché il buffer dei comandi era già stato creato per le particelle, era sufficiente eseguirne il rendering nella nuova fotocamera.</span><span class="sxs-lookup"><span data-stu-id="eb360-184">Since the command buffer was already created for the particles, we simply had to render it again to the new camera.</span></span>

![Progressione del rendering dei bordi del cloud](images/cloud-steps-1-4-700px.jpg)

<span data-ttu-id="eb360-186">Il risultato finale è costituito da bordi acuti con sezioni del centro a basso costo dei cloud.</span><span class="sxs-lookup"><span data-stu-id="eb360-186">The end result was sharp edges with cheap center sections of the clouds.</span></span>

<span data-ttu-id="eb360-187">Sebbene questa operazione fosse molto più rapida rispetto al rendering di tutte le particelle a schermo intero, c'è ancora un costo associato al test di un pixel sul buffer dello stencil.</span><span class="sxs-lookup"><span data-stu-id="eb360-187">While this was much faster than rendering all particles in full screen, there is still a cost associated with testing a pixel against the stencil buffer, so a massive amount of overdraw still came with a cost.</span></span>

## <a name="culling-particles"></a><span data-ttu-id="eb360-188">Eliminazione di particelle</span><span class="sxs-lookup"><span data-stu-id="eb360-188">Culling particles</span></span>

<span data-ttu-id="eb360-189">Per l'effetto vento, sono state generate strisce di triangolo lungo in un compute shader, creando molti WISP di vento nel mondo.</span><span class="sxs-lookup"><span data-stu-id="eb360-189">For our wind effect, we generated long triangle strips in a compute shader, creating many wisps of wind in the world.</span></span> <span data-ttu-id="eb360-190">Sebbene l'effetto vento non fosse pesante per la velocità di riempimento dovuta alle strisce skinny generate, ha prodotto molte centinaia di migliaia di vertici, causando un carico elevato per il vertex shader.</span><span class="sxs-lookup"><span data-stu-id="eb360-190">While the wind effect was not heavy on fill rate due to skinny strips generated, it produced many hundreds of thousands of vertices resulting in a heavy load for the vertex shader.</span></span>

<span data-ttu-id="eb360-191">Sono stati introdotti i buffer di accodamento nel compute shader per inserire un subset di strisce di vento da disegnare.</span><span class="sxs-lookup"><span data-stu-id="eb360-191">We introduced append buffers on the compute shader to feed a subset of the wind strips to be drawn.</span></span> <span data-ttu-id="eb360-192">Con una semplice visualizzazione della logica di eliminazione tronco in compute shader, è possibile determinare se una striscia era esterna alla visualizzazione della fotocamera e impedire che venga aggiunta al buffer di push.</span><span class="sxs-lookup"><span data-stu-id="eb360-192">With some simple view frustum culling logic in the compute shader, we could determine if a strip was outside of camera view and prevent it from being added to the push buffer.</span></span> <span data-ttu-id="eb360-193">Ciò ha ridotto significativamente la quantità di strisce, liberando alcuni cicli necessari sulla GPU.</span><span class="sxs-lookup"><span data-stu-id="eb360-193">This reduced the amount of strips significantly, freeing up some needed cycles on the GPU.</span></span>

<span data-ttu-id="eb360-194">**Codice che illustra un buffer di Accodamento:**</span><span class="sxs-lookup"><span data-stu-id="eb360-194">**Code demonstrating an append buffer:**</span></span>

<span data-ttu-id="eb360-195">*Compute Shader:*</span><span class="sxs-lookup"><span data-stu-id="eb360-195">*Compute shader:*</span></span>

```
AppendStructuredBuffer<int> culledParticleIdx;
 
if (show)
    culledParticleIdx.Append(id.x);
```

<span data-ttu-id="eb360-196">*C#codice*</span><span class="sxs-lookup"><span data-stu-id="eb360-196">*C# code:*</span></span>

```
protected void Awake() 
{
    // Create an append buffer, setting the maximum size and the contents stride length
    culledParticlesIdxBuffer = new ComputeBuffer(ParticleCount, sizeof(int), ComputeBufferType.Append);
 
    // Set up Args Buffer for Draw Procedural Indirect
    argsBuffer = new ComputeBuffer(4, sizeof(int), ComputeBufferType.IndirectArguments);
    argsBuffer.SetData(new int[] { DataVertCount, 0, 0, 0 });
}
 
protected void Update()
{
    // Reset the append buffer, and dispatch the compute shader normally
    culledParticlesIdxBuffer.SetCounterValue(0);
 
    computer.Dispatch(...)
 
    // Copy the append buffer count into the args buffer used by the Draw Procedural Indirect call
    ComputeBuffer.CopyCount(culledParticlesIdxBuffer, argsBuffer, dstOffset: 1);
    ribbonRenderCommand.DrawProceduralIndirect(Matrix4x4.identity, renderMaterial, 0, MeshTopology.Triangles, dataBuffer);
}
```

<span data-ttu-id="eb360-197">Si è provato a usare la stessa tecnica sulle particelle cloud, in cui è possibile eliminarle in compute shader e inserire solo le particelle visibili per il rendering.</span><span class="sxs-lookup"><span data-stu-id="eb360-197">We tried using the same technique on the cloud particles, where we would cull them on the compute shader and only push the visible particles to be rendered.</span></span> <span data-ttu-id="eb360-198">Questa tecnica in realtà non ci ha salvato molto sulla GPU poiché il collo di bottiglia più grande era la quantità di pixel di cui è stato eseguito il rendering sullo schermo e non il costo di calcolo dei vertici.</span><span class="sxs-lookup"><span data-stu-id="eb360-198">This technique actually did not save us much on the GPU since the biggest bottleneck was the amount pixels rendered on the screen, and not the cost of calculating the vertices.</span></span>

<span data-ttu-id="eb360-199">L'altro problema di questa tecnica è che il buffer di accodamento è stato popolato in ordine casuale a causa della natura parallela di calcolo delle particelle, causando la mancata ordinamento delle particelle ordinate, con conseguente sfarfallio delle particelle cloud.</span><span class="sxs-lookup"><span data-stu-id="eb360-199">The other problem with this technique was that the append buffer populated in random order due to its parallelized nature of computing the particles, causing the sorted particles to be un-sorted, resulting in flickering cloud particles.</span></span>

<span data-ttu-id="eb360-200">Esistono tecniche per ordinare il buffer di push, ma la quantità limitata di miglioramento delle prestazioni ottenuta dall'abbassamento di livello delle particelle verrebbe probabilmente sfalsata con un ordinamento aggiuntivo, quindi si è deciso di non eseguire questa ottimizzazione.</span><span class="sxs-lookup"><span data-stu-id="eb360-200">There are techniques to sort the push buffer, but the limited amount of performance gain we got out of culling particles would likely be offset with an additional sort, so we decided to not pursue this optimization.</span></span>

## <a name="adaptive-rendering"></a><span data-ttu-id="eb360-201">Rendering adattivo</span><span class="sxs-lookup"><span data-stu-id="eb360-201">Adaptive rendering</span></span>

<span data-ttu-id="eb360-202">Per garantire un framerate costante in un'app con diverse condizioni di rendering, ad esempio un Cloudy rispetto a una visualizzazione chiara, abbiamo introdotto il rendering adattivo per l'app.</span><span class="sxs-lookup"><span data-stu-id="eb360-202">To ensure a steady framerate on an app with varying rendering conditions like a cloudy vs a clear view, we introduced adaptive rendering to our app.</span></span>

<span data-ttu-id="eb360-203">Il primo passaggio del rendering adattivo consiste nella misurazione della GPU.</span><span class="sxs-lookup"><span data-stu-id="eb360-203">The first step of adaptive rendering is to measure GPU.</span></span> <span data-ttu-id="eb360-204">Questa operazione è stata apportata inserendo codice personalizzato nel buffer dei comandi della GPU all'inizio e alla fine di un frame di cui è stato eseguito il rendering, acquisendo l'ora dello schermo a sinistra e a destra.</span><span class="sxs-lookup"><span data-stu-id="eb360-204">We did this by inserting custom code into the GPU command buffer at the beginning and the end of a rendered frame, capturing both the left and right eye screen time.</span></span>

<span data-ttu-id="eb360-205">Misurando il tempo impiegato per il rendering e il confronto con la frequenza di aggiornamento desiderata, è stato rilevato il modo in cui è possibile eliminare i frame.</span><span class="sxs-lookup"><span data-stu-id="eb360-205">By measuring the time spent rendering and comparing it to our desired refresh-rate we got a sense of how close we were to dropping frames.</span></span>

<span data-ttu-id="eb360-206">Quando ci si avvicina alla rimozione di frame, il rendering viene adattato in modo da renderlo più veloce.</span><span class="sxs-lookup"><span data-stu-id="eb360-206">When close to dropping frames, we adapt our rendering to make it faster.</span></span> <span data-ttu-id="eb360-207">Un modo semplice per adattarsi è modificare la dimensione del viewport dello schermo, richiedendo meno pixel per il rendering.</span><span class="sxs-lookup"><span data-stu-id="eb360-207">One simple way of adapting is changing the viewport size of the screen, requiring less pixels to get rendered.</span></span>

<span data-ttu-id="eb360-208">Utilizzando *UnityEngine. XR. XRSettings. renderViewportScale* , il sistema compatta il viewport di destinazione e estende automaticamente il backup del risultato per adattarlo allo schermo.</span><span class="sxs-lookup"><span data-stu-id="eb360-208">By using *UnityEngine.XR.XRSettings.renderViewportScale* the system shrinks the targeted viewport and automatically stretches the result back up to fit the screen.</span></span> <span data-ttu-id="eb360-209">Una piccola modifica apportata alla scalabilità è difficilmente evidente sulla geometria globale e un fattore di scala 0,7 richiede metà della quantità di pixel di cui eseguire il rendering.</span><span class="sxs-lookup"><span data-stu-id="eb360-209">A small change in scale is barely noticeable on world geometry, and a scale factor of 0.7 requires half the amount of pixels to be rendered.</span></span>

![70% di scala, metà dei pixel](images/datascape-scaling-700px.jpg)

<span data-ttu-id="eb360-211">Quando si rileva che si sta per eliminare i frame, la scala viene ridotta di un numero fisso e viene rimossa quando viene eseguita di nuovo in modo rapido.</span><span class="sxs-lookup"><span data-stu-id="eb360-211">When we detect that we are about to drop frames we lower the scale by a fixed number, and increase it back when we are running fast enough again.</span></span>

<span data-ttu-id="eb360-212">Sebbene sia stata decisa la tecnica cloud da usare in base alle funzionalità grafiche dell'hardware all'avvio, è possibile basarlo sui dati della misurazione GPU per evitare che il sistema si trovi a bassa risoluzione per un lungo periodo di tempo, ma questo è un problema che non abbiamo avuto tempo  per esplorare in DataScape.</span><span class="sxs-lookup"><span data-stu-id="eb360-212">While we decided what cloud technique to use based on graphics capabilities of the hardware at startup, it is possible to base it on data from the GPU measurement to prevent the system from staying at low resolution for a long time, but this is something we did not have time to explore in Datascape.</span></span>

## <a name="final-thoughts"></a><span data-ttu-id="eb360-213">Considerazioni finali</span><span class="sxs-lookup"><span data-stu-id="eb360-213">Final thoughts</span></span>

<span data-ttu-id="eb360-214">La definizione di un'ampia gamma di hardware è impegnativa e richiede una pianificazione.</span><span class="sxs-lookup"><span data-stu-id="eb360-214">Targeting a variety of hardware is challenging and requires some planning.</span></span>

<span data-ttu-id="eb360-215">Si consiglia di iniziare a utilizzare computer con una gestione più bassa per acquisire familiarità con lo spazio del problema e sviluppare una soluzione di backup che viene eseguita su tutti i computer.</span><span class="sxs-lookup"><span data-stu-id="eb360-215">We recommend that you start targeting lower-powered machines to get familiar with the problem space and develop a backup solution that will run on all your machines.</span></span> <span data-ttu-id="eb360-216">Progettare la soluzione tenendo presente la velocità di riempimento, dal momento che i pixel saranno la risorsa più preziosa.</span><span class="sxs-lookup"><span data-stu-id="eb360-216">Design your solution with fill rate in mind, since pixels will be your most precious resource.</span></span> <span data-ttu-id="eb360-217">Specificare come destinazione una geometria solida rispetto alla trasparenza.</span><span class="sxs-lookup"><span data-stu-id="eb360-217">Target solid geometry over transparency.</span></span>

<span data-ttu-id="eb360-218">Con una soluzione di backup, è quindi possibile avviare la sovrapposizione in modo più complesso per i computer di fascia alta o forse semplicemente migliorare la risoluzione della soluzione di backup.</span><span class="sxs-lookup"><span data-stu-id="eb360-218">With a backup solution, you can then start layering in more complexity for high end machines or maybe just enhance resolution of your backup solution.</span></span>

<span data-ttu-id="eb360-219">Progettare per scenari peggiori e forse prendere in considerazione l'uso del rendering adattivo per situazioni complesse.</span><span class="sxs-lookup"><span data-stu-id="eb360-219">Design for worst case scenarios, and maybe consider using adaptive rendering for heavy situations.</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="eb360-220">Informazioni sugli autori</span><span class="sxs-lookup"><span data-stu-id="eb360-220">About the authors</span></span>

<table style="border:0">
<tr>
<td style="border:0" width="60px"><img alt="Picture of Robert Ferrese" width="60" height="60" src="images/robert-ferrese-60px.jpg"></td>
<td style="border:0"><span data-ttu-id="eb360-221"><b>Robert Ferrese</b></span><span class="sxs-lookup"><span data-stu-id="eb360-221"><b>Robert Ferrese</b></span></span><br><span data-ttu-id="eb360-222">Software Engineer@Microsoft</span><span class="sxs-lookup"><span data-stu-id="eb360-222">Software engineer @Microsoft</span></span></td>
</tr>
<tr>
<td style="border:0" width="60px"><img alt="Picture of Dan Andersson" width="60" height="60" src="images/dan-andersson-60px.jpg"></td>
<td style="border:0"><span data-ttu-id="eb360-223"><b>Dan Andersson</b></span><span class="sxs-lookup"><span data-stu-id="eb360-223"><b>Dan Andersson</b></span></span><br><span data-ttu-id="eb360-224">Software Engineer@Microsoft</span><span class="sxs-lookup"><span data-stu-id="eb360-224">Software engineer @Microsoft</span></span></td>
</tr>
</table>


## <a name="see-also"></a><span data-ttu-id="eb360-225">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="eb360-225">See also</span></span>
* [<span data-ttu-id="eb360-226">Informazioni sulle prestazioni per la realtà mista</span><span class="sxs-lookup"><span data-stu-id="eb360-226">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="eb360-227">Suggerimenti sulle prestazioni per Unity</span><span class="sxs-lookup"><span data-stu-id="eb360-227">Performance Recommendations for Unity</span></span>](performance-recommendations-for-unity.md)

 

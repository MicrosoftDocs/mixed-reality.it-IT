---
title: Case study - ridimensionamento Datascape tra i dispositivi con prestazioni diverse
description: Questo case study offre informazioni dettagliate su come gli sviluppatori Microsoft ottimizzare l'app Datascape per offrire un'esperienza coinvolgente per più dispositivi con una gamma di funzionalità delle prestazioni.
author: danandersson
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: visore VR immersivi, case study di ottimizzazione, VR, sulle prestazioni
ms.openlocfilehash: 990a5ee6de07b6416e3150a7885220409a9c8d93
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604870"
---
# <a name="case-study---scaling-datascape-across-devices-with-different-performance"></a><span data-ttu-id="6059a-104">Case study - ridimensionamento Datascape tra i dispositivi con prestazioni diverse</span><span class="sxs-lookup"><span data-stu-id="6059a-104">Case study - Scaling Datascape across devices with different performance</span></span>

<span data-ttu-id="6059a-105">Datascape è un'applicazione di realtà mista di Windows sviluppata internamente presso Microsoft in cui ci siamo concentrati sulla visualizzazione dei dati meteo sui dati di terreno.</span><span class="sxs-lookup"><span data-stu-id="6059a-105">Datascape is a Windows Mixed Reality application developed internally at Microsoft where we focused on displaying weather data on top of terrain data.</span></span> <span data-ttu-id="6059a-106">L'applicazione illustra le informazioni dettagliate esclusive gli utenti di ottenere dall'individuazione dei dati nella realtà mista racchiudendo l'utente con visualizzazione olografica.</span><span class="sxs-lookup"><span data-stu-id="6059a-106">The application explores the unique insights users gain from discovering data in mixed reality by surrounding the user with holographic data visualization.</span></span>

<span data-ttu-id="6059a-107">Per Datascape volevamo un'ampia gamma di piattaforme di destinazione con un hardware diverso che spaziano da Microsoft HoloLens a auricolari coinvolgenti di realtà mista di Windows e dai meno potenti PC per i PC più recenti con GPU di fascia alta.</span><span class="sxs-lookup"><span data-stu-id="6059a-107">For Datascape we wanted to target a variety of platforms with different hardware capabilities ranging from Microsoft HoloLens to Windows Mixed Reality immersive headsets, and from lower-powered PCs to the very latest PCs with high-end GPU.</span></span> <span data-ttu-id="6059a-108">Il problema principale è costituita dal rendering la scena in pochi visivamente accattivanti nei dispositivi con le funzionalità di grafica diversa durante l'esecuzione di un'elevata frequenza dei fotogrammi.</span><span class="sxs-lookup"><span data-stu-id="6059a-108">The main challenge was rendering our scene in a visually appealing matter on devices with wildly different graphics capabilities while executing at a high framerate.</span></span>

<span data-ttu-id="6059a-109">Questo case study in dettaglio il processo e le tecniche usate per creare alcuni dei nostri sistemi più intensivo GPU, che descrive i problemi che si sono verificati e come abbiamo superato.</span><span class="sxs-lookup"><span data-stu-id="6059a-109">This case study will walk through the process and techniques used to create some of our more GPU-intensive systems, describing the problems we encountered and how we overcame them.</span></span>

## <a name="transparency-and-overdraw"></a><span data-ttu-id="6059a-110">La trasparenza ed estenda</span><span class="sxs-lookup"><span data-stu-id="6059a-110">Transparency and overdraw</span></span>

<span data-ttu-id="6059a-111">La difficoltà principale per il rendering è trattata la trasparenza, poiché la trasparenza può essere costosa su una GPU.</span><span class="sxs-lookup"><span data-stu-id="6059a-111">Our main rendering struggles dealt with transparency, since transparency can be expensive on a GPU.</span></span>

<span data-ttu-id="6059a-112">La geometria solida possibile eseguire il rendering da fronte a retro durante la scrittura nel buffer di profondità, arrestare qualsiasi pixel futuri che si trova dietro tale pixel da vengano eliminati.</span><span class="sxs-lookup"><span data-stu-id="6059a-112">Solid geometry can be rendered front to back while writing to the depth buffer, stopping any future pixels located behind that pixel from being discarded.</span></span> <span data-ttu-id="6059a-113">Ciò impedisce l'esecuzione del pixel shader, velocizzando significativamente il processo di pixel nascosto.</span><span class="sxs-lookup"><span data-stu-id="6059a-113">This prevents hidden pixels from executing the pixel shader, speeding up the process significantly.</span></span> <span data-ttu-id="6059a-114">Se la geometria è ordinata in modo ottimale, ogni pixel sullo schermo verrà disegnata una sola volta.</span><span class="sxs-lookup"><span data-stu-id="6059a-114">If geometry is sorted optimally, each pixel on the screen will be drawn only once.</span></span>

<span data-ttu-id="6059a-115">Esigenze di geometria trasparente da ordinare nuovamente in primo piano e si basa su fusione l'output del pixel shader pixel sullo schermo corrente.</span><span class="sxs-lookup"><span data-stu-id="6059a-115">Transparent geometry needs to be sorted back to front and relies on blending the output of the pixel shader to the current pixel on the screen.</span></span> <span data-ttu-id="6059a-116">Ciò può comportare ogni pixel sullo schermo viene disegnato di più volte per ogni fotogramma, noto come caricamento.</span><span class="sxs-lookup"><span data-stu-id="6059a-116">This can result in each pixel on the screen being drawn to multiple times per frame, referred to as overdraw.</span></span>

<span data-ttu-id="6059a-117">Per HoloLens e PC "Mainstream", la schermata è possibile compilare solo un numero limitato di volte, rendendo trasparente per il rendering problematico.</span><span class="sxs-lookup"><span data-stu-id="6059a-117">For HoloLens and mainstream PCs, the screen can only be filled a handful of times, making transparent rendering problematic.</span></span>

## <a name="introduction-to-datascape-scene-components"></a><span data-ttu-id="6059a-118">Introduzione ai componenti di scena Datascape</span><span class="sxs-lookup"><span data-stu-id="6059a-118">Introduction to Datascape scene components</span></span>

<span data-ttu-id="6059a-119">Avevamo tre componenti principali per la scena; **l'interfaccia utente, la mappa**, e **meteo**.</span><span class="sxs-lookup"><span data-stu-id="6059a-119">We had three major components to our scene; **the UI, the map**, and **the weather**.</span></span> <span data-ttu-id="6059a-120">Sapevamo sin dall'inizio che l'effetti meteo richiede tutto il tempo GPU è stato possibile ottenere, in modo che è intenzionalmente progettata l'interfaccia utente e un terreno in modo che consentirebbe di ridurre qualsiasi di carica presente.</span><span class="sxs-lookup"><span data-stu-id="6059a-120">We knew early on that our weather effects would require all the GPU time it could get, so we purposely designed the UI and terrain in a way that would reduce any overdraw.</span></span>

<span data-ttu-id="6059a-121">L'interfaccia utente viene rielaborata più volte per ridurre al minimo la quantità di caricamento produrrebbe.</span><span class="sxs-lookup"><span data-stu-id="6059a-121">We reworked the UI several times to minimize the amount of overdraw it would produce.</span></span> <span data-ttu-id="6059a-122">Abbiamo sbagliato a fianco geometrie più complesse invece di sovrimpressione grafica trasparente uno sopra l'altro per i componenti, ad esempio panoramiche brillante pulsanti e della mappa.</span><span class="sxs-lookup"><span data-stu-id="6059a-122">We erred on the side of more complex geometry rather than overlaying transparent art on top of each other for components like glowing buttons and map overviews.</span></span>

<span data-ttu-id="6059a-123">Per la mappa, è stato usato uno shader personalizzato che potrebbe eliminare le funzionalità standard di Unity, ad esempio variazioni di luminosità e illuminazione complesse, sostituirli con un modello di illuminazione semplice sun singolo e un calcolo nebbia personalizzato.</span><span class="sxs-lookup"><span data-stu-id="6059a-123">For the map, we used a custom shader that would strip out standard Unity features such as shadows and complex lighting, replacing them with a simple single sun lighting model and a custom fog calculation.</span></span> <span data-ttu-id="6059a-124">Questo prodotto un pixel shader semplice e liberare cicli di GPU.</span><span class="sxs-lookup"><span data-stu-id="6059a-124">This produced a simple pixel shader and free up GPU cycles.</span></span>

<span data-ttu-id="6059a-125">Siamo riusciti a ottenere l'interfaccia utente sia la mappa per il rendering in budget in cui non era necessario qualsiasi di tali modifiche a seconda dell'hardware; Tuttavia, la visualizzazione meteo, in particolare il rendering cloud, ha dimostrato di essere più complesso.</span><span class="sxs-lookup"><span data-stu-id="6059a-125">We managed to get both the UI and the map to rendering at budget where we did not need any changes to them depending on the hardware; however, the weather visualization, in particular the cloud rendering, proved to be more of a challenge!</span></span>

## <a name="background-on-cloud-data"></a><span data-ttu-id="6059a-126">Informazioni generali su dati nel cloud</span><span class="sxs-lookup"><span data-stu-id="6059a-126">Background on cloud data</span></span>

<span data-ttu-id="6059a-127">I dati nel cloud è stati scaricati dai server NOAA (http://nomads.ncep.noaa.gov/) e siamo arrivati in tre livelli 2D distinti, ognuno con l'altezza superiore e inferiore del cloud, nonché la densità del cloud per ogni cella della griglia.</span><span class="sxs-lookup"><span data-stu-id="6059a-127">Our cloud data was downloaded from NOAA servers (http://nomads.ncep.noaa.gov/) and came to us in three distinct 2D layers, each with the top and bottom height of the cloud, as well as the density of the cloud for each cell of the grid.</span></span> <span data-ttu-id="6059a-128">I dati è stati elaborati in una trama di informazioni sul cloud in cui ogni componente è stato archiviato nel componente rosso, verde e blu della trama per semplificare l'accesso nella GPU.</span><span class="sxs-lookup"><span data-stu-id="6059a-128">The data got processed into a cloud info texture where each component was stored in the red, green, and blue component of the texture for easy access on the GPU.</span></span>

## <a name="geometry-clouds"></a><span data-ttu-id="6059a-129">Cloud di geometria</span><span class="sxs-lookup"><span data-stu-id="6059a-129">Geometry clouds</span></span>

<span data-ttu-id="6059a-130">Per assicurarsi che i computer con un minore è stato possibile eseguire il rendering nostro cloud abbiamo deciso di iniziare con un approccio che usa la geometria solida per ridurre al minimo estenda.</span><span class="sxs-lookup"><span data-stu-id="6059a-130">To make sure our lower-powered machines could render our clouds we decided to start with an approach that would use solid geometry to minimize overdraw.</span></span>

<span data-ttu-id="6059a-131">Innanzitutto, abbiamo provato producendo cloud tramite la generazione di una rete mesh di heightmap a tinta unita per ogni livello utilizzando il raggio della trama informazioni sul cloud per ogni vertice per generare la forma.</span><span class="sxs-lookup"><span data-stu-id="6059a-131">We first tried producing clouds by generating a solid heightmap mesh for each layer using the radius of the cloud info texture per vertex to generate the shape.</span></span> <span data-ttu-id="6059a-132">Abbiamo utilizzato un geometry shader per produrre i vertici sia nella parte superiore e inferiore del cloud genera forme cloud solida.</span><span class="sxs-lookup"><span data-stu-id="6059a-132">We used a geometry shader to produce the vertices both at the top and the bottom of the cloud generating solid cloud shapes.</span></span> <span data-ttu-id="6059a-133">Viene utilizzato il valore di densità dalla trama per colorare il cloud con i colori più scuri per più cloud ad alta densità.</span><span class="sxs-lookup"><span data-stu-id="6059a-133">We used the density value from the texture to color the cloud with darker colors for more dense clouds.</span></span>

<span data-ttu-id="6059a-134">**Shader per la creazione dei vertici:**</span><span class="sxs-lookup"><span data-stu-id="6059a-134">**Shader for creating the vertices:**</span></span>

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

<span data-ttu-id="6059a-135">È stata introdotta una serie di piccoli disturbi per ottenere altri dettagli su dati reali.</span><span class="sxs-lookup"><span data-stu-id="6059a-135">We introduced a small noise pattern to get more detail on top of the real data.</span></span> <span data-ttu-id="6059a-136">Per produrre i bordi arrotondati cloud, viene troncato il pixel nel pixel shader quando il valore del raggio interpolata raggiunge una soglia per rimuovere valori vicino a zero.</span><span class="sxs-lookup"><span data-stu-id="6059a-136">To produce round cloud edges, we clipped the pixels in the pixel shader when the interpolated radius value hit a threshold to discard near-zero values.</span></span>

![Cloud di geometria](images/datascape-geometry-clouds-700px.jpg)

<span data-ttu-id="6059a-138">Poiché i cloud sono la geometria solida, sia possibile eseguirne il rendering prima del terreno per nascondere tutti i pixel che mappa costose sotto per migliorare ulteriormente la frequenza dei fotogrammi.</span><span class="sxs-lookup"><span data-stu-id="6059a-138">Since the clouds are solid geometry, they can be rendered before the terrain to hide any expensive map pixels underneath to further improve framerate.</span></span> <span data-ttu-id="6059a-139">Questa soluzione è stata eseguita correttamente in tutte le schede di grafica da min-spec alle schede di grafica di alto livello, nonché su HoloLens, a causa dell'approccio di rendering della geometria solida.</span><span class="sxs-lookup"><span data-stu-id="6059a-139">This solution ran well on all graphics cards from min-spec to high-end graphics cards, as well as on HoloLens, because of the solid geometry rendering approach.</span></span>

## <a name="solid-particle-clouds"></a><span data-ttu-id="6059a-140">Cloud particella a tinta unita</span><span class="sxs-lookup"><span data-stu-id="6059a-140">Solid particle clouds</span></span>

<span data-ttu-id="6059a-141">Avevamo ora una soluzione di backup che prodotta una ragionevole rappresentazione dei dati cloud, ma è stato un po' lackluster nel fattore di "wow" e non è stato conferiscono il volumetrici si ritiene che volevamo per i computer di fascia alta.</span><span class="sxs-lookup"><span data-stu-id="6059a-141">We now had a backup solution that produced a decent representation of our cloud data, but was a bit lackluster in the “wow” factor and did not convey the volumetric feel that we wanted for our high-end machines.</span></span>

<span data-ttu-id="6059a-142">Il passaggio successivo è stato creazione i cloud che essi rappresentano con circa 100.000 particelle per produrre un aspetto più organico e volumetrico.</span><span class="sxs-lookup"><span data-stu-id="6059a-142">Our next step was creating the clouds by representing them with approximately 100,000 particles to produce a more organic and volumetric look.</span></span>

<span data-ttu-id="6059a-143">Se le particelle rimangono solide e ordinare parte anteriore a quella posteriore, è possibile trarre comunque vantaggio dai profondità buffer della faccia posteriore dei pixel dietro le particelle precedentemente sottoposti a rendering, riducendo il caricamento.</span><span class="sxs-lookup"><span data-stu-id="6059a-143">If particles stay solid and sort front-to-back, we can still benefit from depth buffer culling of the pixels behind previously rendered particles, reducing the overdraw.</span></span> <span data-ttu-id="6059a-144">Inoltre, con una soluzione basata su particella, è possibile modificare la quantità di particelle utilizzato su hardware diverso di destinazione.</span><span class="sxs-lookup"><span data-stu-id="6059a-144">Also, with a particle-based solution, we can alter the amount of particles used to target different hardware.</span></span> <span data-ttu-id="6059a-145">Tuttavia, tutti i pixel è comunque necessario essere testata profondità, determinando un overhead aggiuntivo.</span><span class="sxs-lookup"><span data-stu-id="6059a-145">However, all pixels still need to be depth tested, which results in some additional overhead.</span></span>

<span data-ttu-id="6059a-146">Sono stati creati dapprima, posizioni delle particelle intorno al punto centrale dell'esperienza all'avvio.</span><span class="sxs-lookup"><span data-stu-id="6059a-146">First, we created particle positions around the center point of the experience at startup.</span></span> <span data-ttu-id="6059a-147">Abbiamo distribuito le particelle più efficiente la capacità intorno al centro e meno così la distanza.</span><span class="sxs-lookup"><span data-stu-id="6059a-147">We distributed the particles more densely around the center and less so in the distance.</span></span> <span data-ttu-id="6059a-148">Tutte le particelle dal centro nella parte posteriore è pre-ordinamento in modo che renda prima di tutto le particelle più vicino.</span><span class="sxs-lookup"><span data-stu-id="6059a-148">We pre-sorted all particles from the center to the back so that the closest particles would render first.</span></span>

<span data-ttu-id="6059a-149">Un compute shader sarebbe campione trama informazioni sul cloud per posizionare ogni particella a un'altezza corretto colore in base la densità.</span><span class="sxs-lookup"><span data-stu-id="6059a-149">A compute shader would sample the cloud info texture to position each particle at a correct height and color it based on the density.</span></span>

<span data-ttu-id="6059a-150">È stato usato *DrawProcedural* per eseguire il rendering di un quadrato per ogni particella consentendone la particella restare sempre aggiornato riguardo la GPU in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="6059a-150">We used *DrawProcedural* to render a quad per particle allowing the particle data to stay on the GPU at all times.</span></span>

<span data-ttu-id="6059a-151">Ogni particella contenuta sia un'altezza e un raggio.</span><span class="sxs-lookup"><span data-stu-id="6059a-151">Each particle contained both a height and a radius.</span></span> <span data-ttu-id="6059a-152">L'altezza è stato in base ai cloud dati campionati dalla trama informazioni sul cloud e il raggio si basava sulla distribuzione iniziale in cui viene calcolato per archiviare la distanza orizzontale per il nodo più vicino.</span><span class="sxs-lookup"><span data-stu-id="6059a-152">The height was based on the cloud data sampled from the cloud info texture, and the radius was based on the initial distribution where it would be calculated to store the horizontal distance to its closest neighbor.</span></span> <span data-ttu-id="6059a-153">I quadrati utilizzerà questi dati per orientarsi meglio all'interno di se stesso con angolazione dall'altezza, in modo che quando utenti esaminano in senso orizzontale, verranno visualizzato l'altezza e rientrerebbero quando gli utenti preso in esame, dall'alto in basso, l'area compresa tra gli elementi adiacenti.</span><span class="sxs-lookup"><span data-stu-id="6059a-153">The quads would use this data to orient itself angled by the height so that when users look at it horizontally, the height would be shown, and when users looked at it top-down, the area between its neighbors would be covered.</span></span>

![Forma particella](images/particle-shape-700px.png)

<span data-ttu-id="6059a-155">**Codice dello shader che illustra la distribuzione:**</span><span class="sxs-lookup"><span data-stu-id="6059a-155">**Shader code showing the distribution:**</span></span>

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

<span data-ttu-id="6059a-156">Poiché Ordiniamo le particelle parte anteriore a quella posteriore e viene ancora usato uno shader a tinta unita con stile ai pixel trasparenti clip (blend non), questa tecnica consente di gestire una quantità sorprendente di particelle, evitando costosa disegno eccessivo anche nei computer con un minore.</span><span class="sxs-lookup"><span data-stu-id="6059a-156">Since we sort the particles front-to-back and we still used a solid style shader to clip (not blend) transparent pixels, this technique handles a surprising amount of particles, avoiding costly over-draw even on the lower-powered machines.</span></span>

## <a name="transparent-particle-clouds"></a><span data-ttu-id="6059a-157">Cloud particella trasparente</span><span class="sxs-lookup"><span data-stu-id="6059a-157">Transparent particle clouds</span></span>

<span data-ttu-id="6059a-158">Le particelle solide fornito organica ottimali per la forma dei cloud ma comunque bisogno di qualcosa di vendere fluffiness di cloud.</span><span class="sxs-lookup"><span data-stu-id="6059a-158">The solid particles provided a good organic feel to the shape of the clouds but still needed something to sell the fluffiness of clouds.</span></span> <span data-ttu-id="6059a-159">Abbiamo deciso di provare a una soluzione personalizzata per le schede di grafica di alto livello in cui è possibile introdurre la trasparenza.</span><span class="sxs-lookup"><span data-stu-id="6059a-159">We decided to try a custom solution for the high-end graphics cards where we can introduce transparency.</span></span>

<span data-ttu-id="6059a-160">A tale scopo è semplicemente passata l'ordinamento iniziale delle particelle e modificare lo shader per utilizzare il canale alfa di trame.</span><span class="sxs-lookup"><span data-stu-id="6059a-160">To do this we simply switched the initial sorting order of the particles and changed the shader to use the textures alpha.</span></span>

![Fluffy cloud](images/fluffy-clouds-700px.jpg)

<span data-ttu-id="6059a-162">Che era eccezionale ma si è rivelata troppo pesante per anche le macchine più complesse perché il risultato sarà il rendering di ogni pixel sullo schermo centinaia di volte!</span><span class="sxs-lookup"><span data-stu-id="6059a-162">It looked great but proved to be too heavy for even the toughest machines since it would result in rendering each pixel on the screen hundreds of times!</span></span>

## <a name="render-off-screen-with-lower-resolution"></a><span data-ttu-id="6059a-163">Eseguire il rendering fuori schermo con risoluzione inferiore</span><span class="sxs-lookup"><span data-stu-id="6059a-163">Render off-screen with lower resolution</span></span>

<span data-ttu-id="6059a-164">Per ridurre il numero di pixel sottoposti a rendering per il cloud, abbiamo iniziato a essi per il rendering nel buffer di risoluzione di un trimestre (rispetto alla schermata) e l'adattamento il risultato finale il backup sullo schermo, dopo che tutte le particelle erano state disegnate.</span><span class="sxs-lookup"><span data-stu-id="6059a-164">To reduce the number of pixels rendered by the clouds, we started rendering them in a quarter resolution buffer (compared to the screen) and stretching the end result back up onto the screen after all the particles had been drawn.</span></span> <span data-ttu-id="6059a-165">Questo ci ha offerto più o meno un aumento della velocità 4 x, ma integrava un paio di aspetti.</span><span class="sxs-lookup"><span data-stu-id="6059a-165">This gave us roughly a 4x speedup, but came with a couple of caveats.</span></span>

<span data-ttu-id="6059a-166">**Codice per il rendering fuori schermo:**</span><span class="sxs-lookup"><span data-stu-id="6059a-166">**Code for rendering off-screen:**</span></span>

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

<span data-ttu-id="6059a-167">In primo luogo, durante il rendering in un buffer fuori schermo, abbiamo perdita di tutte le informazioni di profondità dal nostro scena principale, conseguente particelle dietro montagne rendering nella parte superiore di mountain.</span><span class="sxs-lookup"><span data-stu-id="6059a-167">First, when rendering into an off-screen buffer, we lost all depth information from our main scene, resulting in particles behind mountains rendering on top of the mountain.</span></span>

<span data-ttu-id="6059a-168">In secondo luogo, l'adattamento del buffer sono stati introdotti gli elementi sui bordi dei nostri cloud in cui la modifica di risoluzione è evidente.</span><span class="sxs-lookup"><span data-stu-id="6059a-168">Second, stretching the buffer also introduced artifacts on the edges of our clouds where the resolution change was noticeable.</span></span> <span data-ttu-id="6059a-169">Due sezioni successive parleremo di come è stato risolto questi problemi.</span><span class="sxs-lookup"><span data-stu-id="6059a-169">The next two sections talk about how we resolved these issues.</span></span>

## <a name="particle-depth-buffer"></a><span data-ttu-id="6059a-170">Buffer profondità particella</span><span class="sxs-lookup"><span data-stu-id="6059a-170">Particle depth buffer</span></span>

<span data-ttu-id="6059a-171">Per rendere le particelle coesiste con la geometria del mondo in cui un oggetto o mountain può coprire le particelle dietro di essa, viene popolato il buffer fuori schermo con un buffer di profondità contenente la geometria della scena principale.</span><span class="sxs-lookup"><span data-stu-id="6059a-171">To make the particles co-exist with the world geometry where a mountain or object could cover particles behind it, we populated the off-screen buffer with a depth buffer containing the geometry of the main scene.</span></span> <span data-ttu-id="6059a-172">Per generare tale buffer di profondità, abbiamo creato una fotocamera secondo, il rendering solo la geometria solida e profondità della scena.</span><span class="sxs-lookup"><span data-stu-id="6059a-172">To produce such depth buffer, we created a second camera, rendering only the solid geometry and depth of the scene.</span></span>

<span data-ttu-id="6059a-173">La nuova trama viene quindi utilizzato nel pixel shader dei cloud per nasconde i colori pixel.</span><span class="sxs-lookup"><span data-stu-id="6059a-173">We then used the new texture in the pixel shader of the clouds to occlude pixels.</span></span> <span data-ttu-id="6059a-174">Abbiamo utilizzato la trama stessa per calcolare la distanza di geometria dietro a un pixel di cloud.</span><span class="sxs-lookup"><span data-stu-id="6059a-174">We used the same texture to calculate the distance to the geometry behind a cloud pixel.</span></span> <span data-ttu-id="6059a-175">Utilizzando tale distanza e applicarlo al valore alfa del pixel, avevamo a questo punto l'effetto dei cloud dissolvenza in uscita mano a mano che vicino al terreno, la rimozione di qualsiasi disco rigidi tagli incontro tra le particelle e terreno.</span><span class="sxs-lookup"><span data-stu-id="6059a-175">By using that distance and applying it to the alpha of the pixel, we now had the effect of clouds fading out as they get close to terrain, removing any hard cuts where particles and terrain meet.</span></span>

![Cloud devono essere smussati nel terreno](images/clouds-blended-to-terrain-700px.jpg)

## <a name="sharpening-the-edges"></a><span data-ttu-id="6059a-177">Aumento della nitidezza bordi</span><span class="sxs-lookup"><span data-stu-id="6059a-177">Sharpening the edges</span></span>

<span data-ttu-id="6059a-178">I cloud esteso-up era quasi identici per i cloud di dimensioni normali il fulcro delle particelle o in cui sono sovrapposte, ma ha illustrato alcuni elementi in corrispondenza dei bordi cloud.</span><span class="sxs-lookup"><span data-stu-id="6059a-178">The stretched-up clouds looked almost identical to the normal size clouds at the center of the particles or where they overlapped, but showed some artifacts at the cloud edges.</span></span> <span data-ttu-id="6059a-179">In caso contrario bordi sharp apparirebbe sfocati e sono stati introdotti gli effetti di alias quando spostato la fotocamera.</span><span class="sxs-lookup"><span data-stu-id="6059a-179">Otherwise sharp edges would appear blurry and alias effects were introduced when the camera moved.</span></span>

<span data-ttu-id="6059a-180">Abbiamo risolto questo problema eseguendo un semplice shader nel buffer fuori schermo per determinare dove notevoli modifiche invece si è verificato un (1).</span><span class="sxs-lookup"><span data-stu-id="6059a-180">We solved this by running a simple shader on the off-screen buffer to determine where big changes in contrast occurred (1).</span></span> <span data-ttu-id="6059a-181">Abbiamo inserito i pixel con notevoli modifiche in un nuovo buffer di stencil (2).</span><span class="sxs-lookup"><span data-stu-id="6059a-181">We put the pixels with big changes into a new stencil buffer (2).</span></span> <span data-ttu-id="6059a-182">Successivamente, abbiamo utilizzato il buffer di stencil per nascondere le aree a contrasto elevato quando si applica il buffer fuori schermo nella schermata di conseguente fori e tutto il cloud (3).</span><span class="sxs-lookup"><span data-stu-id="6059a-182">We then used the stencil buffer to mask out these high contrast areas when applying the off-screen buffer back to the screen, resulting in holes in and around the clouds (3).</span></span>

<span data-ttu-id="6059a-183">Abbiamo quindi tutte le particelle eseguire nuovamente il rendering in modalità schermo intero, ma questa volta utilizzato il buffer di stencil per nascondere tutti gli elementi, ma i bordi, risultante in un set minimo di pixel tocca (4).</span><span class="sxs-lookup"><span data-stu-id="6059a-183">We then rendered all the particles again in full-screen mode, but this time used the stencil buffer to mask out everything but the edges, resulting in a minimal set of pixels touched (4).</span></span> <span data-ttu-id="6059a-184">Poiché il buffer dei comandi è stata già creato per le particelle, abbiamo dovuto semplicemente eseguirne il rendering nuovamente alla nuova fotocamera.</span><span class="sxs-lookup"><span data-stu-id="6059a-184">Since the command buffer was already created for the particles, we simply had to render it again to the new camera.</span></span>

![Progressione di rendering cloud bordi](images/cloud-steps-1-4-700px.jpg)

<span data-ttu-id="6059a-186">Il risultato finale era ben strutturati bordi con sezioni center ed economici del cloud.</span><span class="sxs-lookup"><span data-stu-id="6059a-186">The end result was sharp edges with cheap center sections of the clouds.</span></span>

<span data-ttu-id="6059a-187">Mentre questo era molto più veloce rispetto a rendering tutte le particelle nel schermo intero, esiste comunque un costo associato con il test di un pixel con buffer di stencil, in modo che estenda ancora di una notevole quantità di fornito con un costo.</span><span class="sxs-lookup"><span data-stu-id="6059a-187">While this was much faster than rendering all particles in full screen, there is still a cost associated with testing a pixel against the stencil buffer, so a massive amount of overdraw still came with a cost.</span></span>

## <a name="culling-particles"></a><span data-ttu-id="6059a-188">Le particelle della faccia posteriore</span><span class="sxs-lookup"><span data-stu-id="6059a-188">Culling particles</span></span>

<span data-ttu-id="6059a-189">L'effetto del vento, viene generato lungo le strisce di triangoli in un compute shader, creazione di valore molti del vento in tutto il mondo.</span><span class="sxs-lookup"><span data-stu-id="6059a-189">For our wind effect, we generated long triangle strips in a compute shader, creating many wisps of wind in the world.</span></span> <span data-ttu-id="6059a-190">Mentre l'effetto del vento non era impegnativa velocità di riempimento a causa di strisce skinny generato, ha prodotto molte centinaia di migliaia di vertici generino un carico eccessivo per vertex shader.</span><span class="sxs-lookup"><span data-stu-id="6059a-190">While the wind effect was not heavy on fill rate due to skinny strips generated, it produced many hundreds of thousands of vertices resulting in a heavy load for the vertex shader.</span></span>

<span data-ttu-id="6059a-191">È stato introdotto accodare buffer presenti a del compute shader per inserire un sottoinsieme delle strisce wind da disegnare.</span><span class="sxs-lookup"><span data-stu-id="6059a-191">We introduced append buffers on the compute shader to feed a subset of the wind strips to be drawn.</span></span> <span data-ttu-id="6059a-192">Con una visualizzazione semplice cono culling logica nel compute shader, è stato possibile determinare se è stata una striscia di fuori di fotocamera ed evitare che venga aggiunto al buffer di push.</span><span class="sxs-lookup"><span data-stu-id="6059a-192">With some simple view frustum culling logic in the compute shader, we could determine if a strip was outside of camera view and prevent it from being added to the push buffer.</span></span> <span data-ttu-id="6059a-193">Ciò ridurrà la quantità di strisce considerevolmente, liberare alcuni cicli necessari nella GPU.</span><span class="sxs-lookup"><span data-stu-id="6059a-193">This reduced the amount of strips significantly, freeing up some needed cycles on the GPU.</span></span>

<span data-ttu-id="6059a-194">**Codice che illustra un buffer di Accodamento:**</span><span class="sxs-lookup"><span data-stu-id="6059a-194">**Code demonstrating an append buffer:**</span></span>

<span data-ttu-id="6059a-195">*COMPUTE shader:*</span><span class="sxs-lookup"><span data-stu-id="6059a-195">*Compute shader:*</span></span>

```
AppendStructuredBuffer<int> culledParticleIdx;
 
if (show)
    culledParticleIdx.Append(id.x);
```

<span data-ttu-id="6059a-196">*C#codice:*</span><span class="sxs-lookup"><span data-stu-id="6059a-196">*C# code:*</span></span>

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

<span data-ttu-id="6059a-197">Abbiamo provato a usare la stessa tecnica sulle particelle cloud, in cui si sarebbe li riforma del compute shader e push solo le particelle visibile da sottoporre a rendering.</span><span class="sxs-lookup"><span data-stu-id="6059a-197">We tried using the same technique on the cloud particles, where we would cull them on the compute shader and only push the visible particles to be rendered.</span></span> <span data-ttu-id="6059a-198">Questa tecnica in realtà non è stato salvato us soffermano molto sulle GPU poiché il collo di bottiglia principale era il pixel quantità sottoposti a rendering sullo schermo e non il costo di calcolo di vertici.</span><span class="sxs-lookup"><span data-stu-id="6059a-198">This technique actually did not save us much on the GPU since the biggest bottleneck was the amount pixels rendered on the screen, and not the cost of calculating the vertices.</span></span>

<span data-ttu-id="6059a-199">L'altro problema con questa tecnica è che il buffer append popolato in ordine casuale grazie alla sua natura parallelizzata delle particelle, causando le particelle ordinate sia non ordinata, determinando lo sfarfallio particelle di cloud computing.</span><span class="sxs-lookup"><span data-stu-id="6059a-199">The other problem with this technique was that the append buffer populated in random order due to its parallelized nature of computing the particles, causing the sorted particles to be un-sorted, resulting in flickering cloud particles.</span></span>

<span data-ttu-id="6059a-200">Sono disponibili le tecniche per ordinare il buffer di push, ma la quantità limitata di miglioramento delle prestazioni ottenuto all'esterno della faccia posteriore particelle sarebbe probabilmente essere con offset con un ordinamento aggiuntivo, pertanto abbiamo deciso di non adottare questa ottimizzazione.</span><span class="sxs-lookup"><span data-stu-id="6059a-200">There are techniques to sort the push buffer, but the limited amount of performance gain we got out of culling particles would likely be offset with an additional sort, so we decided to not pursue this optimization.</span></span>

## <a name="adaptive-rendering"></a><span data-ttu-id="6059a-201">Rendering adattivo</span><span class="sxs-lookup"><span data-stu-id="6059a-201">Adaptive rendering</span></span>

<span data-ttu-id="6059a-202">Per garantire una frequenza dei fotogrammi costante in un'app con diversi per il rendering di condizioni, come un cloud vs una visione chiara, presentammo adattive per il rendering dell'app.</span><span class="sxs-lookup"><span data-stu-id="6059a-202">To ensure a steady framerate on an app with varying rendering conditions like a cloudy vs a clear view, we introduced adaptive rendering to our app.</span></span>

<span data-ttu-id="6059a-203">Il primo passaggio di rendering adattivo è misurare GPU.</span><span class="sxs-lookup"><span data-stu-id="6059a-203">The first step of adaptive rendering is to measure GPU.</span></span> <span data-ttu-id="6059a-204">Abbiamo fatto ciò, inserendo codice personalizzato nel buffer dei comandi GPU all'inizio e alla fine di un frame sottoposto a rendering, acquisizione entrambi sinistra a destra dell'occhio tempo dello schermo.</span><span class="sxs-lookup"><span data-stu-id="6059a-204">We did this by inserting custom code into the GPU command buffer at the beginning and the end of a rendered frame, capturing both the left and right eye screen time.</span></span>

<span data-ttu-id="6059a-205">Misurando il tempo impiegato per il rendering e confrontandolo con la frequenza di aggiornamento desiderata che abbiamo un'idea di quanto si avvicina eravamo alla perdita di fotogrammi.</span><span class="sxs-lookup"><span data-stu-id="6059a-205">By measuring the time spent rendering and comparing it to our desired refresh-rate we got a sense of how close we were to dropping frames.</span></span>

<span data-ttu-id="6059a-206">Quando più vicino di perdita di fotogrammi, abbiamo adattare il rendering per renderlo più rapido.</span><span class="sxs-lookup"><span data-stu-id="6059a-206">When close to dropping frames, we adapt our rendering to make it faster.</span></span> <span data-ttu-id="6059a-207">Un modo semplice di adattamento sta cambiando le dimensioni del viewport della schermata, che richiedono meno pixel sottoposti a rendering.</span><span class="sxs-lookup"><span data-stu-id="6059a-207">One simple way of adapting is changing the viewport size of the screen, requiring less pixels to get rendered.</span></span>

<span data-ttu-id="6059a-208">Usando *UnityEngine.XR.XRSettings.renderViewportScale* automaticamente estende il risultato al adatta la schermata e si riduce il riquadro di visualizzazione destinazione sistema.</span><span class="sxs-lookup"><span data-stu-id="6059a-208">By using *UnityEngine.XR.XRSettings.renderViewportScale* the system shrinks the targeted viewport and automatically stretches the result back up to fit the screen.</span></span> <span data-ttu-id="6059a-209">Una piccola modifica della scala è poco evidente sulla geometria mondo e un fattore di scala di 0,7 richiede la metà dei pixel da sottoporre a rendering.</span><span class="sxs-lookup"><span data-stu-id="6059a-209">A small change in scale is barely noticeable on world geometry, and a scale factor of 0.7 requires half the amount of pixels to be rendered.</span></span>

![scala il 70%, metà del numero di pixel](images/datascape-scaling-700px.jpg)

<span data-ttu-id="6059a-211">Quando viene rilevato che si sta tentando di eliminare i frame è ridurre la scala per un numero fisso e aumentare nuovamente quando viene eseguito abbastanza velocemente nuovamente.</span><span class="sxs-lookup"><span data-stu-id="6059a-211">When we detect that we are about to drop frames we lower the scale by a fixed number, and increase it back when we are running fast enough again.</span></span>

<span data-ttu-id="6059a-212">Anche se è stato deciso quale tecnica cloud da usare basate sulle grafica funzionalità dell'hardware all'avvio, è possibile basarla su dati dalla misura GPU per impedire al sistema di rimanere bassa risoluzione per molto tempo, ma si tratta di qualcosa che non è stato ora  per esplorare in Datascape.</span><span class="sxs-lookup"><span data-stu-id="6059a-212">While we decided what cloud technique to use based on graphics capabilities of the hardware at startup, it is possible to base it on data from the GPU measurement to prevent the system from staying at low resolution for a long time, but this is something we did not have time to explore in Datascape.</span></span>

## <a name="final-thoughts"></a><span data-ttu-id="6059a-213">Considerazioni finali</span><span class="sxs-lookup"><span data-stu-id="6059a-213">Final thoughts</span></span>

<span data-ttu-id="6059a-214">Come destinazione un'ampia gamma di hardware è difficile e richiede una pianificazione.</span><span class="sxs-lookup"><span data-stu-id="6059a-214">Targeting a variety of hardware is challenging and requires some planning.</span></span>

<span data-ttu-id="6059a-215">È consigliabile iniziare con un minore di computer per acquisire familiarità con lo spazio dei problemi e sviluppare una soluzione di backup che verrà eseguito su tutti i computer di destinazione.</span><span class="sxs-lookup"><span data-stu-id="6059a-215">We recommend that you start targeting lower-powered machines to get familiar with the problem space and develop a backup solution that will run on all your machines.</span></span> <span data-ttu-id="6059a-216">Progettare una soluzione con velocità di riempimento presente, dal momento che pixel sarà la risorsa più preziosa.</span><span class="sxs-lookup"><span data-stu-id="6059a-216">Design your solution with fill rate in mind, since pixels will be your most precious resource.</span></span> <span data-ttu-id="6059a-217">Geometria solida di destinazione tramite la trasparenza.</span><span class="sxs-lookup"><span data-stu-id="6059a-217">Target solid geometry over transparency.</span></span>

<span data-ttu-id="6059a-218">Con una soluzione di backup, è possibile quindi avviare dei livelli nella maggiore complessità per i computer di fascia alta o forse semplicemente migliorare la risoluzione della soluzione di backup.</span><span class="sxs-lookup"><span data-stu-id="6059a-218">With a backup solution, you can then start layering in more complexity for high end machines or maybe just enhance resolution of your backup solution.</span></span>

<span data-ttu-id="6059a-219">Progettare per gli scenari peggiori e forse provare a usare rendering adattivo per situazioni di intenso.</span><span class="sxs-lookup"><span data-stu-id="6059a-219">Design for worst case scenarios, and maybe consider using adaptive rendering for heavy situations.</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="6059a-220">Informazioni sugli autori</span><span class="sxs-lookup"><span data-stu-id="6059a-220">About the authors</span></span>

<table style="border:0">
<tr>
<td style="border:0" width="60px"><img alt="Picture of Robert Ferrese" width="60" height="60" src="images/robert-ferrese-60px.jpg"></td>
<td style="border:0"><span data-ttu-id="6059a-221"><b>Robert Ferrese</b></span><span class="sxs-lookup"><span data-stu-id="6059a-221"><b>Robert Ferrese</b></span></span><br><span data-ttu-id="6059a-222">Tecnico del software @Microsoft</span><span class="sxs-lookup"><span data-stu-id="6059a-222">Software engineer @Microsoft</span></span></td>
</tr>
<tr>
<td style="border:0" width="60px"><img alt="Picture of Dan Andersson" width="60" height="60" src="images/dan-andersson-60px.jpg"></td>
<td style="border:0"><span data-ttu-id="6059a-223"><b>Dan Andersson</b></span><span class="sxs-lookup"><span data-stu-id="6059a-223"><b>Dan Andersson</b></span></span><br><span data-ttu-id="6059a-224">Tecnico del software @Microsoft</span><span class="sxs-lookup"><span data-stu-id="6059a-224">Software engineer @Microsoft</span></span></td>
</tr>
</table>


## <a name="see-also"></a><span data-ttu-id="6059a-225">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6059a-225">See also</span></span>
* [<span data-ttu-id="6059a-226">Ottenere informazioni sulle prestazioni per realtà mista</span><span class="sxs-lookup"><span data-stu-id="6059a-226">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="6059a-227">Raccomandazioni sulle prestazioni per Unity</span><span class="sxs-lookup"><span data-stu-id="6059a-227">Performance Recommendations for Unity</span></span>](performance-recommendations-for-unity.md)

 

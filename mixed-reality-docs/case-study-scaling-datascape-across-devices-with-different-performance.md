---
title: 'Case Study: ridimensionamento di DataScape tra dispositivi con prestazioni diverse'
description: Questo case study offre informazioni sul modo in cui gli sviluppatori Microsoft hanno ottimizzato l'app DataScape per offrire un'esperienza accattivante tra i dispositivi con una gamma di funzionalità di prestazioni.
author: danandersson
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: auricolare immersivo, ottimizzazione delle prestazioni, VR, case study
ms.openlocfilehash: 05f97188c81d85685540be998111ecfc47d9ef9c
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436510"
---
# <a name="case-study---scaling-datascape-across-devices-with-different-performance"></a>Case Study: ridimensionamento di DataScape tra dispositivi con prestazioni diverse

DataScape è un'applicazione di realtà mista di Windows sviluppata internamente in Microsoft, in cui siamo concentrati sulla visualizzazione dei dati meteorologici sui dati del terreno. L'applicazione esamina gli utenti esclusivi di Insights per individuare i dati in realtà mista, circondando l'utente con la visualizzazione dei dati olografici.

Per DataScape si vuole avere come destinazione un'ampia gamma di piattaforme con diverse funzionalità hardware, tra cui Microsoft HoloLens e gli auricolari per la realtà mista di Windows, e dai PC meno potenti ai PC più recenti con GPU di fascia alta. La sfida principale è stata il rendering della nostra scena in una situazione visivamente accattivante sui dispositivi con funzionalità grafiche estremamente diverse durante l'esecuzione con un framerate elevato.

In questo case study verranno illustrati il processo e le tecniche utilizzate per creare alcuni dei sistemi più a elevato utilizzo di GPU, che descrivono i problemi riscontrati e come sono stati superati.

## <a name="transparency-and-overdraw"></a>Trasparenza e sovraestrazione

I nostri principali problemi di rendering sono stati affrontati con la trasparenza, perché la trasparenza può essere costosa su una GPU.

È possibile eseguire il rendering della geometria a tinta unita in primo piano durante la scrittura nel buffer di profondità, arrestando eventuali pixel futuri che si trovano dietro il pixel da eliminare. In questo modo si evita che i pixel nascosti eseguano la pixel shader, velocizzando significativamente il processo. Se la geometria è ordinata in modo ottimale, ogni pixel sullo schermo viene disegnato una sola volta.

La geometria trasparente deve essere ordinata di nuovo in primo piano e si basa sulla fusione dell'output del pixel shader al pixel corrente sullo schermo. Questo può comportare la traccia di ogni pixel sullo schermo su più volte per fotogramma, definito sovradisegno.

Per i PC HoloLens e mainstream, la schermata può essere compilata solo alcune volte, rendendo problematico il rendering trasparente.

## <a name="introduction-to-datascape-scene-components"></a>Introduzione ai componenti della scena di DataScape

Nella nostra scena erano presenti tre componenti principali: **l'interfaccia utente, la mappa**e **il meteo**. Sapevamo che i nostri effetti meteorologici richiedevano tutto il tempo della GPU, quindi abbiamo progettato intenzionalmente l'interfaccia utente e il terreno in modo da ridurre il sovralievo.

L'interfaccia utente è stata rielaborata più volte per ridurre al minimo la quantità di sovragenerazione che produce. Ci siamo sbagliati sul lato di una geometria più complessa anziché sovrapporre l'arte trasparente sopra l'altra per componenti come pulsanti luminosi e panoramiche mappa.

Per la mappa, abbiamo usato uno shader personalizzato che rimuoverebbe le funzionalità di Unity standard come le ombre e l'illuminazione complessa, sostituendolo con un semplice modello di illuminazione solare singolo e un calcolo di nebbia personalizzato. Ciò ha prodotto una semplice pixel shader e libera i cicli della GPU.

Abbiamo gestito l'interfaccia utente e la mappa per il rendering in base al budget in cui non sono state necessarie modifiche a seconda dell'hardware; Tuttavia, la visualizzazione Meteo, in particolare il rendering del cloud, si è rivelata una sfida.

## <a name="background-on-cloud-data"></a>Informazioni di base sui dati cloud

I dati del cloud sono stati scaricati dai server NOAA (https://nomads.ncep.noaa.gov/) e sono stati riuniti in tre diversi livelli 2D, ognuno con l'altezza superiore e inferiore del cloud, nonché la densità del cloud per ogni cella della griglia. I dati sono stati elaborati in una trama di informazioni cloud in cui ogni componente è stato archiviato nel componente rosso, verde e blu della trama per semplificare l'accesso alla GPU.

## <a name="geometry-clouds"></a>Cloud Geometry

Per assicurarsi che i computer meno potenti potessero eseguire il rendering dei cloud, abbiamo deciso di iniziare con un approccio che usa la geometria solida per ridurre al minimo il sovralievo.

Abbiamo prima provato a produrre i cloud generando una mesh heightmap solida per ogni livello usando il raggio della trama delle informazioni sul cloud per ogni vertice per generare la forma. È stato usato un geometry shader per produrre i vertici sia nella parte superiore che nella parte inferiore del cloud che genera forme cloud solide. È stato usato il valore della densità dalla trama per colorare il cloud con colori più scuri per i cloud più densi.

**Shader per la creazione dei vertici:**

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

È stato introdotto un piccolo modello di disturbo per ottenere maggiori dettagli sui dati reali. Per produrre i bordi arrotondati del cloud, abbiamo ritagliato i pixel nel pixel shader quando il valore del raggio interpolato raggiunge una soglia per eliminare i valori near zero.

![Cloud Geometry](images/datascape-geometry-clouds-700px.jpg)

Poiché i cloud sono di tipo geometria uniforme, è possibile eseguirne il rendering prima del terreno per nascondere i pixel di mappa costosi sottostanti per migliorare ulteriormente la frequenza fotogrammi. Questa soluzione è stata eseguita correttamente in tutte le schede grafiche da min-spec a schede grafiche di fascia alta, così come in HoloLens, a causa dell'approccio di rendering a geometria solida.

## <a name="solid-particle-clouds"></a>Cloud di particelle solide

Ora è disponibile una soluzione di backup che ha prodotto una rappresentazione decente dei dati del cloud, ma è un po' scialbo nel fattore "Wow" e non ha trasmesso l'aspetto volumetrico che volevamo per i nostri computer di fascia alta.

Il passaggio successivo consisteva nel creare i cloud, rappresentarli con circa 100.000 particelle per produrre un aspetto più organico e volumetrico.

Se le particelle vengono mantenute solide e ordinate da front-to-back, è comunque possibile trarre vantaggio dall'abbassamento del buffer di profondità dei pixel dietro le particelle precedentemente sottoposte a rendering, riducendo la sovradisegna Inoltre, con una soluzione basata su particelle, è possibile modificare la quantità di particelle utilizzata per la destinazione di hardware diverso. Tuttavia, tutti i pixel devono comunque essere sottoposti a test di profondità, il che comporta un sovraccarico aggiuntivo.

In primo luogo, abbiamo creato posizioni particellari intorno al punto centrale dell'esperienza all'avvio. Le particelle sono state distribuite in modo più denso attorno al centro e in meno, a distanza. Sono state pre-ordinate tutte le particelle dal centro verso il retro, in modo da eseguire prima il rendering delle particelle più vicine.

Un compute shader campiona la trama delle informazioni sul cloud per posizionare ogni particella a un'altezza corretta e colorarla in base alla densità.

È stato usato *DrawProcedural* per eseguire il rendering di un quad per particella che consente ai dati particellari di rimanere sempre aggiornati sulla GPU.

Ogni particella contiene un'altezza e un raggio. L'altezza è basata sui dati del cloud campionati dalla trama delle informazioni sul cloud e il raggio è basato sulla distribuzione iniziale, in cui verrebbe calcolato per archiviare la distanza orizzontale rispetto al relativo Neighbor più vicino. I quad useranno questi dati per orientarsi all'angolo in base all'altezza, in modo che, quando gli utenti li esaminano orizzontalmente, l'altezza venga visualizzata e quando gli utenti li esaminano dall'alto verso il basso, viene analizzata l'area tra gli elementi adiacenti.

![Forma particella](images/particle-shape-700px.png)

**Codice dello shader che mostra la distribuzione:**

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

Poiché le particelle vengono ordinate in primo piano e si usa ancora uno shader di stile solido per ritagliare i pixel trasparenti (non Blend), questa tecnica gestisce una quantità sorprendente di particelle, evitando un costo eccessivo anche per i computer meno potenti.

## <a name="transparent-particle-clouds"></a>Cloud di particelle trasparenti

Le particelle solide forniscono una buona sensazione organica alla forma dei cloud, ma hanno comunque bisogno di qualcosa per vendere il lanosità di cloud. Si è deciso di provare una soluzione personalizzata per le schede grafiche di fascia alta in cui è possibile introdurre la trasparenza.

A tale scopo, è sufficiente passare l'ordinamento iniziale delle particelle e modificare lo shader in modo da usare l'alfa delle trame.

![Cloud soffici](images/fluffy-clouds-700px.jpg)

Ha avuto un aspetto notevole, ma si è dimostrata troppo pesante anche per le macchine più dure, perché comporterebbe il rendering di ogni pixel sullo schermo centinaia di volte.

## <a name="render-off-screen-with-lower-resolution"></a>Rendering fuori schermo con risoluzione inferiore

Per ridurre il numero di pixel di cui è stato eseguito il rendering dai cloud, abbiamo iniziato a eseguirne il rendering in un buffer di risoluzione trimestre (rispetto allo schermo) e allungando il risultato finale sullo schermo dopo che sono state disegnate tutte le particelle. In questo modo è stato fornito approssimativamente un aumento di velocità di 4x, ma sono stati introdotti alcuni aspetti.

**Codice per il rendering fuori schermo:**

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

Per prima cosa, quando si esegue il rendering in un buffer fuori schermo, abbiamo perso tutte le informazioni di profondità dalla nostra scena principale, ottenendo particelle dietro le montagne che si basano sulla montagna.

In secondo luogo, l'estensione del buffer ha introdotto anche elementi sui bordi dei cloud in cui la modifica della risoluzione era evidente. Nelle due sezioni successive viene illustrato il modo in cui sono stati risolti questi problemi.

## <a name="particle-depth-buffer"></a>Buffer profondità particella

Per fare in modo che le particelle coesistano con la geometria globale in cui una montagna o un oggetto può coprire le particelle sottostanti, è stato popolato il buffer fuori schermo con un buffer di profondità contenente la geometria della scena principale. Per produrre tale buffer di profondità, è stata creata una seconda fotocamera, che consente di eseguire il rendering solo della geometria solida e della profondità della scena.

È stata quindi usata la nuova trama nel pixel shader dei cloud per occludere pixel. È stata usata la stessa trama per calcolare la distanza alla geometria dietro un pixel del cloud. Usando tale distanza e applicando l'alfa del pixel, ora si è verificato l'effetto dei cloud che si avvicinano al terreno, rimuovendo eventuali tagli rigidi in cui le particelle e il terreno soddisfano.

![Cloud combinati in un terreno](images/clouds-blended-to-terrain-700px.jpg)

## <a name="sharpening-the-edges"></a>Affilatura dei bordi

I cloud estesi sembravano quasi identici ai cloud di dimensioni normali al centro delle particelle o dove si sovrappongono, ma mostravano alcuni artefatti ai bordi del cloud. In caso contrario, i bordi nitidi appaiono sfocati e sono stati introdotti gli effetti degli alias quando la fotocamera si sposta.

Per risolvere il problema, è possibile eseguire uno shader semplice sul buffer fuori schermo per determinare il punto in cui si è verificata una grande variazione di contrasto (1). Si inseriscono i pixel con grandi modifiche in un nuovo buffer di stencil (2). È stato quindi usato il buffer dello stencil per mascherare queste aree a contrasto elevato quando si applica il buffer fuori schermo allo schermo, ottenendo buchi in e intorno ai cloud (3).

È stato quindi eseguito il rendering di tutte le particelle in modalità a schermo intero, ma questa volta usava il buffer dello stencil per mascherare tutti gli elementi, tranne i bordi, ottenendo un set minimo di pixel interessati (4). Poiché il buffer dei comandi era già stato creato per le particelle, era sufficiente eseguirne il rendering nella nuova fotocamera.

![Progressione del rendering dei bordi del cloud](images/cloud-steps-1-4-700px.jpg)

Il risultato finale è costituito da bordi acuti con sezioni del centro a basso costo dei cloud.

Sebbene questa operazione fosse molto più rapida rispetto al rendering di tutte le particelle a schermo intero, c'è ancora un costo associato al test di un pixel sul buffer dello stencil.

## <a name="culling-particles"></a>Eliminazione di particelle

Per l'effetto vento, sono state generate strisce di triangolo lungo in un compute shader, creando molti WISP di vento nel mondo. Sebbene l'effetto vento non fosse pesante per la velocità di riempimento dovuta alle strisce skinny generate, ha prodotto molte centinaia di migliaia di vertici, causando un carico elevato per il vertex shader.

Sono stati introdotti i buffer di accodamento nel compute shader per inserire un subset di strisce di vento da disegnare. Con una semplice visualizzazione della logica di eliminazione tronco in compute shader, è possibile determinare se una striscia era esterna alla visualizzazione della fotocamera e impedire che venga aggiunta al buffer di push. Ciò ha ridotto significativamente la quantità di strisce, liberando alcuni cicli necessari sulla GPU.

**Codice che illustra un buffer di Accodamento:**

*Compute Shader:*

```
AppendStructuredBuffer<int> culledParticleIdx;
 
if (show)
    culledParticleIdx.Append(id.x);
```

*C#codice*

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

Si è provato a usare la stessa tecnica sulle particelle cloud, in cui è possibile eliminarle in compute shader e inserire solo le particelle visibili per il rendering. Questa tecnica in realtà non ci ha salvato molto sulla GPU poiché il collo di bottiglia più grande era la quantità di pixel di cui è stato eseguito il rendering sullo schermo e non il costo di calcolo dei vertici.

L'altro problema di questa tecnica è che il buffer di accodamento è stato popolato in ordine casuale a causa della natura parallela di calcolo delle particelle, causando la mancata ordinamento delle particelle ordinate, con conseguente sfarfallio delle particelle cloud.

Esistono tecniche per ordinare il buffer di push, ma la quantità limitata di miglioramento delle prestazioni ottenuta dall'abbassamento di livello delle particelle verrebbe probabilmente sfalsata con un ordinamento aggiuntivo, quindi si è deciso di non eseguire questa ottimizzazione.

## <a name="adaptive-rendering"></a>Rendering adattivo

Per garantire un framerate costante in un'app con diverse condizioni di rendering, ad esempio un Cloudy rispetto a una visualizzazione chiara, abbiamo introdotto il rendering adattivo per l'app.

Il primo passaggio del rendering adattivo consiste nella misurazione della GPU. Questa operazione è stata apportata inserendo codice personalizzato nel buffer dei comandi della GPU all'inizio e alla fine di un frame di cui è stato eseguito il rendering, acquisendo l'ora dello schermo a sinistra e a destra.

Misurando il tempo impiegato per il rendering e il confronto con la frequenza di aggiornamento desiderata, è stato rilevato il modo in cui è possibile eliminare i frame.

Quando ci si avvicina alla rimozione di frame, il rendering viene adattato in modo da renderlo più veloce. Un modo semplice per adattarsi è modificare la dimensione del viewport dello schermo, richiedendo meno pixel per il rendering.

Utilizzando *UnityEngine. XR. XRSettings. renderViewportScale* , il sistema compatta il viewport di destinazione e estende automaticamente il backup del risultato per adattarlo allo schermo. Una piccola modifica apportata alla scalabilità è difficilmente evidente sulla geometria globale e un fattore di scala 0,7 richiede metà della quantità di pixel di cui eseguire il rendering.

![70% di scala, metà dei pixel](images/datascape-scaling-700px.jpg)

Quando si rileva che si sta per eliminare i frame, la scala viene ridotta di un numero fisso e viene rimossa quando viene eseguita di nuovo in modo rapido.

Sebbene sia stata decisa la tecnica cloud da usare in base alle funzionalità grafiche dell'hardware all'avvio, è possibile basarlo sui dati della misurazione GPU per evitare che il sistema si trovi a bassa risoluzione per un lungo periodo di tempo, ma questo è un problema che non abbiamo avuto tempo  per esplorare in DataScape.

## <a name="final-thoughts"></a>Considerazioni finali

La definizione di un'ampia gamma di hardware è impegnativa e richiede una pianificazione.

Si consiglia di iniziare a utilizzare computer con una gestione più bassa per acquisire familiarità con lo spazio del problema e sviluppare una soluzione di backup che viene eseguita su tutti i computer. Progettare la soluzione tenendo presente la velocità di riempimento, dal momento che i pixel saranno la risorsa più preziosa. Specificare come destinazione una geometria solida rispetto alla trasparenza.

Con una soluzione di backup, è quindi possibile avviare la sovrapposizione in modo più complesso per i computer di fascia alta o forse semplicemente migliorare la risoluzione della soluzione di backup.

Progettare per scenari peggiori e forse prendere in considerazione l'uso del rendering adattivo per situazioni complesse.

## <a name="about-the-authors"></a>Informazioni sugli autori

<table style="border:0">
<tr>
<td style="border:0" width="60px"><img alt="Picture of Robert Ferrese" width="60" height="60" src="images/robert-ferrese-60px.jpg"></td>
<td style="border:0"><b>Robert Ferrese</b><br>Software Engineer @Microsoft</td>
</tr>
<tr>
<td style="border:0" width="60px"><img alt="Picture of Dan Andersson" width="60" height="60" src="images/dan-andersson-60px.jpg"></td>
<td style="border:0"><b>Dan Andersson</b><br>Software Engineer @Microsoft</td>
</tr>
</table>


## <a name="see-also"></a>Vedi anche
* [Informazioni sulle prestazioni per la realtà mista](understanding-performance-for-mixed-reality.md)
* [Suggerimenti sulle prestazioni per Unity](performance-recommendations-for-unity.md)

 

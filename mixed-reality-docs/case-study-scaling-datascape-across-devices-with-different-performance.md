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
# <a name="case-study---scaling-datascape-across-devices-with-different-performance"></a>Case study - ridimensionamento Datascape tra i dispositivi con prestazioni diverse

Datascape è un'applicazione di realtà mista di Windows sviluppata internamente presso Microsoft in cui ci siamo concentrati sulla visualizzazione dei dati meteo sui dati di terreno. L'applicazione illustra le informazioni dettagliate esclusive gli utenti di ottenere dall'individuazione dei dati nella realtà mista racchiudendo l'utente con visualizzazione olografica.

Per Datascape volevamo un'ampia gamma di piattaforme di destinazione con un hardware diverso che spaziano da Microsoft HoloLens a auricolari coinvolgenti di realtà mista di Windows e dai meno potenti PC per i PC più recenti con GPU di fascia alta. Il problema principale è costituita dal rendering la scena in pochi visivamente accattivanti nei dispositivi con le funzionalità di grafica diversa durante l'esecuzione di un'elevata frequenza dei fotogrammi.

Questo case study in dettaglio il processo e le tecniche usate per creare alcuni dei nostri sistemi più intensivo GPU, che descrive i problemi che si sono verificati e come abbiamo superato.

## <a name="transparency-and-overdraw"></a>La trasparenza ed estenda

La difficoltà principale per il rendering è trattata la trasparenza, poiché la trasparenza può essere costosa su una GPU.

La geometria solida possibile eseguire il rendering da fronte a retro durante la scrittura nel buffer di profondità, arrestare qualsiasi pixel futuri che si trova dietro tale pixel da vengano eliminati. Ciò impedisce l'esecuzione del pixel shader, velocizzando significativamente il processo di pixel nascosto. Se la geometria è ordinata in modo ottimale, ogni pixel sullo schermo verrà disegnata una sola volta.

Esigenze di geometria trasparente da ordinare nuovamente in primo piano e si basa su fusione l'output del pixel shader pixel sullo schermo corrente. Ciò può comportare ogni pixel sullo schermo viene disegnato di più volte per ogni fotogramma, noto come caricamento.

Per HoloLens e PC "Mainstream", la schermata è possibile compilare solo un numero limitato di volte, rendendo trasparente per il rendering problematico.

## <a name="introduction-to-datascape-scene-components"></a>Introduzione ai componenti di scena Datascape

Avevamo tre componenti principali per la scena; **l'interfaccia utente, la mappa**, e **meteo**. Sapevamo sin dall'inizio che l'effetti meteo richiede tutto il tempo GPU è stato possibile ottenere, in modo che è intenzionalmente progettata l'interfaccia utente e un terreno in modo che consentirebbe di ridurre qualsiasi di carica presente.

L'interfaccia utente viene rielaborata più volte per ridurre al minimo la quantità di caricamento produrrebbe. Abbiamo sbagliato a fianco geometrie più complesse invece di sovrimpressione grafica trasparente uno sopra l'altro per i componenti, ad esempio panoramiche brillante pulsanti e della mappa.

Per la mappa, è stato usato uno shader personalizzato che potrebbe eliminare le funzionalità standard di Unity, ad esempio variazioni di luminosità e illuminazione complesse, sostituirli con un modello di illuminazione semplice sun singolo e un calcolo nebbia personalizzato. Questo prodotto un pixel shader semplice e liberare cicli di GPU.

Siamo riusciti a ottenere l'interfaccia utente sia la mappa per il rendering in budget in cui non era necessario qualsiasi di tali modifiche a seconda dell'hardware; Tuttavia, la visualizzazione meteo, in particolare il rendering cloud, ha dimostrato di essere più complesso.

## <a name="background-on-cloud-data"></a>Informazioni generali su dati nel cloud

I dati nel cloud è stati scaricati dai server NOAA (http://nomads.ncep.noaa.gov/) e siamo arrivati in tre livelli 2D distinti, ognuno con l'altezza superiore e inferiore del cloud, nonché la densità del cloud per ogni cella della griglia. I dati è stati elaborati in una trama di informazioni sul cloud in cui ogni componente è stato archiviato nel componente rosso, verde e blu della trama per semplificare l'accesso nella GPU.

## <a name="geometry-clouds"></a>Cloud di geometria

Per assicurarsi che i computer con un minore è stato possibile eseguire il rendering nostro cloud abbiamo deciso di iniziare con un approccio che usa la geometria solida per ridurre al minimo estenda.

Innanzitutto, abbiamo provato producendo cloud tramite la generazione di una rete mesh di heightmap a tinta unita per ogni livello utilizzando il raggio della trama informazioni sul cloud per ogni vertice per generare la forma. Abbiamo utilizzato un geometry shader per produrre i vertici sia nella parte superiore e inferiore del cloud genera forme cloud solida. Viene utilizzato il valore di densità dalla trama per colorare il cloud con i colori più scuri per più cloud ad alta densità.

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

È stata introdotta una serie di piccoli disturbi per ottenere altri dettagli su dati reali. Per produrre i bordi arrotondati cloud, viene troncato il pixel nel pixel shader quando il valore del raggio interpolata raggiunge una soglia per rimuovere valori vicino a zero.

![Cloud di geometria](images/datascape-geometry-clouds-700px.jpg)

Poiché i cloud sono la geometria solida, sia possibile eseguirne il rendering prima del terreno per nascondere tutti i pixel che mappa costose sotto per migliorare ulteriormente la frequenza dei fotogrammi. Questa soluzione è stata eseguita correttamente in tutte le schede di grafica da min-spec alle schede di grafica di alto livello, nonché su HoloLens, a causa dell'approccio di rendering della geometria solida.

## <a name="solid-particle-clouds"></a>Cloud particella a tinta unita

Avevamo ora una soluzione di backup che prodotta una ragionevole rappresentazione dei dati cloud, ma è stato un po' lackluster nel fattore di "wow" e non è stato conferiscono il volumetrici si ritiene che volevamo per i computer di fascia alta.

Il passaggio successivo è stato creazione i cloud che essi rappresentano con circa 100.000 particelle per produrre un aspetto più organico e volumetrico.

Se le particelle rimangono solide e ordinare parte anteriore a quella posteriore, è possibile trarre comunque vantaggio dai profondità buffer della faccia posteriore dei pixel dietro le particelle precedentemente sottoposti a rendering, riducendo il caricamento. Inoltre, con una soluzione basata su particella, è possibile modificare la quantità di particelle utilizzato su hardware diverso di destinazione. Tuttavia, tutti i pixel è comunque necessario essere testata profondità, determinando un overhead aggiuntivo.

Sono stati creati dapprima, posizioni delle particelle intorno al punto centrale dell'esperienza all'avvio. Abbiamo distribuito le particelle più efficiente la capacità intorno al centro e meno così la distanza. Tutte le particelle dal centro nella parte posteriore è pre-ordinamento in modo che renda prima di tutto le particelle più vicino.

Un compute shader sarebbe campione trama informazioni sul cloud per posizionare ogni particella a un'altezza corretto colore in base la densità.

È stato usato *DrawProcedural* per eseguire il rendering di un quadrato per ogni particella consentendone la particella restare sempre aggiornato riguardo la GPU in qualsiasi momento.

Ogni particella contenuta sia un'altezza e un raggio. L'altezza è stato in base ai cloud dati campionati dalla trama informazioni sul cloud e il raggio si basava sulla distribuzione iniziale in cui viene calcolato per archiviare la distanza orizzontale per il nodo più vicino. I quadrati utilizzerà questi dati per orientarsi meglio all'interno di se stesso con angolazione dall'altezza, in modo che quando utenti esaminano in senso orizzontale, verranno visualizzato l'altezza e rientrerebbero quando gli utenti preso in esame, dall'alto in basso, l'area compresa tra gli elementi adiacenti.

![Forma particella](images/particle-shape-700px.png)

**Codice dello shader che illustra la distribuzione:**

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

Poiché Ordiniamo le particelle parte anteriore a quella posteriore e viene ancora usato uno shader a tinta unita con stile ai pixel trasparenti clip (blend non), questa tecnica consente di gestire una quantità sorprendente di particelle, evitando costosa disegno eccessivo anche nei computer con un minore.

## <a name="transparent-particle-clouds"></a>Cloud particella trasparente

Le particelle solide fornito organica ottimali per la forma dei cloud ma comunque bisogno di qualcosa di vendere fluffiness di cloud. Abbiamo deciso di provare a una soluzione personalizzata per le schede di grafica di alto livello in cui è possibile introdurre la trasparenza.

A tale scopo è semplicemente passata l'ordinamento iniziale delle particelle e modificare lo shader per utilizzare il canale alfa di trame.

![Fluffy cloud](images/fluffy-clouds-700px.jpg)

Che era eccezionale ma si è rivelata troppo pesante per anche le macchine più complesse perché il risultato sarà il rendering di ogni pixel sullo schermo centinaia di volte!

## <a name="render-off-screen-with-lower-resolution"></a>Eseguire il rendering fuori schermo con risoluzione inferiore

Per ridurre il numero di pixel sottoposti a rendering per il cloud, abbiamo iniziato a essi per il rendering nel buffer di risoluzione di un trimestre (rispetto alla schermata) e l'adattamento il risultato finale il backup sullo schermo, dopo che tutte le particelle erano state disegnate. Questo ci ha offerto più o meno un aumento della velocità 4 x, ma integrava un paio di aspetti.

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

In primo luogo, durante il rendering in un buffer fuori schermo, abbiamo perdita di tutte le informazioni di profondità dal nostro scena principale, conseguente particelle dietro montagne rendering nella parte superiore di mountain.

In secondo luogo, l'adattamento del buffer sono stati introdotti gli elementi sui bordi dei nostri cloud in cui la modifica di risoluzione è evidente. Due sezioni successive parleremo di come è stato risolto questi problemi.

## <a name="particle-depth-buffer"></a>Buffer profondità particella

Per rendere le particelle coesiste con la geometria del mondo in cui un oggetto o mountain può coprire le particelle dietro di essa, viene popolato il buffer fuori schermo con un buffer di profondità contenente la geometria della scena principale. Per generare tale buffer di profondità, abbiamo creato una fotocamera secondo, il rendering solo la geometria solida e profondità della scena.

La nuova trama viene quindi utilizzato nel pixel shader dei cloud per nasconde i colori pixel. Abbiamo utilizzato la trama stessa per calcolare la distanza di geometria dietro a un pixel di cloud. Utilizzando tale distanza e applicarlo al valore alfa del pixel, avevamo a questo punto l'effetto dei cloud dissolvenza in uscita mano a mano che vicino al terreno, la rimozione di qualsiasi disco rigidi tagli incontro tra le particelle e terreno.

![Cloud devono essere smussati nel terreno](images/clouds-blended-to-terrain-700px.jpg)

## <a name="sharpening-the-edges"></a>Aumento della nitidezza bordi

I cloud esteso-up era quasi identici per i cloud di dimensioni normali il fulcro delle particelle o in cui sono sovrapposte, ma ha illustrato alcuni elementi in corrispondenza dei bordi cloud. In caso contrario bordi sharp apparirebbe sfocati e sono stati introdotti gli effetti di alias quando spostato la fotocamera.

Abbiamo risolto questo problema eseguendo un semplice shader nel buffer fuori schermo per determinare dove notevoli modifiche invece si è verificato un (1). Abbiamo inserito i pixel con notevoli modifiche in un nuovo buffer di stencil (2). Successivamente, abbiamo utilizzato il buffer di stencil per nascondere le aree a contrasto elevato quando si applica il buffer fuori schermo nella schermata di conseguente fori e tutto il cloud (3).

Abbiamo quindi tutte le particelle eseguire nuovamente il rendering in modalità schermo intero, ma questa volta utilizzato il buffer di stencil per nascondere tutti gli elementi, ma i bordi, risultante in un set minimo di pixel tocca (4). Poiché il buffer dei comandi è stata già creato per le particelle, abbiamo dovuto semplicemente eseguirne il rendering nuovamente alla nuova fotocamera.

![Progressione di rendering cloud bordi](images/cloud-steps-1-4-700px.jpg)

Il risultato finale era ben strutturati bordi con sezioni center ed economici del cloud.

Mentre questo era molto più veloce rispetto a rendering tutte le particelle nel schermo intero, esiste comunque un costo associato con il test di un pixel con buffer di stencil, in modo che estenda ancora di una notevole quantità di fornito con un costo.

## <a name="culling-particles"></a>Le particelle della faccia posteriore

L'effetto del vento, viene generato lungo le strisce di triangoli in un compute shader, creazione di valore molti del vento in tutto il mondo. Mentre l'effetto del vento non era impegnativa velocità di riempimento a causa di strisce skinny generato, ha prodotto molte centinaia di migliaia di vertici generino un carico eccessivo per vertex shader.

È stato introdotto accodare buffer presenti a del compute shader per inserire un sottoinsieme delle strisce wind da disegnare. Con una visualizzazione semplice cono culling logica nel compute shader, è stato possibile determinare se è stata una striscia di fuori di fotocamera ed evitare che venga aggiunto al buffer di push. Ciò ridurrà la quantità di strisce considerevolmente, liberare alcuni cicli necessari nella GPU.

**Codice che illustra un buffer di Accodamento:**

*COMPUTE shader:*

```
AppendStructuredBuffer<int> culledParticleIdx;
 
if (show)
    culledParticleIdx.Append(id.x);
```

*C#codice:*

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

Abbiamo provato a usare la stessa tecnica sulle particelle cloud, in cui si sarebbe li riforma del compute shader e push solo le particelle visibile da sottoporre a rendering. Questa tecnica in realtà non è stato salvato us soffermano molto sulle GPU poiché il collo di bottiglia principale era il pixel quantità sottoposti a rendering sullo schermo e non il costo di calcolo di vertici.

L'altro problema con questa tecnica è che il buffer append popolato in ordine casuale grazie alla sua natura parallelizzata delle particelle, causando le particelle ordinate sia non ordinata, determinando lo sfarfallio particelle di cloud computing.

Sono disponibili le tecniche per ordinare il buffer di push, ma la quantità limitata di miglioramento delle prestazioni ottenuto all'esterno della faccia posteriore particelle sarebbe probabilmente essere con offset con un ordinamento aggiuntivo, pertanto abbiamo deciso di non adottare questa ottimizzazione.

## <a name="adaptive-rendering"></a>Rendering adattivo

Per garantire una frequenza dei fotogrammi costante in un'app con diversi per il rendering di condizioni, come un cloud vs una visione chiara, presentammo adattive per il rendering dell'app.

Il primo passaggio di rendering adattivo è misurare GPU. Abbiamo fatto ciò, inserendo codice personalizzato nel buffer dei comandi GPU all'inizio e alla fine di un frame sottoposto a rendering, acquisizione entrambi sinistra a destra dell'occhio tempo dello schermo.

Misurando il tempo impiegato per il rendering e confrontandolo con la frequenza di aggiornamento desiderata che abbiamo un'idea di quanto si avvicina eravamo alla perdita di fotogrammi.

Quando più vicino di perdita di fotogrammi, abbiamo adattare il rendering per renderlo più rapido. Un modo semplice di adattamento sta cambiando le dimensioni del viewport della schermata, che richiedono meno pixel sottoposti a rendering.

Usando *UnityEngine.XR.XRSettings.renderViewportScale* automaticamente estende il risultato al adatta la schermata e si riduce il riquadro di visualizzazione destinazione sistema. Una piccola modifica della scala è poco evidente sulla geometria mondo e un fattore di scala di 0,7 richiede la metà dei pixel da sottoporre a rendering.

![scala il 70%, metà del numero di pixel](images/datascape-scaling-700px.jpg)

Quando viene rilevato che si sta tentando di eliminare i frame è ridurre la scala per un numero fisso e aumentare nuovamente quando viene eseguito abbastanza velocemente nuovamente.

Anche se è stato deciso quale tecnica cloud da usare basate sulle grafica funzionalità dell'hardware all'avvio, è possibile basarla su dati dalla misura GPU per impedire al sistema di rimanere bassa risoluzione per molto tempo, ma si tratta di qualcosa che non è stato ora  per esplorare in Datascape.

## <a name="final-thoughts"></a>Considerazioni finali

Come destinazione un'ampia gamma di hardware è difficile e richiede una pianificazione.

È consigliabile iniziare con un minore di computer per acquisire familiarità con lo spazio dei problemi e sviluppare una soluzione di backup che verrà eseguito su tutti i computer di destinazione. Progettare una soluzione con velocità di riempimento presente, dal momento che pixel sarà la risorsa più preziosa. Geometria solida di destinazione tramite la trasparenza.

Con una soluzione di backup, è possibile quindi avviare dei livelli nella maggiore complessità per i computer di fascia alta o forse semplicemente migliorare la risoluzione della soluzione di backup.

Progettare per gli scenari peggiori e forse provare a usare rendering adattivo per situazioni di intenso.

## <a name="about-the-authors"></a>Informazioni sugli autori

<table style="border:0">
<tr>
<td style="border:0" width="60px"><img alt="Picture of Robert Ferrese" width="60" height="60" src="images/robert-ferrese-60px.jpg"></td>
<td style="border:0"><b>Robert Ferrese</b><br>Tecnico del software @Microsoft</td>
</tr>
<tr>
<td style="border:0" width="60px"><img alt="Picture of Dan Andersson" width="60" height="60" src="images/dan-andersson-60px.jpg"></td>
<td style="border:0"><b>Dan Andersson</b><br>Tecnico del software @Microsoft</td>
</tr>
</table>


## <a name="see-also"></a>Vedere anche
* [Ottenere informazioni sulle prestazioni per realtà mista](understanding-performance-for-mixed-reality.md)
* [Raccomandazioni sulle prestazioni per Unity](performance-recommendations-for-unity.md)

 

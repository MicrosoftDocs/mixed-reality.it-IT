---
title: Comprensione della scena
description: Introduzione alle funzionalità di comprensione della scena per HoloLens
author: szymons
ms.author: szymons
ms.date: 07/08/2019
ms.topic: article
keywords: Comprensione della scena, mapping spaziale, realtà mista di Windows, Unity
ms.openlocfilehash: bacec5e6a9bfda49d4ad6d3dd849156c9cc09add
ms.sourcegitcommit: 83698638b93c5ba77b3ffc399f1706482539f27b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/26/2019
ms.locfileid: "74539697"
---
# <a name="scene-understanding"></a>Comprensione della scena

La comprensione delle scene fornisce agli sviluppatori di realtà mista una rappresentazione dell'ambiente di alto livello strutturata progettata per rendere intuitivo lo sviluppo di applicazioni compatibili con l'ambiente. La comprensione della scena consente di combinare la potenza dei runtime di realtà mista esistenti, ad esempio il [mapping spaziale](spatial-mapping.md) meno strutturato e i nuovi runtime basati su intelligenza artificiale. Combinando queste tecnologie, la comprensione della scena genera rappresentazioni di ambienti 3D simili a quelle che potrebbero essere state usate nei Framework, ad esempio Unity o ARKit/ARCore. Il punto di ingresso comprensione della scena inizia con un osservatore della scena che viene chiamato dall'applicazione per calcolare una nuova scena. Oggi la tecnologia è in grado di generare tre categorie di oggetti distinti ma correlati: mesh dell'ambiente impermeabile semplificate che derivano la struttura dello spazio planare senza confusione, aree del piano per la selezione host che chiameremo quad e uno snapshot del [ mesh di mapping spaziale](spatial-mapping.md) che è allineato con i quad o i dati stagni che emergiamo.

![Mesh di mapping spaziale, superfici planari con etichetta, mesh impermeabile](images/SUScenarios.png)

Questo documento ha lo scopo di fornire una panoramica dello scenario e di chiarire la relazione tra la conoscenza della scena e la condivisione di mapping spaziale.

## <a name="developing-with-scene-understanding"></a>Sviluppo con comprensione della scena

Questo articolo serve solo per introdurre la scena per comprendere il runtime e i concetti. Se si sta cercando la documentazione su come sviluppare con la comprensione della scena, è possibile che si sia interessati a quanto segue:

[Panoramica dell'SDK per la comprensione della scena](scene-understanding-SDK.md)

È possibile scaricare l'app di esempio per informazioni sulla scena dal sito GitHub di esempio:

[Esempio di comprensione della scena](https://github.com/sceneunderstanding-microsoft/unitysample)

Se non si ha un dispositivo e si vuole accedere a scene di esempio per provare a comprendere la scena, sono disponibili alcune scene nella cartella asset di esempio:

[Scene di esempio sulla comprensione della scena](https://github.com/sceneunderstanding-microsoft/unitysample/tree/master/Assets/Resources/SerializedScenesForPCPath)

### <a name="sdk"></a>SDK

Per informazioni dettagliate su come sviluppare per la scena understandiing, per informazioni dettagliate sul funzionamento della comprensione della scena e su come svilupparle, vedere la pagina relativa alla panoramica della documentazione [Panoramica sull'SDK](scene-understanding-SDK.md) .


### <a name="sample"></a>Esempio


## <a name="device-support"></a>Supporto di dispositivi

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Funzionalità</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (prima generazione)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
    </tr>
     <tr>
        <td>Comprensione della scena</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="common-usage-scenarios"></a>Scenari di utilizzo comuni

![illustrazioni degli scenari comuni di utilizzo del mapping spaziale: posizionamento, occlusione, fisica e navigazione](images/sm-concepts-1000px.png)<br>
*Scenari comuni di utilizzo del mapping spaziale: posizionamento, occlusione, fisica e navigazione.*

<br>

Molti degli scenari principali per le applicazioni compatibili con l'ambiente (posizionamento, occlusione, fisica e così via) sono indirizzabili sia dal mapping spaziale che dalla comprensione della scena, in questa sezione vengono evidenziate queste differenze. Una differenza fondamentale tra la comprensione della scena e il mapping spaziale è un compromesso tra precisione massima e latenza alla struttura e alla semplicità. Se l'applicazione richiede la latenza più bassa possibile e richiede solo triangoli mesh, sarà necessario accedere direttamente al mapping spaziale. Tuttavia, se si esegue un'elaborazione di livello superiore, è possibile passare alla scena che comprende il modello deve fornire un superset di funzionalità. Si noti inoltre che, poiché la comprensione della scena fornisce la mesh di mapping spaziale come parte della relativa rappresentazione, sarà sempre possibile accedere ai dati di mapping spaziali più completi e accurati.

 Le sezioni seguenti rivisitano gli scenari di mapping spaziale principali nel contesto della nuova scena Understanding SDK.

### <a name="placement"></a>Posizionamento

La comprensione della scena fornisce nuovi costrutti appositamente progettati per semplificare gli scenari di posizionamento. Una scena può calcolare le primitive denominate SceneQuads che descrivono le superfici piane in cui è possibile posizionare gli ologrammi. SceneQuads sono stati progettati in modo specifico per la selezione host e descrivono una superficie 2D e forniscono un'API per la selezione host su tale superficie. In precedenza, quando si utilizzava la mesh triangolare per eseguire la selezione host, era necessario analizzare tutte le aree del quad ed eseguire operazioni di riempimento/post-elaborazione dei fori per identificare posizioni valide per la posizione degli oggetti. Questa operazione non è sempre necessaria con i quad, perché la scena che comprende il runtime è in grado di dedurre le aree del quad che non sono state analizzate e di invalidare le aree del quad che non fanno parte della superficie.

:::row:::
    :::column:::
       ![SceneQuads con inferenza disabilitata, acquisendo le aree di posizionamento per le aree analizzate.](images/SUQuads.png)<br>
       **Image #1** -SceneQuads con inferenza disabilitata, acquisizione delle aree di posizionamento per le aree analizzate.
    :::column-end:::
        :::column:::
       ![quad con inferenza abilitata, la selezione host non è più limitata alle aree analizzate.](images/SUWatertight.png)<br>
        **Image #2** -quad con inferenza abilitata, la selezione host non è più limitata alle aree analizzate.
    :::column-end:::
:::row-end:::

<br>


Se l'applicazione intende inserire ologrammi 2D o 3D in strutture rigide dell'ambiente, la semplicità e la praticità di SceneQuads per la selezione host sono preferibili al calcolo di queste informazioni dalla mesh di [mapping spaziale](spatial-mapping.md) . Per altri dettagli su questo argomento, vedere la sezione [informazioni di riferimento sull'SDK](scene-understanding-SDK.md)

**Nota** Per il codice di posizionamento legacy che dipende dalla mesh di mapping spaziale, è possibile calcolare la mesh di mapping spaziale insieme a SceneQuads impostando l'impostazione di EnableWorldMesh. Se l'API per la comprensione della scena non soddisfa i requisiti di latenza dell'applicazione, si consiglia di continuare a usare l' [API di mapping spaziale](spatial-mapping.md#placement).

### <a name="occlusion"></a>Occlusione

L' [occlusione del mapping spaziale](spatial-mapping.md#occlusion) rimane il modo meno latente per acquisire lo stato in tempo reale dell'ambiente. Sebbene ciò possa risultare utile per fornire l'occlusione in scenari estremamente dinamici, è consigliabile prendere in considerazione la comprensione della scena per l'occlusione per diversi motivi. Se si usa la mesh di mapping spaziale generata dalla comprensione della scena, è possibile richiedere i dati dal mapping spaziale che non vengono archiviati nella cache locale e pertanto non sono disponibili nelle API di percezione. Se si usa il mapping spaziale per l'occlusione, le mesh stagne forniranno un valore aggiuntivo, in particolare il completamento della struttura dello spazio non analizzata.

Se i requisiti possono tollerare un aumento della latenza della comprensione della scena, gli sviluppatori di applicazioni devono prendere in considerazione l'uso della scena per comprendere la mesh stagna e presumibilmente la mesh di mapping spaziale in Unison con le rappresentazioni planari. Questo offrirebbe una "migliore di entrambi i mondi", in cui l'occlusione stagna semplificata è sposata con una geometria non piana più precisa che fornisce le mappe di occlusione più realistiche possibili.

### <a name="physics"></a>Fisica

La comprensione della scena genera maglie stagne che compongono lo spazio con la semantica in modo specifico per soddisfare molte limitazioni alla fisica imposte dalle mesh di mapping spaziale. Le strutture stagne assicurano che i cast dei raggi fisici vengano sempre raggiunti e la scomposizione semantica consente la generazione più semplice di mesh NAV per la navigazione interna. Come descritto nella sezione sull' [occlusione](#occlusion) per la creazione di una scena con EnableSceneObjectMeshes e EnableWorldMesh, viene prodotta la mesh con la massima fisicità più completa possibile. La proprietà stagne della mesh dell'ambiente impedisce che gli hit test abbiano esito negativo e che i dati della mesh garantiscano che la fisica interagisca con tutti gli oggetti nella scena e non solo con la struttura della stanza.

### <a name="navigation"></a>Navigazione

Le mesh planari decomposte dalla classe semantica sono costrutti ideali per la pianificazione della navigazione e del percorso, semplificando molti dei problemi descritti nella panoramica dello [spostamento del mapping spaziale](spatial-mapping.md#navigation) . Gli oggetti SceneMesh calcolati nella scena sono già decomposti dal tipo di superficie, assicurando che la generazione della mesh NAV sia limitata alle superfici su cui è possibile eseguire il percorso. A causa della semplicità della struttura del piano, la generazione della mesh NAV dinamica nei motori 3D, ad esempio Unity, è raggiungibile a seconda dei requisiti in tempo reale.

La generazione di NAV-mesh accurati richiede attualmente la post-elaborazione, vale a dire che le applicazioni devono ancora proiettare occluders in base al piano per garantire che la navigazione non passi attraverso le tabelle e, così via... Il modo più accurato per eseguire questa operazione consiste nel proiettare i dati di rete globale forniti se la scena viene calcolata con il flag EnableWorldMesh.

### <a name="visualization"></a>Visualizzazione

Sebbene la [visualizzazione del mapping spaziale](spatial-mapping.md#visualization) possa essere usata per il feedback in tempo reale dell'ambiente, esistono molti scenari in cui la semplicità degli oggetti planari e stagni garantisce maggiore prestazioni o qualità visiva. Le tecniche di proiezione Shadow e di base descritte con il mapping spaziale possono essere più gradevoli se proiettate sulle superfici planari fornite da quad o dalla mesh impermeabile piana. Ciò vale soprattutto per gli ambienti e gli scenari in cui l'analisi preliminare completa non è ottimale a causa del fatto che la scena dedurrà e gli ambienti completi e i presupposti planari riducono al minimo gli artefatti.

Inoltre, il numero totale di superfici restituite dal mapping spaziale è limitato dalla cache spaziale interna, mentre la versione di comprensione della scena della mesh di mapping spaziale è in grado di accedere ai dati di mapping spaziali non memorizzati nella cache. Per questo motivo, la comprensione della scena è più adatta per l'acquisizione di rappresentazioni di mesh per spazi più grandi (ad esempio, più grandi di una singola stanza) per la visualizzazione o per un'ulteriore elaborazione di mesh. La mesh globale restituita con EnableWorldMesh avrà un livello di dettaglio coerente, che può produrre una visualizzazione più gradevole se ne viene eseguito il rendering come wireframe.

### <a name="see-also"></a>Vedi anche

* [Scenario di comprensione dell'SDK](scene-understanding-SDK.md)
* [Mapping spaziale](spatial-mapping.md)

---
title: Comprensione della scena
description: Introduzione alle funzionalità di comprensione della scena per HoloLens
author: szymons
ms.author: szymons
ms.date: 07/08/19
ms.topic: article
keywords: Comprensione della scena, mapping spaziale, realtà mista di Windows, Unity
ms.openlocfilehash: fc77126958c653cac2d82f02cceeed9a29bffdf4
ms.sourcegitcommit: c4c293971bb3205a82121bbfb40d1ac52b5cb38e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/10/2019
ms.locfileid: "68941218"
---
# <a name="scene-understanding"></a>Comprensione della scena

La comprensione delle scene fornisce agli sviluppatori di realtà mista una rappresentazione dell'ambiente di alto livello strutturata progettata per rendere intuitivo lo sviluppo di applicazioni compatibili con l'ambiente. La comprensione della scena consente di combinare la potenza dei runtime di realtà mista esistenti, ad esempio il [mapping spaziale](spatial-mapping.md) meno strutturato e i nuovi runtime basati su intelligenza artificiale. Combinando queste tecnologie, la comprensione della scena genera rappresentazioni di ambienti 3D simili a quelle che potrebbero essere state usate nei Framework, ad esempio Unity o ARKit/ARCore. La scena Understanding EntryPoint inizia con un Observer della scena che viene chiamato dall'applicazione per calcolare una nuova scena. Oggi la tecnologia è in grado di generare tre categorie di oggetti distinti ma correlati: mesh dell'ambiente impermeabile semplificate che derivano la struttura dello spazio planare senza confusione, aree del piano per la selezione host che chiameremo quad e uno snapshot del [ mesh di mapping spaziale](spatial-mapping.md) che è allineato con i quad o i dati stagni che emergiamo.

![Mesh di mapping spaziale, superfici planari con etichetta, mesh impermeabile](images/SUScenarios.png)

Questo documento ha lo scopo di fornire una panoramica dello scenario e di chiarire la relazione tra la conoscenza della scena e la condivisione di mapping spaziale. Per informazioni dettagliate sul funzionamento della comprensione della scena e su come svilupparlo, vedere la pagina relativa alla [Panoramica della panoramica dell'SDK](scene-understanding-SDK.md) .

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Funzionalità</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (prima generazione)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td> Comprensione della scena</td><td style="text-align: center;">️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

## <a name="common-usage-scenarios"></a>Scenari di utilizzo comuni

![Illustrazioni degli scenari comuni di utilizzo del mapping spaziale: Posizionamento, occlusione, fisica e navigazione](images/sm-concepts-1000px.png)

Molti degli scenari principali per le applicazioni compatibili con l'ambiente (posizionamento, occlusione, fisica e così via) sono indirizzabili sia dal mapping spaziale che dalla comprensione della scena, in questa sezione vengono evidenziate queste differenze. Una differenza fondamentale tra la comprensione della scena e il mapping spaziale è un compromesso tra precisione massima e latenza alla struttura e alla semplicità. Se l'applicazione richiede la latenza più bassa possibile e richiede solo triangoli mesh, sarà necessario accedere direttamente al mapping spaziale. Tuttavia, se si esegue un'elaborazione di livello superiore, è possibile passare alla scena che comprende il modello deve fornire un superset di funzionalità. Si noti inoltre che, poiché la comprensione della scena fornisce la mesh di mapping spaziale come parte della relativa rappresentazione, sarà sempre possibile accedere ai dati di mapping spaziali più completi e accurati.

 Le sezioni seguenti rivisitano gli scenari di mapping spaziale principali nel contesto della nuova scena Understanding SDK.

### <a name="placement"></a>Posizionamento

La comprensione della scena fornisce nuovi costrutti appositamente progettati per semplificare gli scenari di posizionamento. Una scena può calcolare le primitive denominate SceneQuads che descrivono le superfici piane in cui è possibile posizionare gli ologrammi. SceneQuads sono stati progettati in modo specifico per la selezione host e descrivono una superficie 2D e forniscono un'API per la selezione host su tale superficie. In precedenza, quando si utilizzava la mesh triangolare per eseguire la selezione host, era necessario analizzare tutte le aree del quad ed eseguire operazioni di riempimento/post-elaborazione dei fori per identificare posizioni valide per la posizione degli oggetti. Questa operazione non è sempre necessaria con i quad, perché la scena che comprende il runtime è in grado di dedurre le aree del quad che non sono state analizzate e di invalidare le aree del quad che non fanno parte della superficie.

![SceneQuads con inferenza disabilitata, acquisizione delle aree di posizionamento per le aree analizzate.](images/SUQuads.png)
##### <a name="1-scenequads-with-inference-disabled-capturing-placement-areas-for-scanned-regions"></a>[1] "SceneQuads con inferenza disabilitata, acquisizione delle aree di selezione host per le aree analizzate".

![Quad con inferenza abilitata, la selezione host non è più limitata alle aree analizzate.](images/SUWatertight.png)
##### <a name="2-quads-with-inference-enabled-placement-is-no-longer-limited-to-scanned-areas"></a>[2] "quad con inferenza abilitata, la selezione host non è più limitata alle aree analizzate."

Se l'applicazione intende inserire ologrammi 2D o 3D in strutture rigide dell'ambiente, la semplicità e la praticità di SceneQuads per la selezione host sono preferibili al calcolo di queste informazioni dalla mesh di Surface. Per altri dettagli su questo argomento, vedere la sezione [informazioni di riferimento sull'SDK](scene-understanding-SDK.md)

**Nota** Per il codice legacy che dipende dalla mesh della superficie, è possibile calcolare una scena che contiene l'output del mapping spaziale insieme a SceneQuads, garantendo che tutti i requisiti legacy per la selezione host possano essere mantenuti. Se la scena informazioni sui dati mesh non soddisfa i requisiti di latenza dell'applicazione, si consiglia di continuare a usare le API di mapping spaziale descritte di seguito: [Selezione host per mapping spaziale](spatial-mapping.md#placement)

### <a name="occlusion"></a>Occlusione

L'occlusione del [mapping spaziale](spatial-mapping.md#occlusion) rimane il modo meno latente per acquisire lo stato in tempo reale dell'ambiente. Sebbene ciò possa risultare utile per fornire l'occlusione in scenari estremamente dinamici, è consigliabile prendere in considerazione la comprensione della scena per l'occlusione per diversi motivi. Se si usa la mesh di mapping spaziale generata dalla comprensione della scena, è possibile richiedere dati dal mapping spaziale che non verranno archiviati nella cache locale e pertanto non WDS disponibile dall'API di percezione. Se si usa il mapping spaziale per l'occlusione, le mesh stagne forniranno un valore aggiuntivo, in particolare il completamento della struttura dello spazio non analizzata.

Se i requisiti possono tollerare un aumento della latenza della comprensione della scena, gli sviluppatori di applicazioni devono prendere in considerazione l'uso della scena per comprendere la mesh stagna e presumibilmente la mesh di mapping spaziale in Unison con le rappresentazioni planari. Questo offrirebbe una "migliore di entrambi i mondi", in cui l'occlusione stagna semplificata è sposata con una geometria non piana più precisa che fornisce le mappe di occlusione più realistiche possibili.

### <a name="physics"></a>Fisica

La comprensione della scena genera mesh stagni che compongono lo spazio con la semantica in modo specifico per soddisfare molte limitazioni alla fisica che le mesh di superficie impongono. Le strutture stagne assicurano che i cast dei raggi fisici vengano sempre raggiunti e la scomposizione semantica consente la generazione più semplice di mesh NAV per la navigazione interna. Come descritto nella sezione sull' [occlusione](#occlusion) per la creazione di una scena con EnableSceneObjectMeshes e EnableWorldMesh, viene prodotta la mesh con la massima fisicità più completa possibile. La proprietà stagne della mesh dell'ambiente impedisce che gli hit test abbiano esito negativo e che i dati della mesh garantiscano che la fisica interagisca con tutti gli oggetti nella scena e non solo con la struttura della stanza.

### <a name="navigation"></a>Navigazione

Le mesh planari decomposte dalla classe semantica sono costrutti ideali per la pianificazione della navigazione e del percorso, semplificando molti dei problemi descritti nella panoramica dello [spostamento del mapping spaziale](spatial-mapping.md#navigation) . Gli oggetti SceneMesh calcolati nella scena sono già decomposti dal tipo di superficie, assicurando che la generazione della mesh NAV sia limitata alle superfici su cui è possibile eseguire il percorso. A causa della semplicità della struttura del piano, la generazione della mesh NAV dinamica nei motori 3D, ad esempio Unity, è raggiungibile a seconda dei requisiti in tempo reale.

La generazione di NAV-mesh accurati richiede attualmente la post-elaborazione, vale a dire che le applicazioni devono ancora proiettare occluders in base al piano per garantire che la navigazione non passi attraverso le tabelle e, così via... Il modo più accurato per eseguire questa operazione consiste nel proiettare i dati di rete globale forniti se la scena viene calcolata con il flag EnableWorldMesh.

### <a name="visualization"></a>Visualizzazione

Sebbene la [visualizzazione del mapping spaziale](spatial-mapping.md#visualization) possa essere usata per il feedback in tempo reale dell'ambiente, esistono molti scenari in cui la semplicità degli oggetti planari e stagni garantisce maggiore prestazioni o qualità visiva. Le tecniche di proiezione Shadow e di base descritte con il mapping spaziale possono essere più gradevoli se proiettate sulle superfici planari fornite da quad o dalla mesh impermeabile piana. Ciò vale soprattutto per gli ambienti e gli scenari in cui la pre-analisi non è ottimale a causa del fatto che la scena dedurrà e gli ambienti completi e i presupposti planari riducono al minimo gli artefatti.

Inoltre, il numero totale di superfici restituite dal mapping spaziale è limitato dalla cache spaziale interna, mentre la versione di comprensione della scena della mesh di mapping spaziale è in grado di accedere ai dati di mapping spaziali non memorizzati nella cache. Per questo motivo, la comprensione della scena è più adatta per l'acquisizione di rappresentazioni di mesh per spazi più grandi (ad esempio, più grandi di una singola stanza) per la visualizzazione o per un'ulteriore elaborazione di mesh. La mesh globale restituita con EnableWorldMesh avrà un livello di dettaglio coerente, che può produrre una visualizzazione più gradevole se ne viene eseguito il rendering come wireframe.

### <a name="see-also"></a>Vedere anche

* [Scenario di comprensione dell'SDK](scene-understanding-SDK.md)
* [Mapping spaziale](spatial-mapping.md)
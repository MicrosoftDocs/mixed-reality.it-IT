---
title: Scenario di comprensione dell'SDK
description: Guida alla programmazione per l'SDK di informazioni sulla scena
author: szymons
ms.author: szymons
ms.date: 07/08/2019
ms.topic: article
keywords: Comprensione della scena, mapping spaziale, realtà mista di Windows, Unity
ms.openlocfilehash: f365b0444576e03acd8dba194d7f8f24175e7bee
ms.sourcegitcommit: 83698638b93c5ba77b3ffc399f1706482539f27b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/26/2019
ms.locfileid: "74539517"
---
# <a name="scene-understanding-sdk-overview"></a>Panoramica dell'SDK per la comprensione della scena

L'obiettivo della comprensione della scena consiste nel trasformare i dati dei sensori dell'ambiente non strutturati acquisiti dal dispositivo della realtà mista e convertirli in una rappresentazione potente ma astratta che è intuitiva e facile da sviluppare per. L'SDK funge da livello di comunicazione tra l'applicazione e la scena che comprende il Runtime. Ha lo scopo di simulare costrutti standard esistenti, ad esempio grafici della scena 3D per le rappresentazioni 3D e rettangoli/pannelli 2D per le applicazioni 2D. Mentre la scena dei costrutti che comprendono le simulazioni verrà mappata a Framework concreti che è possibile usare, in generale SceneUnderstanding è un Framework agnostico che consente l'interoperabilità tra diversi Framework che interagiscono con esso. Poiché la comprensione della scena evolve il ruolo dell'SDK è garantire che le nuove rappresentazioni e funzionalità continuino a essere esposte in un framework unificato. In questo documento vengono introdotti i concetti di alto livello che consentiranno di acquisire familiarità con l'ambiente di sviluppo e l'utilizzo e quindi fornire una documentazione più dettagliata per classi e costrutti specifici.

## <a name="where-do-i-get-the-sdk"></a>Dove è possibile ottenere l'SDK?

SceneUnderstanding SDK è scaricabile tramite NuGet.

[SDK di SceneUnderstanding](https://www.nuget.org/packages/Microsoft.MixedReality.SceneUnderstanding/)

**Nota:** la versione più recente dipende dai pacchetti di anteprima ed è necessario abilitare i pacchetti di versioni non definitive per visualizzarli.

A partire dalla versione 0.5.2022-RC, la comprensione della scena supporta le C# proiezioni di linguaggio per e C++ consente alle applicazioni di sviluppare applicazioni per piattaforme Win32 o UWP. A partire da questa versione, SceneUnderstanding supporta Unity support in-Editor, bloccando il SceneObserver usato esclusivamente per la comunicazione con HoloLens2. 

SceneUnderstanding richiede Windows SDK versione 18362 o successiva. 

Se si usa l'SDK in un progetto Unity, usare [NuGet per Unity](https://github.com/GlitchEnzo/NuGetForUnity) per installare il pacchetto nel progetto.

## <a name="conceptual-overview"></a>Panoramica concettuale

### <a name="the-scene"></a>Scena

Il dispositivo di realtà mista sta integrando costantemente le informazioni relative a ciò che viene visualizzato nell'ambiente in uso. La comprensione della scena incanala tutte queste origini dati e produce un'unica astrazione coesiva. La comprensione della scena genera scene che sono una composizione di [SceneObjects](scene-understanding-SDK.md#sceneobjects) che rappresenta un'istanza di un singolo elemento, ad esempio una parete/soffitto/piano. Gli oggetti scena stessi sono una composizione di [SceneComponents](scene-understanding-SDK.md#scenecomponents) che rappresentano parti più granulari che compongono questo SceneObject. Esempi di componenti sono i quad e i mesh, ma in futuro potrebbero rappresentare i riquadri, le mesh di collisione, i metadati e così via.

Il processo di conversione dei dati dei sensori non elaborati in una scena è un'operazione potenzialmente costosa che può richiedere secondi per spazi medi (~ 10x10m) a minuti per spazi di dimensioni molto grandi (~ 50x50m) e pertanto non è un elemento che viene calcolato dal dispositivo senza richiesta dell'applicazione. La generazione della scena viene invece attivata dall'applicazione su richiesta. La classe SceneObserver dispone di metodi statici che consentono di calcolare o deserializzare una scena, con cui è possibile enumerare/interagire. L'azione "calcolo" viene eseguita su richiesta ed eseguita sulla CPU, ma in un processo separato (il driver della realtà mista). Tuttavia, mentre si esegue il calcolo in un altro processo, i dati della scena risultanti vengono archiviati e conservati nell'applicazione nell'oggetto scena. 

Di seguito è riportato un diagramma che illustra il flusso del processo e Mostra esempi di due applicazioni che si confrontano con la scena Understanding Runtime. 

![Diagramma di processo](images/SU-ProcessFlow.png)

Sul lato sinistro è presente un diagramma del runtime di realtà mista che è sempre attivo e in esecuzione nel proprio processo. Questo runtime è responsabile dell'esecuzione del rilevamento dei dispositivi, del mapping spaziale e di altre operazioni che la comprensione della scena USA per comprendere e ragionare in tutto il mondo. Sul lato destro del diagramma sono illustrate due applicazioni teoriche che fanno uso della comprensione della scena. La prima interfaccia dell'applicazione con MRTK che usa la scena Understanding SDK internamente, la seconda app calcola e usa due istanze della scena separate. Tutte e tre le scene in questo diagramma generano istanze distinte delle scene, il driver non rileva lo stato globale condiviso tra le applicazioni e gli oggetti scena in un'unica scena non è presente in un altro. La comprensione della scena fornisce un meccanismo per tenere traccia nel tempo, ma questa operazione viene eseguita usando l'SDK e il codice che esegue questo rilevamento viene eseguito nell'SDK nel processo dell'app.

Poiché ogni scena archivia i dati nello spazio di memoria dell'applicazione, si può presupporre che tutte le funzioni dell'oggetto scene o dei dati interni vengano sempre eseguite nel processo dell'applicazione.

### <a name="layout"></a>Layout

Per lavorare con la comprensione della scena, può essere utile conoscere e comprendere il modo in cui il runtime rappresenta i componenti in modo logico e fisico. La scena rappresenta i dati con un layout specifico che è stato scelto per essere semplice mantenendo una struttura sottostante flessibile per soddisfare i requisiti futuri senza che siano necessarie revisioni principali. Questa operazione viene eseguita archiviando tutti i componenti (elementi di base per tutti gli oggetti della scena) in un elenco semplice e definendo la gerarchia e la composizione tramite riferimenti in cui componenti specifici fanno riferimento ad altri.

Di seguito viene presentato un esempio di una struttura sia nel formato flat che nella forma logica.

<table>
<tr><th>Layout logico</th><th>Layout fisico</th></tr>
<tr>
<td>
<ul>
  Scena
  <ul>
  <li>SceneObject_1
    <ul>
      <li>SceneMesh_1</li>
      <li>SceneQuad_1</li>
      <li>SceneQuad_2</li>
    </ul>
  </li>
  <li>SceneObject_2
    <ul>
      <li>SceneQuad_1</li>
      <li>SceneQuad_3</li>
      </li></ul>
  </li>
  <li>SceneObject_3
    <ul>
      <li>SceneMesh_3</li>
    </ul>
  </ul>
</ul>
</td>
<td>
<ul>
  <li>SceneObject_1</li>
  <li>SceneObject_2</li>
  <li>SceneObject_3</li>
  <li>SceneQuad_1</li>
  <li>SceneQuad_2</li>
  <li>SceneQuad_3</li>
  <li>SceneMesh_1</li>
  <li>SceneMesh_2</li>
</ul>
</td>
</tr>
</table>

In questa illustrazione viene evidenziata la differenza tra il layout fisico e logico della scena. A sinistra viene visualizzato il layout gerarchico dei dati visualizzati dall'applicazione durante l'enumerazione della scena. A destra si noterà che la scena è in realtà costituita da 12 componenti distinti che sono accessibili singolarmente, se necessario. Quando si elabora una nuova scena, si prevede che le applicazioni analizzino logicamente questa gerarchia. Tuttavia, durante il rilevamento tra gli aggiornamenti della scena, alcune applicazioni potrebbero essere interessate solo a specifici componenti condivisi tra due scene.

## <a name="api-overview"></a>Panoramica delle API

Nella sezione seguente viene fornita una panoramica di alto livello dei costrutti nella comprensione della scena. Leggendo questa sezione si apprenderà a comprendere come vengono rappresentate le scene e quali sono i vari componenti usati per. La sezione successiva fornirà esempi di codice concreti e dettagli aggiuntivi che verranno descritti in questa panoramica.

Tutti i tipi descritti di seguito si trovano nello spazio dei nomi `Microsoft.MixedReality.SceneUnderstanding`.

### <a name="scenecomponents"></a>SceneComponents

Dopo aver compreso il layout logico delle scene, è ora possibile presentare il concetto di SceneComponents e il modo in cui vengono usate per comporre la gerarchia. SceneComponents sono le scomposizione più granulari in SceneUnderstanding che rappresentano un'unica cosa fondamentale, ad esempio una mesh o un quad o un rettangolo di delimitazione. SceneComponents sono elementi che possono essere aggiornati in modo indipendente ed è possibile farvi riferimento da altri SceneComponents, di conseguenza hanno un'unica proprietà globale un ID univoco, che consente questo tipo di meccanismo di rilevamento/riferimento. Gli ID vengono usati per la composizione logica della gerarchia della scena e per la persistenza degli oggetti, ovvero l'operazione di aggiornamento di una scena rispetto a un'altra. 

Se si tratta di una nuova scena calcolata come distinta e si esegue semplicemente l'enumerazione di tutti i dati al suo interno, gli ID sono in gran parte trasparenti. Tuttavia, se si prevede di tenere traccia dei componenti in diversi aggiornamenti, si useranno gli ID per indicizzare e trovare SceneComponents tra gli oggetti scena.

### <a name="sceneobjects"></a>SceneObjects

Un SceneObject è un SceneComponent che rappresenta un'istanza di un elemento "Thing", ad esempio un muro, un piano, un soffitto e così via. espressa dalla relativa proprietà Kind. SceneObjects sono geometriche e quindi hanno funzioni e proprietà che rappresentano la loro posizione nello spazio, ma non contengono alcuna struttura geometrica o logica. SceneObjects, invece, fanno riferimento ad altri SceneComponents, in particolare SceneQuads e SceneMeshes, che forniscono le varie rappresentazioni supportate dal sistema. Quando viene calcolata una nuova scena, l'applicazione enumera in modo più probabile la SceneObjects della scena per elaborare gli elementi interessati.

SceneObjects può avere uno dei seguenti elementi:

<table>
<tr>
<th>SceneObjectKind</th> <th>Descrizione</th>
</tr>
<tr><td>Informazioni</td><td>Il SceneObject <b>non</b> è noto come uno degli altri tipi di oggetto scena riconosciuti. Questa classe non deve essere confusa con Unknown, in cui lo sfondo non è a parete/piano/soffitto e così via... mentre Unknown non è ancora stato categorizzato.</b></td></tr>
<tr><td>Parete</td><td>Una parete fisica. Si presuppone che i muri siano strutture ambientali non mobili.</td></tr>
<tr><td>Floor</td><td>I piani sono superfici in cui è possibile spostarsi. Nota: le scale non sono piani. Si noti inoltre che le pavimentazioni presuppongono una superficie a cui è possibile spostarsi e pertanto non esiste alcun presupposto esplicito di un pavimento singolare. Strutture a più livelli, rampe e così via... deve essere classificata come floor.</td></tr>
<tr><td>Ceiling</td><td>Superficie superiore di una stanza.</td></tr>
<tr><td>Piattaforma</td><td>Una superficie piana grande su cui posizionare gli ologrammi. Che tendono a rappresentare tabelle, piani di ridimensionamento e altre superfici orizzontali di grandi dimensioni.</td></tr>
<tr><td>World</td><td>Etichetta riservata per i dati geometrici indipendenti dall'assegnazione di etichette. La mesh generata impostando il flag di aggiornamento EnableWorldMesh verrebbe classificato come World.</td></tr>
<tr><td>Sconosciuta</td><td>Questo oggetto scena deve ancora essere classificato e assegnato un tipo. Questa operazione non deve essere confusa con lo sfondo, perché questo oggetto può essere qualsiasi cosa, il sistema non ha ancora una classificazione sufficientemente forte per il sistema.</td></tr>
</tr>
</table>

### <a name="scenemesh"></a>SceneMesh

Un SceneMesh è un SceneComponent che approssima la geometria degli oggetti geometrici arbitrari usando un elenco di triangolo. SceneMeshes vengono usati in diversi contesti, possono rappresentare i componenti della struttura di celle stagne o come WorldMesh che rappresenta la mesh di mapping spaziale senza limiti associata alla scena. I dati relativi a indici e vertici forniti con ogni mesh utilizzano lo stesso layout familiare dei [buffer di vertice e di indice](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) utilizzati per il rendering di mesh triangolari in tutte le moderne API di rendering. Si noti che nella comprensione della scena le maglie usano gli indici a 32 bit e potrebbero dover essere suddivise in blocchi per determinati motori di rendering.

#### <a name="winding-order-and-coordinate-systems"></a>Ordine di avvolgimento e sistemi di coordinate

Tutte le mesh prodotte dalla comprensione della scena dovrebbero restituire mesh in un sistema di coordinate di destra usando l'ordine di avvolgimento in senso orario. 

Nota: le compilazioni del sistema operativo precedenti a. 191105 possono avere un bug noto in cui le mesh "World" hanno restituito un ordine di avvolgimento in senso antiorario, che in seguito è stato risolto.

### <a name="scenequad"></a>SceneQuad

Un SceneQuad è un SceneComponent che rappresenta le superfici 2D che occupano il mondo 3D. SceneQuads può essere usato in modo analogo ai piani ARKit ARPlaneAnchor o ARCore, ma offre funzionalità più avanzate come Canvas 2D da usare con le app flat o UX potenziato. sono disponibili API specifiche 2D per i quad che semplificano l'uso del posizionamento e del layout e lo sviluppo (ad eccezione del rendering) con i quad dovrebbe essere più simile all'utilizzo di Canvas 2D rispetto alle mesh 3D.

#### <a name="scenequad-shape"></a>Forma SceneQuad

SceneQuads definire una superficie rettangolare delimitata in 2D. Tuttavia, SceneQuads rappresentano le superfici con forme arbitrarie e potenzialmente complesse, ad esempio una tabella con forma di anello. Per rappresentare la forma complessa della superficie di un quad, è possibile usare l'API GetSurfaceMask per eseguire il rendering della forma della superficie in un buffer di immagine fornito. Se anche il SceneObject con il quad ha una mesh, i triangoli di mesh devono essere equivalenti a questa immagine sottoposta a rendering, entrambi rappresentano la geometria reale della superficie, solo in coordinate 2D o 3D.

## <a name="scene-understanding-sdk-details-and-reference"></a>Informazioni dettagliate e informazioni di riferimento sull'SDK della scena

La sezione seguente consente di acquisire familiarità con le nozioni di base di SceneUnderstanding. In questa sezione vengono fornite le nozioni di base, a questo punto è necessario disporre di un contesto sufficiente per esplorare le applicazioni di esempio per vedere come SceneUnderstanding viene usato in modo olistico.

### <a name="initialization"></a>Inizializzazione

Il primo passaggio per lavorare con SceneUnderstanding è che l'applicazione ottenga un riferimento a un oggetto scena. Questa operazione può essere eseguita in uno dei due modi seguenti, una scena può essere calcolata dal driver o una scena esistente calcolata in passato può essere deserializzata. Quest'ultimo è particolarmente utile per lavorare con SceneUnderstanding durante lo sviluppo, in cui le applicazioni e le esperienze possono essere prototipate rapidamente senza un dispositivo di realtà mista.

Le scene vengono calcolate usando un SceneObserver. Prima di creare una scena, l'applicazione deve eseguire una query sul dispositivo per assicurarsi che supporti SceneUnderstanding, oltre a richiedere l'accesso utente per le informazioni necessarie a SceneUnderstanding.

```cs
if (SceneObserver.IsSupported())
{
    // Handle the error
}

// This call should grant the access we need.
await SceneObserver.RequestAccessAsync();
```

Se RequestAccessAsync () non viene chiamato, il calcolo di una nuova scena avrà esito negativo. Successivamente, verrà calcolata una nuova scena che è radicata intorno all'auricolare della realtà mista e ha un raggio di 10 metri.

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

querySettings.EnableSceneObjectQuads = true;                                       // Requests that the scene updates quads.
querySettings.EnableSceneObjectMeshes = true;                                      // Requests that the scene updates watertight mesh data.
querySettings.EnableOnlyObservedSceneObjects = false;                              // Do not explicitly turn off quad inference.
querySettings.EnableWorldMesh = true;                                              // Requests a static version of the spatial mapping mesh.
querySettings.RequestedMeshLevelOfDetail = SceneMeshLevelOfDetail.Fine;            // Requests the finest LOD of the static spatial mapping mesh.

// Initialize a new Scene
Scene myScene = SceneObserver.ComputeAsync(querySettings, 10.0f).GetAwaiter().GetResult();
```

### <a name="initialization-from-data-aka-the-pc-path"></a>Inizializzazione dai dati (noto anche come. Percorso PC)

Mentre le scene possono essere calcolate per il consumo diretto, possono anche essere calcolate in formato serializzato per un uso successivo. Questo si è dimostrato di essere molto utile per lo sviluppo, in quanto consente agli sviluppatori di lavorare e testare la comprensione della scena senza la necessità di un dispositivo. L'azione di serializzazione di una scena è quasi identica a quella di elaborazione. i dati vengono restituiti all'applicazione anziché essere deserializzati localmente dall'SDK. Sarà quindi possibile deserializzarlo manualmente o salvarlo per un uso futuro.

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

// Compute a scene but serialized as a byte array
SceneBuffer newSceneBuffer = SceneObserver.ComputeSerializedAsync(querySettings, 10.0f).GetAwaiter().GetResult();

// If we want to use it immediately we can de-serialize the scene ourselves
byte[] newSceneData = new byte[newSceneBuffer.Size];
newSceneBuffer.GetData(newSceneData);
Scene mySceneDeSerialized = Scene.Deserialize(newSceneData);

// Save newSceneBlob for later
```

### <a name="sceneobject-enumeration"></a>Enumerazione SceneObject

Ora che l'applicazione ha una scena, l'applicazione verrà esaminata e interagirà con SceneObjects. Questa operazione viene eseguita accedendo alla proprietà **SceneObjects** :

```cs
SceneObject firstFloor = null;

// Find the first floor object
foreach (var sceneObject in myScene.SceneObjects)
{
    if (sceneObject.Kind == SceneObjectKind.Floor)
    {
        firstFloor = sceneObject;
        break;
    }
}
```

### <a name="component-update-and-re-finding-components"></a>Aggiornamento dei componenti e riricerca dei componenti

Esiste un'altra funzione che recupera i componenti nella scena denominata ***findComponent***. Questa funzione è utile quando si aggiornano gli oggetti di rilevamento e li si trova nelle scene successive. Il codice seguente consente di calcolare una nuova scena rispetto a una scena precedente e quindi di trovare il piano nella nuova scena.

```cs
// Compute a new scene, and tell the system that we want to compute relative to the previous scene
Scene myNextScene = SceneObserver.ComputeAsync(querySettings, 10.0f, myScene).GetAwaiter().GetResult();

// Use the Id for the floor we found last time, and find it again
firstFloor = (SceneObject)myNextScene.FindComponent(firstFloor.Id);

if (firstFloor != null)
{
    // We found it again, we can now update the transforms of all objects we attached to this floor transform
}
```

## <a name="accessing-meshes-and-quads-from-scene-objects"></a>Accesso a mesh e quad da oggetti scene

Una volta rilevate SceneObjects, è probabile che l'applicazione acceda ai dati contenuti nei Quad/mesh di cui è costituita. Questi dati sono accessibili con le proprietà ***Quad*** e ***mesh*** . Il codice seguente enumera tutti i quad e le maglie dell'oggetto Floor.

```cs

// Get the transform for the SceneObject
System.Numerics.Matrix4x4 objectToSceneOrigin = firstFloor.GetLocationAsMatrix();

// Enumerate quads
foreach (var quad in firstFloor.Quads)
{
    // Process quads
}

// Enumerate meshes
foreach (var mesh in firstFloor.Meshes)
{
    // Process meshes
}
```

Si noti che si tratta del SceneObject con la trasformazione rispetto all'origine della scena. Questo perché SceneObject rappresenta un'istanza di una "cosa" ed è locatable nello spazio, i quad e le mesh rappresentano la geometria che viene trasformata in relazione al rispettivo elemento padre. È possibile che SceneObjects separate facciano riferimento allo stesso SceneComponents SceneMesh/SceneQuad ed è anche possibile che un SceneObject disponga di più di un SceneMesh/SceneQuad.

### <a name="dealing-with-transforms"></a>Gestione delle trasformazioni

La comprensione della scena ha effettuato un tentativo intenzionale di allinearsi alle rappresentazioni tradizionali della scena 3D quando si gestiscono le trasformazioni. Ogni scena è quindi confinata a un singolo sistema di coordinate, in modo analogo alla maggior parte delle rappresentazioni ambientali 3D. SceneObjects forniscono la posizione e l'orientamento all'interno del sistema di coordinate. Se l'applicazione sta affrontando scenari che estendono il limite di una singola origine, può ancorare SceneObjects a SpatialAnchors o generare diverse scene e unirle, ma per semplicità si presuppone che le scene stagne esistano nei propri origine localizzata da un NodeId definito da scene. OriginSpatialGraphNodeId.

Il codice Unity seguente, ad esempio, Mostra come usare la percezione di Windows e le API Unity per allineare i sistemi di coordinate. Vedere [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) e [SpatialGraphInteropPreview](https://docs.microsoft.com//uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) per informazioni dettagliate sulle API di percezione di Windows e sugli [oggetti nativi della realtà mista in Unity](https://docs.microsoft.com//windows/mixed-reality/unity-xrdevice-advanced) per informazioni dettagliate su come ottenere un SpatialCoordinateSystem che corrisponde a Unity ' s di origine, nonché il metodo di estensione `.ToUnity()` per la conversione tra `System.Numerics.Matrix4x4` e `UnityEngine.Matrix4x4`.

```cs
public class SceneRootComponent : MonoBehavior
{
    public SpatialCoordinateSystem worldOrigin;
    public Scene scene;
    SpatialCoordinateSystem sceneOrigin;
    
    void Start()
    {
        // Initialize a SpatialCoordinateSystem for the scene's node in the system's Spatial Graph.
        scene.origin = SpatialGraphInteropPreview.CreateCoordinateSystemForNode(scene.OriginSpatialGraphNodeId);
    }
    
    void Update()
    {
        // Try to get the current transform of the scene's spatial graph node.
        // This may not be available, e.g. when tracking has been lost.
        var sceneToWorld = sceneOrigin.TryGetTransformTo(worldOrigin);
        if (sceneToWorld.HasValue)
        {
            // Convert the transform to Unity numerics and update the game object.
            var sceneToWorldUnity = sceneToWorld.Value.ToUnity();
            this.gameObject.transform.SetPositionAndRotation(sceneToWorldUnity.GetColumn(3), sceneToWorldUnity.rotation);
        }
    }
}
```

Ogni `SceneObject` dispone di una proprietà `Position` e `Orientation` che può essere usata per posizionare il contenuto corrispondente rispetto all'origine del `Scene`che lo contiene. Ad esempio, nell'esempio seguente si presuppone che il gioco sia un figlio della radice della scena e assegna la posizione e la rotazione locali per l'allineamento a una determinata `SceneObject`:

```cs
void SetLocalTransformFromSceneObject(GameObject gameObject, SceneObject sceneObject)
{
    gameObject.transform.localPosition = sceneObject.Position.ToUnity();
    gameObject.transform.localRotation = sceneObject.Orientation.ToUnity());
}
```

### <a name="quad"></a>Quad

I quad sono stati progettati per semplificare gli scenari di posizionamento 2D e dovrebbero essere considerati come estensioni per gli elementi UX di Canvas 2D. Mentre i quad sono componenti di SceneObjects e possono essere sottoposti a rendering in 3D, le API quadre presuppongono quad sono strutture 2D. Offrono informazioni come extent, Shape e forniscono API per la selezione host.

I quad hanno extent rettangolari, ma rappresentano superfici 2D a forma arbitraria. Per abilitare la selezione host in queste superfici 2D che interagiscono con i quad dell'ambiente 3D offrono utilità per rendere possibile questa interazione. Attualmente la comprensione della scena fornisce due funzioni di questo tipo, **FindCentermostPlacement** e **GetOcclusionMask**. FindCentermostPlacement è un'API di alto livello che individua una posizione nel quad in cui è possibile posizionare un oggetto e tenterà di trovare la posizione migliore per l'oggetto, garantendo che il rettangolo di delimitazione fornito si trovi sulla superficie sottostante.

Nell'esempio seguente viene illustrato come trovare la posizione posizionabile effettuare e come ancorare un ologramma al quad.

```cs
// This code assumes you already have a "Root" object that attaches the Scene's Origin.

// Find the first quad
foreach (var sceneObject in myScene.SceneObjects)
{
    // Find a wall
    if (sceneObject.Kind == SceneObjectKind.Wall)
    {
        // Get the quad
        var quads = sceneObject.Quads;
        if (quads.Count > 0)
        {
            // Find a good location for a 1mx1m object  
            System.Numerics.Vector2 location;
            if (quads[0].FindCentermostPlacement(new System.Numerics.Vector2(1.0f, 1.0f), out location))
            {
                // We found one, anchor something to the transform
                // Step 1: Create a new game object for the quad itself as a child of the scene root
                // Step 2: Set the local transform from quads[0].Position and quads[0].Orientation
                // Step 3: Create your hologram and set it as a child of the quad's game object
                // Step 4: Set the hologram's local transform to a translation (location.x, location.y, 0)
            }
        }
    }
}
```

I passaggi 1-4 dipendono in modo estremamente da un particolare Framework/implementazione, ma i temi dovrebbero essere simili. È importante notare che il quad rappresenta semplicemente un piano 2D con binding localizzato nello spazio. Se il motore/Framework sa dove si trova il quad e si radicano gli oggetti rispetto al quad, gli ologrammi saranno posizionati correttamente rispetto al mondo reale. Per informazioni più dettagliate, vedere gli esempi su quad che mostrano implementazioni specifiche.

### <a name="mesh"></a>Mesh

Le mesh rappresentano rappresentazioni geometriche di oggetti o ambienti. In modo analogo al [mapping spaziale](spatial-mapping.md), i dati relativi a indici mesh e vertici forniti con ogni mesh di superficie spaziale utilizzano lo stesso layout familiare dei vertex buffer e degli indici utilizzati per il rendering di mesh triangolari in tutte le moderne API per il rendering. Le posizioni dei vertici vengono fornite nel sistema di coordinate del `Scene`. Le API specifiche usate per fare riferimento a questi dati sono le seguenti:

```cs
void GetTriangleIndices(int[] indices);
void GetVertices(System.Numerics.Vector3[] vertices);
```

Il codice seguente fornisce un esempio di generazione di un elenco di triangolo dalla struttura mesh:

```cs
uint[] indices = new uint[mesh.TriangleIndexCount];
System.Numerics.Vector3[] positions = new System.Numerics.Vector3[mesh.VertexCount];

mesh.GetTriangleIndices(indices);
mesh.GetVertexPositions(positions);
```

I buffer di indice/vertice devono essere > = i conteggi di indice/vertice, ma in caso contrario possono essere dimensionati arbitrariamente, consentendo un utilizzo efficace della memoria.

## <a name="developing-with-scene-understandings"></a>Sviluppo con informazioni sulle scene

A questo punto è necessario comprendere i componenti di base della scena Understanding Runtime and SDK. La maggior parte della potenza e della complessità si basa sui modelli di accesso, sull'interazione con i framework 3D e sugli strumenti che possono essere scritti su queste API per eseguire attività più avanzate, come la pianificazione spaziale, l'analisi delle stanze, la navigazione, la fisica e così via. Ci auguriamo che questi esempi vengano acquisiti in esempi che dovrebbero guidare l'utente nella direzione corretta per rendere più brillanti gli scenari. Se sono presenti esempi/scenari non indirizzati, è possibile inviare una notifica e provare a documentare/prototipare gli elementi necessari.

### <a name="where-can-i-get-sample-code"></a>Dove è possibile ottenere il codice di esempio?

Scenario per informazioni sul codice di esempio per Unity, vedere la pagina di [esempio Unity](https://github.com/sceneunderstanding-microsoft/unitysample) . Questa applicazione consente di comunicare con il dispositivo ed eseguire il rendering dei vari oggetti scena, oppure di caricare una scena serializzata nel PC e di sperimentare la comprensione della scena senza un dispositivo.

### <a name="where-can-i-get-sample-scenes"></a>Dove è possibile ottenere scene di esempio?

Se si dispone di un HoloLens2, è possibile salvare qualsiasi scena acquisita salvando l'output di ComputeSerializedAsync in file e deserializzarlo in base alla propria convenienza. 

Se non si ha un dispositivo HoloLens2 ma si vuole giocare con la comprensione della scena, è necessario scaricare una scena pre-acquisita. L'esempio di comprensione della scena è attualmente fornito con scene serializzate che possono essere scaricate e usate con facilità. È possibile trovarli qui:

[Scene di esempio sulla comprensione della scena](https://github.com/sceneunderstanding-microsoft/unitysample/tree/master/Assets/Resources/SerializedScenesForPCPath)

## <a name="see-also"></a>Vedi anche

* [Mapping spaziale](spatial-mapping.md)
* [Informazioni sulle scene](scene-understanding.md)
* [Esempio di Unity](https://github.com/sceneunderstanding-microsoft/unitysample)

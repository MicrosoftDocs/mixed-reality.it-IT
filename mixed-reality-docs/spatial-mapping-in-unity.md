---
title: Mapping spaziale in Unity
description: Il rendering e che entrino in conflitto con la geometria del mondo reale si in Unity.
author: davidkline-ms
ms.author: davidkl
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, mapping spaziale, renderer, collider, rete, l'analisi, componente
ms.openlocfilehash: 8f7bad1651ab31b2e83ad9d9c8f465547fbbdc5a
ms.sourcegitcommit: 2f600e5ad00cd447b180b0f89192b4b9d86bbc7e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/15/2019
ms.locfileid: "67148644"
---
# <a name="spatial-mapping-in-unity"></a>Mapping spaziale in Unity

In questo argomento viene descritto come utilizzare [mapping spaziale](spatial-mapping.md) nel progetto Unity, il recupero triangolari che rappresentano aree nel mondo intorno a un dispositivo HoloLens, per il posizionamento, relative all'occlusione, chat room analisi e altro ancora.

Unity include il supporto completo per il mapping spaziale, che viene esposto agli sviluppatori nei modi seguenti:
1. I componenti disponibili nel MixedRealityToolkit mapping spaziale, che forniscono un percorso semplice e rapido per iniziare con mapping spaziale
2. Mapping spaziale di basso livello API, che forniscono completo controllare e abilitare più sofisticate di personalizzazione specifici dell'applicazione

Per usare mapping spaziale nell'app, la funzionalità spatialPerception deve essere impostata nella finestra di AppxManifest.

## <a name="setting-the-spatialperception-capability"></a>Impostare la funzionalità SpatialPerception

Affinché un'app utilizzare i dati di mapping spaziale, è necessario abilitare la funzionalità SpatialPerception.

Come abilitare la funzionalità SpatialPerception:
1. Nell'Editor di Unity, aprire il **"Windows Media Player Settings"** riquadro (Modifica > Impostazioni di progetto > Windows Media Player)
2. Fare clic sui **"Windows Store"** scheda
3. Espandere **"Impostazioni di pubblicazione"** e selezionare il **"SpatialPerception"** funzionalità nel **"Funzionalità"** elenco

Si noti che se è già stato esportato il progetto di Unity a una soluzione di Visual Studio, è necessario esportare in una nuova cartella o manualmente [impostare questa funzionalità in AppxManifest in Visual Studio](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).

Mapping spaziale richiede inoltre un MaxVersionTested di 10.0.10586.0 almeno:
1. In Visual Studio, fare clic sulla **package. appxmanifest** in Esplora soluzioni e selezionare **Visualizza codice**
2. Trovare la riga che specifica **TargetDeviceFamily** e modificare **MaxVersionTested = "10.0.10240.0"** a **MaxVersionTested "Version=10.0.10586.0"**
3. **Salvare** il package. appxmanifest.

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a>Introduzione a componenti di mapping spaziale predefiniti di Unity

Unity offre 2 componenti per facilmente aggiunta all'app, mapping spaziale **Renderer Mapping spaziale** e **Collider Mapping spaziale**.

### <a name="spatial-mapping-renderer"></a>Renderer di Mapping spaziale

Il Renderer di Mapping spaziale consente la visualizzazione della trama mapping spaziale.

![Mapping spaziale Renderer in Unity](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a>Mapping spaziale Collider

L'oggetto Collider Mapping spaziale consente holographic contenuto (o carattere) interazione, ad esempio fisica, con la rete di mapping spaziale.

![Mapping spaziale Collider in Unity](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a>Usando i componenti predefiniti mapping spaziale

Se si desidera sia possibile visualizzare e interagire con le superfici fisiche, è possibile aggiungere entrambi i componenti all'app.

Per usare questi due componenti nell'app Unity:
1. Selezionare un GameObject al centro dell'area in cui si desidera rilevare le reti mesh di superficie spaziale.
2. Nella finestra Inspector **Add Component** > **XR** > **Collider Mapping spaziale** o **spaziale Renderer di mapping**.

È possibile trovare altre informazioni su come usare questi componenti al <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">sito della documentazione di Unity</a>.

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a>Non si limita i componenti predefiniti mapping spaziale

Questi componenti rendono drag-and-drop facile iniziare a usare Mapping spaziale.  Quando si desidera continuare, esistono due modi principali per esplorare:
* Per eseguire l'elaborazione di rete di livello inferiore, vedere la sezione seguente sullo script Mapping spaziale a basso livello API.
* Per eseguire analisi di rete di livello superiore, vedere la sezione seguente sulla libreria in SpatialUnderstanding <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>.

## <a name="using-the-low-level-unity-spatial-mapping-api"></a>Con basso livello API di Unity spaziali Mapping

Se è necessario maggiore controllo, quella che si dai componenti Renderer Mapping spaziale e Collider Mapping spaziale, è possibile usare lo script Mapping spaziale a basso livello API.

**Namespace:** *UnityEngine.XR.WSA*<br>
**Tipi**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*

Di seguito è una struttura del flusso di suggerita per un'applicazione che usa l'API di mapping spaziale.

### <a name="set-up-the-surfaceobservers"></a>Configurare il SurfaceObserver(s)

Creare un'istanza di un oggetto SurfaceObserver per ogni area definita dall'applicazione di spazio che sono necessari dati di mapping spaziale per.

```cs
SurfaceObserver surfaceObserver;

 void Start () {
     surfaceObserver = new SurfaceObserver();
 }
```

Specificare l'area di spazio su ogni oggetto SurfaceObserver verrà recuperati i dati per chiamando SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox o SetVolumeAsFrustum. Chiamando semplicemente uno di questi metodi anche in questo caso, è possibile ridefinire l'area di spazio in futuro.

```cs
void Start () {
    ...
     surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

Quando si chiama SurfaceObserver.Update(), è necessario fornire un gestore per ogni area spaziale nell'area del SurfaceObserver dello spazio che il sistema di mapping spaziale contiene informazioni per la nuova. Il gestore riceve, per una sola superficie spaziale:

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
 {
    //see Handling Surface Changes
 }
```

### <a name="handling-surface-changes"></a>Gestione delle modifiche di Surface

Esistono diversi casi principali per la gestione. Aggiunte e aggiornate che è possono usare lo stesso codice di percorso e rimosso.
* Nei casi sono state aggiunte e aggiornate nell'esempio, aggiungere o ottenere il GameObject che rappresenta questo mesh dal dizionario, creare un tipo struct SurfaceData con i componenti necessari, quindi chiamare RequestMeshDataAsync per popolare gli elementi GameObject con i dati di trama e posizione della scena.
* In caso di rimozione, è rimuovere gli elementi GameObject che rappresenta questo reticolato dal dizionario ed eliminarla definitivamente.

```cs
System.Collections.Generic.Dictionary<SurfaceId, GameObject> spatialMeshObjects = 
    new System.Collections.Generic.Dictionary<SurfaceId, GameObject>();

   private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
   {
       switch (changeType)
       {
           case SurfaceChange.Added:
           case SurfaceChange.Updated:
               if (!spatialMeshObjects.ContainsKey(surfaceId))
               {
                   spatialMeshObjects[surfaceId] = new GameObject("spatial-mapping-" + surfaceId);
                   spatialMeshObjects[surfaceId].transform.parent = this.transform;
                   spatialMeshObjects[surfaceId].AddComponent<MeshRenderer>();
               }
               GameObject target = spatialMeshObjects[surfaceId];
               SurfaceData sd = new SurfaceData(
                   //the surface id returned from the system
                   surfaceId,
                   //the mesh filter that is populated with the spatial mapping data for this mesh
                   target.GetComponent<MeshFilter>() ?? target.AddComponent<MeshFilter>(),
                   //the world anchor used to position the spatial mapping mesh in the world
                   target.GetComponent<WorldAnchor>() ?? target.AddComponent<WorldAnchor>(),
                   //the mesh collider that is populated with collider data for this mesh, if true is passed to bakeMeshes below
                   target.GetComponent<MeshCollider>() ?? target.AddComponent<MeshCollider>(),
                   //triangles per cubic meter requested for this mesh
                   1000,
                   //bakeMeshes - if true, the mesh collider is populated, if false, the mesh collider is empty.
                   true
                   );

               SurfaceObserver.RequestMeshAsync(sd, OnDataReady);
               break;
           case SurfaceChange.Removed:
               var obj = spatialMeshObjects[surfaceId];
               spatialMeshObjects.Remove(surfaceId);
               if (obj != null)
               {
                   GameObject.Destroy(obj);
               }
               break;
           default:
               break;
       }
   }
```

### <a name="handling-data-ready"></a>Pronto per la gestione dei dati

Il gestore OnDataReady riceve un oggetto SurfaceData. Il WorldAnchor, MeshFilter e (facoltativamente) MeshCollider oggetti in che esso contenuti riflettono lo stato più recente della superficie spaziale associato. Se lo si desidera eseguire l'analisi e/o [elaborazione](spatial-mapping.md#mesh-processing) dei dati per l'accesso al membro della Mesh dell'oggetto MeshFilter mesh. Il rendering dell'area spaziale con la rete di più recente e (facoltativamente) usato per i conflitti di fisica e raycasts. È importante verificare che il contenuto della finestra di SurfaceData non sia null.

### <a name="start-processing-on-updates"></a>Iniziare a elaborare gli aggiornamenti

SurfaceObserver.Update() deve essere chiamato su un ritardo, non per ogni fotogramma.

```cs
void Start () {
    ...
     StartCoroutine(UpdateLoop());
}

 IEnumerator UpdateLoop()
    {
        var wait = new WaitForSeconds(2.5f);
        while(true)
        {
            surfaceObserver.Update(OnSurfaceChanged);
            yield return wait;
        }
    }
```

## <a name="higher-level-mesh-analysis-spatialunderstanding"></a>Analisi di rete mesh di livello superiore: SpatialUnderstanding

Il <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> è una raccolta di codice di utilità utili per lo sviluppo holographic basato sull'API di Unity holographic.

### <a name="spatial-understanding"></a>Understanding spaziali

Quando si posiziona vntana nel mondo fisico è spesso utile andare oltre mapping spaziale mesh e regolatori della superficie di attacco. Al termine posizionamento modo procedurale, è consigliabile un livello superiore di comprensione dell'ambiente. È in genere necessario prendere decisioni sulle novità walls, floor e ceiling. Inoltre, la possibilità di ottimizzare rispetto a un set di vincoli di posizionamento per determinare i percorsi fisici più utile per gli oggetti holographic.

Durante lo sviluppo di Conker Young e frammenti, Studios Asobo affrontato head questo problema in sviluppo Risolutore di chat room per questo scopo. Ognuno di questi giochi ha esigenze specifiche dei giochi, ma quelle condivise informazioni spaziali sulla tecnologia di base. Il HoloToolkit.SpatialUnderstanding libreria incapsula questa tecnologia, consentendo di rapidamente trovare gli spazi vuoti nelle pareti, collocare oggetti nel tetto massimo, identificare inserito per carattere per un periodo e una miriade di altre query spaziali comprensione.

Tutto il codice sorgente è incluso, consentendo di personalizzarlo in base alle esigenze e condividere i miglioramenti con la community. Il codice per il C++ è stato eseguito il wrapping in una dll UWP ed esposto a Unity con una diminuzione prefab contenuti all'interno di MixedRealityToolkit Risolutore.

### <a name="understanding-modules"></a>Informazioni sui moduli

Sono disponibili tre interfacce principali esposte dal modulo: topologia per area semplice e le query spaziali e forma per il rilevamento di oggetti del Risolutore di selezione host per oggetti per la selezione host di vincoli basato del set di oggetti. Ognuno di questi è descritto di seguito. Oltre alle tre interfacce modulo primario, un'interfaccia di eseguire il cast di ray è utilizzabile per recuperare i tipi di area con tag e una rete mesh playspace stagni personalizzati possono essere copiate.

### <a name="ray-casting"></a>Cast di ray

Dopo la chat è stata analizzata e finalizzata, le etichette vengono generate internamente per superfici come walls, floor e ceiling. La "PlayspaceRaycast" funzione accetta un raggio e restituisce se il raggio è in conflitto con una superficie nota e in tal caso, informazioni che verranno visualizzati sotto forma di un "RaycastResult".

```cpp
struct RaycastResult
{
    enum SurfaceTypes
    {
        Invalid,    // No intersection
        Other,
        Floor,
        FloorLike,  // Not part of the floor topology, 
                    //  but close to the floor and looks like the floor
        Platform,   // Horizontal platform between the ground and 
                    //  the ceiling
        Ceiling,
        WallExternal,
        WallLike,   // Not part of the external wall surface, 
                    //  but vertical surface that looks like a 
                    //  wall structure
    };
    SurfaceTypes SurfaceType;
    float SurfaceArea;  // Zero if unknown 
                        //  (i.e. if not part of the topology analysis)
    DirectX::XMFLOAT3 IntersectPoint;
    DirectX::XMFLOAT3 IntersectNormal;
};
```

Internamente, viene calcolato il raycast contro la rappresentazione di voxel calcolata cm 8 al cubo del playspace. Ogni voxel contiene un set di elementi della superficie con i dati elaborati topologia (noto anche come surfels). Vengono confrontate le surfels contenute all'interno delle celle intersecate voxel e la migliore corrispondenza utilizzata per cercare le informazioni sulla topologia. Data questa topologia contiene l'assegnazione di etichette restituito in forma di enumerazione "SurfaceTypes", nonché la superficie dell'area di intersezione.

Nell'esempio di Unity, il cursore viene eseguito il cast un raggio ogni fotogramma. Prima di tutto rispetto colliders di Unity. In secondo luogo, sulla rappresentazione mondo del modulo comprensione. E infine, anche in questo caso elementi dell'interfaccia utente. In questa applicazione, dell'interfaccia utente ottiene quindi priorità, il risultato di comprensione e, infine, colliders di Unity. Il SurfaceType viene segnalato come testo accanto al cursore.

![Tipo di area con l'etichetta accanto al cursore](images/su-raycastresults-300px.jpg)<br>
*Tipo di area con l'etichetta accanto al cursore*

### <a name="topology-queries"></a>Query di topologia

All'interno della DLL, gestione della topologia gestisce l'assegnazione di etichette dell'ambiente. Come indicato in precedenza, gran parte dei dati verrà archiviata all'interno di surfels, contenuta all'interno di un volume voxel. Inoltre, la struttura "PlaySpaceInfos" viene utilizzata per archiviare le informazioni sugli playspace, tra cui l'allineamento world (ulteriori dettagli su questo argomento di seguito), floor e ceiling altezza. Vengono usate le euristiche per determinare walls, floor e ceiling. Ad esempio, la superficie più grande e più basso orizzontale con maggiore di 1 m2 superficie di attacco è considerata il tetto minimo. Si noti che il percorso della fotocamera durante il processo di analisi viene usato anche in questo processo.

Un subset delle query esposte da Gestione della topologia sono esposte tramite la dll. Di seguito sono riportate le query di topologia esposto.

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

Ogni query dispone di un set di parametri, specifici per il tipo di query. Nell'esempio seguente, l'utente specifica l'altezza minima & larghezza del volume desiderato, altezza minima posizione di sopra la parte intera e la quantità minima di nulla osta davanti il volume. Tutte le misure sono in metri.

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

Ognuna di queste query accetta una matrice di strutture "TopologyResult" pre-allocata. Il parametro "locationCount" Specifica la lunghezza della matrice passata. Il valore restituito indica il numero di percorsi restituiti. Questo numero non è mai maggiore il valore passato nel parametro "locationCount".

"TopologyResult" contiene la posizione centrale del volume restituito, la direzione pubblico (ad esempio normale) e le dimensioni dello spazio trovato.

```cpp
struct TopologyResult 
{ 
    DirectX::XMFLOAT3 position; 
    DirectX::XMFLOAT3 normal; 
    float width; 
    float length;
};
```

Si noti che nell'esempio di Unity, ognuna di queste query è collegato a un pulsante nel pannello dell'interfaccia utente virtuale. L'esempio rigido codici i parametri per ognuna di queste query valori ragionevoli. Nell'esempio di codice per altri esempi, vedere SpaceVisualizer.cs.

### <a name="shape-queries"></a>Query di forma

All'interno della dll, l'analizzatore di forma ("ShapeAnalyzer_W") usa l'analizzatore di topologia da confrontare con le forme personalizzate definite dall'utente. L'esempio di Unity definisce un set di forme ed espone i risultati out tramite il menu di query in-app, all'interno della scheda di forma. L'obiettivo è che l'utente può definire le proprie query forma di oggetto e rendere utilizzo di questi strumenti, in base alle necessità da parte delle applicazioni.

Si noti che l'analisi della forma funziona su superfici orizzontale solo. Un divano, ad esempio, è definito per l'area di postazione flat e flat cima divano nuovamente. La query shape è simile per due aree di un determinato intervallo di dimensioni, altezza e aspetto, con due aree delle allineato e connesse. Utilizzando la terminologia di API, il divano postazione e top indietro sono componenti di forma e i requisiti di allineamento sono limitazioni dei componenti di forma.

Un esempio di query definita nell'esempio di Unity (ShapeDefinition.cs), per gli oggetti "sittable" è come indicato di seguito.

```cs
shapeComponents = new List<ShapeComponent>()
{
    new ShapeComponent(
        new List<ShapeComponentConstraint>()
        {
            ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
            ShapeComponentConstraint.Create_SurfaceCount_Min(1),
            ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
        }
    ),
};
AddShape("Sittable", shapeComponents);
```

Ogni query shape è definita da un set di componenti di forma, ognuno con un set di limitazioni dei componenti e un set di vincoli di forma che elenca le dipendenze tra i componenti. Questo esempio include tre vincoli in una definizione di singoli componenti e senza vincoli di forme tra i componenti (perché è presente un solo componente).

Al contrario, la forma divano presenta due componenti di forma e quattro i vincoli di forma. Si noti che i componenti vengono identificati tramite il relativo indice nell'elenco dei componenti dell'utente (0 e 1 in questo esempio).

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

Le funzioni wrapper vengono fornite nel modulo di Unity per la creazione di definizioni di forma personalizzata. L'elenco completo dei vincoli di componente e la forma è reperibile in "SpatialUnderstandingDll.cs" all'interno di strutture "ShapeConstraint" e "ShapeComponentConstraint".

![Forma rettangolare è disponibile in questa area](images/su-shapequery-300px.jpg)<br>
*Forma rettangolare è disponibile in questa area*

### <a name="object-placement-solver"></a>Oggetto Risolutore di selezione host

Risolutore di selezione host per l'oggetto è utilizzabile per identificare le posizioni ideale nella chat room fisica per posizionare gli oggetti. Il Risolutore troverà che il miglior fit posizione determinata le regole di oggetti e i vincoli. Inoltre, le query di oggetto persistono fino a quando l'oggetto è stata rimossa con "Solver_RemoveObject" o "Solver_RemoveAllObjects" chiamate, consentendo vincolata selezione host per oggetti multipli. Le query di selezione host per gli oggetti sono costituiti da tre parti: il tipo con parametri, un elenco di regole e un elenco di vincoli di posizionamento. Per eseguire una query, usare l'API seguente.

```cpp
public static int Solver_PlaceObject(
            [In] string objectName,
            [In] IntPtr placementDefinition,        // ObjectPlacementDefinition
            [In] int placementRuleCount,
            [In] IntPtr placementRules,             // ObjectPlacementRule
            [In] int constraintCount,
            [In] IntPtr placementConstraints,       // ObjectPlacementConstraint
            [Out] IntPtr placementResult)
```

Questa funzione accetta un nome di oggetto, definizione di selezione host e un elenco delle regole e dei vincoli. Il C# wrapper fornisce costruzione funzioni helper per semplificare la costruzione di regole e dei vincoli. La definizione di selezione host contiene il tipo di query, vale a dire, uno dei seguenti.

```cpp
public enum PlacementType
            {
                Place_OnFloor,
                Place_OnWall,
                Place_OnCeiling,
                Place_OnShape,
                Place_OnEdge,
                Place_OnFloorAndCeiling,
                Place_RandomInAir,
                Place_InMidAir,
                Place_UnderFurnitureEdge,
            };
```

Ognuno dei tipi di selezione host dispone di un set di parametri univoci per il tipo. La struttura "ObjectPlacementDefinition" contiene un set di funzioni di supporto statici per la creazione di queste definizioni. Per trovare una posizione in cui inserire un oggetto nell'ambiente operativo, ad esempio, è possibile usare la funzione seguente. pubblico statico ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) oltre al tipo di selezione host, è possibile fornire un set di regole e i vincoli. Regole non possono essere violate. Percorsi selezione host per possibili che soddisfano il tipo e le regole sono ottimizzati quindi a fronte del set di vincoli per poter selezionare il percorso di posizionamento ottimale. Ognuna delle regole e i vincoli può essere creata da funzioni di creazione statici specificato. Una funzione di costruzione regole e dei vincoli di esempio è disponibili sotto.

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

Il seguente oggetto query di selezione host sta cercando una posizione in cui inserire un misuratore metà cubo sul bordo di una superficie, da altra in precedenza posizionare gli oggetti e vicino al centro della chat room.

```cs
List<ObjectPlacementRule> rules = 
    new List<ObjectPlacementRule>() {
        ObjectPlacementRule.Create_AwayFromOtherObjects(1.0f),
    };

List<ObjectPlacementConstraint> constraints = 
    new List<ObjectPlacementConstraint> {
        ObjectPlacementConstraint.Create_NearCenter(),
    };

Solver_PlaceObject(
    “MyCustomObject”,
    new ObjectPlacementDefinition.Create_OnEdge(
        new Vector3(0.25f, 0.25f, 0.25f), 
        new Vector3(0.25f, 0.25f, 0.25f)),
    rules.Count,
    UnderstandingDLL.PinObject(rules.ToArray()),
    constraints.Count,
    UnderstandingDLL.PinObject(constraints.ToArray()),
    UnderstandingDLL.GetStaticObjectPlacementResultPtr());
```

Se ha esito positivo, una struttura di "ObjectPlacementResult" contenente la posizione di posizionamento, dimensioni e orientamento viene restituito. Inoltre, la selezione host viene aggiunto all'elenco interno della dll di oggetti inseriti. Le query di selezione successiva dovrà tener conto di questo oggetto. Il file "LevelSolver.cs" nell'esempio di Unity contiene più query di esempio.

![Risultati della selezione host per oggetto](images/su-objectplacement-1000px.jpg)<br>
*Figura 3: Caselle blu come il risultato da tre posizione floor esegue una query con lontano da regole di posizione della fotocamera*

Durante la risoluzione per il percorso di posizionamento di più oggetti necessari per uno scenario di applicazione o a un livello, risolvere innanzitutto gli oggetti indispensabili e grandi dimensioni in ordine di ottimizzazione della probabilità che può essere trovato uno spazio. Ordine di inserimento è importante. Se selezioni host per oggetti non viene trovato, provare a configurazioni meno vincolate. Un set di configurazioni di fallback è fondamentale per la funzionalità di supporto in molte configurazioni di chat room.

### <a name="room-scanning-process"></a>Processo di analisi chat room

Mentre la soluzione di mapping spaziale fornita da di HoloLens è progettata per essere abbastanza generici per soddisfare le esigenze dell'intera gamma di aree di problemi, il modulo understanding spaziale è stato compilato per supportare le esigenze dei giochi specifiche due. La soluzione è strutturata su un processo specifico e un set dei presupposti, riepilogate di seguito.

```
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process – 
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace. 
    Query functions will not function until after the scan has been finalized.
```

Utente basato sui playspace "disegno" – durante la fase di analisi, l'utente si sposta e Cerca intorno al passo, la riproduzione della grafica in modo efficace le aree che devono essere incluse. La trama generata è importante fornire commenti e suggerimenti utente durante questa fase. In ambienti chiusi home o l'installazione di office: la query funzioni sono progettate sulla base di superfici flat e walls ad angolo retto. Si tratta di una limitazione temporanea. Tuttavia, durante la fase di analisi, un'asse primario viene completata l'analisi per ottimizzare la suddivisione a mosaico di mesh lungo l'asse principale e secondaria. Il file SpatialUnderstanding.cs incluso gestisce il processo di fase di analisi. Chiama le funzioni seguenti.

```
SpatialUnderstanding_Init – Called once at the start.

GeneratePlayspace_InitScan – Indicates that the scan phase should begin.

GeneratePlayspace_UpdateScan_DynamicScan – 
    Called each frame to update the scanning process. The camera position and 
    orientation is passed in and is used for the playspace painting process, 
    described above.

GeneratePlayspace_RequestFinish – 
    Called to finalize the playspace. This will use the areas “painted” during 
    the scan phase to define and lock the playspace. The application can query 
    statistics during the scanning phase as well as query the custom mesh for 
    providing user feedback.

Import_UnderstandingMesh – 
    During scanning, the “SpatialUnderstandingCustomMesh” behavior provided by 
    the module and placed on the understanding prefab will periodically query the 
    custom mesh generated by the process. In addition, this is done once more 
    after scanning has been finalized.
```

Il flusso di analisi, dovuto il comportamento di "SpatialUnderstanding" chiama il metodo InitScan, UpdateScan ogni fotogramma. Durante la query statistiche report code coverage ragionevole, l'utente è autorizzato a airtap chiamare RequestFinish per indicare la fine della fase di analisi. UpdateScan continua a essere chiamato finché non viene restituito il valore indica che la dll è stata completata l'elaborazione.

### <a name="understanding-mesh"></a>Informazioni sulle Mesh

Informazioni sulle dll archivia internamente il playspace come una griglia dei cubi voxel 8cm ridimensionato. Durante la parte iniziale di analisi, per determinare gli assi della chat room viene completata un'analisi in componenti principali. Archivia internamente, il relativo spazio voxel allineato a questi assi. Una rete mesh viene generata circa ogni secondo, estraendo l'oggetto isosurface dal volume voxel. 

![Mesh generato prodotta dal volume voxel](images/su-custommesh.jpg)<br>
*Mesh generato prodotta dal volume voxel*

## <a name="troubleshooting"></a>Risoluzione dei problemi
* Assicurarsi di aver impostato la [SpatialPerception](#setting-the-spatialperception-capability) funzionalità
* Quando il rilevamento viene perso, il successivo evento OnSurfaceChanged rimuoverà tutte le reti mesh.

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a>Mapping spaziale nel Toolkit di realtà mista
Per altre informazioni sull'uso di Mapping spaziale con v2 Toolkit di realtà mista, vedere la <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">sezione consapevolezza spaziali</a> della documentazione MRTK.

## <a name="see-also"></a>Vedere anche
* [Spaziale MR 230: Mapping spaziale](holograms-230.md)
* [Sistemi di coordinate](coordinate-systems.md)
* [Sistemi di coordinate in Unity](coordinate-systems-in-unity.md)
* <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a>
* <a href="http://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a>
* <a href="http://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a>
* <a href="http://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a>

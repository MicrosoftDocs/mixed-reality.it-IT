---
title: Mapping spaziale in Unity
description: Il rendering e la collisione con la geometria del mondo reale in Unity.
author: davidkline-ms
ms.author: davidkl
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, mapping spaziale, renderer, Collider, mesh, analisi, componente
ms.openlocfilehash: 452e629a877df585ffbc0a6466ffeb2588b66ecf
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438040"
---
# <a name="spatial-mapping-in-unity"></a>Mapping spaziale in Unity

Questo argomento descrive come usare il [mapping spaziale](spatial-mapping.md) nel progetto Unity, il recupero di mesh triangolari che rappresentano le superfici del mondo intorno a un dispositivo HoloLens, per la selezione, l'occlusione, l'analisi delle chat room e altro ancora.

Unity include il supporto completo per il mapping spaziale, esposto agli sviluppatori nei modi seguenti:
1. Componenti di mapping spaziale disponibili in MixedRealityToolkit, che offrono un percorso pratico e rapido per iniziare a usare il mapping spaziale
2. API di mapping spaziale di basso livello, che offrono il controllo completo e consentono una personalizzazione più sofisticata dell'applicazione

Per usare il mapping spaziale nell'app, è necessario impostare la funzionalità spatialPerception in AppxManifest.

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
        <td>Mapping spaziale</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="setting-the-spatialperception-capability"></a>Impostazione della funzionalità SpatialPerception

Per consentire a un'app di utilizzare i dati di mapping spaziale, è necessario abilitare la funzionalità SpatialPerception.

Come abilitare la funzionalità SpatialPerception:
1. Nell'editor di Unity aprire il riquadro **"Impostazioni lettore"** (modificare > impostazioni progetto > lettore)
2. Fare clic sulla scheda **"Windows Store"**
3. Espandere **"impostazioni di pubblicazione"** e selezionare la funzionalità **"SpatialPerception"** nell'elenco **"funzionalità"**

Si noti che se il progetto Unity è già stato esportato in una soluzione di Visual Studio, sarà necessario eseguire l'esportazione in una nuova cartella o [impostare manualmente questa funzionalità in appxmanifest in Visual Studio](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).

Il mapping spaziale richiede anche un MaxVersionTested di almeno 10.0.10586.0:
1. In Visual Studio fare clic con il pulsante destro del mouse su **Package. appxmanifest** nel Esplora soluzioni e selezionare **Visualizza codice** .
2. Trovare la riga che specifica **TargetDeviceFamily** e modificare **MaxVersionTested = "10.0.10240.0"** in **MaxVersionTested = "10.0.10586.0"**
3. **Salvare** il pacchetto. appxmanifest.

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a>Introduzione ai componenti di mapping spaziale incorporati di Unity

Unity offre 2 componenti per aggiungere facilmente il mapping spaziale all'app, al **renderer di mapping spaziale** e al **mapping spaziale**.

### <a name="spatial-mapping-renderer"></a>Renderer mapping spaziale

Il renderer di mapping spaziale consente la visualizzazione della mesh di mapping spaziale.

![Renderer di mapping spaziale in Unity](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a>Conflitto di mapping spaziale

Il mapping spaziale Collider consente l'interazione di contenuto (o carattere) olografico, ad esempio la fisica, con la mesh di mapping spaziale.

![Conflitto di mapping spaziale in Unity](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a>Uso dei componenti di mapping spaziale predefiniti

È possibile aggiungere entrambi i componenti all'app se si vuole visualizzare e interagire con le superfici fisiche.

Per usare questi due componenti nell'app Unity:
1. Selezionare un GameObject al centro dell'area in cui si desidera rilevare le mesh della superficie spaziale.
2. Nella finestra di controllo **aggiungere Component** > **XR** > **Spatial mapping Collider** o il renderer di **mapping spaziale**.

Per altre informazioni su come usare questi componenti, vedere il sito della <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">documentazione di Unity</a>.

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a>Superamento dei componenti predefiniti di mapping spaziale

Questi componenti rendono semplice il trascinamento della selezione per iniziare a usare il mapping spaziale.  Quando si vuole proseguire, è possibile esplorare due percorsi principali:
* Per eseguire l'elaborazione della mesh di livello inferiore, vedere la sezione seguente sull'API script per il mapping spaziale di basso livello.
* Per eseguire un'analisi della rete di livello superiore, vedere la sezione seguente sulla libreria SpatialUnderstanding in <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>.

## <a name="using-the-low-level-unity-spatial-mapping-api"></a>Uso dell'API di mapping spaziale di Unity di basso livello

Se è necessario un maggiore controllo di quanto si ottenga dal renderer di mapping spaziale e dai componenti Collider del mapping spaziale, è possibile usare le API script per il mapping spaziale di basso livello.

**Spazio dei nomi:** *UnityEngine. XR. WSA*<br>
**Tipi**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*

Di seguito è riportato un contorno del flusso suggerito per un'applicazione che usa le API di mapping spaziale.

### <a name="set-up-the-surfaceobservers"></a>Configurare i SurfaceObserver

Creare un'istanza di un oggetto SurfaceObserver per ogni area di spazio definita dall'applicazione per cui sono necessari dati di mapping spaziali.

```cs
SurfaceObserver surfaceObserver;

 void Start () {
     surfaceObserver = new SurfaceObserver();
 }
```

Specificare l'area di spazio a cui ogni oggetto SurfaceObserver fornirà i dati chiamando SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox o SetVolumeAsFrustum. È possibile ridefinire l'area di spazio in futuro semplicemente richiamando uno di questi metodi.

```cs
void Start () {
    ...
     surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

Quando si chiama SurfaceObserver. Update (), è necessario fornire un gestore per ogni superficie spaziale nell'area di spazio di SurfaceObserver per cui il sistema di mapping spaziale dispone di nuove informazioni. Il gestore riceve, per una superficie spaziale:

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
 {
    //see Handling Surface Changes
 }
```

### <a name="handling-surface-changes"></a>Gestione delle modifiche di superficie

Esistono diversi casi principali da gestire. Aggiunta & aggiornata che può utilizzare lo stesso percorso di codice e rimossa.
* Nei casi aggiunti & aggiornati nell'esempio, si aggiunge o si ottiene il GameObject che rappresenta la mesh dal dizionario, si crea uno struct SurfaceData con i componenti necessari, quindi si chiama RequestMeshDataAsync per popolare il GameObject con i dati mesh e posizione nella scena.
* Nel caso rimosso, viene rimosso il GameObject che rappresenta il mesh dal dizionario ed eliminarlo.

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

### <a name="handling-data-ready"></a>Gestione dei dati pronti

Il gestore OnDataReady riceve un oggetto SurfaceData. Gli oggetti WorldAnchor, MeshFilter e (facoltativamente) MeshCollider che contiene riflettono lo stato più recente della superficie spaziale associata. Eseguire facoltativamente l'analisi e/o l' [elaborazione](spatial-mapping.md#mesh-processing) dei dati mesh accedendo al membro mesh dell'oggetto MeshFilter. Eseguire il rendering della superficie spaziale con la mesh più recente e, facoltativamente, usarla per collisioni fisiche e raycasts. È importante verificare che il contenuto di SurfaceData non sia null.

### <a name="start-processing-on-updates"></a>Avviare l'elaborazione degli aggiornamenti

SurfaceObserver. Update () deve essere chiamato su un ritardo, non su tutti i frame.

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

## <a name="higher-level-mesh-analysis-spatialunderstanding"></a>Analisi mesh di livello superiore: SpatialUnderstanding

<a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> è una raccolta di utili codici di utilità per lo sviluppo olografico basato sulle API olografiche di Unity.

### <a name="spatial-understanding"></a>Conoscenza spaziale

Quando si posizionano gli ologrammi nel mondo fisico è spesso consigliabile andare oltre i piani di rete e superficie del mapping spaziale. Quando il posizionamento viene eseguito in maniera procedurale, è auspicabile un livello superiore di comprensione ambientale. Questa operazione richiede in genere le decisioni relative a pavimenti, massimali e muri. Inoltre, la possibilità di eseguire l'ottimizzazione rispetto a un set di vincoli di posizionamento per determinare le posizioni fisiche più desiderate per gli oggetti olografici.

Durante lo sviluppo di Conker e frammenti giovani, Asobo Studios ha affrontato questo problema, sviluppando un risolutore di spazio a questo scopo. Ognuno di questi giochi ha esigenze specifiche del gioco, ma ha condiviso la tecnologia principale per la comprensione spaziale. La libreria HoloToolkit. SpatialUnderstanding incapsula questa tecnologia, consentendo di trovare rapidamente gli spazi vuoti sulle pareti, posizionare gli oggetti sul soffitto, identificare posizionati per il carattere da collocare e una miriade di altre query di comprensione spaziale.

Tutto il codice sorgente è incluso, consentendo di personalizzarlo in base alle proprie esigenze e condividere i miglioramenti con la community. Il codice per il C++ Risolutore è stato sottoposto a incapsulamento in una DLL di UWP ed esposto a Unity con una riduzione della prefabbricata contenuta nel MixedRealityToolkit.

### <a name="understanding-modules"></a>Informazioni sui moduli

Sono disponibili tre interfacce primarie esposte dal modulo: topologia per query di superficie e spaziali semplici, forma per il rilevamento di oggetti e il Risolutore di posizionamento degli oggetti per il posizionamento basato sui vincoli dei set di oggetti. Ognuno di questi è descritto di seguito. Oltre alle tre interfacce del modulo principale, è possibile usare un'interfaccia di cast di tipo Ray per recuperare i tipi di superficie con tag ed è possibile copiare una mesh playspace stermetica personalizzata.

### <a name="ray-casting"></a>Casting Ray

Dopo che la chat è stata sottoposta a scansione e finalizzata, le etichette vengono generate internamente per superfici quali il piano, il soffitto e i muri. La funzione "PlayspaceRaycast" accetta un raggio e restituisce se il raggio è in conflitto con una superficie nota e, in tal caso, le informazioni su tale superficie sotto forma di "RaycastResult".

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

Internamente, il Raycast viene calcolato rispetto alla rappresentazione voxel del cubo di 8cm calcolata del playspace. Ogni voxel contiene un set di elementi Surface con dati della topologia elaborati (noto anche come surfels). Il surfels contenuto all'interno della cella voxel intersecata viene confrontato e la migliore corrispondenza utilizzata per cercare le informazioni sulla topologia. Questi dati della topologia contengono l'etichettatura restituita nel formato dell'enumerazione "SurfaceTypes", nonché la superficie di attacco della superficie intersecata.

Nell'esempio Unity il cursore esegue il cast di un raggio per ogni fotogramma. In primo luogo, rispetto ai Collider di Unity. In secondo luogo, sulla rappresentazione mondiale del modulo di informazioni. Infine, di nuovo gli elementi dell'interfaccia utente. In questa applicazione, l'interfaccia utente ottiene la priorità, successivamente il risultato della comprensione e infine i Collider di Unity. SurfaceType viene segnalato come testo accanto al cursore.

![tipo di superficie è etichettato accanto al cursore](images/su-raycastresults-300px.jpg)<br>
*Il tipo di superficie è contrassegnato accanto al cursore*

### <a name="topology-queries"></a>Query sulla topologia

All'interno della DLL, Gestione topologia gestisce l'assegnazione di etichette all'ambiente. Come indicato in precedenza, gran parte dei dati viene archiviata in surfels, contenuta in un volume voxel. Inoltre, la struttura "PlaySpaceInfos" viene usata per archiviare le informazioni relative a playspace, incluso l'allineamento internazionale (altre informazioni su questo argomento), il piano e l'altezza del soffitto. Vengono usate le regole euristiche per determinare il piano, il soffitto e i muri. Ad esempio, la superficie orizzontale più grande e più bassa con una superficie di attacco maggiore di 1 m2 viene considerata il piano. Si noti che in questo processo viene usato anche il percorso della fotocamera durante il processo di analisi.

Un subset delle query esposte dal gestore della topologia viene esposto tramite la dll. Di seguito sono riportate le query topologia esposte.

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

Ogni query ha un set di parametri, specifico del tipo di query. Nell'esempio seguente l'utente specifica l'altezza minima & larghezza del volume desiderato, l'altezza minima di posizionamento sopra il piano e la quantità minima di spazio di autorizzazione davanti al volume. Tutte le misurazioni sono in metri.

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

Ognuna di queste query accetta una matrice pre-allocata di strutture "TopologyResult". Il parametro "locationCount" specifica la lunghezza della matrice passata. Il valore restituito indica il numero di posizioni restituite. Questo numero non è mai superiore al parametro "locationCount" passato.

"TopologyResult" contiene la posizione centrale del volume restituito, la direzione (ovvero normale) e le dimensioni dello spazio trovato.

```cpp
struct TopologyResult 
{ 
    DirectX::XMFLOAT3 position; 
    DirectX::XMFLOAT3 normal; 
    float width; 
    float length;
};
```

Si noti che nell'esempio Unity ogni query è collegata a un pulsante nel pannello dell'interfaccia utente virtuale. L'esempio codifica in modo rigido i parametri per ognuna di queste query in valori ragionevoli. Per altri esempi, vedere SpaceVisualizer.cs nel codice di esempio.

### <a name="shape-queries"></a>Query di forma

All'interno della dll, l'analizzatore di forme ("ShapeAnalyzer_W") utilizza l'analizzatore della topologia per trovare la corrispondenza con le forme personalizzate definite dall'utente. L'esempio Unity definisce un set di forme ed espone i risultati tramite il menu query in-app, all'interno della scheda Shape. L'intenzione è che l'utente possa definire le proprie query di forma oggetto e utilizzarle, in base alle esigenze dell'applicazione.

Si noti che l'analisi delle forme funziona solo su superfici orizzontali. Un divano, ad esempio, viene definito dalla superficie della postazione piatta e dalla parte superiore piatta del divano. La query Shape cerca due superfici di dimensioni, altezze e intervalli di aspetto specifici, con le due superfici allineate e connesse. Con la terminologia relativa alle API, il divano e la parte superiore sono componenti di forma e i requisiti di allineamento sono vincoli dei componenti della forma.

Di seguito è riportata una query di esempio definita nell'esempio Unity (ShapeDefinition.cs) per gli oggetti "SitTable".

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

Ogni query di forma è definita da un set di componenti di forma, ognuno con un set di vincoli di componente e un set di vincoli di forma che elencano le dipendenze tra i componenti. Questo esempio include tre vincoli in una definizione di componente singolo e nessun vincolo di forma tra i componenti (in quanto è presente un solo componente).

Al contrario, la forma Couch presenta due componenti di forma e quattro vincoli Shape. Si noti che i componenti sono identificati dal relativo indice nell'elenco dei componenti dell'utente (0 e 1 in questo esempio).

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

Le funzioni wrapper sono disponibili nel modulo Unity per semplificare la creazione di definizioni di forme personalizzate. L'elenco completo dei vincoli relativi a componenti e forme si trova in "SpatialUnderstandingDll.cs" all'interno delle strutture "ShapeComponentConstraint" e "ShapeConstraint".

![forma rettangolo presente in questa area](images/su-shapequery-300px.jpg)<br>
*Forma rettangolo individuata in questa superficie*

### <a name="object-placement-solver"></a>Risolutore posizionamento oggetti

Il Risolutore posizionamento oggetti può essere usato per identificare le posizioni ideali nella stanza fisica per inserire gli oggetti. Il Risolutore troverà il percorso più adatto in base alle regole e ai vincoli dell'oggetto. Inoltre, le query di oggetto vengono mantenute fino a quando l'oggetto non viene rimosso con chiamate a "Solver_RemoveObject" o "Solver_RemoveAllObjects", consentendo il posizionamento di più oggetti vincolato. Le query di posizionamento degli oggetti sono costituite da tre parti: tipo di posizionamento con parametri, un elenco di regole e un elenco di vincoli. Per eseguire una query, usare l'API seguente.

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

Questa funzione accetta un nome di oggetto, una definizione di selezione host e un elenco di regole e vincoli. I C# wrapper forniscono funzioni di supporto per la costruzione per semplificare la costruzione di regole e vincoli. La definizione di selezione host contiene il tipo di query, ovvero uno dei seguenti.

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

Ognuno dei tipi di posizionamento dispone di un set di parametri univoco per il tipo. La struttura "ObjectPlacementDefinition" contiene un set di funzioni di supporto statiche per la creazione di queste definizioni. Ad esempio, per trovare una posizione in cui posizionare un oggetto, è possibile usare la funzione seguente. public static ObjectPlacementDefinition Create_OnFloor (Vector3 halfDims) oltre al tipo di posizionamento, è possibile fornire un set di regole e vincoli. Impossibile violare le regole. Le posizioni di posizionamento possibili che soddisfano il tipo e le regole vengono quindi ottimizzate rispetto al set di vincoli per selezionare la posizione ottimale per la selezione host. Ognuna delle regole e dei vincoli può essere creata dalle funzioni di creazione statiche fornite. Di seguito è riportata una funzione di costruzione di regole e vincoli di esempio.

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

La query di posizionamento degli oggetti seguente sta cercando una posizione per inserire un cubo a metà metro sul bordo di una superficie, lontano dagli altri oggetti posizionati in precedenza e vicino al centro della stanza.

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

In caso di esito positivo, viene restituita una struttura "ObjectPlacementResult" che contiene la posizione, le dimensioni e l'orientamento del posizionamento. Inoltre, la selezione host viene aggiunta all'elenco interno della dll degli oggetti inseriti. Questo oggetto verrà preso in considerazione dalle query di posizionamento successive. Il file "LevelSolver.cs" nell'esempio Unity contiene altre query di esempio.

![risultati del posizionamento degli oggetti](images/su-objectplacement-1000px.jpg)<br>
*Figura 3: le caselle blu come il risultato di tre posizioni nelle query sul pavimento con le regole di posizione della fotocamera*

Quando si risolve la posizione di selezione host di più oggetti richiesti per uno scenario di livello o di applicazione, risolvere prima di tutto gli oggetti indispensabili e di grandi dimensioni per ottimizzare la probabilità che uno spazio venga trovato. L'ordine di posizionamento è importante. Se non è possibile trovare le posizioni degli oggetti, provare a eseguire meno configurazioni vincolate. Avere un set di configurazioni di fallback è fondamentale per supportare le funzionalità in molte configurazioni di chat room.

### <a name="room-scanning-process"></a>Processo di analisi chat room

Sebbene la soluzione di mapping spaziale fornita da HoloLens sia progettata per essere sufficientemente generica per soddisfare le esigenze dell'intera gamma di spazi di problemi, il modulo di comprensione spaziale è stato creato per supportare le esigenze di due giochi specifici. La soluzione è strutturata in base a un processo e a un set di presupposti specifici, riepilogati di seguito.

```
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process – 
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace. 
    Query functions will not function until after the scan has been finalized.
```

"Disegno" di playspace basato sull'utente: durante la fase di analisi, l'utente si sposta ed esamina la velocità di riproduzione, disegnando in modo efficace le aree che devono essere incluse. La mesh generata è importante per fornire commenti e suggerimenti degli utenti durante questa fase. Installazione domestica o di Office: le funzioni di query sono progettate per le superfici piane e i muri con angoli corretti. Si tratta di una limitazione flessibile. Tuttavia, durante la fase di analisi, viene completata un'analisi dell'asse primaria per ottimizzare lo schema a mosaico mesh lungo l'asse principale e secondario. Il file SpatialUnderstanding.cs incluso gestisce il processo della fase di analisi. Chiama le funzioni seguenti.

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

Il flusso di analisi, determinato dal comportamento "SpatialUnderstanding", chiama InitScan e quindi UpdateScan ogni frame. Quando la query Statistics segnala una ragionevole copertura, l'utente è autorizzato a AirTap per chiamare RequestFinish per indicare la fine della fase di analisi. UpdateScan continua a essere chiamato fino a quando non viene restituito il valore indica che l'elaborazione della dll è stata completata.

### <a name="understanding-mesh"></a>Informazioni su mesh

La dll informazioni archivia internamente il playspace come griglia di cubi voxel di dimensioni 8 cm. Durante la fase iniziale di analisi, viene completata un'analisi del componente principale per determinare gli assi della stanza. Internamente, archivia lo spazio voxel allineato a questi assi. Una mesh viene generata approssimativamente ogni secondo estraendo oggetto isosurface dal volume voxel. 

![mesh generata dal volume voxel](images/su-custommesh.jpg)<br>
*Mesh generata prodotta dal volume voxel*

## <a name="troubleshooting"></a>Risoluzione dei problemi
* Assicurarsi di aver impostato la funzionalità [SpatialPerception](#setting-the-spatialperception-capability)
* Quando il rilevamento viene perso, l'evento OnSurfaceChanged successivo rimuoverà tutte le mesh.

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a>Mapping spaziale nel Toolkit per realtà mista
Per altre informazioni sull'uso del mapping spaziale con Mixed Reality toolkit V2, vedere la <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">sezione relativa alla conoscenza spaziale</a> della documentazione di MRTK.

## <a name="see-also"></a>Vedi anche
* [MR Spatial 230: mapping spaziale](holograms-230.md)
* [Sistemi di coordinate](coordinate-systems.md)
* [Sistemi di coordinate in Unity](coordinate-systems-in-unity.md)
* <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a>
* <a href="https://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine. MeshFilter</a>
* <a href="https://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine. MeshCollider</a>
* <a href="https://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine. Bounds</a>

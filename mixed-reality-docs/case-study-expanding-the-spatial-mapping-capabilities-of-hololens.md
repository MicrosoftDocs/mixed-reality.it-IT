---
title: 'Case Study: espansione delle funzionalità di mapping spaziale di HoloLens'
description: Quando si creano le prime app per Microsoft HoloLens, siamo ansiosi di vedere come è possibile eseguire il push dei limiti del mapping spaziale sul dispositivo.
author: jevertt
ms.author: jevertt
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, HoloLens, mapping spaziale
ms.openlocfilehash: 602b629afa5900ff34c28b3a3a32725af06590b7
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522672"
---
# <a name="case-study---expanding-the-spatial-mapping-capabilities-of-hololens"></a>Case Study: espansione delle funzionalità di mapping spaziale di HoloLens

Quando si creano le prime app per Microsoft HoloLens, siamo ansiosi di vedere come è possibile eseguire il push dei limiti del mapping spaziale sul dispositivo. Jeff Evertt, un ingegnere del software presso Microsoft Studios, spiega come una nuova tecnologia è stata sviluppata dalla necessità di un maggiore controllo sulla modalità di inserimento degli ologrammi nell'ambiente reale di un utente.

## <a name="watch-the-video"></a>Guarda il video

>[!VIDEO https://www.youtube.com/embed/iUmTi3_Ynus]

## <a name="beyond-spatial-mapping"></a>Oltre il mapping spaziale

Mentre stavamo lavorando per i [frammenti](https://www.microsoft.com/p/fragments/9nblggh5ggm8) e i [Conker giovani](https://www.microsoft.com/p/young-conker/9nblggh5ggk1), due dei primi giochi per HoloLens, abbiamo scoperto che, quando avessimo eseguito il posizionamento procedurale degli ologrammi nel mondo fisico, abbiamo bisogno di un livello superiore di comprensione degli utenti ambiente. Ogni gioco ha esigenze specifiche di selezione host: Nei frammenti, ad esempio, si voleva essere in grado di distinguere tra superfici diverse, ad esempio il piano o una tabella, per inserire gli indizi nelle posizioni pertinenti. Volevamo anche essere in grado di identificare le superfici su cui potevano poggiare i caratteri olografici di dimensioni reali, ad esempio un divano o una poltrona. In Young Conker volevamo che Conker e i suoi avversari fossero in grado di usare le superfici sollevate nella stanza di un giocatore come piattaforme.

[Asobo Studios](http://www.asobostudio.com/index.html), il nostro partner di sviluppo per questi giochi, ha affrontato questo problema e ha creato una tecnologia che estende le funzionalità di mapping spaziale di HoloLens. In questo modo è possibile analizzare la stanza di un giocatore e identificare superfici quali muri, tabelle, poltrone e pavimenti. Inoltre, ci ha consentito di ottimizzare il rispetto di un set di vincoli per determinare la posizione migliore per gli oggetti olografici.

## <a name="the-spatial-understanding-code"></a>Codice di conoscenza spaziale

Abbiamo preso il codice originale di Asobo e abbiamo creato una libreria che incapsula questa tecnologia. Microsoft e Asobo hanno ora aperto questo codice e reso disponibile in [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) per poterlo usare nei propri progetti. Tutto il codice sorgente è incluso, consentendo di personalizzarlo in base alle proprie esigenze e condividere i miglioramenti con la community. Il codice per il C++ Risolutore è stato sottoposto a incapsulamento in una DLL di UWP ed esposto a Unity con una soluzione di [riepilogo a discesa contenuta in MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding).

Nell'esempio Unity sono disponibili numerose query utili che consentono di trovare spazi vuoti sulle pareti, posizionare oggetti sul soffitto o spazi di grandi dimensioni, identificare le posizioni dei caratteri e una miriade di altre query di comprensione spaziale.

Sebbene la soluzione di mapping spaziale fornita da HoloLens sia progettata per essere sufficientemente generica per soddisfare le esigenze dell'intera gamma di spazi di problemi, il modulo di comprensione spaziale è stato creato per supportare le esigenze di due giochi specifici. In questo modo, la soluzione è strutturata in base a un processo e a un set di presupposti specifici:
* **Playspace a dimensione fissa**: L'utente specifica le dimensioni massime di playspace nella chiamata init.
* **Processo di analisi**monouso: Il processo richiede una fase di analisi discreta in cui l'utente si aggira, definendo la playspace. Le funzioni di query non funzioneranno finché non sarà stata completata l'analisi.
* **"Disegno" di playspace basato sull'utente**: Durante la fase di analisi, l'utente sposta ed esamina la playspace, disegnando in modo efficace le aree che devono essere incluse. La mesh generata è importante per fornire commenti e suggerimenti degli utenti durante questa fase.
* **Installazione domestica o di Office**: Le funzioni di query sono progettate intorno ad aree piane e muri a angoli retti. Si tratta di una limitazione flessibile. Tuttavia, durante la fase di analisi, viene completata un'analisi dell'asse primaria per ottimizzare lo schema a mosaico mesh lungo l'asse principale e secondario.

### <a name="room-scanning-process"></a>Processo di analisi chat room

Quando si carica il modulo di conoscenza spaziale, la prima cosa da fare è analizzare lo spazio, in modo che tutte le superfici utilizzabili, ad esempio la pavimentazione, il soffitto e le pareti, siano identificate e con etichetta. Durante il processo di analisi, è possibile esaminare la stanza e "dipingere" le aree da includere nell'analisi.

La mesh rilevata durante questa fase è una parte importante del feedback visivo che consente agli utenti di sapere quali parti della stanza vengono analizzate. La DLL per il modulo di informazioni spaziali archivia internamente playspace come griglia di cubi voxel di dimensioni di 8 cm. Durante la fase iniziale di analisi, viene completata un'analisi del componente principale per determinare gli assi della stanza. Internamente, archivia lo spazio voxel allineato a questi assi. Una mesh viene generata approssimativamente ogni secondo estraendo oggetto isosurface dal volume voxel.

![Mapping spaziale mesh in bianco e informazioni su playspace mesh in verde](images/spatial-mapping-500px.png)

Mapping spaziale mesh in bianco e informazioni su playspace mesh in verde



Il file SpatialUnderstanding.cs incluso gestisce il processo della fase di analisi. Chiama le funzioni seguenti:
* **SpatialUnderstanding_Init**: Chiamato una volta all'inizio.
* **GeneratePlayspace_InitScan**: Indica che deve iniziare la fase di analisi.
* **GeneratePlayspace_UpdateScan_DynamicScan**: Chiamato ogni frame per aggiornare il processo di analisi. La posizione e l'orientamento della fotocamera vengono passati e usati per il processo di disegno playspace, descritto in precedenza.
* **GeneratePlayspace_RequestFinish**: Chiamato per finalizzare playspace. Questa operazione utilizzerà le aree "dipinte" durante la fase di analisi per definire e bloccare il playspace. L'applicazione può eseguire query sulle statistiche durante la fase di analisi, nonché eseguire query sulla mesh personalizzata per fornire commenti e suggerimenti degli utenti.
* **Import_UnderstandingMesh**: Durante l'analisi, il comportamento di **SpatialUnderstandingCustomMesh** fornito dal modulo e inserito nella prefabbricazione di comprensione eseguirà periodicamente una query sulla mesh personalizzata generata dal processo. Inoltre, questa operazione viene eseguita ancora una volta dopo la finalizzazione dell'analisi.

Il flusso di analisi, determinato dal comportamento **SpatialUnderstanding** , chiama **InitScan**e quindi **UpdateScan** ogni frame. Quando la query Statistics segnala una ragionevole copertura, l'utente può AirTap chiamare **RequestFinish** per indicare la fine della fase di analisi. **UpdateScan** continua a essere chiamato fino a quando non viene restituito il valore indica che l'elaborazione della dll è stata completata.

## <a name="the-queries"></a>Query

Una volta completata l'analisi, sarà possibile accedere a tre tipi diversi di query nell'interfaccia:
* **Query topologia**: Si tratta di query veloci basate sulla topologia della stanza sottoposta a scansione.
* **Query di forma**: Questi utilizzano i risultati delle query della topologia per trovare superfici orizzontali che corrispondono a forme personalizzate definite dall'utente.
* **Query posizionamento oggetti**: Si tratta di query più complesse che individuano la posizione più adatta in base a un set di regole e vincoli per l'oggetto.

Oltre alle tre query primarie, è disponibile un'interfaccia Raycasting che può essere usata per recuperare i tipi di superficie con tag e una mesh della stanza stermetica personalizzata che può essere copiata.

### <a name="topology-queries"></a>Query sulla topologia

All'interno della DLL, Gestione topologia gestisce l'assegnazione di etichette all'ambiente. Come indicato in precedenza, gran parte dei dati viene archiviata in surfels, che sono contenuti in un volume voxel. Inoltre, la struttura **PlaySpaceInfos** viene utilizzata per archiviare le informazioni relative a playspace, incluso l'allineamento internazionale (altri dettagli su questo sotto), il piano e l'altezza del soffitto.

Vengono usate le regole euristiche per determinare il piano, il soffitto e i muri. Ad esempio, la superficie orizzontale più grande e più bassa con una superficie di attacco maggiore di 1 m2 viene considerata il piano. Si noti che in questo processo viene usato anche il percorso della fotocamera durante il processo di analisi.

Un subset delle query esposte dal gestore della topologia viene esposto tramite la DLL. Le query di topologia esposte sono le seguenti:
* QueryTopology_FindPositionsOnWalls
* QueryTopology_FindLargePositionsOnWalls
* QueryTopology_FindLargestWall
* QueryTopology_FindPositionsOnFloor
* QueryTopology_FindLargestPositionsOnFloor
* QueryTopology_FindPositionsSittable

Ogni query ha un set di parametri, specifico del tipo di query. Nell'esempio seguente l'utente specifica l'altezza minima & larghezza del volume desiderato, l'altezza minima di posizionamento sopra il piano e la quantità minima di spazio di autorizzazione davanti al volume. Tutte le misurazioni sono in metri.




```
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
          _In_ float minHeightOfWallSpace,
          _In_ float minWidthOfWallSpace,
          _In_ float minHeightAboveFloor,
          _In_ float minFacingClearance,
          _In_ int locationCount,
          _Inout_ Dll_Interface::TopologyResult* locationData)
```

Ognuna di queste query accetta una matrice pre-allocata di strutture **TopologyResult** . Il parametro **locationCount** specifica la lunghezza della matrice passata. Il valore restituito indica il numero di posizioni restituite. Questo numero non è mai superiore al parametro **locationCount** passato.

Il **TopologyResult** contiene la posizione centrale del volume restituito, la direzione (ovvero normale) e le dimensioni dello spazio trovato.




```
struct TopologyResult
     {
          DirectX::XMFLOAT3 position;
          DirectX::XMFLOAT3 normal;
          float width;
          float length;
     };
```

Si noti che nell'esempio Unity ogni query è collegata a un pulsante nel pannello dell'interfaccia utente virtuale. L'esempio codifica in modo rigido i parametri per ognuna di queste query in valori ragionevoli. Per altri esempi, vedere *SpaceVisualizer.cs* nel codice di esempio.

### <a name="shape-queries"></a>Query di forma

All'interno della DLL, l'analizzatore di forme (**ShapeAnalyzer_W**) utilizza l'analizzatore della topologia per trovare la corrispondenza con le forme personalizzate definite dall'utente. Nell'esempio Unity è disponibile un set predefinito di forme, visualizzate nel menu query, nella scheda forma.

Si noti che l'analisi delle forme funziona solo su superfici orizzontali. Un divano, ad esempio, viene definito dalla superficie della postazione piatta e dalla parte superiore piatta del divano. La query Shape cerca due superfici di dimensioni, altezze e intervalli di aspetto specifici, con le due superfici allineate e connesse. Utilizzando la terminologia relativa alle API, la poltrona e la parte superiore della parte posteriore del divano sono componenti di forma e i requisiti di allineamento sono vincoli dei componenti di forma.

Una query di esempio definita nell'esempio Unity (**ShapeDefinition.cs**) per gli oggetti "SitTable" è la seguente:




```
shapeComponents = new List<ShapeComponent>()
     {
          new ShapeComponent(
               new List<ShapeComponentConstraint>()
               {
                    ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
                    ShapeComponentConstraint.Create_SurfaceCount_Min(1),
                    ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
               }),
     };
     AddShape("Sittable", shapeComponents);
```

Ogni query di forma è definita da un set di componenti di forma, ognuno con un set di vincoli di componente e un set di vincoli di forma che elenca le dipendenze tra i componenti. Questo esempio include tre vincoli in una definizione di componente singolo e nessun vincolo di forma tra i componenti (in quanto è presente un solo componente).

Al contrario, la forma Couch presenta due componenti di forma e quattro vincoli Shape. Si noti che i componenti sono identificati dal relativo indice nell'elenco dei componenti dell'utente (0 e 1 in questo esempio).




```
shapeConstraints = new List<ShapeConstraint>()
        {
              ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
              ShapeConstraint.Create_RectanglesParallel(0, 1),
              ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
              ShapeConstraint.Create_AtBackOf(1, 0),
        };
```

Le funzioni wrapper sono disponibili nel modulo Unity per semplificare la creazione di definizioni di forme personalizzate. L'elenco completo dei vincoli relativi ai componenti e alle forme è disponibile in **SpatialUnderstandingDll.cs** all'interno delle strutture **ShapeComponentConstraint** e **ShapeConstraint** .

![Il rettangolo blu evidenzia i risultati della query della forma Chair.](images/chair-shape-query-500px.png)

Il rettangolo blu evidenzia i risultati della query della forma Chair.



### <a name="object-placement-solver"></a>Risolutore posizionamento oggetti

È possibile usare le query di posizionamento degli oggetti per identificare le posizioni ideali nella stanza fisica per inserire gli oggetti. Il Risolutore troverà la posizione più adatta in base alle regole e ai vincoli dell'oggetto. Inoltre, le query di oggetto vengono mantenute fino a quando l'oggetto non viene rimosso con le chiamate a **Solver_RemoveObject** o **Solver_RemoveAllObjects** , consentendo il posizionamento multioggetto vincolato.

Le query di posizionamento degli oggetti sono costituite da tre parti: tipo di posizionamento con parametri, un elenco di regole e un elenco di vincoli. Per eseguire una query, usare l'API seguente:




```
public static int Solver_PlaceObject(
                [In] string objectName,
                [In] IntPtr placementDefinition,    // ObjectPlacementDefinition
                [In] int placementRuleCount,
                [In] IntPtr placementRules,         // ObjectPlacementRule
                [In] int constraintCount,
                [In] IntPtr placementConstraints,   // ObjectPlacementConstraint
                [Out] IntPtr placementResult)
```
Questa funzione accetta un nome di oggetto, una definizione di selezione host e un elenco di regole e vincoli. I C# wrapper forniscono funzioni di supporto per la costruzione per semplificare la costruzione di regole e vincoli. La definizione di selezione host contiene il tipo di query, ovvero uno dei seguenti:




```
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

Ognuno dei tipi di posizionamento dispone di un set di parametri univoco per il tipo. La struttura **ObjectPlacementDefinition** contiene un set di funzioni di supporto statiche per la creazione di queste definizioni. Ad esempio, per trovare una posizione in cui inserire un oggetto a terra, è possibile usare la funzione seguente: 


```
public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims)
```

Oltre al tipo di posizionamento, è possibile specificare un set di regole e vincoli. Impossibile violare le regole. Le posizioni di posizionamento possibili che soddisfano il tipo e le regole vengono quindi ottimizzate in base al set di vincoli per selezionare la posizione ottimale del posizionamento. Ognuna delle regole e dei vincoli può essere creata dalle funzioni di creazione statiche fornite. Di seguito è riportata una funzione di costruzione di regole e vincoli di esempio.




```
public static ObjectPlacementRule Create_AwayFromPosition(
                    Vector3 position, float minDistance)
               public static ObjectPlacementConstraint Create_NearPoint(
                    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

La query di posizionamento degli oggetti riportata di seguito sta cercando una posizione per inserire un cubo a metà metro sul bordo di una superficie, lontano dagli altri oggetti posizionati in precedenza e vicino al centro della stanza.




```
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

In caso di esito positivo, viene restituita una struttura **ObjectPlacementResult** contenente la posizione, le dimensioni e l'orientamento del posizionamento. Inoltre, la selezione host viene aggiunta all'elenco interno della DLL degli oggetti inseriti. Questo oggetto verrà preso in considerazione dalle query di posizionamento successive. Il file **LevelSolver.cs** nell'esempio Unity contiene altre query di esempio.

![Le caselle blu mostrano il risultato da tre posizioni nelle query del piano con le regole di "disattivazione della fotocamera".](images/away-from-camera-position-500px.png)

Le caselle blu mostrano il risultato da tre posizioni nelle query del piano con le regole di "disattivazione della fotocamera".


**Consigli**
* Quando si risolve la posizione di selezione host per più oggetti richiesti per uno scenario di livello o di applicazione, risolvere prima di tutto gli oggetti indispensabili e di grandi dimensioni per ottimizzare la probabilità che uno spazio possa essere trovato.
* L'ordine di posizionamento è importante. Se non è possibile trovare le posizioni degli oggetti, provare a eseguire meno configurazioni vincolate. Avere un set di configurazioni di fallback è fondamentale per supportare le funzionalità in molte configurazioni di chat room.

### <a name="ray-casting"></a>Casting Ray

Oltre alle tre query principali, è possibile usare un'interfaccia di cast di tipo Ray per recuperare i tipi di superficie con tag ed è possibile copiare una mesh playspace stermetica personalizzata quando la chat room è stata analizzata e finalizzata, le etichette vengono generate internamente per superfici come Floor, Ceiling e walls. La funzione **PlayspaceRaycast** accetta un raggio e restituisce se il raggio è in conflitto con una superficie nota e, in tal caso, le informazioni su tale superficie sotto forma di **RaycastResult**. 


```
struct RaycastResult
     {
          enum SurfaceTypes
          {
               Invalid, // No intersection
               Other,
               Floor,
               FloorLike,         // Not part of the floor topology, 
                                  //     but close to the floor and looks like the floor
               Platform,          // Horizontal platform between the ground and 
                                  //     the ceiling
               Ceiling,
               WallExternal,
               WallLike,          // Not part of the external wall surface, 
                                  //     but vertical surface that looks like a 
                                  //    wall structure
               };
               SurfaceTypes SurfaceType;
               float SurfaceArea;   // Zero if unknown 
                                        //  (i.e. if not part of the topology analysis)
               DirectX::XMFLOAT3 IntersectPoint;
               DirectX::XMFLOAT3 IntersectNormal;
     };
```

Internamente, il Raycast viene calcolato rispetto alla rappresentazione voxel del cubo di 8cm calcolata del playspace. Ogni voxel contiene un set di elementi Surface con dati della topologia elaborati (noti anche come surfels). Il surfels contenuto all'interno della cella voxel intersecata viene confrontato e la migliore corrispondenza utilizzata per cercare le informazioni sulla topologia. Questi dati della topologia contengono l'etichettatura restituita sotto forma di enumerazione **SurfaceTypes** , nonché la superficie di attacco della superficie intersecata.

Nell'esempio Unity il cursore esegue il cast di un raggio per ogni fotogramma. Per prima cosa, rispetto ai Collider di Unity; in secondo luogo, sulla rappresentazione mondiale del modulo di informazioni; e infine sugli elementi dell'interfaccia utente. In questa applicazione, l'interfaccia utente ottiene la priorità, quindi il risultato della comprensione e infine i Collider di Unity. **SurfaceType** viene segnalato come testo accanto al cursore.

![Intersezione di report dei risultati di Raycast con il piano.](images/raycast-result-500px.jpg)

Intersezione di report dei risultati di Raycast con il piano.


## <a name="get-the-code"></a>Ottenere il codice

Il codice open source è disponibile in [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity). Se si usa il codice in un progetto, segnalare i [forum per sviluppatori di HoloLens](https://forums.hololens.com/) . Non possiamo attendere per vedere cosa puoi fare!

## <a name="about-the-author"></a>Informazioni sull'autore

<table style="border:0;width:800px">
<tr>
<td style="border:0"> <img alt="Jeff Evertt, Software Engineering Lead at Microsoft" width="200" height="205" src="images/jeff-evertt-200px.jpg" /></td><td style="border:0"> <b>Jeff evertt</b> è un responsabile di ingegneria del software che ha lavorato a HoloLens dai primi giorni, dall'incubazione all'esperienza di sviluppo. Prima di HoloLens, ha collaborato con Xbox Kinect e nel settore dei giochi in un'ampia gamma di piattaforme e giochi. Jeff è appassionato di Robotica, grafica e cose con luci appariscenti. Si diverte ad apprendere nuove cose e a lavorare su software, hardware e in particolare nello spazio in cui si intersecano le due.</td>
</tr>
</table>



## <a name="see-also"></a>Vedere anche
* [Mapping spaziale](spatial-mapping.md)
* [Progettazione del mapping spaziale](spatial-mapping-design.md)
* [Visualizzazione della scansione dello spazio](room-scan-visualization.md)
* [MixedRealityToolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [Asobo Studio: Lezioni dal Frontline dello sviluppo di HoloLens](http://www.gamesindustry.biz/articles/2016-05-12-asobo-lessons-from-the-frontline-of-ar-development)

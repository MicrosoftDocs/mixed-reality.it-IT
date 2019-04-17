---
title: 'Case study: distribuire le funzionalità di mapping spaziale di HoloLens'
description: Quando si crea la prima App per Microsoft HoloLens, siamo felici di poter vedere solo fino a quando è stato possibile oltrepassare i limiti della mapping spaziale nel dispositivo.
author: jevertt
ms.author: jevertt
ms.date: 03/21/2018
ms.topic: article
keywords: Mapping spaziale di realtà mista di Windows, HoloLens,
ms.openlocfilehash: 602b629afa5900ff34c28b3a3a32725af06590b7
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602833"
---
# <a name="case-study---expanding-the-spatial-mapping-capabilities-of-hololens"></a>Case study: distribuire le funzionalità di mapping spaziale di HoloLens

Quando si crea la prima App per Microsoft HoloLens, siamo felici di poter vedere solo fino a quando è stato possibile oltrepassare i limiti della mapping spaziale nel dispositivo. Jeff Evertt, software engineer presso Microsoft Studios, descrive come una nuova tecnologia sviluppata dalla necessità di maggiore controllo sul modo in cui vntana viene inseriti in un ambiente dell'utente reale.

## <a name="watch-the-video"></a>Guarda il video

>[!VIDEO https://www.youtube.com/embed/iUmTi3_Ynus]

## <a name="beyond-spatial-mapping"></a>Oltre a mapping spaziale

Mentre stavamo lavorando [frammenti](https://www.microsoft.com/p/fragments/9nblggh5ggm8) e [Young Conker](https://www.microsoft.com/p/young-conker/9nblggh5ggk1), due dei giochi prima per HoloLens, abbiamo scoperto che se stessimo posizionamento procedura di vntana nel mondo fisico, è necessario un livello superiore comprensione sull'ambiente dell'utente. Ogni gioco ha esigenze la propria posizione specifica: In frammenti, ad esempio, volevamo essere in grado di distinguere tra diverse superfici, ad esempio una tabella o la parte intera, inserire indizi in località pertinenti. Desideravamo anche essere in grado di identificare le superfici che caratteri holographic dimensioni reali è stato possibile attendere in, ad esempio un divano o una sedia. In Conker Young, volevamo Conker e il suo avversari per poter usare superfici generate nella chat room del giocatore come piattaforme.

[Registrazione in Studio Asobo](http://www.asobostudio.com/index.html), il nostro partner di sviluppo per questi giochi, dovuto affrontare il problema; e creato una tecnologia che estende le funzionalità di mapping spaziale di HoloLens. In questo modo si sarebbe analizza stanza del giocatore e identificare aree, ad esempio pareti, le tabelle, anche di sedie e piani. Ha anche fornito a Microsoft la possibilità di ottimizzare rispetto a un set di vincoli per determinare il posizionamento ottimale per gli oggetti holographic.

## <a name="the-spatial-understanding-code"></a>Il codice di conoscenza spaziali

Abbiamo impiegato codice originale del Asobo e creato una libreria che incapsula questa tecnologia. Microsoft e Asobo abbiamo reso open-source questo codice e averlo reso disponibile nel [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) da usare nei propri progetti. Tutto il codice sorgente è incluso, consentendo di personalizzarlo in base alle esigenze e condividere i miglioramenti con la community. Il codice per il C++ Risolutore è stato eseguito il wrapping in una DLL UWP ed esposto a Unity con una [prefab vera e propria contenute MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding).

Ci sono molte query utili inclusa nell'esempio di Unity che è possibile trovare gli spazi vuoti delle pareti, posizionare gli oggetti al tetto massimo o in spazi di grandi dimensioni sul pavimento, identificare le aree per i caratteri per un periodo e una miriade di altre query spaziali comprensione.

Mentre la soluzione di mapping spaziale fornita da HoloLens è progettata per essere abbastanza generici per soddisfare le esigenze dell'intera gamma di aree di problemi, il modulo understanding spaziale è stato compilato per supportare le esigenze dei giochi specifiche due. Di conseguenza, la soluzione è strutturata su un processo specifico e un set dei presupposti:
* **Risolto dimensioni playspace**: L'utente specifica le dimensioni massime playspace nella chiamata di init.
* **Processo di analisi occasionale**: Il processo richiede una discreta analizzando fase in cui l'utente scorre attorno a, che definisce il playspace. Funzioni di query non saranno disponibili fino a dopo l'analisi è stata finalizzata.
* **Utente basato sui playspace "disegno"**: Durante la fase di analisi, l'utente si sposta e Cerca intorno playspace, disegno in modo efficace le aree che devono essere incluse. La trama generata è importante fornire commenti e suggerimenti utente durante questa fase.
* **In ambienti chiusi installazione domestica o aziendale**: Le funzioni di query sono progettate attorno superfici flat e walls ad angolo retto. Si tratta di una limitazione temporanea. Tuttavia, durante la fase di analisi, un'asse primario viene completata l'analisi per ottimizzare la suddivisione a mosaico di mesh lungo l'asse principale e secondaria.

### <a name="room-scanning-process"></a>Processo di analisi chat room

Quando si carica il modulo spaziali comprensione, la prima cosa è necessario è analizzare lo spazio, in modo che tutte le superfici utilizzabile, ad esempio walls, floor e ceiling, ovvero vengono identificati e con etichetta. Durante il processo di analisi Guardatevi intorno la chat e "paint' le aree che devono essere incluse nell'analisi.

Il reticolato visualizzato durante questa fase è un componente essenziale della risposta visiva che consente agli utenti di sapere quali parti della chat room vengono sottoposti a scansione. La DLL per il modulo di conoscenza spaziali archivia internamente il playspace come una griglia dei cubi voxel 8cm ridimensionato. Durante la parte iniziale di analisi, per determinare gli assi della chat room viene completata un'analisi in componenti principali. Archivia internamente, il relativo spazio voxel allineato a questi assi. Una rete mesh viene generata circa ogni secondo, estraendo l'oggetto isosurface dal volume voxel.

![Mapping di rete mesh in bianco e le informazioni playspace spaziali mesh in verde](images/spatial-mapping-500px.png)

Mapping di rete mesh in bianco e le informazioni playspace spaziali mesh in verde



Il file SpatialUnderstanding.cs incluso gestisce il processo di fase di analisi. Chiama le funzioni seguenti:
* **SpatialUnderstanding_Init**: Chiamato una volta all'inizio.
* **GeneratePlayspace_InitScan**: Indica che deve iniziare la fase di analisi.
* **GeneratePlayspace_UpdateScan_DynamicScan**: Chiamata a ogni fotogramma per aggiornare il processo di analisi. La posizione della fotocamera e l'orientamento viene passata e viene usato per il processo di disegno playspace, descritto in precedenza.
* **GeneratePlayspace_RequestFinish**: Chiamato per finalizzare il playspace. Le aree in cui "disegnate" durante la fase di analisi verranno utilizzate per definire e bloccare il playspace. L'applicazione può eseguire una query delle statistiche durante la scansione fase nonché query della rete personalizzata per inviare commenti e suggerimenti utente.
* **Import_UnderstandingMesh**: Durante l'analisi, il **SpatialUnderstandingCustomMesh** comportamento fornito dal modulo e inserito nel prefab understanding periodicamente eseguirà una query mesh personalizzate generate dal processo. Inoltre, questa operazione viene eseguita ancora una volta dopo l'analisi è stato finalizzato.

Il flusso di analisi, dovuto la **SpatialUnderstanding** chiama comportamento **InitScan**, quindi **UpdateScan** ogni fotogramma. Durante la query statistiche report code coverage ragionevole, l'utente può chiamare airtap **RequestFinish** per indicare la fine della fase di analisi. **UpdateScan** continua a essere chiamato finché non viene restituito il valore indica che la DLL è stata completata l'elaborazione.

## <a name="the-queries"></a>Le query

Una volta completata l'analisi, sarà in grado di accedere a tre diversi tipi di query nell'interfaccia:
* **Le query di topologia**: Si tratta di query rapide basati sulla topologia della chat room sottoposta ad analisi.
* **Forma query**: Si utilizzano i risultati delle query di topologia per trovare le superfici orizzontali che sono una corrispondenza soddisfacente a forme personalizzate definite.
* **Selezione host per le query di oggetto**: Si tratta di query più complesse che trovare il percorso di fallback basato su un set di regole e i vincoli per l'oggetto.

Oltre a tre query primaria, è disponibile un'interfaccia raycasting che può essere usata per recuperare i tipi di area con tag e una rete mesh di chat room stagni personalizzati possono essere copiate.

### <a name="topology-queries"></a>Query di topologia

All'interno della DLL, gestione della topologia gestisce l'assegnazione di etichette dell'ambiente. Come indicato in precedenza, gran parte dei dati verrà archiviata all'interno di surfels, che sono contenuti all'interno di un volume voxel. Inoltre, il **PlaySpaceInfos** struttura viene utilizzata per archiviare le informazioni sugli playspace, tra cui l'allineamento world (ulteriori dettagli su questo argomento di seguito), floor e ceiling altezza.

Vengono usate le euristiche per determinare walls, floor e ceiling. Ad esempio, la superficie più grande e più basso orizzontale con maggiore di 1 m2 superficie di attacco è considerata il tetto minimo. Si noti che il percorso della fotocamera durante il processo di analisi viene usato anche in questo processo.

Un subset delle query esposte da Gestione della topologia sono esposte tramite la DLL. Le query esposte topologia sono come segue:
* QueryTopology_FindPositionsOnWalls
* QueryTopology_FindLargePositionsOnWalls
* QueryTopology_FindLargestWall
* QueryTopology_FindPositionsOnFloor
* QueryTopology_FindLargestPositionsOnFloor
* QueryTopology_FindPositionsSittable

Ogni query dispone di un set di parametri, specifici per il tipo di query. Nell'esempio seguente, l'utente specifica l'altezza minima & larghezza del volume desiderato, altezza minima posizione di sopra la parte intera e la quantità minima di nulla osta davanti il volume. Tutte le misure sono in metri.




```
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
          _In_ float minHeightOfWallSpace,
          _In_ float minWidthOfWallSpace,
          _In_ float minHeightAboveFloor,
          _In_ float minFacingClearance,
          _In_ int locationCount,
          _Inout_ Dll_Interface::TopologyResult* locationData)
```

Ognuna di queste query accetta una matrice di pre-allocata **TopologyResult** strutture. Il **locationCount** parametro specifica la lunghezza della matrice passata. Il valore restituito indica il numero di percorsi restituiti. Questo numero non è mai maggiore passato **locationCount** parametro.

Il **TopologyResult** contiene la posizione centrale del volume restituito, la direzione pubblico (ad esempio normale) e le dimensioni dello spazio trovato.




```
struct TopologyResult
     {
          DirectX::XMFLOAT3 position;
          DirectX::XMFLOAT3 normal;
          float width;
          float length;
     };
```

Si noti che nell'esempio di Unity, ognuna di queste query è collegato a un pulsante nel pannello dell'interfaccia utente virtuale. L'esempio rigido codici i parametri per ognuna di queste query valori ragionevoli. Visualizzare *SpaceVisualizer.cs* nel codice di esempio per altri esempi.

### <a name="shape-queries"></a>Query di forma

All'interno della DLL, l'analizzatore di forma (**ShapeAnalyzer_W**) usa l'analizzatore di topologia da confrontare con le forme personalizzate definite dall'utente. L'esempio di Unity è un set predefinito di forme che vengono visualizzati nel menu query, nella scheda della forma.

Si noti che l'analisi della forma funziona su superfici orizzontale solo. Un divano, ad esempio, è definito per l'area di postazione flat e flat cima divano nuovamente. La query shape è simile per due aree di un determinato intervallo di dimensioni, altezza e aspetto, con due aree delle allineato e connesse. Utilizzando la terminologia di API, la postazione divano e la parte superiore alla parte posteriore del divano sono forme componenti e l'allineamento requisiti sono limitazioni dei componenti di forma.

Un esempio di query definita nell'esempio di Unity (**ShapeDefinition.cs**), per gli oggetti "sittable" è il seguente:




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

Ogni query shape è definita da un set di componenti di forma, ognuno con un set di limitazioni dei componenti e un set di vincoli di forma che elenca le dipendenze tra i componenti. Questo esempio include tre vincoli in una definizione di singoli componenti e senza vincoli di forme tra i componenti (perché è presente un solo componente).

Al contrario, la forma divano presenta due componenti di forma e quattro i vincoli di forma. Si noti che i componenti vengono identificati tramite il relativo indice nell'elenco dei componenti dell'utente (0 e 1 in questo esempio).




```
shapeConstraints = new List<ShapeConstraint>()
        {
              ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
              ShapeConstraint.Create_RectanglesParallel(0, 1),
              ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
              ShapeConstraint.Create_AtBackOf(1, 0),
        };
```

Le funzioni wrapper vengono fornite nel modulo di Unity per la creazione di definizioni di forma personalizzata. L'elenco completo dei vincoli di componente e la forma è reperibile nel **SpatialUnderstandingDll.cs** all'interno di **ShapeComponentConstraint** e il **ShapeConstraint** strutture.

![Il rettangolo blu evidenzia i risultati della query shape chair.](images/chair-shape-query-500px.png)

Il rettangolo blu evidenzia i risultati della query shape chair.



### <a name="object-placement-solver"></a>Risolutore di selezione host per oggetto

Query di selezione host per oggetto è utilizzabile per identificare le posizioni ideale nella chat room fisica per posizionare gli oggetti. Il Risolutore verrà indicata la posizione con mapping più appropriata data le regole di oggetti e i vincoli. Inoltre, le query di oggetto salvare in modo permanente fino a quando non viene rimosso l'oggetto con **Solver_RemoveObject** oppure **Solver_RemoveAllObjects** chiamate, consentendo vincolata selezione host per oggetti multipli.

Query di selezione host di oggetto sono costituiti da tre parti: il tipo con parametri, un elenco di regole e un elenco di vincoli di posizionamento. Per eseguire una query, usare l'API seguente:




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
Questa funzione accetta un nome di oggetto, definizione di selezione host e un elenco delle regole e dei vincoli. Il C# wrapper forniscono costruzione funzioni helper per facilitare la costruzione di regole e dei vincoli. La definizione di selezione host contiene il tipo di query, vale a dire, uno dei seguenti:




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

Ognuno dei tipi di selezione host dispone di un set di parametri univoci per il tipo. Il **ObjectPlacementDefinition** struttura contiene un set di funzioni di supporto statici per la creazione di queste definizioni. Per trovare una posizione in cui inserire un oggetto nell'ambiente operativo, ad esempio, è possibile usare la funzione seguente: 


```
public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims)
```

Oltre al tipo di selezione host, è possibile fornire un set di regole e i vincoli. Regole non possono essere violate. Percorsi selezione host per possibili che soddisfano il tipo e le regole sono quindi ottimizzati a fronte del set di vincoli per selezionare il percorso di posizionamento ottimale. Ognuna delle regole e i vincoli può essere creata da funzioni di creazione statici specificato. Una funzione di costruzione regole e dei vincoli di esempio è disponibili sotto.




```
public static ObjectPlacementRule Create_AwayFromPosition(
                    Vector3 position, float minDistance)
               public static ObjectPlacementConstraint Create_NearPoint(
                    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

La query di selezione host di oggetto seguente è alla ricerca di una posizione in cui inserire un misuratore metà cubo sul bordo di una superficie, da altra in precedenza posizionare gli oggetti e vicino al centro della chat room.




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

Se ha esito positivo, un **ObjectPlacementResult** struttura che contiene la posizione originale, dimensioni e orientamento viene restituita. Inoltre, la selezione host viene aggiunto all'elenco interno della DLL di oggetti inseriti. Le query di selezione successiva dovrà tener conto di questo oggetto. Il **LevelSolver.cs** file dell'esempio di Unity contiene più query di esempio.

![Le caselle blu mostrano il risultato da tre query unica posizione nel piano con le regole "distanza dalla posizione della fotocamera".](images/away-from-camera-position-500px.png)

Le caselle blu mostrano il risultato da tre query unica posizione nel piano con le regole "distanza dalla posizione della fotocamera".


**Suggerimenti:**
* Durante la risoluzione per il percorso di posizionamento di più oggetti necessari per uno scenario di applicazione o a un livello, risolvere innanzitutto oggetti grandi e indispensabili per ottimizzare la probabilità che può essere trovato uno spazio.
* Ordine di inserimento è importante. Se selezioni host per oggetti non viene trovato, provare a configurazioni meno vincolate. Un set di configurazioni di fallback è fondamentale per la funzionalità di supporto in molte configurazioni di chat room.

### <a name="ray-casting"></a>Raggio cast

Oltre ai tre query primaria, un'interfaccia di eseguire il cast di ray è utilizzabile per recuperare i tipi di area con tag e una rete mesh playspace stagni personalizzati possono essere copiate out dopo la chat è stata analizzata e finalizzata, le etichette vengono generate internamente, ad esempio le superfici di floor, ceiling e walls. Il **PlayspaceRaycast** funzione accetta un raggio e restituisce se il raggio è in conflitto con una superficie nota e in questo caso, informazioni che verranno visualizzati sotto forma di un **RaycastResult**. 


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

Internamente, viene calcolato il raycast contro la rappresentazione di voxel calcolata cm 8 al cubo del playspace. Ogni voxel contiene un set di elementi della superficie con i dati elaborati topologia (noto anche come surfels). Vengono confrontate le surfels contenute all'interno delle celle intersecate voxel e la migliore corrispondenza utilizzata per cercare le informazioni sulla topologia. Data questa topologia contiene l'assegnazione di etichette restituiti sotto forma del **SurfaceTypes** enum, nonché la superficie dell'area di intersezione.

Nell'esempio di Unity, il cursore viene eseguito il cast un raggio ogni fotogramma. Prima di tutto rispetto colliders di Unity; in secondo luogo, sulla rappresentazione mondo del modulo understanding; e infine, gli elementi dell'interfaccia utente. In questa applicazione, dell'interfaccia utente ottiene priorità, quindi il risultato di comprensione e infine colliders di Unity. Il **SurfaceType** viene segnalato come testo accanto al cursore.

![Risultato Raycast reporting intersezione con la parte intera.](images/raycast-result-500px.jpg)

Risultato Raycast reporting intersezione con la parte intera.


## <a name="get-the-code"></a>Ottieni il codice

Il codice open source è disponibile nel [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity). Commenti nel [forum dedicati allo sviluppo di HoloLens](https://forums.hololens.com/) se si usa il codice in un progetto. Siamo curiosi di vedere cosa fare con esso.

## <a name="about-the-author"></a>Informazioni sull'autore

<table style="border:0;width:800px">
<tr>
<td style="border:0"> <img alt="Jeff Evertt, Software Engineering Lead at Microsoft" width="200" height="205" src="images/jeff-evertt-200px.jpg" /></td><td style="border:0"> <b>Jeff Evertt</b> è un lead di ingegneria del software che ha lavorato su HoloLens sin dai tempi, dalla incubation per attività di sviluppo. Prima di HoloLens, ha lavorato su Kinect il Xbox e nel settore dei giochi su una vasta gamma di piattaforme e giochi. Jeff è passione per la robotica, grafica e cose con luci vistoso che vanno segnale acustico. Ama imparare cose nuove e l'utilizzo del software, hardware e in particolare nello spazio in cui si intersecano le due.</td>
</tr>
</table>



## <a name="see-also"></a>Vedere anche
* [Mapping spaziale](spatial-mapping.md)
* [Progettazione di mapping spaziale](spatial-mapping-design.md)
* [Visualizzazione analisi chat room](room-scan-visualization.md)
* [MixedRealityToolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [Asobo Studio: Lezioni dalla frontline dello sviluppo di HoloLens](http://www.gamesindustry.biz/articles/2016-05-12-asobo-lessons-from-the-frontline-of-ar-development)

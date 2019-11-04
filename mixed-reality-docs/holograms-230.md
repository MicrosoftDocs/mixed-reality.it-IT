---
title: MR Spatial 230-mapping spaziale
description: Seguire questa procedura dettagliata di codifica usando Unity, Visual Studio e HoloLens per informazioni dettagliate sui concetti relativi al mapping spaziale.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academy, esercitazione, mapping spaziale, superficie di ricostruzione, mesh
ms.openlocfilehash: cf4a2dd3e5eb74c0aaf849442e5f5e404d7cb661
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434576"
---
>[!NOTE]
>Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.  Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.  Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.  Verranno mantenuti per continuare a usare i dispositivi supportati. Per HoloLens 2 è stata pubblicata [una nuova serie di esercitazioni](mrlearning-base.md) .

<br>

# <a name="mr-spatial-230-spatial-mapping"></a>MR Spatial 230: mapping spaziale

Il [mapping spaziale](spatial-mapping.md) combina il mondo reale e il mondo virtuale insegnando gli ologrammi sull'ambiente. In MR Spatial 230 (Project Planetarium) si apprenderà come:

* Eseguire la scansione dell'ambiente e trasferire i dati dal HoloLens al computer di sviluppo.
* Esplora gli shader e Scopri come usarli per visualizzare lo spazio.
* Suddividere il mesh della stanza in semplici piani usando l'elaborazione mesh.
* Superare le tecniche di posizionamento apprese in [Mr nozioni di base 101](holograms-101.md)e fornire commenti e suggerimenti sulla posizione in cui un ologramma può essere posizionato nell'ambiente.
* Esplorare gli effetti di occlusione, pertanto quando l'ologramma è dietro un oggetto reale, è ancora possibile visualizzarlo con la visione x-ray.

>[!VIDEO https://www.youtube.com/embed/NSNYRkUX6Mw]

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td>MR Spatial 230: mapping spaziale</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>Prima di iniziare

### <a name="prerequisites"></a>Prerequisiti

* Un PC Windows 10 configurato con gli [strumenti corretti installati](install-the-tools.md).
* Alcune funzionalità C# di programmazione di base.
* Sono state completate le [nozioni di base 101](holograms-101.md).
* Un dispositivo HoloLens [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>File di progetto

* Scaricare i [file](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) richiesti dal progetto. Richiede Unity 2017,2 o versione successiva.
  * Se è ancora necessario il supporto per Unity 5,6, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip).
  * Se è ancora necessario il supporto per Unity 5,5, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip).
  * Se è ancora necessario il supporto per Unity 5,4, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip).
* Annullare l'archiviazione dei file sul desktop o in un'altra posizione facile da raggiungere.

>[!NOTE]
>Se si vuole esaminare il codice sorgente prima del download, è [disponibile in GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping).

### <a name="notes"></a>Note

* "Enable Just My Code" in Visual Studio deve essere disabilitato (*deselezionato*) in strumenti > Opzioni > il debug per raggiungere i punti di interruzione nel codice.

## <a name="unity-setup"></a>Configurazione di Unity

>[!VIDEO https://www.youtube.com/embed/y2Y4LhK6TEM]

* Avviare **Unity**.
* Selezionare **nuovo** per creare un nuovo progetto.
* Denominare il progetto **Planetarium**.
* Verificare che sia selezionata l'impostazione **3D** .
* Fai clic su **Create Project** (Crea progetto).
* Una volta avviato Unity, passare a **Edit > Project Settings > Player**.
* Nel pannello **Inspector** trovare e selezionare l'icona di **Windows Store** verde.
* Espandere **altre impostazioni**.
* Nella sezione **rendering** , controllare l'opzione **Virtual Reality supported** .
* Verificare che **Windows olografico** sia visualizzato nell'elenco degli **SDK di realtà virtuale**. In caso contrario, selezionare il pulsante **+** nella parte inferiore dell'elenco e scegliere **Windows olografico**.
* Espandere **impostazioni di pubblicazione**.
* Nella sezione **funzionalità** selezionare le impostazioni seguenti:
    * InternetClientServer
    * PrivateNetworkClientServer
    * Microfono
    * SpatialPerception
* Passare a **modifica > impostazioni progetto > qualità**
* Nel pannello **Inspector** , sotto l'icona di Windows Store, selezionare la freccia a discesa nera sotto la riga ' default ' e impostare l'impostazione predefinita su **molto bassa**.
* Passare a **asset > importa pacchetto > pacchetto personalizzato**.
* Passare alla cartella **. ..\holographicacademy-holograms-230-SpatialMapping\Starting** .
* Fare clic su **Planetarium. file unitypackage Tools**.
* Fai clic su **Apri**.
* Verrà visualizzata una finestra **Importa pacchetto Unity** , fare clic sul pulsante **Importa** .
* Attendere che Unity importi tutti gli asset necessari per completare il progetto.
* Nel pannello **gerarchia** eliminare la **fotocamera principale**.
* Nel pannello del **progetto** , **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** Folder, trovare l'oggetto **Main camera** .
* Trascinare e rilasciare il prefabbricato della **fotocamera principale** nel pannello **gerarchia** .
* Nel pannello **gerarchia** eliminare l'oggetto **direzionale Light** .
* Nel pannello **progetto** , nella cartella **ologrammi** individuare l'oggetto **cursore** .
* Trascinare & rilasciare il prefabbricato del **cursore** nella **gerarchia**.
* Nel pannello **gerarchia** selezionare l'oggetto **cursore** .
* Nel pannello di **controllo** fare clic sull'elenco a discesa **livello** e selezionare **modifica livelli...** .
* Nome **utente livello 31** come "**SpatialMapping**".
* Salva la nuova scena: **File > Salva scena con nome...**
* Fare clic su **nuova cartella** e denominare la cartella **Scenes**.
* Denominare il file "**Planetarium**" e salvarlo nella cartella **Scenes** .

## <a name="chapter-1---scanning"></a>Capitolo 1-analisi

>[!VIDEO https://www.youtube.com/embed/888oW51z_cE]

**Obiettivi**

* Informazioni su SurfaceObserver e sul modo in cui le impostazioni incidono sull'esperienza e sulle prestazioni.
* Consente di creare un'esperienza di analisi delle chat per raccogliere le maglie della stanza.

**Istruzioni**

* Nella cartella **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** del pannello del **progetto** individuare il prefabbricato **SpatialMapping** .
* Trascinare & rilasciare la prefabbricazione **SpatialMapping** nel pannello **gerarchia** .

**Compilazione e distribuzione (parte 1)**

* In Unity selezionare **File > impostazioni di compilazione**.
* Fare clic su **Aggiungi scene aperte** per aggiungere la scena **planetaria** alla compilazione.
* Selezionare **piattaforma UWP (Universal Windows Platform)** nell'elenco **piattaforma** e fare clic su **Cambia piattaforma**.
* Impostare **SDK** su **Universal 10** e **tipo di compilazione UWP** su **D3D**.
* Controllare **i C# progetti Unity**.
* Fai clic su **Compila**.
* Creare una **nuova cartella** denominata "app".
* Fare clic sulla cartella dell' **app** .
* Premere il pulsante **Seleziona cartella** .
* Al termine della compilazione di Unity, viene visualizzata una finestra Esplora file.
* Fare doppio clic sulla cartella dell' **app** per aprirla.
* Fare doppio clic su **Planetarium. sln** per caricare il progetto in Visual Studio.
* In Visual Studio utilizzare la barra degli strumenti superiore per modificare la configurazione in **Release**.
* Impostare la piattaforma su **x86**.
* Fare clic sulla freccia a discesa a destra di "computer locale" e selezionare **computer remoto**.
* Immettere l' [indirizzo IP del dispositivo](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) nel campo Address e modificare la modalità di autenticazione in **Universal (protocollo non crittografato)** .
* Fare clic su **debug-> avvia senza eseguire debug** o premere **CTRL + F5**.
* Guardare il pannello **output** in Visual Studio per lo stato di compilazione e distribuzione.
* Una volta distribuita l'app, esaminare la chat room. Vengono visualizzate le aree circostanti coperte da mesh wireframe nere e bianche.
* Analizza l'ambiente circostante. Assicurarsi di esaminare i muri, i soffitti e i piani.

**Compilazione e distribuzione (parte 2)**

Si analizzerà ora il modo in cui il mapping spaziale può influire sulle prestazioni.

* In Unity selezionare **finestra > Profiler**.
* Fare clic su **Aggiungi Profiler > GPU**.
* Fare clic su **Active Profiler > <Enter IP>** .
* Immettere l' **indirizzo IP** del HoloLens.
* Fai clic su **Connetti**.
* Osservare il numero di millisecondi impiegato dalla GPU per eseguire il rendering di un frame.
* Arrestare l'esecuzione dell'applicazione nel dispositivo.
* Tornare a Visual Studio e aprire **SpatialMappingObserver.cs**. Si troverà nella cartella HoloToolkit\SpatialMapping del progetto di assembly-CSharp (Windows universale).
* Trovare la funzione **sveglie ()** e aggiungere la riga di codice seguente: **TrianglesPerCubicMeter = 1200;**
* Ridistribuire il progetto nel dispositivo e quindi **riconnettere il profiler**. Osservare la modifica del numero di millisecondi per il rendering di un frame.
* Arrestare l'esecuzione dell'applicazione nel dispositivo.

**Salva e carica in Unity**

Infine, salvare il mesh della stanza e caricarlo in Unity.

* Tornare a Visual Studio e rimuovere la riga **TrianglesPerCubicMeter** aggiunta nella funzione **svegli ()** durante la sezione precedente.
* Ridistribuire il progetto nel dispositivo. A questo punto dovrebbe essere in esecuzione con **500** triangoli per ogni contatore cubo.
* Aprire un browser e immettere in HoloLens IPAddress per passare al portale del **dispositivo Windows**.
* Selezionare l'opzione **visualizzazione 3D** nel pannello di sinistra.
* In **ricostruzione superficie** selezionare il pulsante **Aggiorna** .
* Osservare come le aree analizzate in HoloLens vengono visualizzate nella finestra di visualizzazione.
* Per salvare l'analisi della chat room, fare clic sul pulsante **Salva** .
* Aprire la cartella **Downloads** per trovare il modello di chat room salvato **SRMesh. obj**.
* Copiare **SRMesh. obj** nella cartella **assets** del progetto Unity.
* In Unity selezionare l'oggetto **SpatialMapping** nel pannello **gerarchia** .
* Individuare il componente **Observer Surface Observer (script)** .
* Fare clic sul cerchio a destra della proprietà del **modello room** .
* Individuare e selezionare l'oggetto **SRMesh** e quindi chiudere la finestra.
* Verificare che la proprietà **modello room** nel pannello **Inspector** sia ora impostata su **SRMesh**.
* Premere il pulsante **Riproduci** per attivare la modalità di anteprima di Unity.
* Il componente SpatialMapping caricherà le mesh dal modello di chat room salvato per poterle usare in Unity.
* Passare alla visualizzazione **scena** per visualizzare tutto il modello di chat room visualizzato con wireframe shader.
* Premere di nuovo il pulsante **Riproduci** per uscire dalla modalità di anteprima.

**Nota:** Alla successiva immissione della modalità di anteprima in Unity, verrà caricata la mesh locale salvata per impostazione predefinita.

## <a name="chapter-2---visualization"></a>Capitolo 2-visualizzazione

>[!VIDEO https://www.youtube.com/embed/RnkvXl-aXD4]

**Obiettivi**

* Informazioni sulle nozioni di base degli shader.
* Visualizza l'ambiente circostante.

**Istruzioni**

* Nel pannello **gerarchia** di Unity selezionare l'oggetto **SpatialMapping** .
* Nel pannello **Inspector** trovare il componente **Spatial mapping Manager (script)** .
* Fare clic sul cerchio a destra della proprietà **superficie materiale** .
* Trovare e selezionare il materiale **BlueLinesOnWalls** e chiudere la finestra.
* Nella cartella **shader** Panel del **progetto** fare doppio clic su **BlueLinesOnWalls** per aprire lo shader in Visual Studio.
* Si tratta di un pixel semplice (Vertex to fragment), che consente di eseguire le attività seguenti:
    1. Converte la posizione di un vertice in uno spazio globale.
    2. Controlla la normale del vertice per determinare se un pixel è verticale.
    3. Imposta il colore del pixel per il rendering.

**Compilazione e distribuzione**

* Tornare a Unity e premere **Play** per passare alla modalità di anteprima.
* Il rendering delle linee blu verrà eseguito su tutte le superfici verticali della mesh della stanza, che viene caricata automaticamente dai dati di analisi salvati.
* Passare alla scheda **scena** per modificare la visualizzazione della chat room e vedere come viene visualizzata l'intera mesh room in Unity.
* Nel pannello **progetto** individuare la cartella **Materials** e selezionare il materiale **BlueLinesOnWalls** .
* Modificare alcune proprietà e vedere come vengono visualizzate le modifiche nell'editor di Unity.
    * Nel pannello **Inspector** modificare il valore **LineScale** in modo che le righe risultino più spesse o più sottili.
    * Nel pannello **Inspector** regolare il valore **LinesPerMeter** per modificare il numero di righe visualizzate in ogni parete.
* Fare di nuovo clic su **Riproduci** per uscire dalla modalità anteprima.
* Eseguire la compilazione e la distribuzione in HoloLens e osservare come viene visualizzato il rendering dello shader su superfici reali.

Unity è un ottimo lavoro di anteprima dei materiali, ma è sempre una buona idea estrarre il rendering nel dispositivo.

## <a name="chapter-3---processing"></a>Capitolo 3-elaborazione

>[!VIDEO https://www.youtube.com/embed/kaUKiNiDxwY]

**Obiettivi**

* Informazioni sulle tecniche per elaborare i dati di mapping spaziali da usare nell'applicazione.
* Analizzare i dati del mapping spaziale per individuare i piani e rimuovere i triangoli.
* Usare i piani per la posizione degli ologrammi.

**Istruzioni**

* Nel pannello del **progetto** di Unity, nella cartella **ologrammi** , trovare l'oggetto **SpatialProcessing** .
* Trascinare & rilasciare l'oggetto **SpatialProcessing** nel pannello **gerarchia** .

Il preprocessore SpatialProcessing include componenti per l'elaborazione dei dati di mapping spaziali. **SurfaceMeshesToPlanes.cs** troverà e genererà i piani in base ai dati di mapping spaziali. Microsoft utilizzerà i piani nell'applicazione per rappresentare i muri, i piani e i tetti. Questa prefabbricata include anche **RemoveSurfaceVertices.cs** che possono rimuovere i vertici dalla mesh di mapping spaziale. Questo può essere usato per creare buchi nella mesh o per rimuovere i triangoli superflui che non sono più necessari, perché è invece possibile usare i piani.

* Nel pannello del **progetto** di Unity, cartella **olografici** , trovare l'oggetto **Spacecollection** .
* Trascinare e rilasciare l'oggetto **spaziatore** nel pannello **gerarchia** .
* Nel pannello **gerarchia** selezionare l'oggetto **SpatialProcessing** .
* Nel pannello **Inspector** trovare il componente **Play Space Manager (script)** .
* Fare doppio clic su **PlaySpaceManager.cs** per aprirlo in Visual Studio.

PlaySpaceManager.cs contiene codice specifico dell'applicazione. Si aggiungeranno funzionalità a questo script per abilitare il comportamento seguente:

1. Interrompere la raccolta dei dati di mapping spaziali dopo il superamento del limite di tempo di analisi (10 secondi).
2. Elaborare i dati di mapping spaziale:
    1. Usare SurfaceMeshesToPlanes per creare una rappresentazione più semplice del mondo come piani (muri, piani, soffitti e così via).
    2. Usare RemoveSurfaceVertices per rimuovere i triangoli di superficie che rientrano nei limiti del piano.
3. Generare una raccolta di ologrammi in tutto il mondo e posizionarli sui piani di parete e di piano vicino all'utente.

Completare gli esercizi di codifica contrassegnati in PlaySpaceManager.cs o sostituire lo script con la soluzione completa riportata di seguito:

```cs
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;

/// <summary>
/// The SurfaceManager class allows applications to scan the environment for a specified amount of time 
/// and then process the Spatial Mapping Mesh (find planes, remove vertices) after that time has expired.
/// </summary>
public class PlaySpaceManager : Singleton<PlaySpaceManager>
{
    [Tooltip("When checked, the SurfaceObserver will stop running after a specified amount of time.")]
    public bool limitScanningByTime = true;

    [Tooltip("How much time (in seconds) that the SurfaceObserver will run after being started; used when 'Limit Scanning By Time' is checked.")]
    public float scanTime = 30.0f;

    [Tooltip("Material to use when rendering Spatial Mapping meshes while the observer is running.")]
    public Material defaultMaterial;

    [Tooltip("Optional Material to use when rendering Spatial Mapping meshes after the observer has been stopped.")]
    public Material secondaryMaterial;

    [Tooltip("Minimum number of floor planes required in order to exit scanning/processing mode.")]
    public uint minimumFloors = 1;

    [Tooltip("Minimum number of wall planes required in order to exit scanning/processing mode.")]
    public uint minimumWalls = 1;

    /// <summary>
    /// Indicates if processing of the surface meshes is complete.
    /// </summary>
    private bool meshesProcessed = false;

    /// <summary>
    /// GameObject initialization.
    /// </summary>
    private void Start()
    {
        // Update surfaceObserver and storedMeshes to use the same material during scanning.
        SpatialMappingManager.Instance.SetSurfaceMaterial(defaultMaterial);

        // Register for the MakePlanesComplete event.
        SurfaceMeshesToPlanes.Instance.MakePlanesComplete += SurfaceMeshesToPlanes_MakePlanesComplete;
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        // Check to see if the spatial mapping data has been processed
        // and if we are limiting how much time the user can spend scanning.
        if (!meshesProcessed && limitScanningByTime)
        {
            // If we have not processed the spatial mapping data
            // and scanning time is limited...

            // Check to see if enough scanning time has passed
            // since starting the observer.
            if (limitScanningByTime && ((Time.time - SpatialMappingManager.Instance.StartTime) < scanTime))
            {
                // If we have a limited scanning time, then we should wait until
                // enough time has passed before processing the mesh.
            }
            else
            {
                // The user should be done scanning their environment,
                // so start processing the spatial mapping data...

                /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

                // 3.a: Check if IsObserverRunning() is true on the
                // SpatialMappingManager.Instance.
                if(SpatialMappingManager.Instance.IsObserverRunning())
                {
                    // 3.a: If running, Stop the observer by calling
                    // StopObserver() on the SpatialMappingManager.Instance.
                    SpatialMappingManager.Instance.StopObserver();
                }

                // 3.a: Call CreatePlanes() to generate planes.
                CreatePlanes();

                // 3.a: Set meshesProcessed to true.
                meshesProcessed = true;
            }
        }
    }

    /// <summary>
    /// Handler for the SurfaceMeshesToPlanes MakePlanesComplete event.
    /// </summary>
    /// <param name="source">Source of the event.</param>
    /// <param name="args">Args for the event.</param>
    private void SurfaceMeshesToPlanes_MakePlanesComplete(object source, System.EventArgs args)
    {
        /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

        // Collection of floor and table planes that we can use to set horizontal items on.
        List<GameObject> horizontal = new List<GameObject>();

        // Collection of wall planes that we can use to set vertical items on.
        List<GameObject> vertical = new List<GameObject>();

        // 3.a: Get all floor and table planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'horizontal' list.
        horizontal = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Table | PlaneTypes.Floor);

        // 3.a: Get all wall planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'vertical' list.
        vertical = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Wall);

        // Check to see if we have enough horizontal planes (minimumFloors)
        // and vertical planes (minimumWalls), to set holograms on in the world.
        if (horizontal.Count >= minimumFloors && vertical.Count >= minimumWalls)
        {
            // We have enough floors and walls to place our holograms on...

            // 3.a: Let's reduce our triangle count by removing triangles
            // from SpatialMapping meshes that intersect with our active planes.
            // Call RemoveVertices().
            // Pass in all activePlanes found by SurfaceMeshesToPlanes.Instance.
            RemoveVertices(SurfaceMeshesToPlanes.Instance.ActivePlanes);

            // 3.a: We can indicate to the user that scanning is over by
            // changing the material applied to the Spatial Mapping meshes.
            // Call SpatialMappingManager.Instance.SetSurfaceMaterial().
            // Pass in the secondaryMaterial.
            SpatialMappingManager.Instance.SetSurfaceMaterial(secondaryMaterial);

            // 3.a: We are all done processing the mesh, so we can now
            // initialize a collection of Placeable holograms in the world
            // and use horizontal/vertical planes to set their starting positions.
            // Call SpaceCollectionManager.Instance.GenerateItemsInWorld().
            // Pass in the lists of horizontal and vertical planes that we found earlier.
            SpaceCollectionManager.Instance.GenerateItemsInWorld(horizontal, vertical);
        }
        else
        {
            // We do not have enough floors/walls to place our holograms on...

            // 3.a: Re-enter scanning mode so the user can find more surfaces by
            // calling StartObserver() on the SpatialMappingManager.Instance.
            SpatialMappingManager.Instance.StartObserver();

            // 3.a: Re-process spatial data after scanning completes by
            // re-setting meshesProcessed to false.
            meshesProcessed = false;
        }
    }

    /// <summary>
    /// Creates planes from the spatial mapping surfaces.
    /// </summary>
    private void CreatePlanes()
    {
        // Generate planes based on the spatial map.
        SurfaceMeshesToPlanes surfaceToPlanes = SurfaceMeshesToPlanes.Instance;
        if (surfaceToPlanes != null && surfaceToPlanes.enabled)
        {
            surfaceToPlanes.MakePlanes();
        }
    }

    /// <summary>
    /// Removes triangles from the spatial mapping surfaces.
    /// </summary>
    /// <param name="boundingObjects"></param>
    private void RemoveVertices(IEnumerable<GameObject> boundingObjects)
    {
        RemoveSurfaceVertices removeVerts = RemoveSurfaceVertices.Instance;
        if (removeVerts != null && removeVerts.enabled)
        {
            removeVerts.RemoveSurfaceVerticesWithinBounds(boundingObjects);
        }
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        if (SurfaceMeshesToPlanes.Instance != null)
        {
            SurfaceMeshesToPlanes.Instance.MakePlanesComplete -= SurfaceMeshesToPlanes_MakePlanesComplete;
        }
    }
}
```

**Compilazione e distribuzione**

* Prima di eseguire la distribuzione in HoloLens, premere il pulsante **Riproduci** in Unity per attivare la modalità di riproduzione.
* Dopo che la mesh Room è stata caricata dal file, attendere 10 secondi prima che l'elaborazione venga avviata sulla mesh di mapping spaziale.
* Al termine dell'elaborazione, i piani verranno visualizzati per rappresentare il piano, i muri, il soffitto e così via.
* Una volta trovati tutti i piani, viene visualizzato un sistema solare in una tabella di piano vicino alla fotocamera.
* Verranno visualizzati due poster anche accanto alla fotocamera. Passare alla scheda **scena** se non è possibile visualizzarli in modalità di **gioco** .
* Premere di nuovo il pulsante **Riproduci** per uscire dalla modalità di riproduzione.
* Compilare e distribuire in HoloLens, come di consueto.
* Attendere il completamento dell'analisi e dell'elaborazione dei dati di mapping spaziali.
* Dopo aver visualizzato i piani, provare a trovare il sistema solare e i poster nel mondo.

## <a name="chapter-4---placement"></a>Capitolo 4-selezione host

>[!VIDEO https://www.youtube.com/embed/Srhtpid1uZc]

**Obiettivi**

* Determinare se un ologramma si adatta a una superficie.
* Fornire commenti e suggerimenti all'utente quando un ologramma può o non può adattarsi a una superficie.

**Istruzioni**

* Nel pannello **gerarchia** di Unity selezionare l'oggetto **SpatialProcessing** .
* Nel pannello **Inspector** trovare il componente **Surface Meshs to Planes (script)** .
* Per cancellare la selezione, modificare la proprietà **piani di estrazione** in **Nessun** elemento.
* Modificare la proprietà dei **piani di disegna** su **Wall**, in modo che venga eseguito il rendering solo dei piani di muro.
* Nel pannello **progetto** , cartella **script** , fare doppio clic su **Placeable.cs** per aprirlo in Visual Studio.

Lo script **posizionabile** è già collegato ai manifesti e alla casella di proiezione creati al termine della ricerca del piano. È sufficiente rimuovere il commento dal codice e questo script consentirà di ottenere i risultati seguenti:

1. Determinare se un ologramma si adatta a una superficie Raycasting dal centro e da quattro angoli del cubo di delimitazione.
2. Controllare la normale della superficie per determinare se è sufficientemente uniforme per consentire l'ologramma in cui si trova lo scaricamento.
3. Eseguire il rendering di un cubo di delimitazione intorno all'ologramma per visualizzarne le dimensioni effettive durante la posizione.
4. Consente di eseguire il cast di un'ombreggiatura sotto/dietro l'ologramma per mostrare dove verrà posizionata sul pavimento o sul muro.
5. Eseguire il rendering dell'ombreggiatura in rosso, se l'ologramma non può essere inserito sulla superficie o verde, se possibile.
6. Riorientare l'ologramma per allinearlo al tipo di superficie (verticale o orizzontale) con affinità.
7. Posizionare in modo uniforme l'ologramma sulla superficie selezionata per evitare il comportamento di salto o blocco.

Rimuovere il commento dal codice nell'esercizio di codifica riportato di seguito oppure usare questa soluzione completata in **Placeable.cs**:

```cs
using System.Collections.Generic;
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Enumeration containing the surfaces on which a GameObject
/// can be placed.  For simplicity of this sample, only one
/// surface type is allowed to be selected.
/// </summary>
public enum PlacementSurfaces
{
    // Horizontal surface with an upward pointing normal.
    Horizontal = 1,

    // Vertical surface with a normal facing the user.
    Vertical = 2,
}

/// <summary>
/// The Placeable class implements the logic used to determine if a GameObject
/// can be placed on a target surface. Constraints for placement include:
/// * No part of the GameObject's box collider impacts with another object in the scene
/// * The object lays flat (within specified tolerances) against the surface
/// * The object would not fall off of the surface if gravity were enabled.
/// This class also provides the following visualizations.
/// * A transparent cube representing the object's box collider.
/// * Shadow on the target surface indicating whether or not placement is valid.
/// </summary>
public class Placeable : MonoBehaviour
{
    [Tooltip("The base material used to render the bounds asset when placement is allowed.")]
    public Material PlaceableBoundsMaterial = null;

    [Tooltip("The base material used to render the bounds asset when placement is not allowed.")]
    public Material NotPlaceableBoundsMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it allowed.")]
    public Material PlaceableShadowMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it not allowed.")]
    public Material NotPlaceableShadowMaterial = null;

    [Tooltip("The type of surface on which the object can be placed.")]
    public PlacementSurfaces PlacementSurface = PlacementSurfaces.Horizontal;

    [Tooltip("The child object(s) to hide during placement.")]
    public List<GameObject> ChildrenToHide = new List<GameObject>();

    /// <summary>
    /// Indicates if the object is in the process of being placed.
    /// </summary>
    public bool IsPlacing { get; private set; }

    // The most recent distance to the surface.  This is used to 
    // locate the object when the user's gaze does not intersect
    // with the Spatial Mapping mesh.
    private float lastDistance = 2.0f;

    // The distance away from the target surface that the object should hover prior while being placed.
    private float hoverDistance = 0.15f;

    // Threshold (the closer to 0, the stricter the standard) used to determine if a surface is flat.
    private float distanceThreshold = 0.02f;

    // Threshold (the closer to 1, the stricter the standard) used to determine if a surface is vertical.
    private float upNormalThreshold = 0.9f;

    // Maximum distance, from the object, that placement is allowed.
    // This is used when raycasting to see if the object is near a placeable surface.
    private float maximumPlacementDistance = 5.0f;

    // Speed (1.0 being fastest) at which the object settles to the surface upon placement.
    private float placementVelocity = 0.06f;

    // Indicates whether or not this script manages the object's box collider.
    private bool managingBoxCollider = false;

    // The box collider used to determine of the object will fit in the desired location.
    // It is also used to size the bounding cube.
    private BoxCollider boxCollider = null;

    // Visible asset used to show the dimensions of the object. This asset is sized
    // using the box collider's bounds.
    private GameObject boundsAsset = null;

    // Visible asset used to show the where the object is attempting to be placed.
    // This asset is sized using the box collider's bounds.
    private GameObject shadowAsset = null;

    // The location at which the object will be placed.
    private Vector3 targetPosition;

    /// <summary>
    /// Called when the GameObject is created.
    /// </summary>
    private void Awake()
    {
        targetPosition = gameObject.transform.position;

        // Get the object's collider.
        boxCollider = gameObject.GetComponent<BoxCollider>();
        if (boxCollider == null)
        {
            // The object does not have a collider, create one and remember that
            // we are managing it.
            managingBoxCollider = true;
            boxCollider = gameObject.AddComponent<BoxCollider>();
            boxCollider.enabled = false;
        }

        // Create the object that will be used to indicate the bounds of the GameObject.
        boundsAsset = GameObject.CreatePrimitive(PrimitiveType.Cube);
        boundsAsset.transform.parent = gameObject.transform;
        boundsAsset.SetActive(false);

        // Create a object that will be used as a shadow.
        shadowAsset = GameObject.CreatePrimitive(PrimitiveType.Quad);
        shadowAsset.transform.parent = gameObject.transform;
        shadowAsset.SetActive(false);
    }

    /// <summary>
    /// Called when our object is selected.  Generally called by
    /// a gesture management component.
    /// </summary>
    public void OnSelect()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (!IsPlacing)
        {
            OnPlacementStart();
        }
        else
        {
            OnPlacementStop();
        }
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (IsPlacing)
        {
            // Move the object.
            Move();

            // Set the visual elements.
            Vector3 targetPosition;
            Vector3 surfaceNormal;
            bool canBePlaced = ValidatePlacement(out targetPosition, out surfaceNormal);
            DisplayBounds(canBePlaced);
            DisplayShadow(targetPosition, surfaceNormal, canBePlaced);
        }
        else
        {
            // Disable the visual elements.
            boundsAsset.SetActive(false);
            shadowAsset.SetActive(false);

            // Gracefully place the object on the target surface.
            float dist = (gameObject.transform.position - targetPosition).magnitude;
            if (dist > 0)
            {
                gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, targetPosition, placementVelocity / dist);
            }
            else
            {
                // Unhide the child object(s) to make placement easier.
                for (int i = 0; i < ChildrenToHide.Count; i++)
                {
                    ChildrenToHide[i].SetActive(true);
                }
            }
        }
    }

    /// <summary>
    /// Verify whether or not the object can be placed.
    /// </summary>
    /// <param name="position">
    /// The target position on the surface.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the object is to be placed.
    /// </param>
    /// <returns>
    /// True if the target position is valid for placing the object, otherwise false.
    /// </returns>
    private bool ValidatePlacement(out Vector3 position, out Vector3 surfaceNormal)
    {
        Vector3 raycastDirection = gameObject.transform.forward;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            // Raycast from the bottom face of the box collider.
            raycastDirection = -(Vector3.up);
        }

        // Initialize out parameters.
        position = Vector3.zero;
        surfaceNormal = Vector3.zero;

        Vector3[] facePoints = GetColliderFacePoints();

        // The origin points we receive are in local space and we 
        // need to raycast in world space.
        for (int i = 0; i < facePoints.Length; i++)
        {
            facePoints[i] = gameObject.transform.TransformVector(facePoints[i]) + gameObject.transform.position;
        }

        // Cast a ray from the center of the box collider face to the surface.
        RaycastHit centerHit;
        if (!Physics.Raycast(facePoints[0],
                        raycastDirection,
                        out centerHit,
                        maximumPlacementDistance,
                        SpatialMappingManager.Instance.LayerMask))
        {
            // If the ray failed to hit the surface, we are done.
            return false;
        }

        // We have found a surface.  Set position and surfaceNormal.
        position = centerHit.point;
        surfaceNormal = centerHit.normal;

        // Cast a ray from the corners of the box collider face to the surface.
        for (int i = 1; i < facePoints.Length; i++)
        {
            RaycastHit hitInfo;
            if (Physics.Raycast(facePoints[i],
                                raycastDirection,
                                out hitInfo,
                                maximumPlacementDistance,
                                SpatialMappingManager.Instance.LayerMask))
            {
                // To be a valid placement location, each of the corners must have a similar
                // enough distance to the surface as the center point
                if (!IsEquivalentDistance(centerHit.distance, hitInfo.distance))
                {
                    return false;
                }
            }
            else
            {
                // The raycast failed to intersect with the target layer.
                return false;
            }
        }

        return true;
    }

    /// <summary>
    /// Determine the coordinates, in local space, of the box collider face that 
    /// will be placed against the target surface.
    /// </summary>
    /// <returns>
    /// Vector3 array with the center point of the face at index 0.
    /// </returns>
    private Vector3[] GetColliderFacePoints()
    {
        // Get the collider extents.  
        // The size values are twice the extents.
        Vector3 extents = boxCollider.size / 2;

        // Calculate the min and max values for each coordinate.
        float minX = boxCollider.center.x - extents.x;
        float maxX = boxCollider.center.x + extents.x;
        float minY = boxCollider.center.y - extents.y;
        float maxY = boxCollider.center.y + extents.y;
        float minZ = boxCollider.center.z - extents.z;
        float maxZ = boxCollider.center.z + extents.z;

        Vector3 center;
        Vector3 corner0;
        Vector3 corner1;
        Vector3 corner2;
        Vector3 corner3;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            center = new Vector3(boxCollider.center.x, minY, boxCollider.center.z);
            corner0 = new Vector3(minX, minY, minZ);
            corner1 = new Vector3(minX, minY, maxZ);
            corner2 = new Vector3(maxX, minY, minZ);
            corner3 = new Vector3(maxX, minY, maxZ);
        }
        else
        {
            // Placing on vertical surfaces.
            center = new Vector3(boxCollider.center.x, boxCollider.center.y, maxZ);
            corner0 = new Vector3(minX, minY, maxZ);
            corner1 = new Vector3(minX, maxY, maxZ);
            corner2 = new Vector3(maxX, minY, maxZ);
            corner3 = new Vector3(maxX, maxY, maxZ);
        }

        return new Vector3[] { center, corner0, corner1, corner2, corner3 };
    }

    /// <summary>
    /// Put the object into placement mode.
    /// </summary>
    public void OnPlacementStart()
    {
        // If we are managing the collider, enable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = true;
        }

        // Hide the child object(s) to make placement easier.
        for (int i = 0; i < ChildrenToHide.Count; i++)
        {
            ChildrenToHide[i].SetActive(false);
        }

        // Tell the gesture manager that it is to assume
        // all input is to be given to this object.
        GestureManager.Instance.OverrideFocusedObject = gameObject;

        // Enter placement mode.
        IsPlacing = true;
    }

    /// <summary>
    /// Take the object out of placement mode.
    /// </summary>
    /// <remarks>
    /// This method will leave the object in placement mode if called while
    /// the object is in an invalid location.  To determine whether or not
    /// the object has been placed, check the value of the IsPlacing property.
    /// </remarks>
    public void OnPlacementStop()
    {
        // ValidatePlacement requires a normal as an out parameter.
        Vector3 position;
        Vector3 surfaceNormal;

        // Check to see if we can exit placement mode.
        if (!ValidatePlacement(out position, out surfaceNormal))
        {
            return;
        }

        // The object is allowed to be placed.
        // We are placing at a small buffer away from the surface.
        targetPosition = position + (0.01f * surfaceNormal);

        OrientObject(true, surfaceNormal);

        // If we are managing the collider, disable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = false;
        }

        // Tell the gesture manager that it is to resume
        // its normal behavior.
        GestureManager.Instance.OverrideFocusedObject = null;

        // Exit placement mode.
        IsPlacing = false;
    }

    /// <summary>
    /// Positions the object along the surface toward which the user is gazing.
    /// </summary>
    /// <remarks>
    /// If the user's gaze does not intersect with a surface, the object
    /// will remain at the most recently calculated distance.
    /// </remarks>
    private void Move()
    {
        Vector3 moveTo = gameObject.transform.position;
        Vector3 surfaceNormal = Vector3.zero;
        RaycastHit hitInfo;

        bool hit = Physics.Raycast(Camera.main.transform.position,
                                Camera.main.transform.forward,
                                out hitInfo,
                                20f,
                                SpatialMappingManager.Instance.LayerMask);

        if (hit)
        {
            float offsetDistance = hoverDistance;

            // Place the object a small distance away from the surface while keeping 
            // the object from going behind the user.
            if (hitInfo.distance <= hoverDistance)
            {
                offsetDistance = 0f;
            }

            moveTo = hitInfo.point + (offsetDistance * hitInfo.normal);

            lastDistance = hitInfo.distance;
            surfaceNormal = hitInfo.normal;
        }
        else
        {
            // The raycast failed to hit a surface.  In this case, keep the object at the distance of the last
            // intersected surface.
            moveTo = Camera.main.transform.position + (Camera.main.transform.forward * lastDistance);
        }

        // Follow the user's gaze.
        float dist = Mathf.Abs((gameObject.transform.position - moveTo).magnitude);
        gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, moveTo, placementVelocity / dist);

        // Orient the object.
        // We are using the return value from Physics.Raycast to instruct
        // the OrientObject function to align to the vertical surface if appropriate.
        OrientObject(hit, surfaceNormal);
    }

    /// <summary>
    /// Orients the object so that it faces the user.
    /// </summary>
    /// <param name="alignToVerticalSurface">
    /// If true and the object is to be placed on a vertical surface, 
    /// orient parallel to the target surface.  If false, orient the object 
    /// to face the user.
    /// </param>
    /// <param name="surfaceNormal">
    /// The target surface's normal vector.
    /// </param>
    /// <remarks>
    /// The alignToVerticalSurface parameter is ignored if the object
    /// is to be placed on a horizontalSurface
    /// </remarks>
    private void OrientObject(bool alignToVerticalSurface, Vector3 surfaceNormal)
    {
        Quaternion rotation = Camera.main.transform.localRotation;

        // If the user's gaze does not intersect with the Spatial Mapping mesh,
        // orient the object towards the user.
        if (alignToVerticalSurface && (PlacementSurface == PlacementSurfaces.Vertical))
        {
            // We are placing on a vertical surface.
            // If the normal of the Spatial Mapping mesh indicates that the
            // surface is vertical, orient parallel to the surface.
            if (Mathf.Abs(surfaceNormal.y) <= (1 - upNormalThreshold))
            {
                rotation = Quaternion.LookRotation(-surfaceNormal, Vector3.up);
            }
        }
        else
        {
            rotation.x = 0f;
            rotation.z = 0f;
        }

        gameObject.transform.rotation = rotation;
    }

    /// <summary>
    /// Displays the bounds asset.
    /// </summary>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayBounds(bool canBePlaced)
    {
        // Ensure the bounds asset is sized and positioned correctly.
        boundsAsset.transform.localPosition = boxCollider.center;
        boundsAsset.transform.localScale = boxCollider.size;
        boundsAsset.transform.rotation = gameObject.transform.rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = PlaceableBoundsMaterial;
        }
        else
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableBoundsMaterial;
        }

        // Show the bounds asset.
        boundsAsset.SetActive(true);
    }

    /// <summary>
    /// Displays the placement shadow asset.
    /// </summary>
    /// <param name="position">
    /// The position at which to place the shadow asset.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the asset will be placed
    /// </param>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayShadow(Vector3 position,
                            Vector3 surfaceNormal,
                            bool canBePlaced)
    {
        // Rotate and scale the shadow so that it is displayed on the correct surface and matches the object.
        float rotationX = 0.0f;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            rotationX = 90.0f;
            shadowAsset.transform.localScale = new Vector3(boxCollider.size.x, boxCollider.size.z, 1);
        }
        else
        {
            shadowAsset.transform.localScale = boxCollider.size;
        }

        Quaternion rotation = Quaternion.Euler(rotationX, gameObject.transform.rotation.eulerAngles.y, 0);
        shadowAsset.transform.rotation = rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = PlaceableShadowMaterial;
        }
        else
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableShadowMaterial;
        }

        // Show the shadow asset as appropriate.
        if (position != Vector3.zero)
        {
            // Position the shadow a small distance from the target surface, along the normal.
            shadowAsset.transform.position = position + (0.01f * surfaceNormal);
            shadowAsset.SetActive(true);
        }
        else
        {
            shadowAsset.SetActive(false);
        }
    }

    /// <summary>
    /// Determines if two distance values should be considered equivalent. 
    /// </summary>
    /// <param name="d1">
    /// Distance to compare.
    /// </param>
    /// <param name="d2">
    /// Distance to compare.
    /// </param>
    /// <returns>
    /// True if the distances are within the desired tolerance, otherwise false.
    /// </returns>
    private bool IsEquivalentDistance(float d1, float d2)
    {
        float dist = Mathf.Abs(d1 - d2);
        return (dist <= distanceThreshold);
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        // Unload objects we have created.
        Destroy(boundsAsset);
        boundsAsset = null;
        Destroy(shadowAsset);
        shadowAsset = null;
    }
}
```

**Compilazione e distribuzione**

* Come in precedenza, compilare il progetto e distribuirlo in HoloLens.
* Attendere il completamento dell'analisi e dell'elaborazione dei dati di mapping spaziali.
* Quando viene visualizzato il sistema solare, osservare la casella di proiezione seguente ed eseguire un movimento di selezione per spostarlo. Mentre la casella di proiezione è selezionata, un cubo di delimitazione sarà visibile intorno alla casella di proiezione.
* Sposta la testa per ammirare una posizione diversa nella stanza. La finestra di proiezione dovrebbe seguire lo sguardo. Quando l'ombreggiatura sotto la casella di proiezione è rossa, non è possibile posizionare l'ologramma su tale superficie. Quando l'ombreggiatura sotto la casella di proiezione risulta verde, è possibile posizionare l'ologramma eseguendo un altro movimento di selezione.
* Trovare e selezionare uno dei poster olografici su un muro per spostarlo in una nuova posizione. Si noti che non è possibile posizionare il poster sul pavimento o sul soffitto e che rimane correttamente orientato a ogni muro mentre ci si sposta.

## <a name="chapter-5---occlusion"></a>Capitolo 5-occlusione

>[!VIDEO https://www.youtube.com/embed/6Xrzh_w-7SE]

**Obiettivi**

* Determinare se un ologramma è nascosto dalla mesh di mapping spaziale.
* Applicare diverse tecniche di occlusione per ottenere un effetto divertente.

**Istruzioni**

In primo luogo, si consentirà alla rete di mapping spaziale di occludere altri ologrammi senza occlusione il mondo reale:

* Nel pannello **gerarchia** selezionare l'oggetto **SpatialProcessing** .
* Nel pannello **Inspector** trovare il componente **Play Space Manager (script)** .
* Fare clic sul cerchio a destra della proprietà **Material secondaria** .
* Trovare e selezionare il materiale di **occlusione** e chiudere la finestra.

Successivamente, si aggiungerà un comportamento speciale a Earth, in modo che abbia un'evidenziazione blu ogni volta che diventa bloccato da un altro ologramma (ad esempio il sole) o dalla mesh di mapping spaziale:

* Nel pannello **progetto** , nella cartella **ologrammi** , espandere l'oggetto **Solarsystem** .
* Fare clic su **Earth**.
* Nel pannello **Inspector** trovare il materiale della terra (componente inferiore).
* Nell' **elenco a discesa shader**impostare lo shader su **Custom > OcclusionRim**. Verrà eseguito il rendering di un'evidenziazione blu attorno alla terra ogni volta che viene nascosto da un altro oggetto.

Infine, si Abilita un effetto di visione x-ray per i pianeti nel nostro sistema solare. È necessario modificare **PlanetOcclusion.cs** (presente nella cartella Scripts\SolarSystem) per ottenere i risultati seguenti:

1. Determinare se un pianeta è bloccato dal livello SpatialMapping (maglie e piani della stanza).
2. Mostra la rappresentazione wireframe di un pianeta ogni volta che viene bloccato dal livello SpatialMapping.
3. Nascondere la rappresentazione wireframe di un pianeta quando non è bloccata dal livello SpatialMapping.

Seguire l'esercizio di codifica in PlanetOcclusion.cs o usare la soluzione seguente:

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Determines when the occluded version of the planet should be visible.
/// This script allows us to do selective occlusion, so the occlusionObject
/// will only be rendered when a Spatial Mapping surface is occluding the planet,
/// not when another hologram is responsible for the occlusion.
/// </summary>
public class PlanetOcclusion : MonoBehaviour
{
    [Tooltip("Object to display when the planet is occluded.")]
    public GameObject occlusionObject;

    /// <summary>
    /// Points to raycast to when checking for occlusion.
    /// </summary>
    private Vector3[] checkPoints;

    // Use this for initialization
    void Start()
    {
        occlusionObject.SetActive(false);

        // Set the check points to use when testing for occlusion.
        MeshFilter filter = gameObject.GetComponent<MeshFilter>();
        Vector3 extents = filter.mesh.bounds.extents;
        Vector3 center = filter.mesh.bounds.center;
        Vector3 top = new Vector3(center.x, center.y + extents.y, center.z);
        Vector3 left = new Vector3(center.x - extents.x, center.y, center.z);
        Vector3 right = new Vector3(center.x + extents.x, center.y, center.z);
        Vector3 bottom = new Vector3(center.x, center.y - extents.y, center.z);

        checkPoints = new Vector3[] { center, top, left, right, bottom };
    }

    // Update is called once per frame
    void Update()
    {
        /* TODO: 5.a DEVELOPER CODING EXERCISE 5.a */

        // Check to see if any of the planet's boundary points are occluded.
        for (int i = 0; i < checkPoints.Length; i++)
        {
            // 5.a: Convert the current checkPoint to world coordinates.
            // Call gameObject.transform.TransformPoint(checkPoints[i]).
            // Assign the result to a new Vector3 variable called 'checkPt'.
            Vector3 checkPt = gameObject.transform.TransformPoint(checkPoints[i]);

            // 5.a: Call Vector3.Distance() to calculate the distance
            // between the Main Camera's position and 'checkPt'.
            // Assign the result to a new float variable called 'distance'.
            float distance = Vector3.Distance(Camera.main.transform.position, checkPt);

            // 5.a: Take 'checkPt' and subtract the Main Camera's position from it.
            // Assign the result to a new Vector3 variable called 'direction'.
            Vector3 direction = checkPt - Camera.main.transform.position;

            // Used to indicate if the call to Physics.Raycast() was successful.
            bool raycastHit = false;

            // 5.a: Check if the planet is occluded by a spatial mapping surface.
            // Call Physics.Raycast() with the following arguments:
            // - Pass in the Main Camera's position as the origin.
            // - Pass in 'direction' for the direction.
            // - Pass in 'distance' for the maxDistance.
            // - Pass in SpatialMappingManager.Instance.LayerMask as layerMask.
            // Assign the result to 'raycastHit'.
            raycastHit = Physics.Raycast(Camera.main.transform.position, direction, distance, SpatialMappingManager.Instance.LayerMask);

            if (raycastHit)
            {
                // 5.a: Our raycast hit a surface, so the planet is occluded.
                // Set the occlusionObject to active.
                occlusionObject.SetActive(true);

                // At least one point is occluded, so break from the loop.
                break;
            }
            else
            {
                // 5.a: The Raycast did not hit, so the planet is not occluded.
                // Deactivate the occlusionObject.
                occlusionObject.SetActive(false);
            }
        }
    }
}
```

**Compilazione e distribuzione**

* Compilare e distribuire l'applicazione in HoloLens, come di consueto.
* Attendere che l'analisi e l'elaborazione dei dati del mapping spaziale siano completate (le linee blu verranno visualizzate sui muri).
* Trovare e selezionare la casella di proiezione del sistema solare, quindi impostare la casella accanto a una parete o dietro un contatore.
* È possibile visualizzare l'occlusione di base nascondendo dietro le superfici al peer nel poster o nella casella di proiezione.
* Si osservi il terreno. dovrebbe essere presente un effetto evidenziato blu ogni volta che viene posizionato dietro un altro ologramma o superficie.
* Osservare come i pianeti si spostano dietro la parete o altre superfici della stanza. A questo punto è disponibile la visione x-ray e possono essere visualizzati gli scheletri wireframe.

## <a name="the-end"></a>La fine

Complimenti. A questo punto è stato completato il **mapping spaziale 230: mapping spaziale**.

* Si sa come analizzare l'ambiente e caricare i dati di mapping spaziale in Unity.
* Si conoscono le nozioni di base degli shader e il modo in cui è possibile usare i materiali per visualizzare nuovamente il mondo.
* Sono state apprese le nuove tecniche di elaborazione per individuare i piani e rimuovere i triangoli da una mesh.
* È possibile spostare e posizionare gli ologrammi su superfici che hanno senso.
* Sono state rilevate diverse tecniche di occlusione e sono state sfruttate le potenzialità della visione x-ray.

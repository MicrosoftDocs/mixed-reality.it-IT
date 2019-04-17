---
title: MR Spatial 230 - Spatial mapping
description: Seguire questa procedura dettagliata con Unity, Visual Studio e HoloLens che informazioni dettagliate sui concetti di mapping spaziale di codifica.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit unity, academy, esercitazione, mapping spaziale, la ricostruzione della superficie, mesh
ms.openlocfilehash: 8d5715337ddd20e9868b18fdf0c63c704f584972
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600923"
---
>[!NOTE]
>Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.  Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.  Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.  Essi verranno mantenute per continuare a utilizzare i dispositivi supportati. Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.  Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.

<br>

# <a name="mr-spatial-230-spatial-mapping"></a>MR Spatial 230: Mapping spaziale

[Mapping spaziale](spatial-mapping.md) unisce il mondo reale e il mondo virtuale da insegnare vntana sull'ambiente. MR spaziali 230 (progetto planetario) si apprenderà come:

* Analizzare i dati di ambiente e il trasferimento di HoloLens al computer di sviluppo.
* Esplorare gli shader e imparare a usarle per visualizzare lo spazio.
* Suddividere la rete mesh di chat room in semplici piani utilizzando l'elaborazione di rete.
* Andare oltre le tecniche di selezione host abbiamo imparato negli [MR nozioni di base 101](holograms-101.md)e fornire commenti e suggerimenti sulla posizione ologramma nell'ambiente.
* Esplorare gli effetti di occlusione, in modo che quando l'ologrammi sono protetto da un oggetto reale, è comunque possibile visualizzarlo con raggi x!

>[!VIDEO https://www.youtube.com/embed/NSNYRkUX6Mw]

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></th>
</tr><tr>
<td>MR Spatial 230: Mapping spaziale</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>Prima di iniziare

### <a name="prerequisites"></a>Prerequisiti

* Un PC Windows 10 configurate con i valori corretti [sono installati gli strumenti](install-the-tools.md).
* Alcuni basic C# capacità di programmazione.
* È necessario avere completato [MR nozioni di base 101](holograms-101.md).
* Un dispositivo HoloLens [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>File di progetto

* Scaricare il [file](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) necessarie per il progetto. Richiede Unity 2017.2 o versione successiva.
  * Se è comunque necessario il supporto di Unity 5.6, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip).
  * Se è comunque necessario il supporto di Unity 5.5, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip).
  * Se è ancora necessario supporto 5.4 di Unity, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip).
* Annullare la-archive i file sul desktop o altri facile da raggiungere percorso.

>[!NOTE]
>Se si desidera esaminare il codice sorgente prima di scaricare, ha [disponibile in GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping).

### <a name="notes"></a>Note

* "Abilita Just My Code" in Visual Studio deve essere disabilitato (*unchecked*) in Strumenti > Opzioni > debug per poter raggiungere punti di interruzione nel codice.

## <a name="unity-setup"></a>Programma di installazione di Unity

>[!VIDEO https://www.youtube.com/embed/y2Y4LhK6TEM]

* Avviare **Unity**.
* Selezionare **New** per creare un nuovo progetto.
* Denominare il progetto **planetario**.
* Verificare che il **3D** impostazione è selezionata.
* Fare clic su **Crea progetto**.
* Dopo aver avviato di Unity, passare a **Modifica > Impostazioni di progetto > Player**.
* Nel **Inspector** del pannello individuare e selezionare il colore verde **Windows Store** icona.
* Espandere **altre impostazioni**.
* Nel **Rendering** sezione, verificare il **supportato di realtà virtuale** opzione.
* Verificare che **Windows Holographic** viene visualizzato nell'elenco dei **SDK di realtà virtuale**. In caso contrario, selezionare la **+** pulsante nella parte inferiore dell'elenco e scegliere **Windows Holographic**.
* Espandere **impostazioni di pubblicazione**.
* Nel **funzionalità** sezione, verificare le impostazioni seguenti:
    * InternetClientServer
    * PrivateNetworkClientServer
    * Microfono
    * SpatialPerception
* Passare a **Modifica > impostazioni del progetto > qualità**
* Nel **Inspector** del pannello, sotto l'icona di Windows Store, seleziona la freccia nera elenco a discesa sotto la riga 'Default' e modificare l'impostazione predefinita al **Fastest**.
* Passare a **asset > Importa pacchetto > pacchetto personalizzato**.
* Passare il **...\HolographicAcademy-Holograms-230-SpatialMapping\Starting** cartella.
* Fare clic su **Planetarium.unitypackage**.
* Fare clic su **Apri**.
* Un' **Importa pacchetto Unity** verrà visualizzata la finestra, fare clic sulla **importazione** pulsante.
* Attendere per Unity importare tutte le risorse che è necessario completare questo progetto.
* Nel **gerarchia** panel, eliminare il **Main Camera**.
* Nel **Project** pannello **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** cartella trovare il **Main Camera** oggetto.
* Trascinare e rilasciare il **Main Camera** prefab nel **gerarchia** pannello.
* Nel **gerarchia** panel, eliminare il **Directional Light** oggetto.
* Nel **Project** pannello **Vntana** cartella, individuare il **cursore** oggetto.
* Trascinare e rilasciare il **cursore** prefab nel **gerarchia**.
* Nel **gerarchia** riquadro, seleziona la **cursore** oggetto.
* Nel **Inspector** del pannello, fare clic sul **Layer** elenco a discesa e selezionare **modificare i livelli...** .
* Nome **livello di utente 31** come "**SpatialMapping**".
* Salvare la nuova scena: **File > Salva scena come...**
* Fare clic su **nuova cartella** e denominare la cartella **scene**.
* Denominare il file "**planetario**" e salvarlo nel **scene** cartella.

## <a name="chapter-1---scanning"></a>Capitolo 1 - l'analisi

>[!VIDEO https://www.youtube.com/embed/888oW51z_cE]

**Obiettivi**
* Scopri il SurfaceObserver e in che modo l'impatto delle impostazioni esperienza e le prestazioni.
* Creare una chat room analisi esperienza per raccogliere le trame della chat.

**Istruzioni**
* Nel **Project** pannello **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** cartella trovare il **SpatialMapping** prefab.
* Trascinare e rilasciare il **SpatialMapping** prefab nel **gerarchia** pannello.

**Compila e Distribuisci (parte 1)**
* In Unity, selezionare **File > Build Settings**.
* Fare clic su **aggiungere scene Open** per aggiungere il **planetario** scena alla compilazione.
* Selezionare **Universal Windows Platform** nel **Platform** elenco e fare clic su **commutatore piattaforma**.
* Impostare **SDK** al **10 Universal** e **tipo di compilazione UWP** al **D3D**.
* Controllare **Unity C# progetti**.
* Fai clic su **Compila**.
* Creare un **nuova cartella** denominato "App".
* Solo clic i **App** cartella.
* Premere il **selezionare la cartella** pulsante.
* Quando l'operazione Unity viene eseguita la compilazione, verrà visualizzata una finestra di Esplora File.
* Fare doppio clic sulla **App** cartella per aprirla.
* Fare doppio clic su **Planetarium.sln** per caricare il progetto in Visual Studio.
* In Visual Studio, usare la barra degli strumenti superiore per modificare la configurazione per **rilascio**.
* Modificare la piattaforma **x86**.
* Fare clic sulla freccia giù a destra di 'Locale' e selezionare **computer remoto**.
* Immettere [indirizzo IP del dispositivo](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) l'indirizzo del campo e modificare la modalità di autenticazione per **universale (protocollo non crittografato)**.
* Fare clic su **Debug -> Avvia senza eseguire debug** o premere **Ctrl + F5**.
* Guarda il **Output** pannello in Visual Studio per la compilazione e distribuzione stato.
* Dopo aver distribuito l'app, scorrere nella stanza. Si noterà superfici circostante rientrano le reti mesh di wireframe bianco e nero.
* Analizzare l'ambiente circostante. Assicurarsi di esaminare le pareti, limiti e piani.

**Compila e Distribuisci (parte 2)**

Ora esaminiamo come Mapping spaziale può influire sulle prestazioni.
* In Unity, selezionare **finestra > Profiler**.
* Fare clic su **aggiungere Profiler > GPU**.
* Fare clic su **Profiler attivo > <Enter IP>** .
* Immettere il **indirizzo IP** di HoloLens.
* Fare clic su **Connetti**.
* Osservare il numero di millisecondi impiegato per la GPU eseguire il rendering di un frame.
* Interrompere l'applicazione in esecuzione nel dispositivo.
* Tornare a Visual Studio e aprire **SpatialMappingObserver.cs**. Si troverà nella cartella HoloToolkit\SpatialMapping del progetto di Assembly-CSharp (Windows universale).
* Trovare il **Awake()** funzione e aggiungere la riga di codice seguente: **TrianglesPerCubicMeter = 1200;**
* Ridistribuire il progetto sul dispositivo e quindi **riconnettere il profiler**. Osservare la modifica del numero di millisecondi per il rendering di un frame.
* Interrompere l'applicazione in esecuzione nel dispositivo.

**Salvare e caricare in Unity**

Infine, è possibile salvare la rete mesh di chat e caricarli in Unity.
* Tornare a Visual Studio e rimuovere i **TrianglesPerCubicMeter** riga aggiunta nel **Awake()** funzione durante la sezione precedente.
* Ridistribuire il progetto nel dispositivo. Si dovrebbe ora essere eseguito con **500** triangoli per metro cubo.
* Aprire un browser e immettere il HoloLens IPAddress per passare al **Windows Device Portal**.
* Selezionare il **vista 3D** opzione nel riquadro sinistro.
* Sotto **ricostruzione della superficie di attacco** selezionare la **Update** pulsante.
* Guarda le aree che sono analizzati in di HoloLens vengono visualizzati nella finestra di visualizzazione.
* Per salvare le analisi di chat, premere il **salvare** pulsante.
* Aprire il **Downloads** nella cartella e individuare il modello di spazio salvato **SRMesh.obj**.
* Copia **SRMesh.obj** per il **asset** cartella del progetto Unity.
* In Unity, selezionare la **SpatialMapping** dell'oggetto nel **gerarchia** pannello.
* Individuare il **oggetto area osservatore (Script)** componente.
* Fare clic sul cerchio a destra del **stanza modello** proprietà.
* Individuare e selezionare il **SRMesh** dell'oggetto e quindi chiudere la finestra.
* Verificare che il **modello chat Room** proprietà nel **Inspector** pannello è ora impostato su **SRMesh**.
* Premere il **riprodurre** pulsante per attivare la modalità di anteprima di Unity.
* Il componente SpatialMapping caricherà il mesh dal modello di spazio salvato in modo che è possibile usarli in Unity.
* Passare a **scena** visualizzazione per vedere tutto del modello di chat room visualizzato con lo shader wireframe.
* Premere il **riprodurre** pulsante per uscire dalla modalità di anteprima.

**NOTA:** La volta successiva immettere la modalità di anteprima in Unity, caricherà la mesh spazio salvato per impostazione predefinita.

## <a name="chapter-2---visualization"></a>Capitolo 2 - visualizzazione

>[!VIDEO https://www.youtube.com/embed/RnkvXl-aXD4]

**Obiettivi**
* Informazioni di base di shader.
* Visualizzare l'ambiente circostante.

**Istruzioni**
* Nella finestra di Unity **gerarchia** riquadro, seleziona la **SpatialMapping** oggetto.
* Nel **Inspector** panel, trovare il **Manager Mapping spaziale (Script)** componente.
* Fare clic sul cerchio a destra del **materiale area** proprietà.
* Individuare e selezionare il **BlueLinesOnWalls** materiale e chiudere la finestra.
* Nel **Project** pannello **shader** cartella, fare doppio clic su **BlueLinesOnWalls** per aprire lo shader in Visual Studio.
* Si tratta di un pixel semplice (vertice per frammentare) shader, che esegue le attività seguenti:
    1. Converte la posizione del vertice spazio globale.
    2. Controlla che il vertice 's normale per determinare se un pixel è verticale.
    3. Imposta il colore del pixel per il rendering.

**Compilare e distribuire**
* Tornare a Unity e premere **riprodurre** per attivare la modalità di anteprima.
* Verranno eseguito il rendering di linee blu su tutte le superfici verticale della rete locale (che viene caricata automaticamente dai nostri dati analisi salvati).
* Passare al **scena** pressione di tab per regolare la vista della chat room e vedere come mesh intero chat room viene visualizzato in Unity.
* Nel **Project** panel, trovare il **materiali** cartella e selezionare il **BlueLinesOnWalls** materiale.
* Modificare alcune proprietà e vedere come vengono visualizzate le modifiche apportate nell'editor di Unity.
    * Nel **Inspector** panel, regolare le **LineScale** valore come è possibile visualizzare le righe più spesso o più sottili.
    * Nel **Inspector** del pannello, regolare le **LinesPerMeter** valore per modificare il numero di righe vengono visualizzati su ogni parete.
* Fare clic su **riprodurre** per uscire dalla modalità di anteprima.
* Compilare e distribuire di HoloLens e osservare l'aspetto dello shader per il rendering su superfici reali.

Unity offre interessanti di visualizzazione in anteprima dei materiali, ma è sempre una buona idea per il rendering di estrazione nel dispositivo.

## <a name="chapter-3---processing"></a>Capitolo 3 - elaborazione

>[!VIDEO https://www.youtube.com/embed/kaUKiNiDxwY]

**Obiettivi**
* Informazioni sulle tecniche per l'elaborazione dati di mapping spaziale da utilizzare nell'applicazione.
* Analizzare i dati di mapping spaziale per trovare i piani e rimuovere triangoli.
* Usare i piani per la selezione host di ologramma.

**Istruzioni**
* Nella finestra di Unity **progetto** pannello **Vntana** cartella trovare il **SpatialProcessing** oggetto.
* Trascinare e rilasciare il **SpatialProcessing** all'oggetto il **gerarchia** pannello.

Il prefab SpatialProcessing include i componenti per l'elaborazione dei dati di mapping spaziale. **SurfaceMeshesToPlanes.cs** troveranno e generare piani in base ai dati di mapping spaziale. Si userà i piani nella nostra applicazione per rappresentare le pareti, piani e parte intera superiore. Include anche questo prefab **RemoveSurfaceVertices.cs** cui poter rimuovere i vertici mesh mapping spaziale. Può essere utilizzato per creare aree libere nella mesh o rimuovere in eccesso triangoli che non sono più necessarie (perché è invece possono utilizzare piani).
* Nella finestra di Unity **progetto** pannello **Vntana** cartella trovare il **SpaceCollection** oggetto.
* Trascinare e rilasciare il **SpaceCollection** all'oggetto il **gerarchia** pannello.
* Nel **gerarchia** riquadro, seleziona la **SpatialProcessing** oggetto.
* Nel **Inspector** panel, trovare il **riprodurre spazio Manager (Script)** componente.
* Fare doppio clic su **PlaySpaceManager.cs** per aprirlo in Visual Studio.

PlaySpaceManager.cs contiene codice specifico dell'applicazione. Si aggiungeranno funzionalità per questo script per abilitare il comportamento seguente:
1. Arrestare la raccolta dei dati di mapping spaziale dopo abbiamo superano il limite di tempo di analisi (10 secondi).
2. Elaborare i dati di mapping spaziale:
    1. Usare SurfaceMeshesToPlanes per creare una semplice rappresentazione del mondo come piani (walls pavimenti, limiti, e così via).
    2. Utilizzare RemoveSurfaceVertices rimuovere superficie triangoli che rientrano nei limiti del piano.
3. Generare una raccolta di vntana in tutto il mondo e collocarli in piani muro e floor vicino all'utente.

Eseguire gli esercizi di scrittura di codice contrassegnati in PlaySpaceManager.cs o sostituire lo script con la soluzione finale dal codice seguente:

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

**Compilare e distribuire**
* Prima di distribuire il HoloLens, premere il **riprodurre** pulsante in Unity per attivare la modalità di riproduzione.
* Al termine della mesh chat room viene caricata da file, attendere 10 secondi prima che inizi l'elaborazione della rete di mapping spaziale.
* Una volta completata l'elaborazione, i piani verranno visualizzato per rappresentare la parte intera pareti, ceiling, e così via.
* Dopo che tutti i piani di sono stati trovati, verrà visualizzato un sistema solare in una tabella di floor vicino alla fotocamera.
* Due poster dovrebbe essere visualizzato troppo sui muri vicino alla fotocamera. Passare al **scena** se non è possibile visualizzarli nella **gioco** modalità.
* Premere il **riprodurre** pulsante per uscire dalla modalità di gioco.
* Compilare e distribuire per HoloLens, come di consueto.
* Attesa per l'analisi e l'elaborazione dei dati spaziali mapping per il completamento.
* Dopo aver visualizzato i piani, provare a trovare il poster e il sistema solare in tutto il mondo.

## <a name="chapter-4---placement"></a>Capitolo 4 - Selezione host

>[!VIDEO https://www.youtube.com/embed/Srhtpid1uZc]

**Obiettivi**
* Determinare se ologramma rientrerà in una superficie.
* Fornire un feedback all'utente quando ologramma can/non rientra in una superficie.

**Istruzioni**
* Nella finestra di Unity **gerarchia** riquadro, seleziona la **SpatialProcessing** oggetto.
* Nel **Inspector** panel, trovare il **trame per piani area (Script)** componente.
* Modifica il **disegnare piani** proprietà **Nothing** di deselezione della selezione.
* Modifica il **disegnare piani** proprietà **parete**, in modo che solo i piani wall verranno sottoposti a rendering.
* Nel **Project** pannello **script** cartella, fare doppio clic su **Placeable.cs** per aprirlo in Visual Studio.

Il **Placeable** script è già associato ai poster e finestra di proiezione che vengono creati al termine dell'individuazione di piano. Tutto dobbiamo fare è rimuovere il commento del codice e lo script verrà ottenere quanto segue:
1. Determinare se ologramma rientrerà in una superficie da raycasting dal centro e quattro angoli del rettangolo di selezione cubo.
2. Verifica per determinare se è abbastanza uniforme per ologrammi attendere flush in normale alla superficie.
3. Eseguire il rendering di un cubo di delimitazione intorno ologramma per mostrare l'effettiva dimensione durante l'inserimento.
4. Eseguire il cast di ologramma per mostrare in cui verrà inserito sul pavimento/muro sotto e dietro un'ombreggiatura.
5. Eseguire il rendering dell'ombreggiatura in rosso, se l'ologrammi non possono trovarsi sulla superficie, o verde, se possibile.
6. Orientare nuovamente di ologramma per allinearli con il tipo di area (verticale o orizzontale) che disponga di affinità.
7. Posizionare in modo uniforme l'ologrammi nell'area di selezionato per evitare il passaggio o il comportamento di blocco.

Rimuovere il commento da tutto il codice nell'esercizio scrittura di codice riportato di seguito oppure usare questa soluzione completata nelle **Placeable.cs**:

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
    /// The aligntoVerticalSurface parameter is ignored if the object
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

**Compilare e distribuire**
* Come in precedenza, compilare il progetto e distribuire il HoloLens.
* Attesa per l'analisi e l'elaborazione dei dati spaziali mapping per il completamento.
* Quando viene visualizzato il sistema solare, fissare la casella di proiezione seguito ed eseguire un gesto seleziona spostarla all'interno. Dopo avere selezionata la casella di proiezione, un cubo di delimitazione sarà visibile intorno alla casella di proiezione.
* Spostare head per fissare un percorso diverso nella chat room. La casella di proiezione deve seguire lo sguardo. Quando l'ombreggiatura sotto la casella di proiezione in rosso, è possibile posizionare l'ologrammi in tale area. Quando l'ombreggiatura sotto la casella di proiezione diventa verde, è possibile inserire l'ologrammi eseguendo il movimento di seleziona un altro.
* Trovare e selezionare uno dei poster holographic su una parete per spostarlo in una nuova posizione. Si noti che non è possibile posizionare il poster per il piano o il limite massimo, e che sia sempre orientamento corretto per ogni muro si sposta all'interno.

## <a name="chapter-5---occlusion"></a>Capitolo 5 - occlusione

>[!VIDEO https://www.youtube.com/embed/6Xrzh_w-7SE]

**Obiettivi**
* Determinare se un ologrammi sono nascosto dalla trama mapping spaziale.
* Applicare le tecniche relative all'occlusione diversa per ottenere un divertente effetto.

**Istruzioni**

In primo luogo, si userà per consentire la mesh mapping spaziale nasconde i colori altri vntana senza occluding del mondo reale:
* Nel **gerarchia** riquadro, seleziona la **SpatialProcessing** oggetto.
* Nel **Inspector** panel, trovare il **riprodurre spazio Manager (Script)** componente.
* Fare clic sul cerchio a destra del **materiale secondario** proprietà.
* Individuare e selezionare il **occlusione** materiale e chiudere la finestra.

Successivamente, si intende aggiungere un comportamento speciale a terra, in modo che includa un'evidenziazione blu ogni volta che si viene bloccato da un altro ologrammi (ad esempio il sole) o dalla trama mapping spaziale:
* Nel **Project** pannello il **Vntana** cartella, espandere il **SolarSystem** oggetto.
* Fare clic su **terra**.
* Nel **Inspector** panel, individuare il materiale della terra (componente).
* Nel **discesa Shader**, modificare lo shader **Custom > OcclusionRim**. Questo verrà eseguito il rendering di un'evidenziazione blu attorno a terra ogni volta che viene bloccato da un altro oggetto.

Infine, si intende abilitare un effetto di visione artificiale x-ray per pianeti nel nostro sistema solare. È necessario modificare **PlanetOcclusion.cs** (disponibile nella cartella Scripts\SolarSystem) per ottenere quanto segue:
1. Determinare se un pianeta è bloccato dal livello SpatialMapping (chat room mesh e piani).
2. Mostra la rappresentazione di wireframe di un mondo ogni volta che si è bloccato dal livello SpatialMapping.
3. Nascondere la rappresentazione di wireframe di un pianeta quando non sono bloccata dal livello SpatialMapping.

Seguire l'esercizio di scrittura di codice in PlanetOcclusion.cs o usare la soluzione seguente:

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

**Compilare e distribuire**
* Compilare e distribuire l'applicazione per HoloLens, come di consueto.
* Attesa per l'analisi e l'elaborazione dei dati spaziali mapping per il completamento (visualizzata linee blu vengono visualizzati sui muri).
* Trovare e selezionare casella proiezione del sistema solare e quindi impostare la casella accanto a una parete o dietro un contatore.
* È possibile visualizzare occlusione base dietro superfici di eseguire il peering nella casella di poster o proiezione.
* Cercare la terra, dovrebbe esserci un effetto di evidenziazione blu ogni volta che diventa protetto da un altro ologrammi o area.
* Guarda i pianeti spostata dietro la parete o altre superfici nella chat room. È ora hanno raggi x ed è possibile visualizzare gli scheletri di wireframe.

## <a name="the-end"></a>La fine

La procedura è stata completata. Sono stati completati **SIG spaziali 230: Mapping spaziale**.
* Si sa come analizzare i dati di ambiente e carico mapping spaziale a Unity.
* Comprendere le nozioni di base di shader e come materiali possono essere usati per visualizzare nuovamente il mondo.
* Si è appreso di nuove tecniche di elaborazione per l'individuazione di piani e rimozione triangoli da una rete mesh.
* È stato possibile spostare e posizionare vntana nelle aree che non aveva senso.
* Si è verificato tecniche diverse relative all'occlusione e sfruttate le potenzialità di raggi x!

---
title: Raccomandazioni sulle prestazioni per Unity
description: Suggerimenti specifici del Unity per migliorare le prestazioni con le app di realtà mista.
author: Troy-Ferrell
ms.author: trferrel
ms.date: 03/26/2019
ms.topic: article
keywords: gli elementi grafici, cpu, gpu, il rendering, la garbage collection, hololens
ms.openlocfilehash: 37eac566a0315009330ac7fee96edd82348d6ba3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604910"
---
# <a name="performance-recommendations-for-unity"></a>Raccomandazioni sulle prestazioni per Unity

Questo articolo si basa sulla discussione descritta nella [raccomandazioni sulle prestazioni per realtà mista](understanding-performance-for-mixed-reality.md) ma si concentra su informazioni specifiche per l'ambiente di motore Unity.

È anche consigliabile che gli sviluppatori di rivedere le [consigliati delle impostazioni di ambiente per l'articolo di Unity](Recommended-settings-for-unity.md). Questo articolo offre contenuti con alcune delle configurazioni di scena più importanti in merito alla creazione di App di realtà mista ad alte prestazioni. Alcune di queste impostazioni consigliate vengono evidenziate anche di seguito.

## <a name="how-to-profile-with-unity"></a>Come eseguire la profilatura con Unity

Unity offre il **[Profiler di Unity](https://docs.unity3d.com/Manual/Profiler.html)** predefinite che è un'ottima risorsa per raccogliere informazioni dettagliate preziose sulle prestazioni per l'app specifica. Anche se sarà possibile eseguire il profiler nell'editor, queste metriche non rappresentano l'ambiente di runtime true e di conseguenza, i risultati da questo oggetto devono essere utilizzati con cautela. È consigliabile profilare in modalità remota dell'applicazione durante l'esecuzione nel dispositivo per informazioni dettagliate più accurate e utilizzabili. Inoltre, di Unity [Frame Debugger](https://docs.unity3d.com/Manual/FrameDebugger.html) è anche molto potente e strumento informazioni dettagliate da utilizzare.

Unity offre documentazione molto utile per:
1) Come connettere il [profiler di Unity per le applicazioni UWP in modalità remota](https://docs.unity3d.com/Manual/windowsstore-profiler.html)
2) Come in modo efficace [diagnosticare i problemi di prestazioni con il Profiler di Unity](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)

>[!NOTE]
> Con il Profiler di Unity connessi e dopo l'aggiunta del profiler GPU (vedere *Profiler aggiungere* nell'angolo superiore destro), si possono osservare quanto viene impiegato il tempo della CPU & GPU rispettivamente al centro del profiler. Questo consente allo sviluppatore di ottenere un'approssimazione rapida se l'applicazione della CPU o GPU delimitato.
>
> ![CPU di Unity per vs GPU](images/unity-profiler-cpu-gpu.png)

## <a name="cpu-performance-recommendations"></a>Raccomandazioni per le prestazioni della CPU

Il contenuto seguente vengono illustrate altre procedure consigliate approfondite ad alte prestazioni, destinate in particolare per Unity & C# sviluppo.

#### <a name="cache-references"></a>Riferimenti cache

È consigliabile i riferimenti a tutti i componenti pertinenti e Gameobject in fase di inizializzazione. Infatti, ripetere le chiamate di funzione, ad esempio *[GetComponent\<T > ()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* sono molto più costoso rispetto alla memoria di costo per archiviare un puntatore. Questo vale anche per a di molto, regolarmente usati [Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html). *Camera.Main* semplicemente Usa *[FindGameObjectsWithTag()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* sotto il grafico della scena per un oggetto della fotocamera con un costo esegue la ricerca di *"MainCamera"*  tag.

```CS
using UnityEngine;
using System.Collections;

public class ExampleClass : MonoBehaviour
{
    private Camera cam;
    private CustomComponent comp;

    void Start() 
    {
        cam = Camera.main;
        comp = GetComponent<CustomComponent>();
    }

    void Update()
    {
        // Good
        this.transform.position = cam.transform.position + cam.transform.forward * 10.0f;

        // Bad
        this.transform.position = Camera.main.transform.position + Camera.main.transform.forward * 10.0f;

        // Good
        comp.DoSomethingAwesome();

        // Bad
        GetComponent<CustomComponent>().DoSomethingAwesome();
    }
}
```

>[!NOTE] Evitare GetComponent(string) <br/>
> Quando si usa  *[GetComponent()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)*, esistono una vasta gamma di overload differenti. È importante usare sempre le implementazioni di tipo di base e mai l'overload di ricerca basate su stringa. La ricerca dalla stringa nella scena è notevolmente più costosa rispetto alla ricerca in base al tipo. <br/>
> (Valido) Componente GetComponent (tipo tipo) <br/>
> (Valido) T GetComponent\<T >) <br/>
> (Negativo) Componente GetComponent(string) > <br/>

#### <a name="avoid-expensive-operations"></a>Evitare operazioni costose

1) **Evitare l'uso di [LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)**

    Sebbene LINQ può essere molto pulito e facile da leggere e scrivere, in genere richiede molto più calcoli e più in particolare allocazione di memoria rispetto alla scrittura manualmente l'algoritmo.

    ```CS
    // Example Code
    using System.Linq;

    List<int> data = new List<int>();
    data.Any(x => x > 10);

    var result = from x in data
                 where x > 10
                 select x;
    ```

2) **API comuni di Unity**

    Alcune API di Unity, sebbene utile, può risultare dispendiosa da eseguire. La maggior parte di questi implica la ricerca del grafico della scena intera per un elenco di Gameobject corrispondenti. Queste operazioni possono essere evitate in genere la memorizzazione nella cache i riferimenti o implementando un componente di gestione per il Gameobject in questione rilevare i riferimenti in fase di esecuzione.

        GameObject.SendMessage()
        GameObject.BroadcastMessage()
        UnityEngine.Object.Find()
        UnityEngine.Object.FindWithTag()
        UnityEngine.Object.FindObjectOfType()
        UnityEngine.Object.FindObjectsOfType()
        UnityEngine.Object.FindGameObjectsWithTag()
        UnityEngine.Object.FindGameObjectsWithTag()

>[!NOTE]
> *[SendMessage ()](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)*  e *[BroadcastMessage()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* dovrebbero essere eliminate a tutti i costi. Queste funzioni possono essere nell'ordine di 1000 x più lento rispetto alle chiamate di funzione diretta.

3) **Prestare attenzione della conversione boxing**

    [La conversione boxing](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing) è un concetto fondamentale del C# runtime e linguaggio. È il processo di ritorno a capo nelle variabili di tipo reference valori variabili, ad esempio char, int, bool e così via. Quando una variabile di valore tipizzato è "boxing", vengono incapsulati all'interno di un System. Object, che viene archiviato nell'heap gestito. Di conseguenza, la memoria viene allocata e alla fine quando eliminata devono essere elaborate dal garbage collector. Queste allocazioni e deallocazioni comportano una riduzione delle prestazioni e in molti scenari non sono necessari o possono essere facilmente sostituite da un'alternativa meno costosa.

#### <a name="repeating-code-paths"></a>Ripetere i percorsi del codice

Qualsiasi funzione di callback di Unity (ad esempio ripetuti Aggiornamento) che vengono eseguite molte volte al secondo e/o frame deve essere scritti con estrema cautela. Operazioni dispendiose qui avrà enorme e coerenti con l'impatto sulle prestazioni.

1) **Funzioni di callback vuoto**

    Anche se può sembrare innocente a lasciare nell'applicazione, soprattutto perché ogni Unity script automatico inizializza con il blocco di codice, il codice riportato di seguito questi callback vuoti possono effettivamente diventare molto costosi. Unity opera e viceversa attraverso un limite di codice non gestita/gestita, tra codice UnityEngine e il codice dell'applicazione. Tramite questo bridge il cambio di contesto è piuttosto dispendioso, anche se non c'è niente da eseguire. Ciò risulta particolarmente problematico se l'app contiene centinaia di Gameobject con componenti che devono vuoto i callback di Unity ripetuti.

    ```CS
    void Update()
    {
    }
    ```

>[!NOTE]
> Update () è la manifestazione più comune di questo problema di prestazioni, ma altri callback Unity ripetuti, ad esempio di seguito possono essere ugualmente errata se non peggiore: FixedUpdate(), LateUpdate(), OnPostRender", OnPreRender(), OnRenderImage(), etc. 

2) **Operazioni per favorire la riduzione in esecuzione una sola volta per ogni fotogramma**

    Le seguenti API di Unity sono operazioni comuni per molte App Holographic. Anche se non è sempre possibile, i risultati di queste funzioni molto di frequente possono essere calcolati una volta e i risultati nuovamente utilizzata in tutta l'applicazione per un determinato intervallo.

    a) a livello generale è consigliabile avere una classe Singleton o gestire lo sguardo Raycast nella scena e quindi riutilizzare questo risultato in tutti gli altri componenti di scena, invece di effettuare operazioni Raycast ripetute ed essenzialmente identiche da ogni servizio dedicato componente. Naturalmente, è possibile che alcune applicazioni richiedano raycasts da origini diverse o con diversi [LayerMasks](https://docs.unity3d.com/ScriptReference/LayerMask.html).

        UnityEngine.Physics.Raycast()
        UnityEngine.Physics.RaycastAll()

    b) GetComponent() operazioni ripetute di callback di Unity come Update () per evitare [memorizzazione nella cache i riferimenti](#cache-references) in Start () o Awake()

        UnityEngine.Object.GetComponent()

    c) è consigliabile creare un'istanza di tutti gli oggetti, se possibile, inizializzazione e di utilizzo [pool di oggetti](#object-pooling) per riciclare e riutilizzare Gameobject in fase di esecuzione dell'applicazione

        UnityEngine.Object.Instantiate()

3) **Evitare interfacce e costrutti virtuali**

    Chiamate di funzione tramite oggetti diretti di interfacce Visual Studio o la chiamata di funzioni virtuali può spesso essere notevolmente più costoso che usano costrutti diretti o chiamate di funzione diretta. Se la funzione virtuale o l'interfaccia è necessaria, deve essere rimossa. Tuttavia, le prestazioni riscontri per questi approcci sono in genere è la pena di compromesso se che li usano semplifica la collaborazione di sviluppo, la leggibilità del codice e la gestibilità del codice. 

4) **Evitare gli struct di passaggio per valore**

    A differenza delle classi, struct sono tipi di valore e quando viene passato direttamente a una funzione, i relativi contenuti vengono copiati in un'istanza appena creata. Questa copia aggiunge della CPU, nonché memoria aggiuntiva nello stack. Per gli struct di piccole dimensioni, l'effetto è in genere molto limitate e pertanto accettabili. Tuttavia, per le funzioni richiamato più volte per ogni fotogramma, nonché le funzioni richiede le strutture di grandi dimensioni, se possibile modificare la definizione di funzione venga passato per riferimento. [Altre informazioni sono disponibili qui](https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method)

#### <a name="miscellaneous"></a>Varie

1) **Fisica**

    a) il modo più semplice per migliorare la fisica è a livello generale, per limitare la quantità di tempo trascorso in fisica o il numero di iterazioni al secondo. Naturalmente, ciò riduce la precisione di simulazione. Visualizzare [TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html) in Unity

    b) il tipo di colliders in Unity sono ampiamente diverse caratteristiche di prestazioni. L'ordine riportato di seguito sono elencate le maggior parte delle colliders ad alte prestazioni per almeno colliders ad alte prestazioni da sinistra a destra. È molto importante evitare Colliders Mesh che sono notevolmente più costoso il colliders primitivo.

        Sphere < Capsule < Box <<< Mesh (Convex) < Mesh (non-Convex)

    Visualizzare [Unity fisica consigliate](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices) per altre informazioni

2) **Animazioni**

    Disabilitare le animazioni inattività disabilitando il componente animatore (disabilitazione l'oggetto gioco non hanno lo stesso effetto). Evitare di modelli di progettazione in cui un animatore si trova in un ciclo impostando un valore per la stessa cosa. È un notevole sovraccarico per questa tecnica, senza alcun effetto sull'applicazione. [Altre informazioni sono disponibili qui.](https://docs.unity3d.com/Manual/MecanimPeformanceandOptimization.html)

3) **Algoritmi complessi**

    Se l'applicazione usa algoritmi complessi, ad esempio cinematica inversa, ricerca di percorso, e così via, ricerca per trovare un approccio più semplice o modificare le impostazioni rilevanti per le prestazioni

## <a name="cpu-to-gpu-performance-recommendations"></a>Raccomandazioni per le prestazioni della CPU-a-GPU

In genere, le prestazioni della CPU-a-GPU deduce il **le chiamate di disegno** inviato a una scheda grafica. Per migliorare le prestazioni, devono essere in modo strategico le chiamate di disegno **a) ridotta** oppure **b) ristrutturato** per ottenere risultati ottimali. Poiché le chiamate di disegno stessi sono a elevato utilizzo di risorse, riducendo le ridurrà complessiva lavoro richiesto. Inoltre, lo stato delle modifiche tra le chiamate di disegno richiede la convalida costosa e di passaggi di traduzione dei driver di grafica e di conseguenza, la ristrutturazione delle chiamate di disegno dell'applicazione per limitare le modifiche dello stato (ad es. diversi materiali e così via) può migliorare le prestazioni.

Unity è un articolo eccezionale che offra una panoramica e approfondisce l'invio in batch le chiamate di disegno per la propria piattaforma.
- [Unity disegnare chiamata di invio in batch](https://docs.unity3d.com/Manual/DrawCallBatching.html)

#### <a name="single-pass-instanced-rendering"></a>Rendering singola istanza

Grazie al passaggio singolo Instanced Rendering in Unity per le chiamate di disegno per ogni occhio venga ridotta fino alla chiamata di disegno istanza uno. A causa della coerenza della cache tra due chiamate di disegno, è inoltre disponibile un miglioramento delle prestazioni nella GPU anche.

Per abilitare questa funzionalità nel progetto Unity
1)  Open **le impostazioni del giocatore XR** (Vai al **modifica** > **impostazioni progetto** > **Player**  >  **XR impostazioni**)
2) Selezionare **singola istanza di passare** dal **Stereo metodo di Rendering** dal menu a discesa (**supportato di realtà virtuale** deve essere selezionata la casella di controllo)

Per informazioni dettagliate con questo approccio per il rendering, leggere gli articoli seguenti da Unity.
- [Come ottimizzare le prestazioni di AR e VR con rendering stereo avanzate](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [Creazione di istanze di passaggio singolo](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 

>[!NOTE]
> Si verifica un problema comune relativo all'unico passare istanze per il Rendering se sviluppatori dispongono già di shader personalizzati esistenti non scritti per la creazione di istanze. Dopo aver abilitato questa funzionalità, gli sviluppatori potrebbero notare alcuni Gameobject solo eseguire il rendering in un occhio. Infatti, gli shader personalizzati associati non hanno le proprietà appropriate per la creazione di istanze.
>
> Visualizzare [singolo passare Stereo Rendering per HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) da Unity per la procedura risolvere questo problema

#### <a name="static-batching"></a>L'invio in batch statico

Unity è in grado di inviare in batch numerosi oggetti statici per ridurre le chiamate di disegno nella GPU. L'invio in batch statica funziona per la maggior parte [Renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) gli oggetti in Unity che **1) condividono lo stesso materiale** e **2) sono tutte contrassegnate come *statico***  ( Selezionare un oggetto in Unity e selezionare la casella di controllo nella parte superiore destra della finestra di ispezione). Gameobject contrassegnato come *statici* non possono essere spostati in fase di esecuzione dell'applicazione. Di conseguenza, può essere difficile sfruttare su HoloLens in cui deve essere inserita, spostati, ridimensionati, e così via praticamente tutti gli oggetti statici di invio in batch. Per immersive auricolari, l'invio in batch statico può ridurre notevolmente le chiamate di disegno e pertanto migliorare le prestazioni.

Lettura *batch statici* sotto [disegnare chiamare l'invio in batch in Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) per altri dettagli.

#### <a name="dynamic-batching"></a>L'invio in batch dinamica

Poiché risulta problematico per contrassegnare gli oggetti come *statici* per lo sviluppo di HoloLens, l'invio in batch dinamica può essere uno strumento straordinario per rimediare a questa mancanza di funzionalità. Naturalmente, è possibile anche essere utile su anche auricolari coinvolgente e concreto. In Unity dinamica di invio in batch può essere difficile tuttavia abilitare perché deve Gameobject **a) Condividi lo stesso materiale** e **b) soddisfa un lungo elenco di altri criteri**.

Lettura *batch dinamiche* sotto [disegnare chiamare l'invio in batch in Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) per un elenco completo. In genere, Gameobject diventano non validi da inserire in batch in modo dinamico perché i dati di trama associato possono essere vertici non più di 300.

#### <a name="other-techniques"></a>altre tecniche

L'invio in batch può verificarsi solo se sono in grado di condividere lo stesso materiale Gameobject più. In genere questo verrà bloccato dalla necessità di disporre di una trama univoca per i rispettivi materiali Gameobject. È comune per combinare le trame in una trama di big data, un metodo noto come [trama Atlasing](https://en.wikipedia.org/wiki/Texture_atlas).

Inoltre, è in genere preferibile combinare mesh in un GameObject ove possibile e ragionevole. Ogni Renderer in Unity avrà sono associate a chiamate di disegno e invio di una rete mesh di combinati in un Renderer. 

>[!NOTE]
> Modifica delle proprietà di Renderer.material in fase di esecuzione crea una copia del materiale e pertanto causare il malfunzionamento di invio in batch. Consente di modificare le proprietà materiale condivise tra Gameobject Renderer.sharedMaterial.

## <a name="gpu-performance-recommendations"></a>Raccomandazioni sulle prestazioni di GPU

Altre informazioni su [ottimizzazione del rendering della grafica in Unity](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)

#### <a name="reduce-poly-count"></a>Ridurre il numero di poligono

Numero di poligono in genere viene ridotto di uno
1) Rimozione di oggetti in una scena
2) Decimazione asset che riduce il numero di poligoni per una determinata rete
3) Implementazione di un [sistema a livello di dettaglio della TRAMA](https://docs.unity3d.com/Manual/LevelOfDetail.html) nell'applicazione che esegue il rendering a portata di mano gli oggetti con versione inferiore poligono della stessa geometria

#### <a name="limit-overdraw"></a>Limite di caricamento

In Unity, uno può visualizzare estenda per le scene, attivando e disattivando il [ **disegnare menu modalità** ](https://docs.unity3d.com/Manual/ViewModes.html) nell'angolo superiore sinistro del **visualizzazione scena** e selezionando **carica presente** .

In generale, estenda può essere attenuata della faccia posteriore oggetti anticipo prima che vengano inviati alla GPU. Unity offre informazioni dettagliate sull'implementazione [occlusione della faccia posteriore](https://docs.unity3d.com/Manual/OcclusionCulling.html) per il motore.

#### <a name="understanding-shaders-in-unity"></a>Shader comprensione in Unity

Un'approssimazione semplice per confrontare gli shader nelle prestazioni è per identificare il numero medio di operazioni ogni eseguita in fase di esecuzione. Questa operazione può essere eseguita abbastanza facilmente in Unity.

1) Selezionare l'asset shader o selezionare un materiale, quindi nell'angolo superiore destro della finestra del controllo, selezionare l'icona a forma di ingranaggio e quindi **"Selezionare Shader"**

    ![Selezionare dello shader in Unity](images/Select-shader-unity.png)
2) Con l'asset shader selezionato, scegliere il **"Compilazione e la visualizzazione codice"** pulsante sotto la finestra di controllo

    ![Compilare il codice dello Shader in Unity](images/compile-shader-code-unity.PNG)

3) Dopo la compilazione, cercare la sezione relativa alle statistiche nei risultati con il numero di operazioni diverse per pixel e vertex shader (Nota: i pixel shader sono spesso l'acronimo di shader frammento)

    ![Operazioni Standard di Shader di Unity](images/unity-standard-shader-compilation.png)

##### <a name="unity-standard-shader-alternatives"></a>Alternative Standard shader Unity

Anziché utilizzare un rendering basato su fisicamente (PBR) o altri shader di alta qualità, osservare che usano un più efficiente e più economica dello shader. [Toolkit di realtà mista](https://github.com/Microsoft/MixedRealityToolkit-Unity) fornisce una [shader standard](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/StandardAssets/Shaders/MixedRealityStandard.shader) che è stato ottimizzato per i progetti di realtà mista.

Unity offre anche un spento, vertice è acceso, le opzioni di shader semplificata con riflessione diffusa e altri che sono significativamente più veloce rispetto a shader Unity Standard. Visualizzare [informazioni sull'utilizzo e prestazioni di shader predefinito](https://docs.unity3d.com/Manual/shader-Performance.html) per informazioni più dettagliate.

## <a name="memory-recommendations"></a>Consigli sulla memoria

Operazioni di allocazione e deallocazione di memoria eccessiva possono avere effetti negativi sull'applicazione holographic causando prestazioni incoerenti, frame bloccati e altri comportamenti dannosi. È particolarmente importante comprendere considerazioni sulla memoria quando si sviluppa in Unity, poiché la gestione della memoria è controllata dal garbage collector.

#### <a name="garbage-collection"></a>Operazione di Garbage collection

Le app holographic andranno perse se tempo di calcolo di elaborazione per il garbage collector (GC) quando il Garbage Collector è attivato per analizzare gli oggetti che non sono più nell'ambito durante l'esecuzione e la relativa memoria deve essere rilasciato e può essere reso disponibile per essere riusata. Deprovisioning e le allocazioni costante richiede in genere il garbage collector eseguire più spesso le prestazioni promuovendo così ed esperienza utente.

Unity ha fornito un'eccellente pagina che illustra in dettaglio il funzionamento di garbage collector e suggerimenti per scrivere codice più efficiente in merito alla gestione della memoria.
- [Ottimizzazione della procedura di garbage collection in giochi Unity](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)

Una delle abitudini più comuni che conduce a un numero eccessivo di operazioni di garbage collection non memorizza nella cache i riferimenti a componenti e le classi nello sviluppo di Unity. Tutti i riferimenti devono essere acquisiti durante Start () o Awake() e riusati in funzioni più avanti, ad esempio Update () o LateUpdate().

Altri suggerimenti rapidi:
- Usare la [StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) C# classe per la creazione in modo dinamico le stringhe complesse in fase di esecuzione
- Rimuovere le chiamate a Debug.Log() quando non servono più mentre vengono ancora eseguite in tutte le versioni di compilazione di un'app
- Se l'app holographic richiede in genere grandi quantità di memoria, si consiglia di chiamare [ _**System.GC.Collect ()**_ ](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2) durante il caricamento di fasi, ad esempio per la presentazione di un caricamento o schermata di transizione

#### <a name="object-pooling"></a>Pool di oggetti

Il pool degli oggetti è una tecnica comune per ridurre il costo delle allocazioni di continuo e le deallocazioni di oggetti. Questa operazione viene eseguita, allocando un ampio pool di oggetti identici e riutilizzo di istanze inattive, disponibile da questo pool anziché continuamente durante la generazione e l'eliminazione definitiva di oggetti nel corso del tempo. Pool di oggetti sono ideali per i componenti riutilizzabili che includono la durata delle variabili durante un'app.

- [Esercitazione di Unity di pool di oggetti](https://unity3d.com/learn/tutorials/topics/scripting/object-pooling) 

## <a name="startup-performance"></a>Prestazioni di avvio

Avviare l'app con una scena più piccola, quindi l'uso, è necessario considerare *[SceneManager.LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* per caricare il resto della scena. Ciò consente all'app di ottenere lo stato interattivo nel minor tempo. Essere consapevoli che possono essere presenti uno spike elevato della CPU mentre viene attivata la nuova scena e che qualsiasi contenuto sottoposto a rendering potrebbe stuttering o nessuna difficoltà. Uno per risolvere questo problema consiste nell'impostare la proprietà AsyncOperation.allowSceneActivation su false nella scena in fase di caricamento, attendere la scena caricare, cancellare lo schermo nero e quindi reimpostato su true per completare l'attivazione di scena.

Tenere presente che mentre la scena di avvio viene caricata la schermata iniziale holographic verrà visualizzata all'utente.

## <a name="see-also"></a>Vedere anche
- [Ottimizzazione del rendering di grafica in giochi Unity](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games?playlist=44069)
- [Ottimizzazione della procedura di garbage collection in giochi Unity](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)
- [Procedure consigliate di fisica [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)
- [Ottimizzazione degli script [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)

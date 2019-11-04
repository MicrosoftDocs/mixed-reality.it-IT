---
title: Suggerimenti sulle prestazioni per Unity
description: Suggerimenti specifici per Unity per migliorare le prestazioni con le app di realtà mista.
author: Troy-Ferrell
ms.author: trferrel
ms.date: 03/26/2019
ms.topic: article
keywords: grafica, CPU, GPU, rendering, Garbage Collection, hololens
ms.openlocfilehash: 724ec24408e70360fda07c59a4ca2ffc30b49c1f
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438124"
---
# <a name="performance-recommendations-for-unity"></a>Suggerimenti sulle prestazioni per Unity

Questo articolo si basa sulla discussione descritta in [raccomandazioni sulle prestazioni per la realtà mista](understanding-performance-for-mixed-reality.md) , ma è incentrata sulle informazioni specifiche dell'ambiente del motore Unity.

È inoltre consigliabile che gli sviluppatori rivedano le [impostazioni di ambiente consigliate per l'articolo di Unity](Recommended-settings-for-unity.md). Questo articolo presenta contenuti con alcune delle configurazioni di scena più importanti in relazione alla creazione di app per realtà mista a prestazioni elevate. Alcune di queste impostazioni consigliate sono evidenziate anche di seguito.

## <a name="how-to-profile-with-unity"></a>Come eseguire la profilatura con Unity

Unity offre il **[Profiler di Unity](https://docs.unity3d.com/Manual/Profiler.html)** , che è un'ottima risorsa per raccogliere informazioni preziose sulle prestazioni per la tua app specifica. Sebbene sia possibile eseguire il profiler in-Editor, queste metriche non rappresentano l'ambiente di runtime reale e, di conseguenza, i risultati di questa operazione devono essere usati con cautela. È consigliabile profilare l'applicazione in modalità remota mentre è in esecuzione nel dispositivo per ottenere informazioni più accurate e di utilità pratica. Inoltre, il [debugger frame](https://docs.unity3d.com/Manual/FrameDebugger.html) di Unity è anche uno strumento molto potente e Insight da usare.

Unity offre la documentazione ideale per:
1) Come connettere [Unity Profiler alle applicazioni UWP in remoto](https://docs.unity3d.com/Manual/windowsstore-profiler.html)
2) Come diagnosticare in modo efficace [i problemi di prestazioni con Unity Profiler](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)

>[!NOTE]
> Con il profiler di Unity connesso e dopo l'aggiunta del profiler della GPU (vedere *aggiungere Profiler* nell'angolo superiore destro), è possibile visualizzare il tempo dedicato alla CPU & GPU rispettivamente al centro del profiler. Ciò consente allo sviluppatore di ottenere una rapida approssimazione se l'applicazione è associata a CPU o GPU.
>
> ![CPU Unity rispetto alla GPU](images/unity-profiler-cpu-gpu.png)

## <a name="cpu-performance-recommendations"></a>Raccomandazioni sulle prestazioni della CPU

Il contenuto riportato di seguito include procedure di prestazioni più approfondite, specialmente destinate C# a unity & Development.

#### <a name="cache-references"></a>Riferimenti alla cache

È consigliabile memorizzare nella cache i riferimenti a tutti i componenti rilevanti e GameObject in fase di inizializzazione. Ciò è dovuto al fatto che le chiamate di funzione ripetute come *[getComponent\<t > ()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* sono molto più dispendiose rispetto al costo di memoria per l'archiviazione di un puntatore. Questo vale anche per la [fotocamera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html)utilizzata regolarmente. La *fotocamera. Main* in realtà usa solo *[FindGameObjectsWithTag ()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* sotto il quale cerca in modo oneroso il grafico della scena per un oggetto della fotocamera con il tag *"MainCamera"* .

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

>[!NOTE] 
> Evitare GetComponent (String) <br/>
> Quando si utilizza *[GetComponent ()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* , sono presenti alcuni overload diversi. È importante usare sempre le implementazioni basate sui tipi e mai l'overload di ricerca basato su stringa. La ricerca per stringa nella scena è notevolmente più costosa rispetto alla ricerca per tipo. <br/>
> Buona Componente GetComponent (tipo Type) <br/>
> Buona T getComponent\<T > () <br/>
> Non valido Componente GetComponent (String) > <br/>

#### <a name="avoid-expensive-operations"></a>Evitare operazioni costose

1) **Evitare l'utilizzo di [LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)**

    Sebbene LINQ possa essere molto pulito e facile da leggere e scrivere, in genere richiede un maggior numero di calcoli e una maggiore allocazione di memoria rispetto alla scrittura manuale dell'algoritmo.

    ```CS
    // Example Code
    using System.Linq;

    List<int> data = new List<int>();
    data.Any(x => x > 10);

    var result = from x in data
                 where x > 10
                 select x;
    ```

2) **API Unity comuni**

    Alcune API Unity, sebbene utili, possono essere molto costose da eseguire. La maggior parte di questi comportano la ricerca dell'intero grafico della scena per un elenco corrispondente di GameObject. Queste operazioni possono in genere essere evitate memorizzando nella cache i riferimenti o implementando un componente di gestione per GameObject in questione per tenere traccia dei riferimenti in fase di esecuzione.

        GameObject.SendMessage()
        GameObject.BroadcastMessage()
        UnityEngine.Object.Find()
        UnityEngine.Object.FindWithTag()
        UnityEngine.Object.FindObjectOfType()
        UnityEngine.Object.FindObjectsOfType()
        UnityEngine.Object.FindGameObjectsWithTag()
        UnityEngine.Object.FindGameObjectsWithTag()

>[!NOTE]
> *[SendMessage ()](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* e *[BroadcastMessage ()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* devono essere eliminati a tutti i costi. Queste funzioni possono essere in ordine di 1.000 volte più lento rispetto alle chiamate di funzione dirette.

3) **Attenzione alla conversione boxing**

    La C# [conversione boxing](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing) è un concetto di base del linguaggio e del runtime. Si tratta del processo di wrapping di variabili tipizzate a valore quali Char, int, bool e così via in variabili tipizzate a cui si fa riferimento. Quando una variabile tipizzata come valore è "boxed", viene sottoposta a incapsulamento all'interno di un oggetto System. Object archiviato nell'heap gestito. In questo modo, la memoria viene allocata e alla fine, quando eliminata, deve essere elaborata dal Garbage Collector. Queste allocazioni e deallocazioni comportano un costo in termini di prestazioni e in molti scenari non sono necessari o possono essere facilmente sostituiti da un'alternativa meno costosa.

    Una delle forme più comuni di conversione boxing nello sviluppo è l'uso di [tipi di valore Nullable](https://docs.microsoft.com//dotnet/csharp/programming-guide/nullable-types/). È normale che si voglia essere in grado di restituire null per un tipo di valore in una funzione, specialmente quando l'operazione potrebbe non riuscire a ottenere il valore. Il potenziale problema con questo approccio è che l'allocazione è ora presente nell'heap e, di conseguenza, deve essere sottoposta a Garbage Collection in seguito.

    **Esempio di conversione boxing inC#**

    ```csharp
    // boolean value type is boxed into object boxedMyVar on the heap
    bool myVar = true;
    object boxedMyVar = myVar;
    ```

    **Esempio di conversione boxing problematica tramite tipi di valore Nullable**

    Questo codice illustra una classe particella fittizia che è possibile creare in un progetto Unity. Una chiamata a `TryGetSpeed()` provocherà l'allocazione di oggetti nell'heap che dovrà essere sottoposta a Garbage Collection in un secondo momento. Questo esempio è particolarmente problematico perché in una scena possono essere presenti oltre 1000 particelle, ciascuna delle quali viene richiesta la velocità corrente. In questo modo, vengono allocati 1.000 oggetti e, di conseguenza, deallocati tutti i frame che diminuiscono notevolmente le prestazioni. La riscrittura della funzione per la restituzione di un valore negativo, ad esempio-1, per indicare un errore evita questo problema e mantiene la memoria nello stack.

    ```csharp
        public class MyParticle
        {
            // Example of function returning nullable value type
            public int? TryGetSpeed()
            {
                // Returns current speed int value or null if fails
            }
        }
    ```

#### <a name="repeating-code-paths"></a>Ripetizione dei percorsi di codice

Tutte le funzioni di callback Unity ripetute (ad esempio Update) che vengono eseguiti più volte al secondo e/o frame devono essere scritti con molta attenzione. Tutte le operazioni dispendiose in questo caso avranno un notevole effetto sulle prestazioni.

1) **Funzioni di callback vuote**

    Sebbene il codice seguente possa sembrare innocente da lasciare nell'applicazione, soprattutto perché ogni script Unity Inizializza automaticamente con questo blocco di codice, queste richiamate vuote possono effettivamente diventare molto costose. Unity opera avanti e indietro su un limite di codice gestito/non gestito, tra il codice UnityEngine e il codice dell'applicazione. Il cambio di contesto di questo Bridge è piuttosto costoso anche se non è necessario eseguire alcuna operazione. Questa operazione diventa particolarmente problematica se l'app dispone di 100 GameObject con componenti con callback di Unity ripetuti vuoti.

    ```CS
    void Update()
    {
    }
    ```

>[!NOTE]
> Update () è la manifestazione più comune di questo problema di prestazioni, ma gli altri callback di Unity ripetuti come quelli riportati di seguito possono essere ugualmente non validi se non peggiori: FixedUpdate (), LateUpdate (), OnPostRender ", OnPreRender (), OnRenderImage () e così via. 

2) **Operazioni che favoriscono l'esecuzione una volta per ogni fotogramma**

    Le seguenti API Unity sono operazioni comuni per molte app olografiche. Sebbene non sia sempre possibile, i risultati di queste funzioni possono essere calcolati in genere una sola volta e i risultati vengono riutilizzati nell'applicazione per un determinato frame.

    a) in genere è consigliabile avere un servizio o una classe singleton dedicata per gestire lo sguardo Raycast nella scena e quindi riutilizzare questo risultato in tutti gli altri componenti della scena, anziché eseguire operazioni Raycast ripetute e essenzialmente identiche da ogni componente. Naturalmente, alcune applicazioni possono richiedere raycasts da origini diverse o da [LayerMasks](https://docs.unity3d.com/ScriptReference/LayerMask.html)diversi.

        UnityEngine.Physics.Raycast()
        UnityEngine.Physics.RaycastAll()

    b) evitare operazioni GetComponent () in richiamate Unity ripetute come Update () [memorizzando nella cache i riferimenti](#cache-references) in Start () o svegli ()

        UnityEngine.Object.GetComponent()

    c) è consigliabile creare un'istanza di tutti gli oggetti, se possibile, in fase di inizializzazione e usare il [pool di oggetti](#object-pooling) per riciclare e riutilizzare GameObject durante il runtime dell'applicazione

        UnityEngine.Object.Instantiate()

3) **Evitare le interfacce e i costrutti virtuali**

    Richiamando le chiamate di funzione tramite le interfacce e gli oggetti diretti oppure chiamando le funzioni virtuali spesso è molto più costoso rispetto all'uso di costrutti diretti o chiamate di funzioni dirette. Se la funzione o l'interfaccia virtuale non è necessaria, è necessario rimuoverla. Tuttavia, l'impatto sulle prestazioni di questi approcci è in genere degno di compromesso se l'uso semplifica la collaborazione di sviluppo, la leggibilità del codice e la gestibilità del codice.

    In genere, è consigliabile non contrassegnare campi e funzioni come virtuali, a meno che non esista una chiara previsione che questo membro debba essere sovrascritto. È necessario prestare particolare attenzione ai percorsi di codice ad alta frequenza che vengono chiamati più volte per fotogramma o anche una volta per fotogramma, ad esempio un metodo di `UpdateUI()`.

4) **Evitare il passaggio di struct in base al valore**

    Diversamente dalle classi, gli struct sono tipi di valore e, quando vengono passati direttamente a una funzione, il relativo contenuto viene copiato in un'istanza appena creata. Questa copia aggiunge costi CPU e memoria aggiuntiva nello stack. Per gli struct di piccole dimensioni, l'effetto è generalmente minimo e quindi accettabile. Tuttavia, per le funzioni richiamate ripetutamente ogni frame e funzioni che accettano struct di grandi dimensioni, se possibile, modificare la definizione della funzione in modo che venga passata per riferimento. [Altre informazioni sono disponibili qui](https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method)

#### <a name="miscellaneous"></a>Varie

1) **Fisica**

    a) generalmente, il modo più semplice per migliorare la fisica consiste nel limitare la quantità di tempo impiegato per la fisica o il numero di iterazioni al secondo. Naturalmente, questa operazione ridurrà la precisione della simulazione. Vedere [TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html) in Unity

    b) il tipo di Collider in Unity presenta caratteristiche di prestazioni notevolmente diverse. Nell'ordine seguente sono elencati i Collider più performanti per i Collider meno performanti da sinistra verso destra. È più importante evitare i conflitti di rete che sono sostanzialmente più costosi rispetto ai Collider primitivi.

        Sphere < Capsule < Box <<< Mesh (Convex) < Mesh (non-Convex)

    Vedere le [procedure consigliate per la fisica di Unity](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices) per altre informazioni

2) **Animazioni**

    Disabilitare le animazioni inattive disabilitando il componente animatore (la disabilitazione dell'oggetto gioco non avrà lo stesso effetto). Evitare modelli di progettazione in cui un animatore si trova in un ciclo che imposta un valore sullo stesso elemento. Si verifica un notevole sovraccarico per questa tecnica, senza alcun effetto sull'applicazione. [Altre informazioni sono disponibili qui.](https://docs.unity3d.com/Manual/MecanimPeformanceandOptimization.html)

3) **Algoritmi complessi**

    Se l'applicazione usa algoritmi complessi, ad esempio cinematica inversa, ricerca di percorsi e così via, cercare di trovare un approccio più semplice o modificare le impostazioni rilevanti per le relative prestazioni

## <a name="cpu-to-gpu-performance-recommendations"></a>Raccomandazioni sulle prestazioni da CPU a GPU

In genere, le prestazioni da CPU a GPU si verificano nelle **chiamate di estrazione** inviate alla scheda grafica. Per migliorare le prestazioni, le chiamate di progetto devono essere strategicamente **ridotte** o **b) ristrutturate** per ottenere risultati ottimali. Poiché le chiamate di progetto sono a elevato utilizzo di risorse, la loro riduzione ridurrà il lavoro complessivo richiesto. Inoltre, le modifiche di stato tra le chiamate di un progetto richiedono una procedura di convalida e conversione costose nel driver di grafica e, di conseguenza, la ristrutturazione delle chiamate di progetto dell'applicazione per limitare le modifiche di stato (ad esempio diversi materiali e così via possono migliorare le prestazioni.

Unity è un ottimo articolo che offre una panoramica e una panoramica delle chiamate di estrazione in batch per la piattaforma.
- [Batch di chiamate di progetto Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html)

#### <a name="single-pass-instanced-rendering"></a>Rendering con istanza a passaggio singolo

Il rendering a istanza singola di single pass in Unity consente la riduzione delle chiamate di progetto per ogni occhio a una chiamata di progetto con istanza. A causa della memorizzazione nella cache di coerenza tra due chiamate di progetto, è anche possibile migliorare le prestazioni della GPU.

Per abilitare questa funzionalità nel progetto Unity
1)  Aprire **le impostazioni di Player XR** (per **modificare** le impostazioni del **progetto** >  > **lettore** > **XR**)
2) Selezionare **istanza passaggio singolo** dal menu a discesa **metodo di rendering stereo** (casella di controllo**Virtual Reality supported** )

Per informazioni dettagliate su questo approccio di rendering, vedere gli articoli seguenti di Unity.
- [Come ottimizzare le prestazioni di AR e VR con il rendering stereo avanzato](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [Istanze Single Pass](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 

>[!NOTE]
> Si verifica un problema comune con il rendering con istanze di single pass se gli sviluppatori dispongono già di shader personalizzati non scritti per le istanze. Dopo l'abilitazione di questa funzionalità, gli sviluppatori possono notare che GameObject solo il rendering in un solo occhio. Ciò è dovuto al fatto che gli shader personalizzati associati non dispongono delle proprietà appropriate per le istanze.
>
> Per informazioni su come risolvere questo problema, vedere [rendering stereo a passaggio singolo per HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) da Unity

#### <a name="static-batching"></a>Batch statico

Unity è in grado di raggruppare molti oggetti statici per ridurre le chiamate di progetto alla GPU. Il batch statico funziona per la maggior parte degli oggetti [renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) in Unity che **1) condividono lo stesso materiale** e **2) sono tutti contrassegnati come *statici***  (selezionare un oggetto in Unity e fare clic sulla casella di controllo nella parte superiore destra del controllo). GameObject contrassegnato come *static* non può essere spostato nell'intero runtime dell'applicazione. Pertanto, il batch statico può essere difficile da usare in HoloLens, in cui virtualmente ogni oggetto deve essere inserito, spostato, ridimensionato e così via. Per gli auricolari immersivi, il batch statico può ridurre notevolmente le chiamate di disegni e migliorare le prestazioni.

Per ulteriori informazioni, vedere batch *statici* in [batch di chiamate di chiamata in Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) .

#### <a name="dynamic-batching"></a>Suddivisione in batch dinamica

Poiché è problematico contrassegnare gli oggetti come *statici* per lo sviluppo di HoloLens, l'invio in batch dinamici può essere un ottimo strumento per compensare questa funzionalità mancante. Naturalmente, può essere utile anche per gli auricolari immersivi. La suddivisione in batch dinamica in Unity può tuttavia essere difficile da abilitare perché GameObject deve **condividere lo stesso materiale** e **b) soddisfare un lungo elenco di altri criteri**.

Per l'elenco completo, leggere *batch dinamici* in [batch di chiamate di chiamata](https://docs.unity3d.com/Manual/DrawCallBatching.html) . In genere, GameObject non è più valido per l'invio in batch in modo dinamico perché i dati di mesh associati non possono essere più di 300 vertici.

#### <a name="other-techniques"></a>Altre tecniche

L'invio in batch può verificarsi solo se più GameObject sono in grado di condividere lo stesso materiale. Questa operazione viene in genere bloccata dalla necessità che GameObject disponga di una trama univoca per il rispettivo materiale. È comune combinare le trame in un'unica trama, un metodo noto come [Atlante delle trame](https://en.wikipedia.org/wiki/Texture_atlas).

Inoltre, in genere è preferibile combinare le mesh in una GameObject, ove possibile e ragionevole. A ogni renderer in Unity sarà associata una o più chiamate di disegni e l'invio di una mesh combinata sotto un renderer.

>[!NOTE]
> Se si modificano le proprietà di renderer. Material in fase di esecuzione, viene creata una copia del materiale e, di conseguenza, si interrompe il batch. Utilizzare renderer. sharedMaterial per modificare le proprietà del materiale condiviso tra GameObject.

## <a name="gpu-performance-recommendations"></a>Suggerimenti sulle prestazioni della GPU

Altre informazioni sull' [ottimizzazione del rendering della grafica in Unity](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)

### <a name="optimize-depth-buffer-sharing"></a>Ottimizzare la condivisione del buffer di profondità

È in genere consigliabile abilitare la **condivisione del buffer di profondità** nelle **impostazioni del lettore XR** per ottimizzare la [stabilità degli ologrammi](Hologram-stability.md). Quando si Abilita la riproiezione in fase avanzata basata sulla profondità con questa impostazione, tuttavia, è consigliabile selezionare il **formato di profondità a 16 bit** anziché il **formato di profondità a 24 bit**. I buffer di profondità a 16 bit ridurranno drasticamente la larghezza di banda e quindi il potere associato al traffico del buffer di profondità. Può trattarsi di una grande vittoria sia nella riduzione dell'energia che nel miglioramento delle prestazioni. Tuttavia, esistono due possibili risultati negativi utilizzando il *formato di profondità a 16 bit*.

**Combattimento Z**

La fedeltà ridotta della gamma di profondità rende più probabile che si verifichi un [conflitto z](https://en.wikipedia.org/wiki/Z-fighting) con 16 bit rispetto a 24 bit. Per evitare questi artefatti, modificare i piani di ritaglio vicini/lontani della [fotocamera Unity](https://docs.unity3d.com/Manual/class-Camera.html) per tenere conto della precisione più bassa. Per le applicazioni basate su HoloLens, un piano di ritaglio fino a 50m anziché l'impostazione predefinita di Unity 1000 è in genere in grado di eliminare qualsiasi combattimento z.

**Buffer stencil disabilitato**

Quando Unity crea una [trama di rendering con profondità a 16 bit](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html), non è stato creato alcun buffer dello stencil. Selezionando il formato di profondità a 24 bit, la documentazione per Unity, creerà un buffer z a 24 bit, oltre a un [buffer di stencil a 8 bit](https://docs.unity3d.com/Manual/SL-Stencil.html) (se 32 bit è applicabile nel dispositivo, che in genere è il caso, ad esempio HoloLens).

### <a name="avoid-full-screen-effects"></a>Evitare effetti a schermo intero

Le tecniche che operano sull'intero schermo possono essere piuttosto onerose perché il loro ordine di grandezza è costituito da milioni di operazioni ogni frame. È quindi consigliabile evitare [gli effetti di post-elaborazione](https://docs.unity3d.com/Manual/PostProcessingOverview.html) , ad esempio l'anti-aliasing, Bloom e altro ancora.

### <a name="optimal-lighting-settings"></a>Impostazioni di illuminazione ottimali

L' [illuminazione globale in tempo reale](https://docs.unity3d.com/Manual/GIIntro.html) in Unity può fornire risultati visivi oustanding, ma comporta calcoli di illuminazione piuttosto costosi. È consigliabile disabilitare l'illuminazione globale in tempo reale per ogni file di scena Unity tramite **finestra** > **rendering** > **impostazioni di illuminazione** > deselezionare l' **illuminazione globale in tempo reale**.

Si consiglia inoltre di disabilitare tutti i cast di Shadow, perché aggiungono anche costosi passaggi GPU a una scena Unity. Le ombreggiature possono essere disabilitate per luce ma possono anche essere controllate in maniera olistica tramite le impostazioni di qualità.

**Modificare** > **Impostazioni progetto**, quindi selezionare la categoria **qualità** > selezionare la **qualità bassa** per la piattaforma UWP. È anche possibile impostare la proprietà **Shadows** solo per **disabilitare le ombreggiature**.

### <a name="reduce-poly-count"></a>Ridurre il numero di Poly

Il numero di poligoni viene in genere ridotto da uno
1) Rimozione di oggetti da una scena
2) Decimazione di asset che riduce il numero di poligoni per una determinata mesh
3) Implementazione di un [sistema di livello di dettaglio (LOD)](https://docs.unity3d.com/Manual/LevelOfDetail.html) nell'applicazione che esegue il rendering di oggetti lontani con una versione meno poligonale della stessa geometria

### <a name="understanding-shaders-in-unity"></a>Informazioni sugli shader in Unity

Una semplice approssimazione per confrontare gli shader nelle prestazioni consiste nell'identificare il numero medio di operazioni eseguite in fase di esecuzione. Questa operazione può essere eseguita facilmente in Unity.

1) Selezionare l'asset shader o selezionare un materiale, quindi nell'angolo superiore destro della finestra di controllo, selezionare l'icona a forma di ingranaggio e quindi **"Seleziona shader"** .

    ![Seleziona shader in Unity](images/Select-shader-unity.png)
2) Con l'asset shader selezionato, fare clic sul pulsante **"Compila e Mostra codice"** nella finestra di controllo

    ![Compila il codice dello shader in Unity](images/compile-shader-code-unity.PNG)

3) Dopo la compilazione, cercare la sezione statistiche nei risultati con il numero di operazioni diverse per il vertice e la pixel shader (Nota: i pixel shader sono spesso denominati anche frammenti shader)

    ![Operazioni standard di Unity shader](images/unity-standard-shader-compilation.png)

#### <a name="optmize-pixel-shaders"></a>Pixel shader ottimizzazione

Esaminando i risultati statistici compilati utilizzando il metodo precedente, il [frammento shader](https://en.wikipedia.org/wiki/Shader#Pixel_shaders) eseguirà in genere più operazioni rispetto al [vertex shader](https://en.wikipedia.org/wiki/Shader#Vertex_shaders) in media. Il frammento shader, noto anche come pixel shader, viene eseguito per ogni pixel nell'output dello schermo, mentre il vertex shader viene eseguito solo per ogni vertice di tutte le mesh disegnate sullo schermo. 

Pertanto, non solo gli shader di frammento hanno più istruzioni rispetto ai vertex shader a causa di tutti i calcoli di illuminazione, i frammenti shader vengono quasi sempre eseguiti su un set di dati più grande. Se, ad esempio, l'output della schermata è un'immagine 2K per 2K, il frammento shader può essere eseguito 2000 * 2000 = 4 milioni volte. Se si esegue il rendering di due occhi, questo numero raddoppia perché sono presenti due schermate. Se un'applicazione di realtà mista ha più sessioni, effetti di post-elaborazione a schermo intero o il rendering di più mesh sullo stesso pixel, questo numero aumenterà in modo significativo. 

Pertanto, la riduzione del numero di operazioni nel frammento shader può in genere offrire un miglioramento delle prestazioni notevolmente maggiore rispetto alle ottimizzazioni nel vertex shader.

#### <a name="unity-standard-shader-alternatives"></a>Alternative shader standard Unity

Invece di usare un rendering fisico (PBR) o un altro shader di alta qualità, vedere uso di uno shader più efficiente e più economico. Il [Toolkit di realtà mista](https://github.com/Microsoft/MixedRealityToolkit-Unity) fornisce lo [shader standard MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) ottimizzato per i progetti di realtà mista.

Unity offre anche un'opzione di shader non illuminata, con vertice, diffusa e altre opzioni semplificate che risultano significativamente più veloci rispetto allo shader standard di Unity. Per informazioni più dettagliate, vedere [utilizzo e prestazioni degli shader incorporati](https://docs.unity3d.com/Manual/shader-Performance.html) .

#### <a name="shader-preloading"></a>Precaricamento shader

Usare il *precaricamento dello shader* e altri trucchi per ottimizzare il [tempo di caricamento dello shader](https://docs.unity3d.com/Manual/OptimizingShaderLoadTime.html). In particolare, il precaricamento dello shader significa che non verranno visualizzati intoppi a causa della compilazione dello shader di Runtime.

### <a name="limit-overdraw"></a>Limite di sovralievo

In Unity, è possibile visualizzare il sovraprogetto per la scena, impostando il [**menu modalità**](https://docs.unity3d.com/Manual/ViewModes.html) di visualizzazione nell'angolo superiore sinistro della **visualizzazione scena** e selezionando **sovradisegnato**.

In genere, il sovraprogetto può essere mitigato eliminando gli oggetti in anticipo prima che vengano inviati alla GPU. Unity fornisce informazioni dettagliate sull'implementazione dell' [abbattimento di occlusione](https://docs.unity3d.com/Manual/OcclusionCulling.html) per il motore.

## <a name="memory-recommendations"></a>Consigli sulla memoria

Un'allocazione eccessiva della memoria & operazioni di deallocazione possono avere effetti negativi sull'applicazione olografica, con prestazioni incoerenti, frame bloccati e altro comportamento dannoso. È particolarmente importante comprendere le considerazioni sulla memoria durante lo sviluppo in Unity, perché la gestione della memoria è controllata dal Garbage Collector.

#### <a name="garbage-collection"></a>Garbage Collection

Le app olografiche elimineranno l'elaborazione del tempo di calcolo nel Garbage Collector (GC) quando il GC viene attivato per analizzare gli oggetti che non sono più nell'ambito durante l'esecuzione e la memoria deve essere rilasciata in modo da poter essere resi disponibili per il riutilizzo. Le allocazioni e le deallocazioni costanti richiedono in genere che l'Garbage Collector venga eseguita con maggiore frequenza, in modo da compromettere le prestazioni e l'esperienza utente.

Unity ha fornito una pagina eccellente che illustra in dettaglio il funzionamento del Garbage Collector e suggerimenti per scrivere codice più efficiente per quanto riguarda la gestione della memoria.
- [Ottimizzazione Garbage Collection nei Giochi Unity](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)

Una delle procedure più comuni che porta a un numero eccessivo di Garbage Collection non è la memorizzazione nella cache dei riferimenti a componenti e classi nello sviluppo di Unity. Tutti i riferimenti devono essere acquisiti durante l'avvio () o svegli () e riusati in funzioni successive, ad esempio Update () o LateUpdate ().

Altri suggerimenti rapidi:
- Usare la classe [StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) C# per compilare in modo dinamico stringhe complesse in fase di esecuzione
- Rimuovere le chiamate a debug. log () quando non sono più necessarie perché sono ancora in esecuzione in tutte le versioni di compilazione di un'app
- Se l'app olografica richiede in genere molta memoria, provare a chiamare [ _**System. GC. Collect ()**_ ](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2) durante il caricamento di fasi, ad esempio quando si presenta una schermata di caricamento o di transizione

#### <a name="object-pooling"></a>Pool di oggetti

Il pool di oggetti è una tecnica comune per ridurre il costo delle allocazioni continue & le deallocazioni di oggetti. Questa operazione viene eseguita allocando un pool di grandi dimensioni di oggetti identici e riutilizzando le istanze disponibili inattive da questo pool invece di generare ed eliminare costantemente gli oggetti nel tempo. I pool di oggetti sono ottimi per i componenti riutilizzabili con durata variabile durante un'app.

- [Esercitazione sul pool di oggetti in Unity](https://unity3d.com/learn/tutorials/topics/scripting/object-pooling) 

## <a name="startup-performance"></a>Prestazioni di avvio

È consigliabile avviare l'app con una scena più piccola, quindi usare *[SceneManager. LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* per caricare il resto della scena. Ciò consente all'app di ottenere uno stato interattivo il più velocemente possibile. Tenere presente che potrebbe essere presente un picco di CPU elevato mentre è in corso l'attivazione della nuova scena e che qualsiasi contenuto sottoposto a rendering potrebbe balbettare o bloccarsi. Per ovviare a questo problema, è possibile impostare la proprietà AsyncOperation. allowSceneActivation su false sulla scena caricata, attendere il caricamento della scena, deselezionare la schermata su nero e quindi impostare di nuovo su true per completare l'attivazione della scena.

Tenere presente che, durante il caricamento della scena di avvio, la schermata iniziale olografica verrà visualizzata all'utente.

## <a name="see-also"></a>Vedi anche
- [Ottimizzazione del rendering della grafica nei Giochi Unity](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games?playlist=44069)
- [Ottimizzazione Garbage Collection nei Giochi Unity](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)
- [Procedure consigliate per la fisica [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)
- [Ottimizzazione degli script [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)

---
title: Ottenere informazioni sulle prestazioni per realtà mista
description: Gli argomenti e informazioni dettagliate avanzate sull'ottimizzazione delle prestazioni per le App per realtà mista Windows
author: Troy-Ferrell
ms.author: trferrel
ms.date: 3/26/2019
ms.topic: article
keywords: Windows misti realtà, realtà mista, realtà virtuale, VR, MR, prestazioni, ottimizzazione, CPU, GPU
ms.openlocfilehash: ce59f9023c21dc7c981a2bb97d9fbd0c57622dbf
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603291"
---
# <a name="understanding-performance-for-mixed-reality"></a>Ottenere informazioni sulle prestazioni per realtà mista

Questo articolo costituisce un'introduzione al razionalizzazione l'importanza delle prestazioni per l'app di realtà mista.  Esperienza dell'utente può peggiorare notevolmente se l'applicazione non viene eseguito con frequenza fotogrammi ottimale. Ologrammi apparirà instabile e head rilevamento dell'ambiente non saranno accurato comporta un'esperienza insufficiente per l'utente. In effetti, le prestazioni devono essere considerata come una funzionalità di prima classe per lo sviluppo della realtà mista e non un stabilizzazione, la fine del ciclo di attività.

Per la revisione, i valori di frequenza dei fotogrammi ad alte prestazioni per ogni piattaforma di destinazione sono elencati di seguito.

| Piattaforma | Frequenza dei fotogrammi destinazione |
|----------|-------------------|
| [HoloLens](hololens-hardware-details.md) | 60 FPS |
| [I PC Windows Mixed Reality Ultra](immersive-headset-hardware-details.md) | 90 FPS |
| [Windows PCs realtà mista](immersive-headset-hardware-details.md) | 60 FPS |

Il framework seguente fornisce un quadro generale per le procedure consigliate e la visione verso raggiungendo frequenze dei fotogrammi di destinazione. Per analizzare ulteriormente i dettagli, è consigliabile leggere il [raccomandazioni sulle prestazioni per l'articolo di Unity](performance-recommendations-for-unity.md). In particolare, questo articolo correlato illustra come misurare la frequenza dei fotogrammi le app per realtà mista di Windows di Unity, nonché passaggi da eseguire nell'ambiente di Unity per migliorare le prestazioni.

## <a name="understanding-performance-bottlenecks"></a>La comprensione dei colli di bottiglia delle prestazioni

Se l'app ha una frequenza dei fotogrammi con prestazioni insoddisfacenti, il primo passaggio è analizzare e comprendere l'applicazione è con calcoli complessi. Esistono due processori primari responsabile per il lavoro eseguire il rendering della scena: CPU e GPU. Ognuno di questi due componenti gestiscono diverse operazioni e le fasi dell'app per realtà mista. Ci sono tre posizioni principali in cui potrebbero verificarsi dei colli di bottiglia. 

1. **Thread di App - CPU** -questo thread è responsabile per la logica dell'app. Ciò include l'elaborazione di input, animazioni, fisica e altre app per la logica/stato
2. **Eseguire il rendering Thread - CPU alla GPU** -questo thread è responsabile dell'invio di chiamate di disegno nella GPU. Quando l'app desidera eseguire il rendering di un oggetto, ad esempio un cubo o un modello, questo thread invia una richiesta per la GPU, che ha un'architettura ottimizzata per il rendering, per eseguire queste operazioni.
3. **GPU** - 
    questo processore gestisce in genere la pipeline di grafica dell'applicazione per trasformare i dati 3D (modelli, le trame e così via) in pixel e infine producono un'immagine 2D da inviare alla schermata del dispositivo.

![Durata di un Frame](images/lifetime-of-a-frame.png)

In genere, le applicazioni di HoloLens saranno GPU delimitato. Tuttavia, ciò non ha valore true in ogni applicazione e pertanto è consigliabile usare gli strumenti e tecniche di seguito per ottenere verificate per l'app specifica.

## <a name="how-to-analyze-your-application"></a>Come analizzare l'applicazione

Sono disponibili numerosi strumenti che consentono gli sviluppatori a comprendere il profilo delle prestazioni dell'applicazione di realtà mista. Questi ti permetterà di entrambi destinazione in cui si dispone di colli di bottiglia e come essi vengono manifesta autonomamente per eseguirne il debug.

Si tratta di un elenco di strumenti più diffusi e potenti per ottenere informazioni di profilatura approfondite per l'applicazione.
- [Analizzatori di prestazioni della grafica di Intel](https://software.intel.com/gpa)
- [Debugger grafica di Visual Studio](https://docs.microsoft.com/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics?view=vs-2017)
- [Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)
- [Debugger di Unity Frame](https://docs.unity3d.com/Manual/FrameDebugger.html)

### <a name="how-to-profile-in-any-environment"></a>Come eseguire la profilatura in qualsiasi ambiente

Si verifica un semplice test per determinare rapidamente che se è probabile che con GPU o CPU delimitato nell'applicazione. Se si diminuisce la risoluzione dell'output della destinazione di rendering, sono presenti meno pixel per calcolare e di conseguenza, minore di lavoro GPU deve eseguire per il rendering di un'immagine. Viewport ridimensionamento (ridimensionamento di risoluzione dinamica) è la pratica per il rendering di immagini al valore più piccolo della destinazione di rendering quindi possibile visualizzare il dispositivo di output. Il dispositivo verrà up-sample dal più piccolo set di pixel per visualizzare l'immagine finale.

Dopo aver diminuendo la risoluzione per il rendering, se:
1) Frequenza dei fotogrammi dell'applicazione **aumenta**, quindi è probabile che **delimitato GPU**
1) Frequenza dei fotogrammi dell'applicazione **invariato**, quindi è probabile che **della CPU limitato**

>[!NOTE]
>Unity offre la possibilità di modificare facilmente la risoluzione di destinazione di rendering dell'applicazione in fase di esecuzione tramite il *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* proprietà. L'immagine finale visualizzata sul dispositivo ha una risoluzione fissa. La piattaforma campionerà le risoluzione più bassa per compilare un'immagine con risoluzione superiore per il rendering a su schermi di output. 
>
>```CS
>UnityEngine.XR.XRSettings.renderScale = 0.7f;
>```

## <a name="how-to-improve-your-application"></a>Come migliorare l'applicazione

### <a name="cpu-performance-recommendations"></a>Raccomandazioni per le prestazioni della CPU

In generale, la maggior parte delle operazioni in un'applicazione di realtà mista sulla CPU comporta eseguendo "simulazione" della scena e l'elaborazione della logica di approfonditi delle applicazioni univoco. Di conseguenza, le aree seguenti sono generalmente destinate per l'ottimizzazione.

- Animazioni
- Semplificare la fisica
- Allocazioni di memoria
- Algoritmi complessi (ad es. cinematica inversa, percorso di ricerca)

### <a name="gpu-performance-recommendations"></a>Raccomandazioni sulle prestazioni di GPU

#### <a name="understanding-bandwidth-vs-fill-rate"></a>Velocità di riempimento di comprensione della larghezza di banda Visual Studio
Durante il rendering di un frame nella GPU, un'applicazione è in genere vincolata dalla velocità di riempimento o la larghezza di banda di memoria.

- **Larghezza di banda di memoria** indica la frequenza delle letture e scritture GPU è possibile eseguire dalla memoria
    - Per identificare le limitazioni della larghezza di banda, ridurre la qualità della trama e controllare se la frequenza dei fotogrammi migliorate.
    - In Unity, questa operazione può essere eseguita modificando **trama qualità** nelle **modificare** > **impostazioni progetto**  >   **[ Impostazioni relative alla qualità](https://docs.unity3d.com/Manual/class-QualitySettings.html)**.
- **Velocità di riempimento** fa riferimento alla velocità effettiva di pixel viene eseguito il rendering che possono essere disegnate al secondo dalla GPU.
    - Per identificare le limitazioni di velocità di riempimento, ridurre la risoluzione dello schermo e controllare se la frequenza dei fotogrammi migliorate. 
    - In Unity, questa operazione può essere eseguita tramite il *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* proprietà

Larghezza di banda di memoria implica in genere le ottimizzazioni a uno
1) ridurre le risoluzioni di trama
2) usare meno trame (ad es. e così via con riflessione speculare, Normals)

Velocità di riempimento è mirata principalmente alla riduzione del numero di operazioni che devono essere calcolati per un pixel sottoposto a rendering finale. Esempi di questo genere rientrano in riduzione
1) numero di oggetti di rendering/processo
2) numero di operazioni per shader
3) numero di fasi GPU al risultato finale (geometry shader, post-elaborazione effetti e così via)
4) numero di pixel per il rendering (ad es. risoluzione dello schermo)

#### <a name="reduce-poly-count"></a>Ridurre il numero di poligono
Poligono superiore Conta risultati di ulteriori operazioni per la GPU e riducendo il numero di poligoni in scena ridurrà la quantità di tempo per eseguire il rendering che la geometria. Esistono altri fattori interessati anche ombreggiatura la geometria che può ancora essere costosa, ma count poligono è la metrica di base per determinare il costo una scena sarà per il rendering.

#### <a name="limit-overdraw"></a>Limite di caricamento

Alto estenda si verifica quando più oggetti sono sottoposto a rendering ma non restituiti alla schermata di come sono nascosti da un altro, in genere più da vicino, occluding oggetto. Si supponga esaminando una parete che aveva più le chat e geometry dietro di essa. Sarebbe elaborati tutti la geometria per il rendering, ma solo la parete opaca informazione che invece deve essere sottoposto a rendering come lo occludes la visualizzazione di tutti gli altri contenuti. Ciò comporta operazioni inutili che non sono necessari per la visualizzazione corrente.

#### <a name="shaders"></a>Shader

Gli shader sono piccoli programmi eseguiti sulla GPU e determinano in genere due operazioni importanti per il rendering:
1) vertici dell'oggetto che devono essere disegnati sullo schermo e si trovino nello spazio dello schermo (ad es. Vertex shader)
    - Vertex shader viene in genere eseguito per ogni vertice per ogni GameObject
2) che cosa colorare i pixel (ad es. il Pixel shader)
    - Il Pixel shader viene eseguito per ogni pixel per la trama viene eseguito il rendering per il dispositivo presenta

In genere gli shader eseguono numerose trasformazioni e calcoli di illuminazione. Anche se i modelli di illuminazione complesse, ombreggiature e altre operazioni possono generare risultati fantastici, sono inoltre dotati di un prezzo. Riduzione del numero di operazioni calcolate di shader possono ridurre notevolmente il lavoro complessivo necessario per essere eseguita da una GPU per ogni fotogramma.

##### <a name="shader-coding-recommendations"></a>Shader suggerimenti di codifica

- Usare il filtraggio bilineare quando possibile
- Ridisporre le espressioni per l'uso di funzioni intrinseche MAD scopo un multiply e un'operazione di aggiunta allo stesso tempo
- Precalcolare quanto più possibile sulla CPU e passare come costanti per il materiale
- **Ottimizza per lo spostamento delle operazioni dal pixel shader al vertex shader**
    - In genere il numero di vertici << & di pixel (ad es. 720p = = 921.600 pixel, con risoluzione 1080p e = = 2.073.600 pixel e così via)

#### <a name="remove-gpu-stages"></a>Rimuovere fasi GPU
Gli effetti di post-elaborazione possono essere molto costosa e inibire in genere la velocità di riempimento dell'applicazione. Ciò include anche le tecniche di anti-aliasing, ad esempio MSAA. Su HoloLens, è consigliabile evitare interamente queste tecniche. Inoltre, è consigliabile evitare fasi dello shader aggiuntive, ad esempio compute shader, hull e geometry quando possibile.

## <a name="memory-recommendations"></a>Consigli sulla memoria
Operazioni di allocazione e deallocazione di memoria eccessiva possono avere effetti negativi sull'applicazione holographic causando prestazioni incoerenti, frame bloccati e altri comportamenti dannosi. È particolarmente importante comprendere considerazioni sulla memoria quando si sviluppa in Unity, poiché la gestione della memoria è controllata dal garbage collector.

#### <a name="object-pooling"></a>Pool di oggetti

Il pool degli oggetti è una tecnica comune per ridurre il costo delle allocazioni di continuo e le deallocazioni di oggetti. Questa operazione viene eseguita, allocando un ampio pool di oggetti identici e riutilizzo di istanze inattive, disponibile da questo pool anziché continuamente durante la generazione e l'eliminazione definitiva di oggetti nel corso del tempo. Pool di oggetti sono ideali per i componenti riutilizzabili che includono la durata delle variabili durante un'app.

## <a name="see-also"></a>Vedere anche
- [Raccomandazioni sulle prestazioni per Unity](performance-recommendations-for-unity.md)
- [Impostazioni consigliate per Unity](recommended-settings-for-unity.md)

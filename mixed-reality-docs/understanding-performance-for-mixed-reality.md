---
title: Informazioni sulle prestazioni per la realtà mista
description: Argomenti avanzati e dettagli sull'ottimizzazione delle prestazioni per le app di realtà mista di Windows
author: Troy-Ferrell
ms.author: trferrel
ms.date: 3/26/2019
ms.topic: article
keywords: Realtà mista di Windows, realtà mista, realtà virtuale, VR, MR, prestazioni, ottimizzazione, CPU, GPU
ms.openlocfilehash: 287b95363acff00ab7a0407475e0a419fc076611
ms.sourcegitcommit: 184227dc591ca2791f523d520555730ba1e95b5c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "79479574"
---
# <a name="understanding-performance-for-mixed-reality"></a>Informazioni sulle prestazioni per la realtà mista

Questo articolo è un'introduzione alla comprensione del significato delle prestazioni per l'app per realtà mista.  L'esperienza utente può essere notevolmente degradata se l'applicazione non viene eseguita con una frequenza di fotogrammi ottimale. Gli ologrammi compariranno in modo instabile e il rilevamento delle intestazioni dell'ambiente non sarà accurato, causando una scarsa esperienza per l'utente. Le prestazioni devono essere considerate una funzionalità di prima classe per lo sviluppo di realtà mista e non per le attività polacche.

Di seguito sono elencati i valori di framerate a prestazioni per ogni piattaforma di destinazione.

| Platform | Frequenza fotogrammi di destinazione |
|----------|-------------------|
| [HoloLens](hololens-hardware-details.md) | 60 FPS |
| [Windows reality Ultra PC](immersive-headset-hardware-details.md) | 90 FPS |
| [PC con realtà mista di Windows](immersive-headset-hardware-details.md) | 60 FPS |

Il Framework seguente descrive le procedure consigliate per raggiungere le frequenze dei fotogrammi di destinazione. Se si sviluppa in Unity, è consigliabile leggere l' [articolo raccomandazioni per le prestazioni per Unity](performance-recommendations-for-unity.md) per suggerimenti sulla misurazione e sul miglioramento della frequenza framerate nell'ambiente Unity.

## <a name="understanding-performance-bottlenecks"></a>Informazioni sui colli di bottiglia delle prestazioni

Se l'app ha un framerate sottoposto a sottoesecuzione, il primo passaggio consiste nell'analizzare e comprendere il modo in cui l'applicazione è a elevato utilizzo di calcolo. Ci sono due processori primari responsabili del lavoro per il rendering della scena: CPU e GPU. Ognuno di questi elementi gestisce aspetti diversi dell'app per realtà mista. I colli di bottiglia possono verificarsi in tre posizioni principali: 

1. **Thread-CPU dell'app** : questo thread è responsabile della logica dell'app. Sono inclusi l'elaborazione di input, animazioni, fisica e altre logiche dell'app.
2. **Render thread-CPU alla GPU** : questo thread è responsabile dell'invio delle chiamate di disegnare alla GPU. Quando l'app vuole eseguire il rendering di un oggetto, ad esempio un cubo o un modello, questo thread invia una richiesta alla GPU per eseguire queste operazioni.
3. **GPU** : questo processore gestisce più di frequente la pipeline grafica dell'applicazione per trasformare i dati 3D (modelli, trame e così via) in pixel. Produce infine un'immagine 2D da inviare alla schermata del dispositivo.

![Durata di un frame](images/lifetime-of-a-frame.png)

In genere, le applicazioni HoloLens saranno vincolate alla GPU, ma non sempre. Usare gli strumenti e le tecniche seguenti per capire dove si trova un collo di bottiglia per l'app specifica.

## <a name="how-to-analyze-your-application"></a>Come analizzare l'applicazione

Sono disponibili molti strumenti che consentono di comprendere il profilo delle prestazioni dell'applicazione per realtà mista. Che consentono di trovare la posizione e il motivo per cui si hanno colli di bottiglia, in modo da poterli risolvere.

Di seguito sono riportati alcuni strumenti comuni per ottenere informazioni di profilatura approfondite per l'applicazione:
- [Analizzatori prestazioni grafica Intel](https://software.intel.com/gpa)
- [Debugger grafica di Visual Studio](https://docs.microsoft.com/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics?view=vs-2017)
- [Profiler Unity](https://docs.unity3d.com/Manual/Profiler.html)
- [Debugger frame Unity](https://docs.unity3d.com/Manual/FrameDebugger.html)

### <a name="how-to-profile-in-any-environment"></a>Come profilare in qualsiasi ambiente

Un modo per determinare se l'utente è associato alla GPU o associato alla CPU nell'applicazione consiste nel ridurre la risoluzione dell'output della destinazione di rendering. Riducendo il numero di pixel da calcolare, il carico della GPU verrà ridotto. Il rendering del dispositivo verrà eseguito su una trama più piccola, quindi su-Sample per visualizzare l'immagine finale.

Dopo la riduzione della risoluzione del rendering, se:
1) Il framerate dell'applicazione **aumenta**, quindi è probabile che la **GPU sia associata**
1) Framerate dell'applicazione senza **modifiche**, è probabile che il **limite della CPU**

>[!NOTE]
>Unity offre la possibilità di modificare facilmente la risoluzione della destinazione di rendering dell'applicazione in fase di esecuzione tramite la proprietà *[XRSettings. renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* . La risoluzione dell'immagine finale visualizzata sul dispositivo è fissa. La piattaforma campiona l'output di risoluzione inferiore per creare un'immagine di risoluzione superiore per il rendering delle visualizzazioni. 
>
>```CS
>UnityEngine.XR.XRSettings.renderScale = 0.7f;
>```

## <a name="how-to-improve-your-application"></a>Come migliorare l'applicazione

### <a name="cpu-performance-recommendations"></a>Raccomandazioni sulle prestazioni della CPU

In genere, la maggior parte del lavoro in un'applicazione di realtà mista sulla CPU comporta l'esecuzione della "simulazione" della scena e l'elaborazione della logica dell'applicazione. Le aree seguenti sono in genere destinate all'ottimizzazione:

- Animazioni
- Fisica
- Allocazioni di memoria
- Algoritmi complessi, ad esempio cinematica inversa, ricerca di percorsi

### <a name="gpu-performance-recommendations"></a>Suggerimenti sulle prestazioni della GPU

#### <a name="understanding-bandwidth-vs-fill-rate"></a>Informazioni sulla larghezza di banda e sulla velocità di riempimento
Quando si esegue il rendering di un frame sulla GPU, un'applicazione è in genere associata alla larghezza di banda della memoria o alla velocità di riempimento.

- La **larghezza di banda della memoria** è la velocità di lettura e scrittura che la GPU può eseguire dalla memoria
    - Per identificare le limitazioni della larghezza di banda, ridurre la qualità della trama e verificare se il framerate è migliorato.
    - In Unity, questa operazione può essere eseguita modificando la **qualità della trama** in **modifica** > **Impostazioni progetto** >  **[impostazioni qualità](https://docs.unity3d.com/Manual/class-QualitySettings.html)** .
- La **velocità di riempimento** si riferisce ai pixel che possono essere disegnati al secondo dalla GPU.
    - Per identificare le limitazioni della velocità di riempimento, ridurre la risoluzione dello schermo e verificare se il framerate è migliorato. 
    - In Unity, questa operazione può essere eseguita tramite la proprietà *[XRSettings. renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)*

La larghezza di banda della memoria comporta in genere ottimizzazioni per:
1) Riduzione delle risoluzioni di trama
2) Usare meno trame (normali, speculari e così via)

La velocità di riempimento si concentra sulla riduzione del numero di operazioni che devono essere calcolate per un pixel finale sottoposto a rendering. Ciò include la riduzione di:
1) Numero di oggetti di cui eseguire il rendering o il processo
2) Numero di operazioni per shader
3) Numero di fasi GPU fino al risultato finale (Geometry shader, effetti di post-elaborazione e così via)
4) Numero di pixel di cui eseguire il rendering (risoluzione dello schermo)

#### <a name="reduce-polygon-count"></a>Ridurre il numero di poligoni

I conteggi di poligoni più elevati generano più operazioni per la GPU; [riducendo il numero di poligoni](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets) nella scena si riduce il tempo di rendering. Ci sono altri fattori che interessano l'ombreggiatura della geometria che può essere costosa, ma il conteggio dei poligoni è la metrica più semplice per determinare il costo di rendering di una scena.

#### <a name="limit-overdraw"></a>Limite di sovralievo

Un elevato livello di sovradisegnazione si verifica quando viene eseguito il rendering di più oggetti ma non vengono visualizzati sullo schermo perché sono nascosti da un oggetto occlusione. Si supponga di esaminare un muro con oggetti sottostanti. Tutta la geometria verrebbe elaborata per il rendering, ma è necessario eseguire il rendering solo del muro opaco. Ciò comporta operazioni non necessarie.

#### <a name="shaders"></a>Shader

Gli shader sono piccoli programmi eseguiti sulla GPU ed eseguono due passaggi importanti nel rendering:
1) Determinazione dei vertici da disegnare e della posizione in cui si trovano nello spazio dello schermo (Vertex shader)
    - Il vertex shader viene in genere eseguito per ogni vertice per ogni mesh.
2) Determinazione del colore di ogni pixel (pixel shader)
    - Il pixel shader viene eseguito per ogni pixel sottoposto a rendering dalla geometria alla trama sottoposta a rendering.

In genere, gli shader eseguono numerose trasformazioni e calcoli di illuminazione. Sebbene i modelli di illuminazione complessi, le ombre e altre operazioni possano generare risultati eccezionali, presentano anche un prezzo. La riduzione del numero di operazioni calcolate negli shader può ridurre notevolmente il lavoro necessario per la GPU per fotogramma.

##### <a name="shader-coding-recommendations"></a>Suggerimenti sulla codifica dello shader

- Usare il filtro bilineare, laddove possibile
- Ridisporre le espressioni in modo da usare funzioni intrinseche folli per eseguire un'operazione di moltiplicazione e un aggiunta allo stesso tempo
- Precalcolare quanto più possibile sulla CPU e passare come costanti al materiale
- **Preferire le operazioni di trasferimento dal pixel shader al vertex shader**
    - In genere, il numero di vertici è molto più piccolo del numero di pixel (720p è 921.600 pixel, 1080p è 2.073.600 pixel e così via)

#### <a name="remove-gpu-stages"></a>Rimuovi fasi GPU

Gli effetti di post-elaborazione possono essere molto costosi e aumentare la velocità di riempimento dell'applicazione. Sono incluse tecniche di anti-aliasing, ad esempio MSAA. In HoloLens è consigliabile evitare completamente queste tecniche, oltre ad altre fasi dello shader, ad esempio geometria, scafo e compute shader.

## <a name="memory-recommendations"></a>Consigli sulla memoria

Un numero eccessivo di operazioni di allocazione e deallocazione della memoria può comportare prestazioni incoerenti, frame bloccati e altro comportamento dannoso. È particolarmente importante comprendere le considerazioni sulla memoria durante lo sviluppo in Unity, perché la gestione della memoria è controllata dal Garbage Collector.

#### <a name="object-pooling"></a>Pool di oggetti

Il pool di oggetti è una tecnica comune per ridurre i costi delle allocazioni e delle deallocazioni continue degli oggetti. Questa operazione viene eseguita allocando un pool di grandi dimensioni di oggetti identici e riutilizzando le istanze disponibili inattive da questo pool invece di generare ed eliminare costantemente gli oggetti nel tempo. I pool di oggetti sono ottimi per i componenti riutilizzabili con durata variabile durante un'app.

## <a name="see-also"></a>Vedere anche
- [Consigli sulle prestazioni per Unity](performance-recommendations-for-unity.md)
- [Impostazioni consigliate per Unity](recommended-settings-for-unity.md)
- [Ottimizzare i modelli 3D](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets)
- [Procedure consigliate per la conversione e l'ottimizzazione di modelli 3D in tempo reale](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/best-practices)


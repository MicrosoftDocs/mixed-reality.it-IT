---
title: Informazioni sulle prestazioni per la realtà mista
description: Argomenti avanzati e dettagli sull'ottimizzazione delle prestazioni per le app di realtà mista di Windows
author: Troy-Ferrell
ms.author: trferrel
ms.date: 3/26/2019
ms.topic: article
keywords: Realtà mista di Windows, realtà mista, realtà virtuale, VR, MR, prestazioni, ottimizzazione, CPU, GPU
ms.openlocfilehash: ce59f9023c21dc7c981a2bb97d9fbd0c57622dbf
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548832"
---
# <a name="understanding-performance-for-mixed-reality"></a>Informazioni sulle prestazioni per la realtà mista

Questo articolo è un'introduzione alla razionalizzazione dell'importanza delle prestazioni per l'app per realtà mista.  L'esperienza utente può essere notevolmente degradata se l'applicazione non viene eseguita con una frequenza di fotogrammi ottimale. Gli ologrammi appariranno instabile e il rilevamento delle intestazioni dell'ambiente non sarà accurato, causando una scarsa esperienza per l'utente. Infatti, le prestazioni devono essere considerate come una funzionalità di prima classe per lo sviluppo di realtà mista e non una stabilizzazione, fine dell'attività del ciclo.

Per la revisione, i valori di framerate per ogni piattaforma di destinazione sono elencati di seguito.

| Piattaforma | Frequenza fotogrammi di destinazione |
|----------|-------------------|
| [HoloLens](hololens-hardware-details.md) | 60 FPS |
| [Windows reality Ultra PC](immersive-headset-hardware-details.md) | 90 FPS |
| [PC con realtà mista di Windows](immersive-headset-hardware-details.md) | 60 FPS |

Il Framework seguente fornisce un contorno generale per le procedure consigliate e le comprensioni per raggiungere le frequenze dei fotogrammi di destinazione. Per approfondire i dettagli, provare a leggere l' [articolo raccomandazioni sulle prestazioni per Unity](performance-recommendations-for-unity.md). In particolare, questo articolo correlato descrive come misurare il framerate nell'app per la realtà mista di Windows Unity e i passaggi da eseguire nell'ambiente Unity per migliorare le prestazioni.

## <a name="understanding-performance-bottlenecks"></a>Informazioni sui colli di bottiglia delle prestazioni

Se l'app ha un framerate sottoposto a sottoesecuzione, il primo passaggio consiste nell'analizzare e comprendere il modo in cui l'applicazione è a elevato utilizzo di calcolo. Ci sono due processori primari responsabili del lavoro per il rendering della scena: CPU e GPU. Ognuno di questi due componenti gestisce diverse operazioni e fasi dell'app per realtà mista. I colli di bottiglia possono verificarsi in tre punti chiave. 

1. **Thread-CPU dell'app** : questo thread è responsabile della logica dell'app. Sono inclusi l'elaborazione di input, animazioni, fisica e altro stato/logica dell'app
2. **Render thread-CPU alla GPU** : questo thread è responsabile dell'invio delle chiamate di disegnare alla GPU. Quando l'app vuole eseguire il rendering di un oggetto, ad esempio un cubo o un modello, questo thread invia una richiesta alla GPU, che ha un'architettura ottimizzata per il rendering, per eseguire queste operazioni.
3. **GPU** - 
    Questo processore gestisce più di frequente la pipeline grafica dell'applicazione per trasformare i dati 3D (modelli, trame e così via) in pixel e infine produrre un'immagine 2D da inviare alla schermata del dispositivo.

![Durata di un frame](images/lifetime-of-a-frame.png)

In genere, le applicazioni HoloLens saranno delimitate da GPU. Tuttavia, ciò non è valido in ogni applicazione ed è quindi consigliabile usare gli strumenti & tecniche seguenti per ottenere una verità per la propria app.

## <a name="how-to-analyze-your-application"></a>Come analizzare l'applicazione

Sono disponibili molti strumenti che consentono agli sviluppatori di comprendere il profilo delle prestazioni dell'applicazione per realtà mista. Queste consentiranno di raggiungere entrambi i colli di bottiglia e il modo in cui si manifestano per eseguirne il debug.

Questo è un elenco di strumenti diffusi e potenti per ottenere informazioni di profilatura approfondite per l'applicazione.
- [Analizzatori prestazioni grafica Intel](https://software.intel.com/gpa)
- [Debugger grafica di Visual Studio](https://docs.microsoft.com/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics?view=vs-2017)
- [Profiler Unity](https://docs.unity3d.com/Manual/Profiler.html)
- [Debugger frame Unity](https://docs.unity3d.com/Manual/FrameDebugger.html)

### <a name="how-to-profile-in-any-environment"></a>Come profilare in qualsiasi ambiente

È disponibile un semplice test per determinare rapidamente se è probabile che la GPU sia limitata o associata alla CPU nell'applicazione. Se si riduce la risoluzione dell'output della destinazione di rendering, sono presenti meno pixel da calcolare e, di conseguenza, un numero minore di operazioni che la GPU deve eseguire per il rendering di un'immagine. Il ridimensionamento del viewport (scala della risoluzione dinamica) è la procedura per eseguire il rendering dell'immagine in una destinazione di rendering più piccola, quindi è possibile visualizzare il dispositivo di output. Il dispositivo viene sottoposto a esempio dal set di pixel più piccolo per visualizzare l'immagine finale.

Dopo la riduzione della risoluzione del rendering, se:
1) Il framerate dell'applicazione **aumenta**, quindi è probabile che la **GPU sia limitata**
1) Framerate dell'applicazione senza **modifiche**, è probabile che la **CPU sia limitata**

>[!NOTE]
>Unity offre la possibilità di modificare facilmente la risoluzione della destinazione di rendering dell'applicazione in fase di esecuzione tramite la proprietà *[XRSettings. renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* . La risoluzione dell'immagine finale visualizzata sul dispositivo è fissa. La piattaforma campiona l'output di risoluzione inferiore per creare un'immagine di risoluzione superiore per il rendering delle visualizzazioni. 
>
>```CS
>UnityEngine.XR.XRSettings.renderScale = 0.7f;
>```

## <a name="how-to-improve-your-application"></a>Come migliorare l'applicazione

### <a name="cpu-performance-recommendations"></a>Raccomandazioni sulle prestazioni della CPU

In genere, la maggior parte del lavoro in un'applicazione di realtà mista sulla CPU comporta l'esecuzione della "simulazione" della scena e l'elaborazione di una logica dell'applicazione univoca completa. Pertanto, le aree seguenti sono in genere destinate all'ottimizzazione.

- Animazioni
- Semplificare la fisica
- Allocazioni di memoria
- Algoritmi complessi, ad esempio cinematica inversa, ricerca di percorsi

### <a name="gpu-performance-recommendations"></a>Suggerimenti sulle prestazioni della GPU

#### <a name="understanding-bandwidth-vs-fill-rate"></a>Informazioni sulla velocità di riempimento rispetto alla larghezza di banda
Quando si esegue il rendering di un frame sulla GPU, un'applicazione è in genere limitata dalla larghezza di banda o dalla velocità di riempimento della memoria.

- La **larghezza di banda della memoria** è la velocità di lettura e scrittura che la GPU può eseguire dalla memoria
    - Per identificare le limitazioni della larghezza di banda, ridurre la qualità della trama e verificare se il framerate è migliorato.
    - In Unity, questa operazione può essere eseguita modificando la **qualità della trama** nelle impostazioni di **[qualità](https://docs.unity3d.com/Manual/class-QualitySettings.html)** **modifica** > **Impostazioni** > progetto.
- La **velocità di riempimento** si riferisce alla velocità effettiva dei pixel sottoposti a rendering che possono essere disegnati al secondo dalla GPU.
    - Per identificare le limitazioni della velocità di riempimento, ridurre la risoluzione dello schermo e verificare se il framerate è migliorato. 
    - In Unity, questa operazione può essere eseguita tramite la proprietà *[XRSettings. renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)*

La larghezza di banda della memoria comporta in genere ottimizzazioni per
1) riduzione delle risoluzioni di trama
2) usare meno trame (ad esempio normali, speculari e così via)

La velocità di riempimento si concentra principalmente sulla riduzione del numero di operazioni che devono essere calcolate per un pixel finale sottoposto a rendering. Esempi di questo genere rientrano nella riduzione
1) numero di oggetti di cui eseguire il rendering o il processo
2) numero di operazioni per shader
3) numero di fasi GPU fino al risultato finale (Geometry shader, effetti di post-elaborazione e così via)
4) numero di pixel di cui eseguire il rendering (ovvero risoluzione dello schermo)

#### <a name="reduce-poly-count"></a>Ridurre il numero di Poly
I conteggi di poligoni più elevati comportano più operazioni per la GPU e la riduzione del numero di poligoni nella scena riduce la quantità di tempo per il rendering di tale geometria. Ci sono anche altri fattori da tenere presente nell'ombreggiatura della geometria che può essere ancora costosa, ma il conteggio dei poligoni è la metrica di base per determinare il costo di rendering di una scena.

#### <a name="limit-overdraw"></a>Limite di sovralievo

Un elevato livello di sovradisegnazione si verifica quando viene eseguito il rendering di più oggetti, ma non vengono visualizzati sullo schermo, perché sono nascosti da un altro oggetto, in genere più vicino, oggetto occlusione. Si supponga di esaminare un muro con più sale e geometria. Tutta la geometria verrebbe elaborata per il rendering, ma è necessario eseguire il rendering solo della parete opaca, perché occlude la visualizzazione di tutti gli altri contenuti. Ciò comporta una dispendiosa operazione non necessaria per la visualizzazione corrente.

#### <a name="shaders"></a>Shader

Gli shader sono piccoli programmi eseguiti sulla GPU e in genere determinano due passaggi importanti nel rendering:
1) quali vertici dell'oggetto devono essere disegnati sullo schermo e dove si trovano nello spazio dello schermo, ad esempio Vertex shader)
    - Il vertex shader viene in genere eseguito per ogni vertice per ogni GameObject
2) che cosa colora tali pixel, ad esempio Pixel shader)
    - Il pixel shader viene eseguito per pixel per la trama di cui viene eseguito il rendering per il dispositivo presente

In genere gli shader eseguono numerose trasformazioni e calcoli di illuminazione. Sebbene i modelli di illuminazione complessi, le ombre e altre operazioni possano generare risultati eccezionali, presentano anche un prezzo. La riduzione del numero di operazioni calcolate negli shader può ridurre notevolmente il lavoro complessivo necessario per eseguire una GPU per fotogramma.

##### <a name="shader-coding-recommendations"></a>Suggerimenti sulla codifica dello shader

- Usare il filtro bilineare laddove possibile
- Ridisporre le espressioni in modo da usare funzioni intrinseche folli per eseguire un'operazione di moltiplicazione e un aggiunta allo stesso tempo
- Precalcolare quanto più possibile sulla CPU e passare come costanti al materiale
- **Preferire le operazioni di trasferimento dal pixel shader al vertex shader**
    - Generalmente il numero di vertici < < numero di pixel, ovvero 720p = = 921.600 pixel, 1080p = = 2.073.600 pixel e così via)

#### <a name="remove-gpu-stages"></a>Rimuovi fasi GPU
Gli effetti di post-elaborazione possono essere molto costosi e in genere inibiscono la velocità di riempimento dell'applicazione. Sono incluse anche tecniche di anti-aliasing, ad esempio MSAA. In HoloLens è consigliabile evitare completamente queste tecniche. Inoltre, quando possibile, è consigliabile evitare fasi aggiuntive dello shader, ad esempio geometria, scafo e compute shader.

## <a name="memory-recommendations"></a>Consigli sulla memoria
Un'allocazione eccessiva della memoria & operazioni di deallocazione possono avere effetti negativi sull'applicazione olografica, con prestazioni incoerenti, frame bloccati e altro comportamento dannoso. È particolarmente importante comprendere le considerazioni sulla memoria durante lo sviluppo in Unity, perché la gestione della memoria è controllata dal Garbage Collector.

#### <a name="object-pooling"></a>Pool di oggetti

Il pool di oggetti è una tecnica comune per ridurre il costo delle allocazioni continue & le deallocazioni di oggetti. Questa operazione viene eseguita allocando un pool di grandi dimensioni di oggetti identici e riutilizzando le istanze disponibili inattive da questo pool invece di generare ed eliminare costantemente gli oggetti nel tempo. I pool di oggetti sono ottimi per i componenti riutilizzabili con durata variabile durante un'app.

## <a name="see-also"></a>Vedere anche
- [Consigli sulle prestazioni per Unity](performance-recommendations-for-unity.md)
- [Impostazioni consigliate per Unity](recommended-settings-for-unity.md)

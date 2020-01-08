---
title: Rendering
description: Il rendering olografico consente all'app di creare un ologramma in una posizione precisa in tutto il mondo intorno all'utente, indipendentemente dal fatto che sia collocato esattamente nel mondo fisico o in un'area di autenticazione virtuale creata.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: rendering, ologramma
ms.openlocfilehash: 544e43ced57309cfe2628cbea65d07e94563eb41
ms.sourcegitcommit: 317653cd8500563c514464f0337c1f230a6f3653
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/28/2019
ms.locfileid: "75503819"
---
# <a name="rendering"></a>Rendering

Il rendering olografico consente all'applicazione di creare un ologramma in una posizione precisa in tutto il mondo intorno all'utente, indipendentemente dal fatto che sia collocato esattamente nel mondo fisico o in un'area di autenticazione virtuale creata. Gli [ologrammi](hologram.md) sono oggetti costituiti da suoni e luce. Il rendering consente all'applicazione di aggiungere la luce.

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
        <td>Rendering</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="holographic-rendering"></a>Rendering olografico

La chiave per il rendering olografico è sapere se si sta eseguendo il rendering in una visualizzazione di tipo See-through, ad esempio HoloLens, che consente all'utente di visualizzare sia il mondo fisico che gli ologrammi oppure un display opaco come un auricolare immersivo di Windows a realtà mista che blocca il mondo.

I dispositivi con **schermi See-through**, ad esempio [HoloLens](hololens-hardware-details.md), aggiungono luce al mondo. I pixel neri sono completamente trasparenti, mentre i pixel più luminosi sono sempre più opachi. Poiché la luce dagli schermi viene aggiunta alla luce dal mondo reale, i pixel bianchi sono parzialmente traslucidi.

Sebbene il rendering stereoscopico fornisca un segnale di profondità per gli ologrammi, l'aggiunta di [effetti di base](interaction-fundamentals.md) può aiutare gli utenti a vedere più facilmente la superficie di un ologramma. Una tecnica di base consiste nell'aggiungere un alone intorno a un ologramma sulla superficie vicina, quindi eseguire il rendering di un'ombreggiatura rispetto a questo bagliore. In questo modo, l'ombreggiatura sembra sottrarre la luce dall'ambiente. Il [suono spaziale](spatial-sound.md) è un altro spunto estremamente importante, che consente agli utenti di ragionare sulla distanza e sulla posizione relativa di un ologramma.

I dispositivi con **visualizzazioni opache**, come gli [auricolari ad alta realtà mista di Windows](immersive-headset-hardware-details.md), bloccano il mondo. I pixel neri sono neri a tinta unita e qualsiasi altro colore viene visualizzato come colore per l'utente. L'applicazione è responsabile del rendering di tutto ciò che l'utente vede. Questo rende ancora più importante mantenere una frequenza di aggiornamento costante in modo che gli utenti abbiano un'esperienza confortevole.

## <a name="predicted-rendering-parameters"></a>Parametri di rendering stimati

Gli auricolari con realtà mista (HoloLens e auricolari immersivi) tengono continuamente traccia della posizione e dell'orientamento dell'intestazione dell'utente in relazione all'ambiente circostante. Quando l'applicazione inizia a preparare il frame successivo, il sistema prevede la posizione in cui si troverà la testa dell'utente nel momento esatto in cui il frame viene visualizzato sullo schermo. In base a questa stima, il sistema calcola la visualizzazione e le trasformazioni di proiezione da usare per quel frame. **Per produrre risultati corretti, è necessario che l'applicazione utilizzi queste trasformazioni**. Se le trasformazioni fornite dal sistema non vengono usate, l'immagine risultante non verrà allineata al mondo reale, causando fastidio all'utente.

Si noti che per prevedere in modo accurato quando un nuovo frame raggiungerà gli schermi, il sistema esegue costantemente la misurazione della latenza end-to-end efficace della pipeline di rendering dell'applicazione. Mentre il sistema si adatta alla lunghezza della pipeline di rendering, è possibile migliorare la stabilità dell'ologramma mantenendo la pipeline più breve possibile.

Le applicazioni che utilizzano tecniche avanzate per aumentare la stima del sistema possono eseguire l'override della vista di sistema e delle trasformazioni di proiezione. Queste applicazioni devono comunque usare le trasformazioni fornite dal sistema come base per le trasformazioni personalizzate in modo da produrre risultati significativi.

## <a name="other-rendering-parameters"></a>Altri parametri di rendering

Quando si esegue il rendering di un frame, il sistema specifica il viewport del buffer nascosto in cui l'applicazione deve essere disegnato. Questo viewport è spesso più piccolo delle dimensioni massime del buffer del frame. Indipendentemente dalla dimensione del viewport, una volta che il frame viene sottoposto a rendering dall'applicazione, il sistema ridimensiona l'immagine per riempire l'intera visualizzazione.

Per le applicazioni che non sono in grado di eseguire il rendering alla frequenza di aggiornamento richiesta, [è possibile configurare i parametri di rendering del sistema](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration) per ridurre le richieste di memoria e i costi di rendering a scapito dell'aumento degli alias dei pixel. È anche possibile modificare il formato del buffer nascosto, che per alcune app può contribuire a migliorare la larghezza di banda della memoria e la velocità effettiva dei pixel.

Il tronco di rendering, la risoluzione e il framerate in cui l'app viene richiesta per il rendering potrebbe anche passare da un frame all'altro e può variare in base alla sinistra e all'occhio destro. Ad esempio, quando è attiva l' [acquisizione di realtà mista](mixed-reality-capture.md) (MRC) e la [configurazione della visualizzazione foto/video della fotocamera](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind) non è esplicita, è possibile che venga eseguito il rendering di un'occhiata con una maggiore FOV o una risoluzione.

Per qualsiasi frame specificato, l'app *deve* eseguire il rendering usando la trasformazione visualizzazione, la trasformazione proiezione e la risoluzione del viewport fornita dal sistema. Inoltre, l'applicazione non deve mai presupporre che qualsiasi parametro di rendering o visualizzazione rimanga fisso dal frame al frame. I motori come Unity gestiscono tutte queste trasformazioni per l'utente nei propri oggetti fotocamera, in modo che lo spostamento fisico degli utenti e lo stato del sistema siano sempre rispettati. Se l'applicazione consente lo spostamento virtuale dell'utente in tutto il mondo, ad esempio usando levetta in un gamepad, è possibile aggiungere un oggetto rig padre sopra la fotocamera che lo sposta. In questo modo la fotocamera riflette il movimento virtuale e fisico dell'utente. Se l'applicazione modifica la dimensione della trasformazione visualizzazione, della trasformazione proiezione o del viewport fornita dal sistema, deve informare il sistema chiamando l'API di [sostituzione](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicCameraPose#Windows_Graphics_Holographic_HolographicCameraPose)appropriata.

Per migliorare la stabilità del rendering olografico, l'app deve fornire a Windows ogni frame il buffer di profondità usato per il rendering. Se l'app fornisce un buffer di profondità, deve avere valori di profondità coerenti, con profondità espressa in metri dalla fotocamera. In questo modo, il sistema è in grado di usare i dati di profondità per pixel per stabilizzare meglio il contenuto se la testa dell'utente si sposta leggermente dalla posizione prevista. Se non si è in grado di fornire il buffer di profondità, è possibile fornire un punto di interesse e un normale, definendo un piano che consente di ridurre la maggior parte del contenuto. Se vengono forniti sia il buffer di profondità che un piano di attivazione, il sistema potrebbe utilizzarli entrambi. In particolare, è utile fornire sia il buffer di profondità sia un punto di interesse che include un vettore di velocità quando l'applicazione Visualizza gli ologrammi in movimento.

Per informazioni di basso livello sul suo argomento, vedere l'articolo relativo al [rendering in DirectX](rendering-in-directx.md) .

## <a name="holographic-cameras"></a>Fotocamere olografiche

La realtà mista di Windows introduce il concetto di **fotocamera olografica**. Le fotocamere olografiche sono simili alla fotocamera tradizionale presente nei testi grafici 3D; definiscono le proprietà estrinseche (posizione e orientamento) e intrinseche della fotocamera. (Ad esempio, il campo di visualizzazione viene usato per visualizzare una scena 3D virtuale). Diversamente dalle fotocamere 3D tradizionali, l'applicazione non è in grado di controllare la posizione, l'orientamento e le proprietà intrinseche della fotocamera. La posizione e l'orientamento della fotocamera olografica vengono invece controllati in modo implicito dal movimento dell'utente. Lo spostamento dell'utente viene inoltrato all'applicazione in base ai frame tramite una trasformazione della visualizzazione. Analogamente, le proprietà intrinseche della fotocamera sono definite dall'ottica calibrata del dispositivo e inoltrate frame per frame tramite la trasformazione di proiezione.

In generale, l'applicazione eseguirà il rendering di una singola fotocamera stereo. Tuttavia, un ciclo di rendering affidabile supporta più fotocamere e supporta sia le fotocamere mono che stereo. Ad esempio, il sistema potrebbe chiedere all'applicazione di eseguire il rendering da una prospettiva alternativa quando l'utente attiva una funzionalità come l' [acquisizione di realtà mista](mixed-reality-capture.md) (MRC), a seconda della forma dell'auricolare in questione. Le applicazioni in grado di supportare più fotocamere li ottengono [scegliendo](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration) il [tipo](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind) di fotocamere che possono supportare.

## <a name="volume-rendering"></a>Rendering del volume

Quando si esegue il rendering di MRIs medicali o di volumi di progettazione in 3D, vengono spesso usate tecniche di [rendering del volume](volume-rendering.md) . Queste tecniche possono essere particolarmente interessanti nella realtà mista, in cui gli utenti possono visualizzare naturalmente tale volume dagli angoli principali, semplicemente spostando l'intestazione.

## <a name="supported-resolutions-on-hololens-1st-gen"></a>Risoluzioni supportate su HoloLens (1a generazione)

* La dimensione massima del viewport è una proprietà di [HolographicDisplay](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay). Per impostazione predefinita, HoloLens è impostato sulla dimensione massima del viewport, che è 720p (1268x720).
* È possibile modificare le dimensioni del viewport impostando ViewportScaleFactor in HolographicCamera. Questo fattore di scala è compreso nell'intervallo tra 0 e 1.
* La dimensione più bassa del viewport supportata in HoloLens (1a generazione) è 50% di 720p, ovvero 360p (634x360). Si tratta di un ViewportScaleFactor di 0,5.
* Non è consigliabile usare elementi inferiori a 540p a causa della riduzione visiva, ma è possibile usarli per identificare i colli di bottiglia in percentuale di riempimento in pixel.

## <a name="supported-resolutions-on-hololens-2"></a>Risoluzioni supportate su HoloLens 2

* Le dimensioni correnti e massime della destinazione di rendering supportate sono proprietà della [configurazione della vista](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration). Per impostazione predefinita, HoloLens 2 è impostato sulla dimensione massima della destinazione di rendering, che è 1440x936.
* Le app possono modificare le dimensioni dei buffer di destinazione di rendering chiamando il metodo RequestRenderTargetSize per richiedere una nuova dimensione della destinazione di rendering. Verranno scelte nuove dimensioni della destinazione di rendering, che soddisfano o superano le dimensioni richieste della destinazione di rendering. Questa API modifica la dimensione del buffer di destinazione di rendering, che richiede la riallocazione della memoria sulla GPU. Le implicazioni di questo esempio includono: le dimensioni della destinazione di rendering possono essere ridimensionate per ridurre l'utilizzo della memoria sulla GPU e questo metodo non deve essere chiamato a frequenza elevata.
* Le app possono comunque modificare le dimensioni del viewport nello stesso modo in cui sono state effettuate per HoloLens 1. Questa operazione non comporta la riallocazione della memoria sulla GPU, quindi può essere modificata a frequenza elevata, ma non può essere usata per ridurre le richieste di memoria sulla GPU.
* La dimensione più bassa del viewport supportata in HoloLens 2 è 634x412. Si tratta di un ViewportScaleFactor di circa 0,44 quando la dimensione di destinazione di rendering predefinita è in uso.
* Se viene fornita una dimensione della destinazione di rendering minore della dimensione del viewport supportata più bassa, il fattore di scala del viewport verrà ignorato.
* Non è consigliabile usare elementi inferiori a 540p a causa della riduzione visiva, ma è possibile usarli per identificare i colli di bottiglia in percentuale di riempimento in pixel.



## <a name="see-also"></a>Vedi anche
* [Stabilità degli ologrammi](hologram-stability.md)
* [Rendering in DirectX](rendering-in-directx.md)

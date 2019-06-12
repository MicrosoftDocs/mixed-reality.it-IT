---
title: Per il rendering
description: Rendering holographic consente all'app disegnare un ologrammi in una posizione esatta nell'ambiente circostante all'utente, se viene inserito esattamente nel mondo fisico o all'interno di un'area di autenticazione virtuale creato.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: per il rendering, ologrammi
ms.openlocfilehash: 5271e94521b99e76998c2cbb43475a5f3f847917
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829904"
---
# <a name="rendering"></a>Per il rendering

Rendering holographic consente all'app disegnare un ologrammi in una posizione esatta nell'ambiente circostante all'utente, se viene inserito esattamente nel mondo fisico o all'interno di un'area di autenticazione virtuale creato. [Ologrammi](hologram.md) sono oggetti costituiti suono e chiaro e rendering consente all'app aggiungere la luce.

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
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (dal 1 ° generazione)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Auricolari coinvolgenti</strong></a></td>
    </tr>
     <tr>
        <td>Per il rendering</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="holographic-rendering"></a>Rendering holographic

Chiave per il rendering holographic consiste nel sapere se si esegue il rendering di una visualizzazione trasparente, ad esempio HoloLens, che consente all'utente di visualizzare il mondo fisico sia il vntana insieme - o una visualizzazione opaca, ad esempio cuffie immersive realtà mista di Windows, quali blocchi out del mondo.

I dispositivi con **consente di visualizzare trasparente**, ad esempio [HoloLens](hololens-hardware-details.md), aggiungere chiaro al mondo. Pixel neri sarà completamente trasparente, mentre il pixel più brillanti saranno sempre più opaco. Poiché la luce da verrà visualizzato il viene aggiunto alla luce dal mondo reale, anche bianco pixel sono in qualche modo semitrasparente.

Mentre rendering stereoscopico fornisce una pila di profondità per i vntana, aggiungendo [messa a terra effetti](interaction-fundamentals.md) consente agli utenti di vedere più facilmente quali superficie ologramma si avvicina. Una tecnica di messa a terra consiste nell'aggiungere un alone intorno ologramma nell'area di nelle vicinanze e quindi eseguire il rendering di un'ombreggiatura contro questa alone. In questo modo, verrà visualizzata l'ombreggiatura da sottrarre light dall'ambiente. [Suono spaziale](spatial-sound.md) può essere un altro estremamente importante di profondità, consentendo di motivo gli utenti sulla distanza e la posizione relativa di ologramma.

I dispositivi con **consente di visualizzare opachi**, ad esempio [auricolari coinvolgenti di realtà mista di Windows](immersive-headset-hardware-details.md), blocca tutto il mondo. Pixel neri sarà nero a tinta unita e qualsiasi altro colore verrà visualizzato come colore all'utente. L'app è responsabile del rendering tutto ciò che verrà visualizzato all'utente, è ancora più importante mantenere una frequenza di aggiornamento costante in modo che gli utenti abbiano un'esperienza pratica.

## <a name="predicted-rendering-parameters"></a>Parametri di rendering stimato

Mista auricolari realtà (HoloLens e auricolari immersive) monitorare continuamente la posizione e l'orientamento della testina dell'utente rispetto al loro ambiente circostante. Come l'app inizia a preparare il frame successivo, il sistema consente di stimare in cui head dell'utente sarà in futuro al momento esatto in cui verrà visualizzati i frame sugli schermi. Basato su questa stima, il sistema calcola le trasformazioni di visualizzazione e di proiezione da utilizzare per quel frame. L'applicazione **deve usare queste trasformazioni per produrre risultati corretti**; se non vengono utilizzate le trasformazioni di sistema, l'immagine risultante non verrà allineato con il mondo reale, causando disturbo utente.

Si noti che per stimare con precisione quando un nuovo frame raggiungeranno le visualizzazioni, il sistema è costantemente misurare la latenza end-to-end effettiva della pipeline di rendering dell'app. Mentre il sistema regolerà per la lunghezza della pipeline di rendering, è possibile migliorare ulteriormente la stabilità di ologramma mantenendo tale pipeline più corte possibili.

Le applicazioni che utilizzano tecniche avanzate per potenziare la stima del sistema è possono sostituire le trasformazioni di proiezione e visualizzazione di sistema. Queste App devono deve comunque usare trasformazioni fornito dal sistema come base per le trasformazioni personalizzate per produrre risultati significativi.

## <a name="other-rendering-parameters"></a>Altri parametri di rendering

Durante il rendering di un frame, il sistema specificherà il viewport buffer nascosto in cui l'applicazione deve essere disegnato. Questo riquadro di visualizzazione sarà spesso inferiore rispetto alle dimensioni del buffer frame completa. Indipendentemente dalla dimensione del viewport, dopo che il frame è stato eseguito il rendering dall'applicazione, il sistema verrà ingrandire l'immagine per riempire l'intero degli schermi.

Per le applicazioni che non riescono a eseguire il rendering con la velocità, aggiornamento obbligatorio [è possibile configurare parametri di sistema per il rendering](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration) per ridurre la pressione della memoria e/o dei costi per il rendering al costo di aliasing pixel maggiore. Anche possibile modificare il formato del buffer nascosto, che per alcune App può contribuire a migliorare la velocità effettiva pixel e larghezza di banda di memoria.

Di cono per il rendering, risoluzione e una frequenza in cui l'app viene richiesto di eseguire il rendering può cambiare anche da una cornice e possono differire tra l'occhio del lettore sinistro e destro. Ad esempio, quando [acquisizione di realtà mista](mixed-reality-capture.md) (MRC) è attivo e il [foto/video fotocamera visualizzare la configurazione](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind) non viene scelto in, può eseguire il rendering di un occhio con un campo di visualizzazione o la risoluzione di dimensioni superiori.

Per qualsiasi frame, l'app *necessario* eseguire il rendering utilizzando la trasformazione di visualizzazione, trasformazione di proiezione e la risoluzione del riquadro di visualizzazione fornito dal sistema. Inoltre, l'applicazione non deve dare mai per scontato che qualsiasi parametro di rendering/visualizzazione rimane fisso da fotogramma per fotogramma. Motori come Unity gestiscono tutte queste trasformazioni automaticamente i propri oggetti fotocamera, in modo che lo spostamento fisico di utenti e lo stato del sistema viene sempre rispettato. Se maggiormente l'app consente lo spostamento virtuale dell'utente tramite il mondo (usando ad esempio, il thumbstick su un gamepad), è possibile aggiungere un oggetto padre "di rig" di sopra della fotocamera che viene spostato, causando la fotocamera in modo da riflettere il movimento di fisica e virtuale sia dell'utente. Se l'app modifica la trasformazione di visualizzazione, trasformazione di proiezione o dimensione del viewport fornito dal sistema, è necessario informare il sistema chiamando appropriato [eseguire l'override API](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicCameraPose#Windows_Graphics_Holographic_HolographicCameraPose).

Per migliorare la stabilità del proprio rendering holographic, l'app deve fornire a Windows ogni fotogramma per il rendering utilizzato il buffer di profondità. Se l'app fornisce un buffer di profondità, devono avere valori profondità coerente, con la profondità espressa in metri dalla fotocamera. In questo modo il sistema di usare i dati di profondità per pixel per stabilizzare meglio contenuto se testa il suo finisce leggermente offset dalla posizione prevista. Se non si è in grado di fornire al buffer di profondità, è necessario invece fornire un punto di stato attivo e normale, che definisce un piano che consente di ridurre la maggior parte dei contenuti. Se vengono specificati sia il buffer di profondità e un piano di messa a fuoco, il sistema può utilizzare entrambi. In particolare, può essere utile fornire sia il buffer di profondità e un punto di stato attivo che include un vettore di velocità quando l'app viene visualizzata vntana in movimento.

Per tutti i dettagli di basso livello in questo caso, consultare il [il Rendering in DirectX](rendering-in-directx.md) articolo.

## <a name="holographic-cameras"></a>Fotocamere holographic

Realtà mista di Windows introduce il concetto di una **fotocamera holographic**. Holographic fotocamere sono simili alla fotocamera tradizionale trovata nei testi di grafica 3D: definiscono entrambi estrinseche (posizione e l'orientamento) e le proprietà intrinseche della fotocamera (es: campo di visualizzazione) consente di visualizzare una scena 3D virtuale. A differenza dei tradizionali fotocamere 3D, l'applicazione non è nel controllo della posizione, orientamento e le proprietà intrinseche della fotocamera. Piuttosto, la posizione e l'orientamento della fotocamera holographic in modo implicito è controllata dalle movimento dell'utente. Movimento dell'utente verrà inoltrata all'applicazione su una base di ciascun frame singolarmente tramite una trasformazione di visualizzazione. Allo stesso modo, le proprietà intrinseche della camera sono definite da ottica calibrati del dispositivo e inoltrate fotogramma per fotogramma tramite la trasformazione di proiezione.

Verrà in genere esegue il rendering di app per una fotocamera stereo unica. Tuttavia, un loop di rendering affidabili devono supportare più fotocamere e devono supportare fotocamere mono sia stereo. Ad esempio, il sistema richieda all'app di eseguire il rendering dal punto di vista alternativo quando l'utente attiva una funzionalità simile [acquisizione di realtà mista](mixed-reality-capture.md) MRC (), a seconda della forma delle cuffie in questione. Le app che possono supportare più fotocamere ottengono [acconsentire esplicitamente aggiuntivo](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration) per il [tipo](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind) delle videocamere possono supportare.

## <a name="volume-rendering"></a>Rendering di volume

Durante il rendering medici volumi in 3D, di progettazione o MRI [rendering volume](volume-rendering.md) tecniche vengono spesso usate. Queste tecniche possono essere particolarmente interessante nella realtà mista, in cui gli utenti possono naturalmente visualizzare tali un volume da chiavi angoli, semplicemente spostando propria testa.

## <a name="supported-resolutions-on-hololens-1st-gen"></a>Risoluzioni supportate su HoloLens (dal 1 ° generazione)
> [!NOTE]
> Saranno presenti più gli aggiornamenti in futuro in arrivo a questo articolo. [Visualizzare l'elenco di aggiornamenti](release-notes-april-2018.md)

* Le risoluzioni supportate attuali e massime sono di proprietà del [visualizzare la configurazione](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration). HoloLens è impostato per la risoluzione massima, ovvero 720p (1268 x 720), per impostazione predefinita.
* La dimensione minima supportata del viewport è 50% di 720p, ovvero 360p (634 x 360). A HoloLens, si tratta di un ViewportScaleFactor pari a 0,5.
* Nulla inferiori ai p 540 **non è consigliabile** a causa di riduzione delle prestazioni visual, ma può essere usato per identificare necks bottle in velocità di riempimento in pixel.

## <a name="supported-resolutions-on-hololens-2"></a>Risoluzioni supportate su HoloLens 2

> [!NOTE]
> Altre indicazioni specifiche su 2 HoloLens [presto](index.md#news-and-notes).


## <a name="see-also"></a>Vedere anche
* [Stabilità degli ologrammi](hologram-stability.md)
* [Rendering in DirectX](rendering-in-directx.md)
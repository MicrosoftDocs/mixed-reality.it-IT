---
title: Per il rendering
description: Rendering holographic consente all'app disegnare un ologrammi in una posizione esatta nell'ambiente circostante all'utente, se viene inserito esattamente nel mondo fisico o all'interno di un'area di autenticazione virtuale creato.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: per il rendering, ologrammi
ms.openlocfilehash: 45713fd7a30fc55a799da7e89ef52aff8f7eec46
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415413"
---
# <a name="rendering"></a>Per il rendering

Rendering holographic consente all'applicazione disegnare ologramma in una posizione esatta nell'ambiente circostante all'utente, se viene inserito esattamente nel mondo fisico o all'interno di un'area di autenticazione virtuale creato. [Ologrammi](hologram.md) sono oggetti costituiti suono e light. Per il rendering consente l'Application aggiungere la luce.

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
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
    </tr>
     <tr>
        <td>Per il rendering</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="holographic-rendering"></a>Rendering holographic

Chiave per il rendering holographic consiste nel sapere se si esegue il rendering di una visualizzazione trasparente, ad esempio HoloLens che consente all'utente di visualizzare il mondo fisico sia il vntana insieme, o una visualizzazione opaca, ad esempio visore VR immersivi una realtà mista di Windows che copre i il mondo.

I dispositivi con **consente di visualizzare trasparente**, ad esempio [HoloLens](hololens-hardware-details.md), aggiungere chiaro al mondo. Pixel neri sono completamente trasparente, mentre più brillanti pixel sono sempre più opachi. Poiché la luce da verrà visualizzato il viene aggiunto alla luce dal mondo reale, sono in qualche modo semitrasparente pixel bianco.

Mentre rendering stereoscopico fornisce una pila di profondità per i vntana, aggiungendo [messa a terra effetti](interaction-fundamentals.md) consente agli utenti di vedere più facilmente quali superficie ologramma si avvicina. Una tecnica di messa a terra consiste nell'aggiungere un alone intorno ologramma nell'area di nelle vicinanze e quindi eseguire il rendering di un'ombreggiatura contro questa alone. In questo modo, viene visualizzata l'ombreggiatura da sottrarre light dall'ambiente. [Suono spaziale](spatial-sound.md) è un'altra estremamente importante di profondità, consentendo di motivo gli utenti sulla distanza e la posizione relativa di ologramma.

I dispositivi con **consente di visualizzare opachi**, ad esempio [auricolari coinvolgenti di realtà mista di Windows](immersive-headset-hardware-details.md), blocca tutto il mondo. I pixel neri sono nero a tinta unita e qualsiasi altro colore vengono visualizzati come colore all'utente. L'applicazione è responsabile del rendering tutto ciò che l'utente vede. Questo rende ancora più importante per mantenere una frequenza di aggiornamento costante in modo che gli utenti abbiano un'esperienza pratica.

## <a name="predicted-rendering-parameters"></a>Parametri di rendering stimato

Mista auricolari realtà (HoloLens e auricolari immersive) monitorare continuamente la posizione e l'orientamento della testina dell'utente rispetto al loro ambiente circostante. Come l'applicazione inizia a preparare il frame successivo, il sistema consente di stimare in cui head dell'utente sarà in futuro al momento esatto in cui il frame viene visualizzato sugli schermi. Basato su questa stima, il sistema calcola le trasformazioni di visualizzazione e di proiezione da utilizzare per quel frame. L'applicazione **deve usare queste trasformazioni per produrre risultati corretti**; se non vengono utilizzate le trasformazioni di sistema, l'immagine risultante non verrà allineato con il mondo reale, causando disturbo utente.

Si noti che per stimare con precisione quando un nuovo frame raggiungeranno le visualizzazioni, il sistema è costantemente misurare la latenza end-to-end effettiva della pipeline di rendering dell'applicazione. Mentre il sistema si adatta alla lunghezza della pipeline di rendering, è possibile migliorare la stabilità di ologramma mantenendo tale pipeline più corte possibili.

Le applicazioni che utilizzano tecniche avanzate per potenziare la stima del sistema è possono sostituire le trasformazioni di proiezione e visualizzazione di sistema. Queste applicazioni deve comunque necessario usare trasformazioni fornito dal sistema come base per le trasformazioni personalizzate per produrre risultati significativi.

## <a name="other-rendering-parameters"></a>Altri parametri di rendering

Durante il rendering di un frame, il sistema specifica del viewport buffer nascosto in cui l'applicazione deve essere disegnato. Questo riquadro di visualizzazione è spesso più piccola della dimensione completa del buffer frame. Indipendentemente dalla dimensione del viewport, una volta che viene eseguito il frame dall'applicazione, il sistema upscales sull'immagine per riempire l'intero degli schermi.

Per le applicazioni che non riescono a eseguire il rendering con la velocità, aggiornamento obbligatorio [è possibile configurare parametri di sistema per il rendering](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration) per ridurre la pressione della memoria e i costi per il rendering al costo di aliasing pixel maggiore. Anche possibile modificare il formato del buffer nascosto, che per alcune App può contribuire a migliorare la velocità effettiva pixel e larghezza di banda di memoria.

Di cono per il rendering, risoluzione e una frequenza in cui l'app viene richiesto di eseguire il rendering potrebbe cambiare anche da una cornice e potrebbe variare attraverso l'occhio del lettore sinistro e destro. Ad esempio, quando [acquisizione di realtà mista](mixed-reality-capture.md) (MRC) è attivo e il [foto/video fotocamera visualizzare la configurazione](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind) non viene scelto in, potrebbe eseguire il rendering di un occhio con un campo di visualizzazione o la risoluzione di dimensioni superiori.

Per qualsiasi frame, l'app *necessario* eseguire il rendering utilizzando la trasformazione di visualizzazione, trasformazione di proiezione e la risoluzione del riquadro di visualizzazione fornito dal sistema. Inoltre, l'applicazione non deve dare mai per scontato che qualsiasi parametro di rendering o la vista rimane fisso da fotogramma per fotogramma. Motori come Unity gestiscono tutte queste trasformazioni per l'utente in oggetti corrispondenti della fotocamera in modo che lo spostamento fisico di utenti e lo stato del sistema viene sempre rispettato. Se l'applicazione consente lo spostamento virtuale dell'utente tramite il mondo (usando ad esempio, il thumbstick su un gamepad), è possibile aggiungere un oggetto rig padre di sopra della fotocamera che non si sposta il. In questo modo la fotocamera in modo da riflettere i movimenti di fisica e virtuale dell'utente. Se l'applicazione modifica la trasformazione di visualizzazione, trasformazione di proiezione o dimensione del viewport fornito dal sistema, è necessario informare il sistema chiamando appropriato [eseguire l'override API](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicCameraPose#Windows_Graphics_Holographic_HolographicCameraPose).

Per migliorare la stabilità del proprio rendering holographic, l'app deve fornire a Windows ogni fotogramma per il rendering utilizzato il buffer di profondità. Se l'app fornisce un buffer di profondità, devono avere valori profondità coerente, con la profondità espressa in metri dalla fotocamera. In questo modo il sistema di usare i dati di profondità per pixel per stabilizzare meglio contenuto se testa il suo finisce leggermente offset dalla posizione prevista. Se non si è in grado di fornire al buffer di profondità, è possibile fornire un punto di stato attivo e normale, che definisce un piano che consente di ridurre la maggior parte dei contenuti. Se vengono specificati sia il buffer di profondità e un piano di messa a fuoco, il sistema può utilizzare entrambi. In particolare, è utile fornire sia il buffer di profondità e un punto di stato attivo che include un vettore di velocità quando l'applicazione visualizza vntana in movimento.

Fare riferimento a [il Rendering in DirectX](rendering-in-directx.md) per informazioni dettagliate di basso livello sulle suo argomento.

## <a name="holographic-cameras"></a>Fotocamere holographic

Realtà mista di Windows introduce il concetto di una **fotocamera holographic**. Holographic fotocamere sono simili alla fotocamera tradizionale trovata nei testi di grafica 3D: definiscono entrambi estrinseche (posizione e l'orientamento) e le proprietà intrinseche della fotocamera. (Ad esempio:, campo-di-view consente di visualizzare una scena 3D virtuale.) A differenza dei tradizionali fotocamere 3D, l'applicazione non è nel controllo della posizione, orientamento e le proprietà intrinseche della fotocamera. Piuttosto, la posizione e l'orientamento della fotocamera holographic in modo implicito è controllata dalle movimento dell'utente. Movimento dell'utente verrà inoltrata all'applicazione su una base di ciascun frame singolarmente tramite una trasformazione di visualizzazione. Allo stesso modo, le proprietà intrinseche della camera sono definite da ottica calibrati del dispositivo e inoltrate fotogramma per fotogramma tramite la trasformazione di proiezione.

In generale l'applicazione eseguirà il rendering di una fotocamera stereo unica. Tuttavia, un loop di rendering affidabile supporteranno più fotocamere e supporterà fotocamere mono sia stereo. Ad esempio, il sistema potrebbe chiedere l'applicazione per eseguire il rendering dal punto di vista alternativo quando l'utente attiva una funzionalità simile [acquisizione di realtà mista](mixed-reality-capture.md) MRC (), a seconda della forma delle cuffie in questione. Le applicazioni in grado di supportare più fotocamere ottenerle [acconsentire esplicitamente aggiuntivo](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration) per il [tipo](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind) delle videocamere possono supportare.

## <a name="volume-rendering"></a>Rendering di volume

Quando i volumi in 3D, di progettazione o il rendering MRIs medici [rendering volume](volume-rendering.md) tecniche vengono spesso usate. Queste tecniche possono essere particolarmente interessante nella realtà mista, in cui gli utenti possono naturalmente visualizzare tali un volume da chiavi angoli, semplicemente spostando propria testa.

## <a name="supported-resolutions-on-hololens-1st-gen"></a>Risoluzioni supportate su HoloLens (dal 1 ° generazione)
> [!NOTE]
> Altri aggiornamenti saranno presto disponibili. [Visualizzare l'elenco di aggiornamenti](release-notes-april-2018.md)

* Le risoluzioni supportate attuali e massime sono di proprietà del [visualizzare la configurazione](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration). HoloLens è impostato per la risoluzione massima, ovvero 720p (1268 x 720), per impostazione predefinita.
* La dimensione minima supportata del viewport è 50% di 720p, ovvero 360p (634 x 360). A HoloLens, si tratta di un ViewportScaleFactor pari a 0,5.
* Nulla inferiori ai p 540 **non è consigliabile** a causa di riduzione delle prestazioni visual, ma può essere usato per identificare necks bottle in velocità di riempimento in pixel.

## <a name="supported-resolutions-on-hololens-2"></a>Risoluzioni supportate su HoloLens 2

> [!NOTE]
> Altre indicazioni specifiche su 2 HoloLens [presto](index.md#news-and-notes).


## <a name="see-also"></a>Vedere anche
* [Stabilità degli ologrammi](hologram-stability.md)
* [Rendering in DirectX](rendering-in-directx.md)

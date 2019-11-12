---
title: Criteri di qualità delle app
description: Questo documento descrive i principali fattori che influiscono sulla qualità delle app per realtà mista.
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: criteri di qualità delle app, realtà mista, app per realtà mista
ms.openlocfilehash: d167e141b536f9247d22e40afefa718ecc399f5a
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926584"
---
# <a name="app-quality-criteria"></a>Criteri di qualità delle app

Questo documento descrive i principali fattori che influiscono sulla qualità delle app per realtà mista. Per ogni fattore vengono fornite le informazioni seguenti
* Panoramica: breve descrizione del fattore di qualità e dei motivi per cui è importante.
* Effetto del dispositivo: il tipo di dispositivo di realtà mista della finestra interessato.
* Criteri di qualità: come valutare il fattore di qualità.
* Come misurare, ovvero i metodi per misurare o sperimentare il problema.
* Suggerimenti: riepilogo degli approcci per offrire un'esperienza utente migliore.
* Risorse: risorse di sviluppo e progettazione pertinenti utili per creare esperienze di app migliori.

## <a name="frame-rate"></a>Frequenza dei fotogrammi

La frequenza dei fotogrammi è il primo pilastro della stabilità degli ologrammi e della comodità degli utenti. La frequenza dei fotogrammi al di sotto delle destinazioni consigliate può comportare la distorsione degli ologrammi, con un impatto negativo sulla credibilità dell'esperienza e potenzialmente causare affaticamento degli occhi. La frequenza dei fotogrammi di destinazione per la tua esperienza negli auricolari ad alta realtà mista di Windows è 60Hz o 90Hz, a seconda dei computer compatibili con la realtà Windows che desideri supportare. Per HoloLens la frequenza dei fotogrammi di destinazione è 60Hz.

### <a name="device-impact"></a>Effetti sul dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criteri di qualità

|  Consigliate  |  Soddisfi |  Esito negativo |
--- | --- | ---
| L'app soddisfa costantemente i frame al secondo (FPS) obiettivo del dispositivo di destinazione: 60fps in HoloLens; 90fps su PC ultra; e 60fps nei PC mainstream. | L'app ha un frame intermittente che non ostacola l'esperienza principale; o FPS è costantemente inferiore all'obiettivo desiderato, ma non impedisce l'esperienza dell'app. | L'app sta riscontrando un calo della frequenza dei fotogrammi in media ogni 10 secondi o meno. |

### <a name="how-to-measure"></a>Come misurare

* Un grafico con frequenza dei fotogrammi in tempo reale viene fornito tramite il [portale per dispositivi Windows](using-the-windows-device-portal.md#system-performance) in "prestazioni del sistema".
* Per il debug dello sviluppo, aggiungere un contatore di diagnostica della frequenza dei fotogrammi nell'app. Vedere risorse per un contatore di esempio.
* Le gocce di frequenza dei fotogrammi possono essere rilevate nel dispositivo mentre l'app è in esecuzione spostando l'intestazione da un lato all'altro. Se l'ologramma mostra un movimento nervoso imprevisto, è probabile che la frequenza minima dei frame o il piano di stabilità sia la causa.

### <a name="recommendations"></a>Consigli

* Aggiungere un contatore della frequenza dei fotogrammi all'inizio del lavoro di sviluppo.
* Le modifiche che comportano un calo nella frequenza del frame devono essere valutate e risolte in modo appropriato come bug delle prestazioni.

### <a name="resources"></a>Risorse

#### <a name="documentation"></a>Documentazione

* [Informazioni sulle prestazioni per la realtà mista](understanding-performance-for-mixed-reality.md)
* [Stabilità e framerate degli ologrammi](hologram-stability.md#frame-rate)
* [Budget per le prestazioni dell'asset](asset-creation-process.md)
* [Consigli sulle prestazioni per Unity](performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a>Strumenti ed esercitazioni

* [MRToolkit, visualizzazione del contatore FPS](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [MRToolkit, shader](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a>Riferimenti esterni

* [Unity, ottimizzazione delle applicazioni per dispositivi mobili](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a>Stabilità olografica

Gli ologrammi stabili aumenteranno l'usabilità e la credibilità dell'app e creeranno un'esperienza di visualizzazione più comoda per l'utente. La qualità della stabilità dell'ologramma è il risultato dello sviluppo di App valide e della capacità del dispositivo di comprendere (monitorare) il proprio ambiente. Sebbene la frequenza dei fotogrammi sia il primo pilastro della stabilità, altri fattori possono influiscono sulla stabilità, tra cui:

* Uso del piano di stabilizzazione
* Distanza dagli ancoraggi spaziali
* Tracking

### <a name="device-impact"></a>Effetti sul dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criteri di qualità

|  Consigliate  |  Soddisfi |  Esito negativo |
--- | --- | ---
|  Gli ologrammi appaiono costantemente stabili. | Il contenuto secondario presenta un movimento imprevisto; o un movimento imprevisto non ostacola l'esperienza complessiva dell'app. | Il contenuto primario nel frame presenta un movimento imprevisto. |

### <a name="how-to-measure"></a>Come misurare

Durante l'uso del dispositivo e la visualizzazione dell'esperienza:

* Spostare la testa da un lato all'altro, se gli ologrammi mostrano un movimento imprevisto, la frequenza dei fotogrammi ridotta o l'allineamento non corretto del piano di stabilità al piano focale è la causa probabile.
* Spostarsi tra gli ologrammi e l'ambiente, cercare comportamenti come Swim e nervosismo. Questo tipo di movimento è probabilmente causato dal fatto che il dispositivo non tiene traccia dell'ambiente o la distanza dall'ancoraggio spaziale.
* Se nel frame sono presenti ologrammi di grandi dimensioni o più, osservare il comportamento degli ologrammi a diverse profondità spostando la posizione della testa da un lato all'altro, se shakiness è probabilmente causato dal piano di stabilizzazione.

### <a name="recommendations"></a>Consigli

* Aggiungere un contatore della frequenza dei fotogrammi all'inizio del lavoro di sviluppo.
* Usare il piano di stabilizzazione.
* Eseguire sempre il rendering degli ologrammi ancorati all'interno di 3 metri dell'ancoraggio.
* Assicurarsi che l'ambiente sia configurato per il rilevamento appropriato.
* Progetta la tua esperienza per evitare gli ologrammi a diversi livelli di profondità focale all'interno del frame.

### <a name="resources"></a>Risorse

#### <a name="documentation"></a>Documentazione

* [Stabilità e framerate degli ologrammi](hologram-stability.md#frame-rate)
* [Case Study, uso del piano di stabilizzazione](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [Informazioni sulle prestazioni per la realtà mista](understanding-performance-for-mixed-reality.md)
* [Consigli sulle prestazioni per Unity](performance-recommendations-for-unity.md)
* [Ancoraggi nello spazio](spatial-anchors.md)
* [Gestione degli errori di rilevamento](coordinate-systems.md#handling-tracking-errors)
* [Cornice fissa di riferimento](coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a>Strumenti ed esercitazioni

* [Kit MR Companion, Kinect dpi](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a>Posizione degli ologrammi su superfici reali

I disallineamenti degli ologrammi con oggetti fisici (se destinati a essere posizionati in relazione l'uno con l'altro) sono un'indicazione chiara della mancata unione degli ologrammi e del mondo reale. L'accuratezza della selezione host deve essere relativa alle esigenze dello scenario; ad esempio, la selezione della superficie generale può utilizzare la mappa spaziale, ma la selezione host più accurata richiede l'utilizzo di marcatori e di calibrazione.

### <a name="device-impact"></a>Effetti sul dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criteri di qualità

|  Consigliate  |  Soddisfi |  Esito negativo |
--- | --- | ---
| Gli ologrammi si allineano alla superficie in genere nell'intervallo di centimetri. Se è necessaria una maggiore accuratezza, l'app deve fornire un modo efficiente per collaborare all'interno della specifica dell'app desiderata. | N/D | Gli ologrammi appaiono non allineati con l'oggetto di destinazione fisico suddividendo il piano della superficie o facendo in modo che si trovi in un altro modo. Se è necessaria l'accuratezza, gli ologrammi dovrebbero soddisfare le specifiche di prossimità dello scenario. | 

### <a name="how-to-measure"></a>Come misurare

* Gli ologrammi posizionati sulla mappa spaziale non devono essere visualizzati in modo significativo sopra o sotto la superficie.
* Gli ologrammi che richiedono un posizionamento accurato devono avere una forma di sistema di marcatore e di calibrazione accurato per il requisito dello scenario.

### <a name="recommendations"></a>Consigli

* La mappa spaziale è utile per posizionare oggetti sulle superfici quando la precisione non è necessaria.
* Per la massima precisione, usare i marcatori o i poster per impostare gli ologrammi e un controller Xbox (o un meccanismo di allineamento manuale) per la calibrazione finale.
* Prendere in considerazione la possibilità di suddividere ologrammi molto grandi in parti logiche e di allineare ogni parte alla superficie.
* L'impostazione non corretta della distanza interpupillare (dpi) può anche influire sull'allineamento degli ologrammi. Configurare sempre HoloLens sul DPI dell'utente.

### <a name="resources"></a>Risorse

#### <a name="documentation"></a>Documentazione

* [Selezione host per mapping spaziale](spatial-mapping.md#placement)
* [Processo di analisi chat room](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [Procedure consigliate per gli ancoraggi spaziali](spatial-anchors.md#best-practices)
* [Gestione degli errori di rilevamento](coordinate-systems.md#handling-tracking-errors)
* [Mapping spaziale in Unity](spatial-mapping-in-unity.md)
* [Panoramica sullo sviluppo di Vuforia](vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a>Strumenti ed esercitazioni

* [MR Spatial 230: mapping spaziale](holograms-230.md)
* [MR Toolkit, librerie di mapping spaziale](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [Kit MR Companion, esempio di calibrazione poster](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [Kit MR Companion, Kinect dpi](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a>Riferimenti esterni

* [Case Study di Lowes, allineamento della precisione](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a>Visualizzazione della zona di comfort

Gli sviluppatori di app controllano la posizione di convergenza degli occhi degli utenti inserendo contenuto e ologrammi a diverse profondità. Gli utenti che indossano HoloLens saranno sempre a 2,0 m per mantenere un'immagine chiara, perché le visualizzazioni HoloLens sono fisse a distanza ottica circa 2,0 m dall'utente. Una profondità di contenuto impropria può causare disagi visivi o affaticamento.

### <a name="device-impact"></a>Effetti sul dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criteri di qualità

<table>
<tr>
<td> Consigliate </td><td><ul>
<li>Inserire il contenuto a 2m.</li><li>Quando gli ologrammi non possono essere posizionati su 2m e i conflitti tra la convergenza e l'alloggio non possono essere evitati, la zona ottimale per la posizione degli ologrammi è compresa tra 1.25 m e 5m.</li><li>In ogni caso, i progettisti devono strutturare il contenuto per incoraggiare gli utenti a interagire tra 1 + m (ad esempio, modificare le dimensioni del contenuto e i parametri di posizionamento predefiniti).</li><li>A meno che non sia specificamente necessario per lo scenario, un piano di ritaglio deve essere implementato con dissolvenza a partire da 1 milione.</li><li>Nei casi in cui è necessaria un'osservazione più stretta di un ologramma senza movimento, il contenuto non deve essere più vicino a 50cm.</li>
</ul></td>
</tr><tr>
<td> Soddisfi</td><td> Il contenuto si trova all'interno delle linee guida per la visualizzazione e il movimento, ma non è corretto o non utilizza il piano di ritaglio.</td>
</tr><tr>
<td> Esito negativo </td><td> Il contenuto viene presentato troppo vicino (in genere &lt;1.25 m o &lt;50cm per gli ologrammi stazionari che richiedono un'osservazione più approfondita).</td>
</tr>
</table>

### <a name="how-to-measure"></a>Come misurare

* Il contenuto deve essere in genere 2m, ma non più vicino a 1,25 o più di 5 minuti.
* Con poche eccezioni, la distanza di rendering del ritaglio HoloLens deve essere impostata su. 85CM con la dissolvenza del contenuto a partire da 1 milione. Approccio al contenuto e annotare l'effetto del piano di ritaglio.
* Il contenuto fisso non deve essere più vicino a 50cm.

### <a name="recommendations"></a>Consigli

* Progettare il contenuto per la distanza di visualizzazione ottimale di 2m.
* Impostare la distanza di rendering del ritaglio su 85cm con la dissolvenza del contenuto a partire da 1 milione.
* Per gli ologrammi stazionari che necessitano di una visualizzazione più vicina, il piano di ridimensionamento deve essere non più vicino a 30cm e la dissolvenza dovrebbe iniziare da almeno 10 cm dal piano di ritaglio.

### <a name="resources"></a>Risorse

* [Distanza di rendering](hologram-stability.md#hologram-render-distances)
* [Punto focale in Unity](focus-point-in-unity.md)
* [Sperimentazione con scalabilità](scale.md#experimenting-with-scale)
* [Testo, dimensioni del carattere consigliate](typography.md#recommended-font-size)

## <a name="depth-switching"></a>Cambio di profondità

Indipendentemente dalla visualizzazione della zona di problemi di comfort, l'utente può cambiare spesso o rapidamente tra gli oggetti focali vicini e lontani (inclusi gli ologrammi e il contenuto reale) può causare la fatica oculomotore e il disagio generale.

### <a name="device-impact"></a>Effetti sul dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criteri di qualità

|  Consigliate  |  Soddisfi |  Esito negativo |
--- | --- | ---
|  Cambio di profondità naturale o limitato che non determina una riattivazione non naturale dell'utente. | Cambio di profondità improvviso. si tratta di un elemento di base e progettato nell'esperienza dell'app o di un cambio di profondità improvviso causato da contenuto reale imprevisto. | Commutatore di profondità coerente o cambio di profondità improvviso non necessario o di base per l'esperienza dell'app. | 

### <a name="how-to-measure"></a>Come misurare

* Se l'app richiede all'utente di modificare in modo coerente e/o modificare in modo brusco lo stato attivo, si verifica un problema di cambio di profondità.

### <a name="recommendations"></a>Consigli

* Mantieni il contenuto primario in un piano focale coerente e assicurati che il piano di stabilizzazione corrisponda al piano focale. Ciò ridurrà l'affaticamento oculomotore e lo spostamento imprevisto dell'ologramma.

### <a name="resources"></a>Risorse

* [Distanza di rendering](hologram-stability.md#hologram-render-distances)
* [Punto focale in Unity](focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a>Uso del suono spaziale

In realtà mista di Windows, il motore audio fornisce il componente uditivo dell'esperienza di realtà mista simulando il suono 3D usando la direzione, la distanza e le simulazioni ambientali. L'uso di un suono spaziale in un'applicazione consente agli sviluppatori di collocare in modo convincente i suoni in uno spazio tridimensionale (Sphere) intorno all'utente. Questi suoni sembreranno come se provenissero da oggetti fisici reali o dagli ologrammi della realtà mista nell'ambiente dell'utente. Il suono spaziale è uno strumento potente per l'immersione, l'accessibilità e la progettazione dell'esperienza utente nelle applicazioni di realtà mista.

### <a name="device-impact"></a>Effetti sul dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criteri di qualità

|  Consigliate  |  Soddisfi |  Esito negativo |
--- | --- | ---
|  Il suono è con spazialità logica e l'esperienza utente utilizza in modo appropriato il suono per facilitare l'individuazione degli oggetti e il feedback degli utenti. Il suono è naturale e pertinente per gli oggetti e normalizzato in tutto lo scenario. | L'audio spaziale viene utilizzato in modo appropriato per ottenere la credibilità, ma mancante come mezzo per facilitare il feedback degli utenti e l'individuabilità. | Il suono non viene spaziato come previsto e/o non è presente alcun suono per assistere l'utente all'interno dell'esperienza utente. O l'audio spaziale non è stato considerato o usato nella progettazione dello scenario. | 

### <a name="how-to-measure"></a>Come misurare

* In generale, i suoni rilevanti devono emettere da ologrammi di destinazione (ad esempio, il suono di corteccia proveniente dal cane olografico).
* I segnali acustici devono essere usati in tutta l'esperienza utente per aiutare gli utenti a ricevere commenti e suggerimenti o a conoscere le azioni all'esterno del frame olografico.

### <a name="recommendations"></a>Consigli

* Utilizzare l'audio spaziale per supportare l'individuazione oggetti e le interfacce utente.
* I suoni reali funzionano meglio rispetto alla sintesi o al suono non naturale.
* La maggior parte dei suoni deve essere spaziali.
* Evitare gli emettitori invisibile.
* Evitare la maschera spaziale.
* Normalizzare tutti i suoni.

### <a name="resources"></a>Risorse

#### <a name="documentation"></a>Documentazione

* [Audio spaziale](spatial-sound.md)
* [Progettazione dell'audio spaziale](spatial-sound-design.md)
* [Audio spaziale in Unity](spatial-sound-in-unity.md)
* [Case Study, audio spaziale per HoloTour](case-study-spatial-sound-design-for-holotour.md)
* [Case Study, uso del suono spaziale in RoboRaid](case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a>Strumenti ed esercitazioni

* [MR Spatial 220: audio spaziale](holograms-220.md)
* [MRToolkit, audio spaziale](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a>Concentrarsi sui limiti dei frame olografici (FOV)

L'esperienza utente ben progettata può creare e gestire un contesto utile dell'ambiente virtuale che si estende intorno agli utenti. Attenuare l'effetto dei limiti di FOV implica una progettazione accurata della scalabilità del contenuto e del contesto, l'utilizzo di audio spaziale, i sistemi di linee guida e la posizione dell'utente. Se questa operazione è stata eseguita correttamente, l'utente risulterà meno disaccoppiato dai limiti di FOV, pur avendo un'esperienza di app comoda.

### <a name="device-impact"></a>Effetti sul dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criteri di qualità

|  Consigliate  |  Soddisfi |  Esito negativo |
--- | --- | ---
|  L'utente non perde mai il contesto e la visualizzazione è confortevole. Per gli oggetti di grandi dimensioni viene fornita assistenza del contesto. L'individuabilità e la visualizzazione delle linee guida vengono fornite per gli oggetti esterni al frame. In generale, la progettazione del movimento e la scala degli ologrammi sono appropriate per un'esperienza di visualizzazione confortevole. | L'utente non perde mai il contesto, ma potrebbe essere necessario un movimento del collo aggiuntivo in situazioni limitate. In situazioni limitate la scalabilità induce gli ologrammi a suddividere il frame verticale o orizzontale causando un movimento del collo per visualizzare gli ologrammi. | È necessario che l'utente perda il contesto e/o il movimento del collo coerente per visualizzare gli ologrammi. Nessuna guida al contesto per oggetti olografici di grandi dimensioni, spostamento di oggetti facili da perdere al di fuori del frame senza alcuna indicazione di individuabilità, o ologrammi alti richiede un movimento del collo normale per la visualizzazione. | 

### <a name="how-to-measure"></a>Come misurare

* Il contesto di un ologramma (grande) viene perso o non è compreso perché viene troncato ai limiti.
* La posizione degli ologrammi è difficile da trovare a causa dell'assenza di direttori di attenzione o contenuti che si spostano rapidamente all'interno e all'esterno del frame olografico.
* Per visualizzare completamente un ologramma, è necessario che lo scenario sia normale e ripetitivo, in modo da ottenere una riduzione del collo.

### <a name="recommendations"></a>Consigli

* Inizia l'esperienza con piccoli oggetti che si adattano a FOV, quindi passa con segnali visivi a versioni più grandi.
* Usare i direttori audio e di attenzione spaziali per aiutare l'utente a trovare contenuto esterno a FOV.
* Per quanto possibile, evitare gli ologrammi che ritagliano verticalmente il FOV.
* Fornire all'utente informazioni aggiuntive in-app per una migliore visualizzazione del percorso.

### <a name="resources"></a>Risorse

#### <a name="documentation"></a>Documentazione

* [Frame olografico](holographic-frame.md)
* [Case Study, informazioni sulla progettazione dell'interazione e dell'interfaccia utente di HoloStudio](case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [Scala di oggetti e ambienti](scale.md)
* [Cursori, segnali visivi](cursors.md#visual-cues)

#### <a name="external-references"></a>Riferimenti esterni

* [Molto ADO sulla FOV](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a>Il contenuto reagisce alla posizione dell'utente

Gli ologrammi dovrebbero rispondere alla posizione dell'utente approssimativamente nello stesso modo in cui fanno gli oggetti "reali". Una considerazione di progettazione notevole è rappresentata dagli elementi dell'interfaccia utente che non possono necessariamente presupporre che la posizione di un utente sia stazionaria e adattata al movimento dell'utente. La progettazione di un'app che si adatta correttamente alla posizione utente creerà un'esperienza più credibile e ne renderà più semplice l'uso.

### <a name="device-impact"></a>Effetti sul dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criteri di qualità

<table>
<tr>
<td> Consigliate </td><td> Il contenuto e l'interfaccia utente si adattano a posizioni utente che consentono all'utente di interagire naturalmente con il contenuto nell'ambito del movimento utente previsto.</td>
</tr><tr>
<td> Soddisfi </td><td> L'interfaccia utente si adatta alla posizione dell'utente, ma può impedire la visualizzazione del contenuto della chiave che richiede all'utente di modificare la posizione.</td>
</tr><tr>
<td> Esito negativo </td><td><ol>
<li>Gli elementi dell'interfaccia utente vengono persi o bloccati durante lo spostamento, facendo sì che l'utente ritorni in modo non naturale ai controlli (o trova).</li><li>Gli elementi dell'interfaccia utente limitano la visualizzazione del contenuto primario.</li><li>Lo spostamento dell'interfaccia utente non è ottimizzato per la visualizzazione della distanza e del momento in particolare con elementi dell'interfaccia utente con <a href="billboarding-and-tag-along.md">tag lungo</a> .</li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a>Come misurare

* Tutte le misurazioni devono essere eseguite in un ambito ragionevole dello scenario. Sebbene lo spostamento dell'utente possa variare, non provare a ingannare l'app con lo spostamento estremo dell'utente.
* Per gli elementi dell'interfaccia utente, i controlli pertinenti dovrebbero essere disponibili indipendentemente dallo spostamento dell'utente. Se, ad esempio, l'utente Visualizza e aggira una mappa 3D con lo zoom, il controllo zoom dovrebbe essere prontamente disponibile per l'utente indipendentemente dalla posizione.

### <a name="recommendations"></a>Consigli

* L'utente è la fotocamera e controlla lo spostamento. Consentire l'unità.
* Prendere in considerazione il tabellone per i sistemi di testo e di menu che altrimenti sarebbero bloccati o nascosti se un utente dovesse spostarsi.
* Usare tag-along per il contenuto che deve seguire l'utente, consentendo allo stesso tempo all'utente di vedere cosa è davanti a essi.

### <a name="resources"></a>Risorse

#### <a name="documentation"></a>Documentazione

* [Progettazione interazione](hologram.md)
* [Colore, luce e materiale](color,-light-and-materials.md)
* [Billboarding e tag-along](billboarding-and-tag-along.md)
* [Interazioni istintive](interaction-fundamentals.md)
* [Auto-Motion e locomozione utente](comfort.md#self-motion-and-user-locomotion)

#### <a name="tools-and-tutorials"></a>Strumenti ed esercitazioni

* [Input MR 210: sguardo](holograms-210.md)

## <a name="input-interaction-clarity"></a>Chiarezza interazione input

La chiarezza dell'interazione di input è essenziale per l'usabilità di un'app e include coerenza di input, accessibilità, individuabilità dei metodi di interazione. L'utente deve essere in grado di usare interazioni comuni a livello di piattaforma senza riapprendere. Se l'app ha un input personalizzato, dovrebbe essere chiaramente comunicata e dimostrata.

### <a name="device-impact"></a>Effetti sul dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criteri di qualità

|  Consigliate  |  Soddisfi |  Esito negativo |
--- | --- | ---
|  I metodi di interazione di input sono coerenti con le [linee guida](interaction-fundamentals.md)fornite dalla realtà mista Windows. Qualsiasi input personalizzato non deve essere ridondante con l'input standard (usare invece l'interazione standard) e deve essere chiaramente comunicato e dimostrato all'utente. | Analogamente al migliore, ma gli input personalizzati sono ridondanti con i metodi di input standard. L'utente può comunque raggiungere l'obiettivo e progredire nell'esperienza dell'app. | Difficile comprensione del metodo di input o del mapping dei pulsanti. L'input è molto personalizzato, non supporta l'input standard, nessuna istruzione o probabilmente causa problemi di affaticamento e comfort. | 

### <a name="how-to-measure"></a>Come misurare

* L'app usa [metodi di input standard coerenti.](interaction-fundamentals.md)
* Se l'app ha un input personalizzato, viene chiaramente comunicata tramite:
* Esperienza di prima esecuzione
* Schermate introduttive
* Descrizioni comandi
* Coach mano
* Sezione della Guida
* Voice over

### <a name="recommendations"></a>Consigli

* Usare i metodi di input standard quando possibile.
* Fornire dimostrazioni, esercitazioni e descrizioni comandi per metodi di input non standard.
* Usare un modello di interazione coerente nell'app.

### <a name="resources"></a>Risorse

#### <a name="documentation"></a>Documentazione

* [Interazioni istintive](interaction-fundamentals.md)
* [Oggetti interagibili](interactable-object.md)
* [Puntamento con la testa e attesa](gaze-and-dwell.md)
* [Cursori](cursors.md)
* [Comodità e sguardo](comfort.md#gaze-direction)
* [Input vocale](voice-input.md)
* [Controller del movimento](motion-controllers.md)
* [Guida alla conversione dell'input per Unity](input-porting-guide-for-unity.md)
* [Input da tastiera in Unity](keyboard-input-in-unity.md)
* [Sguardo fisso in Unity](gaze-in-unity.md)
* [Movimenti e controller del movimento in Unity](gestures-and-motion-controllers-in-unity.md)
* [Input vocale in Unity](voice-input-in-unity.md)
* [Input da tastiera, mouse e controller in DirectX](keyboard,-mouse,-and-controller-input-in-directx.md)
* [Puntamento con la testa e sguardo fisso in DirectX](gaze-in-directx.md)
* [Mani e controller del movimento in DirectX](hands-and-motion-controllers-in-directx.md)
* [Input vocale in DirectX](voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a>Strumenti ed esercitazioni

* [Case Study: ricerca di più personal computing](case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [Cast Study: apprendimento dell'interfaccia utente e della progettazione dell'interazione HoloStudio](case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [App di esempio: tabella periodica degli elementi](periodic-table-of-the-elements.md)
* [App di esempio: modulo Lunar](lunar-module.md)
* [Input MR 210: sguardo](holograms-210.md)
* [Input MR 211: movimenti](holograms-211.md)
* [Input di MR 212: Voice](holograms-212.md)

## <a name="interactable-objects"></a>Oggetti interagibili

Un pulsante è a lungo una metafora usata per attivare un evento nel mondo astratto 2D. Nel mondo della realtà mista tridimensionale, non dobbiamo più limitarci a questo mondo dell'astrazione. Qualsiasi elemento può essere un oggetto interagibile che attiva un evento. Un oggetto interactabile può essere rappresentato da qualsiasi elemento da un caffè della tabella a un pallone in aria. Indipendentemente dal modulo, gli oggetti interagiscono devono essere chiaramente riconoscibili dall'utente tramite segnali visivi e audio.

### <a name="device-impact"></a>Effetti sul dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criteri di qualità

|  Consigliate  |  Soddisfi |  Esito negativo |
--- | --- | ---
|  Indipendentemente dalla forma, gli oggetti interagibili sono riconoscibili tramite segnali visivi e audio in tre stati: inattivo, di destinazione e selezionato. "Vedilo, supponiamo che" sia chiaro e costantemente usato in tutta l'esperienza. Gli oggetti vengono ridimensionati e distribuiti per consentire la destinazione senza errori. | L'utente può riconoscere l'oggetto come interagisci tramite commenti audio o visivi e può fare riferimento all'oggetto e attivarlo. | Dato che non sono presenti suggerimenti visivi o audio, l'utente non può riconoscere un oggetto interagibile. Le interazioni sono soggette a errori a causa della scala o della distanza degli oggetti tra oggetti. | 

### <a name="how-to-measure"></a>Come misurare

* Gli oggetti interagibili sono riconoscibili come ' interactable '; inclusi i pulsanti, i menu e il contenuto specifico dell'app. Come regola empirica, è necessario un segnale visivo e un segnale audio quando la destinazione è costituita da oggetti interagibili.

### <a name="recommendations"></a>Consigli

* Usare commenti visivi e audio per le interazioni.
* Il feedback visivo deve essere differenziato per ogni stato di input (inattivo, mirato, selezionato)
* Gli oggetti interagibili devono essere ridimensionati e posizionati per la destinazione senza errori.
* Gli oggetti interagiscono raggruppati, ad esempio una barra dei menu o un elenco, devono avere la spaziatura corretta per la destinazione.
* I pulsanti e i menu che supportano il comando Voice devono fornire etichette di testo per la parola chiave Command ("vedere, Say it")

### <a name="resources"></a>Risorse

#### <a name="documentation"></a>Documentazione

* [Oggetto che supporta interazioni](interactable-object.md)
* [Testo in Unity](text-in-unity.md)
* [Rettangolo di selezione e barra dell'app](app-bar-and-bounding-box.md)
* [Input vocale](voice-input.md)

#### <a name="tools-and-tutorials"></a>Strumenti ed esercitazioni

* [Toolkit per realtà mista-UX](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a>Analisi chat room

Le app che richiedono dati di mapping spaziale si basano sul dispositivo per raccogliere automaticamente questi dati nel tempo e nelle sessioni mentre l'utente Esplora il proprio ambiente con il dispositivo attivo. La completezza e la qualità di questi dati dipendono da diversi fattori, tra cui la quantità di esplorazione eseguita dall'utente, il tempo trascorso dall'esplorazione e l'eventuale spostamento degli oggetti, ad esempio mobili e porte, dal momento in cui il dispositivo ha analizzato l'area. Molte app analizzeranno i dati di mapping spaziali all'inizio dell'esperienza per valutare se l'utente deve eseguire passaggi aggiuntivi per migliorare la completezza e la qualità della mappa spaziale. Se l'utente deve analizzare l'ambiente, è necessario fornire indicazioni chiare durante l'esperienza di analisi.

### <a name="device-impact"></a>Effetti sul dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criteri di qualità

|  Consigliate  |  Soddisfi |  Esito negativo |
--- | --- | ---
|  La visualizzazione della mesh spaziale indica che è in corso l'analisi degli utenti. L'utente sa chiaramente cosa fare e quando l'analisi viene avviata e arrestata. | Viene fornita la visualizzazione della mesh spaziale, ma l'utente potrebbe non sapere chiaramente cosa fare e non viene fornita alcuna informazione sullo stato di avanzamento. | Nessuna visualizzazione della rete mesh. Non sono disponibili informazioni aggiuntive per l'utente in merito alla posizione in cui eseguire l'analisi o all'avvio o all'arresto dell'analisi. |

### <a name="how-to-measure"></a>Come misurare

* Durante un'analisi dello spazio richiesto, viene fornita una guida visiva e audio che indica il punto di ricerca e quando avviare e arrestare l'analisi.

### <a name="recommendations"></a>Consigli

* Indicare la quantità di volume totale in prossimità degli utenti che deve far parte dell'esperienza.
* Comunica quando l'analisi viene avviata e interrotta, ad esempio un indicatore di stato.
* Usare una visualizzazione della mesh durante l'analisi.
* Fornire indicazioni visive e audio per invitare l'utente a cercare e spostarsi in una stanza.
* Informare l'utente della posizione per migliorare i dati. In molti casi, può essere preferibile informare l'utente di cosa è necessario fare (ad esempio, osservare il soffitto, guardare dietro la mobilia), per ottenere la qualità di analisi necessaria.

### <a name="resources"></a>Risorse

#### <a name="documentation"></a>Documentazione

* [Visualizzazione della scansione dello spazio](room-scan-visualization.md)
* [Case Study: espansione delle funzionalità di mapping spaziale di HoloLens](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [Case Study: progettazione di suoni spaziali per HoloTour](case-study-spatial-sound-design-for-holotour.md)
* [Case Study: creazione di un'esperienza immersiva nei frammenti](case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a>Strumenti ed esercitazioni

* [Toolkit per realtà mista-UX](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a>Indicatori direzionali

In un'app di realtà mista, il contenuto può essere esterno al campo di visualizzazione o bloccato da oggetti reali. Un'app ben progettata renderà più semplice per l'utente trovare contenuto non visibile. Gli indicatori direzionali segnalano a un utente un contenuto importante e forniscono indicazioni sul contenuto relativo alla posizione dell'utente. Le linee guida per il contenuto non visibile possono assumere la forma di emettitori di suoni, frecce direzionali o segnali visivi diretti.

### <a name="device-impact"></a>Effetti sul dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criteri di qualità

|  Consigliate  |  Soddisfi |  Esito negativo |
--- | --- | ---
|  I suggerimenti visivi e audio indirizzano direttamente l'utente al contenuto pertinente al di fuori del campo di visualizzazione. | Una freccia o un indicatore che punta l'utente nella direzione generale del contenuto. | Il contenuto pertinente non è compreso nel campo di visualizzazione e non è stata fornita alcuna indicazione per la posizione dell'utente. | 

### <a name="how-to-measure"></a>Come misurare

* Il contenuto pertinente al di fuori del campo di visualizzazione utente può essere individuato tramite segnali visivi e/o audio.

### <a name="recommendations"></a>Consigli

* Quando il contenuto pertinente è esterno al campo di visualizzazione dell'utente, usare indicatori direzionali e segnali audio per guidare l'utente nel contenuto. In molti casi, è preferibile una guida visiva diretta sulle frecce direzionali.
* Gli indicatori direzionali non devono essere incorporati nel cursore.

### <a name="resources"></a>Risorse

* [Frame olografico](holographic-frame.md)

## <a name="data-loading"></a>Caricamento dati

Un controllo di stato fornisce all'utente un feedback nel caso in cui sia in corso un'operazione di lunga durata. Questo può significare che l'utente non può interagire con l'app quando l'indicatore di stato è visibile e può anche indicare la durata del tempo di attesa.

### <a name="device-impact"></a>Effetti sul dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criteri di qualità

|  Consigliate  |  Soddisfi |  Esito negativo |
--- | --- | ---
|  Indicatore visivo animato, sotto forma di indicatore di stato o anello, che mostra lo stato di avanzamento durante il caricamento o l'elaborazione dei dati. L'indicatore visivo fornisce indicazioni sulla durata dell'attesa. | L'utente viene informato che è in corso il caricamento dei dati, ma non è presente alcuna indicazione del tempo di attesa. | Nessun indicatore di caricamento o elaborazione dei dati per l'attività richiede più di 5 secondi. |

### <a name="how-to-measure"></a>Come misurare

* Durante il caricamento dei dati, verificare che non sia presente alcuno stato vuoto per più di 5 secondi.

### <a name="recommendations"></a>Consigli

* Fornire un'animazione per il caricamento dei dati che mostra lo stato di avanzamento in qualsiasi situazione in cui l'utente può percepire che l'app è bloccata o arrestata in modo anomalo. Una regola empirica ragionevole è l'attività di caricamento che può richiedere più di 5 secondi.

### <a name="resources"></a>Risorse

* [Visualizzazione dello stato](progress.md)

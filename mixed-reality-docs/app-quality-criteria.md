---
title: Criteri di qualità delle App
description: Questo documento descrive i principali fattori influiscono sulla qualità delle app di realtà mista.
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: criteri di qualità delle App, realtà mista mista app per realtà
ms.openlocfilehash: 8e635585c0981d81bf71fb5577232af28f2a0fdd
ms.sourcegitcommit: 150d258a23130026c8792da383a3993657841fb4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67024490"
---
# <a name="app-quality-criteria"></a>Criteri di qualità delle App

Questo documento descrive i principali fattori influiscono sulla qualità delle app di realtà mista. Per ogni fattore viene fornite le informazioni seguenti
* Panoramica: una breve descrizione del fattore di qualità e perché è importante.
* Impatto sul dispositivo - il tipo di dispositivo di realtà mista di finestra è stato interessato.
* Criteri di qualità – come valutare il fattore di qualità.
* Viene descritto come misurare: metodi per misurare il problema (o esperienza).
* Recommendations di riepilogo degli approcci per offrire una migliore esperienza utente.
* Risorse: sviluppatore pertinenti e le risorse di progettazione che sono utili per creare esperienze migliori app.

## <a name="frame-rate"></a>Frequenza dei fotogrammi

Frequenza dei fotogrammi è il primo pilastro dello ologrammi stabilità comodità per l'utente. Frequenza dei fotogrammi sotto le destinazioni consigliate può causare vntana visualizzazione instabilità, non hanno conseguenze negative believability dell'esperienza e causando potenzialmente la fatica sotto controllo. La frequenza dei fotogrammi destinazione per la tua esperienza sul auricolari coinvolgenti di realtà mista di Windows sarà 60Hz o 90Hz, a seconda di quale misto realtà compatibile con i PC Windows che si desidera supportare. Per HoloLens la frequenza dei fotogrammi di destinazione è 60Hz.

### <a name="device-impact"></a>Impatto di dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Auricolari coinvolgenti</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criteri di qualità

|  Migliore  |  Soddisfa |  esito negativo |
--- | --- | ---
| L'app risponde in modo coerente fotogrammi al secondo obiettivo (FPS) per il dispositivo di destinazione: 60fps su HoloLens; fps 90 nei PC extra; e 60fps nei PC "Mainstream". | L'app ha cadute cornice intermittente non ostacolare l'esperienza di base; oppure FPS è regolarmente inferiori a obiettivo desiderato, ma non impedisca l'esperienza delle app. | L'app sta riscontrando un calo di frequenza dei fotogrammi in Media ogni dieci secondi o meno. |

### <a name="how-to-measure"></a>Consente di misurare

* Un grafico di frequenza fotogrammi in tempo reale, è possibile per il [Windows Device Portal](using-the-windows-device-portal.md#system-performance) sotto "Le prestazioni del sistema".
* Per il debug, sviluppo aggiungere un contatore di diagnostica di frequenza di frame nell'app. Per un contatore di esempio, vedere le risorse.
* Frame velocità scende possono presentarsi nelle dispositivo mentre l'app è in esecuzione tramite lo spostamento di head da un lato a altro. Se l'ologrammi Mostra lo spostamento di instabilità imprevisto, quindi a bassa frequenza dei fotogrammi o il piano di stabilità è probabilmente la causa.

### <a name="recommendations"></a>Consigli

* Aggiungere un contatore di frequenza fotogrammi all'inizio del lavoro di sviluppo.
* Le modifiche che comportano una riduzione della frequenza dei fotogrammi dovrebbero valutare e risolvere in modo appropriato come un bug nelle prestazioni.

### <a name="resources"></a>Risorse

#### <a name="documentation"></a>Documentazione

* [Ottenere informazioni sulle prestazioni per realtà mista](understanding-performance-for-mixed-reality.md)
* [Frequenza dei fotogrammi e la stabilità di ologramma](hologram-stability.md#frame-rate)
* [Budget di prestazioni di asset](asset-creation-process.md)
* [Consigli sulle prestazioni per Unity](performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a>Strumenti ed esercitazioni

* [MRToolkit, visualizzazione contatore FPS](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [MRToolkit, gli shader](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a>Riferimenti esterni

* [Unity, ottimizzazione delle applicazioni per dispositivi mobili](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a>Stabilità ologrammi

Ologrammi stabile verranno aumentare l'usabilità e believability dell'app e creare un'esperienza di visualizzazione più a proprio agio per l'utente. La qualità della stabilità ologrammi è il risultato dello sviluppo di app valida e la capacità del dispositivo per comprendere (traccia) relativo ambiente. Frequenza dei fotogrammi è il primo pilastro della stabilità, altri fattori possono influire sulle stabilità tra cui:

* Uso del piano di stabilizzazione
* Distanza agli ancoraggi spaziali
* Rilevamento

### <a name="device-impact"></a>Impatto di dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Auricolari coinvolgenti</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criteri di qualità

|  Migliore  |  Soddisfa |  esito negativo |
--- | --- | ---
|  Ologrammi continuano ad apparire stabile. | Contenuto secondario presenta lo spostamento imprevisto. o spostamento imprevisto non influire esperienza app complessiva. | Il contenuto principale nel frame presenta movimento imprevisto. |

### <a name="how-to-measure"></a>Consente di misurare

Mentre l'usura del dispositivo e l'esperienza di visualizzazione:

* Spostare l'head da un lato a altro, se il vntana indicano lo spostamento dei imprevisto quindi a bassa frequenza dei fotogrammi o allineamento non corretta del piano di stabilità a piano focale è la causa più probabile.
* Spostare l'ambiente e vntana, cercare i comportamenti, ad esempio nuoto e jumpiness. Questo tipo di movimento è probabilmente causato dal dispositivo senza il rilevamento dell'ambiente o la distanza in base all'ancoraggio spaziale.
* Se è grande o più vntana è nel frame, osservare il comportamento di ologramma profondità diverse durante lo spostamento alla posizione di head da un lato a altro, se viene visualizzato bruschi è probabilmente causato dal piano di stabilizzazione.

### <a name="recomendations"></a>Consigli sulla

* Aggiungere un contatore di frequenza fotogrammi all'inizio del lavoro di sviluppo.
* Usare il piano di stabilizzazione.
* Eseguire sempre il rendering vntana ancorata all'interno di 3 misuratori del loro punto di ancoraggio.
* Assicurarsi che l'ambiente sia configurato per il rilevamento corretto.
* Progettare l'esperienza per evitare vntana a vari livelli di profondità focale all'interno del frame.

### <a name="resources"></a>Risorse

#### <a name="documentation"></a>Documentazione

* [Frequenza dei fotogrammi e la stabilità di ologramma](hologram-stability.md#frame-rate)
* [Case study, utilizzando il piano di stabilizzazione](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [Ottenere informazioni sulle prestazioni per realtà mista](understanding-performance-for-mixed-reality.md)
* [Consigli sulle prestazioni per Unity](performance-recommendations-for-unity.md)
* [Ancoraggi nello spazio](spatial-anchors.md)
* [Gestione degli errori di rilevamento](coordinate-systems.md#handling-tracking-errors)
* [Fotogramma di riferimento fisso](coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a>Strumenti ed esercitazioni

* [MR Companion Kit, Kinect IPD](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a>Posizione vntana su superfici reali

Disallineamenti di vntana con oggetti fisici (se deve essere posizionato in relazione a altra) è una chiara indicazione dell'unione non-ologrammi e reali. Accuratezza della posizione deve essere relativo alle esigenze dello scenario; ad esempio, posizionamento superficie generale può utilizzare il mapping spaziale, ma il posizionamento più preciso richiederanno utilizzato per scopi di calibrazione e marcatori.

### <a name="device-impact"></a>Impatto di dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Auricolari coinvolgenti</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criteri di qualità

|  Migliore  |  Soddisfa |  esito negativo |
--- | --- | ---
| Ologrammi Allinea all'area di in genere nei centimetri all'intervallo di pollici. Se è necessaria maggiore accuratezza, l'app deve fornire un mezzo efficiente per la collaborazione all'interno di specifica di app desiderata. | N/D | Il vntana vengono visualizzati non allineati con l'oggetto fisico di destinazione al piano della superficie di rilievo o spostata dall'area di visualizzazione. Se la precisione è necessaria, Vntana deve soddisfare le specifiche di prossimità dello scenario. | 

### <a name="how-to-measure"></a>Consente di misurare

* Vntana posizionati sulla mappa spaziale non deve essere visualizzati a float notevolmente di sopra o sotto l'area.
* Ologrammi che richiedono il posizionamento preciso devono avere una forma del marcatore e calibrazione sistema appropriata ai requisiti dello scenario.

### <a name="recommendations"></a>Consigli

* Mapping spaziale è utile per l'inserimento di oggetti su superfici quando la precisione non è obbligatoria.
* Per la precisione migliore, utilizzare gli indicatori o poster per impostare gli ologrammi e un controller Xbox (o un meccanismo di allineamento manuale) per calibrazione finale.
* È consigliabile suddividere vntana molto grande in parti logiche e allineamento di ogni parte all'area di.
* In modo non corretto distanza interpupilary set (IPD) può influire inoltre allineamento ologramma. Configurare sempre HoloLens a IPD dell'utente.

### <a name="resources"></a>Risorse

#### <a name="documentation"></a>Documentazione

* [Posizionamento di mapping spaziale](spatial-mapping.md#placement)
* [Spazio di processo di digitalizzazione](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [Procedure consigliate Anchor spaziali](spatial-anchors.md#best-practices)
* [Gestione degli errori di rilevamento](coordinate-systems.md#handling-tracking-errors)
* [Mapping spaziale in Unity](spatial-mapping-in-unity.md)
* [Panoramica dello sviluppo Vuforia](vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a>Strumenti ed esercitazioni

* [Spaziale MR 230: Mapping spaziale](holograms-230.md)
* [MR Toolkit, le librerie di Mapping spaziale](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [MR Companion Kit, Poster Calibration Sample](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [MR Companion Kit, Kinect IPD](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a>Riferimenti esterni

* [Lowes Case Study, l'allineamento di precisione](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a>Area di visualizzazione del fattore di comfort

Controllo App per gli sviluppatori in cui eseguire la convergenza occhi degli utenti inserendo il contenuto e vntana profondità diversi. Gli utenti che portano HoloLens permetteranno sempre a m 2.0 per mantenere un'immagine chiara in quanto consente di visualizzare HoloLens sono fissati a una distanza ottica circa 2.0m lontano dall'utente. Profondità del contenuto non corretto può causare disturbo visual o fatica.

### <a name="device-impact"></a>Impatto di dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Auricolari coinvolgenti</strong></a></td>
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
<td> Migliore </td><td><ul>
<li>Collocare il contenuto a 2 minuti.</li><li>Quando non è possibile inserire vntana 2M e non è possibile evitare conflitti tra la convergenza e alloggio, la zona ottima per la selezione host ologrammi è compreso tra m 1,25 e 5 minuti.</li><li>In ogni caso, le finestre di progettazione deve strutturare il contenuto per incoraggiare gli utenti di interagire 1 + metri (ad esempio, regolare le dimensioni del contenuto e i parametri di selezione host predefiniti).</li><li>A meno che specificamente non è necessario per lo scenario, un piano di ritaglio debba essere implementare con fadeout iniziando in corrispondenza di 1 milione.</li><li>Nei casi in cui è necessario più da vicino osservazione di ologramma ovvero, il contenuto non deve essere inferiore a quello di 50cm.</li>
</ul></td>
</tr><tr>
<td> Soddisfa</td><td> Il contenuto è entro le indicazioni di visualizzazione e animazione, ma un utilizzo improprio o alcun utilizzo del piano di ritaglio.</td>
</tr><tr>
<td> esito negativo </td><td> Il contenuto viene visualizzato troppo vicino (in genere &lt;1.25 m e o &lt;50 cm per vntana fermo che richiedono più da vicino osservazione.)</td>
</tr>
</table>

### <a name="how-to-measure"></a>Consente di misurare

* Il contenuto deve in genere essere 2M away, ma non inferiore a quello di 1,25 o oltre 5 minuti.
* Con poche eccezioni, la distanza di rendering HoloLens ritaglio debba essere impostata su .85CM con fadeout del contenuto, iniziando in corrispondenza di 1 milione. Raggiungono il contenuto e notare l'effetto di piano di ritaglio.
* Contenuto fisso non deve essere inferiore a quello di 50cm da subito.

### <a name="recommendations"></a>Consigli

* Progettare il contenuto per la visualizzazione ottimale distanza di 2 minuti.
* Impostare la distanza di rendering ritaglio a 85cm con fadeout del contenuto, iniziando in corrispondenza di 1 milione.
* Per vntana fermo che devono visualizzare più vicino, il piano di ritaglio debba essere non supera i 30cm e fadeout deve iniziare almeno 10cm dal piano di ritaglio.

### <a name="resources"></a>Risorse

* [Eseguire il rendering di distanza](hologram-stability.md#hologram-render-distances)
* [Punto focale in Unity](focus-point-in-unity.md)
* [Esperimenti con scala](scale.md#experimenting-with-scale)
* [Testo, la dimensione del carattere consigliato](typography.md#recommended-font-size)

## <a name="depth-switching"></a>Cambio di profondità

Indipendentemente dall'area di visualizzazione dei problemi di fattore di comfort, richiede all'utente di cambiare frequentemente o rapidamente tra vicino e lontano focale oggetti (inclusi ologrammi e il contenuto reale) possono causare fatica oculomotor e disturbo generale.

### <a name="device-impact"></a>Impatto di dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Auricolari coinvolgenti</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criteri di qualità

|  Migliore  |  Soddisfa |  esito negativo |
--- | --- | ---
|  Profondità naturale o limitato cambio che non causa l'utente a e innaturali reimpostare lo stato attivo. | Profondità improvviso si tratta di core e progettata nell'esperienza delle app, profondità improvviso switch o che sia causato dal contenuto del mondo reale imprevisto. | Opzione profondità coerente, o profondità improvviso cambio che non è necessaria o core per l'esperienza delle app. | 

### <a name="how-to-measure"></a>Consente di misurare

* Se l'app richiede all'utente in modo coerente e/o in modo anomalo cambiare lo stato attivo di profondità, sussiste profondità cambio problema.

### <a name="recommendations"></a>Consigli

* Mantenere il contenuto principale a un piano focale coerente e assicurarsi che il piano di stabilizzazione corrisponda al piano focale. Ciò può ridurre fatica oculomotor e dello spostamento ologrammi imprevisto.

### <a name="resources"></a>Risorse

* [Eseguire il rendering di distanza](hologram-stability.md#hologram-render-distances)
* [Punto focale in Unity](focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a>Utilizzo dell'audio spaziale

Nella realtà mista di Windows, il motore di audio fornisce il componente acustico dell'esperienza di realtà mista simulando 3D audio con simulazioni ambientali, distanza e direzione. Utilizzando spaziale audio in un'applicazione consente agli sviluppatori di inserire convincente suoni in uno spazio dimensionale 3 (sfera) per l'utente. Tali suoni risulterà quindi come se provenienti da oggetti fisici reali o vntana la realtà mista nelle vicinanze dell'utente. Spaziale audio è uno strumento potente per full immersion, accessibilità e progettazione dell'esperienza utente nelle applicazioni di realtà mista.

### <a name="device-impact"></a>Impatto di dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Auricolari coinvolgenti</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criteri di qualità

|  Migliore  |  Soddisfa |  esito negativo |
--- | --- | ---
|  Audio è logicamente spatialized e l'esperienza utente in modo appropriato Usa suono per assistere con feedback utente e di individuazione oggetti. Audio è naturale e pertinenti agli oggetti e normalizzati tra lo scenario. | Spaziale audio è utilizzata in modo appropriato per believability ma mancante come mezzo per facilitare l'individuazione e commenti degli utenti. | File audio non è spatialized come previsto, e/o mancanza di suono per assistere l'utente entro l'esperienza utente. O audio spaziale non è stato considerato o la progettazione dello scenario. | 

### <a name="how-to-measure"></a>Consente di misurare

* In generale, suoni rilevanti devono creare da vntana destinazione (ad es., suono cortecce provenienti da holographic dog.)
* Segnali audio devono essere usate in tutta l'esperienza utente per assistere l'utente con commenti e suggerimenti né la conoscenza delle azioni all'esterno della cornice holographic.

### <a name="recommendations"></a>Consigli

* Usare spaziale audio quale supporto per interfacce utente e di individuazione dell'oggetto.
* Suoni reale funzionano meglio synthesize o file audio non naturale.
* La maggior parte dei suoni dovrebbero essere spatialized.
* Evitare di istanze di emissione FixIt invisibile.
* Evitare di mascheramento spaziale.
* Normalizza tutti i file audio.

### <a name="resources"></a>Risorse

#### <a name="documentation"></a>Documentazione

* [Audio spaziale](spatial-sound.md)
* [Progettazione dell'audio spaziale](spatial-sound-design.md)
* [Audio spaziale in Unity](spatial-sound-in-unity.md)
* [Case study, spaziali audio per HoloTour](case-study-spatial-sound-design-for-holotour.md)
* [Case study, utilizzando spaziale audio in RoboRaid](case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a>Strumenti ed esercitazioni

* [Spaziale MR 220: Audio spaziale](holograms-220.md)
* [MRToolkit, Spatial Audio](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a>Concentrarsi sui limiti holographic frame (campo di visualizzazione)

Esperienze utente ben progettata possono creare e gestire un contesto utile dell'ambiente virtuale che si estende sugli utenti. Ridurre l'effetto dei limiti del campo di visualizzazione comporta una progettazione attenta della scala del contenuto e contesto, l'uso di spaziale audio, sistemi di informazioni aggiuntive e la posizione dell'utente. Se eseguita correttamente, l'utente si sentirà che minore danneggiare i limiti del campo di visualizzazione mantenendo un'esperienza app familiarità.

### <a name="device-impact"></a>Impatto di dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Auricolari coinvolgenti</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criteri di qualità

|  Migliore  |  Soddisfa |  esito negativo |
--- | --- | ---
|  Utente non perde mai contesto e la visualizzazione è comodo. Assistenza rapida è disponibile per gli oggetti di grandi dimensioni. L'individuazione e visualizzazione di indicazioni viene fornito per gli oggetti all'esterno della cornice. In generale, progettazione di movimento e la scala del vntana sono appropriati per una visualizzazione ottimale. | Utente non perde mai il contesto, ma movimento collo aggiuntivo potrebbe essere necessario in casi limitati. In alcune situazioni scalabilità comporta interrompere sia il frame verticale o orizzontale provocando alcuni movimenti collo visualizzare ologrammi vntana. | È necessario visualizzare vntana utente potrebbe causare una perdita di contesto e/o movimento collo coerente. Alcuna indicazione di contesto per gli oggetti grandi holographic, lo spostamento di oggetti facile perdere all'esterno della cornice senza informazioni aggiuntive di individuabilità o vntana altezza non richiede movimento collo regolari da visualizzare. | 

### <a name="how-to-measure"></a>Consente di misurare

* Contesto per ologramma (grande) viene smarrito o non riconosciuto a causa di verrà ritagliato in base ai bordi.
* Posizione del vntana sono difficili da individuare a causa della mancanza di casting di attenzione o contenuto che si sposta rapidamente da e verso il frame holographic.
* Scenario è necessario regolare e ripetitive su e giù head movimento per verificare completamente ologramma conseguente fatica collo.

### <a name="recommendations"></a>Consigli

* L'esperienza di avvio con oggetti di piccole dimensioni che adatta il campo di visualizzazione, quindi eseguire la transizione con indicatori visivi alle versioni più grande.
* Usare directors spaziali audio e attenzione per la ricerca di contenuto utente che non è compreso il campo di visualizzazione.
* Per quanto possibile, evitare vntana che tagliano verticalmente il campo di visualizzazione.
* Fornire all'utente indicazioni nell'app per la miglior visualizzazione del percorso.

### <a name="resources"></a>Risorse

#### <a name="documentation"></a>Documentazione

* [Frame olografico](holographic-frame.md)
* [Case Study, HoloStudio UI e conoscenze di progettazione di interazione](case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [Scalabilità degli oggetti e gli ambienti](scale.md)
* [Cursori, segnali visivi](cursors.md#visual-cues)

#### <a name="external-references"></a>Riferimenti esterni

* [Molto discussi sul campo di visualizzazione](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a>Contenuto reagisce all'utente di posizionare

Ologrammi devono reagire in all'utente di posizionare in approssimativamente stesso modo in cui si "reali" oggetti. Una considerazione di progettazione rilevanti è elementi dell'interfaccia utente che non sono necessariamente presuppongono che la posizione dell'utente è fermo e adattare al movimento dell'utente. Progettazione di un'app che si adatti correttamente alla posizione utente crea un'esperienza più credibile e rendono più semplice da utilizzare.

### <a name="device-impact"></a>Impatto di dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Auricolari coinvolgenti</strong></a></td>
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
<td> Migliore </td><td> Il contenuto e interfaccia utente di adattarsi alle posizioni utente consentendo utente interagiscono in modo naturale con contenuto all'interno dell'ambito dello spostamento previsto per l'utente.</td>
</tr><tr>
<td> Soddisfa </td><td> Interfaccia utente adatta per la posizione dell'utente, ma potrebbe impedire la visualizzazione del contenuto della chiave che richiedono all'utente di modificare la loro posizione.</td>
</tr><tr>
<td> esito negativo </td><td><ol>
<li>Elementi dell'interfaccia utente vengono perse o bloccati durante dell'utente che provocano lo spostamento dei controlli e innaturali tornare al (o trovare).</li><li>Elementi dell'interfaccia utente limitano la visualizzazione del contenuto principale.</li><li>Lo spostamento dell'interfaccia utente non è ottimizzato per la visualizzazione di distanza e in particolare con momentum <a href="billboarding-and-tag-along.md">tag-along</a> elementi dell'interfaccia utente.</li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a>Consente di misurare

* Tutte le misure devono essere eseguite all'interno di un ambito ragionevole dello scenario. Durante lo spostamento di utente variano, non provano a ingannare l'app con spostamento utente estremi.
* Per gli elementi dell'interfaccia utente, controlli rilevanti devono essere disponibili indipendentemente dal movimento utente. Ad esempio, se l'utente è la visualizzazione e analisi attorno una mappa 3D con zoom, il controllo zoom deve essere immediatamente disponibile per l'utente indipendentemente dalla posizione.

### <a name="recommendations"></a>Consigli

* L'utente è la fotocamera e controllano lo spostamento. "Let" tali unità.
* Prendere in considerazione del billboard per testo e i sistemi consente in caso contrario, potrebbero essere bloccato world o nascosta se un utente sono stati da spostare.
* Usare tag-along per il contenuto deve seguire l'utente pur senza impedire all'utente di visualizzare gli elementi davanti a essi.

### <a name="resources"></a>Risorse

#### <a name="documentation"></a>Documentazione

* [Progettazione di interazioni](hologram.md)
* [Colore, chiaro e materiale](color,-light-and-materials.md)
* [Billboarding e tag-along](billboarding-and-tag-along.md)
* [Interazioni istintive](interaction-fundamentals.md)
* [Self-animati e locomotion utente](comfort.md#self-motion-and-user-locomotion)

#### <a name="tools-and-tutorials"></a>Strumenti ed esercitazioni

* [Input MR 210: Sguardo fisso](holograms-210.md)

## <a name="input-interaction-clarity"></a>Maggiore chiarezza l'interazione dell'input

L'interazione di input maggiore chiarezza è fondamentale per l'usabilità dell'app e include input coerenza, approachability, l'individuabilità dei metodi di interazione. Utente sarà in grado di utilizzare le interazioni comuni a livello di piattaforma senza un apprendimento. Se l'app ha input personalizzato, deve essere chiaramente comunicato e dimostrato.

### <a name="device-impact"></a>Impatto di dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Auricolari coinvolgenti</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criteri di qualità

|  Migliore  |  Soddisfa |  esito negativo |
--- | --- | ---
|  Metodi di interazione di input siano coerenti con realtà mista di Windows fornito [materiale sussidiario](interaction-fundamentals.md). Qualsiasi input personalizzato non deve essere ridondante con input standard (piuttosto utilizzo interazione standard) e deve essere chiaramente comunicato e illustrato all'utente. | Analogamente agli input migliori, ma personalizzato sono ridondanti con metodi di input standard. Utente ancora possibile ottenere l'obiettivo e stato di avanzamento tramite l'esperienza delle app. | Difficile da comprendere il mapping di metodo o il pulsante di input. È altamente personalizzato, non supporta l'input standard, non le istruzioni, di input o può causare problemi di sollecitazioni e fattore di comfort. | 

### <a name="how-to-measure"></a>Consente di misurare

* L'app Usa coerente [metodi di input standard.](interaction-fundamentals.md)
* Se l'app ha input personalizzati, è chiaramente comunicata tramite:
* Prima esecuzione
* Schermate introduttive
* Descrizioni comandi
* Coach mano
* Sezione della Guida
* Voce su

### <a name="recommendations"></a>Consigli

* Usare i metodi di input standard, laddove possibile.
* Fornire le dimostrazioni, esercitazioni e le descrizioni comandi per i metodi di input non standard.
* Usare un modello di interazione coerente in tutta l'app.

### <a name="resources"></a>Risorse

#### <a name="documentation"></a>Documentazione

* [Interazioni istintive](interaction-fundamentals.md)
* [Oggetti si](interactable-object.md)
* [Puntamento con la testa e attesa](gaze-and-dwell.md)
* [Cursori](cursors.md)
* [Fattore di comfort e sguardo](comfort.md#gaze-direction)
* [Movimenti](gestures.md)
* [Input vocale](voice-input.md)
* [Esecuzione di comandi vocali](voice-design.md)
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

* [Case study: L'esercizio di elaborazione più personale](case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [Eseguire il cast di Studio: Insegnamenti di progettazione HoloStudio UI e l'interazione](case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [App di esempio: Tabella periodico degli elementi](periodic-table-of-the-elements.md)
* [App di esempio: Modulo lunare](lunar-module.md)
* [Input MR 210: Sguardo fisso](holograms-210.md)
* [Input MR 211: Movimenti](holograms-211.md)
* [Input MR 212: Voce](holograms-212.md)

## <a name="interactable-objects"></a>Oggetti si

Un pulsante già da tempo, una metafora utilizzata per l'attivazione di un evento in tutto il mondo astratto 2D. Nel mondo tridimensionale realtà mista, non dobbiamo riguardare esclusivamente questo mondo di astrazione più. Qualsiasi elemento può essere un oggetto si che attiva un evento. Un oggetto si può essere rappresentato come un elemento da una tazza di caffè sulla tabella in un fumetto mobile in modalità wireless. Indipendentemente dal formato, gli oggetti si devono essere chiaramente riconoscibili dall'utente tramite segnali audio e video.

### <a name="device-impact"></a>Impatto di dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Auricolari coinvolgenti</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criteri di qualità

|  Migliore  |  Soddisfa |  esito negativo |
--- | --- | ---
|  Indipendentemente dal form, gli oggetti si sono riconoscibili tramite segnali audio e video in tre stati: inattiva, destinati e selezionato. "A vederla, dice" è chiaro e coerente utilizzato nell'intera esperienza di. Gli oggetti vengono ridimensionati e distribuiti per consentire la destinazione è senza errori. | Utente può riconoscere oggetto come si grazie ai commenti di audio o oggetto visivo e di destinazione e attivare l'oggetto. | Non data segnali visivi o audio, utente in grado di riconoscere un oggetto si. Errore soggetta a causa di scala di oggetto o la distanza tra gli oggetti sono interazioni. | 

### <a name="how-to-measure"></a>Consente di misurare

* Gli oggetti si sono riconoscibili come 'si;' tra cui pulsanti, menu e app contenuto specifico. Come regola generale non vi sarà un segnale audio e video quando la destinazione si oggetti.

### <a name="recommendations"></a>Consigli

* Utilizzare commenti audio e video per le interazioni.
* Feedback visivo deve essere differenziate per ogni input dello stato (inattivo, destinazione, selezionato)
* Oggetti si devono essere ridimensionati e posizionati per la destinazione è senza errori.
* Gli oggetti raggruppati si (ad esempio una barra dei menu o elenco) devono avere spaziatura corretta per specificare come destinazione.
* I pulsanti e menu che supportano i comandi vocali devono fornire le etichette di testo per la parola chiave di comando ("visualizzarlo, dice")

### <a name="resources"></a>Risorse

#### <a name="documentation"></a>Documentazione

* [Oggetto che supporta interazioni](interactable-object.md)
* [Testo in Unity](text-in-unity.md)
* [Rettangolo di selezione e barra dell'app](app-bar-and-bounding-box.md)
* [Esecuzione di comandi vocali](voice-design.md)

#### <a name="tools-and-tutorials"></a>Strumenti ed esercitazioni

* [Toolkit di realtà mista - UX](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a>Chat room l'analisi

Le app che richiedono i dati di mapping spaziale si basano sul dispositivo per raccogliere automaticamente i dati nel tempo e tra le sessioni dell'utente esamina il proprio ambiente con il dispositivo attivo. La completezza e la qualità dei dati dipende da diversi fattori tra cui la quantità di esplorazione che l'utente ha eseguito, quanto tempo è trascorso l'esplorazione e se gli oggetti, ad esempio le porte e mobili hanno spostata dal momento che il dispositivo analizzato l'area. Molte App verranno analizzati i dati di mapping spaziale all'inizio dell'esperienza deve valutare se l'utente deve eseguire passaggi aggiuntivi per migliorare la qualità della mappa spaziale e la completezza. Se l'utente è necessario per analizzare l'ambiente, clear è necessario specificare informazioni aggiuntive durante l'esperienza di analisi.

### <a name="device-impact"></a>Impatto di dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Auricolari coinvolgenti</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criteri di qualità

|  Migliore  |  Soddisfa |  esito negativo |
--- | --- | ---
|  Visualizzazione della trama spaziale indicare agli utenti l'analisi sono in corso. Utente conosca in modo chiaro cosa fare e inizio e la fine dell'analisi. | Visualizzazione della trama spaziale viene fornita, ma l'utente potrebbe non chiaramente sapere cosa fare e viene fornita alcuna informazione di stato di avanzamento. | Nessuna visualizzazione della mesh. Nessuna informazione di materiale sussidiario fornita all'utente sulla posizione in cui cercare oppure quando l'analisi avvia o arresta. |

### <a name="how-to-measure"></a>Consente di misurare

* Durante un'analisi di spazio necessaria, vengono fornite istruzioni audio e video che indica dove guardare e quando avviare e arrestare l'analisi.

### <a name="recommendations"></a>Consigli

* Indicare in che misura il volume totale in prossimità degli utenti deve far parte dell'esperienza.
* Comunicano quando l'analisi viene avviata e si arresta, ad esempio un indicatore di stato.
* Usare una visualizzazione della trama durante l'analisi.
* Fornire segnali audio e video per incoraggiare l'utente di eseguire ricerche e spostarsi nella stanza.
* L'utente che indicano dove è possibile per migliorare i dati. In molti casi, potrebbe essere preferibile informare l'utente ne servano per (ad esempio, esaminare il tetto massimo, cercare dietro mobili), per ottenere la qualità di analisi necessarie.

### <a name="resources"></a>Risorse

#### <a name="documentation"></a>Documentazione

* [Visualizzazione della scansione dello spazio](room-scan-visualization.md)
* [Case study: Distribuire le funzionalità di mapping spaziale di HoloLens](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [Case study: Progettazione per HoloTour spaziale](case-study-spatial-sound-design-for-holotour.md)
* [Case study: Creazione di un'esperienza coinvolgente su in frammenti](case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a>Strumenti ed esercitazioni

* [Toolkit di realtà mista - UX](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a>Indicatori direzionali

In un'app di realtà mista, il contenuto sia all'esterno del campo di visualizzazione o bloccati dagli oggetti reali. Un'applicazione ben progettata renderà più facile trovare il contenuto non visibili all'utente. Indicatori direzionali avvisano un utente al contenuto importante e forniscono materiale sussidiario per il contenuto relativo alla posizione dell'utente. Materiale sussidiario per il contenuto non visibili può richiedere la forma di istanze di emissione FixIt audio, le frecce direzionali o segnali visivi diretti.

### <a name="device-impact"></a>Impatto di dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Auricolari coinvolgenti</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criteri di qualità

|  Migliore  |  Soddisfa |  esito negativo |
--- | --- | ---
|  Segnali audio e video direttamente guidano l'utente per il contenuto pertinente di fuori del campo di visualizzazione. | Una freccia o un indicatore che punta all'utente nella direzione generale del contenuto. | Il contenuto pertinente è di fuori del campo di visualizzazione e scarsa o alcuna indicazione di percorso non viene fornito all'utente. | 

### <a name="how-to-measure"></a>Consente di misurare

* Il contenuto pertinente di fuori del campo utente visivo è individuabile tramite segnali visivi e/o audio.

### <a name="recommendations"></a>Consigli

* Quando il contenuto pertinente non è compreso il campo di vista dell'utente, usare gli indicatori direzionali e segnali acustici per assistere l'utente al contenuto. In molti casi, una guida visiva diretta è preferibile le frecce direzionali.
* Gli indicatori direzionali non devono essere creati nel cursore.

### <a name="resources"></a>Risorse

* [Frame olografico](holographic-frame.md)

## <a name="data-loading"></a>Caricamento dei dati

Un controllo di stato fornisce all'utente un feedback nel caso in cui sia in corso un'operazione di lunga durata. È possibile che l'utente non è possibile interagire con l'app quando l'indicatore di stato è visibile e può anche indicare quanto tempo il tempo di attesa potrebbe essere.

### <a name="device-impact"></a>Impatto di dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Auricolari coinvolgenti</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criteri di qualità

|  Migliore  |  Soddisfa |  esito negativo |
--- | --- | ---
|  Animata indicatore visivo, sotto forma di un indicatore di stato o un anello, che mostra lo stato di avanzamento durante il caricamento o l'elaborazione dati. L'indicatore visivo fornisce indicazioni su quanto tempo può essere l'attesa. | Utente viene informato che il caricamento dei dati è in corso, ma è presente alcuna indicazione di quanto tempo può essere l'attesa. | Non è il caricamento dei dati o indicatori di processo per l'attività richiede più di 5 secondi. |

### <a name="how-to-measure"></a>Consente di misurare

* Durante il caricamento dei dati non verificare lo stato vuoto per più di 5 secondi.

### <a name="recommendations"></a>Consigli

* Fornire un animatore durante il caricamento di dati che mostra lo stato di avanzamento in qualsiasi situazione, quando l'utente potrebbe percepire questa app sono bloccati o arrestato in modo anomalo. Una regola generale ragionevole è un'attività 'caricamento in corso' che potrebbe richiedere più di 5 secondi.

### <a name="resources"></a>Risorse

* [Visualizzazione dello stato](progress.md)

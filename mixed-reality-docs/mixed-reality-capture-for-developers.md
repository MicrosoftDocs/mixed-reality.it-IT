---
title: Mista acquisizione realtà per gli sviluppatori
description: Procedure consigliate per realtà mista acquisiscono per gli sviluppatori.
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: MRC, foto, video, acquisizione, fotocamera
ms.openlocfilehash: c2d98baf16b2ea724247224aabadc1e2ca533ec1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599453"
---
# <a name="mixed-reality-capture-for-developers"></a>Mista acquisizione realtà per gli sviluppatori

> [!NOTE]
> Altre indicazioni specifiche su 2 HoloLens [presto](index.md#news-and-notes). 

Visualizzare [abilitazione MRC nell'app](#enabling-mrc-in-your-app) seguito per indicazioni su una nuova funzionalità MRC per HoloLens 2.

Poiché un utente potrebbe richiedere un [acquisizione di realtà mista](mixed-reality-capture.md) foto (MRC) o video in qualsiasi momento, esistono alcuni aspetti da tenere in considerazione quando si sviluppa l'applicazione. Ciò include le procedure consigliate per una qualità visiva MRC ed essere reattivo alle modifiche del sistema mentre MRCs vengono acquisite.

Gli sviluppatori possono inoltre facilmente integrare acquisizione di realtà mista e l'inserimento nelle app.

MRC su HoloLens (prima generazione) supporta i video e foto fino a 720p, mentre MRC su HoloLens 2 supporta video fino a 1080p e foto fino alla risoluzione 4K.

## <a name="the-importance-of-quality-mrc"></a>L'importanza di qualità MRC

Realtà mista acquisiti foto e video sono probabilmente la prima esperienza che disporrà di un utente dell'app. Se come schermate di realtà mista nella pagina di Microsoft Store o da altri utenti che condividono MRCs nei social network. È possibile usare MRC per l'app demo, informare gli utenti, incoraggiare gli utenti di condividere le relative interazioni world misto e per la ricerca utente e la risoluzione dei problemi.

## <a name="how-mrc-impacts-your-app"></a>Come MRC influisce sulle app

### <a name="enabling-mrc-in-your-app"></a>Abilitazione MRC nell'app

Per impostazione predefinita, un'app non dovrà eseguire alcuna operazione per consentire agli utenti di eseguire le acquisizioni di realtà mista. Tuttavia, poiché la progettazione di HoloLens 2 aumenta la distanza tra la camera foto/video (PV) e la visualizzazione, verrà introdotto una nuova opzione per produrre un rendering di fotocamera 3rd allineato alla camera PV **HoloLens 2**. 

Acconsentire esplicitamente in a 3rd camera il rendering sul HoloLens 2 offre i miglioramenti seguenti tramite l'esperienza MRC predefinita:
* Allineamento ologramma per l'ambiente fisico e mani (per le interazioni quasi) deve essere accurato affatto le distanze, invece di dover diverso da un offset a distanze il [concentrarsi punto](focus-point-in-unity.md) come si può vedere nella MRC predefinito.
* Non verrà compromessa l'occhio del lettore a destra nelle cuffie, perché non verrà usato per eseguire il rendering di vntana per l'output MRC.

### <a name="disabling-mrc-in-your-app"></a>La disabilitazione di MRC nell'app

Quando viene utilizzata un'app 2D [DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://msdn.microsoft.com/library/windows/desktop/bb509554(v=vs.85).aspx) oppure [DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://msdn.microsoft.com/library/windows/desktop/bb173076(v=vs.85).aspx) per visualizzare il contenuto protetto con una catena di scambio configurato correttamente, sarà contenuto visivo dell'app nascosto automaticamente durante l'esecuzione di acquisizione di realtà mista.

### <a name="knowing-when-mrc-is-active"></a>Sapere quando è attiva MRC

Il [AppCapture](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.appcapture.aspx) classe può essere utilizzata da un'app di sapere quando è in esecuzione system acquisizione di realtà mista (ad audio o video).

>[!NOTE]
>Del AppCapture [GetForCurrentView](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.appcapture.getforcurrentview.aspx) API possono restituire null se l'acquisizione di realtà mista non è disponibile nel dispositivo. È anche importante annullare la registrazione dell'evento CapturingChanged quando l'app viene sospesa, altrimenti MRC può trovare in uno stato bloccato.

### <a name="best-practices-hololens-specific"></a>Procedure consigliate (specifico di HoloLens)

MRC dovrebbe funzionare senza operazioni aggiuntive da parte degli sviluppatori, ma esistono alcuni aspetti da tenere presenti per offrire l'esperienza di acquisizione meglio realtà mista dell'app.

**MRC utilizza canale alfa di ologramma per essere combinate con il [fotocamera](locatable-camera.md) immagini**

Il passaggio più importante è per assicurarsi che l'app è la cancellazione su nero trasparente invece di cancellazione sul nero opaco. In Unity, questa operazione viene eseguita per impostazione predefinita con il MixedRealityToolkit ma se si sviluppa in non Unity, si potrebbe essere necessario modificare un una riga.

Ecco alcuni degli elementi che vengono visualizzati in MRC se l'app non è la cancellazione di su nero trasparente:

**Errori di esempio**: Nero bordi intorno al contenuto (riesce a cancellare su nero trasparente)

<table>
<tr>
<td>
<img src="images/chessboardblackedges-300px.jpg" alt="Failing to clear to transparent black: black edge artifacts around holograms"/>
</td>
<td>
<img src="images/fieldblackedges-300px.jpg" alt="Failing to clear to transparent black: black edge artifacts around holograms"/>
</td>
</tr>
</table>

**Errori di esempio**: La scena in background intera di ologramma viene visualizzato in nera. Impostazione di un valore alfa in background dei risultati 1 in un sfondo nero

![Impostazione di un valore alfa in background dei risultati 1 in un sfondo nero](images/clearopaqueblack-300px.png)

**Risultato previsto**: Ologrammi vengono visualizzati correttamente combinate con il mondo reale (risultato previsto se la cancellazione su nero trasparente)

![Risultato previsto se la cancellazione su nero trasparente](images/cleartransparentblack-300px.png)

**Soluzione**:
* Modificare i contenuti vengono visualizzati come colore nero opaco per avere un valore alfa pari a 0.
* Assicurarsi che l'app è la cancellazione su nero trasparente.
* Valore predefinito di Unity da cancellare per cancellare automaticamente con MixedRealityToolkit, ma se si tratta di un'app non Unity che è necessario modificare il colore utilizzato con ID3D11DeiceContext::ClearRenderTargetView(). Si desidera assicurarsi che si deseleziona su nero trasparente (0,0,0,0) anziché nero opaco (0,0,0,1).

Se si desidera, ma in genere non richiedono, è ora possibile ottimizzare i valori alfa degli asset. La maggior parte dei casi, MRCs avrà un aspetto ottimale impostazione predefinita. MRC presuppone alfa premoltiplicato. I valori alfa influiranno solo l'acquisizione MRC.

### <a name="what-to-expect-when-mrc-is-enabled-on-hololens"></a>Cosa accade quando si attiva MRC su HoloLens

Di seguito si applica a sia HoloLens (prima) e 2 di HoloLens, se non diversamente specificato:

* Il sistema limiterà l'applicazione per il rendering di 30Hz. Consente di creare alcune capacità aggiuntiva per MRC di eseguire l'app non è necessario mantenere una riserva di budget costante e corrisponde anche la frequenza dei fotogrammi video record MRC di 30fps
* Contenuto di ologramma l'occhio del lettore a destra del dispositivo può sembrare "coriandoli" durante la registrazione/streaming MRC: testo potrà diventare più difficile da leggere e bordi ologrammi potrebbero apparire più frastagliati (acconsentire esplicitamente in a 3rd camera il rendering sul **HoloLens 2** evita Questo compromesso)
* Video e foto MRC rispetterà dell'applicazione [concentrarsi punto](focus-point-in-unity.md) se l'applicazione è abilitato, che aiuteranno a garantire vntana sono posizionati in modo accurato. Per i video, il punto di stato attivo viene smussato pertanto vntana può sembrare lenta dello sfasamento nella posizione corretta, se la profondità del punto di stato attivo viene modificato in modo significativo. Ologrammi che sono diverse profondità dal punto di stato attivo sembra offset dal mondo reale (vedere l'esempio riportato di seguito in cui il punto di stato attivo è impostato su 2 metri ma ologrammi sono posizionato in corrispondenza di 1 metro).

![Ologrammi 2 metri apparirà perfettamente registrati al mondo. Ologrammi alle distanze close o distante possono essere compensate leggermente.](images/hologramaccuracydistancemrc-1000px.png)

## <a name="integrating-mrc-functionality-from-within-your-app"></a>Integrazione delle funzionalità MRC all'interno dell'app

L'app di realtà mista può avviare MRC foto o acquisizione video all'interno dell'app e il contenuto acquisito viene resa disponibile per l'app senza essere archiviati per il dispositivo "rullino della fotocamera." È possibile creare un registrazione MRC personalizzato o sfruttare i vantaggi di acquisizione della fotocamera incorporata dell'interfaccia utente. 

### <a name="mrc-with-built-in-camera-ui"></a>MRC con interfaccia utente della fotocamera incorporata

Gli sviluppatori possono usare la *[API dell'interfaccia utente di acquisire fotocamera](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* per ottenere un utente acquisiti realtà mista foto o video con solo poche righe di codice.

Questa API viene avviata la fotocamera MRC predefinita dell'interfaccia utente, da cui l'utente può richiedere una foto o video e restituisce l'acquisizione risulta all'app.  Se si desidera creare la propria interfaccia utente della fotocamera o necessario inferiore a livello di accesso al flusso di acquisizione, è possibile creare un registratore di acquisizione di realtà mista personalizzato.

### <a name="creating-a-custom-mrc-recorder"></a>Creazione di un registratore MRC personalizzato

Mentre l'utente può attivare sempre una foto o video usando il sistema MRC acquisire servizio, un'applicazione potrebbe voler creare un'app della fotocamera personalizzato ma includere vntana nel flusso di fotocamera come MRC. In questo modo l'applicazione avviare acquisizioni per conto dell'utente, registrazione personalizzata dell'interfaccia utente di creare o personalizzare le impostazioni di MRC per citare alcuni esempi.

**HoloStudio aggiunge una fotocamera MRC personalizzata usando gli effetti MRC**

![HoloStudio aggiunge una fotocamera MRC personalizzata usando gli effetti MRC](images/cameraiconholostudio-300px.jpg)

Le applicazioni Unity dovrebbe [Locatable_camera_in_Unity](locatable-camera-in-unity.md) per la proprietà abilitare vntana.

Altre applicazioni possono eseguire questa operazione usando il [le API Windows Media acquisire](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx) per controllare la fotocamera e aggiungere un effetto MRC Video e Audio da includere nel video e immagini fisse vntana virtuale e audio dell'applicazione.

Le applicazioni sono disponibili due opzioni per aggiungere l'effetto:
* L'API precedente: [Windows.Media.Capture.MediaCapture.AddEffectAsync()](https://msdn.microsoft.com/library/windows/apps/br211961.aspx)
* Il nuovo Microsoft consiglia di API (restituisce un oggetto, rendendo possibile modificare le proprietà dinamiche): [Windows.Media.Capture.MediaCapture.AddVideoEffectAsync()](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.addvideoeffectasync.aspx) / [Windows.Media.Capture.MediaCapture.AddAudioEffectAsync()](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.addaudioeffectasync.aspx) che richiedono l'app creare una propria implementazione di [IVideoEffectDefinition](https://msdn.microsoft.com/library/windows/apps/windows.media.effects.ivideoeffectdefinition.aspx) e [IAudioEffectDefinition](https://msdn.microsoft.com/library/windows/apps/windows.media.effects.iaudioeffectdefinition.aspx). Vedere l'esempio di effetto MRC per esempio di utilizzo.

(Si noti che questi spazi dei nomi non verranno riconosciuti da Visual Studio, ma le stringhe sono ancora valide)

MRC Video Effect (**Windows.Media.MixedRealityCapture.MixedRealityCaptureVideoEffect**)

|  Nome proprietà  |  Tipo  |  Valore predefinito  |  Descrizione | 
|----------|----------|----------|----------|
|  StreamType  |  UINT32 ([MediaStreamType](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediastreamtype.aspx))  |  1 (VideoRecord)  |  Viene descritto il flusso di acquisizione viene utilizzato per questo effetto. Audio non è disponibile. | 
|  HologramCompositionEnabled  |  booleano  |  TRUE  |  Flag per abilitare o disabilitare vntana nell'acquisizione video. | 
|  RecordingIndicatorEnabled  |  booleano  |  TRUE  |  Flag per abilitare o disabilitare la registrazione indicatore nella schermata durante l'acquisizione di ologramma. | 
|  VideoStabilizationEnabled  |  booleano  |  FALSE  |  Flag per abilitare o disabilitare la stabilizzazione video con tecnologia lo strumento di rilevamento di HoloLens. | 
|  VideoStabilizationBufferLength  |  UINT32  |  0  |  Impostare il numero di frame cronologico viene utilizzato per la stabilizzazione video. 0 è la latenza di 0 e quasi "disponibile" da una prospettiva di potenza e le prestazioni. 15 è consigliato per la qualità più elevata (aumentando tuttavia 15 fotogrammi di latenza e la memoria). | 
|  GlobalOpacityCoefficient  |  float  |  0.9 (HoloLens) 1.0 (visore VR Immersivi)  |  Impostare il coefficiente di opacità globale di ologramma nell'intervallo da 0.0 (trasparente) a 1.0 (completamente opaco). | 
|  BlankOnProtectedContent  |  booleano  |  FALSE  |  Flag per abilitare o disabilitare la restituzione di un frame vuoto se non c'è un contenuto che mostra di app UWP protetti 2d. Se questo flag è false e un 2d app UWP non è protetto con contenuto, che l'app UWP 2d verrà sostituito da una trama di contenuto protetta in entrambe le cuffie e l'acquisizione di realtà mista. |
|  ShowHiddenMesh  |  booleano  |  FALSE  |  Flag per abilitare o disabilitare la visualizzazione di trama di area nascosta della camera holographic e adiacenti contenuto. |

MRC Audio Effect (**Windows.Media.MixedRealityCapture.MixedRealityCaptureAudioEffect**)

<table>
<tr>
<th>Nome proprietà</th>
<th>Tipo</th>
<th>Valore predefinito</th>
<th>Descrizione</th>
</tr>
<tr>
<td>MixerMode</td>
<td>UINT32</td>
<td>2</td>
<td>
<ul>
<li>0 : Solo l'audio MIC</li>
<li>1 : Solo l'audio di sistema</li>
<li>2 : MIC e audio di sistema</li>
</ul>
</td>
</tr>
</table>

### <a name="simultaneous-mrc-limitations"></a>Limitazioni MRC simultanee

Esistono alcune limitazioni intorno a più App che accedono a MRC nello stesso momento.

#### <a name="photovideo-camera-access"></a>Accesso alla fotocamera foto/video

La fotocamera foto/video è limitata al numero di processi che possono accedervi allo stesso tempo. Durante la registrazione di un processo di video o richiede una foto di qualsiasi altro processo avrà esito negativo acquisire la fotocamera foto/video. (si applica per acquisire realtà mista e acquisizione di foto/video standard)

Con Windows 10 April 2018 Update, questa restrizione non si applica se la fotocamera MRC predefinita dell'interfaccia utente viene usata per richiedere una foto o video dopo che un'app è stata avviata la fotocamera foto/video. In questo caso, la risoluzione e la frequenza dei fotogrammi della fotocamera MRC predefinita dell'interfaccia utente potrebbero risultare ridotte dai valori delle relative normale.

Con Windows 10 ottobre 2018 Update, questa restrizione non valida per lo streaming MRC su Miracast.

#### <a name="mrc-access"></a>Accesso MRC

Con Windows 10 April 2018 Update, non è più un limite attorno a più App l'accesso a flusso MRC (tuttavia, l'accesso alla fotocamera foto/video ancora presenta limitazioni).

Precedente a Windows 10 April 2018 Update, registratore MRC personalizzato dell'app è stata si escludono a vicenda con sistema MRC (acquisizione di foto, video di acquisizione o streaming dalla finestra di di Windows Device Portal).

## <a name="see-also"></a>Vedere anche
* [Acquisizione di realtà mista](mixed-reality-capture.md)
* [Visualizzazione spectator](spectator-view.md)

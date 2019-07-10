---
title: Mista acquisizione realtà per gli sviluppatori
description: Procedure consigliate per realtà mista acquisiscono per gli sviluppatori.
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: MRC, foto, video, acquisizione, fotocamera
ms.openlocfilehash: d1675d2d6c74c6d15ca245a66719e00f2a7c2111
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694370"
---
# <a name="mixed-reality-capture-for-developers"></a>Mista acquisizione realtà per gli sviluppatori

> [NOTA!] Visualizzare [eseguire il rendering dalla fotocamera PV](#render-from-the-pv-camera-opt-in) seguito per indicazioni su una nuova funzionalità MRC per HoloLens 2.

Poiché un utente potrebbe richiedere un [acquisizione di realtà mista](mixed-reality-capture.md) foto (MRC) o video in qualsiasi momento, esistono alcuni aspetti da tenere in considerazione quando si sviluppa l'applicazione. Ciò include le procedure consigliate per una qualità visiva MRC ed essere reattivo alle modifiche del sistema mentre MRCs vengono acquisite.

Gli sviluppatori possono inoltre facilmente integrare acquisizione di realtà mista e l'inserimento nelle app.

MRC su HoloLens (prima generazione) supporta i video e foto fino a 720p, mentre MRC su HoloLens 2 supporta video fino a 1080p e foto fino alla risoluzione 4K.

## <a name="the-importance-of-quality-mrc"></a>L'importanza di qualità MRC

Realtà mista acquisiti foto e video sono probabilmente la prima esperienza che disporrà di un utente dell'app. Se come schermate di realtà mista nella pagina di Microsoft Store o da altri utenti che condividono MRCs nei social network. È possibile usare MRC per l'app demo, informare gli utenti, incoraggiare gli utenti di condividere le relative interazioni world misto e per la ricerca utente e la risoluzione dei problemi.

## <a name="how-mrc-impacts-your-app"></a>Come MRC influisce sulle app

### <a name="enabling-mrc-in-your-app"></a>Abilitazione MRC nell'app

Per impostazione predefinita, un'app non dovrà eseguire alcuna operazione per consentire agli utenti di eseguire le acquisizioni di realtà mista.

### <a name="enabling-improved-alignment-for-mrc-in-your-app"></a>Abilitazione della migliore allineamento per MRC nell'app

Per impostazione predefinita, acquisizione di realtà mista combina output holographic dell'attenzione a destra con la fotocamera foto/video (PV). Queste due origini vengono combinate usando il punto di stato attivo impostato dall'app immersive attualmente in esecuzione.

Ciò significa che vntana di fuori del piano lo stato attivo non verrà allineati anche (a causa della distanza fisica tra la camera PV e la visualizzazione a destra).

#### <a name="set-the-focus-point"></a>Impostare il punto di stato attivo

App immersive (su HoloLens) deve impostare il [concentrarsi punto](focus-point-in-unity.md) della posizione in cui il piano di stabilizzazione sia. In questo modo il miglior allineamento in entrambe le cuffie e nell'acquisizione di realtà mista.

Se non è impostato un punto di stato attivo, il piano di stabilizzazione per impostazione predefinita due contatori.

#### <a name="render-from-the-pv-camera-opt-in"></a>Eseguire il rendering dalla fotocamera PV (opt-in)

HoloLens 2 aggiunge la possibilità per un'app immersiva **eseguire il rendering dalla fotocamera PV** durante l'esecuzione di acquisizione di realtà mista. Per garantire che l'app supporta il rendering aggiuntive in modo corretto, l'app deve acconsentire esplicitamente a questa funzionalità.

Eseguire il rendering dalle offerte di fotocamera PV i miglioramenti seguenti tramite l'esperienza MRC predefinita:
* Allineamento di ologramma per l'ambiente fisico e mani (per le interazioni quasi) deve essere accurato affatto distanze, invece di avere un offset a distanze diverso rispetto al punto di stato attivo come si può vedere nella MRC predefinito.
* Non verrà compromessa l'occhio del lettore a destra nelle cuffie, perché non verrà usato per eseguire il rendering di vntana per l'output MRC.

Esistono tre passaggi per abilitare il rendering dalla fotocamera PV:
1. Abilitare il PhotoVideoCamera HolographicViewConfiguration
2. Gestire il rendering HolographicCamera aggiuntive
3. Verificare il codice e gli shader eseguire il rendering correttamente da questa HolographicCamera aggiuntiva

##### <a name="enable-the-photovideocamera-holographicviewconfiguration"></a>Abilitare il PhotoVideoCamera HolographicViewConfiguration

Per acconsentire esplicitamente, un'app attiva semplicemente il PhotoVideoCamera [HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration):
```csharp
var display = Windows.Graphics.Holographic.HolographicDisplay.GetDefault();
var view = display.TryGetViewConfiguration(Windows.Graphics.Holographic.HolographicViewConfiguration.PhotoVideoCamera);
if (view != null)
{
   view.IsEnabled = true;
}
```

##### <a name="handle-the-additional-holographiccamera-render-in-directx"></a>Gestire il rendering HolographicCamera aggiuntive in DirectX

Quando l'app prevede il consenso esplicito per eseguire il rendering dalla fotocamera PV e viene avviata l'acquisizione di realtà mista:
1. Evento CameraAdded dell'HolographicSpace verrà attivato. Questo evento può essere posticipato se l'app non è possibile gestire la fotocamera in questo momento.
2. Dopo l'evento è stata completata (e non esistono Nessun rinvii in sospeso) il HolographicCamera verrà visualizzati nell'elenco di AddedCameras dell'HolographicFrame successivo.

Quando si arresta acquisizione di realtà mista (o se l'app disabilita la configurazione di visualizzazione durante l'esecuzione di acquisizione di realtà mista): il HolographicCamera verrà visualizzati nell'elenco RemovedCameras del HolographicFrame avanti e verrà evento CameraRemoved dell'HolographicSpace vengono attivati.

Oggetto [ViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration) HolographicCamera per consentire di identificare la configurazione a cui appartiene una fotocamera è stata aggiunta proprietà.

##### <a name="handle-the-additional-holographiccamera-render-in-unity"></a>Gestire il rendering HolographicCamera aggiuntive in Unity

>[!NOTE]
> Supporto di Unity per eseguire il rendering dalla fotocamera PV in fase di sviluppo e non può essere, ancora usato. Questa documentazione verrà aggiornata quando è disponibile una compilazione di Unity con il supporto per il rendering dalla fotocamera PV.

##### <a name="verify-shaders-and-code-support-additional-cameras"></a>Verificare gli shader e fotocamere aggiuntive a supporto del codice

Eseguire un'acquisizione di realtà mista e verificare la presenza dell'allineamento insolito, contenuto mancante o problemi di prestazioni. Aggiornare gli shader e il codice come appropriato.

Se sono presenti determinati scene di cui non è in grado di supportare una telecamera aggiuntiva del rendering, è possibile disabilitare HolographicViewConfiguration del PhotoVideoCamera durante la relativa esecuzione.

### <a name="disabling-mrc-in-your-app"></a>La disabilitazione di MRC nell'app

#### <a name="2d-app"></a>App 2D

App 2D possibile scegliere di avere il contenuto visivo oscurato quando eseguendo l'acquisizione di realtà mista:
* Disponibile, con la [DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-present) flag
* Creare una catena di scambio dell'app con il [DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://docs.microsoft.com/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag) flag
* Con Windows 10 potrebbero 2019 aggiornare, l'impostazione del ApplicationView [IsScreenCaptureEnabled](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled)

#### <a name="immersive-app"></a>App immersive

App immersive è possibile scegliere di avere il contenuto visivo escluso dall'acquisizione di realtà mista da:
* Impostazione del HolographicCameraRenderingParameter [IsContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled) per disabilitare l'acquisizione della realtà mista per il relativo frame associato
* Impostazione del HolographicCamera [IsHardwareContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled) per disabilitare l'acquisizione della realtà mista per la fotocamera holographic associato

#### <a name="password-keyboard"></a>Tastiera di password

Con Windows 10 2019 aggiornamento di maggio, contenuto visivo sarà escluso automaticamente dall'acquisizione di realtà mista quando una password o pin tastiera è visibile.

### <a name="knowing-when-mrc-is-active"></a>Sapere quando è attiva MRC

Il [AppCapture](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.AppCapture) classe può essere utilizzata da un'app di sapere quando è in esecuzione system acquisizione di realtà mista (ad audio o video).

>[!NOTE]
>Del AppCapture [GetForCurrentView](https://docs.microsoft.com/uwp/api/windows.media.capture.appcapture.getforcurrentview) API possono restituire null se l'acquisizione di realtà mista non è disponibile nel dispositivo. È anche importante annullare la registrazione dell'evento CapturingChanged quando l'app viene sospesa, altrimenti MRC può trovare in uno stato bloccato.

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

Altre applicazioni possono eseguire questa operazione usando il [le API Windows Media acquisire](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaCapture) per controllare la fotocamera e aggiungere un effetto MRC Video e Audio da includere nel video e immagini fisse vntana virtuale e audio dell'applicazione.

Le applicazioni sono disponibili due opzioni per aggiungere l'effetto:
* L'API precedente: [Windows.Media.Capture.MediaCapture.AddEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addeffectasync)
* Il nuovo Microsoft consiglia di API (restituisce un oggetto, rendendo possibile modificare le proprietà dinamiche): [Windows.Media.Capture.MediaCapture.AddVideoEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync) / [Windows.Media.Capture.MediaCapture.AddAudioEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync) che richiedono l'app creare una propria implementazione di [IVideoEffectDefinition](https://docs.microsoft.com/uwp/api/Windows.Media.Effects.IVideoEffectDefinition) e [IAudioEffectDefinition](https://docs.microsoft.com/uwp/api/windows.media.effects.iaudioeffectdefinition). Vedere l'esempio di effetto MRC per esempio di utilizzo.

>[!NOTE]
> Lo spazio dei nomi Windows.Media.MixedRealityCapture non verrà riconosciuto da Visual Studio, ma le stringhe sono ancora valide.

MRC Video Effect (**Windows.Media.MixedRealityCapture.MixedRealityCaptureVideoEffect**)

|  Nome proprietà  |  type  |  Valore predefinito  |  Descrizione | 
|----------|----------|----------|----------|
|  StreamType  |  UINT32 ([MediaStreamType](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaStreamType))  |  1 (VideoRecord)  |  Viene descritto il flusso di acquisizione viene utilizzato per questo effetto. Audio non è disponibile. | 
|  HologramCompositionEnabled  |  boolean  |  TRUE  |  Flag per abilitare o disabilitare vntana nell'acquisizione video. | 
|  RecordingIndicatorEnabled  |  boolean  |  TRUE  |  Flag per abilitare o disabilitare la registrazione indicatore nella schermata durante l'acquisizione di ologramma. | 
|  VideoStabilizationEnabled  |  boolean  |  FALSE  |  Flag per abilitare o disabilitare la stabilizzazione video con tecnologia lo strumento di rilevamento di HoloLens. | 
|  VideoStabilizationBufferLength  |  UINT32  |  0  |  Impostare il numero di frame cronologico viene utilizzato per la stabilizzazione video. 0 è la latenza di 0 e quasi "disponibile" da una prospettiva di potenza e le prestazioni. 15 è consigliato per la qualità più elevata (aumentando tuttavia 15 fotogrammi di latenza e la memoria). | 
|  GlobalOpacityCoefficient  |  float  |  0.9 (HoloLens) 1.0 (visore VR Immersivi)  |  Impostare il coefficiente di opacità globale di ologramma nell'intervallo da 0.0 (trasparente) a 1.0 (completamente opaco). | 
|  BlankOnProtectedContent  |  boolean  |  FALSE  |  Flag per abilitare o disabilitare la restituzione di un frame vuoto se non c'è un contenuto che mostra di app UWP protetti 2d. Se questo flag è false e un 2d app UWP non è protetto con contenuto, che l'app UWP 2d verrà sostituito da una trama di contenuto protetta in entrambe le cuffie e l'acquisizione di realtà mista. |
|  ShowHiddenMesh  |  boolean  |  FALSE  |  Flag per abilitare o disabilitare la visualizzazione di trama di area nascosta della camera holographic e adiacenti contenuto. |
| OutputSize | Size | 0, 0 | Impostare le dimensioni di output desiderato dopo il ritaglio per la stabilizzazione video. Una dimensione di ritaglio predefinita viene scelto se si specifica 0 o una dimensione di output non valido. |
| PreferredHologramPerspective | UINT32 | 1 (PhotoVideoCamera) | Enumerazione utilizzata per indicare quale visualizzare la configurazione della fotocamera holographic deve essere acquisita. L'impostazione 0 indica (Display) che l'app non verrà chiesto loro di eseguire il rendering tra la camera e foto/video |

MRC Audio Effect (**Windows.Media.MixedRealityCapture.MixedRealityCaptureAudioEffect**)

<table>
<tr>
<th>Nome proprietà</th>
<th>type</th>
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

Con 2 HoloLens, un'app può usare del MediaCaptureInitializationSettings [SharingMode](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode) proprietà per indicare che si desidera eseguire SharedReadOnly se senza bisogno di controllo esclusivo della fotocamera foto/video. Ciò significa che la risoluzione e la frequenza dei fotogrammi dell'acquisizione sarà limitata a quali altre App aver configurato la fotocamera per fornire.

##### <a name="built-in-mrc-photovideo-camera-access"></a>Accesso alla fotocamera di foto/video MRC predefinito

Funzionalità MRC incorporate in Windows 10 (tramite Cortana, Menu Start, rapide da tastiera hardware in Miracast, Windows Device Portal):
* Verrà eseguita con ExclusiveControl per impostazione predefinita

Tuttavia, è stato aggiunto il supporto per ogni sottosistema per operare in modalità condivisa:
* Se un'app richiede l'accesso ExclusiveControl alla fotocamera foto/video, MRC incorporati arresterà automaticamente usando la fotocamera di foto e video in modo che la richiesta dell'app avrà esito positivo
* Se MRC predefinito viene avviato mentre ExclusiveControl dispone di un'app, incorporato MRC verrà eseguito in modalità SharedReadOnly

Questa funzionalità in modalità condivisa presenta alcune restrizioni:
* Foto tramite Cortana, tasti di scelta rapida dell'hardware o dal Menu Start: Richiede Windows 10 April 2018 Update (o versioni successive)
* Video tramite Cortana, tasti di scelta rapida dell'hardware o dal Menu Start: Richiede Windows 10 April 2018 Update (o versioni successive)
* Streaming MRC su Miracast: Richiede Windows 10 ottobre 2018 Update (o versioni successive)
* Streaming MRC su Windows Device Portal o tramite l'app complementare per HoloLens: Richiede HoloLens 2

>[!NOTE]
> La risoluzione e la frequenza dei fotogrammi della fotocamera MRC predefinita dell'interfaccia utente potrebbero risultare ridotte dai valori delle relative normale quando un'altra app sta usando la fotocamera foto/video.

#### <a name="mrc-access"></a>Accesso MRC

Con Windows 10 April 2018 Update, non è più un limite attorno a più App l'accesso a flusso MRC (tuttavia, l'accesso alla fotocamera foto/video ancora presenta limitazioni).

Precedente a Windows 10 April 2018 Update, registratore MRC personalizzato dell'app è stata si escludono a vicenda con sistema MRC (acquisizione di foto, video di acquisizione o streaming dalla finestra di di Windows Device Portal).

## <a name="see-also"></a>Vedere anche
* [Acquisizione realtà mista](mixed-reality-capture.md)
* [Visualizzazione spettatore](spectator-view.md)

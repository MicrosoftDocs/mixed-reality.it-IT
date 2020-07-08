---
title: Acquisizione realtà mista per sviluppatori
description: Procedure consigliate per l'acquisizione di realtà mista per gli sviluppatori.
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: MRC, foto, video, acquisizione, fotocamera
ms.openlocfilehash: 44b853e96ab956e5ea6c03d8c23a61e91ac733d4
ms.sourcegitcommit: fef42e2908e49822f2d13b05d2f9260bf0d72158
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/07/2020
ms.locfileid: "86061144"
---
# <a name="mixed-reality-capture-for-developers"></a>Acquisizione realtà mista per sviluppatori

> [!NOTE]
> Per informazioni su una nuova funzionalità MRC per HoloLens 2, vedere [Render dalla fotocamera PV](#render-from-the-pv-camera-opt-in) di seguito.

Poiché un utente può eseguire una foto o un video di [acquisizione di realtà mista](mixed-reality-capture.md) in qualsiasi momento, è necessario tenere presente alcuni aspetti durante lo sviluppo dell'applicazione. Sono incluse le procedure consigliate per la qualità visiva di MRC e la reattività delle modifiche di sistema durante l'acquisizione di MRCs.

Gli sviluppatori possono anche integrare facilmente l'acquisizione e l'inserimento di realtà miste nelle proprie app.

MRC in HoloLens (prima generazione) supporta video e foto fino a 720p, mentre MRC in HoloLens 2 supporta video fino a 1080p e foto con risoluzione 4K.

## <a name="the-importance-of-quality-mrc"></a>Importanza della qualità MRC

Le foto e i video acquisiti in realtà mista rappresentano probabilmente la prima esposizione che un utente avrà dell'app. Sia che si tratti di screenshot della realtà mista nella pagina Microsoft Store o di altri utenti che condividono MRCs nei social network. È possibile usare MRC per dimostrarne l'app, istruire gli utenti, incoraggiare gli utenti a condividere le interazioni tra il mondo misto e la ricerca degli utenti e la risoluzione dei problemi.

## <a name="how-mrc-impacts-your-app"></a>Effetti di MRC sull'app

### <a name="enabling-mrc-in-your-app"></a>Abilitazione di MRC nell'app

Per impostazione predefinita, un'app non deve eseguire alcuna operazione per consentire agli utenti di eseguire acquisizioni di realtà miste.

### <a name="enabling-improved-alignment-for-mrc-in-your-app"></a>Abilitazione dell'allineamento migliorato per MRC nell'app

Per impostazione predefinita, l'acquisizione di realtà mista combina l'output olografico dell'occhio destro con la fotocamera Photo/video (PV). Queste due origini vengono combinate usando il punto di interesse impostato dall'app immersiva attualmente in esecuzione.

Ciò significa che gli ologrammi al di fuori del piano di attivazione non verranno allineati (a causa della distanza fisica tra la fotocamera FV e la visualizzazione destra).

#### <a name="set-the-focus-point"></a>Imposta il punto di attivazione

Le app immersive (in HoloLens) devono impostare il [punto di messa a fuoco](focus-point-in-unity.md) per la posizione desiderata per il piano di stabilizzazione. In questo modo si garantisce il migliore allineamento nell'auricolare e nell'acquisizione di realtà mista.

Se non è impostato un punto di attivazione, per impostazione predefinita il piano di stabilizzazione sarà di due metri.

#### <a name="render-from-the-pv-camera-opt-in"></a>Rendering dalla fotocamera PV (consenso esplicito)

HoloLens 2 aggiunge la possibilità di eseguire il rendering di un'app immersiva **dalla fotocamera PV** mentre è in esecuzione l'acquisizione di realtà mista. Per assicurarsi che l'app supporti correttamente il rendering aggiuntivo, l'app deve acconsentire esplicitamente a questa funzionalità.

Il rendering dalla fotocamera PV offre i miglioramenti seguenti rispetto all'esperienza MRC predefinita:
* L'allineamento degli ologrammi per l'ambiente fisico e le mani (per le interazioni near) dovrebbe essere accurato a tutte le distanze, anziché avere un offset a distanza diverso dal punto di interesse, come si può vedere nella MRC predefinita.
* L'occhio destro nell'auricolare non verrà compromesso, perché non verrà usato per il rendering degli ologrammi per l'output di MRC.

Per abilitare il rendering dalla fotocamera PV sono disponibili tre passaggi:
1. Abilitare il HolographicViewConfiguration PhotoVideoCamera
2. Gestire il rendering HolographicCamera aggiuntivo
3. Verificare che gli shader e il rendering del codice siano corretti da questa HolographicCamera aggiuntiva

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-directx"></a>Abilitare il HolographicViewConfiguration di PhotoVideoCamera in DirectX

Per acconsentire esplicitamente al rendering dalla fotocamera PV, un'app Abilita semplicemente il [HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration)di PhotoVideoCamera:
```csharp
var display = Windows.Graphics.Holographic.HolographicDisplay.GetDefault();
var view = display.TryGetViewConfiguration(Windows.Graphics.Holographic.HolographicViewConfigurationKind.PhotoVideoCamera);
if (view != null)
{
    view.IsEnabled = true;
}
```

##### <a name="handle-the-additional-holographiccamera-render-in-directx"></a>Gestire il rendering HolographicCamera aggiuntivo in DirectX

Quando l'app ha acconsentito esplicitamente al rendering dalla fotocamera PV e viene avviata l'acquisizione di realtà mista:
1. L'evento CameraAdded di HolographicSpace viene attivato. Questo evento può essere rinviato se l'app non è in grado di gestire la fotocamera in questo momento.
2. Una volta completato l'evento (e non ci sono rinvii in attesa), il HolographicCamera verrà visualizzato nell'elenco AddedCameras di HolographicFrame successivo.

Quando l'acquisizione di realtà mista viene arrestata (o se l'app Disabilita la configurazione della visualizzazione mentre è in esecuzione l'acquisizione della realtà mista): HolographicCamera verrà visualizzato nell'elenco RemovedCameras di HolographicFrame successivo e verrà attivato l'evento CameraRemoved di HolographicSpace.

Una proprietà [ViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration) è stata aggiunta a HolographicCamera per facilitare l'identificazione della configurazione a cui appartiene la fotocamera.

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-unity"></a>Abilitare il HolographicViewConfiguration di PhotoVideoCamera in Unity

> [!NOTE]
> Questa operazione richiede **Unity 2018.4.13 F1**, **Unity 2019.3.0 F1**o versione successiva.

Per acconsentire esplicitamente al rendering dalla fotocamera PV, quando si usa il [Toolkit di realtà mista](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html), abilitare il provider di [impostazioni della camera di realtà mista di Windows](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/CameraSystem/WindowsMixedRealityCameraSettings.html) e selezionare l'impostazione **di rendering dalla fotocamera FV** .

Se non si usa il Toolkit di realtà mista, è possibile usare un componente per [acconsentire manualmente](#enable-the-photovideocamera-holographicviewconfiguration-in-directx) come descritto in precedenza per DirectX.

##### <a name="handle-the-additional-holographiccamera-render-in-unity"></a>Gestire il rendering di HolographicCamera aggiuntivo in Unity

Questa operazione viene eseguita automaticamente da Unity.

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-unreal"></a>Abilita PhotoVideoCamera HolographicViewConfiguration in Unreal

> [!NOTE]
> Questa operazione richiede **Unreal Engine 4.25** o versioni successive.

Per acconsentire esplicitamente al rendering dalla fotocamera/videocamera:

1. Chiama **SetEnabledMixedRealityCamera** e **ResizeMixedRealityCamera**.
    * Usa i valori **Size X** (Dimensione X) e **Size Y** (Dimensione Y) per impostare le dimensioni video.

![Terza fotocamera](images/unreal-camera-3rd.PNG)

##### <a name="handle-the-additional-holographiccamera-render-in-unreal"></a>Gestire il rendering di HolographicCamera aggiuntivo in Unreal

Questa operazione viene eseguita automaticamente da Unreal.

##### <a name="verify-shaders-and-code-support-additional-cameras"></a>Verificare lo shader e il codice supportano fotocamere aggiuntive

Eseguire un'acquisizione di realtà mista e verificare l'allineamento insolito, il contenuto mancante o problemi di prestazioni. Aggiornare gli shader e il codice nel modo appropriato.

Se sono presenti alcune scene che non possono supportare il rendering in una fotocamera aggiuntiva, è possibile disabilitare il HolographicViewConfiguration di PhotoVideoCamera durante l'esecuzione.

### <a name="disabling-mrc-in-your-app"></a>Disabilitazione di MRC nell'app

#### <a name="2d-app"></a>app 2D

le app 2D possono scegliere di nascondere il contenuto visivo quando l'acquisizione di realtà mista viene eseguita da:
* Presente con il flag di [DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-present)
* Creare la catena di scambio dell'app con il flag di [DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://docs.microsoft.com/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag)
* Con l'aggiornamento di Windows 10 maggio 2019, impostando [IsScreenCaptureEnabled](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled) di ApplicationView

#### <a name="immersive-app"></a>App immersiva

Le app immersive possono scegliere di escludere il contenuto visivo dall'acquisizione di realtà mista:
* Impostazione del [IsContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled) di HolographicCameraRenderingParameter per disabilitare l'acquisizione di realtà mista per il frame associato
* Impostazione del [IsHardwareContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled) di HolographicCamera per disabilitare l'acquisizione di realtà mista per la fotocamera olografica associata

#### <a name="password-keyboard"></a>Tastiera password

Con l'aggiornamento di Windows 10 maggio 2019, il contenuto visivo viene automaticamente escluso dall'acquisizione di realtà mista quando è visibile una password o un PIN.

### <a name="knowing-when-mrc-is-active"></a>Sapere quando MRC è attivo

La classe [AppCapture](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.AppCapture) può essere usata da un'app per capire quando viene eseguita l'acquisizione di realtà mista di sistema (per audio o video).

>[!NOTE]
>L'API [GetForCurrentView](https://docs.microsoft.com/uwp/api/windows.media.capture.appcapture.getforcurrentview) di AppCapture può restituire null se l'acquisizione di realtà mista non è disponibile nel dispositivo. È anche importante annullare la registrazione dell'evento CapturingChanged quando l'app viene sospesa. in caso contrario, MRC può entrare in uno stato bloccato.

### <a name="best-practices-hololens-specific"></a>Procedure consigliate (specifiche di HoloLens)

È previsto che MRC funzioni senza lavoro aggiuntivo da parte degli sviluppatori, ma ci sono alcuni aspetti da considerare per fornire la migliore esperienza di acquisizione della realtà mista dell'app.

**MRC usa il canale alfa dell'ologramma per fondersi con le immagini della [fotocamera](locatable-camera.md)**

Il passaggio più importante consiste nel verificare che l'app venga cancellata in nero trasparente anziché in un nero opaco. In Unity questa operazione viene eseguita per impostazione predefinita con la MixedRealityToolkit, ma se si sviluppa in non Unity, potrebbe essere necessario modificare una riga.

Di seguito sono riportati alcuni elementi che potrebbero essere visualizzati in MRC se l'app non viene cancellata in nero trasparente:

**Errori di esempio**: bordi neri intorno al contenuto (da cancellare a nero trasparente)

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

**Errori di esempio**: l'intera scena di sfondo dell'ologramma appare nera. L'impostazione di un valore alfa in background di 1 produce uno sfondo nero

![L'impostazione di un valore alfa in background di 1 produce uno sfondo nero](images/clearopaqueblack-300px.png)

**Risultato previsto**: gli ologrammi appaiono correttamente combinati con il mondo reale (risultato previsto se cancellando il nero trasparente)

![Risultato previsto per la cancellazione del nero trasparente](images/cleartransparentblack-300px.png)

**Soluzione**:
* Modificare il contenuto visualizzato come nero opaco per avere un valore alfa pari a 0.
* Assicurarsi che l'app venga cancellata in nero trasparente.
* Unity viene impostato su Clear per cancellare automaticamente il valore di MixedRealityToolkit, ma se si tratta di un'app non Unity è necessario modificare il colore usato con ID3D11DeiceContext:: ClearRenderTargetView (). Si desidera assicurarsi di deselezionare il nero trasparente (0, 0, 0, 0) invece del nero opaco (0, 0, 0, 1).

È ora possibile ottimizzare i valori alfa delle risorse, se si preferisce, ma in genere non è necessario. Nella maggior parte dei casi, MRCs sarà perfetto. MRC presuppone l'alfa premoltiplicato. I valori alfa avranno effetto solo sull'acquisizione di MRC.

### <a name="what-to-expect-when-mrc-is-enabled-on-hololens"></a>Cosa aspettarsi quando MRC è abilitato in HoloLens

Le condizioni seguenti si applicano sia a HoloLens (First-Generation) che a HoloLens 2, salvo diversa indicazione:

* Il sistema consente di limitare l'applicazione al rendering 30Hz. Questa operazione crea una certa capacità per l'esecuzione di MRC, in modo che l'app non debba tenere una riserva di budget costante e corrisponda anche al framerate dei record video MRC di 30fps
* Il contenuto dell'ologramma nell'occhio destro del dispositivo può sembrare "Spark" durante la registrazione/streaming MRC: il testo potrebbe diventare più difficile da leggere e i bordi dell'ologramma potrebbero sembrare più frastagliati (la scelta del rendering della terza fotocamera in **HoloLens 2** evita questa compromissione)
* Le foto e i video di MRC rispetteranno il [punto di interesse](focus-point-in-unity.md) dell'applicazione se l'applicazione lo ha abilitato, in modo da garantire la corretta posizionamento degli ologrammi. Per i video, il punto di messa a fuoco è smussato, in modo che gli ologrammi possano sembrare lentamente posizionati se la profondità del punto di messa a fuoco cambia significativamente. Gli ologrammi che si trovano in profondità diverse dal punto di interesse possono apparire in offset rispetto al mondo reale (vedere l'esempio riportato di seguito, in cui il punto di messa a fuoco è impostato su 2 metri, ma l'ologramma è posizionato a 1 contatore).

![Gli ologrammi a 2 metri verranno visualizzati perfettamente registrati nel mondo. Gli ologrammi a distanza ravvicinata o distanti possono essere leggermente offset.](images/hologramaccuracydistancemrc-1000px.png)

## <a name="integrating-mrc-functionality-from-within-your-app"></a>Integrazione della funzionalità MRC dall'interno dell'app

L'app per la realtà mista può avviare l'acquisizione di foto o video MRC dall'interno dell'app e il contenuto acquisito viene reso disponibile per l'app senza essere archiviato nel "rullo della fotocamera" del dispositivo. È possibile creare un registratore MRC personalizzato o sfruttare l'interfaccia utente di acquisizione della fotocamera incorporata. 

### <a name="mrc-with-built-in-camera-ui"></a>MRC con interfaccia utente integrata della fotocamera

Gli sviluppatori possono usare l' *[API dell'interfaccia utente di acquisizione della fotocamera](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* per ottenere una foto o un video della realtà mista acquisita dall'utente con poche righe di codice.

Questa API avvia l'interfaccia utente della fotocamera MRC predefinita, da cui l'utente può scattare una foto o un video e restituisce l'acquisizione risultante all'app.  Se si vuole creare un'interfaccia utente della fotocamera personalizzata o un accesso di livello inferiore al flusso di acquisizione, è possibile creare un registratore di acquisizione di realtà mista personalizzato.

### <a name="creating-a-custom-mrc-recorder"></a>Creazione di un registratore MRC personalizzato

Mentre l'utente può sempre attivare una foto o un video usando il servizio di acquisizione di sistema MRC, un'applicazione potrebbe voler creare un'app fotocamera personalizzata, ma includere ologrammi nel flusso della fotocamera come MRC. Questo consente all'applicazione di avviare le acquisizioni per conto dell'utente, creare un'interfaccia utente di registrazione personalizzata o personalizzare le impostazioni di MRC per citare alcuni esempi.

**HoloStudio aggiunge una fotocamera MRC personalizzata usando gli effetti di MRC**

![HoloStudio aggiunge una fotocamera MRC personalizzata usando gli effetti di MRC](images/cameraiconholostudio-300px.jpg)

Le applicazioni Unity dovrebbero vedere [Locatable_camera_in_Unity](locatable-camera-in-unity.md) per la proprietà per abilitare gli ologrammi.

Altre applicazioni possono eseguire questa operazione usando le [API di acquisizione di Windows Media](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaCapture) per controllare la fotocamera e aggiungere un effetto video e audio MRC per includere ologrammi virtuali e audio dell'applicazione in stills e video.

Le applicazioni hanno due opzioni per aggiungere l'effetto:
* API precedente: [Windows. Media. Capture. MediaCapture. AddEffectAsync ()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addeffectasync)
* La nuova API consigliata da Microsoft (restituisce un oggetto, che consente di modificare le proprietà dinamiche): [Windows. Media. Capture. MediaCapture. AddVideoEffectAsync ()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync)  /  [Windows. Media. Capture. MediaCapture. AddAudioEffectAsync ()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync) che richiedono che l'app crei una propria implementazione di [IVideoEffectDefinition](https://docs.microsoft.com/uwp/api/Windows.Media.Effects.IVideoEffectDefinition) e [IAudioEffectDefinition](https://docs.microsoft.com/uwp/api/windows.media.effects.iaudioeffectdefinition). Vedere l'esempio di effetto MRC per l'utilizzo di esempio.

>[!NOTE]
> Lo spazio dei nomi Windows. Media. MixedRealityCapture non verrà riconosciuto da Visual Studio, ma le stringhe sono ancora valide.

Effetto video MRC (**Windows. Media. MixedRealityCapture. MixedRealityCaptureVideoEffect**)

|  Nome proprietà  |  Tipo  |  Valore predefinito  |  Descrizione |
|----------|----------|----------|----------|
|  StreamType  |  UINT32 ([MediaStreamType](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaStreamType))  |  1 (VideoRecord)  |  Descrivere il flusso di acquisizione per cui viene usato questo effetto. L'audio non è disponibile. |
|  HologramCompositionEnabled  |  boolean  |  TRUE  |  Flag per abilitare o disabilitare gli ologrammi nell'acquisizione video. |
|  RecordingIndicatorEnabled  |  boolean  |  TRUE  |  Flag per abilitare o disabilitare l'indicatore di registrazione sullo schermo durante l'acquisizione di ologrammi. |
|  VideoStabilizationEnabled  |  boolean  |  FALSE  |  Flag per abilitare o disabilitare la stabilizzazione video con tecnologia HoloLens Tracker. |
|  VideoStabilizationBufferLength  |  UINT32  |  0  |  Consente di impostare il numero di frame cronologici utilizzati per la stabilizzazione del video. 0 è 0: latenza e quasi "Free" da un punto di vista dell'alimentazione e delle prestazioni. 15 è consigliato per la massima qualità (a costo di 15 fotogrammi di latenza e memoria). |
|  GlobalOpacityCoefficient  |  float  |  0,9 (HoloLens) 1,0 (auricolare immersivo)  |  Impostare il coefficiente di opacità globale di un ologramma compreso tra 0,0 (completamente trasparente) e 1,0 (completamente opaco). |
|  BlankOnProtectedContent  |  boolean  |  FALSE  |  Flag per abilitare o disabilitare la restituzione di un frame vuoto se è presente un'app UWP 2D che mostra il contenuto protetto. Se questo flag è false e un'app UWP 2D Visualizza contenuto protetto, l'app UWP 2D verrà sostituita da una trama di contenuto protetta sia nell'auricolare che nell'acquisizione di realtà mista. |
|  ShowHiddenMesh  |  boolean  |  FALSE  |  Flag per abilitare o disabilitare la visualizzazione della mesh di area nascosta e del contenuto adiacente della fotocamera olografica. |
| OutputSize | Dimensione | 0, 0 | Imposta la dimensione di output desiderata dopo il ritaglio per la stabilizzazione del video. Viene scelta una dimensione di ritaglio predefinita se si specifica 0 o una dimensione di output non valida. |
| PreferredHologramPerspective | UINT32 | **Rendering dall'** impostazione della fotocamera nel portale del dispositivo Windows | Enum usato per indicare quale configurazione della visualizzazione della fotocamera olografica deve essere acquisita: 0 (display) significa che all'app non verrà richiesto di eseguire il rendering dalla fotocamera Photo/video, 1 (PhotoVideoCamera) chiederà all'app di eseguire il rendering dalla fotocamera foto/video (se supportata dall'app). Supportato solo su HoloLens 2 |

>[!NOTE]
> È possibile modificare il valore predefinito di **PreferredHologramPerspective** nel portale per dispositivi Windows passando alla pagina di [acquisizione della realtà mista](using-the-windows-device-portal.md#mixed-reality-capture) e deselezionando il **rendering dalla fotocamera**. L'impostazione predefinita è **1 (PhotoVideoCamera)**, ma può essere deselezionata per impostarla su **0 (visualizzazione)**.
>
> Il valore predefinito di **PreferredHologramPerspective** è **0 (display)** prima dell'aggiornamento del 2020 giugno (Windows olografico, versione 2004 Build 19041,1106 e Windows olografico, versione 1903 Build 18362,1064).

Effetto audio MRC (**Windows. Media. MixedRealityCapture. MixedRealityCaptureAudioEffect**)

| Nome proprietà | Tipo | Valore predefinito | Descrizione |
|----------|----------|----------|----------|
| MixerMode | UINT32 | 2 (MIC e audio di sistema) | Enum usato per indicare le origini audio da usare: 0 (solo audio MIC), 1 (solo audio di sistema), 2 (MIC e audio di sistema) |
| LoopbackGain | float | Impostazione di **miglioramento audio app** nel portale per dispositivi Windows | Ottenere da applicare al volume audio del sistema. Compreso tra 0,0 e 5,0. Supportato solo su HoloLens 2 |
| MicrophoneGain | float | Impostazione del **guadagno audio mic** nel portale del dispositivo Windows | Ottenere da applicare al volume MIC. Compreso tra 0,0 e 5,0. Supportato solo su HoloLens 2 |

>[!NOTE]
> È possibile modificare il valore predefinito di **LoopbackGain** o **MicrophoneGain** nel portale per dispositivi Windows passando alla pagina di [acquisizione della realtà mista](using-the-windows-device-portal.md#mixed-reality-capture) e modificando il dispositivo di scorrimento accanto alle rispettive impostazioni. Per impostazione predefinita, entrambe le impostazioni sono **1,0**, ma possono essere impostate su qualsiasi valore compreso tra **0,0** e **5,0**.
>
> L'uso del portale per dispositivi Windows per configurare i valori di guadagno predefiniti è stato aggiunto con l'aggiornamento di giugno 2020 (Windows olografico, versione 2004 Build 19041,1106 e Windows olografico, versione 1903 Build 18362,1064).

### <a name="simultaneous-mrc-limitations"></a>Limitazioni di MRC simultanee

Esistono alcune limitazioni relative a più app che accedono a MRC nello stesso momento.

#### <a name="photovideo-camera-access"></a>Accesso alla fotocamera foto/video

La fotocamera Photo/video è limitata al numero di processi che possono accedervi nello stesso momento. Durante la registrazione di un processo video o la creazione di una foto, qualsiasi altro processo non riuscirà ad acquisire la fotocamera foto/video. Questo vale sia per l'acquisizione di realtà mista sia per l'acquisizione di foto/video standard.

Con HoloLens 2, un'app può usare la proprietà [SharingMode](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode) di MediaCaptureInitializationSettings per indicare che desiderano eseguire SharedReadOnly se non necessitano di controllo esclusivo sulla fotocamera foto/video. In questo modo, la risoluzione e il framerate dell'acquisizione saranno limitati a ciò che altre app hanno configurato la fotocamera per fornire.

##### <a name="built-in-mrc-photovideo-camera-access"></a>Accesso a foto/video della fotocamera MRC incorporato

Funzionalità MRC incorporata in Windows 10 (tramite Cortana, menu Start, collegamenti hardware, Miracast, portale per dispositivi Windows):
* Per impostazione predefinita, viene eseguito con ExclusiveControl

Tuttavia, il supporto è stato aggiunto a ogni sottosistema per operare in modalità condivisa:
* Se un'app richiede l'accesso ExclusiveControl alla fotocamera Photo/video, la funzionalità MRC predefinita si interrompe automaticamente usando la fotocamera foto/video, in modo che la richiesta dell'app venga completata
* Se viene avviata la funzionalità MRC incorporata mentre un'app include ExclusiveControl, la funzionalità MRC predefinita verrà eseguita in modalità SharedReadOnly

Questa funzionalità in modalità condivisa presenta alcune restrizioni:
* Foto tramite Cortana, collegamenti hardware o menu Start: richiede l'aggiornamento di Windows 10 aprile 2018 (o versione successiva)
* Video tramite Cortana, collegamenti hardware o menu Start: richiede l'aggiornamento di Windows 10 aprile 2018 (o versione successiva)
* Streaming MRC over Miracast: richiede l'aggiornamento di Windows 10 ottobre 2018 (o versione successiva)
* Streaming di MRC sul portale per dispositivi Windows o tramite l'app complementare HoloLens: richiede HoloLens 2

>[!NOTE]
> La risoluzione e il framerate dell'interfaccia utente della fotocamera MRC integrata potrebbero essere ridotti dai valori normali quando un'altra app usa la fotocamera foto/video.

#### <a name="mrc-access"></a>Accesso a MRC

Con l'aggiornamento di Windows 10 aprile 2018, non esiste più una limitazione per più app che accedono al flusso MRC. Tuttavia, l'accesso alla videocamera Photo/video presenta ancora alcune limitazioni.

In precedenza all'aggiornamento di Windows 10 aprile 2018, il registratore MRC personalizzato di un'app si escludono a vicenda con il sistema MRC (acquisizione di foto, acquisizione di video o flusso dal portale per dispositivi Windows).

## <a name="see-also"></a>Vedere anche

* [Acquisizione in realtà mista (MRC, Mixed Reality Capture)](mixed-reality-capture.md)
* [Visualizzazione spettatore](spectator-view.md)
* [Panoramica sullo sviluppo Unity](unity-development-overview.md)
* [Panoramica dello sviluppo con Unreal](unreal-development-overview.md)

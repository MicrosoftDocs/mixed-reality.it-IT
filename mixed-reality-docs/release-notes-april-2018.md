---
title: Note sulla versione-2018 aprile
description: Note sulla versione di HoloLens e Windows Mixed Reality per l'aggiornamento di Windows 10 aprile 2018 (noto anche come RS4).
author: mattzmsft
ms.author: mazeller
ms.date: 05/21/2018
ms.topic: article
keywords: Note sulla versione, versione, Windows 10, compilazione, RS4, sistema operativo
ms.openlocfilehash: 1fc1b43b0581234e835379fd553b78121108086e
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524171"
---
# <a name="release-notes---april-2018"></a>Note sulla versione-2018 aprile

L' **[aggiornamento di Windows 10 aprile 2018](https://blogs.windows.com/windowsexperience/2018/04/30/whats-new-in-the-windows-10-april-2018-update)** (noto anche come RS4) include nuove funzionalità per gli auricolari HoloLens e Windows misto realtà mista connessi ai PC. 

Per eseguire l'aggiornamento alla versione più recente per uno dei due tipi di dispositivo, aprire l'app **Impostazioni** , passare a **Aggiorna & sicurezza**, quindi selezionare il pulsante **Controlla aggiornamenti** . In un PC Windows 10, è anche possibile installare manualmente l'aggiornamento di Windows 10 aprile 2018 usando lo [strumento di creazione di Windows Media](https://www.microsoft.com/software-download/windows10).

**Versione più recente per desktop:** Aggiornamento di Windows 10 aprile 2018 (**10.0.17134.1**)<br>
**Versione più recente per HoloLens:** Aggiornamento di Windows 10 aprile 2018 (**10.0.17134.80**)<br>
<br>

>[!VIDEO https://www.youtube.com/embed/O-84oWjSbr0]

*Un messaggio di Alex Kipman e una panoramica delle nuove funzionalità di realtà mista nell'aggiornamento di Windows 10 aprile 2018*

## <a name="new-features-for-windows-mixed-reality-immersive-headsets"></a>Nuove funzionalità per gli auricolari immersivi a realtà mista di Windows

L'aggiornamento di Windows 10 aprile 2018 include numerosi miglioramenti per l'uso di auricolari con la realtà mista (VR) di Windows con il PC desktop, ad esempio: 

* **Nuovi ambienti per la Home realtà mista** : è ora possibile scegliere tra The Cliff House e il nuovo ambiente Skyloft selezionando **posizioni** nel menu Start. È stata anche aggiunta [una funzionalità sperimentale](add-custom-home-environments.md) che consente di usare ambienti personalizzati creati.
* **Accesso rapido all'acquisizione di realtà mista** : è ora possibile eseguire foto di realtà miste usando un controller di movimento. Premere il pulsante Windows e quindi toccare il trigger. Funziona in ambienti e app, ma non acquisisce contenuti protetti con DRM.
* Le **nuove opzioni per l'avvio e** il ridimensionamento del contenuto-app vengono ora posizionate automaticamente prima di essere avviate dal menu Start. È anche possibile ridimensionare le app 2D trascinando i bordi e gli angoli della finestra.
* **Passare facilmente al contenuto con il comando Voice "Teleport"** . è ora possibile effettuare rapidamente il Teleport di fronte al contenuto della Home realtà mista di Windows guardando il contenuto e affermando "Teleport".
* Avvii di  **[app 3D animati](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#animation-guidelines) e [oggetti 3D decorativi](enable-placement-of-3d-models-in-the-home.md) per la Home realtà mista** : è ora possibile aggiungere animazioni ai lanci di app 3D e consentire agli utenti di inserire modelli 3D decorativi da una pagina Web o un'app 2D nella Home realtà mista di Windows.
* I miglioramenti apportati **[alla realtà mista di Windows per SteamVR](updating-your-steamvr-application-for-windows-mixed-reality.md)** , la realtà mista di Windows per SteamVR, sono fuori "accesso anticipato" con nuovi aggiornamenti, tra cui: feedback tattile quando si usano i controller di movimento, prestazioni e affidabilità migliorate e miglioramenti al aspetto dei controller di movimento in SteamVR.
* **Altri miglioramenti** : le impostazioni delle prestazioni automatiche sono state aggiornate per offrire un'esperienza più ottimizzata. è possibile [sostituire manualmente](#visual-quality) questa impostazione. Il programma di installazione offre ora informazioni più dettagliate sui problemi di compatibilità comuni con i controller USB 3,0 e le schede grafiche.

## <a name="new-features-for-hololens"></a>Nuove funzionalità per HoloLens

L'aggiornamento di Windows 10 aprile 2018 è arrivato per tutti i clienti di HoloLens. Questo aggiornamento include miglioramenti introdotti dopo l'ultima versione principale di HoloLens software nel [2016 agosto](release-notes-august-2016.md).

### <a name="for-everyone"></a>Per tutti

<table>
  <tr>
    <th>Funzionalità</th><th>Dettagli</th><th>Istruzioni</th>
  </tr>
  <tr>
    <td>Posizionamento automatico del contenuto 2D e 3D all'avvio</td><td>Un utilità di avvio di app 2D o un'app UWP 2D posiziona automaticamente nel mondo a una dimensione e una distanza ottimali quando viene avviata, anziché richiedere all'utente di inserirlo. Se un' <a href="app-views.md">app immersiva</a> usa un utilità di avvio di app 2D invece di un <a href="3d-app-launcher-design-guidance.md">Launcher di app 3D</a>, l'app immersiva verrà avviata automaticamente dall'utilità di avvio di app 2D, come in RS1.<br><br>Un avvio di app 3D dal menu Start si inserisce anche automaticamente nel mondo. Anziché avviare automaticamente l'app, gli utenti possono fare clic sul pulsante di avvio per avviare l'app immersiva. contenuto 3D aperto dall'app olografici e dal bordo automatico anche nel mondo.</td><td>Quando si apre un'app dal menu Start, non verrà più richiesto di inserirla nel mondo.<br><br>Se il posizionamento dell'<a href="3d-app-launcher-design-guidance.md">utilità di avvio</a> dell'app 2D o dell'app 3D non è ottimale, è possibile spostarli facilmente usando le nuove modifiche di app fluide descritte di seguito. È anche possibile riposizionare il contenuto 3D o l'utilità di avvio di app 2D digitando "sposta questo" e quindi usando lo sguardo per riposizionare il contenuto.</td>
  </tr>
  <tr>
    <td>Manipolazione di app fluide</td><td>Spostare, ridimensionare e ruotare il contenuto 2D e 3D senza dover immettere la modalità "Adjust".</td><td>Per spostare un'app UWP 2D o un utilità di avvio di app 2D, è sufficiente guardare la barra dell'app e quindi usare il movimento Tap + trattieni + trascina. È possibile spostare il contenuto 3D osservando un punto qualsiasi dell'oggetto e quindi usando Tap + trattieni + drag.<br><br>Per ridimensionare il contenuto 2D, guarda l'angolo. Il cursore dello sguardo si trasforma in un cursore di ridimensionamento, quindi è possibile toccare + Mantieni + trascina per ridimensionare. È anche possibile rendere il contenuto 2D più alto o più ampio osservando i relativi bordi e trascinamento.<br><br>Per ridimensionare il contenuto 3D, sollevare entrambe le mani nel frame di movimento, quindi passare alla posizione pronta. Si noterà che il cursore si trasforma in uno stato con due poche mani. Eseguire il tocco e mantenere il gesto con entrambe le mani. Spostando le mani più vicine o più lontane, si modificano le dimensioni dell'oggetto. Se si spostano le mani avanti e indietro rispetto all'altra, l'oggetto viene ruotato. È anche possibile ridimensionare/ruotare il contenuto 2D in questo modo.</td>
  </tr>
  <tr>
    <td>ridimensionamento orizzontale app 2D con riflusso</td><td>Per visualizzare più contenuto dell'app, è possibile creare un'app UWP 2D più ampia in proporzioni. Ad esempio, rendere l'app di posta elettronica sufficientemente ampia per visualizzare il riquadro di anteprima.</td><td>È sufficiente guardare il bordo sinistro o destro dell'app UWP 2D per visualizzare il cursore di ridimensionamento, quindi usare l'azione Tap + trattieni + trascina per ridimensionare.</td>
  </tr>
  <tr>
    <td>Supporto del comando Voice espanso</td><td>È possibile fare più semplicemente uso della propria voce.</td><td>Provare questi comandi vocali:<ul><li>"Vai a avvio"-Visualizza il menu Start o esce da un' <a href="app-views.md">app immersiva</a>.</li><li>"Sposta questo": consente di spostare un oggetto.</li></ul></td>
  </tr>
  <tr>
    <td>App per ologrammi e foto aggiornate</td><td>App ologrammi aggiornata con nuovi ologrammi. App Photos aggiornata.</td><td>Si noterà un aspetto aggiornato delle app per ologrammi e foto. L'app ologrammi include diversi nuovi ologrammi e un produttore di etichette per semplificare la creazione di testo.</td>
  </tr>
  <tr>
    <td>Acquisizione della realtà mista migliorata</td><td>Video di avvio e fine del collegamento hardware.</td><td>Attendere 3 secondi per avviare la registrazione del video MRC. Toccare di nuovo o usare il gesto Bloom per terminare.</td>
  </tr>
  <tr>
    <td>Spazi consolidati</td><td>Semplifica la gestione dello spazio per gli ologrammi in uno spazio singolo.</td><td>HoloLens consente di trovare automaticamente lo spazio e non è più necessario gestire o selezionare spazi. In caso di problemi con gli ologrammi, è possibile passare a <b>impostazioni > sistema > ologrammi > rimuovere gli ologrammi vicini</b>. Se necessario, è anche possibile selezionare <b>Rimuovi tutti gli ologrammi</b>.</td>
  </tr>
  <tr>
    <td>Migliore immersione audio</td><td>È ora possibile sentire meglio HoloLens in ambienti rumorosi e sperimentare un suono più realistico dalle applicazioni perché il loro suono sarà oscurato da muri reali rilevati dal dispositivo.</td><td>Non è necessario eseguire alcuna operazione per sfruttare il suono spaziale migliorato.</td>
  </tr>
  <tr>
    <td>Esplora file</td><td>Spostare ed eliminare i file dall'interno di HoloLens.</td><td>È possibile usare l'app <b>Esplora file</b> per spostare ed eliminare i file dall'interno di HoloLens.<br><br><b>Punta</b> Se non viene visualizzato alcun file, il filtro "recente" potrebbe essere attivo (l'icona di clock è evidenziata nel riquadro sinistro). Per risolvere il problema, selezionare l'icona del documento del <b>dispositivo</b> nel riquadro sinistro, sotto l'icona di clock, oppure aprire il menu e selezionare il <b>dispositivo</b>.
</td>
  </tr>
  <tr>
    <td>Supporto per MTP (Media Transfer Protocol)</td><td>Consente al PC desktop di accedere alle librerie (foto, video, documenti) in HoloLens per un trasferimento semplice.</td><td>Analogamente ad altri dispositivi mobili, connettere la HoloLens al PC per visualizzare <b>Esplora file</b> per accedere alle librerie di HoloLens (foto, video, documenti) per un trasferimento semplice.<br><br><b>Consigli</b><ul><li>Se non viene visualizzato alcun file, assicurarsi di accedere a HoloLens per abilitare l'accesso ai dati.</li><li>Da <b>Esplora file</b> nel PC è possibile selezionare le <b>proprietà del dispositivo</b> per visualizzare il numero di versione del sistema operativo Windows (versione del firmware) e il numero di serie del dispositivo.</li></ul><b>Problema noto:</b> La ridenominazione di HoloLens tramite <b>Esplora file</b> nel PC non è abilitata.</td>
  </tr>
  <tr>
    <td>Supporto della rete Captive Portal durante l'installazione</td><td>È ora possibile configurare la HoloLens in una rete Guest in alberghi, centri conferenze, negozi commerciali o aziende che usano Captive Portal.</td><td>Durante l'installazione, selezionare la rete, controllare Connetti automaticamente se lo si desidera e immettere le informazioni di rete come richiesto.</td>
  </tr>
  <tr>
    <td>Sincronizzazione di foto e video tramite l'app OneDrive</td><td>Le foto e i video di HoloLens verranno sincronizzati tramite l'app OneDrive dal Microsoft Store invece che direttamente dall'app Photos.</td><td>Per configurare questa impostazione, scaricare e avviare l'app OneDrive dallo Store. Alla prima esecuzione verrà richiesto di caricare automaticamente le foto in OneDrive, oppure è possibile trovare l'opzione nelle impostazioni dell'app.</td>
  </tr>
</table>

### <a name="for-developers"></a>Per sviluppatori

<table>
  <tr>
    <th>Funzionalità</th><th>Dettagli</th><th>Istruzioni</th>
  </tr>
  <tr>
    <td>Miglioramenti al mapping spaziale</td><td>Miglioramento qualitativo, semplificato e delle prestazioni.</td><td>La mesh di mapping spaziale verrà visualizzata come più pulita: sono necessari meno triangoli per rappresentare lo stesso livello di dettaglio. È possibile notare modifiche nella densità dei triangoli nella scena.</td>
  </tr>
  <tr>
    <td>Selezione automatica del punto di interesse in base al buffer di profondità</td><td>L'invio di un buffer di profondità a Windows consente a HoloLens di selezionare automaticamente un punto di attivazione per ottimizzare la stabilità degli ologrammi.</td><td>In Unity passare a <b>Edit > Project settings > Player > piattaforma UWP (Universal Windows Platform) tab > XR Settings</b>, expand the <b>Windows Mixed Reality SDK</b> Item e assicurarsi che <b>Enable depth buffer sharing</b> sia selezionato. Questa operazione verrà verificata automaticamente per i nuovi progetti.<br><br>Per le app DirectX, assicurarsi di chiamare il metodo <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer">CommitDirect3D11DepthBuffer</a> su <b>HolographicRenderingParameters</b> ogni frame per fornire il buffer di profondità a Windows.
</td>
  </tr>
  <tr>
    <td>Modalità di riproiezione olografica</td><td>È ora possibile disabilitare la riproiezione posizionale in HoloLens per migliorare la stabilità dell'ologramma del contenuto rigidamente bloccato del corpo, ad esempio un video di 360 gradi.</td><td>In Unity impostare <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html">HolographicSettings. ReprojectionMode</a> su <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html">HolographicReprojectionMode. OrientationOnly</a> quando tutto il contenuto nella visualizzazione è rigidamente bloccato dal corpo.<br><br>Per le app DirectX, impostare <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.reprojectionmode">HolographicCameraRenderingParameters. ReprojectionMode</a> su <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicreprojectionmode">HolographicReprojectionMode. OrientationOnly</a> quando tutto il contenuto nella visualizzazione è rigidamente bloccato dal corpo.</td>
  </tr>
  <tr>
    <td>API di personalizzazione delle app</td><td>Le API di Windows sono in grado di ottenere altre informazioni sulla posizione in cui è in esecuzione l'app, ad esempio se il display del dispositivo è trasparente (HoloLens) o opaco (auricolare immersivo) e se la visualizzazione 2D di un'app UWP è visualizzata nella shell olografica.</td><td>Unity ha precedentemente esposto manualmente <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html">HolographicSettings. IsDisplayOpaque</a> in un modo che funzionava anche prima di questa compilazione.<br><br>Per le app DirectX, ora è possibile accedere ad API esistenti come <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.isopaque">HolographicDisplay. GetDefault (). Sia Opaque</a> che <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview.iscurrentviewpresentedonholographicdisplay">HolographicApplicationPreview. IsCurrentViewPresentedOnHolographicDisplay</a> in HoloLens.
</td>
  </tr>
  <tr>
      <td>Modalità di ricerca</td><td>Consente agli sviluppatori di accedere ai sensori HoloLens chiave quando si compilano applicazioni accademiche e industriali per testare nuove idee nei campi della visione artificiale e dei robot, tra cui:<ul><li>Le quattro fotocamere di rilevamento dell'ambiente</li><li>Due versioni dei dati della fotocamera con mapping di profondità</li><li>Due versioni di un flusso IR-riflettività</li></ul></td><td><a href="research-mode.md">Documentazione sulla modalità di ricerca</a><br><a href="https://github.com/Microsoft/HoloLensForCV">App di esempio per la modalità di ricerca</a></td>
  </tr>
</table>

### <a name="for-commercial-customers"></a>Per i clienti commerciali

<table>
  <tr>
    <th>Funzionalità</th><th>Dettagli</th><th>Istruzioni</th>
  </tr>
  <tr>
    <td>Usare più account utente Azure Active Directory in un singolo dispositivo</td><td>Condividere un HoloLens con più utenti Azure AD, ognuno con le proprie impostazioni utente e i dati utente nel dispositivo.</td><td><a href="https://docs.microsoft.com/hololens/hololens-multiple-users">Centro per professionisti IT: Condividi HoloLens con più persone</a></td>
  </tr>
  <tr>
    <td>Modificare la rete Wi-Fi all'accesso</td><td>Modificare la rete Wi-Fi prima di accedere per consentire a un altro utente di accedere con il proprio account utente Azure AD per la prima volta, consentendo agli utenti di condividere i dispositivi in diverse posizioni e siti di lavoro.</td><td>Nella schermata di accesso è possibile usare l'icona di rete sotto il campo password per connettersi a una rete. Questa operazione è utile quando è la prima volta che si accede a un dispositivo.</td>
  </tr>
  <tr>
    <td>Registrazione unificata</td><td>È ora facile per un utente HoloLens che configura il dispositivo con un account Microsoft personale per aggiungere un account di lavoro (Azure AD) e aggiungere il dispositivo al server MDM.</td><td>È sufficiente accedere con un account di Azure AD e la registrazione viene eseguita automaticamente.</td>
  </tr>
  <tr>
    <td>Sincronizzazione della posta senza registrazione MDM</td><td>Supporto per la sincronizzazione della posta Exchange Active Sync (EAS) senza richiedere la registrazione MDM.</td><td>È ora possibile sincronizzare la posta elettronica senza registrazione in MDM. È possibile configurare il dispositivo con un account Microsoft, scaricare e installare l'app di posta elettronica e aggiungere direttamente un account di posta elettronica di lavoro.</td>
  </tr>
</table>

### <a name="for-it-pros"></a>Per i professionisti IT

<table>
  <tr>
    <th>Funzionalità</th><th>Dettagli</th><th>Istruzioni</th>
  </tr>
  <tr>
    <td>Nuovo nome del sistema operativo "Windows Olografic for business"</td><td>Cancella la denominazione dell'edizione per ridurre la confusione nell'applicazione di licenza per l'aggiornamento dell'edizione quando le funzionalità della suite commerciale sono abilitate in HoloLens.</td><td>È possibile visualizzare l'edizione di Windows olografica sul dispositivo in <b>impostazioni > sistema > informazioni</b>su. "Windows Olografic for business" verrà visualizzato se è stato applicato un aggiornamento dell'edizione per abilitare le funzionalità della suite commerciale. Informazioni su come <a href="https://docs.microsoft.com/hololens/hololens-upgrade-enterprise">sbloccare le funzionalità di Windows olografico per le aziende</a>.</td>
  </tr>
  <tr>
  <td>Progettazione configurazione Windows (WCD)</td><td>Creare e modificare i pacchetti di provisioning per configurare HoloLens tramite l'app WCD aggiornata. Procedura guidata HoloLens semplice per l'aggiornamento dell'edizione, OOBE configurabile, area/fuso orario, token Azure AD Bulk, rete e CSP per sviluppatori. Editor avanzato filtrato per le opzioni supportate da HoloLens, inclusi i CSP di accesso e di gestione degli account assegnati.</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">Centro per professionisti IT: Configurare HoloLens usando un pacchetto di provisioning</a></td>
  </tr>
  <tr>
    <td>Configurazione configurabile (OOBE)</td><td>Nascondi le schermate di calibrazione, movimento/sguardo e configurazione Wi-Fi durante l'installazione.</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning#create-a-provisioning-package-for-hololens-using-the-hololens-wizard">Centro per professionisti IT: Configurare HoloLens usando un pacchetto di provisioning</a></td>
  </tr>
  <tr>
    <td>Supporto per token Azure AD Bulk</td><td>Pre-registrare il dispositivo nel tenant di Azure AD directory per un flusso di installazione utente più rapido.</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">Centro per professionisti IT: Configurare HoloLens usando un pacchetto di provisioning</a></td>
  </tr>
  <tr>
  <td>CSP DeveloperSetup</td><td>Distribuire il profilo per configurare HoloLens in modalità sviluppatore. Utile per i dispositivi di sviluppo e demo.</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">Centro per professionisti IT: Configurare HoloLens usando un pacchetto di provisioning</a></td>
  </tr>
  <tr>
  <td>CSP AccountManagement</td><td>Condividere un dispositivo HoloLens e rimuovere i dati utente dopo la disconnessione o le soglie di inattività/archiviazione per l'utilizzo temporaneo. Supporta gli account Azure AD.</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">Centro per professionisti IT: Configurare HoloLens usando un pacchetto di provisioning</a></td>
  </tr>
  <tr>
  <td>Accesso assegnato</td><td>Windows ha assegnato l'accesso per i ruoli di lavoro o le demo di prima riga. Blocco single o multiapp. Non è necessario sbloccare lo sviluppatore.</td><td><a href="https://docs.microsoft.com/hololens/hololens-kiosk">Centro per professionisti IT: Configurare HoloLens in modalità tutto schermo</a></td>
  </tr>
  <tr>
  <td>Accesso guest per dispositivi Kiosk</td><td>Windows ha assegnato l'accesso con un account Guest senza password per le demo. Blocco single o multiapp. Non è necessario sbloccare lo sviluppatore.</td><td><a href="https://docs.microsoft.com/hololens/hololens-kiosk#guest">Centro per professionisti IT: Configurare HoloLens in modalità tutto schermo</a></td>
  </tr>
  <tr>
    <td>Diagnostica configurazione (configurazione guidata)</td><td>Ottenere i log di diagnostica da HoloLens per risolvere gli errori di accesso Azure AD (prima che l'hub feedback sia disponibile per l'utente il cui accesso non è riuscito).</td><td>Quando si verifica un errore durante l'installazione o l'accesso, scegliere la nuova opzione <b>Collect info</b> per ottenere i log di diagnostica per la risoluzione dei problemi.</td>
  </tr>
  <tr>
    <td>Scadenza password indefinita account locale</td><td>Rimuovere l'interferenza della reimpostazione del dispositivo quando la password dell'account locale scade.</td><td>Quando si esegue il provisioning di un account locale, non è più necessario modificare la password ogni 42 giorni in <b>Impostazioni</b>, perché la password dell'account non scade più.</td>
  </tr>
  <tr>
    <td>Stato e dettagli della sincronizzazione MDM</td><td>Funzionalità standard di Windows per comprendere lo stato e i dettagli della sincronizzazione MDM dall'interno di HoloLens.</td><td>È possibile controllare lo stato di sincronizzazione MDM per un dispositivo in <b>impostazioni > account > accedere a informazioni > lavoro o dell'Istituto di istruzione</b>. Nella sezione <b>stato<b> sincronizzazione del dispositivo è possibile avviare una sincronizzazione, vedere aree gestite da MDM e creare ed esportare un report di diagnostica avanzata.</td>
  </tr>
</table>

## <a name="known-issues"></a>Problemi noti

Abbiamo lavorato duramente per offrire un'eccezionale esperienza di realtà mista di Windows, ma stiamo ancora verificando alcuni problemi noti. Se si trovano altre persone, inviare [commenti e suggerimenti](give-us-feedback.md).

### <a name="hololens"></a>HoloLens

#### <a name="after-update"></a>Dopo l'aggiornamento

È possibile riscontrare i seguenti problemi dopo l'aggiornamento da RS1 a RS4 in HoloLens:
* **Pin reimpostazione** : le app 3x3 aggiunte al menu Start verranno reimpostate sui valori predefiniti dopo l'aggiornamento. 
* Le **app e** gli ologrammi vengono reimpostati. le app inserite nel mondo verranno rimosse dopo l'aggiornamento e dovranno essere riposizionate in tutto lo spazio. 
* L' **Hub di feedback potrebbe non essere avviato immediatamente** . dopo l'aggiornamento, saranno necessari alcuni minuti prima di poter avviare alcune app della posta in arrivo, ad esempio l'hub di feedback, durante l'aggiornamento. 
* È **necessario ripetere la sincronizzazione dei certificati Wi-Fi aziendali** . si sta esaminando un problema che richiede che il HoloLens sia connesso a una rete diversa affinché i certificati aziendali vengano nuovamente sincronizzati con il dispositivo prima che sia in grado di riconnettersi all'azienda reti con certificati. 
* **H. 265 HEVC la riproduzione video non funziona** : le applicazioni che tentano di riprodurre i video h. 265 riceveranno un messaggio di errore. La soluzione alternativa consiste nell' [accedere al portale del dispositivo Windows](using-the-windows-device-portal.md), selezionare **app** sulla barra di spostamento a sinistra e **rimuovere** l'applicazione HEVC. Quindi, installare la versione più recente dell' [estensione video HEVC](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7) dall'Microsoft Store. Stiamo esaminando il problema. 

#### <a name="for-developers-updating-hololens-apps-for-devices-running-windows-10-april-2018-update"></a>Per gli sviluppatori: aggiornamento delle app HoloLens per i dispositivi che eseguono l'aggiornamento di Windows 10 aprile 2018

Insieme a un ottimo elenco di [nuove funzionalità](#new-features-for-hololens), l'aggiornamento di Windows 10 aprile 2018 (RS4) per HoloLens impone alcuni comportamenti del codice non disponibili nelle versioni precedenti:
* **Richieste di autorizzazione per l'uso di risorse sensibili (fotocamera, microfono e così via)** -RS4 in HoloLens impone richieste di autorizzazione per le app che tendono ad accedere a risorse sensibili, ad esempio la fotocamera o il microfono. RS1 in HoloLens non ha forzato queste richieste, quindi, se l'app presuppone l'accesso immediato a queste risorse, è possibile che si verifichi un arresto anomalo in RS4 (anche se l'utente concede l'autorizzazione per la risorsa richiesta). Per ulteriori informazioni, leggere l'articolo relativo alle [dichiarazioni sulle funzionalità delle app UWP](https://docs.microsoft.com/windows/uwp/packaging/app-capability-declarations) .
* Le **chiamate alle app all'esterno del proprio** -RS4 in HoloLens imporrà l'uso corretto della [classe *Windows. System. Launcher* ](https://docs.microsoft.com/uwp/api/Windows.System.Launcher) per avviare un'altra app dal proprio. Ad esempio, sono stati riscontrati problemi con le app che chiamano *Windows. System. Launcher. LaunchUriForResultsAsync* da un thread non asta (UI). Questa operazione avrà esito positivo in RS1 in HoloLens, ma la chiamata deve essere eseguita sul thread dell'interfaccia utente.

### <a name="windows-mixed-reality-on-desktop"></a>Realtà mista di Windows sul desktop

#### <a name="visual-quality"></a>Qualità visiva

* Se si nota dopo l'aggiornamento di Windows 10 aprile 2018 che la grafica è più sfocata rispetto a prima o che il campo di visualizzazione risulta più piccolo nell'auricolare, è possibile che l'impostazione delle prestazioni automatica sia stata modificata in modo da mantenere un framerate sufficiente a un livello meno potente scheda grafica (ad esempio NVIDIA 1050). È possibile eseguire manualmente l'override di questa opzione (se si sceglie) passando a **impostazioni > realtà mista > visualizzare > Opzioni di esperienza > modificare** e cambiando "automatico" in "90 Hz". È anche possibile provare a modificare la **qualità visiva** (nella stessa pagina delle impostazioni) in "High".

#### <a name="windows-mixed-reality-setup"></a>Configurazione della realtà mista di Windows

* Quando si configura Windows con una cuffia connessa, il monitor del PC potrebbe essere vuoto. Scollegare la cuffia per abilitare l'output del monitor PC per completare l'installazione di Windows.
* Se non si dispone di cuffie connesse, è possibile che non si verifichino ulteriori suggerimenti quando si visita la Home realtà mista di Windows.
* Altri dispositivi Bluetooth possono causare interferenze con i controller di movimento. Se i controller di movimento hanno problemi di connessione/associazione/rilevamento, assicurarsi che la radio Bluetooth (se un dongle esterno) sia collegata a una posizione non bloccata e non immediatamente accanto a un altro dongle Bluetooth. Provare anche a spegnere altre periferiche Bluetooth durante le sessioni di realtà mista di Windows per verificare se è utile.

#### <a name="games-and-apps-from-the-microsoft-store"></a>Giochi e app dal Microsoft Store

* Alcuni giochi a elevato utilizzo di grafica, come Forza Motorsport 7, possono causare problemi di prestazioni sui PC meno idonei quando vengono riprodotti in realtà mista di Windows.

#### <a name="audio"></a>Audio

* Se la Cortana è abilitata nel computer host prima di usare l'auricolare con la realtà mista di Windows, è possibile perdere la simulazione del suono spaziale applicata alle app inserite nella Home realtà mista di Windows. 
   * La soluzione è quella di abilitare "Windows Sonic per le cuffie" in tutti i dispositivi audio collegati al PC, anche il dispositivo audio connesso all'auricolare:
      1. Fare clic sull'icona dell'altoparlante sulla barra delle applicazioni del desktop e selezionare da un elenco di dispositivi audio.
      2. Fare clic con il pulsante destro del mouse sull'icona dell'altoparlante sulla barra delle applicazioni del desktop e selezionare "Windows Sonic per le cuffie" nel menu "impostazione del relatore".
      3. Ripetere questi passaggi per tutti i dispositivi audio (endpoint).
   * Un'altra opzione è la disattivazione di "Let Cortana rispondere a Hey Cortana" in **Settings** > **Cortana** on the desktop prima di avviare la realtà mista di Windows.
* Quando un altro dispositivo USB multimediale (ad esempio una Web Cam) condivide lo stesso hub USB (esterno o all'interno del PC) con l'auricolare della realtà mista di Windows, in rari casi è possibile che lo spinotto/le cuffie audio dell'auricolare abbia un segnale acustico o nessun audio. È possibile risolvere il problema tramite la cuffia in una porta USB che non condivide lo stesso hub dell'altro dispositivo oppure disconnettere/disabilitare l'altro dispositivo multimediale USB.
* In rari casi, l'hub USB del PC host non è in grado di fornire una potenza sufficiente per l'auricolare della realtà mista di Windows e potrebbe verificarsi un aumento del rumore dalle cuffie connesse all'auricolare.

#### <a name="holograms"></a>Ologrammi

* Se è stato inserito un numero elevato di ologrammi nella Home page della realtà mista di Windows, alcuni possono scomparire e riapparire durante l'aspetto. Per evitare questo problema, rimuovere alcuni degli ologrammi in quell'area della Home realtà mista di Windows.

#### <a name="motion-controllers"></a>Controller di movimento

* Se l'input non viene indirizzato all'auricolare, il controller di movimento scomparirà brevemente quando verrà mantenuto accanto al limite della stanza. Se si preme Win + Y per verificare che sia presente un banner blu attraverso il monitor desktop, questa operazione verrà risolta. 
* Occasionalmente, quando si fa clic su una pagina Web in Microsoft Edge, il contenuto viene ingrandito anziché fare clic su.

#### <a name="desktop-app-in-the-windows-mixed-reality-home"></a>App desktop nella Home realtà mista di Windows

* Lo strumento di cattura non funziona nell'app desktop.
* L'app desktop non mantiene l'impostazione al nuovo avvio.
* Se si usa l'anteprima del portale di realtà mista sul desktop, quando si apre l'app desktop nella Home realtà mista di Windows, è possibile notare l'effetto di mirror infinito. 
* L'esecuzione dell'applicazione desktop può causare problemi di prestazioni in PC con una realtà mista Windows non ultra-ultra; non è consigliabile.  
* L'app desktop può essere avviata automaticamente perché una finestra invisibile sul desktop ha lo stato attivo. 
* La richiesta di controllo dell'account utente desktop renderà la visualizzazione della cuffia nera fino al completamento della richiesta.

#### <a name="windows-mixed-reality-for-steamvr"></a>Realtà mista di Windows per SteamVR

* Potrebbe essere necessario avviare il portale di realtà mista dopo l'aggiornamento per assicurarsi che gli aggiornamenti software necessari per l'aggiornamento di Windows 10 aprile 2018 siano stati completati prima di avviare SteamVR. 
* Per mantenere la compatibilità con l'aggiornamento di Windows 10 aprile 2018, è necessario disporre di una versione recente di Windows Mixed Reality per SteamVR. Assicurarsi che gli aggiornamenti automatici siano attivati per la realtà mista di Windows per SteamVR, che si trova nella sezione "software" della libreria in Steam.  

#### <a name="other-issues"></a>Altri problemi

>[!IMPORTANT]
>Una versione iniziale dell'aggiornamento di Windows 10 aprile 2018 push a Insider (versione 17134,5) mancava un componente software necessario per eseguire la realtà mista di Windows. È consigliabile evitare questa versione se si usa la realtà mista di Windows. 

È stata identificata una regressione delle prestazioni quando si usa Surface Book 2 nella versione iniziale di questo aggiornamento (10.0.17134.1) che stiamo lavorando per correggere in una patch di aggiornamento imminente. È consigliabile attendere fino a quando il problema non è stato corretto prima di eseguire l'aggiornamento manualmente o in attesa dell'implementazione normale dell'aggiornamento.

## <a name="provide-feedback-and-report-issues"></a>Inviare commenti e suggerimenti e segnalare problemi

Usare l' [App Hub di feedback in HoloLens o Windows 10 PC](give-us-feedback.md) per inviare commenti e suggerimenti e segnalare problemi. L'uso dell'hub feedback garantisce che tutte le informazioni di diagnostica necessarie siano incluse per aiutare i nostri tecnici a eseguire rapidamente il debug e risolvere il problema.

>[!NOTE]
>Assicurarsi di accettare il prompt che chiede se si vuole che l'hub feedback acceda alla cartella documenti (selezionare **Sì** quando richiesto).

## <a name="prior-release-notes"></a>Note sulla versione precedente

* [Note sulla versione - ottobre 2017](release-notes-october-2017.md)
* [Note sulla versione - agosto 2016](release-notes-august-2016.md)
* [Note sulla versione - maggio 2016](release-notes-may-2016.md)
* [Note sulla versione - marzo 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Vedere anche
* [Supporto per cuffie immersive (collegamento esterno)](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)
* [Supporto di HoloLens (collegamento esterno)](https://support.microsoft.com/products/hololens)
* [Installare gli strumenti](install-the-tools.md)
* [Inviare commenti e suggerimenti](give-us-feedback.md)


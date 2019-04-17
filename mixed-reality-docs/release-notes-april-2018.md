---
title: Note sulla versione - aprile 2018
description: HoloLens e note sulla versione di realtà mista di Windows per Windows 10 April 2018 Update (noto anche come RS4).
author: mattzmsft
ms.author: mazeller
ms.date: 05/21/2018
ms.topic: article
keywords: release notes, versione, windows 10, build, rs4, sistema operativo
ms.openlocfilehash: 1fc1b43b0581234e835379fd553b78121108086e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600903"
---
# <a name="release-notes---april-2018"></a>Note sulla versione - aprile 2018

Il **[Windows 10 April 2018 Update](https://blogs.windows.com/windowsexperience/2018/04/30/whats-new-in-the-windows-10-april-2018-update)** (noto anche come RS4) include nuove funzionalità per HoloLens e realtà mista di Windows auricolari immersive connesso al PC. 

Per aggiornare la versione più recente per uno dei due tipi di dispositivo, aprire il **le impostazioni** app e passare alla **aggiornamento e sicurezza**, quindi selezionare il **Controlla aggiornamenti** pulsante. In un PC Windows 10, è anche possibile installare manualmente Windows 10 April 2018 Update usando le [strumento di creazione dei supporti Windows](https://www.microsoft.com/software-download/windows10).

**Versione più recente per Desktop:** Windows 10 April 2018 Update (**10.0.17134.1**)<br>
**Versione più recente per HoloLens:** Windows 10 April 2018 Update (**10.0.17134.80**)<br>
<br>

>[!VIDEO https://www.youtube.com/embed/O-84oWjSbr0]

*Un messaggio da Alex Kipman e una panoramica delle nuove funzionalità di realtà mista di Windows 10 April 2018 Update*

## <a name="new-features-for-windows-mixed-reality-immersive-headsets"></a>Nuove funzionalità per le cuffie coinvolgenti di realtà mista di Windows

Windows 10 April 2018 Update include numerosi miglioramenti per l'uso auricolari (VR) coinvolgenti di realtà mista di Windows con il PC desktop, ad esempio: 

* **Nuovi ambienti per la realtà mista domestica** -è ora possibile scegliere tra il Cliff House e il nuovo ambiente Skyloft selezionando **posizioni** nel menu Start. Sono stati anche aggiunti [funzionalità sperimentale](add-custom-home-environments.md) che consentirà di usare gli ambienti personalizzati creati.
* **Accesso rapido all'acquisizione di realtà mista** -è ora possibile scattare foto realtà mista utilizzando un controller di movimento. Tenere premuto il pulsante Windows e quindi toccare il trigger. Ciò funziona negli ambienti e le app, ma non acquisiscono il contenuto protetto con DRM.
* **Nuove opzioni per l'avvio e il ridimensionamento contenuto** -App vengono ora inserite automaticamente fronte quando li si avvia dal menu Start. È possibile ridimensionare anche ora 2D App trascinando i bordi e angoli della finestra.
* **Consente di passare a contenuto con i comandi vocali "teleport"** -è ora possibile rapidamente teleport per stare contenuto nella realtà mista di Windows home gazing al contenuto e che indica che "teleport."
* **[Nelle schermate di avvio app 3D animate](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#animation-guidelines) e [decorativi oggetti 3D](enable-placement-of-3d-models-in-the-home.md) per la realtà mista home** -è ora possibile aggiungere un'animazione a utilità di avvio app 3D e consentire agli utenti di inserire decorativi modelli 3D da una pagina Web o 2D app nel Realtà mista di Windows home.
* **[Miglioramenti in Windows Mixed Reality per SteamVR](updating-your-steamvr-application-for-windows-mixed-reality.md)**  -realtà mista di Windows per SteamVR non rientra nel "accesso anticipato" con nuovi aggiornamenti, tra cui: quando si usano controller di movimento, migliorare le prestazioni e affidabilità, del feedback aptico e miglioramenti all'aspetto dei controller di movimento in SteamVR.
* **Altri miglioramenti** -impostazioni automatica delle prestazioni sono state aggiornate per offrire un'esperienza più ottimizzata (è possibile [eseguire l'override manuale](#visual-quality) questa impostazione). Il programma di installazione fornisce ora che informazioni più dettagliate su problemi comuni di compatibilità con USB 3.0 controller e schede grafiche.

## <a name="new-features-for-hololens"></a>Nuove funzionalità per HoloLens

Windows 10 April 2018 Update è ora disponibile per tutti i clienti di HoloLens. Questo aggiornamento include miglioramenti che sono state introdotte rispetto all'ultima versione principale del software HoloLens [agosto 2016](release-notes-august-2016.md).

### <a name="for-everyone"></a>Per tutti gli utenti

<table>
  <tr>
    <th>Funzionalità</th><th>Dettagli</th><th>Istruzioni</th>
  </tr>
  <tr>
    <td>Posizionamento automatico del contenuto 2D e 3D all'avvio</td><td>Un'app UWP app 2D 2D o utilità di avvio automatico-posizioni in tutto il mondo con dimensioni ottimali e distanza all'avvio anziché richiedere all'utente di inserirlo. Se un' <a href="app-views.md">app immersive</a> Usa un'utilità di avvio app 2D invece di un <a href="3d-app-launcher-design-guidance.md">utilità di avvio app 3D</a>, l'app immersive avvierà automaticamente dall'utilità di avvio di app 2D uguale come in RS1.<br><br>Un'utilità di avvio app 3D dal menu Start anche auto-luoghi nel mondo. Invece di avvio automatico dell'app, gli utenti possono fare clic su Utilità di avvio per avviare l'app immersiva. Contenuto 3D aperto dall'app ologrammi e dal bordo anche auto-luoghi nel mondo.</td><td>Quando si apre un'app dal menu Start, non verrà richiesto non è più per inserirlo nel mondo.<br><br>Se l'app 2D /<a href="3d-app-launcher-design-guidance.md">utilità di avvio app 3D</a> posizionamento non ottimale, è possibile spostarle facilmente con nuovo manipolazioni app fluida descritte di seguito. Inoltre è possibile posizionare nuovamente il contenuto di utilità di avvio/3D app 2D che informa che "Spostare questa" e utilizzando quindi sguardo per riposizionare il contenuto.</td>
  </tr>
  <tr>
    <td>Modifica app fluide</td><td>Spostare, ridimensionare e ruotare il contenuto 2D e 3D senza dover passare alla modalità "Regolare".</td><td>Per spostare un'app UWP 2D o un'utilità di avvio app 2D, fissare semplicemente la barra dell'app e quindi usare il modello tap + premuto e trascinare movimento. È possibile spostare il contenuto 3D gazing in qualsiasi punto nell'oggetto e quindi usando toccare e tenere premuto + trascinare.<br><br>Per ridimensionare il contenuto 2D, fissare relativo angolo. Il cursore sguardo si trasforma in un cursore di ridimensionamento e quindi è possibile toccare e tenere premuto + trascinare per ridimensionare. È anche possibile rendere 2D contenuto più alto o più ampio alla ricerca nei suoi bordi e trascinando.<br><br>Per ridimensionare il contenuto 3D, sollevare hanno entrambi le mani in frame di movimento, dita nella posizione pronta. Verrà visualizzato il cursore trasforma in uno stato con 2 poco pratico. Eseguire il modello tap e tenere premuto movimento con entrambe le mani. Spostare le mani più vicina o più lontani si modificherà la dimensione dell'oggetto. Spostare le mani avanti e indietro rispetto a altro verrà ruotare l'oggetto. È anche possibile ridimensionare o ruotare il contenuto 2D in questo modo.</td>
  </tr>
  <tr>
    <td>Ridimensionamento orizzontale di app 2D con adattamento dinamico</td><td>Creare un'app UWP 2D più ampia proporzioni per visualizzare altri contenuti su app. Ad esempio, rendere l'app di posta elettronica sufficientemente ampio per visualizzare il riquadro di anteprima.</td><td>Fissare semplicemente il bordo sinistro o destro dell'app UWP 2D per vedere il cursore di ridimensionamento, quindi usare il modello tap contenere + trascinare movimento da ridimensionare.</td>
  </tr>
  <tr>
    <td>Supporto dei comandi vocali espanso</td><td>È possibile eseguire più semplice utilizzando la voce dell'utente.</td><td>Provare a eseguire questi comandi vocali:<ul><li>"Andare a Start": consente di visualizzare il menu Start o esce da un' <a href="app-views.md">app immersive</a>.</li><li>"Spostare questa" - consente di spostare un oggetto.</li></ul></td>
  </tr>
  <tr>
    <td>App foto e Vntana aggiornamento</td><td>App Vntana aggiornata con nuovi vntana. App foto aggiornato.</td><td>Si noterà un aspetto rinnovato per le app ologrammi e foto. L'app Vntana include diverse nuove Vntana e un produttore di etichetta per la creazione semplificata di testo.</td>
  </tr>
  <tr>
    <td>Migliorata l'acquisizione di realtà mista</td><td>Inizio di scelta rapida di hardware e di fine MRC video.</td><td>Tenere premuto Volume + verso il basso per 3 secondi avviare la registrazione MRC video. Toccare di nuovo entrambi o usare il movimento bloom per terminare.</td>
  </tr>
  <tr>
    <td>Spazi consolidati</td><td>Semplificare la gestione dello spazio per vntana in uno spazio singolo.</td><td>HoloLens Trova automaticamente lo spazio e non richiede più è possibile gestire o selezionare gli spazi. Se hai problemi con vntana si, è possibile passare a <b>Impostazioni > sistema > Vntana > rimuovere nelle vicinanze vntana</b>. Se necessario, è anche possibile selezionare <b>rimuovere tutto vntana</b>.</td>
  </tr>
  <tr>
    <td>Full immersion audio migliorata</td><td>È possibile ascoltare HoloLens migliori in ambienti rumorosi e un'esperienza più realistica suono da applicazioni come il suono sarà nascosti da walls reale rilevato dal dispositivo.</td><td>Non devi eseguire alcuna operazione per sfruttare il suono spaziale migliorato.</td>
  </tr>
  <tr>
    <td>Esplora file</td><td>Spostare ed eliminare file dall'interno di HoloLens.</td><td>È possibile usare la <b>Esplora File</b> app spostare ed eliminare file dall'interno di HoloLens.<br><br><b>Suggerimento:</b> Se non viene visualizzato alcun file, il filtro "Recenti" può essere attivo (icona dell'orologio viene evidenziato nel riquadro a sinistra). Per risolvere il problema, selezionare la <b>questa periferica</b> icona nel riquadro a sinistra (sotto l'icona di orologio), di documento o aprire il menu e selezionare <b>This Device</b>.
</td>
  </tr>
  <tr>
    <td>Supporto MTP (Media Transfer Protocol)</td><td>Abilita il PC desktop per le librerie (foto, video, documenti) di accesso su HoloLens per trasferimento dati.</td><td>Analogamente ad altri dispositivi mobili, la connessione di HoloLens al computer per visualizzare <b>Esplora File</b> per accedere alle raccolte di HoloLens (foto, video, documenti) per trasferimento dati.<br><br><b>Suggerimenti:</b><ul><li>Se qualsiasi file non sono visibili, verificare che accedere a di HoloLens per abilitare l'accesso ai dati.</li><li>Dal <b>Esplora File</b> in un computer, è possibile selezionare <b>le proprietà del dispositivo</b> per visualizzare il numero di versione del sistema operativo Holographic a Windows (versione firmware) e numero di serie del dispositivo.</li></ul><b>Problema noto:</b> La ridenominazione tramite HoloLens <b>Esplora File</b> sul PC non è abilitato.</td>
  </tr>
  <tr>
    <td>Supporto di rete del portale captive durante l'installazione</td><td>È ora possibile impostare il HoloLens in una rete guest a hotel, conference Center, negozi al dettaglio o le aziende che usano captive portal.</td><td>Durante l'installazione, selezionare la rete, verificare di connettersi automaticamente se lo si desidera e immettere le informazioni di rete come richiesto.</td>
  </tr>
  <tr>
    <td>Sincronizzazione foto e video tramite l'app OneDrive</td><td>Le tue foto e video da HoloLens verranno ora sincronizzate tramite l'app OneDrive da di Microsoft Store anziché direttamente tramite l'app foto.</td><td>Per impostare questa funzionalità, scaricare e avviare l'app OneDrive dalla Store. Alla prima esecuzione verrà richiesto per caricare automaticamente le foto in OneDrive o è possibile trovare l'opzione nelle impostazioni dell'app.</td>
  </tr>
</table>

### <a name="for-developers"></a>Per sviluppatori

<table>
  <tr>
    <th>Funzionalità</th><th>Dettagli</th><th>Istruzioni</th>
  </tr>
  <tr>
    <td>Miglioramenti di mapping spaziale</td><td>Miglioramenti di qualità, la semplificazione e prestazioni.</td><td>Mesh mapping spaziale apparirà più chiaro: triangoli meno necessari per rappresentare lo stesso livello di dettaglio. È possibile notare le modifiche di densità considerevole triangolo nella scena.</td>
  </tr>
  <tr>
    <td>Selezione automatica del punto di attivazione basata sul buffer di profondità</td><td>Invio di un buffer di profondità per Windows consente a HoloLens selezionare un punto di stato attivo automaticamente per ottimizzare la stabilità di ologramma.</td><td>In Unity, passare a <b>Modifica > Impostazioni progetto > Player > scheda Universal Windows Platform > Impostazioni XR</b>, espandere il <b>SDK realtà mista di Windows</b> di elemento e assicurarsi che <b>abilitare Buffer profondità Condivisione</b> sia selezionata. Ciò verrà automaticamente verificato per i nuovi progetti.<br><br>Per le app DirectX, verificare che si chiama il <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer">CommitDirect3D11DepthBuffer </a> metodo sul <b>HolographicRenderingParameters</b> ogni fotogramma per fornire il buffer di profondità per Windows.
</td>
  </tr>
  <tr>
    <td>Modalità reprojection holographic</td><td>È ora possibile disabilitare reprojection posizionali in HoloLens per migliorare la stabilità di ologramma del contenuto rigidamente bloccato corpo, ad esempio video a 360 gradi.</td><td>In Unity, impostare <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html">HolographicSettings.ReprojectionMode</a> al <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html">HolographicReprojectionMode.OrientationOnly</a> quando tutto il contenuto nella visualizzazione è rigidamente bloccato corpo.<br><br>Per le app DirectX, impostare <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.reprojectionmode"> HolographicCameraRenderingParameters.ReprojectionMode</a> al <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicreprojectionmode">HolographicReprojectionMode.OrientationOnly</a> quando tutto il contenuto nella visualizzazione è rigidamente bloccato corpo.</td>
  </tr>
  <tr>
    <td>API di personalizzazione di App</td><td>Le API Windows saperne di più su dove l'esecuzione dell'app, ad esempio se display del dispositivo è (visore VR immersivi) opaco o trasparente (HoloLens) e l'eventuale visualizzazione 2D dell'app UWP verrà visualizzati nella shell holographic.</td><td>Unity ha in precedenza manualmente esposti <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html">HolographicSettings.IsDisplayOpaque</a> in modo che ha lavorato anche prima di questa compilazione.<br><br>Per le app DirectX, è ora possibile accedere alle API esistenti, ad esempio <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.isopaque">HolographicDisplay.GetDefault(). IsOpaque</a> e <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview.iscurrentviewpresentedonholographicdisplay">HolographicApplicationPreview.IsCurrentViewPresentedOnHolographicDisplay</a> su HoloLens anche.
</td>
  </tr>
  <tr>
      <td>Modalità di ricerca</td><td>Consente agli sviluppatori di accedere ai sensori HoloLens chiave quando si compilano applicazioni accademiche e industriali per testare nuove idee nei campi di visione artificiale e robotica, tra cui:<ul><li>I quattro ambiente videocamere di rilevamento</li><li>Due versioni dei dati depth mappatura della fotocamera</li><li>Due versioni di un flusso di runtime di integrazione-riflettività</li></ul></td><td><a href="research-mode.md">Documentazione di modalità di ricerca</a><br><a href="https://github.com/Microsoft/HoloLensForCV">App di esempio in modalità di ricerca</a></td>
  </tr>
</table>

### <a name="for-commercial-customers"></a>Per i clienti commerciali

<table>
  <tr>
    <th>Funzionalità</th><th>Dettagli</th><th>Istruzioni</th>
  </tr>
  <tr>
    <td>Usare più account utente di Azure Active Directory in un singolo dispositivo</td><td>Condividere un HoloLens con più utenti di Azure AD, ognuno con le proprie impostazioni utente e dati utente nel dispositivo.</td><td><a href="https://docs.microsoft.com/hololens/hololens-multiple-users">IT Pro Center: HoloLens condivisione con più persone</a></td>
  </tr>
  <tr>
    <td>Modificare la rete Wi-Fi in fase di accesso</td><td>Modificare la rete Wi-Fi prima dell'accesso per attivare un altro utente di accedere con il proprio account utente di Azure AD per la prima volta, consentendo agli utenti di condividere i dispositivi in diverse posizioni e i siti dei processi.</td><td>Nella schermata di accesso, è possibile usare l'icona di rete sotto il campo della password per connettersi a una rete. Ciò risulta utile quando si tratta la prima volta che accede a un dispositivo.</td>
  </tr>
  <tr>
    <td>Registrazione unificata</td><td>Ora è facile per un utente di HoloLens che ha configurato il dispositivo con un account Microsoft personale per aggiungere un account aziendale (Azure AD) e aggiungere il dispositivo al server MDM.</td><td>È sufficiente accedere con un account Azure AD e la registrazione viene eseguita automaticamente.</td>
  </tr>
  <tr>
    <td>Sincronizzazione di posta elettronica senza la registrazione MDM</td><td>Supporto per la sincronizzazione di posta elettronica di Exchange Active Sync (EAS) senza richiedere la registrazione MDM.</td><td>È ora possibile sincronizzare posta elettronica senza la registrazione in MDM. È possibile configurare il dispositivo con un Account Microsoft, scaricare e installare l'app di posta elettronica e aggiungere un account di posta elettronica aziendale direttamente.</td>
  </tr>
</table>

### <a name="for-it-pros"></a>Per i professionisti IT

<table>
  <tr>
    <th>Funzionalità</th><th>Dettagli</th><th>Istruzioni</th>
  </tr>
  <tr>
    <td>Nuovo nome di "Windows Holographic for Business" del sistema operativo</td><td>Cancellare l'edizione di denominazione per ridurre la confusione nell'applicazione di licenza di aggiornamento edizione quando vengono abilitate funzionalità Commercial Suite su HoloLens.</td><td>È possibile visualizzare quale edizione di Windows Holographic è nel dispositivo in <b>Impostazioni > sistema > su</b>. "Windows Holographic for Business" verrà visualizzato se è stato applicato un aggiornamento di edizione per abilitare le funzionalità Commercial Suite. Informazioni su come <a href="https://docs.microsoft.com/hololens/hololens-upgrade-enterprise">sbloccare Windows Holographic for Business funzionalità</a>.</td>
  </tr>
  <tr>
  <td>Windows Configuration Designer (WCD)</td><td>Creare e modificare i pacchetti di provisioning per la configurazione con l'app aggiornata WCD HoloLens. Creazione guidata HoloLens semplice per aggiornamento edizione OOBE configurabile, area/fuso orario, il token di Azure AD in blocco, rete e per gli sviluppatori CSP. Editor avanzato filtrati in base a HoloLens supportato opzioni, tra cui accesso assegnato e Account Management CSP.</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">IT Pro Center: Configurare HoloLens usando un pacchetto di provisioning</a></td>
  </tr>
  <tr>
    <td>Programma di installazione configurabile (OOBE)</td><td>Nascondi calibrazione movimento/sguardo set di training e le schermate di configurazione Wi-Fi durante l'installazione.</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning#create-a-provisioning-package-for-hololens-using-the-hololens-wizard">IT Pro Center: Configurare HoloLens usando un pacchetto di provisioning</a></td>
  </tr>
  <tr>
    <td>Supporto del token Azure AD in blocco</td><td>Pre-registrare il dispositivo al tenant di directory di Azure AD per il flusso di programma di installazione utente più veloce.</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">IT Pro Center: Configurare HoloLens usando un pacchetto di provisioning</a></td>
  </tr>
  <tr>
  <td>CSP DeveloperSetup</td><td>Distribuisci profilo per configurare HoloLens in modalità sviluppatore. È utile per lo sviluppo e demo di dispositivi.</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">IT Pro Center: Configurare HoloLens usando un pacchetto di provisioning</a></td>
  </tr>
  <tr>
  <td>CSP AccountManagement</td><td>Condividere un dispositivo HoloLens e rimuovere i dati utente dopo la disconnessione o soglie di inattività/spazio di archiviazione per l'utilizzo temporaneo. Supporta gli account Azure AD.</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">IT Pro Center: Configurare HoloLens usando un pacchetto di provisioning</a></td>
  </tr>
  <tr>
  <td>Accesso assegnato</td><td>Windows assegnato l'accesso per i ruoli di lavoro della prima riga o le demo. Blocco di uno o più app. Non è necessario per gli sviluppatori lo sblocco.</td><td><a href="https://docs.microsoft.com/hololens/hololens-kiosk">IT Pro Center: Configurare HoloLens in modalità tutto schermo</a></td>
  </tr>
  <tr>
  <td>Accesso guest per i dispositivi chiosco multimediale</td><td>Windows assegnato l'accesso con account guest senza password per le demo. Blocco di uno o più app. Non è necessario per gli sviluppatori lo sblocco.</td><td><a href="https://docs.microsoft.com/hololens/hololens-kiosk#guest">IT Pro Center: Configurare HoloLens in modalità tutto schermo</a></td>
  </tr>
  <tr>
    <td>Configurare la diagnostica (OOBE)</td><td>Ottenere i log di diagnostica da HoloLens in modo che è possibile risolvere gli errori di accesso Azure AD (prima di Hub di commenti e suggerimenti è disponibile all'utente il cui accesso non riuscito).</td><td>Quando il programma di installazione o l'accesso non riesce, scegliere il nuovo <b>raccogliere informazioni</b> opzione per ottenere i log di diagnostica per la risoluzione dei problemi.</td>
  </tr>
  <tr>
    <td>Scadenza password indefinito account locale</td><td>Rimuovere un'interruzione del dispositivo reimpostata alla scadenza della password di account locale.</td><td>Durante il provisioning di un account locale, è non è più necessario modificare la password ogni 42 giorni nella <b>impostazioni</b>, come la password dell'account non scada più.</td>
  </tr>
  <tr>
    <td>I dettagli e lo stato di sincronizzazione MDM</td><td>Funzionalità di Windows standard per comprendere i dettagli all'interno di HoloLens e lo stato di sincronizzazione MDM.</td><td>È possibile controllare lo stato di sincronizzazione MDM di un dispositivo nel <b>Impostazioni > account > accesso azienda o dell'istituto di istruzione > Info</b>. Nel <b>lo stato di sincronizzazione dispositivi<b> sezione, è possibile avviare una sincronizzazione, vedere aree gestite da MDM e creare ed esportare un report di diagnostica avanzata.</td>
  </tr>
</table>

## <a name="known-issues"></a>Problemi noti

Abbiamo lavorato sodo per offrire un'eccezionale esperienza di realtà mista di Windows, ma ancora Microsoft eseguita verificando alcuni problemi noti. Se si trova ad altri utenti, please [commenti e suggerimenti](give-us-feedback.md).

### <a name="hololens"></a>HoloLens

#### <a name="after-update"></a>Dopo l'aggiornamento

Dopo l'aggiornamento da RS1 a RS4 di HoloLens è possibile notare quanto segue:
* **Reimposta PIN** -3x3 App aggiunto al menu Start verranno ripristinate le impostazioni predefinite dopo l'aggiornamento. 
* **Le App e reimpostare vntana posizionato** -App inserite nel tuo mondo verrà rimosso dopo l'aggiornamento e dovranno essere nuovamente inseriti in tutto lo spazio. 
* **Hub di feedback non viene avviata immediatamente** -immediatamente dopo l'aggiornamento, saranno necessari alcuni minuti prima di poter avviare alcune app di posta in arrivo, ad esempio Hub di commenti e suggerimenti, anche se si aggiornano automaticamente. 
* **I certificati Wi-Fi aziendali devono essere sincronizzate nuovamente** -stiamo analizzando un problema che richiede di HoloLens essere connessi a una rete diversa in ordine per i certificati aziendali essere nuovamente sincronizzati nel dispositivo prima che sia in grado di riconnettersi a reti aziendali usando i certificati. 
* **La riproduzione di Video HEVC H.265 non funziona** -applicazioni che tentano di riprodurre video H.265 riceveranno un messaggio di errore. La soluzione alternativa consiste nel [accesso di Windows Device Portal](using-the-windows-device-portal.md), selezionare **Apps** sulla barra di spostamento a sinistra, e **rimuovere** l'applicazione di HEVC. Quindi, installare la versione più recente [estensione Video HEVC](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7) da di Microsoft Store. Stiamo analizzando il problema. 

#### <a name="for-developers-updating-hololens-apps-for-devices-running-windows-10-april-2018-update"></a>Per gli sviluppatori: l'aggiornamento di HoloLens App per dispositivi che eseguono Windows 10 April 2018 Update

Insieme a un elenco di eccezionali [nuove funzionalità](#new-features-for-hololens), Windows 10 aprile 2018 Update (RS4) per HoloLens impone alcuni comportamenti di codice che le versioni precedenti non è state eseguite:
* **Richieste di autorizzazione da usare risorse riservate (fotocamera, microfono e così via)**  -RS4 su HoloLens applicherà le richieste di autorizzazione per le app che si intende accedere alle risorse sensibili, ad esempio la fotocamera o microfono. RS1 su HoloLens non forza queste richieste, pertanto, se l'app presuppone che l'accesso immediato a queste risorse, potrebbe bloccarsi in RS4 (anche se l'utente concede l'autorizzazione per la risorsa richiesta). Leggere il relativo [articolo di dichiarazioni funzionalità app UWP](https://docs.microsoft.com/windows/uwp/packaging/app-capability-declarations) per altre informazioni.
* **Le chiamate alle App esterno il proprio** -RS4 su HoloLens impone l'utilizzo corretto della [ *Windows.System.Launcher* classe](https://docs.microsoft.com/uwp/api/Windows.System.Launcher) per avviare un'altra app dal proprio. Ad esempio, abbiamo visto i problemi con le app di chiamare *Windows.System.Launcher.LaunchUriForResultsAsync* da un thread non UI ASTA. Questo avverrebbe senza problemi in RS1 su HoloLens, ma RS4 richiede la chiamata a essere eseguita sul thread dell'interfaccia utente.

### <a name="windows-mixed-reality-on-desktop"></a>Realtà mista di Windows sul Desktop

#### <a name="visual-quality"></a>Qualità visiva

* Se si nota dopo Windows 10 April 2018 Update che grafica è più sfocata rispetto a prima oppure che il campo di visualizzazione ricerca inferiore sulle cuffie, l'impostazione automatica delle prestazioni potrebbe essere stato modificato per mantenere una frequenza dei fotogrammi sufficiente su una meno potenti scheda grafica (ad esempio Nvidia 1050). È possibile eseguire manualmente l'override questo (se si sceglie), passare a **Impostazioni > realtà mista > visualizzato visore VR > Opzioni di esperienze > Modifica** e modificare "Automatico" su "90 Hz." È anche possibile provare a modificare **qualità visiva** (nella stessa pagina Impostazioni) su "Alta".

#### <a name="windows-mixed-reality-setup"></a>Programma di installazione di realtà mista di Windows

* Quando si configura Windows con le cuffie connessa, il monitor del PC diventi vuoto. Disconnettere le cuffie per abilitare l'output per il monitor del PC per completare l'installazione di Windows.
* Se non hai le cuffie connessi, si potrebbero perdere suggerimenti aggiuntivi quando si visita prima la realtà mista di Windows home.
* Altri dispositivi Bluetooth possono causare l'interferenza con i controller di movimento. Se i controller di movimento sono presenti problemi di connessione/associazione/rilevamento, assicurarsi che l'opzione Bluetooth (se un adattatore esterno) viene collegati a un percorso senza ostacoli e non immediatamente accanto a un altro adattatore Bluetooth. Provare anche a disconnettendo altre periferiche Bluetooth durante le sessioni di realtà mista di Windows per verificare se è utile.

#### <a name="games-and-apps-from-the-microsoft-store"></a>Giochi e App di Microsoft Store

* Alcuni giochi a grafica intensiva, ad esempio 7 Motorsport Forza, potrebbero causare problemi di prestazioni nei PC in grado di supportare meno durante la riproduzione in realtà mista di Windows.

#### <a name="audio"></a>Audio

* Se si dispone di Cortana abilitata nell'host di PC prima di utilizzare il visore VR realtà mista di Windows, si potrebbe perdere spaziali audio simulazione applicati alle App che utilizzare per racchiudere la realtà mista di Windows home. 
   * La soluzione alternativa consiste nell'abilitare "Windows Sonic per le cuffie" in tutti i dispositivi audio associati al computer, anche le cuffie audio dispositivo connesso:
      1. Fare clic sull'icona dell'altoparlante della barra delle applicazioni desktop e selezionare dall'elenco dei dispositivi audio.
      2. Fare doppio clic sull'icona dell'altoparlante della barra delle applicazioni desktop e selezionare "Windows Sonic per le cuffie" nel menu "L'installazione dell'altoparlante".
      3. Ripetere questi passaggi per tutti i dispositivi audio (endpoint).
   * Un'altra opzione è disattivare "Cortana ti permettono di rispondere a Ehi Cortana" **le impostazioni** > **Cortana** sul desktop prima dell'avvio di realtà mista di Windows.
* Quando un altro dispositivo USB multimediale (ad esempio una webcam) condivide lo stesso hub USB (esterno o all'interno del PC) con il visore VR realtà mista di Windows, in casi rari audio jack/cuffie della cuffia potrebbe disporre di un suono apparizione oppure nessun audio affatto. È possibile risolvere il problema per le cuffie in una porta USB che non condividono lo stesso hub come l'altro dispositivo o disconnettere o disabilitare l'altro dispositivo USB multimediale.
* In rari casi, è possibile notare un picco di rumore dalle cuffie connessa per le cuffie hub USB del computer host non può fornire potenza sufficiente per il visore VR realtà mista di Windows.

#### <a name="holograms"></a>Ologrammi

* Se è stato immesso un numero elevato di vntana nella home di realtà mista di Windows, alcuni possono scomparsa e come Guardatevi intorno. Per evitare questo problema, rimuovere alcuni del vntana in tale area della realtà mista di Windows home.

#### <a name="motion-controllers"></a>Controller di movimento

* Se l'input non viene instradato alle cuffie, il controller di movimento brevemente scompare quando viene posizionato accanto il limite di spazio. Premere Windows + Y per assicurarsi che ci sia un banner blu sul monitor Desktop verrà risolvere questo problema. 
* In alcuni casi, quando fa clic su una pagina web in Microsoft Edge, il contenuto verrà ingrandire anziché fare clic su.

#### <a name="desktop-app-in-the-windows-mixed-reality-home"></a>App desktop in casa la realtà mista di Windows

* Strumento di cattura non funziona nelle app Desktop.
* App desktop non viene mantenuta l'impostazione al riavvio.
* Se si Usa anteprima del portale di realtà mista sul desktop, quando si apre l'app Desktop in casa la realtà mista di Windows, è possibile notare l'effetto di mirror infinito. 
* L'esecuzione dell'app Desktop può causare problemi di prestazioni sul non - extra misto realtà i PC Windows; non è consigliabile.  
* App desktop può avviare automaticamente perché una finestra invisibile nel Desktop ha lo stato attivo. 
* Controllo dell'Account utente desktop prompt renderà le cuffie, possono visualizzare nero fino a quando non viene completato il prompt dei comandi.

#### <a name="windows-mixed-reality-for-steamvr"></a>Realtà mista di Windows per SteamVR

* Potrebbe essere necessario avviare il portale di realtà mista dopo l'aggiornamento per assicurarsi che gli aggiornamenti software necessari per Windows 10 April 2018 Update completati prima di avviare SteamVR. 
* È necessario essere in una versione recente di realtà mista di Windows per SteamVR continuare a essere compatibile con Windows 10 April 2018 Update. Assicurarsi che gli aggiornamenti automatici sono attivati per realtà mista di Windows per SteamVR, che si trova nella sezione "Software" della libreria nel flusso.  

#### <a name="other-issues"></a>Altri problemi

>[!IMPORTANT]
>Una versione precedente di Windows 10 April 2018 Update per Insider (versione 17134.5) inseriti manca un componente software necessario per l'esecuzione di realtà mista di Windows. È consigliabile evitare questa versione, se si usa la realtà mista di Windows. 

Abbiamo stabilito una regressione delle prestazioni quando si usa Surface Book 2 nella versione iniziale di questo aggiornamento (10.0.17134.1) che Microsoft sta lavorando per risolvere una patch di aggiornamento futuro. Si consiglia di attendere che tale problema è stato risolto prima di aggiornare manualmente o in attesa per l'aggiornamento a lanciare normalmente.

## <a name="provide-feedback-and-report-issues"></a>Fornire commenti e suggerimenti e segnalare problemi

Usare la [app di Hub di commenti e suggerimenti sul PC Windows 10 o HoloLens](give-us-feedback.md) per fornire commenti e suggerimenti e segnalare problemi. Con Hub di Feedback garantisce che tutte le informazioni di diagnostica necessarie sono incluse per consentire ai nostri tecnici rapidamente il debug e risolvere il problema.

>[!NOTE]
>Assicurarsi di accettare il prompt che chiede se si vuole che Hub di commenti e suggerimenti per accedere alla cartella documenti (selezionare **Sì** quando richiesto).

## <a name="prior-release-notes"></a>Note sulla versione precedente

* [Note sulla versione - ottobre 2017](release-notes-october-2017.md)
* [Note sulla versione - agosto 2016](release-notes-august-2016.md)
* [Note sulla versione - maggio 2016](release-notes-may-2016.md)
* [Note sulla versione - marzo 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Vedere anche
* [Supporto visore VR immersivi (collegamento esterno)](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)
* [Supporto di HoloLens (collegamento esterno)](https://support.microsoft.com/products/hololens)
* [Installare gli strumenti](install-the-tools.md)
* [Invia commenti e suggerimenti](give-us-feedback.md)


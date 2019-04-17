---
title: Modello di App
description: Realtà mista di Windows Usa il modello di app fornito per la piattaforma Windows universale, un modello e l'ambiente per le app di Windows moderne.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Piattaforma UWP, modello di app, ciclo di vita, sospendere, riprendere, riquadro, viste e i contratti
ms.openlocfilehash: 5dc84122e591e7d91657b6f8eadf6eb947f2d706
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602996"
---
# <a name="app-model"></a>Modello di App

Realtà mista di Windows utilizza il modello di app fornito dal [Universal Windows Platform](https://docs.microsoft.com/windows/uwp/get-started/) (UWP), un ambiente per le app di Windows moderne e modello. Il modello di app UWP definisce come le applicazioni sono installate, aggiornate, con controllo delle versioni e rimosso completamente e in modo sicuro. Gestisce il ciclo di vita dell'applicazione come App execute, sospensione e terminano - e del modo in cui è possibile mantenere lo stato. Illustra anche l'integrazione e l'interazione con il sistema operativo, i file e altre app.

![App 2D disposte nella realtà mista di Windows home in un'area colazione](images/20160112-055908-hololens-500px.jpg)<br>
*App con una visualizzazione 2D disposte in casa la realtà mista di Windows*

## <a name="app-lifecycle"></a>Ciclo di vita dell'app

Il ciclo di vita di un'app per realtà mista comporta i concetti di app standard, ad esempio il posizionamento, avvio, chiusura e la rimozione.

### <a name="placement-is-launch"></a>Il posizionamento è avvio

Ogni app viene avviata in realtà mista, inserendo un riquadro dell'app (solo una [riquadro secondario di Windows](https://docs.microsoft.com/uwp/api/Windows.UI.StartScreen.SecondaryTile)) nella [realtà mista di Windows home](navigating-the-windows-mixed-reality-home.md). Questi riquadri di app, sul posizionamento, verranno avviata l'esecuzione dell'app. Questi riquadri app salvare in modo permanente e restare in corrispondenza della posizione in cui vengono inseriti, che agisce come utilità di avvio per in qualsiasi momento si desidera tornare all'app.

![Posizionamento inserisce un riquadro secondario nel mondo](images/slide1-600px.png)<br>
*Posizionamento inserisce un riquadro secondario nel mondo*

Non appena viene completato di selezione host (a meno che la selezione host è stata avviata da un [un'app al](app-model.md#protocols) avviare), l'app viene avviata l'avvio. Realtà mista di Windows è possibile eseguire un numero limitato di App in una sola volta. Appena inserite e avviare un'app, può sospendere le altre App attiva, lasciando una schermata dell'ultimo stato dell'app nel relativo riquadro app ogni volta che è stato inserito. Visualizzare [ciclo di vita app UWP di Windows 10](https://docs.microsoft.com/windows/uwp/launch-resume/app-lifecycle) per altre informazioni sulla gestione di ripristino e altri eventi del ciclo di vita app.

![Dopo aver inserito un riquadro, l'avvio dell'app in esecuzione](images/slide2-500px.png) ![diagramma di stato per l'app in esecuzione, sospese o non è in esecuzione](images/ic576232-500px.png)<br>
*Left: dopo aver inserito un riquadro, l'avvio dell'app in esecuzione. A destra: diagramma di stato per l'app in esecuzione, sospese o non è in esecuzione.*

### <a name="remove-is-closeterminate-process"></a>Rimuovi sono close/Termina processo

Quando si rimuove un riquadro posizionato app da tutto il mondo, consente di chiudere i processi sottostanti. Ciò può essere utile per garantire che l'app viene terminata o il riavvio di un'app problematica.

### <a name="app-suspensiontermination"></a>Sospensione di App/terminazione

Nel [realtà mista di Windows home](navigating-the-windows-mixed-reality-home.md), l'utente è in grado di creare più punti di ingresso per un'app. Tale scopo, avviando l'app dal menu Start e l'inserimento di riquadro dell'app nel mondo. Ogni riquadro dell'app si comporta come un punto di ingresso diverso e dispone di un'istanza di un riquadro separato nel sistema. Una query per [SecondaryTile.FindAllAsync](https://docs.microsoft.com/uwp/api/Windows.UI.StartScreen.SecondaryTile#Windows_UI_StartScreen_SecondaryTile_FindAllAsync) comporterà un **SecondaryTile** per ogni istanza dell'app.

Quando si sospende un'app UWP, viene eseguito uno screenshot dello stato corrente.

![Per le app sospese sono riportati screenshot](images/slide9-800px.png)<br>
*Per le app sospese sono riportati screenshot*

Una differenza essenziale da altre shell di Windows 10 è come l'app è stato informato di un'attivazione di istanze di app tramite il [CoreApplication.Resuming](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_Resuming) e [CoreWindow.Activated](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Activated) gli eventi.

|  Scenario |  Ripresa  |  Attivato | 
|----------|----------|----------|
|  Avviare la nuova istanza dell'app dal menu Start  |   |  **Attivato** con un nuovo [TileId](https://docs.microsoft.com/uwp/api/windows.ui.startscreen.secondarytile#Windows_UI_StartScreen_SecondaryTile_TileId) | 
|  Avviare una seconda istanza dell'app dal menu Start  |   |  **Attivato** con un nuovo **TileId** | 
|  Selezionare l'istanza dell'app che non è attualmente attivo  |   |  **Attivato** con il **TileId** associato all'istanza | 
|  Selezionare un'altra app, quindi selezionare l'istanza attiva in precedenza  |  **Ripresa** generato  |  | 
|  Selezionare un'altra app, quindi selezionare l'istanza che era precedentemente inattivo  |  **Ripresa** generato  |  Quindi **Activated** con il **TileId** associato all'istanza | 

### <a name="extended-execution"></a>Esecuzione estesa

In alcuni casi l'app deve continuare a lavorare in background o la riproduzione di audio. [Le attività in background](https://docs.microsoft.com/windows/uwp/launch-resume/declare-background-tasks-in-the-application-manifest) sono disponibili su HoloLens.

![App possono essere eseguite in background](images/slide10-800px.png)<br>
*App possono essere eseguite in background*

## <a name="app-views"></a>Visualizzazioni delle app

Quando si attiva l'app, è possibile scegliere il tipo di visualizzazione si desidera visualizzare. Per un'app **CoreApplication**, è sempre presente una replica primaria [visualizzazione app](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationView) e un numero qualsiasi di altre visualizzazioni app si vuole creare. Sul desktop, è possibile pensare una visualizzazione dell'app come una finestra. I modelli di app di realtà mista creano un progetto Unity in cui è visualizzazione dell'app principale [coinvolgenti](app-views.md). 

L'app è possibile creare una visualizzazione app 2D aggiuntive tramite la tecnologia, ad esempio XAML, per usare le funzionalità di Windows 10, ad esempio l'acquisto in-app. Se l'app è stata avviata come un'app UWP per altri dispositivi Windows 10, la visualizzazione primaria è 2D, ma è possibile "illuminarsi" nella realtà mista tramite l'aggiunta di una visualizzazione di altre app che è coinvolgente per mostrare un'esperienza volumetrically. Si immagini di creare un'app Visualizzatore foto in XAML in cui il pulsante di presentazione passa a una vista di app immersive che raggiunto foto dall'app nel mondo e superfici.

![L'app in esecuzione può avere una visualizzazione 2D o una vista coinvolgente](images/slide3-800px.png)<br>
*L'app in esecuzione può avere una visualizzazione 2D o una vista coinvolgente*

### <a name="creating-an-immersive-view"></a>Creazione di una visualizzazione coinvolgente

Le app di realtà mista sono quelle che creano una vista coinvolgente, che si può fare con il [HolographicSpace](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace) tipo.

Un'app che è puramente coinvolgente sempre necessario creare una vista immersiva all'avvio, anche se avviata dal desktop. Visualizzazioni coinvolgenti visualizzati sempre nella cuffie, indipendentemente dal fatto dove sono stati creati da. Attivazione di una vista immersiva verrà visualizzare il portale di realtà mista e guidano l'utente da inserire nella loro auricolare.

Un'app che inizia con una visualizzazione 2D sul monitor desktop può creare una visualizzazione secondaria coinvolgente per visualizzare il contenuto nelle cuffie. Un esempio di questo oggetto è una finestra Edge 2D sul monitor di visualizzazione di un video a 360 gradi nelle cuffie.

![Le App in esecuzione nella visualizzazione coinvolgenti sono l'unico visibile](images/slide4-800px.png)<br>
*Un'app in esecuzione in una vista coinvolgente e concreto è l'unico visibile*

### <a name="2d-view-in-the-windows-mixed-reality-home"></a>Visualizzazione 2D in casa la realtà mista di Windows

Qualsiasi elemento diverso da una vista immersiva viene visualizzato come una visualizzazione 2D in tutto il mondo.

Un'app potrebbe avere visualizzazioni 2D in entrambi i monitor da tavolo e nelle cuffie. Si noti che una nuova visualizzazione 2D devono essere posizionata nella stessa shell della visualizzazione cui è stato creato, il monitoraggio o nelle cuffie. Non è attualmente possibile per un'app o un utente di spostare una visualizzazione 2D tra la home page di realtà mista e il monitoraggio.

![Le App in esecuzione nella visualizzazione 2D condividono lo spazio nel mondo misto con altre App](images/slide5-800px.png)<br>
*Le App in esecuzione in una visualizzazione 2D condividono lo spazio con altre App*

### <a name="placement-of-additional-app-tiles"></a>Posizione dei riquadri di app aggiuntive

È possibile inserire molte applicazioni con un 2D consente di visualizzare il mondo, considerando però le [API riquadro secondario](https://docs.microsoft.com/windows/uwp/design/shell/tiles-and-notifications/secondary-tiles). Questi riquadri "bloccati" verranno visualizzato come schermate iniziali che gli utenti devono inserire e quindi possano utilizzare successivamente per avviare l'app. Realtà mista di Windows attualmente non supporta il rendering di uno qualsiasi del contenuto del riquadro 2D come riquadri animati.

![Le app possono avere più selezioni host con riquadri secondari](images/slide6-800px.png)<br>
*Le app possono avere più selezioni host con riquadri secondari*

### <a name="switching-views"></a>Passare da una visualizzazione

#### <a name="switching-from-the-2d-xaml-view-to-the-immersive-view"></a>Passando dalla visualizzazione XAML 2D alla visualizzazione coinvolgente

Se l'app Usa XAML, quindi il XAML [IFrameworkViewSource](https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkviewsource) controllerà la prima visualizzazione dell'app. L'app dovrà passare alla visualizzazione immersiva prima di attivare i **CoreWindow**per assicurarsi che l'app viene avviata direttamente nell'esperienza coinvolgente e concreto.

Uso [CoreApplication.CreateNewView](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_CreateNewView_Windows_ApplicationModel_Core_IFrameworkViewSource_) e [ApplicationViewSwitcher.SwitchAsync](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationViewSwitcher#Windows_UI_ViewManagement_ApplicationViewSwitcher_SwitchAsync_System_Int32_) per renderla attiva la visualizzazione.

> [!NOTE]
>* Non si specifica la [ApplicationViewSwitchingOptions.ConsolidateViews](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationviewswitchingoptions) flag **SwitchAsync** quando verrà rimosso il passaggio dalla visualizzazione di XAML per la visualizzazione immersiva o lo slate che ha avviato l'app dal mondo.
>* **SwitchAsync** deve essere chiamato usando la [Dispatcher](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Dispatcher) associato alla visualizzazione in cui si desidera disattivare.
>* Dovrai **SwitchAsync** tornare alla visualizzazione di XAML, se è necessario avviare una tastiera virtuale o attivare un'altra app.

![Le app possono passare tra le visualizzazioni 2D e visualizzazioni coinvolgenti](images/slide7-600px.png) ![scompaiono quando un'app entra in una vista coinvolgente, tutto il mondo misto e altre App](images/slide8-600px.png)<br>
*Sinistra: le app è possono passare dalla visualizzazione 2D e coinvolgenti. A destra: quando un'app entra in una vista coinvolgente, le app di realtà mista di Windows home e altri scompariranno.*

#### <a name="switching-from-the-immersive-view-back-to-a-keyboard-xaml-view"></a>Passare dalla visualizzazione immersiva tornare a una tastiera visualizzazione XAML

Uno dei motivi comune per il cambio avanti e indietro tra le visualizzazioni è visualizzare una tastiera in un'app di realtà mista. La shell solo è in grado di visualizzare i tasti di sistema se l'app Mostra una visualizzazione 2D. Se l'app deve ottenere l'input di testo, potrebbe forniscono una visualizzazione XAML personalizzata con un campo di input di testo, passare a esso e quindi passare nuovamente al termine dell'input.

Ad esempio nella sezione precedente, è possibile usare **ApplicationViewSwitcher.SwitchAsync** transizione torna a una visualizzazione XAML dalla visualizzazione coinvolgente e concreto.

## <a name="app-size"></a>Dimensioni dell'App

Le visualizzazioni 2D app vengono sempre visualizzati in uno slate virtuale fisso. In questo modo tutte le visualizzazioni 2D Mostra la stessa quantità esatta di contenuto. Ecco alcuni altri dettagli sulle dimensioni della visualizzazione 2D dell'app:
* Le proporzioni dell'app viene mantenuta in caso di ridimensionamento.
* App [fattore di scala e la risoluzione](building-2d-apps.md#2d-app-view-resolution-and-scale-factor) non vengono modificati mediante il ridimensionamento.
* Le app non sono in grado di eseguire una query le dimensioni effettive del mondo.

![Le app 2D vengono visualizzate con dimensioni di finestra predefinito](images/12493521-10104043956964683-6118765685995662420-o-500px.jpg)<br>
*Le app con una visualizzazione 2D vengono visualizzate con dimensioni di finestra predefinito*

## <a name="app-tiles"></a>Riquadri delle App

Nel menu Start utilizza il riquadro piccolo standard e riquadro medio per i pin e la **tutte le app** elenco nella realtà mista. 

![Menu Start per realtà mista di Windows](images/start-500px.png)<br>
*Menu Start per realtà mista di Windows*

## <a name="app-to-app-interactions"></a>App per le interazioni di app

Durante la compilazione delle App, è possibile utilizzare i meccanismi di comunicazione da app per app avanzate disponibili in Windows 10. Molte delle nuove API di protocollo e le registrazioni dei file funziona perfettamente in HoloLens per abilitare l'avvio dell'app e la comunicazione. 

Si noti che per le cuffie desktop, l'app associata a un'estensione di file specificato o protocollo potrebbe essere un'app Win32 che può apparire solo sul monitor desktop o nel desktop slate.

### <a name="protocols"></a>Protocolli

HoloLens supporta l'avvio dell'app per app tramite il [Windows.System.Launcher APIs](https://docs.microsoft.com/uwp/api/Windows.System.Launcher).

Esistono alcuni aspetti da considerare quando si avvia un'altra applicazione:

* Quando si esegue un avvio non modale, ad esempio [LaunchUriAsync](https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriAsync_Windows_Foundation_Uri_), l'utente deve inserire l'app prima di poter interagire con esso.

* Quando si esegue un avvio modale, ad esempio tramite [LaunchUriForResultsAsync](https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriForResultsAsync_Windows_Foundation_Uri_Windows_System_LauncherOptions_Windows_Foundation_Collections_ValueSet_), l'app modale viene posizionato sopra la finestra.

* Realtà mista di Windows non è possibile sovrapporre applicazioni basate su viste esclusive. Per visualizzare l'app avviata, Windows richiede l'utente torna al mondo per visualizzare l'applicazione.

### <a name="file-pickers"></a>I controlli di selezione file

HoloLens supporta sia [FileOpenPicker](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileOpenPicker) e [FileSavePicker](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker) contratti. Tuttavia, non è un'app viene pre-installata che soddisfa i contratti selettore file. Queste App, ad esempio OneDrive - possono essere installate da di Microsoft Store.

Se si dispone di più di un file selezione app installata, non verrà visualizzato qualsiasi interfaccia utente di disambiguazione per la scelta di quali app devono essere avviati; al contrario, verrà scelta la prima selezione file installata. Quando si salva un file, viene generato il nome del file che include il timestamp. Non può essere modificato dall'utente.

Per impostazione predefinita, le estensioni seguenti sono supportate in locale:

|  App  |  Extensions | 
|----------|----------|
|  Foto  |  BMP, gif, jpg, png, avi, mov, mp4, wmv | 
|  Microsoft Edge  |  htm, html, pdf, svg, xml | 

### <a name="app-contracts-and-windows-mixed-reality-extensions"></a>App contratti ed estensioni di realtà mista di Windows

I contratti delle App e i punti di estensione consentono di registrare l'app per sfruttare i vantaggi di funzionalità del sistema operativo più approfondita, ad esempio la gestione di un'estensione di file o utilizzando le attività in background. Questo è un elenco dei punti di estensione su HoloLens e contratti supportati e non supportati.

|  Contratto o un'estensione  |  È supportata? | 
|----------|----------|
| [Provider dell'immagine dell'account (estensione)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#account_picture_provider) | File modifiche disco non supportato | 
| [allarme](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#alarm) | File modifiche disco non supportato | 
| [Servizio App](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#app_service) | Supportato ma non completamente funzionale | 
| [Provider appuntamenti](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#appointmnets_provider) | File modifiche disco non supportato | 
| [Riproduzione automatica (estensione)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#autoplay) | File modifiche disco non supportato | 
| [Attività in background (estensione)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#background_tasts) | Parzialmente supportate (non tutte le operazioni di trigger) | 
| [Attività di aggiornamento (estensione)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#update_task) | Supportato | 
| [Contratto per l'aggiornamento di file memorizzati nella cache](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#cached_file_updater) | Supportato | 
| [Impostazioni videocamera (estensione)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#camera_settings) | File modifiche disco non supportato | 
| [Protocollo di connessione remota](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#dial_protocol) | File modifiche disco non supportato | 
| [Attivazione di file (estensione)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_activation) | Supportato | 
| [Contratto selezione apertura file](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_open_picker_contract) | Supportato | 
| [Contratto selezione salvataggio file](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_save_picker_contract) | Supportato | 
| [Chiamata di blocco dello schermo](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#lock_screen_call) | File modifiche disco non supportato | 
| [Riproduzione multimediale](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#media_playback) | File modifiche disco non supportato | 
| [Contratto Riproduci in](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#playto_contract) | File modifiche disco non supportato | 
| [Attività di configurazione preinstallata](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#preinstalled_config_task) | File modifiche disco non supportato | 
| [Flusso di lavoro stampa 3D](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#print_3d_workflow) | Supportato | 
| [Impostazioni attività Stampa (estensione)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#print_task_settings) | File modifiche disco non supportato | 
| [Attivazione di URI (estensione)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#protocol_activation) | Supportato | 
| [Avvio con restrizioni](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#restricted_launch) | File modifiche disco non supportato | 
| [Contratto Search](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#search_contract) | File modifiche disco non supportato | 
| [Contratto impostazioni](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#settings_contract) | File modifiche disco non supportato | 
| [Contratto condivisione](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#share_contract) | File modifiche disco non supportato | 
| [Certificati SSL / (estensione)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#ssl_certificates) | Supportato | 
| [Provider account Web](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#web_account_provider) | Supportato | 

## <a name="app-file-storage"></a>Archiviazione file di App

Tutta la memoria è tramite il [dello spazio dei nomi Windows. Storage](https://docs.microsoft.com/uwp/api/Windows.Storage). Vedere la documentazione seguente per altri dettagli. HoloLens non supporta archiviazione sincronizzazione/roaming dell'app.

* [File, cartelle e raccolte](https://docs.microsoft.com/windows/uwp/files/index)
* [Store e recuperare le impostazioni e altri dati dell'app](https://docs.microsoft.com/windows/uwp/design/app-settings/store-and-retrieve-app-data)

### <a name="known-folders"></a>Cartelle note

Visualizzare [KnownFolders](https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders) per i dettagli completi per le app UWP.

<table>
<tr>
<th> Proprietà</th><th> Supportato in HoloLens</th><th> Supportato in auricolari coinvolgenti</th><th> Descrizione</th>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_AppCaptures">AppCaptures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ottiene la cartella App acquisisce.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_CameraRoll">CameraRoll</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ottiene la cartella rullino.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_DocumentsLibrary">DocumentsLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ottiene la raccolta documenti. La libreria di documenti non è per uso generale.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MusicLibrary">MusicLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ottiene la raccolta musica.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Objects3D">Objects3D</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ottiene la cartella di oggetti 3D.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_PicturesLibrary">PicturesLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ottiene la raccolta immagini.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Playlists">Elenchi di riproduzione</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ottiene la cartella di elenchi di riproduzione.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_SavedPictures">SavedPictures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ottiene la cartella immagini salvato.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_VideosLibrary">VideosLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ottiene la raccolta di video.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_HomeGroup">HomeGroup</a></td><td></td><td style="text-align: center;">✔️</td><td>Ottiene la cartella gruppo home.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MediaServerDevices">MediaServerDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>Ottiene la cartella del supporto di dispositivi server (Digital Living Network Alliance (DLNA)).</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RecordedCalls">RecordedCalls</a></td><td></td><td style="text-align: center;">✔️</td><td>Ottiene la cartella chiamate registrate.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RemovableDevices">RemovableDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>Ottiene la cartella di dispositivi rimovibili.</td>
</tr>
</table>

## <a name="app-package"></a>Pacchetto dell'app

Con Windows 10 non destinazione non è più un sistema operativo, bensì [come destinazione dell'app a uno o più famiglie di dispositivi](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide#device-families). Una famiglia di dispositivi identifica le API, le caratteristiche del sistema e i comportamenti che ti aspetti dai dispositivi che appartengono a quella famiglia di dispositivi. Determina inoltre il set di dispositivi in cui è possibile installare l'app dal [Microsoft Store](submitting-an-app-to-the-microsoft-store.md#specifying-target-device-families).

* Per impostare come destinazione di desktop auricolari e HoloLens, come destinazione dell'app per la **Universal** famiglia di dispositivi.
* Per impostare come destinazione solo desktop auricolari, come destinazione dell'app per la **Windows.Desktop** famiglia di dispositivi.
* Per impostare come destinazione solo HoloLens, come destinazione dell'app per la **Windows.Holographic** famiglia di dispositivi.

## <a name="see-also"></a>Vedere anche

* [Viste di App](app-views.md)
* [L'aggiornamento di App UWP 2D per realtà mista](building-2d-apps.md)
* [Linee guida di progettazione di app 3D dell'utilità di avvio](3d-app-launcher-design-guidance.md)
* [Implementazione di utilità di avvio app 3D](implementing-3d-app-launchers.md)

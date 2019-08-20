---
title: Modello app
description: La realtà mista di Windows usa il modello di app fornito dal piattaforma UWP (Universal Windows Platform), un modello e un ambiente per le app di Windows moderne.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: UWP, modello app, ciclo di vita, Sospendi, Riprendi, riquadri, viste, contratti
ms.openlocfilehash: 5dc84122e591e7d91657b6f8eadf6eb947f2d706
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63517262"
---
# <a name="app-model"></a>Modello app

La realtà mista di Windows usa il modello di app fornito dal [piattaforma UWP (Universal Windows Platform)](https://docs.microsoft.com/windows/uwp/get-started/) (UWP), un modello e un ambiente per le moderne app di Windows. Il modello di app UWP definisce la modalità di installazione, aggiornamento, controllo delle versioni e rimozione delle app in modo sicuro e completo. Governa il ciclo di vita dell'applicazione, ovvero il modo in cui le app vengono eseguite, sospese e terminate e come possono mantenere lo stato. Viene inoltre illustrata l'integrazione e l'interazione con il sistema operativo, i file e altre app.

![app 2D disposte nella Home realtà mista di Windows in un'area di colazione](images/20160112-055908-hololens-500px.jpg)<br>
*App con una visualizzazione 2D disposta nella Home realtà mista di Windows*

## <a name="app-lifecycle"></a>Ciclo di vita dell'app

Il ciclo di vita di un'app per realtà mista prevede concetti di app standard, ad esempio posizionamento, avvio, terminazione e rimozione.

### <a name="placement-is-launch"></a>Selezione host avviata

Ogni app viene avviata in realtà mista posizionando un riquadro dell'app (solo un [riquadro secondario di Windows](https://docs.microsoft.com/uwp/api/Windows.UI.StartScreen.SecondaryTile)) nella [Home realtà mista di Windows](navigating-the-windows-mixed-reality-home.md). Questi riquadri dell'app, al posizionamento, inizieranno a eseguire l'app. Questi riquadri dell'app vengono mantenuti e rimangono nella posizione in cui si trovano, agendo come avvii per ogni volta che si vuole tornare all'app.

![La selezione host inserisce un riquadro secondario nel mondo](images/slide1-600px.png)<br>
*La selezione host inserisce un riquadro secondario nel mondo*

Non appena il posizionamento viene completato (a meno che la selezione host non sia stata avviata da un' [app all'](app-model.md#protocols) avvio dell'app), viene avviata l'avvio dell'app. La realtà mista di Windows può eseguire un numero limitato di app contemporaneamente. Non appena si posiziona e si avvia un'app, altre app attive potrebbero sospendere, lasciando uno screenshot dell'ultimo stato dell'app nel riquadro dell'app ovunque sia stato inserito. Vedere ciclo di vita dell' [app UWP per Windows 10](https://docs.microsoft.com/windows/uwp/launch-resume/app-lifecycle) per altre informazioni sulla gestione di Riprendi e altri eventi del ciclo di vita dell'app.

![Dopo l'inserimento di un riquadro, l'app](images/slide2-500px.png) avvia ![il diagramma di stato per l'app in esecuzione, sospesa o non in esecuzione](images/ic576232-500px.png)<br>
*Left: dopo aver posizionato un riquadro, viene avviata l'esecuzione dell'app. Right: diagramma di stato per l'app in esecuzione, sospesa o non in esecuzione.*

### <a name="remove-is-closeterminate-process"></a>Rimuovi è il processo di chiusura/terminazione

Quando si rimuove un riquadro dell'app posizionata dal mondo, questo chiude i processi sottostanti. Questo può essere utile per garantire che l'app venga terminata o riavvii un'app problematica.

### <a name="app-suspensiontermination"></a>Sospensione/chiusura dell'app

Nella [Home realtà mista di Windows](navigating-the-windows-mixed-reality-home.md), l'utente è in grado di creare più punti di ingresso per un'app. A tale scopo, avviare l'app dal menu Start e posizionare il riquadro dell'app nel mondo. Ogni riquadro dell'app si comporta come un punto di ingresso diverso e ha un'istanza del riquadro separata nel sistema. Una query per [SecondaryTile. findAllAsync](https://docs.microsoft.com/uwp/api/Windows.UI.StartScreen.SecondaryTile#Windows_UI_StartScreen_SecondaryTile_FindAllAsync) comporterà un **SecondaryTile** per ogni istanza dell'app.

Quando un'app UWP viene sospesa, viene acquisita una schermata dello stato corrente.

![Schermate visualizzate per le app sospese](images/slide9-800px.png)<br>
*Schermate visualizzate per le app sospese*

Una differenza fondamentale rispetto ad altre shell di Windows 10 è il modo in cui l'app viene informata dell'attivazione di un'istanza dell'app tramite gli eventi [CoreApplication. ripresa](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_Resuming) e [CoreWindow. Activated](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Activated) .

|  Scenario |  Resuming  |  Attivato | 
|----------|----------|----------|
|  Avviare una nuova istanza dell'app dal menu Start  |   |  **Attivata** con una nuova [tileId](https://docs.microsoft.com/uwp/api/windows.ui.startscreen.secondarytile#Windows_UI_StartScreen_SecondaryTile_TileId) | 
|  Avvia la seconda istanza dell'app dal menu Start  |   |  **Attivata** con una nuova **tileId** | 
|  Consente di selezionare l'istanza dell'app che non è attualmente attiva  |   |  **Attivata** con **tileId** associato all'istanza | 
|  Selezionare un'app diversa, quindi selezionare l'istanza precedentemente attiva  |  **Ripresa** generata  |  | 
|  Selezionare un'app diversa, quindi selezionare l'istanza che in precedenza era inattiva  |  **Ripresa** generata  |  Viene quindi **attivato** con **tileId** associato all'istanza | 

### <a name="extended-execution"></a>Esecuzione estesa

A volte l'app deve continuare a lavorare in background o riprodurre l'audio. Le [attività in background](https://docs.microsoft.com/windows/uwp/launch-resume/declare-background-tasks-in-the-application-manifest) sono disponibili in HoloLens.

![Le app possono essere eseguite in background](images/slide10-800px.png)<br>
*Le app possono essere eseguite in background*

## <a name="app-views"></a>Visualizzazioni delle app

Quando l'app viene attivata, è possibile scegliere il tipo di visualizzazione che si vuole visualizzare. Per **CoreApplication**di un'app, è sempre disponibile una [visualizzazione](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationView) dell'app primaria e un numero qualsiasi di altre visualizzazioni di app che si desidera creare. Sul desktop è possibile considerare una visualizzazione app come una finestra. I modelli di app per realtà mista creano un progetto Unity in cui la visualizzazione dell'app primaria è [immersiva](app-views.md). 

L'app può creare una visualizzazione app 2D aggiuntiva usando una tecnologia come XAML per usare le funzionalità di Windows 10, ad esempio l'acquisto in-app. Se l'app è stata avviata come app UWP per altri dispositivi Windows 10, la visualizzazione principale è 2D, ma è possibile "illuminare" in realtà mista aggiungendo una visualizzazione app aggiuntiva che è immersiva per mostrare un'esperienza volumetrica. Si supponga di creare un'app visualizzatore foto in XAML, in cui il pulsante Slideshow passa a una visualizzazione App immersiva che ha sorvolato le foto dall'app in tutto il mondo e le aree.

![L'app in esecuzione può avere una visualizzazione 2D o una visualizzazione immersiva](images/slide3-800px.png)<br>
*L'app in esecuzione può avere una visualizzazione 2D o una visualizzazione immersiva*

### <a name="creating-an-immersive-view"></a>Creazione di una visualizzazione immersiva

Le app per realtà miste sono quelle che creano una visualizzazione immersiva, che viene realizzata con il tipo [HolographicSpace](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace) .

Un'app che è esclusivamente immersiva dovrebbe creare sempre una visualizzazione immersiva all'avvio, anche se avviata dal desktop. Le visualizzazioni immersive vengono sempre visualizzate nell'auricolare, indipendentemente dalla posizione in cui sono state create. L'attivazione di una visualizzazione immersiva visualizzerà il portale di realtà misto e guiderà l'utente a inserire l'auricolare.

Un'app che inizia con una visualizzazione 2D su desktop monitor può creare una visualizzazione immersiva secondaria per visualizzare il contenuto dell'auricolare. Un esempio è una finestra perimetrale 2D sul monitor che visualizza un video di 360 gradi nell'auricolare.

![Le app in esecuzione in visualizzazione immersiva sono l'unico visibile](images/slide4-800px.png)<br>
*Un'app in esecuzione in una visualizzazione immersiva è l'unica visibile*

### <a name="2d-view-in-the-windows-mixed-reality-home"></a>visualizzazione 2D nella Home realtà mista di Windows

Qualsiasi elemento diverso da una visualizzazione immersiva viene visualizzato come una visualizzazione 2D nel mondo.

Un'app può avere visualizzazioni 2D sia nel monitor desktop che nell'auricolare. Si noti che una nuova visualizzazione 2D verrà inserita nella stessa shell della visualizzazione che lo ha creato, sia sul monitor che sulla cuffia. Non è attualmente possibile che un'app o un utente sposti una visualizzazione 2D tra la Home realtà mista e il monitoraggio.

![Le app in esecuzione in visualizzazione 2D condividono lo spazio nel mondo misto con altre app](images/slide5-800px.png)<br>
*Le app in esecuzione in una visualizzazione 2D condividono lo spazio con altre app*

### <a name="placement-of-additional-app-tiles"></a>Posizionamento dei riquadri app aggiuntivi

È possibile inserire il numero di app con una visualizzazione 2D nel mondo desiderato con le API del [riquadro secondario](https://docs.microsoft.com/windows/uwp/design/shell/tiles-and-notifications/secondary-tiles). Questi riquadri "aggiunti" verranno visualizzati come schermate iniziali che gli utenti devono inserire e successivamente potranno usare per avviare l'app. La realtà mista di Windows non supporta attualmente il rendering di un contenuto del riquadro 2D come riquadri animati.

![Le app possono avere più posizionamenti usando riquadri secondari](images/slide6-800px.png)<br>
*Le app possono avere più posizionamenti usando riquadri secondari*

### <a name="switching-views"></a>Cambio di visualizzazione

#### <a name="switching-from-the-2d-xaml-view-to-the-immersive-view"></a>Passare dalla visualizzazione XAML 2D alla visualizzazione immersiva

Se l'app usa XAML, il [IFRAMEWORKVIEWSOURCE](https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkviewsource) XAML controllerà la prima visualizzazione dell'app. L'app deve passare alla visualizzazione immersiva prima di attivare il **CoreWindow**, per assicurarsi che l'app venga avviata direttamente nell'esperienza immersiva.

Usare [CoreApplication. CreateNewView](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_CreateNewView_Windows_ApplicationModel_Core_IFrameworkViewSource_) e [ApplicationViewSwitcher. SwitchAsync](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationViewSwitcher#Windows_UI_ViewManagement_ApplicationViewSwitcher_SwitchAsync_System_Int32_) per impostarlo come visualizzazione attiva.

> [!NOTE]
>* Non specificare il flag [ApplicationViewSwitchingOptions. ConsolidateViews](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationviewswitchingoptions) su **SwitchAsync** quando si passa dalla visualizzazione XAML alla visualizzazione immersiva oppure lo Slate che ha avviato l'app verrà rimosso dal mondo.
>* **SwitchAsync** deve essere chiamato utilizzando il [Dispatcher](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Dispatcher) associato alla visualizzazione a cui si sta passando.
>* Se è necessario avviare una tastiera virtuale o si vuole attivare un'altra app, è necessario **SwitchAsync** di nuovo la visualizzazione XAML.

![Le app possono passare tra visualizzazioni 2D e visualizzazioni](images/slide7-600px.png) ![immersive quando un'app entra in una visualizzazione immersiva, il mondo misto e altre app scompaiono](images/slide8-600px.png)<br>
*Left: le app possono passare dalla visualizzazione 2D alla visualizzazione immersiva. Right: quando un'app entra in una vista immersiva, la realtà mista Windows Home e altre app scompaiono.*

#### <a name="switching-from-the-immersive-view-back-to-a-keyboard-xaml-view"></a>Passare dalla visualizzazione immersiva a una visualizzazione XAML della tastiera

Un motivo comune per passare da una visualizzazione all'altra consiste nel visualizzare una tastiera in un'app per realtà mista. La shell è in grado di visualizzare solo la tastiera di sistema se l'app mostra una visualizzazione 2D. Se l'app deve ottenere l'input di testo, può fornire una visualizzazione XAML personalizzata con un campo di input di testo, passare a essa e tornare indietro al termine dell'input.

Come nella sezione precedente, è possibile usare **ApplicationViewSwitcher. SwitchAsync** per eseguire la transizione a una visualizzazione XAML dalla visualizzazione immersiva.

## <a name="app-size"></a>Dimensioni app

le visualizzazioni delle app 2D vengono sempre visualizzate in uno Slate virtuale fisso. In questo modo, tutte le visualizzazioni 2D mostrano esattamente la stessa quantità di contenuto. Di seguito sono riportate altre informazioni sulle dimensioni della visualizzazione 2D dell'app:
* Le proporzioni dell'app vengono mantenute durante il ridimensionamento.
* La [risoluzione](building-2d-apps.md#2d-app-view-resolution-and-scale-factor) delle app e il fattore di scala non vengono modificati tramite il ridimensionamento.
* Le app non sono in grado di eseguire query sulle dimensioni effettive nel mondo.

![le app 2D vengono visualizzate con le dimensioni fisse della finestra](images/12493521-10104043956964683-6118765685995662420-o-500px.jpg)<br>
*Le app con una visualizzazione 2D vengono visualizzate con le dimensioni fisse della finestra*

## <a name="app-tiles"></a>Riquadri dell'app

Il menu Start usa il riquadro standard Small e il riquadro medio per i pin e l'elenco **tutte le app** in realtà mista. 

![Menu Start per la realtà mista di Windows](images/start-500px.png)<br>
*Menu Start per la realtà mista di Windows*

## <a name="app-to-app-interactions"></a>Interazioni tra app e app

Quando si compilano app, è possibile accedere all'app avanzata ai meccanismi di comunicazione delle app disponibili in Windows 10. Molte delle nuove API del protocollo e registrazioni dei file funzionano perfettamente in HoloLens per consentire l'avvio e la comunicazione delle app. 

Si noti che per gli auricolari desktop, l'app associata a una determinata estensione di file o protocollo può essere un'app Win32 che può essere visualizzata solo in monitor desktop o nello Slate desktop.

### <a name="protocols"></a>Protocolli

HoloLens supporta l'avvio di app tramite le [API Windows. System. Launcher](https://docs.microsoft.com/uwp/api/Windows.System.Launcher).

Quando si avvia un'altra applicazione, è necessario considerare alcuni aspetti:

* Quando si esegue un avvio non modale, ad esempio [LaunchUriAsync](https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriAsync_Windows_Foundation_Uri_), l'utente deve inserire l'app prima di interagire con essa.

* Quando si esegue un avvio modale, ad esempio tramite [LaunchUriForResultsAsync](https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriForResultsAsync_Windows_Foundation_Uri_Windows_System_LauncherOptions_Windows_Foundation_Collections_ValueSet_), l'app modale viene posizionata nella parte superiore della finestra.

* La realtà mista di Windows non è in grado di sovrapporre applicazioni su viste esclusive. Per visualizzare l'app avviata, Windows riporta l'utente al mondo per visualizzare l'applicazione.

### <a name="file-pickers"></a>Selezione file

HoloLens supporta entrambi i contratti [FileOpenPicker](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileOpenPicker) e [FileSavePicker](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker) . Tuttavia, nessuna app è preinstallata che soddisfi i contratti di selezione file. Queste app-OneDrive, ad esempio, possono essere installate dal Microsoft Store.

Se sono installate più app di selezione file, non viene visualizzata alcuna interfaccia utente per la risoluzione dell'ambiguità per scegliere l'app da avviare. viene invece scelta la prima selezione file installata. Quando si salva un file, viene generato il nome file che include il timestamp. Questa operazione non può essere modificata dall'utente.

Per impostazione predefinita, le estensioni seguenti sono supportate localmente:

|  App  |  Estensioni | 
|----------|----------|
|  Foto  |  BMP, gif, jpg, PNG, AVI, MOV, MP4, WMV | 
|  Microsoft Edge  |  htm, HTML, PDF, SVG, XML | 

### <a name="app-contracts-and-windows-mixed-reality-extensions"></a>Contratti di app e estensioni di realtà mista di Windows

I contratti e i punti di estensione dell'app consentono di registrare l'app per sfruttare le funzionalità più approfondite del sistema operativo, ad esempio la gestione di un'estensione di file o l'uso di attività in background. Si tratta di un elenco dei contratti supportati e non supportati e dei punti di estensione in HoloLens.

|  Contratto o estensione  |  Supportato? | 
|----------|----------|
| [Provider immagine account (estensione)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#account_picture_provider) | File modifiche disco non supportato | 
| [Allarme](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#alarm) | File modifiche disco non supportato | 
| [Servizio app](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#app_service) | Supportato ma non completamente funzionante | 
| [Provider appuntamenti](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#appointmnets_provider) | File modifiche disco non supportato | 
| [AutoPlay (estensione)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#autoplay) | File modifiche disco non supportato | 
| [Attività in background (estensione)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#background_tasts) | Supportato parzialmente (non tutti i trigger funzionano) | 
| [Attività Update (estensione)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#update_task) | Supportato | 
| [Contratto di aggiornamento file memorizzato nella cache](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#cached_file_updater) | Supportato | 
| [Impostazioni della fotocamera (estensione)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#camera_settings) | File modifiche disco non supportato | 
| [Protocollo di connessione](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#dial_protocol) | File modifiche disco non supportato | 
| [Attivazione file (estensione)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_activation) | Supportato | 
| [Contratto Selezione apertura file](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_open_picker_contract) | Supportato | 
| [Contratto Selezione salvataggio file](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_save_picker_contract) | Supportato | 
| [Chiamata schermata di blocco](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#lock_screen_call) | File modifiche disco non supportato | 
| [Riproduzione multimediale](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#media_playback) | File modifiche disco non supportato | 
| [Riproduci per contratto](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#playto_contract) | File modifiche disco non supportato | 
| [Attività di configurazione preinstallata](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#preinstalled_config_task) | File modifiche disco non supportato | 
| [Flusso di lavoro 3D di stampa](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#print_3d_workflow) | Supportato | 
| [Impostazioni delle attività di stampa (estensione)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#print_task_settings) | File modifiche disco non supportato | 
| [Attivazione URI (estensione)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#protocol_activation) | Supportato | 
| [Avvio con restrizioni](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#restricted_launch) | File modifiche disco non supportato | 
| [Cerca contratto](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#search_contract) | File modifiche disco non supportato | 
| [Contratto di impostazioni](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#settings_contract) | File modifiche disco non supportato | 
| [Condividi contratto](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#share_contract) | File modifiche disco non supportato | 
| [SSL/certificati (estensione)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#ssl_certificates) | Supportato | 
| [Provider account Web](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#web_account_provider) | Supportato | 

## <a name="app-file-storage"></a>Archiviazione file app

Tutto lo spazio di archiviazione viene tramite lo [spazio dei nomi Windows. storage](https://docs.microsoft.com/uwp/api/Windows.Storage). Per ulteriori informazioni, vedere la documentazione seguente. HoloLens non supporta la sincronizzazione/roaming dell'archiviazione delle app.

* [File, cartelle e raccolte](https://docs.microsoft.com/windows/uwp/files/index)
* [Archiviazione e recupero di impostazioni e altri dati dell'app](https://docs.microsoft.com/windows/uwp/design/app-settings/store-and-retrieve-app-data)

### <a name="known-folders"></a>Cartelle note

Vedere [KnownFolders](https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders) per i dettagli completi per le app UWP.

<table>
<tr>
<th> Proprietà</th><th> Supportato in HoloLens</th><th> Supportato su auricolari immersivi</th><th> Descrizione</th>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_AppCaptures">AppCaptures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ottiene la cartella di acquisizione dell'app.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_CameraRoll">CameraRoll</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ottiene la cartella del rullo della fotocamera.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_DocumentsLibrary">DocumentsLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ottiene la raccolta documenti. La raccolta documenti non è destinata all'utilizzo generale.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MusicLibrary">MusicLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ottiene la raccolta musicale.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Objects3D">Objects3D</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ottiene la cartella degli oggetti 3D.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_PicturesLibrary">PicturesLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ottiene la libreria di immagini.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Playlists">Playlist</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ottiene la cartella degli elenchi di riproduzione.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_SavedPictures">SavedPictures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ottiene la cartella immagini salvate.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_VideosLibrary">VideosLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ottiene la raccolta video.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_HomeGroup">Gruppo Home</a></td><td></td><td style="text-align: center;">✔️</td><td>Ottiene la cartella del gruppo Home.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MediaServerDevices">MediaServerDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>Ottiene la cartella dei dispositivi (Digital Living Network Alliance) del server multimediale.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RecordedCalls">RecordedCalls</a></td><td></td><td style="text-align: center;">✔️</td><td>Ottiene la cartella delle chiamate registrate.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RemovableDevices">RemovableDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>Ottiene la cartella dei dispositivi rimovibili.</td>
</tr>
</table>

## <a name="app-package"></a>Pacchetto dell'app

Con Windows 10 non è più destinato a un sistema operativo, ma [l'app è destinata a una o più famiglie di dispositivi](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide#device-families). Una famiglia di dispositivi identifica le API, le caratteristiche del sistema e i comportamenti che ti aspetti dai dispositivi che appartengono a quella famiglia di dispositivi. Determina anche il set di dispositivi in cui l'app può essere installata dal [Microsoft Store](submitting-an-app-to-the-microsoft-store.md#specifying-target-device-families).

* Per avere come destinazione sia gli auricolari desktop che HoloLens, indirizzare l'app alla famiglia di dispositivi **Windows. universali** .
* Per indirizzare solo le cuffie Desktop, indirizzare l'app alla famiglia di dispositivi **Windows. desktop** .
* Per indirizzare solo HoloLens, indirizzare l'app alla famiglia di dispositivi **Windows. olografici** .

## <a name="see-also"></a>Vedere anche

* [Visualizzazioni delle app](app-views.md)
* [Aggiornamento di app UWP 2D per la realtà mista](building-2d-apps.md)
* [Linee guida per la progettazione di utilità di avvio di app 3D](3d-app-launcher-design-guidance.md)
* [Implementazione di lanci di app 3D](implementing-3d-app-launchers.md)

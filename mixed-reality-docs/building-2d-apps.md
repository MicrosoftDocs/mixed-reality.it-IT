---
title: L'aggiornamento di App UWP 2D per realtà mista
description: Questo articolo illustra l'aggiornamento esistente 2D (Universal Windows Platform) eseguire l'app in HoloLens e realtà mista di Windows auricolari coinvolgente e concreto.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: App 2D, UWP, app flat, HoloLens, coinvolgenti le cuffie, possono, modello di app, eseguire il pulsante, barra dell'app, dpi, risoluzione, scalabilità
ms.openlocfilehash: 35a2e7774a79e35893821467f7e9ef8c004efa20
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602183"
---
# <a name="updating-2d-uwp-apps-for-mixed-reality"></a>L'aggiornamento di App UWP 2D per realtà mista

Realtà mista di Windows consente all'utente di vedere vntana come se fossero a destra intorno, nel tuo mondo fisico o digitale. In sostanza, HoloLens sia i PC Desktop si collega agli accessori visore VR immersivi sono dispositivi Windows 10. Ciò significa che si è in grado di eseguire quasi tutte le app Universal Windows Platform (UWP) nella finestra di Store delle App 2D.

## <a name="creating-a-2d-uwp-app-for-mixed-reality"></a>Creazione di un'app UWP 2D per realtà mista

Il primo passaggio per rendere un'app 2D per realtà mista auricolari consiste nell'eseguire l'app in esecuzione come app 2D standard sullo schermo del desktop.

### <a name="building-a-new-2d-uwp-app"></a>Creazione di una nuova app UWP 2D

Per creare una nuova app 2D per realtà mista, è sufficiente creare un 2D standard app Universal Windows Platform (UWP). Nessun altre modifiche all'applicazione sono necessari per l'app eseguire quindi come uno slate in realtà mista.

Per iniziare a creare un'app UWP 2D, consultare il [creare la prima app](https://docs.microsoft.com/windows/uwp/get-started/your-first-app) articolo.

### <a name="bringing-an-existing-2d-store-app-to-uwp"></a>Importare un'app di Store 2D esistente alla piattaforma UWP

Se si dispone già di un'app di Windows 2D nel Store, è necessario assicurarsi innanzitutto è destinato a Windows 10 Universal Windows Platform (UWP). Di seguito sono tutti i potenziali punti di partenza che utente potrebbe avere oggi stesso con l'app Store:
<br>

|  Punto di partenza  |  Manifesto AppX piattaforma di destinazione  |  Come effettuare questa Universal? | 
|----------|----------|----------|
|  Windows Phone (Silverlight)  |  Manifesto dell'applicazione Silverlight |  [Eseguire la migrazione a WinRT](https://msdn.microsoft.com/library/windows/apps/dn642486(v=vs.105).aspx) | 
|  Windows Phone 8.1 universale  |  8.1 manifesto di AppX che non includa una piattaforma di destinazione  |  [Eseguire la migrazione di app per la piattaforma Windows universale](https://msdn.microsoft.com/library/mt148501.aspx) | 
|  Windows Store 8  |  Manifesto di AppX 8 che non includa una piattaforma di destinazione  |  [Eseguire la migrazione di app per la piattaforma Windows universale](https://msdn.microsoft.com/library/mt148501.aspx) | 
|  Universale di Windows Store 8.1  |  8.1 manifesto di AppX che non includa una piattaforma di destinazione  |  [Eseguire la migrazione di app per la piattaforma Windows universale](https://msdn.microsoft.com/library/mt148501.aspx) | 

Se si dispone di un'app Unity 2D oggi compilata come un'app Win32 ("PC, Mac e Linux Standalone" destinazione di compilazione), è possibile assegnare realtà mista passando invece Unity per la destinazione della compilazione "Universal Windows Platform".

Parleremo modi che è possibile limitare l'app in modo specifico per HoloLens utilizzando la famiglia di dispositivi Windows.Holographic [seguito](#publish-and-maintain-your-universal-app).

### <a name="run-your-2d-app-in-a-windows-mixed-reality-immersive-headset"></a>Eseguire l'app 2D in un visore VR immersivi di realtà mista di Windows

Se è stato distribuito l'app 2D per il computer desktop in cui si sta sviluppando e provato sullo schermo, già tutto pronto per provare questa soluzione in un auricolare desktop coinvolgente e concreto.

È sufficiente passare al menu di avvio all'interno di visore VR realtà mista e avviare l'app da tale posizione. La shell desktop e la shell holographic condividono lo stesso set di App UWP e quindi l'app deve essere già presente dopo aver distribuito da Visual Studio.

## <a name="targeting-both-immersive-headsets-and-hololens"></a>Destinazione sia auricolari coinvolgenti e HoloLens

La procedura è stata completata. L'app Usa Windows 10 Universal Windows Platform (UWP).

L'app ora è in grado di eseguire nei dispositivi Windows di oggi, ad esempio Desktop, mobili, auricolari coinvolgenti di realtà mista di Windows, Xbox e HoloLens, futuri anche come dispositivi di Windows. Tuttavia, per impostare come destinazione effettivamente tutti i dispositivi, è necessario assicurarsi che il gruppo di dispositivi Universal è destinata l'app.

### <a name="change-your-device-family-to-windowsuniversal"></a>Modificare la famiglia di dispositivi in Universal

A questo punto è possibile passare al manifesto di AppX per assicurarsi che l'app UWP di Windows 10 può essere eseguita su HoloLens:
* Aprire il file di soluzione dell'app con **Visual Studio** e passare al manifesto di pacchetto dell'app
* Fare clic il **package. appxmanifest** nella soluzione e passare a **Visualizza codice**<br>
  ![package. appxmanifest in Esplora soluzioni](images/openappxmanifest-500px.png)<br>
* Verificare che la piattaforma di destinazione sia Universal nella sezione delle dipendenze
  ```
  <Dependencies>
    <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
  </Dependencies>
  ```
* Risparmia!

Se non si utilizza Visual Studio per l'ambiente di sviluppo, è possibile aprire **appxmanifest. XML** nell'editor di testo di propria scelta per assicurarsi che la destinazione scelta è la **Universal**  *TargetDeviceFamily*.

### <a name="run-in-the-hololens-emulator"></a>Esegui nell'emulatore di HoloLens

Ora che l'app UWP è destinata a "Universal", è possibile compilare l'app ed eseguirla nel [HoloLens emulatore](using-the-hololens-emulator.md).
* Assicurarsi di avere [installato l'emulatore di HoloLens](install-the-tools.md).
* In Visual Studio, selezionare la **x86** compilare configurazione dell'app

  ![configurazione in Visual Studio build x86](images/x86setting.png)<br>
* Selezionare **emulatore HoloLens** nel menu a discesa destinazione distribuzione

  ![HoloLens emulatore nell'elenco di destinazioni di distribuzione](images/deployemulator-500px.png)<br>
* Selezionare **Debug > Avvia debug** per distribuire l'app e avviare il debug.
* L'emulatore verrà avviare ed eseguire l'app.
* Con una tastiera, mouse e/o un controller Xbox, impostare l'app nel mondo per avviarla.

  ![HoloLens emulatore caricato con un esempio di UWP](images/hololensemulatorwithuwpsample-800px.png)<br>

### <a name="next-steps"></a>Passaggi successivi

A questo punto, può verificarsi una delle seguenti operazioni:
1. L'app verrà Mostra la schermata iniziale e avviarne l'esecuzione dopo l'inserimento nell'emulatore. fantastico!
2. Dopo avere visualizzato un'animazione di caricamento per ologramma 2D, interromperà il caricamento e verrà visualizzato solo l'app presso la schermata iniziale. Ciò significa che si è verificato e richiederà ulteriore analisi per comprendere come porta la tua app in vita in realtà mista.

Per ottenere la fine dello causa l'app UWP non venga avviato su HoloLens, è possibile eseguire il debug.

### <a name="running-your-uwp-app-in-the-debugger"></a>Esegue l'app UWP nel debugger

Questa procedura illustrerà di debug dell'app UWP usando il debugger di Visual Studio.
* Se non già stato fatto, aprire la soluzione in Visual Studio. Modificare la destinazione per il **HoloLens emulatore** e la configurazione della build per **x86**.
* Selezionare **Debug > Avvia debug** per distribuire l'app e avviare il debug.
* Inserire l'app in tutto il mondo con il mouse, tastiera o controller Xbox.
* Visual Studio a questo punto dovrebbe interrompersi in una posizione nel codice dell'app.
  - Se l'app non immediatamente l'arresto anomalo del sistema o interrompere il debugger a causa di un errore non gestito, quindi passare a un test delle funzionalità principali dell'app per assicurarsi che tutto sia in esecuzione e funzionanti. È possibile riscontrare errori, ad esempio illustrata di seguito (eccezioni interne che vengono gestite). Per assicurarsi di che non perdere gli errori interni che influisce sull'esperienza dell'app, eseguire i test automatizzati e unit test per assicurarsi che tutto funzioni come previsto.

![HoloLens emulatore caricato con un esempio di UWP che illustra un'eccezione di sistema](images/hololensemulatorwithuwpsampleexception-800px.png)

## <a name="update-your-ui"></a>Aggiornare l'interfaccia utente

Ora che l'esecuzione dell'app UWP in auricolari coinvolgenti e/o HoloLens come ologramma 2D, quindi ci assicureremo che somigli accattivante. Ecco alcuni aspetti da considerare:
* Realtà mista di Windows eseguirà tutte le app 2D con una risoluzione fissa e DPI che equivale a 853 x 480 pixel efficace. È consigliabile se la progettazione deve perfezionamento su questa scala e controllare le indicazioni di progettazione seguenti per migliorare l'esperienza in HoloLens e auricolari coinvolgente e concreto.
* Realtà mista di Windows [nepodporuje](app-model.md) 2D riquadri animati. Se la funzionalità principale visualizza informazioni su un riquadro in tempo reale, si consiglia di spostare nuovamente le informazioni nell'app o esplorare [nelle schermate di avvio app 3D](3d-app-launcher-design-guidance.md).

### <a name="2d-app-view-resolution-and-scale-factor"></a>Fattore di scala e la risoluzione di visualizzazione 2D app

![Da Progettazione reattiva](images/scale-500px.png)

Windows 10 Sposta tutti progettazione visiva da pixel sullo schermo reale in base al **pixel effettivi**. Vale a dire, gli sviluppatori di progettano l'interfaccia utente seguente di Windows 10 Human Interface Guidelines di pixel effettivi e il ridimensionamento di Windows garantisce i pixel effettivi sono le dimensioni corrette per l'usabilità tra dispositivi, le risoluzioni, DPI, e così via. Vedere questo [lettura eccezionale su MSDN](https://msdn.microsoft.com/library/windows/apps/Dn958435.aspx) per altre informazioni, nonché ciò [presentation compilazione](http://video.ch9.ms/sessions/build/2015/2-63_Build_2015_Windows_Scaling.pptx).

Anche con la capacità univoca di inserire le app nel tuo mondo in corrispondenza di un intervallo delle distanze compresa, visualizzazione televisiva distanze sono consigliate per produrre la migliore leggibilità e l'interazione con sguardo/movimento. Per questo motivo, uno slate di casa di realtà mista virtuale verrà visualizzata la visualizzazione UWP flat in:

**1280x720, 150% DPI** (853 x 480 pixel effettivo)

Questa soluzione presenta diversi vantaggi:
* Questo layout di pixel effettivi avrà sulla stessa densità di informazioni come un tablet o desktop di piccole dimensioni.
* Corrisponde al DPI fisso e pixel effettivi per le app UWP in esecuzione su Xbox One, l'abilitazione di un'esperienza trasparente tra dispositivi.
* Queste dimensioni sono corrette per la gamma di operativo distanze per le app nel mondo di aumento del numero.

### <a name="2d-app-view-interface-design-best-practices"></a>App 2D visualizzazione dell'interfaccia di progettazione consigliate

**Eseguire:**
* Seguire le [Windows 10 Human Interface linee guida (HIG)](https://dev.windows.com/design) per gli stili, le dimensioni dei caratteri e le dimensioni del pulsante. HoloLens eseguirà le operazioni per garantire che l'app include i modelli dell'app compatibile, le dimensioni del testo leggibile e ridimensionamento destinazione hit appropriata.
* Assicurarsi che segue l'interfaccia utente per procedure consigliate [progettazione reattiva](https://msdn.microsoft.com/library/windows/apps/dn958435.aspx) al meglio con del HoloLen univoco di risoluzione e DPI.
* Usare le raccomandazioni di tema "light" colore di Windows.

**Non:**
* Modificare l'interfaccia utente troppo drasticamente quando in realtà mista, per assicurarsi che gli utenti hanno un'esperienza familiare da e verso le cuffie.

### <a name="understand-the-app-model"></a>Comprendere il modello di app

Il [modello di app](app-model.md) per realtà mista è progettato per usare la home page realtà mista, in cui molte App in tempo reale tra loro. È possibile scegliere l'equivalente di realtà mista del desktop, in cui viene eseguito contemporaneamente molte App 2D. Ciò può influire sul ciclo di vita delle app, i riquadri e altre funzionalità chiave dell'app.

### <a name="app-bar-and-back-button"></a>Barra dell'App e pulsante Indietro

Le visualizzazioni 2D sono decorate con una barra app sopra il relativo contenuto. Barra dell'app ha due punti di personalizzazione specifici dell'app:

**Titolo:** consente di visualizzare il *displayname* del riquadro associato all'istanza di app

**Pulsante indietro:** genera il *[BackRequested](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.backrequested.aspx)* eventi quando premuto. Visibilità pulsante Indietro è controllata dal  *[SystemNavigationManager.AppViewBackButtonVisibility](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.aspx)*.

![App barra dell'interfaccia utente nella vista app 2D](images/12697297-10104100857470613-1470416918759008487-o-500px.jpg)<br>
*App barra dell'interfaccia utente nella vista app 2D*

### <a name="test-your-2d-apps-design"></a>Progettazione dell'app 2D di test

È importante testare l'app per assicurarsi che il testo è leggibile e i pulsanti sono definibili come destinazione dell'app complessiva risulta corretto. È possibile [testare](testing-your-app-on-hololens.md) cuffie desktop, un HoloLens, un emulatore o un dispositivo a tocco con risoluzione impostato su 1280 x 720 @150%.

## <a name="new-input-possibilities"></a>Nuove possibilità di input

HoloLens Usa sensori profondità avanzate per vedere tutto il mondo e visualizzare gli utenti. In questo modo i movimenti della mano avanzate, ad esempio [bloom](gestures.md#bloom) e [-indice puntato](gestures.md#air-tap). Anche abilitare microfoni potenti [vocali esperienze](voice-input.md).

Con Desktop auricolari, gli utenti possono usare i controller di movimento per puntare all'App ed eseguire azioni. È anche possibile usare un gamepad, la selezione di oggetti con loro sguardo.

Windows si occupa di tali complessità per le app UWP, conversione di [estasiati](gaze.md), i movimenti, voce e movimento di input di controller per [gli eventi puntatore](https://msdn.microsoft.com/library/windows/apps/mt404610#pointer_events) che sottraggono il meccanismo di input. Ad esempio, l'utente può avere eseguito un aria-toccare con mano o il pull di selezionare il trigger in un controller di movimento, ma le applicazioni 2D non devono sapere dove proviene l'input: viene semplicemente visualizzato un tocco 2D premere, come se su un touchscreen.

Di seguito sono i concetti o scenari di alto livello che è necessario comprendere per l'input quando si attiva l'app UWP per HoloLens:
* [Estasiati](gaze.md) assume la forma degli eventi di passaggio del mouse, che possono attivare in modo imprevisto i menu, i riquadri a comparsa o altri elementi dell'interfaccia utente visualizzata facendo semplicemente gazing intorno all'app.
* Sguardo non precisa come input del mouse. Usare ridimensionati in modo appropriato hit destinazioni per HoloLens, simile a pressoché applicazioni per dispositivi mobili. Piccoli elementi vicino ai bordi dell'app sono particolarmente difficili da interagire con.
* Gli utenti devono cambiare la modalità di input per passare da scorrere verso il trascinamento per la panoramica di due dita. Se l'app è stato progettato per l'input tocco, è possibile garantire che nessuna funzionalità principale è bloccato dietro la panoramica di due dita. In questo caso, è consigliabile che i meccanismi di input alternativi, ad esempio i pulsanti in grado di avviare la panoramica di due dita. Ad esempio, l'app esegue il mapping può eseguire lo zoom avanti con la panoramica di due dita, ma con un segno più, meno e ruota pulsante per simulare le stesse interazioni zoom con clic singolo.

[Input vocale](voice-input.md) è una parte essenziale dell'esperienza di realtà mista. Sono stati abilitati tutti speech API che sono in Windows 10 potenziamento Cortana quando si usa un auricolare.

## <a name="publish-and-maintain-your-universal-app"></a>Pubblicare e gestire le app universali

Una volta che l'app è in esecuzione, pacchetto dell'app per [lo invii a di Microsoft Store](submitting-an-app-to-the-microsoft-store.md).

## <a name="see-also"></a>Vedere anche
* [Modello di App](app-model.md)
* [Sguardo](gaze.md)
* [Movimento](gestures.md)
* [Controller di movimento](motion-controllers.md)
* [Voce](voice-input.md)
* [Invio di un'app per i Microsoft Store](submitting-an-app-to-the-microsoft-store.md)
* [Uso dell'emulatore HoloLens](using-the-hololens-emulator.md)

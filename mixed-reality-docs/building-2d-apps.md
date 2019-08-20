---
title: Aggiornamento delle app UWP 2D per realtà mista
description: Questo articolo illustra come aggiornare l'app di piattaforma UWP (Universal Windows Platform) 2D esistente per l'esecuzione in HoloLens e in Windows con cuffie immersive in realtà mista.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: app 2D, UWP, app Flat, HoloLens, auricolare immersivo, modello di app, pulsante indietro, barra delle applicazioni, dpi, risoluzione, scala
ms.openlocfilehash: f9792a7e5fd9729bf9f5f632c699c74c58c10ddf
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414218"
---
# <a name="updating-2d-uwp-apps-for-mixed-reality"></a>Aggiornamento delle app UWP 2D per realtà mista

La realtà mista di Windows consente a un utente di visualizzare gli ologrammi come se fossero più appropriati, nel mondo fisico o digitale. Al suo nucleo, sia HoloLens che i PC desktop a cui si alleghino gli accessori per auricolari immersivi sono dispositivi Windows 10. Ciò significa che è possibile eseguire quasi tutte le app piattaforma UWP (Universal Windows Platform) (UWP) nell'archivio come app 2D.

## <a name="creating-a-2d-uwp-app-for-mixed-reality"></a>Creazione di un'app UWP 2D per realtà mista

Il primo passaggio per l'uso di un'app 2D per gli auricolari a realtà mista consiste nel fare in modo che l'app venga eseguita come app 2D standard sul monitor desktop.

### <a name="building-a-new-2d-uwp-app"></a>Creazione di una nuova app UWP 2D

Per creare una nuova app 2D per la realtà mista, è sufficiente compilare un'app piattaforma UWP (Universal Windows Platform) 2D standard (UWP). Non sono necessarie altre modifiche dell'app per l'app da eseguire come uno Slate in realtà mista.

Per iniziare a creare un'app UWP 2D, vedere l'articolo [creare la prima app](https://docs.microsoft.com/windows/uwp/get-started/your-first-app) .

### <a name="bringing-an-existing-2d-store-app-to-uwp"></a>Introduzione di un'app di archivio 2D esistente a UWP

Se si dispone già di un'app di Windows 2D nello Store, è necessario assicurarsi che sia destinata a Windows 10 piattaforma UWP (Universal Windows Platform) (UWP). Ecco tutti i potenziali punti di partenza che è possibile avere con l'App Store:
<br>

|  Punto di partenza  |  Destinazione piattaforma manifesto AppX  |  Come rendere universale? | 
|----------|----------|----------|
|  Windows Phone (Silverlight)  |  Manifesto dell'applicazione Silverlight |  [Eseguire la migrazione a WinRT](https://msdn.microsoft.com/library/windows/apps/dn642486(v=vs.105).aspx) | 
|  Windows Phone 8,1 universale  |  8,1 manifesto AppX che non include la piattaforma di destinazione  |  [Eseguire la migrazione dell'app al piattaforma UWP (Universal Windows Platform)](https://msdn.microsoft.com/library/mt148501.aspx) | 
|  Windows Store 8  |  8 manifesto AppX che non include la piattaforma di destinazione  |  [Eseguire la migrazione dell'app al piattaforma UWP (Universal Windows Platform)](https://msdn.microsoft.com/library/mt148501.aspx) | 
|  Windows Store 8,1 universale  |  8,1 manifesto AppX che non include la piattaforma di destinazione  |  [Eseguire la migrazione dell'app al piattaforma UWP (Universal Windows Platform)](https://msdn.microsoft.com/library/mt148501.aspx) | 

Se si dispone di un'app di Unity 2D attualmente compilata come app Win32 (la destinazione di compilazione "PC, Mac & Linux standalone"), è possibile usare la realtà mista cambiando Unity alla destinazione di compilazione "piattaforma UWP (Universal Windows Platform)".

Verranno illustrati i modi in cui è possibile limitare l'app in modo specifico a HoloLens usando la famiglia di dispositivi Windows. olografica [riportata di seguito](#publish-and-maintain-your-universal-app).

### <a name="run-your-2d-app-in-a-windows-mixed-reality-immersive-headset"></a>Eseguire l'app 2D in un auricolare immersivo a realtà mista di Windows

Se l'app 2D è stata distribuita nel computer desktop in cui si sta sviluppando ed è stata tentata nel monitor, si è già pronti per provarla in una cuffia desktop immersiva.

È sufficiente passare al menu Start all'interno dell'auricolare con la realtà mista e avviare l'app da questa posizione. La shell desktop e la shell olografica condividono lo stesso set di app UWP, quindi l'app deve essere già presente dopo la distribuzione da Visual Studio.

## <a name="targeting-both-immersive-headsets-and-hololens"></a>Per gli auricolari immersivi e HoloLens

La procedura è stata completata. L'app usa ora Windows 10 piattaforma UWP (Universal Windows Platform) (UWP).

L'app è ora in grado di essere eseguita sui dispositivi Windows odierni, ad esempio desktop, dispositivi mobili, Xbox, Windows Mixed Reality, cuffie immersive e HoloLens, nonché dispositivi Windows futuri. Tuttavia, per fare in modo che tutti questi dispositivi siano destinati a tutti i dispositivi, è necessario verificare che l'app sia destinata al gruppo di dispositivi Windows. universali.

### <a name="change-your-device-family-to-windowsuniversal"></a>Modificare la famiglia di dispositivi in Windows. Universal

Passiamo ora al manifesto di AppX per assicurarsi che l'app Windows 10 UWP possa essere eseguita in HoloLens:
* Aprire il file della soluzione dell'app con **Visual Studio** e passare al manifesto del pacchetto dell'app
* Fare clic con il pulsante destro del mouse sul file **Package. appxmanifest** nella soluzione e passare a **Visualizza codice**<br>
  ![Package. appxmanifest in Esplora soluzioni](images/openappxmanifest-500px.png)<br>
* Verificare che la piattaforma di destinazione sia Windows. Universal nella sezione dipendenze
  ```
  <Dependencies>
    <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
  </Dependencies>
  ```
* Salvare!

Se non si usa Visual Studio per l'ambiente di sviluppo, è possibile aprire **AppXManifest. XML** nell'editor di testo di propria scelta per assicurarsi che la destinazione sia **Windows. Universal** *TargetDeviceFamily*.

### <a name="run-in-the-hololens-emulator"></a>Esecuzione nell'emulatore di HoloLens

Ora che l'app UWP è destinata a "Windows. Universal", è possibile compilare l'app ed eseguirla nell'emulatore di [HoloLens](using-the-hololens-emulator.md).
* Assicurarsi [di aver installato l'emulatore di HoloLens](install-the-tools.md).
* In Visual Studio selezionare la configurazione della build **x86** per l'app

  ![configurazione della build x86 in Visual Studio](images/x86setting.png)<br>
* Selezionare **HoloLens Emulator** nel menu a discesa destinazione distribuzione

  ![Emulatore di HoloLens nell'elenco delle destinazioni di distribuzione](images/deployemulator-500px.png)<br>
* Selezionare **debug > avviare il debug** per distribuire l'app e avviare il debug.
* L'emulatore avvierà ed eseguirà l'app.
* Con una tastiera, un mouse e/o un controller Xbox, inserire l'app nel mondo per avviarla.

  ![Emulatore di HoloLens caricato con un esempio UWP](images/hololensemulatorwithuwpsample-800px.png)<br>

### <a name="next-steps"></a>Passaggi successivi

A questo punto, può verificarsi una delle due situazioni seguenti:
1. L'app visualizzerà il relativo Splash e inizierà a essere eseguito dopo che è stato inserito nell'emulatore. Awesome!
2. O dopo aver visualizzato un'animazione di caricamento per un ologramma 2D, il caricamento si interrompe e l'app viene visualizzata solo nella schermata iniziale. Ciò significa che si è verificato un errore ed è necessario approfondire la conoscenza di come portare la propria applicazione a vivere in realtà mista.

Per raggiungere la fine di ciò che potrebbe causare l'avvio dell'app UWP in HoloLens, è necessario eseguire il debug.

### <a name="running-your-uwp-app-in-the-debugger"></a>Esecuzione dell'app UWP nel debugger

Questi passaggi consentono di eseguire il debug dell'app UWP usando il debugger di Visual Studio.
* Se non è già stato fatto, aprire la soluzione in Visual Studio. Modificare la destinazione nell'emulatore di **HoloLens** e la configurazione della build in **x86**.
* Selezionare **debug > avviare il debug** per distribuire l'app e avviare il debug.
* Inserisci l'app in tutto il mondo con il mouse, la tastiera o il controller Xbox.
* A questo punto, Visual Studio dovrebbe interrompersi nel codice dell'app.
  - Se l'app non si arresta in modo anomalo o si interrompe nel debugger a causa di un errore non gestito, esaminare una sessione di test delle funzionalità principali dell'app per assicurarsi che tutto sia in esecuzione e funzionante. Potrebbe essere visualizzato un errore simile a quello illustrato di seguito (eccezioni interne gestite). Per assicurarsi di non perdere gli errori interni che influiscano sull'esperienza dell'app, eseguire i test automatizzati e gli unit test per assicurarsi che tutto funzioni come previsto.

![Emulatore di HoloLens caricato con un esempio UWP che mostra un'eccezione di sistema](images/hololensemulatorwithuwpsampleexception-800px.png)

## <a name="update-your-ui"></a>Aggiornare l'interfaccia utente

Ora che l'app UWP è in esecuzione su auricolari immersivi e/o HoloLens come ologramma 2D, ci assicureremo che risulti bello. Ecco alcuni aspetti da considerare:
* La realtà mista di Windows eseguirà tutte le app 2D con una risoluzione fissa e un valore DPI equivalente a 853x480 pixel effettivi. Valutare se la progettazione necessita di perfezionamento su questa scala ed esaminare le linee guida di progettazione riportate di seguito per migliorare l'esperienza con HoloLens e auricolari immersivi.
* La realtà mista di Windows [non supporta](app-model.md) i riquadri animati 2D. Se la funzionalità di base Mostra informazioni su un riquadro animato, è consigliabile riportare le informazioni nell'app o esplorare i [lanci di app 3D](3d-app-launcher-design-guidance.md).

### <a name="2d-app-view-resolution-and-scale-factor"></a>risoluzione e fattore di ridimensionamento di visualizzazione app 2D

![Dalla progettazione reattiva](images/scale-500px.png)

Windows 10 sposta tutti i progetti visivi da pixel dello schermo reale a **effettivi pixel**. Ciò significa che gli sviluppatori progettano l'interfaccia utente seguendo le linee guida dell'interfaccia umana di Windows 10 per i pixel effettivi e il ridimensionamento di Windows assicura che i pixel effettivi siano le dimensioni corrette per l'usabilità tra dispositivi, soluzioni, DPI e così via. Per altre informazioni e per questa [presentazione di compilazione](http://video.ch9.ms/sessions/build/2015/2-63_Build_2015_Windows_Scaling.pptx), vedere la pagina [relativa alla lettura su MSDN](https://msdn.microsoft.com/library/windows/apps/Dn958435.aspx) .

Anche con la capacità univoca di collocare le app nel mondo a una gamma di distanze, sono consigliate le distanze di visualizzazione TV, per produrre la migliore leggibilità e l'interazione con lo sguardo o il movimento. Per questo motivo, una lavagna virtuale nella Home realtà mista visualizzerà la visualizzazione UWP piatta in:

**1280x720, 150% dpi** (853x480 pixel effettivi)

Questa risoluzione presenta diversi vantaggi:
* Questo layout di pixel effettivo avrà circa la stessa densità di informazioni di un tablet o di un piccolo desktop.
* Corrisponde al valore DPI fisso e ai pixel effettivi per le app UWP in esecuzione su Xbox One, consentendo un'esperienza trasparente tra i dispositivi.
* Questa dimensione sembra corretta se ridimensionata nell'intervallo di distanza operativa per le app nel mondo.

### <a name="2d-app-view-interface-design-best-practices"></a>procedure consigliate per la progettazione dell'interfaccia di visualizzazione app 2D

**Fare**
* Seguire le [linee guida dell'interfaccia umana di Windows 10 (HIG)](https://dev.windows.com/design) per gli stili, le dimensioni dei tipi di carattere e i pulsanti. HoloLens eseguirà il lavoro per garantire che l'app abbia modelli di app compatibili, dimensioni del testo leggibili e dimensioni appropriate per il target target.
* Assicurarsi che l'interfaccia utente segua le procedure consigliate per la [progettazione reattiva](https://msdn.microsoft.com/library/windows/apps/dn958435.aspx) per ottenere risultati ottimali con la risoluzione univoca di HOLOLEN e dpi.
* Usare le raccomandazioni relative al tema colori "Light" di Windows.

**Non:**
* Modificare l'interfaccia utente in modo drastico quando si è in realtà mista, per garantire agli utenti un'esperienza familiare all'interno e all'esterno dell'auricolare.

### <a name="understand-the-app-model"></a>Informazioni sul modello di app

Il [modello di app](app-model.md) per la realtà mista è progettato per l'uso della Home realtà mista, in cui molte app si trovano insieme. Si può pensare a questo come l'equivalente della realtà mista del desktop, in cui è possibile eseguire molte app 2D in una sola volta. Ciò ha implicazioni sul ciclo di vita dell'app, i riquadri e altre funzionalità chiave dell'app.

### <a name="app-bar-and-back-button"></a>Barra dell'app e pulsante indietro

le visualizzazioni 2D sono decorate con una barra dell'app sopra il contenuto. La barra dell'app presenta due punti di personalizzazione specifici dell'app:

**Title:** Visualizza il *DisplayName* del riquadro associato all'istanza dell'app

**Back Button:** genera l'evento *[BackRequested](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.backrequested.aspx)* quando viene premuto. La visibilità del pulsante indietro è controllata da *[SystemNavigationManager. AppViewBackButtonVisibility](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.aspx)* .

![Interfaccia utente della barra dell'app nella visualizzazione app 2D](images/12697297-10104100857470613-1470416918759008487-o-500px.jpg)<br>
*Interfaccia utente della barra dell'app nella visualizzazione app 2D*

### <a name="test-your-2d-apps-design"></a>Testare la progettazione dell'app 2D

È importante testare l'app per verificare che il testo sia leggibile, che i pulsanti siano mirabili e che l'app complessiva appaia corretta. È possibile [eseguire il test](testing-your-app-on-hololens.md) su un auricolare desktop, un HoloLens, un emulatore o un dispositivo touch con risoluzione impostata @150sul 1280x720%.

## <a name="new-input-possibilities"></a>Nuove possibilità di input

HoloLens usa sensori di profondità avanzati per vedere il mondo e visualizzare gli utenti. Questo consente movimenti avanzati della mano, ad esempio [Bloom](gestures.md#bloom) e il [tocco aereo](gestures.md#air-tap). I microtelefoni potenti consentono anche l' [esperienza vocale](voice-input.md).

Con le cuffie Desktop, gli utenti possono usare i controller di movimento per puntare alle app e intervenire. Possono anche usare un gamepad, destinando gli oggetti allo sguardo.

Windows si occupa di tutte queste complessità per le app UWP, traducendo gli [sguardi](gaze.md), i movimenti, l'input del controller voce e movimento per [gli eventi puntatore](https://msdn.microsoft.com/library/windows/apps/mt404610#pointer_events) che astraggono il meccanismo di input. Ad esempio, è possibile che un utente abbia eseguito un tocco con la propria mano o abbia premuto il trigger SELECT in un controller di movimento, ma le applicazioni 2D non devono sapere da dove proviene l'input, ma solo una pressione 2D touch, come se si trattasse di un touchscreen.

Ecco i concetti e gli scenari di alto livello che è necessario comprendere per l'input quando si porta l'app UWP in HoloLens:
* Lo [sguardo](gaze.md) si sposta negli eventi di passaggio del mouse, che possono attivare menu, riquadri a comparsa o altri elementi dell'interfaccia utente per apparire semplicemente guardando l'app.
* Lo sguardo non è preciso come l'input del mouse. USA destinazioni di hit size appropriate per HoloLens, come le applicazioni per dispositivi mobili intuitive per il tocco. Gli elementi piccoli vicino ai bordi dell'app sono particolarmente difficili da interagire con.
* Gli utenti devono passare dalla modalità di input allo scorrimento fino a due panning con due dita. Se l'app è stata progettata per l'input tocco, provare a garantire che nessuna funzionalità principale venga bloccata dietro la Panoramica di due dita. In tal caso, valutare la possibilità di usare meccanismi di input alternativi come pulsanti che possono avviare due panning del dito. L'app Maps, ad esempio, è in grado di ingrandire due dita, ma presenta un pulsante con il segno più, il segno meno e la rotazione per simulare le stesse interazioni di zoom con singoli clic.

L' [input vocale](voice-input.md) è una parte essenziale dell'esperienza di realtà mista. Sono state abilitate tutte le API vocali che si trovano in Windows 10 Cortana quando si usa un auricolare.

## <a name="publish-and-maintain-your-universal-app"></a>Pubblicare e gestire l'app universale

Quando l'app è in esecuzione, creare un pacchetto dell'app per [inviarla al Microsoft Store](submitting-an-app-to-the-microsoft-store.md).

## <a name="see-also"></a>Vedere anche
* [Modello di app](app-model.md)
* [Sguardo fisso](gaze.md)
* [Gesto](gestures.md)
* [Controller del movimento](motion-controllers.md)
* [Input vocale](voice-input.md)
* [Invio di un'app a Microsoft Store](submitting-an-app-to-the-microsoft-store.md)
* [Uso dell'emulatore HoloLens](using-the-hololens-emulator.md)

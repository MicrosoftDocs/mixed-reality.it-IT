---
title: Esplorazione di realtà mista di Windows home
description: HoloLens e realtà mista di Windows auricolari condividono un paradigma per l'avvio, l'inserimento e modifica di App e i modelli 3D nell'ambiente in uso (se fisico o digitale). Informazioni su come passare la realtà mista di Windows home in entrambi i tipi di dispositivo.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: shell, del sistema operativo, piattaforma, a casa cliff, casa, home, ambiente, start, menu start, menu iniziale, pin, app, le app di avvio, inserire le app, teleport spostarsi, esplorare
ms.openlocfilehash: 1ca6dd66506a64ad2e1c21870fee2725ddf20bd8
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604899"
---
# <a name="navigating-the-windows-mixed-reality-home"></a>Esplorazione di realtà mista di Windows home

Esattamente come viene avviata l'esperienza di PC Windows con il desktop, realtà mista di Windows viene avviata con la home page. La realtà mista di Windows home sfrutta la nostra capacità innata per comprendere e spostarsi tra punti 3D. Con HoloLens, la home page è lo spazio fisico. Con immersive auricolari, la home page è un punto virtuale.

La home page è anche in cui si userà il menu Start aprire e inserire le App e il contenuto. È possibile compilare la home page con contenuto di realtà mista e multitasking con più App contemporaneamente. Le operazioni posizionate in casa rimangono non esiste, anche se si riavvia il dispositivo.

## <a name="start-menu"></a>Menu Start

![Menu Start nei Microsoft HoloLens](images/start-500px.png)

Nel menu Start è costituito da:
* Informazioni di sistema (lo stato della rete, la percentuale della batteria, ora corrente e volume)
* Cortana (auricolari coinvolgenti, un riquadro di avvio; su HoloLens, nella parte superiore di inizio)
* App bloccate
* Pulsante tutte le App (segno più)
* I pulsanti di foto e video per [acquisizione di realtà mista](mixed-reality-capture.md)

Navigare tra le app bloccate e tutte le app selezionando il segno più o meno. Per aprire il menu Start in HoloLens, usare il movimento bloom. In un visore VR immersivi, premere il pulsante di Windows nel controller.

## <a name="launching-apps"></a>Avvio delle App

Per avviare un'app, selezionarla nel menu Start. Non verrà più visualizzato nel menu Start e l'app verrà aperta in modalità di selezione host, come una finestra di 2D o una [modello 3D](implementing-3d-app-launchers.md).

Per eseguire l'app, è necessario inserirla nella propria abitazione:
1. Usare il [estasiati](gaze.md) o un controller per posizionare l'app in cui si desidera. Verrà allineato automaticamente (in dimensioni e posizione) per garantire la conformità per lo spazio in cui inserire.
2. Inserire l'app usando il pulsante di selezione (immersive auricolari) o puntato (HoloLens). Per annullare e riportare online il menu Start, usare il movimento bloom o con il pulsante di Windows.

[Le app 2D](building-2d-apps.md), creato per desktop, dispositivi mobili, o Xbox può essere modificato per l'esecuzione come App immersive di realtà mista tramite il [HolographicSpace API](https://msdn.microsoft.com/library/windows/apps/windows.graphics.holographic.holographicspace.aspx). Un'app immersiva indirizza l'utente da casa e in un'esperienza coinvolgente e concreto. Gli utenti possono restituire home con il movimento bloom (HoloLens) o premendo il pulsante di Windows nel rispettivo controller (immersive auricolari).

Le app possono essere avviate anche tramite un'API di app-app o tramite Cortana.

![App nella home di realtà mista di Windows](images/mixed-reality-home-500px.png)

## <a name="moving-and-adjusting-apps"></a>Lo spostamento e la regolazione delle App

Selezionare **Adjust** sull'app barra per visualizzare i controlli che lo spostamento, scalabilità, e rotazione misto realtà. Al termine, seleziona **Invia**.

![Lo slate di archivio in modalità di regolazione (frame blu). Si noti barra dell'app (superiore) è stato modificato per includere 'Done' e 'Remove' pulsanti.](images/adjust-500px.png)

Diverse App potrebbe avere opzioni aggiuntive nella barra dell'app. Ad esempio, Microsoft Edge ha *Scroll*, *trascinamento*, e *Zoom* scelte. 

![Barra dell'App per le app 2D in esecuzione su HoloLens](images/holobar-500px.png)

Il **nuovamente** pulsante consente di passare nuovamente alle schermate precedentemente visualizzate nell'app. Interrompe quando si raggiunge l'inizio delle esperienze che sono stati visualizzati nell'app e non passerà ad altre app.

## <a name="getting-around-your-home"></a>Recupero di tutta la casa

Con **HoloLens**, passando da una spazio fisico per spostarsi all'interno della casa.

Con **auricolari immersive**, in modo analogo è possibile iniziare subito e camminare nel playspace per spostarsi all'interno di un'area simile nel mondo virtuale. Per spostare tra distanze più lunghe, è possibile usare il thumbstick sul controller per praticamente "percorrere" oppure è possibile usare *teletrasporto* per saltare immediatamente distanze più lunghe.

![Teletrasporto nella home di realtà mista di Windows](images/teleportation-500px.png)

**Per teleport:**
1. Visualizziamo il contorno teletrasporto tratteggiato.
   * Usando [controller di movimento](motion-controllers.md): premere il thumbstick in avanti e li mantiene in tale posizione.
   * Utilizzo di un controller Xbox: premere il thumbstick sinistro in avanti e li mantiene in tale posizione.
   * Utilizzando il mouse: tenere premuto il pulsante destro del mouse (e usare la rotellina di scorrimento per ruotare la direzione in cui si vuole affrontare quando si teleport).
2. Posizionare il tratteggiato in cui si desidera teleport.
   * Usando [controller di movimento](motion-controllers.md): inclinare il controller (in cui si sta tenendo la levetta in avanti) per spostare il tratteggiato.
   * Utilizzo di un controller Xbox: usare il [estasiati](gaze.md) per spostare il tratteggiato.
   * Utilizzando il mouse: passa il mouse per spostare il tratteggiato.
3. Rilasciare il pulsante per teleport in cui è stato inserito il tratteggiato.

**A praticamente "procedura:"**
* Usando [controller di movimento](motion-controllers.md): fare clic sulla levetta e tenere premuto, quindi spostare il thumbstick nella direzione desiderata per "percorrere".
* Utilizzo di un controller Xbox: fare clic sul thumbstick sinistro e tenere premuto, quindi spostare il thumbstick nella direzione desiderata per "percorrere".

## <a name="immersive-headset-input-support"></a>Supporto input visore VR immersivi

[Auricolari coinvolgenti di realtà mista di Windows](immersive-headset-hardware-details.md) supportano più tipi di input per l'esplorazione di realtà mista di Windows home. HoloLens non supporta gli input degli accessori per lo spostamento, in quanto si spostano fisicamente e visualizzare l'ambiente. Tuttavia, in modo HoloLens [supporta input](hardware-accessories.md) per l'interazione con le app.

### <a name="motion-controllers"></a>Controller di movimento

La migliore esperienza di realtà mista di Windows verranno con realtà mista di Windows [controller di movimento](motion-controllers.md) tale rilevamento 6 gradi di libertà di supporto usando solo i sensori nelle cuffie - Nessun fotocamere esterni o marcatori necessari.

Comandi di navigazione sarà presto disponibile.

### <a name="gamepad"></a>Game pad
* **Thumbstick sinistro:**
  * Premere e tenere premuto il thumbstick sinistro in avanti per visualizzare il [teletrasporto](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) tratteggiato.
  * Toccare il thumbstick sinistro, destro, eseguire il backup per spostare a sinistra, destra oppure eseguire il backup a piccoli incrementi.
  * Fare clic sul thumbstick sinistro e tenere premuto, quindi spostare il thumbstick nella direzione desiderata per [praticamente "percorrere".](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)
* Toccare il **levetta destra** verso sinistra o destra per ruotare la direzione di spostamento di 45 gradi.
* Premendo il **oggetto** pulsante esegue un'istruzione select e si comporta come la [indice puntato](gestures.md#air-tap) movimento.
* Premendo il **Guida** viene visualizzata la [menu Start](navigating-the-windows-mixed-reality-home.md#start-menu) e agisce come il [bloom](gestures.md#bloom) movimento.
* Premere il **trigger a sinistra e destro** consente ingrandire o ridurre di un'app desktop 2D si interagisce con nella home page.

### <a name="keyboard-and-mouse"></a>Tastiera e mouse

**Nota:** Uso **tasto Windows + Y** per passare il mouse tra controllo desktop del computer e la realtà mista di Windows home.

All'interno di realtà mista di Windows home:
* Premere il **quindi fare clic su** pulsante del mouse esegue un'istruzione select e si comporta come il [indice puntato](gestures.md#air-tap) movimento.
* Che contiene il **fare doppio clic su** pulsante del mouse viene visualizzata la [teletrasporto](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) tratteggiato.
* Premendo il **Windows** tasto della tastiera consente di visualizzare i [dal Menu Start](navigating-the-windows-mixed-reality-home.md#start-menu) e agisce come il [bloom](gestures.md#bloom) movimento.
* Quando [gazing](gaze.md) in un'app desktop 2D, è possibile **quindi fare clic su** per selezionare, **fare doppio clic su** per visualizzare menu di scelta rapida e usare il **rotellina di scorrimento** di scorrimento (solo come sul desktop del computer).

## <a name="cortana"></a>Cortana

[Cortana](voice-input.md#hey-cortana) è analoga a assistente personale nella realtà mista di Windows, su PC e telefono. HoloLens è un microfono incorporato, ma auricolari immersive possono richiedere hardware aggiuntivo. Usare Cortana per aprire le app, riavviare il dispositivo, cercare online cose e altro ancora. Gli sviluppatori possono anche scegliere di [integrare Cortana](https://dev.windows.com/cortana) nelle proprie esperienze.

È anche possibile usare comandi vocali per evitare la home page. Ad esempio, puntare a un pulsante (tramite [estasiati](gaze.md) o un controller, a seconda del dispositivo) e scelgo "Select". Altri comandi vocali includono "Go home", "Grande", "più piccoli," "Chiudi" e "Affrontano me."

## <a name="store-settings-and-system-apps"></a>App Store e le impostazioni di sistema

Realtà mista di Windows ha un numero di App predefinite, ad esempio:
* **Microsoft Store** per ottenere le App e giochi
* **Hub di feedback** per inviare commenti e suggerimenti sul sistema e le app di sistema
* **Le impostazioni** per configurare le impostazioni di sistema ([inclusa la rete](connecting-to-wi-fi-on-hololens.md) e gli aggiornamenti del sistema)
* **Microsoft Edge** per esplorare i siti Web
* **Foto** per visualizzare e condividere foto e video
* **Calibrazione** (solo HoloLens) per regolare l'esperienza di HoloLens all'utente corrente
* **Scopri i movimenti** (HoloLens) o **informazioni su realtà mista** (auricolari immersive) per informazioni sull'uso del dispositivo
* **Visualizzatore 3D** per decorare il mondo con contenuto di realtà mista
* **Portale di realtà mista** (desktop) per l'installazione e la gestione di visore VR immersivi e streaming un'anteprima in tempo reale della vista nelle cuffie agli altri utenti.
* **Film e TV** Mostra per visualizzazione 360 video e più recenti film e tv
* **Cortana** per tutti gli assistenti virtuali deve
* **Desktop** (auricolari immersive) per visualizzare i monitor da tavolo mentre è in un visore VR immersivi
* **Esplora file** accedere ai file e cartelle che si trovano nel dispositivo

## <a name="see-also"></a>Vedere anche
* [Viste di App](app-views.md)
* [Controller di movimento](motion-controllers.md)
* [Accessori hardware](hardware-accessories.md)
* [Considerazioni relative all'ambiente per HoloLens](environment-considerations-for-hololens.md)
* [Implementazione di utilità di avvio app 3D](implementing-3d-app-launchers.md)
* [Creazione di modelli 3D per l'uso di casa di realtà mista di Windows](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)

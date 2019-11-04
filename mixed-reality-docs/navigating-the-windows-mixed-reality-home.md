---
title: Esplorazione della Home realtà mista di Windows
description: Gli auricolari per la realtà mista HoloLens e Windows condividono un paradigma per avviare, inserire e modificare le app e i modelli 3D nel proprio ambiente (sia fisico che digitale). Informazioni su come spostarsi nella Home realtà mista di Windows in entrambi i tipi di dispositivi.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Shell, sistema operativo, piattaforma, scogliera, casa, casa, ambiente, avvio, menu Start, menu Home, pin, app, avvia app, Inserisci app, Teleport, sposta, naviga
ms.openlocfilehash: 9de4cb44505d6cf4d0d3e4bd0fd9c5ee681063a5
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438157"
---
# <a name="navigating-the-windows-mixed-reality-home"></a>Esplorazione della Home realtà mista di Windows

Proprio come l'esperienza del PC Windows inizia con il desktop, la realtà mista di Windows inizia con la Home page. La Home realtà mista di Windows sfrutta la capacità innata di comprendere ed esplorare i punti 3D. Con HoloLens, la tua abitazione è il tuo spazio fisico. Con auricolari immersivi, la tua casa è una posizione virtuale.

A casa è anche possibile usare il menu Start per aprire e inserire app e contenuti. È possibile compilare la Home page con contenuto della realtà mista e multitasking usando più app nello stesso momento. Gli elementi da inserire in casa sono disponibili anche se si riavvia il dispositivo.

## <a name="start-menu"></a>Menu Start

![Menu Start in Microsoft HoloLens](images/start-500px.png)

Il menu Start è costituito da:
* Informazioni di sistema (stato della rete, percentuale della batteria, ora corrente e volume)
* Cortana (su auricolari immersivi, un riquadro iniziale; in HoloLens, nella parte superiore di Start)
* App aggiunte
* Pulsante tutte le app (segno più)
* Pulsanti foto e video per l' [acquisizione di realtà mista](mixed-reality-capture.md)

Passare tra le visualizzazioni app bloccate e tutte le app selezionando i pulsanti più o meno. Per aprire il menu Start in HoloLens, usare il movimento Bloom. Su un auricolare immersivo, premere il pulsante Windows sul controller.

## <a name="launching-apps"></a>Avvio di app

Per avviare un'app, selezionarla all'avvio. Il menu Start scomparirà e l'app si aprirà in modalità di posizionamento, come una finestra 2D o un [modello 3D](implementing-3d-app-launchers.md).

Per eseguire l'app, è necessario inserirla nella Home page:
1. Usare lo [sguardo](gaze-and-commit.md) o il controller per posizionare l'app dove si vuole. In questo modo, le dimensioni e la posizione verranno regolate automaticamente per essere conformi allo spazio in cui viene inserito.
2. Posizionare l'app usando il tocco di aria (HoloLens) o il pulsante Seleziona (cuffie immersive). Per annullare e ripristinare il menu Start, usare il gesto Bloom o il pulsante Windows.

le [app 2D](building-2d-apps.md), create per desktop, dispositivi mobili o Xbox possono essere modificate per l'esecuzione come app immersive di realtà mista usando l' [API HolographicSpace](https://msdn.microsoft.com/library/windows/apps/windows.graphics.holographic.holographicspace.aspx). Un'app immersiva porta l'utente fuori dalla casa e in un'esperienza immersiva. Gli utenti possono tornare a casa con il movimento Bloom (HoloLens) o premendo il pulsante Windows sul controller (cuffie immersive).

Le app possono essere avviate anche tramite un'API da app a app o tramite Cortana.

![App nella Home realtà mista di Windows](images/mixed-reality-home-500px.png)

## <a name="moving-and-adjusting-apps"></a>Spostamenti e regolazioni delle app

Selezionare **Adjust** sulla barra dell'app per visualizzare i controlli che consentono di spostare, ridimensionare e ruotare il contenuto della realtà mista. Al termine, selezionare **fine**.

![Ardesia del negozio in modalità di regolazione (cornice blu). Si noti che la barra dell'app (superiore) è cambiata per includere i pulsanti ' done ' è Remove '.](images/adjust-500px.png)

App diverse possono avere opzioni aggiuntive sulla barra dell'app. Microsoft Edge, ad esempio, dispone di opzioni di *scorrimento*, *trascinamento*e *Zoom* . 

![Barra dell'app per le app 2D in esecuzione in HoloLens](images/holobar-500px.png)

Il pulsante **indietro** Torna alle schermate visualizzate in precedenza nell'app. Verrà interrotto quando si raggiunge l'inizio delle esperienze visualizzate nell'app e non si passa ad altre app.

## <a name="getting-around-your-home"></a>Guida alla Home page

Con **HoloLens**, è possibile spostarsi nello spazio fisico per spostarsi all'interno della Home page.

Con le **cuffie immersive**, è possibile ottenere in modo analogo le playspace per spostarsi all'interno di un'area simile nel mondo virtuale. Per spostarsi tra le distanze più lunghe, è possibile usare levetta sul controller per la "procedura", oppure è possibile usare la *teleportazione* per passare immediatamente a distanze più lunghe.

![Teleportazione nella Home realtà mista di Windows](images/teleportation-500px.png)

**Per teletrasportarsi:**
1. Visualizzare il reticolo del Teleporting.
   * Usando i [controller di movimento](motion-controllers.md): premere il levetta in poi e tenerlo in tale posizione.
   * Utilizzando un controller Xbox: premere il levetta di sinistra in poi e tenerlo in tale posizione.
   * Uso del mouse: fare clic con il pulsante destro del mouse sul pulsante del mouse (e utilizzare la rotellina di scorrimento per ruotare la direzione da affrontare quando si trasporta).
2. Posizionare il reticolo in cui si vuole effettuare il teletrasporto.
   * Uso dei [controller di movimento](motion-controllers.md): inclinare il controller (su cui si trova il levetta in avanti) per spostare il reticolo.
   * Usando un controller Xbox: usare lo [sguardo](gaze-and-commit.md) per spostare il reticolo.
   * Utilizzando un mouse: spostare il mouse per spostare il reticolo.
3. Rilasciare il pulsante per teletrasportarsi in cui è stato inserito il reticolo.

**A "Walk:"**
* Uso dei [controller di movimento](motion-controllers.md): fare clic su levetta e tenendo premuto, quindi spostare il levetta nella direzione desiderata.
* Utilizzando un controller Xbox: fare clic su giù sul levetta a sinistra e quindi spostare il levetta nella direzione desiderata.

## <a name="immersive-headset-input-support"></a>Supporto per input per cuffie immersive

Gli [auricolari immersivi a realtà mista di Windows](immersive-headset-hardware-details.md) supportano più tipi di input per lo spostamento nella Home realtà mista di Windows. HoloLens non supporta gli input accessori per la navigazione, perché si esplorano fisicamente l'ambiente in uso. Tuttavia, HoloLens [supporta gli input](hardware-accessories.md) per l'interazione con le app.

### <a name="motion-controllers"></a>Controller di movimento

L'esperienza di realtà mista di Windows migliore sarà con i [controller di movimento](motion-controllers.md) per la realtà mista di Windows che supportano il rilevamento di 6 gradi di libertà usando solo i sensori presenti nell'auricolare. non sono richiesti fotocamere o marcatori esterni.

I comandi di navigazione saranno presto disponibili.

### <a name="gamepad"></a>Game pad
* **Levetta a sinistra:**
  * Premere e tenere premuto il levetta di sinistra per visualizzare il reticolo del [Teleporting](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) .
  * Toccare il levetta a sinistra, a destra o a sinistra per spostarsi a sinistra, a destra o indietro in piccoli incrementi.
  * Fai clic sul pulsante destro del mouse sul levetta a sinistra, quindi sposta il levetta nella direzione che preferisci ["Walk".](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)
* Toccare il **levetta destro** a sinistra o a destra per ruotare la direzione di 45 gradi.
* Premendo il pulsante **a** viene eseguita un'operazione SELECT che agisce come il gesto del [rubinetto d'aria](gaze-and-commit.md#composite-gestures) .
* Premendo il pulsante della **Guida** viene [visualizzato il menu Start](navigating-the-windows-mixed-reality-home.md#start-menu) , che agisce come il movimento [Bloom](system-gesture.md#bloom) .
* Premendo i **trigger Left e Right** è possibile eseguire lo zoom avanti e indietro di un'app desktop 2D con cui si interagisce nella Home page.

### <a name="keyboard-and-mouse"></a>Tastiera e mouse

**Nota:** Usare il **tasto Windows + Y** per passare il mouse tra il controllo del desktop del PC e la Home realtà mista di Windows.

All'interno della Home realtà mista di Windows:
* Se si preme il pulsante **sinistro** del mouse, viene eseguita una selezione che agisce come il movimento del [rubinetto d'aria](gaze-and-commit.md#composite-gestures) .
* Tenendo premuto il pulsante destro del mouse **,** viene visualizzata [la porta del reticolo.](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)
* Premendo il tasto **Windows** sulla tastiera si apre il [menu Start](navigating-the-windows-mixed-reality-home.md#start-menu) e si agisce come il movimento [Bloom](system-gesture.md#bloom) .
* Quando [si](gaze-and-commit.md) Guarda un'app desktop 2D, è possibile **fare clic** con il pulsante **destro** del mouse per visualizzare i menu di scelta rapida e utilizzare la **rotellina di scorrimento** per scorrere (proprio come nel desktop del PC).

## <a name="cortana"></a>Cortana

[Cortana](voice-input.md#hey-cortana) è il tuo assistente personale in realtà mista di Windows, proprio come su PC e telefono. HoloLens dispone di un microfono integrato, ma gli auricolari immersivi possono richiedere hardware aggiuntivo. Usare Cortana per aprire le app, riavviare il dispositivo, cercare online e altro ancora. Gli sviluppatori possono anche scegliere di [integrare Cortana](https://dev.windows.com/cortana) nelle proprie esperienze.

È anche possibile usare i comandi vocali per spostarsi a casa. Ad esempio, puntare a un pulsante (usando lo [sguardo](gaze-and-commit.md) o un controller, a seconda del dispositivo) e pronunciare "Select". Altri comandi vocali includono "Go Home", "Bigger", "minor", "close" e "Face me".

## <a name="store-settings-and-system-apps"></a>Archiviazione, impostazioni e app di sistema

La realtà mista di Windows include diverse app predefinite, ad esempio:
* **Microsoft Store** per ottenere app e giochi
* **Hub di feedback** per inviare commenti e suggerimenti sulle app di sistema e di sistema
* **Impostazioni** per configurare le impostazioni di sistema (inclusi gli aggiornamenti di[rete](connecting-to-wi-fi-on-hololens.md) e di sistema)
* **Microsoft Edge** per esplorare siti Web
* **Foto** per visualizzare e condividere foto e video
* **Calibrazione** (solo HoloLens) per la modifica dell'esperienza HoloLens per l'utente corrente
* Apprendimento dei **movimenti** (HoloLens) o **apprendimento della realtà mista** (cuffie immersive) per informazioni sull'uso del dispositivo
* **Visualizzatore 3D** per decorare il mondo con contenuto di realtà mista
* **Portale per la realtà mista** (desktop) per la configurazione e la gestione dell'auricolare immersiva e la trasmissione di un'anteprima in tempo reale della visualizzazione nell'auricolare per poter vedere altri utenti.
* **Film e TV** per visualizzare i video di 360 e i film e i programmi televisivi più recenti
* **Cortana** per tutte le esigenze degli assistenti virtuali
* **Desktop** (auricolari immersivi) per la visualizzazione di monitor desktop in un auricolare immersivo
* **Esplora file** Accedere a file e cartelle che si trovano nel dispositivo

## <a name="see-also"></a>Vedi anche
* [Visualizzazioni delle app](app-views.md)
* [Controller del movimento](motion-controllers.md)
* [Accessori hardware](hardware-accessories.md)
* [Considerazioni relative all'ambiente per HoloLens](environment-considerations-for-hololens.md)
* [Implementazione di lanci di app 3D](implementing-3d-app-launchers.md)
* [Creazione di modelli 3D per l'utilizzo nella Home realtà mista di Windows](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)

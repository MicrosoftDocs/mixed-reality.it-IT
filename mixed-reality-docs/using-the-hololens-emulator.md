---
title: Usa l'emulatore di HoloLens
description: L'emulatore di HoloLens consente di testare le app di realtà mista sul PC senza un HoloLens fisico.
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, emulatore
ms.openlocfilehash: 3551bf48037f0cb7e8d243f2d89d43664e7c3475
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604100"
---
# <a name="using-the-hololens-emulator"></a>Usa l'emulatore di HoloLens

L'emulatore di HoloLens consente di testare le app holographic sul PC senza un HoloLens fisico e viene fornito con il set di strumenti di sviluppo di HoloLens. L'emulatore Usa una macchina virtuale Hyper-V. Gli input umani e dell'ambientali che verranno in genere letti dai sensori di HoloLens sono invece simulati usando la tastiera, mouse o controller Xbox. Le app non devono essere modificati per l'esecuzione nell'emulatore e non si conoscono che non sono in esecuzione su un reale HoloLens.

Se intende per sviluppare il App immersive (VR) visore VR realtà mista di Windows o giochi per PC desktop, consultare il [simulatore di realtà mista di Windows](using-the-windows-mixed-reality-simulator.md), che consente di simulare invece auricolari desktop.

> [!NOTE]
> Altre indicazioni specifiche su 2 HoloLens [presto](index.md#news-and-notes).

## <a name="installing-the-hololens-emulator"></a>Installazione dell'emulatore di HoloLens

Scaricare il [HoloLens (dal 1 ° generazione) emulatore e modelli di progetto holographic](https://go.microsoft.com/fwlink/?linkid=2065980).

È possibile trovare le compilazioni meno recenti dell'emulatore di HoloLens sul [archivio dell'emulatore HoloLens](hololens-emulator-archive.md) pagina.

### <a name="hololens-emulator-system-requirements"></a>Requisiti di sistema dell'emulatore di HoloLens

L'emulatore di HoloLens è basato su Hyper-V e Usa RemoteFx per la grafica con accelerazione hardware. Per usare l'emulatore, assicurarsi che il computer soddisfa questi requisiti hardware:
* 64-bit Windows 10 Pro, Enterprise o Education 
    >[!NOTE]
    >Windows 10 Home edition non supporta Hyper-V o l'emulatore di HoloLens
* CPU a 64 bit
* CPU 4 core (o più CPU con un totale di 4 core)
* 8 GB di RAM o superiore
* Nel BIOS, devono essere le seguenti funzionalità [supportato e abilitato](http://blogs.technet.com/b/iftekhar/archive/2010/08/09/enable-hardware-settings-in-bios-to-run-hyper-v.aspx):
   * Virtualizzazione basata su hardware
   * SLAT (Second Level Address Translation)
   * Protezione esecuzione programmi basata su hardware
* Requisiti di GPU (l'emulatore potrebbe funzionare con una GPU non supportata, ma sarà molto più lenta)
   * DirectX 11.0 e versioni successive
   * Driver WDDM 1.2 o versioni successive

Se il sistema soddisfi i requisiti precedenti, **, assicurarsi che la funzionalità "Hyper-V" sia stata abilitata nel sistema** tramite Pannello di controllo -> programmi -> programmi e funzionalità -> Attivazione delle funzionalità di Windows in o off -> verificare che sia selezionato "Hyper-V" per l'installazione dell'emulatore abbia esito positivo.

### <a name="installation-troubleshooting"></a>Risoluzione dei problemi di installazione

Si potrebbe essere visualizzato un errore durante l'installazione dell'emulatore che occorre *"Visual Studio 2015 Update 1 and UWP tools versione 1.2"*. Esistono tre possibili cause dell'errore:
* Non è una versione sufficientemente recente di Visual Studio (Visual Studio 2017 o Visual Studio 2015 Update 1 o versione successiva). Per risolvere il problema, installare la versione più recente di Visual Studio.
* È installata una versione sufficientemente recente di Visual Studio, ma non è installati gli strumenti di Universal Windows Platform (UWP). Si tratta di una funzionalità facoltativa di Visual Studio.

È inoltre possibile visualizzare un errore durante l'installazione dell'emulatore su un non-PRO e Enterprise/della formazione lo SKU di Windows o se non si è funzionalità Hyper-V abilitato.
* Leggi i [requisiti di sistema](#hololens-emulator-system-requirements) sezione precedente per un set completo di requisiti.
* Assicurarsi anche che funzionalità di Hyper-V è stata abilitata nel sistema.

## <a name="deploying-apps-to-the-hololens-emulator"></a>Distribuzione di App nell'emulatore di HoloLens

1. Carica la soluzione di app in Visual Studio 2015.
    >[!NOTE]
    >Quando si usa Unity, compilare il progetto di Unity e quindi caricare la soluzione compilata in Visual Studio come di consueto.
2. Verificare che la piattaforma è impostata su **x86**.
3. Selezionare il **emulatore HoloLens** come dispositivo di destinazione per il debug.
4. Passare a **Debug > Avvia debug** o premere **F5** per avviare l'emulatore e distribuire l'app per il debug.

L'emulatore può richiedere almeno un minuto per l'avvio al primo avvio. È consigliabile mantenere l'emulatore aperto durante la sessione di debug in modo che è possibile distribuire rapidamente le app nell'emulatore in esecuzione.

## <a name="basic-emulator-input"></a>Input di base dell'emulatore

Controllo dell'emulatore è molto simile a molti comuni videogiochi 3D. Sono disponibili opzioni di input usando la tastiera, mouse o controller Xbox. Per controllare l'emulatore, indirizzando le operazioni eseguite da un utente simulato che portano un HoloLens. Le azioni di spostamento che rispondono utente simulato intorno e le App in esecuzione nell'emulatore come si farebbe in un dispositivo reale.
* **Scorrere in avanti, indietro, a sinistra e destra** -W, usare le chiavi A, S e D su tastiera, oppure la levetta sinistra in un controller Xbox.
* **Cercare, in basso a sinistra e con il pulsante destro** -fare clic e trascinare il mouse, usare i tasti freccia su tastiera, oppure la levetta destra in un controller Xbox.
* **Aria gesto tocco** : fare doppio clic del mouse, premere il tasto INVIO sulla tastiera o usare il pulsante in un controller Xbox.
* **Ha detto movimento** : premere il tasto Windows o F2 sulla tastiera o fare clic sul pulsante B in un controller Xbox.
* **Movimento di scorrimento a mano** : tenere premuto il tasto Alt, tenere premuto il pulsante destro del mouse e trascinare il puntatore del mouse su / giù, o in un controller Xbox premuto un pulsante e il trigger a destra e spostarsi su e giù sulla destra stick.

## <a name="anatomy-of-the-hololens-emulator"></a>Composizione dell'emulatore di HoloLens

### <a name="main-window"></a>Finestra principale

Quando viene avviata nell'emulatore, si verrà visualizzata una finestra che visualizza il sistema operativo HoloLens.

![Finestra principale dell'emulatore di HoloLens](images/emulator-890px.png)

### <a name="toolbar"></a>Barra degli strumenti

A destra della finestra principale, si noterà la barra degli strumenti dell'emulatore. Barra degli strumenti contiene i pulsanti seguenti:
* ![Icona di chiusura](images/emulator-close.png) **Chiudi**: Chiude l'emulatore.
* ![Icona di riduzione a icona](images/emulator-minimize.png) **Riduci a icona**: Riduce a icona la finestra dell'emulatore.
* ![Icona input umano](images/emulator-control.png) **umana Input**: Tastiera e mouse consente di simulare umano [di input per l'emulatore](#basic-emulator-input).
* ![Icona di input da tastiera e mouse](images/emulator-input.png) **Input di Mouse e tastiera**: Tastiera e mouse di input vengono passati direttamente al sistema operativo di HoloLens come eventi di mouse e tastiera come se si è connessi una tastiera Bluetooth e un mouse.
* ![Icona adatta allo schermo](images/emulator-fit.png) **adatta allo schermo**: È appropriato per l'emulatore allo schermo.
* ![Icona dello zoom](images/emulator-zoom.png) **Zoom**: Verificare l'emulatore maggiori e minori.
* ![Icona della Guida](images/emulator-help.png) **aiutare**: Aprire la Guida dell'emulatore.
* ![Icona del portale di dispositivo: apertura](images/emulator-deviceportal.png) **aprire il portale di dispositivo**: Aprire il Windows Device Portal per il sistema operativo HoloLens nell'emulatore.
* ![Icona Tools](images/emulator-tools.png) **strumenti**: Aprire il **strumenti aggiuntivi** riquadro.

### <a name="simulation-tab"></a>Scheda di simulazione

La scheda predefinita all'interno di **strumenti aggiuntivi** riquadro è la **simulazione** scheda.

![Riquadro "Strumenti aggiuntivi" emulatore di HoloLens](images/emulator-simulation-500px.png)

La scheda di simulazione Mostra lo stato corrente dei sensori simulati utilizzato per guidare il sistema operativo HoloLens all'interno dell'emulatore. Posizionare il mouse su qualsiasi valore nella scheda della simulazione fornirà una descrizione comando che descrive come controllare tale valore.

### <a name="room-tab"></a>Scheda chat room

L'emulatore simula input world sotto forma di mesh mapping spaziale da simulato "locali". Questa scheda consente di scegliere quale spazio sufficiente per caricare invece la chat room predefinita.

![Scheda 'Locali' emulatore HoloLens](images/emulator-room-500px.png)

Le chat simulate sono utili per testare l'app in più ambienti. Le chat diversi vengono fornite con l'emulatore e dopo aver installato l'emulazione, questi avvisi sono disponibili nella cartella % ProgramFiles(x86) %\Program file (x86) \Microsoft XDE\10.0.11082.0\Plugins\Rooms. Tutte queste chat sono state acquisite in ambienti reali usando un HoloLens:
* **DefaultRoom.xef** -un salotto piccole con un televisore, la tabella di caffè e due divani. Caricato per impostazione predefinita quando si avvia l'emulatore.
* **Bedroom1.xef** -una piccola locali con un tecnico.
* **Bedroom2.xef** -un locali con un ambiente di dimensioni regina, cassettiera, nightstands e armadio entrare.
* **GreatRoom.xef** -una stanza di eccezionali grande spazio aperto con domestico, ristorante tabelle e di cucina.
* **LivingRoom.xef** : un salotto con un fireplace, divano, armchairs e un tabella caffè con un vaso.

È anche possibile registrare i proprio locali da usare nell'emulatore tramite la pagina di simulazione del [Windows Device Portal](using-the-windows-device-portal.md) di HoloLens.

Nell'emulatore, viene visualizzata solo vntana che si esegue il rendering e non verrà visualizzata la chat simulata dietro il vntana. Ciò viene a differenza di HoloLens reali in cui vengono visualizzate entrambe fusa insieme. Se si desidera visualizzare le chat room simulate nell'emulatore di HoloLens, è necessario aggiornare l'app per eseguire il rendering mesh mapping spaziale nella scena.

### <a name="account-tab"></a>Scheda Account

Scheda Account consente di configurare l'emulatore di effettuare l'accesso con un Account Microsoft. Ciò è utile per il test dell'API che richiedono all'utente di essere eseguito l'accesso aggiuntivo con un account. Dopo avere selezionato la casella in questa pagina, gli avvii successivi dell'emulatore verranno richiesto di accesso, come si farebbe la prima volta che viene avviato il HoloLens.

## <a name="see-also"></a>Vedere anche
* [Input avanzati emulatore HoloLens e il simulatore di realtà mista](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [Cronologia di HoloLens emulatore software](hololens-emulator-archive.md)
* [Mapping spaziale in Unity](spatial-mapping-in-unity.md)
* [Mapping spaziale DirectX](spatial-mapping-in-directx.md)

---
title: Input avanzati emulatore HoloLens e il simulatore di realtà mista
description: Istruzioni dettagliate per usare la tastiera, mouse e controller Xbox per simulare l'input per il simulatore emulatore HoloLens e realtà mista di Windows.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/26/2019
ms.topic: article
keywords: HoloLens, emulatore, simulazione, realtà mista di Windows
ms.openlocfilehash: 6ea493d8c1269ff0bea1d4102b9e224e30d06aef
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/28/2019
ms.locfileid: "64580587"
---
# <a name="advanced-hololens-emulator-and-mixed-reality-simulator-input"></a>Input avanzati emulatore HoloLens e il simulatore di realtà mista

La maggior parte degli utenti emulatore saranno sufficiente utilizzare i controlli di input di base per il [HoloLens emulatore](using-the-hololens-emulator.md#basic-emulator-input) o il [simulatore di realtà mista di Windows](using-the-windows-mixed-reality-simulator.md#basic-simulator-input). Dettaglio di seguito è per gli utenti esperti che hanno trovato una necessità per simulare i tipi più complessi di input.


## <a name="concepts"></a>Concetti

Per iniziare a usare il controllo di input virtuale per il simulatore emulatore HoloLens e realtà mista di Windows, è necessario innanzitutto comprendere alcuni concetti.

Il movimento si intende controllare e modificare la posizione e l'orientamento di un elemento nella scena. Per un oggetto controllabile mirato, movimento è controllato con rotazione e traslazione lungo i tre assi.
* **Rotazione**: TURN verso sinistra o destra.
* **Passo**: Ruotare verso l'alto o verso il basso.
* **Eseguire il rollback**: Eseguire il rollforward parallelo per.
* **X**: Lo spostamento verso sinistra o destra.
* **Y**: Spostare verso l'alto o verso il basso.
* **Z**: Sposta in avanti o indietro.

[Movimento](gestures.md) e movimento controller input sono mappate da vicino al modo in cui sono dispositivi fisici:
* **Azione**: Ciò consente di simulare l'azione di premendo il dito indice per il controllo thumb o il pull di pulsante di azione in un controller. Ad esempio, l'input dell'azione è utilizzabile per simulare il movimento indice puntato, di scorrere il contenuto e a premere e tenere premuto.
* **[Bloom](gestures.md#bloom)movimento /System. o Home**: Il movimento di sistema/bloom HoloLens o un pulsante Home del controller viene usato per restituire immediatamente l'ed eseguire azioni di sistema.

Le mani hanno un reprresentation avanzati in HoloLens 2.  Oltre a essere rilevate/non rilevati e utilizzabili per movimenti determinanti, mani dispongono di un modello scheletro articolati e adattarsi a essi ed esposte allo sviluppatore.  Questo introduce 26 punti rilevati ogni lato.  
* **Joint**: Una delle posizioni rilevate venti per una determinata mano rilevata. Questo avrà un punto è associato uno spazio 3d.
* **Rappresentare**: Una raccolta completa di tutte le giunzioni in una mano rilevata. A questo punto, si tratta di una raccolta di 26 giunti. 

A questo punto, non è esposto un controllo diretto di ciascuna posizione joint singolarmente tramite l'interfaccia utente dell'emulatore, anche se è possibile impostarlo tramite l'API di simulazione. Piuttosto, abbiamo una serie di utili pose rappresentativi che l'emulatore consente di alternare tra.

È inoltre possibile controllare lo stato dell'input di sensori simulati:
* **Reimpostare**: Tutti i sensori simulati restituirà i valori predefiniti.  Iniziando con l'emulatore di 2 HoloLens, una reimpostazione può essere limitata a una o entrambe le mani, coinvolgendo il hand(s) desiderato usando il modificatore appropriato chiavi o aziona (a sinistra e/o Alt destro o paraurti sinistro e/o a destra nel gamepad).
* **Rilevamento**: Scorre le modalità di rilevamento posizionale. È possibile creare, ad esempio:
  * **Predefinito**: Il sistema operativo sceglie la modalità di rilevamento migliore in base alle richieste effettuate del sistema.
   * **Orientamento**: Forza l'orientamento sola rilevamento, indipendentemente dal fatto le richieste effettuate del sistema.
   * **Posizionali**: Rilevamento di posizionali forza, indipendentemente dal fatto le richieste effettuate del sistema.

## <a name="types-of-input"></a>Tipi di input

Nella tabella seguente viene mostrato come ogni tipo di input viene mappato a controller Xbox, tastiera e mouse. Ogni tipo ha un mapping diversi a seconda della modalità di controllo di input; ulteriori informazioni sulle modalità di controllo di input viene fornite più avanti in questo documento.

|  |  Tastiera |  Mouse |  Controller Xbox | 
|----------|----------|----------|----------|
|  Yaw |  Frecce sinistra / destra |  Trascinare verso sinistra / destra |  A destra thumbstick sinistro o destro | 
|  Angolazione |  PGSU / PGGIÙ frecce |  Trascinare su / giù |  A destra thumbstick su / giù | 
|  Roll |  Q / E |  |  Tasto direzionale sinistra / destra | 
|  x |  OGGETTO / 1!D |  |  Thumbstick sinistro a sinistra / destra | 
|  Y |  PGSU / PGGIÙ |  |  Tasto direzionale su / giù | 
|  Z |  W / S |  |  Thumbstick sinistro su / giù | 
|  Azione |  Invio o barra spaziatrice |  Pulsante destro del mouse |  Un pulsante o entrambi trigger | 
|  Sistema/Bloom |  Tasto F2 o Windows |  |  Pulsante B | 
|  Pulsante di triangolo di ridimensionamento controller |  G  |  |  | 
|  Pulsante di menu controller |  M  |  |  | 
|  Tocco touchpad controller |  U  |  |  | 
|  Premere touchpad controller |  P  |  |  | 
|  Premere thumbstick controller |  K  |  |  | 
|  Controller a sinistra di tenere traccia dello stato |  F9 |  |  | 
|  Controller a destra di tenere traccia dello stato |  F10 |  |  | 
|  Posa "Chiudi" mano | 7 |  |  |
|  Passare 'Open' posa (impostazione predefinita) | 8 |  |  |
|  Mano "Punta" posa | 9 |  |  |
|  Mano 'Indietro' posa | 0 |  |  |
|  Reimposta |  Tasto ESC |  |  pulsante Start | 
|  Rilevamento |  T o F3 |  |  Pulsante X | 


Nota: I pulsanti di controller possono essere per il targeting una mano/controller o l'altro che usa l'icona della mano targeting modificatori.

## <a name="targeting"></a>Selezione della destinazione 

Alcuni di questi concetti inpui siedi sulle proprie.  Azione, sistema/Bloom, la reimpostazione della e rilevamento sono concetti completati, non è necessario e non sono interessati da, tutti i modificatori di aggiuntivi per specificare come destinazione.  Tuttavia, i concetti rimanenti è applicabile a uno dei più destinazioni. È stata introdotta modi specificare che eseguirà il comando deve essere applicato a destinazione.  In tutti i casi, è possibile specificare tramite l'interfaccia utente o le pressioni di tasti, oggetto targtet.  In alcuni casi, è anche possibile specificare direttamente con il controller xbox. 

Nella tabella seguente vengono descritte le opzioni per la destinazione e il modo per attivare ognuno di essi.

| Object | Tasto di modifica | Modificatore controller | Modificatore dell'interfaccia utente dell'emulatore |
|----------|----------|----------|----------|
| Body | (predefinito) | (predefinito) | (predefinito) |
| Head | Tenere premuto H | (Non disponibile) | (Non disponibile) |
| A sinistra/Controller | Tenere premuto Alt di sinistra pulsante | Tenere premuto il pulsante sinistro interno di una sessione | Simbolo a sinistra | 
| A destra/Controller | Tenere premuto Alt destro | Tenere premuto il pulsante destro interno di una sessione | A destra puntina da disegno |
| Occhi | Tenere premuto Y | (Non disponibile) | Occhi a puntina da disegno |
  
La tabella seguente illustra come ogni modificatore di destinazione esegue il mapping di ogni input concetti lo spostamento dei

|  | Predefinito (corpo) |  Mano/controller (tenere premuto Alt, tenere premuto il pulsante shoulder gamepad o puntina da disegno dell'interfaccia utente attiva/disattiva) |  Head (tenere premuto H)  |  Occhi (tenere premuto Y o Attiva/Disattiva interfaccia utente puntina da disegno) |
|----------|----------|----------|----------|
|  Yaw |  Attivare corpo a sinistra / destra |  Mano di spostamento a sinistra / destra |  Attivare head sinistra / destra | Sguardo occhio è simile a sinistra/destra |
|  Angolazione |  Attivare head su / giù |  Spostare manualmente su / giù |  Attivare head su / giù | Sguardo occhio Cerca su/giù | 
|  Roll |  Esegue il rollup head sinistra / destra |  |  Esegue il rollup head sinistra / destra | (Nessuna azione) |
|  x |  Diapositiva corpo a sinistra / destra |  Spostare manualmente/controller a sinistra / destra |  Attivare head sinistra / destra | (Nessuna azione) |
|  Y |  Spostamento del corpo su / giù |  Spostare manualmente/controller su / giù |  Attivare head su / giù | (Nessuna azione) |
|  Z |  Spostare corpo avanti / indietro |  Spostamento manuale/controller avanti / indietro |  Attivare head su / giù | (Nessuna azione) |
 
 
## <a name="controlling-an-app"></a>Controllo di un'app

Per l'uso quotidiano viene suggerito il seguente set di controlli:

|  Operazione |  Tastiera e mouse |  Controller | 
|----------|----------|----------|
|  Corpo X |  OGGETTO / 1!D |  Thumbstick sinistro a sinistra / destra | 
|  Corpo Y |  PGSU / PGGIÙ |  Tasto direzionale su / giù | 
|  Corpo Z |  W / S |  Thumbstick sinistro su / giù | 
|  Rotazione di corpo |  Trascinare il mouse a sinistra / destra |  A destra thumbstick sinistro o destro | 
|  Rotazione head |  H + trascinamento del mouse a sinistra / destra |  H (sulla tastiera) + levetta destra a sinistra / destra | 
|  Passo head |  Trascinare il mouse su / giù |  A destra thumbstick su / giù | 
|  Esegue il rollup head |  Q / E |  Tasto direzionale sinistra / destra | 
|  Mano/Controller X |  ALT + A / 1!d |  Shoulder + thumbstick sinistro a sinistra / destra | 
|  Mano/Controller Y |  ALT + PGSU PGSU / PGGIÙ |  Shoulder + tasto direzionale su / giù | 
|  Mano/Controller Z |  ALT + L / S |  Shoulder + thumbstick sinistro su / giù | 
|  Rotazione manuale/Controller |  Alt + trascinamento del mouse a sinistra / destra |  Shoulder + levetta destra a sinistra / destra | 
|  Passo manualmente/Controller |  Alt + trascinamento del mouse su / giù |  Shoulder + levetta destra su / giù | 
|  Esegue il rollup disponibilità/Controller |  ALT + Q / E |  Shoulder + tasto direzionale sinistra / destra | 
|  Azione |  Pulsante destro del mouse |  Trigger | 
|  Bloom / sistema / Home |  Tasto F2 o Windows |  Pulsante B | 
|  Reimposta |  ESC |  pulsante Start | 
|  Rilevamento |  T |  Pulsante X | 
|  Scorrimento |  ALT + destra del pulsante del mouse e trascina il mouse su / giù |  Shoulder + trigger + levetta destra su / giù | 
|  Spostamento/ruotare più velocemente | Tasto MAIUSC destro o sinistro | Premere e tenere premuto il thumbstick a destra |
|  Ruota/spostamento lento | Tasto Ctrl destro o sinistro | Premere e tenere premuto il thumbstick sinistro |

## <a name="perception-simulation-control-panel-keyboard-shortcuts"></a>Tasti di scelta rapida di percezione simulazione del Pannello di controllo

I seguenti tasti di scelta rapida sono disponibili per l'apertura del Pannello di controllo di simulazione di percezione e abilitare o disabilitare i dispositivi di input PC per usano con simulazione.

| Operazione | Tasti di scelta rapida | Descrizione/note |
|-----------|----------|-------------|
| Attiva/Disattiva 'Usa della tastiera per la simulazione' | F4 | Se disattivato, gli input da tastiera passa all'applicazione HoloLens o realtà mista di Windows. |
| Attiva/Disattiva 'Usa il mouse per la simulazione' | F5 | Se disattivato, input del mouse va all'ambiente di realtà mista (realtà mista di Windows solo) |
| Attiva/Disattiva 'Usa gamepad simulazione' | F6 | Se disattivato, gamepad input viene ignorato dal simulazione |
| Mostrare o nascondere il pannello di controllo | F7 | |
| Impostare lo stato attivo della tastiera al pannello di controllo | F8 | Se il pannello non è attualmente visibile verrà visualizzato come prima. |
| Ancorati o disancorati il pannello da e verso l'emulatore o finestra del portale di realtà mista | F9 | Se la finestra viene chiusa quando è disinserito, è ancorata e nascosta. |

## <a name="see-also"></a>Vedere anche
* [Installare gli strumenti](install-the-tools.md)
* [Uso dell'emulatore HoloLens](using-the-hololens-emulator.md)
* [Uso del simulatore di Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md)

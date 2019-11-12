---
title: Advanced HoloLens Emulator and Mixed Reality Simulator input
description: Istruzioni dettagliate per l'uso di tastiera, mouse e controller Xbox per simulare l'input per l'emulatore di HoloLens e il simulatore di realtà mista di Windows.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/26/2019
ms.topic: article
keywords: HoloLens, emulatore, simulazione, realtà mista di Windows
ms.openlocfilehash: c5601ae2caf235cb22248ce7c6bf7e29225ade2c
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926601"
---
# <a name="advanced-hololens-emulator-and-mixed-reality-simulator-input"></a>Advanced HoloLens Emulator and Mixed Reality Simulator input

La maggior parte degli utenti dell'emulatore dovrà usare solo i controlli di input di base per l' [emulatore HoloLens](using-the-hololens-emulator.md#basic-emulator-input) o il [simulatore di realtà mista di Windows](using-the-windows-mixed-reality-simulator.md#basic-simulator-input). I dettagli seguenti sono destinati agli utenti avanzati che hanno dovuto simulare tipi di input più complessi.


## <a name="concepts"></a>Concetti

Per iniziare a controllare l'input virtuale per l'emulatore di HoloLens e il simulatore di realtà mista di Windows, è prima necessario comprendere alcuni concetti.

Per movimento si intende il controllo e la modifica della posizione e dell'orientamento di qualcosa nella scena. Per un oggetto controllabile di destinazione, il movimento è controllato sia dalla rotazione che dalla conversione (spostamento) lungo tre assi.
* **Imbardata**: ruotare verso sinistra o verso destra.
* **Pitch**: attiva o disattiva.
* **Roll**: roll affiancato.
* **X**: sposta a sinistra o a destra.
* **Y**: spostarsi verso l'alto o verso il basso.
* **Z**: spostarsi avanti o indietro.

L'input del controller movimento e movimento viene mappato in modo accurato al modo in cui i dispositivi fisici:
* **Azione**: consente di simulare l'azione di premere l'indice sul pollice o di estrarre il pulsante di azione in un controller. Ad esempio, l'input dell'azione può essere usato per simulare il gesto di tocco aereo, scorrere il contenuto e premere e tenere premuto.
* **Movimento di [Bloom](system-gesture.md#bloom)/System o Home**: il movimento HoloLens Bloom/System o il pulsante Home del controller viene usato per tornare alla shell e per eseguire le azioni di sistema.

Le mani hanno una rappresentazione avanzata in HoloLens 2.  Oltre a essere monitorati/non rilevati e utilizzabili per la guida dei movimenti, le mani hanno ora un modello di ossatura articolato adattabile ed esposto allo sviluppatore.  Questo introduce 26 punti di rilevamento in ogni mano.  
* **Joint**: una delle venti posizioni registrate per una determinata mano rilevata. Questo sarà un punto in cui è associato lo spazio 3D.
* **Pose**: raccolta completa di tutte le giunzioni in una mano rilevata. A questo punto, si tratta di una raccolta di 26 giunzioni. 

Attualmente, il controllo diretto di ogni posizione congiunta non viene esposto singolarmente tramite l'interfaccia utente dell'emulatore, sebbene sia possibile impostarli tramite l'API di simulazione. Piuttosto, abbiamo un set di rappresentazioni utili che l'emulatore consente di passare da una all'altra.

È anche possibile controllare lo stato dell'input del sensore simulato:
* **Reset**: restituirà tutti i sensori simulati ai valori predefiniti.  A partire dall'emulatore HoloLens 2, è possibile definire l'ambito di una reimpostazione a una o entrambe le lancette usando le lancette desiderate usando i tasti di modifica appropriati o i pulsanti (Alt a sinistra e/o a destra o il paraurti sinistro e/o destro).
* **Rilevamento**: scorre le modalità di rilevamento posizionale. È possibile creare, ad esempio:
  * **Impostazione predefinita**: il sistema operativo sceglie la modalità di rilevamento migliore in base alle richieste effettuate dal sistema.
   * **Orientation**: impone il rilevamento solo dell'orientamento, indipendentemente dalle richieste effettuate dal sistema.
   * **Posizionale**: forza il rilevamento posizionale, indipendentemente dalle richieste effettuate dal sistema.

## <a name="types-of-input"></a>Tipi di input

Nella tabella seguente viene illustrato come viene eseguito il mapping di ogni tipo di input con la tastiera, il mouse e il controller Xbox. Ogni tipo ha un mapping diverso a seconda della modalità di controllo dell'input. Altre informazioni sulle modalità di controllo di input sono disponibili più avanti in questo documento.

|  |  Tastiera |  Mouse |  Controller Xbox | 
|----------|----------|----------|----------|
|  Yaw |  Frecce sinistra/destra |  Trascinare verso sinistra/destra |  Destra levetta sinistra/destra | 
|  Pitch |  Frecce su/giù |  Trascina su/giù |  Levetta a destra | 
|  Roll |  DOMANDE E RISPOSTE |  |  DPad a sinistra/destra | 
|  X |  A/D |  |  Sinistra levetta sinistra/destra | 
|  Y |  PGSU/PGGIÙ |  |  DPad | 
|  Z |  W/S |  |  Levetta verso l'alto o verso il basso | 
|  Azione |  Immettere o spazio |  Pulsante destro |  Un pulsante o uno o più trigger | 
|  Bloom/sistema |  Tasto F2 o Windows |  |  Pulsante B | 
|  Pulsante grip controller |  G  |  |  | 
|  Pulsante di menu controller |  M  |  |  | 
|  Tocco touchpad del controller |  U  |  |  | 
|  Pressione del touchpad del controller |  P  |  |  | 
|  Pressione del controller levetta |  K  |  |  | 
|  Stato di rilevamento del controller sinistro |  F9 |  |  | 
|  Stato di rilevamento del controller destro |  F10 |  |  | 
|  Pose "close" della mano | 7 |  |  |
|  "Apertura" della mano (impostazione predefinita) | 8 |  |  |
|  Posizione "punto" della mano | 9 |  |  |
|  Pose "Pinch" della mano | 0 |  |  |
|  Reimposta |  Chiave di escape |  |  pulsante Start | 
|  Tracking |  T o F3 |  |  Pulsante X | 


Nota: i pulsanti del controller possono essere assegnati a una mano/controller o all'altro usando i modificatori di destinazione.

## <a name="targeting"></a>Selezione della destinazione 

Alcuni dei concetti di input precedenti si basano su se stessi.  Action, Bloom/System, reset e tracking sono concetti completi, non sono necessari e non sono interessati da alcun modificatore aggiuntivo per la destinazione.  Tuttavia, i concetti rimanenti possono essere applicati a una di più destinazioni. Sono stati introdotti modi per specificare la destinazione prevista a cui applicare il comando.  In tutti i casi, è possibile specificare tramite l'interfaccia utente o tramite i tasti di scelta rapida, l'oggetto di destinazione.  In alcuni casi, è anche possibile specificare direttamente con il controller Xbox. 

Nella tabella seguente vengono descritte le opzioni per la destinazione e la modalità di attivazione di ognuna di esse.

| Oggetto | Modificatore di tastiera | Modificatore controller | Modificatore dell'interfaccia utente dell'emulatore |
|----------|----------|----------|----------|
| Corpo | (impostazione predefinita) | (impostazione predefinita) | (impostazione predefinita) |
| Head | Mantieni H | (Non disponibile) | (Non disponibile) |
| Mano sinistra/controller | Pulsante Alt sinistro | Pulsante Mantieni la spalla sinistra | Puntina da disegno a sinistra | 
| Mano destra/controller | Pulsante ALT destro | Pulsante destro della spalla | Puntina da disegno a destra |
| Occhi | Mantieni Y | (Non disponibile) | Puntina da disegno |
  
La tabella seguente illustra in che modo ogni modificatore di destinazione esegue il mapping di ognuno dei concetti di base di input Movement

|  | Predefinito (corpo) |  Mano/controller (tenendo premuto ALT, tenendo premuto il pulsante della spalla del gamepad o impostando la puntina da disegno dell'interfaccia utente) |  Head (tenendo H)  |  Occhi (Mantieni Y o imposta puntina da disegno dell'interfaccia utente) |
|----------|----------|----------|----------|
|  Yaw |  Trasforma corpo a sinistra/a destra |  Sposta mano sinistra/destra |  Trasforma la testa a sinistra/destra | Sguardi occhi a sinistra/destra |
|  Pitch |  Attiva/disattiva intestazione |  Spostare la mano verso l'alto o verso il basso |  Attiva/disattiva intestazione | Sguardi occhi in alto/in basso | 
|  Roll |  Roll Head verso sinistra/destra |  |  Roll Head verso sinistra/destra | (Nessuna azione) |
|  X |  Diapositiva corpo sinistro/destro |  Spostare la mano/il controller a sinistra/destra |  Trasforma la testa a sinistra/destra | (Nessuna azione) |
|  Y |  Sposta il corpo verso l'alto o verso il basso |  Spostare la mano/il controller verso l'alto/il basso |  Attiva/disattiva intestazione | (Nessuna azione) |
|  Z |  Sposta il corpo avanti/indietro |  Spostare la mano/il controller avanti/indietro |  Attiva/disattiva intestazione | (Nessuna azione) |
 
 
## <a name="controlling-an-app"></a>Controllo di un'app

Il set di controlli seguente è consigliato per l'utilizzo giornaliero:

|  Operazione |  Tastiera e mouse |  Titolare del trattamento | 
|----------|----------|----------|
|  Corpo X |  A/D |  Sinistra levetta sinistra/destra | 
|  Corpo Y |  PGSU/PGGIÙ |  DPad | 
|  Corpo Z |  W/S |  Levetta verso l'alto o verso il basso | 
|  Imbardata corpo |  Trascinare il mouse verso sinistra/destra |  Destra levetta sinistra/destra | 
|  Imbardata Head |  H + trascina il mouse verso sinistra/destra |  H (sulla tastiera) + destra levetta a sinistra/destra | 
|  Passo Head |  Trascinare il mouse verso l'alto o verso il basso |  Levetta a destra | 
|  Head roll |  DOMANDE E RISPOSTE |  DPad a sinistra/destra | 
|  Mano/controller X |  ALT + A/D |  Spalla + sinistra levetta sinistra/destra | 
|  Mano/controller Y |  ALT + PGSU/PGGIÙ |  Spalla + DPad su/giù | 
|  Mano/controller Z |  ALT + W/S |  Levetta di spalla + sinistra | 
|  Imbardata mano/controller |  Alt + trascinamento del mouse verso sinistra/destra |  Spalla + destra levetta sinistra/destra | 
|  Passo controller/mano |  Alt + trascina il mouse verso l'alto/il basso |  Spalla + levetta a destra | 
|  Rullo della mano/controller |  ALT + Q/E |  Spalla + DPad a sinistra/destra | 
|  Azione |  Pulsante destro del mouse |  Trigger | 
|  Bloom/System/Home |  Tasto F2 o Windows |  Pulsante B | 
|  Reimposta |  ESC |  pulsante Start | 
|  Tracking |  T |  Pulsante X | 
|  Scorrimento |  ALT + pulsante destro del mouse + trascina il mouse verso l'alto/il basso |  Spalla + trigger + levetta destro/giù | 
|  Spostamento/rotazione più veloce | Tasto MAIUSC sinistro o destro | Premere e tenere premuto il levetta destro |
|  Spostamento/rotazione lenta | Tasto CTRL sinistro o destro | Premere e tenere premuto il levetta a sinistra |

## <a name="perception-simulation-control-panel-keyboard-shortcuts"></a>Tasti di scelta rapida della simulazione della percezione del pannello di controllo

I tasti di scelta rapida seguenti sono disponibili per l'accesso al pannello di controllo della simulazione di percezione e l'abilitazione o la disabilitazione dei dispositivi di input PC per l'uso con simulazione.

| Operazione | Tasti di scelta rapida | Descrizione/Note |
|-----------|----------|-------------|
| Imposta/Nascondi ' utilizza tastiera per simulazione ' | F4 | Quando è disattivato, l'input da tastiera passa all'applicazione HoloLens o a realtà mista di Windows. |
| Imposta/Nascondi ' USA mouse per simulazione ' | F5 | Quando è disattivato, l'input del mouse passa all'ambiente di realtà mista (solo per realtà mista di Windows) |
| Imposta/Nascondi ' USA Gamepad per la simulazione ' | F6 | Quando è disattivato, l'input del gamepad viene ignorato dalla simulazione |
| Mostrare o nascondere il pannello di controllo | F7 | |
| Impostare lo stato attivo della tastiera sul pannello di controllo | F8 | Se il pannello non è attualmente visibile, verrà visualizzato per primo. |
| Ancorare o disancorare il pannello da/verso la finestra del portale dell'emulatore o della realtà mista | F9 | Se la finestra viene chiusa quando non ancorata, è ancorata e nascosta. |

## <a name="see-also"></a>Vedi anche
* [Installare gli strumenti](install-the-tools.md)
* [Uso dell'emulatore HoloLens](using-the-hololens-emulator.md)
* [Uso del simulatore di Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md)

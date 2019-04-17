---
title: Input avanzati emulatore HoloLens e il simulatore di realtà mista
description: Istruzioni dettagliate per usare la tastiera, mouse e controller X predefinite per simulare l'input per l'emulatore di HoloLens e il simulatore di realtà mista di Windows.
author: ChimeraScorn
ms.author: cwhite
ms.date: 02/24/2018
ms.topic: article
keywords: HoloLens, emulatore, simulazione, realtà mista di Windows
ms.openlocfilehash: 59bea340a2ecdd2d65481c9ace4ab3f0bf15bc6f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597852"
---
# <a name="advanced-hololens-emulator-and-mixed-reality-simulator-input"></a>Input avanzati emulatore HoloLens e il simulatore di realtà mista

La maggior parte degli utenti emulatore saranno sufficiente utilizzare i controlli di input di base per il [HoloLens emulatore](using-the-hololens-emulator.md#basic-emulator-input) o il [simulatore di realtà mista di Windows](using-the-windows-mixed-reality-simulator.md#basic-simulator-input). Dettaglio di seguito è per gli utenti esperti che hanno trovato una necessità per simulare i tipi più complessi di input.

> [!NOTE]
> Altre indicazioni specifiche su 2 HoloLens [presto](index.md#news-and-notes).

## <a name="concepts"></a>Concetti

Per iniziare a usare il controllo di input virtuale per l'emulatore di HoloLens e il simulatore di realtà mista di Windows, è necessario innanzitutto comprendere alcuni concetti.

Il movimento si intende controllare e modificare la posizione e l'orientamento di un elemento nella scena. Per un oggetto controllabile mirato, movimento è controllato con rotazione e traslazione lungo i tre assi.
* **Rotazione**: TURN verso sinistra o destra.
* **Passo**: Ruotare verso l'alto o verso il basso.
* **Eseguire il rollback**: Eseguire il rollforward parallelo per.
* **X**: Lo spostamento verso sinistra o destra.
* **Y**: Spostare verso l'alto o verso il basso.
* **Z**: Sposta in avanti o indietro.

[Movimento](gestures.md) e movimento controller input sono mappate da vicino al modo in cui sono dispositivi fisici:
* **Azione**: Ciò consente di simulare l'azione di premendo il dito indice per il controllo thumb o il pull di pulsante di azione in un controller. Ad esempio, l'input dell'azione è utilizzabile per simulare il movimento indice puntato, di scorrere il contenuto e a premere e tenere premuto.
* **[Bloom](gestures.md#bloom) o Home**: Pulsante Home del controller viene utilizzato per restituire immediatamente l'ed eseguire azioni di sistema o di HoloLens ha detto movimento.

Le mani hanno un reprresentation avanzati in HoloLens V2.  Oltre a essere rilevate/non rilevati e utilizzabili per movimenti determinanti, mani dispongono di un modello scheletro articolati e adattarsi a essi ed esposte allo sviluppatore.  Questo introduce 20 punti rilevati ogni lato.  
* **Joint**: Una delle posizioni rilevate venti per una determinata mano rilevata. Questo avrà un punto è associato uno spazio 3d.
* **Rappresentare**: Una raccolta completa di tutte le giunzioni in una mano rilevata. A questo punto, si tratta di una raccolta di 20 giunti. 

In questo momento, non è esposto un controllo diretto di ciascuna posizione joint singolarmente tramite l'interfaccia utente dell'emulatore. Tuttavia è possibile impostarlo tramite l'API di simulazione. Piuttosto, abbiamo una serie di utili pose rappresentativi che l'emulatore consente di alternare tra.

È inoltre possibile controllare lo stato dell'input di sensori simulati:
* **Reimpostare**: Tutti i sensori simulati restituirà i valori predefiniti.
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
|  Bloom |  Tasto F2 o Windows (chiave di Windows funziona solo con l'emulatore di HoloLens) |  |  Pulsante B | 
|  Pulsante di triangolo di ridimensionamento controller |  G (realtà mista di Windows simulator-only) |  |  | 
|  Pulsante di menu controller |  M (realtà mista di Windows simulator-only) |  |  | 
|  Tocco touchpad controller |  U (realtà mista di Windows simulator-only) |  |  | 
|  Premere touchpad controller |  P (realtà mista di Windows simulator-only) |  |  | 
|  Set di disponibilità posa | 7, 8, 9 o 0 |  |  |
|  Reimposta |  Tasto ESC |  |  pulsante Start | 
|  Rilevamento |  T o F3 |  |  Pulsante X | 


Nota: Nel simulatore solo di realtà mista di Windows, i pulsanti di controller possono essere assegnato a un lato o l'altro che usa l'icona della mano targeting modificatori.

## <a name="targeting"></a>Selezione della destinazione 

Alcuni di questi concetti inpui siedi sulle proprie.  Azione, Bloom, la reimpostazione della e rilevamento sono concetti completati, non è necessario e non sono interessati da, tutti i modificatori di aggiuntivi per specificare come destinazione.  Tuttavia, i concetti rimanenti è applicabile a uno dei più destinazioni. È stata introdotta modi specificare che eseguirà il comando deve essere applicato a destinazione.  In tutti i casi, è possibile specificare tramite l'interfaccia utente o le pressioni di tasti, oggetto targtet.  In alcuni casi, è anche possibile specificare direttamente con il controller xbox. 

Nella tabella seguente vengono descritte le opzioni per la destinazione e il modo per attivare ognuno di essi.

| Oggetto | Tasto di modifica | Modificatore controller | Modificatore dell'interfaccia utente dell'emulatore |
|----------|----------|----------|----------|
| Body | <default> | <default> | <default> |
| Head | Tenere premuto H | <None available> | Puntina da disegno head nell'interfaccia utente |
| A sinistra/Controller | Pulsante Alt di sinistra | Pulsante sinistro interno di una sessione | Simbolo a sinistra | 
| A destra/Controller | Pulsante Alt destro | Pulsante destro interno di una sessione | A destra puntina da disegno |
| Occhi | Tenere premuto Y | <No contoller modifier available> | Puntina da disegno occhi |
  
La tabella seguente illustra come ogni modificatore di destinazione esegue il mapping di ogni input concetti lo spostamento dei

|  Predefinito (corpo) |  Mano/controller (tenere premuto alt / più tirarti indietro) |  Head (tenere premuto H)  |  Occhi (tenere premuto Y) |
|----------|----------|----------|----------|
|  Yaw |  Attivare corpo a sinistra / destra |  Mano di spostamento a sinistra / destra |  Attivare head sinistra / destra | Sguardo occhio è simile a sinistra/destra |
|  Angolazione |  Attivare head su / giù |  Spostare manualmente su / giù |  Attivare head su / giù | Sguardo occhio Cerca su/giù | 
|  Roll |  Esegue il rollup head sinistra / destra |  |  Esegue il rollup head sinistra / destra | (Nessuna azione) |
|  x |  Diapositiva corpo a sinistra / destra |  Spostare manualmente/controller a sinistra / destra |  Attivare head sinistra / destra | (Nessuna azione) |
|  Y |  Spostamento del corpo su / giù |  Spostare manualmente/controller su / giù |  Attivare head su / giù | (Nessuna azione) |
|  Z |  Spostare corpo avanti / indietro |  Spostamento manuale/controller avanti / indietro |  Attivare head su / giù | (Nessuna azione) |
 
Nota: Nel simulatore solo di realtà mista di Windows, i pulsanti di controller possono essere assegnato a un lato o l'altro che usa l'icona della mano targeting modificatori. Analogamente, in HoloLens solo nell'emulatore, posa mano articolati e può essere per il Targeting a un lato o l'altro usando i modificatori di mano. 
 
## <a name="controlling-an-app"></a>Controllo di un'app

Questo articolo ha descritto il set completo di tipi di input e le modalità di input che sono disponibili nell'emulatore di HoloLens e simulatore di realtà mista di Windows. Per l'uso quotidiano viene suggerito il seguente set di controlli:

|  Operazione |  Tastiera e mouse |  Controller | 
|----------|----------|----------|
|  Corpo X |  OGGETTO / 1!D |  Thumbstick sinistro a sinistra / destra | 
|  Corpo Y |  PGSU / PGGIÙ |  Tasto direzionale su / giù | 
|  Corpo Z |  W / S |  Thumbstick sinistro su / giù | 
|  Rotazione di corpo |  Trascinare il mouse a sinistra / destra |  A destra thumbstick sinistro o destro | 
|  Rotazione head |  H + trascinamento del mouse a sinistra / destra |  H (sulla tastiera) + levetta destra a sinistra / destra | 
|  Passo head |  Trascinare il mouse su / giù |  A destra thumbstick su / giù | 
|  Esegue il rollup head |  Q / E |  Tasto direzionale sinistra / destra | 
|  Parte X |  Alt + trascinamento del mouse a sinistra / destra |  Shoulder + levetta destra a sinistra / destra | 
|  Parte Y |  Alt + trascinamento del mouse su / giù |  Shoulder + levetta destra su / giù | 
|  Mano Z |  ALT + L / S |  Shoulder + thumbstick sinistro su / giù | 
|  Azione |  Pulsante destro del mouse |  Trigger | 
|  Ha detto / Home |  Tasto F2 o Windows (tasto di Windows è solo per l'emulatore di HoloLens) |  Pulsante B | 
|  Reimposta |  ESC |  pulsante Start | 
|  Rilevamento |  T |  Pulsante X | 
|  Scorrimento |  ALT + destra del pulsante del mouse e trascina il mouse su / giù |  Shoulder + trigger + levetta destra su / giù | 

## <a name="see-also"></a>Vedere anche
* [Installare gli strumenti](install-the-tools.md)
* [Uso dell'emulatore HoloLens](using-the-hololens-emulator.md)
* [Il simulatore di realtà mista di Windows](using-the-windows-mixed-reality-simulator.md)

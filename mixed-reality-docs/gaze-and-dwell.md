---
title: Sguardo e permanenza
description: Panoramica del modello di input sguardo e permanenza
author: liamartinez
ms.author: liamar
ms.date: 03/31/2019
ms.topic: article
keywords: Progettare sguardo, permanenza, interazione, realtà mista
ms.openlocfilehash: d99180b6eb278eb6d7bf322c01a1c7cceb7fad1f
ms.sourcegitcommit: a4a53e6772805d89a47588857e3e8fb1fd8d9710
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/09/2019
ms.locfileid: "65469067"
---
# <a name="gaze-and-dwell"></a>Sguardo e permanenza

Quando le mani sono occupate con gli strumenti e le parti, i movimenti possono essere difficile o impossibile.  I comandi vocali, come movimento, è possibile base non è affidabili, ad esempio in condizioni eccessivamente elevate.  Inoltre, l'uso di voce, al computer di controllo non è ancora un'interazione di "Mainstream", ma certamente sta per essere steam!  Permanenza sguardo offre il meccanismo più familiare e facile master per Heads-up lavoro mani libere su HoloLens.  Inoltre, permanenza sguardo è 100% affidabile indipendente dai vincoli rumore di interferenze né inattività nell'ambiente operativo.

## <a name="goals"></a>Obiettivi

Forniscono un meccanismo per le interazioni completo invisibile all'utente, senza usare vocali.

## <a name="design-principles"></a>Principi di progettazione

1. Sguardo non è un'arma
    
    Sguardo richiede indicazioni visive per l'interazione intuitiva, ma una quantità eccessiva commenti e suggerimenti possono indurre anxiety. I commenti e suggerimenti dovrebbero aiutare un utente di sapere cosa destinazione, ma non auto-select per il loro scopo. Lettura di testo richiede considerazioni aggiuntive per creare un utente di spazio per assorbire le informazioni prima di selezionare.
    
2. Velocità di Riccioli d'oro di ricerca
    
    Il riempimento di permanenza può avere diversi timer base all'impatto di navigazione: funzioni più utilizzate in genere trarranno vantaggio da tempi di riempimento, mentre le funzioni più CONSEQUENZIALI possono trarre vantaggio da tempi più lunghi di riempimento. Curve di animazione del colore di riempimento possono influire positivamente un sentimento di tempi di riempimento. Considerazione da eseguire per abilitare la decisione di utente da fast/Media/lente compilare le sostituzioni di velocità.
    
3. Ad esempio no-no effetto yo-yo

    L'effetto di yo-yo (noto anche come "sera in the Roxbury") è uno schema bancario che è possibile che vengano da determinati posizionamento del contenuto e i controlli basati su sguardo. Barra di spostamento a un elenco con il pulsante riempimento nella parte inferiore, ad esempio, provoca un ciclo di - aspetto verso il basso permanenza, esaminare i risultati, uno sguardo a permanenza e così via. Questo modello risulta è spiacevole e deve essere evitato, inserendo i controlli di navigazione in una posizione centralizzata che richiede meno avanti e indietro. Posizione di sosta pulsanti rispetto alla loro effetti diventa importante per comodità.

## <a name="ui-patterns"></a>Modelli dell'interfaccia utente

### <a name="high-frequency-buttons"></a>Pulsanti ad alta frequenza
    
* Pulsanti Avanti/Indietro
  * Pre-riempimento di molto breve ritardo (memorizzazione nel buffer lo sfarfallio comparsa)
  * Pulsanti di dimensioni maggiori sono più facili da colpire con sguardo
  * Interessante non mantenere gli URL in altezza occhio per interagire in modo che pressione
  * Permanenza area può essere maggiore di icona inattiva per renderlo più facile da usare (indietro)

### <a name="low-frequency-buttons"></a>Pulsanti di bassa frequenza
    
* Attivare il menu impostazioni
  * Ritardare più pre-riempimento OK (memorizzazione nel buffer lo sfarfallio comparsa)
  * Provare a mantenere questi pulsanti dall'area dei percorsi di cursore frequenti

* Conferme (ad esempio analisi di flusso, le finestre di dialogo)
  * Mostra evidenziazione della selezione nel pulsante principale
  * Rivelare destinazione permanenza in contemporanea con evidenziazione della selezione
  * Usare permanenza che circondano icona per mantenere semplice interfaccia di destinazione
  * Decisione importante, in modo che non attiva l'evidenziazione, rivela permanenza della destinazione per volta incluso
        
### <a name="toggle-buttons"></a>Interruttori

* Pin
  * Cancella attive/inattive dello stato di visualizzazione
  * Riempimento radiale aiuta l'utente lo stato attivo e offre un corso naturale 

* Singole impostazioni
  * Stati di deselezionare attive/inattive
  * Permanenza destinazioni tutto sull'icona circostante a sinistra
  * Permanenza ha come destinazione vengono visualizzati solo quando selezione evidenziare attivo
  * "Il caso di soffermarsi su dispositivo di scorrimento" sul lato destro per le impostazioni di attivazione/disattivazione

### <a name="list-views"></a>Visualizzazioni elenco

* Visualizzazione elenco esplorazione - Guida file da aprire
  * Cursore Evidenzia riga da un punto qualsiasi sulla riga ma non viene avviata permanenza
  * Quando sono evidenziata righe dal cursore, permanenza della destinazione viene visualizzata a sinistra
  * Permanenza destinazione sempre un cerchio sul lato sinistro del testo in tutte le visualizzazioni elenco
  * Non vengono visualizzati che tutti permanenza destinazioni in una sola volta per evitare ricorrenti dell'interfaccia utente
  * Usare nuovamente lo stesso modello per stabilire la conoscenza dell'esperienza utente
        
* Visualizzazione elenco - gerarchia di attività e i passaggi seguenti in una Guida di esplorazione
  * Permanenza destinazione sempre un cerchio sul lato sinistro del testo
  * Intuitività di permanenza della compressione/espansione
        
* Visualizzazione elenco esplorazione - modalità
  * Seguire modelli stabiliti in precedenza

### <a name="contextual-buttons"></a>Pulsanti contestuali

* Mostra/Nascondi 3D - Mostra backup in 3D lungo attacco quasi vntana 
  * Cancella attive/inattive dello stato di visualizzazione

### <a name="pivots"></a>Pivot

* Elenco di guide recenti/All
  * Compilare l'intuitività dell'interfaccia utente che rimane per indicare qual è la scheda è attiva
  * Per una singola parola breve pivot, abbiamo scelto di rinunciare il criterio di permanenza di destinazione
  * È preferita interfaccia semplificata tramite un altro cerchio 2 destinazioni e una più ampio dell'interfaccia utente
  * In questo caso, le parole sono sufficientemente breve che un ritardo fornisce sufficiente comfort prima del riempimento


## <a name="ux-guidelines-and-best-practices"></a>Linee guida dell'esperienza utente e le procedure consigliate

### <a name="target-sizes"></a>Dimensioni delle destinazioni

  * Dimensioni minime icona PIN: 6cm nello spazio globale in Unity, 30 MRU (30cm @ 2 minuti)
  * Sono affatto obiettivi "magnetizzati" o "permanenti"? (vale a dire estasiati anti-aliasing di cursori)

### <a name="animation"></a>Animazione

  * Ritardo prima della permanenza visual attiva .5sec
  * Durata della permanenza visual 1,2 sec
  * Curva su animazione?

### <a name="visual-feedback"></a>Feedback visivo

  * Riempimento radiale dalla posizione di inizio del cursore sguardo
  * Riempimento sempre radiale dal centro del pulsante. Una risposta coerente è meno ambiguo rispetto a tutte le direzioni diverse in diversi pulsanti. 
    * Questa regola può essere interrotta anche se per le interazioni direzionale (ad esempio, nav su/giù/sinistra/destra, ecc.). Ad esempio, rende Guide un'eccezione in avanti/indietro verrà mantenuto a destra riempie.
    * Prendere in considerazione l'inversione radiale riempimento dall'esterno (se l'attivazione/disattivazione). Il sentimento inversa di pressione di un pulsante è un modello visual interessante per mantenere. 

### <a name="progressive-disclosure"></a>Presentazione progressiva delle

 * Presentazione progressiva delle significa che la destinazione di permanenza viene visualizzata in evidenziazione (ad esempio, in un controllo elenco)
 * Testo barra evidenziazioni con spotlight rivelano su sguardo ovunque si trovino con testo
 * Sguardo riempimento destinazione vengono visualizzati sempre a sinistra, ma solo per l'elemento di elenco evidenziato
 * Evitare di inserire tutte le destinazioni di permanenza in qualsiasi momento a causa di un aspetto ripetitiva dei cerchi in pila
 
 ## <a name="see-also"></a>Vedere anche
* [Manipolazione diretta](direct-manipulation.md)
* [Puntamento e commit](point-and-commit.md)
* [Concetti fondamentali delle interazioni](interaction-fundamentals.md)
* [Puntamento con la testa e commit](gaze-and-commit.md)
* [Sguardo fisso e voce](voice-design.md)

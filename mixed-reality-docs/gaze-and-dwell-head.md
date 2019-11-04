---
title: Puntamento con la testa e attesa
description: Panoramica del modello di input puntamento con la testa e attesa
author: liamartinez
ms.author: liamar
ms.date: 05/13/2019
ms.topic: article
keywords: realtà mista, sguardo fisso, attesa, interazione, progettazione
ms.openlocfilehash: 6d209d3cc91ceecb4b9feef2925f093288c9f8ac
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73439312"
---
# <a name="head-gaze-and-dwell"></a>Puntamento con la testa e attesa

Quando le mani sono occupate con gli attrezzi e le parti, i movimenti possono risultare difficili o addirittura impossibili. I comandi vocali, come i movimenti, possono non essere affidabili in determinati contesti, ad esempio in ambienti particolarmente rumorosi. Inoltre, l'uso della voce per controllare i computer, nonostante conosca una rapida diffusione, non è ancora una pratica comune ovunque. Il modello di input puntamento con la testa e attesa offre un meccanismo già familiare e di facilissima gestione per lavorare in HoloLens con la testa sollevata e senza avere bisogno di usare le mani. Questo modello di input è anche affidabile al 100%, indipendentemente dall'interferenza di possibili rumori o da eventuali obblighi di restare in silenzio nell'ambiente operativo.

## <a name="scenarios"></a>Scenari

Il punto di vista e la permanenza sono eccellenze negli scenari in cui le mani di una persona sono occupate da altre attività e la voce non è del 100% affidabile o disponibile a causa di vincoli ambientali o sociali. Un buon esempio di questo tipo di situazioni è dato da una persona che indossa un dispositivo HoloLens per la sovrimpressione di informazioni di riferimento mentre ripara il motore di un'automobile. Le sue mani sono occupate con gli attrezzi o devono sostenere il corpo mentre la persona si protende sul vano motore. L'autofficina è rumorosa a causa dei colpi e del ronzio costanti degli attrezzi da lavoro, quindi l'uso dei comandi vocali risulterebbe particolarmente difficoltoso. Head-sguardi e l'abitazione consentono all'utente che usa HoloLens di esplorare in modo sicuro il materiale di riferimento senza interrompere il flusso di lavoro. 

## <a name="device-support"></a>Supporto di dispositivi

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Modello di input</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (prima generazione)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
    </tr>
     <tr>
        <td>Puntamento con la testa e attesa</td>
        <td>✔️ Consigliata</td>
        <td>✔️ Consigliata</td>
        <td>✔️ Consigliata</td>
    </tr>
</table>


## <a name="design-principles"></a>Principi di progettazione

**Evitare di "guardare come un'arma"**

Il puntamento con la testa e l'attesa richiedono un feedback visivo intuitivo, ma una mole eccessiva di feedback può produrre ansia. Il feedback deve aiutare l'utente a capire cosa sta puntando, ma non selezionare automaticamente una destinazione contrariamente alla sua intenzione. Per leggere un testo, le icone e le etichette servono più tempo e più attenzione, quindi considera questo aspetto per dare alla persona modo di assorbire le informazioni prima di effettuare la selezione.
    
**Cerca velocità di ricciolo**
    
Le interazioni di attesa possono avere timer diversi in base all'impatto sulla navigazione: le funzioni usate con maggiore frequenza in genere traggono vantaggio da tempi di riempimento più ridotti, mentre le funzioni più consequenziali possono trarre vantaggio da tempi di riempimento più lunghi. Quando viene usato un effetto di riempimento per mostrare questi timer, le curve di animazione del colore di riempimento possono indurre positivamente la sensazione che i tempi di riempimento siano più rapidi. Considera questi aspetti per consentire all'utente di prendere le sue decisioni scegliendo override della velocità di riempimento alta/media/bassa.
    
**Pronunciare no-no per l'effetto yo-yo**

L'effetto yo-yo è uno scomodo andamento del movimento della testa che può verificarsi quando la posizione del contenuto e dei controlli per il puntamento con la testa e l'attesa obbligano gli utenti a guardare ripetutamente in alto e in basso. Ad esempio, un elenco di spostamento con il pulsante di selezione e il pulsante di disattivazione nella parte inferiore induce un ciclo di ricerca verso il basso, Cerca i risultati, Cerca giù e così via. Questo modello risultante è scomodo e deve essere evitato posizionando i controlli di navigazione in una posizione centralizzata che richiede meno avanti e indietro. Il posizionamento dei pulsanti di attesa in base al loro effetto diventa un fattore importante per il comfort dell'utente.

<br>

---


## <a name="ux-guidelines-and-best-practices"></a>Linee guida e procedure consigliate per l'esperienza utente

### <a name="target-sizes"></a>Dimensioni delle destinazioni
  Per essere facilmente accessibili, gli obiettivi di Head-look e di abitazione devono essere sufficientemente grandi da poter essere esaminati in modo semplice e tenere la sede stabile sulla destinazione per il periodo di tempo previsto. Per ottenere un'esperienza ottimale, è consigliabile utilizzare una dimensione minima di 2 gradi. 

### <a name="visual-feedback"></a>Feedback visivo

Quando usi un riempimento radiale per rappresentare il timer di attesa, inizia dalla parte centrale del pulsante. Una risposta uniforme genera meno confusione di tante indicazioni diverse sui vari pulsanti. 

  * È tuttavia possibile contravvenire a questa regola per le interazioni direzionali, ad esempio per la navigazione verso l'alto, il basso, a sinistra, a destra e così via. Ad esempio, Microsoft Dynamics 365 Guides fa un'eccezione per AVANTI/INDIETRO, trattandosi di riempimenti sinistra-destra.
  * Considera la possibilità di invertire il riempimento radiale dall'esterno per scenari come quelli di disattivazione di un pulsante. La sensazione opposta di premere un pulsante è un effetto visivo piacevole da mantenere. 

### <a name="progressive-disclosure"></a>Rivelazione progressiva

Con la rilevazione progressiva vengono mostrati solo i dettagli rilevanti in ciascuna fase di un'interazione. Nel caso dell'attesa, ciò significa rivelare la destinazione con l'evidenziazione, ad esempio in un controllo elenco.

 ### <a name="oversized-targets"></a>Destinazioni di dimensioni eccessive
L'area di attesa può essere più grande dell'icona inattiva per agevolare l'uso, come nel caso del pulsante Indietro in Microsoft Dynamics 365 Guides.

### <a name="prevent-flickering-with-delayed-feedback"></a>Evitare lo sfarfallio con un feedback ritardato
Aggiungi un breve ritardo prima di avviare il feedback visivo per evitare lo sfarfallio quando qualcuno passa su una destinazione di attesa.
* Per i pulsanti che interagiscono con frequenza frequente, è molto breve, in modo che l'applicazione ritenga riattiva.
* Per i pulsanti che interagiscono con una frequenza infrequente, un ritardo più lungo può essere appropriato per evitare l'interfaccia.


<br>

---

## <a name="ui-patterns"></a>Modelli per l'interfaccia utente

### <a name="high-frequency-buttons"></a>Pulsanti usati frequentemente

:::row:::
    :::column:::
        I pulsanti ad alta frequenza sono pulsanti usati comunemente in un'applicazione. Un buon esempio è rappresentato dai pulsanti Avanti e Indietro in Microsoft Dynamics 365 Guides.<br>
        <br>
        **Raccomandazioni**<br>
  * I pulsanti ad alta frequenza dovrebbero essere di grandi dimensioni, più facili da raggiungere con l'Head-sguardi
  * Rimanere vicino all'altezza degli occhi per evitare la pressione ergonomica.<br>
        <br>
*Immagine: pulsante Avanti per Microsoft Dynamics 365 guide*
    :::column-end:::
        :::column:::
       ![Pulsante Avanti per Microsoft Dynamics 365 guide](images/GuideNextButton.png)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="low-frequency-buttons"></a>Pulsanti usati raramente
I pulsanti usati raramente sono pulsanti con cui si interagisce con meno regolarità all'interno dell'applicazione. Un buon esempio è rappresentato da un pulsante che consente di accedere al menu delle impostazioni o di cancellare tutto il lavoro svolto.

* Prova a posizionare questi pulsanti in modo che non intralcino i percorsi di puntamento con la testa di uso frequente per evitare che vengano attivati accidentalmente. 

<br>

---

### <a name="confirmations"></a>Conferme

:::row:::
    :::column:::
        Quando un'azione ha un impatto significativo, ad esempio perché determina un addebito di denaro, l'eliminazione del lavoro svolto o l'avvio di un lungo processo, è utile chiedere alla persona di confermare che intendesse effettivamente selezionare un determinato pulsante.<br>
        <br>
        **Raccomandazioni**<br>
  * Mostra l'evidenziazione della selezione sul pulsante principale.
  * Rivela la destinazione dell'attesa contemporaneamente all'evidenziazione della selezione.
  * Per il pulsante secondario, rivela la destinazione dell'attesa al momento del puntamento con la testa.<br>
        <br>
*Immagine: finestra di conferma della Guida di Microsoft Dynamics 365*
    :::column-end:::
        :::column:::
       ![Finestra di conferma della Guida di Microsoft Dynamics 365](images/GuidesConfirmation.png)<br>
    :::column-end:::
:::row-end:::
        
<br>

---

### <a name="toggle-buttons"></a>Interruttori
Per funzionare correttamente, gli interruttori necessitano di una logica più sottile. Quando una persona si sofferma (ovvero resta in attesa) su un interruttore e lo attiva, deve uscire dal pulsante e quindi tornare per riavviare la logica di attesa. È importante che i pulsanti attivabili o disattivabili come interruttori abbiano uno stato attivo chiaramente diverso dallo stato inattivo. 

<br>

---

### <a name="list-views"></a>Visualizzazioni elenco

:::row:::
    :::column:::
        Le visualizzazioni elenco presentano una particolare sfida per l'input di punta e di residenza. Gli utenti devono poter analizzare il contenuto senza avere la sensazione di doversi muovere con cautela tra le destinazioni di attesa.<br>
        <br>
**Raccomandazioni**<br>
  * Far evidenziare l'intera riga quando si è a capo, ma non inizia la permanenza, a meno che l'Head-sguardi si trovi nella destinazione di residenza specifica.
  * Mostra solo la destinazione di residenza quando la riga viene evidenziata in modo da ridurre il rumore visivo.
  * Essere chiari e coerenti con la posizione delle destinazioni di residenza.
  * Non mostrare tutte le destinazioni di residenza in una sola volta per evitare l'interfaccia utente ripetitiva.
  * Riutilizzare lo stesso modello il più spesso possibile per stabilire la familiarità con l'esperienza utente.<br>
        <br>
*Immagine: elenco delle guide di Microsoft Dynamics 365*
    :::column-end:::
        :::column:::
       ![Elenco delle guide di Microsoft Dynamics 365](images/GuidesListView.png)<br>
    :::column-end:::
:::row-end:::

<br>

---
 
 ## <a name="see-also"></a>Vedi anche
* [Sguardo e commit](gaze-and-commit.md)
* [Manipolazione diretta](direct-manipulation.md)
* [Movimenti pratici](gaze-and-commit.md#composite-gestures)
* [Hand-point e commit](point-and-commit.md)
* [Interazioni istintive](interaction-fundamentals.md)
* [Input vocale](voice-input.md)

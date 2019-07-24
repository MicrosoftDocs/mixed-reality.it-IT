---
title: Puntamento con la testa e attesa
description: Panoramica del modello di input puntamento con la testa e attesa
author: liamartinez
ms.author: liamar
ms.date: 05/13/2019
ms.topic: article
keywords: realtà mista, sguardo fisso, attesa, interazione, progettazione
ms.openlocfilehash: d522ca3a6f36995959e8e6e87482279d05bf0aa3
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387535"
---
# <a name="head-gaze-and-dwell"></a>Puntamento con la testa e attesa

Quando le mani sono occupate con gli attrezzi e le parti, i movimenti possono risultare difficili o addirittura impossibili. I comandi vocali, come i movimenti, possono non essere affidabili in determinati contesti, ad esempio in ambienti particolarmente rumorosi. Inoltre, l'uso della voce per controllare i computer, nonostante conosca una rapida diffusione, non è ancora una pratica comune ovunque. Il modello di input puntamento con la testa e attesa offre un meccanismo già familiare e di facilissima gestione per lavorare in HoloLens con la testa sollevata e senza avere bisogno di usare le mani. Questo modello di input è anche affidabile al 100%, indipendentemente dall'interferenza di possibili rumori o da eventuali obblighi di restare in silenzio nell'ambiente operativo.

## <a name="scenarios"></a>Scenari

Il puntamento con la testa e l'attesa offrono un metodo ottimale a cui ricorrere per gli scenari in cui le mani di una persona sono occupate a svolgere altre attività e l'uso della voce non è affidabile al 100% o non consentito per vincoli sociali o correlati all'ambiente. Un buon esempio di questo tipo di situazioni è dato da una persona che indossa un dispositivo HoloLens per la sovrimpressione di informazioni di riferimento mentre ripara il motore di un'automobile. Le sue mani sono occupate con gli attrezzi o devono sostenere il corpo mentre la persona si protende sul vano motore. L'autofficina è rumorosa a causa dei colpi e del ronzio costanti degli attrezzi da lavoro, quindi l'uso dei comandi vocali risulterebbe particolarmente difficoltoso. Il puntamento con la testa e l'attesa consentono alla persona in HoloLens di navigare in modo sicuro all'interno del materiale di riferimento senza interrompere il flusso di lavoro. 

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
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
    </tr>
     <tr>
        <td>Puntamento con la testa e attesa</td>
        <td>✔️ Consigliato</td>
        <td>✔️ Consigliato</td>
        <td>✔️ Consigliato</td>
    </tr>
</table>

## <a name="goals"></a>Obiettivi

Fornire un meccanismo che consenta di interagire lasciando libere le mani e senza usare la voce.

## <a name="design-principles"></a>Principi di progettazione

1. Evitare di usare lo "sguardo fisso come un'arma"

    Il puntamento con la testa e l'attesa richiedono un feedback visivo intuitivo, ma una mole eccessiva di feedback può produrre ansia. Il feedback deve aiutare l'utente a capire cosa sta puntando, ma non selezionare automaticamente una destinazione contrariamente alla sua intenzione. Per leggere un testo, le icone e le etichette servono più tempo e più attenzione, quindi considera questo aspetto per dare alla persona modo di assorbire le informazioni prima di effettuare la selezione.
    
2. Cercare di ottenere una velocità ottimale
    
    Le interazioni di attesa possono avere timer diversi in base all'impatto sulla navigazione: le funzioni usate con maggiore frequenza in genere traggono vantaggio da tempi di riempimento più ridotti, mentre le funzioni più consequenziali possono trarre vantaggio da tempi di riempimento più lunghi. Quando viene usato un effetto di riempimento per mostrare questi timer, le curve di animazione del colore di riempimento possono indurre positivamente la sensazione che i tempi di riempimento siano più rapidi. Considera questi aspetti per consentire all'utente di prendere le sue decisioni scegliendo override della velocità di riempimento alta/media/bassa.
    
3. Evitare l'effetto yo-yo

    L'effetto yo-yo è uno scomodo andamento del movimento della testa che può verificarsi quando la posizione del contenuto e dei controlli per il puntamento con la testa e l'attesa obbligano gli utenti a guardare ripetutamente in alto e in basso. Ad esempio, se il pulsante per scorrere un elenco mediante puntamento della testa e attesa è posizionato in fondo, l'utente dovrà guardare in basso per effettuare l'attesa, guardare in alto per esaminare i risultati, guardare di nuovo in basso per effettuare l'attesa e così via. Ne risulta una sequenza di movimenti scomoda che è possibile evitare posizionando i controlli di navigazione in un punto centrale per cui si renda meno necessario alzare e abbassare continuamente lo sguardo. Il posizionamento dei pulsanti di attesa in base al loro effetto diventa un fattore importante per il comfort dell'utente.

## <a name="ux-guidelines-and-best-practices"></a>Linee guida e procedure consigliate per l'esperienza utente

### <a name="target-sizes"></a>Dimensioni delle destinazioni
  Per essere facilmente accessibili, le destinazioni del puntamento con la testa e dell'attesa devono essere grandi abbastanza da consentire all'utente di puntarle agevolmente e di mantenere stabilmente la testa puntata su di esse per l'intervallo di tempo previsto. È consigliabile che le destinazioni abbiano una dimensione di almeno 2 gradi per garantire un'esperienza con il massimo comfort. 

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
* Per i pulsanti con cui si interagisce frequentemente, specifica un ritardo molto breve in modo che l'applicazione risulti reattiva.
* Per i pulsanti con cui si interagisce di rado, può essere utile specificare un ritardo maggiore per evitare che l'interfaccia risulti tremolante.

## <a name="ui-patterns"></a>Modelli per l'interfaccia utente

### <a name="high-frequency-buttons"></a>Pulsanti usati frequentemente
![Pulsante Avanti per Microsoft Dynamics 365 guide](images/GuideNextButton.png "Pulsante Avanti per Microsoft Dynamics 365 guide")<br>
*I pulsanti ad alta frequenza sono pulsanti usati comunemente in un'applicazione. Un esempio valido è costituito dai pulsanti avanti e indietro nelle guide di Microsoft Dynamics 365.*

I pulsanti usati frequentemente dovrebbero:
* essere pulsanti piuttosto grandi, in modo che sia più facile puntarli mediante puntamento con la testa;
* essere posizionati all'altezza degli occhi per evitare la tensione dei muscoli a vantaggio dell'ergonomia.

### <a name="low-frequency-buttons"></a>Pulsanti usati raramente
I pulsanti usati raramente sono pulsanti con cui si interagisce con meno regolarità all'interno dell'applicazione. Un buon esempio è rappresentato da un pulsante che consente di accedere al menu delle impostazioni o di cancellare tutto il lavoro svolto.

* Prova a posizionare questi pulsanti in modo che non intralcino i percorsi di puntamento con la testa di uso frequente per evitare che vengano attivati accidentalmente. 

### <a name="confirmations"></a>Conferme
![Finestra di dialogo di conferma di Microsoft Dynamics 365 Guides](images/GuidesConfirmation.png "Finestra di dialogo di conferma di Microsoft Dynamics 365 Guides")

Quando un'azione ha un impatto significativo, ad esempio perché determina un addebito di denaro, l'eliminazione del lavoro svolto o l'avvio di un lungo processo, è utile chiedere alla persona di confermare che intendesse effettivamente selezionare un determinato pulsante. Per le interfacce utente di puntamento con la testa e attesa è necessario attenersi ad alcuni modelli e considerare alcuni aspetti relativi alle finestre di dialogo di conferma:

  * Mostra l'evidenziazione della selezione sul pulsante principale.
  * Rivela la destinazione dell'attesa contemporaneamente all'evidenziazione della selezione.
  * Per il pulsante secondario, rivela la destinazione dell'attesa al momento del puntamento con la testa.
        
### <a name="toggle-buttons"></a>Interruttori
Per funzionare correttamente, gli interruttori necessitano di una logica più sottile. Quando una persona si sofferma (ovvero resta in attesa) su un interruttore e lo attiva, deve uscire dal pulsante e quindi tornare per riavviare la logica di attesa. È importante che i pulsanti attivabili o disattivabili come interruttori abbiano uno stato attivo chiaramente diverso dallo stato inattivo. 

### <a name="list-views"></a>Visualizzazioni elenco
![Finestra di dialogo di conferma di Microsoft Dynamics 365 Guides](images/GuidesListView.png "Finestra di dialogo di conferma di Microsoft Dynamics 365 Guides")<br>
*Le visualizzazioni elenco presentano una particolare sfida per l'input di punta e di residenza. È necessario che gli utenti siano in grado di eseguire la scansione dei contenuti senza sentire la necessità di raggiungere i puntamenti intorno alle destinazioni di residenza.*

Seguono alcuni suggerimenti per progettare le visualizzazioni elenco:
* Fai in modo che l'intera riga venga evidenziata quando viene puntata con la testa, ma fai iniziare l'attesa solo quando con la testa viene puntata la destinazione di attesa specifica.
* Mostra la destinazione di attesa solo quando la riga è evidenziata per ridurre il disturbo visivo.
* Posiziona le destinazioni di attesa in modo chiaro e coerente.
* Non mostrare tutte le destinazioni di attesa contemporaneamente, in modo da non fornire un'interfaccia utente ripetitiva.
* Riutilizza lo stesso modello il più possibile per sviluppare un senso di familiarità con l'esperienza utente.
 
 ## <a name="see-also"></a>Vedere anche
* [Manipolazione diretta con le mani](direct-manipulation.md)
* [Puntamento e commit con le mani](point-and-commit.md)
* [Interazioni istintive](interaction-fundamentals.md)
* [Puntamento con la testa e commit](gaze-and-commit.md)
* [Esecuzione di comandi vocali](voice-design.md)

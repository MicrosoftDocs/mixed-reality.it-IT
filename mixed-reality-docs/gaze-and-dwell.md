---
title: Head-sguardo e permanenza
description: Panoramica del modello di input sguardo a capo e permanenza
author: liamartinez
ms.author: liamar
ms.date: 05/13/2019
ms.topic: article
ms.localizationpriority: high
keywords: Progettare sguardo, permanenza, interazione, realtà mista
ms.openlocfilehash: ae4688da791fd3afb7be66069049bbe51102dd7e
ms.sourcegitcommit: 8d6e5723283c03f984f1fafef81afa5aab5d04bc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/23/2019
ms.locfileid: "66039203"
---
# <a name="head-gaze-and-dwell"></a>Head-sguardo e permanenza

Quando le mani sono occupate con gli strumenti e le parti, i movimenti possono essere difficile o impossibile. I comandi vocali, quali i movimenti, possono non essere affidabili in determinati contesti, ad esempio in condizioni eccessivamente elevate. Inoltre, utilizzando voce di controllo nei computer non è universalmente comune, ma certamente sta per essere steam! Head-sguardo e permanenza offre il meccanismo più familiare e facile master per l'utilizzo di heads-up e automatizzate su HoloLens. Inoltre, head-sguardo e permanenza è affidabile al 100% indipendente dai vincoli rumore di interferenze né inattività nell'ambiente operativo.

## <a name="scenarios"></a>Scenari

Head-sguardo e permanenza è ideale per scenari in cui una persona sono occupato con altre attività e vocale non è 100% sul valore a causa delle limitazioni ambientali o di social networking o affidabili. Un buon esempio è una persona che portano un HoloLens per sovrapporre informazioni di riferimento durante il ripristino di un motore di automobili. Le mani siano occupate con gli strumenti o supportare corpo come essi fare affidamento nel raggruppamento di motore. Lo spazio garage è elevato, con la costante banging e nuovo di strumenti, rendendo difficile comandi vocali. Head-sguardo e permanenza consente alla persona HoloLens per esplorare in tutta sicurezza il materiale di riferimento senza interruzione in flusso di lavoro. 

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
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (dal 1 ° generazione)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Auricolari coinvolgenti</strong></a></td>
    </tr>
     <tr>
        <td>Head-sguardo e permanenza</td>
        <td>✔️ Consigliato</td>
        <td>✔️ Consigliato</td>
        <td>✔️ Consigliato</td>
    </tr>
</table>

## <a name="goals"></a>Obiettivi

Forniscono un meccanismo per le interazioni completamente invisibile, senza usare vocali.

## <a name="design-principles"></a>Principi di progettazione

1. Evitare "Estasiati un'arma"

    Head-sguardo e permanenza richiede indicazioni visive per essere intuitiva, ma possono indurre la anxiety troppa commenti e suggerimenti. I commenti e suggerimenti dovrebbero aiutare un utente di sapere cosa destinazione, ma non di auto-select contro il loro scopo. La lettura di testo, icone e le etichette richiede considerazioni aggiuntive per fornire una stanza di persona per assorbire le informazioni prima di selezionare.
    
2. Velocità di Riccioli d'oro di ricerca
    
    Interazioni di permanenza possono avere diversi timer base all'impatto di navigazione: funzioni più utilizzate in genere trarranno vantaggio da tempi di riempimento, mentre le funzioni più CONSEQUENZIALI possono trarre vantaggio da tempi più lunghi di riempimento. Quando si usa un effetto di riempimento per visualizzare questi timer, curve di animazione del colore di riempimento possono influire positivamente un sentimento di tempi di riempimento. Considerazione da eseguire per abilitare la decisione di utente da fast/Media/lente compilare le sostituzioni di velocità.
    
3. Ad esempio no-no effetto yo-yo

    L'effetto yo-yo è un modello disagio di movimento della testina che è possibile che durante il posizionamento dei controlli contenuto e head sguardo e permanenza impone agli utenti di costantemente aspetto ripetutamente e in verticale. Barra di spostamento a un elenco con il pulsante head sguardo e permanenza nella parte inferiore, ad esempio, provoca un ciclo di - aspetto verso il basso per permanenza, esaminare risultati, cercare verso il basso di permanenza e così via. Questo modello risulta è spiacevole e deve essere evitato, inserendo i controlli di navigazione in una posizione centralizzata che richiede meno avanti e indietro. Posizione di sosta pulsanti rispetto alla loro effetti diventa importante per comodità.

## <a name="ux-guidelines-and-best-practices"></a>Linee guida dell'esperienza utente e le procedure consigliate

### <a name="target-sizes"></a>Dimensioni delle destinazioni
  Per essere facilmente accessibile, head sguardo permanenza le destinazioni devono essere sufficientemente grande da destinazione comforatably e tenere premuto uno head stabily nella destinazione per il periodo di tempo prestabilito. Si consiglia una dimensione di destinazione minimo di 2 gradi per ottenere l'esperienza di maggiore familiarità. 

### <a name="visual-feedback"></a>Feedback visivo

Quando si usa un riempimento radiale per rappresentare il timer di permanenza, iniziare dal centro del pulsante. Una risposta coerente è meno ambiguo rispetto a tutte le direzioni diverse in diversi pulsanti. 

  * Questa regola può essere interrotta anche se per le interazioni direzionale (ad esempio, nav su/giù/sinistra/destra, ecc.). Ad esempio, Microsoft Dynamics 365 Guide rende un'eccezione in avanti/indietro verrà mantenuto riempie a destra.
  * Prendere in considerazione l'inversione di riempimento radiale dall'esterno, per gli scenari, ad esempio usare un pulsante di disattivazione. Il sentimento inversa di pressione di un pulsante è un modello visual interessante per mantenere. 

### <a name="progressive-disclosure"></a>Presentazione progressiva delle

Presentazione progressiva delle significa solo che mostra i dettagli che è pertinente in ogni fase di un'interazione. Per la permanenza, ciò significa che la destinazione di permanenza viene visualizzata in evidenziazione (ad esempio, in un controllo elenco).

 ### <a name="oversized-targets"></a>Destinazioni di dimensioni eccessive
Permanenza area può essere maggiore di icona inattiva per renderne più semplice da usare, ad esempio il pulsante Indietro nelle guide di Microsoft Dynamics 365.

### <a name="prevent-flickering-with-delayed-feedback"></a>Evitare lo sfarfallio ritardata e suggerimenti
Usare un breve ritardo prima di avviare un feedback visivo per evitare lo sfarfallio quando un utente passa su un obiettivo di permanenza.
* Per pulsanti inteacted con frequenza, mantenere il ritardo molto breve in modo che l'applicazione scelga reattiva.
* Per i pulsanti sono ha interagiti con infrequenctly un ritardo maggiore può essere approprate per evitare l'interfaccia sente twitchy.

## <a name="ui-patterns"></a>Modelli dell'interfaccia utente

### <a name="high-frequency-buttons"></a>Pulsanti ad alta frequenza
![Pulsante Avanti di Microsoft Dynamics 365 Guide](images/GuideNextButton.png "pulsante Avanti di Microsoft Dynamics 365 Guide") pulsanti ad alta frequenza sono disponibili pulsanti che vengono comunemente utilizzati in tutta l'applicazione. Un buon esempio di questi sono i pulsanti Avanti e indietro nelle guide di Microsoft Dynamics 365.

Pulsanti ad alta frequenza devono...
* essere pulsanti più grandi, più facile da colpire con head sguardo
* rimangono quasi altezza sotto controllo per evitare ergonomico sforzo.

### <a name="low-frequency-buttons"></a>Pulsanti di bassa frequenza
I pulsanti di bassa frequenza sono pulsanti che non sono ha interagiti con regolarmente in tutta l'applicazione. Un buon esempio potrebbe essere un pulsante per accedere al menu impostazioni, o un pulsante per cancellare tutto il lavoro.

* Provare a mantenere questi pulsanti dall'area percorsi head sguardo frequenti per evitare l'attivazione accidentale. 

### <a name="confirmations"></a>Conferme
![Finestra di dialogo Conferma le guide Microsoft Dynamics 365](images/GuidesConfirmation.png "finestra di dialogo Conferma le guide Microsoft Dynamics 365")

Quando un'azione ha un impatto significativo, come l'addebito di costi, l'eliminazione di lavoro o avviare un processo lungo, è utile verificare che un utente deve selezionare un pulsante. Head-sguardo e permanenza interfacce utente vi sono alcune considerazioni per le finestre di dialogo di conferma e sui modelli:

  * Mostra evidenziazione della selezione nel pulsante principale.
  * Rivelare destinazione permanenza in contemporanea con evidenziazione della selezione.
  * Per il pulsante secondario, evidenziare la destinazione di permanenza in head sguardo.
        
### <a name="toggle-buttons"></a>Interruttori
Pulsanti interruttore richiedono una logica di immagini per il corretto funzionamento. Quando un utente trova su un interruttore e actives lo, devono uscire il pulsante e quindi tornare a riavviare la logica di permanenza. È importante che i pulsanti tipo hanno un chiaro attiva rispetto a stato inattivo. 

### <a name="list-views"></a>Visualizzazioni elenco
![Finestra di dialogo Conferma le guide di Microsoft Dynamics 365](images/GuidesListView.png "finestra di dialogo Conferma le guide di Microsoft Dynamics 365") visualizzazioni elenco presentano una sfida particolare per head sguardo e permanenza input. Gli utenti devono essere in grado di analizzare il contenuto senza senso che è necessario tiptoe tutto gli obiettivi di permanenza. 

Alcuni suggerimenti per la Progettazione visualizzazioni elenco:
* dispone l'intera riga evidenziare quando gazed head ma non inizia permanenza, a meno che non è head sguardo nella destinazione permanenza specifico.
* Mostra solo la destinazione di permanenza quando la riga viene evidenziata per ridurre qualsiasi disturbo visivo.
* essere chiari e coerenti con la posizione di sosta destinazioni.
* Non vengono visualizzati che tutti permanenza destinazioni in una sola volta per evitare ricorrenti dell'interfaccia utente
* riutilizzare lo stesso modello più frequentemente possibile per stabilire la conoscenza dell'esperienza utente
 
 ## <a name="see-also"></a>Vedere anche
* [Manipolazione diretta con le mani](direct-manipulation.md)
* [Puntamento e commit con le mani](point-and-commit.md)
* [Interazioni istintive](interaction-fundamentals.md)
* [Puntamento con la testa e commit](gaze-and-commit.md)
* [Esecuzione di comandi vocali](voice-design.md)

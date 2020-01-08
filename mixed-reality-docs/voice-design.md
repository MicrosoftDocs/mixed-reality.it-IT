---
title: Esecuzione di comandi vocali
description: La direzione dello sguardo, i movimenti e i comandi vocali (GGV, Gaze, Gesture and Voice) sono un mezzo di interazione fondamentale in HoloLens. Questo articolo fornisce indicazioni precise sulla progettazione dei comandi vocali.
author: shengkait
ms.author: shentan
ms.date: 04/21/2019
ms.topic: article
keywords: Windows Mixed Reality, progettazione, interazione, comandi vocali
ms.openlocfilehash: 66afa24699ed22fb17ab36818ba67a526f4c5618
ms.sourcegitcommit: 7e8b9de561cbc8483e84511f3e9cbd779f3a999f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/27/2019
ms.locfileid: "75502642"
---
# <a name="voice-commanding"></a>Esecuzione di comandi vocali

Quando si usano i comandi vocali, lo sguardo viene in genere usato come meccanismo di destinazione, sia che si tratti di un puntatore ("Select") o di indirizzare il comando a un'applicazione ("vedere il messaggio"). Naturalmente alcuni comandi vocali non richiedono una destinazione, ad esempio "Vai all'inizio" o "Ehi Cortana".


## <a name="device-support"></a>Supporto di dispositivi

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Funzionalità</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (prima generazione)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
    </tr>
     <tr>
        <td>Esecuzione di comandi vocali</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️ (con il visore VR collegato)</td>
    </tr>
</table>



## <a name="how-to-use-voice"></a>Modalità di utilizzo dei comandi vocali

Valuta l'opportunità di aggiungere comandi vocali a un'esperienza che stai creando. Voice è un modo potente e pratico per controllare il sistema e le app. Poiché gli utenti parlano con un'ampia gamma di dialetti e accenti, la scelta appropriata delle parole chiave di contenuti vocali garantirà un'interpretazione non ambigua dei comandi degli utenti.

### <a name="best-practices"></a>Procedure consigliate

Di seguito vengono illustrate alcune procedure che semplificheranno il riconoscimento vocale.
* **Usa comandi concisi**. Quando possibile, scegli parole chiave di due o più sillabe. Le parole di una sillaba tendono a usare suoni di vocali differenti se pronunciate da persone con accenti diversi. Esempio: "riprodurre video" è migliore di "riprodurre il video attualmente selezionato"
* **Usare un vocabolario semplice** , ad esempio: "show note" è migliore di "Show manifest"
* **Assicurati che i comandi non siano distruttivi**. Verifica che tutte le azioni eseguibili con un comando vocale siano di tipo non distruttivo e possano essere annullate facilmente qualora un'altra persona che parla vicino all'utente attivi accidentalmente un comando.
* **Evita comandi con suoni simili**. Non registrare più comandi vocali con suoni molto simili. Esempio: "Mostra più" e "Mostra archivio" può essere un suono molto simile.
* **Annulla la registrazione dell'app quando non è in uso**. Quando l'app non è in uno stato in cui sia valido un comando vocale specifico, è consigliabile annullarne la registrazione in modo da evitare confusione tra i comandi.
* **Esegui test con accenti diversi**. Testa l'app con utenti con accenti diversi.
* **Mantieni la coerenza dei comandi vocali**. Se "Indietro" porta alla pagina precedente, mantieni questo comportamento nelle applicazioni.
* **Evita di usare i comandi di sistema**. I comandi vocali seguenti sono riservati per il sistema. Non devono essere usati dalle applicazioni.
   * "Ehi Cortana"
   * "Seleziona"

### <a name="select"></a>"Seleziona"

Pronunciare "seleziona" in qualsiasi momento attiva la destinazione a cui punta il cursore sguardo fisso. 

>Nota: in HoloLens 2, il cursore dello sguardo deve prima essere richiamato dicendo la parola "Select". Pronunciare di nuovo "Select" per l'attivazione. Per nascondere il cursore dello sguardo, è sufficiente usare le mani per AirTap o toccare un oggetto. 

### <a name="see-it-say-it"></a>Guarda, parla

Windows Mixed Reality ha usato un modello di comando vocale "guarda, parla" in cui le **etichette sui pulsanti sono identiche ai comandi vocali associati**. Poiché non esiste alcuna dissonanza tra l'etichetta e il comando vocale, gli utenti possono capire meglio cosa dire per controllare il sistema. Per maggiore chiarezza, soffermandosi su un pulsante, viene visualizzato un **"suggerimento vocale attesa"** per comunicare quali pulsanti vengono abilitati mediante comandi vocali.


![Esempio 1 per "guarda, parla"](images/voice-seeitsayit1-640px.jpg)

![Esempio 2 per "guarda, parla"](images/voice-seeitsayit2-640px.jpg)<br>
*Esempi di "guarda, parla"*

### <a name="voices-strengths"></a>Punti di forza dei comandi vocali

L'input vocale è un modo naturale di comunicare le intenzioni. La voce è particolarmente utile negli **attraversamenti** dell'interfaccia perché può aiutare gli utenti a tagliare più passaggi di un'interfaccia (un utente potrebbe "tornare indietro" guardando una pagina Web, anziché dover fare clic sul pulsante indietro nell'app). Questo piccolo risparmio di tempo ha un forte **effetto emotivo** sulla percezione dell'esperienza dell'utente e offre una piccola quantità di supervisione. I comandi vocali rappresentano anche un pratico metodo di input quando hai le mani occupate oppure quando sei in modalità **multitasking**. Nei dispositivi in cui la digitazione su una tastiera è difficile, la **Dettatura vocale** può essere un modo efficiente e alternativo per l'input. Infine, in alcuni casi, quando l' **intervallo di accuratezza** per lo sguardo e il movimento sono limitati, Voice potrebbe essere un metodo di input attendibile dell'utente.

**In che modo i comandi vocali possono rivelarsi utili per l'utente**
* Riducono i tempi: devono rendere l'obiettivo finale più efficiente.
* Riducono al minimo lo sforzo: devono rendere le attività più fluide e semplici.
* Riducono il carico cognitivo: sono intuitivi e facili da imparare e ricordare.
* Sono socialmente accettabili: devono essere conformi alle regole della società in termini di comportamento.
* Rappresentano la routine: i comandi vocali possono facilmente diventare un comportamento abituale.

### <a name="voices-weaknesses"></a>Svantaggi dei comandi vocali

I comandi vocali presentano anche alcuni svantaggi. Uno di essi è la granularità del controllo. ad esempio, un utente potrebbe dire "più forte", ma non può dire quanto. "Leggermente" è difficile da quantificare. Con i comandi vocali è difficile anche effettuare operazioni di spostamento o ridimensionamento (il comando vocale non offre la granularità del controllo). I comandi vocali possono anche essere imperfetti. In alcuni casi un sistema vocale percepisce in modo non corretto un comando o non lo percepisce affatto. Il ripristino da tali errori è un problema in qualsiasi interfaccia. Infine, i comandi vocali possono non essere socialmente accettabili nei luoghi pubblici. Esistono alcune cose che gli utenti non possono o non devono pronunciare. Queste considerazioni permettono di individuare gli scenari in cui i comandi vocali offrono risultati ottimali.

### <a name="voice-feedback-states"></a>Stati di feedback dei comandi vocali

Quando i comandi vocali vengono applicati in modo corretto, l'utente capisce **cosa può dire e ottiene un feedback chiaro** a indicare che il sistema ha **recepito correttamente i comandi**. Questi due segnali fanno sì che l'utente si senta sicuro di usare i comandi vocali come input principale. Di seguito è riportato un diagramma che illustra che cosa accade al cursore quando l'input vocale viene riconosciuto e come tale risultato viene comunicato all'utente.

![Stati di feedback dei comandi vocali per il cursore](images/voicefeedbackstates.png)<br>
*Stati di feedback dei comandi vocali per il cursore*

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a>Nozioni di base sui comandi vocali che gli utenti devono conoscere per la realtà mista
* Pronuncia **"Seleziona"** quando la destinazione è un pulsante. Puoi usare questo comando ovunque per fare clic su un pulsante.
* Puoi pronunciare il **nome dell'etichetta di un pulsante della barra dell'app** in alcune app per eseguire un'azione. Mentre guarda un'app, ad esempio, un utente può pronunciare il comando "Rimuovi" per rimuovere definitivamente l'app, senza dover fare clic su di essa con la mano e risparmiando così tempo.
* Puoi avviare l'ascolto da parte di Cortana dicendo **"Ehi Cortana"** . È possibile porre le proprie domande ("Hey Cortana, quanto è alta la Torre Eiffel?"), indicare di aprire un'app ("Hey Cortana, Open Netflix") o di visualizzare il menu Start ("Hey Cortana, Take Me Home") e altro ancora.

## <a name="common-questions-and-concerns-users-have-about-voice"></a>Domande e dubbi comuni degli utenti sui comandi vocali
* Cosa posso dire?
* Come posso sapere se il sistema mi ha capito correttamente?
   * Il sistema continua a interpretare i miei comandi vocali in modo errato.
   * Non reagisce quando pronuncio un comando vocale.
* Reagisce in modo non corretto quando pronuncio un comando vocale.
* Come posso indirizzare un comando vocale a una specifica app o un comando di app?
* Posso usare i comandi vocali per operazioni all'esterno del fotogramma olografico di HoloLens?

## <a name="see-also"></a>Vedi anche
* [Movimenti](gaze-and-commit.md#composite-gestures)
* [Puntamento con la testa e attesa](gaze-and-dwell.md)

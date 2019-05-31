---
title: L'esecuzione di comandi vocali
description: Sguardo, gesti e voce (GGV) sono un mezzo principale di interazione su HoloLens. Questo articolo fornisce indicazioni precise sulla progettazione vocali.
author: shentan
ms.author: shentan
ms.date: 04/21/2019
ms.topic: article
ms.localizationpriority: high
keywords: Realtà mista di Windows, progettazione, l'interazione vocale
ms.openlocfilehash: f2362400cba2946c3e97a7128c410ddcd17b4362
ms.sourcegitcommit: 5b4292ef786447549c0199003e041ca48bb454cd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/30/2019
ms.locfileid: "66402375"
---
# <a name="voice-commanding"></a>L'esecuzione di comandi vocali

Quando si usano i comandi vocali, sguardo viene in genere utilizzato come mechaninism targeting, sia come un puntatore ("select") o per indirizzare il comando a un'applicazione ("visualizzarlo, dice"). Naturalmente, alcuni comandi vocali non richiedono una destinazione, ad esempio "go to start" o "Hey, Cortana."


## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Funzionalità</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (dal 1 ° generazione)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></th>
</tr><tr>
<td>L'esecuzione di comandi vocali</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️ (con le cuffie collegata)</td>
</tr>
</table>



## <a name="how-to-use-voice"></a>Come usare la forma

È consigliabile aggiungere comandi vocali per alcuna esperienza che si compila. Voce è un modo pratico e potente di controllo del sistema e le app. Poiché gli utenti parlano con un'ampia gamma di dialetti e accenti, la scelta migliore delle parole chiave vocali garantirà che i comandi degli utenti vengano interpretati in modo non ambiguo.

### <a name="best-practices"></a>Procedure consigliate

Di seguito vengono illustrate alcune tecniche che contribuiranno a smooth riconoscimento vocale.
* **Usare i comandi concisi** : quando possibile, scegliere le parole chiave di due o più sillabe. Una sillaba parole tendono a utilizzare suoni vocali diversi pronuncia da persone con accenti diversi. Esempio: "Riproduci il video" è preferibile rispetto a "Guarda il video attualmente selezionato"
* **Usare vocabolario semplice** -esempio: "Show nota" è preferibile rispetto a "Show manifesto"
* **Assicurarsi che i comandi sono non distruttivi** : assicurarsi che sia non distruttive qualsiasi azione che può essere eseguite da un comando di riconoscimento vocale e può essere annullata facilmente in caso di un'altra persona che parla vicino all'utente accidentalmente attiva un comando.
* **Evitare i comandi di una voce simile** -evitare di registrare più comandi vocali che sembrare molto simili. Esempio: "Mostra più" e "Show store" può essere pronunciati in modo molto simile.
* **Annullare la registrazione all'app quando non usa** : quando l'app non è in uno stato in cui un comando di riconoscimento vocale specifico non è valido, è consigliabile annullarne la registrazione in modo che gli altri comandi non vengono confuse a quella.
* **Test con accenti diversi** -testare l'app con gli utenti di accenti diversi.
* **Mantenere la coerenza di comandi vocali** : se "Vai Indietro" passa alla pagina precedente, mantenere questo comportamento nelle applicazioni.
* **Evitare di usare i comandi del sistema** -comandi vocali seguenti sono riservati per il sistema. Non devono essere usati dalle applicazioni.
   * "Ehi Cortana"
   * "Select"

### <a name="select"></a>"Select"

Che indica che "select" in qualsiasi momento si attiverà qualunque sia il cursore sguardo punta a. 

>Nota: HoloLens 2, le esigenze di cursore sguardo prima di tutto necessario richiamare specificando la parola "select". Ad esempio, "selezionare" nuovo per l'attivazione. Per nascondere il cursore sguardo, usando le mani - airtap o un oggetto di tocco. 

### <a name="see-it-say-it"></a>Visualizzarlo, ad esempio

Realtà mista di Windows ha incaricato un modello di casella vocale "visualizzarlo, dice" dove **le etichette nei pulsanti sono identiche ai comandi vocali associato**. Poiché non c'è alcun dissonance tra l'etichetta e i comandi vocali, agli utenti di comprendere meglio cosa significa controllare il sistema. Per ribadire, mentre appartamento su un pulsante, un **"vocale permanenza suggerimento"** viene visualizzato per comunicare i pulsanti sono servizio voce abilitato.


![Vederlo dice esempio 1](images/voice-seeitsayit1-640px.jpg)

![Vederlo dice esempio 2](images/voice-seeitsayit2-640px.jpg)<br>
*Esempi di "visualizzarlo, dice"*

### <a name="voices-strengths"></a>Punti di forza del Voice

Input vocale è un modo semplice per comunicare l'Intent. Vocale è particolarmente efficaci per interfaccia **attraversamenti** perché ciò può aiutare gli utenti con serenità più passaggi di un'interfaccia (un utente potrebbe ad esempio "tornare" durante la ricerca nella pagina Web, invece di dover configurare e fare clic sul pulsante Indietro nell'app). Il risparmio di tempo piccola è una potente **effetto emotivo** utente di percezione dell'esperienza e fornisce a ognuna superpower una piccola quantità. Con voice è anche un pratico metodo di input quando si hanno i rami completi oppure sono **multitasking**. Nei dispositivi in cui è difficile, digitazione di una tastiera **vocali dettatura** può essere un'alternativa efficiente di input. Infine, in alcuni casi, quando la **intervallo di precisione** per sguardo e movimenti sono limitati, voce potrebbe essere un utente solo attendibili metodo di input.

**Come utilizzare voce possono trarre vantaggio all'utente**
* Riduce il tempo, si deve stabilire l'obiettivo finale più efficiente.
* Riduce al minimo impegno - si devono stabilire le attività più fluida e semplificata.
* Consente di ridurre il carico conoscitivo - è intuitive e facili da imparare e ricordare.
* Si tratta di socialmente accettabile: dovrebbe rappresentare con le norme in termini di comportamento.
* Le routine - vocale può facilmente diventare un comportamento abituale.

### <a name="voices-weaknesses"></a>Punti di debolezza del Voice

La voce presenta anche alcuni svantaggi. Controllo con granularità fine è uno di essi. (ad esempio un utente potrebbe essere indicato "più alto", ma non si può dire quanto. "Un piccolo" sia difficile quantificare. Lo spostamento o la scalabilità cose con vocale è anche difficile (vocale non offre la granularità di controllo). Vocale può anche essere perfetto. In alcuni casi un sistema vocale in modo non corretto ascolta un comando o ha esito negativo lieti di ricevere un comando. Il ripristino da tali errori è un problema in qualsiasi interfaccia. Infine, voce potrebbe non essere socialmente accettabile in luoghi pubblici. Esistono alcuni aspetti che gli utenti non possono o non devono pronunciare. Questi vegetazione consentono riconoscimento vocale da utilizzare per ciò che è consigliabile in.

### <a name="voice-feedback-states"></a>Stati di commenti e suggerimenti vocale

Quando voce viene applicata in modo corretto, l'utente capisca **cosa possono ad esempio e ottenere commenti e suggerimenti chiaro** il sistema **sentito dire loro correttamente**. Questi due segnali di impostare l'utente di sentirsi sicuri usando vocale come un input primari. Seguito è riportato un diagramma che illustra che cosa accade per il cursore quando l'input vocale riconosciuto e le modalità di comunicazione che all'utente.

![Stati di commenti e suggerimenti vocali per cursori](images/voicefeedbackstates.png)<br>
*Stati di commenti e suggerimenti vocali per cursori*

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a>Prime operazioni che gli utenti devono conoscere per "speech" nella realtà mista
* Pronunciare **"Selezionare"** durante l'assegnazione di un pulsante (è possibile usare questo ovunque fare clic su un pulsante).
* È possibile dire il **nome dell'etichetta di un pulsante della barra app** in alcune app di eseguire un'azione. Durante la ricerca in un'app, ad esempio, un utente può pronunciare il comando "Remove" per rimuovere l'app da tutto il mondo (Ciò consente di risparmiare tempo evitando il selezionarlo con mano).
* È possibile avviare Cortana in ascolto affermando **"Ehi Cortana".** È possibile porre suo domande ("Ehi Cortana, l'altezza è la Torre Eiffel"), dille di aprire un'app ("Ehi Cortana, open Netflix") o dille di visualizzare il Menu di avvio ("Ehi Cortana, take me home") e altro ancora.

## <a name="common-questions-and-concerns-users-have-about-voice"></a>Gli utenti di domande e dubbi più comuni hanno sulla voce
* Che cosa posso dire?
* Come si capisce che sistema sentito parlare a me correttamente?
   * Il sistema continua a mio comandi vocali errato.
   * Non reagisce quando si fa riferimento a un comando vocale.
* Quando si fa riferimento a un comando vocale reagisce in modo non corretto.
* Come applicare la voce da una specifica app o un comando di app?
* È possibile usare vocale per le operazioni di comando out frame holographic HoloLens?

## <a name="see-also"></a>Vedere anche
* [Movimenti](gestures.md)
* [Puntamento con la testa e attesa](gaze-and-dwell.md)

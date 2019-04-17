---
title: Scala
description: È una chiave per la visualizzazione di contenuto che cerca realistico nel modulo holographic per simulare le statistiche del mondo reale visual fedelmente possibile.
author: mavitazk
ms.author: mavitazk
ms.date: 03/21/2018
ms.topic: article
keywords: Progettazione di realtà mista di Windows, stile,
ms.openlocfilehash: f13414bff7d84692e8e87aa2abdcded15627346f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59598913"
---
# <a name="scale"></a>Scala

È una chiave per la visualizzazione di contenuto che cerca realistico nel modulo holographic per simulare le statistiche del mondo reale visual fedelmente possibile. Ciò significa che includa il numero dei segnali visivi come siamo in grado di aiutarci (nel mondo reale) comprendere dove gli oggetti sono, big data come sono e ciò che vengono apportate di. La scala di un oggetto è uno dei più importanti di tali segnali visivi, offrendo un visualizzatore un'idea delle dimensioni di un oggetto, nonché i suggerimenti alla posizione (soprattutto per gli oggetti che hanno una dimensione nota). Inoltre, la visualizzazione degli oggetti su larga scala reale è stata osservata come uno dei fattori di differenziazione esperienza per realtà mista, in genere – qualcosa che non è stato possibile su schermo la visualizzazione in precedenza.

## <a name="how-to-suggest-the-scale-of-objects-and-environments"></a>Come per i suggerimenti per la scala di oggetti e gli ambienti

Esistono diversi modi per suggerire la scala di un oggetto, alcuni dei quali sono i possibili effetti su altri fattori percettive. La più importante è semplicemente visualizzare gli oggetti di una dimensione di "reale" e mantengono tali dimensioni realistico come spostano gli utenti. Ciò significa vntana verrà occupano una quantità diversa di angolo visual dell'utente di un utente non appena si verificano più da vicino o ulteriormente fuori sede, simile a quello che si oggetti reali.

### <a name="utilize-the-distance-of-objects-as-they-are-presented-to-the-user"></a>Utilizzare la distanza degli oggetti di presentazione all'utente

Un metodo comune consiste nell'utilizzare la distanza degli oggetti di presentazione all'utente. Si consideri ad esempio un'automobile famiglia grande davanti all'utente la visualizzazione. Se l'automobile fosse direttamente davanti a essi, entro la lunghezza di arm, sarebbe troppo grande per il campo di vista dell'utente. Ciò richiede all'utente di spostare le testa e del corpo per comprendere l'intero dell'oggetto. Se l'auto sono stati concessi ulteriore assente (tutta la stanza), l'utente può stabilire un senso di scalabilità visualizzando l'intero dell'oggetto nel loro campo visivo, quindi se stessi avvicinando spostarsi su di essa per controllare le aree in modo dettagliato.

[Volvo](https://www.youtube.com/watch?v=DilzwF90vec) usato questa tecnica per creare un'esperienza sala per una nuova auto, che usano la scala dell'automobile holographic in modo ritenuto realistici e intuitivo per l'utente. L'esperienza inizia con un ologrammi dell'automobile in una tabella fisica, consentendo all'utente di comprendere le dimensioni totali del modello. In un secondo momento nell'esperienza, l'auto si espande in una scala più grande (oltre le dimensioni del campo visivo del dispositivo), ma, poiché l'utente è già acquisito un riferimento dal modello più piccolo, in modo adeguato è possibile spostarsi tra le funzionalità dell'automobile.

![Esperienza di automobili Volvo per HoloLens](images/volvo-cars-microsoft-hololens-experience01-640px.jpg)<br>
*Esperienza di automobili Volvo per HoloLens*

### <a name="use-holograms-to-modify-the-users-real-space"></a>Usare vntana per modificare lo spazio effettivo dell'utente

Un altro metodo consiste nell'usare vntana modificare spazio effettivo dell'utente, sostituendo le pareti o limiti esistenti con gli ambienti o l'aggiunta di 'fori' o 'windows', che consente di eccessivo oggetti apparentemente 'break-through' lo spazio fisico. Ad esempio, un albero di grandi dimensioni potrebbe non rientrare nella chat room living maggior parte degli utenti, ma posizionando un virtuale sky nella loro ceiling, lo spazio fisico si espande in virtuale. Ciò consente all'utente per spostarsi intorno alla base della struttura ad albero virtuale e raccogliere un senso di scala del modo in cui verrebbe vengono visualizzati in uno scenario reale, quindi cercare per visualizzarlo estenda notevolmente oltre lo spazio fisico della chat room.

[Minecraft](https://minecraft.net/) sviluppato un'esperienza di verifica usando una tecnica simile. Tramite l'aggiunta di una finestra virtuale a una superficie fisica in una stanza, gli oggetti esistenti nella chat room vengono inseriti nel contesto di un ambiente di dimensioni notevolmente maggiore, oltre i limiti di scalabilità fisica della chat room.

![Esperienza di verifica Minecraft per HoloLens](images/800px-minecraftwindow-640px.jpg)<br>
*Esperienza di verifica Minecraft per HoloLens*

## <a name="experimenting-with-scale"></a>Esperimenti con scala

In alcuni casi, le finestre di progettazione hanno sperimentato con la modifica della scala (modificando le dimensioni visualizzate 'reale' dell'oggetto) pur mantenendo una posizione singola dell'oggetto, per simulare un oggetto ricevono più vicino o ulteriormente per un visualizzatore senza alcuno spostamento effettivo. Questo è stato testato in alcuni casi un modo per simulare i dettagli sulla visualizzazione degli elementi rispettando comunque potenziali limitazioni comodità di visualizzazione virtuale contenuto più vicino quanto suggerito "area del Data Center".

Ciò può tuttavia creare alcuni elementi possibili nell'esperienza di:
* Per gli oggetti virtuali che rappresentano un oggetto con una dimensione 'nota' al visualizzatore, modificare la scalabilità senza la modifica della posizione comporta segnali visivi in conflitto: gli occhi possono comunque '' l'oggetto visualizzato alcune profondità a causa di segnali vergence (vedere il [fattore di Comfort ](comfort.md) per altre informazioni su questo articolo), ma le dimensioni agisce come un segnale monoculare che l'oggetto potrebbe essere avvicinandosi. Questi segnali in conflitto causare percezioni confuse: l'oggetto visualizzatori spesso visualizzeranno come rimanendo nella posizione (a causa di costante di profondità), ma in rapida crescita.
* In alcuni casi, modifica della scala viene considerata come un'indicazione 'looming', invece, in cui l'oggetto può o non può essere visualizzato per modificare la scala da un visualizzatore, ma sembra essere passando direttamente a occhi del visualizzatore (che possono essere un successo all'improvviso spiacevole).
* Con le superfici di confronto nel mondo reale, tali modifiche di ridimensionamento vengono a volte usati in Modifica posizione lungo più assi: gli oggetti potrebbero apparire per eliminare più basso anziché spostare più vicino (simile nella proiezione 2D di movimento 3D in alcuni casi).
* Infine, per gli oggetti senza una dimensione noti "real world" (impatto su forme arbitrarie, ad esempio con dimensioni arbitrari, elementi dell'interfaccia utente e così via), la modifica di scala può operare a livello funzionale che consente di simulare le modifiche in termini di distanza: visualizzatori non hanno tutti i segnali dall'alto in basso preesistenti da cui comprendere true dimensioni dell'oggetto o il percorso, in modo che la scala può essere elaborata come un'indicazione più importante.

## <a name="see-also"></a>Vedere anche
* [Colore, chiaro e materiali](color,-light-and-materials.md)
* [Typography](typography.md)
* [Progettazione spaziale](spatial-sound-design.md)

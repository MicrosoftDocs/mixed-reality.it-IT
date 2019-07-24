---
title: Scalabilità
description: Una chiave per la visualizzazione di contenuto che sembra realistico in forma olografica consiste nel simulare il più possibile le statistiche visive del mondo reale.
author: mavitazk
ms.author: mavitazk
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, stile, progettazione
ms.openlocfilehash: f13414bff7d84692e8e87aa2abdcded15627346f
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524102"
---
# <a name="scale"></a>Scalabilità

Una chiave per la visualizzazione di contenuto che sembra realistico in forma olografica consiste nel simulare il più possibile le statistiche visive del mondo reale. Ciò significa che l'integrazione di tutti i segnali visivi, come possiamo aiutarci (nel mondo reale) a capire dove si trovano gli oggetti, quanto è grande e cosa ne fanno. La scala di un oggetto è uno dei più importanti dei segnali visivi, offrendo a un visualizzatore un senso della dimensione di un oggetto, nonché i segnali alla relativa posizione, in particolare per gli oggetti con dimensioni note. Inoltre, la visualizzazione di oggetti su scala reale è stata considerata come uno dei principali elementi di differenziazione per la realtà mista in generale, un elemento che non è stato possibile visualizzare in precedenza sullo schermo.

## <a name="how-to-suggest-the-scale-of-objects-and-environments"></a>Come suggerire la scala di oggetti e ambienti

Esistono diversi modi per suggerire la scala di un oggetto, alcuni dei quali hanno possibili effetti su altri fattori percettivi. La chiave consiste nel visualizzare semplicemente gli oggetti con dimensioni reali e mantenerne le dimensioni realistiche quando gli utenti si spostano. Ciò significa che gli ologrammi prenderanno una quantità diversa di un angolo visivo dell'utente di un utente man mano che si avvicinano o si riferiscono allo stesso modo degli oggetti reali.

### <a name="utilize-the-distance-of-objects-as-they-are-presented-to-the-user"></a>Utilizzare la distanza degli oggetti presentati all'utente

Un metodo comune prevede l'utilizzo della distanza degli oggetti presentati all'utente. Si consideri, ad esempio, la visualizzazione di un'auto famiglia di grandi dimensioni davanti all'utente. Se la vettura si trovava direttamente davanti ad esse, entro la lunghezza di ARM, sarebbe troppo grande per il campo di visualizzazione dell'utente. In questo modo l'utente dovrà spostare la testa e il corpo per comprendere l'intero oggetto. Se la macchina è stata posizionata più a lungo (attraverso la stanza), l'utente può stabilire un senso di ridimensionamento visualizzando l'intero oggetto nel campo di visualizzazione, quindi ci si sposta più vicino per esaminare le aree in dettaglio.

[Volvo](https://www.youtube.com/watch?v=DilzwF90vec) usa questa tecnica per creare un'esperienza di showroom per una nuova macchina, usando la scalabilità dell'automobile olografica in modo da essere realistica e intuitiva per l'utente. L'esperienza inizia con un ologramma dell'auto in una tabella fisica, consentendo all'utente di comprendere la dimensione e la forma totali del modello. Successivamente, l'auto si espande fino a una scala più ampia (oltre le dimensioni del campo di visualizzazione del dispositivo), ma poiché l'utente ha già acquisito un frame di riferimento dal modello più piccolo, può spostarsi in modo adeguato sulle funzionalità dell'auto.

![Esperienza Volvo Cars per HoloLens](images/volvo-cars-microsoft-hololens-experience01-640px.jpg)<br>
*Esperienza Volvo Cars per HoloLens*

### <a name="use-holograms-to-modify-the-users-real-space"></a>Usare gli ologrammi per modificare lo spazio reale dell'utente

Un altro metodo consiste nell'usare gli ologrammi per modificare lo spazio reale dell'utente, sostituendo i muri o i soffitti esistenti con gli ambienti o accodando "buchi" o "finestre", consentendo a oggetti di dimensioni superiori di "interrompere" lo spazio fisico. Un albero di grandi dimensioni, ad esempio, potrebbe non rientrare nella maggior parte dei salotti degli utenti, ma mettendo un cielo virtuale sul soffitto, lo spazio fisico si espande nel computer virtuale. In questo modo, l'utente può aggirare la base dell'albero virtuale e raccogliere un senso di scalabilità di come verrebbe visualizzato nella vita reale, quindi cercare di estenderlo oltre lo spazio fisico della stanza.

[Minecraft](https://minecraft.net/) ha sviluppato un'esperienza concettuale usando una tecnica simile. Aggiungendo una finestra virtuale a una superficie fisica in una stanza, gli oggetti esistenti nella stanza vengono posizionati nel contesto di un ambiente notevolmente più ampio, oltre i limiti della scala fisica della stanza.

![Esperienza del concetto Minecraft per HoloLens](images/800px-minecraftwindow-640px.jpg)<br>
*Esperienza del concetto Minecraft per HoloLens*

## <a name="experimenting-with-scale"></a>Sperimentazione con scalabilità

In alcuni casi, le finestre di progettazione hanno sperimentato la modifica della scala (modificando le dimensioni "reali" visualizzate dell'oggetto) mantenendo una singola posizione dell'oggetto, per approssimare l'avvicinamento di un oggetto a un visualizzatore senza alcuno spostamento effettivo. Questa operazione è stata testata in alcuni casi come un modo per simulare la visualizzazione di elementi più vicini, rispettando al contempo le potenziali limitazioni di comfort della visualizzazione di contenuto virtuale più vicino alla "zona di comfort" suggerita.

Questa operazione può tuttavia creare alcuni artefatti possibili nell'esperienza:
* Per gli oggetti virtuali che rappresentano un oggetto con una dimensione "nota" al visualizzatore, la modifica della scala senza modificare la posizione comporta segnali visivi in conflitto. gli occhi possono comunque "vedere" l'oggetto a una certa profondità a causa di segnali vergence (vedere la [comodità](comfort.md) Per ulteriori informazioni su questo argomento, ma la dimensione funge da spunto monoculare che l'oggetto potrebbe avvicinarsi. Questi segnali in conflitto portano a percezioni confuse: i visualizzatori spesso visualizzano l'oggetto che rimane sul posto (a causa del segnale di profondità costante), ma cresce rapidamente.
* In alcuni casi, la modifica della scala viene invece considerata come una cue "incombente", in cui l'oggetto può essere visualizzato o meno per modificare la scala da un visualizzatore, ma sembra essere spostato direttamente verso gli occhi del visualizzatore, che può essere una sensazione scomoda.
* Con le aree di confronto nel mondo reale, tali modifiche di ridimensionamento vengono talvolta considerate come la modifica della posizione lungo più assi. gli oggetti possono sembrare ridotti anziché essere più vicini (simili in una proiezione 2D di spostamento 3D in alcuni casi).
* Infine, per gli oggetti senza una dimensione nota ' reale ' (ad esempio, forme arbitrarie con dimensioni arbitrarie, elementi dell'interfaccia utente e così via), la modifica della scala può agire dal punto di vista funzionale come un modo per simulare le modifiche a distanza. i visualizzatori non hanno il numero di suggerimenti dall'alto verso il basso preesistenti per i quali comprendere le dimensioni o la posizione dell'oggetto, in modo che la scala possa essere elaborata come una cue più importante.

## <a name="see-also"></a>Vedere anche
* [Colore, luce e materiali](color,-light-and-materials.md)
* [Tipografia](typography.md)
* [Progettazione dell'audio spaziale](spatial-sound-design.md)

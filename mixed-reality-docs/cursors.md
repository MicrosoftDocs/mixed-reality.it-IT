---
title: Cursori
description: Un cursore, o un indicatore del vettore di destinazione, fornisce un feedback continuo all'utente per comprendere quali sono le intenzioni di HoloLens.
author: thetuvix
ms.author: alexturn, thgable
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens (1a generazione), HoloLens 2, realtà mista, cursori, targeting, sguardi, movimenti
ms.openlocfilehash: cdedcaffabe0f90e7956fdb19a7b85e202fcf403
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63526211"
---
# <a name="cursors"></a>Cursori

> [!NOTE]
> Altre indicazioni specifiche per HoloLens 2 [saranno presto](index.md#news-and-notes)disponibili.


Un cursore, o un indicatore del vettore di destinazione corrente, fornisce un feedback continuo all'utente per comprendere dove HoloLens ritiene che la sua attenzione attuale sia in quel momento. Il cursore consente all'utente di comprendere il punto di destinazione corrente e funge da feedback per indicare quale area, ologramma o punto risponderà all'input. Si tratta della rappresentazione digitale del punto in cui il dispositivo è in grado di comprendere l'attenzione dell'utente (anche se ciò potrebbe non essere uguale a quello di determinare le proprie intenzioni).

Il feedback fornito dal cursore offre agli utenti la possibilità di prevedere il modo in cui il sistema risponderà, utilizzare tale segnale come feedback per comunicare meglio la loro intenzione al dispositivo e, infine, avere maggiore fiducia sulle interazioni.

## <a name="hololens-1st-gen"></a>HoloLens (prima generazione)

Il targeting del contenuto in HoloLens (1st Gen) viene eseguito principalmente con lo [sguardo](gaze.md) Vector (un raggio controllato dalla posizione e dalla rotazione della testa). In questo modo viene fornito un tipo di input diretto per l'utente che necessita di un breve insegnamento. Tuttavia, gli utenti hanno difficoltà a usare un centro di sguardi non contrassegnato per la destinazione precisa, quindi un cursore garantisce agli utenti la certezza del punto in cui sono attualmente destinati. 


## <a name="positioning"></a>Posizionamento

In generale, l'indicatore deve spostarsi approssimativamente in un rapporto di 1:1 con lo spostamento della testa. Ci sono alcuni casi in cui il guadagno (aumento o riduzione dei movimenti è notevolmente evidente) può essere usato come un meccanico intenzionale, ma causerà problemi per gli utenti se usati in modo imprevisto (si noti che esiste un piccolo po' di "lag" consigliato per il cursore per evitare problemi con contenuto con blocco completo dello schermo). In particolare, tuttavia, le esperienze dovrebbero essere "onesti" nella rappresentazione della posizione del cursore: se sono inclusi smussamenti, magnetismo, guadagno o altri effetti, il sistema dovrebbe ancora mostrare il cursore laddove il sistema è in grado di individuare la posizione, con tali informazioni effetti inclusi. Il cursore è il modo in cui gli utenti possono o non possono interagire con il sistema, ma non il modo in cui l'utente comunica al sistema.

L'indicatore dovrebbe idealmente bloccare in modo approfondito tutti gli elementi che l'utente può raggiungere in modo plausibile. Questo può comportare un blocco di superficie se è presente una mesh di [mapping spaziale](spatial-mapping.md) o un blocco alla profondità di qualsiasi elemento dell'interfaccia utente "mobile", per consentire all'utente di comprendere il modo in cui è possibile interagire in tempo reale.

## <a name="cursor-design-principles"></a>Principi di progettazione del cursore

### <a name="always-present"></a>Sempre presente
* È consigliabile che il cursore sia sempre presente.
* Se l'utente non riesce a trovare il cursore, andrà perso.
* Le eccezioni a questo comportamento sono istanze in cui un cursore fornisce un'esperienza non ottimale per l'utente. Un esempio è quando un utente guarda un video. A questo punto, il cursore diventa indesiderato perché si trova al centro del video continuamente. Si tratta di uno scenario in cui è possibile rendere il cursore visibile solo quando l'utente ha la possibilità di eseguire un'azione. In caso contrario, non è visibile nel video.

### <a name="cursor-scale"></a>Scala del cursore
* Il cursore non deve essere più grande delle destinazioni disponibili, consentendo agli utenti di interagire con facilità e di visualizzare il contenuto.
* A seconda dell'esperienza creata, il ridimensionamento del cursore mentre l'utente si trova è anche una considerazione importante. Se, ad esempio, l'utente è in grado di ottenere un'ulteriore esperienza nell'esperienza, il cursore non dovrebbe diventare troppo piccolo in modo che sia perduto.
* Quando si ridimensiona il cursore, prendere in considerazione l'applicazione di un'animazione soft in modo da ridimensionare un sentimento organico.
* Evitare di ostacolare il contenuto. Gli ologrammi sono gli elementi che rendono memorabile l'esperienza e il cursore non dovrebbe allontanarsi da essi.

### <a name="directionless-cursor"></a>Cursore direzionale
* Sebbene non esista una forma di cursore a destra, è consigliabile usare una forma senza direzione, ad esempio torus o qualcos'altro. Un cursore che punta in una direzione (ad esempio, un cursore a freccia tradizionale) potrebbe confondere l'utente in modo che sia sempre simile.
* Un'eccezione è rappresentata dall'utilizzo del cursore per la comunicazione dell'istruzione di interazione con l'utente. Ad esempio, quando si ridimensionano gli ologrammi nella shell olografica di Windows, il cursore include temporaneamente frecce che consentono di indicare all'utente come spostare la mano per ridimensionare l'ologramma.

### <a name="look-and-feel"></a>Aspetto
* Un cursore a forma di ciambella o Toro è adatto a una grande quantità di applicazioni.
* Selezionare un colore e una forma che rappresenti al meglio l'esperienza che si sta creando.
* I cursori sono particolarmente soggetti alla [separazione dei colori](hologram-stability.md#color-separation).
* Un piccolo cursore con opacità bilanciata mantiene informativo senza dominare la gerarchia visiva.
* Tenere presente che l'uso di ombre o evidenziazioni dietro il cursore potrebbe ostacolare il contenuto e distrarre dallo scopo.
* I cursori devono essere allineati e abbracciare le superfici nell'app, in modo da dare all'utente la sensazione che il sistema sia in grado di individuare il punto in cui stanno cercando, ma anche che il sistema sia in grado di riconoscere l'ambiente.
* Nel sistema operativo Windows olografico, ad esempio, il cursore è allineato alle superfici del mondo dell'utente, creando una sensazione di consapevolezza del mondo anche quando l'utente non guarda direttamente un ologramma.
* Blocco magnetico del cursore a un elemento interattivo quando si trova in prossimità. In questo modo è possibile migliorare la sicurezza che l'utente interagirà con tale elemento quando eseguirà un'azione di selezione.

### <a name="visual-cues"></a>Segnali visivi
* Nel nostro mondo sono disponibili numerose informazioni e con ologrammi stiamo aggiungendo altre informazioni. Un cursore è un ottimo modo per comunicare all'utente ciò che è importante.
* Se l'esperienza è incentrata su un solo ologramma, il cursore può allinearsi e abbracciare solo tale ologramma e modificare la forma quando si guarda l'ologramma. Ciò può comportare all'utente che l'ologramma è speciale e può interagire con esso.
* Se l'applicazione usa il mapping spaziale, il cursore potrebbe allinearsi e abbracciare ogni superficie che vede. In questo modo viene fornito un feedback agli utenti che HoloLens e l'applicazione possono visualizzare il proprio spazio.
* Questi elementi contribuiscono a rafforzare il fatto che gli ologrammi sono reali e in tutto il mondo. Contribuiscono a colmare il divario tra il reale e il virtuale.
* Avere un'idea di cosa deve fare il cursore quando non sono presenti ologrammi o superfici in visualizzazione. Il posizionamento a una distanza predeterminata davanti all'utente è un'opzione.

## <a name="cursor-feedback"></a>Feedback del cursore

Come è stato affermato, è consigliabile fare in modo che il cursore sia sempre presente, in quanto è possibile utilizzare il cursore per fornire alcune informazioni importanti.

### <a name="possible-actions"></a>Azioni possibili
* Quando l'utente sta osservando un ologramma e il cursore si trova su tale ologramma, è possibile usare il cursore per fornire le azioni possibili su tale ologramma.
* È possibile visualizzare un'icona sul cursore che l'utente può, ad esempio, acquistare l'elemento o ridimensionare l'ologramma. O anche un elemento semplice come l'ologramma può essere utilizzato.
* Aggiungere al cursore informazioni aggiuntive solo se significa qualcosa per l'utente. In caso contrario, gli utenti potrebbero non osservare le modifiche dello stato o essere confuse dal cursore.

### <a name="input-state"></a>Stato input
* È possibile utilizzare il cursore per visualizzare lo stato di input dell'utente. Ad esempio, è possibile visualizzare un'icona che informa l'utente se il sistema rileva lo stato della mano. In questo modo si indica all'utente che l'utente è pronto a eseguire un'azione.
* È anche possibile usare il cursore per fare in modo che l'utente sappia che è disponibile un comando Voice. Oppure è possibile modificare momentaneamente il colore del cursore per indicare all'utente che il comando vocale è stato udito dal sistema.

Questi diversi Stati del cursore possono essere implementati in modi diversi. È possibile implementare questi stati diversi modellando il cursore come una macchina a Stati. Ad esempio:
* Lo stato di inattività è il punto in cui viene visualizzato il cursore predefinito.
* Lo stato pronto è quando è stata rilevata la mano dell'utente nella posizione pronta.
* Lo stato di interazione è quando l'utente sta eseguendo una particolare interazione.
* Lo stato delle azioni possibili è quando si conferiscono azioni possibili che possono essere eseguite su un ologramma.

È anche possibile implementare questi stati in modo che sia possibile visualizzare risorse dell'arte diverse quando vengono rilevati stati diversi.

## <a name="going-cursor-free"></a>"Senza cursore"

La progettazione senza cursore è consigliata solo quando il senso di immersione è un componente chiave di un'esperienza e le interazioni che coinvolgono la destinazione (tramite sguardo e movimento) non richiedono una grande precisione. È necessario che il sistema soddisfi le esigenze normalmente soddisfatte da un cursore, offrendo agli utenti un feedback continuo sulla comprensione del sistema di destinazione e aiutandoli a comunicare in modo sicuro le proprie intenzioni al sistema. Questo può essere raggiungibile attraverso altre modifiche di stato evidenti.

## <a name="see-also"></a>Vedere anche
* [Movimenti](gestures.md)
* [Selezione della destinazione con lo sguardo](gaze-targeting.md)

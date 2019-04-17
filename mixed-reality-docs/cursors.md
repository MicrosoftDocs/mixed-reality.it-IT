---
title: Cursori
description: Un cursore o indicatore del vettore di targeting, fornisce un feedback continuo all'utente di comprendere cosa HoloLens riconosce sulle intenzioni.
author: thetuvix
ms.author: alexturn, thgable
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens (dal 1 ° generazione), 2 HoloLens, realtà mista, cursori, targeting, sguardo, gesti
ms.openlocfilehash: cdedcaffabe0f90e7956fdb19a7b85e202fcf403
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604659"
---
# <a name="cursors"></a>Cursori

> [!NOTE]
> Altre indicazioni specifiche su 2 HoloLens [presto](index.md#news-and-notes).


Un cursore o indica la destinazione oggetto vector corrente, fornisce un feedback continuo all'utente di capire dove HoloLens ritiene che concentrino le loro attività è in quel momento. Il cursore consente all'utente di comprendere la destinazione corrente scegliere e si comporta come commenti e suggerimenti per indicare quale area, ologrammi o punto di rispondere alla richiesta di input. La firma digitale è rappresentazione di in cui il dispositivo riconosce l'attenzione dell'utente sia (ma che potrebbe non essere quello utilizzato per determinare alcun dettaglio relativo le intenzioni).

I commenti e suggerimenti forniti dal cursore offre agli utenti la possibilità di prevedere la modalità di risposta il sistema, usare tale segnale come commenti e suggerimenti per migliorare la comunicazione dell'intenzione di dispositivo e infine essere più sicuri sulle relative interazioni.

## <a name="hololens-1st-gen"></a>HoloLens (dal 1 ° generazione)

Destinazione del contenuto su HoloLens (dal 1 ° generazione) viene eseguita principalmente con il [estasiati](gaze.md) vettore (un raggio controllato dalla posizione e la rotazione dell'intestazione). Ciò fornisce un modulo di input diretto per l'utente che necessita di insegnamento poco. Tuttavia, gli utenti hanno difficoltà nell'utilizzare un centro di sguardo non contrassegnato per la destinazione precisa in modo che un cursore assicura gli utenti conoscono il punto di destinazione che si sta creando. 


## <a name="positioning"></a>Posizionamento

In generale, l'indicatore dovrebbe spostare in circa un rapporto 1:1 con movimento della testina. In alcuni casi in cui guadagno (aumento o riduzione dello spostamento notevolmente) può essere usato come un meccanico intenzionale, ma causerà problemi per gli utenti se utilizzato in modo imprevisto (si noti che esiste un po' di 'lag' consigliata per evitare problemi con il cursore completamente bloccato visualizzazione contenuto). Ancora più importante, tuttavia, esperienze devono essere "onesti" nella rappresentazione della posizione del cursore - se la smussatura, campi, magnetici guadagno, o altri effetti sono inclusi, il sistema deve comunque visualizzata con il cursore ovunque sia comprensione del sistema della posizione, con quelli effetti inclusi. Il cursore è modo di sistema che informa l'utente è possibile o non è possibile interagire con, non il suo metodo indica al sistema.

L'indicatore idealmente deve bloccare in modo approfondito a qualunque elementi plausibly può fare riferimento all'utente. Questo può significare blocco a livello di area se qualche [Mapping spaziale](spatial-mapping.md) mesh o il blocco per la profondità degli elementi dell'interfaccia utente "mobili", per consentire all'utente di comprendere cosa possono interagirvi in tempo reale.

## <a name="cursor-design-principles"></a>Principi di progettazione di cursore

### <a name="always-present"></a>Sempre presente
* È consigliabile che il cursore è sempre presente.
* Se l'utente non è stato trovato il cursore, vengono infatti perse.
* Eccezioni sono le istanze con un cursore in cui fornisce un'esperienza ottimale per l'utente. Un esempio è quando un utente è guardare un video. Il cursore diventa indesiderato a questo punto perché si trova all'interno del video continuamente. Questo è uno scenario in cui si potrebbe prendere in considerazione il cursore è visibile solo quando l'utente ha le mani che indica il desiderio di intervenire. In caso contrario, non visibile sul video.

### <a name="cursor-scale"></a>Scalabilità del cursore
* Il cursore deve essere non superiore le destinazioni disponibili, che consente agli utenti di interagire con facilità e visualizzare il contenuto.
* A seconda dell'esperienza che si crea, la scalabilità del cursore come l'utente cerca è anche importante tenere in considerazione. Ad esempio, come l'utente cerca ulteriore away durante l'utilizzo forse il cursore non deve diventare troppo piccolo in modo che la perdita.
* Quando si ridimensiona il cursore, è consigliabile applicare un'animazione trasferibili ad esso durante il ridimensionamento assegnandogli un sentimento organica.
* Evitare ostruendo contenuto. Ologrammi sono ciò che rende facile da ricordare l'esperienza e il cursore non deve assumere lontano da essi.

### <a name="directionless-cursor"></a>Cursore privo di direzione
* Anche se non è disponibile alcuna forma di cursore appropriato in uno, è consigliabile utilizzare una forma privo di direzione, ad esempio un torus o qualcos'altro. Un cursore che punta nella direzione alcune (ad esempio: un cursore a freccia tradizionali) potrebbe confondere l'utente a sempre lo stesso aspetto.
* Un'eccezione è quando si utilizza il cursore per comunicare istruzioni interazione all'utente. Ad esempio, quando si ridimensiona vntana nella shell di Windows Holographic, il cursore include temporaneamente le frecce che consentono di indicare agli utenti su come spostare le mani di scalare l'ologramma.

### <a name="look-and-feel"></a>Aspetto
* Un grafico ad anello o torus la forma di funzionamento del cursore per molte applicazioni.
* Selezionare un colore e alla forma che meglio rappresenta l'esperienza che si sta creando.
* I cursori sono particolarmente soggetti a [la separazione dei colori](hologram-stability.md#color-separation).
* Un cursori di dimensioni ridotte con opacità bilanciato mantiene il sistema informativo senza che dominano la gerarchia visiva.
* Tenere conto del fatto dell'uso ombre o luci dietro il cursore che potrebbero ostacolare il contenuto e si distaccherà dallo scopo.
* I cursori devono allineare a e segui le superfici nell'app, ciò fornirà all'utente un'idea di che il sistema può visualizzare in cui si sta cercando, ma anche che il sistema è a conoscenza della loro ambiente circostante.
* Ad esempio, del sistema operativo Windows Holographic, il cursore viene allineato alle superfici del mondo dell'utente, la creazione di un sentimento di consapevolezza del mondo, anche quando l'utente non è esaminando direttamente ologramma...
* Schermatura bloccando il cursore da un elemento interattivo quando è all'interno di prossimità. Questo può migliorare la fiducia che l'utente interagisce con quell'elemento quando eseguono un'azione di selezione.

### <a name="visual-cues"></a>Segnali visivi
* È presente un numerose informazioni in questo mondo e con vntana che stiamo aggiungendo altre informazioni. Un cursore è un ottimo modo per comunicare all'utente ciò che è importante.
* Se l'esperienza è incentrata su un singolo ologrammi, quindi forse il cursore viene allineato e scatti solo che ologrammi e le modifiche per la forma quando si esaminano lontano da tale ologramma. Ciò può indicare all'utente che l'ologrammi sono speciali e possono interagire con esso.
* Se l'applicazione Usa mapping spaziale, il cursore è stato possibile allineare e adattarli a ogni area che rileva. In questo modo commenti e suggerimenti degli utenti che HoloLens e l'applicazione può visualizzare il relativo spazio.
* Queste operazioni consentono di evidenziare il fatto che vntana è reali e nel mondo. Consentono di colmare il divario tra reali e virtuali.
* Hai un'idea di cosa deve fare il cursore quando non esistono vntana o superfici nella visualizzazione. Posizionarla a una distanza predeterminata davanti all'utente è una delle opzioni.

## <a name="cursor-feedback"></a>Risposta del cursore

Come già accennato, è buona norma disporre del cursore sia sempre presente, come è possibile usare il cursore per trasmettere alcune situazioni importanti informazioni.

### <a name="possible-actions"></a>Azioni possibili
* Quando l'utente è gazing in ologramma e il cursore si trova in tali ologrammi, è possibile usare il cursore per indicare le possibili azioni su tale ologramma.
* È possibile visualizzare un'icona sul cursore che l'utente può acquistare, ad esempio elementi o forse scalabili che ologramma. O anche qualcosa di semplice, ad esempio può essere tocca l'ologramma.
* Aggiungere informazioni aggiuntive sul cursore solo se ciò significa che un elemento all'utente. In caso contrario, gli utenti potrebbero essere non si noti che i cambiamenti di stato o si confondano dal cursore.

### <a name="input-state"></a>Stato di input
* È possibile utilizzare il cursore per visualizzare lo stato di input dell'utente. Ad esempio, è possibile visualizzare un'icona segnala all'utente se il sistema rileva il relativo stato di disponibilità. Ciò indicherà all'utente che l'applicazione conosca che l'utente è pronto a intervenire.
* Inoltre, è possibile utilizzare il cursore per migliorare il sapere che è disponibile un comando vocale dell'utente. O eventualmente modificare il colore del cursore momentaneamente per informare l'utente che il comando vocale è stato segnalato dal sistema.

Questi stati diversi del cursore possono essere implementati in modi diversi. È possibile implementare questi stati diversi dalla modellazione del cursore, ad esempio una macchina a stati. Ad esempio: 
* Stato di inattività viene visualizzato il cursore predefinito.
* Stato pronto è quando si rileva la mano dell'utente nella posizione pronta.
* Lo stato di interazione è quando l'utente sta eseguendo un determinato tipo di interazione.
* Lo stato di possibili azioni è quando si forniscono possibili azioni che possono essere eseguite su ologramma.

È anche possibile implementare questi stati in maniera in grado di interfaccia in modo che sia possibile visualizzare gli asset grafici diversi quando vengono rilevati diversi stati.

## <a name="going-cursor-free"></a>Passare a "privi di cursore"

Progettazione senza un cursore è consigliata solo quando il senso di full immersion è un componente fondamentale di un'esperienza e le interazioni che coinvolgono targeting (tramite sguardo e movimento) non richiedono estremamente precisa. Il sistema deve soddisfare le esigenze per cui vengono in genere soddisfatte da un cursore tuttavia - fornisce feedback continuo nella comprensione del sistema del loro destinate a utenti e aiutarli a comunicare in tutta sicurezza le intenzioni al sistema. Può trattarsi ottenibile tramite altre modifiche di stato notevole.

## <a name="see-also"></a>Vedere anche
* [Movimenti](gestures.md)
* [Sguardo targeting](gaze-targeting.md)

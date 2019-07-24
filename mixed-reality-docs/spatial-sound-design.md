---
title: Progettazione di suoni spaziali
description: Il suono spaziale è uno strumento potente per l'immersione, l'accessibilità e la progettazione dell'esperienza utente nelle applicazioni di realtà mista.
author: joekellyms
ms.author: joekelly
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, audio spaziale, progettazione, stile
ms.openlocfilehash: c758037300392d9365c16933677fb0f026976c2a
ms.sourcegitcommit: c2a5bff423feba7d29d5431c870b6017c2fe1bc2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/06/2019
ms.locfileid: "66750308"
---
# <a name="spatial-sound-design"></a>Progettazione di suoni spaziali

Il suono spaziale è uno strumento potente per l'immersione, l'accessibilità e la progettazione dell'esperienza utente nelle applicazioni di realtà mista.

Se hai già interpretato [Marco Polo](https://en.wikipedia.org/wiki/Marco_Polo_(game))o qualcuno ha chiamato il tuo telefono per aiutarti a individuarlo, hai già familiarità con l'importanza del suono spaziale. Si usano segnali acustici nella nostra vita quotidiana per individuare gli oggetti, ottenere l'attenzione di un utente o ottenere una migliore comprensione dell'ambiente. Maggiore è il comportamento dell'app, come nel mondo reale, più convincente e coinvolgente sarà il mondo virtuale.

<br>

> [!VIDEO https://www.youtube.com/embed/aB3TDjYklmo]

## <a name="device-support"></a>Supporto di dispositivi

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Funzionalità</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
    </tr>
     <tr>
        <td>Progettazione di suoni spaziali</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>


## <a name="four-key-things-spatial-sound-does-for-mixed-reality-development"></a>Quattro elementi chiave del suono spaziale per lo sviluppo di realtà mista

Per impostazione predefinita, i suoni vengono riprodotti in stereo. Ciò significa che il suono verrà riprodotto senza alcuna posizione spaziale, quindi l'utente non sa da dove proviene il suono. Il suono spaziale esegue quattro operazioni fondamentali per lo sviluppo di realtà miste:

**Terra**

Senza suono, gli oggetti virtuali cessano di esistere in modo efficace quando si trasformano i passi da essi. Analogamente agli oggetti reali, si desidera essere in grado di ascoltare questi oggetti anche quando non è possibile visualizzarli e si desidera essere in grado di individuarli ovunque si trovino. Così come gli oggetti virtuali devono essere considerati come oggetti visivi per fondersi con il mondo reale, è anche necessario avere un sistema di base. Il suono spaziale integra in modo semplice l'ambiente audio reale con l'ambiente audio digitale.

**Attenzione dell'utente**

In situazioni di realtà mista, non è possibile presupporre il punto in cui l'utente sta cercando e si aspetta che venga visualizzata un'immagine che viene collocata in tutto il mondo. Tuttavia, gli utenti possono sempre ascoltare una riproduzione audio anche quando l'oggetto che riproduce il suono è dietro di essi. Gli utenti vengono usati per attirare l'attenzione su un oggetto che ci siamo avvicinati. Quando si desidera indirizzare l'utente a una posizione specifica, anziché utilizzare una freccia per puntare visivamente, inserire un suono in tale posizione è un modo molto naturale e rapido per guidarli.

**Full immersion per**

Quando gli oggetti si spostano o entrano in collisione, in genere si sentono tali interazioni tra i materiali. Quindi, quando gli oggetti non hanno lo stesso suono nel mondo reale, un livello di immersione viene perso, ad esempio guardando un film spaventoso con il volume fino a questo punto. Tutti i suoni nel mondo reale derivano da un particolare punto nello spazio. quando si trasformano le nostre teste, viene rilevata la modifica del modo in cui provengono i suoni rispetto alle orecchie ed è possibile tenere traccia della posizione di qualsiasi suono in questo modo. I suoni spaziali costituiscono la "sensazione" di una posizione superiore a quella che è possibile vedere.

**Progettazione interazione**

Nella maggior parte delle esperienze interattive tradizionali, i suoni di interazione come gli effetti audio dell'interfaccia utente vengono riprodotti in mono o stereo standard. Tuttavia, poiché tutto ciò che si trova in realtà mista esiste nello spazio 3D, inclusa l'interfaccia utente, questi oggetti traggono vantaggio dai suoni spaziali. Quando si preme un pulsante nel mondo reale, il suono da ascoltare deriva dal pulsante. Grazie ai suoni di interazione spatializing, viene nuovamente fornita un'esperienza utente più naturale e realistica.

## <a name="best-practices-when-using-spatial-sound"></a>Procedure consigliate per l'uso di un suono spaziale

**I suoni reali funzionano meglio di quelli sintetizzati o non naturali**

Maggiore è la familiarità dell'utente con un tipo di suono, maggiore sarà il reale aspetto e più facilmente sarà possibile individuarlo nel proprio ambiente. Una voce umana, ad esempio, è un tipo molto comune di suoni e gli utenti la troveranno con la stessa rapidità di una persona reale nella chat room.

**Simulazione di previsione Trumps**

Se si è abituati a un suono proveniente da una direzione particolare, l'attenzione verrà guidata in tale direzione indipendentemente dalle indicazioni spaziali. Ad esempio, la maggior parte del tempo in cui si sentono gli uccelli, si trovano sopra di noi. La riproduzione del suono di un uccello causa molto probabilmente la ricerca da parte dell'utente, anche se il suono viene inserito sotto di essi. Si tratta in genere di confusione ed è consigliabile lavorare con le aspettative, ad esempio per un'esperienza più naturale.

**La maggior parte dei suoni deve essere spaziali**

Come indicato in precedenza, tutto ciò che si verifica in realtà mista esiste nello spazio 3D, anche per i suoni. Anche la musica può talvolta trarre vantaggio dalla spazializzazione, in particolare quando è associata a un menu o a un'altra interfaccia utente.

**Evitare gli emettitori invisibili**

Dato che siamo stati condizionati per esaminare i suoni che ci siamo riusciti, può trattarsi di un'esperienza non naturale e persino snervante per individuare un suono senza presenza visiva. I suoni nel mondo reale non provengono da uno spazio vuoto, quindi è necessario assicurarsi che se un emettitore audio viene inserito nell'ambiente immediato dell'utente, è possibile che possa essere visualizzato.

**Evitare la maschera spaziale**

Il suono spaziale si basa su segnali acustici molto sottili che possono essere amplificati da altri suoni. Se si dispone di musica stereo o di ambiente, assicurarsi che siano sufficientemente bassi nella combinazione per dare spazio ai dettagli dei suoni spaziali che consentiranno agli utenti di individuarli con facilità e di mantenerli in modo realistico e naturale.

## <a name="general-concepts-to-keep-in-mind-when-using-spatial-sound"></a>Concetti generali da tenere presenti quando si usa il suono spaziale

**Il suono spaziale è una simulazione**

L'uso più frequente del suono spaziale è costituito da un suono come se fosse emanato da un oggetto reale o virtuale nel mondo. Pertanto, i suoni spaziali possono essere più sensati provenienti da tali oggetti.

Si noti che la precisione percepita del suono spaziale indica che un suono non deve necessariamente emettere dal centro di un oggetto, in quanto la differenza sarà evidente a seconda delle dimensioni dell'oggetto e della distanza dall'utente. Con piccoli oggetti, il punto centrale dell'oggetto è in genere sufficiente. Per gli oggetti di grandi dimensioni, è possibile che si desideri che un emittente di suoni o più emettitori si trovino in una posizione specifica all'interno dell'oggetto che dovrebbe produrre il suono.

**Normalizza tutti i suoni**

L'attenuazione della distanza si verifica rapidamente all'interno del primo contatore dell'utente, come avviene nel mondo reale. Tutti i file audio devono essere normalizzati per garantire un'attenuazione della distanza fisicamente accurata e assicurarsi che un suono possa essere udito quando più metri di distanza (quando applicabile). Il motore audio spaziale gestirà l'attenuazione necessaria affinché un suono possa "ritenersi" come se fosse a una certa distanza (con una combinazione di attenuazione e "indicatori di distanza") e applicando qualsiasi attenuazione in grado di ridurre l'effetto. Al di fuori della simulazione di un oggetto reale, il decadimento iniziale della distanza dei suoni *spaziali* sarà probabilmente più che sufficiente per una combinazione appropriata dell'audio.

**Individuazione oggetti e interfacce utente**

Quando si usano i segnali audio per indirizzare l'attenzione dell'utente oltre la visualizzazione corrente, il suono dovrebbe essere udibile e prominente nella combinazione, oltre ai suoni stereo e a tutti gli altri suoni spaziali che potrebbero distrarre dalla cue audio direzionale. Per i suoni e la musica associati a un elemento dell'interfaccia utente (ad esempio un menu), l'emettitore di suoni dovrebbe essere collegato a tale oggetto. Lo stereo e altre operazioni di riproduzione audio non posizionale possono rendere gli elementi spaziali difficili da individuare (vedere sopra: Evitare la maschera spaziale).

**Usare il suono spaziale sul suono 3D standard per quanto possibile**

In realtà mista, per la migliore esperienza utente, l'audio 3D dovrebbe essere ottenuta usando un suono spaziale anziché le tecnologie audio 3D legacy. In generale, la spazializzazione migliorata vale la pena del piccolo costo della CPU rispetto al suono 3D standard. L'audio 3D standard può essere usato per i suoni con priorità bassa, i suoni che sono spaziali ma non necessariamente collegati a un oggetto fisico o virtuale e gli oggetti che non sono mai necessari all'utente per interagire con l'app.

## <a name="see-also"></a>Vedere anche
* [Audio spaziale](spatial-sound.md)
* [Mapping spaziale](spatial-mapping.md)

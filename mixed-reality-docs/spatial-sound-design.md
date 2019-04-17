---
title: Progettazione spaziale
description: Spaziale audio è uno strumento potente per full immersion, accessibilità e progettazione dell'esperienza utente nelle applicazioni di realtà mista.
author: joekellyms
ms.author: joekelly
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, spaziale audio, progettazione, lo stile
ms.openlocfilehash: c8f5268faf5eef779401c046947c3137d177cb89
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597612"
---
# <a name="spatial-sound-design"></a>Progettazione spaziale

Spaziale audio è uno strumento potente per full immersion, accessibilità e progettazione dell'esperienza utente nelle applicazioni di realtà mista.

Se hai mai partecipato [Marco Polo](https://en.wikipedia.org/wiki/Marco_Polo_(game)), o non è disponibile un utente chiama il telefono per consentire lo trovi, si ha già familiarità con l'importanza del suono spaziale. Utilizziamo segnali audio nella vita quotidiana per individuare gli oggetti, attirare l'attenzione di un utente oppure ottenere una migliore comprensione dell'ambiente. Più da vicino il suono dell'app si comporta come avviene nel mondo reale, la più convincente e accattivanti che è di mondo virtuale.

<br>

> [!VIDEO https://www.youtube.com/embed/aB3TDjYklmo]

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Funzionalità</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></th>
</tr><tr>
<td> Audio spaziale</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="four-key-things-spatial-sound-does-for-mixed-reality-development"></a>Esegue quattro suono spaziali aspetti fondamentali per lo sviluppo della realtà mista

Per impostazione predefinita, suoni vengono riprodotti nel formato stereo. Ciò significa che verrà riprodotto il suono con nessuna posizione spaziale, in modo che l'utente non sa dove proviene l'audio. Suono spaziale esegue quattro aspetti fondamentali per lo sviluppo della realtà mista:

**Messa a terra**

Senza l'audio, oggetti virtuali in modo efficace cessano di esistere quando si attivano i nostri head lontano da essi. Proprio come oggetti reali, si desidera essere in grado di ascoltare questi oggetti, anche quando non è possibile visualizzarli e si desidera essere in grado di individuarle ovunque si. Proprio come oggetti virtuali devono essere basato sul visivamente per blend con il mondo reale, devono anche essere basato sull'acustico. Suono spaziale mescola facilmente l'ambiente audio del mondo reale con l'ambiente audio digitale.

**Intervento dell'utente**

Nelle esperienze di realtà mista, non è possibile presupporre dove sta guardando l'utente e prevede che possano vedere qualcosa che è inserire visivamente in tutto il mondo. Ma gli utenti possono sempre riprodotto un suono riprodurre anche quando l'oggetto di riproduzione del suono è protetto da essi. Gli utenti consentono di avere la loro attenzione creato in base al suono - saremo instinctually verso un oggetto che abbiamo ricevuto intorno a noi. Quando si desidera indirizzare sguardo dell'utente in una determinata posizione, anziché utilizzare una freccia in modo che puntino a livello visivo, inserendo un suono in percorso rappresenta un modo molto naturale e veloce per le istruzioni.

**Full immersion**

Quando gli oggetti spostano o sono in conflitto, pongono in genere tali interazioni tra i materiali. Pertanto, quando gli oggetti non rendono lo stesso fonema che fossero in realtà, un livello di full immersion verrà perso - come guardare un filmato scary con il volume verso il basso. Tutti i file audio nel mondo reale provengono da un particolare punto nello spazio - quando attiviamo nostro testine, abbiamo ricevuto la modifica in tali suoni provenienza rispetto all'orecchio ed è possibile tracciare il percorso di un suono in questo modo. Suoni spatialized costituiscono l'aspetto"" di una posizione oltre ciò che possiamo vedere.

**Progettazione di interazioni**

Nelle esperienze interattive più tradizionali, suoni di interazione, ad esempio effetti sonori dell'interfaccia utente vengono riprodotte in mono standard o stereo. Ma poiché tutto ciò che in realtà mista esiste nello spazio 3D, tra cui l'interfaccia utente - questi oggetti trarre vantaggio da spatialized suoni. Quando si preme un pulsante nel mondo reale, viene fornito il suono che è impostato da tale pulsante. Da spatializing suoni interazione, offriamo anche in questo caso un'esperienza utente più naturale e realistici.

## <a name="best-practices-when-using-spatial-sound"></a>Le procedure consigliate quando si usa spaziale audio

**Suoni reale funzionano meglio di suoni sintetizzati o non naturali**

Più familiare è l'utente con un tipo di suono, il più reale sentiranno, e più facile saranno in grado di individuarlo nel proprio ambiente. Una voce umana, ad esempio, è un tipo di suono molto comune e gli utenti possano trovarlo altrettanto rapido come una persona reale nella chat room parlare con loro.

**Nella previsione ha la precedenza su simulazione**

Se si è abituati a un suono provenienti da una particolare direzione, l'attenzione dell'utente saranno illustrati in questa direzione indipendentemente dalla segnali spaziale. Ad esempio, la maggior parte dei casi che abbiamo ricevuto volatili, sono di sopra di Stati Uniti. La riproduzione del suono di uccelli potrebbe provocare l'utente da cercare, anche se si inserisce il suono di sotto di essi. Si tratta in genere confusione e si consiglia di lavorare con le aspettative, ad esempio questi anziché su di essi per un'esperienza più naturale.

**La maggior parte dei suoni dovrebbero essere spatialized**

Come indicato sopra, tutto ciò che in realtà mista esiste nello spazio 3D, i suoni devono anche. Musica può talvolta essere utile spatialization, in particolare quando quest'ultima è associata a un menu o parte dell'interfaccia utente.

**Evitare di istanze di emissione FixIt invisibile**

Poiché è stata state condizionate esaminare suoni che abbiamo ricevuto intorno a noi, può essere un'esperienza anche unnerving e complessi per individuare un file audio non viene rappresentato visivamente. Suoni nel mondo reale non provengono da uno spazio vuoto, in modo da assicurarsi che se una funzione di emissione audio viene posizionata all'interno di ambiente immediato dell'utente che può anche essere visualizzato.

**Evitare di mascheramento spaziale**

Suono spaziale si basa su segnali acustici molto complesso che possono essere sovraccaricarsi da altri suoni. Se si dispone di musica stereo o ambiente suoni, assicurarsi che siano sufficientemente basse nella combinazione di spazio per i dettagli dei suoni spatialized che gli utenti possono facilmente individuarli e mantenerli suona realistici e naturale.

## <a name="general-concepts-to-keep-in-mind-when-using-spatial-sound"></a>Concetti generali da tenere presenti quando si usa spaziale audio

**Suono spaziale è una simulazione**

L'uso più frequente del suono spaziale è quello di un suono sembrare come se è che derivano da un oggetto reale o virtuale del mondo. Di conseguenza, suoni spatialized potrebbero prevedere la scelta più sensata provenienti da tali oggetti.

Si noti che l'accuratezza percepito spaziali audio indica che un suono non deve necessariamente generare dal centro dell'oggetto, come la differenza sarà significativo a seconda delle dimensioni dell'oggetto e la distanza da parte dell'utente. Con oggetti di piccole dimensioni, il punto centrale dell'oggetto è in genere sufficiente. Per gli oggetti più grandi, è possibile un suono emissione o più istanze di emissione FixIt in corrispondenza della posizione specifica all'interno dell'oggetto che dovrà essere che produce l'audio.

**Normalizza tutti i file audio**

Attenuazione della distanza avviene rapidamente entro il primo misuratore da parte dell'utente, come avviene nel mondo reale. Tutti i file audio devono essere normalizzati per l'attenuazione della distanza fisicamente accurata e garantisce che può essere ascoltato un suono quando molti contatori di stoccaggio (se applicabile). Il motore di audio spaziale gestisce l'attenuazione necessaria per un suono "percepisca" è una certa distanza (con una combinazione di attenuazione e "segnali distance") e di applicare qualsiasi attenuazione è stato possibile ridurre l'effetto. Di fuori di simulazione di un oggetto reale, iniziale a distanza di decadimento *spaziale audio* suoni saranno probabilmente più che sufficienti per una corretta combinazione di audio.

**Interfacce utente e di individuazione oggetti**

Quando si utilizza segnali acustici per dirigere l'attenzione dell'utente oltre la visualizzazione attuale, deve essere il suono udibile e notificate all'utente nella combinazione, ben oltre qualsiasi audio stereo e altri suoni spatialized che potrebbe essere si distaccherà dal segnale audio direzionale. Per i suoni e musica che sono associati a un elemento dell'interfaccia utente (ad esempio, un menu di scelta), l'emissione audio deve essere collegato a tale oggetto. Stereo e altri non posizionali riproduzione audio può complicare la spatialized elementi agli utenti di individuare (vedere sopra: Evitare di mascheramento spaziale).

**Usare un suono spaziale tramite standard suono 3D quanto più possibile**

Nella realtà mista, per la migliore esperienza utente, 3D audio deve essere ottenuto tramite spaziale audio anziché legacy tecnologie audio 3D. In generale, il miglioramento spatialization vale la pena piccole della CPU su standard 3D audio. Audio 3D standard è utilizzabile per priorità bassa suoni, suoni spatialized, ma non necessariamente collegati a un oggetto fisico o virtuale e gli oggetti che l'utente mai necessario individuare per interagire con l'app.

## <a name="see-also"></a>Vedere anche
* [Spaziale audio](spatial-sound.md)
* [Mapping spaziale](spatial-mapping.md)

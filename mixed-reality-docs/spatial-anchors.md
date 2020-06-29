---
title: Ancoraggi nello spazio
description: Procedure consigliate per l'uso di ancoraggi nello spazio per il rendering di ologrammi stabili.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: sistema di coordinate, sistema di coordinate nello spazio, scala del mondo, mondo, scala, posizione, orientamento, ancoraggio, ancoraggio nello spazio, vincolato al mondo, vincolo con il mondo, persistenza, condivisione
ms.openlocfilehash: 8d270f96add795fdb54e0a91ebc9d38a34640da1
ms.sourcegitcommit: 5612e8bfb9c548eac42182702cec87b160efbbfe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2020
ms.locfileid: "85441788"
---
# <a name="spatial-anchors"></a>Ancoraggi nello spazio

Un ancoraggio spaziale rappresenta un punto importante nel mondo in cui il sistema tiene traccia del tempo. Ogni ancoraggio ha un [sistema di coordinate](coordinate-systems.md) che si adatta in base alle necessità rispetto agli altri ancoraggi o cornici di riferimento, in modo da garantire che gli ologrammi ancorati restino in posizione.  Eseguendo il rendering di un ologramma nel sistema di coordinate di un ancoraggio, puoi ottenere la massima accuratezza nel posizionamento dell'ologramma in qualsiasi momento. Questo comporta il costo di piccoli aggiustamenti nel tempo alla posizione dell'ologramma, in quanto il sistema lo sposta continuamente al posto rispetto al mondo reale.

È anche possibile salvare in permanenza e condividere gli ancoraggi spaziali tra le sessioni dell'applicazione e tra i dispositivi:
* Salvando gli ancoraggi spaziali locali su disco e ricaricarli in un secondo momento, l'applicazione può calcolare la stessa posizione nel mondo reale tra più sessioni dell'applicazione in un singolo HoloLens.
* Usando gli <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">ancoraggi spaziali di Azure</a> per creare un ancoraggio cloud, l'applicazione può condividere un ancoraggio spaziale tra più dispositivi HoloLens, iOS e Android. Poiché ogni dispositivo esegue il rendering di un ologramma usando lo stesso ancoraggio spaziale, gli utenti vedranno che l'ologramma viene visualizzato nella stessa posizione nel mondo reale. Ciò rende possibili esperienze condivise in tempo reale.
* Puoi usare <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Ancoraggi nello spazio di Azure</a> anche per la persistenza asincrona degli ologrammi su dispositivi HoloLens, iOS e Android. Condividendo un ancoraggio durevole nello spazio del cloud, più dispositivi possono osservare nel tempo lo stesso ologramma salvato in modo permanente, anche se tali dispositivi non sono presenti insieme contemporaneamente.

Per esperienze su scala o su larga scala per gli auricolari desktop con tethering che resteranno entro un diametro di 5 metri, in genere è possibile usare il [frame della fase di riferimento](coordinate-systems.md#stage-frame-of-reference) anziché gli ancoraggi spaziali, che fornisce un unico sistema di coordinate in cui eseguire il rendering di tutto il contenuto. Tuttavia, se l'applicazione intende consentire agli utenti di aggirare oltre 5 metri in HoloLens, probabilmente operando in un intero piano di un edificio, saranno necessari ancoraggi spaziali per assicurare la stabilità del contenuto.

Gli ancoraggi nello spazio sono uno strumento utilissimo per gli ologrammi che devono rimanere fissi nel mondo. Tuttavia, una volta posizionati, non possono essere spostati. Sono disponibili alternative agli ancoraggi più appropriati per gli ologrammi dinamici con tag insieme all'utente. È pertanto preferibile posizionare gli ologrammi dinamici usando una cornice di riferimento non spostabile (la base per le coordinate globali di Unity) oppure una cornice di riferimento associata.

## <a name="best-practices"></a>Procedure consigliate

Queste linee guide relative agli ancoraggi nello spazio consentiranno di eseguire il rendering di ologrammi stabili in grado di tenere traccia accuratamente del mondo reale.

### <a name="create-spatial-anchors-where-users-place-them"></a>Creare gli ancoraggi nello spazio nei punti in cui gli utenti li posizionano

In genere, gli utenti sono quelli che posizionano in modo esplicito gli ancoraggi spaziali.

In HoloLens, ad esempio, un'applicazione può intersecare il raggio di [sguardi](gaze-and-commit.md) dell'utente con la mesh di [mapping spaziale](spatial-mapping.md) per consentire all'utente di decidere dove posizionare un ologramma. Quando l'utente tocca per posizionare l'ologramma, creare un ancoraggio spaziale nel punto di intersezione e quindi posizionare l'ologramma all'origine del sistema di coordinate dell'ancoraggio.

Gli ancoraggi spaziali locali sono semplici ed efficienti da creare. Il sistema consoliderà i dati interni se più ancoraggi possono condividere i dati dei sensori sottostanti. È in genere consigliabile creare un nuovo ancoraggio spaziale locale per ogni ologramma che un utente inserisce in modo esplicito, eccetto nei casi descritti di seguito, ad esempio gruppi rigidi di ologrammi.

### <a name="always-render-anchored-holograms-within-3-meters-of-their-anchor"></a>Eseguire sempre il rendering degli ologrammi ancorati entro 3 metri dal relativo ancoraggio

Gli ancoraggi nello spazio stabilizzano il relativo sistema di coordinate vicino alla loro origine. Se si eseguono il rendering degli ologrammi più di 3 metri da tale origine, gli ologrammi potrebbero riscontrare errori posizionali evidenti in proporzione alla distanza da tale origine a causa degli effetti dell'ARM. Questa operazione funziona se l'utente si trova vicino all'ancoraggio, dal momento che l'ologramma è lontano dall'utente. In altre parole, l'errore angolare dell'ologramma a distanza sarà ridotto. Tuttavia, se l'utente si avvicina a tale ologramma distanti, sarà grande nella propria visualizzazione, rendendo piuttosto evidenti gli effetti della leva-ARM dall'origine di ancoraggio faraway.

### <a name="group-holograms-that-should-form-a-rigid-cluster"></a>Raggruppare gli ologrammi che devono formare un gruppo rigido

Più ologrammi possono condividere lo stesso ancoraggio spaziale se l'applicazione prevede che gli ologrammi mantengano relazioni fisse tra loro.

Se ad esempio si aggiunge un'animazione a un sistema olografico solare in una stanza, è preferibile collegare tutti gli oggetti di sistema solari a un singolo ancoraggio al centro, in modo che vengano spostati senza problemi. In questo caso, è il sistema solare nella sua interezza a essere ancorato, benché le parti che lo costituiscono si muovano dinamicamente intorno all'ancoraggio.

Per mantenere la stabilità dell'ologramma, è necessario seguire la regola di 3 metri sopra.

### <a name="render-highly-dynamic-holograms-using-the-stationary-frame-of-reference-instead-of-a-local-spatial-anchor"></a>Eseguire il rendering degli ologrammi a elevata dinamicità usando la cornice di riferimento non spostabile invece di un ancoraggio nello spazio locale

Se si dispone di un ologramma altamente dinamico, ad esempio un carattere che cammina intorno a una stanza o un'interfaccia utente mobile che segue lungo la parete vicino all'utente, è preferibile ignorare gli ancoraggi spaziali locali ed eseguire il rendering degli ologrammi direttamente nel sistema di coordinate fornito dal [frame di riferimento fisso](coordinate-systems.md#stationary-frame-of-reference). In Unity è possibile ottenere questo risultato inserendo gli ologrammi direttamente nelle coordinate internazionali senza una WorldAnchor. Gli ologrammi in un frame di riferimento fisso possono comportare la deriva quando l'utente è distante dall'ologramma. Tuttavia, è meno probabile che sia evidente per gli ologrammi dinamici: l'ologramma è costantemente in movimento o il suo movimento continua a essere sempre vicino all'utente in cui la deriva verrà ridotta a icona.

Un caso interessante di ologrammi dinamici è costituito da un oggetto che si anima da un sistema di coordinate ancorato a un altro. Ad esempio, è possibile che si disponga di due castelli a 10 metri di distanza, ciascuno sul proprio ancoraggio spaziale con un castello che spara una palla di cannone all'altro castello. Al momento della generazione di Cannonball, è possibile eseguirne il rendering nella posizione appropriata nel frame di riferimento fisso per coincidere con il cannone nel sistema di coordinate ancorato del primo castello. La palla può quindi seguire la sua traiettoria nella cornice di riferimento non spostabile mentre percorre 10 metri in aria. Quando la Cannonball raggiunge l'altro castello, è possibile scegliere di spostarla nel sistema di coordinate ancorato del secondo castello per consentire i calcoli fisici con i corpi rigidi del castello.

Se si condivide un ologramma altamente dinamico tra i dispositivi, è necessario selezionare un ancoraggio spaziale cloud per agire come padre perché i frame stazionari di riferimento non possono essere condivisi tra i dispositivi.  Tuttavia, in questo caso, è necessario assicurarsi che l'ologramma dinamico o i dispositivi che lo visualizzano rimangano all'interno del raggio di 3 metri di ancoraggio per assicurarsi che l'ologramma appaia stabile in tutti i dispositivi.

### <a name="avoid-creating-a-grid-of-spatial-anchors"></a>Evitare di creare una griglia di ancoraggi nello spazio

È possibile che l'applicazione rilasci una griglia normale di ancoraggi spaziali Man mano che l'utente si aggira, passando gli oggetti dinamici dall'ancoraggio all'ancoraggio Man mano che si spostano. Tuttavia, ciò implica una grande gestione per l'applicazione, senza il vantaggio dei dati di sensori profondi che il sistema gestisce internamente. In questi casi, in genere si otterranno risultati migliori con minore sforzo inserendo gli ologrammi nel frame di riferimento stazionale, come descritto nella sezione precedente.
Quando si esegue il pre-posizionamento di un set di ancoraggi spaziali cloud intorno a uno spazio statico, è consigliabile posizionare gli ancoraggi spaziali nelle posizioni degli ologrammi chiave che l'utente incontra in base al principio precedente anziché creare una griglia arbitraria di ancoraggi. Ciò garantisce la massima stabilità per tali ologrammi chiave.

### <a name="release-local-spatial-anchors-you-no-longer-need"></a>Rilasciare gli ancoraggi nello spazio locali non più necessari

Mentre un ancoraggio spaziale locale è attivo, il sistema assegna priorità a mantenere i dati del sensore vicini a tale ancoraggio. Se non usi più un ancoraggio nello spazio, non accedere più al relativo sistema di coordinate. In questo modo è possibile rimuovere i dati del sensore sottostanti in base alle esigenze.

Ciò è particolarmente importante per gli ancoraggi locali salvati in modo permanente nell'archivio degli ancoraggi nello spazio. I dati dei sensori dietro questi ancoraggi verranno mantenuti in modo permanente per consentire all'applicazione di trovare tale ancoraggio nelle sessioni future, riducendo così lo spazio disponibile per tenere traccia degli altri ancoraggi. Salvare in modo permanente solo gli ancoraggi locali che è necessario ritrovare nelle sessioni future e rimuoverli dall'archivio quando non sono più significativi per l'utente.

Per gli ancoraggi nello spazio del cloud, le dimensioni dello spazio di archiviazione possono adattarsi come richiesto dallo scenario. È possibile archiviare il numero di ancoraggi cloud necessario, rilasciandoli solo quando si è certi che gli utenti non dovranno ritrovare gli ologrammi in quell'ancoraggio.

## <a name="see-also"></a>Vedi anche
* [Sistemi di coordinate](coordinate-systems.md)
* [Esperienze condivise nella realtà mista](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Ancoraggi nello spazio di Azure</a>
* [Persistenza in Unity](persistence-in-unity.md)
* [Ancoraggi nello spazio in DirectX](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-spatial-anchors)
* [Case study - Guardare attraverso fori nella realtà](case-study-looking-through-holes-in-your-reality.md)

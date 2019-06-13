---
title: Ancoraggi nello spazio
description: Procedure consigliate per l'uso di ancoraggi nello spazio per il rendering di ologrammi stabili.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
ms.localizationpriority: high
keywords: sistema di coordinate, sistema di coordinate nello spazio, scala del mondo, mondo, scala, posizione, orientamento, ancoraggio, ancoraggio nello spazio, vincolato al mondo, vincolo con il mondo, persistenza, condivisione
ms.openlocfilehash: 16165194d040ad22f7885897eddcc65cf9dcaec3
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2019
ms.locfileid: "65730855"
---
# <a name="spatial-anchors"></a>Ancoraggi nello spazio

Un ancoraggio nello spazio rappresenta un punto importante nel mondo di cui il sistema deve tenere traccia nel tempo. Ogni ancoraggio ha un [sistema di coordinate](coordinate-systems.md) che si adatta in base alle necessità rispetto agli altri ancoraggi o cornici di riferimento, in modo da garantire che gli ologrammi ancorati restino in posizione.  Eseguendo il rendering di un ologramma nel sistema di coordinate di un ancoraggio, puoi ottenere la massima accuratezza nel posizionamento dell'ologramma in qualsiasi momento. L'unico inconveniente è rappresentato da piccoli adeguamenti apportati nel tempo alla posizione dell'ologramma, in quanto il sistema lo riporta continuamente in posizione rispetto al mondo reale.

Puoi anche salvare in modo permanente gli ancoraggi nello spazio e condividerli da una sessione all'altra dell'app e da un dispositivo all'altro:
* Salvando su disco gli ancoraggi nello spazio locali e ricaricandoli successivamente, l'app può ragionare sulla stessa posizione nel mondo reale in più sessioni su un unico dispositivo HoloLens.
* Usando <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Ancoraggi nello spazio di Azure</a> per creare un ancoraggio del cloud, l'app può condividere un ancoraggio nello spazio su più dispositivi HoloLens, iOS e Android. Facendo in modo che ciascun dispositivo esegua il rendering di un ologramma usando lo stesso ancoraggio nello spazio, tutti gli utenti vedranno l'ologramma nello stesso punto nel mondo reale.  Ciò rende possibili esperienze condivise in tempo reale.
* Puoi usare <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Ancoraggi nello spazio di Azure</a> anche per la persistenza asincrona degli ologrammi su dispositivi HoloLens, iOS e Android.  Condividendo un ancoraggio durevole nello spazio del cloud, più dispositivi possono osservare nel tempo lo stesso ologramma salvato in modo permanente, anche se tali dispositivi non sono presenti insieme contemporaneamente.

Per esperienze in scala in posizione eretta o all'interno di una stanza con visori VR desktop con tethering che resteranno entro un diametro di 5 metri, in genere puoi semplicemente usare la [cornice di riferimento della scena](coordinate-systems.md#stage-frame-of-reference) anziché gli ancoraggi nello spazio, in modo da avere un unico sistema di coordinate in cui eseguire il rendering di tutto il contenuto. Se però l'app intende consentire agli utenti di spostarsi oltre i 5 metri in HoloLens, ad esempio per operare su un intero piano di un edificio, saranno necessari ancoraggi nello spazio per mantenere stabile il contenuto.

Gli ancoraggi nello spazio sono uno strumento utilissimo per gli ologrammi che devono rimanere fissi nel mondo. Tuttavia, una volta posizionati, non possono essere spostati. In alternativa all'uso degli ancoraggi, sono disponibili metodi più adatti per gli ologrammi dinamici che devono essere associati all'utente. È pertanto preferibile posizionare gli ologrammi dinamici usando una cornice di riferimento non spostabile (la base per le coordinate globali di Unity) oppure una cornice di riferimento associata.

## <a name="best-practices"></a>Procedure consigliate

Queste linee guide relative agli ancoraggi nello spazio consentiranno di eseguire il rendering di ologrammi stabili in grado di tenere traccia accuratamente del mondo reale.

### <a name="create-spatial-anchors-where-users-place-them"></a>Creare gli ancoraggi nello spazio nei punti in cui gli utenti li posizionano

La maggior parte delle volte sono gli utenti a posizionare esplicitamente gli ancoraggi nello spazio.

Ad esempio, in HoloLens un'app può intersecare il raggio dello [sguardo](gaze.md) dell'utente con la mesh di [mapping spaziale](spatial-mapping.md) per consentire all'utente di decidere dove posizionare un ologramma. Quando l'utente effettua un tocco per posizionare l'ologramma, devi creare un ancoraggio nello spazio nel punto di intersezione e quindi posizionare l'ologramma in corrispondenza dell'origine del sistema di coordinate di tale ancoraggio.

Gli ancoraggi nello spazio locali sono facili e rapidi da creare e il sistema ne consoliderà i dati interni se più ancoraggi possono condividere i rispettivi dati dei sensori sottostanti. In genere devi creare un nuovo ancoraggio nello spazio locale per ogni ologramma posizionato esplicitamente da un utente, tranne nei casi illustrati di seguito in cui ad esempio si tratta di gruppi rigidi di ologrammi.

### <a name="always-render-anchored-holograms-within-3-meters-of-their-anchor"></a>Eseguire sempre il rendering degli ologrammi ancorati entro 3 metri dal relativo ancoraggio

Gli ancoraggi nello spazio stabilizzano il relativo sistema di coordinate vicino alla loro origine. Se esegui il rendering degli ologrammi a più di 3 metri circa da tale origine, gli ologrammi possono presentare evidenti errori di posizionamento proporzionalmente alla distanza dalla suddetta origine a causa degli effetti del braccio della leva. Ciò funziona se l'utente è in piedi vicino all'ancoraggio perché l'ologramma è lontano anche dall'utente, nel senso che l'errore di angolo dell'ologramma distante sarà trascurabile. Se invece l'utente raggiunge camminando l'ologramma distante, risulterà grande nella visualizzazione, rendendo alquanto ovvii gli effetti del braccio della leva dall'origine dell'ancoraggio lontano.

### <a name="group-holograms-that-should-form-a-rigid-cluster"></a>Raggruppare gli ologrammi che devono formare un gruppo rigido

Diversi ologrammi possono condividere lo stesso ancoraggio nello spazio se l'app prevede che tali ologrammi mantengano relazioni fisse tra loro.

Ad esempio, se vuoi animare un sistema solare olografico in una stanza, è preferibile collegare tutti gli oggetti del sistema solare a un unico ancoraggio al centro, in modo che si spostino fluidamente l'uno rispetto all'altro. In questo caso, è il sistema solare nella sua interezza a essere ancorato, benché le parti che lo costituiscono si muovano dinamicamente intorno all'ancoraggio.

In questa situazione l'accorgimento principale da adottare per mantenere la stabilità dell'ologramma è seguire la regola dei 3 metri illustrata in precedenza.

### <a name="render-highly-dynamic-holograms-using-the-stationary-frame-of-reference-instead-of-a-local-spatial-anchor"></a>Eseguire il rendering degli ologrammi a elevata dinamicità usando la cornice di riferimento non spostabile invece di un ancoraggio nello spazio locale

Se hai un ologramma a elevata dinamicità, quale ad esempio un personaggio che cammina all'interno di una stanza, oppure un'interfaccia utente mobile che segue il muro accanto all'utente, è consigliabile ignorare gli ancoraggi nello spazio locali ed eseguire il rendering di tali ologrammi direttamente nel sistema di coordinate fornito dalla [cornice di riferimento non spostabile](coordinate-systems.md#stationary-frame-of-reference) (in Unity puoi ottenere questo risultato posizionando gli ologrammi direttamente nelle coordinate globali senza WorldAnchor). Gli ologrammi in una cornice di riferimento non spostabile possono subire uno scostamento quando l'utente è lontano da essi. È tuttavia meno probabile che questa situazione si noti per gli ologrammi dinamici: l'ologramma si sposta costantemente comunque oppure il relativo movimento lo tiene costantemente vicino all'utente, per cui lo scostamento sarà minimo.

Un caso interessante di ologrammi dinamici è costituito da un oggetto che si anima da un sistema di coordinate ancorato a un altro. Ad esempio, puoi avere due castelli distanti tra loro 10 metri, ognuno con un proprio ancoraggio nello spazio, con un castello che spara una palla di cannone verso l'altro castello. Nel momento in cui la palla di cannone viene sparata, puoi eseguirne il rendering nella posizione appropriata nella cornice di riferimento non spostabile, in modo da coincidere con il cannone nel sistema di coordinate ancorato del primo castello. La palla può quindi seguire la sua traiettoria nella cornice di riferimento non spostabile mentre percorre 10 metri in aria. Appena la palla di cannone raggiunge l'altro castello, puoi scegliere di spostarla nel sistema di coordinate ancorato del secondo castello per consentire i calcoli di fisica relativi ai corpi rigidi di tale castello.

Se intendi condividere un ologramma a elevata dinamicità su più dispositivi, dovrai selezionare un ancoraggio nello spazio del cloud che funga da elemento padre perché non è possibile condividere le cornici di riferimento non spostabili su più dispositivi.  In questo caso, devi tuttavia assicurarti che l'ologramma dinamico o i dispositivi che lo visualizzano restino nel raggio di 3 metri dell'ancoraggio, per essere certo che l'ologramma risulti stabile su tutti i dispositivi.

### <a name="avoid-creating-a-grid-of-spatial-anchors"></a>Evitare di creare una griglia di ancoraggi nello spazio

Puoi avere la tentazione di configurare l'app in modo che costituisca una griglia regolare di ancoraggi nello spazio man mano che l'utente cammina, effettuando la transizione degli oggetti dinamici da un ancoraggio all'altro durante il movimento. Ciò tuttavia comporta molte attività di gestione per l'app, senza avere il vantaggio dei dati completi dei sensori che il sistema tiene internamente. Per questi casi, di solito puoi ottenere risultati migliori con meno fatica posizionando gli ologrammi nella cornice di riferimento non spostabile, come descritto nella sezione precedente.

Se posizioni anticipatamente una serie di ancoraggi nello spazio del cloud attorno a uno spazio statico, considera la possibilità di posizionare gli ancoraggi nello spazio in corrispondenza degli ologrammi principali che l'utente incontrerà in base al principio sopra illustrato invece di creare una griglia arbitraria di ancoraggi.  Ciò garantisce la massima stabilità per tali ologrammi chiave.

### <a name="release-local-spatial-anchors-you-no-longer-need"></a>Rilasciare gli ancoraggi nello spazio locali non più necessari

Mentre un ancoraggio nello spazio locale è attivo, il sistema assegnerà le priorità mantenendo i dati dei sensori vicini a tale ancoraggio. Se non usi più un ancoraggio nello spazio, non accedere più al relativo sistema di coordinate. In questo modo verranno rimossi secondo le necessità i relativi dati dei sensori sottostanti.

Ciò è particolarmente importante per gli ancoraggi locali salvati in modo permanente nell'archivio degli ancoraggi nello spazio. I dati dei sensori alla base di tali ancoraggi verranno mantenuti in modo permanente per consentire all'app di trovare l'ancoraggio nelle sessioni future, riducendo lo spazio disponibile per tenere traccia di altri ancoraggi. Salva in modo permanente solo gli ancoraggi locali da ritrovare nelle sessioni future e rimuovili dall'archivio quando non sono più significativi per l'utente.

Per gli ancoraggi nello spazio del cloud, le dimensioni dello spazio di archiviazione possono adattarsi come richiesto dallo scenario.  Puoi archiviare tutti gli ancoraggi del cloud che ritieni necessari, rilasciandoli solo quando sei certo che gli utenti non dovranno collocare di nuovo gli ologrammi in corrispondenza degli ancoraggi in questione.

## <a name="see-also"></a>Vedi anche
* [Sistemi di coordinate](coordinate-systems.md)
* [Esperienze condivise nella realtà mista](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Ancoraggi nello spazio di Azure</a>
* [Persistenza in Unity](persistence-in-unity.md)
* [Ancoraggi nello spazio in DirectX](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-spatial-anchors)
* [Case study - Guardare attraverso fori nella realtà](case-study-looking-through-holes-in-your-reality.md)

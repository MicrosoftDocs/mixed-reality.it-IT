---
title: Ancoraggi spaziali
description: Procedure consigliate per l'uso di ancoraggi spaziali per il rendering vntana stabile.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: sistema di coordinate, spaziale sistema di coordinate, su scala mondiale, mondo, scalabilità, posizione, orientamento, ancoraggio, ancoraggio spaziale, bloccato al mondo, world blocca il thread, persistenza, la condivisione
ms.openlocfilehash: eb0fae7881f1b6517da57305ef2fa3cb1ed78648
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605109"
---
# <a name="spatial-anchors"></a>Ancoraggi spaziali

Un punto di ancoraggio spaziale rappresenta un punto importante nel mondo che il sistema deve tenere traccia nel corso del tempo. Ogni ancoraggio ha un [sistema di coordinate](coordinate-systems.md) che viene regolata in base alle esigenze, rispetto a altro Anchor o posizionare i frame di riferimento, per garantire che rimanga in modo preciso vntana ancorata.  Ologramma nel sistema di coordinate dell'ancoraggio di rendering consente il posizionamento più preciso per tali ologrammi in qualsiasi momento. Ciò comporta il costo di piccole modifiche nel corso del tempo alla posizione del ologrammi, come il sistema continuamente lo sposta nuovamente nella posizione rispetto al mondo reale.

È possibile salvare in modo permanente e condividere gli ancoraggi spaziali tra le sessioni di app e tra dispositivi diversi:
* Salvando Anchor spaziali locale su disco e il caricamento che delle modifiche in un secondo momento, l'app in grado di controllare la stessa posizione nel mondo reale in più sessioni di app in un singolo dispositivo HoloLens.
* Usando <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Anchor spaziali Azure</a> per creare un punto di ancoraggio cloud, l'app può condividere un ancoraggio spaziale tra più HoloLens, dispositivi iOS e Android. Facendo in modo che ogni dispositivo di eseguire il rendering di ologramma usando lo stesso ancoraggio spaziale, tutti gli utenti visualizzeranno l'ologrammi vengono visualizzati nello stesso punto nel mondo reale.  Ciò consente esperienze condivise in tempo reale.
* È anche possibile usare <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Anchor spaziali Azure</a> per la persistenza asincrona ologrammi nei dispositivi Android, iOS e HoloLens.  Condividendo un ancoraggio spaziali cloud durevole, più dispositivi possono osservare le stessi ologrammi persistenti nel corso del tempo, anche se questi dispositivi non sono presenti nello stesso momento.

Per usufruire di scalabilità permanente o gradazioni di chat room per con tethering auricolari desktop che rimarranno all'interno di un diametro del misuratore di 5, è possibile usare in genere solo il [fase fotogramma di riferimento](coordinate-systems.md#stage-frame-of-reference) anziché spaziali ancoraggi, assicurando in questo modo un singolo sistema di coordinate in cui eseguire il rendering di tutto il contenuto. Tuttavia, se l'app è intenzione di consentire agli utenti di vagare oltre 5 contatori su HoloLens, probabilmente opera in un intero piano di un edificio, tutto è necessario spaziali ancorato a mantenere stabili contenuto.

Mentre gli ancoraggi spaziali sono ideali per vntana che deve rimanere predefinito nel mondo, una volta che viene inserito un ancoraggio, non può essere spostato. Sono disponibili alternative all'ancoraggio che è più appropriate per vntana dinamica che deve contrassegnare con l'utente. È consigliabile posizionare vntana dinamico usando un frame di riferimento (la base per le coordinate complessive di Unity) fisso o un frame di riferimento collegati.

## <a name="best-practices"></a>Procedure consigliate

Queste linee guida spaziali ancoraggio consentono di eseguire il rendering vntana stabile che tengono accuratamente traccia del mondo reale.

### <a name="create-spatial-anchors-where-users-place-them"></a>Creare ancoraggi spaziali in cui gli utenti inserirli

La maggior parte dei casi, gli utenti devono essere quelli spaziali Anchor l'inserimento in modo esplicito.

Su HoloLens, ad esempio, un'app può intersecarsi dell'utente [estasiati](gaze.md) ray con la [mapping spaziale](spatial-mapping.md) mesh per consentire all'utente di decidere dove posizionare ologramma. Quando l'utente tocca per posizionare tali ologrammi, creare un punto di ancoraggio spaziale in corrispondenza del punto di intersezione e quindi inserire l'ologrammi in corrispondenza dell'origine del sistema di coordinate che dell'ancoraggio.

Gli ancoraggi spaziali locali sono semplici e ad alte prestazioni per creare e il sistema consoliderà propri dati interni se più Anchor possono condividere i dati dei sensori sottostante. In genere è consigliabile creare un nuovo ancoraggio spaziale locale per ogni ologrammi che un utente inserisce in modo esplicito, tranne nei casi descritti di seguito, ad esempio gruppi rigidi di vntana.

### <a name="always-render-anchored-holograms-within-3-meters-of-their-anchor"></a>Eseguire sempre il rendering vntana ancorata all'interno di 3 misuratori del loro punto di ancoraggio

Gli ancoraggi spaziali stabilizzare il sistema di coordinate in prossimità di origine dell'ancoraggio. Se si esegue il rendering vntana più di circa 3 misuratori da tale origine, tali vntana potrebbe verificarsi errori posizionali evidenti proporzionalmente alla distanza da tale origine, a causa di effetti levetta-Azure Resource Manager. Che funziona se l'utente è l'acronimo quasi il punto di ancoraggio, poiché l'ologrammi sono a portata di mano da parte dell'utente, vale a dire che l'errore angular di ologramma distante saranno ridotte. Tuttavia, se l'utente scorre ricorsivamente a tali ologrammi distanti, quindi sarà grande loro visualizzate in modo gli effetti levetta-Azure Resource Manager dall'origine ancoraggio lontani alquanto ovvia.

### <a name="group-holograms-that-should-form-a-rigid-cluster"></a>Ologrammi gruppo che devono formare un cluster rigido

Ologrammi più possono condividere lo stesso ancoraggio spaziale se l'app prevede tali vntana per mantenere fissi le relazioni tra loro.

Ad esempio, se si sta aggiungendo un'animazione di un sistema solare holographic in una stanza, è migliore collegare tutti gli oggetti di sistema solare a un singolo punto di ancoraggio nel centro, in modo che vengano spostati senza problemi uno rispetto a altro. In questo caso, è il sistema solare nel suo complesso che è ancorata, anche se sue parti componenti, sono in modo dinamico gli spostamenti all'ancoraggio.

La chiave avvertenza qui per mantenere la stabilità di ologramma consiste nel seguire la regola di misurazione di 3 precedente.

### <a name="render-highly-dynamic-holograms-using-the-stationary-frame-of-reference-instead-of-a-local-spatial-anchor"></a>Eseguire il rendering vntana altamente dinamici utilizzando il fotogramma di riferimento fisso anziché un punto di ancoraggio spaziale locale

Se si dispone di ologramma altamente dinamico, ad esempio un carattere walking intorno a chat room oppure a un'interfaccia utente a virgola mobile che segua la parete in prossimità dell'utente, è consigliabile ignorare gli ancoraggi spaziali locali ed eseguire il rendering di tali vntana direttamente nel sistema di coordinate fornita dal [</C0>fotogrammadiriferimentofisso<spanclass="notranslate">](coordinate-systems.md#stationary-frame-of-reference) (vale a dire in Unity, è ottenere questo risultato inserendo vntana direttamente nelle coordinate internazionali senza un WorldAnchor).</span> Ologrammi in un frame di riferimento fisso potrebbero verificarsi gli orientamenti quando l'utente è tutt'altro che di ologramma, ma è meno probabile che essere evidenti per vntana dinamica: l'ologrammi costantemente lo spostamento comunque oppure il movimento mantiene costantemente più vicino all'utente , dove lo sfasamento verrà ridotta a icona.

Un caso interessante di vntana dinamico è un oggetto che viene aggiunta un'animazione da un sistema di coordinate ancorato a un'altra. Ad esempio, potrebbe essere due castles 10 metri, ognuno nella propria ancoraggio spaziale, con uno castle generando un cannonball all'altro castle. Al momento che il cannonball viene attivato, è possibile eseguire il rendering, in corrispondenza della posizione appropriata nel fotogramma di riferimento fisso, in modo tale da coincidono con cannon nel sistema di coordinate ancorato di castle prima. Quindi possibile seguire relativo traiettoria nel frame di riferimento fisso come questa viene rimossa 10 misuratori attraverso l'aria. Come il cannonball raggiunge l'altro castle, è possibile spostare che nel secondo castle ancorata sistema di coordinate per consentire la fisica calcoli con corpi rigida del castle tale.

Se si condivide un ologrammi altamente dinamici tra dispositivi, è necessario scegliere alcune ancoraggio spaziali cloud da usare come relativo elemento padre, come frame di riferimento fisso non può essere condiviso tra i dispositivi.  Tuttavia, in questo caso, è necessario assicurarsi che sia l'ologrammi dinamici o i dispositivi di visualizzazione rimangono nel raggio di misuratore 3 dell'ancoraggio, per essere certi che di ologramma compaia stabile in tutti i dispositivi.

### <a name="avoid-creating-a-grid-of-spatial-anchors"></a>Evitare di creare una griglia di punti di ancoraggio spaziali

Potrebbe essere tentati di avere l'app di eliminare una griglia regolare gli ancoraggi spaziali degli utenti di lavorare, in fase di transizione oggetti dinamici da ancoraggio per ancoraggio si sposta all'interno. Tuttavia, ciò comporta una grande quantità di gestione per l'app, senza il vantaggio dei dati del sensore deep gestiti internamente dal sistema stesso. In questi casi, è in genere otterranno risultati migliori con meno fatica, inserendo il vntana nel frame di riferimento fisso, come descritto nella sezione precedente.

Quando si pre-un set di ancoraggi spaziali cloud intorno a uno spazio statico, è consigliabile posizionare gli ancoraggi spaziali nei percorsi di vntana la chiave sarà che l'utente per ogni principio precedente, anziché creare una griglia arbitraria di punti di ancoraggio.  In questo modo si otterrà la massima stabilità per tali chiavi vntana.

### <a name="release-local-spatial-anchors-you-no-longer-need"></a>Versione locale Anchor spaziale che non è più necessario

Quando un punto di ancoraggio spaziale locale è attivo, il sistema avrà la priorità mantenendo tutto i dati del sensore che si trova accanto a esso associati. Se si usa non più di un punto di ancoraggio spaziale, arrestare l'accesso a un sistema di coordinate. In questo modo sarà relativa sottostante i dati del sensore da rimuovere come necessario.

Ciò è particolarmente importante per gli ancoraggi locali che viene reso persistente nell'archivio di ancoraggio spaziale. Verranno mantenuti i dati del sensore protetti da tali ancoraggi tutto in modo permanente per consentire all'app trovare tale ancoraggio in futuro sessioni di app, che consentiranno di ridurre lo spazio disponibile per tenere traccia di altri punti di ancoraggio. Vengono mantenute solo tali ancoraggi locali che è necessario trovare tra le sessioni future e rimuoverle dall'archivio quando non sono più significative per l'utente.

Per gli ancoraggi spaziali cloud, è possibile aumentare lo spazio di archiviazione come lo scenario richiede.  È possibile archiviare tutti gli ancoraggi cloud in base alle esigenze, rilasciarli solo quando si certi che gli utenti non dovrà individuare vntana che definiscono anche in questo caso.

## <a name="see-also"></a>Vedere anche
* [Sistemi di coordinate](coordinate-systems.md)
* [Condividere esperienze in realtà mista](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Anchor spaziali</a>
* [Persistenza in Unity](persistence-in-unity.md)
* [Ancoraggi spaziali in DirectX](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-spatial-anchors)
* [Case study: ricerca sui difetti nella realtà](case-study-looking-through-holes-in-your-reality.md)

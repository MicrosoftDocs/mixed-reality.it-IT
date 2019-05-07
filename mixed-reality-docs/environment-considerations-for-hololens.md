---
title: Considerazioni relative all'ambiente per HoloLens
description: Ottenere la migliore esperienza possibile con HoloLens quando si ottimizza il dispositivo per l'ambiente e gli occhi. Diversi fattori ambientali sono combinati insieme per abilitare il rilevamento, ma come uno sviluppatore di realtà mista, vi sono molti fattori è possibile tenere a mente per ottimizzare uno spazio per una migliore vntana.
author: dorreneb
ms.author: dobrown
ms.date: 04/22/2019
ms.topic: article
keywords: frame holographic, il campo visivo, campo di visualizzazione, calibrazione, spazi, ambiente, procedure
ms.openlocfilehash: 0070455792e09cd59741362b201ca6b7b9af0aec
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670175"
---
# <a name="environment-considerations-for-hololens"></a>Considerazioni relative all'ambiente per HoloLens

HoloLens combina il holographic con il mondo "real", l'inserimento di vntana nell'ambiente circostante. Una finestra dell'app holographic "Blocca" su una parete, una ballerina holographic ruota intorno al tavolo, orecchie coniglietto inseriti sopra head di un amico non intenzionale. Quando si usa un'app o giochi coinvolgenti, tutto il mondo holographic distribuirà fino a riempire l'ambiente circostante, ma sarà comunque possibile visualizzare e spostarsi all'interno dello spazio.

Il vntana che è inserire rimarrà in cui è stata posizionarli, anche se si disattiva il dispositivo. 

## <a name="setting-up-an-environment"></a>Configurazione di un ambiente

I dispositivi HoloLens saper stabile e accurato vntana da posizionare *rilevamento* gli utenti in uno spazio. Senza rilevamento corretto, il dispositivo non riconosce l'ambiente o l'utente all'interno di esso - vntana può vengono visualizzati in maniera errata, non vengono visualizzati nello stesso punto ogni volta o non essere visualizzato affatto.

Tenere traccia delle prestazioni dipende in larga misura dall'ambiente di cui che l'utente appartiene e l'ottimizzazione di un ambiente per indurre rilevamento stabile e coerenza è un'arte piuttosto che una scienza. Diversi fattori ambientali sono combinati insieme per abilitare il rilevamento, ma come uno sviluppatore di realtà mista, vi sono molti fattori è possibile tenere a mente per ottimizzare uno spazio per una gestione più efficiente.
 
### <a name="lighting"></a>Luce
Realtà mista di Windows utilizza chiaro visiva per rilevare la posizione dell'utente. Quando un ambiente è eccessiva, le fotocamere possono ottenere saturo e viene visualizzato nulla. Se l'ambiente è troppo scuro, le telecamere non possono prelevare le informazioni necessarie e viene visualizzato nulla. Illuminazione deve essere anche e sufficientemente chiaro che una persona possa visualizzare senza sforzo, ma non così luminosità che la luce non dover esaminare.

Le aree in cui sono presenti punti di luce in un'area globale dim sono anche problematici, come la fotocamera debba essere rispettate durante lo spostamento in e out del brillanti spazi. Ciò può causare il dispositivo per "ottenere perso" e che la modifica in luce equivale a una modifica nel percorso. Livelli di illuminazione stabili in un'area porterà a una gestione più efficiente.

Qualsiasi illuminazione può anche causare instabilità nello strumento di rilevamento, come il sole potrebbe variare notevolmente nel corso del tempo. Ad esempio, rilevamento nello stesso spazio nell'estate e invernali può produrre risultati significativamente diversi, come la luce secondhand esterno potrebbe essere elevata in diversi momenti dell'anno.

Se si dispone di un luxmeter, una costante lux 500 e 1000 è un buon punto di partenza. 

#### <a name="types-of-lighting"></a>Tipi di illuminazione
Tipi diversi di luci in uno spazio possono influenzare anche il rilevamento. Lampadine impulsi con l'energia elettrica CA in esecuzione tramite quest'ultimo - se la frequenza di AC è 50Hz, quindi la luce pulsa 50 Hz. Per un essere umano, non è notati questa attivazione. Tuttavia, fotocamera 30fps degli HoloLens rileva queste modifiche - alcuni fotogrammi sarà illuminati, alcuni sarà acceso male e alcune risorse in eccesso esporli come prova della fotocamera compensare la luce impulsi.

Negli Stati Uniti, frequenza di elettricità standard è 60Hz, pertanto sono armonizzate impulsi indicatore lampadina con una frequenza degli HoloLens: 60Hz impulsi allineano con una frequenza di 30 FPS degli Hololens. Tuttavia, molti paesi hanno uno standard di frequenza AC pari a 50Hz, che significa che verranno eseguite durante impulsi alcuni fotogrammi Hololens, mentre altre no. In particolare, fluorescenti in Europa sono noto per causare problemi. 

Esistono alcuni aspetti, che è possibile provare a risolvere i problemi di sfarfallio. Temperatura, l'età di bulbo e cicli di riscaldamento sono le cause più comuni di sfarfallio fluorescente e sostituendo bulbs può essere utile. È utile anche rafforzando bulbs e assicurandosi che consente di disegnare corrente sono costanti. 

### <a name="items-in-a-space"></a>Elementi in uno spazio
HoloLens Usa punti di riferimento dell'ambiente univoci, noto anche come *funzionalità*, per individuare se stesso in uno spazio. 

Un dispositivo non può quasi mai tenere traccia in un'area di funzionalità ridotte, mentre il dispositivo non ha modo di sapere dove nello spazio è. Aggiunta di funzionalità per i muri di uno spazio viene in genere un buon metodo per migliorare il rilevamento. Poster, simboli affisse su una parete, stabilimenti, oggetti univoci o altri elementi simili intera guida. Un tecnico disordinato è un buon esempio di un ambiente che conduce a rilevamento buona: esistono molte diverse funzionalità in una singola area. 

Inoltre, usano funzionalità univoche nello spazio stesso. Lo stesso poster ripetuto più volte su una parete, ad esempio, causa confusione di dispositivo come di HoloLens non sa quale dei poster ripetitive lo sta guardando. Un modo comune per l'aggiunta di funzionalità univoche consiste nell'utilizzare le righe del nastro di mascheramento per creare univoco, modelli nonrepetitve lungo pareti e parte intera di uno spazio. 

Una buona domanda da porsi è: se si verifica solo una piccola quantità di scena, è stato possibile è univocamente individuare manualmente nello spazio? In caso contrario, è probabile che il dispositivo disporrà anche monitoraggio dei problemi.

#### <a name="wormholes"></a>Tunnel spaziali
Se si dispone di due aree o le aree che hanno lo stesso aspetto, potrebbe considerare lo strumento di rilevamento che sono uguali. Il risultato è il dispositivo stesso indurre a pensare è in un'altra posizione. Chiamiamo questi tipi di aree ricorrenti *tunnel spaziali*. 

Per evitare tunnel spaziali, tentare di evitare le aree identiche nello stesso spazio. Aree identiche in alcuni casi possono includere le stazioni di factory, windows in un edificio, rack di server o workstation. Etichettatura aree o l'aggiunta di funzionalità univoche per ogni aree simile può mitigare tunnel spaziali.
 
### <a name="temporal-stability-of-a-space"></a>Stabilità temporali di uno spazio
Se l'ambiente è costantemente lo spostamento e la modifica, il dispositivo non dispone di alcuna funzionalità stabile per individuare rispetto. 

Più oggetti che sono in uno spazio, tra cui le persone, più facile risulterà la perdita di rilevamento. Lo spostamento nastri trasportatori, gli elementi in diversi stati di costruzione e un numero elevato di persone in un'area sono certo noti per causare problemi di rilevamento.
 
### <a name="proximity-of-the-user-to-items-in-the-space"></a>Prossimità dell'utente agli elementi nello spazio
Analogamente a come gli esseri umani non è possibile concentrare l'attenzione anche negli oggetti vicino gli occhi, HoloLens sfuggono quando gli oggetti si avvicinano relativo fotocamere. Se un oggetto è troppo stretta per essere visualizzato con entrambe le videocamere o se un oggetto sta bloccando una fotocamera, nel dispositivo sono molto più problemi con il rilevamento rispetto all'oggetto. 

Le fotocamere possono vedere non meno di 15cm da un oggetto.
 
### <a name="surfaces-in-a-space"></a>Superfici in uno spazio
Le superfici fortemente riflettente avrà un aspetto probabilmente diverse a seconda l'angolo, che influisce sul rilevamento. Pensare a una nuova auto - quando si sposta intorno a esso, rifletta luce e diversi oggetti nell'area di sono visibili durante lo spostamento. Allo strumento di rilevamento, dei diversi oggetti riflesse nella superficie rappresentano un ambiente in evoluzione e rilevamento perde il dispositivo.

Meno oggetti shiny sono più semplici tenere traccia in.

### <a name="wifi-fingerprint-considerations"></a>Considerazioni sulle impronte digitali Wi-Fi
Purché Wi-Fi sono abilitata, i dati della mappa verranno correlati con un'impronta digitale Wi-Fi, anche quando non è connesso a un'effettiva Wi-Fi/router di rete. Senza informazioni di connessione Wi-Fi, potrebbe essere leggermente più lente riconoscere lo spazio e vntana. Se i segnali Wi-Fi cambiare significativamente, il dispositivo potrebbe pensare che è completamente in un altro spazio.

Identificazione di rete (SSID, ad esempio, indirizzo MAC) non vengono inviate a Microsoft e Wi-Fi tutti i riferimenti vengono mantenuti locali di HoloLens.

## <a name="mapping-new-spaces"></a>Nuovi spazi di mapping
Quando si immette un nuovo spazio (o si carica uno esistente), si noterà un grafico di rete mesh di diffondersi tramite lo spazio. Ciò significa che il dispositivo sia [mapping l'ambiente circostante](spatial-mapping-design.md). 

Se si verificano problemi durante l'inserimento vntana, provare a scorrere tutto lo spazio in modo HoloLens possibile eseguirne il mapping più completo. 

Se il HoloLens non è possibile eseguire il mapping lo spazio o all'esterno di calibrazione, è possibile immettere modalità Limited. In modalità Limited, sarà possibile inserire vntana nell'ambiente circostante.

## <a name="environment-management"></a>Gestione dell'ambiente
Sono disponibili due impostazioni che consentono agli utenti per "pulire" ologrammi e causa HoloLens "dimentichi" uno spazio.  Esistono in "Ologrammi e ambienti" nell'app impostazioni, con la seconda impostazione anche visualizzati in "Privacy" nell'app impostazioni.

1.  Elimina nelle vicinanze vntana: se si seleziona questa impostazione, HoloLens cancellerà vntana tutto ancorati e tutti i dati di mapping stored per "spazio corrente" in cui si trova il dispositivo.  Una nuova sezione mappa potrebbe essere creata e archiviata nel database per tale percorso dopo Vntana anche in questo caso viene posizionati in tale spazio stesso.

2.  Eliminare vntana tutte, se si seleziona questa impostazione, HoloLens verranno cancellati tutti i dati della mappa e ancorata vntana nei database interi di spazi.  Non verranno essere nuovamente individuate alcuna ologrammi e qualsiasi vntana desidera essere appena inserite per archiviare nuovamente le sezioni di mapping nel database.

### <a name="managing-your-spaces"></a>Gestire gli spazi

Le sezioni di mappa e diversi spazi sono state compresse in un unico database, archiviato in locale nel dispositivo HoloLens. Il database della mappa verrà archiviato in modo sicuro, con accesso solo disponibile per il sistema interno e mai da un utente del dispositivo, anche quando collegata a un PC e/o usando l'app Esplora file. Quando bitlocker è abilitato, i dati di mapping stored vengono anche crittografati.

I componenti della mappa più esistono quando vntana viene inserite in posizioni diverse senza un percorso tra i percorsi/vntana operatività.  Ologrammi ancorate all'interno della stessa sezione mappa sono considerati "nelle vicinanze" nell'area corrente.

È un'API per esportare un piccolo subset dello "spazio" per sviluppatori (una parte del componente di mappa che è attualmente riconosciuto) per abilitare scenari ologrammi condiviso.  Non è attualmente alcun meccanismo per il download dell'intero database di tutti gli spazi che sono stati mappati.


## <a name="hologram-quality"></a>Qualità ologrammi

Ologrammi possono essere inseriti all'interno dell'ambiente, ovvero elevata, bassa e tutto è, ma sarà possibile visualizzarli un [frame holographic](holographic-frame.md) che è posizionato davanti ai tuoi occhi. Per ottenere la visualizzazione migliore, assicurarsi di regolare il dispositivo in modo che è possibile visualizzare l'intero fotogramma. E non esitare a spostano l'ambiente ed esplorare.

Per i [vntana](hologram.md) per essere precisi, chiaro e stabile, deve essere tarato appositamente per te di HoloLens. Quando si configura prima di tutto di HoloLens, informazioni dettagliate tramite questo processo. In un secondo momento se vntana aspetto non è corretto o si verificano numerosi errori, è possibile apportare modifiche.

### <a name="calibration"></a>Calibrazione

Se il vntana aspetto instabilità o traballanti o se si verificano problemi durante l'inserimento vntana, la prima operazione da eseguire è la [calibrazione app](calibration.md). Questa app è utile anche se si verificano durante l'utilizzo di HoloLens qualsiasi disturbo.

Per accedere all'app calibrazione, passare a Impostazioni > sistema > utilità. Selezionare Open calibrazione e seguire le istruzioni.

Se si esegue l'app di calibrazione e continuano a verificarsi problemi con una qualità ologrammi o un messaggio viene visualizzato "rilevamento persi" frequenti, provare l'app di ottimizzazione del sensore. Passare a Impostazioni > sistema > utilità, selezionare ottimizzazione sensore Open e seguire le istruzioni.

Se un altro utente sta per essere usando il HoloLens, deve essere eseguito l'app di calibrazione prima di tutto in modo che il dispositivo sia configurato correttamente per loro.

## <a name="see-also"></a>Vedere anche
* [Progettazione del mapping spaziale](spatial-mapping-design.md)
* [Ologrammi](hologram.md)
* [Calibrazione](calibration.md)

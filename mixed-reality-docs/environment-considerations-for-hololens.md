---
title: Considerazioni sull'ambiente per HoloLens
description: Ottenere la migliore esperienza possibile usando HoloLens quando si ottimizza il dispositivo per gli occhi e l'ambiente. Molti fattori ambientali diversi sono Uniti per consentire il rilevamento, ma come sviluppatore di realtà mista, esistono diversi fattori che è possibile tenere presente per ottimizzare uno spazio per gli ologrammi migliori.
author: dorreneb
ms.author: dobrown
ms.date: 04/22/2019
ms.topic: article
keywords: frame olografico, campo di visualizzazione, FOV, calibrazione, spazi, ambiente, procedure
ms.openlocfilehash: 0070455792e09cd59741362b201ca6b7b9af0aec
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670175"
---
# <a name="environment-considerations-for-hololens"></a>Considerazioni sull'ambiente per HoloLens

HoloLens unisce il olografico al mondo "reale", posizionando gli ologrammi negli ambienti. Una finestra dell'app olografica "si blocca" sulla parete, una ballerina olografica ruota sul tavolo, le orecchie conigliere si trovano sopra il capo dell'amico. Quando si usa un gioco o un'app immersiva, il mondo olografico si diffonderà per soddisfare le proprie esigenze, ma sarà comunque possibile vedere e spostarsi nello spazio.

Gli ologrammi immessi resteranno nella posizione in cui sono stati inseriti, anche se si disattiva il dispositivo. 

## <a name="setting-up-an-environment"></a>Configurazione di un ambiente

I dispositivi HoloLens sanno come collocare ologrammi stabili e accurati *monitorando* gli utenti in uno spazio. Senza un rilevamento appropriato, il dispositivo non riconosce l'ambiente o l'utente al suo interno. in questo modo gli ologrammi possono apparire in posizioni errate, non vengono visualizzati nello stesso punto ogni volta o non vengono visualizzati.

Il monitoraggio delle prestazioni è fortemente influenzato dall'ambiente in cui si trova l'utente e l'ottimizzazione di un ambiente per indurre un rilevamento stabile e coerente è un'arte piuttosto che una scienza. Molti fattori ambientali diversi sono Uniti per consentire il rilevamento, ma come sviluppatore di realtà mista, esistono diversi fattori che è possibile tenere presente per ottimizzare uno spazio per una migliore verifica.
 
### <a name="lighting"></a>Luce
La realtà mista di Windows usa la luce visiva per tenere traccia della posizione dell'utente. Quando un ambiente è troppo luminoso, le fotocamere possono essere saturate e non viene visualizzato nulla. Se l'ambiente è troppo scuro, le fotocamere non possono raccogliere informazioni sufficienti e non viene visualizzato nulla. L'illuminazione dovrebbe essere ancora e sufficientemente luminosa che un uomo può vedere senza sforzo, ma non è così chiaro che la luce è dolorosa da analizzare.

Anche le aree in cui sono presenti punti di luce chiara in un'area di Dim complessiva sono problematiche, in quanto la fotocamera deve adattarsi quando si trasferiscono e si esauriscono gli spazi luminosi. Ciò può comportare la perdita del dispositivo e pensare che la modifica alla luce equivale a una modifica della posizione. I livelli di luce stabili in un'area consentiranno un rilevamento migliore.

Qualsiasi illuminazione esterna può anche causare instabilità nello strumento di rilevamento, perché il sole può variare notevolmente nel tempo. Ad esempio, il rilevamento nello stesso spazio dell'estate rispetto a quello invernale può produrre risultati notevolmente diversi, perché la luce di seconda generazione può essere più alta in momenti diversi dell'anno.

Se si dispone di un luxmetro, una soluzione stabile 500-1000 Lux è un punto di partenza valido. 

#### <a name="types-of-lighting"></a>Tipi di illuminazione
I diversi tipi di luce in uno spazio possono influenzare anche il rilevamento. Pulse lampadina con l'elettricità AC che esegue l'it: se la frequenza AC è 50Hz, gli impulsi luce a 50Hz. Per un uomo, questo pulsante non viene notato. Tuttavia, la videocamera HoloLens ' 30fps vede queste modifiche. alcuni frame saranno ben illuminati, alcuni saranno poco illuminati e alcuni verranno sovraesposti perché la fotocamera tenta di compensare gli impulsi luminosi.

Negli Stati Uniti, la frequenza di energia elettrica standard è 60Hz, quindi gli impulsi a forma di lampadina sono armonizzati con HoloLens ' framerate-60Hz impulsi allineati con Hololens '30 FPS framerate. Tuttavia, molti paesi hanno un standard di frequenza AC di 50Hz, il che significa che alcuni frame Hololens verranno presi durante gli impulsi e altri no. In particolare, l'illuminazione fluorescente in Europa è nota per causare problemi. 

Ci sono alcuni elementi che è possibile provare a risolvere i problemi di sfarfallio. La temperatura, la durata del bulbo e i cicli di riscaldamento sono cause comuni di sfarfallio fluorescente e la sostituzione delle lampadine può essere utile. È anche possibile ridurre le lampadine e verificare che le estrazioni correnti siano costanti. 

### <a name="items-in-a-space"></a>Elementi in uno spazio
HoloLens usa i punti di interesse ambientali univoci, noti anche come *funzionalità*, per individuarsi in uno spazio. 

Un dispositivo non è quasi mai in grado di tenere traccia di un'area priva di funzionalità, in quanto il dispositivo non ha modo di sapere dove si trova nello spazio. L'aggiunta di funzionalità alle pareti di uno spazio è in genere un metodo efficace per migliorare il rilevamento. Poster, simboli registrati su un muro, piante, oggetti univoci o altri elementi simili. Una scrivania complessa è un valido esempio di un ambiente che conduce a una buona traccia, in un'unica area sono disponibili numerose funzionalità diverse. 

Inoltre, utilizzare funzionalità esclusive nello stesso spazio. Lo stesso poster ripetuto più volte su una parete, ad esempio, causerebbe confusione del dispositivo perché il HoloLens non saprà quale dei poster ripetitivi sta esaminando. Un modo comune per aggiungere funzionalità esclusive consiste nell'usare le linee del nastro di mascheramento per creare modelli univoci, nonrepetitve lungo i muri e il piano di uno spazio. 

Una domanda da porsi è: se si è visto solo una piccola parte della scena, è possibile individuarla in modo univoco nello spazio? In caso contrario, è probabile che si verifichino problemi di rilevamento del dispositivo.

#### <a name="wormholes"></a>Wormholes
Se sono presenti due aree o aree con aspetto identico, lo strumento di rilevamento potrebbe pensare che siano uguali. In questo modo, il dispositivo si ingannerà a pensare che sia altrove. Questi tipi di aree temporali vengono denominati. 

Per evitare i wormhole, provare a impedire aree identiche nello stesso spazio. Le aree identiche possono talvolta includere stazioni Factory, Windows in una compilazione, rack server o stazioni di lavoro. L'assegnazione di etichette alle aree o l'aggiunta di funzionalità univoche a ogni area simile può contribuire a mitigare i tunnel.
 
### <a name="temporal-stability-of-a-space"></a>Stabilità temporale di uno spazio
Se l'ambiente viene costantemente spostato e modificato, il dispositivo non dispone di funzionalità stabili da individuare. 

Maggiore è il numero di oggetti che si trovano in uno spazio, incluse le persone, più semplice è la perdita del rilevamento. Il trasferimento di nastri trasportatori, elementi in diversi Stati di costruzione e molte persone in uno spazio è stato noto a causare problemi di rilevamento.
 
### <a name="proximity-of-the-user-to-items-in-the-space"></a>Prossimità dell'utente agli elementi nello spazio
Analogamente al modo in cui gli utenti non possono concentrarsi bene sugli oggetti vicini agli occhi, HoloLens lotte quando gli oggetti sono vicini alle fotocamere. Se un oggetto è troppo vicino per essere visualizzato con entrambe le fotocamere o se un oggetto blocca una fotocamera, il dispositivo presenta molti più problemi di rilevamento per l'oggetto. 

Le fotocamere possono non essere più vicine a 15 cm da un oggetto.
 
### <a name="surfaces-in-a-space"></a>Superfici in uno spazio
Le superfici fortemente riflettenti saranno probabilmente diverse a seconda dell'angolo, che influiscono sul rilevamento. Si pensi a una nuova auto: quando ci si sposta, la luce riflette e si visualizzano oggetti diversi nella superficie mentre si sposta. Per lo strumento di rilevamento, i diversi oggetti riflessi nella superficie rappresentano un ambiente mutevole e il dispositivo perde la traccia.

Gli oggetti meno lucidi sono più facili da rilevare.

### <a name="wifi-fingerprint-considerations"></a>Considerazioni sulle impronte digitali WiFi
Se il Wi-Fi è abilitato, i dati della mappa saranno correlati con un'impronta digitale Wi-Fi, anche quando non sono connessi a una rete o un router WiFi effettivo. Senza informazioni Wi-Fi, lo spazio e gli ologrammi possono essere leggermente più lenti per essere riconosciuti. Se i segnali WiFi cambiano in modo significativo, il dispositivo può ritenere che si trovi in uno spazio diverso.

L'identificazione di rete (ad esempio, SSID, indirizzo MAC) non viene inviata a Microsoft e tutti i riferimenti Wi-Fi vengono mantenuti locali nella HoloLens.

## <a name="mapping-new-spaces"></a>Mapping di nuovi spazi
Quando si immette un nuovo spazio (o se ne carica uno esistente), viene visualizzata una grafica mesh che si estende sullo spazio. Ciò significa che il dispositivo sta [eseguendo il mapping dell'ambiente](spatial-mapping-design.md). 

Se si verificano problemi nel posizionamento degli ologrammi, provare a aggirare lo spazio in modo che HoloLens possa eseguirne il mapping più completamente. 

Se il HoloLens non è in grado di eseguire il mapping dello spazio o non è disponibile, è possibile attivare la modalità Limited. In modalità limitata, non sarà possibile posizionare gli ologrammi nell'ambiente in uso.

## <a name="environment-management"></a>Gestione dell'ambiente
Sono disponibili due impostazioni che consentono agli utenti di "pulire" gli ologrammi e causare a HoloLens di "dimenticare" uno spazio.  Sono presenti in "ologrammi e ambienti" nell'app Impostazioni, con la seconda impostazione visualizzata anche in "privacy" nell'app Impostazioni.

1.  Elimina gli ologrammi vicini: se si seleziona questa impostazione, HoloLens cancellerà tutti gli ologrammi ancorati e tutti i dati della mappa archiviati per lo "spazio corrente" in cui si trova il dispositivo.  Una nuova sezione della mappa verrà creata e archiviata nel database per la posizione in cui gli ologrammi vengono inseriti di nuovo nello stesso spazio.

2.  Elimina tutti gli ologrammi: se si seleziona questa impostazione, HoloLens cancellerà tutti i dati della mappa e gli ologrammi ancorati nell'intero database di spazi.  Nessun ologramma verrà riindividuato ed è necessario posizionare di nuovo gli ologrammi per archiviare di nuovo le sezioni della mappa nel database.

### <a name="managing-your-spaces"></a>Gestione degli spazi

Le sezioni della mappa e gli spazi diversi sono stati compressi in un singolo database, archiviati localmente nel dispositivo HoloLens. Il database della mappa viene archiviato in modo sicuro, con accesso solo al sistema interno e mai a un utente del dispositivo, anche se collegato a un PC e/o usando l'app Esplora file. Quando BitLocker è abilitato, anche i dati della mappa archiviati vengono crittografati.

Quando gli ologrammi vengono posizionati in posizioni diverse senza un percorso connettivo tra le posizioni o gli ologrammi, esistono più componenti della mappa.  Gli ologrammi ancorati all'interno della stessa sezione della mappa sono considerati "adiacenti" nello spazio corrente.

È disponibile un'API per sviluppatori per esportare un piccolo subset dello "spazio corrente" (parte del componente mappa attualmente riconosciuto) per abilitare gli scenari con ologrammi condivisi.  Attualmente non è disponibile alcun meccanismo per scaricare l'intero database di tutti gli spazi di cui è stato eseguito il mapping.


## <a name="hologram-quality"></a>Qualità ologramma

Gli ologrammi possono essere posizionati in tutto l'ambiente, ad alta, bassa e tutti gli elementi, ma sono visibili tramite un [frame olografico](holographic-frame.md) che si trova davanti agli occhi. Per ottenere la visualizzazione migliore, assicurarsi di modificare il dispositivo in modo che sia possibile visualizzare l'intero frame. E non esitare a esplorare l'ambiente ed esplorare.

Affinché gli [ologrammi](hologram.md) risultino nitide, chiare e stabili, la HoloLens deve essere calibrata solo per l'utente. Quando si configura il HoloLens per la prima volta, verrà illustrato questo processo. In un secondo momento, se gli ologrammi non sembrano corretti o se vengono visualizzati numerosi errori, è possibile apportare modifiche.

### <a name="calibration"></a>Calibrazione

Se gli ologrammi sembrano nervosi o vacillanti o se si verificano problemi nell'inserire gli ologrammi, la prima cosa da provare è l' [app di calibrazione](calibration.md). Questa app può anche essere utile se si riscontrano problemi durante l'uso di HoloLens.

Per accedere all'app Calibration, passare a Settings > System > Utilities. Selezionare Open Calibration e seguire le istruzioni.

Se si esegue l'app di calibrazione e si verificano ancora problemi con la qualità dell'ologramma o se viene visualizzato un messaggio di "rilevamento perso", provare l'app per la regolazione del sensore. Passare a Impostazioni > Utilità di sistema >, selezionare Apri ottimizzazione sensore e seguire le istruzioni.

Se un altro utente sta usando il HoloLens, deve eseguire prima l'app di calibrazione in modo che il dispositivo sia configurato correttamente.

## <a name="see-also"></a>Vedere anche
* [Progettazione del mapping spaziale](spatial-mapping-design.md)
* [Ologrammi](hologram.md)
* [Calibrazione](calibration.md)

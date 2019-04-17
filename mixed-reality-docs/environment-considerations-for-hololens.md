---
title: Considerazioni relative all'ambiente per HoloLens
description: Ottenere la migliore esperienza possibile con HoloLens quando si ottimizza il dispositivo per l'ambiente e gli occhi.
author: thetuvix
ms.author: msamples
ms.date: 02/24/2019
ms.topic: article
keywords: frame holographic, il campo visivo, campo di visualizzazione, calibrazione, spazi, ambiente, procedure
ms.openlocfilehash: d5433dc923aeb70e3ae82e75c9358d3a569e8f83
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59601293"
---
# <a name="environment-considerations-for-hololens"></a>Considerazioni relative all'ambiente per HoloLens

HoloLens combina il holographic con il mondo "real", l'inserimento di vntana nell'ambiente circostante. Una finestra dell'app holographic "Blocca" su una parete, una ballerina holographic ruota intorno al tavolo, orecchie coniglietto inseriti sopra head di un amico non intenzionale. Quando si usa un'app o giochi coinvolgenti, tutto il mondo holographic distribuirà fino a riempire l'ambiente circostante, ma sarà comunque possibile visualizzare e spostarsi all'interno dello spazio.

Il vntana che è inserire rimarrà in cui è stata posizionarli, anche se si disattiva il dispositivo. 

Ecco alcuni aspetti da tenere presente per risultati ottimali con il mondo holographic. Si noti che, HoloLens sono progettato per essere utilizzato in ambienti chiusi in uno spazio sicuro con non risultare positive. Non usarlo durante a piedi o in esecuzione altre attività che richiedono attenzione completo.

## <a name="spaces"></a>Spazi

HoloLens rileva lo spazio in modo che è possibile memorizzare in cui si trovano vntana. HoloLens è possibile memorizzare in più spazi ed è progettato per caricare lo spazio corretto quando si attiva.

### <a name="setting-up"></a>Impostazione di

HoloLens può eseguire il mapping e ricordare gli spazi meglio se si sceglie l'ambiente corretto.
* Usare una chat con chiaro adeguata e una notevole quantità di spazio. Evitare gli spazi scuri e chat con molta superfici scure, shiny o semitrasparente (come mirror o tende thin).
* Se si desidera HoloLens per informazioni su uno spazio, faccia la realtà direttamente, da circa un contatore da subito.
* Evitare gli spazi con molti oggetti in movimento. Se un elemento è stato spostato e si desidera HoloLens per informazioni su una nuova posizione (ad esempio, è stato spostato la tabella di caffè a una nuova sensibile), estasiati e spostare intorno a esso.

### <a name="spatial-mapping"></a>Mapping spaziale

Quando si immette un nuovo spazio (o si carica uno esistente), si noterà un grafico di rete mesh di diffondersi tramite lo spazio. Ciò significa che il dispositivo sia [mapping l'ambiente circostante](spatial-mapping-design.md). Se si verificano problemi durante l'inserimento vntana, provare a scorrere tutto lo spazio in modo HoloLens possibile eseguirne il mapping più completo. Se il HoloLens non è possibile eseguire il mapping lo spazio o all'esterno di calibrazione, è possibile immettere modalità Limited. In modalità Limited, sarà possibile inserire vntana nell'ambiente circostante.

### <a name="managing-your-spaces"></a>Gestire gli spazi

Le sezioni di mappa e diversi spazi sono state compresse in un unico database, archiviato in locale nel dispositivo HoloLens.  Il database della mappa verrà archiviato in modo sicuro, con accesso solo disponibile per il sistema interno e mai da un utente del dispositivo, anche quando collegata a un PC e/o usando l'app Esplora file.  Quando bitlocker è abilitato, i dati di mapping stored vengono anche crittografati.
I componenti della mappa più esistono quando vntana viene inserite in posizioni diverse senza un percorso tra i percorsi/vntana operatività.  Ologrammi ancorate all'interno della stessa sezione mappa sono considerati "nelle vicinanze" nell'area corrente sono è un'API per esportare un piccolo subset dello "spazio" per sviluppatori (una parte del componente di mappa che è attualmente riconosciuto) per abilitare scenari ologrammi condiviso.  Non è attualmente alcun meccanismo per il download dell'intero database di tutti gli spazi che sono stati mappati.

#### <a name="wifi"></a>WiFi
Visual Studio connesso. Non – purché Wi-Fi sono abilitata, i dati della mappa verranno correlati con un'impronta digitale Wi-Fi, anche quando non è connesso a un'effettiva Wi-Fi/router di rete.  Infatti, il MAC indirizzo e forza del segnale (vale a dire con impronta digitale Wi-Fi) di un router è disponibile senza connettersi a esso.  Identificazione di rete (SSID, ad esempio, indirizzo MAC) non vengono inviate a Microsoft e Wi-Fi tutti i riferimenti vengono mantenuti locali di HoloLens.

Visual Studio abilitata. Disabilitata: HoloLens verrà rilevare e ricordare spazi anche quando sono disabilitata Wi-Fi, archiviando in modo sicuro i dati del sensore quando viene inseriti vntana.  Senza le informazioni di connessione Wi-Fi, lo spazio e vntana potrebbe essere leggermente più lente riconoscere in un secondo momento, quando le esigenze di HoloLens confrontare le analisi attive a tutti gli ancoraggi ologrammi e sezioni di mapping archiviate nel dispositivo per poter "relocalize" alla parte destra della mappa.

#### <a name="environment-management"></a>Gestione dell'ambiente
Esistono 2 impostazioni che consentono agli utenti per "pulire" ologrammi e causa HoloLens "dimentichi uno spazio".  Esistono in "Ologrammi e ambienti" nell'app impostazioni, con la seconda impostazione anche visualizzati in "Privacy" nell'app impostazioni.
1.  Elimina nelle vicinanze vntana: se si seleziona questa impostazione, HoloLens cancellerà vntana tutto ancorati e tutti i dati di mapping stored per "spazio corrente" in cui si trova il dispositivo.  Una nuova sezione mappa potrebbe essere creata e archiviata nel database per tale percorso dopo Vntana anche in questo caso viene posizionati in tale spazio stesso.
2.  Eliminare vntana tutte, se si seleziona questa impostazione, HoloLens verranno cancellati tutti i dati della mappa e ancorata vntana nei database interi di spazi.  Non verranno essere nuovamente individuate alcuna ologrammi e qualsiasi vntana desidera essere appena inserite per archiviare nuovamente le sezioni di mapping nel database.


## <a name="hologram-quality"></a>Qualità ologrammi

Ologrammi possono essere inseriti all'interno dell'ambiente, ovvero elevata, bassa e tutto è, ma sarà possibile visualizzarli un [frame holographic](holographic-frame.md) che è posizionato davanti ai tuoi occhi. Per ottenere la visualizzazione migliore, assicurarsi di regolare il dispositivo in modo che è possibile visualizzare l'intero fotogramma. E non esitare a spostano l'ambiente ed esplorare.

Per i [vntana](hologram.md) per essere precisi, chiaro e stabile, deve essere tarato appositamente per te di HoloLens. Quando si configura prima di tutto di HoloLens, informazioni dettagliate tramite questo processo. In un secondo momento se vntana aspetto non è corretto o si verificano numerosi errori, è possibile apportare modifiche.

### <a name="calibration"></a>Calibrazione

Se il vntana aspetto instabilità o traballanti o se si verificano problemi durante l'inserimento vntana, la prima operazione da eseguire è la [calibrazione app](calibration.md). Questa app è utile anche se si verificano durante l'utilizzo di HoloLens qualsiasi disturbo.

Per accedere all'app calibrazione, passare a Impostazioni > sistema > utilità. Selezionare Open calibrazione e seguire le istruzioni.

Se si esegue l'app di calibrazione e continuano a verificarsi problemi con una qualità ologrammi o un messaggio viene visualizzato "rilevamento persi" frequenti, provare l'app di ottimizzazione del sensore. Passare a Impostazioni > sistema > utilità, selezionare ottimizzazione sensore Open e seguire le istruzioni.

Se un altro utente sta per essere usando il HoloLens, deve essere eseguito l'app di calibrazione prima di tutto in modo che il dispositivo sia configurato correttamente per loro.

## <a name="see-also"></a>Vedere anche
* [Progettazione di mapping spaziale](spatial-mapping-design.md)
* [Ologrammi](hologram.md)
* [Calibrazione](calibration.md)

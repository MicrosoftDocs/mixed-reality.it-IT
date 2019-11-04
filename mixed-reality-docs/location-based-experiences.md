---
title: Divertimenti location based con la realtà mista di Windows
description: Ottenere l'accesso agli oggetti nativi olografici sottostanti in Unity.
author: jessemcculloch
ms.author: ishitak
ms.date: 08/22/2019
ms.topic: article
keywords: realtà mista, VR, LBE, località
ms.openlocfilehash: de9cfdaca77574bbbbec96c2e94fddeaa2712c33
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437936"
---
# <a name="location-based-entertainment-with-windows-mixed-reality"></a>Divertimenti location based con la realtà mista di Windows

Negli ultimi due anni abbiamo assistito a una straordinaria quantità di crescita e innovazione nella categoria di intrattenimento location based. Le sedi tradizionali come parchi tematici e teatri hanno iniziato a offrire esperienze coinvolgenti e multiplayer come esperienze gratuite per le corse e le installazioni esistenti. Nuovi operatori e sedi hanno un'esperienza multisensoriale e multiplayer a prezzi attraenti per le masse. Tutte queste esperienze eseguono il push della busta per quanto possibile con la realtà mista.

Questo documento è una guida per iniziare a usare la realtà mista di Windows nella categoria di intrattenimento location based. Le linee guida riportate di seguito possono inoltre essere valide per le esperienze basate sulla posizione, oltre ad esempio per la formazione, la progettazione di prodotti o altri casi d'uso.

## <a name="engineering-faq"></a>Domande frequenti sulla progettazione

### <a name="hardware"></a>Hardware

**D: quali componenti hardware sono disponibili da Microsoft e dai relativi partner che è possibile utilizzare nell'installazione?**

R: Microsoft e i suoi partner OEM offrono un portfolio interessante di dispositivi tra cui scegliere a seconda delle esigenze.  

Se le esperienze fornite ai clienti necessitano di auricolari per la realtà virtuale, i seguenti auricolari sul mercato di HP, Samsung e Acer sono un'ottima soluzione. Ogni auricolare presenta attributi distinti. Ulteriori dettagli su ognuno di essi.

Riverb di HP: [Dettagli](https://hp.com/go/Reverbpro)

Samsung Odyssey +: [Dettagli](https://www.samsung.com/us/computing/hmd/windows-mixed-reality/hmd-odyssey-windows-mixed-reality-headset-xe800zba-hc1us/)

Acer: [Dettagli](https://www.acer.com/ac/en/US/content/model/VD.R05AP.002)

Se la località si specializza in esperienze di realtà miste o potenziate che richiedono l'uso di una cuffia da visualizzare a lungo, è possibile ottenere Microsoft HoloLens 2 (ora aperto per gli interessi pre-ordinati).  

HoloLens 2: [interesse pre-ordinato](https://www.microsoft.com//hololens/buy)

Se si sperimentano esperienze che richiedono funzionalità avanzate per la visione artificiale, il riconoscimento vocale e il corpo, è possibile che l'ambiente Kinect di Azure sia in grado di soddisfare le proprie esigenze.  

Kinect di Azure: [Dettagli](https://azure.microsoft.com//services/kinect-dk/)

**D: qual è il portfolio dei PC zaino che è possibile usare per eseguire le esperienze VR con tethering PC?**

Per le esperienze VR con tethering del PC, gli OEM offrono un'incredibile selezione di PC zaino creati esattamente per le esigenze.

HP ha appena lanciato il proprio HP VR Backpack G2, il PC indossabile più potente del mondo, ottimizzato per le esperienze di roaming gratuito, ora con una potenza del 30% superiore con una GPU RTX 2080 all'interno. [Dettagli](https://www8.hp.com/us/en/vr/vr-backpack.html)

### <a name="setup"></a>Installazione

**D: come è possibile configurare più facilmente il programma di installazione e personalizzare il portale per la realtà mista per LBE?**

>[!NOTE]
>Questa funzionalità richiede la versione 2000.19061.1011.0 o successiva.  

È possibile che sia necessaria una maggiore personalizzazione del portale di realtà mista rispetto a quello normalmente disponibile tramite l'app per la distribuzione di app in chioschi o esperienze personalizzate. L'ultimo aggiornamento di luglio del portale per realtà mista supporta diverse impostazioni avanzate che possono essere eseguite tramite un file di configurazione per eseguire le operazioni seguenti:  

Consenti controlli di sistema non riusciti: in genere il processo di configurazione controlla la compatibilità del PC con la realtà mista di Windows prima di completare l'installazione. Il bypass di questo può causare problemi quando si tenta di eseguire la realtà mista di Windows in caso di problemi di compatibilità.  

Ignora app complementare dispositivi: il DCA fornisce le procedure di configurazione specifiche dell'auricolare fornite dal produttore e consente di aggiornare il firmware dell'auricolare.  

Ignora la configurazione della chat room: anziché richiedere la creazione di un limite per la stanza, è possibile passare direttamente all'auricolare in modalità di seduta/in piedi.  

Ignora l'installazione delle app dallo Store-il programma di installazione normale installa diverse app dello Store, tra cui il visualizzatore 3D e il componente aggiuntivo Visualizzatore perimetrale 360. Questa operazione ignorerà l'installazione di queste app, ma è possibile che manchi la funzionalità del dispositivo.  

Mostra anteprima a schermo intero: il portale per la realtà mista visualizzerà automaticamente l'anteprima dell'auricolare a schermo intero nel PC desktop mentre è in uso l'auricolare.  

Nascondi nuovo per il pannello laterale. in questo modo si impedisce l'espansione del nuovo pannello per l'utente all'avvio del portale di realtà mista.  

#### <a name="how-to-configure"></a>Come configurare:  

Per impostare una di queste configurazioni, è necessario creare un file denominato _userconfig. JSON_ in questa directory: _$env: LOCALAPPDATA\Packages\Microsoft.MixedReality.Portal_8wekyb3d8bbwe\LocalState\\_

Per la maggior parte degli utenti, questo aspetto sarà simile a _C:\Users\<username > \AppData\Local\Packages\microsoft.mixedreality.portal_8wekyb3d8bbwe\LocalState\\_

Il file JSON deve avere il seguente contenuto con "true" impostato per una delle impostazioni precedenti che si vuole abilitare:  

```
{

  "shouldAllowFailedSystemChecks": true,

  "shouldSkipDcaApp": true,

  "shouldSkipRoomSetup": true,

  "shouldSkipStoreAppInstall": true,

  "shouldShowPreviewFullScreen": true,

  "shouldHideEngagementPane": true

}
```
 
**D: sono disponibili istruzioni per la configurazione di playspace?**

R: la configurazione di una playspace deve essere eseguita come se si trattasse di un'esperienza di installazione del consumer. Il processo di configurazione della chat consente inoltre di definire i limiti delle chat room. Altre informazioni sulla configurazione dei limiti delle chat possono essere lette [qui](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary).

Come illustrato nel documento precedente, il numero massimo ragionevole di coordinate singole playspace è intorno a 5mx5m. Se si vuole avere un'area più grande, è possibile usare la funzionalità ancoraggi spaziali nello stack di API olografico di Windows. L'uso di questa API richiederà una progettazione personalizzata nelle esperienze da produrre.  

Altre informazioni su come ottimizzare il contenuto per diverse dimensioni di spazio possono essere lette [qui](https://docs.microsoft.com//windows/mixed-reality/coordinate-systems).
 

**D: lo spazio è troppo grande e si verificano errori quando si tenta di configurare un'esperienza permanente con i limiti. Cosa devo fare per configurare il lavoro di un'esperienza di roaming libero di grandi dimensioni?**

R: per impostare uno spazio maggiore di ~ 18x18ft, non sarà possibile usare l'esperienza limite fornita dal sistema.  I sistemi di limiti si basano sull'uso di una singola coordinata fissa "Anchor", che può diventare instabile quando un utente è troppo lontano dall'ancoraggio della fase centrale. 

In alternativa, è possibile impostare la modalità "in sede", che non visualizzerà il limite o configurerà i limiti di una fase o playspace.  Quindi, sarà necessario configurare più ancoraggi spaziali all'interno dell'app per fare riferimento ad aree di limiti fisici. 

Lo sviluppatore di applicazioni è responsabile di visualizzare le misure di sicurezza necessarie in modo che gli utenti non entrino in conflitto con l'ambiente fisico.  Questi possono essere muri digitali all'interno dell'esperienza o un oggetto visivo limite del gioco personalizzato. 

Informazioni aggiuntive sulla configurazione del limite della stanza con WMR sono disponibili [qui](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary).

**D: dove si trova l'origine del playspace?**

R: l'origine del playspace è determinata dall'esperienza di installazione della chat room, in particolare la posizione di HMD quando viene premuto il pulsante centrale durante l'installazione. 

### <a name="multi-player-setup"></a>CONFIGURAZIONE DI PIÙ GIOCATORI

**D: si sta distribuendo un'esperienza multiplayer in alla mia sede. È supportato per la realtà mista di Windows?**

R: lo strumento di pacchetto di dati spaziali per la realtà mista è una funzionalità beta che consente di localizzare più giocatori nello stesso spazio abilitando il porting dei dati spaziali da un PC a un altro. È possibile accedere allo strumento e ottenere ulteriori informazioni su [di esso.](mixedrealityspatialdatapackager.md)

Se si opta per le compilazioni Windows 20H1 o versioni successive (tramite il programma [Insider](https://docs.microsoft.com//windows-insider/at-home/get-started) ) è possibile accedere a una nuova interfaccia per la condivisione della mappa. Questa nuova funzionalità è disponibile tramite l'interfaccia di gestione mappe del portale del dispositivo Windows. Per usare questo strumento, attenersi alla procedura seguente:
- Assicurarsi di aver scelto 20H1 o versione successiva (a partire dal 2019 di settembre questo significa usare il programma Insider)
- Abilitare il portale del dispositivo Windows (WDP). le istruzioni sono disponibili [qui](https://docs.microsoft.com//windows/uwp/debug-test-perf/device-portal-desktop)
- Inserire un HMD di realtà mista di Windows da cui si vuole scaricare una mappa esistente o importare una nuova mappa
- Passare a WDP nel browser scelto usando l'URL fornito nella schermata Impostazioni. 
  - Passare alla sezione "realtà mista" e selezionare "gestore mappe". 
  - È ora possibile usare il pulsante "download" per esportare una mappa esistente dal computer. 
  - È possibile usare il pulsante "carica un file di mappa" per importare una mappa da un'esportazione precedente (ad esempio in un computer diverso). 
  - È possibile usare "Import" per consentire al sistema di usare tale mappa per questo HMD nel computer.
  
### <a name="tracking"></a>TRACKING

D: come funziona la tecnologia di rilevamento negli auricolari per la realtà mista di Windows?  

La realtà mista condivide la stessa tecnologia di rilevamento del HoloLens. Per ulteriori informazioni sul sistema di rilevamento esterno, consultare la documentazione [qui](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/tracking-system).

Per una descrizione di come funziona il sistema di mapping spaziale di livello superiore, è possibile leggere [qui](spatial-mapping.md)la descrizione.

**D: sono disponibili procedure consigliate per ottenere un volume di rilevamento affidabile?**

Per configurare meglio l'ambiente per la verifica dell'esito positivo, è possibile leggere le procedure consigliate in questo [post](environment-considerations-for-hololens.md).

**D: esistono sfumature specifiche con il rilevamento in spazi di scalabilità o ottimizzazioni da prendere in considerazione?**

R: le procedure seguenti consentono di ottenere un volume di rilevamento più affidabile:  

Fornire un'ampia gamma di funzionalità nella stanza che si sovrappongono a più posizioni consente al sistema di rilevamento di ottenere un blocco a tinta unita. Si pensi a schizzi e tratteggio di colori casuali invece di usare linee di stile di contorno solide. 

Quando possibile, ridurre al minimo l'intervallo dinamico di illuminazione nella propria area. Le fotocamere di rilevamento sulla nostra realtà mista HMDs non sono HDR e sono in corso di AGC (guadagno automatico) e AEC (esposizione automatica) per gestire l'illuminazione in modo diverso. A seconda della distribuzione della luce superficiale, dei modelli e del contrasto, AGC o AEC può concludere che ci si trova in una grande quantità di spazio bianco o nero, che può essere in grado di pulire le funzionalità che potrebbero trovarsi sul "colore" opposto. Se si sta provando a scattare un'immagine interna davanti a una finestra esterna con una luce luminosa e si regola l'esposizione in modo da visualizzare i dettagli al di fuori, tutto ciò che si trova all'interno è sottoesposto e nero. In alternativa, se impostato per interno, tutti gli elementi al di fuori di sono ora sovraesposti e tutti i bianchi.  

I riflettori in una stanza (anche sovraccarico) che sono in vista se le fotocamere di rilevamento possono talvolta essere colpevoli che confondeno l'AEC/AGC delle fotocamere di rilevamento. Illuminazione piatta/diffusa aiuta.  

### <a name="mixed-reality-cloud-services-and-azure"></a>SERVIZI CLOUD DI REALTÀ MISTA E AZURE 

**D: come può Microsoft Azure aiutare la scalabilità aziendale?**

R: la gestione basata su sito e remota di Azure può aiutare la tua azienda a guidare i dati, a ridurre i costi operativi e a ridimensionare la distribuzione in posizioni nuove e esistenti. I servizi cloud di Azure, ad esempio archiviazione di Azure, funzioni di Azure, servizio app, rete di Azure e hub Internet, possono essere utili per i casi d'uso seguenti:  

Gestione & di distribuzione di dispositivi remoti 

Analisi in tempo reale in sede 

Gameplay intelligente LBE adattabile 

Distribuzione e streaming di contenuti LBE 

Preferenza Lettore LBE mappa termica 

Sistema di prenotazione e prenotazione di LBE 

**D: sto sviluppando un MMOG spaziale per la distribuzione su un footprint massiccio. Tutti i servizi che consentono di gestire il contenuto e la persistenza degli oggetti?**

R: gli ancoraggi spaziali di Azure sono un nuovo servizio di realtà mista che consente esperienze di realtà miste che consentono a più utenti e a livello spaziale tra dispositivi HoloLens, iOS e Android. Altre informazioni sugli ancoraggi spaziali di Azure sono disponibili [qui](https://azure.microsoft.com//services/spatial-anchors/).

**D. la nostra sede si specializza in esperienze multiplayer e desidero concentrare il nostro tempo di sviluppo sul contenuto e sullo sviluppo front-end. Sono disponibili offerte che consentono di eseguire il bootstrap o l'offload dello sviluppo back-end?**

R: Azure PlayFab è una piattaforma di back-end completa per giochi Live. Per altre informazioni, vedere [qui](https://playfab.com/).

### <a name="misc"></a>Vari

**D: utilizzo SteamVR per distribuire le mie esperienze. La realtà mista di Windows funziona con SteamVR?**

R: la realtà mista di Windows per SteamVR consente agli utenti di eseguire esperienze SteamVR su cuffie immersive a realtà mista di Windows. Altre informazioni su SteamVR con WMR sono disponibili [qui](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality).

### <a name="support-and-community"></a>Supporto e community  

Di seguito sono riportate alcune risorse utili per coinvolgere esperti del team, ottenere supporto per la risoluzione dei problemi e contribuire alla più ampia community di sviluppatori di realtà mista.  

Se si verificano problemi con le funzionalità rilasciate pubblicamente, inviare un bug usando l'hub feedback. per informazioni aggiuntive, vedere questa [pagina](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/filing-feedback).

Per ulteriori informazioni sulla risoluzione dei problemi relativi a WMR, contattare il team di supporto clienti presentando una [richiesta di supporto](https://support.microsoft.com//supportforbusiness/productselection?sapId=96bfb202-bc79-741b-bf7a-774d8b767782).

Unisciti al canale Slack di HoloDevelopers per coinvolgere gli sviluppatori che lavorano su realtà mista e esperti del team: [aka.ms/holodevelopers](https://aka.ms/holodevelopers)

Twitter: Segui il nostro team di relazioni per sviluppatori di realtà mista per notizie, eventi e aggiornamenti @MxdRealityDev 

Se ci si trova in o intorno a San Francisco, c'è sempre qualcosa che sta succedendo nel reattore Microsoft. [Qui](https://developer.microsoft.com//reactor/Location/San%20Francisco)è possibile visualizzare il calendario degli eventi.

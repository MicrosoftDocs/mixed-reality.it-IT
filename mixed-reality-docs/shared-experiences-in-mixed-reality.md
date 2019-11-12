---
title: Esperienze condivise in realtà mista
description: Le app olografiche possono condividere ancoraggi spaziali da un HoloLens all'altro, consentendo agli utenti di eseguire il rendering di un ologramma nella stessa posizione del mondo reale, tra più dispositivi.
author: thetuvix
ms.author: grbury
ms.date: 02/10/2019
ms.topic: article
keywords: esperienza condivisa, realtà mista, ologramma, ancoraggio spaziale, multiutente, più
ms.openlocfilehash: c846bcd8c9c52f1f169d306df3afd4f982656078
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926926"
---
# <a name="shared-experiences-in-mixed-reality"></a>Esperienze condivise in realtà mista

Gli ologrammi non devono rimanere privati per un solo utente. Le app olografiche possono condividere [ancoraggi spaziali](spatial-anchors.md) da un dispositivo HoloLens, iOS o Android a un altro, consentendo agli utenti di eseguire il rendering di un ologramma nella stessa posizione del mondo reale su più dispositivi.

## <a name="six-questions-to-define-shared-scenarios"></a>Sei domande per definire scenari condivisi

Prima di iniziare la progettazione per esperienze condivise, è importante definire gli scenari di destinazione. Questi scenari consentono di chiarire ciò che si sta progettando e di definire un vocabolario comune per aiutare a confrontare e contrapporre le funzionalità necessarie per la propria esperienza. Comprendere il problema principale e le diverse vie per le soluzioni è fondamentale per individuare le opportunità inerenti a questo nuovo supporto.

Grazie a prototipi ed esplorazioni interni delle nostre agenzie partner HoloLens, abbiamo creato sei domande che ti aiuteranno a definire scenari condivisi. Queste domande costituiscono un Framework, non destinato a essere esaustivo, per facilitare la distillazione degli attributi importanti degli scenari.

### <a name="1-how-are-they-sharing"></a>1. come si condividono?

Una presentazione potrebbe essere condotta da un singolo utente virtuale, mentre più utenti possono collaborare oppure un insegnante può fornire materiale sussidiario per gli studenti virtuali che utilizzano materiali virtuali. la complessità delle esperienze aumenta in base al livello di agenzia di un utente o può avere in uno scenario.

![Uomo e donne con olografo sulla tabella](images/man-and-women-with-holograph-on-table-500px.png)

Ci sono molti modi per condividere, ma abbiamo scoperto che la maggior parte di essi rientrano in tre categorie:

* **Presentazione**: quando viene visualizzato lo stesso contenuto per più utenti. Ad esempio, un professore sta offrendo una lezione a diversi studenti che usano lo stesso materiale olografico presentato a tutti. Il professore, tuttavia, potrebbe avere suggerimenti e note che potrebbero non essere visibili ad altri utenti.
* **Collaborazione**: quando le persone lavorano insieme per raggiungere alcuni obiettivi comuni. Ad esempio, il professore ha fornito un progetto per ottenere informazioni sull'esecuzione di un intervento chirurgico al cuore. Gli studenti si abbinano e creano un'esperienza di Lab per competenze condivise che consente agli studenti di medicina di collaborare al modello di cuore e apprendere.
* **Linee guida**: quando una persona sta aiutando qualcuno a risolvere un problema in un'interazione di stile uno-a-uno. Ad esempio, il professore che fornisce indicazioni a uno studente durante l'esecuzione del Lab delle competenze di Heart Surgery nell'esperienza condivisa.

### <a name="2-what-is-the-group-size"></a>2. quali sono le dimensioni del gruppo?

Le esperienze di condivisione **uno-a-uno** possono fornire una linea di base avanzata e idealmente è possibile creare prove del concetto a questo livello. Tuttavia, tenere presente che la condivisione con gruppi di grandi dimensioni (oltre 6 persone) può causare problemi sia tecnici (dati che di rete) che Social (l'effetto di una stanza con [diversi avatar](https://vimeo.com/160704056)). La complessità aumenta in modo esponenziale Man mano che si passa da gruppi **piccoli** a **grandi**.

È stato rilevato che le esigenze dei gruppi possono rientrare in tre categorie di dimensioni:
* 1:1
* Small < 7
* > Grande = 7

Le dimensioni del gruppo fanno una domanda importante perché influenza:

* Rappresentazioni di persone nello spazio olografico
* Ridimensionamento di oggetti
* Scalabilità dell'ambiente

### <a name="3-where-is-everyone"></a>3. dove si trova tutti?

La forza della realtà mista entra in gioco quando un'esperienza condivisa può essere eseguita nella stessa posizione. Chiamiamo il percorso **condiviso**. Viceversa, quando il gruppo viene distribuito e almeno un partecipante non si trova nello stesso spazio fisico (come spesso accade con VR), chiamiamo un' **esperienza remota**. Spesso, si tratta di un caso in cui il **gruppo dispone di** un percorso condiviso e di un partecipante remoto, ad esempio due gruppi nelle sale riunioni.

![Tre persone con olografo sulla tabella](images/three-people-with-holograph-on-table-500px.png)

Le categorie seguenti consentono di indicare la posizione in cui si trovano gli utenti:

* Percorso **condiviso**: tutti gli utenti si troveranno nello stesso spazio fisico.
* **Remote**: tutti gli utenti saranno in spazi fisici distinti.
* **Entrambi**: gli utenti saranno una combinazione di spazi con percorso condiviso e remoto.

Questa domanda è fondamentale perché influenza:

* Modalità di comunicazione delle persone
    * Ad esempio, se dovrebbero avere avatar?
* Quali oggetti vengono visualizzati. Tutti gli oggetti sono condivisi?
* Se è necessario adattarsi al proprio ambiente,

### <a name="4-when-are-they-sharing"></a>4. quando si condividono?

In genere si pensa a esperienze **sincrone** quando si verificano esperienze condivise: lo stiamo facendo tutti insieme. Tuttavia, se si include un singolo elemento virtuale aggiunto da un altro utente, si avrà uno scenario **asincrono** . Immaginate una nota o un memo vocale, a sinistra in un ambiente virtuale. In che modo è possibile gestire i memo virtuali 100 lasciati dalla progettazione? Che cosa accade se si tratta di dozzine di persone con diversi livelli di privacy?

Considera le tue esperienze come una delle seguenti categorie di tempo:

* In modo **sincrono**: condivisione dell'esperienza olografica nello stesso momento. Ad esempio, due studenti che eseguono il Lab delle competenze nello stesso momento.
* In **modo asincrono**: condivisione dell'esperienza olografica in momenti diversi. Ad esempio, due studenti che eseguono il Lab delle competenze, ma che lavorano su sezioni separate in momenti diversi.
* **Entrambi**: gli utenti potranno a volte condividere in modo sincrono, ma in altre occasioni in modo asincrono. Ad esempio, un professore che valuta l'assegnazione eseguita dagli studenti in un secondo momento e lascia note per gli studenti per il giorno successivo.

Questa domanda è importante perché influenza:

* Persistenza dell'ambiente e dell'oggetto. Ad esempio: archiviazione degli Stati in modo che possano essere recuperati.
* Prospettiva utente. Ad esempio, è probabile che si ricordino gli elementi osservati dall'utente quando si lasciano note.

### <a name="5-how-similar-are-their-physical-environments"></a>5. quanto sono simili gli ambienti fisici?

La probabilità di due ambienti reali identici, al di fuori delle esperienze con risorse condivise, è snella, a meno che tali ambienti non siano stati progettati per essere identici. È più probabile che si disponga di ambienti **simili** . Ad esempio, le sale riunioni sono simili, in genere hanno una tabella con sede centrale racchiusa tra sedie. I salotti, d'altra parte, sono in genere **dissimili** e possono includere un numero qualsiasi di elementi mobili in una matrice infinita di layout.

![Olografo nella tabella](images/holograph-on-table-500px.png)

Prendere in considerazione le esperienze di condivisione che si adattano a una delle due categorie seguenti:

* **Simile**: ambienti che tendono a avere arredi simili, luce ambientale e suoni, dimensioni della stanza fisica. Ad esempio, il professore si trova in una conferenza A e gli studenti si trovano nell'aula B. la conferenza A può avere un minor numero di poltrone rispetto a B, ma entrambi possono avere una scrivania fisica in cui posizionare gli ologrammi.
* **Dissimili**: ambienti molto diversi nelle impostazioni della mobilia, dimensioni delle stanze, considerazioni chiare e valide. Ad esempio, un professore si trova in uno stato attivo, mentre gli studenti si trovano in una sala conferenze di grandi dimensioni, pieni di studenti e docenti.

È importante [considerare l'ambiente](environment-considerations-for-hololens.md), in quanto influenzerà:

* Il modo in cui gli utenti sperimenteranno questi oggetti. Ad esempio, se l'esperienza è ottimale per una tabella e l'utente non dispone di una tabella, O su una superficie piatta, ma l'utente ha uno spazio ingombrante.
* Scala degli oggetti. Ad esempio, l'inserimento di un modello umano a 6 piedi in una tabella potrebbe risultare complesso, ma un modello di cuore sarebbe perfetto.

### <a name="6-what-devices-are-they-using"></a>6. quali dispositivi usano?

Oggi spesso è probabile che si verifichino esperienze condivise tra due [**dispositivi immersivi**](immersive-headset-hardware-details.md) (questi dispositivi potrebbero differire leggermente in termini di pulsanti e funzionalità relative, ma non molto) o di due **dispositivi olografici** in base alle soluzioni di destinazione a questi dispositivi. Considerare tuttavia se i **dispositivi 2D** (un partecipante mobile/desktop o un Observer) saranno considerati necessari, soprattutto in situazioni di **dispositivi 2D e 3D misti**. Conoscere i tipi di dispositivi che verranno usati dai partecipanti è importante, non solo perché sono dotati di diversi vincoli di fedeltà e dati e opportunità, ma poiché gli utenti hanno aspettative univoche per ogni piattaforma.

## <a name="exploring-the-potential-of-shared-experiences"></a>Esplorare le potenzialità delle esperienze condivise

Le risposte alle domande precedenti possono essere combinate per comprendere meglio lo scenario condiviso, cristallizzando le problematiche durante l'espansione dell'esperienza. Per il team di Microsoft, questo ha aiutato a definire una mappa stradale per migliorare le esperienze di uso odierno, comprendere la sfumatura di questi problemi complessi e come sfruttare i vantaggi delle esperienze condivise in realtà mista.

Si consideri, ad esempio, uno degli scenari di Skype dal lancio HoloLens: un utente ha lavorato per [risolvere un cambio di luce rotto](https://www.youtube.com/watch?v=iBfzs3G8BEA) con supporto da un esperto situato in remoto.

![Correzione di uno switch leggero con assistenza tramite Skype per HoloLens](images/fix-a-broken-switch-with-hololens-640px.jpg)

*Un esperto fornisce istruzioni **1:1** dal computer desktop **2D**a un utente di un dispositivo **3D a realtà mista** . Le **linee guida** sono **sincrone** e gli ambienti fisici sono **diversi.***

Un'esperienza di questo tipo è un passaggio dalla nostra esperienza attuale, ovvero l'applicazione del paradigma di video e Voice a un nuovo supporto. Tuttavia, quando osserviamo il futuro, dobbiamo definire meglio l'opportunità degli scenari e le esperienze di compilazione che riflettono la forza della realtà mista.

Si consideri lo [strumento di collaborazione onvisione](https://www.youtube.com/watch?v=XtUyUJAVQ6w), sviluppato dal laboratorio di propulsione jet della NASA. Gli scienziati che lavorano sui dati delle missioni Mars Rover possono collaborare con i colleghi in tempo reale all'interno dei dati del paesaggio marziano.

![Collaborazione tra i colleghi separati in remoto per pianificare il lavoro per Mars Rover](images/onsight-nasa-jpl.gif)

*Uno scienziato Esplora un ambiente usando un dispositivo **3D e in realtà mista** con un **piccolo** gruppo di colleghi **remoti** che usano dispositivi **3D e 2D** . La **collaborazione** è **sincrona** (ma può essere rivisitata in modo asincrono) e gli ambienti fisici sono (praticamente) **simili**.*

Esperienze come onvisione presentano nuove opportunità di collaborazione. Dall'indirizzamento fisico degli elementi nell'ambiente virtuale a un collega e alla condivisione della loro prospettiva come spiegano i risultati. Oninsight usa l'obiettivo dell'immersione e della presenza per ripensare le esperienze di condivisione in realtà mista.

Una collaborazione intuitiva è il fondamento della conversazione, l'interazione e la comprensione del modo in cui possiamo applicare questa intuizione alla complessità della realtà mista è fondamentale. Se non solo è possibile ricreare le esperienze di condivisione in realtà mista, ma è necessario supercaricarle, sarà un cambio di paradigma per il futuro del lavoro. La progettazione di esperienze condivise in realtà mista è uno spazio nuovo e interessante, che è solo all'inizio.

## <a name="get-started-building-shared-experiences"></a>Inizia subito a creare esperienze condivise

A seconda dell'applicazione e dello scenario, per ottenere l'esperienza desiderata saranno necessari vari requisiti. Di seguito sono riportate alcune delle seguenti:

* **Corrispondenza**: possibilità di creare sessioni, annunciare sessioni, individuare e invitare persone specifiche, sia in locale che in remoto per partecipare alla sessione.
* **Condivisione di ancoraggio**: possibilità di allineare le coordinate tra più dispositivi in uno spazio locale comune, in modo che gli ologrammi vengano visualizzati nella stessa posizione per tutti gli utenti.
* **Rete**: possibilità di avere posizioni, interazioni e movimenti di persone e ologrammi sincronizzati in tempo reale in tutti i partecipanti.
* **Archiviazione dello stato**: possibilità di archiviare caratteristiche e posizioni degli ologrammi nello spazio per l'aggiunta a metà sessione, il richiamo in un secondo momento e l'affidabilità in caso di problemi di rete.

La chiave per le esperienze condivise consiste nel fatto che più utenti vedono gli stessi ologrammi nel mondo sul proprio dispositivo, spesso grazie alla condivisione di ancoraggi per allineare le coordinate tra dispositivi.

Per condividere gli ancoraggi, usare gli [ancoraggi spaziali di Azure](https://docs.microsoft.com/azure/spatial-anchors):

* Prima di tutto l'ologramma viene posizionato dall'utente.
* L'app crea un [ancoraggio spaziale](spatial-anchors.md), per aggiungere tale ologramma esattamente nel mondo.
* Gli ancoraggi possono essere condivisi in dispositivi HoloLens, iOS e Android tramite [ancoraggi spaziali di Azure](https://docs.microsoft.com/azure/spatial-anchors/).

Con un ancoraggio spaziale condiviso, l'app in ogni dispositivo dispone ora di un [sistema di coordinate comune](coordinate-systems.md) in cui è possibile collocare il contenuto. A questo punto l'app può garantire la posizione e l'orientamento dell'ologramma nella stessa posizione.

Nei dispositivi HoloLens è anche possibile condividere gli ancoraggi offline da un dispositivo a un altro.  Usare i collegamenti seguenti per decidere quale sia la soluzione migliore per l'applicazione.

## <a name="evaluating-tech-options"></a>Valutazione delle opzioni tecniche

Sono disponibili diverse opzioni per il servizio e la tecnologia che consentono di creare esperienze di realtà mista multiutente.  Può essere difficile scegliere un percorso, in modo da adottare una prospettiva incentrata sullo scenario. di seguito sono elencate alcune opzioni.

## <a name="shared-static-holograms-no-interactions"></a>Ologrammi statici condivisi (nessuna interazione)

Sfruttare gli [ancoraggi spaziali di Azure](https://docs.microsoft.com/azure/spatial-anchors/) nell'app.  L'abilitazione e la condivisione di ancoraggi spaziali tra i dispositivi consentono di creare un'applicazione in cui gli utenti visualizzano gli ologrammi nello stesso punto nello stesso momento.  È necessaria una sincronizzazione aggiuntiva tra dispositivi per consentire agli utenti di interagire con gli ologrammi e visualizzare i movimenti o gli aggiornamenti di stato degli ologrammi.

## <a name="share-1st-person-perspective"></a>Condividi la prospettiva del primo utente

Usare il supporto Miracast incorporato, per gli utenti locali quando si dispone di un ricevitore Miracast supportato, ad esempio un PC o una TV, non è necessario alcun codice dell'app aggiuntivo.

Usare [MixedReality-WebRTC](https://github.com/microsoft/mixedreality-webrtc) nell'app, per gli utenti remoti o quando si dispone di dispositivi non Miracast che si vuole condividere.  L'abilitazione di una connessione WebRTC consente di 1:1 flussi audio/video tra gli utenti, con un canale dati per la messaggistica tra dispositivi.  L'implementazione della realtà mista ottimizza per HoloLens, fornendo un flusso video di acquisizione della realtà mista della visualizzazione dell'utente HoloLens ad altri.  Se si desidera aumentare la scalabilità verticale dei flussi video a più client remoti, viene in genere usato un [provider di servizi MCU](https://webrtcglossary.com/mcu/) (multipoint Conference Unit), ad esempio [SignalWire](https://signalwire.com/).  Una distribuzione SignalWire con un clic in Azure è disponibile tramite [FreeSwitch](https://github.com/andywolk/azure-freeswitch-gpu-windows).

> [!NOTE]
> Si noti che SignalWire è un servizio a pagamento e non è di proprietà/affiliato a Microsoft.

## <a name="presenter-spectator-applications-and-demos"></a>Presenter-applicazioni e demo Spectator

Usare [MixedReality-SpectatorView](https://github.com/microsoft/MixedReality-SpectatorView) per rendere le [funzionalità di visualizzazione degli spettatori](spectator-view.md) nell'app.  Abilitare altri dispositivi (HL, Android, iOS e videocamere) per vedere cosa vede HoloLens da una prospettiva diversa nello stesso percorso e ricevere aggiornamenti sulle interazioni dell'utente HoloLens dell'host che interagisce con gli ologrammi.  Guardare, scattare foto e registrare video sulle operazioni svolte dall'host con gli ologrammi nell'applicazione dal punto di vista spaziale con il compagno spettatore della stessa app.

**Nota:** Le immagini vengono acquisite tramite screenshot sui dispositivi iOS/Android.

## <a name="multi-user-collaborative-experience"></a>Esperienza di collaborazione multiutente

Inizia con l' [esercitazione per l'apprendimento multiutente](mrlearning-sharing(photon)-ch1.md), che sfrutta gli [ancoraggi spaziali di Azure](https://docs.microsoft.com/azure/spatial-anchors/) per gli utenti locali e [Photon SDK](https://www.photonengine.com/PUN) per sincronizzare il contenuto o lo stato nella scena. Crea applicazioni di collaborazione localmente in cui ogni utente ha una propria prospettiva sugli ologrammi nella scena e può interagire completamente con gli ologrammi.  Gli aggiornamenti vengono forniti in tutti i dispositivi e la gestione dei conflitti di interazione viene gestita da Photon.

> [!NOTE]
> Si noti che [Photon](https://www.photonengine.com/) è un prodotto non Microsoft, quindi è possibile che sia necessaria una relazione di fatturazione con Photon per commercializzare e la scalabilità per un utilizzo superiore.

## <a name="future-work"></a>Lavoro futuro

Le funzionalità e le interfacce dei componenti consentono di fornire coerenza comune e un supporto affidabile tra i vari scenari e le tecnologie sottostanti.  Fino ad allora, scegliere il percorso migliore che si allinea allo scenario che si sta tentando di ottenere nell'applicazione.

Uno scenario diverso o il desiderio di usare una tecnologia o un servizio diverso? Inviare commenti e suggerimenti come problemi di GitHub nel repository corrispondente, nella parte inferiore di questa pagina, oppure contattare [HoloDevelopers Slack](https://holodevelopers.slack.com/).

## <a name="see-also"></a>Vedi anche

* [Ancoraggi nello spazio di Azure](https://docs.microsoft.com/azure/spatial-anchors)
* [Ancoraggi nello spazio condivisi in DirectX](shared-spatial-anchors-in-directx.md)
* [Esperienze condivise in Unity](shared-experiences-in-unity.md)
* [Visualizzazione spettatore](spectator-view.md)

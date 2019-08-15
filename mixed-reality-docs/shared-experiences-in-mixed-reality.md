---
title: Esperienze condivise in realtà mista
description: Le app olografiche possono condividere ancoraggi spaziali da un HoloLens all'altro, consentendo agli utenti di eseguire il rendering di un ologramma nella stessa posizione del mondo reale su più dispositivi.
author: thetuvix
ms.author: grbury
ms.date: 02/10/2019
ms.topic: article
keywords: esperienza condivisa, realtà mista, ologramma, ancoraggio spaziale, multiutente, più
ms.openlocfilehash: fbc636a5d65e605ae9e9f9655eb15550ff8de7b7
ms.sourcegitcommit: e5b677f92ac4b1dff9aad6c329345a5aca4fcef5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/14/2019
ms.locfileid: "69020200"
---
# <a name="shared-experiences-in-mixed-reality"></a>Esperienze condivise in realtà mista

Gli ologrammi non devono rimanere privati per un solo utente. Le app olografiche possono condividere [ancoraggi spaziali](coordinate-systems.md) da un dispositivo HoloLens, iOS o Android a un altro, consentendo agli utenti di eseguire il rendering di un ologramma nella stessa posizione del mondo reale su più dispositivi.

## <a name="six-questions-to-define-shared-scenarios"></a>Sei domande per definire scenari condivisi

Prima di iniziare la progettazione per esperienze condivise, è importante definire gli scenari di destinazione. Questi scenari consentono di chiarire ciò che si sta progettando e di definire un vocabolario comune per aiutare a confrontare e contrapporre le funzionalità necessarie per la propria esperienza. Comprendere il problema principale e le diverse vie per le soluzioni è fondamentale per individuare le opportunità inerenti a questo nuovo supporto.

Grazie a prototipi ed esplorazioni interni delle nostre agenzie partner HoloLens, abbiamo creato sei domande che ti aiuteranno a definire scenari condivisi. Queste domande costituiscono un Framework, non destinato a essere esaustivo, per facilitare la distillazione degli attributi importanti degli scenari.

### <a name="1-how-are-they-sharing"></a>1. In che modo condividono?

Una presentazione potrebbe essere condotta da un singolo utente virtuale, mentre più utenti possono collaborare oppure un insegnante può fornire materiale sussidiario per gli studenti virtuali che utilizzano materiali virtuali. la complessità delle esperienze aumenta in base al livello di agenzia di un utente o può avere in uno scenario.

![Uomo e donne con olografo sulla tabella](images/man-and-women-with-holograph-on-table-500px.png)

Ci sono molti modi per condividere, ma abbiamo scoperto che la maggior parte di essi rientrano in tre categorie:
* **Presentazione**: Quando viene visualizzato lo stesso contenuto per più utenti. Ad esempio:  Un professore sta offrendo una lezione a diversi studenti che usano lo stesso materiale olografico presentato a tutti. Il professore potrebbe tuttavia avere suggerimenti e note che potrebbero non essere visibili ad altri utenti.
* **Collaborazione**: Quando le persone lavorano insieme per raggiungere alcuni obiettivi comuni. Ad esempio:  Il professore ha fornito un progetto per ottenere informazioni sull'esecuzione di un intervento chirurgico al cuore. Gli studenti si abbinano e creano un'esperienza di Lab per competenze condivise che consente agli studenti di medicina di collaborare al modello di cuore e apprendere.
* **Linee guida**: Quando una persona sta aiutando qualcuno a risolvere un problema in un'interazione di stile uno-a-uno. Ad esempio:  Il professore fornisce indicazioni a uno studente quando si sta eseguendo il Lab delle competenze di Heart Surgery nell'esperienza condivisa.

### <a name="2-what-is-the-group-size"></a>2. Quali sono le dimensioni del gruppo?

Le esperienze di condivisione **uno-a-uno** possono fornire una linea di base avanzata e idealmente è possibile creare prove del concetto a questo livello. Tuttavia, tenere presente che la condivisione con gruppi di grandi dimensioni (oltre 6 persone) può causare difficoltà da tecniche (dati e rete) a social (l'effetto di una stanza con [diversi avatar](https://vimeo.com/160704056)). La complessità aumenta in modo esponenziale Man mano che si passa da gruppi **piccoli** a **grandi**.

È stato rilevato che le esigenze dei gruppi possono rientrare in tre categorie di dimensioni:
* 1:1
* Small < 7
* > Grande = 7

Le dimensioni del gruppo fanno una domanda importante perché influenza:
* Rappresentazioni di persone nello spazio olografico
* Ridimensionamento di oggetti
* Scalabilità dell'ambiente

### <a name="3-where-is-everyone"></a>3. Dove si trova tutti?

La forza della realtà mista entra in gioco quando un'esperienza condivisa può essere eseguita nella stessa posizione. Chiamiamo il percorso **condiviso**. Viceversa, quando il gruppo viene distribuito e almeno un partecipante non si trova nello stesso spazio fisico (come spesso accade con VR), chiamiamo un'esperienza remota. Spesso è il caso in cui il gruppo disponga di un percorso condiviso e di un partecipante remoto (ad esempio, due gruppi in sale riunioni).

![Tre persone con olografo sulla tabella](images/three-people-with-holograph-on-table-500px.png)

Le categorie seguenti consentono di indicare la posizione in cui si trovano gli utenti:
* Con percorso condiviso: Tutti gli utenti si troveranno nello stesso spazio fisico.
* Remoto Tutti gli utenti si troveranno in spazi fisici distinti.
* Sia Gli utenti saranno una combinazione di spazi con percorso condiviso e remoto.

Ecco alcuni motivi per cui questa domanda è cruciale perché influenza:
* Modalità di comunicazione delle persone
* Ad esempio:  Se dovrebbero avere avatar?
* Quali oggetti vengono visualizzati. Tutti gli oggetti sono condivisi?
* Se è necessario adattarsi al proprio ambiente,

### <a name="4-when-are-they-sharing"></a>4. Quando si condividono?

In genere si pensa a esperienze sincrone quando si verificano esperienze condivise: Lo facciamo tutti insieme. Includere, tuttavia, un singolo elemento virtuale aggiunto da un altro utente ed è presente uno scenario **asincrono** . Immaginate una nota o un memo vocale, a sinistra in un ambiente virtuale. In che modo è possibile gestire i memo virtuali 100 lasciati dalla progettazione? Che cosa accade se si tratta di dozzine di persone con diversi livelli di privacy?

Considera le tue esperienze come una delle seguenti categorie di tempo:
* In modo sincrono: Condivisione dell'esperienza olografica nello stesso momento. Ad esempio:  Due studenti che eseguono il Lab delle competenze nello stesso momento.
* In **modo asincrono**: Condivisione dell'esperienza olografica in momenti diversi. Ad esempio:  Due studenti che eseguono il Lab delle competenze, ma lavorano su sezioni separate in momenti diversi.
* **Entrambi**: A volte gli utenti si condividano in modo sincrono, ma in altre occasioni in modo asincrono. Ad esempio:  Professore che valuta l'assegnazione eseguita dagli studenti in un secondo momento e lascia le note per studenti per il giorno successivo.

Ecco alcuni motivi per cui questa domanda è importante perché influenza:
* Persistenza dell'ambiente e dell'oggetto. Ad esempio:  Archiviazione degli Stati in modo che possano essere recuperati.
* Prospettiva utente. Ad esempio:  È probabile che si ricordino gli elementi osservati dall'utente quando si lasciano note.

### <a name="5-how-similar-are-their-physical-environments"></a>5. Quanto sono simili gli ambienti fisici?

La probabilità di due ambienti reali identici, al di fuori delle esperienze con risorse condivise, è snella, a meno che tali ambienti non siano stati progettati per essere identici. È più probabile che si disponga di ambienti **simili** . Ad esempio, le sale riunioni sono simili, in genere hanno una tabella posizionata a livello centrale racchiusa tra sedie. I salotti, d'altra parte, sono in genere **dissimili** e possono includere un numero qualsiasi di elementi mobili in una matrice infinita di layout.

![Olografo nella tabella](images/holograph-on-table-500px.png)

Prendere in considerazione le esperienze di condivisione che si adattano a una delle due categorie seguenti:
* **Simile**: Ambienti che tendono a avere arredi simili, luce ambientale e suoni, dimensioni della stanza fisica. Ad esempio:  Il professore si trova in una conferenza a e gli studenti si trovano nella conferenza B. la conferenza A può avere un minor numero di poltrone rispetto a B, ma entrambi possono avere una scrivania fisica in cui collocare gli ologrammi.
* **Dissimili**: Ambienti molto diversi nelle impostazioni della mobilia, dimensioni delle stanze, considerazioni chiare e valide. Ad esempio:  Il professore si trova in una sala concentrata, mentre gli studenti si trovano in una grande sala conferenze ricca di studenti e docenti.

È importante considerare l'ambiente in quanto influenzerà:
* In che modo gli utenti sperimenteranno questi oggetti. Ad esempio:  Se l'esperienza è ottimale per una tabella e l'utente non dispone di una tabella, O su una superficie piatta, ma l'utente ha uno spazio ingombrante.
* Scala degli oggetti. Ad esempio:  L'inserimento di un modello umano a 6 metri su una tabella potrebbe risultare complesso, ma un modello di cuore sarebbe perfetto.

### <a name="6-what-devices-are-they-using"></a>6. Quali dispositivi usano?

Oggi spesso è probabile che si verifichino esperienze condivise tra due **dispositivi immersivi** (questi dispositivi potrebbero differire leggermente in termini di pulsanti e funzionalità relative, ma non molto) o di due **dispositivi olografici** in base alle soluzioni di destinazione a questi dispositivi. Tenere tuttavia presente che i **dispositivi 2D** (un partecipante mobile/desktop o un Observer) saranno una considerazione necessaria, soprattutto in situazioni di **dispositivi 2D e 3D misti**. Conoscere i tipi di dispositivi che verranno usati dai partecipanti è importante, non solo perché sono dotati di diversi vincoli di fedeltà e dati e opportunità, ma poiché gli utenti hanno aspettative univoche per ogni piattaforma.

## <a name="exploring-the-potential-of-shared-experiences"></a>Esplorare le potenzialità delle esperienze condivise

Le risposte alle domande precedenti possono essere combinate per comprendere meglio lo scenario condiviso, cristallizzando le problematiche durante l'espansione dell'esperienza. Per il team di Microsoft, questo ha aiutato a definire una mappa stradale per migliorare le esperienze di uso odierno, comprendere la sfumatura di questi problemi complessi e come sfruttare i vantaggi delle esperienze condivise in realtà mista.

Si consideri, ad esempio, uno degli scenari di Skype dal lancio HoloLens: un utente ha lavorato per [risolvere un cambio di luce rotto](https://www.youtube.com/watch?v=iBfzs3G8BEA) con supporto da un esperto situato in remoto.

![Correzione di uno switch leggero con assistenza tramite Skype per HoloLens](images/fix-a-broken-switch-with-hololens-640px.jpg)

<i>Un esperto fornisce istruzioni <b>1:1</b> dal computer desktop <b>2D</b>a un utente di un dispositivo <b>3D a realtà mista</b> . Le <b>linee guida</b> sono <b>sincrone</b> e gli ambienti <b></b>fisici sono diversi.</i>

Un'esperienza di questo tipo è un passaggio dalla nostra esperienza attuale, ovvero l'applicazione del paradigma di video e Voice a un nuovo supporto. Tuttavia, quando osserviamo il futuro, dobbiamo definire meglio l'opportunità degli scenari e le esperienze di compilazione che riflettono la forza della realtà mista.

Si consideri lo [strumento di collaborazione](https://www.youtube.com/watch?v=ZOWQp0-Bkkw) di oninsight sviluppato dal laboratorio di propulsione jet di NASA. Gli scienziati che lavorano sui dati delle missioni Mars Rover possono collaborare con i colleghi in tempo reale all'interno dei dati del paesaggio marziano.

![Collaborazione tra i colleghi separati in remoto per pianificare il lavoro per Mars Rover](images/onsight-nasa-jpl.gif)

<i>Uno scienziato Esplora un ambiente usando un dispositivo <b>3D</b> e in realtà mista con un <b>piccolo</b> gruppo di <b></b> colleghi remoti <b>che usano dispositivi 3D e 2D</b> . La <b>collaborazione</b> è <b>sincrona</b> (ma può essere rivisitata in modo asincrono) e gli ambienti fisici sono (praticamente) <b>simili</b>.</i>

Esperienze come onvisione presentano nuove opportunità di collaborazione. Dall'indirizzamento fisico degli elementi nell'ambiente virtuale a un collega e alla condivisione della loro prospettiva come spiegano i risultati. Oninsight usa l'obiettivo dell'immersione e della presenza per ripensare le esperienze di condivisione in realtà mista.

Una collaborazione intuitiva è il fondamento della conversazione e l'interazione e la comprensione del modo in cui è possibile applicare questa intuizione alla complessità della realtà mista è fondamentale. Se non solo è possibile ricreare le esperienze di condivisione in realtà mista, ma è necessario supercaricarle, sarà un cambio di paradigma per il futuro del lavoro. La progettazione di esperienze condivise in realtà mista è uno spazio nuovo e interessante, che è solo all'inizio.

## <a name="get-started-building-shared-experiences"></a>Inizia subito a creare esperienze condivise

A seconda dell'applicazione e dello scenario, per ottenere l'esperienza desiderata saranno necessari vari requisiti. Alcuni di questi includono
* Creazione di corrispondenze: Possibilità di creare sessioni, annunciare la sessione e individuare e invitare utenti specifici, sia localmente che in remoto, per partecipare alla sessione.
* Condivisione di ancoraggio: Possibilità di allineare le coordinate tra più dispositivi in uno spazio locale comune, in modo che gli ologrammi vengano visualizzati nella stessa posizione per tutti gli utenti.
* Rete Possibilità di avere posizioni, interazioni e movimenti di persone e ologrammi sincronizzati in tempo reale in tutti i partecipanti.
* Archiviazione dello stato: Possibilità di archiviare caratteristiche e posizioni degli ologrammi nello spazio per l'aggiunta a metà sessione, il richiamo in un secondo momento e l'affidabilità in caso di problemi di rete.


La chiave per le esperienze condivise è costituita da più utenti che vedono gli stessi ologrammi nel mondo sul proprio dispositivo, spesso grazie alla condivisione di ancoraggi per allineare le coordinate tra dispositivi.
Per condividere gli ancoraggi, usare gli <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">ancoraggi spaziali di Azure</a>:
* Prima di tutto l'ologramma viene posizionato dall'utente.
* L'app crea un [ancoraggio spaziale](coordinate-systems.md) per aggiungere un ologramma preciso nel mondo.
* Gli ancoraggi possono essere condivisi nei dispositivi HoloLens, iOS e Android tramite gli <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">ancoraggi spaziali di Azure</a>. 

Con un ancoraggio spaziale condiviso, l'app in ogni dispositivo dispone ora di un sistema di coordinate comune in cui è possibile collocare il contenuto. A questo punto l'app può garantire la posizione e l'orientamento dell'ologramma nella stessa posizione.
Nei dispositivi HoloLens è anche possibile condividere gli ancoraggi offline da un dispositivo a un altro.  Usare i collegamenti seguenti per decidere quale sia la soluzione migliore per l'applicazione.


## <a name="evaluating-tech-options"></a>Valutazione delle opzioni tecniche:
Sono disponibili diverse opzioni per il servizio e la tecnologia che consentono di creare esperienze di realtà mista multiutente.  Può essere difficile scegliere un percorso, in modo da adottare una prospettiva incentrata sullo scenario. di seguito sono elencate alcune opzioni.

## <a name="shared-static-holograms-no-interactions"></a>Ologrammi statici condivisi (nessuna interazione):
Sfruttare gli <a href="https://docs.microsoft.com/azure/spatial-anchors/" target="_blank">ancoraggi spaziali di Azure</a> nell'app.  L'abilitazione e la condivisione di ancoraggi spaziali tra i dispositivi consentono di creare un'applicazione in cui gli utenti visualizzano gli ologrammi nello stesso punto nello stesso momento.  È necessaria una sincronizzazione aggiuntiva tra dispositivi per consentire agli utenti di interagire con gli ologrammi e visualizzare i movimenti o gli aggiornamenti di stato degli ologrammi.

## <a name="share-1st-person-perspective"></a>Condividi la prospettiva del primo utente:
Usare il supporto Miracast incorporato, per gli utenti locali quando si dispone di un ricevitore Miracast supportato, ad esempio un PC o una TV, non è necessario alcun codice dell'app aggiuntivo.

Usare <a href="https://github.com/microsoft/mixedreality-webrtc" target="_blank">MixedReality-WebRTC</a> nell'app, per gli utenti remoti o quando si dispone di dispositivi non Miracast che si vuole condividere.  L'abilitazione di una connessione WebRTC consente di 1:1 flussi audio/video tra gli utenti, con un canale dati per la messaggistica tra dispositivi.  L'implementazione della realtà mista ottimizza per HoloLens, fornendo un flusso video di acquisizione della realtà mista della visualizzazione dell'utente HoloLens ad altri.  Se si desidera aumentare la scalabilità verticale dei flussi video a più client remoti, viene in genere usato un <a href="https://webrtcglossary.com/mcu/" target="_blank">provider di servizi MCU</a> (multipoint Conference Unit), ad esempio SignalWire.  Una distribuzione SignalWire con un clic in Azure è disponibile tramite <a href="https://github.com/andywolk/azure-freeswitch-gpu-windows" target="_blank">FreeSwitch</a>.  Si noti che si tratta di un servizio a pagamento e SignalWire non è di proprietà/affiliato a Microsoft.

## <a name="presenter-spectator-applications-and-demos"></a>Relatore-applicazioni e demo Spectator:
Utilizzare <a href="https://github.com/microsoft/MixedReality-SpectatorView" target="_blank">MixedReality-SpectatorView</a> nell'app.  Abilitare altri dispositivi (HL, Android, iOS e videocamere) per vedere cosa vede HoloLens da una prospettiva diversa nello stesso percorso e ricevere aggiornamenti sulle interazioni dell'utente HoloLens dell'host che interagisce con gli ologrammi.  Guardare, scattare foto * e registrare video sulle operazioni dell'host con gli ologrammi nell'applicazione dal punto di vista spaziale con il compagno spettatore della stessa app.

*Nota: Le immagini vengono acquisite tramite screenshot sui dispositivi iOS/Android.

## <a name="multi-user-collaborative-experience"></a>Esperienza di collaborazione multiutente:
Inizia con l' [esercitazione](mrlearning-sharing(photon)-ch1.md)per l'apprendimento multiutente, che sfrutta gli <a href="https://docs.microsoft.com/azure/spatial-anchors/" target="_blank">ancoraggi spaziali di Azure</a> per gli utenti locali e <a href="https://www.photonengine.com/PUN" target="_blank">Photon SDK</a> per sincronizzare il contenuto o lo stato nella scena.  Crea applicazioni di collaborazione localmente in cui ogni utente ha una propria prospettiva sugli ologrammi nella scena e può interagire completamente con gli ologrammi.  Gli aggiornamenti vengono forniti in tutti i dispositivi e la gestione dei conflitti di interazione viene gestita da Photon.  Si noti che Photon è un prodotto non Microsoft, quindi è possibile che sia necessaria una relazione di fatturazione con Photon per commercializzare e la scalabilità per un utilizzo superiore.

## <a name="future-work"></a>Lavori futuri:
Le funzionalità e le interfacce dei componenti consentono di fornire coerenza comune e un supporto affidabile tra i vari scenari e le tecnologie sottostanti.  Fino ad allora, scegliere il percorso migliore che si allinea allo scenario che si sta tentando di ottenere nell'applicazione.

Uno scenario diverso o il desiderio di usare una tecnologia o un servizio diverso?  
Inviare commenti e suggerimenti come problemi di GitHub nel repository corrispondente, nella parte inferiore di questa pagina, oppure contattare <a href="https://holodevelopers.slack.com/">HoloDevelopers Slack</a>.


## <a name="see-also"></a>Vedere anche
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Ancoraggi nello spazio di Azure</a>
* [Ancoraggi nello spazio condivisi in DirectX](shared-spatial-anchors-in-directx.md)
* [Esperienze condivise in Unity](shared-experiences-in-unity.md)
* [Visualizzazione spettatore](spectator-view.md)

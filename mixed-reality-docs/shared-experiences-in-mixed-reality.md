---
title: Condividere esperienze in realtà mista
description: Le app holographic possono condividere gli ancoraggi spaziali da uno HoloLens a altro, consentendo agli utenti di eseguire il rendering di ologramma nello stesso punto nel mondo reale tra più dispositivi.
author: thetuvix
ms.author: grbury
ms.date: 02/10/2019
ms.topic: article
keywords: condividere esperienze, mista realtà, ologrammi, ancoraggio spaziale, multiutente, più
ms.openlocfilehash: b27da1e73c927a26e33746cd2db08e67c6f70acc
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605130"
---
# <a name="shared-experiences-in-mixed-reality"></a>Condividere esperienze in realtà mista

Ologrammi non devono mantenere privato a un solo utente. Possono condividere le app holographic [Anchor spaziali](coordinate-systems.md) da uno HoloLens, dispositivo iOS o Android a un altro, consentendo agli utenti di eseguire il rendering di ologramma nello stesso punto nel mondo reale tra più dispositivi.

## <a name="six-questions-to-define-shared-scenarios"></a>Sei domande per definire scenari condivisi

Prima di iniziare la progettazione di esperienze condivise, è importante definire gli scenari di destinazione. Questi scenari di aiutare a chiarire cosa si ha la progettazione e stabilire un vocabolario comune per confrontare e contrapporre le funzionalità necessarie durante l'utilizzo. Comprendere il problema principale e vulnerabilità diversi per le soluzioni, è fondamentale per le opportunità esploreremo intrinseche in questo nuovo tipo di supporto.

Tramite i prototipi interni ed esplorazioni dal nostro agenzie di partner di HoloLens, abbiamo creato sei domande che consentono di definire scenari condivisi. Queste domande formano un framework, non devono essere ritenute esaustive, per estrarre gli attributi più importanti degli scenari.

### <a name="1-how-are-they-sharing"></a>1. Come si condividono?

Una presentazione potrebbe essere indotti da un singolo utente virtuale, mentre più utenti possono collaborare, o un docente potrebbe fornire indicazioni agli studenti virtuali utilizzo di materiali virtuale, ovvero la complessità di aumenta le esperienze in base al livello di un utente dispone di agenzia o può avere in uno scenario.

![Uomo e donne con holograph su tabella](images/man-and-women-with-holograph-on-table-500px.png)

Esistono diversi modi per condividere, ma abbiamo scoperto che la maggior parte rientra in tre categorie:
* **Presentazione**: Quando viene visualizzato lo stesso contenuto a utenti diversi. Ad esempio:  Professore è fornire una conferenza per gli studenti che diversi utilizzano lo stesso materiale holographic presentato a tutti gli utenti. Il professor tuttavia può includere l'hint per la propria e note che potrebbero non essere visibili ad altri utenti.
* **Collaborazione**: Quando gli utenti operano insieme per ottenere alcuni obiettivi comuni. Ad esempio:  Il professor ha un progetto per apprendere come eseguire un intervento di cuore. Gli studenti uniscono e creare un'esperienza di lab competenze condiviso che consente agli studenti medici di collaborazione sul modello di base e altre.
* **Materiale sussidiario**: Quando una persona aiuta a un utente per risolvere un problema in un'interazione di stile più uno. Ad esempio:  Il professor che fornisce indicazioni per uno studente quando che sta eseguendo il lab di competenze operative cuore dell'esperienza di condiviso.

### <a name="2-what-is-the-group-size"></a>2. Che cos'è la dimensione del gruppo?

**Uno a uno** esperienze di condivisione può fornire una linea di base sicuro e idealmente è possono creare i modelli di prova a questo livello. Ma tenere presente che la condivisione con gruppi di grandi dimensioni (oltre 6 persone) può causare difficoltà da tecnici (dati e rete) per social networking (l'impatto di trovarsi in una stanza con [avatar diversi](https://vimeo.com/160704056)). Complessità aumenta in misura esponenziale man mano che procede dalla **piccola** al **gruppi di grandi dimensioni**.

Si è constatato che le esigenze dei gruppi possono essere classificati in tre categorie di dimensioni:
* 1:1
* Small < 7
* Grandi > = 7

Dimensione del gruppo rende per una domanda importante in quanto influisce sul:
* Rappresentazioni delle persone presenti lo spazio holographic
* Scalabilità degli oggetti
* Scalabilità dell'ambiente

### <a name="3-where-is-everyone"></a>3. Dove si trova tutti gli utenti?

La forza della realtà mista entra in gioco quando un'esperienza condivisa può avvenire nello stesso percorso. Che definiamo **posizionati**. Quando viene distribuito il gruppo e almeno uno dei partecipanti non è inclusa nello stesso spazio fisico (come avviene spesso con VR) è chiamare invece che un'esperienza remota. È spesso il caso che il gruppo dispone **entrambi** partecipanti con risorse condivise e remoti (ad esempio, due gruppi nelle sale).

![Tre persone con holograph su tabella](images/three-people-with-holograph-on-table-500px.png)

Le seguenti categorie utili per trasmettere in cui si trovano gli utenti:
* Percorso condiviso: Tutti gli utenti saranno nello stesso spazio fisico.
* Remote: Tutti gli utenti saranno in spazi fisici separati.
* Entrambi: Gli utenti sarà una combinazione di spazi con risorse condivise e remoti.

Alcuni dei motivi per cui questa domanda è fondamentale poiché influisce sul:
* La modalità di comunicazione degli utenti?
* Ad esempio:  Se si devono avere gli avatar?
* Quali oggetti che vengono visualizzati. Tutti gli oggetti condivisi?
* Indica se è necessario adattarsi all'ambiente?

### <a name="4-when-are-they-sharing"></a>4. Quando si condividono?

È in genere pensare **sincrono** esperienze quando esperienze condivise vengono in mente: Tutti opinione tra loro. Ma includere un elemento virtuale che è stato aggiunto da un altro utente e si dispone di un **asincrona** scenario. Si immagini una nota o promemoria vocali, disponibile in un ambiente virtuale. Come è possibile gestire 100 promemoria virtuale a sinistra nella finestra di progettazione? Cosa accade se sono di decine di persone con diversi livelli di privacy?

Prendere in considerazione le proprie esperienze come una di queste categorie di tempo:
* **In modo sincrono**: L'esperienza olografica allo stesso tempo la condivisione. Ad esempio:  Due studenti eseguire il lab di competenze nello stesso momento.
* **In modo asincrono**: Condivisione esperienza olografica in momenti diversi. Ad esempio:  Due studenti esegue il lab di competenze, ma funziona in sezioni separate in momenti diversi.
* **Entrambi**: Gli utenti a volte condivideranno in modo sincrono ma in altri casi in modo asincrono. Ad esempio: Professor classificazione l'assegnazione eseguita per gli studenti a un secondo momento e da mantenere note per studenti per il giorno successivo.

Alcuni motivi per cui questa domanda è importante perché essa agisce:
* Persistenza di oggetto e l'ambiente. Ad esempio:  Archiviare gli stati in modo che possono essere recuperati.
* Prospettiva dell'utente. Ad esempio: Ricordando probabilmente ciò che l'utente è stato osservando quando si esce da Lotus notes.

### <a name="5-how-similar-are-their-physical-environments"></a>5. La similitudine sono i propri ambienti fisici?

La probabilità che due ambienti identici reali, di fuori di esperienze con risorse condivise, è sottile, a meno che tali ambienti sono stati progettati in modo identico. Si è più probabile che abbiano **simili** ambienti. Ad esempio le sale riunioni sono simili, dispongono in genere una tabella ubicata centralmente racchiusa da sedie. Le chat del Living, d'altra parte, sono in genere **dissimili** e può includere qualsiasi numero di parti di arredi in una matrice infinita di layout.

![Holograph su tabella](images/holograph-on-table-500px.png)

Prendere in considerazione le esperienze di condivisione adattamento in una di queste due categorie:
* **Simili**: Gli ambienti che tendono ad avere mobili simile, la luce di ambiente e suono, le dimensioni di spazio fisico. Ad esempio: Professore incluso nel hall conferenza A e gli studenti nelle lezioni hall hall conferenza B. A potrebbe avere anche di sedie un numero minore di B ma potrebbe abbiano una scrivania fisica per posizionare vntana su.
* **Dissimilar**: Ambienti che sono piuttosto diversi nel arredamento impostazioni, dimensioni delle stanze, considerazioni su chiari e audio. Ad esempio:  Il Professor è in una stanza di messa a fuoco, mentre gli studenti sono in un hall grande conferenza riempita con studenti e docenti.

È importante considerare l'ambiente perché interferisce con:
* Modo in cui le persone si verificheranno questi oggetti. Ad esempio:  Se l'esperienza funziona meglio su una tabella e l'utente non dispone di alcun tabelle? O su una superficie piana floor, ma l'utente ha uno spazio risulti troppo affollato.
* Scala degli oggetti. Ad esempio:  L'inserimento di un modello di risorse umane feet 6 in una tabella può essere complessa, ma un modello di cuore funzionerebbe perfettamente.

### <a name="6-what-devices-are-they-using"></a>6. Quali dispositivi usano?

Oggi è probabile che spesso visualizzare esperienze condivise tra due **dispositivi coinvolgenti** (questi dispositivi potrebbero essere leggermente diverso in termini di pulsanti e relative funzionalità, ma non molto) o due **dispositivi holographic** dato le soluzioni in corso destinate a questi dispositivi. Ma è consigliabile che **dispositivi 2D** (per dispositivi mobili o desktop partecipante o osservatore) sarà necessario presi in considerazione, soprattutto in situazioni di **mista dispositivi 2D e 3D**. Informazioni sui tipi di dispositivi che useranno dei partecipanti è importante, non solo perché presentano diversi fedeltà e i vincoli di dati e le opportunità, ma perché gli utenti hanno aspettative univoche per ogni piattaforma.

## <a name="exploring-the-potential-of-shared-experiences"></a>La possibilità di condividere esperienze di esplorazione

Risposte alle domande precedenti possono essere combinate per comprendere meglio lo scenario condiviso, crystallizing le sfide quando si espande l'esperienza. Per il team di Microsoft, questo ha contribuito a stabilire una Guida di orientamento per migliorare le esperienze utilizziamo oggi, comprendere il gesto di questi problemi complessi e come sfruttare i vantaggi di condividere esperienze in realtà mista.

Ad esempio, considerare uno degli scenari di Skype dall'avvio HoloLens: un utente ha lavorato tramite [come correggere un commutatore di luce interrotto](https://www.youtube.com/watch?v=iBfzs3G8BEA) con l'aiuto di un esperto che si trova in modalità remota.

![Correzione di un interruttore con assistenza tramite Skype per HoloLens](images/fix-a-broken-switch-with-hololens-640px.jpg)

<i>Fornisce un esperto <b>1:1</b> indicazioni dal suo <b>2D</b>, computer desktop a un utente di un <b>3D, realtà mista</b> dispositivo. Il <b>materiale sussidiario</b> viene <b>sincrono</b> e gli ambienti fisici sono <b>dissimili</b>.</i>

Un'esperienza simile alla seguente è una modifica passaggio dalla nostra esperienza corrente, ovvero applicando il paradigma di audio e video in un supporto di nuovi. Ma lo sguardo al futuro, meglio è necessario definire la possibilità di esporre gli scenari e creare esperienze che riflettono la forza della realtà mista.

Prendere in considerazione la [dello strumento di collaborazione OnSight](https://www.youtube.com/watch?v=ZOWQp0-Bkkw) sviluppato da Jet Propulsion Laboratory della NASA. Gli scienziati dei dati dalle missioni spaziale Mars possono collaborare con i colleghi in tempo reale all'interno dei dati dal panorama Martian.

![La collaborazione tra i colleghi separate in remoto in modo da pianificare lavoro per l'esplorazione spaziale](images/onsight-nasa-jpl.gif)

<i>Un esperto di gestione esamina un ambiente usando un <b>3D, realtà mista</b> dispositivo con un <b>small</b> gruppo di <b>remoto</b> con i colleghi <b>2D e 3D</b> dispositivi. Il <b>collaborazione</b> viene <b>sincrono</b> (ma è possibile accedere in modo asincrono) e gli ambienti fisici (quasi) sono <b>simile</b>.</i>

Esperienze, ad esempio OnSight presentano nuove opportunità per collaborare. Da sottolineare fisicamente gli elementi nell'ambiente virtuale per la condivisione di tale prospettiva come questi argomenti illustrano i loro risultati e permanente accanto a un collega. OnSight Usa l'obiettivo di full immersion e presenza per ripensare esperienze di condivisione nella realtà mista.

Collaborazione intuitiva è il fondamento della conversazione e l'utilizzo congiunto e comprendere in che modo applicare questo intuizione alla complessità della realtà mista è fondamentale. Se è possibile non solo ricreare esperienze di condivisione nella realtà mista ma ultrapotenzia li, sarà infatti un nuovo paradigma per il futuro di lavoro. Progettazione delle esperienze condivise nella realtà mista è nuovo e interessante spazio, siamo solo all'inizio.

## <a name="get-started-sharing-experiences"></a>Inizia subito a condividere esperienze

A seconda dell'applicazione e scenario, saranno presenti diversi requisiti per ottenere l'esperienza desiderata. Tra cui
* Creazione di corrispondenza: Possibilità di creare sessioni, annunciare, sessione e individuare e invitare persone specifiche, sia localmente e in modalità remota a partecipare alla sessione.
* Imposta l'ancoraggio di condivisione: Possibilità di allineare le coordinate tra più dispositivi in uno spazio locale comune, in modo vntana presente nella stessa posizione per tutte le persone.
* Funzionalità di rete: Possibilità di posiziona, le interazioni, e gli spostamenti di persone e vntana sincronizzati tempo reale in tutti i partecipanti.
* Archiviazione dello stato: Possibilità di archiviare le caratteristiche ologrammi e posizioni nello spazio per il join a metà della sessione, è importante ricordare alla volta successiva e affidabilità su problemi di rete.


La chiave a esperienze condivise è più che gli utenti visualizzino la stessa vntana in tutto il mondo nel proprio dispositivo, in genere eseguita tramite la condivisione ancoraggi per allineare le coordinate tra dispositivi.
Per condividere gli ancoraggi, usare il <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Anchor spaziali Azure</a>:
* Prima di tutto l'utente posiziona l'ologramma.
* App crea un [ancoraggio spaziale](coordinate-systems.md) aggiungere tali ologrammi con precisione in tutto il mondo.
* Gli ancoraggi possono essere condiviso per HoloLens, dispositivi iOS e Android tramite il <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Anchor spaziali Azure</a>. 

Con un ancoraggio spaziale condiviso, l'app in ogni dispositivo ha ora un sistema di coordinate comune in cui possono generare contenuto. A questo punto l'app può assicurarsi di posizionare e orientare l'ologrammi nella stessa posizione.
Nei dispositivi HoloLens, è anche possibile condividere gli ancoraggi offline da un dispositivo a altro.  Usare i collegamenti seguenti per decidere l'opzione migliore per l'applicazione.


## <a name="see-also"></a>Vedere anche
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Anchor spaziali</a>
* [Condiviso spaziali ancoraggi in DirectX](shared-spatial-anchors-in-directx.md)
* [Esperienze condivise in Unity](shared-experiences-in-unity.md)
* [Visualizzazione spectator](spectator-view.md)
---
title: Creazione di Galaxy Explorer per HoloLens 2
description: Benvenuti nel percorso di aggiornamento di Galaxy Explorer per HoloLens 2. Proprio come in Galaxy Explorer originale, il nostro team sarà in grado di aprire il progetto in GitHub per garantire che la community abbia accesso completo.
author: l-garrett
ms.author: grbury
ms.date: 06/30/2019
ms.topic: article
keywords: Galaxy Explorer, case study, progetto, esempio
ms.openlocfilehash: 1e04b27ff0382d87f8e6a15ae2b7b2284fa020e6
ms.sourcegitcommit: be3631932ea1c88ac3ad8b2390c98c5a6e8b93ed
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/04/2019
ms.locfileid: "68776535"
---
# <a name="the-making-of-galaxy-explorer-for-hololens-2"></a>Creazione di Galaxy Explorer per HoloLens 2

Benvenuti nel percorso di aggiornamento di Galaxy Explorer per HoloLens 2. [Esplora Galaxy] (https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer "Galaxy Explorer") è stato sviluppato originariamente come un'applicazione open source per HoloLens (1st Gen) tramite il programma Condividi il programma di idea ed è una delle prime esperienze di realtà miste che molti hanno avuto. Ora è in corso l'aggiornamento per le [funzionalità nuove ed entusiasmanti di HoloLens 2](https://www.microsoft.com/hololens/hardware).

Come uno degli [studi di realtà mista Microsoft](galaxy-explorer-update.md#mixed-reality-studios), in genere si sviluppano soluzioni di livello commerciale e si stanno sviluppando & test sulle piattaforme di destinazione durante il processo di sviluppo e creatività. È ora disponibile la situazione univoca in cui non è ancora possibile accedere ai dispositivi HoloLens 2, ma è entusiasta di avviare gli aggiornamenti in Galaxy Explorer. Questo progetto verrà usato per i Framework e gli strumenti, ad esempio [MRTK V2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html), che diventano disponibili per gli utenti e per la community, per poi offrirci il viaggio.

Proprio come in Galaxy Explorer originale, il [nostro team](galaxy-explorer-update.md#meet-the-team) sarà [in grado di aprire il progetto in GitHub](https://github.com/Microsoft/GalaxyExplorer) per garantire che la community abbia accesso completo. Il nostro percorso verrà documentato in modo completo sulla trasparenza dei modi in cui è stato sottoposto a porting da MRTK V1 a MRTK V2, in che modo è stata migliorata l'esperienza in base alle nuove funzionalità disponibili in HoloLens 2 e in che modo è stato assicurato che Galaxy Explorer è rimasto Esperienza multipiattaforma. Quindi, che tu stia visualizzando Galaxy Explorer in HoloLens (1 ° generazione), HoloLens 2, un auricolare per la realtà mista di Windows o sul tuo desktop Windows 10, vogliamo assicurarti che tu abbia un'esperienza immersiva e ti piaccia il percorso così com'è.

Questa pagina verrà espansa Man mano che si procede attraverso il progetto e verranno forniti collegamenti ad articoli più dettagliati, codice, artefatti di progettazione, documentazione aggiuntiva di MRTK V2 e così via.

## <a name="unveiling-the-new-logo"></a>Scopri il nuovo logo

Siamo entusiasti di iniziare con un'anteprima del nuovo logo di Galaxy Explorer. Pur facendo un omaggio al logo originale con il latte, abbiamo progettato una visualizzazione realistica e aggiornato la tipografia per offrire un'idea più accattivante e moderna. Il logo è incluso in un'anteprima di una delle nuove icone.

![Logo di New Galaxy Explorer](images/ge-update-app-icon.png)

La progettazione e la tipografia del logo consentiranno di impostare il tono per l'aspetto generale degli elementi dell'interfaccia utente nell'intera esperienza. 

## <a name="thinking-about-interactions"></a>Considerazioni sulle interazioni

Come studio creativo, siamo entusiasti del privilegio di trasferire Galaxy Explorer a HoloLens 2. Dall'inizio abbiamo voluto che l'esperienza fosse una celebrazione del nuovo dispositivo e per dimostrare che l'empowerment della realtà mista è limitato solo alla fantasia.

HoloLens 2 consente agli utenti di toccare, afferrare e spostare gli ologrammi in modi che ritengono naturale: rispondono molto come gli oggetti reali. I modelli a mano completamente articolata sono sorprendenti, perché consentono agli utenti di fare ciò che si ritiene naturale. Ad esempio, tutti gli utenti preferiscono una Coppa leggermente diversa e, anziché applicare un metodo particolare, HoloLens 2 consente di eseguire questa operazione.

>[!VIDEO https://www.youtube.com/embed/wogJv5v9x-s]

Si tratta di un grande cambiamento rispetto alle interfacce basate sul tocco aereo sui dispositivi HoloLens di prima generazione. Invece di interagire con gli ologrammi a distanza, gli utenti possono ora ottenere "Close e personal". Quando si trasferiscono esperienze esistenti a HoloLens 2 o si pianificano nuove esperienze, è importante avere familiarità con la manipolazione diretta degli ologrammi.

### <a name="direct-manipulation-vs-the-vast-distances-in-space"></a>Manipolazione diretta rispetto alle vaste distanze nello spazio

Si tratta di un'esperienza magica che permette di raggiungere, afferrare un pianeta e tenerlo a portata di mano. Il problema con questo approccio è costituito dalla dimensione del sistema solare, che è enorme. L'utente deve esplorare la stanza per avvicinarsi a ogni pianeta per poter interagire con esso.

Per consentire agli utenti di interagire con gli oggetti più lontani, MRTK offre raggi a mano che si rivelano dal centro della palma dell'utente, agendo come un'estensione del manuale. Un cursore a forma di ciambella viene collegato alla fine del raggio per indicare dove si interseca il raggio con un oggetto di destinazione. L'oggetto su cui si posa il cursore può quindi ricevere i comandi gestuali dalla mano. 

>[!VIDEO https://www.youtube.com/embed/Qol5OFNfN14]

Nella versione originale di Galaxy Explorer, l'utente si rivolgerebbe a un pianeta con il cursore dello sguardo e quindi il tocco aereo per chiamarlo più vicino. Il modo più semplice per trasferire l'esperienza in HoloLens 2 è quello di adottare questo comportamento e usare i raggi mano per selezionare i pianeti. Sebbene si trattasse di un problema funzionale, ci ha lasciato più.

### <a name="back-to-the-drawing-board"></a>Torna alla lavagna di disegno

Ci siamo riuniti per ideate ciò che poteva essere compilato sopra le interazioni esistenti. Il pensiero era: Sebbene HoloLens 2 consenta agli utenti di interagire con gli ologrammi in modo naturale e realistico, gli ologrammi sono per definizione non reali. Quindi, purché un'interazione sia plausibile per l'utente, non è importante se tale interazione sarebbe possibile con un oggetto reale o meno, possiamo renderla possibile.

Un concetto che abbiamo esplorato era basato sulla telecinesi, ovvero la potenza per manipolare gli oggetti con la stessa idea. Spesso visto nei film Super Hero, una persona avrebbe dovuto tenere conto e chiamare un oggetto nella loro mano aperta. Abbiamo avuto una certa idea e abbiamo creato un breve abbozzo di come il concetto potrebbe funzionare.

![Concetto di interazione forzata](images/ge-update-interactions-concept-force-grab.png)

L'utente indicherà il raggio della mano su un pianeta, che fornirebbe il feedback di destinazione. Man mano che l'utente estende la propria mano aperta, il pianeta viene indirizzato verso l'utente da una forza magica fino a quando non è sufficientemente vicino per poterlo acquisire. Quindi, il nome dell'interazione: forzare l'esecuzione. Man mano che l'utente spinge il mondo con la loro apertura, tornerà alla propria orbita.

### <a name="force-grab-prototyping"></a>Forza la prototipazione

Sono stati quindi creati più prototipi per testare il concetto: In che modo l'interazione si ritiene complessiva? Se l'oggetto chiamato si arresta davanti all'utente o è attaccato alle mani fino a quando non viene inserito? L'oggetto chiamato deve modificare le dimensioni o la scala durante la chiamata?

<!--
Here is Amit Rojtblat (Technical Artist) presenting one of the prototypes to Yasushi Zonno (Creative Lead).

------------------------------------------------------------------

__*--- VIDEO OF AMIT PLAYING AND EXPLAINING THE PROTOTYPE ---*__

__*--- NEEDS TO BE UPLOADED (TO YOUTUBE?) AND LINKED ---*__

------------------------------------------------------------------
-->

### <a name="implementing-force-grab-into-the-application"></a>Implementazione dell'esecuzione forzata nell'applicazione

Quando si è provato a forzare i pianeti, abbiamo scoperto che abbiamo dovuto modificare la scala del sistema solare. Si è scoperto che una rappresentazione accurata e di medie dimensioni del sistema solare è difficile per gli utenti capire e navigare, non sapevano dove cercare. Tuttavia, una rappresentazione accurata di piccole dimensioni rende alcuni pianeti troppo piccoli per essere facilmente selezionati. Di conseguenza, le dimensioni dei pianeti e la spaziatura tra oggetti solari sono state progettate per essere confortevoli all'interno di una stanza di medie dimensioni, mantenendo al tempo stesso l'accuratezza relativa.

Durante le fasi successive dello sprint di sviluppo, abbiamo avuto una buona fortuna per avere a disposizione gli esperti di realtà mista MSFT, quindi abbiamo dovuto lavorare come tester esperti ed eseguire iterazioni rapide nell'interazione di forzatura.

![Jenny Kam test di una build di anteprima di Galaxy Explorer](images/ge-update-user-testing.png)

In immagine: Jenny Kam, Senior Design lead, test di un lavoro in corso in Galaxy Explorer.

### <a name="adding-affordances-for-targeting"></a>Aggiunta di affordances per la destinazione

Quando abbiamo sperimentato HoloLens 2, abbiamo scoperto che anche se le nuove interazioni sono naturali e intuitive, gli ologrammi rimangono invariati: senza sensazioni di peso o tattili. Poiché gli ologrammi non forniscono il feedback naturale che gli utenti sono abituati a ricevere quando interagiscono con gli oggetti, è necessario crearli.

Sono stati rilevati commenti e suggerimenti visivi e audio che gli utenti fornivano per le varie fasi delle loro interazioni. Poiché il meccanismo di forzatura è fondamentale per interagire con Galaxy Explorer, abbiamo fatto molte iterazioni. Lo scopo era quello di trovare il giusto equilibrio tra il feedback audio e visivo per ogni fase dell'interazione, ovvero concentrandosi sull'oggetto previsto, chiamandolo all'utente e quindi rilasciandolo. Si è appreso che è stato richiesto un maggior numero di commenti e suggerimenti visivi per rafforzare l'interazione rispetto a quello usato per HoloLens (1a generazione).

![Visual affordances sui pianeti](images/ge-update-planet-affordances.png)

### <a name="adding-affordances-for-force-grab"></a>Aggiunta di affordances per Force appigli
 
Una volta ottenuto il meccanismo di forzatura di base con audio e Visual affordances, abbiamo esaminato come rendere più intuitiva la selezione dei pianeti. Ci sono due aspetti principali da considerare: Poiché il sistema solare è un'interfaccia 3D, è necessario che gli utenti apprendano come indirizzare gli oggetti in modo coerente. Questo è stato aggravato dal fatto che il raggio della mano è molto veloce quando si seleziona un oggetto, facendo in modo che i pianeti si spostano verso l'utente incredibilmente rapidamente.

Questa operazione è stata affrontata con una soluzione a tre punte. Il primo era abbastanza intuitivo: rallentare il processo di selezione in modo che i pianeti approccino l'utente a un ritmo più naturale. Dopo che la velocità è stata modificata, è stato necessario rivedere i affordances audio e visivi, aggiungendo commenti e suggerimenti audio aggiuntivi in modo da tenere traccia dell'utente.

La seconda parte della soluzione consisteva nel rendere estremamente tangibile la visualizzazione dell'intera interazione forzata. È stata visualizzata una linea spessa che si sposta verso l'oggetto di destinazione quando il raggio della mano si connette, quindi riporta di nuovo l'oggetto all'utente come un lazo. 

![Affordances visivo "lazo" per la forzatura](images/ge-update-lasso-affordances.png)

Infine, la scalabilità del sistema solare è stata ottimizzata in modo che i pianeti fossero abbastanza grandi da raggiungere lo sguardo e il raggio a mano dell'utente. 

Questi tre miglioramenti consentono agli utenti di effettuare selezioni accurate, chiamando i pianeti in modo intuitivo. In generale, l'effetto del recupero forzato finale è un'esperienza più coinvolgente e interattiva nel sistema solare.

## <a name="spotlight-on-jupiter"></a>Spotlight su Jupiter

Creare i corpi solari del modo latte è un'esperienza umiliante. In particolare, le caratteristiche univoche di Jupiter ne fanno una visione. È il più grande e più colorato dei giganti del gas e contiene un numero maggiore di massa rispetto a tutti gli altri pianeti combinati. Le sue grandi bande di turbolenze e dinamiche cloud sono il prefetto per un'attenzione artistica speciale.

### <a name="geometry-and-meshes"></a>Geometria e mesh

Come un gigante gassoso, le shell esterne di Jupiter sono costituite da livelli gassosi. La combinazione della velocità rotazionale veloce, dello scambio di calore interno e delle forze Coriolis crea livelli colorati e flussi che formano un turbinio di nastri e vortici cloud. L'acquisizione di questa complessa bellezza era fondamentale per la creazione del nostro sistema solare.

È stato immediatamente chiaro che l'uso di tecniche di visualizzazione, ad esempio simulazioni fluide e trame animate con flussi pre-calcolati, non è più una questione. La potenza di calcolo necessaria per simulare questo insieme a tutti gli altri eventi contemporaneamente avrebbe avuto un impatto significativo sulle prestazioni. 

![Panoramica dell'oggetto Jupiter](images/ge-update-jupiter-shells-complete.jpg)

Il secondo approccio era una soluzione "Smoke-and-mirror", costituita dalla sovrapposizione di livelli di trama trasparente, ognuno dei quali ha affrontato un aspetto specifico del movimento atmosferico, compilato su una composizione di mesh rotanti.

Nell'immagine seguente è possibile visualizzare la shell interna sulla sinistra. Questo livello opaco fornisce uno sfondo alla composizione per proteggersi da eventuali piccoli gap tra i diversi livelli che comprendono i cloud. A causa della rotazione lenta del livello, viene anche servito come buffer visivo tra i gruppi di movimento più veloci per facilitare la creazione di Unity visuali in tutti i livelli.

Dopo aver impostato il punto di ancoraggio sul modello, i livelli del cloud spostando sono stati proiettati nelle mesh centrali e giuste visualizzate sotto.

![Panoramica dell'oggetto Jupiter con Shell separate](images/ge-update-jupiter-shells-separated.jpg)

### <a name="texturing"></a>Texturing

La trama esistente è stata suddivisa in un Atlante di trama in tre parti: Il terzo superiore ospita un livello senza movimento di cloud con gap per fornire un effetto di parallasse, la sezione intermedia contiene i flussi esterni a spostamento rapido e il terzo inferiore contiene un livello di base interno a rotazione lenta.

La caratteristica grande macchia rossa è stata inoltre suddivisa nelle varie parti mobili e quindi inserita in un'area altrimenti invisibile della trama. Questi componenti possono essere considerati come le macchie rosse nella sezione centrale dell'immagine seguente.

Poiché ogni banda ha una direzione e una velocità specifiche, la trama è stata applicata singolarmente a ogni mesh. I mesh hanno quindi un centro e un punto di perno comuni per poter animare in modo concentrico l'intera superficie.

![Panoramica delle trame Jupiter](images/ge-update-jupiter-planet-cloud-texture.png)

### <a name="rotation-and-texture-behavior"></a>Comportamento della rotazione e della trama

Ora che è stata impostata la composizione visiva di Jupiter, era necessario assicurarsi che le velocità di rotazione e di orbita fossero calcolate correttamente e applicate di conseguenza. Per il completamento di una rotazione completa, per Jupiter sono necessarie circa 9 ore. Si tratta di una situazione di definizione dovuta alla rotazione differenziale. Di conseguenza, il flusso equatoriale è stato impostato come ' flusso Master ', accettando 3600 frame per una rotazione completa. Ogni altro livello doveva avere una velocità rotazionale come fattore di 3600, in modo da corrispondere alla posizione iniziale, consentendo ad esempio 600, 900, 1200, 1800 e così via.

![Trame della shell Jupiter](images/ge-update-shell-texture.jpg)


### <a name="the-great-red-spot"></a>La grande macchia rossa

I flussi che ruotano singolarmente hanno fornito una buona impressione visiva, ma non sono stati dettagliati se osservati in un intervallo di chiusura.

Il punto di vista più accattivante era il posto di Giove, che ha creato un set di mesh e trame in modo specifico.
 
È stato usato un meccanismo simile a quello delle bande di Giove: un set di parti rotanti è stato composto l'uno dall'altro, mentre veniva anche raggruppato sotto il "livello master" per assicurarsi che rimangano in posizione indipendentemente dalla velocità con cui si sposta il resto.

Quando i mesh sono stati configurati e sul posto, sono stati applicati livelli diversi del vortice Storm e ogni disco è stato animato singolarmente, i pezzi centrali si spostano più velocemente, con il resto progressivamente rallentato quando si sposta verso l'esterno.

![Giove grande Red Mesh spot](images/ge-update-great-red-spot-mesh.jpg)

La composizione ha anche lo stesso pivot di ogni altra mesh, mantenendo anche l'inclinazione dall'asse y originale (!) per consentire la libertà nell'animazione della rotazione. 3600 frame è la velocità di base, in cui ogni livello presenta un fattore come un periodo di rotazione.

![Trama di Giove grande Red Spot](images/ge-update-red-spot-mesh-texture.jpg)

### <a name="getting-it-right-in-unity"></a>Ottenere l'it direttamente in Unity

Quando si implementa questa funzionalità in Unity, è necessario tenere presenti alcuni aspetti fondamentali.

Unity è facilmente confuso quando si gestiscono grandi set di livelli trasparenti. La soluzione consisteva nel duplicare il materiale della trama per ogni mesh e applicare progressivamente i valori della coda di rendering ascendenti dall'interno all'esterno di 5 a ogni materiale.

Il risultato è che la shell interna disponeva di un valore della coda di rendering di 3000 (impostazione predefinita), mentre in un secondo momento l'esterno statico veniva modificato con un valore pari a 3010 3005. La grande macchia rossa (che avanza da interno a livello esterno), terminata con un valore di 3025 in questo modello.

![Oggetto finale Jupiter](images/ge-update-jupiter-final.jpg)

### <a name="final-touches"></a>Tocchi finali

I livelli Jupiter con trama sono stati configurati inizialmente, il che si è rivelato insufficiente per l'implementazione.

Lo shader standard del pianeta originale (e tutte le relative varianti) riceve le informazioni di illuminazione tramite uno script, SunLightReceiver, che non è supportato dallo shader standard MRTK.

Semplicemente lo scambio degli shader non è una soluzione perché lo shader standard del pianeta non supporta le mappe di trama con lucidi. Questo shader è stato modificato per fare in modo che la compilazione Jupiter funzioni come previsto.

Infine, è necessario configurare le miscele Alpha impostando la blend di origine su 10 e la blend di destinazione su 5.

![Proprietà di Jupiter Unity](images/ge-update-jupiter-unity-render-queue.jpg)

È possibile visualizzare il rendering finale di Jupiter in Galaxy Explorer.

## <a name="meet-the-team"></a>Incontra il team 

Il nostro team di studio di realtà mista è costituito da designer, artisti 3D, specialisti di UX, sviluppatori, Program Manager e un responsabile di studio. Ci troviamo da tutto il mondo: Belgio, Canada, Germania, Israele, Giappone, Regno Unito e Stati Uniti. Si tratta di un team multidisciplinare che deriva da un background diversificato, ovvero giochi tradizionali e indie, marketing digitale, sanità e scienza.

Siamo entusiasti di creare Galaxy Explorer per HoloLens 2 e di aggiornare le versioni HoloLens (1st Gen), VR e desktop. 

![Il team di Galaxy Explorer](images/ge-update-team-image.png)

In alto da sinistra a destra: Artemis Tsouflidou (Developer), Angie Teickner (Visual Designer), David Janer (UX Designer), Laura Garrett (Delivery & Production lead), Yasushi Zonno (lead creativo), Eline Ledent (Developer) e ben Turner (SR. Developer).
In basso da sinistra a destra: Amit Rojtblat (Technical Artist), Martin Wettig (3D Artist) e Dirk Songuer (studio Head).
Non in primo piano: Tim Gerken (Tech lead) e Oscar Salandin (finestra di progettazione visiva).

## <a name="additional-information"></a>Informazioni aggiuntive

### <a name="mixed-reality-studios"></a>Studi di realtà mista

Microsoft Mixed Reality Studio teams, che si trovano in America, Europa e Asia-Pacifico, sono esperti di progettazione dell'esperienza utente, elaborazione olografica, tecnologie AR/VR e sviluppo 3D; tra cui creazione di asset 3D, DirectX, Unity e Unreal. Ti aiuteremo a immaginare future, progettare, compilare e distribuire soluzioni, consentendo ai clienti di creare un notevole effetto sull'intera organizzazione. Gli studi collaborano a stretto contatto con oltre 22.000 professionisti dei servizi Microsoft per l'integrazione, l'adozione, le operazioni e il supporto delle applicazioni aziendali.

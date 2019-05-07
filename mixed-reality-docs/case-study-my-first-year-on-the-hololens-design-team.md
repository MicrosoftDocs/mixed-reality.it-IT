---
title: Case study - team di progettare il primo anno di HoloLens
description: Il mio percorso da un flatland 2D per il mondo 3D avviato quando è unita in join il team di progettazione di HoloLens in gennaio 2016.
author: designnomad
ms.author: haejinl
ms.date: 03/21/2018
ms.topic: article
keywords: Personal editoriali, progettazione, realtà mista di Windows, HoloLens,
ms.openlocfilehash: 050645e6096559a4f37b033e5ddfdc5444039c08
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873949"
---
# <a name="case-study---my-first-year-on-the-hololens-design-team"></a>Case study - team di progettare il primo anno di HoloLens

Il mio percorso da un flatland 2D per il mondo 3D avviato quando è unita in join il team di progettazione di HoloLens in gennaio 2016. Prima di aggiungere il team, ho dovuto minima esperienza nella progettazione 3D. È ad esempio il proverbio cinese su un viaggio in miglia mille iniziano con un unico passaggio, con la differenza in questo caso il primo passaggio è stato un passo avanti.

![Accettando il salto da 2D a 3D](images/2D_to_3D-800px.gif)<br>
*Accettando il salto da 2D a 3D*

> *"Mi sentii come se Eccoci nella stesura senza sapere come guidare l'auto. Ero sovraccaricato e mischiare, anche se molto specifica. "*<br>
> Jin georgiano Lee

Durante l'anno scorso, prelevato competenze e conoscenze stessa velocità con cui è possibile, ma ho ancora molto da imparare. In questo caso, ho scritto le 4 osservazioni con un'esercitazione video documentare la transizione da un 2D per progettisti dell'interazione 3D. Mi auguro che la mia esperienza offrirà l'ispirazione altre finestre di progettazione per rendere il salto a 3D.

## <a name="good-bye-frame-hello-spatial--diegetic-ui"></a>Frame Arrivederci. Hello spaziale / diegetic dell'interfaccia utente

Ogni volta che ho progettato poster, riviste, siti Web o schermate dell'app, uno specifico intervallo (in genere un rettangolo) è una costante per tutti i problemi. A meno che non si sta leggendo questo post in un HoloLens o un altro dispositivo VR, sei *osservando dall'esterno* tramite schermo 2D protetto in modo sicuro all'interno di un frame. Il contenuto è esterno all'utente. Tuttavia, visore VR realtà mista *Elimina il frame*, in modo che sia nello spazio di contenuto, alla ricerca e lo attraversa il contenuto da interno a esterno.

Comprese questo livello concettuale, ma all'inizio commesso l'errore di trasferimento semplicemente alcune riflessioni 2D nello spazio 3D. Che ovviamente non ha funzionato bene in quanto spazio 3D ha proprietà univoche specifiche, ad esempio una modifica della visualizzazione (basato su testina dell'utente) e [requisito diverso per comodità per l'utente](https://www.youtube.com/watch?v=-606oZKLa_s/) (basato sulle proprietà dei dispositivi e le persone usando essi). Ad esempio, in uno spazio di progettazione dell'interfaccia utente 2D, bloccando gli elementi dell'interfaccia utente nell'angolo di una schermata è un modello molto comune, ma ritiene questo stile di visualizzazione HUD (Head backup Display) dell'interfaccia utente non siano naturale nelle esperienze di MR/VR; impedisce full immersion dell'utente nello spazio e provoca disturbo utente. È come avere una particella polvere fastidiosi nei bicchieri che sono morti per eliminare. Nel corso del tempo l'ho imparato che ritiene più naturale per posizionare il contenuto nello spazio 3D e aggiungere un comportamento bloccato corpo che rende il contenuto seguire l'utente a una distanza fissa relativa.

![Body-locked](images/bodylockedtagalong.gif)<br>
*Body-locked*

<br>

![World-bloccato](images/worldlocked.gif)<br>
*World-bloccato*

### <a name="fragments-an-example-of-great-diegetic-ui"></a>Frammenti: Un esempio di UI Diegetic eccezionali

[Frammenti](https://www.microsoft.com/p/fragments/9nblggh5ggm8), un thriller prima persona crime sviluppato da [Asobo Studio](http://www.asobostudio.com/) per HoloLens illustra una UI Diegetic eccezionali. In questo gioco, l'utente diventa un carattere principale, un detective che si tenta di risolvere un dubbio. Le indicazioni per risolvere il mistero pivotal ottengano editoriali nella stanza fisica dell'utente e sono spesso incorporati all'interno di un oggetto fittizio anziché esistente in modo indipendente. Questo diegetic dell'interfaccia utente tende a essere meno individuabili più bloccato al corpo dell'interfaccia utente, in modo che segnali molti inclusi direzione sguardo virtuale caratteri, suoni, chiaro e Guide (ad esempio, freccia rivolta verso la posizione dell'indicazione) prosegue senza soste utilizzati dal team di Asobo per attirare l'attenzione dell'utente.

![Frammenti - esempi Diegetic UI](images/fragments-game-example-1.jpg)<br>
*Frammenti - esempi Diegetic UI*

### <a name="observations-about-diegetic-ui"></a>Osservazioni sulle diegetic dell'interfaccia utente

Spaziali dell'interfaccia utente (sia bloccato corpo e bloccato world) e diegetic dell'interfaccia utente hanno i propri vantaggi e svantaggi. Ti suggeriamo di provare tutte le app di MR/VR possibili e per sviluppare le proprie comprensione e sensibility per vari dell'interfaccia utente dei metodi di posizionamento le finestre di progettazione.

## <a name="the-return-of-skeuomorphism-and-magical-interaction"></a>La restituzione di skeuomorphism e magico scrivendo interazione

Skeuomorphism, un'interfaccia digitale che simuli la forma degli oggetti reali è stata "certo" negli ultimi 5 a 7 anni nel settore della progettazione. Quando Apple assegnato infine modo alla struttura flat in iOS 7, mi è sembrato come Skeuomorphism era morto infine come una metodologia di progettazione dell'interfaccia. Ma quindi un nuovo tipo di supporto, è arrivato visore VR MR/VR sul mercato e sembra Skeuomorphism restituito nuovamente. : )

### <a name="job-simulator-an-example-of-skeuomorphic-vr-design"></a>Simulatore di processo: Un esempio di struttura VR skeuomorphic

[Processo simulatore](http://jobsimulatorgame.com/), un gioco bizzarri sviluppato da [Labs Owlchemy](https://owlchemylabs.com/) è uno dei più popolare esempio relativo a progettazione VR skeuomorphic. All'interno di questo gioco, i lettori vengono trasportati in futuro in cui i robot sostituire gli esseri umani ed esseri umani visita un museo per sperimentare data la notevole quantità di attività banali uno dei quattro diversi processi: Auto meccanico, gastronomiche Chef, Store Clerk o ruolo di lavoro di Office.

Il vantaggio di Skeuomorphism è chiaro. Ambiente familiare e gli oggetti all'interno di questo gioco consentono agli utenti di realtà virtuale nuovo sentirsi più a proprio agio e presente nello spazio virtuale. Rende anche li ha l'impressione che ha il controllo associando familiarità della Knowledge Base e i comportamenti di oggetti e relativi effetti collaterali fisici corrispondenti. Ad esempio, per bere una tazza di caffè, le persone sufficiente illustrato per il machine caffè, premere un pulsante, selezionare l'handle cup e inclinare verso i bocca come avviene nel mondo reale.

![Simulatore di processo](images/job-simulator.gif)<br>
*Simulatore di processo*

Poiché MR/VR è comunque un supporto allo sviluppo, con una certa skeuomorphism è necessaria per chiarire la tecnologia di MR/VR e per collegare il dispositivo al pubblico più ampio in tutto il mondo. Inoltre, tramite skeuomorphism o rappresentazione realistico potrebbero risultare utili per tipi specifici di applicazioni, ad esempio simulazione di volo o agli altri. Poiché l'obiettivo di queste App per sviluppare e perfezionare competenze specifiche che possono essere applicate direttamente nel mondo reale, la simulazione è vicino al mondo reale, è più trasferibili la Knowledge Base.

Tenere presente che skeuomorphism è solo uno degli approcci. Il potenziale del mondo MR/VR è molto maggiore che e le finestre di progettazione devono cercare di creare interazioni hyper naturale magico scrivendo, ovvero affordance nuove che sono possibili in modo univoco nel mondo MR/VR. Per iniziare, è consigliabile aggiungere poteri magici agli oggetti normali per consentire agli utenti di soddisfare esigenze fondamentali, tra cui teletrasporto e omniscience.

![Magico scrivendo lo sportello del Doraemon (left) e slippers(right) Ruby](images/doraemons-magical-door-and-ruby-slippers.jpg)<br>
*Magico scrivendo lo sportello del Doraemon (left) e slippers(right) ruby*

### <a name="observations-about-skeuomorphism-in-vr"></a>Osservazioni sulle skeuomorphism in realtà virtuale

Da "Ovunque sportello" in Doraemon, "Ruby Slippers" nella procedura guidata di once alla "Della Maurader mappa" Harry Potter, esempi di oggetti ordinari con la potenza di magico scrivendo abbondano in fittizio più diffusi. Questi oggetti magiche presenti consentono di visualizzare una connessione tra il mondo reale e il fantastico, tra che cos'è e cosa è stato possibile. Tenere presente che, quando si progetta il magici o surreali un oggetto deve raggiungere un equilibrio tra funzionalità e intrattenimento. Prestare attenzione alla tentazione per creare qualcosa puramente magico scrivendo solo per i migliori risultati dell'originalità.

## <a name="understanding-different-input-methods"></a>Informazioni sui diversi metodi di input

Quando ho progettato per il supporto di 2D, ho dovuto concentrarsi sul tocco, mouse e interazioni da tastiera per gli input. Nell'area di progettazione di MR/realtà virtuale, il corpo diventa l'interfaccia e gli utenti sono in grado di utilizzare una selezione più ampia dei metodi di input: ad esempio riconoscimento vocale, sguardo, movimento, [-i gradi di libertà 6 controller](https://en.wikipedia.org/wiki/Six_degrees_of_freedom), guanti che permettersi di connessione più diretta e intuitiva e con oggetti virtuali.

![Input disponibili in HoloLens](images/inputs.jpg)<br>
*Input disponibili in HoloLens*

> *"Tutto ciò che è ideale per un elemento e peggiori in termini di qualcos'altro".*<br>
> — [Bill Buxton](https://www.billbuxton.com/)

Ad esempio, movimento di input con mano bare e sensori della fotocamera in un dispositivo HMD libera manualmente gli utenti che contiene i controller o usura sweaty guanti, ma utilizzo frequente può causare la fatica fisica (dette anche Azure Resource Manager gorilla). Inoltre, gli utenti devono mantenere le mani in linea di visuale; Se la fotocamera non è possibile vedere tutti i vantaggi, messi a disposizione non è utilizzabile.

L'input vocale viene correttamente a attraversamento attività complesse in quanto consente agli utenti di eliminare tramite i menu annidati con un solo comando (ad esempio, "Show me i film effettuati da Laika studio.") e anche molto economico se usato in combinazione con altre modalità (ad esempio, "Affrontano me" comando indirizza il ologramma un utente è guardando verso l'utente). Tuttavia, l'input vocale potrebbe non funzionare correttamente in ambienti rumorosi o potrebbe non appropriate in uno spazio molto non interattiva.

Oltre ai gesti e riconoscimento vocale, touchscreen per rilevare i controller (ad esempio, Oculus touch, Vive e così via) sono metodi di input molto diffusi perché sono di facile utilizzo e accurato, sfrutta Repubblica [proprioception](https://en.wikipedia.org/wiki/Proprioception)e fornire suggerimenti aptico passivi. Tuttavia, questi vantaggi sono evidenti al costo di non poter essere mani bare e utilizzare il rilevamento completo con un dito.

![Senso (Left) e Manus VR(Right)](images/senso-and-manus-vr.jpg)<br>
*Senso (Left) e Manus VR (destra)*

Anche se non più famosi come controller, guanti stanno affermandosi anche in questo caso, grazie a onda di MR/VR. Più di recente, input cervello/idea hanno iniziato a guadagnare consensi come interfaccia per gli ambienti virtuali integrando EEG o EMG sensore per cuffia (ad esempio, [MindMaze VR](http://www.mindmaze.com/)).

### <a name="observations-about-input-methods"></a>Osservazioni sui metodi di input

Si tratta di un solo un campione di dispositivi di input disponibili sul mercato per MR/VR. Continueranno a proliferare fino a quando il settore matura e trova un accordo sulle procedure consigliate. Fino ad allora, progettisti dovrebbero restare informati di nuovi dispositivi di input e che mostrano delle doti i metodi di input specifici per il proprio progetto particolare. Finestre di progettazione devono cercare soluzioni creative all'interno di limitazioni, durante la riproduzione anche a punti di forza del dispositivo.

## <a name="sketch-the-scene-and-test-in-the-headset"></a>Tracciare la scena ed eseguire un test di visore Vr

Quando ho lavorato in 2D, sketch principalmente solo il contenuto. Tuttavia, nello spazio di realtà mista che non era sufficiente. È stato necessario schizzo dell'intera scena a imagine meglio le relazioni tra gli oggetti virtuali e l'utente. Per facilitare la mia mentalità spaziali, ho iniziato sketch scene [Cinema 4D](https://www.maxon.net/en/products/cinema-4d/overview/) e a volte creare asset semplice per la creazione di prototipi nella [Maya](http://www.autodesk.com/products/maya/overview/). Non avessi mai utilizzato uno dei programmi prima di aggiungere il team di HoloLens e sono ancora un principiante, ma si utilizzano questi programmi 3D sicuramente ha consentito di acquisire familiarità con la nuova terminologia, ad esempio [shader](https://en.wikipedia.org/wiki/Shader) e [cinematica inversa (inverso cinematica)](https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2016/ENU/Maya/files/GUID-07C3BA47-32BB-477B-B6C5-1090E5C9B81C-htm.html/).

**"Indipendentemente dalla precisione descritto della scena 3D, l'esperienza effettiva in visore VR era quasi mai lo stesso come lo sketch. Ecco perché è importante testare la scena nella destinazione auricolari. "— georgiano Jin Lee**

Per la creazione di prototipi di HoloLens, ho provato tutte le esercitazioni relative alla [esercitazioni di realtà mista](tutorials.md) per iniziare. Quindi ho iniziato a collaudare [HoloToolkit.Unity](https://github.com/Microsoft/HoloToolkit-Unity/) che Microsoft offre agli sviluppatori per accelerare lo sviluppo di applicazioni holographic. Quando noterai bloccato con un elemento, ho pubblicato alla mia domanda [HoloLens domande e risposte Forum](https://forums.hololens.com/categories/questions-and-answers/).

Dopo aver acquisito familiarità con la creazione di prototipi di HoloLens, volevo migliorare la produttività altri programmatori non prototipo in modo indipendente. Quindi, ho apportato un'esercitazione video che illustra come sviluppare un semplice proiettile usando HoloLens. Illustrare brevemente i concetti di base, in modo che anche se si dispone di zero esperienza nello sviluppo di HoloLens, dovrebbe essere possibile seguire la procedura.

<br>

>[!VIDEO https://www.youtube.com/embed/58612RT2CT8]
*Dopo aver apportato questa semplice esercitazione ai non programmatori come Me.*

Per la creazione di prototipi di realtà virtuale, ho fornito i corsi [VR Dev School](http://learn.vrdev.school/) e anche assunto [creazione contenuto 3D per realtà virtuale](https://www.lynda.com/Unreal-Engine-tutorials/3D-Content-Creation-Virtual-Reality/482055-2.html?srchtrk=index%3a1%0alinktypeid%3a2%0aq%3aVirtual+Reality+%0apage%3a1%0as%3arelevance%0asa%3atrue%0aproducttypeid%3a2/) in Lynda.com. Sviluppo VR dell'istituto di istruzione fornito che ulteriori informazioni nella Knowledge Base profondità nella scrittura di codice e nel corso di Lynda offerti me una breve introduzione alla creazione di asset per VR nice.

## <a name="take-the-leap"></a>Richiedere il salto

Un anno fa, mi è parso tutto questo è stato piuttosto complesso. Ora posso dire che era 100% la pena. MR/VR è ancora molto giovane medium e ci sono così tante possibilità interessante in attesa di essere realizzati. Mi sento ispirazione e fortunata in grado di riprodurre una piccola parte di progettare il futuro. Mi auguro che mi verrà aggiunta durante il viaggio nello spazio 3D.

## <a name="about-the-author"></a>Informazioni sull'autore

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Hae Jin Lee" width="60" height="60" src="images/haejinlee.jpg"></td>
<td style="border-style: none"><b>Georgiano Jin Lee</b><br>UX Designer @Microsoft</td>
</tr>
</table>

 

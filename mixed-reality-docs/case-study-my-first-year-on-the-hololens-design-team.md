---
title: 'Case Study: il primo anno del team di progettazione di HoloLens'
description: Il mio viaggio da un Flatland 2D al mondo 3D è stato avviato quando ho aggiunto il team di progettazione di HoloLens a gennaio 2016.
author: designnomad
ms.author: haejinl
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, HoloLens, progettazione, editoriale, personale
ms.openlocfilehash: 050645e6096559a4f37b033e5ddfdc5444039c08
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873949"
---
# <a name="case-study---my-first-year-on-the-hololens-design-team"></a>Case Study: il primo anno del team di progettazione di HoloLens

Il mio viaggio da un Flatland 2D al mondo 3D è stato avviato quando ho aggiunto il team di progettazione di HoloLens a gennaio 2016. Prima di partecipare al team, ho avuto poca esperienza nella progettazione 3D. Era come il proverbio cinese di un viaggio di migliaia di chilometri che iniziava con un unico passaggio, tranne nel mio caso, il primo passaggio era un salto!

![Salto da 2D a 3D](images/2D_to_3D-800px.gif)<br>
*Salto da 2D a 3D*

> *"Mi sentivo come se avessi saltato il posto del conducente senza sapere come guidare l'auto. Ero sopraffatto e spaventato, ma molto concentrato ".*<br>
> -HAE Jin Lee

Nel corso dell'anno scorso, ho preso le competenze e le conoscenze più velocemente possibile, ma ho ancora molto da imparare. Qui ho scritto 4 osservazioni con un'esercitazione video che documenta la transizione da un interaction designer 2D a 3D. Spero che la mia esperienza ispiri altri designer a passare a 3D.

## <a name="good-bye-frame-hello-spatial--diegetic-ui"></a>Fotogramma di addio. Interfaccia utente di Hello Spatial/diegetica

Ogni volta che ho progettato poster, riviste, siti Web o schermate di app, un frame definito (in genere un rettangolo) era una costante per ogni problema. A meno che non si stia leggendo questo post in un HoloLens o in un altro dispositivo VR, si sta *esaminando questa operazione dall'esterno attraverso la* schermata 2D protetta in modo sicuro all'interno di un frame. Il contenuto è esterno all'utente. Tuttavia, l'auricolare realtà mista *Elimina il frame*, in modo che si trovi all'interno dello spazio di contenuto, cercando ed esaminando il contenuto dall'interno.

Ho compreso questo concetto concettualmente, ma all'inizio ho commesso l'errore di trasferire semplicemente il pensiero 2D nello spazio 3D. Questo ovviamente non funziona bene perché lo spazio 3D ha proprietà univoche quali la modifica di una vista (in base al movimento Head dell'utente) e [requisiti diversi per la comodità degli utenti](https://www.youtube.com/watch?v=-606oZKLa_s/) , in base alle proprietà dei dispositivi e degli utenti che li usano. Ad esempio, in uno spazio di progettazione dell'interfaccia utente 2D, il blocco degli elementi dell'interfaccia utente nell'angolo di una schermata è un modello molto comune, ma questa interfaccia utente dello stile HUD (Head up display) non è naturale nelle esperienze di MR/VR. ostacola l'immersione degli utenti nello spazio e causa disagio dell'utente. È come avere una particella di polvere fastidioso nei bicchieri che si sta morendo per eliminare. Nel corso del tempo, ho capito che è più naturale posizionare il contenuto nello spazio 3D e aggiungere il comportamento di blocco del corpo che rende il contenuto seguito dall'utente a una distanza fissa relativa.

![Corpo-bloccato](images/bodylockedtagalong.gif)<br>
*Corpo-bloccato*

<br>

![Con blocco globale](images/worldlocked.gif)<br>
*Con blocco globale*

### <a name="fragments-an-example-of-great-diegetic-ui"></a>Frammenti Esempio di una grande interfaccia utente di diegetica

[Frammenti](https://www.microsoft.com/p/fragments/9nblggh5ggm8), un thriller per la prima persona, sviluppato da [Asobo Studio](http://www.asobostudio.com/) per HoloLens, dimostra una grande interfaccia utente di diegetica. In questo gioco, l'utente diventa un carattere principale, un detective che tenta di risolvere un mistero. Gli indizi cruciali per risolvere questo mistero vengono spruzzati nella stanza fisica dell'utente e spesso sono incorporati all'interno di un oggetto fittizio anziché esistere in modo autonomo. Questa interfaccia utente di diegetica tende a essere meno individuabile rispetto all'interfaccia utente bloccata dal corpo, quindi il team di Asobo ha usato in modo intelligente molti suggerimenti, tra cui direzione dello sguardo, suono, luce e guide, ad esempio la freccia che punta alla posizione dell'indizio, per attirare l'attenzione dell'utente.

![Frammenti-esempi di interfaccia utente di diegetica](images/fragments-game-example-1.jpg)<br>
*Frammenti-esempi di interfaccia utente di diegetica*

### <a name="observations-about-diegetic-ui"></a>Osservazioni sull'interfaccia utente di diegetica

L'interfaccia utente spaziale (sia bloccata dal corpo che bloccata a livello globale) e l'interfaccia utente diegetica hanno i propri punti di forza e debolezze. Si consiglia ai progettisti di provare il maggior numero possibile di app di MR/VR e di sviluppare la propria comprensione e sensibilità per diversi metodi di posizionamento dell'interfaccia utente.

## <a name="the-return-of-skeuomorphism-and-magical-interaction"></a>La restituzione di skeuomorphism e l'interazione magica

Skeuomorphism, un'interfaccia digitale che simula la forma degli oggetti reali è stata "uncool" negli ultimi 5-7 anni nel settore della progettazione. Quando Apple ha infine fornito una soluzione di progettazione semplice in iOS 7, sembrava che skeuomorphism fosse finalmente morto come metodologia di progettazione dell'interfaccia. Tuttavia, un nuovo mezzo, l'auricolare MR/VR è arrivato al mercato e sembra che skeuomorphism restituito nuovamente. : )

### <a name="job-simulator-an-example-of-skeuomorphic-vr-design"></a>Simulatore di processo: Esempio di progettazione di Skeuomorphic VR

[Simulatore di processi](http://jobsimulatorgame.com/), un gioco stravagante sviluppato da [Owlchemy Labs](https://owlchemylabs.com/) è uno degli esempi più diffusi per la progettazione di Skeuomorphic VR. All'interno di questo gioco, i giocatori vengono trasportati in futuro, in cui i robot sostituiscono gli uomini e gli uomini visitano un museo per provare a eseguire attività banali in uno dei quattro diversi processi: Auto Mechanic, gourmet chef, Store Clerk o Office worker.

Il vantaggio di skeuomorphism è chiaro. Gli ambienti e gli oggetti familiari all'interno di questo gioco consentono ai nuovi utenti di VR di essere più comodi e presenti nello spazio virtuale. Inoltre, si ritiene che siano in controllo associando le conoscenze e i comportamenti familiari agli oggetti e alle reazioni fisiche corrispondenti. Ad esempio, per bere una tazza di caffè, è sufficiente che le persone debbano passare alla macchina da caffè, premere un pulsante, estrarre il punto di controllo della tazza e inclinarlo verso la bocca come farebbe nel mondo reale.

![Simulatore di processi](images/job-simulator.gif)<br>
*Simulatore di processi*

Poiché MR/VR è ancora un supporto di sviluppo, l'uso di un determinato grado di skeuomorphism è necessario per demistificare la tecnologia di MR/VR e per introdurlo a destinatari più grandi in tutto il mondo. Inoltre, l'uso di skeuomorphism o di una rappresentazione realistica può essere utile per tipi specifici di applicazioni, ad esempio la simulazione di un intervento chirurgico o Poiché l'obiettivo di queste app è quello di sviluppare e perfezionare competenze specifiche che possono essere applicate direttamente nel mondo reale, più vicino è la simulazione al mondo reale, più è trasferibile la conoscenza.

Tenere presente che skeuomorphism è un unico approccio. Il potenziale del mondo di MR/VR è molto più grande del previsto e i progettisti devono impegnarsi a creare interazioni ipernaturali magiche, nuove affordances che sono in realtà possibili in MR/VR. Come inizio, è consigliabile aggiungere poteri magici a oggetti ordinari per consentire agli utenti di soddisfare i propri desideri fondamentali, tra cui Teleporting e onniscienza.

![Portello magico di Doraemon (a sinistra) e Ruby pantofole (Right)](images/doraemons-magical-door-and-ruby-slippers.jpg)<br>
*Portello magico di Doraemon (a sinistra) e Ruby pantofole (Right)*

### <a name="observations-about-skeuomorphism-in-vr"></a>Osservazioni su skeuomorphism in VR

Da "dovunque" in Doraemon, "Ruby pantofole" nella procedura guidata di Oz alla "mappa di Maurader" in Harry Potter, esempi di oggetti ordinari con energia magica ricca di romanzi popolari. Questi oggetti magici consentono di visualizzare una connessione tra il mondo reale e quello fantastico, tra le funzionalità e i possibili risultati. Tenere presente che quando si progetta l'oggetto magico o surreale, è necessario trovare un equilibrio tra funzionalità e divertimento. Prestare attenzione alla tentazione di creare un elemento puramente magico solo a scopo di novità.

## <a name="understanding-different-input-methods"></a>Informazioni sui diversi metodi di input

Quando ho progettato per il supporto 2D, ho dovuto concentrarmi sulle interazioni tra tocco, mouse e tastiera per gli input. Nello spazio di progettazione di MR/VR, il corpo diventa l'interfaccia e gli utenti sono in grado di usare una selezione più ampia di metodi di input: tra cui sintesi vocale, sguardo, movimento, [controller 6 DOF](https://en.wikipedia.org/wiki/Six_degrees_of_freedom)e guanti che consentono una connessione più intuitiva e diretta con oggetti virtuali.

![Input disponibili in HoloLens](images/inputs.jpg)<br>
*Input disponibili in HoloLens*

> *"Tutto è adatto a qualcosa e peggio per qualcosa di diverso."*<br>
> \- [Fattura Buxton](https://www.billbuxton.com/)

Ad esempio, l'input dei movimenti usando i sensori bare hand e camera su un dispositivo HMD consente agli utenti di liberare i controller o di indossare guanti sudati, ma l'uso frequente può causare affaticamento fisico (a. k. a Gorilla ARM). Inoltre, è necessario che gli utenti rimangano all'interno della linea di controllo; Se la fotocamera non è visibile, non è possibile usare le mani.

L'input vocale è adatto all'attraversamento di attività complesse perché consente agli utenti di tagliare i menu nidificati con un unico comando (ad esempio, "Mostra i film realizzati da Laika Studio)" e anche molto economico quando abbinato ad altre modalità (ad esempio, il comando "Face me" orienta il ologramma che un utente sta osservando verso l'utente). Tuttavia, l'input vocale potrebbe non funzionare correttamente nell'ambiente rumoroso o potrebbe non essere appropriato in uno spazio molto silenzioso.

Oltre ai movimenti e ai dialoghi, i controller gestiti manualmente, ad esempio Oculus touch, vive e così via, sono metodi di input molto diffusi, perché sono facili da usare, accurati, sfruttano i [propriocezione](https://en.wikipedia.org/wiki/Proprioception)di persone e forniscono segnali tattili passivi. Tuttavia, questi vantaggi comportano il costo di non essere in grado di essere rilevati e di usare il rilevamento automatico delle dita.

![Senso (Left) e Manus VR (Right)](images/senso-and-manus-vr.jpg)<br>
*Senso (Left) e Manus VR (Right)*

Sebbene non sia così comune come i controller, i guanti stanno riprendendo il momento grazie all'onda di MR/VR. Più recentemente, l'input Brain/Mind ha iniziato a ottenere la trazione come interfaccia per gli ambienti virtuali integrando il sensore EEG o EMG con la cuffia (ad esempio, [MINDMAZE VR](http://www.mindmaze.com/)).

### <a name="observations-about-input-methods"></a>Osservazioni sui metodi di input

Si tratta di un semplice esempio di dispositivi di input disponibili sul mercato per il Sig. Continueranno a proliferare fino a quando il settore non è maturo e accetta le procedure consigliate. Fino a quel momento, le finestre di progettazione devono rimanere a conoscenza dei nuovi dispositivi di input ed essere ben versati nei metodi di input specifici per il progetto specifico. È necessario che i progettisti cerchino soluzioni creative all'interno delle limitazioni, giocando anche ai punti di forza di un dispositivo.

## <a name="sketch-the-scene-and-test-in-the-headset"></a>Disegnare la scena e testare l'auricolare

Quando ho lavorato in 2D, ho disegnato principalmente solo il contenuto. Tuttavia, nello spazio di realtà misto che non era sufficiente. Ho dovuto disegnare l'intera scena per immaginare meglio le relazioni tra l'utente e gli oggetti virtuali. Per aiutare il mio pensiero spaziale, ho iniziato a disegnare scene in [cinema 4D](https://www.maxon.net/en/products/cinema-4d/overview/) e talvolta creare risorse semplici per la creazione di prototipi in [Maya](http://www.autodesk.com/products/maya/overview/). Non avevo mai usato alcun programma prima di unirlo al team di HoloLens e sono ancora un newbie, ma l'uso di questi programmi 3D mi ha aiutato a familiarizzare con la nuova terminologia, ad esempio [shader](https://en.wikipedia.org/wiki/Shader) e [IK (cinematica inversa)](https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2016/ENU/Maya/files/GUID-07C3BA47-32BB-477B-B6C5-1090E5C9B81C-htm.html/).

**"Indipendentemente dal modo in cui ho disegnato la scena in 3D, l'esperienza effettiva nell'auricolare è quasi mai identica a quella dello sketch. Per questo motivo è importante testare la scena negli auricolari di destinazione. "-HAE Jin Lee**

Per il prototipo di HoloLens, ho provato a eseguire tutte le esercitazioni sulle esercitazioni della [realtà mista](tutorials.md) . Ho iniziato a giocare con [HoloToolkit. Unity](https://github.com/Microsoft/HoloToolkit-Unity/) fornito da Microsoft agli sviluppatori per accelerare lo sviluppo di applicazioni olografiche. Una volta bloccata, ho inviato la mia domanda a [HoloLens question & Forum di risposta](https://forums.hololens.com/categories/questions-and-answers/).

Dopo aver acquisito la conoscenza di base del prototipo di HoloLens, ho voluto consentire agli altri non codificatori di eseguire il prototipo autonomamente. Quindi, ho creato un'esercitazione video che insegna come sviluppare un semplice proiettile usando HoloLens. Illustrerò brevemente i concetti di base, quindi anche se non si ha esperienza con lo sviluppo HoloLens, è necessario poter proseguire.

<br>

>[!VIDEO https://www.youtube.com/embed/58612RT2CT8]
*Questa semplice esercitazione è stata eseguita per i programmatori non come me.*

Per la creazione di prototipi di VR, ho avuto corsi presso [VR dev School](http://learn.vrdev.school/) e ho preso anche la [creazione di contenuto 3D per la realtà virtuale](https://www.lynda.com/Unreal-Engine-tutorials/3D-Content-Creation-Virtual-Reality/482055-2.html?srchtrk=index%3a1%0alinktypeid%3a2%0aq%3aVirtual+Reality+%0apage%3a1%0as%3arelevance%0asa%3atrue%0aproducttypeid%3a2/) in Lynda.com. VR dev School mi ha fornito una conoscenza approfondita del codice e il corso di Lynda mi ha offerto una breve introduzione alla creazione di asset per VR.

## <a name="take-the-leap"></a>Intercalare

Un anno fa, ho pensato che questo era un po' opprimente. Ora posso dire che è stato il 100% vale la pena. MR/VR è ancora molto giovane e ci sono molte possibilità interessanti in attesa di essere realizzate. Mi sento ispirata e fortunata per poter giocare una piccola parte della progettazione del futuro. Ci auguriamo che tu possa partecipare al viaggio nello spazio 3D.

## <a name="about-the-author"></a>Informazioni sull'autore

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Hae Jin Lee" width="60" height="60" src="images/haejinlee.jpg"></td>
<td style="border-style: none"><b>HAE Jin Lee</b><br>Progettazione UX@Microsoft</td>
</tr>
</table>

 

---
title: Sguardo attento
description: HoloLens 2 consente un nuovo livello di contesto e comprensione umana all'interno dell'esperienza olografica, offrendo agli sviluppatori la possibilità di usare le informazioni relative agli utenti che stanno esaminando.
author: sostel
ms.author: sostel
ms.date: 04/05/2019
ms.topic: article
keywords: Rilevamento degli occhi, realtà mista, input, sguardo oculare, sguardi occhi
ms.openlocfilehash: c847f7de2cf4492c89225a88aeaf189f51cfbc40
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387601"
---
# <a name="eye-gaze-on-hololens-2"></a>Eye-sguardi su HoloLens 2
HoloLens 2 consente un nuovo livello di contesto e comprensione umana all'interno dell'esperienza olografica, offrendo agli sviluppatori la possibilità di usare le informazioni relative agli utenti che stanno esaminando. Questa pagina indica agli sviluppatori come possono trarre vantaggio dal monitoraggio degli sguardi per diversi casi d'uso, nonché da cosa cercare quando si progettano interfacce utente basate sull'occhio. 


## <a name="device-support"></a>Supporto di dispositivi

<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><strong>Funzionalità</strong></td>
     <td><a href="hololens-hardware-details.md"><strong>HoloLens (prima generazione)</strong></a></td>
     <td><strong>HoloLens 2</strong></td>
     <td><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
</tr>
<tr>
     <td>Sguardo attento</td>
     <td>❌</td>
     <td>✔️</td>
     <td>❌</td>
</tr>
</table>

## <a name="use-cases"></a>Casi d'uso
Il tracciamento oculare consente alle applicazioni di tenere traccia di dove guarda l'utente in tempo reale. I casi d'uso seguenti descrivono alcune interazioni possibili con la verifica degli occhi in realtà mista.
Tenere presente che il Toolkit per la [realtà mista](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html) è utile per fornire alcuni esempi interessanti e potenti per l'uso degli occhi, ad esempio selezioni di destinazioni supportate dagli occhi, rapide e senza problemi, nonché lo scorrimento automatico del testo in base a elementi esaminati dall'utente. 

### <a name="user-intent"></a>Intenzione dell'utente    
Le informazioni su dove e cosa esamina un utente forniscono un **contesto potente per altri input**, ad esempio Voice, Hands e Controllers.
Tali informazioni possono essere usate per diverse attività.
Questo, ad esempio, può variare da un punto di  vista rapido e semplice a quello della scena, semplicemente esaminando un ologramma e affermando "Select" (vedere anche lo [sguardo e il commit](gaze-and-commit.md)) o dicendo "put this...", quindi esaminando il percorso in cui l'utente desidera inserire l'ologramma e pronunciare "... ". Per alcuni esempi, vedi [Mixed Reality Toolkit - Selezione della destinazione con lo sguardo](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) e [Mixed Reality Toolkit - Posizionamento della destinazione con lo sguardo](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Positioning.html).

Inoltre, un esempio per finalità utente potrebbe includere l'uso di informazioni sugli elementi esaminati dagli utenti per migliorare l'engagement con agenti virtuali incorporati e ologrammi interattivi. Ad esempio, gli agenti virtuali potrebbero adattare le opzioni disponibili e il relativo comportamento in base al contenuto attualmente visualizzato. 

### <a name="implicit-actions"></a>Azioni implicite
La categoria delle azioni implicite è strettamente correlata all'intenzione dell'utente.
L'idea è che gli ologrammi o gli elementi dell'interfaccia utente reagiscono in modo alquanto istintivo che potrebbe non sembrare che l'utente interagisca con il sistema, ma piuttosto che il sistema e l'utente siano sincronizzati. Un esempio è lo **scorrimento automatico basato sull'occhio** , in cui l'utente legge il testo mentre il testo continua a scorrere o a fluire sincronizzato con con lo sguardo dell'utente. Un aspetto fondamentale è che la velocità di scorrimento si adatta alla velocità di lettura dell'utente.
Un altro esempio è **lo zoom e la panoramica supportati dagli occhi,** in cui l'utente può apparire esattamente come se fosse concentrato o meno. L'attivazione dello zoom e il controllo della velocità di zoom possono essere controllati da input voce o mano, che è importante per fornire all'utente la sensazione di controllo, evitando così la sovraccarica. Di seguito vengono descritte in dettaglio le linee guida di progettazione. Una volta eseguito lo zoom avanti, l'utente può seguire in modo semplice, ad esempio, il corso di una strada per esplorare il suo quartiere utilizzando semplicemente il proprio sguardo.
Alcune demo di esempio per questi tipi di interazioni sono disponibili in [Mixed Reality Toolkit - Navigazione con gli occhi](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html).

Altri casi d'uso per le _azioni implicite_ possono includere:
- **Notifiche intelligenti:** non vieni mai disturbato dalle notifiche che vengono visualizzate proprio nel punto su cui ti sei soffermato? Prendendo in considerazione le informazioni a cui un utente presta attenzione, è possibile migliorare questa esperienza compensando le notifiche da cui l'utente sta attualmente guardando. Questo limita le distrazioni e le chiude automaticamente dopo che l'utente ha terminato la lettura. 
- **Ologrammi reattivi:** Olografici che reagiscono in maniera impercettibile quando si osservano. Questo può variare da elementi dell'interfaccia utente leggermente luminosi a un fiore lentamente fiorito a un animale domestico virtuale che inizia a esaminare l'utente o a provare a evitare gli sguardi degli utenti dopo un prolungamento. Questa interazione potrebbe offrire un'interessante sensazione di connettività e soddisfazione nell'applicazione.

### <a name="attention-tracking"></a>Tracciamento dell'attenzione   
Le informazioni su dove o quali utenti esaminano sono uno strumento estremamente potente per valutare l'usabilità delle progettazioni e per identificare i problemi nei flussi di lavoro efficienti. La visualizzazione e l'analisi dei tracciati degli occhi sono una pratica comune in varie aree di applicazione. Con HoloLens 2, viene fornita una nuova dimensione a questa comprensione perché gli ologrammi 3D possono essere inseriti in contesti reali e valutati di conseguenza. Il [Toolkit di realtà mista](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html) fornisce esempi di base per la registrazione e il caricamento dei dati di rilevamento degli occhi e come visualizzarli.

Altre applicazioni in quest'area possono includere: 
-   **Visualizzazione sguardo remoto:** Consente di visualizzare i collaboratori remoti che esaminano per verificare se le istruzioni sono state comprese correttamente e seguite.
-   **Studi di ricerca sugli utenti:** Il rilevamento dell'attenzione può essere usato per esplorare il modo in cui gli utenti di esperti e esperti analizzano visivamente il contenuto o il modo in cui coordinano le attività complesse, ad esempio per l'analisi di dati medici o di macchinari operativi.
-   **Simulazioni di formazione e monitoraggio delle prestazioni:** è possibile fare pratica e ottimizzare l'esecuzione delle attività identificando i colli di bottiglia in modo più efficace nel flusso di esecuzione.
-   **Valutazioni delle progettazioni e ricerche pubblicitarie e di marketing:** Il rilevamento degli occhi è uno strumento comune per la ricerca di mercato quando si valutano i siti Web e i progetti di prodotti.

### <a name="additional-use-cases"></a>Altri casi di utilizzo
- **Giochi:** hai mai sognato di avere dei superpoteri? Ora hai questa opportunità. È possibile levitare gli ologrammi guardandoli. lanciare raggi laser dagli occhi, Trasformare i nemici in pietra o bloccarli. oppure usare la tua vista a raggi x per esplorare l'interno degli edifici. Insomma, con la tua immaginazione potrai superare ogni ostacolo.  

- **Avatar espressivi:** Il rilevamento degli occhi negli Avatar 3D più espressivi usa la data di rilevamento Live per animare gli occhi dell'avatar che indicano l'aspetto dell'utente. Consente inoltre di aggiungere maggiore espressività mediante strizzate d'occhio e ammiccamenti. 

- **Immissione di testo:** Il rilevamento degli occhi può essere usato come alternativa per la voce di testo a basso sforzo, soprattutto quando il discorso o le mani non sono convenienti da usare. 


## <a name="eye-tracking-api"></a>API di tracciamento oculare
Prima di approfondire le linee guida di progettazione specifiche per l'interazione con gli occhi, è opportuno evidenziare brevemente le funzionalità offerte dall'API HoloLens 2 eye tracker per gli sviluppatori. Fornisce una singola occhiata, che indica l'origine e la direzione, fornendo dati a circa _30 fps_. 

Lo sguardo stimato si trova all'interno della CA. 1,0-1,5 gradi nell'angolo visivo intorno alla destinazione effettiva. Poiché sono prevedibili lievi imprecisioni, effettua la pianificazione in modo da lasciare un po' di margine per questo valore limite minimo. Più avanti verranno forniti altri dettagli in merito. Per un accurato funzionamento del tracciamento oculare, ogni utente deve essere sottoposto a un'apposita calibrazione. 

![Dimensioni ottimali della destinazione a una distanza di 2 metri](images/gazetargeting-size-1000px.jpg)<br>
*Dimensioni di destinazione ottimali a distanza di 2 metri*
<br>
<br>
L' [API di rilevamento degli occhi](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) è accessibile tramite:' Windows. Perception. people. EyesPose '. 

## <a name="eye-gaze-design-guidelines"></a>Linee guida per la progettazione degli sguardi
Può essere difficile creare un'interazione che tragga vantaggio dalla possibilità di selezionare rapidamente la destinazione mediante lo sguardo fisso. In questa sezione vengono riepilogati i principali vantaggi e problemi da tenere in considerazione durante la progettazione dell'applicazione. 

### <a name="benefits-of-eye-gaze-input"></a>Vantaggi dell'input con sguardo a occhio
- **Puntamento ad alta velocità.** Il muscolo dell'occhio è il muscolo del nostro corpo che reagisce con maggiore rapidità. 

- **Sforzo limitato.** Non sono quasi necessari movimenti fisici. 

- **Natura implicita.** Spesso descritta dagli utenti come "lettura mentale", le informazioni sui movimenti degli occhi di un utente consentono al sistema di sapere quale destinazione prevede l'intervento dell'utente. 

- **Canale di input alternativo.** Eye-sguardi può offrire un potente input di supporto per l'input vocale e di mano che si basa su anni di esperienza degli utenti in base al coordinamento degli occhi.

- **Attenzione visiva.** Un altro vantaggio importante è la possibilità di dedurre ciò a cui un utente presta attenzione. Questo può essere utile in diverse aree applicative, da valutare in modo più efficace le diverse progettazioni per aiutare le interfacce utente più intelligenti e suggerimenti sociali avanzati per la comunicazione remota.

In breve, l'uso di Eye-sguardi come input offre un segnale contestuale rapido e facile. Questa operazione è particolarmente efficace se combinata con altri input, ad esempio input *vocale* e *manuale* , per confermare la finalità dell'utente.


### <a name="challenges-of-eye-gaze-as-an-input"></a>Problemi di Eye-sguardi come input
Grazie a un elevato consumo di energia, è molto responsabile.
Sebbene possa essere usato per creare esperienze utente soddisfacenti, è anche importante sapere che cosa non è adatto a tenere in considerazione questo aspetto per quanto riguarda questo aspetto. Di seguito sono illustrate alcune delle *problemi* da tenere in considerazione e come risolverle quando si lavora con l'input Eye-sguardi: 

- **Il controllo degli sguardi è "always on"** Nel momento in cui si aprono i coperchi degli occhi, gli occhi iniziano a fissando su elementi nell'ambiente. Reagire a ogni aspetto effettuato e rilasciare accidentalmente le azioni perché si è verificato un problema per troppo tempo, si otterrebbe un'esperienza insoddisfacente.
Questo è il motivo per cui è consigliabile combinare gli occhi con un *comando vocale*, un *gesto della mano*, un *clic del pulsante* o un'abitazione estesa per attivare la selezione di una destinazione.
Questa soluzione consente anche una modalità in cui l'utente può esaminarsi liberamente senza essere sopraffatto dall'attivazione involontaria di qualcosa. È opportuno tenere conto di tale problematica anche per progettare feedback visivi e audio qualora si guardi semplicemente una destinazione.
Non bombardare l'utente con effetti immediati e improvvisi o suoni al passaggio del puntatore. La sottigliezza è Key. Nella sezione relativa ai suggerimenti per la progettazione verranno illustrate alcune procedure consigliate su questo argomento.

- **Confronto tra osservazione e controllo** Si supponga di voler raddrizzare con precisione una fotografia sulla parete. Guardi pertanto i bordi e l'area circostante per verificare che l'immagine sia allineata correttamente. A questo punto, si supponga di voler usare il proprio sguardo come input per spostare l'immagine. L'esecuzione diventa veramente difficoltosa. Viene descritto il doppio ruolo di occhio quando è necessario sia per l'input che per il controllo. 

- **Uscita prima del clic:** Per le selezioni di destinazione rapide, la ricerca ha dimostrato che lo sguardo d'occhio di un utente può andare avanti prima di concludere un clic manuale (ad esempio, AirTap). Di conseguenza, è necessario prestare particolare attenzione alla sincronizzazione del segnale di sguardo rapido con un input di controllo più lento (ad esempio, Voice, Hands, controller).

- **Destinazioni di piccole dimensioni:** Si conosce la sensazione quando si tenta di leggere il testo che è troppo piccolo per leggere bene? Questa sensazione di limitazione degli sguardi può causare la disattivazione e la disattivazione, perché si tenta di riadattare gli occhi per concentrarsi meglio.
Si tratta di un sentimento che è possibile richiamare negli utenti quando si impone loro di selezionare destinazioni troppo piccole nell'applicazione usando la destinazione degli occhi.
Durante la progettazione, per creare un'esperienza piacevole e confortevole per gli utenti, è consigliabile definire destinazioni con un angolo visivo di almeno 2 gradi.

- **Spostamenti occhi** incompleti Gli occhi eseguono movimenti rapidi dalla fissa alla fissa. Se guardi i percorsi di analisi dei movimenti oculari registrati, noterai che risultano irregolari. Gli occhi si muovono velocemente e con salti spontanei rispetto al *puntamento con la testa* o ai *movimenti delle mani*.  

- **Affidabilità del tracciamento:** il tracciamento oculare può diventare leggermente meno affidabile con il mutare della luce, in quanto gli occhi devono adattarsi alle nuove condizioni di illuminazione.
Sebbene questo non abbia necessariamente effetto sulla progettazione dell'applicazione, in quanto l'accuratezza dovrebbe essere compresa nel limite di 2 °, potrebbe essere necessario che l'utente esegua un'altra taratura. 


## <a name="design-recommendations"></a>Suggerimenti per la progettazione
Di seguito è riportato un elenco di raccomandazioni di progettazione specifiche in base ai vantaggi e alle problemi descritti per l'input degli sguardi:

1. **Eye-sguardi! = Head-sguardi:**
    - **Considerare se i movimenti dell'occhio, rapidi ma non uniformi, sono adatti per l'attività di input da svolgere:** Anche se i nostri movimenti rapidi e incompleti sono molto veloci quando si selezionano rapidamente le destinazioni nel nostro campo di visualizzazione (FoV), è meno applicabile per le attività che richiedono traiettorie di input uniformi, ad esempio la creazione o l'inclusione di annotazioni. In questo caso, è preferibile usare il puntamento con la mano o con la testa.
  
    - **Evitare di allungare direttamente gli sguardi degli utenti (ad esempio, un dispositivo di scorrimento o un cursore).**
Nel caso di un cursore, questo può comportare un effetto di "cursore in fuga" a causa di lievi offset nel segnale oculare proiettato. Nel caso di un dispositivo di scorrimento, può entrare in conflitto con il doppio ruolo del controllo del dispositivo di scorrimento con gli occhi, ma anche per verificare se l'oggetto si trova nella posizione corretta. In breve, gli utenti possono diventare sopraffatti e distratti, soprattutto se il segnale è impreciso per tale utente. 
  
2. **Combinare gli sguardi con gli altri input:** L'integrazione di Eye Tracking con altri input, ad esempio movimenti della mano, comandi vocali o pressioni dei pulsanti, offre diversi vantaggi:
    - **Possibilità di consentire la libera osservazione:** Dato che il ruolo principale degli occhi è osservare l'ambiente, è importante che gli utenti siano in grado di spostarsi senza attivare commenti o azioni (visivi, uditivi e così via). 
    La combinazione di rilevamento degli occhi con un altro controllo di input consente una transizione uniforme tra le modalità di osservazione e controllo di input.
  
    - **Potente provider di contesto:** L'uso di informazioni su dove e cosa sta cercando l'utente durante l'esecuzione di un comando vocale o l'esecuzione di un gesto manuale consente di canalizzare senza interruzioni l'input nel campo della visualizzazione. Ad esempio:  "Metti questo là" per selezionare e posizionare in modo rapido e fluido un ologramma all'interno della scena semplicemente guardando una destinazione e il punto in cui si vuole collocarlo. 

    - **Necessità di sincronizzare input multimodali (problematica della sezione "Uscita prima del clic"):** La combinazione di movimenti di occhi rapidi con input aggiuntivi più complessi, ad esempio comandi di tipo Long Voice o movimenti della mano, presenta il rischio di continuare a osservare gli sguardi prima di terminare il comando di input aggiuntivo. Pertanto, se crei personalmente i controlli di input (ad esempio, movimenti della mano personalizzati), fai in modo di registrare l'inizio di tale input o la durata approssimativa in modo da poterlo mettere in correlazione con cosa aveva fissato in precedenza l'utente.
    
3. **Fornire feedback non invasivo per l'input mediante tracciamento oculare:** È utile per fornire commenti e suggerimenti quando viene esaminata una destinazione per indicare che il sistema funziona come previsto, ma deve essere mantenuto sottile. Questo può includere la fusione lenta, in e out, le evidenziazioni visive o eseguire altri comportamenti sottili della destinazione, ad esempio movimenti lenti, ad esempio un lieve aumento della destinazione, per indicare che il sistema ha rilevato correttamente che l'utente sta esaminando una destinazione senza interruzione inutilmente del flusso di lavoro corrente dell'utente. 

4. **Evitare di applicare movimenti degli occhi innaturali come input:** Non forzare gli utenti a eseguire movimenti oculari specifici (movimenti sguardi) per attivare azioni nell'applicazione.

5. **Tenere conto delle imprecisioni:** Vengono distinti due tipi di imprecisioni che sono evidenti per gli utenti: offset e jitter. Il modo più semplice per risolvere un offset consiste nel fornire destinazioni sufficientemente grandi per interagire con. Si consiglia di usare un angolo visivo maggiore di 2 ° come riferimento. Ad esempio, l'anteprima è di circa 2 ° nell'angolo visivo quando si allunga il ARM. Segui pertanto le indicazioni seguenti:
    - Non forzare gli utenti a selezionare destinazioni minuscole. La ricerca ha dimostrato che se le destinazioni sono sufficientemente grandi e che il sistema è progettato correttamente, gli utenti ne descrivono le interazioni come semplice e magico. Se le destinazioni diventano troppo piccole, gli utenti descrivono l'esperienza come stancante e frustrante.
   

## <a name="see-also"></a>Vedere anche
* [Puntamento con la testa e commit](gaze-and-commit.md)
* [Sguardo in DirectX](gaze-in-directx.md)
* [Eye-sguardi in Unity (Toolkit realtà mista)](https://aka.ms/mrtk-eyes)
* [Movimenti della mano](gestures.md)
* [Input vocale](voice-design.md)
* [Controller del movimento](motion-controllers.md)
* [Comodità](comfort.md)

---
title: Sotto controllo di rilevamento
description: Sotto controllo di rilevamento
author: sostel
ms.author: sostel
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: Rilevamento rossi, mista realtà, Input, sguardo sotto controllo
ms.openlocfilehash: 7298a34a946f86aaf789cfe44ad971169fc8ece3
ms.sourcegitcommit: 60060386305eabfac2758a2c861a43c36286b151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/31/2019
ms.locfileid: "66453696"
---
# <a name="eye-tracking-on-hololens-2"></a>Occhio rilevamento su HoloLens 2
HoloLens 2 consente un livello completamente nuovo di contesto e informazioni sulle risorse umane all'interno di esperienza olografica, offrendo agli sviluppatori la possibilità straordinaria con informazioni su ciò che siano esaminando gli utenti. Questa pagina offre una panoramica del modo in cui gli sviluppatori possono trarre vantaggio dal rilevamento di occhio per diversi casi d'uso e gli elementi da cercare durante la progettazione di interfacce utente basate su occhio-sguardo. 

## <a name="use-cases"></a>Casi di utilizzo
Occhio rilevamento consente alle applicazioni di rilevare dove sta guardando l'utente in tempo reale. In questa sezione descrive alcune delle possibili casi di utilizzo e le interazioni innovative che diventano possibili con sotto controllo di rilevamento nella realtà mista.
Prima di iniziare, in quanto segue si indicano che il [Toolkit di realtà mista](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html) più volte poiché fornisce alcuni esempi interessanti e potenti per l'uso del rilevamento sotto controllo, ad esempio destinazione supportata occhio semplificata e veloce le selezioni e automaticamente lo scorrimento di base in cui l'utente è simile al testo. 

### <a name="user-intent"></a>Intenzioni dell'utente    
Informazioni su dove un utente esamina forniscono una potente **contesto per gli altri input**, ad esempio voce, mani e controller.
Può essere utilizzato per diverse attività.
Ad esempio, la soluzione può variare da rapidamente e facilmente **targeting** tra la scena semplicemente esaminando un ologrammi e che indica che "select" (vedere anche [Head sguardo ed eseguire il commit](gaze-and-commit.md)) o pronunciando "put questo...", quindi ricerca di in cui si desidera posizionare l'ologrammi e scelgo "... There". Esempi per questo sono reperibile nel [Toolkit realtà mista - supportata sotto controllo la selezione di destinazione](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) e [Toolkit di realtà mista - supportata sotto controllo il posizionamento di destinazione](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Positioning.html).

Un altro esempio per le intenzioni dell'utente può includere l'uso di informazioni su cosa esaminano gli utenti per migliorare la collaborazione con gli agenti virtuali integrati e vntana interattiva. Ad esempio, gli agenti virtuali possono adattare le opzioni disponibili e il comportamento di base attualmente visualizzato il contenuto. 

### <a name="implicit-actions"></a>Azioni implicite
La categoria di azioni implicite è strettamente correlato al intenzione dell'utente.
L'idea è che gli elementi dell'interfaccia utente o vntana reagiscono in modo abbastanza instinctual potrebbe non ancora percepisca si interagisce con il sistema affatto, ma piuttosto che il sistema e l'utente siano sincronizzati. Ad esempio, è un esempio estremamente ha esito positivo **scorrimento automatico basati su occhio-sguardo**. L'idea è semplice: L'utente legge un testo e appena possibile continuare la lettura. Il testo gradualmente sposta verso l'alto mantenere gli utenti nel flusso di lettura. Un aspetto fondamentale è che la velocità di scorrimento si adatta per la velocità di lettura dell'utente.
Un altro esempio è **supportato sotto controllo di scorrimento e zoom** per cui l'utente può agiscono come entrare verso esattamente ciò che direste viene messa a fuoco in. Attivare lo zoom e controllando la velocità di zoom può essere controllate tramite vocali o passare input che è importante fornire la sensazione di controllo ed evitare di sovraccaricare l'utente (si discuterà queste linee guida di progettazione in dettaglio più avanti). Dopo lo zoom avanti, l'utente può quindi in modo uniforme seguire, ad esempio, il corso di una via e numero civico esplorazione nodi vicini alla propria semplicemente con loro sguardo sotto controllo.
Esempi di demo per questi tipi di interazioni possono essere individuati nel [Toolkit realtà mista - navigazione supportate occhio](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html) esempio.

Per casi di utilizzo di ulteriori _implicite azioni_ possono includere:
- **Notifiche intelligente:** Mai ottenere infastidita dal notifiche si estraggono in alto a destra in cui erano messa a fuoco? Prendendo in considerazione in cui un utente è attualmente prestando attenzione a, è possibile renderlo migliori! Visualizzare le notifiche di offset da cui attualmente sta guardando l'utente per limitare gli elementi di distrazione e automaticamente non prenderli in considerazione una volta terminata la lettura. 
- **Accurata vntana:** Ologrammi che reagiscono leggermente quando viene preso in esame. Questo può variare da leggermente brillanti elementi dell'interfaccia utente, un lenta blooming fiore al virtuale un avvio animali domestici riesaminare si o tenta di evitare lo sguardo occhio dopo un prolungato limita ad assistere passivamente. Questo può fornire un'idea interessante di connettività e la soddisfazione degli utenti all'app.

### <a name="attention-tracking"></a>Attenzione di rilevamento   
Informazioni su dove gli utenti guardano sono uno strumento estremamente potente per valutare l'usabilità di progettazioni e identificare eventuali problemi nei flussi di lavoro efficienti. A questo punto, occhio analitica e visualizzazione di rilevamento è già presenti una pratica comune nelle diverse aree dell'applicazione. Con 2 HoloLens, offriamo una nuova dimensione per questa conoscenza come vntana 3D può essere inserito in contesti reali e valutate insieme. Il [Toolkit di realtà mista](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html) fornisce esempi di base per la registrazione e il caricamento sotto controllo i dati di rilevamento e come visualizzarle.

Altre applicazioni in quest'area possono includere: 
-   **Visualizzazione di sguardo sotto controllo remoto:** Visualizzare ciò che i collaboratori remoti siano esaminando, ad esempio, verificare se le istruzioni vengono riconosciute correttamente e seguite.
-   **Ricerche di utente:** Attenzione rilevamento utilizzabile per esplorare il modo principiante o gli utenti esperti analizzare visivamente contenuto o il coordinamento di occhio mano per attività complesse (ad esempio, per l'analisi dei dati medici o l'utilizzo della macchina).
-   **Le simulazioni di training e il monitoraggio delle prestazioni:** Fare pratica e ottimizzare l'esecuzione di attività che identifica i colli di bottiglia in modo più efficace nel flusso di esecuzione.
-   **Progettare le valutazioni, annunci e la ricerca di mercato:** Sotto controllo di rilevamento è uno strumento comune per la ricerca di mercato per la valutazione di progettazioni del prodotto e il sito Web.

### <a name="additional-use-cases"></a>Casi d'uso aggiuntive
- **Modalità di gioco:** Mai desiderato di sono così sofisticate come? Qui è un'opportunità! Levitate vntana tempi a tali file. Risolvere i raggi laser dagli occhi. Trasforma nemici in stone o Bloccale! Usare le tue nuove idee x-ray per esplorare gli edifici. Il limite è la tua immaginazione.  

- **Avatar espressivi:** Rilevamento facilita gli avatar 3D più espressivi mediante live sotto controllo Data di rilevamento per animare gli occhi dell'avatar per indicare quali l'utente è attualmente esaminando sotto controllo. Aggiunge anche ulteriori espressività aggiungendo animoticon e lampeggia. 

- **Immissione di testo:** Sotto controllo di rilevamento è utilizzabile come un'alternativa interessante per l'immissione di testo di tutti i tentativi bassa soprattutto quando vocale o mani sono facili da usare. 


## <a name="eye-tracking-api"></a>API rilevamento sotto controllo
Prima di entrare nei dettagli sulle linee guida di progettazione specifiche per l'interazione visiva, si vuole scegliere brevemente le funzionalità che fornisce lo strumento di rilevamento di HoloLens 2 sotto controllo. Il [API di rilevamento occhio](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) è accessibile tramite: `Windows.Perception.People.EyesPose`. Fornisce un raggio di sguardo occhio single (sguardo origine e la direzione) per gli sviluppatori.
Lo strumento di rilevamento occhio offra dati con sui _30 FPS_.
Sguardo l'occhio stimato si trova all'interno di autorità di certificazione. 1.0-1,5 gradi in angolo visual tutto l'effettivo stato destinazione. Sono previste le imprecisioni leggere, è consigliabile pianificare per alcuni dei margini intorno a questo valore limite inferiore. È questo aspetto verrà esaminato più seguito. Per occhio per lavorare in modo accurato di rilevamento, ogni utente deve passare attraverso un occhio calibrazione utente di rilevamento. 

![Dimensioni di destinazione ottimale a distanza di 2 metri](images/gazetargeting-size-1000px.jpg)<br>
*Dimensioni di destinazione ottimale a distanza di 2 metri*


## <a name="eye-gaze-design-guidelines"></a>Linee guida di progettazione sguardo sotto controllo
Compilazione di un'interazione che sfrutta veloce come destinazione rossi mobile può risultare complessa. In questa sezione sono riepilogati i principali vantaggi e problematiche da prendere in considerazione quando si progetta l'app. 

### <a name="benefits-of-eye-gaze-input"></a>Vantaggi dell'input sguardo sotto controllo
- **Che punta ad alta velocità.** Il braccio occhio è il più rapido reacting braccio nel nostro corpo. 

- **Lavoro richiesto basso.** Attività spostamenti fisici sono necessari. 

- **Implicitness.** Spesso descritti dagli utenti come "presente durante la lettura", informazioni sui movimenti occhi dell'utente consentono al sistema di sapere che per interagire con i piani utente di destinazione. 

- **Canale di input alternativi.** Sguardo occhio possibile fornire un input supporto potente per la disponibilità e della voce input compilazione in anni di esperienza di utenti in base al loro coordinamento a forma di mano.

- **Visual attenzione.** Un altro vantaggio importante è la possibilità di dedurre che ciò che un utente è prestando attenzione a. Ciò consente in diverse aree dell'applicazione dalla più efficacemente la valutazione di diversi progetti in modo da consentire nelle interfacce utente più intelligenti e avanzata segnali basati su social network per le comunicazioni remote.

In breve, utilizzando sguardo sotto controllo, come un input potenzialmente offre un segnale contesto semplificato e veloce - risulta particolarmente utile in combinazione con altri input, ad esempio *voice* e *manuale* input confermare l'intenzione dell'utente.


### <a name="challenges-of-eye-gaze-as-an-input"></a>Difficoltà d'occhio estasiati come input
Con molta energia, è disponibile un numero elevato di responsabilità: Mentre sguardo sotto controllo può essere utilizzato per creare esperienze utente magici sente, ad esempio un nostro esperto, è anche importante sapere cosa non è valida in account per questo in modo appropriato. Di seguito, verranno illustrate alcune *sfide* per prendere in considerazione e come risolverli quando si lavora con input sguardo occhio: 

- **Lo sguardo occhio è "always on"** nel momento in cui si apre il coperchio sotto controllo, gli occhi avviare fixating operazioni nell'ambiente in uso. Reazione a ogni aspetto creazione ed emissione potenzialmente accidentalmente azioni perché sono stati esaminati svolgere un compito troppo a lungo comporta un'esperienza terribile!
È per questo motivo è consigliabile combinare sguardo sotto controllo con un *comandi vocali*, *movimento a mano*, *clic sul pulsante* o permanenza esteso per attivare la selezione di una destinazione.
Questa soluzione consente inoltre di una modalità in cui l'utente può liberamente cercare senza la sensazione eccessivamente elevata di involontariamente l'attivazione di un elemento. Questo problema deve anche essere tener conto quando si progettano i commenti e suggerimenti visivi e sonori osservando semplicemente una destinazione.
Non sovraccaricare l'utente con effetto immediato a comparsa o passare il mouse suoni. Importante sottolineare che è fondamentale. Verranno illustrate alcune procedure consigliate per questo ulteriormente di seguito quando si parla di suggerimenti per la progettazione.

- **Osservazione e controllo** si supponga che si desidera allineare in modo preciso una fotografia alla bacheca. Si esamina i bordi e dell'ambiente circostante per vedere se allineato correttamente. Si supponga ora di come si farebbe che quando allo stesso tempo si vuole usare lo sguardo occhio come input a spostare l'immagine. Difficile, vero? Questo descrive il ruolo double di sguardo sotto controllo quando è necessario sia per l'input e controllo. 

- **Uscire dalla prima di fare clic su:** Per le selezioni di destinazione rapide, la ricerca ha dimostrato che sguardo occhi di un utente può passare prima di concludere un clic manuale (ad esempio, un airtap). Di conseguenza, particolare attenzione alla sincronizzazione occhio veloce sguardo segnale con input di controllo più lente (ad esempio, vocali, le mani, controller).

- **Destinazioni di piccole dimensioni:** Si conosce la sensazione quando si prova a leggere il testo che è semplicemente un po' troppo piccolo per difficili da leggere? Il sentimento straining sugli occhi che causano è sentirsi stanco e altri in quanto si tenta di adattare agli occhi di messa a fuoco migliore?
Si tratta di una visione che è possibile richiamare gli utenti quando si forza la selezione di destinazioni troppo piccole nella tua app usando come destinazione rossi.
Per la progettazione, per creare un'esperienza piacevole e comoda per gli utenti, è consigliabile che le destinazioni devono essere almeno 2° in angolo visual, preferibilmente più grande.

- **Incomplete spostamenti sguardo occhio** occhi eseguono spostamenti rapido da fixation fixation. Se si esamina i percorsi di analisi di movimenti registrati sotto controllo, si noterà che il loro aspetto incomplete. Gli occhi spostare rapidamente e in spontanei, che si sposta alla *sguardo head* oppure *mano i movimenti*.  

- **Affidabilità di rilevamento:** Sotto controllo l'accuratezza di rilevamento potrebbe peggiorare qualche modifica light mano a mano d'occhio regolate per le nuove condizioni.
Anche se ciò non necessariamente influenzerà la progettazione di app, come la precisione deve essere entro il limite di 2° citato in precedenza. Significa che l'utente deve eseguire un'altra calibrazione. 


### <a name="design-recommendations"></a>Indicazioni sulla progettazione
Nell'esempio seguente, sono elencati i consigli di progettazione specifiche basate i vantaggi descritti e sfide per occhio estasiati input:

1. **Sguardo occhio! = sguardo Head:**
    - **Prendere in considerazione se rapidi ma occhio incomplete spostamenti adatta l'attività di input:** Sebbene i movimenti occhio veloci e incomplete sono un ottimo per selezionare le destinazioni rapidamente tra il campo visivo, è meno applicabile per le attività che richiedono smooth traiettorie inpue (ad esempio, per il disegno o reti circuizione annotazioni). In questo caso, manualmente o head puntando deve essere preferito.
  
    - **Evitare di associare un elemento direttamente a sguardo occhi dell'utente (ad esempio, un dispositivo di scorrimento o cursore).**
In caso di un cursore, questo può comportare l'effetto "cursore fuga" a causa di un leggero offset nel segnale sguardo previsto sotto controllo. In caso di un dispositivo di scorrimento, è in conflitto con il ruolo double di controllare il dispositivo di scorrimento con gli occhi pur volendo anche verificare se l'oggetto si trova nella posizione corretta. In breve, gli utenti potrebbero rapidamente sentirsi sovraccaricato e distratti, soprattutto se il segnale è impreciso per tale utente. 
  
2. **Combinare sguardo occhio con altri input:** L'integrazione di occhio tracciabilità con gli altri input, ad esempio movimenti della mano, i comandi vocali o pressione di pulsanti, ha diversi vantaggi:
    - **Consenti l'osservazione gratuitamente:** Dato che il ruolo principale di occhi consiste nell'osservare l'ambiente, è importante consentire agli utenti di cercare senza attivare qualsiasi (visual, uditivi...) commenti e suggerimenti o azioni. 
    La combinazione di ET con un altro controllo di input consente di transizione graduale tra le modalità di controllo di input e osservazione ET.
  
    - **Provider di contesto potenti:** Utilizzare le informazioni su dove sta guardando l'utente durante un comando vocale senza o eseguire un gesto della mano consente facilmente inoltrandoli l'input per il campo di visualizzazione. Ecco alcuni esempi: "Put che non esiste" in modo rapido e assicurano la massima selezionare e posizionare ologramma tra la scena osservando semplicemente una destinazione e di destinazione. 

    - **È necessario per la sincronizzazione multimodali input ("lasciare prima di fare clic su" problema):** La combinazione rapida occhio spostamenti più complessi input aggiuntivi (ad esempio, i comandi vocali lunghi o movimenti della mano) assuma il rischio che lo spostamento di con lo sguardo sotto controllo prima di completare il comando di input aggiuntivo. Di conseguenza, se si creano i propri controlli di input (ad esempio, movimenti della mano personalizzato), assicurarsi di inizio di questa durata input o approssimativa per correlare cosa era fixated su un utente in precedenza.
    
3. **Commenti e suggerimenti sottile per sotto controllo input di rilevamento:** È utile fornire commenti e suggerimenti, se una destinazione viene esaminata (per indicare che il sistema funzioni come previsto), ma deve essere mantenuta meno evidente. Ciò può includere la fusione lentamente in ingresso/uscita evidenziazioni visual o eseguire altri comportamenti di destinazione meno evidenti, ad esempio i movimenti lenta (ad esempio, leggermente aumentando la destinazione) per indicare che il sistema in modo corretto ha rilevato che l'utente sta guardando una destinazione, tuttavia, senza inutilmente interrompere il flusso di lavoro corrente dell'utente. 

4. **Evitare l'applicazione di movimenti occhio non naturali come input:** Non forzare agli utenti di eseguire spostamenti occhio specifico (movimenti sguardo) per attivare le azioni nell'app.

5. **Account per le imprecisioni:** Sono disponibili due tipi delle imprecisioni che sono evidenti per gli utenti: Offset e instabilità. Il modo più semplice per gli offset di indirizzo è fornire destinazioni sufficientemente grande per interagire con (> 2° in angolo visual – come riferimento: l'anteprima è circa 2° in angolo visual quando il ridimensionamento orizzontale di Azure Resource Manager (1)). Ciò comporta il materiale sussidiario seguente:
    - Non forzare la selezione di destinazioni di piccole dimensioni: Research ha dimostrato che se le destinazioni sono sufficientemente grandi e il sistema è progettato anche, gli utenti descrivono l'interazione come semplificata e magico scrivendo. Se le destinazioni diventano troppo piccole, gli utenti descrivono l'esperienza come difficoltoso e frustrazione.
   

## <a name="see-also"></a>Vedere anche
* [Puntamento con la testa e commit](gaze-and-commit.md)
* [Puntamento con la testa e sguardo fisso in DirectX](gaze-in-directx.md)
* [Sguardo occhio in Unity (Toolkit di realtà mista)](https://aka.ms/mrtk-eyes)
* [Movimenti della mano](gestures.md)
* [Input vocale](voice-design.md)
* [Controller del movimento](motion-controllers.md)
* [Comodità](comfort.md)

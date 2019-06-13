---
title: Tracciamento oculare
description: Tracciamento oculare
author: sostel
ms.author: sostel
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: tracciamento oculare, realtà mista, input, sguardo fisso
ms.openlocfilehash: 7298a34a946f86aaf789cfe44ad971169fc8ece3
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2019
ms.locfileid: "66453696"
---
# <a name="eye-tracking-on-hololens-2"></a>Tracciamento oculare in HoloLens 2
HoloLens 2 consente di raggiungere un livello totalmente nuovo di comprensione contestuale e umana all'interno dell'esperienza olografica, offrendo agli sviluppatori l'incredibile possibilità di usare le informazioni relative a cosa gli utenti stanno guardando. Questa pagina presenta una panoramica delle modalità con cui gli sviluppatori possono trarre vantaggio dal tracciamento oculare per vari casi di utilizzo e degli aspetti di cui preoccuparsi quando vengono progettate interfacce utente basate sullo sguardo fisso. 

## <a name="use-cases"></a>Casi di utilizzo
Il tracciamento oculare consente alle applicazioni di tenere traccia di dove guarda l'utente in tempo reale. Questa sezione illustra alcuni dei potenziali casi di utilizzo e le nuove interazioni che diventano possibili con il tracciamento oculare nella realtà mista.
Prima di iniziare, è importante notare che di seguito verrà menzionato diverse volte [Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html) perché offre diversi esempi interessanti ed efficaci di utilizzo del tracciamento oculare, ad esempio la selezione semplice e rapida della destinazione mediante lo sguardo fisso e lo scorrimento automatico del testo in base a dove guarda l'utente. 

### <a name="user-intent"></a>Intenzione dell'utente    
Le informazioni relative a dove guarda un utente forniscono un utile **contesto per altri input**, ad esempio la voce, le mani e i controller.
Tali informazioni possono essere usate per diverse attività.
Ad esempio, è possibile **selezionare la destinazione** in modo facile e rapido all'interno della scena semplicemente guardando un ologramma e dicendo "seleziona" (vedi anche [Puntamento con la testa e commit](gaze-and-commit.md)) oppure dire "metti questo...", guardarsi intorno fino al punto in cui si vuole posizionare l'ologramma e dire "...là". Per alcuni esempi, vedi [Mixed Reality Toolkit - Selezione della destinazione con lo sguardo](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) e [Mixed Reality Toolkit - Posizionamento della destinazione con lo sguardo](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Positioning.html).

Un altro esempio di intenzione dell'utente può essere rappresentato dall'uso delle informazioni relative a cosa guarda per aumentare il coinvolgimento con ologrammi interattivi e agenti virtuali incorporati. Ad esempio, gli agenti virtuali possono adattare le opzioni disponibili e il relativo comportamento in base al contenuto visto in quel momento. 

### <a name="implicit-actions"></a>Azioni implicite
La categoria delle azioni implicite è strettamente correlata all'intenzione dell'utente.
L'idea è che gli ologrammi o gli elementi dell'interfaccia utente reagiscano quasi in modo istintivo come se l'utente non stesse interagendo con il sistema, ma come se il sistema e l'utente fossero sincronizzati. Un esempio molto significativo di questo concetto è lo **scorrimento automatico mediante sguardo fisso**. L'idea è molto semplice: l'utente legge un testo e può tranquillamente continuare a leggere. Il testo scorre gradualmente verso l'alto in modo che l'utente possa proseguire nel flusso di lettura. Un aspetto fondamentale è rappresentato dal fatto che la velocità di scorrimento si adatta alla velocità di lettura dell'utente.
Un altro esempio è costituito da **zoom e panoramica con gli occhi**, grazie ai quali l'utente ha la sensazione di immergersi esattamente nel contenuto su cui si è concentrato. L'attivazione dello zoom e il controllo della velocità di zoom possono essere controllati mediante input vocale o della mano. Questo è importante per dare all'utente la sensazione di avere il controllo senza essere sopraffatto (queste linee guida per la progettazione verranno trattate in dettaglio più avanti). Dopo aver fatto zoom avanti, l'utente può ad esempio seguire fluidamente come si snoda una strada per esplorare il proprio quartiere usando semplicemente lo sguardo.
Alcune demo di esempio per questi tipi di interazioni sono disponibili in [Mixed Reality Toolkit - Navigazione con gli occhi](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html).

Seguono altri casi di utilizzo per le _azioni implicite_:
- **Notifiche intelligenti:** non vieni mai disturbato dalle notifiche che vengono visualizzate proprio nel punto su cui ti sei soffermato? Tenendo conto dell'elemento a cui l'utente sta prestando attenzione in un determinato momento, puoi evitare questo problema. Mostra le notifiche lontano dal punto che l'utente sta guardando per limitare le distrazioni e falle scomparire automaticamente al termine della lettura. 
- **Ologrammi reattivi:** crea ologrammi in grado di reagire non appena vengono guardati. Può trattarsi di elementi dell'interfaccia utente che brillano leggermente, di un fiore che sboccia lentamente e persino di un cucciolo virtuale che inizia a guardarti o che tenta di evitare il tuo sguardo dopo essere stato fissato a lungo. Questo può conferire all'app un interessante senso di relazione con l'utente e far provare soddisfazione all'utente stesso.

### <a name="attention-tracking"></a>Tracciamento dell'attenzione   
Le informazioni relative a dove guardano gli utenti sono un potente strumento per valutare l'utilizzabilità delle progettazioni e per identificare i problemi in flussi di lavoro efficienti. La visualizzazione e l'analisi del tracciamento oculare ormai sono una pratica comune in diversi settori di applicazione. Con HoloLens 2 viene aggiunta una nuova dimensione a tali informazioni, in quanto gli ologrammi 3D possono essere posizionati in contesti del mondo reale e valutati contemporaneamente. [Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html) offre esempi di base per la registrazione e il caricamento dei dati di tracciamento oculare e di come visualizzarli.

Di seguito sono riportate altre applicazioni in questo settore: 
-   **Visualizzazione in remoto mediante sguardo fisso:** è possibile visualizzare cosa stanno guardando i collaboratori remoti, ad esempio per assicurarsi che le istruzioni siano state comprese e seguite correttamente.
-   **Studi di ricerca sugli utenti:** è possibile usare il tracciamento dell'attenzione per verificare il modo in cui gli utenti nuovi e quelli esperti analizzano visivamente il contenuto oppure la loro coordinazione tra mano e occhio per le attività complesse, ad esempio per l'analisi di dati medici o durante l'utilizzo di macchinari.
-   **Simulazioni di formazione e monitoraggio delle prestazioni:** è possibile fare pratica e ottimizzare l'esecuzione delle attività identificando i colli di bottiglia in modo più efficace nel flusso di esecuzione.
-   **Valutazioni delle progettazioni e ricerche pubblicitarie e di marketing:** il tracciamento oculare è uno strumento comune per le ricerche di mercato allo scopo di valutare la progettazione dei siti Web e dei prodotti.

### <a name="additional-use-cases"></a>Altri casi di utilizzo
- **Giochi:** hai mai sognato di avere dei superpoteri? Ora hai questa opportunità. Puoi far levitare gli ologrammi guardandoli, lanciare raggi laser dagli occhi, trasformare i nemici in blocchi di pietra o di ghiaccio oppure usare la tua vista a raggi x per esplorare l'interno degli edifici. Insomma, con la tua immaginazione potrai superare ogni ostacolo.  

- **Avatar espressivi:** il tracciamento oculare è utile per rendere più espressivi gli avatar 3D. È infatti possibile usare i dati relativi al tracciamento dell'occhio umano per animare gli occhi dell'avatar e indicare quello che l'utente sta guardando in un determinato momento. Consente inoltre di aggiungere maggiore espressività mediante strizzate d'occhio e ammiccamenti. 

- **Immissione di testo:** il tracciamento oculare può essere usato come alternativa interessante per immettere testo senza sforzo, soprattutto quando non è comodo servirsi della voce o delle mani. 


## <a name="eye-tracking-api"></a>API di tracciamento oculare
Prima di illustrare in dettaglio le linee guida di progettazione specifiche per l'interazione mediante sguardo fisso, vengono descritte brevemente le funzionalità offerte dal tracciatore oculare HoloLens 2. L'[API di tracciamento oculare](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) è accessibile tramite `Windows.Perception.People.EyesPose` e fornisce agli sviluppatori un singolo raggio dello sguardo fisso (origine e direzione dello sguardo fisso).
Il tracciatore oculare fornisce dati a circa _30 fotogrammi al secondo_.
Lo sguardo fisso previsto è all'incirca entro un angolo visivo di 1 - 1,5 gradi attorno alla destinazione effettivamente guardata. Poiché sono prevedibili lievi imprecisioni, effettua la pianificazione in modo da lasciare un po' di margine per questo valore limite minimo. Più avanti verranno forniti altri dettagli in merito. Per un accurato funzionamento del tracciamento oculare, ogni utente deve essere sottoposto a un'apposita calibrazione. 

![Dimensioni ottimali della destinazione a una distanza di 2 metri](images/gazetargeting-size-1000px.jpg)<br>
*Dimensioni ottimali della destinazione a una distanza di 2 metri*


## <a name="eye-gaze-design-guidelines"></a>Linee guida di progettazione per l'uso dello sguardo fisso
Può essere difficile creare un'interazione che tragga vantaggio dalla possibilità di selezionare rapidamente la destinazione mediante lo sguardo fisso. In questa sezione vengono riepilogati i principali vantaggi e problematiche da considerare durante la progettazione dell'app. 

### <a name="benefits-of-eye-gaze-input"></a>Vantaggi dell'input mediante sguardo fisso
- **Puntamento ad alta velocità.** Il muscolo dell'occhio è il muscolo del nostro corpo che reagisce con maggiore rapidità. 

- **Sforzo limitato.** Non sono quasi necessari movimenti fisici. 

- **Natura implicita.** Le informazioni relative ai movimenti degli occhi di un utente consentono al sistema di sapere con quale destinazione l'utente intende interagire. Ecco perché gli utenti spesso descrivono questa situazione come "lettura del pensiero". 

- **Canale di input alternativo.** Lo sguardo fisso può essere un potente input a integrazione dell'input con la mano e la voce che si basa sugli anni di esperienza degli utenti in termini di coordinazione tra la mano e l'occhio.

- **Attenzione visiva.** Un altro vantaggio importante è la possibilità di dedurre su cosa l'utente stia concentrando l'attenzione. Ciò può essere utile in vari settori di applicazione, ad esempio per valutare con maggior efficacia progettazioni diverse, creare interfacce utente più intelligenti e cogliere i segnali sociali per migliorare la comunicazione remota.

In breve, l'uso dello sguardo fisso come input potenzialmente offre un segnale contestuale facile e veloce, soprattutto in combinazione con altri input come quello *vocale* e *manuale* a conferma dell'intenzione dell'utente.


### <a name="challenges-of-eye-gaze-as-an-input"></a>Problematiche correlate all'uso dello sguardo fisso come input
Insieme a tante potenti funzionalità, arrivano anche tante responsabilità: se è possibile usare lo sguardo fisso per creare esperienze magiche che fanno sentire l'utente come un supereroe, è altrettanto importante sapere per quali finalità non è adatto in modo da tenerne conto adeguatamente. Di seguito verranno illustrate alcune *problematiche* da considerare e come affrontarle quando si usa lo sguardo fisso come input: 

- **Lo sguardo è "sempre attivo":** nel momento in cui sollevi le palpebre, gli occhi iniziano a fissare gli elementi presenti nell'ambiente. Il fatto di reagire a ogni sguardo e di poter avviare azioni accidentalmente solo perché hai guardato un oggetto troppo a lungo può dare luogo a un'esperienza terribile.
Ecco perché è consigliabile combinare lo sguardo fisso con un *comando vocale*, un *movimento della mano*, un *clic su un pulsante* o un'attesa estesa per attivare la selezione di una destinazione.
Questa soluzione consente anche di implementare una modalità in cui l'utente può guardarsi liberamente attorno senza avere l'opprimente sensazione di poter attivare involontariamente funzioni non desiderate. È opportuno tenere conto di tale problematica anche per progettare feedback visivi e audio qualora si guardi semplicemente una destinazione.
Non bombardare l'utente con effetti immediati e improvvisi o suoni al passaggio del puntatore. La moderazione è la chiave vincente. Nella sezione relativa ai suggerimenti per la progettazione verranno illustrate alcune procedure consigliate su questo argomento.

- **Osservazione e controllo:** immagina di voler allineare con precisione una fotografia sul muro. Guardi pertanto i bordi e l'area circostante per verificare che l'immagine sia allineata correttamente. Ora immagina come potresti eseguire la stessa operazione e contemporaneamente usare lo sguardo fisso come input per spostare la foto. L'esecuzione diventa veramente difficoltosa. Questo fa comprendere la doppia funzione dello sguardo fisso quando è necessario sia per l'input sia per il controllo. 

- **Uscita prima del clic:** per selezioni rapide della destinazione, le ricerche svolte hanno dimostrato che lo sguardo di un utente può concentrarsi su altri elementi prima che un clic manuale (ad esempio, una simulazione del tocco) venga concluso. È pertanto necessario prestare particolare attenzione alla sincronizzazione del rapido segnale dello sguardo fisso con un input di controllo più lento come ad esempio la voce, le mani o un controller.

- **Destinazioni di piccole dimensioni:** ti è mai capitato di leggere un testo con un carattere troppo piccolo per essere letto comodamente? Hai mai provato quella spiacevole sensazione agli occhi che ti fa sentire esausto perché devi mettere continuamente a fuoco per vedere meglio?
Puoi provocare la stessa sensazione negli utenti se li forzi a selezionare con lo sguardo destinazioni troppo piccole nell'app.
Durante la progettazione, per creare un'esperienza piacevole e confortevole per gli utenti, è consigliabile definire destinazioni con un angolo visivo di almeno 2 gradi.

- **Movimenti degli occhi non uniformi:** i nostri occhi eseguono rapidi movimenti quando passano da un oggetto all'altro per fissarlo. Se guardi i percorsi di analisi dei movimenti oculari registrati, noterai che risultano irregolari. Gli occhi si muovono velocemente e con salti spontanei rispetto al *puntamento con la testa* o ai *movimenti delle mani*.  

- **Affidabilità del tracciamento:** il tracciamento oculare può diventare leggermente meno affidabile con il mutare della luce, in quanto gli occhi devono adattarsi alle nuove condizioni di illuminazione.
Questa situazione non incide necessariamente sulla progettazione dell'app in quanto l'accuratezza deve essere entro il limite sopra indicato di 2 gradi, ma può comportare l'esecuzione di un'altra calibrazione per l'utente. 


### <a name="design-recommendations"></a>Suggerimenti per la progettazione
Di seguito sono riportati alcuni suggerimenti specifici per la progettazione in base ai vantaggi e alle problematiche illustrati per l'uso dello sguardo fisso come input:

1. **Sguardo fisso o puntamento con la testa:**
    - **Considerare se i movimenti dell'occhio, rapidi ma non uniformi, sono adatti per l'attività di input da svolgere:** se i movimenti rapidi e irregolari dei nostri occhi sono utilissimi per selezionare velocemente le destinazioni nel campo visivo, sono meno applicabili per le attività che richiedono traiettorie di input uniformi, ad esempio per disegnare o cerchiare le annotazioni. In questo caso, è preferibile usare il puntamento con la mano o con la testa.
  
    - **Evitare di associare direttamente un elemento, quale un dispositivo di scorrimento o un cursore, allo sguardo dell'utente.**
Nel caso di un cursore, si può verificare il cosiddetto effetto del "cursore che scappa" a causa di lievi offset nel segnale dello sguardo proiettato. Nel caso di un dispositivo di scorrimento, si genera un conflitto dato dalla doppia necessità di controllare il dispositivo con gli occhi e allo stesso tempo di verificare se l'oggetto si trova nella posizione corretta. In pratica, gli utenti possono sentirsi rapidamente sopraffatti ed essere distratti, soprattutto se il segnale è impreciso. 
  
2. **Combinare lo sguardo fisso con altri input:** l'integrazione del tracciamento oculare con altri input, quali i movimenti delle mani, i comandi vocali o le pressioni dei pulsanti, offre diversi vantaggi:
    - **Possibilità di consentire la libera osservazione:** poiché la funzione principale dei nostri occhi è quella di osservare l'ambiente, è importante consentire agli utenti di guardarsi intorno senza attivare alcun feedback (visivo o audio) o azione. 
    Combinando il tracciamento oculare con un altro controllo di input, è possibile effettuare una transizione uniforme tra l'osservazione con tracciamento oculare e le modalità dei controlli di input.
  
    - **Potente provider di contesto:** usando le informazioni relative a dove l'utente sta guardando mentre pronuncia un comando vocale o esegue un movimento con la mano, è possibile incanalare agevolmente l'input nel campo visivo. Ecco alcuni esempi: "Metti questo là" per selezionare e posizionare in modo rapido e fluido un ologramma all'interno della scena semplicemente guardando una destinazione e il punto in cui si vuole collocarlo. 

    - **Necessità di sincronizzare input multimodali (problematica della sezione "Uscita prima del clic"):** combinando i rapidi movimenti oculari con altri input più complessi (come ad esempio movimenti delle mani o comandi vocali lunghi), si corre il rischio di spostare lo sguardo prima di completare il comando di input aggiuntivo. Pertanto, se crei personalmente i controlli di input (ad esempio, movimenti della mano personalizzati), fai in modo di registrare l'inizio di tale input o la durata approssimativa in modo da poterlo mettere in correlazione con cosa aveva fissato in precedenza l'utente.
    
3. **Fornire feedback non invasivo per l'input mediante tracciamento oculare:** è utile fornire un feedback se l'utente guarda una destinazione (per indicare che il sistema funziona come previsto), ma tale feedback non deve essere troppo evidente. Ad esempio, è possibile creare evidenziazioni visive che si fondono all'inizio o alla fine oppure ricorrere ad altri comportamenti poco invasivi per le destinazioni, tra cui movimenti rallentati (ad esempio, che ingrandiscono leggermente la destinazione) per indicare che il sistema ha rilevato correttamente che l'utente sta guardando una destinazione, senza tuttavia interrompere inutilmente il flusso di lavoro corrente dell'utente stesso. 

4. **Evitare di applicare movimenti degli occhi innaturali come input:** non forzare gli utenti a eseguire movimenti degli occhi (o dello sguardo) particolari per attivare azioni all'interno dell'app.

5. **Tenere conto delle imprecisioni:** agli utenti risultano evidenti due tipi di imprecisioni, ovvero offset e instabilità. Il modo più semplice per ovviare agli offset consiste nel fornire destinazioni abbastanza grandi da consentire l'interazione con esse (> 2 gradi di angolo visivo; come riferimento considera che il pollice ha un angolo visivo di circa 2 gradi se distendi il braccio (1)). Segui pertanto le indicazioni seguenti:
    - Non forzare gli utenti a selezionare destinazioni di piccole dimensioni. Le ricerche svolte hanno dimostrato che, se le destinazioni sono sufficientemente grandi (e il sistema è progettato in modo adeguato), gli utenti descrivono l'interazione come facile e magica. Se le destinazioni diventano troppo piccole, gli utenti descrivono l'esperienza come stancante e frustrante.
   

## <a name="see-also"></a>Vedi anche
* [Puntamento con la testa e commit](gaze-and-commit.md)
* [Puntamento con la testa e sguardo fisso in DirectX](gaze-in-directx.md)
* [Sguardo fisso in Unity (Mixed Reality Toolkit)](https://aka.ms/mrtk-eyes)
* [Movimenti della mano](gestures.md)
* [Input vocale](voice-design.md)
* [Controller del movimento](motion-controllers.md)
* [Comodità](comfort.md)

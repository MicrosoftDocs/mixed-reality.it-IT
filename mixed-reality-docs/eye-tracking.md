---
title: Tracciamento oculare
description: HoloLens 2 consente un nuovo livello di contesto e comprensione umana all'interno dell'esperienza olografica, offrendo agli sviluppatori la possibilità di usare le informazioni relative a ciò che l'utente sta esaminando.
author: sostel
ms.author: sostel
ms.date: 10/29/2019
ms.topic: article
keywords: Rilevamento degli occhi, realtà mista, input, sguardi oculari, calibrazione
ms.openlocfilehash: 1f3699330fb4879258693b6959724441bd838d98
ms.sourcegitcommit: 4d43a8f40e3132605cee9ece9229e67d985db645
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491148"
---
# <a name="eye-tracking-on-hololens-2"></a>Tracciamento oculare in HoloLens 2

![Demo sul rilevamento degli occhi in MRTK](images/mrtk_et_scenemenu.jpg)

HoloLens 2 consente un nuovo livello di contesto e comprensione umana all'interno dell'esperienza olografica, offrendo agli sviluppatori la possibilità di usare le informazioni relative a ciò che l'utente sta esaminando. Questa pagina illustra il modo in cui gli sviluppatori possono trarre vantaggio dal rilevamento degli sguardi per diversi casi d'uso, nonché da cosa cercare quando si progettano interazioni utente basate su sguardi visivi. 

L'API di rilevamento degli occhi è stata progettata con la riservatezza di un utente, evitando di passare informazioni identificabili, in particolare qualsiasi biometria. Per le applicazioni che supportano il rilevamento degli occhi, l'utente deve concedere l'autorizzazione dell'app per usare le informazioni di rilevamento degli occhi. 


### <a name="device-support"></a>Supporto di dispositivi
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
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
</tr>
<tr>
     <td>Sguardo attento</td>
     <td>❌</td>
     <td>✔️</td>
     <td>❌</td>
</tr>
</table>

<br>

## <a name="calibration"></a>Calibrazione 
Per il corretto funzionamento degli occhi, è necessario che ogni utente esamini la [calibrazione degli utenti](calibration.md) per cui l'utente deve esaminare un set di destinazioni olografiche. In questo modo, il dispositivo può modificare il sistema per un'esperienza di visualizzazione più comoda e di qualità superiore per l'utente e garantire il rilevamento accurato degli occhi allo stesso tempo. 

Il rilevamento degli occhi dovrebbe funzionare per la maggior parte degli utenti, ma in rari casi un utente potrebbe non essere in grado di calibrare correttamente. La calibrazione potrebbe non riuscire per vari motivi, tra cui: 
* L'utente ha rifiutato in precedenza il processo di calibrazione
* L'utente è stato distratto e non ha seguito gli obiettivi di calibrazione
* L'utente dispone di determinati tipi di obiettivi e occhiali di contatto che il sistema non supporta ancora 
* L'utente ha una certa fisiologia degli occhi, condizioni oculari o interventi chirurgici che il sistema non supporta ancora  
* Fattori esterni che inibiscono la verifica affidabile degli occhi, ad esempio le sbavature sulla visiera HoloLens o sugli occhiali, il sole intenso diretto e le occlusioni a causa dei capelli davanti agli occhi

Gli sviluppatori devono assicurarsi di fornire un supporto adeguato per gli utenti per i quali i dati di rilevamento degli occhi potrebbero non essere disponibili (che non sono in grado di eseguire correttamente la calibrazione). Sono disponibili raccomandazioni per le soluzioni di fallback nella sezione nella parte inferiore di questa pagina. 

Per altre informazioni sulla calibrazione e su come garantire un'esperienza uniforme, vedere la pagina relativa alla [calibrazione degli utenti per la verifica degli occhi](calibration.md) .

<br>

## <a name="available-eye-tracking-data"></a>Dati di rilevamento degli occhi disponibili
Prima di approfondire i casi d'uso specifici per l'input con sguardo a occhio, è opportuno evidenziare brevemente le funzionalità fornite dall'API HoloLens 2 [Eye Tracking](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose) . Gli sviluppatori possono accedere a un singolo raggio d'occhio (origine e direzione dello sguardo) a circa _30 fps (30 Hz)_ .
Per informazioni più dettagliate su come accedere ai dati di rilevamento degli occhi, fare riferimento alle guide per gli sviluppatori per l'uso [degli sguardi in DirectX](gaze-in-directx.md) e [degli sguardi in Unity](https://aka.ms/mrtk-eyes).

Lo sguardo stimato è approssimativamente entro 1,5 gradi nell'angolo visivo intorno alla destinazione effettiva (vedere la figura seguente). Poiché sono previste piccole imprecisioni, gli sviluppatori devono pianificare un certo margine attorno a questo valore con associazione inferiore (ad esempio, 2.0-3.0 gradi possono comportare un'esperienza molto più comoda). Di seguito viene illustrato come gestire la selezione di destinazioni di piccole dimensioni in modo più dettagliato. Per un accurato funzionamento del tracciamento oculare, ogni utente deve essere sottoposto a un'apposita calibrazione. 

![Dimensioni ottimali della destinazione a una distanza di 2 metri](images/gazetargeting-size-1000px.jpg)<br>
*Dimensioni di destinazione ottimali a distanza di 2 metri*

<br>

## <a name="use-cases"></a>Casi di utilizzo
Il tracciamento oculare consente alle applicazioni di tenere traccia di dove guarda l'utente in tempo reale. I casi d'uso seguenti descrivono alcune interazioni possibili con la verifica degli occhi su HoloLens 2 in realtà mista.
Si noti che questi casi d'uso non fanno ancora parte dell'esperienza della shell olografica (ad esempio, l'interfaccia visualizzata quando si avvia HoloLens 2).
È possibile provare alcuni di essi nel [Toolkit di realtà mista](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html), che fornisce diversi esempi interessanti e avanzati per l'uso degli occhi, ad esempio selezioni mirate, rapide e senza problemi, nonché lo scorrimento automatico del testo in base alle informazioni esaminate dall'utente. 

### <a name="user-intent"></a>Intenzione dell'utente    
Le informazioni su dove e cosa esamina un utente forniscono un **contesto potente per altri input**, ad esempio Voice, Hands e Controllers.
Tali informazioni possono essere usate per diverse attività.
Questo, ad esempio, può variare da un punto di vista rapido e semplice a quello della scena semplicemente osservando un ologramma e pronunciando *"Select"* (vedere anche lo [sguardo e il commit](gaze-and-commit.md)) o *"put this..."* , quindi esaminando il punto in cui l'utente desidera inserire l'ologramma e indicare *"... "* . Per alcuni esempi, vedi [Mixed Reality Toolkit - Selezione della destinazione con lo sguardo](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) e [Mixed Reality Toolkit - Posizionamento della destinazione con lo sguardo](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Positioning.html).

Inoltre, un esempio per finalità utente potrebbe includere l'uso di informazioni sugli elementi esaminati dagli utenti per migliorare l'engagement con agenti virtuali incorporati e ologrammi interattivi. Ad esempio, gli agenti virtuali potrebbero adattare le opzioni disponibili e il relativo comportamento, in base al contenuto attualmente visualizzato. 

### <a name="implicit-actions"></a>Azioni implicite
La categoria delle azioni implicite è strettamente correlata all'intenzione dell'utente.
L'idea è che gli ologrammi o gli elementi dell'interfaccia utente reagiscono in maniera istintiva, che potrebbe non sembrare che l'utente stia interagendo con il sistema, ma piuttosto che il sistema e l'utente siano sincronizzati. Un esempio è lo **scorrimento automatico basato sull'occhio** , in cui l'utente può leggere un testo lungo che inizia automaticamente a scorrere dopo che l'utente si trova nella parte inferiore della casella di testo per impedire all'utente di leggere il flusso, senza sollevare il dito.  
Un aspetto fondamentale è che la velocità di scorrimento si adatta alla velocità di lettura dell'utente.
Un altro esempio è **lo zoom e la panoramica supportati dagli occhi,** in cui l'utente può avere la tendenza a concentrarsi esattamente su quello che si sta concentrando. L'attivazione e il controllo della velocità di zoom possono essere controllati da input voce o mano, che è importante per fornire all'utente il controllo, evitando così la sovraccarica. Di seguito vengono descritte in dettaglio le considerazioni di progettazione. Una volta eseguito lo zoom avanti, l'utente può seguire in modo semplice, ad esempio, il corso di una strada per esplorare il suo quartiere utilizzando semplicemente il proprio sguardo.
Alcune demo di esempio per questi tipi di interazioni sono disponibili in [Mixed Reality Toolkit - Navigazione con gli occhi](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html).

Seguono altri casi di utilizzo per le _azioni implicite_:
- **Notifiche intelligenti:** Ci si annoia a ricevere le notifiche che si trovano nel punto in cui si sta cercando? Prendendo in considerazione le informazioni a cui un utente presta attenzione, è possibile migliorare questa esperienza compensando le notifiche da cui l'utente sta attualmente guardando. Questo limita le distrazioni e le chiude automaticamente dopo che l'utente ha terminato la lettura. 
- **Ologrammi attenti:** Olografici che reagiscono in maniera impercettibile quando si osservano. Questo può variare da elementi dell'interfaccia utente leggermente luminosi, un fiore lentamente fiorito a un cane virtuale che inizia a esaminare l'utente e scuotendo la coda. Questa interazione potrebbe offrire un'interessante sensazione di connettività e soddisfazione nell'applicazione.

### <a name="attention-tracking"></a>Tracciamento dell'attenzione   
Le informazioni su dove o quali utenti osservano possono essere uno strumento estremamente potente. Può aiutare a valutare l'usabilità delle progettazioni e identificare i problemi nei flussi di lavoro per renderli più efficienti.
La visualizzazione e l'analisi dei tracciati degli occhi sono una pratica comune in varie aree di applicazione. Con HoloLens 2, viene fornita una nuova dimensione a questa comprensione perché gli ologrammi 3D possono essere inseriti in contesti reali e valutati di conseguenza. Il [Toolkit di realtà mista](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html) fornisce esempi di base per la registrazione e il caricamento dei dati di rilevamento degli occhi e come visualizzarli.
Microsoft è dedicata a facilitare l'innovazione garantendo al tempo stesso agli utenti un'esperienza informativa e trasparente con la modalità di utilizzo delle informazioni di rilevamento degli occhi.  Microsoft collaborerà con gli sviluppatori e i team UX per fornire indicazioni a terze parti per garantire che le esperienze siano centrate sull'utente.  


Di seguito sono riportate altre applicazioni in questo settore: 
-   **Visualizzazione sguardo remoto:** Visualizzazioni remote degli sguardi: è possibile visualizzare quali collaboratori remoti stanno esaminando, per poter fornire feedback immediato e semplificare l'elaborazione di informazioni più accurate.
-   **Studi di ricerca per gli utenti:** Il monitoraggio dell'attenzione può aiutare i ricercatori a ottenere informazioni approfondite sul modo in cui gli utenti percepiscono e si impegnano nell'ambiente naturale, senza interferire, per progettare interazioni tra computer umani più istintivi. Il rilevamento degli occhi può fornire informazioni non direttamente articolate dai partecipanti allo studio, che altrimenti potrebbero essere facilmente perse dal ricercatore. 
-   **Training e monitoraggio delle prestazioni:** Pratica e ottimizza l'esecuzione delle attività identificando i colli di bottiglia in modo più efficace nel flusso di esecuzione. Il monitoraggio degli occhi può fornire informazioni naturali, in tempo reale e obiettive per contribuire al miglioramento della formazione, della produttività e della sicurezza nell'area di lavoro. 
-   **Valutazioni di progettazione, marketing e ricerca di utenti:** Il rilevamento degli occhi consente alle aziende commerciali di eseguire studi di marketing e consumer in ambienti reali o di analizzare ciò che acquisisce l'attenzione di un utente per migliorare la progettazione del prodotto o dello spazio. 

### <a name="additional-use-cases"></a>Altri casi di utilizzo
- **Giochi:** Hai mai voluto avere superpotenza? Ora hai questa opportunità. È possibile levitare gli ologrammi guardandoli. Spara i raggi laser dagli occhi: Provalo in [RoboRaid per HoloLens 2](https://www.microsoft.com/p/roboraid/9nblggh5fv3j).
Trasformare i nemici in pietra o bloccarli. oppure usare la tua vista a raggi x per esplorare l'interno degli edifici. Insomma, con la tua immaginazione potrai superare ogni ostacolo.
Prestare attenzione a non sovraccaricare l'utente. per saperne di più, consultare le [linee guida per la progettazione degli input basati su sguardi](eye-gaze-interaction.md).

- **Avatar espressivi:** Il rilevamento degli occhi negli Avatar 3D più espressivi usa i dati di tracking degli occhi dinamici per animare gli occhi dell'avatar che indicano l'aspetto dell'utente. 

- **Voce di testo:** Il rilevamento degli occhi può essere usato come alternativa per la voce di testo a basso sforzo, soprattutto quando il discorso o le mani non sono convenienti da usare. 

<br>

## <a name="using-eye-gaze-for-interaction"></a>Uso di Eye-sguardi per l'interazione
La creazione di un'interazione che sfrutta la scelta rapida per gli occhi in rapida evoluzione può risultare complessa.
Da un lato, gli occhi si muovono così velocemente che è necessario prestare attenzione a come usare l'input occhio, perché in caso contrario gli utenti potrebbero riscontrare un'esperienza travolgente o distrazione. D'altra parte, è anche possibile creare esperienze realmente magiche che stimolano gli utenti. Per aiutarti, Guarda la panoramica dei vantaggi principali, delle sfida e dei consigli di progettazione per gli occhi mirati [all'interazione](eye-gaze-interaction.md). 
 
## <a name="fallback-solutions-when-eye-tracking-is-not-available"></a>Soluzioni di fallback quando la verifica degli occhi non è disponibile

In rari casi, i dati di rilevamento degli occhi potrebbero non essere disponibili.
Questo problema può essere dovuto a diversi motivi per i quali più comuni sono elencati di seguito:
* Il sistema non è riuscito a [calibrare l'utente](calibration.md).
* La [calibrazione](calibration.md)è stata ignorata dall'utente.   
* L'utente è calibrato, ma ha deciso di non concedere all'app l'autorizzazione per l'uso dei dati di rilevamento degli occhi.    
* L'utente ha occhiali univoci o una condizione oculare che il sistema non supporta ancora.    
* Fattori esterni che inibiscono il monitoraggio degli occhi affidabili, ad esempio le sbavature sulla visiera HoloLens o sugli occhiali, il sole intenso diretto e le occlusioni a causa dei capelli davanti agli occhi.   

Di conseguenza, gli sviluppatori devono assicurarsi che sia disponibile un supporto di fallback appropriato per questi utenti. Nella pagina relativa al [rilevamento degli occhi nella pagina DirectX](gaze-in-directx.md#fallback-when-eye-tracking-is-not-available) vengono illustrate le API necessarie per rilevare se i dati di rilevamento degli occhi sono disponibili. 

Anche se alcuni utenti hanno deciso consapevolmente di revocare l'accesso ai dati di rilevamento degli occhi e sono OK con il compromesso di un'esperienza utente inferiore alla privacy di non fornire l'accesso ai dati di rilevamento degli occhi, in alcuni casi potrebbe non essere intenzionale.  
Di conseguenza, se l'app usa la funzionalità di rilevamento degli occhi e si tratta di una parte importante dell'esperienza, è consigliabile comunicarla chiaramente all'utente.     
Si consiglia di informare l'utente sul motivo per cui la verifica degli occhi è cruciale per l'applicazione (forse anche elencando alcune funzionalità avanzate) per sperimentare il potenziale completo dell'applicazione, può aiutare gli utenti a comprendere meglio ciò che stanno rinunciando.   
Consente all'utente di identificare il motivo per cui la verifica degli occhi potrebbe non funzionare (in base ai controlli precedenti) e offre alcuni suggerimenti per risolvere rapidamente i potenziali problemi.     
Se, ad esempio, è possibile rilevare che il sistema supporta la verifica degli occhi, l'utente è calibrato e ha anche dato le autorizzazioni, ma non vengono ricevuti dati di rilevamento degli occhi, questo può puntare ad altri problemi, ad esempio le sbavature o gli occhi bloccati.    
Si noti che esistono casi rari di utenti per i quali la verifica degli occhi potrebbe non funzionare.   
Quindi, è opportuno rispettarlo consentendo di ignorare o addirittura disabilitare i promemoria per abilitare il rilevamento degli occhi nell'app.

### <a name="fallback-for-apps-using-eye-gaze-as-a-primary-input-pointer"></a>Fallback per le app che usano Eye-sguardi come puntatore di input primario
Se l'app usa Eye-sguardi come input del puntatore per selezionare rapidamente gli ologrammi nella scena, ma i dati di rilevamento degli occhi non sono disponibili, è consigliabile eseguire il fallback a Head-sguardi e iniziare a visualizzare il cursore Head-sguardi. È consigliabile usare un timeout (ad esempio, da 500 a 1500 ms) per determinare se passare o meno. Questa azione impedisce la visualizzazione dei cursori ogni volta che è possibile che il sistema perda brevemente il monitoraggio a causa di movimenti rapidi degli occhi o occhiolini. Per gli sviluppatori di Unity, il fallback automatico a Head-sguardi è già gestito nel Toolkit per la realtà mista. Se si è uno sviluppatore di DirectX, è necessario gestire manualmente questo switch.

### <a name="fallback-for-other-eye-tracking-specific-applications"></a>Fallback per altre applicazioni specifiche per il rilevamento degli occhi
L'app può usare gli sguardi in modo univoco e personalizzata in modo specifico. Ad esempio, animando gli occhi di un avatar o per attirare l'attenzione su Heatmaps che si basa su informazioni precise sull'attenzione visiva. In questo caso, non esiste alcun fallback chiaro. Se il rilevamento degli occhi non è disponibile, è possibile che sia sufficiente disabilitare queste funzionalità.
Anche in questo caso, si consiglia di comunicare chiaramente questo problema all'utente che potrebbe non essere a conoscenza del funzionamento della funzionalità.

<br>

In questa pagina è stata auspicata una panoramica approfondita per iniziare a comprendere il ruolo del rilevamento degli occhi e l'input degli sguardi per HoloLens 2. Per iniziare lo sviluppo, consultare le informazioni sul ruolo di [sguardo attento per interagire con gli ologrammi](eye-gaze-interaction.md), osservare lo sguardo [in Unity](https://aka.ms/mrtk-eyes) e guardare gli [occhi in DirectX](gaze-in-directx.md).


## <a name="see-also"></a>Vedi anche
* [Calibrazione](calibration.md)
* [Comodità](comfort.md)
* [Interazione basata su sguardo fisso](eye-gaze-interaction.md)
* [Eye-sguardi in DirectX](gaze-in-directx.md)
* [Eye-sguardi in Unity (Toolkit realtà mista)](https://aka.ms/mrtk-eyes)
* [Sguardo fisso e commit](gaze-and-commit.md)
* [Input vocale](voice-design.md)



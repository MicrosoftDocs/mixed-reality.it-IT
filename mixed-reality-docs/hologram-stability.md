---
title: Stabilità ologrammi
description: HoloLens vengono stabilite automaticamente vntana, ma esistono gli sviluppatori possono intraprendere per migliorare ulteriormente la stabilità di ologramma.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: ologrammi, stabilità, hololens
ms.openlocfilehash: 9b0227102934650d5640a4ac1c4d6f59ecd8e6dd
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600772"
---
# <a name="hologram-stability"></a>Stabilità ologrammi

Per ottenere vntana stabile, HoloLens dispone di una pipeline di stabilizzazione di immagine incorporata. La pipeline di stabilizzazione funziona automaticamente in background, in modo che non sono previsti passaggi aggiuntivi necessari per abilitarlo. Tuttavia, gli sviluppatori devono esercitare tecniche che consentono di migliorare la stabilità di ologramma ed evitare scenari che riducono la stabilità.

## <a name="hologram-quality-terminology"></a>Terminologia di qualità ologrammi

La qualità di vntana è il risultato dell'ambiente valido e lo sviluppo di app valido. Le app che ha una costante 60 fotogrammi al secondo in un ambiente in cui HoloLens può rilevare l'ambiente circostante garantirà che l'ologrammi e il sistema di coordinate corrispondente siano sincronizzati. Dal punto di vista dell'utente, vntana che deve essere fisso non può essere spostata rispetto all'ambiente.

Quando si rilascia ambiente, frequenze di bassa o non coerenti per il rendering, o altri problemi dell'app visualizzati, la terminologia seguente è utile per identificare il problema.
* **Precisione.** Una volta l'ologrammi bloccato world è inserito nel mondo reale, deve rimanere in cui è stato posizionato, rispetto all'ambiente circostante, indipendentemente dal suo movimento utente e le modifiche dell'ambiente di piccole dimensioni e tipo sparse. Se in un secondo momento, ologramma viene visualizzato in un percorso imprevisto, è un' *accuratezza* problema. Scenari di questo tipo possono verificarsi se due distinte chat apparire identiche.
* **Jitter.** Gli utenti osservano questa come ad alta frequenza agitando di ologramma. Questa situazione può verificarsi quando si riduce di rilevamento dell'ambiente. Per gli utenti, la soluzione è in esecuzione [sensore ottimizzazione](sensor-tuning.md).
* **Sussulto.** Le frequenze di rendering bassa comportare lo spostamento non uniforme e immagini double di vntana. Ciò è particolarmente evidente in vntana con movimento. Gli sviluppatori devono mantenere un [costante 60 FPS](hologram-stability.md#frame-rate).
* **Drift.** Gli utenti vedono questa quando ologrammi sembra allontanano in cui è stata inizialmente posizionata. Ciò si verifica quando venga posizionati a portata di mano vntana da [Anchor spaziali](spatial-anchors.md), in particolare nelle parti dell'ambiente che non sono state mappate completamente. Creazione vntana vicino Anchor spaziale riduce la probabilità di deviazione.
* **Jumpiness.** Quando un ologrammi "POP" o "passa" dalla relativa posizione occasionalmente. Ciò può verificarsi come rilevamento consente di regolare vntana adattandola aggiornato comprensione dell'ambiente.
* **Swim.** Quando un ologrammi sembra sway corrispondente per il movimento della testina dell'utente. Ciò si verifica quando vntana non è attivati i [piano di stabilizzazione](hologram-stability.md#stabilization-plane), e se non è di HoloLens [calibrati](calibration.md) per l'utente corrente. L'utente può rieseguire la [calibrazione](calibration.md) dell'applicazione per risolvere il problema. Gli sviluppatori possono aggiornare il piano di stabilizzazione per migliorare ulteriormente la stabilità.
* **La separazione dei colori.** Le visualizzazioni in HoloLens sono una visualizzazione sequenziale a colori, cui flash canali di colore rosso-verde-blu-verde a 60Hz (colore singolo vengono visualizzati i campi Hz 240). Ogni volta che un utente tiene traccia del movimento ologramma con gli occhi il propria, tali ologrammi bordo iniziale e finale separare i colori che lo costituiscono, producendo un effetto con arcobaleno. Il livello di separazione è dipendente dalla velocità di ologramma. In alcuni casi rari, lo spostamento di quelle head rapidamente mentre si esaminano ologramma fermo può anche comportare un effetto con arcobaleno. Questa operazione viene definita  *[la separazione dei colori](hologram-stability.md#color-separation)*.

## <a name="frame-rate"></a>Frequenza dei fotogrammi

Frequenza dei fotogrammi è il primo pilastro della stabilità di ologramma. Per vntana visualizzazione stabile del mondo, ogni immagine presentati all'utente deve disporre di vntana disegnata nel punto corretto. Consente di visualizzare in caso di aggiornamento di HoloLens 240 volte al secondo, con quattro campi di colore distinto per ogni appena eseguito il rendering image, determinando un'esperienza utente di 60 FPS (fotogrammi al secondo). Per fornire la migliore esperienza possibile, gli sviluppatori di applicazioni devono mantenere 60 FPS, si traduce in modo coerente che fornisce una nuova immagine del sistema operativo ogni 16 millisecondi.

**60 FPS** per disegnare vntana l'aspetto rimangono nel mondo reale, HoloLens deve eseguire il rendering di immagini dalla posizione dell'utente. Poiché il rendering delle immagini richiede tempo, HoloLens consente di stimare in cui saranno head di un utente quando le immagini vengono visualizzate nelle visualizzazioni. Questo algoritmo di previsione è un'approssimazione. HoloLens disponga di hardware che regola l'immagine di rendering per conto di questa discrepanza tra la posizione di head stimata e l'effettiva posizione head. In questo modo si vede l'immagine utente vengono visualizzati come se ne è stato eseguito il rendering dall'indirizzo corretto, l'aspetto vntana stabile. L'immagine di funzionamento degli aggiornamenti meglio con piccole modifiche e non riesce a correggere completamente determinate operazioni nell'immagine sottoposta a rendering come movimento parallasse.

Per il rendering a 60 FPS, si esegue tre operazioni per rendere stabile vntana:
1. Riducendo al minimo la latenza complessiva tra il rendering di un'immagine e tale immagine viene visualizzata all'utente. In un modulo di gestione con un thread di gioco e un thread di rendering in esecuzione in lockstep, in esecuzione 30 fps può aggiungere 33.3ms della latenza aggiuntiva. Riducendo la latenza, ciò riduce l'errore di previsione e aumenta la stabilità di ologramma.
2. Semplificando in modo che ogni immagine di raggiungere gli occhi dell'utente hanno una quantità di latenza coerente. Se si esegue il rendering 30 fps, la visualizzazione vengono ancora visualizzate immagini 60 fps. Ciò significa che la stessa immagine verrà visualizzata due volte in una riga. Il secondo frame avrà 16.6ms latenza più lungo del primo frame e sarà necessario risolvere una quantità più pronuncia di errore. Questa incoerenza in termini di grandezza di errore può causare indesiderato sussulto 60hz.
3. Riduce l'aspetto di sussulto, che è caratterizzata da movimento non uniforme e immagini double. Judder movimento ologrammi più veloce e rendering più bassi tassi di sono associati più evidenti. Pertanto, l'impegno per mantenere 60 FPS affatto volte consente di evitare sussulto per un determinato ologrammi lo spostamento.

**Coerenza di frequenza dei fotogrammi** coerenza frequenza fotogrammi è tanto importante quanto un elevata fotogrammi al secondo. In alcuni casi eliminato frame sono inevitabili per tutte le applicazioni ricche di contenuti e di HoloLens implementa alcuni algoritmi complessi per il ripristino da anomalie occasionali. Tuttavia, una frequenza dei fotogrammi costantemente dinamico è molto più evidente a un utente rispetto all'esecuzione in modo coerente in base alle tariffe frame inferiore. Ad esempio, un'applicazione che esegue il rendering in modo uniforme per 5 frame (60 FPS per la durata dei 5 frame) e quindi Elimina tutti gli altri frame per i successivi 10 frame (30 FPS per la durata di tali 10 frame) verranno visualizzati più instabili rispetto a un'applicazione coerente esegue il rendering 30 fps.

Si noti, il sistema operativo limiterà le applicazioni fino a 30 FPS quando [acquisizione di realtà mista](mixed-reality-capture.md) è in esecuzione.

**Analisi delle prestazioni** esistono numerosi strumenti che può essere utilizzato per valutare la frequenza dei fotogrammi dell'applicazione, ad esempio:
* GPUView
* Debugger grafica di Visual Studio
* Profiler incorporati in 3D motori, ad esempio Unity

## <a name="hologram-render-distances"></a>Distanze di rendering ologrammi

>[!VIDEO https://www.youtube.com/embed/-606oZKLa_s]

Risorse umane visual system si integra più segnali dipendenti dalla distanza quando fixates e si concentra su un oggetto.
* [Ristorazione](https://en.wikipedia.org/wiki/Accommodation_%28eye%29) -lo stato attivo di un occhio singoli.
* [Convergenza](https://en.wikipedia.org/wiki/Convergence_(eye)) - occhi lo spostamento verso l'interno o esterno per allineare al centro in un oggetto.
* [Visione artificiale binoculare](https://en.wikipedia.org/wiki/Stereopsis) -disparità tra le immagini di sinistra e destra eye che dipende a distanza di un oggetto dal punto di fixation.
* Ombreggiatura, dimensione di angular relativi e altri segnali monoculare (singolo rossi).

La convergenza e ristorazione sono univoci poiché sono molto della retina segnali correlati al modo in cui gli occhi modifiche per avvertire gli oggetti alle distanze diverse. Nella visualizzazione naturale, la convergenza e ristorazione sono collegate. Quando gli occhi visualizzare qualcosa vicino (ad esempio, il naso) gli occhi multipiattaforma e adattare a un punto vicino. Quando gli occhi visualizzano un elemento all'infinito che gli occhi diventano paralleli e l'occhio del lettore alcune variazioni verso l'infinito. Gli utenti che portano HoloLens permetteranno sempre a m 2.0 per mantenere un'immagine chiara in quanto consente di visualizzare il HoloLens sono fissati a una distanza ottica circa 2.0m lontano dall'utente. Controllo App per gli sviluppatori in cui eseguire la convergenza occhi degli utenti inserendo il contenuto e vntana profondità diversi. Quando gli utenti di gestire e convergono in distanze diverse, il collegamento naturale tra i due indicatori vengono interrotte e questo può causare disturbo visual o fatica, in particolar modo quando la grandezza del conflitto di grandi dimensioni. Disturbare dal conflitto vergence facilitazione può essere evitato o ridotta a icona, mantenendo il contenuto che gli utenti convergono in più vicino 2.0 m possibile (ad esempio in una scena con molta profondità posizionare le aree di interesse vicino 2.0 m quando possibile). Quando non è possibile inserire contenuto quasi disturbo m 2.0 dal conflitto vergence alloggio è maggiore quando l'utente del estasiati entrata e in uscita tra le distanze diverse. In altre parole, è molto più a proprio agio esaminare fermo ologramma che rimane 50cm distanza rispetto al esaminare ologramma 50cm da subito che si sposta verso e lontano da te nel corso del tempo.

L'inserimento di contenuto m 2.0 è vantaggioso anche perché le due visualizzazioni sono progettate per completamente si sovrappongono a distanza. Per immagini erano inserite in questo piano, durante lo spostamento dal lato del frame holographic verranno rimossi da uno schermo pur essendo ancora visibili in altro. Questo binoculare antagonismo per la sua può essere problematica per la percezione di profondità di ologramma.

**Distanza ottima per il posizionamento vntana da parte dell'utente**

![Distanza ottima per il posizionamento vntana da parte dell'utente](images/distanceguiderendering-750px.png)

**Piani di ritaglio** per la massima comodità è consigliabile distanza di rendering di ritaglio in 85 cm con fadeout del contenuto, iniziando in corrispondenza di 1 milione. Nelle applicazioni in cui sono entrambi fermo ologrammi vntana e gli utenti possono essere visualizzati comodamente il più vicino come 50cm. In questi casi, le applicazioni è consigliabile inserire un piano di ritaglio non meno di 30cm e dissolvenza deve iniziare almeno 10cm lontano dal piano di ritaglio. Ogni volta che è inferiore a quello di 85cm è importante garantire che gli utenti spesso non spostare più vicino o distanza maggiore dal vntana o che vntana non frequente avvicinarsi a o distanza maggiore dall'utente come queste situazioni sono probabilmente a causare disturbo dal contenuto di conflitto vergence facilitazione. Il contenuto deve essere progettato per ridurre al minimo la necessità per l'interazione con più di 85cm da parte dell'utente, ma quando il contenuto deve essere sottoposto a rendering più da vicino a 85cm una buona norma per gli sviluppatori consiste nel progettare gli scenari in cui gli utenti e/o vntana non vengono spostati in modo approfondito più del 25% di t il tempo.

**Procedure consigliate** quando vntana non può essere inserito in 2 minuti e non è possibile evitare conflitti tra la convergenza e alloggio, la zona ottima per la selezione host ologrammi è compreso tra m 1,25 e 5 minuti. In ogni caso, le finestre di progettazione deve strutturare il contenuto per incoraggiare gli utenti di interagire 1 + metri (ad esempio, regolare le dimensioni del contenuto e i parametri di selezione host predefiniti).

## <a name="stabilization-plane"></a>Piano di stabilizzazione
> [!NOTE]
> Per desktop auricolari coinvolgenti, l'impostazione di un piano di stabilizzazione è in genere controproducente, che offre meno qualità visiva rispetto alla disponibilità del buffer di profondità dell'app al sistema per abilitare reprojection basato su profondità per pixel. A meno che non in esecuzione in un HoloLens, è in genere deve evitare di impostare il piano di stabilizzazione.

HoloLens esegue una tecnica di sofisticati stabilizzazione holographic assistita mediante hardware. Ciò avviene automaticamente in gran parte e si ha a che fare con lo spostamento e modifica del punto di vista (CameraPose) come aggiunge un'animazione della scena e l'utente sposta propria testa. Un singolo piano, denominato piano di stabilizzazione, viene scelto per ottimizzare questo stabilizzazione. Mentre tutte vntana nella scena riceve alcuni stabilizzazione, vntana nel piano di stabilizzazione riceve la stabilizzazione hardware massimo.

![Piano di stabilizzazione per oggetti 3D](images/stab-plane-500px.jpg)

Il dispositivo tenterà automaticamente di scegliere il piano, ma l'applicazione può semplificare questo processo, selezionare il punto di stato attivo nella scena. Le app Unity in esecuzione su un HoloLens è consigliabile scegliere il meglio concentrarsi punto di base della scena e passarlo nel [SetFocusPoint()](focus-point-in-unity.md). Un esempio di impostazione del punto di stato attivo in DirectX è incluso nel modello di cubo rotante di predefinito.

Si noti che quando l'app Unity in esecuzione su un visore VR immersivi connesso a un PC desktop, Unity trasmetterà il buffer di profondità Windows abilitare reprojection per pixel, che in genere fornirà ancora migliore qualità di immagine senza lavoro esplicito dall'app. Se si fornisce un punto di stato attivo, che sostituiranno le reprojection per pixel, pertanto, si deve solo eseguire questa operazione quando l'app è in esecuzione su un HoloLens.




```cs
// SetFocusPoint informs the system about a specific point in your scene to
// prioritize for image stabilization. The focus point is set independently
// for each holographic camera.
// You should set the focus point near the content that the user is looking at.
// In this example, we put the focus point at the center of the sample hologram,
// since that is the only hologram available for the user to focus on.
// You can also set the relative velocity and facing of that content; the sample
// hologram is at a fixed point so we only need to indicate its position.
renderingParameters.SetFocusPoint(
    currentCoordinateSystem,
    spinningCubeRenderer.Position
    );
```

Posizione del punto di stato attivo dipende in gran parte di ologramma sta guardando. Progettazione app per la SA contenuto che si desidera che l'utente per osservare l'app ha il vettore sguardo per riferimento.

La cosa più importante singola che uno sviluppatore possa fare per stabilizzare vntana è eseguire il rendering a 60 FPS. Il rilascio sotto 60 FPS ridurrà in modo significativo la stabilità di ologramma, indipendentemente dal fatto l'ottimizzazione del piano di stabilizzazione.

**Procedure consigliate** non è possibile configurare il piano di stabilizzazione universal ed è specifico dell'app, in modo che l'indicazione principale consiste nello sperimentare e vedere cosa è adatta per gli scenari. Tuttavia, è possibile allineare il piano di stabilizzazione con il maggior numero contenuto possibile poiché tutto il contenuto in questo piano è stabilizzato perfettamente.

Ad esempio: 
* Se si dispone solo planare contenuto (app di lettura, la riproduzione di video app), di allineare il piano di stabilizzazione con il piano con il contenuto.
* Se sono presenti 3 sfere piccoli che vengono bloccati al mondo, verificare il piano di stabilizzazione "Taglia" anche se il Data Center di tutte le sfere che sono attualmente in vista dell'utente.
* Se la scena contenuto è sostanzialmente diverse profondità, Ottimizza per dimensione ulteriormente gli oggetti.
* Assicurarsi di modificare il punto di stabilizzazione esaminando ogni fotogramma coincide con l'utente di ologramma

**Cose da evitare** il piano di stabilizzazione è un ottimo strumento per ottenere vntana stabile, ma se utilizzato in modo improprio, può causare instabilità immagine gravi.
* Non "fire and forget", poiché può finire con la stabilizzazione del piano dietro l'utente o collegato a un oggetto che non è più in vista dell'utente. Verificare che il piano di stabilizzazione normale sia impostato opposto fotocamera feedforward (ad esempio: camera.forward)
* Non modificare rapidamente il piano di stabilizzazione avanti e indietro tra estremi
* Non lasciare il piano di stabilizzazione impostato su un distanza fissato/orientamento
* Non lasciare che il piano di stabilizzazione serenità all'utente
* Non impostare il punto di stato attivo durante l'esecuzione in un computer desktop, computer anziché un HoloLens e si basano invece sullo reprojection basato su profondità per pixel.

## <a name="color-separation"></a>Separazione dei colori 

A causa della natura dei display di HoloLens, un elemento denominato "separazione di colori" in alcuni casi può essere percepito. Manifesta come immagine di separazione in singoli base colori: rossi, verdi e blu. L'elemento può essere particolarmente evidenti quando si visualizzano gli oggetti vuoti, poiché sono presenti grandi quantità di rosso, verde e blu. Risulta più evidente quando un utente tiene traccia visivamente ologramma che è in movimento nei frame holographic ad alta velocità. Un altro modo che può manifestarsi l'artefatto è alterare/deformazione degli oggetti. Se un oggetto dispone di contrasto elevato e/o colori puri separazione del colore (rossa, verde, blu), verrà considerata distorsione delle diverse parti dell'oggetto.

**Esempio di quali la selezione di colore di un cursore di arrotondamento bianco blocco head è simile come un utente ruota propria testa al lato:**

![Esempio di quali la selezione di colore di un cursore di arrotondamento bianco blocco head è simile come un utente ruota propria testa al lato.](images/colorseparationofroundwhitecursor-300px.png)

Sebbene sia difficile evitare completamente la separazione di colore, esistono diverse tecniche disponibili per limitare il problema.

**Separazione del colore può essere visualizzata in:**
* Gli oggetti che vengono spostati rapidamente, inclusi gli oggetti di blocco head, ad esempio la [cursore](cursors.md).
* Gli oggetti che sono sostanzialmente distante dal [piano di stabilizzazione](hologram-stability.md#stabilization-plane).

**Per attenuare gli effetti della separazione dei colori:**
* Rendere l'oggetto lag sguardo dell'utente. Dovrebbe apparire come se dispone di alcuni inerzia ed è collegato allo sguardo "on springs". Ciò rallenta il cursore (riduzione distanza di separazione) e lo inserisce dietro punto probabilmente sguardo dell'utente. Purché rapidamente rileva quando l'utente interrompe shifting loro sguardo mi sembra molto naturale.
* Se si desidera spostare ologramma, provare a mantenere relativo spostamento velocità seguito gradi 5 al secondo, se si prevede che l'utente lo seguirà con ai loro stessi occhi.
* Uso *light* invece di *geometry* per il cursore. Un'origine di illuminazione virtuale collegato allo sguardo verrà percepita come un puntatore a interattivo ma non comporterà la separazione di colore.
* Modificare il piano di stabilizzazione in modo che corrisponda il vntana in che l'utente è gazing.
* Rendere il rosso di oggetto, verde o blu.
* Passare a una versione sfocata del contenuto. Un cursore nero round, ad esempio, potrebbe essere modifica a una riga leggermente sfocata orientata nella direzione di movimento.

Come prima, per il rendering a 60 FPS e l'impostazione del piano di stabilizzazione sono le tecniche più importanti per la stabilità di ologramma. Se rivolta verso la separazione di colore evidenti, prima di tutto assicurarsi che la frequenza dei fotogrammi soddisfi le aspettative.

## <a name="see-also"></a>Vedere anche
* [Ottenere informazioni sulle prestazioni per realtà mista](understanding-performance-for-mixed-reality.md)
* [Colore, chiaro e materiali](color,-light-and-materials.md)
* [Nozioni fondamentali di interazione](interaction-fundamentals.md)
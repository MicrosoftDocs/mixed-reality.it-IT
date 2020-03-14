---
title: Stabilità olografica
description: HoloLens stabilizza automaticamente gli ologrammi, ma è possibile eseguire alcuni passaggi per migliorare ulteriormente la stabilità degli ologrammi.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: ologrammi, stabilità, hololens
ms.openlocfilehash: ad48d057ee55d4d0d9ae3080d8030a481aef130f
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375778"
---
# <a name="hologram-stability"></a>Stabilità olografica

Per ottenere ologrammi stabili, HoloLens dispone di una pipeline di stabilizzazione dell'immagine incorporata. La pipeline di stabilizzazione funziona automaticamente in background, pertanto non sono necessari passaggi aggiuntivi per abilitarla. Tuttavia, gli sviluppatori devono esercitare tecniche che migliorano la stabilità degli ologrammi ed evitano scenari che riducono la stabilità.

## <a name="hologram-quality-terminology"></a>Terminologia di qualità olografica

La qualità degli ologrammi è il risultato di un ambiente efficace e uno sviluppo efficace di app. App che hanno raggiunto una costante 60 di frame al secondo in un ambiente in cui HoloLens può tenere traccia degli ambienti, assicurerà che l'ologramma e il sistema di coordinate corrispondente siano sincronizzati. Dal punto di vista di un utente, gli ologrammi che devono essere stazionari non verranno spostati in relazione all'ambiente.

Quando si verificano problemi di ambiente, velocità di rendering incoerenti o basse o altri problemi dell'app, la terminologia seguente è utile per identificare il problema.
* **Precisione.** Una volta che l'ologramma è stato bloccato in tutto il mondo e si trova nel mondo reale, deve rimanere nella posizione in cui è stato collocato, in relazione all'ambiente circostante, indipendentemente dalle modifiche apportate all'ambiente di piccole e sparse. Se un ologramma viene visualizzato in un percorso imprevisto, si tratta di un problema di *accuratezza* . Questi scenari possono verificarsi se due stanze distinte sembrano identiche.
* **Jitter.** Gli utenti osservano questa operazione come agitazione ad alta frequenza di un ologramma. Questo problema può verificarsi quando si verifica un peggioramento dell'ambiente. Per gli utenti, la soluzione esegue l' [ottimizzazione del sensore](sensor-tuning.md).
* **Judder.** Le frequenze di rendering basse generano immagini di movimento e doppie non uniformi degli ologrammi. Questo è particolarmente evidente negli ologrammi con movimento. Gli sviluppatori devono mantenere una [costante 60 fps](hologram-stability.md#frame-rate).
* **Deriva.** Gli utenti visualizzano questo aspetto perché un ologramma sembra allontanarsi dalla posizione in cui è stata originariamente posizionata. Ciò si verifica quando gli ologrammi vengono posizionati lontano dagli [ancoraggi spaziali](spatial-anchors.md), in particolare in parti dell'ambiente che non sono state mappate completamente. La creazione di ologrammi vicini a ancoraggi spaziali riduce la probabilità di Drift.
* **Nervosismo.** Quando un ologramma "estrae" o "salta" fuori dalla propria posizione occasionalmente. Questo problema può verificarsi quando il rilevamento regola gli ologrammi in modo che corrispondano alla conoscenza aggiornata dell'ambiente.
* **Nuotare.** Quando un ologramma sembra ondeggiare corrispondente al movimento della testa dell'utente. Questo errore si verifica quando l'applicazione non ha implementato completamente la [riproiezione](hologram-stability.md#reprojection)e se HoloLens non è [calibrato](calibration.md) per l'utente corrente. Per risolvere il problema, l'utente può eseguire nuovamente l'applicazione di [calibrazione](calibration.md) . Gli sviluppatori possono aggiornare il piano di stabilizzazione per migliorare ulteriormente la stabilità.
* **Separazione dei colori.** Le visualizzazioni in HoloLens sono una visualizzazione sequenziale dei colori, che indica i canali di colore flash di colore rosso-verde-blu-verde a 60Hz (i singoli campi colore sono visualizzati in 240Hz frequenza). Ogni volta che un utente tiene traccia di un ologramma in evoluzione con i suoi occhi, i bordi iniziali e finali di un ologramma si separano nei colori costitutivi, producendo un effetto arcobaleno. Il grado di separazione dipende dalla velocità dell'ologramma. In alcuni casi più rari, lo stato di un ologramma di uno stabile può comportare un effetto arcobaleno. Questa operazione viene definita *[separazione dei colori](hologram-stability.md#color-separation)* .

## <a name="frame-rate"></a>Frequenza dei fotogrammi

La frequenza dei fotogrammi è il primo pilastro della stabilità degli ologrammi. Affinché gli ologrammi siano stabili in tutto il mondo, ogni immagine presentata all'utente deve avere gli ologrammi disegnati nella posizione corretta. Visualizza l'aggiornamento di HoloLens 240 volte al secondo, mostrando quattro campi colore distinti per ogni immagine di cui è stato appena eseguito il rendering, ottenendo un'esperienza utente di 60 FPS (fotogrammi al secondo). Per offrire la migliore esperienza possibile, gli sviluppatori di applicazioni devono mantenere 60 FPS, che si traduce per fornire in modo coerente una nuova immagine al sistema operativo ogni 16 millisecondi.

**60 fps** Per disegnare gli ologrammi come se fossero seduti nel mondo reale, HoloLens deve eseguire il rendering delle immagini dalla posizione dell'utente. Poiché il rendering delle immagini richiede tempo, HoloLens stima la posizione di un utente quando le immagini vengono visualizzate nella visualizzazione. Questo algoritmo di stima è un'approssimazione. HoloLens dispone di hardware che consente di regolare l'immagine di rendering per tenere conto della discrepanza tra la posizione della testa stimata e quella effettiva. In questo modo, l'immagine visualizzata dall'utente viene visualizzata come se fosse stata sottoposta a rendering dalla posizione corretta e gli ologrammi fossero stabili. Gli aggiornamenti delle immagini funzionano meglio con le modifiche minime e non possono correggere completamente alcuni elementi nell'immagine di cui è stato eseguito il rendering come Motion-parallasse.

Eseguendo il rendering a 60 FPS, si eseguono tre operazioni che consentono di creare ologrammi stabili:
1. Riduzione della latenza complessiva tra il rendering di un'immagine e l'immagine visualizzata dall'utente. In un motore con un thread di gioco e un thread di rendering eseguiti contemporaneamente, l'esecuzione a 30 FPS può causare un aumento della latenza di 33,3 ms. La riduzione della latenza consente di ridurre l'errore di stima e aumentare la stabilità degli ologrammi.
2. In modo che ogni immagine che raggiunge gli occhi dell'utente abbia una quantità di latenza uniforme. Se si esegue il rendering a 30 fps, nella visualizzazione vengono comunque visualizzate le immagini a 60 FPS. Ciò significa che la stessa immagine verrà visualizzata due volte in una riga. Il secondo frame avrà una latenza maggiore di 16,6 ms rispetto al primo fotogramma e dovrà correggere una quantità di errore più evidente. Questa incoerenza nella grandezza degli errori può causare un tremolio di 60Hz indesiderato.
3. Riduzione dell'effetto di tremolio, caratterizzato da immagini doppie o con movimento non uniforme. Un movimento dell'ologramma più veloce e velocità di rendering inferiori determinano un effetto di tremolio più pronunciato. Per questo motivo, il tentativo di mantenere 60 FPS in qualsiasi momento consentirà di evitare il tremolio per un ologramma in fase di trasferimento.

**Coerenza frequenza frame** La coerenza della frequenza di fotogrammi è importante quanto un frame elevato al secondo. I frame talvolta eliminati sono inevitabili per qualsiasi applicazione con contenuto e HoloLens implementa alcuni algoritmi sofisticati per il ripristino da problemi occasionali. Tuttavia, un framerate costantemente fluttuante è molto più evidente a un utente rispetto all'esecuzione coerente a frequenze di fotogrammi inferiori. Ad esempio, un'applicazione che esegue il rendering senza problemi di 5 fotogrammi (60 FPS per la durata di questi 5 fotogrammi) e quindi rilascia tutti gli altri frame per i 10 fotogrammi successivi (30 FPS per la durata di questi 10 fotogrammi) risulta più instabile rispetto a un'applicazione che in modo coerente viene eseguito il rendering a 30 FPS.

In una nota correlata, il sistema operativo limiterà le applicazioni fino a 30 FPS quando l' [acquisizione di realtà mista](mixed-reality-capture.md) è in esecuzione.

**Analisi delle prestazioni** Sono disponibili diversi strumenti che è possibile usare per eseguire il benchmark della frequenza dei fotogrammi dell'applicazione, ad esempio:
* GPUView
* Debugger grafica di Visual Studio
* Profiler incorporati in motori 3D, ad esempio Unity

## <a name="hologram-render-distances"></a>Distanze di rendering ologramma

>[!VIDEO https://www.youtube.com/embed/-606oZKLa_s]

Il sistema visivo umano integra più segnali dipendenti dalla distanza quando si fissa e si concentra su un oggetto.
* [Alloggio](https://en.wikipedia.org/wiki/Accommodation_%28eye%29) : l'obiettivo di un singolo occhio.
* [Convergenza](https://en.wikipedia.org/wiki/Convergence_(eye)) : due occhi si spostano verso l'interno o verso l'esterno al centro su un oggetto.
* [Visione binoculare](https://en.wikipedia.org/wiki/Stereopsis) : differenze tra le immagini a sinistra e a destra che dipendono dalla distanza di un oggetto dal punto di ancoraggio.
* Ombreggiatura, dimensioni angolari relative e altri suggerimenti monoculare (occhio singolo).

La convergenza e l'alloggio sono univoche perché si tratta di segnali aggiuntivi retinici correlati al modo in cui gli occhi cambiano per percepire gli oggetti a distanze diverse. In visualizzazione naturale, convergenza e alloggio sono collegati. Quando gli occhi visualizzano un elemento vicino (ad esempio, il naso), gli occhi si incrociano e si adattano a un punto vicino. Quando gli occhi visualizzano qualcosa all'infinito, gli occhi diventano paralleli e l'occhio si adatta all'infinito. Gli utenti che indossano HoloLens saranno sempre a 2,0 m per mantenere un'immagine chiara perché i HoloLens visualizzati sono fissi a distanza ottica circa 2,0 m dall'utente. Gli sviluppatori di app controllano la posizione di convergenza degli occhi degli utenti inserendo contenuto e ologrammi a diverse profondità. Quando gli utenti sono in grado di adattarsi a diverse distanze, il collegamento naturale tra i due segnali viene danneggiato, causando fastidio visivi o affaticamento, soprattutto quando la grandezza del conflitto è grande. Il disagio del conflitto vergence-accommodation può essere evitato o ridotto a icona mantenendo il contenuto che gli utenti convergeranno fino a 2,0 m come possibile (ad esempio, in una scena con molta profondità, quando possibile, le aree di interesse più vicine a 2,0 m). Quando non è possibile posizionare il contenuto vicino a 2,0 m, il disagio del conflitto vergence-Accommodation è maggiore quando lo sguardo dell'utente tra diverse distanze. In altre parole, è molto più confortevole guardare un ologramma che rimane fisso a 50 cm di distanza rispetto a un ologramma distante 50 cm che si avvicina e si allontana nel corso del tempo.

L'inserimento di contenuto a 2,0 m è vantaggioso anche perché i due schermi sono progettati per una sovrapposizione completa a questa distanza. Per le immagini posizionate fuori da questo piano, man mano che si spostano sul lato del frame olografico scompariranno da una visualizzazione rimanendo comunque visibile sull'altro. Questa rivalità binoculare può compromettere la percezione approfondita dell'ologramma.

**Distanza ottimale per il posizionamento degli ologrammi rispetto allo sguardo dell'utente**

![Distanza ottimale per inserire gli ologrammi dall'utente](images/distanceguiderendering-750px.png)

**Ritagliare i piani** Per la massima comodità, è consigliabile ritagliare la distanza di rendering in 85cm con la dissolvenza del contenuto a partire da 1 milione. Nelle applicazioni in cui gli ologrammi e gli utenti sono entrambi stazionari, gli ologrammi possono essere visualizzati comodamente fino a 50 cm. In questi casi, le applicazioni devono posizionare un piano di ritaglio non più vicino a 30cm e il fade out dovrebbe iniziare da almeno 10 cm dal piano di ritaglio. Ogni volta che il contenuto è più vicino a 85cm, è importante assicurarsi che gli utenti non vengano spesso spostati da ologrammi o che gli ologrammi non si avvicinino di frequente all'utente, in quanto questi casi potrebbero causare disagio dalla vergence-conflitto di alloggi. Il contenuto deve essere progettato per ridurre al minimo la necessità di interazioni più vicine a 85cm dall'utente, ma quando il contenuto deve essere sottoposto a rendering più vicino a 85cm, una regola empirica per gli sviluppatori è progettare scenari in cui gli utenti e/o gli ologrammi non si spostano in profondità oltre il 25% del tempo.

**Procedure consigliate** Quando gli ologrammi non possono essere posizionati su 2m e i conflitti tra la convergenza e l'alloggio non possono essere evitati, la zona ottimale per la posizione degli ologrammi è compresa tra 1.25 m e 5m. In ogni caso, i progettisti devono strutturare il contenuto per incoraggiare gli utenti a interagire tra 1 + m (ad esempio, modificare le dimensioni del contenuto e i parametri di posizionamento predefiniti).

## <a name="reprojection"></a>Riproiezione
HoloLens esegue una sofisticata tecnica di stabilizzazione olografica assistita da hardware, nota come riproiezione. In questo modo viene preso in considerazione il movimento e la modifica del punto di vista (CameraPose) durante l'animazione della scena e l'utente sposta la testa.  Le applicazioni devono eseguire azioni specifiche per l'uso ottimale della riproiezione.


Sono disponibili quattro tipi principali di riproiezione
* **Riproiezione profondità:**  Ciò consente di ottenere risultati ottimali con il minor numero di sforzi dell'applicazione.  Tutte le parti della scena sottoposta a rendering sono stabilizzate in modo indipendente in base alla distanza dall'utente.  Alcuni artefatti di rendering possono essere visibili in presenza di modifiche acute in profondità.  Questa opzione è disponibile solo in HoloLens 2 e negli auricolari immersivi.
* **Riproiezione planare:**  Questo consente all'applicazione di controllare in modo preciso la stabilizzazione.  Un piano viene impostato dall'applicazione e tutto ciò che si trova sul piano sarà la parte più stabile della scena.  Più un ologramma è lontano dal piano, minore sarà la stabilità.  Questa opzione è disponibile in tutte le piattaforme Windows.
* **Riproiezione piana automatica:**  Il sistema imposta un piano di stabilizzazione usando le informazioni nel buffer di profondità.  Questa opzione è disponibile in HoloLens generazione 1 e HoloLens 2.
* **Nessuno:** Se l'applicazione non esegue alcuna operazione, la riproiezione piana viene utilizzata con il piano di stabilizzazione fisso a 2 metri nella direzione dello sguardo a capo dell'utente.  Questo genererà risultati sottostandard.

Le applicazioni devono eseguire azioni specifiche per abilitare i diversi tipi di riproiezione
* **Riproiezione profondità:** L'applicazione invia il buffer di profondità al sistema per ogni frame sottoposto a rendering.  In Unity, questa operazione viene eseguita con l'opzione "Abilita condivisione buffer di profondità" nel riquadro Impostazioni lettore.  Le app DirectX chiamano CommitDirect3D11DepthBuffer.  L'applicazione non deve chiamare SetFocusPoint.
* **Riproiezione planare:** In ogni frame, le applicazioni indicano al sistema la posizione di un piano da stabilizzare.  Le applicazioni Unity chiamano SetFocusPointForFrame e dovrebbero essere disabilitate "Abilita condivisione buffer di profondità".  Le app DirectX chiamano SetFocusPoint e non devono chiamare CommitDirect3D11DepthBuffer.
* **Riproiezione piana automatica:** Per abilitare questa operazione, l'applicazione deve inviare il buffer di profondità al sistema come per la riproiezione approfondita.  In HoloLens 2, l'applicazione deve quindi SetFocusPoint con un punto di 0, 0 per ogni fotogramma.  Per HoloLens generazione 1, l'applicazione non deve chiamare SetFocusPoint.

### <a name="choosing-reprojection-technique"></a>Scelta della tecnica di riproiezione

Tipo di stabilizzazione |    Auricolari immersivi |    HoloLens generazione 1 | HoloLens 2
--- | --- | --- | ---
Riproiezione profondità |    Consigliato |   N/D |   Consigliato<br/><br/>Le applicazioni Unity devono usare Unity 2018.4.12 o versione successiva o Unity 2019,3 o versione successiva. In caso contrario, usare la riproiezione piana automatica.
Riproiezione piana automatica | N/D |   Impostazione predefinita consigliata |   Consigliato se la riproiezione di profondità non fornisce i risultati migliori<br/><br/>Le applicazioni Unity sono consigliate per usare Unity 2018.4.12 o versione successiva o Unity 2019,3 o versione successiva.  Le versioni precedenti di Unity funzioneranno con risultati di riproiezione leggermente ridotti.
Riproiezione planare |   Non consigliato |   Consigliato se il Planar automatico non fornisce i risultati migliori |    Usare se nessuna delle opzioni di profondità fornisce i risultati desiderati    

### <a name="verifying-depth-is-set-correctly"></a>La verifica della profondità è stata impostata correttamente
            
Quando un metodo di riproiezione usa il buffer di profondità, è importante verificare che il contenuto del buffer di profondità rappresenti la scena di rendering dell'applicazione.  Una serie di fattori può causare problemi.  Se è presente una seconda fotocamera usata per eseguire il rendering delle sovrapposizioni dell'interfaccia utente, ad esempio, è probabile che sovrascriva tutte le informazioni di profondità dalla visualizzazione effettiva.  Gli oggetti trasparenti spesso non impostano la profondità.  Per impostazione predefinita, per il rendering del testo non viene impostata la profondità.  Quando la profondità non corrisponde agli ologrammi sottoposti a rendering, nel rendering saranno presenti anomalie visibili.
            
HoloLens 2 ha un visualizzatore che mostra dove la profondità è e non viene impostata.  Abilitare questa operazione dal portale del dispositivo.  Nella scheda **viste** > **stabilità ologramma** Selezionare la **Visualizzazione profondità della visualizzazione nella casella di controllo auricolare** .  Le aree con una profondità impostata correttamente saranno blu.  Gli elementi di cui è stato eseguito il rendering senza set di profondità saranno rossi e pertanto dovranno essere corretti.  Si noti che la visualizzazione della profondità non viene visualizzata nell'acquisizione di realtà mista.  È visibile solo tramite il dispositivo.
            
Alcuni strumenti di visualizzazione GPU consentiranno la visualizzazione del buffer di profondità.  Gli sviluppatori di applicazioni possono utilizzare questi strumenti per assicurarsi che la profondità venga impostata correttamente.  Consultare la documentazione per gli strumenti dell'applicazione.

### <a name="using-planar-reprojection"></a>Uso della riproiezione planare
> [!NOTE]
> Per gli auricolari desktop immersivi, l'impostazione di un piano di stabilizzazione è in genere controproducente, in quanto offre una minore qualità visiva rispetto alla fornitura del buffer di profondità dell'app al sistema per abilitare la riproiezione basata sulla profondità per pixel. A meno che non sia in esecuzione in un HoloLens, è in genere consigliabile evitare di impostare il piano di stabilizzazione.

![Piano di stabilizzazione per oggetti 3D](images/stab-plane-500px.jpg)

Il dispositivo tenterà automaticamente di scegliere questo piano, ma l'applicazione deve supportare questo processo selezionando il punto di interesse nella scena. Le app Unity in esecuzione in un HoloLens devono scegliere il punto focale migliore in base alla scena e passarle a [SetFocusPoint ()](focus-point-in-unity.md). Un esempio di impostazione del punto di stato attivo in DirectX è incluso nel modello di cubo rotante predefinito.

Si noti che quando l'app Unity viene eseguita su un headset immersivo connesso a un PC desktop, Unity invierà il buffer di profondità a Windows per abilitare la riproiezione per pixel, che in genere garantisce una qualità dell'immagine ancora migliore senza lavoro esplicito da parte dell'app. Se si fornisce un punto di interesse che sostituisce la riproiezione per pixel, è consigliabile eseguire questa operazione solo quando l'app è in esecuzione in un HoloLens.




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

La posizione del punto di interesse in gran parte dipende da ciò che l'ologramma sta osservando. L'app presenta il vettore dello sguardo per riferimento e la finestra di progettazione dell'app sa quale contenuto desidera che l'utente osservi.

La cosa più importante che uno sviluppatore può eseguire per stabilizzare gli ologrammi consiste nel rendering a 60 FPS. Se si scende sotto 60 FPS, si riduce significativamente la stabilità dell'ologramma, indipendentemente dall'ottimizzazione del piano di stabilizzazione.

**Procedure consigliate** Non esiste un modo universale per configurare il piano di stabilizzazione ed è specifico dell'app, quindi la raccomandazione principale è sperimentare e vedere cosa funziona meglio per gli scenari. Tuttavia, provare a allineare il piano di stabilizzazione con il maggior volume possibile di contenuto, perché tutto il contenuto di questo piano è perfettamente stabilizzato.

Ad esempio,
* Se si dispone solo di contenuto planare (lettura di app, app per la riproduzione video), allineare il piano di stabilizzazione al piano con il contenuto.
* Se sono presenti tre piccole sfere bloccate a livello globale, il piano di stabilizzazione viene tagliato anche se i centri di tutte le sfere attualmente presenti nella visualizzazione dell'utente.
* Se la scena include contenuto con profondità notevolmente diverse, prediligere ulteriori oggetti.
* Assicurarsi di modificare il punto di stabilizzazione di ogni fotogramma per coincidere con l'ologramma esaminato dall'utente

**Aspetti da evitare** Il piano di stabilizzazione è un ottimo strumento per ottenere ologrammi stabili, ma se viene usato in modo improprio, può comportare instabilità di immagini gravi.
* Non "Fire and Forget", dal momento che è possibile finire con il piano di stabilizzazione dietro l'utente o collegato a un oggetto che non è più presente nella visualizzazione dell'utente. Verificare che il piano di stabilizzazione normale sia impostato su un lato successivo della fotocamera (ad esempio,-fotocamera. in poi)
* Non modificare rapidamente il piano di stabilizzazione tra estremi
* Non lasciare il piano di stabilizzazione impostato su una distanza o un orientamento fisso
* Non consentire all'utente di ridurre il piano di stabilizzazione
* Non impostare il punto di messa a fuoco quando viene eseguito in un computer desktop anziché in un HoloLens e si basa invece sulla riproiezione basata sulla profondità per pixel.

## <a name="color-separation"></a>Separazione dei colori 

A causa della natura delle visualizzazioni di HoloLens, è talvolta possibile percepire un artefatto denominato "separazione dei colori". Si manifesta come immagine che separa i singoli colori di base: rosso, verde e blu. L'artefatto può essere particolarmente visibile quando si visualizzano oggetti bianchi, perché hanno grandi quantità di rosso, verde e blu. È più evidente quando un utente tiene traccia visiva di un ologramma che si muove attraverso il frame olografico ad alta velocità. Un altro modo in cui l'artefatto può manifestarsi è la distorsione/deformazione degli oggetti. Se un oggetto ha un contrasto elevato e/o colori puri (rosso, verde, blu), la separazione dei colori viene percepita come distorsione delle diverse parti dell'oggetto.

**Esempio di ciò che la separazione dei colori di un cursore rotondo bianco con blocco Head potrebbe avere l'aspetto di un utente che ruota verso il lato:**

![Esempio di ciò che la separazione dei colori di un cursore rotondo bianco con blocco Head potrebbe apparire come un utente ruota l'intestazione verso il lato.](images/colorseparationofroundwhitecursor-300px.png)

Sebbene sia difficile evitare completamente la separazione dei colori, sono disponibili diverse tecniche per attenuarla.

**La separazione dei colori può essere visualizzata in:**
* Oggetti spostati rapidamente, inclusi oggetti con blocco Head, ad esempio il [cursore](cursors.md).
* Oggetti che sono sostanzialmente lontani dal [piano di stabilizzazione](hologram-stability.md#reprojection).

**Per attenuare gli effetti della separazione dei colori:**
* Fare in modo che l'oggetto ritardi lo sguardo dell'utente. Dovrebbe apparire come se avesse una certa inerzia ed è associato allo sguardo "on Springs". Questo rallenta il cursore (riducendo la distanza di separazione) e lo inserisce dietro il punto di sguardo probabile dell'utente. Fino a quel momento, quando l'utente smette di spostare il proprio sguardo, si sente piuttosto naturale.
* Se si vuole spostare un ologramma, provare a mantenerne la velocità di spostamento al di sotto di 5 gradi al secondo se si prevede che l'utente lo segua con gli occhi.
* Utilizzare la *luce* anziché la *geometria* per il cursore. Un'origine di illuminazione virtuale collegata allo sguardo viene percepita come un puntatore interattivo ma non causa la separazione dei colori.
* Modificare il piano di stabilizzazione in modo che corrisponda agli ologrammi a cui l'utente sta guardando.
* Rendere l'oggetto rosso, verde o blu.
* Passa a una versione sfocata del contenuto. Ad esempio, è possibile modificare un cursore bianco arrotondato in una linea leggermente sfocata orientata alla direzione del movimento.

Come in precedenza, il rendering a 60 FPS e l'impostazione del piano di stabilizzazione sono le tecniche più importanti per la stabilità degli ologrammi. Se si verifica la separazione dei colori evidente, verificare innanzitutto che la frequenza dei fotogrammi soddisfi le aspettative.

## <a name="see-also"></a>Vedere anche
* [Informazioni sulle prestazioni per la realtà mista](understanding-performance-for-mixed-reality.md)
* [Colore, luce e materiali](color,-light-and-materials.md)
* [Interazioni istintive](interaction-fundamentals.md)
* [Stabilizzazione ologramma MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/hologram-stabilization.html)

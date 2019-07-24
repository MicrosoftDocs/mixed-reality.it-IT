---
title: Stabilità olografica
description: HoloLens stabilizza automaticamente gli ologrammi, ma è possibile eseguire alcuni passaggi per migliorare ulteriormente la stabilità degli ologrammi.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: ologrammi, stabilità, hololens
ms.openlocfilehash: b35b904e3c662c5ebd0670a98044706fe208e348
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974931"
---
# <a name="hologram-stability"></a>Stabilità olografica

Per ottenere ologrammi stabili, HoloLens dispone di una pipeline di stabilizzazione dell'immagine incorporata. La pipeline di stabilizzazione funziona automaticamente in background, pertanto non sono necessari passaggi aggiuntivi per abilitarla. Tuttavia, gli sviluppatori devono esercitare tecniche che migliorano la stabilità degli ologrammi ed evitano scenari che riducono la stabilità.

## <a name="hologram-quality-terminology"></a>Terminologia di qualità olografica

La qualità degli ologrammi è il risultato di un ambiente efficace e uno sviluppo efficace di app. App che hanno raggiunto una costante 60 di frame al secondo in un ambiente in cui HoloLens può tenere traccia degli ambienti, assicurerà che l'ologramma e il sistema di coordinate corrispondente siano sincronizzati. Dal punto di vista di un utente, gli ologrammi che devono essere stazionari non verranno spostati in relazione all'ambiente.

Quando si verificano problemi di ambiente, velocità di rendering incoerenti o basse o altri problemi dell'app, la terminologia seguente è utile per identificare il problema.
* **Precisione.** Una volta che l'ologramma è stato bloccato in tutto il mondo e si trova nel mondo reale, deve rimanere nella posizione in cui è stato collocato, in relazione all'ambiente circostante, indipendentemente dalle modifiche apportate all'ambiente di piccole e sparse. Se un ologramma viene visualizzato in un percorso imprevisto, si  tratta di un problema di accuratezza. Questi scenari possono verificarsi se due stanze distinte sembrano identiche.
* **Jitter.** Gli utenti osservano questa operazione come agitazione ad alta frequenza di un ologramma. Questo problema può verificarsi quando si verifica un peggioramento dell'ambiente. Per gli utenti, la soluzione esegue l' [ottimizzazione del sensore](sensor-tuning.md).
* **Judder.** Le frequenze di rendering basse generano immagini di movimento e doppie non uniformi degli ologrammi. Questo è particolarmente evidente negli ologrammi con movimento. Gli sviluppatori devono mantenere una [costante 60 fps](hologram-stability.md#frame-rate).
* **Deriva.** Gli utenti visualizzano questo aspetto perché l'ologramma sembra allontanarsi dalla posizione in cui è stata originariamente posizionata. Ciò si verifica quando gli ologrammi vengono posizionati lontano dagli [ancoraggi spaziali](spatial-anchors.md), in particolare in parti dell'ambiente che non sono state mappate completamente. La creazione di ologrammi vicini a ancoraggi spaziali riduce la probabilità di Drift.
* **Nervosismo.** Quando un ologramma "estrae" o "salta" fuori dalla posizione, occasionalmente. Questo problema può verificarsi quando il rilevamento regola gli ologrammi in modo che corrispondano alla conoscenza aggiornata dell'ambiente.
* **Nuotare.** Quando un ologramma sembra ondeggiare corrispondente al movimento della testa dell'utente. Questo errore si verifica quando gli ologrammi non si trovano sul [piano](hologram-stability.md#stabilization-plane)di stabilizzazione e se HoloLens non è [calibrato](calibration.md) per l'utente corrente. Per risolvere il problema, l'utente può eseguire nuovamente l'applicazione di [calibrazione](calibration.md) . Gli sviluppatori possono aggiornare il piano di stabilizzazione per migliorare ulteriormente la stabilità.
* **Separazione dei colori.** Le visualizzazioni in HoloLens sono una visualizzazione sequenziale dei colori, che indica i canali di colore flash di colore rosso-verde-blu-verde a 60Hz (i singoli campi colore sono visualizzati in 240Hz frequenza). Ogni volta che un utente tiene traccia di un ologramma in evoluzione con i suoi occhi, i bordi iniziali e finali di un ologramma si separano nei colori costitutivi, producendo un effetto arcobaleno. Il grado di separazione dipende dalla velocità dell'ologramma. In alcuni casi più rari, lo stato di un ologramma di uno stabile può comportare un effetto arcobaleno. Questa operazione viene definita *[separazione dei colori](hologram-stability.md#color-separation)* .

## <a name="frame-rate"></a>Frequenza dei fotogrammi

La frequenza dei fotogrammi è il primo pilastro della stabilità degli ologrammi. Affinché gli ologrammi siano stabili in tutto il mondo, ogni immagine presentata all'utente deve avere gli ologrammi disegnati nella posizione corretta. Visualizza l'aggiornamento di HoloLens 240 volte al secondo, mostrando quattro campi colore distinti per ogni immagine di cui è stato appena eseguito il rendering, ottenendo un'esperienza utente di 60 FPS (fotogrammi al secondo). Per offrire la migliore esperienza possibile, gli sviluppatori di applicazioni devono mantenere 60 FPS, che si traduce per fornire in modo coerente una nuova immagine al sistema operativo ogni 16 millisecondi.

**60 fps** Per disegnare gli ologrammi come se fossero seduti nel mondo reale, HoloLens deve eseguire il rendering delle immagini dalla posizione dell'utente. Poiché il rendering delle immagini richiede tempo, HoloLens stima la posizione di un utente quando le immagini vengono visualizzate nella visualizzazione. Questo algoritmo di stima è un'approssimazione. HoloLens dispone di hardware che consente di regolare l'immagine di rendering per tenere conto della discrepanza tra la posizione della testa stimata e quella effettiva. In questo modo, l'immagine visualizzata dall'utente viene visualizzata come se fosse stata sottoposta a rendering dalla posizione corretta e gli ologrammi fossero stabili. Gli aggiornamenti delle immagini funzionano meglio con le modifiche minime e non possono correggere completamente alcuni elementi nell'immagine di cui è stato eseguito il rendering come Motion-parallasse.

Eseguendo il rendering a 60 FPS, si eseguono tre operazioni che consentono di creare ologrammi stabili:
1. Riduzione della latenza complessiva tra il rendering di un'immagine e l'immagine visualizzata dall'utente. In un motore con un thread di gioco e un thread di rendering in esecuzione in contemporanea, l'esecuzione a 30 fps può aggiungere 33,3 ms di latenza aggiuntiva. Riducendo la latenza, questo riduce l'errore di stima e aumenta la stabilità degli ologrammi.
2. In modo che ogni immagine che raggiunge gli occhi dell'utente abbia una quantità di latenza uniforme. Se si esegue il rendering a 30 fps, nella visualizzazione vengono comunque visualizzate le immagini a 60 FPS. Ciò significa che la stessa immagine verrà visualizzata due volte in una riga. Il secondo frame avrà una latenza maggiore di 16,6 ms rispetto al primo fotogramma e dovrà correggere una quantità di errore più evidente. Questa incoerenza nella grandezza degli errori può causare un tremolio di 60Hz indesiderato.
3. Riduzione dell'aspetto di judder, caratterizzato da immagini di movimento e doppie non uniformi. Un movimento dell'ologramma più veloce e frequenze di rendering inferiori sono associate a judder più pronunciato. Per questo motivo, il tentativo di mantenere 60 FPS in qualsiasi momento consentirà di evitare il tremolio per un ologramma in fase di trasferimento.

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

La convergenza e l'alloggio sono univoche perché si tratta di segnali aggiuntivi retinici correlati al modo in cui gli occhi cambiano per percepire gli oggetti a distanze diverse. In visualizzazione naturale, convergenza e alloggio sono collegati. Quando gli occhi visualizzano un elemento vicino, ad esempio il naso, gli occhi si incrociano e si adattano a un punto vicino. Quando gli occhi visualizzano qualcosa all'infinito, gli occhi diventano paralleli e l'occhio si adatta all'infinito. Gli utenti che indossano HoloLens saranno sempre a 2,0 m per mantenere un'immagine chiara perché i HoloLens visualizzati sono fissi a distanza ottica circa 2,0 m dall'utente. Gli sviluppatori di app controllano la posizione di convergenza degli occhi degli utenti inserendo contenuto e ologrammi a diverse profondità. Quando gli utenti sono in grado di adattarsi a diverse distanze, il collegamento naturale tra i due segnali viene danneggiato e ciò può causare disagi visivi o affaticamento, soprattutto quando la grandezza del conflitto è grande. Il disagio del conflitto di vergence-accommodation può essere evitato o ridotto a icona mantenendo il contenuto che gli utenti convergeranno fino a 2,0 m come possibile (ad esempio, in una scena con molta profondità posizionare le aree di interesse quasi a 2,0 m quando possibile). Quando non è possibile posizionare il contenuto vicino a 2,0 m, il conflitto tra vergence è maggiore quando lo sguardo dell'utente si sposta tra diverse distanze. In altre parole, è molto più semplice esaminare un ologramma stazionario che rimanga a 50 centimetri rispetto a un ologramma che si sposta verso e fuori dal tempo.

L'inserimento di contenuto a 2,0 m è vantaggioso anche perché i due schermi sono progettati per una sovrapposizione completa a questa distanza. Per le immagini posizionate fuori da questo piano, man mano che si spostano sul lato del frame olografico scompariranno da una visualizzazione rimanendo comunque visibile sull'altro. Questa rivalità binoculare può compromettere la percezione approfondita dell'ologramma.

**Distanza ottimale per inserire gli ologrammi dall'utente**

![Distanza ottimale per inserire gli ologrammi dall'utente](images/distanceguiderendering-750px.png)

**Ritagliare i piani** Per la massima comodità, è consigliabile ritagliare la distanza di rendering in 85cm con la dissolvenza del contenuto a partire da 1 milione. Nelle applicazioni in cui gli ologrammi e gli utenti sono entrambi ologrammi stazionari possono essere visualizzati comodamente vicino a 50cm. In questi casi, le applicazioni devono posizionare un piano di ritaglio non più vicino a 30cm e il fade out dovrebbe iniziare da almeno 10 cm dal piano di ritaglio. Ogni volta che il contenuto è più vicino a 85cm, è importante assicurarsi che gli utenti non si avvicinino di frequente agli ologrammi o che gli ologrammi non si avvicinino di frequente all'utente, in quanto questi casi potrebbero causare disagio dalla vergence-conflitto di alloggi. Il contenuto deve essere progettato per ridurre al minimo la necessità di interazioni più vicine a 85cm dall'utente, ma quando il contenuto deve essere sottoposto a rendering più vicino a 85cm una regola empirica per gli sviluppatori è progettare scenari in cui gli utenti e/o gli ologrammi non si spostano in profondità oltre il 25% di t tempo.

**Procedure consigliate** Quando gli ologrammi non possono essere posizionati su 2m e i conflitti tra la convergenza e l'alloggio non possono essere evitati, la zona ottimale per la posizione degli ologrammi è compresa tra 1.25 m e 5m. In ogni caso, i progettisti devono strutturare il contenuto per incoraggiare gli utenti a interagire tra 1 + m (ad esempio, modificare le dimensioni del contenuto e i parametri di posizionamento predefiniti).

## <a name="stabilization-plane"></a>Piano di stabilizzazione
> [!NOTE]
> Per gli auricolari desktop immersivi, l'impostazione di un piano di stabilizzazione è in genere controproducente, in quanto offre una minore qualità visiva rispetto alla fornitura del buffer di profondità dell'app al sistema per abilitare la riproiezione basata sulla profondità per pixel. A meno che non sia in esecuzione in un HoloLens, è in genere consigliabile evitare di impostare il piano di stabilizzazione.

HoloLens esegue una tecnica sofisticata di stabilizzazione olografica assistita da hardware. Questa operazione è in gran parte automatica ed è necessario procedere con il movimento e la modifica del punto di vista (CameraPose) quando la scena viene animata e l'utente sposta l'intestazione. Per ottimizzare questa stabilizzazione, viene scelto un singolo piano, denominato piano di stabilizzazione. Sebbene tutti gli ologrammi nella scena ricevano una certa stabilizzazione, gli ologrammi nel piano di stabilizzazione ricevono la massima stabilizzazione hardware.

![Piano di stabilizzazione per oggetti 3D](images/stab-plane-500px.jpg)

Il dispositivo tenterà automaticamente di scegliere questo piano, ma l'applicazione può supportare questo processo selezionando il punto di interesse nella scena. Le app Unity in esecuzione in un HoloLens devono scegliere il punto focale migliore in base alla scena e passarle a [SetFocusPoint ()](focus-point-in-unity.md). Un esempio di impostazione del punto di stato attivo in DirectX è incluso nel modello di cubo rotante predefinito.

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

La posizione del punto di interesse in gran parte dipende dall'ologramma che sta esaminando. L'app presenta il vettore dello sguardo per riferimento e la finestra di progettazione dell'app sa quale contenuto desidera che l'utente osservi.

La cosa più importante che uno sviluppatore può eseguire per stabilizzare gli ologrammi consiste nel rendering a 60 FPS. Se si scende sotto 60 FPS, si riduce significativamente la stabilità dell'ologramma, indipendentemente dall'ottimizzazione del piano di stabilizzazione.

**Procedure consigliate** Non esiste un modo universale per configurare il piano di stabilizzazione ed è specifico dell'app, quindi la raccomandazione principale è sperimentare e vedere cosa funziona meglio per gli scenari. Tuttavia, provare a allineare il piano di stabilizzazione con il maggior volume possibile di contenuto, perché tutto il contenuto di questo piano è perfettamente stabilizzato.

Ad esempio:
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
* Oggetti che sono sostanzialmente lontani dal [piano](hologram-stability.md#stabilization-plane)di stabilizzazione.

**Per attenuare gli effetti della separazione dei colori:**
* Fare in modo che l'oggetto ritardi lo sguardo dell'utente. Dovrebbe apparire come se avesse una certa inerzia ed è associato allo sguardo "on Springs". Questo rallenta il cursore (riducendo la distanza di separazione) e lo inserisce dietro il punto di sguardo probabile dell'utente. Fino a quel momento, quando l'utente smette di spostare il proprio sguardo, si sente piuttosto naturale.
* Se si vuole spostare un ologramma, provare a mantenerla sotto i 5 gradi al secondo se si prevede che l'utente lo segua con gli occhi.
* Utilizzare la *luce* anziché la *geometria* per il cursore. Un'origine di illuminazione virtuale collegata allo sguardo viene percepita come un puntatore interattivo ma non causa la separazione dei colori.
* Modificare il piano di stabilizzazione in modo che corrisponda agli ologrammi a cui l'utente sta guardando.
* Rendere l'oggetto rosso, verde o blu.
* Passa a una versione sfocata del contenuto. Ad esempio, un cursore bianco rotondo può essere modificato in una linea leggermente sfocata orientata alla direzione del movimento.

Come in precedenza, il rendering a 60 FPS e l'impostazione del piano di stabilizzazione sono le tecniche più importanti per la stabilità degli ologrammi. Se si verifica la separazione dei colori evidente, verificare innanzitutto che la frequenza dei fotogrammi soddisfi le aspettative.

## <a name="see-also"></a>Vedere anche
* [Informazioni sulle prestazioni per la realtà mista](understanding-performance-for-mixed-reality.md)
* [Colore, luce e materiali](color,-light-and-materials.md)
* [Interazioni istintive](interaction-fundamentals.md)
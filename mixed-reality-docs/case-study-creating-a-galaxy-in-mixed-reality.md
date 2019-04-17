---
title: 'Case study: creazione di un galaxy in realtà mista'
description: Prima di spedizione Microsoft HoloLens, abbiamo chiesto la nostra community di sviluppatori il tipo di app vorrebbero vedere un team interno di esperti di compilazione per il nuovo dispositivo. Sono stati condivisi più di 5000 idee e dopo un poll di Twitter di 24 ore, il vincitore è stata un'idea denominata "Galaxy Explorer".
author: KarimLUCCIN
ms.author: kaluccin
ms.date: 03/21/2018
ms.topic: article
keywords: Esplora Galaxy, HoloLens, realtà mista di Windows, Condividi la tua idea, case study
ms.openlocfilehash: a478eaa35144a8ee0fbeaeb43cec4b9f901890ab
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604830"
---
# <a name="case-study---creating-a-galaxy-in-mixed-reality"></a>Case study: creazione di un galaxy in realtà mista

Prima di spedizione Microsoft HoloLens, abbiamo chiesto la nostra community di sviluppatori il tipo di app vorrebbero vedere un team interno di esperti di compilazione per il nuovo dispositivo. Sono stati condivisi più di 5000 idee e dopo un poll di Twitter di 24 ore, il vincitore è stata un'idea chiamata [Galaxy Esplora](galaxy-explorer.md).

Andy Zibits, il lead art sul progetto e Karim Luccin, tecnico del grafico del team, parlano la collaborazione tra l'arte e sviluppo che ha portato alla creazione di una rappresentazione accurata e interattiva di galaxy le missioni nello Galaxy Explorer.

## <a name="the-tech"></a>Le tecnologie innovative

[Il nostro team](galaxy-explorer.md#meet-the-team) - effettuata backup di due finestre di progettazione, tre sviluppatori, quattro alle creazioni degli artisti, un producer e un tester, aveva sei settimane per creare un'app completamente funzionale che consente agli utenti di apprendere ed esplorare il vastness e bellezza del nostro Galaxy missioni nello spazio.

Volevamo sfruttare appieno la capacità di eseguire il rendering di oggetti 3D direttamente nello spazio di vita, in modo che abbiamo deciso di che voler creare un realistico galaxy dall'aspetto professionale in cui le persone sarebbe in grado di eseguire lo zoom avanti nella chiusura e vedere i singoli stelle, ognuno nella propria traiettorie HoloLens .

La prima settimana di sviluppo, ci siamo inventati alcuni obiettivi per la rappresentazione di Galaxy le missioni nello spazio: È necessario avere profondità, lo spostamento e l'aspetto volumetrico, completa di stelle che risulterebbe d'aiuto creano la forma del galaxy.

Il problema con la creazione di un'animazione galaxy con miliardi di stelle era che il numero di elementi singoli che necessitano di aggiornamento potrebbe risultare troppo grande per ogni fotogramma per HoloLens animare l'utilizzo della CPU. La nostra soluzione coinvolta una combinazione complessa di arte e scienza.

## <a name="behind-the-scenes"></a>Dietro le quinte

Per consentire agli utenti di esplorare i singoli stelle, è stato il primo passaggio per scoprire quanti particelle è stato possibile eseguire il rendering in una sola volta.

### <a name="rendering-particles"></a>Il rendering di particelle

CPU corrente sono ideali per l'elaborazione di attività seriali e fino a qualche attività in parallelo in una sola volta (a seconda del numero di core hanno), ma le GPU sono molto più efficaci per l'elaborazione di migliaia di operazioni in parallelo. Tuttavia, perché in genere non condividono la stessa memoria CPU, lo scambio di dati tra CPU <> GPU può diventare rapidamente un collo di bottiglia. La soluzione consisteva nel rendere un galaxy sulla GPU e avesse durata (TTL) completamente nella GPU.

Test di stress abbiamo iniziato con migliaia di particelle punto in vari modelli. Ciò ha permesso di ottenere il galaxy su HoloLens per vedere cosa ha funzionato e cosa non è stato.

### <a name="creating-the-position-of-the-stars"></a>Creazione di posizione delle stelle

Uno dei membri del nostro team aveva già scritto la C# codice generato da stelle la loro posizione iniziale. Le stelle si trovano in un'ellisse e la loro posizione può essere descritto da (**curveOffset**, **ellipseSize**, **elevazione**) in cui **curveOffset**è l'angolo della stella lungo l'ellisse **ellipseSize** è la dimensione dell'ellisse lungo X e Z e l'elevazione appropriata della stella all'interno di galaxy l'elevazione dei privilegi. Di conseguenza, possiamo creare un buffer ([ComputeBuffer di Unity](http://docs.unity3d.com/ScriptReference/ComputeBuffer.html)) che verrebbe inizializzata con ogni attributo star e inviarlo nella GPU in cui attivarlo per il resto dell'esperienza. Per disegnare il buffer, usiamo [DrawProcedural di Unity](http://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) che consente di eseguire uno shader (codice di una GPU) in un set arbitrario di punti senza la necessità di una mesh effettiva che rappresenta il galaxy:

**CPU:**




```
GraphicsDrawProcedural(MeshTopology.Points, starCount, 1);
```

**GPU:**




```
v2g vert (uint index : SV_VertexID)
{

 // _Stars is the buffer we created that contains the initial state of the system
 StarDescriptor star = _Stars[index];
 …

}
```

Abbiamo iniziato con modelli circolari non elaborati con migliaia di particelle. Questo ci ha offerto l'avevamo bisogno che è stato possibile gestire molti particelle ed eseguirlo alle velocità del ad alte prestazioni, ma non è stato soddisfatti con la forma complessiva di galaxy della prova. Per migliorare la forma, abbiamo provato diversi modelli e i sistemi particellari con rotazione. Questi sono stati inizialmente promettenti perché il numero di particelle e delle prestazioni è rimasto coerenza, ma la forma ha funzionato in prossimità del centro e le stelle emettesse una verso l'esterno che non era realistico. Ci serviva un'emissione che consente di modificare l'ora e hanno le particelle spostare realisticamente, ciclo mai più da vicino al centro della finestra di galaxy.

![Abbiamo provato diversi modelli e i sistemi particellari ruotato, simili ai seguenti.](images/galaxy-patterns-500px.png)

Abbiamo provato diversi modelli e i sistemi particellari ruotato, simili ai seguenti.

Il nostro team ha qualche ricerca sulla funzione galassie modo e abbiamo effettuato un sistema particellare personalizzato in modo specifico per il galaxy in modo che è stato possibile spostare le particelle sui puntini di sospensione in base "[teoria wave densità](https://en.wikipedia.org/wiki/Density_wave_theory)," quale theorizes che i rami di un Galaxy sono aree di un aumento della densità ma in continuo mutamento, costante, ad esempio un blocco del traffico. Risulta stabile e affidabile, ma gli asterischi vengono effettivamente spostati da e verso i rami durante lo spostamento lungo i rispettivi puntini di sospensione. Nel nostro sistema, le particelle mai presenti sulla CPU, ovvero si generano le schede e orientare tutto su GPU, in modo che l'intero sistema è stato semplicemente iniziale + tempo. Avanzata simile al seguente:

![Progressione di sistema di particelle con rendering GPU](images/spiral-galaxy-arms-500px.jpg)

Progressione di sistema di particelle con rendering GPU


Una volta sufficiente puntini di sospensione vengono aggiunti e configurati per ruotare, i galassie ha iniziato a form "tratti" in cui eseguire la convergenza lo spostamento di stelle. La spaziatura delle stelle lungo ogni percorso ellittico sono stata assegnata casualità e ogni stella ha ottenuto un po' di casualità posizionali aggiunto. Ciò creato una distribuzione professionale molto più naturale della forma a stella di spostamento e la gestione risorse di Azure. Infine, è stata aggiunta la possibilità colore unità in base alla distanza dal centro.

### <a name="creating-the-motion-of-the-stars"></a>Creare il movimento delle stelle

Per animare il movimento a stella generale, è necessario per aggiungere un angolo di costante per ogni fotogramma e ottenere lo spostamento lungo i puntini di sospensione in modo costante radiale stelle. Questo è il motivo principale per l'utilizzo **curveOffset**. Non è tecnicamente corretto come stelle verranno migrate più rapidamente ai lati lungo dei puntini di sospensione, ma il movimento generale ritenuto valido.

![Stelle passare più rapidamente l'arco di tempo, più lento sui bordi.](images/ellipse-movement.jpg)

Stelle passare più rapidamente l'arco di tempo, più lento sui bordi.


Con questo, ogni star è completamente descritto da (**curveOffset**, **ellipseSize**, **l'elevazione dei privilegi**, **Age**) in cui **Age** è un accumulo del tempo totale trascorso dal momento che è stata caricata la scena.




```
float3 ComputeStarPosition(StarDescriptor star)
{

  float curveOffset = star.curveOffset + Age;
  
  // this will be coded as a “sincos” on the hardware which will compute both sides
  float x = cos(curveOffset) * star.xRadii;
  float z = sin(curveOffset) * star.zRadii;
   
  return float3(x, star.elevation, z);
  
}
```

Ciò ha permesso di generare decine di migliaia di stelle una sola volta all'inizio dell'applicazione, quindi viene aggiunta un'animazione di un set di stelle lungo le curve stabilite un. Poiché tutti gli elementi nella GPU, il sistema è possibile aggiungere un'animazione di tutte le stelle in parallelo senza costi aggiuntivi per la CPU.

![Ecco l'aspetto quando disegnare quadrati vuoti.](images/drawing-white-quads-300px.jpg)

Ecco l'aspetto quando disegnare quadrati vuoti.



Per rendere ogni viso quad-la fotocamera, abbiamo utilizzato un geometry shader per trasformare ogni posizione a stella a un rettangolo sullo schermo che conterrà la stella trama 2D.

![A forma di rombo anziché quadrati.](images/drawing-white-quads-300px.jpg)

A forma di rombo anziché quadrati.


Perché volevamo limitare il caricamento (numero di volte in cui verrà elaborato un pixel), per quanto possibile, viene ruotata i quadrati in modo che hanno meno si sovrappongono.

### <a name="adding-clouds"></a>Aggiunta di cloud

Esistono diversi modi per ottenere una visione volumetrica con particelle, ovvero dal raggio marching all'interno di un volume al disegno di particelle tanti possibili per simulare un cloud. Raggio in tempo reale marching stava per essere troppo costoso e complesso all'autore, quindi è un primo tentativo di creazione di un sistema di computer impostore usando un metodo per le foreste per il rendering nei giochi, con molte immagini 2D di alberi rivolta alla fotocamera. Quando si esegue questa operazione in un gioco, è possibile disporre le trame di alberi viene eseguito il rendering da una fotocamera che ruota intorno a salvare tutte le immagini e in fase di esecuzione per ogni scheda billboard, selezionare l'immagine che corrisponde alla direzione di visualizzazione. Questo non funziona anche quando le immagini sono vntana. La differenza tra l'occhio del lettore a sinistra e l'occhio del lettore a destra fare in modo che è necessario un risoluzione più alta, altrimenti solo sembra semplice, un alias, o ripetitivi.

Il secondo tentativo, abbiamo provato con particelle tanti possibili. Gli oggetti visivi migliori sono stati raggiunti quando si modo additivo disegnata particelle e li sfocata prima di aggiungerli alla scena. I tipici problemi con l'approccio erano correlati a quanti particelle è stato possibile disegnare in una sola volta e area si occupava mantenendo al tempo stesso 60fps quanto dello schermo. L'immagine risultante per ottenere questo cloud sente sfocatura è in genere un'operazione molto costosa.

![Senza la trama, questo è ciò che si presenta come il cloud con opacità % 2.](images/clouds-without-texture-300px.jpg)

Senza la trama, questo è ciò che si presenta come il cloud con opacità % 2.



Additive in corso e una quantità elevata di essi significa che avremmo diversi quadrati uno sopra l'altro, ombreggiatura ripetutamente lo stesso pixel. Al centro della finestra di galaxy, lo stesso pixel contiene centinaia di quadrati sopra l'altra e ciò ha un costo elevato quando viene eseguita a schermo intero.

In questo cloud schermo intero e il tentativo di sfocatura li sarebbe stata una cattiva idea, ma che si è deciso di lasciare l'hardware il lavoro per noi.

### <a name="a-bit-of-context-first"></a>Prima di tutto un bit del contesto

Quando si usano le trame in un gioco per le dimensioni della trama corrisponderanno raramente l'area in cui si vuole usarlo in, ma è possibile usare un tipo diverso di filtro per ottenere la scheda grafica per interpolare il colore dai pixel della trama della trama ([filtraggio della trama<C3/>). Il filtro che ci interessa sia [bilineare](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx) che calcola il valore di qualsiasi pixel usando il 4 vicini più prossimi.

![Originale prima dell'applicazione di filtri](images/texture-1.png)

![Risultato dopo il filtro](images/texture-2.png)

Utilizzo di questa proprietà, noteremo che ogni volta che si tenta di disegnare una trama in un'area raddoppiata big data, consente di sfocare il risultato.

Invece di rendering in modalità schermo intero e perdere tali millisecondi preziosi che è stato possibile impiegare una notevole per qualcos'altro, si esegue il rendering di una versione di piccole dimensioni dello schermo. Quindi, copiare questa trama e estendendolo in base a un fattore pari a 2 diverse volte, otteniamo a schermo intero durante la sfocatura il contenuto del processo.

![x3 ingrandire indietro a risoluzione completa.](images/galaxy-resolutions-300px.png)

x3 ingrandire indietro a risoluzione completa.



Ciò ha permesso di ottenere la parte cloud con solo una frazione del costo originale. Anziché aggiungere cloud nella risoluzione massima, abbiamo solo paint 1/64th dei pixel e semplicemente allungare la trama al ad alta risoluzione.

![A sinistra, con una fascia alta parlino da 1/l'8 a risoluzione completa. e a destra, con 3 aumentare con potenza di 2.](images/stars-upscaled-300px.jpg)

A sinistra, con una fascia alta parlino da 1/l'8 a risoluzione completa. e a destra, con 3 aumentare con potenza di 2.


Si noti che il tentativo di passare dal 1/64th le dimensioni per la versione completa delle dimensioni in un'unica operazione risulterebbe completamente diverse, come la scheda grafica sarebbe comunque di usare 4 pixel nel nostro programma di installazione per evidenziare un'area più grande e avviare gli elementi da visualizzare.

Quindi, se si aggiungono stelle risoluzione completa con schede più piccole, otteniamo il completo galaxy:

![Quasi il risultato finale del rendering galaxy utilizzando stelle ad alta risoluzione](images/full-galaxy-500px.png)

Dopo che è stato sulla strada giusta con la forma, è stato aggiunto un livello di cloud, eseguire lo swapping dei punti temporanei con quelli abbiamo disegnato Photoshop e aggiungere alcuni colori aggiuntivi. Il risultato è un Galaxy missioni nell'arte ed entrambi i team di tecnici ritenevano bene e soddisfa gli obiettivi di profondità, volume e di movimento, tutto senza sovraccaricare la CPU.

![Il finale Galaxy missioni nello spazio 3D.](images/final-galaxy-500px.jpg)

Il finale Galaxy missioni nello spazio 3D.


### <a name="more-to-explore"></a>Informazioni di esplorazione

Abbiamo reso open-source il codice per l'app Esplora Galaxy e averlo reso disponibile nel [GitHub](https://github.com/Microsoft/GalaxyExplorer) agli sviluppatori di compilare.

Vuoi ottenere informazioni più dettagliate del processo di sviluppo per Galaxy Explorer? Estrae tutti gli aggiornamenti di progetto precedenti sul [canale YouTube di Microsoft HoloLens](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL).

## <a name="about-the-authors"></a>Informazioni sugli autori

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="Picture of Karim Luccin at his desk" width="60" height="60" src="images/karim-thumb.jpg" /></td>
<td style="border:0"><b>Karim Luccin</b> è un Software Engineer e un appassionato di oggetti visivi fantasiosi. È stato il tecnico della grafica per Galaxy Explorer.</td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Photo of art lead Andy Zibits" width="60" height="60" src="images/andy-avatar.png" /></td>
<td style="border:0"><b>Andy Zibits</b> è un appassionato di Lead arte e lo spazio che ha gestito il team di modellazione 3D per Galaxy Explorer e ritenuta per particelle ancora più.</td>
</tr>
</table>


## <a name="see-also"></a>Vedere anche
* [Esplora Galaxy su GitHub](https://github.com/Microsoft/GalaxyExplorer)
* [Aggiornamenti di progetto Galaxy Explorer su YouTube](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)

---
title: Case Study-creazione di una galassia in realtà mista
description: Prima che Microsoft HoloLens spedito, abbiamo chiesto al nostro community di sviluppatori quale tipo di app vorrebbero vedere un'esperienza di Team Build interna per il nuovo dispositivo. Sono state condivise più di 5000 idee e dopo un sondaggio Twitter di 24 ore, il vincitore era un'idea denominata "Galaxy Explorer".
author: karimluccin
ms.author: kaluccin
ms.date: 03/21/2018
ms.topic: article
keywords: Galaxy Explorer, HoloLens, realtà mista di Windows, Condividi la tua idea case study
ms.openlocfilehash: f13395250c8a73718408c051ab95d2ec4bf62014
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278179"
---
# <a name="case-study---creating-a-galaxy-in-mixed-reality"></a>Case Study-creazione di una galassia in realtà mista

Prima che Microsoft HoloLens spedito, abbiamo chiesto al nostro community di sviluppatori quale tipo di app vorrebbero vedere un'esperienza di Team Build interna per il nuovo dispositivo. Sono state condivise più di 5000 idee e dopo un sondaggio Twitter di 24 ore, il vincitore era un'idea denominata [Galaxy Explorer](galaxy-explorer.md).

Andy Zibits, il responsabile dell'arte del progetto e Karim Luccin, il tecnico di grafica del team, illustrano il lavoro di collaborazione tra l'arte e la progettazione, che hanno portato alla creazione di una rappresentazione accurata e interattiva della galassia del modo lattiginoso in Galaxy Explorer.

## <a name="the-tech"></a>Il Tech

Il [nostro team](galaxy-explorer.md#meet-the-team) , composto da due progettisti, tre sviluppatori, quattro artisti, un produttore e un tester, aveva sei settimane per creare un'app completamente funzionante che consentiva agli utenti di apprendere ed esplorare la vastità e la bellezza della nostra galassia lattiginosa.

Volevamo sfruttare appieno la capacità di HoloLens di eseguire il rendering degli oggetti 3D direttamente nello spazio di lavoro, quindi abbiamo deciso di voler creare una galassia realistica in cui le persone sarebbero in grado di eseguire lo zoom avanti e visualizzare le singole stelle, ognuna sulle proprie traiettorie.

Nella prima settimana dello sviluppo sono stati introdotti alcuni obiettivi per la rappresentazione della galassia del modo lattiginoso: era necessario disporre di profondità, spostamento e sensazione volumetrica, pieno di stelle che consentivano di creare la forma della galassia.

Il problema della creazione di una galassia animata con miliardi di stelle consisteva nel fatto che il numero di singoli elementi che necessitano di aggiornamento sarebbe troppo grande per ogni fotogramma per HoloLens per l'animazione con la CPU. La nostra soluzione comprendeva una complessa combinazione di arte e scienza.

## <a name="behind-the-scenes"></a>Dietro le quinte

Per consentire agli utenti di esplorare le singole stelle, il primo passaggio consiste nel determinare il numero di particelle di cui è possibile eseguire il rendering in una sola volta.

### <a name="rendering-particles"></a>Rendering di particelle

Le CPU correnti sono molto utili per l'elaborazione di attività seriali e fino ad alcune attività parallele contemporaneamente (a seconda del numero di core presenti), ma le GPU sono molto più efficienti nell'elaborazione di migliaia di operazioni in parallelo. Tuttavia, poiché in genere non condividono la stessa memoria della CPU, lo scambio di dati tra CPU < > GPU può diventare rapidamente un collo di bottiglia. La soluzione è stata quella di creare una galassia sulla GPU, che doveva vivere completamente sulla GPU.

Sono stati avviati test di stress con migliaia di particelle puntiformi in vari modelli. Questo ci ha consentito di ottenere la galassia in HoloLens per vedere cosa ha funzionato e cosa non è stato fatto.

### <a name="creating-the-position-of-the-stars"></a>Creazione della posizione delle stelle

Uno dei membri del team ha già scritto il C# codice che genera stelle nella posizione iniziale. Le stelle si trovano su un'ellisse e la loro posizione può essere descritta da (**curveOffset**, **ellipseSize**, **elevazione**) dove **curveOffset** è l'angolo della stella lungo l'ellisse, **ellipseSize** è la dimensione dell'ellisse lungo X e Z ed elevazione dell'elevazione corretta della stella all'interno della galassia. In questo modo, è possibile creare un buffer ([ComputeBuffer di Unity](https://docs.unity3d.com/ScriptReference/ComputeBuffer.html)) che verrebbe inizializzato con ogni attributo Star e lo invierà alla GPU in cui risiederà per il resto dell'esperienza. Per creare questo buffer, viene usato [DrawProcedural di Unity](https://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) che consente l'esecuzione di uno shader (codice su una GPU) in un set arbitrario di punti senza avere una mesh effettiva che rappresenti la galassia:

**CPU**




```
GraphicsDrawProcedural(MeshTopology.Points, starCount, 1);
```

**GPU**




```
v2g vert (uint index : SV_VertexID)
{

 // _Stars is the buffer we created that contains the initial state of the system
 StarDescriptor star = _Stars[index];
 …

}
```

Abbiamo iniziato con modelli circolari non elaborati con migliaia di particelle. Questo ci ha permesso di provare a gestire molte particelle ed eseguirle a velocità elevate, ma non è stata soddisfatta la forma complessiva della galassia. Per migliorare la forma, abbiamo provato a usare diversi modelli e sistemi particellari con rotazione. Inizialmente provenivano promesse, perché il numero di particelle e le prestazioni rimanevano coerenti, ma la forma si è interrotta in prossimità del centro e le stelle venivano emesse in modo esterno e non realistico. Avevamo bisogno di una trasmissione che ci consentisse di manipolare il tempo e far muovere le particelle in modo realistico, scorrendo sempre più vicino al centro della galassia.

![Sono stati tentati diversi modelli e sistemi particellari ruotati, come questi.](images/galaxy-patterns-500px.png)

Sono stati tentati diversi modelli e sistemi particellari ruotati, come questi.

Il nostro team ha eseguito alcune ricerche sul funzionamento delle galassie e abbiamo creato un sistema particellare personalizzato appositamente per la galassia, in modo da poter spostare le particelle sui puntini di sospensione in base alla "[teoria della densità dell'onda](https://en.wikipedia.org/wiki/Density_wave_theory)", che ipotizza che le braccia di una galassia siano aree di densità più elevata, ma in un flusso costante, ad esempio una Jam del traffico. Sembra stabile e uniforme, ma le stelle sono in realtà spostate in e fuori dalle braccia mentre si spostano lungo i rispettivi ellissi. Nel nostro sistema, le particelle non sono mai presenti sulla CPU: le schede vengono generate e ne vengono orientate tutte sulla GPU, quindi l'intero sistema è semplicemente stato iniziale + tempo. Questa operazione è stata avanzata in questo modo:

![Progressione del sistema particellare con rendering GPU](images/spiral-galaxy-arms-500px.jpg)

Progressione del sistema particellare con rendering GPU


Una volta aggiunti i puntini di sospensione sufficienti e impostati per la rotazione, le galassie iniziano a formare "braccia" dove lo spostamento delle stelle converge. Alla spaziatura delle stelle lungo ogni percorso ellittico è stato assegnato un certo grado di casualità e ogni stella ha aggiunto un bit di casualità posizionale. Questo ha creato una distribuzione di aspetto molto più naturale del movimento a stella e della forma ARM. Infine, è stata aggiunta la possibilità di guidare il colore in base alla distanza dal centro.

### <a name="creating-the-motion-of-the-stars"></a>Creazione del movimento delle stelle

Per animare il movimento a stella generale, è necessario aggiungere un angolo costante per ogni fotogramma e ottenere le stelle che si spostano lungo i puntini di sospensione a una velocità radiale costante. Questo è il motivo principale per l'uso di **curveOffset**. Questa operazione non è tecnicamente corretta perché le stelle si muovono più velocemente lungo i lati lunghi dei puntini di sospensione, ma il movimento generale si è ritenuto positivo.

![Le stelle si muovono più velocemente nell'arco lungo, più lentamente sui bordi.](images/ellipse-movement.jpg)

Le stelle si muovono più velocemente nell'arco lungo, più lentamente sui bordi.


A tale scopo, ogni stella viene descritta in modo completo da (**curveOffset**, **ellipseSize**, **Elevation**, **Age**) in cui **Age** è un accumulo del tempo totale trascorso dal momento in cui la scena è stata caricata.




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

Questo ci ha permesso di generare decine di migliaia di stelle una volta all'inizio dell'applicazione, quindi abbiamo animato un set di stelle a un unico lungo le curve stabilite. Poiché tutti gli elementi sono sulla GPU, il sistema può animare tutte le stelle in parallelo senza costi aggiuntivi per la CPU.

![Ecco come appare quando si disegnano i quad bianchi.](images/drawing-white-quads-300px.jpg)

Ecco come appare quando si disegnano i quad bianchi.



Per fare in modo che ogni Quad faccia la fotocamera, abbiamo usato un geometry shader per trasformare ogni posizione a stella in un rettangolo 2D sullo schermo che conterrà la trama a stella.

![Diamanti anziché quad.](images/drawing-white-quads-300px.jpg)

Diamanti anziché quad.


Poiché si desiderava limitare il numero di volte in cui un pixel verrà elaborato, il più possibile è stato ruotato in modo da ottenere una minore sovrapposizione.

### <a name="adding-clouds"></a>Aggiunta di cloud

Esistono diversi modi per ottenere un senso volumetrico con le particelle, da Ray che si trova all'interno di un volume per disegnare il maggior numero possibile di particelle per simulare un cloud. La marcia in tempo reale di un raggio era troppo costosa e difficile da creare, quindi abbiamo prima provato a creare un sistema impostore usando un metodo per il rendering delle foreste nei giochi, con numerose immagini 2D di alberi rivolte alla fotocamera. Quando si esegue questa operazione in un gioco, è possibile eseguire il rendering di trame di alberi da una fotocamera che ruota, salvare tutte le immagini e in fase di esecuzione per ogni scheda del tabellone, selezionare l'immagine che corrisponde alla direzione di visualizzazione. Questa operazione non funziona anche quando le immagini sono ologrammi. La differenza tra l'occhio sinistro e l'occhio destro lo rende, in modo che sia necessaria una risoluzione molto più elevata, in caso contrario si tratta semplicemente di un aspetto Flat, con alias o ripetitivo.

Al secondo tentativo, abbiamo provato a ottenere il maggior numero possibile di particelle. Gli oggetti visivi migliori sono stati realizzati quando sono state apportate in modo additivo le particelle e sono state sfocate prima di aggiungerle alla scena. I problemi tipici di questo approccio sono correlati al numero di particelle che è possibile creare in una sola volta e alla quantità di spazio dello schermo analizzate mantenendo comunque 60fps. La sfocatura dell'immagine risultante per ottenere questa sensazione di cloud era in genere un'operazione molto costosa.

![Senza texture, questo è l'aspetto dei cloud con opacità del 2%.](images/clouds-without-texture-300px.jpg)

Senza texture, questo è l'aspetto dei cloud con opacità del 2%.



Il fatto di essere additivi e avere molti di essi significa che ci saranno più quadre tra loro, ombreggiando ripetutamente lo stesso pixel. Al centro della galassia, lo stesso pixel presenta centinaia di quadre tra loro e questo ha comportato un costo enorme quando viene eseguito a schermo intero.

L'esecuzione di cloud a schermo intero e il tentativo di sfocarli sarebbe stata una pessima idea, quindi abbiamo deciso di lasciare che l'hardware eseguisse il lavoro per noi.

### <a name="a-bit-of-context-first"></a>Prima un po' di contesto

Quando si usano le trame in un gioco, le dimensioni della trama corrisponderanno raramente all'area in cui si vuole usarlo, ma è possibile usare un tipo diverso di filtro della trama per ottenere la scheda grafica per l'interpolazione del colore desiderato dai pixel della trama ([filtro della trama](https://msdn.microsoft.com/library/dn642451.aspx)). Il filtraggio che interessa è il [filtraggio bilineare](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx) che consente di calcolare il valore di qualsiasi pixel usando i 4 adiacenti più vicini.

![Originale prima del filtro](images/texture-1.png)

![Risultato dopo il filtro](images/texture-2.png)

Utilizzando questa proprietà, si noterà che ogni volta che si tenta di creare una trama in un'area con una dimensione doppia, il risultato viene offuscato.

Anziché eseguire il rendering a schermo intero e perdere questi preziosi millisecondi, possiamo passare a un'altra versione dello schermo. Quindi, copiando questa trama e inserendola per un fattore di due volte, viene visualizzata una schermata a schermo intero, mentre il contenuto del processo viene offuscato.

![la scalabilità di X3 torna alla risoluzione completa.](images/galaxy-resolutions-300px.png)

la scalabilità di X3 torna alla risoluzione completa.



Questo ci ha consentito di ottenere la parte cloud con solo una frazione del costo originale. Anziché aggiungere i cloud alla risoluzione completa, si dipinge solo 1/64 dei pixel e si limita a riportare la trama alla risoluzione completa.

![Left, con scalabilità da 1/8 a risoluzione completa; e a destra, con 3 scalabilità usando la potenza di 2.](images/stars-upscaled-300px.jpg)

Left, con scalabilità da 1/8 a risoluzione completa; e a destra, con 3 scalabilità usando la potenza di 2.


Si noti che il tentativo di passare da 1/64 dimensioni a tutte le dimensioni in un solo passaggio avrebbe un aspetto completamente diverso, in quanto la scheda grafica utilizzerebbe comunque 4 pixel nella configurazione per ombreggiare un'area più grande e iniziare a visualizzare gli artefatti.

Quindi, se si aggiungono stelle a risoluzione completa con schede più piccole, si ottiene la galassia completa:

![Risultato finale del rendering Galaxy con le stelle a risoluzione completa](images/full-galaxy-500px.png)

Una volta completata la forma, abbiamo aggiunto un livello di cloud, abbiamo scambiato i punti temporanei con quelli che abbiamo disegnato in Photoshop e abbiamo aggiunto altro colore. Il risultato è un metodo lattiginoso, che i nostri team di progettazione e di ingegneria si sono ritenuti bravi a raggiungere i nostri obiettivi, senza sovraccaricare la CPU.

![Il nostro finale della galassia per la mungitura in 3D.](images/final-galaxy-500px.jpg)

Il nostro finale della galassia per la mungitura in 3D.


### <a name="more-to-explore"></a>Altre informazioni da esplorare

Il codice per l'app Galaxy Explorer è stato aperto e reso disponibile su [GitHub](https://github.com/Microsoft/GalaxyExplorer) per consentire agli sviluppatori di eseguire la compilazione.

Si è interessati a trovare altre informazioni sul processo di sviluppo per Galaxy Explorer? Scopri tutti gli aggiornamenti del progetto precedenti sul [canale Microsoft HoloLens YouTube](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL).

## <a name="about-the-authors"></a>Informazioni sugli autori

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="Picture of Karim Luccin at his desk" width="60" height="60" src="images/karim-thumb.jpg" /></td>
<td style="border:0"><b>Karim Luccin</b> è un tecnico di software e appassionato di oggetti visivi. Era il tecnico di grafica per Galaxy Explorer.</td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Photo of art lead Andy Zibits" width="60" height="60" src="images/andy-avatar.png" /></td>
<td style="border:0"><b>Andy Zibits</b> è un responsabile artistico e un appassionato di spazio che ha gestito il team di modellazione 3D per Galaxy Explorer e ha combattuto un numero ancora maggiore di particelle.</td>
</tr>
</table>


## <a name="see-also"></a>Vedere anche
* [Galaxy Explorer su GitHub](https://github.com/Microsoft/GalaxyExplorer)
* [Aggiornamenti del progetto di Galaxy Explorer in YouTube](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)

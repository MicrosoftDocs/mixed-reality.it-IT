---
title: 'Case Study: uso del piano di stabilizzazione per ridurre la turbolenza olografica'
description: Uso del piano di stabilizzazione per ridurre la turbolenza olografica
author: bstrukus
ms.author: bestruku
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, ologrammi, stabilizzazione, case study
ms.openlocfilehash: d31f3128ba10d6fc7bd57f3068db3dd16b23f901
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436440"
---
# <a name="case-study---using-the-stabilization-plane-to-reduce-holographic-turbulence"></a>Case Study: uso del piano di stabilizzazione per ridurre la turbolenza olografica

L'uso di ologrammi può risultare complesso. Il fatto che sia possibile spostarsi nello spazio e visualizzare gli ologrammi da tutti gli angoli diversi fornisce un livello di immersione che non è possibile ottenere con un normale schermo del computer. Mantenere questi ologrammi e sembrare realistici è un'impresa tecnica eseguita sia dall'hardware Microsoft HoloLens che dalla progettazione intelligente di app olografiche.

## <a name="the-tech"></a>Il Tech

Per far sembrare gli ologrammi come se condividessero effettivamente lo spazio con l'utente, è necessario eseguire il rendering in modo corretto, senza separazione dei colori. Questa operazione viene eseguita, in parte, dalla tecnologia incorporata nell'hardware HoloLens, che mantiene gli ologrammi ancorati su ciò che viene chiamato un [piano di stabilizzazione](hologram-stability.md#reprojection).

Un piano è definito da un punto e da un normale, ma poiché si vuole che il piano faccia sempre fronte alla fotocamera, è sufficiente impostare il punto del piano. Possiamo indicare a HoloLens quale punto di concentrarsi sull'elaborazione per mantenendo tutti gli elementi ancorati e stabili, ma come impostare questo punto di interesse è specifico dell'app e può creare o interrompere l'app a seconda del contenuto.

In breve, gli ologrammi funzionano meglio quando il piano di stabilizzazione viene applicato correttamente, ma ciò che significa effettivamente dipende dal tipo di applicazione che si sta creando. Verrà ora esaminato il modo in cui alcune delle app attualmente disponibili per HoloLens affrontano questo problema.

## <a name="behind-the-scenes"></a>Dietro le quinte

Quando si sviluppano le app seguenti, si è notato che, quando il piano non è stato usato, gli oggetti potrebbero ondeggiare quando la testa è stata spostata e si vedrà la separazione dei colori con movimento rapido o ologramma. Nel corso dell'intervallo di tempo di sviluppo, abbiamo appreso attraverso la versione di valutazione e l'errore come usare al meglio il piano di stabilizzazione e come progettare le nostre app per risolvere i problemi che non possono essere corretti.

### <a name="galaxy-explorer-stationary-content-3d-interactivity"></a>Galaxy Explorer: contenuto fisso, interattività 3D

[Galaxy Explorer](galaxy-explorer.md) include due elementi principali nella scena: la visualizzazione principale del contenuto celeste e la piccola barra degli strumenti dell'interfaccia utente che segue lo sguardo. Per la logica di stabilizzazione, viene esaminato il modo in cui si interseca il vettore di sguardi corrente in ogni frame per determinare se si verificano elementi in un livello di collisione specificato. In questo caso, i livelli a cui si è interessati sono i pianeti, quindi se lo sguardo cade su un pianeta, il piano di stabilizzazione viene inserito. Se nessuno degli oggetti nel livello di collisione di destinazione viene raggiunto, l'app utilizza un livello secondario "piano B". Se non viene preso in osservazione, il piano di stabilizzazione viene mantenuto alla stessa distanza che era quando si guardava il contenuto. Gli strumenti dell'interfaccia utente vengono esclusi come destinazione del piano poiché è stato trovato il salto tra quasi e molto ridotto la stabilità della scena complessiva.

La progettazione di Galaxy Explorer si presta bene a garantire la stabilità e la riduzione dell'effetto della separazione dei colori. L'utente è invitato a esplorare e a orbitare il contenuto, anziché spostarsi da un lato all'altro, e i pianeti sono sufficientemente lenti per evitare che la separazione dei colori sia evidente. Viene inoltre mantenuta una costante 60 FPS, che consente di impedire che si verifichi la separazione dei colori.

Per eseguire questa verifica, cercare un file denominato LSRPlaneModifier.cs nel [codice di Galaxy Explorer su GitHub](https://github.com/Microsoft/GalaxyExplorer/tree/master/Assets/Scripts/Utilities).

### <a name="holostudio-stationary-content-with-a-ui-focus"></a>HoloStudio: contenuto stazionario con lo stato attivo dell'interfaccia utente

In HoloStudio si dedica la maggior parte del tempo alla ricerca dello stesso modello su cui si sta lavorando. Lo sguardo non sposta una quantità significativa, tranne quando si seleziona un nuovo strumento o si vuole spostarsi nell'interfaccia utente, in modo da poter garantire la logica di impostazione del piano. Quando si esamina l'interfaccia utente, il piano è impostato su qualsiasi elemento dell'interfaccia utente a cui lo sguardo si blocca. Quando si esamina il modello, il piano è una distanza impostata, corrispondente alla distanza predefinita tra l'utente e il modello.

![Il piano di stabilizzazione visualizzato in HoloStudio quando l'utente Guarda il pulsante Home](images/holostudio-stabilization-plane-500px.png)

### <a name="holotour-and-3d-viewer-stationary-content-with-animation-and-movies"></a>HoloTour e visualizzatore 3D: contenuto fisso con animazione e filmati

In HoloTour e 3D Viewer si sta esaminando un oggetto animato solitario o un filmato con effetti 3D aggiunti al suo interno. La stabilizzazione in queste app è impostata su quello che attualmente si sta visualizzando.

HoloTour impedisce anche di allontanarsi troppo dal mondo virtuale facendo in modo che venga spostato con l'utente anziché rimanere in una posizione fissa. In questo modo si garantisce che i problemi di stabilità non diventeranno abbastanza lontani dagli altri ologrammi.

![In questo esempio di HoloTour, il piano di stabilizzazione viene impostato su questo film del Pantheon di Adriano.](images/holotour-stabilization-plane-500px.jpg)

### <a name="roboraid-dynamic-content-and-environmental-interactions"></a>RoboRaid: contenuto dinamico e interazioni ambientali

L'impostazione del piano di stabilizzazione in RoboRaid è sorprendentemente semplice, sebbene sia l'app che richiede lo spostamento più improvviso. Il piano è rivolto verso l'allungamento delle pareti o degli oggetti circostanti e fluttua a una distanza fissa davanti all'utente quando si è sufficientemente lontani.

RoboRaid è stato progettato tenendo conto del piano di stabilizzazione. Il reticolo, che sposta il maggior numero da quando è bloccato, evita questo problema usando solo il rosso e il blu, che riduce al minimo l'emorragia del colore. Contiene anche un piccolo bit di profondità tra le parti, riducendo al minimo l'eventuale sanguinamento dei colori che si verificherebbe mascherando con un effetto di parallasse già previsto. I robot non si spostano molto rapidamente e passano a brevi distanze a intervalli regolari. Tendono a rimanere circa 2 metri davanti all'utente, dove la stabilizzazione è impostata per impostazione predefinita.

### <a name="fragments-and-young-conker-dynamic-content-with-environmental-interaction"></a>Frammenti e Conker giovani: contenuto dinamico con interazione ambientale

Scritto da Asobo Studio in C++, i frammenti e le Conker giovani prendono un approccio diverso per impostare il piano di stabilizzazione. I punti di interesse (PDI) sono definiti nel codice e ordinati in base alla priorità. I POIs sono contenuti nel gioco, ad esempio il modello Conker in Conker giovani, i menu, il reticolo di mira e i logo. I POIs sono intersecati dallo sguardo dell'utente e il piano è impostato sul centro dell'oggetto con la priorità più alta. Se non si verifica alcuna intersezione, il piano viene impostato sulla distanza predefinita.

I frammenti e i giovani Conker progettano anche la dispersione di troppo lontano dagli ologrammi sospendendo l'app se si passa al di fuori di ciò che è stato analizzato in precedenza come spazio di riproduzione. Di conseguenza, mantengono l'utente entro i limiti rilevati per offrire l'esperienza più stabile.

## <a name="do-it-yourself"></a>Fai da te

Se si ha un HoloLens e si vuole provare a usare i concetti illustrati, è possibile scaricare una scena di test e provare gli esercizi seguenti. Usa l'API Gizmo incorporata di Unity e consente di visualizzare la posizione in cui viene impostato il piano. Questo codice è stato usato anche per acquisire le schermate in questo case study.
1. Sincronizzare la versione più recente di [MixedRealityToolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity).
2. Aprire la scena [HoloToolkit-examples/Utilities/sceness/StabilizationPlaneSetting. Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Utilities/Scenes/StabilizationPlaneSetting.unity) .
3. Compilare e configurare il progetto generato.
4. Eseguire sul dispositivo.

### <a name="exercise-1"></a>Esercizio 1

Verranno visualizzati diversi puntini di sospensione con orientamenti diversi. In primo piano, verranno visualizzati tre puntini di profondità differenti. Toccare aria per modificare il punto su cui è impostato il piano. Per questo esercizio e per gli altri due, spostarsi nello spazio mentre si osservano i punti. Capovolgere l'intestazione a sinistra, a destra, verso l'alto e verso il basso. Avvicinarsi a e a Father da punti. Vedere come reagiscono quando il piano di stabilizzazione è impostato su destinazioni diverse.

### <a name="exercise-2"></a>Esercizio 2

A questo punto, è possibile tornare a destra fino a visualizzare due punti mobili, uno oscillante su un tracciato orizzontale e uno in un percorso verticale. Anche in questo caso, toccare aria per modificare il punto su cui è impostato il piano. Si noti che la separazione dei colori viene ridotta sul punto collegato al piano. Toccare di nuovo per usare la velocità del punto nella funzione di impostazione del piano. Questo parametro fornisce un hint a HoloLens sul movimento designato dell'oggetto. È importante capire quando usarlo, come si noterà quando la velocità viene usata in un punto, l'altro punto che lo sposti Visualizza una separazione dei colori maggiore. Tenere presente questo aspetto quando si progettano le app: la presenza di un flusso coeso al movimento degli oggetti può impedire la visualizzazione di artefatti.

### <a name="exercise-3"></a>Esercizio 3

Tornare a destra ancora una volta fino a quando non viene visualizzata una nuova configurazione di punti. In questo caso sono presenti punti nella distanza e un punto a spirale all'interno e all'esterno. Toccare aria per modificare il punto su cui è impostato il piano, alternando tra i punti nella parte posteriore e il punto in movimento. Si noti che l'impostazione della posizione del piano e della velocità su quella del punto di spirale rende gli artefatti visibili ovunque.

**Consigli**
* Semplificare la logica di impostazione del piano. Come si è visto, non sono necessari algoritmi di impostazione del piano complessi per creare un'esperienza immersiva. Il piano di stabilizzazione è solo una parte del puzzle.
* Quando possibile, spostare sempre il piano tra le destinazioni in modo graduale. Il cambio immediato di destinazioni distanti può compromettere visivamente la scena.
* Si consiglia di disporre di un'opzione nella logica di impostazione del piano per il blocco su una destinazione molto specifica. In questo modo, se necessario, è possibile bloccare il piano su un oggetto, ad esempio un logo o una schermata del titolo.

## <a name="about-the-author"></a>Informazioni sull'autore

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Ben Strukus" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Ben Strukus</b><br>Software Engineer @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Vedi anche
* [Nozioni fondamentali 100: Introduzione a Unity](holograms-100.md)
* [Punto focale in Unity](focus-point-in-unity.md)
* [Stabilità degli ologrammi](hologram-stability.md)

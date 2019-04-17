---
title: 'Case study: uso il piano di stabilizzazione per ridurre turbolenza holographic'
description: Utilizzando il piano di stabilizzazione per ridurre turbolenza holographic
author: bstrukus
ms.author: bestruku
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, vntana, stabilizzazione, case study
ms.openlocfilehash: a084ede5f9bf3d5f058cc81ec75840e2c2e75af2
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597532"
---
# <a name="case-study---using-the-stabilization-plane-to-reduce-holographic-turbulence"></a>Case study: uso il piano di stabilizzazione per ridurre turbolenza holographic

Utilizzo di vntana può rendere difficile. Il fatto che è possibile spostare lo spazio e visualizzare il vntana da tutte le diverse angolazioni offre un livello di full immersion che non è possibile ottenere una schermata di computer normale. Conservare queste vntana nella posizione e alla ricerca realistico è una specie di tecnica a tale scopo l'hardware di Microsoft HoloLens e la progettazione di App holographic intelligente.

## <a name="the-tech"></a>Le tecnologie innovative

Per rendere vntana apparire come se venisse effettivamente condivide lo spazio con l'utente, è necessario eseguire il rendering correttamente, senza la separazione dei colori. A questo scopo, in parte, tecnologia incorporata per l'hardware di HoloLens che mantiene vntana ancorata su quelle che chiamiamo un [piano di stabilizzazione](hologram-stability.md#stabilization-plane).

Un piano è definito da un punto e una normale, ma poiché vogliamo sempre il piano per affrontare la fotocamera, siamo interessati semplicemente con l'impostazione punto del piano. È possibile indicare a HoloLens che fanno riferimento a concentrare l'attenzione l'elaborazione a tenere che tutto ancorato e stabile, ma come impostare questo punto lo stato attivo è specifico dell'applicazione e può apportare o interruzioni dell'app a seconda del contenuto.

In breve, vntana funzionamento ottimale il piano di stabilizzazione viene correttamente applicato, ma che in realtà significa che varia a seconda del tipo di applicazione che si sta creando. Diamo un'occhiata a come alcune delle App attualmente disponibili per HoloLens affrontare il problema.

## <a name="behind-the-scenes"></a>Dietro le quinte

Durante lo sviluppo di App seguenti, abbiamo notato che, quando è stata usata il piano, gli oggetti verrebbero sway quando l'inizio spostato e ci renderemo conto dei colori con head rapido o spostamenti ologramma. Nel corso dell'intervallo di tempo di sviluppo, abbiamo imparato tramite prove empiriche come progettare l'App in base a problemi che non riesce a correggere e come usare al meglio il piano di stabilizzazione.

### <a name="galaxy-explorer-stationary-content-3d-interactivity"></a>Esplora Galaxy: Contenuto stazionario, interattività 3D

[Esplora Galaxy](galaxy-explorer.md) dispone di due elementi principali della scena: La visualizzazione principale del contenuto tronco e la piccola barra degli strumenti dell'interfaccia utente che segue lo sguardo. Per la logica di stabilizzazione, vengono esaminati si interseca con l'oggetto vector corrente sguardo in ogni fotogramma per determinare se si verifica alcuna operazione su un livello di conflitto specificato. In questo caso, i livelli sono interessati sono i pianeti, in modo che lo sguardo cade un pianeta, il piano di stabilizzazione viene inserito non esiste. Se nessuno degli oggetti nel livello di collisione di destinazione vengono raggiunti, l'app Usa un livello secondario "piano B". Se non è in corso gazed a, il piano di stabilizzazione viene mantenuto alla stessa distanza com'era quando gazing il contenuto. Gli strumenti dell'interfaccia utente sono esclusi come destinazione di piano come abbiamo trovato il salto tra quasi e la stabilità della scena complessiva di riduzione.

La progettazione di Galaxy Esplora presta bene per mantenere la stabilità e ridurre l'impatto della separazione dei colori. L'utente è stimolato a camminare e orbita contenuto anziché spostarsi attraverso di esso da un lato a altro e i pianeti sono fornisce fosse sufficientemente lenta che la selezione colore non è significativa. Inoltre, viene mantenuta una costante 60 FPS, che può risultare molto utile per prevenire la separazione di colore accada.

A tale scopo in totale autonomia, cercare un file denominato LSRPlaneModifier.cs nella [codice Galaxy Explorer su GitHub](https://github.com/Microsoft/GalaxyExplorer/tree/master/Assets/Scripts/Utilities).

### <a name="holostudio-stationary-content-with-a-ui-focus"></a>HoloStudio: Contenuto fermo con un'attenzione particolare dell'interfaccia utente

In HoloStudio, si impiegano la maggior parte del tempo esaminando lo stesso modello che si sta lavorando. Lo sguardo non si sposta una quantità significativa, ad eccezione di quando si seleziona un nuovo strumento o si desidera passare l'interfaccia utente, pertanto è possibile mantenere semplice la logica di impostazione del piano. Quando si esamina l'interfaccia utente, il piano è impostato su qualsiasi elemento dell'interfaccia utente si blocchi lo sguardo. Quando si esamina il modello, il piano è una set di distanza, corrispondente con la distanza predefinita tra te e il modello.

![Il piano di stabilizzazione visualizzati in gazes HoloStudio come utente sul pulsante Home](images/holostudio-stabilization-plane-500px.png)

### <a name="holotour-and-3d-viewer-stationary-content-with-animation-and-movies"></a>HoloTour e Visualizzatore 3D: Contenuto fermo con animazione e sul film

Nel Visualizzatore 3D e HoloTour, si osservano un oggetto animato solitari o di un film con effetti 3D aggiunti sopra di esso. La stabilizzazione in queste App è impostata su tutti i valori attualmente visualizzato.

HoloTour impedisce inoltre di straying troppo lontano dal tuo mondo virtuale facendo in modo che si sposta con l'utente anziché rimanere in una posizione fissa. Ciò garantisce che non si otterranno sufficientemente grande da altri vntana per problemi di stabilità a diventare.

![In questo esempio dalla HoloTour, il piano di stabilizzazione verrebbe impostato a questo film di Pantheon di Hadrian.](images/holotour-stabilization-plane-500px.jpg)

### <a name="roboraid-dynamic-content-and-environmental-interactions"></a>RoboRaid: Interazioni di contenuto e dell'ambiente dinamiche

Impostazione piano di stabilizzazione in RoboRaid è sorprendentemente semplice, nonostante sia l'app che richiede lo spostamento più improvviso. Il piano è rivolto a rispettare le pareti o che la racchiudono gli oggetti e verrà spostata a una distanza fissa fronte quando si è sufficientemente grande da essi.

RoboRaid è stato progettato con il piano di stabilizzazione presente. Il tratteggiato, che consente di spostare più perché è bloccato in head, aggira questo usando solo red e blue riducendo al minimo eventuali installazioni di colore. Include anche una piccola parte di profondità tra le parti, riducendo al minimo eventuali smarginatura del colore che si verificano nascondendoli con un effetto di parallasse già previsto. Robot non passare molto rapidamente e possono spostarsi solo brevi distanze a intervalli regolari. Tendono a essere sempre circa 2 metri sempre a disposizione, in cui la stabilizzazione è impostata per impostazione predefinita.

### <a name="fragments-and-young-conker-dynamic-content-with-environmental-interaction"></a>I frammenti e Conker giovane: Contenuto dinamico interazione da parte dell'ambiente

Scritto da Asobo Studio nel C++, i frammenti e Young Conker adottare un approccio diverso per la configurazione del piano di stabilizzazione. I punti di interesse sono definiti nel codice e ordinati a livello di priorità. Punti di interesse sono contenuti all'interno del gioco come il modello Conker in Conker Young, menu, tratteggiato mira e logo. I punti di interesse sono intersecati dal sguardo dell'utente e il piano è impostato al centro dell'oggetto con la priorità più alta. Se si verifica alcuna intersezione, il piano è impostato per la distanza predefinita.

Progettare anche Conker Young e frammenti si straying troppo lontano dal vntana posizionando l'app se si sposta all'esterno di ciò che è stato analizzato in precedenza come spazio di gioco. Di conseguenza, di cui restare entro i limiti che si trovano a offrire l'esperienza più stabile.

## <a name="do-it-yourself"></a>Eseguire tale operazione manualmente

Se si hanno un HoloLens e si vuole sperimentare con i concetti discussi, è possibile scaricare una scena di test e provare gli esercizi seguenti. Usa gizmo predefinito di Unity API e consentono di visualizzare dove viene impostato il piano. Questo codice è stato usato anche per acquisire le schermate contenute in questo case study.
1. La versione più recente di sincronizzare [MixedRealityToolkit Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity).
2. Aprire il [HoloToolkit-Examples/Utilities/Scenes/StabilizationPlaneSetting.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Utilities/Scenes/StabilizationPlaneSetting.unity) scena.
3. Creare e configurare il progetto generato.
4. Eseguire sul dispositivo.

### <a name="exercise-1"></a>Esercizio 1

Si noterà diversi punti bianchi intorno si alla orientamenti diversi. Sempre a disposizione, si noterà sui tre puntini alla profondità diversi. Indice puntato modificare quale punto del piano è impostato su. Per questo esercizio e per gli altri due, spostarsi lo spazio, gazing in punti. Attivare l'head destra verso sinistra, freccia su e freccia giù. Spostare più prossimo a e father da punti. Vedere come si reagisce quando il piano di stabilizzazione è impostato su destinazioni diverse.

### <a name="exercise-2"></a>Esercizio 2

A questo punto, passare direttamente al fino a visualizzare due punti, lo spostamento uno oscilla avanti su un percorso orizzontale e uno in un percorso UNC verticale. Ancora una volta,-indice puntato per modificare il punto al piano è impostato su. Si noti come riscritture dei colori viene visualizzato sul punto che è connesso al piano. Toccare di nuovo per l'uso della velocità del punto nella funzione di impostazione di piano. Questo parametro fornisce un hint per HoloLens attenzione al movimento desiderata dell'oggetto. È importante sapere quando usare questa operazione, come si noterà che quando si usa velocità in un punto, l'altro punto mobile mostrerà maggiore separazione di colore. Tenere a mente quando si progettano le tue App, ovvero la presenza di un flusso coerente per il movimento degli oggetti può aiutare impedire la visualizzazione degli elementi.

### <a name="exercise-3"></a>Esercizio 3

Passare il diritto ancora una volta finché non viene visualizzata una nuova configurazione di punti. In questo caso esistono punti nella distanza e un punto del processo di gestione in ingresso e in uscita davanti a essi. Per modificare il punto al piano è impostato su, alternando tra il punto in continua evoluzione e i punti nella parte posteriore puntare l'indice. Si noti come impostando la posizione del piano e la velocità a quello del punto spirale rende gli elementi vengono visualizzati ovunque.

**Suggerimenti**
* Mantenere semplice la logica di impostazione del piano. Come si è visto, non occorre algoritmi impostazione piano complesso per rendere un'esperienza coinvolgente e concreto. Il piano di stabilizzazione è solo una parte del puzzle.
* Quando si trova in tutte le possibili, sempre spostare il piano tra le destinazioni in modo uniforme. Cambio immediatamente destinazioni distante può visivamente interrompere la scena.
* È consigliabile che un'opzione nella logica di impostazione del piano di blocco su una destinazione molto specifica. In questo modo, è possibile avere il piano di blocco su un oggetto, ad esempio una schermata del titolo o il logo, se necessario.

## <a name="about-the-author"></a>Informazioni sull'autore

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Ben Strukus" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Bruno Strukus</b><br>Software Engineer @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Vedere anche
* [Nozioni fondamentali di MR 100: Introduzione a Unity](holograms-100.md)
* [Punto di stato attivo in Unity](focus-point-in-unity.md)
* [Stabilità ologrammi](hologram-stability.md)

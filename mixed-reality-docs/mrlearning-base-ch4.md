---
title: Esercitazioni introduttive-5. Interazione con oggetti 3D
description: ''
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 29a31f794cbcda4f0c77b4e6e2d0e3c2c91dcb8c
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/01/2019
ms.locfileid: "68702018"
---
# <a name="5-interacting-with-3d-objects"></a>5. Interazione con oggetti 3D

In questa esercitazione vengono fornite informazioni sul contenuto 3D di base e sull'esperienza utente. Si apprenderà come: 
* Organizzazione di oggetti 3D come parte di una raccolta.
* Caselle di delimitazione per la manipolazione di base.
* Interazione quasi e lontano.
* Toccare e spostare i movimenti con il rilevamento manuale. 

## <a name="objectives"></a>Obiettivi

* Informazioni su come organizzare il contenuto 3D con la raccolta di oggetti Grid di MRTK
* Implementare i cubi di delimitazione
* Configurare gli oggetti 3D per la manipolazione di base-spostare, ruotare e ridimensionare
* Esplorare l'interazione da vicino e da lontano
* Informazioni sugli altri movimenti di rilevamento della mano, ad esempio la cattura e il tocco

## <a name="instructions"></a>Istruzioni

### <a name="organizing-3d-objects-in-a-collection"></a>Organizzazione di oggetti 3D in una raccolta

1. Fare clic con il pulsante destro del mouse sulla gerarchia e selezionare Crea vuoto. Viene creato un oggetto gioco vuoto. Rinominarlo in 3DObjectCollection. In questa posizione inseriremo tutti gli oggetti 3D. Assicurati che il posizionamento della raccolta sia impostato su x = 0, y = 0 e z = 0.

![Immagine lezione 4 capitolo 1 passaggio 1](images/Lesson4_Chapter1_step1im.PNG)

2. Importare gli asset BaseModule usando le stesse istruzioni per importare i pacchetti personalizzati descritti in [dalla lezione 1](mrlearning-base-ch1.md). Gli asset BaseModule includono i moduli 3D e altri script utili usati in questa esercitazione. Il pacchetto BaseModule Unity è disponibile qui:<https://github.com/Microsoft/MixedRealityLearning/releases/tag/V1.1>

3. Il prefab CoffeeCup è riconoscibile dall'icona a forma di cubo blu. Non selezionare il Coffee Cup con il cubo blu e Small white paper perché questo indica il modello 3D originale e non la prefabbricata. 

![Immagine lezione 4 capitolo 1 nota a](images/Lesson4_chapter1_noteaim.PNG)

4. Trascinare la prefabbricata Coffee Cup desiderata nell'oggetto gioco 3DObjectCollection del passaggio 1. CoffeeCup è ora un elemento figlio della raccolta.

![Immagine lezione 4 capitolo 1 passaggio 4](images/Lesson4_chapter1_step4ima.PNG)

5. Successivamente, aggiungeremo alla scena altri oggetti 3D. Di seguito sono elencati gli oggetti che aggiungeremo in questo esempio. Quando si aggiungono gli oggetti, è possibile che vengano visualizzati nella scena in diverse dimensioni. Modificare la scala di ogni modello 3D in impostazione trasformazione nel pannello di controllo. Le modifiche consigliate per questo esempio sono elencate con gli oggetti seguenti. Cercare queste parole nella casella di ricerca nel pannello del progetto e trascinare il prefabbricato dell'oggetto 3D nell'oggetto 3DObjectCollection in modo analogo al passaggio precedente. Queste raccolte di prefabbricati sono disponibili nelle risorse > BaseModuleAssets > i prefabbricati dei moduli di base
- Cercare TheModule_BaseModuleIncomplete. Trascina nella scena. Imposta i valori di ridimensionamento su x = 0.03, y = 0.03 e z = 0.03. 
- Cercare Octa_BaseModuleIncomplete. Trascina nella scena. Imposta i valori di ridimensionamento su x = 0.13, y = 0.13 e z =0.13.
- Cercare EarthCore_BaseModuleIncomplete. Trascina nella scena. Imposta i valori di ridimensionamento su x = 50.0, y = 50.0 e z = 50.0.
- Cercare Cheese_BaseModuleIncomplete. Trascina nella scena. Imposta i valori di ridimensionamento su x = 0.05, y = 0.05 e z = 0.05.
- Cercare Model_Platonic_BaseModuleIncomplete. Trascina nella scena. Imposta i valori di ridimensionamento su x = 0.13, y = 0.13 e z = 0.13.

![Immagine lezione 4 capitolo 1 passaggio 5](images/Lesson4_Chapter1_step5im.PNG)

6. Aggiungere tre cubi alla scena. Fare clic con il pulsante destro del mouse sull'oggetto 3DObjectCollection, scegliere oggetto 3D, quindi cubo. Imposta i valori di ridimensionamento su x = 0.14, y = 0.14 e z = 0.14. Ripetere questo passaggio altre due volte per creare un totale di tre cubi. In alternativa, è possibile duplicare il cubo due volte per un totale di tre cubi. Puoi anche scegliere di usare i tre prefab cubo predefiniti in Assets>BaseModuleAssets>Base Module Prefabs e selezionare GreenCube_BaseModuleIncomplete, BlueCube_BaseModuleIncomplete e OrangeCube_BaseModuleIncomplete.

![Immagine lezione 4 capitolo 1 passaggio 6](images/Lesson4_Chapter1_step6im.PNG)

7. Organizza la raccolta di oggetti in modo da formare una griglia seguendo la procedura illustrata nella [lezione 2](mrlearning-base-ch2.md) tramite la raccolta di oggetti griglia di MRTK. Fai riferimento all'immagine seguente per vedere un esempio di configurazione di oggetti in una griglia 3x3.

![Immagine lezione 4 capitolo 1 nota b](images/Lesson4_chapter1_notebim.PNG)

>Nota: È possibile notare che alcuni oggetti sono fuori centro, ad esempio gli oggetti nell'immagine precedente. Questo avviene perché i prefab o gli oggetti possono includere oggetti figlio non allineati. Puoi apportare le modifiche necessarie alla posizione dell'oggetto o dell'oggetto figlio per ottenere una griglia ben allineata.


### <a name="manipulating-3d-objects"></a>Manipolazione di oggetti 3D
1. Aggiungi la capacità di manipolare un cubo. Per aggiungere la possibilità di modificare gli oggetti 3D, eseguire le operazioni seguenti:
-   Selezionare l'oggetto 3D che si desidera modificare nella gerarchia, ovvero uno dei cubi.
-   Fare clic su Add Component. 
-   Ricerca di manipolazione.
-   Selezionare gestore di manipolazione.
-   Ripetere la ripetizione per tutti gli oggetti 3D nell'oggetto 3DObjectCollection, ma non il 3DObjectCollection stesso.
-   Verificare che tutti gli oggetti 3D dispongano di un Collider o di box Collider (Add Component > Box Collider).

![Immagine lezione 4 capitolo 2 passaggio 1](images/Lesson4_chapter2_step1im.PNG)

>Il gestore di manipolazione è un componente che consente di modificare le impostazioni relative al comportamento degli oggetti quando vengono modificate. Sono incluse la rotazione, il ridimensionamento, lo spostamento e il vincolo di spostamento su un asse specifico. 

2. Limita un cubo in modo che possa solo essere ridimensionato. Selezionare un cubo nell'oggetto 3DObjectCollection. Nel pannello Inspector, accanto a due tipi di manipolazione gestiti, fare clic sul menu a discesa e selezionare Ridimensiona. In questo modo, l'utente può modificare solo le dimensioni del cubo.

![Immagine lezione 4 capitolo 2 passaggio 2](images/Lesson4_Chapter2_step2im.PNG)

3. Modifica il colore di ogni cubo, in modo che sia possibile distinguerli. 
-   Passare al pannello del progetto e scorrere verso il basso fino a quando non viene visualizzato MixedRealityToolkit. SDK, quindi selezionarlo.
-   Selezionare la cartella asset standard.
-   Fare clic sulla cartella materiali.
-   Trascina un materiale diverso in ogni cubo. 

>Nota: puoi scegliere un colore qualsiasi per i cubi. Per questo esempio, si userà glowingcyan, glowingorange e Green. Puoi provare a usare colori diversi. Per aggiungere il colore al cubo, fare clic sul cubo che si desidera modificare, quindi trascinare il materiale nel campo Material del renderer mesh nel pannello Inspector del cubo. 

![Immagine lezione 4 capitolo 2 passaggio 3](images/Lesson4_Chapter2_step3im.PNG)

4. Selezionare un altro cubo nell'oggetto 3DObjectCollection e impostarlo in modo che lo spostamento sia vincolato a una distanza fissa dalla testa. A tale scopo, a destra di vincolo sull'etichetta di spostamento, fare clic sul menu a discesa e selezionare Correggi distanza dall'inizio. In questo modo, l'utente può spostare il cubo solo entro il proprio campo visivo. 

![Immagine lezione 4 capitolo 2 passaggio 4](images/Lesson4_chapter2_step4im.PNG)

L'obiettivo dei passaggi successivi consiste nell'abilitare l'acquisizione e l'interazione con gli oggetti 3D e l'applicazione di impostazioni di manipolazione diverse.

5. Selezionare l'oggetto Cheese, quindi fare clic su Aggiungi componente nel pannello Inspector. 

6. Eseguire una ricerca nella casella di ricerca di near interactionable, quindi selezionare lo script. Questo componente consente agli utenti di raggiungere e acquisire oggetti con le mani tracciate. Gli oggetti possono anche essere modificati a distanza, a meno che la casella di controllo Consenti disparità non sia selezionata come indicato dal cerchio verde nell'immagine seguente.

![Immagine lezione 4 capitolo 2 passaggio 6](images/Lesson4_Chapter2_step6im.PNG)

7. Aggiungere near interactionable all'oggetto Octa, all'oggetto Platonic, a Earth Core, al modulo Lunar e a Coffee Cup ripetendo i passaggi 5 e 6 in tali oggetti.

8. Rimuovi la capacità di manipolazione da lontano dall'oggetto ottaedro. A tale scopo, selezionare il Octa nella gerarchia e deselezionare la casella di controllo Consenti modifiche per la manipolazione (contrassegnato da un cerchio verde). In questo modo, gli utenti possono interagire con l'oggetto ottaedro solo direttamente usando le mani tracciate.

>Nota: per la documentazione completa del componente del gestore di manipolazione e delle relative impostazioni, vedi la [documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html).

9. Verificare che sia stato aggiunto il componente near interactionable interactionable a Earth Core, il modulo Lunar e il caffè Cup (vedere il passaggio 7).

10. Per il modulo Lunar, modificare le impostazioni del gestore delle modifiche in modo che ruoti sul centro dell'oggetto per l'interazione sia quasi che lontano, come illustrato nell'immagine seguente.

![Immagine lezione 4 capitolo 2 passaggio 10](images/Lesson4_chapter2_step10im.PNG)

11: Per Earth Core, modificare il comportamento della versione in Nothing. In questo modo, quando il nucleo di terra viene rilasciato dalla stretta dell'utente, non continua a spostarsi. 

![Immagine lezione 4 capitolo 2 passaggio 11](images/Lesson4_Chapter2_step11im.PNG)

> Nota: questa impostazione è utile per scenari come la creazione di una palla che si può lanciare. Mantenendo la velocità e la velocità angolare, il fatto che una volta rilasciata la palla continuerà a spostarsi alla velocità in cui è stata rilasciata, in modo analogo al comportamento di una palla fisica.

### <a name="adding-bounding-boxes"></a>Aggiunta di cubi di delimitazione
I cubi di delimitazione rendono più semplice e intuitiva la manipolazione degli oggetti con una mano sia per la manipolazione diretta (interazione da vicino) sia per la manipolazione basata su raggio (interazione da lontano). I rettangoli di delimitazione forniscono handle che possono essere recuperati per la scala e la rotazione di oggetti lungo un asse specifico.
>Nota: Prima di poter aggiungere un rettangolo di delimitazione a un oggetto, è necessario innanzitutto disporre di un collider sull'oggetto (ad esempio, un box Collider), come in precedenza in questa lezione. Puoi aggiungere i collisori selezionando l'oggetto e quindi, nel pannello di controllo dell'oggetto, scegliendo Add Component>Box Collider (Aggiungi componente>Collisore cubico).
>

1. Aggiungere un Collider box all'oggetto Earth Core, se non ne esiste già uno. La finestra Collider e il programma di installazione non sono necessari se si usa il prerequisito fornito nella cartella Asset modulo di base per le istruzioni fornite. Nel caso di Earth Core, è stato aggiunto il box Collider all'oggetto, node_id30, sotto il nucleo terrestre, come illustrato nell'immagine seguente. Selezionare node_id30 dalla scheda controllo dell'oggetto, fare clic su Aggiungi componente e cercare box Collider. 

![Immagine lezione 4 capitolo 3 passaggio 1](images/Lesson4_Chapter3_step1im.PNG)

![Immagine lezione 4 capitolo 3 passaggio 2](images/Lesson4_chapter3_step2im.PNG)

> Nota: Assicurarsi di ridimensionare il box Collider in modo che non sia troppo grande o troppo piccolo. Le dimensioni devono essere più o meno analoghe a quelle dell'oggetto circostante (in questo esempio, l'oggetto nucleo terrestre). Modificare la casella Collider in base alle esigenze selezionando l'opzione modifica Collider in box Collider. È possibile modificare i valori x, y e z o trascinare i gestori del riquadro delimitatore nella finestra della scena dell'editor. 

![Immagine lezione 4 capitolo 3 nota](images/Lesson4_Chapter3_noteim.PNG)

2. Aggiungere un rettangolo di delimitazione all'oggetto node_id30 di Earth Core. A tale scopo, selezionare l'oggetto node_id30 da 3DObjectCollection. Nella scheda controllo fare clic su Aggiungi componente e cercare il rettangolo di delimitazione. Assicurati che cubo di delimitazione, collisore cubico e script di manipolazione, Manipulation Handler (Gestore di modifica) e Near Interaction Grabbable (Afferrabile con interazione da vicino), si trovino tutti nello stesso oggetto gioco.

3.  Nella sezione comportamento del riquadro delimitatore selezionare Activate on Start dall'elenco a discesa Activation. Per esaminare altri dettagli riguardanti le varie opzioni di attivazione e altre opzioni del cubo di delimitazione, vedi la [ documentazione relativa al cubo di delimitazione di MRTK](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html>).

   

   *Nei passaggi successivi verrà modificato anche il modo in cui il rettangolo di delimitazione viene visualizzato regolando il materiale predefinito della casella, il materiale mentre viene afferrato, nonché la visualizzazione dell'angolo e degli handle laterali. MRTK contiene diverse opzioni per personalizzare il cubo di delimitazione.*

4. Nel pannello progetto cercare BoundingBox e verrà visualizzato un elenco di materiali indicati da una sfera blu nei risultati della ricerca, come illustrato nell'immagine seguente. 

5. Trascinare il materiale BoundingBox nello slot del materiale della casella sul componente del rettangolo di delimitazione. Inoltre, estrarre il materiale boundingboxgrabbed e inserirlo nello slot di materiali afferrati per il componente del rettangolo di delimitazione.

6. Trascinare il prefabbricato MRTK_BoundingBox_ScaleWidget nello slot per la prefabbricazione del quadratino di ridimensionamento sul componente del rettangolo. 

7. Trascinare il prefabbricato MRTK_BoundingBox_RotateWidget nello slot del punto di controllo di rotazione sul componente della casella di collegamento.

![Immagine lezione 4 capitolo 3 passaggi 4-7](images/Lesson4_chapter3_step4-7im.PNG)

8. Assicurati che il cubo di delimitazione punti all'oggetto corretto. Nel componente del rettangolo di selezione è presente l'oggetto di destinazione e gli script di override dei limiti. Assicurati di trascinare l'oggetto delimitato dal cubo di delimitazione in entrambi questi slot. In questo esempio, trascinare l'oggetto node_id30 in entrambi gli slot, come illustrato nell'immagine seguente.

> Quando si avvia o si riproduce l'applicazione, l'oggetto sarà racchiuso da una cornice blu. Puoi trascinare gli angoli del riquadro per ridimensionare l'oggetto. Se si desidera che i quadratini di ridimensionamento e di rotazione siano più grandi e più visibili, è consigliabile utilizzare le impostazioni predefinite del riquadro (evitando i passaggi da 4 a 7). 

![Immagine lezione 4 capitolo 3 passaggio 8](images/Lesson4_Chapter3_step8im.PNG)

9. Per tornare alla visualizzazione predefinita del riquadro delimitatore, nel pannello di controllo dell'oggetto del rettangolo di selezione selezionare il quadratino di rotazione e premere CANC. Viene visualizzata una visualizzazione del riquadro delimitatore simile all'immagine seguente. Nota: le visualizzazioni del cubo di delimitazione sono visibili solo in modalità di riproduzione.

![Immagine lezione 4 capitolo 3 passaggio 9](images/Lesson4_chapter3_step9im.PNG)

### <a name="adding-touch-effects"></a>Aggiunta degli effetti tocco
In questo esempio riprodurremo un effetto sonoro quando si tocca un oggetto con la mano.

1. Aggiungi un componente di origine audio all'oggetto gioco. Selezionare l'oggetto Octa nella gerarchia della scena. Nel pannello di controllo fare clic sul pulsante Aggiungi componente, cercare e selezionare origine audio. Useremo questa origine audio per riprodurre un effetto sonoro in un passaggio successivo. 

>Nota: Verificare che l'oggetto Octa disponga di un Collider di box.

2. Aggiungere il componente ritoccabile near Interaction. Fare clic sul pulsante Aggiungi componente nel pannello Inspector e cercare near Interaction touchable. Seleziona questa opzione per aggiungere il componente. 

>Nota: In precedenza, abbiamo aggiunto Near interactionable. La differenza tra questa e l'interazione quasi toccabile consiste nel fatto che l'interazione acquisibile è progettata per l'acquisizione e l'interazione di un oggetto. Il componente toccabile è concepito per l'oggetto da toccare. I due componenti possono essere usati insieme per combinare le interazioni.

![Immagine lezione 4 capitolo 4 passaggi 1-2](images/Lesson4_chapter4_step1-2im.PNG)

3. Aggiungere lo script tocco interazione mano. Si noti che questo script è incluso nella scena Unity importata come parte di questa demo e non è incluso nella MRTK originale. Analogamente al passaggio precedente, fare clic su Aggiungi componente e cercare tocco interazione mano per aggiungerlo.

>Si noti che sono disponibili tre opzioni con lo script: 

>   - Al tocco completato: Trigger quando si tocca e rilascia l'oggetto
>   - Al tocco avviato: Viene attivato quando viene toccato l'oggetto
>   - Al tocco aggiornato: Attiva periodicamente quando la mano tocca l'oggetto

>   Per questo esempio verrà utilizzata l'impostazione on touch started.

4. Fare clic sul pulsante + nell'opzione on touch Started come illustrato nell'immagine seguente. Trascinare l'oggetto Octa nel campo vuoto. 

5. Nell'elenco a discesa che indica nessuna funzione (sopra il rettangolo verde nell'immagine seguente) selezionare AudioSource-> PlayOneShot. Verrà aggiunto un clip audio a questo campo usando i concetti seguenti:

   - In MRTK è disponibile un breve elenco di clip audio. Esplora questi elementi nel pannello del progetto. Sono disponibili nella cartella MixedRealityToolkit. SDK e quindi nella cartella assets standard. Verrà visualizzata una cartella audio in cui sono presenti tutti i clip audio.
   - Per questo esempio verrà usato il clip audio MRTK_Gem. 
   - Per aggiungere un clip audio, è sufficiente trascinare l'immagine desiderata dal pannello del progetto in AudioSource>PlayOneShot (contrassegnati con la casella verde nell'esempio precedente) nel pannello di controllo.

   A questo punto, quando l'utente raggiunge e tocca l'oggetto Octa, viene riprodotto il MRTK_Gem della traccia audio. Lo script di tocco interazione mano modifica anche il colore dell'oggetto quando viene toccato. 

![Immagine lezione 4 capitolo 4 passaggi 3-5 nota](images/Lesson4_chapter4_step3-5-noteim.PNG)

## <a name="congratulations"></a>Lezione completata 
In questa esercitazione si è appreso come organizzare gli oggetti 3D in una raccolta di griglie e come modificare gli oggetti 3D (ridimensionamento, rotazione e movimento) usando near Interaction (cattura diretta con le mani rilevate) e un'interazione di gran lunga (usando raggi di sguardi o raggi mano). Si è inoltre appreso come inserire le caselle di delimitazione intorno agli oggetti 3D e come usare e personalizzare i gizmo nei rettangoli di delimitazione. Hai infine appreso come attivare eventi nel momento in cui viene toccato un oggetto.

[Lezione successiva: 6. Esplorazione delle opzioni di input avanzate](mrlearning-base-ch5.md)


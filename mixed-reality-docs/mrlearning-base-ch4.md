---
title: Esercitazioni introduttive-5. Interazione con oggetti 3D
description: ''
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 8c60d8291ede123817c93458fff003891169840c
ms.sourcegitcommit: 781e47db2ca2f2c792c95e76ac309b44b3535555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2019
ms.locfileid: "74105975"
---
# <a name="5-interacting-with-3d-objects"></a>5. interazione con oggetti 3D

In questa esercitazione vengono fornite informazioni sul contenuto 3D di base e sull'esperienza utente, ad esempio:

* Organizzazione di oggetti 3D come parte di una raccolta
* Caselle di delimitazione per la manipolazione di base
* Interazione quasi e lontano
* Movimenti di tocco e controllo con il rilevamento manuale

## <a name="objectives"></a>Obiettivi

* Informazioni su come organizzare il contenuto 3D con la raccolta di oggetti Grid di MRTK
* Implementare i cubi di delimitazione
* Configurare gli oggetti 3D per la manipolazione di base-spostare, ruotare e ridimensionare
* Esplorare l'interazione da vicino e da lontano
* Informazioni sugli altri movimenti di rilevamento della mano, ad esempio la cattura e il tocco

## <a name="instructions"></a>Istruzioni

### <a name="organizing-3d-objects-in-a-collection"></a>Organizzazione di oggetti 3D in una raccolta

1. Fare clic con il pulsante destro del mouse sulla gerarchia e selezionare Crea vuoto per creare un oggetto gioco vuoto, rinominarlo in 3DObjectCollection e verificare che sia posizionato in corrispondenza di x = 0, y = 0 e z = 0.

    ![mrlearning-base-CH4-1-Step1. png](images/mrlearning-base-ch4-1-step1.png)

2. Scaricare il pacchetto Unity [. HoloLens2. GettingStarted. Tutorials. asset. 2.1.0.0](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.0/Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage) e importarlo usando le stesse istruzioni per importare i pacchetti personalizzati descritti in [dalla lezione 1](mrlearning-base-ch1.md). Questo pacchetto include modelli 3D e altre risorse utili che vengono usate in questa esercitazione.

3. Nel pannello del progetto passare a Asset > BaseModuleAssets > modulo di base prefabbricati e cercare "incompleto". si utilizzeranno alcuni di questi prefabbricati.

    ![mrlearning-base-CH4-1-step3. png](images/mrlearning-base-ch4-1-step3.png)

4. Trascinare Coffee Cup nell'oggetto gioco 3DObjectCollection del passaggio 1. CoffeeCup è ora un elemento figlio della raccolta.

    ![mrlearning-base-CH4-1-step4. png](images/mrlearning-base-ch4-1-step4.png)

5. Successivamente, si aggiungeranno altri oggetti 3D nella scena seguendo lo stesso processo del passaggio precedente. Di seguito è riportato un elenco di oggetti da aggiungere in questo esempio. Quando si aggiungono gli oggetti, è possibile che vengano visualizzati nella scena in diverse dimensioni. Modificare la scala di ogni modello 3D in impostazioni di trasformazione nel pannello di controllo. Le modifiche consigliate per questo esempio sono elencate con gli oggetti seguenti.

    * Cheese_BaseModuleIncomplete. Scala: x = 0,05, y = 0,05, z = 0,05.
    * CoffeeCup_BaseModuleIncomplete. Scala: x = 0,1, y = 0,1, z = 0,1.
    * EarthCore_BaseModuleIncomplete. Scala: x = 50,0 y = 50,0, z = 50,0.
    * Model_Platonic_BaseModuleIncomplete. Scala: x = 0,13, y = 0,13, z = 0,13.
    * Octa_BaseModuleIncomplete. Scala: x = 0,13. y = 0.13 e z =0.13.
    * TheModule_BaseModuleIncomplete. Scala: x = 0,03, y = 0,03, z = 0,03.

    ![mrlearning-base-CH4-1-STEP5. png](images/mrlearning-base-ch4-1-step5.png)

6. Aggiungere tre cubi alla scena. Fare clic con il pulsante destro del mouse sull'oggetto 3DObjectCollection, scegliere oggetto 3D, quindi cubo. Imposta i valori di ridimensionamento su x = 0.14, y = 0.14 e z = 0.14. Ripetere questo passaggio altre due volte per creare un totale di tre cubi. In alternativa, è possibile duplicare il cubo due volte per un totale di tre cubi. Puoi anche scegliere di usare i tre prefab cubo predefiniti in Assets>BaseModuleAssets>Base Module Prefabs e selezionare GreenCube_BaseModuleIncomplete, BlueCube_BaseModuleIncomplete e OrangeCube_BaseModuleIncomplete.

    ![mrlearning-base-CH4-1-step6. png](images/mrlearning-base-ch4-1-step6.png)

7. Organizzare la raccolta di oggetti per formare una griglia, tramite la procedura descritta nella [lezione 2](mrlearning-base-ch2.md), usando la raccolta di oggetti Grid di MRTK. Per un esempio di configurazione degli oggetti in una griglia 3x3, vedere l'immagine seguente.

    ![mrlearning-base-CH4-1-STEP7. png](images/mrlearning-base-ch4-1-step7.png)

    >[!NOTE]
    >È possibile notare che alcuni oggetti sono fuori centro, ad esempio gli oggetti nell'immagine precedente. Questo avviene perché i prefab o gli oggetti possono includere oggetti figlio non allineati. Puoi apportare le modifiche necessarie alla posizione dell'oggetto o dell'oggetto figlio per ottenere una griglia ben allineata.

### <a name="manipulating-3d-objects"></a>Manipolazione di oggetti 3D

1. Aggiungi la capacità di manipolare un cubo. Per aggiungere la possibilità di modificare gli oggetti 3D, eseguire le operazioni seguenti:
    * Selezionare l'oggetto 3D che si desidera modificare nella gerarchia (ad esempio, uno dei cubi).
    * Fare clic su Aggiungi componente
    * Cercare "manipolazione"
    * Seleziona gestore di manipolazione
    * Ripetere l'applicazione per tutti gli oggetti 3D nell'oggetto 3DObjectCollection, ma non con il 3DObjectCollection stesso.
    * Verificare che tutti gli oggetti 3D includano un Collider o box Collider (Add Component > Box Collider).

    ![Immagine lezione 4 capitolo 2 passaggio 1](images/Lesson4_chapter2_step1im.PNG)

    >[!NOTE]
    >Il gestore di manipolazione è un componente che consente di modificare le impostazioni relative al comportamento degli oggetti quando vengono modificate. Sono incluse la rotazione, il ridimensionamento, lo spostamento e il vincolo di spostamento su un asse specifico.

2. Limita un cubo in modo che possa solo essere ridimensionato. Selezionare un cubo nell'oggetto 3DObjectCollection. Nel pannello Inspector, accanto a due tipi di manipolazione gestiti, fare clic sul menu a discesa e selezionare Ridimensiona. In questo modo, l'utente può modificare solo le dimensioni del cubo.

    ![Immagine lezione 4 capitolo 2 passaggio 2](images/Lesson4_Chapter2_step2im.PNG)

3. Modifica il colore di ogni cubo, in modo che sia possibile distinguerli.
    * Passare al pannello del progetto e scorrere verso il basso fino a visualizzare MixedRealityToolkit. SDK, quindi selezionarlo.
    * Selezionare la cartella asset standard.
    * Fare clic sulla cartella materiali.
    * Trascina un materiale diverso in ogni cubo.

    >[!NOTE]
    >puoi scegliere un colore qualsiasi per i cubi. Per questo esempio vengono usati glowingcyan, glowingorange e Green. Puoi provare a usare colori diversi. Per aggiungere il colore al cubo, fare clic sul cubo che si desidera modificare, quindi trascinare il materiale nel campo Material del renderer mesh nel pannello Inspector del cubo.

    ![Immagine lezione 4 capitolo 2 passaggio 3](images/Lesson4_Chapter2_step3im.PNG)

4. Selezionare un altro cubo nell'oggetto 3DObjectCollection e impostarlo in modo che lo spostamento sia vincolato a una distanza fissa dalla testa. A tale scopo, a destra di vincolo sull'etichetta di spostamento, fare clic sul menu a discesa e selezionare Correggi distanza dall'inizio. In questo modo il cubo verrà modificato in base al campo della visione.

    ![Immagine lezione 4 capitolo 2 passaggio 4](images/Lesson4_chapter2_step4im.PNG)

    L'obiettivo dei pochi passaggi seguenti consiste nell'abilitare l'acquisizione e l'interazione con gli oggetti 3D e l'applicazione di impostazioni di manipolazione diverse.

5. Selezionare l'oggetto Cheese, quindi fare clic su Add Component nel pannello Inspector.

6. Eseguire una ricerca nella casella di ricerca di near interactionable e selezionare lo script. Questo componente consente agli utenti di raggiungere e acquisire oggetti con le mani tracciate. Gli oggetti possono anche essere modificati a distanza, a meno che la casella di controllo Consenti disparità non sia selezionata come indicato da un cerchio verde nell'immagine seguente.

    ![Immagine lezione 4 capitolo 2 passaggio 6](images/Lesson4_Chapter2_step6im.PNG)

7. Aggiungere near interactionable all'oggetto Octa, all'oggetto Platonic, a Earth Core, al modulo Lunar e a Coffee Cup ripetendo i passaggi 5 e 6 in tali oggetti.

8. Rimuovi la capacità di manipolazione da lontano dall'oggetto ottaedro. A tale scopo, selezionare il Octa nella gerarchia e deselezionare la casella di controllo Consenti modifiche a distanza (contrassegnato da un cerchio verde). In questo modo gli utenti possono interagire solo con il Octa direttamente usando le mani tracciate.

    >[!NOTE]
    >Per la documentazione completa del componente handler di manipolazione e le impostazioni associate, vedere la documentazione di [MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html).

9. Verificare che sia stato aggiunto il componente near interactionable interactionable a Earth Core, il modulo Lunar e il caffè Cup (vedere il passaggio 7).

10. Per il modulo Lunar, modificare le impostazioni del gestore delle modifiche in modo che ruoti intorno al centro dell'oggetto per l'interazione sia quasi che lontano, come illustrato nell'immagine seguente.

    ![Immagine lezione 4 capitolo 2 passaggio 10](images/Lesson4_chapter2_step10im.PNG)

11. Per Earth Core, modificare il comportamento della versione in Nothing. In questo modo, quando il nucleo di terra viene rilasciato dalla stretta dell'utente, non continua a spostarsi.

    ![Immagine lezione 4 capitolo 2 passaggio 11](images/Lesson4_Chapter2_step11im.PNG)

    >[!NOTE]
    >Questa impostazione è utile per gli scenari, ad esempio la creazione di una palla che è possibile generare. Mantenendo la velocità e la velocità angolari appropriate per garantire che una volta rilasciata la palla continuerà a spostarsi alla velocità in cui è stata rilasciata; in modo analogo al comportamento di una palla fisica.

### <a name="adding-bounding-boxes"></a>Aggiunta di cubi di delimitazione

I rettangoli di delimitazione rendono più semplice e intuitivo manipolare gli oggetti con una sola mano per la manipolazione diretta (near Interaction) e la manipolazione basata su Ray (di gran lunga interazione). I rettangoli di delimitazione forniscono handle che possono essere recuperati per la scala e la rotazione di oggetti lungo un asse specifico.

>[!NOTE]
>Prima di poter aggiungere un rettangolo di delimitazione a un oggetto, è necessario innanzitutto disporre di un collider sull'oggetto (ad esempio, un box Collider), come è stato analizzato in precedenza in questa lezione. È possibile aggiungere i Collider selezionando l'oggetto e nel pannello Inspector dell'oggetto selezionando Aggiungi componente > Box Collider.

1. Aggiungere un Collider box all'oggetto Earth Core, se non ne esiste già uno. La finestra Collider e il programma di installazione non sono necessari se si usa la prefabbricata fornita nella cartella asset del modulo di base per le istruzioni fornite. Nel caso di Earth Core, è stato aggiunto il box Collider all'oggetto, node_id30, sotto il nucleo terrestre, come illustrato nell'immagine seguente. Selezionare node_id30 dalla scheda controllo dell'oggetto, fare clic su Aggiungi componente e cercare box Collider.

    ![Immagine lezione 4 capitolo 3 passaggio 1](images/Lesson4_Chapter3_step1im.PNG)

    ![Immagine lezione 4 capitolo 3 passaggio 2](images/Lesson4_chapter3_step2im.PNG)

    >[!NOTE]
    >Assicurarsi di ridimensionare il box Collider in modo che non sia troppo grande o troppo piccolo. Le dimensioni devono essere più o meno analoghe a quelle dell'oggetto circostante (in questo esempio, l'oggetto nucleo terrestre). Modificare la casella Collider in base alle esigenze selezionando l'opzione modifica Collider in box Collider. È possibile modificare i valori x, y e z o trascinare i gestori del riquadro delimitatore nella finestra della scena dell'editor.

    ![Immagine lezione 4 capitolo 3 nota](images/Lesson4_Chapter3_noteim.PNG)

2. Aggiungere un rettangolo di delimitazione all'oggetto node_id30 di Earth Core. A tale scopo, selezionare il node_id30 oggetto da 3DObjectCollection. Nella scheda controllo fare clic su Aggiungi componente e cercare il rettangolo di delimitazione. Assicurati che cubo di delimitazione, collisore cubico e script di manipolazione, Manipulation Handler (Gestore di modifica) e Near Interaction Grabbable (Afferrabile con interazione da vicino), si trovino tutti nello stesso oggetto gioco.

3. Nella sezione comportamento del riquadro delimitatore selezionare Activate on Start dall'elenco a discesa Activation. Per esaminare i dettagli aggiuntivi relativi alle varie opzioni di attivazione e ad altre opzioni del riquadro, vedere la [documentazione relativa al rettangolo di delimitazione di MRTK](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html>)

    *Nei passaggi successivi verrà modificato anche il modo in cui il rettangolo di delimitazione viene visualizzato regolando il materiale predefinito della casella, il materiale mentre viene afferrato, nonché la visualizzazione dell'angolo e degli handle laterali. Il MRTK contiene diverse opzioni per personalizzare il rettangolo di delimitazione.*

4. Nel pannello progetto cercare "BoundingBox" per visualizzare un elenco di materiali indicati da una sfera blu nei risultati della ricerca, come illustrato nell'immagine seguente.

5. Trascinare il materiale BoundingBox nello slot del materiale della casella sul componente del rettangolo di delimitazione. Estrarre anche il materiale boundingboxgrabbed e inserirlo nello slot del materiale afferrato nella casella nel componente del rettangolo di delimitazione.

    ![mrlearning-base-CH4-3-STEP5. png](images/mrlearning-base-ch4-3-step5.png)

6. Trascinare la prefabbricazione di MRTK_BoundingBox_ScaleHandle nello slot per la prefabbricazione del handle di scala e il MRTK_BoundingBox_RotateHandle prefabbricato nello slot dell'handle di rotazione sul componente del riquadro di collegamento.

    ![mrlearning-base-CH4-3-step6. png](images/mrlearning-base-ch4-3-step6.png)

7. Assicurati che il cubo di delimitazione punti all'oggetto corretto. Nel componente del rettangolo di selezione è presente l'oggetto di destinazione e gli script di override dei limiti. Trascinare l'oggetto con il rettangolo di delimitazione in entrambi gli slot. In questo esempio trascinare l'oggetto node_id30 in entrambi gli slot, come illustrato nell'immagine seguente.

    ![mrlearning-base-CH4-3-STEP7. png](images/mrlearning-base-ch4-3-step7.png)

    >[!NOTE]
    >Quando si avvia o si riproduce l'applicazione, l'oggetto sarà racchiuso da una cornice blu. Puoi trascinare gli angoli del riquadro per ridimensionare l'oggetto. Se si desidera che i quadratini di ridimensionamento e di rotazione siano più grandi e più visibili, è consigliabile utilizzare le impostazioni predefinite del riquadro (evitando i passaggi da 4 a 6).

8. Per tornare alla visualizzazione predefinita del riquadro delimitatore, nel pannello Inspector dell'oggetto del rettangolo di selezione selezionare il quadratino di rotazione e premere CANC per rimuoverlo. Quando si entra in modalità di riproduzione, Wou visualizzerà una visualizzazione del riquadro delimitatore simile all'immagine seguente.

    ![mrlearning-base-CH4-3-Step8. png](images/mrlearning-base-ch4-3-step8.png)

    >[!NOTE]
    >Le visualizzazioni del rettangolo di delimitazione vengono visualizzate solo in modalità di riproduzione.

### <a name="adding-touch-effects"></a>Aggiunta degli effetti tocco

In questo esempio riprodurremo un effetto sonoro quando si tocca un oggetto con la mano.

1. Aggiungi un componente di origine audio all'oggetto gioco. Selezionare l'oggetto Octa nella gerarchia della scena. Nel pannello di controllo fare clic sul pulsante Aggiungi componente, cercare e selezionare origine audio. Useremo questa origine audio per riprodurre un effetto sonoro in un passaggio successivo.

    >[!NOTE]
    >Verificare che l'oggetto Octa disponga di un Collider di box.

2. Aggiungere il componente ritoccabile near Interaction. Fare clic sul pulsante Aggiungi componente nel pannello di controllo e cercare near Interaction touchable. Seleziona questa opzione per aggiungere il componente.

    >[!NOTE]
    >In precedenza, abbiamo aggiunto Near interactionable. La differenza tra questa e l'interazione quasi toccabile consiste nel fatto che l'interazione acquisibile è progettata per l'acquisizione e l'interazione di un oggetto. Il componente toccabile è concepito per l'oggetto da toccare. I due componenti possono essere usati insieme per combinare le interazioni.

    ![Immagine lezione 4 capitolo 4 passaggi 1-2](images/Lesson4_chapter4_step1-2im.PNG)

3. Aggiungere lo script tocco interazione mano. Analogamente al passaggio precedente, fare clic su Aggiungi componente e cercare tocco interazione mano per aggiungerlo.

    Si noti che sono disponibili tre opzioni con lo script:
    * Al tocco completato: trigger quando si tocca e rilascia l'oggetto
    * All'avvio del tocco: viene attivato quando viene toccato l'oggetto
    * Al tocco aggiornato: attiva periodicamente quando la mano tocca l'oggetto

    Per questo esempio verrà utilizzata l'impostazione on touch started.

    >[!NOTE]
    >Questo script è incluso nel pacchetto BaseModuleAssets Unity che è stato importato all'inizio di questa esercitazione e non è incluso nella MRTK originale.

4. Fare clic sul pulsante + nell'opzione on touch Started e trascinare l'oggetto Octa nel campo Empty.

    ![mrlearning-base-CH4-4-step4. png](images/mrlearning-base-ch4-4-step4.png)

5. Nell'elenco a discesa che indica nessuna funzione selezionare AudioSource > PlayOneShot. Verrà aggiunto un clip audio a questo campo usando i concetti seguenti:

    * In MRTK è disponibile un breve elenco di clip audio. È possibile esplorarli nel pannello del progetto. Queste informazioni sono disponibili nella cartella assets > MixedRealityToolkit. SDK > risorse standard > audio.
    * Per questo esempio verrà usato il clip audio MRTK_Gem.
    * Per aggiungere un clip audio, è sufficiente trascinare il clip desiderato dal pannello del progetto nel campo AudioSource. PlayOneShot.

    ![mrlearning-base-CH4-4-STEP5. png](images/mrlearning-base-ch4-4-step5.png)

   A questo punto, quando l'utente raggiunge e tocca l'oggetto Octa, la traccia audio MRTK_Gem verrà riprodotto. Lo script di tocco interazione mano modifica anche il colore dell'oggetto, quando viene toccato.

## <a name="congratulations"></a>Lezione completata

In questa esercitazione si è appreso come organizzare gli oggetti 3D in una raccolta di griglie e come manipolare questi oggetti (ridimensionamento, rotazione e movimento) usando near Interaction (cattura diretta con le mani rilevate) e un'interazione di gran lunga (usando raggi di sguardi o raggi mano). Si è inoltre appreso come inserire le caselle di delimitazione intorno agli oggetti 3D e come usare e personalizzare i gizmo nei rettangoli di delimitazione. Hai infine appreso come attivare eventi nel momento in cui viene toccato un oggetto.

[Lezione successiva: 6. esplorazione delle opzioni di input avanzate](mrlearning-base-ch5.md)

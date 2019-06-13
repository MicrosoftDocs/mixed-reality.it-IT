---
title: Modulo di apprendimento di base sulla realtà mista - Interazione con oggetti 3D
description: Completa questo corso per informazioni su come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 45e772de0825fe2161f880a165d6c75c755b849e
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2019
ms.locfileid: "65730912"
---
# <a name="mr-learning-base-module---3d-object-interaction"></a>Modulo di apprendimento di base sulla realtà mista - Interazione con oggetti 3D

In questa lezione esamineremo il contenuto 3D di base e l'esperienza utente. Apprenderemo come organizzare gli oggetti 3D come parte di una raccolta, presenteremo informazioni sui cubi di delimitazione per la manipolazione di base, sull'interazione da vicino e da lontano e sui movimenti per toccare e afferrare con il tracciamento delle mani. 

## <a name="objectives"></a>Obiettivi

* Apprendere come organizzare contenuto 3D con la raccolta di oggetti griglia di MRKT
* Implementare i cubi di delimitazione
* Configurare oggetti 3D per la manipolazione di base (spostare, ruotare e ridimensionare)
* Esplorare l'interazione da vicino e da lontano
* Apprendere ulteriori gesti di tracciamento delle mani come afferrare e toccare

## <a name="instructions"></a>Istruzioni

### <a name="organizing-3d-objects-in-a-collection"></a>Organizzazione di oggetti 3D in una raccolta

1. Fai clic con il pulsante destro del mouse sulla gerarchia e seleziona "Create Empty" (Crea vuoto). Viene creato un oggetto gioco vuoto. Rinominalo in "3DObjectCollection". In questa posizione inseriremo tutti gli oggetti 3D. Assicurati che il posizionamento della raccolta sia impostato su x = 0, y = 0 e z = 0.

![Immagine lezione 4 capitolo 1 passaggio 1](images/Lesson4_Chapter1_step1im.PNG)

2. Importa gli asset del modulo base con le stesse istruzioni usate per importare i pacchetti personalizzati descritti nella [lezione 1](mrlearning-base-ch1.md). Gli asset del modulo base includono moduli 3D e altri script utili che verranno usati in questa esercitazione. Il pacchetto per Unity del modulo base è disponibile qui: <https://github.com/Microsoft/MixedRealityLearning/releases/tag/V1.1>

3. Il prefab CoffeeCup è riconoscibile dall'icona a forma di cubo blu. Non selezionare l'elemento CoffeeCup con l'icona a forma di cubo blu e foglietto bianco (che indica il modello 3D originale e non il prefab). 

![Immagine lezione 4 capitolo 1 nota a](images/Lesson4_chapter1_noteaim.PNG)

4. Trascina il prefab CoffeeCup scelto nell'oggetto gioco "3DObjectCollection" del passaggio 1. CoffeeCup è ora un elemento figlio della raccolta.

![Immagine lezione 4 capitolo 1 passaggio 4](images/Lesson4_chapter1_step4ima.PNG)

5. Successivamente, aggiungeremo alla scena altri oggetti 3D. Di seguito sono elencati gli oggetti che aggiungeremo in questo esempio. Quando aggiungi gli oggetti è probabile che questi vengano visualizzati nella scena in diverse dimensioni. Ridimensiona ogni modello 3D in base all'impostazione di trasformazione nel pannello di controllo. Le modifiche consigliate per questo esempio sono elencate con gli oggetti seguenti. Cerca queste parole nella casella di ricerca del pannello del progetto e trascina il prefab dell'oggetto 3D nell'oggetto "3DObjectCollection", in modo analogo al passaggio precedente. Le raccolte di prefab sono disponibili in Assets>BaseModuleAssets>Base Module Prefabs.
- Cerca "TheModule_BaseModuleIncomplete". Trascina nella scena. Imposta i valori di ridimensionamento su x = 0.03, y = 0.03 e z = 0.03. 
- Cerca "Octa_BaseModuleIncomplete". Trascina nella scena. Imposta i valori di ridimensionamento su x = 0.13, y = 0.13 e z =0.13.
- Cerca "EarthCore_BaseModuleIncomplete". Trascina nella scena. Imposta i valori di ridimensionamento su x = 50.0, y = 50.0 e z = 50.0.
- Cerca "Cheese_BaseModuleIncomplete". Trascina nella scena. Imposta i valori di ridimensionamento su x = 0.05, y = 0.05 e z = 0.05.
- Cerca "Model_Platonic_BaseModuleIncomplete". Trascina nella scena. Imposta i valori di ridimensionamento su x = 0.13, y = 0.13 e z = 0.13.
- Cerca "CoffeeCup_BaseModuleIncomplete". Trascina nella scena.

![Immagine lezione 4 capitolo 1 passaggio 5](images/Lesson4_Chapter1_step5im.PNG)

6. Aggiungi tre cubi alla scena. Fai clic con il pulsante destro del mouse sull'oggetto "3DObjectCollection", seleziona "3D Object" (Oggetto 3D) e quindi seleziona "Cube". Imposta i valori di ridimensionamento su x = 0.14, y = 0.14 e z = 0.14. Ripeti questo passaggio altre due volte per creare tre cubi in totale. In alternativa, puoi duplicare il cubo due volte per un totale di tre cubi. Puoi anche scegliere di usare i tre prefab cubo predefiniti in Assets>BaseModuleAssets>Base Module Prefabs e selezionare GreenCube_BaseModuleIncomplete, BlueCube_BaseModuleIncomplete e OrangeCube_BaseModuleIncomplete.

![Immagine lezione 4 capitolo 1 passaggio 6](images/Lesson4_Chapter1_step6im.PNG)

7. Organizza la raccolta di oggetti in modo da formare una griglia seguendo la procedura illustrata nella [lezione 2](mrlearning-base-ch2.md) tramite la raccolta di oggetti griglia di MRTK. Fai riferimento all'immagine seguente per vedere un esempio di configurazione di oggetti in una griglia 3x3.

![Immagine lezione 4 capitolo 1 nota b](images/Lesson4_chapter1_notebim.PNG)

>Nota: potresti notare che alcuni degli oggetti sono decentrati, come quelli nell'immagine precedente. Questo avviene perché i prefab o gli oggetti possono includere oggetti figlio non allineati. Puoi apportare le modifiche necessarie alla posizione dell'oggetto o dell'oggetto figlio per ottenere una griglia ben allineata.


### <a name="manipulating-3d-objects"></a>Manipolazione di oggetti 3D
1. Aggiungi la capacità di manipolare un cubo. Per aggiungere la capacità di manipolare oggetti 3D, esegui queste operazioni:
-   Seleziona l'oggetto 3D che vuoi manipolare nella gerarchia (in questo esempio, uno dei cubi).
-   Fai clic su "Add Component" (Aggiungi componente). 
-   Cerca "manipulation".
-   Seleziona "Manipulation Handler" (Gestore di manipolazione).
-   Ripeti il passaggio per tutti gli oggetti 3D sotto l'oggetto "3DObjectCollection", ma non per l'oggetto "3DObjectCollection" stesso.
-   Verifica che tutti gli oggetti 3D abbiano un collisore o un collisore cubico scegliendo Add Component>Box Collider (Aggiungi componente>Collisore cubico).

![Immagine lezione 4 capitolo 2 passaggio 1](images/Lesson4_chapter2_step1im.PNG)

>Il gestore di manipolazione è un componente che ti consente di regolare le impostazioni relative al comportamento degli oggetti quando vengono manipolati. Le impostazioni includono la rotazione, il ridimensionamento, lo spostamento e la limitazione dello spostamento su determinati assi. 

2. Limita un cubo in modo che possa solo essere ridimensionato. Seleziona un cubo nell'oggetto "3DObjectCollection". Nel pannello di controllo, accanto a "Two Handed Manipulation Type" (Tipo di manipolazione a due mani), fai clic sul menu a discesa e seleziona "Scale" (Ridimensiona). In questo modo, l'utente può modificare solo le dimensioni del cubo.

![Immagine lezione 4 capitolo 2 passaggio 2](images/Lesson4_Chapter2_step2im.PNG)

3. Modifica il colore di ogni cubo, in modo che sia possibile distinguerli. 
-   Passa al pannello del progetto e scorri verso il basso fino a visualizzare "MixedRealityToolkit.SDK" quindi selezionalo.
-   Seleziona la cartella "StandardAssets".
-   Fai clic sulla cartella "Materials" (Materiali).
-   Trascina un materiale diverso in ogni cubo. 

>Nota: puoi scegliere un colore qualsiasi per i cubi. In questo esempio, si useranno i colori "ciano brillante", "arancione brillante" e "verde". Puoi provare a usare colori diversi. Per aggiungere il colore al cubo, fai clic sul cubo da modificare e quindi trascina il materiale sul campo del materiale del renderer della mesh nel pannello di controllo del cubo. 

![Immagine lezione 4 capitolo 2 passaggio 3](images/Lesson4_Chapter2_step3im.PNG)

4. Seleziona un altro cubo dell'oggetto "3DObjectCollection" e fai in modo che il relativo movimento sia vincolato a una distanza fissa dalla testa. A tale scopo, a destra di "Constraint On Movement" (Vincolo su movimento) fai clic sul menu a discesa e seleziona "Fix Distance From Head" (Distanza fissa dalla testa). In questo modo, l'utente può spostare il cubo solo entro il proprio campo visivo. 

![Immagine lezione 4 capitolo 2 passaggio 4](images/Lesson4_chapter2_step4im.PNG)

Obiettivo dei passaggi successivi: abiliteremo le funzionalità per afferrare e interagire con gli oggetti 3D e applicheremo varie impostazioni di manipolazione. 

5. Seleziona l'oggetto formaggio e nel pannello di controllo fai clic su "Add Component" (Aggiungi componente). 

6. Cerca "Near Interaction Grabbable" nella casella di ricerca e seleziona lo script. Questo componente consente agli utenti di raggiungere e afferrare gli oggetti con le mani tracciate. Gli oggetti potranno anche essere manipolati da una determinata distanza, a meno che la casella di controllo "Allow Far Manipulation" (Consenti manipolazione da lontano) sia deselezionata (evidenziata dal cerchio verde nell'immagine seguente).

![Immagine lezione 4 capitolo 2 passaggio 6](images/Lesson4_Chapter2_step6im.PNG)

7. Aggiungi "Near Interaction Grabbable" (Afferrabile con interazione da vicino) agli oggetti ottaedro, platonico, nucleo terrestre, modulo lunare e tazza di caffè ripetendo i passaggi 5 e 6 per tali oggetti.

8. Rimuovi la capacità di manipolazione da lontano dall'oggetto ottaedro. A tale scopo, seleziona l'oggetto ottaedro nella gerarchia e deseleziona la casella di controllo "Allow Far Manipulation" (Consenti manipolazione da lontano), contrassegnata da un cerchio verde. In questo modo, gli utenti possono interagire con l'oggetto ottaedro solo direttamente usando le mani tracciate.

>Nota: per la documentazione completa del componente del gestore di manipolazione e delle relative impostazioni, vedi la [documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html).

9. Assicurati che il componente "Near Interaction Grabbable" (Afferrabile con interazione da vicino) sia stato aggiunto agli oggetti nucleo terrestre, modulo lunare e tazza di caffè (vedi il passaggio 7).

10. Per il modulo lunare, modifica le impostazioni del gestore di manipolazione in modo che ruoti intorno al centro dell'oggetto per l'interazione da vicino e da lontano, come illustrato nell'immagine seguente.

![Immagine lezione 4 capitolo 2 passaggio 10](images/Lesson4_chapter2_step10im.PNG)

11\. Per l'oggetto nucleo terrestre, modifica il comportamento di rilascio impostandolo su "Nothing" (Nulla). In questo modo, quando l'oggetto nucleo terrestre viene rilasciato dalla presa dell'utente, non continua a spostarsi. 

![Immagine lezione 4 capitolo 2 passaggio 11](images/Lesson4_Chapter2_step11im.PNG)

> Nota: questa impostazione è utile per scenari come la creazione di una palla che si può lanciare. Se si mantengono la velocità e la velocità angolare, quando la palla viene rilasciata continuerà a muoversi alla velocità in cui è stata rilasciata, in modo simile a come si comporta una palla fisica.

### <a name="adding-bounding-boxes"></a>Aggiunta di cubi di delimitazione
I cubi di delimitazione rendono più semplice e intuitiva la manipolazione degli oggetti con una mano sia per la manipolazione diretta (interazione da vicino) sia per la manipolazione basata su raggio (interazione da lontano). I cubi di delimitazione sono dotati di "punti di controllo" che possono essere afferrati per il ridimensionamento e la rotazione degli oggetti lungo assi specifici.
>Nota: prima di poter aggiungere un cubo di delimitazione a un oggetto devi innanzitutto disporre di un collisore sull'oggetto, ad esempio un collisore cubico. Come abbiamo fatto in precedenza in questa lezione. Puoi aggiungere i collisori selezionando l'oggetto e quindi, nel pannello di controllo dell'oggetto, scegliendo Add Component>Box Collider (Aggiungi componente>Collisore cubico).
>

1. Aggiungi un collisore cubico all'oggetto nucleo terrestre, se non già presente. Il collisore cubico e la configurazione non sono necessari se si usa il prefab fornito nella cartella Base Module Assets (Asset modulo base), come da precedenti istruzioni. Nel caso dell'oggetto nucleo terrestre, dovremo aggiungere il collisore cubico all'oggetto "node_id30" sottostante l'oggetto nucleo terrestre, come illustrato nell'immagine seguente. Seleziona node_id30 e, nella scheda di controllo dell'oggetto, fai clic su "Add Component" (Aggiungi componente) e cerca "Box Collider". 

![Immagine lezione 4 capitolo 3 passaggio 1](images/Lesson4_Chapter3_step1im.PNG)

![Immagine lezione 4 capitolo 3 passaggio 2](images/Lesson4_chapter3_step2im.PNG)

> Nota: assicurati di visualizzare il collisore cubico in modo che non sia troppo grande o troppo piccolo. Le dimensioni devono essere più o meno analoghe a quelle dell'oggetto circostante (in questo esempio, l'oggetto nucleo terrestre). Modifica il collisore cubico in base alle tue esigenze selezionando l'opzione Edit Collider (Modifica collisore) in Box Collider (Collisore cubico). Puoi modificare i valori degli assi x, y e z o trascinare i punti di controllo del cubo di delimitazione nella finestra dell'editor della scena. 

![Immagine lezione 4 capitolo 3 nota](images/Lesson4_Chapter3_noteim.PNG)

2. Aggiungi un cubo di delimitazione all'oggetto "node_id30" del nucleo terrestre. A tale scopo, seleziona l'oggetto "node_id30" da "3DObjectCollection". Nella scheda di controllo fai clic su "Add Component" (Aggiungi componente) e cerca "bounding box". Assicurati che cubo di delimitazione, collisore cubico e script di manipolazione, Manipulation Handler (Gestore di modifica) e Near Interaction Grabbable (Afferrabile con interazione da vicino), si trovino tutti nello stesso oggetto gioco.

3.  Nella sezione "Behavior" (Comportamento) del cubo di delimitazione seleziona "Activate On Start" (Attiva all'avvio) nell'elenco a discesa Activation (Attivazione). Per esaminare altri dettagli riguardanti le varie opzioni di attivazione e altre opzioni del cubo di delimitazione, vedi la [ documentazione relativa al cubo di delimitazione di MRTK](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html>).

   

   *Nei passaggi successivi, modificheremo anche l'aspetto del cubo di delimitazione modificandone il materiale predefinito, il materiale nel momento in cui viene afferrato, nonché la visualizzazione dei punti di controllo (punti di controllo angolari e laterali). MRTK contiene diverse opzioni per personalizzare il cubo di delimitazione.*

4. Nel pannello del progetto cerca "Bounding Box" e visualizzerai un elenco di materiali indicato da una sfera blu nei risultati della ricerca, come illustrato nell'immagine seguente. 

5. Trascina il materiale "BoundingBox" nello slot Box Material (Materiale cubo) del cubo di delimitazione. Afferra anche il materiale "BoundingBoxGrabbed" e posizionalo nello slot Box Grabbed Material (Materiale afferrato cubo) del cubo di delimitazione.

6. Trascina il materiale "MRTK_BoundingBox_ScaleWidget" nello slot Scale Handle Prefab (Prefab punto di controllo ridimensionamento) del cubo di delimitazione. 

7. Trascina il materiale "MRTK_BoundingBox_RotateWidget" nello slot Rotation Handle Prefab (Prefab punto di controllo rotazione) del cubo di delimitazione.

![Immagine lezione 4 capitolo 3 passaggi 4-7](images/Lesson4_chapter3_step4-7im.PNG)

8. Assicurati che il cubo di delimitazione punti all'oggetto corretto. Nel cubo di delimitazione sono presenti gli script "Target Object" (Oggetto di destinazione) e "Bounds Override" (Limite sostituzione). Assicurati di trascinare l'oggetto delimitato dal cubo di delimitazione in entrambi questi slot. In questo esempio, trascina l'oggetto "node_id30" in entrambi questi slot, come illustrato nell'immagine seguente.

> Quando avvii o riproduci l'applicazione, l'oggetto verrà delimitato da un riquadro blu. Puoi trascinare gli angoli del riquadro per ridimensionare l'oggetto. Per rendere più grandi e visibili i punti di controllo di ridimensionamento e rotazione, usa le impostazioni predefinite del cubo di delimitazione (tralasciando i passaggi da 4 a 7). 

![Immagine lezione 4 capitolo 3 passaggio 8](images/Lesson4_Chapter3_step8im.PNG)

9. Per tornare alla visualizzazione predefinita del cubo di delimitazione, nel pannello di controllo dell'oggetto del cubo di delimitazione seleziona il punto di controllo di rotazione e premi CANC. Visualizzerai il cubo di delimitazione con un aspetto simile a quello riportato nell'immagine seguente. Nota: le visualizzazioni del cubo di delimitazione sono visibili solo in modalità di riproduzione.

![Immagine lezione 4 capitolo 3 passaggio 9](images/Lesson4_chapter3_step9im.PNG)

### <a name="adding-touch-effects"></a>Aggiunta di effetti di tocco
In questo esempio riprodurremo un effetto sonoro quando si tocca un oggetto con la mano.

1. Aggiungi un componente di origine audio all'oggetto gioco. Seleziona l'oggetto "ottaedro" nella gerarchia della scena. Nel pannello di controllo fai clic sul pulsante "Add Component" (Aggiungi componente) cerca "Audio Source" e seleziona il componente corrispondente. Useremo questa origine audio per riprodurre un effetto sonoro in un passaggio successivo. 

>Nota: assicurati che per l'oggetto "ottaedro" sia definito un collisore cubico.

2. Aggiungi il componente "Near Interaction Touchable" (Toccabile con interazione da vicino). Nel pannello di controllo fai clic sul pulsante "Add Component" (Aggiungi componente) e cerca "Near Interaction Touchable". Seleziona questa opzione per aggiungere il componente. NOTA: correggi lo screenshot per evidenziare che si sta aggiungendo il componente e non solo evidenziando il collisore cubico.

>Nota: in precedenza abbiamo aggiunto il componente "Near Interaction Grabbable" (Afferrabile con interazione da vicino). La differenza tra i due componenti è che l'interazione "Near Interaction Grabbable" (Afferrabile con interazione da vicino) è destinata a un oggetto che deve essere afferrato e con cui si può interagire. Il componente "Near Interaction Touchable" (Toccabile con interazione da vicino) è destinata a un oggetto che può essere toccato. I due componenti possono essere usati insieme per combinare le interazioni.

![Immagine lezione 4 capitolo 4 passaggi 1-2](images/Lesson4_chapter4_step1-2im.PNG)

3. Aggiungi lo script "Hand Interaction Touch" (Tocco con interazione manuale). Nota che questo script è incluso nella scena di Unity importata come parte di questo pacchetto dimostrativo, ma non è incluso nella versione originale di MRTK. Proprio come nel passaggio precedente, fai clic su "Add Component" (Aggiungi componente) e cerca "Hand Interaction Touch" per aggiungere il componente. 
   Nota che con lo script sono disponibili tre opzioni: 

   - "On Touch Completed" (Completato al tocco). Verrà attivata quando tocchi e rilasci l'oggetto. 
   - "On Touch Started" (Avviato al tocco). Verrà attivata quando tocchi l'oggetto. 
   - "On Touch Updated" (Aggiornato al tocco). Verrà attivata periodicamente quando la mano tocca l'oggetto. 

   In questo esempio, si userà l'impostazione "On Touch Started" (Avviato al tocco).

4. Fai clic sul pulsante "+" nell'opzione "On Touch Started" (Avviato al tocco), come illustrato nell'immagine seguente. Trascina l'oggetto ottaedro nel campo vuoto. 

5. Nell'elenco a discesa denominato "No Function" (Nessuna funzione) (sopra al rettangolo verde nell'immagine seguente), seleziona AudioSource>PlayOneShot. Verrà aggiunto un clip audio a questo campo usando i concetti seguenti:

   - In MRTK è disponibile un breve elenco di clip audio. Esplora questi elementi nel pannello del progetto. Sono disponibili nella cartella "MixedRealityToolkit.SDK" e quindi nella cartella "StandardAssets". Qui puoi trovare una cartella "Audio" in cui sono disponibili tutti i clip audio.
   - In questo esempio useremo il clip audio "MRTK_Gem". 
   - Per aggiungere un clip audio, è sufficiente trascinare l'immagine desiderata dal pannello del progetto in AudioSource>PlayOneShot (contrassegnati con la casella verde nell'esempio precedente) nel pannello di controllo.

   A questo punto, quando l'utente raggiunge e tocca l'oggetto ottaedro, la traccia audio "MRTK_Gem" verrà riprodotta. Lo script "Hand Interaction Touch" (Tocco con interazione manuale) modificherà anche il colore dell'oggetto al tocco. 

![Immagine lezione 4 capitolo 4 passaggi 3-5 nota](images/Lesson4_chapter4_step3-5-noteim.PNG)

### <a name="congratulations"></a>Lezione completata 
In questa lezione hai appreso come organizzare gli oggetti 3D in una raccolta di oggetti griglia e come manipolare gli oggetti 3D (ridimensionamento, rotazione e spostamento) usando l'interazione da vicino (afferrando direttamente con le mani tracciate) e l'interazione da lontano (tramite raggi di sguardo o manuali). Hai anche appreso come delimitare gli oggetti 3D con cubi di delimitazione e come usare e personalizzare le parti dei cubi di delimitazione. Hai infine appreso come attivare eventi nel momento in cui viene toccato un oggetto.

[Lezione successiva: Input avanzati](mrlearning-base-ch5.md)


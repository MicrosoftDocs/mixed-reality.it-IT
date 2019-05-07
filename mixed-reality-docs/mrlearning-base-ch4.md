---
title: Modulo di Base Learning MR - l'interazione dell'oggetto 3D
description: Completare questo corso di informazioni su come implementare il riconoscimento di volti di Azure all'interno di un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, hololens, esercitazione di unity,
ms.openlocfilehash: 344b3bc892839bc22445e10af644771bc7008ac3
ms.sourcegitcommit: a32f673814a6cd6ff00f936f448885788b3b882c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/30/2019
ms.locfileid: "64929586"
---
# <a name="mr-learning-base-module---3d-object-interaction"></a>Modulo di Base Learning MR - l'interazione dell'oggetto 3D

In questa lezione verranno esaminate contenuto 3D di base e l'esperienza dell'utente. Si apprenderà come organizzare gli oggetti 3D come parte di una raccolta, informazioni su rettangoli per la manipolazione di base, Scopri l'interazione di vicino e lontano e informazioni su Windows touch e scarica i movimenti con mano di rilevamento. 

## <a name="objectives"></a>Obiettivi

* Informazioni su come organizzare il contenuto 3D tramite raccolta della MRTK di oggetti della griglia
* Implementare le finestre di contenimento
* Configurare oggetti 3D per la manipolazione di base (spostare, ruotare e scala)
* Esplorare un'interazione più vicino e lontano
* Informazioni su ulteriore mano i movimenti come quadratini di ridimensionamento e il tocco di rilevamento

## <a name="instructions"></a>Istruzioni

### <a name="organizing-3d-objects-in-a-collection"></a>Organizzazione di oggetti 3D in una raccolta

1. Fare clic sulla gerarchia e si seleziona, "Crea vuoto". Verrà creato un oggetto gioco vuoto. Rinominarlo in "3DObjectCollection." Si tratta in cui si inseriranno tutti i nostri oggetti 3D. Assicurarsi che il posizionamento della raccolta è impostato su x = 0, y = 0 e z = 0.

![Lesson4 capitolo 1 Step1im](images/Lesson4_Chapter1_step1im.PNG)

2. Importare BaseModule gli asset con le stesse istruzioni per importare pacchetti personalizzati descritti in [dalla lezione 1](mrlearning-base-ch1.md). Le risorse BaseModule includono moduli 3D e altri utili script che verrà usato in questa esercitazione. Il pacchetto unity BaseModule è disponibili qui: <https://github.com/Microsoft/MixedRealityLearning/releases/tag/V1.1>

3. Il prefab tazza di caffè può essere riconosciuto da un cubo blu accanto a esso. Non selezionare i criteri utente personalizzati di caffè con il cubo blu e il white paper piccolo (che indica il modello 3D originale e non il prefab.) 

![Lesson4 capitolo 1 Noteaim](images/Lesson4_chapter1_noteaim.PNG)

4. Trascinare il prefab tazza di caffè di propria scelta nell'oggetto gioco "3DObjectCollection" nel passaggio 1. I criteri utente personalizzati di caffè sono ora un elemento figlio della raccolta.

![Lesson4 capitolo 1 Step4ima](images/Lesson4_chapter1_step4ima.PNG)

5. Successivamente, si aggiungerà ulteriori oggetti 3D nella scena. Di seguito è un elenco di oggetti che verrà aggiunta in questo esempio. Quando si aggiungono gli oggetti che è probabile che questi vengano visualizzati nella scena in diverse dimensioni. Regolare la scala di ogni modello 3D in base all'impostazione di transform nel Pannello di controllo. Modifiche consigliate in questo esempio sono elencati gli oggetti seguenti. Queste parole di ricerca nella casella di ricerca nel Pannello di progetto e trascinare l'oggetto 3D prefab nell'oggetto "3DObjectCollection" simile al passaggio precedente. Si noterà questi raccolta di prefabs negli asset > BaseModuleAssets > Base modulo Prefabs
- Cercare "TheModule_BaseModuleIncomplete." Trascinare nella scena. Impostare il valore di x = 0,03, y = 0,03, z = 0,03. 
- Cercare "Octa_BaseModuleIncomplete." Trascinare nella scena. Impostare il valore di x = 0.13. y = 0.13, z =0.13.
- Cercare "EarthCore_BaseModuleIncomplete." Trascinare nella scena. Impostare il valore di x = 50,0 y = 50,0, z = 50,0.
- Cercare "Cheese_BaseModuleIncomplete." Trascinare nella scena. Impostare il valore di x = 0,05, y = 0,05, z = 0,05.
- Cercare "Model_Platonic_BaseModuleIncomplete." Trascinare nella scena. Impostare il valore di x = 0.13, y = 0.13, z = 0.13.
- Cercare "CoffeeCup_BaseModuleIncomplete." Trascinare nella scena.

![Lesson4 capitolo 1 Step5im](images/Lesson4_Chapter1_step5im.PNG)

6. Aggiungere i 3 cubi nella scena. Fare clic con il pulsante destro dell'oggetto "3DObjectCollection", selezionare "3D Object", quindi selezionare "Cube". Impostare il valore di x = 0,14, y = 0,14 e z = 0,14. Ripetere questo passaggio 2 volte aggiuntive per creare un totale di 3 cubi. In alternativa, è possibile duplicare il cubo due volte per un totale di 3 cubi. È anche possibile scegliere di usare i tre prefabs cubo preparata dagli asset > BaseModuleAssets > Prefabs modulo di Base e selezionare GreenCube_BaseModuleIncomplete, BlueCube_BaseModuleIncomplete e OrangeCube_BaseModuleIncomplete.

![Lesson4 capitolo 1 Step6im](images/Lesson4_Chapter1_step6im.PNG)

7. Organizzare la raccolta di oggetti in modo da formare una griglia seguendo la procedura illustrata nel [lezione 2](mrlearning-base-ch2.md) con raccolta di oggetti della griglia del MRTK. Fare riferimento all'immagine seguente per vedere un esempio di configurazione di oggetti in una 3x3 griglia.

![Lesson4 capitolo 1 Notebim](images/Lesson4_chapter1_notebim.PNG)

>Nota: È possibile notare che alcuni degli oggetti sono fuori centro, ad esempio gli oggetti nell'immagine precedente. Questo avviene perché prefabs o oggetti potrebbero includere oggetti figlio non sono allineati. È possibile apportare le modifiche necessarie nella posizione di oggetto o posizioni di oggetti figlio per ottenere una griglia ben allineata.


### <a name="manipulating-3d-objects"></a>La manipolazione di oggetti 3D
1. Aggiungere la possibilità di modificare un cubo. Per aggiungere la possibilità di modificare oggetti 3D, è necessario eseguire le operazioni seguenti:
-   Selezionare l'oggetto 3D che si desidera modificare nella gerarchia (in questo esempio, uno dei cubi).
-   Fare clic su "Aggiungi componente". 
-   Eseguire la ricerca di "Modifica".
-   Selezionare "Modifica gestore".
-   Ripetere il passaggio per tutti gli oggetti 3D sotto l'oggetto "3DObjectCollection" ma non la "3DObjectCollection" se stesso.
-   Verificare che tutti gli oggetti 3D hanno un collider o collider casella (Add Component > finestra collider).

![Lesson4 Chapter2 Step1im](images/Lesson4_chapter2_step1im.PNG)

>Il gestore di modifica è un componente che è possibile regolare le impostazioni per gli oggetti si comportano come quando viene modificato. Ciò include la rotazione, ridimensionamento, lo spostamento e vincolare lo spostamento su determinati assi. 

2. Limitare un cubo in modo che questa può solo essere ridimensionata. Selezionare un cubo nell'oggetto "3DObjectCollection". Nel Pannello di controllo, accanto a "tipo di modifica la mano due", fare clic sul menu a discesa e selezionare "scalabilità". In questo modo, in modo che l'utente può modificare solo le dimensioni del cubo.

![Lesson4 Chapter2 Step2im](images/Lesson4_Chapter2_step2im.PNG)

3. Modificare il colore di ciascun cubo, in modo che è possibile distinguere tra di essi. 
-   Passare al pannello di progetto e scorrere verso il basso fino a quando non si vedere "MixedRealityToolkit.SDK" quindi selezionarla.
-   Selezionare la cartella "Assets Standard".
-   Fare clic sulla cartella "materiali".
-   Trascinare un materiale diverso in ognuna dei cubi. 

>Nota: È possibile scegliere qualsiasi colore per i cubi. In questo esempio si intende usare "glowingcyan", "glowingorange," e "verdi". È possibile sperimentare con colori diversi. Per aggiungere il colore per il cubo, fare clic sul cubo per modificare il colore di, quindi trascinare il materiale a campo di materiale del programma di rendering mesh nel Pannello di controllo del cubo. 

![Lesson4 Chapter2 Step3im](images/Lesson4_Chapter2_step3im.PNG)

4. Selezionare un altro cubo dell'oggetto "3DObjectCollection" e fare in modo che suo movimento è vincolato alla correzione di distanza dall'inizio. A tale scopo, a destra di "vincolo in movimento", fare clic sul menu a discesa e selezionare "correzione di distanza dall'inizio". In questo modo, in modo che l'utente può spostare solo il cubo nel loro campo visivo. 

![Lesson4 Chapter2 Step4im](images/Lesson4_chapter2_step4im.PNG)

Obiettivo di passaggi successivi: Verrà abilitato quadratini di ridimensionamento e l'interazione con gli oggetti 3D. Microsoft applicherà le impostazioni di manipolazione diversi 

5. Selezionare l'oggetto formaggio e nel Pannello di controllo, fare clic su "Aggiungi componente". 

6. Eseguire la ricerca nella casella di ricerca di "Quasi interazione Grabbable" e selezionare lo script. Questo componente consente agli utenti di raggiungere e recuperare gli oggetti con rilevamento mani. Gli oggetti anche potrà essere modificato da una distanza, a meno che la casella di controllo "Consenti a questo momento manipolazione" sia deselezionata (indicato da un cerchio verde nell'immagine seguente).

![Lesson4 Chapter2 Step6im](images/Lesson4_Chapter2_step6im.PNG)

7. Aggiungere "Quasi interazione Grabbable" per l'ottaidrato oggetto oggetto Platonic, core terra, modulo lunare e tazza di caffè ripetendo il passaggio 5 e 6 per tali oggetti.

8. Rimuovere la possibilità di manipolazione lontano dall'oggetto ottaidrato. A tale scopo, selezionare l'ottaidrato nella gerarchia e deselezionare la casella di controllo "Consenti manipolazione distante" (contrassegnato con un cerchio verde). In questo modo, in modo che gli utenti possono interagire solo con l'ottaidrato usando direttamente le mani rilevate.

>Nota: Per la documentazione completa del componente gestore manipolazione e è associata a impostazioni, consultare il [MRTK documentazione](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html).

9. Assicurarsi che il componente "Quasi interazione Grabbable" è stato aggiunto il nucleo di terra, il modulo lunare e i criteri utente personalizzati di caffè (vedere il passaggio 7).

10. Per il modulo lunare, modificare le impostazioni di gestore di modifica in modo che ruota intorno al centro sia quasi per l'oggetto e distante interazione, come illustrato nell'immagine seguente.

![Lesson4 Chapter2 Step10im](images/Lesson4_chapter2_step10im.PNG)

11: Per i core di terra, modificare il comportamento di rilascio a "nothing". Questo rende affinché il nucleo di terra viene rilasciato da dimestichezza con alcuni degli utenti, non continuare a spostare. 

![Lesson4 Chapter2 Step11im](images/Lesson4_Chapter2_step11im.PNG)

> Nota: Questa impostazione è utile per scenari come la creazione di una palla che è possibile generare. Mantenere la velocità e la velocità angolare semplifica in modo che quando viene rilasciata la palla continuerà a muoversi alla velocità che era simile al modo in cui si comporteranno una palla fisica, rilasciato in.

### <a name="adding-bounding-boxes"></a>Aggiunta di rettangoli
Riquadri di rendono più facile e intuitivo per manipolare gli oggetti con una mano per la manipolazione diretta (accanto all'interazione) e modifica in base al raggio (distante interazione). Rettangoli di selezione dell'offerta "handles" che è possibile utilizzare per la scalabilità e rotazione di oggetti lungo gli assi specifici.
>Nota: Prima di poter aggiungere un rettangolo a un oggetto che è necessario innanzitutto disporre di un collider sull'oggetto (ad esempio, un collider casella.) Come in precedenza in questa lezione. È possibile aggiungere colliders selezionando l'oggetto e nel Pannello di controllo dell'oggetto selezionando Add Component > Collider casella.
>

1. Aggiungere un collider casella all'oggetto core terra, se ne esiste già (collider finestra e il programma di installazione non è necessario se si usa il prefab fornito nella cartella asset di modulo di Base per le istruzioni fornite). Nel caso il nucleo della terra è necessario aggiungere l'oggetto collider casella all'oggetto "node_id30" sotto il nucleo di terra, come illustrato nell'immagine seguente. Selezionare node_id30 e nella scheda di controllo dell'oggetto, fare clic su "Aggiungi componente" e cercare "casella collider". 

![Lesson4 Chapter3 Step1im](images/Lesson4_Chapter3_step1im.PNG)

![Lesson4 Chapter3 Step2im](images/Lesson4_chapter3_step2im.PNG)

> Nota: Assicurarsi che si visualizza l'oggetto collider casella in modo che non è troppo grande o troppo piccolo. Deve essere all'incirca le stesse dimensioni dell'oggetto che è adiacente (in questo esempio, il nucleo della terra). Regolare il collider finestra in base alle esigenze selezionando l'opzione collider modifica nel collider casella. È possibile modificare la x, y e i valori z o trascinare i rettangolo di selezione gestori delle caselle nella finestra dell'editor di scena. 

![Lesson4 Chapter3 Noteim](images/Lesson4_Chapter3_noteim.PNG)

2. Aggiungere un riquadro delimitatore "node_id30" oggetto del core earth. A tale scopo, selezionare l'oggetto "node_id30" da "3DObjectCollection." Nella scheda controllo, fare clic su "Aggiungi componente" e cercare "rettangolo". Assicurarsi che il rettangolo di selezione, collider casella e script di modifica (gestore di modifica, in prossimità di interazione grabbable) siano tutti nello stesso oggetto gioco.

3.  Nella sezione "Comportamento" del rettangolo, selezionare "attiva nel menu start" nell'elenco a discesa di attivazione. Per esaminare altri dettagli riguardanti le varie opzioni di attivazione e altre opzioni della finestra di delimitazione, vedi il [MRTK delimitatore della documentazione di box](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html>)

   

   *In passaggi successivi, si verrà modificato anche l'aspetto di delimitazione regolando il materiale di finestra predefinito, il materiale mentre lo è stato afferrato, nonché la visualizzazione dell'handle (handle d'angolo e laterali). Il MRTK contiene diverse opzioni per personalizzare il riquadro delimitatore.*

4. Nel Pannello di progetto, cercare "boundingbox" e si verrà visualizzato un elenco dei materiali indicato da una sfera blu nei risultati della ricerca, come illustrato nell'immagine seguente. 

5. Trascinare il rettangolo di selezione componente casella il materiale "boundingbox" nello slot di materiale di finestra. Anche agganciare il materiale "boundingboxgrabbed" e inserirlo nello slot di materiale acquisite casella del componente casella delimitazione.

6. Trascinare il materiale "MRTK_BoundingBox_ScaleWidget" nello slot prefab handle scala sul componente casella rettangolo di selezione. 

7. Trascinare il materiale "MRTK_BoundingBox_RotateWidget" nello slot di handle di rotazione del componente casella associazione.

![Lesson4 Chapter3 7Im passaggio 4](images/Lesson4_chapter3_step4-7im.PNG)

8. Assicurarsi che il rettangolo di selezione è destinato l'oggetto a destra. Nel componente casella delimitazione, c'è il "oggetto di destinazione" e "delimita override" script. Assicurarsi di trascinare l'oggetto con il rettangolo di selezione intorno a esso per entrambi questi slot. In questo esempio, trascinare l'oggetto "node_id30" entrambi questi slot, come illustrato nell'immagine seguente.

> Quando si avvia o riprodurre l'applicazione, l'oggetto verrà ora racchiusa da un frame di blu. Siete invitati a trascinare gli angoli di quel frame per ridimensionare l'oggetto. Se si vuole che i quadratini di ridimensionamento e gli handle di rotazione per essere più grande e più visibile, è consigliabile usare il valore predefinito di delimitazione impostazioni della finestra (evitando i passaggi da 4 a 7). 

![Lesson4 Chapter3 Step8im](images/Lesson4_Chapter3_step8im.PNG)

9. Per tornare alla visualizzazione predefinita, nel Pannello di controllo dell'oggetto, del rettangolo delimitatore predefinito selezionare prefab l'handle di rotazione e premere il tasto CANC, verrà ora visualizzato una rettangolo di selezione visualizzazione finestra simile a quella riportata di seguito. Nota: il delimitatore visualizzazioni di finestra viene visualizzata solo quando è in modalità di gioco.

![Lesson4 Chapter3 Step9im](images/Lesson4_chapter3_step9im.PNG)

### <a name="adding-touch-effects"></a>Aggiunta di effetti Touch
In questo esempio verrà per riprodurre un suono effetto quando si tocca un oggetto con una mano.

1. Aggiungere un componente di origine audio per l'oggetto gioco. Selezionare l'oggetto "ottaidrato" nella gerarchia della scena. Nel Pannello di controllo, fare clic sul pulsante "Aggiungi componente", cercare e selezionare "origine audio". Si userà questa origine audio da riprodurre un suono effetto in un passaggio successivo. 

>Nota: Assicurarsi che l'oggetto "Ottaidrato" ha un collider finestra su di esso.

2. Aggiungere il componente "quasi interazione touchable". Fare clic sul pulsante "Add Component" nel Pannello di controllo e cercare "quasi interazione touchable". Selezionare il componente. Nota: correzione screenshot per evidenziare che si sta aggiungendo il componente e non solo evidenziando collider casella.

>Nota: Abbiamo aggiunto in precedenza "quasi interazione grabbable." La differenza tra questo e "quasi interazione touchable" è che l'interazione di "grabbable" è destinato a essere afferrato e interagire con un oggetto. Il componente "touchable" è destinato l'oggetto essere alterato. Entrambi i componenti possono essere usati insieme per una combinazione di interazioni.

![Lesson4 Chapter4 2Im passaggio 1](images/Lesson4_chapter4_step1-2im.PNG)

3. Aggiungere lo script "touch interazione a mano". Si noti che questo script è incluso in scena unity importati come parte di questo pacchetto di demo e non è incluso in MRTK l'originale. Proprio come nel passaggio precedente, fare clic su "Aggiungi componente" e cercare "touch interazione manuale" per aggiungerlo. 
   Si noti che sono disponibili 3 opzioni con lo script: 

   - "Su touch completato." Verrà attivata quando si toccano e rilasciare l'oggetto. 
   - "Su tocco avviato." Verrà attivata quando l'oggetto viene manipolato. 
   - "Su touch aggiornata." Questo attiverà periodicamente mentre la mano tocca l'oggetto. 

   In questo esempio si userà l'impostazione "su tocco avviato".

4. Fare clic sul pulsante "+" l'opzione "on tocco avviato", come illustrato nell'immagine seguente. Trascinare l'oggetto ottaidrato nel campo vuoto. 

5. Nell'elenco a discesa con la dicitura "Nessuna funzione" (superiore al rettangolo verde nell'immagine seguente), selezionare AudioSource > PlayOneShot. Si aggiungerà un clip audio a questo campo usando i concetti illustrati di seguito:

   - Il MRTK offrono un breve elenco di clip audio. È possibile esplorare questi elementi nel Pannello di progetto. Li troverete sotto la cartella "MixedRealityToolkit.SDK" e quindi la cartella "assets standard". Non esiste, si noterà una cartella "audio" dove si trovano tutte le clip audio.
   - In questo esempio si intende usare clip audio "MRTK_Gem". 
   - Per aggiungere un clip audio, è sufficiente trascinare l'immagine desiderata dal pannello progetto la AudioSource.PlayOneShot (contrassegnati con casella verde nell'esempio precedente) nel Pannello di controllo.

   A questo punto quando l'utente raggiunge e tocca l'oggetto ottaidrato, la traccia audio "MRTK_Gem" verrà riprodotto. Lo script "Mano interazione Touch" modificherà anche il colore dell'oggetto quando modificate. 

![Passaggio 3 Chapter4 Lesson4 Noteim 5](images/Lesson4_chapter4_step3-5-noteim.PNG)

### <a name="congratulations"></a>È stata completata 
In questa lezione si è appreso come organizzare oggetti 3D in una raccolta di griglia e come modificare gli oggetti 3D (ridimensionamento, rotazione e spostamento) usando quasi interazione (selezionandola direttamente con le mani rilevate) e l'interazione distante (tramite sguardo rays o rays mano). Inoltre imparato a inserire i rettangoli di selezione intorno a oggetti 3D e imparato a usare e personalizzare il gizmo finestre di delimitazione. Infine, si è appreso come attivare eventi quando si tocca un oggetto.

[Lezione successiva: Input avanzati](mrlearning-base-ch5.md)


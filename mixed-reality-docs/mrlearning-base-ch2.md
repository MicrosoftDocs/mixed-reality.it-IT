---
title: MR Learning modulo di Base - interfaccia utente, a mano di rilevamento e configurazione di Toolkit di realtà mista
description: Completare questo corso di informazioni su come implementare il riconoscimento di volti di Azure all'interno di un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: realtà mista, hololens, esercitazione di unity,
ms.openlocfilehash: 1800d36b7292b9cb53b09fdd4b9c4fb763d49e79
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730947"
---
# <a name="mr-learning-base-module---user-interface-hand-tracking-and-mixed-reality-toolkit-configuration"></a>MR Learning modulo di Base - interfaccia utente, a mano di rilevamento e configurazione di Toolkit di realtà mista

Nella lezione precedente si è appreso alcune delle funzionalità che di MRTK ha da offrire, avviando la prima applicazione per 2 HoloLens. In questa lezione successiva si apprenderà come creare e organizzare i pulsanti con i pannelli di testo dell'interfaccia utente e usare l'interazione predefinito (tocco) per interagire con tutti i pulsanti. Verranno inoltre esplorati l'aggiunta di effetti, ad esempio la modifica delle dimensioni, audio e le operazioni più semplici e il colore degli oggetti. Questo modulo verrà introdotti i concetti di base su come modificare i profili MRTK, a partire da disattivare la visualizzazione della trama spaziale. 

## <a name="objectives"></a>Obiettivi

* Personalizzare e configurare i profili di Toolkit di realtà mista
* L'interazione con vntana usando i pulsanti e gli elementi dell'interfaccia utente
* Le interazioni e base input di rilevamento delle modifiche manuale

## <a name="instructions"></a>Istruzioni

### <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>Come configurare i profili di Toolkit di realtà mista (opzione di visualizzazione di modifica consapevolezza spaziali)
In questa sezione che si apprenderà come personalizzare e configurare i profili di Toolkit di realtà mista predefinita modificando l'opzione di visualizzazione di spaziale di consapevolezza riguardo alla mesh. È possibile seguire gli stessi principi per la configurazione delle impostazioni o i valori nei profili MRTK.

1. Selezionare il Toolkit di realtà mista (MRTK) dalla gerarchia di "BaseScene". Nel Pannello di controllo, cercare "Misto realtà Toolkit Script" e selezionare il profilo"attivo", come illustrato nella figura seguente. Fare doppio clic per aprirlo.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step1im.PNG)

>Nota: Per impostazione predefinita, i profili MRTK non sono modificabili. Questi sono i modelli di profilo predefinito da cui è possibile copiare e personalizzare. Esistono diversi livelli di personalizzazione e profili, pertanto è prassi standard copiare e personalizzare i profili diversi durante la configurazione di una o più impostazioni.
>
>Per altre informazioni sui profili MRTK e la relativa architettura, visitare il [documentazione MRTK](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Architecture/SpatialAwareness/SpatialAwarenessSystemArchitecture.html>).

2. Creare una copia del profilo predefinito per personalizzarlo. Per copiare un profilo predefinito, il "copia e personalizzare" fare clic sul pulsante (vedere la figura). In questo modo viene creata una copia del profilo MRTK. Con una copia del profilo MRTK, ora è possibile personalizzare le impostazioni in questo profilo. Inoltre, è necessario ripetere il passaggio di copia/personalizzare per eventuali altri profili nidificati sotto questo profilo, come descritto nei passaggi successivi.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step2im.PNG)

3. Disattivare la visibilità della mesh consapevolezza spaziale. A tale scopo, trovare "Spaziali consapevolezza System Settings", come illustrato nell'immagine. Fare clic sul pulsante "clone" a destra dell'il "spaziali consapevolezza profilo del sistema" per sostituire il profilo predefinito con una copia personalizzabile. Se viene visualizzata una finestra popup, premere il pulsante "Clone", come illustrato nell'immagine secondo seguente.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3im.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3bim.jpg)

4. Creare una copia personalizzata di predefinito Mixed realtà spaziali Mesh Observer. Fare clic sulla freccia verso il basso accanto a "Windows misti realtà spaziali Mesh osservatore" per visualizzare opzioni aggiuntive. In queste opzioni, verrà visualizzato "Predefinito misto realtà spaziali Mesh Observer" che appare disabilitato (non modificabile). È necessario sostituire questo profilo predefinito con una copia personalizzabile in modo che può essere modificata. Per clonare una copia, fare clic sul pulsante a destra (contrassegnato da una freccia verde).

![MR213_BuildSettings](images/mrlearning-base-ch2-1step4im.PNG)

5. Successivamente, saranno modificate le impostazioni per l'opzione di visualizzazione pronunciare "occlusione." Ciò rende invisibile la mesh spaziale, ma comunque nascondere gli oggetti gioco dietro la mesh spaziale (questo è noto come occlusione.)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step5im.PNG)

>Nota: Mentre la rete mesh di mapping spaziale non è visibile, è ancora presente e può interagire con esso. Qualsiasi vntana dietro la mesh mapping spaziale (ad esempio, un ologrammi dietro la parete visibile) non saranno visibili a causa dell'impostazione relative all'occlusione.

La procedura è stata completata. Appena appreso come modificare un'impostazione nel profilo MRTK. Come può notare, per modificare le impostazioni MRTK è necessario creare copie dei profili predefiniti in modo che è possibile modificarle. Avere sempre i profili predefiniti (che non sono modificabili) per tornare alla se si desidera creare un profilo con nuove impostazioni o fare riferimento a profili predefiniti. Esistono numerose impostazioni che è possibile modificare. Per informazioni di riferimento complete per le impostazioni del profilo MRTK, consultare la documentazione di MRTK qui: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html

### <a name="hand-tracking-gestures-and-interactable-buttons"></a>Pulsanti si e i movimenti della mano di rilevamento
In questa sezione si apprenderà come usare mano la per premere un pulsante si verifica.

1. Selezionare la cartella progetti "Risorse".

2. Digitare nella casella di ricerca, "pressablebutton."

![MR213_BuildSettings](images/mrlearning-base-ch2-2step1im.PNG)

3. Trascinare il prefab (rappresentato da una casella blu) denominato "PressableButton" nella gerarchia. 

   > Nota: Se viene visualizzato un messaggio "importazione TMP Essentials" importarlo in questo momento. Se TMP Essentials non era già parte del progetto, si potrebbe essere necessario ripetere questo passaggio dopo l'importazione Essentials TMP, potrebbe non essere visualizzato in caso contrario, il testo del pulsante.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step3im.PNG)

4. Fare doppio clic sull'oggetto di gioco "PressableButton" (che dovrebbe essere ora nella gerarchia BaseScene) per visualizzarlo nella scena, come illustrato nell'immagine seguente (la grafica pulsante può apparire diversa rispetto a quella riportata di seguito). 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step4im.PNG)

5. Nel Pannello di controllo, fare clic su "Aggiungi evento" per assegnare un evento a cui rispondere quando il push al pulsante. Nell'opzione che viene visualizzato, selezionare il menu di scelta rapida. Selezionare "InteractableOnPressReciever." In questo modo il pulsante rispondere a un evento premuto quando una mano rilevata preme il pulsante.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step5im.PNG)

6. Aggiungere un cubo alla scena. Fare clic con il pulsante destro sull'area di gerarchia, selezionare l'oggetto 3D, quindi fare clic su "cube". A questo punto, la visualizzazione deve essere un cubo. Verrà visualizzato molto grande, modificare le coordinate (mentre "cube" sia ancora selezionata nell'area di gerarchia) per ridurre le dimensioni. Impostare i valori di scala x = 0,1, y = compresa tra 0.1 e z = 0,1. Essere assicurarsi di posizionare il cubo nella scena deve essere posizionato accanto al pulsante pressable, ma non sovrapposte con il pulsante. Nell'immagine seguente, posizione del cubo è x = 0, y = 0.2 e z = 1. 

   > Nota: 1 unità in Unity in generale, è quasi equivalente a 1 metro nel mondo fisico. Sono presenti eccezioni, ad esempio quando gli oggetti sono elementi figlio degli oggetti in scala.
   
   ![MR213_BuildSettings](images/mrlearning-base-ch2-1step6ima.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-2step6imb.PNG)

7. In questo passaggio si configurerà il cubo per modificare il colore quando viene premuto il pulsante. Selezionare il PressableButton nel menu "BaseScene". Nel Pannello di controllo, sotto la casella "Selezionare tipo di evento", fare clic sul pulsante "+". Trascinare il "cube" dal menu "BaseScene" nella casella di "Runtime solo" come illustrato nell'immagine riportata di seguito

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7ima.PNG)

Fare clic sull'elenco a discesa con la dicitura "Nessuna funzione". Selezionare "MeshRenderer" quindi "material Material". In questo modo sarà possibile modificare il materiale quando viene premuto il pulsante. 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imb.PNG)

Passare al pannello progetto e cercare il materiale di cui che si desidera modificarlo in base ai. Prevede di usare il materiale "MRTK_Standard_Cyan" in questo esempio, disponibile digitando "ciano" nella barra di ricerca della scheda project (MRTK The include numerosi materiali e i colori). Trascinare il materiale per la casella sotto "MeshRenderer.material." I materiali MRTK sono reperibile negli asset > MixedRealityToolkit.SDK > StandardAssets > materiali.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imbb.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step7imc.PNG)

L'evento è ora impostata in modo che quando viene premuto il pulsante, il cubo cambia colore in base al materiale che è stato specificato. In questo esempio, il cubo cambierà il colore ciano.

8. Successivamente si desidera configurare l'azione di rilascio in modo che al rilascio, il pulsante diventerà nuovamente sul colore predefinito. Ripetere il passaggio 7, ovvero il passaggio precedente, ma questa volta con l'evento "OnRelease" invece dell'evento "OnPress", come illustrato nell'immagine seguente.

9.  Nel Pannello di progetto, cercare un materiale per il cubo per impostazione predefinita al pulsante rilasciare (in questo caso, abbiamo scelto MRTK_Standard_LightGray.) Trascinare il materiale nella casella sotto il campo "MeshRenderer.material".

![MR213_BuildSettings](images/mrlearning-base-ch2-2step8im.PNG)

A questo punto quando viene premuto il pulsante, è necessario modificare un nuovo colore (ad esempio cyan) e quando viene rilasciato il pulsante dovrebbe risultare nuovamente il colore predefinito specificato (ad esempio, grigio chiaro.) Fare clic sul pulsante "play" nella parte superiore della schermata per provarlo nell'editor o la distribuzione in 2 di HoloLens da testare. Per altre informazioni sulla simulazione di nell'editor, tra cui simulazione manuale leggere il [pagina della documentazione di simulazione del MRTK](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html>). 

### <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>Creazione di un pannello dei pulsanti tramite raccolta della MRTK di oggetti della griglia

In questa sezione si apprenderà come allineare automaticamente più pulsanti in un'interfaccia utente brillante utilizzando lo strumento GridObjectCollection del MRTK.

1. Duplica il pulsante dalla sezione precedente fino a quando non sono presenti i 5 pulsanti. Esistono diversi modi per eseguire questa operazione:
- Fare clic con il pulsante destro fare clic su "copia", quindi verso il basso per sotto il pulsante e fare clic nuovamente e fare clic "Incolla". 
- Fare clic con il pulsante destro e fare clic su "duplicate". 
- Usare il comando di tasti facendo clic sul cubo e premere "ctrl D" sulla tastiera.

Ripetere questo passaggio fino a quando non sono presenti i pulsanti di totali 5 (vedere 5 frecce di colore rosso nell'immagine seguente).

![Base Mrlearning Ch2 3Step1im](images/mrlearning-base-ch2-3step1im.PNG)

2. Gruppo di pulsanti in un oggetto gioco padre vuoto. Per i pulsanti nell'insieme di griglia, è necessario raggruppare i pulsanti in un oggetto padre comune. Fare clic con il pulsante destro nel hiearachy e fare clic su "Crea vuoto". In questo modo viene creata un nuovo oggetto gioco vuoto di mettere tutti i pulsanti. Verrà visualizzato come "gameObject." Fare clic e rinominarlo in "ButtonCollection."

![Base Mrlearning Ch2 3Step2im](images/mrlearning-base-ch2-3step2im.PNG)

3. Spostare tutti i pulsanti nella nuova raccolta. Eseguire questa operazione selezionando tutti e cinque gli oggetti pulsante nella finestra di heirarch e trascinarli tutto dietro "ButtonCollection" oggetto gioco, come illustrato nell'immagine seguente. Suggerimento: selezionare più elementi tenendo premuto il tasto ctrl mentre si seleziona voci.

![Base Mrlearning Ch2 3Step3imb](images/mrlearning-base-ch2-3step3imb.PNG)

4. Aggiungere il componente di "Raccolta di oggetti della griglia" del MRTK insieme di pulsanti.  A tale scopo, selezionare l'oggetto padre "ButtonCollection" e nel Pannello di controllo, fare clic sul pulsante "Add Component". Quindi cercare "Raccolta di oggetti della griglia" nella barra di ricerca e selezionarlo quando viene visualizzato nell'elenco.

![Base Mrlearning Ch2 3Step4im](images/mrlearning-base-ch2-3step4im.PNG)

Il componente di raccolta di oggetti della griglia consente di organizzare i pulsanti o qualsiasi set di oggetti in una riga brillante, una colonna o una griglia. Questo è uno dei blocchi predefiniti forniti da MRTK che offre un modo semplice e rapido per creare interfacce utente accattivanti.

5. Configurare la raccolta di oggetti della griglia. Per garantire all'utente tutti la faccia di pulsanti, selezionare "orientare tipo" e quindi selezionare "affrontano padre forward" (come illustrato nell'immagine.) Successivamente, modificare la dimensione della cella per impostare lo spazio tra i pulsanti. Iniziare con unità 0,12 dalle unità 0,12 per la larghezza di cella e l'altezza della cella, come illustrato nell'immagine seguente. Potrebbe essere necessario modificare questi valori, a seconda delle risorse e/o pulsanti oggetto scelti. Assicurarsi che "Rows" è impostato su 1. Quindi fare clic su "Aggiorna raccolta" e la scena dovrebbe essere simile all'immagine seguente. 


![Base Mrlearning Ch2 3Step5im](images/mrlearning-base-ch2-3step5im.PNG)

>Nota: A seconda dell'orientamento degli oggetti figlio o padre dell'oggetto, sarà probabilmente necessario modificare l'orientamento l'impostazione in modo diverso nei progetti futuri. La larghezza della cella e i campi di altezza della cella potrebbe essere necessario anche essere definiti in modo diverso, a seconda delle dimensioni degli oggetti nella raccolta.

### <a name="adding-text-into-your-scene"></a>Aggiunta di testo nella scena

In questa sezione si apprenderà come aggiungere e modificare il testo per l'esperienza di realtà mista. Se hai già fatto, assicurarsi di aver TextMeshPro abilitata in Unity seguendo le istruzioni riportate [qui](https://docs.unity3d.com/Packages/com.unity.textmeshpro@2.0/manual/index.html#installation).

1. Selezionare l'oggetto padre "ButtonCollection" e fare clic con il pulsante destro la raccolta. Espandere "oggetto 3D" nel menu a discesa, quindi selezionare "TextMeshPro – Text". Dovrebbe essere un oggetto TextMeshPro sotto l'insieme di pulsanti, come illustrato nell'immagine seguente.

![Flusso della lezione 2 Chapter4 Step1a](images/Lesson2_Chapter4_Step1a.JPG)
![Step1b Chapter4 della lezione 2](images/Lesson2_Chapter4_Step1b.JPG)

2. Nel campo di testo del componente TextMeshPro (che si trova nel Pannello di controllo, come illustrato di seguito), digitare "Testo del pulsante raccolta". Il testo verrà visualizzato nella scena, ma verrà nascosto dietro i pulsanti e/o di dimensioni errata.

![Passaggio 2 Chapter4 della lezione 2](images/Lesson2_Chapter4_Step2.JPG)

3. Per migliorare le dimensioni di testo e la selezione host per migliorare la leggibilità, modificare il campo "dimensioni del carattere" nel componente TextMeshPro per modificare le dimensioni del tipo di carattere. È necessario anche modificare la posizione "Rect trasformazione" e la scala come illustrato nell'immagine seguente. Visualizzare le immagini di sotto di valori utilizzati per la configurazione di testo ed è possibile usare questi valori come punto di partenza da cui si desidera migliorare ulteriormente le dimensioni e la posizione del campo di testo.

![Passaggio 3 di flusso della lezione 2 Chapter4](images/Lesson2_Chapter4_Step3.JPG)
![passaggio 4 Chapter4 della lezione 2](images/Lesson2_Chapter4_Step4.JPG)

5. Per modificare i valori di testo negli oggetti pulsante, fare clic sulla freccia accanto al pulsante qualsiasi per espanderlo e passare all'oggetto "SeeItSayItLabel", quindi passare a "TextMeshPro", in cui è possibile modificare il testo per i pulsanti come descritto nei passaggi precedenti.

![Passaggio 5 Chapter4 della lezione 2](images/Lesson2_Chapter4_Step5.JPG)

### <a name="congratulations"></a>È stata completata
In questa lezione è stato descritto come copiare, personalizzare e configurare un'impostazione del profilo MRTK (ad esempio, la consapevolezza spaziali mesh visibilità.) Inoltre appreso come interagire con un pulsante per attivare eventi utilizzando le mani rilevate su 2 HoloLens. Infine, si è appreso come creare una semplice interfaccia dell'interfaccia utente usando Unity testo Mesh Pro raccolta di oggetti della griglia componente del MRTK.

[Lezione successiva: Risolutori e posizionamento del contenuto dinamico](mrlearning-base-ch3.md)


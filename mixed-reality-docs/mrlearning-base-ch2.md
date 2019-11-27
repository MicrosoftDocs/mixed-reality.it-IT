---
title: Esercitazioni introduttive-3. Creazione dell'interfaccia utente e configurazione del Toolkit per realtà mista
description: Completa questo corso per apprendere come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: f0a54bb591479dbe8ffa719cb5e6a9d846f67f9e
ms.sourcegitcommit: 83698638b93c5ba77b3ffc399f1706482539f27b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/26/2019
ms.locfileid: "74539738"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a>3. creazione dell'interfaccia utente e configurazione del Toolkit per la realtà mista

Nella lezione precedente sono state illustrate alcune delle funzionalità offerte dal Toolkit di realtà mista (MRTK) avviando la prima applicazione per HoloLens 2. In questa lezione successiva verrà illustrato come creare e organizzare i pulsanti insieme ai pannelli di testo dell'interfaccia utente e come utilizzare l'interazione predefinita (tocco) per interagire con ciascun pulsante. Potrai inoltre esplorare alcuni effetti e azioni semplici, ad esempio la modifica delle dimensioni, del suono e del colore degli oggetti. Questo modulo introduce i concetti di base sulla modifica dei profili MRTK, a partire dalla disattivazione della visualizzazione Mesh di [mapping spaziale](spatial-mapping.md) .

## <a name="objectives"></a>Obiettivi

* Personalizzare e configurare i profili di Mixed Reality Toolkit
* Interagire con gli ologrammi usando gli elementi e i pulsanti dell'interfaccia utente
* Eseguire interazioni e input di tracciamento delle mani

## <a name="instructions"></a>Istruzioni

### <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>Come configurare i profili del Toolkit di realtà mista (opzione di visualizzazione modifica consapevolezza spaziale)

In questa sezione si apprenderà come personalizzare e configurare i profili MRTK predefiniti regolando l'opzione di visualizzazione della mesh di riconoscimento spaziale. Puoi seguire gli stessi principi per modificare le impostazioni o i valori nei profili di MRTK.

1. Selezionare il Toolkit di realtà mista (MRTK) dalla gerarchia di BaseScene. Nel pannello Inspector cercare lo script Mixed Reality Toolkit e selezionare il profilo attivo, come illustrato nella figura seguente. Fare doppio clic per aprirlo.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step1.png)

    >[!NOTE]
    >per impostazione predefinita, i profili di MRTK non sono modificabili. Si tratta di modelli di profilo predefiniti che è possibile copiare e personalizzare. Sono disponibili diversi livelli di personalizzazione e profili. È quindi consigliabile copiare e personalizzare diversi profili quando si configurano una o più impostazioni.
    >
    >Per altre informazioni sui profili MRTK e la relativa architettura, vedere la [documentazione di MRTK](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html>).

2. Crea una copia del profilo predefinito per personalizzarlo. Per iniziare, fare clic su **copia & Personalizza**.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step2a.png)

    Verrà visualizzata la finestra popup *profilo clone* .

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step2b.png)

    Fare clic su **clona** per creare una copia del profilo MRTK. Con la propria copia del profilo MRTK è ora possibile personalizzare le impostazioni in questo profilo. Sarà inoltre necessario ripetere il passaggio copia e personalizzazione per tutti i profili aggiuntivi nidificati sotto questo profilo, come descritto nei passaggi successivi.

3. Disabilita la visibilità della mesh di consapevolezza spaziale. A tale scopo, individuare le impostazioni del sistema di riconoscimento spaziale come illustrato nell'immagine seguente. Verificare che l'opzione **Abilita il sistema di riconoscimento spaziale** sia selezionata. Fare clic sul pulsante **clona** a destra del profilo di sistema di riconoscimento spaziale per sostituire il profilo predefinito con una copia personalizzabile. Nella finestra popup visualizzata premere il pulsante **Clone** , come illustrato nella seconda immagine riportata di seguito.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step3a.png)

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step3b.png)

4. Crea una copia personalizzata dell'osservatore predefinito della mesh spaziale della realtà mista. Fare clic sulla freccia verso il basso accanto all'Observer di rete spaziale di realtà mista di Windows per visualizzare altre opzioni.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step4a.png)

    In queste opzioni verrà visualizzato l'osservatore mesh spaziale della realtà mista predefinito, non modificabile. Devi sostituire questo profilo predefinito con una copia personalizzabile in modo da poterla modificare. Come è stato fatto in precedenza, fare clic sul pulsante **clona** e quindi, nella finestra popup visualizzata, premere il pulsante **Clone** , come illustrato nella seconda immagine riportata di seguito.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step4b.png)

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step4c.png)

5. Modifica quindi l'impostazione dell'opzione di visualizzazione specificando "Occlusion" (Occlusione). In questo modo la mesh del mapping spaziale è invisibile, ma nasconde comunque gli oggetti di gioco dietro la mesh di mapping spaziale, nota anche come occlusione.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step5.png)

    >[!NOTE]
    >Nota: mentre la mesh di mapping spaziale non è visibile, è ancora presente ed è possibile interagire con essa. Gli ologrammi dietro la mesh di mapping spaziale, ad esempio un ologramma dietro la parete visibile, non saranno visibili a causa dell'impostazione di occlusione.

Complimenti. hai appreso come modificare un'impostazione nel profilo di MRTK. Come puoi notare, per modificare le impostazioni di MRTK devi creare copie dei profili predefiniti in modo da poterle modificare. Si avranno sempre i profili predefiniti, che non sono modificabili, per tornare a se si desidera creare un profilo con nuove impostazioni oppure è possibile fare riferimento ai profili predefiniti. Esistono numerose impostazioni che puoi modificare. Per informazioni di riferimento complete sulle impostazioni del profilo MRTK, vedere la documentazione di MRTK qui: [https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)

### <a name="hand-tracking-gestures-and-interactable-buttons"></a>Movimenti di tracciamento delle mani e pulsanti con supporto per interazioni

In questa sezione si apprenderà come usare il rilevamento manuale per premere un pulsante stampabile.

1. Selezionare asset dalla cartella progetti.

2. Digitare "PressableButtonHoloLens2" nella barra di ricerca.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step2.png)

3. Trascinare il prefabbricato (rappresentato da una casella blu) denominato "PressableButtonHoloLens2" nella gerarchia e impostare imposta i valori di posizione su x = 0, y = 0 e z = 0,2, in modo che il pulsante si trovi davanti alla fotocamera. La fotocamera è posizionata in corrispondenza dell'origine.

    >[!NOTE]
    >Se si riceve un messaggio relativo all'importazione di elementi di base di TMP, importarlo in questo momento. Se TMP Essentials non fa già parte del progetto, potrebbe essere necessario ripetere questo passaggio dopo aver importato TMP Essentials. in caso contrario, il testo del pulsante potrebbe non essere visualizzato.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step3.png)

4. Aggiungi un cubo alla scena. Fare clic con il pulsante destro del mouse sull'area gerarchia, selezionare un oggetto 3D, quindi fare clic su cubo.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step6a.png)

    A questo punto, sullo schermo dovrebbe essere visualizzato un cubo. Verrà visualizzato molto grande. Per ridurre le dimensioni, è possibile modificare le coordinate (mentre il cubo è ancora selezionato nell'area della gerarchia). Impostare i valori di scala su x = 0,02, y = 0,02 e z = 0,02. Assicurarsi di posizionare il cubo nella scena accanto al pulsante, ma non sovrapposto. Nell'immagine seguente la posizione del cubo è x = 0, y = 0,4 e z = 0,2.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step6b.png)

    >[!NOTE]
    >in generale, 1 unità in Unity equivale quasi a 1 metro nel mondo fisico. Ci sono alcune eccezioni. ad esempio, quando gli oggetti sono elementi figlio di oggetti ridimensionati.

5. Con l'oggetto del gioco PressableButtonHoloLens2 selezionato, scorrere verso la parte inferiore del controllo per individuare la sezione degli eventi del componente interactable (script).

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step4.png)

6. Si modificherà l'evento esistente per fornire al pulsante un evento a cui rispondere quando viene eseguito il push. Come si può notare, il tipo di ricevitore di eventi è impostato su InteractableOnPressReceiver. In questo modo il pulsante risponde a un evento di pressione quando una mano tracciata preme il pulsante. A questo punto, è necessario modificare anche il filtro interazione in near e lontano.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step5.png)

7. In questo passaggio configurerai il cubo in modo da cambiare colore quando viene premuto il pulsante. Selezionare PressableButtonHoloLens2 nella gerarchia BaseScene e trascinare l'oggetto Game Cube dalla gerarchia BaseScene nel campo Runtime only, come illustrato nell'immagine seguente.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step7a.png)

    Fare clic sull'elenco a discesa che indica nessuna funzione. Selezionare MeshRenderer, quindi materiale materiale. In questo modo è possibile modificare il materiale quando viene premuto il pulsante.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step7b.png)

    Fare clic sul cerchio accanto al campo materiale vuoto per aprire la finestra popup Seleziona materiale. Il MRTK include molti materiali e colori tra cui scegliere. Per questo esempio, si userà il materiale MRTK_Standard_Cyan trovato digitando "MRTK_Standard" nella barra di ricerca popup. Selezionare il materiale MRTK_Standard_Cyan per popolare il campo Material.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step7c.png)

    L'evento è ora impostato in modo che, quando il pulsante viene premuto, il cubo cambi colore in base al materiale specificato. In questo esempio il cubo assumerà il colore ciano.

8. Successivamente, si imposterà l'azione di rilascio in modo che, al rilascio, il pulsante torni al colore predefinito. Ripetere il passaggio 7 sopra. Tuttavia, questa volta con l'evento onRelease invece che con onPress MRTK_Standard_LightGray Material come illustrato nell'immagine seguente.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step8.png)

    A questo punto, quando si preme il pulsante, questo verrà modificato in un nuovo colore; ciano. Quando il pulsante viene rilasciato, viene modificato nuovamente sul colore predefinito specificato, ad esempio grigio chiaro. Premere il pulsante Riproduci nella parte superiore della schermata per provarlo nell'editor o distribuirlo in HoloLens 2, per eseguire il test. Per altre informazioni sulla simulazione in-Editor, inclusa la simulazione della mano, vedere la [pagina della documentazione di simulazione di MRTK](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html>).

### <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>Creazione di un pannello di pulsanti con la raccolta di oggetti griglia di MRTK

In questa sezione si apprenderà come allineare automaticamente più pulsanti in un'interfaccia utente accurata usando lo strumento GridObjectCollection di MRTK.

1. Duplicare il pulsante della sezione precedente finché non sono disponibili cinque pulsanti. Sono disponibili diversi modi per eseguire questa operazione: fare clic con il pulsante destro del mouse sul pulsante e scegliere Copia. Quindi, andare sotto il pulsante e fare di nuovo clic con il pulsante destro del mouse, quindi scegliere Incolla.
    Fare clic con il pulsante destro del mouse sul pulsante e scegliere Duplica.
    -Utilizzare il comando della tastiera facendo clic sul cubo e premendo CTRL D sulla tastiera.

    Ripetere l'operazione fino a cinque pulsanti. vedere le cinque frecce rosse nell'immagine seguente.

    ![Modulo di apprendimento di base sulla realtà mista Capitolo 2 Passaggio 3 Immagine 1](images/mrlearning-base-ch2-3step1im.PNG)

2. Raggruppa i pulsanti in un oggetto gioco padre vuoto. Per avere i pulsanti nella raccolta della griglia, è necessario raggruppare i pulsanti in un oggetto padre comune. Fare clic con il pulsante destro del mouse su hiearachy e scegliere Crea vuoto. In questo modo viene creato un nuovo oggetto gioco vuoto in cui includere tutti i pulsanti. Viene visualizzato come gameObject. Fare clic con il pulsante destro del mouse e rinominarlo, Buttoncollection.

    ![Modulo di apprendimento di base sulla realtà mista Capitolo 2 Passaggio 3 Immagine 2](images/mrlearning-base-ch2-3step2im.PNG)

3. Sposta tutti i pulsanti nella nuova raccolta. A tale scopo, selezionare tutti e cinque gli oggetti pulsante in gerarchia e trascinarli tutti in oggetto gioco Buttoncollection, come illustrato nell'immagine seguente. Suggerimento: selezionare più elementi tenendo premuto il tasto CTRL mentre si selezionano gli elementi.

    ![Modulo di apprendimento di base sulla realtà mista Capitolo 2 Passaggio 3 Immagine 3](images/mrlearning-base-ch2-3step3imb.PNG)

4. Aggiungere il componente della raccolta di oggetti Grid di MRTK alla raccolta dei pulsanti. A tale scopo, selezionare l'oggetto Buttoncollection padre. Dal pannello di controllo fare clic sul pulsante Aggiungi componente. Cercare la raccolta di oggetti Grid nella barra di ricerca e selezionarla quando viene visualizzata nell'elenco.

    ![Modulo di apprendimento di base sulla realtà mista Capitolo 2 Passaggio 3 Immagine 4](images/mrlearning-base-ch2-3-step4.png)

    Il componente della raccolta di oggetti Grid consente di organizzare i pulsanti o qualsiasi set di oggetti in una riga, una colonna o una griglia ordinata. Questo è uno dei blocchi predefiniti forniti da MRTK che offre un modo rapido e semplice per creare interfacce utente accattivanti.

5. Configura la raccolta di oggetti griglia. Per assicurarsi che tutti i pulsanti facciano parte dell'utente, selezionare Orient Type. Quindi selezionare Face padre avanti come illustrato nell'immagine seguente. Modifica quindi le dimensioni della cella per impostare lo spazio tra i pulsanti. Iniziare con 0,05 unità per 0,05 unità per la larghezza della cella e l'altezza della cella, come illustrato nell'immagine seguente. Verificare che distance sia impostato su 0 e che Rows sia impostato su 1. Fare clic su Aggiorna raccolta. La scena sarà simile all'immagine seguente.

    ![Modulo di apprendimento di base sulla realtà mista Capitolo 2 Passaggio 3 Immagine 5](images/mrlearning-base-ch2-3-step5.png)

    >[!NOTE]
    >a seconda dell'orientamento degli oggetti figlio o dell'oggetto padre, sarà probabilmente necessario modificare l'impostazione dell'orientamento in modo diverso nei progetti futuri. È probabile che sia necessario definire in modo diverso anche i valori dei campi Cell Width (Larghezza cella) e Cell Height (Altezza cella), a seconda delle dimensioni degli oggetti nella raccolta.

### <a name="adding-text-into-your-scene"></a>Aggiunta di testo nella scena

In questa sezione apprenderai come aggiungere e modificare il testo nelle esperienze di realtà mista. Se non è già stato fatto, assicurarsi che TextMeshPro sia abilitato in Unity seguendo le istruzioni riportate [qui](https://docs.unity3d.com/Packages/com.unity.textmeshpro@2.0/manual/index.html#installation).

1. Selezionare l'oggetto Buttoncollection padre e fare clic con il pulsante destro del mouse sulla raccolta. Espandere oggetto 3D nel menu a discesa. Quindi selezionare TextMeshPro-text. Verrà visualizzato un oggetto TextMeshPro nella raccolta dei pulsanti, come illustrato nell'immagine seguente.

    ![della lezione 2 Chapter4 Step1a](images/Lesson2_Chapter4_Step1a.JPG) ![della lezione 2 Chapter4 Step1b](images/Lesson2_Chapter4_Step1b.JPG)

2. Per migliorare le dimensioni del testo e la posizione per la leggibilità, modificare il campo relativo alla dimensione del carattere nel componente TextMeshPro per modificare la dimensione del tipo di carattere. Sarà anche necessario modificare la posizione e la scala della trasformazione Rect, come illustrato nell'immagine seguente. Vedere le immagini seguenti per i valori usati per la configurazione del testo. È possibile usare questi valori come punto di partenza per migliorare ulteriormente le dimensioni e la posizione del campo di testo.

    ![Della lezione 2 Chapter4 passaggio 3](images/mrlearning-base-ch2-4-step3.png)

3. Nel campo di testo del componente TextMeshPro nel pannello Inspector, digitare "button Collection text" e modificare le proprietà di allineamento in modo che siano Center e top, come illustrato nell'immagine seguente.

    ![Della lezione 2 Chapter4 passo 4](images/mrlearning-base-ch2-4-step4.png)

4. Per modificare i valori di testo negli oggetti Button, fare clic sulla freccia accanto a qualsiasi pulsante per espanderlo e passare all'oggetto SeeItSayItLabel. Passare a TextMeshPro, in cui è possibile modificare il testo nei pulsanti, come descritto nei passaggi precedenti.

    ![Lezione 2 capitolo 4 passaggio 5](images/Lesson2_Chapter4_Step5.JPG)

## <a name="congratulations"></a>Lezione completata

In questa lezione si è appreso come copiare, personalizzare e configurare un'impostazione del profilo MRTK (ad esempio, la visibilità della rete di riconoscimento spaziale). Si è anche appreso come interagire con un pulsante per attivare gli eventi usando le mani tracciate in HoloLens 2. Infine, si è appreso come creare una semplice interfaccia dell'interfaccia utente usando la funzionalità text mesh Pro di Unity e il componente Grid Object Collection di MRTK.

[Lezione successiva: 4. posizionamento del contenuto dinamico e uso dei risolutori](mrlearning-base-ch3.md)

---
title: Modulo di apprendimento di base sulla realtà mista - Interfaccia utente, tracciamento delle mani e configurazione di Mixed Reality Toolkit
description: Completa questo corso per informazioni su come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 1800d36b7292b9cb53b09fdd4b9c4fb763d49e79
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2019
ms.locfileid: "65730947"
---
# <a name="mr-learning-base-module---user-interface-hand-tracking-and-mixed-reality-toolkit-configuration"></a>Modulo di apprendimento di base sulla realtà mista - Interfaccia utente, tracciamento delle mani e configurazione di Mixed Reality Toolkit

Nella lezione precedente hai appreso alcune delle funzionalità offerte da MRTK avviando la tua prima applicazione per HoloLens 2. In questa lezione apprenderai come creare e organizzare i pulsanti con i pannelli di testo dell'interfaccia utente e usare l'interazione predefinita (tocco) per interagire con ogni pulsante. Potrai inoltre esplorare alcuni effetti e azioni semplici, ad esempio la modifica delle dimensioni, del suono e del colore degli oggetti. Questo modulo presenterà i concetti di base relativi alla modifica dei profili di MRTK, a partire dalla disabilitazione della visualizzazione della mesh spaziale. 

## <a name="objectives"></a>Obiettivi

* Personalizzare e configurare i profili di Mixed Reality Toolkit
* Interagire con ologrammi usando pulsanti ed elementi dell'interfaccia utente
* Eseguire interazioni e input di tracciamento delle mani

## <a name="instructions"></a>Istruzioni

### <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>Come configurare i profili di Mixed-Reality Toolkit (modifica dell'opzione di visualizzazione della mesh di consapevolezza spaziale)
In questa sezione apprenderai come personalizzare e configurare i profili predefiniti di Mixed Reality Toolkit modificando l'opzione di visualizzazione della mesh di consapevolezza spaziale. Puoi seguire gli stessi principi per modificare le impostazioni o i valori nei profili di MRTK.

1. Seleziona Mixed-Reality Toolkit (MRTK) dalla gerarchia di "BaseScene". Nel pannello di controllo cerca "Mixed Reality Toolkit Script" e seleziona il "profilo attivo", come illustrato nella figura seguente. Fai doppio clic per aprirlo.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step1im.PNG)

>Nota: per impostazione predefinita, i profili di MRTK non sono modificabili. Questi sono i modelli di profilo predefiniti che puoi copiare e personalizzare. Esistono diversi livelli di personalizzazione e profili. È pertanto prassi comune copiare e personalizzare alcuni profili durante la configurazione di una o più impostazioni.
>
>Per altre informazioni sui profili di MRTK e sulla relativa architettura, consulta la [documentazione di MRTK](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Architecture/SpatialAwareness/SpatialAwarenessSystemArchitecture.html>).

2. Crea una copia del profilo predefinito per personalizzarlo. Per copiare un profilo predefinito, fai clic sul pulsante "Copy & Customize" (Copia e personalizza), come illustrato nell'immagine. In questo modo viene creata una copia del profilo di MRTK. Con la tua copia del profilo di MRTK, puoi ora personalizzare le impostazioni del profilo. Dovrai ripetere il passaggio di copia/personalizzazione anche per gli eventuali altri profili annidati sotto questo profilo, come descritto nei passaggi successivi.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step2im.PNG)

3. Disabilita la visibilità della mesh di consapevolezza spaziale. Per eseguire questa operazione, trova "Spatial Awareness System Settings" (Impostazioni sistema di consapevolezza spaziale), come illustrato nell'immagine. Fai clic sul pulsante "Clone" (Clona), a destra del profilo del sistema di consapevolezza spaziale, per sostituire il profilo predefinito con una copia personalizzabile. Se viene visualizzata una finestra popup, fai clic sul pulsante "Clone" (Clona), come illustrato nella seconda immagine seguente.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3im.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3bim.jpg)

4. Crea una copia personalizzata dell'osservatore predefinito della mesh spaziale della realtà mista. Fai clic sulla freccia giù accanto a "Windows Mixed Reality Spatial Mesh Observer" (Osservatore mesh spaziale Windows Mixed Reality) per visualizzare altre opzioni. In queste opzioni potrai notare che "Default Mixed Reality Spatial Mesh Observer" (Osservatore predefinito mesh spaziale realtà mista) risulta disabilitata, ovvero non è modificabile. Devi sostituire questo profilo predefinito con una copia personalizzabile in modo da poterla modificare. Fai clic sul pulsante a destra (contrassegnato da una freccia verde) per clonare una copia.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step4im.PNG)

5. Modifica quindi l'impostazione dell'opzione di visualizzazione specificando "Occlusion" (Occlusione). In questo modo, la mesh spaziale diventa invisibile, ma gli oggetti gioco rimangono comunque nascosti dietro la mesh. Questo comportamento è noto come occlusione.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step5im.PNG)

>Nota: anche se non è visibile, la mesh di mapping spaziale è comunque presente ed è possibile interagire con essa. Gli ologrammi dietro la mesh di mapping spaziale, ad esempio un ologramma nascosto dietro la parete visibile, non saranno visibili a causa dell'impostazione di occlusione.

A questo punto, hai appreso come modificare un'impostazione nel profilo di MRTK. Come puoi notare, per modificare le impostazioni di MRTK devi creare copie dei profili predefiniti in modo da poterle modificare. I profili predefiniti (non modificabili) rimarranno comunque sempre disponibili se vuoi creare un profilo con nuove impostazioni o fare riferimento a tali profili. Esistono numerose impostazioni che puoi modificare. Per informazioni di riferimento complete per le impostazioni dei profili di MRTK, consulta la documentazione di MRTK a questo indirizzo: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html

### <a name="hand-tracking-gestures-and-interactable-buttons"></a>Movimenti di tracciamento delle mani e pulsanti con supporto per interazioni
In questa sezione apprenderai come usare il tracciamento delle mani per premere un pulsante con supporto per interazioni.

1. Seleziona "Assets" dalla cartella del progetto.

2. Digita "pressablebutton" nella barra di ricerca.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step1im.PNG)

3. Trascina il prefab (rappresentato da una casella blu) denominato "PressableButton" nella tua gerarchia. 

   > Nota: se viene visualizzato un messaggio sull'importazione di TMP Essentials, esegui l'importazione in questo momento. Se TMP Essentials non è già parte del progetto, può essere necessario ripetere questo passaggio dopo l'importazione, altrimenti è possibile che il testo del pulsante non venga visualizzato.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step3im.PNG)

4. Fai doppio clic sull'oggetto gioco "PressableButton" (che dovrebbe essere ora nella gerarchia BaseScene) per visualizzarlo nella scena, come illustrato nell'immagine seguente. La grafica del pulsante può apparire diversa rispetto a quella riportata di seguito. 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step4im.PNG)

5. Nel pannello di controllo fai clic su "Add Event" (Aggiungi evento) per assegnare al pulsante un evento a cui rispondere quando viene premuto. Nell'opzione visualizzata seleziona il menu a discesa. Seleziona "InteractableOnPressReceiver". In questo modo il pulsante risponde a un evento di pressione quando una mano tracciata preme il pulsante.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step5im.PNG)

6. Aggiungi un cubo alla scena. Fai clic con il pulsante destro del mouse sull'area della gerarchia, seleziona 3D Object (Oggetto 3D) e quindi fai clic su "Cube". A questo punto, sullo schermo dovrebbe essere visualizzato un cubo. Poiché il cubo è molto grande, modifica le coordinate (mentre "Cube" è ancora selezionato nell'area della gerarchia) per ridurne le dimensioni. Imposta i valori di ridimensionamento su x = 0.1, y = 0.1 e z = 0.1. Assicurati di posizionare il cubo nella scena, accanto al pulsante a pressione, ma senza sovrapposizioni con il pulsante. Nell'immagine seguente la posizione del cubo è x = 0, y = 0.2 e z = 1. 

   > Nota: in generale, 1 unità in Unity equivale quasi a 1 metro nel mondo fisico. Vi sono tuttavia eccezioni, ad esempio quando gli oggetti sono figli di oggetti ridimensionati.
   
   ![MR213_BuildSettings](images/mrlearning-base-ch2-1step6ima.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-2step6imb.PNG)

7. In questo passaggio configurerai il cubo in modo da cambiare colore quando viene premuto il pulsante. Seleziona PressableButton nel menu "BaseScene". Nel pannello di controllo, nella casella "Select Event Type" (Seleziona tipo di evento), fai clic sul pulsante "+". Trascina l'oggetto "Cube" dal menu "BaseScene" nella casella "Runtime Only" (Solo runtime), come illustrato nell'immagine seguente

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7ima.PNG)

Fai clic sull'elenco a discesa denominato "No Function" (Nessuna funzione). Seleziona "MeshRenderer" e quindi "Material material" (Materiale fisico). In questo modo potrai cambiare il materiale quando viene premuto il pulsante. 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imb.PNG)

Passa al pannello del progetto e cerca il materiale che vuoi cambiare sul cubo. Per questo esempio userai il materiale "MRTK_Standard_Cyan", che puoi trovare digitando "cyan" nella barra di ricerca della scheda del progetto. In MRTK sono disponibili per la selezione numerosi materiali e colori. Trascina il materiale nella casella sotto "MeshRenderer.material". I materiali di MRTK si trovano in Assets>MixedRealityToolkit.SDK>StandardAssets>Materials.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imbb.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step7imc.PNG)

L'evento è ora impostato in modo che, quando il pulsante viene premuto, il cubo cambi colore in base al materiale specificato. In questo esempio il cubo assumerà il colore ciano.

8. A questo punto, configurerai l'azione di rilascio in modo che, al momento del rilascio, venga ripristinato il colore predefinito del pulsante. Ripeti il passaggio 7 (il passaggio precedente), ma questa volta con l'evento "OnRelease" invece dell'evento "OnPress", come illustrato nell'immagine seguente.

9.  Nel pannello del progetto cerca un materiale da assegnare al cubo per impostazione predefinita al momento del rilascio del pulsante. In questo caso è stato scelto MRTK_Standard_LightGray. Trascina il materiale nella casella sotto il campo "MeshRenderer.material".

![MR213_BuildSettings](images/mrlearning-base-ch2-2step8im.PNG)

A questo punto, quando il pulsante verrà premuto, dovrebbe assumere un nuovo colore (ad esempio, il ciano) e, quando verrà rilasciato, dovrebbe risultare nuovamente del colore predefinito specificato (ad esempio, il grigio chiaro). Fai clic sul pulsante per la riproduzione nella parte superiore della schermata per provare il pulsante nell'editor oppure distribuisci il tuo HoloLens 2 per il test. Per altre informazioni sulla simulazione all'interno dell'editor, inclusa la simulazione delle mani, leggi la [pagina della documentazione di MRTK sulla simulazione](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html>). 

### <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>Creazione di un pannello di pulsanti con la raccolta di oggetti griglia di MRTK

In questa sezione apprenderai come allineare automaticamente più pulsanti in un'interfaccia utente pulita usando lo strumento GridObjectCollection di MRTK.

1. Duplica il pulsante dalla sezione precedente finché non sono presenti cinque pulsanti. Questa operazione può essere eseguita in diversi modi:
- Fai clic con il pulsante destro del mouse e scegli "Copy" (Copia), quindi sposta il puntatore verso il basso, al di sotto del pulsante, e fai nuovamente clic con il pulsante destro del mouse e scegli "Paste" (Incolla). 
- Fai clic con il pulsante destro del mouse sul pulsante e scegli "Duplicate" (Duplica). 
- Fai clic sul cubo e premi CTRL+D sulla tastiera.

Ripeti questa procedura finché non sono presenti tutti e cinque i pulsanti. Vedi le cinque frecce rosse nell'immagine seguente.

![Modulo di apprendimento di base sulla realtà mista Capitolo 2 Passaggio 3 Immagine 1](images/mrlearning-base-ch2-3step1im.PNG)

2. Raggruppa i pulsanti in un oggetto gioco padre vuoto. Per includere i pulsanti nella raccolta griglia, devi raggrupparli in un oggetto padre comune. Fai clic con il pulsante destro del mouse nella gerarchia e scegli "Create Empty" (Crea vuoto). In questo modo viene creato un nuovo oggetto gioco vuoto in cui includere tutti i pulsanti. Verrà visualizzato come "gameObject". Fai clic con il pulsante destro del mouse e rinominalo in "ButtonCollection".

![Modulo di apprendimento di base sulla realtà mista Capitolo 2 Passaggio 3 Immagine 2](images/mrlearning-base-ch2-3step2im.PNG)

3. Sposta tutti i pulsanti nella nuova raccolta. Per eseguire questa operazione, seleziona tutti e cinque gli oggetti pulsante nella gerarchia e trascinali tutti sotto l'oggetto gioco "ButtonCollection", come illustrato nell'immagine seguente. Suggerimento: per selezionare più elementi, tieni premuto CTRL mentre esegui la selezione.

![Modulo di apprendimento di base sulla realtà mista Capitolo 2 Passaggio 3 Immagine 3](images/mrlearning-base-ch2-3step3imb.PNG)

4. Aggiungi il componente "Grid Object Collection" (Raccolta oggetti griglia) di MRTK alla raccolta di pulsanti.  Per eseguire questa operazione, seleziona l'oggetto padre "ButtonCollection" e nel pannello di controllo fai clic sul pulsante "Add Component" (Aggiungi componente). Cerca quindi "Grid Object Collection" nella barra di ricerca e seleziona la voce corrispondente quando viene visualizzata nell'elenco.

![Modulo di apprendimento di base sulla realtà mista Capitolo 2 Passaggio 3 Immagine 4](images/mrlearning-base-ch2-3step4im.PNG)

Il componente "Grid Object Collection" (Raccolta oggetti griglia) consente di organizzare i pulsanti o qualsiasi set di oggetti in una riga, colonna o griglia vuota. Questo è uno dei blocchi predefiniti di MRTK, che offre un modo semplice e rapido per creare interfacce utente accattivanti.

5. Configura la raccolta di oggetti griglia. Per assicurarti che tutti i pulsanti siano rivolti verso l'utente, seleziona "Orient Type" (Tipo di orientamento) e quindi "Face Parent Forward" (Orientamento padre in avanti), come illustrato nell'immagine. Modifica quindi le dimensioni della cella per impostare lo spazio tra i pulsanti. Iniziare con 0.12 unità per la larghezza della cella e 0.12 unità per l'altezza, come illustrato nell'immagine seguente. Potrebbe essere necessario modificare questi valori, a seconda degli asset oggetto/pulsante selezionati. Assicurati che "Rows" (Righe) sia impostato su 1. Fai quindi clic su "Update Collection" (Aggiorna raccolta). La scena dovrebbe essere simile all'immagine seguente. 


![Modulo di apprendimento di base sulla realtà mista Capitolo 2 Passaggio 3 Immagine 5](images/mrlearning-base-ch2-3step5im.PNG)

>Nota: a seconda dell'orientamento degli oggetti figlio o dell'oggetto padre, sarà probabilmente necessario modificare l'impostazione dell'orientamento in modo diverso nei progetti futuri. È probabile che sia necessario definire in modo diverso anche i valori dei campi Cell Width (Larghezza cella) e Cell Height (Altezza cella), a seconda delle dimensioni degli oggetti nella raccolta.

### <a name="adding-text-into-your-scene"></a>Aggiunta di testo nella scena

In questa sezione apprenderai come aggiungere e modificare il testo nelle esperienze di realtà mista. Se non lo hai già fatto, assicurati che TextMeshPro sia abilitato in Unity seguendo le istruzioni riportate [qui](https://docs.unity3d.com/Packages/com.unity.textmeshpro@2.0/manual/index.html#installation).

1. Seleziona l'oggetto padre "ButtonCollection" e fai clic con il pulsante destro del mouse sulla raccolta. Espandi "3D Object" (Oggetto 3D) nel menu a discesa e quindi seleziona "TextMeshPro - Text". Sotto la raccolta di pulsanti verrà visualizzato un oggetto TextMeshPro, come illustrato nell'immagine seguente.

![Lezione 2 capitolo 4 passaggio 1a](images/Lesson2_Chapter4_Step1a.JPG)
![Lezione 2 capitolo 4 passaggio 1b](images/Lesson2_Chapter4_Step1b.JPG)

2. Nel campo Text (Testo) del componente TextMeshPro (all'interno del pannello di controllo, come illustrato di seguito), digita "Button Collection Text". Il testo verrà visualizzato nella scena, ma sarà nascosto dietro i pulsanti e/o le dimensioni non saranno corrette.

![Lezione 2 capitolo 4 passaggio 2](images/Lesson2_Chapter4_Step2.JPG)

3. Per correggere le dimensioni e la posizione del testo per una migliore leggibilità, imposta un altro valore nel campo "Font Size" (Dimensioni carattere) del componente TextMeshPro per cambiare le dimensioni del tipo di carattere. Dovrai anche modificare la posizione definita in "Rect Transform" (Trasformazione rettangolo) e il fattore di scala, come illustrato nell'immagine seguente. Nelle immagini seguenti verifica i valori definiti per la configurazione del testo, che puoi usare come punto di partenza per migliorare ulteriormente le dimensioni e la posizione del tuo campo di testo.

![Lezione 2 Capitolo 4 Passaggio 3](images/Lesson2_Chapter4_Step3.JPG)
![Lezione 2 Capitolo 4 Passaggio 4](images/Lesson2_Chapter4_Step4.JPG)

5. Per modificare i valori di testo negli oggetti pulsante, fai clic sulla freccia accanto a un pulsante per espanderlo, seleziona l'oggetto "SeeItSayItLabel" e quindi passa a "TextMeshPro", in cui puoi modificare il testo dei pulsanti, come descritto nei passaggi precedenti.

![Lezione 2 capitolo 4 passaggio 5](images/Lesson2_Chapter4_Step5.JPG)

### <a name="congratulations"></a>Lezione completata
In questa lezione hai appreso come copiare, personalizzare e configurare un'impostazione del profilo di MRTK, ad esempio la visibilità della mesh di consapevolezza spaziale. Hai inoltre appreso come interagire con un pulsante per attivare gli eventi usando le mani tracciate sul dispositivo HoloLens 2 e, infine, come creare una semplice interfaccia utente tramite TextMeshPro di Unity e la raccolta di oggetti griglia di MRTK.

[Lezione successiva: Posizionamento dinamico del contenuto e risolutori](mrlearning-base-ch3.md)


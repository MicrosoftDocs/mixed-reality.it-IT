---
title: Modulo MR Learning ASA-Azure Spatial Anchor su HoloLens 2
description: Completa questo corso per informazioni su come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 690ece3a02aeefd598db18baa66de3ddabfa43eb
ms.sourcegitcommit: 611af6ff7a2412abad80c0c7d4decfc0c3a0e8c8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2019
ms.locfileid: "68293812"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a>1. Introduzione agli ancoraggi spaziali di Azure

Benvenuti nel secondo modulo delle esercitazioni di HoloLens 2. Prima di iniziare, assicurarsi che tutti i [prerequisiti](https://docs.microsoft.com/en-us/azure/spatial-anchors/quickstarts/get-started-unity-hololens) siano stati completati. Se non è stato ancora completato il primo [modulo di base](mrlearning-base.md) , è consigliabile completare prima il modulo. Se si inizia da un nuovo progetto Unity, seguire la procedura di creazione del nuovo progetto nel [modulo di base](mrlearning-base.md). 

## <a name="objectives"></a>Obiettivi

* Scopri le nozioni di base sullo sviluppo con i Anchor spaziali di Azure con HoloLens 2

* Creare, caricare e scaricare ancoraggi spaziali

## <a name="instructions"></a>Istruzioni

### <a name="downloading-and-importing-assets"></a>Download e importazione di asset
Prima di iniziare, scaricare e importare gli asset seguenti:

[Ancoraggi nello spazio di Azure](https://github.com/azure/azure-spatial-anchors-samples/releases)

[Asset Pack del modulo di base di MR](https://github.com/microsoft/MixedRealityLearning/releases/tag/1.2)

[Asset Pack del modulo ASA](https://github.com/microsoft/MixedRealityLearning/releases/tag/ASA_1.1)

[Toolkit per realtà mista](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/)

> Nota: Per istruzioni specifiche su come importare gli ancoraggi spaziali di Azure, vedere il passaggio 6 per istruzioni specifiche sull'asset Pack del modulo di base di MR e i passaggi da 3 a 4 per istruzioni specifiche sul Toolkit di realtà mista (MRKT).

1. Creare una nuova scena nel progetto. Fare clic con il pulsante destro del mouse sulla cartella della scena, scegliere Crea, quindi scena. Assegnare alla nuova scena il nome ASALearningmodule.

![module2chapter1step1im](images/module2chapter1step1im.PNG)

2. Fare doppio clic su ASALearningmodule per vedere che vengono visualizzati alcuni elementi predefiniti insieme alla nuova scena. 
3. Configurare la scena per lo sviluppo di realtà mista. 

![module2chapter1step3im](images/module2chapter1step3im.PNG)

> Nota: Viene visualizzato un messaggio popup che indica che è necessario scegliere un file per il Toolkit di realtà mista. Se si fa clic su OK, sarà possibile passare al passaggio 4.

4. Quando si sceglie un file per MRTK, selezionare DefaultMixedRealityToolkitConfigurationProfile.

> Nota: Se è disponibile un profilo di configurazione personalizzato, è possibile utilizzarlo.

![module2chapter1step4im](images/module2chapter1step4im.PNG)

La scena è ora configurata per la realtà mista. Assicurarsi di salvare la scena (eseguire questa operazione con il controllo/comando + S oppure fare clic su file, quindi fare clic su Salva). 

5. Importare gli [ancoraggi spaziali di Azure](https://github.com/azure/azure-spatial-anchors-samples/releases). Per usare gli ancoraggi spaziali, è necessario importare questo asset. Fare clic sul collegamento sopra e fare clic con il pulsante destro del mouse su AzureSpatialAnchors. file unitypackage Tools. Fare clic su Salva destinazione con nome e salvarlo nel computer. 

![module2chapter1step5aim](images/module2chapter1step5aim.PNG)

Dopo il salvataggio, tornare a Unity, fare clic su assets, quindi su Import Package. Quindi fare clic su pacchetto personalizzato... I file del computer si apriranno. Quando si esegue questa operazione, trovare la posizione in cui è stato salvato il pacchetto di ancoraggi spaziali di Azure e selezionarlo. Quindi fare clic su Apri.

![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

Viene visualizzata una finestra popup, providingg un elenco di strumenti e impostazioni, che richiede l'importazione. Selezionare ***tutte*** le opzioni disponibili, quindi fare clic su Importa.

![module2chapter1step5cim](images/module2chapter1step5cim.PNG)

> Nota: L'importazione potrebbe richiedere alcuni minuti. 

6. Importazione [Mr base Module asset Pack]https://github.com/microsoft/MixedRealityLearning/releases/tag/1.2) avanti. Analogamente al passaggio 5, fare clic sul collegamento precedente. Fare quindi clic con il pulsante destro del mouse su BasemoduleAssetsV1 1. unitypackag, quindi scegliere Salva destinazione con nome e salvarlo nel computer.

![module2chapter1step6aim](images/module2chapter1step6aim.PNG)

> Suggerimento: Salvare tutti gli asset nella stessa cartella in modo che risultino più facili da trovare e a cui è possibile accedere. Che consente di mantenere tutti gli elementi interessanti e organizzati.

Analogamente al passaggio 5, tornare a Unity, fare clic su asset e passare il puntatore del mouse su Importa pacchetto. Fare clic su pacchetto personalizzato... I file del computer verranno visualizzati di nuovo. Passare alla posizione in cui è stato archiviato il modulo di base asset Pack. e selezionarlo. Fare clic su Apri.

![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

> Nota: Potrebbero essere presenti più asset necessari più avanti in questo modulo. Seguire questa procedura per importare le risorse indicate da questo punto in poi. 

7. Importare il [pacchetto del modulo ASA](https://github.com/microsoft/MixedRealityLearning/releases/tag/ASA_1.1) usando lo stesso approccio dell'importazione dei pacchetti precedenti.

### <a name="configuring-your-scene"></a>Configurazione della scena

In questa sezione vengono aggiunti i prefabbricati e gli script nella scena per creare una serie di pulsanti che dimostrano le nozioni di base del comportamento di entrambi gli ancoraggi locali e degli ancoraggi spaziali di Azure in un'applicazione.

8. Nella scheda progetto, sotto la cartella assets, fare clic su ASAmoduleAssets. Una volta selezionate, vengono visualizzati due prefabbricati: ButtonParent e ParentAnchor.

![module2chapter1step7im](images/module2chapter1step7im.PNG)

9. Trascinare entrambi i prefabbricati nella scena. 

![module2chapter1step8im](images/module2chapter1step8im.PNG)

10. Fare doppio clic sull'ancoraggio padre per selezionarlo. Potrebbe essere necessario modificare la visualizzazione per visualizzare l'intera scena. Modificare la scena in base alle esigenze.

Acquisire familiarità con la prefabbricata ParentAnchor. Attualmente, l'oggetto gioco denominato, ParentAnchor, è un cubo colorato a scopo dimostrativo. Infine, si nasconde il cubo e si inserisce il contenuto come elemento figlio di ParentAnchor. Questa prefabbricata include lo script AzureSpatialAnchorsDemoWrapper.cs (incluso con l'SDK ASA) e lo script ASAmoduleScript.cs, incluso come parte di questo modulo nell'oggetto ParentAnchor. 

11. Configurare i pulsanti. Sotto la prefabbricata ButtonParent si notino diversi pulsanti con etichetta. Questi pulsanti vengono creati dai prefabbricati PressableButton di MRTK. Altre informazioni su come creare pulsanti stampabili dal modulo di [base](mrlearning-base-ch2.md). Per ogni pulsante, aggiungere un evento che verrà attivato quando l'utente preme o seleziona il pulsante in base all'elenco riportato di seguito. 

- Per il pulsante denominato StartAzureSession, creare un nuovo evento sotto il trigger di evento premuto pulsante, nonché il trigger di evento clic su. Trascinare l'oggetto ParentAnchor nel campo vuoto e assegnare il metodo StartAzureSession () dal componente ASAmoduleScript dell'oggetto ParentAnchor.

![module2chapter1step10aim](images/module2chapter1step10aim.PNG)

![module2chapter1step10bim](images/module2chapter1step10bim.PNG)

![module2chapter1step10cim](images/module2chapter1step10fim.PNG)

- Per il nome del pulsante, StopAzureSession, creare un nuovo evento sotto il trigger evento premuto pulsante, nonché il trigger di evento clic su. Trascinare l'oggetto ParentAnchor nel campo vuoto e assegnare il metodo StopAzureSession () dal componente ASAmoduleScript dell'oggetto ParentAnchor.

- Per il pulsante denominato CreateAnchor, creare un nuovo evento sotto il trigger di evento premuto pulsante, nonché il trigger di evento clic su. Trascinare l'oggetto ParentAnchor nel campo vuoto e assegnare il metodo CreateAzureAnchor () dal componente ASAmoduleScript dell'oggetto ParentAnchor.

- Per il pulsante denominato, avviare la ricerca dell'ancoraggio, creare un nuovo evento sotto il trigger di evento presse Button e il trigger di evento click on. Trascinare l'oggetto ParentAnchor nel campo vuoto e assegnare il metodo FindAzureAnchor () dal componente ASAmoduleScript dell'oggetto ParentAnchor.

- Per il pulsante denominato DeleteAzureAnchor, creare un nuovo evento sotto il trigger di evento premuto pulsante, nonché il trigger di evento clic su. Trascinare l'oggetto ParentAnchor nel campo vuoto e assegnare il metodo DeleteAzureAnchor () dal componente ASAmoduleScript dell'oggetto ParentAnchor.

- Per il pulsante denominato eliminare l'ancoraggio locale, creare un nuovo evento sotto il trigger di evento premuto sul pulsante, nonché il trigger di evento clic su. Trascinare l'oggetto ParentAnchor nel campo vuoto e assegnare il metodo RemoveLocalAnchor () dal componente ASAmoduleScript dell'oggetto ParentAnchor.

### <a name="build-and-demonstrate-base-application"></a>Compilare e dimostrare l'applicazione di base

Ora che la scena è configurata in modo da illustrare gli elementi di base degli ancoraggi spaziali di Azure, verrà creato e illustrato il comportamento di base degli ancoraggi spaziali di Azure. 

1. Se nelle sezioni precedenti hai chiuso la finestra Build Settings (Impostazioni di compilazione), aprila nuovamente passando a File>Build Settings (File>Impostazioni di compilazione).
![Lesson1Chapter5Step1](images/Lesson1Chapter5Step1.JPG)

2. Assicurarsi che la scena che si vuole provare si trovi nell'elenco scene in Build facendo clic sul pulsante Aggiungi scene aperte.

3. Scegli il pulsante Build (Compila) per avviare il processo di compilazione.
![Lesson1Chapter5Step3](images/Lesson1Chapter5Step3.JPG)

4. Crea una nuova cartella per l'applicazione e assegna un nome alla cartella creata. Nell'immagine seguente è stata creata una cartella con l'app nome per contenere l'applicazione. Fare clic su Seleziona cartella per iniziare a compilare la cartella appena creata. Al termine della compilazione, è possibile chiudere l'impostazione di compilazione "finestra in Unity. 
![Lesson1Chapter5Step4](images/Lesson1Chapter5Step4.JPG)

  > NOTA: se la compilazione ha esito negativo, prova a ripeterla o a riavviare Unity e a ripetere la compilazione. Se visualizzi un errore simile al seguente: CS0246 = Impossibile trovare il nome di tipo o spazio dei nomi "XX". manca una direttiva using o un riferimento a un assembly. Potrebbe essere necessario installare [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>) 
  >

5. Al termine della compilazione, apri la nuova cartella creata che contiene i file dell'applicazione appena compilata. Fare doppio clic sulla soluzione "MixedRealityBase. sln" o sul nome corrispondente. Se è stato usato un nome alternativo per il progetto per aprire il file della soluzione in Visual Studio.

  > Nota: Assicurarsi di aprire la cartella appena creata (ad esempio, la cartella dell'app, se si seguono le convenzioni di denominazione dei passaggi precedenti perché è presente un file con estensione sln simile al di fuori della cartella che non deve essere confuso con il file con estensione sln all'interno della cartella di compilazione. 

![Lesson1Chapter5Step5](images/Lesson1Chapter5Step5.JPG)

> Nota: Se Visual Studio richiede di installare nuovi componenti, verificare che tutti i componenti dei prerequisiti siano installati come specifici nella [pagina "installazione degli strumenti"](install-the-tools.md) . 

6. Collega HoloLens 2 al PC con il cavo USB. Sebbene queste istruzioni della lezione presuppongano che si stia distribuendo un test con un dispositivo HoloLens 2, è anche possibile scegliere di eseguire la distribuzione nell' [emulatore HoloLens 2](using-the-hololens-emulator.md) o scegliere di creare un [pacchetto dell'app per sideload](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)

7. Prima della compilazione, assicurati che il dispositivo sia in modalità sviluppatore. Se questa è la prima volta che esegui la distribuzione nel dispositivo HoloLens 2, Visual Studio può richiedere di associare HoloLens 2 a un PIN. Seguire [queste istruzioni](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio) se è necessario abilitare la modalità sviluppatore o la coppia con Visual Studio.

8. Configurare Visual Studio per la compilazione in HoloLens 2 selezionando la configurazione per la versione e l'architettura RM.
![Lesson1Chapter5Step8](images/Lesson1Chapter5Step8.JPG)
   
9. Il passaggio finale consiste nel compilare nel dispositivo selezionando Debug > Avvia senza eseguire debug. Se si seleziona Avvia senza eseguire debug, l'applicazione viene avviata immediatamente sul dispositivo in seguito a una compilazione corretta enza le informazioni di debug visualizzate in Visual Studio. Questo significa anche che, mentre l'applicazione è in esecuzione sul dispositivo HoloLens 2, puoi disconnettere il cavo USB senza arrestare l'applicazione. È anche possibile selezionare Compila > Distribuisci soluzione per eseguire la distribuzione nel dispositivo senza che l'applicazione venga avviata automaticamente.
![Lesson1Chapter5Step9](images/Lesson1Chapter5Step9.JPG)
   
10. Segui le istruzioni visualizzate. Quando l'applicazione è in esecuzione nel dispositivo, seguire le istruzioni visualizzate. Premere i pulsanti della scena corrispondenti ai passaggi seguenti.

![module2chapter1step10eim](images/module2chapter1step10eim.PNG)
    
    1. Avviare la sessione di ancoraggi spaziali.
    
    2. Spostare il cubo in un percorso diverso.
    
    3. Salvare gli ancoraggi spaziali di Azure nella posizione del cubo.
    
    4. Arrestare la sessione di ancoraggi spaziali di Azure.
    
    5. Rimuovere l'ancoraggio locale nel cubo per consentire all'utente di spostare il cubo.
    
    6. Spostare il cubo altrove.
    
    7. Avviare la sessione di ancoraggi spaziali di Azure.
    
    8. Trovare ancoraggi spaziali di Azure. 
    È necessario tornare alla posizione originale in cui è stato inserito quando è stato creato l'ancoraggio.
    
    9. Eliminare l'ancoraggio spaziale di Azure.
    
    10. Arrestare la sessione di Azure.

### <a name="anchoring-an-experience"></a>Ancoraggio di un'esperienza

Nelle sezioni precedenti sono state apprese le nozioni di base degli ancoraggi spaziali di Azure. È stato usato un cubo per rappresentare e visualizzare l'oggetto del gioco padre con l'ancoraggio collegato. In questa sezione viene illustrato come ancorare un'intera esperienza inserendola come elemento figlio dell'oggetto ParentAnchor. Per questo esempio viene usata l'applicazione dimostrativa dell'assembly del modulo Lunar creata durante la [lezione 6 del modulo di base](mrlearning-base-ch6.md).

1. Cercare l'assembly del modulo Lunar completare la prefabbricazione e trascinarlo nella gerarchia come elemento figlio di AnchorParent GameObject, come illustrato nell'immagine seguente.

![module2chapter1step11](images/module2chapter1step11im.PNG)

2. Posizionare l'esperienza di assembly del modulo in modo che il cubo venga ancora esposto come illustrato nell'immagine seguente. Nell'applicazione, gli utenti possono riposizionare l'intera esperienza spostando il cubo. 

![module2chapter1step12im](images/module2chapter1step12im.PNG)

> Nota: Esistono diversi flussi di esperienza utente per il riposizionamento delle esperienze, incluso l'uso di un pulsante per alternare un rettangolo di selezione che racchiude l'esperienza, l'uso di un oggetto di riposizionamento (ad esempio il cubo usato in questo passaggio), l'uso di gizmo di posizione e di rotazione e altro ancora.

## <a name="congratulations"></a>Lezione completata
In questa esercitazione sono state apprese le nozioni di base degli ancoraggi spaziali di Azure. Questo it ha fornito diversi pulsanti che consentono di esaminare i diversi passaggi necessari per avviare e arrestare una sessione di Azure e creare, caricare e scaricare gli ancoraggi di Azure in un singolo dispositivo. Nella lezione successiva verrà illustrato come salvare gli ID di ancoraggio di Azure in HoloLens 2 per il recupero, anche dopo il riavvio dell'applicazione. Durante la serie, si apprenderà anche come trasferire gli ID di ancoraggio tra più dispositivi per ottenere l'allineamento spaziale e acquisire informazioni sulle sessioni condivise multiutente, come parte dell'esercitazione relativa alla condivisione.

[Lezione successiva: Lezione 2 di ASA](mrlearning-asa-ch2.md)


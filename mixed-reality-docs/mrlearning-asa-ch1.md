---
title: Modulo ASA Learning MR Azure spaziali ancoraggio su HoloLens 2
description: Completa questo corso per informazioni su come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: c120d22f955d366042bbcb9ac73eaa4f13dc20e9
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415274"
---
# <a name="getting-started-with-azure-spatial-anchors-on-hololens-2"></a>Introduzione a Azure spaziali ancoraggi su HoloLens 2

Benvenuti al secondo modulo dell'esercitazione 2 HoloLens. Prima di iniziare, assicurarsi che tutti del [prerequisiti](https://docs.microsoft.com/en-us/azure/spatial-anchors/quickstarts/get-started-unity-hololens) vengono completate. Se non è stata completata, il primo [modulo di Base](mrlearning-base.md) ancora, è consigliabile completare prima di tutto tale modulo. Se sta iniziando da un nuovo progetto Unity, seguire la procedura di creazione nuovo progetto nel [modulo di Base](mrlearning-base.md). 

## <a name="objectives"></a>Obiettivi

* Scopri i concetti fondamentali dello sviluppo con Azure Anchor spaziali con 2 HoloLens

* Creare, caricare e scaricare gli ancoraggi spaziali

  

## <a name="instructions"></a>Istruzioni

### <a name="downloading-and-importing-assets"></a>Download e importazione delle risorse
Prima di iniziare, scaricare e importare le risorse seguenti:

[Ancoraggi nello spazio di Azure](https://github.com/azure/azure-spatial-anchors-samples/releases)

[Modulo di Base di MR pacchetto di Asset](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1)

[Modulo ASA pacchetto di Asset](https://github.com/microsoft/MixedRealityLearning/releases/tag/ASA_B2)

[Toolkit per realtà mista](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)

> Nota: Per istruzioni specifiche su come importare gli ancoraggi spaziale di Azure, passaggio 6 per istruzioni specifiche per il modulo di Base di MR pacchetto di Asset e i passaggi 3 e 4 per istruzioni specifiche sul Toolkit di realtà mista (MRKT), vedere il passaggio 5.

1. creare una nuova scena nel progetto. Pulsante destro del mouse fare clic sulla cartella scena, fare clic su "Crea", quindi scena. Nome della nuova scena ASALearningmodule.

![module2chapter1step1im](images/module2chapter1step1im.PNG)

2. Fare doppio clic per visualizzare alcuni elementi predefiniti vengono visualizzate insieme a nuova scena ASALearningmodule. 
3. Configurare la scena per lo sviluppo della realtà mista. 

![module2chapter1step3im](images/module2chapter1step3im.PNG)

> Nota: Verrà visualizzato un messaggio popup che afferma, "È necessario scegliere un file per il Toolkit di realtà mista". Fare clic su Ok, si offre al passaggio 4.

4. Quando si sceglie un file per il MRTK, select, DefaultMixedRealityToolkitConfigurationProfile.

   > Nota: Se si dispone del proprio profilo di configurazione, è possibile utilizzare tale applicazione.

![module2chapter1step4im](images/module2chapter1step4im.PNG)

Ora la scena è configurata per realtà mista. Assicurarsi di salvare la scena (eseguire questa operazione con uno dei due controlli / comando + S o fare clic sul file, quindi fare clic su salvataggio). 

5. Importa i [Anchor spaziali Azure](https://github.com/azure/azure-spatial-anchors-samples/releases). Per usare gli ancoraggi spaziali, è necessario importare questo asset. Fare clic sul collegamento riportato sopra e fare clic con il pulsante destro su AzureSpatialAnchors.unitypackage. Fare clic su Salva oggetto con nome e salvarlo nel computer. 

   ![module2chapter1step5aim](images/module2chapter1step5aim.PNG)

   Dopo il salvataggio, è possibile tornare in Unity, fare clic su risorse, andare alla Importa pacchetto. Fare clic su pacchetto personalizzato... Verranno aperto i file del computer. Quando si eseguire, trovare in cui è stato salvato il pacchetto Azure spaziali ancoraggi e selezionarlo. Quindi fare clic su Apri.

   ![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

   Viene visualizzato un popup, providingg un elenco di strumenti e le impostazioni e che richiede gli elementi da importare. Selezionare ***tutti*** delle opzioni disponibili, quindi fare clic su Importa.

   ![module2chapter1step5cim](images/module2chapter1step5cim.PNG)

   > Nota: È necessario attendere, richiederà alcuni minuti per l'importazione. 

   6. Importazione [modulo di Base di MR Asset Pack](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1) successivo. Molto, come passaggio 5, fare clic sul collegamento precedente. Quindi fare clic con il pulsante destro 1.unitypackag BasemoduleAssetsV1 e fare clic su Salva oggetto con nome e salvarlo nel computer.

   ![module2chapter1step6aim](images/module2chapter1step6aim.PNG)

   > Suggerimento: Salvare tutte queste risorse nella stessa cartella in modo che siano più semplici da individuare e avere accesso a. Conserva tutti gli elementi interessanti e organizzate.

   Come passaggio 5, tornare a Unity, fare clic su asset e passare il mouse sul pacchetto di importazione. Fare clic sul pacchetto personalizzato... I file del computer verranno visualizzata nuovamente. Passare a dove è archiviato il pacchetto di Asset del modulo di Base. e selezionarla. Fare clic su Apri.

   ![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

   > Nota: Potrebbero esserci altre gli asset necessari più avanti in questo modulo. Seguire questi passaggi per importare tutte le risorse indicate da questo momento. 
                                                                                                                                                                                                                    
7. Importare l'ack di modulo ASA usando lo stesso approccio valido per l'importazione dei pacchetti precedenti.

### <a name="configuring-your-scene"></a>Configurazione della scena

In questa sezione si aggiungerà prefabs e gli script nella scena per creare una serie di pulsanti che illustrano le nozioni di base del comportamento sia gli ancoraggi locali e Azure spaziali ancoraggi in un'applicazione.

7. Nella scheda progetti, sotto la cartella Assets, fare clic su ASAmoduleAssets. Una volta selezionata, verrà visualizzato due prefabs: ButtonParent e ParentAnchor.

![module2chapter1step7im](images/module2chapter1step7im.PNG)

8. Trascinare entrambi prefabs nella scena. 

![module2chapter1step8im](images/module2chapter1step8im.PNG)

9. Fare doppio clic su ancoraggio padre per selezionarlo. Si potrebbe essere necessario regolare la vista per visualizzare l'intera scena. Regolare la scena in base alle esigenze.

    Acquisire familiarità con il prefab ParentAnchor. Attualmente, l'oggetto gioco denominato, ParentAnchor, è un cubo colorato per scopi dimostrativi. Infine, abbiamo ', ll nascondere il cubo e inserire il contenuto come figlio di ParentAnchor. Il prefab include lo script AzureSpatialAnchorsDemoWrapper.cs (incluso con il SDK ASA) e lo script ASAmoduleScript.cs, incluso come parte di questo modulo per l'oggetto ParentAnchor. 

10. Pulsanti di configurazione. Sotto il prefab ParentAnchor, si noti che alcuni pulsanti con etichettati. Questi pulsanti vengono creati da prefab PressableButton del MRTK. Altre informazioni su come creare pulsanti Pressable dal [modulo di Base](mrlearning-base-ch2.md). Per ogni pulsante, aggiungere un evento che viene attivato quando l'utente preme o si seleziona il pulsante in base all'elenco seguente. 

- Per il pulsante denominato, StartAzureSession, creare un nuovo evento sotto il trigger di evento fatto clic sul pulsante, nonché il trigger di evento nel fare clic su. Trascinare l'oggetto ParentAnchor nel campo vuoto e assegnare il metodo StartAzureSession() dal componente ASAmoduleScript ParentAnchor dell'oggetto.

  ![module2chapter1step10aim](images/module2chapter1step10aim.PNG)

  ![module2chapter1step10bim](images/module2chapter1step10bim.PNG)

  ![module2chapter1step10cim](images/module2chapter1step10fim.PNG)

- Per il nome del pulsante StopAzureSession, creare un nuovo evento sotto il trigger di evento fatto clic sul pulsante, nonché il trigger di evento nel fare clic su. Trascinare l'oggetto ParentAnchor nel campo vuoto e assegnare il metodo StopAzureSession() dal componente ASAmoduleScript ParentAnchor dell'oggetto.

- Per il pulsante denominato, CreateAnchor, creare un nuovo evento sotto il trigger di evento fatto clic sul pulsante, nonché il trigger di evento nel fare clic su. Trascinare l'oggetto ParentAnchor nel campo vuoto e assegnare il metodo CreateAzureAnchor() dal componente ASAmoduleScript ParentAnchor dell'oggetto.

- Trigger di evento per il pulsante di ancoraggio con nome, avviare la ricerca per, creare un nuovo evento sotto premuto il pulsante"così come il trigger di evento nel fare clic su. Trascinare l'oggetto ParentAnchor nel campo vuoto e assegnare il metodo FindAzureAnchor() dal componente ASAmoduleScript ParentAnchor dell'oggetto.

- Per il pulsante denominato, DeleteAzureAnchor, creare un nuovo evento sotto il trigger di evento fatto clic sul pulsante, nonché il trigger di evento nel fare clic su. Trascinare l'oggetto ParentAnchor nel campo vuoto e assegnare il metodo DeleteAzureAnchor() dal componente ASAmoduleScript ParentAnchor dell'oggetto.

- Per il pulsante di ancoraggio con nome, eliminare locale, creare un nuovo evento sotto il trigger di evento fatto clic sul pulsante, nonché il trigger di evento nel fare clic su. Trascinare l'oggetto ParentAnchor nel campo vuoto e assegnare il metodo RemoveLocalAnchor() dal componente ASAmoduleScript ParentAnchor dell'oggetto.

### <a name="build-and-demonstrate-base-application"></a>Compilare e dimostrare l'applicazione di Base

Dopo avere configurato la scena per illustrare i concetti fondamentali di Azure gli ancoraggi spaziali, verranno creare e illustrano il comportamento di base di Azure gli ancoraggi spaziale. 

1. Se nelle sezioni precedenti hai chiuso la finestra Build Settings (Impostazioni di compilazione), aprila nuovamente passando a File>Build Settings (File>Impostazioni di compilazione).
    ![Lesson1Chapter5Step1](images/Lesson1Chapter5Step1.JPG)

2. Assicurarsi che la scena che si desidera provare sia nelle scene nell'elenco di Build facendo clic sul pulsante Aggiungi scene Open.

3. Scegli il pulsante Build (Compila) per avviare il processo di compilazione.
    ![Lesson1Chapter5Step3](images/Lesson1Chapter5Step3.JPG)

4. Crea una nuova cartella per l'applicazione e assegna un nome alla cartella creata. Nell'immagine seguente, contenente l'applicazione è stata creata una cartella con il nome di App. Fare clic su Seleziona cartella per l'avvio della compilazione alla cartella appena creata. Intervallo dopo il completamento della compilazione, è possibile chiudere l'impostazione di compilazione"in Unity. 
    ![Lesson1Chapter5Step4](images/Lesson1Chapter5Step4.JPG)

  > NOTA: se la compilazione ha esito negativo, prova a ripeterla o a riavviare Unity e a ripetere la compilazione. Se visualizzi un errore simile al seguente: L'errore CS0246 = il nome del tipo o spazio dei nomi "XX" non è stato trovato (probabilmente manca un utilizzo della direttiva o un riferimento all'assembly?). Potrebbe essere necessario installare [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>) 
  >

5. Al termine della compilazione, apri la nuova cartella creata che contiene i file dell'applicazione appena compilata. Fare doppio clic su the"MixedRealityBase.sln soluzione o il nome corrispondente. Se si usa un nome alternativo per il progetto per aprire il file della soluzione in Visual Studio.

  > Nota: Assicurarsi di aprire la cartella appena creata (ad esempio, l'App cartella, se seguono le convenzioni di denominazione nei passaggi precedenti, perché sarà presente un file con estensione sln denominato in modo analogo di fuori di tale cartella non deve essere confusa con il file con estensione sln all'interno della cartella di compilazione. 

![Lesson1Chapter5Step5](images/Lesson1Chapter5Step5.JPG)

  > Nota: Se Visual Studio chiede di installare i componenti nuovi, dedica qualche minuto per garantire che tutti i componenti prerequisiti siano installati il più specifici in [la pagina "Installa gli strumenti"](install-the-tools.md) 

6. Collega HoloLens 2 al PC con il cavo USB. Anche se queste istruzioni lezione si presuppongono si distribuirà un test con un dispositivo HoloLens 2, si può anche scegliere di distribuire il [HoloLens 2 emulatore](using-the-hololens-emulator.md) oppure scegliere di creare un [pacchetto dell'app per il sideload](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)

7. Prima della compilazione, assicurati che il dispositivo sia in modalità sviluppatore. Se questa è la prima volta che esegui la distribuzione nel dispositivo HoloLens 2, Visual Studio può richiedere di associare HoloLens 2 a un PIN. Seguire [queste istruzioni](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio) se è necessario abilitare la modalità sviluppatore o l'associazione con Visual Studio.

8. Configurare Visual Studio per la compilazione per il 2 HoloLens, selezionare la configurazione di rilascio e l'architettura "RM".
    ![Lesson1Chapter5Step8](images/Lesson1Chapter5Step8.JPG)
   
9. Il passaggio finale consiste nella compilazione per il dispositivo selezionando Debug > Avvia senza eseguire debug. Se si seleziona Avvia senza eseguire debug, l'applicazione venga avviata immediatamente sul dispositivo alle informazioni di debug ithout compilazione riuscita di Visual Studio. Questo significa anche che, mentre l'applicazione è in esecuzione sul dispositivo HoloLens 2, puoi disconnettere il cavo USB senza arrestare l'applicazione. È anche possibile selezionare compilazione > Distribuisci soluzione da distribuire al dispositivo senza che l'applicazione avvia automaticamente.
    ![Lesson1Chapter5Step9](images/Lesson1Chapter5Step9.JPG)
    
10. seguire le istruzioni. Quando l'applicazione è in esecuzione nel dispositivo, seguire sullo schermo le istruzioni. Premere i tasti di scena corrispondente per la procedura seguente.
    
    ![module2chapter1step10eim](images/module2chapter1step10eim.PNG)
    
    1. Avviare la sessione di punti di ancoraggio spaziale.
    
    2. Spostare il cubo in una posizione diversa.
    
    3. Salvare gli ancoraggi Azure spaziali in corrispondenza della posizione del cubo.
    
    4. Arrestare la sessione di Azure Anchor spaziale.
    
    5. Rimuovere l'ancoraggio sul cubo per consentire all'utente di spostare il cubo locale.
    6. Spostare il cubo in un'altra posizione.
    
    7. Avviare la sessione di Azure Anchor spaziale.
    
    8. Trovare Azure spaziali aachors. 
    
    e si dovrebbe tornare nella posizione originale è inserirlo quando è stato creato il punto di ancoraggio).
    9. Eliminare Azure ancoraggio spaziale.
    
    10. Arrestare una sessione di Azure.

### <a name="anchoring-an-experience"></a>L'ancoraggio di un'esperienza

Nelle sezioni precedenti, si è appreso le nozioni di base di Azure gli ancoraggi spaziale. È stato utilizzato un cubo per rappresentare e visualizzare l'oggetto gioco padre con il punto di ancoraggio collegato. In questa sezione descrive come ancoraggio di un'intera esperienza inserendolo come elemento figlio dell'oggetto ParentAnchor. Per questo esempio, utilizziamo il modulo lunare applicazione demo di Assembly che è stata creata durante [modulo di Base lezione 6](mrlearning-base-ch6.md).

1. Cercare il modulo lunare Assembly completo prefab e trascinarlo fino a ottenere la gerarchia come elemento figlio il gameobject AnchorParent come illustrato nell'immagine seguente.

   ![module2chapter1step11](images/module2chapter1step11im.PNG)

2. Posizione l'assembly del modulo esperienza in modo che il cubo è ancora esposto come illustrato nell'immagine seguente. Nell'applicazione, gli utenti possono riposizionare l'intera esperienza spostando il cubo. 

   ![module2chapter1step12im](images/module2chapter1step12im.PNG)

   > Nota: Sono disponibili diversi di flussi di esperienza utente per il riposizionamento esperienze, incluso l'uso di un pulsante per attivare o disattivare un rettangolo di selezione che circonda l'esperienza, l'utilizzo di un oggetto riposizionamento (ad esempio il cubo usato in questo passaggio), l'uso di posizione e della rotazione gizmo e così via.

## <a name="congratulations"></a>Lezione completata
In questa lezione si è appreso le nozioni di base di Azure gli ancoraggi spaziale. Questo esson fornito con diversi pulsanti che consentono di esplorare i vari passaggi necessari per avviare e arrestare una sessione di Azure e creare, caricare e scaricare gli ancoraggi azure in un singolo dispositivo. Nella lezione successiva si apprenderà come salvare gli ID di ancoraggio di Azure per il 2 HoloLens per il recupero, anche dopo il riavvio dell'applicazione. Durante la serie si apprenderà anche come trasferire gli ID di ancoraggio tra più dispositivi per ottenere l'allineamento spaziale e scopri qual è multiutente condivisi sessioni (presto disponibili come parte del modulo di condivisione).

[Lezione successiva: ASA lezione 2](mrlearning-asa-ch2.md)


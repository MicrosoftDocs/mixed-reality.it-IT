---
title: Modulo ASA Learning MR Azure spaziali ancoraggio su HoloLens 2
description: Completa questo corso per informazioni su come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 7843e4de014fe14d7c40b5e6d68f72ea45b4df9e
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326474"
---
# <a name="getting-started-with-azure-spatial-anchors-on-hololens-2"></a>Introduzione a Azure ancoraggi spaziali su HoloLens 2

Questo articolo illustra il secondo modulo dell'esercitazione 2 HoloLens. Prima di iniziare, assicurarsi che tutti del [prerequisiti](https://docs.microsoft.com/en-us/azure/spatial-anchors/quickstarts/get-started-unity-hololens) vengono completate. Se non è stata completata, il primo [modulo di base](mrlearning-base.md) ancora, è consigliabile completare prima. Se sta iniziando da un nuovo progetto unity, seguire la procedura di creazione nuovo progetto nel [modulo di base](mrlearning-base.md). 

## <a name="objectives"></a>Obiettivi

* Scopri i concetti fondamentali dello sviluppo con Azure Anchor spaziali con 2 HoloLens

* Creare, caricare e scaricare gli ancoraggi spaziali

  

## <a name="instructions"></a>Istruzioni

### <a name="downloading-and-importing-assets"></a>Download e importazione delle risorse
Prima di iniziare, è necessario scaricare e importare le risorse seguenti:

[Ancoraggi nello spazio di Azure](https://github.com/azure/azure-spatial-anchors-samples/releases)

[Modulo di Base di MR pacchetto di Asset](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1)

[Modulo ASA pacchetto di Asset](https://github.com/microsoft/MixedRealityLearning/releases/tag/ASA_B2)

[Toolkit per realtà mista](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)

> Nota: vedere il passaggio 5 per istruzioni specifiche su come importare il Anchor spaziale di Azure, passaggio 6 per istruzioni specifiche per il modulo di Base di MR pacchetto di Asset e i passaggi 3 e 4 per istruzioni specifiche sul Toolkit di realtà mista.

1. creare una nuova scena nel progetto. Pulsante destro del mouse fare clic sulla cartella scena, fare clic su "Crea", quindi di scena. Denominare la nuova scena "ASALearningmodule."

![module2chapter1step1im](images/module2chapter1step1im.PNG)

2. Fare doppio clic su "ASALearningmodule" per alcuni elementi predefiniti verranno visualizzati insieme a nuova scena. 
3. Configurare la scena per lo sviluppo della realtà mista. 

![module2chapter1step3im](images/module2chapter1step3im.PNG)

> Nota: Verrà visualizzato un messaggio popup che afferma, "è necessario scegliere un file per il Toolkit di realtà mista". Facendo clic su "ok" si passerà al passaggio 4.

4. Quando si sceglie un file per il Toolkit di realtà mista, selezionare, "DefaultMixedRealityToolkitConfigurationProfile."

   > Nota: Se si ha il proprio configurazione profilo è possibile utilizzare tale applicazione.

![module2chapter1step4im](images/module2chapter1step4im.PNG)

Ora la scena è configurata per realtà mista. Assicurarsi di salvare la scena (eseguire questa operazione con uno dei due controlli / comando + S, oppure fare clic sul file, quindi fare clic su Salva). 

5. Importa i [Anchor spaziali Azure](https://github.com/azure/azure-spatial-anchors-samples/releases). Per usare gli ancoraggi spaziali, è necessario importare questo asset. Quindi, fare clic sul collegamento sopra e fare clic con il pulsante destro su "AzureSpatialAnchors.unitypackage." Fare clic su "Salva oggetto con nome" e salvarlo nel computer. 

   ![module2chapter1step5aim](images/module2chapter1step5aim.PNG)

   Quindi, dopo che viene salvato, tornerà a unity, fare clic su "risorse", andare a "import package", quindi fare clic su "pacchetto personalizzato..." I file del computer, verranno visualizzato. Una volta sono, trovare in cui è stato salvato il pacchetto Azure spaziali ancoraggi e selezionarlo. Quindi fare clic su "Apri".

   ![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

   A questo punto saranno presenti un finestra popup fornendo un elenco di strumenti e impostazioni, che richiede gli elementi da importare. Selezionare ***tutti*** delle opzioni disponibili, quindi fare clic su "Importa".

   ![module2chapter1step5cim](images/module2chapter1step5cim.PNG)

   > Nota: richiederà alcuni minuti per importare, quindi SII paziente. 

   6. Importazione [modulo di Base di MR Asset Pack](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1) successivo. Analogamente al passaggio 5, fare clic sul collegamento precedente, quindi fare clic con il pulsante destro "BasemoduleAssetsV1 1.unitypackage" e fare clic su "Salva oggetto con nome" e salvarlo nel computer.

   ![module2chapter1step6aim](images/module2chapter1step6aim.PNG)

   > Suggerimento: Salvare tutte queste risorse nella stessa cartella in modo che siano più semplici da individuare e avere accesso a. Mantengono tutti gli elementi interessanti e organizzate.

   Come passaggio 5, tornare a unity, fare clic su "risorse", "Importa pacchetto" del mouse, quindi fare clic su "personalizzata del pacchetto..." Dovrebbero essere visualizzati anche in questo caso, i file di computer passare a dove è archiviato il pacchetto di Asset del modulo di Base e quindi selezionarlo. Quindi fare clic su "Apri".

   ![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

   > Nota: potrebbe esserci altre gli asset necessari più avanti in questo modulo. Seguire questi passaggi per importare tutte le risorse indicate da questo momento. 

7. Importare il modulo ASA Pack utilizzando lo stesso approccio valido per l'importazione dei pacchetti precedenti.

### <a name="configuring-your-scene"></a>Configurazione della scena

In questa sezione verranno aggiunti gli script e prefabs nella scena per creare una serie di pulsanti che illustrano le nozioni di base del comportamento sia gli ancoraggi locali e Azure spaziali ancoraggi in un'applicazione.

7. Nella scheda "progetto" di sotto della cartella "risorse", fare clic su "ASAmoduleAssets." Una volta selezionato verrà visualizzato 2 prefabs, "ButtonParent" e "ParentAnchor."

![module2chapter1step7im](images/module2chapter1step7im.PNG)

8. Trascinare entrambi il prefabs nella scena. 

![module2chapter1step8im](images/module2chapter1step8im.PNG)

9. Fare doppio clic su ancoraggio padre per selezionarlo. Potrebbe essere necessario regolare la vista per visualizzare l'intera scena, quindi è opportuno regolare la scena in base alle esigenze.

    Acquisire familiarità con il prefab ParentAnchor. Attualmente, l'oggetto gioco denominato "ParentAnchor" è un cubo colorato, a scopo dimostrativo. Infine, verranno nascondere il cubo e inserire il contenuto come figlio di ParentAnchor. Il prefab include lo script AzureSpatialAnchorsDemoWrapper.cs (incluso con il SDK ASA) e lo script ASAmoduleScript.cs (incluso come parte di questo modulo) per l'oggetto ParentAnchor. 

10. Pulsanti di configurazione. Nel prefab ParentAnchor, si noteranno alcuni pulsanti con etichettati. Questi pulsanti vengono creati da prefab PressableButton del MRTK. Altre informazioni su come creare pulsanti Pressable dal [modulo di Base](mrlearning-base-ch2.md). Per ogni pulsante, aggiungere un evento che viene attivato quando l'utente preme o si seleziona il pulsante in base all'elenco seguente. 

- Per il pulsante denominato "StartAzureSession", creare un nuovo evento sotto il trigger di evento "Pulsante premuto" così come il trigger di evento "Scegliere". Trascinare l'oggetto ParentAnchor nel campo vuoto e assegnare il metodo StartAzureSession() dal componente ASAmoduleScript ParentAnchor dell'oggetto.

  ![module2chapter1step10aim](images/module2chapter1step10aim.PNG)

  ![module2chapter1step10bim](images/module2chapter1step10bim.PNG)

  ![module2chapter1step10cim](images/module2chapter1step10fim.PNG)

- Per il pulsante denominato "StopAzureSession", creare un nuovo evento sotto il trigger di evento "Pulsante premuto" così come il trigger di evento "Scegliere". Trascinare l'oggetto ParentAnchor nel campo vuoto e assegnare il metodo StopAzureSession() dal componente ASAmoduleScript ParentAnchor dell'oggetto.

- Per il pulsante denominato "CreateAnchor", creare un nuovo evento sotto il trigger di evento "Pulsante premuto" così come il trigger di evento "Scegliere". Trascinare l'oggetto ParentAnchor nel campo vuoto e assegnare il metodo CreateAzureAnchor() dal componente ASAmoduleScript ParentAnchor dell'oggetto.

- Per il pulsante "Avvia la ricerca per ancoraggio", creare un nuovo evento sotto il trigger di evento "Pulsante premuto" così come il trigger di evento "Scegliere". Trascinare l'oggetto ParentAnchor nel campo vuoto e assegnare il metodo FindAzureAnchor() dal componente ASAmoduleScript ParentAnchor dell'oggetto.

- Per il pulsante denominato "DeleteAzureAnchor", creare un nuovo evento sotto il trigger di evento "Pulsante premuto" così come il trigger di evento "Scegliere". Trascinare l'oggetto ParentAnchor nel campo vuoto e assegnare il metodo DeleteAzureAnchor() dal componente ASAmoduleScript ParentAnchor dell'oggetto.

- Per il pulsante "Elimina ancoraggio locale", creare un nuovo evento sotto il trigger di evento "Pulsante premuto" così come il trigger di evento "Scegliere". Trascinare l'oggetto ParentAnchor nel campo vuoto e assegnare il metodo RemoveLocalAnchor() dal componente ASAmoduleScript ParentAnchor dell'oggetto.

### <a name="build-and-demonstrate-base-application"></a>Compilare e dimostrare l'applicazione di Base

Dopo avere configurato la scena per illustrare i concetti fondamentali di Azure gli ancoraggi spaziali, verranno creare e illustrano il comportamento di base di Azure gli ancoraggi spaziale. 

1. Se nelle sezioni precedenti hai chiuso la finestra Build Settings (Impostazioni di compilazione), aprila nuovamente passando a File>Build Settings (File>Impostazioni di compilazione).
    ![Lesson1Chapter5Step1](images/Lesson1Chapter5Step1.JPG)

2. Assicurati che la scena che vuoi provare sia nell'elenco "Scenes in Build" (Scene nella compilazione) facendo clic sul pulsante "Add Open Scenes" (Aggiungi scene aperte).

3. Scegli il pulsante Build (Compila) per avviare il processo di compilazione.
    ![Lesson1Chapter5Step3](images/Lesson1Chapter5Step3.JPG)

4. Crea una nuova cartella per l'applicazione e assegna un nome alla cartella creata. Nell'immagine seguente è stata creata una cartella con il nome "App" per contenere l'applicazione. Fai clic su "Select Folder" (Seleziona cartella) per iniziare la compilazione nella cartella appena creata. Al termine della compilazione, puoi chiudere la finestra "Build Settings" (Impostazioni di compilazione) in Unity. 
    ![Lesson1Chapter5Step4](images/Lesson1Chapter5Step4.JPG)

  > NOTA: se la compilazione ha esito negativo, prova a ripeterla o a riavviare Unity e a ripetere la compilazione. Se visualizzi un errore simile al seguente: L'errore CS0246 = il nome del tipo o spazio dei nomi "XX" non è stato trovato (probabilmente manca un utilizzo della direttiva o un riferimento all'assembly?) ", potrebbe essere necessario installare [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>) 
  >

5. Al termine della compilazione, apri la nuova cartella creata che contiene i file dell'applicazione appena compilata. Fai doppio clic sulla soluzione "MixedRealityBase.sln" (o il nome corrispondente, se hai usato un nome alternativo per il progetto) per aprire il file della soluzione in Visual Studio.

  > Nota: assicurati di aprire la cartella appena creata (ad esempio la cartella "App", se hai seguito le convenzioni di denominazione dei passaggi precedenti) perché un file con estensione sln denominato in modo analogo sarà presente al di fuori di tale cartella e non devi confonderlo con il file con estensione sln all'interno della cartella di compilazione. 

![Lesson1Chapter5Step5](images/Lesson1Chapter5Step5.JPG)

  > Nota: Se visual studio chiede di installare i componenti nuovi, dedica qualche minuto per garantire che tutti i componenti prerequisiti siano installati il più specifici in [la pagina "Installa gli strumenti"](install-the-tools.md) 

6. Collega HoloLens 2 al PC con il cavo USB. Anche se queste istruzioni lezione si presuppongono si distribuirà un test con un dispositivo HoloLens 2, si può anche scegliere di distribuire il [HoloLens 2 emulatore](using-the-hololens-emulator.md) oppure scegliere di creare un [pacchetto dell'app per il sideload](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)

7. Prima della compilazione, assicurati che il dispositivo sia in modalità sviluppatore. Se questa è la prima volta che esegui la distribuzione nel dispositivo HoloLens 2, Visual Studio può richiedere di associare HoloLens 2 a un PIN. Segui [queste istruzioni](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio) se devi abilitare la modalità sviluppatore o eseguire l'associazione con Visual Studio.

8. Configura Visual Studio per la compilazione nel dispositivo HoloLens 2 selezionando la configurazione "Release" e l'architettura "ARM".
    ![Lesson1Chapter5Step8](images/Lesson1Chapter5Step8.JPG)
    
9. Il passaggio finale consiste nella compilazione per il dispositivo selezionando Debug > Avvia senza eseguire debug. Se selezioni "Avvia senza eseguire debug", l'applicazione viene avviata immediatamente nel dispositivo al termine della compilazione, ma senza che in Visual Studio vengano visualizzate le informazioni di debug. Questo significa anche che, mentre l'applicazione è in esecuzione sul dispositivo HoloLens 2, puoi disconnettere il cavo USB senza arrestare l'applicazione. Puoi anche selezionare Compila>Distribuisci soluzione per distribuire l'applicazione nel dispositivo senza che venga avviata automaticamente.
    ![Lesson1Chapter5Step9](images/Lesson1Chapter5Step9.JPG)
    
10. Quando l'applicazione è in esecuzione nel dispositivo, seguire sullo schermo le istruzioni. Premere i pulsanti di scena corrispondente per la procedura seguente.
    
    ![module2chapter1step10eim](images/module2chapter1step10eim.PNG)
    
    1. Avviare la sessione di Azure Anchor spaziale.
    
    2. Spostare il cubo in una posizione diversa.
    
    3. Salvare gli ancoraggi Azure spaziali in corrispondenza della posizione del cubo.
    
    4. Arrestare la sessione di Azure Anchor spaziale.
    
    5. Rimuovere l'ancoraggio sul cubo per consentire all'utente di spostare il cubo locale.
    6. Spostare il cubo in un'altra posizione.
    
    7. Avviare la sessione di Azure Anchor spaziale.
    
    8. Trovare Azure Anchor spaziale.
    (ora cubo deve tornare nella posizione originale è inserirlo quando è stato creato il punto di ancoraggio).
    9. Eliminare Azure ancoraggio spaziale.
    
    10. Arrestare una sessione di Azure.

### <a name="anchoring-an-experience"></a>L'ancoraggio di un'esperienza

Nelle sezioni precedenti, si è appreso le nozioni di base di Azure gli ancoraggi spaziale. È stato utilizzato un cubo per rappresentare e visualizzare l'oggetto gioco padre con il punto di ancoraggio collegato. In questa sezione si wiill come ancoraggio di un'intera esperienza inserendolo come elemento figlio dell'oggetto ParentAnchor. In questo esempio si userà l'app demo di Assembly del modulo lunare creato durante [modulo di Base lezione 6](mrlearning-base-ch6.md).

1. Cercare il modulo lunare Assembly completo prefab e trascinarlo fino a ottenere la gerarchia come figlio degli elementi gameobject AnchorParent, come illustrato nell'immagine seguente.

   ![module2chapter1step11](images/module2chapter1step11im.PNG)

2. Posizionare l'esperienza di assembly del modulo in modo che il cubo viene ancora esposta, come illustrato nell'immagine seguente. Nell'applicazione, gli utenti possono riposizionare l'intera esperienza spostando il cubo. 

   ![module2chapter1step12im](images/module2chapter1step12im.PNG)

   > Nota: Sono disponibili diversi di flussi di esperienza utente per il riposizionamento esperienze, incluso l'uso di un pulsante per attivare o disattivare un rettangolo di selezione che circonda l'esperienza, l'utilizzo di un oggetto riposizionamento (ad esempio il cubo usato in questo passaggio), l'uso di posizione e della rotazione gizmo e così via.

## <a name="congratulations"></a>Lezione completata
In questa lezione si è appreso le nozioni di base di Azure gli ancoraggi spaziale. In questa lezione è fornito con diversi pulsanti consente di esplorare i vari passaggi necessari per avviare e arrestare una sessione di Azure e creare, caricare e scaricare gli ancoraggi azure in un singolo dispositivo. Nella lezione successiva si apprenderà come salvare gli ID di ancoraggio di Azure per il 2 HoloLens per il recupero, anche dopo il riavvio dell'applicazione. Durante la serie verrà anche informazioni su come trasferire gli ID di ancoraggio tra più dispositivi per ottenere l'allineamento spaziale e apprendere infine multiutente condivisi sessioni (presto disponibili come parte del modulo di condivisione).

[Lezione successiva: ASA lezione 2](mrlearning-asa-ch2.md)


---
title: Esercitazioni sugli ancoraggi spaziali di Azure-1. Introduzione agli ancoraggi spaziali di Azure
description: Completa questo corso per apprendere come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: b615f1135f5d2947f8f718e080ef45a3c1fcc576
ms.sourcegitcommit: 05fa75193059a2dac4b580a9eef7b6c4bb64d8d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74830842"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a>1. Introduzione agli ancoraggi spaziali di Azure

Benvenuti nel secondo modulo delle esercitazioni di HoloLens 2. Prima di iniziare, assicurarsi che tutti i [prerequisiti](https://docs.microsoft.com//azure/spatial-anchors/quickstarts/get-started-unity-hololens) siano stati completati. Se non è stato ancora completato il primo [modulo di base](mrlearning-base.md) , è consigliabile completare prima il modulo. Se si inizia da un nuovo progetto Unity, seguire la procedura di creazione del nuovo progetto nel [modulo di base](mrlearning-base.md). 

## <a name="objectives"></a>Obiettivi

* Scopri le nozioni di base sullo sviluppo con i Anchor spaziali di Azure con HoloLens 2

* Creare, caricare e scaricare ancoraggi spaziali

## <a name="instructions"></a>Istruzioni

### <a name="downloading-and-importing-assets"></a>Download e importazione di asset
Prima di iniziare, scaricare e importare gli asset seguenti:

[Ancoraggi spaziali di Azure v 1.1.0](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v1.1.0/AzureSpatialAnchors.unitypackage)

[Unity. HoloLens2. GettingStarted. Tutorials. asset. 2.1.0.0. file unitypackage Tools](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.0/Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage)

[Unity. HoloLens2. AzureSpatialAnchor. Tutorials. asset. 2.1.0.0. file unitypackage Tools](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchor-v2.1.0.0/Unity.HoloLens2.AzureSpatialAnchor.Tutorials.Asset.2.1.0.0.unitypackage)

[Pacchetto di 2.1.0 di reality Toolkit Foundation](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.1.0)

1. Creare una nuova scena nel progetto. Fare clic con il pulsante destro del mouse sulla cartella della scena, scegliere Crea, quindi scena. Assegnare alla nuova scena il nome "ASALearningModule".

![module2chapter1step1im](images/module2chapter1step1im.PNG)

2. Fare doppio clic sulla scena "ASALearningmodule" per visualizzare alcuni elementi predefiniti da visualizzare insieme alla nuova scena. 
3. Configurare la scena per lo sviluppo di realtà mista. 

![module2chapter1step3im](images/module2chapter1step3im.PNG)

> Nota: è possibile che venga visualizzata una finestra di dialogo popup per la selezione di un [profilo per il Toolkit di realtà mista](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html). Scegliere il profilo denominato *DefaultHoloLens2ConfigurationProfile* facendo doppio clic su di esso.

4. Quando si sceglie un file per il MRTK, selezionare DefaultMixedRealityToolkitConfigurationProfile.

> Nota: se si dispone di un profilo di configurazione personalizzato, è possibile usarlo in alternativa.
>

![module2chapter1step4im](images/module2chapter1step4im.PNG)

La scena è ora configurata per la realtà mista. Assicurarsi di salvare la scena (eseguire questa operazione con il controllo/comando + S oppure fare clic su file, quindi su Salva). 

5. Importare il pacchetto [Azure Spatial Anchors v 1.1.0](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v1.1.0/AzureSpatialAnchors.unitypackage) Unity scaricato nel passaggio 1. A tale proposito, fare clic su asset, passare a importa pacchetto, quindi fare clic su pacchetto personalizzato... I file del computer si apriranno. Quando si esegue questa operazione, trovare la posizione in cui è stato salvato il pacchetto di ancoraggi spaziali di Azure e selezionarlo. Quindi fare clic su Apri.

![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

Viene visualizzato un popup che fornisce un elenco di strumenti e impostazioni e chiede cosa importare. Selezionare ***tutte*** le opzioni disponibili, quindi fare clic su Importa.

![module2chapter1step5cim](images/module2chapter1step5cim.PNG)

> Nota: l'importazione può richiedere alcuni minuti. 

6. Importare [Unity. HoloLens2. GettingStarted. Tutorials. asset. 2.1.0.0. file unitypackage Tools](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.0/Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage) Next. Analogamente al passaggio 5, tornare a Unity, fare clic su assets e passare il puntatore sul pacchetto di importazione. Fare clic su pacchetto personalizzato... I file del computer verranno visualizzati di nuovo. Passare alla posizione in cui è stato archiviato il modulo di base asset Pack. e selezionarlo. Fare clic su Apri.

![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

> Nota: potrebbero essere presenti più asset necessari più avanti in questo modulo. Seguire questa procedura per importare le risorse indicate da questo punto in poi. 

7. Importare il [modulo ASA Pack 1.3.1](https://github.com/Developer-OI/MixedRealityLearning/releases/download/ASA_1.3/ASAModuleAssets_1.3.1.unitypackage), usando la stessa procedura usata per importare i pacchetti precedenti.

### <a name="configuring-your-scene"></a>Configurazione della scena

In questa sezione vengono aggiunti i prefabbricati e gli script nella scena per creare una serie di pulsanti che dimostrano le nozioni di base del comportamento di entrambi gli ancoraggi locali e degli ancoraggi spaziali di Azure in un'applicazione.

8. Nella scheda progetto, sotto la cartella assets, fare clic su ASAmoduleAssets. Una volta selezionate, vengono visualizzati due prefabbricati: ButtonParent e ParentAnchor.

![module2chapter1step7im](images/module2chapter1step7im.PNG)

9. Trascinare entrambi i prefabbricati nella scena. 

![module2chapter1step8im](images/module2chapter1step8im.PNG)

Nota: dopo aver aggiunto ButtonParent alla scena, viene visualizzata una finestra popup in cui viene chiesto di importare le risorse TMP. Importare "TMP Essentials". Successivamente, se nella scena viene visualizzato un testo di tipo carattere di grandi dimensioni, eliminare l'oggetto ButtonParent e aggiungerlo di nuovo dalla cartella ASAmoduleAssets.

Nota: se si desidera controllare i log di debug in HoloLens, è possibile trascinare e rilasciare il DebugWindow prefabbricate dalla cartella ASAModuleAssets alla scena. Alleghi lo script DebugWindowMessaging nel pannello DebugWindow Inspector e Abilita l'opzione debug window Enabled. Successivamente, trascinare e rilasciare la prefabbricazione DebugWindow nel campo DebugText Empty. È anche possibile modificare la posizione del DebugWindow laddove appropriato.

10. Per eseguire lo zoom avanti sulla scena, fare doppio clic sull'ancoraggio padre nella gerarchia e modificare la visualizzazione per visualizzare l'intera scena in base alle esigenze. Attualmente, ParentAnchor è un cubo colorato utilizzato solo a scopo dimostrativo. Infine, il cubo verrà nascosto e il contenuto verrà inserito come elemento figlio di ParentAnchor. 

11. A questo punto è possibile configurare i pulsanti per il funzionamento della scena. A tale proposito, espandere la prefabbricazione ButtonParent e si noterà che sono presenti diversi pulsanti con etichetta, che vengono creati dai prefabbricati PressableButton di MRTK. Altre informazioni su come creare PressableButton dal modulo di [base](mrlearning-base-ch2.md). Per il funzionamento di questi pulsanti, è necessario aggiungere un evento che verrà attivato quando l'utente preme o seleziona i singoli pulsanti. 

- Per il pulsante denominato StartAzureSession, creare un nuovo evento sotto il trigger di evento premuto sul pulsante, nonché il trigger di evento click on. Trascinare l'oggetto ParentAnchor nel campo vuoto e assegnare il metodo StartAzureSession () dal componente ASAmoduleScript dell'oggetto ParentAnchor, come illustrato nella schermata seguente.
- ![module2chapter1step10aim](images/module2chapter1step10aim.PNG)

![module2chapter1step10bim](images/module2chapter1step10bim.PNG)

![module2chapter1step10cim](images/module2chapter1step10fim.PNG)

- Per il pulsante denominato StopAzureSession, creare un nuovo evento sotto il trigger di evento premuto sul pulsante, nonché il trigger di evento click on. Trascinare l'oggetto ParentAnchor nel campo vuoto e assegnare il metodo StopAzureSession () dal componente ASAmoduleScript dell'oggetto ParentAnchor.

- Per il pulsante denominato CreateAnchor, creare un nuovo evento sotto il trigger di evento premuto sul pulsante, nonché il trigger di evento click on. Trascinare l'oggetto ParentAnchor nel campo vuoto e assegnare il metodo CreateAzureAnchor () dal componente ASAmoduleScript dell'oggetto ParentAnchor.  **Successivamente, trascinare di nuovo ParentAnchor nel campo "oggetto gioco" vuoto successivo.**

- Per il pulsante denominato Avvia ricerca di ancoraggio, creare un nuovo evento sotto il pulsante premere "trigger evento, così come il trigger di evento click. Trascinare l'oggetto ParentAnchor nel campo vuoto e assegnare il metodo FindAzureAnchor () dal componente ASAmoduleScript dell'oggetto ParentAnchor.

- Per il pulsante denominato DeleteAzureAnchor, creare un nuovo evento sotto il trigger di evento premuto sul pulsante, nonché il trigger di evento click on. Trascinare l'oggetto ParentAnchor nel campo vuoto e assegnare il metodo DeleteAzureAnchor () dal componente ASAmoduleScript dell'oggetto ParentAnchor.  

- Per il pulsante denominato Elimina ancoraggio locale, creare un nuovo evento sotto il trigger evento premuto pulsante, nonché il trigger di evento clic su. Trascinare l'oggetto ParentAnchor nel campo vuoto e assegnare il metodo RemoveLocalAnchor () dal componente ASAmoduleScript dell'oggetto ParentAnchor. **Successivamente, trascinare nuovamente l'oggetto ParentAnchor nel campo "oggetto gioco" vuoto successivo.**

12. Per configurare gli ancoraggi spaziali di Azure, passare alla cartella AzureSpatialAnchorsPlugin nella cartella assets e passare a examples-> Resources-> file AzureSpatialAnchorsDemoConfig. Nel pannello Inspector aggiungere l'ID dell'account di Azure e la chiave dell'account creati in precedenza. Se non sono stati creati o non sono disponibili, attenersi ai [prerequisiti](https://docs.microsoft.com//azure/spatial-anchors/quickstarts/get-started-unity-hololens). 

  ![module2chapter1step13im](images/module2chapter1step13im.PNG)

### <a name="build-and-demonstrate-base-application"></a>Compilare e dimostrare l'applicazione di base

Ora che la scena è configurata in modo da illustrare gli elementi di base degli ancoraggi spaziali di Azure, verrà creato e illustrato il comportamento di base degli ancoraggi spaziali di Azure. 

1. Aprire di nuovo la finestra impostazioni di compilazione, passando a file > impostazioni di compilazione.
    ![mrlearning-ASA-CH1-3-Step1](images/mrlearning-asa-ch1-3-step1.jpg)
2. Assicurarsi che la scena che si vuole provare sia presente nelle quinte dell'elenco compilazione facendo clic sul pulsante Aggiungi scene aperte.
3. Verificare che la piattaforma sia impostata sul piattaforma UWP (Universal Windows Platform). In caso contrario, impostarlo sullo stesso.
4. Premere il pulsante Impostazioni lettore e passare a impostazioni di pubblicazione. In funzionalità abilitare: Internet, server client Internet, server client di rete privata, archiviazione rimovibile, webcam, microfono e percezione spaziale.
5. Nelle stesse impostazioni del lettore passare a XR Settings e selezionare la realtà virtuale supportata su ON.
6. Scegli il pulsante Build (Compila) per avviare il processo di compilazione.
   ![mrlearning-ASA-CH1-3-passaggio 6](images/mrlearning-asa-ch1-3-step6.jpg)
7. Crea una nuova cartella per l'applicazione e assegna un nome alla cartella creata. Nell'immagine seguente è stata creata una cartella con l'app nome per contenere l'applicazione. Fare clic su Seleziona cartella per iniziare a compilare la cartella appena creata. Al termine della compilazione, è possibile chiudere l'impostazione di compilazione "finestra in Unity.

    ![mrlearning-ASA-CH1-3-STEP7](images/mrlearning-asa-ch1-3-step7.jpg)

    > Nota: se la compilazione ha esito negativo, riprovare a compilare o riavviare Unity e compilare nuovamente. Se viene visualizzato un errore simile a "errore: CS0246 = Impossibile trovare il tipo o il nome dello spazio dei nomi" XX ". probabilmente manca una direttiva using o un riferimento all'assembly. potrebbe essere necessario installare [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com//windows/downloads/windows-10-sdk>) . 


8. Anche dopo una compilazione corretta, è possibile che vengano visualizzati alcuni errori, come illustrato di seguito, ma se la compilazione ha esito positivo, è possibile ignorarli e procedere con i passaggi successivi.

    ![mrlearning-ASA-CH1-3-step7B](images/mrlearning-asa-ch1-3-step7B.png)

    

9. Al termine della compilazione, apri la nuova cartella creata che contiene i file dell'applicazione appena compilata. Fare doppio clic sulla soluzione "MixedRealityBase. sln" o sul nome corrispondente se è stato usato un nome alternativo per il progetto per aprire il file della soluzione in Visual Studio.

    > Nota: assicurarsi di aprire la cartella appena creata (ad esempio, la cartella dell'app, se si seguono le convenzioni di denominazione dei passaggi precedenti, in quanto sarà presente un file con estensione sln analogo al di fuori della cartella che non deve essere confuso con il file con estensione sln all'interno della cartella di compilazione.

    ![mrlearning-ASA-CH1-3-Step8](images/mrlearning-asa-ch1-3-step8.jpg)

    > Nota: se Visual Studio chiede di installare nuovi componenti, assicurarsi che tutti i componenti dei prerequisiti siano installati come specifici nella [pagina "installazione degli strumenti"](install-the-tools.md) .


9. Collega HoloLens 2 al PC con il cavo USB. Sebbene queste istruzioni della lezione presuppongano che si stia distribuendo un test con un dispositivo HoloLens 2, è anche possibile scegliere di eseguire la distribuzione nell' [emulatore HoloLens 2](using-the-hololens-emulator.md) o scegliere di creare un [pacchetto dell'app per sideload](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)

10. Prima di creare il dispositivo, assicurarsi che sia in modalità sviluppatore. Se questa è la prima volta che si esegue la distribuzione in HoloLens 2, è possibile che in Visual Studio venga chiesto di associare HoloLens 2 a un PIN. Seguire [queste istruzioni](https://docs.microsoft.com//windows/mixed-reality/using-visual-studio) se è necessario abilitare la modalità sviluppatore o la coppia con Visual Studio.

11. Configurare Visual Studio per la compilazione in HoloLens 2, selezionando la configurazione per la versione e l'architettura ARM.

    ![mrlearning-ASA-CH1-3-STEP11](images/mrlearning-asa-ch1-3-step11.jpg)


12. Il passaggio finale consiste nella compilazione nel dispositivo selezionando Debug>Avvia senza eseguire debug. Se si seleziona Avvia senza eseguire debug, l'applicazione viene avviata immediatamente sul dispositivo dopo una compilazione riuscita senza informazioni di debug visualizzate in Visual Studio. Questo significa anche che, mentre l'applicazione è in esecuzione sul dispositivo HoloLens 2, puoi disconnettere il cavo USB senza arrestare l'applicazione. È anche possibile selezionare Compila > Distribuisci soluzione per eseguire la distribuzione nel dispositivo senza che l'applicazione venga avviata automaticamente.

    ![mrlearning-ASA-CH1-3-step12](images/mrlearning-asa-ch1-3-step12.jpg)

>Nota: gli ancoraggi spaziali di Azure usano Internet per salvare e caricare i dati di ancoraggio, quindi assicurarsi che il dispositivo sia connesso a Internet prima di testare l'app ASA.

13. Segui le istruzioni visualizzate. 
    Quando l'applicazione è in esecuzione nel dispositivo, seguire le istruzioni visualizzate. Premere i pulsanti della scena corrispondenti ai passaggi seguenti. Se è stata aggiunta la finestra di debug come indicato nei passaggi precedenti, è possibile visualizzare i commenti e i suggerimenti dei singoli pulsanti e lo stato di avanzamento delle singole operazioni correlate agli ancoraggi spaziali di Azure.

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

Nelle sezioni precedenti sono state apprese le nozioni di base degli ancoraggi spaziali di Azure. È stato usato un cubo per rappresentare e visualizzare l'oggetto del gioco padre con l'ancoraggio collegato. In questa sezione verrà illustrato come ancorare un'intera esperienza inserendola come elemento figlio dell'oggetto ParentAnchor. Per questo esempio viene usata l'applicazione dimostrativa dell'assembly del modulo Lunar creata durante la [lezione 6 del modulo di base](mrlearning-base-ch6.md).

1. Cercare il prefabbricato "lanciarazzi complete" e trascinarlo nella gerarchia come figlio dell'oggetto (vedere l'immagine seguente).

![module2chapter1step11](images/module2chapter1step11im.PNG)

2. Posizionare l'esperienza di assembly del modulo in modo che il cubo venga ancora esposto, come illustrato nell'immagine seguente. Nell'applicazione, gli utenti possono riposizionare l'intera esperienza spostando il cubo. 

![module2chapter1step12im](images/module2chapter1step12im.PNG)

> Nota: per le esperienze di riposizionamento sono disponibili diversi flussi di esperienza utente, tra cui l'uso di un pulsante per alternare un rettangolo di selezione che racchiude l'esperienza, l'uso di un oggetto di riposizionamento (ad esempio il cubo usato in questo passaggio), l'uso della posizione e della rotazione Gizmo e altro ancora.

## <a name="congratulations"></a>Lezione completata
In questa esercitazione sono state apprese le nozioni di base degli ancoraggi spaziali di Azure. Questa lezione ha fornito diversi pulsanti che consentono di esplorare i diversi passaggi necessari per avviare e arrestare una sessione di Azure e creare, caricare e scaricare gli ancoraggi di Azure in un singolo dispositivo. Nella lezione successiva si apprenderà come salvare gli ID di ancoraggio di Azure in HoloLens 2 per il recupero, anche dopo il riavvio dell'applicazione. Durante la serie, si apprenderà anche come trasferire gli ID di ancoraggio tra più dispositivi per ottenere l'allineamento spaziale e acquisire informazioni sulle sessioni condivise multiutente, imminenti come parte dell'esercitazione di condivisione.

[Lezione successiva: 2. salvataggio, recupero e condivisione di ancoraggi spaziali di Azure](mrlearning-asa-ch2.md)


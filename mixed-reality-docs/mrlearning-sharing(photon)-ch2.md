---
title: Esercitazioni sulle funzionalità multiutente-2. Preparazione di Unity per lo sviluppo
description: Completare questo corso per apprendere come implementare esperienze condivise multiutente all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 6abf4fa8fc87afc7007d6f7c76becfbd88ed7a12
ms.sourcegitcommit: 2bfe9b1af4ee2cc0d668caeccb8ebc3137cbc20b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901510"
---
# <a name="2-getting-unity-ready-for-development"></a>2. recupero di Unity pronto per lo sviluppo

In questa esercitazione si apprenderà come preparare e configurare Unity per lo sviluppo di applicazioni, tra cui importare il Toolkit di realtà mista, configurare le impostazioni di compilazione e preparare la scena.

## <a name="objectives"></a>Obiettivi

* Configurare Unity per lo sviluppo di applicazioni
* Importare Mixed Reality Toolkit
* Preparare la scena del progetto

## <a name="instructions"></a>Istruzioni

1. Scaricare e salvare il pacchetto Mixed Reality Toolkit Foundation Unity facendo clic [qui.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)

2. In Unity fare clic sul menu assets e selezionare Import Package, quindi fare clic su Custom Package.

    ![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. Selezionare il pacchetto Unity appena scaricato dal collegamento fornito nel passaggio 1. Una volta visualizzata la finestra popup importa in Unity, fare clic sul pulsante Import (importa) per avviare l'importazione del MRTK. Questa operazione può richiedere alcuni minuti.

    ![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

    >[!NOTE]
    >Il pacchetto scaricato si trova nella cartella locale in cui è stato salvato il file. L'immagine precedente non rappresenta la posizione in cui si troverà il pacchetto.

4. Creare una nuova scena. Questa operazione può essere eseguita facendo clic su file e selezionando nuova scena. Salvarlo come HLSharedProjectMain.

    È possibile che venga visualizzato un popup simile all'immagine seguente. Per il momento, fare clic su No.
    ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. In Mixed Reality Toolkit fare clic su Aggiungi a scena e configurare.

    ![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. Una volta completato, viene visualizzato un nuovo file di configurazione che consente di scegliere di personalizzare il profilo.

    ![Module2Chapter1step4ima](images/Module2Chapter1step4ima.PNG)

7. Selezionare il Toolkit di realtà mista (MRTK) dalla gerarchia. Nel pannello Inspector cercare lo script Mixed Reality Toolkit e premere il pulsante "copy & Customize", come illustrato nella figura seguente.  Un pop verrà visualizzato dopo questo e selezionare l'opzione Clona nel menu a comparsa.

    ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

    ![Module3Chapter2step6imd](images/module3chapter2step6imd.PNG)

8. Scorrere verso il basso e deselezionare Abilita sistema di diagnostica se si desidera nascondere la finestra di diagnostica. È consigliabile mantenere la finestra di diagnostica abilitata durante lo sviluppo di applicazioni per monitorare le prestazioni e quindi disabilitarla durante le dimostrazioni di produzione o di applicazioni. 

    ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

9. Per aprire le impostazioni di compilazione, premere CTRL + MAIUSC + B o passare a file-> impostazioni di compilazione. Si noti che il programma è attualmente impostato nel computer, Mac e piattaforma autonoma Linux. Per lo sviluppo HoloLens 2, impostare la piattaforma da piattaforma UWP (Universal Windows Platform). Selezionarlo e fare clic su switch Platform.

    ![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

10. Al termine, fare clic sulla casella denominata Aggiungi scene aperte. Passare ora al pannello Inspector e verificare che la casella di controllo a destra della realtà virtuale supportata (come illustrato nell'immagine seguente) sia selezionata. Assicurarsi inoltre che sia selezionata anche la casella di controllo accanto a Scenes/HLSharedProjectMain, come illustrato nell'immagine seguente.

    ![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

11. Nella sezione impostazioni di pubblicazione del pannello Inspector scorrere fino a funzionalità e verificare che le caselle di controllo seguenti siano contrassegnate:

    ![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

12. Importare i pacchetti personalizzati elencati:

    a. [AzureSpatialAnchors. file unitypackage Tools](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.0.0/AzureSpatialAnchors.unitypackage) (versione 2.0.0)

    b. [MRTK. HoloLens2. Unity. Esercitations. assets. GettingStarted. 2.1.0.1. file unitypackage Tools](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.1.0.1.unitypackage)

    c. [MRTK. HoloLens2. Unity. Esercitations. assets. AzureSpatialAnchors. 2.1.0.1. file unitypackage Tools](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.1.0.1.unitypackage)

    d. [MRTK. HoloLens2. Unity. Esercitations. assets. MultiUserCapabilities. 2.1.0.1. file unitypackage Tools](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage)

    >[!TIP]
    >Per un promemoria su come configurare un progetto Unity per gli ancoraggi spaziali di Azure, è possibile fare riferimento all'esercitazione [Introduzione all'ancoraggio spaziale](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) di Azure che fa parte della serie di esercitazioni sugli [ancoraggi spaziali di Azure](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) .

    ![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

13. Nel pannello progetto passare alla cartella prefabbricates. Nei passaggi seguenti vengono implementati alcuni prefabbricati nella scena. Nella cartella prefabbricati, fare clic e trascinare la finestra prefabbricata, debug nella gerarchia. Al termine, salvare il progetto facendo clic su file, quindi su Salva o premere CTRL + S.

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

    È possibile che venga visualizzato un messaggio popup quando si fa clic sul prefabbricato, che richiede informazioni su TMP Essentials. Fare clic su Importa TMP Essentials in base alle esigenze. Se viene visualizzato questo popup, potrebbe essere necessario eliminare il prefabbricato dalla gerarchia e trascinarlo nella gerarchia per evitare potenziali errori correlati al testo.

    ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)

## <a name="congratulations"></a>Lezione completata

Il progetto Unity è ora pronto per Photon. Nelle esercitazioni riportate di seguito verrà creata questa scena e il progetto Unity per un'esperienza condivisa completa.

[Esercitazione successiva: 3. connessione di più utenti](mrlearning-sharing(photon)-ch3.md)

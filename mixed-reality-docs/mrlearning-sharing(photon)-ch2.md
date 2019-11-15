---
title: Esercitazioni sulle funzionalità multiutente-2. Preparazione di Unity per lo sviluppo
description: Completare questo corso per apprendere come implementare esperienze condivise multiutente all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 750161ff4c52a7ab71869b3cb0f97197d4ad09f2
ms.sourcegitcommit: 781e47db2ca2f2c792c95e76ac309b44b3535555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2019
ms.locfileid: "74106039"
---
# <a name="2-getting-unity-ready-for-development"></a>2. recupero di Unity pronto per lo sviluppo 


In questa esercitazione si apprenderà come preparare e configurare Unity per lo sviluppo di applicazioni, tra cui importare il Toolkit di realtà mista, configurare le impostazioni di compilazione e preparare la scena.

## <a name="objectives"></a>Obiettivi

- Configurare Unity per lo sviluppo di applicazioni

- Importare Mixed Reality Toolkit

- Preparare la scena del progetto

## <a name="instructions"></a>Istruzioni

1. Scaricare e salvare il pacchetto Mixed Reality Toolkit Foundation Unity facendo clic [qui.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)

2. In Unity fare clic sul menu assets e selezionare Import Package, quindi fare clic su Custom Package.

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. Selezionare il pacchetto Unity appena scaricato dal collegamento fornito nel passaggio 1. Una volta visualizzata la finestra popup importa in Unity, fare clic sul pulsante Import (importa) per avviare l'importazione del MRTK. L'operazione potrebbe richiedere alcuni minuti.

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> Nota: il pacchetto scaricato si trova nella cartella locale in cui è stato salvato il file. L'immagine precedente non rappresenta la posizione in cui si troverà il pacchetto.

4. Creare una nuova scena. Questa operazione può essere eseguita facendo clic su file e selezionando nuova scena. Salvarlo come HLSharedProjectMain.

> Nota: è possibile che venga visualizzato un popup simile all'immagine seguente. Per il momento, fare clic su No.
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. In Mixed Reality Toolkit fare clic su Aggiungi a scena e configurare.

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. Una volta completato, viene visualizzato un nuovo file di configurazione che consente di scegliere di personalizzare il profilo. 

![Module2Chapter1step4ima](images/Module2Chapter1step4ima.PNG)

7. Selezionare il Toolkit di realtà mista (MRTK) dalla gerarchia. Nel pannello Inspector cercare lo script Mixed Reality Toolkit e premere il pulsante "copy & Customize", come illustrato nella figura seguente.  Un pop verrà visualizzato dopo questo e selezionare l'opzione Clona nel menu a comparsa.

![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

![Module3Chapter2step6imd](images/module3chapter2step6imd.PNG)

7. Scorrere verso il basso e deselezionare Abilita sistema di diagnostica se si desidera nascondere la finestra di diagnostica. È consigliabile mantenere la finestra di diagnostica abilitata durante lo sviluppo di applicazioni per monitorare le prestazioni e quindi disabilitarla durante le dimostrazioni di produzione o di applicazioni. 

![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

8. Per aprire le impostazioni di compilazione, premere CTRL + MAIUSC + B o passare a file-> impostazioni di compilazione. Si noti che il programma è attualmente impostato nel computer, Mac e piattaforma autonoma Linux. Per lo sviluppo HoloLens 2, impostare la piattaforma da piattaforma UWP (Universal Windows Platform). Selezionarlo e fare clic su switch Platform.

![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

9. Al termine, fare clic sulla casella denominata Aggiungi scene aperte. Passare ora al pannello Inspector e verificare che la casella di controllo a destra della realtà virtuale supportata (come illustrato nell'immagine seguente) sia selezionata. Assicurarsi inoltre che sia selezionata anche la casella di controllo accanto a Scenes/HLSharedProjectMain, come illustrato nell'immagine seguente.

![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

10. Nella sezione impostazioni di pubblicazione del pannello Inspector scorrere fino a funzionalità e verificare che le caselle di controllo seguenti siano contrassegnate:

![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

11. Importare i pacchetti personalizzati elencati:

    a. [Unity. HoloLens2. GettingStarted. Tutorials. asset. 2.1.0.0. file unitypackage Tools](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.0/Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage)

    b. [Unity. HoloLens2. MultiUserCapabilities. Tutorials. asset. 2.1.0.0. file unitypackage Tools](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.1.0.0/Unity.HoloLens2.MultiUserCapabilities.Tutorials.Asset.2.1.0.0.unitypackage)

    >[!TIP]
    >Se sono state completate le [esercitazioni](mrlearning-base-ch1.md)introduttive, potrebbe essere ancora presente il pacchetto Unity denominato _Unity. HoloLens2. GettingStarted. Tutorials. asset. 2.1.0.0. file unitypackage Tools_ archiviato nel computer. In tal caso, è possibile ignorare il download dell'asset elencato nel passaggio a precedente.

![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

12. Nel pannello progetto passare alla cartella prefabbricates. Nei passaggi seguenti vengono implementati alcuni prefabbricati nella scena. Nella cartella prefabbricati, fare clic e trascinare la finestra prefabbricata, debug nella gerarchia. Al termine, salvare il progetto facendo clic su file, quindi su Salva o premere CTRL + S.

![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

   > Nota: è possibile che venga visualizzato un popup quando si fa clic sulla prefabbricata, in cui viene chiesto di installare TMP Essentials. Fare clic su Importa TMP Essentials in base alle esigenze. Se viene visualizzato questo popup, potrebbe essere necessario eliminare il prefabbricato dalla gerarchia e trascinarlo nella gerarchia per evitare potenziali errori correlati al testo.
   >
>![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a>Lezione completata

Il progetto Unity è ora pronto per Photon. Nelle esercitazioni riportate di seguito verrà creata questa scena e il progetto Unity per un'esperienza condivisa completa.

[Esercitazione successiva: 3. connessione di più utenti](mrlearning-sharing(photon)-ch3.md)


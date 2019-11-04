---
title: Esercitazioni sulle funzionalità multiutente-2. Preparazione di Unity per lo sviluppo
description: Completare questo corso per apprendere come implementare esperienze condivise multiutente all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 5d8194e9a51bdb0ce32f345b4adfbfaf408c5396
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438386"
---
# <a name="2-getting-unity-ready-for-development"></a>2. recupero di Unity pronto per lo sviluppo 


In questa esercitazione si apprenderà come preparare e configurare Unity per lo sviluppo di applicazioni, tra cui importare il Toolkit di realtà mista, configurare le impostazioni di compilazione e preparare la scena.

## <a name="objectives"></a>Obiettivi

- Configurare Unity per lo sviluppo di applicazioni

- Importare Mixed Reality Toolkit

- Preparare la scena del progetto

## <a name="instructions"></a>Istruzioni

1. Scaricare e salvare il pacchetto di Unity del Toolkit di realtà misto facendo clic [qui.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)

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

6. Una volta completato, viene visualizzato un nuovo file di configurazione che consente di scegliere di personalizzare il profilo. Fare clic su copia e Personalizza.

![Module3Chapter2step6ima](images/module3chapter2step6ima.PNG)

![Module3Chapter2step6imb](images/module3chapter2step6imb.PNG)

![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

7. Scorrere verso il basso e deselezionare Abilita sistema di diagnostica se si desidera nascondere la finestra di diagnostica. È consigliabile mantenere la finestra di diagnostica abilitata durante lo sviluppo di applicazioni per monitorare le prestazioni e quindi disabilitarla durante le dimostrazioni di produzione o di applicazioni. 

![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

8. Per aprire le impostazioni di compilazione, premere CTRL + MAIUSC + B o passare a file-> impostazioni di compilazione. Si noti che il programma è attualmente impostato nel computer, Mac e piattaforma autonoma Linux. Per lo sviluppo HoloLens 2, impostare la piattaforma da piattaforma UWP (Universal Windows Platform). Selezionarlo e fare clic su switch Platform.

![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

9. Al termine, fare clic sulla casella denominata Aggiungi scene aperte. Passare ora al pannello Inspector e verificare che la casella di controllo a destra della realtà virtuale supportata (come illustrato nell'immagine seguente) sia selezionata. Assicurarsi inoltre che sia selezionata anche la casella di controllo accanto a Scenes/HLSharedProjectMain, come illustrato nell'immagine seguente.

![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

10. Nella sezione impostazioni di pubblicazione del pannello Inspector scorrere fino a funzionalità e verificare che le caselle di controllo seguenti siano contrassegnate:

![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

11. Importare il pacchetto personalizzato denominato SharingAssetCollection, che può essere scaricato [qui.](https://github.com/microsoft/MixedRealityLearning/releases/tag/development)

![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

12. Nel pannello progetto passare alla cartella prefabbricates. Nei passaggi seguenti vengono implementati alcuni prefabbricati nella scena. Nella cartella prefabbricati, fare clic e trascinare la finestra prefabbricata, debug nella gerarchia. Al termine, salvare il progetto facendo clic su file, quindi su Salva o premere CTRL + S.

![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

   > Nota: è possibile che venga visualizzato un popup quando si fa clic sulla prefabbricata, in cui viene chiesto di installare TMP Essentials. Fare clic su Importa TMP Essentials in base alle esigenze. Se viene visualizzato questo popup, potrebbe essere necessario eliminare il prefabbricato dalla gerarchia e trascinarlo nella gerarchia per evitare potenziali errori correlati al testo.
   >
>![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a>Lezione completata

Il progetto Unity è ora pronto per Photon. Nelle esercitazioni riportate di seguito verrà creata questa scena e il progetto Unity per un'esperienza condivisa completa.

[Esercitazione successiva: 3. connessione di più utenti](mrlearning-sharing(photon)-ch3.md)


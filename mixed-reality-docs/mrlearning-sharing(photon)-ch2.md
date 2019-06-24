---
title: MR Learning condivisione del modulo per HoloLens 2
description: Completare questo corso di informazioni su come implementare esperienze condivise con più utenti all'interno di un'applicazione 2 HoloLens.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 957813d24de95aad52c26b4bd0f0996a60d01358
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326958"
---
# <a name="getting-unity-ready-for-development"></a>**Operazioni preliminari per lo sviluppo di Unity** 

In questa lezione si apprenderà come preparare e configurare Unity per lo sviluppo di app, inclusi l'importazione del Toolkit di realtà mista, configurare le impostazioni di compilazione e preparazione la scena.

Obiettivi:

- Configurare Unity per lo sviluppo di app

- Importare Mixed Reality Toolkit

- Preparare la scena di progetto

### <a name="instructions"></a>Istruzioni

1. Scaricare e salvare il pacchetto unity Toolkit di realtà mista facendo [qui.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC1-Refresh.unitypackage)
2. In Unity, fare clic sul menu di risorse e selezionare "Importa pacchetto", quindi fare clic su "Custom Package".

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. Selezionare il pacchetto Unity che appena scaricato dal collegamento specificato nel passaggio 1. Una volta che viene visualizzata la finestra popup di importazione in Unity, fare clic sul pulsante Importa per avviare l'importazione. L'importazione di MRTK potrebbe richiedere alcuni minuti.

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> Nota: Il pacchetto scaricato sarà nella cartella locale in cui il file è stato salvato. L'immagine precedente non indicano dove si troveranno il pacchetto.

4. Creare una nuova scena (questa operazione può essere eseguita facendo clic su "file" e selezionare "nuova scena"). Salvare la scena come "HLSharedProjectMain."

> Nota: è possibile che venga visualizzato un messaggio popup che ha un aspetto simile all'immagine seguente. Per il momento, fare clic su "No".
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. In fare clic su "Toolkit di realtà mista" su "Aggiungi alla scena e configurare".

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. Una volta completata, un nuovo file di configurazione apparirà, offrendo la possibilità di personalizzare il profilo. Fare clic su "copia e personalizzare".

![Module3Chapter2step6im](images/module3chapter2step6im.PNG)

7. Scorrere verso il basso e deselezionare l'opzione "Abilita sistema di diagnostica", se si vuole nascondere la finestra di diagnostica. È consigliabile mantenere la finestra di diagnostica abilitati durante lo sviluppo di app per monitorare le prestazioni e la sua disabilitazione durante le dimostrazioni di produzione o di applicazione.

![Module3Chapter2step7im](images/module3chapter2step7im.PNG)

8. Aprire le impostazioni di compilazione, premere CTRL + MAIUSC + B o passare al File > Build Settings. Si noti che il programma è attualmente impostato con la piattaforma "PC, Mac e Linux in modo autonomo". Per lo sviluppo di HoloLens 2, impostare la piattaforma sia "Universal Windows Platform." Selezionarlo e fare clic su "switch piattaforma".

   ![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

   9. Al termine, fare clic sulla casella con la dicitura "aggiungere scene Apri". A questo punto passare al pannello di controllo e verificare che la casella di controllo a destra di "realtà virtuale supportati" (come illustrato nell'immagine seguente) è selezionata. Inoltre assicurarsi che sia selezionata anche la casella di controllo accanto a "scene/HLSharedProjectMain", come illustrato nell'immagine seguente.

   ![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

   10. Nella sezione "Impostazioni di pubblicazione" sezione lo scorrimento del Pannello di controllo fino alla "Funzionalità" e verificare che le caselle di controllo seguenti siano contrassegnate:
    - client Internet
       
       - server client Internet
       
       - server dei client di rete privata
   
       - camera/webcam

       - Microfono
   
   11. Importare il pacchetto personalizzato denominato "Della lezione 2", che può essere scaricato qui. TODO: Fornire collegamenti al pacchetto di asset.
   
   ![Module3Chapter2step12im](images/module3chapter2step11im.PNG)
   
   12. A questo punto, nel Pannello di progetto, passare alla cartella "prefabs", poiché in passaggi successivi è necessario implementare alcuni prefabs nella scena. Nella cartella "prefabs", fare clic e trascinare il prefab, "DebugWindow" nella gerarchia. Al termine, salvare il progetto (fare clic sul file, quindi salvare, o premere CTRL + S)
   
       ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)
   
   > Nota: È possibile notare un messaggio popup visualizzato fare clic su di prefab, in cui viene richiesto su Essentials TMP. Perché saranno necessarie, fare clic su "Importa TMP Essentials". Se viene visualizzato questo popup, si potrebbe essere necessario eliminare il prefab dalla gerarchia e trascinare nuovamente all'interno della gerarchia per evitare potenziali errori correlati al testo.
   >
   > ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a>Lezione completata

Il progetto Unity è ora pronto per Photon. Nelle prossime lezioni, viene creata al momento questa scena e il progetto Unity verso un'esperienza completa condiviso.

[Lezione successiva: Sharing(photon) lezione 3](mrlearning-sharing(photon)-ch3.md)


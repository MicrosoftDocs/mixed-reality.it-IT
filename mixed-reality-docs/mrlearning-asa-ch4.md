---
title: Modulo MR Learning ASA-Azure Spatial Anchor su HoloLens 2
description: Completa questo corso per informazioni su come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: b29f27284c352d27fb1d4d4de701a1ebc2a7cd1c
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326932"
---
# <a name="photon-correct-me-if-im-wrong"></a>Photon (Correggi se sbaglio)

In questa lezione, 

Obiettivi

* Scopri come _____________________________________________

* Scopri come _________________________________________________

  

## <a name="instructions"></a>Istruzioni

### <a name="setting-up-photon"></a>Configurazione di Photon

1. Configurare un account [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) . Questa operazione consiste nell'imputare il messaggio di posta elettronica e nell'eseguire alcuni passaggi di verifica.
   

![Module2Chapter4step1im](images/Module2chapter4step1im.png)

2. Dopo aver effettuato l'iscrizione, fare clic su SDK. Una volta visualizzata la pagina, fare clic su "Server" e assicurarsi che "self hosted". Scorrere quindi verso il basso e fare clic su "Server", come illustrato nella seconda immagine riportata di seguito.

   

   ![Module2Chapter2step2aim](images/Module2chapter4step2aim.png)

   ![Module2Chapter2step2bim](images/Module2chapter4step2bim.png)
   
   3. Verrà visualizzata una casella di testo con etichetta "Read me". Procediamo con la lettura. Al termine, fare clic sul collegamento accanto a "downloadSDK" per scaricarlo.


![Module2Chapter4step3im](images/Module2chapter4step3im.png)

4. Al termine del download, fare doppio clic sulla cartella.  Una volta visualizzata la cartella SDK, in Esplora file copiare la cartella SDK.
   
   - Il passaggio successivo consiste nell'accedere all'unità C: di Windows e creare una nuova cartella denominata "Server".
   
   ![Module2Chapter4step4im](images/Module2chapter4step4aim.png)
   
   - Aprire quindi la cartella e incollare la cartella SDK copiata in precedenza.
   
   ![Module2Chapter4step4im](images/Module2chapter4step4bim.png)
   
5. Al termine, aprire la cartella SDK e passare a "deploy" (Distribuisci), quindi a "bin_Win64", quindi fare doppio clic su "PHOTON Control".


![Module2Chapter4step4im](images/Module2chapter4step5im.png)

> Nota: In caso di domande relative all'indirizzo IP o ad altre domande simili, è possibile trovare la maggior parte delle informazioni sulla barra degli strumenti, come illustrato nell'immagine seguente.
>
> ![Module2Chapter4step4im](images/Module2chapter4noteim.png)

6. Ora che il server è stato configurato e avviato, tornare al sito Web di Photon e fare clic sull'icona del profilo (boxed nell'immagine seguente) e selezionare "applicazioni".
   

![Module2Chapter3step5im](images/Module2chapter4step6im.png)

7. Per creare un ID applicazione, fare clic sul pulsante "crea una nuova app".

   ![Module2Chapter3step8im](images/Module2chapter4step7aim.png)

   - Selezionare "Photon RUN" dal menu a discesa in "Photon Type". Assegnare quindi un nome (un elemento da ricordare). In questo esempio è stato denominato "HoloLensPhotonProject". Al termine, fare clic su "Crea".

   ![Module2Chapter3step8im](images/Module2chapter4step7bim.png)

8. Al termine, tornare alla pagina delle applicazioni. verrà visualizzata una schermata simile all'immagine seguente. Fare clic sull'ID app e copiarlo. Incollare è possibile accedere facilmente a.  
   

![Module2Chapter4step9im](images/Module2chapter4step8im.png)

9. Creare un nuovo progetto Unity. Aprire Hub Unity e fare clic su "nuovo". Denominarlo "HLSharingProject". Quindi fare clic su Crea. 

   > Si noti Il caricamento di questa operazione può richiedere fino a 2 minuti, in base alla velocità del computer.

![Module2Chapter4step9im](images/Module2chapter4step9im.png)

> Nota: selezionare una posizione in cui salvare il progetto nel computer modificando l'opzione "percorso". Salvarlo in una posizione che si ricorda e avere accesso facile a.

10. Una volta caricato il progetto, fare clic su "assets Store". Quindi, nella casella di ricerca mostrata nell'immagine seguente digitare "PUN" e selezionare l'asset "Photon PUN-2 FREE". 

    ![Module2Chapter4step10im](images/Module2chapter4step10im.PNG)
    
    11. Scaricare e importare
    
    ![Module2Chapter4step11im](images/Module2chapter4step11im.png)

### <a name="setting-up-the-unity-project"></a>**Configurazione del progetto Unity** 

11. scaricare un nuovo asset necessario per configurare Photon in Unity facendo clic [qui.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)

12. In Unity fare clic sul menu assets e selezionare "Import assets", quindi fare clic su "asset personalizzati".

![Module2Chapter4step12im](images/Module2chapter4step12im.PNG)

13. Selezionare il pacchetto Unity appena scaricato dal collegamento fornito nel passaggio 1. Quando il pulsante Importa viene visualizzato in Unity, fare clic su di esso.

![Module2Chapter4step13im](images/Module2chapter4step13im.png)

> Nota: ogni volta che il pacchetto è stato scaricato in, sarà possibile trovarlo. L'immagine precedente non rappresenta la posizione in cui si troverà il pacchetto.

14. Creare una nuova scena. questa operazione può essere eseguita usando Ctrl/Comando + N oppure facendo clic su "file" e selezionando "nuova scena". Salvare la scena come "HLSharedProjectMain".

> Nota: è possibile che venga visualizzato un popup simile all'immagine seguente. Per il momento, è sufficiente fare clic su "No".
>
> ![Module2Chapter4note2im](images/Module2chapter4note2im.png)

15. In "Mixed Reality Toolkit" fare clic su "Aggiungi a scena e configura".

![Module2Chapter4step15im](images/Module2chapter4step15im.png)

16. Al termine, verrà visualizzato un nuovo file di configurazione che consente di scegliere di personalizzare il profilo. Fare clic su "copia e Personalizza".

![Module2Chapter4step16im](images/Module2chapter4step16im.png)

17. Scorrere verso il basso e deselezionare "Abilita sistema di diagnostica". Questo renderà più semplice configurare questo progetto.

![Module2Chapter4step17im](images/Module2chapter4step17im.png)

18. Aprire le impostazioni di compilazione (CTRL + MAIUSC + B). Si noti che il programma è attualmente impostato nella piattaforma "PC, Mac e Linux standalone". Per questo progetto, impostare la piattaforma su "Universal Windows Platform". Selezionarlo e fare clic su "switch Platform".

![Module2Chapter4step18im](images/Module2chapter4step18im.png)

19. Al termine, fare clic sulla casella "Aggiungi scene aperte". Passare ora al pannello Inspector e verificare che la casella di controllo a destra di "Virtual Reality supported" (come illustrato nell'immagine seguente) sia selezionata. 

![Module2Chapter4step19im](images/Module2chapter4step19im.png)

> Si noti Assicurarsi inoltre che sia selezionata anche la casella di controllo accanto a "Scenes/HLSharedProjectMain".

20. In "impostazioni di pubblicazione" nel pannello Inspector scorrere verso il basso fino a "funzionalità" e verificare che siano contrassegnate solo le caselle di controllo seguenti:

- client Internet
- Server client Internet
- Server client di rete privata
- fotocamera/webcam
- Microfono

21. Analogamente al passaggio 12, il passaggio successivo consiste nell'importare un altro pacchetto personalizzato denominato "della lezione 2" che è possibile scaricare [qui.] [collegamento della lezione 2. file unitypackage Tools Importare il pacchetto.

![Module2Chapter4step21im](images/Module2chapter4step20im.png)

22. A questo punto, nel pannello progetto passare alla cartella "prefabbricates", poiché nei prossimi passaggi verranno implementate alcune prefabbricati nella scena. Nella cartella "prefabbricates" fare clic e trascinare la prefabbricata "DebugWindow" nella gerarchia. Al termine, salvare il progetto (fare clic su file, quindi su Salva o CTRL + S).

![Module2Chapter4step22im](images/Module2chapter4step21im.PNG)

> Si noti È possibile che venga visualizzato un messaggio popup quando si fa clic sul prefabbricato, che richiede informazioni su TMP Essentials. Fare clic su "Importa TMP Essentials" perché saranno necessari.
>
> ![Module2Chapter4note3im](images/Module2chapter4note3im.PNG)

### <a name="connecting-multiple-users"></a>**Connessione di più utenti**

23. Come il passaggio 22, nella cartella "prefabbricates" del pannello del progetto, il passaggio successivo consiste nel trascinare e rilasciare il prefabbricato "NetworkLobby" nella gerarchia. 

![Module2Chapter4step22im](images/Module2chapter4step22im.png)

24. Quando si apre la prefabbricata padre, "NetworkLobby", dovrebbe essere visualizzata una prefabbricata figlio, "NetworkRoom". Selezionando questa opzione, passare al pannello di controllo e fare clic su "Aggiungi componente". Cercare "PhotonView" e aggiungere il componente.

![Module2Chapter4step23im](images/Module2chapter4step23im.png)

25. Creare un nuovo oggetto gioco vuoto nella gerarchia di (fare clic con il pulsante destro del mouse nella gerarchia e selezionare "Empty"). Verificare che il posizionamento sia impostato su x = 0, y = 0, z = 0 e denominare l'oggetto "PhotonUser".

![Module2Chapter4step24im](images/Module2chapter4step24im.png)

## <a name="congratulations"></a>Lezione completata




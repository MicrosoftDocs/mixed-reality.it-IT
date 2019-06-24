---
title: Modulo ASA Learning MR Azure ancoraggio spaziale su HoloLens 2
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
# <a name="photon-correct-me-if-im-wrong"></a>Photon (correggere me se si è errato)

In questa lezione, 

Obiettivi:

* Informazioni su come _

* Informazioni su come _

  

## <a name="instructions"></a>Istruzioni

### <a name="setting-up-photon"></a>Configurazione di Photon

1. Configurare un [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account. In questo modo sarà costituito l'immissione dei messaggio di posta elettronica e in uscita tramite alcuni passaggi di verifica.
   

![Module2Chapter4step1im](images/Module2chapter4step1im.png)

2. Dopo che è stata effettuata l'iscrizione, fare clic su SDK. Una volta in tale pagina, fare clic su "server" e assicurarsi che lo stato, "self-hosted." Scorrere verso il basso e fare clic su "server", come illustrato nell'immagine secondo seguente.

   

   ![Module2Chapter2step2aim](images/Module2chapter4step2aim.png)

   ![Module2Chapter2step2bim](images/Module2chapter4step2bim.png)
   
   3. In tal modo una casella di testo da visualizzare con etichette, "Leggi me." Proseguo e leggerlo. Al termine, fare clic sul collegamento accanto a "downloadSDK" per scaricarlo.


![Module2Chapter4step3im](images/Module2chapter4step3im.png)

4. Fare doppio clic sulla cartella termine di download.  Una volta Esplora file viene aperto rivelando la cartella del SDK, copiare la cartella del SDK.
   
   - Il passaggio successivo, è possibile passare nell'unità c: windows e creare una nuova cartella denominata "server".
   
   ![Module2Chapter4step4im](images/Module2chapter4step4aim.png)
   
   - A questo punto aprire la cartella e incollare la cartella SDK copiato in precedenza.
   
   ![Module2Chapter4step4im](images/Module2chapter4step4bim.png)
   
5. Una volta che viene completato, aprire la cartella SDK e passare a "Distribuisci", quindi "bin_Win64", quindi fare doppio clic su "controllo photon".


![Module2Chapter4step4im](images/Module2chapter4step5im.png)

> Nota: Se hai domande sull'indirizzo IP o eventuali altre domande simili, è possibile trovare la maggior parte delle informazioni sulla barra degli strumenti (come illustrato nell'immagine seguente).
>
> ![Module2Chapter4step4im](images/Module2chapter4noteim.png)

6. Ora che il server è configurato e avviato, tornare al sito Web Photon e fare clic sull'icona del profilo (boxed nell'immagine seguente) e selezionare "applicazioni".
   

![Module2Chapter3step5im](images/Module2chapter4step6im.png)

7. Creare un ID applicazione facendo clic sul pulsante "Crea una nuova app".

   ![Module2Chapter3step8im](images/Module2chapter4step7aim.png)

   - Selezionare "Photon RUN" nel menu a discesa in "tipo photon". Assegnargli un nome, (qualcosa che sarebbe ricordarsi). In questo esempio è denominato "HoloLensPhotonProject." Al termine, fare clic su "Crea".

   ![Module2Chapter3step8im](images/Module2chapter4step7bim.png)

8. Al termine dell'operazione, tornare alla pagina delle applicazioni e verrà visualizzato qualcosa di simile all'immagine seguente. Fare clic sull'ID dell'app e copiarlo. Incolla è in una posizione che facilmente accessibile.  
   

![Module2Chapter4step9im](images/Module2chapter4step8im.png)

9. Creare un nuovo progetto unity. Aprire l'Hub di Unity e fare clic su "nuovo". Denominarla "HLSharingProject." Quindi fare clic su Crea. 

   > Nota: L'operazione può richiedere fino a 2 minuti per caricare, in base alla velocità del computer.

![Module2Chapter4step9im](images/Module2chapter4step9im.png)

> Nota: selezionare una posizione in cui salvare il progetto nel computer modificando l'opzione "location". Salvarlo in una posizione si terrà conto e accedere in modo semplice.

10. Una volta che il progetto viene caricato, fare clic su "asset store". Quindi, nella casella di ricerca illustrata nell'immagine seguente, digitare "Stato" e selezionare l'asset "Photon 2 in poi gratuito". 

    ![Module2Chapter4step10im](images/Module2chapter4step10im.PNG)
    
    11. Scaricare e importare.
    
    ![Module2Chapter4step11im](images/Module2chapter4step11im.png)

### <a name="setting-up-the-unity-project"></a>**Impostazione del progetto Unity** 

11. scaricare un nuovo asset necessari per configurare Photon in Unity facendo [qui.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)

12. In Unity, fare clic sul menu di risorse e selezionare "Importa gli asset", quindi fare clic su "risorse personalizzate".

![Module2Chapter4step12im](images/Module2chapter4step12im.PNG)

13. Selezionare il pacchetto Unity che appena scaricato dal collegamento specificato nel passaggio 1. Una volta che viene visualizzato il pulsante di importazione in Unity, selezionarlo.

![Module2Chapter4step13im](images/Module2chapter4step13im.png)

> Nota: ovunque è stato scaricato il pacchetto sarà dove le trovi. L'immagine precedente non indicano dove si troveranno il pacchetto.

14. Creare una nuova scena (può essere effettuata utilizzando controllo / comando + N o facendo clic su "file" e selezionare "nuova scena."). Salvare la scena come "HLSharedProjectMain."

> Nota: è possibile che venga visualizzato un messaggio popup che ha un aspetto simile all'immagine seguente. Per ora, semplicemente fare clic su "no".
>
> ![Module2Chapter4note2im](images/Module2chapter4note2im.png)

15. In fare clic su "Toolkit di realtà mista" su "Aggiungi alla scena e configurare".

![Module2Chapter4step15im](images/Module2chapter4step15im.png)

16. Una volta completata, un nuovo file di configurazione apparirà, offrendo la possibilità di personalizzare il profilo. Fare clic su "copia e personalizzare".

![Module2Chapter4step16im](images/Module2chapter4step16im.png)

17. Scorrere verso il basso e deselezionare l'opzione "Abilita sistema di diagnostica". Ciò renderà più facile configurare questo progetto.

![Module2Chapter4step17im](images/Module2chapter4step17im.png)

18. Aprire le impostazioni di compilazione (controllo + MAIUSC + B). Si noti che il programma è attualmente impostato con la piattaforma "PC, Mac e Linux in modo autonomo". Per questo progetto, impostare la piattaforma sia "universal windows platform." Selezionarlo e fare clic su "switch piattaforma".

![Module2Chapter4step18im](images/Module2chapter4step18im.png)

19. Al termine, fare clic sulla casella con la dicitura "aggiungere scene Apri". A questo punto passare al pannello di controllo e verificare che la casella di controllo a destra di "realtà virtuale supportati" (come illustrato nell'immagine seguente) è selezionata. 

![Module2Chapter4step19im](images/Module2chapter4step19im.png)

> Nota: Assicurarsi anche che la casella di controllo accanto a "scene/HLSharedProjectMain" sia selezionata anche.

20. In "impostazioni di pubblicazione" nel Pannello di controllo scorrere fino alla "funzionalità" e verificare che siano contrassegnate solo le caselle di controllo seguenti:

- client Internet
- server client Internet
- server dei client di rete privata
- camera/webcam
- Microfono

21. Come passaggio 12, il passaggio successivo, è possibile importare un altro pacchetto personalizzato denominato "Della lezione 2", che può essere scaricato da [qui]. [lesson2.unitypackage inserire qui il collegamento] Importare tale pacchetto.

![Module2Chapter4step21im](images/Module2chapter4step20im.png)

22. A questo punto, nel Pannello di progetto, passare alla cartella "prefabs", poiché in passaggi successivi è necessario implementare alcuni prefabs nella scena. Nella cartella "prefabs", fare clic e trascinare il prefab, "DebugWindow" nella gerarchia. Al termine, salvare il progetto (fare clic su file, quindi di salvare o CTRL + S)

![Module2Chapter4step22im](images/Module2chapter4step21im.PNG)

> Nota: È possibile notare un messaggio popup visualizzato fare clic su di prefab, in cui viene richiesto su Essentials TMP. Perché saranno necessarie, fare clic su "Importa TMP Essentials".
>
> ![Module2Chapter4note3im](images/Module2chapter4note3im.PNG)

### <a name="connecting-multiple-users"></a>**Ci si connette più utenti**

23. Come passaggio 22, nella cartella "prefabs" nel Pannello di progetto, il passaggio successivo è per trascinare e rilasciare il prefab "NetworkLobby" in per la gerarchia. 

![Module2Chapter4step22im](images/Module2chapter4step22im.png)

24. Quando si apre il prefab padre, "NetworkLobby", verrà visualizzato un prefab, elemento figlio "NetworkRoom." Con essa selezionate, passare al pannello di controllo e fare clic su "Aggiungi componente". Cercare "PhotonView" e aggiungere il componente.

![Module2Chapter4step23im](images/Module2chapter4step23im.png)

25. Creare un nuovo oggetto gioco vuoto nella gerarchia di (a destra fare clic nella gerarchia e selezionare "vuota"). Verificare che il posizionamento è impostato su x = 0, y = 0, z = 0 e assegnare il nome dell'oggetto, "PhotonUser."

![Module2Chapter4step24im](images/Module2chapter4step24im.png)

## <a name="congratulations"></a>Lezione completata




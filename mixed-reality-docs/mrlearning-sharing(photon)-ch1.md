---
title: MR Learning condivisione del modulo per HoloLens 2
description: Completare questo corso di informazioni su come implementare esperienze condivise con più utenti all'interno di un'applicazione 2 HoloLens.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 8940de029ef5c67c38f427a238f88fcab527d79d
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327928"
---
# <a name="setting-up-photon"></a>Configurazione di Photon

In questa lezione si apprenderà come prepararsi per la creazione di un'esperienza condivisa tramite l'importazione di Networking Unity Photon (stato) nel progetto Unity. Photon è una delle diverse opzioni di rete disponibili per gli sviluppatori di realtà mista per creare esperienze condivise. Si si apprenderà come creare un account Photon, importare Photon e creare un server locale facoltativo

Obiettivi:

* Informazioni su come creare account Photon

* Informazioni su come individuare e importare Networking Unity Photon

* Configurare un server locale Photon

  

### <a name="setting-up-photon"></a>Configurazione di Photon

1. Configurare un [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account. Passare alla pagina di iscrizione Photon facendo clic su [questo collegamento](https://dashboard.photonengine.com/en-US/Account/SignUp). Seguire le istruzioni nella pagina di iscrizione per creare l'account. 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

2. Dopo che è stata effettuata l'iscrizione, fare clic su SDK. Una volta in tale pagina, fare clic su "server" e assicurarsi che lo stato, "self-hosted." Scorrere verso il basso e fare clic su "server", come illustrato nell'immagine secondo seguente.

   

   ![Module3Chapter1step2aim](images/module3chapter1step2aim.PNG)

   ![Module3Chapter1step2bim](images/module3chapter1step2bim.PNG)
   
   3. In tal modo una casella di testo da visualizzare con etichette, "Leggi me." Proseguo e leggerlo. Al termine, fare clic sul collegamento accanto a "downloadSDK" per scaricarlo.


![Module3Chapter1step3im](images/module3chapter1step3im.PNG)

4. Fare doppio clic sulla cartella termine di download.  Una volta Esplora file viene aperto rivelando la cartella del SDK, copiare la cartella del SDK.
   
   - Il passaggio successivo, è possibile passare nell'unità c: windows e creare una nuova cartella denominata "server".
   
   ![Module3Chapter1step4aim](images/module3chapter1step4aim.PNG)
   
   - A questo punto aprire la cartella e incollare la cartella SDK copiato in precedenza.
   
   ![Module3Chapter1step4bim](images/module3chapter1step4bim.PNG)
   
5. Una volta che viene completato, aprire la cartella SDK e passare a "Distribuisci", quindi "bin_Win64", quindi fare doppio clic su "controllo photon".


![Module3Chapter1step5im](images/module3chapter1step5im.PNG)

> Nota: Se hai domande sull'indirizzo IP o eventuali altre domande simili, è possibile trovare la maggior parte delle informazioni sulla barra degli strumenti (come illustrato nell'immagine seguente).
>
> ![Module3Chapter1noteim](images/module3chapter1noteim.PNG)

6. Ora che il server è configurato e avviato, tornare al sito Web Photon e assicurarsi che è ancora connessi (o accedere nuovamente, se non si.) Fare clic sull'icona del profilo (boxed in alto a destra dell'immagine riportata di seguito) e selezionare "applicazioni".
   

![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

7. Creare un ID applicazione facendo clic sul pulsante "Crea una nuova app".

   ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

   - Selezionare "Photon considerato" nel menu a discesa in "tipo photon". Assegnargli un nome, in questo esempio, è denominato "HoloLensPhotonProject." Al termine, fare clic sul pulsante "Crea".

   ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

8. Al termine dell'operazione, tornare alla pagina delle applicazioni e verrà visualizzato qualcosa di simile all'immagine seguente. Fare clic sull'ID dell'app e copiarlo. Incolla è in una posizione che facilmente accessibile.  
   

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

9. Creare un nuovo progetto unity e denominarla "HLSharingProject." Per istruzioni su come creare un nuovo progetto Unity, consultare [sezione "Creare progetto Unity" del modulo Base](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project). 


10. Una volta che il progetto viene caricato, fare clic sulla scheda "asset store", come illustrato nell'immagine seguente. Quindi, nella casella di ricerca evidenziata nell'immagine seguente, digitare "Stato" e selezionare l'asset "Photon 2 in poi" gratuiti"dai risultati della ricerca. 

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)
    
    11. Scaricare e importare questo asset facendo clic sul pulsante "Download" e "Import".
    
    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

## <a name="congratulations"></a>Lezione completata

Si hanno correttamente creato un account Photon configurare un server Photon locale e importato in poi in Unity. Il passaggio successivo è impostare il progetto e quindi consentire le connessioni con altri utenti in modo che più utenti possono visualizzare il proprio lavoro. 

[Lezione successiva: Sharing(photon) lezione 2](mrlearning-sharing(photon)-ch2.md)


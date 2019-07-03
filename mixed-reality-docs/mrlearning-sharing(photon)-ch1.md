---
title: MR Learning condivisione del modulo per HoloLens 2
description: Completare questo corso di informazioni su come implementare esperienze condivise con più utenti all'interno di un'applicazione 2 HoloLens.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 80cefb36ec1944ec6f537aafcbf4b63f7f812d26
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523296"
---
#  <a name="setting-up-photon-unity-networking"></a>Configurazione di rete di Unity Photon

In questa esercitazione, è informazioni su come prepararsi per la creazione di un'esperienza condivisa tramite l'importazione di Networking Unity Photon (stato) nel progetto Unity. Photon è una delle diverse opzioni di rete disponibili per gli sviluppatori di realtà mista per creare esperienze condivise. Si si apprenderà come creare un account Photon, importare Photon e creare un server locale facoltativo

Obiettivi:

* Informazioni su come creare un account Photon

* Informazioni su come individuare e importare Networking Unity Photon

* Configurare un server locale Photon

  

### <a name="setting-up-photon"></a>Configurazione di Photon

1. Configurare un [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account. Passare alla pagina di iscrizione Photon facendo clic su [questo collegamento](https://dashboard.photonengine.com/en-US/Account/SignUp). Seguire le istruzioni nella pagina di iscrizione per creare l'account. 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)



![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. Creare un ID applicazione, fare clic su Crea un pulsante Nuova App.

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. Selezionare poi Photon nel menu a discesa sotto Photon tipo. Assegnargli un nome. In questo esempio è denominato HoloLensPhotonProject. Al termine, fare clic sul pulsante Crea.

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. Al termine dell'operazione, tornare alla pagina delle applicazioni e verrà visualizzato qualcosa di simile all'immagine seguente. Fare clic sull'ID applicazione e copiarlo. Incolla è in una posizione che facilmente accessibile.  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. Creare un nuovo progetto unity e denominarla HLSharingProject. Per istruzioni su come creare un nuovo progetto Unity, consultare [sezione "Creare progetto Unity" del modulo Base](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project). 

6. Una volta che il progetto viene caricato, fare clic sulla scheda Asset Store, come illustrato nell'immagine seguente. Quindi, nella casella di ricerca evidenziata nell'immagine seguente, digitare in poi e selezionare il 2 in poi Photon - da FRE"asset dai risultati della ricerca. 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. Scaricare e importare questo asset facendo clic sul pulsante Download e importazione.

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. Una volta Photon completato il processo di importazione, verrà visualizzata la procedura guidata in poi. Richiedere l'ID dell'applicazione (che deve essere copiata negli Appunti) nel passaggio 4, incollarlo nella casella di AppID e premere il pulsante di progetto di installazione. 
![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. Dopo aver aggiunto l'AppID, passare a Photon -> PhotonUnityNetworking -> risorse -> PhotonServerSettings negli asset. Selezionare l'opzione utilizza un nome Server e impostare il fisso area Stati Uniti o l'area di servizio yourPphoton.

   ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a>Lezione completata

Si hanno correttamente creato un account Photon configurare un server Photon locale e importato in poi in Unity. Il passaggio successivo è impostare il progetto e quindi consentire le connessioni con altri utenti in modo che più utenti possono visualizzare il proprio lavoro. 

[Esercitazione successiva: Operazioni preliminari per lo sviluppo di Unity](mrlearning-sharing(photon)-ch2.md)


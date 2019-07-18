---
title: Modulo MR Learning sharing per HoloLens 2
description: Completare questo corso per apprendere come implementare esperienze condivise multiutente all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: e40cd50f75ca509c601d215cb865161ea3596565
ms.sourcegitcommit: 611af6ff7a2412abad80c0c7d4decfc0c3a0e8c8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2019
ms.locfileid: "68293648"
---
#  <a name="setting-up-photon-unity-networking"></a>Configurazione della rete di Photon Unity

Questa esercitazione illustra come prepararsi per la creazione di un'esperienza condivisa importando la rete di Photon Unity (PUN) nel progetto Unity. Photon è una delle diverse opzioni di rete disponibili agli sviluppatori di realtà mista per creare esperienze condivise. Si apprenderà come creare un account Photon, importare un fotone e creare un server locale facoltativo

Obiettivi

* Informazioni su come creare un account Photon

* Informazioni su come trovare e importare la rete di Photon Unity

* Configurare un server Photon locale

  

### <a name="setting-up-photon"></a>Configurazione di Photon

1. Configurare un account [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) . Passare alla pagina di iscrizione a Photon facendo clic su [questo collegamento](https://dashboard.photonengine.com/en-US/Account/SignUp). Seguire le istruzioni nella pagina di iscrizione per creare l'account. 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. Creare un ID applicazione facendo clic sul pulsante Crea una nuova app.

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. Selezionare Photon PUN dal menu a discesa in tipo di fotone. Assegnare quindi un nome. In questo esempio, il nome è HoloLensPhotonProject. Al termine, fare clic sul pulsante Crea.

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. Al termine, tornare alla pagina delle applicazioni. verrà visualizzata una schermata simile all'immagine seguente. Fare clic sull'ID applicazione e copiarlo. Incollarlo in un'altra posizione a cui è possibile accedere facilmente.  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. Creare un nuovo progetto Unity e denominarlo HLSharingProject. Per istruzioni su come creare un nuovo progetto Unity, vedere [la sezione "creare un progetto Unity" del modulo di base](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project). 

6. Una volta caricato il progetto, fare clic sulla scheda Archivio risorse, come illustrato nell'immagine seguente. Quindi, nella casella di ricerca evidenziata nell'immagine riportata di seguito, digitare PUN e selezionare l'asset Photon PUN 2-FREE "dai risultati della ricerca. 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. Scaricare e importare questo asset premendo i pulsanti Scarica e importa.

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. Dopo che il fotone ha completato il processo di importazione, viene visualizzata la procedura guidata di pun. Prendere l'ID applicazione, che dovrebbe trovarsi negli Appunti, dal passaggio 4 e incollarlo nella casella AppID e premere il pulsante Imposta progetto. 
![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. Dopo aver aggiunto l'AppID, passare a Photon-> PhotonUnityNetworking-> Resources-> PhotonServerSettings in assets. Selezionare l'opzione Usa il server dei nomi e impostare l'area fissa su US o l'area del servizio Photon.

![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a>Lezione completata

È stato creato un account Photon, configurato un server Photon locale e il PUN è stato importato in Unity. Il passaggio successivo consiste nell'impostare il progetto e quindi consentire le connessioni con altri utenti in modo che più utenti possano visualizzare il lavoro. 

[Esercitazione successiva: Preparazione di Unity per lo sviluppo](mrlearning-sharing(photon)-ch2.md)


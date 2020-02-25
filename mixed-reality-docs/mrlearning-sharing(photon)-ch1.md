---
title: Esercitazioni sulle funzionalità multiutente-1. Configurazione della rete di Photon Unity
description: Completare questo corso per apprendere come implementare esperienze condivise multiutente all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: d879144c7097d8b3873618f986b9f169e8553fa8
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553819"
---
# <a name="1-setting-up-photon-unity-networking"></a>1. configurazione della rete di Photon Unity

## <a name="overview"></a>Panoramica

In questa esercitazione si apprenderà come preparare la creazione di un'esperienza condivisa importando la rete di Photon Unity (PUN) nel progetto Unity. Photon è una delle diverse opzioni di rete disponibili agli sviluppatori di realtà mista per creare esperienze condivise. Si apprenderà come creare un account Photon, importare un fotone e creare un server locale facoltativo

## <a name="objectives"></a>Obiettivi

* Informazioni su come creare un account Photon
* Informazioni su come trovare e importare la rete di Photon Unity
* Configurare un server Photon locale

## <a name="prerequisites"></a>Prerequisiti

>[!TIP]
>Se non sono ancora state completate [le esercitazioni introduttive](mrlearning-base.md) e le [esercitazioni di Azure Spatial Anchor avviate](mrlearning-asa-ch1.md) , è consigliabile completare prima queste esercitazioni.

* Un PC Windows 10 configurato in cui siano [installati gli strumenti](install-the-tools.md) corretti
* Windows 10 SDK 10.0.18362.0 o versioni successive
* Alcune funzionalità di programmazione C# di base
* Un dispositivo HoloLens 2 [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode)

>[!IMPORTANT]
> La versione di Unity consigliata per questa serie di esercitazioni è Unity 2019.2.X. Questa istruzione sostituisce gli eventuali requisiti o suggerimenti relativi alla versione di Unity indicati negli argomenti visualizzabili facendo clic sui collegamenti dei prerequisiti sopra riportati.

## <a name="setting-up-photon"></a>Configurazione di Photon

1. Configurare un account [Photon](https://dashboard.photonengine.com//Account/SignUp) . Passare alla pagina di iscrizione a Photon facendo clic su [questo collegamento](https://dashboard.photonengine.com//Account/SignUp). Seguire le istruzioni nella pagina di iscrizione per creare l'account.

    ![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

    ![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. Creare un ID applicazione facendo clic sul pulsante Crea una nuova app.

    ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. Selezionare Photon PUN dal menu a discesa in tipo di fotone. Assegnare quindi un nome. In questo esempio, il nome è HoloLensPhotonProject. Al termine, fare clic sul pulsante Crea.

    ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. Tornare alla pagina delle applicazioni. verrà visualizzata una schermata simile all'immagine seguente. Fare clic sull'ID applicazione e copiarlo. Incollarlo in un'altra posizione a cui è possibile accedere facilmente.  

    ![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. Creare un nuovo progetto Unity e denominarlo HLSharingProject. Per istruzioni su come creare un nuovo progetto Unity, vedere [la sezione "creare un progetto Unity" del modulo di base](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project). 

6. Una volta caricato il progetto, fare clic sulla scheda Archivio risorse, come illustrato nell'immagine seguente. Quindi, nella casella di ricerca evidenziata nell'immagine riportata di seguito, digitare PUN e selezionare l'asset Photon PUN 2-FREE "dai risultati della ricerca.

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. Scaricare e importare questo asset premendo i pulsanti Scarica e importa.

    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. Dopo che il fotone ha completato il processo di importazione, viene visualizzata la procedura guidata di pun. Prendere l'ID applicazione, che dovrebbe trovarsi negli Appunti, dal passaggio 4, incollarlo nella casella AppID e premere il pulsante Imposta progetto.

    ![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. Dopo aver aggiunto l'AppID, passare a Photon-> PhotonUnityNetworking-> Resources-> PhotonServerSettings in assets. Selezionare l'opzione Usa il server dei nomi e impostare l'area fissa su US o l'area del servizio Photon.

    ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a>Complimenti

È stato creato un account Photon, configurato un server Photon locale e il PUN è stato importato in Unity. Il passaggio successivo consiste nell'impostare il progetto e consentire le connessioni con altri utenti in modo che più utenti possano visualizzare il lavoro.

[Esercitazione successiva: 2. preparazione di Unity per lo sviluppo](mrlearning-sharing(photon)-ch2.md)

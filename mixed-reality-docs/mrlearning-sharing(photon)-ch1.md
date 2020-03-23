---
title: Esercitazioni sulle funzionalità multiutente - 1. Configurazione di Photon Unity Networking
description: Completa questo corso per imparare a implementare esperienze condivise multiutente all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: 94068ff706e0e56ca8ec0f23beaed3a34159b777
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031334"
---
# <a name="1-setting-up-photon-unity-networking"></a>1. Configurazione di Photon Unity Networking

## <a name="overview"></a>Panoramica

In questa esercitazione imparerai a prepararti per la creazione di un'esperienza condivisa tramite l'importazione di Photon Unity Networking (PUN) nel tuo progetto Unity. Photon è una delle diverse opzioni di rete disponibili per gli sviluppatori di Realtà mista per creare esperienze condivise. Imparerai a creare un account Photon, importare Photon e creare un server locale facoltativo.

## <a name="objectives"></a>Obiettivi

* Imparare a creare un account Photon
* Sapere come trovare e importare Photon Unity Networking
* Configurare un server Photon locale

## <a name="prerequisites"></a>Prerequisiti

>[!TIP]
>Se non hai ancora completato le serie di [Esercitazioni introduttive](mrlearning-base.md) ed [Esercitazioni introduttive ad Ancoraggi nello spazio di Azure](mrlearning-asa-ch1.md), è consigliabile completare prima queste esercitazioni.

* Un PC Windows 10 configurato in cui siano [installati gli strumenti](install-the-tools.md) corretti
* Windows 10 SDK 10.0.18362.0 o versioni successive
* Alcune funzionalità di programmazione C# di base
* Un dispositivo HoloLens 2 [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode)

>[!IMPORTANT]
> La versione di Unity consigliata per questa serie di esercitazioni è Unity 2019.2.X. Questa istruzione sostituisce gli eventuali requisiti o suggerimenti relativi alla versione di Unity indicati negli argomenti visualizzabili facendo clic sui collegamenti dei prerequisiti sopra riportati.

## <a name="setting-up-photon"></a>Configurazione di Photon

1. Configura un account [Photon](https://dashboard.photonengine.com//Account/SignUp). Passa alla pagina dell'iscrizione a Photon facendo clic su [questo collegamento](https://dashboard.photonengine.com//Account/SignUp). Segui le istruzioni visualizzate nella pagina dell'iscrizione per creare l'account.

    ![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

    ![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. Crea un ID applicazione facendo clic sul pulsante Create a New App (Crea una nuova app).

    ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. Seleziona Photon PUN dal menu a discesa in Photon Type (Tipo Photon). Assegna quindi un nome al tipo. In questo esempio il nome assegnato è HoloLensPhotonProject. Al termine, fai clic sul pulsante Create (Crea).

    ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. Torna alla pagina delle tue applicazioni. Verrà visualizzata una schermata simile all'immagine seguente. Fai clic sull'ID applicazione e copialo. Incollalo in una posizione a cui puoi accedere facilmente.  

    ![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. Crea un nuovo progetto Unity con il nome HLSharingProject. Per istruzioni su come creare un nuovo progetto Unity, vedi [la sezione "Crea un nuovo progetto Unity" del modulo di base](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project). 

6. Dopo aver caricato il progetto, fai clic sulla scheda Assets Store (Archivio asset), come illustrato nell'immagine seguente. Nella casella di ricerca evidenziata nell'immagine seguente digita quindi PUN e seleziona l'asset "Photon PUN 2 - FREE" (Photon PUN 2 - GRATUITO) dai risultati della ricerca.

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. Scarica e importa questo asset premendo i pulsanti Download (Scarica) e Import (Importa).

    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. Dopo che Photon ha completato il processo di importazione, viene visualizzato Pun Wizard (Configurazione guidata PUN). Prendi l'ID applicazione, che deve trovarsi negli Appunti, nel passaggio 4, incollalo nella casella AppID e premi il pulsante Setup Project (Configura progetto).

    ![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. Dopo aver aggiunto AppID, passa a Photon-> PhotonUnityNetworking-> Resources-> PhotonServerSettings (Photon-> PhotonUnityNetworking-> Risorse-> ImpostazioniServerPhoton) in Assets (Asset). Seleziona l'opzione Use Name Server (Usa server dei nomi) e imposta l'area geografica fissa su US (Stati Uniti) o sull'area geografica del servizio Photon.

    ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a>Lezione completata

Hai creato un account Photon, configurato un server Photon locale e importato PUN in Unity. Il passaggio successivo consiste nel configurare il progetto e consentire connessioni con altri utenti, in modo che più utenti possano visualizzare il lavoro che hai svolto.

[Esercitazione successiva: 2. Preparazione di Unity per lo sviluppo](mrlearning-sharing(photon)-ch2.md)

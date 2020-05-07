---
title: Esercitazioni sulle funzionalità multiutente - 4. Condivisione dei movimenti di oggetti con più utenti
description: Completa questo corso per imparare a implementare esperienze condivise multiutente all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: 41b62eb2d9f400d0af341c9fcce887c72af7a3aa
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610645"
---
# <a name="3-sharing-object-movements-with-multiple-users"></a>3. Condivisione dei movimenti di oggetti con più utenti

In questa esercitazione imparerai a condividere i movimenti degli oggetti in modo che tutti i partecipanti di un'esperienza condivisa possano collaborare e visualizzare le interazioni reciproche.

## <a name="objectives"></a>Obiettivi

* Configurare il progetto per condividere i movimenti degli oggetti
* Imparare a creare un'applicazione collaborativa multiutente di base

## <a name="preparing-the-scene"></a>Preparazione della scena

In questa sezione preparerai la scena aggiungendo il prefab dell'esercitazione.

Nella finestra Project (Progetto) passa alla cartella **Assets** (Asset) > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** (Prefab) e trascina il prefab **TableAnchor** nella parte superiore dell'oggetto **SharedPlayground** nella finestra Hierarchy (Gerarchia) per aggiungerlo alla scena come elemento figlio dell'oggetto SharedPlayground:

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial3-section1-step1-1.png)

## <a name="configuring-pun-to-instantiate-the-objects"></a>Configurazione di PUN per creare un'istanza degli oggetti

In questa sezione configurerai il progetto per l'uso del prefab RocketLauncher_Complete_Variant creato nella sezione precedente e definirai la posizione in cui verrà creata l'istanza.

Nella finestra Project (Progetto) passa alla cartella **Assets** (Asset) > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** (Risorse).

Nella finestra Hierarchy (Gerarchia) espandi l'oggetto **NetworkLobby** e seleziona l'oggetto figlio **NetworkRoom** e quindi nella finestra Inspector (Controllo) individua il componente **Photon Room (Script)** (Stanza Photon - Script) e configuralo nel modo seguente:

* Al campo **Photon User Prefab** (Prefab utente Photon) assegna il prefab **PhotonUser** dalla cartella Resources (Risorse)

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial3-section2-step1-1.png)

Con l'oggetto figlio **NetworkRoom** ancora selezionato, nella finestra Hierarchy (Gerarchia) espandi l'oggetto **TableAnchor** e quindi nella finestra Inspector (Controllo) individua il componente **Photon Room (Script)** (Stanza Photon - Script) e configuralo nel modo seguente:

* Al campo **Rocket Launcher Location** (Posizione lanciamissili) assegna l'oggetto figlio **Table** dalla finestra Hierarchy (Gerarchia)

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial3-section2-step1-2.png)

## <a name="trying-the-experience-with-shared-object-movement"></a>Prova dell'esperienza con il movimento di un oggetto condiviso

Se ora compili e distribuisci il progetto Unity in HoloLens e quindi, tornando in Unity, premi il pulsante Play per attivare la modalità di gioco mentre l'applicazione è in esecuzione in HoloLens, vedrai l'oggetto muoversi in Unity quando lo muovi in HoloLens:

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial3-section3-step1-1.gif)

## <a name="congratulations"></a>Lezione completata

Hai configurato il progetto in modo che i movimenti degli oggetti siano sincronizzati e gli utenti possano vedere gli oggetti muoversi quando vengono mossi da altri utenti. Nella prossima esercitazione implementerai le funzionalità in modo che l'esperienza condivisa sia allineata nel mondo fisico, gli utenti possano vedersi nella rispettiva posizione fisica effettiva e quindi gli oggetti vengano visualizzati nella stessa posizione fisica e con la medesima rotazione per tutti gli utenti.

[Esercitazione successiva: 4. Integrazione di Ancoraggi nello spazio di Azure in un'esperienza condivisa](mrlearning-sharing(photon)-ch4.md)

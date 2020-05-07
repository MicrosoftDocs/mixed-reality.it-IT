---
title: Esercitazioni sulle funzionalità multiutente - 3. Connessione di più utenti
description: Completa questo corso per imparare a implementare esperienze condivise multiutente all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: a597aadbddb49fefc824d8c5b5193585fa9476a5
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610912"
---
# <a name="2-connecting-multiple-users"></a>2. Connessione di più utenti

In questa esercitazione imparerai a connettere più utenti all'interno di un'esperienza live condivisa. Al termine dell'esercitazione sarai in grado di eseguire l'applicazione in più dispositivi e fare in modo che ogni utente veda che l'avatar degli altri utenti muoversi in tempo reale.

## <a name="objectives"></a>Obiettivi

* Imparare a connettere più utenti in un'esperienza condivisa

## <a name="preparing-the-scene"></a>Preparazione della scena

In questa sezione preparerai la scena aggiungendo alcuni dei prefab dell'esercitazione.

Nella finestra Project (Progetto) passa alla cartella **Assets** (Asset) > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** (Prefab). Tenendo premuto il pulsante CTRL, fai clic su **DebugWindow**, **NetworkLobby** e **SharedPlayground** per selezionare i tre prefab:

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial2-section1-step1-1.png)

Trascina i tre prefab ancora selezionati nella finestra Hierarchy (Gerarchia) per aggiungerli alla scena:

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial2-section1-step1-2.png)

## <a name="creating-the-user-prefab"></a>Creazione del prefab dell'utente

In questa sezione creerai un prefab che verrà usato per rappresentare gli utenti nell'esperienza condivisa.

### <a name="1-create-and-configure-the-user"></a>1. Creare e configurare l'utente

Nella finestra Hierarchy (Gerarchia) fai clic con il pulsante destro del mouse su un'area vuota e seleziona **Create Empty** (Crea vuoto) per aggiungere alla scena un oggetto vuoto, assegna all'oggetto il nome **PhotonUser** e configuralo nel modo seguente:

* Verifica che il campo **Position** (Posizione) della trasformazione sia impostato su X = 0, Y = 0, Z = 0:

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial2-section2-step1-1.png)

Con l'oggetto **PhotonUser** ancora selezionato, nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Photon User (Script)** (Utente Photon - Script) all'oggetto PhotonUser:

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial2-section2-step1-2.png)

Nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Generic Net Sync (Script)** (Sincronizzazione rete generica - Script) all'oggetto PhotonUser e configura l'oggetto nel modo seguente:

* Seleziona la casella di controllo **Is User** (È utente)

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial2-section2-step1-3.png)

Nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Photon View (Script)** (Visualizzazione Photon - Script) all'oggetto PhotonUser e configura l'oggetto nel modo seguente:

* Al campo **Observed Components** (Componenti osservati) assegna il componente Generic Net Sync (Script) (Sincronizzazione rete generica - Script)

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial2-section2-step1-4.png)

### <a name="2-create-the-avatar"></a>2. Creare l'avatar

Nella finestra Hierarchy (Gerarchia) fai clic con il pulsante destro del mouse sull'oggetto **PhotonUser** e seleziona **3D Object** (Oggetto 3D) > **Sphere** per creare un oggetto sfera come elemento figlio dell'oggetto PhotonUser e configuralo nel modo seguente:

* Verifica che il campo **Position** (Posizione) della trasformazione sia impostato su X = 0, Y = 0, Z = 0
* Imposta il campo **Scale** (Ridimensiona) della trasformazione su una dimensione appropriata, ad esempio X = 0.15, Y = 0.15, Z = 0.15

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial2-section2-step2-1.png)

### <a name="3-create-the-prefab"></a>3. Creare il prefab

Nella finestra Project (Progetto) passa alla cartella **Assets** (Asset) > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** (Risorse):

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial2-section2-step3-1.png)

Con la cartella Resources (Risorse) ancora selezionata, **fai clic e trascina** l'oggetto **PhotonUser** dalla finestra Hierarchy (Gerarchia) nella cartella **Resources** (Risorse) per convertire l'oggetto PhotonUser in un prefab:

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial2-section2-step3-2.png)

Nella finestra Hierarchy (Gerarchia) fai clic con il pulsante destro del mouse sull'oggetto **PhotonUser** e seleziona **Delete** (Elimina) per rimuovere l'oggetto dalla scena:

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial2-section2-step3-3.png)

## <a name="configuring-pun-to-instantiate-the-user-prefab"></a>Configurazione di PUN per creare un'istanza del prefab dell'utente

In questa sezione configurerai il progetto per l'uso del prefab PhotonUser creato nella sezione precedente.

Nella finestra Project (Progetto) passa alla cartella **Assets** (Asset) > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** (Risorse).

Nella finestra Hierarchy (Gerarchia) espandi l'oggetto **NetworkLobby** e seleziona l'oggetto figlio **NetworkRoom** e quindi nella finestra Inspector (Controllo) individua il componente **Photon Room (Script)** (Stanza Photon - Script) e configuralo nel modo seguente:

* Al campo **Photon User Prefab** (Prefab utente Photon) assegna il prefab **PhotonUser** dalla cartella Resources (Risorse)

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial2-section3-step1-1.png)

## <a name="trying-the-experience-with-multiple-users"></a>Prova dell'esperienza con più utenti

Se ora compili e distribuisci il progetto Unity in HoloLens e quindi, tornando in Unity, premi il pulsante Play per attivare la modalità di gioco mentre l'applicazione è in esecuzione in HoloLens, vedrai l'avatar dell'utente HoloLens muoversi quando muovi la testa (HoloLens):

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial2-section4-step1-1.gif)

> [!TIP]
> Per un promemoria su come compilare e distribuire il progetto Unity in HoloLens 2, puoi fare riferimento alle istruzioni riportate in [Compilare l'applicazione nel dispositivo](mrlearning-base-ch1.md#build-your-application-to-your-device).

> [!CAUTION]
> Poiché l'applicazione deve connettersi a Photon, assicurati che il computer o il dispositivo sia connesso a Internet.

## <a name="congratulations"></a>Lezione completata

Hai configurato il progetto per consentire a più utenti di connettersi alla stessa esperienza e vedere i movimenti gli uni degli altri. Nella prossima esercitazione implementerai le funzionalità in modo che anche i movimenti degli oggetti vengano condivisi tra più dispositivi.

[Esercitazione successiva: 2. Condivisione dei movimenti di oggetti con più utenti](mrlearning-sharing(photon)-ch3.md)

---
title: Esercitazioni sulle funzionalità multiutente - 3. Connessione di più utenti
description: Completa questo corso per imparare a implementare esperienze condivise multiutente all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: 56bd4e251d11e39d5495d3fcaf4e3c5fc4e087de
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/14/2020
ms.locfileid: "86305776"
---
# <a name="3-connecting-multiple-users"></a>3. Connessione di più utenti

In questa esercitazione imparerai a connettere più utenti all'interno di un'esperienza live condivisa. Al termine dell'esercitazione sarà possibile eseguire l'app in più dispositivi e fare in modo che ogni utente visualizzi l'avatar degli altri utenti muoversi in tempo reale.

## <a name="objectives"></a>Obiettivi

* Imparare a connettere più utenti in un'esperienza condivisa

## <a name="preparing-the-scene"></a>Preparazione della scena

In questa sezione preparerai la scena aggiungendo alcuni dei prefab dell'esercitazione.

Nella finestra Project (Progetto) passare alla cartella **Assets**  (Asset)  > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** (Prefab) e quindi fare clic e trascinare i prefab seguenti sulla finestra Hierarchy (Gerarchia) per aggiungerli alla scena:

* Prefab **NetworkLobby**
* Prefab **SharedPlayground**

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section1-step1-1.png)

Nella finestra Project (Progetto) passare alla cartella **Assets** (Asset)  > **MRTK.Tutorials.AzureSpeechServices** > **Prefabs** (Prefab) e quindi fare clic e trascinare il prefab seguente sulla finestra Hierarchy (Gerarchia) per aggiungerlo alla scena:

* Prefab **DebugWindow**

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section1-step1-2.png)

## <a name="creating-the-user-prefab"></a>Creazione del prefab dell'utente

In questa sezione creerai un prefab che verrà usato per rappresentare gli utenti nell'esperienza condivisa.

### <a name="1-create-and-configure-the-user"></a>1. Creare e configurare l'utente

Nella finestra Hierarchy (Gerarchia) fai clic con il pulsante destro del mouse su un'area vuota e seleziona **Create Empty** (Crea vuoto) per aggiungere alla scena un oggetto vuoto, assegna all'oggetto il nome **PhotonUser** e configuralo nel modo seguente:

* Verifica che il campo **Position** (Posizione) della trasformazione sia impostato su X = 0, Y = 0, Z = 0:

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-1.png)

Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **PhotonUser** e quindi nella finestra Inspector (Controllo) usare il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Photon User (Script)** (Utente Photon - Script) all'oggetto PhotonUser:

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-2.png)

Nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Generic Net Sync (Script)** (Sincronizzazione rete generica - Script) all'oggetto PhotonUser e configura l'oggetto nel modo seguente:

* Seleziona la casella di controllo **Is User** (È utente)

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-3.png)

Nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Photon View (Script)** (Visualizzazione Photon - Script) all'oggetto PhotonUser e configura l'oggetto nel modo seguente:

* Al campo **Observed Components** (Componenti osservati) assegnare il componente **Generic Net Sync (Script)** (Sincronizzazione rete generica - Script)

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-4.png)

### <a name="2-create-the-avatar"></a>2. Creare l'avatar

Nella finestra Project (Progetto) passare alla cartella **Assets** (Asset)  > **MRTK** > **SDK** > **StandardAssets** > **Materials** (Materiali) per individuare i materiali di MRTK.

Nella finestra Hierarchy (Gerarchia) fare quindi clic con il pulsante destro del mouse sull'oggetto **PhotonUser** e selezionare **3D Object** > **Sphere** (Oggetto 3D > Sfera) per creare un oggetto sfera come elemento figlio dell'oggetto PhotonUser e configuralo nel modo seguente:

* Verifica che il campo **Position** (Posizione) della trasformazione sia impostato su X = 0, Y = 0, Z = 0
* Imposta il campo **Scale** (Ridimensiona) della trasformazione su una dimensione appropriata, ad esempio X = 0.15, Y = 0.15, Z = 0.15
* Al campo MeshRenderer > Materials > **Element 0** (Materiali > Elemento 0) assegnare il materiale **MRTK_Standard_White**

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step2-1.png)

### <a name="3-create-the-prefab"></a>3. Creare il prefab

Nella finestra Project (Progetto) passa alla cartella **Assets** (Asset) > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** (Risorse):

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step3-1.png)

Con la cartella Resources (Risorse) ancora selezionata, **fai clic e trascina** l'oggetto **PhotonUser** dalla finestra Hierarchy (Gerarchia) nella cartella **Resources** (Risorse) per convertire l'oggetto PhotonUser in un prefab:

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step3-2.png)

Nella finestra Hierarchy (Gerarchia) fai clic con il pulsante destro del mouse sull'oggetto **PhotonUser** e seleziona **Delete** (Elimina) per rimuovere l'oggetto dalla scena:

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step3-3.png)

## <a name="configuring-pun-to-instantiate-the-user-prefab"></a>Configurazione di PUN per creare un'istanza del prefab dell'utente

In questa sezione configurerai il progetto per l'uso del prefab PhotonUser creato nella sezione precedente.

Nella finestra Project (Progetto) passa alla cartella **Assets** (Asset) > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** (Risorse).

Nella finestra Hierarchy (Gerarchia) espandi l'oggetto **NetworkLobby** e seleziona l'oggetto figlio **NetworkRoom** e quindi nella finestra Inspector (Controllo) individua il componente **Photon Room (Script)** (Stanza Photon - Script) e configuralo nel modo seguente:

* Al campo **Photon User Prefab** (Prefab utente Photon) assegna il prefab **PhotonUser** dalla cartella Resources (Risorse)

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section3-step1-1.png)

## <a name="trying-the-experience-with-multiple-users"></a>Prova dell'esperienza con più utenti

Se si compila e distribuisce il progetto Unity in HoloLens e quindi, tornando in Unity, si attiva la modalità di gioco mentre l'app è in esecuzione in HoloLens, si visualizzerà l'avatar dell'utente HoloLens muoversi quando si muove la testa (HoloLens):

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section4-step1-1.gif)

> [!TIP]
> Per rivedere la procedura di compilazione e distribuzione di un progetto Unity in HoloLens 2, fare riferimento alle istruzioni riportate in [Compilazione dell'app nel dispositivo HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

> [!CAUTION]
> Poiché l'app deve connettersi a Photon, assicurarsi che il computer o il dispositivo sia connesso a Internet.

## <a name="congratulations"></a>Lezione completata

Hai configurato il progetto per consentire a più utenti di connettersi alla stessa esperienza e vedere i movimenti gli uni degli altri. Nella prossima esercitazione implementerai le funzionalità in modo che anche i movimenti degli oggetti vengano condivisi tra più dispositivi.

[Esercitazione successiva: 4. Condivisione dei movimenti di oggetti con più utenti](mr-learning-sharing-04.md)

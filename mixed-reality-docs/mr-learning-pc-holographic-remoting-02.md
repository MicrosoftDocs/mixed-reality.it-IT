---
title: Esercitazioni su Holographic Remoting per PC - 2 Creare un'applicazione Holographic Remoting per PC
description: Completare questo corso per apprendere come usare in remoto l'esperienza di realtà mista da PC a HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 05/19/2020
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: 32fccbaf6bae8031572ff716f3c9fc26a43849e5
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/14/2020
ms.locfileid: "86305468"
---
# <a name="2-creating-a-holographic-remoting-pc-application"></a>2. Creazione di un'applicazione Holographic Remoting per PC

In questa esercitazione si apprenderà come creare un'app Holographic Remoting per PC e connettere HoloLens 2 in qualsiasi momento, offrendo un modo per visualizzare il contenuto 3D in realtà mista.

## <a name="objectives"></a>Obiettivi

* Configurare Unity per Holographic Remoting
* Imparare a compilare e distribuire l'applicazione con Visual Studio
* Sviluppare un'applicazione Holographic Remoting e connetterla a HoloLens

## <a name="configuring-your-scene-for-holographic-remoting"></a>Configurazione della scena per Holographic Remoting

In questa sezione si configurerà il progetto in modo da trasmettere l'esperienza di realtà mista al dispositivo HoloLens 2 dal PC in tempo reale tramite una connessione Wi-Fi.

Nella finestra Project (Progetto) passare alla cartella **Assets** (Asset)  > **MRTK.Tutorials.PCHolograhicRemoting** > **Prefabs** (Prefab) e selezionare e trascinare il prefab **HolographicRemoting** nella scena.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section1-Step1-1.png)

## <a name="build-your-application-to-pc"></a>Compilare l'applicazione nel PC

L'app Holographic Remoting è ora pronta per la compilazione nel PC. Attenersi ai passaggi seguenti e apportare queste modifiche per compilare l'applicazione nel PC.

### <a name="1-set-the-player-settings"></a>1. Configurare le impostazioni del lettore

Nel menu di Unity scegliere Edit (Modifica) > Project Settings (Impostazioni del progetto) per visualizzare la finestra Player Settings (Impostazioni lettore).

Nella sezione **XR Settings** (Impostazioni XR) selezionare la casella di controllo **WSA Holographic Remoting Supported** e abilitare Holographic Remoting.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step1-1.png)

### <a name="2-build-the-unity-project"></a>2. Compilare il progetto Unity

Dal menu di Unity scegliere File > Build Settings (Impostazioni di compilazione) per visualizzare la finestra corrispondente.

Nella finestra Build Settings (Impostazioni di compilazione) fare clic sul pulsante ***Add Open Scenes*** (Aggiungi scene aperte) per aggiungere la scena corrente alle scene. Nell'elenco Build (Compilazione) fare clic sul pulsante ***Build*** (Compila) per aprire la finestra Build Universal Windows Platform (Compilazione UWP):

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-1.png)

Nella finestra Build Universal Windows Platform (Compilazione UWP) scegliere un percorso adatto per archiviare la compilazione, ad esempio Documenti\MixedRealityLearning. Creare una nuova cartella e assegnarle un nome appropriato, ad esempio PCHolographicRemoting. Fare quindi clic sul pulsante ***Select Folder*** (Seleziona cartella) per avviare il processo di compilazione:

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-2.png)

Attendere che Unity completi il processo di compilazione.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-3.png)

### <a name="3-build-and-deploy-the-application"></a>3. Compilare e distribuire l'applicazione

Al termine del processo di compilazione, Unity richiederà a Esplora file di Windows di aprire il percorso in cui è stata archiviata la compilazione. Spostarsi all'interno della cartella e fare doppio clic sul file con estensione sln per aprirlo in Visual Studio:

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-1.png)

> [!NOTE]
> Se Visual Studio chiede di installare nuovi componenti, dedicare qualche minuto a verificare che siano installati tutti i componenti indispensabili, come specificato nell'argomento Installare gli strumenti.

Configurare Visual Studio per PC selezionando la configurazione Release, l'architettura x64 e Local Machine (Computer locale) come destinazione:

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-2.png)

Fare clic sul pulsante ***Local Machine*** (Computer locale). Viene avviata la compilazione e la distribuzione dell'applicazione nel PC. L'applicazione verrà installata nel PC per impostazione predefinita.

## <a name="testing-holographic-remoting-remote-application"></a>Test di un'applicazione remota Holographic Remoting

Per connettere l'applicazione PC a HoloLens 2, seguire questa procedura:

### <a name="1-install-the-remoting-player-application-on-hololens-2-device"></a>1. Installare l'applicazione Remoting Player nel dispositivo HoloLens 2

* In HoloLens 2 visitare l'app dello Store e cercare "**Remoting Player**".
* Selezionare l'app **Remoting Player**.
* Toccare **Install** (Installa) per scaricare e installare l'app.

### <a name="2-connect-the-holographic-remoting-pc-app-to-the-remoting-player"></a>2. Connettere l'app del PC Holographic Remoting a Remoting Player

* Avviare **Remoting Player** in HoloLens.
* Prendere nota dell'**indirizzo IP** di HoloLens. Verrà visualizzato come ologramma da **Remoting Player** non appena viene avviato.
* Aprire l'applicazione Holographic Remoting per PC nel PC in uso.
* Una volta avviata l'applicazione, immettere l'**indirizzo IP** e fare clic sul pulsante **Connect** (Connetti) per connettersi.

## <a name="congratulations"></a>Lezione completata

In questa esercitazione si è appreso come creare un'app remota Holographic Remoting e connetterla a HoloLens 2 in qualsiasi momento, offrendo un modo per visualizzare il contenuto 3D in realtà mista. Dopo aver connesso HoloLens all'applicazione PC Holographic Remoting, si noterà che l'esperienza di realtà mista è in streaming nel dispositivo HoloLens 2.

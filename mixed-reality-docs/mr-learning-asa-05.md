---
title: Esercitazioni su Ancoraggi nello spazio di Azure - 5. Ancoraggi nello spazio di Azure per Android e iOS
description: Completare questo corso per imparare a distribuire un progetto Unity con Mixed Reality Toolkit e Ancoraggi nello spazio di Azure in Android e iOS.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, android, ios
ms.localizationpriority: high
ms.openlocfilehash: 8c63204948b3e4aa3d25e5b2ca948798726f0838
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376543"
---
# <a name="5-azure-spatial-anchors-for-android-and-ios"></a>5. Ancoraggi nello spazio di Azure per Android e iOS

Questa esercitazione illustra come compilare il progetto nei dispositivi Android e iOS usando AR Foundation, ARCore XR Plugin e ARKit XR Plugin.

## <a name="objectives"></a>Obiettivi

* Imparare a compilare il progetto in un dispositivo Android usando Unity AR Foundation e ARCore XR Plugin
* Imparare a compilare il progetto in un dispositivo iOS usando Unity AR Foundation e ARKit XR Plugin

## <a name="installing-inbuilt-unity-packages"></a>Installazione di pacchetti di Unity incorporati

In questa sezione verrà eseguito l'aggiornamento e l'installazione dei seguenti pacchetti incorporati:

* AR Foundation 3.1.3
* Legacy Input Helpers 2.1.4
* ARCore XR Plugin 3.1.3 per il supporto Android
* ARKit XR plugin 3.1.3 per il supporto iOS

> [!CAUTION]
> Non tutte le versioni sono compatibili con MRTK e solo alcune versioni interagiscono tra loro, quindi è importante assicurarsi di installare le versioni esatte elencate sopra.

Scegliere **Window** (Finestra)  > **Package Manager** (Gestione pacchetti) dal menu Unity per aprire la finestra Package Manager(Gestione pacchetti), quindi selezionare **AR Foundation** > **3.1.3** e fare clic sul pulsante **Update to 3.1.3** (Aggiorna a 3.1.3) per aggiornare il pacchetto:

![mr-learning-asa](images/mr-learning-asa/asa-05-section1-step1-1.png)

Seguire lo stesso processo per importare i pacchetti rimanenti, in base alle esigenze.

> [!NOTE]
> Se sviluppi il progetto per Android, non è necessario installare il pacchetto ARKit XR Plugin. Analogamente, se sviluppi il progetto per iOS, non è necessario installare ARCore XR Plugin.

## <a name="configure-mrtk-for-ar-foundation-camera"></a>Configurare MRTK per AR Foundation Camera

In questa sezione verrà illustrato come configurare MRTK per la distribuzione in un dispositivo mobile.

Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **MixedRealityToolkit**. Quindi, nella finestra Inspector (Controllo) selezionare la scheda **Camera** (Fotocamera), clonare i profilo della fotocamera e assegnare un nome adatto, ad esempio **AzureSpatialAnchors_ARCameraProfile**:

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-1.png)

> [!TIP]
> Per rivedere la procedura di clonazione dei profili MRTK, fare riferimento alle istruzioni contenute in [Configurazione dei profili di Mixed Reality Toolkit](mr-learning-base-03.md).

Con la scheda **Camera** (Fotocamera) ancora selezionata nella finestra Inspector (Controllo), espandere **Camera Setting Providers** (Provider impostazioni fotocamera) e fare clic sul pulsante **+ Add Camera Setting Provider** (+ Aggiungi provider impostazioni fotocamera), quindi espandere **New data provider 1** (Nuovo provider di dati 1):

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-2.png)

Usando l'elenco a discesa **Type** (Tipo), cambiare il tipo in **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > **UnityARCameraSettings**:

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-3.png)

Con l'oggetto **MixedRealityToolkit** ancora selezionato nella finestra Hierarchy (Gerarchia), usare il pulsante **Add Component** (Aggiungi componente) nella finestra Inspector (Controllo) per aggiungere i componenti seguenti:

* AR Anchor Manager (Script)
* DisableDiagnosticsSystem (Script)

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-4.png)

> [!NOTE]
> Quando si aggiunge il componente AR Reference Point Manager (Script), viene aggiunto automaticamente il componente AR Session Origin (Script) perché è richiesto dal componente AR Reference Point Manager (Script).

## <a name="building-your-application-to-your-android-device"></a>Compilazione dell'applicazione in un dispositivo Android

In questa sezione verrà illustrato come configurare il progetto per la compilazione e la distribuzione in un dispositivo Android.

Dal menu di Unity scegli **File** > **Build Settings** (Impostazioni di compilazione) per visualizzare la finestra corrispondente, quindi impostare la piattaforma su Android:

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-1.png)

> [!TIP]
> Per rivedere la procedura per cambiare piattaforma di compilazione, fare riferimento alle istruzioni contenute in [Passaggio a un'altra piattaforma di compilazione](mr-learning-base-02.md#switching-the-build-platform).

Chiudere la finestra Build Settings (Impostazioni di compilazione).

Nel menu di Unity selezionare **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Mixed Reality Toolkit > Utilità > Configura progetto Unity) per aprire la finestra **MRTK Project Configurator** (Configuratore progetto MRTK), verificare che tutte le opzioni siano selezionate, quindi fare clic sul pulsante **Apply** (Applica) per applicare le impostazioni:

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-2.png)

Dal menu Unity scegliere **Edit** > **Project Settings...** (Modifica > Impostazioni del progetto) per aprire la finestra Player Settings (Impostazioni lettore) e quindi individuare la sezione **Player** >  **Other Settings** (Lettore > Altre impostazioni), selezionare **Vulkan** e rimuoverlo facendo clic sul simbolo **"-"** :

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-3.png)

Chiudere la finestra Player Settings (Impostazioni giocatore) e aprire di nuovo la finestra Build Settings (Impostazioni di compilazione).

Nella finestra Build Settings (Impostazioni di compilazione) fare clic sul pulsante **Add Open Scenes** (Aggiungi scene aperte) per aggiungere la scena corrente all'elenco **Scenes In Build** (Scene nella compilazione). Quindi, usare un cavo USB, connettere il dispositivo Android al computer e selezionarlo nell'elenco a discesa **Run Device** (Esegui dispositivo):

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-4.png)

>[!NOTE]
> Se il dispositivo non è presente nell'elenco a discesa Run Device (Esegui dispositivo), potrebbe essere necessario premere il pulsante Refresh (Aggiorna) accanto all'elenco a discesa.

Nella finestra delle impostazioni di compilazione fare clic sul pulsante **Build And Run** (Compila ed esegui) per aprire la finestra Build Android (Compila in Android).

Scegliere il percorso in cui archiviare la build, ad esempio _D:\MixedRealityLearning\Builds_, quindi assegnare un nome adeguato all'apk, ad esempio _MRTKTutorials-AzureSpatialAnchors_, e fare clic sul pulsante **Save** (Salva) per avviare il processo di compilazione:

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-5.png)

> [!NOTE]
Se nella finestra della console Unity viene visualizzato un errore relativo ai moduli Android SDK, NDK o JDK, è necessario aprire Unity Hub e installare i moduli Android Build Support associati.

Al termine del processo di compilazione, le app dovrebbero essere caricate automaticamente nel dispositivo Android.

## <a name="building-your-application-to-your-ios-device"></a>Compilazione dell'applicazione in un dispositivo iOS

In questa sezione verrà illustrato come configurare il progetto per la compilazione e la distribuzione in un dispositivo iOS.

Dal menu di Unity scegli **File** > **Build Settings** (Impostazioni di compilazione) per visualizzare la finestra corrispondente e impostare la piattaforma su iOS:

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-1.png)

> [!TIP]
> Per rivedere la procedura per cambiare piattaforma di compilazione, fare riferimento alle istruzioni contenute in [Passaggio a un'altra piattaforma di compilazione](mr-learning-base-02.md#switching-the-build-platform).

Chiudere la finestra Build Settings (Impostazioni di compilazione).

Nel menu di Unity selezionare **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Mixed Reality Toolkit > Utilità > Configura progetto Unity) per aprire la finestra **MRTK Project Configurator** (Configuratore progetto MRTK), verificare che tutte le opzioni siano selezionate, quindi fare clic sul pulsante **Apply** (Applica) per applicare le impostazioni:

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-2.png)

Dal menu Unity scegliere **Edit** > **Project Settings...** (Modifica > Impostazioni del progetto) per aprire la finestra Player Settings (Impostazioni lettore) e quindi individuare la sezione **Player** >  **Other Settings** (Lettore > Altre impostazioni), deselezionare la casella di controllo **Strip Engine Code** (Rimuovi codice motore) per disabilitarla:

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-3.png)

Chiudere la finestra Player Settings (Impostazioni lettore) e aprire di nuovo la finestra **Build Settings** (Impostazioni di compilazione).

Nella finestra Build Settings (Impostazioni di compilazione) fare clic sul pulsante **Add Open Scenes** (Aggiungi scene aperte) per aggiungere la scena corrente all'elenco **Scenes In Build** (Scene nella compilazione):

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-4.png)

Nella finestra delle impostazioni di compilazione fare clic sul pulsante **Build** (Compila) per aprire la finestra Build iOS (Compila in iOS).

Scegliere un percorso appropriato in cui archiviare il progetto Xcode, ad esempio _D:\MixedRealityLearning\Builds_, creare una nuova cartella e assegnarle un nome adatto, ad esempio, _MRTKTutorials-AzureSpatialAnchors_, e quindi fare clic sul pulsante **Select Folder** (Seleziona cartella) per avviare il processo di compilazione:

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-5.png)

Al termine del processo di compilazione, seguire le istruzioni in [Esportare il progetto Xcode](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) per informazioni su come distribuire il progetto Xcode in un dispositivo iOS.

## <a name="congratulations"></a>Lezione completata

In questa esercitazione è stato descritto come compilare il progetto nei dispositivi Android e iOS usando AR Foundation, ARCore XR Plugin e ARKit XR Plugin.

---
title: Esercitazioni su Ancoraggi nello spazio di Azure - 4. Ancoraggi nello spazio di Azure per Android e iOS
description: Completa questa esercitazione per imparare a implementare Azure Speech SDK in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 05/18/2020
ms.topic: article
keywords: realtà mista, unity, esercitazione, corso, hololens, azure, ancoraggi nello spazio
ms.localizationpriority: high
ms.openlocfilehash: 78fa6a2cdd29bd424ec3016a5467760063b87a14
ms.sourcegitcommit: 7011ac6fde80e5c45f04192fa1db6e1eb559e3b0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/03/2020
ms.locfileid: "84327936"
---
# <a name="4-azure-spatial-anchors-for-android-and-ios"></a>4. Ancoraggi nello spazio di Azure per Android e iOS

Questa esercitazione illustra come compilare il progetto nei dispositivi Android e iOS usando AR Foundation, ARCore XR Plugin e ARKit XR Plugin.

## <a name="objectives"></a>Obiettivi

* Imparare a compilare il progetto in un dispositivo Android usando Unity AR Foundation e ARCore XR Plugin.
* Imparare a compilare il progetto in un dispositivo iOS usando Unity AR Foundation e ARKit XR Plugin.

> [!NOTE]
> Per completare questa esercitazione, è importante avere completato Esercitazioni su Ancoraggi nello spazio di Azure > [Introduzione ad Ancoraggi nello spazio di Azure](mrlearning-asa-ch1.md).

## <a name="adding-inbuilt-unity-packages"></a>Aggiunta di pacchetti di Unity incorporati

In questa sezione installerai i pacchetti AR Foundation, ARCore XR Plugin e ARKit XR Plugin di Unity incorporati che sono necessari per supportare i dispositivi Android e iOS.

Assicurati di installare le versioni corrette di questi pacchetti Unity indicate di seguito:

* **AR Foundation 2.1.4**
* **ARCore XR plugin 2.2.0 preview 2**
* **ARKit XR plugin 2.1.1**

> [!NOTE]
> Se sviluppi il progetto per Android, non è necessario installare il pacchetto ARKit XR Plugin. Analogamente, se sviluppi il progetto per iOS, non è necessario installare ARCore XR Plugin.

Nel menu di Unity seleziona **Window** (Finestra) > **Package Manager** (Gestione pacchetti):

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-1.png)

Potrebbero essere necessari alcuni secondi prima che tutti i pacchetti vengano visualizzati nell'elenco. Per visualizzare i pacchetti in anteprima, fai clic sull'opzione Advanced (Avanzate) e scegli **Show preview packages** (Mostra pacchetti in anteprima).

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-2.png)

Nella finestra Package Manager (Gestione pacchetti) seleziona **AR Foundation**. Tra le diverse versioni presenti, seleziona la **versione 2.1.4**, quindi aggiorna il pacchetto facendo clic sul pulsante **Update to 2.1.4** (Aggiorna a 2.1.4):

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-3.png)

Per supportare i dispositivi Android, segui la stessa procedura per importare **ARCore XR Plugin 2.2.0 preview 2**.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-4.png)

Per supportare i dispositivi iOS, devi importare il pacchetto Unity **ARKit XR plugin 2.1.1** da Package Manager (Gestione pacchetti).

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-5.png)

## <a name="customize-mrtk-to-support-ar-foundation-camera"></a>Personalizzare MRTK per supportare la fotocamera AR Foundation

Personalizza le impostazioni di MRTK per supportare AR Foundation selezionando MixedRealityToolKit nella finestra Hierarchy (Gerarchia) e facendo clic sul pulsante **Clone** (Clona) in Mixed Reality ToolKit, nella finestra Inspector (Controllo).

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-1.png)

Quando fai clic sul pulsante **Clone** (Clona), viene visualizzata una nuova finestra Clone Profile (Clona profilo). Fai di nuovo clic sul pulsante **Clone** (Clona) per clonare il profilo **DefaultMixedRealityToolkitProfile**.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-2.png)

Analogamente, clona **Camera Profile** (Profilo fotocamera) nella finestra Inspector (Controllo).

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-3.png)

Nella finestra Inspector (Controllo) individua MixedReality e seleziona la scheda **Camera** (Fotocamera). Espandi i provider di impostazioni della fotocamera nella finestra Inspector (Controllo) e fai clic su **+Add Camera Setting Provider** (+Aggiungi provider impostazioni fotocamera) > espandi **New data provider 1** (Nuovo provider di dati 1) > in Type (Tipo) seleziona **None** (Nessuno) > seleziona **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > seleziona **UnityARCameraSettings**.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-4.png)

Con l'oggetto MixedRealityToolKit selezionato nella finestra Hierarchy (Gerarchia), nella finestra Inspector (Controllo), associa gli script di supporto. A questo scopo, fai clic sul pulsante **Add component** (Aggiungi componente), digita AR Reference Point Manager (Gestione punto di riferimento AR) e seleziona lo script.

Quando aggiungi lo script **AR Reference Point Manager** (Gestione punto di riferimento AR), viene aggiunto automaticamente anche lo script **AR Session Origin** (Origine sessione AR) nella finestra Inspector (Controllo). Dopo aver aggiunto gli script di supporto, la finestra Inspector (Controllo) dovrebbe risultare analoga alla seguente.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-5.png)

## <a name="build-an-application-to-an-android-device"></a>Compilare un'applicazione in un dispositivo Android

Per compilare l'applicazione in un dispositivo Android, fai clic su **File** nella parte superiore della finestra e seleziona **Build Settings** (Impostazioni di compilazione). Viene visualizzata una nuova finestra. Seleziona **Android** e fai clic su **Switch Platform** (Cambia piattaforma). Il cambio di piattaforma richiederà qualche minuto. Dopo il passaggio alla piattaforma Android, fai clic su **Add Open Scene** (Aggiungi scena aperta) e verifica che la scena corrente sia l'unica scena selezionata nell'elenco **Scenes In Build** (Scene nella compilazione).

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-1.png)

Chiudi la finestra **Build Settings** (Impostazioni di compilazione). Nel menu di Unity seleziona Mixed Reality Toolkit > Utilities (Utilità) > Configure Unity Project (Configura progetto Unity) e fai clic su **Apply** (Applica) per configurare il progetto Unity per la piattaforma Android.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-2.png)

Nel menu di Unity scegli **Edit** (Modifica)  > **Project Settings** (Impostazioni progetto) per visualizzare la finestra corrispondente. Nella finestra Project Settings (Impostazioni progetto) seleziona la scheda **Player** (Giocatore), espandi la sezione **Other Settings** (Altre impostazioni), seleziona **Vulkan** e rimuovila facendo clic sul simbolo " **-** ".

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-3.png)

Chiudi la finestra **Player Settings** (Impostazioni giocatore) e apri di nuovo la finestra **Build Settings** (Impostazioni di compilazione). A questo punto, usando un cavo USB, connetti il dispositivo Android al computer e seleziona il dispositivo nell'elenco a discesa **Build and Run** (Compila ed esegui), quindi fai clic su **Build And Run** (Compila ed esegui). Ti verrà chiesto di salvare un file APK con un nome qualsiasi.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-4.png)

> [!NOTE]
> Se nella finestra della console Unity viene visualizzato un errore relativo ai moduli Android SDK, NDK e JDK, è necessario aprire Unity Hub e installare i moduli SDK, NDK e JDK associati per il modulo Android Build Support.

Al termine del processo di compilazione, le applicazioni dovrebbero essere caricate automaticamente sul dispositivo Android.

## <a name="build-an-application-to-ios-device"></a>Compilare un'applicazione in un dispositivo iOS

Per compilare l'applicazione in un dispositivo iOS, fai clic su **File** nella parte superiore della finestra e seleziona **Build Settings** (Impostazioni di compilazione). Viene visualizzata una nuova finestra. Seleziona **iOS** e fai clic su **Switch Platform** (Cambia piattaforma).

![mrlearning-asa](images/mrlearning-asa/tutorial4-section4-step1-1.png)

Chiudi la finestra **Build Settings** (Impostazioni di compilazione). Nel menu di Unity seleziona Mixed Reality Toolkit > Utilities (Utilità) > Configure Unity Project (Configura progetto Unity) e fai clic su **Apply** (Applica) per configurare il progetto Unity per la piattaforma iOS.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section4-step1-2.png)

Per compilare il progetto iOS XCode, passa a Build Settings (Impostazioni di compilazione) e fai clic su **Build** (Compila).

Segui [questa guida](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) per scoprire come distribuire il progetto in un dispositivo iOS.

## <a name="congratulations"></a>Lezione completata

In questa esercitazione hai imparato a compilare il progetto per dispositivi Android e iOS. Hai anche appreso come usare AR Foundation, ARCore XR Plugin e ARKit XR Plugin per fare in modo che il progetto sia utilizzabile su dispositivi Android e iOS.

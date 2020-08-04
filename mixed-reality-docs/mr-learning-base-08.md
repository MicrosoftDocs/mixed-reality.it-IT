---
title: Esercitazioni introduttive - 8 Uso del tracciamento oculare
description: Questo corso illustra come usare Mixed Reality Toolkit (MRTK) per creare un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: 31552cba9a68d1f1214395dbf4e4ed84ecd3f388
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376603"
---
# <a name="8-using-eye-tracking"></a>8. Uso del tracciamento oculare

## <a name="overview"></a>Panoramica

In questa esercitazione si apprenderà come abilitare il tracciamento oculare per HoloLens 2 e aggiungere questa funzionalità agli oggetti, in modo da attivare le azioni quando l'utente rivolge loro lo sguardo.

> [!NOTE]
> Se si distribuisce questo progetto anche in HoloLens (prima generazione), tenere presente che il tracciamento oculare è supportato solo in HoloLens 2.

## <a name="objectives"></a>Obiettivi

* Imparare ad abilitare il tracciamento oculare per HoloLens 2
* Imparare a usare il tracciamento oculare per attivare un'azione

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a>Verifica dell'abilitazione della funzionalità di input mediante sguardo fisso

Nel menu di Unity selezionare Mixed Reality Toolkit > Utilities > **Configure Unity Project** (Mixed Reality Toolkit > Utilità > Configura progetto Unity) per aprire la finestra **MRTK Project Configurator** (Configuratore del progetto MRTK) e quindi, nella sezione **UWP Capabilities** (Funzionalità UWP), verificare che l'opzione **Enable Eye Gaze Input Capability** (Abilita la funzionalità di input mediante sguardo fisso) sia disattivata:

![mr-learning-base](images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> La funzionalità di input mediante sguardo fisso dovrebbe essere stata abilitata durante la configurazione delle istruzioni riportate in [Apply the MRTK Project Configurator settings](mr-learning-base-02.md#1-apply-the-mrtk-project-configurator-settings) (Applicare le impostazioni del Configuratore del progetto MRTK) quando è stato configurato il progetto Unity all'inizio di questa serie di esercitazioni. Se, tuttavia, non è abilitata, assicurarsi di farlo ora.

## <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a>Abilitazione dello sguardo fisso nel provider di dati per lo sguardo fisso

Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **MixedRealityToolkit** e quindi nella finestra Inspector (Controllo) selezionare la scheda MixedRealityToolkit > **Input** e seguire questa procedura:

* Clonare il profilo **DefaultHoloLens2InputSystemProfile** e assegnargli un nome appropriato, ad esempio _GettingStarted_HoloLens2InputSystemProfile_
* Espandere la sezione**Pointers** (Puntatori)
* Clonare il profilo **DefaultMixedRealityPointerProfile** e assegnargli un nome appropriato, ad esempio _GettingStarted_MixedRealityPointerProfile_
* Individuare la sezione **Gaze Settings** (Impostazioni sguardo) e selezionare la casella di controllo **Is Eye Tracking Enabled** (Tracciamento oculare abilitato)

![mr-learning-base](images/mr-learning-base/base-08-section2-step1-1.png)

> [!TIP]
> Per rivedere la procedura di clonazione dei profili di MRTK, fare riferimento alle istruzioni riportate in [Configurazione dei profili di Mixed Reality Toolkit](mr-learning-base-03.md).

## <a name="enabling-simulated-eye-tracking-for-the-unity-editor"></a>Abilitazione del tracciamento oculare simulato per l'editor di Unity

Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **MixedRealityToolkit**, nella finestra Inspector (Controllo) passare alla scheda **Input** e quindi:

* Espandere la sezione **Input Data Providers** > **Input Simulation Service** (Provider di dati di input > Servizio di simulazione input)
* Clonare il profilo **DefaultMixedRealityInputSimulationProfile** e assegnargli un nome appropriato, ad esempio _GettingStarted_MixedRealityInputSimulationProfile_
* Individuare la sezione **Eye Simulation** (Simulazione oculare) e selezionare la casella di controllo **Simulate Eye Position** (Simula posizione oculare)

![mr-learning-base](images/mr-learning-base/base-08-section3-step1-1.png)

## <a name="adding-eye-tracking-to-objects"></a>Aggiunta del tracciamento oculare agli oggetti

Nella finestra Hierarchy (Gerarchia) espandere l'oggetto RoverExplorer > **Buttons** (Pulsanti) e quindi, per ognuno dei tre oggetti pulsante figlio, espandere e selezionare l'oggetto SeeItSayItLabel > **TextMeshPro**:

![mr-learning-base](images/mr-learning-base/base-08-section4-step1-1.png)

Con i tre oggetti TextMeshPro ancora selezionati, nella finestra Inspector (Controllo) usare il pulsante **Add Component** (Aggiungi componente) per aggiungere i componenti seguenti a tutti gli oggetti selezionati:

* Componente **Box Collider** (Collisore cubico)
* Componente **EyeTrackingTarget**

![mr-learning-base](images/mr-learning-base/base-08-section4-step1-2.png)

Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **Hints** (Suggerimenti) > SeeItSayItLabel > **TextMeshPro** e quindi configurare il componente **EyeTrackingTarget** come indicato di seguito:

* Nella sezione dell'evento **On Look At Start ()** (Quando viene rivolto lo sguardo all'inizio)
  * Fare clic sull'icona **+** piccola per aggiungere un altro evento
  * Assegnare l'oggetto, ad esempio lo stesso oggetto **TextMeshPro**, al campo **None (Object)** (Nessuno - Oggetto)
  * Dall'elenco a discesa **No Function** (Nessuna funzione) selezionare **TextMeshPro** > **float fontSize** (fontSize mobile) per aggiornare il valore della proprietà quando viene attivato l'evento
  * Impostare l'argomento su **0,06** per aumentare del 50% le dimensioni correnti del carattere 0,04
* Nella sezione dell'evento **On Look Away ()** (Quando viene distolto lo sguardo)
  * Fare clic sull'icona **+** piccola per aggiungere un altro evento
  * Assegnare l'oggetto, ad esempio lo stesso oggetto **TextMeshPro**, al campo **None (Object)** (Nessuno - Oggetto)
  * Dall'elenco a discesa **No Function** (Nessuna funzione) selezionare **TextMeshPro** > **float fontSize** (fontSize mobile) per aggiornare il valore della proprietà quando viene attivato l'evento
  * Impostare l'argomento su **0,04** per ripristinare le dimensioni del carattere a 0,04

![mr-learning-base](images/mr-learning-base/base-08-section4-step1-3.png)

**Ripetere** questo passaggio per l'oggetto **Explode** (Espandi) > SeeItSayItLabel > **TextMeshPro** e l'oggetto **Reset** (Ripristina) > SeeItSayItLabel > **TextMeshPro**.

Se si immette la modalità di gioco e quindi si tiene premuto il pulsante destro del mouse mentre si sposta il puntatore del mouse fino a quando lo sguardo fisso raggiunge una delle etichette, si noterà che le dimensioni del carattere aumentano del 50% e vengono ripristinate le dimensioni originali quando si distoglie lo sguardo:

![mr-learning-base](images/mr-learning-base/base-08-section4-step1-4.png)

## <a name="congratulations"></a>Lezione completata

In questa esercitazione si è appreso come abilitare il tracciamento oculare per HoloLens 2 e come aggiungere questa funzionalità agli oggetti per attivare le azioni quando l'utente rivolge loro lo sguardo.

[Esercitazione successiva: 9. Uso dei comandi vocali](mr-learning-base-09.md)
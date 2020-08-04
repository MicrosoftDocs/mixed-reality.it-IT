---
title: Esercitazioni introduttive - 9. Uso dei comandi vocali
description: Questo corso illustra come usare Mixed Reality Toolkit (MRTK) per creare un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: b0b9771d9569d100a354af96a34cd20ef2a3d7c4
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376593"
---
# <a name="9-using-speech-commands"></a>9. Uso dei comandi vocali

## <a name="overview"></a>Panoramica

In questa esercitazione verrà spiegato come creare comandi vocali e come controllarli a livello globale. Si imparerà anche a controllare i comandi vocali locali che richiedono che l'utente guardi l'oggetto che controlla il comando vocale.

## <a name="objectives"></a>Obiettivi

* Imparare a creare comandi vocali
* Imparare a controllare i comandi vocali a livello globale e locale

## <a name="ensuring-the-microphone-capability-is-enabled"></a>Verificare che la funzionalità Microfono sia abilitata

Nel menu di Unity selezionare Mixed Reality Toolkit > Utilities > **Configure Unity Project** (Mixed Reality Toolkit > Utilità > Configura progetto Unity) per aprire la finestra **MRTK Project Configurator** (Configuratore del progetto MRTK) e quindi, nella sezione **UWP Capabilities** (Funzionalità UWP), verificare che l'opzione **Enable Microphone Capability** (Abilita la funzionalità Microfono) sia disattivata:

![mr-learning-base](images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> La funzionalità Microfono dovrebbe essere stata abilitata durante la procedura illustrata in [Applicare le impostazioni di MRTK Project Configurator (Configuratore del progetto MRTK)](mr-learning-base-02.md#1-apply-the-mrtk-project-configurator-settings) quando è stato configurato il progetto Unity all'inizio di questa serie di esercitazioni. Se, tuttavia, non è abilitata, assicurarsi di farlo ora.

## <a name="creating-speech-commands"></a>Creazione di comandi vocali

Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **MixedRealityToolkit** e quindi nella finestra Inspector (Controllo) selezionare la scheda MixedRealityToolkit > **Input** e seguire questa procedura:

* Espandere la **Speech** (Voce)
* Clonare il profilo **DefaultMixedRealitySpeechCommandsProfile** e assegnargli un nome appropriato, ad esempio _GettingStarted_MixedRealitySpeechCommandsProfile_
* Verificare che **Start Behaviour** (Comportamento di avvio) sia impostato su **Auto Start** (Avvio automatico)

![mr-learning-base](images/mr-learning-base/base-09-section2-step1-1.png)

> [!TIP]
> Per rivedere la procedura di clonazione dei profili MRTK, fare riferimento alle istruzioni contenute in [Configurazione dei profili di Mixed Reality Toolkit](mr-learning-base-03.md).

Nella sezione **Speech Commands** (Comandi vocali) fare clic sul pulsante **+ Add a New Speech Command** (+ Aggiungi un nuovo comando vocale) per aggiungere quattro nuovi comandi vocali all'elenco dei comandi vocali esistenti e quindi nei campi **Keyword** (Parola chiave) immettere quanto segue:

* Abilita indicatore
* Abilita tocco per posizionare
* Abilita rettangolo di selezione
* Disabilita rettangolo di selezione

![mr-learning-base](images/mr-learning-base/base-09-section2-step1-2.png)

> [!TIP]
> Se il computer non dispone di un microfono, è possibile assegnare un KeyCode ai comandi vocali, che consente di attivarli quando viene premuto il tasto corrispondente.

## <a name="controlling-speech-commands"></a>Controllo dei comandi vocali

Nella finestra Project (Progetto) passare alla cartella **Assets** (Asset)  > **MRTK** > **SDK** > **Features** (Funzionalità)  > **UX** > **Prefabs** (Prefab)  > **ToolTip** (Descrizione comando) per individuare i prefab relativi alle descrizioni comando:

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-1.png)

Nella finestra Hierarchy (Gerarchia) fare clic con il pulsante destro del mouse su un'area vuota e scegliere **Create Empty** (Crea vuoto) per aggiungere un oggetto vuoto alla scena.

Denominare l'oggetto **SpeechInputHandler_Global**, quindi nella finestra Inspector (Controllo) usare il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **SpeechInputHandler** e configurarlo nel modo seguente:

* **Deselezionare** la casella di controllo **Is Focus Required** (È necessario lo stato attivo) in modo che l'utente non debba guardare l'oggetto con il componente SpeechInputHandler per attivare il comando vocale
* Dalla finestra Project (Progetto) assegnare il prefeb **SpeechConfirmation Tooltip** al campo **Speech Confirmation Tooltip Prefab**, in modo che venga visualizzato questo prefab quando viene riconosciuto un comando vocale

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-2.png)

Nel componente SpeechInputHandler component fare clic tre volte sulla piccola icona **+** per aggiungere tre elementi di parola chiave:

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-3.png)

Espandere **Element 0** e configurarlo come segue:

* Nel campo **Keyword** (Parola chiave) immettere **Abilita indicatore** per fare riferimento al comando vocale Abilita indicatore creato nella sezione precedente
* Fare clic sulla piccola icona **+** per aggiungere un evento
* Nella finestra Hierarchy (Gerarchia) assegnare l'oggetto **Indicator** al campo **None (Object)** (Nessuno - Oggetto)
* Nell'elenco a discesa **No Function** (Nessuna funzione) selezionare **GameObject** > **SetActive (bool)** per impostare questa funzione come l'azione da eseguire quando viene attivato l'evento
* Assicurarsi che la casella di controllo dell'argomento sia **selezionata**

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-4.png)

Espandere **Element 1** e configurarlo come segue:

* Nel campo **Keyword** (Parola chiave) immettere **Abilita rettangolo di selezione** per fare riferimento al comando vocale Abilita rettangolo di selezione creato nella sezione precedente
* Fare clic sulla piccola icona **+** per aggiungere un evento
* Nella finestra Hierarchy (Gerarchia) assegnare l'oggetto **RoverExplorer** al campo **None (Object)** (Nessuno - Oggetto)
* Nell'elenco a discesa **No Function** (Nessuna funzione) selezionare **BoundingBox** > **bool enabled** per aggiornare il valore di questa proprietà quando viene attivato l'evento
* Assicurarsi che la casella di controllo dell'argomento sia **selezionata**
* Fai clic sulla piccola icona **+** per aggiungere un altro evento
* Nella finestra Hierarchy (Gerarchia) assegnare l'oggetto **RoverExplorer** al campo **None (Object)** (Nessuno - Oggetto)
* Nell'elenco a discesa **No Function** (Nessuna funzione) selezionare **ObjectManipulator** > **bool enabled** per aggiornare il valore di questa proprietà quando viene attivato l'evento
* Assicurarsi che la casella di controllo dell'argomento sia **selezionata**

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-5.png)

Espandere **Element 2** e configurarlo come segue:

* Nel campo **Keyword** (Parola chiave) immettere **Disabilita rettangolo di selezione** per fare riferimento al comando vocale Disabilita rettangolo di selezione creato nella sezione precedente
* Fare clic sulla piccola icona **+** per aggiungere un evento
* Nella finestra Hierarchy (Gerarchia) assegnare l'oggetto **RoverExplorer** al campo **None (Object)** (Nessuno - Oggetto)
* Nell'elenco a discesa **No Function** (Nessuna funzione) selezionare **BoundingBox** > **bool enabled** per aggiornare il valore di questa proprietà quando viene attivato l'evento
* Verificare che la casella di controllo dell'argomento sia **deselezionata**
* Fai clic sulla piccola icona **+** per aggiungere un altro evento
* Nella finestra Hierarchy (Gerarchia) assegnare l'oggetto **RoverExplorer** al campo **None (Object)** (Nessuno - Oggetto)
* Nell'elenco a discesa **No Function** (Nessuna funzione) selezionare **ObjectManipulator** > **bool enabled** per aggiornare il valore di questa proprietà quando viene attivato l'evento
* Verificare che la casella di controllo dell'argomento sia **deselezionata**

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-6.png)

Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto RoverExplorer > **RoverAssembly** e quindi nella finestra Inspector (Controllo) usare il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **SpeechInputHandler** e configuralo nel modo seguente:

* Verificare che la casella di controllo **Is Focus Required** (È necessario lo stato attivo) sia **selezionata**, in modo che l'utente debba guardare l'oggetto con il componente SpeechInputHandler, ovvero RoverAssembly, per attivare il comando vocale
* Dalla finestra Project (Progetto) assegnare il prefeb **SpeechConfirmation Tooltip** al campo **Speech Confirmation Tooltip Prefab**, in modo che venga visualizzato questo prefab quando viene riconosciuto un comando vocale

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-7.png)

Nel componente SpeechInputHandler fare clic sulla piccola icona **+** per aggiungere un elemento parola chiave, espandere l'elemento appena creato, quindi configurarlo come segue:

* Nel campo **Keyword** (Parola chiave) immettere **Abilita tocco per posizionare** per fare riferimento al comando vocale Abilita tocco per posizionare creato nella sezione precedente
* Fare clic sulla piccola icona **+** per aggiungere un evento
* Nella finestra Hierarchy (Gerarchia) assegnare l'oggetto stesso, ovvero lo stesso oggetto **RoverAssembly**, al campo **None (Object)** (Nessuno - Oggetto)
* Nell'elenco a discesa **No Function** (Nessuna funzione) selezionare **TapToPlace** > **bool enabled** per aggiornare il valore di questa proprietà quando viene attivato l'evento
* Assicurarsi che la casella di controllo dell'argomento sia **selezionata**

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-8.png)

## <a name="congratulations"></a>Lezione completata

In questa esercitazione è stato spiegato come creare comandi vocali e come controllarli a livello globale. Si è anche imparato a controllare i comandi vocali locali che richiedono che l'utente guardi l'oggetto che controlla il comando vocale.

A questo punto si conclude la serie [Esercitazioni introduttive](mr-learning-base-01.md). In queste esercitazioni è stata creata da zero un'esperienza di realtà mista completa tramite MRTK.

Nelle prossime due serie di esercitazioni, [Esercitazioni su Ancoraggi nello spazio di Azure](mr-learning-asa-01.md) e [Esercitazioni sulle funzionalità multiutente](mr-learning-sharing-01.md), verrà spiegato prima di tutto come integrare Ancoraggi nello spazio di Azure in un progetto per ancorare l'esperienza Rover Explorer creata nel mondo reale. Quindi, verrà illustrato come aggiungere funzionalità multiutente al progetto per condividere i movimenti di utenti e oggetti in tempo reale.

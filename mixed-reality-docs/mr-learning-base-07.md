---
title: Esercitazioni introduttive - 7 Interazione con oggetti 3D
description: Questo corso illustra come usare Mixed Reality Toolkit (MRTK) per creare un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: f02780a1b9421b814242727ce92311d62b5e3461
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376423"
---
# <a name="7-interacting-with-3d-objects"></a>7. Interazione con oggetti 3D

In questa esercitazione apprenderai come abilitare la manipolazione da vicino e da lontano degli oggetti 3D e limitare i tipi di manipolazione consentiti. Apprenderai anche come aggiungere cubi di delimitazione intorno agli oggetti 3D per controllare più facilmente la manipolazione degli oggetti.

## <a name="objectives"></a>Obiettivi

* Apprendere come configurare gli oggetti 3D in modo che sia possibile interagire con essi
* Apprendere come aggiungere cubi di delimitazione a oggetti 3D

## <a name="manipulating-3d-objects"></a>Manipolazione di oggetti 3D

In questa sezione aggiungerai la possibilità di manipolare tutte le parti rover organizzate sul tavolo durante l'esercitazione [Posizionamento degli oggetti nella scena](mr-learning-base-04.md).

Di seguito sono elencati i passaggi principali da eseguire per ottenere questo risultato:

1. Aggiungere il componente Object Manipulator (Script) (Manipolatore oggetti - script) a tutti gli oggetti parte
2. Aggiungere il componente NearInteractionGrabbable a tutti gli oggetti parte
3. Configurare il componente Object Manipulator (Script) (Manipolatore oggetti - script)

> [!NOTE]
> Per poter **manipolare un oggetto**, è necessario che l'oggetto abbia i componenti seguenti:
>
> * Componente **Collider** (Collisore), ad esempio un collisore cuboide
> * Componente **Object Manipulator (Script)** (Manipolatore oggetti - script)
>
> Per poter **manipolare** e **afferrare un oggetto con le mani tracciate**, è necessario che l'oggetto abbia i componenti seguenti:
>
> * Componente **Collider** (Collisore), ad esempio un collisore cuboide
> * Componente **Object Manipulator (Script)** (Manipolatore oggetti - script)
> * Componente **NearInteractionGrabbable**

Configurerai inoltre Rover Explorer (Esplora rover) in modo che sia possibile posizionare le parti rover sul rover per renderlo un assembly di rover completo.

Nella finestra Hierarchy (Gerarchia) espandi l'oggetto RoverExplorer > **RoverParts** e seleziona tutti i relativi oggetti parte rover figlio e l'oggetto **RoverAssembly**, quindi nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere i componenti seguenti a tutti gli oggetti selezionati:

* Componente **Object Manipulator (Script)** (Manipolatore oggetti - script)
* Componente **NearInteractionGrabbable**
* Componente **Part Assembly Controller (Script)** (Controllo assembly parti - script)

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-1.png)

> [!TIP]
> Per selezionare più oggetti non adiacenti, tieni premuto CTRL mentre usi il mouse per selezionare un oggetto.

> [!NOTE]
> Ai fini di questa esercitazione, i collisori sono già stati aggiunti alle parti rover. Per altre informazioni sui collisori, puoi visitare la documentazione <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">corrispondente</a> di Unity.

> [!NOTE]
> Part Assembly Controller (Script) (Controllo assembly parti - script) non fa parte di MRTK, ma è stato incluso negli asset dell'esercitazione.

Con tutti gli oggetti parte rover e l'oggetto RoverAssembly ancora selezionati, nella finestra Inspector (Controllo) configura il componente **Object Manipulator (Script)** (Manipolatore oggetti - script) come indicato di seguito:

* Dall'elenco a discesa **Two Handed Manipulation Type** (Tipo di manipolazione a due mani) deseleziona Scale (Scala) in modo che siano abilitate solo le opzioni **Move** (Sposta) e **Rotate** (Ruota)

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-2.png)

> [!NOTE]
> A questo punto hai abilitato la manipolazione per tutti gli oggetti parte rover e per l'oggetto RoverAssembly.

Nella finestra Project (Progetto) passa alla cartella **Assets (Asset)**  > **MRTK** > **SDK** > **StandardAssets** > **Audio** per individuare i clip audio:

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-3.png)

Nella finestra Hierarchy (Gerarchia) seleziona di nuovo gli **oggetti parte rover** e quindi nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Audio Sources** (Origini audio) e configuralo come indicato di seguito:

* Assegna il clip audio **MRTK_Scale_Start** al campo **AudioClip**
* Deseleziona la casella di controllo **Play On Awake** (Riproduci quando operativo)
* Modifica il campo **Spatial Blend** (Blend spaziale) impostandolo su 1

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-4.png)

Nella finestra Hierarchy (Gerarchia) espandi l'oggetto RoverAssembly > RoverModel_PlacementHints_XRay > **Parts_PlacementHints** in modo da rivelare tutti gli oggetti suggerimento di posizionamento, quindi scegli la prima parte rover, RoverParts > **Camera_Part**, e configura il componente **Part Assembly Controller (Script)** (Controllo assembly parti - script) come indicato di seguito:

* Assegna l'oggetto **Camera_PlacementHint** al campo **Location To Place** (Punto di posizionamento)

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-5.png)

**Ripeti** questo passaggio per ognuno degli oggetti parte rover rimanenti e per l'oggetto RoverAssembly per configurare il componente **Part Assembly Controller (Script)** (Controllo assembly parti - script) come indicato di seguito:

* Per **Generator_Part**, assegna l'oggetto **Generator_PlacementHint** al campo **Location To Place** (Punto di posizionamento)
* Per **Lights_Part**, assegna l'oggetto **Lights_PlacementHint** al campo **Location To Place** (Punto di posizionamento)
* Per **UHFAntenna_Part**, assegna l'oggetto **UHFAntenna_PlacementHint** al campo **Location To Place** (Punto di posizionamento)
* Per **Spectrometer_Part**, assegna l'oggetto **Spectrometer_PlacementHint** al campo **Location To Place** (Punto di posizionamento)
* Per **RoverAssembly**, assegna l'oggetto stesso., ovvero l'oggetto **RoverAssembly** stesso, al campo **Location To Place** (Punto di posizionamento)

Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto pulsante RoverExplorer > Buttons (Pulsanti) > **Reset** (Reimposta) e quindi nella finestra Inspector (Controllo) configura l'evento **OnClick ()** con supporto per interazioni come indicato di seguito:

* Assegna l'oggetto **RoverAssembly** al campo **None (Object)** (Nessuno - Oggetto)
* Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **PartAssemblyController** > **ResetPlacement ()** per impostare questa funzione come l'azione da eseguire quando viene attivato l'evento

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-6.png)

Se attivi ora la modalità di gioco, puoi usare l'interazione da vicino o da lontano per posizionare le parti rover sul rover. Quando è vicina al suggerimento di posizionamento corrispondente, la parte si blocca in posizione e diventa parte del rover. Per reimpostare i posizionamenti, puoi scegliere il pulsante Reset (Reimposta):

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-7.png)

Per altre informazioni sul componente Object Manipulator (Manipolatore oggetti) e sulle relative proprietà associate, puoi visitare la guida su [tale componente](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html) nel [portale della documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="adding-bounding-boxes"></a>Aggiunta di cubi di delimitazione

I cubi di delimitazione consentono di manipolare gli oggetti con una mano in modo più semplice e intuitivo per l'interazione sia da vicino che da lontano, in quanto forniscono punti di manipolazione utilizzabili per il ridimensionamento e la rotazione.

In questo esempio aggiungerai un cubo di delimitazione all'oggetto RoverExplorer in modo da poter spostare, ruotare e ridimensionare facilmente l'intera esperienza. Configurerai inoltre il menu in modo che sia possibile abilitare e disabilitare il cubo di delimitazione.

Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **RoverExplorer**, quindi nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere i componenti seguenti:

* Componente **BoundingBox**
* Componente **Object Manipulator (Script)** (Manipolatore oggetti - script)

**Deseleziona** quindi la casella di controllo accanto a entrambi i componenti in modo che siano **disabilitati** per impostazione predefinita:

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-1.png)

> [!NOTE]
> La visualizzazione del cubo di delimitazione viene creata in fase di runtime e pertanto non è visibile prima di passare alla modalità di gioco.

> [!NOTE]
> Il componente BoundingBox aggiungerà automaticamente il componente NearInteractionGrabbable in fase di runtime. Non è necessario pertanto aggiungere questo componente per afferrare con le mani tracciate gli oggetti racchiusi.

Nella finestra Hierarchy (Gerarchia) espandi l'oggetto Menu > **ButtonCollection** in modo da rivelare i quattro pulsanti e rinomina il terzo pulsante come **BoundingBox_Enable**, quindi nella finestra Inspector (Controllo) configura il componente **Button Config Helper (Script)** (Helper configurazione pulsanti - script) come indicato di seguito:

* Imposta **Main Label Text** (Testo etichetta principale) su **Enable** (Abilita)
* Assegna l'oggetto **RoverExplorer** al campo **None (Object)** (Nessuno - Oggetto)
* Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **BoundingBox** > **bool Enabled** per aggiornare il valore di questa proprietà quando viene attivato l'evento
* Verifica che la casella di controllo dell'argomento sia **selezionata**
* Fai clic sull'icona **+** piccola per aggiungere un altro evento
* Assegna l'oggetto **RoverExplorer** al campo **None (Object)** (Nessuno - Oggetto)
* Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **ObjectManipulator** > **bool Enabled** per aggiornare il valore di questa proprietà quando viene attivato l'evento
* Verifica che la casella di controllo dell'argomento sia **selezionata**
* Lascia per **Icon** (Icona) l'impostazione di icona 'cubo con cubo di delimitazione'

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-2.png)

Rinomina il quarto e ultimo pulsante come **BoundingBox_Disable**, quindi nella finestra Inspector (Controllo) configura il componente **Button Config Helper (Script)** (Helper configurazione pulsanti - script) come indicato di seguito:

* Imposta **Main Label Text** (Testo etichetta principale) su **Disable** (Disabilita)
* Assegna l'oggetto **RoverExplorer** al campo **None (Object)** (Nessuno - Oggetto)
* Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **BoundingBox** > **bool Enabled** per aggiornare il valore di questa proprietà quando viene attivato l'evento
* Verifica che la casella di controllo dell'argomento sia **deselezionata**
* Fai clic sull'icona **+** piccola per aggiungere un altro evento
* Assegna l'oggetto **RoverExplorer** al campo **None (Object)** (Nessuno - Oggetto)
* Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **ObjectManipulator** > **bool Enabled** per aggiornare il valore di questa proprietà quando viene attivato l'evento
* Verifica che la casella di controllo dell'argomento sia **deselezionata**
* Modifica l'impostazione di **Icon** (Icona) configurando l'icona 'cubo con cubo di delimitazione'

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-3.png)

Se ora attivi la modalità di gioco e abiliti il cubo di delimitazione facendo clic sul pulsante Enable (Abilita), puoi usare l'interazione da vicino o da lontano per spostare, ruotare e ridimensionare il cubo di delimitazione e usare il pulsante Disable (Disabilita) per disabilitare nuovamente il cubo di delimitazione:

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-4.png)

Per altre informazioni sul componente Bounding Box (Cubo di delimitazione) e sulle relative proprietà associate, puoi visitare la guida su [tale componente](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) nel [portale della documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="congratulations"></a>Lezione completata

In questa esercitazione hai appreso come abilitare la manipolazione da vicino e da lontano degli oggetti 3D e limitare i tipi di manipolazione consentiti. Hai appreso anche come aggiungere cubi di delimitazione intorno agli oggetti 3D per controllare più facilmente la manipolazione degli oggetti.

[Esercitazione successiva: 8. Uso del tracciamento oculare](mr-learning-base-08.md)

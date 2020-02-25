---
title: Esercitazioni introduttive-5. Interazione con oggetti 3D
description: ''
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 7eb38e205237257e400550299fdeebb73ba746f1
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2020
ms.locfileid: "77555500"
---
# <a name="5-interacting-with-3d-objects"></a>5. interazione con oggetti 3D

In questa esercitazione si apprenderanno informazioni sul contenuto 3D di base e sull'esperienza utente, ad esempio l'organizzazione di oggetti 3D come parte di una raccolta, i riquadri per la manipolazione di base, l'interazione quasi e la distanza e i movimenti di tocco e di manipolazione con il rilevamento manuale.

## <a name="objectives"></a>Obiettivi

* Creare un pannello di oggetti 3D che verrà usato per gli altri obiettivi di apprendimento
* Implementare i cubi di delimitazione
* Configurare gli oggetti 3D per la manipolazione di base, ad esempio spostare, ruotare e ridimensionare
* Esplorare l'interazione da vicino e da lontano
* Informazioni sugli altri movimenti di rilevamento della mano, ad esempio la cattura e il tocco

## <a name="importing-the-tutorial-assets"></a>Importazione delle risorse dell'esercitazione

Scaricare e importare il pacchetto personalizzato Unity:

* [MRTK. HoloLens2. Unity. Esercitations. assets. GettingStarted. 2.3.0.2. file unitypackage Tools](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)

Dopo aver importato le risorse dell'esercitazione, la finestra del progetto avrà un aspetto simile al seguente:

![mrlearning-base](images/mrlearning-base/tutorial4-section1-step1-1.png)

> [!TIP]
> Per un promemoria su come importare un pacchetto personalizzato Unity, è possibile fare riferimento alle istruzioni [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) .

## <a name="decluttering-the-scene-view"></a>Disordine della visualizzazione scena

Per semplificare l'uso della scena, impostare la **visibilità della scena** per il **cubo** e gli oggetti **buttoncollection** su off facendo clic sull'icona a forme di **occhio** a sinistra degli oggetti. In questo modo l'oggetto viene nascosto nella finestra della scena senza modificarne la visibilità nel gioco:

![mrlearning-base](images/mrlearning-base/tutorial4-section2-step1-1.png)

> [!TIP]
> Per altre informazioni sui controlli di visibilità della scena e su come usarli per ottimizzare la visualizzazione scena e il flusso di lavoro, è possibile visitare la documentazione relativa alla <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">visibilità della scena</a> di Unity.

## <a name="organizing-3d-objects-in-a-collection"></a>Organizzazione di oggetti 3D in una raccolta

In questa sezione verrà creato un pannello di oggetti 3D che verrà usato per esplorare varie modalità di interazione con gli oggetti 3D nelle sezioni seguenti di questa esercitazione. In particolare, gli oggetti 3D verranno configurati in modo da essere posizionati in una griglia 3 x 3.

Analogamente a quando è [stato creato un pannello di pulsanti](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection), i passaggi principali da eseguire sono:

1. Padre degli oggetti 3D in un oggetto padre
2. Aggiungere e configurare il componente Grid Object Collection (script)

### <a name="1-parent-the-3d-objects-to-a-parent-object"></a>1. padre degli oggetti 3D in un oggetto padre

Nella finestra gerarchia **creare un oggetto vuoto**, assegnargli un nome appropriato, ad esempio **3DObjectCollection**, e posizionarlo in una posizione appropriata, ad esempio X = 0, Y =-0,2, Z = 2.

Nella finestra del progetto passare a **assets** > **MRTK. Tutorials. GettingStarted** > **prefabbricati** **, quindi i** prefabbricati seguenti in **3DObjectCollection**:

* Cheese
* CoffeeCup
* EarthCore
* Octa
* Platonico
* TheModule

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-1.png)

Nella finestra gerarchia **creare tre cubi** come oggetti figlio di **3DObjectCollection** e impostare la relativa **scala** di trasformazione su X = 0,15, Y = 0,15, Z = 0,15:

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-2.png)

> [!TIP]
> Per un promemoria su come eseguire i passaggi elencati in precedenza, è possibile fare riferimento all'esercitazione relativa alla [creazione dell'interfaccia utente e alla configurazione del Toolkit di realtà mista](mrlearning-base-ch2.md) .

Riposizionare i cubi in modo che sia possibile visualizzare ogni cubo:

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-3.png)

Nella finestra del progetto passare a **assets** > **MixedRealityToolkit. SDK** > **StandardAssets** > **Materials** per visualizzare i materiali forniti con MRTK.

**Fare clic su e trascinare** un materiale appropriato nella proprietà elemento 0 di **materiali** renderer mesh del cubo, ad esempio:

* MRTK_Standard_GlowingCyan
* MRTK_Standard_GlowingOrange
* MRTK_Standard_Green

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-4.png)

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a>2. aggiungere e configurare il componente Grid Object Collection (script)

Aggiungere un componente **Grid Object Collection (script)** all'oggetto **3DObjectCollection** e configurarlo come segue:

* Modificare il **tipo di ordinamento** in **ordine figlio** per assicurarsi che gli oggetti figlio siano ordinati nell'ordine in cui sono stati inseriti nell'oggetto padre.

Quindi fare clic sul pulsante **Aggiorna raccolta** per applicare la nuova configurazione:

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step2-1.png)

## <a name="manipulating-3d-objects"></a>Manipolazione di oggetti 3D

In questa sezione verrà aggiunta la possibilità di modificare tutti gli oggetti 3D nel pannello creato nella sezione precedente. Inoltre, per gli oggetti prefabbricati, si consentirà agli utenti di raggiungere e acquisire questi oggetti con le mani tracciate. Si esamineranno quindi alcuni comportamenti di manipolazione che è possibile applicare agli oggetti.

Di seguito sono riportati i passaggi principali da eseguire per ottenere questo risultato:

1. Aggiungere il componente gestore modifiche (script) a tutti gli oggetti
2. Aggiungere il componente near interactionable (script) a oggetti prefabbricati
3. Configurare il componente di gestione della manipolazione (script)

> [!IMPORTANT]
> Per poter **modificare un oggetto**, l'oggetto deve disporre dei componenti seguenti:
>
> * Componente **Collider** , ad esempio, box Collider
> * Componente **gestione manipolazione (script)**
>
> Per poter **modificare** e **acquisire un oggetto con le lancette rilevate**, l'oggetto deve disporre dei componenti seguenti:
>
> * Componente **Collider** , ad esempio, box Collider
> * Componente **gestione manipolazione (script)**
> * Componente **near Interaction (script)**

### <a name="1-add-the-manipulation-handler-script-component-to-all-the-objects"></a>1. aggiungere il componente gestore modifiche (script) a tutti gli oggetti

Nella finestra gerarchia selezionare l'oggetto **Cheese** , tenere premuto il tasto **MAIUSC** , quindi selezionare l'oggetto **Cube () 2** e aggiungere il componente **handler (script) di manipolazione** a tutti gli oggetti:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step1-1.png)

> [!NOTE]
> Ai fini di questa esercitazione, i Collider sono già stati aggiunti ai prefabbricati. Per le primitive Unity, ad esempio gli oggetti cubo, il componente Collider viene aggiunto automaticamente quando viene creato l'oggetto. Nell'immagine precedente, i Collider sono rappresentati dai profili verdi. Per ulteriori informazioni sui Collider, è possibile visitare la documentazione di Unity <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> .

### <a name="2-add-the-near-interaction-grabbable-script-component-to-the-prefab-objects"></a>2. aggiungere il componente near Interaction (script) a oggetti prefabbricati

Nella finestra gerarchia selezionare l'oggetto **Cheese** , tenere premuto il tasto **MAIUSC** , quindi selezionare l'oggetto **TheModule** e aggiungere il componente **near interactionable (script)** a tutti gli oggetti:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step2-1.png)

### <a name="3-configure-the-manipulation-handler-script-component"></a>3. configurare il componente di gestione della manipolazione (script)

#### <a name="default-manipulation"></a>Manipolazione predefinita

Per l'oggetto **cubo** , lasciare tutte le proprietà predefinite per verificare il comportamento di manipolazione predefinito:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-1.png)

> [!TIP]
> Per reimpostare i valori predefiniti di un componente, è possibile selezionare l'icona delle impostazioni del componente e selezionare Reimposta.

#### <a name="restrict-manipulation-to-scale-only"></a>Limitazione della manipolazione solo per la scalabilità

Per l'oggetto **Cube (1)** , modificare **due tipi di manipolazione gestiti** in **scale** in modo da consentire solo all'utente di modificare le dimensioni dell'oggetto:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-2.png)

#### <a name="constrain-the-movement-to-a-fixed-distance-from-the-user"></a>Vincolare lo spostamento a una distanza fissa dall'utente

Per l'oggetto **Cube (2)** , modificare il **vincolo on Movement** per **correggere la distanza dall'Head** in modo che, quando l'oggetto viene spostato, rimanga alla stessa distanza dall'utente:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-3.png)

#### <a name="default-grabbable-manipulation"></a>Manipolazione predefinita

Per gli oggetti **Cheese**, **CoffeCup**e **EarthCore** , lasciare tutte le proprietà predefinite per poter provare il comportamento predefinito di manipolazione.

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-4.png)

#### <a name="remove-the-ability-of-far-manipulation"></a>Rimuovere la capacità di manipolazione

Per l'oggetto **Octa** , deselezionare la casella di controllo **Consenti modifiche a lungo** per fare in modo che l'utente possa interagire direttamente con l'oggetto usando le mani rilevate:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-5.png)

#### <a name="make-an-object-rotate-around-its-center"></a>Far ruotare un oggetto intorno al centro

Per l'oggetto **Platonic** modificare **una modalità di rotazione della mano vicino** a una modalità di rotazione della **mano** , per **ruotare** l'oggetto in modo da fare in modo che, quando l'utente ruota l'oggetto con una sola mano, ruoti intorno al centro dell'oggetto:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-6.png)

#### <a name="keep-movement-after-object-is-released"></a>Mantieni lo spostamento dopo il rilascio dell'oggetto

Per l'oggetto **TheModule** , aggiungere un componente **Rigidbody** per abilitare la fisica e quindi deselezionare la casella di controllo **USA gravità** in modo che l'oggetto non venga influenzato dalla gravità:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-7.png)

Tornare al componente del gestore di manipolazione (script), verificare che il **comportamento della versione** sia impostato su **Mantieni velocità** e **Mantieni velocità angolare** , in modo che una volta rilasciato l'oggetto dall'utente, lo spostamento continua:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-8.png)

Per ulteriori informazioni sul componente del gestore della manipolazione e sulle proprietà associate, è possibile visitare la guida del [gestore della manipolazione](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) nel portale della [documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="adding-bounding-boxes"></a>Aggiunta di rettangoli di delimitazione

I rettangoli di delimitazione rendono più semplice e intuitivo manipolare gli oggetti con una sola mano, sia per l'interazione vicina che per quella più lunga, fornendo handle che possono essere utilizzati per la scalabilità e la rotazione.

In questo esempio si aggiungerà un rettangolo di delimitazione all'oggetto EarthCore in modo che questo oggetto possa ora interagire con la manipolazione degli oggetti configurata nella sezione precedente, nonché ridimensionata e ruotata usando gli handle del rettangolo di delimitazione.

> [!IMPORTANT]
> Per poter utilizzare un rettangolo di **delimitazione**, è necessario che nell'oggetto siano presenti i componenti seguenti:
>
> * Componente **Collider** , ad esempio, box Collider
> * Componente del rettangolo di **delimitazione (script)**

### <a name="1-add-the-bounding-box-script-component-to-the-earthcore-object"></a>1. aggiungere il componente del rettangolo di delimitazione (script) all'oggetto EarthCore

Nella finestra di controllo selezionare l'oggetto **EarthCore** e aggiungere il componente **(script) del rettangolo** di selezione all'oggetto EarthCore:

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step1-1.png)

> [!NOTE]
> Le visualizzazioni del rettangolo di delimitazione vengono create in fase di esecuzione e pertanto non sono visibili prima di passare alla modalità di gioco.

### <a name="2-visualize-and-test-the-bounding-box-using-the-in-editor-simulation"></a>2. visualizzare e testare il rettangolo di delimitazione usando la simulazione in-Editor

Premere il pulsante Riproduci per attivare la modalità di gioco. Quindi tenere premuto la barra spaziatrice per visualizzare la mano e usare il mouse per interagire con il rettangolo di delimitazione:

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step2-1.png)

Per ulteriori informazioni sul componente del riquadro e sulle proprietà associate, è possibile visitare la guida del rettangolo di [delimitazione](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) nel [portale della documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="adding-touch-effects"></a>Aggiunta degli effetti tocco

In questo esempio verranno abilitati gli eventi da attivare quando si tocca un oggetto con la mano. In particolare, l'oggetto Octa verrà configurato per riprodurre un effetto acustico quando l'utente lo tocca.

Di seguito sono riportati i passaggi principali da eseguire per ottenere questo risultato:

1. Aggiungere un componente di origine audio all'oggetto
2. Aggiungere il componente near Interaction (script) per l'interazione all'oggetto
3. Aggiungere il componente tocco interazione mano (script) all'oggetto
4. Implementare l'evento on touch Started
5. Testare l'interazione con il tocco usando la simulazione in-Editor

> [!IMPORTANT]
> Per poter **attivare gli eventi di tocco**, l'oggetto deve disporre dei componenti seguenti:
>
> * Componente **Collider** , preferibilmente box Collider
> * Componente **near Interaction touchable (script)**
> * Componente **tocco interazione mano (script)**

> [!NOTE]
> Il componente script (Hand Interaction touch) non fa parte di MRTK. È stato importato con le risorse di questa esercitazione ed è stato originariamente incluso negli esempi di Unity Toolkit MixedReality.

### <a name="1-add-an-audio-source-component-to-the-object"></a>1. aggiungere un componente di origine audio all'oggetto

Nella finestra gerarchia selezionare l'oggetto **Octa** , aggiungere un componente di **origine audio** all'oggetto OCTA e quindi modificare **Blend spaziale** in 1 per abilitare l'audio spaziale:

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step1-1.png)

### <a name="2-add-the-near-interaction-touchable-script-component-to-the-object"></a>2. aggiungere il componente di prossimità interazione (script) per l'oggetto

Se l'oggetto **Octa** è ancora selezionato, aggiungere il componente **near Interaction (script)** per l'oggetto Octa, quindi fare clic sui pulsanti **Correggi limiti** e **Correggi centro** per aggiornare le proprietà del centro locale e dei limiti di near Interaction touchable (script) in modo che corrispondano a BoxCollider:

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step2-1.png)

### <a name="3-add-the-hand-interaction-touch-script-component-to-the-object"></a>3. aggiungere il componente script (Hand Interaction touch) all'oggetto

Con l'oggetto **Octa** ancora selezionato, aggiungere il componente **script (Hand Interaction touch)** all'oggetto Octa:

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step3-1.png)

### <a name="4-implement-the-on-touch-started-event"></a>4. implementare l'evento on touch Started

Sul componente **tocco interazione mano (script)** , fare clic sull'icona del piccolo **+** per creare un nuovo evento per **tocco avviato ()** . Configurare quindi l'oggetto **Octa** per ricevere l'evento e definire **audiosource. PlayOneShot** come azione da attivare:

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-1.png)

Passare a **asset** > **MixedRealityToolkit. SDK** > **StandardAssets** > Materials per visualizzare le clip audio fornite con MRTK e quindi assegnare una clip audio adatta al campo **clip** audio, ad esempio il clip audio MRTK_Gem:

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-2.png)

> [!TIP]
> Per un promemoria su come implementare gli eventi, è possibile fare riferimento alle istruzioni per i [movimenti di rilevamento della mano e i pulsanti interagiscono](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) .

### <a name="5-test-the-touch-interaction-using-the-in-editor-simulation"></a>5. testare l'interazione con il tocco usando la simulazione in-Editor

Premere il pulsante Riproduci per attivare la modalità di gioco. Quindi tenere premuto la barra spaziatrice per visualizzare la mano e usare il mouse per toccare l'oggetto OCTA e attivare l'effetto audio:

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step5-1.png)

> [!NOTE]
> Come è stato osservato durante il test dell'interazione del tocco e come illustrato nell'immagine precedente, il colore dell'oggetto Octa pulsava durante il suo tocco. Questo effetto è hardcoded nel componente tocco interazione mano (script) e non è il risultato della configurazione degli eventi completata nei passaggi precedenti.
>
> Se si vuole disabilitare questo effetto, è possibile, ad esempio, impostare come commento o la riga 32' TargetRenderer = GetComponentInChildren<Renderer>();' che restituirà il valore null rimanente di TargetRenderer e il colore non pulsa.

## <a name="congratulations"></a>Complimenti

In questa esercitazione si è appreso come organizzare gli oggetti 3D in una raccolta di griglie e come manipolare questi oggetti (ridimensionamento, rotazione e movimento) usando near Interaction (cattura diretta con le mani rilevate) e un'interazione di gran lunga (usando raggi di sguardi o raggi mano). Si è inoltre appreso come inserire le caselle di delimitazione intorno agli oggetti 3D e come usare e personalizzare gli handle nei rettangoli di delimitazione. Hai infine appreso come attivare eventi nel momento in cui viene toccato un oggetto.

[Lezione successiva: 6. esplorazione delle opzioni di input avanzate](mrlearning-base-ch5.md)

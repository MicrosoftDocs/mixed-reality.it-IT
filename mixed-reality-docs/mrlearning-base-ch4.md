---
title: Esercitazioni introduttive - 5. Interazione con oggetti 3D
description: Informazioni sul contenuto 3D e sulle esperienze utente di base, ad esempio l'organizzazione di oggetti 3D e cubi di delimitazione per la manipolazione di base.
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: 419b381c1240b2cc10708eab03245ed3aabfa859
ms.sourcegitcommit: 61291e83536c8cb2e8401a8e66060128ede35922
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416139"
---
# <a name="5-interacting-with-3d-objects"></a>5. Interazione con oggetti 3D

In questa esercitazione troverai informazioni sul contenuto 3D e sull'esperienza utente di base (ad esempio, l'organizzazione degli oggetti 3D come parte di una raccolta), sui cubi di delimitazione per la manipolazione di base, sull'interazione da vicino e da lontano e sui movimenti per toccare e afferrare con il tracciamento della mano.

## <a name="objectives"></a>Obiettivi

* Creare un pannello di oggetti 3D da usare per gli altri obiettivi di apprendimento
* Implementare i cubi di delimitazione
* Configurare oggetti 3D per la manipolazione di base, ad esempio spostare, ruotare e ridimensionare
* Esplorare l'interazione da vicino e da lontano
* Apprendere altri movimenti di tracciamento della mano, come afferrare e toccare

## <a name="importing-the-tutorial-assets"></a>Importazione degli asset dell'esercitazione

Scarica e importa il pacchetto personalizzato di Unity:

* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)

Dopo l'importazione degli asset dell'esercitazione, la finestra Project (Progetto) avrà un aspetto simile al seguente:

![mrlearning-base](images/mrlearning-base/tutorial4-section1-step1-1.png)

> [!TIP]
> Per rivedere la procedura di importazione di un pacchetto personalizzato di Unity, puoi fare riferimento alle istruzioni contenute in [Importare Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).

## <a name="decluttering-the-scene-view"></a>Rendere più chiara la vista della scena

Per rendere più agevole l'uso della scena, disattiva la **visibilità** per gli oggetti **Cube** e **ButtonCollection** facendo clic sull'icona a forma di **occhio** a sinistra degli oggetti. In questo modo l'oggetto viene nascosto nella finestra Scene (Scena) senza effetti sulla sua visibilità nel gioco:

![mrlearning-base](images/mrlearning-base/tutorial4-section2-step1-1.png)

> [!TIP]
> Per altre informazioni sui controlli per la visibilità nella scena e su come usarli per ottimizzare la vista e il flusso di lavoro della scena, puoi visitare la documentazione <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">corrispondente</a> di Unity.

## <a name="organizing-3d-objects-in-a-collection"></a>Organizzazione di oggetti 3D in una raccolta

In questa sezione creerai un pannello di oggetti 3D che verrà usato per esplorare varie modalità di interazione con gli oggetti 3D nelle sezioni seguenti di questa esercitazione. Più specificamente, configurerai gli oggetti 3D per il posizionamento in una griglia 3 x 3.

Come nella procedura usata per [creare in precedenza un pannello di pulsanti](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection), i passaggi principali da eseguire sono:

1. Associare gli oggetti 3D a un oggetto padre
2. Aggiungere e configurare il componente Grid Object Collection (Script) (Raccolta oggetti griglia - Script)

### <a name="1-parent-the-3d-objects-to-a-parent-object"></a>1. Associare gli oggetti 3D a un oggetto padre

Nella finestra Hierarchy (Gerarchia) **crea un oggetto vuoto**, assegnagli un nome appropriato, ad esempio **3DObjectCollection**, e collocalo in una posizione adatta, ad esempio X = 0, Y = -0.2, Z = 2.

Nella finestra Project (Progetto) passa ad **Assets** (Asset) > **MRTK.Tutorials.GettingStarted** > **Prefabs** (Prefab) e quindi **associa** a **3DObjectCollection** i prefab seguenti:

* Cheese
* CoffeeCup
* EarthCore
* Octa
* Platonic
* TheModule

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-1.png)

Nella finestra Hierarchy (Gerarchia) **crea tre cubi** come oggetti figlio di **3DObjectCollection** e in Transform (Trasformazione) imposta **Scale** (Scala) su X = 0.15, Y = 0.15, Z = 0.15.

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-2.png)

> [!TIP]
> Per rivedere come eseguire i passaggi sopra indicati, puoi fare riferimento all'esercitazione [Creazione dell'interfaccia utente e configurazione di Mixed Reality Toolkit](mrlearning-base-ch2.md).

Riposiziona i cubi in modo che sia possibile visualizzarli tutti:

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-3.png)

Nella finestra Project (Progetto) passa ad **Assets** (Asset) > **MixedRealityToolkit.SDK** > **StandardAssets** > **Materials** (Materiali) per visualizzare i materiali forniti con MRTK.

**Fai clic e trascina** un materiale appropriato sulla proprietà Element 0 (Elemento 0) in **Materials** (Materiali) nella sezione Mesh Renderer (Renderer mesh) di ogni cubo, ad esempio:

* MRTK_Standard_GlowingCyan
* MRTK_Standard_GlowingOrange
* MRTK_Standard_Green

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-4.png)

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a>2. Aggiungere e configurare il componente Grid Object Collection (Script) (Raccolta oggetti griglia - Script)

Aggiungi un componente **Grid Object Collection (Script)** (Raccolta oggetti griglia - Script) all'oggetto **3DObjectCollection** e configuralo come segue:

* Imposta **Sort Type** (Tipo ordinamento) su **Child Order** (Ordine figlio) per assicurarti che gli oggetti figlio vengano ordinati in base alla sequenza in cui li hai posizionati sotto l'oggetto padre

Fai quindi clic sul pulsante **Update Collection** (Aggiorna raccolta) per applicare la nuova configurazione:

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step2-1.png)

## <a name="manipulating-3d-objects"></a>Manipolazione di oggetti 3D

In questa sezione aggiungerai la possibilità di manipolare tutti gli oggetti 3D nel pannello creato nella sezione precedente. Inoltre, per gli oggetti prefab, consentirai agli utenti di afferrare tali oggetti con le mani tracciate. Potrai quindi esplorare alcuni comportamenti di manipolazione applicabili agli oggetti.

Di seguito sono riportati i passaggi principali da eseguire per ottenere questo risultato:

1. Aggiungere il componente Manipulation Handler (Script) (Gestore manipolazione - Script) a tutti gli oggetti
2. Aggiungere il componente Near Interaction Grabbable (Script) (Afferrabile con interazione da vicino - Script) agli oggetti prefab
3. Configurare il componente Manipulation Handler (Script) (Gestore manipolazione - Script)

> [!IMPORTANT]
> Per poter **manipolare un oggetto**, è necessario che l'oggetto abbia i componenti seguenti:
>
> * Componente **Collider** (Collisore), ad esempio un collisore cuboide
> * Componente **Manipulation Handler (Script)** (Gestore manipolazione - Script)
>
> Per poter **manipolare** e **afferrare un oggetto con le mani tracciate**, è necessario che l'oggetto abbia i componenti seguenti:
>
> * Componente **Collider** (Collisore), ad esempio un collisore cuboide
> * Componente **Manipulation Handler (Script)** (Gestore manipolazione - Script)
> * Componente **Near Interaction Grabbable (Script)** (Afferrabile con interazione da vicino - Script)

### <a name="1-add-the-manipulation-handler-script-component-to-all-the-objects"></a>1. Aggiungere il componente Manipulation Handler (Script) (Gestore manipolazione - Script) a tutti gli oggetti

Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **Cheese**, tieni premuto **MAIUSC** e seleziona l'oggetto **Cube (2)** , quindi aggiungi il componente **Manipulation Handler (Script)** (Gestore manipolazione - Script) a tutti gli oggetti:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step1-1.png)

> [!NOTE]
> Ai fini di questa esercitazione, i collisori sono già stati aggiunti ai prefab. Per i primitivi di Unity, quali gli oggetti Cube, il componente Collider (Collisore) viene aggiunto automaticamente quando viene creato l'oggetto. Nell'immagine precedente i collisori sono rappresentati dai contorni verdi. Per altre informazioni sui collisori, puoi visitare la documentazione <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">corrispondente</a> di Unity.

### <a name="2-add-the-near-interaction-grabbable-script-component-to-the-prefab-objects"></a>2. Aggiungere il componente Near Interaction Grabbable (Script) (Afferrabile con interazione da vicino - Script) agli oggetti prefab

Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **Cheese**, tieni premuto **MAIUSC** e seleziona l'oggetto **TheModule**, quindi aggiungi il componente **Near Interaction Grabbable (Script)** (Afferrabile con interazione da vicino - Script) a tutti gli oggetti:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step2-1.png)

### <a name="3-configure-the-manipulation-handler-script-component"></a>3. Configurare il componente Manipulation Handler (Script) (Gestore manipolazione - Script)

#### <a name="default-manipulation"></a>Manipolazione predefinita

Per l'oggetto **Cube**, lascia tutte le proprietà impostate sui rispettivi valori predefiniti per provare il comportamento di manipolazione predefinito:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-1.png)

> [!TIP]
> Per reimpostare un componente sui valori predefiniti, puoi fare clic sull'icona delle impostazioni del componente e quindi su Reset (Reimposta).

#### <a name="restrict-manipulation-to-scale-only"></a>Limitare la manipolazione al solo ridimensionamento

Per l'oggetto **Cube (1)** , imposta **Two Handed Manipulation Type** (Tipo di manipolazione con due mani) su **Scale** (Scala) per consentire all'utente solo di modificare le dimensioni dell'oggetto:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-2.png)

#### <a name="constrain-the-movement-to-a-fixed-distance-from-the-user"></a>Vincolare lo spostamento a una distanza fissa dall'utente

Per l'oggetto **Cube (2)** , imposta **Constraint On Movement** (Vincolo sullo spostamento) su **Fix Distance From Head** (Correggi distanza dalla testa) in modo che, se spostato, l'oggetto rimanga alla stessa distanza dall'utente:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-3.png)

#### <a name="default-grabbable-manipulation"></a>Manipolazione afferrabile predefinita

Per gli oggetti **Cheese**, **CoffeCup** e **EarthCore**, lascia tutte le proprietà impostate sui rispettivi valori predefiniti per provare il comportamento di manipolazione afferrabile predefinito:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-4.png)

#### <a name="remove-the-ability-of-far-manipulation"></a>Rimuovere la capacità di manipolazione da lontano

Per l'oggetto **Octa**, deseleziona la casella di controllo **Allow Far Manipulation** (Consenti manipolazione da lontano) in modo che l'utente possa interagire con l'oggetto solo direttamente usando le mani tracciate:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-5.png)

#### <a name="make-an-object-rotate-around-its-center"></a>Far ruotare un oggetto intorno al centro

Per l'oggetto **Platonic**, imposta **One Hand Rotation Mode Near** (Modalità di rotazione con una mano - Da vicino) e **One Hand Rotation Mode Far** (Modalità di rotazione con una mano - Da lontano) su **Rotate About Object Center** (Rotazione intorno al centro dell'oggetto) in modo che, quando l'utente ruota l'oggetto con una mano, questo ruoti intorno al suo centro:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-6.png)

#### <a name="keep-movement-after-object-is-released"></a>Mantenere lo spostamento dopo il rilascio dell'oggetto

Per l'oggetto **TheModule**, aggiungi un componente **Rigidbody** per abilitare gli effetti della fisica e quindi deseleziona la casella di controllo **Use Gravity** (Usa la gravità) in modo che sull'oggetto non influisca la forza di gravità:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-7.png)

Tornando al componente Manipulation Handler (Script) (Gestore manipolazione - Script), verifica che l'opzione **Release Behavior** (Comportamento al rilascio) sia impostata sia su **Keep Velocity** (Mantieni la velocità) che su **Keep Angular Velocity** (Mantieni la velocità angolare) in modo che, dopo essere stato rilasciato dalla mano dell'utente, l'oggetto continui a muoversi:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-8.png)

Per altre informazioni sul componente Manipulation Handler (Gestore manipolazione) e sulle relative proprietà associate, puoi visitare la guida su [tale gestore](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) nel [portale della documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="adding-bounding-boxes"></a>Aggiunta di cubi di delimitazione

I cubi di delimitazione consentono di manipolare gli oggetti con una mano in modo più semplice e intuitivo per l'interazione sia da vicino che da lontano, in quanto forniscono punti di manipolazione utilizzabili per il ridimensionamento e la rotazione.

In questo esempio aggiungerai un cubo di delimitazione all'oggetto EarthCore in modo che ora sia possibile interagire con tale oggetto usando la manipolazione configurata nella sezione precedente, nonché ridimensionarlo e ruotarlo usando i punti di manipolazione del cubo di delimitazione.

> [!IMPORTANT]
> Per poter usare un **cubo di delimitazione**, è necessario che l'oggetto abbia i componenti seguenti:
>
> * Componente **Collider** (Collisore), ad esempio un collisore cuboide
> * Componente **Bounding Box (Script)** (Cubo di delimitazione- Script)

### <a name="1-add-the-bounding-box-script-component-to-the-earthcore-object"></a>1. Aggiungere il componente Bounding Box (Script) (Cubo di delimitazione- Script) all'oggetto EarthCore

Nella finestra Inspector (Controllo) seleziona l'oggetto **EarthCore** e aggiungigli il componente **Bounding Box (Script)** (Cubo di delimitazione- Script):

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step1-1.png)

> [!NOTE]
> Le visualizzazioni del cubo di delimitazione vengono create in fase di runtime, pertanto non sono visibili prima di passare alla modalità di gioco.

### <a name="2-visualize-and-test-the-bounding-box-using-the-in-editor-simulation"></a>2. Visualizzare e provare il cubo di delimitazione usando la simulazione nell'editor

Fai clic sul pulsante Play (Esegui) per passare alla modalità di gioco. Quindi tieni premuta la barra spaziatrice per visualizzare la mano e usare il mouse per interagire con il cubo di delimitazione:

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step2-1.png)

Per altre informazioni sul componente Bounding Box (Cubo di delimitazione) e sulle relative proprietà associate, puoi visitare la guida su [tale componente](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) nel [portale della documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="adding-touch-effects"></a>Aggiunta di effetti di tocco

In questo esempio abiliterai l'attivazione di eventi al tocco di un oggetto con la mano. Più specificamente, configurerai l'oggetto Octa in modo che riproduca un effetto sonoro quando l'utente lo tocca.

Di seguito sono riportati i passaggi principali da eseguire per ottenere questo risultato:

1. Aggiungere un componente Audio Source (Origine audio) all'oggetto
2. Aggiungere il componente Near Interaction Touchable (Script) (Toccabile con interazione da vicino - Script) all'oggetto
3. Aggiungere il componente Hand Interaction Touch (Script) (Tocco con interazione manuale - Script) all'oggetto
4. Implementare l'evento On Touch Started (Avviato al tocco)
5. Provare l'interazione con tocco tramite la simulazione nell'editor

> [!IMPORTANT]
> Per poter **attivare gli eventi di tocco**, è necessario che l'oggetto abbia i componenti seguenti:
>
> * Componente **Collider** (Collisore), preferibilmente un collisore cuboide
> * Componente **Near Interaction Touchable (Script)** (Toccabile con interazione da vicino - Script)
> * Componente **Hand Interaction Touch (Script)** (Tocco con interazione manuale - Script)

> [!NOTE]
> Il componente Hand Interaction Touch (Script) (Tocco con interazione manuale - Script) non fa parte di MRTK. È stato importato con gli asset di questa esercitazione e originariamente era incluso negli esempi Unity di Mixed Reality Toolkit.

### <a name="1-add-an-audio-source-component-to-the-object"></a>1. Aggiungere un componente Audio Source (Origine audio) all'oggetto

Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **Octa**, aggiungigli un componente **Audio Source** (Origine audio) e quindi imposta **Spatial Blend** (Blend spaziale) su 1 per abilitare l'audio spaziale:

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step1-1.png)

### <a name="2-add-the-near-interaction-touchable-script-component-to-the-object"></a>2. Aggiungere il componente Near Interaction Touchable (Script) (Toccabile con interazione da vicino - Script) all'oggetto

Con l'oggetto **Octa** ancora selezionato, aggiungigli il componente **Near Interaction Touchable (Script)** (Toccabile con interazione da vicino - Script) e quindi fai clic sui pulsanti **Fix Bounds** (Correggi limiti) e **Fix Center** (Correggi centro) per aggiornare le proprietà relative ai limiti e al centro in locale di tale componente in modo che corrispondano a BoxCollider:

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step2-1.png)

### <a name="3-add-the-hand-interaction-touch-script-component-to-the-object"></a>3. Aggiungere il componente Hand Interaction Touch (Script) (Tocco con interazione manuale - Script) all'oggetto

Con l'oggetto **Octa** ancora selezionato, aggiungigli il componente **Hand Interaction Touch (Script)** (Tocco con interazione manuale - Script):

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step3-1.png)

### <a name="4-implement-the-on-touch-started-event"></a>4. Implementare l'evento On Touch Started (Avviato al tocco)

Nel componente **Hand Interaction Touch (Script)** (Tocco con interazione manuale - Script) fai clic sulla piccola icona **+** per creare un nuovo evento **On Touch Started ()** (Avviato al tocco). Quindi configura l'oggetto **Octa** per ricevere l'evento e definisci **AudioSource.PlayOneShot** come azione da attivare:

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-1.png)

Passa ad **Assets** (Asset) > **MixedRealityToolkit.SDK** > **StandardAssets** > Materials (Materiali) per visualizzare i clip audio forniti con MRTK e quindi assegna un clip audio appropriato al campo **Audio Clip** (Clip audio), ad esempio MRTK_Gem:

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-2.png)

> [!TIP]
> Per rivedere la procedura di implementazione degli eventi, puoi fare riferimento alle istruzioni contenute in [Movimenti di rilevamento della mano e pulsanti con supporto per interazioni](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons).

### <a name="5-test-the-touch-interaction-using-the-in-editor-simulation"></a>5. Provare l'interazione con tocco tramite la simulazione nell'editor

Fai clic sul pulsante Play (Esegui) per passare alla modalità di gioco. Quindi tieni premuta la barra spaziatrice per visualizzare la mano e usare il mouse per toccare l'oggetto Octa e attivare l'effetto sonoro:

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step5-1.png)

> [!NOTE]
> Come hai potuto notare quando hai provato l'interazione con tocco e come illustrato nell'immagine precedente, il colore dell'oggetto Octa si è messo a pulsare mentre l'oggetto veniva toccato. Questo effetto è hardcoded nel componente Hand Interaction Touch (Script) (Tocco con interazione manuale - Script) e non deriva dalla configurazione dell'evento completata nella procedura sopra descritta.
>
> Se vuoi disabilitare questo effetto, puoi ad esempio impostare come commento la riga 32 'TargetRenderer = GetComponentInChildren<Renderer>();' in modo che TargetRenderer rimanga null e il colore non pulsi.

## <a name="congratulations"></a>Lezione completata

In questa esercitazione hai appreso come organizzare gli oggetti 3D in una raccolta sotto forma di griglia e come manipolare tali oggetti (ridimensionamento, rotazione e spostamento) usando l'interazione da vicino (afferrando direttamente con le mani tracciate) e l'interazione da lontano (tramite i raggi dello sguardo o i raggi della mano). Hai anche appreso come delimitare gli oggetti 3D con cubi di delimitazione e come usare e personalizzare i punti di manipolazione presenti sui cubi di delimitazione. Hai infine appreso come attivare eventi nel momento in cui viene toccato un oggetto.

[Lezione successiva: 6. Esplorazione delle opzioni di input avanzate](mrlearning-base-ch5.md)

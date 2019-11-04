---
title: Input MR 213
description: Seguire questa esercitazione di codifica usando Unity, Visual Studio e auricolari immersivi per apprendere i dettagli dei controller di movimento.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, immersive, Motion controller, Academy, esercitazione
ms.openlocfilehash: e2199c3afed21f9396ed84f71093a8b2fb3bb23b
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438542"
---
>[!NOTE]
>Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.  Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.  Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.  Verranno mantenuti per continuare a usare i dispositivi supportati. Per HoloLens 2 è stata pubblicata [una nuova serie di esercitazioni](mrlearning-base.md) .

<br>

# <a name="mr-input-213-motion-controllers"></a>Input MR 213: controller di movimento

I controller di movimento nel mondo della realtà mista aggiungono un altro livello di interattività. Con i [controller di movimento](motion-controllers.md)è possibile interagire direttamente con gli oggetti in modo più naturale, in modo analogo alle interazioni fisiche nella vita reale, aumentando l'immersione e la soddisfazione nell'esperienza dell'app.

In MR input 213 gli eventi di input del controller di movimento vengono esaminati creando una semplice esperienza di disegno spaziale. Con questa app, gli utenti possono disegnare nello spazio tridimensionale con diversi tipi di pennelli e colori.

## <a name="topics-covered-in-this-tutorial"></a>Argomenti trattati in questa esercitazione

|![Topic1 MixedReality213](images/mr213-topic1.png)|![MixedReality213 Topic2](images/mr213-topic2.png)|![MixedReality213 Topic3](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|**Visualizzazione del controller**|**Eventi di input del controller**|**Controller e interfaccia utente personalizzati**|
|Informazioni su come eseguire il rendering dei modelli di controller di movimento in modalità di gioco e runtime di Unity.|Informazioni sui diversi tipi di eventi dei pulsanti e sulle relative applicazioni.|Informazioni su come sovrapporre gli elementi dell'interfaccia utente all'inizio del controller o personalizzarlo completamente.|

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td>Input MR 213: controller di movimento</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Prima di iniziare

### <a name="prerequisites"></a>Prerequisiti

Vedere l'elenco di controllo per l'installazione di auricolari immersivi in [Questa pagina](install-the-tools.md).

* Questa esercitazione richiede [Unity 2017.2.1 P2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)

### <a name="project-files"></a>File di progetto

* [Scaricare i file](https://github.com/Microsoft/MixedReality213/archive/master.zip) richiesti dal progetto ed estrarre i file sul desktop.

>[!NOTE]
>Se si vuole esaminare il codice sorgente prima del download, è [disponibile in GitHub](https://github.com/Microsoft/MixedReality213).

## <a name="unity-setup"></a>Configurazione di Unity

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a>Obiettivi

* Ottimizzare Unity per lo sviluppo di realtà mista di Windows
* Configurare la fotocamera della realtà mista
* Ambiente di installazione

### <a name="instructions"></a>Istruzioni

* Avvia Unity.
* Selezionare **Apri**.
* Passare al desktop e trovare la cartella **MixedReality213-Master** precedentemente non archiviata.
* Fare clic su **Seleziona cartella**.
* Al termine del caricamento dei file di progetto Unity, sarà possibile visualizzare l'editor di Unity.
* In Unity selezionare **File > impostazioni di compilazione**.

    ![MR213_BuildSettings](images/mr213-buildsettings-450px.png)

* Selezionare **piattaforma UWP (Universal Windows Platform)** nell'elenco **piattaforma** e fare clic sul pulsante **Switch Platform** .
* Impostare il dispositivo di destinazione su **qualsiasi dispositivo**
* Imposta tipo di compilazione su **D3D**
* Impostare SDK sull' **ultima versione installata**
* Verifica **progetti C# Unity**
    * In questo modo è possibile modificare i file di script nel progetto di Visual Studio senza ricompilare il progetto Unity.
* Fare clic su **Impostazioni lettore**.
* Nel pannello **Inspector** scorrere fino alla fine
* In impostazioni XR controllare la **realtà virtuale supportata**
* In Virtual Reality SDK selezionare **realtà mista di Windows**

    ![MR213_XRSettings](images/mr213-xrsettings-500px.png)

* Chiudi finestra **impostazioni di compilazione** .

### <a name="project-structure"></a>Struttura del progetto

Questa esercitazione USA **[mixed reality Toolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** . È possibile trovare le versioni in [Questa pagina](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).

![ProjectStructure](images/mr213-projectstructure-650px.png)

**Scene completate per il riferimento**

* Sono disponibili due scene Unity completate nella cartella **Scenes** .
    * **MixedReality213**: scena completata con pennello singolo
    * **MixedReality213Advanced**: scenario completato per la progettazione avanzata con più pennelli

**Nuova configurazione della scena per l'esercitazione**

* In Unity fare clic su **File > nuova scena**
* Elimina la **fotocamera principale** e la **luce direzionale**
* Dal **pannello progetto**, cercare e trascinare le seguenti prefabbricati nel pannello **gerarchia** :
    * Assets/HoloToolkit/input/prefabbricates/**MixedRealityCamera**
    * Assets/AppPrefabs/**Environment**

    ![Fotocamera e ambiente](images/mr213-cameraenvironment-300px.jpg)

* Nel Toolkit per realtà mista sono disponibili due prefabbricati della fotocamera:
    * **MixedRealityCamera. prefabbricator**: solo fotocamera
    * **MixedRealityCameraParent. prefabricable**: fotocamera + Teleporting + limite
    * In questa esercitazione si userà **MixedRealityCamera** senza funzionalità di Teleporting. Per questo motivo, è stata aggiunta una semplice prefabbricata dell' **ambiente** che contiene un piano di base per fare in modo che l'utente si trovi a terra.
    * Per altre informazioni sulla teleportazione con **MixedRealityCameraParent**, vedere [Advanced Design-Teleporting and locomotion](#advanced-design---teleportation-and-locomotion)

**Installazione di SKYBOX**

* Fare clic su **finestra > illuminazione impostazioni >**
* Fare clic sul cerchio sul lato destro del **campo materiale SKYBOX**
* Digitare ' Gray ' e selezionare **SkyboxGray** (assets/AppPrefabs/Support/Materials/SkyboxGray. mat)

    ![Impostazione di SKYBOX](images/mr123-skyboxsetting-400px.jpg)

* Selezionare l'opzione **SKYBOX** per visualizzare la sfumatura grigia assegnata SKYBOX

    ![Opzione interruttore SKYBOX](images/mr213-skyboxcheck-400px.jpg)

* La scena con MixedRealityCamera, Environment e SKYBOX grigio sarà simile alla seguente.

    ![Ambiente MixedReality213](images/mr213-environment-600px.jpg)

* Fare clic su **File > Salva scena come**
* **Salva** la scena nella cartella Scenes con qualsiasi nome

## <a name="chapter-1---controller-visualization"></a>Capitolo 1-Visualizzazione del controller

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a>Obiettivi

* Informazioni su come eseguire il rendering dei modelli di controller di movimento in modalità gioco di Unity e in fase di esecuzione.

La realtà mista di Windows fornisce un modello di controller animato per la visualizzazione del controller. È possibile adottare diversi approcci per la visualizzazione del controller nell'app:

* Impostazione predefinita: utilizzo del controller predefinito senza modifiche
* Ibrido: uso del controller predefinito, ma personalizzazione di alcuni elementi o sovrapposizione di componenti dell'interfaccia utente
* Sostituzione: uso del modello 3D personalizzato per il controller

In questo capitolo vengono fornite informazioni sugli esempi di queste personalizzazioni del controller.

### <a name="instructions"></a>Istruzioni

* Nel pannello **progetto** digitare **MotionControllers** nella casella di ricerca. È possibile trovarlo anche in assets/HoloToolkit/input/prefabrics/.
* Trascinare **MotionControllers** prefabbricate nel pannello **gerarchia** .
* Fare clic su **MotionControllers** prefabbricate nel pannello **gerarchia** .

**MotionControllers prefabbricato**

**MotionControllers** prefabbricate include uno script **MotionControllerVisualizer** che fornisce gli slot per i modelli di controller alternativi. Se si assegnano modelli 3D personalizzati, ad esempio una mano o una spada e si seleziona "Usa sempre il modello alternativo sinistro/destro", vengono visualizzati anziché il modello predefinito. Questo slot verrà usato nel capitolo 4 per sostituire il modello di controller con un pennello.

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

**Istruzioni**

* Nel pannello di **controllo** fare doppio clic su **MotionControllerVisualizer** script per visualizzare il codice in Visual Studio

**Script MotionControllerVisualizer**

Le classi **MotionControllerVisualizer** e **MotionControllerInfo** forniscono i mezzi per accedere & modificare i modelli di controller predefiniti. **MotionControllerVisualizer** sottoscrive l'evento **InteractionSourceDetected** di Unity e crea automaticamente un'istanza dei modelli di controller quando vengono trovati.

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

I modelli del controller vengono recapitati in base alla [specifica glTF](https://github.com/KhronosGroup/glTF). Questo formato è stato creato per fornire un formato comune, migliorando al tempo stesso il processo di trasmissione e decompressione degli asset 3D. In questo caso, è necessario recuperare e caricare i modelli di controller in fase di esecuzione, poiché si vuole rendere l'esperienza utente il più semplice possibile e non è garantita la versione dei controller di movimento che l'utente potrebbe usare. Questo corso, tramite il Toolkit di realtà mista, usa una versione del [progetto UnityGLTF](https://github.com/KhronosGroup/UnityGLTF)del gruppo Khronos.

Una volta che il controller è stato recapitato, gli script possono usare **MotionControllerInfo** per trovare le trasformazioni per elementi controller specifici, in modo che possano posizionarsi correttamente.

In un capitolo successivo si apprenderà come usare questi script per alleghi gli elementi dell'interfaccia utente ai controller.

*In alcuni script, i blocchi di codice vengono trovati con **#if. UNITY_EDITOR** o **UNITY_WSA**. Questi blocchi di codice vengono eseguiti solo nel runtime UWP quando si esegue la distribuzione in Windows. Questo perché il set di API usate dall'editor di Unity e dal runtime dell'app UWP sono diversi.*

* **Salva** la scena e fai clic sul pulsante **Riproduci** .

Sarà possibile visualizzare la scena con i controller di movimento nell'auricolare. È possibile visualizzare le animazioni dettagliate per i clic dei pulsanti, lo spostamento levetta e l'evidenziazione tocco touchpad.

![Impostazione predefinita visualizzazione MR213_Controller](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a>Capitolo 2-connessione di elementi dell'interfaccia utente al controller

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a>Obiettivi

* Informazioni sugli elementi dei controller di movimento
* Informazioni su come aggiungere oggetti a parti specifiche dei controller

In questo capitolo verrà illustrato come aggiungere elementi dell'interfaccia utente al controller che l'utente può facilmente accedere e modificare in qualsiasi momento. Si apprenderà anche come aggiungere una semplice interfaccia utente della selezione colori usando l'input del touchpad.

### <a name="instructions"></a>Istruzioni

* Nel pannello del **progetto** cercare script **MotionControllerInfo** .
* Nei risultati della ricerca fare doppio clic su **MotionControllerInfo** script per visualizzare il codice in Visual Studio.

**Script MotionControllerInfo**

Il primo passaggio consiste nel scegliere l'elemento del controller a cui si vuole aggiungere l'interfaccia utente. Questi elementi sono definiti in **ControllerElementEnum** in **MotionControllerInfo.cs**.

![MR213 MotionControllerElements](images/mr213-motioncontrollerelements-1000px.jpg)

* **Casa**
* **Menu**
* **Comprendere**
* **Levetta**
* **Selezionare**
* **Touchpad**
* **Puntamento di pose** : questo elemento rappresenta il suggerimento della direzione di avanzamento del controller.

**Istruzioni**

* Nel pannello del **progetto** cercare script **AttachToController** .
* Nei risultati della ricerca fare doppio clic su **AttachToController** script per visualizzare il codice in Visual Studio.

**Script AttachToController**

Lo script **AttachToController** fornisce un modo semplice per alleghire tutti gli oggetti a un elemento e a una manualità del controller specificati.

In **AttachElementToController ()** ,

* Controllare la manualità usando **MotionControllerInfo. manualità**
* Ottenere un elemento specifico del controller usando **MotionControllerInfo. TryGetElement ()**
* Dopo aver recuperato la trasformazione dell'elemento dal modello del controller, è necessario impostare come elemento padre l'oggetto sottostante e impostare la posizione locale dell'oggetto & rotazione su zero.

```cs
public MotionControllerInfo.ControllerElementEnum Element { get { return element; } }

private void AttachElementToController(MotionControllerInfo newController)
{
     if (!IsAttached && newController.Handedness == handedness)
     {
          if (!newController.TryGetElement(element, out elementTransform))
          {
               Debug.LogError("Unable to find element of type " + element + " under controller " + newController.ControllerParent.name + "; not attaching.");
               return;
          }

          controller = newController;

          SetChildrenActive(true);

          // Parent ourselves under the element and set our offsets
          transform.parent = elementTransform;
          transform.localPosition = positionOffset;
          transform.localEulerAngles = rotationOffset;
          if (setScaleOnAttach)
          {
               transform.localScale = scale;
          }

          // Announce that we're attached
          OnAttachToController();
          IsAttached = true;
     }
}
```

Il modo più semplice per usare lo script **AttachToController** consiste nell'ereditare da esso, come è stato fatto nel caso di **ColorPickerWheel.** È sufficiente eseguire l'override delle funzioni **OnAttachToController** e **OnDetatchFromController** per eseguire l'installazione o la ripartizione quando il controller viene rilevato/disconnesso.

**Istruzioni**

* Nel pannello **progetto** Digitare nella casella di ricerca **ColorPickerWheel**. È possibile trovarlo anche in assets/AppPrefabs/.
* Trascinare **ColorPickerWheel** prefabbricate nel pannello **gerarchia** .
* Fare clic su **ColorPickerWheel** prefabbricate nel pannello **gerarchia** .
* Nel pannello di **controllo** fare doppio clic su **ColorPickerWheel** script per visualizzare il codice in Visual Studio.

![ColorPickerWheel prefabbricato](images/mr213-colorpickerwheel-1000px.jpg)

**Script ColorPickerWheel**

Poiché **ColorPickerWheel** eredita **AttachToController**, Mostra la **manualità** e l' **elemento** nel pannello **Inspector** . L'interfaccia utente verrà collegata all'elemento touchpad sul controller di sinistra.

![Script ColorPickerWheel](images/mr213-attachtocontroller-300px.jpg)

**ColorPickerWheel** esegue l'override di **OnAttachToController** e **OnDetatchFromController** per sottoscrivere l'evento di input che verrà usato nel capitolo successivo per la selezione dei colori con input touchpad.

```cs
public class ColorPickerWheel : AttachToController, IPointerTarget
{
    protected override void OnAttachToController()
    {
        // Subscribe to input now that we're parented under the controller
        InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
    }

    protected override void OnDetachFromController()
    {
        Visible = false;

        // Unsubscribe from input now that we've detached from the controller
        InteractionManager.InteractionSourceUpdated -= InteractionSourceUpdated;
    }
    ...
}
```

* **Salva** la scena e fai clic sul pulsante **Riproduci** .

**Metodo alternativo per il fissaggio di oggetti ai controller**

È consigliabile che gli script ereditino da **AttachToController** ed eseguano l'override di **OnAttachToController**. Tuttavia, questo potrebbe non essere sempre possibile. Un'alternativa viene utilizzata come componente autonomo. Questa operazione può essere utile quando si vuole alleghi un prefabbricato esistente a un controller senza effettuare il refactoring degli script. È sufficiente che la classe attenda che sia impostato su true prima di eseguire qualsiasi installazione. Il modo più semplice per eseguire questa operazione consiste nell'usare una coroutine per "Start".

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a>Capitolo 3-uso dell'input di touchpad

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a>Obiettivi

* Informazioni su come ottenere gli eventi di dati di input di touchpad
* Informazioni su come usare le informazioni sulla posizione dell'asse del touchpad per l'esperienza dell'app

### <a name="instructions"></a>Istruzioni

* Nel pannello **gerarchia** fare clic su **ColorPickerWheel**
* Nel pannello **Inspector** , in **animatior**, fare doppio clic su **ColorPickerWheelController**
* Sarà possibile visualizzare la scheda **Animator** aperta

**Visualizzazione/occultamento dell'interfaccia utente con il controller di animazione di Unity**

Per mostrare e nascondere l'interfaccia utente di **ColorPickerWheel** con animazione, viene usato il [sistema di animazione di Unity](https://docs.unity3d.com/Manual/AnimationOverview.html). Impostando la proprietà **Visible** di **ColorPickerWheel**su true o false, i trigger **mostrano** e **nascondono** i trigger di animazione. I parametri **show** e **Hide** sono definiti nel controller di animazione **ColorPickerWheelController** .

![Controller animazione Unity](images/mr123-animationcontroller-550px.jpg)

**Istruzioni**

* Nel pannello **gerarchia** selezionare **ColorPickerWheel** prefabbricate
* Nel pannello di **controllo** fare doppio clic su **ColorPickerWheel** script per visualizzare il codice in Visual Studio

**Script ColorPickerWheel**

**ColorPickerWheel** sottoscrive l'evento **InteractionSourceUpdated** di Unity per ascoltare gli eventi del touchpad.

In **InteractionSourceUpdated ()** , lo script verifica prima di tutto che:

* è in realtà un evento touchpad (obj. state. **touchpadTouched**)
* ha origine dal controller sinistro (obj. state. Source. **manualità**)

Se entrambi sono true, la posizione del touchpad (obj. state. **touchpadPosition**) viene assegnato a **selectorPosition**.

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness && obj.state.touchpadTouched)
    {
        Visible = true;
        selectorPosition = obj.state.touchpadPosition;
    }
}
```

In **Update ()** , in base alla proprietà **Visible** , attiva i trigger Show e Hide Animation nel componente Animator della selezione colori

```cs
if (visible != visibleLastFrame)
{
    if (visible)
    {
        animator.SetTrigger("Show");
    }
    else
    {
        animator.SetTrigger("Hide");
    }
}
```

In **Update ()** , **selectorPosition** viene usato per eseguire il cast di un raggio nella mesh Collider della rotellina dei colori, che restituisce una posizione UV. Questa posizione può quindi essere usata per trovare la coordinata del pixel e il valore del colore della trama della rotellina dei colori. Questo valore è accessibile ad altri script tramite la proprietà **SelectedColor** .

![Rotellina selezione colori Raycasting](images/mr213-colorpickerwheel-raycast-700px.png)

```cs
...
    // Clamp selector position to a radius of 1
    Vector3 localPosition = new Vector3(selectorPosition.x * inputScale, 0.15f, selectorPosition.y * inputScale);
    if (localPosition.magnitude > 1)
    {
        localPosition = localPosition.normalized;
    }
    selectorTransform.localPosition = localPosition;

    // Raycast the wheel mesh and get its UV coordinates
    Vector3 raycastStart = selectorTransform.position + selectorTransform.up * 0.15f;
    RaycastHit hit;
    Debug.DrawLine(raycastStart, raycastStart - (selectorTransform.up * 0.25f));

    if (Physics.Raycast(raycastStart, -selectorTransform.up, out hit, 0.25f, 1 << colorWheelObject.layer, QueryTriggerInteraction.Ignore))
    {
        // Get pixel from the color wheel texture using UV coordinates
        Vector2 uv = hit.textureCoord;
        int pixelX = Mathf.FloorToInt(colorWheelTexture.width * uv.x);
        int pixelY = Mathf.FloorToInt(colorWheelTexture.height * uv.y);
        selectedColor = colorWheelTexture.GetPixel(pixelX, pixelY);
        selectedColor.a = 1f;
    }
    // Set the selector's color and blend it with white to make it visible on top of the wheel
    selectorRenderer.material.color = Color.Lerp (selectedColor, Color.white, 0.5f);
}
```

## <a name="chapter-4---overriding-controller-model"></a>Capitolo 4-override del modello di controller

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a>Obiettivi

* Informazioni su come eseguire l'override del modello di controller con un modello 3D personalizzato.

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a>Istruzioni

* Fare clic su **MotionControllers** nel pannello **gerarchia** .
* Fare clic sul cerchio sul lato destro del campo del **controller alternativo a destra** .
* Digitare **"BrushController**" e selezionare il prefabbricato dal risultato. È possibile trovarlo in assets/AppPrefabs/**BrushController**.
* Selezionare **Usa sempre il modello alternativo destro**

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

Il prefabbricato **BrushController** non deve essere incluso nel pannello **gerarchia** . Tuttavia, per estrarre i componenti figlio:

* Nel pannello **progetto** digitare **BrushController** e trascinare **BrushController** prefabbricate nel pannello **gerarchia** .

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

Il componente **Tip** è presente in **BrushController**. Si userà la relativa trasformazione per avviare/arrestare il disegno delle linee.

* Eliminare il **BrushController** dal pannello **gerarchia** .
* **Salva** la scena e fai clic sul pulsante **Riproduci** . Sarà possibile vedere il modello di pennello sostituito dal controller di movimento a destra.

## <a name="chapter-5---painting-with-select-input"></a>Capitolo 5-disegno con SELECT input

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a>Obiettivi

* Informazioni su come usare l'evento seleziona pulsante per avviare e arrestare un disegno a linee

### <a name="instructions"></a>Istruzioni

* Cercare **BrushController** prefabbricate nel pannello del **progetto** .
* Nel pannello di **controllo** fare doppio clic su **BrushController** script per visualizzare il codice in Visual Studio

**Script BrushController**

**BrushController** sottoscrive gli eventi **InteractionSourcePressed** e **InteractionSourceReleased** di InteractionManager. Quando viene attivato l'evento **InteractionSourcePressed** , la proprietà di **disegno** del pennello è impostata su true; Quando viene attivato l'evento **InteractionSourceReleased** , la proprietà di **disegno** del pennello è impostata su false.

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = true;
    }
}

private void InteractionSourceReleased(InteractionSourceReleasedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = false;
    }
}
```

Mentre il **disegno** è impostato su true, il pennello genererà punti in un **LineRenderer**Unity di cui è stata creata un'istanza. Un riferimento a questo prefabbricato viene mantenuto nel campo **prefabbricato Stroke** del pennello.

```cs
private IEnumerator DrawOverTime()
{
    // Get the position of the tip
    Vector3 lastPointPosition = tip.position;

    ...

    // Create a new brush stroke
    GameObject newStroke = Instantiate(strokePrefab);
    LineRenderer line = newStroke.GetComponent<LineRenderer>();
    newStroke.transform.position = startPosition;
    line.SetPosition(0, tip.position);
    float initialWidth = line.widthMultiplier;

    // Generate points in an instantiated Unity LineRenderer
    while (draw)
    {
        // Move the last point to the draw point position
        line.SetPosition(line.positionCount - 1, tip.position);
        line.material.color = colorPicker.SelectedColor;
        brushRenderer.material.color = colorPicker.SelectedColor;
        lastPointAddedTime = Time.unscaledTime;
        // Adjust the width between 1x and 2x width based on strength of trigger pull
        line.widthMultiplier = Mathf.Lerp(initialWidth, initialWidth * 2, width);

        if (Vector3.Distance(lastPointPosition, tip.position) > minPositionDelta || Time.unscaledTime > lastPointAddedTime + maxTimeDelta)
        {
            // Spawn a new point
            lastPointAddedTime = Time.unscaledTime;
            lastPointPosition = tip.position;
            line.positionCount += 1;
            line.SetPosition(line.positionCount - 1, lastPointPosition);
        }
        yield return null;
    }
}
```

Per usare il colore attualmente selezionato dall'interfaccia utente della rotellina della selezione colori, **BrushController** deve avere un riferimento all'oggetto **ColorPickerWheel** . Dato che viene creata un'istanza del prefabbricato **BrushController** in fase di esecuzione come controller sostitutivo, tutti i riferimenti agli oggetti nella scena dovranno essere impostati in fase di esecuzione. In questo caso si usa **GameObject. FindObjectOfType** per individuare il **ColorPickerWheel**:

```cs
private void OnEnable()
{
    // Locate the ColorPickerWheel
    colorPicker = FindObjectOfType<ColorPickerWheel>();

    // Assign currently selected color to the brush’s material color
    brushRenderer.material.color = colorPicker.SelectedColor;
    ...
}
```

* **Salva** la scena e fai clic sul pulsante **Riproduci** . Sarà possibile disegnare le linee e il disegno usando il pulsante Seleziona sul controller a destra.

## <a name="chapter-6---object-spawning-with-select-input"></a>Capitolo 6-generazione di oggetti con l'input selezionato

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a>Obiettivi

* Informazioni su come usare gli eventi di input del pulsante Seleziona e afferra
* Informazioni su come creare un'istanza di oggetti

### <a name="instructions"></a>Istruzioni

* Nel pannello **progetto** digitare **ObjectSpawner** nella casella di ricerca. È possibile trovarlo anche in assets/AppPrefabs/
* Trascinare **ObjectSpawner** prefabbricate nel pannello **gerarchia** .
* Fare clic su **ObjectSpawner** nel pannello **gerarchia** .
* **ObjectSpawner** dispone di un campo denominato **source color**.
* Dal pannello **gerarchia** trascinare il riferimento **ColorPickerWheel** in questo campo.

    ![Controllo generatore oggetti](images/mr213-objectspawnercolorpickerwheel-650px.jpg)

* Fare clic su **ObjectSpawner** prefabbricate nel pannello **gerarchia** .
* Nel pannello di **controllo** fare doppio clic su **ObjectSpawner** script per visualizzare il codice in Visual Studio.

**Script ObjectSpawner**

**ObjectSpawner** crea un'istanza delle copie di una mesh primitiva (cubo, sfera, cilindro) nello spazio. Quando viene rilevato un **InteractionSourcePressed** , controlla la manualità e se si tratta di un evento **InteractionSourcePressType. afferrare** o **InteractionSourcePressType. Select** .

Per un evento di **comprensione** , incrementa l'indice del tipo di mesh corrente (Sphere, Cube, Cylinder)

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    // Check handedness, see if it is left controller
    if (obj.state.source.handedness == handedness)
    {
        switch (obj.pressType)
        {
            // If it is Select button event, spawn object
            case InteractionSourcePressType.Select:
                if (state == StateEnum.Idle)
                {
                    // We've pressed the grasp - enter spawning state
                    state = StateEnum.Spawning;
                    SpawnObject();
                }
                break;

            // If it is Grasp button event
            case InteractionSourcePressType.Grasp:

                // Increment the index of current mesh type (sphere, cube, cylinder)
                meshIndex++;
                if (meshIndex >= NumAvailableMeshes)
                {
                    meshIndex = 0;
                }
                break;

            default:
                break;
        }
    }
}
```

Per un evento **Select** , in **SpawnObject ()** , viene creata un'istanza di un nuovo oggetto, senza padre e rilasciato nel mondo.

```cs
private void SpawnObject()
{
    // Instantiate the spawned object
    GameObject newObject = Instantiate(displayObject.gameObject, spawnParent);
    // Detatch the newly spawned object
    newObject.transform.parent = null;
    // Reset the scale transform to 1
    scaleParent.localScale = Vector3.one;
    // Set its material color so its material gets instantiated
    newObject.GetComponent<Renderer>().material.color = colorSource.SelectedColor;
}
```

**ObjectSpawner** utilizza **ColorPickerWheel** per impostare il colore del materiale dell'oggetto visualizzato. Agli oggetti generati viene assegnata un'istanza di questo materiale in modo che mantengano il colore.

* **Salva** la scena e fai clic sul pulsante **Riproduci** .

Sarà possibile modificare gli oggetti con il pulsante di selezione e generare oggetti con il pulsante Seleziona.

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a>Creare e distribuire app nel portale di realtà mista

* In Unity selezionare **File > impostazioni di compilazione**.
* Fare clic su **Aggiungi scene aperte** per aggiungere la scena corrente alle **scene nella compilazione**.
* Fai clic su **Compila**.
* Creare una **nuova cartella** denominata "app".
* Fare clic sulla cartella dell' **app** .
* Fare clic su **Seleziona cartella**.
* Quando si esegue Unity, viene visualizzata una finestra Esplora file.
* Aprire la cartella dell' **app** .
* Fare doppio clic sul file della soluzione Visual Studio **YourSceneName. sln** .
* Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione da debug a **Release** e da ARM a **x64**.
* Fare clic sulla freccia a discesa accanto al pulsante dispositivo e selezionare **computer locale**.
* Fare clic su **debug-> avvia senza eseguire debug** nel menu o premere **CTRL + F5**.

A questo punto l'app viene compilata e installata nel portale per la realtà mista. È possibile riavviarlo tramite il menu Start nel portale per la realtà mista.

## <a name="advanced-design---brush-tools-with-radial-layout"></a>Strumenti di progettazione avanzati con layout radiale

![MixedReality213 principale](images/mr213-main-600px.jpg)

In questo capitolo verrà illustrato come sostituire il modello di controller di movimento predefinito con una raccolta di strumenti di pennelli personalizzati. Per informazioni di riferimento, è possibile trovare la scena completa **MixedReality213Advanced** nella cartella **Scenes** .

### <a name="instructions"></a>Istruzioni

* Nel pannello **progetto** digitare **BrushSelector** nella casella di ricerca. È possibile trovarlo anche in assets/AppPrefabs/
* Trascinare **BrushSelector** prefabbricate nel pannello **gerarchia** .
* Per l'organizzazione, creare un GameObject vuoto denominato **pennelli**
* Trascinare i prefabbricati seguenti dal pannello del **progetto** in **pennelli**
    * Assets/AppPrefabs/**BrushFat**
    * Assets/AppPrefabs/**BrushThin**
    * Asset/AppPrefabs/**gomma**
    * Assets/AppPrefabs/**MarkerFat**
    * Assets/AppPrefabs/**MarkerThin**
    * Asset/AppPrefabs/**matita**

    ![Pennelli](images/mixedreality213-brushes-250px.png)

* Fare clic su **MotionControllers** prefabbricate nel pannello **gerarchia** .
* Nel pannello **Inspector** deselezionare **Usa sempre il modello alternativo a destra** nel Visualizzatore del **controller di movimento**
* Nel pannello **gerarchia** fare clic su **BrushSelector**
* **BrushSelector** dispone di un campo denominato **ColorPicker**
* Dal pannello **gerarchia** trascinare il **ColorPickerWheel** nel campo **ColorPicker** nel pannello **Inspector** .

    ![Assegnare ColorPickerWheel al selettore di pennelli](images/mr213-brushselector-500px.jpg)

* Nel pannello **gerarchia** , in **BrushSelector** prefabbricate, selezionare l'oggetto **menu** .
* Nel pannello **Inspector** , sotto il componente **LineObjectCollection** , aprire l'elenco a discesa **objects** Array. Vengono visualizzati 6 slot vuoti.
* Dal pannello **gerarchia** trascinare ognuna delle prefabbricate con l'elemento padre nei **pennelli** GameObject in questi slot in qualsiasi ordine. Assicurarsi di trascinare le prefabbricati dalla scena, non i prefabbricati nella cartella del progetto.

![Selettore di pennelli](images/mr213-brushselectorbrushes-700px.jpg)

**BrushSelector prefabbricato**

Poiché **BrushSelector** eredita **AttachToController**, Mostra la **manualità** e le opzioni degli **elementi** nel pannello **Inspector** . È stato selezionato il pulsante **destro** del mouse e si fa **riferimento a pose** per associare gli strumenti del pennello al controller destro con la direzione

**BrushSelector** utilizza due utilità:

* **Ellisse**: utilizzata per generare punti nello spazio lungo una forma ellisse.
* **LineObjectCollection**: distribuisce gli oggetti usando i punti generati da qualsiasi classe di riga (ad esempio, ellisse). Questo è ciò che verrà usato per inserire i pennelli lungo la forma ellisse.

In combinazione, è possibile usare queste utilità per creare un menu radiale.

**Script LineObjectCollection**

**LineObjectCollection** dispone di controlli per le dimensioni, la posizione e la rotazione degli oggetti distribuiti lungo la relativa riga. Questa operazione è utile per creare menu radiali come il selettore di pennelli. Per creare l'aspetto dei pennelli che aumentano da nulla quando si avvicinano alla posizione selezionata al centro, la curva **scalaogg** punta al centro e ai nastri in corrispondenza dei bordi.

**Script BrushSelector**

Nel caso di **BrushSelector**, è stato scelto di usare un'animazione procedurale. In primo luogo, i modelli di pennelli vengono distribuiti in un'ellisse dallo script **LineObjectCollection** . Quindi, ogni pennello è responsabile della gestione della propria posizione nella mano dell'utente in base al relativo valore **DisplayMode** , che cambia in base alla selezione. È stato scelto un approccio procedurale a causa dell'elevata probabilità che le transizioni di posizione del pennello vengano interrotte quando l'utente seleziona pennelli. Le animazioni Mecanim possono gestire le interruzioni normalmente, ma tendono a essere più complesse rispetto a una semplice operazione Lerp.

**BrushSelector** usa una combinazione di entrambi. Quando viene rilevato un input del touchpad, le opzioni del pennello diventano visibili e aumentano di livello lungo il menu radiale. Dopo un periodo di timeout (che indica che l'utente ha effettuato una selezione), le opzioni del pennello diminuiscono di nuovo, lasciando solo il pennello selezionato.

**Visualizzazione dell'input di touchpad**

Anche nei casi in cui il modello di controller è stato completamente sostituito, può essere utile visualizzare l'input sugli input del modello originale. In questo modo, le azioni dell'utente vengono instradate in realtà. Per il **BrushSelector** è stato scelto di rendere il touchpad brevemente visibile quando viene ricevuto l'input. Questa operazione è stata eseguita recuperando l'elemento touchpad dal controller, sostituendo il materiale con un materiale personalizzato, quindi applicando una sfumatura al colore del materiale basato sull'ultima volta in cui è stato ricevuto l'input del touchpad.

```cs
protected override void OnAttachToController()
{
    // Turn off the default controller's renderers
    controller.SetRenderersVisible(false);

    // Get the touchpad and assign our custom material to it
    Transform touchpad;
    if (controller.TryGetElement(MotionControllerInfo.ControllerElementEnum.Touchpad, out touchpad))
    {
        touchpadRenderer = touchpad.GetComponentInChildren<MeshRenderer>();
        originalTouchpadMaterial = touchpadRenderer.material;
        touchpadRenderer.material = touchpadMaterial;
        touchpadRenderer.enabled = true;
    }

    // Subscribe to input now that we're parented under the controller
    InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
}

private void Update()
{
    ...
    // Update our touchpad material
    Color glowColor = touchpadColor.Evaluate((Time.unscaledTime - touchpadTouchTime) / touchpadGlowLossTime);
    touchpadMaterial.SetColor("_EmissionColor", glowColor);
    touchpadMaterial.SetColor("_Color", glowColor);
    ...
}
```

**Selezione dello strumento pennello con input touchpad**

Quando il selettore di pennelli rileva l'input premuto del touchpad, controlla la posizione dell'input per determinare se si trovava a sinistra o a destra.

**Spessore tratto con selectPressedAmount**

Anziché l'evento **InteractionSourcePressType. Select** in **InteractionSourcePressed ()** , è possibile ottenere il valore analogo della quantità premuta tramite **selectPressedAmount**. Questo valore può essere recuperato in **InteractionSourceUpdated ()** .

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness)
    {
        if (obj.state.touchpadPressed)
        {
            // Check which side we clicked
            if (obj.state.touchpadPosition.x < 0)
            {
                currentAction = SwipeEnum.Left;
            }
            else
            {
                currentAction = SwipeEnum.Right;
            }

            // Ping the touchpad material so it gets bright
            touchpadTouchTime = Time.unscaledTime;
        }

        if (activeBrush != null)
        {
            // If the pressed amount is greater than our threshold, draw
            if (obj.state.selectPressedAmount >= selectPressedDrawThreshold)
            {
                activeBrush.Draw = true;
                activeBrush.Width = ProcessSelectPressedAmount(obj.state.selectPressedAmount);
            }
            else
            {
                // Otherwise, stop drawing
                activeBrush.Draw = false;
                selectPressedSmooth = 0f;
            }
        }
    }
}
```

**Script di gomma**

**Eraser** è un tipo speciale di pennello che esegue l'override della funzione **DrawOverTime ()** del **pennello**di base. Mentre il disegno è true, la gomma viene controllata per verificare se il suggerimento si interseca con eventuali tratti di pennelli esistenti. In tal caso, vengono aggiunti a una coda per la compattazione e l'eliminazione.

## <a name="advanced-design---teleportation-and-locomotion"></a>Progettazione avanzata: teleporte e locomozione

Se si vuole consentire all'utente di spostarsi nella scena con la teleportazione con levetta, usare **MixedRealityCameraParent** anziché **MixedRealityCamera**. È anche necessario aggiungere **InputManager** e **DefaultCusor**. Poiché **MixedRealityCameraParent** include già **MotionControllers** e **Boundary** come componenti figlio, è necessario rimuovere i prefabbricati **MotionControllers** e **Environment** esistenti.

### <a name="instructions"></a>Istruzioni

* Nel pannello **gerarchia** eliminare **MixedRealityCamera**, **Environment** e **MotionControllers**
* Dal **pannello progetto**, cercare e trascinare le seguenti prefabbricati nel pannello **gerarchia** :
    * Assets/AppPrefabs/input/prefabbricates/**MixedRealityCameraParent**
    * Assets/AppPrefabs/input/prefabbricates/**InputManager**
    * Assets/AppPrefabs/input/prefabrics/Cursor/**DefaultCursor**

    ![Padre della fotocamera della realtà mista](images/mr213-cameraparent-300px.png)

* Nel pannello **gerarchia** fare clic su **Gestione input** .
* Nel pannello **Inspector** scorrere verso il basso fino alla sezione **semplice selettore puntatore singolo**
* Dal pannello **gerarchia** trascinare **DefaultCursor** in campo **cursore**

    ![Assegnazione di DefaultCursor](images/mr213-defaultcursor-500px.png)

* **Salva** la scena e fai clic sul pulsante **Riproduci** . Sarà possibile usare levetta per ruotare verso sinistra o verso destra o Teleport.

## <a name="the-end"></a>La fine

Questa è la fine di questa esercitazione. Si è appreso quanto segue:

* Come usare i modelli di motion controller in modalità di gioco e runtime di Unity.
* Come usare tipi diversi di eventi dei pulsanti e le relative applicazioni.
* Come sovrapporre gli elementi dell'interfaccia utente all'inizio del controller o personalizzarlo completamente.

A questo punto è possibile iniziare a creare un'esperienza immersiva con i controller di movimento.

## <a name="completed-scenes"></a>Scene completate

* Nel pannello del **progetto** di Unity fare clic sulla cartella **Scenes** .
* Sono disponibili due Unity sceens **MixedReality213** e **MixedReality213Advanced**.
    * **MixedReality213**: scena completata con pennello singolo
    * **MixedReality213Advanced**: sequenza completa con più pennelli con l'esempio di pressione del pulsante di selezione

## <a name="see-also"></a>Vedi anche

* [File di progetto MR input 213](https://github.com/Microsoft/MixedReality213)
* [Toolkit di realtà mista-scena di test del controller di movimento](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [Toolkit per realtà mista-meccanismi di recupero](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [Linee guida per lo sviluppo di controller di movimento](motion-controllers.md)

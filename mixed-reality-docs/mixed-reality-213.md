---
title: Input MR 213
description: Seguire questa esercitazione di scrittura del codice grazie a Unity, Visual Studio e auricolari coinvolgenti per informazioni dettagliate sui controller di movimento.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, coinvolgenti, movimento controller, academy, esercitazione
ms.openlocfilehash: 85449795a4fb3d182101cb5b4c4ce3fe85b009c0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604700"
---
>[!NOTE]
>Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.  Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.  Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.  Essi verranno mantenute per continuare a utilizzare i dispositivi supportati. Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.  Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.

<br>

# <a name="mr-input-213-motion-controllers"></a>Input di MR 213: Controller di movimento

I controller di movimento in tutto il mondo delle realtà mista aggiungono un ulteriore livello di interattività. Con [controller di movimento](motion-controllers.md), possiamo direttamente interagire con gli oggetti in modo più naturale, simile alle interazioni fisiche in uno scenario reale, l'aumento di full immersion e maggiori opportunità di sorprendere durante l'utilizzo di app.

MR 213 Input, verrà illustra gli eventi di input del movimento controller tramite la creazione di un'esperienza semplice disegno spaziale. Con questa app, gli utenti possono disegnare nello spazio tridimensionale con vari tipi di pennelli e i colori.

## <a name="topics-covered-in-this-tutorial"></a>Argomenti trattati in questa esercitazione

|![MixedReality213 Topic1](images/mr213-topic1.png)|![MixedReality213 Topic2](images/mr213-topic2.png)|![MixedReality213 Topic3](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|**Visualizzazione controller**|**Eventi di input controller**|**Controller personalizzato e l'interfaccia utente**|
|Informazioni su come eseguire il rendering di modelli di controller di movimento in modalità di gioco Unity e runtime.|Comprendere i diversi tipi di eventi del pulsante e le relative applicazioni.|Informazioni su come sovrimpressione elementi dell'interfaccia utente nella parte superiore del controller o completamente personalizzarlo.|

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></th>
</tr><tr>
<td>Input di MR 213: Controller di movimento</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Prima di iniziare

### <a name="prerequisites"></a>Prerequisiti

Vedere l'elenco di controllo di installazione per auricolari immersive sul [questa pagina](install-the-tools.md).

* Questa esercitazione richiede [2017.2.1p2 Unity](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)

### <a name="project-files"></a>File di progetto

* [Scaricare i file](https://github.com/Microsoft/MixedReality213/archive/master.zip) necessarie per il progetto ed estrarre i file sul desktop.

>[!NOTE]
>Se si desidera esaminare il codice sorgente prima di scaricare, ha [disponibile in GitHub](https://github.com/Microsoft/MixedReality213).

## <a name="unity-setup"></a>Programma di installazione di Unity

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a>Obiettivi

* Ottimizzare lo sviluppo di Unity per realtà mista di Windows
* Il programma di installazione realtà mista fotocamera
* Configurare l'ambiente

### <a name="instructions"></a>Istruzioni

* Avviare Unity.
* Selezionare **aperto**.
* Passare al Desktop e trovare il **MixedReality213-master** cartella precedentemente non archiviati.
* Fare clic su **Seleziona cartella**.
* Una volta Unity ha terminato di caricare i file di progetto, sarà possibile visualizzare l'editor di Unity.
* In Unity, selezionare **File > Build Settings**.

![MR213_BuildSettings](images/mr213-buildsettings-450px.png)
* Selezionare **Universal Windows Platform** nel **piattaforma** elenco e fare clic sui **commutatore piattaforma** pulsante.
* Impostare il dispositivo di destinazione **qualsiasi dispositivo**
* Impostare il tipo di compilazione su **D3D**
* Impostare SDK su **installata più recente**
* Controllare **Unity C# progetti**
    * Ciò permette di che modificare i file di script nel progetto di Visual Studio senza ricompilare il progetto Unity.
* Fare clic su **le impostazioni del giocatore**.
* Nel **Inspector** pannello, scorrere fino alla parte inferiore
* XR impostazioni controllare **supportato di realtà virtuale**
* Nel SDK di realtà virtuale, selezionare **realtà mista di Windows**

![MR213_XRSettings](images/mr213-xrsettings-500px.png)
* Chiusura **Build Settings** finestra.

### <a name="project-structure"></a>Struttura del progetto

Questa esercitazione viene usato  **[Toolkit di realtà mista - Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)**. È possibile trovare le versioni sul [questa pagina](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).

![ProjectStructure](images/mr213-projectstructure-650px.png)

**Scene completate per riferimento**
* Si troveranno due scene Unity completate sotto **scene** cartella.
    * **MixedReality213**: Completato scena con pennello singolo
    * **MixedReality213Advanced**: Completato scena per progettazione avanzata con più pennelli

**Nuova scena il programma di installazione per l'esercitazione**
* In Unity, fare clic su **File > nuova scena**
* Eliminare **fotocamera principale** e **luce direzionale**
* Dal **pannello progetto**, la ricerca e trascinare il prefabs seguenti nel **gerarchia** pannello:
    * Assets/HoloToolkit/Input/Prefabs/**MixedRealityCamera**
    * Assets/AppPrefabs/**Environment**

![Fotocamere e ambiente](images/mr213-cameraenvironment-300px.jpg)
* Esistono due prefabs fotocamera nel Toolkit di realtà mista:
    * **MixedRealityCamera.prefab**: Solo della fotocamera
    * **MixedRealityCameraParent.prefab**: Fotocamera + teletrasporto + limite
    * In questa esercitazione si userà **MixedRealityCamera** senza teletrasporto funzionalità. Per questo motivo, abbiamo aggiunto semplice **ambiente** prefab che contiene un piano di base per rendere l'utente ritiene terra.
    * Per altre informazioni su con il teletrasporto **MixedRealityCameraParent**, vedere [Advanced design - teletrasporto e locomotion](#advanced-design---teleportation-and-locomotion)

**Programma di installazione skybox**
* Fare clic su **finestra > illuminazione > Impostazioni**
* Fare clic sul cerchio sul lato destro del **campo Skybox materiale**
* Digitare "gray" e selezionare **SkyboxGray**

(Assets/AppPrefabs/Support/Materials/SkyboxGray.mat)

![Impostazione skybox](images/mr123-skyboxsetting-400px.jpg)
* Controllare **Skybox** possibilità di essere in grado di vedere assegnato skybox della sfumatura di colore grigio

![Attiva/Disattiva skybox opzione](images/mr213-skyboxcheck-400px.jpg)
* La scena con MixedRealityCamera, ambiente e skybox grigio avrà un aspetto simile al seguente.

![Ambiente MixedReality213](images/mr213-environment-600px.jpg)
* Fare clic su **File > Salva scena come**
* **Salvare** scena nella cartella di scene con qualsiasi nome

## <a name="chapter-1---controller-visualization"></a>Capitolo 1 - visualizzazione Controller

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a>Obiettivi

* Informazioni su come eseguire il rendering di modelli di controller in modalità di gioco Unity e in fase di esecuzione di movimento.

Realtà mista di Windows fornisce un modello animato controller per la visualizzazione di controller. Esistono diversi approcci per la visualizzazione controller nell'app:
* Default - tramite il controller predefinito senza modifiche
* Ibrido - usando controller predefinito, ma la personalizzazione di alcuni dei suoi elementi o la sovrapposizione di componenti dell'interfaccia utente
* Sostituzione - usare il proprio personalizzato un modello 3D per il controller

In questo capitolo, si apprenderanno informazioni sugli esempi di queste personalizzazioni di controller.

### <a name="instructions"></a>Istruzioni

* Nel **Project** panel, digitare **MotionControllers** nella casella di ricerca. È anche possibile trovarlo in asset/HoloToolkit/Input/Prefabs /.
* Trascinare il **MotionControllers** prefab nel **gerarchia** pannello.
* Fare clic sui **MotionControllers** prefab nel **gerarchia** pannello.

**Prefab MotionControllers**

**MotionControllers** prefab ha un **MotionControllerVisualizer** script che fornisce gli slot per i modelli di controller alternativo. Se si assegna i tuoi modelli 3D personalizzati, ad esempio una mano o una sua spada per il e controllare 'Sempre usare alternative sinistra/destra Model', si verrà visualizzato invece il modello predefinito. Si userà questo slot nel capitolo 4 per sostituire il modello controller con un pennello.

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

**Istruzioni**
* Nel **Inspector** del pannello, fare doppio clic **MotionControllerVisualizer** script per visualizzare il codice in Visual Studio

**Script MotionControllerVisualizer**

Il **MotionControllerVisualizer** e **MotionControllerInfo** classi forniscono i mezzi per accedere e modificare i modelli di controller predefinito. **MotionControllerVisualizer** sottoscrive di Unity **InteractionSourceDetected** eventi e crea automaticamente modelli controller quando vengono individuate.

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

I modelli di controller vengano recapitati in base alla [la specifica glTF](https://github.com/KhronosGroup/glTF). Questo formato è stato creato per offrire un formato comune, migliorando il processo dietro la trasmissione e la decompressione automaticamente gli asset 3D. In questo caso, è necessario recuperare e caricare i modelli di controller in fase di esecuzione perché vogliamo migliorare l'esperienza dell'utente più semplice possibile, e non è possibile garantire quale versione del controller di movimento l'utente potrebbe essere utilizzato. Questo corso, tramite il Toolkit di realtà mista, utilizza una versione del gruppo di Khronos [UnityGLTF progetto](https://github.com/KhronosGroup/UnityGLTF).

Una volta che il controller è stato recapitato, gli script possono utilizzare **MotionControllerInfo** per trovare le trasformazioni per gli elementi di un controller specifico in modo che è possibile posizionarsi in modo corretto.

In un capitolo successivo, si apprenderà come usare questi script per collegare gli elementi dell'interfaccia utente per i controller.

*In alcuni alfabeti, sono disponibili i blocchi di codice con **#if! UNITY_EDITOR** oppure **UNITY_WSA**. Questi blocchi di codice eseguiti solo sul runtime di UWP durante la distribuzione in Windows. Questo avviene perché il set di API utilizzate dall'editor di Unity e dal runtime di app UWP sono diversi.*
* **Salvare** di scena e selezionare il **Riproduci** pulsante.

Sarà in grado di visualizzare la scena con i controller di movimento nelle cuffie. È possibile visualizzare dettagliate animazioni per clic sui pulsanti, spostamento thumbstick ed evidenziazione touch touchpad.

![MR213_Controller visualizzazione predefinita](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a>Capitolo 2 - associare elementi dell'interfaccia utente per il controller

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a>Obiettivi

* Informazioni sugli elementi dei controller di movimento
* Informazioni su come connettere gli oggetti a parti specifiche dei controller

In questo capitolo, si apprenderà come aggiungere elementi dell'interfaccia utente per il controller che l'utente può accedere e modificare in qualsiasi momento facilmente. Si apprenderà anche come aggiungere una selezione colori semplice interfaccia utente usando il touchpad di input.

### <a name="instructions"></a>Istruzioni

* Nel **Project** del pannello, cercare **MotionControllerInfo** script.
* Dai risultati della ricerca, fare doppio clic **MotionControllerInfo** script per visualizzare il codice in Visual Studio.

**Script MotionControllerInfo**

Il primo passaggio consiste nello scegliere quale elemento del controller l'interfaccia utente a cui connettersi. Questi elementi sono definiti nello **ControllerElementEnum** nelle **MotionControllerInfo.cs**.

![MR213 MotionControllerElements](images/mr213-motioncontrollerelements-1000px.jpg)
* **Home**
* **Menu**
* **Afferrare**
* **Thumbstick**
* **Selezionare**
* **Touchpad**
* **Puntamento posa** : questo elemento rappresenta la punta del controller che puntano direzione in avanti.

**Istruzioni**
* Nel **Project** del pannello, cercare **AttachToController** script.
* Dai risultati della ricerca, fare doppio clic **AttachToController** script per visualizzare il codice in Visual Studio.

**Script AttachToController**

Il **AttachToController** script fornisce un modo semplice per collegare tutti gli oggetti di una mano del controller specificato e un elemento.

In **AttachElementToController()**,
* Controllare con mano **MotionControllerInfo.Handedness**
* Ottenere l'elemento specifico di controller usando **MotionControllerInfo.TryGetElement()**
* Dopo aver recuperato l'elemento trasformano dal modello di controller, padre dell'oggetto posizionato sotto il e impostare la posizione locale e rotazione dell'oggetto su zero.

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

Il modo più semplice per usare **AttachToController** script consiste nell'ereditare da quest'ultimo, come illustrato nel caso di **ColorPickerWheel.** È sufficiente eseguire l'override di **OnAttachToController** e **OnDetatchFromController** funzioni per eseguire il programma di installazione / scomposizione quando il controller è rilevato o disconnesso.

**Istruzioni**
* Nel **Project** panel, digitare nella casella di ricerca **ColorPickerWheel**. È anche possibile trovarlo in asset/AppPrefabs /.
* Trascinare **ColorPickerWheel** prefab nel **gerarchia** pannello.
* Fare clic sui **ColorPickerWheel** prefab nel **gerarchia** pannello.
* Nel **Inspector** del pannello, fare doppio clic **ColorPickerWheel** Script per visualizzare il codice in Visual Studio.

![Prefab ColorPickerWheel](images/mr213-colorpickerwheel-1000px.jpg)

**Script ColorPickerWheel**

Poiché **ColorPickerWheel** eredita **AttachToController**, Mostra **mano** e **elemento** nel  **Inspector** pannello. È l'interfaccia utente verrà collegamento all'elemento Touchpad nel controller a sinistra.

![Script ColorPickerWheel](images/mr213-attachtocontroller-300px.jpg)

**ColorPickerWheel** esegue l'override di **OnAttachToController** e **OnDetatchFromController** per sottoscrivere l'evento di input che verrà usato nel capitolo successivo per la selezione di colore con touchpad di input.

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
* **Salvare** di scena e selezionare il **Riproduci** pulsante.

**Metodo alternativo per la connessione di oggetti per i controller**

È consigliabile che gli script di ereditano **AttachToController** ed eseguire l'override **OnAttachToController**. Tuttavia, ciò potrebbe non essere sempre possibile. In alternativa lo usa come componente autonomo. Ciò risulta utile quando si desidera collegare un prefab esistente a un controller senza eseguire il refactoring gli script. È sufficiente definire la classe attendere IsAttached sia impostato su true prima di eseguire qualsiasi programma di installazione. Il modo più semplice per eseguire questa operazione consiste nell'usare una coroutine per 'Start'.

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a>Capitolo 3 - uso di input touchpad

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a>Obiettivi

* Informazioni su come ottenere gli eventi di dati di input touchpad
* Informazioni su come usare le informazioni sulla posizione di asse touchpad per l'esperienza di app

### <a name="instructions"></a>Istruzioni

* Nel **gerarchia** del pannello, fare clic su **ColorPickerWheel**
* Nel **Inspector** nel pannello **Animatior**, fare doppio clic **ColorPickerWheelController**
* Sarà in grado di visualizzare **animatore** scheda aperta

**Interfaccia utente di mostrare/nascondere con controller di animazione di Unity**

Per mostrare e nascondere il **ColorPickerWheel** dell'interfaccia utente con un'animazione, utilizziamo [sistema di animazione di Unity](https://docs.unity3d.com/Manual/AnimationOverview.html). Impostando il **ColorPickerWheel**del **Visible** proprietà su true o false trigger **Mostra** e **nascondere** trigger animazione. **Mostrare** e **Nascondi** i parametri sono definiti nel **ColorPickerWheelController** controller dell'animazione.

![Controller di animazione di Unity](images/mr123-animationcontroller-550px.jpg)

**Istruzioni**
* Nel **gerarchia** Pannello di selezione **ColorPickerWheel** prefab
* Nel **Inspector** del pannello, fare doppio clic **ColorPickerWheel** script per visualizzare il codice in Visual Studio

**Script ColorPickerWheel**

**ColorPickerWheel** sottoscrive di Unity **InteractionSourceUpdated** evento da ascoltare gli eventi touchpad.

Nelle **InteractionSourceUpdated()**, lo script prima controlla per verificare che l'it:
* è effettivamente un evento touchpad (obj.state. **touchpadTouched**)
* proveniente dal controller di sinistra (obj.state.source. **mano**)

Se entrambi sono true, posizionare il touchpad (obj.state. **touchpadPosition**) viene assegnato a **selectorPosition**.

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

Nelle **Update ()**, in base **visibile** proprietà, l'avviso si attiverà mostrare e nascondere i trigger animazione nel componente animatore del controllo di selezione colore

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

Nelle **Update ()**, **selectorPosition** viene utilizzato per eseguire il cast di un raggio in collider mesh del selettore colori, che restituisce una posizione UV. Questa posizione è quindi utilizzabile per trovare la coordinata in pixel e valore di trama del selettore colori del colore. Questo valore è accessibile da altri script tramite il **SelectedColor** proprietà.

![Colore selezione rotellina Raycasting](images/mr213-colorpickerwheel-raycast-700px.png)

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

## <a name="chapter-4---overriding-controller-model"></a>Capitolo 4 - eseguire l'override di model controller

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a>Obiettivi

* Informazioni su come eseguire l'override del modello controller con un modello 3D di personalizzati.

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a>Istruzioni

* Fare clic su **MotionControllers** nel **gerarchia** pannello.
* Fare clic sul cerchio sul lato destro del **alternativo destra Controller** campo.
* Digitare **' BrushController**' e selezionare il prefab dal risultato. È possibile trovarla nel Assets/AppPrefabs/**BrushController**.
* Controllare **sempre usare alternativo modello appropriato**

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

Il **BrushController** prefab non deve essere incluso nel **gerarchia** pannello. Tuttavia, per estrarre i componenti figlio:
* Nel **progetto** panel, digitare **BrushController** trascinare **BrushController** prefab nel **gerarchia** pannello.

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

Si noterà il **suggerimento** componente nelle **BrushController**. Si userà la trasformazione corrispondente per l'avvio/arresto disegno di linee.
* Eliminare il **BrushController** dalle **gerarchia** pannello.
* **Salvare** di scena e selezionare il **Riproduci** pulsante. Sarà in grado di visualizzare che il modello di pennello sostituito il controller di movimento a destra.

## <a name="chapter-5---painting-with-select-input"></a>Disegno con l'istruzione Select di capitolo 5 - input

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a>Obiettivi

* Informazioni su come usare l'evento del pulsante Seleziona per avviare e arrestare un disegno di linee

### <a name="instructions"></a>Istruzioni

* Ricerca **BrushController** prefab nel **progetto** pannello.
* Nel **Inspector** del pannello, fare doppio clic **BrushController** Script per visualizzare il codice in Visual Studio

**Script BrushController**

**BrushController** sottoscrive il InteractionManager **InteractionSourcePressed** e **InteractionSourceReleased** gli eventi. Quando **InteractionSourcePressed** evento viene generato, il pennello **disegnare** viene impostata su true; quando **InteractionSourceReleased** evento viene generato, il pennello **Disegnare** proprietà è impostata su false.

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

Sebbene **disegnare** è impostata su true, il pennello genereranno i punti in un'istanza Unity **LineRenderer**. Un riferimento a questa prefab viene mantenuto nel pennello **Stroke Prefab** campo.

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

Usare il colore attualmente selezionato dalla rotellina di selezione dell'interfaccia utente, colore **BrushController** deve avere un riferimento al **ColorPickerWheel** oggetto. Poiché il **BrushController** prefab viene creata un'istanza in fase di esecuzione come controller di sostituzione, tutti i riferimenti agli oggetti nella scena dovrà essere impostata in fase di esecuzione. In questo caso usiamo **GameObject.FindObjectOfType** per individuare le **ColorPickerWheel**:

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
* **Salvare** di scena e selezionare il **Riproduci** pulsante. Sarà in grado di disegnare le linee e disegnare con il pulsante di selezione sul controller a destra.

## <a name="chapter-6---object-spawning-with-select-input"></a>Capitolo 6 - oggetto durante la generazione con l'istruzione Select di input

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a>Obiettivi

* Informazioni su come usare Select e comprendere gli eventi di input di pulsante
* Informazioni su come creare istanze degli oggetti

### <a name="instructions"></a>Istruzioni

* Nel **Project** panel, digitare **ObjectSpawner** nella casella di ricerca. È anche possibile trovarlo in asset/AppPrefabs /
* Trascinare il **ObjectSpawner** prefab nel **gerarchia** pannello.
* Fare clic su **ObjectSpawner** nel **gerarchia** pannello.
* **ObjectSpawner** ha un campo denominato **colore origine**.
* Dal **gerarchia** panel, trascinare le **ColorPickerWheel** riferimento in questo campo.

![Oggetto Spawner Inspector](images/mr213-objectspawnercolorpickerwheel-650px.jpg)
* Fare clic sui **ObjectSpawner** prefab nel **gerarchia** pannello.
* Nel **Inspector** del pannello, fare doppio clic **ObjectSpawner** Script per visualizzare il codice in Visual Studio.

**Script ObjectSpawner**

Il **ObjectSpawner** crea un'istanza di copie di una primitiva mesh (cubo, sfera, cilindro) nello spazio. Quando un **InteractionSourcePressed** viene rilevato controlla la mano utilizzata per scrivere e se è un **InteractionSourcePressType.Grasp** oppure **InteractionSourcePressType.Select** evento.

Per un **afferrare** evento, incrementa l'indice del tipo di rete corrente (sfera, cubi, cilindro)

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

Per un **selezionate** evento, nel **SpawnObject()**, un nuovo oggetto è stata creata un'istanza, senza padre e vengono rilasciati in tutto il mondo.

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

Il **ObjectSpawner** Usa le **ColorPickerWheel** per impostare il colore del materiale dell'oggetto di visualizzazione. Oggetti generati ha un'istanza di questo materiale in modo che manterrà i colori.
* **Salvare** di scena e selezionare il **Riproduci** pulsante.

Sarà possibile modificare gli oggetti con il pulsante. é quindi e generare gli oggetti con il pulsante di selezione.

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a>Compilare e distribuire app al portale di realtà mista
* In Unity, selezionare **File > Build Settings**.
* Fare clic su **aggiungere scene Open** per aggiungere scena corrente per il **scene nella compilazione**.
* Fai clic su **Compila**.
* Creare un **nuova cartella** denominato "App".
* Solo clic i **App** cartella.
* Fare clic su **Seleziona cartella**.
* Quando Unity viene eseguita, verrà visualizzata una finestra di Esplora File.
* Aprire il **App** cartella.
* Fare doppio clic su **YourSceneName.sln** file di soluzione di Visual Studio.
* Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione di debug per **Release** e da ARM a **X64**.
* Fare clic sulla freccia giù accanto al pulsante di dispositivo e selezionare **computer locale**.
* Fare clic su **Debug -> Avvia senza eseguire debug** nel menu o premere **Ctrl + F5**.

Ora l'app viene compilata e installata nel portale di realtà mista. È possibile avviarlo nuovamente tramite il menu Start nel portale di realtà mista.

## <a name="advanced-design---brush-tools-with-radial-layout"></a>Progettazione avanzata - strumenti di pennello con layout Radiale

![MixedReality213 Main](images/mr213-main-600px.jpg)

In questo capitolo, si apprenderà come sostituire il modello di controller di movimento predefiniti con una raccolta di strumento pennello personalizzato. Per riferimento, è possibile trovare la scena completata **MixedReality213Advanced** sotto **scene** cartella.

### <a name="instructions"></a>Istruzioni

* Nel **Project** panel, digitare **BrushSelector** nella casella di ricerca. È anche possibile trovarlo in asset/AppPrefabs /
* Trascinare il **BrushSelector** prefab nel **gerarchia** pannello.
* Per l'organizzazione, creare un GameObject vuoto denominato **pennelli**
* Trascinare in seguito prefabs dal **Project** nel pannello **pennelli**
    * Assets/AppPrefabs/**BrushFat**
    * Assets/AppPrefabs/**BrushThin**
    * Assets/AppPrefabs/**Eraser**
    * Assets/AppPrefabs/**MarkerFat**
    * Assets/AppPrefabs/**MarkerThin**
    * Assets/AppPrefabs/**Pencil**

![Pennelli](images/mixedreality213-brushes-250px.png)
* Fare clic su **MotionControllers** prefab nel **gerarchia** pannello.
* Nel **Inspector** panel, deselezionare l'opzione **sempre utilizzo alternativo a destra del modello** sul **movimento Controller Visualizzatore**
* Nel **gerarchia** del pannello, fare clic su **BrushSelector**
* **BrushSelector** ha un campo denominato **ColorPicker**
* Dal **gerarchia** panel, trascinare le **ColorPickerWheel** in **ColorPicker** campo il **Inspector** pannello.

![Assegnare ColorPickerWheel al selettore del pennello](images/mr213-brushselector-500px.jpg)
* Nel **gerarchia** nel pannello **BrushSelector** prefab, selezionare il **Menu** oggetto.
* Nel **Inspector** nel pannello il **LineObjectCollection** componente, aprire il **oggetti** matrice elenco a discesa. Si noterà 6 slot vuoto.
* Dal **gerarchia** panel, trascinare ogni il prefabs impostata come figlio sotto il **pennelli** GameObject in questi slot in qualsiasi ordine. (Assicurarsi che si sta trascinando il prefabs dalla scena, non il prefabs nella cartella del progetto).

![Selettore di pennello](images/mr213-brushselectorbrushes-700px.jpg)

**Prefab BrushSelector**

Poiché il **BrushSelector** eredita **AttachToController**, Mostra **mano** e **elemento** le opzioni presenti nella  **Inspector** pannello. È stato selezionato **a destra** e **puntando comportare** per collegare gli strumenti di pennello per il controller a destra con direzione in avanti.

Il **BrushSelector** usa due utilità:
* **Ellisse**: usato per generare i punti nello spazio lungo una forma di ellisse.
* **LineObjectCollection**: distribuisce gli oggetti utilizzando i punti generati da qualsiasi classe di riga (ad esempio, puntini di sospensione). Questo è ciò che verrà usato per inserire i pennelli lungo la forma di ellisse.

Insieme, queste utilità è utilizzabile per creare un menu radiale.

**LineObjectCollection script**

**LineObjectCollection** include controlli per la dimensione, posizione e la rotazione di oggetti distribuiti su una riga a sé. Ciò è utile per la creazione di menu radiali, ad esempio il selettore di pennello. Per creare l'aspetto dei pennelli scalabili da nothing stanno per raggiungere la posizione di center selezionato, il **ObjectScale** curva picchi al centro e tapers disattivata in corrispondenza dei bordi.

**Script BrushSelector**

Nel caso del **BrushSelector**, abbiamo scelto di utilizzare l'animazione procedurale. In primo luogo, vengono distribuiti i modelli pennello un'ellisse per il **LineObjectCollection** script. Quindi, ogni pennello è responsabile della propria posizione a disposizione dell'utente in base relativa **DisplayMode** valore, che cambia in base alla selezione. Abbiamo scelto un approccio procedurale a causa di elevata probabilità delle transizioni di posizione pennello viene interrotto, in quanto l'utente seleziona i pennelli. Animazioni Mecanim possono gestire le interruzioni correttamente, ma tende a essere più complesso rispetto a una semplice operazione Lerp.

**BrushSelector** Usa una combinazione di entrambi. Quando viene rilevato l'input touchpad, le opzioni diventano visibili e scalabilità verticale lungo il menu radiale. Dopo un periodo di timeout, che indica che l'utente ha effettuato una selezione, il pennello Opzioni scala verso il basso anche in questo caso, lasciando solo del pennello selezionato.

**La visualizzazione input touchpad**

Anche nei casi in cui il modello di controller è stato completamente sostituito, può essere utile visualizzare input sull'input del modello originale. Ciò consente di forzare a terra in realtà le azioni dell'utente. Per il **BrushSelector** abbiamo scelto di rendere il touchpad brevemente visibile quando viene ricevuto l'input. Tale operazione viene eseguita recuperando l'elemento Touchpad dal controller, sostituendo il materiale con un materiale personalizzato, quindi applicare una sfumatura di colore del materiale tale basata il touchpad ora ultimo stato ricevuto l'input.

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

**Pennello di selezione degli strumenti con input touchpad**

Quando il selettore di pennello rileva un input premuto del touchpad, controlla la posizione dell'input per stabilire se questo è a sinistra o destra.

**Spessore del tratto con selectPressedAmount**

Anziché il **InteractionSourcePressType.Select** evento nel **InteractionSourcePressed()**, è possibile ottenere il valore della quantità premuto tramite analogico **selectPressedAmount**. Questo valore può essere recuperato **InteractionSourceUpdated()**.

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

**Gomma** è un tipo speciale di pennello che esegue l'override della base **pennello**del **DrawOverTime()** (funzione). Mentre disegno è true, la gomma controlla se il suggerimento si interseca con tutte le tracce di pennello esistente. In caso affermativo, vengono aggiunti a una coda che si desidera compattare verso il basso ed eliminati.

## <a name="advanced-design---teleportation-and-locomotion"></a>Progettazione avanzata - teletrasporto e locomotion

Se si vuole consentire all'utente di spostarsi all'interno della scena con teletrasporto usando thumbstick, usare **MixedRealityCameraParent** invece di **MixedRealityCamera**. È inoltre necessario aggiungere **InputManager** e **DefaultCusor**. Poiché **MixedRealityCameraParent** include già **MotionControllers** e **limite** come componenti figlio, è necessario rimuovere esistente  **MotionControllers** e **ambiente** prefab.

### <a name="instructions"></a>Istruzioni

* Nel **gerarchia** panel, eliminare **MixedRealityCamera**, **ambiente** e **MotionControllers**
* Dal **pannello progetto**, la ricerca e trascinare il prefabs seguenti nel **gerarchia** pannello:
    * Assets/AppPrefabs/Input/Prefabs/**MixedRealityCameraParent**
    * Assets/AppPrefabs/Input/Prefabs/**InputManager**
    * Assets/AppPrefabs/Input/Prefabs/Cursor/**DefaultCursor**

![Realtà mista fotocamera padre](images/mr213-cameraparent-300px.png)
* Nel **gerarchia** del pannello, fare clic su **Input Manager**
* Nel **Inspector** panel, scorrere verso il basso il **semplice selettore puntatore singolo** sezione
* Dal **gerarchia** panel, trascinare **DefaultCursor** nelle **cursore** campo

![Assegnazione di DefaultCursor](images/mr213-defaultcursor-500px.png)
* **Salvare** di scena e selezionare il **Riproduci** pulsante. Sarà possibile usare il thumbstick la rotazione a sinistra/destra o teleport.

## <a name="the-end"></a>La fine

E questo è il termine di questa esercitazione. Si è appreso:
* Come lavorare con i modelli di controller di movimento in modalità di gioco e runtime di Unity.
* Come usare diversi tipi di eventi del pulsante e le relative applicazioni.
* Procedure per sovrapporre gli elementi dell'interfaccia utente nella parte superiore del controller o completamente personalizzarlo.

Si è ora pronti per iniziare a creare un'esperienza coinvolgente e concreto con i controller di movimento.

## <a name="completed-scenes"></a>Scene completate

* Nella finestra di Unity **Project** pannello fare clic sui **scene** cartella.
* Sono disponibili due Unity sceens **MixedReality213** e **MixedReality213Advanced**.
    * **MixedReality213**: Completato scena con pennello singolo
    * **MixedReality213Advanced**: Completato scena con più pennello con esempio di quantità pressione del pulsante di selezione

## <a name="see-also"></a>Vedere anche

* [File di progetto MR Input 213](https://github.com/Microsoft/MixedReality213)
* [Toolkit di realtà mista - scena movimento Controller Test](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [Toolkit di realtà mista - Mechanics quadratini di ridimensionamento](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [Linee guida sullo sviluppo di controller di movimento](motion-controllers.md)

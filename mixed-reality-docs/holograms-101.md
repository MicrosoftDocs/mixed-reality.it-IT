---
title: Nozioni di base 101-completare il progetto con il dispositivo
description: Segui questa procedura dettagliata di codifica usando Unity, Visual Studio e HoloLens per apprendere le nozioni di base della realtà mista di Windows.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: realtà mista, realtà mista di Windows, HoloLens, ologramma, Accademia, esercitazione
ms.openlocfilehash: 456aeea88b0d7f51acb52156d8139ec2df06883a
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434714"
---
>[!NOTE]
>Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.  Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.  Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.  Verranno mantenuti per continuare a usare i dispositivi supportati. Per HoloLens 2 è stata pubblicata [una nuova serie di esercitazioni](mrlearning-base.md) .

<br>

# <a name="mr-basics-101-complete-project-with-device"></a>Nozioni fondamentali 101: completare il progetto con il dispositivo

<br>

>[!VIDEO https://www.youtube.com/embed/XKIIEC5BMWg]

Questa esercitazione illustra in dettaglio un progetto completo, integrato in Unity, che illustra le funzionalità di base della realtà mista di Windows su HoloLens, tra cui lo [sguardo](gaze-and-commit.md), i [movimenti](gaze-and-commit.md#composite-gestures), l' [input vocale](voice-input.md), il mapping di [suoni spaziali](spatial-sound.md) e [spaziali](spatial-mapping.md) .

Il completamento dell'esercitazione richiede circa 1 ora.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td>Nozioni fondamentali 101: completare il progetto con il dispositivo</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>Prima di iniziare

### <a name="prerequisites"></a>Prerequisiti

* Un PC Windows 10 configurato con gli [strumenti corretti installati](install-the-tools.md).
* Un dispositivo HoloLens [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>File di progetto

* Scaricare i [file](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) richiesti dal progetto. Richiede Unity 2017,2 o versione successiva.
  * Se è ancora necessario il supporto per Unity 5,6, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).
  * Se è ancora necessario il supporto per Unity 5,5, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).
  * Se è ancora necessario il supporto per Unity 5,4, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).
* Annullare l'archiviazione dei file sul desktop o in un'altra posizione facile da raggiungere. Mantiene il nome della cartella come **origami**.

>[!NOTE]
>Se si vuole esaminare il codice sorgente prima del download, è [disponibile in GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).

## <a name="chapter-1---holo-world"></a>Capitolo 1-"Holo" World

>[!VIDEO https://www.youtube.com/embed/PmtZGjYFroY]

In questo capitolo verrà configurato il primo progetto Unity ed eseguiamo il processo di compilazione e distribuzione.

### <a name="objectives"></a>Obiettivi

* Configurare Unity per lo sviluppo olografico.
* Creare un ologramma.
* Vedere un ologramma creato.

### <a name="instructions"></a>Istruzioni

* Avvia Unity.
* Selezionare **Apri**.
* Immettere il percorso come cartella **origami** precedentemente non archiviata.
* Selezionare **origami** e fare clic su **Seleziona cartella**.
* Poiché il progetto **origami** non contiene una scena, salvare la scena predefinita vuota in un nuovo file usando: **file** / **Salva scena con nome**.
* Assegnare alla nuova scena il nome **origami** e premere il pulsante **Salva** .

#### <a name="setup-the-main-virtual-camera"></a>Configurare la fotocamera virtuale principale

* Nel **Pannello gerarchia**selezionare **Main camera**.
* Nel **controllo** impostare la relativa posizione di trasformazione su **0, 0, 0**.
* Trovare la proprietà **Clear Flags** e modificare l'elenco a discesa da **SKYBOX** a **tinta unita**.
* Fare clic sul campo **sfondo** per aprire una selezione colori.
* Impostare **R, G, B e** a su **0**.

#### <a name="setup-the-scene"></a>Configurare la scena

* Nel **Pannello gerarchia**fare clic su **Crea** e **Crea vuoto**.
* Fare clic con il pulsante destro del mouse sul nuovo **GameObject** e scegliere Rinomina. Rinominare GameObject in **origamicollection**.
* Dalla cartella **olografici** nel pannello del progetto (espandere asset e selezionare ologrammi oppure fare doppio clic sulla cartella ologrammi nel pannello del progetto):
  * Trascinare la **fase** nella gerarchia in modo che sia un elemento figlio di **origamicollection**.
  * Trascinare **Sphere1** nella gerarchia in modo che sia un elemento figlio di **origamicollection**.
  * Trascinare **Sphere2** nella gerarchia in modo che sia un elemento figlio di **origamicollection**.
* Fare clic con il pulsante destro del mouse sull'oggetto **direzionale chiaro** nel **Pannello gerarchia** e scegliere **Elimina**.
* Dalla cartella **ologrammi** trascinare le **spie** nella radice del **Pannello gerarchia**.
* Nella **gerarchia**selezionare **origamicollection**.
* Nel **controllo**impostare la posizione di trasformazione su **0,-0,5, 2,0**.
* Premere il pulsante **Play** in Unity per visualizzare l'anteprima degli ologrammi.
* Nella finestra di anteprima verranno visualizzati gli oggetti origami.
* Premere **Riproduci** una seconda volta per arrestare la modalità di anteprima.

#### <a name="export-the-project-from-unity-to-visual-studio"></a>Esportare il progetto da Unity a Visual Studio

* In Unity selezionare **File > impostazioni di compilazione**.
* Selezionare **piattaforma UWP (Universal Windows Platform)** nell'elenco **piattaforma** e fare clic su **Cambia piattaforma**.
* Impostare **SDK** su **Universal 10** e **tipo di compilazione** su **D3D**.
* Controllare **i C# progetti Unity**.
* Fare clic su **Aggiungi scene aperte** per aggiungere la scena.
* Fai clic su **Compila**.
* Nella finestra Esplora file visualizzata creare una **nuova cartella** denominata "app".
* Fare clic sulla **cartella dell'app**.
* Premere **Seleziona cartella**.
* Quando si esegue Unity, viene visualizzata una finestra Esplora file.
* Aprire la cartella dell' **app** .
* Aprire (doppio clic) **origami. sln**.
* Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione da debug a **Release** e da ARM a **x86**.
* Fare clic sulla freccia accanto al pulsante Device (dispositivo) e selezionare **computer remoto** per la distribuzione tramite Wi-Fi.
  * Impostare l' **Indirizzo** sul nome o sull'indirizzo IP del HoloLens. Se non si conosce l'indirizzo IP del dispositivo, controllare **le impostazioni > rete & Internet > opzioni avanzate** o richiedere a Cortana **"Hey Cortana, qual è il mio indirizzo IP?"**
  * Se il HoloLens è collegato tramite USB, è possibile invece selezionare il **dispositivo** per la distribuzione su USB.
  * Lasciare la **modalità di autenticazione** impostata su **universale**.
  * Fare clic su **Seleziona**

* Fare clic su **debug > avvia senza eseguire debug** o premere **CTRL + F5**. Se questa è la prima volta che si esegue la distribuzione nel dispositivo, sarà necessario [associarla a Visual Studio](using-visual-studio.md#pairing-your-device).

* Il progetto Origami verrà ora compilato, distribuito nella HoloLens e quindi eseguito.
* Inserire il HoloLens e cercare i nuovi ologrammi.

## <a name="chapter-2---gaze"></a>Capitolo 2: sguardo

>[!VIDEO https://www.youtube.com/embed/MSO2BoFSQbM]

In questo capitolo, verranno introdotti i primi tre modi per interagire con gli ologrammi [.](gaze-and-commit.md)

### <a name="objectives"></a>Obiettivi

* Visualizza lo sguardo usando un cursore con blocco globale.

### <a name="instructions"></a>Istruzioni

* Tornare al progetto Unity e chiudere la finestra impostazioni di compilazione se è ancora aperta.
* Selezionare la cartella **ologrammi** nel **Pannello del progetto**.
* Trascinare l'oggetto **cursore** nel **Pannello gerarchia** a livello di radice.
* Fare doppio clic sull'oggetto **cursore** per esaminarlo più da vicino.
* Fare clic con il pulsante destro del mouse sulla cartella **Scripts** nel pannello Project.
* Fare clic sul sottomenu **Crea** .
* Selezionare  **C# script**.
* Denominare lo script **WorldCursor**. Nota: il nome fa distinzione tra maiuscole e minuscole. Non è necessario aggiungere l'estensione. cs.
* Selezionare l'oggetto **cursore** nel **Pannello gerarchia**.
* Trascinare e rilasciare lo script **WorldCursor** nel **pannello Inspector**.
* Fare doppio clic sullo script **WorldCursor** per aprirlo in Visual Studio.
* Copiare e incollare questo codice in **WorldCursor.cs** e **salvare tutti**.

```cs
using UnityEngine;

public class WorldCursor : MonoBehaviour
{
    private MeshRenderer meshRenderer;

    // Use this for initialization
    void Start()
    {
        // Grab the mesh renderer that's on the same object as this script.
        meshRenderer = this.gameObject.GetComponentInChildren<MeshRenderer>();
    }

    // Update is called once per frame
    void Update()
    {
        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;

        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram...
            // Display the cursor mesh.
            meshRenderer.enabled = true;

            // Move the cursor to the point where the raycast hit.
            this.transform.position = hitInfo.point;

            // Rotate the cursor to hug the surface of the hologram.
            this.transform.rotation = Quaternion.FromToRotation(Vector3.up, hitInfo.normal);
        }
        else
        {
            // If the raycast did not hit a hologram, hide the cursor mesh.
            meshRenderer.enabled = false;
        }
    }
}
```

* Ricompilare l'app da **File > impostazioni di compilazione**.
* Tornare alla soluzione di Visual Studio usata in precedenza per eseguire la distribuzione in HoloLens.
* Quando richiesto, selezionare "ricarica tutto".
* Fare clic su **debug-> avvia senza eseguire debug** o premere **CTRL + F5**.
* Osservare ora la scena e notare come il cursore interagisce con la forma degli oggetti.

## <a name="chapter-3---gestures"></a>Capitolo 3-movimenti

>[!VIDEO https://www.youtube.com/embed/kW3ThJ2MbvQ]

In questo capitolo verrà aggiunto il supporto per i [movimenti](gaze-and-commit.md#composite-gestures). Quando l'utente seleziona una sfera della carta, la sfera viene ricadeta attivando la gravità usando il motore di fisica di Unity.

### <a name="objectives"></a>Obiettivi

* Controllare gli ologrammi con il gesto di selezione.

### <a name="instructions"></a>Istruzioni

Si inizierà creando uno script, quindi è possibile rilevare il gesto di selezione.

* Nella cartella **Scripts** creare uno script denominato **GazeGestureManager**.
* Trascinare lo script **GazeGestureManager** sull'oggetto **origamicollection** nella gerarchia.
* Aprire lo script **GazeGestureManager** in Visual Studio e aggiungere il codice seguente:

```cs
using UnityEngine;
using UnityEngine.XR.WSA.Input;

public class GazeGestureManager : MonoBehaviour
{
    public static GazeGestureManager Instance { get; private set; }

    // Represents the hologram that is currently being gazed at.
    public GameObject FocusedObject { get; private set; }

    GestureRecognizer recognizer;

    // Use this for initialization
    void Awake()
    {
        Instance = this;

        // Set up a GestureRecognizer to detect Select gestures.
        recognizer = new GestureRecognizer();
        recognizer.Tapped += (args) =>
        {
            // Send an OnSelect message to the focused object and its ancestors.
            if (FocusedObject != null)
            {
                FocusedObject.SendMessageUpwards("OnSelect", SendMessageOptions.DontRequireReceiver);
            }
        };
        recognizer.StartCapturingGestures();
    }

    // Update is called once per frame
    void Update()
    {
        // Figure out which hologram is focused this frame.
        GameObject oldFocusObject = FocusedObject;

        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;
        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram, use that as the focused object.
            FocusedObject = hitInfo.collider.gameObject;
        }
        else
        {
            // If the raycast did not hit a hologram, clear the focused object.
            FocusedObject = null;
        }

        // If the focused object changed this frame,
        // start detecting fresh gestures again.
        if (FocusedObject != oldFocusObject)
        {
            recognizer.CancelGestures();
            recognizer.StartCapturingGestures();
        }
    }
}
```

* Creare un altro script nella cartella Scripts, questa volta denominata **SphereCommands**.
* Espandere l'oggetto **origamicollection** nella visualizzazione gerarchia.
* Trascinare lo script **SphereCommands** sull'oggetto **Sphere1** nel pannello gerarchia.
* Trascinare lo script **SphereCommands** sull'oggetto **Sphere2** nel pannello gerarchia.
* Aprire lo script in Visual Studio per la modifica e sostituire il codice predefinito con il codice seguente:

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }
}
```

* Esportare, compilare e distribuire l'app in HoloLens.
* Esaminare una delle sfere.
* Eseguire il gesto di selezione e osservare il calo della sfera nell'area sottostante.

## <a name="chapter-4---voice"></a>Capitolo 4-Voice

>[!VIDEO https://www.youtube.com/embed/1-Aq0VVtHM8]

In questo capitolo verrà aggiunto il supporto per due [comandi vocali](voice-input.md): "Reimposta tutto il mondo" per restituire le sfere eliminate alla posizione originale e "drop Sphere" per far precipitare la sfera.

### <a name="objectives"></a>Obiettivi

* Aggiungere i comandi vocali che sono sempre in ascolto in background.
* Creare un ologramma che reagisca a un comando Voice.

### <a name="instructions"></a>Istruzioni

* Nella cartella **Scripts** creare uno script denominato **SpeechManager**.
* Trascinare lo script **SpeechManager** sull'oggetto **Origamicollection** nella gerarchia
* Aprire lo script **SpeechManager** in Visual Studio.
* Copiare e incollare questo codice in **SpeechManager.cs** e **salvare tutti**:

```cs
using System.Collections.Generic;
using System.Linq;
using UnityEngine;
using UnityEngine.Windows.Speech;

public class SpeechManager : MonoBehaviour
{
    KeywordRecognizer keywordRecognizer = null;
    Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();

    // Use this for initialization
    void Start()
    {
        keywords.Add("Reset world", () =>
        {
            // Call the OnReset method on every descendant object.
            this.BroadcastMessage("OnReset");
        });

        keywords.Add("Drop Sphere", () =>
        {
            var focusObject = GazeGestureManager.Instance.FocusedObject;
            if (focusObject != null)
            {
                // Call the OnDrop method on just the focused object.
                focusObject.SendMessage("OnDrop", SendMessageOptions.DontRequireReceiver);
            }
        });

        // Tell the KeywordRecognizer about our keywords.
        keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());

        // Register a callback for the KeywordRecognizer and start recognizing!
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        System.Action keywordAction;
        if (keywords.TryGetValue(args.text, out keywordAction))
        {
            keywordAction.Invoke();
        }
    }
}
```

* Aprire lo script **SphereCommands** in Visual Studio.
* Aggiornare lo script in modo da leggere:

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    Vector3 originalPosition;

    // Use this for initialization
    void Start()
    {
        // Grab the original local position of the sphere when the app starts.
        originalPosition = this.transform.localPosition;
    }

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }

    // Called by SpeechManager when the user says the "Reset world" command
    void OnReset()
    {
        // If the sphere has a Rigidbody component, remove it to disable physics.
        var rigidbody = this.GetComponent<Rigidbody>();
        if (rigidbody != null)
        {
            rigidbody.isKinematic = true;
            Destroy(rigidbody);
        }

        // Put the sphere back into its original local position.
        this.transform.localPosition = originalPosition;
    }

    // Called by SpeechManager when the user says the "Drop sphere" command
    void OnDrop()
    {
        // Just do the same logic as a Select gesture.
        OnSelect();
    }
}
```

* Esportare, compilare e distribuire l'app in HoloLens.
* Esaminare una delle sfere e pronunciare "**Drop Sphere**".
* Pronunciare "**Reimposta tutto il mondo**" per riportare le posizioni iniziali.

## <a name="chapter-5---spatial-sound"></a>Capitolo 5-audio spaziale

>[!VIDEO https://www.youtube.com/embed/Aj4de5Ncbfo]

In questo capitolo verrà aggiunta la musica all'app e quindi verranno generati effetti acustici su determinate azioni. Verrà usato il [suono spaziale](spatial-sound.md) per dare un suono a una posizione specifica nello spazio 3D.

### <a name="objectives"></a>Obiettivi

* Ascolta gli ologrammi nel tuo mondo.

### <a name="instructions"></a>Istruzioni

* In Unity selezionare dal menu in alto **modificare > impostazioni progetto > audio**
* Nel pannello Inspector sul lato destro trovare l'impostazione del plug-in **Spatializer** e selezionare **MS HRTF Spatializer**.
* Dalla cartella **olografici** nel pannello del progetto trascinare l'oggetto **ambiente** nell'oggetto **origamicollection** nel pannello gerarchia.
* Selezionare **origamicollection** e trovare il componente **origine audio** nel pannello di controllo. Modificare le proprietà seguenti:
  * Controllare la proprietà **Spatialize** .
  * Verificare la **riproduzione**.
  * Modificare **Blend spaziali** in **3D** trascinando il dispositivo di scorrimento a destra. Quando si sposta il dispositivo di scorrimento, il valore deve variare da 0 a 1.
  * Controllare la proprietà del **ciclo** .
  * Espandere **impostazioni audio 3D**e immettere **0,1** per **livello Doppler**.
  * Impostare **volume attenuazione** su **attenuazione logaritmico**.
  * Impostare la **distanza massima** su **20**.
* Nella cartella **Scripts** creare uno script denominato **SphereSounds**.
* Trascinare **SphereSounds** negli oggetti **Sphere1** e **Sphere2** della gerarchia.
* Aprire **SphereSounds** in Visual Studio, aggiornare il codice seguente e **salvare tutto**.

```cs
using UnityEngine;

public class SphereSounds : MonoBehaviour
{
    AudioSource impactAudioSource = null;
    AudioSource rollingAudioSource = null;

    bool rolling = false;

    void Start()
    {
        // Add an AudioSource component and set up some defaults
        impactAudioSource = gameObject.AddComponent<AudioSource>();
        impactAudioSource.playOnAwake = false;
        impactAudioSource.spatialize = true;
        impactAudioSource.spatialBlend = 1.0f;
        impactAudioSource.dopplerLevel = 0.0f;
        impactAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        impactAudioSource.maxDistance = 20f;

        rollingAudioSource = gameObject.AddComponent<AudioSource>();
        rollingAudioSource.playOnAwake = false;
        rollingAudioSource.spatialize = true;
        rollingAudioSource.spatialBlend = 1.0f;
        rollingAudioSource.dopplerLevel = 0.0f;
        rollingAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        rollingAudioSource.maxDistance = 20f;
        rollingAudioSource.loop = true;

        // Load the Sphere sounds from the Resources folder
        impactAudioSource.clip = Resources.Load<AudioClip>("Impact");
        rollingAudioSource.clip = Resources.Load<AudioClip>("Rolling");
    }

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Play an impact sound if the sphere impacts strongly enough.
        if (collision.relativeVelocity.magnitude >= 0.1f)
        {
            impactAudioSource.Play();
        }
    }

    // Occurs each frame that this object continues to collide with another object
    void OnCollisionStay(Collision collision)
    {
        Rigidbody rigid = gameObject.GetComponent<Rigidbody>();

        // Play a rolling sound if the sphere is rolling fast enough.
        if (!rolling && rigid.velocity.magnitude >= 0.01f)
        {
            rolling = true;
            rollingAudioSource.Play();
        }
        // Stop the rolling sound if rolling slows down.
        else if (rolling && rigid.velocity.magnitude < 0.01f)
        {
            rolling = false;
            rollingAudioSource.Stop();
        }
    }

    // Occurs when this object stops colliding with another object
    void OnCollisionExit(Collision collision)
    {
        // Stop the rolling sound if the object falls off and stops colliding.
        if (rolling)
        {
            rolling = false;
            impactAudioSource.Stop();
            rollingAudioSource.Stop();
        }
    }
}
```

* Salvare lo script e tornare a Unity.
* Esportare, compilare e distribuire l'app in HoloLens.
* Passare da una fase all'altra e da un lato all'altro per ascoltare le modifiche apportate ai suoni.

## <a name="chapter-6---spatial-mapping"></a>Capitolo 6-mapping spaziale

>[!VIDEO https://www.youtube.com/embed/Pkt1_wNLLXY]

Ora verrà usato il [mapping spaziale](spatial-mapping.md) per collocare la lavagna del gioco su un oggetto reale nel mondo reale.

### <a name="objectives"></a>Obiettivi

* Usa il mondo reale nel mondo virtuale.
* Posizionare gli ologrammi in cui è importante.

### <a name="instructions"></a>Istruzioni

* In Unity fare clic sulla cartella **ologrammi** nel pannello del progetto.
* Trascinare l'asset di **mapping spaziale** nella radice della **gerarchia**.
* Fare clic sull'oggetto **mapping spaziale** nella gerarchia.
* Nel **pannello Inspector**modificare le proprietà seguenti:
  * Selezionare la casella per la **visualizzazione dei mesh** .
  * Individuare il **materiale di estrazione** e fare clic sul cerchio a destra. Digitare "**wireframe**" nel campo di ricerca nella parte superiore. Fare clic sul risultato, quindi chiudere la finestra. Quando si esegue questa operazione, il valore per il materiale di estrazione dovrebbe essere impostato su wireframe.
* Esportare, compilare e distribuire l'app in HoloLens.
* Quando l'app viene eseguita, una mesh wireframe si sovrappone al mondo reale.
* Guarda in che modo una sfera in sequenza ricade sulla fase e sul pavimento!

Ora verrà illustrato come spostare l'oggetto Origamicollection in una nuova posizione:

* Nella cartella **Scripts** creare uno script denominato **TapToPlaceParent**.
* Nella **gerarchia**espandere **origamicollection** e selezionare l'oggetto **stage** .
* Trascinare lo script **TapToPlaceParent** nell'oggetto Stage.
* Aprire lo script **TapToPlaceParent** in Visual Studio e aggiornarlo come segue:

```cs
using UnityEngine;

public class TapToPlaceParent : MonoBehaviour
{
    bool placing = false;

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // On each Select gesture, toggle whether the user is in placing mode.
        placing = !placing;

        // If the user is in placing mode, display the spatial mapping mesh.
        if (placing)
        {
            SpatialMapping.Instance.DrawVisualMeshes = true;
        }
        // If the user is not in placing mode, hide the spatial mapping mesh.
        else
        {
            SpatialMapping.Instance.DrawVisualMeshes = false;
        }
    }

    // Update is called once per frame
    void Update()
    {
        // If the user is in placing mode,
        // update the placement to match the user's gaze.

        if (placing)
        {
            // Do a raycast into the world that will only hit the Spatial Mapping mesh.
            var headPosition = Camera.main.transform.position;
            var gazeDirection = Camera.main.transform.forward;

            RaycastHit hitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out hitInfo,
                30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // Move this object's parent object to
                // where the raycast hit the Spatial Mapping mesh.
                this.transform.parent.position = hitInfo.point;

                // Rotate this object's parent object to face the user.
                Quaternion toQuat = Camera.main.transform.localRotation;
                toQuat.x = 0;
                toQuat.z = 0;
                this.transform.parent.rotation = toQuat;
            }
        }
    }
}
```

* Esportare, compilare e distribuire l'app.
* A questo punto dovrebbe essere possibile collocare il gioco in una posizione specifica guardandolo, usando il gesto di selezione e quindi passando a una nuova posizione e usando di nuovo il movimento di selezione.

## <a name="chapter-7---holographic-fun"></a>Capitolo 7-di divertimento olografico

### <a name="objectives"></a>Obiettivi

* Rivelare l'ingresso a un Sottomondo olografico.

### <a name="instructions"></a>Istruzioni

Ora verrà illustrato come scoprire il Sottomondo olografico:

* Dalla cartella **ologrammi** nel pannello del progetto:
  * Trascinare **Underworld** nella gerarchia in modo che sia un elemento figlio di **origamicollection**.
* Nella cartella **Scripts** creare uno script denominato **HitTarget**.
* Nella **gerarchia**espandere **origamicollection**.
* Espandere l'oggetto **fase** e selezionare l'oggetto di **destinazione** (ventola blu).
* Trascinare lo script **HitTarget** nell'oggetto di **destinazione** .
* Aprire lo script **HitTarget** in Visual Studio e aggiornarlo come segue:

```cs
using UnityEngine;

public class HitTarget : MonoBehaviour
{
    // These public fields become settable properties in the Unity editor.
    public GameObject underworld;
    public GameObject objectToHide;

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Hide the stage and show the underworld.
        objectToHide.SetActive(false);
        underworld.SetActive(true);

        // Disable Spatial Mapping to let the spheres enter the underworld.
        SpatialMapping.Instance.MappingEnabled = false;
    }
}
```

* In Unity selezionare l'oggetto di **destinazione** .
* Due proprietà pubbliche sono ora visibili nel componente **hit target** ed è necessario fare riferimento agli oggetti nella scena:
  * Trascinare **Underworld** dal pannello **gerarchia** alla proprietà **Underworld** sul componente **hit target** .
  * Trascinare **stage** dal pannello **gerarchia** all' **oggetto per nascondere** la proprietà nel componente **hit target** .
* Esportare, compilare e distribuire l'app.
* Posizionare la raccolta origami sul pavimento e quindi usare il gesto di selezione per creare una Drop della sfera.
* Quando la sfera raggiunge la destinazione (ventola blu), si verificherà un'esplosione. La raccolta verrà nascosta e verrà visualizzato un foro nel Sottomondo.

## <a name="the-end"></a>La fine

Questa è la fine di questa esercitazione.

Si è appreso quanto segue:

* Come creare un'app olografica in Unity.
* Come usare lo sguardo, il movimento, la voce, il suono e il mapping spaziale.
* Come compilare e distribuire un'app con Visual Studio.

A questo punto è possibile iniziare a creare una propria esperienza olografica.

## <a name="see-also"></a>Vedi anche

* [Nozioni di base su 101E: completare il progetto con l'emulatore](holograms-101e.md)
* [Sguardo fisso](gaze-and-commit.md)
* [Puntamento con la testa e commit](gaze-and-commit.md)
* [Input vocale](voice-input.md)
* [Audio spaziale](spatial-sound.md)
* [Mapping spaziale](spatial-mapping.md)

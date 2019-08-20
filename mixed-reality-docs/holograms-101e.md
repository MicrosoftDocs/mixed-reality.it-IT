---
title: Nozioni di base su 101E-completare il progetto con l'emulatore
description: Seguire questa procedura dettagliata di codifica usando Unity, Visual Studio e l'emulatore HoloLens per apprendere le nozioni di base di un'applicazione olografica.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: realtà mista, realtà mista di Windows, HoloLens, ologramma, Accademia, esercitazione, emulatore
ms.openlocfilehash: 77f7d497396937bf471a69fa514cef84ab0b699d
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522328"
---
>[!NOTE]
>Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.  Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.  Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.  Verranno mantenuti per continuare a usare i dispositivi supportati. In futuro sarà disponibile una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.  Questo avviso verrà aggiornato con un collegamento a queste esercitazioni quando vengono pubblicate.

<br>

# <a name="mr-basics-101e-complete-project-with-emulator"></a>Nozioni di base su 101E: Completa progetto con emulatore

 >[!VIDEO https://www.youtube.com/embed/Xzm8_s05mm8]

Questa esercitazione illustra in dettaglio un progetto completo, integrato in Unity, che illustra le funzionalità di base della realtà mista di Windows su HoloLens, tra cui lo [sguardo](gaze.md), i [movimenti](gestures.md), l' [input vocale](voice-input.md), il mapping di [suoni spaziali](spatial-sound.md) e [spaziali](spatial-mapping.md) . Il completamento dell'esercitazione richiede circa 1 ora.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td>Nozioni di base su 101E: Completa progetto con emulatore</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>Prima di iniziare

### <a name="prerequisites"></a>Prerequisiti

* Un PC Windows 10 configurato con gli [strumenti corretti installati](install-the-tools.md).

### <a name="project-files"></a>File di progetto

* Scaricare i [file](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) richiesti dal progetto. Richiede Unity 2017,2 o versione successiva.
  * Se è ancora necessario il supporto per Unity 5,6, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).
  * Se è ancora necessario il supporto per Unity 5,5, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).
  * Se è ancora necessario il supporto per Unity 5,4, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).
* Annullare l'archiviazione dei file sul desktop o in un'altra posizione facile da raggiungere. Mantiene il nome della cartella come **origami**.

>[!NOTE]
>Se si vuole esaminare il codice sorgente prima del download, è [disponibile in GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).

## <a name="chapter-1---holo-world"></a>Capitolo 1-"Holo" World

>[!VIDEO https://www.youtube.com/embed/qotpUpIQxVU]

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
* Salvare la nuova scena:File / **Salva scena come**.
* Assegnare un nome alla scena **origami** e premere il pulsante **Salva** .

#### <a name="setup-the-main-camera"></a>Configurare la fotocamera principale

* Nel **Pannello gerarchia**selezionare **Main camera**.
* Nel **controllo** impostare la relativa posizione di trasformazione su **0, 0, 0**.
* Trovare la proprietà **Clear Flags** e modificare l'elenco a discesa da **SKYBOX** a **tinta unita**.
* Fare clic sul campo **sfondo** per aprire una selezione colori.
* Impostare **R, G, B e** a su **0**.

#### <a name="setup-the-scene"></a>Configurare la scena

* Nel **Pannello gerarchia**fare clic su **Crea** e **Crea vuoto**.
* Fare clic con il pulsante destro del mouse sul nuovo **GameObject** e scegliere Rinomina. Rinominare GameObject in **origamicollection**.
* Dalla cartella **ologrammi** nel pannello del **progetto**:
  * Trascinare la **fase** nella gerarchia in modo che sia un elemento figlio di **origamicollection**.
  * Trascinare **Sphere1** nella gerarchia in modo che sia un elementofiglio di origamicollection.
  * Trascinare **Sphere2** nella gerarchia in modo che sia un elementofiglio di origamicollection.
* Fare clic con il pulsante destro del mouse sull'oggetto **direzionale chiaro** nel **Pannello gerarchia** e scegliere **Elimina**.
* Dalla cartella **ologrammi** trascinare le **spie** nella radice del **Pannello gerarchia**.
* Nella **gerarchia**selezionare origamicollection.
* Nel **controllo**impostare la posizione di trasformazione su **0,-0,5, 2,0**.
* Premere il pulsante **Play** in Unity per visualizzare l'anteprima degli ologrammi.
* Nella finestra di anteprima verranno visualizzati gli oggetti origami.
* Premere Riproduci una seconda volta per arrestare la modalità di anteprima.

#### <a name="export-the-project-from-unity-to-visual-studio"></a>Esportare il progetto da Unity a Visual Studio

* In Unity selezionare **File > impostazioni di compilazione**.
* Selezionare **Windows Store** nell'elenco **piattaforma** e fare clic su **Cambia piattaforma**.
* Impostare **SDK** su **Universal 10** e **tipo di compilazione** su **D3D**.
* Controllare **i C# progetti Unity**.
* Fare clic su **Aggiungi scene aperte** per aggiungere la scena.
* Fare clic su **Impostazioni lettore...** .
* Nel pannello Inspector selezionare il **logo di Windows Store**. Quindi selezionare **impostazioni di pubblicazione**.
* Nella sezione **funzionalità** selezionare le funzionalità **Microphone** e **SpatialPerception** .
* Tornare alla finestra Impostazioni compilazione, fare clic su **Compila**.
* Creare una **nuova cartella** denominata "app".
* Fare clic sulla **cartella dell'app**.
* Premere **Seleziona cartella**.
* Quando si esegue Unity, viene visualizzata una finestra Esplora file.
* Aprire la cartella dell' **app** .
* Aprire la **soluzione origami di Visual Studio**.
* Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione da debug a **Release** e da ARM a **x86**.
  * Fare clic sulla freccia accanto al pulsante Device (dispositivo) e selezionare **HoloLens Emulator**(emulatore).
  * Fare clic su **debug-> avvia senza eseguire debug** o premere **CTRL + F5**.
  * Dopo un po' di tempo l'emulatore inizierà con il progetto origami. Quando l'[emulatore](using-the-hololens-emulator.md) viene avviato per la prima volta, possono essere necessari fino a 15 minuti per l'avvio dell'emulatore. Una volta avviata, non chiuderla.

## <a name="chapter-2---gaze"></a>Capitolo 2: sguardo

>[!VIDEO https://www.youtube.com/embed/BPWTbAC210k]

In questo capitolo, verranno introdotti i primi tre modi per interagire con gli ologrammi [.](gaze.md)

### <a name="objectives"></a>Obiettivi

* Visualizza lo sguardo usando un cursore con blocco globale.

### <a name="instructions"></a>Istruzioni

* Tornare al progetto Unity e chiudere la finestra impostazioni di compilazione se è ancora aperta.
* Selezionare la cartella ologrammi nel **Pannello del progetto**.
* Trascinare l'oggetto **cursore** nel **Pannello gerarchia** a livello di radice.
* Fare doppio clic sull'oggetto **cursore** per esaminarlo più da vicino.
* Fare clic con il pulsante destro del mouse sulla cartella Scripts nel pannello Project.
* Fare clic sul sottomenu **Crea** .
* Selezionare  **C# script**.
* Denominare lo script **WorldCursor**. Nota: Per il nome viene fatta distinzione tra maiuscole e minuscole. Non è necessario aggiungere l'estensione. cs.
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

            // Move thecursor to the point where the raycast hit.
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
* Tornare alla soluzione di Visual Studio usata in precedenza per la distribuzione nell'emulatore.
* Quando richiesto, selezionare "ricarica tutto".
* Fare clic su **debug-> avvia senza eseguire debug** o premere **CTRL + F5**.
* Usare il controller Xbox per esaminare la scena. Si noti come il cursore interagisce con la forma degli oggetti.

## <a name="chapter-3---gestures"></a>Capitolo 3-movimenti

>[!VIDEO https://www.youtube.com/embed/6d-0RHeKHq4]

In questo capitolo verrà aggiunto il supporto per i [movimenti](gestures.md). Quando l'utente seleziona una sfera della carta, la sfera viene ricadeta attivando la gravità usando il motore di fisica di Unity.

### <a name="objectives"></a>Obiettivi

* Controllare gli ologrammi con il gesto di selezione.

### <a name="instructions"></a>Istruzioni

Si inizierà creando uno script che può rilevare il gesto di selezione.

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
    void Start()
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
* Espandere l' oggetto origamicollection nella visualizzazione gerarchia.
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

* Esportare, compilare e distribuire l'app nell'emulatore di HoloLens.
* Osservare la scena e centrare su una delle sfere.
* Premere il **pulsante a** del controller Xbox o premere la barra spaziatrice per simulare il movimento di selezione.

## <a name="chapter-4---voice"></a>Capitolo 4-Voice

>[!VIDEO https://www.youtube.com/embed/LxbOhnd2_GM]

In questo capitolo verrà aggiunto il supporto per due [comandi vocali](voice-input.md): "Reimposta il mondo" per restituire le sfere eliminate alla posizione originale e "drop Sphere" per fare in modo che la sfera rientri.

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

* Esportare, compilare e distribuire l'app nell'emulatore di HoloLens.
* L'emulatore supporterà il microfono del PC e risponderà alla voce: modificare la visualizzazione in modo che il cursore si trovi in una delle sfere e pronunciare "drop Sphere".
* Pronunciare "**Reimposta tutto il mondo**" per riportare le posizioni iniziali.

## <a name="chapter-5---spatial-sound"></a>Capitolo 5-audio spaziale

>[!VIDEO https://www.youtube.com/embed/Xc3C4VA10w4]

In questo capitolo verrà aggiunta la musica all'app e quindi verranno generati effetti acustici su determinate azioni. Verrà usato il [suono spaziale](spatial-sound.md) per dare un suono a una posizione specifica nello spazio 3D.

### <a name="objectives"></a>Obiettivi

* Ascolta gli ologrammi nel tuo mondo.

### <a name="instructions"></a>Istruzioni

* In Unity selezionare dal menu in alto **modificare > impostazioni progetto > audio**
* Trovare l'impostazione del plug-in **Spatializer** e selezionare **MS HRTF Spatializer**.
* Dalla cartella **ologrammi** trascinare l'oggetto **ambiente** nell'oggetto origamicollection nel pannello gerarchia.
* Selezionare **origamicollection** e trovare il componente di **origine audio** . Modificare le proprietà seguenti:
  * Controllare la proprietà **Spatialize** .
  * Verificare la **riproduzione**.
  * Modificare **Blend spaziali** in **3D** trascinando il dispositivo di scorrimento a destra.
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
* Esportare, compilare e distribuire l'app nell'emulatore di HoloLens.
* Indossa le cuffie per ottenere l'effetto completo e passa da una fase all'altra in modo da essere in grado di sentire la variazione dei suoni.

## <a name="chapter-6---spatial-mapping"></a>Capitolo 6-mapping spaziale

>[!VIDEO https://www.youtube.com/embed/S-517Y63Cnk]

Ora verrà usato il [mapping spaziale](spatial-mapping.md) per collocare la lavagna del gioco su un oggetto reale nel mondo reale.

### <a name="objectives"></a>Obiettivi

* Usa il mondo reale nel mondo virtuale.
* Posizionare gli ologrammi in cui è importante.

### <a name="instructions"></a>Istruzioni

* Fare clic sulla cartella olografici nel pannello del progetto.
* Trascinare l'asset di **mapping spaziale** nella radice della **gerarchia**.
* Fare clic sull'oggetto **mapping spaziale** nella gerarchia.
* Nel **pannello Inspector**modificare le proprietà seguenti:
  * Selezionare la casella per la **visualizzazione dei mesh** .
  * Individuare il **materiale di estrazione** e fare clic sul cerchio a destra. Digitare "**wireframe**" nel campo di ricerca nella parte superiore. Fare clic sul risultato, quindi chiudere la finestra.
* Esportare, compilare e distribuire l'app nell'emulatore di HoloLens.
* Quando viene eseguita l'app, viene eseguito il rendering in wireframe di una rete di una stanza reale di una stanza reale sottoposta a scansione.
* Guarda in che modo una sfera in sequenza ricade sulla fase e sul pavimento!

Ora verrà illustrato come spostare l'oggetto Origamicollection in una nuova posizione:

* Nella cartella **Scripts** creare uno script denominato **TapToPlaceParent**.
* Nella **gerarchia**espandere origamicollection e selezionare l'oggetto **stage** .
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
* A questo punto dovrebbe essere possibile collocare il gioco in una posizione specifica guardandolo, usando il gesto selezionato (**a** o barra spaziatrice), quindi passando a una nuova posizione e usando di nuovo il movimento di selezione.

## <a name="the-end"></a>La fine

Questa è la fine di questa esercitazione.

Si è appreso quanto segue:

* Come creare un'app olografica in Unity.
* Come usare lo sguardo, il movimento, la voce, i suoni e il mapping spaziale.
* Come compilare e distribuire un'app con Visual Studio.

A questo punto è possibile iniziare a creare le proprie app olografiche.

## <a name="see-also"></a>Vedere anche

* [Nozioni di base MR 101: Progetto completo con dispositivo](holograms-101.md)
* [Sguardo fisso](gaze.md)
* [Movimenti](gestures.md)
* [Input vocale](voice-input.md)
* [Audio spaziale](spatial-sound.md)
* [Mapping spaziale](spatial-mapping.md)

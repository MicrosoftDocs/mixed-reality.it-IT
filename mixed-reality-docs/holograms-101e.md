---
title: Nozioni fondamentali MR 101E - progetto completo con emulatore
description: Seguire questa procedura dettagliata con Unity, Visual Studio e HoloLens emulatore che informazioni di base di un'applicazione holographic di codifica.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: realtà mista, realtà mista di Windows, HoloLens, ologrammi, emulatore tutorial, academy,
ms.openlocfilehash: 77f7d497396937bf471a69fa514cef84ab0b699d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599403"
---
>[!NOTE]
>Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.  Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.  Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.  Essi verranno mantenute per continuare a utilizzare i dispositivi supportati. Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.  Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.

<br>

# <a name="mr-basics-101e-complete-project-with-emulator"></a>Nozioni fondamentali di MR 101E: Progetto completo con emulatore

 >[!VIDEO https://www.youtube.com/embed/Xzm8_s05mm8]

Questa esercitazione illustrerà un progetto completo, compilato in Unity, che illustra le funzionalità di realtà mista di Windows di core per HoloLens, incluse [estasiati](gaze.md), [movimenti](gestures.md), [inputvocale](voice-input.md), [spaziale audio](spatial-sound.md) e [mapping spaziale](spatial-mapping.md). L'esercitazione saranno necessari circa 1 ora.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></th>
</tr><tr>
<td>Nozioni fondamentali di MR 101E: Progetto completo con emulatore</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>Prima di iniziare

### <a name="prerequisites"></a>Prerequisiti

* Un PC Windows 10 configurate con i valori corretti [sono installati gli strumenti](install-the-tools.md).

### <a name="project-files"></a>File di progetto

* Scaricare il [file](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) necessarie per il progetto. Richiede Unity 2017.2 o versione successiva.
  * Se è comunque necessario il supporto di Unity 5.6, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).
  * Se è comunque necessario il supporto di Unity 5.5, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).
  * Se è ancora necessario supporto 5.4 di Unity, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).
* Annullare la-archive i file sul desktop o altri facile da raggiungere percorso. Mantenere il nome di cartella **Origami**.

>[!NOTE]
>Se si desidera esaminare il codice sorgente prima di scaricare, ha [disponibile in GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).

## <a name="chapter-1---holo-world"></a>Capitolo 1 - world "Holo"

>[!VIDEO https://www.youtube.com/embed/qotpUpIQxVU]

In questo capitolo verranno configurare il primo progetto Unity e procedere con la compilazione e processo di distribuzione.

### <a name="objectives"></a>Obiettivi

* Configurare Unity per lo sviluppo holographic.
* Rendere ologramma.
* Vedere ologramma apportate.

### <a name="instructions"></a>Istruzioni

* Avviare Unity.
* Selezionare **aperto**.
* Immettere il percorso come il **Origami** cartella è archiviato in precedenza di annullamento.
* Selezionare **Origami** e fare clic su **Seleziona cartella**.
* Salvare la nuova scena: **File** / **Salva scena come**.
* Denominare la scena **Origami** e premere il **salvare** pulsante.

#### <a name="setup-the-main-camera"></a>Programma di installazione la fotocamera principale

* Nel **Pannello di gerarchia**, selezionare **Main Camera**.
* Nel **Inspector** impostare la posizione di trasformazione **0, 0,0**.
* Trovare il **Cancella flag** proprietà e modificare l'elenco a discesa dal **Skybox** al **colore a tinta unita**.
* Fare clic sui **sfondo** campo per aprire una selezione colori.
* Impostare **R, G, B e A** al **0**.

#### <a name="setup-the-scene"></a>Programma di installazione della scena

* Nel **Pannello di gerarchia**, fare clic su **Create** e **Crea vuoto**.
* Fare doppio clic su nuova **GameObject** e scegliere Rinomina. Rinominare gli elementi GameObject al **OrigamiCollection**.
* Dal **Vntana** cartella le **pannello progetto**:
  * Trascinare **Stage** nella gerarchia di un elemento figlio di **OrigamiCollection**.
  * Trascinare **Sphere1** nella gerarchia di un elemento figlio di **OrigamiCollection**.
  * Trascinare **Sphere2** nella gerarchia di un elemento figlio di **OrigamiCollection**.
* Fare doppio clic sul **luce direzionale** dell'oggetto nel **Pannello di gerarchia** e selezionare **Elimina**.
* Dal **Vntana** cartella, trascinare **luci** nella radice del **gerarchia pannello**.
* Nel **gerarchia**, selezionare la **OrigamiCollection**.
* Nel **Inspector**, impostare la posizione di trasformazione **0, -0,5, 2.0**.
* Premere il **riprodurre** pulsante in Unity per visualizzare in anteprima il vntana.
* Si dovrebbero vedere gli oggetti di Origami nella finestra di anteprima.
* Premere **riprodurre** una seconda volta per arrestare la modalità di anteprima.

#### <a name="export-the-project-from-unity-to-visual-studio"></a>Esporta il progetto di Unity a Visual Studio

* Nella finestra Seleziona Unity **File > Build Settings**.
* Selezionare **Windows Store** nel **Platform** elenco e fare clic su **commutatore piattaforma**.
* Impostare **SDK** al **10 Universal** e **tipo di compilazione** al **D3D**.
* Controllare **Unity C# progetti**.
* Fare clic su **aggiungere scene Open** per aggiungere la scena.
* Fare clic su **le impostazioni del giocatore...** .
* Selezionare il pannello di controllo di **logo di Windows Store**. Quindi selezionare **impostazioni di pubblicazione**.
* Nel **capacità** selezionare la **microfono** e **SpatialPerception** funzionalità.
* Torna nella finestra di impostazioni di compilazione, fare clic su **compilazione**.
* Creare un **nuova cartella** denominato "App".
* Solo clic i **cartella App**.
* Premere **Seleziona cartella**.
* Quando Unity viene eseguita, verrà visualizzata una finestra di Esplora File.
* Aprire il **App** cartella.
* Aprire il **soluzione di Visual Studio di Origami**.
* Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione di debug per **Release** e da ARM a **X86**.
  * Fare clic sulla freccia accanto al pulsante di dispositivo e selezionare **HoloLens emulatore**.
  * Fare clic su **Debug -> Avvia senza eseguire debug** o premere **Ctrl + F5**.
  * Dopo alcuni minuti l'emulatore verrà avviato con il progetto di Origami. Quando si avvia innanzitutto le [emulatore](using-the-hololens-emulator.md), può richiedere fino a 15 minuti per l'emulatore per l'avvio. Dopo l'avvio, non chiudere.

## <a name="chapter-2---gaze"></a>Capitolo 2 - sguardo

>[!VIDEO https://www.youtube.com/embed/BPWTbAC210k]

In questo capitolo verrà per introdurre il primo di tre modi di interagire con i vntana: [estasiati](gaze.md).

### <a name="objectives"></a>Obiettivi

* Visualizzare lo sguardo utilizzando un cursore bloccato al mondo.

### <a name="instructions"></a>Istruzioni

* Tornare al progetto Unity e chiudere la finestra Impostazioni di compilazione se è ancora aperto.
* Selezionare il **Vntana** cartella le **pannello progetto**.
* Trascinare il **cursore** all'oggetto il **Pannello di gerarchia** a livello di radice.
* Fare doppio clic sulla **cursore** oggetto da ottenere un quadro più da vicino.
* Fare clic sui **script** cartella nel Pannello di progetto.
* Scegliere il **Create** sottomenu.
* Selezionare  **C# Script**.
* Denominare lo script **WorldCursor**. Nota: Per il nome viene fatta distinzione tra maiuscole e minuscole. Non devi aggiungere l'estensione. cs.
* Selezionare il **cursore** dell'oggetto nel **Pannello di gerarchia**.
* Trascinare e rilasciare il **WorldCursor** basano gli script delle **Pannello di controllo**.
* Fare doppio clic il **WorldCursor** script per aprirlo in Visual Studio.
* Copiare e incollare questo codice nel **WorldCursor.cs** e **Salva tutto**.

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

* Ricompilare l'app dalla **File > Impostazioni di compilazione**.
* Tornare alla soluzione di Visual Studio usata in precedenza per distribuire l'emulatore.
* Selezionare "Ricarica tutto" quando richiesto.
* Fare clic su **Debug -> Avvia senza eseguire debug** o premere **Ctrl + F5**.
* Usare il controller Xbox per cercare la scena. Si noti come il cursore interagisce con la forma degli oggetti.

## <a name="chapter-3---gestures"></a>Capitolo 3 - movimenti

>[!VIDEO https://www.youtube.com/embed/6d-0RHeKHq4]

In questo capitolo verrà aggiunto il supporto per [movimenti](gestures.md). Quando l'utente seleziona una sfera paper, ci assicureremo sfera rientrano attivando la gravità usando il motore di fisica di Unity.

### <a name="objectives"></a>Obiettivi

* Controllare il vntana con il movimento di Select.

### <a name="instructions"></a>Istruzioni

Si inizierà creando uno script più in grado di rilevare il movimento di Select.

* Nel **gli script** cartella, creare uno script denominato **GazeGestureManager**.
* Trascinare il **GazeGestureManager** lo script nel **OrigamiCollection** oggetto nella gerarchia.
* Aprire il **GazeGestureManager** genera script in Visual Studio e aggiungere il codice seguente:

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
* Espandere la **OrigamiCollection** oggetto nella visualizzazione gerarchica.
* Trascinare il **SphereCommands** nello script le **Sphere1** oggetto nel Pannello di gerarchia.
* Trascinare il **SphereCommands** nello script le **Sphere2** oggetto nel Pannello di gerarchia.
* Aprire lo script in Visual Studio per la modifica e sostituire il codice predefinito con questo:

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
* Guardatevi intorno scena e allineare al centro su uno dei settori.
* Premere il **oggetto** sul controller Xbox oppure premere la barra spaziatrice per simulare il movimento di Select.

## <a name="chapter-4---voice"></a>Capitolo 4 - voce

>[!VIDEO https://www.youtube.com/embed/LxbOhnd2_GM]

In questo capitolo verrà aggiunto il supporto per due [comandi vocali](voice-input.md): Vengono restituiti "Reimposta world" a sfere eliminati nel percorso originale e "Drop sphere" per rendere la sfera di fallback.

### <a name="objectives"></a>Obiettivi

* Aggiungere comandi vocali sempre in ascolto in background.
* Creare un ologrammi che reagisce a un comando vocale.

### <a name="instructions"></a>Istruzioni

* Nel **gli script** cartella, creare uno script denominato **SpeechManager**.
* Trascinare il **SpeechManager** nello script le **OrigamiCollection** oggetto nella gerarchia di
* Aprire il **SpeechManager** script in Visual Studio.
* Copiare e incollare questo codice nel **SpeechManager.cs** e **Salva tutto**:

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

* Aprire il **SphereCommands** script in Visual Studio.
* Aggiornare lo script come segue:

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
* L'emulatore supporterà il microfono del PC e la propria voce: regolare la vista in modo che il cursore si trova in uno dei settori e pronunciare "Drop Sphere".
* Ad esempio "**reimpostare World**" per riportarle posizioni iniziali.

## <a name="chapter-5---spatial-sound"></a>Capitolo 5 - spaziale audio

>[!VIDEO https://www.youtube.com/embed/Xc3C4VA10w4]

In questo capitolo, si sarà aggiungere musica all'app e quindi attivare effetti sonori su determinate azioni. Utilizzeremo [spaziale audio](spatial-sound.md) per fornire un percorso specifico nello spazio 3D suoni.

### <a name="objectives"></a>Obiettivi

* Ascolta vntana in tutto il mondo.

### <a name="instructions"></a>Istruzioni

* In select Unity dal menu in alto **Modifica > Impostazioni di progetto > Audio**
* Trovare il **plug-in spaziale** impostazione e selezionare **MS HRTF Spatializer**.
* Dal **Vntana** cartella, trascinare le **atmosfera** dell'oggetto nel **OrigamiCollection** oggetto nel Pannello di gerarchia.
* Selezionare **OrigamiCollection** e trovare il **origine Audio** componente. Modificare queste proprietà:
  * Verificare i **Spatialize** proprietà.
  * Verificare i **Ascolta al attivi**.
  * Change **Blend spaziali** al **3D** trascinando il dispositivo di scorrimento fino a destra.
  * Verificare i **ciclo** proprietà.
  * Espandere **impostazioni 3D suono**e immettere **0,1** per **livello Doppler**.
  * Impostare **Volume attenuazione** al **attenuazione logaritmica**.
  * Impostare **distanza massima** al **20**.
* Nel **gli script** cartella, creare uno script denominato **SphereSounds**.
* Trascinare **SphereSounds** per il **Sphere1** e **Sphere2** gli oggetti nella gerarchia.
* Aprire **SphereSounds** in Visual Studio, aggiornare il codice seguente e **Salva tutto**.

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
* Wear cuffie per ottenere l'effetto completo e spostare più da vicino e più lontano sul palco per ascoltare i suoni di modifica.

## <a name="chapter-6---spatial-mapping"></a>Capitolo 6 - spaziali mapping

>[!VIDEO https://www.youtube.com/embed/S-517Y63Cnk]

A questo punto si userà [mapping spaziale](spatial-mapping.md) per inserire la tavola da gioco in un oggetto reale nel mondo reale.

### <a name="objectives"></a>Obiettivi

* Rendere il mondo reale del mondo virtuale.
* Posizionare il vntana dove sono più importanti.

### <a name="instructions"></a>Istruzioni

* Fare clic sui **Vntana** cartella nel Pannello di progetto.
* Trascinare il **Mapping spaziale** asset nella radice della **gerarchia**.
* Fare clic sui **Mapping spaziale** oggetto nella gerarchia.
* Nel **Pannello di controllo**, modificare le proprietà seguenti:
  * Verificare i **disegnare Visual trame** casella.
  * Individuare **disegnare materiale** e fare clic sul cerchio nella parte destra. Tipo "**wireframe**" nel campo di ricerca nella parte superiore. Fare clic sul risultato e quindi chiudere la finestra.
* Esportare, compilare e distribuire l'app nell'emulatore di HoloLens.
* Quando si esegue l'app, verrà visualizzata una mesh di una chat room living reali in precedenza sottoposta ad analisi nel wireframe in.
* Guarda come una sfera in sequenza rientrerà il palco e al tetto minimo.

A questo punto vi mostreremo come spostare il OrigamiCollection in una nuova posizione:

* Nel **gli script** cartella, creare uno script denominato **TapToPlaceParent**.
* Nel **gerarchia**, espandere il **OrigamiCollection** e selezionare il **fase** oggetto.
* Trascinare il **TapToPlaceParent** script l'oggetto di fase.
* Aprire il **TapToPlaceParent** script in Visual Studio e aggiornarlo in modo da essere quanto segue:

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
* A questo punto dovrebbe ora essere possibile posizionare il gioco in una posizione specifica, gazing analizzarlo, tramite il movimento di Select (**oggetto** o barra spaziatrice) e quindi lo spostamento in una nuova posizione e l'utilizzo il movimento seleziona nuovamente.

## <a name="the-end"></a>La fine

E questo è il termine di questa esercitazione.

Si è appreso:

* Come creare un'app holographic in Unity.
* Come rendere utilizzare sguardo, gesti, vocali, suoni e mapping spaziale.
* Come compilare e distribuire un'app usando Visual Studio.

Si è ora pronti per iniziare a creare App holographic.

## <a name="see-also"></a>Vedere anche

* [Nozioni fondamentali di MR 101: Progetto completo con dispositivo](holograms-101.md)
* [Sguardo](gaze.md)
* [Movimenti](gestures.md)
* [Input vocale](voice-input.md)
* [Spaziale audio](spatial-sound.md)
* [Mapping spaziale](spatial-mapping.md)

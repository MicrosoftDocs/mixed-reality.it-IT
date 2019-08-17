---
title: Input MR 211-movimento
description: Seguire questa procedura dettagliata di codifica usando Unity, Visual Studio e HoloLens per informazioni dettagliate sui concetti di movimento.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academy, esercitazione, gesto
ms.openlocfilehash: 694f51f1b56588e100d6d2676a8194d7e9936133
ms.sourcegitcommit: e9a55528965048ce34f8247ef6e544f9f432ee37
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/16/2019
ms.locfileid: "69559882"
---
>[!NOTE]
>Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.  Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.  Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.  Verranno mantenuti per continuare a usare i dispositivi supportati. In futuro sarà disponibile una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.  Questo avviso verrà aggiornato con un collegamento a queste esercitazioni quando vengono pubblicate.

# <a name="mr-input-211-gesture"></a>Input MR 211: Movimento

I [movimenti](gestures.md) attivano l'azione dell'utente. Con i movimenti, gli utenti possono interagire con gli ologrammi. In questo corso si apprenderà come tenere traccia delle mani dell'utente, rispondere all'input dell'utente e fornire commenti e suggerimenti all'utente in base allo stato e alla posizione della mano.

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

In [Mr nozioni di base 101](holograms-101.md)è stato usato un semplice gesto d'aria per interagire con gli ologrammi. A questo punto, si passerà oltre il gesto d'aria e si analizzeranno i nuovi concetti per:

* Rilevare quando viene tenuta traccia della mano dell'utente e fornire commenti e suggerimenti all'utente.
* Usare un movimento di navigazione per ruotare gli ologrammi.
* Invia commenti e suggerimenti quando la mano dell'utente sta per uscire dalla visualizzazione.
* Usare gli eventi di manipolazione per consentire agli utenti di spostare gli ologrammi con le proprie mani.

In questo corso verrà rivisitato **Esplora modelli**di progetto Unity, che è stato compilato in [input Mr 210](holograms-210.md). Il nostro amico di un astronauta è stato di aiuto nell'esplorazione di questi nuovi concetti di movimento.

>[!IMPORTANT]
>I video incorporati in ognuno dei capitoli seguenti sono stati registrati usando una versione precedente di Unity e il Toolkit di realtà mista. Sebbene le istruzioni dettagliate siano accurate e aggiornate, è possibile visualizzare gli script e gli oggetti visivi nei video corrispondenti non aggiornati. I video rimangono inclusi per i posteri e perché i concetti trattati sono ancora validi.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td>Input MR 211: Movimento</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Prima di iniziare

### <a name="prerequisites"></a>Prerequisiti

* Un PC Windows 10 configurato con gli [strumenti corretti installati](install-the-tools.md).
* Alcune funzionalità C# di programmazione di base.
* Sono state completate le nozioni di [base 101](holograms-101.md).
* È necessario aver completato il [sig. Input 210](holograms-210.md).
* Un dispositivo HoloLens [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>File di progetto

* Scaricare i [file](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) richiesti dal progetto. Richiede Unity 2017,2 o versione successiva.
* Annullare l'archiviazione dei file sul desktop o in un'altra posizione facile da raggiungere.

>[!NOTE]
>Se si vuole esaminare il codice sorgente prima del download, è [disponibile in GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).

### <a name="errata-and-notes"></a>Errori e note

* "Enable Just My Code" deve essere disabilitato (deselezionato) in Visual Studio in strumenti-Opzioni >-> debug per raggiungere i punti di interruzione nel codice.

## <a name="chapter-0---unity-setup"></a>Capitolo 0-installazione Unity

### <a name="instructions"></a>Istruzioni

1. Avvia Unity.
2. Selezionare **Apri**.
3. Passare alla cartella **movimenti** precedentemente non archiviata.
4. Individuare e selezionare la cartella **avvio**/di**Esplora modelli** .
5. Fare clic sul pulsante **Seleziona cartella** .
6. Nel pannello **progetto** espandere la cartella **Scenes** .
7. Fare doppio clic su **ModelExplorer** scene per caricarla in Unity.

### <a name="building"></a>Compilazione

1. In Unity selezionare **File > impostazioni di compilazione**.
2. Se **Scenes/ModelExplorer** non è elencato in **Scenes in Build**, fare clic su **Aggiungi scene aperte** per aggiungere la scena.
3. Se si sta sviluppando in modo specifico per HoloLens, impostare **dispositivo di destinazione** su **HoloLens**. In caso contrario, lasciarlo in **qualsiasi dispositivo**.
4. Verificare che **tipo di compilazione** sia impostato su **D3D** e che l' **SDK** sia impostato su **installato più recente** (che deve essere SDK 16299 o versione successiva).
5. Fai clic su **Compila**.
6. Creare una **nuova cartella** denominata "app".
7. Fare clic sulla cartella dell' **app** .
8. Premere **Seleziona cartella** e Unity avvierà la compilazione del progetto per Visual Studio.

Quando si esegue Unity, viene visualizzata una finestra Esplora file.

1. Aprire la cartella dell' **app** .
2. Aprire la **soluzione ModelExplorer di Visual Studio**.

Se si esegue la distribuzione in HoloLens:

1. Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione da debug a **Release** e da ARM a **x86**.
2. Fare clic sulla freccia a discesa accanto al pulsante computer locale e selezionare **computer remoto**.
3. Immettere **l'indirizzo IP del dispositivo HoloLens** e impostare la modalità di autenticazione su **universale (protocollo non crittografato)** . Fare clic su **Seleziona**. Se non si conosce l'indirizzo IP del dispositivo, vedere **impostazioni > rete & Internet > opzioni avanzate**.
4. Nella barra dei menu superiore fare clic su **debug-> avvia senza eseguire debug** o premere **CTRL + F5**. Se questa è la prima volta che si esegue la distribuzione nel dispositivo, sarà necessario associarla a [Visual Studio](using-visual-studio.md#pairing-your-device-hololens).
5. Quando l'app è stata distribuita, chiudere il **fitbox** con un **movimento di selezione**.

Se si esegue la distribuzione in un auricolare immersivo:

1. Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione da debug a **Release** e da ARM a **x64**.
2. Verificare che la destinazione di distribuzione sia impostata su **computer locale**.
3. Nella barra dei menu superiore fare clic su **debug-> avvia senza eseguire debug** o premere **CTRL + F5**.
4. Quando l'app è stata distribuita, chiudere il **fitbox** estraendo il trigger in un controller di movimento.

>[!NOTE]
>Si potrebbero notare alcuni errori rossi nel pannello Errori di Visual Studio. È possibile ignorarli. Passare al pannello output per visualizzare lo stato di avanzamento della compilazione. Per gli errori nel pannello di output sarà necessario eseguire una correzione (la maggior parte delle volte è causata da un errore in uno script).

## <a name="chapter-1---hand-detected-feedback"></a>Capitolo 1-feedback rilevato

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a>Obiettivi

* Sottoscrivere gli eventi di rilevamento manuale.
* Usare il feedback del cursore per visualizzare gli utenti quando viene tenuta traccia di una mano.

>[!NOTE]
>In HoloLens 2 sono state rilevate attivazioni ogni volta che le mani sono visibili, non solo quando un dito punta verso l'alto.

### <a name="instructions"></a>Istruzioni

* Nel pannello **gerarchia** espandere l'oggetto **InputManager** .
* Cercare e selezionare l'oggetto **GesturesInput** .

Lo script **InteractionInputSource.cs** esegue i passaggi seguenti:

1. Sottoscrive gli eventi InteractionSourceDetected e InteractionSourceLost.
2. Imposta lo stato HandDetected.
3. Annulla la sottoscrizione degli eventi InteractionSourceDetected e InteractionSourceLost.

Successivamente, il cursore verrà aggiornato da [Mr Input 210](holograms-210.md) in uno che mostra il feedback a seconda delle azioni dell'utente.

1. Nel pannello **gerarchia** selezionare l'oggetto **cursore** ed eliminarlo.
2. Nel pannello **progetto** cercare **CursorWithFeedback** e trascinarlo nel pannello **gerarchia** .
3. Fare clic **su InputManager** nel **Pannello gerarchia** , quindi trascinare l'oggetto **CursorWithFeedback** dalla **gerarchia** nel campo **cursore** **SimpleSinglePointerSelector**di InputManager, nella parte inferiore del **Controllo**.
4. Fare clic su **CursorWithFeedback** nella **gerarchia**.
5. Nel pannello **Inspector** espandere **dati sullo stato del cursore** sullo script del **cursore dell'oggetto** .

I **dati relativi allo stato del cursore** funzionano come segue:

* Qualsiasi stato di **osservazione** indica che non viene rilevata alcuna mano e che l'utente sta semplicemente cercando.
* Qualsiasi stato **Interact** indica che viene rilevata una mano o un controller.
* Qualsiasi stato **hover** indica che l'utente sta esaminando un ologramma.

### <a name="build-and-deploy"></a>Compilazione e distribuzione

* In Unity, usare **File > impostazioni di compilazione** per ricompilare l'applicazione.
* Aprire la cartella dell' **app** .
* Se non è già aperto, aprire la **soluzione ModelExplorer di Visual Studio**.
  * Se il progetto è già stato compilato o distribuito in Visual Studio durante la configurazione, è possibile aprire l'istanza di VS e fare clic su' ricarica tutto ' quando richiesto.
* In Visual Studio fare clic su **debug-> avvia senza eseguire debug** o premere **CTRL + F5**.
* Dopo la distribuzione dell'applicazione in HoloLens, chiudere il fitbox usando il gesto di tocco.
* Spostare la mano nella visualizzazione e puntare il dito dell'indice al cielo per iniziare a tenere traccia della mano.
* Spostare la mano sinistra, destra, verso l'alto e verso il basso.
* Osservare come cambia il cursore quando la mano viene rilevata e quindi persa dalla visualizzazione.
* Se si usa un auricolare immersivo, è necessario connettere e disconnettere il controller. Questo feedback diventa meno interessante in un dispositivo immersivo, perché un controller connesso sarà sempre "disponibile".

## <a name="chapter-2---navigation"></a>Capitolo 2-navigazione

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a>Obiettivi

* Usare gli eventi del movimento di spostamento per ruotare l'astronauta.

### <a name="instructions"></a>Istruzioni

Per usare i movimenti di navigazione nell'app, è necessario modificare **GestureAction.cs** per ruotare gli oggetti quando si verifica il movimento di navigazione. Inoltre, verranno aggiunti commenti e suggerimenti al cursore da visualizzare quando è disponibile la navigazione.

1. Nel pannello **gerarchia** espandere **CursorWithFeedback**.
2. Nella cartella **ologrammi** trovare l'asset **ScrollFeedback** .
3. Trascinare e rilasciare la prefabbricazione **ScrollFeedback** in **CursorWithFeedback** GameObject nella **gerarchia**.
4. Fare clic su **CursorWithFeedback**.
5. Nel pannello **Inspector** fare clic sul pulsante **Add Component** .
6. Nel menu digitare nella casella di ricerca **CursorFeedback**. Selezionare il risultato della ricerca.
7. Trascinare e rilasciare l'oggetto **ScrollFeedback** dalla **gerarchia** sulla proprietà dell' **oggetto gioco rilevato Scroll** nel componente **feedback del cursore** del **controllo**.
8. Nel pannello **gerarchia** selezionare l'oggetto **Astron** .
9. Nel pannello **Inspector** fare clic sul pulsante **Add Component** .
10. Nel menu digitare l' **azione di movimento**della casella di ricerca. Selezionare il risultato della ricerca.

Successivamente, aprire **GestureAction.cs** in Visual Studio. Nel codice esercizio 2. c, modificare lo script per eseguire le operazioni seguenti:

1. **Ruotare l'** oggetto astror ogni volta che viene eseguito un movimento di navigazione.
2. Calcolare **rotationFactor** per controllare la quantità di rotazione applicata all'oggetto.
3. **Ruotare l'oggetto** intorno all'asse y quando l'utente sposta la mano verso sinistra o verso destra.

Completare gli esercizi di codifica 2. c nello script oppure sostituire il codice con la soluzione completata seguente:

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

Si noterà che gli altri eventi di navigazione sono già stati compilati con alcune informazioni. Viene eseguito il push di GameObject nello stack modale InputSystem's del Toolkit, in modo che l'utente non debba mantenere lo stato attivo sull'astronauta dopo che la rotazione è iniziata. Al termine, si estrae il GameObject dallo stack una volta completato il movimento.

### <a name="build-and-deploy"></a>Compilazione e distribuzione

1. Ricompilare l'applicazione in Unity e quindi compilare e distribuire da Visual Studio per eseguirla in HoloLens.
2. Osservando l'astronauta, due frecce dovrebbero apparire su entrambi i lati del cursore. Questo nuovo oggetto visivo indica che l'astronauta può essere ruotato.
3. Posizionare la mano nella posizione pronta (indice puntato verso il cielo), in modo che il HoloLens inizi a tenere traccia della mano.
4. Per ruotare l'astronauta, abbassare il dito dell'indice in una posizione di pizzico, quindi spostare la mano verso sinistra o destra per attivare il movimento NavigationX.

## <a name="chapter-3---hand-guidance"></a>Capitolo 3-linee guida

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a>Obiettivi

* Usare il **punteggio delle linee guida** per aiutare a prevedere quando il rilevamento mano andrà perso.
* Fornire **commenti e suggerimenti sul cursore** da visualizzare quando l'utente si avvicina al bordo di visualizzazione della fotocamera.

### <a name="instructions"></a>Istruzioni

1. Nel pannello **gerarchia** selezionare l'oggetto **CursorWithFeedback** .
2. Nel pannello **Inspector** fare clic sul pulsante **Add Component** .
3. Nel menu digitare le **istruzioni**della casella di ricerca. Selezionare il risultato della ricerca.
4. Nella cartella olografici del pannello del **progetto** individuare l'asset **HandGuidanceFeedback** .
5. Trascinare e rilasciare l'asset **HandGuidanceFeedback** sulla proprietà **indicatore della mano guida** nel pannello **Inspector** .

### <a name="build-and-deploy"></a>Compilazione e distribuzione

* Ricompilare l'applicazione in Unity e quindi compilare e distribuire da Visual Studio per sperimentare l'app in HoloLens.
* È possibile passare alla visualizzazione e aumentare il dito dell'indice per tenerne traccia.
* Iniziare a ruotare l'astronauta con il movimento di navigazione (pizzicare il dito dell'indice e il pollice insieme).
* Spostare la mano all'estrema sinistra, a destra, in alto e in basso.
* Man mano che si avvicina il bordo del frame di movimento, viene visualizzata una freccia accanto al cursore per avvisare che il rilevamento della mano andrà perso. La freccia indica quale direzione spostare la mano per evitare che il rilevamento vada perso.

## <a name="chapter-4---manipulation"></a>Capitolo 4-manipolazione

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a>Obiettivi

* Usare gli eventi di manipolazione per spostare l'astronauta con le mani.
* Fornire commenti e suggerimenti sul cursore per informare l'utente quando è possibile utilizzare la manipolazione.

### <a name="instructions"></a>Istruzioni

GestureManager.cs e AstronautManager.cs ci consentiranno di eseguire le operazioni seguenti:

1. Usare la parola chiave Speech "**Move Astronaut**" per abilitare i movimenti di **manipolazione** e la "**ruota astronauta**" per disabilitarli.
2. Passa a rispondere al riconoscitore del **movimento di manipolazione**.

Ma veniamo al dunque.

1. Nel pannello **gerarchia** creare un nuovo GameObject vuoto. Assegnare al file il nome "**AstronautManager**".
2. Nel pannello **Inspector** fare clic sul pulsante **Add Component** .
3. Nel menu digitare nella casella di ricerca **gestione astronauti**. Selezionare il risultato della ricerca.
4. Nel pannello **Inspector** fare clic sul pulsante **Add Component** .
5. Nel menu digitare l' **origine input vocale**della casella di ricerca. Selezionare il risultato della ricerca.

Verranno ora aggiunti i comandi vocali necessari per controllare lo stato di interazione dell'astronauta.

1. Espandere la sezione Keywords nel **controllo**.
2. **+** Fare clic sul lato destro per aggiungere una nuova parola chiave.
3. Digitare la parola chiave come **Move Astronaut**. Se lo si desidera, è possibile aggiungere un tasto di scelta rapida.
4. **+** Fare clic sul lato destro per aggiungere una nuova parola chiave.
5. Digitare la parola chiave come **ruota astronauta**. Se lo si desidera, è possibile aggiungere un tasto di scelta rapida.
6. Il codice del gestore corrispondente si trova in **GestureAction.cs**nel gestore **ISpeechHandler. OnSpeechKeywordRecognized** .

![Come configurare l'origine di input vocale per il capitolo 4](images/holograms211-speech.png)

Successivamente, verrà configurato il feedback di manipolazione sul cursore.

1. Nella cartella olografici del pannello del **progetto** individuare l'asset **PathingFeedback** .
2. Trascinare e rilasciare la prefabbricazione **PathingFeedback** nell'oggetto **CursorWithFeedback** della **gerarchia**.
3. Nel pannello **gerarchia** fare clic su **CursorWithFeedback**.
4. Trascinare e rilasciare l'oggetto **PathingFeedback** dalla **gerarchia** alla proprietà dell' **oggetto del gioco rilevato nel percorso** nel componente **feedback del cursore** del **controllo**.

A questo punto è necessario aggiungere il codice a **GestureAction.cs** per abilitare gli elementi seguenti:

1. Aggiungere codice alla funzione **IManipulationHandler. OnManipulationUpdated** che sposta l'astronauta quando viene rilevato un movimento di **manipolazione** .
2. Calcolare il **vettore di spostamento** per determinare il punto in cui deve essere spostato l'astronauta in base alla posizione della mano.
3. **Spostare** l'astronauta nella nuova posizione.

Completare il codice esercizio 4. a in **GestureAction.cs**o usare la soluzione completa seguente:

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
            transform.position = manipulationOriginalPosition + eventData.CumulativeDelta;
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

### <a name="build-and-deploy"></a>Compilazione e distribuzione

* Ricompilare in Unity e quindi compilare e distribuire da Visual Studio per eseguire l'app in HoloLens.
* Spostare la mano davanti alla HoloLens e aumentare il dito dell'indice in modo che possa essere rilevata.
* Concentrare il cursore sull'astronauta.
* Pronunciare ' Move Astronaut ' per spostare l'astronauta con un movimento di manipolazione.
* Attorno al cursore verranno visualizzate quattro frecce per indicare che il programma risponderà a eventi di manipolazione.
* Abbassare il dito dell'indice verso il basso e tenerli insieme.
* Man mano che ci si sposta, si sposta anche l'astronauta (si tratta di una manipolazione).
* Aumentare il dito dell'indice per interrompere la manipolazione dell'astronauta.
* Nota: Se non si dice "Sposta astronauta" prima di spostare la mano, verrà usato il movimento di navigazione.
* Pronunciare ' ruota astronauta ' per tornare allo stato girevole.

## <a name="chapter-5---model-expansion"></a>Capitolo 5-espansione del modello

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a>Obiettivi

* Espandere il modello astronauta in più parti più piccole con cui l'utente può interagire.
* Spostare ogni pezzo singolarmente utilizzando movimenti di spostamento e manipolazione.

### <a name="instructions"></a>Istruzioni

In questa sezione vengono eseguite le attività seguenti:

1. Aggiungere una nuova parola chiave "**expand Model**" per espandere il modello Astronaut.
2. Aggiungere una nuova parola chiave "**Reset Model**" per restituire il modello al formato originale.

A tale scopo, aggiungere altre due parole chiave all'origine di input vocale del capitolo precedente. Verrà inoltre illustrato un altro modo per gestire gli eventi di riconoscimento.

1. Fare clic su Back on **AstronautManager** nel **controllo** ed espandere la sezione Keywords nel **controllo**.
2. **+** Fare clic sul lato destro per aggiungere una nuova parola chiave.
3. Digitare la parola chiave come **Espandi modello**. Se lo si desidera, è possibile aggiungere un tasto di scelta rapida.
4. **+** Fare clic sul lato destro per aggiungere una nuova parola chiave.
5. Digitare la parola chiave come **Reimposta modello**. Se lo si desidera, è possibile aggiungere un tasto di scelta rapida.
6. Nel pannello **Inspector** fare clic sul pulsante **Add Component** .
7. Nel menu digitare il **gestore di input vocale**della casella di ricerca. Selezionare il risultato della ricerca.
8. Il controllo **è un listener globale**, perché si vuole che questi comandi funzionino indipendentemente dal GameObject che si sta concentrando.
9. Fare clic **+** sul pulsante e selezionare **Espandi modello** dall'elenco a discesa parola chiave.
10. Fare clic su in risposta e trascinare AstronautManager dalla gerarchia nel campo None **+** (Object).
11. A questo punto, fare clic sull'elenco a discesa **Nessuna funzione** , selezionare **AstronautManager**, quindi **ExpandModelCommand**.
12. Fare clic sul pulsante del gestore **+** di input vocale e selezionare **Reimposta modello** dall'elenco a discesa parola chiave.
13. Fare clic su in risposta e trascinare AstronautManager dalla gerarchia nel campo None **+** (Object).
14. A questo punto, fare clic sull'elenco a discesa **Nessuna funzione** , selezionare **AstronautManager**, quindi **ResetModelCommand**.

![Come configurare l'origine e il gestore di input vocale per il capitolo 5](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a>Compilazione e distribuzione

* Prova! Compilare e distribuire l'app in HoloLens.
* Supponiamo **Espandi modello** per visualizzare il modello astronauta espanso.
* Usare la **navigazione** per ruotare le singole parti del seme degli astronauti.
* Supponiamo di **spostare** l'astronauta e quindi di usare la **manipolazione** per spostare singoli pezzi del seme degli astronauti.
* Dire **ruotare** l'astronauta per ruotare nuovamente le parti.
* Ad esempio **Reimposta modello** per restituire l'astronauta al formato originale.

## <a name="the-end"></a>La fine

La procedura è stata completata. A questo punto è **stato completato il Sig. input 211: Gesto**.

* Si è in grado di rilevare e rispondere agli eventi di rilevamento, spostamento e manipolazione della mano.
* Si comprende la differenza tra i movimenti di spostamento e manipolazione.
* Si è appreso come modificare il cursore per fornire commenti visivi quando viene rilevata una mano, quando una mano sta per andare persa e quando un oggetto supporta interazioni diverse (spostamento e manipolazione).

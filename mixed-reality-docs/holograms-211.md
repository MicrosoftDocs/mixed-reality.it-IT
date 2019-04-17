---
title: Input MR 211 - movimento
description: Seguire questa procedura dettagliata codifica con Unity, Visual Studio e HoloLens informazioni dettagliate sui concetti di movimento.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit unity, academy, esercitazione, movimento
ms.openlocfilehash: 76d2b4c0ac3d0a3783b091f7dc8c39548a18b548
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603387"
---
>[!NOTE]
>Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.  Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.  Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.  Essi verranno mantenute per continuare a utilizzare i dispositivi supportati. Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.  Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.

# <a name="mr-input-211-gesture"></a>Input di MR 211: Movimento

[I movimenti](gestures.md) Trasforma intenzione dell'utente in azione. I movimenti, gli utenti possono interagire con vntana. In questo corso, si apprenderà come tenere traccia delle lancette dell'utente, rispondere all'input dell'utente, e forniscono feedback all'utente d' parte dello stato e la posizione.

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

Nelle [MR nozioni di base 101](holograms-101.md), abbiamo utilizzato un movimento puntato semplice per interagire con i nostri vntana. A questo punto, verrà oltre il movimento indice puntato e vengono illustrati i concetti nuovi da:

* Rilevare quando è sottoposto a rilevamento manuale dell'utente e fornire commenti e suggerimenti all'utente.
* Per ruotare il vntana, utilizzare un gesto di spostamento.
* Fornire commenti e suggerimenti quando sta per passare dalla visualizzazione manuale dell'utente.
* Usare gli eventi di manipolazione per consentire agli utenti di spostare vntana con le mani.

In questo corso, questo aspetto verrà trattato il progetto di Unity **Esplora modelli**, che è stato creato [MR Input 210](holograms-210.md). L'amico astronautici è tornato per facilitare l'esplorazione di questi nuovi concetti di movimento.

>[!IMPORTANT]
>I video incorporati in ognuna delle sezioni seguenti sono stati registrati usando una versione precedente di Unity e il Toolkit di realtà mista. Anche se le istruzioni dettagliate sono accurate e aggiornate, è possibile visualizzare gli script e gli oggetti visivi nei video corrispondenti che non sono aggiornati. I video rimangono inclusi per ci si ricorderà più e perché i concetti illustrati sono applicano.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></th>
</tr><tr>
<td>Input di MR 211: Movimento</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Prima di iniziare

### <a name="prerequisites"></a>Prerequisiti

* Un PC Windows 10 configurate con i valori corretti [sono installati gli strumenti](install-the-tools.md).
* Alcuni basic C# capacità di programmazione.
* È necessario avere completato [MR nozioni di base 101](holograms-101.md).
* È necessario avere completato [MR Input 210](holograms-210.md).
* Un dispositivo HoloLens [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>File di progetto

* Scaricare il [file](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) necessarie per il progetto. Richiede Unity 2017.2 o versione successiva.
* Annullare la-archive i file sul desktop o altri facile da raggiungere percorso.

>[!NOTE]
>Se si desidera esaminare il codice sorgente prima di scaricare, ha [disponibile in GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).

### <a name="errata-and-notes"></a>Errori e note

* "Abilita Just My Code" deve essere disabilitato (*unchecked*) in Visual Studio in Strumenti -> Opzioni -> debug per poter raggiungere punti di interruzione nel codice.

## <a name="chapter-0---unity-setup"></a>Capitolo 0 - programma di installazione di Unity

### <a name="instructions"></a>Istruzioni

1. Avviare Unity.
2. Selezionare **aperto**.
3. Passare al **movimento** cartella è archiviato in precedenza di annullamento.
4. Individuare e selezionare il **Starting**/**Esplora modelli** cartella.
5. Scegliere il **selezionare la cartella** pulsante.
6. Nel **Project** panel, espandere il **scene** cartella.
7. Fare doppio clic su **ModelExplorer** scena a caricarlo in Unity.

### <a name="building"></a>Compilazione

1. In Unity, selezionare **File > Build Settings**.
2. Se **scene/ModelExplorer** non è elencato nella **scene nella compilazione**, fare clic su **aggiungere scene Open** per aggiungere la scena.
3. Se si sta sviluppando in modo specifico per HoloLens, impostare **dispositivo di destinazione** al **HoloLens**. In caso contrario, ci si trova sulla **tutti i dispositivi**.
4. Assicurarsi **tipo di compilazione** è impostata su **D3D** e **SDK** è impostata su **installata più recente** (che deve essere SDK 16299 o versione successiva).
5. Fai clic su **Compila**.
6. Creare un **nuova cartella** denominato "App".
7. Solo clic i **App** cartella.
8. Premere **selezionare la cartella** e Unity verrà avviata la compilazione del progetto per Visual Studio.

Quando Unity viene eseguita, verrà visualizzata una finestra di Esplora File.

1. Aprire il **App** cartella.
2. Aprire il **soluzione ModelExplorer Visual Studio**.

Se la distribuzione in HoloLens:

1. Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione di debug per **Release** e da ARM a **x86**.
2. Fare clic sull'elenco a discesa sulla freccia accanto al pulsante computer locale e selezionare **computer remoto**.
3. Immettere **l'indirizzo IP del dispositivo HoloLens** e impostare la modalità di autenticazione **universale (protocollo non crittografato)**. Fare clic su **Seleziona**. Se non si conosce l'indirizzo IP del dispositivo, esaminare **Impostazioni > rete e Internet > Opzioni avanzate**.
4. Nella barra dei menu superiore, fare clic su **Debug -> Avvia senza eseguire debug** o premere **Ctrl + F5**. Se questa è la prima volta che la distribuzione nel dispositivo, devi [abbinarlo a Visual Studio](using-visual-studio.md#pairing-your-device-hololens).
5. Quando l'app è distribuita, ignorare il **Fitbox** con un **movimento selezionare**.

Se la distribuzione in un visore VR immersivi:

1. Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione di debug per **Release** e da ARM a **x64**.
2. Verificare che la destinazione di distribuzione è impostata su **computer locale**.
3. Nella barra dei menu superiore, fare clic su **Debug -> Avvia senza eseguire debug** o premere **Ctrl + F5**.
4. Quando l'app è distribuita, ignorare il **Fitbox** spostando il trigger in un controller di movimento.

>[!NOTE]
>È possibile riscontrare alcuni errori rosso nel Pannello di errori di Visual Studio. È possibile ignorarli. Passare al pannello di Output per visualizzare effettivamente lo stato della compilazione. Gli errori nel Pannello di Output è necessario rendere una correzione (più spesso che sono causati da un errore in uno script).

## <a name="chapter-1---hand-detected-feedback"></a>Capitolo 1 - mano rilevato commenti e suggerimenti

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a>Obiettivi

* Gli eventi di rilevamento per presentare la sottoscrizione.
* Usare risposta del cursore da visualizzare agli utenti quando è sottoposto a rilevamento una mano.

### <a name="instructions"></a>Istruzioni

* Nel **gerarchia** panel, espandere il **InputManager** oggetto.
* Cercare e selezionare il **GesturesInput** oggetto.

Il **InteractionInputSource.cs** script esegue queste operazioni:

1. Sottoscrive gli eventi InteractionSourceDetected e InteractionSourceLost.
2. Imposta lo stato HandDetected.
3. Annulla la sottoscrizione dagli eventi InteractionSourceDetected e InteractionSourceLost.

Successivamente, aggiornamento verrà eseguito il cursore a partire dal [MR Input 210](holograms-210.md) in un unico che mostra i commenti e suggerimenti a seconda delle azioni dell'utente.

1. Nel **gerarchia** riquadro, seleziona il **cursore** dell'oggetto e lo elimini.
2. Nel **Project** del pannello, cercare **CursorWithFeedback** e trascinarlo nel **gerarchia** pannello.
3. Fare clic su **InputManager** nel **gerarchia** pannello, quindi trascinare il **CursorWithFeedback** dell'oggetto dal **gerarchia** nel Del InputManager **SimpleSinglePointerSelector**del **cursore** campo, nella parte inferiore della **Inspector**.
4. Fare clic sui **CursorWithFeedback** nel **gerarchia**.
5. Nel **Inspector** panel, espandere **i dati sullo stato del cursore** sul **oggetto cursore** script.

Il **i dati sullo stato del cursore** funziona come segue:

* Eventuali **osservazione** stato significa che non viene rilevata alcuna mano e l'utente viene semplicemente esaminato.
* Eventuali **Interact** stato significa che una mano o un controller è stato rilevato.
* Eventuali **passa il mouse** stato indica che l'utente sta guardando ologramma.

### <a name="build-and-deploy"></a>Compilare e distribuire

* In Unity, usare **File > Build Settings** per ricompili l'applicazione.
* Aprire il **App** cartella.
* Se non è già aperto, aprire il **soluzione di Visual Studio ModelExplorer**.
  * (Se è stato creato o distribuito questo progetto in Visual Studio durante la configurazione, quindi è possibile aprire quell'istanza di Visual Studio e fare clic su 'Ricarica tutto' quando viene richiesto).
* In Visual Studio, fare clic su **Debug -> Avvia senza eseguire debug** o premere **Ctrl + F5**.
* Dopo la distribuzione dell'applicazione per il HoloLens, ignorare il fitbox tramite il movimento indice puntato.
* Spostare la mano in visualizzazione e puntare il dito indice le possibilità di avviare manualmente di rilevamento.
* Spostare la mano a sinistra, destra, alto e verso il basso.
* Guarda come il cursore cambia quando viene rilevata e quindi perso dalla visualizzazione la mano.
* Se si usa un visore VR immersivi, è possibile connettere e disconnettere il controller. Questo feedback diventa meno interessanti in un dispositivo coinvolgente, come un controller connesso sarà sempre "disponibile".

## <a name="chapter-2---navigation"></a>Capitolo 2 - navigazione

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a>Obiettivi

* Usare gli eventi di movimento di navigazione per ruotare l'astronautici.

### <a name="instructions"></a>Istruzioni

Per usare i movimenti di navigazione nell'app, si intende modificare **GestureAction.cs** ruotare gli oggetti quando si verifica il movimento di navigazione. Inoltre, si aggiungerà commenti e suggerimenti per il cursore da visualizzare quando l'esplorazione è disponibile.

1. Nel **gerarchia** panel, espandere **CursorWithFeedback**.
2. Nel **Vntana** cartella trovare il **ScrollFeedback** asset.
3. Trascinare e rilasciare il **ScrollFeedback** prefab nel **CursorWithFeedback** GameObject nel **gerarchia**.
4. Fare clic su **CursorWithFeedback**.
5. Nel **Inspector** del pannello, fare clic sui **Add Component** pulsante.
6. Nel menu, digitare nella casella di ricerca **CursorFeedback**. Selezionare il risultato della ricerca.
7. Trascinare e rilasciare il **ScrollFeedback** dall'oggetto il **gerarchia** nel **scorrimento rilevato Game Object** proprietà nel **risposta del cursore**nel componente di **Inspector**.
8. Nel **gerarchia** riquadro, seleziona la **AstroMan** oggetto.
9. Nel **Inspector** del pannello, fare clic sui **Add Component** pulsante.
10. Nel menu, digitare nella casella di ricerca **azione gesto**. Selezionare il risultato della ricerca.

Successivamente, aprire **GestureAction.cs** in Visual Studio. Nella codifica esercitare 2.c, modificare lo script per eseguire le operazioni seguenti:

1. **Ruotare la AstroMan** dell'oggetto ogni volta che viene eseguito un movimento di navigazione.
2. Calcolare le **rotationFactor** per controllare la quantità di rotazione applicata all'oggetto.
3. **Ruotare l'oggetto** intorno all'asse y quando l'utente sposta le mani verso sinistra o destra.

Scrittura di codice completo esercita 2.c nello script, o sostituire il codice con la soluzione completata seguente:

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

Si noterà che gli altri eventi di navigazione sono già compilati con alcune informazioni. Si inserisce gli elementi GameObject nel Toolkit modale dello stack di InputSystem, in modo che l'utente non dispone di mantenere l'attenzione sull'astronautici una volta iniziata la rotazione. Di conseguenza, viene segnalato il GameObject dallo stack dopo aver completato il movimento.

### <a name="build-and-deploy"></a>Compilare e distribuire

1. Ricompilare l'applicazione in Unity e quindi compilare e distribuire da Visual Studio per eseguirla di HoloLens.
2. Fissare astronautici, due frecce dovrebbe essere visualizzato su entrambi i lati del cursore. Questo nuovo oggetto visivo indica che possono essere ruotate di astronautici.
3. Posizionare la mano nella posizione pronta (dito indice rivolta verso il cielo) in modo di HoloLens avvierà la mano di rilevamento.
4. Per ruotare l'astronautici, ridurre il dito indice in una posizione con avvicinamento delle dita e quindi spostare la mano verso sinistra o destra per attivare il movimento NavigationX.

## <a name="chapter-3---hand-guidance"></a>Capitolo 3 - linee guida di mano

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a>Obiettivi

* Uso **punteggio di informazioni aggiuntive a mano** per aiutare a stimare quando mano rilevamento andranno perse.
* Fornire **commenti e suggerimenti sul cursore** da visualizzare quando il manuale dell'utente si avvicina al bordo della camera della visualizzazione.

### <a name="instructions"></a>Istruzioni

1. Nel **gerarchia** riquadro, seleziona la **CursorWithFeedback** oggetto.
2. Nel **Inspector** del pannello, fare clic sui **Add Component** pulsante.
3. Nel menu, digitare nella casella di ricerca **mano indicazioni**. Selezionare il risultato della ricerca.
4. Nel **Project** pannello **Vntana** cartella trovare il **HandGuidanceFeedback** asset.
5. Trascinare e rilasciare il **HandGuidanceFeedback** asset nel **mano indicazioni indicatore** proprietà nel **Inspector** pannello.

### <a name="build-and-deploy"></a>Compilare e distribuire

* Ricompilare l'applicazione in Unity e quindi compilare e distribuire da Visual Studio per provare l'app in HoloLens.
* Portare la mano in visualizzazione e generare il dito indice alla volta registrato.
* Avviare la rotazione di astronautici con il movimento di navigazione (il dito indice indietro e Avanti thumb insieme).
* Spostare la mano estrema sinistra, destra, freccia su e freccia giù.
* Come la mano si avvicina il bordo del frame movimento, viene visualizzata una freccia accanto al cursore per avvisare l'utente mano in corso di rilevamento andranno perso. La freccia indica la direzione per spostare la mano per evitare che verifica la perdita.

## <a name="chapter-4---manipulation"></a>Capitolo 4 - modifica

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a>Obiettivi

* Usare gli eventi di manipolazione per spostare l'astronautici con le mani.
* Fornire commenti e suggerimenti sul cursore per informare l'utente quando la manipolazione può essere utilizzata.

### <a name="instructions"></a>Istruzioni

GestureManager.cs e AstronautManager.cs ci consentirà di eseguire le operazioni seguenti:

1. Usare la parola chiave vocale "**spostare astronautici**" per abilitare **Manipulation** movimenti e "**ruotare astronautici**" per disabilitarli.
2. Passare alla risposta per il **riconoscitore di movimento manipolazione**.

Cominciamo.

1. Nel **gerarchia** panel, creare un nuovo GameObject vuoto. Denominarla "**AstronautManager**".
2. Nel **Inspector** del pannello, fare clic sui **Add Component** pulsante.
3. Nel menu, digitare nella casella di ricerca **astronautici Manager**. Selezionare il risultato della ricerca.
4. Nel **Inspector** del pannello, fare clic sui **Add Component** pulsante.
5. Nel menu, digitare nella casella di ricerca **origine di Input vocale**. Selezionare il risultato della ricerca.

A questo punto si aggiungerà i comandi vocali necessari per controllare lo stato di astronautici l'interazione.

1. Espandere la **parole chiave** sezione il **Inspector**.
2. Scegliere il **+** sul lato destro per aggiungere una nuova parola chiave.
3. Digitare la parola chiave as **spostare astronautici**. È possibile aggiungere un tasto di scelta rapida se si desidera.
4. Scegliere il **+** sul lato destro per aggiungere una nuova parola chiave.
5. Digitare la parola chiave as **ruotare astronautici**. È possibile aggiungere un tasto di scelta rapida se si desidera.
6. Il codice del gestore corrispondente è reperibile nel **GestureAction.cs**, nella **ISpeechHandler.OnSpeechKeywordRecognized** gestore.

![Come configurare l'origine di Input vocale per capitolo 4](images/holograms211-speech.png)

Si verranno successivamente, configurare i commenti e suggerimenti di manipolazione sul cursore.

1. Nel **Project** pannello **Vntana** cartella trovare il **PathingFeedback** asset.
2. Trascinare e rilasciare il **PathingFeedback** prefab nel **CursorWithFeedback** dell'oggetto nel **gerarchia**.
3. Nel **gerarchia** del pannello, fare clic su **CursorWithFeedback**.
4. Trascinare e rilasciare il **PathingFeedback** dall'oggetto il **gerarchia** nel **ricerca del percorso rilevato Game Object** proprietà nel **risposta del cursore**nel componente di **Inspector**.

È ora necessario aggiungere codice al **GestureAction.cs** per abilitare le opzioni seguenti:

1. Aggiungere il codice per il **IManipulationHandler.OnManipulationUpdated** funzione, che verrà spostato l'astronautici quando una **manipolazione** viene rilevato movimento.
2. Calcolare le **vettore di movimento** per determinare dove devono essere spostati gli astronautici basato d' parte posizione.
3. **Spostare** l'astronautici nella nuova posizione.

Scrittura di codice completo esercitare 4.a nel **GestureAction.cs**, oppure usare la nostra soluzione completata riportato di seguito:

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

### <a name="build-and-deploy"></a>Compilare e distribuire

* Ricompilazione in Unity e quindi compilare e distribuire da Visual Studio per eseguire l'app in HoloLens.
* Spostare la mano davanti il HoloLens e generare il dito indice in modo che sia possibile il rilevamento.
* Lo stato attivo del cursore tramite l'astronautici.
* Ad esempio 'Spostare astronautici' per spostare l'astronautici con un gesto di manipolazione.
* Quattro frecce apparirà attorno al cursore per indicare che il programma ora risponderanno a eventi di manipolazione.
* Ridurre il dito indice down il pollice e mantenerli estratte insieme.
* Quando si sposta la mano tutto, l'astronautici sposterà troppo (si tratta di modifica).
* Generare il dito indice per interrompere la modifica di astronautici.
* Nota: Se non dirà piuttosto 'Spostare astronautici' prima di spostare la mano verrà invece utilizzato il movimento di navigazione.
* Ad esempio 'Ruotare astronautici' per tornare allo stato orientamento modificabile.

## <a name="chapter-5---model-expansion"></a>Capitolo 5: espansione del modello

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a>Obiettivi

* Espandere il modello astronautici in più, componenti più piccoli che l'utente può interagire con.
* Spostare ogni componente singolarmente utilizzando i movimenti di navigazione e modifica.

### <a name="instructions"></a>Istruzioni

In questa sezione, si completeranno le attività seguenti:

1. Aggiungere una nuova parola chiave "**modello espandere**" per espandere il modello astronautici.
2. Aggiungere una nuova parola chiave "**reimpostare modello**" per restituire il modello nel formato originale.

Faremo mediante l'aggiunta di due più parole chiave per l'origine di Input vocale nel capitolo precedente. Illustreremo anche un altro modo per gestire gli eventi di riconoscimento.

1. Fare clic nuovamente sul **AstronautManager** nel **Inspector** ed espandere il **parole chiave** sezione la **Inspector**.
2. Scegliere il **+** sul lato destro per aggiungere una nuova parola chiave.
3. Digitare la parola chiave as **espande modello**. È possibile aggiungere un tasto di scelta rapida se si desidera.
4. Scegliere il **+** sul lato destro per aggiungere una nuova parola chiave.
5. Digitare la parola chiave as **reimpostare modello**. È possibile aggiungere un tasto di scelta rapida se si desidera.
6. Nel **Inspector** del pannello, fare clic sui **Add Component** pulsante.
7. Nel menu, digitare nella casella di ricerca **gestore di Input vocale**. Selezionare il risultato della ricerca.
8. Controllare **Listener globale è**, dal momento che intendiamo utilizzare questi comandi al indipendentemente dal fatto il GameObject parliamo.
9. Scegliere il **+** e selezionare **espandere modello** dall'elenco a discesa parola chiave.
10. Fare clic sui **+** nella risposta e quindi trascinare il **AstronautManager** dal **gerarchia** nel **None (oggetto)** campo.
11. A questo punto, fare clic sui **funzione No** elenco a discesa, seleziona **AstronautManager**, quindi **ExpandModelCommand**.
12. Scegliere il gestore di Input vocale **+** e selezionare **reimpostazione modello** dall'elenco a discesa parola chiave.
13. Fare clic sui **+** nella risposta e quindi trascinare il **AstronautManager** dal **gerarchia** nel **None (oggetto)** campo.
14. A questo punto, fare clic sui **funzione No** elenco a discesa, seleziona **AstronautManager**, quindi **ResetModelCommand**.

![Come configurare l'origine di Input vocale e gestore per il capitolo 5](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a>Compilare e distribuire

* Prova! Compilare e distribuire l'app per la HoloLens.
* Pronunciare **modello espandere** per visualizzare il modello astronautici espanso.
* Uso **navigazione** ruotare singole parti del seme astronautici.
* Pronunciare **spostare astronautici** e quindi usare **manipolazione** spostare singole parti del seme astronautici.
* Pronunciare **ruotare astronautici** per ruotare le parti nuovamente.
* Pronunciare **reimpostare modello** per restituire l'astronautici nel formato originale.

## <a name="the-end"></a>La fine

La procedura è stata completata. Sono stati completati **SIG Input 211: Movimento**.

* Sai come rilevare e rispondere per presentare gli eventi di rilevamento, navigazione e modifica.
* Comprendere la differenza tra i movimenti di navigazione e modifica.
* Si sa come modificare il cursore per fornire indicazioni visive per quando viene rilevata una mano, quando una mano sta per essere perso e quando un oggetto supporta diverse interazioni (spostamento vs manipolazione).

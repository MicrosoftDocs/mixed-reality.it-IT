---
title: Input MR 212-Voice
description: Seguire questa procedura dettagliata di codifica usando Unity, Visual Studio e HoloLens per informazioni dettagliate sui concetti vocali.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academy, esercitazione, Voice
ms.openlocfilehash: 9db503ea4c7db9a3eb272ad9663024ca3a407dda
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434594"
---
>[!NOTE]
>Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.  Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.  Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.  Verranno mantenuti per continuare a usare i dispositivi supportati. Per HoloLens 2 è stata pubblicata [una nuova serie di esercitazioni](mrlearning-base.md) .

<br>

# <a name="mr-input-212-voice"></a>Input di MR 212: Voice

L' [input vocale](voice-input.md) ci offre un altro modo per interagire con gli ologrammi. I comandi vocali funzionano in modo molto naturale e semplice. Progettare i comandi vocali in modo che siano:

* Naturale
* Facile da ricordare
* Contesto appropriato
* Sufficientemente distinto dalle altre opzioni nello stesso contesto

>[!VIDEO https://www.youtube.com/embed/BYpYsVFYjdw]

In [Mr nozioni di base 101](holograms-101.md)è stato usato KeywordRecognizer per creare due semplici comandi vocali. In MR input 212 verrà illustrato in dettaglio come:

* Progettare comandi vocali ottimizzati per il motore di sintesi vocale HoloLens.
* Informare l'utente di quali comandi vocali sono disponibili.
* Confermare che è stato ascoltato il comando Voice dell'utente.
* Comprendere le informazioni che l'utente sta dicendo, usando un riconoscimento di dettatura.
* Usare un sistema di riconoscimento della grammatica per restare in ascolto dei comandi basati su un file SRGS o una specifica della grammatica del riconoscimento vocale.

In questo corso, viene rivisitata Esplora modelli, che è stata compilata in [Mr input 210](holograms-210.md) e [Mr input 211](holograms-211.md).

>[!IMPORTANT]
>I video incorporati in ognuno dei capitoli seguenti sono stati registrati usando una versione precedente di Unity e il Toolkit di realtà mista. Sebbene le istruzioni dettagliate siano accurate e aggiornate, è possibile visualizzare gli script e gli oggetti visivi nei video corrispondenti non aggiornati. I video rimangono inclusi per i posteri e perché i concetti trattati sono ancora validi.


## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td>Input di MR 212: Voice</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Prima di iniziare

### <a name="prerequisites"></a>Prerequisiti

* Un PC Windows 10 configurato con gli [strumenti corretti installati](install-the-tools.md).
* Alcune funzionalità C# di programmazione di base.
* Sono state completate le [nozioni di base 101](holograms-101.md).
* È necessario aver completato il [sig. Input 210](holograms-210.md).
* È necessario aver completato il [sig. Input 211](holograms-211.md).
* Un dispositivo HoloLens [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>File di progetto

* Scaricare i [file](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) richiesti dal progetto. Richiede Unity 2017,2 o versione successiva.
* Annullare l'archiviazione dei file sul desktop o in un'altra posizione facile da raggiungere.

>[!NOTE]
>Se si vuole esaminare il codice sorgente prima del download, è [disponibile in GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).

### <a name="errata-and-notes"></a>Errori e note

* "Enable Just My Code" deve essere disabilitato (*deselezionato*) in Visual Studio in strumenti-Opzioni >-> debug per raggiungere i punti di interruzione nel codice.

## <a name="unity-setup"></a>Configurazione di Unity

### <a name="instructions"></a>Istruzioni

1. Avvia Unity.
2. Selezionare **Apri**.
3. Passare alla cartella **HolographicAcademy-ologrammes-212-Voice** precedentemente non archiviata.
4. Individuare e selezionare la cartella **avvio**/**Esplora modelli** .
5. Fare clic sul pulsante **Seleziona cartella** .
6. Nel pannello **progetto** espandere la cartella **Scenes** .
7. Fare doppio clic su **ModelExplorer** scene per caricarla in Unity.

### <a name="building"></a>Build

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
4. Nella barra dei menu superiore fare clic su **debug-> avvia senza eseguire debug** o premere **CTRL + F5**. Se questa è la prima volta che si esegue la distribuzione nel dispositivo, sarà necessario [associarla a Visual Studio](using-visual-studio.md#pairing-your-device).
5. Quando l'app è stata distribuita, chiudere il **fitbox** con un **movimento di selezione**.

Se si esegue la distribuzione in un auricolare immersivo:

1. Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione da debug a **Release** e da ARM a **x64**.
2. Verificare che la destinazione di distribuzione sia impostata su **computer locale**.
3. Nella barra dei menu superiore fare clic su **debug-> avvia senza eseguire debug** o premere **CTRL + F5**.
4. Quando l'app è stata distribuita, chiudere il **fitbox** estraendo il trigger in un controller di movimento.

>[!NOTE]
>Si potrebbero notare alcuni errori rossi nel pannello Errori di Visual Studio. È possibile ignorarli. Passare al pannello output per visualizzare lo stato di avanzamento della compilazione. Per gli errori nel pannello di output sarà necessario eseguire una correzione (la maggior parte delle volte è causata da un errore in uno script).

## <a name="chapter-1---awareness"></a>Capitolo 1-riconoscimento

>[!VIDEO https://www.youtube.com/embed/fDwijJWuEc0]

### <a name="objectives"></a>Obiettivi

* Informazioni su **DOS e non** sulla progettazione dei comandi vocali.
* Usare **KeywordRecognizer** per aggiungere comandi vocali basati su sguardi.
* Consentire agli utenti di riconoscere i comandi vocali utilizzando il **feedback**del cursore.

### <a name="voice-command-design"></a>Progettazione comando vocale

In questo capitolo verrà illustrato come progettare comandi vocali. Quando si creano comandi vocali:

#### <a name="do"></a>DO

* Creare comandi concisi. Non si vuole usare *"Riproduci il video attualmente selezionato"* , perché questo comando non è conciso e può essere facilmente dimenticato dall'utente. È invece consigliabile usare: *"riprodurre video"* , perché è conciso e presenta più sillabe.
* Usare un vocabolario semplice. Provare sempre a usare parole e frasi comuni che possono essere facilmente individuate e memorizzate dall'utente. Se, ad esempio, l'applicazione dispone di un oggetto nota che potrebbe essere visualizzato o nascosto, non è possibile utilizzare il comando *"Mostra cartello"* , perché "cartello" è un termine raramente utilizzato. Usare invece il comando: *"show note"* per rivelare la nota nell'applicazione.
* Mantenere la coerenza. I comandi vocali devono essere mantenuti coerenti nell'intera applicazione. Si supponga di avere due scene nell'applicazione e che entrambe le scene includano un pulsante per la chiusura dell'applicazione. Se la prima scena usava il comando *"Exit"* per attivare il pulsante, ma la seconda scena usava il comando *"close app"* , l'utente sarà molto confuso. Se la stessa funzionalità viene mantenute tra più scene, è necessario usare lo stesso comando Voice per attivarlo.

#### <a name="dont"></a>Non

* Usare i comandi a sillaba singola. Ad esempio, se si crea un comando vocale per riprodurre un video, è consigliabile evitare di usare il semplice comando *"Play"* , poiché si tratta solo di una singola sillaba e potrebbe essere facilmente persa dal sistema. È invece consigliabile usare: *"riprodurre video"* , perché è conciso e presenta più sillabe.
* Usare i comandi di sistema. Il comando *"Select"* è riservato dal sistema per attivare un evento tap per l'oggetto attualmente attivo. Non usare nuovamente il comando *"Select"* in una parola chiave o in una frase, perché potrebbe non funzionare come previsto. Se, ad esempio, il comando Voice per la selezione di un cubo nell'applicazione era *"Select Cube"* , ma l'utente stava osservando una sfera quando ha pronunciato il comando, viene invece selezionata la sfera. Analogamente, i comandi della barra dell'app sono abilitati. Non usare i comandi di riconoscimento vocale seguenti nella visualizzazione CoreWindow:
    1. Indietro
    2. Strumento di scorrimento
    3. Strumento Zoom
    4. Strumento di trascinamento
    5. Adjust
    6. Remove
* Usare suoni simili. Provare a evitare di usare comandi vocali che fanno rima. Se si dispone di un'applicazione di acquisto che supporta *"Mostra archivio"* e *"Mostra più"* come comandi vocali, è necessario disabilitare uno dei comandi mentre l'altro è in uso. Ad esempio, è possibile usare il pulsante *"Mostra archivio"* per aprire l'archivio e quindi disabilitare il comando quando l'archivio è stato visualizzato in modo che il comando *"Mostra più"* possa essere usato per l'esplorazione.

### <a name="instructions"></a>Istruzioni

* Nel pannello **gerarchia** di Unity usare lo strumento di ricerca per trovare l'oggetto **holoComm_screen_mesh** .
* Fare doppio clic sull'oggetto **holoComm_screen_mesh** per visualizzarlo nella **scena**. Si tratta dell'espressione di controllo dell'astronauta, che risponderà ai comandi vocali.
* Nel pannello **Inspector** individuare il componente di **origine input vocale (script)** .
* Espandere la sezione **Keywords (parole chiave** ) per visualizzare il comando Voice supportato: **Open Communicator**.
* Fare clic sull'ingranaggio a destra, quindi selezionare **Modifica script**.
* Esplorare **SpeechInputSource.cs** per comprendere in che modo Usa **KeywordRecognizer** per aggiungere comandi vocali.

### <a name="build-and-deploy"></a>Compilazione e distribuzione

* In Unity, usare **File > impostazioni di compilazione** per ricompilare l'applicazione.
* Aprire la cartella dell' **app** .
* Aprire la **soluzione ModelExplorer di Visual Studio**.

Se il progetto è già stato compilato o distribuito in Visual Studio durante la configurazione, è possibile aprire l'istanza di VS e fare clic su' ricarica tutto ' quando richiesto.

* In Visual Studio fare clic su **debug-> avvia senza eseguire debug** o premere **CTRL + F5**.
* Dopo la distribuzione dell'applicazione in HoloLens, chiudere la casella adatta usando il gesto di [tocco](gaze-and-commit.md#composite-gestures) .
* Guarda l'orologio dell'astronauta.
* Quando l'espressione di controllo ha lo stato attivo, verificare che il cursore venga modificato in un microfono. Questo fornisce il feedback che l'applicazione è in ascolto dei comandi vocali.
* Verificare che nell'espressione di controllo sia presente una descrizione comando. Questo consente agli utenti di individuare il comando *"Apri Communicator"* .
* Quando si guarda l'orologio, si dice *"Apri Communicator"* per aprire il pannello Communicator.

## <a name="chapter-2---acknowledgement"></a>Capitolo 2-riconoscimento

>[!VIDEO https://www.youtube.com/embed/87ViteoPpyU]

### <a name="objectives"></a>Obiettivi

* Registrare un messaggio usando l'input del microfono.
* Fornire un feedback all'utente che l'applicazione sta ascoltando la propria voce.

>[!NOTE]
>Per registrare un app dal microfono, è necessario dichiarare la funzionalità del **microfono** . Questa operazione viene eseguita per l'utente già nell'input 212, ma è opportuno tenerla presente per i propri progetti.
>
>1. Nell'editor di Unity passare a Impostazioni lettore passando a "Modifica > Impostazioni progetto > lettore"
>2. Fare clic sulla scheda "piattaforma UWP (Universal Windows Platform)"
>3. Nella sezione "impostazioni di pubblicazione > funzionalità" controllare la funzionalità del **microfono**

### <a name="instructions"></a>Istruzioni

* Nel pannello **gerarchia** di Unity verificare che sia selezionato l'oggetto **holoComm_screen_mesh** .
* Nel pannello **Inspector** trovare il componente **Watch Astronaut (script)** .
* Fare clic sul piccolo cubo blu che viene impostato come valore della proprietà **prefabbricata di Communicator** .
* Nel pannello del **progetto** , la prefabbricata di **Communicator** dovrebbe ora avere lo stato attivo.
* Fare clic sul prefabbricato di **Communicator** nel pannello del **progetto** per visualizzare i relativi componenti nel **controllo**.
* Si osservi il componente **Microphone Manager (script)** , che consente di registrare la voce dell'utente.
* Si noti che l'oggetto **Communicator** dispone di un componente del **gestore di input vocale (script)** per rispondere al comando **Send Message** .
* Esaminare il componente **Communicator (script)** e fare doppio clic sullo script per aprirlo in Visual Studio.

Communicator.cs è responsabile dell'impostazione degli Stati dei pulsanti appropriati sul dispositivo Communicator. Questo consentirà agli utenti di registrare un messaggio, riprodurlo e inviare il messaggio all'astronauta. Verrà avviato e arrestato anche un modulo Wave animato, per confermare all'utente che la voce è stata ascoltata.

* In **Communicator.cs**eliminare le righe seguenti (81 e 82) dal metodo **Start** . In questo modo verrà abilitato il pulsante "record" in Communicator.

```cs
// TODO: 2.a Delete the following two lines:
RecordButton.SetActive(false);
MessageUIRenderer.gameObject.SetActive(false);
```

### <a name="build-and-deploy"></a>Compilazione e distribuzione

* In Visual Studio ricompilare l'applicazione e distribuirla nel dispositivo.
* Guarda l'orologio dell'astronauta e pronuncia *"Open Communicator"* per visualizzare il Communicator.
* Premere il pulsante di **registrazione** (microfono) per avviare la registrazione di un messaggio verbale per l'astronauta.
* Iniziare a parlare e verificare che l'animazione Wave riproduca sul Communicator, che fornisce commenti e suggerimenti all'utente per ascoltare la voce.
* Premere il pulsante **Interrompi** (riquadro a sinistra) e verificare che l'animazione Wave venga arrestata.
* Premere il pulsante **Play** (triangolo a destra) per riprodurre il messaggio registrato e ascoltarlo sul dispositivo.
* Premere il pulsante **Arresta** (quadrato destro) per arrestare la riproduzione del messaggio registrato.
* Pronunciare *"Send Message"* per chiudere il Communicator e ricevere una risposta "message received" dall'astronauta.

## <a name="chapter-3---understanding-and-the-dictation-recognizer"></a>Capitolo 3-informazioni e riconoscimento della dettatura

>[!VIDEO https://www.youtube.com/embed/TIMddr-HqEU]

### <a name="objectives"></a>Obiettivi

* Usare il riconoscimento di dettatura per convertire il riconoscimento vocale dell'utente in testo.
* Mostra i risultati finali e ipotizzati del riconoscimento di dettatura in Communicator.

In questo capitolo verrà usato il riconoscimento di dettatura per creare un messaggio per l'astronauta. Quando si usa il riconoscimento di dettatura, tenere presente quanto segue:

* È necessario essere connessi al Wi-Fi affinché il sistema di riconoscimento della dettatura funzioni.
* I timeout si verificano dopo un determinato periodo di tempo. È necessario tenere presenti due timeout:
  * Se il riconoscimento viene avviato e non viene sentito alcun audio per i primi cinque secondi, il timeout verrà attivato.
  * Se il riconoscimento ha dato un risultato, ma in seguito viene ascoltato il silenzio per 20 secondi, il timeout verrà completato.
* È possibile eseguire un solo tipo di riconoscimento (parola chiave o dettatura) alla volta.

>[!NOTE]
>Per registrare un app dal microfono, è necessario dichiarare la funzionalità del **microfono** . Questa operazione viene eseguita per l'utente già nell'input 212, ma è opportuno tenerla presente per i propri progetti.
>
>1. Nell'editor di Unity passare a Impostazioni lettore passando a "Modifica > Impostazioni progetto > lettore"
>2. Fare clic sulla scheda "piattaforma UWP (Universal Windows Platform)"
>3. Nella sezione "impostazioni di pubblicazione > funzionalità" controllare la funzionalità del **microfono**

### <a name="instructions"></a>Istruzioni

**MicrophoneManager.cs** verrà modificato in modo da usare il riconoscimento della dettatura. Questo è ciò che verrà aggiunto:

1. Quando si preme il **pulsante record** , si **avvierà il DictationRecognizer**.
2. Mostra l' **ipotesi** di ciò che DictationRecognizer ha compreso.
3. Blocca i **risultati** della comprensione del DictationRecognizer.
4. Verificare la presenza di timeout dal DictationRecognizer.
5. Quando si preme il **pulsante Interrompi** oppure si verifica il timeout della sessione MIC, **arrestare il DictationRecognizer**.
6. Riavviare il **KeywordRecognizer**, che resterà in attesa del comando **Send Message** .

Cominciamo. Completare tutti gli esercizi di codifica per 3. a in **MicrophoneManager.cs**oppure copiare e incollare il codice finito riportato di seguito:

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using System.Collections;
using System.Text;
using UnityEngine;
using UnityEngine.UI;
using UnityEngine.Windows.Speech;

namespace Academy
{
    public class MicrophoneManager : MonoBehaviour
    {
        [Tooltip("A text area for the recognizer to display the recognized strings.")]
        [SerializeField]
        private Text dictationDisplay;

        private DictationRecognizer dictationRecognizer;

        // Use this string to cache the text currently displayed in the text box.
        private StringBuilder textSoFar;

        // Using an empty string specifies the default microphone.
        private static string deviceName = string.Empty;
        private int samplingRate;
        private const int messageLength = 10;

        // Use this to reset the UI once the Microphone is done recording after it was started.
        private bool hasRecordingStarted;

        void Awake()
        {
            /* TODO: DEVELOPER CODING EXERCISE 3.a */

            // 3.a: Create a new DictationRecognizer and assign it to dictationRecognizer variable.
            dictationRecognizer = new DictationRecognizer();

            // 3.a: Register for dictationRecognizer.DictationHypothesis and implement DictationHypothesis below
            // This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
            dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;

            // 3.a: Register for dictationRecognizer.DictationResult and implement DictationResult below
            // This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;

            // 3.a: Register for dictationRecognizer.DictationComplete and implement DictationComplete below
            // This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
            dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;

            // 3.a: Register for dictationRecognizer.DictationError and implement DictationError below
            // This event is fired when an error occurs.
            dictationRecognizer.DictationError += DictationRecognizer_DictationError;

            // Query the maximum frequency of the default microphone. Use 'unused' to ignore the minimum frequency.
            int unused;
            Microphone.GetDeviceCaps(deviceName, out unused, out samplingRate);

            // Use this string to cache the text currently displayed in the text box.
            textSoFar = new StringBuilder();

            // Use this to reset the UI once the Microphone is done recording after it was started.
            hasRecordingStarted = false;
        }

        void Update()
        {
            // 3.a: Add condition to check if dictationRecognizer.Status is Running
            if (hasRecordingStarted && !Microphone.IsRecording(deviceName) && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                // Reset the flag now that we're cleaning up the UI.
                hasRecordingStarted = false;

                // This acts like pressing the Stop button and sends the message to the Communicator.
                // If the microphone stops as a result of timing out, make sure to manually stop the dictation recognizer.
                // Look at the StopRecording function.
                SendMessage("RecordStop");
            }
        }

        /// <summary>
        /// Turns on the dictation recognizer and begins recording audio from the default microphone.
        /// </summary>
        /// <returns>The audio clip recorded from the microphone.</returns>
        public AudioClip StartRecording()
        {
            // 3.a Shutdown the PhraseRecognitionSystem. This controls the KeywordRecognizers
            PhraseRecognitionSystem.Shutdown();

            // 3.a: Start dictationRecognizer
            dictationRecognizer.Start();

            // 3.a Uncomment this line
            dictationDisplay.text = "Dictation is starting. It may take time to display your text the first time, but begin speaking now...";

            // Set the flag that we've started recording.
            hasRecordingStarted = true;

            // Start recording from the microphone for 10 seconds.
            return Microphone.Start(deviceName, false, messageLength, samplingRate);
        }

        /// <summary>
        /// Ends the recording session.
        /// </summary>
        public void StopRecording()
        {
            // 3.a: Check if dictationRecognizer.Status is Running and stop it if so
            if (dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                dictationRecognizer.Stop();
            }

            Microphone.End(deviceName);
        }

        /// <summary>
        /// This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
        /// </summary>
        /// <param name="text">The currently hypothesized recognition.</param>
        private void DictationRecognizer_DictationHypothesis(string text)
        {
            // 3.a: Set DictationDisplay text to be textSoFar and new hypothesized text
            // We don't want to append to textSoFar yet, because the hypothesis may have changed on the next event
            dictationDisplay.text = textSoFar.ToString() + " " + text + "...";
        }

        /// <summary>
        /// This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
        /// </summary>
        /// <param name="text">The text that was heard by the recognizer.</param>
        /// <param name="confidence">A representation of how confident (rejected, low, medium, high) the recognizer is of this recognition.</param>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // 3.a: Append textSoFar with latest text
            textSoFar.Append(text + ". ");

            // 3.a: Set DictationDisplay text to be textSoFar
            dictationDisplay.text = textSoFar.ToString();
        }

        /// <summary>
        /// This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
        /// Typically, this will simply return "Complete". In this case, we check to see if the recognizer timed out.
        /// </summary>
        /// <param name="cause">An enumerated reason for the session completing.</param>
        private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
        {
            // If Timeout occurs, the user has been silent for too long.
            // With dictation, the default timeout after a recognition is 20 seconds.
            // The default timeout with initial silence is 5 seconds.
            if (cause == DictationCompletionCause.TimeoutExceeded)
            {
                Microphone.End(deviceName);

                dictationDisplay.text = "Dictation has timed out. Please press the record button again.";
                SendMessage("ResetAfterTimeout");
            }
        }

        /// <summary>
        /// This event is fired when an error occurs.
        /// </summary>
        /// <param name="error">The string representation of the error reason.</param>
        /// <param name="hresult">The int representation of the hresult.</param>
        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            // 3.a: Set DictationDisplay text to be the error string
            dictationDisplay.text = error + "\nHRESULT: " + hresult;
        }

        /// <summary>
        /// The dictation recognizer may not turn off immediately, so this call blocks on
        /// the recognizer reporting that it has actually stopped.
        /// </summary>
        public IEnumerator WaitForDictationToStop()
        {
            while (dictationRecognizer != null && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                yield return null;
            }
        }
    }
}
```

### <a name="build-and-deploy"></a>Compilazione e distribuzione

* Ricompilare in Visual Studio e distribuirlo nel dispositivo.
* Chiudere la casella adatta con un movimento di tocco aereo.
* Guarda l'orologio dell'astronauta e pronuncia *"Open Communicator"* .
* Selezionare il pulsante di **registrazione** (microfono) per registrare il messaggio.
* Inizia a parlare. Il **riconoscimento della dettatura** interpreterà il riconoscimento vocale e visualizzerà il testo ipotizzato in Communicator.
* Provare a pronunciare *"Invia messaggio"* durante la registrazione di un messaggio. Si noti che la **parola chiave Recognizer** non risponde perché il **riconoscimento della dettatura** è ancora attivo.
* Interrompere la conversazione per alcuni secondi. Osservare come il riconoscimento di dettatura completa l'ipotesi e Mostra il risultato finale.
* Inizia a parlare e quindi Sospendi per 20 secondi. In questo modo il sistema di **riconoscimento della dettatura** verrà sottoposto a timeout.
* Si noti che la **parola chiave Recognizer** viene abilitata di nuovo dopo il timeout precedente. Communicator risponderà ora ai comandi vocali.
* Pronunciare *"Send Message"* per inviare il messaggio all'astronauta.

## <a name="chapter-4---grammar-recognizer"></a>Capitolo 4-riconoscimento grammatica

>[!VIDEO https://www.youtube.com/embed/J2dYJNSvv18]

### <a name="objectives"></a>Obiettivi

* Usare il sistema di riconoscimento della grammatica per riconoscere la voce dell'utente in base a un file di SRGS, o specifica della grammatica del riconoscimento vocale.

>[!NOTE]
>Per registrare un app dal microfono, è necessario dichiarare la funzionalità del **microfono** . Questa operazione viene eseguita per l'utente già nell'input 212, ma è opportuno tenerla presente per i propri progetti.
>
>1. Nell'editor di Unity passare a Impostazioni lettore passando a "Modifica > Impostazioni progetto > lettore"
>2. Fare clic sulla scheda "piattaforma UWP (Universal Windows Platform)"
>3. Nella sezione "impostazioni di pubblicazione > funzionalità" controllare la funzionalità del **microfono**

### <a name="instructions"></a>Istruzioni

1. Nel pannello **gerarchia** cercare **Jetpack_Center** e selezionarlo.
2. Cercare lo script dell' **azione Tagalong** nel pannello **Inspector** .
3. Fare clic sul piccolo cerchio a destra dell' **oggetto da contrassegnare lungo** il campo.
4. Nella finestra visualizzata cercare **SRGSToolbox** e selezionarlo dall'elenco.
5. Esaminare il file **SRGSColor. XML** nella cartella **StreamingAssets**
    1. La specifica di progettazione SRGS è disponibile nel sito Web W3C [qui](https://www.w3.org/TR/speech-grammar/).

Nel file SRGS sono disponibili tre tipi di regole:

* Una regola che consente di indicare un colore da un elenco di dodici colori.
* Tre regole che restano in ascolto di una combinazione della regola colore e di una delle tre forme.
* Regola radice, colorChooser, che rimane in attesa di una combinazione delle tre regole "colore + forma". Le forme possono essere definite in qualsiasi ordine e in qualsiasi quantità da una a tutte e tre. Questa è l'unica regola che viene ascoltata, perché viene specificata come regola radice nella parte superiore del file nel tag &lt;grammatica&gt; iniziale.

### <a name="build-and-deploy"></a>Compilazione e distribuzione

* Ricompilare l'applicazione in Unity, quindi compilare e distribuire da Visual Studio per sperimentare l'app in HoloLens.
* Chiudere la casella adatta con un movimento di tocco aereo.
* Osservare il jetpack dell'astronauta ed eseguire un gesto d'aria.
* Inizia a parlare. Il riconoscimento della **grammatica** interpreterà il riconoscimento vocale e modificherà i colori delle forme in base al riconoscimento. Un comando di esempio è "Blue Circle, Yellow Square".
* Eseguire un altro gesto di tocco aereo per chiudere la casella degli strumenti.

## <a name="the-end"></a>La fine

Complimenti. A questo punto è stato completato il **sig. Input 212: Voice**.

* Si conosce il DOS e non i comandi vocali.
* Sono state illustrate le modalità di utilizzo delle descrizioni comando per consentire agli utenti di riconoscere i comandi vocali.
* Sono stati rilevati diversi tipi di feedback usati per confermare che la voce dell'utente è stata ascoltata.
* Si sa come passare tra il riconoscimento delle parole chiave e il riconoscimento di dettatura e come queste due funzionalità comprendono e interpretano la voce.
* Si è appreso come usare un file SRGS e il riconoscimento della grammatica per il riconoscimento vocale nell'applicazione.

---
title: Input MR 212 - voce
description: Seguire questa procedura dettagliata di scrittura del codice grazie a Unity, Visual Studio e HoloLens per informazioni dettagliate su concetti vocali.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit unity, academy, esercitazione, vocali
ms.openlocfilehash: 7e792bf40c47d4e1d57898fbe75ad050a030b7e3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59598923"
---
>[!NOTE]
>Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.  Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.  Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.  Essi verranno mantenute per continuare a utilizzare i dispositivi supportati. Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.  Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.

<br>

# <a name="mr-input-212-voice"></a>Input di MR 212: Comandi vocali

[Input vocale](voice-input.md) offre un altro modo per interagire con i nostri vntana. I comandi vocali funzionano in modo molto semplice e naturale. Progettare i comandi vocali in modo che siano:

* Naturale
* Facile da ricordare
* Contesto adeguato
* Sufficientemente distinto da altre opzioni nello stesso contesto

>[!VIDEO https://www.youtube.com/embed/BYpYsVFYjdw]

Nelle [MR nozioni di base 101](holograms-101.md), abbiamo usato la KeywordRecognizer per creare due comandi vocali semplice. In 212 Input MR, verrà illustrato in modo approfonditi e Scopri come:

* Progettare i comandi vocali che sono ottimizzati per il motore di sintesi vocale HoloLens.
* Impostare l'utente con riconoscimento della voce che quali comandi sono disponibili.
* Confermare che sono stati segnalati comando vocale dell'utente.
* Comprendere che cos'è l'utente che indica che, utilizzando un riconoscimento dettatura.
* Consente di restare in attesa per i comandi basati su un file SRGS o specifica della grammatica di riconoscimento vocale, una grammatica di riconoscimento.

In questo corso, questo aspetto verrà trattato Esplora modelli, che è stato creato nel [MR Input 210](holograms-210.md) e [MR Input 211](holograms-211.md).

>[!IMPORTANT]
>I video incorporati in ognuna delle sezioni seguenti sono stati registrati usando una versione precedente di Unity e il Toolkit di realtà mista. Anche se le istruzioni dettagliate sono accurate e aggiornate, è possibile visualizzare gli script e gli oggetti visivi nei video corrispondenti che non sono aggiornati. I video rimangono inclusi per ci si ricorderà più e perché i concetti illustrati sono applicano.


## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></th>
</tr><tr>
<td>Input di MR 212: Comandi vocali</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Prima di iniziare

### <a name="prerequisites"></a>Prerequisiti

* Un PC Windows 10 configurate con i valori corretti [sono installati gli strumenti](install-the-tools.md).
* Alcuni basic C# capacità di programmazione.
* È necessario avere completato [MR nozioni di base 101](holograms-101.md).
* È necessario avere completato [MR Input 210](holograms-210.md).
* È necessario avere completato [MR Input 211](holograms-211.md).
* Un dispositivo HoloLens [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>File di progetto

* Scaricare il [file](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) necessarie per il progetto. Richiede Unity 2017.2 o versione successiva.
* Annullare la-archive i file sul desktop o altri facile da raggiungere percorso.

>[!NOTE]
>Se si desidera esaminare il codice sorgente prima di scaricare, ha [disponibile in GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).

### <a name="errata-and-notes"></a>Errori e note

* "Abilita Just My Code" deve essere disabilitato (*unchecked*) in Visual Studio in Strumenti -> Opzioni -> debug per poter raggiungere punti di interruzione nel codice.

## <a name="unity-setup"></a>Programma di installazione di Unity

### <a name="instructions"></a>Istruzioni

1. Avviare Unity.
2. Selezionare **aperto**.
3. Passare al **HolographicAcademy-Vntana 212 Voice** cartella è archiviato in precedenza di annullamento.
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

## <a name="chapter-1---awareness"></a>Capitolo 1 - riconoscimento

>[!VIDEO https://www.youtube.com/embed/fDwijJWuEc0]

### <a name="objectives"></a>Obiettivi

* Scopri le **consigliate e sconsigliate** di progettazione dei comandi vocali.
* Uso **KeywordRecognizer** aggiungere comandi vocali sguardo basato.
* Rendere gli utenti consapevoli di comandi vocali tramite cursore **commenti e suggerimenti**.

### <a name="voice-command-design"></a>Progettazione dei comandi vocali

In questo capitolo, si apprenderà sulla progettazione di comandi vocali. Durante la creazione di comandi vocali:

#### <a name="do"></a>DO

* Creare comandi concisi. Non si vuole usare *"Guarda il video attualmente selezionato"*, perché tale comando non è più conciso e verrebbe rimosse con facilità dall'utente. In alternativa, è consigliabile utilizzare: *"Riproduci Video"*, in quanto è concisa e ha più sillabe.
* Usare un vocabolario semplice. Sempre provare a usare parole e frasi semplici per l'utente di individuare e tenere presente che comuni. Ad esempio, se l'applicazione dispone di un oggetto si noti che potrebbe essere visualizzato o nascosto dalla visualizzazione, non utilizzare il comando *"Mostra manifesto"*, perché "manifesto" è un termine usato raramente. In alternativa, utilizzare il comando: *"Show nota"*, per visualizzare la nota all'interno dell'applicazione.
* Mantenere la coerenza. I comandi vocali devono essere mantenuti coerenti tra l'applicazione. Si supponga di avere due scene nell'applicazione e che entrambe le scene contengono un pulsante della chiusura dell'applicazione. Se il comando utilizzato prima scena *"Esci"* per attivare il pulsante, ma il secondo scena utilizzato il comando *"Chiudi App"*, quindi l'utente dovrà verificare alcuni problemi. Se la stessa funzionalità vengono mantenute per le scene più, quindi lo stesso comando vocali da utilizzare per attivarlo.

#### <a name="dont"></a>DON'T

* Usare i comandi sillaba singolo. Ad esempio, se si crea un comando vocale per riprodurre un video, è consigliabile evitare di usare il comando semplice *"Riprodurre"*, perché è solo una sillaba singola e possono andare perse con facilità dal sistema. In alternativa, è consigliabile utilizzare: *"Riproduci Video"*, in quanto è concisa e ha più sillabe.
* Usare i comandi del sistema. Il *"Selezionare"* comando è riservato dal sistema per attivare un evento di tocco per l'oggetto attualmente con lo stato attivo. Non usare nuovamente il *"Selezionare"* comando in una parola chiave o una frase, mentre potrebbe non funzionare come previsto. Ad esempio, se la voce di comando per la selezione di un cubo all'interno dell'applicazione è stata *"Seleziona cubo"*, ma l'utente è stato esaminando una sfera quando essi pronunciato del comando, quindi verrà selezionata invece la sfera. Allo stesso modo della barra dei comandi di app sono servizio voce abilitato. Non usare i comandi seguenti di riconoscimento vocale nella propria visualizzazione CoreWindow:
    1. tornare indietro
    2. Strumento di scorrimento
    3. Strumento Zoom
    4. Strumento di trascinamento
    5. Regolare
    6. Rimuovi
* Usare suono simile. Provare a evitare di usare i comandi vocali che rhyme. Se si dispone di un'applicazione shopping supportata *"Mostra Store"* e *"Mostra più"* come comandi vocali, sarebbe opportuno disabilitare uno dei comandi, mentre l'altro è in uso. Ad esempio, è possibile usare la *"Mostra Store"* pulsante per aprire lo store e quindi disabilitare tale comando quando l'archivio è stato visualizzato in modo che il *"Mostra più"* comando può essere usato per l'esplorazione.

### <a name="instructions"></a>Istruzioni

* Nella finestra di Unity **gerarchia** del pannello, usare lo strumento di ricerca per trovare il **holoComm_screen_mesh** oggetto.
* Fare doppio clic sulla **holoComm_screen_mesh** oggetto per la visualizzazione nel **scena**. Si tratta di espressioni di controllo del astronautici, che risponderà per i comandi vocali.
* Nel **Inspector** panel, individuare il **origine di Input vocale (Script)** componente.
* Espandere la **parole chiave** sezione per visualizzare i comandi vocali supportate: **Aprire Communicator**.
* Fare clic sull'icona dell'ingranaggio a destra, quindi selezionare **modifica Script**.
* Esplorare **SpeechInputSource.cs** per comprendere come viene utilizzato il **KeywordRecognizer** aggiungere comandi vocali.

### <a name="build-and-deploy"></a>Compilare e distribuire

* In Unity, usare **File > Build Settings** per ricompili l'applicazione.
* Aprire il **App** cartella.
* Aprire il **soluzione ModelExplorer Visual Studio**.

(Se è stato creato o distribuito questo progetto in Visual Studio durante la configurazione, quindi è possibile aprire quell'istanza di Visual Studio e fare clic su 'Ricarica tutto' quando viene richiesto).

* In Visual Studio, fare clic su **Debug -> Avvia senza eseguire debug** o premere **Ctrl + F5**.
* Dopo la distribuzione dell'applicazione per il HoloLens, chiudere la finestra appropriato usando il [puntato](gestures.md#air-tap) movimento.
* Fissare espressioni di controllo del astronautici.
* Quando l'espressione di controllo ha lo stato attivo, verificare che il cursore assuma un microfono. Ciò fornisce un feedback che l'applicazione è in ascolto per i comandi vocali.
* Verificare che viene visualizzato un suggerimento sulle espressioni di controllo. Ciò consente agli utenti di individuare il *"Communicator Open"* comando.
* Mentre gazing all'orologio, pronunciare *"Communicator aprire"* per aprire il pannello di communicator.

## <a name="chapter-2---acknowledgement"></a>Capitolo 2 - Acknowledgement

>[!VIDEO https://www.youtube.com/embed/87ViteoPpyU]

### <a name="objectives"></a>Obiettivi

* Registrare un messaggio utilizzando l'input del microfono.
* Fornire commenti e suggerimenti all'utente che l'applicazione è in ascolto di comandi vocali.

>[!NOTE]
>Il **microfono** funzionalità devono essere dichiarate per un'app per la registrazione dal microfono. Questa operazione viene eseguita per è già in MR Input 212, ma tenere a mente per i propri progetti.
>
>1. Nell'Editor di Unity, passare alle impostazioni del giocatore, passare a "Modifica > progetto Impostazioni > Player"
>2. Fare clic sulla scheda "Universal Windows Platform"
>3. Nella sezione "Impostazioni > le funzionalità di pubblicazione", controllare la **microfono** funzionalità

### <a name="instructions"></a>Istruzioni

* Nella finestra di Unity **gerarchia** panel, verificare che il **holoComm_screen_mesh** oggetto selezionato.
* Nel **Inspector** panel, trovare il **astronautici Watch (Script)** componente.
* Fare clic sul cubo blu, di piccole dimensioni che viene impostato come valore dei **Communicator Prefab** proprietà.
* Nel **Project** pannello, il **Communicator** prefab avranno ora lo stato attivo.
* Fare clic sui **Communicator** prefab nel **Project** pannello per visualizzare i relativi componenti nel **Inspector**.
* Esaminare i **microfono Manager (Script)** componente, ciò permetterà di registrare la voce dell'utente.
* Si noti che il **Communicator** oggetto dispone di un **gestore di Input vocale (Script)** componente per la risposta per il **Invia messaggio** comando.
* Esaminare i **Communicator (Script)** componente e fare doppio clic su script per aprirlo in Visual Studio.

Communicator.cs è responsabile dell'impostazione gli stati del pulsante appropriato sulla periferica communicator. Ciò consentirà agli utenti di registrare un messaggio, riprodurlo e inviare il messaggio per l'astronautici. Inoltre verrà avviare e arrestare un formato wave animato, per confermare all'utente che è stata valere la loro opinione.

* Nelle **Communicator.cs**, eliminare le righe seguenti (81 e 82) dalle **avviare** (metodo). Abilita il pulsante 'Record' di communicator.

```cs
// TODO: 2.a Delete the following two lines:
RecordButton.SetActive(false);
MessageUIRenderer.gameObject.SetActive(false);
```

### <a name="build-and-deploy"></a>Compilare e distribuire

* In Visual Studio, ricompilare l'applicazione e la distribuzione nel dispositivo.
* Fissare espressioni di controllo del astronautici e scelgo *"Communicator Open"* per mostrare il communicator.
* Premere il **Record** pulsante (microfono) per avviare la registrazione di un messaggio verbale per l'astronautici.
* Inizia a parlare e verificare che l'animazione di wave viene riprodotta in communicator, il che fornisce feedback all'utente che sentire la propria voce.
* Premere il **arrestare** pulsante (quadrato a sinistra) e verificare che l'animazione di wave si arresta.
* Premere il **riprodurre** pulsante (triangolo) per riprodurre il messaggio registrato e invita i clienti nel dispositivo.
* Premere il **arrestare** pulsante (quadrata a destra) per arrestare la riproduzione del messaggio registrato.
* Pronunciare *"Invia messaggio"* per chiudere il communicator e ricevere una risposta di 'Messaggio ricevuto' l'astronautici.

## <a name="chapter-3---understanding-and-the-dictation-recognizer"></a>Capitolo 3 - comprensione e il riconoscimento dettatura

>[!VIDEO https://www.youtube.com/embed/TIMddr-HqEU]

### <a name="objectives"></a>Obiettivi

* Usare il riconoscimento dettatura per convertire il riconoscimento vocale dell'utente in testo.
* Visualizzare i risultati ipotizzati e finali del motore di riconoscimento dettatura di communicator.

In questo capitolo, si userà il riconoscimento dettatura per creare un messaggio per l'astronautici. Quando si usa il riconoscimento dettatura, tenere presente che:

* È necessario essere connessi al Wi-Fi per il riconoscimento dettatura a funzionare.
* I timeout si verificano dopo un periodo di tempo. Esistono due timeout da tenere presenti:
  * Se il riconoscimento viene avviato e non ascolta l'audio per i primi cinque secondi, si verifica un timeout.
  * Se il riconoscimento ha fornito un risultato, ma quindi ascolta silenzio per venti secondi, si verifica un timeout.
* Un solo tipo di riconoscimento (parola chiave o la dettatura) possa eseguire contemporaneamente.

>[!NOTE]
>Il **microfono** funzionalità devono essere dichiarate per un'app per la registrazione dal microfono. Questa operazione viene eseguita per è già in MR Input 212, ma tenere a mente per i propri progetti.
>
>1. Nell'Editor di Unity, passare alle impostazioni del giocatore, passare a "Modifica > progetto Impostazioni > Player"
>2. Fare clic sulla scheda "Universal Windows Platform"
>3. Nella sezione "Impostazioni > le funzionalità di pubblicazione", controllare la **microfono** funzionalità

### <a name="instructions"></a>Istruzioni

Dobbiamo modificare **MicrophoneManager.cs** usare il riconoscimento dettatura. Questo è ciò che verrà aggiunto:

1. Quando la **pulsante Record** è premuto, ti invieremo **avvia il DictationRecognizer**.
2. Mostra le **ipotesi** di ciò che il DictationRecognizer compreso.
3. Bloccare le **risultati** di ciò che il DictationRecognizer compreso.
4. Controllo per i timeout dal DictationRecognizer.
5. Quando la **pulsante di arresto** viene premuto, o timeout della sessione mic, **arrestare il DictationRecognizer**.
6. Riavviare il **KeywordRecognizer**, che sarà in ascolto per il **Send Message** comando.

Cominciamo. Completare Tutti esercizi sulla codifica per 3.a nelle **MicrophoneManager.cs**, oppure copiare e incollare il codice disponibile di seguito:

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

### <a name="build-and-deploy"></a>Compilare e distribuire

* Ricompilazione in Visual Studio e distribuire il dispositivo.
* Chiudere la finestra appropriata con un movimento indice puntato.
* Fissare espressioni di controllo del astronautici e scelgo *"Communicator Open"*.
* Selezionare il **Record** pulsante (microfono) per registrare il messaggio.
* Iniziare a parlare. Il **riconoscimento dettatura** verrà interpretare i comandi vocali e Mostra il testo ipotizzato di Communicator.
* Provare a ottimizzazioni *"Invia messaggio"* durante la registrazione di un messaggio. Si noti che il **parola chiave per il riconoscimento** non risponde perché la **riconoscimento dettatura** è ancora attiva.
* Interrompi lettura per alcuni secondi. Guarda come il riconoscimento dettatura completa relative ipotesi e viene illustrato il risultato finale.
* Iniziare a parlare e quindi viene sospeso per 20 secondi. Ciò causerà il **riconoscimento dettatura** per timeout.
* Si noti che il **parola chiave per il riconoscimento** viene abilitata di nuovo dopo il timeout precedente. Di communicator risponderà a questo punto i comandi vocali.
* Pronunciare *"Invia messaggio"* per inviare il messaggio per l'astronautici.

## <a name="chapter-4---grammar-recognizer"></a>Capitolo 4 - riconoscimento di grammatica

>[!VIDEO https://www.youtube.com/embed/J2dYJNSvv18]

### <a name="objectives"></a>Obiettivi

* Usare il riconoscimento di grammatica di riconoscimento vocale dell'utente in base a un file SRGS o specifica della grammatica di riconoscimento vocale.

>[!NOTE]
>Il **microfono** funzionalità devono essere dichiarate per un'app per la registrazione dal microfono. Questa operazione viene eseguita per è già in MR Input 212, ma tenere a mente per i propri progetti.
>
>1. Nell'Editor di Unity, passare alle impostazioni del giocatore, passare a "Modifica > progetto Impostazioni > Player"
>2. Fare clic sulla scheda "Universal Windows Platform"
>3. Nella sezione "Impostazioni > le funzionalità di pubblicazione", controllare la **microfono** funzionalità

### <a name="instructions"></a>Istruzioni

1. Nel **gerarchia** del pannello, cercare **Jetpack_Center** e selezionarlo.
2. Cercare il **azione abbinato** creare uno script nel **Inspector** pannello.
3. Fare clic sul cerchio piccolo a destra del **oggetto di Tag lungo** campo.
4. Nella finestra visualizzata, cercare **SRGSToolbox** e selezionarlo dall'elenco.
5. Esaminiamo il **SRGSColor.xml** del file nei **StreamingAssets** cartella.
* La specifica di progettazione SRGS è reperibile sul sito Web W3C [qui](https://www.w3.org/TR/speech-grammar/).
* Nel file SRGS, sono disponibili tre tipi di regole:
  * Una regola che consente ad esempio un colore da un elenco di dodici colori.
  * Tre regole in ascolto di una combinazione di regola del colore e uno dei tre forme.
  * La regola radice, colorChooser, che è in ascolto per qualsiasi combinazione delle tre regole "colore + forma". Le forme possono avvenire in qualsiasi ordine e in qualsiasi quantità da un unico per tutte e tre. Questo è l'unica regola che è in ascolto, come specificato come regola radice nella parte superiore del file in iniziale &lt;grammatica&gt; tag.

### <a name="build-and-deploy"></a>Compilare e distribuire

* Ricompilare l'applicazione in Unity, quindi compilare e distribuire da Visual Studio per provare l'app in HoloLens.
* Chiudere la finestra appropriata con un movimento indice puntato.
* Fissare jetpack del astronautici ed esegue un movimento indice puntato.
* Iniziare a parlare. Il **grammatica di riconoscimento** verrà interpretare i comandi vocali e modificare i colori delle forme di base del riconoscimento. Un comando di esempio è "quadrato cerchio blu, gialli".
* Eseguire un altro indice puntato movimento per ignorare la casella degli strumenti.

## <a name="the-end"></a>La fine

La procedura è stata completata. Sono stati completati **SIG Input 212: Voce**.

* Sai cosa fare e dei comandi vocali.
* Si è visto come le descrizioni comandi sono stati utilizzati per rendere gli utenti consapevoli di comandi vocali.
* Si è visto diversi tipi di commenti e suggerimenti usati per confermare che la voce dell'utente è stata sentito parlare.
* Si è certi di come passare tra il riconoscimento (parola chiave) e il riconoscimento dettatura e come queste due funzionalità comprendere e interpretare la voce dell'utente.
* Si è appreso come usare un file SRGS e il riconoscimento di grammatica di riconoscimento vocale nell'applicazione.

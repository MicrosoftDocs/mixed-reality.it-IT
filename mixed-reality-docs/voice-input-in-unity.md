---
title: Input vocale in Unity
description: Unity espone tre modi per aggiungere l'input vocale all'applicazione di realtà mista di Windows.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Input vocale, KeywordRecognizer, GrammarRecognizer, microfono, dettatura, vocali
ms.openlocfilehash: ef8114a1c877fe9b858122e0c64628d4b71a69cd
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604819"
---
# <a name="voice-input-in-unity"></a>Input vocale in Unity

Unity espone tre modi per aggiungere [input vocale](voice-input.md) all'applicazione di Unity.

Con KeywordRecognizer (uno dei due tipi di PhraseRecognizers), l'app è possibile assegnare una matrice di comandi di stringa per l'ascolto delle. Con la GrammarRecognizer (l'altro tipo di PhraseRecognizer), l'app può essere fornito un file SRGS che definisce una grammatica specifica per l'ascolto. Con DictationRecognizer, l'app può restare in attesa per tutte le parole e fornire all'utente una nota o altro visualizzatore di loro vocale.

>[!NOTE]
>Solo per la dettatura o riconoscimento dettatura può essere gestito in una sola volta. Ciò significa che se un GrammarRecognizer o KeywordRecognizer è attivo, non può essere attivo un DictationRecognizer e viceversa.

## <a name="enabling-the-capability-for-voice"></a>Abilitazione della funzionalità per le funzionalità vocali

Il **microfono** funzionalità devono essere dichiarate per un'app sfruttare l'input vocale.
1. Nell'Editor di Unity, passare alle impostazioni del giocatore, passare a "Modifica > progetto Impostazioni > Player"
2. Fare clic sulla scheda "Windows Store"
3. Nella sezione "Impostazioni > le funzionalità di pubblicazione", controllare la **microfono** funzionalità

## <a name="phrase-recognition"></a>Riconoscimento dettatura

Per abilitare l'app per l'ascolto delle specifiche frasi pronunciate dall'utente, quindi eseguire un'azione, è necessario:
1. Specificare quali frasi per restare in attesa per l'uso di un KeywordRecognizer o GrammarRecognizer
2. Gestire l'evento OnPhraseRecognized ed esegue azioni corrispondenti alla frase riconosciuta

### <a name="keywordrecognizer"></a>KeywordRecognizer

**Namespace:** *UnityEngine.Windows.Speech*<br>
**Tipi:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*

Sarà necessario alcune istruzioni using a risparmiare alcune sequenze di tasti:

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

Quindi aggiungiamo alcuni campi alla classe per archiviare il riconoscimento e (parola chiave) -> dizionario dell'azione:

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

Aggiungere ora una parola chiave al dizionario (ad esempio, all'interno di un metodo Start ()). Stiamo aggiungendo la parola chiave "attiva" in questo esempio:

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

Creare il riconoscimento (parola chiave) e gli si indica ciò che si desidera riconoscere:

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

Ora registrare per l'evento OnPhraseRecognized

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

Un gestore di esempio è:

```
private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    System.Action keywordAction;
    // if the keyword recognized is in our dictionary, call that Action.
    if (keywords.TryGetValue(args.text, out keywordAction))
    {
        keywordAction.Invoke();
    }
}
```

Al termine, avviare il riconoscimento.

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a>GrammarRecognizer

**Namespace:** *UnityEngine.Windows.Speech*<br>
**Tipi**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*

Il GrammarRecognizer viene usato se si specifica la grammatica di riconoscimento con SRGS. Ciò può essere utile se l'app ha più di pochi parole chiave, se si desidera identificare le frasi più complesse, o se si desidera attivare con facilità e disattivare i set di comandi. Vedere: [Creare grammatiche tramite SRGS XML](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) per informazioni sul formato di file.

Una volta che si dispone di grammatica SRGS ed è nel progetto in un [StreamingAssets cartella](http://docs.unity3d.com/Manual/StreamingAssets.html):

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

Creare un GrammarRecognizer e chiamarla dal percorso del file SRGS:

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

Ora registrare per l'evento OnPhraseRecognized

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

Si riceverà un callback che contiene le informazioni specificate nella grammatica SRGS che è possibile gestire in modo appropriato. La maggior parte delle informazioni importanti verrà fornita nella matrice semanticMeanings.

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

Al termine, avviare il riconoscimento.

```
grammarRecognizer.Start();
```

## <a name="dictation"></a>Dettatura

**Namespace:** *UnityEngine.Windows.Speech*<br>
**Tipi**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*

Usare il DictationRecognizer per convertire il riconoscimento vocale dell'utente in testo. Espone le DictationRecognizer [dettatura](voice-input.md#dictation) funzionalità e supporta la registrazione e l'ascolto delle ipotesi e frase completati gli eventi, pertanto è possibile assegnare i commenti e suggerimenti per l'utente sia mentre si parla e in un secondo momento. Metodi Start () e Stop (), rispettivamente, abilitare e disabilitare il riconoscimento dettatura continua. Una volta completata la sospensione del riconoscimento, che deve essere eliminato usando il metodo Dispose () per rilasciare le risorse che usa. Rilascerà tali risorse automaticamente durante l'operazione di garbage collection a un costo aggiuntivo delle prestazioni se essi non vengono rilasciate prima di tale.

Sono disponibili solo pochi passaggi necessari per iniziare a usare la dettatura:
1. Creare un nuovo DictationRecognizer
2. Gestire gli eventi di dettatura
3. Avviare il DictationRecognizer

### <a name="enabling-the-capability-for-dictation"></a>Abilitazione della funzionalità per la dettatura

La funzionalità "Internet Client", oltre alle funzionalità "Microfono" indicato in precedenza, deve essere dichiarata per un'app sfruttare la dettatura.
1. Nell'Editor di Unity, passare alle impostazioni del giocatore, passare alla pagina "Modifica > progetto Impostazioni > Player"
2. Fare clic sulla scheda "Windows Store"
3. Nella sezione "Impostazioni > le funzionalità di pubblicazione", controllare la **InternetClient** funzionalità

### <a name="dictationrecognizer"></a>DictationRecognizer

Creare un DictationRecognizer come segue:

```
dictationRecognizer = new DictationRecognizer();
```

Esistono quattro eventi dettatura che possono essere sottoscritto e gestiti per implementare il comportamento di dettatura.
1. DictationResult
2. DictationComplete
3. DictationHypothesis
4. DictationError

**DictationResult**

Questo evento viene generato dopo che l'utente mette in pausa, in genere alla fine di una frase. La versione completa riconosciuto stringa viene restituita qui.

In primo luogo, sottoscrivere l'evento DictationResult:

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

Quindi gestire il callback DictationResult:

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

**DictationHypothesis**

Questo evento viene generato continuamente mentre l'utente sta parlando. Come è in ascolto il riconoscimento, fornisce il testo di ciò che è sentito parlare finora.

In primo luogo, sottoscrivere l'evento DictationHypothesis:

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

Quindi gestire il callback DictationHypothesis:

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

**DictationComplete**

Questo evento viene generato quando si arresta il riconoscimento, sia da Stop () viene chiamato, un timeout che si verificano, o un altro errore.

In primo luogo, sottoscrivere l'evento DictationComplete:

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

Quindi gestire il callback DictationComplete:

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

**DictationError**

Questo evento viene generato quando si verifica un errore.

In primo luogo, sottoscrivere l'evento DictationError:

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

Quindi gestire il callback DictationError:

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

Dopo aver sottoscritto e gestiti gli eventi di dettatura che si è interessati, avviare il riconoscimento dettatura per iniziare a ricevere gli eventi.

```
dictationRecognizer.Start();
```

Se non è più si desidera mantenere il DictationRecognizer intorno, è necessario annullare la sottoscrizione a eventi ed eliminare il DictationRecognizer.

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

**Suggerimenti**
* Metodi Start () e Stop (), rispettivamente, abilitare e disabilitare il riconoscimento dettatura continua.
* Una volta completata la sospensione del riconoscimento, deve essere eliminato usando il metodo Dispose () per rilasciare le risorse che usa. Rilascerà tali risorse automaticamente durante l'operazione di garbage collection a un costo aggiuntivo delle prestazioni se essi non vengono rilasciate prima di tale.
* I timeout si verificano dopo un periodo di tempo. È possibile cercare questi timeout nell'evento DictationComplete. Esistono due timeout da tenere presenti:
   1. Se il riconoscimento viene avviato e non ascolta l'audio per i primi cinque secondi, si verifica un timeout.
   2. Se il riconoscimento ha fornito un risultato, ma quindi ascolta silenzio per venti secondi, si verifica un timeout.

## <a name="using-both-phrase-recognition-and-dictation"></a>Tramite riconoscimento dettatura e la dettatura

Se si desidera utilizzare sia riconoscimento dettatura e la dettatura nell'app, è necessario arrestare completamente uno prima di iniziare l'altro. Se si dispone di più in esecuzione KeywordRecognizers, è possibile arrestarli tutto in una sola volta con:

```
PhraseRecognitionSystem.Shutdown();
```

Per ripristinare tutti i riconoscitori allo stato precedente, dopo il DictationRecognizer è stato arrestato, è possibile chiamare:

```
PhraseRecognitionSystem.Restart();
```

È inoltre sufficiente è stato possibile avviare un KeywordRecognizer, che verrà riavviato anche il PhraseRecognitionSystem.

## <a name="using-the-microphone-helper"></a>Utilizzo dell'helper di microfono

Il Toolkit di realtà mista su GitHub contiene una classe helper di microfono per indicativi di sviluppatori se è presente un microfono utilizzabile nel sistema. Uno viene utilizzato in cui uno desidera controllare se è presente microfono sul sistema prima di visualizzare qualsiasi parlato hint per l'interazione dell'applicazione.

Lo script helper microfono è reperibile nella [cartella di Input/script o utilità](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs). Il repository GitHub contiene anche un [piccolo campione](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) che illustra come usare l'helper.

## <a name="voice-input-in-mixed-reality-toolkit"></a>Input vocale in Toolkit di realtà mista
È possibile trovare gli esempi dell'input vocale in questa scena.

- [HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity)

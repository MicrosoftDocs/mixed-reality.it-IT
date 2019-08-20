---
title: Input vocale in Unity
description: Unity espone tre modi per aggiungere input vocale all'applicazione di realtà mista Windows.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Input vocale, KeywordRecognizer, GrammarRecognizer, microfono, dettatura, voce
ms.openlocfilehash: ef8114a1c877fe9b858122e0c64628d4b71a69cd
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548689"
---
# <a name="voice-input-in-unity"></a>Input vocale in Unity

Unity espone tre modi per aggiungere [input vocale](voice-input.md) all'applicazione Unity.

Con KeywordRecognizer (uno dei due tipi di PhraseRecognizers), all'app può essere assegnata una matrice di comandi stringa da ascoltare. Con GrammarRecognizer (l'altro tipo di PhraseRecognizer), all'app può essere assegnato un file SRGS che definisce una grammatica specifica per l'ascolto. Con la DictationRecognizer, l'app può restare in ascolto di qualsiasi parola e fornire all'utente una nota o un'altra visualizzazione del riconoscimento vocale.

>[!NOTE]
>Solo i riconoscimenti di dettatura o di frase possono essere gestiti in una sola volta. Ciò significa che se GrammarRecognizer o KeywordRecognizer è attivo, un DictationRecognizer non può essere attivo e viceversa.

## <a name="enabling-the-capability-for-voice"></a>Abilitazione della funzionalità per la voce

Per poter sfruttare l'input vocale, è necessario dichiarare la funzionalità del **microfono** per un'app.
1. Nell'editor di Unity passare a Impostazioni lettore passando a "Modifica > Impostazioni progetto > lettore"
2. Fare clic sulla scheda "Windows Store"
3. Nella sezione "impostazioni di pubblicazione > funzionalità" controllare la funzionalità del **microfono**

## <a name="phrase-recognition"></a>Riconoscimento di frasi

Per consentire all'app di restare in ascolto di frasi specifiche pronunciate dall'utente, è necessario eseguire le operazioni seguenti:
1. Specificare le frasi da ascoltare tramite KeywordRecognizer o GrammarRecognizer
2. Gestire l'evento OnPhraseRecognized ed eseguire un'azione corrispondente alla frase riconosciuta

### <a name="keywordrecognizer"></a>KeywordRecognizer

**Namespace** *UnityEngine. Windows. Speech*<br>
**Tipi** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*

Sono necessarie alcune istruzioni using per salvare alcune sequenze di tasti:

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

Aggiungere quindi alcuni campi alla classe per archiviare il riconoscimento e la parola chiave > dizionario azione:

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

Aggiungere ora una parola chiave al dizionario, ad esempio all'interno di un metodo Start (). In questo esempio viene aggiunta la parola chiave "Activate":

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

Creare la parola chiave Recognizer e indicare cosa si vuole riconoscere:

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

Registrati ora per l'evento OnPhraseRecognized

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

Infine, iniziare a riconoscere.

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a>GrammarRecognizer

**Namespace** *UnityEngine. Windows. Speech*<br>
**Tipi**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*

GrammarRecognizer viene usato se si specifica la grammatica di riconoscimento usando SRGS. Questo può essere utile se l'app ha più di poche parole chiave, se si desidera riconoscere frasi più complesse o se si desidera attivare e disattivare facilmente i set di comandi. Vedere: [Creare grammatiche usando XML SRGS](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) per le informazioni sul formato di file.

Una volta completata la grammatica SRGS, questa si trova nel progetto in una [cartella StreamingAssets](http://docs.unity3d.com/Manual/StreamingAssets.html):

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

Creare un GrammarRecognizer e passargli il percorso del file SRGS:

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

Registrati ora per l'evento OnPhraseRecognized

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

Si otterrà un callback contenente le informazioni specificate nella grammatica SRGS che è possibile gestire in modo appropriato. La maggior parte delle informazioni importanti verranno fornite nella matrice semanticMeanings.

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

Infine, iniziare a riconoscere.

```
grammarRecognizer.Start();
```

## <a name="dictation"></a>Dettatura

**Spazio dei nomi:** *UnityEngine. Windows. Speech*<br>
**Tipi**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*

Usare DictationRecognizer per convertire il riconoscimento vocale dell'utente in testo. DictationRecognizer espone la funzionalità di [dettatura](voice-input.md#dictation) e supporta la registrazione e l'ascolto di eventi di ipotesi completati e frasi completate, in modo che sia possibile inviare commenti e suggerimenti all'utente sia durante la loro pronuncia che in seguito. I metodi Start () e stop () rispettivamente abilitano e disabilitano il riconoscimento della dettatura. Una volta terminato con il riconoscimento, è necessario eliminarlo utilizzando il metodo Dispose () per rilasciare le risorse utilizzate. Queste risorse verranno rilasciate automaticamente durante Garbage Collection a un costo aggiuntivo in termini di prestazioni, se non vengono rilasciate prima di tale operazione.

Per iniziare a usare la dettatura sono necessari solo alcuni passaggi:
1. Creare un nuovo DictationRecognizer
2. Gestisci eventi di dettatura
3. Avviare il DictationRecognizer

### <a name="enabling-the-capability-for-dictation"></a>Abilitazione della funzionalità per la dettatura

La funzionalità "client Internet", oltre alla funzionalità "microfono" menzionata in precedenza, deve essere dichiarata per poter sfruttare la dettatura per un'app.
1. Nell'editor di Unity passare alle impostazioni del lettore passando alla pagina "Edit > Project Settings > Player"
2. Fare clic sulla scheda "Windows Store"
3. Nella sezione "impostazioni di pubblicazione > funzionalità" controllare la funzionalità **internetClient**

### <a name="dictationrecognizer"></a>DictationRecognizer

Creare un DictationRecognizer come segue:

```
dictationRecognizer = new DictationRecognizer();
```

Sono disponibili quattro eventi di dettatura che è possibile sottoscrivere e gestire per implementare il comportamento di dettatura.
1. DictationResult
2. DictationComplete
3. DictationHypothesis
4. DictationError

**DictationResult**

Questo evento viene generato dopo la sospensione dell'utente, in genere alla fine di una frase. La stringa riconosciuta completa viene restituita qui.

Prima di tutto, sottoscrivere l'evento DictationResult:

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

Gestire quindi il callback di DictationResult:

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

**DictationHypothesis**

Questo evento viene generato continuamente mentre l'utente sta parlando. Quando il riconoscimento è in ascolto, fornisce il testo di ciò che è stato udito finora.

Prima di tutto, sottoscrivere l'evento DictationHypothesis:

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

Gestire quindi il callback di DictationHypothesis:

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

**DictationComplete**

Questo evento viene generato quando il riconoscimento viene arrestato, da Stop () chiamato, da un timeout che si verifica o da un altro errore.

Prima di tutto, sottoscrivere l'evento DictationComplete:

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

Gestire quindi il callback di DictationComplete:

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

**DictationError**

Questo evento viene generato quando si verifica un errore.

Prima di tutto, sottoscrivere l'evento DictationError:

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

Gestire quindi il callback di DictationError:

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

Dopo aver sottoscritto e gestito gli eventi di dettatura di cui si è interessati, avviare il riconoscimento della dettatura per iniziare a ricevere gli eventi.

```
dictationRecognizer.Start();
```

Se non si desidera più proteggere il DictationRecognizer, è necessario annullare la sottoscrizione agli eventi ed eliminare il DictationRecognizer.

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

**Consigli**
* I metodi Start () e stop () rispettivamente abilitano e disabilitano il riconoscimento della dettatura.
* Una volta terminato con il riconoscimento, è necessario eliminarlo utilizzando il metodo Dispose () per rilasciare le risorse utilizzate. Queste risorse verranno rilasciate automaticamente durante Garbage Collection a un costo aggiuntivo in termini di prestazioni, se non vengono rilasciate prima di tale operazione.
* I timeout si verificano dopo un determinato periodo di tempo. È possibile verificare questi timeout nell'evento DictationComplete. È necessario tenere presenti due timeout:
   1. Se il riconoscimento viene avviato e non viene sentito alcun audio per i primi cinque secondi, il timeout verrà attivato.
   2. Se il riconoscimento ha dato un risultato, ma in seguito viene ascoltato il silenzio per 20 secondi, il timeout verrà completato.

## <a name="using-both-phrase-recognition-and-dictation"></a>Uso sia del riconoscimento delle frasi che della dettatura

Se si vuole usare sia il riconoscimento delle frasi che la dettatura nell'app, è necessario chiudere completamente una volta prima di poter avviare l'altra. Se sono in esecuzione più KeywordRecognizers, è possibile arrestarli tutti contemporaneamente con:

```
PhraseRecognitionSystem.Shutdown();
```

Per ripristinare lo stato precedente di tutti i riconoscitori, dopo l'arresto di DictationRecognizer, è possibile chiamare:

```
PhraseRecognitionSystem.Restart();
```

È anche possibile avviare solo un KeywordRecognizer, che riavvia anche il PhraseRecognitionSystem.

## <a name="using-the-microphone-helper"></a>Uso dell'helper del microfono

Il Toolkit di realtà mista in GitHub contiene una classe helper del microfono per suggerire agli sviluppatori se è presente un microfono utilizzabile nel sistema. Uno di questi casi è quello in cui si vuole controllare se è presente un microfono nel sistema prima di visualizzare gli hint di interazione vocale nell'applicazione.

Lo script Helper Microphone è disponibile nella [cartella input/script/Utilities](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs). Il repository GitHub contiene anche un [piccolo esempio](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) che illustra come usare l'helper.

## <a name="voice-input-in-mixed-reality-toolkit"></a>Input vocale nel Toolkit per realtà mista
È possibile trovare gli esempi dell'input vocale in questa scena.

- [HoloToolkit-Examples/input/Scenes/SpeechInputSource. Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity)

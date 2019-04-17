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
# <a name="voice-input-in-unity"></a><span data-ttu-id="159ee-104">Input vocale in Unity</span><span class="sxs-lookup"><span data-stu-id="159ee-104">Voice input in Unity</span></span>

<span data-ttu-id="159ee-105">Unity espone tre modi per aggiungere [input vocale](voice-input.md) all'applicazione di Unity.</span><span class="sxs-lookup"><span data-stu-id="159ee-105">Unity exposes three ways to add [Voice input](voice-input.md) to your Unity application.</span></span>

<span data-ttu-id="159ee-106">Con KeywordRecognizer (uno dei due tipi di PhraseRecognizers), l'app è possibile assegnare una matrice di comandi di stringa per l'ascolto delle.</span><span class="sxs-lookup"><span data-stu-id="159ee-106">With the KeywordRecognizer (one of two types of PhraseRecognizers), your app can be given an array of string commands to listen for.</span></span> <span data-ttu-id="159ee-107">Con la GrammarRecognizer (l'altro tipo di PhraseRecognizer), l'app può essere fornito un file SRGS che definisce una grammatica specifica per l'ascolto.</span><span class="sxs-lookup"><span data-stu-id="159ee-107">With the GrammarRecognizer (the other type of PhraseRecognizer), your app can be given an SRGS file defining a specific grammar to listen for.</span></span> <span data-ttu-id="159ee-108">Con DictationRecognizer, l'app può restare in attesa per tutte le parole e fornire all'utente una nota o altro visualizzatore di loro vocale.</span><span class="sxs-lookup"><span data-stu-id="159ee-108">With the DictationRecognizer, your app can listen for any word and provide the user with a note or other display of their speech.</span></span>

>[!NOTE]
><span data-ttu-id="159ee-109">Solo per la dettatura o riconoscimento dettatura può essere gestito in una sola volta.</span><span class="sxs-lookup"><span data-stu-id="159ee-109">Only dictation or phrase recognition can be handled at once.</span></span> <span data-ttu-id="159ee-110">Ciò significa che se un GrammarRecognizer o KeywordRecognizer è attivo, non può essere attivo un DictationRecognizer e viceversa.</span><span class="sxs-lookup"><span data-stu-id="159ee-110">That means if a GrammarRecognizer or KeywordRecognizer is active, a DictationRecognizer can not be active and vice versa.</span></span>

## <a name="enabling-the-capability-for-voice"></a><span data-ttu-id="159ee-111">Abilitazione della funzionalità per le funzionalità vocali</span><span class="sxs-lookup"><span data-stu-id="159ee-111">Enabling the capability for Voice</span></span>

<span data-ttu-id="159ee-112">Il **microfono** funzionalità devono essere dichiarate per un'app sfruttare l'input vocale.</span><span class="sxs-lookup"><span data-stu-id="159ee-112">The **Microphone** capability must be declared for an app to leverage Voice input.</span></span>
1. <span data-ttu-id="159ee-113">Nell'Editor di Unity, passare alle impostazioni del giocatore, passare a "Modifica > progetto Impostazioni > Player"</span><span class="sxs-lookup"><span data-stu-id="159ee-113">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
2. <span data-ttu-id="159ee-114">Fare clic sulla scheda "Windows Store"</span><span class="sxs-lookup"><span data-stu-id="159ee-114">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="159ee-115">Nella sezione "Impostazioni > le funzionalità di pubblicazione", controllare la **microfono** funzionalità</span><span class="sxs-lookup"><span data-stu-id="159ee-115">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

## <a name="phrase-recognition"></a><span data-ttu-id="159ee-116">Riconoscimento dettatura</span><span class="sxs-lookup"><span data-stu-id="159ee-116">Phrase Recognition</span></span>

<span data-ttu-id="159ee-117">Per abilitare l'app per l'ascolto delle specifiche frasi pronunciate dall'utente, quindi eseguire un'azione, è necessario:</span><span class="sxs-lookup"><span data-stu-id="159ee-117">To enable your app to listen for specific phrases spoken by the user then take some action, you need to:</span></span>
1. <span data-ttu-id="159ee-118">Specificare quali frasi per restare in attesa per l'uso di un KeywordRecognizer o GrammarRecognizer</span><span class="sxs-lookup"><span data-stu-id="159ee-118">Specify which phrases to listen for using a KeywordRecognizer or GrammarRecognizer</span></span>
2. <span data-ttu-id="159ee-119">Gestire l'evento OnPhraseRecognized ed esegue azioni corrispondenti alla frase riconosciuta</span><span class="sxs-lookup"><span data-stu-id="159ee-119">Handle the OnPhraseRecognized event and take action corresponding to the phrase recognized</span></span>

### <a name="keywordrecognizer"></a><span data-ttu-id="159ee-120">KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="159ee-120">KeywordRecognizer</span></span>

<span data-ttu-id="159ee-121">**Namespace:** *UnityEngine.Windows.Speech*</span><span class="sxs-lookup"><span data-stu-id="159ee-121">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="159ee-122">**Tipi:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="159ee-122">**Types:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="159ee-123">Sarà necessario alcune istruzioni using a risparmiare alcune sequenze di tasti:</span><span class="sxs-lookup"><span data-stu-id="159ee-123">We'll need a few using statements to save some keystrokes:</span></span>

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="159ee-124">Quindi aggiungiamo alcuni campi alla classe per archiviare il riconoscimento e (parola chiave) -> dizionario dell'azione:</span><span class="sxs-lookup"><span data-stu-id="159ee-124">Then let's add a few fields to your class to store the recognizer and keyword->action dictionary:</span></span>

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

<span data-ttu-id="159ee-125">Aggiungere ora una parola chiave al dizionario (ad esempio, all'interno di un metodo Start ()).</span><span class="sxs-lookup"><span data-stu-id="159ee-125">Now add a keyword to the dictionary (e.g. inside of a Start() method).</span></span> <span data-ttu-id="159ee-126">Stiamo aggiungendo la parola chiave "attiva" in questo esempio:</span><span class="sxs-lookup"><span data-stu-id="159ee-126">We're adding the "activate" keyword in this example:</span></span>

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

<span data-ttu-id="159ee-127">Creare il riconoscimento (parola chiave) e gli si indica ciò che si desidera riconoscere:</span><span class="sxs-lookup"><span data-stu-id="159ee-127">Create the keyword recognizer and tell it what we want to recognize:</span></span>

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

<span data-ttu-id="159ee-128">Ora registrare per l'evento OnPhraseRecognized</span><span class="sxs-lookup"><span data-stu-id="159ee-128">Now register for the OnPhraseRecognized event</span></span>

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="159ee-129">Un gestore di esempio è:</span><span class="sxs-lookup"><span data-stu-id="159ee-129">An example handler is:</span></span>

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

<span data-ttu-id="159ee-130">Al termine, avviare il riconoscimento.</span><span class="sxs-lookup"><span data-stu-id="159ee-130">Finally, start recognizing!</span></span>

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a><span data-ttu-id="159ee-131">GrammarRecognizer</span><span class="sxs-lookup"><span data-stu-id="159ee-131">GrammarRecognizer</span></span>

<span data-ttu-id="159ee-132">**Namespace:** *UnityEngine.Windows.Speech*</span><span class="sxs-lookup"><span data-stu-id="159ee-132">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="159ee-133">**Tipi**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="159ee-133">**Types**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="159ee-134">Il GrammarRecognizer viene usato se si specifica la grammatica di riconoscimento con SRGS.</span><span class="sxs-lookup"><span data-stu-id="159ee-134">The GrammarRecognizer is used if you're specifying your recognition grammar using SRGS.</span></span> <span data-ttu-id="159ee-135">Ciò può essere utile se l'app ha più di pochi parole chiave, se si desidera identificare le frasi più complesse, o se si desidera attivare con facilità e disattivare i set di comandi.</span><span class="sxs-lookup"><span data-stu-id="159ee-135">This can be useful if your app has more than just a few keywords, if you want to recognize more complex phrases, or if you want to easily turn on and off sets of commands.</span></span> <span data-ttu-id="159ee-136">Vedere: [Creare grammatiche tramite SRGS XML](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) per informazioni sul formato di file.</span><span class="sxs-lookup"><span data-stu-id="159ee-136">See: [Create Grammars Using SRGS XML](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) for file format information.</span></span>

<span data-ttu-id="159ee-137">Una volta che si dispone di grammatica SRGS ed è nel progetto in un [StreamingAssets cartella](http://docs.unity3d.com/Manual/StreamingAssets.html):</span><span class="sxs-lookup"><span data-stu-id="159ee-137">Once you have your SRGS grammar, and it is in your project in a [StreamingAssets folder](http://docs.unity3d.com/Manual/StreamingAssets.html):</span></span>

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

<span data-ttu-id="159ee-138">Creare un GrammarRecognizer e chiamarla dal percorso del file SRGS:</span><span class="sxs-lookup"><span data-stu-id="159ee-138">Create a GrammarRecognizer and pass it the path to your SRGS file:</span></span>

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

<span data-ttu-id="159ee-139">Ora registrare per l'evento OnPhraseRecognized</span><span class="sxs-lookup"><span data-stu-id="159ee-139">Now register for the OnPhraseRecognized event</span></span>

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="159ee-140">Si riceverà un callback che contiene le informazioni specificate nella grammatica SRGS che è possibile gestire in modo appropriato.</span><span class="sxs-lookup"><span data-stu-id="159ee-140">You will get a callback containing information specified in your SRGS grammar which you can handle appropriately.</span></span> <span data-ttu-id="159ee-141">La maggior parte delle informazioni importanti verrà fornita nella matrice semanticMeanings.</span><span class="sxs-lookup"><span data-stu-id="159ee-141">Most of the important information will be provided in the semanticMeanings array.</span></span>

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

<span data-ttu-id="159ee-142">Al termine, avviare il riconoscimento.</span><span class="sxs-lookup"><span data-stu-id="159ee-142">Finally, start recognizing!</span></span>

```
grammarRecognizer.Start();
```

## <a name="dictation"></a><span data-ttu-id="159ee-143">Dettatura</span><span class="sxs-lookup"><span data-stu-id="159ee-143">Dictation</span></span>

<span data-ttu-id="159ee-144">**Namespace:** *UnityEngine.Windows.Speech*</span><span class="sxs-lookup"><span data-stu-id="159ee-144">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="159ee-145">**Tipi**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="159ee-145">**Types**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="159ee-146">Usare il DictationRecognizer per convertire il riconoscimento vocale dell'utente in testo.</span><span class="sxs-lookup"><span data-stu-id="159ee-146">Use the DictationRecognizer to convert the user's speech to text.</span></span> <span data-ttu-id="159ee-147">Espone le DictationRecognizer [dettatura](voice-input.md#dictation) funzionalità e supporta la registrazione e l'ascolto delle ipotesi e frase completati gli eventi, pertanto è possibile assegnare i commenti e suggerimenti per l'utente sia mentre si parla e in un secondo momento.</span><span class="sxs-lookup"><span data-stu-id="159ee-147">The DictationRecognizer exposes [dictation](voice-input.md#dictation) functionality and supports registering and listening for hypothesis and phrase completed events, so you can give feedback to your user both while they speak and afterwards.</span></span> <span data-ttu-id="159ee-148">Metodi Start () e Stop (), rispettivamente, abilitare e disabilitare il riconoscimento dettatura continua.</span><span class="sxs-lookup"><span data-stu-id="159ee-148">Start() and Stop() methods respectively enable and disable dictation recognition.</span></span> <span data-ttu-id="159ee-149">Una volta completata la sospensione del riconoscimento, che deve essere eliminato usando il metodo Dispose () per rilasciare le risorse che usa.</span><span class="sxs-lookup"><span data-stu-id="159ee-149">Once done with the recognizer, it should be disposed using Dispose() method to release the resources it uses.</span></span> <span data-ttu-id="159ee-150">Rilascerà tali risorse automaticamente durante l'operazione di garbage collection a un costo aggiuntivo delle prestazioni se essi non vengono rilasciate prima di tale.</span><span class="sxs-lookup"><span data-stu-id="159ee-150">It will release these resources automatically during garbage collection at an additional performance cost if they are not released prior to that.</span></span>

<span data-ttu-id="159ee-151">Sono disponibili solo pochi passaggi necessari per iniziare a usare la dettatura:</span><span class="sxs-lookup"><span data-stu-id="159ee-151">There are only a few steps needed to get started with dictation:</span></span>
1. <span data-ttu-id="159ee-152">Creare un nuovo DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="159ee-152">Create a new DictationRecognizer</span></span>
2. <span data-ttu-id="159ee-153">Gestire gli eventi di dettatura</span><span class="sxs-lookup"><span data-stu-id="159ee-153">Handle Dictation events</span></span>
3. <span data-ttu-id="159ee-154">Avviare il DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="159ee-154">Start the DictationRecognizer</span></span>

### <a name="enabling-the-capability-for-dictation"></a><span data-ttu-id="159ee-155">Abilitazione della funzionalità per la dettatura</span><span class="sxs-lookup"><span data-stu-id="159ee-155">Enabling the capability for dictation</span></span>

<span data-ttu-id="159ee-156">La funzionalità "Internet Client", oltre alle funzionalità "Microfono" indicato in precedenza, deve essere dichiarata per un'app sfruttare la dettatura.</span><span class="sxs-lookup"><span data-stu-id="159ee-156">The "Internet Client" capability, in addition to the "Microphone" capability mentioned above, must be declared for an app to leverage dictation.</span></span>
1. <span data-ttu-id="159ee-157">Nell'Editor di Unity, passare alle impostazioni del giocatore, passare alla pagina "Modifica > progetto Impostazioni > Player"</span><span class="sxs-lookup"><span data-stu-id="159ee-157">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="159ee-158">Fare clic sulla scheda "Windows Store"</span><span class="sxs-lookup"><span data-stu-id="159ee-158">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="159ee-159">Nella sezione "Impostazioni > le funzionalità di pubblicazione", controllare la **InternetClient** funzionalità</span><span class="sxs-lookup"><span data-stu-id="159ee-159">In the "Publishing Settings > Capabilities" section, check the **InternetClient** capability</span></span>

### <a name="dictationrecognizer"></a><span data-ttu-id="159ee-160">DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="159ee-160">DictationRecognizer</span></span>

<span data-ttu-id="159ee-161">Creare un DictationRecognizer come segue:</span><span class="sxs-lookup"><span data-stu-id="159ee-161">Create a DictationRecognizer like so:</span></span>

```
dictationRecognizer = new DictationRecognizer();
```

<span data-ttu-id="159ee-162">Esistono quattro eventi dettatura che possono essere sottoscritto e gestiti per implementare il comportamento di dettatura.</span><span class="sxs-lookup"><span data-stu-id="159ee-162">There are four dictation events that can be subscribed to and handled to implement dictation behavior.</span></span>
1. <span data-ttu-id="159ee-163">DictationResult</span><span class="sxs-lookup"><span data-stu-id="159ee-163">DictationResult</span></span>
2. <span data-ttu-id="159ee-164">DictationComplete</span><span class="sxs-lookup"><span data-stu-id="159ee-164">DictationComplete</span></span>
3. <span data-ttu-id="159ee-165">DictationHypothesis</span><span class="sxs-lookup"><span data-stu-id="159ee-165">DictationHypothesis</span></span>
4. <span data-ttu-id="159ee-166">DictationError</span><span class="sxs-lookup"><span data-stu-id="159ee-166">DictationError</span></span>

<span data-ttu-id="159ee-167">**DictationResult**</span><span class="sxs-lookup"><span data-stu-id="159ee-167">**DictationResult**</span></span>

<span data-ttu-id="159ee-168">Questo evento viene generato dopo che l'utente mette in pausa, in genere alla fine di una frase.</span><span class="sxs-lookup"><span data-stu-id="159ee-168">This event is fired after the user pauses, typically at the end of a sentence.</span></span> <span data-ttu-id="159ee-169">La versione completa riconosciuto stringa viene restituita qui.</span><span class="sxs-lookup"><span data-stu-id="159ee-169">The full recognized string is returned here.</span></span>

<span data-ttu-id="159ee-170">In primo luogo, sottoscrivere l'evento DictationResult:</span><span class="sxs-lookup"><span data-stu-id="159ee-170">First, subscribe to the DictationResult event:</span></span>

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

<span data-ttu-id="159ee-171">Quindi gestire il callback DictationResult:</span><span class="sxs-lookup"><span data-stu-id="159ee-171">Then handle the DictationResult callback:</span></span>

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

<span data-ttu-id="159ee-172">**DictationHypothesis**</span><span class="sxs-lookup"><span data-stu-id="159ee-172">**DictationHypothesis**</span></span>

<span data-ttu-id="159ee-173">Questo evento viene generato continuamente mentre l'utente sta parlando.</span><span class="sxs-lookup"><span data-stu-id="159ee-173">This event is fired continuously while the user is talking.</span></span> <span data-ttu-id="159ee-174">Come è in ascolto il riconoscimento, fornisce il testo di ciò che è sentito parlare finora.</span><span class="sxs-lookup"><span data-stu-id="159ee-174">As the recognizer listens, it provides text of what it's heard so far.</span></span>

<span data-ttu-id="159ee-175">In primo luogo, sottoscrivere l'evento DictationHypothesis:</span><span class="sxs-lookup"><span data-stu-id="159ee-175">First, subscribe to the DictationHypothesis event:</span></span>

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

<span data-ttu-id="159ee-176">Quindi gestire il callback DictationHypothesis:</span><span class="sxs-lookup"><span data-stu-id="159ee-176">Then handle the DictationHypothesis callback:</span></span>

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

<span data-ttu-id="159ee-177">**DictationComplete**</span><span class="sxs-lookup"><span data-stu-id="159ee-177">**DictationComplete**</span></span>

<span data-ttu-id="159ee-178">Questo evento viene generato quando si arresta il riconoscimento, sia da Stop () viene chiamato, un timeout che si verificano, o un altro errore.</span><span class="sxs-lookup"><span data-stu-id="159ee-178">This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.</span></span>

<span data-ttu-id="159ee-179">In primo luogo, sottoscrivere l'evento DictationComplete:</span><span class="sxs-lookup"><span data-stu-id="159ee-179">First, subscribe to the DictationComplete event:</span></span>

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

<span data-ttu-id="159ee-180">Quindi gestire il callback DictationComplete:</span><span class="sxs-lookup"><span data-stu-id="159ee-180">Then handle the DictationComplete callback:</span></span>

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

<span data-ttu-id="159ee-181">**DictationError**</span><span class="sxs-lookup"><span data-stu-id="159ee-181">**DictationError**</span></span>

<span data-ttu-id="159ee-182">Questo evento viene generato quando si verifica un errore.</span><span class="sxs-lookup"><span data-stu-id="159ee-182">This event is fired when an error occurs.</span></span>

<span data-ttu-id="159ee-183">In primo luogo, sottoscrivere l'evento DictationError:</span><span class="sxs-lookup"><span data-stu-id="159ee-183">First, subscribe to the DictationError event:</span></span>

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

<span data-ttu-id="159ee-184">Quindi gestire il callback DictationError:</span><span class="sxs-lookup"><span data-stu-id="159ee-184">Then handle the DictationError callback:</span></span>

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

<span data-ttu-id="159ee-185">Dopo aver sottoscritto e gestiti gli eventi di dettatura che si è interessati, avviare il riconoscimento dettatura per iniziare a ricevere gli eventi.</span><span class="sxs-lookup"><span data-stu-id="159ee-185">Once you have subscribed and handled the dictation events that you care about, start the dictation recognizer to begin receiving events.</span></span>

```
dictationRecognizer.Start();
```

<span data-ttu-id="159ee-186">Se non è più si desidera mantenere il DictationRecognizer intorno, è necessario annullare la sottoscrizione a eventi ed eliminare il DictationRecognizer.</span><span class="sxs-lookup"><span data-stu-id="159ee-186">If you no longer want to keep the DictationRecognizer around, you need to unsubscribe from the events and Dispose the DictationRecognizer.</span></span>

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

<span data-ttu-id="159ee-187">**Suggerimenti**</span><span class="sxs-lookup"><span data-stu-id="159ee-187">**Tips**</span></span>
* <span data-ttu-id="159ee-188">Metodi Start () e Stop (), rispettivamente, abilitare e disabilitare il riconoscimento dettatura continua.</span><span class="sxs-lookup"><span data-stu-id="159ee-188">Start() and Stop() methods respectively enable and disable dictation recognition.</span></span>
* <span data-ttu-id="159ee-189">Una volta completata la sospensione del riconoscimento, deve essere eliminato usando il metodo Dispose () per rilasciare le risorse che usa.</span><span class="sxs-lookup"><span data-stu-id="159ee-189">Once done with the recognizer, it must be disposed using Dispose() method to release the resources it uses.</span></span> <span data-ttu-id="159ee-190">Rilascerà tali risorse automaticamente durante l'operazione di garbage collection a un costo aggiuntivo delle prestazioni se essi non vengono rilasciate prima di tale.</span><span class="sxs-lookup"><span data-stu-id="159ee-190">It will release these resources automatically during garbage collection at an additional performance cost if they are not released prior to that.</span></span>
* <span data-ttu-id="159ee-191">I timeout si verificano dopo un periodo di tempo.</span><span class="sxs-lookup"><span data-stu-id="159ee-191">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="159ee-192">È possibile cercare questi timeout nell'evento DictationComplete.</span><span class="sxs-lookup"><span data-stu-id="159ee-192">You can check for these timeouts in the DictationComplete event.</span></span> <span data-ttu-id="159ee-193">Esistono due timeout da tenere presenti:</span><span class="sxs-lookup"><span data-stu-id="159ee-193">There are two timeouts to be aware of:</span></span>
   1. <span data-ttu-id="159ee-194">Se il riconoscimento viene avviato e non ascolta l'audio per i primi cinque secondi, si verifica un timeout.</span><span class="sxs-lookup"><span data-stu-id="159ee-194">If the recognizer starts and doesn't hear any audio for the first five seconds, it will timeout.</span></span>
   2. <span data-ttu-id="159ee-195">Se il riconoscimento ha fornito un risultato, ma quindi ascolta silenzio per venti secondi, si verifica un timeout.</span><span class="sxs-lookup"><span data-stu-id="159ee-195">If the recognizer has given a result but then hears silence for twenty seconds, it will timeout.</span></span>

## <a name="using-both-phrase-recognition-and-dictation"></a><span data-ttu-id="159ee-196">Tramite riconoscimento dettatura e la dettatura</span><span class="sxs-lookup"><span data-stu-id="159ee-196">Using both Phrase Recognition and Dictation</span></span>

<span data-ttu-id="159ee-197">Se si desidera utilizzare sia riconoscimento dettatura e la dettatura nell'app, è necessario arrestare completamente uno prima di iniziare l'altro.</span><span class="sxs-lookup"><span data-stu-id="159ee-197">If you want to use both phrase recognition and dictation in your app, you'll need to fully shut one down before you can start the other.</span></span> <span data-ttu-id="159ee-198">Se si dispone di più in esecuzione KeywordRecognizers, è possibile arrestarli tutto in una sola volta con:</span><span class="sxs-lookup"><span data-stu-id="159ee-198">If you have multiple KeywordRecognizers running, you can shut them all down at once with:</span></span>

```
PhraseRecognitionSystem.Shutdown();
```

<span data-ttu-id="159ee-199">Per ripristinare tutti i riconoscitori allo stato precedente, dopo il DictationRecognizer è stato arrestato, è possibile chiamare:</span><span class="sxs-lookup"><span data-stu-id="159ee-199">In order to restore all recognizers to their previous state, after the DictationRecognizer has stopped, you can call:</span></span>

```
PhraseRecognitionSystem.Restart();
```

<span data-ttu-id="159ee-200">È inoltre sufficiente è stato possibile avviare un KeywordRecognizer, che verrà riavviato anche il PhraseRecognitionSystem.</span><span class="sxs-lookup"><span data-stu-id="159ee-200">You could also just start a KeywordRecognizer, which will restart the PhraseRecognitionSystem as well.</span></span>

## <a name="using-the-microphone-helper"></a><span data-ttu-id="159ee-201">Utilizzo dell'helper di microfono</span><span class="sxs-lookup"><span data-stu-id="159ee-201">Using the microphone helper</span></span>

<span data-ttu-id="159ee-202">Il Toolkit di realtà mista su GitHub contiene una classe helper di microfono per indicativi di sviluppatori se è presente un microfono utilizzabile nel sistema.</span><span class="sxs-lookup"><span data-stu-id="159ee-202">The Mixed Reality Toolkit on GitHub contains a microphone helper class to hint at developers if there is a usable microphone on the system.</span></span> <span data-ttu-id="159ee-203">Uno viene utilizzato in cui uno desidera controllare se è presente microfono sul sistema prima di visualizzare qualsiasi parlato hint per l'interazione dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="159ee-203">One use for it is where one would want to check if there is microphone on system before showing any speech interaction hints in the application.</span></span>

<span data-ttu-id="159ee-204">Lo script helper microfono è reperibile nella [cartella di Input/script o utilità](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs).</span><span class="sxs-lookup"><span data-stu-id="159ee-204">The microphone helper script can be found in the [Input/Scripts/Utilities folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs).</span></span> <span data-ttu-id="159ee-205">Il repository GitHub contiene anche un [piccolo campione](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) che illustra come usare l'helper.</span><span class="sxs-lookup"><span data-stu-id="159ee-205">The GitHub repo also contains a [small sample](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) demonstrating how to use the helper.</span></span>

## <a name="voice-input-in-mixed-reality-toolkit"></a><span data-ttu-id="159ee-206">Input vocale in Toolkit di realtà mista</span><span class="sxs-lookup"><span data-stu-id="159ee-206">Voice input in Mixed Reality Toolkit</span></span>
<span data-ttu-id="159ee-207">È possibile trovare gli esempi dell'input vocale in questa scena.</span><span class="sxs-lookup"><span data-stu-id="159ee-207">You can find the examples of the voice input in this scene.</span></span>

- [<span data-ttu-id="159ee-208">HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity</span><span class="sxs-lookup"><span data-stu-id="159ee-208">HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity)

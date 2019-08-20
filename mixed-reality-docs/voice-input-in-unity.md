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
# <a name="voice-input-in-unity"></a><span data-ttu-id="ff533-104">Input vocale in Unity</span><span class="sxs-lookup"><span data-stu-id="ff533-104">Voice input in Unity</span></span>

<span data-ttu-id="ff533-105">Unity espone tre modi per aggiungere [input vocale](voice-input.md) all'applicazione Unity.</span><span class="sxs-lookup"><span data-stu-id="ff533-105">Unity exposes three ways to add [Voice input](voice-input.md) to your Unity application.</span></span>

<span data-ttu-id="ff533-106">Con KeywordRecognizer (uno dei due tipi di PhraseRecognizers), all'app può essere assegnata una matrice di comandi stringa da ascoltare.</span><span class="sxs-lookup"><span data-stu-id="ff533-106">With the KeywordRecognizer (one of two types of PhraseRecognizers), your app can be given an array of string commands to listen for.</span></span> <span data-ttu-id="ff533-107">Con GrammarRecognizer (l'altro tipo di PhraseRecognizer), all'app può essere assegnato un file SRGS che definisce una grammatica specifica per l'ascolto.</span><span class="sxs-lookup"><span data-stu-id="ff533-107">With the GrammarRecognizer (the other type of PhraseRecognizer), your app can be given an SRGS file defining a specific grammar to listen for.</span></span> <span data-ttu-id="ff533-108">Con la DictationRecognizer, l'app può restare in ascolto di qualsiasi parola e fornire all'utente una nota o un'altra visualizzazione del riconoscimento vocale.</span><span class="sxs-lookup"><span data-stu-id="ff533-108">With the DictationRecognizer, your app can listen for any word and provide the user with a note or other display of their speech.</span></span>

>[!NOTE]
><span data-ttu-id="ff533-109">Solo i riconoscimenti di dettatura o di frase possono essere gestiti in una sola volta.</span><span class="sxs-lookup"><span data-stu-id="ff533-109">Only dictation or phrase recognition can be handled at once.</span></span> <span data-ttu-id="ff533-110">Ciò significa che se GrammarRecognizer o KeywordRecognizer è attivo, un DictationRecognizer non può essere attivo e viceversa.</span><span class="sxs-lookup"><span data-stu-id="ff533-110">That means if a GrammarRecognizer or KeywordRecognizer is active, a DictationRecognizer can not be active and vice versa.</span></span>

## <a name="enabling-the-capability-for-voice"></a><span data-ttu-id="ff533-111">Abilitazione della funzionalità per la voce</span><span class="sxs-lookup"><span data-stu-id="ff533-111">Enabling the capability for Voice</span></span>

<span data-ttu-id="ff533-112">Per poter sfruttare l'input vocale, è necessario dichiarare la funzionalità del **microfono** per un'app.</span><span class="sxs-lookup"><span data-stu-id="ff533-112">The **Microphone** capability must be declared for an app to leverage Voice input.</span></span>
1. <span data-ttu-id="ff533-113">Nell'editor di Unity passare a Impostazioni lettore passando a "Modifica > Impostazioni progetto > lettore"</span><span class="sxs-lookup"><span data-stu-id="ff533-113">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
2. <span data-ttu-id="ff533-114">Fare clic sulla scheda "Windows Store"</span><span class="sxs-lookup"><span data-stu-id="ff533-114">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="ff533-115">Nella sezione "impostazioni di pubblicazione > funzionalità" controllare la funzionalità del **microfono**</span><span class="sxs-lookup"><span data-stu-id="ff533-115">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

## <a name="phrase-recognition"></a><span data-ttu-id="ff533-116">Riconoscimento di frasi</span><span class="sxs-lookup"><span data-stu-id="ff533-116">Phrase Recognition</span></span>

<span data-ttu-id="ff533-117">Per consentire all'app di restare in ascolto di frasi specifiche pronunciate dall'utente, è necessario eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="ff533-117">To enable your app to listen for specific phrases spoken by the user then take some action, you need to:</span></span>
1. <span data-ttu-id="ff533-118">Specificare le frasi da ascoltare tramite KeywordRecognizer o GrammarRecognizer</span><span class="sxs-lookup"><span data-stu-id="ff533-118">Specify which phrases to listen for using a KeywordRecognizer or GrammarRecognizer</span></span>
2. <span data-ttu-id="ff533-119">Gestire l'evento OnPhraseRecognized ed eseguire un'azione corrispondente alla frase riconosciuta</span><span class="sxs-lookup"><span data-stu-id="ff533-119">Handle the OnPhraseRecognized event and take action corresponding to the phrase recognized</span></span>

### <a name="keywordrecognizer"></a><span data-ttu-id="ff533-120">KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="ff533-120">KeywordRecognizer</span></span>

<span data-ttu-id="ff533-121">**Namespace** *UnityEngine. Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="ff533-121">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="ff533-122">**Tipi** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="ff533-122">**Types:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="ff533-123">Sono necessarie alcune istruzioni using per salvare alcune sequenze di tasti:</span><span class="sxs-lookup"><span data-stu-id="ff533-123">We'll need a few using statements to save some keystrokes:</span></span>

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="ff533-124">Aggiungere quindi alcuni campi alla classe per archiviare il riconoscimento e la parola chiave > dizionario azione:</span><span class="sxs-lookup"><span data-stu-id="ff533-124">Then let's add a few fields to your class to store the recognizer and keyword->action dictionary:</span></span>

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

<span data-ttu-id="ff533-125">Aggiungere ora una parola chiave al dizionario, ad esempio all'interno di un metodo Start ().</span><span class="sxs-lookup"><span data-stu-id="ff533-125">Now add a keyword to the dictionary (e.g. inside of a Start() method).</span></span> <span data-ttu-id="ff533-126">In questo esempio viene aggiunta la parola chiave "Activate":</span><span class="sxs-lookup"><span data-stu-id="ff533-126">We're adding the "activate" keyword in this example:</span></span>

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

<span data-ttu-id="ff533-127">Creare la parola chiave Recognizer e indicare cosa si vuole riconoscere:</span><span class="sxs-lookup"><span data-stu-id="ff533-127">Create the keyword recognizer and tell it what we want to recognize:</span></span>

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

<span data-ttu-id="ff533-128">Registrati ora per l'evento OnPhraseRecognized</span><span class="sxs-lookup"><span data-stu-id="ff533-128">Now register for the OnPhraseRecognized event</span></span>

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="ff533-129">Un gestore di esempio è:</span><span class="sxs-lookup"><span data-stu-id="ff533-129">An example handler is:</span></span>

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

<span data-ttu-id="ff533-130">Infine, iniziare a riconoscere.</span><span class="sxs-lookup"><span data-stu-id="ff533-130">Finally, start recognizing!</span></span>

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a><span data-ttu-id="ff533-131">GrammarRecognizer</span><span class="sxs-lookup"><span data-stu-id="ff533-131">GrammarRecognizer</span></span>

<span data-ttu-id="ff533-132">**Namespace** *UnityEngine. Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="ff533-132">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="ff533-133">**Tipi**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="ff533-133">**Types**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="ff533-134">GrammarRecognizer viene usato se si specifica la grammatica di riconoscimento usando SRGS.</span><span class="sxs-lookup"><span data-stu-id="ff533-134">The GrammarRecognizer is used if you're specifying your recognition grammar using SRGS.</span></span> <span data-ttu-id="ff533-135">Questo può essere utile se l'app ha più di poche parole chiave, se si desidera riconoscere frasi più complesse o se si desidera attivare e disattivare facilmente i set di comandi.</span><span class="sxs-lookup"><span data-stu-id="ff533-135">This can be useful if your app has more than just a few keywords, if you want to recognize more complex phrases, or if you want to easily turn on and off sets of commands.</span></span> <span data-ttu-id="ff533-136">Vedere: [Creare grammatiche usando XML SRGS](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) per le informazioni sul formato di file.</span><span class="sxs-lookup"><span data-stu-id="ff533-136">See: [Create Grammars Using SRGS XML](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) for file format information.</span></span>

<span data-ttu-id="ff533-137">Una volta completata la grammatica SRGS, questa si trova nel progetto in una [cartella StreamingAssets](http://docs.unity3d.com/Manual/StreamingAssets.html):</span><span class="sxs-lookup"><span data-stu-id="ff533-137">Once you have your SRGS grammar, and it is in your project in a [StreamingAssets folder](http://docs.unity3d.com/Manual/StreamingAssets.html):</span></span>

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

<span data-ttu-id="ff533-138">Creare un GrammarRecognizer e passargli il percorso del file SRGS:</span><span class="sxs-lookup"><span data-stu-id="ff533-138">Create a GrammarRecognizer and pass it the path to your SRGS file:</span></span>

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

<span data-ttu-id="ff533-139">Registrati ora per l'evento OnPhraseRecognized</span><span class="sxs-lookup"><span data-stu-id="ff533-139">Now register for the OnPhraseRecognized event</span></span>

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="ff533-140">Si otterrà un callback contenente le informazioni specificate nella grammatica SRGS che è possibile gestire in modo appropriato.</span><span class="sxs-lookup"><span data-stu-id="ff533-140">You will get a callback containing information specified in your SRGS grammar which you can handle appropriately.</span></span> <span data-ttu-id="ff533-141">La maggior parte delle informazioni importanti verranno fornite nella matrice semanticMeanings.</span><span class="sxs-lookup"><span data-stu-id="ff533-141">Most of the important information will be provided in the semanticMeanings array.</span></span>

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

<span data-ttu-id="ff533-142">Infine, iniziare a riconoscere.</span><span class="sxs-lookup"><span data-stu-id="ff533-142">Finally, start recognizing!</span></span>

```
grammarRecognizer.Start();
```

## <a name="dictation"></a><span data-ttu-id="ff533-143">Dettatura</span><span class="sxs-lookup"><span data-stu-id="ff533-143">Dictation</span></span>

<span data-ttu-id="ff533-144">**Spazio dei nomi:** *UnityEngine. Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="ff533-144">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="ff533-145">**Tipi**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="ff533-145">**Types**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="ff533-146">Usare DictationRecognizer per convertire il riconoscimento vocale dell'utente in testo.</span><span class="sxs-lookup"><span data-stu-id="ff533-146">Use the DictationRecognizer to convert the user's speech to text.</span></span> <span data-ttu-id="ff533-147">DictationRecognizer espone la funzionalità di [dettatura](voice-input.md#dictation) e supporta la registrazione e l'ascolto di eventi di ipotesi completati e frasi completate, in modo che sia possibile inviare commenti e suggerimenti all'utente sia durante la loro pronuncia che in seguito.</span><span class="sxs-lookup"><span data-stu-id="ff533-147">The DictationRecognizer exposes [dictation](voice-input.md#dictation) functionality and supports registering and listening for hypothesis and phrase completed events, so you can give feedback to your user both while they speak and afterwards.</span></span> <span data-ttu-id="ff533-148">I metodi Start () e stop () rispettivamente abilitano e disabilitano il riconoscimento della dettatura.</span><span class="sxs-lookup"><span data-stu-id="ff533-148">Start() and Stop() methods respectively enable and disable dictation recognition.</span></span> <span data-ttu-id="ff533-149">Una volta terminato con il riconoscimento, è necessario eliminarlo utilizzando il metodo Dispose () per rilasciare le risorse utilizzate.</span><span class="sxs-lookup"><span data-stu-id="ff533-149">Once done with the recognizer, it should be disposed using Dispose() method to release the resources it uses.</span></span> <span data-ttu-id="ff533-150">Queste risorse verranno rilasciate automaticamente durante Garbage Collection a un costo aggiuntivo in termini di prestazioni, se non vengono rilasciate prima di tale operazione.</span><span class="sxs-lookup"><span data-stu-id="ff533-150">It will release these resources automatically during garbage collection at an additional performance cost if they are not released prior to that.</span></span>

<span data-ttu-id="ff533-151">Per iniziare a usare la dettatura sono necessari solo alcuni passaggi:</span><span class="sxs-lookup"><span data-stu-id="ff533-151">There are only a few steps needed to get started with dictation:</span></span>
1. <span data-ttu-id="ff533-152">Creare un nuovo DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="ff533-152">Create a new DictationRecognizer</span></span>
2. <span data-ttu-id="ff533-153">Gestisci eventi di dettatura</span><span class="sxs-lookup"><span data-stu-id="ff533-153">Handle Dictation events</span></span>
3. <span data-ttu-id="ff533-154">Avviare il DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="ff533-154">Start the DictationRecognizer</span></span>

### <a name="enabling-the-capability-for-dictation"></a><span data-ttu-id="ff533-155">Abilitazione della funzionalità per la dettatura</span><span class="sxs-lookup"><span data-stu-id="ff533-155">Enabling the capability for dictation</span></span>

<span data-ttu-id="ff533-156">La funzionalità "client Internet", oltre alla funzionalità "microfono" menzionata in precedenza, deve essere dichiarata per poter sfruttare la dettatura per un'app.</span><span class="sxs-lookup"><span data-stu-id="ff533-156">The "Internet Client" capability, in addition to the "Microphone" capability mentioned above, must be declared for an app to leverage dictation.</span></span>
1. <span data-ttu-id="ff533-157">Nell'editor di Unity passare alle impostazioni del lettore passando alla pagina "Edit > Project Settings > Player"</span><span class="sxs-lookup"><span data-stu-id="ff533-157">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="ff533-158">Fare clic sulla scheda "Windows Store"</span><span class="sxs-lookup"><span data-stu-id="ff533-158">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="ff533-159">Nella sezione "impostazioni di pubblicazione > funzionalità" controllare la funzionalità **internetClient**</span><span class="sxs-lookup"><span data-stu-id="ff533-159">In the "Publishing Settings > Capabilities" section, check the **InternetClient** capability</span></span>

### <a name="dictationrecognizer"></a><span data-ttu-id="ff533-160">DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="ff533-160">DictationRecognizer</span></span>

<span data-ttu-id="ff533-161">Creare un DictationRecognizer come segue:</span><span class="sxs-lookup"><span data-stu-id="ff533-161">Create a DictationRecognizer like so:</span></span>

```
dictationRecognizer = new DictationRecognizer();
```

<span data-ttu-id="ff533-162">Sono disponibili quattro eventi di dettatura che è possibile sottoscrivere e gestire per implementare il comportamento di dettatura.</span><span class="sxs-lookup"><span data-stu-id="ff533-162">There are four dictation events that can be subscribed to and handled to implement dictation behavior.</span></span>
1. <span data-ttu-id="ff533-163">DictationResult</span><span class="sxs-lookup"><span data-stu-id="ff533-163">DictationResult</span></span>
2. <span data-ttu-id="ff533-164">DictationComplete</span><span class="sxs-lookup"><span data-stu-id="ff533-164">DictationComplete</span></span>
3. <span data-ttu-id="ff533-165">DictationHypothesis</span><span class="sxs-lookup"><span data-stu-id="ff533-165">DictationHypothesis</span></span>
4. <span data-ttu-id="ff533-166">DictationError</span><span class="sxs-lookup"><span data-stu-id="ff533-166">DictationError</span></span>

<span data-ttu-id="ff533-167">**DictationResult**</span><span class="sxs-lookup"><span data-stu-id="ff533-167">**DictationResult**</span></span>

<span data-ttu-id="ff533-168">Questo evento viene generato dopo la sospensione dell'utente, in genere alla fine di una frase.</span><span class="sxs-lookup"><span data-stu-id="ff533-168">This event is fired after the user pauses, typically at the end of a sentence.</span></span> <span data-ttu-id="ff533-169">La stringa riconosciuta completa viene restituita qui.</span><span class="sxs-lookup"><span data-stu-id="ff533-169">The full recognized string is returned here.</span></span>

<span data-ttu-id="ff533-170">Prima di tutto, sottoscrivere l'evento DictationResult:</span><span class="sxs-lookup"><span data-stu-id="ff533-170">First, subscribe to the DictationResult event:</span></span>

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

<span data-ttu-id="ff533-171">Gestire quindi il callback di DictationResult:</span><span class="sxs-lookup"><span data-stu-id="ff533-171">Then handle the DictationResult callback:</span></span>

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

<span data-ttu-id="ff533-172">**DictationHypothesis**</span><span class="sxs-lookup"><span data-stu-id="ff533-172">**DictationHypothesis**</span></span>

<span data-ttu-id="ff533-173">Questo evento viene generato continuamente mentre l'utente sta parlando.</span><span class="sxs-lookup"><span data-stu-id="ff533-173">This event is fired continuously while the user is talking.</span></span> <span data-ttu-id="ff533-174">Quando il riconoscimento è in ascolto, fornisce il testo di ciò che è stato udito finora.</span><span class="sxs-lookup"><span data-stu-id="ff533-174">As the recognizer listens, it provides text of what it's heard so far.</span></span>

<span data-ttu-id="ff533-175">Prima di tutto, sottoscrivere l'evento DictationHypothesis:</span><span class="sxs-lookup"><span data-stu-id="ff533-175">First, subscribe to the DictationHypothesis event:</span></span>

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

<span data-ttu-id="ff533-176">Gestire quindi il callback di DictationHypothesis:</span><span class="sxs-lookup"><span data-stu-id="ff533-176">Then handle the DictationHypothesis callback:</span></span>

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

<span data-ttu-id="ff533-177">**DictationComplete**</span><span class="sxs-lookup"><span data-stu-id="ff533-177">**DictationComplete**</span></span>

<span data-ttu-id="ff533-178">Questo evento viene generato quando il riconoscimento viene arrestato, da Stop () chiamato, da un timeout che si verifica o da un altro errore.</span><span class="sxs-lookup"><span data-stu-id="ff533-178">This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.</span></span>

<span data-ttu-id="ff533-179">Prima di tutto, sottoscrivere l'evento DictationComplete:</span><span class="sxs-lookup"><span data-stu-id="ff533-179">First, subscribe to the DictationComplete event:</span></span>

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

<span data-ttu-id="ff533-180">Gestire quindi il callback di DictationComplete:</span><span class="sxs-lookup"><span data-stu-id="ff533-180">Then handle the DictationComplete callback:</span></span>

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

<span data-ttu-id="ff533-181">**DictationError**</span><span class="sxs-lookup"><span data-stu-id="ff533-181">**DictationError**</span></span>

<span data-ttu-id="ff533-182">Questo evento viene generato quando si verifica un errore.</span><span class="sxs-lookup"><span data-stu-id="ff533-182">This event is fired when an error occurs.</span></span>

<span data-ttu-id="ff533-183">Prima di tutto, sottoscrivere l'evento DictationError:</span><span class="sxs-lookup"><span data-stu-id="ff533-183">First, subscribe to the DictationError event:</span></span>

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

<span data-ttu-id="ff533-184">Gestire quindi il callback di DictationError:</span><span class="sxs-lookup"><span data-stu-id="ff533-184">Then handle the DictationError callback:</span></span>

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

<span data-ttu-id="ff533-185">Dopo aver sottoscritto e gestito gli eventi di dettatura di cui si è interessati, avviare il riconoscimento della dettatura per iniziare a ricevere gli eventi.</span><span class="sxs-lookup"><span data-stu-id="ff533-185">Once you have subscribed and handled the dictation events that you care about, start the dictation recognizer to begin receiving events.</span></span>

```
dictationRecognizer.Start();
```

<span data-ttu-id="ff533-186">Se non si desidera più proteggere il DictationRecognizer, è necessario annullare la sottoscrizione agli eventi ed eliminare il DictationRecognizer.</span><span class="sxs-lookup"><span data-stu-id="ff533-186">If you no longer want to keep the DictationRecognizer around, you need to unsubscribe from the events and Dispose the DictationRecognizer.</span></span>

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

<span data-ttu-id="ff533-187">**Consigli**</span><span class="sxs-lookup"><span data-stu-id="ff533-187">**Tips**</span></span>
* <span data-ttu-id="ff533-188">I metodi Start () e stop () rispettivamente abilitano e disabilitano il riconoscimento della dettatura.</span><span class="sxs-lookup"><span data-stu-id="ff533-188">Start() and Stop() methods respectively enable and disable dictation recognition.</span></span>
* <span data-ttu-id="ff533-189">Una volta terminato con il riconoscimento, è necessario eliminarlo utilizzando il metodo Dispose () per rilasciare le risorse utilizzate.</span><span class="sxs-lookup"><span data-stu-id="ff533-189">Once done with the recognizer, it must be disposed using Dispose() method to release the resources it uses.</span></span> <span data-ttu-id="ff533-190">Queste risorse verranno rilasciate automaticamente durante Garbage Collection a un costo aggiuntivo in termini di prestazioni, se non vengono rilasciate prima di tale operazione.</span><span class="sxs-lookup"><span data-stu-id="ff533-190">It will release these resources automatically during garbage collection at an additional performance cost if they are not released prior to that.</span></span>
* <span data-ttu-id="ff533-191">I timeout si verificano dopo un determinato periodo di tempo.</span><span class="sxs-lookup"><span data-stu-id="ff533-191">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="ff533-192">È possibile verificare questi timeout nell'evento DictationComplete.</span><span class="sxs-lookup"><span data-stu-id="ff533-192">You can check for these timeouts in the DictationComplete event.</span></span> <span data-ttu-id="ff533-193">È necessario tenere presenti due timeout:</span><span class="sxs-lookup"><span data-stu-id="ff533-193">There are two timeouts to be aware of:</span></span>
   1. <span data-ttu-id="ff533-194">Se il riconoscimento viene avviato e non viene sentito alcun audio per i primi cinque secondi, il timeout verrà attivato.</span><span class="sxs-lookup"><span data-stu-id="ff533-194">If the recognizer starts and doesn't hear any audio for the first five seconds, it will timeout.</span></span>
   2. <span data-ttu-id="ff533-195">Se il riconoscimento ha dato un risultato, ma in seguito viene ascoltato il silenzio per 20 secondi, il timeout verrà completato.</span><span class="sxs-lookup"><span data-stu-id="ff533-195">If the recognizer has given a result but then hears silence for twenty seconds, it will timeout.</span></span>

## <a name="using-both-phrase-recognition-and-dictation"></a><span data-ttu-id="ff533-196">Uso sia del riconoscimento delle frasi che della dettatura</span><span class="sxs-lookup"><span data-stu-id="ff533-196">Using both Phrase Recognition and Dictation</span></span>

<span data-ttu-id="ff533-197">Se si vuole usare sia il riconoscimento delle frasi che la dettatura nell'app, è necessario chiudere completamente una volta prima di poter avviare l'altra.</span><span class="sxs-lookup"><span data-stu-id="ff533-197">If you want to use both phrase recognition and dictation in your app, you'll need to fully shut one down before you can start the other.</span></span> <span data-ttu-id="ff533-198">Se sono in esecuzione più KeywordRecognizers, è possibile arrestarli tutti contemporaneamente con:</span><span class="sxs-lookup"><span data-stu-id="ff533-198">If you have multiple KeywordRecognizers running, you can shut them all down at once with:</span></span>

```
PhraseRecognitionSystem.Shutdown();
```

<span data-ttu-id="ff533-199">Per ripristinare lo stato precedente di tutti i riconoscitori, dopo l'arresto di DictationRecognizer, è possibile chiamare:</span><span class="sxs-lookup"><span data-stu-id="ff533-199">In order to restore all recognizers to their previous state, after the DictationRecognizer has stopped, you can call:</span></span>

```
PhraseRecognitionSystem.Restart();
```

<span data-ttu-id="ff533-200">È anche possibile avviare solo un KeywordRecognizer, che riavvia anche il PhraseRecognitionSystem.</span><span class="sxs-lookup"><span data-stu-id="ff533-200">You could also just start a KeywordRecognizer, which will restart the PhraseRecognitionSystem as well.</span></span>

## <a name="using-the-microphone-helper"></a><span data-ttu-id="ff533-201">Uso dell'helper del microfono</span><span class="sxs-lookup"><span data-stu-id="ff533-201">Using the microphone helper</span></span>

<span data-ttu-id="ff533-202">Il Toolkit di realtà mista in GitHub contiene una classe helper del microfono per suggerire agli sviluppatori se è presente un microfono utilizzabile nel sistema.</span><span class="sxs-lookup"><span data-stu-id="ff533-202">The Mixed Reality Toolkit on GitHub contains a microphone helper class to hint at developers if there is a usable microphone on the system.</span></span> <span data-ttu-id="ff533-203">Uno di questi casi è quello in cui si vuole controllare se è presente un microfono nel sistema prima di visualizzare gli hint di interazione vocale nell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="ff533-203">One use for it is where one would want to check if there is microphone on system before showing any speech interaction hints in the application.</span></span>

<span data-ttu-id="ff533-204">Lo script Helper Microphone è disponibile nella [cartella input/script/Utilities](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs).</span><span class="sxs-lookup"><span data-stu-id="ff533-204">The microphone helper script can be found in the [Input/Scripts/Utilities folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs).</span></span> <span data-ttu-id="ff533-205">Il repository GitHub contiene anche un [piccolo esempio](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) che illustra come usare l'helper.</span><span class="sxs-lookup"><span data-stu-id="ff533-205">The GitHub repo also contains a [small sample](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) demonstrating how to use the helper.</span></span>

## <a name="voice-input-in-mixed-reality-toolkit"></a><span data-ttu-id="ff533-206">Input vocale nel Toolkit per realtà mista</span><span class="sxs-lookup"><span data-stu-id="ff533-206">Voice input in Mixed Reality Toolkit</span></span>
<span data-ttu-id="ff533-207">È possibile trovare gli esempi dell'input vocale in questa scena.</span><span class="sxs-lookup"><span data-stu-id="ff533-207">You can find the examples of the voice input in this scene.</span></span>

- [<span data-ttu-id="ff533-208">HoloToolkit-Examples/input/Scenes/SpeechInputSource. Unity</span><span class="sxs-lookup"><span data-stu-id="ff533-208">HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity)

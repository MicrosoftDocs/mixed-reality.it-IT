---
title: Input vocale in DirectX
description: Viene illustrato come implementare i comandi vocali e il riconoscimento di frasi e frasi brevi in un'app DirectX per la realtà mista di Windows.
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: procedura dettagliata, comando vocale, frase, riconoscimento, sintesi vocale, DirectX, piattaforma, Cortana, realtà mista di Windows
ms.openlocfilehash: 2837a0fc42e8fdebb2e1facee118d20b5668cd43
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277969"
---
# <a name="voice-input-in-directx"></a><span data-ttu-id="620c4-104">Input vocale in DirectX</span><span class="sxs-lookup"><span data-stu-id="620c4-104">Voice input in DirectX</span></span>

<span data-ttu-id="620c4-105">Questo articolo illustra come implementare i [comandi vocali](voice-input.md) e il riconoscimento di frasi brevi e frasi in un'app DirectX per la realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="620c4-105">This article explains how to implement [voice commands](voice-input.md) plus small-phrase and sentence recognition in a DirectX app for Windows Mixed Reality.</span></span>

>[!NOTE]
><span data-ttu-id="620c4-106">I frammenti di codice in questo articolo usano C++/CX anziché/WinRT conforme C++a C + 17, usato nel modello di [ C++ progetto olografico](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="620c4-106">The code snippets in this article use C++/CX rather than C++17-compliant C++/WinRT, which is used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="620c4-107">I concetti sono equivalenti per C++un progetto/WinRT, ma è necessario tradurre il codice.</span><span class="sxs-lookup"><span data-stu-id="620c4-107">The concepts are equivalent for a C++/WinRT project, but you need to translate the code.</span></span>

## <a name="use-speechrecognizer-for-continuous-speech-recognition"></a><span data-ttu-id="620c4-108">Usare SpeechRecognizer per il riconoscimento vocale continuo</span><span class="sxs-lookup"><span data-stu-id="620c4-108">Use SpeechRecognizer for continuous speech recognition</span></span>

<span data-ttu-id="620c4-109">Questa sezione descrive come usare il riconoscimento vocale continuo per abilitare i comandi vocali nell'app.</span><span class="sxs-lookup"><span data-stu-id="620c4-109">This section describes how to use continuous speech recognition to enable voice commands in your app.</span></span> <span data-ttu-id="620c4-110">Questa procedura dettagliata usa il codice dell'esempio [HolographicVoiceInput](https://go.microsoft.com/fwlink/p/?LinkId=844964) .</span><span class="sxs-lookup"><span data-stu-id="620c4-110">This walk-through uses code from the [HolographicVoiceInput](https://go.microsoft.com/fwlink/p/?LinkId=844964) sample.</span></span> <span data-ttu-id="620c4-111">Quando l'esempio è in esecuzione, pronunciare il nome di uno dei comandi colorati registrati per modificare il colore del cubo rotante.</span><span class="sxs-lookup"><span data-stu-id="620c4-111">When the sample is running, speak the name of one of the registered color commands to change the color of the spinning cube.</span></span>

<span data-ttu-id="620c4-112">Per prima cosa, creare una nuova istanza di *Windows:: media:: sintesi vocale:: SpeechRecognizer* .</span><span class="sxs-lookup"><span data-stu-id="620c4-112">First, create a new *Windows::Media::SpeechRecognition::SpeechRecognizer* instance.</span></span>

<span data-ttu-id="620c4-113">Da *HolographicVoiceInputSampleMain:: CreateSpeechConstraintsForCurrentState*:</span><span class="sxs-lookup"><span data-stu-id="620c4-113">From *HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState*:</span></span>

```
m_speechRecognizer = ref new SpeechRecognizer();
```

<span data-ttu-id="620c4-114">Creare un elenco di comandi vocali per il riconoscimento da ascoltare.</span><span class="sxs-lookup"><span data-stu-id="620c4-114">Create a list of speech commands for the recognizer to listen for.</span></span> <span data-ttu-id="620c4-115">Qui viene costruito un set di comandi per modificare il colore di un ologramma.</span><span class="sxs-lookup"><span data-stu-id="620c4-115">Here, we construct a set of commands to change the color of a hologram.</span></span> <span data-ttu-id="620c4-116">Per praticità, vengono creati anche i dati che verranno usati per i comandi in un secondo momento.</span><span class="sxs-lookup"><span data-stu-id="620c4-116">For convenience, we also create the data that we'll use for the commands later.</span></span>

```
m_speechCommandList = ref new Platform::Collections::Vector<String^>();
   m_speechCommandData.clear();
   m_speechCommandList->Append(StringReference(L"white"));
   m_speechCommandData.push_back(float4(1.f, 1.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"grey"));
   m_speechCommandData.push_back(float4(0.5f, 0.5f, 0.5f, 1.f));
   m_speechCommandList->Append(StringReference(L"green"));
   m_speechCommandData.push_back(float4(0.f, 1.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"black"));
   m_speechCommandData.push_back(float4(0.1f, 0.1f, 0.1f, 1.f));
   m_speechCommandList->Append(StringReference(L"red"));
   m_speechCommandData.push_back(float4(1.f, 0.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"yellow"));
   m_speechCommandData.push_back(float4(1.f, 1.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"aquamarine"));
   m_speechCommandData.push_back(float4(0.f, 1.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"blue"));
   m_speechCommandData.push_back(float4(0.f, 0.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"purple"));
   m_speechCommandData.push_back(float4(1.f, 0.f, 1.f, 1.f));
```

<span data-ttu-id="620c4-117">È possibile usare parole fonetiche che potrebbero non essere presenti in un dizionario per specificare i comandi.</span><span class="sxs-lookup"><span data-stu-id="620c4-117">You can use phonetic words that might not be in a dictionary to specify commands.</span></span>

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

<span data-ttu-id="620c4-118">Per caricare l'elenco di comandi nell'elenco di vincoli per il riconoscimento vocale, usare un oggetto [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) .</span><span class="sxs-lookup"><span data-stu-id="620c4-118">To load the commands list into the list of constraints for the speech recognizer use a [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) object.</span></span>

```
SpeechRecognitionListConstraint^ spConstraint = ref new SpeechRecognitionListConstraint(m_speechCommandList);
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(spConstraint);
   create_task(m_speechRecognizer->CompileConstraintsAsync()).then([this](SpeechRecognitionCompilationResult^ compilationResult)
   {
       if (compilationResult->Status == SpeechRecognitionResultStatus::Success)
       {
           m_speechRecognizer->ContinuousRecognitionSession->StartAsync();
       }
       else
       {
           // Handle errors here.
       }
   });
```

<span data-ttu-id="620c4-119">Sottoscrivere l'evento [ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) sulla [SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx)del riconoscimento vocale.</span><span class="sxs-lookup"><span data-stu-id="620c4-119">Subscribe to the [ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) event on the speech recognizer's [SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx).</span></span> <span data-ttu-id="620c4-120">Questo evento invia una notifica all'app quando uno dei comandi è stato riconosciuto.</span><span class="sxs-lookup"><span data-stu-id="620c4-120">This event notifies your app when one of your commands has been recognized.</span></span>

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

<span data-ttu-id="620c4-121">Il gestore dell'evento *OnResultGenerated* riceve i dati dell'evento in un'istanza di [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) .</span><span class="sxs-lookup"><span data-stu-id="620c4-121">Your *OnResultGenerated* event handler receives event data in a [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) instance.</span></span> <span data-ttu-id="620c4-122">Se la confidenza è maggiore della soglia definita, l'applicazione deve tenere presente che si è verificato l'evento.</span><span class="sxs-lookup"><span data-stu-id="620c4-122">If the confidence is greater than the threshold that you defined, your app should note that the event happened.</span></span> <span data-ttu-id="620c4-123">Salvare i dati dell'evento in modo che sia possibile utilizzarli in un ciclo di aggiornamento successivo.</span><span class="sxs-lookup"><span data-stu-id="620c4-123">Save the event data so that you can use it in a subsequent update loop.</span></span>

<span data-ttu-id="620c4-124">Da *HolographicVoiceInputSampleMain. cpp*:</span><span class="sxs-lookup"><span data-stu-id="620c4-124">From *HolographicVoiceInputSampleMain.cpp*:</span></span>

```
// Change the cube color, if we get a valid result.
   void HolographicVoiceInputSampleMain::OnResultGenerated(SpeechContinuousRecognitionSession ^sender, SpeechContinuousRecognitionResultGeneratedEventArgs ^args)
   {
       if (args->Result->RawConfidence > 0.5f)
       {
           m_lastCommand = args->Result->Text;
       }
   }
```

<span data-ttu-id="620c4-125">Nel codice di esempio, viene modificato il colore del cubo dell'ologramma rotante in base al comando dell'utente.</span><span class="sxs-lookup"><span data-stu-id="620c4-125">In our example code, we change the color of the spinning hologram cube according to the user's command.</span></span>

<span data-ttu-id="620c4-126">Da *HolographicVoiceInputSampleMain:: Update*:</span><span class="sxs-lookup"><span data-stu-id="620c4-126">From *HolographicVoiceInputSampleMain::Update*:</span></span>

```
// Check for new speech input since the last frame.
   if (m_lastCommand != nullptr)
   {
       auto command = m_lastCommand;
       m_lastCommand = nullptr;

       int i = 0;
       for each (auto& iter in m_speechCommandList)
       {
           if (iter == command)
           {
               m_spinningCubeRenderer->SetColor(m_speechCommandData[i]);
               break;
           }

           ++i;
       }
   }
```

## <a name="use-one-shot-recognition"></a><span data-ttu-id="620c4-127">Usa il riconoscimento "One-Shot"</span><span class="sxs-lookup"><span data-stu-id="620c4-127">Use "one-shot" recognition</span></span>

<span data-ttu-id="620c4-128">È possibile configurare un riconoscimento vocale per ascoltare frasi o frasi pronunciate dall'utente.</span><span class="sxs-lookup"><span data-stu-id="620c4-128">You can configure a speech recognizer to listen for phrases or sentences that the user speaks.</span></span> <span data-ttu-id="620c4-129">In questo caso, viene applicato un *SpeechRecognitionTopicConstraint* che indica al riconoscimento vocale il tipo di input previsto.</span><span class="sxs-lookup"><span data-stu-id="620c4-129">In this case, we apply a *SpeechRecognitionTopicConstraint* that tells the speech recognizer what type of input to expect.</span></span> <span data-ttu-id="620c4-130">Ecco un flusso di lavoro dell'app per questo scenario:</span><span class="sxs-lookup"><span data-stu-id="620c4-130">Here's an app workflow for this scenario:</span></span>
1. <span data-ttu-id="620c4-131">L'app crea il SpeechRecognizer, fornisce prompt dell'interfaccia utente e inizia l'ascolto di un comando parlato.</span><span class="sxs-lookup"><span data-stu-id="620c4-131">Your app creates the SpeechRecognizer, provides UI prompts, and starts listening for a spoken command.</span></span>
2. <span data-ttu-id="620c4-132">L'utente pronuncia una frase o una frase.</span><span class="sxs-lookup"><span data-stu-id="620c4-132">The user speaks a phrase or sentence.</span></span>
3. <span data-ttu-id="620c4-133">Il riconoscimento della voce dell'utente si verifica e viene restituito un risultato all'app.</span><span class="sxs-lookup"><span data-stu-id="620c4-133">Recognition of the user's speech occurs, and a result is returned to the app.</span></span> <span data-ttu-id="620c4-134">A questo punto, l'app deve fornire un prompt dell'interfaccia utente per indicare che si è verificato il riconoscimento.</span><span class="sxs-lookup"><span data-stu-id="620c4-134">At this point, your app should provide a UI prompt to indicate that recognition has occurred.</span></span>
4. <span data-ttu-id="620c4-135">A seconda del livello di confidenza a cui si desidera rispondere e del livello di confidenza del risultato del riconoscimento vocale, l'app può elaborare il risultato e rispondere nel modo appropriato.</span><span class="sxs-lookup"><span data-stu-id="620c4-135">Depending on the confidence level that you want to respond to and the confidence level of the speech recognition result, your app can process the result and respond as appropriate.</span></span>

<span data-ttu-id="620c4-136">Questa sezione descrive come creare un SpeechRecognizer, compilare il vincolo e restare in ascolto dell'input vocale.</span><span class="sxs-lookup"><span data-stu-id="620c4-136">This section describes how to create a SpeechRecognizer, compile the constraint, and listen for speech input.</span></span>

<span data-ttu-id="620c4-137">Il codice seguente compila il vincolo dell'argomento, che in questo caso è ottimizzato per la ricerca Web.</span><span class="sxs-lookup"><span data-stu-id="620c4-137">The following code compiles the topic constraint, which in this case is optimized for web search.</span></span>

```
auto constraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, L"webSearch");
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(constraint);
   return create_task(m_speechRecognizer->CompileConstraintsAsync())
       .then([this](task<SpeechRecognitionCompilationResult^> previousTask)
   {
```

<span data-ttu-id="620c4-138">Se la compilazione ha esito positivo, è possibile procedere con il riconoscimento vocale.</span><span class="sxs-lookup"><span data-stu-id="620c4-138">If compilation succeeds, we can proceed with speech recognition.</span></span>

```
try
       {
           SpeechRecognitionCompilationResult^ compilationResult = previousTask.get();

           // Check to make sure that the constraints were in a proper format and the recognizer was able to compile it.
           if (compilationResult->Status == SpeechRecognitionResultStatus::Success)
           {
               // If the compilation succeeded, we can start listening for the user's spoken phrase or sentence.
               create_task(m_speechRecognizer->RecognizeAsync()).then([this](task<SpeechRecognitionResult^>& previousTask)
               {
```

<span data-ttu-id="620c4-139">Il risultato viene quindi restituito all'app.</span><span class="sxs-lookup"><span data-stu-id="620c4-139">The result is then returned to the app.</span></span> <span data-ttu-id="620c4-140">Se il risultato è sufficientemente sicuro, è possibile elaborare il comando.</span><span class="sxs-lookup"><span data-stu-id="620c4-140">If we're confident enough in the result, we can process the command.</span></span> <span data-ttu-id="620c4-141">Questo esempio di codice elabora i risultati con almeno una confidenza media.</span><span class="sxs-lookup"><span data-stu-id="620c4-141">This code example processes results with at least medium confidence.</span></span>

```
try
                   {
                       auto result = previousTask.get();

                       if (result->Status != SpeechRecognitionResultStatus::Success)
                       {
                           PrintWstringToDebugConsole(
                               std::wstring(L"Speech recognition was not successful: ") +
                               result->Status.ToString()->Data() +
                               L"\n"
                               );
                       }

                       // In this example, we look for at least medium confidence in the speech result.
                       if ((result->Confidence == SpeechRecognitionConfidence::High) ||
                           (result->Confidence == SpeechRecognitionConfidence::Medium))
                       {
                           // If the user said a color name anywhere in their phrase, it will be recognized in the
                           // Update loop; then, the cube will change color.
                           m_lastCommand = result->Text;

                           PrintWstringToDebugConsole(
                               std::wstring(L"Speech phrase was: ") +
                               m_lastCommand->Data() +
                               L"\n"
                               );
                       }
                       else
                       {
                           PrintWstringToDebugConsole(
                               std::wstring(L"Recognition confidence not high enough: ") +
                               result->Confidence.ToString()->Data() +
                               L"\n"
                               );
                       }
                   }
```

<span data-ttu-id="620c4-142">Quando si usa il riconoscimento vocale, controllare le eccezioni che potrebbero indicare che l'utente ha disattivato il microfono nelle impostazioni relative alla privacy del sistema.</span><span class="sxs-lookup"><span data-stu-id="620c4-142">Whenever you use speech recognition, watch for exceptions that could indicate that the user has turned off the microphone in the system privacy settings.</span></span> <span data-ttu-id="620c4-143">Questo problema può verificarsi durante l'inizializzazione o il riconoscimento.</span><span class="sxs-lookup"><span data-stu-id="620c4-143">This can happen during initialization or recognition.</span></span>

```
catch (Exception^ exception)
                   {
                       // Note that if you get an "Access is denied" exception, you might need to enable the microphone
                       // privacy setting on the device and/or add the microphone capability to your app manifest.

                       PrintWstringToDebugConsole(
                           std::wstring(L"Speech recognizer error: ") +
                           exception->ToString()->Data() +
                           L"\n"
                           );
                   }
               });

               return true;
           }
           else
           {
               OutputDebugStringW(L"Could not initialize predefined grammar speech engine!\n");

               // Handle errors here.
               return false;
           }
       }
       catch (Exception^ exception)
       {
           // Note that if you get an "Access is denied" exception, you might need to enable the microphone
           // privacy setting on the device and/or add the microphone capability to your app manifest.

           PrintWstringToDebugConsole(
               std::wstring(L"Exception while trying to initialize predefined grammar speech engine:") +
               exception->Message->Data() +
               L"\n"
               );

           // Handle exceptions here.
           return false;
       }
   });
```

> [!NOTE]
> <span data-ttu-id="620c4-144">Sono disponibili diversi [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) predefiniti che è possibile usare per ottimizzare il riconoscimento vocale.</span><span class="sxs-lookup"><span data-stu-id="620c4-144">There are several predefined [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) that you can use to optimize speech recognition.</span></span>

* <span data-ttu-id="620c4-145">Per ottimizzare la dettatura, utilizzare lo scenario di dettatura.</span><span class="sxs-lookup"><span data-stu-id="620c4-145">To optimize for dictation, use the dictation scenario.</span></span><br/>
   ```
   // Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
   ```

* <span data-ttu-id="620c4-146">Per le ricerche web vocali, utilizzare il seguente vincolo di scenario specifico per il Web.</span><span class="sxs-lookup"><span data-stu-id="620c4-146">For speech web searches, use the following web-specific scenario constraint.</span></span>

   ```
   // Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
   ```

* <span data-ttu-id="620c4-147">Utilizzare il vincolo form per compilare i moduli.</span><span class="sxs-lookup"><span data-stu-id="620c4-147">Use the form constraint to fill out forms.</span></span> <span data-ttu-id="620c4-148">In questo caso, è preferibile applicare la propria grammatica ottimizzata per compilare il modulo.</span><span class="sxs-lookup"><span data-stu-id="620c4-148">In this case, it's best to apply your own grammar that's optimized for filling out the form.</span></span>

   ```
   // Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
   ```
* <span data-ttu-id="620c4-149">È possibile fornire la propria grammatica nel formato SRGS.</span><span class="sxs-lookup"><span data-stu-id="620c4-149">You can provide your own grammar in the SRGS format.</span></span>

## <a name="use-continuous-recognition"></a><span data-ttu-id="620c4-150">Usa il riconoscimento continuo</span><span class="sxs-lookup"><span data-stu-id="620c4-150">Use continuous recognition</span></span>

<span data-ttu-id="620c4-151">Per lo scenario di dettatura continua, vedere l' [esempio di codice di riconoscimento vocale di Windows 10 UWP](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp).</span><span class="sxs-lookup"><span data-stu-id="620c4-151">For the continuous-dictation scenario, see the [Windows 10 UWP speech code sample](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp).</span></span>

## <a name="handle-quality-degradation"></a><span data-ttu-id="620c4-152">Gestione della riduzione della qualità</span><span class="sxs-lookup"><span data-stu-id="620c4-152">Handle quality degradation</span></span>

<span data-ttu-id="620c4-153">Le condizioni ambientali talvolta interferiscono con il riconoscimento vocale.</span><span class="sxs-lookup"><span data-stu-id="620c4-153">Environmental conditions sometimes interfere with speech recognition.</span></span> <span data-ttu-id="620c4-154">Ad esempio, la stanza potrebbe essere troppo rumorosa o l'utente potrebbe parlare troppo forte.</span><span class="sxs-lookup"><span data-stu-id="620c4-154">For example, the room might be too noisy, or the user might speak too loudly.</span></span> <span data-ttu-id="620c4-155">Quando possibile, l'API riconoscimento vocale fornisce informazioni sulle condizioni che hanno causato la riduzione della qualità.</span><span class="sxs-lookup"><span data-stu-id="620c4-155">Whenever possible, the speech recognition API provides information about the conditions that caused the quality degradation.</span></span> <span data-ttu-id="620c4-156">Queste informazioni vengono inserite nell'app tramite un evento WinRT.</span><span class="sxs-lookup"><span data-stu-id="620c4-156">This information is pushed to your app through a WinRT event.</span></span> <span data-ttu-id="620c4-157">Nell'esempio seguente viene illustrato come sottoscrivere questo evento.</span><span class="sxs-lookup"><span data-stu-id="620c4-157">The following example shows  how to subscribe to this event.</span></span>

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

<span data-ttu-id="620c4-158">Nell'esempio di codice vengono scritte le informazioni sulle condizioni nella console di debug.</span><span class="sxs-lookup"><span data-stu-id="620c4-158">In our code sample, we write the conditions information to the debug console.</span></span> <span data-ttu-id="620c4-159">Un'app potrebbe voler fornire feedback all'utente tramite l'interfaccia utente, la sintesi vocale e un altro metodo.</span><span class="sxs-lookup"><span data-stu-id="620c4-159">An app might want to provide feedback to the user through the UI, speech synthesis, and another method.</span></span> <span data-ttu-id="620c4-160">In alternativa, potrebbe essere necessario comportarsi in modo diverso quando il discorso viene interrotto da una riduzione temporanea della qualità.</span><span class="sxs-lookup"><span data-stu-id="620c4-160">Or it might need to behave differently when speech is interrupted by a temporary reduction in quality.</span></span>

```
void HolographicSpeechPromptSampleMain::OnSpeechQualityDegraded(SpeechRecognizer^ recognizer, SpeechRecognitionQualityDegradingEventArgs^ args)
   {
       switch (args->Problem)
       {
       case SpeechRecognitionAudioProblem::TooFast:
           OutputDebugStringW(L"The user spoke too quickly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooSlow:
           OutputDebugStringW(L"The user spoke too slowly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooQuiet:
           OutputDebugStringW(L"The user spoke too softly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooLoud:
           OutputDebugStringW(L"The user spoke too loudly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooNoisy:
           OutputDebugStringW(L"There is too much noise in the signal.\n");
           break;

       case SpeechRecognitionAudioProblem::NoSignal:
           OutputDebugStringW(L"There is no signal.\n");
           break;

       case SpeechRecognitionAudioProblem::None:
       default:
           OutputDebugStringW(L"An error was reported with no information.\n");
           break;
       }
   }
```

<span data-ttu-id="620c4-161">Se non si usano le classi di riferimento per creare l'app DirectX, è necessario annullare la sottoscrizione all'evento prima di rilasciare o ricreare il riconoscimento vocale.</span><span class="sxs-lookup"><span data-stu-id="620c4-161">If you're not using ref classes to create your DirectX app, you must unsubscribe from the event before you release or recreate your speech recognizer.</span></span> <span data-ttu-id="620c4-162">HolographicSpeechPromptSample dispone di una routine per arrestare il riconoscimento e annullare la sottoscrizione agli eventi.</span><span class="sxs-lookup"><span data-stu-id="620c4-162">The HolographicSpeechPromptSample has a routine to stop recognition and unsubscribe from events.</span></span>

```
Concurrency::task<void> HolographicSpeechPromptSampleMain::StopCurrentRecognizerIfExists()
   {
       return create_task([this]()
       {
           if (m_speechRecognizer != nullptr)
           {
               return create_task(m_speechRecognizer->StopRecognitionAsync()).then([this]()
               {
                   m_speechRecognizer->RecognitionQualityDegrading -= m_speechRecognitionQualityDegradedToken;

                   if (m_speechRecognizer->ContinuousRecognitionSession != nullptr)
                   {
                       m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated -= m_speechRecognizerResultEventToken;
                   }
               });
           }
           else
           {
               return create_task([this]() { m_speechRecognizer = nullptr; });
           }
       });
   }
```

## <a name="use-speech-synthesis-to-provide-audible-prompts"></a><span data-ttu-id="620c4-163">Usare la sintesi vocale per fornire richieste acustiche</span><span class="sxs-lookup"><span data-stu-id="620c4-163">Use speech synthesis to provide audible prompts</span></span>

<span data-ttu-id="620c4-164">Gli esempi di riconoscimento vocale olografico usano la sintesi vocale per fornire istruzioni acustiche all'utente.</span><span class="sxs-lookup"><span data-stu-id="620c4-164">The holographic speech samples use speech synthesis to provide audible instructions to the user.</span></span> <span data-ttu-id="620c4-165">Questa sezione illustra come creare un esempio di voce sintetizzata e riprodurlo con le API HRTF audio.</span><span class="sxs-lookup"><span data-stu-id="620c4-165">This section shows how to create a synthesized voice sample  and then play it back through the HRTF audio APIs.</span></span>

<span data-ttu-id="620c4-166">Quando si richiede l'input di frasi, è necessario fornire le proprie richieste di riconoscimento vocale.</span><span class="sxs-lookup"><span data-stu-id="620c4-166">You should provide your own speech prompts when you request phrase input.</span></span> <span data-ttu-id="620c4-167">I prompt possono anche indicare quando è possibile pronunciare i comandi vocali per uno scenario di riconoscimento continuo.</span><span class="sxs-lookup"><span data-stu-id="620c4-167">Prompts can also help indicate when speech commands can be spoken for a continuous-recognition scenario.</span></span> <span data-ttu-id="620c4-168">Nell'esempio seguente viene illustrato come utilizzare un sintetizzatore vocale a tale scopo.</span><span class="sxs-lookup"><span data-stu-id="620c4-168">The following example demonstrates how to use a speech synthesizer to do this.</span></span> <span data-ttu-id="620c4-169">È anche possibile usare un clip vocale pre-registrato, un'interfaccia utente visiva o un altro indicatore di cosa dire, ad esempio negli scenari in cui la richiesta non è dinamica.</span><span class="sxs-lookup"><span data-stu-id="620c4-169">You could also use a pre-recorded voice clip, a visual UI, or another indicator of what to say, for example in scenarios where the prompt is not dynamic.</span></span>

<span data-ttu-id="620c4-170">Per prima cosa, creare l'oggetto SpeechSynthesizer.</span><span class="sxs-lookup"><span data-stu-id="620c4-170">First, create the SpeechSynthesizer object.</span></span>

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

<span data-ttu-id="620c4-171">È anche necessaria una stringa che includa il testo da sintetizzare.</span><span class="sxs-lookup"><span data-stu-id="620c4-171">You also need a string that includes the text to  synthesize.</span></span>

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

<span data-ttu-id="620c4-172">Il riconoscimento vocale viene sintetizzato in modo asincrono tramite SynthesizeTextToStreamAsync.</span><span class="sxs-lookup"><span data-stu-id="620c4-172">Speech is synthesized asynchronously through SynthesizeTextToStreamAsync.</span></span> <span data-ttu-id="620c4-173">Qui viene avviata un'attività asincrona per sintetizzare il discorso.</span><span class="sxs-lookup"><span data-stu-id="620c4-173">Here, we start an async task to synthesize the speech.</span></span>

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

<span data-ttu-id="620c4-174">La sintesi vocale viene inviata come flusso di byte.</span><span class="sxs-lookup"><span data-stu-id="620c4-174">The speech synthesis is sent as a byte stream.</span></span> <span data-ttu-id="620c4-175">È possibile usare il flusso di byte per inizializzare una voce XAudio2.</span><span class="sxs-lookup"><span data-stu-id="620c4-175">We can use that byte stream to initialize an XAudio2 voice.</span></span> <span data-ttu-id="620c4-176">Per gli esempi di codice olografico, viene riprodotto come effetto audio HRTF.</span><span class="sxs-lookup"><span data-stu-id="620c4-176">For our holographic code samples, we play it back as an HRTF audio effect.</span></span>

```
Windows::Media::SpeechSynthesis::SpeechSynthesisStream^ stream = synthesisStreamTask.get();

           auto hr = m_speechSynthesisSound.Initialize(stream, 0);
           if (SUCCEEDED(hr))
           {
               m_speechSynthesisSound.SetEnvironment(HrtfEnvironment::Small);
               m_speechSynthesisSound.Start();

               // Amount of time to pause after the audio prompt is complete, before listening
               // for speech input.
               static const float bufferTime = 0.15f;

               // Wait until the prompt is done before listening.
               m_secondsUntilSoundIsComplete = m_speechSynthesisSound.GetDuration() + bufferTime;
               m_waitingForSpeechPrompt = true;
           }
       }
```

<span data-ttu-id="620c4-177">Come per il riconoscimento vocale, la sintesi vocale genera un'eccezione se si verifica un errore.</span><span class="sxs-lookup"><span data-stu-id="620c4-177">As with speech recognition, speech synthesis throws an exception if something goes wrong.</span></span>

```
catch (Exception^ exception)
       {
           PrintWstringToDebugConsole(
               std::wstring(L"Exception while trying to synthesize speech: ") +
               exception->Message->Data() +
               L"\n"
               );

           // Handle exceptions here.
       }
   });
```

## <a name="see-also"></a><span data-ttu-id="620c4-178">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="620c4-178">See also</span></span>
* [<span data-ttu-id="620c4-179">Progettazione di app vocali</span><span class="sxs-lookup"><span data-stu-id="620c4-179">Speech app design</span></span>](https://msdn.microsoft.com/library/dn596121.aspx)
* [<span data-ttu-id="620c4-180">Esempio SpeechRecognitionAndSynthesis</span><span class="sxs-lookup"><span data-stu-id="620c4-180">SpeechRecognitionAndSynthesis sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)

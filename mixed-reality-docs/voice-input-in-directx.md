---
title: Input vocale in DirectX
description: Viene illustrato come implementare comandi vocali e il riconoscimento di frase e frase piccole in un'app DirectX per realtà mista di Windows.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: procedura dettagliata, comandi vocali, frase, riconoscimento, riconoscimento vocale, directx, piattaforma, cortana, realtà mista di windows
ms.openlocfilehash: 728457a495616e5f65ec3986dfb6ac60231f9e46
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605100"
---
# <a name="voice-input-in-directx"></a><span data-ttu-id="a9d16-104">Input vocale in DirectX</span><span class="sxs-lookup"><span data-stu-id="a9d16-104">Voice input in DirectX</span></span>

<span data-ttu-id="a9d16-105">In questo argomento viene illustrato come implementare [comandi vocali](voice-input.md), piccola frase e frase riconoscimento e in un'app DirectX per realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="a9d16-105">This topic explains how to implement [voice commands](voice-input.md), and small phrase and sentence recognition in a DirectX app for Windows Mixed Reality.</span></span>

>[!NOTE]
><span data-ttu-id="a9d16-106">I frammenti di codice in questo articolo illustrano attualmente l'utilizzo di C++/CX invece di C + + 17 conformi C++/WinRT usato nel [ C++ modello di progetto holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="a9d16-106">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="a9d16-107">I concetti sono equivalenti per un C++progetto /WinRT, anche se è necessario convertire il codice.</span><span class="sxs-lookup"><span data-stu-id="a9d16-107">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="use-a-speechrecognizer-for-continuous-recognition-of-voice-commands"></a><span data-ttu-id="a9d16-108">Usare un SpeechRecognizer per il riconoscimento continuo dei comandi vocali</span><span class="sxs-lookup"><span data-stu-id="a9d16-108">Use a SpeechRecognizer for continuous recognition of voice commands</span></span>

<span data-ttu-id="a9d16-109">In questa sezione viene descritto come utilizzare riconoscimento vocale continua per abilitare i comandi vocali nell'app.</span><span class="sxs-lookup"><span data-stu-id="a9d16-109">In this section, we describe how to use continuous speech recognition to enable voice commands in your app.</span></span> <span data-ttu-id="a9d16-110">Questa procedura dettagliata Usa codice dal [HolographicVoiceInput](http://go.microsoft.com/fwlink/p/?LinkId=844964) esempio.</span><span class="sxs-lookup"><span data-stu-id="a9d16-110">This walkthrough uses code from the [HolographicVoiceInput](http://go.microsoft.com/fwlink/p/?LinkId=844964) Sample.</span></span> <span data-ttu-id="a9d16-111">Quando viene eseguito il codice di esempio, pronunciare il nome di uno dei comandi per modificare il colore del cubo rotante colore registrati.</span><span class="sxs-lookup"><span data-stu-id="a9d16-111">When the sample is running, speak the name of one of the registered color commands to change the color of the spinning cube.</span></span>

<span data-ttu-id="a9d16-112">In primo luogo, creare una nuova **Windows::Media::SpeechRecognition::SpeechRecognizer** istanza.</span><span class="sxs-lookup"><span data-stu-id="a9d16-112">First, create a new **Windows::Media::SpeechRecognition::SpeechRecognizer** instance.</span></span>

<span data-ttu-id="a9d16-113">Dal *HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState*:</span><span class="sxs-lookup"><span data-stu-id="a9d16-113">From *HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState*:</span></span>

```
m_speechRecognizer = ref new SpeechRecognizer();
```

<span data-ttu-id="a9d16-114">È necessario creare un elenco di comandi vocali per rimanere in ascolto per il riconoscimento.</span><span class="sxs-lookup"><span data-stu-id="a9d16-114">You'll need to create a list of speech commands for the recognizer to listen for.</span></span> <span data-ttu-id="a9d16-115">In questo caso, si crea un set di comandi per modificare il colore di ologramma.</span><span class="sxs-lookup"><span data-stu-id="a9d16-115">Here, we construct a set of commands to change the color of a hologram.</span></span> <span data-ttu-id="a9d16-116">Per maggiore praticità, si crea anche i dati che verranno utilizzate per i comandi in un secondo momento.</span><span class="sxs-lookup"><span data-stu-id="a9d16-116">For the sake of convenience, we also create the data that we'll use for the commands later on.</span></span>

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

<span data-ttu-id="a9d16-117">I comandi possono essere specificati utilizzando fonetiche parole che non sia in un dizionario:</span><span class="sxs-lookup"><span data-stu-id="a9d16-117">Commands can be specified using phonetic words that might not be in a dictionary:</span></span>

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

<span data-ttu-id="a9d16-118">L'elenco dei comandi viene caricato nell'elenco di vincoli per il riconoscimento vocale.</span><span class="sxs-lookup"><span data-stu-id="a9d16-118">The list of commands is loaded into the list of constraints for the speech recognizer.</span></span> <span data-ttu-id="a9d16-119">Questa operazione viene eseguita usando un [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) oggetto.</span><span class="sxs-lookup"><span data-stu-id="a9d16-119">This is done by using a [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) object.</span></span>

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

<span data-ttu-id="a9d16-120">Sottoscrivere il [ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) evento su del riconoscimento vocale [SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx).</span><span class="sxs-lookup"><span data-stu-id="a9d16-120">Subscribe to the [ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) event on the speech recognizer's [SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx).</span></span> <span data-ttu-id="a9d16-121">Questo evento di notifica all'app quando uno dei comandi è stato riconosciuto.</span><span class="sxs-lookup"><span data-stu-id="a9d16-121">This event notifies your app when one of your commands has been recognized.</span></span>

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

<span data-ttu-id="a9d16-122">I **OnResultGenerated** gestore eventi riceve i dati di evento in un [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) istanza.</span><span class="sxs-lookup"><span data-stu-id="a9d16-122">Your **OnResultGenerated** event handler receives event data in a [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) instance.</span></span> <span data-ttu-id="a9d16-123">Se il livello di confidenza è maggiore della soglia che è stata definita, l'app deve tenere presente che si è verificato l'evento.</span><span class="sxs-lookup"><span data-stu-id="a9d16-123">If the confidence is greater than the threshold you have defined, your app should note that the event happened.</span></span> <span data-ttu-id="a9d16-124">Salvare i dati dell'evento in modo da poter apportare uso in un ciclo di aggiornamento successivo.</span><span class="sxs-lookup"><span data-stu-id="a9d16-124">Save the event data so that you can make use of it in a subsequent update loop.</span></span>

<span data-ttu-id="a9d16-125">Dal *HolographicVoiceInputSampleMain.cpp*:</span><span class="sxs-lookup"><span data-stu-id="a9d16-125">From *HolographicVoiceInputSampleMain.cpp*:</span></span>

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

<span data-ttu-id="a9d16-126">Rendere uso dei dati, tuttavia applicabili al proprio scenario di app.</span><span class="sxs-lookup"><span data-stu-id="a9d16-126">Make use of the data however applicable to your app scenario.</span></span> <span data-ttu-id="a9d16-127">Nel nostro codice di esempio, è modificare il colore del cubo rotante ologrammi in base al comando dell'utente.</span><span class="sxs-lookup"><span data-stu-id="a9d16-127">In our example code, we change the color of the spinning hologram cube according to the user's command.</span></span>

<span data-ttu-id="a9d16-128">Dal *HolographicVoiceInputSampleMain::Update*:</span><span class="sxs-lookup"><span data-stu-id="a9d16-128">From *HolographicVoiceInputSampleMain::Update*:</span></span>

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

## <a name="use-dictation-for-one-shot-recognition-of-speech-phrases-and-sentences"></a><span data-ttu-id="a9d16-129">Usare la dettatura per il riconoscimento monofase di frasi e frasi</span><span class="sxs-lookup"><span data-stu-id="a9d16-129">Use dictation for one-shot recognition of speech phrases and sentences</span></span>

<span data-ttu-id="a9d16-130">È possibile configurare un sistema di riconoscimento vocale per l'ascolto delle frasi o le frasi pronunciate dall'utente.</span><span class="sxs-lookup"><span data-stu-id="a9d16-130">You can configure a speech recognizer to listen for phrases or sentences spoken by the user.</span></span> <span data-ttu-id="a9d16-131">In questo caso, viene applicato un SpeechRecognitionTopicConstraint che indica il tipo di input per prevedere il riconoscimento vocale.</span><span class="sxs-lookup"><span data-stu-id="a9d16-131">In this case, we apply a SpeechRecognitionTopicConstraint that tells the speech recognizer what type of input to expect.</span></span> <span data-ttu-id="a9d16-132">Il flusso di lavoro di app è come indicato di seguito, per questo tipo di caso d'uso:</span><span class="sxs-lookup"><span data-stu-id="a9d16-132">The app workflow is as follows, for this type of use case:</span></span>
1. <span data-ttu-id="a9d16-133">L'app viene creata la SpeechRecognizer fornisce prompt dell'interfaccia utente e avvia l'ascolto di un comando da risolvere immediatamente.</span><span class="sxs-lookup"><span data-stu-id="a9d16-133">Your app creates the SpeechRecognizer, provides UI prompts, and starts listening for a command to be spoken immediately.</span></span>
2. <span data-ttu-id="a9d16-134">L'utente pronuncia una frase o una frase.</span><span class="sxs-lookup"><span data-stu-id="a9d16-134">The user speaks a phrase, or sentence.</span></span>
3. <span data-ttu-id="a9d16-135">Riconoscimento vocale dell'utente viene eseguito e viene restituito un risultato per l'app.</span><span class="sxs-lookup"><span data-stu-id="a9d16-135">Recognition of the user's speech is performed, and a result is returned to the app.</span></span> <span data-ttu-id="a9d16-136">A questo punto, l'app deve fornire un prompt dei comandi dell'interfaccia utente che indica che si è verificato un riconoscimento.</span><span class="sxs-lookup"><span data-stu-id="a9d16-136">At this point, your app should provide a UI prompt indicating that recognition has occurred.</span></span>
4. <span data-ttu-id="a9d16-137">A seconda del livello di confidenza per rispondere a e il livello di confidenza del risultato del riconoscimento vocale, l'app può elaborare il risultato e correttivo appropriato.</span><span class="sxs-lookup"><span data-stu-id="a9d16-137">Depending on the confidence level you want to respond to and the confidence level of the speech recognition result, your app can process the result and respond as appropriate.</span></span>

<span data-ttu-id="a9d16-138">In questa sezione viene descritto come creare un SpeechRecognizer, compilare il vincolo e restare in attesa per l'input vocale.</span><span class="sxs-lookup"><span data-stu-id="a9d16-138">This section describes how to create a SpeechRecognizer, compile the constraint, and listen for speech input.</span></span>

<span data-ttu-id="a9d16-139">Il codice seguente compila il vincolo di argomento, che in questo caso è ottimizzato per la ricerca sul Web.</span><span class="sxs-lookup"><span data-stu-id="a9d16-139">The following code compiles the topic constraint, which in this case is optimized for Web search.</span></span>

```
auto constraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, L"webSearch");
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(constraint);
   return create_task(m_speechRecognizer->CompileConstraintsAsync())
       .then([this](task<SpeechRecognitionCompilationResult^> previousTask)
   {
```

<span data-ttu-id="a9d16-140">Se la compilazione ha esito positivo, è possibile procedere con il riconoscimento vocale.</span><span class="sxs-lookup"><span data-stu-id="a9d16-140">If compilation succeeds, we can proceed with speech recognition.</span></span>

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

<span data-ttu-id="a9d16-141">Il risultato viene quindi restituito all'app.</span><span class="sxs-lookup"><span data-stu-id="a9d16-141">The result is then returned to the app.</span></span> <span data-ttu-id="a9d16-142">Se si sono sufficientemente sicuri nel risultato, è possibile elaborare il comando.</span><span class="sxs-lookup"><span data-stu-id="a9d16-142">If we are confident enough in the result, we can process the command.</span></span> <span data-ttu-id="a9d16-143">Questo esempio di codice elabora i risultati in tutta sicurezza almeno su medio.</span><span class="sxs-lookup"><span data-stu-id="a9d16-143">This code example processes results with at least Medium confidence.</span></span>

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

<span data-ttu-id="a9d16-144">Quando si usa il riconoscimento vocale, è opportuno considerare attentamente per le eccezioni che potrebbero indicare che l'utente ha disattivato il microfono nelle impostazioni di privacy del sistema.</span><span class="sxs-lookup"><span data-stu-id="a9d16-144">Whenever you use speech recognition, you should watch for exceptions that could indicate the user has turned off the microphone in the system privacy settings.</span></span> <span data-ttu-id="a9d16-145">Questa situazione può verificarsi durante l'inizializzazione o durante il riconoscimento.</span><span class="sxs-lookup"><span data-stu-id="a9d16-145">This can happen during initialization, or during recognition.</span></span>

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

<span data-ttu-id="a9d16-146">**NOTA:** Esistono diverse predefiniti [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) disponibili per l'ottimizzazione di riconoscimento vocale.</span><span class="sxs-lookup"><span data-stu-id="a9d16-146">**NOTE:** There are several predefined [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) available for optimizing speech recognition.</span></span>
* <span data-ttu-id="a9d16-147">Se si desidera ottimizzare per la dettatura, usare lo scenario di dettatura:</span><span class="sxs-lookup"><span data-stu-id="a9d16-147">If you want to optimize for dictation, use the Dictation scenario:</span></span>

```
// Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
```
* <span data-ttu-id="a9d16-148">Quando si utilizza riconoscimento vocale per eseguire una ricerca sul Web, è possibile usare un vincolo di scenario specifici Web come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="a9d16-148">When using speech to perform a Web search, you can use a Web-specific scenario constraint as follows:</span></span>

```
// Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
```
* <span data-ttu-id="a9d16-149">Usare il vincolo di form per compilare i moduli.</span><span class="sxs-lookup"><span data-stu-id="a9d16-149">Use the form constraint to fill out forms.</span></span> <span data-ttu-id="a9d16-150">In questo caso, si consiglia di applicare il proprio grammatica ottimizzata per la compilazione del modulo.</span><span class="sxs-lookup"><span data-stu-id="a9d16-150">In this case, it is best to apply your own grammar that is optimized for filling out your form.</span></span>

```
// Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
```
* <span data-ttu-id="a9d16-151">È possibile fornire il proprio Grammatica SRGS nel formato.</span><span class="sxs-lookup"><span data-stu-id="a9d16-151">You can provide your own grammar using the SRGS format.</span></span>

## <a name="use-continuous-freeform-speech-dictation"></a><span data-ttu-id="a9d16-152">Usare dettatura continua a mano libera</span><span class="sxs-lookup"><span data-stu-id="a9d16-152">Use continuous, freeform speech dictation</span></span>

<span data-ttu-id="a9d16-153">Vedere l'esempio di codice UWP di Windows 10 vocale per lo scenario di dettatura continua [qui.](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)</span><span class="sxs-lookup"><span data-stu-id="a9d16-153">See the Windows 10 UWP speech code sample for the continuous dictation scenario [here.](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)</span></span>

## <a name="handle-degradation-in-quality"></a><span data-ttu-id="a9d16-154">Gestire una riduzione delle qualità</span><span class="sxs-lookup"><span data-stu-id="a9d16-154">Handle degradation in quality</span></span>

<span data-ttu-id="a9d16-155">Le condizioni nell'ambiente possono a volte impediscono il riconoscimento vocale funzionamento.</span><span class="sxs-lookup"><span data-stu-id="a9d16-155">Conditions in the environment can sometimes prevent speech recognition from working.</span></span> <span data-ttu-id="a9d16-156">Ad esempio, potrebbe essere troppo disturbata chat room oppure l'utente può pronunciare a un volume troppo elevato.</span><span class="sxs-lookup"><span data-stu-id="a9d16-156">For example, the room might be too noisy or the user might speak at too high a volume.</span></span> <span data-ttu-id="a9d16-157">L'API riconoscimento vocale fornisce info, laddove possibile, informazioni sulle condizioni che hanno causato una riduzione delle prestazioni di qualità.</span><span class="sxs-lookup"><span data-stu-id="a9d16-157">The speech recognition API provides info, where possible, about conditions that have caused a degradation in quality.</span></span>

<span data-ttu-id="a9d16-158">Queste informazioni viene eseguito il push all'App usando un evento di WinRT.</span><span class="sxs-lookup"><span data-stu-id="a9d16-158">This information is pushed to your app using a WinRT event.</span></span> <span data-ttu-id="a9d16-159">Ecco un esempio di come sottoscrivere questo evento.</span><span class="sxs-lookup"><span data-stu-id="a9d16-159">Here is an example of how to subscribe to this event.</span></span>

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

<span data-ttu-id="a9d16-160">In questo esempio di codice, si sceglie di scrivere le informazioni di condizioni nella console di debug.</span><span class="sxs-lookup"><span data-stu-id="a9d16-160">In our code sample, we choose to write the conditions info to the debug console.</span></span> <span data-ttu-id="a9d16-161">Un'app potrebbe essere necessario fornire commenti e suggerimenti per l'utente attraverso l'interfaccia utente, sintesi vocale e così via, o potrebbe essere necessario un comportamento diverso quando vocale verrà interrotto da una temporanea riduzione della qualità.</span><span class="sxs-lookup"><span data-stu-id="a9d16-161">An app might want to provide feedback to the user via UI, speech synthesis, and so on, or it might need to behave differently when speech is interrupted by a temporary reduction in quality.</span></span>

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

<span data-ttu-id="a9d16-162">Se non si usa le classi di riferimento per creare l'app DirectX, è necessario annullare la sottoscrizione dall'evento prima di ricreare il riconoscimento vocale o di rilascio.</span><span class="sxs-lookup"><span data-stu-id="a9d16-162">If you are not using ref classes to create your DirectX app, you must unsubscribe from the event before releasing or recreating your speech recognizer.</span></span> <span data-ttu-id="a9d16-163">Il HolographicSpeechPromptSample dispone di una routine per arrestare il riconoscimento e la sottoscrizione di eventi come segue:</span><span class="sxs-lookup"><span data-stu-id="a9d16-163">The HolographicSpeechPromptSample has a routine to stop recognition, and unsubscribe from events like so:</span></span>

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

## <a name="use-speech-synthesis-to-provide-audible-voice-prompts"></a><span data-ttu-id="a9d16-164">Usare la sintesi vocale per fornire istruzioni vocali acustici</span><span class="sxs-lookup"><span data-stu-id="a9d16-164">Use speech synthesis to provide audible voice prompts</span></span>

<span data-ttu-id="a9d16-165">Gli esempi di riconoscimento vocale holographic utilizzano sintesi vocale per fornire istruzioni acustici all'utente.</span><span class="sxs-lookup"><span data-stu-id="a9d16-165">The holographic speech samples use speech synthesis to provide audible instructions to the user.</span></span> <span data-ttu-id="a9d16-166">In questo argomento descrive il processo di creazione di un esempio di voce sintetizzata e riprodurlo usando le API audio HRTF.</span><span class="sxs-lookup"><span data-stu-id="a9d16-166">This topic walks through the process of creating a synthesized voice sample, and playing it back using the HRTF audio APIs.</span></span>

<span data-ttu-id="a9d16-167">È necessario fornire che il proprio riconoscimento vocale richiesto la richiesta di input di una frase.</span><span class="sxs-lookup"><span data-stu-id="a9d16-167">You should provide your own speech prompts when requesting phrase input.</span></span> <span data-ttu-id="a9d16-168">Anche questo può essere utile per indicare quando i comandi di riconoscimento vocale possono essere pronunciati, per uno scenario di riconoscimento continuo.</span><span class="sxs-lookup"><span data-stu-id="a9d16-168">This can also be helpful for indicating when speech commands can be spoken, for a continuous recognition scenario.</span></span> <span data-ttu-id="a9d16-169">Ecco un esempio di come eseguire questa operazione con un sintetizzatore vocale; Si noti che è possibile usare anche un messaggio vocale preregistrati, un'interfaccia utente visual o un altro indicatore di ciò che occorre ad esempio, ad esempio in scenari in cui la richiesta non è dinamica.</span><span class="sxs-lookup"><span data-stu-id="a9d16-169">Here is an example of how to do that with a speech synthesizer; note that you could also use a pre-recorded voice clip, a visual UI, or other indicator of what to say, for example in scenarios where the prompt is not dynamic.</span></span>

<span data-ttu-id="a9d16-170">In primo luogo, creare l'oggetto SpeechSynthesizer:</span><span class="sxs-lookup"><span data-stu-id="a9d16-170">First, create the SpeechSynthesizer object:</span></span>

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

<span data-ttu-id="a9d16-171">È anche necessaria una stringa con il testo da sottoporre:</span><span class="sxs-lookup"><span data-stu-id="a9d16-171">You also need a string with the text to be synthesized:</span></span>

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

<span data-ttu-id="a9d16-172">Riconoscimento vocale è sintetizzati in modo asincrono usando SynthesizeTextToStreamAsync.</span><span class="sxs-lookup"><span data-stu-id="a9d16-172">Speech is synthesized asynchronously using SynthesizeTextToStreamAsync.</span></span> <span data-ttu-id="a9d16-173">In questo caso, abbiamo avviato un'attività asincrona per sintetizzare il riconoscimento vocale.</span><span class="sxs-lookup"><span data-stu-id="a9d16-173">Here, we kick off an async task to synthesize the speech.</span></span>

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

<span data-ttu-id="a9d16-174">La sintesi vocale viene inviata come flusso di byte.</span><span class="sxs-lookup"><span data-stu-id="a9d16-174">The speech synthesis is sent as a byte stream.</span></span> <span data-ttu-id="a9d16-175">È possibile inizializzare una voce XAudio2 usando tale flusso di byte; per gli esempi di codice holographic, abbiamo riprodurlo effetto HRTF audio.</span><span class="sxs-lookup"><span data-stu-id="a9d16-175">We can initialize an XAudio2 voice using that byte stream; for our holographic code samples, we play it back as an HRTF audio effect.</span></span>

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

<span data-ttu-id="a9d16-176">Come con il riconoscimento vocale, sintesi vocale genererà un'eccezione se si verificano problemi.</span><span class="sxs-lookup"><span data-stu-id="a9d16-176">As with speech recognition, speech synthesis will throw an exception if something goes wrong.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a9d16-177">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a9d16-177">See also</span></span>
* [<span data-ttu-id="a9d16-178">Progettazione di app di riconoscimento vocale</span><span class="sxs-lookup"><span data-stu-id="a9d16-178">Speech app design</span></span>](https://msdn.microsoft.com/library/dn596121.aspx)
* [<span data-ttu-id="a9d16-179">Audio spaziale in DirectX</span><span class="sxs-lookup"><span data-stu-id="a9d16-179">Spatial sound in DirectX</span></span>](spatial-sound-in-directx.md)
* [<span data-ttu-id="a9d16-180">Esempio SpeechRecognitionAndSynthesis</span><span class="sxs-lookup"><span data-stu-id="a9d16-180">SpeechRecognitionAndSynthesis sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)
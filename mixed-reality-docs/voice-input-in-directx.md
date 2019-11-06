---
title: Input vocale in DirectX
description: Viene illustrato come implementare i comandi vocali e il riconoscimento di frasi e frasi brevi in un'app DirectX per la realtà mista di Windows.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: procedura dettagliata, comando vocale, frase, riconoscimento, sintesi vocale, DirectX, piattaforma, Cortana, realtà mista di Windows
ms.openlocfilehash: 0dcfaae13f763c9b8a06910f11558d2fd8e00276
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641083"
---
# <a name="voice-input-in-directx"></a><span data-ttu-id="9bcc8-104">Input vocale in DirectX</span><span class="sxs-lookup"><span data-stu-id="9bcc8-104">Voice input in DirectX</span></span>

<span data-ttu-id="9bcc8-105">Questo argomento illustra come implementare i [comandi vocali](voice-input.md)e il riconoscimento di frasi e frasi brevi in un'app DirectX per la realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-105">This topic explains how to implement [voice commands](voice-input.md), and small phrase and sentence recognition in a DirectX app for Windows Mixed Reality.</span></span>

>[!NOTE]
><span data-ttu-id="9bcc8-106">I frammenti di codice in questo articolo illustrano attualmente l' C++uso di/CX, invece di/WinRT conformi C++a C + 17 come usato nel modello di [ C++ progetto olografico](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="9bcc8-106">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="9bcc8-107">I concetti sono equivalenti per C++un progetto/WinRT, anche se sarà necessario tradurre il codice.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-107">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="use-a-speechrecognizer-for-continuous-recognition-of-voice-commands"></a><span data-ttu-id="9bcc8-108">Usare un SpeechRecognizer per il riconoscimento continuo dei comandi vocali</span><span class="sxs-lookup"><span data-stu-id="9bcc8-108">Use a SpeechRecognizer for continuous recognition of voice commands</span></span>

<span data-ttu-id="9bcc8-109">In questa sezione viene descritto come usare il riconoscimento vocale continuo per abilitare i comandi vocali nell'app.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-109">In this section, we describe how to use continuous speech recognition to enable voice commands in your app.</span></span> <span data-ttu-id="9bcc8-110">Questa procedura dettagliata usa il codice dell'esempio [HolographicVoiceInput](https://go.microsoft.com/fwlink/p/?LinkId=844964) .</span><span class="sxs-lookup"><span data-stu-id="9bcc8-110">This walkthrough uses code from the [HolographicVoiceInput](https://go.microsoft.com/fwlink/p/?LinkId=844964) Sample.</span></span> <span data-ttu-id="9bcc8-111">Quando l'esempio è in esecuzione, pronunciare il nome di uno dei comandi colorati registrati per modificare il colore del cubo rotante.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-111">When the sample is running, speak the name of one of the registered color commands to change the color of the spinning cube.</span></span>

<span data-ttu-id="9bcc8-112">Per prima cosa, creare una nuova istanza di **Windows:: media:: sintesi vocale:: SpeechRecognizer** .</span><span class="sxs-lookup"><span data-stu-id="9bcc8-112">First, create a new **Windows::Media::SpeechRecognition::SpeechRecognizer** instance.</span></span>

<span data-ttu-id="9bcc8-113">Da *HolographicVoiceInputSampleMain:: CreateSpeechConstraintsForCurrentState*:</span><span class="sxs-lookup"><span data-stu-id="9bcc8-113">From *HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState*:</span></span>

```
m_speechRecognizer = ref new SpeechRecognizer();
```

<span data-ttu-id="9bcc8-114">È necessario creare un elenco di comandi vocali per il riconoscimento da ascoltare.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-114">You'll need to create a list of speech commands for the recognizer to listen for.</span></span> <span data-ttu-id="9bcc8-115">Qui viene costruito un set di comandi per modificare il colore di un ologramma.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-115">Here, we construct a set of commands to change the color of a hologram.</span></span> <span data-ttu-id="9bcc8-116">Per praticità, vengono creati anche i dati che verranno usati per i comandi in un secondo momento.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-116">For the sake of convenience, we also create the data that we'll use for the commands later on.</span></span>

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

<span data-ttu-id="9bcc8-117">È possibile specificare i comandi utilizzando parole fonetiche che potrebbero non essere presenti in un dizionario:</span><span class="sxs-lookup"><span data-stu-id="9bcc8-117">Commands can be specified using phonetic words that might not be in a dictionary:</span></span>

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

<span data-ttu-id="9bcc8-118">L'elenco dei comandi viene caricato nell'elenco di vincoli per il riconoscimento vocale.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-118">The list of commands is loaded into the list of constraints for the speech recognizer.</span></span> <span data-ttu-id="9bcc8-119">Questa operazione viene eseguita usando un oggetto [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) .</span><span class="sxs-lookup"><span data-stu-id="9bcc8-119">This is done by using a [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) object.</span></span>

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

<span data-ttu-id="9bcc8-120">Sottoscrivere l'evento [ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) sulla [SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx)del riconoscimento vocale.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-120">Subscribe to the [ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) event on the speech recognizer's [SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx).</span></span> <span data-ttu-id="9bcc8-121">Questo evento invia una notifica all'app quando uno dei comandi è stato riconosciuto.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-121">This event notifies your app when one of your commands has been recognized.</span></span>

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

<span data-ttu-id="9bcc8-122">Il gestore dell'evento **OnResultGenerated** riceve i dati dell'evento in un'istanza di [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) .</span><span class="sxs-lookup"><span data-stu-id="9bcc8-122">Your **OnResultGenerated** event handler receives event data in a [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) instance.</span></span> <span data-ttu-id="9bcc8-123">Se la confidenza è maggiore della soglia definita, l'applicazione deve tenere presente che si è verificato l'evento.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-123">If the confidence is greater than the threshold you have defined, your app should note that the event happened.</span></span> <span data-ttu-id="9bcc8-124">Salvare i dati dell'evento in modo che sia possibile utilizzarli in un ciclo di aggiornamento successivo.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-124">Save the event data so that you can make use of it in a subsequent update loop.</span></span>

<span data-ttu-id="9bcc8-125">Da *HolographicVoiceInputSampleMain. cpp*:</span><span class="sxs-lookup"><span data-stu-id="9bcc8-125">From *HolographicVoiceInputSampleMain.cpp*:</span></span>

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

<span data-ttu-id="9bcc8-126">Usare i dati, tuttavia, applicabili allo scenario dell'app.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-126">Make use of the data however applicable to your app scenario.</span></span> <span data-ttu-id="9bcc8-127">Nel codice di esempio, viene modificato il colore del cubo dell'ologramma rotante in base al comando dell'utente.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-127">In our example code, we change the color of the spinning hologram cube according to the user's command.</span></span>

<span data-ttu-id="9bcc8-128">Da *HolographicVoiceInputSampleMain:: Update*:</span><span class="sxs-lookup"><span data-stu-id="9bcc8-128">From *HolographicVoiceInputSampleMain::Update*:</span></span>

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

## <a name="use-dictation-for-one-shot-recognition-of-speech-phrases-and-sentences"></a><span data-ttu-id="9bcc8-129">Usare la dettatura per il riconoscimento monofase di frasi e frasi vocali</span><span class="sxs-lookup"><span data-stu-id="9bcc8-129">Use dictation for one-shot recognition of speech phrases and sentences</span></span>

<span data-ttu-id="9bcc8-130">È possibile configurare un riconoscimento vocale per ascoltare frasi o frasi pronunciate dall'utente.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-130">You can configure a speech recognizer to listen for phrases or sentences spoken by the user.</span></span> <span data-ttu-id="9bcc8-131">In questo caso, viene applicato un SpeechRecognitionTopicConstraint che indica al riconoscimento vocale il tipo di input previsto.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-131">In this case, we apply a SpeechRecognitionTopicConstraint that tells the speech recognizer what type of input to expect.</span></span> <span data-ttu-id="9bcc8-132">Il flusso di lavoro dell'app è il seguente, per questo tipo di caso d'uso:</span><span class="sxs-lookup"><span data-stu-id="9bcc8-132">The app workflow is as follows, for this type of use case:</span></span>
1. <span data-ttu-id="9bcc8-133">L'app crea il SpeechRecognizer, fornisce prompt dell'interfaccia utente e avvia l'ascolto di un comando da pronunciare immediatamente.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-133">Your app creates the SpeechRecognizer, provides UI prompts, and starts listening for a command to be spoken immediately.</span></span>
2. <span data-ttu-id="9bcc8-134">L'utente pronuncia una frase o una frase.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-134">The user speaks a phrase, or sentence.</span></span>
3. <span data-ttu-id="9bcc8-135">Viene eseguito il riconoscimento della voce dell'utente e viene restituito un risultato all'app.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-135">Recognition of the user's speech is performed, and a result is returned to the app.</span></span> <span data-ttu-id="9bcc8-136">A questo punto, l'app deve fornire un prompt dell'interfaccia utente che indichi che si è verificato il riconoscimento.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-136">At this point, your app should provide a UI prompt indicating that recognition has occurred.</span></span>
4. <span data-ttu-id="9bcc8-137">A seconda del livello di confidenza a cui si vuole rispondere e del livello di confidenza del risultato del riconoscimento vocale, l'app può elaborare il risultato e rispondere nel modo appropriato.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-137">Depending on the confidence level you want to respond to and the confidence level of the speech recognition result, your app can process the result and respond as appropriate.</span></span>

<span data-ttu-id="9bcc8-138">Questa sezione descrive come creare un SpeechRecognizer, compilare il vincolo e restare in ascolto dell'input vocale.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-138">This section describes how to create a SpeechRecognizer, compile the constraint, and listen for speech input.</span></span>

<span data-ttu-id="9bcc8-139">Il codice seguente compila il vincolo dell'argomento, che in questo caso è ottimizzato per la ricerca Web.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-139">The following code compiles the topic constraint, which in this case is optimized for Web search.</span></span>

```
auto constraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, L"webSearch");
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(constraint);
   return create_task(m_speechRecognizer->CompileConstraintsAsync())
       .then([this](task<SpeechRecognitionCompilationResult^> previousTask)
   {
```

<span data-ttu-id="9bcc8-140">Se la compilazione ha esito positivo, è possibile procedere con il riconoscimento vocale.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-140">If compilation succeeds, we can proceed with speech recognition.</span></span>

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

<span data-ttu-id="9bcc8-141">Il risultato viene quindi restituito all'app.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-141">The result is then returned to the app.</span></span> <span data-ttu-id="9bcc8-142">Se il risultato è sufficientemente sicuro, è possibile elaborare il comando.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-142">If we are confident enough in the result, we can process the command.</span></span> <span data-ttu-id="9bcc8-143">Questo esempio di codice elabora i risultati con almeno una confidenza media.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-143">This code example processes results with at least Medium confidence.</span></span>

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

<span data-ttu-id="9bcc8-144">Quando si usa il riconoscimento vocale, è necessario controllare le eccezioni che potrebbero indicare che l'utente ha disattivato il microfono nelle impostazioni relative alla privacy del sistema.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-144">Whenever you use speech recognition, you should watch for exceptions that could indicate the user has turned off the microphone in the system privacy settings.</span></span> <span data-ttu-id="9bcc8-145">Questo problema può verificarsi durante l'inizializzazione o durante il riconoscimento.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-145">This can happen during initialization, or during recognition.</span></span>

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

<span data-ttu-id="9bcc8-146">**Nota:** Sono disponibili diversi [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) predefiniti per l'ottimizzazione del riconoscimento vocale.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-146">**NOTE:** There are several predefined [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) available for optimizing speech recognition.</span></span>
* <span data-ttu-id="9bcc8-147">Se si desidera ottimizzare la dettatura, utilizzare lo scenario di dettatura:</span><span class="sxs-lookup"><span data-stu-id="9bcc8-147">If you want to optimize for dictation, use the Dictation scenario:</span></span>

```
// Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
```
* <span data-ttu-id="9bcc8-148">Quando si usa il riconoscimento vocale per eseguire una ricerca Web, è possibile usare un vincolo di scenario specifico per il Web come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="9bcc8-148">When using speech to perform a Web search, you can use a Web-specific scenario constraint as follows:</span></span>

```
// Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
```
* <span data-ttu-id="9bcc8-149">Utilizzare il vincolo form per compilare i moduli.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-149">Use the form constraint to fill out forms.</span></span> <span data-ttu-id="9bcc8-150">In questo caso, è preferibile applicare la propria grammatica ottimizzata per compilare il form.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-150">In this case, it is best to apply your own grammar that is optimized for filling out your form.</span></span>

```
// Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
```
* <span data-ttu-id="9bcc8-151">È possibile fornire la propria grammatica usando il formato SRGS.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-151">You can provide your own grammar using the SRGS format.</span></span>

## <a name="use-continuous-freeform-speech-dictation"></a><span data-ttu-id="9bcc8-152">Usa la dettatura continua e libera vocale</span><span class="sxs-lookup"><span data-stu-id="9bcc8-152">Use continuous, freeform speech dictation</span></span>

<span data-ttu-id="9bcc8-153">Vedere l'esempio di codice vocale di Windows 10 UWP per lo scenario di dettatura continua [qui.](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)</span><span class="sxs-lookup"><span data-stu-id="9bcc8-153">See the Windows 10 UWP speech code sample for the continuous dictation scenario [here.](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)</span></span>

## <a name="handle-degradation-in-quality"></a><span data-ttu-id="9bcc8-154">Gestione della riduzione della qualità</span><span class="sxs-lookup"><span data-stu-id="9bcc8-154">Handle degradation in quality</span></span>

<span data-ttu-id="9bcc8-155">Le condizioni nell'ambiente talvolta possono impedire il corretto funzionamento del riconoscimento vocale.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-155">Conditions in the environment can sometimes prevent speech recognition from working.</span></span> <span data-ttu-id="9bcc8-156">Ad esempio, è possibile che la stanza sia troppo rumorosa o che l'utente abbia un volume troppo elevato.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-156">For example, the room might be too noisy or the user might speak at too high a volume.</span></span> <span data-ttu-id="9bcc8-157">L'API riconoscimento vocale fornisce informazioni, laddove possibile, sulle condizioni che hanno causato una riduzione della qualità.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-157">The speech recognition API provides info, where possible, about conditions that have caused a degradation in quality.</span></span>

<span data-ttu-id="9bcc8-158">Queste informazioni vengono inserite nell'app tramite un evento WinRT.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-158">This information is pushed to your app using a WinRT event.</span></span> <span data-ttu-id="9bcc8-159">Di seguito è riportato un esempio di come sottoscrivere questo evento.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-159">Here is an example of how to subscribe to this event.</span></span>

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

<span data-ttu-id="9bcc8-160">Nell'esempio di codice si sceglie di scrivere le informazioni sulle condizioni nella console di debug.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-160">In our code sample, we choose to write the conditions info to the debug console.</span></span> <span data-ttu-id="9bcc8-161">Un'app potrebbe voler fornire feedback all'utente tramite l'interfaccia utente, la sintesi vocale e così via, oppure potrebbe essere necessario comportarsi in modo diverso quando il discorso viene interrotto da una riduzione temporanea della qualità.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-161">An app might want to provide feedback to the user via UI, speech synthesis, and so on, or it might need to behave differently when speech is interrupted by a temporary reduction in quality.</span></span>

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

<span data-ttu-id="9bcc8-162">Se non si usano le classi di riferimento per creare l'app DirectX, è necessario annullare la sottoscrizione all'evento prima di rilasciare o ricreare il riconoscimento vocale.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-162">If you are not using ref classes to create your DirectX app, you must unsubscribe from the event before releasing or recreating your speech recognizer.</span></span> <span data-ttu-id="9bcc8-163">HolographicSpeechPromptSample dispone di una routine per arrestare il riconoscimento e annullare la sottoscrizione agli eventi come segue:</span><span class="sxs-lookup"><span data-stu-id="9bcc8-163">The HolographicSpeechPromptSample has a routine to stop recognition, and unsubscribe from events like so:</span></span>

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

## <a name="use-speech-synthesis-to-provide-audible-voice-prompts"></a><span data-ttu-id="9bcc8-164">Usare la sintesi vocale per fornire richieste vocali acustiche</span><span class="sxs-lookup"><span data-stu-id="9bcc8-164">Use speech synthesis to provide audible voice prompts</span></span>

<span data-ttu-id="9bcc8-165">Gli esempi di riconoscimento vocale olografico usano la sintesi vocale per fornire istruzioni acustiche all'utente.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-165">The holographic speech samples use speech synthesis to provide audible instructions to the user.</span></span> <span data-ttu-id="9bcc8-166">Questo argomento illustra il processo di creazione di un esempio di voce sintetizzata e la riproduzione tramite le API HRTF audio.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-166">This topic walks through the process of creating a synthesized voice sample, and playing it back using the HRTF audio APIs.</span></span>

<span data-ttu-id="9bcc8-167">È necessario fornire le proprie richieste di riconoscimento vocale quando si richiede l'immissione di frasi.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-167">You should provide your own speech prompts when requesting phrase input.</span></span> <span data-ttu-id="9bcc8-168">Questo può essere utile anche per indicare quando è possibile pronunciare i comandi vocali, per uno scenario di riconoscimento continuo.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-168">This can also be helpful for indicating when speech commands can be spoken, for a continuous recognition scenario.</span></span> <span data-ttu-id="9bcc8-169">Di seguito è riportato un esempio di come eseguire questa operazione con un sintetizzatore vocale. Si noti che è anche possibile usare un clip vocale pre-registrato, un'interfaccia utente visiva o altro indicatore di cosa dire, ad esempio negli scenari in cui la richiesta non è dinamica.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-169">Here is an example of how to do that with a speech synthesizer; note that you could also use a pre-recorded voice clip, a visual UI, or other indicator of what to say, for example in scenarios where the prompt is not dynamic.</span></span>

<span data-ttu-id="9bcc8-170">Per prima cosa, creare l'oggetto SpeechSynthesizer:</span><span class="sxs-lookup"><span data-stu-id="9bcc8-170">First, create the SpeechSynthesizer object:</span></span>

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

<span data-ttu-id="9bcc8-171">È anche necessaria una stringa con il testo da sintetizzare:</span><span class="sxs-lookup"><span data-stu-id="9bcc8-171">You also need a string with the text to be synthesized:</span></span>

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

<span data-ttu-id="9bcc8-172">Il riconoscimento vocale viene sintetizzato in modo asincrono usando SynthesizeTextToStreamAsync.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-172">Speech is synthesized asynchronously using SynthesizeTextToStreamAsync.</span></span> <span data-ttu-id="9bcc8-173">Qui viene avviata un'attività asincrona per sintetizzare il discorso.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-173">Here, we kick off an async task to synthesize the speech.</span></span>

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

<span data-ttu-id="9bcc8-174">La sintesi vocale viene inviata come flusso di byte.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-174">The speech synthesis is sent as a byte stream.</span></span> <span data-ttu-id="9bcc8-175">È possibile inizializzare una voce XAudio2 usando tale flusso di byte; per gli esempi di codice olografico, viene riprodotto come effetto audio HRTF.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-175">We can initialize an XAudio2 voice using that byte stream; for our holographic code samples, we play it back as an HRTF audio effect.</span></span>

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

<span data-ttu-id="9bcc8-176">Come per il riconoscimento vocale, la sintesi vocale genera un'eccezione se si verifica un errore.</span><span class="sxs-lookup"><span data-stu-id="9bcc8-176">As with speech recognition, speech synthesis will throw an exception if something goes wrong.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9bcc8-177">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="9bcc8-177">See also</span></span>
* [<span data-ttu-id="9bcc8-178">Progettazione di app vocali</span><span class="sxs-lookup"><span data-stu-id="9bcc8-178">Speech app design</span></span>](https://msdn.microsoft.com/library/dn596121.aspx)
* [<span data-ttu-id="9bcc8-179">Esempio SpeechRecognitionAndSynthesis</span><span class="sxs-lookup"><span data-stu-id="9bcc8-179">SpeechRecognitionAndSynthesis sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)

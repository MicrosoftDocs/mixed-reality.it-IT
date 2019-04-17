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
# <a name="voice-input-in-directx"></a>Input vocale in DirectX

In questo argomento viene illustrato come implementare [comandi vocali](voice-input.md), piccola frase e frase riconoscimento e in un'app DirectX per realtà mista di Windows.

>[!NOTE]
>I frammenti di codice in questo articolo illustrano attualmente l'utilizzo di C++/CX invece di C + + 17 conformi C++/WinRT usato nel [ C++ modello di progetto holographic](creating-a-holographic-directx-project.md).  I concetti sono equivalenti per un C++progetto /WinRT, anche se è necessario convertire il codice.

## <a name="use-a-speechrecognizer-for-continuous-recognition-of-voice-commands"></a>Usare un SpeechRecognizer per il riconoscimento continuo dei comandi vocali

In questa sezione viene descritto come utilizzare riconoscimento vocale continua per abilitare i comandi vocali nell'app. Questa procedura dettagliata Usa codice dal [HolographicVoiceInput](http://go.microsoft.com/fwlink/p/?LinkId=844964) esempio. Quando viene eseguito il codice di esempio, pronunciare il nome di uno dei comandi per modificare il colore del cubo rotante colore registrati.

In primo luogo, creare una nuova **Windows::Media::SpeechRecognition::SpeechRecognizer** istanza.

Dal *HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState*:

```
m_speechRecognizer = ref new SpeechRecognizer();
```

È necessario creare un elenco di comandi vocali per rimanere in ascolto per il riconoscimento. In questo caso, si crea un set di comandi per modificare il colore di ologramma. Per maggiore praticità, si crea anche i dati che verranno utilizzate per i comandi in un secondo momento.

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

I comandi possono essere specificati utilizzando fonetiche parole che non sia in un dizionario:

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

L'elenco dei comandi viene caricato nell'elenco di vincoli per il riconoscimento vocale. Questa operazione viene eseguita usando un [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) oggetto.

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

Sottoscrivere il [ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) evento su del riconoscimento vocale [SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx). Questo evento di notifica all'app quando uno dei comandi è stato riconosciuto.

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

I **OnResultGenerated** gestore eventi riceve i dati di evento in un [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) istanza. Se il livello di confidenza è maggiore della soglia che è stata definita, l'app deve tenere presente che si è verificato l'evento. Salvare i dati dell'evento in modo da poter apportare uso in un ciclo di aggiornamento successivo.

Dal *HolographicVoiceInputSampleMain.cpp*:

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

Rendere uso dei dati, tuttavia applicabili al proprio scenario di app. Nel nostro codice di esempio, è modificare il colore del cubo rotante ologrammi in base al comando dell'utente.

Dal *HolographicVoiceInputSampleMain::Update*:

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

## <a name="use-dictation-for-one-shot-recognition-of-speech-phrases-and-sentences"></a>Usare la dettatura per il riconoscimento monofase di frasi e frasi

È possibile configurare un sistema di riconoscimento vocale per l'ascolto delle frasi o le frasi pronunciate dall'utente. In questo caso, viene applicato un SpeechRecognitionTopicConstraint che indica il tipo di input per prevedere il riconoscimento vocale. Il flusso di lavoro di app è come indicato di seguito, per questo tipo di caso d'uso:
1. L'app viene creata la SpeechRecognizer fornisce prompt dell'interfaccia utente e avvia l'ascolto di un comando da risolvere immediatamente.
2. L'utente pronuncia una frase o una frase.
3. Riconoscimento vocale dell'utente viene eseguito e viene restituito un risultato per l'app. A questo punto, l'app deve fornire un prompt dei comandi dell'interfaccia utente che indica che si è verificato un riconoscimento.
4. A seconda del livello di confidenza per rispondere a e il livello di confidenza del risultato del riconoscimento vocale, l'app può elaborare il risultato e correttivo appropriato.

In questa sezione viene descritto come creare un SpeechRecognizer, compilare il vincolo e restare in attesa per l'input vocale.

Il codice seguente compila il vincolo di argomento, che in questo caso è ottimizzato per la ricerca sul Web.

```
auto constraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, L"webSearch");
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(constraint);
   return create_task(m_speechRecognizer->CompileConstraintsAsync())
       .then([this](task<SpeechRecognitionCompilationResult^> previousTask)
   {
```

Se la compilazione ha esito positivo, è possibile procedere con il riconoscimento vocale.

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

Il risultato viene quindi restituito all'app. Se si sono sufficientemente sicuri nel risultato, è possibile elaborare il comando. Questo esempio di codice elabora i risultati in tutta sicurezza almeno su medio.

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

Quando si usa il riconoscimento vocale, è opportuno considerare attentamente per le eccezioni che potrebbero indicare che l'utente ha disattivato il microfono nelle impostazioni di privacy del sistema. Questa situazione può verificarsi durante l'inizializzazione o durante il riconoscimento.

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

**NOTA:** Esistono diverse predefiniti [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) disponibili per l'ottimizzazione di riconoscimento vocale.
* Se si desidera ottimizzare per la dettatura, usare lo scenario di dettatura:

```
// Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
```
* Quando si utilizza riconoscimento vocale per eseguire una ricerca sul Web, è possibile usare un vincolo di scenario specifici Web come indicato di seguito:

```
// Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
```
* Usare il vincolo di form per compilare i moduli. In questo caso, si consiglia di applicare il proprio grammatica ottimizzata per la compilazione del modulo.

```
// Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
```
* È possibile fornire il proprio Grammatica SRGS nel formato.

## <a name="use-continuous-freeform-speech-dictation"></a>Usare dettatura continua a mano libera

Vedere l'esempio di codice UWP di Windows 10 vocale per lo scenario di dettatura continua [qui.](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)

## <a name="handle-degradation-in-quality"></a>Gestire una riduzione delle qualità

Le condizioni nell'ambiente possono a volte impediscono il riconoscimento vocale funzionamento. Ad esempio, potrebbe essere troppo disturbata chat room oppure l'utente può pronunciare a un volume troppo elevato. L'API riconoscimento vocale fornisce info, laddove possibile, informazioni sulle condizioni che hanno causato una riduzione delle prestazioni di qualità.

Queste informazioni viene eseguito il push all'App usando un evento di WinRT. Ecco un esempio di come sottoscrivere questo evento.

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

In questo esempio di codice, si sceglie di scrivere le informazioni di condizioni nella console di debug. Un'app potrebbe essere necessario fornire commenti e suggerimenti per l'utente attraverso l'interfaccia utente, sintesi vocale e così via, o potrebbe essere necessario un comportamento diverso quando vocale verrà interrotto da una temporanea riduzione della qualità.

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

Se non si usa le classi di riferimento per creare l'app DirectX, è necessario annullare la sottoscrizione dall'evento prima di ricreare il riconoscimento vocale o di rilascio. Il HolographicSpeechPromptSample dispone di una routine per arrestare il riconoscimento e la sottoscrizione di eventi come segue:

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

## <a name="use-speech-synthesis-to-provide-audible-voice-prompts"></a>Usare la sintesi vocale per fornire istruzioni vocali acustici

Gli esempi di riconoscimento vocale holographic utilizzano sintesi vocale per fornire istruzioni acustici all'utente. In questo argomento descrive il processo di creazione di un esempio di voce sintetizzata e riprodurlo usando le API audio HRTF.

È necessario fornire che il proprio riconoscimento vocale richiesto la richiesta di input di una frase. Anche questo può essere utile per indicare quando i comandi di riconoscimento vocale possono essere pronunciati, per uno scenario di riconoscimento continuo. Ecco un esempio di come eseguire questa operazione con un sintetizzatore vocale; Si noti che è possibile usare anche un messaggio vocale preregistrati, un'interfaccia utente visual o un altro indicatore di ciò che occorre ad esempio, ad esempio in scenari in cui la richiesta non è dinamica.

In primo luogo, creare l'oggetto SpeechSynthesizer:

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

È anche necessaria una stringa con il testo da sottoporre:

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

Riconoscimento vocale è sintetizzati in modo asincrono usando SynthesizeTextToStreamAsync. In questo caso, abbiamo avviato un'attività asincrona per sintetizzare il riconoscimento vocale.

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

La sintesi vocale viene inviata come flusso di byte. È possibile inizializzare una voce XAudio2 usando tale flusso di byte; per gli esempi di codice holographic, abbiamo riprodurlo effetto HRTF audio.

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

Come con il riconoscimento vocale, sintesi vocale genererà un'eccezione se si verificano problemi.

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

## <a name="see-also"></a>Vedere anche
* [Progettazione di app di riconoscimento vocale](https://msdn.microsoft.com/library/dn596121.aspx)
* [Audio spaziale in DirectX](spatial-sound-in-directx.md)
* [Esempio SpeechRecognitionAndSynthesis](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)

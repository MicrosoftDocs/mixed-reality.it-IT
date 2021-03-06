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
# <a name="voice-input-in-directx"></a>Input vocale in DirectX

Questo articolo illustra come implementare i [comandi vocali](voice-input.md) e il riconoscimento di frasi brevi e frasi in un'app DirectX per la realtà mista di Windows.

>[!NOTE]
>I frammenti di codice in questo articolo usano C++/CX anziché/WinRT conforme C++a C + 17, usato nel modello di [ C++ progetto olografico](creating-a-holographic-directx-project.md).  I concetti sono equivalenti per C++un progetto/WinRT, ma è necessario tradurre il codice.

## <a name="use-speechrecognizer-for-continuous-speech-recognition"></a>Usare SpeechRecognizer per il riconoscimento vocale continuo

Questa sezione descrive come usare il riconoscimento vocale continuo per abilitare i comandi vocali nell'app. Questa procedura dettagliata usa il codice dell'esempio [HolographicVoiceInput](https://go.microsoft.com/fwlink/p/?LinkId=844964) . Quando l'esempio è in esecuzione, pronunciare il nome di uno dei comandi colorati registrati per modificare il colore del cubo rotante.

Per prima cosa, creare una nuova istanza di *Windows:: media:: sintesi vocale:: SpeechRecognizer* .

Da *HolographicVoiceInputSampleMain:: CreateSpeechConstraintsForCurrentState*:

```
m_speechRecognizer = ref new SpeechRecognizer();
```

Creare un elenco di comandi vocali per il riconoscimento da ascoltare. Qui viene costruito un set di comandi per modificare il colore di un ologramma. Per praticità, vengono creati anche i dati che verranno usati per i comandi in un secondo momento.

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

È possibile usare parole fonetiche che potrebbero non essere presenti in un dizionario per specificare i comandi.

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

Per caricare l'elenco di comandi nell'elenco di vincoli per il riconoscimento vocale, usare un oggetto [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) .

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

Sottoscrivere l'evento [ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) sulla [SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx)del riconoscimento vocale. Questo evento invia una notifica all'app quando uno dei comandi è stato riconosciuto.

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

Il gestore dell'evento *OnResultGenerated* riceve i dati dell'evento in un'istanza di [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) . Se la confidenza è maggiore della soglia definita, l'applicazione deve tenere presente che si è verificato l'evento. Salvare i dati dell'evento in modo che sia possibile utilizzarli in un ciclo di aggiornamento successivo.

Da *HolographicVoiceInputSampleMain. cpp*:

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

Nel codice di esempio, viene modificato il colore del cubo dell'ologramma rotante in base al comando dell'utente.

Da *HolographicVoiceInputSampleMain:: Update*:

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

## <a name="use-one-shot-recognition"></a>Usa il riconoscimento "One-Shot"

È possibile configurare un riconoscimento vocale per ascoltare frasi o frasi pronunciate dall'utente. In questo caso, viene applicato un *SpeechRecognitionTopicConstraint* che indica al riconoscimento vocale il tipo di input previsto. Ecco un flusso di lavoro dell'app per questo scenario:
1. L'app crea il SpeechRecognizer, fornisce prompt dell'interfaccia utente e inizia l'ascolto di un comando parlato.
2. L'utente pronuncia una frase o una frase.
3. Il riconoscimento della voce dell'utente si verifica e viene restituito un risultato all'app. A questo punto, l'app deve fornire un prompt dell'interfaccia utente per indicare che si è verificato il riconoscimento.
4. A seconda del livello di confidenza a cui si desidera rispondere e del livello di confidenza del risultato del riconoscimento vocale, l'app può elaborare il risultato e rispondere nel modo appropriato.

Questa sezione descrive come creare un SpeechRecognizer, compilare il vincolo e restare in ascolto dell'input vocale.

Il codice seguente compila il vincolo dell'argomento, che in questo caso è ottimizzato per la ricerca Web.

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

Il risultato viene quindi restituito all'app. Se il risultato è sufficientemente sicuro, è possibile elaborare il comando. Questo esempio di codice elabora i risultati con almeno una confidenza media.

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

Quando si usa il riconoscimento vocale, controllare le eccezioni che potrebbero indicare che l'utente ha disattivato il microfono nelle impostazioni relative alla privacy del sistema. Questo problema può verificarsi durante l'inizializzazione o il riconoscimento.

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
> Sono disponibili diversi [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) predefiniti che è possibile usare per ottimizzare il riconoscimento vocale.

* Per ottimizzare la dettatura, utilizzare lo scenario di dettatura.<br/>
   ```
   // Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
   ```

* Per le ricerche web vocali, utilizzare il seguente vincolo di scenario specifico per il Web.

   ```
   // Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
   ```

* Utilizzare il vincolo form per compilare i moduli. In questo caso, è preferibile applicare la propria grammatica ottimizzata per compilare il modulo.

   ```
   // Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
   ```
* È possibile fornire la propria grammatica nel formato SRGS.

## <a name="use-continuous-recognition"></a>Usa il riconoscimento continuo

Per lo scenario di dettatura continua, vedere l' [esempio di codice di riconoscimento vocale di Windows 10 UWP](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp).

## <a name="handle-quality-degradation"></a>Gestione della riduzione della qualità

Le condizioni ambientali talvolta interferiscono con il riconoscimento vocale. Ad esempio, la stanza potrebbe essere troppo rumorosa o l'utente potrebbe parlare troppo forte. Quando possibile, l'API riconoscimento vocale fornisce informazioni sulle condizioni che hanno causato la riduzione della qualità. Queste informazioni vengono inserite nell'app tramite un evento WinRT. Nell'esempio seguente viene illustrato come sottoscrivere questo evento.

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

Nell'esempio di codice vengono scritte le informazioni sulle condizioni nella console di debug. Un'app potrebbe voler fornire feedback all'utente tramite l'interfaccia utente, la sintesi vocale e un altro metodo. In alternativa, potrebbe essere necessario comportarsi in modo diverso quando il discorso viene interrotto da una riduzione temporanea della qualità.

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

Se non si usano le classi di riferimento per creare l'app DirectX, è necessario annullare la sottoscrizione all'evento prima di rilasciare o ricreare il riconoscimento vocale. HolographicSpeechPromptSample dispone di una routine per arrestare il riconoscimento e annullare la sottoscrizione agli eventi.

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

## <a name="use-speech-synthesis-to-provide-audible-prompts"></a>Usare la sintesi vocale per fornire richieste acustiche

Gli esempi di riconoscimento vocale olografico usano la sintesi vocale per fornire istruzioni acustiche all'utente. Questa sezione illustra come creare un esempio di voce sintetizzata e riprodurlo con le API HRTF audio.

Quando si richiede l'input di frasi, è necessario fornire le proprie richieste di riconoscimento vocale. I prompt possono anche indicare quando è possibile pronunciare i comandi vocali per uno scenario di riconoscimento continuo. Nell'esempio seguente viene illustrato come utilizzare un sintetizzatore vocale a tale scopo. È anche possibile usare un clip vocale pre-registrato, un'interfaccia utente visiva o un altro indicatore di cosa dire, ad esempio negli scenari in cui la richiesta non è dinamica.

Per prima cosa, creare l'oggetto SpeechSynthesizer.

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

È anche necessaria una stringa che includa il testo da sintetizzare.

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

Il riconoscimento vocale viene sintetizzato in modo asincrono tramite SynthesizeTextToStreamAsync. Qui viene avviata un'attività asincrona per sintetizzare il discorso.

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

La sintesi vocale viene inviata come flusso di byte. È possibile usare il flusso di byte per inizializzare una voce XAudio2. Per gli esempi di codice olografico, viene riprodotto come effetto audio HRTF.

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

Come per il riconoscimento vocale, la sintesi vocale genera un'eccezione se si verifica un errore.

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
* [Progettazione di app vocali](https://msdn.microsoft.com/library/dn596121.aspx)
* [Esempio SpeechRecognitionAndSynthesis](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)

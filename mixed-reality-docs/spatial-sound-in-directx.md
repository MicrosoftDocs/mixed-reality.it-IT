---
title: Audio spaziale in DirectX
description: Aggiunta alle app di realtà mista di Windows basate su DirectX usando le librerie di audio XAudio2 e xAPO spaziale audio.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows misti realtà, spaziale audio, le app, XAudio2, basso livello, xAPO, libreria di audio, procedura dettagliata, DirectX
ms.openlocfilehash: 04d8c43ab400eed4cec5cbd848af5b888cb66e4b
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605140"
---
# <a name="spatial-sound-in-directx"></a>Audio spaziale in DirectX

Aggiungere suoni spaziali per le app di realtà mista di Windows basate su DirectX usando la [XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx) e [xAPO](https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx) librerie audio.

Questo argomento Usa codice di esempio dal HolographicHRTFAudioSample.

>[!NOTE]
>I frammenti di codice in questo articolo illustrano attualmente l'utilizzo di C++/CX invece di C + + 17 conformi C++/WinRT usato nel [ C++ modello di progetto holographic](creating-a-holographic-directx-project.md).  I concetti sono equivalenti per un C++progetto /WinRT, anche se è necessario convertire il codice.

## <a name="overview-of-head-relative-spatial-sound"></a>Panoramica del suono spaziali relativo Head

Spaziale audio viene implementato come un **oggetto elaborazione audio (APO)** che usa un **head correlate (HRTF) la funzione di trasferimento** filtrare in base a *spatialize* un normale flusso audio.

Includere questi file di intestazione in PCH. h per accedere alle API dell'audio:
* XAudio2.h
* xapo.h
* hrtfapoapi.h

Per impostare il suono spaziale:
1. Chiamare [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) per inizializzare un nuova APO per l'audio HRTF.
2. Assegnare il [parametri HRTF](https://msdn.microsoft.com/library/windows/desktop/mt186608.aspx) e [ambiente HRTF](https://msdn.microsoft.com/library/windows/desktop/mt186604.aspx) per definire le caratteristiche acustiche del APO spaziale audio.
3. Configurare il motore XAudio2 per l'elaborazione HRTF.
4. Creare un [IXAudio2SourceVoice](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.aspx) oggetto e chiamare [avviare](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx).

## <a name="implementing-hrtf-and-spatial-sound-in-your-directx-app"></a>Implementazione HRTF e spaziale audio nell'app DirectX

È possibile ottenere una varietà di effetti configurando il APO HRTF con diversi parametri e ambienti. Usare il codice seguente per esplorare le possibilità. Scaricare l'esempio di codice (Universal Windows Platform) qui: [Esempio Spatial audio](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpatialSound)

In questi file sono disponibili i tipi di supporto:
* [AudioFileReader.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/AudioFileReader.cpp): Carica file audio usando Media Foundation e il [IMFSourceReader interfaccia](https://msdn.microsoft.com/library/windows/desktop/dd374655.aspx).
* [XAudio2Helpers.h](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/XAudio2Helpers.h): Implementa il **SetupXAudio2** funzione per inizializzare XAudio2 per l'elaborazione HRTF.

### <a name="add-spatial-sound-for-an-omnidirectional-source"></a>Aggiungere suoni spaziali per un'origine omnidirezionale

Alcuni vntana nelle vicinanze dell'utente emette un suono in modo uniforme in tutte le direzioni. Il codice seguente viene illustrato come inizializzare un APO per emettere un suono omnidirezionale. In questo esempio, questo concetto si applica al cubo rotante dal modello di app Windows Holographic. Per il listato di codice completo, vedere [OmnidirectionalSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/OmnidirectionalSound.cpp).

**Motore audio spaziale della finestra supporta solo 48 KB samplerate per la riproduzione. La maggior parte dei programmi di middleware, ad esempio Unity, convertirà automaticamente i file audio nel formato desiderato, ma se si avvia manipolare a livelli inferiori nel sistema audio o rendere il proprio, questo è molto importante da ricordare impedire arresti anomali del sistema o comportamenti indesiderati, ad esempio Errore di sistema HRTF.**

In primo luogo, è necessario inizializzare la sospensione. Nell'app di esempio holographic, si sceglie di eseguire questa operazione dopo aver creato il **HolographicSpace**.

From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:

```
// Spatial sound
auto hr = m_omnidirectionalSound.Initialize(L"assets//MonoSound.wav");
```

L'implementazione di inizializzazione, dalla *OmnidirectionalSound.cpp*:

```
// Initializes an APO that emits sound equally in all directions.
HRESULT OmnidirectionalSound::Initialize( LPCWSTR filename )
{
    // _audioFile is of type AudioFileReader, which is defined in AudioFileReader.cpp.
    auto hr = _audioFile.Initialize( filename );

    ComPtr<IXAPO> xapo;
    if ( SUCCEEDED( hr ) )
    {
        // Passing in nullptr as the first arg for HrtfApoInit initializes the APO with defaults of
        // omnidirectional sound with natural distance decay behavior.
        // CreateHrtfApo fails with E_NOTIMPL on unsupported platforms.
        hr = CreateHrtfApo( nullptr, &xapo );
    }

    if ( SUCCEEDED( hr ) )
    {
        // _hrtfParams is of type ComPtr<IXAPOHrtfParameters>.
        hr = xapo.As( &_hrtfParams );
    }

    // Set the default environment.
    if ( SUCCEEDED( hr ) )
    {
        hr = _hrtfParams->SetEnvironment( HrtfEnvironment::Outdoors );
    }

    // Initialize an XAudio2 graph that hosts the HRTF xAPO.
    // The source voice is used to submit audio data and control playback.
    if ( SUCCEEDED( hr ) )
    {
        hr = SetupXAudio2( _audioFile.GetFormat(), xapo.Get(), &_xaudio2, &_sourceVoice );
    }

    // Submit audio data to the source voice.
    if ( SUCCEEDED( hr ) )
    {
        XAUDIO2_BUFFER buffer{ };
        buffer.AudioBytes = static_cast<UINT32>( _audioFile.GetSize() );
        buffer.pAudioData = _audioFile.GetData();
        buffer.LoopCount = XAUDIO2_LOOP_INFINITE;

        // _sourceVoice is of type IXAudio2SourceVoice*.
        hr = _sourceVoice->SubmitSourceBuffer( &buffer );
    }

    return hr;
}
```

Dopo aver configurato il APO per HRTF, si chiama [avviare](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) nella voce origine da riprodurre l'audio. Nell'app di esempio, si sceglie di inserirlo in un ciclo in modo che è possibile continuare ad ascoltare l'audio proveniente dal cubo.

From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:

```
if (SUCCEEDED(hr))
{
    m_omnidirectionalSound.SetEnvironment(HrtfEnvironment::Small);
    m_omnidirectionalSound.OnUpdate(m_spinningCubeRenderer->GetPosition());
    m_omnidirectionalSound.Start();
}
```

Dal *OmnidirectionalSound.cpp*:

```
HRESULT OmnidirectionalSound::Start()
{
    _lastTick = GetTickCount64();
    return _sourceVoice->Start();
}
```

A questo punto, ogni volta che viene aggiornato il frame, è necessario aggiornare la posizione del ologrammi rispetto al dispositivo stesso. Questo avviene perché HRTF posizioni sono sempre espresse in relazione head dell'utente, tra cui la posizione head e l'orientamento.

A questo scopo in un HolographicSpace, è necessario costruire una matrice di trasformazione dal nostro sistema di coordinate SpatialStationaryFrameOfReference a un sistema di coordinate che vengono fissata al dispositivo stesso.

From *HolographicHrtfAudioSampleMain::Update()*:

```
m_spinningCubeRenderer->Update(m_timer);

SpatialPointerPose^ currentPose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
if (currentPose != nullptr)
{
    // Use a coordinate system built from a pointer pose.
    SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
    if (pose != nullptr)
    {
        float3 headPosition = pose->Head->Position;
        float3 headUp = pose->Head->UpDirection;
        float3 headDirection = pose->Head->ForwardDirection;

        // To construct a rotation matrix, we need three vectors that are mutually orthogonal.
        // The first vector is the gaze vector.
        float3 negativeZAxis = normalize(headDirection);

        // The second vector should end up pointing away from the horizontal plane of the device.
        // We first guess by using the head "up" direction.
        float3 positiveYAxisGuess = normalize(headUp);

        // The third vector completes the set by being orthogonal to the other two.
        float3 positiveXAxis = normalize(cross(negativeZAxis, positiveYAxisGuess));

        // Now, we can correct our "up" vector guess by redetermining orthogonality.
        float3 positiveYAxis = normalize(cross(negativeZAxis, positiveXAxis));

        // The rotation matrix is formed as a standard basis rotation.
        float4x4 rotationTransform =
            {
            positiveXAxis.x, positiveYAxis.x, negativeZAxis.x, 0.f,
            positiveXAxis.y, positiveYAxis.y, negativeZAxis.y, 0.f,
            positiveXAxis.z, positiveYAxis.z, negativeZAxis.z, 0.f,
            0.f, 0.f, 0.f, 1.f,
            };

        // The translate transform can be constructed using the Windows::Foundation::Numerics API.
        float4x4 translationTransform = make_float4x4_translation(-headPosition);

        // Now, we have a basis transform from our spatial coordinate system to a device-relative
        // coordinate system.
        float4x4 coordinateSystemTransform = translationTransform * rotationTransform;

        // Reinterpret the cube position in the device's coordinate system.
        float3 cubeRelativeToHead = transform(m_spinningCubeRenderer->GetPosition(), coordinateSystemTransform);

        // Note that at (0, 0, 0) exactly, the HRTF audio will simply pass through audio. We can use a minimal offset
        // to simulate a zero distance when the hologram position vector is exactly at the device origin in order to
        // allow HRTF to continue functioning in this edge case.
        float distanceFromHologramToHead = length(cubeRelativeToHead);
        static const float distanceMin = 0.00001f;
        if (distanceFromHologramToHead < distanceMin)
        {
            cubeRelativeToHead = float3(0.f, distanceMin, 0.f);
        }

        // Position the spatial sound source on the hologram.
        m_omnidirectionalSound.OnUpdate(cubeRelativeToHead);

        // For debugging, it can be interesting to observe the distance in the debugger.
        /*
        std::wstring distanceString = L"Distance from hologram to head: ";
        distanceString += std::to_wstring(distanceFromHologramToHead);
        distanceString += L"\n";
        OutputDebugStringW(distanceString.c_str());
        */
    }
}
```

La posizione HRTF viene applicata direttamente per l'audio APO dalla classe helper OmnidirectionalSound.

Dal *OmnidirectionalSound::OnUpdate*:

```
HRESULT OmnidirectionalSound::OnUpdate(_In_ Numerics::float3 position)
{
    auto hrtfPosition = HrtfPosition{ position.x, position.y, position.z };
    return _hrtfParams->SetSourcePosition(&hrtfPosition);
}
```

La procedura è terminata. Continuare a leggere per altre informazioni sulle operazioni eseguibili con HRTF audio e Windows Holographic.

### <a name="initialize-spatial-sound-for-a-directional-source"></a>Inizializzare spaziale audio per un'origine direzionale

Alcuni vntana nelle vicinanze dell'utente di creare il suono principalmente in una sola direzione. Questo modello audio è denominato *cardioide* perché sembra cuori cartone animato. Il codice seguente viene illustrato come inizializzare un APO per emettere direzionale audio. Per il listato di codice completo, vedere [CardioidSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CardioidSound.cpp) .

Dopo aver configurato il APO per HRTF, chiamare [avviare](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) nella voce origine da riprodurre l'audio.

```
// Initializes an APO that emits directional sound.
HRESULT CardioidSound::Initialize( LPCWSTR filename )
{
    // _audioFile is of type AudioFileReader, which is defined in AudioFileReader.cpp.
    auto hr = _audioFile.Initialize( filename );
    if ( SUCCEEDED( hr ) )
    {
        // Initialize with "Scaling" fully directional and "Order" with broad radiation pattern.
        // As the order goes higher, the cardioid directivity region becomes narrower.
        // Any direct path signal outside of the directivity region will be attenuated based on the scaling factor.
        // For example, if scaling is set to 1 (fully directional) the direct path signal outside of the directivity
        // region will be fully attenuated and only the reflections from the environment will be audible.
        hr = ConfigureApo( 1.0f, 4.0f );
    }
    return hr;
}

HRESULT CardioidSound::ConfigureApo( float scaling, float order )
{
    // Cardioid directivity configuration:
    // Directivity is specified at xAPO instance initialization and can't be changed per frame.
    // To change directivity, stop audio processing and reinitialize another APO instance with the new directivity.
    HrtfDirectivityCardioid cardioid;
    cardioid.directivity.type = HrtfDirectivityType::Cardioid;
    cardioid.directivity.scaling = scaling;
    cardioid.order = order;

    // APO intialization
    HrtfApoInit apoInit;
    apoInit.directivity = &cardioid.directivity;
    apoInit.distanceDecay = nullptr; // nullptr specifies natural distance decay behavior (simulates real world)

    // CreateHrtfApo fails with E_NOTIMPL on unsupported platforms.
    ComPtr<IXAPO> xapo;
    auto hr = CreateHrtfApo( &apoInit, &xapo );

    if ( SUCCEEDED( hr ) )
    {
        hr = xapo.As( &_hrtfParams );
    }

    // Set the initial environment.
    // Environment settings configure the "distance cues" used to compute the early and late reverberations.
    if ( SUCCEEDED( hr ) )
    {
        hr = _hrtfParams->SetEnvironment( _HrtfEnvironment::Outdoors );
    }

    // Initialize an XAudio2 graph that hosts the HRTF xAPO.
    // The source voice is used to submit audio data and control playback.
    if ( SUCCEEDED( hr ) )
    {
        hr = SetupXAudio2( _audioFile.GetFormat(), xapo.Get(), &_xaudio2, &_sourceVoice );
    }

    // Submit audio data to the source voice
    if ( SUCCEEDED( hr ) )
    {
        XAUDIO2_BUFFER buffer{ };
        buffer.AudioBytes = static_cast<UINT32>( _audioFile.GetSize() );
        buffer.pAudioData = _audioFile.GetData();
        buffer.LoopCount = XAUDIO2_LOOP_INFINITE;
        hr = _sourceVoice->SubmitSourceBuffer( &buffer );
    }

    return hr;
}
```

### <a name="implement-custom-decay"></a>Implementare decay personalizzato

È possibile ignorare la frequenza con cui un suono spaziale diminuisce con distanza e/o a quale distanza tagliata completamente. Per implementare il comportamento di decadimento personalizzato su un suono spaziale, popolare un' [struct HrtfDistanceDecay](https://msdn.microsoft.com/library/windows/desktop/mt186602.aspx) e assegnarla al **distanceDecay** campo un [HrtfApoInit struct](https://msdn.microsoft.com/library/windows/desktop/mt186597.aspx) prima di passarlo per il [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) (funzione).

Aggiungere il codice seguente per il **inizializzare** metodo illustrato in precedenza per specificare il comportamento di decadimento personalizzato. Per il listato di codice completo, vedere [CustomDecay.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CustomDecay.cpp).

```
HRESULT CustomDecaySound::Initialize( LPCWSTR filename )
{
    auto hr = _audioFile.Initialize( filename );

    ComPtr<IXAPO> xapo;
    if ( SUCCEEDED( hr ) )
    {
        HrtfDistanceDecay customDecay;
        customDecay.type = HrtfDistanceDecayType::CustomDecay;               // Custom decay behavior, we'll pass in the gain value on every frame.
        customDecay.maxGain = 0;                                             // 0dB max gain
        customDecay.minGain = -96.0f;                                        // -96dB min gain
        customDecay.unityGainDistance = HRTF_DEFAULT_UNITY_GAIN_DISTANCE;    // Default unity gain distance
        customDecay.cutoffDistance = HRTF_DEFAULT_CUTOFF_DISTANCE;           // Default cutoff distance

        // Setting the directivity to nullptr specifies omnidirectional sound.
        HrtfApoInit init;
        init.directivity = nullptr;
        init.distanceDecay = &customDecay;

        // CreateHrtfApo will fail with E_NOTIMPL on unsupported platforms.
        hr = CreateHrtfApo( &init, &xapo );
    }
...
}
```

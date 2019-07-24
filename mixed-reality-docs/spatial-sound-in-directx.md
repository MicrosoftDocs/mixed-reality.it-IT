---
title: Audio spaziale in DirectX
description: Aggiungere un suono spaziale alle app per la realtà mista di Windows in base a DirectX usando le librerie audio XAudio2 e xAPO.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, audio spaziale, app, XAudio2, basso livello, xAPO, libreria audio, procedura dettagliata, DirectX
ms.openlocfilehash: 04d8c43ab400eed4cec5cbd848af5b888cb66e4b
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63550439"
---
# <a name="spatial-sound-in-directx"></a><span data-ttu-id="88753-104">Audio spaziale in DirectX</span><span class="sxs-lookup"><span data-stu-id="88753-104">Spatial sound in DirectX</span></span>

<span data-ttu-id="88753-105">Aggiungere un suono spaziale alle app per la realtà mista di Windows in base a DirectX usando le librerie audio [XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx) e [xAPO](https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx) .</span><span class="sxs-lookup"><span data-stu-id="88753-105">Add spatial sound to your Windows Mixed Reality apps based on DirectX by using the [XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx) and [xAPO](https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx) audio libraries.</span></span>

<span data-ttu-id="88753-106">In questo argomento viene usato il codice di esempio di HolographicHRTFAudioSample.</span><span class="sxs-lookup"><span data-stu-id="88753-106">This topic uses sample code from the HolographicHRTFAudioSample.</span></span>

>[!NOTE]
><span data-ttu-id="88753-107">I frammenti di codice in questo articolo illustrano attualmente l' C++uso di/CX, invece di/WinRT conformi C++a C + 17 come usato nel modello di [ C++ progetto olografico](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="88753-107">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="88753-108">I concetti sono equivalenti per C++un progetto/WinRT, anche se sarà necessario tradurre il codice.</span><span class="sxs-lookup"><span data-stu-id="88753-108">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="overview-of-head-relative-spatial-sound"></a><span data-ttu-id="88753-109">Panoramica dell'audio spaziale relativo alla testa</span><span class="sxs-lookup"><span data-stu-id="88753-109">Overview of Head Relative Spatial Sound</span></span>

<span data-ttu-id="88753-110">Il suono spaziale viene implementato come un **oggetto di elaborazione audio (APO)** che utilizza un filtro **HRTF (Head Related Transfer Function)** per *spatialize* un flusso audio normale.</span><span class="sxs-lookup"><span data-stu-id="88753-110">Spatial sound is implemented as an **audio processing object (APO)** that uses a **head related transfer function (HRTF)** filter to *spatialize* an ordinary audio stream.</span></span>

<span data-ttu-id="88753-111">Includere questi file di intestazione in PCH. h per accedere alle API audio:</span><span class="sxs-lookup"><span data-stu-id="88753-111">Include these header files in pch.h to access the audio APIs:</span></span>
* <span data-ttu-id="88753-112">XAudio2. h</span><span class="sxs-lookup"><span data-stu-id="88753-112">XAudio2.h</span></span>
* <span data-ttu-id="88753-113">xAPO. h</span><span class="sxs-lookup"><span data-stu-id="88753-113">xapo.h</span></span>
* <span data-ttu-id="88753-114">hrtfapoapi. h</span><span class="sxs-lookup"><span data-stu-id="88753-114">hrtfapoapi.h</span></span>

<span data-ttu-id="88753-115">Per configurare il suono spaziale:</span><span class="sxs-lookup"><span data-stu-id="88753-115">To set up spatial sound:</span></span>
1. <span data-ttu-id="88753-116">Chiamare [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) per inizializzare un nuovo APO per audio HRTF.</span><span class="sxs-lookup"><span data-stu-id="88753-116">Call [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) to initialize a new APO for HRTF audio.</span></span>
2. <span data-ttu-id="88753-117">Assegnare i [parametri HRTF](https://msdn.microsoft.com/library/windows/desktop/mt186608.aspx) e l' [ambiente HRTF](https://msdn.microsoft.com/library/windows/desktop/mt186604.aspx) per definire le caratteristiche acustiche del sistema audio APO.</span><span class="sxs-lookup"><span data-stu-id="88753-117">Assign the [HRTF parameters](https://msdn.microsoft.com/library/windows/desktop/mt186608.aspx) and [HRTF environment](https://msdn.microsoft.com/library/windows/desktop/mt186604.aspx) to define the acoustic characteristics of the spatial sound APO.</span></span>
3. <span data-ttu-id="88753-118">Configurare il motore XAudio2 per l'elaborazione HRTF.</span><span class="sxs-lookup"><span data-stu-id="88753-118">Set up the XAudio2 engine for HRTF processing.</span></span>
4. <span data-ttu-id="88753-119">Creare un oggetto [IXAudio2SourceVoice](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.aspx) e chiamare [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx).</span><span class="sxs-lookup"><span data-stu-id="88753-119">Create an [IXAudio2SourceVoice](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.aspx) object and call [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx).</span></span>

## <a name="implementing-hrtf-and-spatial-sound-in-your-directx-app"></a><span data-ttu-id="88753-120">Implementazione di HRTF e del suono spaziale nell'app DirectX</span><span class="sxs-lookup"><span data-stu-id="88753-120">Implementing HRTF and spatial sound in your DirectX app</span></span>

<span data-ttu-id="88753-121">È possibile ottenere un'ampia gamma di effetti configurando HRTF APO con diversi parametri e ambienti.</span><span class="sxs-lookup"><span data-stu-id="88753-121">You can achieve a variety of effects by configuring the HRTF APO with different parameters and environments.</span></span> <span data-ttu-id="88753-122">Per esplorare le possibilità, usare il codice seguente.</span><span class="sxs-lookup"><span data-stu-id="88753-122">Use the following code to explore the possibilities.</span></span> <span data-ttu-id="88753-123">Scaricare l'esempio di codice piattaforma UWP (Universal Windows Platform) da qui: [Esempio di audio spaziale](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpatialSound)</span><span class="sxs-lookup"><span data-stu-id="88753-123">Download the Universal Windows Platform code sample from here: [Spatial sound sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpatialSound)</span></span>

<span data-ttu-id="88753-124">I tipi helper sono disponibili in questi file:</span><span class="sxs-lookup"><span data-stu-id="88753-124">Helper types are available in these files:</span></span>
* <span data-ttu-id="88753-125">[AudioFileReader. cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/AudioFileReader.cpp): Carica i file audio usando Media Foundation e l' [interfaccia IMFSourceReader](https://msdn.microsoft.com/library/windows/desktop/dd374655.aspx).</span><span class="sxs-lookup"><span data-stu-id="88753-125">[AudioFileReader.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/AudioFileReader.cpp): Loads audio files by using Media Foundation and the [IMFSourceReader interface](https://msdn.microsoft.com/library/windows/desktop/dd374655.aspx).</span></span>
* <span data-ttu-id="88753-126">[XAudio2Helpers. h](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/XAudio2Helpers.h): Implementa la funzione **SetupXAudio2** per inizializzare XAudio2 per l'elaborazione di HRTF.</span><span class="sxs-lookup"><span data-stu-id="88753-126">[XAudio2Helpers.h](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/XAudio2Helpers.h): Implements the **SetupXAudio2** function to initialize XAudio2 for HRTF processing.</span></span>

### <a name="add-spatial-sound-for-an-omnidirectional-source"></a><span data-ttu-id="88753-127">Aggiungere un suono spaziale per un'origine omnidirezionale</span><span class="sxs-lookup"><span data-stu-id="88753-127">Add spatial sound for an omnidirectional source</span></span>

<span data-ttu-id="88753-128">Alcuni ologrammi nell'ambiente dell'utente emettono suoni ugualmente in tutte le direzioni.</span><span class="sxs-lookup"><span data-stu-id="88753-128">Some holograms in the user's surroundings emit sound equally in all directions.</span></span> <span data-ttu-id="88753-129">Il codice seguente illustra come inizializzare un'espressione APO per emettere un suono omnidirezionale.</span><span class="sxs-lookup"><span data-stu-id="88753-129">The following code shows how to initialize an APO to emit omnidirectional sound.</span></span> <span data-ttu-id="88753-130">In questo esempio, questo concetto viene applicato al cubo rotante dal modello di app olografico di Windows.</span><span class="sxs-lookup"><span data-stu-id="88753-130">In this example, we apply this concept to the spinning cube from the Windows Holographic app template.</span></span> <span data-ttu-id="88753-131">Per il listato di codice completo, vedere [OmnidirectionalSound. cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/OmnidirectionalSound.cpp).</span><span class="sxs-lookup"><span data-stu-id="88753-131">For the complete code listing, see [OmnidirectionalSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/OmnidirectionalSound.cpp).</span></span>

<span data-ttu-id="88753-132">**Il motore audio spaziale della finestra supporta solo il campionamento 48.000 per la riproduzione. Per la maggior parte dei programmi middleware, come Unity, i file audio verranno convertiti automaticamente nel formato desiderato, ma se si inizia a eseguire la correzione a livelli inferiori nel sistema audio o se ne è stato personalizzato, è molto importante ricordarsi di evitare arresti anomali o comportamenti indesiderati come Errore di sistema HRTF.**</span><span class="sxs-lookup"><span data-stu-id="88753-132">**Window's spatial sound engine only supports 48k samplerate for playback. Most middleware programs, like Unity, will automatically convert sound files into the desired format, but if you start tinkering at lower levels in the audio system or making your own, this is very important to remember to prevent crashes or undesired behaviour like HRTF system failure.**</span></span>

<span data-ttu-id="88753-133">Prima di tutto, è necessario inizializzare APO.</span><span class="sxs-lookup"><span data-stu-id="88753-133">First, we need to initialize the APO.</span></span> <span data-ttu-id="88753-134">Nell'app di esempio olografica è possibile scegliere di eseguire questa operazione una volta **HolographicSpace**.</span><span class="sxs-lookup"><span data-stu-id="88753-134">In our holographic sample app, we choose to do this once we have the **HolographicSpace**.</span></span>

<span data-ttu-id="88753-135">Da *HolographicHrtfAudioSampleMain:: SetHolographicSpace ()* :</span><span class="sxs-lookup"><span data-stu-id="88753-135">From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:</span></span>

```
// Spatial sound
auto hr = m_omnidirectionalSound.Initialize(L"assets//MonoSound.wav");
```

<span data-ttu-id="88753-136">Implementazione di Initialize, da *OmnidirectionalSound. cpp*:</span><span class="sxs-lookup"><span data-stu-id="88753-136">The implementation of Initialize, from *OmnidirectionalSound.cpp*:</span></span>

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

<span data-ttu-id="88753-137">Dopo aver configurato APO per HRTF, chiamare [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) sulla voce di origine per riprodurre l'audio.</span><span class="sxs-lookup"><span data-stu-id="88753-137">After the APO is configured for HRTF, you call [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) on the source voice to play the audio.</span></span> <span data-ttu-id="88753-138">Nell'app di esempio, si sceglie di inserirla in un ciclo in modo che sia possibile continuare a udire il suono proveniente dal cubo.</span><span class="sxs-lookup"><span data-stu-id="88753-138">In our sample app, we choose to put it on a loop so that you can continue to hear the sound coming from the cube.</span></span>

<span data-ttu-id="88753-139">Da *HolographicHrtfAudioSampleMain:: SetHolographicSpace ()* :</span><span class="sxs-lookup"><span data-stu-id="88753-139">From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:</span></span>

```
if (SUCCEEDED(hr))
{
    m_omnidirectionalSound.SetEnvironment(HrtfEnvironment::Small);
    m_omnidirectionalSound.OnUpdate(m_spinningCubeRenderer->GetPosition());
    m_omnidirectionalSound.Start();
}
```

<span data-ttu-id="88753-140">Da *OmnidirectionalSound. cpp*:</span><span class="sxs-lookup"><span data-stu-id="88753-140">From *OmnidirectionalSound.cpp*:</span></span>

```
HRESULT OmnidirectionalSound::Start()
{
    _lastTick = GetTickCount64();
    return _sourceVoice->Start();
}
```

<span data-ttu-id="88753-141">A questo punto, ogni volta che si aggiorna il frame, è necessario aggiornare la posizione dell'ologramma in relazione al dispositivo stesso.</span><span class="sxs-lookup"><span data-stu-id="88753-141">Now, whenever we update the frame, we need to update the hologram's position relative to the device itself.</span></span> <span data-ttu-id="88753-142">Ciò è dovuto al fatto che le posizioni HRTF sono sempre espresse in relazione all'intestazione dell'utente, incluse la posizione e l'orientamento della testa.</span><span class="sxs-lookup"><span data-stu-id="88753-142">This is because HRTF positions are always expressed relative to the user's head, including the head position and orientation.</span></span>

<span data-ttu-id="88753-143">Per eseguire questa operazione in un HolographicSpace, è necessario creare una matrice di trasformazione dal sistema di coordinate SpatialStationaryFrameOfReference a un sistema di coordinate che viene fissato al dispositivo stesso.</span><span class="sxs-lookup"><span data-stu-id="88753-143">To do this in a HolographicSpace, we need to construct a transform matrix from our SpatialStationaryFrameOfReference coordinate system to a coordinate system that is fixed to the device itself.</span></span>

<span data-ttu-id="88753-144">Da *HolographicHrtfAudioSampleMain:: Update ()* :</span><span class="sxs-lookup"><span data-stu-id="88753-144">From *HolographicHrtfAudioSampleMain::Update()*:</span></span>

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

<span data-ttu-id="88753-145">La posizione HRTF viene applicata direttamente al suono APO dalla classe helper OmnidirectionalSound.</span><span class="sxs-lookup"><span data-stu-id="88753-145">The HRTF position is applied directly to the sound APO by the OmnidirectionalSound helper class.</span></span>

<span data-ttu-id="88753-146">Da *OmnidirectionalSound:: OnUpdate*:</span><span class="sxs-lookup"><span data-stu-id="88753-146">From *OmnidirectionalSound::OnUpdate*:</span></span>

```
HRESULT OmnidirectionalSound::OnUpdate(_In_ Numerics::float3 position)
{
    auto hrtfPosition = HrtfPosition{ position.x, position.y, position.z };
    return _hrtfParams->SetSourcePosition(&hrtfPosition);
}
```

<span data-ttu-id="88753-147">La procedura è terminata.</span><span class="sxs-lookup"><span data-stu-id="88753-147">That's it!</span></span> <span data-ttu-id="88753-148">Continuare a leggere per altre informazioni sulle operazioni che è possibile eseguire con HRTF audio e Windows olografico.</span><span class="sxs-lookup"><span data-stu-id="88753-148">Continue reading to learn more about what you can do with HRTF audio and Windows Holographic.</span></span>

### <a name="initialize-spatial-sound-for-a-directional-source"></a><span data-ttu-id="88753-149">Inizializzare il suono spaziale per un'origine direzionale</span><span class="sxs-lookup"><span data-stu-id="88753-149">Initialize spatial sound for a directional source</span></span>

<span data-ttu-id="88753-150">Alcuni ologrammi nell'ambiente dell'utente emettono suoni principalmente in un'unica direzione.</span><span class="sxs-lookup"><span data-stu-id="88753-150">Some holograms in the user's surroundings emit sound mostly in one direction.</span></span> <span data-ttu-id="88753-151">Questo modello audio è denominato *cardioide* perché sembra un cuore animato.</span><span class="sxs-lookup"><span data-stu-id="88753-151">This sound pattern is named *cardioid* because it looks like a cartoon heart.</span></span> <span data-ttu-id="88753-152">Nel codice riportato di seguito viene illustrato come inizializzare un'espressione APO per emettere un suono direzionale.</span><span class="sxs-lookup"><span data-stu-id="88753-152">The following code shows how to initialize an APO to emit directional sound.</span></span> <span data-ttu-id="88753-153">Per il listato di codice completo, vedere [CardioidSound. cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CardioidSound.cpp) .</span><span class="sxs-lookup"><span data-stu-id="88753-153">For the complete code listing, see [CardioidSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CardioidSound.cpp) .</span></span>

<span data-ttu-id="88753-154">Dopo aver configurato APO per HRTF, chiamare [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) sulla voce di origine per riprodurre l'audio.</span><span class="sxs-lookup"><span data-stu-id="88753-154">After the APO is configured for HRTF, call [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) on the source voice to play the audio.</span></span>

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

### <a name="implement-custom-decay"></a><span data-ttu-id="88753-155">Implementare il decadimento personalizzato</span><span class="sxs-lookup"><span data-stu-id="88753-155">Implement custom decay</span></span>

<span data-ttu-id="88753-156">È possibile eseguire l'override della frequenza con cui un suono spaziale si interrompe con la distanza e/o la distanza in cui si interrompe completamente.</span><span class="sxs-lookup"><span data-stu-id="88753-156">You can override the rate at which a spatial sound falls off with distance and/or at what distance it cuts off completely.</span></span> <span data-ttu-id="88753-157">Per implementare un comportamento di decadimento personalizzato su un suono spaziale, popolare uno [struct HrtfDistanceDecay](https://msdn.microsoft.com/library/windows/desktop/mt186602.aspx) e assegnarlo al campo **distanceDecay** in uno [struct HrtfApoInit](https://msdn.microsoft.com/library/windows/desktop/mt186597.aspx) prima di passarlo alla funzione [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) .</span><span class="sxs-lookup"><span data-stu-id="88753-157">To implement custom decay behavior on a spatial sound, populate an [HrtfDistanceDecay struct](https://msdn.microsoft.com/library/windows/desktop/mt186602.aspx) and assign it to the **distanceDecay** field in an [HrtfApoInit struct](https://msdn.microsoft.com/library/windows/desktop/mt186597.aspx) before passing it to the [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) function.</span></span>

<span data-ttu-id="88753-158">Aggiungere il codice seguente al metodo **Initialize** illustrato in precedenza per specificare il comportamento di decadimento personalizzato.</span><span class="sxs-lookup"><span data-stu-id="88753-158">Add the following code to the **Initialize** method shown previously to specify custom decay behavior.</span></span> <span data-ttu-id="88753-159">Per il listato di codice completo, vedere [CustomDecay. cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CustomDecay.cpp).</span><span class="sxs-lookup"><span data-stu-id="88753-159">For the complete code listing, see [CustomDecay.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CustomDecay.cpp).</span></span>

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

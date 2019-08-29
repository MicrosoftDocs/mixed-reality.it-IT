---
title: Sguardo in DirectX
description: Guida per gli sviluppatori per l'uso degli sguardi e degli occhi nelle app DirectX native.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 05/09/2019
ms.topic: article
keywords: occhio, sguardo, Head-sguardi, tracking, tracciamento degli occhi, DirectX, input, ologrammi
ms.openlocfilehash: 2197f0ba3ecb77188d532d77ba29595c380a039d
ms.sourcegitcommit: ff330a7e36e5ff7ae0e9a08c0e99eb7f3f81361f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/28/2019
ms.locfileid: "70122053"
---
# <a name="head-gaze-and-eye-gaze-input-in-directx"></a><span data-ttu-id="55cd6-104">Input occhi e sguardi in DirectX</span><span class="sxs-lookup"><span data-stu-id="55cd6-104">Head-gaze and eye-gaze input in DirectX</span></span>

<span data-ttu-id="55cd6-105">Per quanto riguarda la realtà mista di Windows, viene usato l'input occhi e occhio per determinare l'aspetto dell'utente.</span><span class="sxs-lookup"><span data-stu-id="55cd6-105">In Windows Mixed Reality, eye and head gaze input is used to determine what the user is looking at.</span></span> <span data-ttu-id="55cd6-106">Questo può essere usato per gestire i modelli di input primari, ad esempio [Head-sguardi e commit](gaze-and-commit.md), nonché per fornire il contesto per i tipi di interazioni.</span><span class="sxs-lookup"><span data-stu-id="55cd6-106">This can be used to drive primary input models such as [head-gaze and commit](gaze-and-commit.md), and also to provide context for types of interactions.</span></span> <span data-ttu-id="55cd6-107">Esistono due tipi di vettori di sguardi disponibili tramite l'API, ovvero Head-sguardi e sguardo.</span><span class="sxs-lookup"><span data-stu-id="55cd6-107">There are two types of gaze vectors available through the API: head-gaze and eye-gaze.</span></span>  <span data-ttu-id="55cd6-108">Entrambe sono fornite come un raggio tridimensionale con un'origine e una direzione.</span><span class="sxs-lookup"><span data-stu-id="55cd6-108">Both are provided as a three dimensional ray with an origin and direction.</span></span> <span data-ttu-id="55cd6-109">Le applicazioni possono quindi Raycast nelle proprie scene, o nel mondo reale, e determinare le operazioni di destinazione dell'utente.</span><span class="sxs-lookup"><span data-stu-id="55cd6-109">Applications can then raycast into their scenes, or the real world, and determine what the user is targeting.</span></span>

<span data-ttu-id="55cd6-110">**Head-sguardi** rappresenta la direzione a cui è puntata la testa dell'utente.</span><span class="sxs-lookup"><span data-stu-id="55cd6-110">**Head-gaze** represents the direction that the user's head is pointed in.</span></span> <span data-ttu-id="55cd6-111">Si pensi a questo come la posizione e la direzione di avanzamento del dispositivo stesso, con la posizione che rappresenta il punto centrale tra le due visualizzazioni.</span><span class="sxs-lookup"><span data-stu-id="55cd6-111">Think of this as the position and forward direction of the device itself, with the position representing the center point between the two displays.</span></span> <span data-ttu-id="55cd6-112">Head-sguardi è disponibile in tutti i dispositivi a realtà mista.</span><span class="sxs-lookup"><span data-stu-id="55cd6-112">Head-gaze is available on all Mixed Reality devices.</span></span>

<span data-ttu-id="55cd6-113">**Eye-sguardi** rappresenta la direzione verso la quale gli occhi dell'utente stanno cercando.</span><span class="sxs-lookup"><span data-stu-id="55cd6-113">**Eye-gaze** represents the direction that the user's eyes are looking towards.</span></span> <span data-ttu-id="55cd6-114">L'origine si trova tra gli occhi dell'utente.</span><span class="sxs-lookup"><span data-stu-id="55cd6-114">The origin is located between the user's eyes.</span></span>  <span data-ttu-id="55cd6-115">È disponibile nei dispositivi a realtà mista che includono un sistema di rilevamento degli occhi.</span><span class="sxs-lookup"><span data-stu-id="55cd6-115">It is available on Mixed Reality devices that include an eye tracking system.</span></span>

<span data-ttu-id="55cd6-116">I raggi Head e sguardi sono accessibili tramite l'API [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) .</span><span class="sxs-lookup"><span data-stu-id="55cd6-116">Both head and eye-gaze rays are accessible through the  [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API.</span></span> <span data-ttu-id="55cd6-117">È sufficiente chiamare [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) per ricevere un nuovo oggetto SpatialPointerPose in corrispondenza del timestamp e del [sistema di coordinate](coordinate-systems-in-directx.md)specificati.</span><span class="sxs-lookup"><span data-stu-id="55cd6-117">Simply call [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object at the specified timestamp and [coordinate system](coordinate-systems-in-directx.md).</span></span> <span data-ttu-id="55cd6-118">Questo SpatialPointerPose contiene un'origine e una direzione per lo sguardo del capo.</span><span class="sxs-lookup"><span data-stu-id="55cd6-118">This SpatialPointerPose contains a head-gaze origin and direction.</span></span> <span data-ttu-id="55cd6-119">Contiene anche un'origine e una direzione degli sguardi se è disponibile la verifica degli occhi.</span><span class="sxs-lookup"><span data-stu-id="55cd6-119">It also contains an eye-gaze origin and direction if eye tracking is available.</span></span>

## <a name="using-head-gaze"></a><span data-ttu-id="55cd6-120">Uso di Head-sguardi</span><span class="sxs-lookup"><span data-stu-id="55cd6-120">Using head-gaze</span></span>

<span data-ttu-id="55cd6-121">Per accedere all'Head-sguardi, iniziare chiamando [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) per ricevere un nuovo oggetto SpatialPointerPose.</span><span class="sxs-lookup"><span data-stu-id="55cd6-121">To access the head-gaze, start by calling  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object.</span></span> <span data-ttu-id="55cd6-122">È necessario passare i parametri seguenti.</span><span class="sxs-lookup"><span data-stu-id="55cd6-122">You need to pass the following parameters.</span></span>
 - <span data-ttu-id="55cd6-123">Oggetto [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) che rappresenta il sistema di coordinate desiderato per lo sguardo Head.</span><span class="sxs-lookup"><span data-stu-id="55cd6-123">A [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) that represents the desired coordinate system for the head-gaze.</span></span> <span data-ttu-id="55cd6-124">Questa operazione è rappresentata dalla variabile *coordinateSystem* nel codice riportato di seguito.</span><span class="sxs-lookup"><span data-stu-id="55cd6-124">This is represented by the *coordinateSystem* variable in the following code.</span></span> <span data-ttu-id="55cd6-125">Per ulteriori informazioni, visitare la guida per gli sviluppatori di [sistemi di coordinate](coordinate-systems-in-directx.md) .</span><span class="sxs-lookup"><span data-stu-id="55cd6-125">For more information, visit our [coordinate systems](coordinate-systems-in-directx.md) developer guide.</span></span>
 - <span data-ttu-id="55cd6-126">[Timestamp](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) che rappresenta l'ora esatta della richiesta Head.</span><span class="sxs-lookup"><span data-stu-id="55cd6-126">A [Timestamp](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) that represents the exact time of the head pose requested.</span></span>  <span data-ttu-id="55cd6-127">Viene in genere utilizzato un timestamp corrispondente all'ora in cui verrà visualizzato il frame corrente.</span><span class="sxs-lookup"><span data-stu-id="55cd6-127">Typically you will use a timestamp that corresponds to the time when the current frame will be displayed.</span></span> <span data-ttu-id="55cd6-128">È possibile ottenere questo timestamp di visualizzazione stimato da un oggetto [HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) , accessibile tramite il [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe)corrente.</span><span class="sxs-lookup"><span data-stu-id="55cd6-128">You can get this predicted display timestamp from a  [HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) object, which is accessible through the current [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe).</span></span>  <span data-ttu-id="55cd6-129">Questo oggetto HolographicFramePrediction è rappresentato dalla variabile di *stima* nel codice riportato di seguito.</span><span class="sxs-lookup"><span data-stu-id="55cd6-129">This HolographicFramePrediction object is represented by the *prediction* variable in the following code.</span></span>

 <span data-ttu-id="55cd6-130">Quando si dispone di un SpatialPointerPose valido, la posizione della testa e la direzione di avanzamento sono accessibili come proprietà.</span><span class="sxs-lookup"><span data-stu-id="55cd6-130">Once you have a valid SpatialPointerPose, the head position and forward direction are accessible as properties.</span></span>  <span data-ttu-id="55cd6-131">Nel codice seguente viene illustrato come accedervi.</span><span class="sxs-lookup"><span data-stu-id="55cd6-131">The following code  shows how to access them.</span></span>

 ```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    float3 headPosition = pointerPose.Head().Position();
    float3 headForwardDirection = pointerPose.Head().ForwardDirection();

    // Do something with the head-gaze
}
```

## <a name="using-eye-gaze"></a><span data-ttu-id="55cd6-132">Uso degli sguardi</span><span class="sxs-lookup"><span data-stu-id="55cd6-132">Using eye-gaze</span></span>

<span data-ttu-id="55cd6-133">L'API Eye-sguardi è molto simile a Head-sguardi.</span><span class="sxs-lookup"><span data-stu-id="55cd6-133">The eye-gaze API is very similar to head-gaze.</span></span>  <span data-ttu-id="55cd6-134">Usa la stessa API [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) , che fornisce un'origine e una direzione del raggio che è possibile Raycast per la scena.</span><span class="sxs-lookup"><span data-stu-id="55cd6-134">It uses the same  [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API, which provides a ray origin and direction that you can raycast against your scene.</span></span>  <span data-ttu-id="55cd6-135">L'unica differenza è che è necessario abilitare in modo esplicito il rilevamento degli occhi prima di usarlo.</span><span class="sxs-lookup"><span data-stu-id="55cd6-135">The only difference is that you need to explicitly enable eye tracking before using it.</span></span> <span data-ttu-id="55cd6-136">A tale scopo, è necessario eseguire due passaggi:</span><span class="sxs-lookup"><span data-stu-id="55cd6-136">For this, you need to do two steps:</span></span>
1. <span data-ttu-id="55cd6-137">Richiedere all'utente l'autorizzazione per usare il rilevamento degli occhi nell'app.</span><span class="sxs-lookup"><span data-stu-id="55cd6-137">Request user permission to use eye tracking in your app.</span></span>
2. <span data-ttu-id="55cd6-138">Abilitare la funzionalità di "input dello sguardo" nel manifesto del pacchetto.</span><span class="sxs-lookup"><span data-stu-id="55cd6-138">Enable the "Gaze Input" capability in your package manifest.</span></span>

### <a name="requesting-access-to-eye-gaze-input"></a><span data-ttu-id="55cd6-139">Richiesta di accesso a Eye-sguardi input</span><span class="sxs-lookup"><span data-stu-id="55cd6-139">Requesting access to eye-gaze input</span></span>
<span data-ttu-id="55cd6-140">All'avvio dell'app, chiamare [EyesPose:: RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) per richiedere l'accesso al rilevamento degli occhi.</span><span class="sxs-lookup"><span data-stu-id="55cd6-140">When your app is starting up, call [EyesPose::RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) to request access to eye tracking.</span></span> <span data-ttu-id="55cd6-141">Se necessario, il sistema richiede all'utente e restituisce [GazeInputAccessStatus:: allowed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus) dopo che è stato concesso l'accesso.</span><span class="sxs-lookup"><span data-stu-id="55cd6-141">The system will prompt the user if needed, and return [GazeInputAccessStatus::Allowed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus) once access has been granted.</span></span> <span data-ttu-id="55cd6-142">Si tratta di una chiamata asincrona, quindi richiede un po' di gestione aggiuntiva.</span><span class="sxs-lookup"><span data-stu-id="55cd6-142">This is an asynchronous call, so it requires a bit of extra management.</span></span> <span data-ttu-id="55cd6-143">Nell'esempio seguente viene avviata un'operazione std:: thread scollegata per attendere il risultato, che viene archiviato in una variabile membro denominata *m_isEyeTrackingEnabled*.</span><span class="sxs-lookup"><span data-stu-id="55cd6-143">The following example spins up a detached std::thread to wait for the result, which it stores to a member variable called *m_isEyeTrackingEnabled*.</span></span>

```cpp
using namespace winrt::Windows::Perception::People;
using namespace winrt::Windows::UI::Input;

std::thread requestAccessThread([this]()
{
    auto status = EyesPose::RequestAccessAsync().get();

    if (status == GazeInputAccessStatus::Allowed)
        m_isEyeTrackingEnabled = true;
    else
        m_isEyeTrackingEnabled = false;
});

requestAccessThread.detach();

```
<span data-ttu-id="55cd6-144">L'avvio di un thread scollegato è solo un'opzione per la gestione delle chiamate asincrone.</span><span class="sxs-lookup"><span data-stu-id="55cd6-144">Starting a detached thread is just one option for handling async calls.</span></span>  <span data-ttu-id="55cd6-145">In alternativa, è possibile usare la nuova funzionalità [co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) supportata da C++/WinRT.</span><span class="sxs-lookup"><span data-stu-id="55cd6-145">Alternatively, you could use the new [co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) functionality supported by C++/WinRT.</span></span>
<span data-ttu-id="55cd6-146">Di seguito è riportato un altro esempio per richiedere l'autorizzazione utente:</span><span class="sxs-lookup"><span data-stu-id="55cd6-146">Here is another example for asking for user permission:</span></span>
-   <span data-ttu-id="55cd6-147">EyesPose:: supporto () consente all'applicazione di attivare la finestra di dialogo di autorizzazione solo se è presente uno strumento di rilevamento.</span><span class="sxs-lookup"><span data-stu-id="55cd6-147">EyesPose::IsSupported() allows the application to trigger the permission dialog only if there is an eye tracker.</span></span>
-   <span data-ttu-id="55cd6-148">GazeInputAccessStatus m_gazeInputAccessStatus; In questo modo si evita di riscattare il prompt delle autorizzazioni più volte.</span><span class="sxs-lookup"><span data-stu-id="55cd6-148">GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.</span></span>

```cpp
GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.

// This will trigger to show the permission prompt to the user.
// Ask for access if there is a corresponding device and registry flag did not disable it.
if (Windows::Perception::People::EyesPose::IsSupported() &&
   (m_gazeInputAccessStatus == GazeInputAccessStatus::Unspecified))
{ 
    Concurrency::create_task(Windows::Perception::People::EyesPose::RequestAccessAsync()).then(
    [this](GazeInputAccessStatus status)
    {
        // GazeInputAccessStatus::{Allowed, DeniedBySystem, DeniedByUser, Unspecified}
            m_gazeInputAccessStatus = status;
        
        // Let's be sure to not ask again.
        if(status == GazeInputAccessStatus::Unspecified)
        {
                m_gazeInputAccessStatus = GazeInputAccessStatus::DeniedBySystem;    
        }
    });
}

```


### <a name="declaring-the-gaze-input-capability"></a><span data-ttu-id="55cd6-149">Dichiarazione della funzionalità di *input di sguardi*</span><span class="sxs-lookup"><span data-stu-id="55cd6-149">Declaring the *Gaze Input* capability</span></span>

<span data-ttu-id="55cd6-150">Fare doppio clic sul file appxmanifest in *Esplora soluzioni*.</span><span class="sxs-lookup"><span data-stu-id="55cd6-150">Double click the appxmanifest file in *Solution Explorer*.</span></span>  <span data-ttu-id="55cd6-151">Passare quindi alla sezione *funzionalità* e controllare la funzionalità di *input di sguardi* .</span><span class="sxs-lookup"><span data-stu-id="55cd6-151">Then navigate to the *Capabilities* section and check the *Gaze Input* capability.</span></span> 

![Funzionalità di input di sguardi](images/gaze-input-capability.png)

<span data-ttu-id="55cd6-153">Vengono aggiunte le righe seguenti alla sezione del *pacchetto* nel file appxmanifest:</span><span class="sxs-lookup"><span data-stu-id="55cd6-153">This adds the following lines to the *Package* section in the appxmanifest file:</span></span>
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a><span data-ttu-id="55cd6-154">Ottenere il raggio d'occhio</span><span class="sxs-lookup"><span data-stu-id="55cd6-154">Getting the eye-gaze ray</span></span>
<span data-ttu-id="55cd6-155">Dopo aver ricevuto l'accesso a ET, è possibile cogliere il raggio d'occhio per ogni fotogramma.</span><span class="sxs-lookup"><span data-stu-id="55cd6-155">Once you have received access to ET, you are free to grab the eye-gaze ray every frame.</span></span>
<span data-ttu-id="55cd6-156">Come per gli occhi, ottenere il [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) chiamando [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) con un timestamp e un sistema di coordinate desiderati.</span><span class="sxs-lookup"><span data-stu-id="55cd6-156">Just as with head-gaze, get the [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) by calling [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with a desired timestamp and coordinate system.</span></span> <span data-ttu-id="55cd6-157">SpatialPointerPose contiene un oggetto [EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) tramite la proprietà [Eyes](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) .</span><span class="sxs-lookup"><span data-stu-id="55cd6-157">The SpatialPointerPose contains an [EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) object through the [Eyes](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) property.</span></span> <span data-ttu-id="55cd6-158">Questo valore non è null solo se è abilitata la funzionalità Eye Tracking.</span><span class="sxs-lookup"><span data-stu-id="55cd6-158">This is non-null only if eye tracking is enabled.</span></span> <span data-ttu-id="55cd6-159">Da qui è possibile verificare se l'utente nel dispositivo ha una calibrazione del rilevamento degli occhi chiamando [EyesPose:: IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).</span><span class="sxs-lookup"><span data-stu-id="55cd6-159">From there you can check if the user in the device has an eye tracking calibration by calling [EyesPose::IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).</span></span>  <span data-ttu-id="55cd6-160">Usare quindi la proprietà [sguardi](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) per ottenere la posizione e la direzione di un [SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) .</span><span class="sxs-lookup"><span data-stu-id="55cd6-160">Next, use the [Gaze](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) property to get the a [SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) contianing the eye-gaze position and direction.</span></span> <span data-ttu-id="55cd6-161">La proprietà sguardi può talvolta essere null, quindi assicurarsi di controllarla.</span><span class="sxs-lookup"><span data-stu-id="55cd6-161">The Gaze property can sometimes be null, so be sure to check for this.</span></span> <span data-ttu-id="55cd6-162">Questo problema può verificarsi se un utente calibrato chiude temporaneamente gli occhi.</span><span class="sxs-lookup"><span data-stu-id="55cd6-162">This can happen is if a calibrated user temporarily closes their eyes.</span></span>

<span data-ttu-id="55cd6-163">Il codice seguente illustra come accedere al raggio d'occhio.</span><span class="sxs-lookup"><span data-stu-id="55cd6-163">The following code shows how to access the eye-gaze ray.</span></span>

```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    if (pointerPose.Eyes() && pointerPose.Eyes().IsCalibrationValid())
    {
        if (pointerPose.Eyes().Gaze())
        {
            auto spatialRay = pointerPose.Eyes().Gaze().Value();
            float3 eyeGazeOrigin = spatialRay.Origin;
            float3 eyeGazeDirection = spatialRay.Direction;
            
            // Do something with the eye-gaze
        }
    }
}

```

## <a name="correlating-gaze-with-other-inputs"></a><span data-ttu-id="55cd6-164">Correlazione di sguardi con altri input</span><span class="sxs-lookup"><span data-stu-id="55cd6-164">Correlating gaze with other inputs</span></span>

<span data-ttu-id="55cd6-165">In alcuni casi potrebbe essere necessario un [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) che corrisponda a un evento nel passato.</span><span class="sxs-lookup"><span data-stu-id="55cd6-165">Sometimes you may find that you need a [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) that corresponds with an event in the past.</span></span> <span data-ttu-id="55cd6-166">Ad esempio, se l'utente esegue una scelta aerea, l'app potrebbe voler sapere cosa stavano cercando.</span><span class="sxs-lookup"><span data-stu-id="55cd6-166">For example, if the user performs an Air Tap, your app might want to know what they were looking at.</span></span> <span data-ttu-id="55cd6-167">A questo scopo, l'uso di [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) con il tempo previsto per i frame potrebbe non essere accurato a causa della latenza tra l'elaborazione dell'input di sistema e l'ora di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="55cd6-167">For this purpose, simply using [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with the predicted frame time would be inaccurate because of the latency between system input processing and display time.</span></span> <span data-ttu-id="55cd6-168">Inoltre, se si usa il controllo degli sguardi per la destinazione, gli occhi tendono a proseguire anche prima di terminare un'azione di commit.</span><span class="sxs-lookup"><span data-stu-id="55cd6-168">In addition, if using eye-gaze for targeting, our eyes tend to move on even before finishing a commit action.</span></span> <span data-ttu-id="55cd6-169">Si tratta di un problema minore per un semplice tocco, ma diventa più importante quando si combinano i comandi Long Voice con rapidi movimenti oculari.</span><span class="sxs-lookup"><span data-stu-id="55cd6-169">This is less of an issue for a simple Air Tap, but becomes more critical when combining long voice commands with fast eye movements.</span></span> <span data-ttu-id="55cd6-170">Un modo per gestire questo scenario è eseguire un'ulteriore chiamata a [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), usando un timestamp cronologico corrispondente all'evento di input.</span><span class="sxs-lookup"><span data-stu-id="55cd6-170">One way to handle this scenario is to make an additional call to  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), using a historical timestamp that corresponds to the input event.</span></span>  

<span data-ttu-id="55cd6-171">Tuttavia, per l'input che viene indirizzato attraverso SpatialInteractionManager, è disponibile un metodo più semplice.</span><span class="sxs-lookup"><span data-stu-id="55cd6-171">However, for input that routes through the SpatialInteractionManager, there's an easier method.</span></span> <span data-ttu-id="55cd6-172">[SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) dispone di una propria funzione [TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) .</span><span class="sxs-lookup"><span data-stu-id="55cd6-172">The [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) has its very own [TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) function.</span></span> <span data-ttu-id="55cd6-173">Chiamando che fornirà un [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) perfettamente correlato senza le congetture.</span><span class="sxs-lookup"><span data-stu-id="55cd6-173">Calling that will provide a perfectly correlated [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) without the guesswork.</span></span> <span data-ttu-id="55cd6-174">Per altre informazioni sull'uso di SpatialInteractionSourceStates, vedere la documentazione su [hands and Motion Controllers in DirectX](hands-and-motion-controllers-in-directx.md) .</span><span class="sxs-lookup"><span data-stu-id="55cd6-174">For more information on working with SpatialInteractionSourceStates, take a look at the [Hands and Motion Controllers in DirectX](hands-and-motion-controllers-in-directx.md) documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="55cd6-175">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="55cd6-175">See also</span></span>
* [<span data-ttu-id="55cd6-176">Modello di input Head-sguardi e commit</span><span class="sxs-lookup"><span data-stu-id="55cd6-176">Head-gaze and commit input model</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="55cd6-177">Eye-sguardi su HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="55cd6-177">Eye-gaze on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="55cd6-178">Calibrazione</span><span class="sxs-lookup"><span data-stu-id="55cd6-178">Calibration</span></span>](calibration.md)
* [<span data-ttu-id="55cd6-179">Sistemi di coordinate in DirectX</span><span class="sxs-lookup"><span data-stu-id="55cd6-179">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="55cd6-180">Input vocale in DirectX</span><span class="sxs-lookup"><span data-stu-id="55cd6-180">Voice Input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="55cd6-181">Mani e controller del movimento in DirectX</span><span class="sxs-lookup"><span data-stu-id="55cd6-181">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)

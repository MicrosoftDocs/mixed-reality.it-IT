---
title: Testa e occhio estasiati DirectX
description: Guida per sviluppatori per l'uso sguardo head e sotto controllo di rilevamento in native nelle App DirectX.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 05/09/2019
ms.topic: article
keywords: sguardo, head sguardo, head di rilevamento, sotto controllo di rilevamento, directx, input, vntana
ms.openlocfilehash: edf20a621178d76bfc97477f9f9b2eca200f1318
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414414"
---
# <a name="head-and-eye-gaze-input-in-directx"></a><span data-ttu-id="3f232-104">Testa e occhio estasiati input DirectX</span><span class="sxs-lookup"><span data-stu-id="3f232-104">Head and eye gaze input in DirectX</span></span>

<span data-ttu-id="3f232-105">In realtà mista di Windows, occhio e head sguardo input viene usato per determinare cosa sta guardando l'utente.</span><span class="sxs-lookup"><span data-stu-id="3f232-105">In Windows Mixed Reality, eye and head gaze input is used to determine what the user is looking at.</span></span> <span data-ttu-id="3f232-106">Ciò può essere utilizzato per guidare i modelli di input primari, ad esempio [head sguardo ed eseguire il commit](gaze-and-commit.md)e anche per fornire il contesto per i tipi di interazioni.</span><span class="sxs-lookup"><span data-stu-id="3f232-106">This can be used to drive primary input models such as [head gaze and commit](gaze-and-commit.md), and also to provide context for types of interactions.</span></span> <span data-ttu-id="3f232-107">Esistono due tipi di sguardo vettori disponibili tramite l'API: head sguardo e sguardo sotto controllo.</span><span class="sxs-lookup"><span data-stu-id="3f232-107">There are two types of gaze vectors available through the API: head gaze and eye gaze.</span></span>  <span data-ttu-id="3f232-108">Entrambi sono specificati come una tre ray dimensionale con un'origine e la direzione.</span><span class="sxs-lookup"><span data-stu-id="3f232-108">Both are provided as a three dimensional ray with an origin and direction.</span></span> <span data-ttu-id="3f232-109">Le applicazioni possono quindi raycast le scene o reale e determinare cosa è destinato all'utente.</span><span class="sxs-lookup"><span data-stu-id="3f232-109">Applications can then raycast into their scenes, or the real world, and determine what the user is targeting.</span></span>

<span data-ttu-id="3f232-110">**Head estasiati** rappresenta la direzione che punta in head dell'utente.</span><span class="sxs-lookup"><span data-stu-id="3f232-110">**Head gaze** represents the direction that the user's head is pointed in.</span></span> <span data-ttu-id="3f232-111">È possibile scegliere la posizione e la direzione in avanti dei dispositivi, con la posizione che rappresenta il centro di scegliere tra le due visualizzazioni.</span><span class="sxs-lookup"><span data-stu-id="3f232-111">Think of this as the position and forward direction of the device itself, with the position representing the center point between the two displays.</span></span>  <span data-ttu-id="3f232-112">Sguardo HEAD è disponibile in tutti i dispositivi di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="3f232-112">Head gaze is available on all Mixed Reality devices.</span></span>

<span data-ttu-id="3f232-113">**Sguardo occhio** rappresenta la direzione che desiderano verso gli occhi dell'utente.</span><span class="sxs-lookup"><span data-stu-id="3f232-113">**Eye gaze** represents the direction that the user's eyes are looking towards.</span></span> <span data-ttu-id="3f232-114">L'origine si trova tra gli occhi dell'utente.</span><span class="sxs-lookup"><span data-stu-id="3f232-114">The origin is located between the user's eyes.</span></span>  <span data-ttu-id="3f232-115">È disponibile nei dispositivi di realtà mista che includono un occhio di sistema di registrazione.</span><span class="sxs-lookup"><span data-stu-id="3f232-115">It is available on Mixed Reality devices that include an eye tracking system.</span></span>

<span data-ttu-id="3f232-116">Head sia occhio rays sguardo sono accessibili tramite il [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API.</span><span class="sxs-lookup"><span data-stu-id="3f232-116">Both head and eye gaze rays are accessible through the  [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API.</span></span> <span data-ttu-id="3f232-117">È sufficiente chiamare [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) per ricevere un nuovo oggetto SpatialPointerPose al timestamp specificato e [sistema di coordinate](coordinate-systems-in-directx.md).</span><span class="sxs-lookup"><span data-stu-id="3f232-117">Simply call [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object at the specified timestamp and [coordinate system](coordinate-systems-in-directx.md).</span></span> <span data-ttu-id="3f232-118">Questo SpatialPointerPose contiene un'origine sguardo head e la direzione.</span><span class="sxs-lookup"><span data-stu-id="3f232-118">This SpatialPointerPose contains a head gaze origin and direction.</span></span> <span data-ttu-id="3f232-119">Contiene anche un occhio sguardo origine e la direzione se è disponibile sotto controllo di rilevamento.</span><span class="sxs-lookup"><span data-stu-id="3f232-119">It also contains an eye gaze origin and direction if eye tracking is available.</span></span>

## <a name="using-head-gaze"></a><span data-ttu-id="3f232-120">Usando sguardo head</span><span class="sxs-lookup"><span data-stu-id="3f232-120">Using head gaze</span></span>

<span data-ttu-id="3f232-121">Per accedere la sguardo head, avviare chiamando [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) per ricevere un nuovo oggetto SpatialPointerPose.</span><span class="sxs-lookup"><span data-stu-id="3f232-121">To access the head gaze, start by calling  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object.</span></span> <span data-ttu-id="3f232-122">È necessario passare i parametri seguenti.</span><span class="sxs-lookup"><span data-stu-id="3f232-122">You need to pass the following parameters.</span></span>
 - <span data-ttu-id="3f232-123">Oggetto [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) che rappresenta il sistema di coordinate desiderato per lo sguardo head.</span><span class="sxs-lookup"><span data-stu-id="3f232-123">A [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) that represents the desired coordinate system for the head gaze.</span></span> <span data-ttu-id="3f232-124">Ciò è rappresentato dal *sistema di coordinate* variabile nel codice seguente.</span><span class="sxs-lookup"><span data-stu-id="3f232-124">This is represented by the *coordinateSystem* variable in the following code.</span></span> <span data-ttu-id="3f232-125">Per altre informazioni, visitare il nostro [sistemi di coordinate](coordinate-systems-in-directx.md) Guida per gli sviluppatori.</span><span class="sxs-lookup"><span data-stu-id="3f232-125">For more information, visit our [coordinate systems](coordinate-systems-in-directx.md) developer guide.</span></span>
 - <span data-ttu-id="3f232-126">Oggetto [Timestamp](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) che rappresenta l'ora esatta della posa head richiesta.</span><span class="sxs-lookup"><span data-stu-id="3f232-126">A [Timestamp](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) that represents the exact time of the head pose requested.</span></span>  <span data-ttu-id="3f232-127">In genere si utilizzerà un timestamp che corrisponde al tempo quando verrà visualizzato il frame corrente.</span><span class="sxs-lookup"><span data-stu-id="3f232-127">Typically you will use a timestamp that corresponds to the time when the current frame will be displayed.</span></span> <span data-ttu-id="3f232-128">È possibile ottenere questo timestamp previste per la visualizzazione da un [HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) oggetto, che è accessibile tramite l'istanza corrente [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe).</span><span class="sxs-lookup"><span data-stu-id="3f232-128">You can get this predicted display timestamp from a  [HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) object, which is accessible through the current [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe).</span></span>  <span data-ttu-id="3f232-129">Questo oggetto HolographicFramePrediction è rappresentato dal *stima* variabile nel codice seguente.</span><span class="sxs-lookup"><span data-stu-id="3f232-129">This HolographicFramePrediction object is represented by the *prediction* variable in the following code.</span></span>

 <span data-ttu-id="3f232-130">Dopo aver creato un SpatialPointerPose valido, la posizione head e la direzione in avanti sono accessibili come proprietà.</span><span class="sxs-lookup"><span data-stu-id="3f232-130">Once you have a valid SpatialPointerPose, the head position and forward direction are accessible as properties.</span></span>  <span data-ttu-id="3f232-131">Il codice seguente viene illustrato come accedervi.</span><span class="sxs-lookup"><span data-stu-id="3f232-131">The following code  shows how to access them.</span></span>

 ```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    float3 headPosition = pointerPose.Head().Position();
    float3 headForwardDirection = pointerPose.Head().ForwardDirection();

    // Do something with the head gaze
}
```

## <a name="using-eye-gaze"></a><span data-ttu-id="3f232-132">Usando sguardo sotto controllo</span><span class="sxs-lookup"><span data-stu-id="3f232-132">Using eye gaze</span></span>

<span data-ttu-id="3f232-133">L'API di sguardo occhio è molto simile a sguardo head.</span><span class="sxs-lookup"><span data-stu-id="3f232-133">The eye gaze API is very similar to head gaze.</span></span>  <span data-ttu-id="3f232-134">Usa lo stesso [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API, che offre un raggio di origine e la direzione che è possibile raycast contro la scena.</span><span class="sxs-lookup"><span data-stu-id="3f232-134">It uses the same  [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API, which provides a ray origin and direction that you can raycast against your scene.</span></span>  <span data-ttu-id="3f232-135">L'unica differenza è che è necessario abilitare in modo esplicito il rilevamento sotto controllo prima di poterla usare.</span><span class="sxs-lookup"><span data-stu-id="3f232-135">The only difference is that you need to explicitly enable eye tracking before using it.</span></span> <span data-ttu-id="3f232-136">A tale scopo, è necessario eseguire due passaggi:</span><span class="sxs-lookup"><span data-stu-id="3f232-136">For this, you need to do two steps:</span></span>
1. <span data-ttu-id="3f232-137">Richiedere l'autorizzazione utente per usare occhio rilevamento nell'app.</span><span class="sxs-lookup"><span data-stu-id="3f232-137">Request user permission to use eye tracking in your app.</span></span>
2. <span data-ttu-id="3f232-138">Abilitare la funzionalità di "Input sguardo" nel manifesto del pacchetto.</span><span class="sxs-lookup"><span data-stu-id="3f232-138">Enable the "Gaze Input" capability in your package manifest.</span></span>

### <a name="requesting-access-to-gaze-input"></a><span data-ttu-id="3f232-139">Richiesta di accesso a input sguardo</span><span class="sxs-lookup"><span data-stu-id="3f232-139">Requesting access to gaze input</span></span>
<span data-ttu-id="3f232-140">Quando si avvia l'app, chiamare [EyesPose::RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) per richiedere l'accesso a rilevamento sotto controllo.</span><span class="sxs-lookup"><span data-stu-id="3f232-140">When your app is starting up, call [EyesPose::RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) to request access to eye tracking.</span></span> <span data-ttu-id="3f232-141">Il sistema richiede all'utente se necessario e restituire [GazeInputAccessStatus::Allowed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus) dopo che è stato concesso l'accesso.</span><span class="sxs-lookup"><span data-stu-id="3f232-141">The system will prompt the user if needed, and return [GazeInputAccessStatus::Allowed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus) once access has been granted.</span></span> <span data-ttu-id="3f232-142">Si tratta di una chiamata asincrona, pertanto è necessario un po' di gestione supplementare.</span><span class="sxs-lookup"><span data-stu-id="3f232-142">This is an asynchronous call, so it requires a bit of extra management.</span></span> <span data-ttu-id="3f232-143">Nell'esempio seguente attiva un std::thread scollegato per attendere il risultato, che viene archiviato in una variabile membro denominata *m_isEyeTrackingEnabled*.</span><span class="sxs-lookup"><span data-stu-id="3f232-143">The following example spins up a detached std::thread to wait for the result, which it stores to a member variable called *m_isEyeTrackingEnabled*.</span></span>

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
<span data-ttu-id="3f232-144">Avvio di un thread scollegato è solo un'opzione per la gestione delle chiamate async.</span><span class="sxs-lookup"><span data-stu-id="3f232-144">Starting a detached thread is just one option for handling async calls.</span></span>  <span data-ttu-id="3f232-145">In alternativa, è possibile usare le nuove [co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) funzionalità supportate da C++/WinRT.</span><span class="sxs-lookup"><span data-stu-id="3f232-145">Alternatively, you could use the new [co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) functionality supported by C++/WinRT.</span></span>
<span data-ttu-id="3f232-146">Ecco un altro esempio per l'autorizzazione utente:</span><span class="sxs-lookup"><span data-stu-id="3f232-146">Here is another example for asking for user permission:</span></span>
-   <span data-ttu-id="3f232-147">EyesPose::IsSupported() consente all'applicazione attivare la finestra di dialogo di autorizzazione solo se è presente un tracker sotto controllo.</span><span class="sxs-lookup"><span data-stu-id="3f232-147">EyesPose::IsSupported() allows the application to trigger the permission dialog only if there is an eye tracker.</span></span>
-   <span data-ttu-id="3f232-148">M_gazeInputAccessStatus GazeInputAccessStatus; Si tratta di evitare comparendo ripetutamente il prompt relativo alle autorizzazioni.</span><span class="sxs-lookup"><span data-stu-id="3f232-148">GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.</span></span>

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


### <a name="declaring-the-gaze-input-capability"></a><span data-ttu-id="3f232-149">Dichiarare la *estasiati Input* funzionalità</span><span class="sxs-lookup"><span data-stu-id="3f232-149">Declaring the *Gaze Input* capability</span></span>

<span data-ttu-id="3f232-150">Fare doppio clic sul file appxmanifest nel *Esplora soluzioni*.</span><span class="sxs-lookup"><span data-stu-id="3f232-150">Double click the appxmanifest file in *Solution Explorer*.</span></span>  <span data-ttu-id="3f232-151">Quindi passare al *funzionalità* sezione e selezionare il *estasiati Input* funzionalità.</span><span class="sxs-lookup"><span data-stu-id="3f232-151">Then navigate to the *Capabilities* section and check the *Gaze Input* capability.</span></span> 

![Capacità di input sguardo](images/gaze-input-capability.png)

<span data-ttu-id="3f232-153">Ciò consente di aggiungere le righe seguenti per il *pacchetto* sezione nel file appxmanifest:</span><span class="sxs-lookup"><span data-stu-id="3f232-153">This adds the following lines to the *Package* section in the appxmanifest file:</span></span>
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a><span data-ttu-id="3f232-154">Ottenere il raggio sguardo sotto controllo</span><span class="sxs-lookup"><span data-stu-id="3f232-154">Getting the eye gaze ray</span></span>
<span data-ttu-id="3f232-155">Dopo aver ricevuto l'accesso a ET, si possono acquisire raggio sguardo occhio ogni fotogramma.</span><span class="sxs-lookup"><span data-stu-id="3f232-155">Once you have received access to ET, you are free to grab the eye gaze ray every frame.</span></span>  <span data-ttu-id="3f232-156">Come avviene con head sguardo, ottenere il [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) chiamando [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) con un timestamp desiderato e un sistema di coordinate.</span><span class="sxs-lookup"><span data-stu-id="3f232-156">Just as with head gaze, get the [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) by calling [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with a desired timestamp and coordinate system.</span></span> <span data-ttu-id="3f232-157">Il SpatialPointerPose contiene un' [EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) dell'oggetto tramite il [occhi](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) proprietà.</span><span class="sxs-lookup"><span data-stu-id="3f232-157">The SpatialPointerPose contains an [EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) object through the [Eyes](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) property.</span></span> <span data-ttu-id="3f232-158">Ciò è diverso da null solo se è abilitata l'occhio di rilevamento.</span><span class="sxs-lookup"><span data-stu-id="3f232-158">This is non-null only if eye tracking is enabled.</span></span> <span data-ttu-id="3f232-159">Da qui è possibile controllare se l'utente del dispositivo ha un occhio rilevamento calibrazione chiamando [EyesPose::IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).</span><span class="sxs-lookup"><span data-stu-id="3f232-159">From there you can check if the user in the device has an eye tracking calibration by calling [EyesPose::IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).</span></span>  <span data-ttu-id="3f232-160">Successivamente, usare il [estasiati](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) proprietà da ottenere l'una [SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) fissata l'occhio del lettore estasiati posizione e la direzione.</span><span class="sxs-lookup"><span data-stu-id="3f232-160">Next, use the [Gaze](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) property to get the a [SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) contianing the eye gaze position and direction.</span></span> <span data-ttu-id="3f232-161">La proprietà sguardo può talvolta essere null, pertanto assicurarsi di eseguire questo controllo.</span><span class="sxs-lookup"><span data-stu-id="3f232-161">The Gaze property can sometimes be null, so be sure to check for this.</span></span> <span data-ttu-id="3f232-162">Questo può verificarsi è se un utente calibrato chiude temporaneamente ai loro stessi occhi.</span><span class="sxs-lookup"><span data-stu-id="3f232-162">This can happen is if a calibrated user temporarily closes their eyes.</span></span>

<span data-ttu-id="3f232-163">Il codice seguente viene illustrato come il raggio sguardo sotto controllo di accesso.</span><span class="sxs-lookup"><span data-stu-id="3f232-163">The following code shows how to access the eye gaze ray.</span></span>

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
            
            // Do something with the eye gaze
        }
    }
}

```

## <a name="correlating-gaze-with-other-inputs"></a><span data-ttu-id="3f232-164">Sguardo con correlazione con altri input</span><span class="sxs-lookup"><span data-stu-id="3f232-164">Correlating gaze with other inputs</span></span>

<span data-ttu-id="3f232-165">In alcuni casi si potrebbe rilevare che è necessario un [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) che corrisponde a un evento in passato.</span><span class="sxs-lookup"><span data-stu-id="3f232-165">Sometimes you may find that you need a [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) that corresponds with an event in the past.</span></span> <span data-ttu-id="3f232-166">Ad esempio, se l'utente esegue un'aria toccare, l'app potrebbe essere necessario sapere che cosa si sta cercando.</span><span class="sxs-lookup"><span data-stu-id="3f232-166">For example, if the user performs an Air Tap, your app might want to know what they were looking at.</span></span> <span data-ttu-id="3f232-167">A tale scopo, utilizzare semplicemente [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) il frame stimato ora saranno impreciso a causa della latenza tra l'elaborazione dell'input del sistema e l'ora di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="3f232-167">For this purpose, simply using [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with the predicted frame time would be inaccurate because of the latency between system input processing and display time.</span></span> <span data-ttu-id="3f232-168">Inoltre, se si usa sguardo sotto controllo per specificare come destinazione, gli occhi tendono a passare anche prima del completamento di un'operazione di commit.</span><span class="sxs-lookup"><span data-stu-id="3f232-168">In addition, if using eye gaze for targeting, our eyes tend to move on even before finishing a commit action.</span></span> <span data-ttu-id="3f232-169">È minore di un problema per un semplice Air Tap, ma diventano più importanti quando si combinano tempo comandi vocali con spostamenti occhio veloce.</span><span class="sxs-lookup"><span data-stu-id="3f232-169">This is less of an issue for a simple Air Tap, but becomes more critical when combining long voice commands with fast eye movements.</span></span> <span data-ttu-id="3f232-170">Un modo per gestire questo scenario è eseguire una chiamata aggiuntiva al [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), usando un timestamp cronologico che corrisponde all'evento di input.</span><span class="sxs-lookup"><span data-stu-id="3f232-170">One way to handle this scenario is to make an additional call to  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), using a historical timestamp that corresponds to the input event.</span></span>  

<span data-ttu-id="3f232-171">Tuttavia, per l'input viene indirizzata attraverso il SpatialInteractionManager, vi è un metodo più semplice.</span><span class="sxs-lookup"><span data-stu-id="3f232-171">However, for input that routes through the SpatialInteractionManager, there's an easier method.</span></span> <span data-ttu-id="3f232-172">Il [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) ha il proprio [TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) (funzione).</span><span class="sxs-lookup"><span data-stu-id="3f232-172">The [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) has its very own [TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) function.</span></span> <span data-ttu-id="3f232-173">Chiamare il metodo che fornirà un perfettamente correlati [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) senza lasciare al caso.</span><span class="sxs-lookup"><span data-stu-id="3f232-173">Calling that will provide a perfectly correlated [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) without the guesswork.</span></span> <span data-ttu-id="3f232-174">Per altre informazioni sull'uso di SpatialInteractionSourceStates, esaminiamo il [mani e i controller di movimento in DirectX](hands-and-motion-controllers-in-directx.md) documentazione.</span><span class="sxs-lookup"><span data-stu-id="3f232-174">For more information on working with SpatialInteractionSourceStates, take a look at the [Hands and Motion Controllers in DirectX](hands-and-motion-controllers-in-directx.md) documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="3f232-175">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3f232-175">See also</span></span>
* [<span data-ttu-id="3f232-176">Head sguardo ed eseguire il commit del modello di input</span><span class="sxs-lookup"><span data-stu-id="3f232-176">Head gaze and commit input model</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="3f232-177">Visiva in HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="3f232-177">Eye-gaze on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="3f232-178">Sistemi di coordinate in DirectX</span><span class="sxs-lookup"><span data-stu-id="3f232-178">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="3f232-179">Input vocale in DirectX</span><span class="sxs-lookup"><span data-stu-id="3f232-179">Voice Input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="3f232-180">Mani e controller del movimento in DirectX</span><span class="sxs-lookup"><span data-stu-id="3f232-180">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)

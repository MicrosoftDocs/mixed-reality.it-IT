---
title: Sguardo in DirectX
description: Guida per gli sviluppatori per l'uso degli sguardi e degli occhi nelle app DirectX native.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 05/09/2019
ms.topic: article
keywords: occhio, sguardo, Head-sguardi, tracking, tracciamento degli occhi, DirectX, input, ologrammi
ms.openlocfilehash: 664657b9ab01530a608e31091823e828cc99d0cd
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926554"
---
# <a name="head-gaze-and-eye-gaze-input-in-directx"></a><span data-ttu-id="39520-104">Input occhi e sguardi in DirectX</span><span class="sxs-lookup"><span data-stu-id="39520-104">Head-gaze and eye-gaze input in DirectX</span></span>

<span data-ttu-id="39520-105">Per quanto riguarda la realtà mista di Windows, viene usato l'input occhi e occhio per determinare l'aspetto dell'utente.</span><span class="sxs-lookup"><span data-stu-id="39520-105">In Windows Mixed Reality, eye and head gaze input is used to determine what the user is looking at.</span></span> <span data-ttu-id="39520-106">Questo può essere usato per gestire i modelli di input primari, ad esempio [Head-sguardi e commit](gaze-and-commit.md), nonché per fornire il contesto per i tipi di interazioni.</span><span class="sxs-lookup"><span data-stu-id="39520-106">This can be used to drive primary input models such as [head-gaze and commit](gaze-and-commit.md), and also to provide context for types of interactions.</span></span> <span data-ttu-id="39520-107">Esistono due tipi di vettori di sguardi disponibili tramite l'API, ovvero Head-sguardi e sguardo.</span><span class="sxs-lookup"><span data-stu-id="39520-107">There are two types of gaze vectors available through the API: head-gaze and eye-gaze.</span></span>  <span data-ttu-id="39520-108">Entrambe sono fornite come un raggio tridimensionale con un'origine e una direzione.</span><span class="sxs-lookup"><span data-stu-id="39520-108">Both are provided as a three dimensional ray with an origin and direction.</span></span> <span data-ttu-id="39520-109">Le applicazioni possono quindi Raycast nelle proprie scene, o nel mondo reale, e determinare le operazioni di destinazione dell'utente.</span><span class="sxs-lookup"><span data-stu-id="39520-109">Applications can then raycast into their scenes, or the real world, and determine what the user is targeting.</span></span>

<span data-ttu-id="39520-110">**Head-sguardi** rappresenta la direzione a cui è puntata la testa dell'utente.</span><span class="sxs-lookup"><span data-stu-id="39520-110">**Head-gaze** represents the direction that the user's head is pointed in.</span></span> <span data-ttu-id="39520-111">Si pensi a questo come la posizione e la direzione di avanzamento del dispositivo stesso, con la posizione che rappresenta il punto centrale tra le due visualizzazioni.</span><span class="sxs-lookup"><span data-stu-id="39520-111">Think of this as the position and forward direction of the device itself, with the position representing the center point between the two displays.</span></span> <span data-ttu-id="39520-112">Head-sguardi è disponibile in tutti i dispositivi a realtà mista.</span><span class="sxs-lookup"><span data-stu-id="39520-112">Head-gaze is available on all Mixed Reality devices.</span></span>

<span data-ttu-id="39520-113">**Eye-sguardi** rappresenta la direzione verso la quale gli occhi dell'utente stanno cercando.</span><span class="sxs-lookup"><span data-stu-id="39520-113">**Eye-gaze** represents the direction that the user's eyes are looking towards.</span></span> <span data-ttu-id="39520-114">L'origine si trova tra gli occhi dell'utente.</span><span class="sxs-lookup"><span data-stu-id="39520-114">The origin is located between the user's eyes.</span></span>  <span data-ttu-id="39520-115">È disponibile nei dispositivi a realtà mista che includono un sistema di rilevamento degli occhi.</span><span class="sxs-lookup"><span data-stu-id="39520-115">It is available on Mixed Reality devices that include an eye tracking system.</span></span>

<span data-ttu-id="39520-116">I raggi Head e sguardi sono accessibili tramite l'API [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) .</span><span class="sxs-lookup"><span data-stu-id="39520-116">Both head and eye-gaze rays are accessible through the  [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API.</span></span> <span data-ttu-id="39520-117">È sufficiente chiamare [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) per ricevere un nuovo oggetto SpatialPointerPose in corrispondenza del timestamp e del [sistema di coordinate](coordinate-systems-in-directx.md)specificati.</span><span class="sxs-lookup"><span data-stu-id="39520-117">Simply call [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object at the specified timestamp and [coordinate system](coordinate-systems-in-directx.md).</span></span> <span data-ttu-id="39520-118">Questo SpatialPointerPose contiene un'origine e una direzione per lo sguardo del capo.</span><span class="sxs-lookup"><span data-stu-id="39520-118">This SpatialPointerPose contains a head-gaze origin and direction.</span></span> <span data-ttu-id="39520-119">Contiene anche un'origine e una direzione degli sguardi se è disponibile la verifica degli occhi.</span><span class="sxs-lookup"><span data-stu-id="39520-119">It also contains an eye-gaze origin and direction if eye tracking is available.</span></span>

### <a name="device-support"></a><span data-ttu-id="39520-120">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="39520-120">Device support</span></span>
<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><span data-ttu-id="39520-121"><strong>Funzionalità</strong></span><span class="sxs-lookup"><span data-stu-id="39520-121"><strong>Feature</strong></span></span></td>
     <td><span data-ttu-id="39520-122"><a href="hololens-hardware-details.md"><strong>HoloLens (prima generazione)</strong></a></span><span class="sxs-lookup"><span data-stu-id="39520-122"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="39520-123"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="39520-123"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
     <td><span data-ttu-id="39520-124"><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="39520-124"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="39520-125">Puntamento con la testa</span><span class="sxs-lookup"><span data-stu-id="39520-125">Head-gaze</span></span></td>
     <td><span data-ttu-id="39520-126">✔️</span><span class="sxs-lookup"><span data-stu-id="39520-126">✔️</span></span></td>
     <td><span data-ttu-id="39520-127">✔️</span><span class="sxs-lookup"><span data-stu-id="39520-127">✔️</span></span></td>
     <td><span data-ttu-id="39520-128">✔️</span><span class="sxs-lookup"><span data-stu-id="39520-128">✔️</span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="39520-129">Sguardo attento</span><span class="sxs-lookup"><span data-stu-id="39520-129">Eye-gaze</span></span></td>
     <td>❌</td>
     <td><span data-ttu-id="39520-130">✔️</span><span class="sxs-lookup"><span data-stu-id="39520-130">✔️</span></span></td>
     <td>❌</td>
</tr>
</table>

## <a name="using-head-gaze"></a><span data-ttu-id="39520-131">Uso di Head-sguardi</span><span class="sxs-lookup"><span data-stu-id="39520-131">Using head-gaze</span></span>

<span data-ttu-id="39520-132">Per accedere all'Head-sguardi, iniziare chiamando [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) per ricevere un nuovo oggetto SpatialPointerPose.</span><span class="sxs-lookup"><span data-stu-id="39520-132">To access the head-gaze, start by calling  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object.</span></span> <span data-ttu-id="39520-133">È necessario passare i parametri seguenti.</span><span class="sxs-lookup"><span data-stu-id="39520-133">You need to pass the following parameters.</span></span>
 - <span data-ttu-id="39520-134">Oggetto [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) che rappresenta il sistema di coordinate desiderato per lo sguardo Head.</span><span class="sxs-lookup"><span data-stu-id="39520-134">A [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) that represents the desired coordinate system for the head-gaze.</span></span> <span data-ttu-id="39520-135">Questa operazione è rappresentata dalla variabile *coordinateSystem* nel codice riportato di seguito.</span><span class="sxs-lookup"><span data-stu-id="39520-135">This is represented by the *coordinateSystem* variable in the following code.</span></span> <span data-ttu-id="39520-136">Per ulteriori informazioni, visitare la guida per gli sviluppatori di [sistemi di coordinate](coordinate-systems-in-directx.md) .</span><span class="sxs-lookup"><span data-stu-id="39520-136">For more information, visit our [coordinate systems](coordinate-systems-in-directx.md) developer guide.</span></span>
 - <span data-ttu-id="39520-137">[Timestamp](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) che rappresenta l'ora esatta della richiesta Head.</span><span class="sxs-lookup"><span data-stu-id="39520-137">A [Timestamp](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) that represents the exact time of the head pose requested.</span></span>  <span data-ttu-id="39520-138">Viene in genere utilizzato un timestamp corrispondente all'ora in cui verrà visualizzato il frame corrente.</span><span class="sxs-lookup"><span data-stu-id="39520-138">Typically you will use a timestamp that corresponds to the time when the current frame will be displayed.</span></span> <span data-ttu-id="39520-139">È possibile ottenere questo timestamp di visualizzazione stimato da un oggetto [HolographicFramePrediction](https://docs.microsoft.com//uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) , accessibile tramite il [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe)corrente.</span><span class="sxs-lookup"><span data-stu-id="39520-139">You can get this predicted display timestamp from a  [HolographicFramePrediction](https://docs.microsoft.com//uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) object, which is accessible through the current [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe).</span></span>  <span data-ttu-id="39520-140">Questo oggetto HolographicFramePrediction è rappresentato dalla variabile di *stima* nel codice riportato di seguito.</span><span class="sxs-lookup"><span data-stu-id="39520-140">This HolographicFramePrediction object is represented by the *prediction* variable in the following code.</span></span>

 <span data-ttu-id="39520-141">Quando si dispone di un SpatialPointerPose valido, la posizione della testa e la direzione di avanzamento sono accessibili come proprietà.</span><span class="sxs-lookup"><span data-stu-id="39520-141">Once you have a valid SpatialPointerPose, the head position and forward direction are accessible as properties.</span></span>  <span data-ttu-id="39520-142">Nel codice seguente viene illustrato come accedervi.</span><span class="sxs-lookup"><span data-stu-id="39520-142">The following code  shows how to access them.</span></span>

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

## <a name="using-eye-gaze"></a><span data-ttu-id="39520-143">Uso degli sguardi</span><span class="sxs-lookup"><span data-stu-id="39520-143">Using eye-gaze</span></span>

<span data-ttu-id="39520-144">Si noti che, per consentire agli utenti di usare l'input con sguardo oculare, ogni utente deve esaminare la [calibrazione degli utenti](calibration.md) per la prima volta che usa il dispositivo.</span><span class="sxs-lookup"><span data-stu-id="39520-144">Please note that for your users to use eye-gaze input, each user has to go through an [eye tracking user calibration](calibration.md) the first time they use the device.</span></span> <span data-ttu-id="39520-145">L'API Eye-sguardi è molto simile a Head-sguardi.</span><span class="sxs-lookup"><span data-stu-id="39520-145">The eye-gaze API is very similar to head-gaze.</span></span>
<span data-ttu-id="39520-146">Usa la stessa API [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) , che fornisce un'origine e una direzione del raggio che è possibile Raycast per la scena.</span><span class="sxs-lookup"><span data-stu-id="39520-146">It uses the same [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API, which provides a ray origin and direction that you can raycast against your scene.</span></span>  <span data-ttu-id="39520-147">L'unica differenza è che è necessario abilitare in modo esplicito il rilevamento degli occhi prima di usarlo.</span><span class="sxs-lookup"><span data-stu-id="39520-147">The only difference is that you need to explicitly enable eye tracking before using it.</span></span> <span data-ttu-id="39520-148">A tale scopo, è necessario eseguire due passaggi:</span><span class="sxs-lookup"><span data-stu-id="39520-148">For this, you need to do two steps:</span></span>
1. <span data-ttu-id="39520-149">Richiedere all'utente l'autorizzazione per usare il rilevamento degli occhi nell'app.</span><span class="sxs-lookup"><span data-stu-id="39520-149">Request user permission to use eye tracking in your app.</span></span>
2. <span data-ttu-id="39520-150">Abilitare la funzionalità di "input dello sguardo" nel manifesto del pacchetto.</span><span class="sxs-lookup"><span data-stu-id="39520-150">Enable the "Gaze Input" capability in your package manifest.</span></span>

### <a name="requesting-access-to-eye-gaze-input"></a><span data-ttu-id="39520-151">Richiesta di accesso a Eye-sguardi input</span><span class="sxs-lookup"><span data-stu-id="39520-151">Requesting access to eye-gaze input</span></span>
<span data-ttu-id="39520-152">All'avvio dell'app, chiamare [EyesPose:: RequestAccessAsync](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) per richiedere l'accesso al rilevamento degli occhi.</span><span class="sxs-lookup"><span data-stu-id="39520-152">When your app is starting up, call [EyesPose::RequestAccessAsync](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) to request access to eye tracking.</span></span> <span data-ttu-id="39520-153">Se necessario, il sistema richiede all'utente e restituisce [GazeInputAccessStatus:: allowed](https://docs.microsoft.com//uwp/api/windows.ui.input.gazeinputaccessstatus) dopo che è stato concesso l'accesso.</span><span class="sxs-lookup"><span data-stu-id="39520-153">The system will prompt the user if needed, and return [GazeInputAccessStatus::Allowed](https://docs.microsoft.com//uwp/api/windows.ui.input.gazeinputaccessstatus) once access has been granted.</span></span> <span data-ttu-id="39520-154">Si tratta di una chiamata asincrona, quindi richiede un po' di gestione aggiuntiva.</span><span class="sxs-lookup"><span data-stu-id="39520-154">This is an asynchronous call, so it requires a bit of extra management.</span></span> <span data-ttu-id="39520-155">Nell'esempio seguente viene avviata un'operazione std:: thread scollegata per attendere il risultato, che viene archiviato in una variabile membro denominata *m_isEyeTrackingEnabled*.</span><span class="sxs-lookup"><span data-stu-id="39520-155">The following example spins up a detached std::thread to wait for the result, which it stores to a member variable called *m_isEyeTrackingEnabled*.</span></span>

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
<span data-ttu-id="39520-156">L'avvio di un thread scollegato è solo un'opzione per la gestione delle chiamate asincrone.</span><span class="sxs-lookup"><span data-stu-id="39520-156">Starting a detached thread is just one option for handling async calls.</span></span> <span data-ttu-id="39520-157">In alternativa, è possibile usare la nuova funzionalità di [co_await](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) supportata C++da/WinRT.</span><span class="sxs-lookup"><span data-stu-id="39520-157">Alternatively, you could use the new [co_await](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) functionality supported by C++/WinRT.</span></span>
<span data-ttu-id="39520-158">Di seguito è riportato un altro esempio per richiedere l'autorizzazione utente:</span><span class="sxs-lookup"><span data-stu-id="39520-158">Here is another example for asking for user permission:</span></span>
-   <span data-ttu-id="39520-159">EyesPose:: supporto () consente all'applicazione di attivare la finestra di dialogo di autorizzazione solo se è presente uno strumento di rilevamento.</span><span class="sxs-lookup"><span data-stu-id="39520-159">EyesPose::IsSupported() allows the application to trigger the permission dialog only if there is an eye tracker.</span></span>
-   <span data-ttu-id="39520-160">GazeInputAccessStatus m_gazeInputAccessStatus; In questo modo si evita di riscattare il prompt delle autorizzazioni più volte.</span><span class="sxs-lookup"><span data-stu-id="39520-160">GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.</span></span>

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

### <a name="declaring-the-gaze-input-capability"></a><span data-ttu-id="39520-161">Dichiarazione della funzionalità di *input di sguardi*</span><span class="sxs-lookup"><span data-stu-id="39520-161">Declaring the *Gaze Input* capability</span></span>

<span data-ttu-id="39520-162">Fare doppio clic sul file appxmanifest in *Esplora soluzioni*.</span><span class="sxs-lookup"><span data-stu-id="39520-162">Double click the appxmanifest file in *Solution Explorer*.</span></span>  <span data-ttu-id="39520-163">Passare quindi alla sezione *funzionalità* e controllare la funzionalità di *input di sguardi* .</span><span class="sxs-lookup"><span data-stu-id="39520-163">Then navigate to the *Capabilities* section and check the *Gaze Input* capability.</span></span> 

![Funzionalità di input di sguardi](images/gaze-input-capability.png)

<span data-ttu-id="39520-165">Vengono aggiunte le righe seguenti alla sezione del *pacchetto* nel file appxmanifest:</span><span class="sxs-lookup"><span data-stu-id="39520-165">This adds the following lines to the *Package* section in the appxmanifest file:</span></span>
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a><span data-ttu-id="39520-166">Ottenere il raggio d'occhio</span><span class="sxs-lookup"><span data-stu-id="39520-166">Getting the eye-gaze ray</span></span>
<span data-ttu-id="39520-167">Dopo aver ricevuto l'accesso a ET, è possibile cogliere il raggio d'occhio per ogni fotogramma.</span><span class="sxs-lookup"><span data-stu-id="39520-167">Once you have received access to ET, you are free to grab the eye-gaze ray every frame.</span></span>
<span data-ttu-id="39520-168">Come per gli occhi, ottenere il [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) chiamando [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) con un timestamp e un sistema di coordinate desiderati.</span><span class="sxs-lookup"><span data-stu-id="39520-168">Just as with head-gaze, get the [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) by calling [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with a desired timestamp and coordinate system.</span></span> <span data-ttu-id="39520-169">SpatialPointerPose contiene un oggetto [EyesPose](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose) tramite la proprietà [Eyes](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) .</span><span class="sxs-lookup"><span data-stu-id="39520-169">The SpatialPointerPose contains an [EyesPose](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose) object through the [Eyes](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) property.</span></span> <span data-ttu-id="39520-170">Questo valore non è null solo se è abilitata la funzionalità Eye Tracking.</span><span class="sxs-lookup"><span data-stu-id="39520-170">This is non-null only if eye tracking is enabled.</span></span> <span data-ttu-id="39520-171">Da qui è possibile verificare se l'utente nel dispositivo ha una calibrazione del rilevamento degli occhi chiamando [EyesPose:: IsCalibrationValid](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).</span><span class="sxs-lookup"><span data-stu-id="39520-171">From there you can check if the user in the device has an eye tracking calibration by calling [EyesPose::IsCalibrationValid](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).</span></span>  <span data-ttu-id="39520-172">Usare quindi la proprietà [sguardi](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) per ottenere l'oggetto [SpatialRay](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialray) che contiene la posizione e la direzione degli sguardi.</span><span class="sxs-lookup"><span data-stu-id="39520-172">Next, use the [Gaze](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) property to get the a [SpatialRay](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialray) containing the eye-gaze position and direction.</span></span> <span data-ttu-id="39520-173">La proprietà sguardi può talvolta essere null, quindi assicurarsi di controllarla.</span><span class="sxs-lookup"><span data-stu-id="39520-173">The Gaze property can sometimes be null, so be sure to check for this.</span></span> <span data-ttu-id="39520-174">Questo problema può verificarsi se un utente calibrato chiude temporaneamente gli occhi.</span><span class="sxs-lookup"><span data-stu-id="39520-174">This can happen is if a calibrated user temporarily closes their eyes.</span></span>

<span data-ttu-id="39520-175">Il codice seguente illustra come accedere al raggio d'occhio.</span><span class="sxs-lookup"><span data-stu-id="39520-175">The following code shows how to access the eye-gaze ray.</span></span>

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

## <a name="fallback-when-eye-tracking-is-not-available"></a><span data-ttu-id="39520-176">Fallback quando il rilevamento degli occhi non è disponibile</span><span class="sxs-lookup"><span data-stu-id="39520-176">Fallback when eye tracking is not available</span></span>
<span data-ttu-id="39520-177">Come indicato nella documentazione di progettazione per il [monitoraggio degli occhi](eye-tracking.md#fallback-solutions-when-eye-tracking-is-not-available), sia le finestre di progettazione che gli sviluppatori devono tenere presente che potrebbero essere presenti istanze in cui i dati di rilevamento degli occhi potrebbero non essere disponibili per l'app.</span><span class="sxs-lookup"><span data-stu-id="39520-177">As mentioned in our [eye tracking design docs](eye-tracking.md#fallback-solutions-when-eye-tracking-is-not-available), both designers as well as developers should be aware that there may be instances in which eye tracking data may not be available to your app.</span></span>
<span data-ttu-id="39520-178">Sono diversi i motivi per cui un utente non è calibrato, l'utente ha negato l'accesso dell'app ai dati di rilevamento degli occhi o semplicemente interferenze temporanee (ad esempio, le sbavature sulla visiera HoloLens o sui capelli occlusione gli occhi dell'utente).</span><span class="sxs-lookup"><span data-stu-id="39520-178">There are various reasons for this ranging from a user not being calibrated, the user having denied the app access to his/her eye tracking data or simply temporary interferences (such as smudges on the HoloLens visor or hair occluding the user's eyes).</span></span> <span data-ttu-id="39520-179">Sebbene alcune API siano già state citate in questo documento, di seguito viene fornito un riepilogo su come rilevare che il rilevamento degli occhi è disponibile come riferimento rapido:</span><span class="sxs-lookup"><span data-stu-id="39520-179">While some of the APIs have already been mentioned in this document, in the following, we provide a summary of how to detect that eye tracking is available as a quick reference:</span></span> 

* <span data-ttu-id="39520-180">Verificare che il sistema supporti la verifica degli occhi.</span><span class="sxs-lookup"><span data-stu-id="39520-180">Check that the system supports eye tracking at all.</span></span> <span data-ttu-id="39520-181">Chiamare il *Metodo*seguente: [Windows. Perception. people. EyesPose. IsValid ()](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.issupported#Windows_Perception_People_EyesPose_IsSupported)</span><span class="sxs-lookup"><span data-stu-id="39520-181">Call the following *method*: [Windows.Perception.People.EyesPose.IsSupported()](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.issupported#Windows_Perception_People_EyesPose_IsSupported)</span></span>

* <span data-ttu-id="39520-182">Verificare che l'utente sia calibrato.</span><span class="sxs-lookup"><span data-stu-id="39520-182">Check that the user is calibrated.</span></span> <span data-ttu-id="39520-183">Chiamare la *Proprietà*seguente: [Windows. Perception. people. EyesPose. IsCalibrationValid](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)</span><span class="sxs-lookup"><span data-stu-id="39520-183">Call the following *property*: [Windows.Perception.People.EyesPose.IsCalibrationValid](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)</span></span> 

* <span data-ttu-id="39520-184">Verificare che l'utente abbia specificato l'autorizzazione dell'app per usare i dati di rilevamento degli occhi: recuperare il _' GazeInputAccessStatus '_ corrente.</span><span class="sxs-lookup"><span data-stu-id="39520-184">Check that the user has given your app permission to use their eye tracking data: Retrieve the current _'GazeInputAccessStatus'_.</span></span> <span data-ttu-id="39520-185">Un esempio di come eseguire questa operazione è illustrato nella pagina relativa alla [richiesta di accesso a sguardi input](https://docs.microsoft.com/windows/mixed-reality/gaze-in-directX#requesting-access-to-gaze-input).</span><span class="sxs-lookup"><span data-stu-id="39520-185">An example on how to do this is explained at [Requesting access to gaze input](https://docs.microsoft.com/windows/mixed-reality/gaze-in-directX#requesting-access-to-gaze-input).</span></span>   

<span data-ttu-id="39520-186">Inoltre, è possibile verificare che i dati di rilevamento degli occhi non siano obsoleti aggiungendo un timeout tra gli aggiornamenti dei dati di rilevamento degli occhi ricevuti e altrimenti il fallback a Head-sguardi come descritto di seguito.</span><span class="sxs-lookup"><span data-stu-id="39520-186">In addition, you may want to check that your eye tracking data is not stale by adding a timeout between received eye tracking data updates and otherwise fallback to head-gaze as discussed below.</span></span>  
<span data-ttu-id="39520-187">Per ulteriori informazioni, vedere le [considerazioni sulla progettazione di fallback](eye-tracking.md#fallback-solutions-when-eye-tracking-is-not-available) .</span><span class="sxs-lookup"><span data-stu-id="39520-187">Please visit our [fallback design considerations](eye-tracking.md#fallback-solutions-when-eye-tracking-is-not-available) for more information.</span></span>

<br>

## <a name="correlating-gaze-with-other-inputs"></a><span data-ttu-id="39520-188">Correlazione di sguardi con altri input</span><span class="sxs-lookup"><span data-stu-id="39520-188">Correlating gaze with other inputs</span></span>
<span data-ttu-id="39520-189">In alcuni casi potrebbe essere necessario un [SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) che corrisponda a un evento nel passato.</span><span class="sxs-lookup"><span data-stu-id="39520-189">Sometimes you may find that you need a [SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) that corresponds with an event in the past.</span></span> <span data-ttu-id="39520-190">Ad esempio, se l'utente esegue una scelta aerea, l'app potrebbe voler sapere cosa stavano cercando.</span><span class="sxs-lookup"><span data-stu-id="39520-190">For example, if the user performs an Air Tap, your app might want to know what they were looking at.</span></span> <span data-ttu-id="39520-191">A questo scopo, l'uso di [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) con il tempo previsto per i frame potrebbe non essere accurato a causa della latenza tra l'elaborazione dell'input di sistema e l'ora di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="39520-191">For this purpose, simply using [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with the predicted frame time would be inaccurate because of the latency between system input processing and display time.</span></span> <span data-ttu-id="39520-192">Inoltre, se si usa il controllo degli sguardi per la destinazione, gli occhi tendono a proseguire anche prima di terminare un'azione di commit.</span><span class="sxs-lookup"><span data-stu-id="39520-192">In addition, if using eye-gaze for targeting, our eyes tend to move on even before finishing a commit action.</span></span> <span data-ttu-id="39520-193">Si tratta di un problema minore per un semplice tocco, ma diventa più importante quando si combinano i comandi Long Voice con rapidi movimenti oculari.</span><span class="sxs-lookup"><span data-stu-id="39520-193">This is less of an issue for a simple Air Tap, but becomes more critical when combining long voice commands with fast eye movements.</span></span> <span data-ttu-id="39520-194">Un modo per gestire questo scenario è eseguire un'ulteriore chiamata a [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), usando un timestamp cronologico corrispondente all'evento di input.</span><span class="sxs-lookup"><span data-stu-id="39520-194">One way to handle this scenario is to make an additional call to  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), using a historical timestamp that corresponds to the input event.</span></span>  

<span data-ttu-id="39520-195">Tuttavia, per l'input che viene indirizzato attraverso SpatialInteractionManager, è disponibile un metodo più semplice.</span><span class="sxs-lookup"><span data-stu-id="39520-195">However, for input that routes through the SpatialInteractionManager, there's an easier method.</span></span> <span data-ttu-id="39520-196">[SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) dispone di una propria funzione [TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) .</span><span class="sxs-lookup"><span data-stu-id="39520-196">The [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) has its very own [TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) function.</span></span> <span data-ttu-id="39520-197">Chiamando che fornirà un [SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) perfettamente correlato senza le congetture.</span><span class="sxs-lookup"><span data-stu-id="39520-197">Calling that will provide a perfectly correlated [SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) without the guesswork.</span></span> <span data-ttu-id="39520-198">Per altre informazioni sull'uso di SpatialInteractionSourceStates, vedere la documentazione su [hands and Motion Controllers in DirectX](hands-and-motion-controllers-in-directx.md) .</span><span class="sxs-lookup"><span data-stu-id="39520-198">For more information on working with SpatialInteractionSourceStates, take a look at the [Hands and Motion Controllers in DirectX](hands-and-motion-controllers-in-directx.md) documentation.</span></span>

<br>

## <a name="calibration"></a><span data-ttu-id="39520-199">Calibrazione</span><span class="sxs-lookup"><span data-stu-id="39520-199">Calibration</span></span>
<span data-ttu-id="39520-200">Per il corretto funzionamento dell'analisi degli occhi, è necessario che ogni utente debba esaminare la [calibrazione degli utenti](calibration.md).</span><span class="sxs-lookup"><span data-stu-id="39520-200">For eye tracking to work accurately, each user is required to go through an [eye tracking user calibration](calibration.md).</span></span> <span data-ttu-id="39520-201">In questo modo, il dispositivo può modificare il sistema per un'esperienza di visualizzazione più comoda e di qualità superiore per l'utente e garantire il rilevamento accurato degli occhi allo stesso tempo.</span><span class="sxs-lookup"><span data-stu-id="39520-201">This allows the device to adjust the system for a more comfortable and higher quality viewing experience for the user and to ensure accurate eye tracking at the same time.</span></span> <span data-ttu-id="39520-202">Gli sviluppatori non devono eseguire alcuna operazione al termine della gestione della calibrazione degli utenti.</span><span class="sxs-lookup"><span data-stu-id="39520-202">Developers don’t need to do anything on their end to manage user calibration.</span></span> <span data-ttu-id="39520-203">Il sistema garantisce che all'utente venga richiesto di calibrare il dispositivo nei casi seguenti:</span><span class="sxs-lookup"><span data-stu-id="39520-203">The system will ensure that the user gets prompted to calibrate the device under the following circumstances:</span></span>
* <span data-ttu-id="39520-204">L'utente sta usando il dispositivo per la prima volta</span><span class="sxs-lookup"><span data-stu-id="39520-204">The user is using the device for the first time</span></span>
* <span data-ttu-id="39520-205">L'utente ha rifiutato in precedenza il processo di calibrazione</span><span class="sxs-lookup"><span data-stu-id="39520-205">The user previously opted out of the calibration process</span></span>
* <span data-ttu-id="39520-206">Il processo di calibrazione non ha avuto esito positivo all'ultima volta in cui l'utente ha usato il dispositivo</span><span class="sxs-lookup"><span data-stu-id="39520-206">The calibration process did not succeed the last time the user used the device</span></span>

<span data-ttu-id="39520-207">Gli sviluppatori devono garantire un supporto adeguato per gli utenti per i quali i dati di rilevamento degli occhi potrebbero non essere disponibili.</span><span class="sxs-lookup"><span data-stu-id="39520-207">Developers should make sure to provide adequate support for users for whom eye tracking data may not be available.</span></span> <span data-ttu-id="39520-208">Per altre informazioni sulle soluzioni di fallback, vedere [Eye tracking on Hololens 2](eye-tracking.md).</span><span class="sxs-lookup"><span data-stu-id="39520-208">Learn more about considerations for fallback solutions at [Eye tracking on Hololens 2](eye-tracking.md).</span></span>

<br>

## <a name="see-also"></a><span data-ttu-id="39520-209">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="39520-209">See also</span></span>
* [<span data-ttu-id="39520-210">Calibrazione</span><span class="sxs-lookup"><span data-stu-id="39520-210">Calibration</span></span>](calibration.md)
* [<span data-ttu-id="39520-211">Sistemi di coordinate in DirectX</span><span class="sxs-lookup"><span data-stu-id="39520-211">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="39520-212">Eye-sguardi su HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="39520-212">Eye-gaze on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="39520-213">Modello di input sguardo e commit</span><span class="sxs-lookup"><span data-stu-id="39520-213">Gaze and commit input model</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="39520-214">Mani e controller del movimento in DirectX</span><span class="sxs-lookup"><span data-stu-id="39520-214">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="39520-215">Input vocale in DirectX</span><span class="sxs-lookup"><span data-stu-id="39520-215">Voice Input in DirectX</span></span>](voice-input-in-directx.md)

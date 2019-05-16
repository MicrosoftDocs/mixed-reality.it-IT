---
title: Per il rendering in DirectX
description: Viene illustrato il rendering holographic per realtà mista di Windows.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Eseguire il rendering di realtà mista di Windows, vntana, rendering, grafica 3D, HolographicFrame, loop, ciclo di aggiornamento, procedura dettagliata, codice di esempio
ms.openlocfilehash: 6edcaf808f2d7d48f480169e5579adb8984678a0
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629040"
---
# <a name="rendering-in-directx"></a><span data-ttu-id="6bef2-104">Per il rendering in DirectX</span><span class="sxs-lookup"><span data-stu-id="6bef2-104">Rendering in DirectX</span></span>

<span data-ttu-id="6bef2-105">Realtà mista di Windows si basa su DirectX per produrre avanzata, grafica 3D esperienze per gli utenti.</span><span class="sxs-lookup"><span data-stu-id="6bef2-105">Windows Mixed Reality is built on DirectX to produce rich, 3D graphical experiences for users.</span></span> <span data-ttu-id="6bef2-106">L'astrazione per il rendering si trova immediatamente sopra DirectX e di un motivo app sulla posizione e l'orientamento di uno o più Observer di una scena holographic, come previsto dal sistema.</span><span class="sxs-lookup"><span data-stu-id="6bef2-106">The rendering abstraction sits just above DirectX and lets an app reason about the position and orientation of one or more observers of a holographic scene, as predicted by the system.</span></span> <span data-ttu-id="6bef2-107">Lo sviluppatore può individuare i vntana relativo ogni videocamera, consentendo all'app di rendering questi vntana in vari sistemi di coordinate spaziali, come l'utente si sposta.</span><span class="sxs-lookup"><span data-stu-id="6bef2-107">The developer can then locate their holograms relative to each camera, letting the app render these holograms in various spatial coordinate systems as the user moves around.</span></span>

## <a name="update-for-the-current-frame"></a><span data-ttu-id="6bef2-108">Aggiornamento per il frame corrente</span><span class="sxs-lookup"><span data-stu-id="6bef2-108">Update for the current frame</span></span>

<span data-ttu-id="6bef2-109">Per aggiornare lo stato dell'applicazione per vntana, una volta per ogni fotogramma dell'app sarà:</span><span class="sxs-lookup"><span data-stu-id="6bef2-109">To update the application state for holograms, once per frame the app will:</span></span>
* <span data-ttu-id="6bef2-110">Ottenere un <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> dal sistema di gestione di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="6bef2-110">Get a <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> from the display management system.</span></span>
* <span data-ttu-id="6bef2-111">Eseguire il rendering della scena con la stima corrente in cui la visualizzazione della fotocamera sarà quando è stato completato.</span><span class="sxs-lookup"><span data-stu-id="6bef2-111">Update the scene with the current prediction of where the camera view will be when render is completed.</span></span> <span data-ttu-id="6bef2-112">Si noti che possono essere presenti più di una fotocamera per la scena holographic.</span><span class="sxs-lookup"><span data-stu-id="6bef2-112">Note, there can be more than one camera for the holographic scene.</span></span>

<span data-ttu-id="6bef2-113">Per eseguire il rendering per le visualizzazioni di fotocamera holographic, una volta per ogni fotogramma dell'app sarà:</span><span class="sxs-lookup"><span data-stu-id="6bef2-113">To render to holographic camera views, once per frame the app will:</span></span>
* <span data-ttu-id="6bef2-114">Per ogni videocamera, eseguire il rendering della scena per il frame corrente, usando le matrici di visualizzazione e di proiezione della fotocamera dal sistema.</span><span class="sxs-lookup"><span data-stu-id="6bef2-114">For each camera, render the scene for the current frame, using the camera view and projection matrices from the system.</span></span>

### <a name="create-a-new-holographic-frame-and-get-its-prediction"></a><span data-ttu-id="6bef2-115">Creare un nuovo frame holographic e ottenere la stima</span><span class="sxs-lookup"><span data-stu-id="6bef2-115">Create a new holographic frame and get its prediction</span></span>

<span data-ttu-id="6bef2-116">Il <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> dispone di informazioni che l'app necessita per aggiornare ed eseguire il rendering il frame corrente.</span><span class="sxs-lookup"><span data-stu-id="6bef2-116">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> has information that the app needs in order to update and render the current frame.</span></span> <span data-ttu-id="6bef2-117">L'app viene avviata ogni nuovo frame chiamando il **CreateNextFrame** (metodo).</span><span class="sxs-lookup"><span data-stu-id="6bef2-117">The app begins each new frame by calling the **CreateNextFrame** method.</span></span> <span data-ttu-id="6bef2-118">Quando questo metodo viene chiamato, le previsioni vengono eseguite usando i dati di sensori più recenti disponibili e incapsulati nella **CurrentPrediction** oggetto.</span><span class="sxs-lookup"><span data-stu-id="6bef2-118">When this method is called, predictions are made using the latest sensor data available, and encapsulated in **CurrentPrediction** object.</span></span>

<span data-ttu-id="6bef2-119">Un nuovo oggetto frame da utilizzare per ogni fotogramma sottoposto a rendering come è valido solo per un istante nel tempo.</span><span class="sxs-lookup"><span data-stu-id="6bef2-119">A new frame object must be used for each rendered frame as it is only valid for an instant in time.</span></span> <span data-ttu-id="6bef2-120">Il **CurrentPrediction** proprietà contiene informazioni quali la posizione della camera.</span><span class="sxs-lookup"><span data-stu-id="6bef2-120">The **CurrentPrediction** property contains information such as the camera position.</span></span> <span data-ttu-id="6bef2-121">Le informazioni sono estrapolate per il momento esatto in cui è previsto che il frame sia visibile all'utente.</span><span class="sxs-lookup"><span data-stu-id="6bef2-121">The information is extrapolated to the exact moment in time when the frame is expected to be visible to the user.</span></span>

<span data-ttu-id="6bef2-122">Il codice seguente è un estratto **AppMain::Update**:</span><span class="sxs-lookup"><span data-stu-id="6bef2-122">The following code is excerpted from **AppMain::Update**:</span></span>

```cpp
// The HolographicFrame has information that the app needs in order
// to update and render the current frame. The app begins each new
// frame by calling CreateNextFrame.
HolographicFrame holographicFrame = m_holographicSpace.CreateNextFrame();

// Get a prediction of where holographic cameras will be when this frame
// is presented.
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="process-camera-updates"></a><span data-ttu-id="6bef2-123">Elaborazione degli aggiornamenti della fotocamera</span><span class="sxs-lookup"><span data-stu-id="6bef2-123">Process camera updates</span></span>

<span data-ttu-id="6bef2-124">I buffer nascosti modificabili da fotogramma per fotogramma.</span><span class="sxs-lookup"><span data-stu-id="6bef2-124">Back buffers can change from frame to frame.</span></span> <span data-ttu-id="6bef2-125">Le esigenze delle app per convalidare la parte posteriore del buffer per ogni videocamera e rilasciano e ricreare le viste di risorsa e i buffer di profondità in base alle esigenze.</span><span class="sxs-lookup"><span data-stu-id="6bef2-125">Your app needs to validate the back buffer for each camera, and release and recreate resource views and depth buffers as needed.</span></span> <span data-ttu-id="6bef2-126">Si noti che il set di può causare nella stima è l'elenco autorevole delle videocamere utilizzato nel frame corrente.</span><span class="sxs-lookup"><span data-stu-id="6bef2-126">Notice that the set of poses in the prediction is the authoritative list of cameras being used in the current frame.</span></span> <span data-ttu-id="6bef2-127">È in genere, usare questo elenco per eseguire l'iterazione sul set di fotocamere digitali.</span><span class="sxs-lookup"><span data-stu-id="6bef2-127">Usually, you use this list to iterate on the set of cameras.</span></span>

<span data-ttu-id="6bef2-128">Dal **AppMain::Update**:</span><span class="sxs-lookup"><span data-stu-id="6bef2-128">From **AppMain::Update**:</span></span>

```cpp
m_deviceResources->EnsureCameraResources(holographicFrame, prediction);
```

<span data-ttu-id="6bef2-129">Dal **DeviceResources::EnsureCameraResources**:</span><span class="sxs-lookup"><span data-stu-id="6bef2-129">From **DeviceResources::EnsureCameraResources**:</span></span>

```cpp
for (HolographicCameraPose const& cameraPose : prediction.CameraPoses())
{
    HolographicCameraRenderingParameters renderingParameters = frame.GetRenderingParameters(cameraPose);
    CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();
    pCameraResources->CreateResourcesForBackBuffer(this, renderingParameters);
}
```

### <a name="get-the-coordinate-system-to-use-as-a-basis-for-rendering"></a><span data-ttu-id="6bef2-130">Ottenere il sistema di coordinate da utilizzare come base per il rendering</span><span class="sxs-lookup"><span data-stu-id="6bef2-130">Get the coordinate system to use as a basis for rendering</span></span>

<span data-ttu-id="6bef2-131">Realtà mista di Windows consente all'app di creare vari [sistemi di coordinate](coordinate-systems-in-directx.md) in base alle esigenze, ad esempio il frame di riferimento collegati e il frame di riferimento fisso, che tengono traccia dei percorsi nel mondo fisico.</span><span class="sxs-lookup"><span data-stu-id="6bef2-131">Windows Mixed Reality lets your app create various [coordinate systems](coordinate-systems-in-directx.md) as needed, such as the attached reference frame and the stationary reference frame, that track locations in the physical world.</span></span> <span data-ttu-id="6bef2-132">L'app può quindi usare questi sistemi di coordinate per motivo sulla posizione in cui eseguire il rendering di ogni fotogramma vntana.</span><span class="sxs-lookup"><span data-stu-id="6bef2-132">Your app can then use these coordinate systems to reason about where to render holograms each frame.</span></span> <span data-ttu-id="6bef2-133">Quando si richiedono le coordinate da un'API, verrà sempre passato il <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> all'interno di cui si desidera queste coordinate per esprimere.</span><span class="sxs-lookup"><span data-stu-id="6bef2-133">When requesting coordinates from an API, you will always pass in the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> within which you want those coordinates to be expressed.</span></span>

<span data-ttu-id="6bef2-134">Dal **AppMain::Update**:</span><span class="sxs-lookup"><span data-stu-id="6bef2-134">From **AppMain::Update**:</span></span>

```cpp
pose = SpatialPointerPose::TryGetAtTimestamp(
    m_stationaryReferenceFrame.CoordinateSystem(), prediction.Timestamp());
```

<span data-ttu-id="6bef2-135">Questi sistemi di coordinate è quindi utilizzabile per generare matrici stereo visualizzazione durante il rendering del contenuto nella scena.</span><span class="sxs-lookup"><span data-stu-id="6bef2-135">These coordinate systems can then be used to generate stereo view matrices when rendering the content in your scene.</span></span>

<span data-ttu-id="6bef2-136">From **CameraResources::UpdateViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="6bef2-136">From **CameraResources::UpdateViewProjectionBuffer**:</span></span>

```cpp
// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);
```

### <a name="process-gaze-and-gesture-input"></a><span data-ttu-id="6bef2-137">Sguardo processo e il movimento di input</span><span class="sxs-lookup"><span data-stu-id="6bef2-137">Process gaze and gesture input</span></span>

<span data-ttu-id="6bef2-138">[Estasiati](gaze-in-directx.md) e [mano](hands-and-motion-controllers-in-directx.md) non sono basati sul tempo di input e pertanto non è necessario aggiornare il **StepTimer** (funzione).</span><span class="sxs-lookup"><span data-stu-id="6bef2-138">[Gaze](gaze-in-directx.md) and [hand](hands-and-motion-controllers-in-directx.md) input are not time-based and thus do not have to update in the **StepTimer** function.</span></span> <span data-ttu-id="6bef2-139">Tuttavia questo input è qualcosa che l'app deve esaminare ogni fotogramma.</span><span class="sxs-lookup"><span data-stu-id="6bef2-139">However this input is something that the app needs to look at each frame.</span></span>

### <a name="process-time-based-updates"></a><span data-ttu-id="6bef2-140">Elaborazione degli aggiornamenti basati sul tempo</span><span class="sxs-lookup"><span data-stu-id="6bef2-140">Process time-based updates</span></span>

<span data-ttu-id="6bef2-141">Qualsiasi app in tempo reale per il rendering sarà necessario trovare un modo per elaborare gli aggiornamenti basati sul tempo. Offriamo un modo per eseguire questa operazione nel modello di app Windows Holographic tramite un **StepTimer** implementazione.</span><span class="sxs-lookup"><span data-stu-id="6bef2-141">Any real-time rendering app will need some way to process time-based updates; we provide a way to do this in the Windows Holographic app template via a **StepTimer** implementation.</span></span> <span data-ttu-id="6bef2-142">Ciò è simile al StepTimer fornito nel modello di app DirectX 11 UWP, pertanto se sono già stati analizzati tale modello dovrebbe essere familiare attraverso modalità.</span><span class="sxs-lookup"><span data-stu-id="6bef2-142">This is similar to the StepTimer provided in the DirectX 11 UWP app template, so if you already have looked at that template you should be on familiar ground.</span></span> <span data-ttu-id="6bef2-143">Questa classe helper di esempio StepTimer è in grado di fornire aggiornamenti intervallo temporale fissi, nonché gli aggiornamenti di variabile-intervallo temporale e la modalità predefinita è intervalli temporali di variabile.</span><span class="sxs-lookup"><span data-stu-id="6bef2-143">This StepTimer sample helper class is able to provide fixed time-step updates, as well as variable time-step updates, and the default mode is variable time steps.</span></span>

<span data-ttu-id="6bef2-144">Nel caso di rendering holographic, abbiamo scelto in modo specifico per non inserire troppi alla funzione timer.</span><span class="sxs-lookup"><span data-stu-id="6bef2-144">In the case of holographic rendering, we've specifically chosen not to put too much into the timer function.</span></span> <span data-ttu-id="6bef2-145">Infatti, è possibile configurare in modo che sia un passaggio di tempo fisso, nel qual caso potrebbe essere chiamata più volte per ogni fotogramma, o non ereditarli affatto, per alcuni fotogrammi – e gli aggiornamenti dati holographic devono avvengono una sola volta per ogni fotogramma.</span><span class="sxs-lookup"><span data-stu-id="6bef2-145">This is because you can configure it to be a fixed time step, in which case it might get called more than once per frame – or not at all, for some frames – and our holographic data updates should happen once per frame.</span></span>


<span data-ttu-id="6bef2-146">Dal **AppMain::Update**:</span><span class="sxs-lookup"><span data-stu-id="6bef2-146">From **AppMain::Update**:</span></span>

```cpp
m_timer.Tick([this]()
{
    m_spinningCubeRenderer->Update(m_timer);
});
```

### <a name="position-and-rotate-holograms-in-your-coordinate-system"></a><span data-ttu-id="6bef2-147">Posizione e la rotazione vntana nel sistema di coordinate</span><span class="sxs-lookup"><span data-stu-id="6bef2-147">Position and rotate holograms in your coordinate system</span></span>

<span data-ttu-id="6bef2-148">Se si opera in un singolo sistema di coordinate, così come il modello con il **SpatialStationaryReferenceFrame**, questo processo non è diverso da quello che si sta in caso contrario utilizzate per nella grafica 3D.</span><span class="sxs-lookup"><span data-stu-id="6bef2-148">If you are operating in a single coordinate system, as the template does with the **SpatialStationaryReferenceFrame**, this process isn't different from what you're otherwise used to in 3D graphics.</span></span> <span data-ttu-id="6bef2-149">In questo caso, si ruota il cubo e imposta la matrice di modello rispetto alla posizione nel sistema di coordinate fermo.</span><span class="sxs-lookup"><span data-stu-id="6bef2-149">Here, we rotate the cube and set the model matrix relative to the position in the stationary coordinate system.</span></span>

<span data-ttu-id="6bef2-150">From **SpinningCubeRenderer::Update**:</span><span class="sxs-lookup"><span data-stu-id="6bef2-150">From **SpinningCubeRenderer::Update**:</span></span>

```cpp
// Rotate the cube.
// Convert degrees to radians, then convert seconds to rotation angle.
const float    radiansPerSecond = XMConvertToRadians(m_degreesPerSecond);
const double   totalRotation = timer.GetTotalSeconds() * radiansPerSecond;
const float    radians = static_cast<float>(fmod(totalRotation, XM_2PI));
const XMMATRIX modelRotation = XMMatrixRotationY(-radians);

// Position the cube.
const XMMATRIX modelTranslation = XMMatrixTranslationFromVector(XMLoadFloat3(&m_position));

// Multiply to get the transform matrix.
// Note that this transform does not enforce a particular coordinate system. The calling
// class is responsible for rendering this content in a consistent manner.
const XMMATRIX modelTransform = XMMatrixMultiply(modelRotation, modelTranslation);

// The view and projection matrices are provided by the system; they are associated
// with holographic cameras, and updated on a per-camera basis.
// Here, we provide the model transform for the sample hologram. The model transform
// matrix is transposed to prepare it for the shader.
XMStoreFloat4x4(&m_modelConstantBufferData.model, XMMatrixTranspose(modelTransform));
```

<span data-ttu-id="6bef2-151">**Nota sugli scenari avanzati:** Il cubo rotante è un esempio molto semplice di come posizionare un ologrammi all'interno di un singolo fotogramma di riferimento.</span><span class="sxs-lookup"><span data-stu-id="6bef2-151">**Note about advanced scenarios:** The spinning cube is a very simple example of how to position a hologram within a single reference frame.</span></span> <span data-ttu-id="6bef2-152">È anche possibile [utilizzare più SpatialCoordinateSystems](coordinate-systems-in-directx.md) nello stesso frame sottoposto a rendering, nello stesso momento.</span><span class="sxs-lookup"><span data-stu-id="6bef2-152">It's also possible to [use multiple SpatialCoordinateSystems](coordinate-systems-in-directx.md) in the same rendered frame, at the same time.</span></span>

### <a name="update-constant-buffer-data"></a><span data-ttu-id="6bef2-153">Aggiornare i dati nel buffer costanti</span><span class="sxs-lookup"><span data-stu-id="6bef2-153">Update constant buffer data</span></span>

<span data-ttu-id="6bef2-154">Trasformazioni di modello per il contenuto vengono aggiornate come di consueto.</span><span class="sxs-lookup"><span data-stu-id="6bef2-154">Model transforms for content are updated as usual.</span></span> <span data-ttu-id="6bef2-155">A questo punto, si verranno calcolata trasformazioni valide per il sistema di coordinate in che è sarà per il rendering.</span><span class="sxs-lookup"><span data-stu-id="6bef2-155">By now, you will have computed valid transforms for the coordinate system you'll be rendering in.</span></span>

<span data-ttu-id="6bef2-156">From **SpinningCubeRenderer::Update**:</span><span class="sxs-lookup"><span data-stu-id="6bef2-156">From **SpinningCubeRenderer::Update**:</span></span>

```cpp
// Update the model transform buffer for the hologram.
context->UpdateSubresource(
    m_modelConstantBuffer.Get(),
    0,
    nullptr,
    &m_modelConstantBufferData,
    0,
    0
);
```

<span data-ttu-id="6bef2-157">Per quanto riguarda le trasformazioni di proiezione e di visualizzazione?</span><span class="sxs-lookup"><span data-stu-id="6bef2-157">What about view and projection transforms?</span></span> <span data-ttu-id="6bef2-158">Per ottenere risultati ottimali, si vuole attendere fino a quando non si è quasi pronti per le chiamate di disegno prima di addentrarsi questi.</span><span class="sxs-lookup"><span data-stu-id="6bef2-158">For best results, we want to wait until we're almost ready for our draw calls before we get these.</span></span>

## <a name="render-the-current-frame"></a><span data-ttu-id="6bef2-159">Eseguire il rendering il frame corrente</span><span class="sxs-lookup"><span data-stu-id="6bef2-159">Render the current frame</span></span>

<span data-ttu-id="6bef2-160">Il rendering in realtà mista di Windows non è molto diverso dal rendering su uno schermo di mono 2D, ma esistono alcune differenze di che è necessario essere a conoscenza:</span><span class="sxs-lookup"><span data-stu-id="6bef2-160">Rendering on Windows Mixed Reality is not much different from rendering on a 2D mono display, but there are some differences you need to be aware of:</span></span>
* <span data-ttu-id="6bef2-161">Le stime holographic frame sono importanti.</span><span class="sxs-lookup"><span data-stu-id="6bef2-161">Holographic frame predictions are important.</span></span> <span data-ttu-id="6bef2-162">Si avvicina alla stima consiste nella quando viene presentato il frame, migliore sarà il vntana avrà un aspetto.</span><span class="sxs-lookup"><span data-stu-id="6bef2-162">The closer the prediction is to when your frame is presented, the better your holograms will look.</span></span>
* <span data-ttu-id="6bef2-163">Realtà mista di Windows controlla le viste della fotocamera.</span><span class="sxs-lookup"><span data-stu-id="6bef2-163">Windows Mixed Reality controls the camera views.</span></span> <span data-ttu-id="6bef2-164">È necessario eseguire il rendering in ciascuno di essi in quanto il frame holographic terrà una presentazione li automaticamente in un secondo momento.</span><span class="sxs-lookup"><span data-stu-id="6bef2-164">You need to render to each one because the holographic frame will be presenting them for you later.</span></span>
* <span data-ttu-id="6bef2-165">È consigliabile stereo per il rendering di questo strumento equivalgano disegno creato in una matrice di destinazione di rendering.</span><span class="sxs-lookup"><span data-stu-id="6bef2-165">Stereo rendering is recommended to be accomplished using instanced drawing to a render target array.</span></span> <span data-ttu-id="6bef2-166">Il modello di app holographic Usa l'approccio consigliato di disegno creato in una matrice di destinazione di rendering, che usa una visualizzazione destinazione rendering su un **Texture2DArray**.</span><span class="sxs-lookup"><span data-stu-id="6bef2-166">The holographic app template uses the recommended approach of instanced drawing to a render target array, which uses a render target view onto a **Texture2DArray**.</span></span>
* <span data-ttu-id="6bef2-167">Se si desidera eseguire il rendering senza l'utilizzo delle istanze stereo, è necessario creare due RenderTargetViews non di matrice, una per ogni sotto controllo, che ogni riferimento uno dei due periodi nel **Texture2DArray** fornita per l'app dal sistema.</span><span class="sxs-lookup"><span data-stu-id="6bef2-167">If you want to render without using stereo instancing, you will need to create two non-array RenderTargetViews (one for each eye) that each reference one of the two slices in the **Texture2DArray** provided to the app from the system.</span></span> <span data-ttu-id="6bef2-168">Ciò non è consigliabile, perché è in genere notevolmente più lento rispetto all'uso delle istanze.</span><span class="sxs-lookup"><span data-stu-id="6bef2-168">This is not recommended, as it is typically significantly slower than using instancing.</span></span>

### <a name="get-an-updated-holographicframe-prediction"></a><span data-ttu-id="6bef2-169">Ottenere una stima HolographicFrame aggiornato</span><span class="sxs-lookup"><span data-stu-id="6bef2-169">Get an updated HolographicFrame prediction</span></span>

<span data-ttu-id="6bef2-170">L'aggiornamento alla stima di frame migliora l'efficacia di stabilizzazione di immagine e consente il posizionamento più preciso di vntana a causa del tempo più breve tra la stima e quando il frame è visibile all'utente.</span><span class="sxs-lookup"><span data-stu-id="6bef2-170">Updating the frame prediction enhances the effectiveness of image stabilization and allows for more accurate positioning of holograms due to the shorter time between the prediction and when the frame is visible to the user.</span></span> <span data-ttu-id="6bef2-171">In teoria, aggiornare la stima di frame appena prima del rendering.</span><span class="sxs-lookup"><span data-stu-id="6bef2-171">Ideally update your frame prediction just before rendering.</span></span>

```cpp
holographicFrame.UpdateCurrentPrediction();
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="render-to-each-camera"></a><span data-ttu-id="6bef2-172">Eseguire il rendering per ogni videocamera</span><span class="sxs-lookup"><span data-stu-id="6bef2-172">Render to each camera</span></span>

<span data-ttu-id="6bef2-173">Il ciclo sul set di fotocamera può causare la stima e il rendering a ogni tipo di camera in questo set.</span><span class="sxs-lookup"><span data-stu-id="6bef2-173">Loop on the set of camera poses in the prediction, and render to each camera in this set.</span></span>

<span data-ttu-id="6bef2-174">**Configurare il passaggio di rendering**</span><span class="sxs-lookup"><span data-stu-id="6bef2-174">**Set up your rendering pass**</span></span>

<span data-ttu-id="6bef2-175">Realtà mista di Windows usa per il rendering stereoscopico per migliorare l'illusione di profondità e per eseguire il rendering stereoscopicamente, in modo da sinistra e la visualizzazione a destra sono attivi.</span><span class="sxs-lookup"><span data-stu-id="6bef2-175">Windows Mixed Reality uses stereoscopic rendering to enhance the illusion of depth and to render stereoscopically, so both the left and the right display are active.</span></span> <span data-ttu-id="6bef2-176">Con il rendering stereoscopico è presente un offset da una schermata, che può risolvere le differenze tra il cervello come profondità effettivo.</span><span class="sxs-lookup"><span data-stu-id="6bef2-176">With stereoscopic rendering there is an offset between the two displays, which the brain can reconcile as actual depth.</span></span> <span data-ttu-id="6bef2-177">Questa sezione illustra stereoscopico per il rendering tramite la creazione di istanze, tramite codice dal modello di app Windows Holographic.</span><span class="sxs-lookup"><span data-stu-id="6bef2-177">This section covers stereoscopic rendering using instancing, using code from the Windows Holographic app template.</span></span>

<span data-ttu-id="6bef2-178">Ogni videocamera ha il proprio rendering (buffer nascosto), destinazione e di visualizzazione e di proiezione le matrici, nello spazio holographic.</span><span class="sxs-lookup"><span data-stu-id="6bef2-178">Each camera has its own render target (back buffer), and view and projection matrices, into the holographic space.</span></span> <span data-ttu-id="6bef2-179">L'app dovrà creare qualsiasi altra basata su fotocamera risorsa - ad esempio il buffer di profondità - pagamento in base al fotocamera.</span><span class="sxs-lookup"><span data-stu-id="6bef2-179">Your app will need to create any other camera-based resources - such as the depth buffer - on a per-camera basis.</span></span> <span data-ttu-id="6bef2-180">Il modello di app Windows Holographic, fornisce una classe helper per creare un bundle queste risorse insieme in DX::CameraResources.</span><span class="sxs-lookup"><span data-stu-id="6bef2-180">In the Windows Holographic app template, we provide a helper class to bundle these resources together in DX::CameraResources.</span></span> <span data-ttu-id="6bef2-181">Inizia configurando le visualizzazioni destinazione rendering:</span><span class="sxs-lookup"><span data-stu-id="6bef2-181">Start by setting up the render target views:</span></span>

<span data-ttu-id="6bef2-182">Dal **AppMain::Render**:</span><span class="sxs-lookup"><span data-stu-id="6bef2-182">From **AppMain::Render**:</span></span>

```cpp
// This represents the device-based resources for a HolographicCamera.
DX::CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();

// Get the device context.
const auto context = m_deviceResources->GetD3DDeviceContext();
const auto depthStencilView = pCameraResources->GetDepthStencilView();

// Set render targets to the current holographic camera.
ID3D11RenderTargetView *const targets[1] =
    { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, depthStencilView);

// Clear the back buffer and depth stencil view.
if (m_canGetHolographicDisplayForCamera &&
    cameraPose.HolographicCamera().Display().IsOpaque())
{
    context->ClearRenderTargetView(targets[0], DirectX::Colors::CornflowerBlue);
}
else
{
    context->ClearRenderTargetView(targets[0], DirectX::Colors::Transparent);
}
context->ClearDepthStencilView(
    depthStencilView, D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);
```

<span data-ttu-id="6bef2-183">**Usare la stima per ottenere le matrici di visualizzazione e di proiezione della fotocamera**</span><span class="sxs-lookup"><span data-stu-id="6bef2-183">**Use the prediction to get the view and projection matrices for the camera**</span></span>

<span data-ttu-id="6bef2-184">Le matrici di visualizzazione e di proiezione per ogni videocamera holographic verranno modificato con ogni fotogramma.</span><span class="sxs-lookup"><span data-stu-id="6bef2-184">The view and projection matrices for each holographic camera will change with every frame.</span></span> <span data-ttu-id="6bef2-185">Aggiornare i dati nel buffer di costanti per ogni videocamera holographic.</span><span class="sxs-lookup"><span data-stu-id="6bef2-185">Refresh the data in the constant buffer for each holographic camera.</span></span> <span data-ttu-id="6bef2-186">Eseguire questa operazione dopo che è stato aggiornato di stima, e prima di apportare qualsiasi draw chiama per tale fotocamera.</span><span class="sxs-lookup"><span data-stu-id="6bef2-186">Do this after you updated the prediction, and before you make any draw calls for that camera.</span></span>

<span data-ttu-id="6bef2-187">Dal **AppMain::Render**:</span><span class="sxs-lookup"><span data-stu-id="6bef2-187">From **AppMain::Render**:</span></span>

```cpp
// The view and projection matrices for each holographic camera will change
// every frame. This function refreshes the data in the constant buffer for
// the holographic camera indicated by cameraPose.
if (m_stationaryReferenceFrame)
{
    pCameraResources->UpdateViewProjectionBuffer(
        m_deviceResources, cameraPose, m_stationaryReferenceFrame.CoordinateSystem());
}

// Attach the view/projection constant buffer for this camera to the graphics pipeline.
bool cameraActive = pCameraResources->AttachViewProjectionBuffer(m_deviceResources);
```

<span data-ttu-id="6bef2-188">Di seguito viene illustrato come le matrici vengono acquisite dal posa fotocamera.</span><span class="sxs-lookup"><span data-stu-id="6bef2-188">Here, we show how the matrices are acquired from the camera pose.</span></span> <span data-ttu-id="6bef2-189">Durante questo processo è anche possibile ottenere il viewport per la fotocamera.</span><span class="sxs-lookup"><span data-stu-id="6bef2-189">During this process we also obtain the current viewport for the camera.</span></span> <span data-ttu-id="6bef2-190">Si noti come presentiamo un sistema di coordinate: questo è il sistema di coordinate stesso è stato usato per comprendere sguardo ed è uguale a quello abbiamo usati per posizionare il cubo rotante.</span><span class="sxs-lookup"><span data-stu-id="6bef2-190">Note how we provide a coordinate system: this is the same coordinate system we used to understand gaze, and it's the same one we used to position the spinning cube.</span></span>


<span data-ttu-id="6bef2-191">From **CameraResources::UpdateViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="6bef2-191">From **CameraResources::UpdateViewProjectionBuffer**:</span></span>

```cpp
// The system changes the viewport on a per-frame basis for system optimizations.
auto viewport = cameraPose.Viewport();
m_d3dViewport = CD3D11_VIEWPORT(
    viewport.X,
    viewport.Y,
    viewport.Width,
    viewport.Height
);

// The projection transform for each frame is provided by the HolographicCameraPose.
HolographicStereoTransform cameraProjectionTransform = cameraPose.ProjectionTransform();

// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);

// If TryGetViewTransform returns a null pointer, that means the pose and coordinate
// system cannot be understood relative to one another; content cannot be rendered
// in this coordinate system for the duration of the current frame.
// This usually means that positional tracking is not active for the current frame, in
// which case it is possible to use a SpatialLocatorAttachedFrameOfReference to render
// content that is not world-locked instead.
DX::ViewProjectionConstantBuffer viewProjectionConstantBufferData;
bool viewTransformAcquired = viewTransformContainer != nullptr;
if (viewTransformAcquired)
{
    // Otherwise, the set of view transforms can be retrieved.
    HolographicStereoTransform viewCoordinateSystemTransform = viewTransformContainer.Value();

    // Update the view matrices. Holographic cameras (such as Microsoft HoloLens) are
    // constantly moving relative to the world. The view matrices need to be updated
    // every frame.
    XMStoreFloat4x4(
        &viewProjectionConstantBufferData.viewProjection[0],
        XMMatrixTranspose(XMLoadFloat4x4(&viewCoordinateSystemTransform.Left) *
            XMLoadFloat4x4(&cameraProjectionTransform.Left))
    );
    XMStoreFloat4x4(
        &viewProjectionConstantBufferData.viewProjection[1],
        XMMatrixTranspose(XMLoadFloat4x4(&viewCoordinateSystemTransform.Right) *
            XMLoadFloat4x4(&cameraProjectionTransform.Right))
    );
}
```

<span data-ttu-id="6bef2-192">Il viewport deve essere impostato ogni fotogramma.</span><span class="sxs-lookup"><span data-stu-id="6bef2-192">The viewport should be set each frame.</span></span> <span data-ttu-id="6bef2-193">Shader vertice (minimo) in genere necessario accedere ai dati di visualizzazione o di proiezione.</span><span class="sxs-lookup"><span data-stu-id="6bef2-193">Your vertex shader (at least) will generally need access to the view/projection data.</span></span>


<span data-ttu-id="6bef2-194">Dal **CameraResources::AttachViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="6bef2-194">From **CameraResources::AttachViewProjectionBuffer**:</span></span>

```cpp
// Set the viewport for this camera.
context->RSSetViewports(1, &m_d3dViewport);

// Send the constant buffer to the vertex shader.
context->VSSetConstantBuffers(
    1,
    1,
    m_viewProjectionConstantBuffer.GetAddressOf()
);
```

<span data-ttu-id="6bef2-195">**Eseguire il rendering per il buffer nascosto della fotocamera ed eseguire il commit il buffer di profondità**:</span><span class="sxs-lookup"><span data-stu-id="6bef2-195">**Render to the camera back buffer and commit the depth buffer**:</span></span>

<span data-ttu-id="6bef2-196">È una buona idea per verificare che **TryGetViewTransform** ha avuto esito positivo prima di provare a usare i dati di visualizzazione o di proiezione, in quanto se il sistema di coordinate non è individuabile (ad esempio, il rilevamento è stata interrotta) l'app non è possibile eseguire il rendering con esso per tale frame.</span><span class="sxs-lookup"><span data-stu-id="6bef2-196">It's a good idea to check that **TryGetViewTransform** succeeded before trying to use the view/projection data, because if the coordinate system is not locatable (e.g., tracking was interrupted) your app cannot render with it for that frame.</span></span> <span data-ttu-id="6bef2-197">Il modello chiama solo **eseguire il rendering** sul cubo rotante se il **CameraResources** classe indica che l'aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="6bef2-197">The template only calls **Render** on the spinning cube if the **CameraResources** class indicates a successful update.</span></span>

<span data-ttu-id="6bef2-198">Per mantenere vntana in cui uno sviluppatore o un utente li inserisce nel mondo, realtà mista di Windows include funzionalità per [immagine della stabilizzazione](hologram-stability.md).</span><span class="sxs-lookup"><span data-stu-id="6bef2-198">To keep holograms where a developer or a user puts them in the world, Windows Mixed Reality includes features for [image stabilization](hologram-stability.md).</span></span> <span data-ttu-id="6bef2-199">Stabilizzazione immagine consente di nascondere la latenza intrinseca in una pipeline di rendering per garantire le migliori esperienze holographic per gli utenti; un punto di stato attivo può essere specificato per migliorare ulteriormente la stabilizzazione immagine o un buffer di profondità può essere fornito per il calcolo con ottimizzazione per la stabilizzazione immagine in tempo reale.</span><span class="sxs-lookup"><span data-stu-id="6bef2-199">Image stabilization helps hide the latency inherent in a rendering pipeline to ensure the best holographic experiences for users; a focus point may be specified to enhance image stabilization even further, or a depth buffer may be provided to compute optimized image stabilization in real time.</span></span>

<span data-ttu-id="6bef2-200">Per ottenere risultati ottimali, l'app deve fornire un buffer di profondità tramite il <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API.</span><span class="sxs-lookup"><span data-stu-id="6bef2-200">For best results, your app should provide a depth buffer using the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API.</span></span> <span data-ttu-id="6bef2-201">Realtà mista di Windows possono utilizzare informazioni geometry dal buffer di profondità per ottimizzare la stabilizzazione immagine in tempo reale.</span><span class="sxs-lookup"><span data-stu-id="6bef2-201">Windows Mixed Reality can then use geometry information from the depth buffer to optimize image stabilization in real time.</span></span> <span data-ttu-id="6bef2-202">Il modello di app per Windows Holographic esegue il commit del buffer di profondità dell'app per impostazione predefinita, consentire l'ottimizzazione della stabilità di ologramma.</span><span class="sxs-lookup"><span data-stu-id="6bef2-202">The Windows Holographic app template commits the app's depth buffer by default, helping optimize hologram stability.</span></span>

<span data-ttu-id="6bef2-203">Dal **AppMain::Render**:</span><span class="sxs-lookup"><span data-stu-id="6bef2-203">From **AppMain::Render**:</span></span>

```cpp
// Only render world-locked content when positional tracking is active.
if (cameraActive)
{
    // Draw the sample hologram.
    m_spinningCubeRenderer->Render();
    if (m_canCommitDirect3D11DepthBuffer)
    {
        // On versions of the platform that support the CommitDirect3D11DepthBuffer API, we can 
        // provide the depth buffer to the system, and it will use depth information to stabilize 
        // the image at a per-pixel level.
        HolographicCameraRenderingParameters renderingParameters =
            holographicFrame.GetRenderingParameters(cameraPose);
        
        IDirect3DSurface interopSurface =
            DX::CreateDepthTextureInteropObject(pCameraResources->GetDepthStencilTexture2D());

        // Calling CommitDirect3D11DepthBuffer causes the system to queue Direct3D commands to 
        // read the depth buffer. It will then use that information to stabilize the image as
        // the HolographicFrame is presented.
        renderingParameters.CommitDirect3D11DepthBuffer(interopSurface);
    }
}
```

>[!NOTE]
><span data-ttu-id="6bef2-204">Windows elabora la trama profondità nella GPU, pertanto deve essere possibile usare i buffer di profondità come una risorsa shader.</span><span class="sxs-lookup"><span data-stu-id="6bef2-204">Windows will process your depth texture on the GPU, so it must be possible to use your depth buffer as a shader resource.</span></span> <span data-ttu-id="6bef2-205">ID3D11Texture2D creato deve essere in un formato senza tipo e deve essere associato come una visualizzazione di risorse shader.</span><span class="sxs-lookup"><span data-stu-id="6bef2-205">The ID3D11Texture2D that you create should be in a typeless format and it should be bound as a shader resource view.</span></span> <span data-ttu-id="6bef2-206">Di seguito è riportato un esempio di come creare una trama di profondità che può essere eseguito il commit per la stabilizzazione immagine.</span><span class="sxs-lookup"><span data-stu-id="6bef2-206">Here is an example of how to create a depth texture that can be committed for image stabilization.</span></span>

<span data-ttu-id="6bef2-207">Codice per un **creazione di risorse di buffer di profondità per CommitDirect3D11DepthBuffer**:</span><span class="sxs-lookup"><span data-stu-id="6bef2-207">Code for **Depth buffer resource creation for CommitDirect3D11DepthBuffer**:</span></span>

```cpp
// Create a depth stencil view for use with 3D rendering if needed.
CD3D11_TEXTURE2D_DESC depthStencilDesc(
    DXGI_FORMAT_R16_TYPELESS,
    static_cast<UINT>(m_d3dRenderTargetSize.Width),
    static_cast<UINT>(m_d3dRenderTargetSize.Height),
    m_isStereo ? 2 : 1, // Create two textures when rendering in stereo.
    1, // Use a single mipmap level.
    D3D11_BIND_DEPTH_STENCIL | D3D11_BIND_SHADER_RESOURCE
);

winrt::check_hresult(
    device->CreateTexture2D(
        &depthStencilDesc,
        nullptr,
        &m_d3dDepthStencil
    ));

CD3D11_DEPTH_STENCIL_VIEW_DESC depthStencilViewDesc(
    m_isStereo ? D3D11_DSV_DIMENSION_TEXTURE2DARRAY : D3D11_DSV_DIMENSION_TEXTURE2D,
    DXGI_FORMAT_D16_UNORM
);
winrt::check_hresult(
    device->CreateDepthStencilView(
        m_d3dDepthStencil.Get(),
        &depthStencilViewDesc,
        &m_d3dDepthStencilView
    ));
```

<span data-ttu-id="6bef2-208">**Creazione del contenuto holographic**</span><span class="sxs-lookup"><span data-stu-id="6bef2-208">**Draw holographic content**</span></span>

<span data-ttu-id="6bef2-209">Il modello di app per Windows Holographic esegue il rendering di contenuto nel formato stereo usando la tecnica consigliata di disegno di istanza geometry da un Texture2DArray di dimensione 2.</span><span class="sxs-lookup"><span data-stu-id="6bef2-209">The Windows Holographic app template renders content in stereo by using the recommended technique of drawing instanced geometry to a Texture2DArray of size 2.</span></span> <span data-ttu-id="6bef2-210">Esaminiamo la parte delle istanze di questo e il funzionamento in realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="6bef2-210">Let's look at the instancing part of this, and how it works on Windows Mixed Reality.</span></span>

<span data-ttu-id="6bef2-211">From **SpinningCubeRenderer::Render**:</span><span class="sxs-lookup"><span data-stu-id="6bef2-211">From **SpinningCubeRenderer::Render**:</span></span>

```cpp
// Draw the objects.
context->DrawIndexedInstanced(
    m_indexCount,   // Index count per instance.
    2,              // Instance count.
    0,              // Start index location.
    0,              // Base vertex location.
    0               // Start instance location.
);
```

<span data-ttu-id="6bef2-212">Ogni istanza accede a una matrice di proiezione/vista diverso dal buffer costante.</span><span class="sxs-lookup"><span data-stu-id="6bef2-212">Each instance accesses a different view/projection matrix from the constant buffer.</span></span> <span data-ttu-id="6bef2-213">Ecco la struttura di buffer costante, che è semplicemente una matrice di 2 matrici.</span><span class="sxs-lookup"><span data-stu-id="6bef2-213">Here's the constant buffer structure, which is just an array of 2 matrices.</span></span>

<span data-ttu-id="6bef2-214">Dal **VertexShaderShared.hlsl**, incluso dal **VPRTVertexShader.hlsl**:</span><span class="sxs-lookup"><span data-stu-id="6bef2-214">From **VertexShaderShared.hlsl**, included by **VPRTVertexShader.hlsl**:</span></span>

```HLSL
// A constant buffer that stores each set of view and projection matrices in column-major format.
cbuffer ViewProjectionConstantBuffer : register(b1)
{
    float4x4 viewProjection[2];
};
```

<span data-ttu-id="6bef2-215">Indice della matrice di destinazione rendering deve essere impostata per ogni pixel.</span><span class="sxs-lookup"><span data-stu-id="6bef2-215">The render target array index must be set for each pixel.</span></span> <span data-ttu-id="6bef2-216">Nel frammento di codice seguente, output.viewId viene eseguito il mapping per il **SV_RenderTargetArrayIndex** semantico.</span><span class="sxs-lookup"><span data-stu-id="6bef2-216">In the following snippet, output.viewId is mapped to the **SV_RenderTargetArrayIndex** semantic.</span></span> <span data-ttu-id="6bef2-217">Si noti che questa operazione richiede il supporto per una funzionalità di Direct3D 11.3 facoltativa, che consente l'indice di matrice di destinazione rendering semantica impostarla da qualsiasi fase dello shader.</span><span class="sxs-lookup"><span data-stu-id="6bef2-217">Note that this requires support for an optional Direct3D 11.3 feature, which allows the render target array index semantic to be set from any shader stage.</span></span>

<span data-ttu-id="6bef2-218">Dal **VPRTVertexShader.hlsl**:</span><span class="sxs-lookup"><span data-stu-id="6bef2-218">From **VPRTVertexShader.hlsl**:</span></span>

```HLSL    
// Per-vertex data passed to the geometry shader.
struct VertexShaderOutput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;

    // The render target array index is set here in the vertex shader.
    uint        viewId  : SV_RenderTargetArrayIndex;
};
```

<span data-ttu-id="6bef2-219">Dal **VertexShaderShared.hlsl**, incluso dal **VPRTVertexShader.hlsl**:</span><span class="sxs-lookup"><span data-stu-id="6bef2-219">From **VertexShaderShared.hlsl**, included by **VPRTVertexShader.hlsl**:</span></span>

```HLSL
// Per-vertex data used as input to the vertex shader.
struct VertexShaderInput
{
    min16float3 pos     : POSITION;
    min16float3 color   : COLOR0;
    uint        instId  : SV_InstanceID;
};

// Simple shader to do vertex processing on the GPU.
VertexShaderOutput main(VertexShaderInput input)
{
    VertexShaderOutput output;
    float4 pos = float4(input.pos, 1.0f);

    // Note which view this vertex has been sent to. Used for matrix lookup.
    // Taking the modulo of the instance ID allows geometry instancing to be used
    // along with stereo instanced drawing; in that case, two copies of each 
    // instance would be drawn, one for left and one for right.
    int idx = input.instId % 2;

    // Transform the vertex position into world space.
    pos = mul(pos, model);

    // Correct for perspective and project the vertex position onto the screen.
    pos = mul(pos, viewProjection[idx]);
    output.pos = (min16float4)pos;

    // Pass the color through without modification.
    output.color = input.color;

    // Set the render target array index.
    output.viewId = idx;

    return output;
}
```

<span data-ttu-id="6bef2-220">Se si desidera utilizzare le proprie creata un'istanza di matrice di destinazione eseguire il rendering di tecniche di disegnare con questo metodo di disegno di un impianto stereo, tutto è necessario eseguire è creare due volte il numero di istanze in genere necessario.</span><span class="sxs-lookup"><span data-stu-id="6bef2-220">If you want to use your existing instanced drawing techniques with this method of drawing to a stereo render target array, all you have to do is draw twice the number of instances you normally have.</span></span> <span data-ttu-id="6bef2-221">Nello shader, dividere **input.instId** da 2 a ottenere l'ID istanza originale, che possono essere indicizzati, ad esempio, un buffer di dati per ogni oggetto: `int actualIdx = input.instId / 2;`</span><span class="sxs-lookup"><span data-stu-id="6bef2-221">In the shader, divide **input.instId** by 2 to get the original instance ID, which can be indexed into (for example) a buffer of per-object data: `int actualIdx = input.instId / 2;`</span></span>

### <a name="important-note-about-rendering-stereo-content-on-hololens"></a><span data-ttu-id="6bef2-222">Nota importante sul rendering del contenuto stereo su HoloLens</span><span class="sxs-lookup"><span data-stu-id="6bef2-222">Important note about rendering stereo content on HoloLens</span></span>

<span data-ttu-id="6bef2-223">Realtà mista di Windows supporta la possibilità di impostare l'indice di matrice di destinazione rendering da qualsiasi fase dello shader; in genere, si tratta di un'attività che poteva essere eseguita solo nella fase geometry shader a causa del modo in cui che la semantica viene definita per Direct3D 11.</span><span class="sxs-lookup"><span data-stu-id="6bef2-223">Windows Mixed Reality supports the ability to set the render target array index from any shader stage; normally, this is a task that could only be done in the geometry shader stage due to the way the semantic is defined for Direct3D 11.</span></span> <span data-ttu-id="6bef2-224">Di seguito viene illustrato un esempio completo di come configurare una pipeline di rendering con solo il pixel e vertex shader fasi set.</span><span class="sxs-lookup"><span data-stu-id="6bef2-224">Here, we show a complete example of how to set up a rendering pipeline with just the vertex and pixel shader stages set.</span></span> <span data-ttu-id="6bef2-225">Il codice dello shader è come descritto in precedenza.</span><span class="sxs-lookup"><span data-stu-id="6bef2-225">The shader code is as described above.</span></span>

<span data-ttu-id="6bef2-226">From **SpinningCubeRenderer::Render**:</span><span class="sxs-lookup"><span data-stu-id="6bef2-226">From **SpinningCubeRenderer::Render**:</span></span>

```cpp
const auto context = m_deviceResources->GetD3DDeviceContext();

// Each vertex is one instance of the VertexPositionColor struct.
const UINT stride = sizeof(VertexPositionColor);
const UINT offset = 0;
context->IASetVertexBuffers(
    0,
    1,
    m_vertexBuffer.GetAddressOf(),
    &stride,
    &offset
);
context->IASetIndexBuffer(
    m_indexBuffer.Get(),
    DXGI_FORMAT_R16_UINT, // Each index is one 16-bit unsigned integer (short).
    0
);
context->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);
context->IASetInputLayout(m_inputLayout.Get());

// Attach the vertex shader.
context->VSSetShader(
    m_vertexShader.Get(),
    nullptr,
    0
);
// Apply the model constant buffer to the vertex shader.
context->VSSetConstantBuffers(
    0,
    1,
    m_modelConstantBuffer.GetAddressOf()
);

// Attach the pixel shader.
context->PSSetShader(
    m_pixelShader.Get(),
    nullptr,
    0
);

// Draw the objects.
context->DrawIndexedInstanced(
    m_indexCount,   // Index count per instance.
    2,              // Instance count.
    0,              // Start index location.
    0,              // Base vertex location.
    0               // Start instance location.
);
```

### <a name="important-note-about-rendering-on-non-hololens-devices"></a><span data-ttu-id="6bef2-227">Nota importante sul rendering sui dispositivi non HoloLens</span><span class="sxs-lookup"><span data-stu-id="6bef2-227">Important note about rendering on non-HoloLens devices</span></span>

<span data-ttu-id="6bef2-228">L'impostazione di indice di matrice di destinazione di rendering nel vertex shader richiede che il driver di grafica supporta una funzionalità di Direct3D 11.3 facoltativa, che supporta HoloLens.</span><span class="sxs-lookup"><span data-stu-id="6bef2-228">Setting the render target array index in the vertex shader requires that the graphics driver supports an optional Direct3D 11.3 feature, which HoloLens does support.</span></span> <span data-ttu-id="6bef2-229">L'app potrebbe essere in grado di implementare in modo sicuro solo tale tecnica per il rendering e tutti i requisiti per l'esecuzione in di Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="6bef2-229">Your app may be able to safely implement just that technique for rendering, and all requirements will be met for running on the Microsoft HoloLens.</span></span>

<span data-ttu-id="6bef2-230">Potrebbe essere il caso che si desidera utilizzare HoloLens emulatore, che può essere uno strumento di sviluppo avanzato per l'app holographic - e supportare i dispositivi visore VR immersivi realtà mista di Windows che sono collegati a PC Windows 10.</span><span class="sxs-lookup"><span data-stu-id="6bef2-230">It may be the case that you want to use the HoloLens emulator as well, which can be a powerful development tool for your holographic app - and support Windows Mixed Reality immersive headset devices that are attached to Windows 10 PCs.</span></span> <span data-ttu-id="6bef2-231">Supporto per il percorso per il rendering non HoloLens - e di conseguenza, per tutti di realtà mista di Windows - viene compilato nel modello di app Windows Holographic.</span><span class="sxs-lookup"><span data-stu-id="6bef2-231">Support for the non-HoloLens rendering path - and therefore, for all of Windows Mixed Reality - is also built into the Windows Holographic app template.</span></span> <span data-ttu-id="6bef2-232">Nel codice del modello, si noterà codice per abilitare l'app holographic per l'esecuzione sulla GPU nel PC di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="6bef2-232">In the template code, you will find code to enable your holographic app to run on the GPU in your development PC.</span></span> <span data-ttu-id="6bef2-233">Ecco come la **DeviceResources** classe controlli per il supporto di questa funzionalità facoltativa.</span><span class="sxs-lookup"><span data-stu-id="6bef2-233">Here is how the **DeviceResources** class checks for this optional feature support.</span></span>

<span data-ttu-id="6bef2-234">Dal **DeviceResources::CreateDeviceResources**:</span><span class="sxs-lookup"><span data-stu-id="6bef2-234">From **DeviceResources::CreateDeviceResources**:</span></span>

```cpp
// Check for device support for the optional feature that allows setting the render target array index from the vertex shader stage.
D3D11_FEATURE_DATA_D3D11_OPTIONS3 options;
m_d3dDevice->CheckFeatureSupport(D3D11_FEATURE_D3D11_OPTIONS3, &options, sizeof(options));
if (options.VPAndRTArrayIndexFromAnyShaderFeedingRasterizer)
{
    m_supportsVprt = true;
}
```

<span data-ttu-id="6bef2-235">Per supportare il rendering senza questa funzionalità facoltativa, l'app deve usare un geometry shader per impostare l'indice di matrice di destinazione di rendering.</span><span class="sxs-lookup"><span data-stu-id="6bef2-235">To support rendering without this optional feature, your app must use a geometry shader to set the render target array index.</span></span> <span data-ttu-id="6bef2-236">È necessario aggiungere questo frammento di codice *dopo aver* **VSSetConstantBuffers**, e *prima* **PSSetShader** nell'esempio di codice illustrato nella precedente sezione che illustra come eseguire il rendering stereo su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="6bef2-236">This snippet would be added *after* **VSSetConstantBuffers**, and *before* **PSSetShader** in the code example shown in the previous section that explains how to render stereo on HoloLens.</span></span>

<span data-ttu-id="6bef2-237">From **SpinningCubeRenderer::Render**:</span><span class="sxs-lookup"><span data-stu-id="6bef2-237">From **SpinningCubeRenderer::Render**:</span></span>

```cpp
if (!m_usingVprtShaders)
{
    // On devices that do not support the D3D11_FEATURE_D3D11_OPTIONS3::
    // VPAndRTArrayIndexFromAnyShaderFeedingRasterizer optional feature,
    // a pass-through geometry shader is used to set the render target 
    // array index.
    context->GSSetShader(
        m_geometryShader.Get(),
        nullptr,
        0
    );
}
```

<span data-ttu-id="6bef2-238">**NOTA DI HLSL**: In questo caso, è necessario caricare un leggermente modificata vertex shader che passa l'indice di matrice di destinazione rendering di geometry shader usando un semantico, ad esempio TEXCOORD0 shader sempre consentito.</span><span class="sxs-lookup"><span data-stu-id="6bef2-238">**HLSL NOTE**: In this case, you must also load a slightly modified vertex shader that passes the render target array index to the geometry shader using an always-allowed shader semantic, such as TEXCOORD0.</span></span> <span data-ttu-id="6bef2-239">Geometry shader non è necessario eseguire alcuna operazione; geometry shader modello passa attraverso tutti i dati, fatta eccezione per l'indice di matrice destinazione rendering, che consente di impostare il SV_RenderTargetArrayIndex semantico.</span><span class="sxs-lookup"><span data-stu-id="6bef2-239">The geometry shader does not have to do any work; the template geometry shader passes through all data, with the exception of the render target array index, which is used to set the SV_RenderTargetArrayIndex semantic.</span></span>

<span data-ttu-id="6bef2-240">Codice del modello App per **GeometryShader.hlsl**:</span><span class="sxs-lookup"><span data-stu-id="6bef2-240">App template code for **GeometryShader.hlsl**:</span></span>

```HLSL
// Per-vertex data from the vertex shader.
struct GeometryShaderInput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;
    uint        instId  : TEXCOORD0;
};

// Per-vertex data passed to the rasterizer.
struct GeometryShaderOutput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;
    uint        rtvId   : SV_RenderTargetArrayIndex;
};

// This geometry shader is a pass-through that leaves the geometry unmodified 
// and sets the render target array index.
[maxvertexcount(3)]
void main(triangle GeometryShaderInput input[3], inout TriangleStream<GeometryShaderOutput> outStream)
{
    GeometryShaderOutput output;
    [unroll(3)]
    for (int i = 0; i < 3; ++i)
    {
        output.pos   = input[i].pos;
        output.color = input[i].color;
        output.rtvId = input[i].instId;
        outStream.Append(output);
    }
}
```

## <a name="present"></a><span data-ttu-id="6bef2-241">Presente</span><span class="sxs-lookup"><span data-stu-id="6bef2-241">Present</span></span>

### <a name="enable-the-holographic-frame-to-present-the-swap-chain"></a><span data-ttu-id="6bef2-242">Abilitare il frame holographic presentare la catena di scambio</span><span class="sxs-lookup"><span data-stu-id="6bef2-242">Enable the holographic frame to present the swap chain</span></span>

<span data-ttu-id="6bef2-243">Con realtà mista di Windows, il sistema controlla la catena di scambio.</span><span class="sxs-lookup"><span data-stu-id="6bef2-243">With Windows Mixed Reality, the system controls the swap chain.</span></span> <span data-ttu-id="6bef2-244">Il sistema gestisce quindi i frame presentazione a ogni tipo di camera holographic per garantire un'esperienza utente di alta qualità.</span><span class="sxs-lookup"><span data-stu-id="6bef2-244">The system then manages presenting frames to each holographic camera to ensure a high quality user experience.</span></span> <span data-ttu-id="6bef2-245">Fornisce inoltre un aggiornamento del riquadro di visualizzazione ogni fotogramma per ogni videocamera, per ottimizzare gli aspetti del sistema, ad esempio stabilizzazione immagine o acquisire realtà mista.</span><span class="sxs-lookup"><span data-stu-id="6bef2-245">It also provides a viewport update each frame, for each camera, to optimize aspects of the system such as image stabilization or Mixed Reality Capture.</span></span> <span data-ttu-id="6bef2-246">Pertanto, non chiama un'app holographic usando DirectX **presente** su DXGI una catena di scambio.</span><span class="sxs-lookup"><span data-stu-id="6bef2-246">So, a holographic app using DirectX doesn't call **Present** on a DXGI swap chain.</span></span> <span data-ttu-id="6bef2-247">Usare invece i <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> classe per presentare tutte le catene di scambio per un frame dopo aver completato lo disegna.</span><span class="sxs-lookup"><span data-stu-id="6bef2-247">Instead, you use the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> class to present all swapchains for a frame once you're done drawing it.</span></span>

<span data-ttu-id="6bef2-248">Dal **DeviceResources::Present**:</span><span class="sxs-lookup"><span data-stu-id="6bef2-248">From **DeviceResources::Present**:</span></span>

```
HolographicFramePresentResult presentResult = frame.PresentUsingCurrentPrediction();
```

<span data-ttu-id="6bef2-249">Per impostazione predefinita, questa API è in attesa per il frame terminare prima che venga restituito.</span><span class="sxs-lookup"><span data-stu-id="6bef2-249">By default, this API waits for the frame to finish before it returns.</span></span> <span data-ttu-id="6bef2-250">App holographic deve attendere per il frame precedente il completamento prima di iniziare a lavorare su un nuovo frame, perché questo riduce la latenza e consente per ottenere risultati migliori da stime holographic frame.</span><span class="sxs-lookup"><span data-stu-id="6bef2-250">Holographic apps should wait for the previous frame to finish before starting work on a new frame, because this reduces latency and allows for better results from holographic frame predictions.</span></span> <span data-ttu-id="6bef2-251">Si tratta di una regola del disco rigida e se si dispone di frame che richiedono più di aggiornamento di una schermata per il rendering è possono disabilitare questo tipo di attesa, passando il parametro HolographicFramePresentWaitBehavior <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>.</span><span class="sxs-lookup"><span data-stu-id="6bef2-251">This isn't a hard rule, and if you have frames that take longer than one screen refresh to render you can disable this wait by passing the HolographicFramePresentWaitBehavior parameter to <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>.</span></span> <span data-ttu-id="6bef2-252">In questo caso, probabilmente si utilizzerebbe un thread di rendering asincrono per gestire un carico continuo sulla GPU.</span><span class="sxs-lookup"><span data-stu-id="6bef2-252">In this case, you would likely use an asynchronous rendering thread in order to maintain a continuous load on the GPU.</span></span> <span data-ttu-id="6bef2-253">Si noti che la frequenza di aggiornamento del dispositivo HoloLens è 60hz, in cui un frame ha una durata pari a circa 16 ms.</span><span class="sxs-lookup"><span data-stu-id="6bef2-253">Note that the refresh rate of the HoloLens device is 60hz, where one frame has a duration of approximately 16 ms.</span></span> <span data-ttu-id="6bef2-254">I dispositivi visore VR immersivi possono variare da 60hz a 90hz; Quando si aggiornano la visualizzazione 90 Hz, ogni fotogramma avranno una durata pari a circa 11 ms.</span><span class="sxs-lookup"><span data-stu-id="6bef2-254">Immersive headset devices can range from 60hz to 90hz; when refreshing the display at 90 hz, each frame will have a duration of approximately 11 ms.</span></span>

### <a name="handle-devicelost-scenarios-in-cooperation-with-the-holographicframe"></a><span data-ttu-id="6bef2-255">Gestire gli scenari DeviceLost in collaborazione con il HolographicFrame</span><span class="sxs-lookup"><span data-stu-id="6bef2-255">Handle DeviceLost scenarios in cooperation with the HolographicFrame</span></span>

<span data-ttu-id="6bef2-256">App DirectX 11 in genere è necessario controllare il valore HRESULT restituito dalla catena di scambio DXGI **presente** funzione per scoprire se si è verificato un **DeviceLost** errore.</span><span class="sxs-lookup"><span data-stu-id="6bef2-256">DirectX 11 apps would typically want to check the HRESULT returned by the DXGI swap chain's **Present** function to find out if there was a **DeviceLost** error.</span></span> <span data-ttu-id="6bef2-257">Il <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> classe a farlo.</span><span class="sxs-lookup"><span data-stu-id="6bef2-257">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> class handles this for you.</span></span> <span data-ttu-id="6bef2-258">Esaminare i <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> restituisce per scoprire se è necessario rilasciare e ricreare il dispositivo Direct3D e le risorse basate sul dispositivo.</span><span class="sxs-lookup"><span data-stu-id="6bef2-258">Inspect the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> it returns to find out if you need to release and recreate the Direct3D device and device-based resources.</span></span>

```cpp
// The PresentUsingCurrentPrediction API will detect when the graphics device
// changes or becomes invalid. When this happens, it is considered a Direct3D
// device lost scenario.
if (presentResult == HolographicFramePresentResult::DeviceRemoved)
{
    // The Direct3D device, context, and resources should be recreated.
    HandleDeviceLost();
}
```

<span data-ttu-id="6bef2-259">Si noti che se il dispositivo Direct3D persa e si ricrearlo, è necessario indicare il <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> per iniziare a usare il nuovo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="6bef2-259">Note that if the Direct3D device was lost, and you did recreate it, you have to tell the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> to start using the new device.</span></span> <span data-ttu-id="6bef2-260">Verrà ricreata la catena di scambio per questo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="6bef2-260">The swap chain will be recreated for this device.</span></span>

<span data-ttu-id="6bef2-261">From **DeviceResources::InitializeUsingHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="6bef2-261">From **DeviceResources::InitializeUsingHolographicSpace**:</span></span>

```
m_holographicSpace.SetDirect3D11Device(m_d3dInteropDevice);
```

<span data-ttu-id="6bef2-262">Una volta che viene presentato il frame, è possibile tornare indietro al ciclo di programma principale e consentirgli di continuare al frame successivo.</span><span class="sxs-lookup"><span data-stu-id="6bef2-262">Once your frame is presented, you can return back to the main program loop and allow it to continue to the next frame.</span></span>

## <a name="hybrid-graphics-pcs-and-mixed-reality-applications"></a><span data-ttu-id="6bef2-263">I PC grafica ibrida e le applicazioni di realtà mista</span><span class="sxs-lookup"><span data-stu-id="6bef2-263">Hybrid graphics PCs and mixed reality applications</span></span>

<span data-ttu-id="6bef2-264">Windows 10 Creators Update PC può essere configurato con **entrambi** GPU discrete e integrate.</span><span class="sxs-lookup"><span data-stu-id="6bef2-264">Windows 10 Creators Update PCs may be configured with **both** discrete and integrated GPUs.</span></span> <span data-ttu-id="6bef2-265">Con questi tipi di computer, Windows sceglierà l'adapter a che di visore VR è connesso.</span><span class="sxs-lookup"><span data-stu-id="6bef2-265">With these types of computers, Windows will choose the adapter the headset is connected to.</span></span> <span data-ttu-id="6bef2-266">Applicazioni devono assicurarsi che il dispositivo DirectX che crea Usa la stessa scheda.</span><span class="sxs-lookup"><span data-stu-id="6bef2-266">Applications must ensure the DirectX device it creates uses the same adapter.</span></span>

<span data-ttu-id="6bef2-267">Codice di esempio Direct3D più generale viene illustrata la creazione di un dispositivo DirectX usando la scheda hardware predefinito, che in un sistema ibrido potrebbe non essere identico a quello usato per le cuffie.</span><span class="sxs-lookup"><span data-stu-id="6bef2-267">Most general Direct3D sample code demonstrates creating a DirectX device using the default hardware adapter, which on a hybrid system may not be the same as the one used for the headset.</span></span>

<span data-ttu-id="6bef2-268">Per risolvere eventuali problemi di questo può causare, usare il <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a> dalla <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>. PrimaryAdapterId() oppure <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>. AdapterId().</span><span class="sxs-lookup"><span data-stu-id="6bef2-268">To work around any issues this may cause, use the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a> from either <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>.PrimaryAdapterId() or <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>.AdapterId().</span></span> <span data-ttu-id="6bef2-269">Questo adapterId è quindi utilizzabile per selezionare il giusto DXGIAdapter usando IDXGIFactory4.EnumAdapterByLuid.</span><span class="sxs-lookup"><span data-stu-id="6bef2-269">This adapterId can then be used to select the right DXGIAdapter using IDXGIFactory4.EnumAdapterByLuid.</span></span>

<span data-ttu-id="6bef2-270">From **DeviceResources::InitializeUsingHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="6bef2-270">From **DeviceResources::InitializeUsingHolographicSpace**:</span></span>

```cpp
// The holographic space might need to determine which adapter supports
// holograms, in which case it will specify a non-zero PrimaryAdapterId.
LUID id =
{
    m_holographicSpace.PrimaryAdapterId().LowPart,
    m_holographicSpace.PrimaryAdapterId().HighPart
};

// When a primary adapter ID is given to the app, the app should find
// the corresponding DXGI adapter and use it to create Direct3D devices
// and device contexts. Otherwise, there is no restriction on the DXGI
// adapter the app can use.
if ((id.HighPart != 0) || (id.LowPart != 0))
{
    UINT createFlags = 0;

    // Create the DXGI factory.
    ComPtr<IDXGIFactory1> dxgiFactory;
    winrt::check_hresult(
        CreateDXGIFactory2(
            createFlags,
            IID_PPV_ARGS(&dxgiFactory)
        ));
    ComPtr<IDXGIFactory4> dxgiFactory4;
    winrt::check_hresult(dxgiFactory.As(&dxgiFactory4));

    // Retrieve the adapter specified by the holographic space.
    winrt::check_hresult(
        dxgiFactory4->EnumAdapterByLuid(
            id,
            IID_PPV_ARGS(&m_dxgiAdapter)
        ));
}
else
{
    m_dxgiAdapter.Reset();
}
```

<span data-ttu-id="6bef2-271">Codice a **aggiornare DeviceResources::CreateDeviceResources aggiornerò IDXGIAdapter**</span><span class="sxs-lookup"><span data-stu-id="6bef2-271">Code to **update DeviceResources::CreateDeviceResources to use IDXGIAdapter**</span></span>

```cpp
// Create the Direct3D 11 API device object and a corresponding context.
ComPtr<ID3D11Device> device;
ComPtr<ID3D11DeviceContext> context;

const D3D_DRIVER_TYPE driverType = m_dxgiAdapter == nullptr ? D3D_DRIVER_TYPE_HARDWARE : D3D_DRIVER_TYPE_UNKNOWN;
const HRESULT hr = D3D11CreateDevice(
    m_dxgiAdapter.Get(),        // Either nullptr, or the primary adapter determined by Windows Holographic.
    driverType,                 // Create a device using the hardware graphics driver.
    0,                          // Should be 0 unless the driver is D3D_DRIVER_TYPE_SOFTWARE.
    creationFlags,              // Set debug and Direct2D compatibility flags.
    featureLevels,              // List of feature levels this app can support.
    ARRAYSIZE(featureLevels),   // Size of the list above.
    D3D11_SDK_VERSION,          // Always set this to D3D11_SDK_VERSION for Windows Runtime apps.
    &device,                    // Returns the Direct3D device created.
    &m_d3dFeatureLevel,         // Returns feature level of device created.
    &context                    // Returns the device immediate context.
);
```

<span data-ttu-id="6bef2-272">**Elementi grafici ibridi e Media Foundation**</span><span class="sxs-lookup"><span data-stu-id="6bef2-272">**Hybrid graphics and Media Foundation**</span></span>

<span data-ttu-id="6bef2-273">Uso di Media Foundation in sistemi ibridi può causare problemi in cui non eseguirà il rendering video o video trama è danneggiata.</span><span class="sxs-lookup"><span data-stu-id="6bef2-273">Using Media Foundation on hybrid systems may cause issues where video will not render or video texture is corrupt.</span></span> <span data-ttu-id="6bef2-274">Ciò può verificarsi perché Media Foundation è verrà utilizzato un comportamento del sistema come indicato in precedenza.</span><span class="sxs-lookup"><span data-stu-id="6bef2-274">This can occur because Media Foundation is defaulting to a system behavior as mentioned above.</span></span> <span data-ttu-id="6bef2-275">In alcuni scenari, la creazione di un ID3D11Device separato è necessaria per il supporto multithreading e la creazione corretta flag sono impostati.</span><span class="sxs-lookup"><span data-stu-id="6bef2-275">In some scenarios, creating a separate ID3D11Device is required to support multi-threading and the correct creation flags are set.</span></span>

<span data-ttu-id="6bef2-276">Durante l'inizializzazione di ID3D11Device, D3D11_CREATE_DEVICE_VIDEO_SUPPORT flag deve essere definito come parte di D3D11_CREATE_DEVICE_FLAG.</span><span class="sxs-lookup"><span data-stu-id="6bef2-276">When initializing the ID3D11Device, D3D11_CREATE_DEVICE_VIDEO_SUPPORT flag must be defined as part of the D3D11_CREATE_DEVICE_FLAG.</span></span> <span data-ttu-id="6bef2-277">Dopo aver creato il dispositivo e il contesto, chiamare <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a> per abilitare il multithreading.</span><span class="sxs-lookup"><span data-stu-id="6bef2-277">Once the device and context is created, call <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a> to enable multithreading.</span></span> <span data-ttu-id="6bef2-278">Per associare il dispositivo con il <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>, utilizzare il <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager::ResetDevice</a> (funzione).</span><span class="sxs-lookup"><span data-stu-id="6bef2-278">To associate the device with the <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>, use the <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager::ResetDevice</a> function.</span></span>

<span data-ttu-id="6bef2-279">Codice a **associare un ID3D11Device IMFDXGIDeviceManager**:</span><span class="sxs-lookup"><span data-stu-id="6bef2-279">Code to **associate a ID3D11Device with IMFDXGIDeviceManager**:</span></span>

```cpp
// create dx device for media pipeline
winrt::com_ptr<ID3D11Device> spMediaDevice;

// See above. Also make sure to enable the following flags on the D3D11 device:
//   * D3D11_CREATE_DEVICE_VIDEO_SUPPORT
//   * D3D11_CREATE_DEVICE_BGRA_SUPPORT
if (FAILED(CreateMediaDevice(spAdapter.get(), &spMediaDevice)))
    return;                                                     

// Turn multithreading on 
winrt::com_ptr<ID3D10Multithread> spMultithread;
if (spContext.try_as(spMultithread))
{
    spMultithread->SetMultithreadProtected(TRUE);
}

// lock the shared dxgi device manager
// call MFUnlockDXGIDeviceManager when no longer needed
UINT uiResetToken;
winrt::com_ptr<IMFDXGIDeviceManager> spDeviceManager;
hr = MFLockDXGIDeviceManager(&uiResetToken, spDeviceManager.put());
if (FAILED(hr))
    return hr;
    
// associate the device with the manager
hr = spDeviceManager->ResetDevice(spMediaDevice.get(), uiResetToken);
if (FAILED(hr))
    return hr;
```

## <a name="see-also"></a><span data-ttu-id="6bef2-280">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6bef2-280">See also</span></span>
* [<span data-ttu-id="6bef2-281">Sistemi di coordinate in DirectX</span><span class="sxs-lookup"><span data-stu-id="6bef2-281">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="6bef2-282">Uso dell'emulatore HoloLens</span><span class="sxs-lookup"><span data-stu-id="6bef2-282">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
